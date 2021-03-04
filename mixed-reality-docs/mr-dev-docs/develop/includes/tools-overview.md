---
ms.openlocfilehash: e8eb162b1d2d1e416ba90530f41d2724a960ca11
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/03/2021
ms.locfileid: "101882320"
---
# <a name="unity"></a>[<span data-ttu-id="d6c9d-101">Unity</span><span class="sxs-lookup"><span data-stu-id="d6c9d-101">Unity</span></span>](#tab/unity)

![Unity 標誌橫幅](../images/unity_logo_banner.png)<br>

### <a name="1-download-the-latest-version"></a><span data-ttu-id="d6c9d-103">1.下載最新版本</span><span class="sxs-lookup"><span data-stu-id="d6c9d-103">1. Download the latest version</span></span>

<span data-ttu-id="d6c9d-104">建議 [Unity LTS (長期支援)](https://unity3d.com/unity/qa/lts-releases) 資料流作為用來啟動新專案的最佳版本，並更新為其最新修訂版本，以挑選最新穩定的修正程式。</span><span class="sxs-lookup"><span data-stu-id="d6c9d-104">We recommend the [Unity LTS (Long Term Support)](https://unity3d.com/unity/qa/lts-releases) stream as the best version to use when starting new projects, updating to its latest revision to pick up the latest stable fixes.</span></span>
* <span data-ttu-id="d6c9d-105">目前的建議是使用 **[Unity 2019.4 LTS](https://unity3d.com/unity/qa/lts-releases?version=2019.4)**，這是下列 MRTK v2 所需的 LTS 組建。</span><span class="sxs-lookup"><span data-stu-id="d6c9d-105">The current recommendation is to use **[Unity 2019.4 LTS](https://unity3d.com/unity/qa/lts-releases?version=2019.4)**, which is the LTS build required for MRTK v2 below.</span></span>
* <span data-ttu-id="d6c9d-106">如果您基於特定理由而需要使用不同的 Unity 版本，Unity 支援不同版本的並存安裝。</span><span class="sxs-lookup"><span data-stu-id="d6c9d-106">If you need to use a different version of Unity for specific reasons, Unity supports side-by-side installs of different versions.</span></span>

### <a name="2-install-the-mixed-reality-feature-tool"></a><span data-ttu-id="d6c9d-107">2. 安裝 Mixed Reality 功能工具</span><span class="sxs-lookup"><span data-stu-id="d6c9d-107">2. Install the Mixed Reality Feature Tool</span></span>

<span data-ttu-id="d6c9d-108">「 [混合現實」功能工具](../unity/welcome-to-mr-feature-tool.md) 是一種新的方法，讓開發人員可以探索並將混合現實功能套件新增至 Unity 專案。</span><span class="sxs-lookup"><span data-stu-id="d6c9d-108">The [Mixed Reality Feature Tool](../unity/welcome-to-mr-feature-tool.md) is a new way for developers to discover and add Mixed Reality feature packages into Unity projects.</span></span> 

<span data-ttu-id="d6c9d-109">您可以依名稱或類別搜尋套件、查看其相依性，甚至在匯入之前查看專案資訊清單檔的建議變更。</span><span class="sxs-lookup"><span data-stu-id="d6c9d-109">You can search packages by name or category, see their dependencies, and even view proposed changes to your projects manifest file before importing.</span></span> <span data-ttu-id="d6c9d-110">驗證您想要的封裝之後，混合現實功能工具會將這些套件下載到您選擇的專案。</span><span class="sxs-lookup"><span data-stu-id="d6c9d-110">Once you've validated the packages you want, the Mixed Reality Feature tool will download them into the project of your choice.</span></span>

#### <a name="importing-the-mixed-reality-toolkit"></a><span data-ttu-id="d6c9d-111">匯入混合實境工具組</span><span class="sxs-lookup"><span data-stu-id="d6c9d-111">Importing the Mixed Reality Toolkit</span></span>

![MRTK](../../design/images/MRTK_UX_Hero.png)

<span data-ttu-id="d6c9d-113">[混合實境工具組](../unity/mrtk-getting-started.md) (MRTK) 是混合實境應用程式的開放原始碼跨平台開發套件。</span><span class="sxs-lookup"><span data-stu-id="d6c9d-113">[Mixed Reality Toolkit](../unity/mrtk-getting-started.md) (MRTK) is an open-source, cross-platform development kit for mixed reality applications.</span></span> 

* <span data-ttu-id="d6c9d-114">遵循 [安裝和使用方式指示](../unity/welcome-to-mr-feature-tool.md#system-requirements) ，並選取 **混合現實工具組基礎** 套件，以安裝混合現實工具組套件。</span><span class="sxs-lookup"><span data-stu-id="d6c9d-114">Install the Mixed Reality Toolkit package by following the [installation and usage instructions](../unity/welcome-to-mr-feature-tool.md#system-requirements) and selecting the **Mixed Reality Toolkit Foundation** package.</span></span>

<span data-ttu-id="d6c9d-115">建議您在策劃 [HoloLens](../unity/unity-development-overview.md#1-getting-started) 或 [VR](../unity/unity-development-wmr-overview.md#1-getting-started) 開發旅程中完成「開始使用」一節。</span><span class="sxs-lookup"><span data-stu-id="d6c9d-115">We recommend completing the getting started section in our curated [HoloLens](../unity/unity-development-overview.md#1-getting-started) or [VR](../unity/unity-development-wmr-overview.md#1-getting-started) development journeys.</span></span> <span data-ttu-id="d6c9d-116">依循適用於 HoloLens 的 Unity 開發旅程，接下來請完成下列其餘的設定步驟，並繼續進行 [HoloLens 2 開始使用教學課程](../unity/tutorials/mr-learning-base-01.md)。</span><span class="sxs-lookup"><span data-stu-id="d6c9d-116">If you're already following the Unity development for HoloLens journey, finish up the rest of the setup steps listed below and continue on to the [HoloLens 2 Getting Started tutorials](../unity/tutorials/mr-learning-base-01.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d6c9d-117">請注意，安裝指示的目標是 MRTK 和 Unity 版本的最新穩定組合（ **MRTK 2.5.1** 和 **unity 2019.4 LTS**）。</span><span class="sxs-lookup"><span data-stu-id="d6c9d-117">Note that installation instructions are targeted for the latest stable combination of MRTK and Unity releases, which are **MRTK 2.5.1** and **Unity 2019.4 LTS**.</span></span>

> [!NOTE]
> <span data-ttu-id="d6c9d-118">如果您不想要使用適用于 Unity 的 MRTK，您必須 [自行編寫所有互動和行為的腳本](../unity/configure-unity-project.md)。</span><span class="sxs-lookup"><span data-stu-id="d6c9d-118">If you don't want to use MRTK for Unity, you'll need to [script all interactions and behaviors yourself](../unity/configure-unity-project.md).</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="d6c9d-119"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">![Unity 橫幅](../images/MRTK-Unity-Banner.png)</span><span class="sxs-lookup"><span data-stu-id="d6c9d-119"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">![Unity banner](../images/MRTK-Unity-Banner.png)</span></span><br><span data-ttu-id="d6c9d-120">**混合實境工具組-Unity (GitHub)** </a></span><span class="sxs-lookup"><span data-stu-id="d6c9d-120">**Mixed Reality Toolkit-Unity (GitHub)**</a></span></span><br>
    :::column-end:::
:::row-end:::

#### <a name="other-tools-optional"></a><span data-ttu-id="d6c9d-121">其他工具 [選用]</span><span class="sxs-lookup"><span data-stu-id="d6c9d-121">Other tools [optional]</span></span>
* <span data-ttu-id="d6c9d-122"><a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">混合實境配套工具組 (GitHub)</a> - 無法直接在 HoloLens 或沈浸式 (VR) 頭戴裝置上執行的程式碼位元和元件，但是將其搭配使用可打造以 Windows Mixed Reality 為目標的體驗。</span><span class="sxs-lookup"><span data-stu-id="d6c9d-122"><a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">Mixed Reality Companion Kit (GitHub)</a> - code bits and components that might not run directly on HoloLens or immersive (VR) headsets, but instead pair with them to build experiences targeting Windows Mixed Reality.</span></span>
* <span data-ttu-id="d6c9d-123"><a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">混合的現實工具組 - 通用 (GitHub)</a> - 共用指令碼和元件的集合。</span><span class="sxs-lookup"><span data-stu-id="d6c9d-123"><a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">Mixed Reality Toolkit - Common (GitHub)</a> - a collection of shared scripts and components.</span></span>

### <a name="3-set-up-your-pc-for-mixed-reality-development"></a><span data-ttu-id="d6c9d-124">3.設定您的電腦以便進行混合實境開發</span><span class="sxs-lookup"><span data-stu-id="d6c9d-124">3. Set up your PC for Mixed Reality development</span></span>

<span data-ttu-id="d6c9d-125">Windows 10 SDK 最適合用於 Windows 10 作業系統。</span><span class="sxs-lookup"><span data-stu-id="d6c9d-125">The Windows 10 SDK works best on the Windows 10 operating system.</span></span> <span data-ttu-id="d6c9d-126">Windows 8.1、Windows 8、Windows 7、Windows Server 2012、Windows Server 2008 R2 也支援此 SDK。</span><span class="sxs-lookup"><span data-stu-id="d6c9d-126">This SDK is also supported on Windows 8.1, Windows 8, Windows 7, Windows Server 2012, Windows Server 2008 R2.</span></span> <span data-ttu-id="d6c9d-127">請注意，舊版作業系統不支援所有工具。</span><span class="sxs-lookup"><span data-stu-id="d6c9d-127">Note that not all tools are supported on older operating systems.</span></span>

> [!NOTE]
> <span data-ttu-id="d6c9d-128">您可以針對 HoloLens、VR 沉浸式頭戴裝置或兩者開發及部署應用程式。</span><span class="sxs-lookup"><span data-stu-id="d6c9d-128">You can develop and deploy your apps for HoloLens, VR immersive headsets, or both.</span></span> <span data-ttu-id="d6c9d-129">視您的需求而定，請確定您符合下列需求。</span><span class="sxs-lookup"><span data-stu-id="d6c9d-129">Make sure you fulfill the requirements below depending on your needs.</span></span>

#### <a name="for-hololens-development"></a><span data-ttu-id="d6c9d-130">對於 HoloLens 開發</span><span class="sxs-lookup"><span data-stu-id="d6c9d-130">For HoloLens development</span></span>

<span data-ttu-id="d6c9d-131">設定您的開發電腦以便進行 HoloLens 開發時，請確定其同時符合 <a href="https://unity3d.com/unity/system-requirements" target="_blank">Unity</a> 和 <a href="//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a> 的系統需求。</span><span class="sxs-lookup"><span data-stu-id="d6c9d-131">When setting up your development PC for HoloLens development, please make sure it meets the system requirements for both <a href="https://unity3d.com/unity/system-requirements" target="_blank">Unity</a> and <a href="//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a>.</span></span> <span data-ttu-id="d6c9d-132">如果您想要在 HoloLens 裝置上執行您的應用程式，則必須遵循 [Windows 裝置入口網站安裝指示](../platform-capabilities-and-apis/using-the-windows-device-portal.md#setting-up-hololens-to-use-windows-device-portal)。</span><span class="sxs-lookup"><span data-stu-id="d6c9d-132">If you want to run your app on a HoloLens device, you need to follow the [Windows Device Portal setup instructions](../platform-capabilities-and-apis/using-the-windows-device-portal.md#setting-up-hololens-to-use-windows-device-portal).</span></span> <span data-ttu-id="d6c9d-133">如果您打算使用 [HoloLens 模擬器](../platform-capabilities-and-apis/using-the-hololens-emulator.md)，您應確定您的電腦也符合 [HoloLens 模擬器系統需求](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements)。</span><span class="sxs-lookup"><span data-stu-id="d6c9d-133">If you plan on using the [HoloLens emulator](../platform-capabilities-and-apis/using-the-hololens-emulator.md), you'll want to make sure your PC meets the [HoloLens emulator system requirements](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements) as well.</span></span>

<span data-ttu-id="d6c9d-134">若要開始使用 HoloLens 模擬器，請參閱[使用 HoloLens 模擬器](../platform-capabilities-and-apis/using-the-hololens-emulator.md)。</span><span class="sxs-lookup"><span data-stu-id="d6c9d-134">To get started with the HoloLens emulator, see [Using the HoloLens emulator](../platform-capabilities-and-apis/using-the-hololens-emulator.md).</span></span>

<span data-ttu-id="d6c9d-135">如果您打算針對 HoloLens 與 Windows Mixed Reality 沈浸式 (VR) 頭戴裝置進行開發，請使用下一節中的系統建議和需求。</span><span class="sxs-lookup"><span data-stu-id="d6c9d-135">If you plan to develop for both HoloLens and Windows Mixed Reality immersive (VR) headsets, use the system recommendations and requirements in the section below.</span></span>

#### <a name="hololens-troubleshooting"></a><span data-ttu-id="d6c9d-136">HoloLens 疑難排解</span><span class="sxs-lookup"><span data-stu-id="d6c9d-136">HoloLens troubleshooting</span></span>

##### <a name="setting-developer-mode-is-grayed-out"></a><span data-ttu-id="d6c9d-137">設定開發人員模式呈現灰色</span><span class="sxs-lookup"><span data-stu-id="d6c9d-137">Setting Developer Mode is grayed out</span></span>

<span data-ttu-id="d6c9d-138">如果您在裝置上啟用開發人員模式時遇到問題，您可能不是[裝置擁有者](/hololens/security-adminless-os)。</span><span class="sxs-lookup"><span data-stu-id="d6c9d-138">If you're running into issues enabling Developer Mode on your device you might not be the [device owner](/hololens/security-adminless-os).</span></span> <span data-ttu-id="d6c9d-139">在多使用者模式中，第一個使用裝置的人員就是裝置擁有者，任何後續的使用者都不會擁有啟用 [開發人員模式] 或其他組態變更所需的權限。</span><span class="sxs-lookup"><span data-stu-id="d6c9d-139">In multi-user mode, the person who uses the device first is the device owner - any subsequent users won't have the required permissions to enable Developer Mode or other configuration changes.</span></span> <span data-ttu-id="d6c9d-140">不過，有一個例外狀況，那就是第一個使用者可能不是 Autopilot 環境中的裝置擁有者，這會在 [HoloLens 安全性文件](/hololens/security-adminless-os#device-owner)詳述。</span><span class="sxs-lookup"><span data-stu-id="d6c9d-140">However, there is an exception where the first user may not be the device owner in an Autopilot environment, which is detailed in the [HoloLens security documentation](/hololens/security-adminless-os#device-owner).</span></span>

<span data-ttu-id="d6c9d-141">可能的解決方案包括：</span><span class="sxs-lookup"><span data-stu-id="d6c9d-141">Possible solutions include:</span></span>

* <span data-ttu-id="d6c9d-142">在將裝置傳遞給其他使用者或開發人員之前，讓裝置擁有者開啟開發人員模式</span><span class="sxs-lookup"><span data-stu-id="d6c9d-142">Having the device owner turn Developer Mode on before passing the device to other users or developers</span></span>
* <span data-ttu-id="d6c9d-143">建議您的 IT/MDM 管理員針對特定裝置或開發人員裝置群組啟用 CSP [Policy ApplicationManagement/AllowDeveloperUnlock](/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock)。</span><span class="sxs-lookup"><span data-stu-id="d6c9d-143">Suggesting that your IT/MDM Admin enables CSP [Policy ApplicationManagement/AllowDeveloperUnlock](/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock) for the specific device or a developer device group.</span></span> 
    * <span data-ttu-id="d6c9d-144">此原則可經由[佈建套件](/hololens/hololens-provisioning)或透過 [HoloLens 裝置的 MDM](/hololens/hololens-mdm-configure) 來設定</span><span class="sxs-lookup"><span data-stu-id="d6c9d-144">This policy can be set by [Provisioning Packages](/hololens/hololens-provisioning) or via [MDM for HoloLens devices](/hololens/hololens-mdm-configure)</span></span>
* <span data-ttu-id="d6c9d-145">使用 [Advanced Recovery Companion (ARC)](/hololens/hololens-recovery)</span><span class="sxs-lookup"><span data-stu-id="d6c9d-145">Using the [Advanced Recovery Companion (ARC)](/hololens/hololens-recovery)</span></span>

> [!NOTE]
> <span data-ttu-id="d6c9d-146">您可以在 **[HoloLens 裝置管理](/hololens/hololens-csp-policy-overview)** 概觀中深入了解裝置管理。</span><span class="sxs-lookup"><span data-stu-id="d6c9d-146">You can learn more about device management in the **[HoloLens device management](/hololens/hololens-csp-policy-overview)** overview.</span></span>

##### <a name="i-cant-deploy-over-usb"></a><span data-ttu-id="d6c9d-147">我無法透過 USB 部署</span><span class="sxs-lookup"><span data-stu-id="d6c9d-147">I can't deploy over USB</span></span>

<span data-ttu-id="d6c9d-148">如果您無法直接透過 USB 部署應用程式，請確定您符合上述所有的安裝需求，並遵循我們的[逐步教學課程](../unity/tutorials/mr-learning-base-02.md#building-your-application-to-your-hololens-2)。</span><span class="sxs-lookup"><span data-stu-id="d6c9d-148">If you're not able to deploy an application directly over USB, make sure you've met all the installation requirements listed above and follow our [step-by-step tutorial](../unity/tutorials/mr-learning-base-02.md#building-your-application-to-your-hololens-2).</span></span>

#### <a name="immersive-vr-headset-requirements"></a><span data-ttu-id="d6c9d-149">沈浸式 (VR) 頭戴式裝置需求</span><span class="sxs-lookup"><span data-stu-id="d6c9d-149">Immersive (VR) headset requirements</span></span>

>[!NOTE]
><span data-ttu-id="d6c9d-150">下列指導方針是沈浸式 (VR) 頭戴裝置「開發電腦」目前的最低建議規格，而且會定期更新。</span><span class="sxs-lookup"><span data-stu-id="d6c9d-150">The following guidelines are the current minimum and recommended specs for your immersive (VR) headset *development PC*, and are updated regularly.</span></span>

>[!WARNING]
><span data-ttu-id="d6c9d-151">請勿將此指導方針與[最低電腦硬體相容性指導方針](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)混淆，其中概述了沈浸式 (VR) 頭戴裝置應用程式或遊戲應該定向的「取用者電腦規格」。</span><span class="sxs-lookup"><span data-stu-id="d6c9d-151">Do not confuse this with the [minimum PC hardware compatibility guidelines](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines), which outlines the *consumer PC specs* to which you should target your immersive (VR) headset app or game.</span></span>

<span data-ttu-id="d6c9d-152">如果沉浸式頭戴裝置開發電腦沒有完整大小的 HDMI 和/或 USB 3.0 連接埠，您需要[配接器](/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs)才能連線頭戴式裝置。</span><span class="sxs-lookup"><span data-stu-id="d6c9d-152">If your immersive headset development PC does not have full-sized HDMI and/or USB 3.0 ports, you'll need [adapters](/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs) to connect your headset.</span></span>

<span data-ttu-id="d6c9d-153">目前某些硬體設定有[已知問題](/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)，尤其是具有混合式圖形的筆記型電腦。</span><span class="sxs-lookup"><span data-stu-id="d6c9d-153">There are currently [known issues](/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality) with some hardware configurations, particularly notebooks that have hybrid graphics.</span></span>

<table>
<tr>
<th></th><th> <span data-ttu-id="d6c9d-154">最低需求</span><span class="sxs-lookup"><span data-stu-id="d6c9d-154">Minimum</span></span></th><th> <span data-ttu-id="d6c9d-155">建議</span><span class="sxs-lookup"><span data-stu-id="d6c9d-155">Recommended</span></span></th>
</tr><tr>
<td> <span data-ttu-id="d6c9d-156">處理器</span><span class="sxs-lookup"><span data-stu-id="d6c9d-156">Processor</span></span></td><td> <span data-ttu-id="d6c9d-157"><b>筆記型電腦：</b>Intel Mobile Core i5 第 7 代 CPU、採用超執行緒技術的雙核心 <b>傳統型：</b>Intel Desktop i5 第 6 代 CPU、採用超執行緒技術的雙核心<b>或</b> AMD FX4350 4.2Ghz 四核心對等項目</span><span class="sxs-lookup"><span data-stu-id="d6c9d-157"><b>Notebook:</b> Intel Mobile Core i5 7th generation CPU, Dual-Core with Hyper Threading <b>Desktop:</b> Intel Desktop i5 6th generation CPU, Dual-Core with Hyper Threading <b>OR</b> AMD FX4350 4.2Ghz Quad-Core equivalent</span></span></td><td> <span data-ttu-id="d6c9d-158"><b>傳統型：</b>Intel Desktop i7 第 6 代 (6 核心) <b>或</b> AMD Ryzen 5 1600 (6 核心，12 個執行緒)</span><span class="sxs-lookup"><span data-stu-id="d6c9d-158"><b>Desktop:</b> Intel Desktop i7 6th generation (6 Core) <b>OR</b> AMD Ryzen 5 1600 (6 Core, 12 threads)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="d6c9d-159">GPU</span><span class="sxs-lookup"><span data-stu-id="d6c9d-159">GPU</span></span></td><td> <span data-ttu-id="d6c9d-160"><b>筆記型電腦：</b>NVIDIA GTX 965M、AMD RX 460M (2GB) 對等項目或更高的 DX12 支援 GPU <b>傳統型：</b>NVIDIA GTX 960/1050、AMD Radeon RX 460 (2GB) 對等項目或更高的 DX12 支援 GPU</span><span class="sxs-lookup"><span data-stu-id="d6c9d-160"><b>Notebook:</b> NVIDIA GTX 965M, AMD RX 460M (2GB) equivalent or greater DX12 capable GPU <b>Desktop:</b> NVIDIA GTX 960/1050, AMD Radeon RX 460 (2GB) equivalent or greater DX12 capable GPU</span></span></td><td><span data-ttu-id="d6c9d-161"><b>傳統型：</b>NVIDIA GTX 980/1060、AMD Radeon RX 480 (2GB) 對等項目或更高的 DX12 支援 GPU</span><span class="sxs-lookup"><span data-stu-id="d6c9d-161"><b>Desktop:</b> NVIDIA GTX 980/1060, AMD Radeon RX 480 (2GB) equivalent or greater DX12 capable GPU</span></span></td>
</tr><tr>
<td> <span data-ttu-id="d6c9d-162">GPU 驅動程式 WDDM 版本</span><span class="sxs-lookup"><span data-stu-id="d6c9d-162">GPU driver WDDM version</span></span></td><td colspan="2"> <span data-ttu-id="d6c9d-163">WDDM 2.2 驅動程式</span><span class="sxs-lookup"><span data-stu-id="d6c9d-163">WDDM 2.2 driver</span></span></td>
</tr><tr>
<td> <span data-ttu-id="d6c9d-164">散熱設計功率</span><span class="sxs-lookup"><span data-stu-id="d6c9d-164">Thermal Design Power</span></span></td><td colspan="2"> <span data-ttu-id="d6c9d-165">15W 或更大</span><span class="sxs-lookup"><span data-stu-id="d6c9d-165">15W or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="d6c9d-166">圖形顯示連接埠</span><span class="sxs-lookup"><span data-stu-id="d6c9d-166">Graphics display ports</span></span></td><td colspan="2"> <span data-ttu-id="d6c9d-167">適用於頭戴式裝置的 1x 可用圖形顯示連接埠 (適用於 60Hz 頭戴式裝置的 HDMI 1.4 或 DisplayPort 1.2，適用於 90Hz 頭戴式裝置的 HDMI 2.0 或 DisplayPort 1.2)</span><span class="sxs-lookup"><span data-stu-id="d6c9d-167">1x available graphics display port for&#160;headset (HDMI 1.4 or DisplayPort 1.2 for 60Hz headsets, HDMI 2.0 or DisplayPort 1.2 for 90Hz headsets)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="d6c9d-168">顯示器解析度</span><span class="sxs-lookup"><span data-stu-id="d6c9d-168">Display resolution</span></span></td><td colspan="2"> <span data-ttu-id="d6c9d-169">解決方法：SVGA (800 x 600) 或更大的位元深度：每像素 32 位元的色彩</span><span class="sxs-lookup"><span data-stu-id="d6c9d-169">Resolution: SVGA (800x600) or greater Bit depth: 32 bits of color per pixel</span></span></td>
</tr><tr>
<td> <span data-ttu-id="d6c9d-170">Memory</span><span class="sxs-lookup"><span data-stu-id="d6c9d-170">Memory</span></span></td><td> <span data-ttu-id="d6c9d-171">8&#160;GB RAM 或更大</span><span class="sxs-lookup"><span data-stu-id="d6c9d-171">8&#160;GB of RAM or greater</span></span></td><td> <span data-ttu-id="d6c9d-172">16 GB RAM 或更大</span><span class="sxs-lookup"><span data-stu-id="d6c9d-172">16 GB of RAM or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="d6c9d-173">存放裝置</span><span class="sxs-lookup"><span data-stu-id="d6c9d-173">Storage</span></span></td><td colspan="2"> <span data-ttu-id="d6c9d-174">&gt;10 GB 額外可用空間</span><span class="sxs-lookup"><span data-stu-id="d6c9d-174">&gt;10 GB additional free space</span></span></td>
</tr><tr>
<td> <span data-ttu-id="d6c9d-175">USB 連接埠</span><span class="sxs-lookup"><span data-stu-id="d6c9d-175">USB Ports</span></span></td><td colspan="2"> <span data-ttu-id="d6c9d-176">適用於頭戴式裝置的 1x 可用 USB 連接埠 (USB 3.0 Type-A) <b>注意：USB 必須提供至少 900mA</b></span><span class="sxs-lookup"><span data-stu-id="d6c9d-176">1x available USB port for headset (USB 3.0 Type-A) <b>Note: USB must supply a minimum of 900mA</b></span></span></td>
</tr><tr>
<td> <span data-ttu-id="d6c9d-177">Bluetooth</span><span class="sxs-lookup"><span data-stu-id="d6c9d-177">Bluetooth</span></span></td><td colspan="2"> <span data-ttu-id="d6c9d-178">Bluetooth 4.0 (適用於周邊連線)</span><span class="sxs-lookup"><span data-stu-id="d6c9d-178">Bluetooth 4.0 (for accessory connectivity)</span></span></td>
</tr>
</table>

<span data-ttu-id="d6c9d-179">如果您是首次使用 Unity 進行 MRTK 開發，建議您依循我們策劃的 Unity 開發旅程：</span><span class="sxs-lookup"><span data-stu-id="d6c9d-179">If you're new to MRTK development with Unity, we recommend following our curated Unity development journey:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="d6c9d-180">開始您適用於 HoloLens 的 Unity 開發旅程</span><span class="sxs-lookup"><span data-stu-id="d6c9d-180">Start your Unity for HoloLens journey</span></span>](../unity/unity-development-overview.md)

> [!div class="nextstepaction"]
> [<span data-ttu-id="d6c9d-181">開始您適用於 VR 的 Unity 開發旅程</span><span class="sxs-lookup"><span data-stu-id="d6c9d-181">Start your Unity for VR journey</span></span>](../unity/unity-development-wmr-overview.md)

## <a name="next-development-checkpoint"></a><span data-ttu-id="d6c9d-182">下一個開發檢查點</span><span class="sxs-lookup"><span data-stu-id="d6c9d-182">Next Development Checkpoint</span></span>

<span data-ttu-id="d6c9d-183">依循我們所配置適用於 HoloLens 的 Unity 開發檢查點旅程，您的下一個工作將是進行 HoloLens 2 教學課程系列。</span><span class="sxs-lookup"><span data-stu-id="d6c9d-183">If you're following the Unity for HoloLens development checkpoint journey we've laid out, your next task is to work through our HoloLens 2 tutorial series.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="d6c9d-184">HoloLens 2 教學課程系列</span><span class="sxs-lookup"><span data-stu-id="d6c9d-184">HoloLens 2 tutorial series</span></span>](../unity/tutorials/mr-learning-base-01.md)

<span data-ttu-id="d6c9d-185">如果您要依循適用於 VR 的 Unity 旅程，下一個工作是設定您的專案。</span><span class="sxs-lookup"><span data-stu-id="d6c9d-185">If you're following the Unity for VR journey, your next task is to setup your project.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="d6c9d-186">針對 WMR 設定您的專案</span><span class="sxs-lookup"><span data-stu-id="d6c9d-186">Configuring your project for WMR</span></span>](../unity/configure-unity-project.md)

<span data-ttu-id="d6c9d-187">您可以隨時回到適用於 [HoloLens](../unity/unity-development-overview.md#1-getting-started) 和 [VR](../unity/unity-development-wmr-overview.md#1-getting-started)的 Unity 開發檢查點。</span><span class="sxs-lookup"><span data-stu-id="d6c9d-187">You can always go back to the Unity development checkpoints for [HoloLens](../unity/unity-development-overview.md#1-getting-started) and [VR](../unity/unity-development-wmr-overview.md#1-getting-started) at any time.</span></span>

# <a name="unreal"></a>[<span data-ttu-id="d6c9d-188">Unreal</span><span class="sxs-lookup"><span data-stu-id="d6c9d-188">Unreal</span></span>](#tab/unreal)

![Unreal](../images/unreal_logo_banner.png)

### <a name="1-download-the-latest-version"></a><span data-ttu-id="d6c9d-190">1.下載最新版本</span><span class="sxs-lookup"><span data-stu-id="d6c9d-190">1. Download the latest version</span></span>

<span data-ttu-id="d6c9d-191">建議您安裝 [Unreal Engine 4.25 版](https://docs.unrealengine.com//GettingStarted/Installation/index.html)或更新版本，以充分利用內建的 HoloLens 支援。</span><span class="sxs-lookup"><span data-stu-id="d6c9d-191">We recommend installing [Unreal Engine version 4.25](https://docs.unrealengine.com//GettingStarted/Installation/index.html) or later to take full advantage of built-in HoloLens support.</span></span>

<span data-ttu-id="d6c9d-192">移至長篇遊戲啟動器中的 [ **媒體** 櫃] 索引標籤，選取 [ **啟動** ] 旁的下拉箭號，然後按一下 [ **選項**]。</span><span class="sxs-lookup"><span data-stu-id="d6c9d-192">Go to the **Library** tab in the Epic Games Launcher, select the dropdown arrow next to **Launch** and click **Options**.</span></span> <span data-ttu-id="d6c9d-193">在 [目標平台] 中，選取 **HoloLens 2**，然後按一下 [套用]。</span><span class="sxs-lookup"><span data-stu-id="d6c9d-193">Under **Target Platforms**, select **HoloLens 2** and click **Apply**.</span></span>
<span data-ttu-id="d6c9d-194">![MRTK](../../develop/images/Unreal_Install_Option_HoloLens2.png)</span><span class="sxs-lookup"><span data-stu-id="d6c9d-194">![MRTK](../../develop/images/Unreal_Install_Option_HoloLens2.png)</span></span>

### <a name="2-import-mixed-reality-toolkit-mrtk"></a><span data-ttu-id="d6c9d-195">2.匯入混合實境工具組 (MRTK)</span><span class="sxs-lookup"><span data-stu-id="d6c9d-195">2. Import Mixed Reality Toolkit (MRTK)</span></span>
![MRTK](../../design/images/MRTK_UX_Hero.png)

<span data-ttu-id="d6c9d-197">混合實境工具組 (MRTK) 是混合實境應用程式的開放原始碼跨平台開發套件。</span><span class="sxs-lookup"><span data-stu-id="d6c9d-197">Mixed Reality Toolkit (MRTK) is an open-source, cross-platform development kit for mixed reality applications.</span></span> <span data-ttu-id="d6c9d-198">MRTK 提供跨平台輸入系統、基礎元件，以及空間互動的常見基本要素。</span><span class="sxs-lookup"><span data-stu-id="d6c9d-198">MRTK provides a cross-platform input system, foundational components, and common building blocks for spatial interactions.</span></span> <span data-ttu-id="d6c9d-199">該工具組主要用於加速開發以 Microsoft HoloLens、Windows Mixed Reality 沈浸式 (VR) 頭戴裝置和 OpenVR 平台為目標的應用程式。</span><span class="sxs-lookup"><span data-stu-id="d6c9d-199">The toolkit is intended to accelerate the development of applications targeting Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets, and the OpenVR platform.</span></span>

<span data-ttu-id="d6c9d-200">進行安裝時，建議您完成我們策劃的 [Unreal 開發旅程圖](../unreal/unreal-development-overview.md)的[開始使用一節](../unreal/unreal-development-overview.md#1-getting-started)。</span><span class="sxs-lookup"><span data-stu-id="d6c9d-200">For installation, we recommend completing the [Getting Started section](../unreal/unreal-development-overview.md#1-getting-started) of our curated [Unreal development journey](../unreal/unreal-development-overview.md).</span></span> <span data-ttu-id="d6c9d-201">依循 Unreal 開發旅程，接下來請完成下列其餘的設定步驟，並繼續進行 [HoloLens 2 開始使用教學課程](../unreal/tutorials/unreal-uxt-ch1.md)。</span><span class="sxs-lookup"><span data-stu-id="d6c9d-201">If you're already following the Unreal development journey, finish up the rest of the setup steps listed below and continue on to the [HoloLens 2 Getting Started tutorials](../unreal/tutorials/unreal-uxt-ch1.md).</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="d6c9d-202"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unreal" target="_blank">![Unity 標誌影像](../images/MRTK-Unreal-Banner.png)</span><span class="sxs-lookup"><span data-stu-id="d6c9d-202"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unreal" target="_blank">![Unity logo image](../images/MRTK-Unreal-Banner.png)</span></span><br><span data-ttu-id="d6c9d-203">**混合實境工具組-Unreal (GitHub)** </a></span><span class="sxs-lookup"><span data-stu-id="d6c9d-203">**Mixed Reality Toolkit-Unreal (GitHub)**</a></span></span><br>
    :::column-end:::
:::row-end:::

> [!NOTE]
> <span data-ttu-id="d6c9d-204">如果您不想使用適用於 Unreal 的 MRTK，則必須自行撰寫所有互動和行為的指令碼。</span><span class="sxs-lookup"><span data-stu-id="d6c9d-204">If you don't want to use MRTK for Unreal, you'll need to script all interactions and behaviors yourself.</span></span>

#### <a name="other-tools-optional"></a><span data-ttu-id="d6c9d-205">其他工具 [選用]</span><span class="sxs-lookup"><span data-stu-id="d6c9d-205">Other tools [optional]</span></span>
* <span data-ttu-id="d6c9d-206"><a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">混合實境配套工具組 (GitHub)</a> - 無法直接在 HoloLens 或沈浸式 (VR) 頭戴裝置上執行的程式碼位元和元件，但是將其搭配使用可打造以 Windows Mixed Reality 為目標的體驗。</span><span class="sxs-lookup"><span data-stu-id="d6c9d-206"><a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">Mixed Reality Companion Kit (GitHub)</a> - code bits and components that might not run directly on HoloLens or immersive (VR) headsets, but instead pair with them to build experiences targeting Windows Mixed Reality.</span></span>
* <span data-ttu-id="d6c9d-207"><a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">混合的現實工具組 - 通用 (GitHub)</a> - 共用指令碼和元件的集合。</span><span class="sxs-lookup"><span data-stu-id="d6c9d-207"><a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">Mixed Reality Toolkit - Co mmon (GitHub)</a> - a collection of shared scripts and components.</span></span>

### <a name="3-set-up-your-pc-for-mixed-reality-development"></a><span data-ttu-id="d6c9d-208">3.設定您的電腦以便進行混合實境開發</span><span class="sxs-lookup"><span data-stu-id="d6c9d-208">3. Set up your PC for mixed reality development</span></span>

<span data-ttu-id="d6c9d-209">Windows 10 SDK 最適合用於 Windows 10 作業系統。</span><span class="sxs-lookup"><span data-stu-id="d6c9d-209">The Windows 10 SDK works best on the Windows 10 operating system.</span></span> <span data-ttu-id="d6c9d-210">Windows 8.1、Windows 8、Windows 7、Windows Server 2012、Windows Server 2008 R2 也支援此 SDK。</span><span class="sxs-lookup"><span data-stu-id="d6c9d-210">This SDK is also supported on Windows 8.1, Windows 8, Windows 7, Windows Server 2012, Windows Server 2008 R2.</span></span> <span data-ttu-id="d6c9d-211">請注意，舊版作業系統不支援所有工具。</span><span class="sxs-lookup"><span data-stu-id="d6c9d-211">Note that not all tools are supported on older operating systems.</span></span>

> [!NOTE]
> <span data-ttu-id="d6c9d-212">您可以針對 HoloLens、VR 沉浸式頭戴裝置或兩者開發及部署應用程式。</span><span class="sxs-lookup"><span data-stu-id="d6c9d-212">You can develop and deploy your apps for HoloLens, VR immersive headsets, or both.</span></span> <span data-ttu-id="d6c9d-213">視您的需求而定，請確定您符合下列需求。</span><span class="sxs-lookup"><span data-stu-id="d6c9d-213">Make sure you fulfill the requirements below depending on your needs.</span></span>

#### <a name="for-hololens-development"></a><span data-ttu-id="d6c9d-214">對於 HoloLens 開發</span><span class="sxs-lookup"><span data-stu-id="d6c9d-214">For HoloLens development</span></span>

<span data-ttu-id="d6c9d-215">設定您的開發電腦以便進行 HoloLens 開發時，請確定您符合 [Unity](https://docs.unrealengine.com/GettingStarted/RecommendedSpecifications/index.html) 和 <a href="//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a> 的系統需求。</span><span class="sxs-lookup"><span data-stu-id="d6c9d-215">When setting up your development PC for HoloLens development, please make sure you meet the system requirements for [Unreal](https://docs.unrealengine.com/GettingStarted/RecommendedSpecifications/index.html) and and <a href="//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a>.</span></span> <span data-ttu-id="d6c9d-216">如果您想要在 HoloLens 裝置上執行您的應用程式，則必須遵循 [Windows 裝置入口網站安裝指示](../platform-capabilities-and-apis/using-the-windows-device-portal.md#setting-up-hololens-to-use-windows-device-portal)。</span><span class="sxs-lookup"><span data-stu-id="d6c9d-216">If you want to run your app on a HoloLens device, you need to follow the [Windows Device Portal setup instructions](../platform-capabilities-and-apis/using-the-windows-device-portal.md#setting-up-hololens-to-use-windows-device-portal).</span></span> <span data-ttu-id="d6c9d-217">如果您打算使用 [HoloLens 模擬器](../platform-capabilities-and-apis/using-the-hololens-emulator.md)，您應確定您的電腦也符合 [HoloLens 模擬器系統需求](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements)。</span><span class="sxs-lookup"><span data-stu-id="d6c9d-217">If you plan on using the [HoloLens emulator](../platform-capabilities-and-apis/using-the-hololens-emulator.md), you'll want to make sure your PC meets the [HoloLens emulator system requirements](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements) as well.</span></span>

<span data-ttu-id="d6c9d-218">如果您打算針對 HoloLens 與 Windows Mixed Reality 沈浸式 (VR) 頭戴裝置進行開發，請使用下一節中的系統建議和需求。</span><span class="sxs-lookup"><span data-stu-id="d6c9d-218">If you plan to develop for both HoloLens and Windows Mixed Reality immersive (VR) headsets, use the system recommendations and requirements in the section below.</span></span>

#### <a name="hololens-troubleshooting"></a><span data-ttu-id="d6c9d-219">HoloLens 疑難排解</span><span class="sxs-lookup"><span data-stu-id="d6c9d-219">HoloLens troubleshooting</span></span>

##### <a name="setting-developer-mode-is-grayed-out"></a><span data-ttu-id="d6c9d-220">設定開發人員模式呈現灰色</span><span class="sxs-lookup"><span data-stu-id="d6c9d-220">Setting Developer Mode is grayed out</span></span>

<span data-ttu-id="d6c9d-221">如果您在裝置上啟用開發人員模式時遇到問題，您可能不是[裝置擁有者](/hololens/security-adminless-os)。</span><span class="sxs-lookup"><span data-stu-id="d6c9d-221">If you're running into issues enabling Developer Mode on your device you might not be the [device owner](/hololens/security-adminless-os).</span></span> <span data-ttu-id="d6c9d-222">在多使用者模式中，第一個使用裝置的人員就是裝置擁有者，任何後續的使用者都不會擁有啟用 [開發人員模式] 或其他組態變更所需的權限。</span><span class="sxs-lookup"><span data-stu-id="d6c9d-222">In multi-user mode, the person who uses the device first is the device owner - any subsequent users won't have the required permissions to enable Developer Mode or other configuration changes.</span></span> <span data-ttu-id="d6c9d-223">不過，有一個例外狀況，那就是第一個使用者可能不是 Autopilot 環境中的裝置擁有者，這會在 [HoloLens 安全性文件](/hololens/security-adminless-os#device-owner)詳述。</span><span class="sxs-lookup"><span data-stu-id="d6c9d-223">However, there is an exception where the first user may not be the device owner in an Autopilot environment, which is detailed in the [HoloLens security documentation](/hololens/security-adminless-os#device-owner).</span></span>

<span data-ttu-id="d6c9d-224">可能的解決方案包括：</span><span class="sxs-lookup"><span data-stu-id="d6c9d-224">Possible solutions include:</span></span>

* <span data-ttu-id="d6c9d-225">在將裝置傳遞給其他使用者或開發人員之前，讓裝置擁有者開啟開發人員模式</span><span class="sxs-lookup"><span data-stu-id="d6c9d-225">Having the device owner turn Developer Mode on before passing the device to other users or developers</span></span>
* <span data-ttu-id="d6c9d-226">建議您的 IT/MDM 管理員針對特定裝置或開發人員裝置群組啟用 CSP [Policy ApplicationManagement/AllowDeveloperUnlock](/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock)。</span><span class="sxs-lookup"><span data-stu-id="d6c9d-226">Suggesting that your IT/MDM Admin enables CSP [Policy ApplicationManagement/AllowDeveloperUnlock](/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock) for the specific device or a developer device group.</span></span> 
    * <span data-ttu-id="d6c9d-227">此原則可經由[佈建套件](/hololens/hololens-provisioning)或透過 [HoloLens 裝置的 MDM](/hololens/hololens-mdm-configure) 來設定</span><span class="sxs-lookup"><span data-stu-id="d6c9d-227">This policy can be set by [Provisioning Packages](/hololens/hololens-provisioning) or via [MDM for HoloLens devices](/hololens/hololens-mdm-configure)</span></span>
* <span data-ttu-id="d6c9d-228">使用 [Advanced Recovery Companion (ARC)](/hololens/hololens-recovery)</span><span class="sxs-lookup"><span data-stu-id="d6c9d-228">Using the [Advanced Recovery Companion (ARC)](/hololens/hololens-recovery)</span></span>

> [!NOTE]
> <span data-ttu-id="d6c9d-229">您可以在 **[HoloLens 裝置管理](/hololens/hololens-csp-policy-overview)** 概觀中深入了解裝置管理。</span><span class="sxs-lookup"><span data-stu-id="d6c9d-229">You can learn more about device management in the **[HoloLens device management](/hololens/hololens-csp-policy-overview)** overview.</span></span>

##### <a name="i-cant-deploy-over-usb"></a><span data-ttu-id="d6c9d-230">我無法透過 USB 部署</span><span class="sxs-lookup"><span data-stu-id="d6c9d-230">I can't deploy over USB</span></span>

<span data-ttu-id="d6c9d-231">如果您無法直接透過 USB 部署應用程式，請確定您符合上述所有的安裝需求，並遵循我們的[逐步教學課程](../unreal/tutorials/unreal-uxt-ch6.md)。</span><span class="sxs-lookup"><span data-stu-id="d6c9d-231">If you're not able to deploy an application directly over USB, make sure you've met all the installation requirements listed above and follow our [step-by-step tutorial](../unreal/tutorials/unreal-uxt-ch6.md).</span></span>

#### <a name="immersive-vr-headset-requirements"></a><span data-ttu-id="d6c9d-232">沈浸式 (VR) 頭戴式裝置需求</span><span class="sxs-lookup"><span data-stu-id="d6c9d-232">Immersive (VR) headset requirements</span></span>

>[!NOTE]
><span data-ttu-id="d6c9d-233">下列指導方針是沈浸式 (VR) 頭戴裝置「開發電腦」目前的最低建議規格，而且會定期更新。</span><span class="sxs-lookup"><span data-stu-id="d6c9d-233">The following guidelines are the current minimum and recommended specs for your immersive (VR) headset *development PC*, and are updated regularly.</span></span>

>[!WARNING]
><span data-ttu-id="d6c9d-234">請勿將此指導方針與[最低電腦硬體相容性指導方針](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)混淆，其中概述了沈浸式 (VR) 頭戴裝置應用程式或遊戲應該定向的「取用者電腦規格」。</span><span class="sxs-lookup"><span data-stu-id="d6c9d-234">Do not confuse this with the [minimum PC hardware compatibility guidelines](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines), which outlines the *consumer PC specs* to which you should target your immersive (VR) headset app or game.</span></span>

<span data-ttu-id="d6c9d-235">如果沉浸式頭戴裝置開發電腦沒有完整大小的 HDMI 和/或 USB 3.0 連接埠，您需要[配接器](/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs)才能連線頭戴式裝置。</span><span class="sxs-lookup"><span data-stu-id="d6c9d-235">If your immersive headset development PC does not have full-sized HDMI and/or USB 3.0 ports, you'll need [adapters](/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs) to connect your headset.</span></span>

<span data-ttu-id="d6c9d-236">目前某些硬體設定有[已知問題](/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)，尤其是具有混合式圖形的筆記型電腦。</span><span class="sxs-lookup"><span data-stu-id="d6c9d-236">There are currently [known issues](/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality) with some hardware configurations, particularly notebooks that have hybrid graphics.</span></span>

<table>
<tr>
<th></th><th> <span data-ttu-id="d6c9d-237">最低需求</span><span class="sxs-lookup"><span data-stu-id="d6c9d-237">Minimum</span></span></th><th> <span data-ttu-id="d6c9d-238">建議</span><span class="sxs-lookup"><span data-stu-id="d6c9d-238">Recommended</span></span></th>
</tr><tr>
<td> <span data-ttu-id="d6c9d-239">處理器</span><span class="sxs-lookup"><span data-stu-id="d6c9d-239">Processor</span></span></td><td> <span data-ttu-id="d6c9d-240"><b>筆記型電腦：</b>Intel Mobile Core i5 第 7 代 CPU、採用超執行緒技術的雙核心 <b>傳統型：</b>Intel Desktop i5 第 6 代 CPU、採用超執行緒技術的雙核心<b>或</b> AMD FX4350 4.2Ghz 四核心對等項目</span><span class="sxs-lookup"><span data-stu-id="d6c9d-240"><b>Notebook:</b> Intel Mobile Core i5 7th generation CPU, Dual-Core with Hyper Threading <b>Desktop:</b> Intel Desktop i5 6th generation CPU, Dual-Core with Hyper Threading <b>OR</b> AMD FX4350 4.2Ghz Quad-Core equivalent</span></span></td><td> <span data-ttu-id="d6c9d-241"><b>傳統型：</b>Intel Desktop i7 第 6 代 (6 核心) <b>或</b> AMD Ryzen 5 1600 (6 核心，12 個執行緒)</span><span class="sxs-lookup"><span data-stu-id="d6c9d-241"><b>Desktop:</b> Intel Desktop i7 6th generation (6 Core) <b>OR</b> AMD Ryzen 5 1600 (6 Core, 12 threads)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="d6c9d-242">GPU</span><span class="sxs-lookup"><span data-stu-id="d6c9d-242">GPU</span></span></td><td> <span data-ttu-id="d6c9d-243"><b>筆記型電腦：</b>NVIDIA GTX 965M、AMD RX 460M (2GB) 對等項目或更高的 DX12 支援 GPU <b>傳統型：</b>NVIDIA GTX 960/1050、AMD Radeon RX 460 (2GB) 對等項目或更高的 DX12 支援 GPU</span><span class="sxs-lookup"><span data-stu-id="d6c9d-243"><b>Notebook:</b> NVIDIA GTX 965M, AMD RX 460M (2GB) equivalent or greater DX12 capable GPU <b>Desktop:</b> NVIDIA GTX 960/1050, AMD Radeon RX 460 (2GB) equivalent or greater DX12 capable GPU</span></span></td><td><span data-ttu-id="d6c9d-244"><b>傳統型：</b>NVIDIA GTX 980/1060、AMD Radeon RX 480 (2GB) 對等項目或更高的 DX12 支援 GPU</span><span class="sxs-lookup"><span data-stu-id="d6c9d-244"><b>Desktop:</b> NVIDIA GTX 980/1060, AMD Radeon RX 480 (2GB) equivalent or greater DX12 capable GPU</span></span></td>
</tr><tr>
<td> <span data-ttu-id="d6c9d-245">GPU 驅動程式 WDDM 版本</span><span class="sxs-lookup"><span data-stu-id="d6c9d-245">GPU driver WDDM version</span></span></td><td colspan="2"> <span data-ttu-id="d6c9d-246">WDDM 2.2 驅動程式</span><span class="sxs-lookup"><span data-stu-id="d6c9d-246">WDDM 2.2 driver</span></span></td>
</tr><tr>
<td> <span data-ttu-id="d6c9d-247">散熱設計功率</span><span class="sxs-lookup"><span data-stu-id="d6c9d-247">Thermal Design Power</span></span></td><td colspan="2"> <span data-ttu-id="d6c9d-248">15W 或更大</span><span class="sxs-lookup"><span data-stu-id="d6c9d-248">15W or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="d6c9d-249">圖形顯示連接埠</span><span class="sxs-lookup"><span data-stu-id="d6c9d-249">Graphics display ports</span></span></td><td colspan="2"> <span data-ttu-id="d6c9d-250">適用於頭戴式裝置的 1x 可用圖形顯示連接埠 (適用於 60Hz 頭戴式裝置的 HDMI 1.4 或 DisplayPort 1.2，適用於 90Hz 頭戴式裝置的 HDMI 2.0 或 DisplayPort 1.2)</span><span class="sxs-lookup"><span data-stu-id="d6c9d-250">1x available graphics display port for&#160;headset (HDMI 1.4 or DisplayPort 1.2 for 60Hz headsets, HDMI 2.0 or DisplayPort 1.2 for 90Hz headsets)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="d6c9d-251">顯示器解析度</span><span class="sxs-lookup"><span data-stu-id="d6c9d-251">Display resolution</span></span></td><td colspan="2"> <span data-ttu-id="d6c9d-252">解決方法：SVGA (800 x 600) 或更大的位元深度：每像素 32 位元的色彩</span><span class="sxs-lookup"><span data-stu-id="d6c9d-252">Resolution: SVGA (800x600) or greater Bit depth: 32 bits of color per pixel</span></span></td>
</tr><tr>
<td> <span data-ttu-id="d6c9d-253">Memory</span><span class="sxs-lookup"><span data-stu-id="d6c9d-253">Memory</span></span></td><td> <span data-ttu-id="d6c9d-254">8&#160;GB RAM 或更大</span><span class="sxs-lookup"><span data-stu-id="d6c9d-254">8&#160;GB of RAM or greater</span></span></td><td> <span data-ttu-id="d6c9d-255">16 GB RAM 或更大</span><span class="sxs-lookup"><span data-stu-id="d6c9d-255">16 GB of RAM or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="d6c9d-256">存放裝置</span><span class="sxs-lookup"><span data-stu-id="d6c9d-256">Storage</span></span></td><td colspan="2"> <span data-ttu-id="d6c9d-257">&gt;10 GB 額外可用空間</span><span class="sxs-lookup"><span data-stu-id="d6c9d-257">&gt;10 GB additional free space</span></span></td>
</tr><tr>
<td> <span data-ttu-id="d6c9d-258">USB 連接埠</span><span class="sxs-lookup"><span data-stu-id="d6c9d-258">USB Ports</span></span></td><td colspan="2"> <span data-ttu-id="d6c9d-259">適用於頭戴式裝置的 1x 可用 USB 連接埠 (USB 3.0 Type-A) <b>注意：USB 必須提供至少 900mA</b></span><span class="sxs-lookup"><span data-stu-id="d6c9d-259">1x available USB port for headset (USB 3.0 Type-A) <b>Note: USB must supply a minimum of 900mA</b></span></span></td>
</tr><tr>
<td> <span data-ttu-id="d6c9d-260">Bluetooth</span><span class="sxs-lookup"><span data-stu-id="d6c9d-260">Bluetooth</span></span></td><td colspan="2"> <span data-ttu-id="d6c9d-261">Bluetooth 4.0 (適用於周邊連線)</span><span class="sxs-lookup"><span data-stu-id="d6c9d-261">Bluetooth 4.0 (for accessory connectivity)</span></span></td>
</tr>
</table>

<span data-ttu-id="d6c9d-262">如果您是首次使用 Unreal 進行 MRTK 開發，建議您依循我們策劃的 Unreal 開發旅程：</span><span class="sxs-lookup"><span data-stu-id="d6c9d-262">If you're new to MRTK development with Unreal, we recommend following our curated Unreal development journey:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="d6c9d-263">開始您的 Unreal 旅程</span><span class="sxs-lookup"><span data-stu-id="d6c9d-263">Start your Unreal journey</span></span>](../unreal/unreal-development-overview.md)

## <a name="next-development-checkpoint"></a><span data-ttu-id="d6c9d-264">下一個開發檢查點</span><span class="sxs-lookup"><span data-stu-id="d6c9d-264">Next Development Checkpoint</span></span>

<span data-ttu-id="d6c9d-265">依循我們配置的 Unreal 開發檢查點旅程，您的下一個工作將是進行 HoloLens 2 教學課程系列。</span><span class="sxs-lookup"><span data-stu-id="d6c9d-265">If you're following the Unreal development checkpoint journey we've laid out, your next task is to work through our HoloLens 2 tutorial series.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="d6c9d-266">HoloLens 2 教學課程系列</span><span class="sxs-lookup"><span data-stu-id="d6c9d-266">HoloLens 2 tutorial series</span></span>](../unreal/tutorials/unreal-uxt-ch1.md)

<span data-ttu-id="d6c9d-267">您可以隨時回到 [Unreal 開發檢查點](../unreal/unreal-development-overview.md#1-getting-started)。</span><span class="sxs-lookup"><span data-stu-id="d6c9d-267">You can always go back to the [Unreal development checkpoints](../unreal/unreal-development-overview.md#1-getting-started) at any time.</span></span>

# <a name="native-openxr"></a>[<span data-ttu-id="d6c9d-268">原生 (OpenXR)</span><span class="sxs-lookup"><span data-stu-id="d6c9d-268">Native (OpenXR)</span></span>](#tab/native)

 ![原生應用程式開發](../images/native_logo_banner.png)

<span data-ttu-id="d6c9d-270">原生 OpenXR 開發沒有可供您下載的引擎。</span><span class="sxs-lookup"><span data-stu-id="d6c9d-270">Native OpenXR development doesn't have an engine for you to download.</span></span> <span data-ttu-id="d6c9d-271">您可以在[開始使用 OpenXR](../native/openxr-getting-started.md) 文件中找到開始進行開發所需的一切資訊。</span><span class="sxs-lookup"><span data-stu-id="d6c9d-271">You can find everything you need to begin development in the [Getting started with OpenXR](../native/openxr-getting-started.md) document.</span></span>

### <a name="1-set-up-your-pc-for-mixed-reality-development"></a><span data-ttu-id="d6c9d-272">1.設定您的電腦以便進行混合實境開發</span><span class="sxs-lookup"><span data-stu-id="d6c9d-272">1. Set up your PC for mixed reality development</span></span>

<span data-ttu-id="d6c9d-273">Windows 10 SDK 最適合用於 Windows 10 作業系統。</span><span class="sxs-lookup"><span data-stu-id="d6c9d-273">The Windows 10 SDK works best on the Windows 10 operating system.</span></span> <span data-ttu-id="d6c9d-274">Windows 8.1、Windows 8、Windows 7、Windows Server 2012、Windows Server 2008 R2 也支援此 SDK。</span><span class="sxs-lookup"><span data-stu-id="d6c9d-274">This SDK is also supported on Windows 8.1, Windows 8, Windows 7, Windows Server 2012, Windows Server 2008 R2.</span></span> <span data-ttu-id="d6c9d-275">請注意，舊版作業系統不支援所有工具。</span><span class="sxs-lookup"><span data-stu-id="d6c9d-275">Note that not all tools are supported on older operating systems.</span></span>

#### <a name="for-hololens-development"></a><span data-ttu-id="d6c9d-276">對於 HoloLens 開發</span><span class="sxs-lookup"><span data-stu-id="d6c9d-276">For HoloLens development</span></span>

<span data-ttu-id="d6c9d-277">設定您的開發電腦以便進行 HoloLens 開發時，請確定您符合 <a href="//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a> 的系統需求。</span><span class="sxs-lookup"><span data-stu-id="d6c9d-277">When setting up your development PC for HoloLens development, please make sure you meet the system requirements for <a href="//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a>.</span></span> <span data-ttu-id="d6c9d-278">如果您想要在 HoloLens 裝置上執行您的應用程式，則必須遵循 [Windows 裝置入口網站安裝指示](../platform-capabilities-and-apis/using-the-windows-device-portal.md#setting-up-hololens-to-use-windows-device-portal)。</span><span class="sxs-lookup"><span data-stu-id="d6c9d-278">If you want to run your app on a HoloLens device, you need to follow the [Windows Device Portal setup instructions](../platform-capabilities-and-apis/using-the-windows-device-portal.md#setting-up-hololens-to-use-windows-device-portal).</span></span> <span data-ttu-id="d6c9d-279">如果您打算使用 [HoloLens 模擬器](../platform-capabilities-and-apis/using-the-hololens-emulator.md)，您應確定您的電腦也符合 [HoloLens 模擬器系統需求](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements)。</span><span class="sxs-lookup"><span data-stu-id="d6c9d-279">If you plan on using the [HoloLens emulator](../platform-capabilities-and-apis/using-the-hololens-emulator.md), you'll want to make sure your PC meets the [HoloLens emulator system requirements](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements) as well.</span></span>

<span data-ttu-id="d6c9d-280">如果您打算針對 HoloLens 與 Windows Mixed Reality 沈浸式 (VR) 頭戴裝置進行開發，請使用下一節中的系統建議和需求。</span><span class="sxs-lookup"><span data-stu-id="d6c9d-280">If you plan to develop for both HoloLens and Windows Mixed Reality immersive (VR) headsets, use the system recommendations and requirements in the section below.</span></span>

> [!NOTE]
> <span data-ttu-id="d6c9d-281">您可以針對 HoloLens、VR 沉浸式頭戴裝置或兩者開發及部署應用程式。</span><span class="sxs-lookup"><span data-stu-id="d6c9d-281">You can develop and deploy your apps for HoloLens, VR immersive headsets, or both.</span></span> <span data-ttu-id="d6c9d-282">視您的需求而定，請確定您符合下列需求。</span><span class="sxs-lookup"><span data-stu-id="d6c9d-282">Make sure you fulfill the requirements below depending on your needs.</span></span>

#### <a name="hololens-troubleshooting"></a><span data-ttu-id="d6c9d-283">HoloLens 疑難排解</span><span class="sxs-lookup"><span data-stu-id="d6c9d-283">HoloLens troubleshooting</span></span>

##### <a name="setting-developer-mode-is-grayed-out"></a><span data-ttu-id="d6c9d-284">設定開發人員模式呈現灰色</span><span class="sxs-lookup"><span data-stu-id="d6c9d-284">Setting Developer Mode is grayed out</span></span>

<span data-ttu-id="d6c9d-285">如果您在裝置上啟用開發人員模式時遇到問題，您可能不是[裝置擁有者](/hololens/security-adminless-os)。</span><span class="sxs-lookup"><span data-stu-id="d6c9d-285">If you're running into issues enabling Developer Mode on your device you might not be the [device owner](/hololens/security-adminless-os).</span></span> <span data-ttu-id="d6c9d-286">在多使用者模式中，第一個使用裝置的人員就是裝置擁有者，任何後續的使用者都不會擁有啟用 [開發人員模式] 或其他組態變更所需的權限。</span><span class="sxs-lookup"><span data-stu-id="d6c9d-286">In multi-user mode, the person who uses the device first is the device owner - any subsequent users won't have the required permissions to enable Developer Mode or other configuration changes.</span></span> <span data-ttu-id="d6c9d-287">不過，有一個例外狀況，那就是第一個使用者可能不是 Autopilot 環境中的裝置擁有者，這會在 [HoloLens 安全性文件](/hololens/security-adminless-os#device-owner)詳述。</span><span class="sxs-lookup"><span data-stu-id="d6c9d-287">However, there is an exception where the first user may not be the device owner in an Autopilot environment, which is detailed in the [HoloLens security documentation](/hololens/security-adminless-os#device-owner).</span></span>

<span data-ttu-id="d6c9d-288">可能的解決方案包括：</span><span class="sxs-lookup"><span data-stu-id="d6c9d-288">Possible solutions include:</span></span>

* <span data-ttu-id="d6c9d-289">在將裝置傳遞給其他使用者或開發人員之前，讓裝置擁有者開啟開發人員模式</span><span class="sxs-lookup"><span data-stu-id="d6c9d-289">Having the device owner turn Developer Mode on before passing the device to other users or developers</span></span>
* <span data-ttu-id="d6c9d-290">建議您的 IT/MDM 管理員針對特定裝置或開發人員裝置群組啟用 CSP [Policy ApplicationManagement/AllowDeveloperUnlock](/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock)。</span><span class="sxs-lookup"><span data-stu-id="d6c9d-290">Suggesting that your IT/MDM Admin enables CSP [Policy ApplicationManagement/AllowDeveloperUnlock](/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock) for the specific device or a developer device group.</span></span> 
    * <span data-ttu-id="d6c9d-291">此原則可經由[佈建套件](/hololens/hololens-provisioning)或透過 [HoloLens 裝置的 MDM](/hololens/hololens-mdm-configure) 來設定</span><span class="sxs-lookup"><span data-stu-id="d6c9d-291">This policy can be set by [Provisioning Packages](/hololens/hololens-provisioning) or via [MDM for HoloLens devices](/hololens/hololens-mdm-configure)</span></span>
* <span data-ttu-id="d6c9d-292">使用 [Advanced Recovery Companion (ARC)](/hololens/hololens-recovery)</span><span class="sxs-lookup"><span data-stu-id="d6c9d-292">Using the [Advanced Recovery Companion (ARC)](/hololens/hololens-recovery)</span></span>

> [!NOTE]
> <span data-ttu-id="d6c9d-293">您可以在 **[HoloLens 裝置管理](/hololens/hololens-csp-policy-overview)** 概觀中深入了解裝置管理。</span><span class="sxs-lookup"><span data-stu-id="d6c9d-293">You can learn more about device management in the **[HoloLens device management](/hololens/hololens-csp-policy-overview)** overview.</span></span>

#### <a name="immersive-vr-headset-requirements"></a><span data-ttu-id="d6c9d-294">沈浸式 (VR) 頭戴式裝置需求</span><span class="sxs-lookup"><span data-stu-id="d6c9d-294">Immersive (VR) headset requirements</span></span>

>[!NOTE]
><span data-ttu-id="d6c9d-295">下列指導方針是沈浸式 (VR) 頭戴裝置「開發電腦」目前的最低建議規格，而且會定期更新。</span><span class="sxs-lookup"><span data-stu-id="d6c9d-295">The following guidelines are the current minimum and recommended specs for your immersive (VR) headset *development PC*, and are updated regularly.</span></span>

>[!WARNING]
><span data-ttu-id="d6c9d-296">請勿將此指導方針與[最低電腦硬體相容性指導方針](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)混淆，其中概述了沈浸式 (VR) 頭戴裝置應用程式或遊戲應該定向的「取用者電腦規格」。</span><span class="sxs-lookup"><span data-stu-id="d6c9d-296">Do not confuse this with the [minimum PC hardware compatibility guidelines](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines), which outlines the *consumer PC specs* to which you should target your immersive (VR) headset app or game.</span></span>

<span data-ttu-id="d6c9d-297">如果沉浸式頭戴裝置開發電腦沒有完整大小的 HDMI 和/或 USB 3.0 連接埠，您需要[配接器](/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs)才能連線頭戴式裝置。</span><span class="sxs-lookup"><span data-stu-id="d6c9d-297">If your immersive headset development PC does not have full-sized HDMI and/or USB 3.0 ports, you'll need [adapters](/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs) to connect your headset.</span></span>

<span data-ttu-id="d6c9d-298">目前某些硬體設定有[已知問題](/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)，尤其是具有混合式圖形的筆記型電腦。</span><span class="sxs-lookup"><span data-stu-id="d6c9d-298">There are currently [known issues](/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality) with some hardware configurations, particularly notebooks that have hybrid graphics.</span></span>

<table>
<tr>
<th></th><th> <span data-ttu-id="d6c9d-299">最低需求</span><span class="sxs-lookup"><span data-stu-id="d6c9d-299">Minimum</span></span></th><th> <span data-ttu-id="d6c9d-300">建議</span><span class="sxs-lookup"><span data-stu-id="d6c9d-300">Recommended</span></span></th>
</tr><tr>
<td> <span data-ttu-id="d6c9d-301">處理器</span><span class="sxs-lookup"><span data-stu-id="d6c9d-301">Processor</span></span></td><td> <span data-ttu-id="d6c9d-302"><b>筆記型電腦：</b>Intel Mobile Core i5 第 7 代 CPU、採用超執行緒技術的雙核心 <b>傳統型：</b>Intel Desktop i5 第 6 代 CPU、採用超執行緒技術的雙核心<b>或</b> AMD FX4350 4.2Ghz 四核心對等項目</span><span class="sxs-lookup"><span data-stu-id="d6c9d-302"><b>Notebook:</b> Intel Mobile Core i5 7th generation CPU, Dual-Core with Hyper Threading <b>Desktop:</b> Intel Desktop i5 6th generation CPU, Dual-Core with Hyper Threading <b>OR</b> AMD FX4350 4.2Ghz Quad-Core equivalent</span></span></td><td> <span data-ttu-id="d6c9d-303"><b>傳統型：</b>Intel Desktop i7 第 6 代 (6 核心) <b>或</b> AMD Ryzen 5 1600 (6 核心，12 個執行緒)</span><span class="sxs-lookup"><span data-stu-id="d6c9d-303"><b>Desktop:</b> Intel Desktop i7 6th generation (6 Core) <b>OR</b> AMD Ryzen 5 1600 (6 Core, 12 threads)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="d6c9d-304">GPU</span><span class="sxs-lookup"><span data-stu-id="d6c9d-304">GPU</span></span></td><td> <span data-ttu-id="d6c9d-305"><b>筆記型電腦：</b>NVIDIA GTX 965M、AMD RX 460M (2GB) 對等項目或更高的 DX12 支援 GPU <b>傳統型：</b>NVIDIA GTX 960/1050、AMD Radeon RX 460 (2GB) 對等項目或更高的 DX12 支援 GPU</span><span class="sxs-lookup"><span data-stu-id="d6c9d-305"><b>Notebook:</b> NVIDIA GTX 965M, AMD RX 460M (2GB) equivalent or greater DX12 capable GPU <b>Desktop:</b> NVIDIA GTX 960/1050, AMD Radeon RX 460 (2GB) equivalent or greater DX12 capable GPU</span></span></td><td><span data-ttu-id="d6c9d-306"><b>傳統型：</b>NVIDIA GTX 980/1060、AMD Radeon RX 480 (2GB) 對等項目或更高的 DX12 支援 GPU</span><span class="sxs-lookup"><span data-stu-id="d6c9d-306"><b>Desktop:</b> NVIDIA GTX 980/1060, AMD Radeon RX 480 (2GB) equivalent or greater DX12 capable GPU</span></span></td>
</tr><tr>
<td> <span data-ttu-id="d6c9d-307">GPU 驅動程式 WDDM 版本</span><span class="sxs-lookup"><span data-stu-id="d6c9d-307">GPU driver WDDM version</span></span></td><td colspan="2"> <span data-ttu-id="d6c9d-308">WDDM 2.2 驅動程式</span><span class="sxs-lookup"><span data-stu-id="d6c9d-308">WDDM 2.2 driver</span></span></td>
</tr><tr>
<td> <span data-ttu-id="d6c9d-309">散熱設計功率</span><span class="sxs-lookup"><span data-stu-id="d6c9d-309">Thermal Design Power</span></span></td><td colspan="2"> <span data-ttu-id="d6c9d-310">15W 或更大</span><span class="sxs-lookup"><span data-stu-id="d6c9d-310">15W or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="d6c9d-311">圖形顯示連接埠</span><span class="sxs-lookup"><span data-stu-id="d6c9d-311">Graphics display ports</span></span></td><td colspan="2"> <span data-ttu-id="d6c9d-312">適用於頭戴式裝置的 1x 可用圖形顯示連接埠 (適用於 60Hz 頭戴式裝置的 HDMI 1.4 或 DisplayPort 1.2，適用於 90Hz 頭戴式裝置的 HDMI 2.0 或 DisplayPort 1.2)</span><span class="sxs-lookup"><span data-stu-id="d6c9d-312">1x available graphics display port for&#160;headset (HDMI 1.4 or DisplayPort 1.2 for 60Hz headsets, HDMI 2.0 or DisplayPort 1.2 for 90Hz headsets)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="d6c9d-313">顯示器解析度</span><span class="sxs-lookup"><span data-stu-id="d6c9d-313">Display resolution</span></span></td><td colspan="2"> <span data-ttu-id="d6c9d-314">解決方法：SVGA (800 x 600) 或更大的位元深度：每像素 32 位元的色彩</span><span class="sxs-lookup"><span data-stu-id="d6c9d-314">Resolution: SVGA (800x600) or greater Bit depth: 32 bits of color per pixel</span></span></td>
</tr><tr>
<td> <span data-ttu-id="d6c9d-315">Memory</span><span class="sxs-lookup"><span data-stu-id="d6c9d-315">Memory</span></span></td><td> <span data-ttu-id="d6c9d-316">8&#160;GB RAM 或更大</span><span class="sxs-lookup"><span data-stu-id="d6c9d-316">8&#160;GB of RAM or greater</span></span></td><td> <span data-ttu-id="d6c9d-317">16 GB RAM 或更大</span><span class="sxs-lookup"><span data-stu-id="d6c9d-317">16 GB of RAM or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="d6c9d-318">存放裝置</span><span class="sxs-lookup"><span data-stu-id="d6c9d-318">Storage</span></span></td><td colspan="2"> <span data-ttu-id="d6c9d-319">&gt;10 GB 額外可用空間</span><span class="sxs-lookup"><span data-stu-id="d6c9d-319">&gt;10 GB additional free space</span></span></td>
</tr><tr>
<td> <span data-ttu-id="d6c9d-320">USB 連接埠</span><span class="sxs-lookup"><span data-stu-id="d6c9d-320">USB Ports</span></span></td><td colspan="2"> <span data-ttu-id="d6c9d-321">適用於頭戴式裝置的 1x 可用 USB 連接埠 (USB 3.0 Type-A) <b>注意：USB 必須提供至少 900mA</b></span><span class="sxs-lookup"><span data-stu-id="d6c9d-321">1x available USB port for headset (USB 3.0 Type-A) <b>Note: USB must supply a minimum of 900mA</b></span></span></td>
</tr><tr>
<td> <span data-ttu-id="d6c9d-322">Bluetooth</span><span class="sxs-lookup"><span data-stu-id="d6c9d-322">Bluetooth</span></span></td><td colspan="2"> <span data-ttu-id="d6c9d-323">Bluetooth 4.0 (適用於周邊連線)</span><span class="sxs-lookup"><span data-stu-id="d6c9d-323">Bluetooth 4.0 (for accessory connectivity)</span></span></td>
</tr>
</table>

<span data-ttu-id="d6c9d-324">如果您是首次使用 MRTK 進行原生開發，建議您依循我們策劃的原生開發旅程：</span><span class="sxs-lookup"><span data-stu-id="d6c9d-324">If you're new to Native development with MRTK, we recommend following our curated Native development journey:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="d6c9d-325">開始您的原生旅程</span><span class="sxs-lookup"><span data-stu-id="d6c9d-325">Start your Native journey</span></span>](../native/directx-development-overview.md)

## <a name="next-development-checkpoint"></a><span data-ttu-id="d6c9d-326">下一個開發檢查點</span><span class="sxs-lookup"><span data-stu-id="d6c9d-326">Next Development Checkpoint</span></span>

<span data-ttu-id="d6c9d-327">依循我們配置的 Native 開發檢查點旅程，您的下一個工作將是設定 HoloLens 2 的開發環境。</span><span class="sxs-lookup"><span data-stu-id="d6c9d-327">If you're following the Native development checkpoint journey we've laid out, your next task is to configure your development environment for HoloLens 2.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="d6c9d-328">設定 HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="d6c9d-328">Setup for HoloLens 2</span></span>](../native/openxr-getting-started.md#getting-started-with-openxr-for-hololens-2)

<span data-ttu-id="d6c9d-329">您可以隨時回到[原生開發檢查點](../native/directx-development-overview.md#1-getting-started)。</span><span class="sxs-lookup"><span data-stu-id="d6c9d-329">You can always go back to the [Native development checkpoints](../native/directx-development-overview.md#1-getting-started) at any time.</span></span>