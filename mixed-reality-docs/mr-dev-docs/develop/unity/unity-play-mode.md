---
title: Unity 播放模式
description: 瞭解如何在 Unity 編輯器中使用播放模式，以預覽裝置上的應用程式變更，而不需要部署應用程式。
author: keveleigh
ms.author: kurtie
ms.date: 05/21/2021
ms.topic: article
keywords: Unity、遠端處理、全像全像攝影、全像遠端播放機、HoloLens、混合現實耳機、windows mixed reality 耳機、虛擬實境耳機、unity play 模式
ms.openlocfilehash: b998233fda34beee0c98795a1efa2c86a53541ba
ms.sourcegitcommit: bdf4babd13e021f41fb04cdb3611bb759bd77537
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2021
ms.locfileid: "112392287"
---
# <a name="unity-play-mode"></a>Unity 播放模式

處理 Unity 專案的快速方式是使用「播放模式」，這會在本機電腦上的 Unity 編輯器中執行您的應用程式。 Unity 使用全像的遠端處理功能，在實際 HoloLens 裝置上提供快速的預覽內容。 [播放] 模式也可以與連接至開發電腦的 Windows Mixed Reality 耳機一起使用。

## <a name="holographic-remoting-setup"></a>全像遠端設定

1. 首先，您必須從 HoloLens 2 上的 Microsoft Store 安裝全像[遠端播放機應用程式](https://www.microsoft.com/store/productId/9NBLGGH4SV40)
2. 在 HoloLens 2 上執行全像遠端播放播放程式應用程式，您會看到要連接的版本號碼和 IP 位址
    * 您將需要2.4 或更新版本才能使用 OpenXR 外掛程式

    ![HoloLens 中執行的全像 Remoting 播放程式的螢幕擷取畫面](images/openxr-features-img-01.png)

## <a name="unity-play-mode-with-holographic-remoting"></a>使用全像攝影遠端的 Unity 播放模式

使用全像全像全像，在您的電腦上的 Unity 編輯器中執行應用程式時，您可以在 HoloLens 上體驗您的應用程式。 「注視」、「手勢」、「聲音」和「空間對應」輸入會從 HoloLens 傳送到您的電腦。 轉譯後的畫面會傳回給您的 HoloLens。 這是快速偵測應用程式，而不需要建立及部署完整專案的絕佳方式。

[!INCLUDE[](includes/unity-play-mode.md)]

全像遠端處理需要快速的電腦和 Wi-Fi 連接。 您可以在全像是「全像 [遠端播放機](../platform-capabilities-and-apis/holographic-remoting-player.md) 」檔中找到更多詳細資料。

為了獲得最佳結果，請確定您的應用程式已正確設定 [焦點點](focus-point-in-unity.md)。 這可協助全像攝影的遠端處理，以最適合您的場景來調整您的無線連線延遲。

## <a name="see-also"></a>另請參閱

* [全像攝影遠端播放程式](../platform-capabilities-and-apis/holographic-remoting-player.md)
