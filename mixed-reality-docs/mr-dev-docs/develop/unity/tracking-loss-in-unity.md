---
title: Unity 中的追蹤遺失
description: 瞭解如何在 Unity mixed reality 應用程式內處理手動和預設追蹤的遺失。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Unity、追蹤遺失、追蹤遺失影像、輪詢、混合現實耳機、windows mixed reality 耳機、虛擬實境耳機
ms.openlocfilehash: 39ce4e079886b27ed35c419a3b3913c6700e0d32
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009848"
---
# <a name="tracking-loss-in-unity"></a>Unity 中的追蹤遺失

當裝置無法在世界中找到自己的裝置時，應用程式會遇到「追蹤遺失」。 根據預設，Unity 將會暫停更新迴圈，並在每次追蹤遺失時向使用者顯示啟動顯示映射。 一旦重新開機追蹤之後，啟動顯示映射就會消失，而且更新迴圈會繼續進行。

或者，使用者可以退出宣告設定，以手動方式處理這項轉換。 如果沒有執行任何動作來處理，則所有內容在追蹤遺失期間都會變成主體鎖定。

## <a name="default-handling"></a>預設處理

根據預設，更新迴圈和所有訊息和事件將會在追蹤遺失期間停止。 如此一來，使用者就會看到一個影像。 您可以從 [編輯->設定->播放程式]、按一下 [啟動顯示影像]，然後設定全像攝影追蹤損失影像來自訂此映射。

## <a name="manual-handling"></a>手動處理

若要手動處理追蹤遺失，您需要移至 [**編輯**  >  **專案設定**  >  **播放機**  >  **] 通用 Windows 平臺設定]** 索引標籤  >  **啟動顯示映射**  >  **Windows** 全像，然後取消核取 [追蹤遺失暫停和顯示影像]。 之後，您必須使用下列指定的 Api 來處理追蹤變更。

**命名空間：** *UnityEngine. XR*<br>
**類型：** *WorldManager*

* 全域管理員會公開事件，以偵測遺失/取得的追蹤 (*WorldManager OnPositionalLocatorStateChanged*) 和屬性，以查詢目前狀態 (*WorldManager 的狀態*) 
* 當追蹤狀態為非作用中時，即使使用者翻譯，相機也不會在虛擬環境中轉譯。 物件不會再對應到任何實體位置，而且會顯示為已鎖定主體。

處理您自己的追蹤變更時，您必須輪詢每個框架的狀態屬性，或處理 *OnPositionalLocatorStateChanged* 事件。

### <a name="polling"></a>輪詢

最重要的狀態是 *PositionalLocatorState*，這表示追蹤功能完全正常運作。 任何其他狀態都只會導致主要攝影機的旋轉差異。 例如：

```cs
void Update()
{
    switch (UnityEngine.XR.WSA.WorldManager.state)
    {
        case PositionalLocatorState.Active:
            // handle active
            break;
        case PositionalLocatorState.Activating:
        case PositionalLocatorState.Inhibited:
        case PositionalLocatorState.OrientationOnly:
        case PositionalLocatorState.Unavailable:
        default:
            // only rotational information is available
            break;
    }
}
```

### <a name="handling-the-onpositionallocatorstatechanged-event"></a>處理 OnPositionalLocatorStateChanged 事件

更方便的一點是，您也可以訂閱 *OnPositionalLocatorStateChanged* 來處理轉換：

```cs
void Start()
{
    UnityEngine.XR.WSA.WorldManager.OnPositionalLocatorStateChanged += WorldManager_OnPositionalLocatorStateChanged;
}

private void WorldManager_OnPositionalLocatorStateChanged(PositionalLocatorState oldState, PositionalLocatorState newState)
{
    if (newState == PositionalLocatorState.Active)
    {
        // Handle becoming active
    }
    else
    {
        // Handle becoming rotational only
    }
}
```

## <a name="see-also"></a>請參閱

* [處理 DirectX 中的追蹤遺失](../native/coordinate-systems-in-directx.md#handling-tracking-loss)
