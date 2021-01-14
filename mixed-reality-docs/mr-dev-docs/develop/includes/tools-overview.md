---
ms.openlocfilehash: 4b9a1c20a8d885ea796c296f6a542d41e3ab58ef
ms.sourcegitcommit: b13c517df19179ca281362a1f006914289c58ad4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2021
ms.locfileid: "98052982"
---
# <a name="unity"></a>[<span data-ttu-id="731e1-101">Unity</span><span class="sxs-lookup"><span data-stu-id="731e1-101">Unity</span></span>](#tab/unity)

![Unity 標誌橫幅](../images/unity_logo_banner.png)<br>

### <a name="1-download-the-latest-version"></a><span data-ttu-id="731e1-103">1.下載最新版本</span><span class="sxs-lookup"><span data-stu-id="731e1-103">1. Download the latest version</span></span>

<span data-ttu-id="731e1-104">建議 [Unity LTS (長期支援)](https://unity3d.com/unity/qa/lts-releases) 資料流作為用來啟動新專案的最佳版本，並更新為其最新修訂版本，以挑選最新穩定的修正程式。</span><span class="sxs-lookup"><span data-stu-id="731e1-104">We recommend the [Unity LTS (Long Term Support)](https://unity3d.com/unity/qa/lts-releases) stream as the best version to use when starting new projects, updating to its latest revision to pick up the latest stable fixes.</span></span>
* <span data-ttu-id="731e1-105">目前建議使用 **Unity 2019**，這是以下 MRTK v2 所需的 LTS 組建。</span><span class="sxs-lookup"><span data-stu-id="731e1-105">The current recommendation is to use **Unity 2019**, which is the LTS build required for MRTK v2 below.</span></span>
* <span data-ttu-id="731e1-106">如果您基於特定理由而需要使用不同的 Unity 版本，Unity 支援不同版本的並存安裝。</span><span class="sxs-lookup"><span data-stu-id="731e1-106">If you need to use a different version of Unity for specific reasons, Unity supports side-by-side installs of different versions.</span></span>

### <a name="2-import-mixed-reality-toolkit-mrtk"></a><span data-ttu-id="731e1-107">2.匯入混合實境工具組 (MRTK)</span><span class="sxs-lookup"><span data-stu-id="731e1-107">2. Import Mixed Reality Toolkit (MRTK)</span></span>
![MRTK](../../design/images/MRTK_UX_Hero.png)

<span data-ttu-id="731e1-109">[混合實境工具組](../unity/mrtk-getting-started.md) (MRTK) 是混合實境應用程式的開放原始碼跨平台開發套件。</span><span class="sxs-lookup"><span data-stu-id="731e1-109">[Mixed Reality Toolkit](../unity/mrtk-getting-started.md) (MRTK) is an open-source, cross-platform development kit for mixed reality applications.</span></span> <span data-ttu-id="731e1-110">MRTK 提供跨平台輸入系統、基礎元件，以及空間互動的常見基本要素。</span><span class="sxs-lookup"><span data-stu-id="731e1-110">MRTK provides a cross-platform input system, foundational components, and common building blocks for spatial interactions.</span></span> <span data-ttu-id="731e1-111">該工具組主要用於加速開發以 Microsoft HoloLens、Windows Mixed Reality 沈浸式 (VR) 頭戴裝置和 OpenVR 平台為目標的應用程式。</span><span class="sxs-lookup"><span data-stu-id="731e1-111">The toolkit is intended to accelerate the development of applications targeting Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets, and the OpenVR platform.</span></span>

<span data-ttu-id="731e1-112">進行安裝時，建議您完成我們策劃的 [HoloLens](../unity/unity-development-overview.md#1-getting-started) 或 [VR](../unity/unity-development-wmr-overview.md#1-getting-started) 開發旅程中的開始使用一節。</span><span class="sxs-lookup"><span data-stu-id="731e1-112">For installation, we recommend completing the getting started section in our curated [HoloLens](../unity/unity-development-overview.md#1-getting-started) or [VR](../unity/unity-development-wmr-overview.md#1-getting-started) development journeys.</span></span> <span data-ttu-id="731e1-113">依循適用於 HoloLens 的 Unity 開發旅程，接下來請完成下列其餘的設定步驟，並繼續進行 [HoloLens 2 開始使用教學課程](../unity/tutorials/mr-learning-base-01.md)。</span><span class="sxs-lookup"><span data-stu-id="731e1-113">If you're already following the Unity development for HoloLens journey, finish up the rest of the setup steps listed below and continue on to the [HoloLens 2 Getting Started tutorials](../unity/tutorials/mr-learning-base-01.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="731e1-114">請注意，安裝指示的適用標的為 MRTK 和 Unity 最新的穩定版本組合，也就是 **MRTK 2.4.0** 和 **Unity 2019.3.15**。</span><span class="sxs-lookup"><span data-stu-id="731e1-114">Note that installation instructions are targeted for the latest stable combination of MRTK and Unity releases, which are **MRTK 2.4.0** and **Unity 2019.3.15**.</span></span>

> [!NOTE]
> <span data-ttu-id="731e1-115">如果您不想使用適用於 Unity 的 MRTK，則必須自行撰寫所有互動和行為的指令碼。</span><span class="sxs-lookup"><span data-stu-id="731e1-115">If you don't want to use MRTK for Unity, you'll need to script all interactions and behaviors yourself.</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="731e1-116"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">![Unity 橫幅](../images/MRTK-Unity-Banner.png)</span><span class="sxs-lookup"><span data-stu-id="731e1-116"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">![Unity banner](../images/MRTK-Unity-Banner.png)</span></span><br><span data-ttu-id="731e1-117">**混合實境工具組-Unity (GitHub)** </a></span><span class="sxs-lookup"><span data-stu-id="731e1-117">**Mixed Reality Toolkit-Unity (GitHub)**</a></span></span><br>
    :::column-end:::
:::row-end:::

#### <a name="other-tools-optional"></a><span data-ttu-id="731e1-118">其他工具 [選用]</span><span class="sxs-lookup"><span data-stu-id="731e1-118">Other tools [optional]</span></span>
* <span data-ttu-id="731e1-119"><a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">混合實境配套工具組 (GitHub)</a> - 無法直接在 HoloLens 或沈浸式 (VR) 頭戴裝置上執行的程式碼位元和元件，但是將其搭配使用可打造以 Windows Mixed Reality 為目標的體驗。</span><span class="sxs-lookup"><span data-stu-id="731e1-119"><a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">Mixed Reality Companion Kit (GitHub)</a> - code bits and components that might not run directly on HoloLens or immersive (VR) headsets, but instead pair with them to build experiences targeting Windows Mixed Reality.</span></span>
* <span data-ttu-id="731e1-120"><a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">混合的現實工具組 - 通用 (GitHub)</a> - 共用指令碼和元件的集合。</span><span class="sxs-lookup"><span data-stu-id="731e1-120"><a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">Mixed Reality Toolkit - Common (GitHub)</a> - a collection of shared scripts and components.</span></span>

### <a name="3-set-up-your-pc-for-mixed-reality-development"></a><span data-ttu-id="731e1-121">3.設定您的電腦以便進行混合實境開發</span><span class="sxs-lookup"><span data-stu-id="731e1-121">3. Set up your PC for Mixed Reality development</span></span>

<span data-ttu-id="731e1-122">Windows 10 SDK 最適合用於 Windows 10 作業系統。</span><span class="sxs-lookup"><span data-stu-id="731e1-122">The Windows 10 SDK works best on the Windows 10 operating system.</span></span> <span data-ttu-id="731e1-123">Windows 8.1、Windows 8、Windows 7、Windows Server 2012、Windows Server 2008 R2 也支援此 SDK。</span><span class="sxs-lookup"><span data-stu-id="731e1-123">This SDK is also supported on Windows 8.1, Windows 8, Windows 7, Windows Server 2012, Windows Server 2008 R2.</span></span> <span data-ttu-id="731e1-124">請注意，舊版作業系統不支援所有工具。</span><span class="sxs-lookup"><span data-stu-id="731e1-124">Note that not all tools are supported on older operating systems.</span></span>

> [!NOTE]
> <span data-ttu-id="731e1-125">您可以針對 HoloLens、VR 沉浸式頭戴裝置或兩者開發及部署應用程式。</span><span class="sxs-lookup"><span data-stu-id="731e1-125">You can develop and deploy your apps for HoloLens, VR immersive headsets, or both.</span></span> <span data-ttu-id="731e1-126">視您的需求而定，請確定您符合下列需求。</span><span class="sxs-lookup"><span data-stu-id="731e1-126">Make sure you fulfill the requirements below depending on your needs.</span></span>

#### <a name="for-hololens-development"></a><span data-ttu-id="731e1-127">對於 HoloLens 開發</span><span class="sxs-lookup"><span data-stu-id="731e1-127">For HoloLens development</span></span>

<span data-ttu-id="731e1-128">設定您的開發電腦以便進行 HoloLens 開發時，請確定其同時符合 <a href="https://unity3d.com/unity/system-requirements" target="_blank">Unity</a> 和 <a href="https://docs.microsoft.com//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a> 的系統需求。</span><span class="sxs-lookup"><span data-stu-id="731e1-128">When setting up your development PC for HoloLens development, please make sure it meets the system requirements for both <a href="https://unity3d.com/unity/system-requirements" target="_blank">Unity</a> and <a href="https://docs.microsoft.com//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a>.</span></span> <span data-ttu-id="731e1-129">如果您想要在 HoloLens 裝置上執行您的應用程式，則必須遵循 [Windows 裝置入口網站安裝指示](../platform-capabilities-and-apis/using-the-windows-device-portal.md#setting-up-hololens-to-use-windows-device-portal)。</span><span class="sxs-lookup"><span data-stu-id="731e1-129">If you want to run your app on a HoloLens device, you need to follow the [Windows Device Portal setup instructions](../platform-capabilities-and-apis/using-the-windows-device-portal.md#setting-up-hololens-to-use-windows-device-portal).</span></span> <span data-ttu-id="731e1-130">如果您打算使用 [HoloLens 模擬器](../platform-capabilities-and-apis/using-the-hololens-emulator.md)，您應確定您的電腦也符合 [HoloLens 模擬器系統需求](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements)。</span><span class="sxs-lookup"><span data-stu-id="731e1-130">If you plan on using the [HoloLens emulator](../platform-capabilities-and-apis/using-the-hololens-emulator.md), you'll want to make sure your PC meets the [HoloLens emulator system requirements](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements) as well.</span></span>

<span data-ttu-id="731e1-131">若要開始使用 HoloLens 模擬器，請參閱[使用 HoloLens 模擬器](../platform-capabilities-and-apis/using-the-hololens-emulator.md)。</span><span class="sxs-lookup"><span data-stu-id="731e1-131">To get started with the HoloLens emulator, see [Using the HoloLens emulator](../platform-capabilities-and-apis/using-the-hololens-emulator.md).</span></span>

<span data-ttu-id="731e1-132">如果您打算針對 HoloLens 與 Windows Mixed Reality 沈浸式 (VR) 頭戴裝置進行開發，請使用下一節中的系統建議和需求。</span><span class="sxs-lookup"><span data-stu-id="731e1-132">If you plan to develop for both HoloLens and Windows Mixed Reality immersive (VR) headsets, use the system recommendations and requirements in the section below.</span></span>

#### <a name="hololens-troubleshooting"></a><span data-ttu-id="731e1-133">HoloLens 疑難排解</span><span class="sxs-lookup"><span data-stu-id="731e1-133">HoloLens troubleshooting</span></span>

##### <a name="setting-developer-mode-is-grayed-out"></a><span data-ttu-id="731e1-134">設定開發人員模式呈現灰色</span><span class="sxs-lookup"><span data-stu-id="731e1-134">Setting Developer Mode is grayed out</span></span>

<span data-ttu-id="731e1-135">如果您在裝置上啟用開發人員模式時遇到問題，您可能不是[裝置擁有者](https://docs.microsoft.com/hololens/security-adminless-os)。</span><span class="sxs-lookup"><span data-stu-id="731e1-135">If you're running into issues enabling Developer Mode on your device you might not be the [device owner](https://docs.microsoft.com/hololens/security-adminless-os).</span></span> <span data-ttu-id="731e1-136">在多使用者模式中，第一個使用裝置的人員就是裝置擁有者，任何後續的使用者都不會擁有啟用 [開發人員模式] 或其他組態變更所需的權限。</span><span class="sxs-lookup"><span data-stu-id="731e1-136">In multi-user mode, the person who uses the device first is the device owner - any subsequent users won't have the required permissions to enable Developer Mode or other configuration changes.</span></span> <span data-ttu-id="731e1-137">不過，有一個例外狀況，那就是第一個使用者可能不是 Autopilot 環境中的裝置擁有者，這會在 [HoloLens 安全性文件](https://docs.microsoft.com/hololens/security-adminless-os#device-owner)詳述。</span><span class="sxs-lookup"><span data-stu-id="731e1-137">However, there is an exception where the first user may not be the device owner in an Autopilot environment, which is detailed in the [HoloLens security documentation](https://docs.microsoft.com/hololens/security-adminless-os#device-owner).</span></span>

<span data-ttu-id="731e1-138">可能的解決方案包括：</span><span class="sxs-lookup"><span data-stu-id="731e1-138">Possible solutions include:</span></span>

* <span data-ttu-id="731e1-139">在將裝置傳遞給其他使用者或開發人員之前，讓裝置擁有者開啟開發人員模式</span><span class="sxs-lookup"><span data-stu-id="731e1-139">Having the device owner turn Developer Mode on before passing the device to other users or developers</span></span>
* <span data-ttu-id="731e1-140">建議您的 IT/MDM 管理員針對特定裝置或開發人員裝置群組啟用 CSP [Policy ApplicationManagement/AllowDeveloperUnlock](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock)。</span><span class="sxs-lookup"><span data-stu-id="731e1-140">Suggesting that your IT/MDM Admin enables CSP [Policy ApplicationManagement/AllowDeveloperUnlock](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock) for the specific device or a developer device group.</span></span> 
    * <span data-ttu-id="731e1-141">此原則可經由[佈建套件](https://docs.microsoft.com/hololens/hololens-provisioning)或透過 [HoloLens 裝置的 MDM](https://docs.microsoft.com/hololens/hololens-mdm-configure) 來設定</span><span class="sxs-lookup"><span data-stu-id="731e1-141">This policy can be set by [Provisioning Packages](https://docs.microsoft.com/hololens/hololens-provisioning) or via [MDM for HoloLens devices](https://docs.microsoft.com/hololens/hololens-mdm-configure)</span></span>
* <span data-ttu-id="731e1-142">使用 [Advanced Recovery Companion (ARC)](https://docs.microsoft.com/hololens/hololens-recovery)</span><span class="sxs-lookup"><span data-stu-id="731e1-142">Using the [Advanced Recovery Companion (ARC)](https://docs.microsoft.com/hololens/hololens-recovery)</span></span>

> [!NOTE]
> <span data-ttu-id="731e1-143">您可以在 **[HoloLens 裝置管理](https://docs.microsoft.com/hololens/hololens-csp-policy-overview)** 概觀中深入了解裝置管理。</span><span class="sxs-lookup"><span data-stu-id="731e1-143">You can learn more about device management in the **[HoloLens device management](https://docs.microsoft.com/hololens/hololens-csp-policy-overview)** overview.</span></span>

##### <a name="i-cant-deploy-over-usb"></a><span data-ttu-id="731e1-144">我無法透過 USB 部署</span><span class="sxs-lookup"><span data-stu-id="731e1-144">I can't deploy over USB</span></span>

<span data-ttu-id="731e1-145">如果您無法直接透過 USB 部署應用程式，請確定您符合上述所有的安裝需求，並遵循我們的[逐步教學課程](../unity/tutorials/mr-learning-base-02.md#building-and-deploying-to-your-hololens-2)。</span><span class="sxs-lookup"><span data-stu-id="731e1-145">If you're not able to deploy an application directly over USB, make sure you've met all the installation requirements listed above and follow our [step-by-step tutorial](../unity/tutorials/mr-learning-base-02.md#building-and-deploying-to-your-hololens-2).</span></span>

#### <a name="immersive-vr-headset-requirements"></a><span data-ttu-id="731e1-146">沈浸式 (VR) 頭戴式裝置需求</span><span class="sxs-lookup"><span data-stu-id="731e1-146">Immersive (VR) headset requirements</span></span>

>[!NOTE]
><span data-ttu-id="731e1-147">下列指導方針是沈浸式 (VR) 頭戴裝置「開發電腦」目前的最低建議規格，而且會定期更新。</span><span class="sxs-lookup"><span data-stu-id="731e1-147">The following guidelines are the current minimum and recommended specs for your immersive (VR) headset *development PC*, and are updated regularly.</span></span>

>[!WARNING]
><span data-ttu-id="731e1-148">請勿將此指導方針與[最低電腦硬體相容性指導方針](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)混淆，其中概述了沈浸式 (VR) 頭戴裝置應用程式或遊戲應該定向的「取用者電腦規格」。</span><span class="sxs-lookup"><span data-stu-id="731e1-148">Do not confuse this with the [minimum PC hardware compatibility guidelines](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines), which outlines the *consumer PC specs* to which you should target your immersive (VR) headset app or game.</span></span>

<span data-ttu-id="731e1-149">如果沉浸式頭戴裝置開發電腦沒有完整大小的 HDMI 和/或 USB 3.0 連接埠，您需要[配接器](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs)才能連線頭戴式裝置。</span><span class="sxs-lookup"><span data-stu-id="731e1-149">If your immersive headset development PC does not have full-sized HDMI and/or USB 3.0 ports, you'll need [adapters](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs) to connect your headset.</span></span>

<span data-ttu-id="731e1-150">目前某些硬體設定有[已知問題](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)，尤其是具有混合式圖形的筆記型電腦。</span><span class="sxs-lookup"><span data-stu-id="731e1-150">There are currently [known issues](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality) with some hardware configurations, particularly notebooks that have hybrid graphics.</span></span>

<table>
<tr>
<th></th><th> <span data-ttu-id="731e1-151">最低需求</span><span class="sxs-lookup"><span data-stu-id="731e1-151">Minimum</span></span></th><th> <span data-ttu-id="731e1-152">建議</span><span class="sxs-lookup"><span data-stu-id="731e1-152">Recommended</span></span></th>
</tr><tr>
<td> <span data-ttu-id="731e1-153">處理器</span><span class="sxs-lookup"><span data-stu-id="731e1-153">Processor</span></span></td><td> <span data-ttu-id="731e1-154"><b>筆記型電腦：</b>Intel Mobile Core i5 第 7 代 CPU、採用超執行緒技術的雙核心 <b>傳統型：</b>Intel Desktop i5 第 6 代 CPU、採用超執行緒技術的雙核心<b>或</b> AMD FX4350 4.2Ghz 四核心對等項目</span><span class="sxs-lookup"><span data-stu-id="731e1-154"><b>Notebook:</b> Intel Mobile Core i5 7th generation CPU, Dual-Core with Hyper Threading <b>Desktop:</b> Intel Desktop i5 6th generation CPU, Dual-Core with Hyper Threading <b>OR</b> AMD FX4350 4.2Ghz Quad-Core equivalent</span></span></td><td> <span data-ttu-id="731e1-155"><b>傳統型：</b>Intel Desktop i7 第 6 代 (6 核心) <b>或</b> AMD Ryzen 5 1600 (6 核心，12 個執行緒)</span><span class="sxs-lookup"><span data-stu-id="731e1-155"><b>Desktop:</b> Intel Desktop i7 6th generation (6 Core) <b>OR</b> AMD Ryzen 5 1600 (6 Core, 12 threads)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="731e1-156">GPU</span><span class="sxs-lookup"><span data-stu-id="731e1-156">GPU</span></span></td><td> <span data-ttu-id="731e1-157"><b>筆記型電腦：</b>NVIDIA GTX 965M、AMD RX 460M (2GB) 對等項目或更高的 DX12 支援 GPU <b>傳統型：</b>NVIDIA GTX 960/1050、AMD Radeon RX 460 (2GB) 對等項目或更高的 DX12 支援 GPU</span><span class="sxs-lookup"><span data-stu-id="731e1-157"><b>Notebook:</b> NVIDIA GTX 965M, AMD RX 460M (2GB) equivalent or greater DX12 capable GPU <b>Desktop:</b> NVIDIA GTX 960/1050, AMD Radeon RX 460 (2GB) equivalent or greater DX12 capable GPU</span></span></td><td><span data-ttu-id="731e1-158"><b>傳統型：</b>NVIDIA GTX 980/1060、AMD Radeon RX 480 (2GB) 對等項目或更高的 DX12 支援 GPU</span><span class="sxs-lookup"><span data-stu-id="731e1-158"><b>Desktop:</b> NVIDIA GTX 980/1060, AMD Radeon RX 480 (2GB) equivalent or greater DX12 capable GPU</span></span></td>
</tr><tr>
<td> <span data-ttu-id="731e1-159">GPU 驅動程式 WDDM 版本</span><span class="sxs-lookup"><span data-stu-id="731e1-159">GPU driver WDDM version</span></span></td><td colspan="2"> <span data-ttu-id="731e1-160">WDDM 2.2 驅動程式</span><span class="sxs-lookup"><span data-stu-id="731e1-160">WDDM 2.2 driver</span></span></td>
</tr><tr>
<td> <span data-ttu-id="731e1-161">散熱設計功率</span><span class="sxs-lookup"><span data-stu-id="731e1-161">Thermal Design Power</span></span></td><td colspan="2"> <span data-ttu-id="731e1-162">15W 或更大</span><span class="sxs-lookup"><span data-stu-id="731e1-162">15W or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="731e1-163">圖形顯示連接埠</span><span class="sxs-lookup"><span data-stu-id="731e1-163">Graphics display ports</span></span></td><td colspan="2"> <span data-ttu-id="731e1-164">適用於頭戴式裝置的 1x 可用圖形顯示連接埠 (適用於 60Hz 頭戴式裝置的 HDMI 1.4 或 DisplayPort 1.2，適用於 90Hz 頭戴式裝置的 HDMI 2.0 或 DisplayPort 1.2)</span><span class="sxs-lookup"><span data-stu-id="731e1-164">1x available graphics display port for&#160;headset (HDMI 1.4 or DisplayPort 1.2 for 60Hz headsets, HDMI 2.0 or DisplayPort 1.2 for 90Hz headsets)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="731e1-165">顯示器解析度</span><span class="sxs-lookup"><span data-stu-id="731e1-165">Display resolution</span></span></td><td colspan="2"> <span data-ttu-id="731e1-166">解決方法：SVGA (800 x 600) 或更大的位元深度：每像素 32 位元的色彩</span><span class="sxs-lookup"><span data-stu-id="731e1-166">Resolution: SVGA (800x600) or greater Bit depth: 32 bits of color per pixel</span></span></td>
</tr><tr>
<td> <span data-ttu-id="731e1-167">Memory</span><span class="sxs-lookup"><span data-stu-id="731e1-167">Memory</span></span></td><td> <span data-ttu-id="731e1-168">8&#160;GB RAM 或更大</span><span class="sxs-lookup"><span data-stu-id="731e1-168">8&#160;GB of RAM or greater</span></span></td><td> <span data-ttu-id="731e1-169">16 GB RAM 或更大</span><span class="sxs-lookup"><span data-stu-id="731e1-169">16 GB of RAM or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="731e1-170">存放裝置</span><span class="sxs-lookup"><span data-stu-id="731e1-170">Storage</span></span></td><td colspan="2"> <span data-ttu-id="731e1-171">&gt;10 GB 額外可用空間</span><span class="sxs-lookup"><span data-stu-id="731e1-171">&gt;10 GB additional free space</span></span></td>
</tr><tr>
<td> <span data-ttu-id="731e1-172">USB 連接埠</span><span class="sxs-lookup"><span data-stu-id="731e1-172">USB Ports</span></span></td><td colspan="2"> <span data-ttu-id="731e1-173">適用於頭戴式裝置的 1x 可用 USB 連接埠 (USB 3.0 Type-A) <b>注意：USB 必須提供至少 900mA</b></span><span class="sxs-lookup"><span data-stu-id="731e1-173">1x available USB port for headset (USB 3.0 Type-A) <b>Note: USB must supply a minimum of 900mA</b></span></span></td>
</tr><tr>
<td> <span data-ttu-id="731e1-174">Bluetooth</span><span class="sxs-lookup"><span data-stu-id="731e1-174">Bluetooth</span></span></td><td colspan="2"> <span data-ttu-id="731e1-175">Bluetooth 4.0 (適用於周邊連線)</span><span class="sxs-lookup"><span data-stu-id="731e1-175">Bluetooth 4.0 (for accessory connectivity)</span></span></td>
</tr>
</table>

<span data-ttu-id="731e1-176">如果您是首次使用 Unity 進行 MRTK 開發，建議您依循我們策劃的 Unity 開發旅程：</span><span class="sxs-lookup"><span data-stu-id="731e1-176">If you're new to MRTK development with Unity, we recommend following our curated Unity development journey:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="731e1-177">開始您適用於 HoloLens 的 Unity 開發旅程</span><span class="sxs-lookup"><span data-stu-id="731e1-177">Start your Unity for HoloLens journey</span></span>](../unity/unity-development-overview.md)

> [!div class="nextstepaction"]
> [<span data-ttu-id="731e1-178">開始您適用於 VR 的 Unity 開發旅程</span><span class="sxs-lookup"><span data-stu-id="731e1-178">Start your Unity for VR journey</span></span>](../unity/unity-development-wmr-overview.md)

## <a name="next-development-checkpoint"></a><span data-ttu-id="731e1-179">下一個開發檢查點</span><span class="sxs-lookup"><span data-stu-id="731e1-179">Next Development Checkpoint</span></span>

<span data-ttu-id="731e1-180">依循我們所配置適用於 HoloLens 的 Unity 開發檢查點旅程，您的下一個工作將是進行 HoloLens 2 教學課程系列。</span><span class="sxs-lookup"><span data-stu-id="731e1-180">If you're following the Unity for HoloLens development checkpoint journey we've laid out, your next task is to work through our HoloLens 2 tutorial series.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="731e1-181">HoloLens 2 教學課程系列</span><span class="sxs-lookup"><span data-stu-id="731e1-181">HoloLens 2 tutorial series</span></span>](../unity/tutorials/mr-learning-base-01.md)

<span data-ttu-id="731e1-182">如果您要依循適用於 VR 的 Unity 旅程，下一個工作是設定您的專案。</span><span class="sxs-lookup"><span data-stu-id="731e1-182">If you're following the Unity for VR journey, your next task is to setup your project.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="731e1-183">針對 WMR 設定您的專案</span><span class="sxs-lookup"><span data-stu-id="731e1-183">Configuring your project for WMR</span></span>](../unity/configure-unity-project.md)

<span data-ttu-id="731e1-184">您可以隨時回到適用於 [HoloLens](../unity/unity-development-overview.md#1-getting-started) 和 [VR](../unity/unity-development-wmr-overview.md#1-getting-started)的 Unity 開發檢查點。</span><span class="sxs-lookup"><span data-stu-id="731e1-184">You can always go back to the Unity development checkpoints for [HoloLens](../unity/unity-development-overview.md#1-getting-started) and [VR](../unity/unity-development-wmr-overview.md#1-getting-started) at any time.</span></span>

# <a name="unreal"></a>[<span data-ttu-id="731e1-185">Unreal</span><span class="sxs-lookup"><span data-stu-id="731e1-185">Unreal</span></span>](#tab/unreal)

![Unreal](../images/unreal_logo_banner.png)

### <a name="1-download-the-latest-version"></a><span data-ttu-id="731e1-187">1.下載最新版本</span><span class="sxs-lookup"><span data-stu-id="731e1-187">1. Download the latest version</span></span>

<span data-ttu-id="731e1-188">建議您安裝 [Unreal Engine 4.25 版](https://docs.unrealengine.com//GettingStarted/Installation/index.html)或更新版本，以充分利用內建的 HoloLens 支援。</span><span class="sxs-lookup"><span data-stu-id="731e1-188">We recommend installing [Unreal Engine version 4.25](https://docs.unrealengine.com//GettingStarted/Installation/index.html) or later to take full advantage of built-in HoloLens support.</span></span>

### <a name="2-import-mixed-reality-toolkit-mrtk"></a><span data-ttu-id="731e1-189">2.匯入混合實境工具組 (MRTK)</span><span class="sxs-lookup"><span data-stu-id="731e1-189">2. Import Mixed Reality Toolkit (MRTK)</span></span>
![MRTK](../../design/images/MRTK_UX_Hero.png)

<span data-ttu-id="731e1-191">混合實境工具組 (MRTK) 是混合實境應用程式的開放原始碼跨平台開發套件。</span><span class="sxs-lookup"><span data-stu-id="731e1-191">Mixed Reality Toolkit (MRTK) is an open-source, cross-platform development kit for mixed reality applications.</span></span> <span data-ttu-id="731e1-192">MRTK 提供跨平台輸入系統、基礎元件，以及空間互動的常見基本要素。</span><span class="sxs-lookup"><span data-stu-id="731e1-192">MRTK provides a cross-platform input system, foundational components, and common building blocks for spatial interactions.</span></span> <span data-ttu-id="731e1-193">該工具組主要用於加速開發以 Microsoft HoloLens、Windows Mixed Reality 沈浸式 (VR) 頭戴裝置和 OpenVR 平台為目標的應用程式。</span><span class="sxs-lookup"><span data-stu-id="731e1-193">The toolkit is intended to accelerate the development of applications targeting Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets, and the OpenVR platform.</span></span>

<span data-ttu-id="731e1-194">進行安裝時，建議您完成我們策劃的 [Unreal 開發旅程圖](../unreal/unreal-development-overview.md)的[開始使用一節](../unreal/unreal-development-overview.md#1-getting-started)。</span><span class="sxs-lookup"><span data-stu-id="731e1-194">For installation, we recommend completing the [Getting Started section](../unreal/unreal-development-overview.md#1-getting-started) of our curated [Unreal development journey](../unreal/unreal-development-overview.md).</span></span> <span data-ttu-id="731e1-195">依循 Unreal 開發旅程，接下來請完成下列其餘的設定步驟，並繼續進行 [HoloLens 2 開始使用教學課程](../unreal/tutorials/unreal-uxt-ch1.md)。</span><span class="sxs-lookup"><span data-stu-id="731e1-195">If you're already following the Unreal development journey, finish up the rest of the setup steps listed below and continue on to the [HoloLens 2 Getting Started tutorials](../unreal/tutorials/unreal-uxt-ch1.md).</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="731e1-196"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unreal" target="_blank">![Unity 標誌影像](../images/MRTK-Unreal-Banner.png)</span><span class="sxs-lookup"><span data-stu-id="731e1-196"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unreal" target="_blank">![Unity logo image](../images/MRTK-Unreal-Banner.png)</span></span><br><span data-ttu-id="731e1-197">**混合實境工具組-Unreal (GitHub)** </a></span><span class="sxs-lookup"><span data-stu-id="731e1-197">**Mixed Reality Toolkit-Unreal (GitHub)**</a></span></span><br>
    :::column-end:::
:::row-end:::

> [!NOTE]
> <span data-ttu-id="731e1-198">如果您不想使用適用於 Unreal 的 MRTK，則必須自行撰寫所有互動和行為的指令碼。</span><span class="sxs-lookup"><span data-stu-id="731e1-198">If you don't want to use MRTK for Unreal, you'll need to script all interactions and behaviors yourself.</span></span>

#### <a name="other-tools-optional"></a><span data-ttu-id="731e1-199">其他工具 [選用]</span><span class="sxs-lookup"><span data-stu-id="731e1-199">Other tools [optional]</span></span>
* <span data-ttu-id="731e1-200"><a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">混合實境配套工具組 (GitHub)</a> - 無法直接在 HoloLens 或沈浸式 (VR) 頭戴裝置上執行的程式碼位元和元件，但是將其搭配使用可打造以 Windows Mixed Reality 為目標的體驗。</span><span class="sxs-lookup"><span data-stu-id="731e1-200"><a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">Mixed Reality Companion Kit (GitHub)</a> - code bits and components that might not run directly on HoloLens or immersive (VR) headsets, but instead pair with them to build experiences targeting Windows Mixed Reality.</span></span>
* <span data-ttu-id="731e1-201"><a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">混合的現實工具組 - 通用 (GitHub)</a> - 共用指令碼和元件的集合。</span><span class="sxs-lookup"><span data-stu-id="731e1-201"><a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">Mixed Reality Toolkit - Co mmon (GitHub)</a> - a collection of shared scripts and components.</span></span>

### <a name="3-set-up-your-pc-for-mixed-reality-development"></a><span data-ttu-id="731e1-202">3.設定您的電腦以便進行混合實境開發</span><span class="sxs-lookup"><span data-stu-id="731e1-202">3. Set up your PC for mixed reality development</span></span>

<span data-ttu-id="731e1-203">Windows 10 SDK 最適合用於 Windows 10 作業系統。</span><span class="sxs-lookup"><span data-stu-id="731e1-203">The Windows 10 SDK works best on the Windows 10 operating system.</span></span> <span data-ttu-id="731e1-204">Windows 8.1、Windows 8、Windows 7、Windows Server 2012、Windows Server 2008 R2 也支援此 SDK。</span><span class="sxs-lookup"><span data-stu-id="731e1-204">This SDK is also supported on Windows 8.1, Windows 8, Windows 7, Windows Server 2012, Windows Server 2008 R2.</span></span> <span data-ttu-id="731e1-205">請注意，舊版作業系統不支援所有工具。</span><span class="sxs-lookup"><span data-stu-id="731e1-205">Note that not all tools are supported on older operating systems.</span></span>

> [!NOTE]
> <span data-ttu-id="731e1-206">您可以針對 HoloLens、VR 沉浸式頭戴裝置或兩者開發及部署應用程式。</span><span class="sxs-lookup"><span data-stu-id="731e1-206">You can develop and deploy your apps for HoloLens, VR immersive headsets, or both.</span></span> <span data-ttu-id="731e1-207">視您的需求而定，請確定您符合下列需求。</span><span class="sxs-lookup"><span data-stu-id="731e1-207">Make sure you fulfill the requirements below depending on your needs.</span></span>

#### <a name="for-hololens-development"></a><span data-ttu-id="731e1-208">對於 HoloLens 開發</span><span class="sxs-lookup"><span data-stu-id="731e1-208">For HoloLens development</span></span>

<span data-ttu-id="731e1-209">設定您的開發電腦以便進行 HoloLens 開發時，請確定您符合 [Unity](https://docs.unrealengine.com/GettingStarted/RecommendedSpecifications/index.html) 和 <a href="https://docs.microsoft.com//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a> 的系統需求。</span><span class="sxs-lookup"><span data-stu-id="731e1-209">When setting up your development PC for HoloLens development, please make sure you meet the system requirements for [Unreal](https://docs.unrealengine.com/GettingStarted/RecommendedSpecifications/index.html) and and <a href="https://docs.microsoft.com//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a>.</span></span> <span data-ttu-id="731e1-210">如果您想要在 HoloLens 裝置上執行您的應用程式，則必須遵循 [Windows 裝置入口網站安裝指示](../platform-capabilities-and-apis/using-the-windows-device-portal.md#setting-up-hololens-to-use-windows-device-portal)。</span><span class="sxs-lookup"><span data-stu-id="731e1-210">If you want to run your app on a HoloLens device, you need to follow the [Windows Device Portal setup instructions](../platform-capabilities-and-apis/using-the-windows-device-portal.md#setting-up-hololens-to-use-windows-device-portal).</span></span> <span data-ttu-id="731e1-211">如果您打算使用 [HoloLens 模擬器](../platform-capabilities-and-apis/using-the-hololens-emulator.md)，您應確定您的電腦也符合 [HoloLens 模擬器系統需求](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements)。</span><span class="sxs-lookup"><span data-stu-id="731e1-211">If you plan on using the [HoloLens emulator](../platform-capabilities-and-apis/using-the-hololens-emulator.md), you'll want to make sure your PC meets the [HoloLens emulator system requirements](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements) as well.</span></span>

<span data-ttu-id="731e1-212">如果您打算針對 HoloLens 與 Windows Mixed Reality 沈浸式 (VR) 頭戴裝置進行開發，請使用下一節中的系統建議和需求。</span><span class="sxs-lookup"><span data-stu-id="731e1-212">If you plan to develop for both HoloLens and Windows Mixed Reality immersive (VR) headsets, use the system recommendations and requirements in the section below.</span></span>

#### <a name="hololens-troubleshooting"></a><span data-ttu-id="731e1-213">HoloLens 疑難排解</span><span class="sxs-lookup"><span data-stu-id="731e1-213">HoloLens troubleshooting</span></span>

##### <a name="setting-developer-mode-is-grayed-out"></a><span data-ttu-id="731e1-214">設定開發人員模式呈現灰色</span><span class="sxs-lookup"><span data-stu-id="731e1-214">Setting Developer Mode is grayed out</span></span>

<span data-ttu-id="731e1-215">如果您在裝置上啟用開發人員模式時遇到問題，您可能不是[裝置擁有者](https://docs.microsoft.com/hololens/security-adminless-os)。</span><span class="sxs-lookup"><span data-stu-id="731e1-215">If you're running into issues enabling Developer Mode on your device you might not be the [device owner](https://docs.microsoft.com/hololens/security-adminless-os).</span></span> <span data-ttu-id="731e1-216">在多使用者模式中，第一個使用裝置的人員就是裝置擁有者，任何後續的使用者都不會擁有啟用 [開發人員模式] 或其他組態變更所需的權限。</span><span class="sxs-lookup"><span data-stu-id="731e1-216">In multi-user mode, the person who uses the device first is the device owner - any subsequent users won't have the required permissions to enable Developer Mode or other configuration changes.</span></span> <span data-ttu-id="731e1-217">不過，有一個例外狀況，那就是第一個使用者可能不是 Autopilot 環境中的裝置擁有者，這會在 [HoloLens 安全性文件](https://docs.microsoft.com/hololens/security-adminless-os#device-owner)詳述。</span><span class="sxs-lookup"><span data-stu-id="731e1-217">However, there is an exception where the first user may not be the device owner in an Autopilot environment, which is detailed in the [HoloLens security documentation](https://docs.microsoft.com/hololens/security-adminless-os#device-owner).</span></span>

<span data-ttu-id="731e1-218">可能的解決方案包括：</span><span class="sxs-lookup"><span data-stu-id="731e1-218">Possible solutions include:</span></span>

* <span data-ttu-id="731e1-219">在將裝置傳遞給其他使用者或開發人員之前，讓裝置擁有者開啟開發人員模式</span><span class="sxs-lookup"><span data-stu-id="731e1-219">Having the device owner turn Developer Mode on before passing the device to other users or developers</span></span>
* <span data-ttu-id="731e1-220">建議您的 IT/MDM 管理員針對特定裝置或開發人員裝置群組啟用 CSP [Policy ApplicationManagement/AllowDeveloperUnlock](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock)。</span><span class="sxs-lookup"><span data-stu-id="731e1-220">Suggesting that your IT/MDM Admin enables CSP [Policy ApplicationManagement/AllowDeveloperUnlock](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock) for the specific device or a developer device group.</span></span> 
    * <span data-ttu-id="731e1-221">此原則可經由[佈建套件](https://docs.microsoft.com/hololens/hololens-provisioning)或透過 [HoloLens 裝置的 MDM](https://docs.microsoft.com/hololens/hololens-mdm-configure) 來設定</span><span class="sxs-lookup"><span data-stu-id="731e1-221">This policy can be set by [Provisioning Packages](https://docs.microsoft.com/hololens/hololens-provisioning) or via [MDM for HoloLens devices](https://docs.microsoft.com/hololens/hololens-mdm-configure)</span></span>
* <span data-ttu-id="731e1-222">使用 [Advanced Recovery Companion (ARC)](https://docs.microsoft.com/hololens/hololens-recovery)</span><span class="sxs-lookup"><span data-stu-id="731e1-222">Using the [Advanced Recovery Companion (ARC)](https://docs.microsoft.com/hololens/hololens-recovery)</span></span>

> [!NOTE]
> <span data-ttu-id="731e1-223">您可以在 **[HoloLens 裝置管理](https://docs.microsoft.com/hololens/hololens-csp-policy-overview)** 概觀中深入了解裝置管理。</span><span class="sxs-lookup"><span data-stu-id="731e1-223">You can learn more about device management in the **[HoloLens device management](https://docs.microsoft.com/hololens/hololens-csp-policy-overview)** overview.</span></span>

##### <a name="i-cant-deploy-over-usb"></a><span data-ttu-id="731e1-224">我無法透過 USB 部署</span><span class="sxs-lookup"><span data-stu-id="731e1-224">I can't deploy over USB</span></span>

<span data-ttu-id="731e1-225">如果您無法直接透過 USB 部署應用程式，請確定您符合上述所有的安裝需求，並遵循我們的[逐步教學課程](../unreal/tutorials/unreal-uxt-ch6.md)。</span><span class="sxs-lookup"><span data-stu-id="731e1-225">If you're not able to deploy an application directly over USB, make sure you've met all the installation requirements listed above and follow our [step-by-step tutorial](../unreal/tutorials/unreal-uxt-ch6.md).</span></span>

#### <a name="immersive-vr-headset-requirements"></a><span data-ttu-id="731e1-226">沈浸式 (VR) 頭戴式裝置需求</span><span class="sxs-lookup"><span data-stu-id="731e1-226">Immersive (VR) headset requirements</span></span>

>[!NOTE]
><span data-ttu-id="731e1-227">下列指導方針是沈浸式 (VR) 頭戴裝置「開發電腦」目前的最低建議規格，而且會定期更新。</span><span class="sxs-lookup"><span data-stu-id="731e1-227">The following guidelines are the current minimum and recommended specs for your immersive (VR) headset *development PC*, and are updated regularly.</span></span>

>[!WARNING]
><span data-ttu-id="731e1-228">請勿將此指導方針與[最低電腦硬體相容性指導方針](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)混淆，其中概述了沈浸式 (VR) 頭戴裝置應用程式或遊戲應該定向的「取用者電腦規格」。</span><span class="sxs-lookup"><span data-stu-id="731e1-228">Do not confuse this with the [minimum PC hardware compatibility guidelines](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines), which outlines the *consumer PC specs* to which you should target your immersive (VR) headset app or game.</span></span>

<span data-ttu-id="731e1-229">如果沉浸式頭戴裝置開發電腦沒有完整大小的 HDMI 和/或 USB 3.0 連接埠，您需要[配接器](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs)才能連線頭戴式裝置。</span><span class="sxs-lookup"><span data-stu-id="731e1-229">If your immersive headset development PC does not have full-sized HDMI and/or USB 3.0 ports, you'll need [adapters](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs) to connect your headset.</span></span>

<span data-ttu-id="731e1-230">目前某些硬體設定有[已知問題](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)，尤其是具有混合式圖形的筆記型電腦。</span><span class="sxs-lookup"><span data-stu-id="731e1-230">There are currently [known issues](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality) with some hardware configurations, particularly notebooks that have hybrid graphics.</span></span>

<table>
<tr>
<th></th><th> <span data-ttu-id="731e1-231">最低需求</span><span class="sxs-lookup"><span data-stu-id="731e1-231">Minimum</span></span></th><th> <span data-ttu-id="731e1-232">建議</span><span class="sxs-lookup"><span data-stu-id="731e1-232">Recommended</span></span></th>
</tr><tr>
<td> <span data-ttu-id="731e1-233">處理器</span><span class="sxs-lookup"><span data-stu-id="731e1-233">Processor</span></span></td><td> <span data-ttu-id="731e1-234"><b>筆記型電腦：</b>Intel Mobile Core i5 第 7 代 CPU、採用超執行緒技術的雙核心 <b>傳統型：</b>Intel Desktop i5 第 6 代 CPU、採用超執行緒技術的雙核心<b>或</b> AMD FX4350 4.2Ghz 四核心對等項目</span><span class="sxs-lookup"><span data-stu-id="731e1-234"><b>Notebook:</b> Intel Mobile Core i5 7th generation CPU, Dual-Core with Hyper Threading <b>Desktop:</b> Intel Desktop i5 6th generation CPU, Dual-Core with Hyper Threading <b>OR</b> AMD FX4350 4.2Ghz Quad-Core equivalent</span></span></td><td> <span data-ttu-id="731e1-235"><b>傳統型：</b>Intel Desktop i7 第 6 代 (6 核心) <b>或</b> AMD Ryzen 5 1600 (6 核心，12 個執行緒)</span><span class="sxs-lookup"><span data-stu-id="731e1-235"><b>Desktop:</b> Intel Desktop i7 6th generation (6 Core) <b>OR</b> AMD Ryzen 5 1600 (6 Core, 12 threads)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="731e1-236">GPU</span><span class="sxs-lookup"><span data-stu-id="731e1-236">GPU</span></span></td><td> <span data-ttu-id="731e1-237"><b>筆記型電腦：</b>NVIDIA GTX 965M、AMD RX 460M (2GB) 對等項目或更高的 DX12 支援 GPU <b>傳統型：</b>NVIDIA GTX 960/1050、AMD Radeon RX 460 (2GB) 對等項目或更高的 DX12 支援 GPU</span><span class="sxs-lookup"><span data-stu-id="731e1-237"><b>Notebook:</b> NVIDIA GTX 965M, AMD RX 460M (2GB) equivalent or greater DX12 capable GPU <b>Desktop:</b> NVIDIA GTX 960/1050, AMD Radeon RX 460 (2GB) equivalent or greater DX12 capable GPU</span></span></td><td><span data-ttu-id="731e1-238"><b>傳統型：</b>NVIDIA GTX 980/1060、AMD Radeon RX 480 (2GB) 對等項目或更高的 DX12 支援 GPU</span><span class="sxs-lookup"><span data-stu-id="731e1-238"><b>Desktop:</b> NVIDIA GTX 980/1060, AMD Radeon RX 480 (2GB) equivalent or greater DX12 capable GPU</span></span></td>
</tr><tr>
<td> <span data-ttu-id="731e1-239">GPU 驅動程式 WDDM 版本</span><span class="sxs-lookup"><span data-stu-id="731e1-239">GPU driver WDDM version</span></span></td><td colspan="2"> <span data-ttu-id="731e1-240">WDDM 2.2 驅動程式</span><span class="sxs-lookup"><span data-stu-id="731e1-240">WDDM 2.2 driver</span></span></td>
</tr><tr>
<td> <span data-ttu-id="731e1-241">散熱設計功率</span><span class="sxs-lookup"><span data-stu-id="731e1-241">Thermal Design Power</span></span></td><td colspan="2"> <span data-ttu-id="731e1-242">15W 或更大</span><span class="sxs-lookup"><span data-stu-id="731e1-242">15W or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="731e1-243">圖形顯示連接埠</span><span class="sxs-lookup"><span data-stu-id="731e1-243">Graphics display ports</span></span></td><td colspan="2"> <span data-ttu-id="731e1-244">適用於頭戴式裝置的 1x 可用圖形顯示連接埠 (適用於 60Hz 頭戴式裝置的 HDMI 1.4 或 DisplayPort 1.2，適用於 90Hz 頭戴式裝置的 HDMI 2.0 或 DisplayPort 1.2)</span><span class="sxs-lookup"><span data-stu-id="731e1-244">1x available graphics display port for&#160;headset (HDMI 1.4 or DisplayPort 1.2 for 60Hz headsets, HDMI 2.0 or DisplayPort 1.2 for 90Hz headsets)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="731e1-245">顯示器解析度</span><span class="sxs-lookup"><span data-stu-id="731e1-245">Display resolution</span></span></td><td colspan="2"> <span data-ttu-id="731e1-246">解決方法：SVGA (800 x 600) 或更大的位元深度：每像素 32 位元的色彩</span><span class="sxs-lookup"><span data-stu-id="731e1-246">Resolution: SVGA (800x600) or greater Bit depth: 32 bits of color per pixel</span></span></td>
</tr><tr>
<td> <span data-ttu-id="731e1-247">Memory</span><span class="sxs-lookup"><span data-stu-id="731e1-247">Memory</span></span></td><td> <span data-ttu-id="731e1-248">8&#160;GB RAM 或更大</span><span class="sxs-lookup"><span data-stu-id="731e1-248">8&#160;GB of RAM or greater</span></span></td><td> <span data-ttu-id="731e1-249">16 GB RAM 或更大</span><span class="sxs-lookup"><span data-stu-id="731e1-249">16 GB of RAM or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="731e1-250">存放裝置</span><span class="sxs-lookup"><span data-stu-id="731e1-250">Storage</span></span></td><td colspan="2"> <span data-ttu-id="731e1-251">&gt;10 GB 額外可用空間</span><span class="sxs-lookup"><span data-stu-id="731e1-251">&gt;10 GB additional free space</span></span></td>
</tr><tr>
<td> <span data-ttu-id="731e1-252">USB 連接埠</span><span class="sxs-lookup"><span data-stu-id="731e1-252">USB Ports</span></span></td><td colspan="2"> <span data-ttu-id="731e1-253">適用於頭戴式裝置的 1x 可用 USB 連接埠 (USB 3.0 Type-A) <b>注意：USB 必須提供至少 900mA</b></span><span class="sxs-lookup"><span data-stu-id="731e1-253">1x available USB port for headset (USB 3.0 Type-A) <b>Note: USB must supply a minimum of 900mA</b></span></span></td>
</tr><tr>
<td> <span data-ttu-id="731e1-254">Bluetooth</span><span class="sxs-lookup"><span data-stu-id="731e1-254">Bluetooth</span></span></td><td colspan="2"> <span data-ttu-id="731e1-255">Bluetooth 4.0 (適用於周邊連線)</span><span class="sxs-lookup"><span data-stu-id="731e1-255">Bluetooth 4.0 (for accessory connectivity)</span></span></td>
</tr>
</table>

<span data-ttu-id="731e1-256">如果您是首次使用 Unreal 進行 MRTK 開發，建議您依循我們策劃的 Unreal 開發旅程：</span><span class="sxs-lookup"><span data-stu-id="731e1-256">If you're new to MRTK development with Unreal, we recommend following our curated Unreal development journey:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="731e1-257">開始您的 Unreal 旅程</span><span class="sxs-lookup"><span data-stu-id="731e1-257">Start your Unreal journey</span></span>](../unreal/unreal-development-overview.md)

## <a name="next-development-checkpoint"></a><span data-ttu-id="731e1-258">下一個開發檢查點</span><span class="sxs-lookup"><span data-stu-id="731e1-258">Next Development Checkpoint</span></span>

<span data-ttu-id="731e1-259">依循我們配置的 Unreal 開發檢查點旅程，您的下一個工作將是進行 HoloLens 2 教學課程系列。</span><span class="sxs-lookup"><span data-stu-id="731e1-259">If you're following the Unreal development checkpoint journey we've laid out, your next task is to work through our HoloLens 2 tutorial series.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="731e1-260">HoloLens 2 教學課程系列</span><span class="sxs-lookup"><span data-stu-id="731e1-260">HoloLens 2 tutorial series</span></span>](../unreal/tutorials/unreal-uxt-ch1.md)

<span data-ttu-id="731e1-261">您可以隨時回到 [Unreal 開發檢查點](../unreal/unreal-development-overview.md#1-getting-started)。</span><span class="sxs-lookup"><span data-stu-id="731e1-261">You can always go back to the [Unreal development checkpoints](../unreal/unreal-development-overview.md#1-getting-started) at any time.</span></span>

# <a name="native-openxr"></a>[<span data-ttu-id="731e1-262">原生 (OpenXR)</span><span class="sxs-lookup"><span data-stu-id="731e1-262">Native (OpenXR)</span></span>](#tab/native)

 ![原生應用程式開發](../images/native_logo_banner.png)

<span data-ttu-id="731e1-264">原生 OpenXR 開發沒有可供您下載的引擎。</span><span class="sxs-lookup"><span data-stu-id="731e1-264">Native OpenXR development doesn't have an engine for you to download.</span></span> <span data-ttu-id="731e1-265">您可以在[開始使用 OpenXR](../native/openxr-getting-started.md) 文件中找到開始進行開發所需的一切資訊。</span><span class="sxs-lookup"><span data-stu-id="731e1-265">You can find everything you need to begin development in the [Getting started with OpenXR](../native/openxr-getting-started.md) document.</span></span>

### <a name="1-set-up-your-pc-for-mixed-reality-development"></a><span data-ttu-id="731e1-266">1.設定您的電腦以便進行混合實境開發</span><span class="sxs-lookup"><span data-stu-id="731e1-266">1. Set up your PC for mixed reality development</span></span>

<span data-ttu-id="731e1-267">Windows 10 SDK 最適合用於 Windows 10 作業系統。</span><span class="sxs-lookup"><span data-stu-id="731e1-267">The Windows 10 SDK works best on the Windows 10 operating system.</span></span> <span data-ttu-id="731e1-268">Windows 8.1、Windows 8、Windows 7、Windows Server 2012、Windows Server 2008 R2 也支援此 SDK。</span><span class="sxs-lookup"><span data-stu-id="731e1-268">This SDK is also supported on Windows 8.1, Windows 8, Windows 7, Windows Server 2012, Windows Server 2008 R2.</span></span> <span data-ttu-id="731e1-269">請注意，舊版作業系統不支援所有工具。</span><span class="sxs-lookup"><span data-stu-id="731e1-269">Note that not all tools are supported on older operating systems.</span></span>

#### <a name="for-hololens-development"></a><span data-ttu-id="731e1-270">對於 HoloLens 開發</span><span class="sxs-lookup"><span data-stu-id="731e1-270">For HoloLens development</span></span>

<span data-ttu-id="731e1-271">設定您的開發電腦以便進行 HoloLens 開發時，請確定您符合 <a href="https://docs.microsoft.com//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a> 的系統需求。</span><span class="sxs-lookup"><span data-stu-id="731e1-271">When setting up your development PC for HoloLens development, please make sure you meet the system requirements for <a href="https://docs.microsoft.com//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a>.</span></span> <span data-ttu-id="731e1-272">如果您想要在 HoloLens 裝置上執行您的應用程式，則必須遵循 [Windows 裝置入口網站安裝指示](../platform-capabilities-and-apis/using-the-windows-device-portal.md#setting-up-hololens-to-use-windows-device-portal)。</span><span class="sxs-lookup"><span data-stu-id="731e1-272">If you want to run your app on a HoloLens device, you need to follow the [Windows Device Portal setup instructions](../platform-capabilities-and-apis/using-the-windows-device-portal.md#setting-up-hololens-to-use-windows-device-portal).</span></span> <span data-ttu-id="731e1-273">如果您打算使用 [HoloLens 模擬器](../platform-capabilities-and-apis/using-the-hololens-emulator.md)，您應確定您的電腦也符合 [HoloLens 模擬器系統需求](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements)。</span><span class="sxs-lookup"><span data-stu-id="731e1-273">If you plan on using the [HoloLens emulator](../platform-capabilities-and-apis/using-the-hololens-emulator.md), you'll want to make sure your PC meets the [HoloLens emulator system requirements](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements) as well.</span></span>

<span data-ttu-id="731e1-274">如果您打算針對 HoloLens 與 Windows Mixed Reality 沈浸式 (VR) 頭戴裝置進行開發，請使用下一節中的系統建議和需求。</span><span class="sxs-lookup"><span data-stu-id="731e1-274">If you plan to develop for both HoloLens and Windows Mixed Reality immersive (VR) headsets, use the system recommendations and requirements in the section below.</span></span>

> [!NOTE]
> <span data-ttu-id="731e1-275">您可以針對 HoloLens、VR 沉浸式頭戴裝置或兩者開發及部署應用程式。</span><span class="sxs-lookup"><span data-stu-id="731e1-275">You can develop and deploy your apps for HoloLens, VR immersive headsets, or both.</span></span> <span data-ttu-id="731e1-276">視您的需求而定，請確定您符合下列需求。</span><span class="sxs-lookup"><span data-stu-id="731e1-276">Make sure you fulfill the requirements below depending on your needs.</span></span>

#### <a name="hololens-troubleshooting"></a><span data-ttu-id="731e1-277">HoloLens 疑難排解</span><span class="sxs-lookup"><span data-stu-id="731e1-277">HoloLens troubleshooting</span></span>

##### <a name="setting-developer-mode-is-grayed-out"></a><span data-ttu-id="731e1-278">設定開發人員模式呈現灰色</span><span class="sxs-lookup"><span data-stu-id="731e1-278">Setting Developer Mode is grayed out</span></span>

<span data-ttu-id="731e1-279">如果您在裝置上啟用開發人員模式時遇到問題，您可能不是[裝置擁有者](https://docs.microsoft.com/hololens/security-adminless-os)。</span><span class="sxs-lookup"><span data-stu-id="731e1-279">If you're running into issues enabling Developer Mode on your device you might not be the [device owner](https://docs.microsoft.com/hololens/security-adminless-os).</span></span> <span data-ttu-id="731e1-280">在多使用者模式中，第一個使用裝置的人員就是裝置擁有者，任何後續的使用者都不會擁有啟用 [開發人員模式] 或其他組態變更所需的權限。</span><span class="sxs-lookup"><span data-stu-id="731e1-280">In multi-user mode, the person who uses the device first is the device owner - any subsequent users won't have the required permissions to enable Developer Mode or other configuration changes.</span></span> <span data-ttu-id="731e1-281">不過，有一個例外狀況，那就是第一個使用者可能不是 Autopilot 環境中的裝置擁有者，這會在 [HoloLens 安全性文件](https://docs.microsoft.com/hololens/security-adminless-os#device-owner)詳述。</span><span class="sxs-lookup"><span data-stu-id="731e1-281">However, there is an exception where the first user may not be the device owner in an Autopilot environment, which is detailed in the [HoloLens security documentation](https://docs.microsoft.com/hololens/security-adminless-os#device-owner).</span></span>

<span data-ttu-id="731e1-282">可能的解決方案包括：</span><span class="sxs-lookup"><span data-stu-id="731e1-282">Possible solutions include:</span></span>

* <span data-ttu-id="731e1-283">在將裝置傳遞給其他使用者或開發人員之前，讓裝置擁有者開啟開發人員模式</span><span class="sxs-lookup"><span data-stu-id="731e1-283">Having the device owner turn Developer Mode on before passing the device to other users or developers</span></span>
* <span data-ttu-id="731e1-284">建議您的 IT/MDM 管理員針對特定裝置或開發人員裝置群組啟用 CSP [Policy ApplicationManagement/AllowDeveloperUnlock](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock)。</span><span class="sxs-lookup"><span data-stu-id="731e1-284">Suggesting that your IT/MDM Admin enables CSP [Policy ApplicationManagement/AllowDeveloperUnlock](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock) for the specific device or a developer device group.</span></span> 
    * <span data-ttu-id="731e1-285">此原則可經由[佈建套件](https://docs.microsoft.com/hololens/hololens-provisioning)或透過 [HoloLens 裝置的 MDM](https://docs.microsoft.com/hololens/hololens-mdm-configure) 來設定</span><span class="sxs-lookup"><span data-stu-id="731e1-285">This policy can be set by [Provisioning Packages](https://docs.microsoft.com/hololens/hololens-provisioning) or via [MDM for HoloLens devices](https://docs.microsoft.com/hololens/hololens-mdm-configure)</span></span>
* <span data-ttu-id="731e1-286">使用 [Advanced Recovery Companion (ARC)](https://docs.microsoft.com/hololens/hololens-recovery)</span><span class="sxs-lookup"><span data-stu-id="731e1-286">Using the [Advanced Recovery Companion (ARC)](https://docs.microsoft.com/hololens/hololens-recovery)</span></span>

> [!NOTE]
> <span data-ttu-id="731e1-287">您可以在 **[HoloLens 裝置管理](https://docs.microsoft.com/hololens/hololens-csp-policy-overview)** 概觀中深入了解裝置管理。</span><span class="sxs-lookup"><span data-stu-id="731e1-287">You can learn more about device management in the **[HoloLens device management](https://docs.microsoft.com/hololens/hololens-csp-policy-overview)** overview.</span></span>

#### <a name="immersive-vr-headset-requirements"></a><span data-ttu-id="731e1-288">沈浸式 (VR) 頭戴式裝置需求</span><span class="sxs-lookup"><span data-stu-id="731e1-288">Immersive (VR) headset requirements</span></span>

>[!NOTE]
><span data-ttu-id="731e1-289">下列指導方針是沈浸式 (VR) 頭戴裝置「開發電腦」目前的最低建議規格，而且會定期更新。</span><span class="sxs-lookup"><span data-stu-id="731e1-289">The following guidelines are the current minimum and recommended specs for your immersive (VR) headset *development PC*, and are updated regularly.</span></span>

>[!WARNING]
><span data-ttu-id="731e1-290">請勿將此指導方針與[最低電腦硬體相容性指導方針](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)混淆，其中概述了沈浸式 (VR) 頭戴裝置應用程式或遊戲應該定向的「取用者電腦規格」。</span><span class="sxs-lookup"><span data-stu-id="731e1-290">Do not confuse this with the [minimum PC hardware compatibility guidelines](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines), which outlines the *consumer PC specs* to which you should target your immersive (VR) headset app or game.</span></span>

<span data-ttu-id="731e1-291">如果沉浸式頭戴裝置開發電腦沒有完整大小的 HDMI 和/或 USB 3.0 連接埠，您需要[配接器](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs)才能連線頭戴式裝置。</span><span class="sxs-lookup"><span data-stu-id="731e1-291">If your immersive headset development PC does not have full-sized HDMI and/or USB 3.0 ports, you'll need [adapters](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs) to connect your headset.</span></span>

<span data-ttu-id="731e1-292">目前某些硬體設定有[已知問題](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)，尤其是具有混合式圖形的筆記型電腦。</span><span class="sxs-lookup"><span data-stu-id="731e1-292">There are currently [known issues](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality) with some hardware configurations, particularly notebooks that have hybrid graphics.</span></span>

<table>
<tr>
<th></th><th> <span data-ttu-id="731e1-293">最低需求</span><span class="sxs-lookup"><span data-stu-id="731e1-293">Minimum</span></span></th><th> <span data-ttu-id="731e1-294">建議</span><span class="sxs-lookup"><span data-stu-id="731e1-294">Recommended</span></span></th>
</tr><tr>
<td> <span data-ttu-id="731e1-295">處理器</span><span class="sxs-lookup"><span data-stu-id="731e1-295">Processor</span></span></td><td> <span data-ttu-id="731e1-296"><b>筆記型電腦：</b>Intel Mobile Core i5 第 7 代 CPU、採用超執行緒技術的雙核心 <b>傳統型：</b>Intel Desktop i5 第 6 代 CPU、採用超執行緒技術的雙核心<b>或</b> AMD FX4350 4.2Ghz 四核心對等項目</span><span class="sxs-lookup"><span data-stu-id="731e1-296"><b>Notebook:</b> Intel Mobile Core i5 7th generation CPU, Dual-Core with Hyper Threading <b>Desktop:</b> Intel Desktop i5 6th generation CPU, Dual-Core with Hyper Threading <b>OR</b> AMD FX4350 4.2Ghz Quad-Core equivalent</span></span></td><td> <span data-ttu-id="731e1-297"><b>傳統型：</b>Intel Desktop i7 第 6 代 (6 核心) <b>或</b> AMD Ryzen 5 1600 (6 核心，12 個執行緒)</span><span class="sxs-lookup"><span data-stu-id="731e1-297"><b>Desktop:</b> Intel Desktop i7 6th generation (6 Core) <b>OR</b> AMD Ryzen 5 1600 (6 Core, 12 threads)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="731e1-298">GPU</span><span class="sxs-lookup"><span data-stu-id="731e1-298">GPU</span></span></td><td> <span data-ttu-id="731e1-299"><b>筆記型電腦：</b>NVIDIA GTX 965M、AMD RX 460M (2GB) 對等項目或更高的 DX12 支援 GPU <b>傳統型：</b>NVIDIA GTX 960/1050、AMD Radeon RX 460 (2GB) 對等項目或更高的 DX12 支援 GPU</span><span class="sxs-lookup"><span data-stu-id="731e1-299"><b>Notebook:</b> NVIDIA GTX 965M, AMD RX 460M (2GB) equivalent or greater DX12 capable GPU <b>Desktop:</b> NVIDIA GTX 960/1050, AMD Radeon RX 460 (2GB) equivalent or greater DX12 capable GPU</span></span></td><td><span data-ttu-id="731e1-300"><b>傳統型：</b>NVIDIA GTX 980/1060、AMD Radeon RX 480 (2GB) 對等項目或更高的 DX12 支援 GPU</span><span class="sxs-lookup"><span data-stu-id="731e1-300"><b>Desktop:</b> NVIDIA GTX 980/1060, AMD Radeon RX 480 (2GB) equivalent or greater DX12 capable GPU</span></span></td>
</tr><tr>
<td> <span data-ttu-id="731e1-301">GPU 驅動程式 WDDM 版本</span><span class="sxs-lookup"><span data-stu-id="731e1-301">GPU driver WDDM version</span></span></td><td colspan="2"> <span data-ttu-id="731e1-302">WDDM 2.2 驅動程式</span><span class="sxs-lookup"><span data-stu-id="731e1-302">WDDM 2.2 driver</span></span></td>
</tr><tr>
<td> <span data-ttu-id="731e1-303">散熱設計功率</span><span class="sxs-lookup"><span data-stu-id="731e1-303">Thermal Design Power</span></span></td><td colspan="2"> <span data-ttu-id="731e1-304">15W 或更大</span><span class="sxs-lookup"><span data-stu-id="731e1-304">15W or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="731e1-305">圖形顯示連接埠</span><span class="sxs-lookup"><span data-stu-id="731e1-305">Graphics display ports</span></span></td><td colspan="2"> <span data-ttu-id="731e1-306">適用於頭戴式裝置的 1x 可用圖形顯示連接埠 (適用於 60Hz 頭戴式裝置的 HDMI 1.4 或 DisplayPort 1.2，適用於 90Hz 頭戴式裝置的 HDMI 2.0 或 DisplayPort 1.2)</span><span class="sxs-lookup"><span data-stu-id="731e1-306">1x available graphics display port for&#160;headset (HDMI 1.4 or DisplayPort 1.2 for 60Hz headsets, HDMI 2.0 or DisplayPort 1.2 for 90Hz headsets)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="731e1-307">顯示器解析度</span><span class="sxs-lookup"><span data-stu-id="731e1-307">Display resolution</span></span></td><td colspan="2"> <span data-ttu-id="731e1-308">解決方法：SVGA (800 x 600) 或更大的位元深度：每像素 32 位元的色彩</span><span class="sxs-lookup"><span data-stu-id="731e1-308">Resolution: SVGA (800x600) or greater Bit depth: 32 bits of color per pixel</span></span></td>
</tr><tr>
<td> <span data-ttu-id="731e1-309">Memory</span><span class="sxs-lookup"><span data-stu-id="731e1-309">Memory</span></span></td><td> <span data-ttu-id="731e1-310">8&#160;GB RAM 或更大</span><span class="sxs-lookup"><span data-stu-id="731e1-310">8&#160;GB of RAM or greater</span></span></td><td> <span data-ttu-id="731e1-311">16 GB RAM 或更大</span><span class="sxs-lookup"><span data-stu-id="731e1-311">16 GB of RAM or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="731e1-312">存放裝置</span><span class="sxs-lookup"><span data-stu-id="731e1-312">Storage</span></span></td><td colspan="2"> <span data-ttu-id="731e1-313">&gt;10 GB 額外可用空間</span><span class="sxs-lookup"><span data-stu-id="731e1-313">&gt;10 GB additional free space</span></span></td>
</tr><tr>
<td> <span data-ttu-id="731e1-314">USB 連接埠</span><span class="sxs-lookup"><span data-stu-id="731e1-314">USB Ports</span></span></td><td colspan="2"> <span data-ttu-id="731e1-315">適用於頭戴式裝置的 1x 可用 USB 連接埠 (USB 3.0 Type-A) <b>注意：USB 必須提供至少 900mA</b></span><span class="sxs-lookup"><span data-stu-id="731e1-315">1x available USB port for headset (USB 3.0 Type-A) <b>Note: USB must supply a minimum of 900mA</b></span></span></td>
</tr><tr>
<td> <span data-ttu-id="731e1-316">Bluetooth</span><span class="sxs-lookup"><span data-stu-id="731e1-316">Bluetooth</span></span></td><td colspan="2"> <span data-ttu-id="731e1-317">Bluetooth 4.0 (適用於周邊連線)</span><span class="sxs-lookup"><span data-stu-id="731e1-317">Bluetooth 4.0 (for accessory connectivity)</span></span></td>
</tr>
</table>

<span data-ttu-id="731e1-318">如果您是首次使用 MRTK 進行原生開發，建議您依循我們策劃的原生開發旅程：</span><span class="sxs-lookup"><span data-stu-id="731e1-318">If you're new to Native development with MRTK, we recommend following our curated Native development journey:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="731e1-319">開始您的原生旅程</span><span class="sxs-lookup"><span data-stu-id="731e1-319">Start your Native journey</span></span>](../native/directx-development-overview.md)

## <a name="next-development-checkpoint"></a><span data-ttu-id="731e1-320">下一個開發檢查點</span><span class="sxs-lookup"><span data-stu-id="731e1-320">Next Development Checkpoint</span></span>

<span data-ttu-id="731e1-321">依循我們配置的 Native 開發檢查點旅程，您的下一個工作將是設定 HoloLens 2 的開發環境。</span><span class="sxs-lookup"><span data-stu-id="731e1-321">If you're following the Native development checkpoint journey we've laid out, your next task is to configure your development environment for HoloLens 2.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="731e1-322">設定 HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="731e1-322">Setup for HoloLens 2</span></span>](../native/openxr-getting-started.md#getting-started-with-openxr-for-hololens-2)

<span data-ttu-id="731e1-323">您可以隨時回到[原生開發檢查點](../native/directx-development-overview.md#1-getting-started)。</span><span class="sxs-lookup"><span data-stu-id="731e1-323">You can always go back to the [Native development checkpoints](../native/directx-development-overview.md#1-getting-started) at any time.</span></span>
