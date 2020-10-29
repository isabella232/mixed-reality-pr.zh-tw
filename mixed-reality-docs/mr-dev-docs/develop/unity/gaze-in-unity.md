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
# <a name="head-gaze-in-unity"></a><span data-ttu-id="d9471-104">Unity 中的頭部</span><span class="sxs-lookup"><span data-stu-id="d9471-104">Head-gaze in Unity</span></span>

<span data-ttu-id="d9471-105">「[注視](../../design/gaze-and-commit.md)」是一種主要方式，可[讓使用者](../../discover/hologram.md)以[混合現實](../../discover/mixed-reality.md)的方式來設定您應用程式所建立的全像</span><span class="sxs-lookup"><span data-stu-id="d9471-105">[Gaze](../../design/gaze-and-commit.md) is a primary way for users to target the [holograms](../../discover/hologram.md) your app creates in [Mixed Reality](../../discover/mixed-reality.md).</span></span>


## <a name="implementing-head-gaze"></a><span data-ttu-id="d9471-106">執行頭部</span><span class="sxs-lookup"><span data-stu-id="d9471-106">Implementing head-gaze</span></span>

<span data-ttu-id="d9471-107">從概念上來說， [前端](../../design/gaze-and-commit.md) 的執行方式是從使用者的標頭投射光線，其中耳機是在正向方向，並決定光線的衝突。</span><span class="sxs-lookup"><span data-stu-id="d9471-107">Conceptually, [head-gaze](../../design/gaze-and-commit.md) is implemented by projecting a ray from the user's head where the headset is, in the forward direction they are facing and determining what that ray collides with.</span></span>
<span data-ttu-id="d9471-108">在 Unity 中，使用者的標頭位置和方向會透過 Unity 主要[攝影機](camera-in-unity.md)（特別是[UnityEngine](https://docs.unity3d.com/ScriptReference/Camera-main.html)）公開。[轉換. 轉寄](https://docs.unity3d.com/ScriptReference/Transform-forward.html)和[UnityEngine。](https://docs.unity3d.com/ScriptReference/Camera-main.html)[轉換。位置](https://docs.unity3d.com/ScriptReference/Transform-position.html)。</span><span class="sxs-lookup"><span data-stu-id="d9471-108">In Unity, the user's head position and direction are exposed through the Unity Main [Camera](camera-in-unity.md), specifically [UnityEngine.Camera.main](https://docs.unity3d.com/ScriptReference/Camera-main.html).[transform.forward](https://docs.unity3d.com/ScriptReference/Transform-forward.html) and [UnityEngine.Camera.main](https://docs.unity3d.com/ScriptReference/Camera-main.html).[transform.position](https://docs.unity3d.com/ScriptReference/Transform-position.html).</span></span>

<span data-ttu-id="d9471-109">呼叫 [RayCast](https://docs.unity3d.com/ScriptReference/Physics.Raycast.html) 會產生 [RaycastHit](https://docs.unity3d.com/ScriptReference/RaycastHit.html) 結構，其中包含衝突的相關資訊，包括發生衝突的3d 點，還有另一個 GameObject 的前端光線衝突。</span><span class="sxs-lookup"><span data-stu-id="d9471-109">Calling [Physics.RayCast](https://docs.unity3d.com/ScriptReference/Physics.Raycast.html) results in a [RaycastHit](https://docs.unity3d.com/ScriptReference/RaycastHit.html) structure which contains information about the collision including the 3D point where collision occurred and the other GameObject the head-gaze ray collided with.</span></span>

### <a name="example-implement-head-gaze"></a><span data-ttu-id="d9471-110">範例：執行頭部-注視</span><span class="sxs-lookup"><span data-stu-id="d9471-110">Example: Implement head-gaze</span></span>

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

### <a name="best-practices"></a><span data-ttu-id="d9471-111">最佳作法</span><span class="sxs-lookup"><span data-stu-id="d9471-111">Best practices</span></span>

<span data-ttu-id="d9471-112">雖然上述範例示範如何在更新迴圈中執行單一 raycast，以尋找使用者前端的目標，但建議您在管理前端的單一物件中執行此動作，而不是在可能對 gazed 物件有興趣的任何物件中執行此動作。</span><span class="sxs-lookup"><span data-stu-id="d9471-112">While the example above demonstrates how to do a single raycast in an update loop to find the target the user's head points at, it is recommended to do this in a single object managing head-gaze instead of doing this in any object that is potentially interested in the object being gazed at.</span></span> <span data-ttu-id="d9471-113">這可讓您的應用程式藉由在每個畫面上執行一個 head raycast 來節省處理。</span><span class="sxs-lookup"><span data-stu-id="d9471-113">This lets your app save processing by doing just one head-gaze raycast each frame.</span></span>

## <a name="visualizing-head-gaze"></a><span data-ttu-id="d9471-114">將頭部視覺化</span><span class="sxs-lookup"><span data-stu-id="d9471-114">Visualizing head-gaze</span></span>

<span data-ttu-id="d9471-115">就像在您使用滑鼠指標來鎖定內容並與其互動的桌面上一樣，您應該執行代表使用者前端的 [游標](../../design/cursors.md) 。</span><span class="sxs-lookup"><span data-stu-id="d9471-115">Just like on the desktop where you use a mouse pointer to target and interact with content, you should implement a [cursor](../../design/cursors.md) that represents the user's head-gaze.</span></span> <span data-ttu-id="d9471-116">這可讓使用者在他們即將與其互動的方面具有信賴度。</span><span class="sxs-lookup"><span data-stu-id="d9471-116">This gives the user confidence in what they're about to interact with.</span></span>

## <a name="head-gaze-in-the-mixed-reality-toolkit-v2"></a><span data-ttu-id="d9471-117">混合現實工具組 v2 中的頭部</span><span class="sxs-lookup"><span data-stu-id="d9471-117">Head-gaze in the Mixed Reality Toolkit v2</span></span>
<span data-ttu-id="d9471-118">您可以從 MRTK v2 中的 [輸入管理員](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html) 來存取 head。</span><span class="sxs-lookup"><span data-stu-id="d9471-118">You can access head-gaze from the [Input Manager](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html) in MRTK v2.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="d9471-119">下一個開發檢查點</span><span class="sxs-lookup"><span data-stu-id="d9471-119">Next Development Checkpoint</span></span>

<span data-ttu-id="d9471-120">如果您要遵循我們所配置的 Unity 開發檢查點旅程，您將在探索 MRTK 核心構成要素。</span><span class="sxs-lookup"><span data-stu-id="d9471-120">If you're following the Unity development checkpoint journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="d9471-121">您可以從這裡繼續進行下一個組建區塊：</span><span class="sxs-lookup"><span data-stu-id="d9471-121">From here, you can proceed to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="d9471-122">手勢和運動控制器</span><span class="sxs-lookup"><span data-stu-id="d9471-122">Gestures and motion controllers</span></span>](gestures-and-motion-controllers-in-unity.md)

<span data-ttu-id="d9471-123">或跳至混合的現實平臺功能和 Api：</span><span class="sxs-lookup"><span data-stu-id="d9471-123">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="d9471-124">共用體驗</span><span class="sxs-lookup"><span data-stu-id="d9471-124">Shared experiences</span></span>](shared-experiences-in-unity.md)

<span data-ttu-id="d9471-125">您隨時都可以回到 [Unity 開發檢查點](unity-development-overview.md#2-core-building-blocks) 。</span><span class="sxs-lookup"><span data-stu-id="d9471-125">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="d9471-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d9471-126">See also</span></span>
* [<span data-ttu-id="d9471-127">相機</span><span class="sxs-lookup"><span data-stu-id="d9471-127">Camera</span></span>](camera-in-unity.md)
* [<span data-ttu-id="d9471-128">資料指標</span><span class="sxs-lookup"><span data-stu-id="d9471-128">Cursors</span></span>](../../design/cursors.md)
* [<span data-ttu-id="d9471-129">頭部目光和行動</span><span class="sxs-lookup"><span data-stu-id="d9471-129">Head-gaze and commit</span></span>](../../design/gaze-and-commit.md)
