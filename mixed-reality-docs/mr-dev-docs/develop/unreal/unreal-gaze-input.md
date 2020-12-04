---
title: Unreal 中的注視輸入
description: 針對 HoloLens 和 Unreal 引擎設定注視輸入的教學課程
author: hferrone
ms.author: jacksonf
ms.date: 06/10/2020
ms.topic: article
keywords: Windows Mixed Reality、全像 HoloLens 2、眼睛追蹤、注視輸入、前端掛接顯示器、Unreal 引擎、混合現實耳機、windows Mixed reality 耳機、虛擬實境耳機
ms.openlocfilehash: d0470c5abbefce797254aa9f2030519d3347aaab
ms.sourcegitcommit: 9c640c96e2270ef69edd46f1b12acb00b373554d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/04/2020
ms.locfileid: "96578887"
---
# <a name="gaze-input"></a><span data-ttu-id="29218-104">注視輸入</span><span class="sxs-lookup"><span data-stu-id="29218-104">Gaze Input</span></span>

<span data-ttu-id="29218-105">注視用來指出使用者所查看的內容。</span><span class="sxs-lookup"><span data-stu-id="29218-105">Gaze is used to indicate what the user is looking at.</span></span>  <span data-ttu-id="29218-106">這會使用裝置上的眼睛追蹤攝影機，在 Unreal 世界空間中尋找符合使用者目前查看的光線。</span><span class="sxs-lookup"><span data-stu-id="29218-106">This uses the eye tracking cameras on the device to find a ray in Unreal world space matching what the user is currently looking at.</span></span>

## <a name="enabling-eye-tracking"></a><span data-ttu-id="29218-107">啟用眼睛追蹤</span><span class="sxs-lookup"><span data-stu-id="29218-107">Enabling eye tracking</span></span>

- <span data-ttu-id="29218-108">在 [ **> HoloLens 的專案設定**] 中，啟用 [ **注視輸入** ] 功能：</span><span class="sxs-lookup"><span data-stu-id="29218-108">In **Project Settings > HoloLens**, enable the **Gaze Input** capability:</span></span>

![已反白顯示注視輸入的 HoloLens 專案設定功能螢幕擷取畫面](images/unreal-gaze-img-01.png)

- <span data-ttu-id="29218-110">建立新的動作專案並將其新增至您的場景</span><span class="sxs-lookup"><span data-stu-id="29218-110">Create a new actor and add it to your scene</span></span>

> [!NOTE] 
> <span data-ttu-id="29218-111">Unreal 中的 HoloLens 眼睛追蹤只會有一個眼睛光線，而不是 stereoscopic 追蹤所需的兩個光線，而這是不受支援的。</span><span class="sxs-lookup"><span data-stu-id="29218-111">HoloLens eye tracking in Unreal only has a single gaze ray for both eyes instead of the two rays needed for stereoscopic tracking, which is not supported.</span></span>

## <a name="using-eye-tracking"></a><span data-ttu-id="29218-112">使用眼球追蹤</span><span class="sxs-lookup"><span data-stu-id="29218-112">Using eye tracking</span></span>

<span data-ttu-id="29218-113">先確認裝置支援使用 IsEyeTrackerConnected 函式的眼睛追蹤。</span><span class="sxs-lookup"><span data-stu-id="29218-113">First check that the device supports eye tracking with the IsEyeTrackerConnected function.</span></span>  <span data-ttu-id="29218-114">如果傳回 true，請呼叫 GetGazeData，以找出使用者的眼睛在目前畫面格的位置：</span><span class="sxs-lookup"><span data-stu-id="29218-114">If this returns true, call GetGazeData to find where the user’s eyes are looking at during the current frame:</span></span>

![的藍圖是眼睛追蹤連接函數](images/unreal-gaze-img-02.png)

> [!NOTE]
> <span data-ttu-id="29218-116">HoloLens 上無法使用 fixation 點和信賴值。</span><span class="sxs-lookup"><span data-stu-id="29218-116">The fixation point and the confidence value are not available on HoloLens.</span></span>

<span data-ttu-id="29218-117">若要找出使用者所查看的內容，請線上條追蹤中使用 [注視來源] 和 [方向]。</span><span class="sxs-lookup"><span data-stu-id="29218-117">To find what the user is looking at, use the gaze origin and direction in a line trace.</span></span>  <span data-ttu-id="29218-118">此向量的開頭是注視原點，而結尾是原點，而注視方向乘以所需距離：</span><span class="sxs-lookup"><span data-stu-id="29218-118">The start of this vector is the gaze origin and the end is the origin plus the gaze direction multiplied by the desired distance:</span></span>

![Get-help Data 函數的藍圖](images/unreal-gaze-img-03.png)

## <a name="getting-head-orientation"></a><span data-ttu-id="29218-120">取得頭部方向</span><span class="sxs-lookup"><span data-stu-id="29218-120">Getting head orientation</span></span>

<span data-ttu-id="29218-121">或者，HMD 旋轉可以用來代表使用者的標頭方向。</span><span class="sxs-lookup"><span data-stu-id="29218-121">Alternatively, the HMD rotation can be used to represent the direction of the user’s head.</span></span>  <span data-ttu-id="29218-122">這並不需要注視輸入功能，但不會提供任何眼睛追蹤資訊。</span><span class="sxs-lookup"><span data-stu-id="29218-122">This does not require the Gaze Input capability but won't give you any eye tracking information.</span></span>  <span data-ttu-id="29218-123">您必須將藍圖的參考新增為世界內容，才能取得正確的輸出資料：</span><span class="sxs-lookup"><span data-stu-id="29218-123">A reference to the blueprint must be added as the world context to get the correct output data:</span></span>

