---
title: 手勢指導
description: 瞭解當系統未偵測到使用者的手協助時，如何使用手指導來觸發3D 手。
author: grayclee
ms.author: glee
ms.date: 09/25/2019
ms.topic: article
keywords: Windows Mixed Reality、設計、手輔導、沉浸式耳機、MRTK、手、協助手、混合現實耳機、windows Mixed reality 耳機、虛擬實境耳機、HoloLens、MRTK、混合現實工具組
ms.openlocfilehash: 0fe0d87e26d06838c0d1b7935573d9bd8ce258ee
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600427"
---
# <a name="hand-coach"></a><span data-ttu-id="c7c88-104">手勢指導</span><span class="sxs-lookup"><span data-stu-id="c7c88-104">Hand coach</span></span>

![範例：手形指導](images/HandCoach/MRTK_handCoach.jpg)<br>

<span data-ttu-id="c7c88-106">當系統未偵測到使用者的手時，手上的教練會觸發3D 模型化的手。</span><span class="sxs-lookup"><span data-stu-id="c7c88-106">Hand coach triggers 3D modeled hands when the system doesn't detect the user’s hands.</span></span> <span data-ttu-id="c7c88-107">這項功能是一個「教學」元件，可在未教授手勢時協助引導使用者。</span><span class="sxs-lookup"><span data-stu-id="c7c88-107">This feature is a “teaching” component that helps guide the user when the gesture hasn't been taught.</span></span> <span data-ttu-id="c7c88-108">如果使用者尚未針對某個句號完成指定的手勢，則手會有延遲的迴圈。</span><span class="sxs-lookup"><span data-stu-id="c7c88-108">If users haven't done the specified gesture for a period, the hands will loop with a delay.</span></span> <span data-ttu-id="c7c88-109">手形指導可用來代表按下按鈕或挑選全像影像。</span><span class="sxs-lookup"><span data-stu-id="c7c88-109">The Hand coach could be used to represent pressing a button or picking up a hologram.</span></span>  

## <a name="hand-coach-provided"></a><span data-ttu-id="c7c88-110">提供的手勢</span><span class="sxs-lookup"><span data-stu-id="c7c88-110">Hand coach provided</span></span>

