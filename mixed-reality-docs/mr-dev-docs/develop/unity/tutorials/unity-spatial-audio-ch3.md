---
title: 從影片空間化音訊
description: 瞭解如何將影片資產匯入 Unity mixed reality 專案中，並從影片 spatialize 音訊。
author: kegodin
ms.author: v-hferrone
ms.date: 12/01/2019
ms.topic: article
keywords: 混合現實、unity、教學課程、hololens2、空間音訊、MRTK、混合現實工具組、UWP、Windows 10、HRTF、前端相關的傳送功能、回音、Microsoft 空間定位器、影片匯入、影片播放工具
ms.openlocfilehash: 211d1e32a8137444d0f33d442a60067dcd77ca36
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2021
ms.locfileid: "98007409"
---
# <a name="spatializing-audio-from-a-video"></a><span data-ttu-id="8da68-104">從影片空間化音訊</span><span class="sxs-lookup"><span data-stu-id="8da68-104">Spatializing audio from a video</span></span>

<span data-ttu-id="8da68-105">在 HoloLens 2 Unity 教學課程的「空間音訊」課程模組的第3章中，您將會：</span><span class="sxs-lookup"><span data-stu-id="8da68-105">In this 3rd chapter of the spatial audio module of the HoloLens 2 Unity tutorials, you'll:</span></span>
* <span data-ttu-id="8da68-106">匯入影片並新增影片播放影片</span><span class="sxs-lookup"><span data-stu-id="8da68-106">Import a video and add a Video Player</span></span>
* <span data-ttu-id="8da68-107">播放影片到四邊形</span><span class="sxs-lookup"><span data-stu-id="8da68-107">Play the video onto a quadrangle</span></span>
* <span data-ttu-id="8da68-108">將音訊從影片路由傳送至四邊形，並 spatialize 音訊</span><span class="sxs-lookup"><span data-stu-id="8da68-108">Route audio from the video to the quadrangle, and spatialize the audio</span></span>

## <a name="import-a-video-and-add-a-video-player"></a><span data-ttu-id="8da68-109">匯入影片並新增影片播放影片</span><span class="sxs-lookup"><span data-stu-id="8da68-109">Import a video and add a Video Player</span></span>

