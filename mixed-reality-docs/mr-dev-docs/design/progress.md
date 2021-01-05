---
title: 顯示進度
description: 進度控制項為使用者提供回饋，告知正在進行長時間執行的操作。
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality、設計、控制項、ui、ux、進度指標、混合現實耳機、windows Mixed Reality 耳機、虛擬實境耳機、HoloLens、MRTK、混合現實工具組
ms.openlocfilehash: 3f24f7095147a0d220df8adc42b67a1b8e4053c9
ms.sourcegitcommit: d340303cda71c31e6c3320231473d623c0930d33
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/01/2021
ms.locfileid: "97848286"
---
# <a name="progress-indicator"></a><span data-ttu-id="a01b6-104">進度指示器</span><span class="sxs-lookup"><span data-stu-id="a01b6-104">Progress indicator</span></span>

<br>

<img src="images/MRTK_ProgressIndicator.gif" alt="Progress ring example in HoloLens" width="940px">

<span data-ttu-id="a01b6-105">進度控制項可提供執行長時間執行作業的意見反應。</span><span class="sxs-lookup"><span data-stu-id="a01b6-105">A progress control provides feedback that a long-running operation is underway.</span></span> <span data-ttu-id="a01b6-106">當進度指標可見時，使用者可以看到等待時間，而且無法與應用程式互動。</span><span class="sxs-lookup"><span data-stu-id="a01b6-106">When a progress indicator is visible, users can see the wait time and can't interact with the app.</span></span>

<br>

---

## <a name="types-of-progress"></a><span data-ttu-id="a01b6-107">進度的類型</span><span class="sxs-lookup"><span data-stu-id="a01b6-107">Types of progress</span></span>

<span data-ttu-id="a01b6-108">請務必提供有關所發生情況的使用者資訊。</span><span class="sxs-lookup"><span data-stu-id="a01b6-108">It's important to provide the user information about what is happening.</span></span> <span data-ttu-id="a01b6-109">在混合的情況下，如果您的應用程式沒有良好的視覺效果意見反應，就可以輕鬆地將使用者的注意力帶到實體環境或物件。</span><span class="sxs-lookup"><span data-stu-id="a01b6-109">In mixed reality, users can be easily distracted by the physical environment or objects if your app doesn't have good visual feedback.</span></span> <span data-ttu-id="a01b6-110">在需要幾秒鐘的情況下（例如資料載入或場景正在進行更新時），最好是顯示視覺指標。</span><span class="sxs-lookup"><span data-stu-id="a01b6-110">For situations that take a few seconds, like when data is loading or a scene is updating, it's a good idea to show a visual indicator.</span></span> <span data-ttu-id="a01b6-111">有兩個選項可讓使用者顯示作業正在進行中– **進度** 列或 **進度環形**。</span><span class="sxs-lookup"><span data-stu-id="a01b6-111">There are two options to show the user that an operation is underway – a **Progress bar** or a **Progress ring**.</span></span>

:::row:::
    :::column:::
        ### <a name="progress-barbr"></a><span data-ttu-id="a01b6-112">進度列</span><span class="sxs-lookup"><span data-stu-id="a01b6-112">Progress bar</span></span><br>
        <span data-ttu-id="a01b6-113">進度列會顯示工作的完成百分比。</span><span class="sxs-lookup"><span data-stu-id="a01b6-113">A Progress bar shows the percentage completed of a task.</span></span> <span data-ttu-id="a01b6-114">它應該在其持續時間已知 (確定) 的作業期間使用，但其進度不應封鎖使用者與應用程式的互動。</span><span class="sxs-lookup"><span data-stu-id="a01b6-114">It should be used during an operation whose duration is known (determinate), but its progress shouldn't block the user's interaction with the app.</span></span><br>
        <br>
        <span data-ttu-id="a01b6-115">*影像： HoloLens 的進度列範例*</span><span class="sxs-lookup"><span data-stu-id="a01b6-115">*Image: Progress bar example in HoloLens*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="a01b6-116">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="a01b6-116">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="a01b6-117">![HoloLens 中的進度列範例](images/640px-progressbar.jpg)</span><span class="sxs-lookup"><span data-stu-id="a01b6-117">![Progress bar example in HoloLens](images/640px-progressbar.jpg)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

