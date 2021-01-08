---
title: 頭部注視並佇留
description: 開始使用前端和停留輸入模型的總覽，包括常見案例和設計原則。
author: hferrone
ms.author: v-hferrone
ms.date: 05/13/2019
ms.topic: article
keywords: 混合的現實、注視、停留、互動、設計、混合現實耳機、windows mixed reality 耳機、虛擬實境耳機、HoloLens、MRTK、混合現實工具組、ux、指導方針、清單視圖
ms.openlocfilehash: 2bfd984a466c1ccd3913e889ca57663800f46380
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2021
ms.locfileid: "98007078"
---
# <a name="head-gaze-and-dwell"></a><span data-ttu-id="0b4f7-104">頭部注視並佇留</span><span class="sxs-lookup"><span data-stu-id="0b4f7-104">Head-gaze and dwell</span></span>

<span data-ttu-id="0b4f7-105">當手上拿著工具和組件時，手勢可以很繁瑣或不可能進行。</span><span class="sxs-lookup"><span data-stu-id="0b4f7-105">When hands are occupied with tools and parts, gestures can be tedious or impossible.</span></span> <span data-ttu-id="0b4f7-106">語音命令 (例如手勢) 在特定情境 (例如極度喧噪的情況) 中可能不大可靠。</span><span class="sxs-lookup"><span data-stu-id="0b4f7-106">Voice commands, like gestures, can be unreliable in certain contexts, for example under excessively loud conditions.</span></span> <span data-ttu-id="0b4f7-107">此外，使用語音來控制電腦並不十分普遍，但的確可取得資料流！</span><span class="sxs-lookup"><span data-stu-id="0b4f7-107">Additionally, using voice to control computers isn't universally common, but it certainly is gaining steam!</span></span> <span data-ttu-id="0b4f7-108">「頭部注視並佇留」提供最熟悉且容易掌握的機制，可在 HoloLens 上以抬頭和免持式運作。</span><span class="sxs-lookup"><span data-stu-id="0b4f7-108">Head-gaze and dwell offers the most familiar and easy-to-master mechanism for working heads-up and hands-free on HoloLens.</span></span> <span data-ttu-id="0b4f7-109">此外，「頭部注視並佇留」 100% 可靠，完全不受雜訊干擾，而且在作業環境中也沒有靜音限制。</span><span class="sxs-lookup"><span data-stu-id="0b4f7-109">Additionally, head-gaze and dwell is 100% reliable independent of noise interference nor silence constraints in the operating environment.</span></span>

## <a name="scenarios"></a><span data-ttu-id="0b4f7-110">案例</span><span class="sxs-lookup"><span data-stu-id="0b4f7-110">Scenarios</span></span>

<span data-ttu-id="0b4f7-111">當人的手中有其他工作忙碌的情況下，前端和停留就很好用。</span><span class="sxs-lookup"><span data-stu-id="0b4f7-111">Head-gaze and dwell is great in scenarios where a person's hands are busy with other tasks.</span></span> <span data-ttu-id="0b4f7-112">當語音不是100% 可靠或因為環境或社交條件約束而無法使用時，此功能也很有用。</span><span class="sxs-lookup"><span data-stu-id="0b4f7-112">The feature is also useful when voice isn't 100% reliable or available because of environmental or social constraints.</span></span> <span data-ttu-id="0b4f7-113">穿戴 HoloLens 的人員在修理汽車引擎時覆疊參考資訊就是個不錯的範例。</span><span class="sxs-lookup"><span data-stu-id="0b4f7-113">A good example is a person wearing a HoloLens to overlay reference information while repairing a car engine.</span></span> <span data-ttu-id="0b4f7-114">他們的雙手忙著拿起工具，或在靠向引擎室時支撐其身體。</span><span class="sxs-lookup"><span data-stu-id="0b4f7-114">Their hands are busy with tools or supporting their body as they lean into the engine compartment.</span></span> <span data-ttu-id="0b4f7-115">車庫空間很吵雜，充斥著工具的碰撞和唧唧聲，讓語音命令變得難以使用。</span><span class="sxs-lookup"><span data-stu-id="0b4f7-115">The garage space is loud, with the constant banging and buzzing of tools, making voice commands difficult.</span></span> <span data-ttu-id="0b4f7-116">前端和停留可讓使用 HoloLens 的人員安心地流覽其參考資料，而不會中斷其工作流程。</span><span class="sxs-lookup"><span data-stu-id="0b4f7-116">Head-gaze and dwell allows the person using the HoloLens to confidently navigate their reference material without interrupting their workflow.</span></span> 

