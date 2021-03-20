---
title: HolographicRemoting
description: 檔全像全像遠端 MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: 6d3804134d4b6c0a21aa62468aa39c446de52101
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104685081"
---
# <a name="holographic-remoting"></a><span data-ttu-id="b449b-104">全像攝影遠端處理</span><span class="sxs-lookup"><span data-stu-id="b449b-104">Holographic Remoting</span></span>

<span data-ttu-id="b449b-105">全像是，使用 Wi-Fi 或 USB 纜線連線，全像是即時的遠端處理將電腦上的全息內容串流處理到您的 Microsoft HoloLens。</span><span class="sxs-lookup"><span data-stu-id="b449b-105">Holographic remoting streams holographic content from a PC to your Microsoft HoloLens in real-time, using a Wi-Fi or USB cable connection.</span></span> <span data-ttu-id="b449b-106">當開發混合現實應用程式時，這項功能可以大幅提升開發人員的生產力。</span><span class="sxs-lookup"><span data-stu-id="b449b-106">This feature can significantly increase developer productivity when developing mixed reality applications.</span></span>

<span data-ttu-id="b449b-107">XR SDK （如下所述）是 unity [2019.3 及更高的 unity 新 XR 管線](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/)。</span><span class="sxs-lookup"><span data-stu-id="b449b-107">XR SDK as mentioned below refers to Unity's [new XR pipeline in Unity 2019.3 and beyond](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/).</span></span> <span data-ttu-id="b449b-108">如需搭配使用 XR SDK 與 MRTK 的詳細資訊，請參閱 [這裡](../../configuration/getting-started-with-mrtk-and-xrsdk.md) 。</span><span class="sxs-lookup"><span data-stu-id="b449b-108">See [here](../../configuration/getting-started-with-mrtk-and-xrsdk.md) for more information on using XR SDK with MRTK.</span></span> <span data-ttu-id="b449b-109">舊版 XR 是指 unity 2018 中包含的現有 XR 管線，在 Unity 2019.3 中已被取代，並已在 Unity 2020 中移除。</span><span class="sxs-lookup"><span data-stu-id="b449b-109">Legacy XR refers to the existing XR pipeline that is included in Unity 2018, deprecated in Unity 2019.3 and removed in Unity 2020.</span></span>

## <a name="initial-setup"></a><span data-ttu-id="b449b-110">初始設定</span><span class="sxs-lookup"><span data-stu-id="b449b-110">Initial setup</span></span>

<span data-ttu-id="b449b-111">若要啟用 HoloLens 的遠端功能，請務必確定專案使用的是最新的遠端處理元件。</span><span class="sxs-lookup"><span data-stu-id="b449b-111">To enable remoting to a HoloLens, it is important to ensure that the project is using the latest remoting components.</span></span>

1. <span data-ttu-id="b449b-112">開啟 **視窗 > 封裝管理員**</span><span class="sxs-lookup"><span data-stu-id="b449b-112">Open **Window > Package Manager**</span></span>
    - <span data-ttu-id="b449b-113">如果使用舊版 XR：確認已安裝最新版的 **Windows Mixed Reality** 套件。</span><span class="sxs-lookup"><span data-stu-id="b449b-113">If using legacy XR: Verify that latest version of the **Windows Mixed Reality** package is installed.</span></span>
    - <span data-ttu-id="b449b-114">如果使用 XR SDK：請確認已安裝最新版的 **WINDOWS XR 外掛程式** 套件。</span><span class="sxs-lookup"><span data-stu-id="b449b-114">If using XR SDK: Verify that latest version of the **Windows XR Plugin** package is installed.</span></span>
1. <span data-ttu-id="b449b-115">確定已在 HoloLens 上透過 Microsoft Store 安裝最新的全像全像遠端處理應用程式。</span><span class="sxs-lookup"><span data-stu-id="b449b-115">Ensure the latest Holographic Remoting application is installed, on the HoloLens, via the Microsoft Store.</span></span>

<span data-ttu-id="b449b-116">請根據專案中使用的管線，繼續閱讀 [舊版 XR 安裝指示](#legacy-xr-setup-instructions) 或 [XR SDK 設定指示](#xr-sdk-setup-instructions) 。</span><span class="sxs-lookup"><span data-stu-id="b449b-116">Please continue to [Legacy XR setup instructions](#legacy-xr-setup-instructions) or [XR SDK setup instructions](#xr-sdk-setup-instructions) depending on which pipeline is used in the project.</span></span>

## <a name="legacy-xr-setup-instructions"></a><span data-ttu-id="b449b-117">舊版 XR 安裝指示</span><span class="sxs-lookup"><span data-stu-id="b449b-117">Legacy XR setup instructions</span></span>

<span data-ttu-id="b449b-118">下列指示僅適用于使用 HoloLens 2 的遠端處理。</span><span class="sxs-lookup"><span data-stu-id="b449b-118">The instructions below only apply to remoting with HoloLens 2.</span></span> <span data-ttu-id="b449b-119">如果您只使用 HoloLens (第1代) 進行遠端處理，請跳至 [使用 wi-fi 連線到 hololens](#connecting-to-the-hololens-with-wi-fi)。</span><span class="sxs-lookup"><span data-stu-id="b449b-119">If you only perform remoting with HoloLens (1st Gen), skip to [Connecting to the HoloLens with Wi-Fi](#connecting-to-the-hololens-with-wi-fi).</span></span>

<span data-ttu-id="b449b-120">使用 HoloLens 2 時，已將對遠端的已表達和眼睛追蹤資料的支援新增至 MRTK。</span><span class="sxs-lookup"><span data-stu-id="b449b-120">When using a HoloLens 2, support for remoting articulated hand and eye tracking data has been added to MRTK.</span></span> <span data-ttu-id="b449b-121">若要啟用這些功能，請遵循將 DotNetWinRT 匯 [入到專案](#import-dotnetwinrt-into-the-project)中所述的步驟。</span><span class="sxs-lookup"><span data-stu-id="b449b-121">To enable these features, please follow the steps documented in [Import DotNetWinRT into the project](#import-dotnetwinrt-into-the-project).</span></span>

<span data-ttu-id="b449b-122">匯入之後，下一步是選取 **混合現實工具** 組  >  **公用程式**  >  **Windows Mixed Reality**  >  **檢查** 設定。</span><span class="sxs-lookup"><span data-stu-id="b449b-122">Once imported, the next step is to select **Mixed Reality Toolkit** > **Utilities** > **Windows Mixed Reality** > **Check Configuration**.</span></span> <span data-ttu-id="b449b-123">此步驟會新增可啟用 DotNetWinRT 相依性的腳本定義。</span><span class="sxs-lookup"><span data-stu-id="b449b-123">This step adds a scripting define that enables the DotNetWinRT dependency.</span></span>

> [!NOTE]
> <span data-ttu-id="b449b-124">使用 Unity 2019.4 和更新版本時，不需要執行檢查設定公用程式。</span><span class="sxs-lookup"><span data-stu-id="b449b-124">When using Unity 2019.4 and newer, it is not necessary to run the Check Configuration utility.</span></span>

<span data-ttu-id="b449b-125">若要追蹤手接程式和眼睛追蹤，請依照 **HoloLens 2 透過 Unity 套件匯入** 和相關章節進行的偵錯工具中的步驟進行。</span><span class="sxs-lookup"><span data-stu-id="b449b-125">To enable tracking of hand joints and eye tracking, follow the steps in the **Debugging HoloLens 2 remoting via Unity package import** and related sections.</span></span>

### <a name="debugging-hololens-2-remoting-via-unity-package-import"></a><span data-ttu-id="b449b-126">透過 Unity 套件匯入進行 HoloLens 2 遠端處理的調試</span><span class="sxs-lookup"><span data-stu-id="b449b-126">Debugging HoloLens 2 remoting via Unity package import</span></span>

<span data-ttu-id="b449b-127">如果 HoloLens 2 的手接點和眼睛追蹤未在遠端處理，則有幾個常見的潛在問題點。</span><span class="sxs-lookup"><span data-stu-id="b449b-127">If HoloLens 2 hand joints and eye tracking aren't working over remoting, there are a few common points of potential issues.</span></span> <span data-ttu-id="b449b-128">它們會依應檢查的順序列于下方。</span><span class="sxs-lookup"><span data-stu-id="b449b-128">They're listed below in the order they should be checked.</span></span>

<span data-ttu-id="b449b-129">這些問題在 **Unity 2019.3** 或更新版本上執行時特別相關。</span><span class="sxs-lookup"><span data-stu-id="b449b-129">These issues are particularly relevant when running on **Unity 2019.3** or later.</span></span>

#### <a name="import-dotnetwinrt-into-the-project"></a><span data-ttu-id="b449b-130">將 DotNetWinRT 匯入專案</span><span class="sxs-lookup"><span data-stu-id="b449b-130">Import DotNetWinRT into the project</span></span>

1. <span data-ttu-id="b449b-131">下載 [Mixed Reality 功能工具](https://aka.ms/MRFeatureTool)</span><span class="sxs-lookup"><span data-stu-id="b449b-131">Download the [Mixed Reality Feature Tool](https://aka.ms/MRFeatureTool)</span></span>

1. <span data-ttu-id="b449b-132">在 [**探索功能**] 視圖中，選取 [*混合的事實 WinRT 投影*]</span><span class="sxs-lookup"><span data-stu-id="b449b-132">In the **Discover features** view, select *Mixed Reality WinRT Projections*</span></span>

    ![選取 DotNetWinRT 套件](../images/tools/remoting/SelectDotNetWinRT.png)

1. <span data-ttu-id="b449b-134">按一下 [ **取得功能** ]，然後繼續匯 [入封裝](https://docs.microsoft.com/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool#3-importing-feature-packages)。</span><span class="sxs-lookup"><span data-stu-id="b449b-134">Click **Get Features** and continue to [import the package](https://docs.microsoft.com/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool#3-importing-feature-packages).</span></span>

#### <a name="dotnetwinrt_present-define-written-into-player-settings"></a><span data-ttu-id="b449b-135">DOTNETWINRT_PRESENT 定義寫入播放機設定</span><span class="sxs-lookup"><span data-stu-id="b449b-135">DOTNETWINRT_PRESENT define written into player settings</span></span>

> [!NOTE]
> <span data-ttu-id="b449b-136">使用 Unity 2019.4 和更新版本時，DOTNETWINRT_PRESENT 定義會包含在適當的 asmdef 檔案中，而不是包含在 Unity Player 設定中。</span><span class="sxs-lookup"><span data-stu-id="b449b-136">When using Unity 2019.4 and newer, the DOTNETWINRT_PRESENT define is contained within the appropriate .asmdef files and not the Unity Player Settings.</span></span> <span data-ttu-id="b449b-137">不需要檢查設定步驟。</span><span class="sxs-lookup"><span data-stu-id="b449b-137">The Check Configuration step is not required.</span></span>

<span data-ttu-id="b449b-138">從 MRTK 版本2.5.0 開始，基於效能的考慮，不再自動設定此 #define。</span><span class="sxs-lookup"><span data-stu-id="b449b-138">Beginning with MRTK version 2.5.0, for performance reasons, this #define is no longer automatically set.</span></span> <span data-ttu-id="b449b-139">若要啟用此旗標，請使用 **Mixed Reality** 工具組  >  **公用程式**  >  **Windows Mixed Reality**  >  **檢查** 設定功能表項目。</span><span class="sxs-lookup"><span data-stu-id="b449b-139">To enable this flag, please use the **Mixed Reality Toolkit** > **Utilities** > **Windows Mixed Reality** > **Check Configuration** menu item.</span></span>

> [!Note]
> <span data-ttu-id="b449b-140">檢查設定專案不會顯示確認。</span><span class="sxs-lookup"><span data-stu-id="b449b-140">The Check Configuration item does not display a confirmation.</span></span> <span data-ttu-id="b449b-141">若要確認已設定定義，請流覽至 Unity Player 設定。</span><span class="sxs-lookup"><span data-stu-id="b449b-141">To confirm that the define has been set, please navigate to the Unity Player Settings.</span></span> <span data-ttu-id="b449b-142">從該處的 [UWP] 索引標籤底下，檢查腳本定義符號的其他設定。</span><span class="sxs-lookup"><span data-stu-id="b449b-142">From there, under the UWP tab, check under Other Settings for the Scripting Define Symbols.</span></span> <span data-ttu-id="b449b-143">請確定已在該清單中正確寫入 DOTNETWINRT_PRESENT。</span><span class="sxs-lookup"><span data-stu-id="b449b-143">Make sure DOTNETWINRT_PRESENT is properly written in that list.</span></span> <span data-ttu-id="b449b-144">如果有的話，這個步驟就成功了。</span><span class="sxs-lookup"><span data-stu-id="b449b-144">If that's there, this step succeeded.</span></span>

![DotNetWinRT 存在](../images/tools/remoting/DotNetWinRTPresent.png)

### <a name="removing-hololens-2-specific-remoting-support"></a><span data-ttu-id="b449b-146">移除 HoloLens 2 特定的遠端支援</span><span class="sxs-lookup"><span data-stu-id="b449b-146">Removing HoloLens 2-specific remoting support</span></span>

<span data-ttu-id="b449b-147">如果您因為 DotNetWinRT 介面卡的存在而遇到衝突或其他問題，請前往 [我們的其中一個說明資源](../../index.md#getting-help)。</span><span class="sxs-lookup"><span data-stu-id="b449b-147">If you're running into conflicts or other issues due to the presence of the DotNetWinRT adapter, please [reach out on one of our help resources](../../index.md#getting-help).</span></span>

## <a name="xr-sdk-setup-instructions"></a><span data-ttu-id="b449b-148">XR SDK 安裝指示</span><span class="sxs-lookup"><span data-stu-id="b449b-148">XR SDK setup instructions</span></span>

<span data-ttu-id="b449b-149">遵循 [[開始使用 MRTK 和 XR SDK] 頁面上的 Windows Mixed Reality 設定指示](../../configuration/getting-started-with-mrtk-and-xrsdk.md#windows-mixed-reality) ，並務必執行編輯器前 HoloLens 遠端處理所需的步驟。</span><span class="sxs-lookup"><span data-stu-id="b449b-149">Follow the [Windows Mixed Reality setup instructions on the Getting started with MRTK and XR SDK page](../../configuration/getting-started-with-mrtk-and-xrsdk.md#windows-mixed-reality) and make sure to perform the step required for in-editor HoloLens Remoting.</span></span>

## <a name="connecting-to-the-hololens-with-wi-fi"></a><span data-ttu-id="b449b-150">使用 Wi-Fi 連接到 HoloLens</span><span class="sxs-lookup"><span data-stu-id="b449b-150">Connecting to the HoloLens with Wi-Fi</span></span>

<span data-ttu-id="b449b-151">設定好專案之後，就可以建立 HoloLens 的連接。</span><span class="sxs-lookup"><span data-stu-id="b449b-151">Once the project has been configured, a connection can be established to the HoloLens.</span></span>

1. <span data-ttu-id="b449b-152">在 [檔案 **> 組建設定**] 中，確定 [專案組建類型] 已設定為 [ **通用 Windows 平臺**</span><span class="sxs-lookup"><span data-stu-id="b449b-152">In **File > Build Settings**, ensure that the project build type is set to **Universal Windows Platform**</span></span>
1. <span data-ttu-id="b449b-153">在 HoloLens 上啟動全像 **遠端處理** 應用程式。</span><span class="sxs-lookup"><span data-stu-id="b449b-153">On the HoloLens, launch the **Holographic Remoting** application.</span></span>
1. <span data-ttu-id="b449b-154">在 Unity 中，如果使用 **XR SDK (，請選取 Window > XR (> 全像 XR) /WINDOWS XR 外掛程式遠端處理)**。</span><span class="sxs-lookup"><span data-stu-id="b449b-154">In Unity, select **Window > XR > Holographic Emulation (if using legacy XR) / Windows XR Plugin Remoting (if using XR SDK)**.</span></span>

    ![開始全像模擬](../images/tools/remoting/StartHolographicEmulation.png)

1. <span data-ttu-id="b449b-156">將 **模擬模式** 設定為 [ **遠端裝置**]。</span><span class="sxs-lookup"><span data-stu-id="b449b-156">Set **Emulation Mode** to **Remote to Device**.</span></span>

    ![設定模擬模式](../images/tools/remoting/SelectEmulationMode.png)

1. <span data-ttu-id="b449b-158"> (**_僅適用于舊版 XR_**) 選取 **裝置版本**。</span><span class="sxs-lookup"><span data-stu-id="b449b-158">(**_Only applies to legacy XR_**) Select the **Device Version**.</span></span>

    ![選取裝置版本](../images/tools/remoting/SelectDeviceVersion.png)

1. <span data-ttu-id="b449b-160">使用「全像遠端播放播放程式」應用程式所顯示的 IP 位址，設定 [ **遠端電腦** ] 欄位。</span><span class="sxs-lookup"><span data-stu-id="b449b-160">Using the IP Address displayed by the Holographic Remoting Player application, set the **Remote Machine** field.</span></span>

    ![輸入 IP 位址](../images/tools/remoting/EnterIPAddress.png)

1. <span data-ttu-id="b449b-162">按一下 [連線]。</span><span class="sxs-lookup"><span data-stu-id="b449b-162">Click **Connect**.</span></span>

> [!NOTE]
> <span data-ttu-id="b449b-163">如果您無法連線，請確定您的 HoloLens 2 未插入電腦並重新啟動 Unity。</span><span class="sxs-lookup"><span data-stu-id="b449b-163">If you cannot connect, make sure your HoloLens 2 is not plugged in to your PC and restart Unity.</span></span>

## <a name="connecting-to-the-hololens-with-usb-cable"></a><span data-ttu-id="b449b-164">使用 USB 纜線連接到 HoloLens</span><span class="sxs-lookup"><span data-stu-id="b449b-164">Connecting to the HoloLens with USB cable</span></span>

<span data-ttu-id="b449b-165">USB 纜線連接可提供更佳的轉譯品質和穩定性。</span><span class="sxs-lookup"><span data-stu-id="b449b-165">USB cable connection gives better rendering quality and stability.</span></span> <span data-ttu-id="b449b-166">若要使用 USB 纜線連線，請從 Wi-Fi HoloLens 與 HoloLens 的設定中斷連線，並啟動全像遠端播放機應用程式。</span><span class="sxs-lookup"><span data-stu-id="b449b-166">To use USB cable connection, disconnect from the HoloLens from Wi-Fi in HoloLens's Settings and launch Holographic Remoting Player app.</span></span> <span data-ttu-id="b449b-167">它會顯示開頭為169的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="b449b-167">It will display an IP address that starts with 169.</span></span> <span data-ttu-id="b449b-168">在 Unity 的全像模擬設定中使用此 IP 位址來連接。</span><span class="sxs-lookup"><span data-stu-id="b449b-168">Use this IP address in Unity's Holographic Emulation setting to connect.</span></span> <span data-ttu-id="b449b-169">一旦識別出 USB 纜線的 IP 位址之後，就可以安全地將 HoloLens 連接到 Wi-Fi。</span><span class="sxs-lookup"><span data-stu-id="b449b-169">Once the IP address for USB cable has been identified, it is safe to connect the HoloLens to Wi-Fi again.</span></span>

## <a name="starting-a-remoting-session"></a><span data-ttu-id="b449b-170">啟動遠端會話</span><span class="sxs-lookup"><span data-stu-id="b449b-170">Starting a remoting session</span></span>

<span data-ttu-id="b449b-171">將 Unity 連接到 HoloLens 之後，請在編輯器中輸入播放模式。</span><span class="sxs-lookup"><span data-stu-id="b449b-171">With Unity connected to the HoloLens, enter play mode in the editor.</span></span>

<span data-ttu-id="b449b-172">當會話完成時，結束播放模式。</span><span class="sxs-lookup"><span data-stu-id="b449b-172">When the session is complete, exit play mode.</span></span>

> [!NOTE]
> <span data-ttu-id="b449b-173">有一些 Unity 版本的已知問題，在遠端會話期間，編輯器可能會在進入播放模式時停止回應。</span><span class="sxs-lookup"><span data-stu-id="b449b-173">There is a known issue with some versions of Unity where the editor may hang upon entering play mode during a remoting session.</span></span> <span data-ttu-id="b449b-174">如果在載入專案時，全像全像是開啟的全像是，就會發生此問題。</span><span class="sxs-lookup"><span data-stu-id="b449b-174">This issue may manifest if the Holographic window is open when the project is loaded.</span></span> <span data-ttu-id="b449b-175">若要確保不會發生此問題，請一律在離開 Unity 之前關閉全像的對話方塊。</span><span class="sxs-lookup"><span data-stu-id="b449b-175">To ensure this issue does not occur, always close the Holographic dialog prior to exiting Unity.</span></span>

## <a name="see-also"></a><span data-ttu-id="b449b-176">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b449b-176">See also</span></span>

- [<span data-ttu-id="b449b-177">全像遠端的疑難排解和限制</span><span class="sxs-lookup"><span data-stu-id="b449b-177">Holographic Remoting troubleshooting and limitations</span></span>](https://docs.microsoft.com/windows/mixed-reality/holographic-remoting-troubleshooting)
- [<span data-ttu-id="b449b-178">Microsoft 全像遠端軟體授權條款</span><span class="sxs-lookup"><span data-stu-id="b449b-178">Microsoft Holographic Remoting software license terms</span></span>](https://docs.microsoft.com/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
