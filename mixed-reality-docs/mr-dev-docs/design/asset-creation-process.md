---
title: 資產建立程序
description: 針對混合現實體驗建立資產的指引。
author: shengkait
ms.author: shentan
ms.date: 03/21/2018
ms.topic: article
keywords: 資產、建立、處理、預算、多邊形、材質、著色器、效能、混合現實耳機、windows mixed reality 耳機、虛擬實境耳機、HoloLens、MRTK、混合現實工具組、資產
ms.openlocfilehash: 0c6f592dd813c06613801510ad8c8a936ad0de65
ms.sourcegitcommit: 4f3ef057a285be2e260615e5d6c41f00d15d08f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2020
ms.locfileid: "94702874"
---
# <a name="asset-creation-process"></a><span data-ttu-id="38711-104">資產建立程序</span><span class="sxs-lookup"><span data-stu-id="38711-104">Asset creation process</span></span>

<span data-ttu-id="38711-105">Windows Mixed Reality 是以 Microsoft 在 DirectX 中所做的投資數十年為基礎。</span><span class="sxs-lookup"><span data-stu-id="38711-105">Windows Mixed Reality builds on the decades of investment Microsoft has made into DirectX.</span></span> <span data-ttu-id="38711-106">這表示，開發人員在建立3D 圖形時，所擁有的所有經驗和技能，會持續對 HoloLens 有價值。</span><span class="sxs-lookup"><span data-stu-id="38711-106">This means that all of the experience and skills developers have with building 3D graphics continues to be valuable with HoloLens.</span></span>

<span data-ttu-id="38711-107">您為專案建立的資產有許多圖形和表單。</span><span class="sxs-lookup"><span data-stu-id="38711-107">The assets you create for a project come in many shapes and forms.</span></span> <span data-ttu-id="38711-108">它們可以由一連串的材質/影像、音訊、影片、3D 模型和動畫組成。</span><span class="sxs-lookup"><span data-stu-id="38711-108">They can be comprised of a series of textures/images, audio, video, 3D models and animations.</span></span> <span data-ttu-id="38711-109">我們無法開始討論可用來建立專案中不同類型資產的所有工具。</span><span class="sxs-lookup"><span data-stu-id="38711-109">We can't begin to cover all the tools that are available to create the different types of assets used in a project.</span></span> <span data-ttu-id="38711-110">在本文中，我們將著重于3D 資產建立方法。</span><span class="sxs-lookup"><span data-stu-id="38711-110">For this article we will focus on 3D asset creation methods.</span></span>

