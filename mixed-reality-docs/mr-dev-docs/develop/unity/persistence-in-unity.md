---
title: Unity 中的持續性
description: 持續性可讓您的使用者在想要的任何地方釘選個別的全像全像全半商店或工作區，然後在應用程式的許多用途之後找出它。
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: HoloLens、持續性、Unity
ms.openlocfilehash: bb1a9b0544f9325a60c86c7424b7b451b6b4335b
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2020
ms.locfileid: "91682460"
---
# <a name="persistence-in-unity"></a><span data-ttu-id="163cc-104">Unity 中的持續性</span><span class="sxs-lookup"><span data-stu-id="163cc-104">Persistence in Unity</span></span>

<span data-ttu-id="163cc-105">**命名空間：** *UnityEngine. XR*</span><span class="sxs-lookup"><span data-stu-id="163cc-105">**Namespace:** *UnityEngine.XR.WSA.Persistence*</span></span><br>
<span data-ttu-id="163cc-106">**類別：** *WorldAnchorStore*</span><span class="sxs-lookup"><span data-stu-id="163cc-106">**Class:** *WorldAnchorStore*</span></span>

<span data-ttu-id="163cc-107">WorldAnchorStore 是建立全像攝影體驗的關鍵，也就是在應用程式的各個實例上，全像地方都有特定的真實世界位置。</span><span class="sxs-lookup"><span data-stu-id="163cc-107">The WorldAnchorStore is the key to creating holographic experiences where holograms stay in specific real world positions across instances of the application.</span></span> <span data-ttu-id="163cc-108">這可讓您的使用者在想要的任何地方釘選個別的全像全像全像全半商店或工作區，然後在您應用程式的許多用途之後找出它。</span><span class="sxs-lookup"><span data-stu-id="163cc-108">This lets your users pin individual holograms or a workspace wherever they want it, and then find it later where they expect over many uses of your app.</span></span>

## <a name="how-to-persist-holograms-across-sessions"></a><span data-ttu-id="163cc-109">如何跨會話保存全息</span><span class="sxs-lookup"><span data-stu-id="163cc-109">How to persist holograms across sessions</span></span>

<span data-ttu-id="163cc-110">WorldAnchorStore 可讓您跨會話保存 WorldAnchor 的位置。</span><span class="sxs-lookup"><span data-stu-id="163cc-110">The WorldAnchorStore will allow you to persist the location of WorldAnchor's across sessions.</span></span> <span data-ttu-id="163cc-111">若要實際跨會話保存全像投影，您必須個別追蹤使用特定世界錨點的 Gameobject。</span><span class="sxs-lookup"><span data-stu-id="163cc-111">To actually persist holograms across sessions, you will need to separately keep track of your GameObjects that use a particular world anchor.</span></span> <span data-ttu-id="163cc-112">建立具有世界錨點的 GameObject 根目錄通常是合理的，並讓子影像以本機位置位移錨定。</span><span class="sxs-lookup"><span data-stu-id="163cc-112">It often makes sense to create a GameObject root with a world anchor and have children holograms anchored by it with a local position offset.</span></span>

<span data-ttu-id="163cc-113">若要從先前的會話載入全息影像：</span><span class="sxs-lookup"><span data-stu-id="163cc-113">To load holograms from previous sessions:</span></span>
1. <span data-ttu-id="163cc-114">取得 WorldAnchorStore</span><span class="sxs-lookup"><span data-stu-id="163cc-114">Get the WorldAnchorStore</span></span>
2. <span data-ttu-id="163cc-115">載入與全球錨點相關的應用程式資料，以提供您世界錨點的識別碼</span><span class="sxs-lookup"><span data-stu-id="163cc-115">Load app data relating to the world anchor which gives you the id of the world anchor</span></span>
3. <span data-ttu-id="163cc-116">從識別碼載入世界錨點</span><span class="sxs-lookup"><span data-stu-id="163cc-116">Load a world anchor from its id</span></span>

<span data-ttu-id="163cc-117">若要在未來的會話中儲存影像：</span><span class="sxs-lookup"><span data-stu-id="163cc-117">To save holograms for future sessions:</span></span>
1. <span data-ttu-id="163cc-118">取得 WorldAnchorStore</span><span class="sxs-lookup"><span data-stu-id="163cc-118">Get the WorldAnchorStore</span></span>
2. <span data-ttu-id="163cc-119">儲存指定識別碼的世界錨點</span><span class="sxs-lookup"><span data-stu-id="163cc-119">Save a world anchor specifying an id</span></span>
3. <span data-ttu-id="163cc-120">儲存與世界錨點相關的應用程式資料以及識別碼</span><span class="sxs-lookup"><span data-stu-id="163cc-120">Save app data relating to the world anchor along with an id</span></span>

