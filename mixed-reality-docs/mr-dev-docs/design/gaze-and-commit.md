---
title: 注視並認可
description: 深入瞭解「注視」和「認可」輸入模型，包括兩種類型的注視 (前端和眼睛) ，以及各種類型的認可。
author: sostel
ms.author: sostel
ms.date: 10/31/2019
ms.topic: article
keywords: 混合的現實、注視、注視目標、互動、設計、眼睛追蹤、head 追蹤、混合現實耳機、windows mixed reality 耳機、虛擬實境耳機、HoloLens、MRTK、混合現實工具組
ms.openlocfilehash: f9e79f8d600002f63e87316ea588741a21c0d68b
ms.sourcegitcommit: d340303cda71c31e6c3320231473d623c0930d33
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/01/2021
ms.locfileid: "97847935"
---
# <a name="gaze-and-commit"></a><span data-ttu-id="0c516-104">注視並認可</span><span class="sxs-lookup"><span data-stu-id="0c516-104">Gaze and commit</span></span>

<span data-ttu-id="0c516-105">「_注視」和「認可_」是一種基本的輸入模型，與使用滑鼠：_點 & 按一下_ 來與電腦互動的方式密切相關。</span><span class="sxs-lookup"><span data-stu-id="0c516-105">_Gaze and commit_ is a fundamental input model that is closely related to the way we're interacting with our computers using the mouse: _Point & click_.</span></span> <span data-ttu-id="0c516-106">在這個頁面中，我們會介紹兩種類型的注視輸入 (前端和眼睛) 以及不同類型的認可動作。</span><span class="sxs-lookup"><span data-stu-id="0c516-106">On this page, we introduce two types of gaze input (head- and eye-gaze) and different types of commit actions.</span></span> <span data-ttu-id="0c516-107">您可以使用間接操作將 _注視和 commit_ 視為最遠的輸入模型。</span><span class="sxs-lookup"><span data-stu-id="0c516-107">_Gaze and commit_ is considered a far input model with indirect manipulation.</span></span> <span data-ttu-id="0c516-108">它最適合用來與不觸及的全像內容互動。</span><span class="sxs-lookup"><span data-stu-id="0c516-108">It's best used for interacting with holographic content that is out of reach.</span></span>

<span data-ttu-id="0c516-109">混合現實耳機可以使用使用者的標頭位置和方向來決定其前端方向向量。</span><span class="sxs-lookup"><span data-stu-id="0c516-109">Mixed reality headsets can use the position and orientation of the user's head to determine their head direction vector.</span></span> <span data-ttu-id="0c516-110">把眼睛想像成直接從使用者的眼睛之間直接指向的鐳射。</span><span class="sxs-lookup"><span data-stu-id="0c516-110">Think of gaze as a laser pointing straight ahead from directly between the user's eyes.</span></span> <span data-ttu-id="0c516-111">這是相當粗略的使用者觀看位置概算。</span><span class="sxs-lookup"><span data-stu-id="0c516-111">This is a fairly coarse approximation of where the user is looking.</span></span> <span data-ttu-id="0c516-112">您的應用程式可以將此光線與虛擬或真實世界物件相交，並在該位置繪製游標，讓使用者知道其目標。</span><span class="sxs-lookup"><span data-stu-id="0c516-112">Your application can intersect this ray with virtual or real-world objects, and draw a cursor at that location to let the user know what they're targeting.</span></span>

<span data-ttu-id="0c516-113">除了頭部眼，某些混合的現實耳機（例如 HoloLens 2）包含產生眼睛向量的眼睛追蹤系統。</span><span class="sxs-lookup"><span data-stu-id="0c516-113">In addition to head gaze, some mixed reality headsets, such as HoloLens 2, include eye tracking systems that produce an eye-gaze vector.</span></span> <span data-ttu-id="0c516-114">這會對使用者觀看的位置提供精細的測量。</span><span class="sxs-lookup"><span data-stu-id="0c516-114">This provides a fine-grained measurement of where the user is looking.</span></span> <span data-ttu-id="0c516-115">在這兩種情況下，注視都代表使用者意圖的重要信號。</span><span class="sxs-lookup"><span data-stu-id="0c516-115">In both cases, the gaze represents an important signal for the user's intent.</span></span> <span data-ttu-id="0c516-116">系統可以解讀和預測使用者的預期動作，更好的使用者滿意度和效能也會改善。</span><span class="sxs-lookup"><span data-stu-id="0c516-116">The better the system can interpret and predict the user's intended actions, the more user satisfaction and performance improves.</span></span>

<span data-ttu-id="0c516-117">以下幾個範例可讓您以混合現實開發人員的身分來受益于 head 或眼睛：</span><span class="sxs-lookup"><span data-stu-id="0c516-117">Below are a few examples for how you as a mixed reality developer can benefit from head- or eye-gaze:</span></span>
* <span data-ttu-id="0c516-118">您的應用程式可以與場景中的全像眼睛相同，以判斷使用者的注意力 (更精確的眼睛) 。</span><span class="sxs-lookup"><span data-stu-id="0c516-118">Your app can intersect gaze with the holograms in your scene to determine where the user's attention is (more precise with eye-gaze).</span></span>
* <span data-ttu-id="0c516-119">您的應用程式可以根據使用者的注視來進行頻道手勢和控制器按，讓使用者可以順暢地選取、啟用、抓取、滾動或以其他方式與其全息的互動。</span><span class="sxs-lookup"><span data-stu-id="0c516-119">Your app can channel gestures and controller presses based on the user's gaze, which lets the user seamlessly select, activate, grab, scroll, or otherwise interact with their holograms.</span></span>
* <span data-ttu-id="0c516-120">您的應用程式可以讓使用者將表面光線與空間對應網格相交，以將影像放在真實世界的表面上。</span><span class="sxs-lookup"><span data-stu-id="0c516-120">Your app can let the user place holograms on real-world surfaces by intersecting their gaze ray with the spatial mapping mesh.</span></span>
* <span data-ttu-id="0c516-121">您的應用程式可以知道使用者何時不會查看重要物件的方向，這可能會導致您的應用程式提供視覺效果和音訊提示，以轉向該物件。</span><span class="sxs-lookup"><span data-stu-id="0c516-121">Your app can know when the user isn't looking in the direction of an important object, which can lead your app to give visual and audio cues to turn towards that object.</span></span>

<br>

