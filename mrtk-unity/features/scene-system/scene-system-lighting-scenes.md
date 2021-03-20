---
title: SceneSystemLightingScenes
description: 場景中光源的相關檔。
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: 4cd6b61172f03da99ba33a06d06e20f095572622
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104688358"
---
# <a name="lighting-scene-operations"></a>光源場景作業

在啟動時，會載入設定檔中定義的預設光源場景。 該照明場景會保持載入，直到 `SetLightingScene` 呼叫為止。

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

sceneSystem.SetLightingScene("MorningLighting");
```

## <a name="lighting-setting-transitions"></a>光源設定轉換

`transitionType` 控制轉換到新光源場景的樣式。

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

sceneSystem.SetLightingScene("MiddayLighting", LightingSceneTransitionType.CrossFade);
```

可用的樣式如下：

類型 | Description | 持續時間
--- | --- | ---
無 | 先前的光源場景已卸載，已載入新的光源場景。 沒有轉換。 | 忽略
FadeToBlack | 上一個光源場景淡出為黑色。 已載入新的光源場景，然後從黑色淡出。 適用于在位置之間進行平滑轉換。 | 已使用
CrossFade | 當新的燈光場景淡入時，先前的光源場景會淡出。 適用于在相同位置中的光源設置之間進行平滑轉換。 | 已使用

請注意，某些光源設定無法在轉換期間插補。 如果您想要有平滑的視覺效果轉換，這些設定必須在燈光場景之間保持一致。

設定 | 平滑 FadeToBlack 轉換 | 平滑 CrossFade 轉換
--- | --- | ---
Skybox | 否 | 否
自訂反射 | 否 | 否
Sun light 即時陰影 | 是 | 否
