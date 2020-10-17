---
title: 適用於開發人員的混合實境擷取
description: 適用于開發人員的混合現實開發最佳做法。
author: mattzmsft
ms.author: mazeller
ms.date: 02/24/2019
ms.topic: article
keywords: mrc、相片、影片、捕捉、攝影機
ms.openlocfilehash: 6e42bd904b842bac160ece346d9b0df13cf3eaa3
ms.sourcegitcommit: 53a00690f32a0a629ed23aefaae5a888f669dcb6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2020
ms.locfileid: "92138030"
---
# <a name="mixed-reality-capture-for-developers"></a><span data-ttu-id="8fe61-104">適用於開發人員的混合實境擷取</span><span class="sxs-lookup"><span data-stu-id="8fe61-104">Mixed reality capture for developers</span></span>

> [!NOTE]
> <span data-ttu-id="8fe61-105">請參閱下面 [的 PV 攝影機](#render-from-the-pv-camera-opt-in) 轉譯，以取得 HoloLens 2 新的 MRC 功能的指引。</span><span class="sxs-lookup"><span data-stu-id="8fe61-105">See [Render from the PV camera](#render-from-the-pv-camera-opt-in) below for guidance on a new MRC capability for HoloLens 2.</span></span>

<span data-ttu-id="8fe61-106">由於使用者可能會 [在一段時間內 (的](../../mixed-reality-capture.md)) 相片或影片，讓您在開發應用程式時，應該牢記幾件事。</span><span class="sxs-lookup"><span data-stu-id="8fe61-106">Since a user could take a [mixed reality capture](../../mixed-reality-capture.md) (MRC) photo or video at any time, there are a few things that you should keep in mind when developing your application.</span></span> <span data-ttu-id="8fe61-107">這包括了 MRC 視覺品質的最佳作法，並在 MRCs 時回應系統變更。</span><span class="sxs-lookup"><span data-stu-id="8fe61-107">This includes best practices for MRC visual quality and being responsive to system changes while MRCs are being captured.</span></span>

<span data-ttu-id="8fe61-108">開發人員也可以將混合現實的捕獲和插入順暢地整合到他們的應用程式中。</span><span class="sxs-lookup"><span data-stu-id="8fe61-108">Developers can also seamlessly integrate mixed reality capture and insertion into their apps.</span></span>

<span data-ttu-id="8fe61-109">HoloLens (第一代) 支援最高720p 的影片和相片，而 HoloLens 2 上的 MRC 可支援最高1080p 和最高4K 解析度的影像。</span><span class="sxs-lookup"><span data-stu-id="8fe61-109">MRC on HoloLens (first-generation) supports videos and photos up to 720p, while MRC on HoloLens 2 supports videos up to 1080p and photos up to 4K resolution.</span></span>

## <a name="the-importance-of-quality-mrc"></a><span data-ttu-id="8fe61-110">品質 MRC 的重要性</span><span class="sxs-lookup"><span data-stu-id="8fe61-110">The importance of quality MRC</span></span>

<span data-ttu-id="8fe61-111">混合現實的拍攝相片和影片很可能是使用者將擁有您應用程式的第一次暴露。</span><span class="sxs-lookup"><span data-stu-id="8fe61-111">Mixed reality captured photos and videos are likely the first exposure a user will have of your app.</span></span> <span data-ttu-id="8fe61-112">在您的 Microsoft Store 頁面上，還是在社交網路上共用 MRCs 的其他使用者，是否為混合現實螢幕擷取畫面。</span><span class="sxs-lookup"><span data-stu-id="8fe61-112">Whether as mixed reality screenshots on your Microsoft Store page or from other users sharing MRCs on social networks.</span></span> <span data-ttu-id="8fe61-113">您可以使用 MRC 來示範您的應用程式、教育使用者、鼓勵使用者共用其混合的世界互動，以及進行使用者研究和解決問題。</span><span class="sxs-lookup"><span data-stu-id="8fe61-113">You can use MRC to demo your app, educate users, encourage users to share their mixed world interactions, and for user research and problem solving.</span></span>

## <a name="how-mrc-impacts-your-app"></a><span data-ttu-id="8fe61-114">MRC 如何影響您的應用程式</span><span class="sxs-lookup"><span data-stu-id="8fe61-114">How MRC impacts your app</span></span>

### <a name="enabling-mrc-in-your-app"></a><span data-ttu-id="8fe61-115">在您的應用程式中啟用 MRC</span><span class="sxs-lookup"><span data-stu-id="8fe61-115">Enabling MRC in your app</span></span>

<span data-ttu-id="8fe61-116">根據預設，應用程式不需要執行任何動作，就能讓使用者採用混合的事實捕獲。</span><span class="sxs-lookup"><span data-stu-id="8fe61-116">By default, an app does not have to do anything to enable users to take mixed reality captures.</span></span>

### <a name="enabling-improved-alignment-for-mrc-in-your-app"></a><span data-ttu-id="8fe61-117">為您應用程式中的 MRC 啟用改良的對齊</span><span class="sxs-lookup"><span data-stu-id="8fe61-117">Enabling improved alignment for MRC in your app</span></span>

<span data-ttu-id="8fe61-118">依預設，mixed reality capture 會將適當的眼睛全像影像輸出與相片/影片 (PV) 攝影機。</span><span class="sxs-lookup"><span data-stu-id="8fe61-118">By default, mixed reality capture combines the right eye's holographic output with the photo/video (PV) camera.</span></span> <span data-ttu-id="8fe61-119">這兩個來源會使用目前執行的沉浸式應用程式所設定的焦點點來合併。</span><span class="sxs-lookup"><span data-stu-id="8fe61-119">These two sources are combined using the focus point set by the currently running immersive app.</span></span>

<span data-ttu-id="8fe61-120">這表示，由於 PV 攝影機和右邊顯示) 之間的實體距離，因此焦點平面以外的全像全像 (也不會對齊。</span><span class="sxs-lookup"><span data-stu-id="8fe61-120">This means that holograms outside the focus plane won't align as well (due to the physical distance between the PV camera and the right display).</span></span>

#### <a name="set-the-focus-point"></a><span data-ttu-id="8fe61-121">設定焦點點</span><span class="sxs-lookup"><span data-stu-id="8fe61-121">Set the focus point</span></span>

<span data-ttu-id="8fe61-122">在) HoloLens 上 (的沉浸式應用程式，應該將其穩定平面的 [焦點放](../unity/focus-point-in-unity.md) 在您要的位置。</span><span class="sxs-lookup"><span data-stu-id="8fe61-122">Immersive apps (on HoloLens) should set the [focus point](../unity/focus-point-in-unity.md) of where they want their stabilization plane to be.</span></span> <span data-ttu-id="8fe61-123">這可確保耳機和混合式現實捕捉中的最佳對齊。</span><span class="sxs-lookup"><span data-stu-id="8fe61-123">This ensures the best alignment in both the headset and in mixed reality capture.</span></span>

<span data-ttu-id="8fe61-124">如果未設定焦點點，穩定平面會預設為兩個計量。</span><span class="sxs-lookup"><span data-stu-id="8fe61-124">If a focus point is not set, the stabilization plane will default to two meters.</span></span>

#### <a name="render-from-the-pv-camera-opt-in"></a><span data-ttu-id="8fe61-125">從 PV 攝影機轉譯 (加入宣告) </span><span class="sxs-lookup"><span data-stu-id="8fe61-125">Render from the PV camera (opt-in)</span></span>

<span data-ttu-id="8fe61-126">HoloLens 2 新增了當混合的現實捕捉正在執行時，可讓沉浸式應用程式 **從 PV 攝影機** 轉譯的功能。</span><span class="sxs-lookup"><span data-stu-id="8fe61-126">HoloLens 2 adds the ability for an immersive app to **render from the PV camera** while mixed reality capture is running.</span></span> <span data-ttu-id="8fe61-127">為了確保應用程式能夠正確地支援其他轉譯，應用程式必須加入宣告這項功能。</span><span class="sxs-lookup"><span data-stu-id="8fe61-127">To ensure the app supports the additional render correctly, the app has to opt-in to this functionality.</span></span>

<span data-ttu-id="8fe61-128">從 PV 攝影機轉譯可針對預設的 MRC 體驗提供下列改良功能：</span><span class="sxs-lookup"><span data-stu-id="8fe61-128">Render from the PV camera offers the following improvements over the default MRC experience:</span></span>
* <span data-ttu-id="8fe61-129">全像您的實體環境的全像點對齊，而針對近乎互動的手 () 應該在所有距離都是正確的，而不是在焦點點以外的距離之間取得位移，如同您可能會在預設的 MRC 中看到的距離。</span><span class="sxs-lookup"><span data-stu-id="8fe61-129">Hologram alignment to both your physical environment and hands (for near interactions) should be accurate at all distances, instead of having an offset at distances other than the focus point as you might see in the default MRC.</span></span>
* <span data-ttu-id="8fe61-130">耳機中的適當眼睛不會遭到入侵，因為它不會用來呈現 MRC 輸出的全像影像。</span><span class="sxs-lookup"><span data-stu-id="8fe61-130">The right eye in the headset won't be compromised, as it won't be used to render the holograms for the MRC output.</span></span>

<span data-ttu-id="8fe61-131">有三個步驟可讓您從 PV 攝影機進行轉譯：</span><span class="sxs-lookup"><span data-stu-id="8fe61-131">There are three steps to enable rendering from the PV camera:</span></span>
1. <span data-ttu-id="8fe61-132">啟用 PhotoVideoCamera HolographicViewConfiguration</span><span class="sxs-lookup"><span data-stu-id="8fe61-132">Enable the PhotoVideoCamera HolographicViewConfiguration</span></span>
2. <span data-ttu-id="8fe61-133">處理其他 HolographicCamera 轉譯</span><span class="sxs-lookup"><span data-stu-id="8fe61-133">Handle the additional HolographicCamera render</span></span>
3. <span data-ttu-id="8fe61-134">從這個額外的 HolographicCamera 確認您的著色器和程式碼轉譯正確</span><span class="sxs-lookup"><span data-stu-id="8fe61-134">Verify your shaders and code render correctly from this additional HolographicCamera</span></span>

##### <a name="enable-the-photovideocamera-holographicviewconfiguration-in-directx"></a><span data-ttu-id="8fe61-135">啟用 DirectX 中的 PhotoVideoCamera HolographicViewConfiguration</span><span class="sxs-lookup"><span data-stu-id="8fe61-135">Enable the PhotoVideoCamera HolographicViewConfiguration in DirectX</span></span>

<span data-ttu-id="8fe61-136">若要選擇從 PV 攝影機轉譯，應用程式只會啟用 PhotoVideoCamera 的 [HolographicViewConfiguration](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicViewConfiguration)：</span><span class="sxs-lookup"><span data-stu-id="8fe61-136">To opt-in to rendering from the PV Camera, an app simply enables the PhotoVideoCamera's [HolographicViewConfiguration](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicViewConfiguration):</span></span>
```csharp
var display = Windows.Graphics.Holographic.HolographicDisplay.GetDefault();
var view = display.TryGetViewConfiguration(Windows.Graphics.Holographic.HolographicViewConfigurationKind.PhotoVideoCamera);
if (view != null)
{
    view.IsEnabled = true;
}
```

##### <a name="handle-the-additional-holographiccamera-render-in-directx"></a><span data-ttu-id="8fe61-137">處理 DirectX 中的其他 HolographicCamera 轉譯</span><span class="sxs-lookup"><span data-stu-id="8fe61-137">Handle the additional HolographicCamera render in DirectX</span></span>

<span data-ttu-id="8fe61-138">當應用程式已從 PV 攝影機加入宣告，且混合現實捕捉開始時：</span><span class="sxs-lookup"><span data-stu-id="8fe61-138">When the app has opt-in to render from the PV camera and mixed reality capture starts:</span></span>
1. <span data-ttu-id="8fe61-139">將引發 HolographicSpace 的 CameraAdded 事件。</span><span class="sxs-lookup"><span data-stu-id="8fe61-139">HolographicSpace's CameraAdded event will fire.</span></span> <span data-ttu-id="8fe61-140">如果應用程式目前無法處理相機，則可以延後此事件。</span><span class="sxs-lookup"><span data-stu-id="8fe61-140">This event can be deferred if the app cannot handle the camera at this time.</span></span>
2. <span data-ttu-id="8fe61-141">當事件完成 (且沒有未完成的延期) HolographicCamera 將會出現在下一個 HolographicFrame 的 AddedCameras 清單中。</span><span class="sxs-lookup"><span data-stu-id="8fe61-141">Once the event has completed (and there are no outstanding deferrals) the HolographicCamera will appear in the next HolographicFrame's AddedCameras list.</span></span>

<span data-ttu-id="8fe61-142">當混合式事實 capture (停止，或應用程式在混合式事實捕捉正在執行時停用 view 設定) ： HolographicCamera 將會出現在下一個 HolographicFrame 的 RemovedCameras 清單中，而且 HolographicSpace 的 CameraRemoved 事件將會引發。</span><span class="sxs-lookup"><span data-stu-id="8fe61-142">When mixed reality capture stops (or if the app disables the view configuration while mixed reality capture is running): the HolographicCamera will appear in the next HolographicFrame's RemovedCameras list and the HolographicSpace's CameraRemoved event will fire.</span></span>

<span data-ttu-id="8fe61-143">已將 [ViewConfiguration](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.viewconfiguration) 屬性新增至 HolographicCamera，以協助識別相機所屬的設定。</span><span class="sxs-lookup"><span data-stu-id="8fe61-143">A [ViewConfiguration](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.viewconfiguration) property has been added to HolographicCamera to help identify the configuration a camera belongs to.</span></span>

##### <a name="enable-the-photovideocamera-holographicviewconfiguration-in-unity"></a><span data-ttu-id="8fe61-144">在 Unity 中啟用 PhotoVideoCamera HolographicViewConfiguration</span><span class="sxs-lookup"><span data-stu-id="8fe61-144">Enable the PhotoVideoCamera HolographicViewConfiguration in Unity</span></span>

> [!NOTE]
> <span data-ttu-id="8fe61-145">這需要 **unity 2018.4.13 f1**、 **unity 2019.3.0 f1**或更新版本。</span><span class="sxs-lookup"><span data-stu-id="8fe61-145">This requires **Unity 2018.4.13f1**, **Unity 2019.3.0f1**, or newer.</span></span>

<span data-ttu-id="8fe61-146">若要選擇從 PV 攝影機轉譯，在使用「 [混合現實」工具](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)組時，請啟用 [Windows Mixed Reality 相機設定](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/CameraSystem/WindowsMixedRealityCameraSettings.html) 提供者，並核取 [ **從 PV 攝影機** 轉譯] 設定。</span><span class="sxs-lookup"><span data-stu-id="8fe61-146">To opt-in to rendering from the PV Camera, when using the [Mixed Reality Toolkit](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html), enable the [Windows Mixed Reality Camera Settings](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/CameraSystem/WindowsMixedRealityCameraSettings.html) provider and check the **Render from PV Camera** setting.</span></span>

<span data-ttu-id="8fe61-147">如果您不是使用「混合現實」工具組，您可以使用元件以 [手動方式加入宣告](#enable-the-photovideocamera-holographicviewconfiguration-in-directx) ，如上面的 DirectX 所述。</span><span class="sxs-lookup"><span data-stu-id="8fe61-147">If you're not using the Mixed Reality Toolkit, you can use a component to [manually opt-in](#enable-the-photovideocamera-holographicviewconfiguration-in-directx) as described above for DirectX.</span></span>

##### <a name="handle-the-additional-holographiccamera-render-in-unity"></a><span data-ttu-id="8fe61-148">處理 Unity 中的其他 HolographicCamera 轉譯</span><span class="sxs-lookup"><span data-stu-id="8fe61-148">Handle the additional HolographicCamera render in Unity</span></span>

<span data-ttu-id="8fe61-149">Unity 會自動為您完成這項操作。</span><span class="sxs-lookup"><span data-stu-id="8fe61-149">This is done for you automatically by Unity.</span></span>

##### <a name="enable-the-photovideocamera-holographicviewconfiguration-in-unreal"></a><span data-ttu-id="8fe61-150">在 Unreal 中啟用 PhotoVideoCamera HolographicViewConfiguration</span><span class="sxs-lookup"><span data-stu-id="8fe61-150">Enable the PhotoVideoCamera HolographicViewConfiguration in Unreal</span></span>

> [!NOTE]
> <span data-ttu-id="8fe61-151">這需要 **Unreal Engine 4.25** 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="8fe61-151">This requires **Unreal Engine 4.25** or newer.</span></span>

<span data-ttu-id="8fe61-152">若要選擇從 PV 相機呈現：</span><span class="sxs-lookup"><span data-stu-id="8fe61-152">To opt-in to rendering from the PV Camera:</span></span>

1. <span data-ttu-id="8fe61-153">呼叫 **SetEnabledMixedRealityCamera** 和 **ResizeMixedRealityCamera**</span><span class="sxs-lookup"><span data-stu-id="8fe61-153">Call **SetEnabledMixedRealityCamera** and **ResizeMixedRealityCamera**</span></span>
    * <span data-ttu-id="8fe61-154">使用 **Size X** 和 **Size Y** 值來設定影片大小。</span><span class="sxs-lookup"><span data-stu-id="8fe61-154">Use the **Size X** and **Size Y** values to set the video dimensions.</span></span>

![第三相機](images/unreal-camera-3rd.PNG)

##### <a name="handle-the-additional-holographiccamera-render-in-unreal"></a><span data-ttu-id="8fe61-156">處理 Unreal 中的其他 HolographicCamera 轉譯</span><span class="sxs-lookup"><span data-stu-id="8fe61-156">Handle the additional HolographicCamera render in Unreal</span></span>

<span data-ttu-id="8fe61-157">Unreal 會自動為您完成這項操作。</span><span class="sxs-lookup"><span data-stu-id="8fe61-157">This is done for you automatically by Unreal.</span></span>

##### <a name="verify-shaders-and-code-support-additional-cameras"></a><span data-ttu-id="8fe61-158">確認著色器和程式碼支援其他攝影機</span><span class="sxs-lookup"><span data-stu-id="8fe61-158">Verify shaders and code support additional cameras</span></span>

<span data-ttu-id="8fe61-159">執行混合現實的捕獲，並檢查是否有不尋常的對齊、遺漏內容或效能問題。</span><span class="sxs-lookup"><span data-stu-id="8fe61-159">Run a mixed reality capture and check for unusual alignment, missing content, or performance issues.</span></span> <span data-ttu-id="8fe61-160">適當地更新著色器和程式碼。</span><span class="sxs-lookup"><span data-stu-id="8fe61-160">Update shaders and code as appropriate.</span></span>

<span data-ttu-id="8fe61-161">如果有某些場景無法支援轉譯成其他相機，您可以在 PhotoVideoCamera 的 HolographicViewConfiguration 期間停用它。</span><span class="sxs-lookup"><span data-stu-id="8fe61-161">If there are certain scenes that cannot support rendering to an additional camera, you can disable the PhotoVideoCamera's HolographicViewConfiguration during them.</span></span>

### <a name="disabling-mrc-in-your-app"></a><span data-ttu-id="8fe61-162">在您的應用程式中停用 MRC</span><span class="sxs-lookup"><span data-stu-id="8fe61-162">Disabling MRC in your app</span></span>

#### <a name="2d-app"></a><span data-ttu-id="8fe61-163">2D 應用程式</span><span class="sxs-lookup"><span data-stu-id="8fe61-163">2D app</span></span>

<span data-ttu-id="8fe61-164">當混合的現實捕捉正在執行時，2D 應用程式可以選擇將其視覺內容遮蔽：</span><span class="sxs-lookup"><span data-stu-id="8fe61-164">2D apps can choose to have their visual content obscured when mixed reality capture is running by:</span></span>
* <span data-ttu-id="8fe61-165">以 [DXGI_PRESENT_RESTRICT_TO_OUTPUT](https://docs.microsoft.com/windows/desktop/direct3ddxgi/dxgi-present) 旗標呈現</span><span class="sxs-lookup"><span data-stu-id="8fe61-165">Present with the [DXGI_PRESENT_RESTRICT_TO_OUTPUT](https://docs.microsoft.com/windows/desktop/direct3ddxgi/dxgi-present) flag</span></span>
* <span data-ttu-id="8fe61-166">使用 [DXGI_SWAP_CHAIN_FLAG_HW_PROTECTED](https://docs.microsoft.com/windows/desktop/api/dxgi/ne-dxgi-dxgi_swap_chain_flag) 旗標來建立應用程式的交換鏈</span><span class="sxs-lookup"><span data-stu-id="8fe61-166">Create the app's swap chain with the [DXGI_SWAP_CHAIN_FLAG_HW_PROTECTED](https://docs.microsoft.com/windows/desktop/api/dxgi/ne-dxgi-dxgi_swap_chain_flag) flag</span></span>
* <span data-ttu-id="8fe61-167">使用 Windows 10 2019 年5月更新，設定 ApplicationView 的 [IsScreenCaptureEnabled](https://docs.microsoft.com/uwp/api/windows.ui.viewmanagement.applicationview.isscreencaptureenabled)</span><span class="sxs-lookup"><span data-stu-id="8fe61-167">With the Windows 10 May 2019 Update, setting ApplicationView's [IsScreenCaptureEnabled](https://docs.microsoft.com/uwp/api/windows.ui.viewmanagement.applicationview.isscreencaptureenabled)</span></span>

#### <a name="immersive-app"></a><span data-ttu-id="8fe61-168">沉浸式應用程式</span><span class="sxs-lookup"><span data-stu-id="8fe61-168">Immersive app</span></span>

<span data-ttu-id="8fe61-169">沉浸式應用程式可以選擇從混合現實捕捉中排除其視覺內容：</span><span class="sxs-lookup"><span data-stu-id="8fe61-169">Immersive apps can choose to have their visual content excluded from mixed reality capture by:</span></span>
* <span data-ttu-id="8fe61-170">設定 HolographicCameraRenderingParameter 的 [IsContentProtectionEnabled](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.iscontentprotectionenabled) ，以停用其相關聯框架的混合現實 capture</span><span class="sxs-lookup"><span data-stu-id="8fe61-170">Setting HolographicCameraRenderingParameter's [IsContentProtectionEnabled](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.iscontentprotectionenabled) to disable mixed reality capture for its associated frame</span></span>
* <span data-ttu-id="8fe61-171">設定 HolographicCamera 的 [IsHardwareContentProtectionEnabled](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.ishardwarecontentprotectionenabled) ，以停用其相關聯的全像攝影相機的混合現實 capture</span><span class="sxs-lookup"><span data-stu-id="8fe61-171">Setting HolographicCamera's [IsHardwareContentProtectionEnabled](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.ishardwarecontentprotectionenabled) to disable mixed reality capture for its associated holographic camera</span></span>

#### <a name="password-keyboard"></a><span data-ttu-id="8fe61-172">密碼鍵盤</span><span class="sxs-lookup"><span data-stu-id="8fe61-172">Password Keyboard</span></span>

<span data-ttu-id="8fe61-173">使用 Windows 10 2019 年5月更新，在顯示密碼或 pin 鍵盤時，會自動從混合現實捕獲中排除視覺內容。</span><span class="sxs-lookup"><span data-stu-id="8fe61-173">With the Windows 10 May 2019 Update, visual content is automatically excluded from mixed reality capture when a password or pin keyboard is visible.</span></span>

### <a name="knowing-when-mrc-is-active"></a><span data-ttu-id="8fe61-174">知道當 MRC 處於作用中狀態</span><span class="sxs-lookup"><span data-stu-id="8fe61-174">Knowing when MRC is active</span></span>

<span data-ttu-id="8fe61-175">[AppCapture](https://docs.microsoft.com/uwp/api/Windows.Media.Capture.AppCapture)類別可供應用程式用來知道系統 mixed reality capture (針對音訊或影片) 執行時。</span><span class="sxs-lookup"><span data-stu-id="8fe61-175">The [AppCapture](https://docs.microsoft.com/uwp/api/Windows.Media.Capture.AppCapture) class can be used by an app to know when system mixed reality capture is running (for either audio or video).</span></span>

>[!NOTE]
><span data-ttu-id="8fe61-176">如果裝置上沒有混合現實 capture，AppCapture 的 [GetForCurrentView](https://docs.microsoft.com/uwp/api/windows.media.capture.appcapture.getforcurrentview) API 可能會傳回 null。</span><span class="sxs-lookup"><span data-stu-id="8fe61-176">AppCapture's [GetForCurrentView](https://docs.microsoft.com/uwp/api/windows.media.capture.appcapture.getforcurrentview) API can return null if mixed reality capture isn't available on the device.</span></span> <span data-ttu-id="8fe61-177">也請務必在您的應用程式暫停時，取消註冊 CapturingChanged 事件，否則，可能會進入封鎖狀態。</span><span class="sxs-lookup"><span data-stu-id="8fe61-177">It's also important to de-register the CapturingChanged event when your app is suspended, otherwise MRC can get into a blocked state.</span></span>

### <a name="best-practices-hololens-specific"></a><span data-ttu-id="8fe61-178"> (HoloLens 專用) 的最佳作法</span><span class="sxs-lookup"><span data-stu-id="8fe61-178">Best practices (HoloLens-specific)</span></span>

<span data-ttu-id="8fe61-179">MRC 預期會在沒有其他開發人員工作的情況下運作，但有幾件事要注意，以提供應用程式的最佳混合現實體驗體驗。</span><span class="sxs-lookup"><span data-stu-id="8fe61-179">MRC is expected to work without additional work from developers, but there are a few things to be aware of to provide the best mixed reality capture experience of your app.</span></span>

<span data-ttu-id="8fe61-180">**MRC 使用全像 [相機](locatable-camera.md) 的 Alpha 色板來 blend 影像**</span><span class="sxs-lookup"><span data-stu-id="8fe61-180">**MRC uses the hologram’s alpha channel to blend with the [camera](locatable-camera.md) imagery**</span></span>

<span data-ttu-id="8fe61-181">最重要的步驟是確保您的應用程式會清除為透明黑色，而不是清除為不透明的黑色。</span><span class="sxs-lookup"><span data-stu-id="8fe61-181">The most important step is to make sure your app is clearing to transparent black instead of clearing to opaque black.</span></span> <span data-ttu-id="8fe61-182">在 Unity 中，這會依預設使用 MixedRealityToolkit 完成，但如果您是在非 Unity 中進行開發，您可能需要進行一行變更。</span><span class="sxs-lookup"><span data-stu-id="8fe61-182">In Unity, this is done by default with the MixedRealityToolkit but if you are developing in non-Unity, you may need to make a one line change.</span></span>

<span data-ttu-id="8fe61-183">如果您的應用程式未清除為透明的黑色，您可能會在 MRC 中看到一些成品：</span><span class="sxs-lookup"><span data-stu-id="8fe61-183">Here are some of the artifacts you might see in MRC if your app is not clearing to transparent black:</span></span>

<span data-ttu-id="8fe61-184">**範例失敗**：內容周圍的黑色邊緣 (無法清除為透明黑色) </span><span class="sxs-lookup"><span data-stu-id="8fe61-184">**Example Failures**: Black edges around the content (failing to clear to transparent black)</span></span>

<table>
<tr>
<td>
<img src="images/chessboardblackedges-300px.jpg" alt="Failing to clear to transparent black: black edge artifacts around holograms"/>
</td>
<td>
<img src="images/fieldblackedges-300px.jpg" alt="Failing to clear to transparent black: black edge artifacts around holograms"/>
</td>
</tr>
</table>

<span data-ttu-id="8fe61-185">**失敗範例**：全像全像全螢幕的背景場景會顯示黑色。</span><span class="sxs-lookup"><span data-stu-id="8fe61-185">**Example Failures**: The entire background scene of the hologram appears black.</span></span> <span data-ttu-id="8fe61-186">將背景 Alpha 值設定為1會導致黑色背景</span><span class="sxs-lookup"><span data-stu-id="8fe61-186">Setting a background alpha value of 1 results in a black background</span></span>

![將背景 Alpha 值設定為1會導致黑色背景](images/clearopaqueblack-300px.png)

<span data-ttu-id="8fe61-188">**預期的結果**：如果清除透明) 黑色，則會以真實世界 (預期的結果來適當地混合影像：</span><span class="sxs-lookup"><span data-stu-id="8fe61-188">**Expected Result**: Holograms appear properly blended with the real-world (expected result if clearing to transparent black)</span></span>

![如果清除透明黑色，則預期的結果](images/cleartransparentblack-300px.png)

<span data-ttu-id="8fe61-190">**解決方案**：</span><span class="sxs-lookup"><span data-stu-id="8fe61-190">**Solution**:</span></span>
* <span data-ttu-id="8fe61-191">將顯示為不透明黑色的任何內容變更為具有 Alpha 值0。</span><span class="sxs-lookup"><span data-stu-id="8fe61-191">Change any content that is showing up as opaque black to have an alpha value of 0.</span></span>
* <span data-ttu-id="8fe61-192">確定應用程式已清除為透明的黑色。</span><span class="sxs-lookup"><span data-stu-id="8fe61-192">Ensure that the app is clearing to transparent black.</span></span>
* <span data-ttu-id="8fe61-193">Unity 預設為清除以使用 MixedRealityToolkit 自動清除，但如果它是非 Unity 應用程式，您應該修改與 ID3D11DeiceCoNtext：： ClearRenderTargetView 搭配使用的色彩， ( # A1。</span><span class="sxs-lookup"><span data-stu-id="8fe61-193">Unity defaults to clear to clear automatically with the MixedRealityToolkit, but if it’s a non-Unity app you should modify the color used with ID3D11DeiceContext::ClearRenderTargetView().</span></span> <span data-ttu-id="8fe61-194">您想要確保清楚透明的黑色 (0、0、0、0) ，而不是不透明的黑色 (0、0、0、1) 。</span><span class="sxs-lookup"><span data-stu-id="8fe61-194">You want to ensure you clear to transparent black (0,0,0,0) instead of opaque black (0,0,0,1).</span></span>

<span data-ttu-id="8fe61-195">如果您想要的話，現在可以調整資產的 Alpha 值，但通常不需要這麼做。</span><span class="sxs-lookup"><span data-stu-id="8fe61-195">You can now tune the alpha values of your assets if you’d like, but typically don’t need to.</span></span> <span data-ttu-id="8fe61-196">大部分的情況下，MRCs 都看起來不錯。</span><span class="sxs-lookup"><span data-stu-id="8fe61-196">Most of the time, MRCs will look good out of the box.</span></span> <span data-ttu-id="8fe61-197">MRC 假設預乘 Alpha。</span><span class="sxs-lookup"><span data-stu-id="8fe61-197">MRC assumes pre-multiplied alpha.</span></span> <span data-ttu-id="8fe61-198">Alpha 值只會影響 MRC 捕捉。</span><span class="sxs-lookup"><span data-stu-id="8fe61-198">The alpha values will only affect the MRC capture.</span></span>

### <a name="what-to-expect-when-mrc-is-enabled-on-hololens"></a><span data-ttu-id="8fe61-199">HoloLens 在 HoloLens 上啟用時的預期結果</span><span class="sxs-lookup"><span data-stu-id="8fe61-199">What to expect when MRC is enabled on HoloLens</span></span>

<span data-ttu-id="8fe61-200">下列適用于 HoloLens (第一代) 和 HoloLens 2，除非另有注明：</span><span class="sxs-lookup"><span data-stu-id="8fe61-200">The following apply to both HoloLens (first-generation) and HoloLens 2, unless otherwise noted:</span></span>

* <span data-ttu-id="8fe61-201">系統會將應用程式節流處理以30Hz 轉譯。</span><span class="sxs-lookup"><span data-stu-id="8fe61-201">The system will throttle the application to 30Hz rendering.</span></span> <span data-ttu-id="8fe61-202">這會建立一些可供 MRC 執行的空間，因此應用程式不需要保留固定的預算保留，也不需要符合30fps 的 MRC 影片記錄幀率</span><span class="sxs-lookup"><span data-stu-id="8fe61-202">This creates some headroom for MRC to run so the app doesn’t need to keep a constant budget reserve and also matches the MRC video record framerate of 30fps</span></span>
* <span data-ttu-id="8fe61-203">錄製/串流處理常式時，在裝置上顯示的全息圖內容可能會顯示為「閃爍」：文字可能會變得更難閱讀，而全息圖邊緣可能會變得更 jaggy， (在 **HoloLens 2** 上選擇第三個相機轉譯，以避免此折衷) </span><span class="sxs-lookup"><span data-stu-id="8fe61-203">Hologram content in the right eye of the device may appear to “sparkle” when recording/streaming MRC: text may become more difficult to read and hologram edges may appear more jaggy (opting-in to 3rd camera render on **HoloLens 2** avoids this compromise)</span></span>
* <span data-ttu-id="8fe61-204">如果應用程式已啟用，則 MRC 照片和影片將會遵循應用程式的 [焦點點](../unity/focus-point-in-unity.md) ，以協助確保全像投影正確放置。</span><span class="sxs-lookup"><span data-stu-id="8fe61-204">MRC photos and videos will respect the application’s [focus point](../unity/focus-point-in-unity.md) if the application has enabled it, which will help ensure holograms are accurately positioned.</span></span> <span data-ttu-id="8fe61-205">針對影片，焦點會經過平滑處理，如此一來，如果焦點深度的變更大幅改變，則可能會出現緩慢的漂移。</span><span class="sxs-lookup"><span data-stu-id="8fe61-205">For videos, the Focus Point is smoothed so holograms may appear to slowly drift into place if the Focus Point depth changes significantly.</span></span> <span data-ttu-id="8fe61-206">來自焦點點之不同深度的全像影像可能會顯示在現實世界的位移 (請參閱下方的範例，其中焦點點是設定為2個計量，但全像是放置在1個計量) 。</span><span class="sxs-lookup"><span data-stu-id="8fe61-206">Holograms that are at different depths from the focus point may appear offset from the real world (see example below where Focus Point is set at 2 meters but hologram is positioned at 1 meter).</span></span>

![2米的全像全像全球的全像投影。](images/hologramaccuracydistancemrc-1000px.png)

## <a name="integrating-mrc-functionality-from-within-your-app"></a><span data-ttu-id="8fe61-209">從您的應用程式內整合 MRC 功能</span><span class="sxs-lookup"><span data-stu-id="8fe61-209">Integrating MRC functionality from within your app</span></span>

<span data-ttu-id="8fe61-210">您的混合現實應用程式可以從應用程式內起始 MRC 照片或影片捕獲，而您的應用程式也可以使用所捕捉的內容，而不需儲存至裝置的「相機變換」。</span><span class="sxs-lookup"><span data-stu-id="8fe61-210">Your mixed reality app can initiate MRC photo or video capture from within the app, and the content captured is made available to your app without being stored to the device's "Camera roll."</span></span> <span data-ttu-id="8fe61-211">您可以建立自訂的「MRC 錄製器」，或利用內建的「相機捕捉」 UI。</span><span class="sxs-lookup"><span data-stu-id="8fe61-211">You can create a custom MRC recorder or take advantage of built-in camera capture UI.</span></span> 

### <a name="mrc-with-built-in-camera-ui"></a><span data-ttu-id="8fe61-212">使用內建相機 UI 的 MRC</span><span class="sxs-lookup"><span data-stu-id="8fe61-212">MRC with built-in camera UI</span></span>

<span data-ttu-id="8fe61-213">只要幾行程式碼，開發人員就可以使用 *[相機捕捉 UI API](https://docs.microsoft.com/windows/uwp/audio-video-camera/capture-photos-and-video-with-cameracaptureui)* 來取得使用者所取得的混合現實照片或影片。</span><span class="sxs-lookup"><span data-stu-id="8fe61-213">Developers can use the *[Camera Capture UI API](https://docs.microsoft.com/windows/uwp/audio-video-camera/capture-photos-and-video-with-cameracaptureui)* to get a user-captured mixed reality photo or video with just a few lines of code.</span></span>

<span data-ttu-id="8fe61-214">此 API 會啟動內建的「MRC 攝影機」 UI，讓使用者可以拍攝相片或影片，並將產生的捕獲傳回您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="8fe61-214">This API launches the built-in MRC camera UI, from which the user can take a photo or video, and returns the resulting capture to your app.</span></span>  <span data-ttu-id="8fe61-215">如果您想要建立自己的攝影機 UI，或需要較低層級的捕獲串流存取權，您可以建立自訂的混合實境擷取錄製器。</span><span class="sxs-lookup"><span data-stu-id="8fe61-215">If you want to create your own camera UI, or need lower-level access to the capture stream, you can create a custom Mixed Reality Capture recorder.</span></span>

### <a name="creating-a-custom-mrc-recorder"></a><span data-ttu-id="8fe61-216">建立自訂的 MRC 錄製器</span><span class="sxs-lookup"><span data-stu-id="8fe61-216">Creating a custom MRC recorder</span></span>

<span data-ttu-id="8fe61-217">雖然使用者一律可以使用系統 MRC 捕捉服務來觸發相片或影片，但應用程式可能會想要建立自訂相機應用程式，但在相機串流中包含全像 MRC 一樣的全像投影。</span><span class="sxs-lookup"><span data-stu-id="8fe61-217">While the user can always trigger a photo or video using the system MRC capture service, an application may want to build a custom camera app but include holograms in the camera stream just like MRC.</span></span> <span data-ttu-id="8fe61-218">這可讓應用程式代表使用者啟動捕獲、建立自訂錄製 UI，或自訂 MRC 設定來命名一些範例。</span><span class="sxs-lookup"><span data-stu-id="8fe61-218">This allows the application to kick off captures on behalf of the user, build custom recording UI, or customize MRC settings to name a few examples.</span></span>

<span data-ttu-id="8fe61-219">**HoloStudio 使用 MRC 效果新增自訂的 MRC 攝影機**</span><span class="sxs-lookup"><span data-stu-id="8fe61-219">**HoloStudio adds a custom MRC camera using MRC effects**</span></span>

![HoloStudio 使用 MRC 效果新增自訂的 MRC 攝影機](images/cameraiconholostudio-300px.jpg)

<span data-ttu-id="8fe61-221">Unity 應用程式應該會看到屬性 [Locatable_camera_in_Unity](../unity/locatable-camera-in-unity.md) ，以啟用全像。</span><span class="sxs-lookup"><span data-stu-id="8fe61-221">Unity Applications should see [Locatable_camera_in_Unity](../unity/locatable-camera-in-unity.md) for the property to enable holograms.</span></span>

<span data-ttu-id="8fe61-222">其他應用程式也可以使用 [Windows Media Capture api](https://docs.microsoft.com/uwp/api/Windows.Media.Capture.MediaCapture) 來控制相機，並新增 MRC 影片和音訊效果，以在靜止和影片中包含虛擬全像影像和應用程式音訊。</span><span class="sxs-lookup"><span data-stu-id="8fe61-222">Other applications can do this by using the [Windows Media Capture APIs](https://docs.microsoft.com/uwp/api/Windows.Media.Capture.MediaCapture) to control the Camera and add an MRC Video and Audio effect to include virtual holograms and application audio in stills and videos.</span></span>

<span data-ttu-id="8fe61-223">應用程式有兩個選項可新增效果：</span><span class="sxs-lookup"><span data-stu-id="8fe61-223">Applications have two options to add the effect:</span></span>
* <span data-ttu-id="8fe61-224">舊版 API： [MediaCapture. AddEffectAsync ( # B1 ](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacapture.addeffectasync)</span><span class="sxs-lookup"><span data-stu-id="8fe61-224">The older API: [Windows.Media.Capture.MediaCapture.AddEffectAsync()](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacapture.addeffectasync)</span></span>
* <span data-ttu-id="8fe61-225">新的 Microsoft 建議 API (會傳回物件，讓您可以操控動態屬性) ： [MediaCapture. AddVideoEffectAsync ( # B3](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacapture.addvideoeffectasync)  /  [MediaCapture.. AddAudioEffectAsync ( # B5](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacapture.addaudioeffectasync) ，這需要應用程式建立自己的[IVideoEffectDefinition](https://docs.microsoft.com/uwp/api/Windows.Media.Effects.IVideoEffectDefinition)和[IAudioEffectDefinition](https://docs.microsoft.com/uwp/api/windows.media.effects.iaudioeffectdefinition)執行。</span><span class="sxs-lookup"><span data-stu-id="8fe61-225">The new Microsoft recommended API (returns an object, making it possible to manipulate dynamic properties): [Windows.Media.Capture.MediaCapture.AddVideoEffectAsync()](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacapture.addvideoeffectasync) / [Windows.Media.Capture.MediaCapture.AddAudioEffectAsync()](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacapture.addaudioeffectasync) which require the app create its own implementation of [IVideoEffectDefinition](https://docs.microsoft.com/uwp/api/Windows.Media.Effects.IVideoEffectDefinition) and [IAudioEffectDefinition](https://docs.microsoft.com/uwp/api/windows.media.effects.iaudioeffectdefinition).</span></span> <span data-ttu-id="8fe61-226">請參閱 MRC [效果範例](https://docs.microsoft.com/windows/mixed-reality/develop/platform-capabilities-and-apis/mixed-reality-capture-for-developers#integrating-mrc-functionality-from-within-your-app) 以取得範例使用方式。</span><span class="sxs-lookup"><span data-stu-id="8fe61-226">Please see the MRC [effect sample](https://docs.microsoft.com/windows/mixed-reality/develop/platform-capabilities-and-apis/mixed-reality-capture-for-developers#integrating-mrc-functionality-from-within-your-app) for example usage.</span></span>

>[!NOTE]
> <span data-ttu-id="8fe61-227">Visual Studio 不會辨識 MixedRealityCapture 命名空間，但字串仍然有效。</span><span class="sxs-lookup"><span data-stu-id="8fe61-227">The Windows.Media.MixedRealityCapture namespace will not be recognized by Visual Studio, but the strings are still valid.</span></span>

<span data-ttu-id="8fe61-228">**MixedRealityCapture. MixedRealityCaptureVideoEffect**) 的 MRC 影片效果 (</span><span class="sxs-lookup"><span data-stu-id="8fe61-228">MRC Video Effect (**Windows.Media.MixedRealityCapture.MixedRealityCaptureVideoEffect**)</span></span>

|  <span data-ttu-id="8fe61-229">屬性名稱</span><span class="sxs-lookup"><span data-stu-id="8fe61-229">Property Name</span></span>  |  <span data-ttu-id="8fe61-230">類型</span><span class="sxs-lookup"><span data-stu-id="8fe61-230">Type</span></span>  |  <span data-ttu-id="8fe61-231">預設值</span><span class="sxs-lookup"><span data-stu-id="8fe61-231">Default Value</span></span>  |  <span data-ttu-id="8fe61-232">描述</span><span class="sxs-lookup"><span data-stu-id="8fe61-232">Description</span></span> |
|----------|----------|----------|----------|
|  <span data-ttu-id="8fe61-233">StreamType</span><span class="sxs-lookup"><span data-stu-id="8fe61-233">StreamType</span></span>  |  <span data-ttu-id="8fe61-234">UINT32 ([MediaStreamType](https://docs.microsoft.com/uwp/api/Windows.Media.Capture.MediaStreamType)) </span><span class="sxs-lookup"><span data-stu-id="8fe61-234">UINT32 ([MediaStreamType](https://docs.microsoft.com/uwp/api/Windows.Media.Capture.MediaStreamType))</span></span>  |  <span data-ttu-id="8fe61-235">1 (VideoRecord) </span><span class="sxs-lookup"><span data-stu-id="8fe61-235">1 (VideoRecord)</span></span>  |  <span data-ttu-id="8fe61-236">描述此效果用於哪個捕獲資料流程。</span><span class="sxs-lookup"><span data-stu-id="8fe61-236">Describe which capture stream this effect is used for.</span></span> <span data-ttu-id="8fe61-237">無法使用音訊。</span><span class="sxs-lookup"><span data-stu-id="8fe61-237">Audio is not available.</span></span> |
|  <span data-ttu-id="8fe61-238">HologramCompositionEnabled</span><span class="sxs-lookup"><span data-stu-id="8fe61-238">HologramCompositionEnabled</span></span>  |  <span data-ttu-id="8fe61-239">boolean</span><span class="sxs-lookup"><span data-stu-id="8fe61-239">boolean</span></span>  |  <span data-ttu-id="8fe61-240">true</span><span class="sxs-lookup"><span data-stu-id="8fe61-240">TRUE</span></span>  |  <span data-ttu-id="8fe61-241">用來啟用或停用影片捕獲中全像影像的旗標。</span><span class="sxs-lookup"><span data-stu-id="8fe61-241">Flag to enable or disable holograms in video capture.</span></span> |
|  <span data-ttu-id="8fe61-242">RecordingIndicatorEnabled</span><span class="sxs-lookup"><span data-stu-id="8fe61-242">RecordingIndicatorEnabled</span></span>  |  <span data-ttu-id="8fe61-243">boolean</span><span class="sxs-lookup"><span data-stu-id="8fe61-243">boolean</span></span>  |  <span data-ttu-id="8fe61-244">true</span><span class="sxs-lookup"><span data-stu-id="8fe61-244">TRUE</span></span>  |  <span data-ttu-id="8fe61-245">用來啟用或停用全息圖捕獲期間在螢幕上錄製指標的旗標。</span><span class="sxs-lookup"><span data-stu-id="8fe61-245">Flag to enable or disable recording indicator on screen during hologram capturing.</span></span> |
|  <span data-ttu-id="8fe61-246">VideoStabilizationEnabled</span><span class="sxs-lookup"><span data-stu-id="8fe61-246">VideoStabilizationEnabled</span></span>  |  <span data-ttu-id="8fe61-247">boolean</span><span class="sxs-lookup"><span data-stu-id="8fe61-247">boolean</span></span>  |  <span data-ttu-id="8fe61-248">false</span><span class="sxs-lookup"><span data-stu-id="8fe61-248">FALSE</span></span>  |  <span data-ttu-id="8fe61-249">此旗標可啟用或停用由 HoloLens 追蹤器提供技術支援的影片穩定。</span><span class="sxs-lookup"><span data-stu-id="8fe61-249">Flag to enable or disable video stabilization powered by the HoloLens tracker.</span></span> |
|  <span data-ttu-id="8fe61-250">VideoStabilizationBufferLength</span><span class="sxs-lookup"><span data-stu-id="8fe61-250">VideoStabilizationBufferLength</span></span>  |  <span data-ttu-id="8fe61-251">UINT32</span><span class="sxs-lookup"><span data-stu-id="8fe61-251">UINT32</span></span>  |  <span data-ttu-id="8fe61-252">0</span><span class="sxs-lookup"><span data-stu-id="8fe61-252">0</span></span>  |  <span data-ttu-id="8fe61-253">設定用於視頻穩定的歷程記錄畫面格數目。</span><span class="sxs-lookup"><span data-stu-id="8fe61-253">Set how many historical frames are used for video stabilization.</span></span> <span data-ttu-id="8fe61-254">0從電源和效能的觀點來看，有0延遲且幾乎「免費」。</span><span class="sxs-lookup"><span data-stu-id="8fe61-254">0 is 0-latency and nearly "free" from a power and performance perspective.</span></span> <span data-ttu-id="8fe61-255">針對最高品質 (，建議使用15，但延遲和記憶體) 的15個框架成本。</span><span class="sxs-lookup"><span data-stu-id="8fe61-255">15 is recommended for highest quality (at the cost of 15 frames of latency and memory).</span></span> |
|  <span data-ttu-id="8fe61-256">GlobalOpacityCoefficient</span><span class="sxs-lookup"><span data-stu-id="8fe61-256">GlobalOpacityCoefficient</span></span>  |  <span data-ttu-id="8fe61-257">FLOAT</span><span class="sxs-lookup"><span data-stu-id="8fe61-257">float</span></span>  |  <span data-ttu-id="8fe61-258">0.9 (HoloLens) 1.0 (沉浸式耳機) </span><span class="sxs-lookup"><span data-stu-id="8fe61-258">0.9 (HoloLens) 1.0 (Immersive headset)</span></span>  |  <span data-ttu-id="8fe61-259">在 0.0 (完全透明) 至 1.0 (完全不透明的) ，設定全像影像的全域不透明度係數。</span><span class="sxs-lookup"><span data-stu-id="8fe61-259">Set global opacity coefficient of hologram in range from 0.0 (fully transparent) to 1.0 (fully opaque).</span></span> |
|  <span data-ttu-id="8fe61-260">BlankOnProtectedContent</span><span class="sxs-lookup"><span data-stu-id="8fe61-260">BlankOnProtectedContent</span></span>  |  <span data-ttu-id="8fe61-261">boolean</span><span class="sxs-lookup"><span data-stu-id="8fe61-261">boolean</span></span>  |  <span data-ttu-id="8fe61-262">false</span><span class="sxs-lookup"><span data-stu-id="8fe61-262">FALSE</span></span>  |  <span data-ttu-id="8fe61-263">如果有 2d UWP 應用程式顯示受保護的內容，則為啟用或停用會傳回空框架的旗標。</span><span class="sxs-lookup"><span data-stu-id="8fe61-263">Flag to enable or disable returning an empty frame if there is a 2d UWP app showing protected content.</span></span> <span data-ttu-id="8fe61-264">如果此旗標為 false，而 2d UWP 應用程式顯示受保護的內容，則會在耳機和混合式現實捕捉中，以受保護的內容材質取代 2d UWP 應用程式。</span><span class="sxs-lookup"><span data-stu-id="8fe61-264">If this flag is false and a 2d UWP app is showing protected content, the 2d UWP app will be replaced by a protected content texture in both the headset and in the mixed reality capture.</span></span> |
|  <span data-ttu-id="8fe61-265">ShowHiddenMesh</span><span class="sxs-lookup"><span data-stu-id="8fe61-265">ShowHiddenMesh</span></span>  |  <span data-ttu-id="8fe61-266">boolean</span><span class="sxs-lookup"><span data-stu-id="8fe61-266">boolean</span></span>  |  <span data-ttu-id="8fe61-267">false</span><span class="sxs-lookup"><span data-stu-id="8fe61-267">FALSE</span></span>  |  <span data-ttu-id="8fe61-268">啟用或停用的旗標，顯示全像攝影的隱藏區域網格和連續的內容。</span><span class="sxs-lookup"><span data-stu-id="8fe61-268">Flag to enable or disable showing the holographic camera's hidden area mesh and neighboring content.</span></span> |
| <span data-ttu-id="8fe61-269">OutputSize</span><span class="sxs-lookup"><span data-stu-id="8fe61-269">OutputSize</span></span> | <span data-ttu-id="8fe61-270">大小</span><span class="sxs-lookup"><span data-stu-id="8fe61-270">Size</span></span> | <span data-ttu-id="8fe61-271">0, 0</span><span class="sxs-lookup"><span data-stu-id="8fe61-271">0, 0</span></span> | <span data-ttu-id="8fe61-272">在裁剪影片穩定之後，設定所需的輸出大小。</span><span class="sxs-lookup"><span data-stu-id="8fe61-272">Set the desired output size after cropping for video stabilization.</span></span> <span data-ttu-id="8fe61-273">如果指定0或不正確輸出大小，則會選擇預設裁剪大小。</span><span class="sxs-lookup"><span data-stu-id="8fe61-273">A default crop size is chosen if 0 or an invalid output size is specified.</span></span> |
| <span data-ttu-id="8fe61-274">PreferredHologramPerspective</span><span class="sxs-lookup"><span data-stu-id="8fe61-274">PreferredHologramPerspective</span></span> | <span data-ttu-id="8fe61-275">UINT32</span><span class="sxs-lookup"><span data-stu-id="8fe61-275">UINT32</span></span> | <span data-ttu-id="8fe61-276">**從** Windows 裝置入口網站中的相機設定轉譯</span><span class="sxs-lookup"><span data-stu-id="8fe61-276">**Render from Camera** setting in the Windows Device Portal</span></span> | <span data-ttu-id="8fe61-277">列舉用來指出應捕捉的全像攝影相機視圖設定： 0 (顯示) 表示不會要求應用程式從相片/攝影機轉譯，1 (PhotoVideoCamera) 將會要求應用程式從相片/視頻攝影機轉譯 (如果應用程式支援) 。</span><span class="sxs-lookup"><span data-stu-id="8fe61-277">Enum used to indicate which holographic camera view configuration should be captured: 0 (Display) means that the app won't be asked to render from the photo/video camera, 1 (PhotoVideoCamera) will ask the app to render from the photo/video camera (if the app supports it).</span></span> <span data-ttu-id="8fe61-278">僅 HoloLens 2 支援</span><span class="sxs-lookup"><span data-stu-id="8fe61-278">Only supported on HoloLens 2</span></span> |

>[!NOTE]
> <span data-ttu-id="8fe61-279">您可以在 Windows 裝置入口網站中變更 **PreferredHologramPerspective** 的預設值，方法是前往 [ [混合實境擷取] 頁面](using-the-windows-device-portal.md#mixed-reality-capture) ，並取消核取 [ **從相機**轉譯]。</span><span class="sxs-lookup"><span data-stu-id="8fe61-279">You can change the default value of **PreferredHologramPerspective** in the Windows Device Portal by going to the [Mixed Reality Capture page](using-the-windows-device-portal.md#mixed-reality-capture) and unchecking **Render from Camera**.</span></span> <span data-ttu-id="8fe61-280">此設定預設為 \*\*1 (PhotoVideoCamera) \*\*，但可以取消核取，將它設為 \*\*0 (顯示) \*\*。</span><span class="sxs-lookup"><span data-stu-id="8fe61-280">The setting defaults to **1 (PhotoVideoCamera)**, but can be unchecked to set it to **0 (Display)**.</span></span>
>
> <span data-ttu-id="8fe61-281">**PreferredHologramPerspective**的預設值為**0 (顯示**2020 年6月更新 (Windows 全像2004版組建19041.1106 和 windows 全像1903組建 18362.1064) 的) 。</span><span class="sxs-lookup"><span data-stu-id="8fe61-281">The default value of **PreferredHologramPerspective** was **0 (Display)** prior to the June 2020 update (Windows Holographic, version 2004 build 19041.1106 and Windows Holographic, version 1903 build 18362.1064).</span></span>

<span data-ttu-id="8fe61-282">**MixedRealityCapture. MixedRealityCaptureAudioEffect) 的**MRC 音訊效果 (</span><span class="sxs-lookup"><span data-stu-id="8fe61-282">MRC Audio Effect (**Windows.Media.MixedRealityCapture.MixedRealityCaptureAudioEffect**)</span></span>

| <span data-ttu-id="8fe61-283">屬性名稱</span><span class="sxs-lookup"><span data-stu-id="8fe61-283">Property Name</span></span> | <span data-ttu-id="8fe61-284">類型</span><span class="sxs-lookup"><span data-stu-id="8fe61-284">Type</span></span> | <span data-ttu-id="8fe61-285">預設值</span><span class="sxs-lookup"><span data-stu-id="8fe61-285">Default Value</span></span> | <span data-ttu-id="8fe61-286">描述</span><span class="sxs-lookup"><span data-stu-id="8fe61-286">Description</span></span> |
|----------|----------|----------|----------|
| <span data-ttu-id="8fe61-287">MixerMode</span><span class="sxs-lookup"><span data-stu-id="8fe61-287">MixerMode</span></span> | <span data-ttu-id="8fe61-288">UINT32</span><span class="sxs-lookup"><span data-stu-id="8fe61-288">UINT32</span></span> | <span data-ttu-id="8fe61-289">2 (Mic 和系統音訊) </span><span class="sxs-lookup"><span data-stu-id="8fe61-289">2 (Mic and System audio)</span></span> | <span data-ttu-id="8fe61-290">用來指出應使用哪些音訊來源的列舉： 0 (僅限 Mic 音訊) 、1 (僅限系統音訊) 、2 (Mic 和系統音訊) </span><span class="sxs-lookup"><span data-stu-id="8fe61-290">Enum used to indicate which audio sources should be used: 0 (Mic audio only), 1 (System audio only), 2 (Mic and System audio)</span></span> |
| <span data-ttu-id="8fe61-291">LoopbackGain</span><span class="sxs-lookup"><span data-stu-id="8fe61-291">LoopbackGain</span></span> | <span data-ttu-id="8fe61-292">FLOAT</span><span class="sxs-lookup"><span data-stu-id="8fe61-292">float</span></span> | <span data-ttu-id="8fe61-293">Windows 裝置入口網站中的**應用程式音訊增益**設定</span><span class="sxs-lookup"><span data-stu-id="8fe61-293">**App Audio Gain** setting in the Windows Device Portal</span></span> | <span data-ttu-id="8fe61-294">適用于系統音訊音量的增益。</span><span class="sxs-lookup"><span data-stu-id="8fe61-294">Gain to apply to system audio volume.</span></span> <span data-ttu-id="8fe61-295">範圍從0.0 到5.0。</span><span class="sxs-lookup"><span data-stu-id="8fe61-295">Ranges from 0.0 to 5.0.</span></span> <span data-ttu-id="8fe61-296">僅 HoloLens 2 支援</span><span class="sxs-lookup"><span data-stu-id="8fe61-296">Only supported on HoloLens 2</span></span> |
| <span data-ttu-id="8fe61-297">MicrophoneGain</span><span class="sxs-lookup"><span data-stu-id="8fe61-297">MicrophoneGain</span></span> | <span data-ttu-id="8fe61-298">FLOAT</span><span class="sxs-lookup"><span data-stu-id="8fe61-298">float</span></span> | <span data-ttu-id="8fe61-299">Windows 裝置入口網站中的**Mic 音訊增益**設定</span><span class="sxs-lookup"><span data-stu-id="8fe61-299">**Mic Audio Gain** setting in the Windows Device Portal</span></span> | <span data-ttu-id="8fe61-300">適用于 mic 音量的增益。</span><span class="sxs-lookup"><span data-stu-id="8fe61-300">Gain to apply to mic volume.</span></span> <span data-ttu-id="8fe61-301">範圍從0.0 到5.0。</span><span class="sxs-lookup"><span data-stu-id="8fe61-301">Ranges from 0.0 to 5.0.</span></span> <span data-ttu-id="8fe61-302">僅 HoloLens 2 支援</span><span class="sxs-lookup"><span data-stu-id="8fe61-302">Only supported on HoloLens 2</span></span> |

>[!NOTE]
> <span data-ttu-id="8fe61-303">您可以在 Windows 裝置入口網站中變更 **LoopbackGain** 或 **MicrophoneGain** 的預設值，方法是移至 [ [混合實境擷取] 頁面](using-the-windows-device-portal.md#mixed-reality-capture) ，然後調整其各自設定旁邊的滑杆。</span><span class="sxs-lookup"><span data-stu-id="8fe61-303">You can change the default value of **LoopbackGain** or **MicrophoneGain** in the Windows Device Portal by going to the [Mixed Reality Capture page](using-the-windows-device-portal.md#mixed-reality-capture) and adjusting the slider next to their respective settings.</span></span> <span data-ttu-id="8fe61-304">這兩個設定預設為 **1.0**，但可以設定為 **0.0** 與 **5.0**之間的任何值。</span><span class="sxs-lookup"><span data-stu-id="8fe61-304">Both settings default to **1.0**, but can be set to any value between **0.0** and **5.0**.</span></span>
>
> <span data-ttu-id="8fe61-305">在2020年6月的更新中，您可以使用 Windows 裝置入口網站來設定預設增益值 (Windows 全像2004組建19041.1106 和 Windows 全像版本1903組建 18362.1064) 。</span><span class="sxs-lookup"><span data-stu-id="8fe61-305">Using Windows Device Portal to configure the default gain values was added with the June 2020 update (Windows Holographic, version 2004 build 19041.1106 and Windows Holographic, version 1903 build 18362.1064).</span></span>

### <a name="simultaneous-mrc-limitations"></a><span data-ttu-id="8fe61-306">同時 MRC 限制</span><span class="sxs-lookup"><span data-stu-id="8fe61-306">Simultaneous MRC limitations</span></span>

<span data-ttu-id="8fe61-307">有多個應用程式同時存取 MRC 有一些限制。</span><span class="sxs-lookup"><span data-stu-id="8fe61-307">There are certain limitations around multiple apps accessing MRC at the same time.</span></span>

#### <a name="photovideo-camera-access"></a><span data-ttu-id="8fe61-308">相片/攝影機存取</span><span class="sxs-lookup"><span data-stu-id="8fe61-308">Photo/video camera access</span></span>

<span data-ttu-id="8fe61-309">相片/攝影機受限於可同時存取它的進程數目。</span><span class="sxs-lookup"><span data-stu-id="8fe61-309">The photo/video camera is limited to the number of processes that can access it at the same time.</span></span> <span data-ttu-id="8fe61-310">當處理常式錄製影片或拍攝相片時，任何其他程式將無法取得相片/攝影機。</span><span class="sxs-lookup"><span data-stu-id="8fe61-310">While a process is recording video or taking a photo any other process will fail to acquire the photo/video camera.</span></span> <span data-ttu-id="8fe61-311"> (這適用于混合實境擷取和標準相片/影片捕獲) </span><span class="sxs-lookup"><span data-stu-id="8fe61-311">(this applies to both Mixed Reality Capture and standard photo/video capture)</span></span>

<span data-ttu-id="8fe61-312">使用 HoloLens 2 時，應用程式可以使用 MediaCaptureInitializationSettings 的 [SharingMode](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacaptureinitializationsettings.sharingmode) 屬性，來指出如果它們不需要對相片/攝影機進行獨佔控制，他們想要執行 SharedReadOnly。</span><span class="sxs-lookup"><span data-stu-id="8fe61-312">With HoloLens 2, an app can use MediaCaptureInitializationSettings' [SharingMode](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacaptureinitializationsettings.sharingmode) property to indicate that they want to run SharedReadOnly if they don't need exclusive control over the photo/video camera.</span></span> <span data-ttu-id="8fe61-313">如此一來，就會限制捕捉的解析度和畫面播放速率將會限制為其他應用程式已設定相機來提供。</span><span class="sxs-lookup"><span data-stu-id="8fe61-313">Doing so means the resolution and framerate of the capture will be limited to what other apps have configured the camera to provide.</span></span>

##### <a name="built-in-mrc-photovideo-camera-access"></a><span data-ttu-id="8fe61-314">內建的 MRC 相片/攝影機存取</span><span class="sxs-lookup"><span data-stu-id="8fe61-314">Built-in MRC photo/video camera access</span></span>

<span data-ttu-id="8fe61-315">內建于透過 Cortana、[開始] 功能表、硬體快捷方式、Miracast、Windows 裝置入口網站) 的 Windows 10 (的 MRC 功能：</span><span class="sxs-lookup"><span data-stu-id="8fe61-315">MRC functionality built into Windows 10 (via Cortana, Start Menu, hardware shortcuts, Miracast, Windows Device Portal):</span></span>
* <span data-ttu-id="8fe61-316">預設會以 ExclusiveControl 執行</span><span class="sxs-lookup"><span data-stu-id="8fe61-316">Will run with ExclusiveControl by default</span></span>

<span data-ttu-id="8fe61-317">不過，每個子系統都已新增支援，以在共用模式下運作：</span><span class="sxs-lookup"><span data-stu-id="8fe61-317">However, support has been added to each subsystem to operate in a shared mode:</span></span>
* <span data-ttu-id="8fe61-318">如果應用程式要求相片/攝影機的 ExclusiveControl 存取權，內建的 MRC 將會自動停止使用相片/攝影機，因此應用程式的要求將會成功</span><span class="sxs-lookup"><span data-stu-id="8fe61-318">If an app requests ExclusiveControl access to the photo/video camera, built-in MRC will automatically stop using the photo/video camera so the app's request will succeed</span></span>
* <span data-ttu-id="8fe61-319">如果在應用程式 ExclusiveControl 時啟動內建的 MRC，內建的 MRC 將會以 SharedReadOnly 模式執行</span><span class="sxs-lookup"><span data-stu-id="8fe61-319">If built-in MRC is started while an app has ExclusiveControl, built-in MRC will run in SharedReadOnly mode</span></span>

<span data-ttu-id="8fe61-320">此共用模式功能有某些限制：</span><span class="sxs-lookup"><span data-stu-id="8fe61-320">This shared mode functionality has certain restrictions:</span></span>
* <span data-ttu-id="8fe61-321">透過 Cortana、硬體快速鍵或 [開始] 功能表的相片：需要 Windows 10 2018 年4月更新 (或更新版本) </span><span class="sxs-lookup"><span data-stu-id="8fe61-321">Photo via Cortana, hardware shortcuts, or Start Menu: Requires the Windows 10 April 2018 Update (or later)</span></span>
* <span data-ttu-id="8fe61-322">透過 Cortana、硬體快速鍵或 [開始] 功能表的影片：需要 Windows 10 2018 年4月更新 (或更新版本) </span><span class="sxs-lookup"><span data-stu-id="8fe61-322">Video via Cortana, hardware shortcuts, or Start Menu: Requires the Windows 10 April 2018 Update (or later)</span></span>
* <span data-ttu-id="8fe61-323">透過 Miracast 的串流處理 MRC：需要 Windows 10 2018 年10月更新 (或更新版本) </span><span class="sxs-lookup"><span data-stu-id="8fe61-323">Streaming MRC over Miracast: Requires the Windows 10 October 2018 Update (or later)</span></span>
* <span data-ttu-id="8fe61-324">透過 Windows 裝置入口網站或透過 HoloLens 附屬應用程式串流處理 MRC：需要 HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="8fe61-324">Streaming MRC over Windows Device Portal or via the HoloLens companion app: Requires HoloLens 2</span></span>

>[!NOTE]
> <span data-ttu-id="8fe61-325">當另一個應用程式正在使用相片/攝影機時，內建的 MRC 攝影機 UI 的解析度和畫面播放速率可能會從其正常值減少。</span><span class="sxs-lookup"><span data-stu-id="8fe61-325">The resolution and framerate of the built-in MRC camera UI might be reduced from its normal values when another app is using the photo/video camera.</span></span>

#### <a name="mrc-access"></a><span data-ttu-id="8fe61-326">MRC 存取</span><span class="sxs-lookup"><span data-stu-id="8fe61-326">MRC access</span></span>

<span data-ttu-id="8fe61-327">有了 Windows 10 2018 年4月更新，存取 MRC 串流的多個應用程式就不再有限制 (不過，相片/攝影機的存取權仍有) 的限制。</span><span class="sxs-lookup"><span data-stu-id="8fe61-327">With the Windows 10 April 2018 Update, there is no longer a limitation around multiple apps accessing the MRC stream (however, the access to the photo/video camera still has limitations).</span></span>

<span data-ttu-id="8fe61-328">在 Windows 10 2018 年4月更新之前，應用程式的自訂 MRC 錄製器與系統 MRC 的互斥 (捕獲相片、捕獲影片或從 Windows 裝置入口網站) 進行串流。</span><span class="sxs-lookup"><span data-stu-id="8fe61-328">Previous to the Windows 10 April 2018 Update, an app's custom MRC recorder was mutually exclusive with system MRC (capturing photos, capturing videos, or streaming from the Windows Device Portal).</span></span>

## <a name="see-also"></a><span data-ttu-id="8fe61-329">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8fe61-329">See also</span></span>

* [<span data-ttu-id="8fe61-330">混合實境擷取</span><span class="sxs-lookup"><span data-stu-id="8fe61-330">Mixed reality capture</span></span>](../../mixed-reality-capture.md)
* [<span data-ttu-id="8fe61-331">觀眾檢視</span><span class="sxs-lookup"><span data-stu-id="8fe61-331">Spectator view</span></span>](spectator-view.md)
* [<span data-ttu-id="8fe61-332">Unity 開發總覽</span><span class="sxs-lookup"><span data-stu-id="8fe61-332">Unity Development Overview</span></span>](../unity/unity-development-overview.md)
* [<span data-ttu-id="8fe61-333">Unreal 開發概觀</span><span class="sxs-lookup"><span data-stu-id="8fe61-333">Unreal development overview</span></span>](../unreal/unreal-development-overview.md)