## <a name="device-support"></a><span data-ttu-id="0c516-122">裝置支援</span><span class="sxs-lookup"><span data-stu-id="0c516-122">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="0c516-123"><strong>輸入模型</strong></span><span class="sxs-lookup"><span data-stu-id="0c516-123"><strong>Input model</strong></span></span></td>
        <td><span data-ttu-id="0c516-124"><a href="../hololens-hardware-details.md"><strong>HoloLens (第 1 代)</strong></a></span><span class="sxs-lookup"><span data-stu-id="0c516-124"><a href="../hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="0c516-125"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="0c516-125"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="0c516-126"><a href="../discover/immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></span><span class="sxs-lookup"><span data-stu-id="0c516-126"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="0c516-127">頭部注視並認可</span><span class="sxs-lookup"><span data-stu-id="0c516-127">Head-gaze and commit</span></span></td>
        <td><span data-ttu-id="0c516-128">✔️ 建議使用</span><span class="sxs-lookup"><span data-stu-id="0c516-128">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="0c516-129">✔️ 建議使用 (第三個選擇 - <a href="interaction-fundamentals.md">查看其他選項</a>)</span><span class="sxs-lookup"><span data-stu-id="0c516-129">✔️ Recommended (third choice - <a href="interaction-fundamentals.md">See the other options</a>)</span></span></td>
        <td><span data-ttu-id="0c516-130">➕ 替代選項</span><span class="sxs-lookup"><span data-stu-id="0c516-130">➕ Alternate option</span></span></td>
    </tr>
         <tr>
        <td><span data-ttu-id="0c516-131">眼部注視並認可</span><span class="sxs-lookup"><span data-stu-id="0c516-131">Eye-gaze and commit</span></span></td>
        <td><span data-ttu-id="0c516-132">❌ 無法使用</span><span class="sxs-lookup"><span data-stu-id="0c516-132">❌ Not available</span></span></td>
        <td><span data-ttu-id="0c516-133">✔️ 建議使用 (第三個選擇 - <a href="interaction-fundamentals.md">查看其他選項</a>)</span><span class="sxs-lookup"><span data-stu-id="0c516-133">✔️ Recommended (third choice - <a href="interaction-fundamentals.md">See the other options</a>)</span></span></td>
        <td><span data-ttu-id="0c516-134">❌ 無法使用</span><span class="sxs-lookup"><span data-stu-id="0c516-134">❌ Not available</span></span></td>
    </tr>
</table>


## <a name="gaze"></a><span data-ttu-id="0c516-135">注視</span><span class="sxs-lookup"><span data-stu-id="0c516-135">Gaze</span></span>

### <a name="eye--or-head-gaze"></a><span data-ttu-id="0c516-136">眼睛或頭部？</span><span class="sxs-lookup"><span data-stu-id="0c516-136">Eye- or head-gaze?</span></span>
<span data-ttu-id="0c516-137">無論您是否應該使用「眼睛和認可」或「前端和認可」輸入模型，都有幾個考慮。</span><span class="sxs-lookup"><span data-stu-id="0c516-137">There are several considerations when faced with the question whether you should use the "eye-gaze and commit" or "head-gaze and commit" input model.</span></span> <span data-ttu-id="0c516-138">如果您正在針對沉浸式耳機或 HoloLens (第一代) 進行開發，則選擇很簡單：標上和認可。</span><span class="sxs-lookup"><span data-stu-id="0c516-138">If you're developing for an immersive headset or for HoloLens (1st gen), then the choice is simple: Head-gaze and commit.</span></span> <span data-ttu-id="0c516-139">如果您是針對 HoloLens 2 進行開發，則選擇會變得更困難。</span><span class="sxs-lookup"><span data-stu-id="0c516-139">If you're developing for HoloLens 2, the choice becomes a little harder.</span></span> <span data-ttu-id="0c516-140">請務必瞭解每個都有的優點和挑戰。</span><span class="sxs-lookup"><span data-stu-id="0c516-140">It's important to understand the advantages and challenges that come with each of them.</span></span>
<span data-ttu-id="0c516-141">在下表中，我們編譯了一些很廣泛的專業人員和 con，以對比眼睛的目標。</span><span class="sxs-lookup"><span data-stu-id="0c516-141">We compiled some broad pro's and con's in the table below to contrast head- vs. eye-gaze targeting.</span></span> <span data-ttu-id="0c516-142">這並不是完整的，我們建議您在此處深入瞭解混合現實中的眼睛目標：</span><span class="sxs-lookup"><span data-stu-id="0c516-142">This is far from complete and we suggest learning more about eye-gaze targeting in mixed reality here:</span></span>
* <span data-ttu-id="0c516-143">[HoloLens 2 上的眼睛追蹤](eye-tracking.md)：在 HoloLens 2 上推出新的眼睛追蹤功能，包括一些開發人員指引。</span><span class="sxs-lookup"><span data-stu-id="0c516-143">[Eye tracking on HoloLens 2](eye-tracking.md): General introduction of our new eye tracking capability on HoloLens 2 including some developer guidance.</span></span> 
* <span data-ttu-id="0c516-144">[眼睛的互動](eye-gaze-interaction.md)：規劃使用眼睛追蹤作為輸入時的設計考慮和建議。</span><span class="sxs-lookup"><span data-stu-id="0c516-144">[Eye-gaze interaction](eye-gaze-interaction.md): Design considerations and recommendations when planning to use eye tracking as an input.</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
   <tr>
        <td><span data-ttu-id="0c516-145"><strong>眼睛的目標</strong></span><span class="sxs-lookup"><span data-stu-id="0c516-145"><strong>Eye-gaze targeting</strong></span></span></td>
        <td><span data-ttu-id="0c516-146"><strong>頭部注視定向</strong></span><span class="sxs-lookup"><span data-stu-id="0c516-146"><strong>Head-gaze targeting</strong></span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="0c516-147">快速！</span><span class="sxs-lookup"><span data-stu-id="0c516-147">Fast!</span></span></td>
        <td><span data-ttu-id="0c516-148">慢</span><span class="sxs-lookup"><span data-stu-id="0c516-148">Slower</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="0c516-149">低工作量 (幾乎不需要任何主體移動) </span><span class="sxs-lookup"><span data-stu-id="0c516-149">Low effort (barely any body movements necessary)</span></span></td>
        <td><span data-ttu-id="0c516-150">可以是 fatiguing 可能的不適感 (例如，頸部壓力) </span><span class="sxs-lookup"><span data-stu-id="0c516-150">Can be fatiguing - Possible discomfort (for example, neck strain)</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="0c516-151">不需要資料指標，但建議使用微妙的意見反應</span><span class="sxs-lookup"><span data-stu-id="0c516-151">Doesn't require a cursor, but subtle feedback is recommended</span></span></td>
        <td><span data-ttu-id="0c516-152">需要顯示資料指標</span><span class="sxs-lookup"><span data-stu-id="0c516-152">Requires to show a cursor</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="0c516-153">無平滑的移動–例如，不適合繪圖</span><span class="sxs-lookup"><span data-stu-id="0c516-153">No smooth eye movements – for example, not good for drawing</span></span></td>
        <td><span data-ttu-id="0c516-154">更受控制且明確</span><span class="sxs-lookup"><span data-stu-id="0c516-154">More controlled and explicit</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="0c516-155">很難進行小型目標 (例如，小按鈕或網頁連結) </span><span class="sxs-lookup"><span data-stu-id="0c516-155">Difficult for small targets (for example, tiny buttons or weblinks)</span></span></td>
        <td><span data-ttu-id="0c516-156">可靠！</span><span class="sxs-lookup"><span data-stu-id="0c516-156">Reliable!</span></span> <span data-ttu-id="0c516-157">絕佳的回復！</span><span class="sxs-lookup"><span data-stu-id="0c516-157">Great fallback!</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="0c516-158">...</span><span class="sxs-lookup"><span data-stu-id="0c516-158">...</span></span></td>
        <td><span data-ttu-id="0c516-159">...</span><span class="sxs-lookup"><span data-stu-id="0c516-159">...</span></span></td>
    </tr>
