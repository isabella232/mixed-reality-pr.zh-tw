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
# <a name="rendering-in-directx"></a>DirectX 中的呈現

> [!NOTE]
> 本文與舊版 WinRT 原生 Api 相關。  針對新的原生應用程式專案，建議使用 **[OPENXR API](openxr-getting-started.md)** 。

Windows Mixed Reality 建基於 DirectX，為使用者產生豐富的3D 圖形體驗。 轉譯抽象概念位於 DirectX 之上，並可讓應用程式考慮全像系統所預測的全像全像全像攝影場景的位置和方向。 然後，開發人員可以找出相對於每個相機的全像投影，讓應用程式在使用者四處移動時，轉譯各種空間座標系統中的全像影像。

注意：此逐步解說說明 Direct3D 11 中的全像轉譯。 您也可以使用「混合現實應用程式範本」延伸模組來提供 Direct3D 12 Windows Mixed Reality 應用程式範本。

## <a name="update-for-the-current-frame"></a>目前畫面格的更新

若要更新影像的應用程式狀態，每個畫面格一次，應用程式將會：
* 從顯示管理系統取得 <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> 。
* 在轉譯完成時，使用相機視圖的目前預測來更新場景。 請注意，全像攝影場景可以有一個以上的相機。

若要轉譯成全像攝影相機，每個畫面格一次，應用程式將會：
* 針對每個相機，使用系統中的相機視圖和投影矩陣，轉譯目前框架的場景。

### <a name="create-a-new-holographic-frame-and-get-its-prediction"></a>建立新的全像攝影框架並取得其預測

<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>具有應用程式所需的資訊，以便更新和轉譯目前的框架。 應用程式會藉由呼叫 **CreateNextFrame** 方法來開始每個新的框架。 當呼叫這個方法時，會使用最新可用的感應器資料來進行預測，並封裝在 **CurrentPrediction** 物件中。

必須針對每個呈現的框架使用新的框架物件，因為它只適用于及時的有效時間。 **CurrentPrediction** 屬性包含攝影機位置之類的資訊。 這項資訊會在預期使用者看到畫面格的確切時間點推斷。

下列程式碼會從 **AppMain：： Update** 摘錄：

```cpp
// The HolographicFrame has information that the app needs in order
// to update and render the current frame. The app begins each new
// frame by calling CreateNextFrame.
HolographicFrame holographicFrame = m_holographicSpace.CreateNextFrame();

// Get a prediction of where holographic cameras will be when this frame
// is presented.
HolographicFramePrediction prediction = holographicFrame.CurrentPrediction();
```

### <a name="process-camera-updates"></a>處理相機更新

背景緩衝區可以從框架變更為框架。 您的應用程式必須驗證每個相機的後置緩衝區，並視需要釋放和重新建立資源檢視和深度緩衝區。 請注意，預測中的一組姿勢是目前框架中使用的相機授權清單。 通常，您可以使用這份清單來逐一查看一組攝影機。

從 **AppMain：： Update** ：

```cpp
m_deviceResources->EnsureCameraResources(holographicFrame, prediction);
```

從 **DeviceResources：： EnsureCameraResources** ：

```cpp
for (HolographicCameraPose const& cameraPose : prediction.CameraPoses())
{
    HolographicCameraRenderingParameters renderingParameters = frame.GetRenderingParameters(cameraPose);
    CameraResources* pCameraResources = cameraResourceMap[cameraPose.HolographicCamera().Id()].get();
    pCameraResources->CreateResourcesForBackBuffer(this, renderingParameters);
}
```

### <a name="get-the-coordinate-system-to-use-as-a-basis-for-rendering"></a>取得座標系統作為轉譯的基礎

Windows Mixed Reality 可讓您的應用程式視需要建立各種 [座標系統](coordinate-systems-in-directx.md) ，例如，連接的參考框架和固定的參考框架，以追蹤實體世界中的位置。 然後，您的應用程式可以使用這些座標系統，來指出要在哪裡轉譯每個畫面格。 從 API 要求座標時，您一律會傳入要在其中表示這些座標的 <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a> 。

從 **AppMain：： Update** ：

```cpp
pose = SpatialPointerPose::TryGetAtTimestamp(
    m_stationaryReferenceFrame.CoordinateSystem(), prediction.Timestamp());
```

然後，您可以在轉譯場景中的內容時，使用這些座標系統來產生身歷聲視圖矩陣。

從 **CameraResources：： UpdateViewProjectionBuffer** ：

