---
title: Unity 中的目光
description: 「注視」是一種主要方式，可讓使用者以混合現實的方式來設定您應用程式所建立的全像
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: 眼睛、中眼、unity、全息全像、混合式現實、混合現實耳機、windows mixed reality 耳機、虛擬實境耳機、MRTK、混合現實工具組
ms.openlocfilehash: 0c62de9cb1b7ea892831ea2cedbeb23be5ea7b37
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2020
ms.locfileid: "94677507"
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

依循我們配置的 Unity 開發檢查點旅程，此時您會探索 MRTK核心建置組塊。 接下來，您可以繼續進行下一個建置組塊：

> [!div class="nextstepaction"]
> [手勢和運動控制器](gestures-and-motion-controllers-in-unity.md)

或者，直接跳到混合實境平台功能和 API 的主題：

> [!div class="nextstepaction"]
> [共用體驗](shared-experiences-in-unity.md)

您可以隨時回到 [Unity 開發檢查點](unity-development-overview.md#2-core-building-blocks)。

## <a name="see-also"></a>另請參閱
* [相機](camera-in-unity.md)
* [資料指標](../../design/cursors.md)
* [頭部目光和行動](../../design/gaze-and-commit.md)
