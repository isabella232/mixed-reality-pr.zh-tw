---
title: Dock
description: 停駐控制項的描述。
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: 4446dbe3199aab63d7ee85474d3696a45cf4401f1d8100a8d99885a7265c7fe2
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2021
ms.locfileid: "115226570"
---
# <a name="dock"></a>Dock

![Dock](../images/dock/MRTK_UX_Dock_Main.png)

此控制項可讓您將物件移入和移出預定的位置，以建立調色板、貨架和導覽列。

## <a name="features"></a>功能

- 支援任意數目的 dock 位置和版面配置 (可搭配 [`GridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection)) 
- 停駐的物件會自動移至新物件的空間
- 物件會縮放以符合停駐的空間，然後在拖曳時調整為其原始位置。

## <a name="getting-started-with-dock"></a>開始使用 Dock

- 使用 Dock 元件建立 GameObject，並在其中新增 Gameobject 的子系。
- 將 DockPosition 元件新增至每個子系。
- 在場景中將可停駐元件新增至任意數目的物件，以允許它們固定。 它們也必須有 [`ObjectManipulator`](xref:Microsoft.MixedReality.Toolkit.UI.ObjectManipulator) 元件和碰撞。
- *選擇性：* 使用 [`GridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection) Dock 來自動設定 DockPositions。

### <a name="prerequisites"></a>必要條件

- 每個可停駐的物件都必須具有或的碰撞 [`ObjectManipulator`](xref:Microsoft.MixedReality.Toolkit.UI.ObjectManipulator) [`ManipulationHandler`](xref:Microsoft.MixedReality.Toolkit.UI.ManipulationHandler) 。
- 如果您想要物件在場景載入時啟動停駐，請將它指派給任何 DockPosition 的停駐物件屬性。

## <a name="how-it-works"></a>運作方式

可停駐元件是以操作事件為基礎，可讓拖曳的物件在特定位置停駐和取消停駐。 放置是由最接近的重迭觸發 DockPosition 至拖曳的物件所決定，因此這兩個物件都必須有 Colliders，觸發程式才能啟動。
