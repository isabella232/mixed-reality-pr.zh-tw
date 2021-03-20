---
title: 藍圖
description: 概述 MRTK 藍圖的檔。
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
ms.localizationpriority: medium
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: 49471f555e9d397bffd37bb6d1cc7f22c6e37bca
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104684351"
---
# <a name="roadmap"></a><span data-ttu-id="0dd39-104">藍圖</span><span class="sxs-lookup"><span data-stu-id="0dd39-104">Roadmap</span></span>

<span data-ttu-id="0dd39-105">本檔概述混合現實工具組的藍圖。</span><span class="sxs-lookup"><span data-stu-id="0dd39-105">This document outlines the roadmap of the Mixed Reality Toolkit.</span></span>

## <a name="current-release"></a><span data-ttu-id="0dd39-106">目前的版本</span><span class="sxs-lookup"><span data-stu-id="0dd39-106">Current release</span></span>

[<span data-ttu-id="0dd39-107">Microsoft Mixed Reality 工具組 v 2.3。0</span><span class="sxs-lookup"><span data-stu-id="0dd39-107">Microsoft Mixed Reality Toolkit v2.3.0</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases/tag/v2.3.0)

## <a name="upcoming-releases"></a><span data-ttu-id="0dd39-108">即將推出的版本</span><span class="sxs-lookup"><span data-stu-id="0dd39-108">Upcoming releases</span></span>

