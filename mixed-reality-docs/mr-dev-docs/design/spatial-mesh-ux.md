---
title: 空間網格視覺效果
description: 深入瞭解 MRTK 中的空間網格視覺效果的設計方針和實體環境瞭解。
author: cre8ivepark
ms.author: dongpark
ms.date: 06/19/2020
ms.topic: article
keywords: 混合的現實、HoloLens、UI 控制項、互動、UI、ux、UX 設計、空間 UI、空間互動、3D UI、3D UX、混合現實耳機、windows mixed reality 耳機、虛擬實境耳機、HoloLens、MRTK、混合現實工具組
ms.openlocfilehash: 5bdcba60f38ac67bbf0f394337735f4a2d4ec423
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600627"
---
# <a name="spatial-mesh"></a><span data-ttu-id="a9e9a-104">空間網格</span><span class="sxs-lookup"><span data-stu-id="a9e9a-104">Spatial mesh</span></span>

![空間網格](images/MRTK_PulseShader_SpatialMesh.gif)

<span data-ttu-id="a9e9a-106">使用者瞭解裝置如何透過空間網格視覺效果來理解及瞭解實體環境。</span><span class="sxs-lookup"><span data-stu-id="a9e9a-106">Users learn how a device perceives and understands the physical environment through spatial mesh visualization.</span></span> <span data-ttu-id="a9e9a-107">適當的空間網格視覺效果可在提供空間內容時建立趣味性兼具和神奇體驗。</span><span class="sxs-lookup"><span data-stu-id="a9e9a-107">Proper spatial mesh visualization can create a delightful and magical experience while providing spatial context.</span></span>  

## <a name="design-guideline"></a><span data-ttu-id="a9e9a-108">設計指導方針</span><span class="sxs-lookup"><span data-stu-id="a9e9a-108">Design guideline</span></span>

<span data-ttu-id="a9e9a-109">請務必讓使用者專注並與內容互動。</span><span class="sxs-lookup"><span data-stu-id="a9e9a-109">It's important to allow the user to focus and interact with content.</span></span> <span data-ttu-id="a9e9a-110">背景中空間網格的連續視覺效果可能會造成干擾。</span><span class="sxs-lookup"><span data-stu-id="a9e9a-110">Continuous visualization of the spatial mesh in the background can be distracting.</span></span> <span data-ttu-id="a9e9a-111">建議您在初始啟動時，或當使用者清楚地顯示其想要依目標和空中點擊空間來查看環境網格時，謹慎地視覺化環境。</span><span class="sxs-lookup"><span data-stu-id="a9e9a-111">We recommend visualizing the environment sparingly, either only once in the initial launch or when the user clearly shows they want to see the environmental mesh by targeting and air-tapping space.</span></span> <span data-ttu-id="a9e9a-112">您可以在混合實境入口中觀察這項行為。</span><span class="sxs-lookup"><span data-stu-id="a9e9a-112">You can observe this behavior in the Mixed Reality Portal.</span></span>
<br>

## <a name="spatial-mesh-visualization-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="a9e9a-113">適用于 Unity 的 MRTK (混合現實工具組) 的空間網格視覺效果</span><span class="sxs-lookup"><span data-stu-id="a9e9a-113">Spatial mesh visualization in MRTK (Mixed Reality Toolkit) for Unity</span></span>

<span data-ttu-id="a9e9a-114">MRTK 為空間網格視覺效果提供數種材質。</span><span class="sxs-lookup"><span data-stu-id="a9e9a-114">MRTK provides several materials for the spatial mesh visualization.</span></span>

- <span data-ttu-id="a9e9a-115">**MRTK_Wireframe，MRTK_Wireframe** 的材質：預設的靜態空間網格材質，顯示沒有動畫的網格輪廓。</span><span class="sxs-lookup"><span data-stu-id="a9e9a-115">**MRTK_Wireframe.mat, MRTK_Wireframe.mat**: Default static spatial mesh material, which shows the mesh outlines without animation.</span></span> <span data-ttu-id="a9e9a-116">這項資料適用于偵錯工具，因為它會顯示整個空間網格幾何。</span><span class="sxs-lookup"><span data-stu-id="a9e9a-116">This material is useful for debugging purposes since it shows the entire spatial mesh geometries.</span></span> <span data-ttu-id="a9e9a-117">但是，不建議用於生產環境。</span><span class="sxs-lookup"><span data-stu-id="a9e9a-117">However, it isn't recommended for production.</span></span>
<br>
<img src="images/SurfaceReconstruction.jpg" alt="Wireframe spatial mesh visualization" width="640px">

