---
title: 空間音訊教學課程-2。 空間化按鈕互動音效
description: 將按鈕加入至您的專案，並 spatialize 按鈕互動音效。
author: kegodin
ms.author: v-hferrone
ms.date: 02/05/2021
ms.topic: article
keywords: 混合的現實、unity、教學課程、hololens2、空間音訊、MRTK、混合現實工具組、UWP、Windows 10、HRTF、head 相關的傳送函式、回音、Microsoft 空間定位器、prefabs、音量曲線
ms.openlocfilehash: f3f2faf8220eaebcc674bcf02a45d99d58169076
ms.sourcegitcommit: 4a6c26615d52776bdc4faab70391592092a471fc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2021
ms.locfileid: "110712799"
---
# <a name="2-spatializing-button-interaction-sounds"></a>2.空間化按鈕互動音效

## <a name="overview"></a>概觀

在本教學課程中，您將學習如何 spatialize 按鈕互動音效，以及瞭解如何使用音訊剪輯來測試 hrtf 按鈕互動。  

## <a name="objectives"></a>目標

* 新增並 Spatialize 按鈕的 click 聲

## <a name="add-a-button"></a>新增按鈕

若要加入按鈕預製專案，請在 [ **專案** ] 視窗中選取 [ **封裝** ]，然後在搜尋列中輸入 "PressableButtonHoloLens2"。

![資產中的按鈕預製專案](images/spatial-audio/spatial-audio-02-section1-step1-1.PNG)

按鈕預製專案是以藍色圖示表示的專案。 按一下 [ **PressableButtonHoloLens2** ] 預製專案，並將其拖曳到階層中。 在仍選取 **PressableButtonHoloLens2** 物件的情況下，在 [偵測器] 視窗中設定 **轉換** 元件，如下所示：

* **Position**： X = 0，Y =-0.4，Z = 2
* **旋轉**：X = 0、Y = 0、Z = 0
* **縮放**：X = 1、Y = 1、Z = 1

![按鈕轉換](images/spatial-audio/spatial-audio-02-section1-step1-2.PNG)

若要將焦點放在場景中的物件上，您可以按兩下 **PressableButtonHoloLens2** 物件，然後再稍微放大：

## <a name="spatialize-button-feedback"></a>Spatialize 按鈕意見反應

在此步驟中，您將 spatialize 按鈕的音訊意見反應。 如需相關的設計建議，請參閱 [空間音效設計](../../../design/spatial-sound-design.md)。

在 [**音訊混音** 器] 視窗中，您將為音訊 **來源** 元件的音訊播放定義稱為 **混音器群組** 的目的地。

若要開啟 [**音訊混音** 器] 視窗，請在 Unity 功能表中，選取 [**視窗**  >  **音訊**  >  **音訊混音** 器： ![ 開啟音訊混音器] 視窗](images/spatial-audio/spatial-audio-02-section2-step1-1.PNG)

 按一下 [ **Mixers** ] 旁邊的 [+]，並輸入適當的混音名稱（例如 _空間音訊混音_ 器）來建立 **混音** 器。 新的混音器將包含稱為 **Master** 的預設 **群組**。

![具有第一個混音器的混音器面板](images/spatial-audio/spatial-audio-02-section2-step1-2.PNG)

> [!NOTE]
> 在第5章啟用回條之後 [：使用回音將距離新增至空間音訊](unity-spatial-audio-ch5.md)，混音器的音量計量不會顯示透過 Microsoft 空間定位器播放之音效的活動

在 [階層] 視窗中，選取 **PressableButtonHoloLens2** ，然後在 [偵測器] 視窗中尋找 **音訊來源** 元件，並設定音訊來源元件，如下所示：

1. 針對 [ **輸出** ] 屬性，按一下選取器，然後選擇您建立的 **混音** 器。
2. 核取 [ **Spatialize** ] 核取方塊。
3. 將 **空間 Blend** 滑杆移至 3d (1) 。

![按鈕音訊來源](images/spatial-audio/spatial-audio-02-section2-step1-3.PNG)

> [!NOTE]
> 如果您在未核取 [ **Spatialize** ] 核取方塊的情況下，將 **空間 Blend** 移至 1 (3d) ，Unity 將會使用其移動流覽空間定位器，而不是使用 hrtf 的 **Microsoft 空間定位器**。

## <a name="adjust-the-volume-curve"></a>調整音量曲線

根據預設，Unity 會在從接聽程式更遠的情況下 attenuate hrtf 音效。 當此衰減套用至互動回饋音效時，介面可能會變得更難使用。

若要停用此衰減，您需要調整 **音訊來源** 元件中的 **音量** 曲線。

在 [階層] 視窗中，選取 [ **PressableButtonHoloLens2** ]，然後在 [偵測器] 視窗中流覽至 [**音訊來源**  >  **3d 音效] 設定**，並設定如下：

1. 將 **Volume Rolloff** 屬性設定為線性 Rolloff
2. 拖曳 **音量** 曲線上的端點 (紅色曲線) 從 y 軸上的 ' 0 ' 到 ' 1 '
3. 若要將 **音量** 曲線的形狀調整為平面，請將白色曲線圖形控制項平行地拖曳至 X 軸

![按鈕3D 音效設定](images/spatial-audio/spatial-audio-02-section3-step1-1.PNG)

## <a name="testing-the-spatialize-audio"></a>測試 spatialize 音訊

若要在 unity 編輯器中測試 spatialize 音訊，您必須在 [**音訊來源** 元件] 中新增音訊剪輯，並在 **PressableButtonHoloLens2** 物件上簽入 **迴圈** 選項。

在 [播放] 模式中，將 **PressableButtonHoloLens2** 物件從左至右移動到右邊，並與您的工作站上未啟用空間音訊進行比較。 您也可以變更用於測試的音訊來源設定：

* 將 **空間 Blend** 屬性移至 0-1 (2d 非 Hrtf 和 3d hrtf 音效) 
* 檢查和取消選取 **Spatialize** 屬性

試用 HoloLens 2 上的應用程式。 在應用程式中，您可以按一下按鈕，聽聽 hrtf 按鈕的互動音效。

> [!TIP]
> 如需有關如何建立 Unity 專案並將其部署至 HoloLens 2 的提醒，您可以參閱[對您的 HoloLens 2 建置應用程式](mr-learning-base-02.md#building-your-application-to-your-hololens-2)的指示。

## <a name="congratulations"></a>恭喜！

在本教學課程中，您已學會 spatialize 按鈕互動音效，並使用音訊剪輯來測試 hrtf 按鈕互動。 在下一個教學課程中，您將瞭解如何從影片來源 spatialize 音訊。

> [!div class="nextstepaction"]
> [下一個教學課程： 3. 從影片 Spatializing 音訊](unity-spatial-audio-ch3.md)
