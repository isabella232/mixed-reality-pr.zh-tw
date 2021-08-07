---
title: 啟用住家內的 3D 模型位置
description: 瞭解如何將您的網站或應用程式的3d 模型放在 Windows Mixed Reality 首頁。
author: thmignon
ms.author: thmignon
ms.date: 05/04/2018
ms.topic: article
keywords: 3D，型號，放置於家裡、地點、世界、模型化、混合實境首頁、web、應用程式、混合現實耳機、windows mixed reality 耳機、虛擬實境耳機
ms.openlocfilehash: 29761cb2a8725221a3be90187488cb13bf6643e4ff334a1edca73e633e7b1d4c
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2021
ms.locfileid: "115186794"
---
# <a name="enable-placement-of-3d-models-in-the-mixed-reality-home"></a>在混合實境首頁中啟用 3D 模型的放置

> [!NOTE]
> 這項功能已在[2018 年4月更新的 Windows 10](/windows/mixed-reality/enthusiast-guide/release-notes-april-2018)中新增。 較舊版本的 Windows 與這項功能不相容。

[Windows Mixed Reality home](../discover/navigating-the-windows-mixed-reality-home.md)是使用者在啟動應用程式之前所居住的起點。 在某些案例中，2d 應用程式 (類似全像投影應用程式) 讓3d 模型以裝飾的形式直接放入混合實境首頁，或在完整的3d 中進行進一步的檢查。 「*新增模型」通訊協定* 可讓您將來自您網站或應用程式的3d 模型直接傳送到 Windows Mixed Reality 首頁，它會保存為 [3d 應用程式啟動器](3d-app-launcher-design-guidance.md)、2d 應用程式和全像影像。 

例如，如果您要開發的應用程式會呈現3D 傢俱的目錄來設計空間，請使用「 *新增模型」通訊協定* ，讓使用者能夠從類別目錄放置這些3d 傢俱模型。 一旦放在世界中，使用者就可以移動、調整大小和移除這些3D 模型，就像家裡的其他全息圖一樣。 本文概述如何實行「 *新增模型」通訊協定* ，讓使用者能夠從您的應用程式或 Web 使用3d 物件裝飾其世界。

## <a name="device-support"></a>裝置支援

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><strong>功能</strong></td>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></td>
        <td><a href="../discover/immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></td>
    </tr>
     <tr>
        <td>新增模型通訊協定</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
</table>

## <a name="the-basics"></a>基本概念

有兩個步驟可讓您在 Windows Mixed Reality 首頁中放置3d 模型：
1. [確定您的3d 模型與 Windows Mixed Reality 首頁相容](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)。
2.  (本文) ，在您的應用程式或網頁中執行「 *新增模型」通訊協定* 。

## <a name="implementing-the-add-model-protocol"></a>執行 *新增模型通訊協定*

當您有 [相容的3d 模型](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)之後，您可以從任何網頁或應用程式啟用下列 URI，以執行「 *新增模型」通訊協定* ：

```
ms-mixedreality:addmodel?uri=<Path to a .glb 3D model either local or remote>
```

如果 URI 指向遠端資源，則會自動下載並放在首頁中。 本機資源將會先複製到混合實境首頁的應用程式資料夾，然後再放在首頁中。 我們建議您設計體驗，以考慮使用者可能會藉由隱藏按鈕或在可能情況下停用的方式，來執行不支援這項功能的舊版 Windows。 

### <a name="invoking-the-add-model-protocol-from-a-universal-windows-platform-app"></a>從通用 Windows 平臺應用程式叫用 *新增模型通訊協定*：

```C#
private async void launchURI_Click(object sender, RoutedEventArgs e)
{
   // Define the add model URI
   var uriAddModel = new Uri(@"ms-mixedreality:addModel?uri=sample.glb");

   // Launch the URI to invoke the placement
   var success = await Windows.System.Launcher.LaunchUriAsync(uriAddModel);

   if (success)
   {
      // URI launched
   }
   else
   {
      // URI launch failed
   }
}
```

### <a name="invoking-the-add-model-protocol-from-a-webpage"></a>從網頁叫用 *新增模型通訊協定* ：

```html
<a class="btn btn-default" href="ms-mixedreality:addModel?uri=sample.glb"> Place 3D Model </a>
```

## <a name="considerations-for-immersive-vr-headsets"></a>沉浸式 (VR) 耳機的考慮

* 針對沉浸式 (VR) 耳機，混合實境入口不需要在叫用 *新增模型通訊協定* 之前執行。 在此情況下，「 *新增模型」通訊協定* 將會啟動混合實境入口，並在您抵達混合實境首頁之後，直接將物件放在耳機所要查看的位置。 
* 從已執行混合實境入口的桌面叫用 *新增模型通訊協定* 時，請確定耳機為「喚醒」。 如果沒有，則放置將不會成功。 

## <a name="see-also"></a>另請參閱

* [建立要在 Windows Mixed Reality 首頁中使用的3d 模型](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [瀏覽 Windows Mixed Reality 住家](../discover/navigating-the-windows-mixed-reality-home.md)