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
# <a name="udp-packets-in-unity-uwp-apps"></a><span data-ttu-id="1ea0b-104">Unity UWP 應用程式中的 UDP 封包</span><span class="sxs-lookup"><span data-stu-id="1ea0b-104">UDP packets in Unity UWP apps</span></span>

<span data-ttu-id="1ea0b-105">您可以使用 UDP 通訊端用戶端和伺服器的協助，設定通用 Windows 平臺 (UWP) Unity 應用程式接收 UDP 封包。</span><span class="sxs-lookup"><span data-stu-id="1ea0b-105">You can setup your Universal Windows Platform (UWP) Unity apps to receive UDP packets with the help of a UDP socket client and server.</span></span> <span data-ttu-id="1ea0b-106">UDP 通訊端不會在這兩個端點上維持連線，因此它們是在遠端電腦之間進行網路的快速且簡單的解決方案。</span><span class="sxs-lookup"><span data-stu-id="1ea0b-106">UDP sockets don't maintain connection on both endpoints, so they're a fast and simple solution for networking between remote machines.</span></span> <span data-ttu-id="1ea0b-107">不過，您將負責檢查封包是否到達其目的地，因為 UDP 通訊端不會自動進行。</span><span class="sxs-lookup"><span data-stu-id="1ea0b-107">However, you'll be responsible for checking if the packets get to their destination, as UDP sockets don't do that automatically.</span></span>

## <a name="setup"></a><span data-ttu-id="1ea0b-108">安裝程式</span><span class="sxs-lookup"><span data-stu-id="1ea0b-108">Setup</span></span>

<span data-ttu-id="1ea0b-109">開啟您的專案 HoloLens manifest.json file，確定您已啟用：</span><span class="sxs-lookup"><span data-stu-id="1ea0b-109">Open your projects HoloLens manifest.json file and make sure you've enabled:</span></span>
* <span data-ttu-id="1ea0b-110">**網際網路 (用戶端 & 伺服器)**</span><span class="sxs-lookup"><span data-stu-id="1ea0b-110">**Internet (Client & Server)**</span></span> 
* <span data-ttu-id="1ea0b-111">**私人網路 (用戶端 & 伺服器)**。</span><span class="sxs-lookup"><span data-stu-id="1ea0b-111">**Private Networks (Client & Server)**.</span></span>

## <a name="build-your-socket-client-and-server"></a><span data-ttu-id="1ea0b-112">建立您的通訊端用戶端和伺服器</span><span class="sxs-lookup"><span data-stu-id="1ea0b-112">Build your socket client and server</span></span> 

<span data-ttu-id="1ea0b-113">請依照指示來 [建立基本的 UDP 通訊端用戶端和伺服器](https://docs.microsoft.com/windows/uwp/networking/sockets#build-a-basic-udp-socket-client-and-server)。</span><span class="sxs-lookup"><span data-stu-id="1ea0b-113">Follow the instructions for [building a basic UDP socket client and server](https://docs.microsoft.com/windows/uwp/networking/sockets#build-a-basic-udp-socket-client-and-server).</span></span> <span data-ttu-id="1ea0b-114">您將使用 [DatagramSocket](https://docs.microsoft.com/uwp/api/Windows.Networking.Sockets.DatagramSocket) 類別透過 UDP 傳送和接收資料，並形成 echo 用戶端和伺服器。</span><span class="sxs-lookup"><span data-stu-id="1ea0b-114">You'll be using the [DatagramSocket](https://docs.microsoft.com/uwp/api/Windows.Networking.Sockets.DatagramSocket) class to send and receive data over UDP and form an echo client and server.</span></span> <span data-ttu-id="1ea0b-115">我們也建議您閱讀本文中的其他資源章節，因為它們適用于更多自訂和複雜的使用案例。</span><span class="sxs-lookup"><span data-stu-id="1ea0b-115">We also recommend reading through the other resource sections in this article, as they apply to more customized and complex use cases.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="1ea0b-116">如果您無法從電腦傳送 UDP 封包到電腦，請確認您的網路允許這些作業。</span><span class="sxs-lookup"><span data-stu-id="1ea0b-116">If you're having trouble sending UDP packets from PC to PC, check that your network allows these operations.</span></span> <span data-ttu-id="1ea0b-117">如果您的網路以任何方式封鎖 UDP 封包，則 HoloLens 裝置將無法接聽它們。</span><span class="sxs-lookup"><span data-stu-id="1ea0b-117">If your network is blocking the UDP packets in any way, your HoloLens device won't be able to listen for them.</span></span>

<span data-ttu-id="1ea0b-118">您可以從下列連結下載完整的 DatagramSocket UDP 範例應用程式：</span><span class="sxs-lookup"><span data-stu-id="1ea0b-118">You can download a complete DatagramSocket UDP sample app from the link below:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="1ea0b-119">安裝工具</span><span class="sxs-lookup"><span data-stu-id="1ea0b-119">Install the tools</span></span>](https://docs.microsoft.com/samples/microsoft/windows-universal-samples/datagramsocket/)

## <a name="see-also"></a><span data-ttu-id="1ea0b-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1ea0b-120">See also</span></span> 
* [<span data-ttu-id="1ea0b-121">具有共用全像 Azure Blob 儲存體/UDP 多播的實驗</span><span class="sxs-lookup"><span data-stu-id="1ea0b-121">Experiments with Shared Holograms and Azure Blob Storage/UDP Multicasting</span></span>](https://mtaulty.com/2017/12/29/experiments-with-shared-holograms-and-azure-blob-storage-udp-multicasting-part-1/)