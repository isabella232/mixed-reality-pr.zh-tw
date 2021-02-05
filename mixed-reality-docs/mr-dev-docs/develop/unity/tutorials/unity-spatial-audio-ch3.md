---
title: 空間音訊教學課程-3。 從影片空間化音訊
description: 將影片資產匯入您的 Unity 專案，並從影片 spatialize 音訊。
author: kegodin
ms.author: v-hferrone
ms.date: 02/05/2021
ms.topic: article
keywords: 混合現實、unity、教學課程、hololens2、空間音訊、MRTK、混合現實工具組、UWP、Windows 10、HRTF、前端相關的傳送功能、回音、Microsoft 空間定位器、影片匯入、影片播放工具
ms.openlocfilehash: 876918c3e886fae6cd2066d84c55a6e158e4c773
ms.sourcegitcommit: 68140e9ce84e69a99c2b3d970c7b8f2927a7fc93
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/05/2021
ms.locfileid: "99590050"
---
# <a name="3-spatializing-audio-from-a-video"></a>3.從影片空間化音訊

## <a name="overview"></a>概觀

在本教學課程中，您將瞭解如何從影片來源 spatialize 音訊，並在 unity 編輯器中測試，並 HoloLens 2。

## <a name="objectives"></a>目標

* 匯入影片並新增影片播放影片
* 播放影片到四邊形
* 將音訊從影片路由傳送至四邊形，並 spatialize 音訊

## <a name="import-a-video-and-add-a-video-player-to-the-scene"></a>匯入影片並將影片播放機新增至場景

在本教學課程中，您可以使用「空間音訊」範例專案中的 [這段影片](https://github.com/microsoft/spatialaudio-unity/blob/develop/Samples/MicrosoftSpatializerSample/Assets/Microsoft%20HoloLens%20-%20Spatial%20Sound-PTPvx7mDon4.mp4?raw=true) 。

將影片匯入 unity 專案。 在 Unity 功能表中，選取 [**資產** 匯  >  **入新增** 資產匯 
 ![ 入資產]](images/spatial-audio/spatial-audio-03-section1-step1-1.png)

在 [匯 **入新資產** ] 視窗中，選取您下載的 **Microsoft HoloLens 空間音效 PTPvx7mDon4** 檔案，然後按一下 [ **開啟** ] 按鈕，將資產匯入至專案中：

![選取資產](images/spatial-audio/spatial-audio-03-section1-step1-2.png)

調整影片剪輯的品質設定，可確保在 HoloLens 2 上進行順暢的播放。 在 [ **專案** ] 視窗和影片檔案的 [偵測器] 視窗中選取影片檔案，覆 **寫** **Windows Store 應用程式** 的設定，以及：

* 啟用 **轉碼**
* 將 **編解碼器** 設定為 H264
* 將 **位元速率模式** 設定為低
* 將 **空間品質** 設定為中等空間品質

進行這些調整之後，請按一下 [套用] 來變更影片剪輯上的品質設定。

![影片屬性變更](images/spatial-audio/spatial-audio-03-section1-step1-3.png)

以滑鼠右鍵按一下階層，然後選取 [**視頻**  >  **影片播放** 影片] 以新增影片播放元件。

![新增影片播放影片](images/spatial-audio/spatial-audio-03-section1-step1-4.png)

## <a name="play-video-onto-a-quadrangle"></a>播放影片至四邊形

**影片播放影片** 物件需要有紋理的遊戲物件才能轉譯影片。

以滑鼠右鍵按一下階層，選取 [ **3d 物件**  >  **四** 個] 以建立四個並設定其 **轉換** 元件，如下所示：

* **位置**： X = 0、Y = 0、Z = 2
* **旋轉**：X = 0、Y = 0、Z = 0
* **Scale**： X = 1.28、Y = 0.72、Z = 1

![新增四個](images/spatial-audio/spatial-audio-03-section2-step1-1.png)

現在您需要將 **四** 段影片的材質材質，請在 [**專案**] 視窗中，以滑鼠右鍵按一下並選擇 [**建立** 轉譯  >  **材質**] 來建立轉譯材質元件、為轉譯紋理輸入適當的名稱，例如，_空間音訊材質_：

![建立呈現材質](images/spatial-audio/spatial-audio-03-section2-step1-2.png)

選取 [轉譯 **材質** ]，然後在 [偵測器] 視窗中設定 [ **大小** ] 屬性，以符合影片的1280x720 原生解析度。 然後，若要確保 HoloLens 2 的良好轉譯效能，請將 [ **深度緩衝區** ] 屬性設定為 **至少16個位的深度**。

![轉譯材質屬性](images/spatial-audio/spatial-audio-03-section2-step1-3.png)

接下來，使用已建立的轉譯材質 **空間音訊紋理** 作為 **四** 個的材質：

1. 將 [ **空間音訊材質** ] 從 [ **專案** ] 視窗拖曳至階層中的 [ **四** 個]，以將轉譯紋理新增至 [四]
2. 若要確保 HoloLens 2 的良好效能，請選取階層中的 [四]，然後在著色器的 [偵測器] 視窗中選取 [**混合現實工具** 組  >  **標準** 著色器]

![四材質屬性](images/spatial-audio/spatial-audio-03-section2-step1-4.png)

若要設定 **影片播放** 和轉譯 **材質** 來播放影片剪輯，請選取 **階層和偵測****器** 視窗中的 **影片播放機**。

* 將 **影片剪輯** 屬性設定為下載的影片檔案 ' Microsoft HoloLens-空間音效-PTPvx7mDon4 '
* 核取 [ **迴圈** ] 核取方塊
* 將 **目標材質** 設定為新的轉譯材質 **空間音訊紋理**

![影片播放影片屬性](images/spatial-audio/spatial-audio-03-section2-step1-5.png)

## <a name="spatialize-the-audio-from-the-video"></a>從影片 Spatialize 音訊

在 [階層] 視窗中，選取 [ **四** 個物件]，然後在 [偵測器] 視窗中，使用 [ **新增元件** ] 按鈕來新增 **音訊來源** ，您將從影片將音訊傳送至該來源。

在 **音訊來源** 中：

* 將 **輸出** 設定為 **空間音訊混音** 器
* 核取 [ **Spatialize** ] 方塊
* 將 **空間 Blend** 滑杆移至 1 (3d) 

![四音訊來源檢查](images/spatial-audio/spatial-audio-03-section3-step1-1.png)

若要設定影片播放影片將其音訊路由傳送到 **音訊來源**，請在 [階層] 視窗中選取 **影片播放機** ，然後在偵測器中的 [影片播放流程] 物件執行下列變更。

* 將 **音訊輸出模式** 設定為 **音訊來源**
* 將 [**音訊來源**] 屬性設定為 [**四**]

![影片播放影片設定音訊來源](images/spatial-audio/spatial-audio-03-section3-step1-2.png)

> [!TIP]
> 如需有關如何建立 Unity 專案並將其部署至 HoloLens 2 的提醒，您可以參閱[對您的 HoloLens 2 建置應用程式](mr-learning-base-02.md#building-your-application-to-your-hololens-2)的指示。

## <a name="congratulations"></a>恭喜！

在本教學課程中，您已瞭解如何從影片來源 spatialize 音訊，並在 HoloLens 2 或 Unity 編輯器中試用您的應用程式。 您將會看到並聆聽影片，而影片中的音訊 hrtf。

在下一個教學課程中，您將瞭解如何在執行時間啟用和停用 spatialization

> [!div class="nextstepaction"]
> [下一個教學課程： 4. 在執行時間啟用和停用 spatialization](unity-spatial-audio-ch4.md)
