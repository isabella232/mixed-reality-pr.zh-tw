---
title: DirectX 中的頭部和眼睛目光
description: 瞭解如何在原生 DirectX 應用程式中，要求、使用和解除封裝 raycasting 資料，從前端和眼睛追蹤。
author: caseymeekhof
ms.author: cmeekhof
ms.date: 08/04/2020
ms.topic: article
keywords: 眼睛、頭部眼、前端追蹤、眼睛追蹤、directx、輸入、全像投影、混合現實耳機、windows mixed reality 耳機、虛擬實境耳機
ms.openlocfilehash: a518e5e4153da9c58295abb257a8ed2d69145211
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009548"
---
# <a name="head-gaze-and-eye-gaze-input-in-directx"></a>DirectX 中的列印頭和眼睛輸入

> [!NOTE]
> 本文與舊版 WinRT 原生 Api 相關。  針對新的原生應用程式專案，建議使用 **[OPENXR API](openxr-getting-started.md)**。

在 Windows Mixed Reality 中，眼睛和前端的輸入是用來判斷使用者所查看的內容。 您可以使用資料來驅動主要的輸入模型（例如 [前端和認可](../../design/gaze-and-commit.md)），並提供不同互動類型的內容。 有兩種類型的注視向量可透過 API 取得：標眼和眼睛。  兩者都是以具有原點和方向的立體光線形式提供。 然後，應用程式可以 raycast 到其幕後或真實世界，判斷使用者的目標。

**前端看著** 表示使用者的標頭指向的方向。 將前端視為裝置本身的位置和轉寄方向，並將位置作為兩個顯示器之間的中心點。 所有混合現實裝置都可使用前端。

**眼睛** 表示使用者的眼睛朝的方向。 原點位於使用者的眼睛之間。  它可在包含眼睛追蹤系統的混合現實裝置上使用。

