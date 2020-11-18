---
title: 頭部注視並佇留
description: 頭部注視並佇留輸入模型的概觀
author: hferrone
ms.author: v-hferrone
ms.date: 05/13/2019
ms.topic: article
keywords: 混合的現實、注視、停留、互動、設計、混合現實耳機、windows mixed reality 耳機、虛擬實境耳機、HoloLens、MRTK、混合現實工具組、ux、指導方針、清單視圖
ms.openlocfilehash: abedff5a273816f49419c7823b96eda1d474e336
ms.sourcegitcommit: 4f3ef057a285be2e260615e5d6c41f00d15d08f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2020
ms.locfileid: "94702314"
---
# <a name="head-gaze-and-dwell"></a><span data-ttu-id="b19b6-104">頭部注視並佇留</span><span class="sxs-lookup"><span data-stu-id="b19b6-104">Head-gaze and dwell</span></span>

<span data-ttu-id="b19b6-105">當手上拿著工具和組件時，手勢可以很繁瑣或不可能進行。</span><span class="sxs-lookup"><span data-stu-id="b19b6-105">When hands are occupied with tools and parts, gestures can be tedious or impossible.</span></span> <span data-ttu-id="b19b6-106">語音命令 (例如手勢) 在特定情境 (例如極度喧噪的情況) 中可能不大可靠。</span><span class="sxs-lookup"><span data-stu-id="b19b6-106">Voice commands, like gestures, can be unreliable in certain contexts, for example under excessively loud conditions.</span></span> <span data-ttu-id="b19b6-107">此外，使用語音來控制電腦並不十分普遍，但的確可取得資料流！</span><span class="sxs-lookup"><span data-stu-id="b19b6-107">Additionally, using voice to control computers isn't universally common, but it certainly is gaining steam!</span></span> <span data-ttu-id="b19b6-108">「頭部注視並佇留」提供最熟悉且容易掌握的機制，可在 HoloLens 上以抬頭和免持式運作。</span><span class="sxs-lookup"><span data-stu-id="b19b6-108">Head-gaze and dwell offers the most familiar and easy-to-master mechanism for working heads-up and hands-free on HoloLens.</span></span> <span data-ttu-id="b19b6-109">此外，「頭部注視並佇留」 100% 可靠，完全不受雜訊干擾，而且在作業環境中也沒有靜音限制。</span><span class="sxs-lookup"><span data-stu-id="b19b6-109">Additionally, head-gaze and dwell is 100% reliable independent of noise interference nor silence constraints in the operating environment.</span></span>

## <a name="scenarios"></a><span data-ttu-id="b19b6-110">案例</span><span class="sxs-lookup"><span data-stu-id="b19b6-110">Scenarios</span></span>

<span data-ttu-id="b19b6-111">當人的手中有其他工作忙碌的情況下，您可以擅長，而語音也不是100% 的可靠性，或是因為環境或社交條件約束而無法使用。</span><span class="sxs-lookup"><span data-stu-id="b19b6-111">Head-gaze and dwell excels in scenarios where a person's hands are busy with other tasks, and voice isn't 100% reliable or available due to environmental or social constraints.</span></span> <span data-ttu-id="b19b6-112">穿戴 HoloLens 的人員在修理汽車引擎時覆疊參考資訊就是個不錯的範例。</span><span class="sxs-lookup"><span data-stu-id="b19b6-112">A good example is a person wearing a HoloLens to overlay reference information while repairing a car engine.</span></span> <span data-ttu-id="b19b6-113">他們的雙手忙著拿起工具，或在靠向引擎室時支撐其身體。</span><span class="sxs-lookup"><span data-stu-id="b19b6-113">Their hands are busy with tools or supporting their body as they lean into the engine compartment.</span></span> <span data-ttu-id="b19b6-114">車庫空間很吵雜，充斥著工具的碰撞和唧唧聲，讓語音命令變得難以使用。</span><span class="sxs-lookup"><span data-stu-id="b19b6-114">The garage space is loud, with the constant banging and buzzing of tools, making voice commands difficult.</span></span> <span data-ttu-id="b19b6-115">前端和停留可讓使用 HoloLens 的人員安心地流覽其參考資料，而不會中斷其工作流程。</span><span class="sxs-lookup"><span data-stu-id="b19b6-115">Head-gaze and dwell allows the person using the HoloLens to confidently navigate their reference material without interrupting their workflow.</span></span> 