## <a name="device-support"></a><span data-ttu-id="0b4f7-117">裝置支援</span><span class="sxs-lookup"><span data-stu-id="0b4f7-117">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="0b4f7-118"><strong>輸入模型</strong></span><span class="sxs-lookup"><span data-stu-id="0b4f7-118"><strong>Input model</strong></span></span></td>
        <td><span data-ttu-id="0b4f7-119"><a href="../hololens-hardware-details.md"><strong>HoloLens (第 1 代)</strong></a></span><span class="sxs-lookup"><span data-stu-id="0b4f7-119"><a href="../hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="0b4f7-120"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="0b4f7-120"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="0b4f7-121"><a href="../discover/immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></span><span class="sxs-lookup"><span data-stu-id="0b4f7-121"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="0b4f7-122">頭部注視並佇留</span><span class="sxs-lookup"><span data-stu-id="0b4f7-122">Head-gaze and dwell</span></span></td>
        <td><span data-ttu-id="0b4f7-123">✔️ 建議使用</span><span class="sxs-lookup"><span data-stu-id="0b4f7-123">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="0b4f7-124">✔️ 建議使用</span><span class="sxs-lookup"><span data-stu-id="0b4f7-124">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="0b4f7-125">✔️ 建議使用</span><span class="sxs-lookup"><span data-stu-id="0b4f7-125">✔️ Recommended</span></span></td>
    </tr>
</table>


## <a name="design-principles"></a><span data-ttu-id="0b4f7-126">設計原則</span><span class="sxs-lookup"><span data-stu-id="0b4f7-126">Design principles</span></span>

<span data-ttu-id="0b4f7-127">**避免「使用注視作為手段」**</span><span class="sxs-lookup"><span data-stu-id="0b4f7-127">**Avoid "Gaze as a weapon"**</span></span>

<span data-ttu-id="0b4f7-128">「頭部注視並佇留」需要直覺式視覺化回饋，但是太多回饋可能會引起焦慮。</span><span class="sxs-lookup"><span data-stu-id="0b4f7-128">Head-gaze and dwell requires visual feedback to be intuitive, but too much feedback can induce anxiety.</span></span> <span data-ttu-id="0b4f7-129">意見反應應可協助使用者瞭解他們的目標，但不會根據其意圖來將其反或。</span><span class="sxs-lookup"><span data-stu-id="0b4f7-129">The feedback should help a user know what they're targeting, but not autoselect it against their intent.</span></span> <span data-ttu-id="0b4f7-130">讀取文字、圖示和標籤時，您必須提供使用者在選取之前吸收資訊的時間。</span><span class="sxs-lookup"><span data-stu-id="0b4f7-130">When reading text, icons, and labels, you need to provide users time to absorb the information before selecting.</span></span>
    
<span data-ttu-id="0b4f7-131">**追求 Goldilocks 速度**</span><span class="sxs-lookup"><span data-stu-id="0b4f7-131">**Seek Goldilocks speed**</span></span>
    
<span data-ttu-id="0b4f7-132">佇留互動可根據瀏覽的影響而有不同的計時器 - 較多常用功能通常受益於更快速的填滿時間，而較多衍生性功能則可受益於較長的填滿時間。</span><span class="sxs-lookup"><span data-stu-id="0b4f7-132">Dwell interactions can have different timers based on impact of navigation - more frequently used functions will generally benefit from faster fill times, while more consequential functions may benefit from longer fill times.</span></span> <span data-ttu-id="0b4f7-133">使用填滿效果來顯示這些計時器時，填滿色彩的動畫曲線對於較快速填滿時間的感覺有正面影響。</span><span class="sxs-lookup"><span data-stu-id="0b4f7-133">When using a fill-effect to show these timers, animation curves of the fill color can positively influence a feeling of faster fill times.</span></span> <span data-ttu-id="0b4f7-134">應可慮讓使用者決定快速/中等/緩慢填滿速度覆寫。</span><span class="sxs-lookup"><span data-stu-id="0b4f7-134">Consideration should be taken to enable user decision from fast/medium/slow fill speed overrides.</span></span>
    
<span data-ttu-id="0b4f7-135">**Say no-no to yo-yo 效應**</span><span class="sxs-lookup"><span data-stu-id="0b4f7-135">**Say no-no to yo-yo effect**</span></span>