<span data-ttu-id="8da68-110">將影片檔案拖曳至 Unity 專案的 [ **專案** ] 窗格中。</span><span class="sxs-lookup"><span data-stu-id="8da68-110">Drag a video file into the **Project** pane in your Unity project.</span></span> <span data-ttu-id="8da68-111">您可以從空間音訊範例專案使用 [這段影片](https://github.com/microsoft/spatialaudio-unity/blob/develop/Samples/MicrosoftSpatializerSample/Assets/Microsoft%20HoloLens%20-%20Spatial%20Sound-PTPvx7mDon4.mp4?raw=true) 。</span><span class="sxs-lookup"><span data-stu-id="8da68-111">You can use [this video](https://github.com/microsoft/spatialaudio-unity/blob/develop/Samples/MicrosoftSpatializerSample/Assets/Microsoft%20HoloLens%20-%20Spatial%20Sound-PTPvx7mDon4.mp4?raw=true) from the spatial audio sample project.</span></span>

![具有影片的資產資料夾](images/spatial-audio/assets-folder-with-video.png)

<span data-ttu-id="8da68-113">調整影片剪輯的品質設定，可確保在 HoloLens 2 上進行順暢的播放。</span><span class="sxs-lookup"><span data-stu-id="8da68-113">Adjusting the quality settings on the video clip can ensure smooth playback on HoloLens 2.</span></span> <span data-ttu-id="8da68-114">按一下 [ **專案** ] 窗格中的影片檔案。</span><span class="sxs-lookup"><span data-stu-id="8da68-114">Click on the video file in the **Project** pane.</span></span> <span data-ttu-id="8da68-115">然後，在影片檔案的 [偵測 **器** ] 窗格中，覆寫 Windows Store 應用程式的設定，以及：</span><span class="sxs-lookup"><span data-stu-id="8da68-115">Then in the **Inspector** pane for the video file, override the settings for Windows Store Apps, and:</span></span>
* <span data-ttu-id="8da68-116">啟用 **轉碼**</span><span class="sxs-lookup"><span data-stu-id="8da68-116">Enable **Transcode**</span></span>
* <span data-ttu-id="8da68-117">將 **編解碼器** 設定為 H264</span><span class="sxs-lookup"><span data-stu-id="8da68-117">Set **Codec** to H264</span></span>
* <span data-ttu-id="8da68-118">將 **位元速率模式** 設定為低</span><span class="sxs-lookup"><span data-stu-id="8da68-118">Set **Bitrate Mode** to Low</span></span>
* <span data-ttu-id="8da68-119">將 **空間品質** 設定為中等空間品質</span><span class="sxs-lookup"><span data-stu-id="8da68-119">Set **Spatial Quality** to Medium Spatial Quality</span></span>

<span data-ttu-id="8da68-120">這些調整之後，影片檔案的偵測 **器** 窗格看起來會像這樣：</span><span class="sxs-lookup"><span data-stu-id="8da68-120">After these adjustments, the **Inspector** pane for the video file will look like this:</span></span>

![影片屬性窗格](images/spatial-audio/video-property-pane.png)

<span data-ttu-id="8da68-122">接下來，以滑鼠右鍵 **按一下 [階層**] 窗格，然後 **選擇 [** **影片-> 影片播放程式**]，將 **影片播放** 程式物件新增至階層：</span><span class="sxs-lookup"><span data-stu-id="8da68-122">Next, add a **Video Player** object to the **Hierarchy** by right-clicking on the **Hierarchy** pane and choosing **Video -> Video Player**:</span></span>

![階層中的影片播放影片](images/spatial-audio/video-player-in-hierarchy.png)

## <a name="play-video-onto-a-quadrangle"></a><span data-ttu-id="8da68-124">播放影片至四邊形</span><span class="sxs-lookup"><span data-stu-id="8da68-124">Play video onto a quadrangle</span></span>

<span data-ttu-id="8da68-125">**影片播放影片** 物件需要有紋理的遊戲物件來呈現影片。</span><span class="sxs-lookup"><span data-stu-id="8da68-125">The **Video Player** object needs a textured game object on which to render the video.</span></span> <span data-ttu-id="8da68-126">首先 **，以滑鼠** 按右鍵階層 **窗格，然後選擇 [** **3d 物件-> 四** 個：</span><span class="sxs-lookup"><span data-stu-id="8da68-126">First, add a **Quad** to your **Hierarchy** by right-clicking on the **Hierarchy** pane and choosing **3D Object -> Quad**:</span></span>

![將四個階層新增至階層](images/spatial-audio/add-quad-to-hierarchy.png)

<span data-ttu-id="8da68-128">為了確保在應用程式啟動時出現在使用者前面的 **四** 個部分，請將 **四** 個的 [**位置**] 屬性設定為 [ (0、0、2) ]，並將 [**小** 數位數] 屬性設定為 (1.28、0.72、1) 。</span><span class="sxs-lookup"><span data-stu-id="8da68-128">To ensure the **Quad** appears in front of the user when the application starts, set the **Position** property of the **Quad** to (0, 0, 2), and the **Scale** property to (1.28, 0.72, 1).</span></span> <span data-ttu-id="8da68-129">這些變更之後，**四** 個 [**檢查**] 窗格上的 [**轉換**] 元件看起來會像這樣：</span><span class="sxs-lookup"><span data-stu-id="8da68-129">After these changes, the **Transform** component on the **Inspector** pane for the **Quad** will look like this:</span></span>

![四轉換](images/spatial-audio/quad-transform.png)

<span data-ttu-id="8da68-131">若要使用影片來材質 **四** 段影片，請建立新的轉譯 **紋理**。</span><span class="sxs-lookup"><span data-stu-id="8da68-131">To texture the **Quad** with video, create a new **Render Texture**.</span></span> <span data-ttu-id="8da68-132">在 [ **專案** ] 窗格中，以滑鼠右鍵按一下並選擇 [ **建立-> 呈現材質**：</span><span class="sxs-lookup"><span data-stu-id="8da68-132">In the **Project** pane, right-click and choose **Create -> Render Texture**:</span></span>

![建立呈現材質](images/spatial-audio/create-render-texture.png)

<span data-ttu-id="8da68-134">在轉譯 **紋理** 的 [偵測 **器**] 窗格中，將 [**大小**] 屬性設定為符合影片的1280x720 原生解析度。</span><span class="sxs-lookup"><span data-stu-id="8da68-134">On the **Inspector** pane of the **Render Texture**, set the **Size** property to match the video's native resolution of 1280x720.</span></span> <span data-ttu-id="8da68-135">然後，若要確保 HoloLens 2 的良好轉譯效能，請將 [ **深度緩衝區** ] 屬性設定為 **至少16個位的深度**。</span><span class="sxs-lookup"><span data-stu-id="8da68-135">Then, to ensure good rendering performance on HoloLens 2, set the **Depth Buffer** property to **At least 16 bits depth**.</span></span> <span data-ttu-id="8da68-136">這些設定之後，轉譯 **紋理** 的偵測 **器** 窗格看起來會像這樣：</span><span class="sxs-lookup"><span data-stu-id="8da68-136">After these settings, the **Inspector** pane for the **Render Texture** will look like this:</span></span>

![轉譯材質屬性](images/spatial-audio/render-texture-properties.png)

<span data-ttu-id="8da68-138">接下來，使用新的轉譯 **紋理** 作為 **四** 個的材質：</span><span class="sxs-lookup"><span data-stu-id="8da68-138">Next, use your new **Render Texture** as the texture for the **Quad**:</span></span>
1. <span data-ttu-id="8da68-139">將 [轉譯 **材質**] 從 [**專案**] 窗格拖曳到階層 **中的 [** **四** 個]</span><span class="sxs-lookup"><span data-stu-id="8da68-139">Drag the **Render Texture** from the **Project** pane onto the **Quad** in the **Hierarchy**</span></span>
2. <span data-ttu-id="8da68-140">若要確保 HoloLens 2 的良好效能，請在 **四** 個 [偵測 **器**] 窗格中，選取 [**混合現實工具組標準著色器**]。</span><span class="sxs-lookup"><span data-stu-id="8da68-140">To ensure good performance on HoloLens 2, on the **Inspector** pane for the **Quad**, select the **Mixed Reality Toolkit Standard Shader**.</span></span>

<span data-ttu-id="8da68-141">使用這些設定時，**四** 個 [**檢查**] 窗格上的 **材質** 元件看起來會像這樣：</span><span class="sxs-lookup"><span data-stu-id="8da68-141">With these settings, the **Texture** component on the **Inspector** pane for the **Quad** will look like this:</span></span>

![四材質屬性](images/spatial-audio/quad-texture-properties.png)

<span data-ttu-id="8da68-143">若要設定新的 **影片播放** 程式並轉譯 **材質** 來播放影片剪輯，請開啟 **影片播放** 程式的 [偵測 **器**] 窗格，然後：</span><span class="sxs-lookup"><span data-stu-id="8da68-143">To set your new **Video Player** and **Render Texture** to play your video clip, open the **Inspector** pane for the **Video Player** and:</span></span>
* <span data-ttu-id="8da68-144">將 **影片剪輯** 屬性設定為您的影片檔案</span><span class="sxs-lookup"><span data-stu-id="8da68-144">Set the **Video Clip** property to your video file</span></span>
* <span data-ttu-id="8da68-145">核取 [ **迴圈** ] 核取方塊</span><span class="sxs-lookup"><span data-stu-id="8da68-145">Check the **Loop** checkbox</span></span>
* <span data-ttu-id="8da68-146">將 **目標材質** 設定為新的呈現材質</span><span class="sxs-lookup"><span data-stu-id="8da68-146">Set **Target Texture** to your new render texture</span></span>

<span data-ttu-id="8da68-147">**影片播放** 程式的 [偵測 **器**] 窗格現在看起來會像這樣：</span><span class="sxs-lookup"><span data-stu-id="8da68-147">The **Inspector** pane for the **Video Player** will now look like this:</span></span>

![影片播放影片屬性](images/spatial-audio/video-player-properties.png)

## <a name="spatialize-the-audio-from-the-video"></a><span data-ttu-id="8da68-149">從影片 Spatialize 音訊</span><span class="sxs-lookup"><span data-stu-id="8da68-149">Spatialize the audio from the video</span></span>

<span data-ttu-id="8da68-150">在 **四** 個的 [偵測 **器**] 窗格中，建立 **音訊來源**，您將從影片將音訊傳送至該來源：</span><span class="sxs-lookup"><span data-stu-id="8da68-150">In the **Inspector** pane for the **Quad**, create an **Audio Source** to which you'll route the audio from the video:</span></span>
* <span data-ttu-id="8da68-151">按一下窗格底部的 [ **新增元件** ]</span><span class="sxs-lookup"><span data-stu-id="8da68-151">Click **Add Component** at the bottom of the pane</span></span>
* <span data-ttu-id="8da68-152">新增 **音訊來源**</span><span class="sxs-lookup"><span data-stu-id="8da68-152">Add an **Audio Source**</span></span>

<span data-ttu-id="8da68-153">然後，在 **音訊來源**：</span><span class="sxs-lookup"><span data-stu-id="8da68-153">Then, on the **Audio Source**:</span></span>
* <span data-ttu-id="8da68-154">將 **輸出** 設定至混音器</span><span class="sxs-lookup"><span data-stu-id="8da68-154">Set **Output** to your mixer</span></span>
* <span data-ttu-id="8da68-155">核取 [ **Spatialize** ] 方塊</span><span class="sxs-lookup"><span data-stu-id="8da68-155">Check the **Spatialize** box</span></span>
* <span data-ttu-id="8da68-156">將 **空間 Blend** 滑杆移至 1 (3d) </span><span class="sxs-lookup"><span data-stu-id="8da68-156">Move the **Spatial Blend** slider to 1 (3D)</span></span>

<span data-ttu-id="8da68-157">這些變更之後，**四個四** 個 [**檢查**] 窗格上的 [**音訊來源**] 元件看起來會像這樣：</span><span class="sxs-lookup"><span data-stu-id="8da68-157">After these changes, the **Audio Source** component on the **Inspector** pane for the **Quad** will look like this:</span></span>

![四音訊來源檢查](images/spatial-audio/quad-audio-source-inspector.png)

<span data-ttu-id="8da68-159">若要設定 **影片播放** 程式以將其音訊傳送至 **四** 個 **音訊來源**，請開啟 **影片播放** 程式的 [偵測 **器**] 窗格，然後：</span><span class="sxs-lookup"><span data-stu-id="8da68-159">To set the **Video Player** to route its audio to the **Audio Source** on the **Quad**, open the **Inspector** pane for the **Video Player** and:</span></span>
* <span data-ttu-id="8da68-160">將 **音訊輸出模式** 設定為 [音訊來源]</span><span class="sxs-lookup"><span data-stu-id="8da68-160">Set the **Audio Output Mode** to 'Audio Source'</span></span>
* <span data-ttu-id="8da68-161">將 [ **音訊來源** ] 屬性設定為 [四]</span><span class="sxs-lookup"><span data-stu-id="8da68-161">Set the **Audio Source** property to your Quad</span></span>

<span data-ttu-id="8da68-162">這些變更之後，**影片播放** 程式的 [偵測 **器**] 窗格看起來會像這樣：</span><span class="sxs-lookup"><span data-stu-id="8da68-162">After these changes, the **Inspector** pane for the **Video Player** will look like this:</span></span>

![影片播放影片設定音訊來源](images/spatial-audio/video-player-set-audio-source.png)

## <a name="next-steps"></a><span data-ttu-id="8da68-164">後續步驟</span><span class="sxs-lookup"><span data-stu-id="8da68-164">Next steps</span></span>

<span data-ttu-id="8da68-165">在 HoloLens 2 或 Unity 編輯器中試用您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="8da68-165">Try out your app on a HoloLens 2 or in the Unity editor.</span></span> <span data-ttu-id="8da68-166">您將會看到並聆聽影片，而影片中的音訊將會 hrtf。</span><span class="sxs-lookup"><span data-stu-id="8da68-166">You'll see and hear the video, and the audio from the video will be spatialized.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="8da68-167">第4章</span><span class="sxs-lookup"><span data-stu-id="8da68-167">Chapter 4</span></span>](unity-spatial-audio-ch4.md) 

