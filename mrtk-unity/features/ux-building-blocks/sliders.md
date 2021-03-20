---
title: 滑桿
description: 滑杆 MRTK 簡介
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、滑杆、
ms.openlocfilehash: d0ef491c25383e3a192c3e76d6d4ae38ffa075ce
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104689101"
---
# <a name="sliders"></a>滑桿

![滑杆範例](../images/slider/MRTK_UX_Slider_Main.jpg)

滑杆是 UI 元件，可讓您藉由移動軌跡上的滑杆來持續變更值。目前，您可以直接或距離，直接抓取滑杆來移動縮小滑杆。 滑杆適用于 AR 和 VR，使用動作控制器、手或手勢 + 語音。

## <a name="example-scene"></a>範例場景

您可以在的 **SliderExample** 場景中找到範例 `MRTK/Examples/Demos/UX/Slider/Scenes/` 。

## <a name="how-to-use-sliders"></a>如何使用滑杆

將 **PinchSlider** 預製專案拖放到場景階層中。 如果您想要修改或建立自己的滑杆，請務必執行下列動作：

- 請確定您的 thumb 物件有其碰撞器。 在 PinchSlider 預製專案中，碰撞器已開啟 `SliderThumb/Button_AnimationContainer/Slider_Button`
- 如果您想要能夠抓取靠近的滑杆，請確定包含碰撞器的物件也有近乎互動的 Grabbable 元件。

我們也建議使用下列階層

- PinchSlider-包含 sliderComponent
  - SliderThumb-包含可移動的拇指
  - TrackVisuals-包含曲目和任何其他視覺效果
  - OtherVisuals-包含任何其他視覺效果

## <a name="slider-events"></a>滑杆事件

滑杆會公開下列事件：

- OnValueUpdated-每當滑杆值變更時呼叫
- OnInteractionStarted-當使用者抓取滑杆時呼叫
- OnInteractionEnded-當使用者放開滑杆時呼叫
- OnHoverEntered-當使用者的手形/控制器停留在滑杆上時，使用接近或遠的互動來呼叫。
- OnHoverExited-當使用者的手形/控制器不再靠近滑杆時呼叫。

## <a name="configuring-slider-bound-and-axis"></a>設定滑杆系結和軸

您可以藉由移動場景中的控點，直接移動滑杆的起點和終點：

![滑杆設定](../images/sliders/MRTK_Sliders_Setup.png)

您也可以透過 _滑杆軸_ 欄位，在滑杆的 [本機空間]) 中指定軸 (

如果您無法使用控制碼，您可以改為透過 [ _滑杆開始距離_ ] 和 [ _滑杆結束距離_ ] 欄位來指定滑杆的起點和終點。 這些會將滑杆的開始/結束位置指定為距離滑杆中心的距離（以區域座標表示）。 這表示一旦您依需要設定滑杆的開始和結束距離，您可以將滑杆調整為較小或更大，而不需要更新開始和結束距離。

## <a name="inspector-properties"></a>偵測器屬性

**Thumb 根目錄** 包含滑杆 thumb 的 gameobject。

**滑杆值** 滑杆的值。

**追蹤視覺效果** Gameobject，其中包含沿著滑杆的所需追蹤視覺效果。

**刻度標記** Gameobject，其中包含沿著滑杆的所需刻度標記。

**Thumb 視覺效果** Gameobject，其中包含沿著滑杆的所需 thumb 視覺效果。

**滑杆軸** 滑杆沿著的軸移動。

**滑杆開始距離** 滑杆播放軌的起點，以當地空間單位為中心沿著滑杆軸的距離。

**滑杆結束距離** 滑杆軌結束的位置，以當地空間單位為中心沿著滑杆軸的距離。

當使用者更新編輯器中的滑杆軸值時，如果指定了追蹤視覺效果或刻度視覺效果，則會更新其轉換。
具體而言，其本機位置會重設，而其本機旋轉會設定為符合滑杆軸的方向。
未修改其規模。
如果刻度具有方格物件集合元件，則版面配置和 CellWidth 或 CellHeight 會隨之更新，以符合滑杆軸。
