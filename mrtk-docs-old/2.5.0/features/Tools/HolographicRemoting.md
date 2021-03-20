---
title: HolographicRemoting
description: 檔全像全像遠端 MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: ec58aff6d055c55ef4af9ea6ce43f79203f28727
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104689578"
---
# <a name="holographic-remoting"></a><span data-ttu-id="4d3b8-104">全像攝影遠端處理</span><span class="sxs-lookup"><span data-stu-id="4d3b8-104">Holographic Remoting</span></span>

<span data-ttu-id="4d3b8-105">全像是，使用 Wi-Fi 或 USB 纜線連線，全像是即時的遠端處理將電腦上的全息內容串流處理到您的 Microsoft HoloLens。</span><span class="sxs-lookup"><span data-stu-id="4d3b8-105">Holographic remoting streams holographic content from a PC to your Microsoft HoloLens in real-time, using a Wi-Fi or USB cable connection.</span></span> <span data-ttu-id="4d3b8-106">當開發混合現實應用程式時，這項功能可以大幅提升開發人員的生產力。</span><span class="sxs-lookup"><span data-stu-id="4d3b8-106">This feature can significantly increase developer productivity when developing mixed reality applications.</span></span>

<span data-ttu-id="4d3b8-107">XR SDK （如下所述）是 unity [2019.3 及更高的 unity 新 XR 管線](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/)。</span><span class="sxs-lookup"><span data-stu-id="4d3b8-107">XR SDK as mentioned below refers to Unity's [new XR pipeline in Unity 2019.3 and beyond](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/).</span></span> <span data-ttu-id="4d3b8-108">如需搭配使用 XR SDK 與 MRTK 的詳細資訊，請參閱 [這裡](../../configuration/GettingStartedWithMRTKAndXRSDK.md) 。</span><span class="sxs-lookup"><span data-stu-id="4d3b8-108">See [here](../../configuration/GettingStartedWithMRTKAndXRSDK.md) for more information on using XR SDK with MRTK.</span></span> <span data-ttu-id="4d3b8-109">舊版 XR 是指 unity 2018 中包含的現有 XR 管線，在 Unity 2019.3 中已被取代，並已在 Unity 2020 中移除。</span><span class="sxs-lookup"><span data-stu-id="4d3b8-109">Legacy XR refers to the existing XR pipeline that is included in Unity 2018, deprecated in Unity 2019.3 and removed in Unity 2020.</span></span>

## <a name="initial-setup"></a><span data-ttu-id="4d3b8-110">初始設定</span><span class="sxs-lookup"><span data-stu-id="4d3b8-110">Initial setup</span></span>

<span data-ttu-id="4d3b8-111">若要啟用 HoloLens 的遠端功能，請務必確定專案使用的是最新的遠端處理元件。</span><span class="sxs-lookup"><span data-stu-id="4d3b8-111">To enable remoting to a HoloLens, it is important to ensure that the project is using the latest remoting components.</span></span>

1. <span data-ttu-id="4d3b8-112">開啟 **視窗 > 封裝管理員**</span><span class="sxs-lookup"><span data-stu-id="4d3b8-112">Open **Window > Package Manager**</span></span>
    - <span data-ttu-id="4d3b8-113">如果使用舊版 XR：確認已安裝最新版的 **Windows Mixed Reality** 套件。</span><span class="sxs-lookup"><span data-stu-id="4d3b8-113">If using legacy XR: Verify that latest version of the **Windows Mixed Reality** package is installed.</span></span>
    - <span data-ttu-id="4d3b8-114">如果使用 XR SDK：請確認已安裝最新版的 **WINDOWS XR 外掛程式** 套件。</span><span class="sxs-lookup"><span data-stu-id="4d3b8-114">If using XR SDK: Verify that latest version of the **Windows XR Plugin** package is installed.</span></span>
1. <span data-ttu-id="4d3b8-115">確定已在 HoloLens 上透過 Microsoft Store 安裝最新的全像全像遠端處理應用程式。</span><span class="sxs-lookup"><span data-stu-id="4d3b8-115">Ensure the latest Holographic Remoting application is installed, on the HoloLens, via the Microsoft Store.</span></span>

