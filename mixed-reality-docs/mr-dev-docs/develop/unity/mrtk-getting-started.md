---
title: 適用於 Unity 的 MRTK 簡介
description: 適用於想要使用 MRTK 的新開發人員
author: cre8ivepark
ms.author: dongpark
ms.date: 05/15/2019
ms.topic: article
ms.localizationpriority: high
keywords: Windows Mixed Reality, 測試, 混合實境工具組, MRTK 第 2 版, MRTK, 工具, SDK, HoloLens, HoloLens 2, 混合實境頭戴式裝置, windows 混合實境頭戴式裝置, 虛擬實境頭戴式裝置, 跨平台
ms.openlocfilehash: 6887d79d4a0737f3ed0f63af5686699fc7a1a2b6
ms.sourcegitcommit: 2bf79eef6a9b845494484f458443ef4f89d7efc0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/17/2020
ms.locfileid: "97613442"
---
# <a name="introducing-mrtk-for-unity"></a><span data-ttu-id="af28c-104">適用於 Unity 的 MRTK 簡介</span><span class="sxs-lookup"><span data-stu-id="af28c-104">Introducing MRTK for Unity</span></span>

![MRTK](../../design/images/MRTK_UX_Hero.png)

## <a name="what-is-mixed-reality-toolkit-mrtk"></a><span data-ttu-id="af28c-106">混合實境工具組 (MRTK) 是什麼？</span><span class="sxs-lookup"><span data-stu-id="af28c-106">What is Mixed Reality Toolkit (MRTK)?</span></span>
<span data-ttu-id="af28c-107">MRTK 是一項令人驚奇的開放原始碼工具組，自 HoloLens 首次發行之後就已經存在。</span><span class="sxs-lookup"><span data-stu-id="af28c-107">MRTK is an amazing open-source toolkit that has been around since the HoloLens was first released.</span></span> <span data-ttu-id="af28c-108">沒有開發人員社群的努力，就不會達到今天的境界。</span><span class="sxs-lookup"><span data-stu-id="af28c-108">The toolkit wouldn't be where it is today without the hard work of our contributing developer community.</span></span> <span data-ttu-id="af28c-109">過去三年來，我們聽取了開發人員社群的意見反應，將最主要的考量納入，建置了 MRTK v2。</span><span class="sxs-lookup"><span data-stu-id="af28c-109">Over the past three years, we've listened to the feedback of our developer community, and built MRTK v2 to take the biggest concerns into account.</span></span>  

<span data-ttu-id="af28c-110">適用於 Unity 的 MRTK 是混合實境應用程式的開放原始碼跨平台開發套件。</span><span class="sxs-lookup"><span data-stu-id="af28c-110">MRTK for Unity is an open-source, cross-platform development kit for mixed reality applications.</span></span> <span data-ttu-id="af28c-111">此工具組提供跨平台輸入系統、基礎元件，以及空間互動的常見基本要素。</span><span class="sxs-lookup"><span data-stu-id="af28c-111">The toolkit provides a cross-platform input system, foundational components, and common building blocks for spatial interactions.</span></span> <span data-ttu-id="af28c-112">MRTK 第 2 版主要用於加速開發適用於 Microsoft HoloLens、Windows Mixed Reality 沈浸式 (VR) 頭戴裝置和 OpenVR 平台的應用程式。</span><span class="sxs-lookup"><span data-stu-id="af28c-112">MRTK version 2 intends to speed up application development for Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets, and OpenVR platform.</span></span> <span data-ttu-id="af28c-113">此專案的目標是減少進入障礙、建立混合實境應用程式，以及回饋伴著我們成長的社群。</span><span class="sxs-lookup"><span data-stu-id="af28c-113">The project is aimed at reducing barriers to entry, creating mixed reality applications, and contributing back to the community as we all grow.</span></span>

<br>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4IkCG]

