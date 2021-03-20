---
title: README_ScrollingObject
description: MRTK 中的描述滾動物件集合。
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
ms.localizationpriority: medium
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: a8c81be94d155a125366a390e0032a099e2d80b9
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104692685"
---
# <a name="scrolling-object-collection"></a>滾動物件集合

![滾動收集](../../features/Images/ScrollingCollection/MRTK_UX_ScrollingCollection_Main.jpg)

ScrollingObjectCollection 是原生滾動3D 物件的物件集合。 它支援滾動 pressable 按鈕和 Interactables，以及非互動式物件。 此集合支援近和遠的輸入。 若要使用 ScrollingObjectCollection，物件必須使用 MRTK 標準著色器，才能讓剪切效果正常運作。

## <a name="getting-started-with-scrolling-object-collection"></a>開始使用滾動物件集合

為了方便起見，有兩個 ScrollingObjectCollection Prefabs 可供使用。 其中一個設定為使用 32x92mm PressableButton prefabs，另一個則適用于32x32x32mm 容器中的任何物件。

只要將這些 prefabs 放入場景中，加入所需的物件，然後按 "UpdateCollection"，即可完成集合的設定和配置。

### <a name="prerequisites"></a>Prerequisites

- 集合中的所有物件都必須使用 MRTK 標準著色器
- 集合中的每個物件都必須具有具有的碰撞 [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) 。 所有的衝突測試目前都是使用這些 colliders 來完成;ScrollingObjectCollection 尚不支援靜態/nonmoving 支援碰撞。
- 集合中的所有物件目前都必須是相同的大小，此外，如果您的物件不是在 gameObject 中，您可能會得到非預期的結果。
- 針對無縫可觸式介面，滾動集合中的「資料格大小」應該符合集合中每個物件的大小。

使用按鈕時有其他需求：

- 必須停用 PressableButton。 ReleaseOnTouch。
- PhysicalPressEventRouter. InteractableOnClick 最多可設定為 EventOnClickCompletion 或 EventOnPress。
- 在編輯時，ScrollingObjectCollection 可以自動修正這些元件。 但是，當動態具現化 Prefabs 或元件時，請確定已正確設定這些屬性。

## <a name="how-it-works"></a>運作方式

ScrollingObjectCollection 會將本身訂閱為觸控和指標事件的全域接聽程式，以篩選對應至清單中專案的事件。 一開始，集合不會執行任何動作，並讓事件傳遞至子物件，如此可讓子物件如預期般主角和選取。 一旦 ScrollingObjectCollection 將互動視為「拖曳」之後，集合就會開始將所有後續的 eventData 標示為已使用，並開始在設定軸上滾動清單。

使用觸控時，清單會繼續滾動，直到 PokePointer 超過清單前方的觸控平面為止。