<span data-ttu-id="4d3b8-116">請根據專案中使用的管線，繼續閱讀 [舊版 XR 安裝指示](#legacy-xr-setup-instructions) 或 [XR SDK 設定指示](#xr-sdk-setup-instructions) 。</span><span class="sxs-lookup"><span data-stu-id="4d3b8-116">Please continue to [Legacy XR setup instructions](#legacy-xr-setup-instructions) or [XR SDK setup instructions](#xr-sdk-setup-instructions) depending on which pipeline is used in the project.</span></span>

## <a name="legacy-xr-setup-instructions"></a><span data-ttu-id="4d3b8-117">舊版 XR 安裝指示</span><span class="sxs-lookup"><span data-stu-id="4d3b8-117">Legacy XR setup instructions</span></span>

<span data-ttu-id="4d3b8-118">下列指示僅適用于使用 HoloLens 2 的遠端處理。</span><span class="sxs-lookup"><span data-stu-id="4d3b8-118">The instructions below only apply to remoting with HoloLens 2.</span></span> <span data-ttu-id="4d3b8-119">如果您只使用 HoloLens (第1代) 進行遠端處理，請跳至 [使用 wi-fi 連線到 hololens](#connecting-to-the-hololens-with-wi-fi)。</span><span class="sxs-lookup"><span data-stu-id="4d3b8-119">If you only perform remoting with HoloLens (1st Gen), skip to [Connecting to the HoloLens with Wi-Fi](#connecting-to-the-hololens-with-wi-fi).</span></span>

<span data-ttu-id="4d3b8-120">使用 HoloLens 2 時，已將對遠端的已表達和眼睛追蹤資料的支援新增至 MRTK。</span><span class="sxs-lookup"><span data-stu-id="4d3b8-120">When using a HoloLens 2, support for remoting articulated hand and eye tracking data has been added to MRTK.</span></span> <span data-ttu-id="4d3b8-121">若要啟用這些功能，請選取 **混合的現實工具** 組  >  **msbuild**  >  **將 msbuild 用於 Unity** 相依性解析。</span><span class="sxs-lookup"><span data-stu-id="4d3b8-121">To enable these features, please select **Mixed Reality Toolkit** > **MSBuild** > **Use MSBuild for Unity dependency resolution**.</span></span> <span data-ttu-id="4d3b8-122">這將會為全像全像進行安裝時安裝必要的相依性。</span><span class="sxs-lookup"><span data-stu-id="4d3b8-122">This will install the required dependencies for Holographic Remoting.</span></span>

<span data-ttu-id="4d3b8-123">當 MSBuild 完成匯入程式之後，下一個步驟是選取 **混合現實工具** 組  >  **公用程式**  >  **Windows Mixed Reality**  >  **檢查** 設定。</span><span class="sxs-lookup"><span data-stu-id="4d3b8-123">Once MSBuild completes the import process, the next step is to select **Mixed Reality Toolkit** > **Utilities** > **Windows Mixed Reality** > **Check Configuration**.</span></span> <span data-ttu-id="4d3b8-124">此步驟會新增腳本定義，以啟用 MSBuild for Unity 所安裝的 DotNetWinRT 相依性。</span><span class="sxs-lookup"><span data-stu-id="4d3b8-124">This step adds a scripting define that enables the DotNetWinRT dependency that is installed by MSBuild for Unity.</span></span>

<span data-ttu-id="4d3b8-125">某些版本的 Unity 2019 在使用適用于 Unity 的 MSBuild 時遇到問題。</span><span class="sxs-lookup"><span data-stu-id="4d3b8-125">Some versions of Unity 2019 have encountered issues when using MSBuild for Unity.</span></span> <span data-ttu-id="4d3b8-126">如果 [ **使用 MSBuild For Unity** 相依性解析] 選項失敗，請使用下列步驟來啟用全像的遠端處理。</span><span class="sxs-lookup"><span data-stu-id="4d3b8-126">If the **Use MSBuild for Unity dependency resolution** option fails, please use the following steps to enable holographic remoting.</span></span>

1. <span data-ttu-id="4d3b8-127">將檔案 **> 組建** 設定中的目標平臺設定為 **通用 Windows 平臺**</span><span class="sxs-lookup"><span data-stu-id="4d3b8-127">Set the target platform in **File > Build Settings** to **Universal Windows Platform**</span></span>
1. <span data-ttu-id="4d3b8-128">如果未自動顯示，請 (**混合現實工具組 > 公用程式 > 設定 Unity 專案** 來執行 MRTK 設定程式公用程式) </span><span class="sxs-lookup"><span data-stu-id="4d3b8-128">If it does not automatically display, run the MRTK Configurator Utility (**Mixed Reality Toolkit > Utilities > Configure Unity Project**)</span></span>
1. <span data-ttu-id="4d3b8-129">按一下 [套用]  。</span><span class="sxs-lookup"><span data-stu-id="4d3b8-129">Click **Apply**</span></span>
1. <span data-ttu-id="4d3b8-130">開啟 **視窗 > 封裝管理員**</span><span class="sxs-lookup"><span data-stu-id="4d3b8-130">Open **Window > Package Manager**</span></span>
    - <span data-ttu-id="4d3b8-131">確定未安裝 **WINDOWS XR 外掛程式**</span><span class="sxs-lookup"><span data-stu-id="4d3b8-131">Ensure that the **Windows XR Plugin** is not installed</span></span>
1. <span data-ttu-id="4d3b8-132">**> Player 開啟 [編輯 > 專案設定**</span><span class="sxs-lookup"><span data-stu-id="4d3b8-132">Open **Edit > Project Settings > Player**</span></span>

    ![Windows Mixed Reality SDK](../Images/Tools/Remoting/WindowsMixedRealitySDK.png)

1. <span data-ttu-id="4d3b8-134">確定已選取 **支援的虛擬實境** ，且 **Windows Mixed Reality** 已新增至 **虛擬實境 sdk**</span><span class="sxs-lookup"><span data-stu-id="4d3b8-134">Ensure that **Virtual Reality Supported** is selected and that **Windows Mixed Reality** is added to the **Virtual Reality SDKs**</span></span>

<span data-ttu-id="4d3b8-135">若要追蹤手接程式和眼睛追蹤，請依照 **HoloLens 2 透過 Unity 套件匯入** 和相關章節進行的偵錯工具中的步驟進行。</span><span class="sxs-lookup"><span data-stu-id="4d3b8-135">To enable tracking of hand joints and eye tracking, follow the steps in the **Debugging HoloLens 2 remoting via Unity package import** and related sections.</span></span>

### <a name="debugging-hololens-2-remoting-via-unity-package-import"></a><span data-ttu-id="4d3b8-136">透過 Unity 套件匯入進行 HoloLens 2 遠端處理的調試</span><span class="sxs-lookup"><span data-stu-id="4d3b8-136">Debugging HoloLens 2 remoting via Unity package import</span></span>

<span data-ttu-id="4d3b8-137">如果 HoloLens 2 的手接點和眼睛追蹤未在遠端處理，則有幾個常見的潛在問題點。</span><span class="sxs-lookup"><span data-stu-id="4d3b8-137">If HoloLens 2 hand joints and eye tracking aren't working over remoting, there are a few common points of potential issues.</span></span> <span data-ttu-id="4d3b8-138">它們會依應檢查的順序列于下方。</span><span class="sxs-lookup"><span data-stu-id="4d3b8-138">They're listed below in the order they should be checked.</span></span>

<span data-ttu-id="4d3b8-139">這些問題在 **Unity 2019.3** 或更新版本上執行時特別相關。</span><span class="sxs-lookup"><span data-stu-id="4d3b8-139">These issues are particularly relevant when running on **Unity 2019.3** or later.</span></span>

#### <a name="msbuildforunity-package-import-via-writing-into-the-packagemanifest"></a><span data-ttu-id="4d3b8-140">透過寫入封裝 MSBuildForUnity 套件匯入。資訊清單</span><span class="sxs-lookup"><span data-stu-id="4d3b8-140">MSBuildForUnity package import via writing into the package.manifest</span></span>

<span data-ttu-id="4d3b8-141">若要啟用適用于 unity 的 msbuild，請執行 **混合現實工具** 組  >  **msbuild**  >  **使用 msbuild 進行 unity** 相依性解析。</span><span class="sxs-lookup"><span data-stu-id="4d3b8-141">To enable MSBuild for Unity, please run **Mixed Reality Toolkit** > **MSBuild** > **Use MSBuild for Unity dependency resolution**.</span></span> <span data-ttu-id="4d3b8-142">執行此命令之後，MSBuild 應該開始匯入相依性。</span><span class="sxs-lookup"><span data-stu-id="4d3b8-142">After running this command, MSBuild should begin importing dependencies.</span></span> <span data-ttu-id="4d3b8-143">匯入可能需要幾秒鐘的時間才會開始。</span><span class="sxs-lookup"><span data-stu-id="4d3b8-143">It may take a few seconds for importing to begin.</span></span>

<span data-ttu-id="4d3b8-144">[ **使用 MSBuild For Unity** 相依性解析] 命令不會顯示確認。</span><span class="sxs-lookup"><span data-stu-id="4d3b8-144">The **Use MSBuild for Unity dependency resolution** command does not display a confirmation.</span></span> <span data-ttu-id="4d3b8-145">若要確認是否成功，請開啟 [ **Window**  >  **封裝管理員**]，並確定 [封裝] 清單中顯示 [適用于 Unity 的 MSBuild]。</span><span class="sxs-lookup"><span data-stu-id="4d3b8-145">To confirm that it succeeded, open **Window** > **Package Manager** and make sure MSBuild for Unity shows up in the packages list.</span></span> <span data-ttu-id="4d3b8-146">如果有的話，請假設此步驟成功。</span><span class="sxs-lookup"><span data-stu-id="4d3b8-146">If it's there, assume this step succeeded.</span></span>

> [!Note]
> <span data-ttu-id="4d3b8-147">有一個問題會導致 MSBuild for Unity 無法在某些 Unity 2019 版本上正常運作。</span><span class="sxs-lookup"><span data-stu-id="4d3b8-147">There is an issue that prevents MSBuild for Unity from functioning properly on some versions of Unity 2019.</span></span> <span data-ttu-id="4d3b8-148">如果遇到問題，請參閱 [手動安裝指示](#manual-dotnetadapter-installation)。</span><span class="sxs-lookup"><span data-stu-id="4d3b8-148">If issues are encountered, please refer to the [manual installation instructions](#manual-dotnetadapter-installation).</span></span>

![MSB4U 封裝管理員](../Images/Tools/Remoting/MSB4UPackageManager.png)

#### <a name="dotnetwinrt-nuget-package-resolution"></a><span data-ttu-id="4d3b8-150">DotNetWinRT NuGet 套件解析</span><span class="sxs-lookup"><span data-stu-id="4d3b8-150">DotNetWinRT NuGet package resolution</span></span>

<span data-ttu-id="4d3b8-151">檢查的最佳方式是在 [資產] 資料夾中搜尋 DotNetWinRT.dll。</span><span class="sxs-lookup"><span data-stu-id="4d3b8-151">The best way to check is to search the Assets folder for DotNetWinRT.dll.</span></span> <span data-ttu-id="4d3b8-152">如果不存在，請流覽至 [專案] 視圖中的 [資產] 資料夾，然後選取 [] `[ProjectName].Dependencies.msb4u.csproj` 。</span><span class="sxs-lookup"><span data-stu-id="4d3b8-152">If this doesn't exist, navigate to the Assets folder in the Project view and select `[ProjectName].Dependencies.msb4u.csproj`.</span></span> <span data-ttu-id="4d3b8-153">假設第1部分成功，應該會有一個具有組建、重建和清除按鈕的自訂偵測器。</span><span class="sxs-lookup"><span data-stu-id="4d3b8-153">Assuming part 1 did succeed, there should be a custom inspector with Build, Rebuild, and Clean buttons.</span></span> <span data-ttu-id="4d3b8-154">請嘗試按一下 [建立] 或 [重建]，然後重新搜尋 DotNetWinRT.dll。</span><span class="sxs-lookup"><span data-stu-id="4d3b8-154">Try clicking Build or Rebuild, and then re-search for DotNetWinRT.dll.</span></span> <span data-ttu-id="4d3b8-155">如果該 DLL 現在存在，這個步驟就會成功。</span><span class="sxs-lookup"><span data-stu-id="4d3b8-155">If that DLL now exists, this step succeeded.</span></span>

![DotNetAdapter 偵測器](../Images/Tools/Remoting/DotNetAdapterInspector.png)

#### <a name="dotnetadaptercsproj-missing"></a><span data-ttu-id="4d3b8-157">DotNetAdapter 缺少 .csproj</span><span class="sxs-lookup"><span data-stu-id="4d3b8-157">DotNetAdapter.csproj missing</span></span>

<span data-ttu-id="4d3b8-158">如果上一個步驟失敗，最好再次檢查您專案中是否有適當的 .csproj。</span><span class="sxs-lookup"><span data-stu-id="4d3b8-158">If the previous step didn't succeed, it's good to double check that the appropriate csproj exists in your project.</span></span> <span data-ttu-id="4d3b8-159">在 [ **MRTK**  /  **提供者**] 下，檢查  /  **WindowsMixedReality**  /  **Shared**  /  **DotNetAdapter** ，並確認 DotNetAdapter .csproj 存在。</span><span class="sxs-lookup"><span data-stu-id="4d3b8-159">Check under **MRTK** / **Providers** / **WindowsMixedReality** / **Shared** / **DotNetAdapter** and confirm that DotNetAdapter.csproj exists.</span></span> <span data-ttu-id="4d3b8-160">如果您的 .gitignore 忽略 .csproj 檔案，而且您已將 MRTK 檔案認可到遠端存放庫，則其中一個常見的情況是此檔案可能不存在。</span><span class="sxs-lookup"><span data-stu-id="4d3b8-160">One common case where this file might not exist is if your .gitignore ignores csproj files and you've committed the MRTK files to a remote repo.</span></span> <span data-ttu-id="4d3b8-161">在此情況下，請確定您已強制新增 DotNetAdapter .csproj， `git add -f [path/to]/DotNetAdapter.csproj` 以確定它會針對所有其他共同作業者或電腦進行認可和複製。</span><span class="sxs-lookup"><span data-stu-id="4d3b8-161">In this case, please make sure you force add DotNetAdapter.csproj with `git add -f [path/to]/DotNetAdapter.csproj` to make sure it gets committed and cloned for all other collaborators or computers.</span></span>

#### <a name="dotnetwinrt_present-define-written-into-player-settings"></a><span data-ttu-id="4d3b8-162">DOTNETWINRT_PRESENT 定義寫入播放機設定</span><span class="sxs-lookup"><span data-stu-id="4d3b8-162">DOTNETWINRT_PRESENT define written into player settings</span></span>

<span data-ttu-id="4d3b8-163">從 MRTK 版本2.5.0 開始，基於效能的考慮，不再自動設定此 #define。</span><span class="sxs-lookup"><span data-stu-id="4d3b8-163">Beginning with MRTK version 2.5.0, for performance reasons, this #define is no longer automatically set.</span></span> <span data-ttu-id="4d3b8-164">若要啟用此旗標，請使用 **Mixed Reality** 工具組  >  **公用程式**  >  **Windows Mixed Reality**  >  **檢查** 設定功能表項目。</span><span class="sxs-lookup"><span data-stu-id="4d3b8-164">To enable this flag, please use the **Mixed Reality Toolkit** > **Utilities** > **Windows Mixed Reality** > **Check Configuration** menu item.</span></span>

> [!Note]
> <span data-ttu-id="4d3b8-165">檢查設定專案不會顯示確認。</span><span class="sxs-lookup"><span data-stu-id="4d3b8-165">The Check Configuration item does not display a confirmation.</span></span> <span data-ttu-id="4d3b8-166">若要確認已設定定義，請流覽至 Unity Player 設定。</span><span class="sxs-lookup"><span data-stu-id="4d3b8-166">To confirm that the define has been set, please navigate to the Unity Player Settings.</span></span> <span data-ttu-id="4d3b8-167">從該處的 [UWP] 索引標籤底下，檢查腳本定義符號的其他設定。</span><span class="sxs-lookup"><span data-stu-id="4d3b8-167">From there, under the UWP tab, check under Other Settings for the Scripting Define Symbols.</span></span> <span data-ttu-id="4d3b8-168">請確定已在該清單中正確寫入 DOTNETWINRT_PRESENT。</span><span class="sxs-lookup"><span data-stu-id="4d3b8-168">Make sure DOTNETWINRT_PRESENT is properly written in that list.</span></span> <span data-ttu-id="4d3b8-169">如果有的話，這個步驟就成功了。</span><span class="sxs-lookup"><span data-stu-id="4d3b8-169">If that's there, this step succeeded.</span></span>

![DotNetWinRT 存在](../Images/Tools/Remoting/DotNetWinRTPresent.png)

#### <a name="failure-to-find-dotnetexe"></a><span data-ttu-id="4d3b8-171">找不到 dotnet.exe 的問題</span><span class="sxs-lookup"><span data-stu-id="4d3b8-171">Failure to find dotnet.exe</span></span>

<span data-ttu-id="4d3b8-172">適用于 Unity 的 MSBuild 取決於系統路徑中現有的 dotnet.exe，dotnet.exe 必須安裝並存在於 PATH 環境變數中。</span><span class="sxs-lookup"><span data-stu-id="4d3b8-172">MSBuild for Unity depends on dotnet.exe existing in the system path - dotnet.exe must both be installed and present in the PATH environment variable.</span></span> <span data-ttu-id="4d3b8-173">如果這兩項需求都不成立，Unity 主控台可能會出現此錯誤：</span><span class="sxs-lookup"><span data-stu-id="4d3b8-173">If neither of those requirements are true, this error may manifest in the Unity console:</span></span>

```cmd
Win32Exception: ApplicationName='dotnet', CommandLine='msbuild DotNetAdapter.csproj -restore  -v:minimal -p:NuGetInteractive=true  -t:Build -p:Configuration=Release -nologo', CurrentDirectory='C:\src\Assets\MRTK\Providers\WindowsMixedReality\Shared\DotNetAdapter', Native error= The system cannot find the file specified.
```

<span data-ttu-id="4d3b8-174">解決方法是確保 [安裝 .NET Core CLI 的工具](https://docs.microsoft.com/dotnet/core/tools/?tabs=netcore2x) ，並重新啟動系統，以強制所有應用程式取得重新整理的系統路徑。</span><span class="sxs-lookup"><span data-stu-id="4d3b8-174">The solution to this is to ensure that the [.NET Core CLI tools are installed](https://docs.microsoft.com/dotnet/core/tools/?tabs=netcore2x) and reboot the system to force all apps to get a refreshed system path.</span></span>

<span data-ttu-id="4d3b8-175">如果在執行上述步驟之後，透過遠端處理的操作仍無法運作，則在裝置上的一般操作設定檔中可能會有設定不正確的問題。</span><span class="sxs-lookup"><span data-stu-id="4d3b8-175">If hand joints over remoting are still not working after following the above steps, there might be something misconfigured in the profiles for general hand joints on-device.</span></span> <span data-ttu-id="4d3b8-176">在此情況下，請與 [我們的其中一個說明資源聯繫](../../WelcomeToMRTK.md#getting-help)。</span><span class="sxs-lookup"><span data-stu-id="4d3b8-176">In that case, please [reach out on one of our help resources](../../WelcomeToMRTK.md#getting-help).</span></span>

#### <a name="manual-dotnetadapter-installation"></a><span data-ttu-id="4d3b8-177">手動 DotNetAdapter 安裝</span><span class="sxs-lookup"><span data-stu-id="4d3b8-177">Manual DotNetAdapter installation</span></span>

<span data-ttu-id="4d3b8-178">如果無法透過 MSBuild for Unity 執行 DotNetAdapter 安裝，則可以執行下列步驟。</span><span class="sxs-lookup"><span data-stu-id="4d3b8-178">In the event that the installation of the DotNetAdapter cannot be performed via MSBuild for Unity, the following steps can be performed.</span></span>

> [!Important]
> <span data-ttu-id="4d3b8-179">不支援同時使用適用于 Unity 的 MSBuild 和相同專案中的另一個 NuGet 用戶端，因此可能會導致相依性解析問題。</span><span class="sxs-lookup"><span data-stu-id="4d3b8-179">Using both MSBuild for Unity and another NuGet client within the same project is not supported and can result in potential dependency resolution issues.</span></span>

1. <span data-ttu-id="4d3b8-180">安裝 NuGet 用戶端</span><span class="sxs-lookup"><span data-stu-id="4d3b8-180">Install a NuGet client</span></span>

    > [!Note]
    > <span data-ttu-id="4d3b8-181">下列指示假設使用 [適用于 Unity 的 NuGet](https://github.com/GlitchEnzo/NuGetForUnity/releases)</span><span class="sxs-lookup"><span data-stu-id="4d3b8-181">The following instructions presume use of [NuGet for Unity](https://github.com/GlitchEnzo/NuGetForUnity/releases)</span></span>

1. <span data-ttu-id="4d3b8-182">流覽至 NuGet 用戶端 UI</span><span class="sxs-lookup"><span data-stu-id="4d3b8-182">Navigate to the NuGet client UI</span></span>

    ![啟動 NuGet UI](../Images/Tools/Remoting/LaunchNuGetForUnity.png)

1. <span data-ttu-id="4d3b8-184">找出 `Microsoft.Windows.MixedReality.DotNetWinRT` 套件</span><span class="sxs-lookup"><span data-stu-id="4d3b8-184">Locate the `Microsoft.Windows.MixedReality.DotNetWinRT` package</span></span>

    ![尋找套件](../Images/Tools/Remoting/LocateDotNetWinRT.png)

1. <span data-ttu-id="4d3b8-186">選取安裝</span><span class="sxs-lookup"><span data-stu-id="4d3b8-186">Select Install</span></span>

### <a name="removing-hololens-2-specific-remoting-support"></a><span data-ttu-id="4d3b8-187">移除 HoloLens 2 特定的遠端支援</span><span class="sxs-lookup"><span data-stu-id="4d3b8-187">Removing HoloLens 2-specific remoting support</span></span>

<span data-ttu-id="4d3b8-188">如果您因為 DotNetWinRT 介面卡的存在而遇到衝突或其他問題，請前往 [我們的其中一個說明資源](../../WelcomeToMRTK.md#getting-help)。</span><span class="sxs-lookup"><span data-stu-id="4d3b8-188">If you're running into conflicts or other issues due to the presence of the DotNetWinRT adapter, please [reach out on one of our help resources](../../WelcomeToMRTK.md#getting-help).</span></span>

<span data-ttu-id="4d3b8-189">您也可以透過下列步驟，暫時移除介面卡以因應您的問題：</span><span class="sxs-lookup"><span data-stu-id="4d3b8-189">You can also temporarily remove the adapter to workaround your issue via the following steps:</span></span>

1. <span data-ttu-id="4d3b8-190">在 Unity 中，移至視窗-> 封裝管理員並卸載適用于 Unity 的 MSBuild。</span><span class="sxs-lookup"><span data-stu-id="4d3b8-190">In Unity, go to Window -> Package Manager and uninstall MSBuild for Unity.</span></span>
1. <span data-ttu-id="4d3b8-191">在 Unity 的 [資產] 清單中搜尋 DotNetWinRT.dll，並刪除 DLL 或刪除 (MRTK 2.2 或舊版) 的外掛程式，或刪除 (MRTK 2.3 或更新版本或更新版本) 資料夾，其中包含幾個層級。</span><span class="sxs-lookup"><span data-stu-id="4d3b8-191">Search for DotNetWinRT.dll in your assets list in Unity and either delete the DLL or delete the Plugins (MRTK 2.2 or earlier) or Dependencies (MRTK 2.3 or later) folder that contains it a few levels up.</span></span> <span data-ttu-id="4d3b8-192">這應該會移除這些衝突的命名空間，同時保持 MRTK。</span><span class="sxs-lookup"><span data-stu-id="4d3b8-192">That should remove these conflicting namespaces, while keeping MRTK around.</span></span>
1. <span data-ttu-id="4d3b8-193"> (選擇性) 在您的檔案瀏覽器中流覽至 MRTK/Providers/WindowsMixedReality/Shared/DotNetAdapter， (不是 Unity 的資產視圖) 並刪除 `.bin` 和 `.obj` 資料夾。</span><span class="sxs-lookup"><span data-stu-id="4d3b8-193">(Optional) Navigate to MRTK / Providers / WindowsMixedReality / Shared / DotNetAdapter in your file explorer (not Unity's Assets view) and delete the `.bin` and `.obj` folders.</span></span> <span data-ttu-id="4d3b8-194">這會移除 DotNetWinRT 的 NuGet 還原套件的本機快取。</span><span class="sxs-lookup"><span data-stu-id="4d3b8-194">This removes the local cache of NuGet restored packages for DotNetWinRT.</span></span>
1. <span data-ttu-id="4d3b8-195">如果您再次執行 MRTK 配置器，請確定您不會重新啟用適用于 Unity 的 MSBuild。</span><span class="sxs-lookup"><span data-stu-id="4d3b8-195">If you run the MRTK Configurator again, make sure you don't re-enable MSBuild for Unity.</span></span>

## <a name="xr-sdk-setup-instructions"></a><span data-ttu-id="4d3b8-196">XR SDK 安裝指示</span><span class="sxs-lookup"><span data-stu-id="4d3b8-196">XR SDK setup instructions</span></span>

<span data-ttu-id="4d3b8-197">遵循 [[開始使用 MRTK 和 XR SDK] 頁面上的 Windows Mixed Reality 設定指示](../../configuration/GettingStartedWithMRTKAndXRSDK.md#windows-mixed-reality) ，並務必執行編輯器前 HoloLens 遠端處理所需的步驟。</span><span class="sxs-lookup"><span data-stu-id="4d3b8-197">Follow the [Windows Mixed Reality setup instructions on the Getting started with MRTK and XR SDK page](../../configuration/GettingStartedWithMRTKAndXRSDK.md#windows-mixed-reality) and make sure to perform the step required for in-editor HoloLens Remoting.</span></span>

## <a name="connecting-to-the-hololens-with-wi-fi"></a><span data-ttu-id="4d3b8-198">使用 Wi-Fi 連接到 HoloLens</span><span class="sxs-lookup"><span data-stu-id="4d3b8-198">Connecting to the HoloLens with Wi-Fi</span></span>

<span data-ttu-id="4d3b8-199">設定好專案之後，就可以建立 HoloLens 的連接。</span><span class="sxs-lookup"><span data-stu-id="4d3b8-199">Once the project has been configured, a connection can be established to the HoloLens.</span></span>

1. <span data-ttu-id="4d3b8-200">在 [檔案 **> 組建設定**] 中，確定 [專案組建類型] 已設定為 [ **通用 Windows 平臺**</span><span class="sxs-lookup"><span data-stu-id="4d3b8-200">In **File > Build Settings**, ensure that the project build type is set to **Universal Windows Platform**</span></span>
1. <span data-ttu-id="4d3b8-201">在 HoloLens 上啟動全像 **遠端處理** 應用程式。</span><span class="sxs-lookup"><span data-stu-id="4d3b8-201">On the HoloLens, launch the **Holographic Remoting** application.</span></span>
1. <span data-ttu-id="4d3b8-202">在 Unity 中，如果使用 **XR SDK (，請選取 Window > XR (> 全像 XR) /WINDOWS XR 外掛程式遠端處理)**。</span><span class="sxs-lookup"><span data-stu-id="4d3b8-202">In Unity, select **Window > XR > Holographic Emulation (if using legacy XR) / Windows XR Plugin Remoting (if using XR SDK)**.</span></span>

    ![開始全像模擬](../Images/Tools/Remoting/StartHolographicEmulation.png)

1. <span data-ttu-id="4d3b8-204">將 **模擬模式** 設定為 [ **遠端裝置**]。</span><span class="sxs-lookup"><span data-stu-id="4d3b8-204">Set **Emulation Mode** to **Remote to Device**.</span></span>

    ![設定模擬模式](../Images/Tools/Remoting/SelectEmulationMode.png)

1. <span data-ttu-id="4d3b8-206"> (**_僅適用于舊版 XR_**) 選取 **裝置版本**。</span><span class="sxs-lookup"><span data-stu-id="4d3b8-206">(**_Only applies to legacy XR_**) Select the **Device Version**.</span></span>

    ![選取裝置版本](../Images/Tools/Remoting/SelectDeviceVersion.png)

1. <span data-ttu-id="4d3b8-208">使用「全像遠端播放播放程式」應用程式所顯示的 IP 位址，設定 [ **遠端電腦** ] 欄位。</span><span class="sxs-lookup"><span data-stu-id="4d3b8-208">Using the IP Address displayed by the Holographic Remoting Player application, set the **Remote Machine** field.</span></span>

    ![輸入 IP 位址](../Images/Tools/Remoting/EnterIPAddress.png)

1. <span data-ttu-id="4d3b8-210">按一下 [連線]。</span><span class="sxs-lookup"><span data-stu-id="4d3b8-210">Click **Connect**.</span></span>

> [!NOTE]
> <span data-ttu-id="4d3b8-211">如果您無法連線，請確定您的 HoloLens 2 未插入電腦並重新啟動 Unity。</span><span class="sxs-lookup"><span data-stu-id="4d3b8-211">If you cannot connect, make sure your HoloLens 2 is not plugged in to your PC and restart Unity.</span></span>

## <a name="connecting-to-the-hololens-with-usb-cable"></a><span data-ttu-id="4d3b8-212">使用 USB 纜線連接到 HoloLens</span><span class="sxs-lookup"><span data-stu-id="4d3b8-212">Connecting to the HoloLens with USB cable</span></span>

<span data-ttu-id="4d3b8-213">USB 纜線連接可提供更佳的轉譯品質和穩定性。</span><span class="sxs-lookup"><span data-stu-id="4d3b8-213">USB cable connection gives better rendering quality and stability.</span></span> <span data-ttu-id="4d3b8-214">若要使用 USB 纜線連線，請從 Wi-Fi HoloLens 與 HoloLens 的設定中斷連線，並啟動全像遠端播放機應用程式。</span><span class="sxs-lookup"><span data-stu-id="4d3b8-214">To use USB cable connection, disconnect from the HoloLens from Wi-Fi in HoloLens's Settings and launch Holographic Remoting Player app.</span></span> <span data-ttu-id="4d3b8-215">它會顯示開頭為169的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="4d3b8-215">It will display an IP address that starts with 169.</span></span> <span data-ttu-id="4d3b8-216">在 Unity 的全像模擬設定中使用此 IP 位址來連接。</span><span class="sxs-lookup"><span data-stu-id="4d3b8-216">Use this IP address in Unity's Holographic Emulation setting to connect.</span></span> <span data-ttu-id="4d3b8-217">一旦識別出 USB 纜線的 IP 位址之後，就可以安全地將 HoloLens 連接到 Wi-Fi。</span><span class="sxs-lookup"><span data-stu-id="4d3b8-217">Once the IP address for USB cable has been identified, it is safe to connect the HoloLens to Wi-Fi again.</span></span>

## <a name="starting-a-remoting-session"></a><span data-ttu-id="4d3b8-218">啟動遠端會話</span><span class="sxs-lookup"><span data-stu-id="4d3b8-218">Starting a remoting session</span></span>

<span data-ttu-id="4d3b8-219">將 Unity 連接到 HoloLens 之後，請在編輯器中輸入播放模式。</span><span class="sxs-lookup"><span data-stu-id="4d3b8-219">With Unity connected to the HoloLens, enter play mode in the editor.</span></span>

<span data-ttu-id="4d3b8-220">當會話完成時，結束播放模式。</span><span class="sxs-lookup"><span data-stu-id="4d3b8-220">When the session is complete, exit play mode.</span></span>

> [!NOTE]
> <span data-ttu-id="4d3b8-221">有一些 Unity 版本的已知問題，在遠端會話期間，編輯器可能會在進入播放模式時停止回應。</span><span class="sxs-lookup"><span data-stu-id="4d3b8-221">There is a known issue with some versions of Unity where the editor may hang upon entering play mode during a remoting session.</span></span> <span data-ttu-id="4d3b8-222">如果在載入專案時，全像全像是開啟的全像是，就會發生此問題。</span><span class="sxs-lookup"><span data-stu-id="4d3b8-222">This issue may manifest if the Holographic window is open when the project is loaded.</span></span> <span data-ttu-id="4d3b8-223">若要確保不會發生此問題，請一律在離開 Unity 之前關閉全像的對話方塊。</span><span class="sxs-lookup"><span data-stu-id="4d3b8-223">To ensure this issue does not occur, always close the Holographic dialog prior to exiting Unity.</span></span>

## <a name="see-also"></a><span data-ttu-id="4d3b8-224">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4d3b8-224">See also</span></span>

- [<span data-ttu-id="4d3b8-225">全像遠端的疑難排解和限制</span><span class="sxs-lookup"><span data-stu-id="4d3b8-225">Holographic Remoting troubleshooting and limitations</span></span>](https://docs.microsoft.com/windows/mixed-reality/holographic-remoting-troubleshooting)
- [<span data-ttu-id="4d3b8-226">Microsoft 全像遠端軟體授權條款</span><span class="sxs-lookup"><span data-stu-id="4d3b8-226">Microsoft Holographic Remoting software license terms</span></span>](https://docs.microsoft.com/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
