---
title: 預覽您的工作與全像攝影遠端
description: 在播放模式中使用全像的遠端處理功能，在不部署應用程式的情況下預覽裝置上的應用程式變更。
author: keveleigh
ms.author: v-vtieto
ms.date: 07/26/2021
ms.topic: article
keywords: Unity、遠端、全像全像遠端、全像遠端播放機、HoloLens、混合現實耳機、windows mixed reality 耳機、虛擬實境耳機、unity play 模式
ms.openlocfilehash: cd9dca9d1ddf17b78e8c317fa3a58093c9b5837de379510148c6e645b31120ca
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2021
ms.locfileid: "115226230"
---
# <a name="preview-your-work-with-holographic-remoting"></a>預覽您的工作與全像攝影遠端

您可以使用內建的遠端功能，即時將全息內容串流至您的 HoloLens 2。 這是快速偵測應用程式，而不需要建立及部署完整專案的絕佳方式。 

處理 Unity 專案的快速方式是使用「播放模式」，這會在本機電腦上的 Unity 編輯器中執行您的應用程式。 Unity 使用全像的遠端處理功能，提供快速的方式，在實際的 HoloLens 裝置上預覽內容。 [播放] 模式也可以與連接至開發電腦的 Windows Mixed Reality 耳機一起使用。

## <a name="holographic-remoting-setup"></a>全像遠端設定

1. 首先，您必須從 HoloLens 2 上的 Microsoft Store 安裝全像[遠端播放機應用程式](https://www.microsoft.com/store/productId/9NBLGGH4SV40)
2. 在 HoloLens 2 上執行全像遠端播放播放程式應用程式，您會看到要連接的版本號碼和 IP 位址
    * 您將需要2.4 或更新版本才能使用 OpenXR 外掛程式

    ![HoloLens 中執行的全像遠端播放播放程式螢幕擷取畫面](images/openxr-features-img-01.png)

## <a name="unity-play-mode-with-holographic-remoting"></a>使用全像攝影遠端的 Unity 播放模式

使用全像全像的遠端功能，您可以在電腦上的 Unity 編輯器中執行應用程式時，在 HoloLens 上體驗您的應用程式。 注視、手勢、語音和空間對應輸入會從您的 HoloLens 傳送到您的電腦。 轉譯後的框架接著會傳回 HoloLens。 這是快速偵測應用程式，而不需要建立及部署完整專案的絕佳方式。

[!INCLUDE[](includes/unity-play-mode.md)]

全像遠端處理需要快速的電腦和 Wi-Fi 連接。 您可以在全像是「全像 [遠端播放機](../platform-capabilities-and-apis/holographic-remoting-player.md) 」檔中找到更多詳細資料。

為了獲得最佳結果，請確定您的應用程式已正確設定 [焦點點](focus-point-in-unity.md)。 這可協助全像攝影的遠端處理，以最適合您的場景來調整您的無線連線延遲。

## <a name="see-also"></a>另請參閱

* [全像攝影遠端播放程式](../platform-capabilities-and-apis/holographic-remoting-player.md)
