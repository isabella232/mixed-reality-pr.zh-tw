---
title: Unity 中的本機錨點傳輸
description: 瞭解如何在 Unity mixed reality 應用程式中的多個 HoloLens 裝置之間傳輸錨點。
author: fieldsjacksong
ms.author: jacksonf
ms.date: 03/21/2018
ms.topic: article
keywords: 共用、錨定、WorldAnchor、MR 共用250、WorldAnchorTransferBatch、>spatialperception、傳輸、本機錨定、錨點匯出、錨點匯入
ms.openlocfilehash: 1048e6a3cfc41a04cd49e201e5d1841e805a4193
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009638"
---
# <a name="local-anchor-transfers-in-unity"></a><span data-ttu-id="bf59b-104">Unity 中的本機錨點傳輸</span><span class="sxs-lookup"><span data-stu-id="bf59b-104">Local anchor transfers in Unity</span></span>

<span data-ttu-id="bf59b-105">在您無法使用 <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure 空間錨點</a>的情況下，本機錨點轉移可讓一部 hololens 裝置匯出錨點，以供第二個 hololens 裝置匯入。</span><span class="sxs-lookup"><span data-stu-id="bf59b-105">In situations where you cannot use <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>, local anchor transfers enable one HoloLens device to export an anchor to be imported by a second HoloLens device.</span></span>

>[!NOTE]
><span data-ttu-id="bf59b-106">本機錨點傳輸可提供比 <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure 空間錨點</a>更不健全的錨定回收，而且此方法不支援 IOS 和 Android 裝置。</span><span class="sxs-lookup"><span data-stu-id="bf59b-106">Local anchor transfers provide less robust anchor recall than <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>, and iOS and Android devices are not supported by this approach.</span></span>

### <a name="setting-the-spatialperception-capability"></a><span data-ttu-id="bf59b-107">設定 >spatialperception 功能</span><span class="sxs-lookup"><span data-stu-id="bf59b-107">Setting the SpatialPerception capability</span></span>

<span data-ttu-id="bf59b-108">為了讓應用程式能夠傳送空間錨點，必須啟用 *>spatialperception* 功能。</span><span class="sxs-lookup"><span data-stu-id="bf59b-108">In order for an app to transfer spatial anchors, the *SpatialPerception* capability must be enabled.</span></span>

<span data-ttu-id="bf59b-109">如何啟用 *>spatialperception* 功能：</span><span class="sxs-lookup"><span data-stu-id="bf59b-109">How to enable the *SpatialPerception* capability:</span></span>
1. <span data-ttu-id="bf59b-110">在 Unity 編輯器中，開啟 [ **播放機設定** ] 窗格 (編輯 > 專案設定 > 播放) </span><span class="sxs-lookup"><span data-stu-id="bf59b-110">In the Unity Editor, open the **"Player Settings"** pane (Edit > Project Settings > Player)</span></span>
2. <span data-ttu-id="bf59b-111">按一下 [ **Windows 市存放區** ] 索引標籤</span><span class="sxs-lookup"><span data-stu-id="bf59b-111">Click on the **"Windows Store"** tab</span></span>
3. <span data-ttu-id="bf59b-112">展開 [**發行設定]** ，並檢查 [**功能]** 清單中的 [ **>spatialperception]** 功能</span><span class="sxs-lookup"><span data-stu-id="bf59b-112">Expand **"Publishing Settings"** and check the **"SpatialPerception"** capability in the **"Capabilities"** list</span></span>

