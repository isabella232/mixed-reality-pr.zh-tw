---
ms.openlocfilehash: d7e248788d4c4976acbb9ff23177d354894f57dd
ms.sourcegitcommit: 6272d086a2856e8b514a719e1f9e3b78554be5be
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/30/2021
ms.locfileid: "105958329"
---
# <a name="unity"></a>[<span data-ttu-id="0e748-101">Unity</span><span class="sxs-lookup"><span data-stu-id="0e748-101">Unity</span></span>](#tab/unity)

![Unity 標誌橫幅](../images/unity_logo_banner.png)<br>

### <a name="1-download-the-recommended-unity-version"></a><span data-ttu-id="0e748-103">1. 下載建議的 Unity 版本</span><span class="sxs-lookup"><span data-stu-id="0e748-103">1. Download the recommended Unity version</span></span> 

<span data-ttu-id="0e748-104">目前的混合現實開發建議版本是 **Unity 2019.4 LTS (長期支援)**。</span><span class="sxs-lookup"><span data-stu-id="0e748-104">The current recommended version for Mixed Reality development is **Unity 2019.4 LTS (Long Term Support)**.</span></span> <span data-ttu-id="0e748-105">安裝和管理 Unity 的最佳方式是透過 **Unity 中樞**。</span><span class="sxs-lookup"><span data-stu-id="0e748-105">The best way to install and manage Unity is through the **Unity Hub**.</span></span> 

> [!NOTE]
>  <span data-ttu-id="0e748-106">如果您使用 Unity 2020 LTS，混合現實支援可供 HoloLens 2 開發之用。</span><span class="sxs-lookup"><span data-stu-id="0e748-106">If you’re using Unity 2020 LTS, Mixed Reality support is available for HoloLens 2 development.</span></span> <span data-ttu-id="0e748-107">不過，目前有一些已知問題。</span><span class="sxs-lookup"><span data-stu-id="0e748-107">However, there are currently some known issues.</span></span> <span data-ttu-id="0e748-108">這將會在今年稍後成為建議的 Unity 版本。</span><span class="sxs-lookup"><span data-stu-id="0e748-108">This will become the recommended Unity version later this year.</span></span> 

