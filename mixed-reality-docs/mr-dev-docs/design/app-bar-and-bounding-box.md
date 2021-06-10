---
title: 週框方塊和應用程式列
description: 應用程式行是一個物件層級的功能表，其中包含一系列的按鈕，可顯示在全像影像的範圍下邊緣。
author: radicalad
ms.author: adlinv
ms.date: 06/07/2019
ms.topic: article
keywords: Windows Mixed Reality，應用程式橫條，周框方塊，混合現實耳機，windows Mixed Reality 耳機，虛擬實境耳機、HoloLens、MRTK、混合現實工具組
ms.openlocfilehash: 750fb238e5b7f22998a86f71607498c8f6982076
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600517"
---
# <a name="bounding-box-and-app-bar"></a>週框方塊和應用程式列
![「周框」是混合現實物件操作的標準介面。](images/UX_Hero_BoundingBox.jpg)<br>
<br>

## <a name="what-is-the-bounding-box"></a>什麼是周框方塊？

「周框」是混合現實物件操作的標準介面。 這項功能可為使用者提供視覺提示，指出物件目前是可調整的。 在 HoloLens 2 上，周框方塊適用于直接操作，而且會回應使用者的 finger's 鄰近性。 它會顯示視覺效果的意見反應，以協助使用者感知與物件之間的距離。

:::row:::
    :::column:::
        ### <a name="scaling-an-objectbr"></a>調整物件<br>
        周框方塊的邊角會告訴使用者物件可以調整的範圍。 控點會遵循廣泛瞭解的調整規模模式。 此視覺提示會顯示使用者物件的總區域，即使在調整模式之外看不到它。 如果沒有這項功能，則會有一個物件（貼齊至另一個物件或介面）的行為，就像是在不應該出現的位置周圍一樣。<br>
        <br>
        *影片迴圈：透過周框方塊調整物件*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       ![HoloLens 透過周框方塊調整物件的觀點](images/HoloLens2_BoundingBox.gif)<br>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ### <a name="rotating-an-objectbr"></a>旋轉物件<br>
        周框方塊邊緣的垂直矩形 affordances 是旋轉指示器。 如此可讓使用者更精細地調整其放置的全像投影。 他們不僅能調整規模，還能調整規模，現在也可以旋轉。<br>
        <br>
        *影片迴圈：透過周框方塊旋轉物件*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       ![HoloLens 透過周框方塊旋轉物件的觀點](images/HoloLens2_BoundingBox_Rotate.gif)<br>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ### <a name="visual-feedback-on-hand-proximity-on-hololens-2br"></a>HoloLens 2 上的手近距離視覺回饋<br>
        在 HoloLens 2 上有一個額外的視覺提示，可協助使用者深入瞭解。 當 fingertip 接近物件時，靠近其 fingertip 的環形會顯示並縮小。 當觸達已按下的狀態時，環形最終會聚合成點。 此 visual affordance 可協助使用者瞭解它們與物件之間的距離。<br>
        <br>
        *影片迴圈：根據鄰近範圍方塊的視覺效果意見反應範例*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       ![關於手近距離的視覺回饋](images/HoloLens2_Proximity.gif)<br>
    :::column-end:::
:::row-end:::

<br>

**針對 Unity 應用程式開發，請參閱 [混合現實工具組-Unity 中的周框方塊。](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)**

<br>

---

## <a name="what-is-the-app-bar"></a>什麼是應用程式行？

應用程式行是一個物件層級的功能表，其中包含一系列顯示在全像全像全像在全像是在全像影像的邊界下邊緣的按鈕。 此模式通常用來讓使用者移除及調整全像投影。 應用程式行的設計主要是在使用者的環境中管理放置物件的方式。 結合周框方塊，使用者可以完全掌控物件在混合現實中的位置和方式。

:::row:::
    :::column:::
        ### <a name="the-app-bar-follows-the-userbr"></a>應用程式行會跟隨使用者<br>
        由於這個模式會與全球鎖定的物件一起使用，因此當使用者四處移動物件時，應用程式行一律會顯示在最接近使用者的物件端。 雖然在技術上並不 billboarding，但這項功能實際上也達到相同的結果。 防止使用者的位置遮蔽或封鎖可從環境中的不同位置取得的功能。 <br>
        <br>
        *影片迴圈：流覽全像投影，應用程式行*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       ![四處移動全像投影。 應用程式行如下。](images/HoloLens2_AppBarFollowing.gif)<br>
    :::column-end:::
:::row-end:::

<br>


## <a name="bounding-box-in-mrtk-mixed-reality-toolkit-for-unity"></a>Unity 的 MRTK (混合現實工具組) 中的周框方塊
**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** 提供周框方塊和應用程式行的腳本和 prefabs。 您可以藉由將 BoundingBox .cs 腳本指派給任何物件，來新增周框方塊。

* [MRTK 周框方塊](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/bounding-box)


<br>

---


## <a name="see-also"></a>另請參閱

* [游標](cursors.md)
* [手部光線](point-and-commit.md)
* [Button](button.md)
* [可互動的物件](interactable-object.md)
* [週框方塊和應用程式列](app-bar-and-bounding-box.md)
* [操作](direct-manipulation.md)
* [手部功能表](hand-menu.md)
* [近端功能表](near-menu.md)
* [物件集合](object-collection.md)
* [語音命令](voice-input.md)
* [鍵盤](keyboard.md)
* [工具提示](tooltip.md)
* [平板](slate.md)
* [滑桿](slider.md)
* [著色器](shader.md)
* [佈告板和常駐標籤](billboarding-and-tag-along.md)
* [顯示進度](progress.md)
* [表面磁性](surface-magnetism.md)