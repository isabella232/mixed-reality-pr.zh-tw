---
title: Unity UWP 應用程式中的 UDP 封包
description: 瞭解如何設定 Unity UWP 應用程式，以透過安全網路傳送和接收 UDP 封包。
author: hferrone
ms.author: v-hferrone
ms.date: 02/3/2021
ms.topic: article
keywords: UDP、UWP、Unity、UDP 封包、通訊端、用戶端伺服器、端點、網路、遠端電腦、datagramsocket、範例、.net
ms.openlocfilehash: a24498384ccb2018f62f00523bf33764d2ef7c019dec0cfd8fc70d86b55a81bb
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2021
ms.locfileid: "115192554"
---
# <a name="udp-packets-in-unity-uwp-apps"></a>Unity UWP 應用程式中的 UDP 封包

您可以使用 udp 通訊端用戶端和伺服器的協助，設定通用 Windows 平臺 (UWP) Unity 應用程式接收 udp 封包。 UDP 通訊端不會在這兩個端點上維持連線，因此它們是在遠端電腦之間進行網路的快速且簡單的解決方案。 不過，您將負責檢查封包是否到達其目的地，因為 UDP 通訊端不會自動進行。

## <a name="setup"></a>設定

開啟您的專案 HoloLens manifest.js檔案，並確認您已啟用：
* **網際網路 (用戶端 & 伺服器)** 
* **私人網路 (用戶端 & 伺服器)**。

## <a name="build-your-socket-client-and-server"></a>建立您的通訊端用戶端和伺服器 

請依照指示來 [建立基本的 UDP 通訊端用戶端和伺服器](/windows/uwp/networking/sockets#build-a-basic-udp-socket-client-and-server)。 您將使用 [DatagramSocket](/uwp/api/Windows.Networking.Sockets.DatagramSocket) 類別透過 UDP 傳送和接收資料，並形成 echo 用戶端和伺服器。 我們也建議您閱讀本文中的其他資源章節，因為它們適用于更多自訂和複雜的使用案例。 

> [!IMPORTANT]
> 如果您無法從電腦傳送 UDP 封包到電腦，請確認您的網路允許這些作業。 如果您的網路以任何方式封鎖 UDP 封包，您的 HoloLens 裝置將無法接聽它們。

您可以從下列連結下載完整的 DatagramSocket UDP 範例應用程式：

> [!div class="nextstepaction"]
> [安裝工具](/samples/microsoft/windows-universal-samples/datagramsocket/)

## <a name="see-also"></a>另請參閱 
* [具有共用全像投影和 Azure Blob 儲存體/UDP 多播的實驗](https://mtaulty.com/2017/12/29/experiments-with-shared-holograms-and-azure-blob-storage-udp-multicasting-part-1/)