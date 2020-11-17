---
title: 空間音訊教學課程-2。 空間化按鈕互動音效
description: 將按鈕加入至您的專案，並 spatialize 按鈕互動音效。
author: kegodin
ms.author: kegodin
ms.date: 12/01/2019
ms.topic: article
keywords: 混合的現實、unity、教學課程、hololens2、空間音訊、MRTK、混合現實工具組、UWP、Windows 10、HRTF、head 相關的傳送函式、回音、Microsoft 空間定位器、prefabs、音量曲線
ms.openlocfilehash: eb550c3127e13926d73428b337abfd7cf9872eb7
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2020
ms.locfileid: "94678187"
---
# <a name="spatializing-button-interaction-sounds"></a><span data-ttu-id="06e79-105">空間化按鈕互動音效</span><span class="sxs-lookup"><span data-stu-id="06e79-105">Spatializing button interaction sounds</span></span>

## <a name="objectives"></a><span data-ttu-id="06e79-106">目標</span><span class="sxs-lookup"><span data-stu-id="06e79-106">Objectives</span></span>
<span data-ttu-id="06e79-107">在 HoloLens 2 教學課程的空間音訊模組的第二章中，您將會：</span><span class="sxs-lookup"><span data-stu-id="06e79-107">In this second chapter of the spatial audio module of the HoloLens 2 tutorials, you'll:</span></span>
* <span data-ttu-id="06e79-108">新增按鈕</span><span class="sxs-lookup"><span data-stu-id="06e79-108">Add a button</span></span>
* <span data-ttu-id="06e79-109">Spatialize 按鈕的 click 聲</span><span class="sxs-lookup"><span data-stu-id="06e79-109">Spatialize the button click sounds</span></span>

## <a name="add-a-button"></a><span data-ttu-id="06e79-110">新增按鈕</span><span class="sxs-lookup"><span data-stu-id="06e79-110">Add a button</span></span>
<span data-ttu-id="06e79-111">在 [ **專案** ] 窗格中，選取 [ **資產** ]，然後在搜尋列中輸入 "PressableButtonHoloLens2"：</span><span class="sxs-lookup"><span data-stu-id="06e79-111">In the **Project** pane, select **Assets** and type "PressableButtonHoloLens2" in the search bar:</span></span>

![資產中的按鈕預製專案](images/spatial-audio/button-prefab-in-assets.png)

<span data-ttu-id="06e79-113">按鈕預製專案是以藍色圖示（而非白色圖示）表示的專案。</span><span class="sxs-lookup"><span data-stu-id="06e79-113">The button prefab is the entry represented by a blue icon, rather than a white icon.</span></span> <span data-ttu-id="06e79-114">將名為 **PressableButtonHoloLens2** 的預製專案拖曳到 [ **階層] 窗格** 中。</span><span class="sxs-lookup"><span data-stu-id="06e79-114">Drag the prefab named **PressableButtonHoloLens2** into the **Hierarchy** pane.</span></span> <span data-ttu-id="06e79-115">在新按鈕的 [偵測 **器** ] 窗格中，將 [ **位置** ] 屬性設定為 (0、-0.4、2) ，以便在應用程式啟動時出現在使用者前面。</span><span class="sxs-lookup"><span data-stu-id="06e79-115">In the **Inspector** pane for your new button, set the **Position** property to (0, -0.4, 2) so that it will appear in front of the user when the application starts.</span></span> <span data-ttu-id="06e79-116">按鈕的 **轉換** 元件看起來會像這樣：</span><span class="sxs-lookup"><span data-stu-id="06e79-116">The **Transform** component of the button will look like this:</span></span>

![按鈕轉換](images/spatial-audio/button-transform.png)

