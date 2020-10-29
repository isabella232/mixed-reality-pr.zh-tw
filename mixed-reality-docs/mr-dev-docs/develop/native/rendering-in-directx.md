---
title: DirectX 中的呈現
description: 說明 Windows Mixed Reality 的全息轉譯。
author: mikeriches
ms.author: mriches
ms.date: 08/04/2020
ms.topic: article
keywords: Windows Mixed Reality、全息圖、轉譯、3D 圖形、HolographicFrame、轉譯迴圈、更新迴圈、逐步解說、範例程式碼、Direct3D
ms.openlocfilehash: 4c1e6207dd7e858a323ea5234f2849e6a3bdfab3
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2020
ms.locfileid: "91679329"
---
# <a name="rendering-in-directx"></a><span data-ttu-id="8e564-104">DirectX 中的呈現</span><span class="sxs-lookup"><span data-stu-id="8e564-104">Rendering in DirectX</span></span>

> [!NOTE]
> <span data-ttu-id="8e564-105">本文與舊版 WinRT 原生 Api 相關。</span><span class="sxs-lookup"><span data-stu-id="8e564-105">This article relates to the legacy WinRT native APIs.</span></span>  <span data-ttu-id="8e564-106">針對新的原生應用程式專案，建議使用 **[OPENXR API](openxr-getting-started.md)** 。</span><span class="sxs-lookup"><span data-stu-id="8e564-106">For new native app projects, we recommend using the **[OpenXR API](openxr-getting-started.md)** .</span></span>

<span data-ttu-id="8e564-107">Windows Mixed Reality 建基於 DirectX，為使用者產生豐富的3D 圖形體驗。</span><span class="sxs-lookup"><span data-stu-id="8e564-107">Windows Mixed Reality is built on DirectX to produce rich, 3D graphical experiences for users.</span></span> <span data-ttu-id="8e564-108">轉譯抽象概念位於 DirectX 之上，並可讓應用程式考慮全像系統所預測的全像全像全像攝影場景的位置和方向。</span><span class="sxs-lookup"><span data-stu-id="8e564-108">The rendering abstraction sits just above DirectX and lets an app reason about the position and orientation of one or more observers of a holographic scene, as predicted by the system.</span></span> <span data-ttu-id="8e564-109">然後，開發人員可以找出相對於每個相機的全像投影，讓應用程式在使用者四處移動時，轉譯各種空間座標系統中的全像影像。</span><span class="sxs-lookup"><span data-stu-id="8e564-109">The developer can then locate their holograms relative to each camera, letting the app render these holograms in various spatial coordinate systems as the user moves around.</span></span>

<span data-ttu-id="8e564-110">注意：此逐步解說說明 Direct3D 11 中的全像轉譯。</span><span class="sxs-lookup"><span data-stu-id="8e564-110">Note: This walkthrough describes holographic rendering in Direct3D 11.</span></span> <span data-ttu-id="8e564-111">您也可以使用「混合現實應用程式範本」延伸模組來提供 Direct3D 12 Windows Mixed Reality 應用程式範本。</span><span class="sxs-lookup"><span data-stu-id="8e564-111">A Direct3D 12 Windows Mixed Reality app template is also supplied with the Mixed Reality app templates extension.</span></span>

## <a name="update-for-the-current-frame"></a><span data-ttu-id="8e564-112">目前畫面格的更新</span><span class="sxs-lookup"><span data-stu-id="8e564-112">Update for the current frame</span></span>

<span data-ttu-id="8e564-113">若要更新影像的應用程式狀態，每個畫面格一次，應用程式將會：</span><span class="sxs-lookup"><span data-stu-id="8e564-113">To update the application state for holograms, once per frame the app will:</span></span>
* <span data-ttu-id="8e564-114">從顯示管理系統取得 <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> 。</span><span class="sxs-lookup"><span data-stu-id="8e564-114">Get a <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> from the display management system.</span></span>
* <span data-ttu-id="8e564-115">在轉譯完成時，使用相機視圖的目前預測來更新場景。</span><span class="sxs-lookup"><span data-stu-id="8e564-115">Update the scene with the current prediction of where the camera view will be when render is completed.</span></span> <span data-ttu-id="8e564-116">請注意，全像攝影場景可以有一個以上的相機。</span><span class="sxs-lookup"><span data-stu-id="8e564-116">Note, there can be more than one camera for the holographic scene.</span></span>

<span data-ttu-id="8e564-117">若要轉譯成全像攝影相機，每個畫面格一次，應用程式將會：</span><span class="sxs-lookup"><span data-stu-id="8e564-117">To render to holographic camera views, once per frame the app will:</span></span>
* <span data-ttu-id="8e564-118">針對每個相機，使用系統中的相機視圖和投影矩陣，轉譯目前框架的場景。</span><span class="sxs-lookup"><span data-stu-id="8e564-118">For each camera, render the scene for the current frame, using the camera view and projection matrices from the system.</span></span>

### <a name="create-a-new-holographic-frame-and-get-its-prediction"></a><span data-ttu-id="8e564-119">建立新的全像攝影框架並取得其預測</span><span class="sxs-lookup"><span data-stu-id="8e564-119">Create a new holographic frame and get its prediction</span></span>

<span data-ttu-id="8e564-120"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>具有應用程式所需的資訊，以便更新和轉譯目前的框架。</span><span class="sxs-lookup"><span data-stu-id="8e564-120">The <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> has information that the app needs in order to update and render the current frame.</span></span> <span data-ttu-id="8e564-121">應用程式會藉由呼叫 **CreateNextFrame** 方法來開始每個新的框架。</span><span class="sxs-lookup"><span data-stu-id="8e564-121">The app begins each new frame by calling the **CreateNextFrame** method.</span></span> <span data-ttu-id="8e564-122">當呼叫這個方法時，會使用最新可用的感應器資料來進行預測，並封裝在 **CurrentPrediction** 物件中。</span><span class="sxs-lookup"><span data-stu-id="8e564-122">When this method is called, predictions are made using the latest sensor data available, and encapsulated in **CurrentPrediction** object.</span></span>

<span data-ttu-id="8e564-123">必須針對每個呈現的框架使用新的框架物件，因為它只適用于及時的有效時間。</span><span class="sxs-lookup"><span data-stu-id="8e564-123">A new frame object must be used for each rendered frame as it is only valid for an instant in time.</span></span> <span data-ttu-id="8e564-124">**CurrentPrediction** 屬性包含攝影機位置之類的資訊。</span><span class="sxs-lookup"><span data-stu-id="8e564-124">The **CurrentPrediction** property contains information such as the camera position.</span></span> <span data-ttu-id="8e564-125">這項資訊會在預期使用者看到畫面格的確切時間點推斷。</span><span class="sxs-lookup"><span data-stu-id="8e564-125">The information is extrapolated to the exact moment in time when the frame is expected to be visible to the user.</span></span>

<span data-ttu-id="8e564-126">下列程式碼會從 **AppMain：： Update** 摘錄：</span><span class="sxs-lookup"><span data-stu-id="8e564-126">The following code is excerpted from **AppMain::Update** :</span></span>

```cpp
// The HolographicFrame has information that the app needs in order
// to update and render the current frame. The app begins each new
// frame by calling CreateNextFrame.
HolographicFrame holographicFrame = m_holographicSpace.CreateNextFrame();

// Get a prediction of where holographic cameras will be when this frame
// is presented.
HolographicFramePrediction prediction = holographicFrame.CurrentPrediction();
```

### <a name="process-camera-updates"></a><span data-ttu-id="8e564-127">處理相機更新</span><span class="sxs-lookup"><span data-stu-id="8e564-127">Process camera updates</span></span>

<span data-ttu-id="8e564-128">背景緩衝區可以從框架變更為框架。</span><span class="sxs-lookup"><span data-stu-id="8e564-128">Back buffers can change from frame to frame.</span></span> <span data-ttu-id="8e564-129">您的應用程式必須驗證每個相機的後置緩衝區，並視需要釋放和重新建立資源檢視和深度緩衝區。</span><span class="sxs-lookup"><span data-stu-id="8e564-129">Your app needs to validate the back buffer for each camera, and release and recreate resource views and depth buffers as needed.</span></span> <span data-ttu-id="8e564-130">請注意，預測中的一組姿勢是目前框架中使用的相機授權清單。</span><span class="sxs-lookup"><span data-stu-id="8e564-130">Notice that the set of poses in the prediction is the authoritative list of cameras being used in the current frame.</span></span> <span data-ttu-id="8e564-131">通常，您可以使用這份清單來逐一查看一組攝影機。</span><span class="sxs-lookup"><span data-stu-id="8e564-131">Usually, you use this list to iterate on the set of cameras.</span></span>

<span data-ttu-id="8e564-132">從 **AppMain：： Update** ：</span><span class="sxs-lookup"><span data-stu-id="8e564-132">From **AppMain::Update** :</span></span>

```cpp
m_deviceResources->EnsureCameraResources(holographicFrame, prediction);
```

<span data-ttu-id="8e564-133">從 **DeviceResources：： EnsureCameraResources** ：</span><span class="sxs-lookup"><span data-stu-id="8e564-133">From **DeviceResources::EnsureCameraResources** :</span></span>

```cpp
for (HolographicCameraPose const& cameraPose : prediction.CameraPoses())
{
    HolographicCameraRenderingParameters renderingParameters = frame.GetRenderingParameters(cameraPose);
    CameraResources* pCameraResources = cameraResourceMap[cameraPose.HolographicCamera().Id()].get();
    pCameraResources->CreateResourcesForBackBuffer(this, renderingParameters);
}
```

