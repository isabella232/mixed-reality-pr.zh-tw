---
title: HolographicRemoting
description: 檔全像全像遠端 MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: f8631db428464c1381d4940a71908c45a6d4ad9d
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/03/2021
ms.locfileid: "101781210"
---
# <a name="holographic-remoting"></a><span data-ttu-id="c346c-104">全像攝影遠端處理</span><span class="sxs-lookup"><span data-stu-id="c346c-104">Holographic Remoting</span></span>

<span data-ttu-id="c346c-105">全像是使用 Wi-Fi 或 USB 纜線連線，將電腦上的全像攝影內容從電腦即時串流處理至 Microsoft HoloLens。</span><span class="sxs-lookup"><span data-stu-id="c346c-105">Holographic remoting streams holographic content from a PC to your Microsoft HoloLens in real-time, using a Wi-Fi or USB cable connection.</span></span> <span data-ttu-id="c346c-106">當開發混合現實應用程式時，這項功能可以大幅提升開發人員的生產力。</span><span class="sxs-lookup"><span data-stu-id="c346c-106">This feature can significantly increase developer productivity when developing mixed reality applications.</span></span>

## <a name="initial-setup"></a><span data-ttu-id="c346c-107">初始設定</span><span class="sxs-lookup"><span data-stu-id="c346c-107">Initial setup</span></span>

<span data-ttu-id="c346c-108">若要啟用 HoloLens 的遠端功能，請務必確定專案使用的是最新的遠端處理元件。</span><span class="sxs-lookup"><span data-stu-id="c346c-108">To enable remoting to a HoloLens, it is important to ensure that the project is using the latest remoting components.</span></span>

1. <span data-ttu-id="c346c-109">開啟 **視窗 > 套件管理員**</span><span class="sxs-lookup"><span data-stu-id="c346c-109">Open **Window > Package Manager**</span></span>
    - <span data-ttu-id="c346c-110">確認已安裝最新版的 **Windows Mixed Reality** 套件。</span><span class="sxs-lookup"><span data-stu-id="c346c-110">Verify that latest version of the **Windows Mixed Reality** package is installed.</span></span>
1. <span data-ttu-id="c346c-111">確定已在 HoloLens 上透過 Microsoft Store 安裝最新的全像全像遠端應用程式。</span><span class="sxs-lookup"><span data-stu-id="c346c-111">Ensure the latest Holographic Remoting application is installed, on the HoloLens, via the Microsoft Store.</span></span>

### <a name="hololens-2"></a><span data-ttu-id="c346c-112">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="c346c-112">HoloLens 2</span></span>

<span data-ttu-id="c346c-113">使用 HoloLens 2 時，已將對遠端處理明確和眼睛追蹤資料的支援新增至 MRTK。</span><span class="sxs-lookup"><span data-stu-id="c346c-113">When using a HoloLens 2, support for remoting articulated hand and eye tracking data has been added to MRTK.</span></span> <span data-ttu-id="c346c-114">若要啟用這些功能，請使用下列步驟來設定專案。</span><span class="sxs-lookup"><span data-stu-id="c346c-114">To enable these features, configure the project using the following steps.</span></span>

1. <span data-ttu-id="c346c-115"> (混合的現實工具組 **> 公用程式 > 設定 Unity 專案** 來執行 MRTK 設定程式公用程式) </span><span class="sxs-lookup"><span data-stu-id="c346c-115">Run the MRTK Configurator Utility (**Mixed Reality Toolkit > Utilities > Configure Unity Project**)</span></span>
1. <span data-ttu-id="c346c-116">展開 [**修改** 設定]</span><span class="sxs-lookup"><span data-stu-id="c346c-116">Expand **Modify Configurations**</span></span>

    ![MRTK 配置器](../Images/Tools/Remoting/EnableMSBuildForUnity.png)

