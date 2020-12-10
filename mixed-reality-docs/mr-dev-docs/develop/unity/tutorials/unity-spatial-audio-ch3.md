---
title: 空間音訊教學課程-3。 從影片空間化音訊
description: 將影片資產匯入您的 Unity 專案，並從影片 spatialize 音訊。
author: kegodin
ms.author: v-hferrone
ms.date: 12/01/2019
ms.topic: article
keywords: 混合現實、unity、教學課程、hololens2、空間音訊、MRTK、混合現實工具組、UWP、Windows 10、HRTF、前端相關的傳送功能、回音、Microsoft 空間定位器、影片匯入、影片播放工具
ms.openlocfilehash: 46f2f88be6613096a835f04e826b776c32c1b8c2
ms.sourcegitcommit: fbeff51cae92add88d2b960c9b7bbfb04d5a0291
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "97002623"
---
# <a name="spatializing-audio-from-a-video"></a>從影片空間化音訊
在 HoloLens 2 Unity 教學課程的「空間音訊」課程模組的第3章中，您將會：
* 匯入影片並新增影片播放影片
* 播放影片到四邊形
* 將音訊從影片路由傳送至四邊形，並 spatialize 音訊

## <a name="import-a-video-and-add-a-video-player"></a>匯入影片並新增影片播放影片

將影片檔案拖曳至 Unity 專案的 [ **專案** ] 窗格中。 您可以從空間音訊範例專案使用 [這段影片](https://github.com/microsoft/spatialaudio-unity/blob/develop/Samples/MicrosoftSpatializerSample/Assets/Microsoft%20HoloLens%20-%20Spatial%20Sound-PTPvx7mDon4.mp4?raw=true) 。

![具有影片的資產資料夾](images/spatial-audio/assets-folder-with-video.png)

調整影片剪輯的品質設定，可確保在 HoloLens 2 上進行順暢的播放。 按一下 [ **專案** ] 窗格中的影片檔案。 然後，在影片檔案的 [偵測 **器** ] 窗格中，覆寫 Windows Store 應用程式的設定，以及：
* 啟用 **轉碼**
* 將 **編解碼器** 設定為 H264
* 將 **位元速率模式** 設定為低
* 將 **空間品質** 設定為中等空間品質

這些調整之後，影片檔案的偵測 **器** 窗格看起來會像這樣：

![影片屬性窗格](images/spatial-audio/video-property-pane.png)

接下來，以滑鼠右鍵 **按一下 [階層**] 窗格，然後 **選擇 [** **影片-> 影片播放程式**]，將 **影片播放** 程式物件新增至階層：

![階層中的影片播放影片](images/spatial-audio/video-player-in-hierarchy.png)

## <a name="play-video-onto-a-quadrangle"></a>播放影片至四邊形
**影片播放影片** 物件需要有紋理的遊戲物件來呈現影片。 首先 **，以滑鼠** 按右鍵階層 **窗格，然後選擇 [** **3d 物件-> 四** 個：

![將四個階層新增至階層](images/spatial-audio/add-quad-to-hierarchy.png)

為了確保在應用程式啟動時出現在使用者前面的 **四** 個部分，請將 **四** 個的 [**位置**] 屬性設定為 [ (0、0、2) ]，並將 [**小** 數位數] 屬性設定為 (1.28、0.72、1) 。 這些變更之後，**四** 個 [**檢查**] 窗格上的 [**轉換**] 元件看起來會像這樣：

![四轉換](images/spatial-audio/quad-transform.png)

若要使用影片來材質 **四** 段影片，請建立新的轉譯 **紋理**。 在 [ **專案** ] 窗格中，以滑鼠右鍵按一下並選擇 [ **建立-> 呈現材質**：

![建立呈現材質](images/spatial-audio/create-render-texture.png)

在轉譯 **紋理** 的 [偵測 **器**] 窗格中，將 [**大小**] 屬性設定為符合影片的1280x720 原生解析度。 然後，若要確保 HoloLens 2 的良好轉譯效能，請將 [ **深度緩衝區** ] 屬性設定為 **至少16個位的深度**。 這些設定之後，轉譯 **紋理** 的偵測 **器** 窗格看起來會像這樣：

![轉譯材質屬性](images/spatial-audio/render-texture-properties.png)

接下來，使用新的轉譯 **紋理** 作為 **四** 個的材質：
1. 將 [轉譯 **材質**] 從 [**專案**] 窗格拖曳到階層 **中的 [** **四** 個]
2. 若要確保 HoloLens 2 的良好效能，請在 **四** 個 [偵測 **器**] 窗格中，選取 [**混合現實工具組標準著色器**]。

使用這些設定時，**四** 個 [**檢查**] 窗格上的 **材質** 元件看起來會像這樣：

![四材質屬性](images/spatial-audio/quad-texture-properties.png)

若要設定新的 **影片播放** 程式並轉譯 **材質** 來播放影片剪輯，請開啟 **影片播放** 程式的 [偵測 **器**] 窗格，然後：
* 將 **影片剪輯** 屬性設定為您的影片檔案
* 核取 [ **迴圈** ] 核取方塊
* 將 **目標材質** 設定為新的呈現材質

**影片播放** 程式的 [偵測 **器**] 窗格現在看起來會像這樣：

![影片播放影片屬性](images/spatial-audio/video-player-properties.png)

## <a name="spatialize-the-audio-from-the-video"></a>從影片 Spatialize 音訊
在 **四** 個的 [偵測 **器**] 窗格中，建立 **音訊來源**，您將從影片將音訊傳送至該來源：
* 按一下窗格底部的 [ **新增元件** ]
* 新增 **音訊來源**

然後，在 **音訊來源**：
* 將 **輸出** 設定至混音器
* 核取 [ **Spatialize** ] 方塊
* 將 **空間 Blend** 滑杆移至 1 (3d) 

這些變更之後，**四個四** 個 [**檢查**] 窗格上的 [**音訊來源**] 元件看起來會像這樣：

![四音訊來源檢查](images/spatial-audio/quad-audio-source-inspector.png)

若要設定 **影片播放** 程式以將其音訊傳送至 **四** 個 **音訊來源**，請開啟 **影片播放** 程式的 [偵測 **器**] 窗格，然後：
* 將 **音訊輸出模式** 設定為 [音訊來源]
* 將 [ **音訊來源** ] 屬性設定為 [四]

這些變更之後，**影片播放** 程式的 [偵測 **器**] 窗格看起來會像這樣：

![影片播放影片設定音訊來源](images/spatial-audio/video-player-set-audio-source.png)

## <a name="next-steps"></a>後續步驟
在 HoloLens 2 或 Unity 編輯器中試用您的應用程式。 您將會看到並聆聽影片，而影片中的音訊將會 hrtf。

> [!div class="nextstepaction"]
> [第4章](unity-spatial-audio-ch4.md) 

