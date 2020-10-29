---
title: 著色器
description: MRTK 標準著色器提供各種類型的視覺效果，可搭配全像全像使用。
author: cre8ivepark
ms.author: dongpark
ms.date: 11/01/2019
ms.topic: article
keywords: 混合的現實、控制項、互動、ui、ux
ms.openlocfilehash: 86e56de93736c90f3b28467a0ecd6e18a1ba0146
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2020
ms.locfileid: "91679413"
---
# <a name="shader"></a><span data-ttu-id="15f72-104">著色器</span><span class="sxs-lookup"><span data-stu-id="15f72-104">Shader</span></span>

![著色器](images/UX_Hero_StandardShader.jpg)

<span data-ttu-id="15f72-106">因為全像真實環境中的實體物件會混合使用，所以請務必提供視覺提示給使用者。</span><span class="sxs-lookup"><span data-stu-id="15f72-106">Since holographic objects are mixed with physical ones in the real environment, it's important to provide visual cues to the user.</span></span> <span data-ttu-id="15f72-107">MRTK 標準著色器提供各種類型的視覺效果，可搭配全像全像使用。</span><span class="sxs-lookup"><span data-stu-id="15f72-107">The MRTK Standard shader provides various types of visual effects that can be used with holograms.</span></span> <span data-ttu-id="15f72-108">MRTK 標準陰影系統利用單一、彈性的著色器，其可達成與 Unity 標準著色器類似的視覺效果、實行 [Fluent Design 系統準則](https://www.microsoft.com/design/fluent/#/)，並在混合現實裝置上維持效能。</span><span class="sxs-lookup"><span data-stu-id="15f72-108">The MRTK Standard shading system utilizes a single, flexible shader that can achieve visuals similar to Unity's Standard Shader, implements [Fluent Design System principles](https://www.microsoft.com/design/fluent/#/), and remains performant on mixed reality devices.</span></span>
<br>

## <a name="examples-of-visual-effects-using-mrtk-standard-shader"></a><span data-ttu-id="15f72-109">使用 MRTK 標準著色器的視覺效果範例</span><span class="sxs-lookup"><span data-stu-id="15f72-109">Examples of visual effects using MRTK Standard shader</span></span> 
:::row:::
    :::column:::
       <span data-ttu-id="15f72-110">![移動](images/UX_Button_Affordance_ProximityLight.jpg)</span><span class="sxs-lookup"><span data-stu-id="15f72-110">![Move](images/UX_Button_Affordance_ProximityLight.jpg)</span></span><br>
       <span data-ttu-id="15f72-111">**近亮光**</span><span class="sxs-lookup"><span data-stu-id="15f72-111">**Proximity light**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="15f72-112">![旋轉](images/UX_Button_Affordance_FocusHighlight.jpg)</span><span class="sxs-lookup"><span data-stu-id="15f72-112">![Rotate](images/UX_Button_Affordance_FocusHighlight.jpg)</span></span><br>
        <span data-ttu-id="15f72-113">**框線燈**</span><span class="sxs-lookup"><span data-stu-id="15f72-113">**Border light**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="mrtk-standard-shader-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="15f72-114">在 MRTK 中 MRTK 標準著色器 (Unity 的混合現實工具組) </span><span class="sxs-lookup"><span data-stu-id="15f72-114">MRTK Standard shader in MRTK (Mixed Reality Toolkit) for Unity</span></span>

* [<span data-ttu-id="15f72-115">MRTK-標準著色器</span><span class="sxs-lookup"><span data-stu-id="15f72-115">MRTK - Standard shader</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html)


<br>

---

## <a name="see-also"></a><span data-ttu-id="15f72-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="15f72-116">See also</span></span>

* [<span data-ttu-id="15f72-117">游標</span><span class="sxs-lookup"><span data-stu-id="15f72-117">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="15f72-118">手部光線</span><span class="sxs-lookup"><span data-stu-id="15f72-118">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="15f72-119">Button</span><span class="sxs-lookup"><span data-stu-id="15f72-119">Button</span></span>](button.md)
* [<span data-ttu-id="15f72-120">可互動的物件</span><span class="sxs-lookup"><span data-stu-id="15f72-120">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="15f72-121">週框方塊和應用程式列</span><span class="sxs-lookup"><span data-stu-id="15f72-121">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="15f72-122">操作</span><span class="sxs-lookup"><span data-stu-id="15f72-122">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="15f72-123">手部功能表</span><span class="sxs-lookup"><span data-stu-id="15f72-123">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="15f72-124">近端功能表</span><span class="sxs-lookup"><span data-stu-id="15f72-124">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="15f72-125">物件集合</span><span class="sxs-lookup"><span data-stu-id="15f72-125">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="15f72-126">語音命令</span><span class="sxs-lookup"><span data-stu-id="15f72-126">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="15f72-127">鍵盤</span><span class="sxs-lookup"><span data-stu-id="15f72-127">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="15f72-128">工具提示</span><span class="sxs-lookup"><span data-stu-id="15f72-128">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="15f72-129">平板</span><span class="sxs-lookup"><span data-stu-id="15f72-129">Slate</span></span>](slate.md)
* [<span data-ttu-id="15f72-130">滑桿</span><span class="sxs-lookup"><span data-stu-id="15f72-130">Slider</span></span>](slider.md)
* [<span data-ttu-id="15f72-131">佈告板和常駐標籤</span><span class="sxs-lookup"><span data-stu-id="15f72-131">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="15f72-132">顯示進度</span><span class="sxs-lookup"><span data-stu-id="15f72-132">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="15f72-133">表面磁性</span><span class="sxs-lookup"><span data-stu-id="15f72-133">Surface magnetism</span></span>](surface-magnetism.md)
