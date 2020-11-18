---
title: Unreal 的效能建議
description: 在 Unreal 中使用混合實境應用程式的最佳效能建議
author: hferrone
ms.author: v-hferrone
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 混合實境, 效能, 最佳化, 設定, 文件
ms.openlocfilehash: 21bd3ee9fb7db23eab9365e41adfd0033aa0046e
ms.sourcegitcommit: 520c69eb761ad6083b36f448bbcfab89e343e40d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/12/2020
ms.locfileid: "94549123"
---
# <a name="performance-recommendations-for-unreal"></a><span data-ttu-id="31b13-104">Unreal 的效能建議</span><span class="sxs-lookup"><span data-stu-id="31b13-104">Performance recommendations for Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="31b13-105">概觀</span><span class="sxs-lookup"><span data-stu-id="31b13-105">Overview</span></span>

<span data-ttu-id="31b13-106">本文是以[混合實境效能建議](../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md)中所述的討論為基礎，但著重於 Unreal Engine 特有的功能。</span><span class="sxs-lookup"><span data-stu-id="31b13-106">This article builds on the discussion outlined in [performance recommendations for mixed reality](../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md), but focuses on features specific to Unreal Engine.</span></span> <span data-ttu-id="31b13-107">建議您先閱讀應用程式瓶頸、分析和剖析混合實境應用程式，並進行一般效能修正，再繼續進行。</span><span class="sxs-lookup"><span data-stu-id="31b13-107">You're encouraged to read up on application bottlenecks, analyzing and profiling mixed reality apps, and general performance fixes before continuing.</span></span>

## <a name="recommended-unreal-project-settings"></a><span data-ttu-id="31b13-108">建議的 Unreal 專案設定</span><span class="sxs-lookup"><span data-stu-id="31b13-108">Recommended Unreal project settings</span></span>
<span data-ttu-id="31b13-109">您可以在 [編輯] > [專案設定] 中找到下列每個設定。</span><span class="sxs-lookup"><span data-stu-id="31b13-109">You can find each of the following settings in **Edit > Project Settings**.</span></span>

1. <span data-ttu-id="31b13-110">使用行動 VR 轉譯器：</span><span class="sxs-lookup"><span data-stu-id="31b13-110">Using the mobile VR renderer:</span></span>
    * <span data-ttu-id="31b13-111">向下捲動至 [專案] 區段、選取 [目標硬體]，然後將目標平台設定為 [行動裝置/平板電腦]</span><span class="sxs-lookup"><span data-stu-id="31b13-111">Scroll to the **Project** section, select **Target Hardware**, and set the target platform to **Mobile/Tablet**</span></span>

![行動目標設定](images/unreal/performance-recommendations-img-01.png)