</table>

<span data-ttu-id="0c516-160">無論您是針對您的注視和認可輸入模型使用頭部眼或眼睛，都有不同的設計條件約束集合。</span><span class="sxs-lookup"><span data-stu-id="0c516-160">Whether you use head-gaze or eye-gaze for your gaze-and-commit input model, each comes with different sets of design constraints.</span></span> <span data-ttu-id="0c516-161">這些都是在眼睛和 [認可](gaze-and-commit-eyes.md) 和 [認可文章中](gaze-and-commit-head.md) 分開討論。</span><span class="sxs-lookup"><span data-stu-id="0c516-161">These are covered separately in the [eye-gaze and commit](gaze-and-commit-eyes.md) and [head-gaze and commit](gaze-and-commit-head.md) articles.</span></span>

<br>

---

### <a name="cursor"></a><span data-ttu-id="0c516-162">資料指標</span><span class="sxs-lookup"><span data-stu-id="0c516-162">Cursor</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="0c516-163">針對 head，大部分的應用程式應該使用資料 [指標](cursors.md) 或其他聽覺/視覺指示，讓使用者在他們即將與其互動的方面具有信賴度。</span><span class="sxs-lookup"><span data-stu-id="0c516-163">For head gaze, most apps should use a [cursor](cursors.md) or other auditory/visual indication to give the user confidence in what they're about to interact with.</span></span> <span data-ttu-id="0c516-164">您通常會將這個資料指標放在世界中，其中的前端光線最先與物件（可能是全息圖或真實世界表面）相交。</span><span class="sxs-lookup"><span data-stu-id="0c516-164">You typically position this cursor in the world where their head gaze ray first intersects an object, which may be a hologram or a real-world surface.</span></span><br>
        <br>
        <span data-ttu-id="0c516-165">針對眼睛，我們通常不建議您 *不要* 顯示資料指標，因為這可能會對使用者造成干擾和討厭。</span><span class="sxs-lookup"><span data-stu-id="0c516-165">For eye gaze, we generally recommend *not* to show a cursor, as this can quickly become distracting and annoying for the user.</span></span> <span data-ttu-id="0c516-166">相反地，請特別強調視覺效果目標，或使用不清楚的眼睛游標，以提供使用者即將互動的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="0c516-166">Instead subtly highlight visual targets or use a faint eye cursor to provide confidence about what the user is about to interact with.</span></span> <span data-ttu-id="0c516-167">如需詳細資訊，請參閱 HoloLens 2 上 [的眼睛輸入的設計指引](eye-tracking.md) 。</span><span class="sxs-lookup"><span data-stu-id="0c516-167">For more information, please check out our [design guidance for eye-based input](eye-tracking.md) on HoloLens 2.</span></span>
    :::column-end:::
        :::column:::
       <span data-ttu-id="0c516-168">![顯示注視的視覺效果游標範例](images/cursor.jpg)</span><span class="sxs-lookup"><span data-stu-id="0c516-168">![An example visual cursor to show gaze](images/cursor.jpg)</span></span><br>
       <span data-ttu-id="0c516-169">*影像：顯示注視的視覺效果游標範例*</span><span class="sxs-lookup"><span data-stu-id="0c516-169">*Image: An example visual cursor to show gaze*</span></span>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="commit"></a><span data-ttu-id="0c516-170">Commit</span><span class="sxs-lookup"><span data-stu-id="0c516-170">Commit</span></span>
<span data-ttu-id="0c516-171">談到不同的 _方式來看_ 看某個目標之後，讓我們再談談一下看看 _和認可_ 的 _認可_ 部分。</span><span class="sxs-lookup"><span data-stu-id="0c516-171">After talking about different ways to _gaze_ at a target, let's talk a bit more about the _commit_ part in _gaze and commit_.</span></span>
<span data-ttu-id="0c516-172">以物件或 UI 元素為目標之後，使用者可以使用次要輸入進行互動或按一下。</span><span class="sxs-lookup"><span data-stu-id="0c516-172">After targeting an object or UI element, the user can interact or click on it using a secondary input.</span></span> <span data-ttu-id="0c516-173">這就是所謂的輸入模型認可步驟。</span><span class="sxs-lookup"><span data-stu-id="0c516-173">This is known as the commit step of the input model.</span></span> 

