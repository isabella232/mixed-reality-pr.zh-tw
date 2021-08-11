---
title: 建立全像攝影遠端處理電腦應用程式
description: 完成此課程，以了解如何建立電腦應用程式，以遠端處理從您的電腦到 HoloLens 2 的混合實境體驗。
author: jessemcculloch
ms.author: v-vtieto
ms.date: 07/26/2021
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens, 電腦全像攝影遠端處理, Visual Studio
ms.localizationpriority: high
ms.openlocfilehash: d395801c20d95ee0fdddc144b4e28c841554fb5116f847574ec4a931d116026e
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2021
ms.locfileid: "115197921"
---
# <a name="2-creating-a-holographic-remoting-pc-application"></a>2.建立全像攝影遠端處理電腦應用程式

在本教學課程中，您將瞭解如何建立使用內建遠端的電腦應用程式，讓您可以將進行中的工作串流至 HoloLens 並加以查看，而不需要先建立它。

[瞭解全像攝影的基本概念。](../../platform-capabilities-and-apis/holographic-remoting-overview.md)

## <a name="objectives"></a>目標

* 設定適用於全像攝影遠端處理的 Unity
* 了解如何使用 Visual Studio 建立及部署應用程式
* 開發全像遠端應用程式並連接到 HoloLens

## <a name="configuring-the-capabilities"></a>設定功能

在 [ **Project 設定**] 視窗中，展開 [**發佈設定**]，向下滾動至 [功能] 區段，然後選取 [下一項功能] 核取方塊，除了現有的功能以外。

* 網際網路用戶端伺服器
* 私人網路用戶端伺服器

![啟用功能](images/mrlearning-pc-holographic-remoting/tutorial2-section0-step1-1.png)

[!INCLUDE[](includes/configuring-scene-for-holographic-remoting.md)]

## <a name="build-your-application-to-pc"></a>在電腦中建置應用程式

您的全像攝影遠端處理應用程式現在已準備好在電腦上建置。 請遵循下列步驟來進行這些變更，以將此應用程式建立到您的電腦上。

[!INCLUDE[](includes/build-your-application-to-pc.md)]

## <a name="testing-holographic-remoting-remote-application"></a>測試全像攝影遠端處理應用程式

若要將您的電腦應用程式連線到 HoloLens 2，請遵循下列程序：

### <a name="1-install-the-remoting-player-application-on-hololens-2-device"></a>1.在 HoloLens 2 裝置上安裝遠端播放程式應用程式

* 在您的 HoloLens 2 上，瀏覽市集應用程式並搜尋「遠端播放程式」。
* 選取 **遠端處理播放程式** 應用程式。
* 請點選 [安裝] 來下載並安裝應用程式。

### <a name="2-connect-the-holographic-remoting-pc-app-to-the-remoting-player"></a>2.將全像攝影遠端處理電腦應用程式連線到遠端播放程式

* 啟動 HoloLens 上的 **遠端播放程式**。
* 記下 HoloLens 的 **IP 位址**。 **遠端播放程式** 會在啟動時，將其顯示為全像投影。
* 在您的電腦上開啟全像攝影遠端處理電腦應用程式。
* 啟動應用程式之後，輸入 **IP 位址**，然後按一下 [連線] 按鈕以進行連線。

## <a name="congratulations"></a>恭喜！

在本教學課程中，您已了解如何建立全像攝影遠端處理應用程式，並在任何時間點連線 HoloLens 2，進而提供一種在混合實境中將 3D 內容視覺化的方式。 當 HoloLens 連線到全像攝影遠端處理電腦應用程式之後，您應該會看到混合實境體驗串流至您的 HoloLens 2 裝置。
