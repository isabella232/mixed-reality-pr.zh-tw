---
ms.openlocfilehash: fd44d63ad502b6807c6aa18ce6fc63493fc254dc
ms.sourcegitcommit: 09522ab15a9008ca4d022f9e37fcc98f6eaf6093
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/30/2020
ms.locfileid: "96354438"
---
# <a name="425"></a>[<span data-ttu-id="61c59-101">4.25</span><span class="sxs-lookup"><span data-stu-id="61c59-101">4.25</span></span>](#tab/425)

<span data-ttu-id="61c59-102">Unreal 不會以原生方式編譯4.25 版中的 WinRT 程式碼，因此您必須建立個別的二進位檔，並且可供 Unreal 的組建系統取用。</span><span class="sxs-lookup"><span data-stu-id="61c59-102">Unreal doesn't natively compile WinRT code in version 4.25, so it's your job to build a separate binary and that can be consumed by Unreal’s build system.</span></span> <span data-ttu-id="61c59-103">本教學課程將逐步引導您完成這類案例。</span><span class="sxs-lookup"><span data-stu-id="61c59-103">This tutorial will walk you through just such a scenario.</span></span>

## <a name="objectives"></a><span data-ttu-id="61c59-104">目標</span><span class="sxs-lookup"><span data-stu-id="61c59-104">Objectives</span></span>
- <span data-ttu-id="61c59-105">建立會開啟 FileSaveDialogue 的通用 Windows DLL</span><span class="sxs-lookup"><span data-stu-id="61c59-105">Create a Universal Windows DLL that opens a FileSaveDialogue</span></span>
- <span data-ttu-id="61c59-106">將該 DLL 連結至 Unreal 遊戲專案</span><span class="sxs-lookup"><span data-stu-id="61c59-106">Link that DLL to an Unreal game project</span></span>
- <span data-ttu-id="61c59-107">使用新的 DLL，從 Unreal 藍圖將檔案儲存在 HoloLens 上</span><span class="sxs-lookup"><span data-stu-id="61c59-107">Save a file on the HoloLens from an Unreal blueprint using the new DLL</span></span>

