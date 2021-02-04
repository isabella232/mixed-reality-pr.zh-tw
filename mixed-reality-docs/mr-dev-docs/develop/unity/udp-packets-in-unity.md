---
title: Unity UWP 應用程式中的 UDP 封包
description: 瞭解如何設定 Unity UWP 應用程式，以透過安全網路傳送和接收 UDP 封包。
author: hferrone
ms.author: v-hferrone
ms.date: 02/3/2021
ms.topic: article
keywords: UDP、UWP、Unity、UDP 封包、通訊端、用戶端伺服器、端點、網路、遠端電腦、datagramsocket、範例、.net
ms.openlocfilehash: e4fbdc12a1f7fbca44e14f6ace89ef791a09608f
ms.sourcegitcommit: 8647702638f7600c51df1d89d76c761b52bdf0d7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/04/2021
ms.locfileid: "99566973"
---
# <a name="udp-packets-in-unity-uwp-apps"></a>Unity UWP 應用程式中的 UDP 封包

您可以使用 UDP 通訊端用戶端和伺服器的協助，設定通用 Windows 平臺 (UWP) Unity 應用程式接收 UDP 封包。 UDP 通訊端不會在這兩個端點上維持連線，因此它們是在遠端電腦之間進行網路的快速且簡單的解決方案。 不過，您將負責檢查封包是否到達其目的地，因為 UDP 通訊端不會自動進行。

## <a name="setup"></a>安裝程式

開啟您的專案 HoloLens manifest.json file，確定您已啟用：
* **網際網路 (用戶端 & 伺服器)** 
* **私人網路 (用戶端 & 伺服器)**。

## <a name="build-your-socket-client-and-server"></a>建立您的通訊端用戶端和伺服器 

請依照指示來 [建立基本的 UDP 通訊端用戶端和伺服器](https://docs.microsoft.com/windows/uwp/networking/sockets#build-a-basic-udp-socket-client-and-server)。 您將使用 [DatagramSocket](https://docs.microsoft.com/uwp/api/Windows.Networking.Sockets.DatagramSocket) 類別透過 UDP 傳送和接收資料，並形成 echo 用戶端和伺服器。 我們也建議您閱讀本文中的其他資源章節，因為它們適用于更多自訂和複雜的使用案例。 

> [!IMPORTANT]
> 如果您無法從電腦傳送 UDP 封包到電腦，請確認您的網路允許這些作業。 如果您的網路以任何方式封鎖 UDP 封包，則 HoloLens 裝置將無法接聽它們。

您可以從下列連結下載完整的 DatagramSocket UDP 範例應用程式：

> [!div class="nextstepaction"]
> [安裝工具](https://docs.microsoft.com/samples/microsoft/windows-universal-samples/datagramsocket/)

## <a name="see-also"></a>另請參閱 
* [具有共用全像 Azure Blob 儲存體/UDP 多播的實驗](https://mtaulty.com/2017/12/29/experiments-with-shared-holograms-and-azure-blob-storage-udp-multicasting-part-1/)