### <a name="get-the-coordinate-system-to-use-as-a-basis-for-rendering"></a><span data-ttu-id="8e564-134">取得座標系統作為轉譯的基礎</span><span class="sxs-lookup"><span data-stu-id="8e564-134">Get the coordinate system to use as a basis for rendering</span></span>

<span data-ttu-id="8e564-135">Windows Mixed Reality 可讓您的應用程式視需要建立各種 [座標系統](coordinate-systems-in-directx.md) ，例如，連接的參考框架和固定的參考框架，以追蹤實體世界中的位置。</span><span class="sxs-lookup"><span data-stu-id="8e564-135">Windows Mixed Reality lets your app create various [coordinate systems](coordinate-systems-in-directx.md) as needed, such as the attached reference frame and the stationary reference frame, that track locations in the physical world.</span></span> <span data-ttu-id="8e564-136">然後，您的應用程式可以使用這些座標系統，來指出要在哪裡轉譯每個畫面格。</span><span class="sxs-lookup"><span data-stu-id="8e564-136">Your app can then use these coordinate systems to reason about where to render holograms each frame.</span></span> <span data-ttu-id="8e564-137">從 API 要求座標時，您一律會傳入要在其中表示這些座標的 <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a> 。</span><span class="sxs-lookup"><span data-stu-id="8e564-137">When requesting coordinates from an API, you will always pass in the <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a> within which you want those coordinates to be expressed.</span></span>

<span data-ttu-id="8e564-138">從 **AppMain：： Update** ：</span><span class="sxs-lookup"><span data-stu-id="8e564-138">From **AppMain::Update** :</span></span>

```cpp
pose = SpatialPointerPose::TryGetAtTimestamp(
    m_stationaryReferenceFrame.CoordinateSystem(), prediction.Timestamp());
```

<span data-ttu-id="8e564-139">然後，您可以在轉譯場景中的內容時，使用這些座標系統來產生身歷聲視圖矩陣。</span><span class="sxs-lookup"><span data-stu-id="8e564-139">These coordinate systems can then be used to generate stereo view matrices when rendering the content in your scene.</span></span>

<span data-ttu-id="8e564-140">從 **CameraResources：： UpdateViewProjectionBuffer** ：</span><span class="sxs-lookup"><span data-stu-id="8e564-140">From **CameraResources::UpdateViewProjectionBuffer** :</span></span>

```cpp
// Get a container object with the view and projection matrices for the given
// pose in the given coordinate system.
auto viewTransformContainer = cameraPose.TryGetViewTransform(coordinateSystem);
```

### <a name="process-gaze-and-gesture-input"></a><span data-ttu-id="8e564-141">處理注視和手勢輸入</span><span class="sxs-lookup"><span data-stu-id="8e564-141">Process gaze and gesture input</span></span>

<span data-ttu-id="8e564-142">[注視](gaze-in-directx.md) 和 [手](hands-and-motion-controllers-in-directx.md) 輸入不是以時間為基礎，因此不需要在 **StepTimer** 函式中更新。</span><span class="sxs-lookup"><span data-stu-id="8e564-142">[Gaze](gaze-in-directx.md) and [hand](hands-and-motion-controllers-in-directx.md) input are not time-based and thus do not have to update in the **StepTimer** function.</span></span> <span data-ttu-id="8e564-143">不過，此輸入是應用程式需要查看每個畫面格的內容。</span><span class="sxs-lookup"><span data-stu-id="8e564-143">However this input is something that the app needs to look at each frame.</span></span>

### <a name="process-time-based-updates"></a><span data-ttu-id="8e564-144">處理以時間為基礎的更新</span><span class="sxs-lookup"><span data-stu-id="8e564-144">Process time-based updates</span></span>

<span data-ttu-id="8e564-145">任何即時轉譯應用程式都需要某種方式來處理以時間為基礎的更新;我們在 Windows 全像應用程式範本中，透過 **StepTimer** 的執行方式提供了一種方法。</span><span class="sxs-lookup"><span data-stu-id="8e564-145">Any real-time rendering app will need some way to process time-based updates; we provide a way to do this in the Windows Holographic app template via a **StepTimer** implementation.</span></span> <span data-ttu-id="8e564-146">這類似于 DirectX 11 UWP 應用程式範本中提供的 StepTimer，因此如果您已經看過該範本，您應該會在熟悉的基礎上。</span><span class="sxs-lookup"><span data-stu-id="8e564-146">This is similar to the StepTimer provided in the DirectX 11 UWP app template, so if you already have looked at that template you should be on familiar ground.</span></span> <span data-ttu-id="8e564-147">此 StepTimer 範例協助程式類別可以提供固定的時間步驟更新以及可變的時間步驟更新，而預設模式則是可變時間步驟。</span><span class="sxs-lookup"><span data-stu-id="8e564-147">This StepTimer sample helper class is able to provide fixed time-step updates, as well as variable time-step updates, and the default mode is variable time steps.</span></span>

<span data-ttu-id="8e564-148">在全像攝影轉譯的案例中，我們特別選擇不要將太多放入計時器函數中。</span><span class="sxs-lookup"><span data-stu-id="8e564-148">In the case of holographic rendering, we've specifically chosen not to put too much into the timer function.</span></span> <span data-ttu-id="8e564-149">這是因為您可以將它設定為固定的時間步驟，在這種情況下，每個畫面可能會被呼叫一次以上，或根本不會針對某些框架呼叫一次，而且每個畫面格的全像資料更新應該會進行一次。</span><span class="sxs-lookup"><span data-stu-id="8e564-149">This is because you can configure it to be a fixed time step, in which case it might get called more than once per frame – or not at all, for some frames – and our holographic data updates should happen once per frame.</span></span>


<span data-ttu-id="8e564-150">從 **AppMain：： Update** ：</span><span class="sxs-lookup"><span data-stu-id="8e564-150">From **AppMain::Update** :</span></span>

```cpp
m_timer.Tick([this]()
{
    m_spinningCubeRenderer->Update(m_timer);
});
```

### <a name="position-and-rotate-holograms-in-your-coordinate-system"></a><span data-ttu-id="8e564-151">在座標系統中定位和旋轉全像投影</span><span class="sxs-lookup"><span data-stu-id="8e564-151">Position and rotate holograms in your coordinate system</span></span>

<span data-ttu-id="8e564-152">如果您是在單一座標系統中操作，當範本使用 **SpatialStationaryReferenceFrame** 時，此程式不會與您在3d 圖形中使用的方式不同。</span><span class="sxs-lookup"><span data-stu-id="8e564-152">If you are operating in a single coordinate system, as the template does with the **SpatialStationaryReferenceFrame** , this process isn't different from what you're otherwise used to in 3D graphics.</span></span> <span data-ttu-id="8e564-153">在這裡，我們會旋轉 cube，並將模型矩陣設定為相對於固定座標系統中的位置。</span><span class="sxs-lookup"><span data-stu-id="8e564-153">Here, we rotate the cube and set the model matrix relative to the position in the stationary coordinate system.</span></span>

<span data-ttu-id="8e564-154">從 **SpinningCubeRenderer：： Update** ：</span><span class="sxs-lookup"><span data-stu-id="8e564-154">From **SpinningCubeRenderer::Update** :</span></span>

```cpp
// Rotate the cube.
// Convert degrees to radians, then convert seconds to rotation angle.
const float    radiansPerSecond = XMConvertToRadians(m_degreesPerSecond);
const double   totalRotation = timer.GetTotalSeconds() * radiansPerSecond;
const float    radians = static_cast<float>(fmod(totalRotation, XM_2PI));
const XMMATRIX modelRotation = XMMatrixRotationY(-radians);

// Position the cube.
const XMMATRIX modelTranslation = XMMatrixTranslationFromVector(XMLoadFloat3(&m_position));

// Multiply to get the transform matrix.
// Note that this transform does not enforce a particular coordinate system. The calling
// class is responsible for rendering this content in a consistent manner.
const XMMATRIX modelTransform = XMMatrixMultiply(modelRotation, modelTranslation);

// The view and projection matrices are provided by the system; they are associated
// with holographic cameras, and updated on a per-camera basis.
// Here, we provide the model transform for the sample hologram. The model transform
// matrix is transposed to prepare it for the shader.
XMStoreFloat4x4(&m_modelConstantBufferData.model, XMMatrixTranspose(modelTransform));
```

<span data-ttu-id="8e564-155">**關於 advanced 案例的注意事項：** 旋轉 cube 是一個非常簡單的範例，說明如何在單一參考框架內放置全像影像。</span><span class="sxs-lookup"><span data-stu-id="8e564-155">**Note about advanced scenarios:** The spinning cube is a very simple example of how to position a hologram within a single reference frame.</span></span> <span data-ttu-id="8e564-156">您也可以同時在相同的呈現框架中 [使用多個 SpatialCoordinateSystems](coordinate-systems-in-directx.md) 。</span><span class="sxs-lookup"><span data-stu-id="8e564-156">It's also possible to [use multiple SpatialCoordinateSystems](coordinate-systems-in-directx.md) in the same rendered frame, at the same time.</span></span>

### <a name="update-constant-buffer-data"></a><span data-ttu-id="8e564-157">更新常數緩衝區資料</span><span class="sxs-lookup"><span data-stu-id="8e564-157">Update constant buffer data</span></span>