1. <span data-ttu-id="c346c-118">確定已選取 [ **啟用適用于 Unity 的 MSBuild** ]</span><span class="sxs-lookup"><span data-stu-id="c346c-118">Ensure that **Enable MSBuild for Unity** is selected</span></span>
1. <span data-ttu-id="c346c-119">按一下 [套用]  。</span><span class="sxs-lookup"><span data-stu-id="c346c-119">Click **Apply**</span></span>

<span data-ttu-id="c346c-120">使用 **unity 2019.3** 和更新版本時，無法使用 **啟用適用于 Unity 的 MSBuild** 。</span><span class="sxs-lookup"><span data-stu-id="c346c-120">When using **Unity 2019.3** and later the **Enable MSBuild for Unity** is not available.</span></span> <span data-ttu-id="c346c-121">請遵循下列程式來啟用全像的遠端處理。</span><span class="sxs-lookup"><span data-stu-id="c346c-121">please follow the below procedures to enable holographic remoting.</span></span>

1. <span data-ttu-id="c346c-122"> (混合的現實工具組 **> 公用程式 > 設定 Unity 專案** 來執行 MRTK 設定程式公用程式) </span><span class="sxs-lookup"><span data-stu-id="c346c-122">Run the MRTK Configurator Utility (**Mixed Reality Toolkit > Utilities > Configure Unity Project**)</span></span>
1. <span data-ttu-id="c346c-123">將檔案 **> 組建** 設定中的目標平臺設定為 **通用 Windows 平臺**</span><span class="sxs-lookup"><span data-stu-id="c346c-123">Set the target platform in **File > Build Settings** to **Universal Windows Platform**</span></span>
1. <span data-ttu-id="c346c-124">按一下 [套用]  。</span><span class="sxs-lookup"><span data-stu-id="c346c-124">Click **Apply**</span></span>
1. <span data-ttu-id="c346c-125">開啟 **視窗 > 套件管理員**</span><span class="sxs-lookup"><span data-stu-id="c346c-125">Open **Window > Package Manager**</span></span>
    - <span data-ttu-id="c346c-126">如果專案未使用 [XR SDK](../../configuration/GettingStartedWithMRTKAndXRSDK.md)，請確定未安裝 **Windows XR 外掛程式**，因為舊版 **Windows Mixed Reality** 套件將不會與它一起運作</span><span class="sxs-lookup"><span data-stu-id="c346c-126">Ensure that the **Windows XR Plugin** is not installed if the project isn't using [XR SDK](../../configuration/GettingStartedWithMRTKAndXRSDK.md), as the legacy **Windows Mixed Reality** package will not function alongside it</span></span>