<span data-ttu-id="0b4f7-136">Yo 效果是一種不舒服的標頭移動模式，它會在內容放置和前端/停留控制項強制使用者重複查詢時發生。</span><span class="sxs-lookup"><span data-stu-id="0b4f7-136">The yo-yo effect is an uncomfortable head movement pattern that happens when the content placement and head-gaze/dwell controls forces people to look up and down repeatedly.</span></span> <span data-ttu-id="0b4f7-137">例如，底部的 [流覽] 和 [停留] 按鈕的清單導覽會引發停留的迴圈、在結果中查看、向下切入到停留等等。</span><span class="sxs-lookup"><span data-stu-id="0b4f7-137">For example, a list nav with the head-gaze and dwell button at the bottom induces a loop of - look down to dwell, look up at results, look down to dwell, and so on.</span></span> <span data-ttu-id="0b4f7-138">產生的模式不舒服，因此建議您將導覽控制項放在需要較少的集中位置。</span><span class="sxs-lookup"><span data-stu-id="0b4f7-138">The resulting pattern is uncomfortable, so we recommend placing navigation controls in a centralized location that requires less back-and-forth.</span></span> <span data-ttu-id="0b4f7-139">根據其效果放置停留按鈕的位置，對於緩和是很重要的。</span><span class="sxs-lookup"><span data-stu-id="0b4f7-139">Placement of dwell buttons based on their effects becomes important for comfort.</span></span>
<span data-ttu-id="0b4f7-140">s</span><span class="sxs-lookup"><span data-stu-id="0b4f7-140">s</span></span>
<br>

---

## <a name="ux-guidelines-and-best-practices"></a><span data-ttu-id="0b4f7-141">UX 指導方針和最佳作法</span><span class="sxs-lookup"><span data-stu-id="0b4f7-141">UX Guidelines and best practices</span></span>

### <a name="target-sizes"></a><span data-ttu-id="0b4f7-142">目標大小</span><span class="sxs-lookup"><span data-stu-id="0b4f7-142">Target sizes</span></span>

<span data-ttu-id="0b4f7-143">為了方便存取，前端和停留目標必須夠大，才能輕鬆地查看，並且在指定的時間將一個固定在目標上。</span><span class="sxs-lookup"><span data-stu-id="0b4f7-143">To be easily accessible, head-gaze and dwell targets need to be large enough to look at comfortably, and hold one's head stable on the target for the prescribed time.</span></span> <span data-ttu-id="0b4f7-144">我們建議的最小目標大小為2度，以達成最舒適的體驗。</span><span class="sxs-lookup"><span data-stu-id="0b4f7-144">We recommend a minimum target size of 2 degrees to achieve the most comfortable experience.</span></span> 

### <a name="visual-feedback"></a><span data-ttu-id="0b4f7-145">視覺化回饋</span><span class="sxs-lookup"><span data-stu-id="0b4f7-145">Visual feedback</span></span>

<span data-ttu-id="0b4f7-146">使用放射狀填滿來表示佇留計時器時，從按鈕中心開始。</span><span class="sxs-lookup"><span data-stu-id="0b4f7-146">When using a radial fill to represent the dwell timer, start from the center of button.</span></span> <span data-ttu-id="0b4f7-147">相較於不同按鈕上的所有不同方向，一致的回應比較不容易混淆。</span><span class="sxs-lookup"><span data-stu-id="0b4f7-147">A consistent response is less confusing than all different directions on different buttons.</span></span> 

  * <span data-ttu-id="0b4f7-148">此規則可能會因為方向互動而中斷 (例如，nav/向下/向左/向右，依此類推) 。</span><span class="sxs-lookup"><span data-stu-id="0b4f7-148">This rule can be broken though for directional interactions (for example, nav up/down/left/right, and so on).</span></span> <span data-ttu-id="0b4f7-149">例如，Microsoft Dynamics 365 Guides 讓「下一頁/上一頁」成為左右填滿則屬例外狀況。</span><span class="sxs-lookup"><span data-stu-id="0b4f7-149">For example, Microsoft Dynamics 365 Guides makes an exception on NEXT/BACK being left right fills.</span></span>
  * <span data-ttu-id="0b4f7-150">請考慮在切換按鈕的情況下，從外部反轉星形填滿。</span><span class="sxs-lookup"><span data-stu-id="0b4f7-150">Consider inverting radial fill from outside, for scenarios like toggling off a button.</span></span> <span data-ttu-id="0b4f7-151">按壓按鈕的反向感覺是可維護的良好視覺模式。</span><span class="sxs-lookup"><span data-stu-id="0b4f7-151">The inverse feeling of pushing a button is a nice visual pattern to maintain.</span></span> 

