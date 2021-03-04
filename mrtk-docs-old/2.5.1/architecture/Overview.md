---
title: 架構概觀
description: MRTK 的架構總覽。
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK 架構、
ms.openlocfilehash: a40905284215c3b616f4db645e12ca92e1e5fe01
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/03/2021
ms.locfileid: "101779969"
---
# <a name="architecture-overview"></a><span data-ttu-id="7bbed-104">架構概觀</span><span class="sxs-lookup"><span data-stu-id="7bbed-104">Architecture overview</span></span>

<span data-ttu-id="7bbed-105">如需 MRTK 內容的整體簡介，本檔中包含的架構資訊將協助您瞭解下列各項：</span><span class="sxs-lookup"><span data-stu-id="7bbed-105">For an overall introduction to the contents of MRTK, the architecture information contained in this document will help you understand the following:</span></span>

- <span data-ttu-id="7bbed-106">大量 MRTK 以及它們如何連接</span><span class="sxs-lookup"><span data-stu-id="7bbed-106">Large pieces of MRTK and how they connect</span></span>
- <span data-ttu-id="7bbed-107">MRTK 引進的概念可能不存在於香草 Unity 中</span><span class="sxs-lookup"><span data-stu-id="7bbed-107">Concepts that MRTK introduces which may not exist in vanilla Unity</span></span>
- <span data-ttu-id="7bbed-108">某些較大型的系統 (例如輸入) 的運作方式</span><span class="sxs-lookup"><span data-stu-id="7bbed-108">How some of the larger systems (such as Input) work</span></span>

<span data-ttu-id="7bbed-109">本節的目的不是要告訴您如何進行工作，而是如何將這類工作結構化及原因。</span><span class="sxs-lookup"><span data-stu-id="7bbed-109">This section isn't intended to teach you how to do tasks, but rather how such tasks are structured and why.</span></span>

## <a name="many-audiences-one-toolkit"></a><span data-ttu-id="7bbed-110">許多物件，一個工具組</span><span class="sxs-lookup"><span data-stu-id="7bbed-110">Many audiences, one toolkit</span></span>

<span data-ttu-id="7bbed-111">MRTK 沒有單一、統一的物件。</span><span class="sxs-lookup"><span data-stu-id="7bbed-111">MRTK doesn't have a single, uniform audience.</span></span> <span data-ttu-id="7bbed-112">它是為了支援使用案例（範圍從第一次駭客松），到為企業建立複雜且共用體驗的人員所撰寫。</span><span class="sxs-lookup"><span data-stu-id="7bbed-112">It's been written to support use cases ranging from first time hackathons, to individuals building complex, shared experiences for enterprise.</span></span> <span data-ttu-id="7bbed-113">某些程式碼和 Api 可能已撰寫為比其他更多的 (，也就是 MRTK 的某些部分會比較適合「單鍵設定」 ) ，但請務必注意，某些程式碼和應用程式開發介面的原因較多。</span><span class="sxs-lookup"><span data-stu-id="7bbed-113">Some code and APIs may have been written that are optimized for one more than the other (i.e. some parts of the MRTK seem more optimized for "one click configure"), but it's important to note that some of those are more for historical and resourcing reasons.</span></span> <span data-ttu-id="7bbed-114">隨著 MRTK 發展，所建的功能應該設計成可支援使用案例的範圍。</span><span class="sxs-lookup"><span data-stu-id="7bbed-114">As MRTK evolves, the features that get built should be designed to scale to support the range of use cases.</span></span>

<span data-ttu-id="7bbed-115">MRTK 也具有在 VR 和 AR 體驗之間妥善調整的需求。</span><span class="sxs-lookup"><span data-stu-id="7bbed-115">MRTK also has requirements to gracefully scale across VR and AR experiences.</span></span> <span data-ttu-id="7bbed-116">在 HoloLens 2 或 HoloLens 1 上部署應用程式時，您應該可以輕鬆地建立可正常回復行為的應用程式，而且可以輕鬆地建立以 OpenVR 和 WMR 為目標的應用程式，並)  (和其他平臺。</span><span class="sxs-lookup"><span data-stu-id="7bbed-116">It should be easy to build applications that gracefully fallback in behavior when deployed on a HoloLens 2 OR a HoloLens 1, and it should be simple to build applications that target OpenVR and WMR (and other platforms).</span></span> <span data-ttu-id="7bbed-117">雖然團隊有時可能會將特定的反復專案放在特定的系統或平臺上，但長期目標是要在使用者建立混合現實體驗的任何地方建立廣泛的支援。</span><span class="sxs-lookup"><span data-stu-id="7bbed-117">While at times the team may focus a particular iteration on a specific system or platform, the long term goal is to build a wide range of support for wherever people are building mixed reality experiences.</span></span>

## <a name="high-level-breakdown"></a><span data-ttu-id="7bbed-118">高層級明細</span><span class="sxs-lookup"><span data-stu-id="7bbed-118">High level breakdown</span></span>

<span data-ttu-id="7bbed-119">MRTK 是一組工具的集合，可讓您輕鬆地 (MR) 的經驗，同時也提供應用程式架構，其中包含自己的執行時間、其擴充方式，以及其設定方式。</span><span class="sxs-lookup"><span data-stu-id="7bbed-119">The MRTK is both a collection of tools for getting mixed reality (MR) experiences off the ground quickly, and also an application framework with opinions on its own runtime, how it should be extended, and how it should be configured.</span></span>

<span data-ttu-id="7bbed-120">概括而言，MRTK 可透過下列方式細分：</span><span class="sxs-lookup"><span data-stu-id="7bbed-120">At a high level, the MRTK can be broken down in the following ways:</span></span>

![架構總覽圖表](../features/images/architecture/MRTK_Architecture.png)

<span data-ttu-id="7bbed-122">MRTK 還包含另一組抓取包公用程式，這些公用程式幾乎不需要相依于其餘的 MRTK (來列出一些：組建工具、解析器、音訊影響因素、平滑處理公用程式和線條轉譯器) </span><span class="sxs-lookup"><span data-stu-id="7bbed-122">The MRTK also contains another set of grab-bag utilities that have little to no dependencies on the rest of the MRTK (to list a few: build tools, solvers, audio influencers, smoothing utilities, and line renderers)</span></span>

<span data-ttu-id="7bbed-123">架構檔的其餘部分將從架構和執行時間開始，並在更有趣且複雜的系統（例如輸入）上發展。</span><span class="sxs-lookup"><span data-stu-id="7bbed-123">The remainder of the architecture documentation will build bottom up, starting from the framework and runtime, progressing to more interesting and complex systems, such as input.</span></span> <span data-ttu-id="7bbed-124">請參閱目錄以繼續進行架構總覽。</span><span class="sxs-lookup"><span data-stu-id="7bbed-124">Please see the table of contents to continue with the architectural overview.</span></span>
