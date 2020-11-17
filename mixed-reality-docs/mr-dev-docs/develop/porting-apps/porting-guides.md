---
title: 移植指南
description: 逐步解說逐步解說，說明如何將現有的沉浸式應用程式移植至 Windows Mixed Reality。
author: JBrentJ
ms.author: alexturn
ms.date: 07/07/2020
ms.topic: article
keywords: 埠、unity、unreal、中介軟體、引擎、UWP、Win32、移植、HoloLens 第1代、混合現實耳機、windows mixed reality 耳機、遷移、Windows 10、輸入對應、
ms.openlocfilehash: 18129151b1e3d11f9e9c7bb3c3420c23b5fd1dd0
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2020
ms.locfileid: "94677727"
---
# <a name="porting-guides"></a><span data-ttu-id="d67ee-104">移植指南</span><span class="sxs-lookup"><span data-stu-id="d67ee-104">Porting guides</span></span>

<span data-ttu-id="d67ee-105">Windows 10 包含沉浸式和全像攝影耳機的直接支援。</span><span class="sxs-lookup"><span data-stu-id="d67ee-105">Windows 10 includes direct support for immersive and holographic headsets.</span></span> <span data-ttu-id="d67ee-106">如果您已建立其他裝置的內容（例如 Oculus Rift 或 HTC Vive），這些裝置會相依于存在於作業系統平臺 API 之上的程式庫。</span><span class="sxs-lookup"><span data-stu-id="d67ee-106">If you've built content for other devices, such as the Oculus Rift or HTC Vive, these have dependencies on libraries that exist above the operating system's platform API.</span></span> <span data-ttu-id="d67ee-107">將現有的 Win32 Unity VR 應用程式帶入 Windows Mixed Reality 牽涉到將廠商專屬的 VR Sdk 重定目標使用於 Unity 的跨廠商 VR Api。</span><span class="sxs-lookup"><span data-stu-id="d67ee-107">Bringing existing Win32 Unity VR apps over to Windows Mixed Reality involves retargeting usage of vendor-specific VR SDKs to Unity's cross-vendor VR APIs.</span></span>

## <a name="porting-overview"></a><span data-ttu-id="d67ee-108">移植總覽</span><span class="sxs-lookup"><span data-stu-id="d67ee-108">Porting overview</span></span>

