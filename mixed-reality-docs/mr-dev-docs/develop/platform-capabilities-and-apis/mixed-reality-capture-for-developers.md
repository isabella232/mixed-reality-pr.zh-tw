---
title: 適用于開發人員的混合現實 capture
description: 瞭解為開發人員啟用、使用和轉譯混合現實 capture 的最佳作法。
author: mattzmsft
ms.author: mazeller
ms.date: 02/24/2019
ms.topic: article
keywords: mrc、相片、影片、捕捉、攝影機
ms.openlocfilehash: ec1a53d2f623a8047c2ee1973d8d6f20458ade88
ms.sourcegitcommit: c65759b8d6465b6b13925cacab5af74443f7e6bd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/15/2021
ms.locfileid: "112110249"
---
# <a name="mixed-reality-capture-for-developers"></a><span data-ttu-id="11d8d-104">適用于開發人員的混合現實 capture</span><span class="sxs-lookup"><span data-stu-id="11d8d-104">Mixed reality capture for developers</span></span>

> [!NOTE]
> <span data-ttu-id="11d8d-105">請參閱下面 [的 PV 攝影機](#render-from-the-pv-camera-opt-in) 轉譯，以取得 HoloLens 2 新的 MRC 功能的指引。</span><span class="sxs-lookup"><span data-stu-id="11d8d-105">See [Render from the PV camera](#render-from-the-pv-camera-opt-in) below for guidance on a new MRC capability for HoloLens 2.</span></span>

<span data-ttu-id="11d8d-106">您可以隨時 (的) 相片或影片進行 [混合的現實 capture](/hololens/holographic-photos-and-videos) ，但在開發應用程式時，請記住幾件事。</span><span class="sxs-lookup"><span data-stu-id="11d8d-106">You can take a [mixed reality capture](/hololens/holographic-photos-and-videos) (MRC) photo or video at any time, but there are few things to keep in mind when developing your application.</span></span> <span data-ttu-id="11d8d-107">這包括了 MRC 視覺品質的最佳作法，並在 MRCs 時回應系統變更。</span><span class="sxs-lookup"><span data-stu-id="11d8d-107">This includes best practices for MRC visual quality and being responsive to system changes while MRCs are being captured.</span></span>

<span data-ttu-id="11d8d-108">開發人員也可以將混合現實的捕獲和插入順暢地整合到他們的應用程式中。</span><span class="sxs-lookup"><span data-stu-id="11d8d-108">Developers can also seamlessly integrate mixed reality capture and insertion into their apps.</span></span>

<span data-ttu-id="11d8d-109">HoloLens (第一代) 支援最高720p 的影片和相片，而 HoloLens 2 上的 MRC 可支援最高1080p 和最高4K 解析度的影像。</span><span class="sxs-lookup"><span data-stu-id="11d8d-109">MRC on HoloLens (first-generation) supports videos and photos up to 720p, while MRC on HoloLens 2 supports videos up to 1080p and photos up to 4K resolution.</span></span>

## <a name="the-importance-of-quality-mrc"></a><span data-ttu-id="11d8d-110">品質 MRC 的重要性</span><span class="sxs-lookup"><span data-stu-id="11d8d-110">The importance of quality MRC</span></span>

<span data-ttu-id="11d8d-111">無論是 Microsoft Store 頁面上的混合現實螢幕擷取畫面，還是在社交網路上共用捕捉內容的其他使用者，混合實境擷取媒體通常是使用者首次暴露于您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="11d8d-111">Whether it's mixed reality screenshots on your Microsoft Store page or other users sharing capture content on social networks, Mixed Reality Capture media is often a users first exposure to your app.</span></span> <span data-ttu-id="11d8d-112">您可以使用 MRC 來示範您的應用程式、教育使用者、鼓勵使用者共用其混合的世界互動，以及進行使用者研究和解決問題。</span><span class="sxs-lookup"><span data-stu-id="11d8d-112">You can use MRC to demo your app, educate users, encourage users to share their mixed world interactions, and for user research and problem solving.</span></span>

## <a name="how-mrc-impacts-your-app"></a><span data-ttu-id="11d8d-113">MRC 如何影響您的應用程式</span><span class="sxs-lookup"><span data-stu-id="11d8d-113">How MRC impacts your app</span></span>

### <a name="enabling-mrc-in-your-app"></a><span data-ttu-id="11d8d-114">在您的應用程式中啟用 MRC</span><span class="sxs-lookup"><span data-stu-id="11d8d-114">Enabling MRC in your app</span></span>

<span data-ttu-id="11d8d-115">根據預設，應用程式不需要執行任何動作，就能讓使用者採用混合的事實捕獲。</span><span class="sxs-lookup"><span data-stu-id="11d8d-115">By default, an app doesn't have to do anything to enable users to take mixed reality captures.</span></span>

### <a name="enabling-improved-alignment-for-mrc-in-your-app"></a><span data-ttu-id="11d8d-116">為您應用程式中的 MRC 啟用改良的對齊</span><span class="sxs-lookup"><span data-stu-id="11d8d-116">Enabling improved alignment for MRC in your app</span></span>

<span data-ttu-id="11d8d-117">依預設，mixed reality capture 會將適當的眼睛全像影像輸出與相片/影片 (PV) 攝影機。</span><span class="sxs-lookup"><span data-stu-id="11d8d-117">By default, mixed reality capture combines the right eye's holographic output with the photo/video (PV) camera.</span></span> <span data-ttu-id="11d8d-118">這兩個來源會使用目前執行的沉浸式應用程式所設定的焦點點來合併。</span><span class="sxs-lookup"><span data-stu-id="11d8d-118">These two sources are combined using the focus point set by the currently running immersive app.</span></span>

<span data-ttu-id="11d8d-119">這表示焦點平面以外的全像全像，不會因為 PV 攝影機和右邊顯示器之間的實體距離而對齊。</span><span class="sxs-lookup"><span data-stu-id="11d8d-119">This means that holograms outside the focus plane won't align because of the physical distance between the PV camera and the right display.</span></span>

#### <a name="set-the-focus-point"></a><span data-ttu-id="11d8d-120">設定焦點點</span><span class="sxs-lookup"><span data-stu-id="11d8d-120">Set the focus point</span></span>

<span data-ttu-id="11d8d-121">在) HoloLens 上 (的沉浸式應用程式，應該將其穩定平面的 [焦點放](../unity/focus-point-in-unity.md) 在您要的位置。</span><span class="sxs-lookup"><span data-stu-id="11d8d-121">Immersive apps (on HoloLens) should set the [focus point](../unity/focus-point-in-unity.md) of where they want their stabilization plane to be.</span></span> <span data-ttu-id="11d8d-122">這可確保耳機和混合式現實捕捉中的最佳對齊。</span><span class="sxs-lookup"><span data-stu-id="11d8d-122">This ensures the best alignment in both the headset and in mixed reality capture.</span></span>

<span data-ttu-id="11d8d-123">如果未設定焦點點，穩定平面會預設為2個計量。</span><span class="sxs-lookup"><span data-stu-id="11d8d-123">If a focus point isn't set, the stabilization plane will default to 2 meters.</span></span>

#### <a name="render-from-the-pv-camera-opt-in"></a><span data-ttu-id="11d8d-124">從 PV 攝影機轉譯 (加入宣告) </span><span class="sxs-lookup"><span data-stu-id="11d8d-124">Render from the PV camera (opt-in)</span></span>

<span data-ttu-id="11d8d-125">HoloLens 2 新增了當混合的現實捕捉正在執行時，可讓沉浸式應用程式 **從 PV 攝影機** 轉譯的功能。</span><span class="sxs-lookup"><span data-stu-id="11d8d-125">HoloLens 2 adds the ability for an immersive app to **render from the PV camera** while mixed reality capture is running.</span></span> <span data-ttu-id="11d8d-126">為了確保應用程式能夠正確地支援其他轉譯，應用程式必須加入宣告這項功能。</span><span class="sxs-lookup"><span data-stu-id="11d8d-126">To ensure the app supports the additional render correctly, the app has to opt in to this functionality.</span></span>

<span data-ttu-id="11d8d-127">從 PV 攝影機轉譯可針對預設的 MRC 體驗提供下列改良功能：</span><span class="sxs-lookup"><span data-stu-id="11d8d-127">Render from the PV camera offers the following improvements over the default MRC experience:</span></span>
* <span data-ttu-id="11d8d-128">全像您的實體環境的全息圖對齊，而手近距離的互動應該都是正確的。</span><span class="sxs-lookup"><span data-stu-id="11d8d-128">Hologram alignment to your physical environment and hands for near interactions should be accurate at all distances.</span></span> <span data-ttu-id="11d8d-129">避免在焦點點（而非焦點點）之間有位移，如您在預設的 MRC 中所見。</span><span class="sxs-lookup"><span data-stu-id="11d8d-129">Avoid having an offset at distances other than the focus point as you might see in the default MRC.</span></span>
* <span data-ttu-id="11d8d-130">耳機中的適當眼睛不會遭到入侵，因為它不會用來呈現 MRC 輸出的全像影像。</span><span class="sxs-lookup"><span data-stu-id="11d8d-130">The right eye in the headset won't be compromised, as it won't be used to render the holograms for the MRC output.</span></span>

<span data-ttu-id="11d8d-131">有三個步驟可讓您從 PV 攝影機進行轉譯：</span><span class="sxs-lookup"><span data-stu-id="11d8d-131">There are three steps to enable rendering from the PV camera:</span></span>
1. <span data-ttu-id="11d8d-132">啟用 PhotoVideoCamera HolographicViewConfiguration</span><span class="sxs-lookup"><span data-stu-id="11d8d-132">Enable the PhotoVideoCamera HolographicViewConfiguration</span></span>
2. <span data-ttu-id="11d8d-133">處理其他 HolographicCamera 轉譯</span><span class="sxs-lookup"><span data-stu-id="11d8d-133">Handle the additional HolographicCamera render</span></span>
3. <span data-ttu-id="11d8d-134">從這個額外的 HolographicCamera 確認您的著色器和程式碼轉譯正確</span><span class="sxs-lookup"><span data-stu-id="11d8d-134">Verify your shaders and code render correctly from this additional HolographicCamera</span></span>

##### <a name="enable-the-photovideocamera-holographicviewconfiguration-in-directx"></a><span data-ttu-id="11d8d-135">啟用 DirectX 中的 PhotoVideoCamera HolographicViewConfiguration</span><span class="sxs-lookup"><span data-stu-id="11d8d-135">Enable the PhotoVideoCamera HolographicViewConfiguration in DirectX</span></span>

<span data-ttu-id="11d8d-136">若要選擇從 PV 攝影機轉譯，應用程式只會啟用 PhotoVideoCamera 的 [HolographicViewConfiguration](/uwp/api/Windows.Graphics.Holographic.HolographicViewConfiguration)：</span><span class="sxs-lookup"><span data-stu-id="11d8d-136">To opt in to rendering from the PV Camera, an app simply enables the PhotoVideoCamera's [HolographicViewConfiguration](/uwp/api/Windows.Graphics.Holographic.HolographicViewConfiguration):</span></span>
```csharp
var display = Windows.Graphics.Holographic.HolographicDisplay.GetDefault();
var view = display.TryGetViewConfiguration(Windows.Graphics.Holographic.HolographicViewConfigurationKind.PhotoVideoCamera);
if (view != null)
{
    view.IsEnabled = true;
}
```

##### <a name="handle-the-additional-holographiccamera-render-in-directx"></a><span data-ttu-id="11d8d-137">處理 DirectX 中的其他 HolographicCamera 轉譯</span><span class="sxs-lookup"><span data-stu-id="11d8d-137">Handle the additional HolographicCamera render in DirectX</span></span>

<span data-ttu-id="11d8d-138">當應用程式已從 PV 攝影機加入宣告，且混合現實捕捉開始時：</span><span class="sxs-lookup"><span data-stu-id="11d8d-138">When the app has opt-in to render from the PV camera and mixed reality capture starts:</span></span>
1. <span data-ttu-id="11d8d-139">將引發 HolographicSpace 的 CameraAdded 事件。</span><span class="sxs-lookup"><span data-stu-id="11d8d-139">HolographicSpace's CameraAdded event will fire.</span></span> <span data-ttu-id="11d8d-140">如果應用程式目前無法處理相機，則可以延後此事件。</span><span class="sxs-lookup"><span data-stu-id="11d8d-140">This event can be deferred if the app can't handle the camera at this time.</span></span>
2. <span data-ttu-id="11d8d-141">一旦完成事件且沒有未完成的延期，HolographicCamera 將會出現在下一個 HolographicFrame 的 AddedCameras 清單中。</span><span class="sxs-lookup"><span data-stu-id="11d8d-141">Once the event has completed with no outstanding deferrals, the HolographicCamera will appear in the next HolographicFrame's AddedCameras list.</span></span>

<span data-ttu-id="11d8d-142">當混合式事實 capture (停止，或應用程式在混合式事實捕捉正在執行時停用 view 設定) ： HolographicCamera 將會出現在下一個 HolographicFrame 的 RemovedCameras 清單中，而且 HolographicSpace 的 CameraRemoved 事件將會引發。</span><span class="sxs-lookup"><span data-stu-id="11d8d-142">When mixed reality capture stops (or if the app disables the view configuration while mixed reality capture is running): the HolographicCamera will appear in the next HolographicFrame's RemovedCameras list and the HolographicSpace's CameraRemoved event will fire.</span></span>

<span data-ttu-id="11d8d-143">已將 [ViewConfiguration](/uwp/api/windows.graphics.holographic.holographiccamera.viewconfiguration) 屬性新增至 HolographicCamera，以協助識別相機所屬的設定。</span><span class="sxs-lookup"><span data-stu-id="11d8d-143">A [ViewConfiguration](/uwp/api/windows.graphics.holographic.holographiccamera.viewconfiguration) property has been added to HolographicCamera to help identify the configuration a camera belongs to.</span></span>

##### <a name="enable-the-photovideocamera-holographicviewconfiguration-in-unity"></a><span data-ttu-id="11d8d-144">在 Unity 中啟用 PhotoVideoCamera HolographicViewConfiguration</span><span class="sxs-lookup"><span data-stu-id="11d8d-144">Enable the PhotoVideoCamera HolographicViewConfiguration in Unity</span></span>

> [!NOTE]
> <span data-ttu-id="11d8d-145">如果您使用的是 Unity 2018，則需要 **unity 2018.4.13 f1** 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="11d8d-145">If you're using Unity 2018, this requires **Unity 2018.4.13f1** or newer.</span></span> <span data-ttu-id="11d8d-146">如果您使用的是 Unity 2019，則需要 **unity 2019.4** 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="11d8d-146">If you're using Unity 2019, this requires **Unity 2019.4**, or newer.</span></span>

<span data-ttu-id="11d8d-147">若要在使用 [Mixed Reality 工具](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)組時選擇從 pv 攝影機進行轉譯，請啟用 [Windows Mixed Reality 攝影機設定](/windows/mixed-reality/mrtk-unity/features/camera-system/windows-mixed-reality-camera-settings) 提供者，並檢查 **從 pv 攝影機** 轉譯。</span><span class="sxs-lookup"><span data-stu-id="11d8d-147">To opt in to rendering from the PV Camera when using the [Mixed Reality Toolkit](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html), enable the [Windows Mixed Reality Camera Settings](/windows/mixed-reality/mrtk-unity/features/camera-system/windows-mixed-reality-camera-settings) provider and check **Render from PV Camera**.</span></span>

<span data-ttu-id="11d8d-148">如果您不是使用「混合現實」工具組，您可以使用元件以 [手動方式加入宣告](#enable-the-photovideocamera-holographicviewconfiguration-in-directx) ，如上面的 DirectX 所述。</span><span class="sxs-lookup"><span data-stu-id="11d8d-148">If you're not using the Mixed Reality Toolkit, you can use a component to [manually opt-in](#enable-the-photovideocamera-holographicviewconfiguration-in-directx) as described above for DirectX.</span></span>

##### <a name="handle-the-additional-holographiccamera-render-in-unity"></a><span data-ttu-id="11d8d-149">處理 Unity 中的其他 HolographicCamera 轉譯</span><span class="sxs-lookup"><span data-stu-id="11d8d-149">Handle the additional HolographicCamera render in Unity</span></span>

<span data-ttu-id="11d8d-150">Unity 會自動為您完成這項操作。</span><span class="sxs-lookup"><span data-stu-id="11d8d-150">This is done for you automatically by Unity.</span></span>

##### <a name="enable-the-photovideocamera-holographicviewconfiguration-in-unreal"></a><span data-ttu-id="11d8d-151">在 Unreal 中啟用 PhotoVideoCamera HolographicViewConfiguration</span><span class="sxs-lookup"><span data-stu-id="11d8d-151">Enable the PhotoVideoCamera HolographicViewConfiguration in Unreal</span></span>

> [!NOTE]
> <span data-ttu-id="11d8d-152">這需要 **Unreal Engine 4.25** 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="11d8d-152">This requires **Unreal Engine 4.25** or newer.</span></span>

<span data-ttu-id="11d8d-153">若要選擇從 PV 相機呈現：</span><span class="sxs-lookup"><span data-stu-id="11d8d-153">To opt in to rendering from the PV Camera:</span></span>

1. <span data-ttu-id="11d8d-154">呼叫 **SetEnabledMixedRealityCamera** 和 **ResizeMixedRealityCamera**</span><span class="sxs-lookup"><span data-stu-id="11d8d-154">Call **SetEnabledMixedRealityCamera** and **ResizeMixedRealityCamera**</span></span>
    * <span data-ttu-id="11d8d-155">使用 **Size X** 和 **Size Y** 值來設定影片大小。</span><span class="sxs-lookup"><span data-stu-id="11d8d-155">Use the **Size X** and **Size Y** values to set the video dimensions.</span></span>

![第三相機](images/unreal-camera-3rd.PNG)

##### <a name="handle-the-additional-holographiccamera-render-in-unreal"></a><span data-ttu-id="11d8d-157">處理 Unreal 中的其他 HolographicCamera 轉譯</span><span class="sxs-lookup"><span data-stu-id="11d8d-157">Handle the additional HolographicCamera render in Unreal</span></span>

<span data-ttu-id="11d8d-158">Unreal 會自動為您完成這項操作。</span><span class="sxs-lookup"><span data-stu-id="11d8d-158">This is done for you automatically by Unreal.</span></span>

##### <a name="verify-shaders-and-code-support-additional-cameras"></a><span data-ttu-id="11d8d-159">確認著色器和程式碼支援其他攝影機</span><span class="sxs-lookup"><span data-stu-id="11d8d-159">Verify shaders and code support additional cameras</span></span>

<span data-ttu-id="11d8d-160">執行混合現實的捕獲，並檢查是否有不尋常的對齊、遺漏內容或效能問題。</span><span class="sxs-lookup"><span data-stu-id="11d8d-160">Run a mixed reality capture and check for unusual alignment, missing content, or performance issues.</span></span> <span data-ttu-id="11d8d-161">適當地更新著色器和程式碼。</span><span class="sxs-lookup"><span data-stu-id="11d8d-161">Update shaders and code as appropriate.</span></span>

<span data-ttu-id="11d8d-162">如果有某些場景無法支援轉譯成其他相機，您可以停用 PhotoVideoCamera 的 HolographicViewConfiguration。</span><span class="sxs-lookup"><span data-stu-id="11d8d-162">If there are certain scenes that can't support rendering to an additional camera, you can disable the PhotoVideoCamera's HolographicViewConfiguration.</span></span>

### <a name="disabling-mrc-in-your-app"></a><span data-ttu-id="11d8d-163">在您的應用程式中停用 MRC</span><span class="sxs-lookup"><span data-stu-id="11d8d-163">Disabling MRC in your app</span></span>

#### <a name="2d-app"></a><span data-ttu-id="11d8d-164">2D 應用程式</span><span class="sxs-lookup"><span data-stu-id="11d8d-164">2D app</span></span>

<span data-ttu-id="11d8d-165">當混合的現實捕捉正在執行時，2D 應用程式可以選擇將其視覺內容遮蔽：</span><span class="sxs-lookup"><span data-stu-id="11d8d-165">2D apps can choose to have their visual content obscured when mixed reality capture is running by:</span></span>
* <span data-ttu-id="11d8d-166">以 [DXGI_PRESENT_RESTRICT_TO_OUTPUT](/windows/desktop/direct3ddxgi/dxgi-present) 旗標呈現</span><span class="sxs-lookup"><span data-stu-id="11d8d-166">Present with the [DXGI_PRESENT_RESTRICT_TO_OUTPUT](/windows/desktop/direct3ddxgi/dxgi-present) flag</span></span>
* <span data-ttu-id="11d8d-167">使用 [DXGI_SWAP_CHAIN_FLAG_HW_PROTECTED](/windows/desktop/api/dxgi/ne-dxgi-dxgi_swap_chain_flag) 旗標來建立應用程式的交換鏈</span><span class="sxs-lookup"><span data-stu-id="11d8d-167">Create the app's swap chain with the [DXGI_SWAP_CHAIN_FLAG_HW_PROTECTED](/windows/desktop/api/dxgi/ne-dxgi-dxgi_swap_chain_flag) flag</span></span>
* <span data-ttu-id="11d8d-168">使用 Windows 10 2019 年5月更新，設定 ApplicationView 的 [IsScreenCaptureEnabled](/uwp/api/windows.ui.viewmanagement.applicationview.isscreencaptureenabled)</span><span class="sxs-lookup"><span data-stu-id="11d8d-168">With the Windows 10 May 2019 Update, setting ApplicationView's [IsScreenCaptureEnabled](/uwp/api/windows.ui.viewmanagement.applicationview.isscreencaptureenabled)</span></span>

#### <a name="immersive-app"></a><span data-ttu-id="11d8d-169">沉浸式應用程式</span><span class="sxs-lookup"><span data-stu-id="11d8d-169">Immersive app</span></span>

<span data-ttu-id="11d8d-170">沉浸式應用程式可以選擇從混合現實捕捉中排除其視覺內容：</span><span class="sxs-lookup"><span data-stu-id="11d8d-170">Immersive apps can choose to have their visual content excluded from mixed reality capture by:</span></span>
* <span data-ttu-id="11d8d-171">設定 HolographicCameraRenderingParameter 的 [IsContentProtectionEnabled](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.iscontentprotectionenabled) ，以停用其相關聯框架的混合現實 capture</span><span class="sxs-lookup"><span data-stu-id="11d8d-171">Setting HolographicCameraRenderingParameter's [IsContentProtectionEnabled](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.iscontentprotectionenabled) to disable mixed reality capture for its associated frame</span></span>
* <span data-ttu-id="11d8d-172">設定 HolographicCamera 的 [IsHardwareContentProtectionEnabled](/uwp/api/windows.graphics.holographic.holographiccamera.ishardwarecontentprotectionenabled) ，以停用其相關聯的全像攝影相機的混合現實 capture</span><span class="sxs-lookup"><span data-stu-id="11d8d-172">Setting HolographicCamera's [IsHardwareContentProtectionEnabled](/uwp/api/windows.graphics.holographic.holographiccamera.ishardwarecontentprotectionenabled) to disable mixed reality capture for its associated holographic camera</span></span>

#### <a name="password-keyboard"></a><span data-ttu-id="11d8d-173">密碼鍵盤</span><span class="sxs-lookup"><span data-stu-id="11d8d-173">Password Keyboard</span></span>

<span data-ttu-id="11d8d-174">使用 Windows 10 2019 年5月更新，在顯示密碼或 pin 鍵盤時，會自動從混合現實捕獲中排除視覺內容。</span><span class="sxs-lookup"><span data-stu-id="11d8d-174">With the Windows 10 May 2019 Update, visual content is automatically excluded from mixed reality capture when a password or pin keyboard is visible.</span></span>

### <a name="knowing-when-mrc-is-active"></a><span data-ttu-id="11d8d-175">知道當 MRC 處於作用中狀態</span><span class="sxs-lookup"><span data-stu-id="11d8d-175">Knowing when MRC is active</span></span>

<span data-ttu-id="11d8d-176">[AppCapture](/uwp/api/Windows.Media.Capture.AppCapture)類別可供應用程式用來知道系統 mixed reality capture (針對音訊或影片) 執行時。</span><span class="sxs-lookup"><span data-stu-id="11d8d-176">The [AppCapture](/uwp/api/Windows.Media.Capture.AppCapture) class can be used by an app to know when system mixed reality capture is running (for either audio or video).</span></span>

>[!NOTE]
><span data-ttu-id="11d8d-177">如果裝置上沒有混合現實 capture，AppCapture 的 [GetForCurrentView](/uwp/api/windows.media.capture.appcapture.getforcurrentview) API 可能會傳回 null。</span><span class="sxs-lookup"><span data-stu-id="11d8d-177">AppCapture's [GetForCurrentView](/uwp/api/windows.media.capture.appcapture.getforcurrentview) API can return null if mixed reality capture isn't available on the device.</span></span> <span data-ttu-id="11d8d-178">也請務必在您的應用程式暫停時，取消註冊 CapturingChanged 事件，否則，可能會進入封鎖狀態。</span><span class="sxs-lookup"><span data-stu-id="11d8d-178">It's also important to de-register the CapturingChanged event when your app is suspended, otherwise MRC can get into a blocked state.</span></span>

### <a name="best-practices-hololens-specific"></a><span data-ttu-id="11d8d-179"> (HoloLens 專用) 的最佳作法</span><span class="sxs-lookup"><span data-stu-id="11d8d-179">Best practices (HoloLens-specific)</span></span>

<span data-ttu-id="11d8d-180">在不需要其他開發工作的情況下，必須留意到 MRC 的工作，但在提供最佳的混合現實捕獲經驗時，有幾件事要注意。</span><span class="sxs-lookup"><span data-stu-id="11d8d-180">MRC is expected to work without additional development effort, but there are a few things to be aware of when providing the best mixed reality capture experience.</span></span>

<span data-ttu-id="11d8d-181">**MRC 使用全像 [相機](locatable-camera.md) 的 Alpha 色板來 blend 影像**</span><span class="sxs-lookup"><span data-stu-id="11d8d-181">**MRC uses the hologram’s alpha channel to blend with the [camera](locatable-camera.md) imagery**</span></span>

<span data-ttu-id="11d8d-182">最重要的步驟是確保您的應用程式會清除為透明黑色，而不是清除為不透明的黑色。</span><span class="sxs-lookup"><span data-stu-id="11d8d-182">The most important step is to make sure your app is clearing to transparent black instead of clearing to opaque black.</span></span> <span data-ttu-id="11d8d-183">在 Unity 中，這會依預設使用 MixedRealityToolkit 來完成。</span><span class="sxs-lookup"><span data-stu-id="11d8d-183">In Unity, this is done by default with the MixedRealityToolkit.</span></span> <span data-ttu-id="11d8d-184">如果您是在非 Unity 中進行開發，您可能需要進行一行變更。</span><span class="sxs-lookup"><span data-stu-id="11d8d-184">If you're developing in non-Unity, you may need to make a one line change.</span></span>

<span data-ttu-id="11d8d-185">如果您的應用程式未清除為透明黑色，您可能會在 MRC 中看到一些成品：</span><span class="sxs-lookup"><span data-stu-id="11d8d-185">Here are some of the artifacts you might see in MRC if your app isn't clearing to transparent black:</span></span>

<span data-ttu-id="11d8d-186">**範例失敗**：內容周圍的黑色邊緣 (無法清除為透明黑色) </span><span class="sxs-lookup"><span data-stu-id="11d8d-186">**Example Failures**: Black edges around the content (failing to clear to transparent black)</span></span>

<table>
<tr>
<td>
<img src="images/chessboardblackedges-300px.jpg" alt="Failure to clear to transparent black: black edge artifacts around holograms"/>
</td>
<td>
<img src="images/fieldblackedges-300px.jpg" alt="Failing to clear to transparent black: black edge artifacts around holograms"/>
</td>
</tr>
</table>

<span data-ttu-id="11d8d-187">**失敗範例**：全像全像全螢幕的背景場景會顯示黑色。</span><span class="sxs-lookup"><span data-stu-id="11d8d-187">**Example Failures**: The entire background scene of the hologram appears black.</span></span> <span data-ttu-id="11d8d-188">在黑色背景中設定一個結果的背景 Alpha 值</span><span class="sxs-lookup"><span data-stu-id="11d8d-188">Setting a background alpha value of one results in a black background</span></span>

![將背景 Alpha 值設定為1會導致黑色背景](images/clearopaqueblack-300px.png)

<span data-ttu-id="11d8d-190">**預期的結果**：如果清除透明) 黑色，則會以真實世界 (預期的結果來適當地混合影像：</span><span class="sxs-lookup"><span data-stu-id="11d8d-190">**Expected Result**: Holograms appear properly blended with the real-world (expected result if clearing to transparent black)</span></span>

![如果清除透明黑色，則預期的結果](images/cleartransparentblack-300px.png)

<span data-ttu-id="11d8d-192">**解決方案**：</span><span class="sxs-lookup"><span data-stu-id="11d8d-192">**Solution**:</span></span>
* <span data-ttu-id="11d8d-193">將顯示為不透明黑色的任何內容變更為具有 Alpha 值0。</span><span class="sxs-lookup"><span data-stu-id="11d8d-193">Change any content that is showing up as opaque black to have an alpha value of 0.</span></span>
* <span data-ttu-id="11d8d-194">確定應用程式已清除為透明的黑色。</span><span class="sxs-lookup"><span data-stu-id="11d8d-194">Ensure that the app is clearing to transparent black.</span></span>
* <span data-ttu-id="11d8d-195">Unity 預設會自動使用 MixedRealityToolkit 來清除，但如果它是非 Unity 應用程式，則您應該修改與 ID3D11DeiceCoNtext：： ClearRenderTargetView () 搭配使用的色彩。</span><span class="sxs-lookup"><span data-stu-id="11d8d-195">Unity defaults to clear automatically with the MixedRealityToolkit, but if it’s a non-Unity app you should modify the color used with ID3D11DeiceContext::ClearRenderTargetView().</span></span> <span data-ttu-id="11d8d-196">您想要確保清楚透明的黑色 (0、0、0、0) ，而不是不透明的黑色 (0、0、0、1) 。</span><span class="sxs-lookup"><span data-stu-id="11d8d-196">You want to ensure you clear to transparent black (0,0,0,0) instead of opaque black (0,0,0,1).</span></span>

<span data-ttu-id="11d8d-197">如果您想要的話，現在可以調整資產的 Alpha 值，但通常不需要這麼做。</span><span class="sxs-lookup"><span data-stu-id="11d8d-197">You can now tune the alpha values of your assets if you’d like, but typically don’t need to.</span></span> <span data-ttu-id="11d8d-198">大部分的情況下，MRCs 都看起來不錯。</span><span class="sxs-lookup"><span data-stu-id="11d8d-198">Most of the time, MRCs will look good out of the box.</span></span> <span data-ttu-id="11d8d-199">MRC 假設預乘 Alpha。</span><span class="sxs-lookup"><span data-stu-id="11d8d-199">MRC assumes pre-multiplied alpha.</span></span> <span data-ttu-id="11d8d-200">Alpha 值只會影響 MRC 捕捉。</span><span class="sxs-lookup"><span data-stu-id="11d8d-200">The alpha values will only affect the MRC capture.</span></span>

### <a name="what-to-expect-when-mrc-is-enabled-on-hololens"></a><span data-ttu-id="11d8d-201">HoloLens 在 HoloLens 上啟用時的預期結果</span><span class="sxs-lookup"><span data-stu-id="11d8d-201">What to expect when MRC is enabled on HoloLens</span></span>

<span data-ttu-id="11d8d-202">下列適用于 HoloLens (第一代) 和 HoloLens 2，除非另有注明：</span><span class="sxs-lookup"><span data-stu-id="11d8d-202">The following apply to both HoloLens (first-generation) and HoloLens 2, unless otherwise noted:</span></span>

* <span data-ttu-id="11d8d-203">系統會將應用程式節流至 30-Hz 轉譯。</span><span class="sxs-lookup"><span data-stu-id="11d8d-203">The system will throttle the application to 30-Hz rendering.</span></span> <span data-ttu-id="11d8d-204">這會建立一些可供 MRC 執行的空間，因此應用程式不需要保留固定的預算保留，也不需要符合每 30 fps 的 MRC 影片記錄幀率</span><span class="sxs-lookup"><span data-stu-id="11d8d-204">This creates some headroom for MRC to run so the app doesn’t need to keep a constant budget reserve and also matches the MRC video record framerate of 30 fps</span></span>
* <span data-ttu-id="11d8d-205">錄製/串流處理常式時，裝置上的全息圖內容可能會顯示為「閃爍」：文字可能會變得更難閱讀，而全息圖邊緣可能會變得更 jaggy (選擇在 **HoloLens 2** 上進行第三個攝影機轉譯，以避免此折衷) </span><span class="sxs-lookup"><span data-stu-id="11d8d-205">Hologram content in the right eye of the device may appear to “sparkle” when recording/streaming MRC: text may become more difficult to read and hologram edges may appear more jaggy (opting in to third camera render on **HoloLens 2** avoids this compromise)</span></span>
* <span data-ttu-id="11d8d-206">如果應用程式已啟用，則 MRC 照片和影片將會遵循應用程式的 [焦點點](../unity/focus-point-in-unity.md) ，以協助確保全像投影正確放置。</span><span class="sxs-lookup"><span data-stu-id="11d8d-206">MRC photos and videos will respect the application’s [focus point](../unity/focus-point-in-unity.md) if the application has enabled it, which will help ensure holograms are accurately positioned.</span></span> <span data-ttu-id="11d8d-207">針對影片，焦點會經過平滑處理，如此一來，如果焦點深度的變更大幅改變，則可能會出現緩慢的漂移。</span><span class="sxs-lookup"><span data-stu-id="11d8d-207">For videos, the Focus Point is smoothed so holograms may appear to slowly drift into place if the Focus Point depth changes significantly.</span></span> <span data-ttu-id="11d8d-208">來自焦點點之不同深度的全像影像可能會顯示在現實世界的位移 (請參閱下方的範例，其中焦點點是設定為2個計量，但全像是放置在1個計量) 。</span><span class="sxs-lookup"><span data-stu-id="11d8d-208">Holograms that are at different depths from the focus point may appear offset from the real world (see example below where Focus Point is set at 2 meters but hologram is positioned at 1 meter).</span></span>

![2米的全像全像全球的全像投影。](images/hologramaccuracydistancemrc-1000px.png)

## <a name="integrating-mrc-functionality-from-within-your-app"></a><span data-ttu-id="11d8d-211">從您的應用程式內整合 MRC 功能</span><span class="sxs-lookup"><span data-stu-id="11d8d-211">Integrating MRC functionality from within your app</span></span>

<span data-ttu-id="11d8d-212">您的混合現實應用程式可以從應用程式中啟動 MRC 相片或影片捕獲，而您的應用程式也可以使用所捕捉的內容，而不需儲存至裝置的「相機變換」。</span><span class="sxs-lookup"><span data-stu-id="11d8d-212">Your mixed reality app can start MRC photo or video capture from within the app, and the content captured is made available to your app without being stored to the device's "Camera roll."</span></span> <span data-ttu-id="11d8d-213">您可以建立自訂的「MRC 錄製器」，或利用內建的「相機捕捉」 UI。</span><span class="sxs-lookup"><span data-stu-id="11d8d-213">You can create a custom MRC recorder or take advantage of built-in camera capture UI.</span></span> 

### <a name="mrc-with-built-in-camera-ui"></a><span data-ttu-id="11d8d-214">使用內建相機 UI 的 MRC</span><span class="sxs-lookup"><span data-stu-id="11d8d-214">MRC with built-in camera UI</span></span>

<span data-ttu-id="11d8d-215">只要幾行程式碼，開發人員就可以使用 *[相機捕捉 UI API](/windows/uwp/audio-video-camera/capture-photos-and-video-with-cameracaptureui)* 來取得使用者所取得的混合現實照片或影片。</span><span class="sxs-lookup"><span data-stu-id="11d8d-215">Developers can use the *[Camera Capture UI API](/windows/uwp/audio-video-camera/capture-photos-and-video-with-cameracaptureui)* to get a user-captured mixed reality photo or video with just a few lines of code.</span></span>

<span data-ttu-id="11d8d-216">此 API 會啟動內建的「MRC 攝影機」 UI，讓使用者可以拍攝相片或影片，並將產生的捕獲傳回您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="11d8d-216">This API launches the built-in MRC camera UI where users can take a photo or video and returns the resulting capture to your app.</span></span> <span data-ttu-id="11d8d-217">如果您需要新增自己的攝影機 UI 或較低層級的存取權來捕捉串流，您可以建立自訂的混合實境擷取錄製器。</span><span class="sxs-lookup"><span data-stu-id="11d8d-217">You can create a custom Mixed Reality Capture recorder if you need to add your own camera UI or lower-level access to capture streams.</span></span>

### <a name="creating-a-custom-mrc-recorder"></a><span data-ttu-id="11d8d-218">建立自訂的 MRC 錄製器</span><span class="sxs-lookup"><span data-stu-id="11d8d-218">Creating a custom MRC recorder</span></span>

<span data-ttu-id="11d8d-219">雖然使用者一律可以使用系統 MRC 捕捉服務來觸發相片或影片，但應用程式可能會想要建立自訂相機應用程式，以在相機串流中包含全像 MRC 一樣的影像。</span><span class="sxs-lookup"><span data-stu-id="11d8d-219">While the user can always trigger a photo or video using the system MRC capture service, an application may want to build a custom camera app that include holograms in the camera stream just like MRC.</span></span> <span data-ttu-id="11d8d-220">這可讓應用程式從使用者輸入開始進行捕捉、建立自訂錄製 UI，或自訂 MRC 設定來命名一些範例。</span><span class="sxs-lookup"><span data-stu-id="11d8d-220">This allows the application to kick off captures from user input, build custom recording UI, or customize MRC settings to name a few examples.</span></span>

<span data-ttu-id="11d8d-221">**HoloStudio 使用 MRC 效果新增自訂的 MRC 攝影機**</span><span class="sxs-lookup"><span data-stu-id="11d8d-221">**HoloStudio adds a custom MRC camera using MRC effects**</span></span>

![HoloStudio 使用 MRC 效果新增自訂的 MRC 攝影機](images/cameraiconholostudio-300px.jpg)

<span data-ttu-id="11d8d-223">Unity 應用程式應該會看到屬性 [Locatable_camera_in_Unity](../unity/locatable-camera-in-unity.md) ，以啟用全像。</span><span class="sxs-lookup"><span data-stu-id="11d8d-223">Unity Applications should see [Locatable_camera_in_Unity](../unity/locatable-camera-in-unity.md) for the property to enable holograms.</span></span>

<span data-ttu-id="11d8d-224">其他應用程式也可以使用 [Windows Media Capture api](/uwp/api/Windows.Media.Capture.MediaCapture) 來控制相機，並新增 MRC 影片和音訊效果，以在靜止和影片中包含虛擬全像影像和應用程式音訊。</span><span class="sxs-lookup"><span data-stu-id="11d8d-224">Other applications can do this by using the [Windows Media Capture APIs](/uwp/api/Windows.Media.Capture.MediaCapture) to control the Camera and add an MRC Video and Audio effect to include virtual holograms and application audio in stills and videos.</span></span>

<span data-ttu-id="11d8d-225">應用程式有兩個選項可新增效果：</span><span class="sxs-lookup"><span data-stu-id="11d8d-225">Applications have two options to add the effect:</span></span>
* <span data-ttu-id="11d8d-226">舊版 API： [MediaCapture. AddEffectAsync () ](/uwp/api/windows.media.capture.mediacapture.addeffectasync)</span><span class="sxs-lookup"><span data-stu-id="11d8d-226">The older API: [Windows.Media.Capture.MediaCapture.AddEffectAsync()](/uwp/api/windows.media.capture.mediacapture.addeffectasync)</span></span>
* <span data-ttu-id="11d8d-227">新的 Microsoft 建議 API (會傳回物件，讓您能夠操作動態屬性) ： [MediaCapture. AddVideoEffectAsync () ](/uwp/api/windows.media.capture.mediacapture.addvideoeffectasync)  /  [MediaCapture.. AddAudioEffectAsync () ](/uwp/api/windows.media.capture.mediacapture.addaudioeffectasync)需要應用程式建立自己的[IVideoEffectDefinition](/uwp/api/Windows.Media.Effects.IVideoEffectDefinition)和[IAudioEffectDefinition](/uwp/api/windows.media.effects.iaudioeffectdefinition)執行。</span><span class="sxs-lookup"><span data-stu-id="11d8d-227">The new Microsoft recommended API (returns an object, making it possible to manipulate dynamic properties): [Windows.Media.Capture.MediaCapture.AddVideoEffectAsync()](/uwp/api/windows.media.capture.mediacapture.addvideoeffectasync) / [Windows.Media.Capture.MediaCapture.AddAudioEffectAsync()](/uwp/api/windows.media.capture.mediacapture.addaudioeffectasync) which require the app create its own implementation of [IVideoEffectDefinition](/uwp/api/Windows.Media.Effects.IVideoEffectDefinition) and [IAudioEffectDefinition](/uwp/api/windows.media.effects.iaudioeffectdefinition).</span></span> <span data-ttu-id="11d8d-228">如需範例，請參閱 [MRC 範例應用程式](https://github.com/microsoft/Windows-universal-samples/tree/master/Samples/HolographicMixedRealityCapture) 。</span><span class="sxs-lookup"><span data-stu-id="11d8d-228">See the [MRC sample app](https://github.com/microsoft/Windows-universal-samples/tree/master/Samples/HolographicMixedRealityCapture) for examples.</span></span>

>[!NOTE]
> <span data-ttu-id="11d8d-229">Visual Studio 不會辨識 MixedRealityCapture 命名空間，但字串仍然有效。</span><span class="sxs-lookup"><span data-stu-id="11d8d-229">The Windows.Media.MixedRealityCapture namespace will not be recognized by Visual Studio, but the strings are still valid.</span></span>

<span data-ttu-id="11d8d-230">**MixedRealityCapture. MixedRealityCaptureVideoEffect**) 的 MRC 影片效果 (</span><span class="sxs-lookup"><span data-stu-id="11d8d-230">MRC Video Effect (**Windows.Media.MixedRealityCapture.MixedRealityCaptureVideoEffect**)</span></span>

|  <span data-ttu-id="11d8d-231">屬性名稱</span><span class="sxs-lookup"><span data-stu-id="11d8d-231">Property Name</span></span>  |  <span data-ttu-id="11d8d-232">類型</span><span class="sxs-lookup"><span data-stu-id="11d8d-232">Type</span></span>  |  <span data-ttu-id="11d8d-233">預設值</span><span class="sxs-lookup"><span data-stu-id="11d8d-233">Default Value</span></span>  |  <span data-ttu-id="11d8d-234">描述</span><span class="sxs-lookup"><span data-stu-id="11d8d-234">Description</span></span> |
|----------|----------|----------|----------|
|  <span data-ttu-id="11d8d-235">StreamType</span><span class="sxs-lookup"><span data-stu-id="11d8d-235">StreamType</span></span>  |  <span data-ttu-id="11d8d-236">UINT32 ([MediaStreamType](/uwp/api/Windows.Media.Capture.MediaStreamType)) </span><span class="sxs-lookup"><span data-stu-id="11d8d-236">UINT32 ([MediaStreamType](/uwp/api/Windows.Media.Capture.MediaStreamType))</span></span>  |  <span data-ttu-id="11d8d-237">1 (VideoRecord) </span><span class="sxs-lookup"><span data-stu-id="11d8d-237">1 (VideoRecord)</span></span>  |  <span data-ttu-id="11d8d-238">描述此效果用於哪個捕獲資料流程。</span><span class="sxs-lookup"><span data-stu-id="11d8d-238">Describe which capture stream this effect is used for.</span></span> <span data-ttu-id="11d8d-239">無法使用音訊。</span><span class="sxs-lookup"><span data-stu-id="11d8d-239">Audio isn't available.</span></span> |
|  <span data-ttu-id="11d8d-240">HologramCompositionEnabled</span><span class="sxs-lookup"><span data-stu-id="11d8d-240">HologramCompositionEnabled</span></span>  |  <span data-ttu-id="11d8d-241">boolean</span><span class="sxs-lookup"><span data-stu-id="11d8d-241">boolean</span></span>  |  <span data-ttu-id="11d8d-242">true</span><span class="sxs-lookup"><span data-stu-id="11d8d-242">TRUE</span></span>  |  <span data-ttu-id="11d8d-243">用來啟用或停用影片捕獲中全像影像的旗標。</span><span class="sxs-lookup"><span data-stu-id="11d8d-243">Flag to enable or disable holograms in video capture.</span></span> |
|  <span data-ttu-id="11d8d-244">RecordingIndicatorEnabled</span><span class="sxs-lookup"><span data-stu-id="11d8d-244">RecordingIndicatorEnabled</span></span>  |  <span data-ttu-id="11d8d-245">boolean</span><span class="sxs-lookup"><span data-stu-id="11d8d-245">boolean</span></span>  |  <span data-ttu-id="11d8d-246">true</span><span class="sxs-lookup"><span data-stu-id="11d8d-246">TRUE</span></span>  |  <span data-ttu-id="11d8d-247">用來啟用或停用全息圖捕獲期間在螢幕上錄製指標的旗標。</span><span class="sxs-lookup"><span data-stu-id="11d8d-247">Flag to enable or disable recording indicator on screen during hologram capturing.</span></span> |
|  <span data-ttu-id="11d8d-248">VideoStabilizationEnabled</span><span class="sxs-lookup"><span data-stu-id="11d8d-248">VideoStabilizationEnabled</span></span>  |  <span data-ttu-id="11d8d-249">boolean</span><span class="sxs-lookup"><span data-stu-id="11d8d-249">boolean</span></span>  |  <span data-ttu-id="11d8d-250">FALSE</span><span class="sxs-lookup"><span data-stu-id="11d8d-250">FALSE</span></span>  |  <span data-ttu-id="11d8d-251">此旗標可啟用或停用由 HoloLens 追蹤器提供技術支援的影片穩定。</span><span class="sxs-lookup"><span data-stu-id="11d8d-251">Flag to enable or disable video stabilization powered by the HoloLens tracker.</span></span> |
|  <span data-ttu-id="11d8d-252">VideoStabilizationBufferLength</span><span class="sxs-lookup"><span data-stu-id="11d8d-252">VideoStabilizationBufferLength</span></span>  |  <span data-ttu-id="11d8d-253">UINT32</span><span class="sxs-lookup"><span data-stu-id="11d8d-253">UINT32</span></span>  |  <span data-ttu-id="11d8d-254">0</span><span class="sxs-lookup"><span data-stu-id="11d8d-254">0</span></span>  |  <span data-ttu-id="11d8d-255">設定用於視頻穩定的歷程記錄畫面格數目。</span><span class="sxs-lookup"><span data-stu-id="11d8d-255">Set how many historical frames are used for video stabilization.</span></span> <span data-ttu-id="11d8d-256">0從電源和效能的觀點來看，有0延遲且幾乎「免費」。</span><span class="sxs-lookup"><span data-stu-id="11d8d-256">0 is 0-latency and nearly "free" from a power and performance perspective.</span></span> <span data-ttu-id="11d8d-257">針對最高品質 (，建議使用15，但延遲和記憶體) 的15個框架成本。</span><span class="sxs-lookup"><span data-stu-id="11d8d-257">15 is recommended for highest quality (at the cost of 15 frames of latency and memory).</span></span> |
|  <span data-ttu-id="11d8d-258">GlobalOpacityCoefficient</span><span class="sxs-lookup"><span data-stu-id="11d8d-258">GlobalOpacityCoefficient</span></span>  |  <span data-ttu-id="11d8d-259">FLOAT</span><span class="sxs-lookup"><span data-stu-id="11d8d-259">float</span></span>  |  <span data-ttu-id="11d8d-260">0.9 (HoloLens) 1.0 (沉浸式耳機) </span><span class="sxs-lookup"><span data-stu-id="11d8d-260">0.9 (HoloLens) 1.0 (Immersive headset)</span></span>  |  <span data-ttu-id="11d8d-261">在 0.0 (完全透明) 至 1.0 (完全不透明的) ，設定全像影像的全域不透明度係數。</span><span class="sxs-lookup"><span data-stu-id="11d8d-261">Set global opacity coefficient of hologram in range from 0.0 (fully transparent) to 1.0 (fully opaque).</span></span> |
|  <span data-ttu-id="11d8d-262">BlankOnProtectedContent</span><span class="sxs-lookup"><span data-stu-id="11d8d-262">BlankOnProtectedContent</span></span>  |  <span data-ttu-id="11d8d-263">boolean</span><span class="sxs-lookup"><span data-stu-id="11d8d-263">boolean</span></span>  |  <span data-ttu-id="11d8d-264">FALSE</span><span class="sxs-lookup"><span data-stu-id="11d8d-264">FALSE</span></span>  |  <span data-ttu-id="11d8d-265">如果有 2d UWP 應用程式顯示受保護的內容，則為啟用或停用會傳回空框架的旗標。</span><span class="sxs-lookup"><span data-stu-id="11d8d-265">Flag to enable or disable returning an empty frame if there's a 2d UWP app showing protected content.</span></span> <span data-ttu-id="11d8d-266">如果此旗標為 false，而 2d UWP 應用程式顯示受保護的內容，則會在耳機和混合式現實捕捉中，以受保護的內容材質取代 2d UWP 應用程式。</span><span class="sxs-lookup"><span data-stu-id="11d8d-266">If this flag is false and a 2d UWP app is showing protected content, the 2d UWP app will be replaced by a protected content texture in both the headset and in the mixed reality capture.</span></span> |
|  <span data-ttu-id="11d8d-267">ShowHiddenMesh</span><span class="sxs-lookup"><span data-stu-id="11d8d-267">ShowHiddenMesh</span></span>  |  <span data-ttu-id="11d8d-268">boolean</span><span class="sxs-lookup"><span data-stu-id="11d8d-268">boolean</span></span>  |  <span data-ttu-id="11d8d-269">FALSE</span><span class="sxs-lookup"><span data-stu-id="11d8d-269">FALSE</span></span>  |  <span data-ttu-id="11d8d-270">啟用或停用的旗標，顯示全像攝影的隱藏區域網格和連續的內容。</span><span class="sxs-lookup"><span data-stu-id="11d8d-270">Flag to enable or disable showing the holographic camera's hidden area mesh and neighboring content.</span></span> |
| <span data-ttu-id="11d8d-271">OutputSize</span><span class="sxs-lookup"><span data-stu-id="11d8d-271">OutputSize</span></span> | <span data-ttu-id="11d8d-272">大小</span><span class="sxs-lookup"><span data-stu-id="11d8d-272">Size</span></span> | <span data-ttu-id="11d8d-273">0, 0</span><span class="sxs-lookup"><span data-stu-id="11d8d-273">0, 0</span></span> | <span data-ttu-id="11d8d-274">在裁剪影片穩定之後，設定所需的輸出大小。</span><span class="sxs-lookup"><span data-stu-id="11d8d-274">Set the desired output size after cropping for video stabilization.</span></span> <span data-ttu-id="11d8d-275">如果指定0或不正確輸出大小，則會選擇預設裁剪大小。</span><span class="sxs-lookup"><span data-stu-id="11d8d-275">A default crop size is chosen if 0 or an invalid output size is specified.</span></span> |
| <span data-ttu-id="11d8d-276">PreferredHologramPerspective</span><span class="sxs-lookup"><span data-stu-id="11d8d-276">PreferredHologramPerspective</span></span> | <span data-ttu-id="11d8d-277">UINT32</span><span class="sxs-lookup"><span data-stu-id="11d8d-277">UINT32</span></span> | <span data-ttu-id="11d8d-278">**從** Windows 裝置入口網站中的相機設定轉譯</span><span class="sxs-lookup"><span data-stu-id="11d8d-278">**Render from Camera** setting in the Windows Device Portal</span></span> | <span data-ttu-id="11d8d-279">列舉用來指出應捕捉的全像攝影相機視圖設定： 0 (顯示) 表示不會要求應用程式從相片/攝影機轉譯，1 (PhotoVideoCamera) 將會要求應用程式從相片/視頻攝影機轉譯 (如果應用程式支援) 。</span><span class="sxs-lookup"><span data-stu-id="11d8d-279">Enum used to indicate which holographic camera view configuration should be captured: 0 (Display) means that the app won't be asked to render from the photo/video camera, 1 (PhotoVideoCamera) will ask the app to render from the photo/video camera (if the app supports it).</span></span> <span data-ttu-id="11d8d-280">僅 HoloLens 2 支援</span><span class="sxs-lookup"><span data-stu-id="11d8d-280">Only supported on HoloLens 2</span></span> |

>[!NOTE]
> <span data-ttu-id="11d8d-281">您可以在 Windows 裝置入口網站中變更 **PreferredHologramPerspective** 的預設值，方法是前往 [ [混合實境擷取] 頁面](using-the-windows-device-portal.md#mixed-reality-capture) ，並取消核取 [ **從相機** 轉譯]。</span><span class="sxs-lookup"><span data-stu-id="11d8d-281">You can change the default value of **PreferredHologramPerspective** in the Windows Device Portal by going to the [Mixed Reality Capture page](using-the-windows-device-portal.md#mixed-reality-capture) and unchecking **Render from Camera**.</span></span> <span data-ttu-id="11d8d-282">此設定預設為 **1 (PhotoVideoCamera)**，但可以取消核取，將它設為 **0 (顯示)**。</span><span class="sxs-lookup"><span data-stu-id="11d8d-282">The setting defaults to **1 (PhotoVideoCamera)**, but can be unchecked to set it to **0 (Display)**.</span></span>
>
> <span data-ttu-id="11d8d-283">**PreferredHologramPerspective** 的預設值為 **0 (顯示** 2020 年6月更新 (Windows 全像2004版組建19041.1106 和 windows 全像1903組建 18362.1064) 的) 。</span><span class="sxs-lookup"><span data-stu-id="11d8d-283">The default value of **PreferredHologramPerspective** was **0 (Display)** prior to the June 2020 update (Windows Holographic, version 2004 build 19041.1106 and Windows Holographic, version 1903 build 18362.1064).</span></span>

<span data-ttu-id="11d8d-284">**MixedRealityCapture. MixedRealityCaptureAudioEffect) 的** MRC 音訊效果 (</span><span class="sxs-lookup"><span data-stu-id="11d8d-284">MRC Audio Effect (**Windows.Media.MixedRealityCapture.MixedRealityCaptureAudioEffect**)</span></span>

| <span data-ttu-id="11d8d-285">屬性名稱</span><span class="sxs-lookup"><span data-stu-id="11d8d-285">Property Name</span></span> | <span data-ttu-id="11d8d-286">類型</span><span class="sxs-lookup"><span data-stu-id="11d8d-286">Type</span></span> | <span data-ttu-id="11d8d-287">預設值</span><span class="sxs-lookup"><span data-stu-id="11d8d-287">Default Value</span></span> | <span data-ttu-id="11d8d-288">描述</span><span class="sxs-lookup"><span data-stu-id="11d8d-288">Description</span></span> |
|----------|----------|----------|----------|
| <span data-ttu-id="11d8d-289">MixerMode</span><span class="sxs-lookup"><span data-stu-id="11d8d-289">MixerMode</span></span> | <span data-ttu-id="11d8d-290">UINT32</span><span class="sxs-lookup"><span data-stu-id="11d8d-290">UINT32</span></span> | <span data-ttu-id="11d8d-291">2 (Mic 和系統音訊) </span><span class="sxs-lookup"><span data-stu-id="11d8d-291">2 (Mic and System audio)</span></span> | <span data-ttu-id="11d8d-292">用來指出應使用哪些音訊來源的列舉： 0 (僅限 Mic 音訊) 、1 (僅限系統音訊) 、2 (Mic 和系統音訊) </span><span class="sxs-lookup"><span data-stu-id="11d8d-292">Enum used to indicate which audio sources should be used: 0 (Mic audio only), 1 (System audio only), 2 (Mic and System audio)</span></span> |
| <span data-ttu-id="11d8d-293">LoopbackGain</span><span class="sxs-lookup"><span data-stu-id="11d8d-293">LoopbackGain</span></span> | <span data-ttu-id="11d8d-294">FLOAT</span><span class="sxs-lookup"><span data-stu-id="11d8d-294">float</span></span> | <span data-ttu-id="11d8d-295">Windows 裝置入口網站中的 **應用程式音訊增益** 設定</span><span class="sxs-lookup"><span data-stu-id="11d8d-295">**App Audio Gain** setting in the Windows Device Portal</span></span> | <span data-ttu-id="11d8d-296">適用于系統音訊音量的增益。</span><span class="sxs-lookup"><span data-stu-id="11d8d-296">Gain to apply to system audio volume.</span></span> <span data-ttu-id="11d8d-297">範圍從0.0 到5.0。</span><span class="sxs-lookup"><span data-stu-id="11d8d-297">Ranges from 0.0 to 5.0.</span></span> <span data-ttu-id="11d8d-298">僅 HoloLens 2 支援</span><span class="sxs-lookup"><span data-stu-id="11d8d-298">Only supported on HoloLens 2</span></span> |
| <span data-ttu-id="11d8d-299">MicrophoneGain</span><span class="sxs-lookup"><span data-stu-id="11d8d-299">MicrophoneGain</span></span> | <span data-ttu-id="11d8d-300">FLOAT</span><span class="sxs-lookup"><span data-stu-id="11d8d-300">float</span></span> | <span data-ttu-id="11d8d-301">Windows 裝置入口網站中的 **Mic 音訊增益** 設定</span><span class="sxs-lookup"><span data-stu-id="11d8d-301">**Mic Audio Gain** setting in the Windows Device Portal</span></span> | <span data-ttu-id="11d8d-302">適用于 mic 音量的增益。</span><span class="sxs-lookup"><span data-stu-id="11d8d-302">Gain to apply to mic volume.</span></span> <span data-ttu-id="11d8d-303">範圍從0.0 到5.0。</span><span class="sxs-lookup"><span data-stu-id="11d8d-303">Ranges from 0.0 to 5.0.</span></span> <span data-ttu-id="11d8d-304">僅 HoloLens 2 支援</span><span class="sxs-lookup"><span data-stu-id="11d8d-304">Only supported on HoloLens 2</span></span> |

>[!NOTE]
> <span data-ttu-id="11d8d-305">您可以在 Windows 裝置入口網站中變更 **LoopbackGain** 或 **MicrophoneGain** 的預設值，方法是移至 [ [混合實境擷取] 頁面](using-the-windows-device-portal.md#mixed-reality-capture) ，然後調整其各自設定旁邊的滑杆。</span><span class="sxs-lookup"><span data-stu-id="11d8d-305">You can change the default value of **LoopbackGain** or **MicrophoneGain** in the Windows Device Portal by going to the [Mixed Reality Capture page](using-the-windows-device-portal.md#mixed-reality-capture) and adjusting the slider next to their respective settings.</span></span> <span data-ttu-id="11d8d-306">這兩個設定預設為 **1.0**，但可以設定為 **0.0** 與 **5.0** 之間的任何值。</span><span class="sxs-lookup"><span data-stu-id="11d8d-306">Both settings default to **1.0**, but can be set to any value between **0.0** and **5.0**.</span></span>
>
> <span data-ttu-id="11d8d-307">在2020年6月的更新中，您可以使用 Windows 裝置入口網站來設定預設增益值 (Windows 全像2004組建19041.1106 和 Windows 全像版本1903組建 18362.1064) 。</span><span class="sxs-lookup"><span data-stu-id="11d8d-307">Using Windows Device Portal to configure the default gain values was added with the June 2020 update (Windows Holographic, version 2004 build 19041.1106 and Windows Holographic, version 1903 build 18362.1064).</span></span>

### <a name="simultaneous-mrc-limitations"></a><span data-ttu-id="11d8d-308">同時 MRC 限制</span><span class="sxs-lookup"><span data-stu-id="11d8d-308">Simultaneous MRC limitations</span></span>

<span data-ttu-id="11d8d-309">當有多個應用程式同時存取 MRC 時，您必須留意某些限制。</span><span class="sxs-lookup"><span data-stu-id="11d8d-309">You need to be aware of certain limitations when multiple apps are accessing MRC at the same time.</span></span>

#### <a name="photovideo-camera-access"></a><span data-ttu-id="11d8d-310">相片/攝影機存取</span><span class="sxs-lookup"><span data-stu-id="11d8d-310">Photo/video camera access</span></span>

<span data-ttu-id="11d8d-311">在 HoloLens 1 上，當處理常式錄製影片或拍攝相片時，MRC 將無法拍攝相片或抓取影片。</span><span class="sxs-lookup"><span data-stu-id="11d8d-311">On HoloLens 1, MRC will fail to capture a photo or capture video while a process is recording video or taking a photo.</span></span> <span data-ttu-id="11d8d-312">反之亦然：如果 MRC 正在執行，應用程式將無法取得相機的存取權。</span><span class="sxs-lookup"><span data-stu-id="11d8d-312">The reverse is also true: if MRC is running, the application will fail to get access to the camera.</span></span> 

<span data-ttu-id="11d8d-313">有了 HoloLens 2，您就可以共用相機的存取權。</span><span class="sxs-lookup"><span data-stu-id="11d8d-313">With HoloLens 2, it's possible for you to share access to the camera.</span></span> <span data-ttu-id="11d8d-314">如果您不需要直接控制解析度或畫面播放速率，您可以搭配 SharedReadOnly 使用 [SharedMode 屬性](/uwp/api/windows.media.capture.mediacaptureinitializationsettings.sharingmode?view=winrt-19041) 來初始化 MediaCapture。</span><span class="sxs-lookup"><span data-stu-id="11d8d-314">If you don't need direct control of the resolution or frame-rate, you can initialize MediaCapture using the [SharedMode property](/uwp/api/windows.media.capture.mediacaptureinitializationsettings.sharingmode?view=winrt-19041) with SharedReadOnly.</span></span>  

##### <a name="built-in-mrc-photovideo-camera-access"></a><span data-ttu-id="11d8d-315">內建的 MRC 相片/攝影機存取</span><span class="sxs-lookup"><span data-stu-id="11d8d-315">Built-in MRC photo/video camera access</span></span>

<span data-ttu-id="11d8d-316">內建于透過 Cortana、[開始] 功能表、硬體快捷方式、Miracast、Windows 裝置入口網站) 的 Windows 10 (的 MRC 功能：</span><span class="sxs-lookup"><span data-stu-id="11d8d-316">MRC functionality built into Windows 10 (via Cortana, Start Menu, hardware shortcuts, Miracast, Windows Device Portal):</span></span>

* <span data-ttu-id="11d8d-317">預設會以 ExclusiveControl 執行</span><span class="sxs-lookup"><span data-stu-id="11d8d-317">Will run with ExclusiveControl by default</span></span>

<span data-ttu-id="11d8d-318">不過，支援已新增至 MRC 子系統以在共用模式中運作：</span><span class="sxs-lookup"><span data-stu-id="11d8d-318">However, support has been added to MRC subsystem to operate in a shared mode:</span></span> 

* <span data-ttu-id="11d8d-319">如果應用程式要求相片/攝影機的 ExclusiveControl 存取權，內建的 MRC 將會自動停止使用相片/攝影機，因此應用程式的要求將會成功</span><span class="sxs-lookup"><span data-stu-id="11d8d-319">If an app requests ExclusiveControl access to the photo/video camera, built-in MRC will automatically stop using the photo/video camera so the app's request will succeed</span></span> 
* <span data-ttu-id="11d8d-320">如果在應用程式 ExclusiveControl 時啟動內建的 MRC，內建的 MRC 將會以 SharedReadOnly 模式執行</span><span class="sxs-lookup"><span data-stu-id="11d8d-320">If built in MRC is started while an app has ExclusiveControl, built-in MRC will run in SharedReadOnly mode</span></span> 

<span data-ttu-id="11d8d-321">此共用模式功能有某些限制：</span><span class="sxs-lookup"><span data-stu-id="11d8d-321">This shared mode functionality has certain restrictions:</span></span>

* <span data-ttu-id="11d8d-322">透過 Cortana、硬體快速鍵或 [開始] 功能表的相片：需要 Windows 10 2018 年4月更新 (或更新版本) </span><span class="sxs-lookup"><span data-stu-id="11d8d-322">Photo via Cortana, hardware shortcuts, or Start Menu: Requires the Windows 10 April 2018 Update (or later)</span></span>
* <span data-ttu-id="11d8d-323">透過 Cortana、硬體快速鍵或 [開始] 功能表的影片：需要 Windows 10 2018 年4月更新 (或更新版本) </span><span class="sxs-lookup"><span data-stu-id="11d8d-323">Video via Cortana, hardware shortcuts, or Start Menu: Requires the Windows 10 April 2018 Update (or later)</span></span>
* <span data-ttu-id="11d8d-324">透過 Miracast 的串流處理 MRC：需要 Windows 10 2018 年10月更新 (或更新版本) </span><span class="sxs-lookup"><span data-stu-id="11d8d-324">Streaming MRC over Miracast: Requires the Windows 10 October 2018 Update (or later)</span></span>
* <span data-ttu-id="11d8d-325">透過 Windows 裝置入口網站或透過 HoloLens 附屬應用程式串流處理 MRC：需要 HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="11d8d-325">Streaming MRC over Windows Device Portal or via the HoloLens companion app: Requires HoloLens 2</span></span>

>[!NOTE]
> <span data-ttu-id="11d8d-326">當另一個應用程式正在使用相片/攝影機時，內建的 MRC 攝影機 UI 的解析度和畫面播放速率可能會從其正常值減少。</span><span class="sxs-lookup"><span data-stu-id="11d8d-326">The resolution and frame-rate of the built-in MRC camera UI might be reduced from its normal values when another app is using the photo/video camera.</span></span>

#### <a name="mrc-access-for-developers"></a><span data-ttu-id="11d8d-327">開發人員的 MRC 存取</span><span class="sxs-lookup"><span data-stu-id="11d8d-327">MRC access for developers</span></span>

<span data-ttu-id="11d8d-328">使用 MRC 時，建議您一律要求相機的獨佔控制。</span><span class="sxs-lookup"><span data-stu-id="11d8d-328">We recommend you always request Exclusive control for the camera when using MRC.</span></span> <span data-ttu-id="11d8d-329">這可確保您的應用程式可以完全掌控相機的設定，只要您知道上面所列的限制即可。</span><span class="sxs-lookup"><span data-stu-id="11d8d-329">This will ensure your application has full control of the settings for the camera as long as you're aware of the limitations listed above.</span></span> 

* <span data-ttu-id="11d8d-330">使用[初始化設定](/uwp/api/windows.media.capture.mediacaptureinitializationsettings?view=winrt-19041)建立 media capture 物件</span><span class="sxs-lookup"><span data-stu-id="11d8d-330">Create a media capture object using the [initialization settings](/uwp/api/windows.media.capture.mediacaptureinitializationsettings?view=winrt-19041)</span></span>
* <span data-ttu-id="11d8d-331">將 [SharingMode](/uwp/api/windows.media.capture.mediacaptureinitializationsettings.sharingmode?view=winrt-19041#Windows_Media_Capture_MediaCaptureInitializationSettings_SharingMode) 屬性設定為 **專有**</span><span class="sxs-lookup"><span data-stu-id="11d8d-331">Set the [SharingMode](/uwp/api/windows.media.capture.mediacaptureinitializationsettings.sharingmode?view=winrt-19041#Windows_Media_Capture_MediaCaptureInitializationSettings_SharingMode) property to **exclusive**</span></span>

> [!CAUTION]
> <span data-ttu-id="11d8d-332">請務必仔細閱讀 [SharingMode 備註](/uwp/api/windows.media.capture.mediacaptureinitializationsettings.sharingmode?view=winrt-19041#remarks) ，再繼續進行操作。</span><span class="sxs-lookup"><span data-stu-id="11d8d-332">Be sure to carefully read the [SharingMode remarks](/uwp/api/windows.media.capture.mediacaptureinitializationsettings.sharingmode?view=winrt-19041#remarks) before continuing.</span></span>

* <span data-ttu-id="11d8d-333">以您想要的方式設定您的相機</span><span class="sxs-lookup"><span data-stu-id="11d8d-333">Set up your camera the way you want it</span></span>
* <span data-ttu-id="11d8d-334">啟動應用程式、使用啟動 API 來捕獲影片畫面，然後啟用 MRC</span><span class="sxs-lookup"><span data-stu-id="11d8d-334">Start the app, capture video frames with the start API, then enable MRC</span></span>

> [!CAUTION]
> <span data-ttu-id="11d8d-335">如果您在啟動應用程式之前啟動了您的應用程式，我們無法保證此功能將會如預期般運作。</span><span class="sxs-lookup"><span data-stu-id="11d8d-335">If you start MRC before you start your app, we can't guarantee the feature will work as expected.</span></span>

<span data-ttu-id="11d8d-336">您可以在全像全像 [臉部追蹤範例](/samples/microsoft/windows-universal-samples/holographicfacetracking)中找到上述程式的完整範例。</span><span class="sxs-lookup"><span data-stu-id="11d8d-336">You can find a full sample of the above process in the [holographic face tracking sample](/samples/microsoft/windows-universal-samples/holographicfacetracking).</span></span>

> [!NOTE]
> <span data-ttu-id="11d8d-337">在 Windows 10 2018 年4月更新之前，應用程式的自訂 MRC 錄製器會與系統 MRC 互斥 (捕獲相片、捕獲影片或從 Windows 裝置入口網站) 進行串流。</span><span class="sxs-lookup"><span data-stu-id="11d8d-337">Before the Windows 10 April 2018 Update, an app's custom MRC recorder was mutually exclusive with system MRC (capturing photos, capturing videos, or streaming from the Windows Device Portal).</span></span>

## <a name="see-also"></a><span data-ttu-id="11d8d-338">另請參閱</span><span class="sxs-lookup"><span data-stu-id="11d8d-338">See also</span></span>

* [<span data-ttu-id="11d8d-339">混合實境擷取</span><span class="sxs-lookup"><span data-stu-id="11d8d-339">Mixed reality capture</span></span>](/hololens/holographic-photos-and-videos)
* [<span data-ttu-id="11d8d-340">觀眾檢視</span><span class="sxs-lookup"><span data-stu-id="11d8d-340">Spectator view</span></span>](spectator-view.md)
* [<span data-ttu-id="11d8d-341">Unity 開發總覽</span><span class="sxs-lookup"><span data-stu-id="11d8d-341">Unity Development Overview</span></span>](../unity/unity-development-overview.md)
* [<span data-ttu-id="11d8d-342">Unreal 開發概觀</span><span class="sxs-lookup"><span data-stu-id="11d8d-342">Unreal development overview</span></span>](../unreal/unreal-development-overview.md)