<span data-ttu-id="af28c-114">請參閱 [GitHub 上的 MRTK 文件](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)，並從[安裝指南](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html)來開始著手。</span><span class="sxs-lookup"><span data-stu-id="af28c-114">Take a look at the [MRTK's documentation on GitHub](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html) and get started with the [installation guide](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html).</span></span>


## <a name="new-with-mrtk-v2"></a><span data-ttu-id="af28c-115">MRTK v2 的新功能</span><span class="sxs-lookup"><span data-stu-id="af28c-115">New with MRTK v2</span></span>
<span data-ttu-id="af28c-116">我們想要強調我們對這些平台工具的承諾。</span><span class="sxs-lookup"><span data-stu-id="af28c-116">We want to stress our commitment to these platform tools.</span></span>  <span data-ttu-id="af28c-117">事實上，我們使用 MRTK 第 2 版來開發收件匣體驗，例如全新安裝體驗 (OOBE) 和我們的混合實境提示應用程式。</span><span class="sxs-lookup"><span data-stu-id="af28c-117">In fact, we used MRTK version 2 to develop our inbox experiences, such as the out-of-box setup experience (OOBE) and our Mixed Reality Tips application.</span></span> <span data-ttu-id="af28c-118">您也可以預期新的 HoloLens 2 功能會先透過 MRTK 公開，因為我們認為這是在我們的平台上進行開發的最佳方式。</span><span class="sxs-lookup"><span data-stu-id="af28c-118">You can also expect to see new HoloLens 2 capabilities first exposed through MRTK because we believe it’s the best way to develop on our platform.</span></span> 

### <a name="modular"></a><span data-ttu-id="af28c-119">模組化</span><span class="sxs-lookup"><span data-stu-id="af28c-119">Modular</span></span>
<span data-ttu-id="af28c-120">我們以模組化的方式建置，因此您不需要個別將工具組的部分納入您的專案中。</span><span class="sxs-lookup"><span data-stu-id="af28c-120">We have built it in a modular way, so you don't need to take every bit of the toolkit into your project.</span></span>  <span data-ttu-id="af28c-121">這其實有幾個優點。</span><span class="sxs-lookup"><span data-stu-id="af28c-121">There are actually a few benefits to this.</span></span>  <span data-ttu-id="af28c-122">它會讓您的專案大小變小，讓您更容易管理。</span><span class="sxs-lookup"><span data-stu-id="af28c-122">It keeps your project size smaller, and makes it easier to manage.</span></span>  <span data-ttu-id="af28c-123">此外，由於它是以可編寫指令碼的物件建置，而且是介面驅動的，因此您也可以用自己的物件取代其中所包含的元件，以支援其他服務、系統和平台。</span><span class="sxs-lookup"><span data-stu-id="af28c-123">Additionally, because it’s built with scriptable objects and is interface-driven, it’s also possible for you to replace the components that are included with your own, to support other services, systems, and platforms.</span></span>

### <a name="cross-platform"></a><span data-ttu-id="af28c-124">跨平台</span><span class="sxs-lookup"><span data-stu-id="af28c-124">Cross-platform</span></span>
<span data-ttu-id="af28c-125">說到其他平台，它有跨平台支援。</span><span class="sxs-lookup"><span data-stu-id="af28c-125">Speaking of other platforms, it has cross-platform support.</span></span>  <span data-ttu-id="af28c-126">雖然這並不代表每個平台都會獲得支援，但是我們確定當您將建置目標切換至其他平台時，不會有任何工具組程式碼中斷。</span><span class="sxs-lookup"><span data-stu-id="af28c-126">And while this doesn’t mean every single platform is supported, we have made sure none of the toolkit code will break when you switch your build target to other platforms.</span></span>  <span data-ttu-id="af28c-127">模組化設計的健全性和擴充性，會讓應用程式有能力支援多個平台，例如 ARCore、ARKit 和 OpenVR。</span><span class="sxs-lookup"><span data-stu-id="af28c-127">The robustness and extensibility of the modular design sets your apps up to support multiple platforms, such as ARCore, ARKit, and OpenVR.</span></span>

### <a name="performant"></a><span data-ttu-id="af28c-128">效能</span><span class="sxs-lookup"><span data-stu-id="af28c-128">Performant</span></span>
<span data-ttu-id="af28c-129">使用行動平台時，我們會考慮到效能。</span><span class="sxs-lookup"><span data-stu-id="af28c-129">Working with mobile platforms, we constructed it with performance in mind.</span></span>  <span data-ttu-id="af28c-130">這是非常重要的，我們想要確保工具不會與您作對。</span><span class="sxs-lookup"><span data-stu-id="af28c-130">This is super important, and we wanted to ensure that the tools aren't going to work against you.</span></span>

## <a name="see-also"></a><span data-ttu-id="af28c-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="af28c-131">See also</span></span>
* [<span data-ttu-id="af28c-132">安裝工具</span><span class="sxs-lookup"><span data-stu-id="af28c-132">Install the tools</span></span>](../install-the-tools.md)
* [<span data-ttu-id="af28c-133">MRTK - 安裝指南 (GitHub)</span><span class="sxs-lookup"><span data-stu-id="af28c-133">MRTK - Installation guide (GitHub)</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html)
* [<span data-ttu-id="af28c-134">MRTK - 文件首頁 (GitHub)</span><span class="sxs-lookup"><span data-stu-id="af28c-134">MRTK - Documentation home (GitHub)</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
* [<span data-ttu-id="af28c-135">從 HoloToolkit/MRTK 移植到 MRTK 第 2 版 (GitHub)</span><span class="sxs-lookup"><span data-stu-id="af28c-135">Porting from HoloToolkit/MRTK to MRTK version 2 (GitHub)</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/HTKToMRTKPortingGuide.html)