## <a name="spatialize-button-feedback"></a><span data-ttu-id="06e79-118">Spatialize 按鈕意見反應</span><span class="sxs-lookup"><span data-stu-id="06e79-118">Spatialize button feedback</span></span>
<span data-ttu-id="06e79-119">在此步驟中，您將 spatialize 按鈕的音訊意見反應。</span><span class="sxs-lookup"><span data-stu-id="06e79-119">In this step, you'll spatialize the audio feedback for the button.</span></span> <span data-ttu-id="06e79-120">如需相關的設計建議，請參閱 [空間音效設計](../../../design/spatial-sound-design.md)。</span><span class="sxs-lookup"><span data-stu-id="06e79-120">For related design suggestions, see [spatial sound design](../../../design/spatial-sound-design.md).</span></span> 

<span data-ttu-id="06e79-121">您可以在 [**音訊混音** 器] 窗格中，為音訊 **來源** 元件定義音訊播放的目的地，稱為 **混音器群組**。</span><span class="sxs-lookup"><span data-stu-id="06e79-121">The **Audio Mixer** pane is where you'll define destinations, called **Mixer Groups**, for audio playback from **Audio Source** components.</span></span> 
* <span data-ttu-id="06e79-122">使用 **視窗-> 音訊 > 音訊混音** 器，從功能表列開啟 [**音訊混音** 器] 窗格</span><span class="sxs-lookup"><span data-stu-id="06e79-122">Open the **Audio Mixer** pane from the menu bar using **Window -> Audio -> Audio Mixer**</span></span>
* <span data-ttu-id="06e79-123">按一下 [ **Mixers**] 旁邊的 [+]，以建立 **混音** 器。</span><span class="sxs-lookup"><span data-stu-id="06e79-123">Create a **Mixer** by clicking the '+' next to **Mixers**.</span></span> <span data-ttu-id="06e79-124">新的混音器將包含稱為 **Master** 的預設 **群組**。</span><span class="sxs-lookup"><span data-stu-id="06e79-124">The new mixer will include a default **Group** called **Master**.</span></span>

<span data-ttu-id="06e79-125">您的 **混音** 器窗格現在看起來像這樣：</span><span class="sxs-lookup"><span data-stu-id="06e79-125">Your **Mixer** pane will now look like this:</span></span>

![具有第一個混音器的混音器面板](images/spatial-audio/mixer-panel-with-first-mixer.png)

> [!NOTE]
> <span data-ttu-id="06e79-127">在 [第5章](unity-spatial-audio-ch5.md)啟用 [回條] 之前，混音器的音量計量不會顯示透過 Microsoft 空間定位器播放之音效的活動</span><span class="sxs-lookup"><span data-stu-id="06e79-127">Until reverb is enabled in [Chapter 5](unity-spatial-audio-ch5.md), the mixer's volume meter doesn't show activity for sounds played through the Microsoft Spatializer</span></span>

<span data-ttu-id="06e79-128">按一下 [**階層] 窗格中的 [** **PressableButtonHoloLens2** ]。</span><span class="sxs-lookup"><span data-stu-id="06e79-128">Click the **PressableButtonHoloLens2** in the **Hierarchy** pane.</span></span> <span data-ttu-id="06e79-129">在 [偵測 **器** ] 窗格中：</span><span class="sxs-lookup"><span data-stu-id="06e79-129">In the **Inspector** pane:</span></span>
1. <span data-ttu-id="06e79-130">尋找 **音訊來源** 元件</span><span class="sxs-lookup"><span data-stu-id="06e79-130">Find the **Audio Source** component</span></span>
2. <span data-ttu-id="06e79-131">針對 [ **輸出** ] 屬性，按一下選取器並選擇混音器</span><span class="sxs-lookup"><span data-stu-id="06e79-131">For the **Output** property, click the selector and choose your mixer</span></span>
3. <span data-ttu-id="06e79-132">核取 [ **Spatialize** ] 核取方塊</span><span class="sxs-lookup"><span data-stu-id="06e79-132">Check the **Spatialize** checkbox</span></span>
4. <span data-ttu-id="06e79-133">將 **空間 Blend** 滑杆移至 3d (1) 。</span><span class="sxs-lookup"><span data-stu-id="06e79-133">Move the **Spatial Blend** slider to 3D (1).</span></span>

