---
title: Unity 中的目光
description: 瞭解如何使用「注視輸入」作為主要方式，讓使用者將應用程式所建立的全像是以混合現實的形式來設定。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: 眼睛、中眼、unity、全息全像、混合式現實、混合現實耳機、windows mixed reality 耳機、虛擬實境耳機、MRTK、混合現實工具組
ms.openlocfilehash: f10079d36f737e5d8a2ee74a88ca0f8b2b3d791c
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600147"
---
# <a name="head-gaze-in-unity"></a>Unity 中的頭部

[注視](../../design/gaze-and-commit.md)是讓您的應用程式以[混合現實](../../discover/mixed-reality.md)的方式來鎖定您的應用[程式所建立](../../discover/hologram.md)的主要方式。

## <a name="implementing-head-gaze"></a>執行頭部

在概念上，您可以從使用者的耳機投射光線，以查看其點擊的內容，藉以判斷 [head](../../design/gaze-and-commit.md) 。 在 Unity 中，使用者的標頭位置和方向會透過[相機](camera-in-unity.md)（特別是[UnityEngine](https://docs.unity3d.com/ScriptReference/Camera-main.html)）公開。[轉換. 轉寄](https://docs.unity3d.com/ScriptReference/Transform-forward.html)和[UnityEngine。](https://docs.unity3d.com/ScriptReference/Camera-main.html)[轉換。位置](https://docs.unity3d.com/ScriptReference/Transform-position.html)。

呼叫 [RayCast](https://docs.unity3d.com/ScriptReference/Physics.Raycast.html) 可為您提供一個 [RaycastHit](https://docs.unity3d.com/ScriptReference/RaycastHit.html) ，其中包含衝突的相關資訊，包括3d 衝突點以及另一個 GameObject 的前端光線點擊。

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

### <a name="best-practices"></a>最佳做法

雖然上述範例會從更新迴圈引發單一 raycast，以找出使用者的標頭的目標，我們建議使用單一物件來管理所有的前端進程。 結合您的列印頭邏輯可節省您的應用程式珍貴處理能力，並將您的 raycasting 限制為每個畫面一個。

## <a name="visualizing-head-gaze"></a>將頭部視覺化

就像電腦上的滑鼠指標一樣，您應該執行代表使用者前端的 [游標](../../design/cursors.md) 。 知道使用者的目標內容會讓他們即將與其互動的內容更加可靠。

## <a name="head-gaze-in-the-mixed-reality-toolkit"></a>混合現實工具組中的頭部

您可以從 MRTK 的 [輸入管理員](/windows/mixed-reality/mrtk-unity/features/input/overview) 存取前端。

## <a name="next-development-checkpoint"></a>下一個開發檢查點

如果您是遵循我們所配置的 Unity 開發旅程，您將會在探索 MRTK 核心構成要素的過程中進行。 接下來，您可以繼續進行下一個建置組塊：

> [!div class="nextstepaction"]
> [運動控制器](motion-controllers-in-unity.md)

或者，直接跳到混合實境平台功能和 API 的主題：

> [!div class="nextstepaction"]
> [共用體驗](shared-experiences-in-unity.md)

您可以隨時回到 [Unity 開發檢查點](unity-development-overview.md#2-core-building-blocks)。

## <a name="see-also"></a>另請參閱
* [相機](camera-in-unity.md)
* [資料指標](../../design/cursors.md)
* [頭部目光和行動](../../design/gaze-and-commit.md)