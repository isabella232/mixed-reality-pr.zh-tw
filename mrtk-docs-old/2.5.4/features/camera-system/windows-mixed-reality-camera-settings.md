---
title: WindowsMixedRealityCameraSettings
description: 在 MRTK 中使用 Windows Mixed Reality 攝影機的檔
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、攝影機、
ms.openlocfilehash: 46543bce0b542ef3d211b47e2f84ba89627c0ac3
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/03/2021
ms.locfileid: "101779691"
---
# <a name="windows-mixed-reality-camera-settings-provider"></a><span data-ttu-id="eb24e-104">Windows Mixed Reality 攝影機設定提供者</span><span class="sxs-lookup"><span data-stu-id="eb24e-104">Windows Mixed Reality camera settings provider</span></span>

<span data-ttu-id="eb24e-105">Windows Mixed Reality 攝影機設定提供者會決定應用程式執行所在的裝置類型，並根據顯示 (透明或不透明) 來套用適當的設定。</span><span class="sxs-lookup"><span data-stu-id="eb24e-105">The Windows Mixed Reality camera settings provider determines the type of device, upon which the application is running and applies the appropriate configuration settings based on the display (transparent or opaque).</span></span>

## <a name="enabling-the-windows-mixed-reality-camera-settings-provider"></a><span data-ttu-id="eb24e-106">啟用 Windows Mixed Reality 攝影機設定提供者</span><span class="sxs-lookup"><span data-stu-id="eb24e-106">Enabling the Windows Mixed Reality camera settings provider</span></span>

<span data-ttu-id="eb24e-107">下列步驟假設使用 MixedRealityToolkit 物件。</span><span class="sxs-lookup"><span data-stu-id="eb24e-107">The following steps presume use of the MixedRealityToolkit object.</span></span> <span data-ttu-id="eb24e-108">其他服務註冊機構所需的步驟可能會不同。</span><span class="sxs-lookup"><span data-stu-id="eb24e-108">Steps required for other service registrars may be different.</span></span>

1. <span data-ttu-id="eb24e-109">選取場景階層中的 MixedRealityToolkit 物件。</span><span class="sxs-lookup"><span data-stu-id="eb24e-109">Select the MixedRealityToolkit object in the scene hierarchy.</span></span>

    ![MRTK 設定的場景階層](../images/MRTK_ConfiguredHierarchy.png)

2. <span data-ttu-id="eb24e-111">將 [偵測器] 面板移至 [相機系統] 區段，然後展開 [ **相機設定提供者** ] 區段。</span><span class="sxs-lookup"><span data-stu-id="eb24e-111">Navigate the Inspector panel to the camera system section and expand the **Camera Settings Providers** section.</span></span>

    ![展開設定提供者](../images/camera-system/ExpandProviders.png)

3. <span data-ttu-id="eb24e-113">按一下 [新增 **相機設定提供者** ]，並展開新加入的 **新相機設定** 專案。</span><span class="sxs-lookup"><span data-stu-id="eb24e-113">Click **Add Camera Settings Provider** and expand the newly added **New camera settings** entry.</span></span>

    ![展開新的設定提供者](../images/camera-system/ExpandNewProvider.png)

4. <span data-ttu-id="eb24e-115">選取 Windows Mixed Reality 攝影機設定提供者</span><span class="sxs-lookup"><span data-stu-id="eb24e-115">Select the Windows Mixed Reality Camera Settings provider</span></span>

    ![選取 Windows Mixed Reality 設定提供者](../images/camera-system/SelectWindowsMixedRealitySettings.png)

> [!NOTE]
> <span data-ttu-id="eb24e-117">使用 Microsoft Mixed Reality 工具組預設設定檔時，將已啟用並設定 Windows Mixed Reality 攝影機設定提供者。</span><span class="sxs-lookup"><span data-stu-id="eb24e-117">When using the Microsoft Mixed Reality Toolkit default profiles, the Windows Mixed Reality camera settings provider will already be enabled and configured.</span></span>

## <a name="configuring-the-windows-mixed-reality-camera-settings-provider"></a><span data-ttu-id="eb24e-118">設定 Windows Mixed Reality 攝影機設定提供者</span><span class="sxs-lookup"><span data-stu-id="eb24e-118">Configuring the Windows Mixed Reality camera settings provider</span></span>

<span data-ttu-id="eb24e-119">Windows Mixed Reality 攝影機設定也支援設定檔。</span><span class="sxs-lookup"><span data-stu-id="eb24e-119">The Windows Mixed Reality Camera Settings also supports a profile.</span></span> <span data-ttu-id="eb24e-120">此設定檔提供下列選項：</span><span class="sxs-lookup"><span data-stu-id="eb24e-120">This profile provides the following options:</span></span>

![Windows Mixed Reality 攝影機設定設定](../images/camera-system/WMRCameraSettingsProfile.png)

### <a name="render-mixed-reality-capture-from-the-photovideo-camera"></a><span data-ttu-id="eb24e-122">從相片/攝影機轉譯混合現實 capture</span><span class="sxs-lookup"><span data-stu-id="eb24e-122">Render mixed reality capture from the photo/video camera</span></span>