<span data-ttu-id="c7c88-111">目前的互動模型代表各式各樣的手勢控制項，例如滾動、遠選和近端點擊。</span><span class="sxs-lookup"><span data-stu-id="c7c88-111">The current interaction model represents a wide variety of gesture controls such as scrolling, far select, and near tap.</span></span> <span data-ttu-id="c7c88-112">以下是<a href="https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets"> MRTK</a>中所提供之現有手勢的完整清單：</span><span class="sxs-lookup"><span data-stu-id="c7c88-112">Below is a full list of existing hand gestures provided in<a href="https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets"> MRTK</a>:</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="c7c88-113">![接近 Select 的範例](images/HandCoach/NearSelect.gif)</span><span class="sxs-lookup"><span data-stu-id="c7c88-113">![Example of Near Select](images/HandCoach/NearSelect.gif)</span></span><br>
       <span data-ttu-id="c7c88-114">**接近選擇使用的範例顯示如何選取按鈕或關閉互動物件**</span><span class="sxs-lookup"><span data-stu-id="c7c88-114">**Example of Near Select - Used show how to select buttons or close interactable objects**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="c7c88-115">![點擊點範例](images/HandCoach/AirTap.gif)</span><span class="sxs-lookup"><span data-stu-id="c7c88-115">![Example of Air Tap](images/HandCoach/AirTap.gif)</span></span><br>
        <span data-ttu-id="c7c88-116">**用來顯示如何選取遠距離的物件的點擊範例**</span><span class="sxs-lookup"><span data-stu-id="c7c88-116">**Example of Air Tap - Used to show how to select objects that are far away**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="c7c88-117">![移動的範例](images/HandCoach/Move.gif)</span><span class="sxs-lookup"><span data-stu-id="c7c88-117">![Example of Move](images/HandCoach/Move.gif)</span></span><br>
       <span data-ttu-id="c7c88-118">**移動空間中物件的範例，用來示範如何在空間中移動全息圖**</span><span class="sxs-lookup"><span data-stu-id="c7c88-118">**Example of Moving an object in space-Used to show how to move a hologram in space**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="c7c88-119">![旋轉範例](images/HandCoach/Rotate.gif)</span><span class="sxs-lookup"><span data-stu-id="c7c88-119">![Example of Rotate](images/HandCoach/Rotate.gif)</span></span><br>
       <span data-ttu-id="c7c88-120">**示範如何旋轉全像全像是影像或物件的 Rotate-Used 範例**</span><span class="sxs-lookup"><span data-stu-id="c7c88-120">**Example of Rotate-Used to show how to rotate holograms or objects**</span></span><br>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="c7c88-121">![調整規模範例](images/HandCoach/Scale.gif)</span><span class="sxs-lookup"><span data-stu-id="c7c88-121">![Example of Scale](images/HandCoach/Scale.gif)</span></span><br>
       <span data-ttu-id="c7c88-122">**相應縮小範例，用來示範如何操作大容量**</span><span class="sxs-lookup"><span data-stu-id="c7c88-122">**Example of Scale- Used to show how to manipulate holograms to be bigger or smaller**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="c7c88-123">![手掌的範例](images/HandCoach/PalmUp.gif)</span><span class="sxs-lookup"><span data-stu-id="c7c88-123">![Example of Palm Up](images/HandCoach/PalmUp.gif)</span></span><br>
        <span data-ttu-id="c7c88-124">**用來顯示快顯功能表的上方範例-建議使用**</span><span class="sxs-lookup"><span data-stu-id="c7c88-124">**Example of Palm up – Suggested use, to bring up hand menus**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="c7c88-125">![HandFlip 範例](images/HandCoach/HandFlip.gif)</span><span class="sxs-lookup"><span data-stu-id="c7c88-125">![Example of HandFlip](images/HandCoach/HandFlip.gif)</span></span><br>
       <span data-ttu-id="c7c88-126">**手勢範例-另一種顯示功能表的方法**</span><span class="sxs-lookup"><span data-stu-id="c7c88-126">**Exmaple of Hand Flip – Another way to bring up Hand Menus**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="c7c88-127">![滾動的範例](images/HandCoach/Scoll.gif)</span><span class="sxs-lookup"><span data-stu-id="c7c88-127">![Example of Scroll](images/HandCoach/Scoll.gif)</span></span><br>
       <span data-ttu-id="c7c88-128">**滾動範例-用於滾動清單或長檔**</span><span class="sxs-lookup"><span data-stu-id="c7c88-128">**Example of Scroll – Used for scrolling a list or a long document**</span></span><br>
    :::column-end:::
:::row-end:::

## <a name="design-concepts"></a><span data-ttu-id="c7c88-129">設計概念</span><span class="sxs-lookup"><span data-stu-id="c7c88-129">Design concepts</span></span>

<span data-ttu-id="c7c88-130">針對 Hololens2，我們根據 instinctual 和自然手勢來設計出互動。</span><span class="sxs-lookup"><span data-stu-id="c7c88-130">For Hololens2, we designed out hand interactions based on instinctual and natural hand gestures.</span></span> <span data-ttu-id="c7c88-131">我們相信大部分的使用者都可以直覺化，因此我們不會建立專用的手勢學習時間。</span><span class="sxs-lookup"><span data-stu-id="c7c88-131">We believe these to be intuitive to most users, so we didn't create dedicated gesture learning moments.</span></span> <span data-ttu-id="c7c88-132">相反地，我們建立了一項指導，以協助使用者瞭解這些手勢是否停滯，或不熟悉全像全息圖互動。</span><span class="sxs-lookup"><span data-stu-id="c7c88-132">Instead, we created the hand coach to help users learn about these gestures if they get stuck or are unfamiliar with hologram interactions.</span></span> <span data-ttu-id="c7c88-133">在沒有學習的時候，我們認為顯示使用者如何藉由示範來執行動作，這是最佳選項。</span><span class="sxs-lookup"><span data-stu-id="c7c88-133">Without a learning moment, we felt that showing users how to perform an action by demonstrating it would be the best option.</span></span> <span data-ttu-id="c7c88-134">我們發現使用者能夠找出手勢，但需要一些指引。</span><span class="sxs-lookup"><span data-stu-id="c7c88-134">We found that users were able to figure out the gesture but needed a little guidance.</span></span> <span data-ttu-id="c7c88-135">如果我們偵測到使用者未與某個物件進行互動，則會觸發適當的手勢和手指放置。</span><span class="sxs-lookup"><span data-stu-id="c7c88-135">If we detect a user doesn't interact with an object for a period, a Hand coach would be triggered demonstrating the correct hand and finger placement.</span></span> 

