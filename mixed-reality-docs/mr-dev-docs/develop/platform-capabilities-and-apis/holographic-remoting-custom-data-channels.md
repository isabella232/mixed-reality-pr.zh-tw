---
title: 自訂全像攝影遠端資料通道
description: 自訂資料通道可用來透過已建立的全像「全像」遠端連線來傳送使用者資料。
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 12/01/2020
ms.topic: article
keywords: HoloLens、遠端、全像攝影遠端、混合現實耳機、windows mixed reality 耳機、虛擬實境耳機、資料頻道
ms.openlocfilehash: a11fe0bb023ae34692015585f6e1689db4330ac7
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/20/2021
ms.locfileid: "98582612"
---
# <a name="custom-holographic-remoting-data-channels"></a><span data-ttu-id="cd759-104">自訂全像攝影遠端資料通道</span><span class="sxs-lookup"><span data-stu-id="cd759-104">Custom Holographic Remoting data channels</span></span>

>[!NOTE]
><span data-ttu-id="cd759-105">本指南專為 HoloLens 2 上的全像攝影遠端所特有。</span><span class="sxs-lookup"><span data-stu-id="cd759-105">This guidance is specific to Holographic Remoting on HoloLens 2.</span></span>

<span data-ttu-id="cd759-106">使用自訂資料通道，透過已建立的遠端連線來傳送自訂資料。</span><span class="sxs-lookup"><span data-stu-id="cd759-106">Use custom data channels to send custom data over an established remoting connection.</span></span>

>[!IMPORTANT]
><span data-ttu-id="cd759-107">自訂資料通道需要自訂遠端應用程式和自訂播放機應用程式，因為它允許在兩個自訂應用程式之間進行通訊。</span><span class="sxs-lookup"><span data-stu-id="cd759-107">Custom data channels require a custom remote app and a custom player app, as it allows for communication between the two custom apps.</span></span>

>[!TIP]
><span data-ttu-id="cd759-108">簡單的乒乓球範例可在「全像遠端」 [範例 github 存放庫](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples)內的遠端和播放機範例中找到。</span><span class="sxs-lookup"><span data-stu-id="cd759-108">A simple ping-pong example can be found in the remote and player samples inside the [Holographic Remoting samples github repository](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).</span></span> <span data-ttu-id="cd759-109">在 ```#define ENABLE_CUSTOM_DATA_CHANNEL_SAMPLE``` SampleRemoteMain .h/SamplePlayerMain .h 檔案內取消批註，以啟用範例程式碼。</span><span class="sxs-lookup"><span data-stu-id="cd759-109">Uncomment ```#define ENABLE_CUSTOM_DATA_CHANNEL_SAMPLE``` inside the SampleRemoteMain.h / SamplePlayerMain.h files to enable the sample code.</span></span>


## <a name="create-a-custom-data-channel"></a><span data-ttu-id="cd759-110">建立自訂資料通道</span><span class="sxs-lookup"><span data-stu-id="cd759-110">Create a custom data channel</span></span>


<span data-ttu-id="cd759-111">若要建立自訂資料通道，需要下欄欄位：</span><span class="sxs-lookup"><span data-stu-id="cd759-111">To create a custom data channel, the following fields are required:</span></span>
```cpp
std::recursive_mutex m_customDataChannelLock;
winrt::Microsoft::Holographic::AppRemoting::IDataChannel m_customDataChannel = nullptr;
winrt::Microsoft::Holographic::AppRemoting::IDataChannel::OnDataReceived_revoker m_customChannelDataReceivedEventRevoker;
winrt::Microsoft::Holographic::AppRemoting::IDataChannel::OnClosed_revoker m_customChannelClosedEventRevoker;
```