### <a name="progressive-disclosure"></a><span data-ttu-id="0b4f7-152">漸進式揭露</span><span class="sxs-lookup"><span data-stu-id="0b4f7-152">Progressive disclosure</span></span>

<span data-ttu-id="0b4f7-153">漸進式揭露表示只有盡可能詳細顯示與互動的每個階段相關。</span><span class="sxs-lookup"><span data-stu-id="0b4f7-153">Progressive disclosure means only showing as much detail as is relevant at each stage of an interaction.</span></span> <span data-ttu-id="0b4f7-154">針對停留，這表示停留目標會顯示在反白顯示的 (例如，清單控制項) 。</span><span class="sxs-lookup"><span data-stu-id="0b4f7-154">For dwell, that means the dwell target is revealed on highlight (for example, in a list control).</span></span>

 ### <a name="oversized-targets"></a><span data-ttu-id="0b4f7-155">過大的目標</span><span class="sxs-lookup"><span data-stu-id="0b4f7-155">Oversized targets</span></span>

<span data-ttu-id="0b4f7-156">佇留區域可大於非使用中的圖示，使其更容易使用，例如 Microsoft Dynamics 365 Guides 中的 [上一頁] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="0b4f7-156">Dwell region can be larger than inactive icon to make it easier to use, like the Back button in Microsoft Dynamics 365 Guides.</span></span>

### <a name="prevent-flickering-with-delayed-feedback"></a><span data-ttu-id="0b4f7-157">使用延遲回饋防止閃爍</span><span class="sxs-lookup"><span data-stu-id="0b4f7-157">Prevent flickering with delayed feedback</span></span>

<span data-ttu-id="0b4f7-158">在開始視覺化回饋前使用短暫延遲，可避免有人經過佇留目標時發生閃爍。</span><span class="sxs-lookup"><span data-stu-id="0b4f7-158">Use a short delay before starting visual feedback to avoid flickering when someone passes over a dwell target.</span></span>
* <span data-ttu-id="0b4f7-159">針對經常與頻繁互動的按鈕，請將延遲縮短，讓應用程式感覺變得很慢。</span><span class="sxs-lookup"><span data-stu-id="0b4f7-159">For buttons interacted with frequently, keep the delay short so the application feels reactive.</span></span>
* <span data-ttu-id="0b4f7-160">對於不常進行互動的按鈕而言，較長的延遲可能適合避免介面感覺 twitchy。</span><span class="sxs-lookup"><span data-stu-id="0b4f7-160">For buttons that are interacted with infrequently, a longer delay can be appropriate to avoid the interface feeling twitchy.</span></span>

<br>

---

## <a name="ui-patterns"></a><span data-ttu-id="0b4f7-161">UI 模式</span><span class="sxs-lookup"><span data-stu-id="0b4f7-161">UI patterns</span></span>

### <a name="high-frequency-buttons"></a><span data-ttu-id="0b4f7-162">高頻率按鈕</span><span class="sxs-lookup"><span data-stu-id="0b4f7-162">High frequency buttons</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="0b4f7-163">高頻率按鈕是常用於整個應用程式的按鈕。</span><span class="sxs-lookup"><span data-stu-id="0b4f7-163">High frequency buttons are buttons that are used commonly throughout an application.</span></span> <span data-ttu-id="0b4f7-164">Microsoft Dynamics 365 Guides 中的下一頁和上一頁按鈕都是不錯的範例。</span><span class="sxs-lookup"><span data-stu-id="0b4f7-164">A good example of these are the next and back buttons in Microsoft Dynamics 365 Guides.</span></span><br>
        <br>
        <span data-ttu-id="0b4f7-165">**建議**</span><span class="sxs-lookup"><span data-stu-id="0b4f7-165">**Recommendations**</span></span><br>
  * <span data-ttu-id="0b4f7-166">高頻率按鈕應該很大，而且可以更輕鬆地使用列印頭</span><span class="sxs-lookup"><span data-stu-id="0b4f7-166">High frequency buttons should be large, easier to hit with head-gaze</span></span>
  * <span data-ttu-id="0b4f7-167">保持近乎眼睛的高度，以避免人體工學緊張。</span><span class="sxs-lookup"><span data-stu-id="0b4f7-167">Stay near eye height to avoid ergonomic straining.</span></span><br>
        <br>
