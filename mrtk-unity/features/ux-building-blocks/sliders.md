---
title: 滑桿
description: 滑杆 MRTK 簡介
author: RogPodge
ms.author: roliu
ms.date: 06/18/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、滑杆、
ms.openlocfilehash: c8a2b6c377762918bfff79008ab34d3dfe4e20bb
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177504"
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
  - TouchCollider-碰撞，包含滑杆的整個可選取區域。 啟用 [貼齊至位置] 行為。
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

**貼齊至位置** 此滑杆是否貼齊滑杆上的指定位置

**為可觸式** 此滑杆是否可透過觸控事件進行控制

**Thumb 碰撞** 控制滑杆捲軸的碰撞程式

**可觸式碰撞** 當貼齊至位置為 true 時，可以觸及或選取的滑杆區域。

**滑杆值** 滑杆的值。

**使用滑杆步驟的部門** 控制此滑杆是否會在步驟中或連續遞增。

**滑杆步驟部門** 啟用 [使用滑杆步驟] 區域時，滑杆分割至的子分割數目。

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

## <a name="example-slider-configurations"></a>範例滑杆設定

具有貼齊位置連續滑杆的連續滑杆 ![](https://user-images.githubusercontent.com/39840334/122488212-d410a400-cf91-11eb-8d31-fc7584ddc465.gif)

貼齊位置的步驟滑杆

![步驟滑杆](https://user-images.githubusercontent.com/39840334/122488226-dc68df00-cf91-11eb-9459-89655bbb054d.gif)

觸控滑杆

![觸控滑杆](https://user-images.githubusercontent.com/39840334/122488221-d8d55800-cf91-11eb-91a1-bb12debe2797.gif)