<span data-ttu-id="8e564-158">內容的模型轉換會如往常般更新。</span><span class="sxs-lookup"><span data-stu-id="8e564-158">Model transforms for content are updated as usual.</span></span> <span data-ttu-id="8e564-159">現在，您將會針對要轉譯的座標系統，計算出有效的轉換。</span><span class="sxs-lookup"><span data-stu-id="8e564-159">By now, you will have computed valid transforms for the coordinate system you'll be rendering in.</span></span>

<span data-ttu-id="8e564-160">從 **SpinningCubeRenderer：： Update** ：</span><span class="sxs-lookup"><span data-stu-id="8e564-160">From **SpinningCubeRenderer::Update** :</span></span>

```cpp
// Update the model transform buffer for the hologram.
context->UpdateSubresource(
    m_modelConstantBuffer.Get(),
    0,
    nullptr,
    &m_modelConstantBufferData,
    0,
    0
);
```

<span data-ttu-id="8e564-161">什麼是視圖和投射轉換？</span><span class="sxs-lookup"><span data-stu-id="8e564-161">What about view and projection transforms?</span></span> <span data-ttu-id="8e564-162">為了獲得最佳結果，我們想要等到我們準備好進行繪製呼叫之後，才取得這些。</span><span class="sxs-lookup"><span data-stu-id="8e564-162">For best results, we want to wait until we're almost ready for our draw calls before we get these.</span></span>

## <a name="render-the-current-frame"></a><span data-ttu-id="8e564-163">轉譯目前的框架</span><span class="sxs-lookup"><span data-stu-id="8e564-163">Render the current frame</span></span>

<span data-ttu-id="8e564-164">轉譯 Windows Mixed Reality 與在 2D mono 顯示器上轉譯的方式不同，但有一些需要注意的差異：</span><span class="sxs-lookup"><span data-stu-id="8e564-164">Rendering on Windows Mixed Reality is not much different from rendering on a 2D mono display, but there are some differences you need to be aware of:</span></span>
* <span data-ttu-id="8e564-165">全像攝影框架的預測很重要。</span><span class="sxs-lookup"><span data-stu-id="8e564-165">Holographic frame predictions are important.</span></span> <span data-ttu-id="8e564-166">預測越接近您的畫面格呈現的樣子，您的全像全像投影就越好。</span><span class="sxs-lookup"><span data-stu-id="8e564-166">The closer the prediction is to when your frame is presented, the better your holograms will look.</span></span>
* <span data-ttu-id="8e564-167">Windows Mixed Reality 控制攝影機的視圖。</span><span class="sxs-lookup"><span data-stu-id="8e564-167">Windows Mixed Reality controls the camera views.</span></span> <span data-ttu-id="8e564-168">您需要轉譯為每個畫面格，因為全像照片框架將在稍後呈現。</span><span class="sxs-lookup"><span data-stu-id="8e564-168">You need to render to each one because the holographic frame will be presenting them for you later.</span></span>
* <span data-ttu-id="8e564-169">建議您使用對轉譯目標陣列使用實例繪製來完成身歷聲轉譯。</span><span class="sxs-lookup"><span data-stu-id="8e564-169">Stereo rendering is recommended to be accomplished using instanced drawing to a render target array.</span></span> <span data-ttu-id="8e564-170">全像「全像」應用程式範本會使用具現化繪圖的建議方法來繪製到轉譯目標陣列，這會使用呈現目標視圖 **Texture2DArray** 。</span><span class="sxs-lookup"><span data-stu-id="8e564-170">The holographic app template uses the recommended approach of instanced drawing to a render target array, which uses a render target view onto a **Texture2DArray** .</span></span>
* <span data-ttu-id="8e564-171">如果您想要在不使用身歷聲實例的情況下轉譯，則必須建立兩個非陣列 RenderTargetViews (每個) ，每一個都參考從系統提供給應用程式之 **Texture2DArray** 中的兩個配量之一。</span><span class="sxs-lookup"><span data-stu-id="8e564-171">If you want to render without using stereo instancing, you will need to create two non-array RenderTargetViews (one for each eye) that each reference one of the two slices in the **Texture2DArray** provided to the app from the system.</span></span> <span data-ttu-id="8e564-172">這是不建議的作法，因為它的速度通常會比使用實例慢很多。</span><span class="sxs-lookup"><span data-stu-id="8e564-172">This is not recommended, as it is typically significantly slower than using instancing.</span></span>

### <a name="get-an-updated-holographicframe-prediction"></a><span data-ttu-id="8e564-173">取得更新的 HolographicFrame 預測</span><span class="sxs-lookup"><span data-stu-id="8e564-173">Get an updated HolographicFrame prediction</span></span>

<span data-ttu-id="8e564-174">更新框架預測可增強影像穩定的效能，並可讓您更精確地放置全像投影，因為預測和使用者可以看到畫面格的時間較短。</span><span class="sxs-lookup"><span data-stu-id="8e564-174">Updating the frame prediction enhances the effectiveness of image stabilization and allows for more accurate positioning of holograms due to the shorter time between the prediction and when the frame is visible to the user.</span></span> <span data-ttu-id="8e564-175">在呈現之前，最好先更新您的框架預測。</span><span class="sxs-lookup"><span data-stu-id="8e564-175">Ideally update your frame prediction just before rendering.</span></span>

```cpp
holographicFrame.UpdateCurrentPrediction();
HolographicFramePrediction prediction = holographicFrame.CurrentPrediction();
```

### <a name="render-to-each-camera"></a><span data-ttu-id="8e564-176">轉譯為每個相機</span><span class="sxs-lookup"><span data-stu-id="8e564-176">Render to each camera</span></span>

<span data-ttu-id="8e564-177">在一組相機上的迴圈會在預測中產生，並轉譯為此集合中的每個相機。</span><span class="sxs-lookup"><span data-stu-id="8e564-177">Loop on the set of camera poses in the prediction, and render to each camera in this set.</span></span>

<span data-ttu-id="8e564-178">**設定您的轉譯階段**</span><span class="sxs-lookup"><span data-stu-id="8e564-178">**Set up your rendering pass**</span></span>

<span data-ttu-id="8e564-179">Windows Mixed Reality 使用 stereoscopic 轉譯來加強深度的幻影和轉譯 stereoscopically，讓左邊和右邊的顯示都處於作用中狀態。</span><span class="sxs-lookup"><span data-stu-id="8e564-179">Windows Mixed Reality uses stereoscopic rendering to enhance the illusion of depth and to render stereoscopically, so both the left and the right display are active.</span></span> <span data-ttu-id="8e564-180">使用 stereoscopic 轉譯時，會有兩個顯示器之間的位移，而大腦可將其視為實際的深度。</span><span class="sxs-lookup"><span data-stu-id="8e564-180">With stereoscopic rendering there is an offset between the two displays, which the brain can reconcile as actual depth.</span></span> <span data-ttu-id="8e564-181">本節說明如何使用 Windows 全像應用程式範本中的程式碼，使用實例進行 stereoscopic 轉譯。</span><span class="sxs-lookup"><span data-stu-id="8e564-181">This section covers stereoscopic rendering using instancing, using code from the Windows Holographic app template.</span></span>

<span data-ttu-id="8e564-182">每個攝影機都有自己的轉譯目標 (回緩衝區) ，以及將矩陣和投影矩陣放入全像空間中。</span><span class="sxs-lookup"><span data-stu-id="8e564-182">Each camera has its own render target (back buffer), and view and projection matrices, into the holographic space.</span></span> <span data-ttu-id="8e564-183">您的應用程式將需要建立任何其他以相機為基礎的資源，例如深度緩衝區（以每個相機為基礎）。</span><span class="sxs-lookup"><span data-stu-id="8e564-183">Your app will need to create any other camera-based resources - such as the depth buffer - on a per-camera basis.</span></span> <span data-ttu-id="8e564-184">在 Windows 全像應用程式範本中，我們提供一個協助程式類別，將這些資源組合在 DX：： CameraResources 中。</span><span class="sxs-lookup"><span data-stu-id="8e564-184">In the Windows Holographic app template, we provide a helper class to bundle these resources together in DX::CameraResources.</span></span> <span data-ttu-id="8e564-185">從設定轉譯目標視圖開始：</span><span class="sxs-lookup"><span data-stu-id="8e564-185">Start by setting up the render target views:</span></span>

<span data-ttu-id="8e564-186">從 **AppMain：： Render** ：</span><span class="sxs-lookup"><span data-stu-id="8e564-186">From **AppMain::Render** :</span></span>

```cpp
// This represents the device-based resources for a HolographicCamera.
DX::CameraResources* pCameraResources = cameraResourceMap[cameraPose.HolographicCamera().Id()].get();

// Get the device context.
const auto context = m_deviceResources->GetD3DDeviceContext();
const auto depthStencilView = pCameraResources->GetDepthStencilView();

// Set render targets to the current holographic camera.
ID3D11RenderTargetView *const targets[1] =
    { pCameraResources->GetBackBufferRenderTargetView() };
context->OMSetRenderTargets(1, targets, depthStencilView);

// Clear the back buffer and depth stencil view.
if (m_canGetHolographicDisplayForCamera &&
    cameraPose.HolographicCamera().Display().IsOpaque())
{
    context->ClearRenderTargetView(targets[0], DirectX::Colors::CornflowerBlue);
}
else
{
    context->ClearRenderTargetView(targets[0], DirectX::Colors::Transparent);
}
context->ClearDepthStencilView(
    depthStencilView, D3D11_CLEAR_DEPTH | D3D11_CLEAR_STENCIL, 1.0f, 0);
```

