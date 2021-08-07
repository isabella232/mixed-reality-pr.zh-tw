---
title: 手部與運動控制器
description: 瞭解手和移動控制器互動模型，其可以移除虛擬與實體之間的界限。
author: shengkait
ms.author: shentan
ms.date: 04/26/2019
ms.topic: article
keywords: 混合的現實、手、運動控制器、互動、設計、混合現實耳機、windows mixed Reality 耳機、虛擬實境耳機、HoloLens、MRTK、混合現實工具組
ms.openlocfilehash: 3a54d707260a3e5aebd83a53b62098504c86c9fea7b2ecbb49d3dbd8b72400dd
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2021
ms.locfileid: "115213688"
---
# <a name="hands-and-motion-controllers"></a>手部與運動控制器

## <a name="scenarios"></a>案例

閱讀 [互動總覽](interaction-fundamentals.md)之後，您可以選擇手和移動控制器互動模型。 這表示您要開發一個應用程式，要求使用者使用兩次手與全像全球互動。 您的應用程式即將達成在虛擬和實體之間移除界限的目標。

某些特定案例可能是：
* 為資訊工作者提供具有 UI 能供性的 2D 虛擬畫面，以顯示及控制內容
* 提供工廠元件線的第一行工作者教學課程和指南
* 開發專業工具以協助及教育醫療專業人員  
* 使用 3D 虛擬物件來裝飾真實世界或建立第二個世界 
* 以真實世界為背景來建立以位置為基礎的服務與遊戲

<br>

---

## <a name="hands-and-motion-controllers-modalities"></a>手和移動控制器形式

:::row:::
    :::column:::
       [![用手直接操作](images/hands-and-controllers-direct-manipulation.jpg)](direct-manipulation.md)<br>
       ### <a name="direct-manipulation-with-handsbr"></a>[手部直接操作](direct-manipulation.md)<br>
       運用使用者可用來觸控和操作全像的功能的樣式。 藉由使用每日體驗並提供適當的視覺 affordances，使用者就可以使用相同的方式來操作真實世界的物件，以與虛擬使用者互動。
    :::column-end:::
    :::column:::
       [![用手指向並認可](images/hands-and-controllers-point-and-commit.jpg)](point-and-commit.md)<br>
        ### <a name="point-and-commit-with-handsbr"></a>[手部指向和行動](point-and-commit.md)<br>
        這種樣式可讓使用者在距離中與全像影像互動。 它可讓使用者充分利用環境。 使用者可以在任何地方放置全像位置，然後從任何距離進行存取。 用來控制和操作2D 和3D 全像投影的精神模型和筆勢，與直接操作的高度同步。
    :::column-end:::
    :::column:::
       [![運動控制器](images/hands-and-controllers-motion-controllers.jpg)](motion-controllers.md)<br>
       ### <a name="motion-controllersbr"></a>[運動控制器](motion-controllers.md)<br>
       移動控制器會擴充使用者的實體功能，並在使用一或兩個區域時，以精確的方式進行互動。 這些硬體配件提供許多常用互動的快捷方式，並針對各種動作提供 footed、tactile 的意見反應。 目前，移動控制器僅適用于 Windows Mixed Reality (WMR) 案例。 
    :::column-end:::
:::row-end:::

<br>

---

## <a name="see-also"></a>另請參閱
* [頭部目光和行動](gaze-and-commit.md)
* [頭部目光和停駐](gaze-and-dwell.md)
* [手部直接操作](direct-manipulation.md)
* [手部指向和行動](point-and-commit.md)
* [免持式](hands-free.md)
