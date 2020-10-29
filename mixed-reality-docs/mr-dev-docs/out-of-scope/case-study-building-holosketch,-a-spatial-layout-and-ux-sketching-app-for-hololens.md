---
title: 案例研究-建立 HoloSketch、適用于 HoloLens 的空間配置和 UX 草圖應用程式
description: HoloSketch 是適用于 HoloLens 的裝置空間配置和 UX 草圖工具，可協助打造全像攝影體驗。
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: HoloSketch、HoloLens、Windows Mixed Reality、草圖、應用程式
ms.openlocfilehash: 4cb5b6a0a0e057bafb7820d8893b2561b44a2d7e
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2020
ms.locfileid: "91680577"
---
# <a name="case-study---building-holosketch-a-spatial-layout-and-ux-sketching-app-for-hololens"></a><span data-ttu-id="ba9f3-104">案例研究-建立 HoloSketch、適用于 HoloLens 的空間配置和 UX 草圖應用程式</span><span class="sxs-lookup"><span data-stu-id="ba9f3-104">Case study - Building HoloSketch, a spatial layout and UX sketching app for HoloLens</span></span>

<span data-ttu-id="ba9f3-105">HoloSketch 是適用于 HoloLens 的裝置空間配置和 UX 草圖工具，可協助打造全像攝影體驗。</span><span class="sxs-lookup"><span data-stu-id="ba9f3-105">HoloSketch is an on-device spatial layout and UX sketching tool for HoloLens to help build holographic experiences.</span></span> <span data-ttu-id="ba9f3-106">HoloSketch 適用于配對的藍牙鍵盤和滑鼠，以及手勢和語音命令。</span><span class="sxs-lookup"><span data-stu-id="ba9f3-106">HoloSketch works with a paired Bluetooth keyboard and mouse as well as gesture and voice commands.</span></span> <span data-ttu-id="ba9f3-107">HoloSketch 的目的是要提供簡單的 UX 版面組態工具，以進行快速的視覺效果和反復專案。</span><span class="sxs-lookup"><span data-stu-id="ba9f3-107">The purpose of HoloSketch is to provide a simple UX layout tool for quick visualization and iteration.</span></span>

<span data-ttu-id="ba9f3-108">![HoloSketch：適用于 HoloLens 的空間配置和 UX 草圖應用程式。](images/holosketch-image-01-640px.png)</span><span class="sxs-lookup"><span data-stu-id="ba9f3-108">![HoloSketch: A spatial layout and UX sketching app for HoloLens.](images/holosketch-image-01-640px.png)</span></span><br>
<span data-ttu-id="ba9f3-109">*HoloSketch： HoloLens 的空間配置和 UX 草圖應用程式*</span><span class="sxs-lookup"><span data-stu-id="ba9f3-109">*HoloSketch: spatial layout and UX sketching app for HoloLens*</span></span>

<span data-ttu-id="ba9f3-110">![適用于快速視覺化和反復專案的簡單 UX 版面組態工具。](images/holosketch-image-02.png)</span><span class="sxs-lookup"><span data-stu-id="ba9f3-110">![A simple UX layout tool for quick visualization and iteration.](images/holosketch-image-02.png)</span></span><br>
<span data-ttu-id="ba9f3-111">*適用于快速視覺化和反復專案的簡單 UX 版面組態工具*</span><span class="sxs-lookup"><span data-stu-id="ba9f3-111">*A simple UX layout tool for quick visualization and iteration*</span></span>

## <a name="features"></a><span data-ttu-id="ba9f3-112">特性</span><span class="sxs-lookup"><span data-stu-id="ba9f3-112">Features</span></span>

### <a name="primitives-for-quick-studies-and-scale-prototyping"></a><span data-ttu-id="ba9f3-113">用於快速研究和調整原型的基本專案</span><span class="sxs-lookup"><span data-stu-id="ba9f3-113">Primitives for quick studies and scale-prototyping</span></span>

![使用基本圖形](images/holosketch-primitives-giphy.gif)

<span data-ttu-id="ba9f3-115">使用基本圖形來進行快速 massing 研究和調整原型。</span><span class="sxs-lookup"><span data-stu-id="ba9f3-115">Use primitive shapes for quick massing studies and scale-prototyping.</span></span>

