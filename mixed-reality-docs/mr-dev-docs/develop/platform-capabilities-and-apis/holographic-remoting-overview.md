---
title: 全像遠端處理總覽
description: 瞭解什麼是全像的遠端處理，以及它如何讓您的開發程式受益。
author: hferrone
ms.author: v-vtieto
ms.date: 07/26/2021
ms.topic: article
keywords: openxr、unity、hololens、hololens 2、mixed reality、MRTK、Mixed Reality 工具組、增強的現實、虛擬實境、混合現實耳機、學習、教學課程、快速入門、攝影遠端、桌面、預覽
ms.openlocfilehash: 6eb3b9e9fe8811ab4666ef1beda0e48668bedbe6
ms.sourcegitcommit: 9831b89a1641ba1b5df14419ee2a4f29d3fa2d64
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/29/2021
ms.locfileid: "114757392"
---
# <a name="holographic-remoting-overview"></a>全像遠端處理總覽

當您將全息轉譯的支援新增至您的電腦應用程式或遊戲時，可讓應用程式即時將全像攝影內容串流至您的 HoloLens 2。 這是快速偵測應用程式，而不需要建立及部署完整專案的絕佳方式。 「注視」、「手勢」、「聲音」和「空間對應」輸入會從您的 HoloLens 2 傳送到您的電腦，使用電腦的較大系統資源將內容轉譯為虛擬的沉浸式視圖，然後轉譯後的框架會傳回您的 HoloLens 2。 Windows Mixed Reality 沉浸式耳機也有提供全像的遠端處理功能。

您可以透過 NuGet 套件，透過您的桌面或 UWP 應用程式新增全像的遠端處理功能，並使用標準 wi-fi 來建立連接。 需要額外的程式碼，以處理連接並以沉浸式視圖呈現。 一般的遠端連線的延遲將會降到50毫秒。 您的裝置會使用可即時報告延遲的「播放程式」應用程式，來顯示已串流處理的內容。

如果您是 Unity 開發人員，也可以在 Unity 編輯器中以播放模式執行您的應用程式，以使用「全像」遠端功能。

## <a name="see-also"></a>另請參閱
* [全像攝影遠端播放程式](holographic-remoting-player.md)
* [使用 Windows Mixed Reality api 撰寫全像遠端執行遠端應用程式](holographic-remoting-create-remote-wmr.md)
* [使用 OpenXR Api 撰寫全像遠端執行遠端應用程式](holographic-remoting-create-remote-openxr.md)
* [教學課程：開始使用 PC 全像遠端](../unity/tutorials/mr-learning-pc-holographic-remoting-01.md)
* [教學課程：建立全像遠端電腦應用程式](../unity/tutorials/mr-learning-pc-holographic-remoting-02.md)
