---
title: 手部與運動控制器
description: 瞭解手和移動控制器互動模型，其可以移除虛擬與實體之間的界限。
author: shengkait
ms.author: shentan
ms.date: 04/26/2019
ms.topic: article
keywords: 混合的現實、手、移動控制器、互動、設計
ms.openlocfilehash: 8b2ed6127708204d0c4a537c56b2225ff26e0d0f
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2020
ms.locfileid: "91680865"
---
# <a name="hands-and-motion-controllers"></a>手部與運動控制器
## <a name="scenarios"></a>案例
如果您在閱讀 [互動總覽](interaction-fundamentals.md)之後選擇採用此互動模型，表示您正在開發應用程式，要求使用者使用兩次手與全像全球互動。 您的應用程式即將達成在虛擬和實體之間移除界限的目標。

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
       這是運用手的強大功能，讓使用者能夠直接觸及和操作全像投影。 藉由運用每日使用經驗並提供適當的視覺 affordances，使用者就能夠使用相同的方式來操作真實世界的物件，以與虛擬化物件互動。
    :::column-end:::
    :::column:::
       [![用手指向並認可](images/hands-and-controllers-point-and-commit.jpg)](point-and-commit.md)<br>
        ### <a name="point-and-commit-with-handsbr"></a>[手部指向和行動](point-and-commit.md)<br>
        這種樣式可讓使用者在距離中與全像影像互動。 它可讓使用者充分利用環境。 使用者可以在任何地方放置全像位置，然後從任何距離進行存取。 用來控制和操作2D 和3D 全像投影的精神模型和筆勢，與直接操作的高度同步。
    :::column-end:::
    :::column:::
       [![運動控制器](images/hands-and-controllers-motion-controllers.jpg)](motion-controllers.md)<br>
       ### <a name="motion-controllersbr"></a>[運動控制器](motion-controllers.md)<br>
       移動控制器是一種工具，可在使用其中一種或兩種方式時，跨大量距離提供精確的互動，以擴充使用者的實體功能。 這些硬體配件提供許多常用互動的快捷方式，並針對各種不同的動作提供 surefooted、tactile 的意見反應。 目前，移動控制器僅適用于 Windows Mixed Reality (WMR) 案例。 
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
