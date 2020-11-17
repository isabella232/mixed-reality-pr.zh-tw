---
title: Unreal 中的材質建議
description: Unreal 引擎中的材質總覽。
author: hferrone
ms.author: v-hferrone
ms.date: 09/18/2020
ms.topic: article
keywords: Unreal、Unreal Engine 4、UE4、HoloLens、HoloLens 2、開發、教材、檔、指南、功能、全息表、遊戲開發、混合現實耳機、windows mixed reality 耳機、虛擬實境耳機
ms.openlocfilehash: d57689e9427ab5877e3afb49b0d19f35df6c47d2
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2020
ms.locfileid: "94678937"
---
# <a name="material-recommendations-in-unreal"></a><span data-ttu-id="fe6e3-104">Unreal 中的材質建議</span><span class="sxs-lookup"><span data-stu-id="fe6e3-104">Material recommendations in Unreal</span></span>

<span data-ttu-id="fe6e3-105">材質可以在 Unreal 引擎中建立或打破效能。</span><span class="sxs-lookup"><span data-stu-id="fe6e3-105">Materials can make or break performance in Unreal Engine.</span></span> <span data-ttu-id="fe6e3-106">此頁面可作為基本設定的快速入門，您應該使用這些設定才能獲得最佳效能。</span><span class="sxs-lookup"><span data-stu-id="fe6e3-106">This page acts as a quick-start on the basic settings you should be using in order to get the best performance.</span></span>

## <a name="using-customizeduvs"></a><span data-ttu-id="fe6e3-107">使用 CustomizedUVs</span><span class="sxs-lookup"><span data-stu-id="fe6e3-107">Using CustomizedUVs</span></span>

<span data-ttu-id="fe6e3-108">如果您需要為您的材質提供 UVs 圖，您應該使用 CustomizedUVs 而不是直接修改材質節點的 UV。</span><span class="sxs-lookup"><span data-stu-id="fe6e3-108">If you need to provide tiling of UVs on your material, you should use CustomizedUVs rather than modifying the UV of the texture node directly.</span></span> <span data-ttu-id="fe6e3-109">CustomizedUVs 允許在頂點著色器中發生 UV 操作，而不是圖元著色器。</span><span class="sxs-lookup"><span data-stu-id="fe6e3-109">CustomizedUVs allow UV manipulation to happen in the Vertex shaders rather than Pixel shader.</span></span> 

![Unreal 中的材質設定](images/unreal-materials-img-01c.png)

<span data-ttu-id="fe6e3-111">您可以在下列螢幕擷取畫面中找到 [Unreal 引擎檔](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html) 和最佳作法範例中的材質詳細資料：</span><span class="sxs-lookup"><span data-stu-id="fe6e3-111">You can find more details on materials in the [Unreal Engine documentation](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html) and best practice examples in the screenshots below:</span></span>

