---
title: Unity 中的 OpenXR 外掛程式支援功能
description: 探索 OpenXR 針對 Unity 中的混合現實開發所支援的功能。
author: hferrone
ms.author: alexturn
ms.date: 12/15/2020
ms.topic: article
keywords: openxr、unity、hololens、hololens 2、mixed reality、MRTK、Mixed Reality 工具組、增強的現實、虛擬實境、混合現實耳機、學習、教學課程、快速入門
ms.openlocfilehash: dc908762d6e44e04f56b8ff82b90394106ca42e5
ms.sourcegitcommit: 2bf79eef6a9b845494484f458443ef4f89d7efc0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/17/2020
ms.locfileid: "97622898"
---
# <a name="mixed-reality-openxr-supported-features-in-unity"></a><span data-ttu-id="4b035-104">混合現實 OpenXR Unity 中支援的功能</span><span class="sxs-lookup"><span data-stu-id="4b035-104">Mixed Reality OpenXR supported features in Unity</span></span>

<span data-ttu-id="4b035-105">**Mixed Reality OpenXR 外掛程式** 套件是 Unity **OpenXR 外掛程式** 的延伸模組，並支援 HoloLens 2 和 Windows Mixed Reality 耳機的功能套件。</span><span class="sxs-lookup"><span data-stu-id="4b035-105">The **Mixed Reality OpenXR Plugin** package is an extension of Unity's **OpenXR Plugin** and supports a suite of features for HoloLens 2 and Windows Mixed Reality headsets.</span></span> <span data-ttu-id="4b035-106">繼續之前，請確定您已安裝 **unity 2020.2** 或更新版本、 **OpenXR 外掛程式版本 0.1.1** 或更新版本，且您的 Unity 專案已 [設定 OpenXR](openxr-getting-started.md)。</span><span class="sxs-lookup"><span data-stu-id="4b035-106">Before continuing, make sure that you've installed **Unity 2020.2** or later, **OpenXR Plugin version 0.1.1** or later, and your Unity project is [configured for OpenXR](openxr-getting-started.md).</span></span>

## <a name="whats-supported"></a><span data-ttu-id="4b035-107">支援的項目</span><span class="sxs-lookup"><span data-stu-id="4b035-107">What's supported</span></span>

<span data-ttu-id="4b035-108">目前支援下列功能：</span><span class="sxs-lookup"><span data-stu-id="4b035-108">The following features are currently supported:</span></span>

* <span data-ttu-id="4b035-109">支援 HoloLens 2 的 UWP 應用程式，以及 Windows Mixed Reality 耳機的 Win32 VR 應用程式。</span><span class="sxs-lookup"><span data-stu-id="4b035-109">Supports both UWP applications for HoloLens 2 and Win32 VR applications for Windows Mixed Reality headsets.</span></span>
* <span data-ttu-id="4b035-110">針對 HoloLens 2 應用程式優化 UWP 套件和 CoreWindow 互動。</span><span class="sxs-lookup"><span data-stu-id="4b035-110">Optimizes UWP package and CoreWindow interaction for HoloLens 2 applications.</span></span>
* <span data-ttu-id="4b035-111">使用錨點和未系結空間的世界規模追蹤。</span><span class="sxs-lookup"><span data-stu-id="4b035-111">World scale tracking using Anchors and Unbounded space.</span></span>
* <span data-ttu-id="4b035-112">錨點儲存體 API，以將錨點保存到 HoloLens 2 的本機儲存體。</span><span class="sxs-lookup"><span data-stu-id="4b035-112">Anchor storage API to persist anchors to HoloLens 2 local storage.</span></span>
* <span data-ttu-id="4b035-113">移動控制器和手互動，包括新的 HP 回音卡控制器。</span><span class="sxs-lookup"><span data-stu-id="4b035-113">Motion controller and hand interactions, including the new HP Reverb G2 controller.</span></span>
* <span data-ttu-id="4b035-114">使用26個接點和聯合半徑輸入，以明確表述的手勢進行追蹤。</span><span class="sxs-lookup"><span data-stu-id="4b035-114">Articulated hand tracking using 26 joints and joint radius inputs.</span></span>
* <span data-ttu-id="4b035-115">HoloLens 2 上的眼睛注視互動。</span><span class="sxs-lookup"><span data-stu-id="4b035-115">Eye gaze interaction on HoloLens 2.</span></span>
* <span data-ttu-id="4b035-116">HoloLens 2 上尋找 (PV) 攝影機的相片/影片。</span><span class="sxs-lookup"><span data-stu-id="4b035-116">Locating photo/video (PV) camera on HoloLens 2.</span></span>
* <span data-ttu-id="4b035-117">混合實境擷取使用透過 PV 攝影機的第三種眼睛呈現。</span><span class="sxs-lookup"><span data-stu-id="4b035-117">Mixed Reality Capture using 3rd eye rendering through PV camera.</span></span>
* <span data-ttu-id="4b035-118">支援「播放」以使用全像「遠端處理」應用程式 HoloLens 2，讓開發人員不需要建立及部署到裝置，即可將腳本進行偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="4b035-118">Supports "Play" to HoloLens 2 using the Holographic Remoting app, allowing developers to debug scripts without building and deploying to the device.</span></span>
* <span data-ttu-id="4b035-119">透過 MRTK OpenXR adapter 套件與 MRTK Unity 2.5.2 相容。</span><span class="sxs-lookup"><span data-stu-id="4b035-119">Compatible with MRTK Unity 2.5.2 through MRTK OpenXR adapter package.</span></span> <missing link>
* <span data-ttu-id="4b035-120">與 Unity [ARFoundation 4.0](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html) 或更新版本相容</span><span class="sxs-lookup"><span data-stu-id="4b035-120">Compatible with Unity [ARFoundation 4.0](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html) or later</span></span>