<span data-ttu-id="8e564-187">**使用預測來取得相機的視圖和投射矩陣**</span><span class="sxs-lookup"><span data-stu-id="8e564-187">**Use the prediction to get the view and projection matrices for the camera**</span></span>

<span data-ttu-id="8e564-188">每個全像攝影相機的視圖和投射矩陣都會隨著每個畫面格而改變。</span><span class="sxs-lookup"><span data-stu-id="8e564-188">The view and projection matrices for each holographic camera will change with every frame.</span></span> <span data-ttu-id="8e564-189">重新整理每個全息相機的常數緩衝區中的資料。</span><span class="sxs-lookup"><span data-stu-id="8e564-189">Refresh the data in the constant buffer for each holographic camera.</span></span> <span data-ttu-id="8e564-190">在您更新預測之後，以及對該攝影機進行任何繪製呼叫之前，請執行此動作。</span><span class="sxs-lookup"><span data-stu-id="8e564-190">Do this after you updated the prediction, and before you make any draw calls for that camera.</span></span>

<span data-ttu-id="8e564-191">從 **AppMain：： Render** ：</span><span class="sxs-lookup"><span data-stu-id="8e564-191">From **AppMain::Render** :</span></span>

```cpp
// The view and projection matrices for each holographic camera will change
// every frame. This function refreshes the data in the constant buffer for
// the holographic camera indicated by cameraPose.
if (m_stationaryReferenceFrame)
{
    pCameraResources->UpdateViewProjectionBuffer(
        m_deviceResources, cameraPose, m_stationaryReferenceFrame.CoordinateSystem());
}

// Attach the view/projection constant buffer for this camera to the graphics pipeline.
bool cameraActive = pCameraResources->AttachViewProjectionBuffer(m_deviceResources);
```

<span data-ttu-id="8e564-192">在這裡，我們會示範如何從相機姿勢取得矩陣。</span><span class="sxs-lookup"><span data-stu-id="8e564-192">Here, we show how the matrices are acquired from the camera pose.</span></span> <span data-ttu-id="8e564-193">在這個過程中，我們也會取得相機的目前的視口。</span><span class="sxs-lookup"><span data-stu-id="8e564-193">During this process we also obtain the current viewport for the camera.</span></span> <span data-ttu-id="8e564-194">請注意我們如何提供座標系統：這是我們用來瞭解注視的相同座標系統，也是我們用來定位旋轉 cube 的相同座標系統。</span><span class="sxs-lookup"><span data-stu-id="8e564-194">Note how we provide a coordinate system: this is the same coordinate system we used to understand gaze, and it's the same one we used to position the spinning cube.</span></span>


<span data-ttu-id="8e564-195">從 **CameraResources：： UpdateViewProjectionBuffer** ：</span><span class="sxs-lookup"><span data-stu-id="8e564-195">From **CameraResources::UpdateViewProjectionBuffer** :</span></span>

```cpp
// The system changes the viewport on a per-frame basis for system optimizations.
auto viewport = cameraPose.Viewport();
m_d3dViewport = CD3D11_VIEWPORT(
    viewport.X,
    viewport.Y,
    viewport.Width,
    viewport.Height
);

// The projection transform for each frame is provided by the HolographicCameraPose.
HolographicStereoTransform cameraProjectionTransform = cameraPose.ProjectionTransform();

// Get a container object with the view and projection matrices for the given
// pose in the given coordinate system.
auto viewTransformContainer = cameraPose.TryGetViewTransform(coordinateSystem);

// If TryGetViewTransform returns a null pointer, that means the pose and coordinate
// system cannot be understood relative to one another; content cannot be rendered
// in this coordinate system for the duration of the current frame.
// This usually means that positional tracking is not active for the current frame, in
// which case it is possible to use a SpatialLocatorAttachedFrameOfReference to render
// content that is not world-locked instead.
DX::ViewProjectionConstantBuffer viewProjectionConstantBufferData;
bool viewTransformAcquired = viewTransformContainer != nullptr;
if (viewTransformAcquired)
{
    // Otherwise, the set of view transforms can be retrieved.
    HolographicStereoTransform viewCoordinateSystemTransform = viewTransformContainer.Value();

    // Update the view matrices. Holographic cameras (such as Microsoft HoloLens) are
    // constantly moving relative to the world. The view matrices need to be updated
    // every frame.
    XMStoreFloat4x4(
        &viewProjectionConstantBufferData.viewProjection[0],
        XMMatrixTranspose(XMLoadFloat4x4(&viewCoordinateSystemTransform.Left) *
            XMLoadFloat4x4(&cameraProjectionTransform.Left))
    );
    XMStoreFloat4x4(
        &viewProjectionConstantBufferData.viewProjection[1],
        XMMatrixTranspose(XMLoadFloat4x4(&viewCoordinateSystemTransform.Right) *
            XMLoadFloat4x4(&cameraProjectionTransform.Right))
    );
}
```

<span data-ttu-id="8e564-196">應設定每個畫面格的區。</span><span class="sxs-lookup"><span data-stu-id="8e564-196">The viewport should be set each frame.</span></span> <span data-ttu-id="8e564-197">您的頂點著色器 (至少) 通常需要存取 view/投射資料。</span><span class="sxs-lookup"><span data-stu-id="8e564-197">Your vertex shader (at least) will generally need access to the view/projection data.</span></span>


<span data-ttu-id="8e564-198">從 **CameraResources：： AttachViewProjectionBuffer** ：</span><span class="sxs-lookup"><span data-stu-id="8e564-198">From **CameraResources::AttachViewProjectionBuffer** :</span></span>

```cpp
// Set the viewport for this camera.
context->RSSetViewports(1, &m_d3dViewport);

// Send the constant buffer to the vertex shader.
context->VSSetConstantBuffers(
    1,
    1,
    m_viewProjectionConstantBuffer.GetAddressOf()
);
```

<span data-ttu-id="8e564-199">轉譯 **成相機背面緩衝區，並認可深度緩衝區** ：</span><span class="sxs-lookup"><span data-stu-id="8e564-199">**Render to the camera back buffer and commit the depth buffer** :</span></span>

<span data-ttu-id="8e564-200">最好先檢查 **TryGetViewTransform** 是否成功，再嘗試使用視圖/投射資料，因為如果無法定位座標系統 (例如，追蹤已中斷，) 您的應用程式在該框架中無法呈現。</span><span class="sxs-lookup"><span data-stu-id="8e564-200">It's a good idea to check that **TryGetViewTransform** succeeded before trying to use the view/projection data, because if the coordinate system is not locatable (e.g., tracking was interrupted) your app cannot render with it for that frame.</span></span> <span data-ttu-id="8e564-201">如果 **CameraResources** 類別指出成功更新，則範本只 **會呼叫旋轉** cube 上的轉譯。</span><span class="sxs-lookup"><span data-stu-id="8e564-201">The template only calls **Render** on the spinning cube if the **CameraResources** class indicates a successful update.</span></span>

<span data-ttu-id="8e564-202">為了讓開發人員或使用者將它們放在世界各地，Windows Mixed Reality 包含影像 [穩定](../platform-capabilities-and-apis/hologram-stability.md)的功能。</span><span class="sxs-lookup"><span data-stu-id="8e564-202">To keep holograms where a developer or a user puts them in the world, Windows Mixed Reality includes features for [image stabilization](../platform-capabilities-and-apis/hologram-stability.md).</span></span> <span data-ttu-id="8e564-203">影像穩定有助於隱藏轉譯管線固有的延遲，以確保最適合使用者的全像攝影體驗;您可以指定焦點點來進一步增強影像穩定，或可以提供深度緩衝區來即時計算優化的影像穩定。</span><span class="sxs-lookup"><span data-stu-id="8e564-203">Image stabilization helps hide the latency inherent in a rendering pipeline to ensure the best holographic experiences for users; a focus point may be specified to enhance image stabilization even further, or a depth buffer may be provided to compute optimized image stabilization in real time.</span></span>

<span data-ttu-id="8e564-204">為了獲得最佳結果，您的應用程式應該使用 <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer" target="_blank">CommitDirect3D11DepthBuffer</a> API 提供深度緩衝區。</span><span class="sxs-lookup"><span data-stu-id="8e564-204">For best results, your app should provide a depth buffer using the <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer" target="_blank">CommitDirect3D11DepthBuffer</a> API.</span></span> <span data-ttu-id="8e564-205">Windows Mixed Reality 接著可以使用深度緩衝區的幾何資訊，即時優化影像穩定。</span><span class="sxs-lookup"><span data-stu-id="8e564-205">Windows Mixed Reality can then use geometry information from the depth buffer to optimize image stabilization in real time.</span></span> <span data-ttu-id="8e564-206">Windows 全像影像應用程式範本預設會認可應用程式的深度緩衝區，以協助優化全像全像全像是</span><span class="sxs-lookup"><span data-stu-id="8e564-206">The Windows Holographic app template commits the app's depth buffer by default, helping optimize hologram stability.</span></span>

<span data-ttu-id="8e564-207">從 **AppMain：： Render** ：</span><span class="sxs-lookup"><span data-stu-id="8e564-207">From **AppMain::Render** :</span></span>