### <a name="import-objects-through-onedrive"></a><span data-ttu-id="ba9f3-116">透過 OneDrive 匯入物件</span><span class="sxs-lookup"><span data-stu-id="ba9f3-116">Import objects through OneDrive</span></span>

![匯入物件](images/holosketch-importobjects-giphy.gif)

<span data-ttu-id="ba9f3-118">匯入 PNG/JPG 影像或 3D FBX 物件 (需要透過 OneDrive 將 Unity) 封裝到混合現實空間中。</span><span class="sxs-lookup"><span data-stu-id="ba9f3-118">Import PNG/JPG images or 3D FBX objects(requires packaging in Unity) into the mixed reality space through OneDrive.</span></span>

### <a name="manipulate-objects"></a><span data-ttu-id="ba9f3-119">操作物件</span><span class="sxs-lookup"><span data-stu-id="ba9f3-119">Manipulate objects</span></span>

![操作物件](images/manipulate-objects-640px.jpg)

<span data-ttu-id="ba9f3-121">使用熟悉的3D 物件介面，操作物件 (移動/旋轉/調整) 。</span><span class="sxs-lookup"><span data-stu-id="ba9f3-121">Manipulate objects (move/rotate/scale) with a familiar 3D object interface.</span></span>

### <a name="bluetooth-mousekeyboard-gestures-and-voice-commands"></a><span data-ttu-id="ba9f3-122">藍牙、滑鼠/鍵盤、手勢和語音命令</span><span class="sxs-lookup"><span data-stu-id="ba9f3-122">Bluetooth, mouse/keyboard, gestures and voice commands</span></span>

![支援藍牙](images/supports-bluetooth-640px.jpg)

<span data-ttu-id="ba9f3-124">HoloSketch 支援藍牙滑鼠/鍵盤、手勢和語音命令。</span><span class="sxs-lookup"><span data-stu-id="ba9f3-124">HoloSketch supports Bluetooth mouse/keyboard, gestures and voice commands.</span></span>

## <a name="background"></a><span data-ttu-id="ba9f3-125">背景</span><span class="sxs-lookup"><span data-stu-id="ba9f3-125">Background</span></span>

### <a name="importance-of-experiencing-your-design-in-the-device"></a><span data-ttu-id="ba9f3-126">在裝置中體驗您設計的重要性</span><span class="sxs-lookup"><span data-stu-id="ba9f3-126">Importance of experiencing your design in the device</span></span>

<span data-ttu-id="ba9f3-127">當您針對 HoloLens 設計某項功能時，請務必在裝置中體驗您的設計。</span><span class="sxs-lookup"><span data-stu-id="ba9f3-127">When you design something for HoloLens, it is important to experience your design in the device.</span></span> <span data-ttu-id="ba9f3-128">混合現實應用程式設計中最大的挑戰之一，就是很難得到調整、定位和深度的意義，尤其是透過傳統2D 草圖。</span><span class="sxs-lookup"><span data-stu-id="ba9f3-128">One of the biggest challenges in mixed reality app design is that it is hard to get the sense of scale, position and depth, especially through traditional 2D sketches.</span></span>

### <a name="cost-of-2d-based-communication"></a><span data-ttu-id="ba9f3-129">以2D 為基礎的通訊成本</span><span class="sxs-lookup"><span data-stu-id="ba9f3-129">Cost of 2D based communication</span></span>

<span data-ttu-id="ba9f3-130">為了有效地與其他人溝通 UX 流程和案例，設計人員可能會花很多時間使用傳統2D 工具（例如 Illustrator、Photoshop 和 PowerPoint）來建立資產。</span><span class="sxs-lookup"><span data-stu-id="ba9f3-130">To effectively communicate UX flows and scenarios to others, a designer may end up spending a lot of time creating assets using traditional 2D tools such as Illustrator, Photoshop and PowerPoint.</span></span> <span data-ttu-id="ba9f3-131">這些2D 設計通常需要額外努力才能將其轉換成3D。</span><span class="sxs-lookup"><span data-stu-id="ba9f3-131">These 2D designs often require additional effort to convert them it into 3D.</span></span> <span data-ttu-id="ba9f3-132">從2D 到3D 的這項轉譯會遺失某些想法。</span><span class="sxs-lookup"><span data-stu-id="ba9f3-132">Some ideas are lost in this translation from 2D to 3D.</span></span>