<span data-ttu-id="0b4f7-168">*影像： Microsoft Dynamics 365 指南 [下一步] 按鈕*</span><span class="sxs-lookup"><span data-stu-id="0b4f7-168">*Image: Microsoft Dynamics 365 Guides next button*</span></span>
    :::column-end:::
        :::column:::
       ![Microsoft Dynamics 365 指南 [下一步] 按鈕](images/GuideNextButton.png)<br>
    :::column-end:::
:::row-end:::

<br>

---


### <a name="low-frequency-buttons"></a><span data-ttu-id="0b4f7-170">低頻率按鈕</span><span class="sxs-lookup"><span data-stu-id="0b4f7-170">Low frequency buttons</span></span>

<span data-ttu-id="0b4f7-171">低頻率按鈕是指不會在整個應用程式中定期進行互動的按鈕。</span><span class="sxs-lookup"><span data-stu-id="0b4f7-171">Low frequency buttons are buttons that aren't interacted with as regularly throughout the application.</span></span> <span data-ttu-id="0b4f7-172">可存取 [設定] 功能表的按鈕，或可清除所有工作的按鈕都是不錯的範例。</span><span class="sxs-lookup"><span data-stu-id="0b4f7-172">A good example might be a button to access the settings menu, or a button to clear all work.</span></span>

* <span data-ttu-id="0b4f7-173">嘗試讓這些按鈕不在常用的頭部注視路徑中，以免意外啟動。</span><span class="sxs-lookup"><span data-stu-id="0b4f7-173">Try to keep these buttons out of the way of frequent head-gaze paths to avoid accidental activation.</span></span> 

<br>

---

### <a name="confirmations"></a><span data-ttu-id="0b4f7-174">確認</span><span class="sxs-lookup"><span data-stu-id="0b4f7-174">Confirmations</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="0b4f7-175">當某個動作有顯著的影響時（例如收費、刪除工作或啟動長時間），確認要選取按鈕的人員會很有用。</span><span class="sxs-lookup"><span data-stu-id="0b4f7-175">When an action has significant impact, like charging money, deleting work, or starting a long process, it's useful to confirm that a person meant to select a button.</span></span><br>
        <br>
        <span data-ttu-id="0b4f7-176">**建議**</span><span class="sxs-lookup"><span data-stu-id="0b4f7-176">**Recommendations**</span></span><br>
  * <span data-ttu-id="0b4f7-177">在主要按鈕上顯示選取醒目提示。</span><span class="sxs-lookup"><span data-stu-id="0b4f7-177">Show selection highlight on main button.</span></span>
  * <span data-ttu-id="0b4f7-178">與選取醒目提示同時顯示佇留目標。</span><span class="sxs-lookup"><span data-stu-id="0b4f7-178">Reveal dwell target at same time as selection highlight.</span></span>
  * <span data-ttu-id="0b4f7-179">對於次要按鈕，顯示頭部注視的佇留目標。</span><span class="sxs-lookup"><span data-stu-id="0b4f7-179">For the secondary button, reveal the dwell target on head-gaze.</span></span><br>
        <br>
<span data-ttu-id="0b4f7-180">*影像： Microsoft Dynamics 365 指南確認對話方塊*</span><span class="sxs-lookup"><span data-stu-id="0b4f7-180">*Image: Microsoft Dynamics 365 Guides confirmation dialog*</span></span>
    :::column-end:::
        :::column:::
       ![Microsoft Dynamics 365 指南確認對話方塊](images/GuidesConfirmation.png)<br>
    :::column-end:::
:::row-end:::
        
<br>

---

### <a name="toggle-buttons"></a><span data-ttu-id="0b4f7-182">切換按鈕</span><span class="sxs-lookup"><span data-stu-id="0b4f7-182">Toggle buttons</span></span>

