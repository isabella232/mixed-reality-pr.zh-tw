---
title: 按鈕
description: 瞭解如何使用按鈕觸發立即動作，這是其中一個混合現實的基礎元件。
author: cre8ivepark
ms.author: dongpark
ms.date: 11/01/2019
ms.topic: article
keywords: 混合的現實、控制項、互動、ui、ux、混合現實耳機、windows mixed reality 耳機、虛擬實境耳機、HoloLens、MRTK、混合現實工具組、按鈕
ms.openlocfilehash: b4e8388c4e3ea855c191cbdfc06621018274ff86
ms.sourcegitcommit: d340303cda71c31e6c3320231473d623c0930d33
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/01/2021
ms.locfileid: "97847595"
---
# <a name="button"></a><span data-ttu-id="59300-104">Button</span><span class="sxs-lookup"><span data-stu-id="59300-104">Button</span></span>

![Button](images/UX_Hero_Button.jpg)

<span data-ttu-id="59300-106">按鈕可讓您的使用者在混合現實體驗中觸發立即動作。</span><span class="sxs-lookup"><span data-stu-id="59300-106">A button lets your users trigger immediate actions in a mixed reality experience.</span></span> <span data-ttu-id="59300-107">在 HoloLens 2 中，按鈕具有視覺提示和 affordances，可協助提高對使用者的互動。</span><span class="sxs-lookup"><span data-stu-id="59300-107">In HoloLens 2, buttons have visual cues and affordances that help increase interaction confidence with users.</span></span> 

:::row:::
    :::column:::
       <span data-ttu-id="59300-108">![顯示相近光線效果的按鈕](images/UX_Button_Affordance_ProximityLight.jpg)</span><span class="sxs-lookup"><span data-stu-id="59300-108">![Button with proximity light effect shown](images/UX_Button_Affordance_ProximityLight.jpg)</span></span><br>
       <span data-ttu-id="59300-109">**近亮光**</span><span class="sxs-lookup"><span data-stu-id="59300-109">**Proximity light**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="59300-110">![顯示焦點醒目提示效果的選取按鈕](images/UX_Button_Affordance_FocusHighlight.jpg)</span><span class="sxs-lookup"><span data-stu-id="59300-110">![Button selected with focus highlight effect shown](images/UX_Button_Affordance_FocusHighlight.jpg)</span></span><br>
        <span data-ttu-id="59300-111">**焦點醒目提示**</span><span class="sxs-lookup"><span data-stu-id="59300-111">**Focus highlight**</span></span><br>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="59300-112">![顯示具有壓縮箱效果的按鈕](images/UX_Button_Affordance_Compression.jpg)</span><span class="sxs-lookup"><span data-stu-id="59300-112">![Button being pressed with compression cage effect shown](images/UX_Button_Affordance_Compression.jpg)</span></span><br>
       <span data-ttu-id="59300-113">**壓縮框架**</span><span class="sxs-lookup"><span data-stu-id="59300-113">**Compressing cage**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="59300-114">![顯示觸發程式脈衝效果的按鍵](images/UX_Button_Affordance_Pulse.jpg)</span><span class="sxs-lookup"><span data-stu-id="59300-114">![Button being pressed with trigger pulse effect shown](images/UX_Button_Affordance_Pulse.jpg)</span></span><br>
        <span data-ttu-id="59300-115">**觸發程式上的脈衝**</span><span class="sxs-lookup"><span data-stu-id="59300-115">**Pulse on trigger**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="button-in-mrtkmixed-reality-toolkit-for-unity"></a><span data-ttu-id="59300-116">MRTK 中的按鈕 (混合現實工具組) for Unity</span><span class="sxs-lookup"><span data-stu-id="59300-116">Button in MRTK(Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="59300-117">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** 提供各種類型的按鈕 prefabs，包括 HoloLens 2 的 shell 樣式按鈕，以及 HoloLens (第1代) 。</span><span class="sxs-lookup"><span data-stu-id="59300-117">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** provides various types of button prefabs, including shell-style buttons for HoloLens 2 and HoloLens (1st gen).</span></span> <span data-ttu-id="59300-118">HoloLens 2 按鈕預製專案包含數個詳細 affordances，可協助提升使用者的信心：</span><span class="sxs-lookup"><span data-stu-id="59300-118">The HoloLens 2 button prefab contains several detailed affordances that help improve user confidence:</span></span>

* <span data-ttu-id="59300-119">鄰近性醒目提示</span><span class="sxs-lookup"><span data-stu-id="59300-119">Proximity-based highlight</span></span>
* <span data-ttu-id="59300-120">壓縮 front 籠</span><span class="sxs-lookup"><span data-stu-id="59300-120">Compressing front cage</span></span>
* <span data-ttu-id="59300-121">對觸發程式的脈衝效果。</span><span class="sxs-lookup"><span data-stu-id="59300-121">Pulse effect on trigger.</span></span>

* <span data-ttu-id="59300-122">如需詳細指示和自訂的範例，請參閱 [MRTK 按鈕](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html) 。</span><span class="sxs-lookup"><span data-stu-id="59300-122">Check out the [MRTK - Button](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html) for more instructions and customized examples.</span></span>

<br>

---

## <a name="see-also"></a><span data-ttu-id="59300-123">請參閱</span><span class="sxs-lookup"><span data-stu-id="59300-123">See also</span></span>

* [<span data-ttu-id="59300-124">游標</span><span class="sxs-lookup"><span data-stu-id="59300-124">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="59300-125">手部光線</span><span class="sxs-lookup"><span data-stu-id="59300-125">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="59300-126">Button</span><span class="sxs-lookup"><span data-stu-id="59300-126">Button</span></span>](button.md)
* [<span data-ttu-id="59300-127">可互動的物件</span><span class="sxs-lookup"><span data-stu-id="59300-127">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="59300-128">週框方塊和應用程式列</span><span class="sxs-lookup"><span data-stu-id="59300-128">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="59300-129">操作</span><span class="sxs-lookup"><span data-stu-id="59300-129">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="59300-130">手部功能表</span><span class="sxs-lookup"><span data-stu-id="59300-130">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="59300-131">近端功能表</span><span class="sxs-lookup"><span data-stu-id="59300-131">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="59300-132">物件集合</span><span class="sxs-lookup"><span data-stu-id="59300-132">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="59300-133">語音命令</span><span class="sxs-lookup"><span data-stu-id="59300-133">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="59300-134">鍵盤</span><span class="sxs-lookup"><span data-stu-id="59300-134">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="59300-135">工具提示</span><span class="sxs-lookup"><span data-stu-id="59300-135">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="59300-136">平板</span><span class="sxs-lookup"><span data-stu-id="59300-136">Slate</span></span>](slate.md)
* [<span data-ttu-id="59300-137">滑桿</span><span class="sxs-lookup"><span data-stu-id="59300-137">Slider</span></span>](slider.md)
* [<span data-ttu-id="59300-138">著色器</span><span class="sxs-lookup"><span data-stu-id="59300-138">Shader</span></span>](shader.md)
* [<span data-ttu-id="59300-139">佈告板和常駐標籤</span><span class="sxs-lookup"><span data-stu-id="59300-139">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="59300-140">顯示進度</span><span class="sxs-lookup"><span data-stu-id="59300-140">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="59300-141">表面磁性</span><span class="sxs-lookup"><span data-stu-id="59300-141">Surface magnetism</span></span>](surface-magnetism.md)
