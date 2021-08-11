---
title: Unreal 中的注視輸入
description: 瞭解如何在 Unreal 中使用 HoloLens 應用程式的眼睛追蹤和頭部方向來設定和使用注視輸入。
author: hferrone
ms.author: jacksonf
ms.date: 12/9/2020
ms.topic: article
keywords: Windows Mixed Reality、全像 HoloLens 2、眼睛追蹤、注視輸入、前端掛接顯示器、Unreal 引擎、混合現實耳機、Windows Mixed reality 耳機、虛擬實境耳機
ms.openlocfilehash: e423086e293629e3dfadb49b52a376c0b93f5e465328b93f47c2f1e3e0790b63
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2021
ms.locfileid: "115200668"
---
# <a name="gaze-input"></a>注視輸入

在混合現實應用程式中看看輸入，全都是找出您的使用者所看到的內容。 當您裝置上的眼睛追蹤攝影機與 Unreal 世界空間中的光線相符時，您使用者的資料行資料就會變成可用。 注視可用於藍圖和 c + +，而且是物件互動、尋找和攝影機控制項等機制的核心功能。

## <a name="enabling-eye-tracking"></a>啟用眼睛追蹤

- 在 **Project 設定 > HoloLens** 中，啟用「**注視輸入**」功能：

![醒目提示輸入注視輸入的 HoloLens 專案設定功能的螢幕擷取畫面](images/unreal-gaze-img-01.png)

- 建立新的動作專案並將其新增至您的場景

> [!NOTE]
> Unreal 中的眼睛追蹤在中只會有一個眼睛光線。 HoloLens 不支援 Stereoscopic 追蹤（需要兩個光線）。

## <a name="using-eye-tracking"></a>使用眼球追蹤

首先，請檢查您的裝置是否支援使用 **IsEyeTrackerConnected** 函式的眼睛追蹤。  如果函式傳回 true，請呼叫 **GetGazeData** ，以找出使用者的眼睛在目前框架中的位置：

![的藍圖是眼睛追蹤連接函數](images/unreal-gaze-img-02.png)

> [!NOTE]
> HoloLens 上無法使用 fixation 點和信賴值。

使用線條追蹤中的「注視原點」和「方向」來精確找出您的使用者所查看的位置。  「注視」值是向量，從注視原點開始，然後在原點結束時再以線條軌跡距離乘以：

![Get-help Data 函數的藍圖](images/unreal-gaze-img-03.png)

## <a name="getting-head-orientation"></a>取得頭部方向

您也可以使用前端掛接顯示器的旋轉 (HMD) 來代表使用者的標頭方向。 您可以取得使用者的前端方向，而不啟用注視輸入功能，但您不會收到任何眼睛追蹤資訊。  將藍圖的參考新增為世界內容，以取得正確的輸出資料：

> [!NOTE]
> 取得 HMD 資料僅適用于 Unreal 4.26 和更新版本。

![Get HMDData 函式的藍圖](images/unreal-gaze-img-04.png)

## <a name="using-c"></a>使用 C++

- 在您遊戲的 **build .cs** 檔案中，將 **EyeTracker** 新增至 **PublicDependencyModuleNames** 清單：

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

- 在檔案 **/新的 c + + 類別** 中，建立名為 **EyeTracker** 的新 c + + 執行者。
    - Visual Studio 的解決方案將會開啟新的 EyeTracker 類別。 建立並執行，以使用新的 EyeTracker 執行者開啟 Unreal 遊戲。  在 [ **放置** 動作專案] 視窗中搜尋 "EyeTracker"，並將類別拖放到遊戲視窗中，以將其新增至專案：

![開啟動作專案視窗的動作專案螢幕擷取畫面](images/unreal-gaze-img-06.png)

- 在 **EyeTracker .cpp** 中，新增 **EyeTrackerFunctionLibrary** 和 **DrawDebugHelpers** 的 include：

```cpp
#include "EyeTrackerFunctionLibrary.h"
#include "DrawDebugHelpers.h"
```

檢查您的裝置是否支援使用 **UEyeTrackerFunctionLibrary：： IsEyeTrackerConnected** 的眼睛追蹤，然後再嘗試取得任何眼睛的資料。  如果支援眼睛追蹤，請從 **UEyeTrackerFunctionLibrary：： GetGazeData** 找出線條追蹤的光線起點和終點。 從該處，您可以建立看看的向量，並將其內容傳遞給 **LineTraceSingleByChannel** ，以對任何光線搜尋結果進行處理：

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

依循我們配置的 Unreal 開發旅程，此時您會探索 MRTK核心建置組塊。 接下來，您可以繼續進行下一個建置組塊：

> [!div class="nextstepaction"]
> [手勢追蹤](unreal-hand-tracking.md)

或者，直接跳到混合實境平台功能和 API 的主題：

> [!div class="nextstepaction"]
> [HoloLens 相機](unreal-hololens-camera.md)

您可以隨時回到 [Unreal 開發檢查點](unreal-development-overview.md#2-core-building-blocks)。

## <a name="see-also"></a>另請參閱
* [校正](/hololens/hololens-calibration)
* [舒適度](../../design/comfort.md)
* [目光和行動](../../design/gaze-and-commit.md)
* [語音輸入](../../out-of-scope/voice-design.md)