<span data-ttu-id="38711-111">![概念、建立、整合和反復專案流程](images/concept-creation-integration-iteration-flow-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="38711-111">![Concept, creation, integration and iteration flow](images/concept-creation-integration-iteration-flow-640px.jpg)</span></span><br>
<span data-ttu-id="38711-112">*概念、建立、整合和反復專案流程*</span><span class="sxs-lookup"><span data-stu-id="38711-112">*Concept, creation, integration and iteration flow*</span></span>

## <a name="things-to-consider"></a><span data-ttu-id="38711-113">考量事項</span><span class="sxs-lookup"><span data-stu-id="38711-113">Things to consider</span></span>

<span data-ttu-id="38711-114">查看您嘗試建立的體驗時，您想要將它視為 **預算** ，您可以花在嘗試建立最佳體驗。</span><span class="sxs-lookup"><span data-stu-id="38711-114">When looking at the experience you're trying to create think of it as a **budget** that you can spend to try to create the best experience.</span></span> <span data-ttu-id="38711-115">在您的資產中使用的 **多邊形** 或資料 **類型** 數目不一定會有固定限制，但是有一組預算的取捨。</span><span class="sxs-lookup"><span data-stu-id="38711-115">There is not necessarily hard limits on the number of **polygons** or **types of materials** use in your assets but more a budgeted set of tradeoffs.</span></span>

<span data-ttu-id="38711-116">以下是您體驗的範例預算。</span><span class="sxs-lookup"><span data-stu-id="38711-116">Below is an example budget for your experience.</span></span> <span data-ttu-id="38711-117">效能通常不是單一失敗點，而是每個 se 會有上千個剪下。</span><span class="sxs-lookup"><span data-stu-id="38711-117">Performance is usually not a single point of failure but death by a thousand cuts per-se.</span></span>
<br>

<table style="float:right; margin-left: 10px;">
<tr>
<th style="text-align:left;"><span data-ttu-id="38711-118"><b>資產</b></span><span class="sxs-lookup"><span data-stu-id="38711-118"><b>Assets</b></span></span></th><th style="text-align:right;"> <span data-ttu-id="38711-119">CPU</span><span class="sxs-lookup"><span data-stu-id="38711-119">CPU</span></span></th><th> <span data-ttu-id="38711-120">GPU</span><span class="sxs-lookup"><span data-stu-id="38711-120">GPU</span></span></th><th> <span data-ttu-id="38711-121">記憶體</span><span class="sxs-lookup"><span data-stu-id="38711-121">Memory</span></span></th>
</tr><tr>
<td> <span data-ttu-id="38711-122">多邊形</span><span class="sxs-lookup"><span data-stu-id="38711-122">Polygons</span></span></td><td> <span data-ttu-id="38711-123">0%</span><span class="sxs-lookup"><span data-stu-id="38711-123">0%</span></span></td><td> <span data-ttu-id="38711-124">5%</span><span class="sxs-lookup"><span data-stu-id="38711-124">5%</span></span></td><td> <span data-ttu-id="38711-125">10%</span><span class="sxs-lookup"><span data-stu-id="38711-125">10%</span></span></td>
</tr><tr>
<td> <span data-ttu-id="38711-126">紋理</span><span class="sxs-lookup"><span data-stu-id="38711-126">Textures</span></span></td><td> <span data-ttu-id="38711-127">5%</span><span class="sxs-lookup"><span data-stu-id="38711-127">5%</span></span></td><td> <span data-ttu-id="38711-128">15%</span><span class="sxs-lookup"><span data-stu-id="38711-128">15%</span></span></td><td><span data-ttu-id="38711-129">25%</span><span class="sxs-lookup"><span data-stu-id="38711-129">25%</span></span></td>
</tr><tr>
<td> <span data-ttu-id="38711-130">著色器</span><span class="sxs-lookup"><span data-stu-id="38711-130">Shaders</span></span></td><td> <span data-ttu-id="38711-131">15%</span><span class="sxs-lookup"><span data-stu-id="38711-131">15%</span></span></td><td> <span data-ttu-id="38711-132">35%</span><span class="sxs-lookup"><span data-stu-id="38711-132">35%</span></span></td><td> <span data-ttu-id="38711-133">0%</span><span class="sxs-lookup"><span data-stu-id="38711-133">0%</span></span></td>
</tr><tr>
<td> <span data-ttu-id="38711-134"><b>Dynamics</b></span><span class="sxs-lookup"><span data-stu-id="38711-134"><b>Dynamics</b></span></span></td><td></td><td></td><td></td>
</tr><tr>
<td> <span data-ttu-id="38711-135">物理特性</span><span class="sxs-lookup"><span data-stu-id="38711-135">Physics</span></span></td><td> <span data-ttu-id="38711-136">5%</span><span class="sxs-lookup"><span data-stu-id="38711-136">5%</span></span></td><td> <span data-ttu-id="38711-137">15%</span><span class="sxs-lookup"><span data-stu-id="38711-137">15%</span></span></td><td> <span data-ttu-id="38711-138">0%</span><span class="sxs-lookup"><span data-stu-id="38711-138">0%</span></span></td>
</tr><tr>
<td> <span data-ttu-id="38711-139">即時光源</span><span class="sxs-lookup"><span data-stu-id="38711-139">Realtime lighting</span></span></td><td> <span data-ttu-id="38711-140">10%</span><span class="sxs-lookup"><span data-stu-id="38711-140">10%</span></span></td><td> <span data-ttu-id="38711-141">0%</span><span class="sxs-lookup"><span data-stu-id="38711-141">0%</span></span></td><td> <span data-ttu-id="38711-142">0%</span><span class="sxs-lookup"><span data-stu-id="38711-142">0%</span></span></td>
</tr><tr>
<td> <span data-ttu-id="38711-143">媒體 (音訊/影片) </span><span class="sxs-lookup"><span data-stu-id="38711-143">Media (audio/video)</span></span></td><td> -</td><td> <span data-ttu-id="38711-144">15%</span><span class="sxs-lookup"><span data-stu-id="38711-144">15%</span></span></td><td> <span data-ttu-id="38711-145">25%</span><span class="sxs-lookup"><span data-stu-id="38711-145">25%</span></span></td>
</tr><tr>
<td> <span data-ttu-id="38711-146">腳本/邏輯</span><span class="sxs-lookup"><span data-stu-id="38711-146">Script/logic</span></span></td><td> <span data-ttu-id="38711-147">25%</span><span class="sxs-lookup"><span data-stu-id="38711-147">25%</span></span></td><td> <span data-ttu-id="38711-148">0%</span><span class="sxs-lookup"><span data-stu-id="38711-148">0%</span></span></td><td> <span data-ttu-id="38711-149">5%</span><span class="sxs-lookup"><span data-stu-id="38711-149">5%</span></span></td>
</tr><tr>
<td> <span data-ttu-id="38711-150">一般負荷</span><span class="sxs-lookup"><span data-stu-id="38711-150">General overhead</span></span></td><td> <span data-ttu-id="38711-151">5%</span><span class="sxs-lookup"><span data-stu-id="38711-151">5%</span></span></td><td> <span data-ttu-id="38711-152">5%</span><span class="sxs-lookup"><span data-stu-id="38711-152">5%</span></span></td><td> <span data-ttu-id="38711-153">5%</span><span class="sxs-lookup"><span data-stu-id="38711-153">5%</span></span></td>
</tr><tr>
<td> <span data-ttu-id="38711-154"><b>總計</b></span><span class="sxs-lookup"><span data-stu-id="38711-154"><b>Total</b></span></span></td><td> <span data-ttu-id="38711-155"><b>65%</b></span><span class="sxs-lookup"><span data-stu-id="38711-155"><b>65%</b></span></span></td><td> <span data-ttu-id="38711-156"><b>90%</b></span><span class="sxs-lookup"><span data-stu-id="38711-156"><b>90%</b></span></span></td><td> <span data-ttu-id="38711-157"><b>70%</b></span><span class="sxs-lookup"><span data-stu-id="38711-157"><b>70%</b></span></span></td>
</tr>
</table>

<span data-ttu-id="38711-158">**總資產數**</span><span class="sxs-lookup"><span data-stu-id="38711-158">**Total number of assets**</span></span>
* <span data-ttu-id="38711-159">場景中有多少可用的資產？</span><span class="sxs-lookup"><span data-stu-id="38711-159">How many assets are active in the scene?</span></span>

<span data-ttu-id="38711-160">**資產的複雜度**</span><span class="sxs-lookup"><span data-stu-id="38711-160">**Complexity of assets**</span></span>
* <span data-ttu-id="38711-161">有多少三角形/多邊形？</span><span class="sxs-lookup"><span data-stu-id="38711-161">How many triangles / polygons?</span></span>
* <span data-ttu-id="38711-162">著色器有多複雜？</span><span class="sxs-lookup"><span data-stu-id="38711-162">How complex is the shader?</span></span> <span data-ttu-id="38711-163">使用混合現實工具組時，建議使用 [混合現實工具組標準著色器](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_MRTKStandardShader.md) 來減少著色器的複雜度。</span><span class="sxs-lookup"><span data-stu-id="38711-163">When using the Mixed Reality Toolkit, it is recommended to use the [Mixed Reality Toolkit Standard shader](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_MRTKStandardShader.md) to reduce shader complexity.</span></span>

<span data-ttu-id="38711-164">開發人員和演出者都必須考慮裝置和圖形引擎的功能。</span><span class="sxs-lookup"><span data-stu-id="38711-164">Both the developers and artists have to consider the capabilities of the device and the graphics engine.</span></span> <span data-ttu-id="38711-165">Microsoft HoloLens 具有裝置內建的所有計算和圖形。</span><span class="sxs-lookup"><span data-stu-id="38711-165">Microsoft HoloLens has all of the computational and graphics built into the device.</span></span> <span data-ttu-id="38711-166">它會共用開發人員可在行動平臺上找到的功能。</span><span class="sxs-lookup"><span data-stu-id="38711-166">It shares the capabilities developers would find on a mobile platform.</span></span>

<span data-ttu-id="38711-167">無論您是以全像全像 [裝置或沉浸式裝置](../discover/mixed-reality.md#the-mixed-reality-spectrum)的體驗為目標，資產的建立程式都相同。</span><span class="sxs-lookup"><span data-stu-id="38711-167">The creation process for assets is the same regardless of whether you're targeting an experience for a [holographic device or an immersive device](../discover/mixed-reality.md#the-mixed-reality-spectrum).</span></span> <span data-ttu-id="38711-168">要注意的主要事項是上述的裝置功能以及調整規模，因為您可以在混合現實中看到真實世界，所以您會想要根據體驗來維持正確的規模。</span><span class="sxs-lookup"><span data-stu-id="38711-168">The primary thing to note is the device capability as mentioned above as well as scale since you can see the real world in mixed reality you will want to maintain the correct scale based on the experience.</span></span>

## <a name="authoring-assets"></a><span data-ttu-id="38711-169">撰寫資產</span><span class="sxs-lookup"><span data-stu-id="38711-169">Authoring assets</span></span>

<span data-ttu-id="38711-170">我們將從取得專案資產的方法開始：</span><span class="sxs-lookup"><span data-stu-id="38711-170">We'll start with the ways to get assets for your project:</span></span>
1. <span data-ttu-id="38711-171">建立資產 (Authoring tools 和物件捕捉) </span><span class="sxs-lookup"><span data-stu-id="38711-171">Creating Assets (Authoring tools and object capture)</span></span>
2. <span data-ttu-id="38711-172">購買資產 (線上購買資產) </span><span class="sxs-lookup"><span data-stu-id="38711-172">Purchasing Assets (Buying assets online)</span></span>
3. <span data-ttu-id="38711-173"> (取得現有資產) 來移植資產</span><span class="sxs-lookup"><span data-stu-id="38711-173">Porting Assets (Taking existing assets)</span></span>
4. <span data-ttu-id="38711-174">從協力廠商匯入資產 (外包資產) </span><span class="sxs-lookup"><span data-stu-id="38711-174">Outsourcing Assets (Importing assets from 3rd parties)</span></span>

### <a name="creating-assets"></a><span data-ttu-id="38711-175">建立資產</span><span class="sxs-lookup"><span data-stu-id="38711-175">Creating assets</span></span>

<span data-ttu-id="38711-176">**Authoring tools**</span><span class="sxs-lookup"><span data-stu-id="38711-176">**Authoring tools**</span></span><br>
<span data-ttu-id="38711-177">首先，您可以使用數種不同的方式來建立自己的資產。</span><span class="sxs-lookup"><span data-stu-id="38711-177">First you can create your own assets in a number of different ways.</span></span> <span data-ttu-id="38711-178">3D 演出者使用許多應用程式和工具來建立包含 **網格**、 **材質** 和 **材質** 的模型。</span><span class="sxs-lookup"><span data-stu-id="38711-178">3D artists use a number of applications and tools to create models which consist of **meshes**, **textures**, and **materials**.</span></span> <span data-ttu-id="38711-179">然後，這會以檔案格式儲存，讓應用程式使用的圖形引擎可以匯入或使用，例如 **。FBX** 或 **。OBJ**。</span><span class="sxs-lookup"><span data-stu-id="38711-179">This is then saved in a file format that can be imported or used by the graphics engine used by the app, such as **.FBX** or **.OBJ**.</span></span> <span data-ttu-id="38711-180">任何產生您所選圖形引擎支援之模型的工具，都可以在 **HoloLens** 上運作。</span><span class="sxs-lookup"><span data-stu-id="38711-180">Any tool that generates a model that your chosen graphics engine supports will work on **HoloLens**.</span></span> <span data-ttu-id="38711-181">在3D 演出者之間，許多選擇使用 [Autodesk 的 Maya，其本身可以使用 HoloLens](https://www.youtube.com/watch?v=q0K3n0Gf8mA) 來轉換資產的建立方式。</span><span class="sxs-lookup"><span data-stu-id="38711-181">Among 3D artists, many choose to use [Autodesk’s Maya which itself is able to use HoloLens](https://www.youtube.com/watch?v=q0K3n0Gf8mA) to transform the way assets are created.</span></span> <span data-ttu-id="38711-182">如果您想要快速取得東西，也可以使用 Windows 所附的 [3D Builder](https://developer.microsoft.com/windows/hardware/3d-print/3d-builder-resources) 來匯出。要在應用程式中使用的 OBJ。</span><span class="sxs-lookup"><span data-stu-id="38711-182">If you want to get something in quick you can also use [3D Builder](https://developer.microsoft.com/windows/hardware/3d-print/3d-builder-resources) that comes with Windows to export .OBJ for use in your application.</span></span>

<span data-ttu-id="38711-183">**物件捕獲**</span><span class="sxs-lookup"><span data-stu-id="38711-183">**Object capture**</span></span><br>
<span data-ttu-id="38711-184">另外還有在3D 中捕捉物件的選項。</span><span class="sxs-lookup"><span data-stu-id="38711-184">There is also the option to capture objects in 3D.</span></span> <span data-ttu-id="38711-185">使用數位內容建立軟體來捕捉3D 中的無生命物件，並使用數位內容建立軟體進行編輯，在3D 列印的增加方面越來越普遍。</span><span class="sxs-lookup"><span data-stu-id="38711-185">Capturing inanimate objects in 3D and editing them with digital content creation software is increasingly popular with the rise of 3D printing.</span></span> <span data-ttu-id="38711-186">使用 **Kinect 2** 感應器和 [3D Builder](https://developer.microsoft.com/windows/hardware/3d-print/3d-builder-resources) 您可以使用「捕捉」功能，從真實世界的物件建立資產。</span><span class="sxs-lookup"><span data-stu-id="38711-186">Using the **Kinect 2** sensor and [3D Builder](https://developer.microsoft.com/windows/hardware/3d-print/3d-builder-resources) you can use the capture feature to create assets from real world objects.</span></span> <span data-ttu-id="38711-187">這也是一 [套工具](https://en.wikipedia.org/wiki/Comparison_of_photogrammetry_software) ，可透過處理一些影像來拼接以及網格和材質，來與 **攝影測量** 相同。</span><span class="sxs-lookup"><span data-stu-id="38711-187">This is also a [suite of tools](https://en.wikipedia.org/wiki/Comparison_of_photogrammetry_software) to do the same with **photogrammetry** by processing a number of images to stitch together and mesh and textures.</span></span>

### <a name="purchasing-assets"></a><span data-ttu-id="38711-188">購買資產</span><span class="sxs-lookup"><span data-stu-id="38711-188">Purchasing assets</span></span>

<span data-ttu-id="38711-189">另一個絕佳的選項是購買資產以供您體驗。</span><span class="sxs-lookup"><span data-stu-id="38711-189">Another excellent option is to purchase assets for your experience.</span></span> <span data-ttu-id="38711-190">有許多資產可透過 [Unity 資產存放區](https://www.assetstore.unity3d.com/) 或 [TurboSquid](https://www.turbosquid.com/) 等服務使用。</span><span class="sxs-lookup"><span data-stu-id="38711-190">There are a ton of assets available through services such as the [Unity Asset Store](https://www.assetstore.unity3d.com/) or [TurboSquid](https://www.turbosquid.com/) among others.</span></span>

<span data-ttu-id="38711-191">當您從協力廠商購買資產時，一律要檢查下列各項：</span><span class="sxs-lookup"><span data-stu-id="38711-191">When you purchase assets from a 3rd party you always want to check the following:</span></span>
* <span data-ttu-id="38711-192">**Poly 計數為何？**</span><span class="sxs-lookup"><span data-stu-id="38711-192">**What's the poly count?**</span></span>
  * <span data-ttu-id="38711-193">它是否適合您的預算？</span><span class="sxs-lookup"><span data-stu-id="38711-193">Does it fit within your budget?</span></span>
* <span data-ttu-id="38711-194">**模型有 (LODs) 的詳細資料層級嗎？**</span><span class="sxs-lookup"><span data-stu-id="38711-194">**Are there levels of detail (LODs) for the model?**</span></span>
  * <span data-ttu-id="38711-195">模型的詳細資料層級可讓您針對效能調整模型的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="38711-195">Level of detail of a model allow you to scale the detail of a model for performance.</span></span>
* <span data-ttu-id="38711-196">**來源檔案是否可供使用？**</span><span class="sxs-lookup"><span data-stu-id="38711-196">**Is the source file available?**</span></span>
  * <span data-ttu-id="38711-197">通常不會隨附于 [Unity 資產存放區](https://www.assetstore.unity3d.com/) ，但一律會包含在服務（例如 [TurboSquid](https://www.turbosquid.com/)）中。</span><span class="sxs-lookup"><span data-stu-id="38711-197">Usually not included with [Unity Asset Store](https://www.assetstore.unity3d.com/) but always included with services like [TurboSquid](https://www.turbosquid.com/).</span></span>
  * <span data-ttu-id="38711-198">如果沒有來源檔案，您將無法修改資產。</span><span class="sxs-lookup"><span data-stu-id="38711-198">Without the source file you won't be able to modify the asset.</span></span>
  * <span data-ttu-id="38711-199">請確定您的3D 工具可以匯入所提供的原始程式檔。</span><span class="sxs-lookup"><span data-stu-id="38711-199">Make sure the source file provided can be imported by your 3D tools.</span></span>
* <span data-ttu-id="38711-200">**知道您要取得的內容**</span><span class="sxs-lookup"><span data-stu-id="38711-200">**Know what you're getting**</span></span>
  * <span data-ttu-id="38711-201">是否提供動畫？</span><span class="sxs-lookup"><span data-stu-id="38711-201">Are animations provided?</span></span>
  * <span data-ttu-id="38711-202">請務必檢查您所購買資產的內容清單。</span><span class="sxs-lookup"><span data-stu-id="38711-202">Make sure to check the contents list of the asset you're purchasing.</span></span>

### <a name="porting-assets"></a><span data-ttu-id="38711-203">移植資產</span><span class="sxs-lookup"><span data-stu-id="38711-203">Porting assets</span></span>

<span data-ttu-id="38711-204">在某些情況下，您將會取得原本為其他裝置和不同應用程式建立的現有資產。</span><span class="sxs-lookup"><span data-stu-id="38711-204">In some cases you'll be handed existing assets that were originally built for other devices and different apps.</span></span> <span data-ttu-id="38711-205">在大部分情況下，這些資產可以轉換成與應用程式所使用之圖形引擎相容的格式。</span><span class="sxs-lookup"><span data-stu-id="38711-205">In most cases these assets can be converted to formats compatible with the graphics engine their app is using.</span></span>

<span data-ttu-id="38711-206">在您的 HoloLens 應用程式中移植要使用的資產時，您會想要詢問下列各項：</span><span class="sxs-lookup"><span data-stu-id="38711-206">When porting assets to use in your HoloLens application you will want to ask the following:</span></span>
* <span data-ttu-id="38711-207">**您可以直接匯入或需要轉換成另一種格式嗎？**</span><span class="sxs-lookup"><span data-stu-id="38711-207">**Can you import directly or does need to be converted to another format?**</span></span> <span data-ttu-id="38711-208">使用您所使用的圖形引擎來檢查您要匯入的格式。</span><span class="sxs-lookup"><span data-stu-id="38711-208">Check the format you're importing with the graphics engine you're using.</span></span>
* <span data-ttu-id="38711-209">**如果轉換成相容的格式，是否有任何遺失？**</span><span class="sxs-lookup"><span data-stu-id="38711-209">**If converting to a compatible format is anything lost?**</span></span> <span data-ttu-id="38711-210">有時詳細資料可能會遺失或匯入，可能會導致需要在 3D authoring tool 中清除的成品。</span><span class="sxs-lookup"><span data-stu-id="38711-210">Sometimes details can be lost or importing can cause artifacts that need to be cleaned up in a 3D authoring tool.</span></span>
* <span data-ttu-id="38711-211">**資產的三角形/多邊形計數為何？**</span><span class="sxs-lookup"><span data-stu-id="38711-211">**What is the triangles / polygons count for the asset?**</span></span> <span data-ttu-id="38711-212">根據您的應用程式預算，您可以使用 [Simplygon](https://www.simplygon.com/) 或類似的工具來刪減 (cti，或手動減少) 原始資產的 poly 計數，以符合您的應用程式預算。</span><span class="sxs-lookup"><span data-stu-id="38711-212">Based on the budget for you application you can use [Simplygon](https://www.simplygon.com/) or similar tools to decimate (procedurally or manually reduce poly count) the original asset to fit within your applications budget.</span></span>

### <a name="outsourcing-assets"></a><span data-ttu-id="38711-213">外包資產</span><span class="sxs-lookup"><span data-stu-id="38711-213">Outsourcing assets</span></span>

<span data-ttu-id="38711-214">如果大型專案需要比您的小組更多的資產，則另一個選項是建立資產建立。</span><span class="sxs-lookup"><span data-stu-id="38711-214">Another option for larger projects that require more assets than your team is equipped to create is to outsource asset creation.</span></span> <span data-ttu-id="38711-215">外包的程式牽涉到尋找專門參與外包資產的適當 studio 或機構。</span><span class="sxs-lookup"><span data-stu-id="38711-215">The process of outsourcing involves finding the right studio or agency that specializes in outsourcing assets.</span></span> <span data-ttu-id="38711-216">這可能是最昂貴的選項，但也是最具彈性的選項。</span><span class="sxs-lookup"><span data-stu-id="38711-216">This can be the most expensive option but also be the most flexible in what you get.</span></span>
* <span data-ttu-id="38711-217">**清楚地定義您所要求的內容**</span><span class="sxs-lookup"><span data-stu-id="38711-217">**Clearly define what you're requesting**</span></span>
  * <span data-ttu-id="38711-218">盡可能提供最多詳細資料</span><span class="sxs-lookup"><span data-stu-id="38711-218">Provide as much detail as possible</span></span>
  * <span data-ttu-id="38711-219">前端和後端概念影像</span><span class="sxs-lookup"><span data-stu-id="38711-219">Front, side and back concept images</span></span>
  * <span data-ttu-id="38711-220">顯示內容中資產的參考圖片</span><span class="sxs-lookup"><span data-stu-id="38711-220">Reference art showing asset in context</span></span>
  * <span data-ttu-id="38711-221">物件的小數位數 (通常以公分為單位指定) </span><span class="sxs-lookup"><span data-stu-id="38711-221">Scale of object (Usually specified in centimeters)</span></span>
* <span data-ttu-id="38711-222">**提供預算**</span><span class="sxs-lookup"><span data-stu-id="38711-222">**Provide a Budget**</span></span>
  * <span data-ttu-id="38711-223">Poly 計數範圍</span><span class="sxs-lookup"><span data-stu-id="38711-223">Poly count range</span></span>
  * <span data-ttu-id="38711-224">紋理數目</span><span class="sxs-lookup"><span data-stu-id="38711-224">Number of textures</span></span>
  * <span data-ttu-id="38711-225">Unity 和 HoloLens 的著色器 (類型，一律預設為行動著色器優先) </span><span class="sxs-lookup"><span data-stu-id="38711-225">Type of shader (For Unity and HoloLens you should always default to mobile shaders first)</span></span>
* <span data-ttu-id="38711-226">**瞭解成本**</span><span class="sxs-lookup"><span data-stu-id="38711-226">**Understand the costs**</span></span>
  * <span data-ttu-id="38711-227">變更要求的外包原則是什麼？</span><span class="sxs-lookup"><span data-stu-id="38711-227">What's the outsourcing policy for change requests?</span></span>

<span data-ttu-id="38711-228">外包可以根據您的專案時程表來運作得非常順利，但需要更多監督才能保證您第一次就能取得所需的正確資產。</span><span class="sxs-lookup"><span data-stu-id="38711-228">Outsourcing can work extremely well based on your projects timeline but requires more oversight to guarantee that you get the right assets you need the first time.</span></span>