```cpp
// Only render world-locked content when positional tracking is active.
if (cameraActive)
{
    // Draw the sample hologram.
    m_spinningCubeRenderer->Render();
    if (m_canCommitDirect3D11DepthBuffer)
    {
        // On versions of the platform that support the CommitDirect3D11DepthBuffer API, we can 
        // provide the depth buffer to the system, and it will use depth information to stabilize 
        // the image at a per-pixel level.
        HolographicCameraRenderingParameters renderingParameters =
            holographicFrame.GetRenderingParameters(cameraPose);
        
        IDirect3DSurface interopSurface =
            DX::CreateDepthTextureInteropObject(pCameraResources->GetDepthStencilTexture2D());

        // Calling CommitDirect3D11DepthBuffer causes the system to queue Direct3D commands to 
        // read the depth buffer. It will then use that information to stabilize the image as
        // the HolographicFrame is presented.
        renderingParameters.CommitDirect3D11DepthBuffer(interopSurface);
    }
}
```

>[!NOTE]
><span data-ttu-id="8e564-208">Windows 將會在 GPU 上處理您的深度材質，因此必須可以使用您的深度緩衝區做為著色器資源。</span><span class="sxs-lookup"><span data-stu-id="8e564-208">Windows will process your depth texture on the GPU, so it must be possible to use your depth buffer as a shader resource.</span></span> <span data-ttu-id="8e564-209">您所建立的 ID3D11Texture2D 應該採用無類型的格式，而且應該系結為著色器資源檢視。</span><span class="sxs-lookup"><span data-stu-id="8e564-209">The ID3D11Texture2D that you create should be in a typeless format and it should be bound as a shader resource view.</span></span> <span data-ttu-id="8e564-210">以下範例說明如何建立可針對影像穩定認可的深度材質。</span><span class="sxs-lookup"><span data-stu-id="8e564-210">Here is an example of how to create a depth texture that can be committed for image stabilization.</span></span>

<span data-ttu-id="8e564-211">CommitDirect3D11DepthBuffer 的 **深度緩衝區資源建立** 程式碼：</span><span class="sxs-lookup"><span data-stu-id="8e564-211">Code for **Depth buffer resource creation for CommitDirect3D11DepthBuffer** :</span></span>

```cpp
// Create a depth stencil view for use with 3D rendering if needed.
CD3D11_TEXTURE2D_DESC depthStencilDesc(
    DXGI_FORMAT_R16_TYPELESS,
    static_cast<UINT>(m_d3dRenderTargetSize.Width),
    static_cast<UINT>(m_d3dRenderTargetSize.Height),
    m_isStereo ? 2 : 1, // Create two textures when rendering in stereo.
    1, // Use a single mipmap level.
    D3D11_BIND_DEPTH_STENCIL | D3D11_BIND_SHADER_RESOURCE
);

winrt::check_hresult(
    device->CreateTexture2D(
        &depthStencilDesc,
        nullptr,
        &m_d3dDepthStencil
    ));

CD3D11_DEPTH_STENCIL_VIEW_DESC depthStencilViewDesc(
    m_isStereo ? D3D11_DSV_DIMENSION_TEXTURE2DARRAY : D3D11_DSV_DIMENSION_TEXTURE2D,
    DXGI_FORMAT_D16_UNORM
);
winrt::check_hresult(
    device->CreateDepthStencilView(
        m_d3dDepthStencil.Get(),
        &depthStencilViewDesc,
        &m_d3dDepthStencilView
    ));
```

<span data-ttu-id="8e564-212">**繪製全息內容**</span><span class="sxs-lookup"><span data-stu-id="8e564-212">**Draw holographic content**</span></span>

<span data-ttu-id="8e564-213">Windows 全像攝影應用程式範本會使用將實例幾何的建議技術轉譯為大小2的 Texture2DArray，以身歷聲呈現內容。</span><span class="sxs-lookup"><span data-stu-id="8e564-213">The Windows Holographic app template renders content in stereo by using the recommended technique of drawing instanced geometry to a Texture2DArray of size 2.</span></span> <span data-ttu-id="8e564-214">讓我們來看看這部分的實例，以及它在 Windows Mixed Reality 的運作方式。</span><span class="sxs-lookup"><span data-stu-id="8e564-214">Let's look at the instancing part of this, and how it works on Windows Mixed Reality.</span></span>

<span data-ttu-id="8e564-215">從 **SpinningCubeRenderer：： Render** ：</span><span class="sxs-lookup"><span data-stu-id="8e564-215">From **SpinningCubeRenderer::Render** :</span></span>

```cpp
// Draw the objects.
context->DrawIndexedInstanced(
    m_indexCount,   // Index count per instance.
    2,              // Instance count.
    0,              // Start index location.
    0,              // Base vertex location.
    0               // Start instance location.
);
```

<span data-ttu-id="8e564-216">每個實例都會從常數緩衝區存取不同的視圖/投射矩陣。</span><span class="sxs-lookup"><span data-stu-id="8e564-216">Each instance accesses a different view/projection matrix from the constant buffer.</span></span> <span data-ttu-id="8e564-217">以下是常數緩衝區結構，也就是2個矩陣的陣列。</span><span class="sxs-lookup"><span data-stu-id="8e564-217">Here's the constant buffer structure, which is just an array of 2 matrices.</span></span>

<span data-ttu-id="8e564-218">From **VertexShaderShared. hlsl** ，包含 **VPRTVertexShader. hlsl** ：</span><span class="sxs-lookup"><span data-stu-id="8e564-218">From **VertexShaderShared.hlsl** , included by **VPRTVertexShader.hlsl** :</span></span>

```HLSL
// A constant buffer that stores each set of view and projection matrices in column-major format.
cbuffer ViewProjectionConstantBuffer : register(b1)
{
    float4x4 viewProjection[2];
};
```

<span data-ttu-id="8e564-219">您必須為每個圖元設定轉譯目標陣列索引。</span><span class="sxs-lookup"><span data-stu-id="8e564-219">The render target array index must be set for each pixel.</span></span> <span data-ttu-id="8e564-220">在下列程式碼片段中，viewId 會對應至 **SV_RenderTargetArrayIndex** 語義。</span><span class="sxs-lookup"><span data-stu-id="8e564-220">In the following snippet, output.viewId is mapped to the **SV_RenderTargetArrayIndex** semantic.</span></span> <span data-ttu-id="8e564-221">請注意，這需要選擇性 Direct3D 11.3 功能的支援，以允許從任何著色器階段設定轉譯目標陣列索引語義。</span><span class="sxs-lookup"><span data-stu-id="8e564-221">Note that this requires support for an optional Direct3D 11.3 feature, which allows the render target array index semantic to be set from any shader stage.</span></span>

<span data-ttu-id="8e564-222">從 **VPRTVertexShader. hlsl** ：</span><span class="sxs-lookup"><span data-stu-id="8e564-222">From **VPRTVertexShader.hlsl** :</span></span>

```HLSL    
// Per-vertex data passed to the geometry shader.
struct VertexShaderOutput
{
    min16float4 pos     : SV_POSITION;
    min16float3 color   : COLOR0;

    // The render target array index is set here in the vertex shader.
    uint        viewId  : SV_RenderTargetArrayIndex;
};
```

<span data-ttu-id="8e564-223">From **VertexShaderShared. hlsl** ，包含 **VPRTVertexShader. hlsl** ：</span><span class="sxs-lookup"><span data-stu-id="8e564-223">From **VertexShaderShared.hlsl** , included by **VPRTVertexShader.hlsl** :</span></span>

```HLSL
// Per-vertex data used as input to the vertex shader.
struct VertexShaderInput
{
    min16float3 pos     : POSITION;
    min16float3 color   : COLOR0;
    uint        instId  : SV_InstanceID;
};

// Simple shader to do vertex processing on the GPU.
VertexShaderOutput main(VertexShaderInput input)
{
    VertexShaderOutput output;
    float4 pos = float4(input.pos, 1.0f);

    // Note which view this vertex has been sent to. Used for matrix lookup.
    // Taking the modulo of the instance ID allows geometry instancing to be used
    // along with stereo instanced drawing; in that case, two copies of each 
    // instance would be drawn, one for left and one for right.
    int idx = input.instId % 2;

    // Transform the vertex position into world space.
    pos = mul(pos, model);

    // Correct for perspective and project the vertex position onto the screen.
    pos = mul(pos, viewProjection[idx]);
    output.pos = (min16float4)pos;

    // Pass the color through without modification.
    output.color = input.color;

    // Set the render target array index.
    output.viewId = idx;

    return output;
}
```

<span data-ttu-id="8e564-224">如果您想要使用現有的實例繪圖技術搭配此方法繪製到身歷聲轉譯目標陣列，您只需要繪製您平常所擁有之實例數目的兩倍。</span><span class="sxs-lookup"><span data-stu-id="8e564-224">If you want to use your existing instanced drawing techniques with this method of drawing to a stereo render target array, all you have to do is draw twice the number of instances you normally have.</span></span> <span data-ttu-id="8e564-225">在著色器中，將 **instId** 除以2以取得原始實例識別碼，此識別碼可編制索引為 (例如) 每個物件資料的緩衝區： `int actualIdx = input.instId / 2;`</span><span class="sxs-lookup"><span data-stu-id="8e564-225">In the shader, divide **input.instId** by 2 to get the original instance ID, which can be indexed into (for example) a buffer of per-object data: `int actualIdx = input.instId / 2;`</span></span>

