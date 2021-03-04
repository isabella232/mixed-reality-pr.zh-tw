---
title: 藍圖
description: 概述 MRTK 藍圖的檔。
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: 09582407aab71424225dd8762f080ac162a0aaa5
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/03/2021
ms.locfileid: "101780998"
---
# <a name="roadmap"></a><span data-ttu-id="efee4-104">藍圖</span><span class="sxs-lookup"><span data-stu-id="efee4-104">Roadmap</span></span>

<span data-ttu-id="efee4-105">本檔概述混合現實工具組的藍圖。</span><span class="sxs-lookup"><span data-stu-id="efee4-105">This document outlines the roadmap of the Mixed Reality Toolkit.</span></span> <span data-ttu-id="efee4-106">請注意，下列各項反映的是開發中的工作，而目標日期會反映預估值。</span><span class="sxs-lookup"><span data-stu-id="efee4-106">Please note that the following reflects work that is in development and target dates reflect estimates.</span></span>

## <a name="current-release"></a><span data-ttu-id="efee4-107">目前的版本</span><span class="sxs-lookup"><span data-stu-id="efee4-107">Current release</span></span>

[<span data-ttu-id="efee4-108">Microsoft Mixed Reality 工具組 v1。1</span><span class="sxs-lookup"><span data-stu-id="efee4-108">Microsoft Mixed Reality Toolkit v2.5.1</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases/tag/v2.5.1)

## <a name="upcoming-releases"></a><span data-ttu-id="efee4-109">即將推出的版本</span><span class="sxs-lookup"><span data-stu-id="efee4-109">Upcoming releases</span></span>

