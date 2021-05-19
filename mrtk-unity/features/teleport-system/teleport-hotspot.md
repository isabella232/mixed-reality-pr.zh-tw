---
title: 傳送熱點
description: MRTK 中 [傳送] 熱點元件的檔
author: RogPodge
ms.author: roliu
ms.date: 03/25/2021
ms.localizationpriority: medium
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、傳送系統、傳送熱點
ms.openlocfilehash: 0cbdad3c038d457109077b742d3f453d63436ae4
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144432"
---
# <a name="teleport-hotspot-experimental"></a>傳送熱點 [實驗]

「傳送」熱點是您可以新增至 gameobject 的元件，可確保使用者在傳送至該位置時，在特定的位置和方向。

## <a name="usage"></a>使用方式

### <a name="how-to-create-a-teleport-hotspot"></a>如何建立傳送熱點

若要建立傳送點傳送熱點，請將 TeleportHotspot 元件新增至也有碰撞器元件的物件。 

![傳送熱點元件](../images/teleport/TeleportHotspotComponent.png)

現在，當傳送指標指標超過 TeleportHotspot 時，會變更其色彩。 當透過熱點完成傳送動作時，使用者會傳送至 TeleportHotspot 的中心。

如果核取 [覆寫方向] 旗標，使用者的方向將符合 [傳送] 熱點的方向。

![傳送熱點範例](../images/teleport/TeleportHotspotExample.gif)