### <a name="important-note-about-rendering-stereo-content-on-hololens"></a><span data-ttu-id="8e564-226">在 HoloLens 上轉譯身歷聲內容的重要注意事項</span><span class="sxs-lookup"><span data-stu-id="8e564-226">Important note about rendering stereo content on HoloLens</span></span>

<span data-ttu-id="8e564-227">Windows Mixed Reality 支援從任何著色器階段設定轉譯目標陣列索引的能力;一般來說，這是一項只能在幾何著色器階段完成的工作，因為它是針對 Direct3D 11 定義了語義的方式。</span><span class="sxs-lookup"><span data-stu-id="8e564-227">Windows Mixed Reality supports the ability to set the render target array index from any shader stage; normally, this is a task that could only be done in the geometry shader stage due to the way the semantic is defined for Direct3D 11.</span></span> <span data-ttu-id="8e564-228">在這裡，我們會示範如何設定只設定頂點和圖元著色器階段的轉譯管線的完整範例。</span><span class="sxs-lookup"><span data-stu-id="8e564-228">Here, we show a complete example of how to set up a rendering pipeline with just the vertex and pixel shader stages set.</span></span> <span data-ttu-id="8e564-229">著色器程式碼如上所述。</span><span class="sxs-lookup"><span data-stu-id="8e564-229">The shader code is as described above.</span></span>

<span data-ttu-id="8e564-230">從 **SpinningCubeRenderer：： Render** ：</span><span class="sxs-lookup"><span data-stu-id="8e564-230">From **SpinningCubeRenderer::Render** :</span></span>

```cpp
const auto context = m_deviceResources->GetD3DDeviceContext();

// Each vertex is one instance of the VertexPositionColor struct.
const UINT stride = sizeof(VertexPositionColor);
const UINT offset = 0;
context->IASetVertexBuffers(
    0,
    1,
    m_vertexBuffer.GetAddressOf(),
    &stride,
    &offset
);
context->IASetIndexBuffer(
    m_indexBuffer.Get(),
    DXGI_FORMAT_R16_UINT, // Each index is one 16-bit unsigned integer (short).
    0
);
context->IASetPrimitiveTopology(D3D11_PRIMITIVE_TOPOLOGY_TRIANGLELIST);
context->IASetInputLayout(m_inputLayout.Get());

// Attach the vertex shader.
context->VSSetShader(
    m_vertexShader.Get(),
    nullptr,
    0
);
// Apply the model constant buffer to the vertex shader.
context->VSSetConstantBuffers(
    0,
    1,
    m_modelConstantBuffer.GetAddressOf()
);

// Attach the pixel shader.
context->PSSetShader(
    m_pixelShader.Get(),
    nullptr,
    0
);

// Draw the objects.
context->DrawIndexedInstanced(
    m_indexCount,   // Index count per instance.
    2,              // Instance count.
    0,              // Start index location.
    0,              // Base vertex location.
    0               // Start instance location.
);
```

### <a name="important-note-about-rendering-on-non-hololens-devices"></a><span data-ttu-id="8e564-231">在非 HoloLens 裝置上轉譯的重要注意事項</span><span class="sxs-lookup"><span data-stu-id="8e564-231">Important note about rendering on non-HoloLens devices</span></span>

<span data-ttu-id="8e564-232">若要在頂點著色器中設定轉譯目標陣列索引，圖形驅動程式必須支援 HoloLens 支援的選用 Direct3D 11.3 功能。</span><span class="sxs-lookup"><span data-stu-id="8e564-232">Setting the render target array index in the vertex shader requires that the graphics driver supports an optional Direct3D 11.3 feature, which HoloLens does support.</span></span> <span data-ttu-id="8e564-233">您的應用程式可以安全地執行轉譯所需的技巧，並符合在 Microsoft HoloLens 上執行的所有需求。</span><span class="sxs-lookup"><span data-stu-id="8e564-233">Your app may be able to safely implement just that technique for rendering, and all requirements will be met for running on the Microsoft HoloLens.</span></span>

<span data-ttu-id="8e564-234">您可能也會想要使用 HoloLens 模擬器，這是一個功能強大的開發工具，可供您的全像裝置應用程式使用，並支援 Windows Mixed Reality 連接到 Windows 10 電腦的沉浸式耳機裝置。</span><span class="sxs-lookup"><span data-stu-id="8e564-234">It may be the case that you want to use the HoloLens emulator as well, which can be a powerful development tool for your holographic app - and support Windows Mixed Reality immersive headset devices that are attached to Windows 10 PCs.</span></span> <span data-ttu-id="8e564-235">非 HoloLens 轉譯路徑的支援，因此，所有 Windows Mixed Reality 也都內建在 Windows 全像應用程式範本中。</span><span class="sxs-lookup"><span data-stu-id="8e564-235">Support for the non-HoloLens rendering path - and therefore, for all of Windows Mixed Reality - is also built into the Windows Holographic app template.</span></span> <span data-ttu-id="8e564-236">在範本程式碼中，您會發現程式碼，讓您的全像應用程式可在開發電腦上的 GPU 上執行。</span><span class="sxs-lookup"><span data-stu-id="8e564-236">In the template code, you will find code to enable your holographic app to run on the GPU in your development PC.</span></span> <span data-ttu-id="8e564-237">以下是 **DeviceResources** 類別檢查此選用功能支援的方式。</span><span class="sxs-lookup"><span data-stu-id="8e564-237">Here is how the **DeviceResources** class checks for this optional feature support.</span></span>

<span data-ttu-id="8e564-238">從 **DeviceResources：： CreateDeviceResources** ：</span><span class="sxs-lookup"><span data-stu-id="8e564-238">From **DeviceResources::CreateDeviceResources** :</span></span>

```cpp
// Check for device support for the optional feature that allows setting the render target array index from the vertex shader stage.
D3D11_FEATURE_DATA_D3D11_OPTIONS3 options;
m_d3dDevice->CheckFeatureSupport(D3D11_FEATURE_D3D11_OPTIONS3, &options, sizeof(options));
if (options.VPAndRTArrayIndexFromAnyShaderFeedingRasterizer)
{
    m_supportsVprt = true;
}
```

<span data-ttu-id="8e564-239">若要在沒有此選用功能的情況下支援轉譯，您的應用程式必須使用幾何著色器來設定轉譯目標陣列索引。</span><span class="sxs-lookup"><span data-stu-id="8e564-239">To support rendering without this optional feature, your app must use a geometry shader to set the render target array index.</span></span> <span data-ttu-id="8e564-240">此程式碼片段會在 *after* **VSSetConstantBuffers** 之後 *，以及上* 一節所示的程式碼範例中 **pssetshade** ，以說明如何在 HoloLens 上呈現身歷聲。</span><span class="sxs-lookup"><span data-stu-id="8e564-240">This snippet would be added *after* **VSSetConstantBuffers** , and *before* **PSSetShader** in the code example shown in the previous section that explains how to render stereo on HoloLens.</span></span>

<span data-ttu-id="8e564-241">從 **SpinningCubeRenderer：： Render** ：</span><span class="sxs-lookup"><span data-stu-id="8e564-241">From **SpinningCubeRenderer::Render** :</span></span>

```cpp
if (!m_usingVprtShaders)
{
    // On devices that do not support the D3D11_FEATURE_D3D11_OPTIONS3::
    // VPAndRTArrayIndexFromAnyShaderFeedingRasterizer optional feature,
    // a pass-through geometry shader is used to set the render target 
    // array index.
    context->GSSetShader(
        m_geometryShader.Get(),
        nullptr,
        0
    );
}
```

<span data-ttu-id="8e564-242">**HLSL 注意** ：在此情況下，您也必須載入稍微修改的端點著色器，以使用一律允許的著色器語義（例如 TEXCOORD0），將轉譯目標陣列索引傳遞給幾何著色器。</span><span class="sxs-lookup"><span data-stu-id="8e564-242">**HLSL NOTE** : In this case, you must also load a slightly modified vertex shader that passes the render target array index to the geometry shader using an always-allowed shader semantic, such as TEXCOORD0.</span></span> <span data-ttu-id="8e564-243">幾何著色器不需要執行任何工作;樣板幾何著色器會傳遞所有資料，但呈現目標陣列索引例外，可用來設定 SV_RenderTargetArrayIndex 語義。</span><span class="sxs-lookup"><span data-stu-id="8e564-243">The geometry shader does not have to do any work; the template geometry shader passes through all data, with the exception of the render target array index, which is used to set the SV_RenderTargetArrayIndex semantic.</span></span>

<span data-ttu-id="8e564-244">適用于 GeometryShader 的應用程式範本程式碼 **hlsl** ：</span><span class="sxs-lookup"><span data-stu-id="8e564-244">App template code for **GeometryShader.hlsl** :</span></span>

```HLSL
// Per-vertex data from the vertex shader.
struct GeometryShaderInput
{
    min16float4 pos     : SV_POSITION;
    min16float3 color   : COLOR0;
    uint        instId  : TEXCOORD0;
};

// Per-vertex data passed to the rasterizer.
struct GeometryShaderOutput
{
    min16float4 pos     : SV_POSITION;
    min16float3 color   : COLOR0;
    uint        rtvId   : SV_RenderTargetArrayIndex;
};

// This geometry shader is a pass-through that leaves the geometry unmodified 
// and sets the render target array index.
[maxvertexcount(3)]
void main(triangle GeometryShaderInput input[3], inout TriangleStream<GeometryShaderOutput> outStream)
{
    GeometryShaderOutput output;
    [unroll(3)]
    for (int i = 0; i < 3; ++i)
    {
        output.pos   = input[i].pos;
        output.color = input[i].color;
        output.rtvId = input[i].instId;
        outStream.Append(output);
    }
}
```