```cpp
// Get a container object with the view and projection matrices for the given
// pose in the given coordinate system.
auto viewTransformContainer = cameraPose.TryGetViewTransform(coordinateSystem);
```

### <a name="process-gaze-and-gesture-input"></a>處理注視和手勢輸入

[注視](gaze-in-directx.md) 和 [手](hands-and-motion-controllers-in-directx.md) 輸入不是以時間為基礎，因此不需要在 **StepTimer** 函式中更新。 不過，此輸入是應用程式需要查看每個畫面格的內容。

### <a name="process-time-based-updates"></a>處理以時間為基礎的更新

任何即時轉譯應用程式都需要某種方式來處理以時間為基礎的更新;我們在 Windows 全像應用程式範本中，透過 **StepTimer** 的執行方式提供了一種方法。 這類似于 DirectX 11 UWP 應用程式範本中提供的 StepTimer，因此如果您已經看過該範本，您應該會在熟悉的基礎上。 此 StepTimer 範例協助程式類別可以提供固定的時間步驟更新以及可變的時間步驟更新，而預設模式則是可變時間步驟。

在全像攝影轉譯的案例中，我們特別選擇不要將太多放入計時器函數中。 這是因為您可以將它設定為固定的時間步驟，在這種情況下，每個畫面可能會被呼叫一次以上，或根本不會針對某些框架呼叫一次，而且每個畫面格的全像資料更新應該會進行一次。


從 **AppMain：： Update** ：

```cpp
m_timer.Tick([this]()
{
    m_spinningCubeRenderer->Update(m_timer);
});
```

### <a name="position-and-rotate-holograms-in-your-coordinate-system"></a>在座標系統中定位和旋轉全像投影

如果您是在單一座標系統中操作，當範本使用 **SpatialStationaryReferenceFrame** 時，此程式不會與您在3d 圖形中使用的方式不同。 在這裡，我們會旋轉 cube，並將模型矩陣設定為相對於固定座標系統中的位置。

從 **SpinningCubeRenderer：： Update** ：

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

**關於 advanced 案例的注意事項：** 旋轉 cube 是一個非常簡單的範例，說明如何在單一參考框架內放置全像影像。 您也可以同時在相同的呈現框架中 [使用多個 SpatialCoordinateSystems](coordinate-systems-in-directx.md) 。

### <a name="update-constant-buffer-data"></a>更新常數緩衝區資料

內容的模型轉換會如往常般更新。 現在，您將會針對要轉譯的座標系統，計算出有效的轉換。

從 **SpinningCubeRenderer：： Update** ：

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

什麼是視圖和投射轉換？ 為了獲得最佳結果，我們想要等到我們準備好進行繪製呼叫之後，才取得這些。

## <a name="render-the-current-frame"></a>轉譯目前的框架

轉譯 Windows Mixed Reality 與在 2D mono 顯示器上轉譯的方式不同，但有一些需要注意的差異：
* 全像攝影框架的預測很重要。 預測越接近您的畫面格呈現的樣子，您的全像全像投影就越好。
* Windows Mixed Reality 控制攝影機的視圖。 您需要轉譯為每個畫面格，因為全像照片框架將在稍後呈現。
* 建議您使用對轉譯目標陣列使用實例繪製來完成身歷聲轉譯。 全像「全像」應用程式範本會使用具現化繪圖的建議方法來繪製到轉譯目標陣列，這會使用呈現目標視圖 **Texture2DArray** 。
* 如果您想要在不使用身歷聲實例的情況下轉譯，則必須建立兩個非陣列 RenderTargetViews (每個) ，每一個都參考從系統提供給應用程式之 **Texture2DArray** 中的兩個配量之一。 這是不建議的作法，因為它的速度通常會比使用實例慢很多。

### <a name="get-an-updated-holographicframe-prediction"></a>取得更新的 HolographicFrame 預測

更新框架預測可增強影像穩定的效能，並可讓您更精確地放置全像投影，因為預測和使用者可以看到畫面格的時間較短。 在呈現之前，最好先更新您的框架預測。

```cpp
holographicFrame.UpdateCurrentPrediction();
HolographicFramePrediction prediction = holographicFrame.CurrentPrediction();
```

### <a name="render-to-each-camera"></a>轉譯為每個相機

在一組相機上的迴圈會在預測中產生，並轉譯為此集合中的每個相機。

**設定您的轉譯階段**