:::row:::
    :::column:::
        ### <a name="progress-ringbr"></a><span data-ttu-id="a01b6-118">進度環</span><span class="sxs-lookup"><span data-stu-id="a01b6-118">Progress ring</span></span><br>
        <span data-ttu-id="a01b6-119">進度環形只有不定狀態，而且應該在作業完成之前封鎖使用者互動時使用。</span><span class="sxs-lookup"><span data-stu-id="a01b6-119">A Progress ring only has an indeterminate state, and should be used when user interaction is blocked until the operation has completed.</span></span><br>
        <br>
        <span data-ttu-id="a01b6-120">*影像： HoloLens 的進度環形範例*</span><span class="sxs-lookup"><span data-stu-id="a01b6-120">*Image: Progress ring example in HoloLens*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="a01b6-121">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="a01b6-121">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="a01b6-122">![HoloLens 裝置上的進度環形範例](images/640px-progressring.jpg)</span><span class="sxs-lookup"><span data-stu-id="a01b6-122">![Progress ring example on HoloLens device](images/640px-progressring.jpg)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

:::row:::
    :::column:::
        ### <a name="progress-with-a-custom-objectbr"></a><span data-ttu-id="a01b6-123">使用自訂物件的進度</span><span class="sxs-lookup"><span data-stu-id="a01b6-123">Progress with a custom object</span></span><br>
        <span data-ttu-id="a01b6-124">您可以使用自己的自訂 2D/3D 物件自訂進度控制項，以新增至您應用程式的個人和品牌身分識別。</span><span class="sxs-lookup"><span data-stu-id="a01b6-124">You can add to your app's personality and brand identity by customizing the Progress control with your own custom 2D/3D objects.</span></span><br>
        <br>
        <span data-ttu-id="a01b6-125">*影像：在 HoloLens 中使用自訂網格範例的進度*</span><span class="sxs-lookup"><span data-stu-id="a01b6-125">*Image: Progress with custom mesh example in HoloLens*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="a01b6-126">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="a01b6-126">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="a01b6-127">![HoloLens 中自訂網格範例的進度](images/640px-progresscustom.jpg)</span><span class="sxs-lookup"><span data-stu-id="a01b6-127">![Progress with custom mesh example in HoloLens](images/640px-progresscustom.jpg)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="best-practices"></a><span data-ttu-id="a01b6-128">最佳作法</span><span class="sxs-lookup"><span data-stu-id="a01b6-128">Best practices</span></span>
* <span data-ttu-id="a01b6-129">將 [billboarding 或標記](billboarding-and-tag-along.md) 緊密結合到進度顯示，因為使用者可以輕鬆地將其移到空白空間並遺失內容。</span><span class="sxs-lookup"><span data-stu-id="a01b6-129">Tightly couple [billboarding or tag-along](billboarding-and-tag-along.md) to the display of Progress since the user can easily move their head into empty space and lose context.</span></span> <span data-ttu-id="a01b6-130">如果使用者無法看到任何結果，您的應用程式可能看起來像是損毀。</span><span class="sxs-lookup"><span data-stu-id="a01b6-130">Your app might look like it has crashed if the user is unable to see anything.</span></span> <span data-ttu-id="a01b6-131">Billboarding 和標記-也內建在進度預製專案中。</span><span class="sxs-lookup"><span data-stu-id="a01b6-131">Billboarding and tag-along is built into the Progress prefab.</span></span>
* <span data-ttu-id="a01b6-132">提供使用者所發生狀況的狀態資訊一律是很好的方式。</span><span class="sxs-lookup"><span data-stu-id="a01b6-132">It's always good to provide status information about what is happening to the user.</span></span> <span data-ttu-id="a01b6-133">進度預製專案提供各種視覺化樣式，包括提供狀態的 Windows 標準環形類型進度。</span><span class="sxs-lookup"><span data-stu-id="a01b6-133">The Progress prefab provides various visual styles including the Windows standard ring-type progress for providing status.</span></span> <span data-ttu-id="a01b6-134">如果您希望進度的樣式與您的應用程式品牌保持一致，您也可以使用自訂網格和動畫。</span><span class="sxs-lookup"><span data-stu-id="a01b6-134">You can also use a custom mesh with an animation if you want the style of your progress to align to your app’s brand.</span></span>

