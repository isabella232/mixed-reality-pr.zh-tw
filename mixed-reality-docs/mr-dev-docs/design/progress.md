---
title: 顯示進度
description: 進度控制項為使用者提供回饋，告知正在進行長時間執行的操作。
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality、設計、控制項、ui、ux、進度指標、混合現實耳機、windows Mixed Reality 耳機、虛擬實境耳機、HoloLens、MRTK、混合現實工具組
ms.openlocfilehash: 93cdd7054c05af9f8621e091fa3d4b59d9e65ee3
ms.sourcegitcommit: 4f3ef057a285be2e260615e5d6c41f00d15d08f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2020
ms.locfileid: "94703384"
---
# <a name="progress-indicator"></a><span data-ttu-id="9eb3b-104">進度指示器</span><span class="sxs-lookup"><span data-stu-id="9eb3b-104">Progress indicator</span></span>

<br>

<img src="images/MRTK_ProgressIndicator.gif" alt="Progress ring example in HoloLens" width="940px">

<span data-ttu-id="9eb3b-105">進度控制項為使用者提供回饋，告知正在進行長時間執行的操作。</span><span class="sxs-lookup"><span data-stu-id="9eb3b-105">A progress control provides feedback to the user that a long-running operation is underway.</span></span> <span data-ttu-id="9eb3b-106">根據所使用的指示器，它可以表示在進度指示器可見的時候，使用者無法與 App 互動，也可以指示可能需要等待多久的時間。</span><span class="sxs-lookup"><span data-stu-id="9eb3b-106">It can mean that the user cannot interact with the app when the progress indicator is visible, and can also indicate how long the wait time might be, depending on the indicator used.</span></span>

<br>

---

## <a name="types-of-progress"></a><span data-ttu-id="9eb3b-107">進度的類型</span><span class="sxs-lookup"><span data-stu-id="9eb3b-107">Types of progress</span></span>

<span data-ttu-id="9eb3b-108">請務必提供有關所發生情況的使用者資訊。</span><span class="sxs-lookup"><span data-stu-id="9eb3b-108">It is important to provide the user information about what is happening.</span></span> <span data-ttu-id="9eb3b-109">如果您的應用程式沒有提供良好的視覺效果意見反應，則在混合現實的使用者中，實體環境或物件很容易就會有問題。</span><span class="sxs-lookup"><span data-stu-id="9eb3b-109">In mixed reality users can be easily distracted by physical environment or objects if your app does not gives good visual feedback.</span></span> <span data-ttu-id="9eb3b-110">在需要幾秒鐘的情況下（例如，當資料正在載入或場景正在更新時），最好是顯示視覺指標。</span><span class="sxs-lookup"><span data-stu-id="9eb3b-110">For situations that take a few seconds, such when data is loading or a scene is updating, it is good idea to show a visual indicator.</span></span> <span data-ttu-id="9eb3b-111">有兩個選項可讓使用者顯示作業正在進行中– **進度** 列或 **進度環形**。</span><span class="sxs-lookup"><span data-stu-id="9eb3b-111">There are two options to show the user that an operation is underway – a **Progress bar** or a **Progress ring**.</span></span>

:::row:::
    :::column:::
        ### <a name="progress-barbr"></a><span data-ttu-id="9eb3b-112">進度列</span><span class="sxs-lookup"><span data-stu-id="9eb3b-112">Progress bar</span></span><br>
        <span data-ttu-id="9eb3b-113">進度列會顯示工作的完成百分比。</span><span class="sxs-lookup"><span data-stu-id="9eb3b-113">A Progress bar shows the percentage completed of a task.</span></span> <span data-ttu-id="9eb3b-114">它應該在其持續時間已知 (確定) 的作業期間使用，但其進度不應封鎖使用者與應用程式的互動。</span><span class="sxs-lookup"><span data-stu-id="9eb3b-114">It should be used during an operation whose duration is known (determinate), but it's progress should not block the user's interaction with the app.</span></span><br>
        <br>
        <span data-ttu-id="9eb3b-115">*影像： HoloLens 的進度列範例*</span><span class="sxs-lookup"><span data-stu-id="9eb3b-115">*Image: Progress bar example in HoloLens*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="9eb3b-116">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="9eb3b-116">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="9eb3b-117">![HoloLens 中的進度列範例](images/640px-progressbar.jpg)</span><span class="sxs-lookup"><span data-stu-id="9eb3b-117">![Progress bar example in HoloLens](images/640px-progressbar.jpg)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