### <a name="getting-the-worldanchorstore"></a><span data-ttu-id="163cc-121">取得 WorldAnchorStore</span><span class="sxs-lookup"><span data-stu-id="163cc-121">Getting the WorldAnchorStore</span></span>

<span data-ttu-id="163cc-122">我們會想要保留 WorldAnchorStore 的參考，讓我們知道當我們想要執行作業時，我們已經準備好了。</span><span class="sxs-lookup"><span data-stu-id="163cc-122">We will want to keep a reference to the WorldAnchorStore around so we know we are ready to go when we want to perform an operation.</span></span> <span data-ttu-id="163cc-123">因為這是非同步呼叫，可能會在啟動時立即呼叫</span><span class="sxs-lookup"><span data-stu-id="163cc-123">Since this is an async call, potentially as soon as start up, we want to call</span></span>

```
WorldAnchorStore.GetAsync(StoreLoaded);
```

<span data-ttu-id="163cc-124">StoreLoaded 在此案例中是 WorldAnchorStore 完成載入時的處理常式：</span><span class="sxs-lookup"><span data-stu-id="163cc-124">StoreLoaded in this case is our handler for when the WorldAnchorStore has completed loading:</span></span>

```
private void StoreLoaded(WorldAnchorStore store)
{
       this.store = store;
}
```

<span data-ttu-id="163cc-125">我們現在已有 WorldAnchorStore 的參考，我們將用它來儲存和載入特定的世界錨點。</span><span class="sxs-lookup"><span data-stu-id="163cc-125">We now have a reference to the WorldAnchorStore which we will use to save and load specific World Anchors.</span></span>

### <a name="saving-a-worldanchor"></a><span data-ttu-id="163cc-126">儲存 WorldAnchor</span><span class="sxs-lookup"><span data-stu-id="163cc-126">Saving a WorldAnchor</span></span>

<span data-ttu-id="163cc-127">為了節省時間，我們只需要命名要儲存的內容，並將它傳遞到我們要儲存的 WorldAnchor 中。</span><span class="sxs-lookup"><span data-stu-id="163cc-127">To save, we simply need to name what we are saving and pass it in the WorldAnchor we got before when we want to save.</span></span> <span data-ttu-id="163cc-128">注意：嘗試將兩個錨點儲存至相同的字串將會 (存放區失敗。Save 會傳回 false) 。</span><span class="sxs-lookup"><span data-stu-id="163cc-128">Note: trying to save two anchors to the same string will fail (store.Save will return false).</span></span> <span data-ttu-id="163cc-129">您需要先刪除先前的儲存，然後再儲存新的儲存：</span><span class="sxs-lookup"><span data-stu-id="163cc-129">You need to Delete the previous save before saving the new one:</span></span>

```
private void SaveGame()
{
       // Save data about holograms positioned by this world anchor
       if (!this.savedRoot) // Only Save the root once
       {
              this.savedRoot = this.store.Save("rootGameObject", anchor);
              Assert(this.savedRoot);
       }
}
```

### <a name="loading-a-worldanchor"></a><span data-ttu-id="163cc-130">載入 WorldAnchor</span><span class="sxs-lookup"><span data-stu-id="163cc-130">Loading a WorldAnchor</span></span>

<span data-ttu-id="163cc-131">並載入：</span><span class="sxs-lookup"><span data-stu-id="163cc-131">And to load:</span></span>

```
private void LoadGame()
{
       // Save data about holograms positioned by this world anchor
       this.savedRoot = this.store.Load("rootGameObject", rootGameObject);
       if (!this.savedRoot)
       {
              // We didn't actually have the game root saved! We have to re-place our objects or start over
       }
}
```

