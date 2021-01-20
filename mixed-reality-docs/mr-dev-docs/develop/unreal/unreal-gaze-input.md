---
title: Unreal 中的注視輸入
description: 瞭解如何在 Unreal 中使用適用于 HoloLens 的眼睛追蹤和頭部方向來設定和使用注視輸入。
author: hferrone
ms.author: jacksonf
ms.date: 12/9/2020
ms.topic: article
keywords: Windows Mixed Reality、全像 HoloLens 2、眼睛追蹤、注視輸入、前端掛接顯示器、Unreal 引擎、混合現實耳機、windows Mixed reality 耳機、虛擬實境耳機
ms.openlocfilehash: 0c5191534313b94a5382d1065f5a5dd1a208bb49
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/20/2021
ms.locfileid: "98579984"
---
# <a name="gaze-input"></a><span data-ttu-id="8608b-104">注視輸入</span><span class="sxs-lookup"><span data-stu-id="8608b-104">Gaze Input</span></span>

<span data-ttu-id="8608b-105">在混合現實應用程式中看看輸入，全都是找出您的使用者所看到的內容。</span><span class="sxs-lookup"><span data-stu-id="8608b-105">Gaze input in mixed reality apps is all about finding out what your users are looking at.</span></span> <span data-ttu-id="8608b-106">當您裝置上的眼睛追蹤攝影機與 Unreal 世界空間中的光線相符時，您使用者的資料行資料就會變成可用。</span><span class="sxs-lookup"><span data-stu-id="8608b-106">When the eye tracking cameras on your device match up with rays in Unreal's world space, your user's line of sight data becomes available.</span></span> <span data-ttu-id="8608b-107">注視可用於藍圖和 c + +，而且是物件互動、尋找和攝影機控制項等機制的核心功能。</span><span class="sxs-lookup"><span data-stu-id="8608b-107">Gaze can be used in both blueprints and C++, and is a core feature for mechanics like object interaction, way finding, and camera controls.</span></span>

## <a name="enabling-eye-tracking"></a><span data-ttu-id="8608b-108">啟用眼睛追蹤</span><span class="sxs-lookup"><span data-stu-id="8608b-108">Enabling eye tracking</span></span>

- <span data-ttu-id="8608b-109">在 [ **> HoloLens 的專案設定**] 中，啟用 [ **注視輸入** ] 功能：</span><span class="sxs-lookup"><span data-stu-id="8608b-109">In **Project Settings > HoloLens**, enable the **Gaze Input** capability:</span></span>

![已反白顯示注視輸入的 HoloLens 專案設定功能螢幕擷取畫面](images/unreal-gaze-img-01.png)

- <span data-ttu-id="8608b-111">建立新的動作專案並將其新增至您的場景</span><span class="sxs-lookup"><span data-stu-id="8608b-111">Create a new actor and add it to your scene</span></span>

> [!NOTE]
> <span data-ttu-id="8608b-112">Unreal 中的 HoloLens 眼睛追蹤只會有一個眼睛光線。</span><span class="sxs-lookup"><span data-stu-id="8608b-112">HoloLens eye tracking in Unreal only has a single gaze ray for both eyes.</span></span> <span data-ttu-id="8608b-113">不支援 Stereoscopic 追蹤（需要兩個光線）。</span><span class="sxs-lookup"><span data-stu-id="8608b-113">Stereoscopic tracking, which requires two rays, isn't supported.</span></span>

## <a name="using-eye-tracking"></a><span data-ttu-id="8608b-114">使用眼球追蹤</span><span class="sxs-lookup"><span data-stu-id="8608b-114">Using eye tracking</span></span>

<span data-ttu-id="8608b-115">首先，請檢查您的裝置是否支援使用 **IsEyeTrackerConnected** 函式的眼睛追蹤。</span><span class="sxs-lookup"><span data-stu-id="8608b-115">First, check that your device supports eye tracking with the **IsEyeTrackerConnected** function.</span></span>  <span data-ttu-id="8608b-116">如果函式傳回 true，請呼叫 **GetGazeData** ，以找出使用者的眼睛在目前框架中的位置：</span><span class="sxs-lookup"><span data-stu-id="8608b-116">If the function returns true, call **GetGazeData** to find where the user’s eyes are looking at in the current frame:</span></span>

![的藍圖是眼睛追蹤連接函數](images/unreal-gaze-img-02.png)

> [!NOTE]
> <span data-ttu-id="8608b-118">HoloLens 上無法使用 fixation 點和信賴值。</span><span class="sxs-lookup"><span data-stu-id="8608b-118">The fixation point and the confidence value are not available on HoloLens.</span></span>

