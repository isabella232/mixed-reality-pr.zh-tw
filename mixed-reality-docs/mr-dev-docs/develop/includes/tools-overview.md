---
ms.openlocfilehash: cd6541dd651573f31ddc2e2a388be53394059c5f
ms.sourcegitcommit: f459c7deb254409fd5db3967bcc875bcbc367e77
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/10/2020
ms.locfileid: "94482409"
---
# <a name="unity"></a>[<span data-ttu-id="bda05-101">Unity</span><span class="sxs-lookup"><span data-stu-id="bda05-101">Unity</span></span>](#tab/unity)

![Unity 標誌橫幅](../images/unity_logo_banner.png)<br>

### <a name="1-download-the-latest-version"></a><span data-ttu-id="bda05-103">1.下載最新版本</span><span class="sxs-lookup"><span data-stu-id="bda05-103">1. Download the latest version</span></span>

<span data-ttu-id="bda05-104">建議 [Unity LTS (長期支援)](https://unity3d.com/unity/qa/lts-releases) 資料流作為用來啟動新專案的最佳版本，並更新為其最新修訂版本，以挑選最新穩定的修正程式。</span><span class="sxs-lookup"><span data-stu-id="bda05-104">We recommend the [Unity LTS (Long Term Support)](https://unity3d.com/unity/qa/lts-releases) stream as the best version to use when starting new projects, updating to its latest revision to pick up the latest stable fixes.</span></span>
* <span data-ttu-id="bda05-105">目前建議使用 **Unity 2019**，這是以下 MRTK v2 所需的 LTS 組建。</span><span class="sxs-lookup"><span data-stu-id="bda05-105">The current recommendation is to use **Unity 2019**, which is the LTS build required for MRTK v2 below.</span></span>
* <span data-ttu-id="bda05-106">如果您基於特定理由而需要使用不同的 Unity 版本，Unity 支援不同版本的並存安裝。</span><span class="sxs-lookup"><span data-stu-id="bda05-106">If you need to use a different version of Unity for specific reasons, Unity supports side-by-side installs of different versions.</span></span>

### <a name="2-import-mixed-reality-toolkit-mrtk"></a><span data-ttu-id="bda05-107">2.匯入混合實境工具組 (MRTK)</span><span class="sxs-lookup"><span data-stu-id="bda05-107">2. Import Mixed Reality Toolkit (MRTK)</span></span>
![MRTK](../../design/images/MRTK_UX_Hero.png)

<span data-ttu-id="bda05-109">[混合實境工具組](../unity/mrtk-getting-started.md) (MRTK) 是混合實境應用程式的開放原始碼跨平台開發套件。</span><span class="sxs-lookup"><span data-stu-id="bda05-109">[Mixed Reality Toolkit](../unity/mrtk-getting-started.md) (MRTK) is an open-source, cross-platform development kit for mixed reality applications.</span></span> <span data-ttu-id="bda05-110">MRTK 提供跨平台輸入系統、基礎元件，以及空間互動的常見基本要素。</span><span class="sxs-lookup"><span data-stu-id="bda05-110">MRTK provides a cross-platform input system, foundational components, and common building blocks for spatial interactions.</span></span> <span data-ttu-id="bda05-111">該工具組主要用於加速開發以 Microsoft HoloLens、Windows Mixed Reality 沈浸式 (VR) 頭戴裝置和 OpenVR 平台為目標的應用程式。</span><span class="sxs-lookup"><span data-stu-id="bda05-111">The toolkit is intended to accelerate the development of applications targeting Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets, and the OpenVR platform.</span></span>

<span data-ttu-id="bda05-112">進行安裝時，建議您完成我們策劃的 [Unity 開發旅程圖](../unity/unity-development-overview.md)的[開始使用一節](../unity/unity-development-overview.md#1-getting-started)。</span><span class="sxs-lookup"><span data-stu-id="bda05-112">For installation, we recommend completing the [Getting Started section](../unity/unity-development-overview.md#1-getting-started) of our curated [Unity development journey](../unity/unity-development-overview.md).</span></span> <span data-ttu-id="bda05-113">依循 Unity 開發旅程，接下來請完成下列其餘的設定步驟，並繼續進行 [HoloLens 2 開始使用教學課程](../unity/tutorials/mr-learning-base-01.md)。</span><span class="sxs-lookup"><span data-stu-id="bda05-113">If you're already following the Unity development journey, finish up the rest of the setup steps listed below and continue on to the [HoloLens 2 Getting Started tutorials](../unity/tutorials/mr-learning-base-01.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bda05-114">請注意，安裝指示的適用標的為 MRTK 和 Unity 最新的穩定版本組合，也就是 **MRTK 2.4.0** 和 **Unity 2019.3.15**。</span><span class="sxs-lookup"><span data-stu-id="bda05-114">Note that installation instructions are targeted for the latest stable combination of MRTK and Unity releases, which are **MRTK 2.4.0** and **Unity 2019.3.15**.</span></span>

> [!NOTE]
> <span data-ttu-id="bda05-115">如果您不想使用適用於 Unity 的 MRTK，則必須自行撰寫所有互動和行為的指令碼。</span><span class="sxs-lookup"><span data-stu-id="bda05-115">If you don't want to use MRTK for Unity, you'll need to script all interactions and behaviors yourself.</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="bda05-116"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">![Unity 橫幅](../images/MRTK-Unity-Banner.png)</span><span class="sxs-lookup"><span data-stu-id="bda05-116"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">![Unity banner](../images/MRTK-Unity-Banner.png)</span></span><br><span data-ttu-id="bda05-117">**混合實境工具組-Unity (GitHub)** </a></span><span class="sxs-lookup"><span data-stu-id="bda05-117">**Mixed Reality Toolkit-Unity (GitHub)**</a></span></span><br>
    :::column-end:::
:::row-end:::

#### <a name="other-tools-optional"></a><span data-ttu-id="bda05-118">其他工具 [選用]</span><span class="sxs-lookup"><span data-stu-id="bda05-118">Other tools [optional]</span></span>
* <span data-ttu-id="bda05-119"><a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">混合實境配套工具組 (GitHub)</a> - 無法直接在 HoloLens 或沈浸式 (VR) 頭戴裝置上執行的程式碼位元和元件，但是將其搭配使用可打造以 Windows Mixed Reality 為目標的體驗。</span><span class="sxs-lookup"><span data-stu-id="bda05-119"><a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">Mixed Reality Companion Kit (GitHub)</a> - code bits and components that might not run directly on HoloLens or immersive (VR) headsets, but instead pair with them to build experiences targeting Windows Mixed Reality.</span></span>
* <span data-ttu-id="bda05-120"><a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">混合的現實工具組 - 通用 (GitHub)</a> - 共用指令碼和元件的集合。</span><span class="sxs-lookup"><span data-stu-id="bda05-120"><a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">Mixed Reality Toolkit - Common (GitHub)</a> - a collection of shared scripts and components.</span></span>

### <a name="3-set-up-your-pc-for-mixed-reality-development"></a><span data-ttu-id="bda05-121">3.設定您的電腦以便進行混合實境開發</span><span class="sxs-lookup"><span data-stu-id="bda05-121">3. Set up your PC for Mixed Reality development</span></span>

<span data-ttu-id="bda05-122">Windows 10 SDK 最適合用於 Windows 10 作業系統。</span><span class="sxs-lookup"><span data-stu-id="bda05-122">The Windows 10 SDK works best on the Windows 10 operating system.</span></span> <span data-ttu-id="bda05-123">Windows 8.1、Windows 8、Windows 7、Windows Server 2012、Windows Server 2008 R2 也支援此 SDK。</span><span class="sxs-lookup"><span data-stu-id="bda05-123">This SDK is also supported on Windows 8.1, Windows 8, Windows 7, Windows Server 2012, Windows Server 2008 R2.</span></span> <span data-ttu-id="bda05-124">請注意，舊版作業系統不支援所有工具。</span><span class="sxs-lookup"><span data-stu-id="bda05-124">Note that not all tools are supported on older operating systems.</span></span>

> [!NOTE]
> <span data-ttu-id="bda05-125">您可以針對 HoloLens、VR 沉浸式頭戴裝置或兩者開發及部署應用程式。</span><span class="sxs-lookup"><span data-stu-id="bda05-125">You can develop and deploy your apps for HoloLens, VR immersive headsets, or both.</span></span> <span data-ttu-id="bda05-126">視您的需求而定，請確定您符合下列需求。</span><span class="sxs-lookup"><span data-stu-id="bda05-126">Make sure you fulfill the requirements below depending on your needs.</span></span>

#### <a name="for-hololens-development"></a><span data-ttu-id="bda05-127">對於 HoloLens 開發</span><span class="sxs-lookup"><span data-stu-id="bda05-127">For HoloLens development</span></span>

<span data-ttu-id="bda05-128">設定您的開發電腦以便進行 HoloLens 開發時，請確定其同時符合 <a href="https://unity3d.com/unity/system-requirements" target="_blank">Unity</a> 和 <a href="https://docs.microsoft.com//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a> 的系統需求。</span><span class="sxs-lookup"><span data-stu-id="bda05-128">When setting up your development PC for HoloLens development, please make sure it meets the system requirements for both <a href="https://unity3d.com/unity/system-requirements" target="_blank">Unity</a> and <a href="https://docs.microsoft.com//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a>.</span></span> <span data-ttu-id="bda05-129">如果您想要在 HoloLens 裝置上執行您的應用程式，則必須遵循 [Windows 裝置入口網站安裝指示](../platform-capabilities-and-apis/using-the-windows-device-portal.md#setting-up-hololens-to-use-windows-device-portal)。</span><span class="sxs-lookup"><span data-stu-id="bda05-129">If you want to run your app on a HoloLens device, you need to follow the [Windows Device Portal setup instructions](../platform-capabilities-and-apis/using-the-windows-device-portal.md#setting-up-hololens-to-use-windows-device-portal).</span></span> <span data-ttu-id="bda05-130">如果您打算使用 [HoloLens 模擬器](../platform-capabilities-and-apis/using-the-hololens-emulator.md)，您應確定您的電腦也符合 [HoloLens 模擬器系統需求](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements)。</span><span class="sxs-lookup"><span data-stu-id="bda05-130">If you plan on using the [HoloLens emulator](../platform-capabilities-and-apis/using-the-hololens-emulator.md), you'll want to make sure your PC meets the [HoloLens emulator system requirements](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements) as well.</span></span>

<span data-ttu-id="bda05-131">若要開始使用 HoloLens 模擬器，請參閱[使用 HoloLens 模擬器](../platform-capabilities-and-apis/using-the-hololens-emulator.md)。</span><span class="sxs-lookup"><span data-stu-id="bda05-131">To get started with the HoloLens emulator, see [Using the HoloLens emulator](../platform-capabilities-and-apis/using-the-hololens-emulator.md).</span></span>

<span data-ttu-id="bda05-132">如果您打算針對 HoloLens 與 Windows Mixed Reality 沈浸式 (VR) 頭戴裝置進行開發，請使用下一節中的系統建議和需求。</span><span class="sxs-lookup"><span data-stu-id="bda05-132">If you plan to develop for both HoloLens and Windows Mixed Reality immersive (VR) headsets, use the system recommendations and requirements in the section below.</span></span>

#### <a name="hololens-troubleshooting"></a><span data-ttu-id="bda05-133">HoloLens 疑難排解</span><span class="sxs-lookup"><span data-stu-id="bda05-133">HoloLens troubleshooting</span></span>

##### <a name="setting-developer-mode-is-grayed-out"></a><span data-ttu-id="bda05-134">設定開發人員模式呈現灰色</span><span class="sxs-lookup"><span data-stu-id="bda05-134">Setting Developer Mode is grayed out</span></span>

<span data-ttu-id="bda05-135">如果您在裝置上啟用開發人員模式時遇到問題，您可能不是[裝置擁有者](https://docs.microsoft.com/hololens/security-adminless-os)。</span><span class="sxs-lookup"><span data-stu-id="bda05-135">If you're running into issues enabling Developer Mode on your device you might not be the [device owner](https://docs.microsoft.com/hololens/security-adminless-os).</span></span> <span data-ttu-id="bda05-136">在多使用者模式中，第一個使用裝置的人員就是裝置擁有者，任何後續的使用者都不會擁有啟用 [開發人員模式] 或其他組態變更所需的權限。</span><span class="sxs-lookup"><span data-stu-id="bda05-136">In multi-user mode, the person who uses the device first is the device owner - any subsequent users won't have the required permissions to enable Developer Mode or other configuration changes.</span></span> <span data-ttu-id="bda05-137">不過，有一個例外狀況，那就是第一個使用者可能不是 Autopilot 環境中的裝置擁有者，這會在 [HoloLens 安全性文件](https://docs.microsoft.com/hololens/security-adminless-os#device-owner)詳述。</span><span class="sxs-lookup"><span data-stu-id="bda05-137">However, there is an exception where the first user may not be the device owner in an Autopilot environment, which is detailed in the [HoloLens security documentation](https://docs.microsoft.com/hololens/security-adminless-os#device-owner).</span></span>

<span data-ttu-id="bda05-138">可能的解決方案包括：</span><span class="sxs-lookup"><span data-stu-id="bda05-138">Possible solutions include:</span></span>

* <span data-ttu-id="bda05-139">在將裝置傳遞給其他使用者或開發人員之前，讓裝置擁有者開啟開發人員模式</span><span class="sxs-lookup"><span data-stu-id="bda05-139">Having the device owner turn Developer Mode on before passing the device to other users or developers</span></span>
* <span data-ttu-id="bda05-140">建議您的 IT/MDM 管理員針對特定裝置或開發人員裝置群組啟用 CSP [Policy ApplicationManagement/AllowDeveloperUnlock](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock)。</span><span class="sxs-lookup"><span data-stu-id="bda05-140">Suggesting that your IT/MDM Admin enables CSP [Policy ApplicationManagement/AllowDeveloperUnlock](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock) for the specific device or a developer device group.</span></span> 
    * <span data-ttu-id="bda05-141">此原則可經由[佈建套件](https://docs.microsoft.com/hololens/hololens-provisioning)或透過 [HoloLens 裝置的 MDM](https://docs.microsoft.com/hololens/hololens-mdm-configure) 來設定</span><span class="sxs-lookup"><span data-stu-id="bda05-141">This policy can be set by [Provisioning Packages](https://docs.microsoft.com/hololens/hololens-provisioning) or via [MDM for HoloLens devices](https://docs.microsoft.com/hololens/hololens-mdm-configure)</span></span>
* <span data-ttu-id="bda05-142">使用 [Advanced Recovery Companion (ARC)](https://docs.microsoft.com/hololens/hololens-recovery)</span><span class="sxs-lookup"><span data-stu-id="bda05-142">Using the [Advanced Recovery Companion (ARC)](https://docs.microsoft.com/hololens/hololens-recovery)</span></span>

> [!NOTE]
> <span data-ttu-id="bda05-143">您可以在 **[HoloLens 裝置管理](https://docs.microsoft.com/hololens/hololens-csp-policy-overview)** 概觀中深入了解裝置管理。</span><span class="sxs-lookup"><span data-stu-id="bda05-143">You can learn more about device management in the **[HoloLens device management](https://docs.microsoft.com/hololens/hololens-csp-policy-overview)** overview.</span></span>

##### <a name="i-cant-deploy-over-usb"></a><span data-ttu-id="bda05-144">我無法透過 USB 部署</span><span class="sxs-lookup"><span data-stu-id="bda05-144">I can't deploy over USB</span></span>

<span data-ttu-id="bda05-145">如果您無法直接透過 USB 部署應用程式，請確定您符合上述所有的安裝需求，並遵循我們的[逐步教學課程](../unity/tutorials/mr-learning-base-02.md#building-your-application-to-your-hololens-2)。</span><span class="sxs-lookup"><span data-stu-id="bda05-145">If you're not able to deploy an application directly over USB, make sure you've met all the installation requirements listed above and follow our [step-by-step tutorial](../unity/tutorials/mr-learning-base-02.md#building-your-application-to-your-hololens-2).</span></span>

#### <a name="immersive-vr-headset-requirements"></a><span data-ttu-id="bda05-146">沈浸式 (VR) 頭戴式裝置需求</span><span class="sxs-lookup"><span data-stu-id="bda05-146">Immersive (VR) headset requirements</span></span>

>[!NOTE]
><span data-ttu-id="bda05-147">下列指導方針是沈浸式 (VR) 頭戴裝置「開發電腦」目前的最低建議規格，而且會定期更新。</span><span class="sxs-lookup"><span data-stu-id="bda05-147">The following guidelines are the current minimum and recommended specs for your immersive (VR) headset *development PC*, and are updated regularly.</span></span>

>[!WARNING]
><span data-ttu-id="bda05-148">請勿將此指導方針與[最低電腦硬體相容性指導方針](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)混淆，其中概述了沈浸式 (VR) 頭戴裝置應用程式或遊戲應該定向的「取用者電腦規格」。</span><span class="sxs-lookup"><span data-stu-id="bda05-148">Do not confuse this with the [minimum PC hardware compatibility guidelines](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines), which outlines the *consumer PC specs* to which you should target your immersive (VR) headset app or game.</span></span>

<span data-ttu-id="bda05-149">如果您使用 **Reverb G2** 頭戴式裝置，請下載 **Microsoft-Valve OpenXR** 外掛程式 (TODO: //需要連結)。</span><span class="sxs-lookup"><span data-stu-id="bda05-149">If you're using a **Reverb G2** headset, download the **Microsoft-Valve OpenXR** plugin (TODO: // Need link).</span></span>

<span data-ttu-id="bda05-150">如果沉浸式頭戴裝置開發電腦沒有完整大小的 HDMI 和/或 USB 3.0 連接埠，您需要[配接器](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs)才能連線頭戴式裝置。</span><span class="sxs-lookup"><span data-stu-id="bda05-150">If your immersive headset development PC does not have full-sized HDMI and/or USB 3.0 ports, you'll need [adapters](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs) to connect your headset.</span></span>

<span data-ttu-id="bda05-151">目前某些硬體設定有[已知問題](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)，尤其是具有混合式圖形的筆記型電腦。</span><span class="sxs-lookup"><span data-stu-id="bda05-151">There are currently [known issues](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality) with some hardware configurations, particularly notebooks that have hybrid graphics.</span></span>

<table>
<tr>
<th></th><th> <span data-ttu-id="bda05-152">最低需求</span><span class="sxs-lookup"><span data-stu-id="bda05-152">Minimum</span></span></th><th> <span data-ttu-id="bda05-153">建議</span><span class="sxs-lookup"><span data-stu-id="bda05-153">Recommended</span></span></th>
</tr><tr>
<td> <span data-ttu-id="bda05-154">處理器</span><span class="sxs-lookup"><span data-stu-id="bda05-154">Processor</span></span></td><td> <span data-ttu-id="bda05-155"><b>筆記型電腦：</b>Intel Mobile Core i5 第 7 代 CPU、採用超執行緒技術的雙核心 <b>傳統型：</b>Intel Desktop i5 第 6 代 CPU、採用超執行緒技術的雙核心<b>或</b> AMD FX4350 4.2Ghz 四核心對等項目</span><span class="sxs-lookup"><span data-stu-id="bda05-155"><b>Notebook:</b> Intel Mobile Core i5 7th generation CPU, Dual-Core with Hyper Threading <b>Desktop:</b> Intel Desktop i5 6th generation CPU, Dual-Core with Hyper Threading <b>OR</b> AMD FX4350 4.2Ghz Quad-Core equivalent</span></span></td><td> <span data-ttu-id="bda05-156"><b>傳統型：</b>Intel Desktop i7 第 6 代 (6 核心) <b>或</b> AMD Ryzen 5 1600 (6 核心，12 個執行緒)</span><span class="sxs-lookup"><span data-stu-id="bda05-156"><b>Desktop:</b> Intel Desktop i7 6th generation (6 Core) <b>OR</b> AMD Ryzen 5 1600 (6 Core, 12 threads)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="bda05-157">GPU</span><span class="sxs-lookup"><span data-stu-id="bda05-157">GPU</span></span></td><td> <span data-ttu-id="bda05-158"><b>筆記型電腦：</b>NVIDIA GTX 965M、AMD RX 460M (2GB) 對等項目或更高的 DX12 支援 GPU <b>傳統型：</b>NVIDIA GTX 960/1050、AMD Radeon RX 460 (2GB) 對等項目或更高的 DX12 支援 GPU</span><span class="sxs-lookup"><span data-stu-id="bda05-158"><b>Notebook:</b> NVIDIA GTX 965M, AMD RX 460M (2GB) equivalent or greater DX12 capable GPU <b>Desktop:</b> NVIDIA GTX 960/1050, AMD Radeon RX 460 (2GB) equivalent or greater DX12 capable GPU</span></span></td><td><span data-ttu-id="bda05-159"><b>傳統型：</b>NVIDIA GTX 980/1060、AMD Radeon RX 480 (2GB) 對等項目或更高的 DX12 支援 GPU</span><span class="sxs-lookup"><span data-stu-id="bda05-159"><b>Desktop:</b> NVIDIA GTX 980/1060, AMD Radeon RX 480 (2GB) equivalent or greater DX12 capable GPU</span></span></td>
</tr><tr>
<td> <span data-ttu-id="bda05-160">GPU 驅動程式 WDDM 版本</span><span class="sxs-lookup"><span data-stu-id="bda05-160">GPU driver WDDM version</span></span></td><td colspan="2"> <span data-ttu-id="bda05-161">WDDM 2.2 驅動程式</span><span class="sxs-lookup"><span data-stu-id="bda05-161">WDDM 2.2 driver</span></span></td>
</tr><tr>
<td> <span data-ttu-id="bda05-162">散熱設計功率</span><span class="sxs-lookup"><span data-stu-id="bda05-162">Thermal Design Power</span></span></td><td colspan="2"> <span data-ttu-id="bda05-163">15W 或更大</span><span class="sxs-lookup"><span data-stu-id="bda05-163">15W or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="bda05-164">圖形顯示連接埠</span><span class="sxs-lookup"><span data-stu-id="bda05-164">Graphics display ports</span></span></td><td colspan="2"> <span data-ttu-id="bda05-165">適用於頭戴式裝置的 1x 可用圖形顯示連接埠 (適用於 60Hz 頭戴式裝置的 HDMI 1.4 或 DisplayPort 1.2，適用於 90Hz 頭戴式裝置的 HDMI 2.0 或 DisplayPort 1.2)</span><span class="sxs-lookup"><span data-stu-id="bda05-165">1x available graphics display port for&#160;headset (HDMI 1.4 or DisplayPort 1.2 for 60Hz headsets, HDMI 2.0 or DisplayPort 1.2 for 90Hz headsets)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="bda05-166">顯示器解析度</span><span class="sxs-lookup"><span data-stu-id="bda05-166">Display resolution</span></span></td><td colspan="2"> <span data-ttu-id="bda05-167">解決方法：SVGA (800 x 600) 或更大的位元深度：每像素 32 位元的色彩</span><span class="sxs-lookup"><span data-stu-id="bda05-167">Resolution: SVGA (800x600) or greater Bit depth: 32 bits of color per pixel</span></span></td>
</tr><tr>
<td> <span data-ttu-id="bda05-168">Memory</span><span class="sxs-lookup"><span data-stu-id="bda05-168">Memory</span></span></td><td> <span data-ttu-id="bda05-169">8&#160;GB RAM 或更大</span><span class="sxs-lookup"><span data-stu-id="bda05-169">8&#160;GB of RAM or greater</span></span></td><td> <span data-ttu-id="bda05-170">16 GB RAM 或更大</span><span class="sxs-lookup"><span data-stu-id="bda05-170">16 GB of RAM or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="bda05-171">存放裝置</span><span class="sxs-lookup"><span data-stu-id="bda05-171">Storage</span></span></td><td colspan="2"> <span data-ttu-id="bda05-172">&gt;10 GB 額外可用空間</span><span class="sxs-lookup"><span data-stu-id="bda05-172">&gt;10 GB additional free space</span></span></td>
</tr><tr>
<td> <span data-ttu-id="bda05-173">USB 連接埠</span><span class="sxs-lookup"><span data-stu-id="bda05-173">USB Ports</span></span></td><td colspan="2"> <span data-ttu-id="bda05-174">適用於頭戴式裝置的 1x 可用 USB 連接埠 (USB 3.0 Type-A) <b>注意：USB 必須提供至少 900mA</b></span><span class="sxs-lookup"><span data-stu-id="bda05-174">1x available USB port for headset (USB 3.0 Type-A) <b>Note: USB must supply a minimum of 900mA</b></span></span></td>
</tr><tr>
<td> <span data-ttu-id="bda05-175">Bluetooth</span><span class="sxs-lookup"><span data-stu-id="bda05-175">Bluetooth</span></span></td><td colspan="2"> <span data-ttu-id="bda05-176">Bluetooth 4.0 (適用於周邊連線)</span><span class="sxs-lookup"><span data-stu-id="bda05-176">Bluetooth 4.0 (for accessory connectivity)</span></span></td>
</tr>
</table>

<span data-ttu-id="bda05-177">如果您是首次使用 Unity 進行 MRTK 開發，建議您依循我們策劃的 Unity 開發旅程：</span><span class="sxs-lookup"><span data-stu-id="bda05-177">If you're new to MRTK development with Unity, we recommend following our curated Unity development journey:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="bda05-178">開始您的 Unity 旅程</span><span class="sxs-lookup"><span data-stu-id="bda05-178">Start your Unity journey</span></span>](../unity/unity-development-overview.md)

## <a name="next-development-checkpoint"></a><span data-ttu-id="bda05-179">下一個開發檢查點</span><span class="sxs-lookup"><span data-stu-id="bda05-179">Next Development Checkpoint</span></span>

<span data-ttu-id="bda05-180">依循我們配置的 Unity 開發檢查點旅程，您的下一個工作將是進行 HoloLens 2 教學課程系列。</span><span class="sxs-lookup"><span data-stu-id="bda05-180">If you're following the Unity development checkpoint journey we've laid out, your next task is to work through our HoloLens 2 tutorial series.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="bda05-181">HoloLens 2 教學課程系列</span><span class="sxs-lookup"><span data-stu-id="bda05-181">HoloLens 2 tutorial series</span></span>](../unity/tutorials/mr-learning-base-01.md)

<span data-ttu-id="bda05-182">您可以隨時回到 [Unity 開發檢查點](../unity/unity-development-overview.md#1-getting-started)。</span><span class="sxs-lookup"><span data-stu-id="bda05-182">You can always go back to the [Unity development checkpoints](../unity/unity-development-overview.md#1-getting-started) at any time.</span></span>

# <a name="unreal"></a>[<span data-ttu-id="bda05-183">Unreal</span><span class="sxs-lookup"><span data-stu-id="bda05-183">Unreal</span></span>](#tab/unreal)

![Unreal](../images/unreal_logo_banner.png)

### <a name="1-download-the-latest-version"></a><span data-ttu-id="bda05-185">1.下載最新版本</span><span class="sxs-lookup"><span data-stu-id="bda05-185">1. Download the latest version</span></span>

<span data-ttu-id="bda05-186">建議您安裝 [Unreal Engine 4.25 版](https://docs.unrealengine.com//GettingStarted/Installation/index.html)或更新版本，以充分利用內建的 HoloLens 支援。</span><span class="sxs-lookup"><span data-stu-id="bda05-186">We recommend installing [Unreal Engine version 4.25](https://docs.unrealengine.com//GettingStarted/Installation/index.html) or later to take full advantage of built-in HoloLens support.</span></span>

### <a name="2-import-mixed-reality-toolkit-mrtk"></a><span data-ttu-id="bda05-187">2.匯入混合實境工具組 (MRTK)</span><span class="sxs-lookup"><span data-stu-id="bda05-187">2. Import Mixed Reality Toolkit (MRTK)</span></span>
![MRTK](../../design/images/MRTK_UX_Hero.png)

<span data-ttu-id="bda05-189">混合實境工具組 (MRTK) 是混合實境應用程式的開放原始碼跨平台開發套件。</span><span class="sxs-lookup"><span data-stu-id="bda05-189">Mixed Reality Toolkit (MRTK) is an open-source, cross-platform development kit for mixed reality applications.</span></span> <span data-ttu-id="bda05-190">MRTK 提供跨平台輸入系統、基礎元件，以及空間互動的常見基本要素。</span><span class="sxs-lookup"><span data-stu-id="bda05-190">MRTK provides a cross-platform input system, foundational components, and common building blocks for spatial interactions.</span></span> <span data-ttu-id="bda05-191">該工具組主要用於加速開發以 Microsoft HoloLens、Windows Mixed Reality 沈浸式 (VR) 頭戴裝置和 OpenVR 平台為目標的應用程式。</span><span class="sxs-lookup"><span data-stu-id="bda05-191">The toolkit is intended to accelerate the development of applications targeting Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets, and the OpenVR platform.</span></span>

<span data-ttu-id="bda05-192">進行安裝時，建議您完成我們策劃的 [Unreal 開發旅程圖](../unreal/unreal-development-overview.md)的[開始使用一節](../unreal/unreal-development-overview.md#1-getting-started)。</span><span class="sxs-lookup"><span data-stu-id="bda05-192">For installation, we recommend completing the [Getting Started section](../unreal/unreal-development-overview.md#1-getting-started) of our curated [Unreal development journey](../unreal/unreal-development-overview.md).</span></span> <span data-ttu-id="bda05-193">依循 Unreal 開發旅程，接下來請完成下列其餘的設定步驟，並繼續進行 [HoloLens 2 開始使用教學課程](../unreal/tutorials/unreal-uxt-ch1.md)。</span><span class="sxs-lookup"><span data-stu-id="bda05-193">If you're already following the Unreal development journey, finish up the rest of the setup steps listed below and continue on to the [HoloLens 2 Getting Started tutorials](../unreal/tutorials/unreal-uxt-ch1.md).</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="bda05-194"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unreal" target="_blank">![Unity 標誌影像](../images/MRTK-Unreal-Banner.png)</span><span class="sxs-lookup"><span data-stu-id="bda05-194"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unreal" target="_blank">![Unity logo image](../images/MRTK-Unreal-Banner.png)</span></span><br><span data-ttu-id="bda05-195">**混合實境工具組-Unreal (GitHub)** </a></span><span class="sxs-lookup"><span data-stu-id="bda05-195">**Mixed Reality Toolkit-Unreal (GitHub)**</a></span></span><br>
    :::column-end:::
:::row-end:::

> [!NOTE]
> <span data-ttu-id="bda05-196">如果您不想使用適用於 Unreal 的 MRTK，則必須自行撰寫所有互動和行為的指令碼。</span><span class="sxs-lookup"><span data-stu-id="bda05-196">If you don't want to use MRTK for Unreal, you'll need to script all interactions and behaviors yourself.</span></span>

#### <a name="other-tools-optional"></a><span data-ttu-id="bda05-197">其他工具 [選用]</span><span class="sxs-lookup"><span data-stu-id="bda05-197">Other tools [optional]</span></span>
* <span data-ttu-id="bda05-198"><a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">混合實境配套工具組 (GitHub)</a> - 無法直接在 HoloLens 或沈浸式 (VR) 頭戴裝置上執行的程式碼位元和元件，但是將其搭配使用可打造以 Windows Mixed Reality 為目標的體驗。</span><span class="sxs-lookup"><span data-stu-id="bda05-198"><a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">Mixed Reality Companion Kit (GitHub)</a> - code bits and components that might not run directly on HoloLens or immersive (VR) headsets, but instead pair with them to build experiences targeting Windows Mixed Reality.</span></span>
* <span data-ttu-id="bda05-199"><a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">混合的現實工具組 - 通用 (GitHub)</a> - 共用指令碼和元件的集合。</span><span class="sxs-lookup"><span data-stu-id="bda05-199"><a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">Mixed Reality Toolkit - Co mmon (GitHub)</a> - a collection of shared scripts and components.</span></span>

### <a name="3-set-up-your-pc-for-mixed-reality-development"></a><span data-ttu-id="bda05-200">3.設定您的電腦以便進行混合實境開發</span><span class="sxs-lookup"><span data-stu-id="bda05-200">3. Set up your PC for mixed reality development</span></span>

<span data-ttu-id="bda05-201">Windows 10 SDK 最適合用於 Windows 10 作業系統。</span><span class="sxs-lookup"><span data-stu-id="bda05-201">The Windows 10 SDK works best on the Windows 10 operating system.</span></span> <span data-ttu-id="bda05-202">Windows 8.1、Windows 8、Windows 7、Windows Server 2012、Windows Server 2008 R2 也支援此 SDK。</span><span class="sxs-lookup"><span data-stu-id="bda05-202">This SDK is also supported on Windows 8.1, Windows 8, Windows 7, Windows Server 2012, Windows Server 2008 R2.</span></span> <span data-ttu-id="bda05-203">請注意，舊版作業系統不支援所有工具。</span><span class="sxs-lookup"><span data-stu-id="bda05-203">Note that not all tools are supported on older operating systems.</span></span>

> [!NOTE]
> <span data-ttu-id="bda05-204">您可以針對 HoloLens、VR 沉浸式頭戴裝置或兩者開發及部署應用程式。</span><span class="sxs-lookup"><span data-stu-id="bda05-204">You can develop and deploy your apps for HoloLens, VR immersive headsets, or both.</span></span> <span data-ttu-id="bda05-205">視您的需求而定，請確定您符合下列需求。</span><span class="sxs-lookup"><span data-stu-id="bda05-205">Make sure you fulfill the requirements below depending on your needs.</span></span>

#### <a name="for-hololens-development"></a><span data-ttu-id="bda05-206">對於 HoloLens 開發</span><span class="sxs-lookup"><span data-stu-id="bda05-206">For HoloLens development</span></span>

<span data-ttu-id="bda05-207">設定您的開發電腦以便進行 HoloLens 開發時，請確定您符合 [Unity](https://docs.unrealengine.com/GettingStarted/RecommendedSpecifications/index.html) 和 <a href="https://docs.microsoft.com//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a> 的系統需求。</span><span class="sxs-lookup"><span data-stu-id="bda05-207">When setting up your development PC for HoloLens development, please make sure you meet the system requirements for [Unreal](https://docs.unrealengine.com/GettingStarted/RecommendedSpecifications/index.html) and and <a href="https://docs.microsoft.com//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a>.</span></span> <span data-ttu-id="bda05-208">如果您想要在 HoloLens 裝置上執行您的應用程式，則必須遵循 [Windows 裝置入口網站安裝指示](../platform-capabilities-and-apis/using-the-windows-device-portal.md#setting-up-hololens-to-use-windows-device-portal)。</span><span class="sxs-lookup"><span data-stu-id="bda05-208">If you want to run your app on a HoloLens device, you need to follow the [Windows Device Portal setup instructions](../platform-capabilities-and-apis/using-the-windows-device-portal.md#setting-up-hololens-to-use-windows-device-portal).</span></span> <span data-ttu-id="bda05-209">如果您打算使用 [HoloLens 模擬器](../platform-capabilities-and-apis/using-the-hololens-emulator.md)，您應確定您的電腦也符合 [HoloLens 模擬器系統需求](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements)。</span><span class="sxs-lookup"><span data-stu-id="bda05-209">If you plan on using the [HoloLens emulator](../platform-capabilities-and-apis/using-the-hololens-emulator.md), you'll want to make sure your PC meets the [HoloLens emulator system requirements](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements) as well.</span></span>

<span data-ttu-id="bda05-210">如果您打算針對 HoloLens 與 Windows Mixed Reality 沈浸式 (VR) 頭戴裝置進行開發，請使用下一節中的系統建議和需求。</span><span class="sxs-lookup"><span data-stu-id="bda05-210">If you plan to develop for both HoloLens and Windows Mixed Reality immersive (VR) headsets, use the system recommendations and requirements in the section below.</span></span>

#### <a name="hololens-troubleshooting"></a><span data-ttu-id="bda05-211">HoloLens 疑難排解</span><span class="sxs-lookup"><span data-stu-id="bda05-211">HoloLens troubleshooting</span></span>

##### <a name="setting-developer-mode-is-grayed-out"></a><span data-ttu-id="bda05-212">設定開發人員模式呈現灰色</span><span class="sxs-lookup"><span data-stu-id="bda05-212">Setting Developer Mode is grayed out</span></span>

<span data-ttu-id="bda05-213">如果您在裝置上啟用開發人員模式時遇到問題，您可能不是[裝置擁有者](https://docs.microsoft.com/hololens/security-adminless-os)。</span><span class="sxs-lookup"><span data-stu-id="bda05-213">If you're running into issues enabling Developer Mode on your device you might not be the [device owner](https://docs.microsoft.com/hololens/security-adminless-os).</span></span> <span data-ttu-id="bda05-214">在多使用者模式中，第一個使用裝置的人員就是裝置擁有者，任何後續的使用者都不會擁有啟用 [開發人員模式] 或其他組態變更所需的權限。</span><span class="sxs-lookup"><span data-stu-id="bda05-214">In multi-user mode, the person who uses the device first is the device owner - any subsequent users won't have the required permissions to enable Developer Mode or other configuration changes.</span></span> <span data-ttu-id="bda05-215">不過，有一個例外狀況，那就是第一個使用者可能不是 Autopilot 環境中的裝置擁有者，這會在 [HoloLens 安全性文件](https://docs.microsoft.com/hololens/security-adminless-os#device-owner)詳述。</span><span class="sxs-lookup"><span data-stu-id="bda05-215">However, there is an exception where the first user may not be the device owner in an Autopilot environment, which is detailed in the [HoloLens security documentation](https://docs.microsoft.com/hololens/security-adminless-os#device-owner).</span></span>

<span data-ttu-id="bda05-216">可能的解決方案包括：</span><span class="sxs-lookup"><span data-stu-id="bda05-216">Possible solutions include:</span></span>

* <span data-ttu-id="bda05-217">在將裝置傳遞給其他使用者或開發人員之前，讓裝置擁有者開啟開發人員模式</span><span class="sxs-lookup"><span data-stu-id="bda05-217">Having the device owner turn Developer Mode on before passing the device to other users or developers</span></span>
* <span data-ttu-id="bda05-218">建議您的 IT/MDM 管理員針對特定裝置或開發人員裝置群組啟用 CSP [Policy ApplicationManagement/AllowDeveloperUnlock](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock)。</span><span class="sxs-lookup"><span data-stu-id="bda05-218">Suggesting that your IT/MDM Admin enables CSP [Policy ApplicationManagement/AllowDeveloperUnlock](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock) for the specific device or a developer device group.</span></span> 
    * <span data-ttu-id="bda05-219">此原則可經由[佈建套件](https://docs.microsoft.com/hololens/hololens-provisioning)或透過 [HoloLens 裝置的 MDM](https://docs.microsoft.com/hololens/hololens-mdm-configure) 來設定</span><span class="sxs-lookup"><span data-stu-id="bda05-219">This policy can be set by [Provisioning Packages](https://docs.microsoft.com/hololens/hololens-provisioning) or via [MDM for HoloLens devices](https://docs.microsoft.com/hololens/hololens-mdm-configure)</span></span>
* <span data-ttu-id="bda05-220">使用 [Advanced Recovery Companion (ARC)](https://docs.microsoft.com/hololens/hololens-recovery)</span><span class="sxs-lookup"><span data-stu-id="bda05-220">Using the [Advanced Recovery Companion (ARC)](https://docs.microsoft.com/hololens/hololens-recovery)</span></span>

> [!NOTE]
> <span data-ttu-id="bda05-221">您可以在 **[HoloLens 裝置管理](https://docs.microsoft.com/hololens/hololens-csp-policy-overview)** 概觀中深入了解裝置管理。</span><span class="sxs-lookup"><span data-stu-id="bda05-221">You can learn more about device management in the **[HoloLens device management](https://docs.microsoft.com/hololens/hololens-csp-policy-overview)** overview.</span></span>

##### <a name="i-cant-deploy-over-usb"></a><span data-ttu-id="bda05-222">我無法透過 USB 部署</span><span class="sxs-lookup"><span data-stu-id="bda05-222">I can't deploy over USB</span></span>

<span data-ttu-id="bda05-223">如果您無法直接透過 USB 部署應用程式，請確定您符合上述所有的安裝需求，並遵循我們的[逐步教學課程](../unreal/tutorials/unreal-uxt-ch6.md)。</span><span class="sxs-lookup"><span data-stu-id="bda05-223">If you're not able to deploy an application directly over USB, make sure you've met all the installation requirements listed above and follow our [step-by-step tutorial](../unreal/tutorials/unreal-uxt-ch6.md).</span></span>

#### <a name="immersive-vr-headset-requirements"></a><span data-ttu-id="bda05-224">沈浸式 (VR) 頭戴式裝置需求</span><span class="sxs-lookup"><span data-stu-id="bda05-224">Immersive (VR) headset requirements</span></span>

>[!NOTE]
><span data-ttu-id="bda05-225">下列指導方針是沈浸式 (VR) 頭戴裝置「開發電腦」目前的最低建議規格，而且會定期更新。</span><span class="sxs-lookup"><span data-stu-id="bda05-225">The following guidelines are the current minimum and recommended specs for your immersive (VR) headset *development PC*, and are updated regularly.</span></span>

>[!WARNING]
><span data-ttu-id="bda05-226">請勿將此指導方針與[最低電腦硬體相容性指導方針](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)混淆，其中概述了沈浸式 (VR) 頭戴裝置應用程式或遊戲應該定向的「取用者電腦規格」。</span><span class="sxs-lookup"><span data-stu-id="bda05-226">Do not confuse this with the [minimum PC hardware compatibility guidelines](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines), which outlines the *consumer PC specs* to which you should target your immersive (VR) headset app or game.</span></span>

<span data-ttu-id="bda05-227">如果您使用 **Reverb G2** 頭戴式裝置，請下載 **Microsoft-Valve OpenXR** 外掛程式 (TODO: //需要連結)。</span><span class="sxs-lookup"><span data-stu-id="bda05-227">If you're using a **Reverb G2** headset, download the **Microsoft-Valve OpenXR** plugin (TODO: // Need link).</span></span>

<span data-ttu-id="bda05-228">如果沉浸式頭戴裝置開發電腦沒有完整大小的 HDMI 和/或 USB 3.0 連接埠，您需要[配接器](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs)才能連線頭戴式裝置。</span><span class="sxs-lookup"><span data-stu-id="bda05-228">If your immersive headset development PC does not have full-sized HDMI and/or USB 3.0 ports, you'll need [adapters](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs) to connect your headset.</span></span>

<span data-ttu-id="bda05-229">目前某些硬體設定有[已知問題](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)，尤其是具有混合式圖形的筆記型電腦。</span><span class="sxs-lookup"><span data-stu-id="bda05-229">There are currently [known issues](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality) with some hardware configurations, particularly notebooks that have hybrid graphics.</span></span>

<table>
<tr>
<th></th><th> <span data-ttu-id="bda05-230">最低需求</span><span class="sxs-lookup"><span data-stu-id="bda05-230">Minimum</span></span></th><th> <span data-ttu-id="bda05-231">建議</span><span class="sxs-lookup"><span data-stu-id="bda05-231">Recommended</span></span></th>
</tr><tr>
<td> <span data-ttu-id="bda05-232">處理器</span><span class="sxs-lookup"><span data-stu-id="bda05-232">Processor</span></span></td><td> <span data-ttu-id="bda05-233"><b>筆記型電腦：</b>Intel Mobile Core i5 第 7 代 CPU、採用超執行緒技術的雙核心 <b>傳統型：</b>Intel Desktop i5 第 6 代 CPU、採用超執行緒技術的雙核心<b>或</b> AMD FX4350 4.2Ghz 四核心對等項目</span><span class="sxs-lookup"><span data-stu-id="bda05-233"><b>Notebook:</b> Intel Mobile Core i5 7th generation CPU, Dual-Core with Hyper Threading <b>Desktop:</b> Intel Desktop i5 6th generation CPU, Dual-Core with Hyper Threading <b>OR</b> AMD FX4350 4.2Ghz Quad-Core equivalent</span></span></td><td> <span data-ttu-id="bda05-234"><b>傳統型：</b>Intel Desktop i7 第 6 代 (6 核心) <b>或</b> AMD Ryzen 5 1600 (6 核心，12 個執行緒)</span><span class="sxs-lookup"><span data-stu-id="bda05-234"><b>Desktop:</b> Intel Desktop i7 6th generation (6 Core) <b>OR</b> AMD Ryzen 5 1600 (6 Core, 12 threads)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="bda05-235">GPU</span><span class="sxs-lookup"><span data-stu-id="bda05-235">GPU</span></span></td><td> <span data-ttu-id="bda05-236"><b>筆記型電腦：</b>NVIDIA GTX 965M、AMD RX 460M (2GB) 對等項目或更高的 DX12 支援 GPU <b>傳統型：</b>NVIDIA GTX 960/1050、AMD Radeon RX 460 (2GB) 對等項目或更高的 DX12 支援 GPU</span><span class="sxs-lookup"><span data-stu-id="bda05-236"><b>Notebook:</b> NVIDIA GTX 965M, AMD RX 460M (2GB) equivalent or greater DX12 capable GPU <b>Desktop:</b> NVIDIA GTX 960/1050, AMD Radeon RX 460 (2GB) equivalent or greater DX12 capable GPU</span></span></td><td><span data-ttu-id="bda05-237"><b>傳統型：</b>NVIDIA GTX 980/1060、AMD Radeon RX 480 (2GB) 對等項目或更高的 DX12 支援 GPU</span><span class="sxs-lookup"><span data-stu-id="bda05-237"><b>Desktop:</b> NVIDIA GTX 980/1060, AMD Radeon RX 480 (2GB) equivalent or greater DX12 capable GPU</span></span></td>
</tr><tr>
<td> <span data-ttu-id="bda05-238">GPU 驅動程式 WDDM 版本</span><span class="sxs-lookup"><span data-stu-id="bda05-238">GPU driver WDDM version</span></span></td><td colspan="2"> <span data-ttu-id="bda05-239">WDDM 2.2 驅動程式</span><span class="sxs-lookup"><span data-stu-id="bda05-239">WDDM 2.2 driver</span></span></td>
</tr><tr>
<td> <span data-ttu-id="bda05-240">散熱設計功率</span><span class="sxs-lookup"><span data-stu-id="bda05-240">Thermal Design Power</span></span></td><td colspan="2"> <span data-ttu-id="bda05-241">15W 或更大</span><span class="sxs-lookup"><span data-stu-id="bda05-241">15W or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="bda05-242">圖形顯示連接埠</span><span class="sxs-lookup"><span data-stu-id="bda05-242">Graphics display ports</span></span></td><td colspan="2"> <span data-ttu-id="bda05-243">適用於頭戴式裝置的 1x 可用圖形顯示連接埠 (適用於 60Hz 頭戴式裝置的 HDMI 1.4 或 DisplayPort 1.2，適用於 90Hz 頭戴式裝置的 HDMI 2.0 或 DisplayPort 1.2)</span><span class="sxs-lookup"><span data-stu-id="bda05-243">1x available graphics display port for&#160;headset (HDMI 1.4 or DisplayPort 1.2 for 60Hz headsets, HDMI 2.0 or DisplayPort 1.2 for 90Hz headsets)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="bda05-244">顯示器解析度</span><span class="sxs-lookup"><span data-stu-id="bda05-244">Display resolution</span></span></td><td colspan="2"> <span data-ttu-id="bda05-245">解決方法：SVGA (800 x 600) 或更大的位元深度：每像素 32 位元的色彩</span><span class="sxs-lookup"><span data-stu-id="bda05-245">Resolution: SVGA (800x600) or greater Bit depth: 32 bits of color per pixel</span></span></td>
</tr><tr>
<td> <span data-ttu-id="bda05-246">Memory</span><span class="sxs-lookup"><span data-stu-id="bda05-246">Memory</span></span></td><td> <span data-ttu-id="bda05-247">8&#160;GB RAM 或更大</span><span class="sxs-lookup"><span data-stu-id="bda05-247">8&#160;GB of RAM or greater</span></span></td><td> <span data-ttu-id="bda05-248">16 GB RAM 或更大</span><span class="sxs-lookup"><span data-stu-id="bda05-248">16 GB of RAM or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="bda05-249">存放裝置</span><span class="sxs-lookup"><span data-stu-id="bda05-249">Storage</span></span></td><td colspan="2"> <span data-ttu-id="bda05-250">&gt;10 GB 額外可用空間</span><span class="sxs-lookup"><span data-stu-id="bda05-250">&gt;10 GB additional free space</span></span></td>
</tr><tr>
<td> <span data-ttu-id="bda05-251">USB 連接埠</span><span class="sxs-lookup"><span data-stu-id="bda05-251">USB Ports</span></span></td><td colspan="2"> <span data-ttu-id="bda05-252">適用於頭戴式裝置的 1x 可用 USB 連接埠 (USB 3.0 Type-A) <b>注意：USB 必須提供至少 900mA</b></span><span class="sxs-lookup"><span data-stu-id="bda05-252">1x available USB port for headset (USB 3.0 Type-A) <b>Note: USB must supply a minimum of 900mA</b></span></span></td>
</tr><tr>
<td> <span data-ttu-id="bda05-253">Bluetooth</span><span class="sxs-lookup"><span data-stu-id="bda05-253">Bluetooth</span></span></td><td colspan="2"> <span data-ttu-id="bda05-254">Bluetooth 4.0 (適用於周邊連線)</span><span class="sxs-lookup"><span data-stu-id="bda05-254">Bluetooth 4.0 (for accessory connectivity)</span></span></td>
</tr>
</table>

<span data-ttu-id="bda05-255">如果您是首次使用 Unreal 進行 MRTK 開發，建議您依循我們策劃的 Unreal 開發旅程：</span><span class="sxs-lookup"><span data-stu-id="bda05-255">If you're new to MRTK development with Unreal, we recommend following our curated Unreal development journey:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="bda05-256">開始您的 Unreal 旅程</span><span class="sxs-lookup"><span data-stu-id="bda05-256">Start your Unreal journey</span></span>](../unreal/unreal-development-overview.md)

## <a name="next-development-checkpoint"></a><span data-ttu-id="bda05-257">下一個開發檢查點</span><span class="sxs-lookup"><span data-stu-id="bda05-257">Next Development Checkpoint</span></span>

<span data-ttu-id="bda05-258">依循我們配置的 Unreal 開發檢查點旅程，您的下一個工作將是進行 HoloLens 2 教學課程系列。</span><span class="sxs-lookup"><span data-stu-id="bda05-258">If you're following the Unreal development checkpoint journey we've laid out, your next task is to work through our HoloLens 2 tutorial series.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="bda05-259">HoloLens 2 教學課程系列</span><span class="sxs-lookup"><span data-stu-id="bda05-259">HoloLens 2 tutorial series</span></span>](../unreal/tutorials/unreal-uxt-ch1.md)

<span data-ttu-id="bda05-260">您可以隨時回到 [Unreal 開發檢查點](../unreal/unreal-development-overview.md#1-getting-started)。</span><span class="sxs-lookup"><span data-stu-id="bda05-260">You can always go back to the [Unreal development checkpoints](../unreal/unreal-development-overview.md#1-getting-started) at any time.</span></span>

# <a name="native-openxr"></a>[<span data-ttu-id="bda05-261">原生 (OpenXR)</span><span class="sxs-lookup"><span data-stu-id="bda05-261">Native (OpenXR)</span></span>](#tab/native)

 ![原生應用程式開發](../images/native_logo_banner.png)

<span data-ttu-id="bda05-263">原生 OpenXR 開發沒有可供您下載的引擎。</span><span class="sxs-lookup"><span data-stu-id="bda05-263">Native OpenXR development doesn't have an engine for you to download.</span></span> <span data-ttu-id="bda05-264">您可以在[開始使用 OpenXR](../native/openxr-getting-started.md) 文件中找到開始進行開發所需的一切資訊。</span><span class="sxs-lookup"><span data-stu-id="bda05-264">You can find everything you need to begin development in the [Getting started with OpenXR](../native/openxr-getting-started.md) document.</span></span>

### <a name="1-set-up-your-pc-for-mixed-reality-development"></a><span data-ttu-id="bda05-265">1.設定您的電腦以便進行混合實境開發</span><span class="sxs-lookup"><span data-stu-id="bda05-265">1. Set up your PC for mixed reality development</span></span>

<span data-ttu-id="bda05-266">Windows 10 SDK 最適合用於 Windows 10 作業系統。</span><span class="sxs-lookup"><span data-stu-id="bda05-266">The Windows 10 SDK works best on the Windows 10 operating system.</span></span> <span data-ttu-id="bda05-267">Windows 8.1、Windows 8、Windows 7、Windows Server 2012、Windows Server 2008 R2 也支援此 SDK。</span><span class="sxs-lookup"><span data-stu-id="bda05-267">This SDK is also supported on Windows 8.1, Windows 8, Windows 7, Windows Server 2012, Windows Server 2008 R2.</span></span> <span data-ttu-id="bda05-268">請注意，舊版作業系統不支援所有工具。</span><span class="sxs-lookup"><span data-stu-id="bda05-268">Note that not all tools are supported on older operating systems.</span></span>

#### <a name="for-hololens-development"></a><span data-ttu-id="bda05-269">對於 HoloLens 開發</span><span class="sxs-lookup"><span data-stu-id="bda05-269">For HoloLens development</span></span>

<span data-ttu-id="bda05-270">設定您的開發電腦以便進行 HoloLens 開發時，請確定您符合 <a href="https://docs.microsoft.com//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a> 的系統需求。</span><span class="sxs-lookup"><span data-stu-id="bda05-270">When setting up your development PC for HoloLens development, please make sure you meet the system requirements for <a href="https://docs.microsoft.com//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a>.</span></span> <span data-ttu-id="bda05-271">如果您想要在 HoloLens 裝置上執行您的應用程式，則必須遵循 [Windows 裝置入口網站安裝指示](../platform-capabilities-and-apis/using-the-windows-device-portal.md#setting-up-hololens-to-use-windows-device-portal)。</span><span class="sxs-lookup"><span data-stu-id="bda05-271">If you want to run your app on a HoloLens device, you need to follow the [Windows Device Portal setup instructions](../platform-capabilities-and-apis/using-the-windows-device-portal.md#setting-up-hololens-to-use-windows-device-portal).</span></span> <span data-ttu-id="bda05-272">如果您打算使用 [HoloLens 模擬器](../platform-capabilities-and-apis/using-the-hololens-emulator.md)，您應確定您的電腦也符合 [HoloLens 模擬器系統需求](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements)。</span><span class="sxs-lookup"><span data-stu-id="bda05-272">If you plan on using the [HoloLens emulator](../platform-capabilities-and-apis/using-the-hololens-emulator.md), you'll want to make sure your PC meets the [HoloLens emulator system requirements](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements) as well.</span></span>

<span data-ttu-id="bda05-273">如果您打算針對 HoloLens 與 Windows Mixed Reality 沈浸式 (VR) 頭戴裝置進行開發，請使用下一節中的系統建議和需求。</span><span class="sxs-lookup"><span data-stu-id="bda05-273">If you plan to develop for both HoloLens and Windows Mixed Reality immersive (VR) headsets, use the system recommendations and requirements in the section below.</span></span>

> [!NOTE]
> <span data-ttu-id="bda05-274">您可以針對 HoloLens、VR 沉浸式頭戴裝置或兩者開發及部署應用程式。</span><span class="sxs-lookup"><span data-stu-id="bda05-274">You can develop and deploy your apps for HoloLens, VR immersive headsets, or both.</span></span> <span data-ttu-id="bda05-275">視您的需求而定，請確定您符合下列需求。</span><span class="sxs-lookup"><span data-stu-id="bda05-275">Make sure you fulfill the requirements below depending on your needs.</span></span>

#### <a name="hololens-troubleshooting"></a><span data-ttu-id="bda05-276">HoloLens 疑難排解</span><span class="sxs-lookup"><span data-stu-id="bda05-276">HoloLens troubleshooting</span></span>

##### <a name="setting-developer-mode-is-grayed-out"></a><span data-ttu-id="bda05-277">設定開發人員模式呈現灰色</span><span class="sxs-lookup"><span data-stu-id="bda05-277">Setting Developer Mode is grayed out</span></span>

<span data-ttu-id="bda05-278">如果您在裝置上啟用開發人員模式時遇到問題，您可能不是[裝置擁有者](https://docs.microsoft.com/hololens/security-adminless-os)。</span><span class="sxs-lookup"><span data-stu-id="bda05-278">If you're running into issues enabling Developer Mode on your device you might not be the [device owner](https://docs.microsoft.com/hololens/security-adminless-os).</span></span> <span data-ttu-id="bda05-279">在多使用者模式中，第一個使用裝置的人員就是裝置擁有者，任何後續的使用者都不會擁有啟用 [開發人員模式] 或其他組態變更所需的權限。</span><span class="sxs-lookup"><span data-stu-id="bda05-279">In multi-user mode, the person who uses the device first is the device owner - any subsequent users won't have the required permissions to enable Developer Mode or other configuration changes.</span></span> <span data-ttu-id="bda05-280">不過，有一個例外狀況，那就是第一個使用者可能不是 Autopilot 環境中的裝置擁有者，這會在 [HoloLens 安全性文件](https://docs.microsoft.com/hololens/security-adminless-os#device-owner)詳述。</span><span class="sxs-lookup"><span data-stu-id="bda05-280">However, there is an exception where the first user may not be the device owner in an Autopilot environment, which is detailed in the [HoloLens security documentation](https://docs.microsoft.com/hololens/security-adminless-os#device-owner).</span></span>

<span data-ttu-id="bda05-281">可能的解決方案包括：</span><span class="sxs-lookup"><span data-stu-id="bda05-281">Possible solutions include:</span></span>

* <span data-ttu-id="bda05-282">在將裝置傳遞給其他使用者或開發人員之前，讓裝置擁有者開啟開發人員模式</span><span class="sxs-lookup"><span data-stu-id="bda05-282">Having the device owner turn Developer Mode on before passing the device to other users or developers</span></span>
* <span data-ttu-id="bda05-283">建議您的 IT/MDM 管理員針對特定裝置或開發人員裝置群組啟用 CSP [Policy ApplicationManagement/AllowDeveloperUnlock](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock)。</span><span class="sxs-lookup"><span data-stu-id="bda05-283">Suggesting that your IT/MDM Admin enables CSP [Policy ApplicationManagement/AllowDeveloperUnlock](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock) for the specific device or a developer device group.</span></span> 
    * <span data-ttu-id="bda05-284">此原則可經由[佈建套件](https://docs.microsoft.com/hololens/hololens-provisioning)或透過 [HoloLens 裝置的 MDM](https://docs.microsoft.com/hololens/hololens-mdm-configure) 來設定</span><span class="sxs-lookup"><span data-stu-id="bda05-284">This policy can be set by [Provisioning Packages](https://docs.microsoft.com/hololens/hololens-provisioning) or via [MDM for HoloLens devices](https://docs.microsoft.com/hololens/hololens-mdm-configure)</span></span>
* <span data-ttu-id="bda05-285">使用 [Advanced Recovery Companion (ARC)](https://docs.microsoft.com/hololens/hololens-recovery)</span><span class="sxs-lookup"><span data-stu-id="bda05-285">Using the [Advanced Recovery Companion (ARC)](https://docs.microsoft.com/hololens/hololens-recovery)</span></span>

> [!NOTE]
> <span data-ttu-id="bda05-286">您可以在 **[HoloLens 裝置管理](https://docs.microsoft.com/hololens/hololens-csp-policy-overview)** 概觀中深入了解裝置管理。</span><span class="sxs-lookup"><span data-stu-id="bda05-286">You can learn more about device management in the **[HoloLens device management](https://docs.microsoft.com/hololens/hololens-csp-policy-overview)** overview.</span></span>

#### <a name="immersive-vr-headset-requirements"></a><span data-ttu-id="bda05-287">沈浸式 (VR) 頭戴式裝置需求</span><span class="sxs-lookup"><span data-stu-id="bda05-287">Immersive (VR) headset requirements</span></span>

>[!NOTE]
><span data-ttu-id="bda05-288">下列指導方針是沈浸式 (VR) 頭戴裝置「開發電腦」目前的最低建議規格，而且會定期更新。</span><span class="sxs-lookup"><span data-stu-id="bda05-288">The following guidelines are the current minimum and recommended specs for your immersive (VR) headset *development PC*, and are updated regularly.</span></span>

>[!WARNING]
><span data-ttu-id="bda05-289">請勿將此指導方針與[最低電腦硬體相容性指導方針](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)混淆，其中概述了沈浸式 (VR) 頭戴裝置應用程式或遊戲應該定向的「取用者電腦規格」。</span><span class="sxs-lookup"><span data-stu-id="bda05-289">Do not confuse this with the [minimum PC hardware compatibility guidelines](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines), which outlines the *consumer PC specs* to which you should target your immersive (VR) headset app or game.</span></span>

<span data-ttu-id="bda05-290">如果沉浸式頭戴裝置開發電腦沒有完整大小的 HDMI 和/或 USB 3.0 連接埠，您需要[配接器](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs)才能連線頭戴式裝置。</span><span class="sxs-lookup"><span data-stu-id="bda05-290">If your immersive headset development PC does not have full-sized HDMI and/or USB 3.0 ports, you'll need [adapters](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs) to connect your headset.</span></span>

<span data-ttu-id="bda05-291">目前某些硬體設定有[已知問題](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)，尤其是具有混合式圖形的筆記型電腦。</span><span class="sxs-lookup"><span data-stu-id="bda05-291">There are currently [known issues](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality) with some hardware configurations, particularly notebooks that have hybrid graphics.</span></span>

<table>
<tr>
<th></th><th> <span data-ttu-id="bda05-292">最低需求</span><span class="sxs-lookup"><span data-stu-id="bda05-292">Minimum</span></span></th><th> <span data-ttu-id="bda05-293">建議</span><span class="sxs-lookup"><span data-stu-id="bda05-293">Recommended</span></span></th>
</tr><tr>
<td> <span data-ttu-id="bda05-294">處理器</span><span class="sxs-lookup"><span data-stu-id="bda05-294">Processor</span></span></td><td> <span data-ttu-id="bda05-295"><b>筆記型電腦：</b>Intel Mobile Core i5 第 7 代 CPU、採用超執行緒技術的雙核心 <b>傳統型：</b>Intel Desktop i5 第 6 代 CPU、採用超執行緒技術的雙核心<b>或</b> AMD FX4350 4.2Ghz 四核心對等項目</span><span class="sxs-lookup"><span data-stu-id="bda05-295"><b>Notebook:</b> Intel Mobile Core i5 7th generation CPU, Dual-Core with Hyper Threading <b>Desktop:</b> Intel Desktop i5 6th generation CPU, Dual-Core with Hyper Threading <b>OR</b> AMD FX4350 4.2Ghz Quad-Core equivalent</span></span></td><td> <span data-ttu-id="bda05-296"><b>傳統型：</b>Intel Desktop i7 第 6 代 (6 核心) <b>或</b> AMD Ryzen 5 1600 (6 核心，12 個執行緒)</span><span class="sxs-lookup"><span data-stu-id="bda05-296"><b>Desktop:</b> Intel Desktop i7 6th generation (6 Core) <b>OR</b> AMD Ryzen 5 1600 (6 Core, 12 threads)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="bda05-297">GPU</span><span class="sxs-lookup"><span data-stu-id="bda05-297">GPU</span></span></td><td> <span data-ttu-id="bda05-298"><b>筆記型電腦：</b>NVIDIA GTX 965M、AMD RX 460M (2GB) 對等項目或更高的 DX12 支援 GPU <b>傳統型：</b>NVIDIA GTX 960/1050、AMD Radeon RX 460 (2GB) 對等項目或更高的 DX12 支援 GPU</span><span class="sxs-lookup"><span data-stu-id="bda05-298"><b>Notebook:</b> NVIDIA GTX 965M, AMD RX 460M (2GB) equivalent or greater DX12 capable GPU <b>Desktop:</b> NVIDIA GTX 960/1050, AMD Radeon RX 460 (2GB) equivalent or greater DX12 capable GPU</span></span></td><td><span data-ttu-id="bda05-299"><b>傳統型：</b>NVIDIA GTX 980/1060、AMD Radeon RX 480 (2GB) 對等項目或更高的 DX12 支援 GPU</span><span class="sxs-lookup"><span data-stu-id="bda05-299"><b>Desktop:</b> NVIDIA GTX 980/1060, AMD Radeon RX 480 (2GB) equivalent or greater DX12 capable GPU</span></span></td>
</tr><tr>
<td> <span data-ttu-id="bda05-300">GPU 驅動程式 WDDM 版本</span><span class="sxs-lookup"><span data-stu-id="bda05-300">GPU driver WDDM version</span></span></td><td colspan="2"> <span data-ttu-id="bda05-301">WDDM 2.2 驅動程式</span><span class="sxs-lookup"><span data-stu-id="bda05-301">WDDM 2.2 driver</span></span></td>
</tr><tr>
<td> <span data-ttu-id="bda05-302">散熱設計功率</span><span class="sxs-lookup"><span data-stu-id="bda05-302">Thermal Design Power</span></span></td><td colspan="2"> <span data-ttu-id="bda05-303">15W 或更大</span><span class="sxs-lookup"><span data-stu-id="bda05-303">15W or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="bda05-304">圖形顯示連接埠</span><span class="sxs-lookup"><span data-stu-id="bda05-304">Graphics display ports</span></span></td><td colspan="2"> <span data-ttu-id="bda05-305">適用於頭戴式裝置的 1x 可用圖形顯示連接埠 (適用於 60Hz 頭戴式裝置的 HDMI 1.4 或 DisplayPort 1.2，適用於 90Hz 頭戴式裝置的 HDMI 2.0 或 DisplayPort 1.2)</span><span class="sxs-lookup"><span data-stu-id="bda05-305">1x available graphics display port for&#160;headset (HDMI 1.4 or DisplayPort 1.2 for 60Hz headsets, HDMI 2.0 or DisplayPort 1.2 for 90Hz headsets)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="bda05-306">顯示器解析度</span><span class="sxs-lookup"><span data-stu-id="bda05-306">Display resolution</span></span></td><td colspan="2"> <span data-ttu-id="bda05-307">解決方法：SVGA (800 x 600) 或更大的位元深度：每像素 32 位元的色彩</span><span class="sxs-lookup"><span data-stu-id="bda05-307">Resolution: SVGA (800x600) or greater Bit depth: 32 bits of color per pixel</span></span></td>
</tr><tr>
<td> <span data-ttu-id="bda05-308">Memory</span><span class="sxs-lookup"><span data-stu-id="bda05-308">Memory</span></span></td><td> <span data-ttu-id="bda05-309">8&#160;GB RAM 或更大</span><span class="sxs-lookup"><span data-stu-id="bda05-309">8&#160;GB of RAM or greater</span></span></td><td> <span data-ttu-id="bda05-310">16 GB RAM 或更大</span><span class="sxs-lookup"><span data-stu-id="bda05-310">16 GB of RAM or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="bda05-311">存放裝置</span><span class="sxs-lookup"><span data-stu-id="bda05-311">Storage</span></span></td><td colspan="2"> <span data-ttu-id="bda05-312">&gt;10 GB 額外可用空間</span><span class="sxs-lookup"><span data-stu-id="bda05-312">&gt;10 GB additional free space</span></span></td>
</tr><tr>
<td> <span data-ttu-id="bda05-313">USB 連接埠</span><span class="sxs-lookup"><span data-stu-id="bda05-313">USB Ports</span></span></td><td colspan="2"> <span data-ttu-id="bda05-314">適用於頭戴式裝置的 1x 可用 USB 連接埠 (USB 3.0 Type-A) <b>注意：USB 必須提供至少 900mA</b></span><span class="sxs-lookup"><span data-stu-id="bda05-314">1x available USB port for headset (USB 3.0 Type-A) <b>Note: USB must supply a minimum of 900mA</b></span></span></td>
</tr><tr>
<td> <span data-ttu-id="bda05-315">Bluetooth</span><span class="sxs-lookup"><span data-stu-id="bda05-315">Bluetooth</span></span></td><td colspan="2"> <span data-ttu-id="bda05-316">Bluetooth 4.0 (適用於周邊連線)</span><span class="sxs-lookup"><span data-stu-id="bda05-316">Bluetooth 4.0 (for accessory connectivity)</span></span></td>
</tr>
</table>

<span data-ttu-id="bda05-317">如果您是首次使用 MRTK 進行原生開發，建議您依循我們策劃的原生開發旅程：</span><span class="sxs-lookup"><span data-stu-id="bda05-317">If you're new to Native development with MRTK, we recommend following our curated Native development journey:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="bda05-318">開始您的原生旅程</span><span class="sxs-lookup"><span data-stu-id="bda05-318">Start your Native journey</span></span>](../native/directx-development-overview.md)

## <a name="next-development-checkpoint"></a><span data-ttu-id="bda05-319">下一個開發檢查點</span><span class="sxs-lookup"><span data-stu-id="bda05-319">Next Development Checkpoint</span></span>

<span data-ttu-id="bda05-320">依循我們配置的 Native 開發檢查點旅程，您的下一個工作將是設定 HoloLens 2 的開發環境。</span><span class="sxs-lookup"><span data-stu-id="bda05-320">If you're following the Native development checkpoint journey we've laid out, your next task is to configure your development environment for HoloLens 2.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="bda05-321">設定 HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="bda05-321">Setup for HoloLens 2</span></span>](../native/openxr-getting-started.md#getting-started-with-openxr-for-hololens-2)

<span data-ttu-id="bda05-322">您可以隨時回到[原生開發檢查點](../native/directx-development-overview.md#1-getting-started)。</span><span class="sxs-lookup"><span data-stu-id="bda05-322">You can always go back to the [Native development checkpoints](../native/directx-development-overview.md#1-getting-started) at any time.</span></span>