前端和眼睛光線都可透過  [SpatialPointerPose](https://docs.microsoft.com//uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) API 存取。 呼叫 [SpatialPointerPose：： TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) ，以在指定的時間戳記和 [座標系統](coordinate-systems-in-directx.md)接收新的 SpatialPointerPose 物件。 此 SpatialPointerPose 包含頭部的原點和方向。 如果有眼睛追蹤，它也會包含眼睛的原點和方向。

### <a name="device-support"></a>裝置支援

<table>
<colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
</colgroup>
<tr>
     <td><strong>功能</strong></td>
     <td><a href="../../hololens-hardware-details.md"><strong>HoloLens (第 1 代)</strong></a></td>
     <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
     <td><a href="../../discover/immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></td>
</tr>
<tr>
     <td>頭部注視</td>
     <td>✔️</td>
     <td>✔️</td>
     <td>✔️</td>
</tr>
<tr>
     <td>眼睛</td>
     <td>❌</td>
     <td>✔️</td>
     <td>❌</td>
</tr>
</table>

## <a name="using-head-gaze"></a>使用頭部

若要存取標頭，請從呼叫  [SpatialPointerPose：： TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) 開始，以接收新的 SpatialPointerPose 物件。 傳遞下列參數。
 - [SpatialCoordinateSystem](https://docs.microsoft.com//uwp/api/windows.perception.spatial.spatialcoordinatesystem) ，表示您想要用於頭部注視的座標系統。 這會以下列程式碼中的 *coordinateSystem* 變數表示。 如需詳細資訊，請造訪我們的 [座標系統](coordinate-systems-in-directx.md) 開發人員指南。
 - 表示所要求之 head 姿勢確切時間的 [時間戳記](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframeprediction.timestamp#Windows_Graphics_Holographic_HolographicFramePrediction_Timestamp) 。  一般而言，您會使用對應至目前畫面格顯示時間的時間戳記。 您可以從  [HolographicFramePrediction](https://docs.microsoft.com//uwp/api/Windows.Graphics.Holographic.HolographicFramePrediction) 物件（可透過目前的 [HolographicFrame](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframe)存取）取得這個預測的顯示時間戳記。  這個 HolographicFramePrediction 物件是由下列程式碼中的 *預測* 變數表示。

 當您有有效的 SpatialPointerPose 之後，就可以將標頭位置和轉寄方向作為屬性來存取。  下列程式碼顯示如何存取它們。

 ```cpp
using namespace winrt::Windows::UI::Input::Spatial;
using namespace winrt::Windows::Foundation::Numerics;

SpatialPointerPose pointerPose = SpatialPointerPose::TryGetAtTimestamp(coordinateSystem, prediction.Timestamp());
if (pointerPose)
{
    float3 headPosition = pointerPose.Head().Position();
    float3 headForwardDirection = pointerPose.Head().ForwardDirection();

    // Do something with the head-gaze
}
```

## <a name="using-eye-gaze"></a>使用眼睛

為了讓您的使用者使用眼睛輸入，每位使用者在第一次使用裝置時，都必須經過 [眼睛追蹤使用者校正](../../calibration.md) 。 眼睛類似的 API 類似于列印頭。
它會使用相同的 [SpatialPointerPose](https://docs.microsoft.com//uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) API，以提供您可以針對場景 raycast 的光線來源和方向。  唯一的差別是您必須先明確啟用眼睛追蹤，再加以使用：
1. 要求使用者在您的應用程式中使用眼睛追蹤的許可權。
2. 啟用套件資訊清單中的「注視輸入」功能。

### <a name="requesting-access-to-eye-gaze-input"></a>要求存取眼睛輸入

當您的應用程式啟動時，請呼叫 [EyesPose：： RequestAccessAsync](https://docs.microsoft.com//uwp/api/windows.perception.people.eyespose.requestaccessasync#Windows_Perception_People_EyesPose_RequestAccessAsync) 來要求存取眼睛追蹤。 系統會視需要提示使用者，並在授與存取權之後傳回 [GazeInputAccessStatus：：「允許](https://docs.microsoft.com//uwp/api/windows.ui.input.gazeinputaccessstatus) 」。 這是非同步呼叫，因此需要一些額外的管理。 下列範例會啟動卸離的 std：： thread 以等候結果，而該結果會儲存至名為 *m_isEyeTrackingEnabled* 的成員變數。

```cpp
using namespace winrt::Windows::Perception::People;
using namespace winrt::Windows::UI::Input;

std::thread requestAccessThread([this]()
{
    auto status = EyesPose::RequestAccessAsync().get();

    if (status == GazeInputAccessStatus::Allowed)
        m_isEyeTrackingEnabled = true;
    else
        m_isEyeTrackingEnabled = false;
});

requestAccessThread.detach();

```
啟動卸離的執行緒只是一個處理非同步呼叫的選項。 您也可以使用 c + + 所支援的新 [co_await](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/concurrency) 功能/winrt
以下是要求使用者權限的另一個範例：
-   EyesPose：： IsSupported ( # A1 可讓應用程式只有在有眼睛追蹤器時，才會觸發許可權對話方塊。
-   GazeInputAccessStatus m_gazeInputAccessStatus;這是為了防止再次彈出許可權提示。

```cpp
GazeInputAccessStatus m_gazeInputAccessStatus; // This is to prevent popping up the permission prompt over and over again.

// This will trigger to show the permission prompt to the user.
// Ask for access if there is a corresponding device and registry flag did not disable it.
if (Windows::Perception::People::EyesPose::IsSupported() &&
   (m_gazeInputAccessStatus == GazeInputAccessStatus::Unspecified))
{ 
    Concurrency::create_task(Windows::Perception::People::EyesPose::RequestAccessAsync()).then(
    [this](GazeInputAccessStatus status)
    {
        // GazeInputAccessStatus::{Allowed, DeniedBySystem, DeniedByUser, Unspecified}
            m_gazeInputAccessStatus = status;
        
        // Let's be sure to not ask again.
        if(status == GazeInputAccessStatus::Unspecified)
        {
                m_gazeInputAccessStatus = GazeInputAccessStatus::DeniedBySystem;    
        }
    });
}

```

### <a name="declaring-the-gaze-input-capability"></a>宣告 *注視輸入* 功能

按兩下 *方案總管* 中的 package.appxmanifest 檔案。  然後流覽至 [ *功能* ] 區段，並檢查 [ *注視輸入* ] 功能。 

![注視輸入功能](images/gaze-input-capability.png)

這會將下列幾行新增至 package.appxmanifest 檔案中的 *封裝* 區段：
```xml
  <Capabilities>
    <DeviceCapability Name="gazeInput" />
  </Capabilities>
```

### <a name="getting-the-eye-gaze-ray"></a>取得眼睛光線

當您取得 ET 的存取權之後，就可以自由抓取每個畫面的眼睛光線。
如同前端，請使用所需的時間戳記和座標系統來呼叫[SpatialPointerPose：： TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) ，以取得[SpatialPointerPose](https://docs.microsoft.com//uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) 。 SpatialPointerPose 包含透過[眼睛](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.eyes)屬性的[EyesPose](https://docs.microsoft.com//uwp/api/windows.perception.people.eyespose)物件。 只有在已啟用眼睛追蹤的情況下，此值才會是 null。 從該處，您可以藉由呼叫 [EyesPose：： IsCalibrationValid](https://docs.microsoft.com//uwp/api/windows.perception.people.eyespose.iscalibrationvalid#Windows_Perception_People_EyesPose_IsCalibrationValid)，檢查裝置中的使用者是否有眼睛追蹤校正。  接下來，使用 [眼睛屬性來](https://docs.microsoft.com//uwp/api/windows.perception.people.eyespose.gaze#Windows_Perception_People_EyesPose_Gaze) 取得包含眼睛的位置和方向的 [SpatialRay](https://docs.microsoft.com//uwp/api/windows.perception.spatial.spatialray) 。 注視屬性有時可以是 null，因此請務必檢查此值。 發生這種情況的原因是，已校正的使用者暫時關閉其眼睛。

下列程式碼顯示如何存取眼睛光線。

```cpp
using namespace winrt::Windows::UI::Input::Spatial;
using namespace winrt::Windows::Foundation::Numerics;

SpatialPointerPose pointerPose = SpatialPointerPose::TryGetAtTimestamp(coordinateSystem, prediction.Timestamp());
if (pointerPose)
{
    if (pointerPose.Eyes() && pointerPose.Eyes().IsCalibrationValid())
    {
        if (pointerPose.Eyes().Gaze())
        {
            auto spatialRay = pointerPose.Eyes().Gaze().Value();
            float3 eyeGazeOrigin = spatialRay.Origin;
            float3 eyeGazeDirection = spatialRay.Direction;
            
            // Do something with the eye-gaze
        }
    }
}

```

## <a name="fallback-when-eye-tracking-isnt-available"></a>當眼睛追蹤無法使用時回復

如同我們的 [眼睛追蹤設計](../../design/eye-tracking.md#fallback-solutions-when-eye-tracking-isnt-available)檔中所述，設計人員和開發人員都應該留意可能無法使用眼睛追蹤資料的情況。

資料無法使用的原因有很多種：
* 未進行校正的使用者
* 使用者已拒絕應用程式存取其眼睛追蹤資料
* 暫時干擾差異性，例如 HoloLens 面板上的塗抹，或遮蔽使用者眼睛的頭髮。 

雖然本檔中已提及部分 Api，但我們將在下列內容中提供一份摘要，說明如何偵測如何以快速參考的方式來使用眼睛追蹤： 

* 檢查系統是否支援眼睛追蹤。 呼叫下列 *方法*： [EyesPose. IsSupported ( # B1](https://docs.microsoft.com/uwp/api/windows.perception.people.eyespose.issupported#Windows_Perception_People_EyesPose_IsSupported)

* 檢查使用者是否已校正。 呼叫下列 *屬性*： [EyesPose. IsCalibrationValid](https://docs.microsoft.com/uwp/api/windows.perception.people.eyespose.iscalibrationvalid#Windows_Perception_People_EyesPose_IsCalibrationValid) 

* 確認使用者已為您的應用程式提供使用其眼睛追蹤資料的許可權：取出目前的 _' GazeInputAccessStatus '_。 有關如何進行這項操作的範例，請參閱 [要求存取注視輸入](https://docs.microsoft.com/windows/mixed-reality/gaze-in-directX#requesting-access-to-gaze-input)的說明。   

您也可能想要在收到的眼睛追蹤資料更新之間加上超時時間，以檢查您的眼睛追蹤資料是否已過時，如以下所述，則改回前端。   
如需詳細資訊，請流覽我們的回溯 [設計考慮](../../design/eye-tracking.md#fallback-solutions-when-eye-tracking-isnt-available) 。

<br>

## <a name="correlating-gaze-with-other-inputs"></a>將注視與其他輸入相互關聯

有時您可能會發現您需要的 [SpatialPointerPose](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose) 與過去的事件相對應。 例如，如果使用者進行了點擊，您的應用程式可能會想要知道他們正在查看的內容。 基於這個目的，只要將 [SpatialPointerPose：： TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) 與預測的框架時間搭配使用，就會因為系統輸入處理和顯示時間之間的延遲而不正確。 此外，如果針對目標使用眼睛，我們的眼睛通常會在完成認可動作之前繼續進行。 這對簡單的分流來說比較不成問題，但在結合長聲音命令與快速的移動時變得更重要。 處理此案例的其中一種方式是使用對應至輸入事件的歷程時間戳記，對  [SpatialPointerPose：： TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp)進行額外的呼叫。  

不過，針對透過 SpatialInteractionManager 進行路由的輸入，有更簡單的方法。 [SpatialInteractionSourceState](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate)有自己的[TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygetpointerpose)函數。 呼叫以提供完全相關的 [SpatialPointerPose](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose) ，而不需要猜測。 如需有關使用 SpatialInteractionSourceStates 的詳細資訊，請參閱 DirectX 檔 [中的手和移動控制器](hands-and-motion-controllers-in-directx.md) 。

<br>

## <a name="calibration"></a>校正

為了讓眼睛追蹤能準確地運作，每位使用者都必須經過 [眼睛追蹤使用者的校正](../../calibration.md)。 這可讓裝置為使用者調整系統，以獲得更舒適且更高品質的觀賞體驗，並同時確保一致的眼睛追蹤。 開發人員不需要在其端進行任何動作，即可管理使用者校正。 系統會在下列情況下，確定使用者會收到校正裝置的提示：
* 使用者第一次使用裝置
* 使用者先前退出宣告校正流程
* 上次使用者使用裝置時，校正程式未成功

開發人員應務必為可能無法使用眼睛追蹤資料的使用者提供適當的支援。 深入瞭解 [HoloLens 2 上的眼睛追蹤](../../design/eye-tracking.md)之回溯解決方案的考慮。

<br>

## <a name="see-also"></a>請參閱

* [校正](../../calibration.md)
* [DirectX 中的座標系統](coordinate-systems-in-directx.md)
* [HoloLens 2 上的眼睛](../../design/eye-tracking.md)
* [注視和認可輸入模型](../../design/gaze-and-commit.md)
* [DirectX 中的手部和運動控制器](hands-and-motion-controllers-in-directx.md)
* [DirectX 中的語音輸入](voice-input-in-directx.md)
