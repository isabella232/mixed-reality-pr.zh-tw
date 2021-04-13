---
title: 開始設計並建立原型
description: 如果您已準備好要建立一些東西，請學習所需的基本概念以開始設計並建立原型。
author: grbury
ms.author: grbury
ms.date: 12/9/2020
ms.topic: article
ms.localizationpriority: high
keywords: 混合實境, 探索, 散發, 索引, 登陸頁面, 設計, 開發, 教學課程, 範例應用程式, 基本, 案例研究, 資源, HoloLens 操作說明, 開放原始碼專案, 核心概念, 互動, 混合實境頭戴式裝置, windows 混合實境頭戴式裝置, 虛擬實境頭戴式裝置, HoloLens, MRTK, 混合實境工具組
ms.openlocfilehash: 36af6b1c439c47eef2126408d1185ecfe151cf8b
ms.sourcegitcommit: e9a0ba97fd288479ad324cdaabee9b6abc9f4dc2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2021
ms.locfileid: "107221560"
---
# <a name="start-designing-and-prototyping"></a><span data-ttu-id="22a2d-104">開始設計並建立原型</span><span class="sxs-lookup"><span data-stu-id="22a2d-104">Start designing and prototyping</span></span>

![混合實境設計抽象](images/design-hero-image.png)

<span data-ttu-id="22a2d-106">混合實境應用程式不同於現今既有的任何技術，其設計是很困難的工作。</span><span class="sxs-lookup"><span data-stu-id="22a2d-106">Mixed Reality applications are unlike anything else in the world today, and designing them is hard work.</span></span> <span data-ttu-id="22a2d-107">您不僅必須將考量您所建立的實際和虛擬環境之間全新的組合，也必須考量其所提供的全新使用者體驗。</span><span class="sxs-lookup"><span data-stu-id="22a2d-107">Not only do you have to account for the new combinations of real and virtual worlds you're creating, but also the new user experiences they afford.</span></span> <span data-ttu-id="22a2d-108">由於混合實境牽涉領域很廣，我們僅選擇了若干重點及其設計頻譜，並將以一系列檢查點的形式列於下方。</span><span class="sxs-lookup"><span data-stu-id="22a2d-108">Since Mixed Reality is a big place, we've selected important points along its design spectrum and laid them out below as a series of checkpoints.</span></span> <span data-ttu-id="22a2d-109">這些檢查點通常應依序執行，但如果您有把握，則可以隨意跳到下列任何一節。</span><span class="sxs-lookup"><span data-stu-id="22a2d-109">These are meant to be sequential, but if you've already dipped your feet in feel free to jump to any of the following sections.</span></span> 

<span data-ttu-id="22a2d-110">請觀看我們的設計概觀影片以開始使用：</span><span class="sxs-lookup"><span data-stu-id="22a2d-110">Take a look at our design overview video to get started:</span></span>

>[!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4LhlW]

## <a name="design-checkpoints"></a><span data-ttu-id="22a2d-111">設計檢查點</span><span class="sxs-lookup"><span data-stu-id="22a2d-111">Design checkpoints</span></span>

<span data-ttu-id="22a2d-112">使用下列檢查點，將您的應用程式構想和概念融入混合實境的世界中。</span><span class="sxs-lookup"><span data-stu-id="22a2d-112">Use the following checkpoints to bring your application ideas and concepts into the world of mixed reality.</span></span>

### <a name="1-getting-started"></a><span data-ttu-id="22a2d-113">1.開始使用</span><span class="sxs-lookup"><span data-stu-id="22a2d-113">1. Getting started</span></span>

