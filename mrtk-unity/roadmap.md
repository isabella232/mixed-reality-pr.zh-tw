---
title: 藍圖
description: 概述 MRTK 藍圖的檔。
author: polar-kev
ms.author: kesemple
ms.date: 03/03/2021
ms.localizationpriority: high
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK
ms.openlocfilehash: 53cf7ffe786ea5cb650bfd04ff8d42d5bdd7cf09
ms.sourcegitcommit: 7a8fa3257a13635ddad77d963e49440f62c19774
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2021
ms.locfileid: "101883123"
---
# <a name="roadmap"></a><span data-ttu-id="25e88-104">藍圖</span><span class="sxs-lookup"><span data-stu-id="25e88-104">Roadmap</span></span>

<span data-ttu-id="25e88-105">本檔概述混合現實工具組的藍圖。</span><span class="sxs-lookup"><span data-stu-id="25e88-105">This document outlines the roadmap of the Mixed Reality Toolkit.</span></span> <span data-ttu-id="25e88-106">請注意，下列各項反映的是開發中的工作，而目標日期會反映預估值。</span><span class="sxs-lookup"><span data-stu-id="25e88-106">Please note that the following reflects work that is in development and target dates reflect estimates.</span></span>

## <a name="current-release"></a><span data-ttu-id="25e88-107">目前的版本</span><span class="sxs-lookup"><span data-stu-id="25e88-107">Current release</span></span>

<span data-ttu-id="25e88-108">Microsoft Mixed Reality 工具組2.6 版</span><span class="sxs-lookup"><span data-stu-id="25e88-108">Microsoft Mixed Reality Toolkit v2.6</span></span>

## <a name="upcoming-releases"></a><span data-ttu-id="25e88-109">即將推出的版本</span><span class="sxs-lookup"><span data-stu-id="25e88-109">Upcoming releases</span></span>