> [!NOTE]
> <span data-ttu-id="06e79-134">在2019之前的 Unity 版本中，[Spatialize] 核取方塊位於 **音訊來源** 的 [偵測 **器**] 窗格底部。</span><span class="sxs-lookup"><span data-stu-id="06e79-134">In versions of Unity prior to 2019, the 'Spatialize' checkbox is at the bottom of the **Inspector** pane for the **Audio Source**.</span></span>

<span data-ttu-id="06e79-135">這些變更之後， **PressableButtonHoloLens2** 的 **音訊來源** 元件看起來會像這樣：</span><span class="sxs-lookup"><span data-stu-id="06e79-135">After these changes, the **Audio Source** component of your **PressableButtonHoloLens2** will look like this:</span></span>

![按鈕音訊來源](images/spatial-audio/button-audio-source.png)

> [!NOTE]
> <span data-ttu-id="06e79-137">如果您在未核取 [ **Spatialize** ] 核取方塊的情況下，將 **空間 Blend** 移至 1 (3d) ，Unity 將會使用其移動流覽空間定位器，而不是使用 hrtf 的 **Microsoft 空間定位器**。</span><span class="sxs-lookup"><span data-stu-id="06e79-137">If you move **Spatial Blend** to 1 (3D) without checking the **Spatialize** checkbox, Unity will use its panning spatializer, instead of the **Microsoft Spatializer** with HRTFs.</span></span>

## <a name="adjust-the-volume-curve"></a><span data-ttu-id="06e79-138">調整音量曲線</span><span class="sxs-lookup"><span data-stu-id="06e79-138">Adjust the Volume curve</span></span>
<span data-ttu-id="06e79-139">根據預設，Unity 會在從接聽程式更遠的情況下 attenuate hrtf 音效。</span><span class="sxs-lookup"><span data-stu-id="06e79-139">By default, Unity will attenuate spatialized sounds as they get farther from the listener.</span></span> <span data-ttu-id="06e79-140">當此衰減套用至互動回饋音效時，介面可能會變得更難使用。</span><span class="sxs-lookup"><span data-stu-id="06e79-140">When this attenuation is applied to interaction feedback sounds, the interface can become more difficult to use.</span></span>

<span data-ttu-id="06e79-141">若要停用此衰減，請調整 **音量** 曲線。</span><span class="sxs-lookup"><span data-stu-id="06e79-141">To disable this attenuation, adjust the **Volume** curve.</span></span> <span data-ttu-id="06e79-142">在 **PressableButtonHoloLens2** 的 [偵測 **器**] 窗格的 [**音訊來源**] 元件中，有一個稱為 **3d 音效設定** 的區段。</span><span class="sxs-lookup"><span data-stu-id="06e79-142">In the **Audio Source** component of the **Inspector** pane for the **PressableButtonHoloLens2**, there is a section called **3D Sound Settings**.</span></span> <span data-ttu-id="06e79-143">在該區段中：</span><span class="sxs-lookup"><span data-stu-id="06e79-143">In that section:</span></span>
1. <span data-ttu-id="06e79-144">將 **Volume Rolloff** 屬性設定為線性</span><span class="sxs-lookup"><span data-stu-id="06e79-144">Set the **Volume Rolloff** property to Linear</span></span>
2. <span data-ttu-id="06e79-145">拖曳 **音量** 曲線上的端點 (紅色曲線) 從 y 軸上的 ' 0 ' 到 ' 1 '</span><span class="sxs-lookup"><span data-stu-id="06e79-145">Drag the endpoint on the **Volume** curve (the red curve) from '0' on the y axis up to '1'</span></span>
3. <span data-ttu-id="06e79-146">若要將 **音量** 曲線的形狀調整為平面，請將白色曲線圖形控制項平行地拖曳至 X 軸</span><span class="sxs-lookup"><span data-stu-id="06e79-146">To adjust the shape of the **Volume** curve to be flat, drag the white curve shape control to be parallel to the X axis</span></span>

