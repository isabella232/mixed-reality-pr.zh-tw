---
ms.openlocfilehash: 53d22260603c4e52096eccf1d7af6a3b0732124e
ms.sourcegitcommit: 672a7a145cfc656273af4ea34f99583eb9fa849c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/14/2021
ms.locfileid: "98225273"
---
# <a name="426"></a>[4.26](#tab/426) 

## <a name="pv-camera-feed-setup"></a>PV 相機摘要設定

> [!IMPORTANT]
> PV 相機會同時在 Windows Mixed Reality 和 OpenXR 外掛程式中實作。 不過，OpenXR 需要安裝 [Microsoft OpenXR 外掛程式](https://github.com/microsoft/Microsoft-OpenXR-Unreal)。 此外，OpenXR 目前有所限制，相機可以搭配 DirectX11 RHI 運作。 在更高的 Unreal 版本中將會修正這項限制。 

- 在 [專案設定] > [HoloLens] 中，啟用 [網路攝影機] 功能：

![已醒目提示 [網路攝影機] 屬性的 HoloLens 專案設定螢幕擷取畫面](../images/unreal-pvc-img-01.png)

- 建立名為 "CamCapture" 的新動作項目，並新增平面來呈現相機摘要：

![螢幕擷取畫面：已新增平面的動作項目](../images/unreal-pvc-img-02.png)

- 將動作項目新增至您的場景，建立具有「材質物件參數」且名為 CamTextureMaterial 的新材質，以及材質範例。  將材質的 rgb 資料傳送至輸出放射色彩：

![藍圖：材質和材質範例](../images/unreal-pvc-img-03.png)

## <a name="rendering-the-pv-camera-feed"></a>呈現 PV 相機摘要

- 在 CamCapture 藍圖中，開啟「PV 相機」：

![藍圖：已開啟 PV 相機的「切換 ARCapture」函式](../images/unreal-pvc-img-04.png)

- 從 CamTextureMaterial 建立動態材質執行個體，並將此材質指派給動作項目的平面：

![藍圖：建立動態材質執行個體函式](../images/unreal-pvc-img-05.png)

- 從相機摘要取得材質，並將其指派給動態材質 (如果此材質有效的話)。  如果此材質無效，請啟動計時器，並在逾時後再試一次：

![藍圖：指派給動態材質的相機摘要材質](../images/unreal-pvc-img-06.png)

- 最後，依據相機影像的外觀比例來調整平面：

![藍圖：相對於相機影像外觀比例來調整的平面](../images/unreal-pvc-img-07.png)

## <a name="find-camera-positions-in-world-space"></a>尋找世界空間中的相機位置

HoloLens 2 上的相機會與裝置的頭部追蹤垂直偏移。  有幾個函式可用來定位世界空間中的相機，以因應此情況。

GetPVCameraToWorldTransform 會取得 PV 相機世界空間中的轉換，並將其定位在相機鏡頭上：

![藍圖：取得 PVCamera 對世界轉換函式](../images/unreal-pvc-img-08.png)

GetWorldSpaceRayFromCameraPoint 會從相機鏡頭射出光線到 Unreal 世界空間中的場景，以找出相機框架中特定像素的內容：

![藍圖：取得從相機位置點射出的世界空間光線](../images/unreal-pvc-img-09.png)

GetPVCameraIntrinsics 會傳回相機內建值，這可在對相機框架進行電腦視覺處理時用到：

![藍圖：取得 PVCamera 內建函式](../images/unreal-pvc-img-10.png)

若要找出世界空間內的特定像素座標上有何項目，請搭配使用光線追蹤與世界空間光線：

![藍圖：世界空間光線，用來找出世界空間內的特定座標上有何項目](../images/unreal-pvc-img-11.png)

在這裡，我們會從相機鏡頭射出 2 公尺的光線到框架左上角的相機空間位置 1/4 處。  然後，使用命中結果來呈現物件存在於世界空間中的某些內容：

![藍圖：從相機鏡頭射出 2 公尺的光線到框架左上角的相機空間位置 1/4 處](../images/unreal-pvc-img-12.png)

使用空間對應時，此命中位置會符合相機所看到的表面。

## <a name="rendering-the-pv-camera-feed-in-c"></a>在 C++ 中呈現 PV 相機摘要

- 建立名為 CamCapture 的新 C++ 動作項目
- 在專案的 build.cs 中，於 PublicDependencyModuleNames 清單中新增 “AugmentedReality”：

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

- 在 CamCapture.h 中，納入 ARBlueprintLibrary.h

```cpp
#include "ARBlueprintLibrary.h"
```

- 您也需要為網格和材質新增本機變數：

```cpp
private:
    UStaticMesh* StaticMesh;
    UStaticMeshComponent* StaticMeshComponent;
    UMaterialInstanceDynamic* DynamicMaterial;
    bool IsTextureParamSet = false;
```

- 在 CamCapture.cpp 中，更新建構函式以將靜態網格新增至場景：

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

在 BeginPlay 中，從專案的相機材質建立動態材質執行個體，將其套用至靜態網格元件，然後啟動 HoloLens 相機。 
 
在編輯器中，以滑鼠右鍵按一下內容瀏覽器中的 CamTextureMaterial，然後選取 [複製參考] 以取得 CameraMatPath 的字串。

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

在 [刻度] 中，從相機取得材質，將其設定為 CamTextureMaterial 材質中的材質參數，並根據相機框架的外觀比例調整靜態網格元件：

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

# <a name="425"></a>[4.25](#tab/425)

## <a name="render-from-the-pv-camera-for-mrc"></a>從適用於 MRC 的 PV 相機呈現

> [!NOTE]
> 這需要 **Unreal Engine 4.25** 或更新版本。

系統和自訂 MRC 錄製器，藉由結合 PV 相機與應用程式所呈現的全像投影，建立混合實境。

根據預設，混合實境擷取會使用右眼的全像投影輸出。 如果沉浸式應用程式選擇[從 PV 相機呈現](../../platform-capabilities-and-apis/mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in)，則會改用此功能。 從 PV 相機呈現可以改善實際世界與 MRC 影片中全像投影之間的對應。

若要選擇從 PV 相機呈現：

1. 呼叫 **SetEnabledMixedRealityCamera** 和 **ResizeMixedRealityCamera**
    * 使用 **Size X** 和 **Size Y** 值來設定影片大小。

![第三相機](../../platform-capabilities-and-apis/images/unreal-camera-3rd.PNG)

然後，Unreal 會處理來自 MRC 的要求，以從 PV 相機的視角呈現。

> [!NOTE]
> 只有在觸發了[混合實境擷取](../../../mixed-reality-capture.md)時，才會要求應用程式從相片/影片相機的視角呈現。

## <a name="using-the-pv-camera"></a>使用 PV 相機

網路攝影機紋理可以在執行階段於遊戲中擷取，但必須在編輯器的 [編輯] > [專案設定] 中啟用：
1. 移至 [平台] > [HoloLens] > [功能]，並勾選 [網路攝影機]。
    * 使用 **StartCameraCapture** 函式，以在執行階段使用網路攝影機，以及使用 **StopCameraCapture** 函式以停止錄製。

![相機啟動停止](../images/unreal-camera-startstop.PNG)

## <a name="rendering-an-image"></a>呈現影像
若要呈現相機影像：
1. 根據專案中的材質建立動態材質執行個體，在下列螢幕擷取畫面中將其稱為 **PVCamMat**。  
2. 將動態材質執行個體設定為 **材質執行個體動態物件參考** 變數。  
3. 將場景中呈現相機摘要的物件材質設定為這個新的動態材質執行個體。
    * 啟動用來將相機影像繫結至材質的計時器。

![相機轉譯](../images/unreal-camera-render.PNG)

4. 建立此計時器的新函式 (在這個案例中為 **MaterialTimer**)，並且呼叫 **GetARCameraImage** 以從網路攝影機取得紋理。  
5. 如果紋理有效，請將著色器中的紋理參數設定為影像。  否則，請重新啟動材質計時器。

![網路攝影機的相機紋理](../images/unreal-camera-texture.PNG)

5. 確定材質有一個參數符合 **SetTextureParameterValue** 中繫結至色彩項目的名稱。 如果沒有參數，相機影像就無法正確顯示。

![相機紋理](../images/unreal-camera-material.PNG)

