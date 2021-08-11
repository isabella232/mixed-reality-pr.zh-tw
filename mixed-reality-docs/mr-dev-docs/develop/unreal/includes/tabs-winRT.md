---
ms.openlocfilehash: 555360092a65b80a1298eb779736b29360f8c6e13bd1834994f316043843b47a
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2021
ms.locfileid: "115198385"
---
# <a name="426"></a>[4.26](#tab/426)

## <a name="the-standard-winrt-apis"></a>標準 WinRT Api

使用 WinRT 最常見且最簡單的方式，就是從 WinSDK 呼叫方法。 若要這樣做，請開啟 YourModule 檔案，並新增下列幾行：

```csharp
if (Target.Platform == UnrealTargetPlatform.Win64 || Target.Platform == UnrealTargetPlatform.HoloLens)
{
    // These parameters are mandatory for winrt support
    bEnableExceptions = true;
    bUseUnity = false;
    CppStandard = CppStandardVersion.Cpp17;
    PublicSystemLibraries.AddRange(new string[] { "shlwapi.lib", "runtimeobject.lib" });
    PrivateIncludePaths.Add(Path.Combine(Target.WindowsPlatform.WindowsSdkDir,        
                                        "Include", 
                                        Target.WindowsPlatform.WindowsSdkVersion, 
                                        "cppwinrt"));
}
```

接下來，您需要新增下列 WinRT 標頭： 

```cpp
#if (PLATFORM_WINDOWS || PLATFORM_HOLOLENS) 
//Before writing any code, you need to disable common warnings in WinRT headers
#pragma warning(disable : 5205 4265 4268 4946)

#include "Windows/AllowWindowsPlatformTypes.h"
#include "Windows/AllowWindowsPlatformAtomics.h"
#include "Windows/PreWindowsApi.h"

#include <unknwn.h>
#include <winrt/Windows.Foundation.h>
#include <winrt/Windows.Perception.Spatial.h>
#include <winrt/Windows.Foundation.Collections.h>

#include "Windows/PostWindowsApi.h"
#include "Windows/HideWindowsPlatformAtomics.h"
#include "Windows/HideWindowsPlatformTypes.h"
#endif
```

winrt 程式碼只能在 Win64 和 HoloLens 平臺中進行編譯，而 if 語句會防止將 WinRT 程式庫包含在其他平臺上。 已新增 unknwn 來取得 IUnknown 介面。 


## <a name="winrt-from-a-nuget-package"></a>從 NuGet 套件 WinRT

如果您需要使用 WinRT 支援新增 NuGet 套件，則會稍微複雜一點。 在此情況下，Visual Studio 可以為您完成所有工作，但 Unreal 組建系統則無法這麼做。 幸運的是，這並不難。 以下範例說明如何下載 MixedReality 的 < </< QR 套件。 您可以將它取代為另一個，只要確定您不會遺失 winmd 檔案並複製正確的 dll。 

Windows上一節中的 SDK dll 是由作業系統處理。 NuGet 的 dll 必須由模組中的程式碼管理。 建議您新增程式碼來下載它們、複製到二進位檔資料夾，然後載入模組啟動時的進程記憶體。

