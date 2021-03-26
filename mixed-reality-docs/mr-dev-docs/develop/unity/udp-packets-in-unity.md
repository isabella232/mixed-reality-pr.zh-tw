---
title: Unity UWP 應用程式中的 UDP 封包
description: 瞭解如何設定 Unity UWP 應用程式，以透過安全網路傳送和接收 UDP 封包。
author: hferrone
ms.author: v-hferrone
ms.date: 02/3/2021
ms.topic: article
keywords: UDP、UWP、Unity、UDP 封包、通訊端、用戶端伺服器、端點、網路、遠端電腦、datagramsocket、範例、.net
ms.openlocfilehash: b38897f228a62abeb63b7e2ffc0f2a98a840b781
ms.sourcegitcommit: ac315c1d35f2b9c431e79bc3f1212215301bb867
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105550518"
---
# <a name="udp-packets-in-unity-uwp-apps"></a><span data-ttu-id="49d04-104">Unity UWP 應用程式中的 UDP 封包</span><span class="sxs-lookup"><span data-stu-id="49d04-104">UDP packets in Unity UWP apps</span></span>

<span data-ttu-id="49d04-105">您可以使用 UDP 通訊端用戶端和伺服器的協助，設定通用 Windows 平臺 (UWP) Unity 應用程式接收 UDP 封包。</span><span class="sxs-lookup"><span data-stu-id="49d04-105">You can setup your Universal Windows Platform (UWP) Unity apps to receive UDP packets with the help of a UDP socket client and server.</span></span> <span data-ttu-id="49d04-106">UDP 通訊端不會在這兩個端點上維持連線，因此它們是在遠端電腦之間進行網路的快速且簡單的解決方案。</span><span class="sxs-lookup"><span data-stu-id="49d04-106">UDP sockets don't maintain connection on both endpoints, so they're a fast and simple solution for networking between remote machines.</span></span> <span data-ttu-id="49d04-107">不過，您將負責檢查封包是否到達其目的地，因為 UDP 通訊端不會自動進行。</span><span class="sxs-lookup"><span data-stu-id="49d04-107">However, you'll be responsible for checking if the packets get to their destination, as UDP sockets don't do that automatically.</span></span>

## <a name="setup"></a><span data-ttu-id="49d04-108">設定</span><span class="sxs-lookup"><span data-stu-id="49d04-108">Setup</span></span>

<span data-ttu-id="49d04-109">開啟您的專案 HoloLens manifest.json file，確定您已啟用：</span><span class="sxs-lookup"><span data-stu-id="49d04-109">Open your projects HoloLens manifest.json file and make sure you've enabled:</span></span>
* <span data-ttu-id="49d04-110">**網際網路 (用戶端 & 伺服器)**</span><span class="sxs-lookup"><span data-stu-id="49d04-110">**Internet (Client & Server)**</span></span> 
* <span data-ttu-id="49d04-111">**私人網路 (用戶端 & 伺服器)**。</span><span class="sxs-lookup"><span data-stu-id="49d04-111">**Private Networks (Client & Server)**.</span></span>

## <a name="build-your-socket-client-and-server"></a><span data-ttu-id="49d04-112">建立您的通訊端用戶端和伺服器</span><span class="sxs-lookup"><span data-stu-id="49d04-112">Build your socket client and server</span></span> 

<span data-ttu-id="49d04-113">請依照指示來 [建立基本的 UDP 通訊端用戶端和伺服器](/windows/uwp/networking/sockets#build-a-basic-udp-socket-client-and-server)。</span><span class="sxs-lookup"><span data-stu-id="49d04-113">Follow the instructions for [building a basic UDP socket client and server](/windows/uwp/networking/sockets#build-a-basic-udp-socket-client-and-server).</span></span> <span data-ttu-id="49d04-114">您將使用 [DatagramSocket](/uwp/api/Windows.Networking.Sockets.DatagramSocket) 類別透過 UDP 傳送和接收資料，並形成 echo 用戶端和伺服器。</span><span class="sxs-lookup"><span data-stu-id="49d04-114">You'll be using the [DatagramSocket](/uwp/api/Windows.Networking.Sockets.DatagramSocket) class to send and receive data over UDP and form an echo client and server.</span></span> <span data-ttu-id="49d04-115">我們也建議您閱讀本文中的其他資源章節，因為它們適用于更多自訂和複雜的使用案例。</span><span class="sxs-lookup"><span data-stu-id="49d04-115">We also recommend reading through the other resource sections in this article, as they apply to more customized and complex use cases.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="49d04-116">如果您無法從電腦傳送 UDP 封包到電腦，請確認您的網路允許這些作業。</span><span class="sxs-lookup"><span data-stu-id="49d04-116">If you're having trouble sending UDP packets from PC to PC, check that your network allows these operations.</span></span> <span data-ttu-id="49d04-117">如果您的網路以任何方式封鎖 UDP 封包，則 HoloLens 裝置將無法接聽它們。</span><span class="sxs-lookup"><span data-stu-id="49d04-117">If your network is blocking the UDP packets in any way, your HoloLens device won't be able to listen for them.</span></span>

<span data-ttu-id="49d04-118">您可以從下列連結下載完整的 DatagramSocket UDP 範例應用程式：</span><span class="sxs-lookup"><span data-stu-id="49d04-118">You can download a complete DatagramSocket UDP sample app from the link below:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="49d04-119">安裝工具</span><span class="sxs-lookup"><span data-stu-id="49d04-119">Install the tools</span></span>](/samples/microsoft/windows-universal-samples/datagramsocket/)

## <a name="see-also"></a><span data-ttu-id="49d04-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="49d04-120">See also</span></span> 
* [<span data-ttu-id="49d04-121">具有共用全像 Azure Blob 儲存體/UDP 多播的實驗</span><span class="sxs-lookup"><span data-stu-id="49d04-121">Experiments with Shared Holograms and Azure Blob Storage/UDP Multicasting</span></span>](https://mtaulty.com/2017/12/29/experiments-with-shared-holograms-and-azure-blob-storage-udp-multicasting-part-1/)