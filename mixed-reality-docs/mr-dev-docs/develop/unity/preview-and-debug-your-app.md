---
title: 使用全像全像「遠端處理」和「播放」模式來預覽及偵測應用
description: 使用全像遠端和播放模式來預覽和偵測您的應用程式
author: vtieto
ms.author: v-vtieto
ms.date: 08/12/2021
ms.topic: article
keywords: openxr、unity、hololens、hololens 2、mixed reality、MRTK、Mixed Reality 工具組、增強的現實、虛擬實境、混合現實耳機、學習、教學課程、快速入門、攝影遠端、桌面、預覽、debug
ms.openlocfilehash: fe15d55037f09c47fe1e8a1dd996d0c69480f7b2
ms.sourcegitcommit: 820f2dfe98065298f6978a651f838de12620dd45
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/14/2021
ms.locfileid: "122203836"
---
# <a name="preview-and-debug-your-app-using-holographic-remoting-and-play-mode"></a>使用全像遠端和播放模式來預覽和偵測應用程式

本文說明適用于全像攝影的下列使用案例： 

- **您想要在開發過程中預覽和偵測應用程式**：您可以在電腦上的 Unity 編輯器中，以播放模式執行您的應用程式，並將體驗串流至您的 HoloLens。 這可讓您快速地對應用程式進行偵錯工具，而不需要建立及部署完整的專案。 我們會將這種類型的應用程式稱為全像 _遠端播放模式預覽應用程式_。 來自 HoloLens 的輸入（注視、手勢、語音和空間對應）會傳送至電腦，其中內容會以虛擬沉浸式視圖呈現。 然後，轉譯的框架會傳送至 HoloLens。 

若要深入瞭解全像攝影的[遠端處理功能，請參閱全](../platform-capabilities-and-apis/holographic-remoting-overview.md)像

請注意，如果[您想要讓電腦的資源開啟您的應用程式](use-pc-resources.md)，而不是依賴 HoloLens 的內部資源，您也可以使用全像的遠端處理。

## <a name="set-up-holographic-remoting"></a>設定全像遠端

若要使用全像的遠端功能，您必須從 HoloLens 上的 Microsoft Store 安裝全像[遠端播放機](../platform-capabilities-and-apis/holographic-remoting-player.md)應用程式。 如下所述，下載並執行應用程式之後，您會看到要連接的版本號碼和 IP 位址。 **您將需要2.4 版或更新版本，才能使用 OpenXR 外掛程式**。

全像遠端處理需要快速的電腦和 Wi-Fi 連接。 您可以在上面所連結的全像「全像遠端播放播放」文章中找到詳細資料。

![HoloLens 中執行的全像遠端播放播放程式螢幕擷取畫面](images/openxr-features-img-01.png)

[!INCLUDE[](includes/unity-play-mode.md)]

## <a name="see-also"></a>另請參閱
* [全像攝影遠端播放程式](../platform-capabilities-and-apis/holographic-remoting-player.md)
* [教學課程：開始使用 PC 全像遠端](tutorials/mr-learning-pc-holographic-remoting-01.md)
* [教學課程：建立全像遠端電腦應用程式](tutorials/mr-learning-pc-holographic-remoting-02.md)