<span data-ttu-id="22a2d-114">和所有的旅程一樣，在探索如何設計混合實境應用程式時，您也應從基本概念開始著手。</span><span class="sxs-lookup"><span data-stu-id="22a2d-114">Like all journeys, your adventure into designing Mixed Reality applications starts with the basics.</span></span> <span data-ttu-id="22a2d-115">建議您詳閱[什麼是混合實境](../discover/mixed-reality.md)和[什麼是全像投影？](../discover/hologram.md)這兩篇文章，以取得沉浸式設計的概念。</span><span class="sxs-lookup"><span data-stu-id="22a2d-115">We recommend familiarizing yourself with the [What is Mixed Reality](../discover/mixed-reality.md) and [What is a hologram?](../discover/hologram.md) articles to get your mind primed for immersive design.</span></span> <span data-ttu-id="22a2d-116">閱讀完成後，您即可展開混合實境設計旅程！</span><span class="sxs-lookup"><span data-stu-id="22a2d-116">Once you've completed your read-through, you'll be ready to start your Mixed Reality design journey!</span></span>

![從 Designing Holograms 應用程式開始使用 GIF](images/HandTracking2.gif)

|  <span data-ttu-id="22a2d-118">Checkpoint</span><span class="sxs-lookup"><span data-stu-id="22a2d-118">Checkpoint</span></span>  |  <span data-ttu-id="22a2d-119">結果</span><span class="sxs-lookup"><span data-stu-id="22a2d-119">Outcome</span></span>  |
| --- | --- |
| [<span data-ttu-id="22a2d-120">展開您的設計程序</span><span class="sxs-lookup"><span data-stu-id="22a2d-120">Expand your design process</span></span>](../discover/case-study-expanding-the-design-process-for-mixed-reality.md) | <span data-ttu-id="22a2d-121">從 Microsoft 內部和外部的設計師收集有關混合實境的設計過程第一手資料</span><span class="sxs-lookup"><span data-stu-id="22a2d-121">Get a first-hand look at design process for Mixed Reality, gathered from designers inside and outside of Microsoft</span></span> |
| [<span data-ttu-id="22a2d-122">混合實境應用程式的類型</span><span class="sxs-lookup"><span data-stu-id="22a2d-122">Types of Mixed Reality apps</span></span>](types-of-mixed-reality-apps.md) | <span data-ttu-id="22a2d-123">決定您的應用程式體驗在混合實境頻譜上的位置</span><span class="sxs-lookup"><span data-stu-id="22a2d-123">Decide where your app experience will live on the Mixed Reality spectrum</span></span> |
| [<span data-ttu-id="22a2d-124">Designing Holograms 應用程式</span><span class="sxs-lookup"><span data-stu-id="22a2d-124">Designing Holograms app</span></span>](https://www.microsoft.com/p/designing-holograms/9nxwnjklrzwd) | <span data-ttu-id="22a2d-125">深入了解混合實境 UX 設計的基本概念，方法是體驗如何建立絕佳 HoloLens 應用程式 (可從 HoloLens 2 的 Microsoft Store 下載) 的行為、秘訣和建議</span><span class="sxs-lookup"><span data-stu-id="22a2d-125">Learn the fundamentals of Mixed Reality UX Design by experiencing with behaviors, tips, and recommendations for creating amazing HoloLens apps (available for download from Microsoft Store in HoloLens 2)</span></span> |
| [<span data-ttu-id="22a2d-126">MRTK 範例中樞</span><span class="sxs-lookup"><span data-stu-id="22a2d-126">MRTK Examples Hub</span></span>](https://www.microsoft.com/en-us/p/mrtk-examples-hub/9mv8c39l2sj4) | <span data-ttu-id="22a2d-127">體驗適用於混合實境的一般空間互動和 UX 建構元素 (可從 HoloLens 2 中的 Microsoft Store 下載)</span><span class="sxs-lookup"><span data-stu-id="22a2d-127">Experience common spatial interactions and UX building blocks for Mixed Reality (available for download from Microsoft Store in HoloLens 2)</span></span> |
| <span data-ttu-id="22a2d-128">**選擇性**[下載 Figma 工具](figma-toolkit.md)組</span><span class="sxs-lookup"><span data-stu-id="22a2d-128">**Optional** [Download the Figma Toolkit](figma-toolkit.md)</span></span> | <span data-ttu-id="22a2d-129">Figma 工具組提供的資產可供您用來根據 MRTK 中可用的元件來繪製和配置 UI</span><span class="sxs-lookup"><span data-stu-id="22a2d-129">The Figma Toolkit provides assets for you to use for sketching and laying out UI based on the components available in MRTK</span></span> |

### <a name="2-core-concepts"></a><span data-ttu-id="22a2d-130">2.核心概念</span><span class="sxs-lookup"><span data-stu-id="22a2d-130">2. Core concepts</span></span>

<span data-ttu-id="22a2d-131">無論您進行 VR 還是 AR 的開發，為了設計流暢的沉浸式體驗，有幾個核心概念是務必牢記在心的。</span><span class="sxs-lookup"><span data-stu-id="22a2d-131">Whether you're developing for VR or AR, there are several core concepts that apply to designing fluid immersive experiences.</span></span> <span data-ttu-id="22a2d-132">了解使用者的觀點、定位物件，以及確保每個人都感到安心舒適，是您在這個階段的旅程首先要考量的。</span><span class="sxs-lookup"><span data-stu-id="22a2d-132">Understanding the users point of view, positioning objects, and ensuring everyone is comfortable and safe are your top priorities at this stage of your journey.</span></span> <span data-ttu-id="22a2d-133">在本節結束時，您就已打好堅實的基礎，可繼續進入互動設計階段。</span><span class="sxs-lookup"><span data-stu-id="22a2d-133">By the end of this section you'll have a solid foundation to carry through into interaction design.</span></span>

![核心概念範例影像](images/fragments-750px.jpg)

|  <span data-ttu-id="22a2d-135">概念</span><span class="sxs-lookup"><span data-stu-id="22a2d-135">Concept</span></span>  |  <span data-ttu-id="22a2d-136">結果</span><span class="sxs-lookup"><span data-stu-id="22a2d-136">Outcome</span></span>  |
| --- | --- |
| [<span data-ttu-id="22a2d-137">全像攝影框架</span><span class="sxs-lookup"><span data-stu-id="22a2d-137">Holographic frame</span></span>](holographic-frame.md) | <span data-ttu-id="22a2d-138">了解使用者在配戴頭戴式裝置看您覆疊在實際環境上的內容時，是什麼情形</span><span class="sxs-lookup"><span data-stu-id="22a2d-138">Understand how users see your content overlaid onto the real world when wearing their headsets</span></span> |
| [<span data-ttu-id="22a2d-139">座標系統</span><span class="sxs-lookup"><span data-stu-id="22a2d-139">Coordinate systems</span></span>](coordinate-systems.md) | <span data-ttu-id="22a2d-140">了解如何將全像投影放置在世界上有意義的地方，不論是他們所在的實際空間或您所建立的虛擬領域</span><span class="sxs-lookup"><span data-stu-id="22a2d-140">Learn how to position holograms in meaningful places in the world, whether it's their physical room or a virtual realm you've created</span></span> |
| [<span data-ttu-id="22a2d-141">空間對應</span><span class="sxs-lookup"><span data-stu-id="22a2d-141">Spatial mapping</span></span>](spatial-mapping.md) | <span data-ttu-id="22a2d-142">錨定使用者世界中的物件，並利用真實世界的實體介面</span><span class="sxs-lookup"><span data-stu-id="22a2d-142">Anchor objects in the user's world and take advantage of real world's physical surfaces</span></span> |
| [<span data-ttu-id="22a2d-143">舒適度考量</span><span class="sxs-lookup"><span data-stu-id="22a2d-143">Comfort considerations</span></span>](comfort.md) | <span data-ttu-id="22a2d-144">以模仿自然環境的方式建立和呈現沉浸式內容，以確保使用者的舒適度和安全性</span><span class="sxs-lookup"><span data-stu-id="22a2d-144">Ensure user comfort and safety by creating and presenting immersive content in a way that mimics the natural world</span></span> |

### <a name="3-interaction-design"></a><span data-ttu-id="22a2d-145">3.互動設計</span><span class="sxs-lookup"><span data-stu-id="22a2d-145">3. Interaction design</span></span>

<span data-ttu-id="22a2d-146">無論虛擬體驗有多美好、多讓人投入，若沒有互動，一切都是枉然。</span><span class="sxs-lookup"><span data-stu-id="22a2d-146">No matter how beautiful and immersive a virtual experience is, it's useless without interaction.</span></span> <span data-ttu-id="22a2d-147">本節將逐步引導您了解基本互動模型、手部和運動控制器、語音輸入，以及如何收集使用者的眼睛追蹤資料。</span><span class="sxs-lookup"><span data-stu-id="22a2d-147">This section will walk you through basic interaction models, hand and motion controllers, voice input, and gathering eye tracking data from your users.</span></span> <span data-ttu-id="22a2d-148">本節結束後，您即可進入設計旅程的最後一個重要主題：使用者體驗。</span><span class="sxs-lookup"><span data-stu-id="22a2d-148">By the end of this section you'll be ready to tackle the last big topic on your design journey: user experience.</span></span>

![互動設計因素](images/UX_Hero_Manipulation.jpg)

|  <span data-ttu-id="22a2d-150">概念</span><span class="sxs-lookup"><span data-stu-id="22a2d-150">Concept</span></span>  |  <span data-ttu-id="22a2d-151">結果</span><span class="sxs-lookup"><span data-stu-id="22a2d-151">Outcome</span></span>  |
| --- | --- |
| [<span data-ttu-id="22a2d-152">互動模型</span><span class="sxs-lookup"><span data-stu-id="22a2d-152">Interaction models</span></span>](interaction-fundamentals.md) | <span data-ttu-id="22a2d-153">透過手部、眼睛和語音輸入，為您的使用者提供本能互動</span><span class="sxs-lookup"><span data-stu-id="22a2d-153">Provide your users with instinctual interactions through hand, eye, and voice input</span></span> |
| [<span data-ttu-id="22a2d-154">手部和運動控制器</span><span class="sxs-lookup"><span data-stu-id="22a2d-154">Hands and motion controllers</span></span>](hands-and-tools.md) | <span data-ttu-id="22a2d-155">了解如何以使用者的手部近距離與全像投影互動，或透過精確的互動長距離操控</span><span class="sxs-lookup"><span data-stu-id="22a2d-155">Learn how to interact with holograms at close range with a user' hands or at long range with precise interactions</span></span> |
| [<span data-ttu-id="22a2d-156">語音輸入</span><span class="sxs-lookup"><span data-stu-id="22a2d-156">Voice input</span></span>](voice-input.md) | <span data-ttu-id="22a2d-157">在您的沉浸式應用程式中使用語音命令作為輸入，以控制全像投影和環境</span><span class="sxs-lookup"><span data-stu-id="22a2d-157">Use voice commands as input in your immersive apps to control surrounding holograms and environments</span></span>  |
| [<span data-ttu-id="22a2d-158">眼睛追蹤</span><span class="sxs-lookup"><span data-stu-id="22a2d-158">Eye Tracking</span></span>](eye-tracking.md) | <span data-ttu-id="22a2d-159">以使用者所見景象的相關資訊，在全像攝影體驗中加入新一層的內容和人類理解</span><span class="sxs-lookup"><span data-stu-id="22a2d-159">Add a new level of context and human understanding in a holographic experience by using information about what your users are looking at</span></span> |

### <a name="4-user-experience-elements"></a><span data-ttu-id="22a2d-160">4.使用者體驗元素</span><span class="sxs-lookup"><span data-stu-id="22a2d-160">4. User experience elements</span></span>

<span data-ttu-id="22a2d-161">在您已熟知基本的互動後，接下來即可專注於使用者體驗元素更細微的部分，並針對混合實境的獨特環境進行調整。</span><span class="sxs-lookup"><span data-stu-id="22a2d-161">Now that you've mastered basic interactions, you can focus on the finer points of user experience elements and how to adapt them for Mixed Reality's unique environments.</span></span> <span data-ttu-id="22a2d-162">常見的行為、資產設計、物件調整和印刷樣式都應涵蓋在內，而且讓使用者擁有直覺式體驗。</span><span class="sxs-lookup"><span data-stu-id="22a2d-162">You'll cover common behaviors, asset design, object scaling, and typography, while making the experience intuitive for your users.</span></span> <span data-ttu-id="22a2d-163">本節完成後，正式的混合實境設計旅程即告終，但您可以參考[下一步是什麼？](#whats-next)一節，繼續深入探索。</span><span class="sxs-lookup"><span data-stu-id="22a2d-163">This section marks the end of the official Mixed Reality design journey, but there are more resources in the [What's next?](#whats-next) section to keep you going.</span></span>

![UX 元素](images/UX_Hero_BoundingBox.jpg)

|  <span data-ttu-id="22a2d-165">概念</span><span class="sxs-lookup"><span data-stu-id="22a2d-165">Concept</span></span>  |  <span data-ttu-id="22a2d-166">結果</span><span class="sxs-lookup"><span data-stu-id="22a2d-166">Outcome</span></span>  |
| --- | --- |
| [<span data-ttu-id="22a2d-167">通用控制項和行為</span><span class="sxs-lookup"><span data-stu-id="22a2d-167">Common controls and behaviors</span></span>](app-patterns-landingpage.md) | <span data-ttu-id="22a2d-168">了解常用的空間互動和 UI 建置組塊</span><span class="sxs-lookup"><span data-stu-id="22a2d-168">Learn about frequently used spatial interactions and UI building blocks</span></span> |
| [<span data-ttu-id="22a2d-169">色彩、光線和材質</span><span class="sxs-lookup"><span data-stu-id="22a2d-169">Color, light, and materials</span></span>](color-light-and-materials.md) | <span data-ttu-id="22a2d-170">為混合實境設計將色彩、光源和材質納入考量的高品質資產</span><span class="sxs-lookup"><span data-stu-id="22a2d-170">Design quality assets for Mixed Reality that take color, lighting, and materials into account</span></span> |
| [<span data-ttu-id="22a2d-171">物件縮放比例</span><span class="sxs-lookup"><span data-stu-id="22a2d-171">Object scale</span></span>](scale.md) | <span data-ttu-id="22a2d-172">盡可能整合較多的實際環境視覺提示，以協助使用者了解物件的位置、物件的大小，及其組成元素</span><span class="sxs-lookup"><span data-stu-id="22a2d-172">Incorporate as many real-world visual cues as possible to us help your users understand where objects are, how big they are, and what they’re made of</span></span> |
| [<span data-ttu-id="22a2d-173">印刷樣式</span><span class="sxs-lookup"><span data-stu-id="22a2d-173">Typography</span></span>](typography.md) | <span data-ttu-id="22a2d-174">在三維空間中使用清楚、可讀的文字，讓您的使用者獲得所需的重要資訊</span><span class="sxs-lookup"><span data-stu-id="22a2d-174">Use clear, readable text in three-dimensional space to give your users the important information they need</span></span> |

## <a name="whats-next"></a><span data-ttu-id="22a2d-175">接下來要做什麼？</span><span class="sxs-lookup"><span data-stu-id="22a2d-175">What's next?</span></span>

<span data-ttu-id="22a2d-176">設計人員的工作無止境，在學習以新的開發架構建立沉浸式體驗時，尤其如此。</span><span class="sxs-lookup"><span data-stu-id="22a2d-176">A designer's job is never done, especially when learning to create immersive experiences in a new paradigm.</span></span> <span data-ttu-id="22a2d-177">完成入門級設計教學後，以下各節將帶領您進一步深入混合實境開發的領域。</span><span class="sxs-lookup"><span data-stu-id="22a2d-177">The following sections will take you beyond the beginner level design material you've already completed and into the world of Mixed Reality development.</span></span> <span data-ttu-id="22a2d-178">這些主題和資源無須依序使用，您可以隨意來回探索！</span><span class="sxs-lookup"><span data-stu-id="22a2d-178">These topics and resources aren't in any sequential order, so feel free to explore!</span></span>

### <a name="choose-a-prototyping-option"></a><span data-ttu-id="22a2d-179">選擇原型設計選項</span><span class="sxs-lookup"><span data-stu-id="22a2d-179">Choose a prototyping option</span></span>  

:::row:::   
    :::column:::    
       <span data-ttu-id="22a2d-180">[![學習 Unity](images/logo-unity.png)](https://learn.unity.com/)</span><span class="sxs-lookup"><span data-stu-id="22a2d-180">[![Learn Unity](images/logo-unity.png)](https://learn.unity.com/)</span></span><br>
        <span data-ttu-id="22a2d-181">**[學習 Unity](https://learn.unity.com/)**</span><span class="sxs-lookup"><span data-stu-id="22a2d-181">**[Learn Unity](https://learn.unity.com/)**</span></span><br>
        <span data-ttu-id="22a2d-182">瞭解如何使用 Unity 建立互動式體驗。</span><span class="sxs-lookup"><span data-stu-id="22a2d-182">Learn how to create interactive experiences with Unity.</span></span> <span data-ttu-id="22a2d-183">邊做邊學，從開始到完成。</span><span class="sxs-lookup"><span data-stu-id="22a2d-183">Learn by doing, from start to finish.</span></span>
    :::column-end:::    
    :::column:::    
        <span data-ttu-id="22a2d-184">[![混合實境工具組 (MRTK)](images/74-12.png)](https://github.com/Microsoft/MixedRealityToolkit-Unity)</span><span class="sxs-lookup"><span data-stu-id="22a2d-184">[![Mixed Reality Toolkit (MRTK)](images/74-12.png)](https://github.com/Microsoft/MixedRealityToolkit-Unity)</span></span><br>
        <span data-ttu-id="22a2d-185">**[混合實境工具組 (MRTK)](https://github.com/Microsoft/MixedRealityToolkit-Unity)**</span><span class="sxs-lookup"><span data-stu-id="22a2d-185">**[Mixed Reality Toolkit (MRTK)](https://github.com/Microsoft/MixedRealityToolkit-Unity)**</span></span><br>  
        <span data-ttu-id="22a2d-186">透過混合實境工具組的空間互動和 UI 基本要素，您可以使用 Unity 快速進行混合實境的設計和開發。</span><span class="sxs-lookup"><span data-stu-id="22a2d-186">With spatial interaction and UI building blocks, jump-start your mixed reality design and development with Unity.</span></span>   
    :::column-end:::
    :::column:::    
        <span data-ttu-id="22a2d-187">[![混合實境設計實驗室](images/74-13.png)](https://github.com/Microsoft/MRDL_Unity_PeriodicTable)</span><span class="sxs-lookup"><span data-stu-id="22a2d-187">[![Mixed Reality Design Labs](images/74-13.png)](https://github.com/Microsoft/MRDL_Unity_PeriodicTable)</span></span><br>
        <span data-ttu-id="22a2d-188">**[混合實境設計實驗室](https://github.com/Microsoft/MRDL_Unity_PeriodicTable)**</span><span class="sxs-lookup"><span data-stu-id="22a2d-188">**[Mixed Reality Design Labs](https://github.com/Microsoft/MRDL_Unity_PeriodicTable)**</span></span><br>  
        <span data-ttu-id="22a2d-189">取得範例應用程式，示範如何使用 MRTK 的建置元素來建立美觀的混合實境體驗。</span><span class="sxs-lookup"><span data-stu-id="22a2d-189">Get sample apps that show you how to use MRTK's building blocks to create beautiful mixed reality experiences.</span></span>
    :::column-end:::        
    :::column:::    
        <span data-ttu-id="22a2d-190">[![Microsoft Maquette](images/74-14.png)](https://www.maquette.ms/)</span><span class="sxs-lookup"><span data-stu-id="22a2d-190">[![Microsoft Maquette](images/74-14.png)](https://www.maquette.ms/)</span></span><br>
        <span data-ttu-id="22a2d-191">**[Microsoft Maquette](https://www.maquette.ms/)**</span><span class="sxs-lookup"><span data-stu-id="22a2d-191">**[Microsoft Maquette](https://www.maquette.ms/)**</span></span><br>  
        <span data-ttu-id="22a2d-192">為 VR 而設計。</span><span class="sxs-lookup"><span data-stu-id="22a2d-192">Design for VR.</span></span> <span data-ttu-id="22a2d-193">Microsoft Maquette 讓空間原型設計變得簡單、快速、身歷其境。</span><span class="sxs-lookup"><span data-stu-id="22a2d-193">Microsoft Maquette makes spatial prototyping easy, quick, and immersive.</span></span> 
    :::column-end:::    
:::row-end:::

<br>

---

### <a name="other-resources"></a><span data-ttu-id="22a2d-194">其他資源</span><span class="sxs-lookup"><span data-stu-id="22a2d-194">Other resources</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="22a2d-195">[![了解基本概念](images/74-15.png)](../discover/get-started-with-mr.md#understand-the-basics)</span><span class="sxs-lookup"><span data-stu-id="22a2d-195">[![Understand the basics](images/74-15.png)](../discover/get-started-with-mr.md#understand-the-basics)</span></span><br>
        <span data-ttu-id="22a2d-196">**[了解基本概念](../discover/get-started-with-mr.md#understand-the-basics)**</span><span class="sxs-lookup"><span data-stu-id="22a2d-196">**[Understand the basics](../discover/get-started-with-mr.md#understand-the-basics)**</span></span><br>
        <span data-ttu-id="22a2d-197">進一步瞭解混合實境的定義以及其使用方式。</span><span class="sxs-lookup"><span data-stu-id="22a2d-197">Get a better understanding of what defines mixed reality and how it’s being used.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="22a2d-198">[![參加活動](images/74-16.png)](../whats-new/sf-academy-events.md)</span><span class="sxs-lookup"><span data-stu-id="22a2d-198">[![Come to an event](images/74-16.png)](../whats-new/sf-academy-events.md)</span></span><br>
         <span data-ttu-id="22a2d-199">**[參加活動](../whats-new/sf-academy-events.md)**</span><span class="sxs-lookup"><span data-stu-id="22a2d-199">**[Come to an event](../whats-new/sf-academy-events.md)**</span></span><br>
        <span data-ttu-id="22a2d-200">參觀硬體並取得實際操作教學課程，製作您的第一個 HoloLens 2 應用程式。</span><span class="sxs-lookup"><span data-stu-id="22a2d-200">See the hardware and get a hands-on tutorial to make your first HoloLens 2 application.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="22a2d-201">[![安裝工具](images/74-17.png)](../develop/install-the-tools.md)</span><span class="sxs-lookup"><span data-stu-id="22a2d-201">[![Install the tools](images/74-17.png)](../develop/install-the-tools.md)</span></span><br>
         <span data-ttu-id="22a2d-202">**[安裝工具](../develop/install-the-tools.md)**</span><span class="sxs-lookup"><span data-stu-id="22a2d-202">**[Install the tools](../develop/install-the-tools.md)**</span></span><br>
        <span data-ttu-id="22a2d-203">使用安裝檢查清單來取得建置 HoloLens 和混合實境應用程式所需的工具。</span><span class="sxs-lookup"><span data-stu-id="22a2d-203">Use the installation checklist to get the tools you need to build apps for HoloLens and mixed reality.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="22a2d-204">[![開始進行開發](images/74-18.png)](../develop/development.md)</span><span class="sxs-lookup"><span data-stu-id="22a2d-204">[![Start developing](images/74-18.png)](../develop/development.md)</span></span><br>
        <span data-ttu-id="22a2d-205">**[開始進行開發](../develop/development.md)**</span><span class="sxs-lookup"><span data-stu-id="22a2d-205">**[Start developing](../develop/development.md)**</span></span><br>
        <span data-ttu-id="22a2d-206">根據您的技能層級、工作風格或感興趣的平台，選擇開發路徑。</span><span class="sxs-lookup"><span data-stu-id="22a2d-206">Choose a development path based on your skill level, work style, or platform interest.</span></span>
    :::column-end:::
:::row-end:::

<br>

<br>
