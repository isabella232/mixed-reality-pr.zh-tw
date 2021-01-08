---
title: Unity 中的目光
description: 瞭解如何使用「注視輸入」作為主要方式，讓使用者將應用程式所建立的全像是以混合現實的形式來設定。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: 眼睛、中眼、unity、全息全像、混合式現實、混合現實耳機、windows mixed reality 耳機、虛擬實境耳機、MRTK、混合現實工具組
ms.openlocfilehash: 5dab8cb38aaa4b9a4547f4bf494afb093b6d8058
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009888"
---
# <a name="head-gaze-in-unity"></a><span data-ttu-id="cbf0e-104">Unity 中的頭部</span><span class="sxs-lookup"><span data-stu-id="cbf0e-104">Head-gaze in Unity</span></span>

<span data-ttu-id="cbf0e-105">[注視](../../design/gaze-and-commit.md)是讓您的應用程式以[混合現實](../../discover/mixed-reality.md)的方式來鎖定您的應用[程式所建立](../../discover/hologram.md)的主要方式。</span><span class="sxs-lookup"><span data-stu-id="cbf0e-105">[Gaze](../../design/gaze-and-commit.md) is the primary way for users to target [holograms](../../discover/hologram.md) your app creates in [Mixed Reality](../../discover/mixed-reality.md).</span></span>

## <a name="implementing-head-gaze"></a><span data-ttu-id="cbf0e-106">執行頭部</span><span class="sxs-lookup"><span data-stu-id="cbf0e-106">Implementing head-gaze</span></span>

