---
title: Unity 中的持續性
description: 持續性可讓您的使用者在想要的地方釘選個別的全像影像，然後在應用程式的許多用途之後找出它。
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: HoloLens、持續性、Unity、混合現實耳機、windows mixed reality 耳機、虛擬實境耳機
ms.openlocfilehash: 9283191c024cbe33ecda3946a4e9bcbd5f3708c21a3578484b547207ee70a49b
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2021
ms.locfileid: "115208968"
---
# <a name="persistence-in-unity"></a>Unity 中的持續性

**命名空間：** *UnityEngine. XR*<br>
**類別：** *WorldAnchorStore*

WorldAnchorStore 是建立全像攝影體驗的關鍵，也就是在應用程式的各個實例上，全像地方都有特定的真實世界位置。 然後，使用者可以在想要的任何地方釘選個別的全像

## <a name="how-to-persist-holograms-across-sessions"></a>如何跨會話保存全息

WorldAnchorStore 可讓您跨會話保存 WorldAnchor 的位置。 若要實際跨會話保存全像投影，您必須個別追蹤使用特定世界錨點的 Gameobject。 建立具有世界錨點的 GameObject 根目錄通常是合理的，並讓子影像以本機位置位移錨定。

若要從先前的會話載入全息影像：
1. 取得 WorldAnchorStore
2. 載入與世界錨點相關的應用程式資料，以提供您世界錨點的識別碼
3. 從識別碼載入世界錨點

若要在未來的會話中儲存影像：
1. 取得 WorldAnchorStore
2. 儲存指定識別碼的世界錨點
3. 儲存與世界錨點相關的應用程式資料以及識別碼

### <a name="getting-the-worldanchorstore"></a>取得 WorldAnchorStore

您會想要保留 WorldAnchorStore 的參考，讓您知道它準備好執行作業的時間。 因為這是非同步呼叫，可能會在啟動時立即執行，您想要呼叫：

```
WorldAnchorStore.GetAsync(StoreLoaded);
```

StoreLoaded 在此案例中是 WorldAnchorStore 完成載入時的處理常式：

```
private void StoreLoaded(WorldAnchorStore store)
{
       this.store = store;
}
```

我們現在已有 WorldAnchorStore 的參考，我們將用它來儲存和載入特定的世界錨點。

### <a name="saving-a-worldanchor"></a>儲存 WorldAnchor

為了節省時間，我們只需要命名要儲存的內容，並將它傳遞到我們要儲存的 WorldAnchor 中。 注意：嘗試將兩個錨點儲存至相同的字串將會 (存放區失敗。Save 會傳回 false) 。 儲存新的儲存之前，請先刪除先前的儲存：

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

### <a name="loading-a-worldanchor"></a>載入 WorldAnchor

並載入：

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

此外，我們還可以使用 store。刪除 () 以移除先前儲存和儲存的錨點。清除 () 移除先前儲存的所有資料。

### <a name="enumerating-existing-anchors"></a>列舉現有錨點

若要探索先前儲存的錨點，請呼叫 GetAllIds。

```
string[] ids = this.store.GetAllIds();
for (int index = 0; index < ids.Length; index++)
{
        Debug.Log(ids[index]);
}
```

## <a name="persisting-holograms-for-multiple-devices"></a>保存多個裝置的全像影像

您可以使用<a href="/azure/spatial-anchors/overview" target="_blank">Azure 空間錨點</a>，從本機 WorldAnchor 建立持久的雲端錨點，讓您的應用程式可以在多個 HoloLens、iOS 和 Android 裝置上找到，即使這些裝置不會同時出現在同一時間。  由於雲端錨點是持續性的，因此每一段時間的多個裝置都可以看到相對於相同實體位置中錨點轉譯的內容。

若要開始在 Unity 中建立共用體驗，請嘗試5分鐘的 <a href="/azure/spatial-anchors/unity-overview" target="_blank">Azure 空間錨點 Unity 快速入門</a>。

在您啟動並執行 Azure 空間錨點之後，您可以 <a href="/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">在 Unity 中建立及尋找錨點</a>。

## <a name="next-development-checkpoint"></a>下一個開發檢查點

如果您正在遵循我們所配置的 Unity 開發檢查點旅程，您將會在探索混合現實核心構成要素。 接下來，您可以繼續進行下一個建置組塊：

> [!div class="nextstepaction"]
> [空間對應](spatial-mapping-in-unity.md)

或者，直接跳到混合實境平台功能和 API 的主題：

> [!div class="nextstepaction"]
> [共用體驗](shared-experiences-in-unity.md)

您可以隨時回到 [Unity 開發檢查點](unity-development-overview.md#2-core-building-blocks)。

## <a name="see-also"></a>另請參閱
* [空間錨點持續性](../../design/coordinate-systems.md#spatial-anchor-persistence)
* <a href="/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>
* <a href="/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">適用于 Unity 的 Azure 空間錨點 SDK</a>