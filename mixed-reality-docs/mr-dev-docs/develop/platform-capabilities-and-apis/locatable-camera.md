---
title: 定位相機
description: 有關 HoloLens 正面攝影機、其運作方式，以及可供開發人員使用的設定檔和解決方案的一般資訊。
author: cdedmonds
ms.author: wguyman
ms.date: 06/12/2019
ms.topic: article
keywords: 攝影機、hololens、彩色攝影機、正面、hololens 2、cv、電腦視覺、基準、標記、qr 代碼、qr、相片、影片
ms.openlocfilehash: 33faa4107c6b44041958f422329d8967958a666606a474949184628abcd12544
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2021
ms.locfileid: "115217094"
---
# <a name="locatable-camera"></a>定位相機

HoloLens 包含掛接在裝置前方的全球面向相機，可讓應用程式查看使用者看到的內容。 開發人員可以存取和控制攝影機，就像在 smartphone、筆記本電腦或桌上型電腦上的彩色攝影機一樣。 適用于行動裝置和桌上型電腦的相同通用 windows [media capture](/uwp/api/Windows.Media.Capture.MediaCapture)和 windows Media foundation api 可在 HoloLens 上運作。 Unity[已包裝這些 Windows api](../unity/locatable-camera-in-unity.md) ，以 HoloLens 上的相機使用功能。 功能工作包括將一般相片和影片 (與或不含全像投影) ，以及在場景中找出相機的位置和觀點。

## <a name="device-camera-information"></a>裝置相機資訊

### <a name="hololens-first-generation"></a>HoloLens (第一代) 

