---
ms.openlocfilehash: ad8f4a5ea9bda7915731f879da96cf7e007c58fb
ms.sourcegitcommit: 4bb5544a0c74ac4e9766bab3401c9b30ee170a71
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2020
ms.locfileid: "92755650"
---
# <a name="unity"></a>[<span data-ttu-id="b0347-101">Unity</span><span class="sxs-lookup"><span data-stu-id="b0347-101">Unity</span></span>](#tab/unity)

![Unity 標誌橫幅](../images/unity_logo_banner.png)<br>

### <a name="1-download-the-latest-version"></a><span data-ttu-id="b0347-103">1.下載最新版本</span><span class="sxs-lookup"><span data-stu-id="b0347-103">1. Download the latest version</span></span>

<span data-ttu-id="b0347-104">建議 [Unity LTS (長期支援)](https://unity3d.com/unity/qa/lts-releases) 資料流作為用來啟動新專案的最佳版本，並更新為其最新修訂版本，以挑選最新穩定的修正程式。</span><span class="sxs-lookup"><span data-stu-id="b0347-104">We recommend the [Unity LTS (Long Term Support)](https://unity3d.com/unity/qa/lts-releases) stream as the best version to use when starting new projects, updating to its latest revision to pick up the latest stable fixes.</span></span>
* <span data-ttu-id="b0347-105">目前建議使用 **Unity 2019** ，這是以下 MRTK v2 所需的 LTS 組建。</span><span class="sxs-lookup"><span data-stu-id="b0347-105">The current recommendation is to use **Unity 2019** , which is the LTS build required for MRTK v2 below.</span></span>
* <span data-ttu-id="b0347-106">如果您基於特定理由而需要使用不同的 Unity 版本，Unity 支援不同版本的並存安裝。</span><span class="sxs-lookup"><span data-stu-id="b0347-106">If you need to use a different version of Unity for specific reasons, Unity supports side-by-side installs of different versions.</span></span>

### <a name="2-import-mixed-reality-toolkit-mrtk"></a><span data-ttu-id="b0347-107">2.匯入混合實境工具組 (MRTK)</span><span class="sxs-lookup"><span data-stu-id="b0347-107">2. Import Mixed Reality Toolkit (MRTK)</span></span>
![MRTK](../../design/images/MRTK_UX_Hero.png)

<span data-ttu-id="b0347-109">[混合實境工具組](../unity/mrtk-getting-started.md) (MRTK) 是混合實境應用程式的開放原始碼跨平台開發套件。</span><span class="sxs-lookup"><span data-stu-id="b0347-109">[Mixed Reality Toolkit](../unity/mrtk-getting-started.md) (MRTK) is an open-source, cross-platform development kit for mixed reality applications.</span></span> <span data-ttu-id="b0347-110">MRTK 提供跨平台輸入系統、基礎元件，以及空間互動的常見基本要素。</span><span class="sxs-lookup"><span data-stu-id="b0347-110">MRTK provides a cross-platform input system, foundational components, and common building blocks for spatial interactions.</span></span> <span data-ttu-id="b0347-111">該工具組主要用於加速開發以 Microsoft HoloLens、Windows Mixed Reality 沈浸式 (VR) 頭戴裝置和 OpenVR 平台為目標的應用程式。</span><span class="sxs-lookup"><span data-stu-id="b0347-111">The toolkit is intended to accelerate the development of applications targeting Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets, and the OpenVR platform.</span></span>

<span data-ttu-id="b0347-112">進行安裝時，建議您完成我們策劃的 [Unity 開發旅程圖](../unity/unity-development-overview.md)的[開始使用一節](../unity/unity-development-overview.md#1-getting-started)。</span><span class="sxs-lookup"><span data-stu-id="b0347-112">For installation, we recommend completing the [Getting Started section](../unity/unity-development-overview.md#1-getting-started) of our curated [Unity development journey](../unity/unity-development-overview.md).</span></span> <span data-ttu-id="b0347-113">依循 Unity 開發旅程，接下來請完成下列其餘的設定步驟，並繼續進行 [HoloLens 2 開始使用教學課程](../unity/tutorials/mr-learning-base-01.md)。</span><span class="sxs-lookup"><span data-stu-id="b0347-113">If you're already following the Unity development journey, finish up the rest of the setup steps listed below and continue on to the [HoloLens 2 Getting Started tutorials](../unity/tutorials/mr-learning-base-01.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b0347-114">請注意，安裝指示的適用標的為 MRTK 和 Unity 最新的穩定版本組合，也就是 **MRTK 2.4.0** 和 **Unity 2019.3.15** 。</span><span class="sxs-lookup"><span data-stu-id="b0347-114">Note that installation instructions are targeted for the latest stable combination of MRTK and Unity releases, which are **MRTK 2.4.0** and **Unity 2019.3.15**.</span></span>

> [!NOTE]
> <span data-ttu-id="b0347-115">如果您不想使用適用於 Unity 的 MRTK，則必須自行撰寫所有互動和行為的指令碼。</span><span class="sxs-lookup"><span data-stu-id="b0347-115">If you don't want to use MRTK for Unity, you'll need to script all interactions and behaviors yourself.</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="b0347-116"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">![Unity 橫幅](../images/MRTK-Unity-Banner.png)</span><span class="sxs-lookup"><span data-stu-id="b0347-116"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">![Unity banner](../images/MRTK-Unity-Banner.png)</span></span><br><span data-ttu-id="b0347-117">**混合實境工具組-Unity (GitHub)** </a></span><span class="sxs-lookup"><span data-stu-id="b0347-117">**Mixed Reality Toolkit-Unity (GitHub)**</a></span></span><br>
    :::column-end:::
:::row-end:::

#### <a name="other-tools-optional"></a><span data-ttu-id="b0347-118">其他工具 [選用]</span><span class="sxs-lookup"><span data-stu-id="b0347-118">Other tools [optional]</span></span>
* <span data-ttu-id="b0347-119"><a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">混合實境配套工具組 (GitHub)</a> - 無法直接在 HoloLens 或沈浸式 (VR) 頭戴裝置上執行的程式碼位元和元件，但是將其搭配使用可打造以 Windows Mixed Reality 為目標的體驗。</span><span class="sxs-lookup"><span data-stu-id="b0347-119"><a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">Mixed Reality Companion Kit (GitHub)</a> - code bits and components that might not run directly on HoloLens or immersive (VR) headsets, but instead pair with them to build experiences targeting Windows Mixed Reality.</span></span>
* <span data-ttu-id="b0347-120"><a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">混合的現實工具組 - 通用 (GitHub)</a> - 共用指令碼和元件的集合。</span><span class="sxs-lookup"><span data-stu-id="b0347-120"><a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">Mixed Reality Toolkit - Common (GitHub)</a> - a collection of shared scripts and components.</span></span>

### <a name="3-set-up-your-pc-for-mixed-reality-development"></a><span data-ttu-id="b0347-121">3.設定您的電腦以便進行混合實境開發</span><span class="sxs-lookup"><span data-stu-id="b0347-121">3. Set up your PC for Mixed Reality development</span></span>

<span data-ttu-id="b0347-122">Windows 10 SDK 最適合用於 Windows 10 作業系統。</span><span class="sxs-lookup"><span data-stu-id="b0347-122">The Windows 10 SDK works best on the Windows 10 operating system.</span></span> <span data-ttu-id="b0347-123">Windows 8.1、Windows 8、Windows 7、Windows Server 2012、Windows Server 2008 R2 也支援此 SDK。</span><span class="sxs-lookup"><span data-stu-id="b0347-123">This SDK is also supported on Windows 8.1, Windows 8, Windows 7, Windows Server 2012, Windows Server 2008 R2.</span></span> <span data-ttu-id="b0347-124">請注意，舊版作業系統不支援所有工具。</span><span class="sxs-lookup"><span data-stu-id="b0347-124">Note that not all tools are supported on older operating systems.</span></span>

> [!NOTE]
> <span data-ttu-id="b0347-125">您可以針對 HoloLens、VR 沉浸式頭戴裝置或兩者開發及部署應用程式。</span><span class="sxs-lookup"><span data-stu-id="b0347-125">You can develop and deploy your apps for HoloLens, VR immersive headsets, or both.</span></span> <span data-ttu-id="b0347-126">視您的需求而定，請確定您符合下列需求。</span><span class="sxs-lookup"><span data-stu-id="b0347-126">Make sure you fulfill the requirements below depending on your needs.</span></span>

#### <a name="for-hololens-development"></a><span data-ttu-id="b0347-127">對於 HoloLens 開發</span><span class="sxs-lookup"><span data-stu-id="b0347-127">For HoloLens development</span></span>

<span data-ttu-id="b0347-128">設定您的開發電腦以便進行 HoloLens 開發時，請確定其同時符合 <a href="https://unity3d.com/unity/system-requirements" target="_blank">Unity</a> 和 <a href="https://docs.microsoft.com//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a> 的系統需求。</span><span class="sxs-lookup"><span data-stu-id="b0347-128">When setting up your development PC for HoloLens development, please make sure it meets the system requirements for both <a href="https://unity3d.com/unity/system-requirements" target="_blank">Unity</a> and <a href="https://docs.microsoft.com//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a>.</span></span> <span data-ttu-id="b0347-129">如果您打算使用 [HoloLens 模擬器](../platform-capabilities-and-apis/using-the-hololens-emulator.md)，您應確定您的電腦也符合 [HoloLens 模擬器系統需求](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements)。</span><span class="sxs-lookup"><span data-stu-id="b0347-129">If you plan on using the [HoloLens emulator](../platform-capabilities-and-apis/using-the-hololens-emulator.md), you'll want to make sure your PC meets the [HoloLens emulator system requirements](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements) as well.</span></span>

<span data-ttu-id="b0347-130">若要開始使用 HoloLens 模擬器，請參閱[使用 HoloLens 模擬器](../platform-capabilities-and-apis/using-the-hololens-emulator.md)。</span><span class="sxs-lookup"><span data-stu-id="b0347-130">To get started with the HoloLens emulator, see [Using the HoloLens emulator](../platform-capabilities-and-apis/using-the-hololens-emulator.md).</span></span>

<span data-ttu-id="b0347-131">如果您打算針對 HoloLens 與 Windows Mixed Reality 沈浸式 (VR) 頭戴裝置進行開發，請使用下一節中的系統建議和需求。</span><span class="sxs-lookup"><span data-stu-id="b0347-131">If you plan to develop for both HoloLens and Windows Mixed Reality immersive (VR) headsets, use the system recommendations and requirements in the section below.</span></span>

#### <a name="immersive-vr-headset-requirements"></a><span data-ttu-id="b0347-132">沈浸式 (VR) 頭戴式裝置需求</span><span class="sxs-lookup"><span data-stu-id="b0347-132">Immersive (VR) headset requirements</span></span>

>[!NOTE]
><span data-ttu-id="b0347-133">下列指導方針是沈浸式 (VR) 頭戴裝置「開發電腦」目前的最低建議規格，而且會定期更新。</span><span class="sxs-lookup"><span data-stu-id="b0347-133">The following guidelines are the current minimum and recommended specs for your immersive (VR) headset *development PC* , and are updated regularly.</span></span>

>[!WARNING]
><span data-ttu-id="b0347-134">請勿將此指導方針與[最低電腦硬體相容性指導方針](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)混淆，其中概述了沈浸式 (VR) 頭戴裝置應用程式或遊戲應該定向的「取用者電腦規格」。</span><span class="sxs-lookup"><span data-stu-id="b0347-134">Do not confuse this with the [minimum PC hardware compatibility guidelines](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines), which outlines the *consumer PC specs* to which you should target your immersive (VR) headset app or game.</span></span>

<span data-ttu-id="b0347-135">如果您使用 **Reverb G2** 頭戴式裝置，請下載 **Microsoft-Valve OpenXR** 外掛程式 (TODO: //需要連結)。</span><span class="sxs-lookup"><span data-stu-id="b0347-135">If you're using a **Reverb G2** headset, download the **Microsoft-Valve OpenXR** plugin (TODO: // Need link).</span></span>

<span data-ttu-id="b0347-136">如果沉浸式頭戴裝置開發電腦沒有完整大小的 HDMI 和/或 USB 3.0 連接埠，您需要[配接器](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs)才能連線頭戴式裝置。</span><span class="sxs-lookup"><span data-stu-id="b0347-136">If your immersive headset development PC does not have full-sized HDMI and/or USB 3.0 ports, you'll need [adapters](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs) to connect your headset.</span></span>

<span data-ttu-id="b0347-137">目前某些硬體設定有[已知問題](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)，尤其是具有混合式圖形的筆記型電腦。</span><span class="sxs-lookup"><span data-stu-id="b0347-137">There are currently [known issues](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality) with some hardware configurations, particularly notebooks that have hybrid graphics.</span></span>

<table>
<tr>
<th></th><th> <span data-ttu-id="b0347-138">最低需求</span><span class="sxs-lookup"><span data-stu-id="b0347-138">Minimum</span></span></th><th> <span data-ttu-id="b0347-139">建議</span><span class="sxs-lookup"><span data-stu-id="b0347-139">Recommended</span></span></th>
</tr><tr>
<td> <span data-ttu-id="b0347-140">處理器</span><span class="sxs-lookup"><span data-stu-id="b0347-140">Processor</span></span></td><td> <span data-ttu-id="b0347-141"><b>筆記型電腦：</b>Intel Mobile Core i5 第 7 代 CPU、採用超執行緒技術的雙核心 <b>傳統型：</b>Intel Desktop i5 第 6 代 CPU、採用超執行緒技術的雙核心<b>或</b> AMD FX4350 4.2Ghz 四核心對等項目</span><span class="sxs-lookup"><span data-stu-id="b0347-141"><b>Notebook:</b> Intel Mobile Core i5 7th generation CPU, Dual-Core with Hyper Threading <b>Desktop:</b> Intel Desktop i5 6th generation CPU, Dual-Core with Hyper Threading <b>OR</b> AMD FX4350 4.2Ghz Quad-Core equivalent</span></span></td><td> <span data-ttu-id="b0347-142"><b>傳統型：</b>Intel Desktop i7 第 6 代 (6 核心) <b>或</b> AMD Ryzen 5 1600 (6 核心，12 個執行緒)</span><span class="sxs-lookup"><span data-stu-id="b0347-142"><b>Desktop:</b> Intel Desktop i7 6th generation (6 Core) <b>OR</b> AMD Ryzen 5 1600 (6 Core, 12 threads)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="b0347-143">GPU</span><span class="sxs-lookup"><span data-stu-id="b0347-143">GPU</span></span></td><td> <span data-ttu-id="b0347-144"><b>筆記型電腦：</b>NVIDIA GTX 965M、AMD RX 460M (2GB) 對等項目或更高的 DX12 支援 GPU <b>傳統型：</b>NVIDIA GTX 960/1050、AMD Radeon RX 460 (2GB) 對等項目或更高的 DX12 支援 GPU</span><span class="sxs-lookup"><span data-stu-id="b0347-144"><b>Notebook:</b> NVIDIA GTX 965M, AMD RX 460M (2GB) equivalent or greater DX12 capable GPU <b>Desktop:</b> NVIDIA GTX 960/1050, AMD Radeon RX 460 (2GB) equivalent or greater DX12 capable GPU</span></span></td><td><span data-ttu-id="b0347-145"><b>傳統型：</b>NVIDIA GTX 980/1060、AMD Radeon RX 480 (2GB) 對等項目或更高的 DX12 支援 GPU</span><span class="sxs-lookup"><span data-stu-id="b0347-145"><b>Desktop:</b> NVIDIA GTX 980/1060, AMD Radeon RX 480 (2GB) equivalent or greater DX12 capable GPU</span></span></td>
</tr><tr>
<td> <span data-ttu-id="b0347-146">GPU 驅動程式 WDDM 版本</span><span class="sxs-lookup"><span data-stu-id="b0347-146">GPU driver WDDM version</span></span></td><td colspan="2"> <span data-ttu-id="b0347-147">WDDM 2.2 驅動程式</span><span class="sxs-lookup"><span data-stu-id="b0347-147">WDDM 2.2 driver</span></span></td>
</tr><tr>
<td> <span data-ttu-id="b0347-148">散熱設計功率</span><span class="sxs-lookup"><span data-stu-id="b0347-148">Thermal Design Power</span></span></td><td colspan="2"> <span data-ttu-id="b0347-149">15W 或更大</span><span class="sxs-lookup"><span data-stu-id="b0347-149">15W or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="b0347-150">圖形顯示連接埠</span><span class="sxs-lookup"><span data-stu-id="b0347-150">Graphics display ports</span></span></td><td colspan="2"> <span data-ttu-id="b0347-151">適用於頭戴式裝置的 1x 可用圖形顯示連接埠 (適用於 60Hz 頭戴式裝置的 HDMI 1.4 或 DisplayPort 1.2，適用於 90Hz 頭戴式裝置的 HDMI 2.0 或 DisplayPort 1.2)</span><span class="sxs-lookup"><span data-stu-id="b0347-151">1x available graphics display port for&#160;headset (HDMI 1.4 or DisplayPort 1.2 for 60Hz headsets, HDMI 2.0 or DisplayPort 1.2 for 90Hz headsets)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="b0347-152">顯示器解析度</span><span class="sxs-lookup"><span data-stu-id="b0347-152">Display resolution</span></span></td><td colspan="2"> <span data-ttu-id="b0347-153">解決方法：SVGA (800 x 600) 或更大的位元深度：每像素 32 位元的色彩</span><span class="sxs-lookup"><span data-stu-id="b0347-153">Resolution: SVGA (800x600) or greater Bit depth: 32 bits of color per pixel</span></span></td>
</tr><tr>
<td> <span data-ttu-id="b0347-154">Memory</span><span class="sxs-lookup"><span data-stu-id="b0347-154">Memory</span></span></td><td> <span data-ttu-id="b0347-155">8&#160;GB RAM 或更大</span><span class="sxs-lookup"><span data-stu-id="b0347-155">8&#160;GB of RAM or greater</span></span></td><td> <span data-ttu-id="b0347-156">16 GB RAM 或更大</span><span class="sxs-lookup"><span data-stu-id="b0347-156">16 GB of RAM or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="b0347-157">存放裝置</span><span class="sxs-lookup"><span data-stu-id="b0347-157">Storage</span></span></td><td colspan="2"> <span data-ttu-id="b0347-158">&gt;10 GB 額外可用空間</span><span class="sxs-lookup"><span data-stu-id="b0347-158">&gt;10 GB additional free space</span></span></td>
</tr><tr>
<td> <span data-ttu-id="b0347-159">USB 連接埠</span><span class="sxs-lookup"><span data-stu-id="b0347-159">USB Ports</span></span></td><td colspan="2"> <span data-ttu-id="b0347-160">適用於頭戴式裝置的 1x 可用 USB 連接埠 (USB 3.0 Type-A) <b>注意：USB 必須提供至少 900mA</b></span><span class="sxs-lookup"><span data-stu-id="b0347-160">1x available USB port for headset (USB 3.0 Type-A) <b>Note: USB must supply a minimum of 900mA</b></span></span></td>
</tr><tr>
<td> <span data-ttu-id="b0347-161">Bluetooth</span><span class="sxs-lookup"><span data-stu-id="b0347-161">Bluetooth</span></span></td><td colspan="2"> <span data-ttu-id="b0347-162">Bluetooth 4.0 (適用於周邊連線)</span><span class="sxs-lookup"><span data-stu-id="b0347-162">Bluetooth 4.0 (for accessory connectivity)</span></span></td>
</tr>
</table>

<span data-ttu-id="b0347-163">如果您是首次使用 Unity 進行 MRTK 開發，建議您依循我們策劃的 Unity 開發旅程：</span><span class="sxs-lookup"><span data-stu-id="b0347-163">If you're new to MRTK development with Unity, we recommend following our curated Unity development journey:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="b0347-164">開始您的 Unity 旅程</span><span class="sxs-lookup"><span data-stu-id="b0347-164">Start your Unity journey</span></span>](../unity/unity-development-overview.md)

## <a name="next-development-checkpoint"></a><span data-ttu-id="b0347-165">下一個開發檢查點</span><span class="sxs-lookup"><span data-stu-id="b0347-165">Next Development Checkpoint</span></span>

<span data-ttu-id="b0347-166">依循我們配置的 Unity 開發檢查點旅程，您的下一個工作將是進行 HoloLens 2 教學課程系列。</span><span class="sxs-lookup"><span data-stu-id="b0347-166">If you're following the Unity development checkpoint journey we've laid out, your next task is to work through our HoloLens 2 tutorial series.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="b0347-167">HoloLens 2 教學課程系列</span><span class="sxs-lookup"><span data-stu-id="b0347-167">HoloLens 2 tutorial series</span></span>](../unity/tutorials/mr-learning-base-01.md)

<span data-ttu-id="b0347-168">您可以隨時回到 [Unity 開發檢查點](../unity/unity-development-overview.md#1-getting-started)。</span><span class="sxs-lookup"><span data-stu-id="b0347-168">You can always go back to the [Unity development checkpoints](../unity/unity-development-overview.md#1-getting-started) at any time.</span></span>

# <a name="unreal"></a>[<span data-ttu-id="b0347-169">Unreal</span><span class="sxs-lookup"><span data-stu-id="b0347-169">Unreal</span></span>](#tab/unreal)

![Unreal](../images/unreal_logo_banner.png)

### <a name="1-download-the-latest-version"></a><span data-ttu-id="b0347-171">1.下載最新版本</span><span class="sxs-lookup"><span data-stu-id="b0347-171">1. Download the latest version</span></span>

<span data-ttu-id="b0347-172">建議您安裝 [Unreal Engine 4.25 版](https://docs.unrealengine.com//GettingStarted/Installation/index.html)或更新版本，以充分利用內建的 HoloLens 支援。</span><span class="sxs-lookup"><span data-stu-id="b0347-172">We recommend installing [Unreal Engine version 4.25](https://docs.unrealengine.com//GettingStarted/Installation/index.html) or later to take full advantage of built-in HoloLens support.</span></span>

### <a name="2-import-mixed-reality-toolkit-mrtk"></a><span data-ttu-id="b0347-173">2.匯入混合實境工具組 (MRTK)</span><span class="sxs-lookup"><span data-stu-id="b0347-173">2. Import Mixed Reality Toolkit (MRTK)</span></span>
![MRTK](../../design/images/MRTK_UX_Hero.png)

<span data-ttu-id="b0347-175">混合實境工具組 (MRTK) 是混合實境應用程式的開放原始碼跨平台開發套件。</span><span class="sxs-lookup"><span data-stu-id="b0347-175">Mixed Reality Toolkit (MRTK) is an open-source, cross-platform development kit for mixed reality applications.</span></span> <span data-ttu-id="b0347-176">MRTK 提供跨平台輸入系統、基礎元件，以及空間互動的常見基本要素。</span><span class="sxs-lookup"><span data-stu-id="b0347-176">MRTK provides a cross-platform input system, foundational components, and common building blocks for spatial interactions.</span></span> <span data-ttu-id="b0347-177">該工具組主要用於加速開發以 Microsoft HoloLens、Windows Mixed Reality 沈浸式 (VR) 頭戴裝置和 OpenVR 平台為目標的應用程式。</span><span class="sxs-lookup"><span data-stu-id="b0347-177">The toolkit is intended to accelerate the development of applications targeting Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets, and the OpenVR platform.</span></span>

<span data-ttu-id="b0347-178">進行安裝時，建議您完成我們策劃的 [Unreal 開發旅程圖](../unreal/unreal-development-overview.md)的[開始使用一節](../unreal/unreal-development-overview.md#1-getting-started)。</span><span class="sxs-lookup"><span data-stu-id="b0347-178">For installation, we recommend completing the [Getting Started section](../unreal/unreal-development-overview.md#1-getting-started) of our curated [Unreal development journey](../unreal/unreal-development-overview.md).</span></span> <span data-ttu-id="b0347-179">依循 Unreal 開發旅程，接下來請完成下列其餘的設定步驟，並繼續進行 [HoloLens 2 開始使用教學課程](../unreal/tutorials/unreal-uxt-ch1.md)。</span><span class="sxs-lookup"><span data-stu-id="b0347-179">If you're already following the Unreal development journey, finish up the rest of the setup steps listed below and continue on to the [HoloLens 2 Getting Started tutorials](../unreal/tutorials/unreal-uxt-ch1.md).</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="b0347-180"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unreal" target="_blank">![Unity 標誌影像](../images/MRTK-Unreal-Banner.png)</span><span class="sxs-lookup"><span data-stu-id="b0347-180"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unreal" target="_blank">![Unity logo image](../images/MRTK-Unreal-Banner.png)</span></span><br><span data-ttu-id="b0347-181">**混合實境工具組-Unreal (GitHub)** </a></span><span class="sxs-lookup"><span data-stu-id="b0347-181">**Mixed Reality Toolkit-Unreal (GitHub)**</a></span></span><br>
    :::column-end:::
:::row-end:::

> [!NOTE]
> <span data-ttu-id="b0347-182">如果您不想使用適用於 Unreal 的 MRTK，則必須自行撰寫所有互動和行為的指令碼。</span><span class="sxs-lookup"><span data-stu-id="b0347-182">If you don't want to use MRTK for Unreal, you'll need to script all interactions and behaviors yourself.</span></span>

#### <a name="other-tools-optional"></a><span data-ttu-id="b0347-183">其他工具 [選用]</span><span class="sxs-lookup"><span data-stu-id="b0347-183">Other tools [optional]</span></span>
* <span data-ttu-id="b0347-184"><a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">混合實境配套工具組 (GitHub)</a> - 無法直接在 HoloLens 或沈浸式 (VR) 頭戴裝置上執行的程式碼位元和元件，但是將其搭配使用可打造以 Windows Mixed Reality 為目標的體驗。</span><span class="sxs-lookup"><span data-stu-id="b0347-184"><a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">Mixed Reality Companion Kit (GitHub)</a> - code bits and components that might not run directly on HoloLens or immersive (VR) headsets, but instead pair with them to build experiences targeting Windows Mixed Reality.</span></span>
* <span data-ttu-id="b0347-185"><a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">混合的現實工具組 - 通用 (GitHub)</a> - 共用指令碼和元件的集合。</span><span class="sxs-lookup"><span data-stu-id="b0347-185"><a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">Mixed Reality Toolkit - Co mmon (GitHub)</a> - a collection of shared scripts and components.</span></span>

### <a name="3-set-up-your-pc-for-mixed-reality-development"></a><span data-ttu-id="b0347-186">3.設定您的電腦以便進行混合實境開發</span><span class="sxs-lookup"><span data-stu-id="b0347-186">3. Set up your PC for mixed reality development</span></span>

<span data-ttu-id="b0347-187">Windows 10 SDK 最適合用於 Windows 10 作業系統。</span><span class="sxs-lookup"><span data-stu-id="b0347-187">The Windows 10 SDK works best on the Windows 10 operating system.</span></span> <span data-ttu-id="b0347-188">Windows 8.1、Windows 8、Windows 7、Windows Server 2012、Windows Server 2008 R2 也支援此 SDK。</span><span class="sxs-lookup"><span data-stu-id="b0347-188">This SDK is also supported on Windows 8.1, Windows 8, Windows 7, Windows Server 2012, Windows Server 2008 R2.</span></span> <span data-ttu-id="b0347-189">請注意，舊版作業系統不支援所有工具。</span><span class="sxs-lookup"><span data-stu-id="b0347-189">Note that not all tools are supported on older operating systems.</span></span>

> [!NOTE]
> <span data-ttu-id="b0347-190">您可以針對 HoloLens、VR 沉浸式頭戴裝置或兩者開發及部署應用程式。</span><span class="sxs-lookup"><span data-stu-id="b0347-190">You can develop and deploy your apps for HoloLens, VR immersive headsets, or both.</span></span> <span data-ttu-id="b0347-191">視您的需求而定，請確定您符合下列需求。</span><span class="sxs-lookup"><span data-stu-id="b0347-191">Make sure you fulfill the requirements below depending on your needs.</span></span>

#### <a name="for-hololens-development"></a><span data-ttu-id="b0347-192">對於 HoloLens 開發</span><span class="sxs-lookup"><span data-stu-id="b0347-192">For HoloLens development</span></span>

<span data-ttu-id="b0347-193">設定您的開發電腦以便進行 HoloLens 開發時，請確定您符合 [Unity](https://docs.unrealengine.com/GettingStarted/RecommendedSpecifications/index.html) 和 <a href="https://docs.microsoft.com//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a> 的系統需求。</span><span class="sxs-lookup"><span data-stu-id="b0347-193">When setting up your development PC for HoloLens development, please make sure you meet the system requirements for [Unreal](https://docs.unrealengine.com/GettingStarted/RecommendedSpecifications/index.html) and and <a href="https://docs.microsoft.com//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a>.</span></span> <span data-ttu-id="b0347-194">如果您打算使用 [HoloLens 模擬器](../platform-capabilities-and-apis/using-the-hololens-emulator.md)，您應確定您的電腦也符合 [HoloLens 模擬器系統需求](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements)。</span><span class="sxs-lookup"><span data-stu-id="b0347-194">If you plan on using the [HoloLens emulator](../platform-capabilities-and-apis/using-the-hololens-emulator.md), you'll want to make sure your PC meets the [HoloLens emulator system requirements](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements) as well.</span></span>

<span data-ttu-id="b0347-195">如果您打算針對 HoloLens 與 Windows Mixed Reality 沈浸式 (VR) 頭戴裝置進行開發，請使用下一節中的系統建議和需求。</span><span class="sxs-lookup"><span data-stu-id="b0347-195">If you plan to develop for both HoloLens and Windows Mixed Reality immersive (VR) headsets, use the system recommendations and requirements in the section below.</span></span>

#### <a name="immersive-vr-headset-requirements"></a><span data-ttu-id="b0347-196">沈浸式 (VR) 頭戴式裝置需求</span><span class="sxs-lookup"><span data-stu-id="b0347-196">Immersive (VR) headset requirements</span></span>

>[!NOTE]
><span data-ttu-id="b0347-197">下列指導方針是沈浸式 (VR) 頭戴裝置「開發電腦」目前的最低建議規格，而且會定期更新。</span><span class="sxs-lookup"><span data-stu-id="b0347-197">The following guidelines are the current minimum and recommended specs for your immersive (VR) headset *development PC* , and are updated regularly.</span></span>

>[!WARNING]
><span data-ttu-id="b0347-198">請勿將此指導方針與[最低電腦硬體相容性指導方針](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)混淆，其中概述了沈浸式 (VR) 頭戴裝置應用程式或遊戲應該定向的「取用者電腦規格」。</span><span class="sxs-lookup"><span data-stu-id="b0347-198">Do not confuse this with the [minimum PC hardware compatibility guidelines](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines), which outlines the *consumer PC specs* to which you should target your immersive (VR) headset app or game.</span></span>

<span data-ttu-id="b0347-199">如果您使用 **Reverb G2** 頭戴式裝置，請下載 **Microsoft-Valve OpenXR** 外掛程式 (TODO: //需要連結)。</span><span class="sxs-lookup"><span data-stu-id="b0347-199">If you're using a **Reverb G2** headset, download the **Microsoft-Valve OpenXR** plugin (TODO: // Need link).</span></span>

<span data-ttu-id="b0347-200">如果沉浸式頭戴裝置開發電腦沒有完整大小的 HDMI 和/或 USB 3.0 連接埠，您需要[配接器](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs)才能連線頭戴式裝置。</span><span class="sxs-lookup"><span data-stu-id="b0347-200">If your immersive headset development PC does not have full-sized HDMI and/or USB 3.0 ports, you'll need [adapters](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs) to connect your headset.</span></span>

<span data-ttu-id="b0347-201">目前某些硬體設定有[已知問題](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)，尤其是具有混合式圖形的筆記型電腦。</span><span class="sxs-lookup"><span data-stu-id="b0347-201">There are currently [known issues](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality) with some hardware configurations, particularly notebooks that have hybrid graphics.</span></span>

<table>
<tr>
<th></th><th> <span data-ttu-id="b0347-202">最低需求</span><span class="sxs-lookup"><span data-stu-id="b0347-202">Minimum</span></span></th><th> <span data-ttu-id="b0347-203">建議</span><span class="sxs-lookup"><span data-stu-id="b0347-203">Recommended</span></span></th>
</tr><tr>
<td> <span data-ttu-id="b0347-204">處理器</span><span class="sxs-lookup"><span data-stu-id="b0347-204">Processor</span></span></td><td> <span data-ttu-id="b0347-205"><b>筆記型電腦：</b>Intel Mobile Core i5 第 7 代 CPU、採用超執行緒技術的雙核心 <b>傳統型：</b>Intel Desktop i5 第 6 代 CPU、採用超執行緒技術的雙核心<b>或</b> AMD FX4350 4.2Ghz 四核心對等項目</span><span class="sxs-lookup"><span data-stu-id="b0347-205"><b>Notebook:</b> Intel Mobile Core i5 7th generation CPU, Dual-Core with Hyper Threading <b>Desktop:</b> Intel Desktop i5 6th generation CPU, Dual-Core with Hyper Threading <b>OR</b> AMD FX4350 4.2Ghz Quad-Core equivalent</span></span></td><td> <span data-ttu-id="b0347-206"><b>傳統型：</b>Intel Desktop i7 第 6 代 (6 核心) <b>或</b> AMD Ryzen 5 1600 (6 核心，12 個執行緒)</span><span class="sxs-lookup"><span data-stu-id="b0347-206"><b>Desktop:</b> Intel Desktop i7 6th generation (6 Core) <b>OR</b> AMD Ryzen 5 1600 (6 Core, 12 threads)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="b0347-207">GPU</span><span class="sxs-lookup"><span data-stu-id="b0347-207">GPU</span></span></td><td> <span data-ttu-id="b0347-208"><b>筆記型電腦：</b>NVIDIA GTX 965M、AMD RX 460M (2GB) 對等項目或更高的 DX12 支援 GPU <b>傳統型：</b>NVIDIA GTX 960/1050、AMD Radeon RX 460 (2GB) 對等項目或更高的 DX12 支援 GPU</span><span class="sxs-lookup"><span data-stu-id="b0347-208"><b>Notebook:</b> NVIDIA GTX 965M, AMD RX 460M (2GB) equivalent or greater DX12 capable GPU <b>Desktop:</b> NVIDIA GTX 960/1050, AMD Radeon RX 460 (2GB) equivalent or greater DX12 capable GPU</span></span></td><td><span data-ttu-id="b0347-209"><b>傳統型：</b>NVIDIA GTX 980/1060、AMD Radeon RX 480 (2GB) 對等項目或更高的 DX12 支援 GPU</span><span class="sxs-lookup"><span data-stu-id="b0347-209"><b>Desktop:</b> NVIDIA GTX 980/1060, AMD Radeon RX 480 (2GB) equivalent or greater DX12 capable GPU</span></span></td>
</tr><tr>
<td> <span data-ttu-id="b0347-210">GPU 驅動程式 WDDM 版本</span><span class="sxs-lookup"><span data-stu-id="b0347-210">GPU driver WDDM version</span></span></td><td colspan="2"> <span data-ttu-id="b0347-211">WDDM 2.2 驅動程式</span><span class="sxs-lookup"><span data-stu-id="b0347-211">WDDM 2.2 driver</span></span></td>
</tr><tr>
<td> <span data-ttu-id="b0347-212">散熱設計功率</span><span class="sxs-lookup"><span data-stu-id="b0347-212">Thermal Design Power</span></span></td><td colspan="2"> <span data-ttu-id="b0347-213">15W 或更大</span><span class="sxs-lookup"><span data-stu-id="b0347-213">15W or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="b0347-214">圖形顯示連接埠</span><span class="sxs-lookup"><span data-stu-id="b0347-214">Graphics display ports</span></span></td><td colspan="2"> <span data-ttu-id="b0347-215">適用於頭戴式裝置的 1x 可用圖形顯示連接埠 (適用於 60Hz 頭戴式裝置的 HDMI 1.4 或 DisplayPort 1.2，適用於 90Hz 頭戴式裝置的 HDMI 2.0 或 DisplayPort 1.2)</span><span class="sxs-lookup"><span data-stu-id="b0347-215">1x available graphics display port for&#160;headset (HDMI 1.4 or DisplayPort 1.2 for 60Hz headsets, HDMI 2.0 or DisplayPort 1.2 for 90Hz headsets)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="b0347-216">顯示器解析度</span><span class="sxs-lookup"><span data-stu-id="b0347-216">Display resolution</span></span></td><td colspan="2"> <span data-ttu-id="b0347-217">解決方法：SVGA (800 x 600) 或更大的位元深度：每像素 32 位元的色彩</span><span class="sxs-lookup"><span data-stu-id="b0347-217">Resolution: SVGA (800x600) or greater Bit depth: 32 bits of color per pixel</span></span></td>
</tr><tr>
<td> <span data-ttu-id="b0347-218">Memory</span><span class="sxs-lookup"><span data-stu-id="b0347-218">Memory</span></span></td><td> <span data-ttu-id="b0347-219">8&#160;GB RAM 或更大</span><span class="sxs-lookup"><span data-stu-id="b0347-219">8&#160;GB of RAM or greater</span></span></td><td> <span data-ttu-id="b0347-220">16 GB RAM 或更大</span><span class="sxs-lookup"><span data-stu-id="b0347-220">16 GB of RAM or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="b0347-221">存放裝置</span><span class="sxs-lookup"><span data-stu-id="b0347-221">Storage</span></span></td><td colspan="2"> <span data-ttu-id="b0347-222">&gt;10 GB 額外可用空間</span><span class="sxs-lookup"><span data-stu-id="b0347-222">&gt;10 GB additional free space</span></span></td>
</tr><tr>
<td> <span data-ttu-id="b0347-223">USB 連接埠</span><span class="sxs-lookup"><span data-stu-id="b0347-223">USB Ports</span></span></td><td colspan="2"> <span data-ttu-id="b0347-224">適用於頭戴式裝置的 1x 可用 USB 連接埠 (USB 3.0 Type-A) <b>注意：USB 必須提供至少 900mA</b></span><span class="sxs-lookup"><span data-stu-id="b0347-224">1x available USB port for headset (USB 3.0 Type-A) <b>Note: USB must supply a minimum of 900mA</b></span></span></td>
</tr><tr>
<td> <span data-ttu-id="b0347-225">Bluetooth</span><span class="sxs-lookup"><span data-stu-id="b0347-225">Bluetooth</span></span></td><td colspan="2"> <span data-ttu-id="b0347-226">Bluetooth 4.0 (適用於周邊連線)</span><span class="sxs-lookup"><span data-stu-id="b0347-226">Bluetooth 4.0 (for accessory connectivity)</span></span></td>
</tr>
</table>

<span data-ttu-id="b0347-227">如果您是首次使用 Unreal 進行 MRTK 開發，建議您依循我們策劃的 Unreal 開發旅程：</span><span class="sxs-lookup"><span data-stu-id="b0347-227">If you're new to MRTK development with Unreal, we recommend following our curated Unreal development journey:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="b0347-228">開始您的 Unreal 旅程</span><span class="sxs-lookup"><span data-stu-id="b0347-228">Start your Unreal journey</span></span>](../unreal/unreal-development-overview.md)

## <a name="next-development-checkpoint"></a><span data-ttu-id="b0347-229">下一個開發檢查點</span><span class="sxs-lookup"><span data-stu-id="b0347-229">Next Development Checkpoint</span></span>

<span data-ttu-id="b0347-230">依循我們配置的 Unreal 開發檢查點旅程，您的下一個工作將是進行 HoloLens 2 教學課程系列。</span><span class="sxs-lookup"><span data-stu-id="b0347-230">If you're following the Unreal development checkpoint journey we've laid out, your next task is to work through our HoloLens 2 tutorial series.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="b0347-231">HoloLens 2 教學課程系列</span><span class="sxs-lookup"><span data-stu-id="b0347-231">HoloLens 2 tutorial series</span></span>](../unreal/tutorials/unreal-uxt-ch1.md)

<span data-ttu-id="b0347-232">您可以隨時回到 [Unreal 開發檢查點](../unreal/unreal-development-overview.md#1-getting-started)。</span><span class="sxs-lookup"><span data-stu-id="b0347-232">You can always go back to the [Unreal development checkpoints](../unreal/unreal-development-overview.md#1-getting-started) at any time.</span></span>

# <a name="native-openxr"></a>[<span data-ttu-id="b0347-233">原生 (OpenXR)</span><span class="sxs-lookup"><span data-stu-id="b0347-233">Native (OpenXR)</span></span>](#tab/native)

 ![原生應用程式開發](../images/native_logo_banner.png)

<span data-ttu-id="b0347-235">原生 OpenXR 開發沒有可供您下載的引擎。</span><span class="sxs-lookup"><span data-stu-id="b0347-235">Native OpenXR development doesn't have an engine for you to download.</span></span> <span data-ttu-id="b0347-236">您可以在[開始使用 OpenXR](../native/openxr-getting-started.md) 文件中找到開始進行開發所需的一切資訊。</span><span class="sxs-lookup"><span data-stu-id="b0347-236">You can find everything you need to begin development in the [Getting started with OpenXR](../native/openxr-getting-started.md) document.</span></span>

### <a name="1-set-up-your-pc-for-mixed-reality-development"></a><span data-ttu-id="b0347-237">1.設定您的電腦以便進行混合實境開發</span><span class="sxs-lookup"><span data-stu-id="b0347-237">1. Set up your PC for mixed reality development</span></span>

<span data-ttu-id="b0347-238">Windows 10 SDK 最適合用於 Windows 10 作業系統。</span><span class="sxs-lookup"><span data-stu-id="b0347-238">The Windows 10 SDK works best on the Windows 10 operating system.</span></span> <span data-ttu-id="b0347-239">Windows 8.1、Windows 8、Windows 7、Windows Server 2012、Windows Server 2008 R2 也支援此 SDK。</span><span class="sxs-lookup"><span data-stu-id="b0347-239">This SDK is also supported on Windows 8.1, Windows 8, Windows 7, Windows Server 2012, Windows Server 2008 R2.</span></span> <span data-ttu-id="b0347-240">請注意，舊版作業系統不支援所有工具。</span><span class="sxs-lookup"><span data-stu-id="b0347-240">Note that not all tools are supported on older operating systems.</span></span>

#### <a name="for-hololens-development"></a><span data-ttu-id="b0347-241">對於 HoloLens 開發</span><span class="sxs-lookup"><span data-stu-id="b0347-241">For HoloLens development</span></span>

<span data-ttu-id="b0347-242">設定您的開發電腦以便進行 HoloLens 開發時，請確定您符合 <a href="https://docs.microsoft.com//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a> 的系統需求。</span><span class="sxs-lookup"><span data-stu-id="b0347-242">When setting up your development PC for HoloLens development, please make sure you meet the system requirements for <a href="https://docs.microsoft.com//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a>.</span></span> <span data-ttu-id="b0347-243">如果您打算使用 [HoloLens 模擬器](../platform-capabilities-and-apis/using-the-hololens-emulator.md)，您應確定您的電腦也符合 [HoloLens 模擬器系統需求](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements)。</span><span class="sxs-lookup"><span data-stu-id="b0347-243">If you plan on using the [HoloLens emulator](../platform-capabilities-and-apis/using-the-hololens-emulator.md), you'll want to make sure your PC meets the [HoloLens emulator system requirements](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements) as well.</span></span>

<span data-ttu-id="b0347-244">如果您打算針對 HoloLens 與 Windows Mixed Reality 沈浸式 (VR) 頭戴裝置進行開發，請使用下一節中的系統建議和需求。</span><span class="sxs-lookup"><span data-stu-id="b0347-244">If you plan to develop for both HoloLens and Windows Mixed Reality immersive (VR) headsets, use the system recommendations and requirements in the section below.</span></span>

> [!NOTE]
> <span data-ttu-id="b0347-245">您可以針對 HoloLens、VR 沉浸式頭戴裝置或兩者開發及部署應用程式。</span><span class="sxs-lookup"><span data-stu-id="b0347-245">You can develop and deploy your apps for HoloLens, VR immersive headsets, or both.</span></span> <span data-ttu-id="b0347-246">視您的需求而定，請確定您符合下列需求。</span><span class="sxs-lookup"><span data-stu-id="b0347-246">Make sure you fulfill the requirements below depending on your needs.</span></span>

#### <a name="immersive-vr-headset-requirements"></a><span data-ttu-id="b0347-247">沈浸式 (VR) 頭戴式裝置需求</span><span class="sxs-lookup"><span data-stu-id="b0347-247">Immersive (VR) headset requirements</span></span>

>[!NOTE]
><span data-ttu-id="b0347-248">下列指導方針是沈浸式 (VR) 頭戴裝置「開發電腦」目前的最低建議規格，而且會定期更新。</span><span class="sxs-lookup"><span data-stu-id="b0347-248">The following guidelines are the current minimum and recommended specs for your immersive (VR) headset *development PC* , and are updated regularly.</span></span>

>[!WARNING]
><span data-ttu-id="b0347-249">請勿將此指導方針與[最低電腦硬體相容性指導方針](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)混淆，其中概述了沈浸式 (VR) 頭戴裝置應用程式或遊戲應該定向的「取用者電腦規格」。</span><span class="sxs-lookup"><span data-stu-id="b0347-249">Do not confuse this with the [minimum PC hardware compatibility guidelines](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines), which outlines the *consumer PC specs* to which you should target your immersive (VR) headset app or game.</span></span>

<span data-ttu-id="b0347-250">如果沉浸式頭戴裝置開發電腦沒有完整大小的 HDMI 和/或 USB 3.0 連接埠，您需要[配接器](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs)才能連線頭戴式裝置。</span><span class="sxs-lookup"><span data-stu-id="b0347-250">If your immersive headset development PC does not have full-sized HDMI and/or USB 3.0 ports, you'll need [adapters](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs) to connect your headset.</span></span>

<span data-ttu-id="b0347-251">目前某些硬體設定有[已知問題](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)，尤其是具有混合式圖形的筆記型電腦。</span><span class="sxs-lookup"><span data-stu-id="b0347-251">There are currently [known issues](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality) with some hardware configurations, particularly notebooks that have hybrid graphics.</span></span>

<table>
<tr>
<th></th><th> <span data-ttu-id="b0347-252">最低需求</span><span class="sxs-lookup"><span data-stu-id="b0347-252">Minimum</span></span></th><th> <span data-ttu-id="b0347-253">建議</span><span class="sxs-lookup"><span data-stu-id="b0347-253">Recommended</span></span></th>
</tr><tr>
<td> <span data-ttu-id="b0347-254">處理器</span><span class="sxs-lookup"><span data-stu-id="b0347-254">Processor</span></span></td><td> <span data-ttu-id="b0347-255"><b>筆記型電腦：</b>Intel Mobile Core i5 第 7 代 CPU、採用超執行緒技術的雙核心 <b>傳統型：</b>Intel Desktop i5 第 6 代 CPU、採用超執行緒技術的雙核心<b>或</b> AMD FX4350 4.2Ghz 四核心對等項目</span><span class="sxs-lookup"><span data-stu-id="b0347-255"><b>Notebook:</b> Intel Mobile Core i5 7th generation CPU, Dual-Core with Hyper Threading <b>Desktop:</b> Intel Desktop i5 6th generation CPU, Dual-Core with Hyper Threading <b>OR</b> AMD FX4350 4.2Ghz Quad-Core equivalent</span></span></td><td> <span data-ttu-id="b0347-256"><b>傳統型：</b>Intel Desktop i7 第 6 代 (6 核心) <b>或</b> AMD Ryzen 5 1600 (6 核心，12 個執行緒)</span><span class="sxs-lookup"><span data-stu-id="b0347-256"><b>Desktop:</b> Intel Desktop i7 6th generation (6 Core) <b>OR</b> AMD Ryzen 5 1600 (6 Core, 12 threads)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="b0347-257">GPU</span><span class="sxs-lookup"><span data-stu-id="b0347-257">GPU</span></span></td><td> <span data-ttu-id="b0347-258"><b>筆記型電腦：</b>NVIDIA GTX 965M、AMD RX 460M (2GB) 對等項目或更高的 DX12 支援 GPU <b>傳統型：</b>NVIDIA GTX 960/1050、AMD Radeon RX 460 (2GB) 對等項目或更高的 DX12 支援 GPU</span><span class="sxs-lookup"><span data-stu-id="b0347-258"><b>Notebook:</b> NVIDIA GTX 965M, AMD RX 460M (2GB) equivalent or greater DX12 capable GPU <b>Desktop:</b> NVIDIA GTX 960/1050, AMD Radeon RX 460 (2GB) equivalent or greater DX12 capable GPU</span></span></td><td><span data-ttu-id="b0347-259"><b>傳統型：</b>NVIDIA GTX 980/1060、AMD Radeon RX 480 (2GB) 對等項目或更高的 DX12 支援 GPU</span><span class="sxs-lookup"><span data-stu-id="b0347-259"><b>Desktop:</b> NVIDIA GTX 980/1060, AMD Radeon RX 480 (2GB) equivalent or greater DX12 capable GPU</span></span></td>
</tr><tr>
<td> <span data-ttu-id="b0347-260">GPU 驅動程式 WDDM 版本</span><span class="sxs-lookup"><span data-stu-id="b0347-260">GPU driver WDDM version</span></span></td><td colspan="2"> <span data-ttu-id="b0347-261">WDDM 2.2 驅動程式</span><span class="sxs-lookup"><span data-stu-id="b0347-261">WDDM 2.2 driver</span></span></td>
</tr><tr>
<td> <span data-ttu-id="b0347-262">散熱設計功率</span><span class="sxs-lookup"><span data-stu-id="b0347-262">Thermal Design Power</span></span></td><td colspan="2"> <span data-ttu-id="b0347-263">15W 或更大</span><span class="sxs-lookup"><span data-stu-id="b0347-263">15W or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="b0347-264">圖形顯示連接埠</span><span class="sxs-lookup"><span data-stu-id="b0347-264">Graphics display ports</span></span></td><td colspan="2"> <span data-ttu-id="b0347-265">適用於頭戴式裝置的 1x 可用圖形顯示連接埠 (適用於 60Hz 頭戴式裝置的 HDMI 1.4 或 DisplayPort 1.2，適用於 90Hz 頭戴式裝置的 HDMI 2.0 或 DisplayPort 1.2)</span><span class="sxs-lookup"><span data-stu-id="b0347-265">1x available graphics display port for&#160;headset (HDMI 1.4 or DisplayPort 1.2 for 60Hz headsets, HDMI 2.0 or DisplayPort 1.2 for 90Hz headsets)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="b0347-266">顯示器解析度</span><span class="sxs-lookup"><span data-stu-id="b0347-266">Display resolution</span></span></td><td colspan="2"> <span data-ttu-id="b0347-267">解決方法：SVGA (800 x 600) 或更大的位元深度：每像素 32 位元的色彩</span><span class="sxs-lookup"><span data-stu-id="b0347-267">Resolution: SVGA (800x600) or greater Bit depth: 32 bits of color per pixel</span></span></td>
</tr><tr>
<td> <span data-ttu-id="b0347-268">Memory</span><span class="sxs-lookup"><span data-stu-id="b0347-268">Memory</span></span></td><td> <span data-ttu-id="b0347-269">8&#160;GB RAM 或更大</span><span class="sxs-lookup"><span data-stu-id="b0347-269">8&#160;GB of RAM or greater</span></span></td><td> <span data-ttu-id="b0347-270">16 GB RAM 或更大</span><span class="sxs-lookup"><span data-stu-id="b0347-270">16 GB of RAM or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="b0347-271">存放裝置</span><span class="sxs-lookup"><span data-stu-id="b0347-271">Storage</span></span></td><td colspan="2"> <span data-ttu-id="b0347-272">&gt;10 GB 額外可用空間</span><span class="sxs-lookup"><span data-stu-id="b0347-272">&gt;10 GB additional free space</span></span></td>
</tr><tr>
<td> <span data-ttu-id="b0347-273">USB 連接埠</span><span class="sxs-lookup"><span data-stu-id="b0347-273">USB Ports</span></span></td><td colspan="2"> <span data-ttu-id="b0347-274">適用於頭戴式裝置的 1x 可用 USB 連接埠 (USB 3.0 Type-A) <b>注意：USB 必須提供至少 900mA</b></span><span class="sxs-lookup"><span data-stu-id="b0347-274">1x available USB port for headset (USB 3.0 Type-A) <b>Note: USB must supply a minimum of 900mA</b></span></span></td>
</tr><tr>
<td> <span data-ttu-id="b0347-275">Bluetooth</span><span class="sxs-lookup"><span data-stu-id="b0347-275">Bluetooth</span></span></td><td colspan="2"> <span data-ttu-id="b0347-276">Bluetooth 4.0 (適用於周邊連線)</span><span class="sxs-lookup"><span data-stu-id="b0347-276">Bluetooth 4.0 (for accessory connectivity)</span></span></td>
</tr>
</table>

<span data-ttu-id="b0347-277">如果您是首次使用 MRTK 進行原生開發，建議您依循我們策劃的原生開發旅程：</span><span class="sxs-lookup"><span data-stu-id="b0347-277">If you're new to Native development with MRTK, we recommend following our curated Native development journey:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="b0347-278">開始您的原生旅程</span><span class="sxs-lookup"><span data-stu-id="b0347-278">Start your Native journey</span></span>](../native/directx-development-overview.md)

## <a name="next-development-checkpoint"></a><span data-ttu-id="b0347-279">下一個開發檢查點</span><span class="sxs-lookup"><span data-stu-id="b0347-279">Next Development Checkpoint</span></span>

<span data-ttu-id="b0347-280">依循我們配置的 Native 開發檢查點旅程，您的下一個工作將是設定 HoloLens 2 的開發環境。</span><span class="sxs-lookup"><span data-stu-id="b0347-280">If you're following the Native development checkpoint journey we've laid out, your next task is to configure your development environment for HoloLens 2.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="b0347-281">設定 HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="b0347-281">Setup for HoloLens 2</span></span>](../native/openxr-getting-started.md#getting-started-with-openxr-for-hololens-2)

<span data-ttu-id="b0347-282">您可以隨時回到[原生開發檢查點](../native/directx-development-overview.md#1-getting-started)。</span><span class="sxs-lookup"><span data-stu-id="b0347-282">You can always go back to the [Native development checkpoints](../native/directx-development-overview.md#1-getting-started) at any time.</span></span>
