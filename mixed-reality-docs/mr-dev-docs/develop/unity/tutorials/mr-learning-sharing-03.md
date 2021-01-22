---
title: 連線多個使用者
description: 完成此課程，以了解如何連線 HoloLens 2 混合實境應用程式中的多個使用者。
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens, 多使用者功能, Photon, MRTK, 混合實境工具組, UWP, Azure 空間錨點
ms.localizationpriority: high
ms.openlocfilehash: 8db3c4b7ed65e657ba433110921d3b287323e3d1
ms.sourcegitcommit: 04927427226928bd9178da0049d4cef626a6b0bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/21/2021
ms.locfileid: "98669470"
---
# <a name="3-connecting-multiple-users"></a>3.連線多個使用者

在此教學課程中，您將了解如何在即時共用體驗中連線多個使用者。 在本教學課程結束時，您將能夠在多個裝置上執行應用程式，並讓每位使用者看到其他使用者虛擬人偶的即時移動狀態。

## <a name="objectives"></a>目標

* 了解如何在共用體驗中連線多個使用者

## <a name="preparing-the-scene"></a>準備場景

在本節中，您將藉由新增一些教學課程 Prefab 來準備場景。

在 [專案] 視窗中，瀏覽至 [資產]  >  [MRTK.Tutorials.MultiUserCapabilities]  >  [Prefabs] 資料夾，然後按一下下列 Prefab 並將其拖曳到 [階層] 視窗中，將其新增到您的場景中：

* **NetworkLobby** prefab
* **SharedPlayground** prefab

![已選取新增 NetworkLobby 和 SharedPlayground Prefabs 的 Unity](images/mr-learning-sharing/sharing-03-section1-step1-1.png)

在 [專案] 視窗中，瀏覽至 [資產] > [MRTK.Tutorials.AzureSpatialAnchors] > [Prefabs] 資料夾，然後按一下下列 Prefab 並將其拖曳至 [階層] 視窗中，將其新增到您的場景中：

* **DebugWindow** prefab

![已選取新增 DebugWindow Prefab 的 Unity](images/mr-learning-sharing/sharing-03-section1-step1-2.png)

## <a name="creating-the-user-prefab"></a>建立使用者預製物件

在本節中，您將建立一個預製物件來代表共用體驗中的使用者。

### <a name="1-create-and-configure-the-user"></a>1.建立並設定使用者

在 [階層] 視窗中，以滑鼠右鍵按一下空白區域，然後選取 [建立空物件] 以將空的物件新增至場景，並將物件命名為 **PhotonUser**，然後進行下列設定：

* 請確定變形的 **位置** 已設定為 X = 0、Y = 0、Z = 0：

![已選取新建立 PhotonUser 物件的 Unity](images/mr-learning-sharing/sharing-03-section2-step1-1.png)

在 [階層] 視窗中選取 [PhotonUser] 物件，在 [偵測器] 視窗中，使用 [新增元件] 按鈕，將 **Photon User (指令碼)** 元件新增至 PhotonUser 物件：

![已新增 Photon 使用者元件的 Unity](images/mr-learning-sharing/sharing-03-section2-step1-2.png)

在 [偵測器] 視窗中，使用 [新增元件] 按鈕，將 **Generic Net Sync (指令碼)** 元件新增至 PhotonUser 物件，並進行下列設定：

* 勾選 [是使用者] 核取方塊

![已新增和設定 Generic Net Sync 元件的 Unity](images/mr-learning-sharing/sharing-03-section2-step1-3.png)

在 [偵測器] 視窗中，使用 [新增元件] 按鈕，將 **Photon View (指令碼)** 元件新增至 PhotonUser 物件，並進行下列設定：

* 針對 [觀察到的元件] 欄位，請指派 **Generic Net Sync (指令碼)** 元件

![已新增和設定 Photon View 元件的 Unity](images/mr-learning-sharing/sharing-03-section2-step1-4.png)

### <a name="2-create-the-avatar"></a>2.建立虛擬人偶

