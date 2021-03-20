---
title: 使用眼球追蹤
description: 本課程說明如何在混合實境應用程式中透過混合實境工具組 (MRTK) 來使用眼球追蹤。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens, MRTK, 混合實境工具組, UWP, 眼球追蹤
ms.localizationpriority: high
ms.openlocfilehash: 08793622917ca977c51be56267d8710e5abb78e8
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "102237165"
---
# <a name="8-using-eye-tracking"></a>8.使用眼球追蹤

在本教學課程中，您將了解如何啟用 HoloLens 2 的眼球追蹤，並將眼球追蹤新增至物件，以在使用者查看物件時觸發動作。

> [!NOTE]
> 如果您也要將此專案部署到 HoloLens (第 1 代)，請注意，只有 HoloLens 2 支援眼球追蹤。

## <a name="objectives"></a>目標

* 了解如何啟用 HoleLens 2 的眼球追蹤
* 了解如何使用眼球追蹤來觸發動作

## <a name="ensuring-the-eye-gaze-input-capability-is-enabled"></a>確保已啟用「眼球注視輸入」功能

在 Unity 功能表中，選取 [混合實境工具組] > [公用程式] > [設定 Unity 專案] 以開啟 [MRTK 專案設定程式] 視窗，然後在 [UWP 功能] 區段中，確認 [啟用眼球注視輸入功能] 呈現灰色：

![Unity [MRTK 專案設定程式] 視窗](images/mr-learning-base/base-08-section1-step1-1.png)

> [!NOTE]
> 當您在本教學課程系列開頭設定 Unity 時，「注視輸入」功能應該在[套用 MRTK 專案設定程式設定](mr-learning-base-02.md#creating-and-configuring-the-scene)指示期間啟用。 不過如果未啟用，請確定您立即啟用。

## <a name="enabling-eye-based-gaze-in-the-gaze-provider"></a>在注視提供者中啟用眼球型追蹤

在 [階層] 視窗中，選取 **MixedRealityToolkit** 物件，然後在 [偵測器] 視窗中，選取 [MixedRealityToolkit] > [輸入] 索引標籤，並採取下列步驟：

* 複製 **DefaultHoloLens2InputSystemProfile** 並為其指定適當的名稱，例如 _GettingStarted_HoloLens2InputSystemProfile_
* 展開 [指標] 區段
* 複製 **DefaultMixedRealityPointerProfile** 並為其指定適當的名稱，例如 _GettingStarted_MixedRealityPointerProfile_
* 找出 [注視設定] 區段，然後勾選 [已啟用眼球追蹤] 核取方塊

![已套用新建立設定檔並已啟用眼球追蹤的 Unity MixedRealityToolkit 元件](images/mr-learning-base/base-08-section2-step1-1.png)

> [!TIP]
> 如需有關如何複製 MRTK 設定檔的提示，您可以參閱[設定 MRTK 設定檔](mr-learning-base-03.md)的指示。

## <a name="enabling-simulated-eye-tracking-for-the-unity-editor"></a>啟用 Unity 編輯器的模擬眼球追蹤

在 [階層] 視窗中，選取 **MixedRealityToolkit** 物件，在 [偵測器] 視窗中，瀏覽至 [輸入] 索引標籤，然後：

* 展開 [輸入資料提供者]  >  [輸入模擬服務] 區段
* 複製 **DefaultMixedRealityInputSimulationProfile** 並為其指定適當的名稱，例如 _GettingStarted_MixedRealityInputSimulationProfile_
* 找出 **眼睛的模擬** ，並將 **預設眼睛的眼睛模擬模式** 設定為 **相機轉寄軸**

![已選取 TextMeshPro 物件的 Unity](images/mr-learning-base/base-08-section3-step1-1.png)

## <a name="adding-eye-tracking-to-objects"></a>將眼球追蹤新增至物件

在 [階層] 視窗中，展開 [ **RoverExplorer**]  >  **按鈕**，然後選取三個子按鈕物件：

![已選取按鈕物件的 Unity](images/mr-learning-base/base-08-section4-step1-1.png)

當所有三個按鈕物件仍為選取狀態時，在 [偵測器] 視窗中，使用 [ **新增元件** ] 按鈕將 **EyeTrackingTarget** 元件新增至所有選取的物件：

![已選取 TextMeshPro 物件並已新增元件的 Unity](images/mr-learning-base/base-08-section4-step1-2.png)

在 [階層] 視窗中，展開 [ **RoverExplorer**  >  **按鈕**  >  **提示**  >  **SeeItSayItLabel**  >  **TextMeshPro**

然後，在 [階層] 視窗中選取 [ **提示** ] 按鈕物件，並設定 **EyeTrackingTarget** 元件，如下所示：

* 在 **On Look At Start ()** 事件區段中
  * 按一下小型 **+** 圖示，以新增另一個事件
  * 將  **TextMeshPro** 物件從 [ **提示** ] 按鈕指派給 [ **無 (物件)** ] 欄位
  * 從 [沒有函式] 下拉式清單中，選取 [TextMeshPro]  >  [float fontSize] 以在觸發事件時更新此屬性值
  * 將引數設定為 **0.06**，以將目前的字型大小增加 50% 成為 0.04
* 在 **On Look Away ()** 事件區段中
  * 按一下小型 **+** 圖示，以新增另一個事件
  * 將  **TextMeshPro** 物件從 [ **提示** ] 按鈕指派給 [ **無 (物件)** ] 欄位
  * 從 [沒有函式] 下拉式清單中，選取 [TextMeshPro]  >  [float fontSize] 以在觸發事件時更新此屬性值
  * 將引數設定為 **0.04**，以將字型大小重設回 0.04

![已選取提示 TextMeshPro 物件並已設定 EyeTrackingTarget 元件的 Unity](images/mr-learning-base/base-08-section4-step1-3.png)

針對 [**分解**] 和 [**重設**] 按鈕物件 **重複** 此步驟，以設定其他按鈕的眼睛追蹤。

如果您現在進入遊戲模式，然後在移動滑鼠時按住滑鼠右鍵，然後再移動滑鼠，直到看看看看看看它的其中一個按鈕時，您會看到文字字型大小增加50%，並在離開時重設回原始大小：

![具有注視點擊眼球追蹤目標 [分解] 按鈕標籤的 Unity 播放模式分割檢視](images/mr-learning-base/base-08-section4-step1-4.png)

## <a name="congratulations"></a>恭喜！

在本教學課程中，您將了解如何啟用 HoloLens 2 的眼球追蹤，以及如何將眼球追蹤新增至物件，以在使用者查看物件時觸發動作。

> [!div class="nextstepaction"]
> [下一個教學課程：9.使用語音命令](mr-learning-base-09.md)