### <a name="intuitive"></a><span data-ttu-id="c7c88-136">直觀</span><span class="sxs-lookup"><span data-stu-id="c7c88-136">Intuitive</span></span>

<span data-ttu-id="c7c88-137">製作手動畫時，應該很明顯，不會造成任何混淆。</span><span class="sxs-lookup"><span data-stu-id="c7c88-137">When animating hands, it should be obvious and shouldn't cause any confusion.</span></span> <span data-ttu-id="c7c88-138">手動畫是您嘗試提示使用者瞭解的手勢標記法。</span><span class="sxs-lookup"><span data-stu-id="c7c88-138">The hand animation is a representation of the gesture you're trying to prompt the user to understand.</span></span> 

<span data-ttu-id="c7c88-139">例如，如果您希望使用者按下按鈕，就會觸發按下按鈕的動作。</span><span class="sxs-lookup"><span data-stu-id="c7c88-139">For example, if you wish a user to press a button, a hand pressing a button would be triggered.</span></span>

<span data-ttu-id="c7c88-140">![範例：近乎點擊的手勢](images/HandCoach/NearSelect_unity.gif)</span><span class="sxs-lookup"><span data-stu-id="c7c88-140">![Example: Hand coach Near Tap](images/HandCoach/NearSelect_unity.gif)</span></span><br>
<span data-ttu-id="c7c88-141">*示範近乎點擊 Gem 的手勢*</span><span class="sxs-lookup"><span data-stu-id="c7c88-141">*Hand Coach demonstrating Near Tapping a Gem*</span></span>  

### <a name="hand-scale"></a><span data-ttu-id="c7c88-142">手擴展</span><span class="sxs-lookup"><span data-stu-id="c7c88-142">Hand scale</span></span>

<span data-ttu-id="c7c88-143">我們使用 UI 功能表來測試各種手上的大小，並覺得如果手上的大小為真，則會提供阻感受。</span><span class="sxs-lookup"><span data-stu-id="c7c88-143">We tested various hand sizes with the UI menus and felt that if the hands were true to size, it gave a menacing feeling.</span></span> <span data-ttu-id="c7c88-144">如果太小，就很難查看並瞭解手勢。</span><span class="sxs-lookup"><span data-stu-id="c7c88-144">If they were too small, it was hard to see and understand the gesture.</span></span> 

<span data-ttu-id="c7c88-145">**語氣和手**</span><span class="sxs-lookup"><span data-stu-id="c7c88-145">**Voice over and hands**</span></span>

<span data-ttu-id="c7c88-146">不要預期使用者可透過語音聆聽一組指示，並透過手動指導來觀看不同的指示。</span><span class="sxs-lookup"><span data-stu-id="c7c88-146">Don’t expect users can listen to one set of instructions via voice over and watch different instructions via Hand coach.</span></span> <span data-ttu-id="c7c88-147">排序您的指示，以協助使用者專注于競爭，以減少感應式多載。</span><span class="sxs-lookup"><span data-stu-id="c7c88-147">Sequence your instructions to help users focus versus compete for their attention to reduce sensory overload.</span></span>


