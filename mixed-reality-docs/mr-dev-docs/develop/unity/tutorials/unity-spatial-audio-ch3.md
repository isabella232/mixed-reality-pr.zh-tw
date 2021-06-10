---
title: 空間音訊教學課程-3。 從影片空間化音訊
description: 將影片資產匯入您的 Unity 專案，並從影片 spatialize 音訊。
author: kegodin
ms.author: v-hferrone
ms.date: 02/05/2021
ms.topic: article
keywords: 混合現實、unity、教學課程、hololens2、空間音訊、MRTK、混合現實工具組、UWP、Windows 10、HRTF、前端相關的傳送功能、回音、Microsoft 空間定位器、影片匯入、影片播放工具
ms.openlocfilehash: 60b70fc3b7f49f5b39138a218f93c0b37f29b9d9
ms.sourcegitcommit: 4a6c26615d52776bdc4faab70391592092a471fc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2021
ms.locfileid: "110712876"
---
# <a name="3-spatializing-audio-from-a-video"></a><span data-ttu-id="142fb-105">3.從影片空間化音訊</span><span class="sxs-lookup"><span data-stu-id="142fb-105">3. Spatializing audio from a video</span></span>

## <a name="overview"></a><span data-ttu-id="142fb-106">概觀</span><span class="sxs-lookup"><span data-stu-id="142fb-106">Overview</span></span>

<span data-ttu-id="142fb-107">在本教學課程中，您將瞭解如何從影片來源 spatialize 音訊，並在 unity 編輯器中測試，並 HoloLens 2。</span><span class="sxs-lookup"><span data-stu-id="142fb-107">In this tutorial, you will learn how to spatialize audio from an video source and test this in the unity editor and HoloLens 2.</span></span>

## <a name="objectives"></a><span data-ttu-id="142fb-108">目標</span><span class="sxs-lookup"><span data-stu-id="142fb-108">Objectives</span></span>

* <span data-ttu-id="142fb-109">匯入影片並新增影片播放影片</span><span class="sxs-lookup"><span data-stu-id="142fb-109">Import a video and add a Video Player</span></span>
* <span data-ttu-id="142fb-110">播放影片到四邊形</span><span class="sxs-lookup"><span data-stu-id="142fb-110">Play the video onto a quadrangle</span></span>
* <span data-ttu-id="142fb-111">將音訊從影片路由傳送至四邊形，並 spatialize 音訊</span><span class="sxs-lookup"><span data-stu-id="142fb-111">Route audio from the video to the quadrangle, and spatialize the audio</span></span>

## <a name="import-a-video-and-add-a-video-player-to-the-scene"></a><span data-ttu-id="142fb-112">匯入影片並將影片播放機新增至場景</span><span class="sxs-lookup"><span data-stu-id="142fb-112">Import a video and add a Video Player to the Scene</span></span>

<span data-ttu-id="142fb-113">在本教學課程中，您可以使用「空間音訊」範例專案中的 [這段影片](https://github.com/microsoft/spatialaudio-unity/blob/develop/Samples/MicrosoftSpatializerSample/Assets/Microsoft%20HoloLens%20-%20Spatial%20Sound-PTPvx7mDon4.mp4?raw=true) 。</span><span class="sxs-lookup"><span data-stu-id="142fb-113">For this tutorial use You can use [this video](https://github.com/microsoft/spatialaudio-unity/blob/develop/Samples/MicrosoftSpatializerSample/Assets/Microsoft%20HoloLens%20-%20Spatial%20Sound-PTPvx7mDon4.mp4?raw=true) from the spatial audio sample project.</span></span>

<span data-ttu-id="142fb-114">將影片匯入 unity 專案。</span><span class="sxs-lookup"><span data-stu-id="142fb-114">To import Video into the unity project.</span></span> <span data-ttu-id="142fb-115">在 Unity 功能表中，選取 [**資產** 匯  >  **入新增** 資產匯 
 ![ 入資產]](images/spatial-audio/spatial-audio-03-section1-step1-1.PNG)</span><span class="sxs-lookup"><span data-stu-id="142fb-115">in the Unity menu select **Asset** > **Import New Asset**
![Importing Asset](images/spatial-audio/spatial-audio-03-section1-step1-1.PNG)</span></span>

<span data-ttu-id="142fb-116">在 [匯 **入新資產** ] 視窗中，選取您下載的 **Microsoft HoloLens 空間音效 PTPvx7mDon4** 檔案，然後按一下 [ **開啟** ] 按鈕，將資產匯入至專案中：</span><span class="sxs-lookup"><span data-stu-id="142fb-116">In the **Import New Asset...** window, select the **Microsoft HoloLens - Spatial Sound-PTPvx7mDon4** file you downloaded and click the **Open** button to import the asset into the project:</span></span>

![選取資產](images/spatial-audio/spatial-audio-03-section1-step1-2.PNG)

<span data-ttu-id="142fb-118">調整影片剪輯的品質設定，可確保在 HoloLens 2 上進行順暢的播放。</span><span class="sxs-lookup"><span data-stu-id="142fb-118">Adjusting the quality settings on the video clip can ensure smooth playback on HoloLens 2.</span></span> <span data-ttu-id="142fb-119">在 [ **專案** ] 視窗和影片檔案的 [偵測器] 視窗中選取影片檔案，覆 **寫** **Windows Store 應用程式** 的設定，以及：</span><span class="sxs-lookup"><span data-stu-id="142fb-119">Select the video file in the **Project** window and in the Inspector window of the video file, **override** the settings for **Windows Store Apps**, and:</span></span>

* <span data-ttu-id="142fb-120">啟用 **轉碼**</span><span class="sxs-lookup"><span data-stu-id="142fb-120">Enable **Transcode**</span></span>
* <span data-ttu-id="142fb-121">將 **編解碼器** 設定為 H264</span><span class="sxs-lookup"><span data-stu-id="142fb-121">Set **Codec** to H264</span></span>
* <span data-ttu-id="142fb-122">將 **位元速率模式** 設定為低</span><span class="sxs-lookup"><span data-stu-id="142fb-122">Set **Bitrate Mode** to Low</span></span>
* <span data-ttu-id="142fb-123">將 **空間品質** 設定為中等空間品質</span><span class="sxs-lookup"><span data-stu-id="142fb-123">Set **Spatial Quality** to Medium Spatial Quality</span></span>

<span data-ttu-id="142fb-124">進行這些調整之後，請按一下 [套用] 來變更影片剪輯上的品質設定。</span><span class="sxs-lookup"><span data-stu-id="142fb-124">After these adjustments, click on Apply to change the quality setting on the video clip.</span></span>

![影片屬性變更](images/spatial-audio/spatial-audio-03-section1-step1-3.PNG)

<span data-ttu-id="142fb-126">以滑鼠右鍵按一下階層，然後選取 [**視頻**  >  **影片播放** 影片] 以新增影片播放元件。</span><span class="sxs-lookup"><span data-stu-id="142fb-126">Right click on the Hierarchy, Select **Video** > **Video Player** to add Video player component.</span></span>

![新增影片播放影片](images/spatial-audio/spatial-audio-03-section1-step1-4.PNG)

## <a name="play-video-onto-a-quadrangle"></a><span data-ttu-id="142fb-128">播放影片至四邊形</span><span class="sxs-lookup"><span data-stu-id="142fb-128">Play video onto a quadrangle</span></span>

<span data-ttu-id="142fb-129">**影片播放影片** 物件需要有紋理的遊戲物件才能轉譯影片。</span><span class="sxs-lookup"><span data-stu-id="142fb-129">The **Video Player** object needs a textured game object to render the video.</span></span>

<span data-ttu-id="142fb-130">以滑鼠右鍵按一下階層，選取 [ **3d 物件**  >  **四** 個] 以建立四個並設定其 **轉換** 元件，如下所示：</span><span class="sxs-lookup"><span data-stu-id="142fb-130">Right click the Hierarchy , Select **3D Object** > **Quad** to create a quad and configure its **Transform** component as follows:</span></span>

* <span data-ttu-id="142fb-131">**位置**： X = 0、Y = 0、Z = 2</span><span class="sxs-lookup"><span data-stu-id="142fb-131">**Position**: X = 0, Y = 0, Z = 2</span></span>
* <span data-ttu-id="142fb-132">**旋轉**：X = 0、Y = 0、Z = 0</span><span class="sxs-lookup"><span data-stu-id="142fb-132">**Rotation**: X = 0, Y = 0, Z = 0</span></span>
* <span data-ttu-id="142fb-133">**Scale**： X = 1.28、Y = 0.72、Z = 1</span><span class="sxs-lookup"><span data-stu-id="142fb-133">**Scale**: X = 1.28, Y = 0.72, Z = 1</span></span>

![新增四個](images/spatial-audio/spatial-audio-03-section2-step1-1.PNG)

<span data-ttu-id="142fb-135">現在您需要將 **四** 段影片的材質材質，請在 [**專案**] 視窗中，以滑鼠右鍵按一下並選擇 [**建立** 轉譯  >  **材質**] 來建立轉譯材質元件、為轉譯紋理輸入適當的名稱，例如，_空間音訊材質_：</span><span class="sxs-lookup"><span data-stu-id="142fb-135">Now you need to texture the **Quad** with the video, In the **Project** window, right-click and choose **Create** > **Render Texture** to create a Render Texture component, enter a suitable name to the Render Texture for example, _Spatial Audio Texture_:</span></span>

![建立呈現材質](images/spatial-audio/spatial-audio-03-section2-step1-2.PNG)

<span data-ttu-id="142fb-137">選取 [轉譯 **材質** ]，然後在 [偵測器] 視窗中設定 [ **大小** ] 屬性，以符合影片的1280x720 原生解析度。</span><span class="sxs-lookup"><span data-stu-id="142fb-137">Select the **Render Texture** and in the Inspector window set the **Size** property to match the video's native resolution of 1280x720.</span></span> <span data-ttu-id="142fb-138">然後，若要確保 HoloLens 2 的良好轉譯效能，請將 [ **深度緩衝區** ] 屬性設定為 **至少16個位的深度**。</span><span class="sxs-lookup"><span data-stu-id="142fb-138">Then, to ensure good rendering performance on HoloLens 2, set the **Depth Buffer** property to **At least 16 bits depth**.</span></span>

![轉譯材質屬性](images/spatial-audio/spatial-audio-03-section2-step1-3.PNG)

<span data-ttu-id="142fb-140">接下來，使用已建立的轉譯材質 **空間音訊紋理** 作為 **四** 個的材質：</span><span class="sxs-lookup"><span data-stu-id="142fb-140">Next, use the created Render Texture **Spatial Audio Texture** as the texture for the **Quad**:</span></span>

1. <span data-ttu-id="142fb-141">將 [ **空間音訊材質** ] 從 [ **專案** ] 視窗拖曳至階層中的 [ **四** 個]，以將轉譯紋理新增至 [四]</span><span class="sxs-lookup"><span data-stu-id="142fb-141">Drag the **Spatial Audio Texture** from the **Project** window onto the **Quad** in the Hierarchy to add the Render Texture to the Quad</span></span>
2. <span data-ttu-id="142fb-142">若要確保 HoloLens 2 的良好效能，請選取階層中的 [四]，然後在著色器的 [偵測器] 視窗中選取 [**混合現實工具** 組  >  **標準** 著色器]</span><span class="sxs-lookup"><span data-stu-id="142fb-142">To ensure good performance on HoloLens 2, select Quad in the Hierarchy and in the Inspector window for shader select the **Mixed Reality Toolkit** > **Standard** Shader.</span></span>

![四材質屬性](images/spatial-audio/spatial-audio-03-section2-step1-4.PNG)

<span data-ttu-id="142fb-144">若要設定 **影片播放** 和轉譯 **材質** 來播放影片剪輯，請選取 **階層和偵測\*\*\*\*器** 視窗中的 **影片播放機**。</span><span class="sxs-lookup"><span data-stu-id="142fb-144">To set **Video Player** and **Render Texture** to play the video clip, select the **Video Player** in the **Hierarchy** and in the **Inspector** window,</span></span>

* <span data-ttu-id="142fb-145">將 **影片剪輯** 屬性設定為下載的影片檔案 ' Microsoft HoloLens-空間音效-PTPvx7mDon4 '</span><span class="sxs-lookup"><span data-stu-id="142fb-145">Set the **Video Clip** property to the downloaded video file 'Microsoft HoloLens - Spatial Sound-PTPvx7mDon4'</span></span>
* <span data-ttu-id="142fb-146">核取 [ **迴圈** ] 核取方塊</span><span class="sxs-lookup"><span data-stu-id="142fb-146">Check the **Loop** checkbox</span></span>
* <span data-ttu-id="142fb-147">將 **目標材質** 設定為新的轉譯材質 **空間音訊紋理**</span><span class="sxs-lookup"><span data-stu-id="142fb-147">Set **Target Texture** to your new render texture **Spatial Audio Texture**</span></span>

![影片播放影片屬性](images/spatial-audio/spatial-audio-03-section2-step1-5.PNG)

## <a name="spatialize-the-audio-from-the-video"></a><span data-ttu-id="142fb-149">從影片 Spatialize 音訊</span><span class="sxs-lookup"><span data-stu-id="142fb-149">Spatialize the audio from the video</span></span>

<span data-ttu-id="142fb-150">在 [階層] 視窗中，選取 [ **四** 個物件]，然後在 [偵測器] 視窗中，使用 [ **新增元件** ] 按鈕來新增 **音訊來源** ，您將從影片將音訊傳送至該來源。</span><span class="sxs-lookup"><span data-stu-id="142fb-150">In the Hierarchy window, select **Quad** object, then in the Inspector window, use the **Add Component** button to add **Audio Source** to which you'll route the audio from the video.</span></span>

<span data-ttu-id="142fb-151">在 **音訊來源** 中：</span><span class="sxs-lookup"><span data-stu-id="142fb-151">In the **Audio Source**:</span></span>

* <span data-ttu-id="142fb-152">將 **輸出** 設定為 **空間音訊混音** 器</span><span class="sxs-lookup"><span data-stu-id="142fb-152">Set **Output** to the **Spatial Audio Mixer**</span></span>
* <span data-ttu-id="142fb-153">核取 [ **Spatialize** ] 方塊</span><span class="sxs-lookup"><span data-stu-id="142fb-153">Check the **Spatialize** box</span></span>
* <span data-ttu-id="142fb-154">將 **空間 Blend** 滑杆移至 1 (3d) </span><span class="sxs-lookup"><span data-stu-id="142fb-154">Move the **Spatial Blend** slider to 1 (3D)</span></span>

![四音訊來源檢查](images/spatial-audio/spatial-audio-03-section3-step1-1.PNG)

<span data-ttu-id="142fb-156">若要設定影片播放影片將其音訊路由傳送到 **音訊來源**，請在 [階層] 視窗中選取 **影片播放機** ，然後在偵測器中的 [影片播放流程] 物件執行下列變更。</span><span class="sxs-lookup"><span data-stu-id="142fb-156">To set the Video Player to route its audio to the **Audio Source**, select the **Video Player** In the Hierarchy window, and in Video Player object in the Inspector do the following changes.</span></span>

* <span data-ttu-id="142fb-157">將 **音訊輸出模式** 設定為 **音訊來源**</span><span class="sxs-lookup"><span data-stu-id="142fb-157">Set the **Audio Output Mode** to **Audio Source**</span></span>
* <span data-ttu-id="142fb-158">將 [**音訊來源**] 屬性設定為 [**四**]</span><span class="sxs-lookup"><span data-stu-id="142fb-158">Set the **Audio Source** property to the **Quad**</span></span>

![影片播放影片設定音訊來源](images/spatial-audio/spatial-audio-03-section3-step1-2.PNG)

> [!TIP]
> <span data-ttu-id="142fb-160">如需有關如何建立 Unity 專案並將其部署至 HoloLens 2 的提醒，您可以參閱[對您的 HoloLens 2 建置應用程式](mr-learning-base-02.md#building-your-application-to-your-hololens-2)的指示。</span><span class="sxs-lookup"><span data-stu-id="142fb-160">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Building your app to your HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions.</span></span>

## <a name="congratulations"></a><span data-ttu-id="142fb-161">恭喜！</span><span class="sxs-lookup"><span data-stu-id="142fb-161">Congratulations</span></span>

<span data-ttu-id="142fb-162">在本教學課程中，您已瞭解如何從影片來源 spatialize 音訊，並在 HoloLens 2 或 Unity 編輯器中試用您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="142fb-162">In this tutorial, you have learned how to spatialize audio from an video source Try out your app on a HoloLens 2 or in the Unity editor.</span></span> <span data-ttu-id="142fb-163">您將會看到並聆聽影片，而影片中的音訊 hrtf。</span><span class="sxs-lookup"><span data-stu-id="142fb-163">You'll see and hear the video, and the audio from the video is spatialized.</span></span>

<span data-ttu-id="142fb-164">在下一個教學課程中，您將瞭解如何在執行時間啟用和停用 spatialization</span><span class="sxs-lookup"><span data-stu-id="142fb-164">In the next tutorial you will learn how to Enable and disable spatialization at run time</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="142fb-165">下一個教學課程： 4. 在執行時間啟用和停用 spatialization</span><span class="sxs-lookup"><span data-stu-id="142fb-165">Next Tutorial: 4. Enabling and disabling spatialization at run time</span></span>](unity-spatial-audio-ch4.md)
