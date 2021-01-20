---
title: 將 VR 應用程式移植到 Windows Mixed Reality
description: 逐步解說逐步解說，說明如何將現有的沉浸式應用程式移植至 Windows Mixed Reality。
author: JBrentJ
ms.author: alexturn
ms.date: 12/9/2020
ms.topic: article
keywords: 埠、unity、unreal、中介軟體、引擎、UWP、Win32、移植、HoloLens 第1代、混合現實耳機、windows mixed reality 耳機、遷移、Windows 10、輸入對應、
ms.openlocfilehash: dd09c6479bfcf3659b3e9355be898d77bccc6dc6
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/20/2021
ms.locfileid: "98580570"
---
# <a name="porting-vr-apps-to-windows-mixed-reality"></a><span data-ttu-id="4016f-104">將 VR 應用程式移植到 Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="4016f-104">Porting VR apps to Windows Mixed Reality</span></span>

<span data-ttu-id="4016f-105">Windows 10 包含沉浸式和全像攝影耳機的支援。</span><span class="sxs-lookup"><span data-stu-id="4016f-105">Windows 10 includes support for immersive and holographic headsets.</span></span> <span data-ttu-id="4016f-106">如果您已建立其他裝置的內容（例如 Oculus Rift 或 HTC Vive），它們就會相依于存在於作業系統平臺 API 之上的程式庫。</span><span class="sxs-lookup"><span data-stu-id="4016f-106">If you've built content for other devices like the Oculus Rift or HTC Vive, they have dependencies on libraries that exist above the operating system's platform API.</span></span> <span data-ttu-id="4016f-107">將現有的 Win32 Unity VR 應用程式帶入 Windows Mixed Reality 牽涉到將廠商專屬的 VR Sdk 重定目標使用於 Unity 的跨廠商 VR Api。</span><span class="sxs-lookup"><span data-stu-id="4016f-107">Bringing existing Win32 Unity VR apps over to Windows Mixed Reality involves retargeting usage of vendor-specific VR SDKs to Unity's cross-vendor VR APIs.</span></span>

## <a name="porting-requirements"></a><span data-ttu-id="4016f-108">移植需求</span><span class="sxs-lookup"><span data-stu-id="4016f-108">Porting requirements</span></span>