| <span data-ttu-id="25e88-110">產品</span><span class="sxs-lookup"><span data-stu-id="25e88-110">Product</span></span> | <span data-ttu-id="25e88-111">描述</span><span class="sxs-lookup"><span data-stu-id="25e88-111">Description</span></span> | <span data-ttu-id="25e88-112">時間表</span><span class="sxs-lookup"><span data-stu-id="25e88-112">Timeline</span></span> | <span data-ttu-id="25e88-113">專案面板</span><span class="sxs-lookup"><span data-stu-id="25e88-113">Project board</span></span> |
| --- | --- | --- | --- |
| [<span data-ttu-id="25e88-114">MRTK V 2。7</span><span class="sxs-lookup"><span data-stu-id="25e88-114">MRTK V2.7</span></span>](#270) | <span data-ttu-id="25e88-115">MRTK 的下一個反復專案</span><span class="sxs-lookup"><span data-stu-id="25e88-115">Next iteration of MRTK</span></span> | <span data-ttu-id="25e88-116">2021 年 5 月</span><span class="sxs-lookup"><span data-stu-id="25e88-116">May 2021</span></span> | https://github.com/microsoft/MixedRealityToolkit-Unity/milestone/14 |

<span data-ttu-id="25e88-117">版本是以主題為中心， (例如：大型功能區) ，而且排定為大約每8-12 周進行。</span><span class="sxs-lookup"><span data-stu-id="25e88-117">Releases are centered around themes (ex: large feature areas) and are scheduled to occur approximately every 8-12 weeks.</span></span>

<span data-ttu-id="25e88-118">您可以在 [GitHub 里程碑頁面](https://github.com/Microsoft/MixedRealityToolkit-Unity/milestones)上找到發行詳細資料，包括待處理專案（backlog）。</span><span class="sxs-lookup"><span data-stu-id="25e88-118">Release details, including backlog items, can be found on the [GitHub milestone pages](https://github.com/Microsoft/MixedRealityToolkit-Unity/milestones).</span></span> <span data-ttu-id="25e88-119">您也可以在 [GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/issues)上找到一組完整的開啟問題。</span><span class="sxs-lookup"><span data-stu-id="25e88-119">The complete set of open issues can also be found on [GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/issues).</span></span>

## <a name="mixed-reality-toolkit-mrtk-roadmap"></a><span data-ttu-id="25e88-120">混合現實工具組 (MRTK) 藍圖</span><span class="sxs-lookup"><span data-stu-id="25e88-120">Mixed Reality Toolkit (MRTK) roadmap</span></span>

<span data-ttu-id="25e88-121">混合的現實工具組建基於設計的跨 MR/AR/VR/XR 平臺。</span><span class="sxs-lookup"><span data-stu-id="25e88-121">The Mixed Reality Toolkit is built to be cross MR/AR/VR/XR platform by design.</span></span> <span data-ttu-id="25e88-122">此工具組目前支援 Unity 2019.4. x 和 Unity 2018.4. x。</span><span class="sxs-lookup"><span data-stu-id="25e88-122">The toolkit currently supports Unity 2019.4.x and Unity 2018.4.x.</span></span>

> <span data-ttu-id="25e88-123">當 Unity 釋出 LTS (長期支援) 產品時，Mixed Reality 工具組將會更新為 LTS 版本。</span><span class="sxs-lookup"><span data-stu-id="25e88-123">When Unity releases an LTS (Long Term Support) product, the Mixed Reality Toolkit will update to the LTS release.</span></span> <span data-ttu-id="25e88-124">雖然混合現實工具組是在最新的非 Beta 版 (（例如： 2020.1) tech 分支版本的 Unity）上執行，但並未正式支援。</span><span class="sxs-lookup"><span data-stu-id="25e88-124">Although the Mixed Reality Toolkit runs on the latest non-beta (ex: 2020.1) tech branch version of Unity, it is not officially supported.</span></span>

### <a name="270"></a><span data-ttu-id="25e88-125">2.7.0</span><span class="sxs-lookup"><span data-stu-id="25e88-125">2.7.0</span></span>

<span data-ttu-id="25e88-126">我們目前正在規劃2.7.0 版本，且即將有更多更新可供您使用！</span><span class="sxs-lookup"><span data-stu-id="25e88-126">We are currently planning the 2.7.0 release and will have more updates for you soon!</span></span>
<span data-ttu-id="25e88-127">如需版本的最新狀態，請造訪 [里程碑頁面](https://github.com/microsoft/MixedRealityToolkit-Unity/milestone/14)。</span><span class="sxs-lookup"><span data-stu-id="25e88-127">For the latest status of the release, please visit the [milestone page](https://github.com/microsoft/MixedRealityToolkit-Unity/milestone/14).</span></span>

<span data-ttu-id="25e88-128">狀態：規劃</span><span class="sxs-lookup"><span data-stu-id="25e88-128">Status: Planning</span></span>

<span data-ttu-id="25e88-129">目標時程表：5月2021</span><span class="sxs-lookup"><span data-stu-id="25e88-129">Target Timeline: May 2021</span></span>

<span data-ttu-id="25e88-130">主題：</span><span class="sxs-lookup"><span data-stu-id="25e88-130">Themes:</span></span>

- <span data-ttu-id="25e88-131">Stability</span><span class="sxs-lookup"><span data-stu-id="25e88-131">Stability</span></span> 
- <span data-ttu-id="25e88-132">平臺擴充： OpenXR</span><span class="sxs-lookup"><span data-stu-id="25e88-132">Platform Expansion: OpenXR</span></span>
- <span data-ttu-id="25e88-133">使用者體驗</span><span class="sxs-lookup"><span data-stu-id="25e88-133">User Experience</span></span>
- <span data-ttu-id="25e88-134">開發人員教育</span><span class="sxs-lookup"><span data-stu-id="25e88-134">Developer Education</span></span>
- <span data-ttu-id="25e88-135">包裝</span><span class="sxs-lookup"><span data-stu-id="25e88-135">Packaging</span></span>

<span data-ttu-id="25e88-136">**穩定性**</span><span class="sxs-lookup"><span data-stu-id="25e88-136">**Stability**</span></span>

<span data-ttu-id="25e88-137">品質和穩定性是此與所有 Microsoft Mixed Reality 工具組版本的最高優先順序。</span><span class="sxs-lookup"><span data-stu-id="25e88-137">Quality and stability are the top priority for this and all Microsoft Mixed Reality Toolkit releases.</span></span> <span data-ttu-id="25e88-138">我們會持續優先處理影響 MRTK 元件穩定性的客戶和合作夥伴問題。</span><span class="sxs-lookup"><span data-stu-id="25e88-138">We will continue to prioritize customer and partner issues that impact the stability of MRTK components.</span></span>

<span data-ttu-id="25e88-139">**平臺擴充： OpenXR**</span><span class="sxs-lookup"><span data-stu-id="25e88-139">**Platform Expansion: OpenXR**</span></span>

<span data-ttu-id="25e88-140">MRTK 團隊透過 [OpenXR](https://techcommunity.microsoft.com/t5/mixed-reality-blog/moving-forward-to-openxr/ba-p/1825672)支援混合現實的開放未來。</span><span class="sxs-lookup"><span data-stu-id="25e88-140">The MRTK team supports the open future of mixed reality through [OpenXR](https://techcommunity.microsoft.com/t5/mixed-reality-blog/moving-forward-to-openxr/ba-p/1825672).</span></span> <span data-ttu-id="25e88-141">OpenXR 的支援目前正在開發中，並在 MRTK 2.5.2 中發行了初始預覽支援。</span><span class="sxs-lookup"><span data-stu-id="25e88-141">Support for OpenXR is currently under development, with initial preview support released in MRTK 2.5.2.</span></span>

<span data-ttu-id="25e88-142">**使用者體驗**</span><span class="sxs-lookup"><span data-stu-id="25e88-142">**User Experience**</span></span>

<span data-ttu-id="25e88-143">我們正在聆聽您對 MRTK 的意見反應，並持續規劃：</span><span class="sxs-lookup"><span data-stu-id="25e88-143">We're listening to your feedback about MRTK and have continued plans for:</span></span>

- <span data-ttu-id="25e88-144">錯誤修正</span><span class="sxs-lookup"><span data-stu-id="25e88-144">Bug fixes</span></span>
- <span data-ttu-id="25e88-145">讓 MRTK UX 控制項更容易瞭解</span><span class="sxs-lookup"><span data-stu-id="25e88-145">Making MRTK UX controls easier to understand</span></span>
- <span data-ttu-id="25e88-146">HoloLens Shell 同位</span><span class="sxs-lookup"><span data-stu-id="25e88-146">HoloLens Shell parity</span></span>
- <span data-ttu-id="25e88-147">測試以確保功能不會回歸</span><span class="sxs-lookup"><span data-stu-id="25e88-147">Tests to ensure features do not regress</span></span>

<span data-ttu-id="25e88-148">**開發人員教育**</span><span class="sxs-lookup"><span data-stu-id="25e88-148">**Developer Education**</span></span>

<span data-ttu-id="25e88-149">我們已將開發人員檔從 Github 遷移至新的檔平臺！</span><span class="sxs-lookup"><span data-stu-id="25e88-149">We've migrated our developer documentation from Github to a new docs platform!</span></span> <span data-ttu-id="25e88-150">我們想要聽取您的意見反應，讓我們可以繼續改善開發人員的檔體驗。</span><span class="sxs-lookup"><span data-stu-id="25e88-150">We want to hear your feedback so we can continue to improve our developer documentation experience.</span></span>
<span data-ttu-id="25e88-151">我們目前有 [MRTK 的教學](https://docs.microsoft.com/windows/mixed-reality/develop/unity/tutorials) 課程存在於不同的混合現實檔區段中。我們會將這些教學課程與 MRTK 檔的其餘部分一起遷移。</span><span class="sxs-lookup"><span data-stu-id="25e88-151">We currently have [MRTK tutorials](https://docs.microsoft.com/windows/mixed-reality/develop/unity/tutorials) that live in a different section of Mixed Reality docs. We will be migrating these tutorials to live with the rest of the MRTK documentation.</span></span> 

<span data-ttu-id="25e88-152">**包裝**</span><span class="sxs-lookup"><span data-stu-id="25e88-152">**Packaging**</span></span>

<span data-ttu-id="25e88-153">「 [混合現實」功能工具](https://docs.microsoft.com/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool) 是一種新方法，可讓開發人員探索、更新和新增混合現實功能套件至 Unity 專案。</span><span class="sxs-lookup"><span data-stu-id="25e88-153">The [Mixed Reality Feature Tool](https://docs.microsoft.com/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool) is a new way for developers to discover, update, and add Mixed Reality feature packages into Unity projects.</span></span> <span data-ttu-id="25e88-154">您可以依名稱或類別搜尋套件、查看其相依性，甚至在匯入之前查看專案資訊清單檔的建議變更。</span><span class="sxs-lookup"><span data-stu-id="25e88-154">You can search packages by name or category, see their dependencies, and even view proposed changes to your projects manifest file before importing.</span></span> <span data-ttu-id="25e88-155">我們想要在回應功能要求和 bug 時，對混合現實功能工具進行更新。</span><span class="sxs-lookup"><span data-stu-id="25e88-155">We intend to make updates to the Mixed Reality Feature Tool as we respond to feature requests and bugs.</span></span>

## <a name="backlog"></a><span data-ttu-id="25e88-156">Backlog</span><span class="sxs-lookup"><span data-stu-id="25e88-156">Backlog</span></span>

<span data-ttu-id="25e88-157">下列清單強調 MRTK 小組打算採用的一些主要投資。</span><span class="sxs-lookup"><span data-stu-id="25e88-157">The following list highlights some of the key investments the MRTK team intends to pursue.</span></span>

- <span data-ttu-id="25e88-158">平臺擴充</span><span class="sxs-lookup"><span data-stu-id="25e88-158">Platform expansion</span></span>
- <span data-ttu-id="25e88-159">擴充性</span><span class="sxs-lookup"><span data-stu-id="25e88-159">Extensibility</span></span>
- <span data-ttu-id="25e88-160">模組 化</span><span class="sxs-lookup"><span data-stu-id="25e88-160">Modularity</span></span>
- <span data-ttu-id="25e88-161">協助工具功能</span><span class="sxs-lookup"><span data-stu-id="25e88-161">Accessibility features</span></span>
- <span data-ttu-id="25e88-162">全球化增強功能</span><span class="sxs-lookup"><span data-stu-id="25e88-162">Globalization enhancements</span></span>
- <span data-ttu-id="25e88-163">雲端服務支援</span><span class="sxs-lookup"><span data-stu-id="25e88-163">Cloud service support</span></span>
- <span data-ttu-id="25e88-164">工具</span><span class="sxs-lookup"><span data-stu-id="25e88-164">Tools</span></span>