<br>

---

## <a name="progress-indicator-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="a01b6-135">Unity 的 MRTK (混合現實工具組) 的進度列指示器</span><span class="sxs-lookup"><span data-stu-id="a01b6-135">Progress indicator in MRTK (Mixed Reality Toolkit) for Unity</span></span>

* [<span data-ttu-id="a01b6-136">MRTK-進度指標 prefabs</span><span class="sxs-lookup"><span data-stu-id="a01b6-136">MRTK - Progress indicator prefabs</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MRTK/SDK/Features/UX/Prefabs/ProgressIndicators)
* [<span data-ttu-id="a01b6-137">MRTK-場景轉換服務</span><span class="sxs-lookup"><span data-stu-id="a01b6-137">MRTK - Scene transition service</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Extensions/SceneTransitionService/SceneTransitionServiceOverview.html)


<br>

---

## <a name="see-also"></a><span data-ttu-id="a01b6-138">請參閱</span><span class="sxs-lookup"><span data-stu-id="a01b6-138">See also</span></span>

* [<span data-ttu-id="a01b6-139">游標</span><span class="sxs-lookup"><span data-stu-id="a01b6-139">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="a01b6-140">手部光線</span><span class="sxs-lookup"><span data-stu-id="a01b6-140">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="a01b6-141">Button</span><span class="sxs-lookup"><span data-stu-id="a01b6-141">Button</span></span>](button.md)
* [<span data-ttu-id="a01b6-142">可互動的物件</span><span class="sxs-lookup"><span data-stu-id="a01b6-142">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="a01b6-143">週框方塊和應用程式列</span><span class="sxs-lookup"><span data-stu-id="a01b6-143">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="a01b6-144">操作</span><span class="sxs-lookup"><span data-stu-id="a01b6-144">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="a01b6-145">手部功能表</span><span class="sxs-lookup"><span data-stu-id="a01b6-145">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="a01b6-146">近端功能表</span><span class="sxs-lookup"><span data-stu-id="a01b6-146">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="a01b6-147">物件集合</span><span class="sxs-lookup"><span data-stu-id="a01b6-147">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="a01b6-148">語音命令</span><span class="sxs-lookup"><span data-stu-id="a01b6-148">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="a01b6-149">鍵盤</span><span class="sxs-lookup"><span data-stu-id="a01b6-149">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="a01b6-150">工具提示</span><span class="sxs-lookup"><span data-stu-id="a01b6-150">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="a01b6-151">平板</span><span class="sxs-lookup"><span data-stu-id="a01b6-151">Slate</span></span>](slate.md)
* [<span data-ttu-id="a01b6-152">滑桿</span><span class="sxs-lookup"><span data-stu-id="a01b6-152">Slider</span></span>](slider.md)
* [<span data-ttu-id="a01b6-153">著色器</span><span class="sxs-lookup"><span data-stu-id="a01b6-153">Shader</span></span>](shader.md)
* [<span data-ttu-id="a01b6-154">佈告板和常駐標籤</span><span class="sxs-lookup"><span data-stu-id="a01b6-154">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="a01b6-155">顯示進度</span><span class="sxs-lookup"><span data-stu-id="a01b6-155">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="a01b6-156">表面磁性</span><span class="sxs-lookup"><span data-stu-id="a01b6-156">Surface magnetism</span></span>](surface-magnetism.md)