> [!NOTE]
> <span data-ttu-id="29218-124">取得 HMD 資料僅適用于 Unreal 4.26 和更新版本。</span><span class="sxs-lookup"><span data-stu-id="29218-124">Getting HMD Data is only available in Unreal 4.26 and onwards.</span></span>

![Get HMDData 函式的藍圖](images/unreal-gaze-img-04.png)

## <a name="using-c"></a><span data-ttu-id="29218-126">使用 C++</span><span class="sxs-lookup"><span data-stu-id="29218-126">Using C++</span></span> 

- <span data-ttu-id="29218-127">在您遊戲的 build.cs 檔案中，將 "EyeTracker" 新增至 PublicDependencyModuleNames 清單：</span><span class="sxs-lookup"><span data-stu-id="29218-127">In your game’s build.cs file, add “EyeTracker” to the PublicDependencyModuleNames list:</span></span>

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

- <span data-ttu-id="29218-128">在 [File/New c + + 類別] 中，建立名為 "EyeTracker" 的新 c + + 執行者</span><span class="sxs-lookup"><span data-stu-id="29218-128">In “File/ New C++ Class”, Create a new C++ actor called “EyeTracker”</span></span>
    - <span data-ttu-id="29218-129">Visual Studio 的解決方案將會開啟新的 EyeTracker 類別。</span><span class="sxs-lookup"><span data-stu-id="29218-129">A Visual Studio solution will open to the new EyeTracker class.</span></span> <span data-ttu-id="29218-130">建立並執行，以使用新的 EyeTracker 執行者開啟 Unreal 遊戲。</span><span class="sxs-lookup"><span data-stu-id="29218-130">Build and run to open the Unreal game with the new EyeTracker actor.</span></span>  <span data-ttu-id="29218-131">在 [放置動作專案] 視窗中搜尋 "EyeTracker"。</span><span class="sxs-lookup"><span data-stu-id="29218-131">Search for “EyeTracker” in the “Place Actors” window.</span></span>  <span data-ttu-id="29218-132">將此類別拖放到遊戲視窗中，以將它新增至專案：</span><span class="sxs-lookup"><span data-stu-id="29218-132">Drag and drop this class into the game window to add it to the project:</span></span>

![開啟動作專案視窗的動作專案螢幕擷取畫面](images/unreal-gaze-img-06.png)

- <span data-ttu-id="29218-134">在 EyeTracker .cpp 中，新增 EyeTrackerFunctionLibrary 和 DrawDebugHelpers 的 include：</span><span class="sxs-lookup"><span data-stu-id="29218-134">In EyeTracker.cpp, add includes for EyeTrackerFunctionLibrary, and DrawDebugHelpers:</span></span>

```cpp
#include "EyeTrackerFunctionLibrary.h"
#include "DrawDebugHelpers.h"
```

<span data-ttu-id="29218-135">在 [滴答] 中，檢查裝置是否支援使用 UEyeTrackerFunctionLibrary：： IsEyeTrackerConnected 的眼睛追蹤。</span><span class="sxs-lookup"><span data-stu-id="29218-135">In Tick, check that the device supports eye tracking with UEyeTrackerFunctionLibrary::IsEyeTrackerConnected.</span></span>  <span data-ttu-id="29218-136">然後，從 UEyeTrackerFunctionLibrary：： GetGazeData 找出線條追蹤的光線起點和終點：</span><span class="sxs-lookup"><span data-stu-id="29218-136">Then find the start and end of a ray for a line trace from UEyeTrackerFunctionLibrary::GetGazeData:</span></span>

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

## <a name="next-development-checkpoint"></a><span data-ttu-id="29218-137">下一個開發檢查點</span><span class="sxs-lookup"><span data-stu-id="29218-137">Next Development Checkpoint</span></span>

<span data-ttu-id="29218-138">依循我們配置的 Unreal 開發檢查點旅程，此時您會探索 MRTK核心建置組塊。</span><span class="sxs-lookup"><span data-stu-id="29218-138">If you're following the Unreal development checkpoint journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="29218-139">接下來，您可以繼續進行下一個建置組塊：</span><span class="sxs-lookup"><span data-stu-id="29218-139">From here, you can proceed to the next building block:</span></span> 

> [!div class="nextstepaction"]
> [<span data-ttu-id="29218-140">手勢追蹤</span><span class="sxs-lookup"><span data-stu-id="29218-140">Hand tracking</span></span>](unreal-hand-tracking.md)

<span data-ttu-id="29218-141">或者，直接跳到混合實境平台功能和 API 的主題：</span><span class="sxs-lookup"><span data-stu-id="29218-141">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="29218-142">HoloLens 相機</span><span class="sxs-lookup"><span data-stu-id="29218-142">HoloLens camera</span></span>](unreal-hololens-camera.md)

<span data-ttu-id="29218-143">您可以隨時回到 [Unreal 開發檢查點](unreal-development-overview.md#2-core-building-blocks)。</span><span class="sxs-lookup"><span data-stu-id="29218-143">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="29218-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="29218-144">See also</span></span>
* [<span data-ttu-id="29218-145">校正</span><span class="sxs-lookup"><span data-stu-id="29218-145">Calibration</span></span>](../../calibration.md)
* [<span data-ttu-id="29218-146">舒適度</span><span class="sxs-lookup"><span data-stu-id="29218-146">Comfort</span></span>](../../design/comfort.md)
* [<span data-ttu-id="29218-147">目光和行動</span><span class="sxs-lookup"><span data-stu-id="29218-147">Gaze and commit</span></span>](../../design/gaze-and-commit.md)
* [<span data-ttu-id="29218-148">語音輸入</span><span class="sxs-lookup"><span data-stu-id="29218-148">Voice input</span></span>](../../out-of-scope/voice-design.md)