<span data-ttu-id="8608b-119">使用線條追蹤中的「注視原點」和「方向」來精確找出您的使用者所查看的位置。</span><span class="sxs-lookup"><span data-stu-id="8608b-119">Use the gaze origin and direction in a line trace to find out exactly where your users are looking.</span></span>  <span data-ttu-id="8608b-120">「注視」值是向量，從注視原點開始，然後在原點結束時再以線條軌跡距離乘以：</span><span class="sxs-lookup"><span data-stu-id="8608b-120">The gaze value is a vector, starting at the gaze origin and ending at the origin plus the gaze direction multiplied by the line trace distance:</span></span>

![Get-help Data 函數的藍圖](images/unreal-gaze-img-03.png)

## <a name="getting-head-orientation"></a><span data-ttu-id="8608b-122">取得頭部方向</span><span class="sxs-lookup"><span data-stu-id="8608b-122">Getting head orientation</span></span>

<span data-ttu-id="8608b-123">您也可以使用前端掛接顯示器的旋轉 (HMD) 來代表使用者的標頭方向。</span><span class="sxs-lookup"><span data-stu-id="8608b-123">You can also use the rotation of the Head Mounted Display (HMD) to represent the direction of the user’s head.</span></span> <span data-ttu-id="8608b-124">您可以取得使用者的前端方向，而不啟用注視輸入功能，但您不會收到任何眼睛追蹤資訊。</span><span class="sxs-lookup"><span data-stu-id="8608b-124">You can get the users head direction without enabling the Gaze Input capability, but you won't get you any eye tracking information.</span></span>  <span data-ttu-id="8608b-125">將藍圖的參考新增為世界內容，以取得正確的輸出資料：</span><span class="sxs-lookup"><span data-stu-id="8608b-125">Add a reference to the blueprint as the world context to get the correct output data:</span></span>

> [!NOTE]
> <span data-ttu-id="8608b-126">取得 HMD 資料僅適用于 Unreal 4.26 和更新版本。</span><span class="sxs-lookup"><span data-stu-id="8608b-126">Getting HMD Data is only available in Unreal 4.26 and onwards.</span></span>

![Get HMDData 函式的藍圖](images/unreal-gaze-img-04.png)

## <a name="using-c"></a><span data-ttu-id="8608b-128">使用 C++</span><span class="sxs-lookup"><span data-stu-id="8608b-128">Using C++</span></span>

- <span data-ttu-id="8608b-129">在您遊戲的 **build.cs** 檔案中，將 **EyeTracker** 新增至 **PublicDependencyModuleNames** 清單：</span><span class="sxs-lookup"><span data-stu-id="8608b-129">In your game’s **build.cs** file, add **EyeTracker** to the **PublicDependencyModuleNames** list:</span></span>

```cpp
PublicDependencyModuleNames.AddRange(
    new string[] {
        "Core",
        "CoreUObject",
        "Engine",
        "InputCore",
        "EyeTracker"
});
```

- <span data-ttu-id="8608b-130">在檔案 **/新的 c + + 類別** 中，建立名為 **EyeTracker** 的新 c + + 執行者。</span><span class="sxs-lookup"><span data-stu-id="8608b-130">In **File/ New C++ Class**, create a new C++ actor called **EyeTracker**</span></span>
    - <span data-ttu-id="8608b-131">Visual Studio 的解決方案將會開啟新的 EyeTracker 類別。</span><span class="sxs-lookup"><span data-stu-id="8608b-131">A Visual Studio solution will open up the new EyeTracker class.</span></span> <span data-ttu-id="8608b-132">建立並執行，以使用新的 EyeTracker 執行者開啟 Unreal 遊戲。</span><span class="sxs-lookup"><span data-stu-id="8608b-132">Build and run to open the Unreal game with the new EyeTracker actor.</span></span>  <span data-ttu-id="8608b-133">在 [ **放置** 動作專案] 視窗中搜尋 "EyeTracker"，並將類別拖放到遊戲視窗中，以將其新增至專案：</span><span class="sxs-lookup"><span data-stu-id="8608b-133">Search for “EyeTracker” in the **Place Actors** window and drag and drop the class into the game window to add it to the project:</span></span>

![開啟動作專案視窗的動作專案螢幕擷取畫面](images/unreal-gaze-img-06.png)

- <span data-ttu-id="8608b-135">在 **EyeTracker .cpp** 中，新增 **EyeTrackerFunctionLibrary** 和 **DrawDebugHelpers** 的 include：</span><span class="sxs-lookup"><span data-stu-id="8608b-135">In **EyeTracker.cpp**, add includes for **EyeTrackerFunctionLibrary**, and **DrawDebugHelpers**:</span></span>