## <a name="present"></a><span data-ttu-id="8e564-245">存在</span><span class="sxs-lookup"><span data-stu-id="8e564-245">Present</span></span>

### <a name="enable-the-holographic-frame-to-present-the-swap-chain"></a><span data-ttu-id="8e564-246">讓全像畫面框架呈現交換鏈</span><span class="sxs-lookup"><span data-stu-id="8e564-246">Enable the holographic frame to present the swap chain</span></span>

<span data-ttu-id="8e564-247">使用 Windows Mixed Reality 時，系統會控制交換鏈。</span><span class="sxs-lookup"><span data-stu-id="8e564-247">With Windows Mixed Reality, the system controls the swap chain.</span></span> <span data-ttu-id="8e564-248">然後系統會管理呈現每個全像攝影攝影機的畫面，以確保高品質的使用者體驗。</span><span class="sxs-lookup"><span data-stu-id="8e564-248">The system then manages presenting frames to each holographic camera to ensure a high quality user experience.</span></span> <span data-ttu-id="8e564-249">它也會為每個相機提供一個可更新每個畫面格的區，以優化系統的各個層面，例如影像穩定或混合實境擷取。</span><span class="sxs-lookup"><span data-stu-id="8e564-249">It also provides a viewport update each frame, for each camera, to optimize aspects of the system such as image stabilization or Mixed Reality Capture.</span></span> <span data-ttu-id="8e564-250">因此，使用 DirectX 的全像全息應用程式不會在 DXGI 交換 **鏈上呼叫** 。</span><span class="sxs-lookup"><span data-stu-id="8e564-250">So, a holographic app using DirectX doesn't call **Present** on a DXGI swap chain.</span></span> <span data-ttu-id="8e564-251">相反地，您會使用 <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> 類別，在完成繪製框架之後，顯示該框架的所有 swapchains。</span><span class="sxs-lookup"><span data-stu-id="8e564-251">Instead, you use the <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> class to present all swapchains for a frame once you're done drawing it.</span></span>

<span data-ttu-id="8e564-252">從 **DeviceResources：:P 重發** ：</span><span class="sxs-lookup"><span data-stu-id="8e564-252">From **DeviceResources::Present** :</span></span>

```
HolographicFramePresentResult presentResult = frame.PresentUsingCurrentPrediction();
```

<span data-ttu-id="8e564-253">根據預設，這個 API 會等候框架在傳回之前完成。</span><span class="sxs-lookup"><span data-stu-id="8e564-253">By default, this API waits for the frame to finish before it returns.</span></span> <span data-ttu-id="8e564-254">在新的畫面上開始工作之前，全像攝影應用程式應該等候前一個畫面格完成，因為這樣可減少延遲，並允許來自全像攝影框架預測的較佳結果。</span><span class="sxs-lookup"><span data-stu-id="8e564-254">Holographic apps should wait for the previous frame to finish before starting work on a new frame, because this reduces latency and allows for better results from holographic frame predictions.</span></span> <span data-ttu-id="8e564-255">這不是一項困難的規則，如果您的畫面格需要超過一個螢幕重新整理才能轉譯，則可以將 HolographicFramePresentWaitBehavior 參數傳遞給 <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.presentusingcurrentprediction" target="_blank">PresentUsingCurrentPrediction</a>來停用這項等候。</span><span class="sxs-lookup"><span data-stu-id="8e564-255">This isn't a hard rule, and if you have frames that take longer than one screen refresh to render you can disable this wait by passing the HolographicFramePresentWaitBehavior parameter to <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.presentusingcurrentprediction" target="_blank">PresentUsingCurrentPrediction</a>.</span></span> <span data-ttu-id="8e564-256">在此情況下，您可能會使用非同步轉譯執行緒，以維持 GPU 的連續負載。</span><span class="sxs-lookup"><span data-stu-id="8e564-256">In this case, you would likely use an asynchronous rendering thread in order to maintain a continuous load on the GPU.</span></span> <span data-ttu-id="8e564-257">請注意，HoloLens 裝置的重新整理頻率為60hz，其中一個框架的持續時間大約為16毫秒。</span><span class="sxs-lookup"><span data-stu-id="8e564-257">Note that the refresh rate of the HoloLens device is 60hz, where one frame has a duration of approximately 16 ms.</span></span> <span data-ttu-id="8e564-258">沉浸式耳機裝置的範圍可以從60hz 到 90hz;在 90 hz 重新整理顯示器時，每個畫面的持續時間大約為11毫秒。</span><span class="sxs-lookup"><span data-stu-id="8e564-258">Immersive headset devices can range from 60hz to 90hz; when refreshing the display at 90 hz, each frame will have a duration of approximately 11 ms.</span></span>

### <a name="handle-devicelost-scenarios-in-cooperation-with-the-holographicframe"></a><span data-ttu-id="8e564-259">處理與 HolographicFrame 合作的 DeviceLost 案例</span><span class="sxs-lookup"><span data-stu-id="8e564-259">Handle DeviceLost scenarios in cooperation with the HolographicFrame</span></span>

<span data-ttu-id="8e564-260">DirectX 11 應用程式通常會想要檢查由 DXGI 交換鏈 **目前** 的函式所傳回的 HRESULT，以找出是否有 **DeviceLost** 錯誤。</span><span class="sxs-lookup"><span data-stu-id="8e564-260">DirectX 11 apps would typically want to check the HRESULT returned by the DXGI swap chain's **Present** function to find out if there was a **DeviceLost** error.</span></span> <span data-ttu-id="8e564-261"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>類別會為您處理這種情況。</span><span class="sxs-lookup"><span data-stu-id="8e564-261">The <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> class handles this for you.</span></span> <span data-ttu-id="8e564-262">檢查它所傳回的 <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframepresentresult" target="_blank">HolographicFramePresentResult</a> ，以瞭解您是否需要釋出並重新建立 Direct3D 裝置和裝置資源。</span><span class="sxs-lookup"><span data-stu-id="8e564-262">Inspect the <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframepresentresult" target="_blank">HolographicFramePresentResult</a> it returns to find out if you need to release and recreate the Direct3D device and device-based resources.</span></span>

```cpp
// The PresentUsingCurrentPrediction API will detect when the graphics device
// changes or becomes invalid. When this happens, it is considered a Direct3D
// device lost scenario.
if (presentResult == HolographicFramePresentResult::DeviceRemoved)
{
    // The Direct3D device, context, and resources should be recreated.
    HandleDeviceLost();
}
```

<span data-ttu-id="8e564-263">請注意，如果 Direct3D 裝置已遺失，而您已重新建立，則必須告訴 <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a> 開始使用新的裝置。</span><span class="sxs-lookup"><span data-stu-id="8e564-263">Note that if the Direct3D device was lost, and you did recreate it, you have to tell the <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a> to start using the new device.</span></span> <span data-ttu-id="8e564-264">將會重新建立此裝置的交換鏈。</span><span class="sxs-lookup"><span data-stu-id="8e564-264">The swap chain will be recreated for this device.</span></span>

<span data-ttu-id="8e564-265">從 **DeviceResources：： InitializeUsingHolographicSpace** ：</span><span class="sxs-lookup"><span data-stu-id="8e564-265">From **DeviceResources::InitializeUsingHolographicSpace** :</span></span>

```
m_holographicSpace.SetDirect3D11Device(m_d3dInteropDevice);
```

<span data-ttu-id="8e564-266">當您的框架出現之後，您可以返回主要的程式迴圈，並允許它繼續前往下一個畫面格。</span><span class="sxs-lookup"><span data-stu-id="8e564-266">Once your frame is presented, you can return back to the main program loop and allow it to continue to the next frame.</span></span>

## <a name="hybrid-graphics-pcs-and-mixed-reality-applications"></a><span data-ttu-id="8e564-267">混合式圖形電腦和混合現實應用程式</span><span class="sxs-lookup"><span data-stu-id="8e564-267">Hybrid graphics PCs and mixed reality applications</span></span>

<span data-ttu-id="8e564-268">Windows 10 Creators Update 的電腦可以設定為 **離散和** 整合式 gpu。</span><span class="sxs-lookup"><span data-stu-id="8e564-268">Windows 10 Creators Update PCs may be configured with **both** discrete and integrated GPUs.</span></span> <span data-ttu-id="8e564-269">使用這些類型的電腦時，Windows 會選擇耳機所連接的介面卡。</span><span class="sxs-lookup"><span data-stu-id="8e564-269">With these types of computers, Windows will choose the adapter the headset is connected to.</span></span> <span data-ttu-id="8e564-270">應用程式必須確定它所建立的 DirectX 裝置使用相同的介面卡。</span><span class="sxs-lookup"><span data-stu-id="8e564-270">Applications must ensure the DirectX device it creates uses the same adapter.</span></span>

<span data-ttu-id="8e564-271">最常見的 Direct3D 範例程式碼示範如何使用預設硬體配接器來建立 DirectX 裝置，該裝置在混合式系統上可能與用於耳機的不同。</span><span class="sxs-lookup"><span data-stu-id="8e564-271">Most general Direct3D sample code demonstrates creating a DirectX device using the default hardware adapter, which on a hybrid system may not be the same as the one used for the headset.</span></span>