## <a name="device-support"></a><span data-ttu-id="b19b6-116">裝置支援</span><span class="sxs-lookup"><span data-stu-id="b19b6-116">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="b19b6-117"><strong>輸入模型</strong></span><span class="sxs-lookup"><span data-stu-id="b19b6-117"><strong>Input model</strong></span></span></td>
        <td><span data-ttu-id="b19b6-118"><a href="../hololens-hardware-details.md"><strong>HoloLens (第 1 代)</strong></a></span><span class="sxs-lookup"><span data-stu-id="b19b6-118"><a href="../hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="b19b6-119"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="b19b6-119"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="b19b6-120"><a href="../discover/immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></span><span class="sxs-lookup"><span data-stu-id="b19b6-120"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="b19b6-121">頭部注視並佇留</span><span class="sxs-lookup"><span data-stu-id="b19b6-121">Head-gaze and dwell</span></span></td>
        <td><span data-ttu-id="b19b6-122">✔️ 建議使用</span><span class="sxs-lookup"><span data-stu-id="b19b6-122">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="b19b6-123">✔️ 建議使用</span><span class="sxs-lookup"><span data-stu-id="b19b6-123">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="b19b6-124">✔️ 建議使用</span><span class="sxs-lookup"><span data-stu-id="b19b6-124">✔️ Recommended</span></span></td>
    </tr>
</table>


## <a name="design-principles"></a><span data-ttu-id="b19b6-125">設計原則</span><span class="sxs-lookup"><span data-stu-id="b19b6-125">Design principles</span></span>

<span data-ttu-id="b19b6-126">**避免「使用注視作為手段」**</span><span class="sxs-lookup"><span data-stu-id="b19b6-126">**Avoid "Gaze as a weapon"**</span></span>

<span data-ttu-id="b19b6-127">「頭部注視並佇留」需要直覺式視覺化回饋，但是太多回饋可能會引起焦慮。</span><span class="sxs-lookup"><span data-stu-id="b19b6-127">Head-gaze and dwell requires visual feedback to be intuitive, but too much feedback can induce anxiety.</span></span> <span data-ttu-id="b19b6-128">回饋應協助使用者知道他們所定向的目標，但不會針對其意圖予以自動選取。</span><span class="sxs-lookup"><span data-stu-id="b19b6-128">The feedback should help a user know what they're targeting, but not auto-select it against their intent.</span></span> <span data-ttu-id="b19b6-129">讀取文字、圖示和標籤需要額外的考量，在選取之前為人員提供吸收資訊的空間。</span><span class="sxs-lookup"><span data-stu-id="b19b6-129">Reading text, icons, and labels requires extra consideration to provide a person room to absorb the information before selecting.</span></span>
    
<span data-ttu-id="b19b6-130">**追求 Goldilocks 速度**</span><span class="sxs-lookup"><span data-stu-id="b19b6-130">**Seek Goldilocks speed**</span></span>
    
<span data-ttu-id="b19b6-131">佇留互動可根據瀏覽的影響而有不同的計時器 - 較多常用功能通常受益於更快速的填滿時間，而較多衍生性功能則可受益於較長的填滿時間。</span><span class="sxs-lookup"><span data-stu-id="b19b6-131">Dwell interactions can have different timers based on impact of navigation - more frequently used functions will generally benefit from faster fill times, while more consequential functions may benefit from longer fill times.</span></span> <span data-ttu-id="b19b6-132">使用填滿效果來顯示這些計時器時，填滿色彩的動畫曲線對於較快速填滿時間的感覺有正面影響。</span><span class="sxs-lookup"><span data-stu-id="b19b6-132">When using a fill-effect to show these timers, animation curves of the fill color can positively influence a feeling of faster fill times.</span></span> <span data-ttu-id="b19b6-133">應可慮讓使用者決定快速/中等/緩慢填滿速度覆寫。</span><span class="sxs-lookup"><span data-stu-id="b19b6-133">Consideration should be taken to enable user decision from fast/medium/slow fill speed overrides.</span></span>
    
