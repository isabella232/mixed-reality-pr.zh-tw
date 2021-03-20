---
title: README_AppBar
description: MRTK 中的應用程式行總覽
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、應用程式行、
ms.openlocfilehash: 5bb7f780cf49486c68ca6dc3efa6c8cccd55ab65
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104682071"
---
# <a name="app-bar"></a>應用程式列

![應用程式列](../images/app-bar/MRTK_AppBar_Main.png)

應用程式行是與 [界限控制](bounds-control.md) 腳本一起使用的 UI 元件。 它會將按鈕控制項新增至物件，並具有要操作的目的。 您可以使用 [調整] 按鈕，將物件的界限控制介面解除/啟用。 [移除] 按鈕應該從場景中移除該物件。

## <a name="how-to-use-app-bar"></a>如何使用應用程式行

拖放 `AppBar` (資產/MRTK/SDK/Features/UX/Prefabs/AppBar/AppBar. 預製專案) 入場景階層中。 在元件的 [偵測器] 面板中，將具有界限控制項的任何物件指派為 *目標周框* 方塊，以將應用程式行加入其中。

**重要事項：** 目標物件的界限控制項啟用選項應該是「手動啟用」。

<img src="../images/app-bar/MRTK_AppBar_Setup1.png" width="450" alt="Setup 1">

<img src="../images/app-bar/MRTK_AppBar_Setup2.png" width="450" alt="Set up 2">