:::row:::
    :::column:::
        ### <a name="progress-ringbr"></a><span data-ttu-id="9eb3b-118">進度環</span><span class="sxs-lookup"><span data-stu-id="9eb3b-118">Progress ring</span></span><br>
        <span data-ttu-id="9eb3b-119">只有在作業完成之後，才會封鎖進度環形的狀態，而且應該在任何進一步的使用者互動時使用。</span><span class="sxs-lookup"><span data-stu-id="9eb3b-119">A Progress ring only has an indeterminate state, and should be used when any further user interaction is blocked until the operation has completed.</span></span><br>
        <br>
        <span data-ttu-id="9eb3b-120">*影像： HoloLens 的進度環形範例*</span><span class="sxs-lookup"><span data-stu-id="9eb3b-120">*Image: Progress ring example in HoloLens*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="9eb3b-121">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="9eb3b-121">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="9eb3b-122">![HoloLens 的進度環形範例](images/640px-progressring.jpg)</span><span class="sxs-lookup"><span data-stu-id="9eb3b-122">![Progress ring example in HoloLens](images/640px-progressring.jpg)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

:::row:::
    :::column:::
        ### <a name="progress-with-a-custom-objectbr"></a><span data-ttu-id="9eb3b-123">使用自訂物件的進度</span><span class="sxs-lookup"><span data-stu-id="9eb3b-123">Progress with a custom object</span></span><br>
        <span data-ttu-id="9eb3b-124">您可以使用自己的自訂 2D/3D 物件自訂進度控制項，以新增至您應用程式的個人和品牌身分識別。</span><span class="sxs-lookup"><span data-stu-id="9eb3b-124">You can add to your app's personality and brand identity by customizing the Progress control with your own custom 2D/3D objects.</span></span><br>
        <br>
        <span data-ttu-id="9eb3b-125">*影像：在 HoloLens 中使用自訂網格範例的進度*</span><span class="sxs-lookup"><span data-stu-id="9eb3b-125">*Image: Progress with custom mesh example in HoloLens*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="9eb3b-126">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="9eb3b-126">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="9eb3b-127">![HoloLens 中自訂網格範例的進度](images/640px-progresscustom.jpg)</span><span class="sxs-lookup"><span data-stu-id="9eb3b-127">![Progress with custom mesh example in HoloLens](images/640px-progresscustom.jpg)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="best-practices"></a><span data-ttu-id="9eb3b-128">最佳作法</span><span class="sxs-lookup"><span data-stu-id="9eb3b-128">Best practices</span></span>
* <span data-ttu-id="9eb3b-129">將 [billboarding 或標記](billboarding-and-tag-along.md) 緊密結合到進度顯示，因為使用者可以輕鬆地將其移到空白空間並遺失內容。</span><span class="sxs-lookup"><span data-stu-id="9eb3b-129">Tightly couple [billboarding or tag-along](billboarding-and-tag-along.md) to the display of Progress since the user can easily move their head into empty space and lose context.</span></span> <span data-ttu-id="9eb3b-130">如果使用者無法看到任何結果，您的應用程式可能看起來像是損毀。</span><span class="sxs-lookup"><span data-stu-id="9eb3b-130">Your app might look like it has crashed if the user is unable to see anything.</span></span> <span data-ttu-id="9eb3b-131">Billboarding 和標記-也內建在進度預製專案中。</span><span class="sxs-lookup"><span data-stu-id="9eb3b-131">Billboarding and tag-along is built into the Progress prefab.</span></span>
* <span data-ttu-id="9eb3b-132">提供使用者所發生狀況的狀態資訊一律是很好的方式。</span><span class="sxs-lookup"><span data-stu-id="9eb3b-132">It's always good to provide status information about what is happening to the user.</span></span> <span data-ttu-id="9eb3b-133">進度預製專案提供各種視覺化樣式，包括提供狀態的 Windows 標準環形類型進度。</span><span class="sxs-lookup"><span data-stu-id="9eb3b-133">The Progress prefab provides various visual styles including the Windows standard ring-type progress for providing status.</span></span> <span data-ttu-id="9eb3b-134">如果您希望進度的樣式與您的應用程式品牌保持一致，您也可以使用自訂網格和動畫。</span><span class="sxs-lookup"><span data-stu-id="9eb3b-134">You can also use a custom mesh with an animation if you want the style of your progress to align to your app’s brand.</span></span>

