---
title: 注視並認可
description: 深入瞭解「注視」和「認可」輸入模型，包括兩種類型的注視 (前端和眼睛) ，以及各種類型的認可。
author: sostel
ms.author: sostel
ms.date: 10/31/2019
ms.topic: article
keywords: 混合的現實、注視、注視目標、互動、設計、眼睛追蹤、head 追蹤
ms.openlocfilehash: 887d1a30a974bdd643889959a1fee55e96d7b16a
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2020
ms.locfileid: "91680940"
---
# <a name="gaze-and-commit"></a><span data-ttu-id="155ca-104">注視並認可</span><span class="sxs-lookup"><span data-stu-id="155ca-104">Gaze and commit</span></span>

<span data-ttu-id="155ca-105">「 _注視」和「認可_ 」是一種基本的輸入模型，與使用滑鼠： _點 & 按一下_ 來與電腦互動的方式密切相關。</span><span class="sxs-lookup"><span data-stu-id="155ca-105">_Gaze and commit_ is a fundamental input model that is closely related with the way we're interacting with our computers using the mouse: _Point & click_ .</span></span>
<span data-ttu-id="155ca-106">在這個頁面中，我們會介紹兩種類型的注視輸入 (前端和眼睛) 以及不同類型的認可動作。</span><span class="sxs-lookup"><span data-stu-id="155ca-106">On this page, we introduce two types of gaze input (head- and eye-gaze) and different types of commit actions.</span></span> 
<span data-ttu-id="155ca-107">您可以使用間接操作將 _注視和 commit_ 視為最遠的輸入模型。</span><span class="sxs-lookup"><span data-stu-id="155ca-107">_Gaze and commit_ is considered a far input model with indirect manipulation.</span></span>
<span data-ttu-id="155ca-108">這表示它最適合用來與不觸及的全像內容互動。</span><span class="sxs-lookup"><span data-stu-id="155ca-108">This means it is best used for interacting with holographic content that is out of reach.</span></span>

<span data-ttu-id="155ca-109">混合現實耳機可以使用使用者的標頭位置和方向來決定其前端方向向量。</span><span class="sxs-lookup"><span data-stu-id="155ca-109">Mixed reality headsets can use the position and orientation of the user's head to determine their head direction vector.</span></span> <span data-ttu-id="155ca-110">您可以將此視為直接從使用者的雙眼之間向前直指的雷射。</span><span class="sxs-lookup"><span data-stu-id="155ca-110">You can think of this as a laser that points straight ahead from directly between the user's eyes.</span></span> <span data-ttu-id="155ca-111">這是相當粗略的使用者觀看位置概算。</span><span class="sxs-lookup"><span data-stu-id="155ca-111">This is a fairly coarse approximation of where the user is looking.</span></span> <span data-ttu-id="155ca-112">您的應用程式可以將此光線與虛擬或真實世界物件相交，並在該位置繪製游標，讓使用者知道他們目前的目標。</span><span class="sxs-lookup"><span data-stu-id="155ca-112">Your application can intersect this ray with virtual or real-world objects, and draw a cursor at that location to let the user know what they are currently targeting.</span></span>

<span data-ttu-id="155ca-113">除了頭部眼，某些混合的現實耳機（例如 HoloLens 2）包含產生眼睛向量的眼睛追蹤系統。</span><span class="sxs-lookup"><span data-stu-id="155ca-113">In addition to head gaze, some mixed reality headsets, such as HoloLens 2, include eye tracking systems that produce an eye-gaze vector.</span></span> <span data-ttu-id="155ca-114">這會對使用者觀看的位置提供精細的測量。</span><span class="sxs-lookup"><span data-stu-id="155ca-114">This provides a fine-grained measurement of where the user is looking.</span></span> <span data-ttu-id="155ca-115">在這兩種情況下，注視都代表使用者意圖的重要信號。</span><span class="sxs-lookup"><span data-stu-id="155ca-115">In both cases, the gaze represents an important signal for the user's intent.</span></span> <span data-ttu-id="155ca-116">系統可以更妥善地解讀和預測使用者的預期動作、提高使用者滿意度，以及提升效能。</span><span class="sxs-lookup"><span data-stu-id="155ca-116">The better the system can interpret and predict the user's intended actions, user satisfaction increases and performance improves.</span></span>

<span data-ttu-id="155ca-117">以下幾個範例可讓您以混合現實開發人員的身分來受益于 head 或眼睛：</span><span class="sxs-lookup"><span data-stu-id="155ca-117">Below are a few examples for how you as a mixed reality developer can benefit from head- or eye-gaze:</span></span>
* <span data-ttu-id="155ca-118">您的應用程式可以與場景中的全像眼睛相同，以判斷使用者的注意力 (更精確的眼睛) 。</span><span class="sxs-lookup"><span data-stu-id="155ca-118">Your app can intersect gaze with the holograms in your scene to determine where the user's attention is (more precise with eye-gaze).</span></span>
* <span data-ttu-id="155ca-119">您的應用程式可以根據使用者的注視來進行頻道手勢和控制器按動作，讓使用者可以順暢地選取、啟用、抓取、滾動或以其他方式與其全息的互動。</span><span class="sxs-lookup"><span data-stu-id="155ca-119">Your app can channel gestures and controller presses based on the user's gaze, letting the user seamlessly select, activate, grab, scroll, or otherwise interact with their holograms.</span></span>
* <span data-ttu-id="155ca-120">您的應用程式可以讓使用者將表面光線與空間對應網格相交，以將影像放在真實世界的表面上。</span><span class="sxs-lookup"><span data-stu-id="155ca-120">Your app can let the user place holograms on real-world surfaces by intersecting their gaze ray with the spatial mapping mesh.</span></span>
* <span data-ttu-id="155ca-121">您的應用程式可以知道使用者何時 *不* 會查看重要物件的方向，這可能會導致您的應用程式提供視覺效果和音訊提示，以轉向該物件。</span><span class="sxs-lookup"><span data-stu-id="155ca-121">Your app can know when the user is *not* looking in the direction of an important object, which can lead your app to give visual and audio cues to turn towards that object.</span></span>

<br>


