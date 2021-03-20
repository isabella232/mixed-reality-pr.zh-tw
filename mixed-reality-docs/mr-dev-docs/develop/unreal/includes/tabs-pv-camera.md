---
ms.openlocfilehash: e79b14c19a452b5b78c6f8cf7ea24bd65bfa0eaa
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "98605299"
---
# <a name="426"></a>[<span data-ttu-id="46653-101">4.26</span><span class="sxs-lookup"><span data-stu-id="46653-101">4.26</span></span>](#tab/426) 

## <a name="pv-camera-feed-setup"></a><span data-ttu-id="46653-102">PV 相機摘要設定</span><span class="sxs-lookup"><span data-stu-id="46653-102">PV Camera Feed Setup</span></span>

> [!IMPORTANT]
> <span data-ttu-id="46653-103">PV 相機會同時在 Windows Mixed Reality 和 OpenXR 外掛程式中實作。</span><span class="sxs-lookup"><span data-stu-id="46653-103">PV camera is implemented in both Windows Mixed Reality and OpenXR plugins.</span></span> <span data-ttu-id="46653-104">不過，OpenXR 需要安裝 [Microsoft OpenXR 外掛程式](https://github.com/microsoft/Microsoft-OpenXR-Unreal)。</span><span class="sxs-lookup"><span data-stu-id="46653-104">However OpenXR needs [Microsoft OpenXR plugin](https://github.com/microsoft/Microsoft-OpenXR-Unreal) to be installed.</span></span> <span data-ttu-id="46653-105">此外，OpenXR 目前有所限制，相機可以搭配 DirectX11 RHI 運作。</span><span class="sxs-lookup"><span data-stu-id="46653-105">Also OpenXR has current limitation, camera can work with DirectX11 RHI.</span></span> <span data-ttu-id="46653-106">在更高的 Unreal 版本中將會修正這項限制。</span><span class="sxs-lookup"><span data-stu-id="46653-106">This limitation will be fixed in a further Unreal version.</span></span> 

- <span data-ttu-id="46653-107">在 [專案設定] > [HoloLens] 中，啟用 [網路攝影機] 功能：</span><span class="sxs-lookup"><span data-stu-id="46653-107">In **Project Settings > HoloLens**, enable the **Webcam** capability:</span></span>

![已醒目提示 [網路攝影機] 屬性的 HoloLens 專案設定螢幕擷取畫面](../images/unreal-pvc-img-01.png)

- <span data-ttu-id="46653-109">建立名為 "CamCapture" 的新動作項目，並新增平面來呈現相機摘要：</span><span class="sxs-lookup"><span data-stu-id="46653-109">Create a new actor called “CamCapture” and add a plane to render the camera feed:</span></span>

![螢幕擷取畫面：已新增平面的動作項目](../images/unreal-pvc-img-02.png)

- <span data-ttu-id="46653-111">將動作項目新增至您的場景，建立具有「材質物件參數」且名為 CamTextureMaterial 的新材質，以及材質範例。</span><span class="sxs-lookup"><span data-stu-id="46653-111">Add the actor to your scene, create a new material called CamTextureMaterial with a Texture Object Parameter, and a texture sample.</span></span>  <span data-ttu-id="46653-112">將材質的 rgb 資料傳送至輸出放射色彩：</span><span class="sxs-lookup"><span data-stu-id="46653-112">Send the texture’s rgb data to the output emissive color:</span></span>

![藍圖：材質和材質範例](../images/unreal-pvc-img-03.png)

## <a name="rendering-the-pv-camera-feed"></a><span data-ttu-id="46653-114">呈現 PV 相機摘要</span><span class="sxs-lookup"><span data-stu-id="46653-114">Rendering the PV Camera Feed</span></span>

- <span data-ttu-id="46653-115">在 CamCapture 藍圖中，開啟「PV 相機」：</span><span class="sxs-lookup"><span data-stu-id="46653-115">In the CamCapture blueprint, turn on the PV Camera:</span></span>

![藍圖：已開啟 PV 相機的「切換 ARCapture」函式](../images/unreal-pvc-img-04.png)

- <span data-ttu-id="46653-117">從 CamTextureMaterial 建立動態材質執行個體，並將此材質指派給動作項目的平面：</span><span class="sxs-lookup"><span data-stu-id="46653-117">Create a dynamic material instance from CamTextureMaterial and assign this material to the actor’s plane:</span></span>

![藍圖：建立動態材質執行個體函式](../images/unreal-pvc-img-05.png)

- <span data-ttu-id="46653-119">從相機摘要取得材質，並將其指派給動態材質 (如果此材質有效的話)。</span><span class="sxs-lookup"><span data-stu-id="46653-119">Get the texture from the camera feed and assign it to the dynamic material if it's valid.</span></span>  <span data-ttu-id="46653-120">如果此材質無效，請啟動計時器，並在逾時後再試一次：</span><span class="sxs-lookup"><span data-stu-id="46653-120">If the texture isn't valid, start a timer and try again after the timeout:</span></span>

![藍圖：指派給動態材質的相機摘要材質](../images/unreal-pvc-img-06.png)

- <span data-ttu-id="46653-122">最後，依據相機影像的外觀比例來調整平面：</span><span class="sxs-lookup"><span data-stu-id="46653-122">Finally, scale the plane by the camera image’s aspect ratio:</span></span>

![藍圖：相對於相機影像外觀比例來調整的平面](../images/unreal-pvc-img-07.png)

## <a name="find-camera-positions-in-world-space"></a><span data-ttu-id="46653-124">尋找世界空間中的相機位置</span><span class="sxs-lookup"><span data-stu-id="46653-124">Find Camera Positions in World Space</span></span>

<span data-ttu-id="46653-125">HoloLens 2 上的相機會與裝置的頭部追蹤垂直偏移。</span><span class="sxs-lookup"><span data-stu-id="46653-125">The camera on the HoloLens 2 is offset vertically from the device’s head tracking.</span></span>  <span data-ttu-id="46653-126">有幾個函式可用來定位世界空間中的相機，以因應此情況。</span><span class="sxs-lookup"><span data-stu-id="46653-126">A few functions exist to locate the camera in world space to account for the offset.</span></span>

<span data-ttu-id="46653-127">GetPVCameraToWorldTransform 會取得 PV 相機世界空間中的轉換，並將其定位在相機鏡頭上：</span><span class="sxs-lookup"><span data-stu-id="46653-127">GetPVCameraToWorldTransform gets the transform in world space of the PV Camera and will be positioned on the camera lens:</span></span>

![藍圖：取得 PVCamera 對世界轉換函式](../images/unreal-pvc-img-08.png)

<span data-ttu-id="46653-129">GetWorldSpaceRayFromCameraPoint 會從相機鏡頭射出光線到 Unreal 世界空間中的場景，以找出相機框架中特定像素的內容：</span><span class="sxs-lookup"><span data-stu-id="46653-129">GetWorldSpaceRayFromCameraPoint casts a ray from the camera lens into the scene in Unreal world space to find a pixel's content in the camera frame:</span></span>

![藍圖：取得從相機位置點射出的世界空間光線](../images/unreal-pvc-img-09.png)

<span data-ttu-id="46653-131">GetPVCameraIntrinsics 會傳回相機內建值，這可在對相機框架進行電腦視覺處理時用到：</span><span class="sxs-lookup"><span data-stu-id="46653-131">GetPVCameraIntrinsics returns the camera intrinsic values, which can be used when doing computer vision processing on a camera frame:</span></span>

![藍圖：取得 PVCamera 內建函式](../images/unreal-pvc-img-10.png)

<span data-ttu-id="46653-133">若要找出世界空間內的特定像素座標上有何項目，請搭配使用光線追蹤與世界空間光線：</span><span class="sxs-lookup"><span data-stu-id="46653-133">To find what exists in world space at a particular pixel coordinate, use a line trace with the world space ray:</span></span>

![藍圖：世界空間光線，用來找出世界空間內的特定座標上有何項目](../images/unreal-pvc-img-11.png)

<span data-ttu-id="46653-135">在這裡，我們會從相機鏡頭射出 2 公尺的光線到框架左上角的相機空間位置 1/4 處。</span><span class="sxs-lookup"><span data-stu-id="46653-135">Here we cast a 2-meter ray from the camera lens to the camera-space position ¼ from the top left of the frame.</span></span>  <span data-ttu-id="46653-136">然後，使用命中結果來呈現物件存在於世界空間中的某些內容：</span><span class="sxs-lookup"><span data-stu-id="46653-136">Then use the hit result to render something where the object exists in world space:</span></span>

![藍圖：從相機鏡頭射出 2 公尺的光線到框架左上角的相機空間位置 1/4 處](../images/unreal-pvc-img-12.png)

<span data-ttu-id="46653-138">使用空間對應時，此命中位置會符合相機所看到的表面。</span><span class="sxs-lookup"><span data-stu-id="46653-138">When using spatial mapping, this hit position will match the surface that the camera is seeing.</span></span>

## <a name="rendering-the-pv-camera-feed-in-c"></a><span data-ttu-id="46653-139">在 C++ 中呈現 PV 相機摘要</span><span class="sxs-lookup"><span data-stu-id="46653-139">Rendering the PV Camera Feed in C++</span></span>

- <span data-ttu-id="46653-140">建立名為 CamCapture 的新 C++ 動作項目</span><span class="sxs-lookup"><span data-stu-id="46653-140">Create a new C++ actor called CamCapture</span></span>
- <span data-ttu-id="46653-141">在專案的 build.cs 中，於 PublicDependencyModuleNames 清單中新增 “AugmentedReality”：</span><span class="sxs-lookup"><span data-stu-id="46653-141">In the project’s build.cs, add “AugmentedReality” to the PublicDependencyModuleNames list:</span></span>

```cpp
PublicDependencyModuleNames.AddRange(
    new string[] {
        "Core",
        "CoreUObject",
        "Engine",
        "InputCore",
        "AugmentedReality"
});
```

- <span data-ttu-id="46653-142">在 CamCapture.h 中，納入 ARBlueprintLibrary.h</span><span class="sxs-lookup"><span data-stu-id="46653-142">In CamCapture.h, include ARBlueprintLibrary.h</span></span>

```cpp
#include "ARBlueprintLibrary.h"
```

- <span data-ttu-id="46653-143">您也需要為網格和材質新增本機變數：</span><span class="sxs-lookup"><span data-stu-id="46653-143">You also need to add local variables for the mesh and material:</span></span>

```cpp
private:
    UStaticMesh* StaticMesh;
    UStaticMeshComponent* StaticMeshComponent;
    UMaterialInstanceDynamic* DynamicMaterial;
    bool IsTextureParamSet = false;
```

- <span data-ttu-id="46653-144">在 CamCapture.cpp 中，更新建構函式以將靜態網格新增至場景：</span><span class="sxs-lookup"><span data-stu-id="46653-144">In CamCapture.cpp, update the constructor to add a static mesh to the scene:</span></span>

```cpp
ACamCapture::ACamCapture()
{
    PrimaryActorTick.bCanEverTick = true;

    // Load a mesh from the engine to render the camera feed to.
    StaticMesh = LoadObject<UStaticMesh>(nullptr, TEXT("/Engine/EngineMeshes/Cube.Cube"), nullptr, LOAD_None, nullptr);

    // Create a static mesh component to render the static mesh
    StaticMeshComponent = CreateDefaultSubobject<UStaticMeshComponent>(TEXT("CameraPlane"));
    StaticMeshComponent->SetStaticMesh(StaticMesh);

    // Scale and add to the scene
    StaticMeshComponent->SetWorldScale3D(FVector(0.1f, 1, 1));
    this->SetRootComponent(StaticMeshComponent);
}
```

<span data-ttu-id="46653-145">在 BeginPlay 中，從專案的相機材質建立動態材質執行個體，將其套用至靜態網格元件，然後啟動 HoloLens 相機。</span><span class="sxs-lookup"><span data-stu-id="46653-145">In BeginPlay create a dynamic material instance from the project’s camera material, apply it to the static mesh component, and start the HoloLens camera.</span></span> 
 
<span data-ttu-id="46653-146">在編輯器中，以滑鼠右鍵按一下內容瀏覽器中的 CamTextureMaterial，然後選取 [複製參考] 以取得 CameraMatPath 的字串。</span><span class="sxs-lookup"><span data-stu-id="46653-146">In the editor, right-click on the CamTextureMaterial in the content browser and select “Copy Reference” to get the string for CameraMatPath.</span></span>

```cpp
void ACamCapture::BeginPlay()
{
    Super::BeginPlay();

    // Create a dynamic material instance from the game's camera material.
    // Right-click on a material in the project and select "Copy Reference" to get this string.
    FString CameraMatPath("Material'/Game/Materials/CamTextureMaterial.CamTextureMaterial'");
    UMaterial* BaseMaterial = (UMaterial*)StaticLoadObject(UMaterial::StaticClass(), nullptr, *CameraMatPath, nullptr, LOAD_None, nullptr);
    DynamicMaterial = UMaterialInstanceDynamic::Create(BaseMaterial, this);

    // Use the dynamic material instance when rendering the camera mesh.
    StaticMeshComponent->SetMaterial(0, DynamicMaterial);

    // Start the webcam.
    UARBlueprintLibrary::ToggleARCapture(true, EARCaptureType::Camera);
}
```

<span data-ttu-id="46653-147">在 [刻度] 中，從相機取得材質，將其設定為 CamTextureMaterial 材質中的材質參數，並根據相機框架的外觀比例調整靜態網格元件：</span><span class="sxs-lookup"><span data-stu-id="46653-147">In Tick get the texture from the camera, set it to the texture parameter in the CamTextureMaterial material, and scale the static mesh component by the camera frame’s aspect ratio:</span></span>

```cpp
void ACamCapture::Tick(float DeltaTime)
{
    Super::Tick(DeltaTime);

    // Dynamic material instance only needs to be set once.
    if(IsTextureParamSet)
    {
        return;
    }

    // Get the texture from the camera.
    UARTexture* ARTexture = UARBlueprintLibrary::GetARTexture(EARTextureType::CameraImage);
    if(ARTexture != nullptr)
    {
        // Set the shader's texture parameter (named "Param") to the camera image.
        DynamicMaterial->SetTextureParameterValue("Param", ARTexture);
        IsTextureParamSet = true;

        // Get the camera instrincs
        FARCameraIntrinsics Intrinsics;
        UARBlueprintLibrary::GetCameraIntrinsics(Intrinsics);

        // Scale the camera mesh by the aspect ratio.
        float R = (float)Intrinsics.ImageResolution.X / (float)Intrinsics.ImageResolution.Y;
        StaticMeshComponent->SetWorldScale3D(FVector(0.1f, R, 1));
    }
}
```

# <a name="425"></a>[<span data-ttu-id="46653-148">4.25</span><span class="sxs-lookup"><span data-stu-id="46653-148">4.25</span></span>](#tab/425)

## <a name="render-from-the-pv-camera-for-mrc"></a><span data-ttu-id="46653-149">從適用於 MRC 的 PV 相機呈現</span><span class="sxs-lookup"><span data-stu-id="46653-149">Render from the PV Camera for MRC</span></span>

> [!NOTE]
> <span data-ttu-id="46653-150">這需要 **Unreal Engine 4.25** 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="46653-150">This requires **Unreal Engine 4.25** or newer.</span></span>

<span data-ttu-id="46653-151">系統和自訂 MRC 錄製器，藉由結合 PV 相機與應用程式所呈現的全像投影，建立混合實境。</span><span class="sxs-lookup"><span data-stu-id="46653-151">The system and custom MRC recorders create mixed reality captures by combining the PV Camera with holograms rendered by the app.</span></span>

<span data-ttu-id="46653-152">根據預設，混合實境擷取會使用右眼的全像投影輸出。</span><span class="sxs-lookup"><span data-stu-id="46653-152">By default, mixed reality capture uses the right eye's holographic output.</span></span> <span data-ttu-id="46653-153">如果沉浸式應用程式選擇[從 PV 相機呈現](../../platform-capabilities-and-apis/mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in)，則會改用此功能。</span><span class="sxs-lookup"><span data-stu-id="46653-153">If an immersive app chooses to [render from the PV Camera](../../platform-capabilities-and-apis/mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in), then that will be used instead.</span></span> <span data-ttu-id="46653-154">從 PV 相機呈現可以改善實際世界與 MRC 影片中全像投影之間的對應。</span><span class="sxs-lookup"><span data-stu-id="46653-154">Rendering from the PV Camera improves the mapping between the real world and the holograms in the MRC video.</span></span>

<span data-ttu-id="46653-155">若要選擇從 PV 相機呈現：</span><span class="sxs-lookup"><span data-stu-id="46653-155">To opt in to rendering from the PV Camera:</span></span>

1. <span data-ttu-id="46653-156">呼叫 **SetEnabledMixedRealityCamera** 和 **ResizeMixedRealityCamera**</span><span class="sxs-lookup"><span data-stu-id="46653-156">Call **SetEnabledMixedRealityCamera** and **ResizeMixedRealityCamera**</span></span>
    * <span data-ttu-id="46653-157">使用 **Size X** 和 **Size Y** 值來設定影片大小。</span><span class="sxs-lookup"><span data-stu-id="46653-157">Use the **Size X** and **Size Y** values to set the video dimensions.</span></span>

![第三相機](../../platform-capabilities-and-apis/images/unreal-camera-3rd.PNG)

<span data-ttu-id="46653-159">然後，Unreal 會處理來自 MRC 的要求，以從 PV 相機的視角呈現。</span><span class="sxs-lookup"><span data-stu-id="46653-159">Unreal will then handle requests from MRC to render from the PV Camera's perspective.</span></span>

> [!NOTE]
> <span data-ttu-id="46653-160">只有在觸發了[混合實境擷取](/hololens/holographic-photos-and-videos)時，才會要求應用程式從相片/影片相機的視角呈現。</span><span class="sxs-lookup"><span data-stu-id="46653-160">Only when [Mixed Reality Capture](/hololens/holographic-photos-and-videos) is triggered will the app be asked to render from the photo/video camera's perspective.</span></span>

## <a name="using-the-pv-camera"></a><span data-ttu-id="46653-161">使用 PV 相機</span><span class="sxs-lookup"><span data-stu-id="46653-161">Using the PV Camera</span></span>

<span data-ttu-id="46653-162">網路攝影機紋理可以在執行階段於遊戲中擷取，但必須在編輯器的 [編輯] > [專案設定] 中啟用：</span><span class="sxs-lookup"><span data-stu-id="46653-162">The webcam texture can be retrieved in the game at runtime, but it needs to be enabled in the editor's **Edit > Project Settings**:</span></span>
1. <span data-ttu-id="46653-163">移至 [平台] > [HoloLens] > [功能]，並勾選 [網路攝影機]。</span><span class="sxs-lookup"><span data-stu-id="46653-163">Go to **Platforms > HoloLens > Capabilities** and check **Webcam**.</span></span>
    * <span data-ttu-id="46653-164">使用 **StartCameraCapture** 函式，以在執行階段使用網路攝影機，以及使用 **StopCameraCapture** 函式以停止錄製。</span><span class="sxs-lookup"><span data-stu-id="46653-164">Use the **StartCameraCapture** function to use the webcam at runtime and the **StopCameraCapture** function to stop recording.</span></span>

![相機啟動停止](../images/unreal-camera-startstop.PNG)

## <a name="rendering-an-image"></a><span data-ttu-id="46653-166">呈現影像</span><span class="sxs-lookup"><span data-stu-id="46653-166">Rendering an image</span></span>
<span data-ttu-id="46653-167">若要呈現相機影像：</span><span class="sxs-lookup"><span data-stu-id="46653-167">To render the camera image:</span></span>
1. <span data-ttu-id="46653-168">根據專案中的材質建立動態材質執行個體，在下列螢幕擷取畫面中將其稱為 **PVCamMat**。</span><span class="sxs-lookup"><span data-stu-id="46653-168">Create a dynamic material instance based on a material in the project, which is named **PVCamMat** in the screenshot below.</span></span>  
2. <span data-ttu-id="46653-169">將動態材質執行個體設定為 **材質執行個體動態物件參考** 變數。</span><span class="sxs-lookup"><span data-stu-id="46653-169">Set the dynamic material instance to a **Material Instance Dynamic Object Reference** variable.</span></span>  
3. <span data-ttu-id="46653-170">將場景中呈現相機摘要的物件材質設定為這個新的動態材質執行個體。</span><span class="sxs-lookup"><span data-stu-id="46653-170">Set the material of the object in the scene that will render the camera feed to this new dynamic material instance.</span></span>
    * <span data-ttu-id="46653-171">啟動用來將相機影像繫結至材質的計時器。</span><span class="sxs-lookup"><span data-stu-id="46653-171">Start a timer that will be used to bind the camera image to the material.</span></span>

![相機轉譯](../images/unreal-camera-render.PNG)

4. <span data-ttu-id="46653-173">建立此計時器的新函式 (在這個案例中為 **MaterialTimer**)，並且呼叫 **GetARCameraImage** 以從網路攝影機取得紋理。</span><span class="sxs-lookup"><span data-stu-id="46653-173">Create a new function for this timer, in this case **MaterialTimer**, and call **GetARCameraImage** to get the texture from the webcam.</span></span>  
5. <span data-ttu-id="46653-174">如果紋理有效，請將著色器中的紋理參數設定為影像。</span><span class="sxs-lookup"><span data-stu-id="46653-174">If the texture is valid, set a texture parameter in the shader to the image.</span></span>  <span data-ttu-id="46653-175">否則，請重新啟動材質計時器。</span><span class="sxs-lookup"><span data-stu-id="46653-175">Otherwise, start the material timer again.</span></span>

![網路攝影機的相機紋理](../images/unreal-camera-texture.PNG)

5. <span data-ttu-id="46653-177">確定材質有一個參數符合 **SetTextureParameterValue** 中繫結至色彩項目的名稱。</span><span class="sxs-lookup"><span data-stu-id="46653-177">Make sure the material has a parameter that matches the name in **SetTextureParameterValue** that's bound to a color entry.</span></span> <span data-ttu-id="46653-178">如果沒有參數，相機影像就無法正確顯示。</span><span class="sxs-lookup"><span data-stu-id="46653-178">Without the parameter, the camera image can't be displayed properly.</span></span>

![相機紋理](../images/unreal-camera-material.PNG)