<br>

---

## <a name="progress-indicator-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="9eb3b-135">Unity 的 MRTK (混合現實工具組) 的進度列指示器</span><span class="sxs-lookup"><span data-stu-id="9eb3b-135">Progress indicator in MRTK (Mixed Reality Toolkit) for Unity</span></span>

* [<span data-ttu-id="9eb3b-136">MRTK-進度指標 prefabs</span><span class="sxs-lookup"><span data-stu-id="9eb3b-136">MRTK - Progress indicator prefabs</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Prefabs/ProgressIndicators)
* [<span data-ttu-id="9eb3b-137">MRTK-場景轉換服務</span><span class="sxs-lookup"><span data-stu-id="9eb3b-137">MRTK - Scene transition service</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Extensions/SceneTransitionService/SceneTransitionServiceOverview.html)


<br>

---

## <a name="see-also"></a><span data-ttu-id="9eb3b-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9eb3b-138">See also</span></span>

* [<span data-ttu-id="9eb3b-139">游標</span><span class="sxs-lookup"><span data-stu-id="9eb3b-139">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="9eb3b-140">手部光線</span><span class="sxs-lookup"><span data-stu-id="9eb3b-140">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="9eb3b-141">Button</span><span class="sxs-lookup"><span data-stu-id="9eb3b-141">Button</span></span>](button.md)
* [<span data-ttu-id="9eb3b-142">可互動的物件</span><span class="sxs-lookup"><span data-stu-id="9eb3b-142">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="9eb3b-143">週框方塊和應用程式列</span><span class="sxs-lookup"><span data-stu-id="9eb3b-143">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="9eb3b-144">操作</span><span class="sxs-lookup"><span data-stu-id="9eb3b-144">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="9eb3b-145">手部功能表</span><span class="sxs-lookup"><span data-stu-id="9eb3b-145">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="9eb3b-146">近端功能表</span><span class="sxs-lookup"><span data-stu-id="9eb3b-146">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="9eb3b-147">物件集合</span><span class="sxs-lookup"><span data-stu-id="9eb3b-147">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="9eb3b-148">語音命令</span><span class="sxs-lookup"><span data-stu-id="9eb3b-148">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="9eb3b-149">鍵盤</span><span class="sxs-lookup"><span data-stu-id="9eb3b-149">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="9eb3b-150">工具提示</span><span class="sxs-lookup"><span data-stu-id="9eb3b-150">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="9eb3b-151">平板</span><span class="sxs-lookup"><span data-stu-id="9eb3b-151">Slate</span></span>](slate.md)
* [<span data-ttu-id="9eb3b-152">滑桿</span><span class="sxs-lookup"><span data-stu-id="9eb3b-152">Slider</span></span>](slider.md)
* [<span data-ttu-id="9eb3b-153">著色器</span><span class="sxs-lookup"><span data-stu-id="9eb3b-153">Shader</span></span>](shader.md)
* [<span data-ttu-id="9eb3b-154">佈告板和常駐標籤</span><span class="sxs-lookup"><span data-stu-id="9eb3b-154">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="9eb3b-155">顯示進度</span><span class="sxs-lookup"><span data-stu-id="9eb3b-155">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="9eb3b-156">表面磁性</span><span class="sxs-lookup"><span data-stu-id="9eb3b-156">Surface magnetism</span></span>](surface-magnetism.md)