## <a name="can-i-create-my-own"></a><span data-ttu-id="c7c88-148">我可以建立自己的嗎？</span><span class="sxs-lookup"><span data-stu-id="c7c88-148">Can I create my own?</span></span>

<span data-ttu-id="c7c88-149">可以！</span><span class="sxs-lookup"><span data-stu-id="c7c88-149">Yes!</span></span> <span data-ttu-id="c7c88-150">建議您為您的遊戲建立自己的獨特手勢，並貢獻回該社區！</span><span class="sxs-lookup"><span data-stu-id="c7c88-150">We encourage you to create your own unique gesture for your game and contribute back to the community!</span></span>
<span data-ttu-id="c7c88-151">我們提供 Rigged 手的 Maya 檔，可用於您的應用程式，您可以在這裡下載： <a href="files/HandCoach_MRTK.zip"> 下載 HandCoach_MRTK.zip </a></span><span class="sxs-lookup"><span data-stu-id="c7c88-151">We've provided a Maya file of a Rigged hand that can be used for your app, which can be downloaded here: <a href="files/HandCoach_MRTK.zip"> Download HandCoach_MRTK.zip </a></span></span>

<span data-ttu-id="c7c88-152">![Maya 中的動畫指標範例](images/HandCoach/MayaSelect_Gif.gif)</span><span class="sxs-lookup"><span data-stu-id="c7c88-152">![Example of Animated Hands in Maya](images/HandCoach/MayaSelect_Gif.gif)</span></span><br>
<span data-ttu-id="c7c88-153">*在 Maya 中刺探方塊的動畫手勢範例*</span><span class="sxs-lookup"><span data-stu-id="c7c88-153">*Example of animated Hand Poking a box in Maya*</span></span>


<span data-ttu-id="c7c88-154">**建議的 authoring tool**</span><span class="sxs-lookup"><span data-stu-id="c7c88-154">**Recommended authoring tool**</span></span>

