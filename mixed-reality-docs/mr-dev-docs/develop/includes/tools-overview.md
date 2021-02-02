---
ms.openlocfilehash: c205e3b812eeb7a85bfe361d4fd83f9aec7b7999
ms.sourcegitcommit: cef969ffd22dc1e5a1e9c3c32fbf0646206519a1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/01/2021
ms.locfileid: "99244917"
---
# <a name="unity"></a>[<span data-ttu-id="86e02-101">Unity</span><span class="sxs-lookup"><span data-stu-id="86e02-101">Unity</span></span>](#tab/unity)

![Unity 標誌橫幅](../images/unity_logo_banner.png)<br>

### <a name="1-download-the-latest-version"></a><span data-ttu-id="86e02-103">1.下載最新版本</span><span class="sxs-lookup"><span data-stu-id="86e02-103">1. Download the latest version</span></span>

<span data-ttu-id="86e02-104">建議 [Unity LTS (長期支援)](https://unity3d.com/unity/qa/lts-releases) 資料流作為用來啟動新專案的最佳版本，並更新為其最新修訂版本，以挑選最新穩定的修正程式。</span><span class="sxs-lookup"><span data-stu-id="86e02-104">We recommend the [Unity LTS (Long Term Support)](https://unity3d.com/unity/qa/lts-releases) stream as the best version to use when starting new projects, updating to its latest revision to pick up the latest stable fixes.</span></span>
* <span data-ttu-id="86e02-105">目前的建議是使用 **[Unity 2019.4 LTS](https://unity3d.com/unity/qa/lts-releases?version=2019.4)**，這是下列 MRTK v2 所需的 LTS 組建。</span><span class="sxs-lookup"><span data-stu-id="86e02-105">The current recommendation is to use **[Unity 2019.4 LTS](https://unity3d.com/unity/qa/lts-releases?version=2019.4)**, which is the LTS build required for MRTK v2 below.</span></span>
* <span data-ttu-id="86e02-106">如果您基於特定理由而需要使用不同的 Unity 版本，Unity 支援不同版本的並存安裝。</span><span class="sxs-lookup"><span data-stu-id="86e02-106">If you need to use a different version of Unity for specific reasons, Unity supports side-by-side installs of different versions.</span></span>

### <a name="2-install-the-mixed-reality-feature-tool"></a><span data-ttu-id="86e02-107">2. 安裝 Mixed Reality 功能工具</span><span class="sxs-lookup"><span data-stu-id="86e02-107">2. Install the Mixed Reality Feature Tool</span></span>

<span data-ttu-id="86e02-108">「 [混合現實」功能工具](../unity/welcome-to-mr-feature-tool.md) 是一種新的方法，讓開發人員可以探索並將混合現實功能套件新增至 Unity 專案。</span><span class="sxs-lookup"><span data-stu-id="86e02-108">The [Mixed Reality Feature Tool](../unity/welcome-to-mr-feature-tool.md) is a new way for developers to discover and add Mixed Reality feature packages into Unity projects.</span></span> 

<span data-ttu-id="86e02-109">您可以依名稱或類別搜尋套件、查看其相依性，甚至在匯入之前查看專案資訊清單檔的建議變更。</span><span class="sxs-lookup"><span data-stu-id="86e02-109">You can search packages by name or category, see their dependencies, and even view proposed changes to your projects manifest file before importing.</span></span> <span data-ttu-id="86e02-110">驗證您想要的封裝之後，混合現實功能工具會將這些套件下載到您選擇的專案。</span><span class="sxs-lookup"><span data-stu-id="86e02-110">Once you've validated the packages you want, the Mixed Reality Feature tool will download them into the project of your choice.</span></span>

#### <a name="importing-the-mixed-reality-toolkit"></a><span data-ttu-id="86e02-111">匯入混合實境工具組</span><span class="sxs-lookup"><span data-stu-id="86e02-111">Importing the Mixed Reality Toolkit</span></span>

![MRTK](../../design/images/MRTK_UX_Hero.png)

<span data-ttu-id="86e02-113">[混合實境工具組](../unity/mrtk-getting-started.md) (MRTK) 是混合實境應用程式的開放原始碼跨平台開發套件。</span><span class="sxs-lookup"><span data-stu-id="86e02-113">[Mixed Reality Toolkit](../unity/mrtk-getting-started.md) (MRTK) is an open-source, cross-platform development kit for mixed reality applications.</span></span> 

* <span data-ttu-id="86e02-114">遵循 [安裝和使用方式指示](../unity/welcome-to-mr-feature-tool.md#system-requirements) ，並選取 **混合現實工具組基礎** 套件，以安裝混合現實工具組套件。</span><span class="sxs-lookup"><span data-stu-id="86e02-114">Install the Mixed Reality Toolkit package by following the [installation and usage instructions](../unity/welcome-to-mr-feature-tool.md#system-requirements) and selecting the **Mixed Reality Toolkit Foundation** package.</span></span>

<span data-ttu-id="86e02-115">建議您在策劃 [HoloLens](../unity/unity-development-overview.md#1-getting-started) 或 [VR](../unity/unity-development-wmr-overview.md#1-getting-started) 開發旅程中完成「開始使用」一節。</span><span class="sxs-lookup"><span data-stu-id="86e02-115">We recommend completing the getting started section in our curated [HoloLens](../unity/unity-development-overview.md#1-getting-started) or [VR](../unity/unity-development-wmr-overview.md#1-getting-started) development journeys.</span></span> <span data-ttu-id="86e02-116">依循適用於 HoloLens 的 Unity 開發旅程，接下來請完成下列其餘的設定步驟，並繼續進行 [HoloLens 2 開始使用教學課程](../unity/tutorials/mr-learning-base-01.md)。</span><span class="sxs-lookup"><span data-stu-id="86e02-116">If you're already following the Unity development for HoloLens journey, finish up the rest of the setup steps listed below and continue on to the [HoloLens 2 Getting Started tutorials](../unity/tutorials/mr-learning-base-01.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="86e02-117">請注意，安裝指示的目標是 MRTK 和 Unity 版本的最新穩定組合（ **MRTK 2.5.1** 和 **unity 2019.4 LTS**）。</span><span class="sxs-lookup"><span data-stu-id="86e02-117">Note that installation instructions are targeted for the latest stable combination of MRTK and Unity releases, which are **MRTK 2.5.1** and **Unity 2019.4 LTS**.</span></span>

> [!NOTE]
> <span data-ttu-id="86e02-118">如果您不想要使用適用于 Unity 的 MRTK，您必須 [自行編寫所有互動和行為的腳本](../unity/configure-unity-project.md)。</span><span class="sxs-lookup"><span data-stu-id="86e02-118">If you don't want to use MRTK for Unity, you'll need to [script all interactions and behaviors yourself](../unity/configure-unity-project.md).</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="86e02-119"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">![Unity 橫幅](../images/MRTK-Unity-Banner.png)</span><span class="sxs-lookup"><span data-stu-id="86e02-119"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">![Unity banner](../images/MRTK-Unity-Banner.png)</span></span><br><span data-ttu-id="86e02-120">**混合實境工具組-Unity (GitHub)** </a></span><span class="sxs-lookup"><span data-stu-id="86e02-120">**Mixed Reality Toolkit-Unity (GitHub)**</a></span></span><br>
    :::column-end:::
:::row-end:::

#### <a name="other-tools-optional"></a><span data-ttu-id="86e02-121">其他工具 [選用]</span><span class="sxs-lookup"><span data-stu-id="86e02-121">Other tools [optional]</span></span>
* <span data-ttu-id="86e02-122"><a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">混合實境配套工具組 (GitHub)</a> - 無法直接在 HoloLens 或沈浸式 (VR) 頭戴裝置上執行的程式碼位元和元件，但是將其搭配使用可打造以 Windows Mixed Reality 為目標的體驗。</span><span class="sxs-lookup"><span data-stu-id="86e02-122"><a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">Mixed Reality Companion Kit (GitHub)</a> - code bits and components that might not run directly on HoloLens or immersive (VR) headsets, but instead pair with them to build experiences targeting Windows Mixed Reality.</span></span>
* <span data-ttu-id="86e02-123"><a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">混合的現實工具組 - 通用 (GitHub)</a> - 共用指令碼和元件的集合。</span><span class="sxs-lookup"><span data-stu-id="86e02-123"><a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">Mixed Reality Toolkit - Common (GitHub)</a> - a collection of shared scripts and components.</span></span>

### <a name="3-set-up-your-pc-for-mixed-reality-development"></a><span data-ttu-id="86e02-124">3.設定您的電腦以便進行混合實境開發</span><span class="sxs-lookup"><span data-stu-id="86e02-124">3. Set up your PC for Mixed Reality development</span></span>

<span data-ttu-id="86e02-125">Windows 10 SDK 最適合用於 Windows 10 作業系統。</span><span class="sxs-lookup"><span data-stu-id="86e02-125">The Windows 10 SDK works best on the Windows 10 operating system.</span></span> <span data-ttu-id="86e02-126">Windows 8.1、Windows 8、Windows 7、Windows Server 2012、Windows Server 2008 R2 也支援此 SDK。</span><span class="sxs-lookup"><span data-stu-id="86e02-126">This SDK is also supported on Windows 8.1, Windows 8, Windows 7, Windows Server 2012, Windows Server 2008 R2.</span></span> <span data-ttu-id="86e02-127">請注意，舊版作業系統不支援所有工具。</span><span class="sxs-lookup"><span data-stu-id="86e02-127">Note that not all tools are supported on older operating systems.</span></span>

> [!NOTE]
> <span data-ttu-id="86e02-128">您可以針對 HoloLens、VR 沉浸式頭戴裝置或兩者開發及部署應用程式。</span><span class="sxs-lookup"><span data-stu-id="86e02-128">You can develop and deploy your apps for HoloLens, VR immersive headsets, or both.</span></span> <span data-ttu-id="86e02-129">視您的需求而定，請確定您符合下列需求。</span><span class="sxs-lookup"><span data-stu-id="86e02-129">Make sure you fulfill the requirements below depending on your needs.</span></span>

#### <a name="for-hololens-development"></a><span data-ttu-id="86e02-130">對於 HoloLens 開發</span><span class="sxs-lookup"><span data-stu-id="86e02-130">For HoloLens development</span></span>

<span data-ttu-id="86e02-131">設定您的開發電腦以便進行 HoloLens 開發時，請確定其同時符合 <a href="https://unity3d.com/unity/system-requirements" target="_blank">Unity</a> 和 <a href="//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a> 的系統需求。</span><span class="sxs-lookup"><span data-stu-id="86e02-131">When setting up your development PC for HoloLens development, please make sure it meets the system requirements for both <a href="https://unity3d.com/unity/system-requirements" target="_blank">Unity</a> and <a href="//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a>.</span></span> <span data-ttu-id="86e02-132">如果您想要在 HoloLens 裝置上執行您的應用程式，則必須遵循 [Windows 裝置入口網站安裝指示](../platform-capabilities-and-apis/using-the-windows-device-portal.md#setting-up-hololens-to-use-windows-device-portal)。</span><span class="sxs-lookup"><span data-stu-id="86e02-132">If you want to run your app on a HoloLens device, you need to follow the [Windows Device Portal setup instructions](../platform-capabilities-and-apis/using-the-windows-device-portal.md#setting-up-hololens-to-use-windows-device-portal).</span></span> <span data-ttu-id="86e02-133">如果您打算使用 [HoloLens 模擬器](../platform-capabilities-and-apis/using-the-hololens-emulator.md)，您應確定您的電腦也符合 [HoloLens 模擬器系統需求](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements)。</span><span class="sxs-lookup"><span data-stu-id="86e02-133">If you plan on using the [HoloLens emulator](../platform-capabilities-and-apis/using-the-hololens-emulator.md), you'll want to make sure your PC meets the [HoloLens emulator system requirements](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements) as well.</span></span>

<span data-ttu-id="86e02-134">若要開始使用 HoloLens 模擬器，請參閱[使用 HoloLens 模擬器](../platform-capabilities-and-apis/using-the-hololens-emulator.md)。</span><span class="sxs-lookup"><span data-stu-id="86e02-134">To get started with the HoloLens emulator, see [Using the HoloLens emulator](../platform-capabilities-and-apis/using-the-hololens-emulator.md).</span></span>

<span data-ttu-id="86e02-135">如果您打算針對 HoloLens 與 Windows Mixed Reality 沈浸式 (VR) 頭戴裝置進行開發，請使用下一節中的系統建議和需求。</span><span class="sxs-lookup"><span data-stu-id="86e02-135">If you plan to develop for both HoloLens and Windows Mixed Reality immersive (VR) headsets, use the system recommendations and requirements in the section below.</span></span>

#### <a name="hololens-troubleshooting"></a><span data-ttu-id="86e02-136">HoloLens 疑難排解</span><span class="sxs-lookup"><span data-stu-id="86e02-136">HoloLens troubleshooting</span></span>

##### <a name="setting-developer-mode-is-grayed-out"></a><span data-ttu-id="86e02-137">設定開發人員模式呈現灰色</span><span class="sxs-lookup"><span data-stu-id="86e02-137">Setting Developer Mode is grayed out</span></span>

<span data-ttu-id="86e02-138">如果您在裝置上啟用開發人員模式時遇到問題，您可能不是[裝置擁有者](/hololens/security-adminless-os)。</span><span class="sxs-lookup"><span data-stu-id="86e02-138">If you're running into issues enabling Developer Mode on your device you might not be the [device owner](/hololens/security-adminless-os).</span></span> <span data-ttu-id="86e02-139">在多使用者模式中，第一個使用裝置的人員就是裝置擁有者，任何後續的使用者都不會擁有啟用 [開發人員模式] 或其他組態變更所需的權限。</span><span class="sxs-lookup"><span data-stu-id="86e02-139">In multi-user mode, the person who uses the device first is the device owner - any subsequent users won't have the required permissions to enable Developer Mode or other configuration changes.</span></span> <span data-ttu-id="86e02-140">不過，有一個例外狀況，那就是第一個使用者可能不是 Autopilot 環境中的裝置擁有者，這會在 [HoloLens 安全性文件](/hololens/security-adminless-os#device-owner)詳述。</span><span class="sxs-lookup"><span data-stu-id="86e02-140">However, there is an exception where the first user may not be the device owner in an Autopilot environment, which is detailed in the [HoloLens security documentation](/hololens/security-adminless-os#device-owner).</span></span>

<span data-ttu-id="86e02-141">可能的解決方案包括：</span><span class="sxs-lookup"><span data-stu-id="86e02-141">Possible solutions include:</span></span>

* <span data-ttu-id="86e02-142">在將裝置傳遞給其他使用者或開發人員之前，讓裝置擁有者開啟開發人員模式</span><span class="sxs-lookup"><span data-stu-id="86e02-142">Having the device owner turn Developer Mode on before passing the device to other users or developers</span></span>
* <span data-ttu-id="86e02-143">建議您的 IT/MDM 管理員針對特定裝置或開發人員裝置群組啟用 CSP [Policy ApplicationManagement/AllowDeveloperUnlock](/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock)。</span><span class="sxs-lookup"><span data-stu-id="86e02-143">Suggesting that your IT/MDM Admin enables CSP [Policy ApplicationManagement/AllowDeveloperUnlock](/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock) for the specific device or a developer device group.</span></span> 
    * <span data-ttu-id="86e02-144">此原則可經由[佈建套件](/hololens/hololens-provisioning)或透過 [HoloLens 裝置的 MDM](/hololens/hololens-mdm-configure) 來設定</span><span class="sxs-lookup"><span data-stu-id="86e02-144">This policy can be set by [Provisioning Packages](/hololens/hololens-provisioning) or via [MDM for HoloLens devices](/hololens/hololens-mdm-configure)</span></span>
* <span data-ttu-id="86e02-145">使用 [Advanced Recovery Companion (ARC)](/hololens/hololens-recovery)</span><span class="sxs-lookup"><span data-stu-id="86e02-145">Using the [Advanced Recovery Companion (ARC)](/hololens/hololens-recovery)</span></span>

> [!NOTE]
> <span data-ttu-id="86e02-146">您可以在 **[HoloLens 裝置管理](/hololens/hololens-csp-policy-overview)** 概觀中深入了解裝置管理。</span><span class="sxs-lookup"><span data-stu-id="86e02-146">You can learn more about device management in the **[HoloLens device management](/hololens/hololens-csp-policy-overview)** overview.</span></span>

##### <a name="i-cant-deploy-over-usb"></a><span data-ttu-id="86e02-147">我無法透過 USB 部署</span><span class="sxs-lookup"><span data-stu-id="86e02-147">I can't deploy over USB</span></span>

<span data-ttu-id="86e02-148">如果您無法直接透過 USB 部署應用程式，請確定您符合上述所有的安裝需求，並遵循我們的[逐步教學課程](../unity/tutorials/mr-learning-base-02.md#building-your-application-to-your-hololens-2)。</span><span class="sxs-lookup"><span data-stu-id="86e02-148">If you're not able to deploy an application directly over USB, make sure you've met all the installation requirements listed above and follow our [step-by-step tutorial](../unity/tutorials/mr-learning-base-02.md#building-your-application-to-your-hololens-2).</span></span>

#### <a name="immersive-vr-headset-requirements"></a><span data-ttu-id="86e02-149">沈浸式 (VR) 頭戴式裝置需求</span><span class="sxs-lookup"><span data-stu-id="86e02-149">Immersive (VR) headset requirements</span></span>

>[!NOTE]
><span data-ttu-id="86e02-150">下列指導方針是沈浸式 (VR) 頭戴裝置「開發電腦」目前的最低建議規格，而且會定期更新。</span><span class="sxs-lookup"><span data-stu-id="86e02-150">The following guidelines are the current minimum and recommended specs for your immersive (VR) headset *development PC*, and are updated regularly.</span></span>

>[!WARNING]
><span data-ttu-id="86e02-151">請勿將此指導方針與[最低電腦硬體相容性指導方針](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)混淆，其中概述了沈浸式 (VR) 頭戴裝置應用程式或遊戲應該定向的「取用者電腦規格」。</span><span class="sxs-lookup"><span data-stu-id="86e02-151">Do not confuse this with the [minimum PC hardware compatibility guidelines](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines), which outlines the *consumer PC specs* to which you should target your immersive (VR) headset app or game.</span></span>

<span data-ttu-id="86e02-152">如果沉浸式頭戴裝置開發電腦沒有完整大小的 HDMI 和/或 USB 3.0 連接埠，您需要[配接器](/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs)才能連線頭戴式裝置。</span><span class="sxs-lookup"><span data-stu-id="86e02-152">If your immersive headset development PC does not have full-sized HDMI and/or USB 3.0 ports, you'll need [adapters](/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs) to connect your headset.</span></span>

<span data-ttu-id="86e02-153">目前某些硬體設定有[已知問題](/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)，尤其是具有混合式圖形的筆記型電腦。</span><span class="sxs-lookup"><span data-stu-id="86e02-153">There are currently [known issues](/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality) with some hardware configurations, particularly notebooks that have hybrid graphics.</span></span>

<table>
<tr>
<th></th><th> <span data-ttu-id="86e02-154">最低需求</span><span class="sxs-lookup"><span data-stu-id="86e02-154">Minimum</span></span></th><th> <span data-ttu-id="86e02-155">建議</span><span class="sxs-lookup"><span data-stu-id="86e02-155">Recommended</span></span></th>
</tr><tr>
<td> <span data-ttu-id="86e02-156">處理器</span><span class="sxs-lookup"><span data-stu-id="86e02-156">Processor</span></span></td><td> <span data-ttu-id="86e02-157"><b>筆記型電腦：</b>Intel Mobile Core i5 第 7 代 CPU、採用超執行緒技術的雙核心 <b>傳統型：</b>Intel Desktop i5 第 6 代 CPU、採用超執行緒技術的雙核心<b>或</b> AMD FX4350 4.2Ghz 四核心對等項目</span><span class="sxs-lookup"><span data-stu-id="86e02-157"><b>Notebook:</b> Intel Mobile Core i5 7th generation CPU, Dual-Core with Hyper Threading <b>Desktop:</b> Intel Desktop i5 6th generation CPU, Dual-Core with Hyper Threading <b>OR</b> AMD FX4350 4.2Ghz Quad-Core equivalent</span></span></td><td> <span data-ttu-id="86e02-158"><b>傳統型：</b>Intel Desktop i7 第 6 代 (6 核心) <b>或</b> AMD Ryzen 5 1600 (6 核心，12 個執行緒)</span><span class="sxs-lookup"><span data-stu-id="86e02-158"><b>Desktop:</b> Intel Desktop i7 6th generation (6 Core) <b>OR</b> AMD Ryzen 5 1600 (6 Core, 12 threads)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="86e02-159">GPU</span><span class="sxs-lookup"><span data-stu-id="86e02-159">GPU</span></span></td><td> <span data-ttu-id="86e02-160"><b>筆記型電腦：</b>NVIDIA GTX 965M、AMD RX 460M (2GB) 對等項目或更高的 DX12 支援 GPU <b>傳統型：</b>NVIDIA GTX 960/1050、AMD Radeon RX 460 (2GB) 對等項目或更高的 DX12 支援 GPU</span><span class="sxs-lookup"><span data-stu-id="86e02-160"><b>Notebook:</b> NVIDIA GTX 965M, AMD RX 460M (2GB) equivalent or greater DX12 capable GPU <b>Desktop:</b> NVIDIA GTX 960/1050, AMD Radeon RX 460 (2GB) equivalent or greater DX12 capable GPU</span></span></td><td><span data-ttu-id="86e02-161"><b>傳統型：</b>NVIDIA GTX 980/1060、AMD Radeon RX 480 (2GB) 對等項目或更高的 DX12 支援 GPU</span><span class="sxs-lookup"><span data-stu-id="86e02-161"><b>Desktop:</b> NVIDIA GTX 980/1060, AMD Radeon RX 480 (2GB) equivalent or greater DX12 capable GPU</span></span></td>
</tr><tr>
<td> <span data-ttu-id="86e02-162">GPU 驅動程式 WDDM 版本</span><span class="sxs-lookup"><span data-stu-id="86e02-162">GPU driver WDDM version</span></span></td><td colspan="2"> <span data-ttu-id="86e02-163">WDDM 2.2 驅動程式</span><span class="sxs-lookup"><span data-stu-id="86e02-163">WDDM 2.2 driver</span></span></td>
</tr><tr>
<td> <span data-ttu-id="86e02-164">散熱設計功率</span><span class="sxs-lookup"><span data-stu-id="86e02-164">Thermal Design Power</span></span></td><td colspan="2"> <span data-ttu-id="86e02-165">15W 或更大</span><span class="sxs-lookup"><span data-stu-id="86e02-165">15W or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="86e02-166">圖形顯示連接埠</span><span class="sxs-lookup"><span data-stu-id="86e02-166">Graphics display ports</span></span></td><td colspan="2"> <span data-ttu-id="86e02-167">適用於頭戴式裝置的 1x 可用圖形顯示連接埠 (適用於 60Hz 頭戴式裝置的 HDMI 1.4 或 DisplayPort 1.2，適用於 90Hz 頭戴式裝置的 HDMI 2.0 或 DisplayPort 1.2)</span><span class="sxs-lookup"><span data-stu-id="86e02-167">1x available graphics display port for&#160;headset (HDMI 1.4 or DisplayPort 1.2 for 60Hz headsets, HDMI 2.0 or DisplayPort 1.2 for 90Hz headsets)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="86e02-168">顯示器解析度</span><span class="sxs-lookup"><span data-stu-id="86e02-168">Display resolution</span></span></td><td colspan="2"> <span data-ttu-id="86e02-169">解決方法：SVGA (800 x 600) 或更大的位元深度：每像素 32 位元的色彩</span><span class="sxs-lookup"><span data-stu-id="86e02-169">Resolution: SVGA (800x600) or greater Bit depth: 32 bits of color per pixel</span></span></td>
</tr><tr>
<td> <span data-ttu-id="86e02-170">Memory</span><span class="sxs-lookup"><span data-stu-id="86e02-170">Memory</span></span></td><td> <span data-ttu-id="86e02-171">8&#160;GB RAM 或更大</span><span class="sxs-lookup"><span data-stu-id="86e02-171">8&#160;GB of RAM or greater</span></span></td><td> <span data-ttu-id="86e02-172">16 GB RAM 或更大</span><span class="sxs-lookup"><span data-stu-id="86e02-172">16 GB of RAM or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="86e02-173">存放裝置</span><span class="sxs-lookup"><span data-stu-id="86e02-173">Storage</span></span></td><td colspan="2"> <span data-ttu-id="86e02-174">&gt;10 GB 額外可用空間</span><span class="sxs-lookup"><span data-stu-id="86e02-174">&gt;10 GB additional free space</span></span></td>
</tr><tr>
<td> <span data-ttu-id="86e02-175">USB 連接埠</span><span class="sxs-lookup"><span data-stu-id="86e02-175">USB Ports</span></span></td><td colspan="2"> <span data-ttu-id="86e02-176">適用於頭戴式裝置的 1x 可用 USB 連接埠 (USB 3.0 Type-A) <b>注意：USB 必須提供至少 900mA</b></span><span class="sxs-lookup"><span data-stu-id="86e02-176">1x available USB port for headset (USB 3.0 Type-A) <b>Note: USB must supply a minimum of 900mA</b></span></span></td>
</tr><tr>
<td> <span data-ttu-id="86e02-177">Bluetooth</span><span class="sxs-lookup"><span data-stu-id="86e02-177">Bluetooth</span></span></td><td colspan="2"> <span data-ttu-id="86e02-178">Bluetooth 4.0 (適用於周邊連線)</span><span class="sxs-lookup"><span data-stu-id="86e02-178">Bluetooth 4.0 (for accessory connectivity)</span></span></td>
</tr>
</table>

<span data-ttu-id="86e02-179">如果您是首次使用 Unity 進行 MRTK 開發，建議您依循我們策劃的 Unity 開發旅程：</span><span class="sxs-lookup"><span data-stu-id="86e02-179">If you're new to MRTK development with Unity, we recommend following our curated Unity development journey:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="86e02-180">開始您適用於 HoloLens 的 Unity 開發旅程</span><span class="sxs-lookup"><span data-stu-id="86e02-180">Start your Unity for HoloLens journey</span></span>](../unity/unity-development-overview.md)

> [!div class="nextstepaction"]
> [<span data-ttu-id="86e02-181">開始您適用於 VR 的 Unity 開發旅程</span><span class="sxs-lookup"><span data-stu-id="86e02-181">Start your Unity for VR journey</span></span>](../unity/unity-development-wmr-overview.md)

## <a name="next-development-checkpoint"></a><span data-ttu-id="86e02-182">下一個開發檢查點</span><span class="sxs-lookup"><span data-stu-id="86e02-182">Next Development Checkpoint</span></span>

<span data-ttu-id="86e02-183">依循我們所配置適用於 HoloLens 的 Unity 開發檢查點旅程，您的下一個工作將是進行 HoloLens 2 教學課程系列。</span><span class="sxs-lookup"><span data-stu-id="86e02-183">If you're following the Unity for HoloLens development checkpoint journey we've laid out, your next task is to work through our HoloLens 2 tutorial series.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="86e02-184">HoloLens 2 教學課程系列</span><span class="sxs-lookup"><span data-stu-id="86e02-184">HoloLens 2 tutorial series</span></span>](../unity/tutorials/mr-learning-base-01.md)

<span data-ttu-id="86e02-185">如果您要依循適用於 VR 的 Unity 旅程，下一個工作是設定您的專案。</span><span class="sxs-lookup"><span data-stu-id="86e02-185">If you're following the Unity for VR journey, your next task is to setup your project.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="86e02-186">針對 WMR 設定您的專案</span><span class="sxs-lookup"><span data-stu-id="86e02-186">Configuring your project for WMR</span></span>](../unity/configure-unity-project.md)

<span data-ttu-id="86e02-187">您可以隨時回到適用於 [HoloLens](../unity/unity-development-overview.md#1-getting-started) 和 [VR](../unity/unity-development-wmr-overview.md#1-getting-started)的 Unity 開發檢查點。</span><span class="sxs-lookup"><span data-stu-id="86e02-187">You can always go back to the Unity development checkpoints for [HoloLens](../unity/unity-development-overview.md#1-getting-started) and [VR](../unity/unity-development-wmr-overview.md#1-getting-started) at any time.</span></span>

# <a name="unreal"></a>[<span data-ttu-id="86e02-188">Unreal</span><span class="sxs-lookup"><span data-stu-id="86e02-188">Unreal</span></span>](#tab/unreal)

![Unreal](../images/unreal_logo_banner.png)

### <a name="1-download-the-latest-version"></a><span data-ttu-id="86e02-190">1.下載最新版本</span><span class="sxs-lookup"><span data-stu-id="86e02-190">1. Download the latest version</span></span>

<span data-ttu-id="86e02-191">建議您安裝 [Unreal Engine 4.25 版](https://docs.unrealengine.com//GettingStarted/Installation/index.html)或更新版本，以充分利用內建的 HoloLens 支援。</span><span class="sxs-lookup"><span data-stu-id="86e02-191">We recommend installing [Unreal Engine version 4.25](https://docs.unrealengine.com//GettingStarted/Installation/index.html) or later to take full advantage of built-in HoloLens support.</span></span>

### <a name="2-import-mixed-reality-toolkit-mrtk"></a><span data-ttu-id="86e02-192">2.匯入混合實境工具組 (MRTK)</span><span class="sxs-lookup"><span data-stu-id="86e02-192">2. Import Mixed Reality Toolkit (MRTK)</span></span>
![MRTK](../../design/images/MRTK_UX_Hero.png)

<span data-ttu-id="86e02-194">混合實境工具組 (MRTK) 是混合實境應用程式的開放原始碼跨平台開發套件。</span><span class="sxs-lookup"><span data-stu-id="86e02-194">Mixed Reality Toolkit (MRTK) is an open-source, cross-platform development kit for mixed reality applications.</span></span> <span data-ttu-id="86e02-195">MRTK 提供跨平台輸入系統、基礎元件，以及空間互動的常見基本要素。</span><span class="sxs-lookup"><span data-stu-id="86e02-195">MRTK provides a cross-platform input system, foundational components, and common building blocks for spatial interactions.</span></span> <span data-ttu-id="86e02-196">該工具組主要用於加速開發以 Microsoft HoloLens、Windows Mixed Reality 沈浸式 (VR) 頭戴裝置和 OpenVR 平台為目標的應用程式。</span><span class="sxs-lookup"><span data-stu-id="86e02-196">The toolkit is intended to accelerate the development of applications targeting Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets, and the OpenVR platform.</span></span>

<span data-ttu-id="86e02-197">進行安裝時，建議您完成我們策劃的 [Unreal 開發旅程圖](../unreal/unreal-development-overview.md)的[開始使用一節](../unreal/unreal-development-overview.md#1-getting-started)。</span><span class="sxs-lookup"><span data-stu-id="86e02-197">For installation, we recommend completing the [Getting Started section](../unreal/unreal-development-overview.md#1-getting-started) of our curated [Unreal development journey](../unreal/unreal-development-overview.md).</span></span> <span data-ttu-id="86e02-198">依循 Unreal 開發旅程，接下來請完成下列其餘的設定步驟，並繼續進行 [HoloLens 2 開始使用教學課程](../unreal/tutorials/unreal-uxt-ch1.md)。</span><span class="sxs-lookup"><span data-stu-id="86e02-198">If you're already following the Unreal development journey, finish up the rest of the setup steps listed below and continue on to the [HoloLens 2 Getting Started tutorials](../unreal/tutorials/unreal-uxt-ch1.md).</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="86e02-199"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unreal" target="_blank">![Unity 標誌影像](../images/MRTK-Unreal-Banner.png)</span><span class="sxs-lookup"><span data-stu-id="86e02-199"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unreal" target="_blank">![Unity logo image](../images/MRTK-Unreal-Banner.png)</span></span><br><span data-ttu-id="86e02-200">**混合實境工具組-Unreal (GitHub)** </a></span><span class="sxs-lookup"><span data-stu-id="86e02-200">**Mixed Reality Toolkit-Unreal (GitHub)**</a></span></span><br>
    :::column-end:::
:::row-end:::

> [!NOTE]
> <span data-ttu-id="86e02-201">如果您不想使用適用於 Unreal 的 MRTK，則必須自行撰寫所有互動和行為的指令碼。</span><span class="sxs-lookup"><span data-stu-id="86e02-201">If you don't want to use MRTK for Unreal, you'll need to script all interactions and behaviors yourself.</span></span>

#### <a name="other-tools-optional"></a><span data-ttu-id="86e02-202">其他工具 [選用]</span><span class="sxs-lookup"><span data-stu-id="86e02-202">Other tools [optional]</span></span>
* <span data-ttu-id="86e02-203"><a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">混合實境配套工具組 (GitHub)</a> - 無法直接在 HoloLens 或沈浸式 (VR) 頭戴裝置上執行的程式碼位元和元件，但是將其搭配使用可打造以 Windows Mixed Reality 為目標的體驗。</span><span class="sxs-lookup"><span data-stu-id="86e02-203"><a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">Mixed Reality Companion Kit (GitHub)</a> - code bits and components that might not run directly on HoloLens or immersive (VR) headsets, but instead pair with them to build experiences targeting Windows Mixed Reality.</span></span>
* <span data-ttu-id="86e02-204"><a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">混合的現實工具組 - 通用 (GitHub)</a> - 共用指令碼和元件的集合。</span><span class="sxs-lookup"><span data-stu-id="86e02-204"><a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">Mixed Reality Toolkit - Co mmon (GitHub)</a> - a collection of shared scripts and components.</span></span>

### <a name="3-set-up-your-pc-for-mixed-reality-development"></a><span data-ttu-id="86e02-205">3.設定您的電腦以便進行混合實境開發</span><span class="sxs-lookup"><span data-stu-id="86e02-205">3. Set up your PC for mixed reality development</span></span>

<span data-ttu-id="86e02-206">Windows 10 SDK 最適合用於 Windows 10 作業系統。</span><span class="sxs-lookup"><span data-stu-id="86e02-206">The Windows 10 SDK works best on the Windows 10 operating system.</span></span> <span data-ttu-id="86e02-207">Windows 8.1、Windows 8、Windows 7、Windows Server 2012、Windows Server 2008 R2 也支援此 SDK。</span><span class="sxs-lookup"><span data-stu-id="86e02-207">This SDK is also supported on Windows 8.1, Windows 8, Windows 7, Windows Server 2012, Windows Server 2008 R2.</span></span> <span data-ttu-id="86e02-208">請注意，舊版作業系統不支援所有工具。</span><span class="sxs-lookup"><span data-stu-id="86e02-208">Note that not all tools are supported on older operating systems.</span></span>

> [!NOTE]
> <span data-ttu-id="86e02-209">您可以針對 HoloLens、VR 沉浸式頭戴裝置或兩者開發及部署應用程式。</span><span class="sxs-lookup"><span data-stu-id="86e02-209">You can develop and deploy your apps for HoloLens, VR immersive headsets, or both.</span></span> <span data-ttu-id="86e02-210">視您的需求而定，請確定您符合下列需求。</span><span class="sxs-lookup"><span data-stu-id="86e02-210">Make sure you fulfill the requirements below depending on your needs.</span></span>

#### <a name="for-hololens-development"></a><span data-ttu-id="86e02-211">對於 HoloLens 開發</span><span class="sxs-lookup"><span data-stu-id="86e02-211">For HoloLens development</span></span>

<span data-ttu-id="86e02-212">設定您的開發電腦以便進行 HoloLens 開發時，請確定您符合 [Unity](https://docs.unrealengine.com/GettingStarted/RecommendedSpecifications/index.html) 和 <a href="//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a> 的系統需求。</span><span class="sxs-lookup"><span data-stu-id="86e02-212">When setting up your development PC for HoloLens development, please make sure you meet the system requirements for [Unreal](https://docs.unrealengine.com/GettingStarted/RecommendedSpecifications/index.html) and and <a href="//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a>.</span></span> <span data-ttu-id="86e02-213">如果您想要在 HoloLens 裝置上執行您的應用程式，則必須遵循 [Windows 裝置入口網站安裝指示](../platform-capabilities-and-apis/using-the-windows-device-portal.md#setting-up-hololens-to-use-windows-device-portal)。</span><span class="sxs-lookup"><span data-stu-id="86e02-213">If you want to run your app on a HoloLens device, you need to follow the [Windows Device Portal setup instructions](../platform-capabilities-and-apis/using-the-windows-device-portal.md#setting-up-hololens-to-use-windows-device-portal).</span></span> <span data-ttu-id="86e02-214">如果您打算使用 [HoloLens 模擬器](../platform-capabilities-and-apis/using-the-hololens-emulator.md)，您應確定您的電腦也符合 [HoloLens 模擬器系統需求](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements)。</span><span class="sxs-lookup"><span data-stu-id="86e02-214">If you plan on using the [HoloLens emulator](../platform-capabilities-and-apis/using-the-hololens-emulator.md), you'll want to make sure your PC meets the [HoloLens emulator system requirements](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements) as well.</span></span>

<span data-ttu-id="86e02-215">如果您打算針對 HoloLens 與 Windows Mixed Reality 沈浸式 (VR) 頭戴裝置進行開發，請使用下一節中的系統建議和需求。</span><span class="sxs-lookup"><span data-stu-id="86e02-215">If you plan to develop for both HoloLens and Windows Mixed Reality immersive (VR) headsets, use the system recommendations and requirements in the section below.</span></span>

#### <a name="hololens-troubleshooting"></a><span data-ttu-id="86e02-216">HoloLens 疑難排解</span><span class="sxs-lookup"><span data-stu-id="86e02-216">HoloLens troubleshooting</span></span>

##### <a name="setting-developer-mode-is-grayed-out"></a><span data-ttu-id="86e02-217">設定開發人員模式呈現灰色</span><span class="sxs-lookup"><span data-stu-id="86e02-217">Setting Developer Mode is grayed out</span></span>

<span data-ttu-id="86e02-218">如果您在裝置上啟用開發人員模式時遇到問題，您可能不是[裝置擁有者](/hololens/security-adminless-os)。</span><span class="sxs-lookup"><span data-stu-id="86e02-218">If you're running into issues enabling Developer Mode on your device you might not be the [device owner](/hololens/security-adminless-os).</span></span> <span data-ttu-id="86e02-219">在多使用者模式中，第一個使用裝置的人員就是裝置擁有者，任何後續的使用者都不會擁有啟用 [開發人員模式] 或其他組態變更所需的權限。</span><span class="sxs-lookup"><span data-stu-id="86e02-219">In multi-user mode, the person who uses the device first is the device owner - any subsequent users won't have the required permissions to enable Developer Mode or other configuration changes.</span></span> <span data-ttu-id="86e02-220">不過，有一個例外狀況，那就是第一個使用者可能不是 Autopilot 環境中的裝置擁有者，這會在 [HoloLens 安全性文件](/hololens/security-adminless-os#device-owner)詳述。</span><span class="sxs-lookup"><span data-stu-id="86e02-220">However, there is an exception where the first user may not be the device owner in an Autopilot environment, which is detailed in the [HoloLens security documentation](/hololens/security-adminless-os#device-owner).</span></span>

<span data-ttu-id="86e02-221">可能的解決方案包括：</span><span class="sxs-lookup"><span data-stu-id="86e02-221">Possible solutions include:</span></span>

* <span data-ttu-id="86e02-222">在將裝置傳遞給其他使用者或開發人員之前，讓裝置擁有者開啟開發人員模式</span><span class="sxs-lookup"><span data-stu-id="86e02-222">Having the device owner turn Developer Mode on before passing the device to other users or developers</span></span>
* <span data-ttu-id="86e02-223">建議您的 IT/MDM 管理員針對特定裝置或開發人員裝置群組啟用 CSP [Policy ApplicationManagement/AllowDeveloperUnlock](/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock)。</span><span class="sxs-lookup"><span data-stu-id="86e02-223">Suggesting that your IT/MDM Admin enables CSP [Policy ApplicationManagement/AllowDeveloperUnlock](/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock) for the specific device or a developer device group.</span></span> 
    * <span data-ttu-id="86e02-224">此原則可經由[佈建套件](/hololens/hololens-provisioning)或透過 [HoloLens 裝置的 MDM](/hololens/hololens-mdm-configure) 來設定</span><span class="sxs-lookup"><span data-stu-id="86e02-224">This policy can be set by [Provisioning Packages](/hololens/hololens-provisioning) or via [MDM for HoloLens devices](/hololens/hololens-mdm-configure)</span></span>
* <span data-ttu-id="86e02-225">使用 [Advanced Recovery Companion (ARC)](/hololens/hololens-recovery)</span><span class="sxs-lookup"><span data-stu-id="86e02-225">Using the [Advanced Recovery Companion (ARC)](/hololens/hololens-recovery)</span></span>

> [!NOTE]
> <span data-ttu-id="86e02-226">您可以在 **[HoloLens 裝置管理](/hololens/hololens-csp-policy-overview)** 概觀中深入了解裝置管理。</span><span class="sxs-lookup"><span data-stu-id="86e02-226">You can learn more about device management in the **[HoloLens device management](/hololens/hololens-csp-policy-overview)** overview.</span></span>

##### <a name="i-cant-deploy-over-usb"></a><span data-ttu-id="86e02-227">我無法透過 USB 部署</span><span class="sxs-lookup"><span data-stu-id="86e02-227">I can't deploy over USB</span></span>

<span data-ttu-id="86e02-228">如果您無法直接透過 USB 部署應用程式，請確定您符合上述所有的安裝需求，並遵循我們的[逐步教學課程](../unreal/tutorials/unreal-uxt-ch6.md)。</span><span class="sxs-lookup"><span data-stu-id="86e02-228">If you're not able to deploy an application directly over USB, make sure you've met all the installation requirements listed above and follow our [step-by-step tutorial](../unreal/tutorials/unreal-uxt-ch6.md).</span></span>

#### <a name="immersive-vr-headset-requirements"></a><span data-ttu-id="86e02-229">沈浸式 (VR) 頭戴式裝置需求</span><span class="sxs-lookup"><span data-stu-id="86e02-229">Immersive (VR) headset requirements</span></span>

>[!NOTE]
><span data-ttu-id="86e02-230">下列指導方針是沈浸式 (VR) 頭戴裝置「開發電腦」目前的最低建議規格，而且會定期更新。</span><span class="sxs-lookup"><span data-stu-id="86e02-230">The following guidelines are the current minimum and recommended specs for your immersive (VR) headset *development PC*, and are updated regularly.</span></span>

>[!WARNING]
><span data-ttu-id="86e02-231">請勿將此指導方針與[最低電腦硬體相容性指導方針](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)混淆，其中概述了沈浸式 (VR) 頭戴裝置應用程式或遊戲應該定向的「取用者電腦規格」。</span><span class="sxs-lookup"><span data-stu-id="86e02-231">Do not confuse this with the [minimum PC hardware compatibility guidelines](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines), which outlines the *consumer PC specs* to which you should target your immersive (VR) headset app or game.</span></span>

<span data-ttu-id="86e02-232">如果沉浸式頭戴裝置開發電腦沒有完整大小的 HDMI 和/或 USB 3.0 連接埠，您需要[配接器](/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs)才能連線頭戴式裝置。</span><span class="sxs-lookup"><span data-stu-id="86e02-232">If your immersive headset development PC does not have full-sized HDMI and/or USB 3.0 ports, you'll need [adapters](/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs) to connect your headset.</span></span>

<span data-ttu-id="86e02-233">目前某些硬體設定有[已知問題](/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)，尤其是具有混合式圖形的筆記型電腦。</span><span class="sxs-lookup"><span data-stu-id="86e02-233">There are currently [known issues](/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality) with some hardware configurations, particularly notebooks that have hybrid graphics.</span></span>

<table>
<tr>
<th></th><th> <span data-ttu-id="86e02-234">最低需求</span><span class="sxs-lookup"><span data-stu-id="86e02-234">Minimum</span></span></th><th> <span data-ttu-id="86e02-235">建議</span><span class="sxs-lookup"><span data-stu-id="86e02-235">Recommended</span></span></th>
</tr><tr>
<td> <span data-ttu-id="86e02-236">處理器</span><span class="sxs-lookup"><span data-stu-id="86e02-236">Processor</span></span></td><td> <span data-ttu-id="86e02-237"><b>筆記型電腦：</b>Intel Mobile Core i5 第 7 代 CPU、採用超執行緒技術的雙核心 <b>傳統型：</b>Intel Desktop i5 第 6 代 CPU、採用超執行緒技術的雙核心<b>或</b> AMD FX4350 4.2Ghz 四核心對等項目</span><span class="sxs-lookup"><span data-stu-id="86e02-237"><b>Notebook:</b> Intel Mobile Core i5 7th generation CPU, Dual-Core with Hyper Threading <b>Desktop:</b> Intel Desktop i5 6th generation CPU, Dual-Core with Hyper Threading <b>OR</b> AMD FX4350 4.2Ghz Quad-Core equivalent</span></span></td><td> <span data-ttu-id="86e02-238"><b>傳統型：</b>Intel Desktop i7 第 6 代 (6 核心) <b>或</b> AMD Ryzen 5 1600 (6 核心，12 個執行緒)</span><span class="sxs-lookup"><span data-stu-id="86e02-238"><b>Desktop:</b> Intel Desktop i7 6th generation (6 Core) <b>OR</b> AMD Ryzen 5 1600 (6 Core, 12 threads)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="86e02-239">GPU</span><span class="sxs-lookup"><span data-stu-id="86e02-239">GPU</span></span></td><td> <span data-ttu-id="86e02-240"><b>筆記型電腦：</b>NVIDIA GTX 965M、AMD RX 460M (2GB) 對等項目或更高的 DX12 支援 GPU <b>傳統型：</b>NVIDIA GTX 960/1050、AMD Radeon RX 460 (2GB) 對等項目或更高的 DX12 支援 GPU</span><span class="sxs-lookup"><span data-stu-id="86e02-240"><b>Notebook:</b> NVIDIA GTX 965M, AMD RX 460M (2GB) equivalent or greater DX12 capable GPU <b>Desktop:</b> NVIDIA GTX 960/1050, AMD Radeon RX 460 (2GB) equivalent or greater DX12 capable GPU</span></span></td><td><span data-ttu-id="86e02-241"><b>傳統型：</b>NVIDIA GTX 980/1060、AMD Radeon RX 480 (2GB) 對等項目或更高的 DX12 支援 GPU</span><span class="sxs-lookup"><span data-stu-id="86e02-241"><b>Desktop:</b> NVIDIA GTX 980/1060, AMD Radeon RX 480 (2GB) equivalent or greater DX12 capable GPU</span></span></td>
</tr><tr>
<td> <span data-ttu-id="86e02-242">GPU 驅動程式 WDDM 版本</span><span class="sxs-lookup"><span data-stu-id="86e02-242">GPU driver WDDM version</span></span></td><td colspan="2"> <span data-ttu-id="86e02-243">WDDM 2.2 驅動程式</span><span class="sxs-lookup"><span data-stu-id="86e02-243">WDDM 2.2 driver</span></span></td>
</tr><tr>
<td> <span data-ttu-id="86e02-244">散熱設計功率</span><span class="sxs-lookup"><span data-stu-id="86e02-244">Thermal Design Power</span></span></td><td colspan="2"> <span data-ttu-id="86e02-245">15W 或更大</span><span class="sxs-lookup"><span data-stu-id="86e02-245">15W or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="86e02-246">圖形顯示連接埠</span><span class="sxs-lookup"><span data-stu-id="86e02-246">Graphics display ports</span></span></td><td colspan="2"> <span data-ttu-id="86e02-247">適用於頭戴式裝置的 1x 可用圖形顯示連接埠 (適用於 60Hz 頭戴式裝置的 HDMI 1.4 或 DisplayPort 1.2，適用於 90Hz 頭戴式裝置的 HDMI 2.0 或 DisplayPort 1.2)</span><span class="sxs-lookup"><span data-stu-id="86e02-247">1x available graphics display port for&#160;headset (HDMI 1.4 or DisplayPort 1.2 for 60Hz headsets, HDMI 2.0 or DisplayPort 1.2 for 90Hz headsets)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="86e02-248">顯示器解析度</span><span class="sxs-lookup"><span data-stu-id="86e02-248">Display resolution</span></span></td><td colspan="2"> <span data-ttu-id="86e02-249">解決方法：SVGA (800 x 600) 或更大的位元深度：每像素 32 位元的色彩</span><span class="sxs-lookup"><span data-stu-id="86e02-249">Resolution: SVGA (800x600) or greater Bit depth: 32 bits of color per pixel</span></span></td>
</tr><tr>
<td> <span data-ttu-id="86e02-250">Memory</span><span class="sxs-lookup"><span data-stu-id="86e02-250">Memory</span></span></td><td> <span data-ttu-id="86e02-251">8&#160;GB RAM 或更大</span><span class="sxs-lookup"><span data-stu-id="86e02-251">8&#160;GB of RAM or greater</span></span></td><td> <span data-ttu-id="86e02-252">16 GB RAM 或更大</span><span class="sxs-lookup"><span data-stu-id="86e02-252">16 GB of RAM or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="86e02-253">存放裝置</span><span class="sxs-lookup"><span data-stu-id="86e02-253">Storage</span></span></td><td colspan="2"> <span data-ttu-id="86e02-254">&gt;10 GB 額外可用空間</span><span class="sxs-lookup"><span data-stu-id="86e02-254">&gt;10 GB additional free space</span></span></td>
</tr><tr>
<td> <span data-ttu-id="86e02-255">USB 連接埠</span><span class="sxs-lookup"><span data-stu-id="86e02-255">USB Ports</span></span></td><td colspan="2"> <span data-ttu-id="86e02-256">適用於頭戴式裝置的 1x 可用 USB 連接埠 (USB 3.0 Type-A) <b>注意：USB 必須提供至少 900mA</b></span><span class="sxs-lookup"><span data-stu-id="86e02-256">1x available USB port for headset (USB 3.0 Type-A) <b>Note: USB must supply a minimum of 900mA</b></span></span></td>
</tr><tr>
<td> <span data-ttu-id="86e02-257">Bluetooth</span><span class="sxs-lookup"><span data-stu-id="86e02-257">Bluetooth</span></span></td><td colspan="2"> <span data-ttu-id="86e02-258">Bluetooth 4.0 (適用於周邊連線)</span><span class="sxs-lookup"><span data-stu-id="86e02-258">Bluetooth 4.0 (for accessory connectivity)</span></span></td>
</tr>
</table>

<span data-ttu-id="86e02-259">如果您是首次使用 Unreal 進行 MRTK 開發，建議您依循我們策劃的 Unreal 開發旅程：</span><span class="sxs-lookup"><span data-stu-id="86e02-259">If you're new to MRTK development with Unreal, we recommend following our curated Unreal development journey:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="86e02-260">開始您的 Unreal 旅程</span><span class="sxs-lookup"><span data-stu-id="86e02-260">Start your Unreal journey</span></span>](../unreal/unreal-development-overview.md)

## <a name="next-development-checkpoint"></a><span data-ttu-id="86e02-261">下一個開發檢查點</span><span class="sxs-lookup"><span data-stu-id="86e02-261">Next Development Checkpoint</span></span>

<span data-ttu-id="86e02-262">依循我們配置的 Unreal 開發檢查點旅程，您的下一個工作將是進行 HoloLens 2 教學課程系列。</span><span class="sxs-lookup"><span data-stu-id="86e02-262">If you're following the Unreal development checkpoint journey we've laid out, your next task is to work through our HoloLens 2 tutorial series.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="86e02-263">HoloLens 2 教學課程系列</span><span class="sxs-lookup"><span data-stu-id="86e02-263">HoloLens 2 tutorial series</span></span>](../unreal/tutorials/unreal-uxt-ch1.md)

<span data-ttu-id="86e02-264">您可以隨時回到 [Unreal 開發檢查點](../unreal/unreal-development-overview.md#1-getting-started)。</span><span class="sxs-lookup"><span data-stu-id="86e02-264">You can always go back to the [Unreal development checkpoints](../unreal/unreal-development-overview.md#1-getting-started) at any time.</span></span>

# <a name="native-openxr"></a>[<span data-ttu-id="86e02-265">原生 (OpenXR)</span><span class="sxs-lookup"><span data-stu-id="86e02-265">Native (OpenXR)</span></span>](#tab/native)

 ![原生應用程式開發](../images/native_logo_banner.png)

<span data-ttu-id="86e02-267">原生 OpenXR 開發沒有可供您下載的引擎。</span><span class="sxs-lookup"><span data-stu-id="86e02-267">Native OpenXR development doesn't have an engine for you to download.</span></span> <span data-ttu-id="86e02-268">您可以在[開始使用 OpenXR](../native/openxr-getting-started.md) 文件中找到開始進行開發所需的一切資訊。</span><span class="sxs-lookup"><span data-stu-id="86e02-268">You can find everything you need to begin development in the [Getting started with OpenXR](../native/openxr-getting-started.md) document.</span></span>

### <a name="1-set-up-your-pc-for-mixed-reality-development"></a><span data-ttu-id="86e02-269">1.設定您的電腦以便進行混合實境開發</span><span class="sxs-lookup"><span data-stu-id="86e02-269">1. Set up your PC for mixed reality development</span></span>

<span data-ttu-id="86e02-270">Windows 10 SDK 最適合用於 Windows 10 作業系統。</span><span class="sxs-lookup"><span data-stu-id="86e02-270">The Windows 10 SDK works best on the Windows 10 operating system.</span></span> <span data-ttu-id="86e02-271">Windows 8.1、Windows 8、Windows 7、Windows Server 2012、Windows Server 2008 R2 也支援此 SDK。</span><span class="sxs-lookup"><span data-stu-id="86e02-271">This SDK is also supported on Windows 8.1, Windows 8, Windows 7, Windows Server 2012, Windows Server 2008 R2.</span></span> <span data-ttu-id="86e02-272">請注意，舊版作業系統不支援所有工具。</span><span class="sxs-lookup"><span data-stu-id="86e02-272">Note that not all tools are supported on older operating systems.</span></span>

#### <a name="for-hololens-development"></a><span data-ttu-id="86e02-273">對於 HoloLens 開發</span><span class="sxs-lookup"><span data-stu-id="86e02-273">For HoloLens development</span></span>

<span data-ttu-id="86e02-274">設定您的開發電腦以便進行 HoloLens 開發時，請確定您符合 <a href="//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a> 的系統需求。</span><span class="sxs-lookup"><span data-stu-id="86e02-274">When setting up your development PC for HoloLens development, please make sure you meet the system requirements for <a href="//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a>.</span></span> <span data-ttu-id="86e02-275">如果您想要在 HoloLens 裝置上執行您的應用程式，則必須遵循 [Windows 裝置入口網站安裝指示](../platform-capabilities-and-apis/using-the-windows-device-portal.md#setting-up-hololens-to-use-windows-device-portal)。</span><span class="sxs-lookup"><span data-stu-id="86e02-275">If you want to run your app on a HoloLens device, you need to follow the [Windows Device Portal setup instructions](../platform-capabilities-and-apis/using-the-windows-device-portal.md#setting-up-hololens-to-use-windows-device-portal).</span></span> <span data-ttu-id="86e02-276">如果您打算使用 [HoloLens 模擬器](../platform-capabilities-and-apis/using-the-hololens-emulator.md)，您應確定您的電腦也符合 [HoloLens 模擬器系統需求](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements)。</span><span class="sxs-lookup"><span data-stu-id="86e02-276">If you plan on using the [HoloLens emulator](../platform-capabilities-and-apis/using-the-hololens-emulator.md), you'll want to make sure your PC meets the [HoloLens emulator system requirements](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements) as well.</span></span>

<span data-ttu-id="86e02-277">如果您打算針對 HoloLens 與 Windows Mixed Reality 沈浸式 (VR) 頭戴裝置進行開發，請使用下一節中的系統建議和需求。</span><span class="sxs-lookup"><span data-stu-id="86e02-277">If you plan to develop for both HoloLens and Windows Mixed Reality immersive (VR) headsets, use the system recommendations and requirements in the section below.</span></span>

> [!NOTE]
> <span data-ttu-id="86e02-278">您可以針對 HoloLens、VR 沉浸式頭戴裝置或兩者開發及部署應用程式。</span><span class="sxs-lookup"><span data-stu-id="86e02-278">You can develop and deploy your apps for HoloLens, VR immersive headsets, or both.</span></span> <span data-ttu-id="86e02-279">視您的需求而定，請確定您符合下列需求。</span><span class="sxs-lookup"><span data-stu-id="86e02-279">Make sure you fulfill the requirements below depending on your needs.</span></span>

#### <a name="hololens-troubleshooting"></a><span data-ttu-id="86e02-280">HoloLens 疑難排解</span><span class="sxs-lookup"><span data-stu-id="86e02-280">HoloLens troubleshooting</span></span>

##### <a name="setting-developer-mode-is-grayed-out"></a><span data-ttu-id="86e02-281">設定開發人員模式呈現灰色</span><span class="sxs-lookup"><span data-stu-id="86e02-281">Setting Developer Mode is grayed out</span></span>

<span data-ttu-id="86e02-282">如果您在裝置上啟用開發人員模式時遇到問題，您可能不是[裝置擁有者](/hololens/security-adminless-os)。</span><span class="sxs-lookup"><span data-stu-id="86e02-282">If you're running into issues enabling Developer Mode on your device you might not be the [device owner](/hololens/security-adminless-os).</span></span> <span data-ttu-id="86e02-283">在多使用者模式中，第一個使用裝置的人員就是裝置擁有者，任何後續的使用者都不會擁有啟用 [開發人員模式] 或其他組態變更所需的權限。</span><span class="sxs-lookup"><span data-stu-id="86e02-283">In multi-user mode, the person who uses the device first is the device owner - any subsequent users won't have the required permissions to enable Developer Mode or other configuration changes.</span></span> <span data-ttu-id="86e02-284">不過，有一個例外狀況，那就是第一個使用者可能不是 Autopilot 環境中的裝置擁有者，這會在 [HoloLens 安全性文件](/hololens/security-adminless-os#device-owner)詳述。</span><span class="sxs-lookup"><span data-stu-id="86e02-284">However, there is an exception where the first user may not be the device owner in an Autopilot environment, which is detailed in the [HoloLens security documentation](/hololens/security-adminless-os#device-owner).</span></span>

<span data-ttu-id="86e02-285">可能的解決方案包括：</span><span class="sxs-lookup"><span data-stu-id="86e02-285">Possible solutions include:</span></span>

* <span data-ttu-id="86e02-286">在將裝置傳遞給其他使用者或開發人員之前，讓裝置擁有者開啟開發人員模式</span><span class="sxs-lookup"><span data-stu-id="86e02-286">Having the device owner turn Developer Mode on before passing the device to other users or developers</span></span>
* <span data-ttu-id="86e02-287">建議您的 IT/MDM 管理員針對特定裝置或開發人員裝置群組啟用 CSP [Policy ApplicationManagement/AllowDeveloperUnlock](/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock)。</span><span class="sxs-lookup"><span data-stu-id="86e02-287">Suggesting that your IT/MDM Admin enables CSP [Policy ApplicationManagement/AllowDeveloperUnlock](/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock) for the specific device or a developer device group.</span></span> 
    * <span data-ttu-id="86e02-288">此原則可經由[佈建套件](/hololens/hololens-provisioning)或透過 [HoloLens 裝置的 MDM](/hololens/hololens-mdm-configure) 來設定</span><span class="sxs-lookup"><span data-stu-id="86e02-288">This policy can be set by [Provisioning Packages](/hololens/hololens-provisioning) or via [MDM for HoloLens devices](/hololens/hololens-mdm-configure)</span></span>
* <span data-ttu-id="86e02-289">使用 [Advanced Recovery Companion (ARC)](/hololens/hololens-recovery)</span><span class="sxs-lookup"><span data-stu-id="86e02-289">Using the [Advanced Recovery Companion (ARC)](/hololens/hololens-recovery)</span></span>

> [!NOTE]
> <span data-ttu-id="86e02-290">您可以在 **[HoloLens 裝置管理](/hololens/hololens-csp-policy-overview)** 概觀中深入了解裝置管理。</span><span class="sxs-lookup"><span data-stu-id="86e02-290">You can learn more about device management in the **[HoloLens device management](/hololens/hololens-csp-policy-overview)** overview.</span></span>

#### <a name="immersive-vr-headset-requirements"></a><span data-ttu-id="86e02-291">沈浸式 (VR) 頭戴式裝置需求</span><span class="sxs-lookup"><span data-stu-id="86e02-291">Immersive (VR) headset requirements</span></span>

>[!NOTE]
><span data-ttu-id="86e02-292">下列指導方針是沈浸式 (VR) 頭戴裝置「開發電腦」目前的最低建議規格，而且會定期更新。</span><span class="sxs-lookup"><span data-stu-id="86e02-292">The following guidelines are the current minimum and recommended specs for your immersive (VR) headset *development PC*, and are updated regularly.</span></span>

>[!WARNING]
><span data-ttu-id="86e02-293">請勿將此指導方針與[最低電腦硬體相容性指導方針](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)混淆，其中概述了沈浸式 (VR) 頭戴裝置應用程式或遊戲應該定向的「取用者電腦規格」。</span><span class="sxs-lookup"><span data-stu-id="86e02-293">Do not confuse this with the [minimum PC hardware compatibility guidelines](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines), which outlines the *consumer PC specs* to which you should target your immersive (VR) headset app or game.</span></span>

<span data-ttu-id="86e02-294">如果沉浸式頭戴裝置開發電腦沒有完整大小的 HDMI 和/或 USB 3.0 連接埠，您需要[配接器](/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs)才能連線頭戴式裝置。</span><span class="sxs-lookup"><span data-stu-id="86e02-294">If your immersive headset development PC does not have full-sized HDMI and/or USB 3.0 ports, you'll need [adapters](/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs) to connect your headset.</span></span>

<span data-ttu-id="86e02-295">目前某些硬體設定有[已知問題](/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)，尤其是具有混合式圖形的筆記型電腦。</span><span class="sxs-lookup"><span data-stu-id="86e02-295">There are currently [known issues](/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality) with some hardware configurations, particularly notebooks that have hybrid graphics.</span></span>

<table>
<tr>
<th></th><th> <span data-ttu-id="86e02-296">最低需求</span><span class="sxs-lookup"><span data-stu-id="86e02-296">Minimum</span></span></th><th> <span data-ttu-id="86e02-297">建議</span><span class="sxs-lookup"><span data-stu-id="86e02-297">Recommended</span></span></th>
</tr><tr>
<td> <span data-ttu-id="86e02-298">處理器</span><span class="sxs-lookup"><span data-stu-id="86e02-298">Processor</span></span></td><td> <span data-ttu-id="86e02-299"><b>筆記型電腦：</b>Intel Mobile Core i5 第 7 代 CPU、採用超執行緒技術的雙核心 <b>傳統型：</b>Intel Desktop i5 第 6 代 CPU、採用超執行緒技術的雙核心<b>或</b> AMD FX4350 4.2Ghz 四核心對等項目</span><span class="sxs-lookup"><span data-stu-id="86e02-299"><b>Notebook:</b> Intel Mobile Core i5 7th generation CPU, Dual-Core with Hyper Threading <b>Desktop:</b> Intel Desktop i5 6th generation CPU, Dual-Core with Hyper Threading <b>OR</b> AMD FX4350 4.2Ghz Quad-Core equivalent</span></span></td><td> <span data-ttu-id="86e02-300"><b>傳統型：</b>Intel Desktop i7 第 6 代 (6 核心) <b>或</b> AMD Ryzen 5 1600 (6 核心，12 個執行緒)</span><span class="sxs-lookup"><span data-stu-id="86e02-300"><b>Desktop:</b> Intel Desktop i7 6th generation (6 Core) <b>OR</b> AMD Ryzen 5 1600 (6 Core, 12 threads)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="86e02-301">GPU</span><span class="sxs-lookup"><span data-stu-id="86e02-301">GPU</span></span></td><td> <span data-ttu-id="86e02-302"><b>筆記型電腦：</b>NVIDIA GTX 965M、AMD RX 460M (2GB) 對等項目或更高的 DX12 支援 GPU <b>傳統型：</b>NVIDIA GTX 960/1050、AMD Radeon RX 460 (2GB) 對等項目或更高的 DX12 支援 GPU</span><span class="sxs-lookup"><span data-stu-id="86e02-302"><b>Notebook:</b> NVIDIA GTX 965M, AMD RX 460M (2GB) equivalent or greater DX12 capable GPU <b>Desktop:</b> NVIDIA GTX 960/1050, AMD Radeon RX 460 (2GB) equivalent or greater DX12 capable GPU</span></span></td><td><span data-ttu-id="86e02-303"><b>傳統型：</b>NVIDIA GTX 980/1060、AMD Radeon RX 480 (2GB) 對等項目或更高的 DX12 支援 GPU</span><span class="sxs-lookup"><span data-stu-id="86e02-303"><b>Desktop:</b> NVIDIA GTX 980/1060, AMD Radeon RX 480 (2GB) equivalent or greater DX12 capable GPU</span></span></td>
</tr><tr>
<td> <span data-ttu-id="86e02-304">GPU 驅動程式 WDDM 版本</span><span class="sxs-lookup"><span data-stu-id="86e02-304">GPU driver WDDM version</span></span></td><td colspan="2"> <span data-ttu-id="86e02-305">WDDM 2.2 驅動程式</span><span class="sxs-lookup"><span data-stu-id="86e02-305">WDDM 2.2 driver</span></span></td>
</tr><tr>
<td> <span data-ttu-id="86e02-306">散熱設計功率</span><span class="sxs-lookup"><span data-stu-id="86e02-306">Thermal Design Power</span></span></td><td colspan="2"> <span data-ttu-id="86e02-307">15W 或更大</span><span class="sxs-lookup"><span data-stu-id="86e02-307">15W or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="86e02-308">圖形顯示連接埠</span><span class="sxs-lookup"><span data-stu-id="86e02-308">Graphics display ports</span></span></td><td colspan="2"> <span data-ttu-id="86e02-309">適用於頭戴式裝置的 1x 可用圖形顯示連接埠 (適用於 60Hz 頭戴式裝置的 HDMI 1.4 或 DisplayPort 1.2，適用於 90Hz 頭戴式裝置的 HDMI 2.0 或 DisplayPort 1.2)</span><span class="sxs-lookup"><span data-stu-id="86e02-309">1x available graphics display port for&#160;headset (HDMI 1.4 or DisplayPort 1.2 for 60Hz headsets, HDMI 2.0 or DisplayPort 1.2 for 90Hz headsets)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="86e02-310">顯示器解析度</span><span class="sxs-lookup"><span data-stu-id="86e02-310">Display resolution</span></span></td><td colspan="2"> <span data-ttu-id="86e02-311">解決方法：SVGA (800 x 600) 或更大的位元深度：每像素 32 位元的色彩</span><span class="sxs-lookup"><span data-stu-id="86e02-311">Resolution: SVGA (800x600) or greater Bit depth: 32 bits of color per pixel</span></span></td>
</tr><tr>
<td> <span data-ttu-id="86e02-312">Memory</span><span class="sxs-lookup"><span data-stu-id="86e02-312">Memory</span></span></td><td> <span data-ttu-id="86e02-313">8&#160;GB RAM 或更大</span><span class="sxs-lookup"><span data-stu-id="86e02-313">8&#160;GB of RAM or greater</span></span></td><td> <span data-ttu-id="86e02-314">16 GB RAM 或更大</span><span class="sxs-lookup"><span data-stu-id="86e02-314">16 GB of RAM or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="86e02-315">存放裝置</span><span class="sxs-lookup"><span data-stu-id="86e02-315">Storage</span></span></td><td colspan="2"> <span data-ttu-id="86e02-316">&gt;10 GB 額外可用空間</span><span class="sxs-lookup"><span data-stu-id="86e02-316">&gt;10 GB additional free space</span></span></td>
</tr><tr>
<td> <span data-ttu-id="86e02-317">USB 連接埠</span><span class="sxs-lookup"><span data-stu-id="86e02-317">USB Ports</span></span></td><td colspan="2"> <span data-ttu-id="86e02-318">適用於頭戴式裝置的 1x 可用 USB 連接埠 (USB 3.0 Type-A) <b>注意：USB 必須提供至少 900mA</b></span><span class="sxs-lookup"><span data-stu-id="86e02-318">1x available USB port for headset (USB 3.0 Type-A) <b>Note: USB must supply a minimum of 900mA</b></span></span></td>
</tr><tr>
<td> <span data-ttu-id="86e02-319">Bluetooth</span><span class="sxs-lookup"><span data-stu-id="86e02-319">Bluetooth</span></span></td><td colspan="2"> <span data-ttu-id="86e02-320">Bluetooth 4.0 (適用於周邊連線)</span><span class="sxs-lookup"><span data-stu-id="86e02-320">Bluetooth 4.0 (for accessory connectivity)</span></span></td>
</tr>
</table>

<span data-ttu-id="86e02-321">如果您是首次使用 MRTK 進行原生開發，建議您依循我們策劃的原生開發旅程：</span><span class="sxs-lookup"><span data-stu-id="86e02-321">If you're new to Native development with MRTK, we recommend following our curated Native development journey:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="86e02-322">開始您的原生旅程</span><span class="sxs-lookup"><span data-stu-id="86e02-322">Start your Native journey</span></span>](../native/directx-development-overview.md)

## <a name="next-development-checkpoint"></a><span data-ttu-id="86e02-323">下一個開發檢查點</span><span class="sxs-lookup"><span data-stu-id="86e02-323">Next Development Checkpoint</span></span>

<span data-ttu-id="86e02-324">依循我們配置的 Native 開發檢查點旅程，您的下一個工作將是設定 HoloLens 2 的開發環境。</span><span class="sxs-lookup"><span data-stu-id="86e02-324">If you're following the Native development checkpoint journey we've laid out, your next task is to configure your development environment for HoloLens 2.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="86e02-325">設定 HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="86e02-325">Setup for HoloLens 2</span></span>](../native/openxr-getting-started.md#getting-started-with-openxr-for-hololens-2)

<span data-ttu-id="86e02-326">您可以隨時回到[原生開發檢查點](../native/directx-development-overview.md#1-getting-started)。</span><span class="sxs-lookup"><span data-stu-id="86e02-326">You can always go back to the [Native development checkpoints](../native/directx-development-overview.md#1-getting-started) at any time.</span></span>