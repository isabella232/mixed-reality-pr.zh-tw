---
title: ManipulationHandler
description: MRTK 中操作處理常式的相關檔
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、操作、
ms.openlocfilehash: 2731e66c09a7c207a709f1073d9f3f09c59233b0
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104686311"
---
# <a name="manipulation-handler"></a>操作處理常式

![操作處理常式](../images/manipulation-handler/MRTK_Manipulation_Main.png)

*ManipulationHandler* 腳本可讓您使用一或兩個手將物件設為可移動、可擴充和 rotatable。 可以限制操作，讓它只允許特定類型的轉換。 此腳本適用于各種類型的輸入，包括 HoloLens 2 明確的手寫輸入、手片、HoloLens (第一代) 手勢輸入，以及沉浸式耳機移動控制器輸入。

## <a name="how-to-use-the-manipulation-handler"></a>如何使用操作處理常式

將 `ManipulationHandler` 腳本元件新增至 GameObject。 請務必同時將碰撞新增至物件，以符合其 grabbable 界限。

若要讓物件回應接近明確的手輸入，請新增 `NearInteractionGrabbable` 腳本。

![操作處理常式](../images/manipulation-handler/MRTK_ManipulationHandler_Howto.png)

## <a name="inspector-properties"></a>偵測器屬性

<img src="../images/manipulation-handler/MRTK_ManipulationHandler_Structure.png" width="450" alt="Manipulation Handler structure">

**主機轉換** 將拖曳的轉換。 預設為元件的物件。

**操作類型** 指定是否可以使用一或兩個手來操作物件。

* *僅限一次*
* *僅限兩個右手*
* *一和兩個右手*

**兩個右手操作類型**

* *調整*：只允許縮放。
* *旋轉*：只允許旋轉。
* *移動縮放*：允許移動和調整。
* *移動旋轉*：允許移動和旋轉。
* *旋轉比例*：允許旋轉和縮放。
* *移動旋轉比例*：允許移動、旋轉和縮放。

![操作處理常式](../images/manipulation-handler/MRTK_ManipulationHandler_TwoHanded.jpg)

**允許目前的操作** 指定是否可以使用與指標互動的方式來執行操作。

**接近的一次旋轉模式** 指定當物件在接近的一端進行抓取時，該物件的行為。

**一種手邊的旋轉模式** 指定當物件以距離的一端抓取時，該物件的行為。

**一種旋轉模式選項** 指定當物件被抓取時，物件將如何旋轉。

* *維護原始輪替*：不會在物件移動時旋轉物件
* *維護對使用者的旋轉*：為使用者維護 X/Y 軸的物件原始旋轉
* *引力對齊維護對使用者的旋轉*：將物件的原始旋轉維護給使用者，但讓物件垂直。 適用于具有界限控制項的物件。
* *臉部使用者*：確保物件一律會臉部給使用者。 適用于平板/面板。
* *離開使用者的臉部*：確保物件永遠都不會離開使用者。 適用于已設定反向的平板/面板。
* *旋轉物件中心*：僅適用于已明確說明的手/控制器。 使用手形/控制器的旋轉旋轉物件，但關於物件中心點。 適用于檢查距離。
* *旋轉大約抓取點*：僅適用于已明確說明的手/控制器。 旋轉物件，如同由手動/控制器持有一樣。 適用于檢查。

**發行行為** 釋放物件時，請指定其實體移動行為。 要求 rigidbody 元件必須在該物件上。

* *Nothing*
* *所有項目*
* *保持速度*
* *保持角度速度*

**旋轉的條件約束** 指定當互動時，物件將旋轉的軸。

* *None*
* *僅限 X 軸*
* *僅 Y 軸*
* *僅 Z 軸*

**使用本機空間進行條件約束** 切換在套用條件約束與全球空間軸或本機空間軸之間的切換。

**移動時的條件約束**

* *None*
* *修正與 head 之間的距離*

**啟用平滑** 指定是否啟用平滑處理。

**平滑量一手勢** 要套用到移動、縮放、旋轉的凹凸貼圖數量。 將0平滑表示無平滑。 最大值表示不變更值。

## <a name="events"></a>事件

操作處理常式會提供下列事件：

* *OnManipulationStarted*：在操作開始時引發。
* *OnManipulationEnded*：在操作結束時引發。
* *OnHoverStarted*：當手形/控制器停留在接近或遠的 manipulatable 時，就會引發。
* *OnHoverEnded*：當手形/控制器取消暫留 manipulatable 時（接近或遠）時，就會引發。
