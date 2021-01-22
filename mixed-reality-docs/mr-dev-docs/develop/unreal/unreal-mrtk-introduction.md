---
title: 適用于 Unreal 的 MRTK 簡介
description: 開始使用適用于 Unreal 的混合現實工具組，必須提供新的混合現實開發人員。
author: hferrone
ms.author: v-hferrone
ms.date: 01/08/2021
ms.topic: article
ms.localizationpriority: high
keywords: Windows Mixed Reality, 測試, 混合實境工具組, MRTK 第 2 版, MRTK, 工具, SDK, HoloLens, HoloLens 2, 混合實境頭戴式裝置, windows 混合實境頭戴式裝置, 虛擬實境頭戴式裝置, 跨平台
ms.openlocfilehash: 4aa21cbee75c4c362abfd609add922ad9c922682
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/20/2021
ms.locfileid: "98584714"
---
# <a name="introducing-mrtk-for-unreal"></a><span data-ttu-id="862eb-104">適用于 Unreal 的 MRTK 簡介</span><span class="sxs-lookup"><span data-stu-id="862eb-104">Introducing MRTK for Unreal</span></span>

![MRTK](../../design/images/MRTK_UX_Hero.png)

## <a name="what-is-mixed-reality-toolkit-mrtk"></a><span data-ttu-id="862eb-106">混合實境工具組 (MRTK) 是什麼？</span><span class="sxs-lookup"><span data-stu-id="862eb-106">What is Mixed Reality Toolkit (MRTK)?</span></span>

<span data-ttu-id="862eb-107">MRTK 是一項令人驚奇的開放原始碼工具組，自 HoloLens 首次發行之後就已經存在。</span><span class="sxs-lookup"><span data-stu-id="862eb-107">MRTK is an amazing open-source toolkit that has been around since the HoloLens was first released.</span></span> <span data-ttu-id="862eb-108">沒有開發人員社群的努力，就不會達到今天的境界。</span><span class="sxs-lookup"><span data-stu-id="862eb-108">The toolkit wouldn't be where it is today without the hard work of our contributing developer community.</span></span> 

