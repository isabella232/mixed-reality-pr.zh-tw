---
title: 顯示進度
description: 瞭解進度控制項如何提供意見反應給使用者，在您的混合現實應用程式中進行長時間執行的作業。
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality、設計、控制項、ui、ux、進度指標、混合現實耳機、windows Mixed Reality 耳機、虛擬實境耳機、HoloLens、MRTK、混合現實工具組
ms.openlocfilehash: 489f4bd9fea31126f936673db7acafeab27d9cd9
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009458"
---
# <a name="progress-indicator"></a>進度指示器

<br>

<img src="images/MRTK_ProgressIndicator.gif" alt="Progress ring example in HoloLens" width="940px">

進度控制項可提供執行長時間執行作業的意見反應。 當進度指標可見時，使用者可以看到等待時間，而且無法與應用程式互動。

<br>

---

## <a name="types-of-progress"></a>進度的類型

請務必提供有關所發生情況的使用者資訊。 在混合的情況下，如果您的應用程式沒有良好的視覺效果意見反應，就可以輕鬆地將使用者的注意力帶到實體環境或物件。 在需要幾秒鐘的情況下（例如資料載入或場景正在進行更新時），最好是顯示視覺指標。 有兩個選項可讓使用者顯示作業正在進行中– **進度** 列或 **進度環形**。

:::row:::
    :::column:::
        ### <a name="progress-barbr"></a>進度列<br>
        進度列會顯示工作的完成百分比。 它應該在其持續時間已知 (確定) 的作業期間使用，但其進度不應封鎖使用者與應用程式的互動。<br>
        <br>
        *影像： HoloLens 的進度列範例*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       ![HoloLens 中的進度列範例](images/640px-progressbar.jpg)<br>
    :::column-end:::
:::row-end:::

<br>

---

:::row:::
    :::column:::
        ### <a name="progress-ringbr"></a>進度環<br>
        進度環形只有不定狀態，而且應該在作業完成之前封鎖使用者互動時使用。<br>
        <br>
        *影像： HoloLens 的進度環形範例*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       ![HoloLens 裝置上的進度環形範例](images/640px-progressring.jpg)<br>
    :::column-end:::
:::row-end:::

<br>

---

:::row:::
    :::column:::
        ### <a name="progress-with-a-custom-objectbr"></a>使用自訂物件的進度<br>
        您可以使用自己的自訂 2D/3D 物件自訂進度控制項，以新增至您應用程式的個人和品牌身分識別。<br>
        <br>
        *影像：在 HoloLens 中使用自訂網格範例的進度*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       ![HoloLens 中自訂網格範例的進度](images/640px-progresscustom.jpg)<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="best-practices"></a>最佳作法
* 將 [billboarding 或標記](billboarding-and-tag-along.md) 緊密結合到進度顯示，因為使用者可以輕鬆地將其移到空白空間並遺失內容。 如果使用者無法看到任何結果，您的應用程式可能看起來像是損毀。 Billboarding 和標記-也內建在進度預製專案中。
* 提供使用者所發生狀況的狀態資訊一律是很好的方式。 進度預製專案提供各種視覺化樣式，包括提供狀態的 Windows 標準環形類型進度。 如果您希望進度的樣式與您的應用程式品牌保持一致，您也可以使用自訂網格和動畫。

<br>

---

## <a name="progress-indicator-in-mrtk-mixed-reality-toolkit-for-unity"></a>Unity 的 MRTK (混合現實工具組) 的進度列指示器

* [MRTK-進度指標 prefabs](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MRTK/SDK/Features/UX/Prefabs/ProgressIndicators)
* [MRTK-場景轉換服務](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Extensions/SceneTransitionService/SceneTransitionServiceOverview.html)


<br>

---

## <a name="see-also"></a>請參閱

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
