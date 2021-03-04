---
title: README_HandPhysicsExtensionService
description: 描述手型物理延伸模組服務。
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: 4a046eb1582c443aeb0a3e07a40738f5e9b53d80
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/03/2021
ms.locfileid: "101780717"
---
# <a name="hand-physics-extension-service"></a>手上物理延伸模組服務

![手上物理延伸模組服務](../../Images/HandPhysics/MRTK_UX_HandPhysics_Main.jpg)

實際的物理服務可讓您使用明確的內文衝突事件，並與明確的手進行互動。

## <a name="getting-started-with-hand-physics-extension-service"></a>開始使用手型物理延伸模組服務

將「手型物理服務」新增至擴充服務清單，並使用預設設定檔。

啟用之後，請使用任何碰撞器的 IsTrigger 屬性來接收來自所有10位數的衝突事件 (以及手掌是否已啟用) 。

### <a name="prerequisites"></a>必要條件

- 已啟用延伸模組服務
- 將適當的預製專案指派給手指/掌接合。

## <a name="recommendations"></a>建議

雖然服務預設為「預設」層，但建議針對 HandPhysics 物件使用不同的層級。 否則可能會發生不必要的衝突和（或）不正確的 raycasts。