<span data-ttu-id="b19b6-134">**Say no-no to yo-yo 效應**</span><span class="sxs-lookup"><span data-stu-id="b19b6-134">**Say no-no to yo-yo effect**</span></span>

<span data-ttu-id="b19b6-135">溜溜球效應是當內容和「頭部注視並佇留」控制項的放置方式強迫人們要不斷地重複仰視和俯視時，可能出現的不舒適頭部移動模式。</span><span class="sxs-lookup"><span data-stu-id="b19b6-135">The yo-yo effect is an uncomfortable pattern of head movement that can emerge when the placement of content and head-gaze and dwell controls forces people to constantly look up and down repeatedly.</span></span> <span data-ttu-id="b19b6-136">例如，底部的 [流覽] 和 [停留] 按鈕的清單導覽會引發停留的迴圈、在結果中查看、向下切入到停留等等。這種產生的模式不舒服，而且應該避免將導覽控制項放在需要較低的集中位置。</span><span class="sxs-lookup"><span data-stu-id="b19b6-136">For example, a list nav with the head-gaze and dwell button at the bottom induces a loop of - look down to dwell, look up at results, look down to dwell, etc. This resulting pattern is uncomfortable and should be avoided by placing navigation controls in a centralized location that requires less back-and-forth.</span></span> <span data-ttu-id="b19b6-137">與效應相關的佇留按鈕放置方式，對於舒適度而言很重要。</span><span class="sxs-lookup"><span data-stu-id="b19b6-137">Placement of dwell buttons relative to their effects becomes important for comfort.</span></span>

<br>

---


## <a name="ux-guidelines-and-best-practices"></a><span data-ttu-id="b19b6-138">UX 指導方針和最佳作法</span><span class="sxs-lookup"><span data-stu-id="b19b6-138">UX Guidelines and best practices</span></span>

### <a name="target-sizes"></a><span data-ttu-id="b19b6-139">目標大小</span><span class="sxs-lookup"><span data-stu-id="b19b6-139">Target sizes</span></span>
  <span data-ttu-id="b19b6-140">為了方便存取，前端和停留目標必須夠大，才能輕鬆地查看，並且在指定的時間為目標保持一個穩定的狀態。</span><span class="sxs-lookup"><span data-stu-id="b19b6-140">To be easily accessible, head-gaze and dwell targets need to be large enough to comfortably look at, and hold one's head stable on the target for the prescribed time.</span></span> <span data-ttu-id="b19b6-141">我們建議的最小目標大小為2度，以達成最舒適的體驗。</span><span class="sxs-lookup"><span data-stu-id="b19b6-141">We recommend a minimum target size of 2 degrees to achieve the most comfortable experience.</span></span> 

### <a name="visual-feedback"></a><span data-ttu-id="b19b6-142">視覺化回饋</span><span class="sxs-lookup"><span data-stu-id="b19b6-142">Visual feedback</span></span>

<span data-ttu-id="b19b6-143">使用放射狀填滿來表示佇留計時器時，從按鈕中心開始。</span><span class="sxs-lookup"><span data-stu-id="b19b6-143">When using a radial fill to represent the dwell timer, start from the center of button.</span></span> <span data-ttu-id="b19b6-144">相較於不同按鈕上的所有不同方向，一致的回應比較不容易混淆。</span><span class="sxs-lookup"><span data-stu-id="b19b6-144">A consistent response is less confusing than all different directions on different buttons.</span></span> 

  * <span data-ttu-id="b19b6-145">有方向的互動 (例如，向上/向下/左/右瀏覽等) 可以打破此規則。</span><span class="sxs-lookup"><span data-stu-id="b19b6-145">This rule can be broken though for directional interactions (e.g., nav up/down/left/right, etc.).</span></span> <span data-ttu-id="b19b6-146">例如，Microsoft Dynamics 365 Guides 讓「下一頁/上一頁」成為左右填滿則屬例外狀況。</span><span class="sxs-lookup"><span data-stu-id="b19b6-146">For example, Microsoft Dynamics 365 Guides makes an exception on NEXT/BACK being left right fills.</span></span>
  * <span data-ttu-id="b19b6-147">在關閉按鈕等情境下，請考慮從外部反轉放射狀填滿。</span><span class="sxs-lookup"><span data-stu-id="b19b6-147">Consider inverting radial fill from outside, for scenarios like toggling a button off.</span></span> <span data-ttu-id="b19b6-148">按壓按鈕的反向感覺是可維護的良好視覺模式。</span><span class="sxs-lookup"><span data-stu-id="b19b6-148">The inverse feeling of pushing a button is a nice visual pattern to maintain.</span></span> 

