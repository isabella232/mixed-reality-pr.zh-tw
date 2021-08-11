---
title: 自訂全像攝影遠端資料通道
description: 自訂資料通道可用來透過已建立的全像「全像」遠端連線來傳送使用者資料。
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 12/01/2020
ms.topic: article
keywords: HoloLens、遠端、全像全像遠端、混合現實耳機、windows mixed reality 耳機、虛擬實境耳機、資料頻道
ms.openlocfilehash: 09fea161f9042d7afc59c16d3b5e8a6c69892e84b1de5e9ab4a4808733b4f171
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2021
ms.locfileid: "115217084"
---
# <a name="custom-holographic-remoting-data-channels"></a>自訂全像攝影遠端資料通道

>[!NOTE]
>本指南專為 HoloLens 2 上的全像攝影遠端所特有。

使用自訂資料通道，透過已建立的遠端連線來傳送自訂資料。

>[!IMPORTANT]
>自訂資料通道需要自訂遠端應用程式和自訂播放機應用程式，因為它允許在兩個自訂應用程式之間進行通訊。

>[!TIP]
>簡單的乒乓球範例可在「全像遠端」 [範例 github 存放庫](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples)內的遠端和播放機範例中找到。 在 ```#define ENABLE_CUSTOM_DATA_CHANNEL_SAMPLE``` SampleRemoteMain .h/SamplePlayerMain .h 檔案內取消批註，以啟用範例程式碼。


## <a name="create-a-custom-data-channel"></a>建立自訂資料通道


若要建立自訂資料通道，需要下欄欄位：
```cpp
std::recursive_mutex m_customDataChannelLock;
winrt::Microsoft::Holographic::AppRemoting::IDataChannel m_customDataChannel = nullptr;
winrt::Microsoft::Holographic::AppRemoting::IDataChannel::OnDataReceived_revoker m_customChannelDataReceivedEventRevoker;
winrt::Microsoft::Holographic::AppRemoting::IDataChannel::OnClosed_revoker m_customChannelClosedEventRevoker;
```

成功建立連接之後，您可以從遠端端、播放程式端或兩者建立新的資料通道。 RemoteCoNtext 和 PlayerCoNtext 都提供 ```CreateDataChannel()``` 建立資料通道的方法。 第一個參數是通道識別碼，用來識別後續作業中的資料通道。 第二個參數是優先順序，可指定此通道的資料會傳送到另一端的優先順序。 遠端端的有效通道識別碼是從0到（含）（包括63）和64（最高），並包含玩家端的127。 有效的優先順序 ```Low``` 是 ```Medium```) 兩側的、或 ```High``` (。

若要開始在 **遠端** 建立資料通道：
```cpp
// Valid channel ids for channels created on the remote side are 0 up to and including 63
m_remoteContext.CreateDataChannel(0, DataChannelPriority::Low);
```

若要開始在 **播放** 程式端建立資料通道：
```cpp
// Valid channel ids for channels created on the player side are 64 up to and including 127
m_playerContext.CreateDataChannel(64, DataChannelPriority::Low);
```

>[!NOTE]
>若要建立新的自訂資料通道， (遠端或玩家) 只需要呼叫 ```CreateDataChannel``` 方法。

## <a name="handling-custom-data-channel-events"></a>處理自訂資料通道事件

若要建立自訂資料通道， ```OnDataChannelCreated``` 必須在播放玩家和遠端端)  (處理事件。 它會在使用者資料通道由任一端建立時觸發，並提供 ```IDataChannel``` 可用於透過此通道傳送及接收資料的物件。

若要在事件上註冊接聽程式 ```OnDataChannelCreated``` ：
```cpp
m_onDataChannelCreatedEventRevoker = m_remoteContext.OnDataChannelCreated(winrt::auto_revoke,
    [this](const IDataChannel& dataChannel, uint8_t channelId)
    {
        std::lock_guard lock(m_customDataChannelLock);
        m_customDataChannel = dataChannel;

        // Register to OnDataReceived and OnClosed event of the data channel here, see below...
    });
```

若要在收到資料時收到通知，請 ```OnDataReceived``` 在 ```IDataChannel``` 處理常式所提供的物件上註冊事件 ```OnDataChannelCreated``` 。 註冊至 ```OnClosed``` 事件，以在資料通道關閉時收到通知。

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

## <a name="sending-data"></a>傳送資料

若要透過自訂資料通道傳送資料，請使用 ```IDataChannel::SendData()``` 方法。 第一個參數是 ```winrt::array_view<const uint8_t>``` 應該傳送之資料的。 第二個參數會指定應重新傳送資料的位置，直到另一端認可接收為止。 

>[!IMPORTANT]
>如果網路狀況不佳，則相同的資料封包可能會抵達一次以上。 接收端程式碼必須能夠處理這種情況。

```cpp
uint8_t data[] = {1};
m_customDataChannel.SendData(data, true);
```

## <a name="closing-a-custom-data-channel"></a>關閉自訂資料通道

若要關閉自訂資料通道，請使用 ```IDataChannel::Close()``` 方法。 ```OnClosed```當自訂資料通道關閉之後，事件就會通知雙方。

```cpp
m_customDataChannel.Close();
```

## <a name="see-also"></a>另請參閱
* [使用 Windows Mixed Reality api 撰寫全像遠端執行遠端應用程式](holographic-remoting-create-remote-wmr.md)
* [使用 OpenXR Api 撰寫全像遠端執行遠端應用程式](holographic-remoting-create-remote-openxr.md)
* [撰寫自訂全像攝影遠端播放應用程式](holographic-remoting-create-player.md)
* [全像遠端的疑難排解和限制](holographic-remoting-troubleshooting.md)
* [全像攝影遠端軟體授權條款](/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Microsoft 隱私權聲明](https://go.microsoft.com/fwlink/?LinkId=521839)