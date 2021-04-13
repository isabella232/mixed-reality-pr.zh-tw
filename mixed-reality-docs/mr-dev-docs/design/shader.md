---
title: 著色器
description: 瞭解混合現實工具組標準著色器如何提供各種類型的視覺效果，可搭配您的混合現實應用程式中的全像影像使用。
author: cre8ivepark
ms.author: dongpark
ms.date: 11/01/2019
ms.topic: article
keywords: 混合的現實、控制項、互動、ui、ux、著色器、混合現實耳機、windows mixed Reality 耳機、虛擬實境耳機、HoloLens、MRTK、混合現實工具組、視覺效果
ms.openlocfilehash: 4bf8205ac9dfbd22a0deb9ffe796fd4e33a96f89
ms.sourcegitcommit: 1c9035487270af76c6eaba11b11f6fc56c008135
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/13/2021
ms.locfileid: "107300383"
---
# <a name="shader"></a><span data-ttu-id="dab82-104">著色器</span><span class="sxs-lookup"><span data-stu-id="dab82-104">Shader</span></span>

![著色器](images/UX_Hero_StandardShader.jpg)

<span data-ttu-id="dab82-106">因為全像真實環境中的實體物件會混合使用，所以請務必提供視覺提示給使用者。</span><span class="sxs-lookup"><span data-stu-id="dab82-106">Since holographic objects are mixed with physical ones in the real environment, it's important to provide visual cues to the user.</span></span> <span data-ttu-id="dab82-107">混合現實工具組標準著色器提供各種類型的視覺效果，以用於全像影像。</span><span class="sxs-lookup"><span data-stu-id="dab82-107">The Mixed Reality Toolkit Standard shader provides various types of visual effects for use with holograms.</span></span> <span data-ttu-id="dab82-108">陰影系統使用單一、彈性的著色器來達成類似 Unity 標準著色器的視覺效果。</span><span class="sxs-lookup"><span data-stu-id="dab82-108">The shading system uses a single, flexible shader to achieve visuals similar to Unity's Standard Shader.</span></span> <span data-ttu-id="dab82-109">著色器會在混合現實裝置上實行 [Fluent Design 系統準則](https://www.microsoft.com/design/fluent/#/) 並維持效能。</span><span class="sxs-lookup"><span data-stu-id="dab82-109">The shader implements [Fluent Design System principles](https://www.microsoft.com/design/fluent/#/) and remains performant on mixed reality devices.</span></span>
<br>

## <a name="examples-of-visual-effects-using-mrtk-mixed-reality-toolkit-standard-shader"></a><span data-ttu-id="dab82-110">使用 MRTK (混合現實工具組的視覺效果範例) 標準著色器</span><span class="sxs-lookup"><span data-stu-id="dab82-110">Examples of visual effects using MRTK (Mixed Reality Toolkit) Standard shader</span></span> 
:::row:::
    :::column:::
       <span data-ttu-id="dab82-111">![移動](images/UX_Button_Affordance_ProximityLight.jpg)</span><span class="sxs-lookup"><span data-stu-id="dab82-111">![Move](images/UX_Button_Affordance_ProximityLight.jpg)</span></span><br>
       <span data-ttu-id="dab82-112">**近亮光**</span><span class="sxs-lookup"><span data-stu-id="dab82-112">**Proximity light**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="dab82-113">![旋轉](images/UX_Button_Affordance_FocusHighlight.jpg)</span><span class="sxs-lookup"><span data-stu-id="dab82-113">![Rotate](images/UX_Button_Affordance_FocusHighlight.jpg)</span></span><br>
        <span data-ttu-id="dab82-114">**框線燈**</span><span class="sxs-lookup"><span data-stu-id="dab82-114">**Border light**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="standard-shader-in-mrtk-for-unity"></a><span data-ttu-id="dab82-115">適用于 Unity 的 MRTK 中的標準著色器</span><span class="sxs-lookup"><span data-stu-id="dab82-115">Standard shader in MRTK for Unity</span></span>

* [<span data-ttu-id="dab82-116">MRTK-標準著色器</span><span class="sxs-lookup"><span data-stu-id="dab82-116">MRTK - Standard shader</span></span>](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/rendering/mrtk-standard-shader)

<br>

---

## <a name="see-also"></a><span data-ttu-id="dab82-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dab82-117">See also</span></span>

* [<span data-ttu-id="dab82-118">游標</span><span class="sxs-lookup"><span data-stu-id="dab82-118">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="dab82-119">手部光線</span><span class="sxs-lookup"><span data-stu-id="dab82-119">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="dab82-120">Button</span><span class="sxs-lookup"><span data-stu-id="dab82-120">Button</span></span>](button.md)
* [<span data-ttu-id="dab82-121">可互動的物件</span><span class="sxs-lookup"><span data-stu-id="dab82-121">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="dab82-122">週框方塊和應用程式列</span><span class="sxs-lookup"><span data-stu-id="dab82-122">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="dab82-123">操作</span><span class="sxs-lookup"><span data-stu-id="dab82-123">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="dab82-124">手部功能表</span><span class="sxs-lookup"><span data-stu-id="dab82-124">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="dab82-125">近端功能表</span><span class="sxs-lookup"><span data-stu-id="dab82-125">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="dab82-126">物件集合</span><span class="sxs-lookup"><span data-stu-id="dab82-126">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="dab82-127">語音命令</span><span class="sxs-lookup"><span data-stu-id="dab82-127">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="dab82-128">鍵盤</span><span class="sxs-lookup"><span data-stu-id="dab82-128">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="dab82-129">工具提示</span><span class="sxs-lookup"><span data-stu-id="dab82-129">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="dab82-130">平板</span><span class="sxs-lookup"><span data-stu-id="dab82-130">Slate</span></span>](slate.md)
* [<span data-ttu-id="dab82-131">滑桿</span><span class="sxs-lookup"><span data-stu-id="dab82-131">Slider</span></span>](slider.md)
* [<span data-ttu-id="dab82-132">佈告板和常駐標籤</span><span class="sxs-lookup"><span data-stu-id="dab82-132">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="dab82-133">顯示進度</span><span class="sxs-lookup"><span data-stu-id="dab82-133">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="dab82-134">表面磁性</span><span class="sxs-lookup"><span data-stu-id="dab82-134">Surface magnetism</span></span>](surface-magnetism.md)
