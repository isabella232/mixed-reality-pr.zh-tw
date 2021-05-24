---
title: Unity 播放模式
description: 瞭解如何在 Unity 編輯器中使用播放模式，以預覽裝置上的應用程式變更，而不需要部署應用程式。
author: jonmlyons
ms.author: jlyons
ms.date: 03/21/2018
ms.topic: article
keywords: Unity、遠端處理、全像全像攝影、全像遠端播放機、HoloLens、混合現實耳機、windows mixed reality 耳機、虛擬實境耳機、unity play 模式
ms.openlocfilehash: 35f80b0c217adfd5c5d14799dc882d5c504925aa
ms.sourcegitcommit: b195b82f7e83e2ac4f5d8937d169e9dcb865d46d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/24/2021
ms.locfileid: "110333396"
---
# <a name="unity-play-mode"></a>Unity 播放模式

處理 Unity 專案的快速方式是使用「播放模式」，這會在本機電腦上的 Unity 編輯器中執行您的應用程式。 Unity 使用全像的遠端處理功能，在實際 HoloLens 裝置上提供快速的預覽內容。 [播放] 模式也可以與連接至開發電腦的 Windows Mixed Reality 耳機一起使用。

## <a name="holographic-remoting-setup"></a>全像遠端設定

1. 首先，您必須從 HoloLens 2 上的 Microsoft Store 安裝全像[遠端播放機應用程式](https://www.microsoft.com/store/productId/9NBLGGH4SV40)
2. 在 HoloLens 2 上執行全像遠端播放播放程式應用程式，您會看到要連接的版本號碼和 IP 位址
    * 您將需要2.4 或更新版本才能使用 OpenXR 外掛程式

    ![HoloLens 中執行的全像 Remoting 播放程式的螢幕擷取畫面](images/openxr-features-img-01.png)

## <a name="holographic-remoting-in-unity-editor-play-mode"></a>Unity 編輯器 play 模式的全像遠端功能

在 Visual Studio 專案中建立 UWP Unity 專案，然後將它封裝並部署到 HoloLens 2 裝置，可能需要一些時間。 其中一個解決方法是啟用全像「全像」編輯器遠端功能，讓您透過網路直接使用「播放」模式來將 c # 腳本進行 HoloLens 2 裝置的偵測。 此案例可避免建立 UWP 套件並將其部署至遠端裝置的額外負荷。

1. 遵循全像全像[遠端設定](#holographic-remoting-setup)的步驟
2. 開啟 **Windows > XR > OpenXR 編輯器遠端** 執行：

    ![醒目提示 XR 外掛程式管理的 Unity 編輯器中開啟之 [專案設定] 面板的螢幕擷取畫面](images/openxr-features-img-02.png)

3. 輸入您從全像全像遠端應用程式取得的 IP 位址，然後選取 [**啟用編輯器遠端**]

    ![在 Unity 編輯器中開啟專案設定面板的螢幕擷取畫面，其中已醒目提示功能](images/openxr-features-img-03.png)

現在您可以按一下 [播放] 按鈕，以在 HoloLens 上的全像遠端應用程式中播放 Unity 應用程式。 您也可以 [將 Visual Studio 附加至 Unity](/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows) ，以在播放模式中進行 c # 腳本的調試。

> [!NOTE]
> 從0.1.0 版起，全像「全像」遠端執行時間不支援錨點，而 ARAnchorManager 功能將無法透過遠端處理。  這項功能會在未來的版本中推出。

## <a name="unity-play-mode-with-holographic-remoting"></a>使用全像攝影遠端的 Unity 播放模式

使用全像全像全像，在您的電腦上的 Unity 編輯器中執行應用程式時，您可以在 HoloLens 上體驗您的應用程式。 「注視」、「手勢」、「聲音」和「空間對應」輸入會從 HoloLens 傳送到您的電腦。 轉譯後的畫面會傳回給您的 HoloLens。 這是快速偵測應用程式，而不需要建立及部署完整專案的絕佳方式。
1. 在 HoloLens 上，移至 **Microsoft Store** 並安裝全像 **[遠端播放機](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)** 應用程式。
2. 在您的 HoloLens 上，啟動全像 **Remoting 的播放** 程式應用程式。
3. 在 Unity 中，移至 [ **視窗]** 功能表，展開 [ **XR** ] 子功能表，然後選取 [全像] **模擬**。
4. 將 **模擬模式** 設定為 [ **遠端裝置**]。
5. 針對 [ **遠端電腦**]，輸入 HOLOLENS 的 IP 位址。
6. 選取 [連線]。 您應該會看到 [連線 **狀態** ] 變更為 [ **已連接** ]，並在 HoloLens 中看到畫面空白。
7. 選取 [ **播放** ] 按鈕以啟動播放模式，並在您的 HoloLens 上體驗應用程式。

全像遠端處理需要快速的電腦和 Wi-Fi 連接。 您可以在全像是「全像 [遠端播放機](../platform-capabilities-and-apis/holographic-remoting-player.md) 」檔中找到更多詳細資料。

為了獲得最佳結果，請確定您的應用程式已正確設定 [焦點點](focus-point-in-unity.md)。 這可協助全像攝影的遠端處理，以最適合您的場景來調整您的無線連線延遲。

## <a name="see-also"></a>另請參閱
* [全像攝影遠端播放程式](../platform-capabilities-and-apis/holographic-remoting-player.md)