<span data-ttu-id="862eb-109">適用于 Unreal (MRTK-Unreal) 的混合現實工具組是一組元件（以外掛程式、範例和檔的形式），其設計目的是要協助使用 Unreal 引擎開發混合現實應用程式。</span><span class="sxs-lookup"><span data-stu-id="862eb-109">The Mixed Reality Toolkit for Unreal (MRTK-Unreal) is a set of components, in the form of plugins, samples and documentation, designed to help development of Mixed Reality applications using the Unreal Engine.</span></span> <span data-ttu-id="862eb-110">目前，此工具組包含：</span><span class="sxs-lookup"><span data-stu-id="862eb-110">Currently, the toolkit consists of:</span></span>
* <span data-ttu-id="862eb-111">[適用于 Unreal 的 UX 工具](https://github.com/microsoft/MixedReality-UXTools-Unreal)，可提供程式碼、藍圖和範例，以針對 Hololens 2 應用程式執行 UX 功能。</span><span class="sxs-lookup"><span data-stu-id="862eb-111">[UX Tools for Unreal](https://github.com/microsoft/MixedReality-UXTools-Unreal), which provides code, blueprints, and examples to implement UX features for Hololens 2 applications.</span></span>
* <span data-ttu-id="862eb-112">[適用于 Unreal 的圖形工具](https://github.com/microsoft/MixedReality-GraphicsTools-Unreal)，可協助改善混合現實應用程式的視覺精確度，同時維持在效能預算內。</span><span class="sxs-lookup"><span data-stu-id="862eb-112">[Graphics Tools for Unreal](https://github.com/microsoft/MixedReality-GraphicsTools-Unreal), which helps improve the visual fidelity of Mixed Reality applications while staying within performance budgets.</span></span>

<br>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4IkCG]

<span data-ttu-id="862eb-113">請參閱 [GitHub 上的 MRTK 檔](https://microsoft.github.io/MixedReality-UXTools-Unreal/README.html) ，並開始使用 [UX 工具](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/Installation.html) 或 [圖形工具](https://github.com/microsoft/MixedReality-GraphicsTools-Unreal/blob/main/Docs/Installation.md) 安裝指南。</span><span class="sxs-lookup"><span data-stu-id="862eb-113">Take a look at [MRTK's documentation on GitHub](https://microsoft.github.io/MixedReality-UXTools-Unreal/README.html) and get started with [UX Tools](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/Installation.html) or [Graphics Tools](https://github.com/microsoft/MixedReality-GraphicsTools-Unreal/blob/main/Docs/Installation.md) installation guides.</span></span>

### <a name="modular"></a><span data-ttu-id="862eb-114">模組化</span><span class="sxs-lookup"><span data-stu-id="862eb-114">Modular</span></span>

<span data-ttu-id="862eb-115">我們以模組化的方式建立了 MRTK Unreal，因此您不需要將工具組的每個專案都帶到您的專案中。</span><span class="sxs-lookup"><span data-stu-id="862eb-115">We've built MRTK Unreal in a modular way, so you don't need to take every bit of the toolkit into your project.</span></span> <span data-ttu-id="862eb-116">您可以選擇並選擇所需的外掛程式，並在每次看到合適的時候新增或移除它們。</span><span class="sxs-lookup"><span data-stu-id="862eb-116">You can pick and choose the plugins you need, and add or remove them whenever you see fit.</span></span> <span data-ttu-id="862eb-117">這種方法可讓您的專案大小保持較小，而且更容易管理。</span><span class="sxs-lookup"><span data-stu-id="862eb-117">This approach keeps your project size smaller and makes it easier to manage.</span></span>  

### <a name="performant"></a><span data-ttu-id="862eb-118">效能</span><span class="sxs-lookup"><span data-stu-id="862eb-118">Performant</span></span>

<span data-ttu-id="862eb-119">使用行動平臺時，我們已將效能考慮到 MRTK Unreal。</span><span class="sxs-lookup"><span data-stu-id="862eb-119">Working with mobile platforms, we constructed MRTK Unreal with performance in mind.</span></span> <span data-ttu-id="862eb-120">這是非常重要的，我們想要確保工具不會與您合作。</span><span class="sxs-lookup"><span data-stu-id="862eb-120">This is super important and we wanted to ensure that the tools aren't going to work against you.</span></span>

## <a name="see-also"></a><span data-ttu-id="862eb-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="862eb-121">See also</span></span>

* [<span data-ttu-id="862eb-122">安裝工具</span><span class="sxs-lookup"><span data-stu-id="862eb-122">Install the tools</span></span>](../install-the-tools.md)
* [<span data-ttu-id="862eb-123">使用 MRTK for Unreal 進行開發</span><span class="sxs-lookup"><span data-stu-id="862eb-123">Developing with MRTK for Unreal</span></span>](unreal-development-overview.md)
* [<span data-ttu-id="862eb-124">UX 工具- (GitHub) 的安裝指南 </span><span class="sxs-lookup"><span data-stu-id="862eb-124">UX Tools - Installation guide (GitHub)</span></span>](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/Installation.html)
* [<span data-ttu-id="862eb-125">UX 工具-檔首頁 (GitHub) </span><span class="sxs-lookup"><span data-stu-id="862eb-125">UX Tools- Documentation home (GitHub)</span></span>](https://microsoft.github.io/MixedReality-UXTools-Unreal/README.html)
* [<span data-ttu-id="862eb-126">圖形工具- (GitHub) 的安裝指南 </span><span class="sxs-lookup"><span data-stu-id="862eb-126">Graphics Tools - Installation guide (GitHub)</span></span>](https://github.com/microsoft/MixedReality-GraphicsTools-Unreal/blob/main/Docs/Installation.md)
* [<span data-ttu-id="862eb-127">圖形工具-檔首頁 (GitHub) </span><span class="sxs-lookup"><span data-stu-id="862eb-127">Graphics Tools - Documentation home (GitHub)</span></span>](https://github.com/microsoft/MixedReality-GraphicsTools-Unreal/)