>[!NOTE]
><span data-ttu-id="bf59b-113">如果您已將 Unity 專案匯出至 Visual Studio 的解決方案，您必須匯出至新資料夾，或在 [Visual Studio 的 package.appxmanifest 中手動設定這項功能](local-anchor-transfers-in-directx.md#set-up-your-app-to-use-the-spatialperception-capability)。</span><span class="sxs-lookup"><span data-stu-id="bf59b-113">If you have already exported your Unity project to a Visual Studio solution, you will need to either export to a new folder or manually [set this capability in the AppxManifest in Visual Studio](local-anchor-transfers-in-directx.md#set-up-your-app-to-use-the-spatialperception-capability).</span></span>

### <a name="anchor-transfer"></a><span data-ttu-id="bf59b-114">錨點傳輸</span><span class="sxs-lookup"><span data-stu-id="bf59b-114">Anchor Transfer</span></span>

<span data-ttu-id="bf59b-115">**命名空間：** *UnityEngine. XR。共用*</span><span class="sxs-lookup"><span data-stu-id="bf59b-115">**Namespace:** *UnityEngine.XR.WSA.Sharing*</span></span><br>
<span data-ttu-id="bf59b-116">**類型**： *WorldAnchorTransferBatch*</span><span class="sxs-lookup"><span data-stu-id="bf59b-116">**Type**: *WorldAnchorTransferBatch*</span></span>

<span data-ttu-id="bf59b-117">若要傳送 [WorldAnchor](../develop/unity/coordinate-systems-in-unity.md)，必須建立要傳送的錨點。</span><span class="sxs-lookup"><span data-stu-id="bf59b-117">To transfer a [WorldAnchor](../develop/unity/coordinate-systems-in-unity.md), one must establish the anchor to be transferred.</span></span> <span data-ttu-id="bf59b-118">其中一個 HoloLens 的使用者會掃描其環境，並以手動或程式設計方式選擇空間中的點來作為共用體驗的錨點。</span><span class="sxs-lookup"><span data-stu-id="bf59b-118">The user of one HoloLens scans their environment and either manually or programmatically chooses a point in space to be the Anchor for the shared experience.</span></span> <span data-ttu-id="bf59b-119">接著可以將代表這點的資料序列化，並傳輸至體驗中共用的其他裝置。</span><span class="sxs-lookup"><span data-stu-id="bf59b-119">The data that represents this point can then be serialized and transmitted to the other devices that are sharing in the experience.</span></span> <span data-ttu-id="bf59b-120">然後每個裝置都會將錨點資料還原序列化，並嘗試找出空間中的那個點。</span><span class="sxs-lookup"><span data-stu-id="bf59b-120">Each device then de-serializes the anchor data and attempts to locate that point in space.</span></span> <span data-ttu-id="bf59b-121">為了讓錨點傳送正常運作，每個裝置都必須掃描出足夠的環境，讓錨點表示的點可以識別。</span><span class="sxs-lookup"><span data-stu-id="bf59b-121">In order for Anchor Transfer to work, each device must have scanned in enough of the environment such that the point represented by the anchor can be identified.</span></span>

### <a name="setup"></a><span data-ttu-id="bf59b-122">安裝程式</span><span class="sxs-lookup"><span data-stu-id="bf59b-122">Setup</span></span>

<span data-ttu-id="bf59b-123">此頁面上的範例程式碼會有幾個需要初始化的欄位：</span><span class="sxs-lookup"><span data-stu-id="bf59b-123">The sample code on this page has a few fields that will need to be initialized:</span></span>
1. <span data-ttu-id="bf59b-124">*GameObject rootGameObject* 是 Unity 中具有 *WorldAnchor* 元件的 *GameObject* 。</span><span class="sxs-lookup"><span data-stu-id="bf59b-124">*GameObject rootGameObject* is a *GameObject* in Unity that has a *WorldAnchor* Component on it.</span></span> <span data-ttu-id="bf59b-125">共用體驗中的一位使用者將會放置此 *GameObject* ，並將資料匯出給其他使用者。</span><span class="sxs-lookup"><span data-stu-id="bf59b-125">One user in the shared experience will place this *GameObject* and export the data to the other users.</span></span>
2. <span data-ttu-id="bf59b-126">*WorldAnchor gameRootAnchor* 是 *WorldAnchor* 上的 *UnityEngine. XR rootGameObject* 。</span><span class="sxs-lookup"><span data-stu-id="bf59b-126">*WorldAnchor gameRootAnchor* is the *UnityEngine.XR.WSA.WorldAnchor* that is on *rootGameObject*.</span></span>
3. <span data-ttu-id="bf59b-127">*byte [] importedData* 是每個用戶端透過網路接收之序列化錨點的位元組陣列。</span><span class="sxs-lookup"><span data-stu-id="bf59b-127">*byte[] importedData* is a byte array for the serialized anchor each client is receiving over the network.</span></span>

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

### <a name="exporting"></a><span data-ttu-id="bf59b-128">出口</span><span class="sxs-lookup"><span data-stu-id="bf59b-128">Exporting</span></span>

<span data-ttu-id="bf59b-129">若要匯出，我們只需要一個 *WorldAnchor* ，並知道我們會呼叫它，讓接收的應用程式有意義。</span><span class="sxs-lookup"><span data-stu-id="bf59b-129">To export, we just need a *WorldAnchor* and to know what we will call it such that it makes sense for the receiving app.</span></span> <span data-ttu-id="bf59b-130">共用體驗中的一個用戶端會執行下列步驟來匯出共用錨點：</span><span class="sxs-lookup"><span data-stu-id="bf59b-130">One client in the shared experience will perform these steps to export the shared anchor:</span></span>
1. <span data-ttu-id="bf59b-131">建立 *WorldAnchorTransferBatch*</span><span class="sxs-lookup"><span data-stu-id="bf59b-131">Create a *WorldAnchorTransferBatch*</span></span>
2. <span data-ttu-id="bf59b-132">新增要傳送的 *WorldAnchors*</span><span class="sxs-lookup"><span data-stu-id="bf59b-132">Add the *WorldAnchors* to transfer</span></span>
3. <span data-ttu-id="bf59b-133">開始匯出</span><span class="sxs-lookup"><span data-stu-id="bf59b-133">Begin the export</span></span>
4. <span data-ttu-id="bf59b-134">當資料變成可用時，處理 *OnExportDataAvailable* 事件</span><span class="sxs-lookup"><span data-stu-id="bf59b-134">Handle the *OnExportDataAvailable* event as data becomes available</span></span>
5. <span data-ttu-id="bf59b-135">處理 *OnExportComplete* 事件</span><span class="sxs-lookup"><span data-stu-id="bf59b-135">Handle the *OnExportComplete* event</span></span>

<span data-ttu-id="bf59b-136">我們會建立 *WorldAnchorTransferBatch* 來封裝即將傳輸的內容，然後將其匯出為位元組：</span><span class="sxs-lookup"><span data-stu-id="bf59b-136">We create a *WorldAnchorTransferBatch* to encapsulate what we will be transferring and then export that into bytes:</span></span>

```
private void ExportGameRootAnchor()
{
    WorldAnchorTransferBatch transferBatch = new WorldAnchorTransferBatch();
    transferBatch.AddWorldAnchor("gameRoot", this.gameRootAnchor);
    WorldAnchorTransferBatch.ExportAsync(transferBatch, OnExportDataAvailable, OnExportComplete);
}
```

<span data-ttu-id="bf59b-137">當資料可供使用時，會將位元組傳送至用戶端或緩衝區，因為資料區段可供使用，並可透過任何需要的方式傳送：</span><span class="sxs-lookup"><span data-stu-id="bf59b-137">As data becomes available, send the bytes to the client or buffer as segments of data is available and send through whatever means desired:</span></span>

```
private void OnExportDataAvailable(byte[] data)
{
    TransferDataToClient(data);
}
```

<span data-ttu-id="bf59b-138">匯出完成後，如果我們傳輸的資料和序列化失敗，請告知用戶端捨棄資料。</span><span class="sxs-lookup"><span data-stu-id="bf59b-138">Once the export is complete, if we have been transferring data and serialization failed, tell the client to discard the data.</span></span> <span data-ttu-id="bf59b-139">如果序列化成功，請告知用戶端已傳送所有資料，而且可以開始匯入：</span><span class="sxs-lookup"><span data-stu-id="bf59b-139">If the serialization succeeded, tell the client that all data has been transferred and importing can start:</span></span>

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

### <a name="importing"></a><span data-ttu-id="bf59b-140">匯入</span><span class="sxs-lookup"><span data-stu-id="bf59b-140">Importing</span></span>

<span data-ttu-id="bf59b-141">從傳送者收到所有位元組之後，我們可以將資料匯回 *WorldAnchorTransferBatch* ，並將我們的根遊戲物件鎖在相同的實體位置。</span><span class="sxs-lookup"><span data-stu-id="bf59b-141">After receiving all of the bytes from the sender, we can import the data back into a *WorldAnchorTransferBatch* and lock our root game object into the same physical location.</span></span> <span data-ttu-id="bf59b-142">注意：匯入有時會暫時失敗，需要重試：</span><span class="sxs-lookup"><span data-stu-id="bf59b-142">Note: import will sometimes transiently fail and needs to be retried:</span></span>

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

<span data-ttu-id="bf59b-143">透過 *LockObject* 呼叫鎖定 *GameObject* 之後，它會有一個 *WorldAnchor* ，將它保留在世界各地的相同實體位置，但它可能與其他使用者位於 Unity 座標空間中的不同位置。</span><span class="sxs-lookup"><span data-stu-id="bf59b-143">After a *GameObject* is locked via the *LockObject* call, it will have a *WorldAnchor* which will keep it in the same physical position in the world, but it may be at a different location in the Unity coordinate space than other users.</span></span>

