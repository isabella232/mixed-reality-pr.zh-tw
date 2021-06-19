---
title: 適用于 Unreal 的 MRTK 簡介
description: 開始使用適用于 Unreal 的混合現實工具組，必須提供新的混合現實開發人員。
author: hferrone
ms.author: v-hferrone
ms.date: 01/08/2021
ms.topic: article
ms.localizationpriority: high
keywords: Windows Mixed Reality, 測試, 混合實境工具組, MRTK 第 2 版, MRTK, 工具, SDK, HoloLens, HoloLens 2, 混合實境頭戴式裝置, windows 混合實境頭戴式裝置, 虛擬實境頭戴式裝置, 跨平台
ms.openlocfilehash: 3d46b92dbf3182ca5a50a8e106d2b947e4f7120f
ms.sourcegitcommit: 6ade7e8ebab7003fc24f9e0b5fa81d091369622c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2021
ms.locfileid: "112394282"
---
# <a name="introducing-mrtk-for-unreal"></a><span data-ttu-id="f8d88-104">適用于 Unreal 的 MRTK 簡介</span><span class="sxs-lookup"><span data-stu-id="f8d88-104">Introducing MRTK for Unreal</span></span>

![MRTK 橫幅影像](../../design/images/MRTK_UX_Hero.png)

## <a name="what-is-mixed-reality-toolkit-mrtk"></a><span data-ttu-id="f8d88-106">混合實境工具組 (MRTK) 是什麼？</span><span class="sxs-lookup"><span data-stu-id="f8d88-106">What is Mixed Reality Toolkit (MRTK)?</span></span>

<span data-ttu-id="f8d88-107">MRTK 是一項令人驚奇的開放原始碼工具組，自 HoloLens 首次發行之後就已經存在。</span><span class="sxs-lookup"><span data-stu-id="f8d88-107">MRTK is an amazing open-source toolkit that has been around since the HoloLens was first released.</span></span> <span data-ttu-id="f8d88-108">沒有開發人員社群的努力，就不會達到今天的境界。</span><span class="sxs-lookup"><span data-stu-id="f8d88-108">The toolkit wouldn't be where it is today without the hard work of our contributing developer community.</span></span> 