<span data-ttu-id="cbf0e-107">在概念上，您可以從使用者的耳機投射光線，以查看其點擊的內容，藉以判斷 [head](../../design/gaze-and-commit.md) 。</span><span class="sxs-lookup"><span data-stu-id="cbf0e-107">Conceptually, you determine [head-gaze](../../design/gaze-and-commit.md) by projecting a ray forward from the user's headset to see what it hits.</span></span> <span data-ttu-id="cbf0e-108">在 Unity 中，使用者的標頭位置和方向會透過[相機](camera-in-unity.md)（特別是[UnityEngine](https://docs.unity3d.com/ScriptReference/Camera-main.html)）公開。[轉換. 轉寄](https://docs.unity3d.com/ScriptReference/Transform-forward.html)和[UnityEngine。](https://docs.unity3d.com/ScriptReference/Camera-main.html)[轉換。位置](https://docs.unity3d.com/ScriptReference/Transform-position.html)。</span><span class="sxs-lookup"><span data-stu-id="cbf0e-108">In Unity, the user's head position and direction are exposed through the [Camera](camera-in-unity.md), specifically [UnityEngine.Camera.main](https://docs.unity3d.com/ScriptReference/Camera-main.html).[transform.forward](https://docs.unity3d.com/ScriptReference/Transform-forward.html) and [UnityEngine.Camera.main](https://docs.unity3d.com/ScriptReference/Camera-main.html).[transform.position](https://docs.unity3d.com/ScriptReference/Transform-position.html).</span></span>

<span data-ttu-id="cbf0e-109">呼叫 [RayCast](https://docs.unity3d.com/ScriptReference/Physics.Raycast.html) 可為您提供一個 [RaycastHit](https://docs.unity3d.com/ScriptReference/RaycastHit.html) ，其中包含衝突的相關資訊，包括3d 衝突點以及另一個 GameObject 的前端光線點擊。</span><span class="sxs-lookup"><span data-stu-id="cbf0e-109">Calling [Physics.RayCast](https://docs.unity3d.com/ScriptReference/Physics.Raycast.html) gives you a [RaycastHit](https://docs.unity3d.com/ScriptReference/RaycastHit.html) containing information about the collision, including the 3D collision point and the other GameObject the head-gaze ray hit.</span></span>

### <a name="example-implement-head-gaze"></a><span data-ttu-id="cbf0e-110">範例：執行頭部-注視</span><span class="sxs-lookup"><span data-stu-id="cbf0e-110">Example: Implement head-gaze</span></span>

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

### <a name="best-practices"></a><span data-ttu-id="cbf0e-111">最佳作法</span><span class="sxs-lookup"><span data-stu-id="cbf0e-111">Best practices</span></span>

<span data-ttu-id="cbf0e-112">雖然上述範例會從更新迴圈引發單一 raycast，以找出使用者的標頭的目標，我們建議使用單一物件來管理所有的前端進程。</span><span class="sxs-lookup"><span data-stu-id="cbf0e-112">While the example above fires a single raycast from the update loop to find the target the user's head points at, we recommended using a single object to manage all head-gaze processes.</span></span> <span data-ttu-id="cbf0e-113">結合您的列印頭邏輯可節省您的應用程式珍貴處理能力，並將您的 raycasting 限制為每個畫面一個。</span><span class="sxs-lookup"><span data-stu-id="cbf0e-113">Combining your head-gaze logic will save your app precious processing power and limit your raycasting to one per frame.</span></span>

## <a name="visualizing-head-gaze"></a><span data-ttu-id="cbf0e-114">將頭部視覺化</span><span class="sxs-lookup"><span data-stu-id="cbf0e-114">Visualizing head-gaze</span></span>

<span data-ttu-id="cbf0e-115">就像電腦上的滑鼠指標一樣，您應該執行代表使用者前端的 [游標](../../design/cursors.md) 。</span><span class="sxs-lookup"><span data-stu-id="cbf0e-115">Just like with a mouse pointer on a computer, you should implement a [cursor](../../design/cursors.md) that represents the user's head-gaze.</span></span> <span data-ttu-id="cbf0e-116">知道使用者的目標內容會讓他們即將與其互動的內容更加可靠。</span><span class="sxs-lookup"><span data-stu-id="cbf0e-116">Knowing what content a user is targeting increases confidence in what they're about to interact with.</span></span>

## <a name="head-gaze-in-the-mixed-reality-toolkit"></a><span data-ttu-id="cbf0e-117">混合現實工具組中的頭部</span><span class="sxs-lookup"><span data-stu-id="cbf0e-117">Head-gaze in the Mixed Reality Toolkit</span></span> 
<span data-ttu-id="cbf0e-118">您可以從 MRTK 的 [輸入管理員](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html) 存取前端。</span><span class="sxs-lookup"><span data-stu-id="cbf0e-118">You can access head-gaze from the [Input Manager](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html) in MRTK.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="cbf0e-119">下一個開發檢查點</span><span class="sxs-lookup"><span data-stu-id="cbf0e-119">Next Development Checkpoint</span></span>

<span data-ttu-id="cbf0e-120">如果您是遵循我們所配置的 Unity 開發旅程，您將會在探索 MRTK 核心構成要素的過程中進行。</span><span class="sxs-lookup"><span data-stu-id="cbf0e-120">If you're following the Unity development journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="cbf0e-121">接下來，您可以繼續進行下一個建置組塊：</span><span class="sxs-lookup"><span data-stu-id="cbf0e-121">From here, you can continue to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="cbf0e-122">手勢和運動控制器</span><span class="sxs-lookup"><span data-stu-id="cbf0e-122">Gestures and motion controllers</span></span>](gestures-and-motion-controllers-in-unity.md)

<span data-ttu-id="cbf0e-123">或者，直接跳到混合實境平台功能和 API 的主題：</span><span class="sxs-lookup"><span data-stu-id="cbf0e-123">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="cbf0e-124">共用體驗</span><span class="sxs-lookup"><span data-stu-id="cbf0e-124">Shared experiences</span></span>](shared-experiences-in-unity.md)

<span data-ttu-id="cbf0e-125">您可以隨時回到 [Unity 開發檢查點](unity-development-overview.md#2-core-building-blocks)。</span><span class="sxs-lookup"><span data-stu-id="cbf0e-125">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="cbf0e-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cbf0e-126">See also</span></span>
* [<span data-ttu-id="cbf0e-127">相機</span><span class="sxs-lookup"><span data-stu-id="cbf0e-127">Camera</span></span>](camera-in-unity.md)
* [<span data-ttu-id="cbf0e-128">資料指標</span><span class="sxs-lookup"><span data-stu-id="cbf0e-128">Cursors</span></span>](../../design/cursors.md)
* [<span data-ttu-id="cbf0e-129">頭部目光和行動</span><span class="sxs-lookup"><span data-stu-id="cbf0e-129">Head-gaze and commit</span></span>](../../design/gaze-and-commit.md)