在 [專案] 視窗中，瀏覽至 [資產]  >  [MRTK]  >  [SDK]  >  [StandardAssets]  >  [材質] 資料夾，以找出 MRTK 材質。

然後在 [階層] 視窗中，以滑鼠右鍵按一下 [PhotonUser] 物件，然後選取 [3D 物件]  >  [球體]，將球體物件建立為 PhotonUser 物件的子系，並依照下列方式進行設定：

* 請確定變形的 **位置** 已設定為 X = 0、Y = 0、Z = 0
* 將變形 **縮放** 變更為適當大小，例如 X = 0.15、Y = 0.15 和 Z = 0.15
* 對 [MeshRenderer] > [材質] > [元素 0] 欄位，指派 **MRTK_Standard_White** 材質

![具有新建立和已設定頭像球體的 Unity](images/mr-learning-sharing/sharing-03-section2-step2-1.png)

### <a name="3-create-the-prefab"></a>3.建立預製物件

在 [專案] 視窗中，瀏覽至 [資產] > [MRTK.Tutorials.MultiUserCapabilities] > [Resources] 資料夾：

![已選取 [資源] 資料夾的 Unity [專案] 視窗](images/mr-learning-sharing/sharing-03-section2-step3-1.png)

在仍選取 [資源] 資料夾的情況下，從 [階層] 視窗中 **按一下並拖曳** **PhotonUser** 物件到 [Resources] 資料夾，讓 PhotonUser 物件成為預製物件：

![已選取新建立 PhotonUser Prefab 的 Unity](images/mr-learning-sharing/sharing-03-section2-step3-2.png)

在 [階層] 視窗中，以滑鼠右鍵按一下 [PhotonUser] 物件，然後選取 [刪除]，從場景中將其移除：

![已從場景中移除新建立 PhotonUser Prefab 物件的 Unity](images/mr-learning-sharing/sharing-03-section2-step3-3.png)

## <a name="configuring-pun-to-instantiate-the-user-prefab"></a>設定 PUN 以具現化使用者預製物件

在本節中，您會將專案設定為使用上一節中建立的 PhotonUser 預製物件。

在 [專案] 視窗中，瀏覽至 [資產] > [MRTK.Tutorials.MultiUserCapabilities] > [Resources] 資料夾。

在 [階層] 視窗中，展開 **NetworkLobby** 物件，然後選取 **NetworkRoom** 子物件，接著在 [偵測器] 視窗中找出 **Photon Room (指令碼)** 元件，並依照下列方式進行設定：

* 在 [Photon 使用者預製物件] 欄位中，從 [Resources] 資料夾指派 **PhotonUser** 預製物件

![已部分設定 Photon Room 元件的 Unity](images/mr-learning-sharing/sharing-03-section3-step1-1.png)

## <a name="trying-the-experience-with-multiple-users"></a>嘗試多位使用者的體驗

如果您現在建立了 Unity 專案並將其部署至 HoloLens，則回到 Unity，並在應用程式於 HoloLens 上執行時進入遊戲模式，您會在移動頭部 (HoloLens) 時看到 HoloLens 使用者虛擬人偶跟著移動：

![動畫，顯示具有網路使用者的 Unity](images/mr-learning-sharing/sharing-03-section4-step1-1.gif)

> [!TIP]
> 如需有關如何建立 Unity 專案並將其部署至 HoloLens 2 的提醒，您可以參閱[對您的 HoloLens 2 建置應用程式](mr-learning-base-02.md#building-your-application-to-your-hololens-2)的指示。

> [!CAUTION]
> 應用程式必須連線到 Photon，因此請確定您的電腦/裝置已連線到網際網路。

## <a name="congratulations"></a>恭喜！

您已成功設定您的專案，可讓多個使用者連線到相同的體驗，並查看彼此的移動。 在下一個教學課程中，您將會實作功能，讓物件的移動也能在多個裝置之間共用。

> [!div class="nextstepaction"]
> [下一個教學課程：4.與多個使用者共用物件移動](mr-learning-sharing-04.md)