<span data-ttu-id="4016f-109">概括而言，下列步驟牽涉到移植現有的內容：</span><span class="sxs-lookup"><span data-stu-id="4016f-109">At a high level, the following steps are involved in porting existing content:</span></span>
1. <span data-ttu-id="4016f-110">**確定您的電腦正在執行 Windows 10 Fall Creators Update (16299) 。**</span><span class="sxs-lookup"><span data-stu-id="4016f-110">**Make sure your PC is running the Windows 10 Fall Creators Update (16299).**</span></span> <span data-ttu-id="4016f-111">我們不再建議從 Insider Skip 通道接收預覽版，因為這些組建對於混合現實開發來說不是最穩定的。</span><span class="sxs-lookup"><span data-stu-id="4016f-111">We no longer recommend receiving preview builds from the Insider Skip Ahead ring, as those builds won't be the most stable for mixed reality development.</span></span>
2. <span data-ttu-id="4016f-112">**升級至最新版本的圖形或遊戲引擎。**</span><span class="sxs-lookup"><span data-stu-id="4016f-112">**Upgrade to the latest version of your graphics or game engine.**</span></span> <span data-ttu-id="4016f-113">遊戲引擎將需要支援2017年4月) 或更高版本的 Windows 10 SDK 版本 10.0.15063.0 (。</span><span class="sxs-lookup"><span data-stu-id="4016f-113">Game engines will need to support the Windows 10 SDK version 10.0.15063.0 (released in April 2017) or higher.</span></span>
3. <span data-ttu-id="4016f-114">**升級任何中介軟體、外掛程式或元件。**</span><span class="sxs-lookup"><span data-stu-id="4016f-114">**Upgrade any middleware, plug-ins, or components.**</span></span> <span data-ttu-id="4016f-115">如果您的應用程式包含任何元件，最好是升級到最新版本。</span><span class="sxs-lookup"><span data-stu-id="4016f-115">If your app contains any components, it's a good idea to upgrade to the latest version.</span></span>
4. <span data-ttu-id="4016f-116">**移除重複 sdk 的** 相依性。</span><span class="sxs-lookup"><span data-stu-id="4016f-116">**Remove dependencies on duplicate SDKs**.</span></span> <span data-ttu-id="4016f-117">視內容的目標裝置而定，您必須移除或有條件地編譯該 SDK，讓您可以改為以 Windows Api 為目標。</span><span class="sxs-lookup"><span data-stu-id="4016f-117">Depending on which device your content was targeting, you'll need to remove or conditionally compile out that SDK so you can target the Windows APIs instead.</span></span> <span data-ttu-id="4016f-118">此案例的範例將會 SteamVR。</span><span class="sxs-lookup"><span data-stu-id="4016f-118">An example of this scenario would be SteamVR.</span></span>
5. <span data-ttu-id="4016f-119">**解決組建問題。**</span><span class="sxs-lookup"><span data-stu-id="4016f-119">**Work through build issues.**</span></span> <span data-ttu-id="4016f-120">此時，移植練習是您的應用程式、引擎和您擁有的元件相依性所特有的。</span><span class="sxs-lookup"><span data-stu-id="4016f-120">At this point, the porting exercise is specific to your app, your engine, and the component dependencies you have.</span></span>

## <a name="common-porting-steps"></a><span data-ttu-id="4016f-121">常見的移植步驟</span><span class="sxs-lookup"><span data-stu-id="4016f-121">Common porting steps</span></span>

### <a name="1-make-sure-you-have-the-right-development-hardware"></a><span data-ttu-id="4016f-122">1. 請確定您有正確的開發硬體</span><span class="sxs-lookup"><span data-stu-id="4016f-122">1. Make sure you have the right development hardware</span></span>

<span data-ttu-id="4016f-123">[ [安裝工具](../install-the-tools.md#immersive-vr-headset-requirements) ] 頁面會列出建議的開發硬體。</span><span class="sxs-lookup"><span data-stu-id="4016f-123">The [install the tools](../install-the-tools.md#immersive-vr-headset-requirements) page lists the recommended development hardware.</span></span>

### <a name="2-upgrade-to-the-latest-flight-of-windows-10"></a><span data-ttu-id="4016f-124">2. 升級到 Windows 10 的最新航班</span><span class="sxs-lookup"><span data-stu-id="4016f-124">2. Upgrade to the latest flight of Windows 10</span></span>

<span data-ttu-id="4016f-125">Windows Mixed Reality 平臺仍在積極開發中。</span><span class="sxs-lookup"><span data-stu-id="4016f-125">The Windows Mixed Reality platform is still under active development.</span></span> <span data-ttu-id="4016f-126">建議您 [加入 Windows 測試人員計畫](https://insider.windows.com/) ，以存取「Windows 測試人員快速」飛行。</span><span class="sxs-lookup"><span data-stu-id="4016f-126">We recommend [joining the Windows Insider Program](https://insider.windows.com/) to access the "Windows Insider Fast" flight.</span></span>
1. <span data-ttu-id="4016f-127">安裝 [Windows 10 Creators Update](https://www.microsoft.com/software-download/windows10)</span><span class="sxs-lookup"><span data-stu-id="4016f-127">Install the [Windows 10 Creators Update](https://www.microsoft.com/software-download/windows10)</span></span>
2. <span data-ttu-id="4016f-128">[加入](https://insider.windows.com/) Windows 測試人員計畫。</span><span class="sxs-lookup"><span data-stu-id="4016f-128">[Join](https://insider.windows.com/) the Windows Insider Program.</span></span>
3. <span data-ttu-id="4016f-129">啟用 [開發人員模式](/windows/uwp/get-started/enable-your-device-for-development)</span><span class="sxs-lookup"><span data-stu-id="4016f-129">Enable [Developer Mode](/windows/uwp/get-started/enable-your-device-for-development)</span></span>
4. <span data-ttu-id="4016f-130">透過 [**設定] > 更新 & 安全性] 區段** 切換至 [Windows 測試人員快速航班](/archive/blogs/uktechnet/joining-insider-preview)</span><span class="sxs-lookup"><span data-stu-id="4016f-130">Switch to the [Windows Insider Fast flights](/archive/blogs/uktechnet/joining-insider-preview) through **Settings > Update & Security Section**</span></span>

### <a name="3-upgrade-to-the-most-recent-build-of-visual-studio"></a><span data-ttu-id="4016f-131">3. 升級為最新組建的 Visual Studio</span><span class="sxs-lookup"><span data-stu-id="4016f-131">3. Upgrade to the most recent build of Visual Studio</span></span>
* <span data-ttu-id="4016f-132">如果您是使用 Visual Studio，請升級至最新的組建</span><span class="sxs-lookup"><span data-stu-id="4016f-132">If you're using Visual Studio, then upgrade to the most recent build</span></span>
* <span data-ttu-id="4016f-133">請參閱 Visual Studio 2019 下 [的安裝工具](../install-the-tools.md#installation-checklist) 頁面</span><span class="sxs-lookup"><span data-stu-id="4016f-133">See [Install the tools](../install-the-tools.md#installation-checklist) page under Visual Studio 2019</span></span>

### <a name="4-choose-the-correct-adapter"></a><span data-ttu-id="4016f-134">4. 選擇正確的介面卡</span><span class="sxs-lookup"><span data-stu-id="4016f-134">4. Choose the correct Adapter</span></span>
* <span data-ttu-id="4016f-135">在具有兩個 Gpu 的筆記本系統中，以 [正確的介面卡為目標](../native/rendering-in-directx.md#hybrid-graphics-pcs-and-mixed-reality-applications)。</span><span class="sxs-lookup"><span data-stu-id="4016f-135">In systems like notebooks with two GPUs, [target the correct adapter](../native/rendering-in-directx.md#hybrid-graphics-pcs-and-mixed-reality-applications).</span></span> <span data-ttu-id="4016f-136">這適用于 Unity 和原生 DirectX 應用程式，其中會以明確或隱含的方式 (媒體基礎) ）來建立 ID3D11Device，以供其功能使用。</span><span class="sxs-lookup"><span data-stu-id="4016f-136">This applies to Unity and native DirectX apps where a ID3D11Device is created, either explicitly or implicitly (Media Foundation), for its functionality.</span></span>

## <a name="unity-porting-guidance"></a><span data-ttu-id="4016f-137">Unity 移植指引</span><span class="sxs-lookup"><span data-stu-id="4016f-137">Unity porting guidance</span></span>

[!INCLUDE[](includes/unity-porting-guidance.md)]

## <a name="unreal-porting-guidance"></a><span data-ttu-id="4016f-138">Unreal 移植指引</span><span class="sxs-lookup"><span data-stu-id="4016f-138">Unreal porting guidance</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4016f-139">如果您使用的是 HP 回 G2 控制器，請參閱 [本文以取得其他](../unreal/unreal-reverb-g2-controllers.md) 輸入對應指示。</span><span class="sxs-lookup"><span data-stu-id="4016f-139">If you're using HP Reverb G2 controllers, please refer to [this article](../unreal/unreal-reverb-g2-controllers.md) for additional input mapping instructions.</span></span>

## <a name="see-also"></a><span data-ttu-id="4016f-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4016f-140">See also</span></span>
* [<span data-ttu-id="4016f-141">Windows Mixed Reality 最小電腦硬體相容性指導方針</span><span class="sxs-lookup"><span data-stu-id="4016f-141">Windows Mixed Reality minimum PC hardware compatibility guidelines</span></span>](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)
* [<span data-ttu-id="4016f-142">瞭解混合現實的效能</span><span class="sxs-lookup"><span data-stu-id="4016f-142">Understanding Performance for Mixed Reality</span></span>](../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md)
* [<span data-ttu-id="4016f-143">Unity 的效能建議</span><span class="sxs-lookup"><span data-stu-id="4016f-143">Performance Recommendations for Unity</span></span>](../unity/performance-recommendations-for-unity.md)
* [<span data-ttu-id="4016f-144">運動控制器</span><span class="sxs-lookup"><span data-stu-id="4016f-144">Motion controllers</span></span>](../../design/motion-controllers.md)
* [<span data-ttu-id="4016f-145">Unity 中的動作控制器</span><span class="sxs-lookup"><span data-stu-id="4016f-145">Motion controllers in Unity</span></span>](../unity/motion-controllers-in-unity.md)
* [<span data-ttu-id="4016f-146">UnityEngine. XR。輸入</span><span class="sxs-lookup"><span data-stu-id="4016f-146">UnityEngine.XR.WSA.Input</span></span>](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.html)
* [<span data-ttu-id="4016f-147">UnityEngine. XR. InputTracking</span><span class="sxs-lookup"><span data-stu-id="4016f-147">UnityEngine.XR.InputTracking</span></span>](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)
* [<span data-ttu-id="4016f-148">移植指南</span><span class="sxs-lookup"><span data-stu-id="4016f-148">Porting guides</span></span>](porting-guides.md)