<span data-ttu-id="d67ee-109">概括而言，下列步驟牽涉到移植現有的內容：</span><span class="sxs-lookup"><span data-stu-id="d67ee-109">At a high level, the following steps are involved in porting existing content:</span></span>
1. <span data-ttu-id="d67ee-110">**確定您的電腦正在執行 Windows 10 Fall Creators Update (16299) 。**</span><span class="sxs-lookup"><span data-stu-id="d67ee-110">**Make sure your PC is running the Windows 10 Fall Creators Update (16299).**</span></span> <span data-ttu-id="d67ee-111">我們不再建議從 Insider Skip 通道接收預覽版，因為這些組建對於混合現實開發來說不是最穩定的。</span><span class="sxs-lookup"><span data-stu-id="d67ee-111">We no longer recommend receiving preview builds from the Insider Skip Ahead ring, as those builds won't be the most stable for mixed reality development.</span></span>
2. <span data-ttu-id="d67ee-112">**升級至最新版本的圖形或遊戲引擎。**</span><span class="sxs-lookup"><span data-stu-id="d67ee-112">**Upgrade to the latest version of your graphics or game engine.**</span></span> <span data-ttu-id="d67ee-113">遊戲引擎將需要支援2017年4月) 或更高版本的 Windows 10 SDK 版本 10.0.15063.0 (。</span><span class="sxs-lookup"><span data-stu-id="d67ee-113">Game engines will need to support the Windows 10 SDK version 10.0.15063.0 (released in April 2017) or higher.</span></span>
3. <span data-ttu-id="d67ee-114">**升級任何中介軟體、外掛程式或元件。**</span><span class="sxs-lookup"><span data-stu-id="d67ee-114">**Upgrade any middleware, plug-ins, or components.**</span></span> <span data-ttu-id="d67ee-115">如果您的應用程式包含任何元件，最好是升級到最新版本。</span><span class="sxs-lookup"><span data-stu-id="d67ee-115">If your app contains any components, it's a good idea to upgrade to the latest version.</span></span>
4. <span data-ttu-id="d67ee-116">**移除重複 sdk 的** 相依性。</span><span class="sxs-lookup"><span data-stu-id="d67ee-116">**Remove dependencies on duplicate SDKs**.</span></span> <span data-ttu-id="d67ee-117">根據您的內容的目標裝置而定，您必須移除或有條件地編譯該 SDK (例如 SteamVR) ，因此您可以改為以 Windows Api 為目標。</span><span class="sxs-lookup"><span data-stu-id="d67ee-117">Depending on which device your content was targeting, you'll need to remove or conditionally compile out that SDK (for example, SteamVR) so you can target the Windows APIs instead.</span></span>
5. <span data-ttu-id="d67ee-118">**解決組建問題。**</span><span class="sxs-lookup"><span data-stu-id="d67ee-118">**Work through build issues.**</span></span> <span data-ttu-id="d67ee-119">此時，移植練習是您的應用程式、引擎和您擁有的元件相依性所特有的。</span><span class="sxs-lookup"><span data-stu-id="d67ee-119">At this point, the porting exercise is specific to your app, your engine, and the component dependencies you have.</span></span>

## <a name="common-porting-steps"></a><span data-ttu-id="d67ee-120">常見的移植步驟</span><span class="sxs-lookup"><span data-stu-id="d67ee-120">Common porting steps</span></span>

### <a name="1-make-sure-you-have-the-right-development-hardware"></a><span data-ttu-id="d67ee-121">1. 請確定您有正確的開發硬體</span><span class="sxs-lookup"><span data-stu-id="d67ee-121">1. Make sure you have the right development hardware</span></span>

<span data-ttu-id="d67ee-122">[ [安裝工具](../install-the-tools.md#immersive-vr-headset-requirements) ] 頁面會列出建議的開發硬體。</span><span class="sxs-lookup"><span data-stu-id="d67ee-122">The [install the tools](../install-the-tools.md#immersive-vr-headset-requirements) page lists the recommended development hardware.</span></span>

### <a name="2-upgrade-to-the-latest-flight-of-windows-10"></a><span data-ttu-id="d67ee-123">2. 升級到 Windows 10 的最新航班</span><span class="sxs-lookup"><span data-stu-id="d67ee-123">2. Upgrade to the latest flight of Windows 10</span></span>

<span data-ttu-id="d67ee-124">Windows Mixed Reality 平臺仍在積極開發中。</span><span class="sxs-lookup"><span data-stu-id="d67ee-124">The Windows Mixed Reality platform is still under active development.</span></span> <span data-ttu-id="d67ee-125">建議您 [加入 Windows 測試人員計畫](https://insider.windows.com/) ，以存取「Windows 測試人員快速」飛行。</span><span class="sxs-lookup"><span data-stu-id="d67ee-125">We recommend [joining the Windows Insider Program](https://insider.windows.com/) to access the "Windows Insider Fast" flight.</span></span>
1. <span data-ttu-id="d67ee-126">安裝 [Windows 10 Creators Update](https://www.microsoft.com/software-download/windows10)</span><span class="sxs-lookup"><span data-stu-id="d67ee-126">Install the [Windows 10 Creators Update](https://www.microsoft.com/software-download/windows10)</span></span>
2. <span data-ttu-id="d67ee-127">[加入](https://insider.windows.com/) Windows 測試人員計畫。</span><span class="sxs-lookup"><span data-stu-id="d67ee-127">[Join](https://insider.windows.com/) the Windows Insider Program.</span></span>
3. <span data-ttu-id="d67ee-128">啟用 [開發人員模式](https://docs.microsoft.com/windows/uwp/get-started/enable-your-device-for-development)</span><span class="sxs-lookup"><span data-stu-id="d67ee-128">Enable [Developer Mode](https://docs.microsoft.com/windows/uwp/get-started/enable-your-device-for-development)</span></span>
4. <span data-ttu-id="d67ee-129">透過 [**設定] > 更新 & 安全性] 區段** 切換至 [Windows 測試人員快速航班](https://blogs.technet.microsoft.com/uktechnet/2016/07/01/joining-insider-preview)</span><span class="sxs-lookup"><span data-stu-id="d67ee-129">Switch to the [Windows Insider Fast flights](https://blogs.technet.microsoft.com/uktechnet/2016/07/01/joining-insider-preview) through **Settings > Update & Security Section**</span></span>

### <a name="3-upgrade-to-the-most-recent-build-of-visual-studio"></a><span data-ttu-id="d67ee-130">3. 升級為最新組建的 Visual Studio</span><span class="sxs-lookup"><span data-stu-id="d67ee-130">3. Upgrade to the most recent build of Visual Studio</span></span>
* <span data-ttu-id="d67ee-131">如果您是使用 Visual Studio 然後升級至最新的組建</span><span class="sxs-lookup"><span data-stu-id="d67ee-131">If you're using Visual Studio then upgrade to the most recent build</span></span>
* <span data-ttu-id="d67ee-132">請參閱 Visual Studio 2019 下 [的安裝工具](../install-the-tools.md#installation-checklist) 頁面</span><span class="sxs-lookup"><span data-stu-id="d67ee-132">See [Install the tools](../install-the-tools.md#installation-checklist) page under Visual Studio 2019</span></span>

### <a name="4-choose-the-correct-adapter"></a><span data-ttu-id="d67ee-133">4. 選擇正確的介面卡</span><span class="sxs-lookup"><span data-stu-id="d67ee-133">4. Choose the correct Adapter</span></span>
* <span data-ttu-id="d67ee-134">在具有兩個 Gpu 的筆記本系統中，以 [正確的介面卡為目標](../native/rendering-in-directx.md#hybrid-graphics-pcs-and-mixed-reality-applications)。</span><span class="sxs-lookup"><span data-stu-id="d67ee-134">In systems like notebooks with two GPUs, [target the correct adapter](../native/rendering-in-directx.md#hybrid-graphics-pcs-and-mixed-reality-applications).</span></span> <span data-ttu-id="d67ee-135">這適用于 Unity 和原生 DirectX 應用程式，其中會以明確或隱含的方式 (媒體基礎) ）來建立 ID3D11Device，以供其功能使用。</span><span class="sxs-lookup"><span data-stu-id="d67ee-135">This applies to Unity and native DirectX apps where a ID3D11Device is created, either explicitly or implicitly (Media Foundation), for its functionality.</span></span>

## <a name="unity-porting-guidance"></a><span data-ttu-id="d67ee-136">Unity 移植指引</span><span class="sxs-lookup"><span data-stu-id="d67ee-136">Unity porting guidance</span></span>

[!INCLUDE[](includes/unity-porting-guidance.md)]

## <a name="unreal-porting-guidance"></a><span data-ttu-id="d67ee-137">Unreal 移植指引</span><span class="sxs-lookup"><span data-stu-id="d67ee-137">Unreal porting guidance</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d67ee-138">如果您使用的是 HP 回 G2 控制器，請參閱 [本文以取得其他](../unreal/unreal-reverb-g2-controllers.md) 輸入對應指示。</span><span class="sxs-lookup"><span data-stu-id="d67ee-138">If you're using HP Reverb G2 controllers, please refer to [this article](../unreal/unreal-reverb-g2-controllers.md) for additional input mapping instructions.</span></span>

## <a name="see-also"></a><span data-ttu-id="d67ee-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d67ee-139">See also</span></span>
* [<span data-ttu-id="d67ee-140">Windows Mixed Reality 最小電腦硬體相容性指導方針</span><span class="sxs-lookup"><span data-stu-id="d67ee-140">Windows Mixed Reality minimum PC hardware compatibility guidelines</span></span>](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)
* [<span data-ttu-id="d67ee-141">瞭解混合現實的效能</span><span class="sxs-lookup"><span data-stu-id="d67ee-141">Understanding Performance for Mixed Reality</span></span>](../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md)
* [<span data-ttu-id="d67ee-142">Unity 的效能建議</span><span class="sxs-lookup"><span data-stu-id="d67ee-142">Performance Recommendations for Unity</span></span>](../unity/performance-recommendations-for-unity.md)
* [<span data-ttu-id="d67ee-143">運動控制器</span><span class="sxs-lookup"><span data-stu-id="d67ee-143">Motion controllers</span></span>](../../design/motion-controllers.md)
* [<span data-ttu-id="d67ee-144">Unity 中的筆勢和運動控制器</span><span class="sxs-lookup"><span data-stu-id="d67ee-144">Gestures and motion controllers in Unity</span></span>](../unity/gestures-and-motion-controllers-in-unity.md)
* [<span data-ttu-id="d67ee-145">UnityEngine. XR。輸入</span><span class="sxs-lookup"><span data-stu-id="d67ee-145">UnityEngine.XR.WSA.Input</span></span>](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.html)
* [<span data-ttu-id="d67ee-146">UnityEngine. XR. InputTracking</span><span class="sxs-lookup"><span data-stu-id="d67ee-146">UnityEngine.XR.InputTracking</span></span>](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)
* [<span data-ttu-id="d67ee-147">移植指南</span><span class="sxs-lookup"><span data-stu-id="d67ee-147">Porting guides</span></span>](porting-guides.md)