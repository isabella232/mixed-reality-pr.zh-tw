---
title: 實作 3D 應用程式啟動器 (UWP 應用程式)
description: 如何建立 Windows Mixed Reality UWP 應用程式和遊戲的3D 應用程式啟動器和標誌， (透過 Microsoft Store) （包括 HoloLens 和沉浸式 (VR) 耳機）散佈。
author: thmignon
ms.author: thmignon
ms.date: 07/12/2018
ms.topic: article
keywords: 3D、標誌、圖示、模型、啟動器、3D 啟動器、磚、即時立方體、深層連結、secondarytile、次要磚、UWP、混合現實耳機、windows mixed reality 耳機、虛擬實境耳機、XML、周框方塊、unity
ms.openlocfilehash: 926d0b3bb337517b65986f85f6977b3dd1975735
ms.sourcegitcommit: 4f3ef057a285be2e260615e5d6c41f00d15d08f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2020
ms.locfileid: "94703194"
---
# <a name="implement-3d-app-launchers-uwp-apps"></a>實作 3D 應用程式啟動器 (UWP 應用程式)

> [!NOTE]
> 這項功能是在2017的「建立者」更新中新增的， (RS3) 適用于沉浸式耳機，並支援 HoloLens 與 Windows 10 2018 年4月更新。 確定您的應用程式是以10.0.16299 的版本為目標，在沉浸式耳機上使用大於或等於的 Windows SDK 版本，並在 HoloLens 上進行10.0.17125。 您可以在 [這裡](https://developer.microsoft.com/windows/downloads/windows-10-sdk)找到最新的 Windows SDK。

[Windows Mixed Reality home](../discover/navigating-the-windows-mixed-reality-home.md)是使用者在啟動應用程式之前所居住的起點。 針對 Windows Mixed Reality 建立 UWP 應用程式時，根據預設，應用程式會以2D 平板的形式啟動，並使用其應用程式的標誌。 開發 Windows Mixed Reality 的體驗時，可以選擇性地定義3D 啟動器以覆寫應用程式的預設2D 啟動器。 一般而言，建議使用3D 啟動器來啟動將使用者移出 Windows Mixed Reality 首頁的沉浸式應用程式，而當應用程式已啟動時，建議使用預設2D 啟動器。 您也可以建立 [3d 深層連結 (secondaryTile) ](#3d-deep-links-secondarytiles) 作為 2d UWP 應用程式中內容的3d 啟動器。

>[!VIDEO https://www.youtube.com/embed/TxIslHsEXno]

## <a name="3d-app-launcher-creation-process"></a>3D 應用程式啟動器建立流程

建立3D 應用程式啟動器有3個步驟：
1. [設計和 concepting](3d-app-launcher-design-guidance.md)
2. [模型化和匯出](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
3.  (本文中將其整合到您的應用程式) 

要做為應用程式的啟動器使用的3D 資產，應使用 [Windows Mixed Reality 撰寫指導方針](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) ，以確保相容性。 無法符合此撰寫規格的資產將不會在 Windows Mixed Reality 首頁轉譯。

## <a name="configuring-the-3d-launcher"></a>設定3D 啟動器

在 Visual Studio 中建立新的專案時，它會建立一個顯示 app 名稱和標誌的簡單預設磚。 若要使用自訂3D 模型來取代此2D 標記法，請編輯應用程式的應用程式資訊清單，以在預設的磚定義中包含 "MixedRealityModel" 元素。 若要還原成2D 啟動程式，只需從資訊清單中移除 MixedRealityModel 定義。

### <a name="xml"></a>XML

首先，找出目前專案中的應用程式套件資訊清單。 根據預設，資訊清單會命名為 package.appxmanifest。 如果您使用 Visual Studio，請以滑鼠右鍵按一下方案檢視器中的資訊清單，然後選取 [ **視圖來源** ] 以開啟 xml 進行編輯。 

在資訊清單頂端，加入 uap5 架構，並將它包含為可忽略的命名空間：

```xml
<Package xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest" 
         xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10" 
         xmlns:uap2="http://schemas.microsoft.com/appx/manifest/uap/windows10/2" 
         xmlns:uap5="http://schemas.microsoft.com/appx/manifest/uap/windows10/5"
         IgnorableNamespaces="uap uap2 uap5 mp"
         xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10">
```

接下來，在您應用程式的預設磚中指定 "MixedRealityModel"：

```xml
<Applications>
    <Application Id="App"
      Executable="$targetnametoken$.exe"
      EntryPoint="ExampleApp.App">
      <uap:VisualElements
        DisplayName="ExampleApp"
        Square150x150Logo="Assets\Logo.png"
        Square44x44Logo="Assets\SmallLogo.png"
        Description="ExampleApp"
        BackgroundColor="#464646">
        <uap:DefaultTile Wide310x150Logo="Assets\WideLogo.png" >
          <uap5:MixedRealityModel Path="Assets\My3DTile.glb" />
        </uap:DefaultTile>
        <uap:SplashScreen Image="Assets\SplashScreen.png" />
      </uap:VisualElements>
    </Application>
</Applications>
```

MixedRealityModel 元素接受指向儲存在應用程式套件中的3D 資產的檔案路徑。 目前只支援使用 glb 檔案格式所提供的3D 模型，並針對 [Windows Mixed Reality 3d 資產撰寫指示](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) 來撰寫。 資產必須儲存在應用程式套件中，而且目前不支援動畫。 如果 "Path" 參數保留空白，Windows 將會顯示2D 的平板，而不是3D 啟動器。 **注意：** 在建立並執行您的應用程式之前，必須先將 glb 資產標示為組建設定中的「內容」。


![在您的 [方案 glb] 中選取 []，並使用 [屬性] 區段，在組建設定中將其標示為 [內容]](images/buildsetting-content-300px.png)<br>
*在您的 [方案 glb] 中選取 []，並使用 [屬性] 區段，在組建設定中將其標示為 [內容]*

### <a name="bounding-box"></a>週框方塊

您可以使用周框方塊，選擇性地在物件周圍加入額外的緩衝區區域。 您可以使用中心點和範圍來指定周框方塊，以表示從周框方塊中央到其邊緣沿著每個軸的距離。 周框方塊的單位可以對應至1個 unit = 1 個計量。 如果未提供周框方塊，則會自動將它調整為物件的網格。 如果提供的周框方塊小於模型，則會調整大小以符合網格。

周框方塊屬性的支援會隨附于 Windows RS4 update 做為 MixedRealityModel 元素上的屬性。 若要在應用程式資訊清單頂端先定義周框方塊，請新增 uap6 架構，並將其包含為可忽略的命名空間：

```xml
<Package xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest" 
         xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10" 
         xmlns:uap2="http://schemas.microsoft.com/appx/manifest/uap/windows10/2" 
         xmlns:uap5="http://schemas.microsoft.com/appx/manifest/uap/windows10/5"
         xmlns:uap6="http://schemas.microsoft.com/appx/manifest/uap/windows10/6"
         IgnorableNamespaces="uap uap2 uap5 uap6 mp"
         xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10">
```
接下來，在 MixedRealityModel 上設定 SpatialBoundingBox 屬性，以定義周框方塊： 

```xml
        <uap:DefaultTile Wide310x150Logo="Assets\WideLogo.png" >
          <uap5:MixedRealityModel Path="Assets\My3DTile.glb">
              <uap6:SpatialBoundingBox  Center=”1,-2,3” Extents=”1,2,3” />
          </uap5:MixedRealityModel>
        </uap:DefaultTile>
```

### <a name="using-unity"></a>使用 Unity

使用 Unity 時，必須先在 Visual Studio 中建立並開啟專案，然後才能編輯應用程式資訊清單。 

>[!NOTE]
>從 Unity 建立和部署新的 Visual Studio 解決方案時，必須在資訊清單中重新定義3D 啟動器。

## <a name="3d-deep-links-secondarytiles"></a>3D 深層連結 (secondaryTiles) 

> [!NOTE]
> 這項功能已新增為2017秋季建立者更新的一部分 (RS3) 適用于沉浸式 (VR) 耳機，以及屬於2018年4月更新 (RS4) 的 HoloLens。 確定您的應用程式是以10.0.16299 在沉浸式 (VR) 耳機和10.0.17125 上的版本為目標，而該版本的 Windows SDK 大於或等於。 您可以在 [這裡](https://developer.microsoft.com/windows/downloads/windows-10-sdk)找到最新的 Windows SDK。

>[!IMPORTANT]
>3D 深層連結 (secondaryTiles) 僅適用于 2D UWP 應用程式。 不過，您可以建立 [3d 應用程式啟動器](implementing-3d-app-launchers.md) ，從 Windows Mixed Reality 首頁啟動專屬應用程式。

您可以藉由將3D 模型從您的應用程式放入 [Windows Mixed Reality 首頁](../discover/navigating-the-windows-mixed-reality-home.md) 作為2d 應用程式內的內容深層連結（如同 Windows [開始] 功能表上的 [2d 次要磚](https://docs.microsoft.com/windows/uwp/controls-and-patterns/tiles-and-notifications-secondary-tiles) ），來增強您的2d 應用程式以進行 Windows Mixed Reality。 例如，您可以建立可直接連結至360相片檢視器應用程式的360° photospheres，或讓使用者從開啟有關作者詳細資料頁面的資產集合中放置3D 內容。 這些只是利用3D 內容擴充2D 應用程式功能的幾種方式。

### <a name="creating-a-3d-secondarytile"></a>建立 3D "secondaryTile"

您可以在建立時定義混合的現實模型，藉由使用 "secondaryTiles" 在應用程式中放置3D 內容。 混合現實模型的建立方式是在您的應用程式套件中參考3D 資產，並選擇性地定義周框方塊。 

> [!NOTE]
> 目前不支援在專屬視圖內建立 "secondaryTiles"。

```cs
using Windows.UI.StartScreen;
using Windows.Foundation.Numerics;
using Windows.Perception.Spatial;

// Initialize the tile
SecondaryTile tile = new SecondaryTile("myTileId")
{
    DisplayName = "My Tile",
    Arguments = "myArgs"
};

tile.VisualElements.Square150x150Logo = new Uri("ms-appx:///Assets/MyTile/Square150x150Logo.png");

//Assign 3D model (only ms-appx and ms-appdata are allowed)
TileMixedRealityModel model = tile.VisualElements.MixedRealityModel;
model.Uri = new Uri("ms-appx:///Assets/MyTile/MixedRealityModel.glb");
model.ActivationBehavior = TileMixedRealityModelActivationBehavior.Default;
model.BoundingBox = new SpatialBoundingBox
{
    Center = new Vector3 { X = 1, Y = 0, Z = 0 },
    Extents = new Vector3 { X = 3, Y = 5, Z = 4 }
};

// And place it
await tile.RequestCreateAsync();
```

### <a name="bounding-box"></a>週框方塊

您可以使用周框方塊，在物件周圍加入額外的緩衝區區域。 您可以使用中心點和範圍來指定周框方塊，以表示從周框方塊中央到其邊緣沿著每個軸的距離。 周框方塊的單位可以對應至1個 unit = 1 個計量。 如果未提供周框方塊，則會自動將它調整為物件的網格。 如果提供的周框方塊小於模型，則會調整大小以符合網格。

### <a name="activation-behavior"></a>啟用行為

> [!NOTE]
> Windows RS4 update 將支援這項功能。 如果您打算使用這項功能，請確定您的應用程式的目標版本 Windows SDK 大於或等於10.0.17125

您可以定義 3D secondaryTile 的啟用行為，以控制使用者選取時的回應方式。 這可以用來將3D 物件放在純資訊或裝飾性的混合現實首頁中。 以下是支援的啟用行為類型：
1. 預設值：當使用者選取 3D secondaryTile 時，應用程式會啟用
2. 無：當使用者選取 3D secondaryTile 時，不會發生任何動作，且不會啟動應用程式。

### <a name="obtaining-and-updating-an-existing-secondarytile"></a>取得和更新現有的 "secondaryTile"

開發人員可以取回其現有的次要磚清單，其中包括先前指定的屬性。 它們也可以藉由變更值，然後呼叫 >updateasync ( # A1 來更新屬性。

```cs
// Grab the existing secondary tile
SecondaryTile tile = (await SecondaryTile.FindAllAsync()).First();

Uri updatedUri = new Uri("ms-appdata:///local/MixedRealityUpdated.glb");

// See if the model needs updating
if (!tile.VisualElements.MixedRealityModel.Uri.Equals(updatedUri))
{
    // Update it
    tile.VisualElements.MixedRealityModel.Uri = updatedUri;

    // And apply the changes
    await tile.UpdateAsync();
}
```

### <a name="checking-that-the-user-is-in-windows-mixed-reality"></a>檢查使用者是否位於 Windows Mixed Reality

只有在 Windows Mixed Reality 耳機中顯示視圖時，才可以建立3D 深層連結 (secondaryTiles) 。 當您的觀點未顯示在 Windows Mixed Reality 耳機時，建議您隱藏進入點或顯示錯誤訊息，以正常方式處理此問題。 您可以查詢 [IsCurrentViewPresentedOnHolographic ( # B1 ](https://docs.microsoft.com/uwp/api/windows.applicationmodel.preview.holographic.holographicapplicationpreview#Windows_ApplicationModel_Preview_Holographic_HolographicApplicationPreview_IsCurrentViewPresentedOnHolographicDisplay_)來檢查這一點。

## <a name="tile-notifications"></a>磚通知

磚通知目前不支援傳送含3D 資產的更新。 這表示開發人員將無法執行下列動作：
* 推播通知
* 定期輪詢
* 排程的通知

如需其他磚功能和屬性的詳細資訊，以及它們如何用於2D 磚，請參閱 [UWP 應用程式的磚檔](https://docs.microsoft.com/windows/uwp/controls-and-patterns/tiles-and-notifications-creating-tiles)。

## <a name="see-also"></a>另請參閱

* 包含3D 應用程式啟動器的[混合現實模型範例](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/MixedRealityModel)。
* [3D 應用程式啟動程式設計指引](3d-app-launcher-design-guidance.md)
* [建立要在 Windows Mixed Reality 首頁中使用的3D 模型](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [ (Win32 應用程式執行3D 應用程式啟動器) ](implementing-3d-app-launchers-win32.md)
* [瀏覽 Windows Mixed Reality 住家](../discover/navigating-the-windows-mixed-reality-home.md)
