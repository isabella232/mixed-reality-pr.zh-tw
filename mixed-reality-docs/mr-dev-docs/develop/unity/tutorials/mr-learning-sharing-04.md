---
title: 與多個使用者共用物件移動
description: 完成此課程，以了解如何在 HoloLens 2 應用程式中與多個使用者共用物件移動。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens, 多使用者功能, Photon, MRTK, 混合實境工具組, UWP, Azure 空間錨點
ms.localizationpriority: high
ms.openlocfilehash: 4be0fc30b6d1b401bf137be4060704f54515ceb1
ms.sourcegitcommit: cf8df1720ddb8236207ab581bc149edcc76e6199
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/26/2021
ms.locfileid: "114702491"
---
# <a name="4-sharing-object-movements-with-multiple-users"></a>4.與多個使用者共用物件移動

在本教學課程中，您將了解如何共用物件的移動，讓共用體驗的所有參與者都可以共同作業及查看彼此的互動。

## <a name="objectives"></a>目標

* 設定專案來共用物件的移動
* 了解如何建立基本的多使用者共同作業應用程式

## <a name="preparing-the-scene"></a>準備場景

在本節中，您將藉由新增教學課程預製物件 (Prefab) 來準備場景。

在 [階層] 視窗中，展開 [ **MixedRealityPlayspace** ] 物件，並選取 [ **主要攝影機** ] 子物件，然後在 [偵測器] 視窗中，使用 [ **新增元件** ] 按鈕將 **AR 攝影機管理員 (腳本)** 元件新增至 **主要攝影機** 物件：

![Unity 與 AR 攝影機管理員元件部分設定](images/mr-learning-sharing/sharing-04-section1-step1-0.png)

在 [專案] 視窗中，瀏覽至 [資產] > [MRTK.Tutorials.MultiUserCapabilities] > [Prefabs] 資料夾，並將 **TableAnchor** 預製物件 (Prefab) 拖曳到階層視窗中的 **SharedPlayground** 物件上方，以將其作為 SharedPlayground 物件的子系來新增至您的場景：

![已選取新增 TableAnchor Prefab 的 Unity](images/mr-learning-sharing/sharing-04-section1-step1-1.png)

在 [階層] 視窗中，確定已展開 [ **MixedRealityPlayspace** ] 物件，並已選取 [ **TableAnchor** ] 物件。 將 **主要攝影機** 元件拖曳至 **TableAnchor** 之 **AR 會話來源** 元件的 **相機** 欄位：

![已設定 AR 會話原始的 Unity 指派](images/mr-learning-sharing/sharing-04-section1-step1-2.png)

## <a name="configuring-pun-to-instantiate-the-objects"></a>設定 PUN 以具現化物件

在本節中，您會將專案設定為使用在[使用者入門教學課程](mr-learning-base-01.md)中建立的 Rover Explorer 體驗，並定義其將會具現化的位置。

在 [專案] 視窗中，瀏覽至 [資產] > [MRTK.Tutorials.MultiUserCapabilities] > [Resources] 資料夾。

在 [階層] 視窗中，展開 **NetworkLobby** 物件，然後選取 **NetworkRoom** 子物件，接著在 [偵測器] 視窗中找出 **Photon Room (指令碼)** 元件，並依照下列方式進行設定：

* 在 [Rover Explorer Prefab] 欄位中，從 [資源] 資料夾指派 **RoverExplorer_Complete_Variant** Prefab

![已部分設定 Photon Room 元件的 Unity](images/mr-learning-sharing/sharing-04-section2-step1-1.png)

在仍選取 **NetworkRoom** 子物件的情況下，在 [階層] 視窗中，展開 **TableAnchor** 物件，然後在 [偵測器] 視窗中找出 **Photon Room (指令碼)** 元件，並依照下列方式進行設定：

* 在 [Rover Explorer 位置] 欄位中，從 [階層] 視窗指派 TableAnchor > **Table** 子物件

![已設定 Photon Room 元件的 Unity](images/mr-learning-sharing/sharing-04-section2-step1-2.png)

## <a name="trying-the-experience-with-shared-object-movement"></a>嘗試共用物件移動的體驗

如果您現在建立了 Unity 專案並將其部署至 HoloLens，然後回到 Unity，並在應用程式於 HoloLens 上執行時，按下 [開始遊戲] 按鈕進入遊戲模式，當您在 HoloLens 中移動物件時，您將會看到物件在 Unity 中移動：

![動畫，顯示具有網路物件的 Unity](images/mr-learning-sharing/sharing-04-section3-step1-1.gif)

## <a name="congratulations"></a>恭喜！

您已成功設定專案來同步物件移動，因此使用者可以在其他使用者移動物件時，看到物件移動。 在下一個教學課程中，您將會實作功能來配合實體世界中的體驗。 這可確保使用者在實際的實體位置看到彼此，因此物件會出現在相同實體位置，並且針對所有使用者旋轉。

> [!div class="nextstepaction"]
> [下一個教學課程：5.將 Azure Spatial Anchors 整合到共用體驗](mr-learning-sharing-05.md)