- <span data-ttu-id="a9e9a-118">**MRTK_SurfaceReconstruction** 的材質：此材質提供您對空間網格的動畫脈衝效果。</span><span class="sxs-lookup"><span data-stu-id="a9e9a-118">**MRTK_SurfaceReconstruction.mat**: This material gives you an animated pulse effect on the spatial mesh.</span></span> <span data-ttu-id="a9e9a-119">您可以使用這份資料，在特定時間或使用者的按兩下輸入時，將環境視覺化。</span><span class="sxs-lookup"><span data-stu-id="a9e9a-119">You can use this material to visualize the environment at a specific moment or on the user's air-tap input.</span></span> <span data-ttu-id="a9e9a-120">如需範例，請參閱 **PulseShaderExamples unity** 場景。</span><span class="sxs-lookup"><span data-stu-id="a9e9a-120">See **PulseShaderExamples.unity** scene for the examples.</span></span>
<br>
<img src="images/MRTK_SRMesh_Pulse.jpg" alt="Pulse spatial mesh visualization" width="640px">

* <span data-ttu-id="a9e9a-121">如需詳細資訊，請參閱 [MRTK-空間感知](/windows/mixed-reality/mrtk-unity/features/spatial-awareness/spatial-awareness-getting-started) 和 [MRTK-脈衝著色器](/windows/mixed-reality/mrtk-unity/features/experimental/pulse-shader)。</span><span class="sxs-lookup"><span data-stu-id="a9e9a-121">For more information, see [MRTK - Spatial Awareness](/windows/mixed-reality/mrtk-unity/features/spatial-awareness/spatial-awareness-getting-started) and [MRTK - Pulse Shader](/windows/mixed-reality/mrtk-unity/features/experimental/pulse-shader).</span></span>

<br>

---

## <a name="see-also"></a><span data-ttu-id="a9e9a-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a9e9a-122">See also</span></span>

* [<span data-ttu-id="a9e9a-123">游標</span><span class="sxs-lookup"><span data-stu-id="a9e9a-123">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="a9e9a-124">手部光線</span><span class="sxs-lookup"><span data-stu-id="a9e9a-124">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="a9e9a-125">Button</span><span class="sxs-lookup"><span data-stu-id="a9e9a-125">Button</span></span>](button.md)
* [<span data-ttu-id="a9e9a-126">可互動的物件</span><span class="sxs-lookup"><span data-stu-id="a9e9a-126">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="a9e9a-127">週框方塊和應用程式列</span><span class="sxs-lookup"><span data-stu-id="a9e9a-127">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="a9e9a-128">操作</span><span class="sxs-lookup"><span data-stu-id="a9e9a-128">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="a9e9a-129">手部功能表</span><span class="sxs-lookup"><span data-stu-id="a9e9a-129">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="a9e9a-130">近端功能表</span><span class="sxs-lookup"><span data-stu-id="a9e9a-130">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="a9e9a-131">物件集合</span><span class="sxs-lookup"><span data-stu-id="a9e9a-131">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="a9e9a-132">語音命令</span><span class="sxs-lookup"><span data-stu-id="a9e9a-132">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="a9e9a-133">鍵盤</span><span class="sxs-lookup"><span data-stu-id="a9e9a-133">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="a9e9a-134">工具提示</span><span class="sxs-lookup"><span data-stu-id="a9e9a-134">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="a9e9a-135">平板</span><span class="sxs-lookup"><span data-stu-id="a9e9a-135">Slate</span></span>](slate.md)
* [<span data-ttu-id="a9e9a-136">滑桿</span><span class="sxs-lookup"><span data-stu-id="a9e9a-136">Slider</span></span>](slider.md)
* [<span data-ttu-id="a9e9a-137">著色器</span><span class="sxs-lookup"><span data-stu-id="a9e9a-137">Shader</span></span>](shader.md)
* [<span data-ttu-id="a9e9a-138">佈告板和常駐標籤</span><span class="sxs-lookup"><span data-stu-id="a9e9a-138">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="a9e9a-139">顯示進度</span><span class="sxs-lookup"><span data-stu-id="a9e9a-139">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="a9e9a-140">表面磁性</span><span class="sxs-lookup"><span data-stu-id="a9e9a-140">Surface magnetism</span></span>](surface-magnetism.md)