1. <span data-ttu-id="c346c-127">**> Player 開啟 [編輯 > 專案設定**</span><span class="sxs-lookup"><span data-stu-id="c346c-127">Open **Edit > Project Settings > Player**</span></span>

    ![Windows Mixed Reality SDK](../Images/Tools/Remoting/WindowsMixedRealitySDK.png)

1. <span data-ttu-id="c346c-129">確定已選取 [ **支援虛擬實境** ]，並將 **Windows Mixed Reality** 新增至 **虛擬實境 sdk**</span><span class="sxs-lookup"><span data-stu-id="c346c-129">Ensure that **Virtual Reality Supported** is selected and that **Windows Mixed Reality** is added to the **Virtual Reality SDKs**</span></span>

<span data-ttu-id="c346c-130">若要啟用手動接點和眼睛追蹤的追蹤，請依照「透過 Unity 套件匯入和相關章節的 **偵錯工具 HoloLens 2 遠端處理** 」中的步驟進行。</span><span class="sxs-lookup"><span data-stu-id="c346c-130">To enable tracking of hand joints and eye tracking, follow the steps in the **Debugging HoloLens 2 remoting via Unity package import** and related sections.</span></span>

### <a name="debugging-hololens-2-remoting-via-unity-package-import"></a><span data-ttu-id="c346c-131">透過 Unity 套件匯入進行 HoloLens 2 遠端處理的調試</span><span class="sxs-lookup"><span data-stu-id="c346c-131">Debugging HoloLens 2 remoting via Unity package import</span></span>

<span data-ttu-id="c346c-132">如果 HoloLens 2 的手接點和眼睛追蹤無法透過遠端處理，則有幾個常見的潛在問題點。</span><span class="sxs-lookup"><span data-stu-id="c346c-132">If HoloLens 2 hand joints and eye tracking aren't working over remoting, there are a few common points of potential issues.</span></span> <span data-ttu-id="c346c-133">它們會依應檢查的順序列于下方。</span><span class="sxs-lookup"><span data-stu-id="c346c-133">They're listed below in the order they should be checked.</span></span>

<span data-ttu-id="c346c-134">這些問題在 **Unity 2019.3** 或更新版本上執行時特別相關。</span><span class="sxs-lookup"><span data-stu-id="c346c-134">These issues are particularly relevant when running on **Unity 2019.3** or later.</span></span>

#### <a name="msbuildforunity-package-import-via-writing-into-the-packagemanifest"></a><span data-ttu-id="c346c-135">透過寫入封裝 MSBuildForUnity 套件匯入。資訊清單</span><span class="sxs-lookup"><span data-stu-id="c346c-135">MSBuildForUnity package import via writing into the package.manifest</span></span>

> [!Note]
> <span data-ttu-id="c346c-136">有一個已知的問題，可防止適用于 Unity 的某些 Unity 2019 版本上的 MSBuild 無法正常運作。</span><span class="sxs-lookup"><span data-stu-id="c346c-136">There is a known issue that prevents MSBuild for Unity from functioning properly on some versions of Unity 2019.</span></span> <span data-ttu-id="c346c-137">若要避免此問題，MRTK 不支援 Unity 2019.3 上適用于 Unity 的 MSBuild。</span><span class="sxs-lookup"><span data-stu-id="c346c-137">To avoid this issue, the MRTK does not support MSBuild for Unity on Unity 2019.3.</span></span>
>
> <span data-ttu-id="c346c-138">若要在 Unity 2019.3 上執行時取得必要的 NuGet 套件，請參閱 [手動安裝指示](#manual-dotnetadapter-installation)。</span><span class="sxs-lookup"><span data-stu-id="c346c-138">To acquire the required NuGet package when running on Unity 2019.3, please refer to the [manual installation instructions](#manual-dotnetadapter-installation).</span></span>

<span data-ttu-id="c346c-139">檢查的最佳方式是開啟視窗 > 的封裝管理員，並確定 [封裝] 清單中顯示 [適用于 Unity 的 MSBuild]。</span><span class="sxs-lookup"><span data-stu-id="c346c-139">The best way to check is to open Window -> Package Manager and make sure MSBuild for Unity shows up in the packages list.</span></span> <span data-ttu-id="c346c-140">如果有的話，請假設此步驟成功。</span><span class="sxs-lookup"><span data-stu-id="c346c-140">If it's there, assume this step succeeded.</span></span> <span data-ttu-id="c346c-141">如果沒有，請嘗試執行混合現實工具組-> 公用程式-> 設定 Unity，然後重複上述步驟來執行 MRTK 設定程式。</span><span class="sxs-lookup"><span data-stu-id="c346c-141">If it's not there, try running Mixed Reality Toolkit -> Utilities -> Configure Unity and repeat the steps above for running the MRTK Configurator.</span></span>

![MSB4U 套件管理員](../Images/Tools/Remoting/MSB4UPackageManager.png)

#### <a name="dotnetwinrt-nuget-package-resolution"></a><span data-ttu-id="c346c-143">DotNetWinRT NuGet 套件解析</span><span class="sxs-lookup"><span data-stu-id="c346c-143">DotNetWinRT NuGet package resolution</span></span>

<span data-ttu-id="c346c-144">檢查的最佳方式是在 [資產] 資料夾中搜尋 DotNetWinRT.dll。</span><span class="sxs-lookup"><span data-stu-id="c346c-144">The best way to check is to search the Assets folder for DotNetWinRT.dll.</span></span> <span data-ttu-id="c346c-145">如果不存在，請流覽至 [專案] 視圖中的 [資產] 資料夾，然後選取 [] `[ProjectName].Dependencies.msb4u.csproj` 。</span><span class="sxs-lookup"><span data-stu-id="c346c-145">If this doesn't exist, navigate to the Assets folder in the Project view and select `[ProjectName].Dependencies.msb4u.csproj`.</span></span> <span data-ttu-id="c346c-146">假設第1部分成功，應該會有一個具有組建、重建和清除按鈕的自訂偵測器。</span><span class="sxs-lookup"><span data-stu-id="c346c-146">Assuming part 1 did succeed, there should be a custom inspector with Build, Rebuild, and Clean buttons.</span></span> <span data-ttu-id="c346c-147">請嘗試按一下 [建立] 或 [重建]，然後重新搜尋 DotNetWinRT.dll。</span><span class="sxs-lookup"><span data-stu-id="c346c-147">Try clicking Build or Rebuild, and then re-search for DotNetWinRT.dll.</span></span> <span data-ttu-id="c346c-148">如果該 DLL 現在存在，這個步驟就會成功。</span><span class="sxs-lookup"><span data-stu-id="c346c-148">If that DLL now exists, this step succeeded.</span></span>

![DotNetAdapter 偵測器](../Images/Tools/Remoting/DotNetAdapterInspector.png)

#### <a name="dotnetadaptercsproj-missing"></a><span data-ttu-id="c346c-150">DotNetAdapter 缺少 .csproj</span><span class="sxs-lookup"><span data-stu-id="c346c-150">DotNetAdapter.csproj missing</span></span>

<span data-ttu-id="c346c-151">如果上一個步驟失敗，最好再次檢查您專案中是否有適當的 .csproj。</span><span class="sxs-lookup"><span data-stu-id="c346c-151">If the previous step didn't succeed, it's good to double check that the appropriate csproj exists in your project.</span></span> <span data-ttu-id="c346c-152">檢查 MRTK/Providers/WindowsMixedReality/Shared/DotNetAdapter，並檢查 DotNetAdapter 是否存在。</span><span class="sxs-lookup"><span data-stu-id="c346c-152">Check under MRTK / Providers / WindowsMixedReality / Shared / DotNetAdapter and check that DotNetAdapter.csproj exists.</span></span> <span data-ttu-id="c346c-153">如果您的 .gitignore 忽略 .csproj 檔案，而且您已將 MRTK 檔案認可到遠端存放庫，則其中一個常見的情況是此檔案可能不存在。</span><span class="sxs-lookup"><span data-stu-id="c346c-153">One common case where this file might not exist is if your .gitignore ignores csproj files and you've committed the MRTK files to a remote repo.</span></span> <span data-ttu-id="c346c-154">在此情況下，請確定您已強制新增 DotNetAdapter .csproj， `git add -f [path/to]/DotNetAdapter.csproj` 以確定它會針對所有其他共同作業者或電腦進行認可和複製。</span><span class="sxs-lookup"><span data-stu-id="c346c-154">In this case, please make sure you force add DotNetAdapter.csproj with `git add -f [path/to]/DotNetAdapter.csproj` to make sure it gets committed and cloned for all other collaborators or computers.</span></span>

#### <a name="dotnetwinrt_present-define-written-into-player-settings"></a><span data-ttu-id="c346c-155">`DOTNETWINRT_PRESENT` #define 寫入播放的設定</span><span class="sxs-lookup"><span data-stu-id="c346c-155">`DOTNETWINRT_PRESENT` #define written into player settings</span></span>

<span data-ttu-id="c346c-156">流覽至 Unity Player 設定。</span><span class="sxs-lookup"><span data-stu-id="c346c-156">Navigate to the Unity Player Settings.</span></span> <span data-ttu-id="c346c-157">從該處的 [UWP] 索引標籤底下，檢查腳本定義符號的其他設定。</span><span class="sxs-lookup"><span data-stu-id="c346c-157">From there, under the UWP tab, check under Other Settings for the Scripting Define Symbols.</span></span> <span data-ttu-id="c346c-158">請確定已在該清單中正確寫入 DOTNETWINRT_PRESENT。</span><span class="sxs-lookup"><span data-stu-id="c346c-158">Make sure DOTNETWINRT_PRESENT is properly written in that list.</span></span> <span data-ttu-id="c346c-159">如果有的話，這個步驟就成功了。</span><span class="sxs-lookup"><span data-stu-id="c346c-159">If that's there, this step succeeded.</span></span>

![DotNetWinRT 存在](../Images/Tools/Remoting/DotNetWinRTPresent.png)

#### <a name="failure-to-find-dotnetexe"></a><span data-ttu-id="c346c-161">找不到 dotnet.exe 的問題</span><span class="sxs-lookup"><span data-stu-id="c346c-161">Failure to find dotnet.exe</span></span>

<span data-ttu-id="c346c-162">適用于 Unity 的 MSBuild 取決於系統路徑中現有的 dotnet.exe，dotnet.exe 必須安裝並存在於 PATH 環境變數中。</span><span class="sxs-lookup"><span data-stu-id="c346c-162">MSBuild for Unity depends on dotnet.exe existing in the system path - dotnet.exe must both be installed and present in the PATH environment variable.</span></span> <span data-ttu-id="c346c-163">如果這兩項需求都不成立，Unity 主控台可能會出現此錯誤：</span><span class="sxs-lookup"><span data-stu-id="c346c-163">If neither of those requirements are true, this error may manifest in the Unity console:</span></span>

```cmd
Win32Exception: ApplicationName='dotnet', CommandLine='msbuild DotNetAdapter.csproj -restore  -v:minimal -p:NuGetInteractive=true  -t:Build -p:Configuration=Release -nologo', CurrentDirectory='C:\src\Assets\MRTK\Providers\WindowsMixedReality\Shared\DotNetAdapter', Native error= The system cannot find the file specified.
```

<span data-ttu-id="c346c-164">解決方法是確保 [已安裝 .Net CORE CLI 工具](https://docs.microsoft.com/dotnet/core/tools/?tabs=netcore2x) ，並重新啟動系統，以強制所有應用程式取得重新整理的系統路徑。</span><span class="sxs-lookup"><span data-stu-id="c346c-164">The solution to this is to ensure that the [.NET Core CLI tools are installed](https://docs.microsoft.com/dotnet/core/tools/?tabs=netcore2x) and reboot the system to force all apps to get a refreshed system path.</span></span>

<span data-ttu-id="c346c-165">如果在執行上述步驟之後，透過遠端處理的操作仍無法運作，則在裝置上的一般操作設定檔中可能會有設定不正確的問題。</span><span class="sxs-lookup"><span data-stu-id="c346c-165">If hand joints over remoting are still not working after following the above steps, there might be something misconfigured in the profiles for general hand joints on-device.</span></span> <span data-ttu-id="c346c-166">在此情況下，請與 [我們的其中一個說明資源聯繫](../../WelcomeToMRTK.md#getting-help)。</span><span class="sxs-lookup"><span data-stu-id="c346c-166">In that case, please [reach out on one of our help resources](../../WelcomeToMRTK.md#getting-help).</span></span>

#### <a name="manual-dotnetadapter-installation"></a><span data-ttu-id="c346c-167">手動 DotNetAdapter 安裝</span><span class="sxs-lookup"><span data-stu-id="c346c-167">Manual DotNetAdapter installation</span></span>

<span data-ttu-id="c346c-168">如果無法透過 MSBuild for Unity 執行 DotNetAdapter 安裝，則可以執行下列步驟。</span><span class="sxs-lookup"><span data-stu-id="c346c-168">In the event that the installation of the DotNetAdapter cannot be performed via MSBuild for Unity, the following steps can be performed.</span></span>

> [!Important]
> <span data-ttu-id="c346c-169">不支援同時使用適用于 Unity 的 MSBuild 和相同專案中的另一個 NuGet 用戶端，因此可能會導致相依性解析問題。</span><span class="sxs-lookup"><span data-stu-id="c346c-169">Using both MSBuild for Unity and another NuGet client within the same project is not supported and can result in potential dependency resolution issues.</span></span>

1. <span data-ttu-id="c346c-170">安裝 NuGet 用戶端</span><span class="sxs-lookup"><span data-stu-id="c346c-170">Install a NuGet client</span></span>

    > [!Note]
    > <span data-ttu-id="c346c-171">下列指示假設使用 [適用于 Unity 的 NuGet](https://github.com/GlitchEnzo/NuGetForUnity/releases)</span><span class="sxs-lookup"><span data-stu-id="c346c-171">The following instructions presume use of [NuGet for Unity](https://github.com/GlitchEnzo/NuGetForUnity/releases)</span></span>

1. <span data-ttu-id="c346c-172">流覽至 NuGet 用戶端 UI</span><span class="sxs-lookup"><span data-stu-id="c346c-172">Navigate to the NuGet client UI</span></span>

    ![啟動 NuGet UI](../Images/Tools/Remoting/LaunchNuGetForUnity.png)

1. <span data-ttu-id="c346c-174">找出 `Microsoft.Windows.MixedReality.DotNetWinRT` 套件</span><span class="sxs-lookup"><span data-stu-id="c346c-174">Locate the `Microsoft.Windows.MixedReality.DotNetWinRT` package</span></span>

    ![尋找套件](../Images/Tools/Remoting/LocateDotNetWinRT.png)

1. <span data-ttu-id="c346c-176">選取安裝</span><span class="sxs-lookup"><span data-stu-id="c346c-176">Select Install</span></span>

### <a name="removing-hololens-2-specific-remoting-support"></a><span data-ttu-id="c346c-177">移除 HoloLens 2 特定的遠端支援</span><span class="sxs-lookup"><span data-stu-id="c346c-177">Removing HoloLens 2-specific remoting support</span></span>

<span data-ttu-id="c346c-178">如果您因為 DotNetWinRT 介面卡的存在而遇到衝突或其他問題，請前往 [我們的其中一個說明資源](../../WelcomeToMRTK.md#getting-help)。</span><span class="sxs-lookup"><span data-stu-id="c346c-178">If you're running into conflicts or other issues due to the presence of the DotNetWinRT adapter, please [reach out on one of our help resources](../../WelcomeToMRTK.md#getting-help).</span></span>

<span data-ttu-id="c346c-179">您也可以透過下列步驟，暫時移除介面卡以因應您的問題：</span><span class="sxs-lookup"><span data-stu-id="c346c-179">You can also temporarily remove the adapter to workaround your issue via the following steps:</span></span>

1. <span data-ttu-id="c346c-180">在 Unity 中，移至 [視窗-> 套件管理員]，並卸載適用于 Unity 的 MSBuild。</span><span class="sxs-lookup"><span data-stu-id="c346c-180">In Unity, go to Window -> Package Manager and uninstall MSBuild for Unity.</span></span>
1. <span data-ttu-id="c346c-181">在 Unity 的 [資產] 清單中搜尋 DotNetWinRT.dll，並刪除 DLL 或刪除 (MRTK 2.2 或舊版) 的外掛程式，或刪除 (MRTK 2.3 或更新版本或更新版本) 資料夾，其中包含幾個層級。</span><span class="sxs-lookup"><span data-stu-id="c346c-181">Search for DotNetWinRT.dll in your assets list in Unity and either delete the DLL or delete the Plugins (MRTK 2.2 or earlier) or Dependencies (MRTK 2.3 or later) folder that contains it a few levels up.</span></span> <span data-ttu-id="c346c-182">這應該會移除這些衝突的命名空間，同時保持 MRTK。</span><span class="sxs-lookup"><span data-stu-id="c346c-182">That should remove these conflicting namespaces, while keeping MRTK around.</span></span>
1. <span data-ttu-id="c346c-183"> (選擇性) 在您的檔案瀏覽器中流覽至 MRTK/Providers/WindowsMixedReality/Shared/DotNetAdapter， (不是 Unity 的資產視圖) 並刪除 `.bin` 和 `.obj` 資料夾。</span><span class="sxs-lookup"><span data-stu-id="c346c-183">(Optional) Navigate to MRTK / Providers / WindowsMixedReality / Shared / DotNetAdapter in your file explorer (not Unity's Assets view) and delete the `.bin` and `.obj` folders.</span></span> <span data-ttu-id="c346c-184">這會移除 DotNetWinRT 的 NuGet 還原套件的本機快取。</span><span class="sxs-lookup"><span data-stu-id="c346c-184">This removes the local cache of NuGet restored packages for DotNetWinRT.</span></span>
1. <span data-ttu-id="c346c-185">如果您再次執行 MRTK 配置器，請確定您不會重新啟用適用于 Unity 的 MSBuild。</span><span class="sxs-lookup"><span data-stu-id="c346c-185">If you run the MRTK Configurator again, make sure you don't re-enable MSBuild for Unity.</span></span>

## <a name="connecting-to-the-hololens-with-wi-fi"></a><span data-ttu-id="c346c-186">使用 Wi-Fi 連接到 HoloLens</span><span class="sxs-lookup"><span data-stu-id="c346c-186">Connecting to the HoloLens with Wi-Fi</span></span>

<span data-ttu-id="c346c-187">設定好專案之後，就可以建立 HoloLens 的連接。</span><span class="sxs-lookup"><span data-stu-id="c346c-187">Once the project has been configured, a connection can be established to the HoloLens.</span></span>

1. <span data-ttu-id="c346c-188">在 [檔案 **> 組建設定**] 中，確定 [專案組建類型] 已設定為 [**通用 Windows 平臺**]</span><span class="sxs-lookup"><span data-stu-id="c346c-188">In **File > Build Settings**, ensure that the project build type is set to **Universal Windows Platform**</span></span>
1. <span data-ttu-id="c346c-189">在 HoloLens 上啟動全像 **遠端處理** 應用程式。</span><span class="sxs-lookup"><span data-stu-id="c346c-189">On the HoloLens, launch the **Holographic Remoting** application.</span></span>
1. <span data-ttu-id="c346c-190">在 Unity 中，選取 [ **Window > XR] >**[全像] 模擬。</span><span class="sxs-lookup"><span data-stu-id="c346c-190">In Unity, select **Window > XR > Holographic Emulation**.</span></span>

    ![開始全像模擬](../Images/Tools/Remoting/StartHolographicEmulation.png)

1. <span data-ttu-id="c346c-192">將 **模擬模式** 設定為 [ **遠端裝置**]。</span><span class="sxs-lookup"><span data-stu-id="c346c-192">Set **Emulation Mode** to **Remote to Device**.</span></span>

    ![設定模擬模式](../Images/Tools/Remoting/SelectEmulationMode.png)

1. <span data-ttu-id="c346c-194">選取 **裝置版本**。</span><span class="sxs-lookup"><span data-stu-id="c346c-194">Select the **Device Version**.</span></span>

    ![選取裝置版本](../Images/Tools/Remoting/SelectDeviceVersion.png)

1. <span data-ttu-id="c346c-196">使用「全像遠端播放播放程式」應用程式所顯示的 IP 位址，設定 [ **遠端電腦** ] 欄位。</span><span class="sxs-lookup"><span data-stu-id="c346c-196">Using the IP Address displayed by the Holographic Remoting Player application, set the **Remote Machine** field.</span></span>

    ![輸入 IP 位址](../Images/Tools/Remoting/EnterIPAddress.png)

1. <span data-ttu-id="c346c-198">按一下 [連線]。</span><span class="sxs-lookup"><span data-stu-id="c346c-198">Click **Connect**.</span></span>

> [!NOTE]
> <span data-ttu-id="c346c-199">如果您無法連線，請確定您的 HoloLens 2 未插入電腦並重新啟動 Unity。</span><span class="sxs-lookup"><span data-stu-id="c346c-199">If you cannot connect, make sure your HoloLens 2 is not plugged in to your PC and restart Unity.</span></span>

## <a name="connecting-to-the-hololens-with-usb-cable"></a><span data-ttu-id="c346c-200">使用 USB 纜線連接到 HoloLens</span><span class="sxs-lookup"><span data-stu-id="c346c-200">Connecting to the HoloLens with USB cable</span></span>

<span data-ttu-id="c346c-201">USB 纜線連接可提供更佳的轉譯品質和穩定性。</span><span class="sxs-lookup"><span data-stu-id="c346c-201">USB cable connection gives better rendering quality and stability.</span></span> <span data-ttu-id="c346c-202">若要使用 USB 纜線連線，請從 Wi-Fi HoloLens 與 HoloLens 的設定中斷連線，並啟動全像遠端播放機應用程式。</span><span class="sxs-lookup"><span data-stu-id="c346c-202">To use USB cable connection, disconnect from the HoloLens from Wi-Fi in HoloLens's Settings and launch Holographic Remoting Player app.</span></span> <span data-ttu-id="c346c-203">它會顯示開頭為169的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="c346c-203">It will display an IP address that starts with 169.</span></span> <span data-ttu-id="c346c-204">在 Unity 的全像模擬設定中使用此 IP 位址來連接。</span><span class="sxs-lookup"><span data-stu-id="c346c-204">Use this IP address in Unity's Holographic Emulation setting to connect.</span></span> <span data-ttu-id="c346c-205">一旦識別出 USB 纜線的 IP 位址之後，就可以安全地將 HoloLens 連接到 Wi-Fi。</span><span class="sxs-lookup"><span data-stu-id="c346c-205">Once the IP address for USB cable has been identified, it is safe to connect the HoloLens to Wi-Fi again.</span></span>

## <a name="starting-a-remoting-session"></a><span data-ttu-id="c346c-206">啟動遠端會話</span><span class="sxs-lookup"><span data-stu-id="c346c-206">Starting a remoting session</span></span>

<span data-ttu-id="c346c-207">將 Unity 連接到 HoloLens 之後，請在編輯器中輸入播放模式。</span><span class="sxs-lookup"><span data-stu-id="c346c-207">With Unity connected to the HoloLens, enter play mode in the editor.</span></span>

<span data-ttu-id="c346c-208">當會話完成時，結束播放模式。</span><span class="sxs-lookup"><span data-stu-id="c346c-208">When the session is complete, exit play mode.</span></span>

> [!NOTE]
> <span data-ttu-id="c346c-209">有一些 Unity 版本的已知問題，在遠端會話期間，編輯器可能會在進入播放模式時停止回應。</span><span class="sxs-lookup"><span data-stu-id="c346c-209">There is a known issue with some versions of Unity where the editor may hang upon entering play mode during a remoting session.</span></span> <span data-ttu-id="c346c-210">如果在載入專案時，全像全像是開啟的全像是，就會發生此問題。</span><span class="sxs-lookup"><span data-stu-id="c346c-210">This issue may manifest if the Holographic window is open when the project is loaded.</span></span> <span data-ttu-id="c346c-211">若要確保不會發生此問題，請一律在離開 Unity 之前關閉全像的對話方塊。</span><span class="sxs-lookup"><span data-stu-id="c346c-211">To ensure this issue does not occur, always close the Holographic dialog prior to exiting Unity.</span></span>

## <a name="see-also"></a><span data-ttu-id="c346c-212">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c346c-212">See also</span></span>

- [<span data-ttu-id="c346c-213">全像遠端的疑難排解和限制</span><span class="sxs-lookup"><span data-stu-id="c346c-213">Holographic Remoting troubleshooting and limitations</span></span>](https://docs.microsoft.com/windows/mixed-reality/holographic-remoting-troubleshooting)
- [<span data-ttu-id="c346c-214">Microsoft 全像遠端軟體授權條款</span><span class="sxs-lookup"><span data-stu-id="c346c-214">Microsoft Holographic Remoting software license terms</span></span>](https://docs.microsoft.com/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
