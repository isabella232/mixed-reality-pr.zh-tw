---
title: README_Tooltip
description: MRTK 中的工具提示總覽
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、工具提示、
ms.openlocfilehash: 92c49761dca4b3fa58853dfced2c556454c9d2b6
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/03/2021
ms.locfileid: "101781051"
---
# <a name="tooltip"></a>工具提示

![工具提示主要](Images/Tooltip/MRTK_Tooltip_Main.png)

工具提示通常用來在進一步檢查物件時傳達提示或額外資訊。 工具提示可以用來標注實體環境中的物件。

## <a name="how-to-use-a-tooltip"></a>如何使用工具提示

工具提示可以直接新增至階層，並以物件為目標。

若要使用這個方法，只需將遊戲物件和其中一個工具提示 prefabs (資產/MRTK/SDK/Features/UX/Prefabs/工具提示) 至場景階層。 在預製專案的 [偵測器] 面板中，展開 [`ToolTip`](xref:Microsoft.MixedReality.Toolkit.UI.ToolTip) 腳本。 選取提示狀態，並設定工具提示。  在 [文字] 欄位中，輸入工具提示的個別文字。 展開 [`ToolTipConnector`](xref:Microsoft.MixedReality.Toolkit.UI.ToolTipConnector) 腳本，並將具有工具提示的物件從階層拖曳至標示為 [ *目標*] 的欄位。 這會將工具提示附加至物件。
![工具提示連接器](Images/Tooltip/MRTK_Tooltip_Connector.png)

這種使用方式假設工具提示一律會顯示，或是藉由變更 tooltip 元件的工具提示狀態屬性，透過腳本顯示/隱藏。

## <a name="dynamically-spawning-tooltips"></a>動態產生工具提示

工具提示可以在執行時間以動態方式加入至物件，也可以預先設定為在點按或焦點上顯示和隱藏。 只要將 [`ToolTipSpawner`](xref:Microsoft.MixedReality.Toolkit.UI.ToolTipSpawner) 腳本新增到任何遊戲物件。 出現和消失的延遲可在腳本偵測器和存留期內設定，讓工具提示在設定的持續時間之後消失。 工具提示也是功能樣式屬性，例如 spawner 腳本中的背景視覺效果。 根據預設，工具提示會使用 spawner 腳本錨定至物件。 這可以藉由將 GameObject 指派給錨點欄位來加以變更。

## <a name="example-scene"></a>範例場景

在範例場景中 (資產/MRTK/範例/示範/UX/工具提示/場景) ，您將可以找到工具提示的各種範例。

![工具提示範例](Images/Tooltip/MRTK_Tooltip_Examples.png)