<span data-ttu-id="8e564-272">若要解決這種情況可能造成的任何問題，請使用<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>的<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicadapterid" target="_blank">HolographicAdapterId</a> 。PrimaryAdapterId ( # A1 或<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay" target="_blank">HolographicDisplay</a>。AdapterId ( # A3。</span><span class="sxs-lookup"><span data-stu-id="8e564-272">To work around any issues this may cause, use the <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicadapterid" target="_blank">HolographicAdapterId</a> from either <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>.PrimaryAdapterId() or <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay" target="_blank">HolographicDisplay</a>.AdapterId().</span></span> <span data-ttu-id="8e564-273">然後，您可以使用這個 adapterId 來選取使用 IDXGIFactory4 EnumAdapterByLuid 的正確 DXGIAdapter。</span><span class="sxs-lookup"><span data-stu-id="8e564-273">This adapterId can then be used to select the right DXGIAdapter using IDXGIFactory4.EnumAdapterByLuid.</span></span>

<span data-ttu-id="8e564-274">從 **DeviceResources：： InitializeUsingHolographicSpace** ：</span><span class="sxs-lookup"><span data-stu-id="8e564-274">From **DeviceResources::InitializeUsingHolographicSpace** :</span></span>

```cpp
// The holographic space might need to determine which adapter supports
// holograms, in which case it will specify a non-zero PrimaryAdapterId.
LUID id =
{
    m_holographicSpace.PrimaryAdapterId().LowPart,
    m_holographicSpace.PrimaryAdapterId().HighPart
};

// When a primary adapter ID is given to the app, the app should find
// the corresponding DXGI adapter and use it to create Direct3D devices
// and device contexts. Otherwise, there is no restriction on the DXGI
// adapter the app can use.
if ((id.HighPart != 0) || (id.LowPart != 0))
{
    UINT createFlags = 0;

    // Create the DXGI factory.
    ComPtr<IDXGIFactory1> dxgiFactory;
    winrt::check_hresult(
        CreateDXGIFactory2(
            createFlags,
            IID_PPV_ARGS(&dxgiFactory)
        ));
    ComPtr<IDXGIFactory4> dxgiFactory4;
    winrt::check_hresult(dxgiFactory.As(&dxgiFactory4));

    // Retrieve the adapter specified by the holographic space.
    winrt::check_hresult(
        dxgiFactory4->EnumAdapterByLuid(
            id,
            IID_PPV_ARGS(&m_dxgiAdapter)
        ));
}
else
{
    m_dxgiAdapter.Reset();
}
```

<span data-ttu-id="8e564-275">將 **DeviceResources：： CreateDeviceResources 更新為使用 IDXGIAdapter 的** 程式碼</span><span class="sxs-lookup"><span data-stu-id="8e564-275">Code to **update DeviceResources::CreateDeviceResources to use IDXGIAdapter**</span></span>

```cpp
// Create the Direct3D 11 API device object and a corresponding context.
ComPtr<ID3D11Device> device;
ComPtr<ID3D11DeviceContext> context;

const D3D_DRIVER_TYPE driverType = m_dxgiAdapter == nullptr ? D3D_DRIVER_TYPE_HARDWARE : D3D_DRIVER_TYPE_UNKNOWN;
const HRESULT hr = D3D11CreateDevice(
    m_dxgiAdapter.Get(),        // Either nullptr, or the primary adapter determined by Windows Holographic.
    driverType,                 // Create a device using the hardware graphics driver.
    0,                          // Should be 0 unless the driver is D3D_DRIVER_TYPE_SOFTWARE.
    creationFlags,              // Set debug and Direct2D compatibility flags.
    featureLevels,              // List of feature levels this app can support.
    ARRAYSIZE(featureLevels),   // Size of the list above.
    D3D11_SDK_VERSION,          // Always set this to D3D11_SDK_VERSION for Windows Runtime apps.
    &device,                    // Returns the Direct3D device created.
    &m_d3dFeatureLevel,         // Returns feature level of device created.
    &context                    // Returns the device immediate context.
);
```

<span data-ttu-id="8e564-276">**混合式圖形和媒體基礎**</span><span class="sxs-lookup"><span data-stu-id="8e564-276">**Hybrid graphics and Media Foundation**</span></span>

<span data-ttu-id="8e564-277">使用混合式系統上的媒體基礎可能會導致影片無法轉譯或影片材質已損毀的問題。</span><span class="sxs-lookup"><span data-stu-id="8e564-277">Using Media Foundation on hybrid systems may cause issues where video will not render or video texture is corrupt.</span></span> <span data-ttu-id="8e564-278">發生這種情況的原因是媒體基礎如上面所述，預設為系統行為。</span><span class="sxs-lookup"><span data-stu-id="8e564-278">This can occur because Media Foundation is defaulting to a system behavior as mentioned above.</span></span> <span data-ttu-id="8e564-279">在某些情況下，需要建立個別的 ID3D11Device 來支援多執行緒處理，並設定正確的建立旗標。</span><span class="sxs-lookup"><span data-stu-id="8e564-279">In some scenarios, creating a separate ID3D11Device is required to support multi-threading and the correct creation flags are set.</span></span>

<span data-ttu-id="8e564-280">當您初始化 ID3D11Device 時，D3D11_CREATE_DEVICE_VIDEO_SUPPORT 旗標必須定義為 D3D11_CREATE_DEVICE_FLAG 的一部分。</span><span class="sxs-lookup"><span data-stu-id="8e564-280">When initializing the ID3D11Device, D3D11_CREATE_DEVICE_VIDEO_SUPPORT flag must be defined as part of the D3D11_CREATE_DEVICE_FLAG.</span></span> <span data-ttu-id="8e564-281">一旦建立裝置和內容之後，請呼叫 <a href="https://docs.microsoft.com/windows/desktop/api/d3d10/nf-d3d10-id3d10multithread-setmultithreadprotected" target="_blank">SetMultithreadProtected</a> 來啟用多執行緒處理。</span><span class="sxs-lookup"><span data-stu-id="8e564-281">Once the device and context is created, call <a href="https://docs.microsoft.com/windows/desktop/api/d3d10/nf-d3d10-id3d10multithread-setmultithreadprotected" target="_blank">SetMultithreadProtected</a> to enable multithreading.</span></span> <span data-ttu-id="8e564-282">若要將裝置與 <a href="https://docs.microsoft.com/windows/desktop/api/mfobjects/nn-mfobjects-imfdxgidevicemanager" target="_blank">IMFDXGIDeviceManager</a>建立關聯，請使用 <a href="https://docs.microsoft.com/windows/desktop/api/mfobjects/nf-mfobjects-imfdxgidevicemanager-resetdevice" target="_blank">IMFDXGIDeviceManager：： ResetDevice</a> 函式。</span><span class="sxs-lookup"><span data-stu-id="8e564-282">To associate the device with the <a href="https://docs.microsoft.com/windows/desktop/api/mfobjects/nn-mfobjects-imfdxgidevicemanager" target="_blank">IMFDXGIDeviceManager</a>, use the <a href="https://docs.microsoft.com/windows/desktop/api/mfobjects/nf-mfobjects-imfdxgidevicemanager-resetdevice" target="_blank">IMFDXGIDeviceManager::ResetDevice</a> function.</span></span>

<span data-ttu-id="8e564-283">**將 ID3D11Device 與 IMFDXGIDeviceManager 建立關聯** 的程式碼：</span><span class="sxs-lookup"><span data-stu-id="8e564-283">Code to **associate a ID3D11Device with IMFDXGIDeviceManager** :</span></span>

```cpp
// create dx device for media pipeline
winrt::com_ptr<ID3D11Device> spMediaDevice;

// See above. Also make sure to enable the following flags on the D3D11 device:
//   * D3D11_CREATE_DEVICE_VIDEO_SUPPORT
//   * D3D11_CREATE_DEVICE_BGRA_SUPPORT
if (FAILED(CreateMediaDevice(spAdapter.get(), &spMediaDevice)))
    return;                                                     

// Turn multithreading on 
winrt::com_ptr<ID3D10Multithread> spMultithread;
if (spContext.try_as(spMultithread))
{
    spMultithread->SetMultithreadProtected(TRUE);
}

// lock the shared dxgi device manager
// call MFUnlockDXGIDeviceManager when no longer needed
UINT uiResetToken;
winrt::com_ptr<IMFDXGIDeviceManager> spDeviceManager;
hr = MFLockDXGIDeviceManager(&uiResetToken, spDeviceManager.put());
if (FAILED(hr))
    return hr;
    
// associate the device with the manager
hr = spDeviceManager->ResetDevice(spMediaDevice.get(), uiResetToken);
if (FAILED(hr))
    return hr;
```

## <a name="see-also"></a><span data-ttu-id="8e564-284">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8e564-284">See also</span></span>
* [<span data-ttu-id="8e564-285">DirectX 中的座標系統</span><span class="sxs-lookup"><span data-stu-id="8e564-285">Coordinate systems in DirectX</span></span>](coordinate-systems-in-directx.md)
* [<span data-ttu-id="8e564-286">使用 HoloLens 模擬器</span><span class="sxs-lookup"><span data-stu-id="8e564-286">Using the HoloLens emulator</span></span>](../platform-capabilities-and-apis/using-the-hololens-emulator.md)