| <span data-ttu-id="0dd39-109">產品</span><span class="sxs-lookup"><span data-stu-id="0dd39-109">Product</span></span> | <span data-ttu-id="0dd39-110">Description</span><span class="sxs-lookup"><span data-stu-id="0dd39-110">Description</span></span> | <span data-ttu-id="0dd39-111">時間表</span><span class="sxs-lookup"><span data-stu-id="0dd39-111">Timeline</span></span> | <span data-ttu-id="0dd39-112">專案面板</span><span class="sxs-lookup"><span data-stu-id="0dd39-112">Project board</span></span> |
| --- | --- | --- | --- |
| [<span data-ttu-id="0dd39-113">MRTK V 2。5</span><span class="sxs-lookup"><span data-stu-id="0dd39-113">MRTK V2.5</span></span>](#250) | <span data-ttu-id="0dd39-114">MRTK 的下一個反復專案</span><span class="sxs-lookup"><span data-stu-id="0dd39-114">Next iteration of MRTK</span></span> | <span data-ttu-id="0dd39-115">TBD 2020</span><span class="sxs-lookup"><span data-stu-id="0dd39-115">TBD 2020</span></span> | [https://github.com/microsoft/MixedRealityToolkit-Unity/milestone/12](https://github.com/microsoft/MixedRealityToolkit-Unity/milestone/12) |

<span data-ttu-id="0dd39-116">版本是以主題為中心， (例如：大型功能區) ，而且排程大約每隔8周進行。</span><span class="sxs-lookup"><span data-stu-id="0dd39-116">Releases are centered around themes (ex: large feature areas) and are scheduled to occur approximately every 8 weeks.</span></span>

<span data-ttu-id="0dd39-117">您可以在 [GitHub 里程碑頁面](https://github.com/Microsoft/MixedRealityToolkit-Unity/milestones)上找到發行詳細資料，包括待處理專案（backlog）。</span><span class="sxs-lookup"><span data-stu-id="0dd39-117">Release details, including backlog items, can be found on the [GitHub milestone pages](https://github.com/Microsoft/MixedRealityToolkit-Unity/milestones).</span></span> <span data-ttu-id="0dd39-118">您也可以在 [GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/issues)上找到一組完整的開啟問題。</span><span class="sxs-lookup"><span data-stu-id="0dd39-118">The complete set of open issues can also be found on [GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/issues).</span></span>

## <a name="mixed-reality-toolkit-mrtk-roadmap"></a><span data-ttu-id="0dd39-119">混合現實工具組 (MRTK) 藍圖</span><span class="sxs-lookup"><span data-stu-id="0dd39-119">Mixed Reality Toolkit (MRTK) roadmap</span></span>

<span data-ttu-id="0dd39-120">「混合現實」工具組是一項全新的產品，建基於設計的跨 MR/AR/VR/XR 平臺。</span><span class="sxs-lookup"><span data-stu-id="0dd39-120">The Mixed Reality Toolkit is an all-new product, built to be cross MR/AR/VR/XR platform by design.</span></span> <span data-ttu-id="0dd39-121">有兩個已規劃的發行前版本，混合現實工具組將成為主要產品。</span><span class="sxs-lookup"><span data-stu-id="0dd39-121">There are two planned pre-releases after which the Mixed Reality Toolkit will become the primary product.</span></span>

<span data-ttu-id="0dd39-122">混合現實工具組將需要 Unity 2018.4。</span><span class="sxs-lookup"><span data-stu-id="0dd39-122">The Mixed Reality Toolkit will require Unity 2018.4.</span></span>

> <span data-ttu-id="0dd39-123">當 Unity 釋出 LTS (長期支援) 產品時，Mixed Reality 工具組將會更新為 LTS 版本。</span><span class="sxs-lookup"><span data-stu-id="0dd39-123">When Unity releases an LTS (Long Term Support) product, the Mixed Reality Toolkit will update to the LTS release.</span></span> <span data-ttu-id="0dd39-124">MRTK 也會在 MRTK 發行時，支援 Unity 的最新非 Beta (例如： 2019.1) tech 分支版本。</span><span class="sxs-lookup"><span data-stu-id="0dd39-124">MRTK will also support the latest non-beta (ex: 2019.1) tech branch version of Unity, at the time at which MRTK was released.</span></span>

### <a name="250"></a><span data-ttu-id="0dd39-125">2.5.0</span><span class="sxs-lookup"><span data-stu-id="0dd39-125">2.5.0</span></span>

<span data-ttu-id="0dd39-126">如需版本的最新狀態，請造訪 [里程碑頁面]( https://github.com/microsoft/MixedRealityToolkit-Unity/milestone/12)。</span><span class="sxs-lookup"><span data-stu-id="0dd39-126">For the latest status of the release, please visit the [milestone page]( https://github.com/microsoft/MixedRealityToolkit-Unity/milestone/12).</span></span>

<span data-ttu-id="0dd39-127">狀態：開發中</span><span class="sxs-lookup"><span data-stu-id="0dd39-127">Status: In development</span></span>

<span data-ttu-id="0dd39-128">時間軸： TBD 2020</span><span class="sxs-lookup"><span data-stu-id="0dd39-128">Timeline: TBD 2020</span></span>

<span data-ttu-id="0dd39-129">主題：</span><span class="sxs-lookup"><span data-stu-id="0dd39-129">Themes:</span></span>

- <span data-ttu-id="0dd39-130">Stability</span><span class="sxs-lookup"><span data-stu-id="0dd39-130">Stability</span></span>
- <span data-ttu-id="0dd39-131">開發人員教育</span><span class="sxs-lookup"><span data-stu-id="0dd39-131">Developer education</span></span>
- <span data-ttu-id="0dd39-132">使用者體驗</span><span class="sxs-lookup"><span data-stu-id="0dd39-132">User Experience</span></span>

<span data-ttu-id="0dd39-133">**穩定性**</span><span class="sxs-lookup"><span data-stu-id="0dd39-133">**Stability**</span></span>

<span data-ttu-id="0dd39-134">品質和穩定性是此與所有 Microsoft Mixed Reality 工具組版本的最高優先順序。</span><span class="sxs-lookup"><span data-stu-id="0dd39-134">Quality and stability are the top priority for this and all Microsoft Mixed Reality Toolkit releases.</span></span> <span data-ttu-id="0dd39-135">我們會持續優先處理影響 MRTK 元件穩定性的客戶和合作夥伴問題。</span><span class="sxs-lookup"><span data-stu-id="0dd39-135">We will continue to prioritize customer and partner issues that impact the stability of MRTK components.</span></span>

<span data-ttu-id="0dd39-136">**開發人員教育**</span><span class="sxs-lookup"><span data-stu-id="0dd39-136">**Developer education**</span></span>

<span data-ttu-id="0dd39-137">[開發人員檔](https://microsoft.github.io/MixedRealityToolkit-Unity) 和範例場景（例如穩定性）是 MRTK 團隊的持續性優先。</span><span class="sxs-lookup"><span data-stu-id="0dd39-137">[Developer documentation](https://microsoft.github.io/MixedRealityToolkit-Unity) and example scenes are, like stability, an ongoing priority for the MRTK team.</span></span>

<span data-ttu-id="0dd39-138">**使用者體驗**</span><span class="sxs-lookup"><span data-stu-id="0dd39-138">**User Experience**</span></span>

- <span data-ttu-id="0dd39-139">錯誤修正</span><span class="sxs-lookup"><span data-stu-id="0dd39-139">Bug fixes</span></span>
- <span data-ttu-id="0dd39-140">HoloLens Shell 同位</span><span class="sxs-lookup"><span data-stu-id="0dd39-140">HoloLens Shell parity</span></span>
- <span data-ttu-id="0dd39-141">即將畢業實驗性功能</span><span class="sxs-lookup"><span data-stu-id="0dd39-141">Graduating experimental features</span></span>
- <span data-ttu-id="0dd39-142">測試以確保功能不會回歸</span><span class="sxs-lookup"><span data-stu-id="0dd39-142">Tests to ensure features do not regress</span></span>

## <a name="backlog"></a><span data-ttu-id="0dd39-143">Backlog</span><span class="sxs-lookup"><span data-stu-id="0dd39-143">Backlog</span></span>

<span data-ttu-id="0dd39-144">下列清單強調 MRTK 小組打算採用的一些主要投資。</span><span class="sxs-lookup"><span data-stu-id="0dd39-144">The following list highlights some of the key investments the MRTK team intends to pursue.</span></span>

- <span data-ttu-id="0dd39-145">平臺擴充</span><span class="sxs-lookup"><span data-stu-id="0dd39-145">Platform expansion</span></span>
- <span data-ttu-id="0dd39-146">擴充性</span><span class="sxs-lookup"><span data-stu-id="0dd39-146">Extensibility</span></span>
- <span data-ttu-id="0dd39-147">模組 化</span><span class="sxs-lookup"><span data-stu-id="0dd39-147">Modularity</span></span>
- <span data-ttu-id="0dd39-148">協助工具功能</span><span class="sxs-lookup"><span data-stu-id="0dd39-148">Accessibility features</span></span>
- <span data-ttu-id="0dd39-149">全球化增強功能</span><span class="sxs-lookup"><span data-stu-id="0dd39-149">Globalization enhancements</span></span>
- <span data-ttu-id="0dd39-150">包裝</span><span class="sxs-lookup"><span data-stu-id="0dd39-150">Packaging</span></span>
- <span data-ttu-id="0dd39-151">雲端服務支援</span><span class="sxs-lookup"><span data-stu-id="0dd39-151">Cloud service support</span></span>
- <span data-ttu-id="0dd39-152">工具</span><span class="sxs-lookup"><span data-stu-id="0dd39-152">Tools</span></span>