<span data-ttu-id="0c516-174">支援的認可方法如下：</span><span class="sxs-lookup"><span data-stu-id="0c516-174">The following commit methods are supported:</span></span>
- <span data-ttu-id="0c516-175">點擊手勢 (也就是提高您手上的手，並將您的食指和 thumb 合在一起) </span><span class="sxs-lookup"><span data-stu-id="0c516-175">Air tap hand gesture (that is, raise your hand in front of you and bring together your index finger and thumb)</span></span>
- <span data-ttu-id="0c516-176">說「 _select_ 」或其中一個目標語音命令</span><span class="sxs-lookup"><span data-stu-id="0c516-176">Say _"select"_ or one of the targeted voice commands</span></span>
- <span data-ttu-id="0c516-177">在[HoloLens Clicker](https://docs.microsoft.com/hololens/hololens1-clicker)上按單一按鈕</span><span class="sxs-lookup"><span data-stu-id="0c516-177">Press a single button on a [HoloLens Clicker](https://docs.microsoft.com/hololens/hololens1-clicker)</span></span>
- <span data-ttu-id="0c516-178">按下 Xbox 遊戲台上的 [A] 按鈕</span><span class="sxs-lookup"><span data-stu-id="0c516-178">Press the 'A' button on an Xbox gamepad</span></span>
- <span data-ttu-id="0c516-179">按下 Xbox 適應性控制器上的 [A] 按鈕</span><span class="sxs-lookup"><span data-stu-id="0c516-179">Press the 'A' button on an Xbox adaptive controller</span></span>

### <a name="gaze-and-air-tap-gesture"></a><span data-ttu-id="0c516-180">注視和點擊手勢</span><span class="sxs-lookup"><span data-stu-id="0c516-180">Gaze and air tap gesture</span></span>
<span data-ttu-id="0c516-181">空中點選是手部直立的點選手勢。</span><span class="sxs-lookup"><span data-stu-id="0c516-181">Air tap is a tapping gesture with the hand held upright.</span></span> <span data-ttu-id="0c516-182">若要使用 [點一下]，請將您的索引指向 [就緒] 位置，然後使用您的 thumb 來縮小，然後將您的索引手指重設為 [發行]。</span><span class="sxs-lookup"><span data-stu-id="0c516-182">To use an air tap, raise your index finger to the ready position, then pinch with your thumb, and raise your index finger back up to release.</span></span> <span data-ttu-id="0c516-183">在 HoloLens (第1代) 上，按一下是最常見的次要輸入。</span><span class="sxs-lookup"><span data-stu-id="0c516-183">On HoloLens (1st gen), air tap is the most common secondary input.</span></span>


:::row:::
    :::column:::
       <span data-ttu-id="0c516-184">![觸達就緒位置](images/readyandpress-ready.jpg)</span><span class="sxs-lookup"><span data-stu-id="0c516-184">![Finger in the ready position](images/readyandpress-ready.jpg)</span></span><br>
       <span data-ttu-id="0c516-185">**觸達就緒位置**</span><span class="sxs-lookup"><span data-stu-id="0c516-185">**Finger in the ready position**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="0c516-186">![按下手指以點擊或按一下](images/readyandpress-press.jpg)</span><span class="sxs-lookup"><span data-stu-id="0c516-186">![Press finger down to tap or click](images/readyandpress-press.jpg)</span></span><br>
        <span data-ttu-id="0c516-187">**按下手指以點擊或按一下**</span><span class="sxs-lookup"><span data-stu-id="0c516-187">**Press finger down to tap or click**</span></span><br>
    :::column-end:::
:::row-end:::


<span data-ttu-id="0c516-188">HoloLens 2 也可以使用 [點一下]。</span><span class="sxs-lookup"><span data-stu-id="0c516-188">Air tap is also available on HoloLens 2.</span></span> <span data-ttu-id="0c516-189">它已從原始版本中放寬。</span><span class="sxs-lookup"><span data-stu-id="0c516-189">It has been relaxed from the original version.</span></span> <span data-ttu-id="0c516-190">幾乎所有類型的 pinches 現在都可支援，只要手邊的手是直立的，且仍維持。</span><span class="sxs-lookup"><span data-stu-id="0c516-190">Nearly all types of pinches are now supported as long as the hand is upright and holding still.</span></span> <span data-ttu-id="0c516-191">這讓使用者更容易學習和使用手勢。</span><span class="sxs-lookup"><span data-stu-id="0c516-191">This makes it much easier for users to learn and use the gesture.</span></span> <span data-ttu-id="0c516-192">這個新的空中會透過相同的 API 來取代舊的，讓現有的應用程式在重新編譯以進行 HoloLens 2 之後，會自動有新的行為。</span><span class="sxs-lookup"><span data-stu-id="0c516-192">This new air tap replaces the old one through the same API, so existing applications will have the new behavior automatically after recompiling for HoloLens 2.</span></span>

<br>

---

### <a name="gaze-and-select-voice-command"></a><span data-ttu-id="0c516-193">注視和「選取」聲音命令</span><span class="sxs-lookup"><span data-stu-id="0c516-193">Gaze and "Select" voice command</span></span>
<span data-ttu-id="0c516-194">語音命令是混合現實中的其中一個主要互動方法。</span><span class="sxs-lookup"><span data-stu-id="0c516-194">Voice commanding is one of the primary interaction methods in mixed reality.</span></span> <span data-ttu-id="0c516-195">它提供強大的無人參與機制來控制系統。</span><span class="sxs-lookup"><span data-stu-id="0c516-195">It provides a powerful hands-free mechanism to control the system.</span></span> <span data-ttu-id="0c516-196">語音互動模型有不同的類型：</span><span class="sxs-lookup"><span data-stu-id="0c516-196">There are different types of voice interaction models:</span></span>

- <span data-ttu-id="0c516-197">使用 click actuation 或 commit 作為次要輸入的泛型 "Select" 命令。</span><span class="sxs-lookup"><span data-stu-id="0c516-197">The generic "Select" command that uses a click actuation or commit as a secondary input.</span></span>
- <span data-ttu-id="0c516-198">物件命令 (例如，「關閉」或「變得更大」 ) 執行並認可至動作做為次要輸入。</span><span class="sxs-lookup"><span data-stu-id="0c516-198">Object commands (for example, "Close" or "Make it bigger") perform and commit to an action as a secondary input.</span></span>
- <span data-ttu-id="0c516-199">全域命令 (例如「移至開始」 ) 不需要目標。</span><span class="sxs-lookup"><span data-stu-id="0c516-199">Global commands (for example, "Go to start") don't require a target.</span></span>
- <span data-ttu-id="0c516-200">對話使用者介面或 Cortana 之類的實體都具有 AI 自然語言功能。</span><span class="sxs-lookup"><span data-stu-id="0c516-200">Conversation user interfaces or entities like Cortana have an AI natural language capability.</span></span>
- <span data-ttu-id="0c516-201">自訂語音命令</span><span class="sxs-lookup"><span data-stu-id="0c516-201">Custom voice commands</span></span>

<span data-ttu-id="0c516-202">若要深入瞭解詳細資料和可用語音命令的完整清單，以及如何使用這些命令，請參閱我們的 [語音命令](../out-of-scope/voice-design.md) 指引。</span><span class="sxs-lookup"><span data-stu-id="0c516-202">To find out more about details and a comprehensive list of available voice commands and how to use them, check out our [voice commanding](../out-of-scope/voice-design.md) guidance.</span></span>

<br>

---


### <a name="gaze-and-hololens-clicker"></a><span data-ttu-id="0c516-203">注視和 HoloLens Clicker</span><span class="sxs-lookup"><span data-stu-id="0c516-203">Gaze and HoloLens Clicker</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="0c516-204">HoloLens Clicker 是特別為 HoloLens 建立的第一個週邊設備。</span><span class="sxs-lookup"><span data-stu-id="0c516-204">The HoloLens Clicker is the first peripheral device built specifically for HoloLens.</span></span> <span data-ttu-id="0c516-205">它隨附于 HoloLens (第一代) 開發版。</span><span class="sxs-lookup"><span data-stu-id="0c516-205">It's included with HoloLens (1st gen) Development Edition.</span></span> <span data-ttu-id="0c516-206">HoloLens Clicker 可讓使用者按下最少量的動作，並認可為次要輸入。</span><span class="sxs-lookup"><span data-stu-id="0c516-206">The HoloLens Clicker lets a user click with minimal hand motion, and commit as a secondary input.</span></span> <span data-ttu-id="0c516-207">HoloLens Clicker 會連接到 HoloLens (第1代) 或使用藍牙低能源 (BTLE) HoloLens 2。</span><span class="sxs-lookup"><span data-stu-id="0c516-207">The HoloLens Clicker connects to HoloLens (1st gen) or HoloLens 2 using Bluetooth Low Energy (BTLE).</span></span><br>
        <br>
        [<span data-ttu-id="0c516-208">有關將裝置配對的詳細資訊和指示</span><span class="sxs-lookup"><span data-stu-id="0c516-208">More information and instructions to pair the device</span></span>](../discover/hardware-accessories.md#pairing-bluetooth-accessories)<br>
        <br>
        <span data-ttu-id="0c516-209">*映射： HoloLens Clicker*</span><span class="sxs-lookup"><span data-stu-id="0c516-209">*Image: HoloLens Clicker*</span></span>
    :::column-end:::
        :::column:::
       ![HoloLens Clicker](images/hololens-clicker-500px.jpg)<br>
    :::column-end:::
:::row-end:::

<br>

---


### <a name="gaze-and-xbox-wireless-controller"></a><span data-ttu-id="0c516-211">注視和 Xbox 無線控制器</span><span class="sxs-lookup"><span data-stu-id="0c516-211">Gaze and Xbox Wireless Controller</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="0c516-212">Xbox 無線控制器會使用 [A] 按鈕，以次要輸入的形式執行 click actuation。</span><span class="sxs-lookup"><span data-stu-id="0c516-212">The Xbox Wireless Controller performs a click actuation as a secondary input by using the 'A' button.</span></span> <span data-ttu-id="0c516-213">裝置會對應至一組預設的動作，以協助流覽和控制系統。</span><span class="sxs-lookup"><span data-stu-id="0c516-213">The device is mapped to a default set of actions that help navigate and control the system.</span></span> <span data-ttu-id="0c516-214">如果您想要自訂控制器，請使用 Xbox 配件應用程式來設定 Xbox 無線控制器。</span><span class="sxs-lookup"><span data-stu-id="0c516-214">If you want to customize the controller, use the Xbox Accessories application to configure your Xbox Wireless Controller.</span></span><br>
        <br>
        [<span data-ttu-id="0c516-215">如何將 Xbox 控制器與您的電腦配對</span><span class="sxs-lookup"><span data-stu-id="0c516-215">How to pair an Xbox controller with your PC</span></span>](../discover/hardware-accessories.md#pairing-bluetooth-accessories)<br>
        <br>
        <span data-ttu-id="0c516-216">*影像： Xbox 無線控制器*</span><span class="sxs-lookup"><span data-stu-id="0c516-216">*Image: Xbox Wireless Controller*</span></span>
    :::column-end:::
        :::column:::
       ![Xbox 無線控制器](images/xboxcontroller.jpg)<br>
    :::column-end:::
:::row-end:::



<br>

---


### <a name="gaze-and-xbox-adaptive-controller"></a><span data-ttu-id="0c516-218">注視和 Xbox 調適型控制器</span><span class="sxs-lookup"><span data-stu-id="0c516-218">Gaze and Xbox Adaptive Controller</span></span>
<span data-ttu-id="0c516-219">Xbox 調適型控制器是專為滿足行動裝置的需求而設計，可協助讓混合現實更容易存取的裝置具有統一的中樞。</span><span class="sxs-lookup"><span data-stu-id="0c516-219">Designed primarily to meet the needs of gamers with limited mobility, the Xbox Adaptive Controller is a unified hub for devices that helps make mixed reality more accessible.</span></span>

<span data-ttu-id="0c516-220">Xbox 適應性控制器會使用 [A] 按鈕，以次要輸入的形式執行 click actuation。</span><span class="sxs-lookup"><span data-stu-id="0c516-220">The Xbox Adaptive Controller performs a click actuation as a secondary input by using the 'A' button.</span></span> <span data-ttu-id="0c516-221">裝置會對應至一組預設的動作，以協助流覽和控制系統。</span><span class="sxs-lookup"><span data-stu-id="0c516-221">The device is mapped to a default set of actions that help navigate and control the system.</span></span> <span data-ttu-id="0c516-222">如果您想要自訂控制器，請使用 Xbox 配件應用程式來設定 Xbox 調適型控制器。</span><span class="sxs-lookup"><span data-stu-id="0c516-222">If you want to customize the controller, use the Xbox Accessories application to configure your Xbox Adaptive Controller.</span></span>

<span data-ttu-id="0c516-223">![Xbox Adaptive Controller](images/xbox-adaptive-controller-devices.jpg)</span><span class="sxs-lookup"><span data-stu-id="0c516-223">![Xbox Adaptive Controller](images/xbox-adaptive-controller-devices.jpg)</span></span><br>
<span data-ttu-id="0c516-224">*Xbox Adaptive Controller*</span><span class="sxs-lookup"><span data-stu-id="0c516-224">*Xbox Adaptive Controller*</span></span>

<span data-ttu-id="0c516-225">連接外部裝置（例如交換器、按鈕、掛接和操作杆）來建立獨特的自訂控制器體驗。</span><span class="sxs-lookup"><span data-stu-id="0c516-225">Connect external devices such as switches, buttons, mounts, and joysticks to create a custom controller experience that is uniquely yours.</span></span> <span data-ttu-id="0c516-226">按鈕、操縱杆和觸發程式輸入都是由透過 3.5-mm 插座和 USB 埠連接的輔助裝置所控制。</span><span class="sxs-lookup"><span data-stu-id="0c516-226">Button, thumbstick, and trigger inputs are controlled with assistive devices connected through 3.5-mm jacks and USB ports.</span></span>

<span data-ttu-id="0c516-227">![Xbox Adaptive Controller 連接埠](images/xbox-adaptive-controller-ports.jpg)</span><span class="sxs-lookup"><span data-stu-id="0c516-227">![Xbox Adaptive Controller ports](images/xbox-adaptive-controller-ports.jpg)</span></span><br>
<span data-ttu-id="0c516-228">*Xbox Adaptive Controller 連接埠*</span><span class="sxs-lookup"><span data-stu-id="0c516-228">*Xbox Adaptive Controller ports*</span></span>

[<span data-ttu-id="0c516-229">裝置配對指示</span><span class="sxs-lookup"><span data-stu-id="0c516-229">Instructions to pair the device</span></span>](../discover/hardware-accessories.md#pairing-bluetooth-accessories)

<span data-ttu-id="0c516-230"><a href=https://www.xbox.com/xbox-one/accessories/controllers/xbox-adaptive-controller>在 Xbox 網站上可取得更多資訊</a></span><span class="sxs-lookup"><span data-stu-id="0c516-230"><a href=https://www.xbox.com/xbox-one/accessories/controllers/xbox-adaptive-controller>More info available on the Xbox site</a></span></span>

<br>

---

## <a name="composite-gestures"></a><span data-ttu-id="0c516-231">複合手勢</span><span class="sxs-lookup"><span data-stu-id="0c516-231">Composite gestures</span></span>

### <a name="air-tap"></a><span data-ttu-id="0c516-232">空中點選</span><span class="sxs-lookup"><span data-stu-id="0c516-232">Air tap</span></span>
<span data-ttu-id="0c516-233">點擊手勢 (，下的其他手勢) 只會回應特定的點。</span><span class="sxs-lookup"><span data-stu-id="0c516-233">The air tap gesture (and the other gestures below) reacts only to a specific tap.</span></span> <span data-ttu-id="0c516-234">若要偵測其他點擊（例如功能表或理解），您的應用程式必須直接使用上述兩個主要元件手勢區段中所述的較低層級互動。</span><span class="sxs-lookup"><span data-stu-id="0c516-234">To detect other taps, such as Menu or Grasp, your application must directly use the lower-level interactions described in the two key component gestures section above.</span></span>

### <a name="tap-and-hold"></a><span data-ttu-id="0c516-235">點選並按住</span><span class="sxs-lookup"><span data-stu-id="0c516-235">Tap and hold</span></span>
<span data-ttu-id="0c516-236">按住只是維持空中點選的手指朝下位置。</span><span class="sxs-lookup"><span data-stu-id="0c516-236">Hold is simply maintaining the downward finger position of the air tap.</span></span> <span data-ttu-id="0c516-237">結合了「點擊和拖曳」互動與 arm 移動（例如挑選物件），而不是啟用或 mousedown 次要互動（例如顯示操作功能表）。</span><span class="sxs-lookup"><span data-stu-id="0c516-237">The combination of air tap and hold allows for various more complex "click and drag" interactions when combined with arm movement such as picking up an object instead of activating it or mousedown secondary interactions such as showing a context menu.</span></span>
<span data-ttu-id="0c516-238">不過，在設計此筆勢時應謹慎使用，因為使用者可能很容易在任何延長的手勢中放寬其手做法。</span><span class="sxs-lookup"><span data-stu-id="0c516-238">Caution should be used when designing for this gesture however, as users can be prone to relaxing their hand postures during any extended gesture.</span></span>

### <a name="manipulation"></a><span data-ttu-id="0c516-239">操作</span><span class="sxs-lookup"><span data-stu-id="0c516-239">Manipulation</span></span>
<span data-ttu-id="0c516-240">當您想1:1 要讓全像全像移動、調整大小或旋轉全像移動、調整大小或旋轉影像時，可以使用操作手勢來移動、調整大小或旋轉。</span><span class="sxs-lookup"><span data-stu-id="0c516-240">Manipulation gestures can be used to move, resize, or rotate a hologram when you want the hologram to react 1:1 to the user's hand movements.</span></span> <span data-ttu-id="0c516-241">這類 1:1 移動的用途之一是要讓使用者可以實際繪圖。</span><span class="sxs-lookup"><span data-stu-id="0c516-241">One use for such 1:1 movements is to let the user draw or paint in the world.</span></span>
<span data-ttu-id="0c516-242">操作手勢的初始定向應經由注視或指向來完成。</span><span class="sxs-lookup"><span data-stu-id="0c516-242">The initial targeting for a manipulation gesture should be done by gaze or pointing.</span></span> <span data-ttu-id="0c516-243">當點一下和按住開始之後，任何物件操作都會由手動移動處理，如此可讓使用者在操作時進行查詢。</span><span class="sxs-lookup"><span data-stu-id="0c516-243">Once the tap and hold starts, any object manipulation is handled by hand movements, which frees the user to look around while they manipulate.</span></span>

### <a name="navigation"></a><span data-ttu-id="0c516-244">瀏覽</span><span class="sxs-lookup"><span data-stu-id="0c516-244">Navigation</span></span>
<span data-ttu-id="0c516-245">瀏覽手勢的運作方式如同虛擬搖桿，可用來瀏覽 UI 小工具，例如放射狀功能表。</span><span class="sxs-lookup"><span data-stu-id="0c516-245">Navigation gestures operate like a virtual joystick, and can be used to navigate UI widgets, such as radial menus.</span></span> <span data-ttu-id="0c516-246">您可點選並按住來啟動手勢，然後在標準化 3D Cube (在初次按壓時置中) 中移動您的手。</span><span class="sxs-lookup"><span data-stu-id="0c516-246">You tap and hold to start the gesture and then move your hand within a normalized 3D cube, centered around the initial press.</span></span> <span data-ttu-id="0c516-247">您可以將來自 X、Y 或 Z 軸的手移至從-1 到1的值，並將0視為起始點。</span><span class="sxs-lookup"><span data-stu-id="0c516-247">You can move your hand along the X, Y, or Z axis from a value of -1 to 1, with 0 being the starting point.</span></span>
<span data-ttu-id="0c516-248">瀏覽可用來建置以速度為基礎的連續捲動或縮放手勢，類似於藉由按一下滑鼠中間按鈕，然後上下移動滑鼠來捲動 2D UI。</span><span class="sxs-lookup"><span data-stu-id="0c516-248">Navigation can be used to build velocity-based continuous scrolling or zooming gestures, similar to scrolling a 2D UI by clicking the middle mouse button and then moving the mouse up and down.</span></span>

<span data-ttu-id="0c516-249">使用 rails 的導覽指的是在特定軸中辨識移動的能力，直到到達該軸上的特定臨界值為止。</span><span class="sxs-lookup"><span data-stu-id="0c516-249">Navigation with rails refers to the ability of recognizing movements in certain axis until a certain threshold is reached on that axis.</span></span> <span data-ttu-id="0c516-250">當開發人員在應用程式中啟用多個軸的移動時（例如，如果應用程式設定為辨識跨 X、Y 軸的導覽手勢，但同時指定 X 軸與 rails），這項功能就很有用。</span><span class="sxs-lookup"><span data-stu-id="0c516-250">This is only useful when movement in more than one axis is enabled in an application by the developer, such as if an application is configured to recognize navigation gestures across X, Y axis but also specified X axis with rails.</span></span> <span data-ttu-id="0c516-251">在這種情況下，系統會在 X 軸上辨識手間的移動，只要它們留在 X 軸的虛數滑軌 (指南) ，如果在 Y 軸上也會發生手移動。</span><span class="sxs-lookup"><span data-stu-id="0c516-251">In this case, the system will recognize hand movements across X axis as long as they remain within an imaginary rails (guide) on the X axis, if hand movement also occurs on the Y axis.</span></span>

<span data-ttu-id="0c516-252">在 2D 應用程式內，使用者可以使用垂直瀏覽手勢在應用程式內捲動、縮放或拖曳。</span><span class="sxs-lookup"><span data-stu-id="0c516-252">Within 2D apps, users can use vertical navigation gestures to scroll, zoom, or drag inside the app.</span></span> <span data-ttu-id="0c516-253">這會在應用程式中插入虛擬手指觸控，以模擬同類型的觸控手勢。</span><span class="sxs-lookup"><span data-stu-id="0c516-253">This injects virtual finger touches to the app to simulate touch gestures of the same type.</span></span> <span data-ttu-id="0c516-254">使用者可以在應用程式上方的工具列上切換，藉由選取按鈕或說「<滾動/拖曳/縮放> 工具」，來選取要進行的動作。</span><span class="sxs-lookup"><span data-stu-id="0c516-254">Users can select which of these actions take place by toggling between the tools on the bar above the application, either by selecting the button or saying '<Scroll/Drag/Zoom> Tool'.</span></span>

[<span data-ttu-id="0c516-255">複合手勢的詳細資訊</span><span class="sxs-lookup"><span data-stu-id="0c516-255">More info on composite gestures</span></span>](gaze-and-commit.md#composite-gestures)

## <a name="gesture-recognizers"></a><span data-ttu-id="0c516-256">手勢辨識器</span><span class="sxs-lookup"><span data-stu-id="0c516-256">Gesture recognizers</span></span>

<span data-ttu-id="0c516-257">使用手勢辨識的其中一個優點是，您只能針對目前目標的全像全像影像所能接受的手勢設定手勢辨識器。</span><span class="sxs-lookup"><span data-stu-id="0c516-257">One benefit of using gesture recognition is that you can configure a gesture recognizer only for the gestures the currently targeted hologram can accept.</span></span> <span data-ttu-id="0c516-258">平臺只會視需要去除混淆，以區別這些特定支援的手勢。</span><span class="sxs-lookup"><span data-stu-id="0c516-258">The platform only does disambiguation as necessary to distinguish those particular supported gestures.</span></span> <span data-ttu-id="0c516-259">如此一來，只支援「敲擊」的全像是在按下和放開之間有任何時間長度，而同時支援點一下和按住的全像投影可以在按住時間閾值之後升階。</span><span class="sxs-lookup"><span data-stu-id="0c516-259">In this way, a hologram that just supports air tap can accept any length of time between press and release, while a hologram that supports both tap and hold can promote the tap to a hold after the hold time threshold.</span></span>

## <a name="hand-recognition"></a><span data-ttu-id="0c516-260">手部辨識</span><span class="sxs-lookup"><span data-stu-id="0c516-260">Hand recognition</span></span>
<span data-ttu-id="0c516-261">HoloLens 可藉由追蹤裝置可見的任一手或雙手位置來辨識手勢。</span><span class="sxs-lookup"><span data-stu-id="0c516-261">HoloLens recognizes hand gestures by tracking the position of either or both hands that are visible to the device.</span></span> <span data-ttu-id="0c516-262">當手部處於就緒狀態 (手背朝向您且食指朝上) 或按下狀態 (手背朝向您且食指朝下) 時，HoloLens 就會看見手部。</span><span class="sxs-lookup"><span data-stu-id="0c516-262">HoloLens sees hands when they are in either the ready state (back of the hand facing you with index finger up) or the pressed state (back of the hand facing you with the index finger down).</span></span> <span data-ttu-id="0c516-263">當手中有其他人時，HoloLens 會忽略它們。</span><span class="sxs-lookup"><span data-stu-id="0c516-263">When hands are in other poses, HoloLens ignores them.</span></span>
<span data-ttu-id="0c516-264">針對 HoloLens 偵測到的每個手，您可以存取其位置，而不需要方向和按下的狀態。</span><span class="sxs-lookup"><span data-stu-id="0c516-264">For each hand that HoloLens detects, you can access its position without orientation and its pressed state.</span></span> <span data-ttu-id="0c516-265">當手部接近手勢框架邊緣時，您也會取得方向向量，而您可對使用者顯示該向量，讓他們知道如何移動其手部以回到 HoloLens 可看見手部的位置。</span><span class="sxs-lookup"><span data-stu-id="0c516-265">As the hand nears the edge of the gesture frame, you're also provided with a direction vector, which you can show to the user so they know how to move their hand to get it back where HoloLens can see it.</span></span>

## <a name="gesture-frame"></a><span data-ttu-id="0c516-266">手勢框架</span><span class="sxs-lookup"><span data-stu-id="0c516-266">Gesture frame</span></span>
<span data-ttu-id="0c516-267">針對 HoloLens 上的手勢，手必須位於手勢框架內、手勢檢測攝影機可適當地查看的範圍、從鼻子到 waist，以及肩膀之間。</span><span class="sxs-lookup"><span data-stu-id="0c516-267">For gestures on HoloLens, the hand must be within a gesture frame, in a range that the gesture-sensing cameras can see appropriately,  from nose to waist and between the shoulders.</span></span> <span data-ttu-id="0c516-268">使用者必須在此辨識區域上進行訓練，以獲得動作的成功，並讓他們自己的舒適。</span><span class="sxs-lookup"><span data-stu-id="0c516-268">Users need to be trained on this area of recognition both for success of action and for their own comfort.</span></span> <span data-ttu-id="0c516-269">許多使用者一開始會假設手勢框架必須在其觀看的情況下，透過 HoloLens，並讓其 arm uncomfortably 互動。</span><span class="sxs-lookup"><span data-stu-id="0c516-269">Many users will initially assume that the gesture frame must be within their view through HoloLens, and hold up their arms uncomfortably to interact.</span></span> <span data-ttu-id="0c516-270">使用 HoloLens Clicker 時，不一定要將手放在手勢框架內。</span><span class="sxs-lookup"><span data-stu-id="0c516-270">When using the HoloLens Clicker, it's not necessary for hands to be within the gesture frame.</span></span>

<span data-ttu-id="0c516-271">尤其是針對連續手勢，當移動全像投影片的物件時，使用者可能會有一些風險將手移至手勢框架之外，而不會發生預期的結果。</span><span class="sxs-lookup"><span data-stu-id="0c516-271">For continuous gestures in particular, there's some risk of users moving their hands outside of the gesture frame while in mid-gesture when moving a holographic object, for example, and losing their intended outcome.</span></span>

<span data-ttu-id="0c516-272">您應該考量下列三個事項：</span><span class="sxs-lookup"><span data-stu-id="0c516-272">There are three things that you should consider:</span></span>

- <span data-ttu-id="0c516-273">手勢框架存在和大約界限的使用者教育。</span><span class="sxs-lookup"><span data-stu-id="0c516-273">User education on the gesture frame's existence and approximate boundaries.</span></span> <span data-ttu-id="0c516-274">這是在 HoloLens 安裝期間教授。</span><span class="sxs-lookup"><span data-stu-id="0c516-274">This is taught during HoloLens setup.</span></span>

- <span data-ttu-id="0c516-275">當使用者的手勢接近或中斷應用程式內的手勢框架界限時，通知使用者，表示遺失的手勢會導致不想要的結果。</span><span class="sxs-lookup"><span data-stu-id="0c516-275">Notifying users when their gestures are nearing or breaking the gesture frame boundaries within an application to the degree that a lost gesture leads to undesired outcomes.</span></span> <span data-ttu-id="0c516-276">研究已展示這類通知系統的主要品質。</span><span class="sxs-lookup"><span data-stu-id="0c516-276">Research has shown the key qualities of such a notification system.</span></span> <span data-ttu-id="0c516-277">HoloLens shell 會在中央游標上提供此類型通知（視覺效果）的良好範例，指出界限跨越的方向。</span><span class="sxs-lookup"><span data-stu-id="0c516-277">The HoloLens shell provides a good example of this type of notification--visual, on the central cursor, indicating the direction in which boundary crossing is taking place.</span></span>

- <span data-ttu-id="0c516-278">您應該將突破手勢框架界限的後果最小化。</span><span class="sxs-lookup"><span data-stu-id="0c516-278">Consequences of breaking the gesture frame boundaries should be minimized.</span></span> <span data-ttu-id="0c516-279">一般來說，這表示手勢的結果應該在界限停止，而不是反轉。</span><span class="sxs-lookup"><span data-stu-id="0c516-279">In general, this means that the outcome of a gesture should be stopped at the boundary, and not reversed.</span></span> <span data-ttu-id="0c516-280">比方說，如果使用者要在房間內移動一些全像的物件，則當軌跡框架被入侵時，移動應該會停止，而且不會傳回至起始點。</span><span class="sxs-lookup"><span data-stu-id="0c516-280">For example, if a user is moving some holographic object across a room, the movement should stop when the gesture frame is breached, and not returned to the starting point.</span></span> <span data-ttu-id="0c516-281">使用者可能會遇到一些挫折，但可能更快速地瞭解界限，而不必每次重新開機其完整的預期動作。</span><span class="sxs-lookup"><span data-stu-id="0c516-281">The user might experience some frustration, but might more quickly understand the boundaries, and not have to restart their full intended actions each time.</span></span>



## <a name="see-also"></a><span data-ttu-id="0c516-282">請參閱</span><span class="sxs-lookup"><span data-stu-id="0c516-282">See also</span></span>
* [<span data-ttu-id="0c516-283">眼動式互動</span><span class="sxs-lookup"><span data-stu-id="0c516-283">Eye-based interaction</span></span>](eye-gaze-interaction.md)
* [<span data-ttu-id="0c516-284">HoloLens 2 的眼球追蹤</span><span class="sxs-lookup"><span data-stu-id="0c516-284">Eye tracking on HoloLens 2</span></span>](eye-tracking.md)
* [<span data-ttu-id="0c516-285">目光和停駐</span><span class="sxs-lookup"><span data-stu-id="0c516-285">Gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="0c516-286">手 - 直接操作</span><span class="sxs-lookup"><span data-stu-id="0c516-286">Hands - Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="0c516-287">手 - 手勢</span><span class="sxs-lookup"><span data-stu-id="0c516-287">Hands - Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="0c516-288">手 - 指向和行動</span><span class="sxs-lookup"><span data-stu-id="0c516-288">Hands - Point and commit</span></span>](point-and-commit.md)
* [<span data-ttu-id="0c516-289">本能互動</span><span class="sxs-lookup"><span data-stu-id="0c516-289">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="0c516-290">語音輸入</span><span class="sxs-lookup"><span data-stu-id="0c516-290">Voice input</span></span>](voice-input.md)