## <a name="holographic-remoting-in-unity-editor-play-mode"></a><span data-ttu-id="4b035-121">Unity 編輯器 play 模式的全像遠端功能</span><span class="sxs-lookup"><span data-stu-id="4b035-121">Holographic Remoting in Unity Editor play mode</span></span>

<span data-ttu-id="4b035-122">在 Visual Studio 專案中建立 UWP Unity 專案，然後將它封裝並部署到 HoloLens 2 裝置，可能需要一些時間。</span><span class="sxs-lookup"><span data-stu-id="4b035-122">Building a UWP Unity project in Visual Studio project and then packaging and deploying it to a HoloLens 2 device can take some time.</span></span> <span data-ttu-id="4b035-123">其中一個解決方法是啟用全像「全像」編輯器遠端處理，讓您透過網路直接使用「播放」模式來將 c # 腳本進行 HoloLens 2 裝置的偵測。</span><span class="sxs-lookup"><span data-stu-id="4b035-123">One solution is to enable the Holographic Editor Remoting, which lets you debug your C# script using “Play” mode directly to a HoloLens 2 device over your network.</span></span> <span data-ttu-id="4b035-124">此案例可避免建立 UWP 套件並將其部署至遠端裝置的額外負荷。</span><span class="sxs-lookup"><span data-stu-id="4b035-124">This scenario avoids the overhead of building and deploying a UWP package to remote device.</span></span>

