---
title: README_ScrollingObject
description: MRTK 中的描述滾動物件集合。
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: dea20e9df9c00207b2a9b1c6b5a893fa357de755
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/03/2021
ms.locfileid: "101779506"
---
# <a name="scrolling-object-collection"></a><span data-ttu-id="98f94-104">滾動物件集合</span><span class="sxs-lookup"><span data-stu-id="98f94-104">Scrolling object collection</span></span>

![滾動收集](../../features/Images/ScrollingCollection/MRTK_UX_ScrollingCollection_Main.jpg)

<span data-ttu-id="98f94-106">ScrollingObjectCollection 是原生滾動3D 物件的物件集合。</span><span class="sxs-lookup"><span data-stu-id="98f94-106">The ScrollingObjectCollection is an Object Collection that natively scrolls 3D objects.</span></span> <span data-ttu-id="98f94-107">它支援滾動 pressable 按鈕和 Interactables，以及非互動式物件。</span><span class="sxs-lookup"><span data-stu-id="98f94-107">It supports scrolling pressable buttons and Interactables as well as non-interactive objects.</span></span> <span data-ttu-id="98f94-108">此集合支援近和遠的輸入。</span><span class="sxs-lookup"><span data-stu-id="98f94-108">This collection supports both near and far input.</span></span> <span data-ttu-id="98f94-109">若要使用 ScrollingObjectCollection，物件必須使用 MRTK 標準著色器，才能讓剪切效果正常運作。</span><span class="sxs-lookup"><span data-stu-id="98f94-109">In order to use ScrollingObjectCollection, objects must use the MRTK Standard Shader in order for the clipping effect to work properly.</span></span>

## <a name="getting-started-with-scrolling-object-collection"></a><span data-ttu-id="98f94-110">開始使用滾動物件集合</span><span class="sxs-lookup"><span data-stu-id="98f94-110">Getting started with scrolling object collection</span></span>

<span data-ttu-id="98f94-111">為了方便起見，有兩個 ScrollingObjectCollection Prefabs 可供使用。</span><span class="sxs-lookup"><span data-stu-id="98f94-111">For convenience, there are two ScrollingObjectCollection Prefabs available to use.</span></span> <span data-ttu-id="98f94-112">其中一個設定為使用 32x92mm PressableButton prefabs，另一個則適用于32x32x32mm 容器中的任何物件。</span><span class="sxs-lookup"><span data-stu-id="98f94-112">One is configured to work with 32x92mm PressableButton prefabs, and the other is for any object in a 32x32x32mm container.</span></span>

<span data-ttu-id="98f94-113">只要將這些 prefabs 放入場景中，加入所需的物件，然後按 "UpdateCollection"，即可完成集合的設定和配置。</span><span class="sxs-lookup"><span data-stu-id="98f94-113">Simply drop these prefabs into a scene, add the desired objects, and press "UpdateCollection" to finalize the set up and layout of the Collection.</span></span>

### <a name="prerequisites"></a><span data-ttu-id="98f94-114">必要條件</span><span class="sxs-lookup"><span data-stu-id="98f94-114">Prerequisites</span></span>

- <span data-ttu-id="98f94-115">集合中的所有物件都必須使用 MRTK 標準著色器</span><span class="sxs-lookup"><span data-stu-id="98f94-115">All objects in collection must use the MRTK standard shader</span></span>
- <span data-ttu-id="98f94-116">集合中的每個物件都必須具有具有的碰撞 [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) 。</span><span class="sxs-lookup"><span data-stu-id="98f94-116">Every object in the collection must have a collider with a [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable).</span></span> <span data-ttu-id="98f94-117">所有的衝突測試目前都是使用這些 colliders 來完成;ScrollingObjectCollection 尚不支援靜態/nonmoving 支援碰撞。</span><span class="sxs-lookup"><span data-stu-id="98f94-117">All collision testing is currently done using these colliders; ScrollingObjectCollection does not yet support a static/nonmoving backing collider.</span></span>
- <span data-ttu-id="98f94-118">集合中的所有物件目前都必須是相同的大小，此外，如果您的物件不是在 gameObject 中，您可能會得到非預期的結果。</span><span class="sxs-lookup"><span data-stu-id="98f94-118">All objects in collection need to be the same size currently, additionally you may get unexpected results if your objects aren't centered in a gameObject.</span></span>
- <span data-ttu-id="98f94-119">針對無縫可觸式介面，滾動集合中的「資料格大小」應該符合集合中每個物件的大小。</span><span class="sxs-lookup"><span data-stu-id="98f94-119">For a seamless touchable surface, the 'cell size' in the scrolling collection should match the size of every object in the collection.</span></span>

<span data-ttu-id="98f94-120">使用按鈕時有其他需求：</span><span class="sxs-lookup"><span data-stu-id="98f94-120">There are additional requirements when using buttons:</span></span>

- <span data-ttu-id="98f94-121">必須停用 PressableButton。 ReleaseOnTouch。</span><span class="sxs-lookup"><span data-stu-id="98f94-121">PressableButton.ReleaseOnTouch must be disabled.</span></span>
- <span data-ttu-id="98f94-122">PhysicalPressEventRouter. InteractableOnClick 最多可設定為 EventOnClickCompletion 或 EventOnPress。</span><span class="sxs-lookup"><span data-stu-id="98f94-122">PhysicalPressEventRouter.InteractableOnClick most be set to EventOnClickCompletion or EventOnPress.</span></span>
- <span data-ttu-id="98f94-123">在編輯時，ScrollingObjectCollection 可以自動修正這些元件。</span><span class="sxs-lookup"><span data-stu-id="98f94-123">At edit time, ScrollingObjectCollection can automatically fix these components.</span></span> <span data-ttu-id="98f94-124">但是，當動態具現化 Prefabs 或元件時，請確定已正確設定這些屬性。</span><span class="sxs-lookup"><span data-stu-id="98f94-124">But when dynamically instantiating Prefabs or components, make sure these properties are set properly.</span></span>

## <a name="how-it-works"></a><span data-ttu-id="98f94-125">運作方式</span><span class="sxs-lookup"><span data-stu-id="98f94-125">How it works</span></span>

<span data-ttu-id="98f94-126">ScrollingObjectCollection 會將本身訂閱為觸控和指標事件的全域接聽程式，以篩選對應至清單中專案的事件。</span><span class="sxs-lookup"><span data-stu-id="98f94-126">ScrollingObjectCollection subscribes itself as a global listener for Touch and Pointer events, filtering for events that correspond to the items in the list.</span></span> <span data-ttu-id="98f94-127">一開始，集合不會執行任何動作，並讓事件傳遞至子物件，如此可讓子物件如預期般主角和選取。</span><span class="sxs-lookup"><span data-stu-id="98f94-127">Initially, the Collection doesn't do anything and lets events pass through to the child objects, this allows child objects to be poked and selected as expected.</span></span> <span data-ttu-id="98f94-128">一旦 ScrollingObjectCollection 將互動視為「拖曳」之後，集合就會開始將所有後續的 eventData 標示為已使用，並開始在設定軸上滾動清單。</span><span class="sxs-lookup"><span data-stu-id="98f94-128">Once the ScrollingObjectCollection has deemed an interaction as a "drag", the collection begins marking all subsequent eventData as used and begins scrolling the list on the set axis.</span></span>

<span data-ttu-id="98f94-129">使用觸控時，清單會繼續滾動，直到 PokePointer 超過清單前方的觸控平面為止。</span><span class="sxs-lookup"><span data-stu-id="98f94-129">When using touch, the list will continue to scroll, until the PokePointer has crossed the touch plane in front of the list.</span></span>