<span data-ttu-id="06e79-147">這些變更之後， **PressableButtonHoloLens2** **音訊來源** 屬性的 [ **3d 音效設定**] 區段看起來會像這樣：</span><span class="sxs-lookup"><span data-stu-id="06e79-147">After these changes, the **3D Sound Settings** section of the **Audio Source** properties of the **PressableButtonHoloLens2** will look like this:</span></span>

![按鈕3D 音效設定](images/spatial-audio/button-3d-sound-settings.png)

## <a name="testing-the-spatialize-audio"></a><span data-ttu-id="06e79-149">測試 spatialize 音訊</span><span class="sxs-lookup"><span data-stu-id="06e79-149">Testing the spatialize audio</span></span>

<span data-ttu-id="06e79-150">您可以隨意測試新的 hrtf 按鈕互動音效：</span><span class="sxs-lookup"><span data-stu-id="06e79-150">Feel free to test out the new spatialized button interaction sounds:</span></span>

* <span data-ttu-id="06e79-151">在 Unity 編輯器中輸入遊戲模式，最好是場景中的迴圈音訊範例</span><span class="sxs-lookup"><span data-stu-id="06e79-151">Enter game mode in the Unity editor, ideally with a looped audio sample in the scene</span></span>
* <span data-ttu-id="06e79-152">從左至右移動物件與音訊來源，並比較是否已啟用空間音訊。</span><span class="sxs-lookup"><span data-stu-id="06e79-152">Move the object with the audio source from left to right and compare with and without spatial audio enabled.</span></span> <span data-ttu-id="06e79-153">您可以透過下列方式變更要測試的音訊來源設定：</span><span class="sxs-lookup"><span data-stu-id="06e79-153">You can change the Audio Source settings for testing by:</span></span>
    * <span data-ttu-id="06e79-154">將空間 Blend 屬性移至 0-1 (2D 非 hrtf 和 3D hrtf 音效) </span><span class="sxs-lookup"><span data-stu-id="06e79-154">Moving the Spatial Blend property between 0 - 1 (2D non-spatialized and 3D spatialized sound)</span></span>
    * <span data-ttu-id="06e79-155">檢查和取消選取 Spatialize 屬性</span><span class="sxs-lookup"><span data-stu-id="06e79-155">Checking and unchecking the Spatialize property</span></span>

## <a name="next-steps"></a><span data-ttu-id="06e79-156">後續步驟</span><span class="sxs-lookup"><span data-stu-id="06e79-156">Next steps</span></span>

<span data-ttu-id="06e79-157">在 HoloLens 2 或 Unity 編輯器中試用您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="06e79-157">Try out your app on a HoloLens 2, or in the Unity editor.</span></span> <span data-ttu-id="06e79-158">在應用程式中，您可以觸控按鈕，聽聽 hrtf 按鈕的互動音效。</span><span class="sxs-lookup"><span data-stu-id="06e79-158">In the app, you can touch the button and hear the spatialized button interaction sounds.</span></span>

<span data-ttu-id="06e79-159">在 Unity 編輯器中進行測試時，請按下空格鍵並以滾輪滾動，以啟動手動模擬。</span><span class="sxs-lookup"><span data-stu-id="06e79-159">When testing in the Unity editor, press the space bar and scroll with the scroll wheel to activate hand simulation.</span></span> <span data-ttu-id="06e79-160">如需詳細資訊，請參閱 [MRTK 檔](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene)。</span><span class="sxs-lookup"><span data-stu-id="06e79-160">For more info, see the [MRTK documentation](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene).</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="06e79-161">第3章</span><span class="sxs-lookup"><span data-stu-id="06e79-161">Chapter 3</span></span>](unity-spatial-audio-ch3.md)