## <a name="getting-started"></a><span data-ttu-id="61c59-108">開始使用</span><span class="sxs-lookup"><span data-stu-id="61c59-108">Getting started</span></span>
1. <span data-ttu-id="61c59-109">檢查您是否已安裝所有[必要的工具](../tutorials/unreal-uxt-ch1.md)</span><span class="sxs-lookup"><span data-stu-id="61c59-109">Check that you have all [required tools](../tutorials/unreal-uxt-ch1.md) installed</span></span>
2. <span data-ttu-id="61c59-110">[建立新的 Unreal 專案](../tutorials/unreal-uxt-ch2.md#creating-a-new-unreal-project) ，並將其命名為 **Consumewinrt**</span><span class="sxs-lookup"><span data-stu-id="61c59-110">[Create a new Unreal project](../tutorials/unreal-uxt-ch2.md#creating-a-new-unreal-project) and name it **Consumewinrt**</span></span>
3. <span data-ttu-id="61c59-111">啟用 [所需的外掛程式](../tutorials/unreal-uxt-ch2.md#enabling-required-plugins) 以進行 HoloLens 開發</span><span class="sxs-lookup"><span data-stu-id="61c59-111">Enable the [required plugins](../tutorials/unreal-uxt-ch2.md#enabling-required-plugins) for HoloLens development</span></span>
4. <span data-ttu-id="61c59-112">[設定部署](../tutorials/unreal-uxt-ch6.md) 至裝置或模擬器</span><span class="sxs-lookup"><span data-stu-id="61c59-112">[Setup for deployment](../tutorials/unreal-uxt-ch6.md) to a device or emulator</span></span>

## <a name="creating-a-winrt-dll"></a><span data-ttu-id="61c59-113">建立 WinRT DLL</span><span class="sxs-lookup"><span data-stu-id="61c59-113">Creating a WinRT DLL</span></span> 
1. <span data-ttu-id="61c59-114">開啟新的 Visual Studio 專案，然後在與 Unreal 遊戲的 **uproject** 檔案相同的目錄中，建立 **DLL (通用 Windows)** 專案。</span><span class="sxs-lookup"><span data-stu-id="61c59-114">Open a new Visual Studio project and create a **DLL (Universal Windows)** project in the same directory to the Unreal game’s **uproject** file.</span></span> 

![建立 DLL](../images/unreal-winrt-img-01.png)

2. <span data-ttu-id="61c59-116">將專案命名為 **HoloLensWinrtDLL** ，並將位置設定為 Unreal 遊戲 uproject 檔的 **ThirdParty** 子目錄。</span><span class="sxs-lookup"><span data-stu-id="61c59-116">Name the project **HoloLensWinrtDLL** and set the location as a **ThirdParty** subdirectory to the Unreal game’s uproject file.</span></span> 
    * <span data-ttu-id="61c59-117">選取 **在相同目錄中放置方案和專案** ，以簡化稍後尋找路徑的功能。</span><span class="sxs-lookup"><span data-stu-id="61c59-117">Select **Place solution and project in the same directory** to simplify looking for paths later.</span></span> 

![設定 DLL](../images/unreal-winrt-img-02.png)

> [!IMPORTANT]
> <span data-ttu-id="61c59-119">在新的專案編譯之後，您想要特別注意空白的 cpp 和標頭檔，分別名為 **HoloLensWinrtDLL .cpp** 和 **HoloLensWinrtDLL** 。</span><span class="sxs-lookup"><span data-stu-id="61c59-119">After the new project compiles, you want to pay special attention to the blank cpp and header files, named **HoloLensWinrtDLL.cpp** and **HoloLensWinrtDLL.h** respectively.</span></span> <span data-ttu-id="61c59-120">標頭是在 Unreal 中使用 DLL 的 include 檔，而 cpp 會保存您所匯出之任何函式的主體，並包含 Unreal 無法編譯的任何 WinRT 程式碼。</span><span class="sxs-lookup"><span data-stu-id="61c59-120">The header is the include file that uses the DLL in Unreal, while the cpp holds the body of any functions you export and includes any WinRT code that Unreal wouldn't otherwise be able to compile.</span></span> 

3. <span data-ttu-id="61c59-121">在您新增任何程式碼之前，您需要更新專案屬性，以確保您需要的 WinRT 程式碼可以編譯：</span><span class="sxs-lookup"><span data-stu-id="61c59-121">Before you add any code, you need to update the project properties to ensure the WinRT code you need can compile:</span></span> 
    * <span data-ttu-id="61c59-122">以滑鼠右鍵按一下 HoloLensWinrtDLL 專案，然後選取 [**屬性**]</span><span class="sxs-lookup"><span data-stu-id="61c59-122">Right click on the HoloLensWinrtDLL project and select **properties**</span></span>  
    * <span data-ttu-id="61c59-123">**將設定下拉式清單** 變更 **為所有的設定，並將\*\*\*\*平臺** 下拉式清單變更為 **所有平臺**</span><span class="sxs-lookup"><span data-stu-id="61c59-123">Change the **Configuration** dropdown to **All Configurations** and the **Platform** dropdown to **All Platforms**</span></span>  
    * <span data-ttu-id="61c59-124">在 **Configuration Properties> C/c + +> 所有選項**：</span><span class="sxs-lookup"><span data-stu-id="61c59-124">Under **Configuration Properties> C/C++> All Options**:</span></span>
        * <span data-ttu-id="61c59-125">將 **await** 新增至 **其他選項** ，以確保我們可以等候非同步工作</span><span class="sxs-lookup"><span data-stu-id="61c59-125">Add **await** to **Additional Options** to ensure we can wait on async tasks</span></span>  
        * <span data-ttu-id="61c59-126">將 **c + + 語言標準** 變更為 **ISO c + + 17 標準 (/std： c + + 17)** 以包含任何 WinRT 程式碼</span><span class="sxs-lookup"><span data-stu-id="61c59-126">Change **C++ Language Standard** to **ISO C++17 Standard (/std:c++17)** to include any WinRT code</span></span>

![升級專案屬性](../images/unreal-winrt-img-03.png)

<span data-ttu-id="61c59-128">您的專案已準備好使用 WinRT 程式碼來更新 DLL 的來源，以開啟檔案對話方塊，並將檔案儲存到 HoloLens 磁片。</span><span class="sxs-lookup"><span data-stu-id="61c59-128">Your project is ready to update the DLL’s source with WinRT code that opens a file dialogue and saves a file to the HoloLens disk.</span></span>  

## <a name="adding-the-dll-code"></a><span data-ttu-id="61c59-129">加入 DLL 程式碼</span><span class="sxs-lookup"><span data-stu-id="61c59-129">Adding the DLL code</span></span>
1. <span data-ttu-id="61c59-130">開啟 **HoloLensWinrtDLL** ，並加入 dll 匯出函式以供 Unreal 使用：</span><span class="sxs-lookup"><span data-stu-id="61c59-130">Open **HoloLensWinrtDLL.h** and add a dll exported function for Unreal to consume:</span></span> 

```cpp
#pragma once

class HoloLensWinrtDLL
{
public:
    _declspec(dllexport) static void OpenFileDialogue();
};
```

2. <span data-ttu-id="61c59-131">開啟 **HoloLensWinrtDLL .cpp** ，然後加入類別將使用的所有標頭：</span><span class="sxs-lookup"><span data-stu-id="61c59-131">Open **HoloLensWinrtDLL.cpp** and add all headers the class will use:</span></span>  

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
> <span data-ttu-id="61c59-132">所有 WinRT 程式碼都會儲存在 **HoloLensWinrtDLL** 中，因此在參考標頭時，Unreal 不會嘗試包含任何 WinRT 程式碼。</span><span class="sxs-lookup"><span data-stu-id="61c59-132">All WinRT code is stored in **HoloLensWinrtDLL.cpp** so Unreal doesn't try to include any WinRT code when referencing the header.</span></span> 

3. <span data-ttu-id="61c59-133">仍在 **HoloLensWinrtDLL .cpp** 中，為 OpenFileDialogue ( # A1 和所有支援的程式碼新增函式主體：</span><span class="sxs-lookup"><span data-stu-id="61c59-133">Still in **HoloLensWinrtDLL.cpp**, add a function body for OpenFileDialogue() and all supported code:</span></span> 

```cpp
// sgm is declared outside of OpenFileDialogue so it doesn't
// get destroyed when OpenFileDialogue goes out of scope.
SaveGameManager sgm;

void HoloLensWinrtDLL::OpenFileDialogue()
{
    sgm.SaveGame();
}
```

4. <span data-ttu-id="61c59-134">將 SaveGameManager 類別新增至 **HoloLensWinrtDLL** ，以處理檔案對話方塊並儲存檔案：</span><span class="sxs-lookup"><span data-stu-id="61c59-134">Add a SaveGameManager class to **HoloLensWinrtDLL.cpp** to handle the file dialogue and saving the file:</span></span> 

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

5. <span data-ttu-id="61c59-135">建立 **發行 > ARM64** 的解決方案，以從 dll 方案將 dll 建立至子目錄 ARM64/Release/HoloLensWinrtDLL。</span><span class="sxs-lookup"><span data-stu-id="61c59-135">Build the solution for **Release > ARM64** to build the DLL to the child directory ARM64/Release/HoloLensWinrtDLL from the DLL solution.</span></span> 

## <a name="adding-the-winrt-binary-to-unreal"></a><span data-ttu-id="61c59-136">將 WinRT 二進位檔新增至 Unreal</span><span class="sxs-lookup"><span data-stu-id="61c59-136">Adding the WinRT binary to Unreal</span></span> 
<span data-ttu-id="61c59-137">在 Unreal 中連結和使用 DLL 需要 c + + 專案。</span><span class="sxs-lookup"><span data-stu-id="61c59-137">Linking and using a DLL in Unreal requires a C++ project.</span></span> <span data-ttu-id="61c59-138">如果您使用藍圖專案，可以藉由新增 c + + 類別，輕鬆地將它轉換成 c + + 專案：</span><span class="sxs-lookup"><span data-stu-id="61c59-138">If you're using a Blueprint project, it can be easily converted to a C++ project by adding a C++ class:</span></span>  

1. <span data-ttu-id="61c59-139">在 [Unreal 編輯器] 中，開啟 [ **File > New c + + 類別 ...**</span><span class="sxs-lookup"><span data-stu-id="61c59-139">In the Unreal editor, open **File > New C++ Class…**</span></span> <span data-ttu-id="61c59-140">然後， **建立名為** **WinrtActor** 的新動作專案來執行 DLL 中的程式碼：</span><span class="sxs-lookup"><span data-stu-id="61c59-140">and create a new **Actor** named **WinrtActor** to run the code in the DLL:</span></span> 

![建立新的執行者](../images/unreal-winrt-img-04.png)

> [!NOTE]
> <span data-ttu-id="61c59-142">現在已在與 uproject 檔案相同的目錄中建立方案，以及名為 Source/ConsumeWinRT/ConsumeWinRT 的新組建腳本。</span><span class="sxs-lookup"><span data-stu-id="61c59-142">A solution has now been created in the same directory as the uproject file along with a new build script named Source/ConsumeWinRT/ConsumeWinRT.Build.cs.</span></span>

2. <span data-ttu-id="61c59-143">開啟方案、流覽 **遊戲/ConsumeWinRT/來源/ConsumeWinRT** 資料夾，然後開啟 **ConsumeWinRT.build.cs**：</span><span class="sxs-lookup"><span data-stu-id="61c59-143">Open the solution, browse for the **Games/ConsumeWinRT/Source/ConsumeWinRT** folder, and open **ConsumeWinRT.build.cs**:</span></span>

![開啟 ConsumeWinRT.build.cs 檔案](../images/unreal-winrt-img-05.png)

### <a name="linking-the-dll"></a><span data-ttu-id="61c59-145">連結 DLL</span><span class="sxs-lookup"><span data-stu-id="61c59-145">Linking the DLL</span></span>
1. <span data-ttu-id="61c59-146">在 **ConsumeWinRT.build.cs** 中，新增屬性以找出 DLL (目錄中包含 HoloLensWinrtDLL) 的 include 路徑。</span><span class="sxs-lookup"><span data-stu-id="61c59-146">In **ConsumeWinRT.build.cs**, add a property to find the include path for the DLL (the directory containing HoloLensWinrtDLL.h).</span></span> <span data-ttu-id="61c59-147">DLL 位於 include 路徑的子目錄中，因此此屬性將用來作為二進位根目錄目錄：</span><span class="sxs-lookup"><span data-stu-id="61c59-147">The DLL is in a child directory to the include path, so this property will be used as the binary root dir:</span></span>

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

2. <span data-ttu-id="61c59-148">在類別的函式中，加入下列程式碼來更新包含路徑、連結新的 lib 和延遲載入，然後將 DLL 複製到已封裝的 appx 位置：</span><span class="sxs-lookup"><span data-stu-id="61c59-148">In the class constructor, add the following code to update the include path, link the new lib, and delay-load and copy the DLL to the packaged appx location:</span></span>

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

3. <span data-ttu-id="61c59-149">開啟 **WinrtActor** ，並新增一個函式定義（藍圖將呼叫的定義）：</span><span class="sxs-lookup"><span data-stu-id="61c59-149">Open **WinrtActor.h** and add one function definition, one that a blueprint will call:</span></span> 

```cpp
public:
    UFUNCTION(BlueprintCallable)
    static void OpenFileDialogue();
```

4. <span data-ttu-id="61c59-150">開啟 **WinrtActor .cpp** ，並更新 BeginPlay 以載入 DLL：</span><span class="sxs-lookup"><span data-stu-id="61c59-150">Open **WinrtActor.cpp** and update BeginPlay to load the DLL:</span></span> 

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
> <span data-ttu-id="61c59-151">必須先載入 DLL，然後再呼叫它的任何函式。</span><span class="sxs-lookup"><span data-stu-id="61c59-151">The DLL must be loaded before calling any of its functions.</span></span>

### <a name="building-the-game"></a><span data-ttu-id="61c59-152">打造遊戲</span><span class="sxs-lookup"><span data-stu-id="61c59-152">Building the game</span></span>
1. <span data-ttu-id="61c59-153">建立遊戲解決方案，以啟動對遊戲專案開啟的 Unreal 編輯器：</span><span class="sxs-lookup"><span data-stu-id="61c59-153">Build the game solution to launch the Unreal editor opened to the game project:</span></span> 
    * <span data-ttu-id="61c59-154">在 [ **放置** 動作專案] 索引標籤中，搜尋新的 **WinrtActor** 並將它拖曳到場景中</span><span class="sxs-lookup"><span data-stu-id="61c59-154">In the **Place Actors** tab, search for the new **WinrtActor** and drag it into the scene</span></span> 
    * <span data-ttu-id="61c59-155">開啟層級藍圖，以在 **WinrtActor** 中執行藍圖可呼叫函式</span><span class="sxs-lookup"><span data-stu-id="61c59-155">Open the level blueprint to execute the blueprint callable function in the **WinrtActor**</span></span> 

![將 WinrtActor 放在場景中](../images/unreal-winrt-img-06.png)

2. <span data-ttu-id="61c59-157">在 **世界 Outliner** 中，找出先前放置在場景中的 **WindrtActor** ，並將它拖曳到層級藍圖中：</span><span class="sxs-lookup"><span data-stu-id="61c59-157">In the **World Outliner**, find the **WindrtActor** previously dropped into the scene and drag it into the level blueprint:</span></span> 

![將 WinrtActor 拖曳至層級藍圖](../images/unreal-winrt-img-07.png)

3. <span data-ttu-id="61c59-159">在層級的藍圖中，從 WinrtActor 拖曳輸出節點，搜尋 [開啟檔案] **對話方塊**，然後從任何使用者輸入路由傳送節點。</span><span class="sxs-lookup"><span data-stu-id="61c59-159">In the level blueprint, drag the output node from WinrtActor, search for **Open File Dialogue**, then route the node from any user input.</span></span>  <span data-ttu-id="61c59-160">在此情況下，會從語音事件呼叫 Open File 對話：</span><span class="sxs-lookup"><span data-stu-id="61c59-160">In this case, Open File Dialogue is being called from a speech event:</span></span> 

![設定層級藍圖中的節點](../images/unreal-winrt-img-08.png)

4. <span data-ttu-id="61c59-162">將[此遊戲封裝到 HoloLens](../tutorials/unreal-uxt-ch6.md)、加以部署，然後執行。</span><span class="sxs-lookup"><span data-stu-id="61c59-162">[Package this game for HoloLens](../tutorials/unreal-uxt-ch6.md), deploy it, and run.</span></span>  

<span data-ttu-id="61c59-163">當 Unreal 呼叫 OpenFileDialogue 時，會在 HoloLens 提示輸入 .txt 檔案名時開啟 [檔案] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="61c59-163">When Unreal calls OpenFileDialogue, a File Dialogue opens on the HoloLens prompting for a .txt file name.</span></span>  <span data-ttu-id="61c59-164">儲存檔案之後，請移至裝置入口網站中的 [檔案 **瀏覽器** ] 索引標籤，以查看 "Hello WinRT" 內容。</span><span class="sxs-lookup"><span data-stu-id="61c59-164">After the file is saved, go to the **File explorer** tab in the device portal to see the contents “Hello WinRT”.</span></span> 

## <a name="summary"></a><span data-ttu-id="61c59-165">摘要</span><span class="sxs-lookup"><span data-stu-id="61c59-165">Summary</span></span> 

<span data-ttu-id="61c59-166">我們鼓勵您使用本教學課程中的程式碼，做為在 Unreal 中使用 WinRT 程式碼的起點。</span><span class="sxs-lookup"><span data-stu-id="61c59-166">We encourage you to use the code in this tutorial as a starting point for consuming WinRT code in Unreal.</span></span>  <span data-ttu-id="61c59-167">它可讓使用者使用與 Windows 相同的檔案對話方塊，將檔案儲存到 HoloLens 磁片。</span><span class="sxs-lookup"><span data-stu-id="61c59-167">It allows users to save files to the HoloLens disk using the same file dialogue as Windows.</span></span>  <span data-ttu-id="61c59-168">遵循相同的程式，從 HoloLensWinrtDLL 標頭匯出任何額外的函式，並在 Unreal 中使用。</span><span class="sxs-lookup"><span data-stu-id="61c59-168">Follow the same process to export any additional functions from the HoloLensWinrtDLL header and used in Unreal.</span></span>  <span data-ttu-id="61c59-169">請注意在背景 MTA 執行緒中等候任何非同步 WinRT 程式碼的 DLL 程式碼，可避免死結 Unreal 遊戲執行緒。</span><span class="sxs-lookup"><span data-stu-id="61c59-169">Note the DLL code that waits on any async WinRT code in a background MTA thread, which avoids deadlocking the Unreal game thread.</span></span> 

# <a name="426"></a>[<span data-ttu-id="61c59-170">4.26</span><span class="sxs-lookup"><span data-stu-id="61c59-170">4.26</span></span>](#tab/426)

## <a name="the-standard-winrt-apis"></a><span data-ttu-id="61c59-171">標準 WinRT Api</span><span class="sxs-lookup"><span data-stu-id="61c59-171">The standard WinRT APIs</span></span>

<span data-ttu-id="61c59-172">使用 WinRT 最常見且最簡單的方式，就是從 WinSDK 呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="61c59-172">The most common and easiest way to use WinRT is to call methods from WinSDK.</span></span> <span data-ttu-id="61c59-173">若要這樣做，請開啟 YourModule.Build.cs 檔案，並新增下列幾行：</span><span class="sxs-lookup"><span data-stu-id="61c59-173">To do so, open YourModule.Build.cs file and add the following lines:</span></span>

```cpp
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

<span data-ttu-id="61c59-174">接下來，您需要新增下列 WinRT 標頭：</span><span class="sxs-lookup"><span data-stu-id="61c59-174">Next, you need to add the following WinRT headers:</span></span> 

```cpp
#if (PLATFORM_WINDOWS || PLATFORM_HOLOLENS) 
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

<span data-ttu-id="61c59-175">WinRT 程式碼只能在 Win64 和 HoloLens 平臺中進行編譯，而 if 語句會防止將 WinRT 程式庫包含在其他平臺上。</span><span class="sxs-lookup"><span data-stu-id="61c59-175">WinRT code can only be compiled in the Win64 and HoloLens platforms, so the if statement prevents WinRT libraries from being included on other platforms.</span></span> <span data-ttu-id="61c59-176">已新增 unknwn 來取得 IUnknown 介面。</span><span class="sxs-lookup"><span data-stu-id="61c59-176">unknwn.h was added for having the IUnknown interface.</span></span> 

<span data-ttu-id="61c59-177">撰寫任何程式碼之前，您必須使用下列方法停用 WinRT 標頭中的一般警告：</span><span class="sxs-lookup"><span data-stu-id="61c59-177">Before writing any code, you need to disable common warnings in WinRT headers by using:</span></span>

```cpp
#pragma warning(disable : 5205 4265)
```

## <a name="winrt-from-a-nuget-package"></a><span data-ttu-id="61c59-178">從 NuGet 套件 WinRT</span><span class="sxs-lookup"><span data-stu-id="61c59-178">WinRT from a NuGet package</span></span>

<span data-ttu-id="61c59-179">如果您需要新增具有 WinRT 支援的 nuget 套件，則會稍微複雜一點。</span><span class="sxs-lookup"><span data-stu-id="61c59-179">It’s a little more complicated if you need to add a nuget package with WinRT support.</span></span> <span data-ttu-id="61c59-180">在此情況下，Visual Studio 可以為您完成所有工作，但 Unreal 組建系統則無法這麼做。</span><span class="sxs-lookup"><span data-stu-id="61c59-180">In this case, Visual Studio can do practically all job for you, but the Unreal build system can’t.</span></span> <span data-ttu-id="61c59-181">幸運的是，這並不難。</span><span class="sxs-lookup"><span data-stu-id="61c59-181">Luckily, it’s not too difficult.</span></span> <span data-ttu-id="61c59-182">以下範例說明如何下載 MixedReality 的 < </< QR 套件。</span><span class="sxs-lookup"><span data-stu-id="61c59-182">Below is an example of how you would go about downloading the Microsoft.MixedReality.QR package.</span></span> <span data-ttu-id="61c59-183">您可以將它取代為另一個，只要確定您不會遺失 winmd 檔案並複製正確的 dll。</span><span class="sxs-lookup"><span data-stu-id="61c59-183">You can replace it with another, just make sure that you don’t lose the winmd file and copy the correct dll.</span></span> 

<span data-ttu-id="61c59-184">從上一節 Windows SDK dll 是由作業系統處理。</span><span class="sxs-lookup"><span data-stu-id="61c59-184">Windows SDK dlls from the previous section are handled by the OS.</span></span> <span data-ttu-id="61c59-185">Nuget 的 dll 必須由模組中的程式碼管理。</span><span class="sxs-lookup"><span data-stu-id="61c59-185">Nuget’s dlls must be managed by the code in your module.</span></span> <span data-ttu-id="61c59-186">您應該加入程式碼以下載它們、將其複製到二進位檔案資料夾，並載入至模組啟動時的進程記憶體。</span><span class="sxs-lookup"><span data-stu-id="61c59-186">You should add code to download them, copy into binaries folder and load into the process memory at the module startup.</span></span>

<span data-ttu-id="61c59-187">在第一個步驟中，您應該將 packages.config (新增 https://docs.microsoft.com/nuget/reference/packages-config) 至模組的根資料夾。</span><span class="sxs-lookup"><span data-stu-id="61c59-187">At the first step, you should add a packages.config (https://docs.microsoft.com/nuget/reference/packages-config) into the root folder of your module.</span></span> <span data-ttu-id="61c59-188">您應該新增所有您想要下載的套件，包括其所有相依性。</span><span class="sxs-lookup"><span data-stu-id="61c59-188">There you should add all packages you want to download, including all their dependencies.</span></span> <span data-ttu-id="61c59-189">我在這裡新增了 MixedReality 做為主要承載，並將其他兩個專案作為相依性。</span><span class="sxs-lookup"><span data-stu-id="61c59-189">Here I added Microsoft.MixedReality.QR as a primary payload and two others as dependencies to it.</span></span> <span data-ttu-id="61c59-190">該檔案的格式與 Visual Studio 中的格式相同：</span><span class="sxs-lookup"><span data-stu-id="61c59-190">The format of that file is same as in Visual Studio:</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<packages>
  <package id="Microsoft.MixedReality.QR" version="0.5.2102" targetFramework="native" />
  <package id="Microsoft.VCRTForwarders.140" version="1.0.6" targetFramework="native" />
  <package id="Microsoft.Windows.CppWinRT" version="2.0.200729.8" targetFramework="native" />
</packages>
```

<span data-ttu-id="61c59-191">現在您可以下載 NuGet、必要的套件，或參閱 NuGet [檔](https://docs.microsoft.com/nuget/consume-packages/install-use-packages-nuget-cli)。</span><span class="sxs-lookup"><span data-stu-id="61c59-191">Now you can download the NuGet, the required packages, or refer to the NuGet [documentation](https://docs.microsoft.com/nuget/consume-packages/install-use-packages-nuget-cli).</span></span>

<span data-ttu-id="61c59-192">開啟 YourModule.Build.cs 並新增下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="61c59-192">Open YourModule.Build.cs and add the following code:</span></span>

```cpp
if(Target.Platform == UnrealTargetPlatform.Win64 || Target.Platform == UnrealTargetPlatform.HoloLens)
{
    string MyModuleName = GetType().Name;

    // these parameters mandatory for winrt support
    bEnableExceptions = true;
    bUseUnity = false;
    CppStandard = CppStandardVersion.Cpp17;
    PublicSystemLibraries.Add("shlwapi.lib");
    PublicSystemLibraries.Add("runtimeobject.lib");

    // prepare everything for nuget
    string NugetFolder = Path.Combine(PluginDirectory, "Intermediate", "Nuget", MyModuleName);
    Directory.CreateDirectory(NugetFolder);

    string BinariesSubFolder = Path.Combine("Binaries", "ThirdParty", Target.Type.ToString(), Target.Platform.ToString(), Target.Architecture);

            PrivateDefinitions.Add(string.Format("THIRDPARTY_BINARY_SUBFOLDER=\"{0}\"", BinariesSubFolder.Replace(@"\", @"\\")));

    string BinariesFolder = Path.Combine(PluginDirectory, BinariesSubFolder);
    Directory.CreateDirectory(BinariesFolder);

    // download nuget
    string NugetExe = Path.Combine(NugetFolder, "nuget.exe");
    if(!File.Exists(NugetExe))
    {
        using (System.Net.WebClient myWebClient = new System.Net.WebClient())
        {
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
            
    // get list of the installed packages
    string[] InstalledPackages = Utils.RunLocalProcessAndReturnStdOut(NugetExe, string.Format("list -Source \"{0}\"", NugetFolder)).Split(new char[] {'\r', '\n' });

    // get WinRT package 
    string CppWinRTPackage = InstalledPackages.First(x => x.StartsWith("Microsoft.Windows.CppWinRT"));
    if(!string.IsNullOrEmpty(CppWinRTPackage))
    {
        string CppWinRTName = CppWinRTPackage.Replace(" ", ".");
        string CppWinRTExe = Path.Combine(NugetFolder, CppWinRTName, "bin", "cppwinrt.exe");
        string CppWinRTFolder = Path.Combine(PluginDirectory, "Intermediate", CppWinRTName, MyModuleName);
        Directory.CreateDirectory(CppWinRTFolder);

        // search all downloaded packages for winmd files
        string[] WinMDFiles = Directory.GetFiles(NugetFolder, "*.winmd", SearchOption.AllDirectories);

        // all downloaded winmd file with WinSDK to be processed by cppwinrt.exe
        var WinMDFilesStringbuilder = new System.Text.StringBuilder();
        foreach(var winmd in WinMDFiles)
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
        // fall to default WinSDK headers
                        PrivateIncludePaths.Add(Path.Combine(Target.WindowsPlatform.WindowsSdkDir, "Include", Target.WindowsPlatform.WindowsSdkVersion, "cppwinrt"));
            }

    // WinRT lib for some job
    string QRPackage = InstalledPackages.First(x => x.StartsWith("Microsoft.MixedReality.QR"));
    if (!string.IsNullOrEmpty(QRPackage))
    {
        string QRFolderName = QRPackage.Replace(" ", ".");

        // copying dll and winmd binaries to our local binaries folder
        // !!!!! please make sure that you use the path of file! Unreal can't do it for you !!!!!
        SafeCopy(Path.Combine(NugetFolder, QRFolderName, @"lib\uap10.0.18362\Microsoft.MixedReality.QR.winmd"), 
        Path.Combine(BinariesFolder, "Microsoft.MixedReality.QR.winmd"));

        SafeCopy(Path.Combine(NugetFolder, QRFolderName, string.Format(@"runtimes\win10-{0}\native\Microsoft.MixedReality.QR.dll", Target.WindowsPlatform.Architecture.ToString())), 
        Path.Combine(BinariesFolder, "Microsoft.MixedReality.QR.dll"));

        // also both both binaries must be in RuntimeDependencies, unless you get failures in Hololens platform
        RuntimeDependencies.Add(Path.Combine(BinariesFolder, "Microsoft.MixedReality.QR.dll"));
        RuntimeDependencies.Add(Path.Combine(BinariesFolder, "Microsoft.MixedReality.QR.winmd"));
    }

    if(Target.Platform == UnrealTargetPlatform.Win64)
    {
        // Microsoft.VCRTForwarders.140 is needed to run WinRT dlls in Win64 platforms
        string VCRTForwardersPackage = InstalledPackages.First(x => x.StartsWith("Microsoft.VCRTForwarders.140"));
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
```

<span data-ttu-id="61c59-193">您必須定義 SafeCopy 方法，如下所示：</span><span class="sxs-lookup"><span data-stu-id="61c59-193">You'll need to define the SafeCopy method as follows:</span></span>

```cpp
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

<span data-ttu-id="61c59-194">您必須手動將 Nuget Dll 載入您的 Win32 進程記憶體。</span><span class="sxs-lookup"><span data-stu-id="61c59-194">Nuget DLLs needs to load into your Win32 process memory manually.</span></span> <span data-ttu-id="61c59-195">您應該將手動載入新增至模組的啟動方法：</span><span class="sxs-lookup"><span data-stu-id="61c59-195">You should add manual loading into the startup method of your module:</span></span>

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

<span data-ttu-id="61c59-196">最後，您可以將 WinRT 標頭包含在程式碼中，如上一節中所述。</span><span class="sxs-lookup"><span data-stu-id="61c59-196">Finally, you can include WinRT headers into your code as described in the previous section.</span></span>