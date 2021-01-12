---
title: 觀眾檢視
description: 將來自外部裝置的全像投影視覺化，以顯示或錄製外部顯示器上的混合實境體驗。
author: chrisfromwork
ms.author: chriba
ms.date: 02/11/2019
ms.topic: article
ms.localizationpriority: high
keywords: 觀眾檢視, iPhone, iOS, iPad, OpenCV, 相機, ARKit, HoloLens, 混合實境, MixedRealityToolkit, 示範, 錄製
ms.openlocfilehash: 1f61d2094ec2762ab22576d2eac85ed6bf81d5c7
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2021
ms.locfileid: "98008608"
---
# <a name="spectator-view-for-hololens-and-hololens-2"></a><span data-ttu-id="a9d8b-104">HoloLens 和 HoloLens 2 的觀眾檢視</span><span class="sxs-lookup"><span data-stu-id="a9d8b-104">Spectator View for HoloLens and HoloLens 2</span></span>

![Marker](images/SpecViewPhoneHero.jpg)

<span data-ttu-id="a9d8b-106">當您穿戴 HoloLens 時，很容易忘記沒有 HoloLens 的人員無法體驗您所看到的相同奇觀。</span><span class="sxs-lookup"><span data-stu-id="a9d8b-106">When you're wearing a HoloLens, it's easy to forget a person without one can't experience the same wonders you're seeing.</span></span> <span data-ttu-id="a9d8b-107">「觀眾檢視」可讓其他人看到 HoloLens 使用者在 2D 螢幕上看到的內容。</span><span class="sxs-lookup"><span data-stu-id="a9d8b-107">Spectator View lets others see what a HoloLens user sees on a 2D screen.</span></span> <span data-ttu-id="a9d8b-108">這也是一種快速且經濟實惠的方法，可使用行動裝置來錄製 HD 中的全像投影，並透過攝影機取得高品質的全像投影錄影。</span><span class="sxs-lookup"><span data-stu-id="a9d8b-108">It's also a fast and affordable approach to recording holograms in HD with mobile devices and getting great quality recordings of holograms with video cameras.</span></span>

## <a name="key-resources"></a><span data-ttu-id="a9d8b-109">主要資源</span><span class="sxs-lookup"><span data-stu-id="a9d8b-109">Key Resources</span></span>