### <a name="complex-deployment-process"></a><span data-ttu-id="ba9f3-133">複雜的部署流程</span><span class="sxs-lookup"><span data-stu-id="ba9f3-133">Complex deployment process</span></span>

<span data-ttu-id="ba9f3-134">由於混合現實是我們的新畫布，因此它的本質牽涉到許多設計反復專案和試用版和錯誤。</span><span class="sxs-lookup"><span data-stu-id="ba9f3-134">Since mixed reality is a new canvas for us, it involves a lot of design iteration and trial and error by its nature.</span></span> <span data-ttu-id="ba9f3-135">針對不熟悉 Unity 和 Visual Studio 等工具的設計工具，不容易在 HoloLens 中放入一些東西。</span><span class="sxs-lookup"><span data-stu-id="ba9f3-135">For designer who are not familiar with tools such as Unity and Visual Studio, it is not easy to put something together in HoloLens.</span></span> <span data-ttu-id="ba9f3-136">一般來說，您必須完成下列程式，才能查看裝置中的 2D/3D 插圖。</span><span class="sxs-lookup"><span data-stu-id="ba9f3-136">Typically you have to go through the process below to see your 2D/3D artwork in the device.</span></span> <span data-ttu-id="ba9f3-137">這是讓設計人員快速逐一查看構想和案例的大障礙。</span><span class="sxs-lookup"><span data-stu-id="ba9f3-137">This was a big barrier for designers iterating on ideas and scenarios quickly.</span></span>