### <a name="progressive-disclosure"></a><span data-ttu-id="b19b6-149">漸進式揭露</span><span class="sxs-lookup"><span data-stu-id="b19b6-149">Progressive disclosure</span></span>

<span data-ttu-id="b19b6-150">漸進式揭露表示只有盡可能詳細顯示與互動的每個階段相關。</span><span class="sxs-lookup"><span data-stu-id="b19b6-150">Progressive disclosure means only showing as much detail as is relevant at each stage of an interaction.</span></span> <span data-ttu-id="b19b6-151">對於佇留，這表示佇留目標會顯現於醒目提示 (例如，在清單控制項中)。</span><span class="sxs-lookup"><span data-stu-id="b19b6-151">For dwell, that means the dwell target is revealed on highlight (e.g., in a list control).</span></span>

 ### <a name="oversized-targets"></a><span data-ttu-id="b19b6-152">過大的目標</span><span class="sxs-lookup"><span data-stu-id="b19b6-152">Oversized targets</span></span>
<span data-ttu-id="b19b6-153">佇留區域可大於非使用中的圖示，使其更容易使用，例如 Microsoft Dynamics 365 Guides 中的 [上一頁] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="b19b6-153">Dwell region can be larger than inactive icon to make it easier to use, like the Back button in Microsoft Dynamics 365 Guides.</span></span>

### <a name="prevent-flickering-with-delayed-feedback"></a><span data-ttu-id="b19b6-154">使用延遲回饋防止閃爍</span><span class="sxs-lookup"><span data-stu-id="b19b6-154">Prevent flickering with delayed feedback</span></span>
<span data-ttu-id="b19b6-155">在開始視覺化回饋前使用短暫延遲，可避免有人經過佇留目標時發生閃爍。</span><span class="sxs-lookup"><span data-stu-id="b19b6-155">Use a short delay before starting visual feedback to avoid flickering when someone passes over a dwell target.</span></span>
* <span data-ttu-id="b19b6-156">針對頻繁互動的按鈕，請將延遲保持在很短的時間，讓應用程式感覺很慢。</span><span class="sxs-lookup"><span data-stu-id="b19b6-156">For buttons interacted with frequently, keep the delay very short so the application feels reactive.</span></span>
* <span data-ttu-id="b19b6-157">對於不常進行互動的按鈕而言，較長的延遲可能適合避免介面感覺 twitchy。</span><span class="sxs-lookup"><span data-stu-id="b19b6-157">For buttons that are interacted with infrequently, a longer delay can be appropriate to avoid the interface feeling twitchy.</span></span>


<br>

---

## <a name="ui-patterns"></a><span data-ttu-id="b19b6-158">UI 模式</span><span class="sxs-lookup"><span data-stu-id="b19b6-158">UI patterns</span></span>

### <a name="high-frequency-buttons"></a><span data-ttu-id="b19b6-159">高頻率按鈕</span><span class="sxs-lookup"><span data-stu-id="b19b6-159">High frequency buttons</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="b19b6-160">高頻率按鈕是常用於整個應用程式的按鈕。</span><span class="sxs-lookup"><span data-stu-id="b19b6-160">High frequency buttons are buttons that are used commonly throughout an application.</span></span> <span data-ttu-id="b19b6-161">Microsoft Dynamics 365 Guides 中的下一頁和上一頁按鈕都是不錯的範例。</span><span class="sxs-lookup"><span data-stu-id="b19b6-161">A good example of these are the next and back buttons in Microsoft Dynamics 365 Guides.</span></span><br>
        <br>
        <span data-ttu-id="b19b6-162">**建議**</span><span class="sxs-lookup"><span data-stu-id="b19b6-162">**Recommendations**</span></span><br>
  * <span data-ttu-id="b19b6-163">高頻率按鈕應該很大，而且可以更輕鬆地使用列印頭</span><span class="sxs-lookup"><span data-stu-id="b19b6-163">High frequency buttons should be large, easier to hit with head-gaze</span></span>
  * <span data-ttu-id="b19b6-164">保持近乎眼睛的高度，以避免人體工學緊張。</span><span class="sxs-lookup"><span data-stu-id="b19b6-164">Stay near eye height to avoid ergonomic straining.</span></span><br>
        <br>
