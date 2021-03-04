---
title: SceneSystemLightingScenes
description: 場景中光源的相關檔。
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: 753738d8ac1404bb4d959ede108bfd8f4ec4749b
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/03/2021
ms.locfileid: "101783521"
---
# <a name="lighting-scene-operations"></a><span data-ttu-id="365e1-104">光源場景作業</span><span class="sxs-lookup"><span data-stu-id="365e1-104">Lighting scene operations</span></span>

<span data-ttu-id="365e1-105">在啟動時，會載入設定檔中定義的預設光源場景。</span><span class="sxs-lookup"><span data-stu-id="365e1-105">The default lighting scene defined in your profile is loaded on startup.</span></span> <span data-ttu-id="365e1-106">該照明場景會保持載入，直到 `SetLightingScene` 呼叫為止。</span><span class="sxs-lookup"><span data-stu-id="365e1-106">That lighting scene remains loaded until `SetLightingScene` is called.</span></span>

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

sceneSystem.SetLightingScene("MorningLighting");
```

## <a name="lighting-setting-transitions"></a><span data-ttu-id="365e1-107">光源設定轉換</span><span class="sxs-lookup"><span data-stu-id="365e1-107">Lighting setting transitions</span></span>

<span data-ttu-id="365e1-108">`transitionType` 控制轉換到新光源場景的樣式。</span><span class="sxs-lookup"><span data-stu-id="365e1-108">`transitionType` controls the style of the transition to new lighting scene.</span></span>

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

sceneSystem.SetLightingScene("MiddayLighting", LightingSceneTransitionType.CrossFade);
```

<span data-ttu-id="365e1-109">可用的樣式如下：</span><span class="sxs-lookup"><span data-stu-id="365e1-109">The available styles are:</span></span>

<span data-ttu-id="365e1-110">類型</span><span class="sxs-lookup"><span data-stu-id="365e1-110">Type</span></span> | <span data-ttu-id="365e1-111">描述</span><span class="sxs-lookup"><span data-stu-id="365e1-111">Description</span></span> | <span data-ttu-id="365e1-112">持續時間</span><span class="sxs-lookup"><span data-stu-id="365e1-112">Duration</span></span>
--- | --- | ---
<span data-ttu-id="365e1-113">無</span><span class="sxs-lookup"><span data-stu-id="365e1-113">None</span></span> | <span data-ttu-id="365e1-114">先前的光源場景已卸載，已載入新的光源場景。</span><span class="sxs-lookup"><span data-stu-id="365e1-114">Previous lighting scene is unloaded, new lighting scene is loaded.</span></span> <span data-ttu-id="365e1-115">沒有轉換。</span><span class="sxs-lookup"><span data-stu-id="365e1-115">No transition.</span></span> | <span data-ttu-id="365e1-116">忽略</span><span class="sxs-lookup"><span data-stu-id="365e1-116">Ignored</span></span>
<span data-ttu-id="365e1-117">FadeToBlack</span><span class="sxs-lookup"><span data-stu-id="365e1-117">FadeToBlack</span></span> | <span data-ttu-id="365e1-118">上一個光源場景淡出為黑色。</span><span class="sxs-lookup"><span data-stu-id="365e1-118">Previous lighting scene fades out to black.</span></span> <span data-ttu-id="365e1-119">已載入新的光源場景，然後從黑色淡出。</span><span class="sxs-lookup"><span data-stu-id="365e1-119">New lighting scene is loaded, then faded up from black.</span></span> <span data-ttu-id="365e1-120">適用于在位置之間進行平滑轉換。</span><span class="sxs-lookup"><span data-stu-id="365e1-120">Useful for smooth transitions between locations.</span></span> | <span data-ttu-id="365e1-121">已使用</span><span class="sxs-lookup"><span data-stu-id="365e1-121">Used</span></span>
<span data-ttu-id="365e1-122">CrossFade</span><span class="sxs-lookup"><span data-stu-id="365e1-122">CrossFade</span></span> | <span data-ttu-id="365e1-123">當新的燈光場景淡入時，先前的光源場景會淡出。</span><span class="sxs-lookup"><span data-stu-id="365e1-123">Previous lighting scene fades out as new lighting scene fades in.</span></span> <span data-ttu-id="365e1-124">適用于在相同位置中的光源設置之間進行平滑轉換。</span><span class="sxs-lookup"><span data-stu-id="365e1-124">Useful for smooth transitions between lighting setups in the same location.</span></span> | <span data-ttu-id="365e1-125">已使用</span><span class="sxs-lookup"><span data-stu-id="365e1-125">Used</span></span>

<span data-ttu-id="365e1-126">請注意，某些光源設定無法在轉換期間插補。</span><span class="sxs-lookup"><span data-stu-id="365e1-126">Note that some lighting settings cannot be interpolated during transitions.</span></span> <span data-ttu-id="365e1-127">如果您想要有平滑的視覺效果轉換，這些設定必須在燈光場景之間保持一致。</span><span class="sxs-lookup"><span data-stu-id="365e1-127">If you want a smooth visual transition these settings will have to remain consistent between lighting scenes.</span></span>

<span data-ttu-id="365e1-128">設定</span><span class="sxs-lookup"><span data-stu-id="365e1-128">Setting</span></span> | <span data-ttu-id="365e1-129">平滑 FadeToBlack 轉換</span><span class="sxs-lookup"><span data-stu-id="365e1-129">Smooth FadeToBlack Transition</span></span> | <span data-ttu-id="365e1-130">平滑 CrossFade 轉換</span><span class="sxs-lookup"><span data-stu-id="365e1-130">Smooth CrossFade Transition</span></span>
--- | --- | ---
<span data-ttu-id="365e1-131">Skybox</span><span class="sxs-lookup"><span data-stu-id="365e1-131">Skybox</span></span> | <span data-ttu-id="365e1-132">否</span><span class="sxs-lookup"><span data-stu-id="365e1-132">No</span></span> | <span data-ttu-id="365e1-133">否</span><span class="sxs-lookup"><span data-stu-id="365e1-133">No</span></span>
<span data-ttu-id="365e1-134">自訂反射</span><span class="sxs-lookup"><span data-stu-id="365e1-134">Custom Reflections</span></span> | <span data-ttu-id="365e1-135">否</span><span class="sxs-lookup"><span data-stu-id="365e1-135">No</span></span> | <span data-ttu-id="365e1-136">否</span><span class="sxs-lookup"><span data-stu-id="365e1-136">No</span></span>
<span data-ttu-id="365e1-137">Sun light 即時陰影</span><span class="sxs-lookup"><span data-stu-id="365e1-137">Sun light realtime shadows</span></span> | <span data-ttu-id="365e1-138">是</span><span class="sxs-lookup"><span data-stu-id="365e1-138">Yes</span></span> | <span data-ttu-id="365e1-139">否</span><span class="sxs-lookup"><span data-stu-id="365e1-139">No</span></span>
