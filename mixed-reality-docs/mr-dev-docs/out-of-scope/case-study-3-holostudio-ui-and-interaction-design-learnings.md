---
title: 案例研究-3 HoloStudio UI 和互動設計學習
description: 了解 HoloStudio UI 和互動設計
author: rwinj
ms.author: marcghal
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens、HoloStudio、Windows Mixed Reality
ms.openlocfilehash: 55fc9cea93582612abb5e0f8955deb5629da3093
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2020
ms.locfileid: "91681213"
---
# <a name="case-study---3-holostudio-ui-and-interaction-design-learnings"></a><span data-ttu-id="9ef61-104">案例研究-3 HoloStudio UI 和互動設計學習</span><span class="sxs-lookup"><span data-stu-id="9ef61-104">Case study - 3 HoloStudio UI and interaction design learnings</span></span>

<span data-ttu-id="9ef61-105">[HoloStudio](https://www.youtube.com/watch?v=BRIJG0x_We8) 是適用于 HoloLens 的第一個 Microsoft 應用程式。</span><span class="sxs-lookup"><span data-stu-id="9ef61-105">[HoloStudio](https://www.youtube.com/watch?v=BRIJG0x_We8) was one of the first Microsoft apps for HoloLens.</span></span> <span data-ttu-id="9ef61-106">因此，我們必須建立新的 3D UI 和互動設計最佳作法。</span><span class="sxs-lookup"><span data-stu-id="9ef61-106">Because of this, we had to create new best practices for 3D UI and interaction design.</span></span> <span data-ttu-id="9ef61-107">我們透過許多使用者測試、原型設計和試用和錯誤來完成這項工作。</span><span class="sxs-lookup"><span data-stu-id="9ef61-107">We did this through a lot of user testing, prototyping, and trial and error.</span></span>

<span data-ttu-id="9ef61-108">我們知道，並非每個人都具有可進行這類研究的資源，因此我們的 Marcus Ghaly 會分享我們在開發 HoloStudio 時所學到的三件事。</span><span class="sxs-lookup"><span data-stu-id="9ef61-108">We know that not everyone has the resources at their disposal to do this type of research, so we had our Sr. Holographic Designer, Marcus Ghaly, share three things we learned during the development of HoloStudio about UI and interaction design for HoloLens apps.</span></span>

## <a name="watch-the-video"></a><span data-ttu-id="9ef61-109">觀賞影片</span><span class="sxs-lookup"><span data-stu-id="9ef61-109">Watch the video</span></span>

>[!VIDEO https://www.youtube.com/embed/sX6yKHmN1qM]

## <a name="problem-1-people-didnt-want-to-move-around-their-creations"></a><span data-ttu-id="9ef61-110">問題 #1：人們不希望四處移動</span><span class="sxs-lookup"><span data-stu-id="9ef61-110">Problem #1: People didn't want to move around their creations</span></span>

<span data-ttu-id="9ef61-111">我們最初將 HoloStudio 中的工作臺設計為矩形，就像您在真實世界中所找到的一樣。</span><span class="sxs-lookup"><span data-stu-id="9ef61-111">We originally designed the workbench in HoloStudio as a rectangle, much like you'd find in the real world.</span></span> <span data-ttu-id="9ef61-112">問題在於，人們有經驗的存留期，讓他們在離開辦公桌或在電腦前方工作時仍能保持不變，因此他們不會四處移動，也不會從所有的邊緣探索其3D 建立。</span><span class="sxs-lookup"><span data-stu-id="9ef61-112">The problem is that people have a lifetime of experience that tells them to stay still when they're sitting at a desk or working in front of a computer, so they weren't moving around the workbench and exploring their 3D creation from all sides.</span></span>

![HoloStudio 中工作臺的矩形設計 dissuaded 使用者四處移動並查看其在所有邊的建立。](images/rectangular-workbench-500px.jpg)

<span data-ttu-id="9ef61-114">我們的見解是讓工作臺輪回，因此沒有任何「正面」或明確的地方。</span><span class="sxs-lookup"><span data-stu-id="9ef61-114">We had the insight to make the workbench round, so that there was no "front" or clear place that you were supposed to stand.</span></span> <span data-ttu-id="9ef61-115">經過測試後，突然有人開始不斷地四處探索自己的作品。</span><span class="sxs-lookup"><span data-stu-id="9ef61-115">When we tested this, suddenly people started moving around and exploring their creations on their own.</span></span>

![迴圈工作臺設計鼓勵使用者在建立過程中逐步解說。](images/circular-workbench-500px.jpg)

<span data-ttu-id="9ef61-117">**我們學到了什麼**</span><span class="sxs-lookup"><span data-stu-id="9ef61-117">**What we learned**</span></span>

<span data-ttu-id="9ef61-118">請一律考慮使用者的熟悉功能。</span><span class="sxs-lookup"><span data-stu-id="9ef61-118">Always be thinking about what's comfortable for the user.</span></span> <span data-ttu-id="9ef61-119">利用其實體空間是 HoloLens 的絕佳功能，而您無法使用其他裝置來執行這項功能。</span><span class="sxs-lookup"><span data-stu-id="9ef61-119">Taking advantage of their physical space is a cool feature of HoloLens and something you can't do with other devices.</span></span>

## <a name="problem-2-modal-dialogs-are-sometimes-out-of-the-holographic-frame"></a><span data-ttu-id="9ef61-120">問題 #2：強制回應對話方塊有時候不在全像攝影框架中</span><span class="sxs-lookup"><span data-stu-id="9ef61-120">Problem #2: Modal dialogs are sometimes out of the holographic frame</span></span>

<span data-ttu-id="9ef61-121">有時，您的使用者可能會在您的應用程式中查看需要注意的不同方向。</span><span class="sxs-lookup"><span data-stu-id="9ef61-121">Sometimes, your user may be looking in a different direction from something that needs their attention in your app.</span></span> <span data-ttu-id="9ef61-122">在電腦上，您可以直接快顯對話方塊，但如果您在3D 環境中的某個人面對這種情況，就可能覺得對話正在進行。</span><span class="sxs-lookup"><span data-stu-id="9ef61-122">On a PC, you can just pop up a dialog, but if you do this in someone's face in a 3D environment, it can feel like the dialog is getting in their way.</span></span> <span data-ttu-id="9ef61-123">您需要它們來讀取訊息，但其直覺是嘗試離開它。</span><span class="sxs-lookup"><span data-stu-id="9ef61-123">You need them to read the message, but their instinct is to try to get away from it.</span></span> <span data-ttu-id="9ef61-124">如果您想要玩遊戲，但在設計工作的工具中，這種反應就很好用，因為它不是理想的做法。</span><span class="sxs-lookup"><span data-stu-id="9ef61-124">This reaction is great if you're playing a game, but in a tool designed for work, it's less than ideal.</span></span>

<span data-ttu-id="9ef61-125">在嘗試幾個不同的專案之後，我們終於針對對話使用「思考的反升」系統，並新增使用者可遵循的 tendrils，讓使用者在應用程式中需要注意。</span><span class="sxs-lookup"><span data-stu-id="9ef61-125">After trying a few different things, we finally settled on using a "thought bubble" system for our dialogs and added tendrils that users can follow to where their attention is needed in our application.</span></span> <span data-ttu-id="9ef61-126">我們也做了 tendrils 脈衝，暗示了方向性的意義，讓使用者知道要前往哪裡。</span><span class="sxs-lookup"><span data-stu-id="9ef61-126">We also made the tendrils pulse, which implied a sense of directionality so that users knew where to go.</span></span>

![「思考的反升」系統包含可提供某種方向的閃爍 tendrils，讓使用者在應用程式中需要注意的地方。](images/thought-bubble-500px.jpg)

<span data-ttu-id="9ef61-128">**我們學到了什麼**</span><span class="sxs-lookup"><span data-stu-id="9ef61-128">**What we learned**</span></span>

<span data-ttu-id="9ef61-129">3D 會更難向使用者發出警告，以提醒使用者他們必須注意的事項。</span><span class="sxs-lookup"><span data-stu-id="9ef61-129">It's much harder in 3D to alert users to things they need to pay attention to.</span></span> <span data-ttu-id="9ef61-130">使用「 [空間音效](../design/spatial-sound.md)」、「光線光線」或「想像」等注意控制器，可以讓使用者在需要的位置。</span><span class="sxs-lookup"><span data-stu-id="9ef61-130">Using attention directors such as [spatial sound](../design/spatial-sound.md), light rays, or thought bubbles, can lead users to where they need to be.</span></span>

## <a name="problem-3-sometimes-ui-can-get-blocked-by-other-holograms"></a><span data-ttu-id="9ef61-131">問題 #3：有時候 UI 可能會被其他全息</span><span class="sxs-lookup"><span data-stu-id="9ef61-131">Problem #3: Sometimes UI can get blocked by other holograms</span></span>

<span data-ttu-id="9ef61-132">有時候，使用者想要與一張全像和其相關聯的 UI 控制項進行互動，但因為有其他的全息圖，所以會被封鎖而無法查看。</span><span class="sxs-lookup"><span data-stu-id="9ef61-132">There are times when a user wants to interact with a hologram and its associated UI controls, but they are blocked from view because another hologram is in front of them.</span></span> <span data-ttu-id="9ef61-133">當我們開發 HoloStudio 時，我們使用了試用版和錯誤來解決這個問題。</span><span class="sxs-lookup"><span data-stu-id="9ef61-133">While we were developing HoloStudio, we used trial and error to come to a solution for this.</span></span>

![如果有另一個全息圖與使用者戴上 HoloLens，則會封鎖與全像影像相關聯的 UI 控制項。](images/ui-blocked-500px.jpg)

<span data-ttu-id="9ef61-135">我們嘗試將 UI 控制項移到更接近使用者的位置，使其無法被封鎖，但發現它不適合用戶查看靠近您的控制項，同時查看離離的全像位置。</span><span class="sxs-lookup"><span data-stu-id="9ef61-135">We tried moving the UI control closer to the user so it couldn't get blocked, but found that it wasn't comfortable for the user to look at a control that was near to you while simultaneously looking at a hologram that was far away.</span></span> <span data-ttu-id="9ef61-136">但是，如果我們將最接近的全像全像投影的控制項移至使用者，他們就認為它是從它所影響的全像是卸離的。</span><span class="sxs-lookup"><span data-stu-id="9ef61-136">If, however, we moved the control in front of the closest hologram to the user, they felt like it was detached from the hologram it should be affecting.</span></span>

<span data-ttu-id="9ef61-137">最後，我們會將 UI 控制項的時間加上一次，並將它與使用者建立關聯的全像是相同的距離，讓它們都覺得有連線。</span><span class="sxs-lookup"><span data-stu-id="9ef61-137">We finally ended up ghosting the UI control, and put it at the same distance from the user as the hologram it's associated with, so they both feel connected.</span></span> <span data-ttu-id="9ef61-138">這可讓使用者與控制項互動，即使它已遮蔽也一樣。</span><span class="sxs-lookup"><span data-stu-id="9ef61-138">This allows the user to interact with the control even though it's been obscured.</span></span>

![解決方案：我們將 UI 控制項加上幻影，這兩者都允許與控制項互動，讓它能夠連線到它所影響的全像影像。](images/ghosting-ui-500px.jpg)

<span data-ttu-id="9ef61-140">**我們學到了什麼**</span><span class="sxs-lookup"><span data-stu-id="9ef61-140">**What we learned**</span></span>

<span data-ttu-id="9ef61-141">使用者必須能夠輕鬆地存取 UI 控制項（即使已被封鎖），因此請找出方法，以確保使用者可以完成他們的工作，無論是在真實世界的哪一處。</span><span class="sxs-lookup"><span data-stu-id="9ef61-141">Users need to be able to easily access UI controls even if they've been blocked, so figure out methods to ensure that users can complete their tasks no matter where their holograms are in the real world.</span></span>

## <a name="about-the-author"></a><span data-ttu-id="9ef61-142">關於作者</span><span class="sxs-lookup"><span data-stu-id="9ef61-142">About the author</span></span>

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Marcus Ghaly" width="60" height="60" src="images/marcus-ghaly-200px.jpg"></td>
<td style="border-style: none"><span data-ttu-id="9ef61-143"><b>Marcus Ghaly</b></span><span class="sxs-lookup"><span data-stu-id="9ef61-143"><b>Marcus Ghaly</b></span></span><br><span data-ttu-id="9ef61-144">Sr-iov 設計工具 @Microsoft</span><span class="sxs-lookup"><span data-stu-id="9ef61-144">Sr. Holographic Designer @Microsoft</span></span></td>
</tr>
</table>

## <a name="see-also"></a><span data-ttu-id="9ef61-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9ef61-145">See also</span></span>
* [<span data-ttu-id="9ef61-146">本能互動</span><span class="sxs-lookup"><span data-stu-id="9ef61-146">Instinctual interactions</span></span>](../design/interaction-fundamentals.md)