* [<span data-ttu-id="a9d8b-110">**GitHub 上的觀眾檢視**</span><span class="sxs-lookup"><span data-stu-id="a9d8b-110">**Spectator View on GitHub**</span></span>](https://github.com/microsoft/MixedReality-SpectatorView)
* [<span data-ttu-id="a9d8b-111">**觀眾檢視文件**</span><span class="sxs-lookup"><span data-stu-id="a9d8b-111">**Spectator View Documentation**</span></span>](https://microsoft.github.io/MixedReality-SpectatorView/README.html)
* [<span data-ttu-id="a9d8b-112">**觀眾檢視範例**</span><span class="sxs-lookup"><span data-stu-id="a9d8b-112">**Spectator View Samples**</span></span>](https://github.com/microsoft/MixedReality-SpectatorView/tree/master/samples)

## <a name="use-cases"></a><span data-ttu-id="a9d8b-113">使用案例</span><span class="sxs-lookup"><span data-stu-id="a9d8b-113">Use Cases</span></span>

* <span data-ttu-id="a9d8b-114">您可以使用 iPhone 或 Android 裝置錄製混合實境體驗。</span><span class="sxs-lookup"><span data-stu-id="a9d8b-114">You can record a mixed reality experience using an iPhone or Android device.</span></span> <span data-ttu-id="a9d8b-115">以 Full HD 錄製並將消除鋸齒功能套用到全像投影和陰影，以符合成本效益且快速的方式來擷取全像投影的影片。</span><span class="sxs-lookup"><span data-stu-id="a9d8b-115">Record in full HD and apply anti-aliasing to holograms and shadow for a cost-effective and quick way to capture video of holograms.</span></span>
* <span data-ttu-id="a9d8b-116">直接從您的 iPhone 或 iPad 將即時混合實境體驗串流至 Apple TV，沒有延遲！</span><span class="sxs-lookup"><span data-stu-id="a9d8b-116">Stream live mixed reality experiences to an Apple TV directly from your iPhone or iPad, lag-free!</span></span>
* <span data-ttu-id="a9d8b-117">與來賓分享體驗：讓非 HoloLens 使用者直接從他們的手機或平板電腦體驗全像投影。</span><span class="sxs-lookup"><span data-stu-id="a9d8b-117">Share the experience with guests: Let non-HoloLens users experience holograms directly from their phones or tablets.</span></span>

## <a name="current-features"></a><span data-ttu-id="a9d8b-118">目前的功能</span><span class="sxs-lookup"><span data-stu-id="a9d8b-118">Current Features</span></span>

* <span data-ttu-id="a9d8b-119">全像投影的空間同步處理，因此每個人都能在完全相同的位置看到全像投影。</span><span class="sxs-lookup"><span data-stu-id="a9d8b-119">Spatial synchronization of Holograms, so everyone sees holograms in the exact same place.</span></span>
* <span data-ttu-id="a9d8b-120">支援 iOS (已啟用 ARKit 的裝置) 和 Android (已啟用 ARCore 的裝置)。</span><span class="sxs-lookup"><span data-stu-id="a9d8b-120">iOS (ARKit-enabled devices) and Android (ARCore-enabled devices) support.</span></span>
<span data-ttu-id="a9d8b-121">多個 iOS 來賓。</span><span class="sxs-lookup"><span data-stu-id="a9d8b-121">Multiple iOS guests.</span></span>
<span data-ttu-id="a9d8b-122">影片錄製 + 全像投影 + 環境音效 + 全像投影音效。</span><span class="sxs-lookup"><span data-stu-id="a9d8b-122">Recording of video + holograms + ambient sound + hologram sound.</span></span>
<span data-ttu-id="a9d8b-123">共用工作表，讓您可以儲存影片、透過電子郵件傳送，或與其他支援的應用程式共用。</span><span class="sxs-lookup"><span data-stu-id="a9d8b-123">Share sheet so you can save video, email it, or share with other supporting apps.</span></span>

<span data-ttu-id="a9d8b-124">![標記](images/SpecViewPhoneDemo.jpg)
![標記](images/hololensspectatorview-500px.jpg) ![標記](images/spectatorview-300px.png)</span><span class="sxs-lookup"><span data-stu-id="a9d8b-124">![Marker](images/SpecViewPhoneDemo.jpg)
![Marker](images/hololensspectatorview-500px.jpg) ![Marker](images/spectatorview-300px.png)</span></span>

<span data-ttu-id="a9d8b-125">下表顯示不同的觀眾檢視功能及其功能。</span><span class="sxs-lookup"><span data-stu-id="a9d8b-125">The following table shows different Spectator View functionality and their capabilities.</span></span> <span data-ttu-id="a9d8b-126">選擇最適合您影片錄製需求的選項：</span><span class="sxs-lookup"><span data-stu-id="a9d8b-126">Choose the option that best fits your video recording needs:</span></span>

|      <span data-ttu-id="a9d8b-127">功能</span><span class="sxs-lookup"><span data-stu-id="a9d8b-127">Functionality</span></span>                                | <span data-ttu-id="a9d8b-128">行動</span><span class="sxs-lookup"><span data-stu-id="a9d8b-128">Mobile</span></span>                  |                    <span data-ttu-id="a9d8b-129">攝影機</span><span class="sxs-lookup"><span data-stu-id="a9d8b-129">Video Camera</span></span>              |
|--------------------------------------|:-----------------------:|:-------------------------------------------:|
| <span data-ttu-id="a9d8b-130">HD 品質</span><span class="sxs-lookup"><span data-stu-id="a9d8b-130">HD quality</span></span>                           |         <span data-ttu-id="a9d8b-131">Full HD</span><span class="sxs-lookup"><span data-stu-id="a9d8b-131">Full HD</span></span>         |        <span data-ttu-id="a9d8b-132">專業品質攝影 (由攝影機決定)</span><span class="sxs-lookup"><span data-stu-id="a9d8b-132">Professional quality filming (as determined by video camera)</span></span>      |
| <span data-ttu-id="a9d8b-133">簡易相機移動</span><span class="sxs-lookup"><span data-stu-id="a9d8b-133">Easy camera movement</span></span>                 |            <span data-ttu-id="a9d8b-134">✔</span><span class="sxs-lookup"><span data-stu-id="a9d8b-134">✔</span></span>            |                      <span data-ttu-id="a9d8b-135">✔</span><span class="sxs-lookup"><span data-stu-id="a9d8b-135">✔</span></span>                      |
| <span data-ttu-id="a9d8b-136">第三人稱視角</span><span class="sxs-lookup"><span data-stu-id="a9d8b-136">Third-person view</span></span>                    |            <span data-ttu-id="a9d8b-137">✔</span><span class="sxs-lookup"><span data-stu-id="a9d8b-137">✔</span></span>            |                      <span data-ttu-id="a9d8b-138">✔</span><span class="sxs-lookup"><span data-stu-id="a9d8b-138">✔</span></span>                      |
| <span data-ttu-id="a9d8b-139">可以串流至螢幕</span><span class="sxs-lookup"><span data-stu-id="a9d8b-139">Can be streamed to screens</span></span>           |            <span data-ttu-id="a9d8b-140">✔</span><span class="sxs-lookup"><span data-stu-id="a9d8b-140">✔</span></span>            |                      <span data-ttu-id="a9d8b-141">✔</span><span class="sxs-lookup"><span data-stu-id="a9d8b-141">✔</span></span>                      |
| <span data-ttu-id="a9d8b-142">可攜式</span><span class="sxs-lookup"><span data-stu-id="a9d8b-142">Portable</span></span>                             |            <span data-ttu-id="a9d8b-143">✔</span><span class="sxs-lookup"><span data-stu-id="a9d8b-143">✔</span></span>            |                                             |
| <span data-ttu-id="a9d8b-144">無線</span><span class="sxs-lookup"><span data-stu-id="a9d8b-144">Wireless</span></span>                             |            <span data-ttu-id="a9d8b-145">✔</span><span class="sxs-lookup"><span data-stu-id="a9d8b-145">✔</span></span>            |                                             |
| <span data-ttu-id="a9d8b-146">其他必要硬體</span><span class="sxs-lookup"><span data-stu-id="a9d8b-146">Additional required hardware</span></span>         |     <span data-ttu-id="a9d8b-147">Android 手機、iPhone</span><span class="sxs-lookup"><span data-stu-id="a9d8b-147">Android phone, iPhone</span></span>    | <span data-ttu-id="a9d8b-148">HoloLens + Rig + 三腳架 + 攝影機 + PC + Unity</span><span class="sxs-lookup"><span data-stu-id="a9d8b-148">HoloLens + Rig + Tripod + Video Camera + PC + Unity</span></span> |
| <span data-ttu-id="a9d8b-149">硬體投資</span><span class="sxs-lookup"><span data-stu-id="a9d8b-149">Hardware investment</span></span>                  |           <span data-ttu-id="a9d8b-150">低度</span><span class="sxs-lookup"><span data-stu-id="a9d8b-150">Low</span></span>            |                     <span data-ttu-id="a9d8b-151">高</span><span class="sxs-lookup"><span data-stu-id="a9d8b-151">High</span></span>                    |
| <span data-ttu-id="a9d8b-152">跨平台</span><span class="sxs-lookup"><span data-stu-id="a9d8b-152">Cross-platform</span></span>                       |           <span data-ttu-id="a9d8b-153">Android、iOS</span><span class="sxs-lookup"><span data-stu-id="a9d8b-153">Android, iOS</span></span>   |                                             |
| <span data-ttu-id="a9d8b-154">同步處理的內容</span><span class="sxs-lookup"><span data-stu-id="a9d8b-154">Synchronized content</span></span>                 |            <span data-ttu-id="a9d8b-155">✔</span><span class="sxs-lookup"><span data-stu-id="a9d8b-155">✔</span></span>            |                      <span data-ttu-id="a9d8b-156">✔</span><span class="sxs-lookup"><span data-stu-id="a9d8b-156">✔</span></span>                      |
| <span data-ttu-id="a9d8b-157">執行階段安裝持續時間</span><span class="sxs-lookup"><span data-stu-id="a9d8b-157">Runtime setup duration</span></span>               |         <span data-ttu-id="a9d8b-158">立即</span><span class="sxs-lookup"><span data-stu-id="a9d8b-158">Instant</span></span>          |                     <span data-ttu-id="a9d8b-159">緩慢</span><span class="sxs-lookup"><span data-stu-id="a9d8b-159">Slow</span></span>                    |
## <a name="see-also"></a><span data-ttu-id="a9d8b-160">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a9d8b-160">See also</span></span>

* [<span data-ttu-id="a9d8b-161">混合實境擷取</span><span class="sxs-lookup"><span data-stu-id="a9d8b-161">Mixed reality capture</span></span>](../../mixed-reality-capture.md) 
* [<span data-ttu-id="a9d8b-162">適用於開發人員的混合實境擷取</span><span class="sxs-lookup"><span data-stu-id="a9d8b-162">Mixed reality capture for developers</span></span>](mixed-reality-capture-for-developers.md)
* [<span data-ttu-id="a9d8b-163">混合實境中的共用體驗</span><span class="sxs-lookup"><span data-stu-id="a9d8b-163">Shared experiences in mixed reality</span></span>](shared-experiences-in-mixed-reality.md)
