---
title: 觀眾檢視
description: 將來自外部裝置的全像投影視覺化，作為在外部顯示器上示範混合實境體驗，或錄製混合實境體驗影片的方法。
author: chrisfromwork
ms.author: chriba
ms.date: 02/11/2019
ms.topic: article
ms.localizationpriority: high
keywords: 觀眾檢視, iPhone, iOS, iPad, OpenCV, 相機, ARKit, HoloLens, 混合實境, MixedRealityToolkit, 示範, 錄製
ms.openlocfilehash: 7b48315753ada0ae7a94abca5377a083ac659a34
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2020
ms.locfileid: "91696541"
---
# <a name="spectator-view-for-hololens-and-hololens-2"></a><span data-ttu-id="34410-104">HoloLens 和 HoloLens 2 的觀眾檢視</span><span class="sxs-lookup"><span data-stu-id="34410-104">Spectator View for HoloLens and HoloLens 2</span></span>

![Marker](images/SpecViewPhoneHero.jpg)

## <a name="overview"></a><span data-ttu-id="34410-106">概觀</span><span class="sxs-lookup"><span data-stu-id="34410-106">Overview</span></span>

<span data-ttu-id="34410-107">戴上 HoloLens 時，我們通常會忘記沒有穿戴裝置的人無法體驗我們所體驗的奧妙。</span><span class="sxs-lookup"><span data-stu-id="34410-107">When wearing a HoloLens, we often forget that a person who does not have it on is unable to experience the wonders that we can.</span></span> <span data-ttu-id="34410-108">觀眾檢視可以讓其他人在 2D 螢幕上看到 HoloLens 使用者在他們的世界中所看到的內容。</span><span class="sxs-lookup"><span data-stu-id="34410-108">Spectator View allows others to see on a 2D screen what a HoloLens user sees in their world.</span></span>
<span data-ttu-id="34410-109">觀眾檢視提供快速且實惠的方法，讓您使用行動裝置以 HD 錄製全像投影。</span><span class="sxs-lookup"><span data-stu-id="34410-109">Spectator View offers a fast and affordable approach to recording holograms in HD with mobile devices.</span></span> <span data-ttu-id="34410-110">它也提供透過攝影機的全像投影專業品質錄影。</span><span class="sxs-lookup"><span data-stu-id="34410-110">It also offers a professional quality recording of holograms with video cameras.</span></span>

## <a name="key-resources"></a><span data-ttu-id="34410-111">主要資源</span><span class="sxs-lookup"><span data-stu-id="34410-111">Key Resources</span></span>

* [<span data-ttu-id="34410-112">**GitHub 上的觀眾檢視**</span><span class="sxs-lookup"><span data-stu-id="34410-112">**Spectator View on GitHub**</span></span>](https://github.com/microsoft/MixedReality-SpectatorView)
* [<span data-ttu-id="34410-113">**觀眾檢視文件**</span><span class="sxs-lookup"><span data-stu-id="34410-113">**Spectator View Documentation**</span></span>](https://microsoft.github.io/MixedReality-SpectatorView/README.html)
* [<span data-ttu-id="34410-114">**觀眾檢視範例**</span><span class="sxs-lookup"><span data-stu-id="34410-114">**Spectator View Samples**</span></span>](https://github.com/microsoft/MixedReality-SpectatorView/tree/master/samples)

## <a name="use-cases"></a><span data-ttu-id="34410-115">使用案例</span><span class="sxs-lookup"><span data-stu-id="34410-115">Use Cases</span></span>
* <span data-ttu-id="34410-116">您可以使用 iPhone 或 Android 裝置錄製混合實境體驗。</span><span class="sxs-lookup"><span data-stu-id="34410-116">You can record a mixed reality experience using an iPhone or Android device.</span></span> <span data-ttu-id="34410-117">以 Full HD 錄製，對全像投影甚至是陰影套用消除鋸齒功能。</span><span class="sxs-lookup"><span data-stu-id="34410-117">Record in full HD and apply anti-aliasing to holograms and even shadows.</span></span> <span data-ttu-id="34410-118">這是擷取全像投影影片的符合成本效益且快速的方式。</span><span class="sxs-lookup"><span data-stu-id="34410-118">It is a cost-effective and quick way to capture video of holograms.</span></span>
* <span data-ttu-id="34410-119">直接從您的 iPhone 或 iPad 將即時混合實境體驗串流至 Apple TV，沒有延遲！</span><span class="sxs-lookup"><span data-stu-id="34410-119">Stream live mixed reality experiences to an Apple TV directly from your iPhone or iPad, lag-free!</span></span>
* <span data-ttu-id="34410-120">與來賓分享體驗：讓非 HoloLens 使用者直接從他們的手機或平板電腦體驗全像投影。</span><span class="sxs-lookup"><span data-stu-id="34410-120">Share the experience with guests: Let non-HoloLens users experience holograms directly from their phones or tablets.</span></span>

## <a name="current-features"></a><span data-ttu-id="34410-121">目前的功能</span><span class="sxs-lookup"><span data-stu-id="34410-121">Current Features</span></span>

* <span data-ttu-id="34410-122">全像投影的空間同步處理，因此每個人都能在完全相同的位置看到全像投影。</span><span class="sxs-lookup"><span data-stu-id="34410-122">Spatial synchronization of Holograms, so everyone sees holograms in the exact same place.</span></span>
* <span data-ttu-id="34410-123">支援 iOS (已啟用 ARKit 的裝置) 和 Android (已啟用 ARCore 的裝置)。</span><span class="sxs-lookup"><span data-stu-id="34410-123">iOS (ARKit-enabled devices) and Android (ARCore-enabled devices) support.</span></span>
<span data-ttu-id="34410-124">多個 iOS 來賓。</span><span class="sxs-lookup"><span data-stu-id="34410-124">Multiple iOS guests.</span></span>
<span data-ttu-id="34410-125">影片錄製 + 全像投影 + 環境音效 + 全像投影音效。</span><span class="sxs-lookup"><span data-stu-id="34410-125">Recording of video + holograms + ambient sound + hologram sound.</span></span>
<span data-ttu-id="34410-126">共用工作表，讓您可以儲存影片、透過電子郵件傳送，或與其他支援的應用程式共用。</span><span class="sxs-lookup"><span data-stu-id="34410-126">Share sheet so you can save video, email it, or share with other supporting apps.</span></span>

<span data-ttu-id="34410-127">![標記](images/SpecViewPhoneDemo.jpg)
![標記](images/hololensspectatorview-500px.jpg) ![標記](images/spectatorview-300px.png)</span><span class="sxs-lookup"><span data-stu-id="34410-127">![Marker](images/SpecViewPhoneDemo.jpg)
![Marker](images/hololensspectatorview-500px.jpg) ![Marker](images/spectatorview-300px.png)</span></span>

<span data-ttu-id="34410-128">下表顯示不同的觀眾檢視功能及其功能。</span><span class="sxs-lookup"><span data-stu-id="34410-128">The following table shows different Spectator View functionality and their capabilities.</span></span> <span data-ttu-id="34410-129">選擇最適合您影片錄製需求的選項：</span><span class="sxs-lookup"><span data-stu-id="34410-129">Choose the option that best fits your video recording needs:</span></span>

|      <span data-ttu-id="34410-130">功能</span><span class="sxs-lookup"><span data-stu-id="34410-130">Functionality</span></span>                                | <span data-ttu-id="34410-131">行動</span><span class="sxs-lookup"><span data-stu-id="34410-131">Mobile</span></span>                  |                    <span data-ttu-id="34410-132">攝影機</span><span class="sxs-lookup"><span data-stu-id="34410-132">Video Camera</span></span>              |
|--------------------------------------|:-----------------------:|:-------------------------------------------:|
| <span data-ttu-id="34410-133">HD 品質</span><span class="sxs-lookup"><span data-stu-id="34410-133">HD quality</span></span>                           |         <span data-ttu-id="34410-134">Full HD</span><span class="sxs-lookup"><span data-stu-id="34410-134">Full HD</span></span>         |        <span data-ttu-id="34410-135">專業品質攝影 (由攝影機決定)</span><span class="sxs-lookup"><span data-stu-id="34410-135">Professional quality filming (as determined by video camera)</span></span>      |
| <span data-ttu-id="34410-136">簡易相機移動</span><span class="sxs-lookup"><span data-stu-id="34410-136">Easy camera movement</span></span>                 |            <span data-ttu-id="34410-137">✔</span><span class="sxs-lookup"><span data-stu-id="34410-137">✔</span></span>            |                      <span data-ttu-id="34410-138">✔</span><span class="sxs-lookup"><span data-stu-id="34410-138">✔</span></span>                      |
| <span data-ttu-id="34410-139">第三人稱視角</span><span class="sxs-lookup"><span data-stu-id="34410-139">Third-person view</span></span>                    |            <span data-ttu-id="34410-140">✔</span><span class="sxs-lookup"><span data-stu-id="34410-140">✔</span></span>            |                      <span data-ttu-id="34410-141">✔</span><span class="sxs-lookup"><span data-stu-id="34410-141">✔</span></span>                      |
| <span data-ttu-id="34410-142">可以串流至螢幕</span><span class="sxs-lookup"><span data-stu-id="34410-142">Can be streamed to screens</span></span>           |            <span data-ttu-id="34410-143">✔</span><span class="sxs-lookup"><span data-stu-id="34410-143">✔</span></span>            |                      <span data-ttu-id="34410-144">✔</span><span class="sxs-lookup"><span data-stu-id="34410-144">✔</span></span>                      |
| <span data-ttu-id="34410-145">可攜式</span><span class="sxs-lookup"><span data-stu-id="34410-145">Portable</span></span>                             |            <span data-ttu-id="34410-146">✔</span><span class="sxs-lookup"><span data-stu-id="34410-146">✔</span></span>            |                                             |
| <span data-ttu-id="34410-147">無線</span><span class="sxs-lookup"><span data-stu-id="34410-147">Wireless</span></span>                             |            <span data-ttu-id="34410-148">✔</span><span class="sxs-lookup"><span data-stu-id="34410-148">✔</span></span>            |                                             |
| <span data-ttu-id="34410-149">其他必要硬體</span><span class="sxs-lookup"><span data-stu-id="34410-149">Additional required hardware</span></span>         |     <span data-ttu-id="34410-150">Android 手機、iPhone</span><span class="sxs-lookup"><span data-stu-id="34410-150">Android phone, iPhone</span></span>    | <span data-ttu-id="34410-151">HoloLens + Rig + 三腳架 + 攝影機 + PC + Unity</span><span class="sxs-lookup"><span data-stu-id="34410-151">HoloLens + Rig + Tripod + Video Camera + PC + Unity</span></span> |
| <span data-ttu-id="34410-152">硬體投資</span><span class="sxs-lookup"><span data-stu-id="34410-152">Hardware investment</span></span>                  |           <span data-ttu-id="34410-153">低度</span><span class="sxs-lookup"><span data-stu-id="34410-153">Low</span></span>            |                     <span data-ttu-id="34410-154">高</span><span class="sxs-lookup"><span data-stu-id="34410-154">High</span></span>                    |
| <span data-ttu-id="34410-155">跨平台</span><span class="sxs-lookup"><span data-stu-id="34410-155">Cross-platform</span></span>                       |           <span data-ttu-id="34410-156">Android、iOS</span><span class="sxs-lookup"><span data-stu-id="34410-156">Android, iOS</span></span>   |                                             |
| <span data-ttu-id="34410-157">同步處理的內容</span><span class="sxs-lookup"><span data-stu-id="34410-157">Synchronized content</span></span>                 |            <span data-ttu-id="34410-158">✔</span><span class="sxs-lookup"><span data-stu-id="34410-158">✔</span></span>            |                      <span data-ttu-id="34410-159">✔</span><span class="sxs-lookup"><span data-stu-id="34410-159">✔</span></span>                      |
| <span data-ttu-id="34410-160">執行階段安裝持續時間</span><span class="sxs-lookup"><span data-stu-id="34410-160">Runtime setup duration</span></span>               |         <span data-ttu-id="34410-161">立即</span><span class="sxs-lookup"><span data-stu-id="34410-161">Instant</span></span>          |                     <span data-ttu-id="34410-162">緩慢</span><span class="sxs-lookup"><span data-stu-id="34410-162">Slow</span></span>                    |
## <a name="see-also"></a><span data-ttu-id="34410-163">另請參閱</span><span class="sxs-lookup"><span data-stu-id="34410-163">See also</span></span>

* [<span data-ttu-id="34410-164">混合實境擷取</span><span class="sxs-lookup"><span data-stu-id="34410-164">Mixed reality capture</span></span>](../../mixed-reality-capture.md) 
* [<span data-ttu-id="34410-165">適用於開發人員的混合實境擷取</span><span class="sxs-lookup"><span data-stu-id="34410-165">Mixed reality capture for developers</span></span>](mixed-reality-capture-for-developers.md)
* [<span data-ttu-id="34410-166">混合實境中的共用體驗</span><span class="sxs-lookup"><span data-stu-id="34410-166">Shared experiences in mixed reality</span></span>](shared-experiences-in-mixed-reality.md)