| <span data-ttu-id="efee4-110">產品</span><span class="sxs-lookup"><span data-stu-id="efee4-110">Product</span></span> | <span data-ttu-id="efee4-111">描述</span><span class="sxs-lookup"><span data-stu-id="efee4-111">Description</span></span> | <span data-ttu-id="efee4-112">時間表</span><span class="sxs-lookup"><span data-stu-id="efee4-112">Timeline</span></span> | <span data-ttu-id="efee4-113">專案面板</span><span class="sxs-lookup"><span data-stu-id="efee4-113">Project board</span></span> |
| --- | --- | --- | --- |
| [<span data-ttu-id="efee4-114">MRTK 2.6 版</span><span class="sxs-lookup"><span data-stu-id="efee4-114">MRTK V2.6</span></span>](#260) | <span data-ttu-id="efee4-115">MRTK 的下一個反復專案</span><span class="sxs-lookup"><span data-stu-id="efee4-115">Next iteration of MRTK</span></span> | <span data-ttu-id="efee4-116">2021 年 1 月</span><span class="sxs-lookup"><span data-stu-id="efee4-116">January 2021</span></span> | [https://github.com/microsoft/MixedRealityToolkit-Unity/milestone/13](https://github.com/microsoft/MixedRealityToolkit-Unity/milestone/13) |

<span data-ttu-id="efee4-117">版本是以主題為中心， (例如：大型功能區) ，而且排定為大約每8-12 周進行。</span><span class="sxs-lookup"><span data-stu-id="efee4-117">Releases are centered around themes (ex: large feature areas) and are scheduled to occur approximately every 8-12 weeks.</span></span>

<span data-ttu-id="efee4-118">您可以在 [GitHub 里程碑頁面](https://github.com/Microsoft/MixedRealityToolkit-Unity/milestones)上找到發行詳細資料，包括待處理專案（backlog）。</span><span class="sxs-lookup"><span data-stu-id="efee4-118">Release details, including backlog items, can be found on the [GitHub milestone pages](https://github.com/Microsoft/MixedRealityToolkit-Unity/milestones).</span></span> <span data-ttu-id="efee4-119">您也可以在 [GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/issues)上找到一組完整的開啟問題。</span><span class="sxs-lookup"><span data-stu-id="efee4-119">The complete set of open issues can also be found on [GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/issues).</span></span>

## <a name="mixed-reality-toolkit-mrtk-roadmap"></a><span data-ttu-id="efee4-120">混合現實工具組 (MRTK) 藍圖</span><span class="sxs-lookup"><span data-stu-id="efee4-120">Mixed Reality Toolkit (MRTK) roadmap</span></span>

<span data-ttu-id="efee4-121">混合的現實工具組建基於設計的跨 MR/AR/VR/XR 平臺。</span><span class="sxs-lookup"><span data-stu-id="efee4-121">The Mixed Reality Toolkit is built to be cross MR/AR/VR/XR platform by design.</span></span> <span data-ttu-id="efee4-122">此工具組目前支援 Unity 2019.4. x 和 Unity 2018.4. x。</span><span class="sxs-lookup"><span data-stu-id="efee4-122">The toolkit currently supports Unity 2019.4.x and Unity 2018.4.x.</span></span>

> <span data-ttu-id="efee4-123">當 Unity 釋出 LTS (長期支援) 產品時，Mixed Reality 工具組將會更新為 LTS 版本。</span><span class="sxs-lookup"><span data-stu-id="efee4-123">When Unity releases an LTS (Long Term Support) product, the Mixed Reality Toolkit will update to the LTS release.</span></span> <span data-ttu-id="efee4-124">雖然混合現實工具組是在最新的非 Beta 版 (（例如： 2020.1) tech 分支版本的 Unity）上執行，但並未正式支援。</span><span class="sxs-lookup"><span data-stu-id="efee4-124">Although the Mixed Reality Toolkit runs on the latest non-beta (ex: 2020.1) tech branch version of Unity, it is not officially supported.</span></span>

### <a name="260"></a><span data-ttu-id="efee4-125">2.6.0</span><span class="sxs-lookup"><span data-stu-id="efee4-125">2.6.0</span></span>

<span data-ttu-id="efee4-126">如需版本的最新狀態，請造訪 [里程碑頁面]( https://github.com/microsoft/MixedRealityToolkit-Unity/milestone/13)。</span><span class="sxs-lookup"><span data-stu-id="efee4-126">For the latest status of the release, please visit the [milestone page]( https://github.com/microsoft/MixedRealityToolkit-Unity/milestone/13).</span></span>

<span data-ttu-id="efee4-127">狀態：開發中</span><span class="sxs-lookup"><span data-stu-id="efee4-127">Status: In development</span></span>

<span data-ttu-id="efee4-128">目標時間軸：2021年1月</span><span class="sxs-lookup"><span data-stu-id="efee4-128">Target Timeline: January 2021</span></span>

<span data-ttu-id="efee4-129">主題：</span><span class="sxs-lookup"><span data-stu-id="efee4-129">Themes:</span></span>

- <span data-ttu-id="efee4-130">Stability</span><span class="sxs-lookup"><span data-stu-id="efee4-130">Stability</span></span>
- <span data-ttu-id="efee4-131">使用者體驗</span><span class="sxs-lookup"><span data-stu-id="efee4-131">User Experience</span></span>
- <span data-ttu-id="efee4-132">平臺擴充： OpenXR</span><span class="sxs-lookup"><span data-stu-id="efee4-132">Platform Expansion: OpenXR</span></span>
- <span data-ttu-id="efee4-133">開發人員教育</span><span class="sxs-lookup"><span data-stu-id="efee4-133">Developer Education</span></span>
- <span data-ttu-id="efee4-134">包裝</span><span class="sxs-lookup"><span data-stu-id="efee4-134">Packaging</span></span>

<span data-ttu-id="efee4-135">**穩定性**</span><span class="sxs-lookup"><span data-stu-id="efee4-135">**Stability**</span></span>

<span data-ttu-id="efee4-136">品質和穩定性是此與所有 Microsoft Mixed Reality 工具組版本的最高優先順序。</span><span class="sxs-lookup"><span data-stu-id="efee4-136">Quality and stability are the top priority for this and all Microsoft Mixed Reality Toolkit releases.</span></span> <span data-ttu-id="efee4-137">我們會持續優先處理影響 MRTK 元件穩定性的客戶和合作夥伴問題。</span><span class="sxs-lookup"><span data-stu-id="efee4-137">We will continue to prioritize customer and partner issues that impact the stability of MRTK components.</span></span>

<span data-ttu-id="efee4-138">**使用者體驗**</span><span class="sxs-lookup"><span data-stu-id="efee4-138">**User Experience**</span></span>

<span data-ttu-id="efee4-139">我們正在聆聽您對 MRTK 的意見反應，並持續規劃：</span><span class="sxs-lookup"><span data-stu-id="efee4-139">We're listening to your feedback about MRTK and have continued plans for:</span></span>

- <span data-ttu-id="efee4-140">錯誤修正</span><span class="sxs-lookup"><span data-stu-id="efee4-140">Bug fixes</span></span>
- <span data-ttu-id="efee4-141">讓 MRTK UX 控制項更容易瞭解</span><span class="sxs-lookup"><span data-stu-id="efee4-141">Making MRTK UX controls easier to understand</span></span>
- <span data-ttu-id="efee4-142">HoloLens Shell 同位</span><span class="sxs-lookup"><span data-stu-id="efee4-142">HoloLens Shell parity</span></span>
- <span data-ttu-id="efee4-143">測試以確保功能不會回歸</span><span class="sxs-lookup"><span data-stu-id="efee4-143">Tests to ensure features do not regress</span></span>

<span data-ttu-id="efee4-144">**平臺擴充： OpenXR**</span><span class="sxs-lookup"><span data-stu-id="efee4-144">**Platform Expansion: OpenXR**</span></span>

<span data-ttu-id="efee4-145">MRTK 團隊透過 [OpenXR](https://techcommunity.microsoft.com/t5/mixed-reality-blog/moving-forward-to-openxr/ba-p/1825672)支援混合現實的開放未來。</span><span class="sxs-lookup"><span data-stu-id="efee4-145">The MRTK team supports the open future of mixed reality through [OpenXR](https://techcommunity.microsoft.com/t5/mixed-reality-blog/moving-forward-to-openxr/ba-p/1825672).</span></span> <span data-ttu-id="efee4-146">OpenXR 的支援目前正在開發中。</span><span class="sxs-lookup"><span data-stu-id="efee4-146">Support for OpenXR is currently under development.</span></span>

<span data-ttu-id="efee4-147">**開發人員教育**</span><span class="sxs-lookup"><span data-stu-id="efee4-147">**Developer Education**</span></span>

<span data-ttu-id="efee4-148">[開發人員檔](https://microsoft.github.io/MixedRealityToolkit-Unity) 和範例場景是 MRTK 團隊的持續性優先。</span><span class="sxs-lookup"><span data-stu-id="efee4-148">[Developer documentation](https://microsoft.github.io/MixedRealityToolkit-Unity) and example scenes are an ongoing priority for the MRTK team.</span></span>

<span data-ttu-id="efee4-149">藉由持續投資 [MRTK 教學](https://docs.microsoft.com/windows/mixed-reality/develop/unity/tutorials)課程，MRTK 小組致力於加速開發人員的使用者入門體驗，並改進如何運用 Azure 服務和其他延伸模組搭配 MRTK 的指示。</span><span class="sxs-lookup"><span data-stu-id="efee4-149">With continued investments in [MRTK tutorials](https://docs.microsoft.com/windows/mixed-reality/develop/unity/tutorials), the MRTK team seeks to accelerate the getting started experience for developers and improve instructions on how to leverage Azure Services and other extensions with the MRTK.</span></span>

<span data-ttu-id="efee4-150">**包裝**</span><span class="sxs-lookup"><span data-stu-id="efee4-150">**Packaging**</span></span>

<span data-ttu-id="efee4-151">在 MRTK 2.5.0 中，我們發行了 Unity 套件管理員 (UPM) 的支援。</span><span class="sxs-lookup"><span data-stu-id="efee4-151">In MRTK 2.5.0 we released support for Unity Package Manager (UPM).</span></span> <span data-ttu-id="efee4-152">我們將繼續進行改進，讓您更輕鬆地使用 UPM 下載套件。</span><span class="sxs-lookup"><span data-stu-id="efee4-152">We are continuing to make improvements so it's even easier for you to download packages with UPM.</span></span>

## <a name="backlog"></a><span data-ttu-id="efee4-153">Backlog</span><span class="sxs-lookup"><span data-stu-id="efee4-153">Backlog</span></span>

<span data-ttu-id="efee4-154">下列清單強調 MRTK 小組打算採用的一些主要投資。</span><span class="sxs-lookup"><span data-stu-id="efee4-154">The following list highlights some of the key investments the MRTK team intends to pursue.</span></span>

- <span data-ttu-id="efee4-155">平臺擴充</span><span class="sxs-lookup"><span data-stu-id="efee4-155">Platform expansion</span></span>
- <span data-ttu-id="efee4-156">擴充性</span><span class="sxs-lookup"><span data-stu-id="efee4-156">Extensibility</span></span>
- <span data-ttu-id="efee4-157">模組 化</span><span class="sxs-lookup"><span data-stu-id="efee4-157">Modularity</span></span>
- <span data-ttu-id="efee4-158">協助工具功能</span><span class="sxs-lookup"><span data-stu-id="efee4-158">Accessibility features</span></span>
- <span data-ttu-id="efee4-159">全球化增強功能</span><span class="sxs-lookup"><span data-stu-id="efee4-159">Globalization enhancements</span></span>
- <span data-ttu-id="efee4-160">雲端服務支援</span><span class="sxs-lookup"><span data-stu-id="efee4-160">Cloud service support</span></span>
- <span data-ttu-id="efee4-161">工具</span><span class="sxs-lookup"><span data-stu-id="efee4-161">Tools</span></span>