* 已修正焦點相片/影片 (PV) 攝影機與自動白平衡、自動曝光和完整的影像處理管線。
* 當相機處於作用中狀態時，世界上的白色隱私權 LED 將會發亮
* 攝影機支援下列模式 (所有模式都是16:9 的外觀比例) 30、24、20、15和 5 fps：

  |  影片  |  預覽  |  還  |  水準視圖 (H-FOV)  |  建議用法 | 
  |----------|----------|----------|----------|----------|
  |  1280x720 |  1280x720 |  1280x720 |  45度  |  使用影片穩定)  (預設模式 | 
  |  N/A |  N/A |  2048x1152 |  67度 |  最高解析度仍為影像 | 
  |  1408x792 |  1408x792 |  1408x792 |  48度 |  Overscan (填補影片穩定之前的) 解析度 | 
  |  1344x756 |  1344x756 |  1344x756 |  67度 |  使用 overscan 的大型 FOV 影片模式 | 
  |  896x504 |  896x504 |  896x504 |  48度 |  影像處理工作的低電源/低解析度模式 | 

### <a name="hololens-2"></a>HoloLens 2

* 自動聚焦相片/影片 (PV) 攝影機（具有自動白平衡、自動曝光和完整的影像處理管線）。
* 當相機處於作用中狀態時，就會導致世界各地的白色隱私權燈亮著。
* HoloLens 2 支援不同的相機設定檔。 瞭解如何 [探索並選取攝影機功能](/windows/uwp/audio-video-camera/camera-profiles)。
* 攝影機支援下列設定檔和解析度 (所有的影片模式都是16:9 的外觀比例) ：
  
  | 設定檔                                         | 影片     | 預覽   | 還     | 畫面播放速率 | 水準視圖 (H-FOV)  | 建議用法                             |
  |-------------------------------------------------|-----------|-----------|-----------|-------------|----------------------------------|---------------------------------------------|
  | 舊版、0 BalancedVideoAndPhoto、100             | 2272x1278 | 2272x1278 |           | 15.30       | 64.69                            | 高品質的影片錄製                |
  | 舊版、0 BalancedVideoAndPhoto、100             | 896x504   | 896x504   |           | 15.30       | 64.69                            | 適用于高品質相片捕捉的預覽串流 |
  | 舊版、0 BalancedVideoAndPhoto、100             |           |           | 3904x2196 |             | 64.69                            | 高品質的相片捕捉                  |
  | BalancedVideoAndPhoto，120                       | 1952x1100 | 1952x1100 | 1952x1100 | 15.30       | 64.69                            | 長時間案例                     |
  | BalancedVideoAndPhoto，120                       | 1504x846  | 1504x846  |           | 15.30       | 64.69                            | 長時間案例                     |
  | 視訊會議，100                           | 1952x1100 | 1952x1100 | 1952x1100 | 15、30、60    | 64.69                            | 視訊會議，長時間案例 |
  | 視訊會議，100                           | 1504x846  | 1504x846  |           | 5、15、30、60  | 64.69                            | 視訊會議，長時間案例 |
  | 視訊會議，100 BalancedVideoAndPhoto，120 | 1920x1080 | 1920x1080 | 1920x1080 | 15、30       | 64.69                            | 視訊會議，長時間案例 |
  | 視訊會議，100 BalancedVideoAndPhoto，120 | 1280x720  | 1280x720  | 1280x720  | 15、30       | 64.69                            | 視訊會議，長時間案例 |
  | 視訊會議，100 BalancedVideoAndPhoto，120 | 1128x636  |           |           | 15、30       | 64.69                            | 視訊會議，長時間案例 |
  | 視訊會議，100 BalancedVideoAndPhoto，120 | 960x540   |           |           | 15、30       | 64.69                            | 視訊會議，長時間案例 |
  | 視訊會議，100 BalancedVideoAndPhoto，120 | 760x428   |           |           | 15、30       | 64.69                            | 視訊會議，長時間案例 |
  | 視訊會議，100 BalancedVideoAndPhoto，120 | 640x360   |           |           | 15、30       | 64.69                            | 視訊會議，長時間案例 |
  | 視訊會議，100 BalancedVideoAndPhoto，120 | 500x282   |           |           | 15、30       | 64.69                            | 視訊會議，長時間案例 |
  | 視訊會議，100 BalancedVideoAndPhoto，120 | 424x240   |           |           | 15、30       | 64.69                            | 視訊會議，長時間案例 |

> [!NOTE]
> 客戶可以利用 [混合的現實 capture](/hololens/holographic-photos-and-videos) 來拍攝您應用程式的影片或相片，包括全像全像觀賞和影片穩定。
>
>開發人員在建立應用程式時，如果您想要在客戶捕獲內容時盡可能地查看，則有一些考慮需要考慮。 您也可以直接在應用程式內啟用 (和自訂) mixed reality capture。 深入瞭解 [適用于開發人員的混合現實開發](mixed-reality-capture-for-developers.md)。

## <a name="locating-the-device-camera-in-the-world"></a>找出世界中的裝置攝影機

當 HoloLens 拍攝相片和影片時，所捕捉的框架會包含相機在世界的位置，以及相機的鏡頭模型。 這可讓應用程式在真實世界中的相機位置，以增強影像案例。 開發人員可以使用其最愛的影像處理或自訂電腦視覺程式庫，以創造性的來變換自己的案例。

HoloLens 檔中其他位置的「相機」可能參考「虛擬遊戲攝影機」 (應用程式轉譯成) 的錐。 除非另有指示，否則這個頁面上的「相機」是指真實的 RGB 色攝影機。

### <a name="using-unity"></a>使用 Unity

若要從「CameraIntrinsics」和「CameraCoordinateSystem」移至您的應用程式/全局座標系統，請依照 [Unity 文章中](../unity/locatable-camera-in-unity.md) 的可定位相機中的指示進行。  CameraToWorldMatrix 是由 PhotoCaptureFrame 類別自動提供，因此您不需要擔心下面討論的 CameraCoordinateSystem 轉換。

### <a name="using-mediaframereference"></a>使用 MediaFrameReference

如果 you'r 使用 [MediaFrameReference](/uwp/api/windows.media.capture.frames.mediaframereference) 類別從相機讀取影像畫面格，則適用這些指示。

每個影像框架都會 (相片或影片) 是否包含在拍攝時根目錄于相機的[SpatialCoordinateSystem](/uwp/api/windows.perception.spatial.spatialcoordinatesystem) ，可使用[MediaFrameReference](/uwp/api/Windows.Media.Capture.Frames.MediaFrameReference)的[CoordinateSystem](/uwp/api/windows.media.capture.frames.mediaframereference.coordinatesystem#Windows_Media_Capture_Frames_MediaFrameReference_CoordinateSystem)屬性來存取。 每個畫面格都包含相機鏡頭模型的描述，可在 [CameraIntrinsics](/uwp/api/windows.media.capture.frames.videomediaframe.cameraintrinsics#Windows_Media_Capture_Frames_VideoMediaFrame_CameraIntrinsics) 屬性中找到。 這些轉換會一起定義3D 空間中每個圖元的光線，代表產生圖元的光子所採用的路徑。 這些光線可以與應用程式中的其他內容相關，方法是從框架的座標系統取得轉換到其他的座標系統 (例如從 [固定的參考框架](../../design/coordinate-systems.md#stationary-frame-of-reference)) 。 

每個影像框架都會提供下列各項：
* 以 RGB/NV12/JPEG/etc 格式) 的圖元資料 (
* 從 capture 的位置[SpatialCoordinateSystem](/uwp/api/windows.perception.spatial.spatialcoordinatesystem)
* 包含相機鏡頭模式的 [CameraIntrinsics](/uwp/api/windows.media.capture.frames.videomediaframe.cameraintrinsics#Windows_Media_Capture_Frames_VideoMediaFrame_CameraIntrinsics) 類別

[HolographicFaceTracking 範例會示範](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicFaceTracking)在相機座標系統和您自己的應用程式座標系統之間，查詢轉換的方式相當直接。

### <a name="using-media-foundation"></a>使用媒體基礎

如果您直接使用媒體基礎從相機讀取影像畫面格，您可以使用每個畫面格的 [MFSampleExtension_CameraExtrinsics 屬性](/windows/win32/medfound/mfsampleextension-cameraextrinsics) 和 [MFSampleExtension_PinholeCameraIntrinsics 屬性](/windows/win32/medfound/mfsampleextension-pinholecameraintrinsics) 來找出相對於應用程式其他座標系統的相機畫面格，如下列範例程式碼所示：

```cpp
#include <winrt/windows.perception.spatial.preview.h>
#include <mfapi.h>
#include <mfidl.h>
 
using namespace winrt::Windows::Foundation;
using namespace winrt::Windows::Foundation::Numerics;
using namespace winrt::Windows::Perception;
using namespace winrt::Windows::Perception::Spatial;
using namespace winrt::Windows::Perception::Spatial::Preview;
 
class CameraFrameLocator
{
public:
    struct CameraFrameLocation
    {
        SpatialCoordinateSystem CoordinateSystem;
        float4x4 CameraViewToCoordinateSytemTransform;
        MFPinholeCameraIntrinsics Intrinsics;
    };
 
    std::optional<CameraFrameLocation> TryLocateCameraFrame(IMFSample* pSample)
    {
        MFCameraExtrinsics cameraExtrinsics;
        MFPinholeCameraIntrinsics cameraIntrinsics;
        UINT32 sizeCameraExtrinsics = 0;
        UINT32 sizeCameraIntrinsics = 0;
        UINT64 sampleTimeHns = 0;
 
        // query sample for calibration and validate
        if (FAILED(pSample->GetUINT64(MFSampleExtension_DeviceTimestamp, &sampleTimeHns)) ||
            FAILED(pSample->GetBlob(MFSampleExtension_CameraExtrinsics, (UINT8*)& cameraExtrinsics, sizeof(cameraExtrinsics), &sizeCameraExtrinsics)) ||
            FAILED(pSample->GetBlob(MFSampleExtension_PinholeCameraIntrinsics, (UINT8*)& cameraIntrinsics, sizeof(cameraIntrinsics), &sizeCameraIntrinsics)) ||
            (sizeCameraExtrinsics != sizeof(cameraExtrinsics)) ||
            (sizeCameraIntrinsics != sizeof(cameraIntrinsics)) ||
            (cameraExtrinsics.TransformCount == 0))
        {
            return std::nullopt;
        }
 
        // compute extrinsic transform
        const auto& calibratedTransform = cameraExtrinsics.CalibratedTransforms[0];
        const GUID& dynamicNodeId = calibratedTransform.CalibrationId;
        const float4x4 cameraToDynamicNode =
            make_float4x4_from_quaternion(quaternion{ calibratedTransform.Orientation.x, calibratedTransform.Orientation.y, calibratedTransform.Orientation.z, calibratedTransform.Orientation.w }) *
            make_float4x4_translation(calibratedTransform.Position.x, calibratedTransform.Position.y, calibratedTransform.Position.z);
 
        // update locator cache for dynamic node
        if (dynamicNodeId != m_currentDynamicNodeId || !m_locator)
        {
            m_locator = SpatialGraphInteropPreview::CreateLocatorForNode(dynamicNodeId);
            if (!m_locator)
            {
                return std::nullopt;
            }
 
            m_frameOfReference = m_locator.CreateAttachedFrameOfReferenceAtCurrentHeading();
            m_currentDynamicNodeId = dynamicNodeId;
        }
 
        // locate dynamic node
        auto timestamp = PerceptionTimestampHelper::FromSystemRelativeTargetTime(TimeSpan{ sampleTimeHns });
        auto coordinateSystem = m_frameOfReference.GetStationaryCoordinateSystemAtTimestamp(timestamp);
        auto location = m_locator.TryLocateAtTimestamp(timestamp, coordinateSystem);
        if (!location)
        {
            return std::nullopt;
        }
 
        const float4x4 dynamicNodeToCoordinateSystem = make_float4x4_from_quaternion(location.Orientation()) * make_float4x4_translation(location.Position());
 
        return CameraFrameLocation{ coordinateSystem, cameraToDynamicNode * dynamicNodeToCoordinateSystem, cameraIntrinsics };
    }

private:
    GUID m_currentDynamicNodeId{ GUID_NULL };
    SpatialLocator m_locator{ nullptr };
    SpatialLocatorAttachedFrameOfReference m_frameOfReference{ nullptr };
};
```

### <a name="distortion-error"></a>扭曲錯誤

在 HoloLens 上，影片和靜止影像資料流程會在系統的影像處理管線中 undistorted，然後才會將框架提供給應用程式 (預覽資料流程包含) 的原始失真畫面。 由於只有 CameraIntrinsics 可供使用，因此應用程式必須假設圖像框架代表完美的 pinhole 攝影機。

在 HoloLens (第一代) 上，在框架中繼資料中使用 CameraIntrinsics 時，映射處理器中的 undistortion 函式可能仍會保留最多10圖元的錯誤。 在許多使用案例中，此錯誤並不重要，但如果您要將影像對齊真實的海報/標記，而您注意到 <的10圖元位移 (大約是 11 mm 的空間，代表2計量離開) ，則可能造成失真錯誤。 

## <a name="locatable-camera-usage-scenarios"></a>的相機使用案例

### <a name="show-a-photo-or-video-in-the-world-where-it-was-captured"></a>顯示在世界中的拍攝相片或影片

裝置相機框架隨附「相機到世界」轉換，可用來顯示裝置在拍攝影像時的確切位置。 例如，您可以將小型的全像攝影圖示放置在此位置， (CameraToWorld MultiplyPoint (Vector3) ) ，甚至在相機面對的方向繪製一個小箭號 (CameraToWorld. MultiplyVector (Vector3. 轉寄) ) 。

### <a name="tag--pattern--poster--object-tracking"></a>標記/模式/海報/物件追蹤

許多混合現實應用程式都使用可辨識的影像或視覺模式來建立空間中的可追蹤點。 然後，這會用來呈現相對於該點的物件，或建立已知位置。 HoloLens 的某些用途包括尋找以 fiducials 標記的真實世界物件 (例如，具有 QR 代碼) 的電視監視器、將 fiducials 放在，以及以視覺化方式與非 HoloLens 裝置（例如已設定為透過 wi-fi 與 HoloLens 進行通訊的平板電腦）。

您需要一些東西來辨識視覺效果模式，並將物件放在應用程式世界空間中：
1. 影像模式辨識工具組，例如 QR 代碼、AR 標記、臉部搜尋工具、圓形追蹤器、OCR 等等。
2. 在執行時間收集影像畫面格，並將其傳遞至辨識層
3. 將其影像位置 Unproject 回世界位置，或可能是世界光線。 
4. 將您的虛擬模型放在這些世界位置

一些重要的影像處理連結：
* [OpenCV](https://opencv.org/)
* [QR 標記](https://en.wikipedia.org/wiki/QR_code)
* [FaceSDK](https://research.microsoft.com/projects/facesdk/)
* [Microsoft Translator](https://www.microsoft.com/translator/business)

保持互動式應用程式框架速率很重要，特別是在處理長時間執行的影像辨識演算法時。 基於這個理由，我們通常會使用下列模式：
1. 主要執行緒：管理相機物件
2. 主要執行緒：要求新的框架 (async) 
3. 主執行緒：傳遞新的框架至追蹤執行緒
4. 追蹤執行緒：進程映射以收集關鍵點
5. 主要執行緒：移動虛擬模型以符合找到的重點
6. 主執行緒：重複步驟2

某些影像標記系統只會提供單一圖元位置 (其他人會提供完整的轉換，在此情況下不需要此區段) ，這相當於可能的位置。 若要取得單一3d 位置，我們可以利用多個光線，並依其近似交集找出最終結果。 若要這樣做，您需要執行下列動作：
1. 取得迴圈來收集多個相機影像
2. 尋找相關聯的功能點及其世界光線
3. 當您有功能的字典，而且每個都有多個世界光線時，您可以使用下列程式碼來解決這些光線的交集：

```
public static Vector3 ClosestPointBetweenRays(
   Vector3 point1, Vector3 normalizedDirection1,
   Vector3 point2, Vector3 normalizedDirection2) {
   float directionProjection = Vector3.Dot(normalizedDirection1, normalizedDirection2);
   if (directionProjection == 1) {
     return point1; // parallel lines
   }
   float projection1 = Vector3.Dot(point2 - point1, normalizedDirection1);
   float projection2 = Vector3.Dot(point2 - point1, normalizedDirection2);
   float distanceAlongLine1 = (projection1 - directionProjection * projection2) / (1 - directionProjection * directionProjection);
   float distanceAlongLine2 = (projection2 - directionProjection * projection1) / (directionProjection * directionProjection - 1);
   Vector3 pointOnLine1 = point1 + distanceAlongLine1 * normalizedDirection1;
   Vector3 pointOnLine2 = point2 + distanceAlongLine2 * normalizedDirection2;
   return Vector3.Lerp(pointOnLine2, pointOnLine1, 0.5f);
 }
```

如果有兩個或多個追蹤的標記位置，您可以將模型化的場景定位至符合使用者目前的案例。 如果您無法採用重力，則需要三個標記位置。 在許多情況下，我們會使用色彩配置，其中白色球體代表即時追蹤標記位置，而藍色球體表示模型化標記位置。 這可讓使用者以視覺化方式測量對齊品質。 我們假設所有的應用程式都有下列設定：
* 兩個或多個模型化標記位置
* 一個「校正空間」，在場景中是標記的父系
* 相機功能識別碼
* 行為，這會移動校正空間來對齊模型標記與即時標籤 (我們很小心地移動上層空間，而不是模型標記本身，因為其他連接是相對於其) 的位置。

```
// In the two tags case:
 Vector3 idealDelta = (realTags[1].EstimatedWorldPos - realTags[0].EstimatedWorldPos);
 Vector3 curDelta = (modelledTags[1].transform.position - modelledTags[0].transform.position);
 if (IsAssumeGravity) {
   idealDelta.y = 0;
   curDelta.y = 0;
 }
 Quaternion deltaRot = Quaternion.FromToRotation(curDelta, idealDelta);
 trans.rotation = Quaternion.LookRotation(deltaRot * trans.forward, trans.up);
 trans.position += realTags[0].EstimatedWorldPos - modelledTags[0].transform.position;
```

### <a name="track-or-identify-tagged-stationary-or-moving-real-world-objectsfaces-using-leds-or-other-recognizer-libraries"></a>使用 Led 或其他辨識器程式庫追蹤或識別已標記的固定或移動真實世界的物件/臉部

範例：
* 具有 Led (的產業機器人，或較慢移動物件的 QR 代碼) 
* 識別和辨識房間中的物件
* 識別和辨識房間中的人員，例如，將全像攝影的連絡人卡片放在臉部上

## <a name="see-also"></a>另請參閱
* [已定位相機範例](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicFaceTracking)
* [Unity 中的定位相機](../unity/locatable-camera-in-unity.md)
* [混合實境擷取](/hololens/holographic-photos-and-videos)
* [適用於開發人員的混合實境擷取](mixed-reality-capture-for-developers.md)
* [Media capture 簡介](/windows/uwp/audio-video-camera/)
* [全像臉部追蹤範例](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicFaceTracking)