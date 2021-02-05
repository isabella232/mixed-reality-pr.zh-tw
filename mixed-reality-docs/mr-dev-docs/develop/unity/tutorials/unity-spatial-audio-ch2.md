---
title: 空間音訊教學課程-2。 空間化按鈕互動音效
description: 將按鈕加入至您的專案，並 spatialize 按鈕互動音效。
author: kegodin
ms.author: v-hferrone
ms.date: 02/05/2021
ms.topic: article
keywords: 混合的現實、unity、教學課程、hololens2、空間音訊、MRTK、混合現實工具組、UWP、Windows 10、HRTF、head 相關的傳送函式、回音、Microsoft 空間定位器、prefabs、音量曲線
ms.openlocfilehash: 12d159cb162cbf136483f7be94b0d297319a0737
ms.sourcegitcommit: 68140e9ce84e69a99c2b3d970c7b8f2927a7fc93
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/05/2021
ms.locfileid: "99590760"
---
# <a name="2-spatializing-button-interaction-sounds"></a><span data-ttu-id="3f905-105">2.空間化按鈕互動音效</span><span class="sxs-lookup"><span data-stu-id="3f905-105">2. Spatializing button interaction sounds</span></span>

## <a name="overview"></a><span data-ttu-id="3f905-106">概觀</span><span class="sxs-lookup"><span data-stu-id="3f905-106">Overview</span></span>

<span data-ttu-id="3f905-107">在本教學課程中，您將學習如何 spatialize 按鈕互動音效，以及瞭解如何使用音訊剪輯來測試 hrtf 按鈕互動。</span><span class="sxs-lookup"><span data-stu-id="3f905-107">In this tutorial, you will learn how to spatialize the button interaction sounds and also learn how to use an audio clip to test spatialized button interaction.</span></span>  

## <a name="objectives"></a><span data-ttu-id="3f905-108">目標</span><span class="sxs-lookup"><span data-stu-id="3f905-108">Objectives</span></span>

* <span data-ttu-id="3f905-109">新增並 Spatialize 按鈕的 click 聲</span><span class="sxs-lookup"><span data-stu-id="3f905-109">Add and Spatialize the button click sounds</span></span>

## <a name="add-a-button"></a><span data-ttu-id="3f905-110">新增按鈕</span><span class="sxs-lookup"><span data-stu-id="3f905-110">Add a button</span></span>

<span data-ttu-id="3f905-111">若要加入按鈕預製專案，請在 [ **專案** ] 視窗中選取 [ **封裝** ]，然後在搜尋列中輸入 "PressableButtonHoloLens2"。</span><span class="sxs-lookup"><span data-stu-id="3f905-111">To add the Button prefab, in the **Project** window, select **Packages** and type "PressableButtonHoloLens2" in the search bar.</span></span>

![資產中的按鈕預製專案](images/spatial-audio/spatial-audio-02-section1-step1-1.png)

<span data-ttu-id="3f905-113">按鈕預製專案是以藍色圖示表示的專案。</span><span class="sxs-lookup"><span data-stu-id="3f905-113">The button prefab is the entry represented by a blue icon.</span></span> <span data-ttu-id="3f905-114">按一下 [ **PressableButtonHoloLens2** ] 預製專案，並將其拖曳到階層中。</span><span class="sxs-lookup"><span data-stu-id="3f905-114">Click and drag the **PressableButtonHoloLens2** prefab into the Hierarchy.</span></span> <span data-ttu-id="3f905-115">在仍選取 **PressableButtonHoloLens2** 物件的情況下，在 [偵測器] 視窗中設定 **轉換** 元件，如下所示：</span><span class="sxs-lookup"><span data-stu-id="3f905-115">With the **PressableButtonHoloLens2** object still selected, in the Inspector window, configure the **Transform** component as follows:</span></span>

* <span data-ttu-id="3f905-116">**Position**： X = 0，Y =-0.4，Z = 2</span><span class="sxs-lookup"><span data-stu-id="3f905-116">**Position**: X = 0, Y = -0.4, Z = 2</span></span>
* <span data-ttu-id="3f905-117">**旋轉**：X = 0、Y = 0、Z = 0</span><span class="sxs-lookup"><span data-stu-id="3f905-117">**Rotation**: X = 0, Y = 0, Z = 0</span></span>
* <span data-ttu-id="3f905-118">**縮放**：X = 1、Y = 1、Z = 1</span><span class="sxs-lookup"><span data-stu-id="3f905-118">**Scale**: X = 1, Y = 1, Z = 1</span></span>

![按鈕轉換](images/spatial-audio/spatial-audio-02-section1-step1-2.png)

<span data-ttu-id="3f905-120">若要將焦點放在場景中的物件上，您可以按兩下 **PressableButtonHoloLens2** 物件，然後再稍微放大：</span><span class="sxs-lookup"><span data-stu-id="3f905-120">To focus in on the objects in the scene, you can double-click on the **PressableButtonHoloLens2** object, and then zoom slightly in again:</span></span>

## <a name="spatialize-button-feedback"></a><span data-ttu-id="3f905-121">Spatialize 按鈕意見反應</span><span class="sxs-lookup"><span data-stu-id="3f905-121">Spatialize button feedback</span></span>

<span data-ttu-id="3f905-122">在此步驟中，您將 spatialize 按鈕的音訊意見反應。</span><span class="sxs-lookup"><span data-stu-id="3f905-122">In this step, you'll spatialize the audio feedback for the button.</span></span> <span data-ttu-id="3f905-123">如需相關的設計建議，請參閱 [空間音效設計](../../../design/spatial-sound-design.md)。</span><span class="sxs-lookup"><span data-stu-id="3f905-123">For related design suggestions, see [spatial sound design](../../../design/spatial-sound-design.md).</span></span>

<span data-ttu-id="3f905-124">在 [**音訊混音** 器] 視窗中，您將為音訊 **來源** 元件的音訊播放定義稱為 **混音器群組** 的目的地。</span><span class="sxs-lookup"><span data-stu-id="3f905-124">In the **Audio Mixer** window you will define destinations called **Mixer Groups**, for audio playback from **Audio Source** components.</span></span>

<span data-ttu-id="3f905-125">若要開啟 [**音訊混音** 器] 視窗，請在 Unity 功能表中，選取 [**視窗**  >  **音訊**  >  **音訊混音** 器： ![ 開啟音訊混音器] 視窗](images/spatial-audio/spatial-audio-02-section2-step1-1.png)</span><span class="sxs-lookup"><span data-stu-id="3f905-125">To open the **Audio Mixer** window, In the Unity menu, select **Window** > **Audio** > **Audio Mixer**: ![Open Audio Mixer Window](images/spatial-audio/spatial-audio-02-section2-step1-1.png)</span></span>

 <span data-ttu-id="3f905-126">按一下 [ **Mixers** ] 旁邊的 [+]，並輸入適當的混音名稱（例如 _空間音訊混音_ 器）來建立 **混音** 器。</span><span class="sxs-lookup"><span data-stu-id="3f905-126">Create a **Mixer** by clicking the '+' next to **Mixers** and enter a suitable name to the Mixer for example, _Spatial Audio Mixer_.</span></span> <span data-ttu-id="3f905-127">新的混音器將包含稱為 **Master** 的預設 **群組**。</span><span class="sxs-lookup"><span data-stu-id="3f905-127">The new mixer will include a default **Group** called **Master**.</span></span>

![具有第一個混音器的混音器面板](images/spatial-audio/spatial-audio-02-section2-step1-2.png)

> [!NOTE]
> <span data-ttu-id="3f905-129">在第5章啟用回條之後 [：使用回音將距離新增至空間音訊](unity-spatial-audio-ch5.md)，混音器的音量計量不會顯示透過 Microsoft 空間定位器播放之音效的活動</span><span class="sxs-lookup"><span data-stu-id="3f905-129">Until reverb is enabled in [5th Chapter: Using reverb to add distance to spatial audio](unity-spatial-audio-ch5.md), the mixer's volume meter doesn't show activity for sounds played through the Microsoft Spatializer</span></span>

<span data-ttu-id="3f905-130">在 [階層] 視窗中，選取 **PressableButtonHoloLens2** ，然後在 [偵測器] 視窗中尋找 **音訊來源** 元件，並設定音訊來源元件，如下所示：</span><span class="sxs-lookup"><span data-stu-id="3f905-130">In the Hierarchy window, select the **PressableButtonHoloLens2** then in the Inspector window find the **Audio Source** component and Configure the Audio Source component as follows:</span></span>

1. <span data-ttu-id="3f905-131">針對 [ **輸出** ] 屬性，按一下選取器，然後選擇您建立的 **混音** 器。</span><span class="sxs-lookup"><span data-stu-id="3f905-131">For the **Output** property, click the selector and choose the **Mixer** that you created.</span></span>
2. <span data-ttu-id="3f905-132">核取 [ **Spatialize** ] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="3f905-132">Check the **Spatialize** checkbox.</span></span>
3. <span data-ttu-id="3f905-133">將 **空間 Blend** 滑杆移至 3d (1) 。</span><span class="sxs-lookup"><span data-stu-id="3f905-133">Move the **Spatial Blend** slider to 3D (1).</span></span>

![按鈕音訊來源](images/spatial-audio/spatial-audio-02-section2-step1-3.png)

> [!NOTE]
> <span data-ttu-id="3f905-135">如果您在未核取 [ **Spatialize** ] 核取方塊的情況下，將 **空間 Blend** 移至 1 (3d) ，Unity 將會使用其移動流覽空間定位器，而不是使用 hrtf 的 **Microsoft 空間定位器**。</span><span class="sxs-lookup"><span data-stu-id="3f905-135">If you move **Spatial Blend** to 1 (3D) without checking the **Spatialize** checkbox, Unity will use its panning spatializer, instead of the **Microsoft Spatializer** with HRTFs.</span></span>

## <a name="adjust-the-volume-curve"></a><span data-ttu-id="3f905-136">調整音量曲線</span><span class="sxs-lookup"><span data-stu-id="3f905-136">Adjust the Volume curve</span></span>

<span data-ttu-id="3f905-137">根據預設，Unity 會在從接聽程式更遠的情況下 attenuate hrtf 音效。</span><span class="sxs-lookup"><span data-stu-id="3f905-137">By default, Unity will attenuate spatialized sounds as they get farther from the listener.</span></span> <span data-ttu-id="3f905-138">當此衰減套用至互動回饋音效時，介面可能會變得更難使用。</span><span class="sxs-lookup"><span data-stu-id="3f905-138">When this attenuation is applied to interaction feedback sounds, the interface can become more difficult to use.</span></span>

<span data-ttu-id="3f905-139">若要停用此衰減，您需要調整 **音訊來源** 元件中的 **音量** 曲線。</span><span class="sxs-lookup"><span data-stu-id="3f905-139">To disable this attenuation, you need to adjust the **Volume** curve In the **Audio Source** component.</span></span>

<span data-ttu-id="3f905-140">在 [階層] 視窗中，選取 [ **PressableButtonHoloLens2** ]，然後在 [偵測器] 視窗中流覽至 [**音訊來源**  >  **3d 音效] 設定**，並設定如下：</span><span class="sxs-lookup"><span data-stu-id="3f905-140">In the Hierarchy window, select the **PressableButtonHoloLens2** then in the Inspector window navigate to  **Audio Source** > **3D Sound Settings** and Configure as follows:</span></span>

1. <span data-ttu-id="3f905-141">將 **Volume Rolloff** 屬性設定為線性 Rolloff</span><span class="sxs-lookup"><span data-stu-id="3f905-141">Set the **Volume Rolloff** property to Linear Rolloff</span></span>
2. <span data-ttu-id="3f905-142">拖曳 **音量** 曲線上的端點 (紅色曲線) 從 y 軸上的 ' 0 ' 到 ' 1 '</span><span class="sxs-lookup"><span data-stu-id="3f905-142">Drag the endpoint on the **Volume** curve (the red curve) from '0' on the y axis up to '1'</span></span>
3. <span data-ttu-id="3f905-143">若要將 **音量** 曲線的形狀調整為平面，請將白色曲線圖形控制項平行地拖曳至 X 軸</span><span class="sxs-lookup"><span data-stu-id="3f905-143">To adjust the shape of the **Volume** curve to be flat, drag the white curve shape control to be parallel to the X axis</span></span>