<span data-ttu-id="0e748-109">請參閱 [選擇 unity 版本和 XR 外掛程式](../unity/choosing-unity-version.md) ，以瞭解有哪些混合現實支援可在不同的 Unity 引擎和 XR 外掛程式版本中使用。</span><span class="sxs-lookup"><span data-stu-id="0e748-109">See [Choosing a Unity version and XR plugin](../unity/choosing-unity-version.md) to learn what Mixed Reality support is available in different Unity engine and XR plugin versions.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="0e748-110">下載 Unity 中樞</span><span class="sxs-lookup"><span data-stu-id="0e748-110">Download Unity Hub</span></span>](https://unity3d.com/get-unity/download)

<span data-ttu-id="0e748-111">安裝 Unity 時，請務必檢查「 **平臺**」底下的下列元件。</span><span class="sxs-lookup"><span data-stu-id="0e748-111">When installing Unity, please make sure to check following components under **'Platforms'**.</span></span>
* <span data-ttu-id="0e748-112">**通用 Windows 平臺組建支援**</span><span class="sxs-lookup"><span data-stu-id="0e748-112">**Universal Windows Platform Build Support**</span></span> 
* <span data-ttu-id="0e748-113">**Windows Build 支援 (IL2CPP)**</span><span class="sxs-lookup"><span data-stu-id="0e748-113">**Windows Build Support (IL2CPP)**</span></span>

![Unity 通用 Windows 平臺組建支援選項](../../develop/images/Unity_Install_Option_UWP.png)

<span data-ttu-id="0e748-115">如果您已安裝 Unity 但未安裝這些選項，您可以透過 Unity Hub 中 **的 [新增模組** ] 功能表來新增這些選項。</span><span class="sxs-lookup"><span data-stu-id="0e748-115">If you installed Unity without these options, you can add them through **'Add Modules'** menu in Unity Hub.</span></span>

![Unity Windows Build 支援選項](../../develop/images/Unity_Install_Option_UWP2.png)


### <a name="2-install-the-mixed-reality-feature-tool"></a><span data-ttu-id="0e748-117">2. 安裝 Mixed Reality 功能工具</span><span class="sxs-lookup"><span data-stu-id="0e748-117">2. Install the Mixed Reality Feature Tool</span></span>

<span data-ttu-id="0e748-118">「 [混合現實」功能工具](../unity/welcome-to-mr-feature-tool.md) 是一種新的方法，讓開發人員可以探索並將混合現實功能套件新增至 Unity 專案。</span><span class="sxs-lookup"><span data-stu-id="0e748-118">The [Mixed Reality Feature Tool](../unity/welcome-to-mr-feature-tool.md) is a new way for developers to discover and add Mixed Reality feature packages into Unity projects.</span></span> 

<span data-ttu-id="0e748-119">您可以依名稱或類別搜尋套件、查看其相依性，甚至在匯入之前查看專案資訊清單檔的建議變更。</span><span class="sxs-lookup"><span data-stu-id="0e748-119">You can search packages by name or category, see their dependencies, and even view proposed changes to your projects manifest file before importing.</span></span> <span data-ttu-id="0e748-120">驗證您想要的封裝之後，混合現實功能工具會將這些套件下載到您選擇的專案。</span><span class="sxs-lookup"><span data-stu-id="0e748-120">Once you've validated the packages you want, the Mixed Reality Feature tool will download them into the project of your choice.</span></span>

#### <a name="importing-the-mixed-reality-toolkit"></a><span data-ttu-id="0e748-121">匯入混合實境工具組</span><span class="sxs-lookup"><span data-stu-id="0e748-121">Importing the Mixed Reality Toolkit</span></span>

![MRTK](../../design/images/MRTK_UX_Hero.png)

<span data-ttu-id="0e748-123">[混合實境工具組](../unity/mrtk-getting-started.md) (MRTK) 是混合實境應用程式的開放原始碼跨平台開發套件。</span><span class="sxs-lookup"><span data-stu-id="0e748-123">[Mixed Reality Toolkit](../unity/mrtk-getting-started.md) (MRTK) is an open-source, cross-platform development kit for mixed reality applications.</span></span> 

* <span data-ttu-id="0e748-124">遵循 [安裝和使用方式指示](../unity/welcome-to-mr-feature-tool.md#system-requirements) ，並選取 **混合現實工具組基礎** 套件，以安裝混合現實工具組套件。</span><span class="sxs-lookup"><span data-stu-id="0e748-124">Install the Mixed Reality Toolkit package by following the [installation and usage instructions](../unity/welcome-to-mr-feature-tool.md#system-requirements) and selecting the **Mixed Reality Toolkit Foundation** package.</span></span>

<span data-ttu-id="0e748-125">建議您在策劃 [HoloLens](../unity/unity-development-overview.md#1-getting-started) 或 [VR](../unity/unity-development-wmr-overview.md#1-getting-started) 開發旅程中完成「開始使用」一節。</span><span class="sxs-lookup"><span data-stu-id="0e748-125">We recommend completing the getting started section in our curated [HoloLens](../unity/unity-development-overview.md#1-getting-started) or [VR](../unity/unity-development-wmr-overview.md#1-getting-started) development journeys.</span></span> <span data-ttu-id="0e748-126">依循適用於 HoloLens 的 Unity 開發旅程，接下來請完成下列其餘的設定步驟，並繼續進行 [HoloLens 2 開始使用教學課程](../unity/tutorials/mr-learning-base-01.md)。</span><span class="sxs-lookup"><span data-stu-id="0e748-126">If you're already following the Unity development for HoloLens journey, finish up the rest of the setup steps listed below and continue on to the [HoloLens 2 Getting Started tutorials](../unity/tutorials/mr-learning-base-01.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0e748-127">請注意，安裝指示的目標是 MRTK 和 Unity 版本的最新穩定組合，也就是 **MRTK 2.6.1** 和 **unity 2019.4 LTS**。</span><span class="sxs-lookup"><span data-stu-id="0e748-127">Note that installation instructions are targeted for the latest stable combination of MRTK and Unity releases, which are **MRTK 2.6.1** and **Unity 2019.4 LTS**.</span></span>

> [!NOTE]
> <span data-ttu-id="0e748-128">如果您不想要使用適用于 Unity 的 MRTK，您必須 [自行編寫所有互動和行為的腳本](../unity/configure-unity-project.md)。</span><span class="sxs-lookup"><span data-stu-id="0e748-128">If you don't want to use MRTK for Unity, you'll need to [script all interactions and behaviors yourself](../unity/configure-unity-project.md).</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="0e748-129"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">![Unity 橫幅](../images/MRTK-Unity-Banner.png)</span><span class="sxs-lookup"><span data-stu-id="0e748-129"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">![Unity banner](../images/MRTK-Unity-Banner.png)</span></span><br><span data-ttu-id="0e748-130">**混合實境工具組-Unity (GitHub)** </a></span><span class="sxs-lookup"><span data-stu-id="0e748-130">**Mixed Reality Toolkit-Unity (GitHub)**</a></span></span><br>
    :::column-end:::
:::row-end:::

#### <a name="other-tools-optional"></a><span data-ttu-id="0e748-131">其他工具 [選用]</span><span class="sxs-lookup"><span data-stu-id="0e748-131">Other tools [optional]</span></span>
* <span data-ttu-id="0e748-132"><a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">混合實境配套工具組 (GitHub)</a> - 無法直接在 HoloLens 或沈浸式 (VR) 頭戴裝置上執行的程式碼位元和元件，但是將其搭配使用可打造以 Windows Mixed Reality 為目標的體驗。</span><span class="sxs-lookup"><span data-stu-id="0e748-132"><a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">Mixed Reality Companion Kit (GitHub)</a> - code bits and components that might not run directly on HoloLens or immersive (VR) headsets, but instead pair with them to build experiences targeting Windows Mixed Reality.</span></span>
* <span data-ttu-id="0e748-133"><a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">混合的現實工具組 - 通用 (GitHub)</a> - 共用指令碼和元件的集合。</span><span class="sxs-lookup"><span data-stu-id="0e748-133"><a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">Mixed Reality Toolkit - Common (GitHub)</a> - a collection of shared scripts and components.</span></span>

### <a name="3-set-up-your-pc-for-mixed-reality-development"></a><span data-ttu-id="0e748-134">3.設定您的電腦以便進行混合實境開發</span><span class="sxs-lookup"><span data-stu-id="0e748-134">3. Set up your PC for Mixed Reality development</span></span>

<span data-ttu-id="0e748-135">Windows 10 SDK 最適合用於 Windows 10 作業系統。</span><span class="sxs-lookup"><span data-stu-id="0e748-135">The Windows 10 SDK works best on the Windows 10 operating system.</span></span> <span data-ttu-id="0e748-136">Windows 8.1、Windows 8、Windows 7、Windows Server 2012、Windows Server 2008 R2 也支援此 SDK。</span><span class="sxs-lookup"><span data-stu-id="0e748-136">This SDK is also supported on Windows 8.1, Windows 8, Windows 7, Windows Server 2012, Windows Server 2008 R2.</span></span> <span data-ttu-id="0e748-137">請注意，舊版作業系統不支援所有工具。</span><span class="sxs-lookup"><span data-stu-id="0e748-137">Note that not all tools are supported on older operating systems.</span></span>

> [!NOTE]
> <span data-ttu-id="0e748-138">您可以針對 HoloLens、VR 沉浸式頭戴裝置或兩者開發及部署應用程式。</span><span class="sxs-lookup"><span data-stu-id="0e748-138">You can develop and deploy your apps for HoloLens, VR immersive headsets, or both.</span></span> <span data-ttu-id="0e748-139">視您的需求而定，請確定您符合下列需求。</span><span class="sxs-lookup"><span data-stu-id="0e748-139">Make sure you fulfill the requirements below depending on your needs.</span></span>

#### <a name="for-hololens-development"></a><span data-ttu-id="0e748-140">對於 HoloLens 開發</span><span class="sxs-lookup"><span data-stu-id="0e748-140">For HoloLens development</span></span>

<span data-ttu-id="0e748-141">設定您的開發電腦以便進行 HoloLens 開發時，請確定其同時符合 <a href="https://unity3d.com/unity/system-requirements" target="_blank">Unity</a> 和 <a href="//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a> 的系統需求。</span><span class="sxs-lookup"><span data-stu-id="0e748-141">When setting up your development PC for HoloLens development, please make sure it meets the system requirements for both <a href="https://unity3d.com/unity/system-requirements" target="_blank">Unity</a> and <a href="//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a>.</span></span> <span data-ttu-id="0e748-142">如果您想要在 HoloLens 裝置上執行您的應用程式，則必須遵循 [Windows 裝置入口網站安裝指示](../platform-capabilities-and-apis/using-the-windows-device-portal.md#setting-up-hololens-to-use-windows-device-portal)。</span><span class="sxs-lookup"><span data-stu-id="0e748-142">If you want to run your app on a HoloLens device, you need to follow the [Windows Device Portal setup instructions](../platform-capabilities-and-apis/using-the-windows-device-portal.md#setting-up-hololens-to-use-windows-device-portal).</span></span> <span data-ttu-id="0e748-143">如果您打算使用 [HoloLens 模擬器](../platform-capabilities-and-apis/using-the-hololens-emulator.md)，您應確定您的電腦也符合 [HoloLens 模擬器系統需求](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements)。</span><span class="sxs-lookup"><span data-stu-id="0e748-143">If you plan on using the [HoloLens emulator](../platform-capabilities-and-apis/using-the-hololens-emulator.md), you'll want to make sure your PC meets the [HoloLens emulator system requirements](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements) as well.</span></span>

<span data-ttu-id="0e748-144">若要開始使用 HoloLens 模擬器，請參閱[使用 HoloLens 模擬器](../platform-capabilities-and-apis/using-the-hololens-emulator.md)。</span><span class="sxs-lookup"><span data-stu-id="0e748-144">To get started with the HoloLens emulator, see [Using the HoloLens emulator](../platform-capabilities-and-apis/using-the-hololens-emulator.md).</span></span>

<span data-ttu-id="0e748-145">如果您打算針對 HoloLens 與 Windows Mixed Reality 沈浸式 (VR) 頭戴裝置進行開發，請使用下一節中的系統建議和需求。</span><span class="sxs-lookup"><span data-stu-id="0e748-145">If you plan to develop for both HoloLens and Windows Mixed Reality immersive (VR) headsets, use the system recommendations and requirements in the section below.</span></span>

#### <a name="hololens-troubleshooting"></a><span data-ttu-id="0e748-146">HoloLens 疑難排解</span><span class="sxs-lookup"><span data-stu-id="0e748-146">HoloLens troubleshooting</span></span>

##### <a name="setting-developer-mode-is-grayed-out"></a><span data-ttu-id="0e748-147">設定開發人員模式呈現灰色</span><span class="sxs-lookup"><span data-stu-id="0e748-147">Setting Developer Mode is grayed out</span></span>

<span data-ttu-id="0e748-148">如果您在裝置上啟用開發人員模式時遇到問題，您可能不是[裝置擁有者](/hololens/security-adminless-os)。</span><span class="sxs-lookup"><span data-stu-id="0e748-148">If you're running into issues enabling Developer Mode on your device you might not be the [device owner](/hololens/security-adminless-os).</span></span> <span data-ttu-id="0e748-149">在多使用者模式中，第一個使用裝置的人員就是裝置擁有者，任何後續的使用者都不會擁有啟用 [開發人員模式] 或其他組態變更所需的權限。</span><span class="sxs-lookup"><span data-stu-id="0e748-149">In multi-user mode, the person who uses the device first is the device owner - any subsequent users won't have the required permissions to enable Developer Mode or other configuration changes.</span></span> <span data-ttu-id="0e748-150">不過，有一個例外狀況，那就是第一個使用者可能不是 Autopilot 環境中的裝置擁有者，這會在 [HoloLens 安全性文件](/hololens/security-adminless-os#device-owner)詳述。</span><span class="sxs-lookup"><span data-stu-id="0e748-150">However, there is an exception where the first user may not be the device owner in an Autopilot environment, which is detailed in the [HoloLens security documentation](/hololens/security-adminless-os#device-owner).</span></span>

<span data-ttu-id="0e748-151">可能的解決方案包括：</span><span class="sxs-lookup"><span data-stu-id="0e748-151">Possible solutions include:</span></span>

* <span data-ttu-id="0e748-152">在將裝置傳遞給其他使用者或開發人員之前，讓裝置擁有者開啟開發人員模式</span><span class="sxs-lookup"><span data-stu-id="0e748-152">Having the device owner turn Developer Mode on before passing the device to other users or developers</span></span>
* <span data-ttu-id="0e748-153">建議您的 IT/MDM 管理員針對特定裝置或開發人員裝置群組啟用 CSP [Policy ApplicationManagement/AllowDeveloperUnlock](/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock)。</span><span class="sxs-lookup"><span data-stu-id="0e748-153">Suggesting that your IT/MDM Admin enables CSP [Policy ApplicationManagement/AllowDeveloperUnlock](/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock) for the specific device or a developer device group.</span></span> 
    * <span data-ttu-id="0e748-154">此原則可經由[佈建套件](/hololens/hololens-provisioning)或透過 [HoloLens 裝置的 MDM](/hololens/hololens-mdm-configure) 來設定</span><span class="sxs-lookup"><span data-stu-id="0e748-154">This policy can be set by [Provisioning Packages](/hololens/hololens-provisioning) or via [MDM for HoloLens devices](/hololens/hololens-mdm-configure)</span></span>
* <span data-ttu-id="0e748-155">使用 [Advanced Recovery Companion (ARC)](/hololens/hololens-recovery)</span><span class="sxs-lookup"><span data-stu-id="0e748-155">Using the [Advanced Recovery Companion (ARC)](/hololens/hololens-recovery)</span></span>

> [!NOTE]
> <span data-ttu-id="0e748-156">您可以在 **[HoloLens 裝置管理](/hololens/hololens-csp-policy-overview)** 概觀中深入了解裝置管理。</span><span class="sxs-lookup"><span data-stu-id="0e748-156">You can learn more about device management in the **[HoloLens device management](/hololens/hololens-csp-policy-overview)** overview.</span></span>

##### <a name="i-cant-deploy-over-usb"></a><span data-ttu-id="0e748-157">我無法透過 USB 部署</span><span class="sxs-lookup"><span data-stu-id="0e748-157">I can't deploy over USB</span></span>

<span data-ttu-id="0e748-158">如果您無法直接透過 USB 部署應用程式，請確定您符合上述所有的安裝需求，並遵循我們的[逐步教學課程](../unity/tutorials/mr-learning-base-02.md#building-your-application-to-your-hololens-2)。</span><span class="sxs-lookup"><span data-stu-id="0e748-158">If you're not able to deploy an application directly over USB, make sure you've met all the installation requirements listed above and follow our [step-by-step tutorial](../unity/tutorials/mr-learning-base-02.md#building-your-application-to-your-hololens-2).</span></span>

#### <a name="immersive-vr-headset-requirements"></a><span data-ttu-id="0e748-159">沈浸式 (VR) 頭戴式裝置需求</span><span class="sxs-lookup"><span data-stu-id="0e748-159">Immersive (VR) headset requirements</span></span>

>[!NOTE]
><span data-ttu-id="0e748-160">下列指導方針是沈浸式 (VR) 頭戴裝置「開發電腦」目前的最低建議規格，而且會定期更新。</span><span class="sxs-lookup"><span data-stu-id="0e748-160">The following guidelines are the current minimum and recommended specs for your immersive (VR) headset *development PC*, and are updated regularly.</span></span>

>[!WARNING]
><span data-ttu-id="0e748-161">請勿將此指導方針與[最低電腦硬體相容性指導方針](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)混淆，其中概述了沈浸式 (VR) 頭戴裝置應用程式或遊戲應該定向的「取用者電腦規格」。</span><span class="sxs-lookup"><span data-stu-id="0e748-161">Do not confuse this with the [minimum PC hardware compatibility guidelines](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines), which outlines the *consumer PC specs* to which you should target your immersive (VR) headset app or game.</span></span>

<span data-ttu-id="0e748-162">如果沉浸式頭戴裝置開發電腦沒有完整大小的 HDMI 和/或 USB 3.0 連接埠，您需要[配接器](/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs)才能連線頭戴式裝置。</span><span class="sxs-lookup"><span data-stu-id="0e748-162">If your immersive headset development PC does not have full-sized HDMI and/or USB 3.0 ports, you'll need [adapters](/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs) to connect your headset.</span></span>

<span data-ttu-id="0e748-163">目前某些硬體設定有[已知問題](/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)，尤其是具有混合式圖形的筆記型電腦。</span><span class="sxs-lookup"><span data-stu-id="0e748-163">There are currently [known issues](/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality) with some hardware configurations, particularly notebooks that have hybrid graphics.</span></span>

<table>
<tr>
<th></th><th> <span data-ttu-id="0e748-164">最低需求</span><span class="sxs-lookup"><span data-stu-id="0e748-164">Minimum</span></span></th><th> <span data-ttu-id="0e748-165">建議</span><span class="sxs-lookup"><span data-stu-id="0e748-165">Recommended</span></span></th>
</tr><tr>
<td> <span data-ttu-id="0e748-166">處理器</span><span class="sxs-lookup"><span data-stu-id="0e748-166">Processor</span></span></td><td> <span data-ttu-id="0e748-167"><b>筆記型電腦：</b>Intel Mobile Core i5 第 7 代 CPU、採用超執行緒技術的雙核心 <b>傳統型：</b>Intel Desktop i5 第 6 代 CPU、採用超執行緒技術的雙核心<b>或</b> AMD FX4350 4.2Ghz 四核心對等項目</span><span class="sxs-lookup"><span data-stu-id="0e748-167"><b>Notebook:</b> Intel Mobile Core i5 7th generation CPU, Dual-Core with Hyper Threading <b>Desktop:</b> Intel Desktop i5 6th generation CPU, Dual-Core with Hyper Threading <b>OR</b> AMD FX4350 4.2Ghz Quad-Core equivalent</span></span></td><td> <span data-ttu-id="0e748-168"><b>傳統型：</b>Intel Desktop i7 第 6 代 (6 核心) <b>或</b> AMD Ryzen 5 1600 (6 核心，12 個執行緒)</span><span class="sxs-lookup"><span data-stu-id="0e748-168"><b>Desktop:</b> Intel Desktop i7 6th generation (6 Core) <b>OR</b> AMD Ryzen 5 1600 (6 Core, 12 threads)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="0e748-169">GPU</span><span class="sxs-lookup"><span data-stu-id="0e748-169">GPU</span></span></td><td> <span data-ttu-id="0e748-170"><b>筆記型電腦：</b>NVIDIA GTX 965M、AMD RX 460M (2GB) 對等項目或更高的 DX12 支援 GPU <b>傳統型：</b>NVIDIA GTX 960/1050、AMD Radeon RX 460 (2GB) 對等項目或更高的 DX12 支援 GPU</span><span class="sxs-lookup"><span data-stu-id="0e748-170"><b>Notebook:</b> NVIDIA GTX 965M, AMD RX 460M (2GB) equivalent or greater DX12 capable GPU <b>Desktop:</b> NVIDIA GTX 960/1050, AMD Radeon RX 460 (2GB) equivalent or greater DX12 capable GPU</span></span></td><td><span data-ttu-id="0e748-171"><b>傳統型：</b>NVIDIA GTX 980/1060、AMD Radeon RX 480 (2GB) 對等項目或更高的 DX12 支援 GPU</span><span class="sxs-lookup"><span data-stu-id="0e748-171"><b>Desktop:</b> NVIDIA GTX 980/1060, AMD Radeon RX 480 (2GB) equivalent or greater DX12 capable GPU</span></span></td>
</tr><tr>
<td> <span data-ttu-id="0e748-172">GPU 驅動程式 WDDM 版本</span><span class="sxs-lookup"><span data-stu-id="0e748-172">GPU driver WDDM version</span></span></td><td colspan="2"> <span data-ttu-id="0e748-173">WDDM 2.2 驅動程式</span><span class="sxs-lookup"><span data-stu-id="0e748-173">WDDM 2.2 driver</span></span></td>
</tr><tr>
<td> <span data-ttu-id="0e748-174">散熱設計功率</span><span class="sxs-lookup"><span data-stu-id="0e748-174">Thermal Design Power</span></span></td><td colspan="2"> <span data-ttu-id="0e748-175">15W 或更大</span><span class="sxs-lookup"><span data-stu-id="0e748-175">15W or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="0e748-176">圖形顯示連接埠</span><span class="sxs-lookup"><span data-stu-id="0e748-176">Graphics display ports</span></span></td><td colspan="2"> <span data-ttu-id="0e748-177">適用於頭戴式裝置的 1x 可用圖形顯示連接埠 (適用於 60Hz 頭戴式裝置的 HDMI 1.4 或 DisplayPort 1.2，適用於 90Hz 頭戴式裝置的 HDMI 2.0 或 DisplayPort 1.2)</span><span class="sxs-lookup"><span data-stu-id="0e748-177">1x available graphics display port for&#160;headset (HDMI 1.4 or DisplayPort 1.2 for 60Hz headsets, HDMI 2.0 or DisplayPort 1.2 for 90Hz headsets)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="0e748-178">顯示器解析度</span><span class="sxs-lookup"><span data-stu-id="0e748-178">Display resolution</span></span></td><td colspan="2"> <span data-ttu-id="0e748-179">解決方法：SVGA (800 x 600) 或更大的位元深度：每像素 32 位元的色彩</span><span class="sxs-lookup"><span data-stu-id="0e748-179">Resolution: SVGA (800x600) or greater Bit depth: 32 bits of color per pixel</span></span></td>
</tr><tr>
<td> <span data-ttu-id="0e748-180">Memory</span><span class="sxs-lookup"><span data-stu-id="0e748-180">Memory</span></span></td><td> <span data-ttu-id="0e748-181">8&#160;GB RAM 或更大</span><span class="sxs-lookup"><span data-stu-id="0e748-181">8&#160;GB of RAM or greater</span></span></td><td> <span data-ttu-id="0e748-182">16 GB RAM 或更大</span><span class="sxs-lookup"><span data-stu-id="0e748-182">16 GB of RAM or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="0e748-183">存放裝置</span><span class="sxs-lookup"><span data-stu-id="0e748-183">Storage</span></span></td><td colspan="2"> <span data-ttu-id="0e748-184">&gt;10 GB 額外可用空間</span><span class="sxs-lookup"><span data-stu-id="0e748-184">&gt;10 GB additional free space</span></span></td>
</tr><tr>
<td> <span data-ttu-id="0e748-185">USB 連接埠</span><span class="sxs-lookup"><span data-stu-id="0e748-185">USB Ports</span></span></td><td colspan="2"> <span data-ttu-id="0e748-186">適用於頭戴式裝置的 1x 可用 USB 連接埠 (USB 3.0 Type-A) <b>注意：USB 必須提供至少 900mA</b></span><span class="sxs-lookup"><span data-stu-id="0e748-186">1x available USB port for headset (USB 3.0 Type-A) <b>Note: USB must supply a minimum of 900mA</b></span></span></td>
</tr><tr>
<td> <span data-ttu-id="0e748-187">Bluetooth</span><span class="sxs-lookup"><span data-stu-id="0e748-187">Bluetooth</span></span></td><td colspan="2"> <span data-ttu-id="0e748-188">Bluetooth 4.0 (適用於周邊連線)</span><span class="sxs-lookup"><span data-stu-id="0e748-188">Bluetooth 4.0 (for accessory connectivity)</span></span></td>
</tr>
</table>

<span data-ttu-id="0e748-189">如果您是首次使用 Unity 進行 MRTK 開發，建議您依循我們策劃的 Unity 開發旅程：</span><span class="sxs-lookup"><span data-stu-id="0e748-189">If you're new to MRTK development with Unity, we recommend following our curated Unity development journey:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="0e748-190">開始您適用於 HoloLens 的 Unity 開發旅程</span><span class="sxs-lookup"><span data-stu-id="0e748-190">Start your Unity for HoloLens journey</span></span>](../unity/unity-development-overview.md)

> [!div class="nextstepaction"]
> [<span data-ttu-id="0e748-191">開始您適用於 VR 的 Unity 開發旅程</span><span class="sxs-lookup"><span data-stu-id="0e748-191">Start your Unity for VR journey</span></span>](../unity/unity-development-wmr-overview.md)

## <a name="next-development-checkpoint"></a><span data-ttu-id="0e748-192">下一個開發檢查點</span><span class="sxs-lookup"><span data-stu-id="0e748-192">Next Development Checkpoint</span></span>

<span data-ttu-id="0e748-193">依循我們所配置適用於 HoloLens 的 Unity 開發檢查點旅程，您的下一個工作將是進行 HoloLens 2 教學課程系列。</span><span class="sxs-lookup"><span data-stu-id="0e748-193">If you're following the Unity for HoloLens development checkpoint journey we've laid out, your next task is to work through our HoloLens 2 tutorial series.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="0e748-194">HoloLens 2 教學課程系列</span><span class="sxs-lookup"><span data-stu-id="0e748-194">HoloLens 2 tutorial series</span></span>](../unity/tutorials/mr-learning-base-01.md)

<span data-ttu-id="0e748-195">如果您要依循適用於 VR 的 Unity 旅程，下一個工作是設定您的專案。</span><span class="sxs-lookup"><span data-stu-id="0e748-195">If you're following the Unity for VR journey, your next task is to setup your project.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="0e748-196">針對 WMR 設定您的專案</span><span class="sxs-lookup"><span data-stu-id="0e748-196">Configuring your project for WMR</span></span>](../unity/configure-unity-project.md)

<span data-ttu-id="0e748-197">您可以隨時回到適用於 [HoloLens](../unity/unity-development-overview.md#1-getting-started) 和 [VR](../unity/unity-development-wmr-overview.md#1-getting-started)的 Unity 開發檢查點。</span><span class="sxs-lookup"><span data-stu-id="0e748-197">You can always go back to the Unity development checkpoints for [HoloLens](../unity/unity-development-overview.md#1-getting-started) and [VR](../unity/unity-development-wmr-overview.md#1-getting-started) at any time.</span></span>

# <a name="unreal"></a>[<span data-ttu-id="0e748-198">Unreal</span><span class="sxs-lookup"><span data-stu-id="0e748-198">Unreal</span></span>](#tab/unreal)

![Unreal](../images/unreal_logo_banner.png)

### <a name="1-download-the-latest-version"></a><span data-ttu-id="0e748-200">1.下載最新版本</span><span class="sxs-lookup"><span data-stu-id="0e748-200">1. Download the latest version</span></span>

<span data-ttu-id="0e748-201">建議您安裝 [Unreal Engine 4.25 版](https://docs.unrealengine.com//GettingStarted/Installation/index.html)或更新版本，以充分利用內建的 HoloLens 支援。</span><span class="sxs-lookup"><span data-stu-id="0e748-201">We recommend installing [Unreal Engine version 4.25](https://docs.unrealengine.com//GettingStarted/Installation/index.html) or later to take full advantage of built-in HoloLens support.</span></span>

<span data-ttu-id="0e748-202">移至長篇遊戲啟動器中的 [ **媒體** 櫃] 索引標籤，選取 [ **啟動** ] 旁的下拉箭號，然後按一下 [ **選項**]。</span><span class="sxs-lookup"><span data-stu-id="0e748-202">Go to the **Library** tab in the Epic Games Launcher, select the dropdown arrow next to **Launch** and click **Options**.</span></span> <span data-ttu-id="0e748-203">在 [目標平台] 中，選取 **HoloLens 2**，然後按一下 [套用]。</span><span class="sxs-lookup"><span data-stu-id="0e748-203">Under **Target Platforms**, select **HoloLens 2** and click **Apply**.</span></span>
<span data-ttu-id="0e748-204">![Unreal 安裝選項 HoloLens 2](../../develop/images/Unreal_Install_Option_HoloLens2.png)</span><span class="sxs-lookup"><span data-stu-id="0e748-204">![Unreal Install Option HoloLens 2](../../develop/images/Unreal_Install_Option_HoloLens2.png)</span></span>

### <a name="2-import-mixed-reality-toolkit-mrtk"></a><span data-ttu-id="0e748-205">2.匯入混合實境工具組 (MRTK)</span><span class="sxs-lookup"><span data-stu-id="0e748-205">2. Import Mixed Reality Toolkit (MRTK)</span></span>
![MRTK](../../design/images/MRTK_UX_Hero.png)

<span data-ttu-id="0e748-207">混合實境工具組 (MRTK) 是混合實境應用程式的開放原始碼跨平台開發套件。</span><span class="sxs-lookup"><span data-stu-id="0e748-207">Mixed Reality Toolkit (MRTK) is an open-source, cross-platform development kit for mixed reality applications.</span></span> <span data-ttu-id="0e748-208">MRTK 提供跨平台輸入系統、基礎元件，以及空間互動的常見基本要素。</span><span class="sxs-lookup"><span data-stu-id="0e748-208">MRTK provides a cross-platform input system, foundational components, and common building blocks for spatial interactions.</span></span> <span data-ttu-id="0e748-209">該工具組主要用於加速開發以 Microsoft HoloLens、Windows Mixed Reality 沈浸式 (VR) 頭戴裝置和 OpenVR 平台為目標的應用程式。</span><span class="sxs-lookup"><span data-stu-id="0e748-209">The toolkit is intended to accelerate the development of applications targeting Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets, and the OpenVR platform.</span></span>

<span data-ttu-id="0e748-210">進行安裝時，建議您完成我們策劃的 [Unreal 開發旅程圖](../unreal/unreal-development-overview.md)的[開始使用一節](../unreal/unreal-development-overview.md#1-getting-started)。</span><span class="sxs-lookup"><span data-stu-id="0e748-210">For installation, we recommend completing the [Getting Started section](../unreal/unreal-development-overview.md#1-getting-started) of our curated [Unreal development journey](../unreal/unreal-development-overview.md).</span></span> <span data-ttu-id="0e748-211">依循 Unreal 開發旅程，接下來請完成下列其餘的設定步驟，並繼續進行 [HoloLens 2 開始使用教學課程](../unreal/tutorials/unreal-uxt-ch1.md)。</span><span class="sxs-lookup"><span data-stu-id="0e748-211">If you're already following the Unreal development journey, finish up the rest of the setup steps listed below and continue on to the [HoloLens 2 Getting Started tutorials](../unreal/tutorials/unreal-uxt-ch1.md).</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="0e748-212"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unreal" target="_blank">![Unity 標誌影像](../images/MRTK-Unreal-Banner.png)</span><span class="sxs-lookup"><span data-stu-id="0e748-212"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unreal" target="_blank">![Unity logo image](../images/MRTK-Unreal-Banner.png)</span></span><br><span data-ttu-id="0e748-213">**混合實境工具組-Unreal (GitHub)** </a></span><span class="sxs-lookup"><span data-stu-id="0e748-213">**Mixed Reality Toolkit-Unreal (GitHub)**</a></span></span><br>
    :::column-end:::
:::row-end:::

> [!NOTE]
> <span data-ttu-id="0e748-214">如果您不想使用適用於 Unreal 的 MRTK，則必須自行撰寫所有互動和行為的指令碼。</span><span class="sxs-lookup"><span data-stu-id="0e748-214">If you don't want to use MRTK for Unreal, you'll need to script all interactions and behaviors yourself.</span></span>

#### <a name="other-tools-optional"></a><span data-ttu-id="0e748-215">其他工具 [選用]</span><span class="sxs-lookup"><span data-stu-id="0e748-215">Other tools [optional]</span></span>
* <span data-ttu-id="0e748-216"><a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">混合實境配套工具組 (GitHub)</a> - 無法直接在 HoloLens 或沈浸式 (VR) 頭戴裝置上執行的程式碼位元和元件，但是將其搭配使用可打造以 Windows Mixed Reality 為目標的體驗。</span><span class="sxs-lookup"><span data-stu-id="0e748-216"><a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">Mixed Reality Companion Kit (GitHub)</a> - code bits and components that might not run directly on HoloLens or immersive (VR) headsets, but instead pair with them to build experiences targeting Windows Mixed Reality.</span></span>
* <span data-ttu-id="0e748-217"><a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">混合的現實工具組 - 通用 (GitHub)</a> - 共用指令碼和元件的集合。</span><span class="sxs-lookup"><span data-stu-id="0e748-217"><a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">Mixed Reality Toolkit - Co mmon (GitHub)</a> - a collection of shared scripts and components.</span></span>

### <a name="3-set-up-your-pc-for-mixed-reality-development"></a><span data-ttu-id="0e748-218">3.設定您的電腦以便進行混合實境開發</span><span class="sxs-lookup"><span data-stu-id="0e748-218">3. Set up your PC for mixed reality development</span></span>

<span data-ttu-id="0e748-219">Windows 10 SDK 最適合用於 Windows 10 作業系統。</span><span class="sxs-lookup"><span data-stu-id="0e748-219">The Windows 10 SDK works best on the Windows 10 operating system.</span></span> <span data-ttu-id="0e748-220">Windows 8.1、Windows 8、Windows 7、Windows Server 2012、Windows Server 2008 R2 也支援此 SDK。</span><span class="sxs-lookup"><span data-stu-id="0e748-220">This SDK is also supported on Windows 8.1, Windows 8, Windows 7, Windows Server 2012, Windows Server 2008 R2.</span></span> <span data-ttu-id="0e748-221">請注意，舊版作業系統不支援所有工具。</span><span class="sxs-lookup"><span data-stu-id="0e748-221">Note that not all tools are supported on older operating systems.</span></span>

> [!NOTE]
> <span data-ttu-id="0e748-222">您可以針對 HoloLens、VR 沉浸式頭戴裝置或兩者開發及部署應用程式。</span><span class="sxs-lookup"><span data-stu-id="0e748-222">You can develop and deploy your apps for HoloLens, VR immersive headsets, or both.</span></span> <span data-ttu-id="0e748-223">視您的需求而定，請確定您符合下列需求。</span><span class="sxs-lookup"><span data-stu-id="0e748-223">Make sure you fulfill the requirements below depending on your needs.</span></span>

#### <a name="for-hololens-development"></a><span data-ttu-id="0e748-224">對於 HoloLens 開發</span><span class="sxs-lookup"><span data-stu-id="0e748-224">For HoloLens development</span></span>

<span data-ttu-id="0e748-225">設定您的開發電腦以便進行 HoloLens 開發時，請確定您符合 [Unity](https://docs.unrealengine.com/GettingStarted/RecommendedSpecifications/index.html) 和 <a href="//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a> 的系統需求。</span><span class="sxs-lookup"><span data-stu-id="0e748-225">When setting up your development PC for HoloLens development, please make sure you meet the system requirements for [Unreal](https://docs.unrealengine.com/GettingStarted/RecommendedSpecifications/index.html) and and <a href="//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a>.</span></span> <span data-ttu-id="0e748-226">如果您想要在 HoloLens 裝置上執行您的應用程式，則必須遵循 [Windows 裝置入口網站安裝指示](../platform-capabilities-and-apis/using-the-windows-device-portal.md#setting-up-hololens-to-use-windows-device-portal)。</span><span class="sxs-lookup"><span data-stu-id="0e748-226">If you want to run your app on a HoloLens device, you need to follow the [Windows Device Portal setup instructions](../platform-capabilities-and-apis/using-the-windows-device-portal.md#setting-up-hololens-to-use-windows-device-portal).</span></span> <span data-ttu-id="0e748-227">如果您打算使用 [HoloLens 模擬器](../platform-capabilities-and-apis/using-the-hololens-emulator.md)，您應確定您的電腦也符合 [HoloLens 模擬器系統需求](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements)。</span><span class="sxs-lookup"><span data-stu-id="0e748-227">If you plan on using the [HoloLens emulator](../platform-capabilities-and-apis/using-the-hololens-emulator.md), you'll want to make sure your PC meets the [HoloLens emulator system requirements](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements) as well.</span></span>

<span data-ttu-id="0e748-228">如果您打算針對 HoloLens 與 Windows Mixed Reality 沈浸式 (VR) 頭戴裝置進行開發，請使用下一節中的系統建議和需求。</span><span class="sxs-lookup"><span data-stu-id="0e748-228">If you plan to develop for both HoloLens and Windows Mixed Reality immersive (VR) headsets, use the system recommendations and requirements in the section below.</span></span>

#### <a name="hololens-troubleshooting"></a><span data-ttu-id="0e748-229">HoloLens 疑難排解</span><span class="sxs-lookup"><span data-stu-id="0e748-229">HoloLens troubleshooting</span></span>

##### <a name="setting-developer-mode-is-grayed-out"></a><span data-ttu-id="0e748-230">設定開發人員模式呈現灰色</span><span class="sxs-lookup"><span data-stu-id="0e748-230">Setting Developer Mode is grayed out</span></span>

<span data-ttu-id="0e748-231">如果您在裝置上啟用開發人員模式時遇到問題，您可能不是[裝置擁有者](/hololens/security-adminless-os)。</span><span class="sxs-lookup"><span data-stu-id="0e748-231">If you're running into issues enabling Developer Mode on your device you might not be the [device owner](/hololens/security-adminless-os).</span></span> <span data-ttu-id="0e748-232">在多使用者模式中，第一個使用裝置的人員就是裝置擁有者，任何後續的使用者都不會擁有啟用 [開發人員模式] 或其他組態變更所需的權限。</span><span class="sxs-lookup"><span data-stu-id="0e748-232">In multi-user mode, the person who uses the device first is the device owner - any subsequent users won't have the required permissions to enable Developer Mode or other configuration changes.</span></span> <span data-ttu-id="0e748-233">不過，有一個例外狀況，那就是第一個使用者可能不是 Autopilot 環境中的裝置擁有者，這會在 [HoloLens 安全性文件](/hololens/security-adminless-os#device-owner)詳述。</span><span class="sxs-lookup"><span data-stu-id="0e748-233">However, there is an exception where the first user may not be the device owner in an Autopilot environment, which is detailed in the [HoloLens security documentation](/hololens/security-adminless-os#device-owner).</span></span>

<span data-ttu-id="0e748-234">可能的解決方案包括：</span><span class="sxs-lookup"><span data-stu-id="0e748-234">Possible solutions include:</span></span>

* <span data-ttu-id="0e748-235">在將裝置傳遞給其他使用者或開發人員之前，讓裝置擁有者開啟開發人員模式</span><span class="sxs-lookup"><span data-stu-id="0e748-235">Having the device owner turn Developer Mode on before passing the device to other users or developers</span></span>
* <span data-ttu-id="0e748-236">建議您的 IT/MDM 管理員針對特定裝置或開發人員裝置群組啟用 CSP [Policy ApplicationManagement/AllowDeveloperUnlock](/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock)。</span><span class="sxs-lookup"><span data-stu-id="0e748-236">Suggesting that your IT/MDM Admin enables CSP [Policy ApplicationManagement/AllowDeveloperUnlock](/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock) for the specific device or a developer device group.</span></span> 
    * <span data-ttu-id="0e748-237">此原則可經由[佈建套件](/hololens/hololens-provisioning)或透過 [HoloLens 裝置的 MDM](/hololens/hololens-mdm-configure) 來設定</span><span class="sxs-lookup"><span data-stu-id="0e748-237">This policy can be set by [Provisioning Packages](/hololens/hololens-provisioning) or via [MDM for HoloLens devices](/hololens/hololens-mdm-configure)</span></span>
* <span data-ttu-id="0e748-238">使用 [Advanced Recovery Companion (ARC)](/hololens/hololens-recovery)</span><span class="sxs-lookup"><span data-stu-id="0e748-238">Using the [Advanced Recovery Companion (ARC)](/hololens/hololens-recovery)</span></span>

> [!NOTE]
> <span data-ttu-id="0e748-239">您可以在 **[HoloLens 裝置管理](/hololens/hololens-csp-policy-overview)** 概觀中深入了解裝置管理。</span><span class="sxs-lookup"><span data-stu-id="0e748-239">You can learn more about device management in the **[HoloLens device management](/hololens/hololens-csp-policy-overview)** overview.</span></span>

##### <a name="i-cant-deploy-over-usb"></a><span data-ttu-id="0e748-240">我無法透過 USB 部署</span><span class="sxs-lookup"><span data-stu-id="0e748-240">I can't deploy over USB</span></span>

<span data-ttu-id="0e748-241">如果您無法直接透過 USB 部署應用程式，請確定您符合上述所有的安裝需求，並遵循我們的[逐步教學課程](../unreal/tutorials/unreal-uxt-ch6.md)。</span><span class="sxs-lookup"><span data-stu-id="0e748-241">If you're not able to deploy an application directly over USB, make sure you've met all the installation requirements listed above and follow our [step-by-step tutorial](../unreal/tutorials/unreal-uxt-ch6.md).</span></span>

#### <a name="immersive-vr-headset-requirements"></a><span data-ttu-id="0e748-242">沈浸式 (VR) 頭戴式裝置需求</span><span class="sxs-lookup"><span data-stu-id="0e748-242">Immersive (VR) headset requirements</span></span>

>[!NOTE]
><span data-ttu-id="0e748-243">下列指導方針是沈浸式 (VR) 頭戴裝置「開發電腦」目前的最低建議規格，而且會定期更新。</span><span class="sxs-lookup"><span data-stu-id="0e748-243">The following guidelines are the current minimum and recommended specs for your immersive (VR) headset *development PC*, and are updated regularly.</span></span>

>[!WARNING]
><span data-ttu-id="0e748-244">請勿將此指導方針與[最低電腦硬體相容性指導方針](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)混淆，其中概述了沈浸式 (VR) 頭戴裝置應用程式或遊戲應該定向的「取用者電腦規格」。</span><span class="sxs-lookup"><span data-stu-id="0e748-244">Do not confuse this with the [minimum PC hardware compatibility guidelines](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines), which outlines the *consumer PC specs* to which you should target your immersive (VR) headset app or game.</span></span>

<span data-ttu-id="0e748-245">如果沉浸式頭戴裝置開發電腦沒有完整大小的 HDMI 和/或 USB 3.0 連接埠，您需要[配接器](/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs)才能連線頭戴式裝置。</span><span class="sxs-lookup"><span data-stu-id="0e748-245">If your immersive headset development PC does not have full-sized HDMI and/or USB 3.0 ports, you'll need [adapters](/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs) to connect your headset.</span></span>

<span data-ttu-id="0e748-246">目前某些硬體設定有[已知問題](/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)，尤其是具有混合式圖形的筆記型電腦。</span><span class="sxs-lookup"><span data-stu-id="0e748-246">There are currently [known issues](/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality) with some hardware configurations, particularly notebooks that have hybrid graphics.</span></span>

<table>
<tr>
<th></th><th> <span data-ttu-id="0e748-247">最低需求</span><span class="sxs-lookup"><span data-stu-id="0e748-247">Minimum</span></span></th><th> <span data-ttu-id="0e748-248">建議</span><span class="sxs-lookup"><span data-stu-id="0e748-248">Recommended</span></span></th>
</tr><tr>
<td> <span data-ttu-id="0e748-249">處理器</span><span class="sxs-lookup"><span data-stu-id="0e748-249">Processor</span></span></td><td> <span data-ttu-id="0e748-250"><b>筆記型電腦：</b>Intel Mobile Core i5 第 7 代 CPU、採用超執行緒技術的雙核心 <b>傳統型：</b>Intel Desktop i5 第 6 代 CPU、採用超執行緒技術的雙核心<b>或</b> AMD FX4350 4.2Ghz 四核心對等項目</span><span class="sxs-lookup"><span data-stu-id="0e748-250"><b>Notebook:</b> Intel Mobile Core i5 7th generation CPU, Dual-Core with Hyper Threading <b>Desktop:</b> Intel Desktop i5 6th generation CPU, Dual-Core with Hyper Threading <b>OR</b> AMD FX4350 4.2Ghz Quad-Core equivalent</span></span></td><td> <span data-ttu-id="0e748-251"><b>傳統型：</b>Intel Desktop i7 第 6 代 (6 核心) <b>或</b> AMD Ryzen 5 1600 (6 核心，12 個執行緒)</span><span class="sxs-lookup"><span data-stu-id="0e748-251"><b>Desktop:</b> Intel Desktop i7 6th generation (6 Core) <b>OR</b> AMD Ryzen 5 1600 (6 Core, 12 threads)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="0e748-252">GPU</span><span class="sxs-lookup"><span data-stu-id="0e748-252">GPU</span></span></td><td> <span data-ttu-id="0e748-253"><b>筆記型電腦：</b>NVIDIA GTX 965M、AMD RX 460M (2GB) 對等項目或更高的 DX12 支援 GPU <b>傳統型：</b>NVIDIA GTX 960/1050、AMD Radeon RX 460 (2GB) 對等項目或更高的 DX12 支援 GPU</span><span class="sxs-lookup"><span data-stu-id="0e748-253"><b>Notebook:</b> NVIDIA GTX 965M, AMD RX 460M (2GB) equivalent or greater DX12 capable GPU <b>Desktop:</b> NVIDIA GTX 960/1050, AMD Radeon RX 460 (2GB) equivalent or greater DX12 capable GPU</span></span></td><td><span data-ttu-id="0e748-254"><b>傳統型：</b>NVIDIA GTX 980/1060、AMD Radeon RX 480 (2GB) 對等項目或更高的 DX12 支援 GPU</span><span class="sxs-lookup"><span data-stu-id="0e748-254"><b>Desktop:</b> NVIDIA GTX 980/1060, AMD Radeon RX 480 (2GB) equivalent or greater DX12 capable GPU</span></span></td>
</tr><tr>
<td> <span data-ttu-id="0e748-255">GPU 驅動程式 WDDM 版本</span><span class="sxs-lookup"><span data-stu-id="0e748-255">GPU driver WDDM version</span></span></td><td colspan="2"> <span data-ttu-id="0e748-256">WDDM 2.2 驅動程式</span><span class="sxs-lookup"><span data-stu-id="0e748-256">WDDM 2.2 driver</span></span></td>
</tr><tr>
<td> <span data-ttu-id="0e748-257">散熱設計功率</span><span class="sxs-lookup"><span data-stu-id="0e748-257">Thermal Design Power</span></span></td><td colspan="2"> <span data-ttu-id="0e748-258">15W 或更大</span><span class="sxs-lookup"><span data-stu-id="0e748-258">15W or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="0e748-259">圖形顯示連接埠</span><span class="sxs-lookup"><span data-stu-id="0e748-259">Graphics display ports</span></span></td><td colspan="2"> <span data-ttu-id="0e748-260">適用於頭戴式裝置的 1x 可用圖形顯示連接埠 (適用於 60Hz 頭戴式裝置的 HDMI 1.4 或 DisplayPort 1.2，適用於 90Hz 頭戴式裝置的 HDMI 2.0 或 DisplayPort 1.2)</span><span class="sxs-lookup"><span data-stu-id="0e748-260">1x available graphics display port for&#160;headset (HDMI 1.4 or DisplayPort 1.2 for 60Hz headsets, HDMI 2.0 or DisplayPort 1.2 for 90Hz headsets)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="0e748-261">顯示器解析度</span><span class="sxs-lookup"><span data-stu-id="0e748-261">Display resolution</span></span></td><td colspan="2"> <span data-ttu-id="0e748-262">解決方法：SVGA (800 x 600) 或更大的位元深度：每像素 32 位元的色彩</span><span class="sxs-lookup"><span data-stu-id="0e748-262">Resolution: SVGA (800x600) or greater Bit depth: 32 bits of color per pixel</span></span></td>
</tr><tr>
<td> <span data-ttu-id="0e748-263">Memory</span><span class="sxs-lookup"><span data-stu-id="0e748-263">Memory</span></span></td><td> <span data-ttu-id="0e748-264">8&#160;GB RAM 或更大</span><span class="sxs-lookup"><span data-stu-id="0e748-264">8&#160;GB of RAM or greater</span></span></td><td> <span data-ttu-id="0e748-265">16 GB RAM 或更大</span><span class="sxs-lookup"><span data-stu-id="0e748-265">16 GB of RAM or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="0e748-266">存放裝置</span><span class="sxs-lookup"><span data-stu-id="0e748-266">Storage</span></span></td><td colspan="2"> <span data-ttu-id="0e748-267">&gt;10 GB 額外可用空間</span><span class="sxs-lookup"><span data-stu-id="0e748-267">&gt;10 GB additional free space</span></span></td>
</tr><tr>
<td> <span data-ttu-id="0e748-268">USB 連接埠</span><span class="sxs-lookup"><span data-stu-id="0e748-268">USB Ports</span></span></td><td colspan="2"> <span data-ttu-id="0e748-269">適用於頭戴式裝置的 1x 可用 USB 連接埠 (USB 3.0 Type-A) <b>注意：USB 必須提供至少 900mA</b></span><span class="sxs-lookup"><span data-stu-id="0e748-269">1x available USB port for headset (USB 3.0 Type-A) <b>Note: USB must supply a minimum of 900mA</b></span></span></td>
</tr><tr>
<td> <span data-ttu-id="0e748-270">Bluetooth</span><span class="sxs-lookup"><span data-stu-id="0e748-270">Bluetooth</span></span></td><td colspan="2"> <span data-ttu-id="0e748-271">Bluetooth 4.0 (適用於周邊連線)</span><span class="sxs-lookup"><span data-stu-id="0e748-271">Bluetooth 4.0 (for accessory connectivity)</span></span></td>
</tr>
</table>

<span data-ttu-id="0e748-272">如果您是首次使用 Unreal 進行 MRTK 開發，建議您依循我們策劃的 Unreal 開發旅程：</span><span class="sxs-lookup"><span data-stu-id="0e748-272">If you're new to MRTK development with Unreal, we recommend following our curated Unreal development journey:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="0e748-273">開始您的 Unreal 旅程</span><span class="sxs-lookup"><span data-stu-id="0e748-273">Start your Unreal journey</span></span>](../unreal/unreal-development-overview.md)

## <a name="next-development-checkpoint"></a><span data-ttu-id="0e748-274">下一個開發檢查點</span><span class="sxs-lookup"><span data-stu-id="0e748-274">Next Development Checkpoint</span></span>

<span data-ttu-id="0e748-275">依循我們配置的 Unreal 開發檢查點旅程，您的下一個工作將是進行 HoloLens 2 教學課程系列。</span><span class="sxs-lookup"><span data-stu-id="0e748-275">If you're following the Unreal development checkpoint journey we've laid out, your next task is to work through our HoloLens 2 tutorial series.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="0e748-276">HoloLens 2 教學課程系列</span><span class="sxs-lookup"><span data-stu-id="0e748-276">HoloLens 2 tutorial series</span></span>](../unreal/tutorials/unreal-uxt-ch1.md)

<span data-ttu-id="0e748-277">您可以隨時回到 [Unreal 開發檢查點](../unreal/unreal-development-overview.md#1-getting-started)。</span><span class="sxs-lookup"><span data-stu-id="0e748-277">You can always go back to the [Unreal development checkpoints](../unreal/unreal-development-overview.md#1-getting-started) at any time.</span></span>

# <a name="native-openxr"></a>[<span data-ttu-id="0e748-278">原生 (OpenXR)</span><span class="sxs-lookup"><span data-stu-id="0e748-278">Native (OpenXR)</span></span>](#tab/native)

 ![原生應用程式開發](../images/native_logo_banner.png)

<span data-ttu-id="0e748-280">原生 OpenXR 開發沒有可供您下載的引擎。</span><span class="sxs-lookup"><span data-stu-id="0e748-280">Native OpenXR development doesn't have an engine for you to download.</span></span> <span data-ttu-id="0e748-281">您可以在[開始使用 OpenXR](../native/openxr-getting-started.md) 文件中找到開始進行開發所需的一切資訊。</span><span class="sxs-lookup"><span data-stu-id="0e748-281">You can find everything you need to begin development in the [Getting started with OpenXR](../native/openxr-getting-started.md) document.</span></span>

### <a name="1-set-up-your-pc-for-mixed-reality-development"></a><span data-ttu-id="0e748-282">1.設定您的電腦以便進行混合實境開發</span><span class="sxs-lookup"><span data-stu-id="0e748-282">1. Set up your PC for mixed reality development</span></span>

<span data-ttu-id="0e748-283">Windows 10 SDK 最適合用於 Windows 10 作業系統。</span><span class="sxs-lookup"><span data-stu-id="0e748-283">The Windows 10 SDK works best on the Windows 10 operating system.</span></span> <span data-ttu-id="0e748-284">Windows 8.1、Windows 8、Windows 7、Windows Server 2012、Windows Server 2008 R2 也支援此 SDK。</span><span class="sxs-lookup"><span data-stu-id="0e748-284">This SDK is also supported on Windows 8.1, Windows 8, Windows 7, Windows Server 2012, Windows Server 2008 R2.</span></span> <span data-ttu-id="0e748-285">請注意，舊版作業系統不支援所有工具。</span><span class="sxs-lookup"><span data-stu-id="0e748-285">Note that not all tools are supported on older operating systems.</span></span>

#### <a name="for-hololens-development"></a><span data-ttu-id="0e748-286">對於 HoloLens 開發</span><span class="sxs-lookup"><span data-stu-id="0e748-286">For HoloLens development</span></span>

<span data-ttu-id="0e748-287">設定您的開發電腦以便進行 HoloLens 開發時，請確定您符合 <a href="//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a> 的系統需求。</span><span class="sxs-lookup"><span data-stu-id="0e748-287">When setting up your development PC for HoloLens development, please make sure you meet the system requirements for <a href="//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a>.</span></span> <span data-ttu-id="0e748-288">如果您想要在 HoloLens 裝置上執行您的應用程式，則必須遵循 [Windows 裝置入口網站安裝指示](../platform-capabilities-and-apis/using-the-windows-device-portal.md#setting-up-hololens-to-use-windows-device-portal)。</span><span class="sxs-lookup"><span data-stu-id="0e748-288">If you want to run your app on a HoloLens device, you need to follow the [Windows Device Portal setup instructions](../platform-capabilities-and-apis/using-the-windows-device-portal.md#setting-up-hololens-to-use-windows-device-portal).</span></span> <span data-ttu-id="0e748-289">如果您打算使用 [HoloLens 模擬器](../platform-capabilities-and-apis/using-the-hololens-emulator.md)，您應確定您的電腦也符合 [HoloLens 模擬器系統需求](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements)。</span><span class="sxs-lookup"><span data-stu-id="0e748-289">If you plan on using the [HoloLens emulator](../platform-capabilities-and-apis/using-the-hololens-emulator.md), you'll want to make sure your PC meets the [HoloLens emulator system requirements](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements) as well.</span></span>

<span data-ttu-id="0e748-290">如果您打算針對 HoloLens 與 Windows Mixed Reality 沈浸式 (VR) 頭戴裝置進行開發，請使用下一節中的系統建議和需求。</span><span class="sxs-lookup"><span data-stu-id="0e748-290">If you plan to develop for both HoloLens and Windows Mixed Reality immersive (VR) headsets, use the system recommendations and requirements in the section below.</span></span>

> [!NOTE]
> <span data-ttu-id="0e748-291">您可以針對 HoloLens、VR 沉浸式頭戴裝置或兩者開發及部署應用程式。</span><span class="sxs-lookup"><span data-stu-id="0e748-291">You can develop and deploy your apps for HoloLens, VR immersive headsets, or both.</span></span> <span data-ttu-id="0e748-292">視您的需求而定，請確定您符合下列需求。</span><span class="sxs-lookup"><span data-stu-id="0e748-292">Make sure you fulfill the requirements below depending on your needs.</span></span>

#### <a name="hololens-troubleshooting"></a><span data-ttu-id="0e748-293">HoloLens 疑難排解</span><span class="sxs-lookup"><span data-stu-id="0e748-293">HoloLens troubleshooting</span></span>

##### <a name="setting-developer-mode-is-grayed-out"></a><span data-ttu-id="0e748-294">設定開發人員模式呈現灰色</span><span class="sxs-lookup"><span data-stu-id="0e748-294">Setting Developer Mode is grayed out</span></span>

<span data-ttu-id="0e748-295">如果您在裝置上啟用開發人員模式時遇到問題，您可能不是[裝置擁有者](/hololens/security-adminless-os)。</span><span class="sxs-lookup"><span data-stu-id="0e748-295">If you're running into issues enabling Developer Mode on your device you might not be the [device owner](/hololens/security-adminless-os).</span></span> <span data-ttu-id="0e748-296">在多使用者模式中，第一個使用裝置的人員就是裝置擁有者，任何後續的使用者都不會擁有啟用 [開發人員模式] 或其他組態變更所需的權限。</span><span class="sxs-lookup"><span data-stu-id="0e748-296">In multi-user mode, the person who uses the device first is the device owner - any subsequent users won't have the required permissions to enable Developer Mode or other configuration changes.</span></span> <span data-ttu-id="0e748-297">不過，有一個例外狀況，那就是第一個使用者可能不是 Autopilot 環境中的裝置擁有者，這會在 [HoloLens 安全性文件](/hololens/security-adminless-os#device-owner)詳述。</span><span class="sxs-lookup"><span data-stu-id="0e748-297">However, there is an exception where the first user may not be the device owner in an Autopilot environment, which is detailed in the [HoloLens security documentation](/hololens/security-adminless-os#device-owner).</span></span>

<span data-ttu-id="0e748-298">可能的解決方案包括：</span><span class="sxs-lookup"><span data-stu-id="0e748-298">Possible solutions include:</span></span>

* <span data-ttu-id="0e748-299">在將裝置傳遞給其他使用者或開發人員之前，讓裝置擁有者開啟開發人員模式</span><span class="sxs-lookup"><span data-stu-id="0e748-299">Having the device owner turn Developer Mode on before passing the device to other users or developers</span></span>
* <span data-ttu-id="0e748-300">建議您的 IT/MDM 管理員針對特定裝置或開發人員裝置群組啟用 CSP [Policy ApplicationManagement/AllowDeveloperUnlock](/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock)。</span><span class="sxs-lookup"><span data-stu-id="0e748-300">Suggesting that your IT/MDM Admin enables CSP [Policy ApplicationManagement/AllowDeveloperUnlock](/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock) for the specific device or a developer device group.</span></span> 
    * <span data-ttu-id="0e748-301">此原則可經由[佈建套件](/hololens/hololens-provisioning)或透過 [HoloLens 裝置的 MDM](/hololens/hololens-mdm-configure) 來設定</span><span class="sxs-lookup"><span data-stu-id="0e748-301">This policy can be set by [Provisioning Packages](/hololens/hololens-provisioning) or via [MDM for HoloLens devices](/hololens/hololens-mdm-configure)</span></span>
* <span data-ttu-id="0e748-302">使用 [Advanced Recovery Companion (ARC)](/hololens/hololens-recovery)</span><span class="sxs-lookup"><span data-stu-id="0e748-302">Using the [Advanced Recovery Companion (ARC)](/hololens/hololens-recovery)</span></span>

> [!NOTE]
> <span data-ttu-id="0e748-303">您可以在 **[HoloLens 裝置管理](/hololens/hololens-csp-policy-overview)** 概觀中深入了解裝置管理。</span><span class="sxs-lookup"><span data-stu-id="0e748-303">You can learn more about device management in the **[HoloLens device management](/hololens/hololens-csp-policy-overview)** overview.</span></span>

#### <a name="immersive-vr-headset-requirements"></a><span data-ttu-id="0e748-304">沈浸式 (VR) 頭戴式裝置需求</span><span class="sxs-lookup"><span data-stu-id="0e748-304">Immersive (VR) headset requirements</span></span>

>[!NOTE]
><span data-ttu-id="0e748-305">下列指導方針是沈浸式 (VR) 頭戴裝置「開發電腦」目前的最低建議規格，而且會定期更新。</span><span class="sxs-lookup"><span data-stu-id="0e748-305">The following guidelines are the current minimum and recommended specs for your immersive (VR) headset *development PC*, and are updated regularly.</span></span>

>[!WARNING]
><span data-ttu-id="0e748-306">請勿將此指導方針與[最低電腦硬體相容性指導方針](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)混淆，其中概述了沈浸式 (VR) 頭戴裝置應用程式或遊戲應該定向的「取用者電腦規格」。</span><span class="sxs-lookup"><span data-stu-id="0e748-306">Do not confuse this with the [minimum PC hardware compatibility guidelines](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines), which outlines the *consumer PC specs* to which you should target your immersive (VR) headset app or game.</span></span>

<span data-ttu-id="0e748-307">如果沉浸式頭戴裝置開發電腦沒有完整大小的 HDMI 和/或 USB 3.0 連接埠，您需要[配接器](/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs)才能連線頭戴式裝置。</span><span class="sxs-lookup"><span data-stu-id="0e748-307">If your immersive headset development PC does not have full-sized HDMI and/or USB 3.0 ports, you'll need [adapters](/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs) to connect your headset.</span></span>

<span data-ttu-id="0e748-308">目前某些硬體設定有[已知問題](/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)，尤其是具有混合式圖形的筆記型電腦。</span><span class="sxs-lookup"><span data-stu-id="0e748-308">There are currently [known issues](/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality) with some hardware configurations, particularly notebooks that have hybrid graphics.</span></span>

<table>
<tr>
<th></th><th> <span data-ttu-id="0e748-309">最低需求</span><span class="sxs-lookup"><span data-stu-id="0e748-309">Minimum</span></span></th><th> <span data-ttu-id="0e748-310">建議</span><span class="sxs-lookup"><span data-stu-id="0e748-310">Recommended</span></span></th>
</tr><tr>
<td> <span data-ttu-id="0e748-311">處理器</span><span class="sxs-lookup"><span data-stu-id="0e748-311">Processor</span></span></td><td> <span data-ttu-id="0e748-312"><b>筆記型電腦：</b>Intel Mobile Core i5 第 7 代 CPU、採用超執行緒技術的雙核心 <b>傳統型：</b>Intel Desktop i5 第 6 代 CPU、採用超執行緒技術的雙核心<b>或</b> AMD FX4350 4.2Ghz 四核心對等項目</span><span class="sxs-lookup"><span data-stu-id="0e748-312"><b>Notebook:</b> Intel Mobile Core i5 7th generation CPU, Dual-Core with Hyper Threading <b>Desktop:</b> Intel Desktop i5 6th generation CPU, Dual-Core with Hyper Threading <b>OR</b> AMD FX4350 4.2Ghz Quad-Core equivalent</span></span></td><td> <span data-ttu-id="0e748-313"><b>傳統型：</b>Intel Desktop i7 第 6 代 (6 核心) <b>或</b> AMD Ryzen 5 1600 (6 核心，12 個執行緒)</span><span class="sxs-lookup"><span data-stu-id="0e748-313"><b>Desktop:</b> Intel Desktop i7 6th generation (6 Core) <b>OR</b> AMD Ryzen 5 1600 (6 Core, 12 threads)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="0e748-314">GPU</span><span class="sxs-lookup"><span data-stu-id="0e748-314">GPU</span></span></td><td> <span data-ttu-id="0e748-315"><b>筆記型電腦：</b>NVIDIA GTX 965M、AMD RX 460M (2GB) 對等項目或更高的 DX12 支援 GPU <b>傳統型：</b>NVIDIA GTX 960/1050、AMD Radeon RX 460 (2GB) 對等項目或更高的 DX12 支援 GPU</span><span class="sxs-lookup"><span data-stu-id="0e748-315"><b>Notebook:</b> NVIDIA GTX 965M, AMD RX 460M (2GB) equivalent or greater DX12 capable GPU <b>Desktop:</b> NVIDIA GTX 960/1050, AMD Radeon RX 460 (2GB) equivalent or greater DX12 capable GPU</span></span></td><td><span data-ttu-id="0e748-316"><b>傳統型：</b>NVIDIA GTX 980/1060、AMD Radeon RX 480 (2GB) 對等項目或更高的 DX12 支援 GPU</span><span class="sxs-lookup"><span data-stu-id="0e748-316"><b>Desktop:</b> NVIDIA GTX 980/1060, AMD Radeon RX 480 (2GB) equivalent or greater DX12 capable GPU</span></span></td>
</tr><tr>
<td> <span data-ttu-id="0e748-317">GPU 驅動程式 WDDM 版本</span><span class="sxs-lookup"><span data-stu-id="0e748-317">GPU driver WDDM version</span></span></td><td colspan="2"> <span data-ttu-id="0e748-318">WDDM 2.2 驅動程式</span><span class="sxs-lookup"><span data-stu-id="0e748-318">WDDM 2.2 driver</span></span></td>
</tr><tr>
<td> <span data-ttu-id="0e748-319">散熱設計功率</span><span class="sxs-lookup"><span data-stu-id="0e748-319">Thermal Design Power</span></span></td><td colspan="2"> <span data-ttu-id="0e748-320">15W 或更大</span><span class="sxs-lookup"><span data-stu-id="0e748-320">15W or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="0e748-321">圖形顯示連接埠</span><span class="sxs-lookup"><span data-stu-id="0e748-321">Graphics display ports</span></span></td><td colspan="2"> <span data-ttu-id="0e748-322">適用於頭戴式裝置的 1x 可用圖形顯示連接埠 (適用於 60Hz 頭戴式裝置的 HDMI 1.4 或 DisplayPort 1.2，適用於 90Hz 頭戴式裝置的 HDMI 2.0 或 DisplayPort 1.2)</span><span class="sxs-lookup"><span data-stu-id="0e748-322">1x available graphics display port for&#160;headset (HDMI 1.4 or DisplayPort 1.2 for 60Hz headsets, HDMI 2.0 or DisplayPort 1.2 for 90Hz headsets)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="0e748-323">顯示器解析度</span><span class="sxs-lookup"><span data-stu-id="0e748-323">Display resolution</span></span></td><td colspan="2"> <span data-ttu-id="0e748-324">解決方法：SVGA (800 x 600) 或更大的位元深度：每像素 32 位元的色彩</span><span class="sxs-lookup"><span data-stu-id="0e748-324">Resolution: SVGA (800x600) or greater Bit depth: 32 bits of color per pixel</span></span></td>
</tr><tr>
<td> <span data-ttu-id="0e748-325">Memory</span><span class="sxs-lookup"><span data-stu-id="0e748-325">Memory</span></span></td><td> <span data-ttu-id="0e748-326">8&#160;GB RAM 或更大</span><span class="sxs-lookup"><span data-stu-id="0e748-326">8&#160;GB of RAM or greater</span></span></td><td> <span data-ttu-id="0e748-327">16 GB RAM 或更大</span><span class="sxs-lookup"><span data-stu-id="0e748-327">16 GB of RAM or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="0e748-328">存放裝置</span><span class="sxs-lookup"><span data-stu-id="0e748-328">Storage</span></span></td><td colspan="2"> <span data-ttu-id="0e748-329">&gt;10 GB 額外可用空間</span><span class="sxs-lookup"><span data-stu-id="0e748-329">&gt;10 GB additional free space</span></span></td>
</tr><tr>
<td> <span data-ttu-id="0e748-330">USB 連接埠</span><span class="sxs-lookup"><span data-stu-id="0e748-330">USB Ports</span></span></td><td colspan="2"> <span data-ttu-id="0e748-331">適用於頭戴式裝置的 1x 可用 USB 連接埠 (USB 3.0 Type-A) <b>注意：USB 必須提供至少 900mA</b></span><span class="sxs-lookup"><span data-stu-id="0e748-331">1x available USB port for headset (USB 3.0 Type-A) <b>Note: USB must supply a minimum of 900mA</b></span></span></td>
</tr><tr>
<td> <span data-ttu-id="0e748-332">Bluetooth</span><span class="sxs-lookup"><span data-stu-id="0e748-332">Bluetooth</span></span></td><td colspan="2"> <span data-ttu-id="0e748-333">Bluetooth 4.0 (適用於周邊連線)</span><span class="sxs-lookup"><span data-stu-id="0e748-333">Bluetooth 4.0 (for accessory connectivity)</span></span></td>
</tr>
</table>

<span data-ttu-id="0e748-334">如果您是首次使用 MRTK 進行原生開發，建議您依循我們策劃的原生開發旅程：</span><span class="sxs-lookup"><span data-stu-id="0e748-334">If you're new to Native development with MRTK, we recommend following our curated Native development journey:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="0e748-335">開始您的原生旅程</span><span class="sxs-lookup"><span data-stu-id="0e748-335">Start your Native journey</span></span>](../native/directx-development-overview.md)

## <a name="next-development-checkpoint"></a><span data-ttu-id="0e748-336">下一個開發檢查點</span><span class="sxs-lookup"><span data-stu-id="0e748-336">Next Development Checkpoint</span></span>

<span data-ttu-id="0e748-337">依循我們配置的 Native 開發檢查點旅程，您的下一個工作將是設定 HoloLens 2 的開發環境。</span><span class="sxs-lookup"><span data-stu-id="0e748-337">If you're following the Native development checkpoint journey we've laid out, your next task is to configure your development environment for HoloLens 2.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="0e748-338">設定 HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="0e748-338">Setup for HoloLens 2</span></span>](../native/openxr-getting-started.md#getting-started-with-openxr-for-hololens-2)

<span data-ttu-id="0e748-339">您可以隨時回到[原生開發檢查點](../native/directx-development-overview.md#1-getting-started)。</span><span class="sxs-lookup"><span data-stu-id="0e748-339">You can always go back to the [Native development checkpoints](../native/directx-development-overview.md#1-getting-started) at any time.</span></span>