<span data-ttu-id="ba9f3-138">![複雜的部署流程](images/holosketch-image-03-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="ba9f3-138">![Complex deployment process](images/holosketch-image-03-1000px.png)</span></span><br>
<span data-ttu-id="ba9f3-139">*部署程序*</span><span class="sxs-lookup"><span data-stu-id="ba9f3-139">*Deployment process*</span></span>

### <a name="simplified-process-with-holosketch"></a><span data-ttu-id="ba9f3-140">使用 HoloSketch 簡化的進程</span><span class="sxs-lookup"><span data-stu-id="ba9f3-140">Simplified process with HoloSketch</span></span>

<span data-ttu-id="ba9f3-141">有了 HoloSketch，我們想要簡化此程式，而不涉及開發工具和裝置入口網站配對。</span><span class="sxs-lookup"><span data-stu-id="ba9f3-141">With HoloSketch, we wanted to simplify this process without involving development tools and device portal pairing.</span></span> <span data-ttu-id="ba9f3-142">使用 OneDrive，使用者可以輕鬆地將 2D/3D 資產放入 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="ba9f3-142">Using OneDrive, users can easily put 2D/3D assets into HoloLens.</span></span>

<span data-ttu-id="ba9f3-143">![使用 HoloSketch 簡化的進程](images/holosketch-image-04-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="ba9f3-143">![Simplified process with HoloSketch](images/holosketch-image-04-1000px.png)</span></span><br>
<span data-ttu-id="ba9f3-144">*使用 HoloSketch 簡化的進程*</span><span class="sxs-lookup"><span data-stu-id="ba9f3-144">*Simplified process with HoloSketch*</span></span>

### <a name="encouraging-three-dimensional-design-thinking-and-solutions"></a><span data-ttu-id="ba9f3-145">鼓勵三維設計思考與解決方案</span><span class="sxs-lookup"><span data-stu-id="ba9f3-145">Encouraging three-dimensional design thinking and solutions</span></span>

<span data-ttu-id="ba9f3-146">我們認為這項工具會讓設計人員有機會在真正的立體空間中探索解決方案，而不會停滯在2D 中。</span><span class="sxs-lookup"><span data-stu-id="ba9f3-146">We thought this tool would give designers an opportunity to explore solutions in a truly three-dimensional space and not be stuck in 2D.</span></span> <span data-ttu-id="ba9f3-147">他們不需要考慮為其 UI 建立3D 背景，因為在 HoloLens 的情況下，背景是真實世界。</span><span class="sxs-lookup"><span data-stu-id="ba9f3-147">They don’t have to think about creating a 3D background for their UI since the background is the real world in the case of HoloLens.</span></span> <span data-ttu-id="ba9f3-148">HoloSketch 開啟了一個方法，讓設計人員可以輕鬆地在 HoloLens 上探索3D 設計。</span><span class="sxs-lookup"><span data-stu-id="ba9f3-148">HoloSketch opens up a way for designers to easily explore 3D design on HoloLens.</span></span>

## <a name="get-started"></a><span data-ttu-id="ba9f3-149">開始使用</span><span class="sxs-lookup"><span data-stu-id="ba9f3-149">Get Started</span></span>

### <a name="how-to-import-2d-images-jpgpng-into-holosketch"></a><span data-ttu-id="ba9f3-150">如何將 (JPG/PNG) 的2D 影像匯入 HoloSketch</span><span class="sxs-lookup"><span data-stu-id="ba9f3-150">How to import 2D images (JPG/PNG) into HoloSketch</span></span>

* <span data-ttu-id="ba9f3-151">將 JPG/PNG 影像上傳至您的 OneDrive 資料夾 ' Documents/HoloSketch '。</span><span class="sxs-lookup"><span data-stu-id="ba9f3-151">Upload JPG/PNG images to your OneDrive folder ‘Documents/HoloSketch’.</span></span>
* <span data-ttu-id="ba9f3-152">從 HoloSketch 的 [OneDrive] 功能表中，您將能夠選取並將映射放在環境中。</span><span class="sxs-lookup"><span data-stu-id="ba9f3-152">From the OneDrive menu in HoloSketch, you will be able to select and place the image in the environment.</span></span>

<span data-ttu-id="ba9f3-153">![匯入2D 影像](images/import-2d-images-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="ba9f3-153">![Importing 2D images](images/import-2d-images-1000px.jpg)</span></span><br>
<span data-ttu-id="ba9f3-154">*透過 OneDrive 匯入影像和3D 物件*</span><span class="sxs-lookup"><span data-stu-id="ba9f3-154">*Importing images and 3D objects through OneDrive*</span></span>

### <a name="how-to-import-3d-objects-into-holosketch"></a><span data-ttu-id="ba9f3-155">如何將3D 物件匯入 HoloSketch</span><span class="sxs-lookup"><span data-stu-id="ba9f3-155">How to import 3D objects into HoloSketch</span></span>

<span data-ttu-id="ba9f3-156">上傳至您的 OneDrive 資料夾之前，請遵循下列步驟，將您的3D 物件封裝至 Unity 資產套件組合。</span><span class="sxs-lookup"><span data-stu-id="ba9f3-156">Before uploading to your OneDrive folder, please follow the steps below to package your 3D objects into a Unity asset bundle.</span></span> <span data-ttu-id="ba9f3-157">您可以使用此程式從3D 軟體（例如 Maya、電影院4D 和 Microsoft 小畫家3D）匯入 FBX/OBJ 檔案。</span><span class="sxs-lookup"><span data-stu-id="ba9f3-157">Using this process you can import your FBX/OBJ files from 3D software such as Maya, Cinema 4D and Microsoft Paint 3D.</span></span>

>[!IMPORTANT]
><span data-ttu-id="ba9f3-158">目前，Unity 版本5.4.5 節 f1 支援資產組合建立。</span><span class="sxs-lookup"><span data-stu-id="ba9f3-158">Currently, asset bundle creation is supported with Unity version 5.4.5f1.</span></span>

1. <span data-ttu-id="ba9f3-159">下載並開啟 Unity 專案 [' AssetBunlder_Unity '](https://github.com/Microsoft/MRDesignLabs/tree/master/ReleasedApps/HoloSketch/AssetBundler_Unity)。</span><span class="sxs-lookup"><span data-stu-id="ba9f3-159">Download and open the Unity project ['AssetBunlder_Unity'](https://github.com/Microsoft/MRDesignLabs/tree/master/ReleasedApps/HoloSketch/AssetBundler_Unity).</span></span> <span data-ttu-id="ba9f3-160">此 Unity 專案包含產生配套資產的腳本。</span><span class="sxs-lookup"><span data-stu-id="ba9f3-160">This Unity project includes the script for the bundle asset generation.</span></span>
2. <span data-ttu-id="ba9f3-161">建立新的 GameObject。</span><span class="sxs-lookup"><span data-stu-id="ba9f3-161">Create a new GameObject.</span></span>
3. <span data-ttu-id="ba9f3-162">以內容為基礎來命名 GameObject。</span><span class="sxs-lookup"><span data-stu-id="ba9f3-162">Name the GameObject based on the contents.</span></span>
4. <span data-ttu-id="ba9f3-163">在 [偵測器] 面板中，按一下 [新增元件]，然後新增 [方塊碰撞器]。</span><span class="sxs-lookup"><span data-stu-id="ba9f3-163">In the Inspector panel, click ‘Add Component’ and add ‘Box Collider’.</span></span> 

   ![在 [偵測器] 面板中，按一下 [新增元件]，然後新增 [方塊碰撞器]](images/holosketch-10a-assetbundles-1000px.png)
   
   ![在 [偵測器] 面板中，按一下 [新增元件]，然後新增 [方塊碰撞器] #2](images/holosketch-10b-assetbundles-1000px.png)

5. <span data-ttu-id="ba9f3-166">將 3D FBX 檔案拖曳至 [專案] 面板中，以匯入該檔案。</span><span class="sxs-lookup"><span data-stu-id="ba9f3-166">Import the 3D FBX file by dragging it into the project panel.</span></span>
6. <span data-ttu-id="ba9f3-167">將物件拖曳至 **新 GameObject 下** 的 [階層] 面板中。</span><span class="sxs-lookup"><span data-stu-id="ba9f3-167">Drag the object into the Hierarchy panel **under your new GameObject** .</span></span>

   ![將物件拖曳至新 GameObject 底下的階層面板](images/holosketch-12-assetbundles-1000px.png)

7. <span data-ttu-id="ba9f3-169">如果碰撞項維度不符合物件，則調整其大小。</span><span class="sxs-lookup"><span data-stu-id="ba9f3-169">Adjust the collider dimension if it does not match the object.</span></span> <span data-ttu-id="ba9f3-170">將物件旋轉為臉部 **Z 軸** 。</span><span class="sxs-lookup"><span data-stu-id="ba9f3-170">Rotate the object to face **Z-axis** .</span></span>

   ![調整碰撞維度（如果它不符合物件）。](images/holosketch-13-assetbundles-1000px.png)

8. <span data-ttu-id="ba9f3-172">將物件從 [階層] 面板拖曳至 [專案] 面板， **讓它預製專案** 。</span><span class="sxs-lookup"><span data-stu-id="ba9f3-172">Drag the object from the Hierarchy panel to the Project panel to **make it prefab** .</span></span>
9. <span data-ttu-id="ba9f3-173">在 [偵測器] 面板底部，按一下下拉式清單，建立並指派新的唯一名稱。</span><span class="sxs-lookup"><span data-stu-id="ba9f3-173">On the bottom of the inspector panel, click the dropdown, create and assign a new unique name.</span></span> <span data-ttu-id="ba9f3-174">下列範例顯示如何為 AssetBundle 名稱新增和指派 ' brownchair '。</span><span class="sxs-lookup"><span data-stu-id="ba9f3-174">Below example shows adding and assigning 'brownchair' for the AssetBundle Name.</span></span> 

   ![在 [偵測器] 面板底部，按一下下拉式清單，然後指派新的唯一名稱。](images/holosketch-14-assetbundles-1000px.png)

10. <span data-ttu-id="ba9f3-176">準備模型物件的縮圖影像。</span><span class="sxs-lookup"><span data-stu-id="ba9f3-176">Prepare a thumbnail image for the model object.</span></span> 
   <span data-ttu-id="ba9f3-177">![將影像拖曳至 [專案] 面板中，並指派用於物件的名稱。](images/holosketch-15-assetbundles-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="ba9f3-177">![Drag an image into the project panel and assign the name used for the object.](images/holosketch-15-assetbundles-1000px.png)</span></span>

11. <span data-ttu-id="ba9f3-178">在 Unity 專案的 [資產] 資料夾下建立名為 ' Assetbundles ' 的資料夾。</span><span class="sxs-lookup"><span data-stu-id="ba9f3-178">Create a folder named ‘Assetbundles’ under the Unity project’s ‘Asset’ folder.</span></span>

12. <span data-ttu-id="ba9f3-179">在 [資產] 功能表中，選取 [組建 AssetBundles] 以產生檔案。</span><span class="sxs-lookup"><span data-stu-id="ba9f3-179">From the Assets menu, select ‘Build AssetBundles’ to generate file.</span></span> 
   <span data-ttu-id="ba9f3-180">![在 [資產] 功能表中，選取 [組建 AssetBundles] 以產生檔案。](images/holosketch-15a-assetbundles.png)</span><span class="sxs-lookup"><span data-stu-id="ba9f3-180">![From the Assets menu, select ‘Build AssetBundles’ to generate file.](images/holosketch-15a-assetbundles.png)</span></span>


13. <span data-ttu-id="ba9f3-181">**將產生的檔案上傳至 OneDrive 上的/Files/Documents/HoloSketch 資料夾。**</span><span class="sxs-lookup"><span data-stu-id="ba9f3-181">**Upload the generated file to the /Files/Documents/HoloSketch folder on OneDrive.**</span></span> <span data-ttu-id="ba9f3-182">僅上傳 asset_unique_name 檔案。</span><span class="sxs-lookup"><span data-stu-id="ba9f3-182">Upload the asset_unique_name file only.</span></span> <span data-ttu-id="ba9f3-183">您不需要上傳資訊清單檔案或 AssetBundles 檔案。</span><span class="sxs-lookup"><span data-stu-id="ba9f3-183">You don’t need to upload manifest files or AssetBundles file.</span></span> <br>
<span data-ttu-id="ba9f3-184">![將檔案新增至檔案/檔/HoloSketch/資料夾 ](images/holosketch-onedriveupload-1000px.png)
 ![ 您會在 HoloSketch 的 OneDrive 功能表中看到新增的3d 物件](images/holosketch-14-onedriveexample-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="ba9f3-184">![Add files to Files/Documents/HoloSketch/ folder](images/holosketch-onedriveupload-1000px.png)
![You will see added 3D object in HoloSketch's OneDrive menu](images/holosketch-14-onedriveexample-1000px.jpg)</span></span>

## <a name="how-to-manipulate-the-objects"></a><span data-ttu-id="ba9f3-185">如何操作物件</span><span class="sxs-lookup"><span data-stu-id="ba9f3-185">How to manipulate the objects</span></span>

<span data-ttu-id="ba9f3-186">HoloSketch 支援廣泛用於3D 軟體的傳統介面。</span><span class="sxs-lookup"><span data-stu-id="ba9f3-186">HoloSketch supports the traditional interface that is widely used in 3D software.</span></span> <span data-ttu-id="ba9f3-187">您可以使用移動、旋轉、使用筆勢和滑鼠來縮放物件。</span><span class="sxs-lookup"><span data-stu-id="ba9f3-187">You can use move, rotate, scale the objects with gestures and a mouse.</span></span> <span data-ttu-id="ba9f3-188">您可以使用語音或鍵盤在不同模式之間快速切換。</span><span class="sxs-lookup"><span data-stu-id="ba9f3-188">You can quickly switch between different modes with voice or keyboard.</span></span>

### <a name="object-manipulation-modes"></a><span data-ttu-id="ba9f3-189">物件操作模式</span><span class="sxs-lookup"><span data-stu-id="ba9f3-189">Object manipulation modes</span></span>

<span data-ttu-id="ba9f3-190">![如何操作物件](images/holosketch-image-06-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="ba9f3-190">![How to manipulate the objects](images/holosketch-image-06-1000px.png)</span></span><br>
<span data-ttu-id="ba9f3-191">*如何操作物件*</span><span class="sxs-lookup"><span data-stu-id="ba9f3-191">*How to manipulate the objects*</span></span>

### <a name="contextual-and-tool-belt-menus"></a><span data-ttu-id="ba9f3-192">內容和工具皮帶功能表</span><span class="sxs-lookup"><span data-stu-id="ba9f3-192">Contextual and Tool Belt menus</span></span>

<span data-ttu-id="ba9f3-193">**使用操作功能表**</span><span class="sxs-lookup"><span data-stu-id="ba9f3-193">**Using the Contextual Menu**</span></span>

<span data-ttu-id="ba9f3-194">按兩下以開啟內容功能表。</span><span class="sxs-lookup"><span data-stu-id="ba9f3-194">Double air tap to open the Contextual Menu.</span></span> 

<span data-ttu-id="ba9f3-195">功能表項目：</span><span class="sxs-lookup"><span data-stu-id="ba9f3-195">Menu items:</span></span>
* <span data-ttu-id="ba9f3-196">**版面配置介面：** 這是3D 格線系統，您可以在其中配置多個物件，並以群組方式管理它們。</span><span class="sxs-lookup"><span data-stu-id="ba9f3-196">**Layout Surface:** This is a 3D grid system where you can layout multiple objects and manage them as a group.</span></span> <span data-ttu-id="ba9f3-197">按兩下版面配置介面，將物件新增至其中。</span><span class="sxs-lookup"><span data-stu-id="ba9f3-197">Double air-tap on the Layout Surface to add objects to it.</span></span>
* <span data-ttu-id="ba9f3-198">**基本：** 使用 cube、球體、圓柱和圓錐 massing 研究。</span><span class="sxs-lookup"><span data-stu-id="ba9f3-198">**Primitives:** Use cubes, spheres, cylinders and cones for massing studies.</span></span>
* <span data-ttu-id="ba9f3-199">**OneDrive：** 開啟 OneDrive 功能表以匯入物件。</span><span class="sxs-lookup"><span data-stu-id="ba9f3-199">**OneDrive:** Open the OneDrive menu to import objects.</span></span>
* <span data-ttu-id="ba9f3-200">說明 **：** 顯示說明畫面。</span><span class="sxs-lookup"><span data-stu-id="ba9f3-200">**Help:** Displays help screen.</span></span>

<span data-ttu-id="ba9f3-201">![操作功能表](images/holosketch-image-07.png)</span><span class="sxs-lookup"><span data-stu-id="ba9f3-201">![Contextual menu](images/holosketch-image-07.png)</span></span><br>
<span data-ttu-id="ba9f3-202">*操作功能表*</span><span class="sxs-lookup"><span data-stu-id="ba9f3-202">*Contextual menu*</span></span>

<span data-ttu-id="ba9f3-203">**使用工具功能表**</span><span class="sxs-lookup"><span data-stu-id="ba9f3-203">**Using the Tool Belt Menu**</span></span>

<span data-ttu-id="ba9f3-204">您可以從工具功能表使用移動、旋轉、縮放、儲存和載入場景。</span><span class="sxs-lookup"><span data-stu-id="ba9f3-204">Move, Rotate, Scale, Save, and Load Scene are available from the Tool Belt Menu.</span></span> 

## <a name="using-keyboard-gestures-and-voice-commands"></a><span data-ttu-id="ba9f3-205">使用鍵盤、手勢和語音命令</span><span class="sxs-lookup"><span data-stu-id="ba9f3-205">Using keyboard, gestures and voice commands</span></span>

<span data-ttu-id="ba9f3-206">![鍵盤、手勢和語音命令](images/holosketch-image-08-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="ba9f3-206">![Keyboard, Gestures and Voice Commands](images/holosketch-image-08-1000px.png)</span></span><br>
<span data-ttu-id="ba9f3-207">*鍵盤、手勢和語音命令*</span><span class="sxs-lookup"><span data-stu-id="ba9f3-207">*Keyboard, gestures, and voice commands*</span></span>

## <a name="download-the-app"></a><span data-ttu-id="ba9f3-208">下載此應用程式</span><span class="sxs-lookup"><span data-stu-id="ba9f3-208">Download the app</span></span>

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="HoloSketch app icon" width="60" height="60" src="images/holosketch-app-icon.png">
</td>
<td style="border-style: none"><span data-ttu-id="ba9f3-209"><a href="https://www.microsoft.com/store/p/holosketch/9p3br4t5m4tv">從 Microsoft Store 免費下載並安裝 HoloSketch 應用程式</a>
</span><span class="sxs-lookup"><span data-stu-id="ba9f3-209"><a href="https://www.microsoft.com/store/p/holosketch/9p3br4t5m4tv">Download and install the HoloSketch app for free from the Microsoft Store</a>
</span></span></td>
</tr>
</table>

## <a name="known-issues"></a><span data-ttu-id="ba9f3-210">已知問題</span><span class="sxs-lookup"><span data-stu-id="ba9f3-210">Known issues</span></span>
* <span data-ttu-id="ba9f3-211">**Unity 版本5.4.5 節 f1** 支援目前的資產套件組合建立。</span><span class="sxs-lookup"><span data-stu-id="ba9f3-211">Currently asset bundle creation is supported with **Unity version 5.4.5f1.**</span></span>
* <span data-ttu-id="ba9f3-212">視 OneDrive 中的資料量而定，應用程式可能會顯示為在載入 OneDrive 內容時停止</span><span class="sxs-lookup"><span data-stu-id="ba9f3-212">Depending on the amount of data in your OneDrive, the app might appear as if it has stopped while loading OneDrive contents</span></span>
* <span data-ttu-id="ba9f3-213">目前，儲存和載入功能只支援基本物件</span><span class="sxs-lookup"><span data-stu-id="ba9f3-213">Currently, Save and Load feature only supports primitive objects</span></span>
* <span data-ttu-id="ba9f3-214">在內容功能表上停用文字、音效、影片和相片功能表</span><span class="sxs-lookup"><span data-stu-id="ba9f3-214">Text, Sound, Video and Photo menus are disabled on the contextual menu</span></span>
* <span data-ttu-id="ba9f3-215">工具功能表上的 [播放] 按鈕會清除操作 gizmos</span><span class="sxs-lookup"><span data-stu-id="ba9f3-215">The Play button on the Tool Belt menu clears the manipulation gizmos</span></span>

## <a name="sharing-your-sketches"></a><span data-ttu-id="ba9f3-216">共用您的草圖</span><span class="sxs-lookup"><span data-stu-id="ba9f3-216">Sharing your sketches</span></span>

<span data-ttu-id="ba9f3-217">您可以藉由說出「嗨 Cortana、開始/停止錄製」來使用 HoloLens 中的影片錄製功能。</span><span class="sxs-lookup"><span data-stu-id="ba9f3-217">You can use the video recording feature in HoloLens by saying 'Hey Cortana, Start/Stop recording'.</span></span> <span data-ttu-id="ba9f3-218">同步選取音量向上/向下鍵，以拍攝草圖的圖片。</span><span class="sxs-lookup"><span data-stu-id="ba9f3-218">Press the volume up/down key together to take a picture of your sketch.</span></span>

## <a name="about-the-authors"></a><span data-ttu-id="ba9f3-219">關於作者</span><span class="sxs-lookup"><span data-stu-id="ba9f3-219">About the authors</span></span>

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="../develop/unity/images/dongyoonpark.jpg"></td>
<td style="border-style: none"><span data-ttu-id="ba9f3-220"><b>盾 Yoon 公園</b></span><span class="sxs-lookup"><span data-stu-id="ba9f3-220"><b>Dong Yoon Park</b></span></span><br><span data-ttu-id="ba9f3-221">UX 設計工具 @Microsoft</span><span class="sxs-lookup"><span data-stu-id="ba9f3-221">UX Designer @Microsoft</span></span></td>
</tr>
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Patrick Sebring" width="60" height="60" src="images/paseb-60px.jpg"></td>
<td style="border-style: none"><span data-ttu-id="ba9f3-222"><b>派翠克 Sebring</b></span><span class="sxs-lookup"><span data-stu-id="ba9f3-222"><b>Patrick Sebring</b></span></span><br><span data-ttu-id="ba9f3-223">開發 人員 @Microsoft</span><span class="sxs-lookup"><span data-stu-id="ba9f3-223">Developer @Microsoft</span></span></td>
</tr>
</table> 