## <a name="device-support"></a><span data-ttu-id="155ca-122">裝置支援</span><span class="sxs-lookup"><span data-stu-id="155ca-122">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="155ca-123"><strong>輸入模型</strong></span><span class="sxs-lookup"><span data-stu-id="155ca-123"><strong>Input model</strong></span></span></td>
        <td><span data-ttu-id="155ca-124"><a href="../hololens-hardware-details.md"><strong>HoloLens (第 1 代)</strong></a></span><span class="sxs-lookup"><span data-stu-id="155ca-124"><a href="../hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="155ca-125"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="155ca-125"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="155ca-126"><a href="../discover/immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></span><span class="sxs-lookup"><span data-stu-id="155ca-126"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="155ca-127">頭部注視並認可</span><span class="sxs-lookup"><span data-stu-id="155ca-127">Head-gaze and commit</span></span></td>
        <td><span data-ttu-id="155ca-128">✔️ 建議使用</span><span class="sxs-lookup"><span data-stu-id="155ca-128">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="155ca-129">✔️ 建議使用 (第三個選擇 - <a href="interaction-fundamentals.md">查看其他選項</a>)</span><span class="sxs-lookup"><span data-stu-id="155ca-129">✔️ Recommended (third choice - <a href="interaction-fundamentals.md">See the other options</a>)</span></span></td>
        <td><span data-ttu-id="155ca-130">➕ 替代選項</span><span class="sxs-lookup"><span data-stu-id="155ca-130">➕ Alternate option</span></span></td>
    </tr>
         <tr>
        <td><span data-ttu-id="155ca-131">眼部注視並認可</span><span class="sxs-lookup"><span data-stu-id="155ca-131">Eye-gaze and commit</span></span></td>
        <td><span data-ttu-id="155ca-132">❌ 無法使用</span><span class="sxs-lookup"><span data-stu-id="155ca-132">❌ Not available</span></span></td>
        <td><span data-ttu-id="155ca-133">✔️ 建議使用 (第三個選擇 - <a href="interaction-fundamentals.md">查看其他選項</a>)</span><span class="sxs-lookup"><span data-stu-id="155ca-133">✔️ Recommended (third choice - <a href="interaction-fundamentals.md">See the other options</a>)</span></span></td>
        <td><span data-ttu-id="155ca-134">❌ 無法使用</span><span class="sxs-lookup"><span data-stu-id="155ca-134">❌ Not available</span></span></td>
    </tr>
</table>


## <a name="gaze"></a><span data-ttu-id="155ca-135">注視</span><span class="sxs-lookup"><span data-stu-id="155ca-135">Gaze</span></span>

### <a name="eye--or-head-gaze"></a><span data-ttu-id="155ca-136">眼睛或頭部？</span><span class="sxs-lookup"><span data-stu-id="155ca-136">Eye- or head-gaze?</span></span>
<span data-ttu-id="155ca-137">當遇到問題時，您應該考慮幾個考慮：您是否應該使用「眼睛和認可」或「前端和認可」輸入模型。</span><span class="sxs-lookup"><span data-stu-id="155ca-137">There are several considerations to take into account when faced with the question whether you should use the "eye-gaze and commit" or "head-gaze and commit" input model.</span></span> <span data-ttu-id="155ca-138">如果您正在針對沉浸式耳機或 HoloLens (第一代) 進行開發，則選擇很簡單：標上和認可。</span><span class="sxs-lookup"><span data-stu-id="155ca-138">If you're developing for an immersive headset or for HoloLens (1st gen) then the choice is simple: Head-gaze and commit.</span></span> <span data-ttu-id="155ca-139">如果您正在針對 HoloLens 2 進行開發，則選擇會變得更困難，這也是瞭解每一種方法的優點和挑戰，是很重要的。</span><span class="sxs-lookup"><span data-stu-id="155ca-139">If you're developing for HoloLens 2, the choice becomes a little harder which is why it's important to understand the advantages and challenges that come with each of them.</span></span>
<span data-ttu-id="155ca-140">在下表中，我們編譯了一些很廣泛的專業人員和 con，以對比眼睛的目標。</span><span class="sxs-lookup"><span data-stu-id="155ca-140">We compiled some broad pro's and con's in the table below to contrast head- vs. eye-gaze targeting.</span></span> <span data-ttu-id="155ca-141">這並不是完整的，我們建議您在此處深入瞭解混合現實中的眼睛目標：</span><span class="sxs-lookup"><span data-stu-id="155ca-141">This is far from complete and we suggest learning more about eye-gaze targeting in mixed reality here:</span></span>
* <span data-ttu-id="155ca-142">[HoloLens 2 上的眼睛追蹤](eye-tracking.md)：在 HoloLens 2 上推出新的眼睛追蹤功能，包括一些開發人員指引。</span><span class="sxs-lookup"><span data-stu-id="155ca-142">[Eye tracking on HoloLens 2](eye-tracking.md): General introduction of our new eye tracking capability on HoloLens 2 including some developer guidance.</span></span> 
* <span data-ttu-id="155ca-143">[眼睛的互動](eye-gaze-interaction.md)：規劃使用眼睛追蹤作為輸入時的設計考慮和建議。</span><span class="sxs-lookup"><span data-stu-id="155ca-143">[Eye-gaze interaction](eye-gaze-interaction.md): Design considerations and recommendations when planning to use eye tracking as an input.</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
   <tr>
        <td><span data-ttu-id="155ca-144"><strong>眼睛的目標</strong></span><span class="sxs-lookup"><span data-stu-id="155ca-144"><strong>Eye-gaze targeting</strong></span></span></td>
        <td><span data-ttu-id="155ca-145"><strong>頭部注視定向</strong></span><span class="sxs-lookup"><span data-stu-id="155ca-145"><strong>Head-gaze targeting</strong></span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="155ca-146">快速！</span><span class="sxs-lookup"><span data-stu-id="155ca-146">Fast!</span></span></td>
        <td><span data-ttu-id="155ca-147">慢</span><span class="sxs-lookup"><span data-stu-id="155ca-147">Slower</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="155ca-148">低工作量 (幾乎不需要任何主體移動) </span><span class="sxs-lookup"><span data-stu-id="155ca-148">Low effort (barely any body movements necessary)</span></span></td>
        <td><span data-ttu-id="155ca-149">可以是 fatiguing 可能的不適感 (例如，頸部壓力) </span><span class="sxs-lookup"><span data-stu-id="155ca-149">Can be fatiguing - Possible discomfort (e.g., neck strain)</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="155ca-150">不需要資料指標，但建議使用微妙的意見反應</span><span class="sxs-lookup"><span data-stu-id="155ca-150">Does not require a cursor, but subtle feedback is recommended</span></span></td>
        <td><span data-ttu-id="155ca-151">需要顯示資料指標</span><span class="sxs-lookup"><span data-stu-id="155ca-151">Requires to show a cursor</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="155ca-152">無平滑的移動–例如，不適合繪圖</span><span class="sxs-lookup"><span data-stu-id="155ca-152">No smooth eye movements – e.g., not good for drawing</span></span></td>
        <td><span data-ttu-id="155ca-153">更受控制且明確</span><span class="sxs-lookup"><span data-stu-id="155ca-153">More controlled and explicit</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="155ca-154">很難進行非常小的目標 (例如，小按鈕或網頁連結) </span><span class="sxs-lookup"><span data-stu-id="155ca-154">Difficult for very small targets (e.g., tiny buttons or weblinks)</span></span></td>
        <td><span data-ttu-id="155ca-155">可靠！</span><span class="sxs-lookup"><span data-stu-id="155ca-155">Reliable!</span></span> <span data-ttu-id="155ca-156">絕佳的回復！</span><span class="sxs-lookup"><span data-stu-id="155ca-156">Great fallback!</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="155ca-157">...</span><span class="sxs-lookup"><span data-stu-id="155ca-157">...</span></span></td>
        <td><span data-ttu-id="155ca-158">...</span><span class="sxs-lookup"><span data-stu-id="155ca-158">...</span></span></td>
    </tr>