1. <span data-ttu-id="4b035-125">首先，您必須從存放區的 HoloLens 2 安裝全像 [遠端播放機應用程式](https://www.microsoft.com/store/productId/9NBLGGH4SV40) 。</span><span class="sxs-lookup"><span data-stu-id="4b035-125">First, you need to [install the Holographic Remoting Player app](https://www.microsoft.com/store/productId/9NBLGGH4SV40) from Store on your HoloLens 2</span></span>  
2. <span data-ttu-id="4b035-126">在 HoloLens 2 上執行全像遠端播放播放程式應用程式，您會看到要連接的版本號碼和 IP 位址</span><span class="sxs-lookup"><span data-stu-id="4b035-126">Run the Holographic Remoting Player app on HoloLens 2 and you'll see the version number and IP address to connect to</span></span>
    * <span data-ttu-id="4b035-127">您將需要2.4 或更新版本才能使用 OpenXR 外掛程式</span><span class="sxs-lookup"><span data-stu-id="4b035-127">You'll need v2.4 or later to work with the OpenXR plugin</span></span>

![HoloLens 中執行的全像 Remoting 播放程式的螢幕擷取畫面](images/openxr-features-img-01.png)

3. <span data-ttu-id="4b035-129">開啟 [ **編輯-> 專案設定**]，流覽至 **XR 外掛程式管理**，然後選取 [ **Windows Mixed Reality 功能集** ] 方塊：</span><span class="sxs-lookup"><span data-stu-id="4b035-129">Open **Edit -> Project Settings**, navigate to **XR plug-in Management**, and check the **Windows Mixed Reality feature set** box:</span></span>

![醒目提示 XR 外掛程式管理的 Unity 編輯器中開啟之 [專案設定] 面板的螢幕擷取畫面](images/openxr-features-img-02.png)

4. <span data-ttu-id="4b035-131">展開 [ **OpenXR** ] 底下的 [**功能**] 區段，然後選取 [**全部顯示**]</span><span class="sxs-lookup"><span data-stu-id="4b035-131">Expand the **Features** section under **OpenXR** and select **Show All**</span></span>
5. <span data-ttu-id="4b035-132">核取 [全像攝影 **編輯器遠端處理** ] 核取方塊，然後輸入您從「全像」遠端應用程式取得的 IP 位址</span><span class="sxs-lookup"><span data-stu-id="4b035-132">Check the **Holographic Editor Remoting** checkbox and input the IP address you get from the Holographic Remoting app:</span></span>

![在 Unity 編輯器中開啟專案設定面板的螢幕擷取畫面，其中已醒目提示功能](images/openxr-features-img-03.png)

<span data-ttu-id="4b035-134">現在您可以按一下 [播放] 按鈕，以在 HoloLens 上的全像遠端應用程式中播放 Unity 應用程式。</span><span class="sxs-lookup"><span data-stu-id="4b035-134">Now you can click the “Play” button to play your Unity app into the Holographic Remoting app on your HoloLens.</span></span> <span data-ttu-id="4b035-135">您也可以 [將 Visual Studio 附加至 Unity](https://docs.microsoft.com/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows) ，以在播放模式中進行 c # 腳本的調試。</span><span class="sxs-lookup"><span data-stu-id="4b035-135">You can also [attach Visual Studio to Unity](https://docs.microsoft.com/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows) to debug C# scripts in the play mode.</span></span>

> [!NOTE]
> <span data-ttu-id="4b035-136">從0.1.0 的「全像」版本中，執行時間不支援錨定功能，而 ARAnchorManager 功能將無法透過遠端處理。</span><span class="sxs-lookup"><span data-stu-id="4b035-136">As of version 0.1.0 the Holographic Remoting, runtime doesn’t support Anchor feature, and ARAnchorManager functionalities will not work through remoting.</span></span>  <span data-ttu-id="4b035-137">這項功能會在未來的版本中推出。</span><span class="sxs-lookup"><span data-stu-id="4b035-137">This feature is coming in future releases.</span></span>

## <a name="motion-controller-and-hand-interactions"></a><span data-ttu-id="4b035-138">移動控制器和手互動</span><span class="sxs-lookup"><span data-stu-id="4b035-138">Motion controller and hand interactions</span></span>
<span data-ttu-id="4b035-139">若要瞭解 Unity 中混合現實互動的基本概念，請流覽 unity [Manual For UNITY XR 輸入](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html)。</span><span class="sxs-lookup"><span data-stu-id="4b035-139">To learn the basics about mixed reality interactions in Unity, visit the [Unity Manual for Unity XR Input](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html).</span></span> <span data-ttu-id="4b035-140">這項 Unity 檔涵蓋從控制器專屬輸入到更一般化的對應 `InputFeatureUsage` 、如何識別和分類可用的 XR 輸入、如何從這些輸入讀取資料等等。</span><span class="sxs-lookup"><span data-stu-id="4b035-140">This Unity documentation covers the mappings from controller-specific inputs to more generalizable `InputFeatureUsage`s, how available XR inputs can be identified and categorized, how to read data from these inputs, and more.</span></span> 
 
<span data-ttu-id="4b035-141">Mixed Reality OpenXR 外掛程式提供額外的輸入互動設定檔，如下所述，對應至標準 `InputFeatureUsage` s：</span><span class="sxs-lookup"><span data-stu-id="4b035-141">The Mixed Reality OpenXR Plugin provides additional input interaction profiles, mapped to standard `InputFeatureUsage`s as detailed below:</span></span> 
 
| `InputFeatureUsage` | <span data-ttu-id="4b035-142">HP 回音 (OpenXR) </span><span class="sxs-lookup"><span data-stu-id="4b035-142">HP Reverb G2 Controller (OpenXR)</span></span> | <span data-ttu-id="4b035-143">HoloLens (OpenXR) </span><span class="sxs-lookup"><span data-stu-id="4b035-143">HoloLens Hand (OpenXR)</span></span> |
| ---- | ---- | ---- |
| <span data-ttu-id="4b035-144">primary2DAxis</span><span class="sxs-lookup"><span data-stu-id="4b035-144">primary2DAxis</span></span> | <span data-ttu-id="4b035-145">操縱 杆</span><span class="sxs-lookup"><span data-stu-id="4b035-145">Joystick</span></span> | |
| <span data-ttu-id="4b035-146">primary2DAxisClick</span><span class="sxs-lookup"><span data-stu-id="4b035-146">primary2DAxisClick</span></span> | <span data-ttu-id="4b035-147">搖桿-按一下</span><span class="sxs-lookup"><span data-stu-id="4b035-147">Joystick - Click</span></span> | |
| <span data-ttu-id="4b035-148">觸發程序 (trigger)</span><span class="sxs-lookup"><span data-stu-id="4b035-148">trigger</span></span> | <span data-ttu-id="4b035-149">觸發程序</span><span class="sxs-lookup"><span data-stu-id="4b035-149">Trigger</span></span>  | |
| <span data-ttu-id="4b035-150">握</span><span class="sxs-lookup"><span data-stu-id="4b035-150">grip</span></span> | <span data-ttu-id="4b035-151">握</span><span class="sxs-lookup"><span data-stu-id="4b035-151">Grip</span></span> | <span data-ttu-id="4b035-152">點擊或擠壓</span><span class="sxs-lookup"><span data-stu-id="4b035-152">Air tap or squeeze</span></span> |
| <span data-ttu-id="4b035-153">primaryButton</span><span class="sxs-lookup"><span data-stu-id="4b035-153">primaryButton</span></span> | <span data-ttu-id="4b035-154">[X/A]-按下</span><span class="sxs-lookup"><span data-stu-id="4b035-154">[X/A] - Press</span></span> | <span data-ttu-id="4b035-155">空中點選</span><span class="sxs-lookup"><span data-stu-id="4b035-155">Air tap</span></span> |
| <span data-ttu-id="4b035-156">secondaryButton</span><span class="sxs-lookup"><span data-stu-id="4b035-156">secondaryButton</span></span> | <span data-ttu-id="4b035-157">[Y/B]-按下</span><span class="sxs-lookup"><span data-stu-id="4b035-157">[Y/B] - Press</span></span> | |
| <span data-ttu-id="4b035-158">gripButton</span><span class="sxs-lookup"><span data-stu-id="4b035-158">gripButton</span></span> | <span data-ttu-id="4b035-159">握住-按</span><span class="sxs-lookup"><span data-stu-id="4b035-159">Grip - Press</span></span> | |
| <span data-ttu-id="4b035-160">triggerButton</span><span class="sxs-lookup"><span data-stu-id="4b035-160">triggerButton</span></span> | <span data-ttu-id="4b035-161">觸發程式-按下</span><span class="sxs-lookup"><span data-stu-id="4b035-161">Trigger - Press</span></span> | |
| <span data-ttu-id="4b035-162">menuButton</span><span class="sxs-lookup"><span data-stu-id="4b035-162">menuButton</span></span> | <span data-ttu-id="4b035-163">功能表</span><span class="sxs-lookup"><span data-stu-id="4b035-163">Menu</span></span> | |

#### <a name="haptics"></a><span data-ttu-id="4b035-164">Haptics</span><span class="sxs-lookup"><span data-stu-id="4b035-164">Haptics</span></span>
<span data-ttu-id="4b035-165">如需在 Unity 的 XR 輸入系統中使用 haptics 的相關資訊，請參閱 unity [Manual For UNITY XR 輸入-haptics](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html#Haptics)中的檔。</span><span class="sxs-lookup"><span data-stu-id="4b035-165">For information on using haptics in Unity’s XR Input system, documentation can be found at the [Unity Manual for Unity XR Input - Haptics](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html#Haptics).</span></span> 


## <a name="whats-coming-soon"></a><span data-ttu-id="4b035-166">即將推出的內容</span><span class="sxs-lookup"><span data-stu-id="4b035-166">What's coming soon</span></span>

<span data-ttu-id="4b035-167">下列問題和遺漏的功能都是已知的混合現實 OpenXR 外掛程式 **版本 0.1.0**。</span><span class="sxs-lookup"><span data-stu-id="4b035-167">The following issues and missing features are known with Mixed Reality OpenXR plugin **version 0.1.0**.</span></span> <span data-ttu-id="4b035-168">我們正在處理這些問題，並將在即將推出的版本中發行修正程式和新功能。</span><span class="sxs-lookup"><span data-stu-id="4b035-168">We're working on these and will release fixes and new features in upcoming releases.</span></span>

* <span data-ttu-id="4b035-169">尚不支援 **ARPlaneSubsystem** 。</span><span class="sxs-lookup"><span data-stu-id="4b035-169">**ARPlaneSubsystem** is not supported yet.</span></span> <span data-ttu-id="4b035-170">HoloLens 2 也不支援 **ARPlaneManager**、 **ARRaycastManager** 和相關的 API，例如 **ARAnchorManager. AttachAnchor** 。</span><span class="sxs-lookup"><span data-stu-id="4b035-170">**ARPlaneManager**, **ARRaycastManager**, and related API like **ARAnchorManager.AttachAnchor** are also not supported on HoloLens 2.</span></span>
* <span data-ttu-id="4b035-171">目前尚未支援錨點，但不久的未來將會推出 **錨點**。</span><span class="sxs-lookup"><span data-stu-id="4b035-171">**Anchor** isn't supported by Holographic Remoting yet, but it's coming in the near future.</span></span>
* <span data-ttu-id="4b035-172">目前尚不支援手上的 **網格** 追蹤、 **QR 代碼** 和 **XRMeshSubsystem** 。</span><span class="sxs-lookup"><span data-stu-id="4b035-172">**Hand Mesh** tracking, **QR Codes**, and **XRMeshSubsystem** aren't supported yet.</span></span>
* <span data-ttu-id="4b035-173">**Azure 空間錨點** 支援即將在未來版本中推出。</span><span class="sxs-lookup"><span data-stu-id="4b035-173">**Azure Spatial Anchors** support is coming in a future release.</span></span>
* <span data-ttu-id="4b035-174">**ARM64** 是 HoloLens 2 應用程式唯一支援的平臺。</span><span class="sxs-lookup"><span data-stu-id="4b035-174">**ARM64** is the only supported platform for HoloLens 2 apps.</span></span> <span data-ttu-id="4b035-175">**ARM** 平臺即將在未來版本中推出。</span><span class="sxs-lookup"><span data-stu-id="4b035-175">The **ARM** platform is coming in a future release.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="4b035-176">疑難排解</span><span class="sxs-lookup"><span data-stu-id="4b035-176">Troubleshooting</span></span> 

<span data-ttu-id="4b035-177">當您在 HoloLens 2 上暫停和繼續 Unity 應用程式時，應用程式無法正確地繼續，這會導致 HoloLens 視圖中有4個旋轉點。</span><span class="sxs-lookup"><span data-stu-id="4b035-177">When you suspend and resume a Unity app on HoloLens 2, the app can't correctly resume, which leads to 4 spinning dots in the HoloLens view.</span></span> 
* <span data-ttu-id="4b035-178">將 OpenXR 專案設定中的 **深度提交模式** 設定為 [ **無** ] 作為因應措施</span><span class="sxs-lookup"><span data-stu-id="4b035-178">Set **Depth submission Mode** to **None** in the OpenXR project settings as a workaround</span></span>