<span data-ttu-id="163cc-132">此外，我們還可以使用 store。刪除 ( # A1 以移除先前儲存和儲存的錨點。清除 ( # A3 以移除所有先前儲存的資料。</span><span class="sxs-lookup"><span data-stu-id="163cc-132">We additionally can use store.Delete() to remove an anchor we previously saved and store.Clear() to remove all previously saved data.</span></span>

### <a name="enumerating-existing-anchors"></a><span data-ttu-id="163cc-133">列舉現有錨點</span><span class="sxs-lookup"><span data-stu-id="163cc-133">Enumerating Existing Anchors</span></span>

<span data-ttu-id="163cc-134">若要探索先前儲存的錨點，請呼叫 GetAllIds。</span><span class="sxs-lookup"><span data-stu-id="163cc-134">To discover previously stored anchors, call GetAllIds.</span></span>

```
string[] ids = this.store.GetAllIds();
for (int index = 0; index < ids.Length; index++)
{
        Debug.Log(ids[index]);
}
```

## <a name="persisting-holograms-for-multiple-devices"></a><span data-ttu-id="163cc-135">保存多個裝置的全像影像</span><span class="sxs-lookup"><span data-stu-id="163cc-135">Persisting holograms for multiple devices</span></span>

<span data-ttu-id="163cc-136">您可以使用 <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure 空間錨點</a> ，從本機 WorldAnchor 建立持久的雲端錨點，讓您的應用程式可以在多個 HoloLens、IOS 和 Android 裝置上找到，即使這些裝置不會同時出現在同一時間。</span><span class="sxs-lookup"><span data-stu-id="163cc-136">You can use <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> to create a durable cloud anchor from a local WorldAnchor, which your app can then locate across multiple HoloLens, iOS and Android devices, even if those devices are not present together at the same time.</span></span>  <span data-ttu-id="163cc-137">由於雲端錨點是持續性的，因此每一段時間的多個裝置都可以看到相對於相同實體位置中錨點轉譯的內容。</span><span class="sxs-lookup"><span data-stu-id="163cc-137">Because cloud anchors are persistent, multiple devices over time can each see content rendered relative to that anchor in the same physical location.</span></span>

<span data-ttu-id="163cc-138">若要開始在 Unity 中建立共用體驗，請嘗試5分鐘的 <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">Azure 空間錨點 Unity 快速入門</a>。</span><span class="sxs-lookup"><span data-stu-id="163cc-138">To get started building shared experiences in Unity, try out the 5-minute <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">Azure Spatial Anchors Unity quickstarts</a>.</span></span>

<span data-ttu-id="163cc-139">在您啟動並執行 Azure 空間錨點之後，您可以 <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">在 Unity 中建立及尋找錨點</a>。</span><span class="sxs-lookup"><span data-stu-id="163cc-139">Once you're up and running with Azure Spatial Anchors, you can then <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">create and locate anchors in Unity</a>.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="163cc-140">下一個開發檢查點</span><span class="sxs-lookup"><span data-stu-id="163cc-140">Next Development Checkpoint</span></span>

<span data-ttu-id="163cc-141">如果您正在遵循我們所配置的 Unity 開發檢查點旅程，您將會在探索混合現實核心構成要素。</span><span class="sxs-lookup"><span data-stu-id="163cc-141">If you're following the Unity development checkpoint journey we've laid out, you're in the midst of exploring the Mixed Reality core building blocks.</span></span> <span data-ttu-id="163cc-142">您可以從這裡繼續進行下一個組建區塊：</span><span class="sxs-lookup"><span data-stu-id="163cc-142">From here, you can proceed to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="163cc-143">空間對應</span><span class="sxs-lookup"><span data-stu-id="163cc-143">Spatial mapping</span></span>](spatial-mapping-in-unity.md)

<span data-ttu-id="163cc-144">或跳至混合的現實平臺功能和 Api：</span><span class="sxs-lookup"><span data-stu-id="163cc-144">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="163cc-145">共用體驗</span><span class="sxs-lookup"><span data-stu-id="163cc-145">Shared experiences</span></span>](shared-experiences-in-unity.md)

<span data-ttu-id="163cc-146">您隨時都可以回到 [Unity 開發檢查點](unity-development-overview.md#2-core-building-blocks) 。</span><span class="sxs-lookup"><span data-stu-id="163cc-146">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="163cc-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="163cc-147">See Also</span></span>
* [<span data-ttu-id="163cc-148">空間錨點持續性</span><span class="sxs-lookup"><span data-stu-id="163cc-148">Spatial anchor persistence</span></span>](../../design/coordinate-systems.md#spatial-anchor-persistence)
* <span data-ttu-id="163cc-149"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span><span class="sxs-lookup"><span data-stu-id="163cc-149"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span></span>
* <span data-ttu-id="163cc-150"><a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">適用于 Unity 的 Azure 空間錨點 SDK</a></span><span class="sxs-lookup"><span data-stu-id="163cc-150"><a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure Spatial Anchors SDK for Unity</a></span></span>
