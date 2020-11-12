---
title: Unity 播放模式
description: 在 Unity 編輯器中使用播放模式，以預覽裝置上的變更，而不需要部署應用程式。
author: jonmlyons
ms.author: jlyons
ms.date: 03/21/2018
ms.topic: article
keywords: Unity、遠端、全像全像全像攝影遠端播放
ms.openlocfilehash: 4239eba84bd94c0bdc596392fdf7a0c780778850
ms.sourcegitcommit: 520c69eb761ad6083b36f448bbcfab89e343e40d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/12/2020
ms.locfileid: "94549091"
---
# <a name="unity-play-mode"></a>Unity 播放模式

處理 Unity 專案的快速方式是使用「播放模式」。 這會在電腦的 Unity 編輯器中本機執行您的應用程式。 Unity 使用全像的遠端處理功能，在實際 HoloLens 裝置上提供快速的預覽內容。 [播放] 模式也可以與連接至開發電腦的 Windows Mixed Reality 耳機一起使用。

## <a name="unity-play-mode-with-holographic-remoting"></a>使用全像攝影遠端的 Unity 播放模式

使用全像全像攝影版，您可以在 HoloLens 上體驗您的應用程式，同時在您的電腦上的 Unity 編輯器中執行應用程式。 「注視」、「手勢」、「聲音」和「空間對應」輸入會從 HoloLens 傳送到您的電腦。 轉譯後的畫面會傳回給您的 HoloLens。 這是快速偵測應用程式，而不需要建立及部署完整專案的絕佳方式。
1. 在 HoloLens 上，移至 **Microsoft Store** 並安裝全像 **[遠端播放機](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)** 應用程式。
2. 在您的 HoloLens 上，啟動全像 **Remoting 的播放** 程式應用程式。
3. 在 Unity 中，移至 [ **視窗]** 功能表，展開 [ **XR** ] 子功能表，然後選取 [全像] **模擬** 。
4. 將 **模擬模式** 設定為 [ **遠端裝置** ]。
5. 針對 [ **遠端電腦** ]，輸入 HOLOLENS 的 IP 位址。
6. 按一下 [ **連接** ]。 您應該會看到 [連線 **狀態** ] 變更為 [ **已連接** ]，並在 HoloLens 中看到畫面空白。
7. 按一下 [ **播放** ] 按鈕以啟動播放模式，並在您的 HoloLens 上體驗應用程式。

全像遠端處理需要快速的電腦和 Wi-Fi 連接。 如需完整的詳細資料，請參閱全像全像[遠端播放機](../platform-capabilities-and-apis/holographic-remoting-player.md)

為了獲得最佳結果，請確定您的應用程式已正確設定 [焦點點](focus-point-in-unity.md)。 這可協助全像攝影的遠端處理，以最適合您的場景來調整您的無線連線延遲。

## <a name="see-also"></a>另請參閱
* [全像攝影遠端播放程式](../platform-capabilities-and-apis/holographic-remoting-player.md)
