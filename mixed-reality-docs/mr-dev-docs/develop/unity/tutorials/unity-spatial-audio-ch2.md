---
title: 空間音訊教學課程-2。 空間化按鈕互動音效
description: 將按鈕加入至您的專案，並 spatialize 按鈕互動音效。
author: kegodin
ms.author: kegodin
ms.date: 12/01/2019
ms.topic: article
keywords: 混合現實、unity、教學課程、hololens2、空間音訊
ms.openlocfilehash: 25386819826efc6f25182e0780ff148206248a06
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2020
ms.locfileid: "91682328"
---
# <a name="spatializing-button-interaction-sounds"></a>空間化按鈕互動音效

## <a name="objectives"></a>目標
在 HoloLens 2 教學課程的空間音訊模組的第二章中，您將會：
* 新增按鈕
* Spatialize 按鈕的 click 聲

## <a name="add-a-button"></a>新增按鈕
在 [ **專案** ] 窗格中，選取 [ **資產** ]，然後在搜尋列中輸入 "PressableButtonHoloLens2"：

![資產中的按鈕預製專案](images/spatial-audio/button-prefab-in-assets.png)

按鈕預製專案是以藍色圖示（而非白色圖示）表示的專案。 將名為 **PressableButtonHoloLens2** 的預製專案拖曳到 [ **階層] 窗格** 中。 在新按鈕的 [偵測 **器** ] 窗格中，將 [ **位置** ] 屬性設定為 (0、-0.4、2) ，以便在應用程式啟動時出現在使用者前面。 按鈕的 **轉換** 元件看起來會像這樣：

![按鈕轉換](images/spatial-audio/button-transform.png)

## <a name="spatialize-button-feedback"></a>Spatialize 按鈕意見反應
在此步驟中，您將 spatialize 按鈕的音訊意見反應。 如需相關的設計建議，請參閱 [空間音效設計](../../../design/spatial-sound-design.md)。 

您可以在 [ **音訊混音** 器] 窗格中，為音訊 **來源** 元件定義音訊播放的目的地，稱為 **混音器群組** 。 
* 使用 **視窗-> 音訊 > 音訊混音** 器，從功能表列開啟 [ **音訊混音** 器] 窗格
* 按一下 [ **Mixers** ] 旁邊的 [+]，以建立 **混音** 器。 新的混音器將包含稱為 **Master** 的預設 **群組** 。

您的 **混音** 器窗格現在看起來像這樣：

![具有第一個混音器的混音器面板](images/spatial-audio/mixer-panel-with-first-mixer.png)

> [!NOTE]
> 在 [第5章](unity-spatial-audio-ch5.md)啟用 [回條] 之前，混音器的音量計量不會顯示透過 Microsoft 空間定位器播放之音效的活動

按一下 [ **階層] 窗格中的 [** **PressableButtonHoloLens2** ]。 在 [偵測 **器** ] 窗格中：
1. 尋找 **音訊來源** 元件
2. 針對 [ **輸出** ] 屬性，按一下選取器並選擇混音器
3. 核取 [ **Spatialize** ] 核取方塊
4. 將 **空間 Blend** 滑杆移至 3d (1) 。

> [!NOTE]
> 在2019之前的 Unity 版本中，[Spatialize] 核取方塊位於 **音訊來源** 的 [偵測 **器** ] 窗格底部。

這些變更之後， **PressableButtonHoloLens2** 的 **音訊來源** 元件看起來會像這樣：

![按鈕音訊來源](images/spatial-audio/button-audio-source.png)

> [!NOTE]
> 如果您在未核取 [ **Spatialize** ] 核取方塊的情況下，將 **空間 Blend** 移至 1 (3d) ，Unity 將會使用其移動流覽空間定位器，而不是使用 hrtf 的 **Microsoft 空間定位器** 。

## <a name="adjust-the-volume-curve"></a>調整音量曲線
根據預設，Unity 會在從接聽程式更遠的情況下 attenuate hrtf 音效。 當此衰減套用至互動回饋音效時，介面可能會變得更難使用。

若要停用此衰減，請調整 **音量** 曲線。 在 **PressableButtonHoloLens2** 的 [偵測 **器** ] 窗格的 [ **音訊來源** ] 元件中，有一個稱為 **3d 音效設定** 的區段。 在該區段中：
1. 將 **Volume Rolloff** 屬性設定為線性
2. 拖曳 **音量** 曲線上的端點 (紅色曲線) 從 y 軸上的 ' 0 ' 到 ' 1 '
3. 若要將 **音量** 曲線的形狀調整為平面，請將白色曲線圖形控制項平行地拖曳至 X 軸

這些變更之後， **PressableButtonHoloLens2** **音訊來源** 屬性的 [ **3d 音效設定** ] 區段看起來會像這樣：

![按鈕3D 音效設定](images/spatial-audio/button-3d-sound-settings.png)

## <a name="next-steps"></a>後續步驟

在 HoloLens 2 或 Unity 編輯器中試用您的應用程式。 在應用程式中，您可以觸控按鈕，聽聽 hrtf 按鈕的互動音效。

在 Unity 編輯器中進行測試時，請按下空格鍵並以滾輪滾動，以啟動手動模擬。 如需詳細資訊，請參閱 [MRTK 檔](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene)。

> [!div class="nextstepaction"]
> [第3章](unity-spatial-audio-ch3.md)