</table>

<span data-ttu-id="155ca-159">無論您是針對您的注視和認可輸入模型使用前端或眼睛，都有不同組的設計條件約束，這些條件約束將會在 [眼睛和認可](gaze-and-commit-eyes.md) 以及 [前端和認可](gaze-and-commit-head.md) 文章中各自討論。</span><span class="sxs-lookup"><span data-stu-id="155ca-159">Whether you use head-gaze or eye-gaze for your gaze-and-commit input model comes with different sets of design constraints, which will be covered separately in the [eye-gaze and commit](gaze-and-commit-eyes.md) and [head-gaze and commit](gaze-and-commit-head.md) articles.</span></span>

<br>

---

### <a name="cursor"></a><span data-ttu-id="155ca-160">資料指標</span><span class="sxs-lookup"><span data-stu-id="155ca-160">Cursor</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="155ca-161">針對 head，大部分的應用程式應該使用 [游標](cursors.md) (或其他聽覺/視覺指示) ，讓使用者在他們即將與其互動的方面具有信賴度。</span><span class="sxs-lookup"><span data-stu-id="155ca-161">For head gaze, most apps should use a [cursor](cursors.md) (or other auditory/visual indication) to give the user confidence in what they're about to interact with.</span></span> <span data-ttu-id="155ca-162">您通常會將這個資料指標放在世界中，其中的前端光線最先與物件（可能是全息圖或真實世界表面）相交。</span><span class="sxs-lookup"><span data-stu-id="155ca-162">You typically position this cursor in the world where their head gaze ray first intersects an object, which may be a hologram or a real-world surface.</span></span><br>
        <br>
        <span data-ttu-id="155ca-163">針對眼睛，我們通常不建議您 *不要* 顯示資料指標，因為這可能會對使用者造成干擾和討厭。</span><span class="sxs-lookup"><span data-stu-id="155ca-163">For eye gaze, we generally recommend *not* to show a cursor, as this can quickly become distracting and annoying for the user.</span></span> <span data-ttu-id="155ca-164">相反地強調顯示視覺效果目標，或使用非常模糊的眼睛游標，以提供使用者即將與其互動的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="155ca-164">Instead subtly highlight visual targets or use a very faint eye cursor to provide confidence about what the user is about to interact with.</span></span> <span data-ttu-id="155ca-165">如需詳細資訊，請參閱 HoloLens 2 上 [的眼睛輸入的設計指引](eye-tracking.md) 。</span><span class="sxs-lookup"><span data-stu-id="155ca-165">For more information, please check out our [design guidance for eye-based input](eye-tracking.md) on HoloLens 2.</span></span>
    :::column-end:::
        :::column:::
       <span data-ttu-id="155ca-166">![顯示注視的視覺效果游標範例](images/cursor.jpg)</span><span class="sxs-lookup"><span data-stu-id="155ca-166">![An example visual cursor to show gaze](images/cursor.jpg)</span></span><br>
       <span data-ttu-id="155ca-167">*影像：顯示注視的視覺效果游標範例*</span><span class="sxs-lookup"><span data-stu-id="155ca-167">*Image: An example visual cursor to show gaze*</span></span>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="commit"></a><span data-ttu-id="155ca-168">Commit</span><span class="sxs-lookup"><span data-stu-id="155ca-168">Commit</span></span>
<span data-ttu-id="155ca-169">談到不同的 _方式來看_ 看某個目標之後，讓我們再談談一下看看 _和認可_ 的 _認可_ 部分。</span><span class="sxs-lookup"><span data-stu-id="155ca-169">After talking about different ways to _gaze_ at a target, let's talk a bit more about the _commit_ part in _gaze and commit_ .</span></span>
<span data-ttu-id="155ca-170">以物件或 UI 元素為目標之後，使用者可以使用次要輸入進行互動或按一下。</span><span class="sxs-lookup"><span data-stu-id="155ca-170">After targeting an object or UI element, the user can interact or click on it using a secondary input.</span></span> <span data-ttu-id="155ca-171">這就是所謂的輸入模型認可步驟。</span><span class="sxs-lookup"><span data-stu-id="155ca-171">This is known as the commit step of the input model.</span></span> 

