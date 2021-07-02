---
title: 手物理學服務
description: 在 MRTK 中使用手物理延伸模組服務的檔
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: af7ea753d52b5e478c54ca19d6d8e391401eea6d
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176254"
---
# <a name="hand-physics-service"></a>手物理學服務

![手上物理延伸模組服務](../images/hand-physics/MRTK_UX_HandPhysics_Main.jpg)

實際的物理服務可讓您使用明確的內文衝突事件，並與明確的手進行互動。

## <a name="enabling-the-extension"></a>啟用擴充功能

若要啟用擴充功能，請開啟您的 RegisteredServiceProvider 設定檔。 按一下 `Register a new Service Provider` 以新增設定。 在 [元件類型] 欄位中，選取 [HandPhysicsService]。 在 [設定設定檔] 欄位中，選取延伸模組隨附的預設的 [物理設定檔]。

## <a name="profile-options"></a>設定檔選項

### <a name="hand-physics-layer"></a>手中實體層

控制具現化的手接點將移至的圖層。

雖然服務預設為「預設」層 (0) ，但建議針對手物理物件使用不同的層級。 否則可能會發生不必要的衝突和（或）不正確的 raycasts。

### <a name="finger-tip-kinematic-body-prefab"></a>手指運動主體預製專案

控制可隨時具現化的預製專案。 為了讓服務能夠如預期般運作，預製專案需要：

- 啟用 isKinematic 的 rigidbody 元件
- 碰撞
- `JointKinematicBody` 元件

### <a name="use-palm-kinematic-body"></a>使用 palm 運動學主體

控制服務是否會嘗試將預製專案具現化于 palm 聯合。

### <a name="palm-kinematic-body-prefab"></a>掌運動學內文主體預製專案

當 `UsePalmKinematicBody` 啟用時，這會是要具現化的預製專案。 就像 `FingerTipKinematicBodyPrefab` 這樣的預製專案需要：

- 啟用 isKinematic 的 rigidbody 元件
- 碰撞
- `JointKinematicBody` 元件

## <a name="how-to-use-the-service"></a>如何使用服務

啟用之後，請使用任何碰撞器的 `IsTrigger` 屬性來接收所有10位數的衝突事件 (和手掌（如果已啟用) ）。
