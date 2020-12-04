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
# <a name="gaze-input"></a>注視輸入

注視用來指出使用者所查看的內容。  這會使用裝置上的眼睛追蹤攝影機，在 Unreal 世界空間中尋找符合使用者目前查看的光線。

## <a name="enabling-eye-tracking"></a>啟用眼睛追蹤

- 在 [ **> HoloLens 的專案設定**] 中，啟用 [ **注視輸入** ] 功能：

![已反白顯示注視輸入的 HoloLens 專案設定功能螢幕擷取畫面](images/unreal-gaze-img-01.png)

- 建立新的動作專案並將其新增至您的場景

> [!NOTE] 
> Unreal 中的 HoloLens 眼睛追蹤只會有一個眼睛光線，而不是 stereoscopic 追蹤所需的兩個光線，而這是不受支援的。

## <a name="using-eye-tracking"></a>使用眼球追蹤

先確認裝置支援使用 IsEyeTrackerConnected 函式的眼睛追蹤。  如果傳回 true，請呼叫 GetGazeData，以找出使用者的眼睛在目前畫面格的位置：

![的藍圖是眼睛追蹤連接函數](images/unreal-gaze-img-02.png)

> [!NOTE]
> HoloLens 上無法使用 fixation 點和信賴值。

若要找出使用者所查看的內容，請線上條追蹤中使用 [注視來源] 和 [方向]。  此向量的開頭是注視原點，而結尾是原點，而注視方向乘以所需距離：

![Get-help Data 函數的藍圖](images/unreal-gaze-img-03.png)

## <a name="getting-head-orientation"></a>取得頭部方向

或者，HMD 旋轉可以用來代表使用者的標頭方向。  這並不需要注視輸入功能，但不會提供任何眼睛追蹤資訊。  您必須將藍圖的參考新增為世界內容，才能取得正確的輸出資料：

> [!NOTE]
> 取得 HMD 資料僅適用于 Unreal 4.26 和更新版本。

![Get HMDData 函式的藍圖](images/unreal-gaze-img-04.png)

## <a name="using-c"></a>使用 C++ 

- 在您遊戲的 build.cs 檔案中，將 "EyeTracker" 新增至 PublicDependencyModuleNames 清單：

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

- 在 [File/New c + + 類別] 中，建立名為 "EyeTracker" 的新 c + + 執行者
    - Visual Studio 的解決方案將會開啟新的 EyeTracker 類別。 建立並執行，以使用新的 EyeTracker 執行者開啟 Unreal 遊戲。  在 [放置動作專案] 視窗中搜尋 "EyeTracker"。  將此類別拖放到遊戲視窗中，以將它新增至專案：

![開啟動作專案視窗的動作專案螢幕擷取畫面](images/unreal-gaze-img-06.png)

- 在 EyeTracker .cpp 中，新增 EyeTrackerFunctionLibrary 和 DrawDebugHelpers 的 include：

```cpp
#include "EyeTrackerFunctionLibrary.h"
#include "DrawDebugHelpers.h"
```

在 [滴答] 中，檢查裝置是否支援使用 UEyeTrackerFunctionLibrary：： IsEyeTrackerConnected 的眼睛追蹤。  然後，從 UEyeTrackerFunctionLibrary：： GetGazeData 找出線條追蹤的光線起點和終點：

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

## <a name="next-development-checkpoint"></a>下一個開發檢查點

依循我們配置的 Unreal 開發檢查點旅程，此時您會探索 MRTK核心建置組塊。 接下來，您可以繼續進行下一個建置組塊： 

> [!div class="nextstepaction"]
> [手勢追蹤](unreal-hand-tracking.md)

或者，直接跳到混合實境平台功能和 API 的主題：

> [!div class="nextstepaction"]
> [HoloLens 相機](unreal-hololens-camera.md)

您可以隨時回到 [Unreal 開發檢查點](unreal-development-overview.md#2-core-building-blocks)。

## <a name="see-also"></a>另請參閱
* [校正](../../calibration.md)
* [舒適度](../../design/comfort.md)
* [目光和行動](../../design/gaze-and-commit.md)
* [語音輸入](../../out-of-scope/voice-design.md)
