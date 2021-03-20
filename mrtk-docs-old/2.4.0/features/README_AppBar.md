---
title: README_AppBar
description: MRTK 中的應用程式行總覽
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
ms.localizationpriority: medium
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、應用程式行、
ms.openlocfilehash: e730c5a51aa32e72147ec7482b9ebbcdb9fafedc
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104688808"
---
# <a name="app-bar"></a>應用程式列

![應用程式列](Images/AppBar/MRTK_AppBar_Main.png)

應用程式行是與周 [框](README_BoundingBox.md) 方塊腳本一起使用的 UI 元件。 它會將按鈕控制項新增至物件，並具有要操作的目的。 您可以使用 [調整] 按鈕，將物件的周框方塊介面解除/啟用。 [移除] 按鈕應該從場景中移除該物件。

## <a name="how-to-use-app-bar"></a>如何使用應用程式行

拖放 `AppBar` (資產/MRTK/SDK/Features/UX/Prefabs/AppBar/AppBar. 預製專案) 入場景階層中。 在元件的 [偵測器] 面板中，指派具有周框方塊的任何物件做為 *目標周框* 方塊，以將應用程式行加入其中。

**重要事項：** 目標物件的周框方塊啟用選項應該是「手動啟用」。

<img src="Images/AppBar/MRTK_AppBar_Setup1.png" width="450" alt="App Bar Setup 1">

<img src="Images/AppBar/MRTK_AppBar_Setup2.png" width="450" alt="App Bar Setup 2">