在第一個步驟中，您應該將 packages.config (新增 https://docs.microsoft.com/nuget/reference/packages-config) 至模組的根資料夾。 您應該新增所有您想要下載的套件，包括其所有相依性。 我在這裡新增了 MixedReality 做為主要承載，並將其他兩個專案作為相依性。 該檔案的格式與 Visual Studio 中的格式相同：

```xml
<?xml version="1.0" encoding="utf-8"?>
<packages>
  <package id="Microsoft.MixedReality.QR" version="0.5.2102" targetFramework="native" />
  <package id="Microsoft.VCRTForwarders.140" version="1.0.6" targetFramework="native" />
  <package id="Microsoft.Windows.CppWinRT" version="2.0.200729.8" targetFramework="native" />
</packages>
```

現在您可以下載 NuGet、必要的套件，或參閱 NuGet[檔](/nuget/consume-packages/install-use-packages-nuget-cli)。

開啟 YourModule，並加入下列程式碼：

```csharp
// WinRT with Nuget support
if (Target.Platform == UnrealTargetPlatform.Win64 || Target.Platform == UnrealTargetPlatform.HoloLens)
{
    // these parameters mandatory for winrt support
    bEnableExceptions = true;
    bUseUnity = false;
    CppStandard = CppStandardVersion.Cpp17;
    PublicSystemLibraries.AddRange(new string [] { "shlwapi.lib", "runtimeobject.lib" });

    // prepare everything for nuget
    string MyModuleName = GetType().Name;
    string NugetFolder = Path.Combine(PluginDirectory, "Intermediate", "Nuget", MyModuleName);
    Directory.CreateDirectory(NugetFolder);

    string BinariesSubFolder = Path.Combine("Binaries", "ThirdParty", Target.Type.ToString(), Target.Platform.ToString(), Target.Architecture);

    PrivateDefinitions.Add(string.Format("THIRDPARTY_BINARY_SUBFOLDER=\"{0}\"", BinariesSubFolder.Replace(@"\", @"\\")));

    string BinariesFolder = Path.Combine(PluginDirectory, BinariesSubFolder);
    Directory.CreateDirectory(BinariesFolder);

    ExternalDependencies.Add("packages.config");

    // download nuget
    string NugetExe = Path.Combine(NugetFolder, "nuget.exe");
    if (!File.Exists(NugetExe))
    {
        using (System.Net.WebClient myWebClient = new System.Net.WebClient())
        {
            // we aren't focusing on a specific nuget version, we can use any of them but the latest one is preferable
            myWebClient.DownloadFile(@"https://dist.nuget.org/win-x86-commandline/latest/nuget.exe", NugetExe);
        }
    }

    // run nuget to update the packages
    {
        var StartInfo = new System.Diagnostics.ProcessStartInfo(NugetExe, string.Format("install \"{0}\" -OutputDirectory \"{1}\"", Path.Combine(ModuleDirectory, "packages.config"), NugetFolder));
        StartInfo.UseShellExecute = false;
        StartInfo.CreateNoWindow = true;
        var ExitCode = Utils.RunLocalProcessAndPrintfOutput(StartInfo);
        if (ExitCode < 0)
        {
            throw new BuildException("Failed to get nuget packages.  See log for details.");
        }
    }

    // get list of the installed packages, that's needed because the code should get particular versions of the installed packages
    string[] InstalledPackages = Utils.RunLocalProcessAndReturnStdOut(NugetExe, string.Format("list -Source \"{0}\"", NugetFolder)).Split(new char[] { '\r', '\n' });

    // winmd files of the packages
    List<string> WinMDFiles = new List<string>();

    // WinRT lib for some job
    string QRPackage = InstalledPackages.FirstOrDefault(x => x.StartsWith("Microsoft.MixedReality.QR"));
    if (!string.IsNullOrEmpty(QRPackage))
    {
        string QRFolderName = QRPackage.Replace(" ", ".");

        // copying dll and winmd binaries to our local binaries folder
        // !!!!! please make sure that you use the path of file! Unreal can't do it for you !!!!!
        string WinMDFile = Path.Combine(NugetFolder, QRFolderName, @"lib\uap10.0.18362\Microsoft.MixedReality.QR.winmd");
        SafeCopy(WinMDFile, Path.Combine(BinariesFolder, "Microsoft.MixedReality.QR.winmd"));

        SafeCopy(Path.Combine(NugetFolder, QRFolderName, string.Format(@"runtimes\win10-{0}\native\Microsoft.MixedReality.QR.dll", Target.WindowsPlatform.Architecture.ToString())),
            Path.Combine(BinariesFolder, "Microsoft.MixedReality.QR.dll"));

        // also both both binaries must be in RuntimeDependencies, unless you get failures in Hololens platform
        RuntimeDependencies.Add(Path.Combine(BinariesFolder, "Microsoft.MixedReality.QR.dll"));
        RuntimeDependencies.Add(Path.Combine(BinariesFolder, "Microsoft.MixedReality.QR.winmd"));

        //add winmd file to the list for further processing using cppwinrt.exe
        WinMDFiles.Add(WinMDFile);
    }

    if (Target.Platform == UnrealTargetPlatform.Win64)
    {
        // Microsoft.VCRTForwarders.140 is needed to run WinRT dlls in Win64 platforms
        string VCRTForwardersPackage = InstalledPackages.FirstOrDefault(x => x.StartsWith("Microsoft.VCRTForwarders.140"));
        if (!string.IsNullOrEmpty(VCRTForwardersPackage))
        {
            string VCRTForwardersName = VCRTForwardersPackage.Replace(" ", ".");
            foreach (var Dll in Directory.EnumerateFiles(Path.Combine(NugetFolder, VCRTForwardersName, "runtimes/win10-x64/native/release"), "*_app.dll"))
            {
                string newDll = Path.Combine(BinariesFolder, Path.GetFileName(Dll));
                SafeCopy(Dll, newDll);
                RuntimeDependencies.Add(newDll);
            }
        }
    }

    // get WinRT package 
    string CppWinRTPackage = InstalledPackages.FirstOrDefault(x => x.StartsWith("Microsoft.Windows.CppWinRT"));
    if (!string.IsNullOrEmpty(CppWinRTPackage))
    {
        string CppWinRTName = CppWinRTPackage.Replace(" ", ".");
        string CppWinRTExe = Path.Combine(NugetFolder, CppWinRTName, "bin", "cppwinrt.exe");
        string CppWinRTFolder = Path.Combine(PluginDirectory, "Intermediate", CppWinRTName, MyModuleName);
        Directory.CreateDirectory(CppWinRTFolder);

        // all downloaded winmd file with WinSDK to be processed by cppwinrt.exe
        var WinMDFilesStringbuilder = new System.Text.StringBuilder();
        foreach (var winmd in WinMDFiles)
        {
            WinMDFilesStringbuilder.Append(" -input \"");
            WinMDFilesStringbuilder.Append(winmd);
            WinMDFilesStringbuilder.Append("\"");
        }

        // generate winrt headers and add them into include paths
        var StartInfo = new System.Diagnostics.ProcessStartInfo(CppWinRTExe, string.Format("{0} -input \"{1}\" -output \"{2}\"", WinMDFilesStringbuilder, Target.WindowsPlatform.WindowsSdkVersion, CppWinRTFolder));
        StartInfo.UseShellExecute = false;
        StartInfo.CreateNoWindow = true;
        var ExitCode = Utils.RunLocalProcessAndPrintfOutput(StartInfo);
        if (ExitCode < 0)
        {
            throw new BuildException("Failed to get generate WinRT headers.  See log for details.");
        }

        PrivateIncludePaths.Add(CppWinRTFolder);
    }
    else
    {
        // fall back to default WinSDK headers if no winrt package in our list
        PrivateIncludePaths.Add(Path.Combine(Target.WindowsPlatform.WindowsSdkDir, "Include", Target.WindowsPlatform.WindowsSdkVersion, "cppwinrt"));
    }
}
```

您必須定義 SafeCopy 方法，如下所示：

```csharp
private void SafeCopy(string source, string destination)
{
    if(!File.Exists(source))
    {
        Log.TraceError("Class {0} can't find {1} file for copying", this.GetType().Name, source);
        return;
    }

    try
    {
        File.Copy(source, destination, true);
    }
    catch(IOException ex)
    {
        Log.TraceWarning("Failed to copy {0} to {1} with exception: {2}", source, destination, ex.Message);
        if (!File.Exists(destination))
        {
            Log.TraceError("Destination file {0} does not exist", destination);
            return;
        }

        Log.TraceWarning("Destination file {0} already existed and is probably in use.  The old file will be used for the runtime dependency.  This may happen when packaging a Win64 exe from the editor.", destination);
    }
}
```

NuGetDll 需要以手動方式載入您的 Win32 進程記憶體;建議您將手動載入新增至模組的啟動方法：

```cpp
void StartupModule() override
{
#if PLATFORM_WINDOWS
    const FString LibrariesDir = FPaths::ProjectPluginsDir() / "MyModule" / THIRDPARTY_BINARY_SUBFOLDER;
    FPlatformProcess::PushDllDirectory(*LibrariesDir);

    const FString DllName = "Microsoft.MixedReality.QR.dll";
    if (!FPlatformProcess::GetDllHandle(*DllName))
    {
        UE_LOG(LogHMD, Warning, TEXT("Dll \'%s\' can't be loaded from \'%s\'"), *DllName, *LibrariesDir);
    }

    FPlatformProcess::PopDllDirectory(*LibrariesDir);
#endif
}
```

最後，您可以將 WinRT 標頭包含在程式碼中，如上一節中所述。

# <a name="425"></a>[4.25](#tab/425)

Unreal 不會以原生方式編譯4.25 版中的 WinRT 程式碼，因此您可以建立 Unreal 的組建系統可使用的個別二進位檔。 

## <a name="objectives"></a>目標

- 建立會開啟 FileSaveDialogue 的通用 Windows DLL
- 將該 DLL 連結至 Unreal 遊戲專案
- 使用新的 DLL，從 Unreal 藍圖將檔案儲存在 HoloLens

## <a name="getting-started"></a>使用者入門

1. 檢查您是否已安裝所有[必要的工具](../tutorials/unreal-uxt-ch1.md)
2. [建立新的 Unreal 專案](../tutorials/unreal-uxt-ch2.md#creating-a-new-unreal-project) ，並將其命名為 **Consumewinrt**
3. 啟用 HoloLens 開發[所需的外掛程式](../tutorials/unreal-uxt-ch2.md#enabling-required-plugins)
4. [設定部署](../tutorials/unreal-uxt-ch6.md) 至裝置或模擬器

## <a name="creating-a-winrt-dll"></a>建立 WinRT DLL 

1. 開啟新的 Visual Studio 專案，並在與 Unreal 遊戲的 **uproject** 檔案相同的目錄中建立 **DLL (通用 Windows)** 專案。 

![建立 DLL](../images/unreal-winrt-img-01.png)

2. 將專案命名為 **HoloLensWinrtDLL** ，並將位置設定為 Unreal 遊戲 uproject 檔的 **ThirdParty** 子目錄。 
    * 選取 **在相同目錄中放置方案和專案** ，以簡化稍後尋找路徑的功能。 

![設定 DLL](../images/unreal-winrt-img-02.png)

> [!IMPORTANT]
> 在新的專案編譯之後，請特別注意空白的 cpp 和標頭檔，分別名為 **HoloLensWinrtDLL .cpp** 和 **HoloLensWinrtDLL** 。 標頭是在 Unreal 中使用 DLL 的 include 檔，而 cpp 會保存您所匯出之任何函式的主體，並包含 Unreal 無法編譯的任何 WinRT 程式碼。 

3. 在您新增任何程式碼之前，您需要更新專案屬性，以確保您需要的 WinRT 程式碼可以編譯： 
    * 以滑鼠右鍵按一下 HoloLensWinrtDLL 專案，然後選取 [**屬性**]  
    * **將設定下拉式清單** 變更 **為所有的設定，並將****平臺** 下拉式清單變更為 **所有平臺**  
    * 在 **Configuration Properties> C/c + +> 所有選項**：
        * 將 **await** 新增至 **其他選項** ，以確保我們可以等候非同步工作  
        * 將 **c + + 語言標準** 變更為 **ISO c + + 17 標準 (/std： c + + 17)** 以包含任何 WinRT 程式碼

![升級專案屬性](../images/unreal-winrt-img-03.png)

您的專案已準備好使用 WinRT 程式碼來更新 DLL 的來源，以開啟檔案對話方塊，並將檔案儲存到 HoloLens 磁片。  

## <a name="adding-the-dll-code"></a>加入 DLL 程式碼

1. 開啟 **HoloLensWinrtDLL** ，並加入 dll 匯出函式以供 Unreal 使用： 

```cpp
#pragma once

class HoloLensWinrtDLL
{
public:
    _declspec(dllexport) static void OpenFileDialogue();
};
```

2. 開啟 **HoloLensWinrtDLL .cpp** ，然後加入類別將使用的所有標頭：  

```cpp
#include "pch.h"
#include "HoloLensWinrtDLL.h"

#include <winrt/Windows.Storage.h>
#include <winrt/Windows.Storage.Streams.h>
#include <winrt/Windows.Storage.Pickers.h>
#include <winrt/Windows.Foundation.h>
#include <winrt/Windows.Foundation.Collections.h>

#include <string>
#include <vector>
#include <thread>
```

> [!NOTE]
> 所有 WinRT 程式碼都會儲存在 **HoloLensWinrtDLL** 中，因此在參考標頭時，Unreal 不會嘗試包含任何 WinRT 程式碼。 

3. 仍在 **HoloLensWinrtDLL .cpp** 中，為 OpenFileDialogue () 和所有支援的程式碼新增函數主體： 

```cpp
// sgm is declared outside of OpenFileDialogue so it doesn't
// get destroyed when OpenFileDialogue goes out of scope.
SaveGameManager sgm;

void HoloLensWinrtDLL::OpenFileDialogue()
{
    sgm.SaveGame();
}
```

4. 將 SaveGameManager 類別新增至 **HoloLensWinrtDLL** ，以處理檔案對話方塊並儲存檔案： 

```cpp
class SaveGameManager
{
public:
    SaveGameManager()
    {
    }

    ~SaveGameManager()
    {
        // Wait for currently running thread to complete before terminating.
        if(m_thread.joinable())
        {
            m_thread.join();
        }
    }

    void SaveGame()
    {
        OpenFileDialogueAction();
    }

private:
    winrt::Windows::Storage::StorageFile m_file = winrt::Windows::Storage::StorageFile(nullptr);
    std::thread m_thread;

    winrt::Windows::Foundation::IAsyncAction OpenFileDialogueAction()
    {
        std::vector<winrt::hstring> extensions;
        extensions.push_back(L".txt");

        auto picker = winrt::Windows::Storage::Pickers::FileSavePicker();

        // FileSavePicker needs a file type to open without errors.
        picker.FileTypeChoices().Insert(L"Plain Text",
                                        winrt::single_threaded_vector<winrt::hstring>(
                                        std::move(extensions)));

        // Opening the FilePicker must be done on the Game UI thread.
        // Any other IAsyncOperations should be done on a background thread.
        m_file = co_await picker.PickSaveFileAsync();

        if(m_file)
        {
            // Unreal's game thread is an STA, async tasks need to run on
            // a background MTA thread, or waiting on them will deadlock.    
            std::thread thread([this]() { RunThread(); });
            m_thread = std::move(thread);
        }
    }

    void RunThread()
    {
        // Ensure this thread is an MTA
        winrt::init_apartment();
        Run().get();
    }

    winrt::Windows::Foundation::IAsyncAction Run()
    {
        co_await winrt::Windows::Storage::FileIO::WriteTextAsync(
                m_file, L"Hello WinRT");
    }
};
```

5. 建立 **發行 > ARM64** 的解決方案，以從 dll 方案將 dll 建立至子目錄 ARM64/Release/HoloLensWinrtDLL。 

## <a name="adding-the-winrt-binary-to-unreal"></a>將 WinRT 二進位檔新增至 Unreal 
在 Unreal 中連結和使用 DLL 需要 c + + 專案。 如果您使用藍圖專案，可以藉由新增 c + + 類別，輕鬆地將它轉換成 c + + 專案：  

1. 在 [Unreal 編輯器] 中，開啟 [ **File > New c + + 類別 ...** 然後， **建立名為** **WinrtActor** 的新動作專案來執行 DLL 中的程式碼： 

![建立新的執行者](../images/unreal-winrt-img-04.png)

> [!NOTE]
> 現在已在與 uproject 檔案相同的目錄中建立方案，以及名為 Source/ConsumeWinRT/ConsumeWinRT 的新組建腳本。

2. 開啟方案、流覽 **遊戲/ConsumeWinRT/來源/ConsumeWinRT** 資料夾，然後開啟 **ConsumeWinRT**：

![開啟 ConsumeWinRT .cs 檔案](../images/unreal-winrt-img-05.png)

### <a name="linking-the-dll"></a>連結 DLL
1. 在 **ConsumeWinRT** 中，加入一個屬性來尋找 DLL 的 include 路徑， (包含 HoloLensWinrtDLL 的目錄) 。 DLL 位於 include 路徑的子目錄中，因此此屬性將用來作為二進位根目錄目錄：

```cs
using System.IO;

public class ConsumeWinRT : ModuleRules
{
    private string WinrtIncPath
    {
        get 
        {
            string ModulePath = Path.GetDirectoryName(
                   RulesCompiler.GetFileNameFromType(this.GetType()));

            // Third party directory is at the project root,
            // which is two directories up from the game .exe (Binaries/HoloLens)
            return Path.GetFullPath(
                   Path.Combine(ModulePath,
                   "../../ThirdParty/HoloLensWinrtDLL"));
        }
    }
}
```

2. 在類別的函式中，加入下列程式碼來更新包含路徑、連結新的 lib 和延遲載入，然後將 DLL 複製到已封裝的 appx 位置：

```cs
public ConsumeWinRT(ReadOnlyTargetRules target) : base(Target)
{
    // This is the directory the DLL's include header is in.
    PublicIncludePaths.Add(WinrtIncPath);

    // The code in HoloLensWinrtDLL will only work in a Windows Store app.
    // Only link these binaries for HoloLens.
    // Similar code can be written for desktop and similarly linked 
    // to use the same features when using Holographic Remoting.
    if(Target.Platform == UnrealTargetPlatform.HoloLens)
    {
        // Link the lib
        PublicAdditionalLibraries.Add(Path.Combine(
              WinrtIncPath, "ARM64", "Release",
              "HoloLensWinrtDLL","HoloLensWinrtDLL.lib"));

        string winrtDLL = "HoloLensWinrtDLL.dll";
        // Mark the dll to be DelayLoaded
        PublicDelayLoadDLLs.Add(winrtDLL);
        // RuntimeDependencies are included in packaged builds.
        RuntimeDependencies.Add(Path.Combine(WinrtIncPath,
                "ARM64", "Release", "HoloLensWinrtDLL", winrtDLL));
    }

    // Preserve the original code in build.cs below:
}
```

3. 開啟 **WinrtActor** ，並新增一個函式定義（藍圖將呼叫的定義）： 

```cpp
public:
    UFUNCTION(BlueprintCallable)
    static void OpenFileDialogue();
```

4. 開啟 **WinrtActor .cpp** ，並更新 BeginPlay 以載入 DLL： 

```cpp
void AWinrtActor::BeginPlay()
{
    Super::BeginPlay();

    // Gets path to DLL location
    const FString BinDir = FPaths::ProjectDir() / 
        "ThirdParty" / "HoloLensWinrtDLL" / 
        "arm64" / "Release" / "HoloLensWinrtDLL";

    // Loads DLL into application
    void * dllHandle = FPlatformProcess::GetDllHandle(
        *(BinDir / "HoloLensWinrtDLL.dll"));
}

void AWinrtActor::OpenFileDialogue()
{
#if PLATFORM_HOLOLENS
    HoloLensWinrtDLL::OpenFileDialogue();
#endif
}
``` 

>[!CAUTION]
> 必須先載入 DLL，然後再呼叫它的任何函式。

### <a name="building-the-game"></a>打造遊戲
1. 建立遊戲解決方案，以啟動對遊戲專案開啟的 Unreal 編輯器： 
    * 在 [ **放置** 動作專案] 索引標籤中，搜尋新的 **WinrtActor** 並將它拖曳到場景中 
    * 開啟層級藍圖，以在 **WinrtActor** 中執行藍圖可呼叫函式 

![將 WinrtActor 放在場景中](../images/unreal-winrt-img-06.png)

2. 在 **世界 Outliner** 中，找出先前放置在場景中的 **WindrtActor** ，並將它拖曳到層級藍圖中： 

![將 WinrtActor 拖曳至層級藍圖](../images/unreal-winrt-img-07.png)

3. 在層級的藍圖中，從 WinrtActor 拖曳輸出節點，搜尋 [開啟檔案] **對話方塊**，然後從任何使用者輸入路由傳送節點。  在此情況下，會從語音事件呼叫 Open File 對話： 

![設定層級藍圖中的節點](../images/unreal-winrt-img-08.png)

4. [封裝此遊戲以進行 HoloLens](../tutorials/unreal-uxt-ch6.md)、部署和執行。  

當 Unreal 呼叫 OpenFileDialogue 時，[檔案] 對話方塊會開啟 HoloLens 提示輸入 .txt 的檔案名。  儲存檔案之後，請移至裝置入口網站中的 [檔案 **瀏覽器** ] 索引標籤，以查看 "Hello WinRT" 內容。 

## <a name="summary"></a>總結 

當您需要使用相同的檔案對話作為 Windows，將檔案儲存到 HoloLens 磁片時，建議您使用本教學課程做為在 Unreal 中使用 WinRT 程式碼的起點。  相同的程式也適用于從 HoloLensWinrtDLL 標頭匯出額外的函式，並在 Unreal 中使用。  請特別注意在背景 MTA 執行緒中等候非同步 WinRT 程式碼的 DLL 程式碼，這樣可避免死結 Unreal 遊戲執行緒。