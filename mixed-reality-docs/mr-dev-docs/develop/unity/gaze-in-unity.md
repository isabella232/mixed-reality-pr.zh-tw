---
title: Unity 中的目光
description: 「注視」是一種主要方式，可讓使用者以混合現實的方式來設定您應用程式所建立的全像
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: 眼睛、頭部眼、unity、全息圖、混合現實
ms.openlocfilehash: 8c1a6cb0847cd0e6e776c6d4e1f7c1efdc126279
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2020
ms.locfileid: "91679773"
---
# <a name="head-gaze-in-unity"></a>Unity 中的頭部

「[注視](../../design/gaze-and-commit.md)」是一種主要方式，可[讓使用者](../../discover/hologram.md)以[混合現實](../../discover/mixed-reality.md)的方式來設定您應用程式所建立的全像


## <a name="implementing-head-gaze"></a>執行頭部

從概念上來說， [前端](../../design/gaze-and-commit.md) 的執行方式是從使用者的標頭投射光線，其中耳機是在正向方向，並決定光線的衝突。
在 Unity 中，使用者的標頭位置和方向會透過 Unity 主要[攝影機](camera-in-unity.md)（特別是[UnityEngine](https://docs.unity3d.com/ScriptReference/Camera-main.html)）公開。[轉換. 轉寄](https://docs.unity3d.com/ScriptReference/Transform-forward.html)和[UnityEngine。](https://docs.unity3d.com/ScriptReference/Camera-main.html)[轉換。位置](https://docs.unity3d.com/ScriptReference/Transform-position.html)。

呼叫 [RayCast](https://docs.unity3d.com/ScriptReference/Physics.Raycast.html) 會產生 [RaycastHit](https://docs.unity3d.com/ScriptReference/RaycastHit.html) 結構，其中包含衝突的相關資訊，包括發生衝突的3d 點，還有另一個 GameObject 的前端光線衝突。

### <a name="example-implement-head-gaze"></a>範例：執行頭部-注視

```cs
void Update()
{
       RaycastHit hitInfo;
       if (Physics.Raycast(
               Camera.main.transform.position,
               Camera.main.transform.forward,
               out hitInfo,
               20.0f,
               Physics.DefaultRaycastLayers))
       {
           // If the Raycast has succeeded and hit a hologram
           // hitInfo's point represents the position being gazed at
           // hitInfo's collider GameObject represents the hologram being gazed at
       }
}
```

### <a name="best-practices"></a>最佳作法

雖然上述範例示範如何在更新迴圈中執行單一 raycast，以尋找使用者前端的目標，但建議您在管理前端的單一物件中執行此動作，而不是在可能對 gazed 物件有興趣的任何物件中執行此動作。 這可讓您的應用程式藉由在每個畫面上執行一個 head raycast 來節省處理。

## <a name="visualizing-head-gaze"></a>將頭部視覺化

就像在您使用滑鼠指標來鎖定內容並與其互動的桌面上一樣，您應該執行代表使用者前端的 [游標](../../design/cursors.md) 。 這可讓使用者在他們即將與其互動的方面具有信賴度。

## <a name="head-gaze-in-the-mixed-reality-toolkit-v2"></a>混合現實工具組 v2 中的頭部
您可以從 MRTK v2 中的 [輸入管理員](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html) 來存取 head。

## <a name="next-development-checkpoint"></a>下一個開發檢查點

如果您要遵循我們所配置的 Unity 開發檢查點旅程，您將在探索 MRTK 核心構成要素。 您可以從這裡繼續進行下一個組建區塊：

> [!div class="nextstepaction"]
> [手勢和運動控制器](gestures-and-motion-controllers-in-unity.md)

或跳至混合的現實平臺功能和 Api：

> [!div class="nextstepaction"]
> [共用體驗](shared-experiences-in-unity.md)

您隨時都可以回到 [Unity 開發檢查點](unity-development-overview.md#2-core-building-blocks) 。

## <a name="see-also"></a>另請參閱
* [相機](camera-in-unity.md)
* [資料指標](../../design/cursors.md)
* [頭部目光和行動](../../design/gaze-and-commit.md)