<span data-ttu-id="f8d88-109">適用于 Unreal (MRTK-Unreal) 的混合現實工具組是一組元件（以外掛程式、範例和檔的形式），其設計目的是要協助使用 Unreal 引擎開發混合現實應用程式。</span><span class="sxs-lookup"><span data-stu-id="f8d88-109">The Mixed Reality Toolkit for Unreal (MRTK-Unreal) is a set of components, in the form of plugins, samples and documentation, designed to help development of Mixed Reality applications using the Unreal Engine.</span></span> <span data-ttu-id="f8d88-110">目前，此工具組包含：</span><span class="sxs-lookup"><span data-stu-id="f8d88-110">Currently, the toolkit consists of:</span></span>
* <span data-ttu-id="f8d88-111">[適用于 Unreal 的 UX 工具](https://github.com/microsoft/MixedReality-UXTools-Unreal)，可提供程式碼、藍圖和範例，以針對 Hololens 2 應用程式執行 UX 功能。</span><span class="sxs-lookup"><span data-stu-id="f8d88-111">[UX Tools for Unreal](https://github.com/microsoft/MixedReality-UXTools-Unreal), which provides code, blueprints, and examples to implement UX features for Hololens 2 applications.</span></span>
* <span data-ttu-id="f8d88-112">[適用于 Unreal 的圖形工具](https://github.com/microsoft/MixedReality-GraphicsTools-Unreal)，可協助改善混合現實應用程式的視覺精確度，同時維持在效能預算內。</span><span class="sxs-lookup"><span data-stu-id="f8d88-112">[Graphics Tools for Unreal](https://github.com/microsoft/MixedReality-GraphicsTools-Unreal), which helps improve the visual fidelity of Mixed Reality applications while staying within performance budgets.</span></span>

<span data-ttu-id="f8d88-113">請參閱 [GitHub 上的 MRTK 檔](https://microsoft.github.io/MixedReality-UXTools-Unreal/README.html) ，並開始使用 [UX 工具](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/Installation.html) 或 [圖形工具](https://github.com/microsoft/MixedReality-GraphicsTools-Unreal/blob/main/Docs/Installation.md) 安裝指南。</span><span class="sxs-lookup"><span data-stu-id="f8d88-113">Take a look at [MRTK's documentation on GitHub](https://microsoft.github.io/MixedReality-UXTools-Unreal/README.html) and get started with [UX Tools](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/Installation.html) or [Graphics Tools](https://github.com/microsoft/MixedReality-GraphicsTools-Unreal/blob/main/Docs/Installation.md) installation guides.</span></span>

### <a name="modular"></a><span data-ttu-id="f8d88-114">模組化</span><span class="sxs-lookup"><span data-stu-id="f8d88-114">Modular</span></span>

<span data-ttu-id="f8d88-115">我們以模組化的方式建立了 MRTK Unreal，因此您不需要將工具組的每個專案都帶到您的專案中。</span><span class="sxs-lookup"><span data-stu-id="f8d88-115">We've built MRTK Unreal in a modular way, so you don't need to take every bit of the toolkit into your project.</span></span> <span data-ttu-id="f8d88-116">您可以選擇並選擇所需的外掛程式，並在每次看到合適的時候新增或移除它們。</span><span class="sxs-lookup"><span data-stu-id="f8d88-116">You can pick and choose the plugins you need, and add or remove them whenever you see fit.</span></span> <span data-ttu-id="f8d88-117">這種方法可讓您的專案大小保持較小，而且更容易管理。</span><span class="sxs-lookup"><span data-stu-id="f8d88-117">This approach keeps your project size smaller and makes it easier to manage.</span></span>  

### <a name="performant"></a><span data-ttu-id="f8d88-118">效能</span><span class="sxs-lookup"><span data-stu-id="f8d88-118">Performant</span></span>

<span data-ttu-id="f8d88-119">使用行動平臺時，我們已將效能考慮到 MRTK Unreal。</span><span class="sxs-lookup"><span data-stu-id="f8d88-119">Working with mobile platforms, we constructed MRTK Unreal with performance in mind.</span></span> <span data-ttu-id="f8d88-120">這是非常重要的，我們想要確保工具不會與您合作。</span><span class="sxs-lookup"><span data-stu-id="f8d88-120">This is super important and we wanted to ensure that the tools aren't going to work against you.</span></span>

## <a name="project-setup"></a><span data-ttu-id="f8d88-121">專案設定</span><span class="sxs-lookup"><span data-stu-id="f8d88-121">Project setup</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="f8d88-122">下載 Unreal Engine 和 MRTK</span><span class="sxs-lookup"><span data-stu-id="f8d88-122">Download Unreal Engine and MRTK</span></span>](unreal-project-setup.md)

## <a name="see-also"></a><span data-ttu-id="f8d88-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f8d88-123">See also</span></span>

* [<span data-ttu-id="f8d88-124">安裝工具</span><span class="sxs-lookup"><span data-stu-id="f8d88-124">Install the tools</span></span>](../install-the-tools.md)
* [<span data-ttu-id="f8d88-125">使用 MRTK for Unreal 進行開發</span><span class="sxs-lookup"><span data-stu-id="f8d88-125">Developing with MRTK for Unreal</span></span>](unreal-development-overview.md)
* [<span data-ttu-id="f8d88-126">UX 工具- (GitHub) 的安裝指南 </span><span class="sxs-lookup"><span data-stu-id="f8d88-126">UX Tools - Installation guide (GitHub)</span></span>](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/Installation.html)
* [<span data-ttu-id="f8d88-127">UX 工具-檔首頁 (GitHub) </span><span class="sxs-lookup"><span data-stu-id="f8d88-127">UX Tools- Documentation home (GitHub)</span></span>](https://microsoft.github.io/MixedReality-UXTools-Unreal/README.html)
* [<span data-ttu-id="f8d88-128">圖形工具- (GitHub) 的安裝指南 </span><span class="sxs-lookup"><span data-stu-id="f8d88-128">Graphics Tools - Installation guide (GitHub)</span></span>](https://github.com/microsoft/MixedReality-GraphicsTools-Unreal/blob/main/Docs/Installation.md)
* [<span data-ttu-id="f8d88-129">圖形工具-檔首頁 (GitHub) </span><span class="sxs-lookup"><span data-stu-id="f8d88-129">Graphics Tools - Documentation home (GitHub)</span></span>](https://github.com/microsoft/MixedReality-GraphicsTools-Unreal/)