<span data-ttu-id="0b4f7-183">切換按鈕需要一些微妙的邏輯，才能正常運作。</span><span class="sxs-lookup"><span data-stu-id="0b4f7-183">Toggle buttons require some nuanced logic to work properly.</span></span> <span data-ttu-id="0b4f7-184">當使用者在切換按鈕上 dwells 並啟動它時，他們需要結束按鈕，然後返回以重新開機停留邏輯。</span><span class="sxs-lookup"><span data-stu-id="0b4f7-184">When a person dwells on a toggle button and activates it, they need to exit the button and then return to restart the dwell logic.</span></span> <span data-ttu-id="0b4f7-185">Togglable 按鈕必須具有明確的作用中與非作用中狀態。</span><span class="sxs-lookup"><span data-stu-id="0b4f7-185">It's important that togglable buttons have a clear active versus inactive state.</span></span> 

<br>

---

### <a name="list-views"></a><span data-ttu-id="0b4f7-186">清單檢視</span><span class="sxs-lookup"><span data-stu-id="0b4f7-186">List views</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="0b4f7-187">列出視圖會針對前端和停留輸入提供特定挑戰。</span><span class="sxs-lookup"><span data-stu-id="0b4f7-187">List views present a particular challenge for head-gaze and dwell input.</span></span> <span data-ttu-id="0b4f7-188">人們可以掃描內容，而不需要在停留目標周圍 tiptoe。</span><span class="sxs-lookup"><span data-stu-id="0b4f7-188">People can scan the content without feeling like that have to tiptoe around the dwell targets.</span></span><br>
        <br>
<span data-ttu-id="0b4f7-189">**建議**</span><span class="sxs-lookup"><span data-stu-id="0b4f7-189">**Recommendations**</span></span><br>
  * <span data-ttu-id="0b4f7-190">當標頭 gazed 但不會開始停留時，請將整個資料列反白顯示，除非前端看著特定的停留目標。</span><span class="sxs-lookup"><span data-stu-id="0b4f7-190">Have the entire row highlight when head-gazed but doesn’t begin dwell unless head-gaze is on the specific dwell target.</span></span>
  * <span data-ttu-id="0b4f7-191">當資料列反白顯示以在視覺雜訊上剪下時，才會顯示停留目標。</span><span class="sxs-lookup"><span data-stu-id="0b4f7-191">Only show the dwell target when the row is highlighted to cut down on visual noise.</span></span>
  * <span data-ttu-id="0b4f7-192">與停留目標的位置清楚且一致。</span><span class="sxs-lookup"><span data-stu-id="0b4f7-192">Be clear and consistent with the position of dwell targets.</span></span>
  * <span data-ttu-id="0b4f7-193">請勿同時顯示所有停留目標，以避免重複的 UI。</span><span class="sxs-lookup"><span data-stu-id="0b4f7-193">Don't show all dwell targets at once to avoid repetitive UI.</span></span>
  * <span data-ttu-id="0b4f7-194">盡可能重複使用相同的模式，以建立 UX 熟悉度。</span><span class="sxs-lookup"><span data-stu-id="0b4f7-194">Reuse the same pattern as often as possible to establish UX familiarity.</span></span><br>
        <br>
<span data-ttu-id="0b4f7-195">*影像： Microsoft Dynamics 365 指南清單*</span><span class="sxs-lookup"><span data-stu-id="0b4f7-195">*Image: Microsoft Dynamics 365 Guides list*</span></span>
    :::column-end:::
        :::column:::
       ![Microsoft Dynamics 365 指南清單](images/GuidesListView.png)<br>
    :::column-end:::
:::row-end:::

<br>

---
 
 ## <a name="see-also"></a><span data-ttu-id="0b4f7-197">請參閱</span><span class="sxs-lookup"><span data-stu-id="0b4f7-197">See also</span></span>

* [<span data-ttu-id="0b4f7-198">目光和行動</span><span class="sxs-lookup"><span data-stu-id="0b4f7-198">Gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="0b4f7-199">手 - 直接操作</span><span class="sxs-lookup"><span data-stu-id="0b4f7-199">Hands - Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="0b4f7-200">手 - 手勢</span><span class="sxs-lookup"><span data-stu-id="0b4f7-200">Hands - Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="0b4f7-201">手 - 指向和行動</span><span class="sxs-lookup"><span data-stu-id="0b4f7-201">Hands - Point and commit</span></span>](point-and-commit.md)
* [<span data-ttu-id="0b4f7-202">本能互動</span><span class="sxs-lookup"><span data-stu-id="0b4f7-202">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="0b4f7-203">語音輸入</span><span class="sxs-lookup"><span data-stu-id="0b4f7-203">Voice input</span></span>](voice-input.md)
