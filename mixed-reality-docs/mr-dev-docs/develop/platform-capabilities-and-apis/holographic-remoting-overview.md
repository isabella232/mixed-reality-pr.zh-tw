---
title: 全像遠端處理總覽
description: 瞭解什麼是全像攝影的遠端處理，以及它如何受益于您的開發流程。
author: hferrone
ms.author: v-vtieto
ms.date: 08/12/2021
ms.topic: article
keywords: openxr、unity、hololens、hololens 2、mixed reality、MRTK、Mixed Reality 工具組、增強的現實、虛擬實境、混合現實耳機、學習、教學課程、快速入門、攝影遠端、桌面、預覽
ms.openlocfilehash: 52b69f942797b1f0a6a9bcc5276a49d4d2cebba5
ms.sourcegitcommit: 820f2dfe98065298f6978a651f838de12620dd45
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/14/2021
ms.locfileid: "122184599"
---
# <a name="holographic-remoting-overview"></a>全像遠端處理總覽

您可以使用內建的遠端功能，即時將全息內容串流至您的 HoloLens。 這有兩個主要用途，請務必瞭解差異：

1.  (Unity 或 Unreal) ：**您想要在開發過程中預覽和偵測應用程式**：您可以在電腦上的 Unity 編輯器中，以播放模式執行您的應用程式，並將體驗串流至您的 HoloLens。 這可讓您快速地對應用程式進行偵錯工具，而不需要建立及部署完整的專案。 我們會將這種類型的應用程式稱為全像 _遠端播放模式預覽應用程式_。

    - [深入瞭解如何在 Unity 中預覽和偵錯工具](../unity/preview-and-debug-your-app.md)

    - [深入瞭解如何在 Unreal 中預覽和偵測應用程式](../unreal/unreal-streaming.md)

1.  (Unity、Unreal 或 c + +) ：**您希望電腦的資源能夠為您的應用程式提供強大的功能，而不需依賴 HoloLens 的內部資源**：您可以建立並建立具有全像全像的應用程式的應用程式。 使用者會在 HoloLens 上體驗應用程式，但應用程式實際上是在電腦上執行，讓它能夠利用電腦的功能更強大的資源。 如果您的應用程式具有高解析度的資產或模型，而且您不希望畫面播放速率受到影響，這會特別有用。 我們將這種類型的應用程式稱為全像遠端 _遠端應用程式_。

    - [深入瞭解如何在 Unity 中使用 PC 資源](../unity/use-pc-resources.md)

    - [深入瞭解如何在 Unreal 中使用 PC 資源](../unreal/unreal-streaming.md)

    - [使用 Windows Mixed Reality api (c + + 撰寫全像遠端遠端應用程式) ](holographic-remoting-create-remote-wmr.md)

    - [使用 OpenXR Api (c + +) 撰寫全像遠端遠端應用程式 ](holographic-remoting-create-remote-openxr.md)

無論是哪一種情況，HoloLens 的輸入（像是注視、手勢、語音和空間對應）都會傳送至電腦，內容會以虛擬沉浸式視圖轉譯，然後轉譯後的框架會傳送至 HoloLens。 

## <a name="see-also"></a>另請參閱

* [全像攝影遠端播放程式](holographic-remoting-player.md)
* [教學課程：開始使用 PC 全像遠端](../unity/tutorials/mr-learning-pc-holographic-remoting-01.md)
* [教學課程：建立全像遠端電腦應用程式](../unity/tutorials/mr-learning-pc-holographic-remoting-02.md)