2. <span data-ttu-id="31b13-113">使用前向轉譯器：</span><span class="sxs-lookup"><span data-stu-id="31b13-113">Using the Forward Renderer:</span></span> 
    * <span data-ttu-id="31b13-114">這項功能在混合實境中的效能遠優於預設的延遲轉譯管線。</span><span class="sxs-lookup"><span data-stu-id="31b13-114">This feature is much better for Mixed Reality than the default Deferred rendering pipeline.</span></span> <span data-ttu-id="31b13-115">這主要是因為有多項功能可以個別關閉。</span><span class="sxs-lookup"><span data-stu-id="31b13-115">This is primarily because of the number of features that can be individually turned off.</span></span> 
    * <span data-ttu-id="31b13-116">您可以在 [Unreal 的文件](https://docs.unrealengine.com/Platforms/VR/DevelopVR/VRPerformance/index.html)中找到詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="31b13-116">You can find more information in [Unreal's documentation](https://docs.unrealengine.com/Platforms/VR/DevelopVR/VRPerformance/index.html).</span></span>

![前向轉譯](images/unreal/performance-recommendations-img-04.png)

3. <span data-ttu-id="31b13-118">使用行動多重檢視：</span><span class="sxs-lookup"><span data-stu-id="31b13-118">Using mobile multi-view:</span></span>
    * <span data-ttu-id="31b13-119">向下捲動至 [引擎] 區段、選取 [轉譯]、展開 [VR] 區段，然後同時啟用 [執行個體化立體聲] 和 [行動多重檢視]。</span><span class="sxs-lookup"><span data-stu-id="31b13-119">Scroll to the **Engine** section, select **Rendering**, expand the **VR** section, and enable both **Instanced Stereo** and **Mobile Multi-View**.</span></span> <span data-ttu-id="31b13-120">應取消核取行動設備 HDR。</span><span class="sxs-lookup"><span data-stu-id="31b13-120">Mobile HDR should be unchecked.</span></span>

![VR 轉譯設定](images/unreal/performance-recommendations-img-03.png)

4. <span data-ttu-id="31b13-122">使用 OpenXR 時，確保 [預設] 或 [D3D12] 是選取的 [預設 RHI]。</span><span class="sxs-lookup"><span data-stu-id="31b13-122">Ensure **Default** or **D3D12** is the selected **Default RHI** when using OpenXR.</span></span>
    * <span data-ttu-id="31b13-123">選取 **D3D11** 會對效能造成負面影響，因為平台會執行額外的轉譯行程。</span><span class="sxs-lookup"><span data-stu-id="31b13-123">Selecting **D3D11** will have a negative performance impact due to the platform performing an additional render pass.</span></span> <span data-ttu-id="31b13-124">除了避免額外的轉譯行程，**D3D12** 應提供轉譯效能改善。</span><span class="sxs-lookup"><span data-stu-id="31b13-124">**D3D12** should provide rendering performance improvements besides avoiding the additional render pass.</span></span>

![預設 RHI](images/unreal/performance-recommendations-img-09.png)

5. <span data-ttu-id="31b13-126">停用頂點霧化：</span><span class="sxs-lookup"><span data-stu-id="31b13-126">Disabling Vertex Fogging:</span></span> 
    * <span data-ttu-id="31b13-127">頂點霧化會在多邊形的每個頂點套用霧計算，然後在多邊形的整個表面上插補結果。</span><span class="sxs-lookup"><span data-stu-id="31b13-127">Vertex fogging applies fog calculations at each vertex in a polygon and then interpolates the results across the face of the polygon.</span></span> <span data-ttu-id="31b13-128">如果您的遊戲未使用霧，則應選擇此設定將霧停用，以提高陰影效能。</span><span class="sxs-lookup"><span data-stu-id="31b13-128">If your game does not use fog, you should choose this setting to disable fog to increase shading performance.</span></span>

![頂點霧化選項](images/unreal/performance-recommendations-img-05.png)

6. <span data-ttu-id="31b13-130">停用遮蔽消除：</span><span class="sxs-lookup"><span data-stu-id="31b13-130">Disabling occlusion culling:</span></span>
    * <span data-ttu-id="31b13-131">向下捲動至 [引擎] 區段、選取 [轉譯]、展開 [消除] 區段，然後取消勾選 [遮蔽消除]。</span><span class="sxs-lookup"><span data-stu-id="31b13-131">Scroll to the **Engine** section, select **Rendering**, expand the **Culling** section, and uncheck **Occlusion Culling**.</span></span>
        + <span data-ttu-id="31b13-132">如果您需要針對轉譯的詳細場景進行遮蔽消除，建議您在 [引擎] > [轉譯] 中啟用 [支援軟體遮蔽消除]。</span><span class="sxs-lookup"><span data-stu-id="31b13-132">If you need occlusion culling for a detailed scene being rendered, it's recommended that you enable **Support Software Occlusion Culling** in **Engine > Rendering**.</span></span> <span data-ttu-id="31b13-133">這讓 Unreal 可在 CPU 上執行此工作，並避免 GPU 的遮蔽查詢 (此功能在 HoloLens 2 上的執行效能不佳)。</span><span class="sxs-lookup"><span data-stu-id="31b13-133">This lets Unreal to do the work on the CPU and avoid GPU occlusion queries, which perform poorly on HoloLens 2.</span></span>
    * <span data-ttu-id="31b13-134">在行動裝置上，對 GPU 消除遮蔽的速度很慢。</span><span class="sxs-lookup"><span data-stu-id="31b13-134">Occlusion culling on the GPU on mobile devices is slow.</span></span> <span data-ttu-id="31b13-135">一般來說，您會希望 GPU 主要用在轉譯上。</span><span class="sxs-lookup"><span data-stu-id="31b13-135">Generally, you want the GPU to be primarily concerned with rendering.</span></span> <span data-ttu-id="31b13-136">如果您覺得遮蔽有助於效能，請試著改為啟用軟體遮蔽。</span><span class="sxs-lookup"><span data-stu-id="31b13-136">If you feel that occlusion will help performance, try enabling software occlusion instead.</span></span> <span data-ttu-id="31b13-137">請注意，如果您已使用大量的繪製呼叫來繫結 CPU，啟用軟體遮蔽可能會使效能變差。</span><span class="sxs-lookup"><span data-stu-id="31b13-137">Note that enabling software occlusion could make performance worse if you're already CPU bound by a large number of draw-calls.</span></span>

![停用遮蔽消除](images/unreal/performance-recommendations-img-02.png)

7. <span data-ttu-id="31b13-139">停用自訂深度樣板傳遞：</span><span class="sxs-lookup"><span data-stu-id="31b13-139">Disabling Custom Depth-Stencil Pass:</span></span>
    * <span data-ttu-id="31b13-140">這項功能需要額外的傳遞，這表示速度會很慢。</span><span class="sxs-lookup"><span data-stu-id="31b13-140">This feature requires an extra pass, meaning it's slow.</span></span> <span data-ttu-id="31b13-141">透明度在 Unreal 上的執行速度也很慢。</span><span class="sxs-lookup"><span data-stu-id="31b13-141">Translucency is also slow on Unreal.</span></span> <span data-ttu-id="31b13-142">您可以在 [Unreal 的文件](https://docs.unrealengine.com/Engine/Performance/Guidelines/index.html)中找到詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="31b13-142">You can find more information in [Unreal's documentation](https://docs.unrealengine.com/Engine/Performance/Guidelines/index.html).</span></span>

![深度樣板](images/unreal/performance-recommendations-img-06.png)

8. <span data-ttu-id="31b13-144">減少重疊的陰影圖：</span><span class="sxs-lookup"><span data-stu-id="31b13-144">Reducing Cascaded Shadow Maps:</span></span> 
    * <span data-ttu-id="31b13-145">減少陰影圖的數目將可改善效能。</span><span class="sxs-lookup"><span data-stu-id="31b13-145">Reducing the number of shadow maps will improve performance.</span></span> <span data-ttu-id="31b13-146">此設定通常應設為 1，除非有可見的品質損失。</span><span class="sxs-lookup"><span data-stu-id="31b13-146">Generally, this should be set to 1 unless there is a visible quality loss.</span></span> 

![重疊的陰影圖](images/unreal/performance-recommendations-img-07.png)

## <a name="optional-settings"></a><span data-ttu-id="31b13-148">選擇性設定</span><span class="sxs-lookup"><span data-stu-id="31b13-148">Optional settings</span></span>

> [!NOTE]
> <span data-ttu-id="31b13-149">下列設定可能會改善效能，但代價是某些功能須停用。</span><span class="sxs-lookup"><span data-stu-id="31b13-149">The following settings may improve performance, but at the cost of disabling certain features.</span></span> <span data-ttu-id="31b13-150">只有在您確定不需要這類功能時，才可使用這些設定。</span><span class="sxs-lookup"><span data-stu-id="31b13-150">Only use these settings if you're sure you don't need the features in question.</span></span>

1. <span data-ttu-id="31b13-151">減少行動著色器排列</span><span class="sxs-lookup"><span data-stu-id="31b13-151">Mobile Shader Permutation Reduction</span></span>
    * <span data-ttu-id="31b13-152">如果您的燈光不會脫離相機獨立移動，則可以安全地將此值設定為 0。</span><span class="sxs-lookup"><span data-stu-id="31b13-152">If your lights don't move independently of the camera, then you can safely set this value to 0.</span></span> <span data-ttu-id="31b13-153">其主要的優點是可以讓 Unreal 消除數個著色器排列，加快著色器編譯速度。</span><span class="sxs-lookup"><span data-stu-id="31b13-153">The primary benefit is that it will allow Unreal to cull several shader permutations, speeding up shader compilation.</span></span>

![減少行動著色器排列](images/unreal/performance-recommendations-img-08.png)

## <a name="see-also"></a><span data-ttu-id="31b13-155">另請參閱</span><span class="sxs-lookup"><span data-stu-id="31b13-155">See also</span></span>
* [<span data-ttu-id="31b13-156">Unreal Engine 行動效能指導方針</span><span class="sxs-lookup"><span data-stu-id="31b13-156">Unreal Engine mobile performance guidelines</span></span>]( https://docs.unrealengine.com/Platforms/Mobile/Performance/index.html)