<span data-ttu-id="cd759-112">成功建立連接之後，您可以從遠端端、播放程式端或兩者建立新的資料通道。</span><span class="sxs-lookup"><span data-stu-id="cd759-112">After a connection is successfully established, you can create new data channels from either the remote side, the player side, or both.</span></span> <span data-ttu-id="cd759-113">RemoteCoNtext 和 PlayerCoNtext 都提供 ```CreateDataChannel()``` 建立資料通道的方法。</span><span class="sxs-lookup"><span data-stu-id="cd759-113">Both the RemoteContext and the PlayerContext provide a ```CreateDataChannel()``` method for creating data channels.</span></span> <span data-ttu-id="cd759-114">第一個參數是通道識別碼，用來識別後續作業中的資料通道。</span><span class="sxs-lookup"><span data-stu-id="cd759-114">The first parameter is the channel ID, which is used to identify the data channel in subsequent operations.</span></span> <span data-ttu-id="cd759-115">第二個參數是優先順序，可指定此通道的資料會傳送到另一端的優先順序。</span><span class="sxs-lookup"><span data-stu-id="cd759-115">The second parameter is the priority, which specifies the priority with which data of this channel is transferred to the other side.</span></span> <span data-ttu-id="cd759-116">遠端端的有效通道識別碼是從0到（含）（包括63）和64（最高），並包含玩家端的127。</span><span class="sxs-lookup"><span data-stu-id="cd759-116">Valid channel IDs on the remote side are from 0 up to and including 63, and 64 up to and including 127 for the player side.</span></span> <span data-ttu-id="cd759-117">有效的優先順序 ```Low``` 是 ```Medium```) 兩側的、或 ```High``` (。</span><span class="sxs-lookup"><span data-stu-id="cd759-117">Valid priorities are ```Low```, ```Medium```, or ```High``` (on both sides).</span></span>

<span data-ttu-id="cd759-118">若要開始在 **遠端** 建立資料通道：</span><span class="sxs-lookup"><span data-stu-id="cd759-118">To start the creation of a data channel on the **remote** side:</span></span>
```cpp
// Valid channel ids for channels created on the remote side are 0 up to and including 63
m_remoteContext.CreateDataChannel(0, DataChannelPriority::Low);
```

<span data-ttu-id="cd759-119">若要開始在 **播放** 程式端建立資料通道：</span><span class="sxs-lookup"><span data-stu-id="cd759-119">To start the creation of a data channel on the **player** side:</span></span>
```cpp
// Valid channel ids for channels created on the player side are 64 up to and including 127
m_playerContext.CreateDataChannel(64, DataChannelPriority::Low);
```

>[!NOTE]
><span data-ttu-id="cd759-120">若要建立新的自訂資料通道， (遠端或玩家) 只需要呼叫 ```CreateDataChannel``` 方法。</span><span class="sxs-lookup"><span data-stu-id="cd759-120">To create a new custom data channel, only one side (either remote or player) needs to call the ```CreateDataChannel``` method.</span></span>

## <a name="handling-custom-data-channel-events"></a><span data-ttu-id="cd759-121">處理自訂資料通道事件</span><span class="sxs-lookup"><span data-stu-id="cd759-121">Handling custom data channel events</span></span>

<span data-ttu-id="cd759-122">若要建立自訂資料通道， ```OnDataChannelCreated``` 必須在播放玩家和遠端端)  (處理事件。</span><span class="sxs-lookup"><span data-stu-id="cd759-122">To establish a custom data channel, the ```OnDataChannelCreated``` event needs to be handled (on both the player and the remote side).</span></span> <span data-ttu-id="cd759-123">它會在使用者資料通道由任一端建立時觸發，並提供 ```IDataChannel``` 可用於透過此通道傳送及接收資料的物件。</span><span class="sxs-lookup"><span data-stu-id="cd759-123">It triggers when a user data channel has been created by either side and provides a ```IDataChannel``` object, which can be used to send and receive data over this channel.</span></span>

<span data-ttu-id="cd759-124">若要在事件上註冊接聽程式 ```OnDataChannelCreated``` ：</span><span class="sxs-lookup"><span data-stu-id="cd759-124">To register a listener on the ```OnDataChannelCreated``` event:</span></span>
```cpp
m_onDataChannelCreatedEventRevoker = m_remoteContext.OnDataChannelCreated(winrt::auto_revoke,
    [this](const IDataChannel& dataChannel, uint8_t channelId)
    {
        std::lock_guard lock(m_customDataChannelLock);
        m_customDataChannel = dataChannel;

        // Register to OnDataReceived and OnClosed event of the data channel here, see below...
    });
```

<span data-ttu-id="cd759-125">若要在收到資料時收到通知，請 ```OnDataReceived``` 在 ```IDataChannel``` 處理常式所提供的物件上註冊事件 ```OnDataChannelCreated``` 。</span><span class="sxs-lookup"><span data-stu-id="cd759-125">To get notified when data is received, register to the ```OnDataReceived``` event on the ```IDataChannel``` object provided by the ```OnDataChannelCreated``` handler.</span></span> <span data-ttu-id="cd759-126">註冊至 ```OnClosed``` 事件，以在資料通道關閉時收到通知。</span><span class="sxs-lookup"><span data-stu-id="cd759-126">Register to the ```OnClosed``` event, to get notified when the data channel has been closed.</span></span>

```cpp
m_customChannelDataReceivedEventRevoker = m_customDataChannel.OnDataReceived(winrt::auto_revoke, 
    [this]()
    {
        // React on data received via the custom data channel here.
    });

m_customChannelClosedEventRevoker = m_customDataChannel.OnClosed(winrt::auto_revoke,
    [this]()
    {
        // React on data channel closed here.

        std::lock_guard lock(m_customDataChannelLock);
        if (m_customDataChannel)
        {
            m_customDataChannel = nullptr;
        }
    });
```

## <a name="sending-data"></a><span data-ttu-id="cd759-127">傳送資料</span><span class="sxs-lookup"><span data-stu-id="cd759-127">Sending data</span></span>

<span data-ttu-id="cd759-128">若要透過自訂資料通道傳送資料，請使用 ```IDataChannel::SendData()``` 方法。</span><span class="sxs-lookup"><span data-stu-id="cd759-128">To send data over a custom data channel, use the ```IDataChannel::SendData()``` method.</span></span> <span data-ttu-id="cd759-129">第一個參數是 ```winrt::array_view<const uint8_t>``` 應該傳送之資料的。</span><span class="sxs-lookup"><span data-stu-id="cd759-129">The first parameter is a ```winrt::array_view<const uint8_t>``` to the data that should be send.</span></span> <span data-ttu-id="cd759-130">第二個參數會指定應重新傳送資料的位置，直到另一端認可接收為止。</span><span class="sxs-lookup"><span data-stu-id="cd759-130">The second parameter specifies where the data should be resend, until the other side acknowledge the reception.</span></span> 

>[!IMPORTANT]
><span data-ttu-id="cd759-131">如果網路狀況不佳，則相同的資料封包可能會抵達一次以上。</span><span class="sxs-lookup"><span data-stu-id="cd759-131">In case of bad network conditions, the same data packet might arrive more than once.</span></span> <span data-ttu-id="cd759-132">接收端程式碼必須能夠處理這種情況。</span><span class="sxs-lookup"><span data-stu-id="cd759-132">The receiving code must be able to handle this situation.</span></span>

```cpp
uint8_t data[] = {1};
m_customDataChannel.SendData(data, true);
```

## <a name="closing-a-custom-data-channel"></a><span data-ttu-id="cd759-133">關閉自訂資料通道</span><span class="sxs-lookup"><span data-stu-id="cd759-133">Closing a custom data channel</span></span>

<span data-ttu-id="cd759-134">若要關閉自訂資料通道，請使用 ```IDataChannel::Close()``` 方法。</span><span class="sxs-lookup"><span data-stu-id="cd759-134">To close a custom data channel, use the ```IDataChannel::Close()``` method.</span></span> <span data-ttu-id="cd759-135">```OnClosed```當自訂資料通道關閉之後，事件就會通知雙方。</span><span class="sxs-lookup"><span data-stu-id="cd759-135">Both sides will be notified by the ```OnClosed``` event once the custom data channel has been closed.</span></span>

```cpp
m_customDataChannel.Close();
```

## <a name="see-also"></a><span data-ttu-id="cd759-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cd759-136">See Also</span></span>
* [<span data-ttu-id="cd759-137">使用 Windows Mixed Reality Api 撰寫全像遠端執行遠端應用程式</span><span class="sxs-lookup"><span data-stu-id="cd759-137">Writing a Holographic Remoting remote app using Windows Mixed Reality APIs</span></span>](holographic-remoting-create-remote-wmr.md)
* [<span data-ttu-id="cd759-138">使用 OpenXR Api 撰寫全像遠端執行遠端應用程式</span><span class="sxs-lookup"><span data-stu-id="cd759-138">Writing a Holographic Remoting remote app using OpenXR APIs</span></span>](holographic-remoting-create-remote-openxr.md)
* [<span data-ttu-id="cd759-139">撰寫自訂全像攝影遠端播放應用程式</span><span class="sxs-lookup"><span data-stu-id="cd759-139">Writing a custom Holographic Remoting player app</span></span>](holographic-remoting-create-player.md)
* [<span data-ttu-id="cd759-140">全像遠端的疑難排解和限制</span><span class="sxs-lookup"><span data-stu-id="cd759-140">Holographic Remoting troubleshooting and limitations</span></span>](holographic-remoting-troubleshooting.md)
* [<span data-ttu-id="cd759-141">全像攝影遠端軟體授權條款</span><span class="sxs-lookup"><span data-stu-id="cd759-141">Holographic Remoting software license terms</span></span>](//legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [<span data-ttu-id="cd759-142">Microsoft 隱私權聲明</span><span class="sxs-lookup"><span data-stu-id="cd759-142">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)