<span data-ttu-id="b19b6-165">*影像： Microsoft Dynamics 365 指南 [下一步] 按鈕*</span><span class="sxs-lookup"><span data-stu-id="b19b6-165">*Image: Microsoft Dynamics 365 Guides next button*</span></span>
    :::column-end:::
        :::column:::
       ![Microsoft Dynamics 365 指南 [下一步] 按鈕](images/GuideNextButton.png)<br>
    :::column-end:::
:::row-end:::

<br>

---


### <a name="low-frequency-buttons"></a><span data-ttu-id="b19b6-167">低頻率按鈕</span><span class="sxs-lookup"><span data-stu-id="b19b6-167">Low frequency buttons</span></span>
<span data-ttu-id="b19b6-168">低頻率按鈕是整個應用程式中不會定期互動的按鈕。</span><span class="sxs-lookup"><span data-stu-id="b19b6-168">Low frequency buttons are buttons that are not interacted with as regularly throughout the application.</span></span> <span data-ttu-id="b19b6-169">可存取 [設定] 功能表的按鈕，或可清除所有工作的按鈕都是不錯的範例。</span><span class="sxs-lookup"><span data-stu-id="b19b6-169">A good example might be a button to access the settings menu, or a button to clear all work.</span></span>

* <span data-ttu-id="b19b6-170">嘗試讓這些按鈕不在常用的頭部注視路徑中，以免意外啟動。</span><span class="sxs-lookup"><span data-stu-id="b19b6-170">Try to keep these buttons out of the way of frequent head-gaze paths to avoid accidental activation.</span></span> 

<br>

---

### <a name="confirmations"></a><span data-ttu-id="b19b6-171">確認</span><span class="sxs-lookup"><span data-stu-id="b19b6-171">Confirmations</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="b19b6-172">當某個動作有重大影響時 (例如收費、刪除工作或開始長時間處理)，最好確認個人要選取按鈕。</span><span class="sxs-lookup"><span data-stu-id="b19b6-172">When an action has significant impact, like charging money, deleting work, or starting a long process, it is useful to confirm that a person meant to select a button.</span></span><br>
        <br>
        <span data-ttu-id="b19b6-173">**建議**</span><span class="sxs-lookup"><span data-stu-id="b19b6-173">**Recommendations**</span></span><br>
  * <span data-ttu-id="b19b6-174">在主要按鈕上顯示選取醒目提示。</span><span class="sxs-lookup"><span data-stu-id="b19b6-174">Show selection highlight on main button.</span></span>
  * <span data-ttu-id="b19b6-175">與選取醒目提示同時顯示佇留目標。</span><span class="sxs-lookup"><span data-stu-id="b19b6-175">Reveal dwell target at same time as selection highlight.</span></span>
  * <span data-ttu-id="b19b6-176">對於次要按鈕，顯示頭部注視的佇留目標。</span><span class="sxs-lookup"><span data-stu-id="b19b6-176">For the secondary button, reveal the dwell target on head-gaze.</span></span><br>
        <br>
<span data-ttu-id="b19b6-177">*影像： Microsoft Dynamics 365 指南確認對話方塊*</span><span class="sxs-lookup"><span data-stu-id="b19b6-177">*Image: Microsoft Dynamics 365 Guides confirmation dialog*</span></span>
    :::column-end:::
        :::column:::
       ![Microsoft Dynamics 365 指南確認對話方塊](images/GuidesConfirmation.png)<br>
    :::column-end:::
:::row-end:::
        
<br>

---