Windows Mixed Reality 使用 stereoscopic 轉譯來加強深度的幻影和轉譯 stereoscopically，讓左邊和右邊的顯示都處於作用中狀態。 使用 stereoscopic 轉譯時，會有兩個顯示器之間的位移，而大腦可將其視為實際的深度。 本節說明如何使用 Windows 全像應用程式範本中的程式碼，使用實例進行 stereoscopic 轉譯。

每個攝影機都有自己的轉譯目標 (回緩衝區) ，以及將矩陣和投影矩陣放入全像空間中。 您的應用程式將需要建立任何其他以相機為基礎的資源，例如深度緩衝區（以每個相機為基礎）。 在 Windows 全像應用程式範本中，我們提供一個協助程式類別，將這些資源組合在 DX：： CameraResources 中。 從設定轉譯目標視圖開始：

從 **AppMain：： Render** ：

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

**使用預測來取得相機的視圖和投射矩陣**

每個全像攝影相機的視圖和投射矩陣都會隨著每個畫面格而改變。 重新整理每個全息相機的常數緩衝區中的資料。 在您更新預測之後，以及對該攝影機進行任何繪製呼叫之前，請執行此動作。

從 **AppMain：： Render** ：

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

在這裡，我們會示範如何從相機姿勢取得矩陣。 在這個過程中，我們也會取得相機的目前的視口。 請注意我們如何提供座標系統：這是我們用來瞭解注視的相同座標系統，也是我們用來定位旋轉 cube 的相同座標系統。


從 **CameraResources：： UpdateViewProjectionBuffer** ：

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

應設定每個畫面格的區。 您的頂點著色器 (至少) 通常需要存取 view/投射資料。


從 **CameraResources：： AttachViewProjectionBuffer** ：

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

轉譯 **成相機背面緩衝區，並認可深度緩衝區** ：

最好先檢查 **TryGetViewTransform** 是否成功，再嘗試使用視圖/投射資料，因為如果無法定位座標系統 (例如，追蹤已中斷，) 您的應用程式在該框架中無法呈現。 如果 **CameraResources** 類別指出成功更新，則範本只 **會呼叫旋轉** cube 上的轉譯。

為了讓開發人員或使用者將它們放在世界各地，Windows Mixed Reality 包含影像 [穩定](../platform-capabilities-and-apis/hologram-stability.md)的功能。 影像穩定有助於隱藏轉譯管線固有的延遲，以確保最適合使用者的全像攝影體驗;您可以指定焦點點來進一步增強影像穩定，或可以提供深度緩衝區來即時計算優化的影像穩定。

為了獲得最佳結果，您的應用程式應該使用 <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer" target="_blank">CommitDirect3D11DepthBuffer</a> API 提供深度緩衝區。 Windows Mixed Reality 接著可以使用深度緩衝區的幾何資訊，即時優化影像穩定。 Windows 全像影像應用程式範本預設會認可應用程式的深度緩衝區，以協助優化全像全像全像是

從 **AppMain：： Render** ：

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
>Windows 將會在 GPU 上處理您的深度材質，因此必須可以使用您的深度緩衝區做為著色器資源。 您所建立的 ID3D11Texture2D 應該採用無類型的格式，而且應該系結為著色器資源檢視。 以下範例說明如何建立可針對影像穩定認可的深度材質。

CommitDirect3D11DepthBuffer 的 **深度緩衝區資源建立** 程式碼：

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

**繪製全息內容**

Windows 全像攝影應用程式範本會使用將實例幾何的建議技術轉譯為大小2的 Texture2DArray，以身歷聲呈現內容。 讓我們來看看這部分的實例，以及它在 Windows Mixed Reality 的運作方式。

從 **SpinningCubeRenderer：： Render** ：

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

每個實例都會從常數緩衝區存取不同的視圖/投射矩陣。 以下是常數緩衝區結構，也就是2個矩陣的陣列。

From **VertexShaderShared. hlsl** ，包含 **VPRTVertexShader. hlsl** ：

```HLSL
// A constant buffer that stores each set of view and projection matrices in column-major format.
cbuffer ViewProjectionConstantBuffer : register(b1)
{
    float4x4 viewProjection[2];
};
```

您必須為每個圖元設定轉譯目標陣列索引。 在下列程式碼片段中，viewId 會對應至 **SV_RenderTargetArrayIndex** 語義。 請注意，這需要選擇性 Direct3D 11.3 功能的支援，以允許從任何著色器階段設定轉譯目標陣列索引語義。

從 **VPRTVertexShader. hlsl** ：

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