![按鈕3D 音效設定](images/spatial-audio/spatial-audio-02-section3-step1-1.png)

## <a name="testing-the-spatialize-audio"></a><span data-ttu-id="3f905-145">測試 spatialize 音訊</span><span class="sxs-lookup"><span data-stu-id="3f905-145">Testing the spatialize audio</span></span>

<span data-ttu-id="3f905-146">若要在 unity 編輯器中測試 spatialize 音訊，您必須在 [**音訊來源** 元件] 中新增音訊剪輯，並在 **PressableButtonHoloLens2** 物件上簽入 **迴圈** 選項。</span><span class="sxs-lookup"><span data-stu-id="3f905-146">To test the spatialize audio in the unity editor you have to add an audio clip in the **Audio Source** component with **Loop** option checked in on **PressableButtonHoloLens2** object.</span></span>

<span data-ttu-id="3f905-147">在 [播放] 模式中，將 **PressableButtonHoloLens2** 物件從左至右移動到右邊，並與您的工作站上未啟用空間音訊進行比較。</span><span class="sxs-lookup"><span data-stu-id="3f905-147">In the play mode move the **PressableButtonHoloLens2** object from left to right and compare with and without spatial audio enabled on your workstation.</span></span> <span data-ttu-id="3f905-148">您也可以變更用於測試的音訊來源設定：</span><span class="sxs-lookup"><span data-stu-id="3f905-148">You can also change the Audio Source settings for testing by:</span></span>

* <span data-ttu-id="3f905-149">將 **空間 Blend** 屬性移至 0-1 (2d 非 Hrtf 和 3d hrtf 音效) </span><span class="sxs-lookup"><span data-stu-id="3f905-149">Moving the **Spatial Blend** property between 0 - 1 (2D non-spatialized and 3D spatialized sound)</span></span>
* <span data-ttu-id="3f905-150">檢查和取消選取 **Spatialize** 屬性</span><span class="sxs-lookup"><span data-stu-id="3f905-150">Checking and unchecking the **Spatialize** property</span></span>

<span data-ttu-id="3f905-151">試用 HoloLens 2 上的應用程式。</span><span class="sxs-lookup"><span data-stu-id="3f905-151">Try out the app on HoloLens 2.</span></span> <span data-ttu-id="3f905-152">在應用程式中，您可以按一下按鈕，聽聽 hrtf 按鈕的互動音效。</span><span class="sxs-lookup"><span data-stu-id="3f905-152">In the app, you can click the button and hear the spatialized button interaction sounds.</span></span>

> [!TIP]
> <span data-ttu-id="3f905-153">如需有關如何建立 Unity 專案並將其部署至 HoloLens 2 的提醒，您可以參閱[對您的 HoloLens 2 建置應用程式](mr-learning-base-02.md#building-your-application-to-your-hololens-2)的指示。</span><span class="sxs-lookup"><span data-stu-id="3f905-153">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Building your app to your HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions.</span></span>

## <a name="congratulations"></a><span data-ttu-id="3f905-154">恭喜！</span><span class="sxs-lookup"><span data-stu-id="3f905-154">Congratulations</span></span>

<span data-ttu-id="3f905-155">在本教學課程中，您已學會 spatialize 按鈕互動音效，並使用音訊剪輯來測試 hrtf 按鈕互動。</span><span class="sxs-lookup"><span data-stu-id="3f905-155">In this tutorial you have learnt to spatialize the button interaction sounds and to use an audio clip to test spatialized button interaction.</span></span> <span data-ttu-id="3f905-156">在下一個教學課程中，您將瞭解如何從影片來源 spatialize 音訊。</span><span class="sxs-lookup"><span data-stu-id="3f905-156">In the next tutorial you will learn how to spatialize audio from an video source.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="3f905-157">下一個教學課程： 3. 從影片 Spatializing 音訊</span><span class="sxs-lookup"><span data-stu-id="3f905-157">Next Tutorial: 3. Spatializing audio from a video</span></span>](unity-spatial-audio-ch3.md)