<span data-ttu-id="eb24e-123">使用 HoloLens 2 上的這項設定，您可以在混合現實的捕獲中啟用全像對齊。</span><span class="sxs-lookup"><span data-stu-id="eb24e-123">With this setting on HoloLens 2, you can enable hologram alignment in your mixed reality captures.</span></span> <span data-ttu-id="eb24e-124">如果啟用，平臺會在進行混合現實的拍攝相片或影片時，為應用程式提供額外的 HolographicCamera。</span><span class="sxs-lookup"><span data-stu-id="eb24e-124">If enabled, the platform will provide an additional HolographicCamera to the app when a mixed reality capture photo or video is taken.</span></span> <span data-ttu-id="eb24e-125">此 HolographicCamera 會提供對應至相片/攝影機位置的視圖矩陣，並使用 [相片/攝影機] 欄位提供投射矩陣。</span><span class="sxs-lookup"><span data-stu-id="eb24e-125">This HolographicCamera provides view matrices corresponding to the photo/video camera location, and it provides projection matrices using the photo/video camera field of view.</span></span> <span data-ttu-id="eb24e-126">這可確保在影片輸出中保持一致的全像影像，例如手形網格。</span><span class="sxs-lookup"><span data-stu-id="eb24e-126">This will ensure that holograms, such as hand meshes, remain visibly aligned in the video output.</span></span>

### <a name="hololens-2-reprojection-method"></a><span data-ttu-id="eb24e-127">HoloLens 2 reprojection 方法</span><span class="sxs-lookup"><span data-stu-id="eb24e-127">HoloLens 2 reprojection method</span></span>

<span data-ttu-id="eb24e-128">設定 HoloLens 2 reprojection 的初始方法。</span><span class="sxs-lookup"><span data-stu-id="eb24e-128">Sets the initial method for HoloLens 2 reprojection.</span></span> <span data-ttu-id="eb24e-129">預設的建議是使用深度 reprojection，因為場景的所有部分都會根據與使用者的距離而獨立地穩定。</span><span class="sxs-lookup"><span data-stu-id="eb24e-129">The default recommendation is to use depth reprojection, as all parts of the scene will be independently stabilized based on their distance from the user.</span></span> <span data-ttu-id="eb24e-130">如果不穩定的全像是，請嘗試確保所有物件都已正確地將其深度提交至深度緩衝區。</span><span class="sxs-lookup"><span data-stu-id="eb24e-130">If holograms still appear unstable, try ensuring all objects have properly submitted their depth to the depth buffer.</span></span> <span data-ttu-id="eb24e-131">這有時是著色器設定。</span><span class="sxs-lookup"><span data-stu-id="eb24e-131">This is sometimes a shader setting.</span></span> <span data-ttu-id="eb24e-132">如果深度看似正確提交，而且仍然存在不穩定的情況下，請嘗試使用深度緩衝區來計算穩定平面的 autoplanar 穩定。</span><span class="sxs-lookup"><span data-stu-id="eb24e-132">If depth appears to be properly submitted and instability is still present, try autoplanar stabilization, which uses the depth buffer to calculate a stabilization plane.</span></span> <span data-ttu-id="eb24e-133">如果應用程式無法為其中一個選項提交足夠的深度資料可供使用，則會提供平面 reprojection 做為回復。</span><span class="sxs-lookup"><span data-stu-id="eb24e-133">If an app is unable to submit enough depth data for either of those options to be usable, planar reprojection is provided as a fallback.</span></span> <span data-ttu-id="eb24e-134">這個方法會以應用程式透過 [SetFocusPointForFrame](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.SetFocusPointForFrame.html)提供的焦點資料為基礎。</span><span class="sxs-lookup"><span data-stu-id="eb24e-134">This method will be based on an app's provided focus point data via [SetFocusPointForFrame](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.SetFocusPointForFrame.html).</span></span>

<span data-ttu-id="eb24e-135">若要在執行時間更新 reprojection 方法，請存取， `WindowsMixedRealityReprojectionUpdater` 如下所示：</span><span class="sxs-lookup"><span data-stu-id="eb24e-135">To update the reprojection method at runtime, access the `WindowsMixedRealityReprojectionUpdater` like so:</span></span>

```c#
var reprojectionUpdater = CameraCache.Main.EnsureComponent<WindowsMixedRealityReprojectionUpdater>();
reprojectionUpdater.ReprojectionMethod = HolographicDepthReprojectionMethod.AutoPlanar;
```

<span data-ttu-id="eb24e-136">這只需要更新一次，而且會針對所有後續的框架重複使用該值。</span><span class="sxs-lookup"><span data-stu-id="eb24e-136">This only needs to be updated once and the value is reused for all subsequent frames.</span></span> <span data-ttu-id="eb24e-137">如果方法會經常更新，建議您快取的結果， `EnsureComponent` 而不是經常呼叫它。</span><span class="sxs-lookup"><span data-stu-id="eb24e-137">If the method will be updated frequently, it's recommended to cache the result of `EnsureComponent` instead of calling it often.</span></span>

## <a name="see-also"></a><span data-ttu-id="eb24e-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eb24e-138">See also</span></span>

- [<span data-ttu-id="eb24e-139">攝影機系統總覽</span><span class="sxs-lookup"><span data-stu-id="eb24e-139">Camera System Overview</span></span>](camera-system-overview.md)
- [<span data-ttu-id="eb24e-140">建立相機設定提供者</span><span class="sxs-lookup"><span data-stu-id="eb24e-140">Creating a Camera Settings Provider</span></span>](create-settings-provider.md)
- [<span data-ttu-id="eb24e-141">從 PV 攝影機轉譯混合現實 Capture</span><span class="sxs-lookup"><span data-stu-id="eb24e-141">Rendering Mixed Reality Capture from the PV camera</span></span>](https://docs.microsoft.com/windows/mixed-reality/mixed-reality-capture-for-developers#render-from-the-pv-camera-opt-in)
- [<span data-ttu-id="eb24e-142">全像 reprojection</span><span class="sxs-lookup"><span data-stu-id="eb24e-142">Holographic reprojection</span></span>](https://docs.microsoft.com/windows/mixed-reality/hologram-stability#reprojection)