```cpp
#include "EyeTrackerFunctionLibrary.h"
#include "DrawDebugHelpers.h"
```

<span data-ttu-id="8608b-136">檢查您的裝置是否支援使用 **UEyeTrackerFunctionLibrary：： IsEyeTrackerConnected** 的眼睛追蹤，然後再嘗試取得任何眼睛的資料。</span><span class="sxs-lookup"><span data-stu-id="8608b-136">Check that your device supports eye tracking with **UEyeTrackerFunctionLibrary::IsEyeTrackerConnected** before trying to get any gaze data.</span></span>  <span data-ttu-id="8608b-137">如果支援眼睛追蹤，請從 **UEyeTrackerFunctionLibrary：： GetGazeData** 找出線條追蹤的光線起點和終點。</span><span class="sxs-lookup"><span data-stu-id="8608b-137">If eye tracking is supported, find the start and end of a ray for a line trace from **UEyeTrackerFunctionLibrary::GetGazeData**.</span></span> <span data-ttu-id="8608b-138">從該處，您可以建立看看的向量，並將其內容傳遞給 **LineTraceSingleByChannel** ，以對任何光線搜尋結果進行處理：</span><span class="sxs-lookup"><span data-stu-id="8608b-138">From there, you can construct a gaze vector and pass its contents to **LineTraceSingleByChannel** to debug any ray hit results:</span></span>

```cpp
void AEyeTracker::Tick(float DeltaTime)
{
    Super::Tick(DeltaTime);

    if(UEyeTrackerFunctionLibrary::IsEyeTrackerConnected())
    {
        FEyeTrackerGazeData GazeData;
        if(UEyeTrackerFunctionLibrary::GetGazeData(GazeData))
        {
            FVector Start = GazeData.GazeOrigin;
            FVector End = GazeData.GazeOrigin + GazeData.GazeDirection * 100;

            FHitResult Hit Result;
            if (GWorld->LineTraceSingleByChannel(HitResult, Start, End, ECollisionChannel::ECC_Visiblity))
            {
                DrawDebugCoordinateSystem(GWorld, HitResult.Location, FQuat::Identity.Rotator(), 10);
            }
        }
    }
}
```

## <a name="next-development-checkpoint"></a><span data-ttu-id="8608b-139">下一個開發檢查點</span><span class="sxs-lookup"><span data-stu-id="8608b-139">Next Development Checkpoint</span></span>

<span data-ttu-id="8608b-140">依循我們配置的 Unreal 開發旅程，此時您會探索 MRTK核心建置組塊。</span><span class="sxs-lookup"><span data-stu-id="8608b-140">If you're following the Unreal development journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="8608b-141">接下來，您可以繼續進行下一個建置組塊：</span><span class="sxs-lookup"><span data-stu-id="8608b-141">From here, you can continue to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="8608b-142">手勢追蹤</span><span class="sxs-lookup"><span data-stu-id="8608b-142">Hand tracking</span></span>](unreal-hand-tracking.md)

<span data-ttu-id="8608b-143">或者，直接跳到混合實境平台功能和 API 的主題：</span><span class="sxs-lookup"><span data-stu-id="8608b-143">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="8608b-144">HoloLens 相機</span><span class="sxs-lookup"><span data-stu-id="8608b-144">HoloLens camera</span></span>](unreal-hololens-camera.md)

<span data-ttu-id="8608b-145">您可以隨時回到 [Unreal 開發檢查點](unreal-development-overview.md#2-core-building-blocks)。</span><span class="sxs-lookup"><span data-stu-id="8608b-145">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="8608b-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8608b-146">See also</span></span>
* [<span data-ttu-id="8608b-147">校正</span><span class="sxs-lookup"><span data-stu-id="8608b-147">Calibration</span></span>](/hololens/hololens-calibration)
* [<span data-ttu-id="8608b-148">舒適度</span><span class="sxs-lookup"><span data-stu-id="8608b-148">Comfort</span></span>](../../design/comfort.md)
* [<span data-ttu-id="8608b-149">目光和行動</span><span class="sxs-lookup"><span data-stu-id="8608b-149">Gaze and commit</span></span>](../../design/gaze-and-commit.md)
* [<span data-ttu-id="8608b-150">語音輸入</span><span class="sxs-lookup"><span data-stu-id="8608b-150">Voice input</span></span>](../../out-of-scope/voice-design.md)