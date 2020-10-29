---
title: 案例研究-Lowe 廚房的課程
description: HoloLens 團隊想要分享衍生自 Lowe HoloLens 專案的一些最佳作法。
author: brandonbray
ms.author: kevincol
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality、Lowe、HoloLens、廚房、個案研究
ms.openlocfilehash: a6bd7a09f77fb71dc23dc640525ff250abac8f12
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2020
ms.locfileid: "91681140"
---
# <a name="case-study---lessons-from-the-lowes-kitchen"></a><span data-ttu-id="8e244-104">案例研究-Lowe 廚房的課程</span><span class="sxs-lookup"><span data-stu-id="8e244-104">Case study - Lessons from the Lowe's kitchen</span></span>

<span data-ttu-id="8e244-105">HoloLens 團隊想要分享衍生自 Lowe HoloLens 專案的一些最佳作法。</span><span class="sxs-lookup"><span data-stu-id="8e244-105">The HoloLens team wants to share some of the best practices that were derived from the Lowe's HoloLens project.</span></span> <span data-ttu-id="8e244-106">以下是 Lowe 的 HoloLens 投射影片，其示範于 Satya 的 2016 Ignite 專題演講。</span><span class="sxs-lookup"><span data-stu-id="8e244-106">Below is a video of the Lowe's HoloLens projected demonstrated at Satya's 2016 Ignite keynote.</span></span>
<br>
>[!VIDEO https://www.youtube.com/embed/gC_4JxF0e_k]

## <a name="lowes-hololens-best-practices"></a><span data-ttu-id="8e244-107">Lowe 的 HoloLens 最佳作法</span><span class="sxs-lookup"><span data-stu-id="8e244-107">Lowe's HoloLens Best Practices</span></span>

<span data-ttu-id="8e244-108">這兩段影片涵蓋的最佳作法是衍生自2016年4月起，已在兩個 Lowe 存放區中的 Lowe HoloLens 試驗。</span><span class="sxs-lookup"><span data-stu-id="8e244-108">The two videos cover best practices that were derived from the Lowe's HoloLens Pilot that has been in two Lowe's stores since April 2016.</span></span> <span data-ttu-id="8e244-109">重要主題如下：</span><span class="sxs-lookup"><span data-stu-id="8e244-109">The key topics are:</span></span>
* <span data-ttu-id="8e244-110">將行動裝置的效能最大化</span><span class="sxs-lookup"><span data-stu-id="8e244-110">Maximize performance for a mobile device</span></span>
* <span data-ttu-id="8e244-111">使用全像全像全像全像全像全像的框架來建立 UX 方法)  (</span><span class="sxs-lookup"><span data-stu-id="8e244-111">Create UX methods with a full holographic frame (2nd talk)</span></span>
* <span data-ttu-id="8e244-112">精確度對齊 (第二個交談) </span><span class="sxs-lookup"><span data-stu-id="8e244-112">Precision alignment (2nd talk)</span></span>
* <span data-ttu-id="8e244-113">共用的全像攝影體驗 (第二談) </span><span class="sxs-lookup"><span data-stu-id="8e244-113">Shared holographic experiences (2nd talk)</span></span>
* <span data-ttu-id="8e244-114">與客戶互動 (第二談) </span><span class="sxs-lookup"><span data-stu-id="8e244-114">Interacting with customers (2nd talk)</span></span>

## <a name="video-1"></a><span data-ttu-id="8e244-115">影片1</span><span class="sxs-lookup"><span data-stu-id="8e244-115">Video 1</span></span>

<span data-ttu-id="8e244-116">**將行動裝置的效能最大化** HoloLens 是在裝置上進行所有處理的非網路共用裝置。</span><span class="sxs-lookup"><span data-stu-id="8e244-116">**Maximize performance for a mobile device** HoloLens is an untethered device with all the processing taking place in the device.</span></span> <span data-ttu-id="8e244-117">這需要行動平臺，而且需要類似于建立行動應用程式的思維。</span><span class="sxs-lookup"><span data-stu-id="8e244-117">This requires a mobile platform and requires a mindset similar to creating mobile applications.</span></span> <span data-ttu-id="8e244-118">Microsoft 建議您的 HoloLens 應用程式維護60FPS，以為您的使用者提供美味體驗。</span><span class="sxs-lookup"><span data-stu-id="8e244-118">Microsoft recommends that your HoloLens application maintain 60FPS to provide a delicious experience for your users.</span></span> <span data-ttu-id="8e244-119">具有低 FPS 可能會導致不穩定的全像影像。</span><span class="sxs-lookup"><span data-stu-id="8e244-119">Having low FPS can result in unstable holograms.</span></span>

<span data-ttu-id="8e244-120">在 HoloLens 上進行開發時，您可以查看的一些最重要的事項是資產優化/減去，使用 [HoloLens 工具](https://github.com/Microsoft/HoloToolkit-Unity) 組) 免費提供的自訂著色器 (。</span><span class="sxs-lookup"><span data-stu-id="8e244-120">Some of the most important things to look at when developing on HoloLens is asset optimization/decimation, using custom shaders (available for free in the [HoloLens Toolkit](https://github.com/Microsoft/HoloToolkit-Unity)).</span></span> <span data-ttu-id="8e244-121">另一個重要的考慮是從專案的最開頭測量畫面播放速率。</span><span class="sxs-lookup"><span data-stu-id="8e244-121">Another important consideration is to measure the frame rate from the very beginning of your project.</span></span> <span data-ttu-id="8e244-122">根據專案而定，顯示資產的順序也可能是很大的參與者</span><span class="sxs-lookup"><span data-stu-id="8e244-122">Depending on the project, the order of displaying your assets can also be a big contributor</span></span>
<br>
>[!VIDEO https://www.youtube.com/embed/o0QIPwgiP9A]

## <a name="video-2"></a><span data-ttu-id="8e244-123">影片2</span><span class="sxs-lookup"><span data-stu-id="8e244-123">Video 2</span></span>

<span data-ttu-id="8e244-124">**使用全像全像全像全像的框架** 請務必瞭解在實體世界中放置全息的位置。</span><span class="sxs-lookup"><span data-stu-id="8e244-124">**Create UX methods with a full holographic frame** It's important to understand the placement of holograms in a physical world.</span></span> <span data-ttu-id="8e244-125">有了 Lowe，我們會討論不同的 UX 方法，以協助使用者在看起來更大的全像投影環境時，能更貼近使用者體驗。</span><span class="sxs-lookup"><span data-stu-id="8e244-125">With Lowe's we talk about different UX methods that help users experience holograms up close while still seeing the larger environment of holograms.</span></span>

<span data-ttu-id="8e244-126">有效 **位數對齊** 在 Lowe 的案例中，最重要的是要讓全像是在實體廚房之間精確地對齊全像投影。</span><span class="sxs-lookup"><span data-stu-id="8e244-126">**Precision alignment** For the Lowe's scenario, it was paramount to the experience to have precision alignment of the holograms to the physical kitchen.</span></span> <span data-ttu-id="8e244-127">我們討論的技術可協助確保說服使用者實體環境已變更的體驗。</span><span class="sxs-lookup"><span data-stu-id="8e244-127">We discuss techniques helps ensure an experience that convinces users that their physical environment has changed.</span></span>

<span data-ttu-id="8e244-128">**共用** 的全像攝影體驗結合是使用 Lowe 經驗的主要方式。</span><span class="sxs-lookup"><span data-stu-id="8e244-128">**Shared holographic experiences** Couples are the primary way that the Lowe's experience is consumed.</span></span> <span data-ttu-id="8e244-129">一個人可以變更檯面，另一個人會看到變更。</span><span class="sxs-lookup"><span data-stu-id="8e244-129">One person can change the countertop and the other person will see the changes.</span></span> <span data-ttu-id="8e244-130">我們稱之為「共用體驗」。</span><span class="sxs-lookup"><span data-stu-id="8e244-130">We called this "shared experiences".</span></span>

<span data-ttu-id="8e244-131">**與客戶互動** Lowe 的設計人員不是使用 HoloLens，但需要查看客戶看到的內容。</span><span class="sxs-lookup"><span data-stu-id="8e244-131">**Interacting with customers** Lowe's designers are not using a HoloLens, but they need to see what the customers are seeing.</span></span> <span data-ttu-id="8e244-132">我們會示範如何抓住客戶在 UWP 應用程式上看到的內容。</span><span class="sxs-lookup"><span data-stu-id="8e244-132">We show how to capture what the customer is seeing on a UWP application.</span></span>
<br>
>[!VIDEO https://www.youtube.com/embed/LceMdyKZ4PI]