<span data-ttu-id="fe6e3-112">[ ![ 建議的材質設定 Unreal ](images/unreal-materials-img-01.png) 建議的](images/unreal-materials-img-01.png#lightbox) 
 *材質設定*</span><span class="sxs-lookup"><span data-stu-id="fe6e3-112">[ ![Recommended material settings in Unreal](images/unreal-materials-img-01.png) ](images/unreal-materials-img-01.png#lightbox)
*Recommended material setup*</span></span>

<span data-ttu-id="fe6e3-113">Unreal 不建議的材質設定[ ![ 中不建議的材質設定 ](images/unreal-materials-img-01b.png) ](images/unreal-materials-img-01b.png#lightbox) 
 *Non-recommended material setup*</span><span class="sxs-lookup"><span data-stu-id="fe6e3-113">[ ![Non recommended material settings in Unreal](images/unreal-materials-img-01b.png) ](images/unreal-materials-img-01b.png#lightbox)
*Non-recommended material setup*</span></span>

## <a name="changing-blend-mode"></a><span data-ttu-id="fe6e3-114">變更 Blend 模式</span><span class="sxs-lookup"><span data-stu-id="fe6e3-114">Changing Blend Mode</span></span>

<span data-ttu-id="fe6e3-115">除非有強原因，否則您應該將 blend 模式設定為不透明。</span><span class="sxs-lookup"><span data-stu-id="fe6e3-115">You should set blend mode to opaque unless there is a strong reason to do otherwise.</span></span> <span data-ttu-id="fe6e3-116">遮罩和半透明材質很慢。</span><span class="sxs-lookup"><span data-stu-id="fe6e3-116">Masked and Translucent materials are slow.</span></span> <span data-ttu-id="fe6e3-117">您可以在 [Unreal 引擎檔](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html)中找到更多有關材質的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="fe6e3-117">You can find more details on materials in the [Unreal Engine documentation](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html).</span></span>

![變更 blend 模式](images/unreal-materials-img-02.jpg)

## <a name="updating-lighting-for-mobile"></a><span data-ttu-id="fe6e3-119">更新行動裝置的燈光</span><span class="sxs-lookup"><span data-stu-id="fe6e3-119">Updating lighting for mobile</span></span>

<span data-ttu-id="fe6e3-120">應關閉完整精確度。</span><span class="sxs-lookup"><span data-stu-id="fe6e3-120">Full precision should be turned off.</span></span> <span data-ttu-id="fe6e3-121">您可以藉由關閉方向資訊，來向下撥號 Lightmap 光源。</span><span class="sxs-lookup"><span data-stu-id="fe6e3-121">Lightmap lighting can be dialed down by turning of directional information.</span></span> <span data-ttu-id="fe6e3-122">停用時，lightmaps 中的光源將會是平坦的，但較便宜。</span><span class="sxs-lookup"><span data-stu-id="fe6e3-122">When disabled, lighting from lightmaps will be flat but cheaper.</span></span>

![Unreal 中的行動電話材質設定](images/unreal-materials-img-03.jpg)

## <a name="adjusting-forward-shading"></a><span data-ttu-id="fe6e3-124">調整正向網底</span><span class="sxs-lookup"><span data-stu-id="fe6e3-124">Adjusting Forward Shading</span></span>

<span data-ttu-id="fe6e3-125">這些選項會以效能的成本改善視覺精確度。</span><span class="sxs-lookup"><span data-stu-id="fe6e3-125">These options improve visual fidelity at the cost of performance.</span></span> <span data-ttu-id="fe6e3-126">它們應該會關閉以獲得最大效能。</span><span class="sxs-lookup"><span data-stu-id="fe6e3-126">They should be turned off for maximum performance.</span></span>

![Unreal 中的向前陰影材質設定](images/unreal-materials-img-04.jpg)

## <a name="setting-material-translucency"></a><span data-ttu-id="fe6e3-128">設定材質半透明度</span><span class="sxs-lookup"><span data-stu-id="fe6e3-128">Setting material translucency</span></span>

<span data-ttu-id="fe6e3-129">指出透明的材質不應受到 bloom 或 DOF 的影響。</span><span class="sxs-lookup"><span data-stu-id="fe6e3-129">Indicates that the translucent material should not be affected by bloom or DOF.</span></span> <span data-ttu-id="fe6e3-130">由於這兩種效果在 MR 中都很罕見，因此預設應該開啟此設定。</span><span class="sxs-lookup"><span data-stu-id="fe6e3-130">Since both those effects are rare in MR, this setting should be on by default.</span></span>

![Unreal 中的 Mobile 個別半透明度設定](images/unreal-materials-img-05.jpg)

## <a name="optional-settings"></a><span data-ttu-id="fe6e3-132">選擇性設定</span><span class="sxs-lookup"><span data-stu-id="fe6e3-132">Optional settings</span></span>

<span data-ttu-id="fe6e3-133">下列設定可能會改善效能，但請注意，這些設定會停用某些功能。</span><span class="sxs-lookup"><span data-stu-id="fe6e3-133">The following settings may improve performance, but note that they disable certain features.</span></span> <span data-ttu-id="fe6e3-134">只有在您確定不需要有問題的功能時，才使用這些設定。</span><span class="sxs-lookup"><span data-stu-id="fe6e3-134">Only use these settings if you are sure you don't need the features in question.</span></span>

![Unreal 中的選擇性材質設定](images/unreal-materials-img-06.jpg)

<span data-ttu-id="fe6e3-136">如果您的材質不需要反射或眼，則設定此選項可提供大幅的效能提升。</span><span class="sxs-lookup"><span data-stu-id="fe6e3-136">If your material doesn't require reflections or shine, then setting this option can provide a tremendous performance boost.</span></span> <span data-ttu-id="fe6e3-137">在內部測試中，它會與「unlit」一樣快速，同時提供光源資訊。</span><span class="sxs-lookup"><span data-stu-id="fe6e3-137">In internal testing, it is as fast as "unlit" while providing lighting information.</span></span>

## <a name="best-practices"></a><span data-ttu-id="fe6e3-138">最佳作法</span><span class="sxs-lookup"><span data-stu-id="fe6e3-138">Best practices</span></span>

<span data-ttu-id="fe6e3-139">以下不是「設定」，因為它們是與材質相關的最佳做法。</span><span class="sxs-lookup"><span data-stu-id="fe6e3-139">The following are not "settings" as much as they are best practices related to Materials.</span></span>

<span data-ttu-id="fe6e3-140">建立參數時，最好盡可能使用「靜態參數」。</span><span class="sxs-lookup"><span data-stu-id="fe6e3-140">When creating parameters, prefer to use "Static Parameters" wherever possible.</span></span> <span data-ttu-id="fe6e3-141">靜態參數可用來移除沒有執行時間成本之材質的整個分支。</span><span class="sxs-lookup"><span data-stu-id="fe6e3-141">Static Switches can be used to remove an entire branch of a material with no runtime cost.</span></span> <span data-ttu-id="fe6e3-142">實例可以有不同的值，因此可以有樣板化著色器設定，而不會遺失效能。</span><span class="sxs-lookup"><span data-stu-id="fe6e3-142">Instances can have different values, making it possible to have a templated shader setup with no performance loss.</span></span> <span data-ttu-id="fe6e3-143">但缺點在於，這會建立許多會導致重新編譯許多著色器的排列。</span><span class="sxs-lookup"><span data-stu-id="fe6e3-143">The downside, however, is that this creates many permutations that will cause a lot of shader recompilation.</span></span> <span data-ttu-id="fe6e3-144">請儘量減少材質中的靜態參數數目，以及這些靜態參數實際上使用的排列數目。</span><span class="sxs-lookup"><span data-stu-id="fe6e3-144">Try to minimize the number of static parameters in the material and the number of permutations of those static parameters that are actually used.</span></span> <span data-ttu-id="fe6e3-145">您可以在 [Unreal 引擎檔](https://docs.unrealengine.com/Engine/Rendering/Materials/ExpressionReference/Parameters/index.html#staticswitchparameter)中找到轉譯材質參數的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="fe6e3-145">You can find more details on rendering material parameters in the [Unreal Engine documentation](https://docs.unrealengine.com/Engine/Rendering/Materials/ExpressionReference/Parameters/index.html#staticswitchparameter).</span></span>

![材質設定的最佳作法](images/unreal-materials-img-07.jpg)

<span data-ttu-id="fe6e3-147">建立材質實例時，應該將喜好設定提供給材質實例動態的 **材質實例常數** 。</span><span class="sxs-lookup"><span data-stu-id="fe6e3-147">When creating Material Instances, preference should be given to **Material Instance Constant** over Material Instance Dynamic.</span></span> <span data-ttu-id="fe6e3-148">**材質實例常數** 是在執行時間之前只計算一次的實例材質。</span><span class="sxs-lookup"><span data-stu-id="fe6e3-148">**Material Instance Constant** is an instanced Material that calculates only once, prior to runtime.</span></span>

<span data-ttu-id="fe6e3-149">透過內容瀏覽器建立的材質實例 (以 **滑鼠右鍵按一下 > 建立材質實例**) 是材質實例常數。</span><span class="sxs-lookup"><span data-stu-id="fe6e3-149">The material instance created via the Content Browser (**right-click > Create Material Instance**) is a Material Instance Constant.</span></span> <span data-ttu-id="fe6e3-150">動態資料實例是透過程式碼建立。</span><span class="sxs-lookup"><span data-stu-id="fe6e3-150">Material Instance Dynamic are created via code.</span></span> <span data-ttu-id="fe6e3-151">您可以在 [Unreal 引擎檔](https://docs.unrealengine.com/Engine/Rendering/Materials/MaterialInstances/index.html)中找到有關材質實例的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="fe6e3-151">You can find more details on material instances in the [Unreal Engine documentation](https://docs.unrealengine.com/Engine/Rendering/Materials/MaterialInstances/index.html).</span></span>

![在 Unreal 中建立材質實例](images/unreal-materials-img-08.png)

<span data-ttu-id="fe6e3-153">請留意您的材質/著色器複雜度。</span><span class="sxs-lookup"><span data-stu-id="fe6e3-153">Keep an eye on the complexity of your materials/shaders.</span></span> <span data-ttu-id="fe6e3-154">您可以按一下 [平臺統計資料] 圖示，以查看各種平臺上的材質成本。</span><span class="sxs-lookup"><span data-stu-id="fe6e3-154">You can view the cost of your Material on various platforms by clicking on the Platform Stats icon.</span></span> <span data-ttu-id="fe6e3-155">您也可以在 [Unreal 引擎檔](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html)中找到更多有關材質的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="fe6e3-155">You can also find more details on materials in the [Unreal Engine documentation](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html).</span></span>

![在 Unreal 中建立材質實例動態設定](images/unreal-materials-img-09.png)

<span data-ttu-id="fe6e3-157">您可以透過著色器複雜性 [視圖模式](https://docs.unrealengine.com/Engine/UI/LevelEditor/Viewports/ViewModes/index.html)，快速瞭解著色器的相對複雜度。</span><span class="sxs-lookup"><span data-stu-id="fe6e3-157">You can get a quick idea of the relative complexity of your shader via the Shader Complexity [View mode](https://docs.unrealengine.com/Engine/UI/LevelEditor/Viewports/ViewModes/index.html).</span></span>

* <span data-ttu-id="fe6e3-158">視圖模式熱鍵： Alt + 8</span><span class="sxs-lookup"><span data-stu-id="fe6e3-158">View Mode Hotkey: Alt + 8</span></span>
* <span data-ttu-id="fe6e3-159">主控台命令： viewmode shadercomplexity</span><span class="sxs-lookup"><span data-stu-id="fe6e3-159">Console command: viewmode shadercomplexity</span></span>

![Unreal 中的材質複雜性](images/unreal-materials-img-10.png)

## <a name="see-also"></a><span data-ttu-id="fe6e3-161">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fe6e3-161">See also</span></span>
* [<span data-ttu-id="fe6e3-162">行動教材</span><span class="sxs-lookup"><span data-stu-id="fe6e3-162">Mobile materials</span></span>](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html)
* [<span data-ttu-id="fe6e3-163">視圖模式</span><span class="sxs-lookup"><span data-stu-id="fe6e3-163">View modes</span></span>](https://docs.unrealengine.com/Engine/UI/LevelEditor/Viewports/ViewModes/index.html)
* [<span data-ttu-id="fe6e3-164">材質實例</span><span class="sxs-lookup"><span data-stu-id="fe6e3-164">Material instances</span></span>](https://docs.unrealengine.com/Engine/Rendering/Materials/MaterialInstances/index.html)