From **VertexShaderShared. hlsl** ，包含 **VPRTVertexShader. hlsl** ：

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

如果您想要使用現有的實例繪圖技術搭配此方法繪製到身歷聲轉譯目標陣列，您只需要繪製您平常所擁有之實例數目的兩倍。 在著色器中，將 **instId** 除以2以取得原始實例識別碼，此識別碼可編制索引為 (例如) 每個物件資料的緩衝區： `int actualIdx = input.instId / 2;`

### <a name="important-note-about-rendering-stereo-content-on-hololens"></a>在 HoloLens 上轉譯身歷聲內容的重要注意事項

Windows Mixed Reality 支援從任何著色器階段設定轉譯目標陣列索引的能力;一般來說，這是一項只能在幾何著色器階段完成的工作，因為它是針對 Direct3D 11 定義了語義的方式。 在這裡，我們會示範如何設定只設定頂點和圖元著色器階段的轉譯管線的完整範例。 著色器程式碼如上所述。

從 **SpinningCubeRenderer：： Render** ：

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

### <a name="important-note-about-rendering-on-non-hololens-devices"></a>在非 HoloLens 裝置上轉譯的重要注意事項

若要在頂點著色器中設定轉譯目標陣列索引，圖形驅動程式必須支援 HoloLens 支援的選用 Direct3D 11.3 功能。 您的應用程式可以安全地執行轉譯所需的技巧，並符合在 Microsoft HoloLens 上執行的所有需求。

您可能也會想要使用 HoloLens 模擬器，這是一個功能強大的開發工具，可供您的全像裝置應用程式使用，並支援 Windows Mixed Reality 連接到 Windows 10 電腦的沉浸式耳機裝置。 非 HoloLens 轉譯路徑的支援，因此，所有 Windows Mixed Reality 也都內建在 Windows 全像應用程式範本中。 在範本程式碼中，您會發現程式碼，讓您的全像應用程式可在開發電腦上的 GPU 上執行。 以下是 **DeviceResources** 類別檢查此選用功能支援的方式。

從 **DeviceResources：： CreateDeviceResources** ：

```cpp
// Check for device support for the optional feature that allows setting the render target array index from the vertex shader stage.
D3D11_FEATURE_DATA_D3D11_OPTIONS3 options;
m_d3dDevice->CheckFeatureSupport(D3D11_FEATURE_D3D11_OPTIONS3, &options, sizeof(options));
if (options.VPAndRTArrayIndexFromAnyShaderFeedingRasterizer)
{
    m_supportsVprt = true;
}
```

若要在沒有此選用功能的情況下支援轉譯，您的應用程式必須使用幾何著色器來設定轉譯目標陣列索引。 此程式碼片段會在 *after* **VSSetConstantBuffers** 之後 *，以及上* 一節所示的程式碼範例中 **pssetshade** ，以說明如何在 HoloLens 上呈現身歷聲。

從 **SpinningCubeRenderer：： Render** ：

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

**HLSL 注意** ：在此情況下，您也必須載入稍微修改的端點著色器，以使用一律允許的著色器語義（例如 TEXCOORD0），將轉譯目標陣列索引傳遞給幾何著色器。 幾何著色器不需要執行任何工作;樣板幾何著色器會傳遞所有資料，但呈現目標陣列索引例外，可用來設定 SV_RenderTargetArrayIndex 語義。

適用于 GeometryShader 的應用程式範本程式碼 **hlsl** ：

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

## <a name="present"></a>存在

### <a name="enable-the-holographic-frame-to-present-the-swap-chain"></a>讓全像畫面框架呈現交換鏈

使用 Windows Mixed Reality 時，系統會控制交換鏈。 然後系統會管理呈現每個全像攝影攝影機的畫面，以確保高品質的使用者體驗。 它也會為每個相機提供一個可更新每個畫面格的區，以優化系統的各個層面，例如影像穩定或混合實境擷取。 因此，使用 DirectX 的全像全息應用程式不會在 DXGI 交換 **鏈上呼叫** 。 相反地，您會使用 <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> 類別，在完成繪製框架之後，顯示該框架的所有 swapchains。

從 **DeviceResources：:P 重發** ：

```
HolographicFramePresentResult presentResult = frame.PresentUsingCurrentPrediction();
```