<span data-ttu-id="155ca-172">支援的認可方法如下：</span><span class="sxs-lookup"><span data-stu-id="155ca-172">The following commit methods are supported:</span></span>
- <span data-ttu-id="155ca-173">點擊手勢 (也就是，將您手上的手抬起，並將您的食指與 thumb 合在一起) </span><span class="sxs-lookup"><span data-stu-id="155ca-173">Air tap hand gesture (i.e., raise your hand in front of you and bring together your index finger and thumb)</span></span>
- <span data-ttu-id="155ca-174">說「 _select_ 」或其中一個目標語音命令</span><span class="sxs-lookup"><span data-stu-id="155ca-174">Say _"select"_ or one of the targeted voice commands</span></span>
- <span data-ttu-id="155ca-175">在[HoloLens Clicker](https://docs.microsoft.com/hololens/hololens1-clicker)上按單一按鈕</span><span class="sxs-lookup"><span data-stu-id="155ca-175">Press a single button on a [HoloLens Clicker](https://docs.microsoft.com/hololens/hololens1-clicker)</span></span>
- <span data-ttu-id="155ca-176">按下 Xbox 遊戲台上的 [A] 按鈕</span><span class="sxs-lookup"><span data-stu-id="155ca-176">Press the 'A' button on an Xbox gamepad</span></span>
- <span data-ttu-id="155ca-177">按下 Xbox 適應性控制器上的 [A] 按鈕</span><span class="sxs-lookup"><span data-stu-id="155ca-177">Press the 'A' button on an Xbox adaptive controller</span></span>

### <a name="gaze-and-air-tap-gesture"></a><span data-ttu-id="155ca-178">注視和點擊手勢</span><span class="sxs-lookup"><span data-stu-id="155ca-178">Gaze and air tap gesture</span></span>
<span data-ttu-id="155ca-179">空中點選是手部直立的點選手勢。</span><span class="sxs-lookup"><span data-stu-id="155ca-179">Air tap is a tapping gesture with the hand held upright.</span></span> <span data-ttu-id="155ca-180">若要執行點一下，請將您的索引指向就緒的位置，然後使用您的 thumb 來縮小，然後將您的索引手指重回來以釋放。</span><span class="sxs-lookup"><span data-stu-id="155ca-180">To perform an air tap, raise your index finger to the ready position, then pinch with your thumb, and raise your index finger back up to release.</span></span> <span data-ttu-id="155ca-181">在 HoloLens (第1代) 上，按一下是最常見的次要輸入。</span><span class="sxs-lookup"><span data-stu-id="155ca-181">On HoloLens (1st gen), air tap is the most common secondary input.</span></span>


:::row:::
    :::column:::
       <span data-ttu-id="155ca-182">![觸達就緒位置](images/readyandpress-ready.jpg)</span><span class="sxs-lookup"><span data-stu-id="155ca-182">![Finger in the ready position](images/readyandpress-ready.jpg)</span></span><br>
       <span data-ttu-id="155ca-183">**觸達就緒位置**</span><span class="sxs-lookup"><span data-stu-id="155ca-183">**Finger in the ready position**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="155ca-184">![按下手指以點擊或按一下](images/readyandpress-press.jpg)</span><span class="sxs-lookup"><span data-stu-id="155ca-184">![Press finger down to tap or click](images/readyandpress-press.jpg)</span></span><br>
        <span data-ttu-id="155ca-185">**按下手指以點擊或按一下**</span><span class="sxs-lookup"><span data-stu-id="155ca-185">**Press finger down to tap or click**</span></span><br>
    :::column-end:::
:::row-end:::


<span data-ttu-id="155ca-186">HoloLens 2 也可以使用 [點一下]。</span><span class="sxs-lookup"><span data-stu-id="155ca-186">Air tap is also available on HoloLens 2.</span></span> <span data-ttu-id="155ca-187">它已從原始版本中放寬。</span><span class="sxs-lookup"><span data-stu-id="155ca-187">It has been relaxed from the original version.</span></span> <span data-ttu-id="155ca-188">幾乎所有類型的 pinches 現在都可支援，只要手邊的手是直立的，且仍維持。</span><span class="sxs-lookup"><span data-stu-id="155ca-188">Nearly all types of pinches are now supported as long as the hand is upright and holding still.</span></span> <span data-ttu-id="155ca-189">這可讓使用者更容易了解和執行手勢。</span><span class="sxs-lookup"><span data-stu-id="155ca-189">This makes it much easier for users to learn and perform the gesture.</span></span> <span data-ttu-id="155ca-190">這個新的空中會透過相同的 API 來取代舊的，讓現有的應用程式在重新編譯以進行 HoloLens 2 之後，會自動有新的行為。</span><span class="sxs-lookup"><span data-stu-id="155ca-190">This new air tap replaces the old one through the same API, so existing applications will have the new behavior automatically after recompiling for HoloLens 2.</span></span>

<br>

---

### <a name="gaze-and-select-voice-command"></a><span data-ttu-id="155ca-191">注視和「選取」聲音命令</span><span class="sxs-lookup"><span data-stu-id="155ca-191">Gaze and "Select" voice command</span></span>
<span data-ttu-id="155ca-192">語音命令是混合現實中的其中一個主要互動方法。</span><span class="sxs-lookup"><span data-stu-id="155ca-192">Voice commanding is one of the primary interaction methods in mixed reality.</span></span> <span data-ttu-id="155ca-193">它提供了一套功能強大的無人參與機制來控制系統。</span><span class="sxs-lookup"><span data-stu-id="155ca-193">It provides a very powerful hands-free mechanism to control the system.</span></span> <span data-ttu-id="155ca-194">語音互動模型有不同的類型：</span><span class="sxs-lookup"><span data-stu-id="155ca-194">There are different types of voice interaction models:</span></span>

- <span data-ttu-id="155ca-195">執行 click actuation 或 commit 作為次要輸入的泛型 "Select" 命令。</span><span class="sxs-lookup"><span data-stu-id="155ca-195">The generic "Select" command that performs a click actuation or commit as a secondary input.</span></span>
- <span data-ttu-id="155ca-196">物件命令 (例如，「關閉」或「變得更大」 ) 執行並認可至動作做為次要輸入。</span><span class="sxs-lookup"><span data-stu-id="155ca-196">Object commands (e.g., "Close" or "Make it bigger") perform and commit to an action as a secondary input.</span></span>
- <span data-ttu-id="155ca-197">全域命令 (例如「移至開始」 ) 不需要目標。</span><span class="sxs-lookup"><span data-stu-id="155ca-197">Global commands (e.g., "Go to start") don't require a target.</span></span>
- <span data-ttu-id="155ca-198">對話使用者介面或 Cortana 之類的實體都具有 AI 自然語言功能。</span><span class="sxs-lookup"><span data-stu-id="155ca-198">Conversation user interfaces or entities like Cortana have an AI natural language capability.</span></span>
- <span data-ttu-id="155ca-199">自訂語音命令</span><span class="sxs-lookup"><span data-stu-id="155ca-199">Custom voice commands</span></span>

<span data-ttu-id="155ca-200">若要瞭解更多詳細資料，以及可用語音命令的完整清單，以及如何使用這些命令，請參閱我們的 [語音](../out-of-scope/voice-design.md) 命令指引。</span><span class="sxs-lookup"><span data-stu-id="155ca-200">To find out more details as well as a comprehensive list of available voice commands and how to use them, check out our [voice commanding](../out-of-scope/voice-design.md) guidance.</span></span>

<br>

---


### <a name="gaze-and-hololens-clicker"></a><span data-ttu-id="155ca-201">注視和 HoloLens Clicker</span><span class="sxs-lookup"><span data-stu-id="155ca-201">Gaze and HoloLens Clicker</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="155ca-202">HoloLens Clicker 是特別為 HoloLens 建立的第一個週邊設備。</span><span class="sxs-lookup"><span data-stu-id="155ca-202">The HoloLens Clicker is the first peripheral device built specifically for HoloLens.</span></span> <span data-ttu-id="155ca-203">它隨附于 HoloLens (第一代) 開發版。</span><span class="sxs-lookup"><span data-stu-id="155ca-203">It is included with HoloLens (1st gen) Development Edition.</span></span> <span data-ttu-id="155ca-204">HoloLens Clicker 可讓使用者按下最少量的動作，並認可為次要輸入。</span><span class="sxs-lookup"><span data-stu-id="155ca-204">The HoloLens Clicker lets a user click with minimal hand motion, and commit as a secondary input.</span></span> <span data-ttu-id="155ca-205">HoloLens Clicker 會連接到 HoloLens (第1代) 或使用藍牙低能源 (BTLE) HoloLens 2。</span><span class="sxs-lookup"><span data-stu-id="155ca-205">The HoloLens Clicker connects to HoloLens (1st gen) or HoloLens 2 using Bluetooth Low Energy (BTLE).</span></span><br>
        <br>
        [<span data-ttu-id="155ca-206">有關將裝置配對的詳細資訊和指示</span><span class="sxs-lookup"><span data-stu-id="155ca-206">More information and instructions to pair the device</span></span>](../discover/hardware-accessories.md#pairing-bluetooth-accessories)<br>
        <br>
        <span data-ttu-id="155ca-207">*映射： HoloLens Clicker*</span><span class="sxs-lookup"><span data-stu-id="155ca-207">*Image: HoloLens Clicker*</span></span>
    :::column-end:::
        :::column:::
       ![HoloLens Clicker](images/hololens-clicker-500px.jpg)<br>
    :::column-end:::
:::row-end:::

<br>

---


### <a name="gaze-and-xbox-wireless-controller"></a><span data-ttu-id="155ca-209">注視和 Xbox 無線控制器</span><span class="sxs-lookup"><span data-stu-id="155ca-209">Gaze and Xbox Wireless Controller</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="155ca-210">Xbox 無線控制器會使用 [A] 按鈕，以次要輸入的形式執行 click actuation。</span><span class="sxs-lookup"><span data-stu-id="155ca-210">The Xbox Wireless Controller performs a click actuation as a secondary input by using the 'A' button.</span></span> <span data-ttu-id="155ca-211">裝置會對應至一組預設的動作，以協助流覽和控制系統。</span><span class="sxs-lookup"><span data-stu-id="155ca-211">The device is mapped to a default set of actions that help navigate and control the system.</span></span> <span data-ttu-id="155ca-212">如果您想要自訂控制器，請使用 Xbox 配件應用程式來設定 Xbox 無線控制器。</span><span class="sxs-lookup"><span data-stu-id="155ca-212">If you want to customize the controller, use the Xbox Accessories application to configure your Xbox Wireless Controller.</span></span><br>
        <br>
        [<span data-ttu-id="155ca-213">如何將 Xbox 控制器與您的電腦配對</span><span class="sxs-lookup"><span data-stu-id="155ca-213">How to pair an Xbox controller with your PC</span></span>](../discover/hardware-accessories.md#pairing-bluetooth-accessories)<br>
        <br>
        <span data-ttu-id="155ca-214">*影像： Xbox 無線控制器*</span><span class="sxs-lookup"><span data-stu-id="155ca-214">*Image: Xbox Wireless Controller*</span></span>
    :::column-end:::
        :::column:::
       ![Xbox 無線控制器](images/xboxcontroller.jpg)<br>
    :::column-end:::
:::row-end:::



<br>

---


### <a name="gaze-and-xbox-adaptive-controller"></a><span data-ttu-id="155ca-216">注視和 Xbox 調適型控制器</span><span class="sxs-lookup"><span data-stu-id="155ca-216">Gaze and Xbox Adaptive Controller</span></span>
<span data-ttu-id="155ca-217">Xbox 調適型控制器是專為滿足行動裝置的需求而設計，可協助讓混合現實更容易存取的裝置具有統一的中樞。</span><span class="sxs-lookup"><span data-stu-id="155ca-217">Designed primarily to meet the needs of gamers with limited mobility, the Xbox Adaptive Controller is a unified hub for devices that helps make mixed reality more accessible.</span></span>

<span data-ttu-id="155ca-218">Xbox 適應性控制器會使用 [A] 按鈕，以次要輸入的形式執行 click actuation。</span><span class="sxs-lookup"><span data-stu-id="155ca-218">The Xbox Adaptive Controller performs a click actuation as a secondary input by using the 'A' button.</span></span> <span data-ttu-id="155ca-219">裝置會對應至一組預設的動作，以協助流覽和控制系統。</span><span class="sxs-lookup"><span data-stu-id="155ca-219">The device is mapped to a default set of actions that help navigate and control the system.</span></span> <span data-ttu-id="155ca-220">如果您想要自訂控制器，請使用 Xbox 配件應用程式來設定 Xbox 調適型控制器。</span><span class="sxs-lookup"><span data-stu-id="155ca-220">If you want to customize the controller, use the Xbox Accessories application to configure your Xbox Adaptive Controller.</span></span>

<span data-ttu-id="155ca-221">![Xbox Adaptive Controller](images/xbox-adaptive-controller-devices.jpg)</span><span class="sxs-lookup"><span data-stu-id="155ca-221">![Xbox Adaptive Controller](images/xbox-adaptive-controller-devices.jpg)</span></span><br>
<span data-ttu-id="155ca-222">*Xbox Adaptive Controller*</span><span class="sxs-lookup"><span data-stu-id="155ca-222">*Xbox Adaptive Controller*</span></span>

<span data-ttu-id="155ca-223">連接外部裝置（例如交換器、按鈕、掛接和操作杆）來建立獨特的自訂控制器體驗。</span><span class="sxs-lookup"><span data-stu-id="155ca-223">Connect external devices such as switches, buttons, mounts, and joysticks to create a custom controller experience that is uniquely yours.</span></span> <span data-ttu-id="155ca-224">按鈕、操縱杆和觸發程式輸入都是由透過 3.5 mm 插孔和 USB 埠連接的輔助裝置所控制。</span><span class="sxs-lookup"><span data-stu-id="155ca-224">Button, thumbstick, and trigger inputs are controlled with assistive devices connected through 3.5mm jacks and USB ports.</span></span>

<span data-ttu-id="155ca-225">![Xbox Adaptive Controller 連接埠](images/xbox-adaptive-controller-ports.jpg)</span><span class="sxs-lookup"><span data-stu-id="155ca-225">![Xbox Adaptive Controller ports](images/xbox-adaptive-controller-ports.jpg)</span></span><br>
<span data-ttu-id="155ca-226">*Xbox Adaptive Controller 連接埠*</span><span class="sxs-lookup"><span data-stu-id="155ca-226">*Xbox Adaptive Controller ports*</span></span>

[<span data-ttu-id="155ca-227">裝置配對指示</span><span class="sxs-lookup"><span data-stu-id="155ca-227">Instructions to pair the device</span></span>](../discover/hardware-accessories.md#pairing-bluetooth-accessories)

<span data-ttu-id="155ca-228"><a href=https://www.xbox.com/xbox-one/accessories/controllers/xbox-adaptive-controller>在 Xbox 網站上可取得更多資訊</a></span><span class="sxs-lookup"><span data-stu-id="155ca-228"><a href=https://www.xbox.com/xbox-one/accessories/controllers/xbox-adaptive-controller>More info available on the Xbox site</a></span></span>

<br>

---

## <a name="composite-gestures"></a><span data-ttu-id="155ca-229">複合手勢</span><span class="sxs-lookup"><span data-stu-id="155ca-229">Composite gestures</span></span>

### <a name="air-tap"></a><span data-ttu-id="155ca-230">空中點選</span><span class="sxs-lookup"><span data-stu-id="155ca-230">Air tap</span></span>
<span data-ttu-id="155ca-231">點擊手勢 (以及下面的其他手勢) 只會回應特定的點。</span><span class="sxs-lookup"><span data-stu-id="155ca-231">The air tap gesture (as well as the other gestures below) reacts only to a specific tap.</span></span> <span data-ttu-id="155ca-232">若要偵測其他點擊（例如功能表或理解），您的應用程式必須直接使用上述兩個主要元件手勢區段中所述的較低層級互動。</span><span class="sxs-lookup"><span data-stu-id="155ca-232">To detect other taps, such as Menu or Grasp, your application must directly use the lower-level interactions described in the two key component gestures section above.</span></span>

### <a name="tap-and-hold"></a><span data-ttu-id="155ca-233">點選並按住</span><span class="sxs-lookup"><span data-stu-id="155ca-233">Tap and hold</span></span>
<span data-ttu-id="155ca-234">按住只是維持空中點選的手指朝下位置。</span><span class="sxs-lookup"><span data-stu-id="155ca-234">Hold is simply maintaining the downward finger position of the air tap.</span></span> <span data-ttu-id="155ca-235">使用「點擊和拖曳」的組合，可讓您在結合 arm 移動（例如挑選物件）時，使用各種更複雜的「點擊和拖曳」互動，而不是啟用它，或在顯示操作功能表之類的次要互動。</span><span class="sxs-lookup"><span data-stu-id="155ca-235">The combination of air tap and hold allows for a variety of more complex "click and drag" interactions when combined with arm movement such as picking up an object instead of activating it or mousedown secondary interactions such as showing a context menu.</span></span>
<span data-ttu-id="155ca-236">不過，針對這個手勢進行設計時應格外小心，因為使用者很容易在任何延伸手勢的過程中放鬆其手勢。</span><span class="sxs-lookup"><span data-stu-id="155ca-236">Caution should be used when designing for this gesture however, as users can be prone to relaxing their hand postures during the course of any extended gesture.</span></span>

### <a name="manipulation"></a><span data-ttu-id="155ca-237">操作</span><span class="sxs-lookup"><span data-stu-id="155ca-237">Manipulation</span></span>
<span data-ttu-id="155ca-238">當您想1:1 要讓全像全像移動、調整大小或旋轉全像移動、調整大小或旋轉影像時，可以使用操作手勢來移動、調整大小或旋轉。</span><span class="sxs-lookup"><span data-stu-id="155ca-238">Manipulation gestures can be used to move, resize, or rotate a hologram when you want the hologram to react 1:1 to the user's hand movements.</span></span> <span data-ttu-id="155ca-239">這類 1:1 移動的用途之一是要讓使用者可以實際繪圖。</span><span class="sxs-lookup"><span data-stu-id="155ca-239">One use for such 1:1 movements is to let the user draw or paint in the world.</span></span>
<span data-ttu-id="155ca-240">操作手勢的初始定向應經由注視或指向來完成。</span><span class="sxs-lookup"><span data-stu-id="155ca-240">The initial targeting for a manipulation gesture should be done by gaze or pointing.</span></span> <span data-ttu-id="155ca-241">當點一下和按住開始之後，就會以手動方式處理物件的任何操作，讓使用者在操作時進行查詢。</span><span class="sxs-lookup"><span data-stu-id="155ca-241">Once the tap and hold starts, any manipulation of the object is handled by hand movements, freeing the user to look around while they manipulate.</span></span>

### <a name="navigation"></a><span data-ttu-id="155ca-242">巡覽</span><span class="sxs-lookup"><span data-stu-id="155ca-242">Navigation</span></span>
<span data-ttu-id="155ca-243">瀏覽手勢的運作方式如同虛擬搖桿，可用來瀏覽 UI 小工具，例如放射狀功能表。</span><span class="sxs-lookup"><span data-stu-id="155ca-243">Navigation gestures operate like a virtual joystick, and can be used to navigate UI widgets, such as radial menus.</span></span> <span data-ttu-id="155ca-244">您可點選並按住來啟動手勢，然後在標準化 3D Cube (在初次按壓時置中) 中移動您的手。</span><span class="sxs-lookup"><span data-stu-id="155ca-244">You tap and hold to start the gesture and then move your hand within a normalized 3D cube, centered around the initial press.</span></span> <span data-ttu-id="155ca-245">您可以將您的手沿著 X、 Y 或 Z 軸從值 -1 移到 1 (而 0 表示起點)。</span><span class="sxs-lookup"><span data-stu-id="155ca-245">You can move your hand along the X, Y or Z axis from a value of -1 to 1, with 0 being the starting point.</span></span>
<span data-ttu-id="155ca-246">瀏覽可用來建置以速度為基礎的連續捲動或縮放手勢，類似於藉由按一下滑鼠中間按鈕，然後上下移動滑鼠來捲動 2D UI。</span><span class="sxs-lookup"><span data-stu-id="155ca-246">Navigation can be used to build velocity-based continuous scrolling or zooming gestures, similar to scrolling a 2D UI by clicking the middle mouse button and then moving the mouse up and down.</span></span>

<span data-ttu-id="155ca-247">使用 rails 的導覽指的是在特定軸中辨識移動的能力，直到到達該軸上的特定臨界值為止。</span><span class="sxs-lookup"><span data-stu-id="155ca-247">Navigation with rails refers to the ability of recognizing movements in certain axis until a certain threshold is reached on that axis.</span></span> <span data-ttu-id="155ca-248">當開發人員在應用程式中啟用多個軸的移動時（例如，如果應用程式設定為辨識跨 X、Y 軸的導覽手勢，但同時指定 X 軸與 rails），這項功能就很有用。</span><span class="sxs-lookup"><span data-stu-id="155ca-248">This is only useful when movement in more than one axis is enabled in an application by the developer, such as if an application is configured to recognize navigation gestures across X, Y axis but also specified X axis with rails.</span></span> <span data-ttu-id="155ca-249">在此情況下，系統會在 X 軸上辨識手間的移動，只要它們留在 X 軸的虛數滑軌 (指南) ，如果在 Y 軸上也會發生手移動。</span><span class="sxs-lookup"><span data-stu-id="155ca-249">In this case the system will recognize hand movements across X axis as long as they remain within an imaginary rails (guide) on the X axis, if hand movement also occurs on the Y axis.</span></span>

<span data-ttu-id="155ca-250">在 2D 應用程式內，使用者可以使用垂直瀏覽手勢在應用程式內捲動、縮放或拖曳。</span><span class="sxs-lookup"><span data-stu-id="155ca-250">Within 2D apps, users can use vertical navigation gestures to scroll, zoom, or drag inside the app.</span></span> <span data-ttu-id="155ca-251">這會在應用程式中插入虛擬手指觸控，以模擬同類型的觸控手勢。</span><span class="sxs-lookup"><span data-stu-id="155ca-251">This injects virtual finger touches to the app to simulate touch gestures of the same type.</span></span> <span data-ttu-id="155ca-252">使用者可以在應用程式上方的工具列上切換，藉由選取按鈕或說「<滾動/拖曳/縮放> 工具」，來選取要進行的動作。</span><span class="sxs-lookup"><span data-stu-id="155ca-252">Users can select which of these actions take place by toggling between the tools on the bar above the application, either by selecting the button or saying '<Scroll/Drag/Zoom> Tool'.</span></span>

[<span data-ttu-id="155ca-253">複合手勢的詳細資訊</span><span class="sxs-lookup"><span data-stu-id="155ca-253">More info on composite gestures</span></span>](gaze-and-commit.md#composite-gestures)

## <a name="gesture-recognizers"></a><span data-ttu-id="155ca-254">手勢辨識器</span><span class="sxs-lookup"><span data-stu-id="155ca-254">Gesture recognizers</span></span>

<span data-ttu-id="155ca-255">使用手勢辨識的其中一個優點是，您只能針對目前目標的全像全像影像所能接受的手勢設定手勢辨識器。</span><span class="sxs-lookup"><span data-stu-id="155ca-255">One benefit of using gesture recognition is that you can configure a gesture recognizer only for the gestures the currently targeted hologram can accept.</span></span> <span data-ttu-id="155ca-256">平臺只會視需要去除混淆，以區別這些特定支援的手勢。</span><span class="sxs-lookup"><span data-stu-id="155ca-256">The platform only does disambiguation as necessary to distinguish those particular supported gestures.</span></span> <span data-ttu-id="155ca-257">如此一來，只支援「敲擊」的全像是在按下和放開之間有任何時間長度，而同時支援點一下和按住的全像投影可以在按住時間閾值之後升階。</span><span class="sxs-lookup"><span data-stu-id="155ca-257">In this way, a hologram that just supports air tap can accept any length of time between press and release, while a hologram that supports both tap and hold can promote the tap to a hold after the hold time threshold.</span></span>

## <a name="hand-recognition"></a><span data-ttu-id="155ca-258">手部辨識</span><span class="sxs-lookup"><span data-stu-id="155ca-258">Hand recognition</span></span>
<span data-ttu-id="155ca-259">HoloLens 可藉由追蹤裝置可見的任一手或雙手位置來辨識手勢。</span><span class="sxs-lookup"><span data-stu-id="155ca-259">HoloLens recognizes hand gestures by tracking the position of either or both hands that are visible to the device.</span></span> <span data-ttu-id="155ca-260">當手部處於就緒狀態 (手背朝向您且食指朝上) 或按下狀態 (手背朝向您且食指朝下) 時，HoloLens 就會看見手部。</span><span class="sxs-lookup"><span data-stu-id="155ca-260">HoloLens sees hands when they are in either the ready state (back of the hand facing you with index finger up) or the pressed state (back of the hand facing you with the index finger down).</span></span> <span data-ttu-id="155ca-261">當手中有其他人時，HoloLens 會忽略它們。</span><span class="sxs-lookup"><span data-stu-id="155ca-261">When hands are in other poses, HoloLens ignores them.</span></span>
<span data-ttu-id="155ca-262">針對 HoloLens 偵測到的每個手，您可以存取其位置，而不需要方向和按下的狀態。</span><span class="sxs-lookup"><span data-stu-id="155ca-262">For each hand that HoloLens detects, you can access its position without orientation and its pressed state.</span></span> <span data-ttu-id="155ca-263">當手部接近手勢框架邊緣時，您也會取得方向向量，而您可對使用者顯示該向量，讓他們知道如何移動其手部以回到 HoloLens 可看見手部的位置。</span><span class="sxs-lookup"><span data-stu-id="155ca-263">As the hand nears the edge of the gesture frame, you're also provided with a direction vector, which you can show to the user so they know how to move their hand to get it back where HoloLens can see it.</span></span>

## <a name="gesture-frame"></a><span data-ttu-id="155ca-264">手勢框架</span><span class="sxs-lookup"><span data-stu-id="155ca-264">Gesture frame</span></span>
<span data-ttu-id="155ca-265">針對 HoloLens 上的手勢，手必須位於手勢框架內、手勢檢測攝影機可適當地查看的範圍、從鼻子到 waist，以及肩膀之間。</span><span class="sxs-lookup"><span data-stu-id="155ca-265">For gestures on HoloLens, the hand must be within a gesture frame, in a range that the gesture-sensing cameras can see appropriately,  from nose to waist and between the shoulders.</span></span> <span data-ttu-id="155ca-266">使用者必須在此辨識區域上進行訓練，以獲得動作的成功，並讓他們自己的舒適。</span><span class="sxs-lookup"><span data-stu-id="155ca-266">Users need to be trained on this area of recognition both for success of action and for their own comfort.</span></span> <span data-ttu-id="155ca-267">許多使用者一開始會假設手勢畫面格必須在其觀看的情況下，並保有 uncomfortably，以便進行互動。</span><span class="sxs-lookup"><span data-stu-id="155ca-267">Many users will initially assume that the gesture frame must be within their view through HoloLens, and hold their arms up uncomfortably in order to interact.</span></span> <span data-ttu-id="155ca-268">使用 HoloLens Clicker 時，不一定要將手放在手勢框架內。</span><span class="sxs-lookup"><span data-stu-id="155ca-268">When using the HoloLens Clicker, it's not necessary for hands to be within the gesture frame.</span></span>

<span data-ttu-id="155ca-269">尤其是連續手勢的情況下，使用者在移動全息型物件時，將其手移至手勢框架之外時，會有一些風險，例如，以及遺失其預期結果。</span><span class="sxs-lookup"><span data-stu-id="155ca-269">In the case of continuous gestures in particular, there is some risk of users moving their hands outside of the gesture frame while in mid-gesture when moving a holographic object, for example, and losing their intended outcome.</span></span>

<span data-ttu-id="155ca-270">您應該考量下列三個事項：</span><span class="sxs-lookup"><span data-stu-id="155ca-270">There are three things that you should consider:</span></span>

- <span data-ttu-id="155ca-271">手勢框架存在和大約界限的使用者教育。</span><span class="sxs-lookup"><span data-stu-id="155ca-271">User education on the gesture frame's existence and approximate boundaries.</span></span> <span data-ttu-id="155ca-272">這是在 HoloLens 安裝期間教授。</span><span class="sxs-lookup"><span data-stu-id="155ca-272">This is taught during HoloLens setup.</span></span>

- <span data-ttu-id="155ca-273">當使用者的手勢接近或中斷應用程式內的手勢框架界限時，通知使用者，表示遺失的手勢會導致不想要的結果。</span><span class="sxs-lookup"><span data-stu-id="155ca-273">Notifying users when their gestures are nearing or breaking the gesture frame boundaries within an application to the degree that a lost gesture leads to undesired outcomes.</span></span> <span data-ttu-id="155ca-274">研究已展示這類通知系統的主要品質。</span><span class="sxs-lookup"><span data-stu-id="155ca-274">Research has shown the key qualities of such a notification system.</span></span> <span data-ttu-id="155ca-275">HoloLens shell 會在中央游標上提供此類型通知（視覺效果）的良好範例，指出界限跨越的方向。</span><span class="sxs-lookup"><span data-stu-id="155ca-275">The HoloLens shell provides a good example of this type of notification--visual, on the central cursor, indicating the direction in which boundary crossing is taking place.</span></span>

- <span data-ttu-id="155ca-276">您應該將突破手勢框架界限的後果最小化。</span><span class="sxs-lookup"><span data-stu-id="155ca-276">Consequences of breaking the gesture frame boundaries should be minimized.</span></span> <span data-ttu-id="155ca-277">一般來說，這表示手勢的結果應該在界限停止，而不是反轉。</span><span class="sxs-lookup"><span data-stu-id="155ca-277">In general, this means that the outcome of a gesture should be stopped at the boundary, and not reversed.</span></span> <span data-ttu-id="155ca-278">比方說，如果使用者要在房間內移動一些全像的物件，則當軌跡框架被入侵時，移動應該會停止，而且不會傳回至起始點。</span><span class="sxs-lookup"><span data-stu-id="155ca-278">For example, if a user is moving some holographic object across a room, the movement should stop when the gesture frame is breached, and not returned to the starting point.</span></span> <span data-ttu-id="155ca-279">使用者可能會遇到一些挫折，但可能更快速地瞭解界限，而不必每次重新開機其完整的預期動作。</span><span class="sxs-lookup"><span data-stu-id="155ca-279">The user might experience some frustration, but might more quickly understand the boundaries, and not have to restart their full intended actions each time.</span></span>



## <a name="see-also"></a><span data-ttu-id="155ca-280">另請參閱</span><span class="sxs-lookup"><span data-stu-id="155ca-280">See also</span></span>
* [<span data-ttu-id="155ca-281">眼動式互動</span><span class="sxs-lookup"><span data-stu-id="155ca-281">Eye-based interaction</span></span>](eye-gaze-interaction.md)
* [<span data-ttu-id="155ca-282">HoloLens 2 的眼球追蹤</span><span class="sxs-lookup"><span data-stu-id="155ca-282">Eye tracking on HoloLens 2</span></span>](eye-tracking.md)
* [<span data-ttu-id="155ca-283">目光和停駐</span><span class="sxs-lookup"><span data-stu-id="155ca-283">Gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="155ca-284">手 - 直接操作</span><span class="sxs-lookup"><span data-stu-id="155ca-284">Hands - Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="155ca-285">手 - 手勢</span><span class="sxs-lookup"><span data-stu-id="155ca-285">Hands - Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="155ca-286">手 - 指向和行動</span><span class="sxs-lookup"><span data-stu-id="155ca-286">Hands - Point and commit</span></span>](point-and-commit.md)
* [<span data-ttu-id="155ca-287">本能互動</span><span class="sxs-lookup"><span data-stu-id="155ca-287">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="155ca-288">語音輸入</span><span class="sxs-lookup"><span data-stu-id="155ca-288">Voice input</span></span>](voice-input.md)

