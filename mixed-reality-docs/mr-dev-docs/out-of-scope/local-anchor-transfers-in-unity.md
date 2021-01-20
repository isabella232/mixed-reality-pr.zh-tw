---
title: Unity 中的本機錨點傳輸
description: 瞭解如何在 Unity mixed reality 應用程式中的多個 HoloLens 裝置之間傳輸錨點。
author: fieldsjacksong
ms.author: jacksonf
ms.date: 03/21/2018
ms.topic: article
keywords: 共用、錨定、WorldAnchor、MR 共用250、WorldAnchorTransferBatch、>spatialperception、傳輸、本機錨定、錨點匯出、錨點匯入
ms.openlocfilehash: 4949dd49817d723729974fb5666d5defb64b72ba
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583869"
---
# <a name="local-anchor-transfers-in-unity"></a>Unity 中的本機錨點傳輸

在您無法使用 <a href="/azure/spatial-anchors" target="_blank">Azure 空間錨點</a>的情況下，本機錨點轉移可讓一部 hololens 裝置匯出錨點，以供第二個 hololens 裝置匯入。

>[!NOTE]
>本機錨點傳輸可提供比 <a href="/azure/spatial-anchors" target="_blank">Azure 空間錨點</a>更不健全的錨定回收，而且此方法不支援 IOS 和 Android 裝置。

### <a name="setting-the-spatialperception-capability"></a>設定 >spatialperception 功能

為了讓應用程式能夠傳送空間錨點，必須啟用 *>spatialperception* 功能。

如何啟用 *>spatialperception* 功能：
1. 在 Unity 編輯器中，開啟 [ **播放機設定** ] 窗格 (編輯 > 專案設定 > 播放) 
2. 按一下 [ **Windows 市存放區** ] 索引標籤
3. 展開 [**發行設定]** ，並檢查 [**功能]** 清單中的 [ **>spatialperception]** 功能

>[!NOTE]
>如果您已將 Unity 專案匯出至 Visual Studio 的解決方案，您必須匯出至新資料夾，或在 [Visual Studio 的 package.appxmanifest 中手動設定這項功能](local-anchor-transfers-in-directx.md#set-up-your-app-to-use-the-spatialperception-capability)。

### <a name="anchor-transfer"></a>錨點傳輸

**命名空間：** *UnityEngine. XR。共用*<br>
**類型**： *WorldAnchorTransferBatch*

若要傳送 [WorldAnchor](../develop/unity/coordinate-systems-in-unity.md)，必須建立要傳送的錨點。 其中一個 HoloLens 的使用者會掃描其環境，並以手動或程式設計方式選擇空間中的點來作為共用體驗的錨點。 接著可以將代表這點的資料序列化，並傳輸至體驗中共用的其他裝置。 然後每個裝置都會將錨點資料還原序列化，並嘗試找出空間中的那個點。 為了讓錨點傳送正常運作，每個裝置都必須掃描出足夠的環境，讓錨點表示的點可以識別。

### <a name="setup"></a>安裝程式

此頁面上的範例程式碼會有幾個需要初始化的欄位：
1. *GameObject rootGameObject* 是 Unity 中具有 *WorldAnchor* 元件的 *GameObject* 。 共用體驗中的一位使用者將會放置此 *GameObject* ，並將資料匯出給其他使用者。
2. *WorldAnchor gameRootAnchor* 是 *WorldAnchor* 上的 *UnityEngine. XR rootGameObject* 。
3. *byte [] importedData* 是每個用戶端透過網路接收之序列化錨點的位元組陣列。

```
public GameObject rootGameObject;
private UnityEngine.XR.WSA.WorldAnchor gameRootAnchor;

void Start ()
{
    gameRootAnchor = rootGameObject.GetComponent<UnityEngine.XR.WSA.WorldAnchor>();

    if (gameRootAnchor == null)
    {
        gameRootAnchor = rootGameObject.AddComponent<UnityEngine.XR.WSA.WorldAnchor>();
    }
}
```

### <a name="exporting"></a>出口

若要匯出，我們只需要一個 *WorldAnchor* ，並知道我們會呼叫它，讓接收的應用程式有意義。 共用體驗中的一個用戶端會執行下列步驟來匯出共用錨點：
1. 建立 *WorldAnchorTransferBatch*
2. 新增要傳送的 *WorldAnchors*
3. 開始匯出
4. 當資料變成可用時，處理 *OnExportDataAvailable* 事件
5. 處理 *OnExportComplete* 事件

我們會建立 *WorldAnchorTransferBatch* 來封裝即將傳輸的內容，然後將其匯出為位元組：

```
private void ExportGameRootAnchor()
{
    WorldAnchorTransferBatch transferBatch = new WorldAnchorTransferBatch();
    transferBatch.AddWorldAnchor("gameRoot", this.gameRootAnchor);
    WorldAnchorTransferBatch.ExportAsync(transferBatch, OnExportDataAvailable, OnExportComplete);
}
```

當資料可供使用時，會將位元組傳送至用戶端或緩衝區，因為資料區段可供使用，並可透過任何需要的方式傳送：

```
private void OnExportDataAvailable(byte[] data)
{
    TransferDataToClient(data);
}
```

匯出完成後，如果我們傳輸的資料和序列化失敗，請告知用戶端捨棄資料。 如果序列化成功，請告知用戶端已傳送所有資料，而且可以開始匯入：

```
private void OnExportComplete(SerializationCompletionReason completionReason)
{
    if (completionReason != SerializationCompletionReason.Succeeded)
    {
        SendExportFailedToClient();
    }
    else
    {
        SendExportSucceededToClient();
    }
}
```

### <a name="importing"></a>匯入

從傳送者收到所有位元組之後，我們可以將資料匯回 *WorldAnchorTransferBatch* ，並將我們的根遊戲物件鎖在相同的實體位置。 注意：匯入有時會暫時失敗，需要重試：

```
// This byte array should have been updated over the network from TransferDataToClient
private byte[] importedData;
private int retryCount = 3;

private void ImportRootGameObject()
{
    WorldAnchorTransferBatch.ImportAsync(importedData, OnImportComplete);
}

private void OnImportComplete(SerializationCompletionReason completionReason, WorldAnchorTransferBatch deserializedTransferBatch)
{
    if (completionReason != SerializationCompletionReason.Succeeded)
    {
        Debug.Log("Failed to import: " + completionReason.ToString());
        if (retryCount > 0)
        {
            retryCount--;
            WorldAnchorTransferBatch.ImportAsync(importedData, OnImportComplete);
        }
        return;
    }

    this.gameRootAnchor = deserializedTransferBatch.LockObject("gameRoot", this.rootGameObject);
}
```

透過 *LockObject* 呼叫鎖定 *GameObject* 之後，它會有一個 *WorldAnchor* ，將它保留在世界各地的相同實體位置，但它可能與其他使用者位於 Unity 座標空間中的不同位置。