根據預設，這個 API 會等候框架在傳回之前完成。 在新的畫面上開始工作之前，全像攝影應用程式應該等候前一個畫面格完成，因為這樣可減少延遲，並允許來自全像攝影框架預測的較佳結果。 這不是一項困難的規則，如果您的畫面格需要超過一個螢幕重新整理才能轉譯，則可以將 HolographicFramePresentWaitBehavior 參數傳遞給 <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.presentusingcurrentprediction" target="_blank">PresentUsingCurrentPrediction</a>來停用這項等候。 在此情況下，您可能會使用非同步轉譯執行緒，以維持 GPU 的連續負載。 請注意，HoloLens 裝置的重新整理頻率為60hz，其中一個框架的持續時間大約為16毫秒。 沉浸式耳機裝置的範圍可以從60hz 到 90hz;在 90 hz 重新整理顯示器時，每個畫面的持續時間大約為11毫秒。

### <a name="handle-devicelost-scenarios-in-cooperation-with-the-holographicframe"></a>處理與 HolographicFrame 合作的 DeviceLost 案例

DirectX 11 應用程式通常會想要檢查由 DXGI 交換鏈 **目前** 的函式所傳回的 HRESULT，以找出是否有 **DeviceLost** 錯誤。 <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>類別會為您處理這種情況。 檢查它所傳回的 <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframepresentresult" target="_blank">HolographicFramePresentResult</a> ，以瞭解您是否需要釋出並重新建立 Direct3D 裝置和裝置資源。

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

請注意，如果 Direct3D 裝置已遺失，而您已重新建立，則必須告訴 <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a> 開始使用新的裝置。 將會重新建立此裝置的交換鏈。

從 **DeviceResources：： InitializeUsingHolographicSpace** ：

```
m_holographicSpace.SetDirect3D11Device(m_d3dInteropDevice);
```

當您的框架出現之後，您可以返回主要的程式迴圈，並允許它繼續前往下一個畫面格。

## <a name="hybrid-graphics-pcs-and-mixed-reality-applications"></a>混合式圖形電腦和混合現實應用程式

Windows 10 Creators Update 的電腦可以設定為 **離散和** 整合式 gpu。 使用這些類型的電腦時，Windows 會選擇耳機所連接的介面卡。 應用程式必須確定它所建立的 DirectX 裝置使用相同的介面卡。

最常見的 Direct3D 範例程式碼示範如何使用預設硬體配接器來建立 DirectX 裝置，該裝置在混合式系統上可能與用於耳機的不同。

若要解決這種情況可能造成的任何問題，請使用<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>的<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicadapterid" target="_blank">HolographicAdapterId</a> 。PrimaryAdapterId ( # A1 或<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay" target="_blank">HolographicDisplay</a>。AdapterId ( # A3。 然後，您可以使用這個 adapterId 來選取使用 IDXGIFactory4 EnumAdapterByLuid 的正確 DXGIAdapter。

從 **DeviceResources：： InitializeUsingHolographicSpace** ：

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

將 **DeviceResources：： CreateDeviceResources 更新為使用 IDXGIAdapter 的** 程式碼

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

**混合式圖形和媒體基礎**

使用混合式系統上的媒體基礎可能會導致影片無法轉譯或影片材質已損毀的問題。 發生這種情況的原因是媒體基礎如上面所述，預設為系統行為。 在某些情況下，需要建立個別的 ID3D11Device 來支援多執行緒處理，並設定正確的建立旗標。

當您初始化 ID3D11Device 時，D3D11_CREATE_DEVICE_VIDEO_SUPPORT 旗標必須定義為 D3D11_CREATE_DEVICE_FLAG 的一部分。 一旦建立裝置和內容之後，請呼叫 <a href="https://docs.microsoft.com/windows/desktop/api/d3d10/nf-d3d10-id3d10multithread-setmultithreadprotected" target="_blank">SetMultithreadProtected</a> 來啟用多執行緒處理。 若要將裝置與 <a href="https://docs.microsoft.com/windows/desktop/api/mfobjects/nn-mfobjects-imfdxgidevicemanager" target="_blank">IMFDXGIDeviceManager</a>建立關聯，請使用 <a href="https://docs.microsoft.com/windows/desktop/api/mfobjects/nf-mfobjects-imfdxgidevicemanager-resetdevice" target="_blank">IMFDXGIDeviceManager：： ResetDevice</a> 函式。

**將 ID3D11Device 與 IMFDXGIDeviceManager 建立關聯** 的程式碼：

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

## <a name="see-also"></a>另請參閱
* [DirectX 中的座標系統](coordinate-systems-in-directx.md)
* [使用 HoloLens 模擬器](../platform-capabilities-and-apis/using-the-hololens-emulator.md)