### <a name="toggle-buttons"></a><span data-ttu-id="b19b6-179">切換按鈕</span><span class="sxs-lookup"><span data-stu-id="b19b6-179">Toggle buttons</span></span>
<span data-ttu-id="b19b6-180">切換按鈕需要一些微妙的邏輯，才能正常運作。</span><span class="sxs-lookup"><span data-stu-id="b19b6-180">Toggle buttons require some nuanced logic to work properly.</span></span> <span data-ttu-id="b19b6-181">當人員佇留在切換按鈕並啟動它時，他們需要結束按鈕，然後回頭重新啟動佇留邏輯。</span><span class="sxs-lookup"><span data-stu-id="b19b6-181">When a person dwells on a toggle button and actives it, they need to exit the button and then return to restart the dwell logic.</span></span> <span data-ttu-id="b19b6-182">切換按鈕會有清楚的作用與非作用中狀態很重要。</span><span class="sxs-lookup"><span data-stu-id="b19b6-182">It is important that togglable buttons have a clear active versus inactive state.</span></span> 

<br>

---

### <a name="list-views"></a><span data-ttu-id="b19b6-183">清單檢視</span><span class="sxs-lookup"><span data-stu-id="b19b6-183">List views</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="b19b6-184">列出視圖會針對前端和停留輸入提供特定挑戰。</span><span class="sxs-lookup"><span data-stu-id="b19b6-184">List views present a particular challenge for head-gaze and dwell input.</span></span> <span data-ttu-id="b19b6-185">人們需要能夠掃描內容，而不覺得必須偷偷摸摸地環顧佇留目標。</span><span class="sxs-lookup"><span data-stu-id="b19b6-185">People need to be able to scan the content without feeling like that have to tiptoe around the dwell targets.</span></span><br>
        <br>
<span data-ttu-id="b19b6-186">**建議**</span><span class="sxs-lookup"><span data-stu-id="b19b6-186">**Recommendations**</span></span><br>
  * <span data-ttu-id="b19b6-187">當標頭 gazed 但不會開始停留時，請將整個資料列反白顯示，除非前端看著特定的停留目標。</span><span class="sxs-lookup"><span data-stu-id="b19b6-187">Have the entire row highlight when head-gazed but doesn’t begin dwell unless head-gaze is on the specific dwell target.</span></span>
  * <span data-ttu-id="b19b6-188">當資料列反白顯示以在視覺雜訊上剪下時，才會顯示停留目標。</span><span class="sxs-lookup"><span data-stu-id="b19b6-188">Only show the dwell target when the row is highlighted to cut down on visual noise.</span></span>
  * <span data-ttu-id="b19b6-189">與停留目標的位置清楚且一致。</span><span class="sxs-lookup"><span data-stu-id="b19b6-189">Be clear and consistent with the position of dwell targets.</span></span>
  * <span data-ttu-id="b19b6-190">請勿同時顯示所有停留目標，以避免重複的 UI。</span><span class="sxs-lookup"><span data-stu-id="b19b6-190">Don't show all dwell targets at once to avoid repetitive UI.</span></span>
  * <span data-ttu-id="b19b6-191">盡可能重複使用相同的模式，以建立 UX 熟悉度。</span><span class="sxs-lookup"><span data-stu-id="b19b6-191">Re-use the same pattern as often as possible to establish UX familiarity.</span></span><br>
        <br>
<span data-ttu-id="b19b6-192">*影像： Microsoft Dynamics 365 指南清單*</span><span class="sxs-lookup"><span data-stu-id="b19b6-192">*Image: Microsoft Dynamics 365 Guides list*</span></span>
    :::column-end:::
        :::column:::
       ![Microsoft Dynamics 365 指南清單](images/GuidesListView.png)<br>
    :::column-end:::
:::row-end:::

<br>

---
 
 ## <a name="see-also"></a><span data-ttu-id="b19b6-194">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b19b6-194">See also</span></span>
* [<span data-ttu-id="b19b6-195">目光和行動</span><span class="sxs-lookup"><span data-stu-id="b19b6-195">Gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="b19b6-196">手 - 直接操作</span><span class="sxs-lookup"><span data-stu-id="b19b6-196">Hands - Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="b19b6-197">手 - 手勢</span><span class="sxs-lookup"><span data-stu-id="b19b6-197">Hands - Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="b19b6-198">手 - 指向和行動</span><span class="sxs-lookup"><span data-stu-id="b19b6-198">Hands - Point and commit</span></span>](point-and-commit.md)
* [<span data-ttu-id="b19b6-199">本能互動</span><span class="sxs-lookup"><span data-stu-id="b19b6-199">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="b19b6-200">語音輸入</span><span class="sxs-lookup"><span data-stu-id="b19b6-200">Voice input</span></span>](voice-input.md)