<span data-ttu-id="c7c88-155">在3D 演出者之間，許多選擇使用 [Autodesk 的 Maya，可以使用 HoloLens](https://www.youtube.com/watch?v=q0K3n0Gf8mA) 來轉換資產的建立方式。</span><span class="sxs-lookup"><span data-stu-id="c7c88-155">Among 3D artists, many choose to use [Autodesk’s Maya, which can use HoloLens](https://www.youtube.com/watch?v=q0K3n0Gf8mA) to transform the way assets are created.</span></span> <span data-ttu-id="c7c88-156">提供的手入檔案是 Maya 二進位檔案，因此建議使用 Maya 來建立動畫和匯出手。</span><span class="sxs-lookup"><span data-stu-id="c7c88-156">The hands file provided is a Maya Binary File, so it's recommended to use Maya to animate and export the hands.</span></span> <span data-ttu-id="c7c88-157">如果您想要使用其他3D 程式，以下是 <b>。FBX</b>： <a href="files/HandCoachMRTK_FBX.zip"> 下載 HandCoachMRTK_FBX.zip </a> 以建立您自己的控制器設定。</span><span class="sxs-lookup"><span data-stu-id="c7c88-157">If you prefer to use another 3D program, here's a <b>.FBX</b>: <a href="files/HandCoachMRTK_FBX.zip"> Download HandCoachMRTK_FBX.zip </a> to create your own controller setup.</span></span> 

<span data-ttu-id="c7c88-158">如果使用提供的可下載 maya 檔，建議您將 unity 中的手縮小為0.6。</span><span class="sxs-lookup"><span data-stu-id="c7c88-158">If using the downloadable maya Hand File provided, it's suggested to scale down the hands in unity to 0.6.</span></span>

<span data-ttu-id="c7c88-159">![範例： Maya 中的手教練裝備](images/HandCoach/MayaExample.png)</span><span class="sxs-lookup"><span data-stu-id="c7c88-159">![Example: Hand coach rig in Maya](images/HandCoach/MayaExample.png)</span></span><br>
<span data-ttu-id="c7c88-160">*Rigged 手*</span><span class="sxs-lookup"><span data-stu-id="c7c88-160">*Rigged Hands*</span></span>

### <a name="technical-specs"></a><span data-ttu-id="c7c88-161">技術規格</span><span class="sxs-lookup"><span data-stu-id="c7c88-161">Technical Specs</span></span>

*   <span data-ttu-id="c7c88-162">Maya Ascii 格式有兩個右手檔案可用</span><span class="sxs-lookup"><span data-stu-id="c7c88-162">Two handed File is available in Maya Ascii format</span></span>
*    <span data-ttu-id="c7c88-163">右邊和左方都提供 Maya 二進位格式</span><span class="sxs-lookup"><span data-stu-id="c7c88-163">Right and Left Hand is available in Maya Binary format</span></span>
*   <span data-ttu-id="c7c88-164">將 Maya 檔案設定為 24 FPS</span><span class="sxs-lookup"><span data-stu-id="c7c88-164">Set your Maya file to 24 FPS</span></span>
*   <span data-ttu-id="c7c88-165">在檔案中，有左方和右手邊，可用於兩個右手或單次手勢。</span><span class="sxs-lookup"><span data-stu-id="c7c88-165">Within the file, there's a left and right hand, which can be used for two handed or single-handed gestures.</span></span> <span data-ttu-id="c7c88-166">預設只會顯示右手邊。</span><span class="sxs-lookup"><span data-stu-id="c7c88-166">The right hand will only be visible by default.</span></span>
*   <span data-ttu-id="c7c88-167">建議將大約10個框架的緩衝區留在開頭和結尾，以淡化</span><span class="sxs-lookup"><span data-stu-id="c7c88-167">It's suggested to leave a buffer of about 10 frames at the beginning and end for fades</span></span>
*   <span data-ttu-id="c7c88-168">如果使用指定的目標建立物件的動畫，它的最佳作法是建立預設方塊或 Null 的動畫。</span><span class="sxs-lookup"><span data-stu-id="c7c88-168">If animating an object with a specified target, its best practice to animate to a Default box or Null.</span></span>
*   <span data-ttu-id="c7c88-169">如果手上有一個實體物件（例如方塊）的動畫，它的最佳作法是不要在 Maya 中製作轉譯的動畫，但等候在 Unity 或程式碼中建立動畫。</span><span class="sxs-lookup"><span data-stu-id="c7c88-169">If the hand is animating a physical object such as a box, its best practice to not animate the translation in Maya but wait to animate it in Unity or in Code.</span></span>
*   <span data-ttu-id="c7c88-170">可見的動畫應為1.5 秒，才能傳達有意義的資訊</span><span class="sxs-lookup"><span data-stu-id="c7c88-170">Visible Animation should be 1.5 secs for any meaningful information to be conveyed</span></span>
*   <span data-ttu-id="c7c88-171">當您感到滿意動畫時：</span><span class="sxs-lookup"><span data-stu-id="c7c88-171">When you feel satisfied with your animation:</span></span>
    *   <span data-ttu-id="c7c88-172">選取所有接點並製作主要畫面格</span><span class="sxs-lookup"><span data-stu-id="c7c88-172">Select all joints and bake key frames</span></span>
    *   <span data-ttu-id="c7c88-173">刪除控制器，選取接點和網狀，然後匯出為 FBX</span><span class="sxs-lookup"><span data-stu-id="c7c88-173">Delete the Controllers, Select the joints and mesh and export as an FBX</span></span>
    *  <span data-ttu-id="c7c88-174">如果有多個動畫，您可以使用 Maya 的內建遊戲匯出工具： https://knowledge.autodesk.com/support/maya/learn-explore/caas/CloudHelp/cloudhelp/2015/ENU/Maya/files/Game-Exporter-htm.html</span><span class="sxs-lookup"><span data-stu-id="c7c88-174">If there are Multiple Animations, you can use Maya’s built-in Game Exporter: https://knowledge.autodesk.com/support/maya/learn-explore/caas/CloudHelp/cloudhelp/2015/ENU/Maya/files/Game-Exporter-htm.html</span></span>

## <a name="exporting-from-maya"></a><span data-ttu-id="c7c88-175">從 Maya 匯出</span><span class="sxs-lookup"><span data-stu-id="c7c88-175">Exporting from Maya</span></span>

<span data-ttu-id="c7c88-176">當您滿意動畫之後</span><span class="sxs-lookup"><span data-stu-id="c7c88-176">After you're satisfied with your animation</span></span>
* <span data-ttu-id="c7c88-177">選取所有接點：選取 > 階層</span><span class="sxs-lookup"><span data-stu-id="c7c88-177">Select all joints: Select > Hierarchy</span></span>

     ![範例：功能表中的階層](images/HandCoach/Hierarchy.png)<br>
* <span data-ttu-id="c7c88-179">製作您的動畫：切換至動畫 > 按鍵 > 製作動畫</span><span class="sxs-lookup"><span data-stu-id="c7c88-179">Bake out your animation: Switch to Animation > Key > Bake Animation</span></span>

     ![範例：製作動畫功能表位置](images/HandCoach/BakeAnimation.png)<br>
* <span data-ttu-id="c7c88-181">刪除控制器 Rig： Outliner > MainR_Grp 或 MainL_Grp</span><span class="sxs-lookup"><span data-stu-id="c7c88-181">Delete the Controller Rig: Outliner > MainR_Grp or MainL_Grp</span></span>

     ![範例：控制器 Rig 功能表位置](images/HandCoach/ControllerRig.png)<br>

* <span data-ttu-id="c7c88-183">匯出為 FBX：選取 .JNT + 網格：檔案 > 匯出選取範圍 (選項方塊) > 匯出選取專案</span><span class="sxs-lookup"><span data-stu-id="c7c88-183">Export as FBX: Select JNT + Mesh: File > Export Selection (option box) > Export Selection</span></span>

     ![範例：匯出選取專案功能表位置](images/HandCoach/OptionBox.png)<br>

     ![範例：功能表位置](images/HandCoach/SelectionExport.png)<br>

     ![範例：匯出選項功能表位置](images/HandCoach/FBXSelection.png)<br>


 <span data-ttu-id="c7c88-187">當匯出為 FBX 並帶入 Unity 時，請將手向下調整為0.6。</span><span class="sxs-lookup"><span data-stu-id="c7c88-187">When exporting as an FBX and brought into Unity, scale the hands down to 0.6.</span></span> <span data-ttu-id="c7c88-188">我們發現這是實際顯示的完美平衡。</span><span class="sxs-lookup"><span data-stu-id="c7c88-188">We found that this was perfect balance for displaying the hands.</span></span> 

<span data-ttu-id="c7c88-189">![範例： Unity 設定](images/HandCoach/HandHintScale.png)</span><span class="sxs-lookup"><span data-stu-id="c7c88-189">![Example: Unity Settings](images/HandCoach/HandHintScale.png)</span></span><br>
<span data-ttu-id="c7c88-190">*在 MRTK 中找到 HandCoach_R 預製專案的 Unity 設定*</span><span class="sxs-lookup"><span data-stu-id="c7c88-190">*Unity Settings for HandCoach_R prefab found in MRTK*</span></span>


## <a name="implementing-hands-into-your-unity-project"></a><span data-ttu-id="c7c88-191">實際執行您的 Unity 專案</span><span class="sxs-lookup"><span data-stu-id="c7c88-191">Implementing Hands into your Unity project</span></span>

### <a name="best-practices"></a><span data-ttu-id="c7c88-192">最佳做法</span><span class="sxs-lookup"><span data-stu-id="c7c88-192">Best practices</span></span>

* <span data-ttu-id="c7c88-193">建議您將 unity 中的手縮小至0。6</span><span class="sxs-lookup"><span data-stu-id="c7c88-193">It's suggested to scale down the hands in unity to 0.6</span></span>
* <span data-ttu-id="c7c88-194">雙手應該播放兩次，如果未完成，則會持續迴圈直到手勢完成為止。</span><span class="sxs-lookup"><span data-stu-id="c7c88-194">Hands should be played twice and if not completed then continuously looped until gesture is completed.</span></span> <span data-ttu-id="c7c88-195">雙手應迴圈兩次，以確保使用者有時間註冊並查看手勢。</span><span class="sxs-lookup"><span data-stu-id="c7c88-195">The hands should be looped twice to ensure the user had time to register and see the gesture.</span></span> <span data-ttu-id="c7c88-196">手應該在迴圈之間淡入和縮小。</span><span class="sxs-lookup"><span data-stu-id="c7c88-196">The hands should fade in and out between loops.</span></span> 
 *  <span data-ttu-id="c7c88-197">如果 HL2 攝影機看到使用者的手，但使用者未進行需要的互動，則手會在10秒後出現。</span><span class="sxs-lookup"><span data-stu-id="c7c88-197">If user’s hands are visible by HL2 cameras but users aren't doing the interaction needed of them the hands will appear after 10 seconds.</span></span>
*   <span data-ttu-id="c7c88-198">如果 HL2 攝影機看不到使用者的手，就會在5秒後出現手。</span><span class="sxs-lookup"><span data-stu-id="c7c88-198">If user’s hands are NOT visible by HL2 cameras, the hands will appear after 5 seconds.</span></span>  
*   <span data-ttu-id="c7c88-199">如果在動畫中間的 HL2 攝影機會以明顯的方式追蹤使用者的手，動畫將會完成並淡出。</span><span class="sxs-lookup"><span data-stu-id="c7c88-199">If user’s hands are visibly tracked by HL2 cameras in the middle of the animation, the animation will complete and fade out.</span></span>
*   <span data-ttu-id="c7c88-200">如果您要包含語音，建議您將其對應至手的手勢。</span><span class="sxs-lookup"><span data-stu-id="c7c88-200">If you're including voice over, we suggest that it corresponds to the gesture of the hand.</span></span>
*   <span data-ttu-id="c7c88-201">如果您至少教授過一次，只要偵測到使用者停滯，請只重複手勢。</span><span class="sxs-lookup"><span data-stu-id="c7c88-201">If you've taught the hands at least once, only repeat the gesture if it's detected that the user is stuck.</span></span>
*   <span data-ttu-id="c7c88-202">如果特定的手指/手位置很重要，請確保使用者可以清楚地在動畫中看到這些細微差異。</span><span class="sxs-lookup"><span data-stu-id="c7c88-202">If specific finger/hand positions are critical, ensure users can clearly see these nuances in the animation.</span></span> <span data-ttu-id="c7c88-203">試著 angling 手，讓最重要的部分清楚可見。</span><span class="sxs-lookup"><span data-stu-id="c7c88-203">Try angling the hands so the most important parts are clearly visible.</span></span> 
* <span data-ttu-id="c7c88-204">如果您注意到手上的失真，您需要移至 Unity 的品質設定來提高骨骼數目。</span><span class="sxs-lookup"><span data-stu-id="c7c88-204">If you notice distortion on the hands, you need to go to Unity's Quality settings increase the number of bones.</span></span> 
 <span data-ttu-id="c7c88-205">移至 Unity 的 [編輯] > 專案設定 > 品質 > 其他 > Blend 加權。</span><span class="sxs-lookup"><span data-stu-id="c7c88-205">Go to Unity's Edit > Project Settings > Quality > Other > Blend Weights.</span></span> <span data-ttu-id="c7c88-206">確定已選取「4個骨骼」以查看平滑接點。</span><span class="sxs-lookup"><span data-stu-id="c7c88-206">Make sure "4 bones" are selected to see Smooth Joints.</span></span>

   ![範例：專案設定視窗](images/HandCoach/ProjectSettings.png)<br>


### <a name="what-to-avoid"></a><span data-ttu-id="c7c88-208">避免事項</span><span class="sxs-lookup"><span data-stu-id="c7c88-208">What to avoid</span></span>

* <span data-ttu-id="c7c88-209">調整手太大</span><span class="sxs-lookup"><span data-stu-id="c7c88-209">Scaling the Hands too large</span></span>
* <span data-ttu-id="c7c88-210">把手放在使用者附近</span><span class="sxs-lookup"><span data-stu-id="c7c88-210">placing the Hands too close to the user</span></span>
* <span data-ttu-id="c7c88-211">手中應只教授一次。</span><span class="sxs-lookup"><span data-stu-id="c7c88-211">Hands should only be taught once.</span></span> <span data-ttu-id="c7c88-212">透過教學可能會造成混淆和 messiness</span><span class="sxs-lookup"><span data-stu-id="c7c88-212">Over teaching can cause confusion and messiness</span></span>
* <span data-ttu-id="c7c88-213">將它帶入 Unity，請在這裡下載最新的 MRTK： https://github.com/microsoft/MixedRealityToolkit-Unity</span><span class="sxs-lookup"><span data-stu-id="c7c88-213">Bringing it into Unity, download the latest MRTK  here: https://github.com/microsoft/MixedRealityToolkit-Unity</span></span>
  * <span data-ttu-id="c7c88-214">材質： Teaching_Hand2</span><span class="sxs-lookup"><span data-stu-id="c7c88-214">Material: Teaching_Hand2</span></span>
  * <span data-ttu-id="c7c88-215">腳本：請參閱 MRTK 指導方針以取得<a href= "/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/hand-coach">MRTK</a>的指導方針</span><span class="sxs-lookup"><span data-stu-id="c7c88-215">Scripts: Refer to MRTK guidelines for <a href= "/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/hand-coach"> MRTK hand coach </a></span></span>
  * <span data-ttu-id="c7c88-216">每個專案的設定</span><span class="sxs-lookup"><span data-stu-id="c7c88-216">Per- project setting</span></span>
    * <span data-ttu-id="c7c88-217">設定為 UWP 的場景：您可以在設定 [Unity 專案](../develop/unity/Configure-Unity-Project.md) 中找到 Windows Mixed Reality 的指示。</span><span class="sxs-lookup"><span data-stu-id="c7c88-217">Scene set to UWP: Instruction can be found on the [Configure Unity Project](../develop/unity/Configure-Unity-Project.md) for Windows Mixed Reality</span></span>

## <a name="see-also"></a><span data-ttu-id="c7c88-218">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c7c88-218">See also</span></span>

* [<span data-ttu-id="c7c88-219">互動-基礎</span><span class="sxs-lookup"><span data-stu-id="c7c88-219">Interaction-fundamentals</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="c7c88-220">資產建立流程</span><span class="sxs-lookup"><span data-stu-id="c7c88-220">Asset Creation Process</span></span>](asset-creation-process.md)
* [<span data-ttu-id="c7c88-221">手勢</span><span class="sxs-lookup"><span data-stu-id="c7c88-221">Gestures</span></span>](./interaction-fundamentals.md)
* [<span data-ttu-id="c7c88-222">安裝工具</span><span class="sxs-lookup"><span data-stu-id="c7c88-222">Install the Tools</span></span>](../develop/install-the-tools.md)
* [<span data-ttu-id="c7c88-223">設定 Unity 專案</span><span class="sxs-lookup"><span data-stu-id="c7c88-223">Configure Unity Project</span></span>](../develop/unity/Configure-Unity-Project.md)
* [<span data-ttu-id="c7c88-224">Unity 開發概觀</span><span class="sxs-lookup"><span data-stu-id="c7c88-224">Unity development overview</span></span>](../develop/unity/unity-development-overview.md)
* [<span data-ttu-id="c7c88-225">MRTK 101</span><span class="sxs-lookup"><span data-stu-id="c7c88-225">MRTK 101</span></span>](/windows/mixed-reality/mrtk-unity/)