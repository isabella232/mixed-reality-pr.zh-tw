---
title: 啟用住家內的 3D 模型位置
description: 瞭解如何將您的網站或應用程式的3D 模型放在 Windows Mixed Reality 首頁。
author: thmignon
ms.author: thmignon
ms.date: 05/04/2018
ms.topic: article
keywords: 3D，型號，放置於家裡、地點、世界、模型化、混合實境首頁、web、應用程式、混合現實耳機、windows mixed reality 耳機、虛擬實境耳機
ms.openlocfilehash: c92ba7a3242b618b9ef9cef01ae400cf4dbf36b2
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2021
ms.locfileid: "98010098"
---
# <a name="enable-placement-of-3d-models-in-the-mixed-reality-home"></a><span data-ttu-id="065f8-104">在混合實境首頁中啟用 3D 模型的放置</span><span class="sxs-lookup"><span data-stu-id="065f8-104">Enable placement of 3D models in the mixed reality home</span></span>

> [!NOTE]
> <span data-ttu-id="065f8-105">這項功能已新增為 [Windows 10 2018 年4月更新](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/release-notes-april-2018)的一部分。</span><span class="sxs-lookup"><span data-stu-id="065f8-105">This feature was added as part of the [Windows 10 April 2018 Update](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/release-notes-april-2018).</span></span> <span data-ttu-id="065f8-106">較舊版本的 Windows 與這項功能不相容。</span><span class="sxs-lookup"><span data-stu-id="065f8-106">Older versions of Windows are not compatible with this feature.</span></span>

<span data-ttu-id="065f8-107">[Windows Mixed Reality home](../discover/navigating-the-windows-mixed-reality-home.md)是使用者在啟動應用程式之前所居住的起點。</span><span class="sxs-lookup"><span data-stu-id="065f8-107">The [Windows Mixed Reality home](../discover/navigating-the-windows-mixed-reality-home.md) is the starting point where users land before launching applications.</span></span> <span data-ttu-id="065f8-108">在某些案例中，2D 應用程式 (像是全像全像影像應用程式) 將3D 模型以裝飾的形式直接放入混合實境首頁，或以完整3D 進行進一步檢查。</span><span class="sxs-lookup"><span data-stu-id="065f8-108">In some scenarios, 2D apps (like the Holograms app) enable placement of 3D models directly into the mixed reality home as decorations or for further inspection in full 3D.</span></span> <span data-ttu-id="065f8-109">「 *新增模型」通訊協定* 可讓您將來自您網站或應用程式的3d 模型直接傳送到 Windows Mixed Reality 首頁，它會保存為 [3d 應用程式啟動器](3d-app-launcher-design-guidance.md)、2d 應用程式和全像影像。</span><span class="sxs-lookup"><span data-stu-id="065f8-109">The *add model protocol* allows you to send a 3D model from your website or application directly into the Windows Mixed Reality home, where it will persist like [3D app launchers](3d-app-launcher-design-guidance.md), 2D apps, and holograms.</span></span> 

<span data-ttu-id="065f8-110">例如，如果您要開發的應用程式會呈現3D 傢俱的目錄來設計空間，請使用「 *新增模型」通訊協定* ，讓使用者能夠從類別目錄放置這些3d 傢俱模型。</span><span class="sxs-lookup"><span data-stu-id="065f8-110">For example, if you're developing an application that surfaces a catalog of 3D furniture for designing a space, use the *add model protocol* to allow users to place those 3D furniture models from the catalog.</span></span> <span data-ttu-id="065f8-111">一旦放在世界中，使用者就可以移動、調整大小和移除這些3D 模型，就像家裡的其他全息圖一樣。</span><span class="sxs-lookup"><span data-stu-id="065f8-111">Once placed in the world, users can move, resize, and remove these 3D models just like other holograms in the home.</span></span> <span data-ttu-id="065f8-112">本文概述如何實行「 *新增模型」通訊協定* ，讓使用者能夠從您的應用程式或 Web 使用3d 物件裝飾其世界。</span><span class="sxs-lookup"><span data-stu-id="065f8-112">This article provides an overview of implementing the *add model protocol* for enabling users to decorate their world with 3D objects from your app or the web.</span></span>

## <a name="device-support"></a><span data-ttu-id="065f8-113">裝置支援</span><span class="sxs-lookup"><span data-stu-id="065f8-113">Device support</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="065f8-114"><strong>功能</strong></span><span class="sxs-lookup"><span data-stu-id="065f8-114"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="065f8-115"><a href="../hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="065f8-115"><a href="../hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="065f8-116"><a href="../discover/immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></span><span class="sxs-lookup"><span data-stu-id="065f8-116"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="065f8-117">新增模型通訊協定</span><span class="sxs-lookup"><span data-stu-id="065f8-117">Add model protocol</span></span></td>
        <td><span data-ttu-id="065f8-118">✔️</span><span class="sxs-lookup"><span data-stu-id="065f8-118">✔️</span></span></td>
        <td><span data-ttu-id="065f8-119">✔️</span><span class="sxs-lookup"><span data-stu-id="065f8-119">✔️</span></span></td>
    </tr>
</table>

## <a name="the-basics"></a><span data-ttu-id="065f8-120">基本概念</span><span class="sxs-lookup"><span data-stu-id="065f8-120">The basics</span></span>

<span data-ttu-id="065f8-121">有兩個步驟可讓您在 Windows Mixed Reality 首頁中放置3D 模型：</span><span class="sxs-lookup"><span data-stu-id="065f8-121">There are two steps to enabling the placement of 3D models in the Windows Mixed Reality home:</span></span>
1. <span data-ttu-id="065f8-122">[確定您的3d 模型與 Windows Mixed Reality 首頁相容](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)。</span><span class="sxs-lookup"><span data-stu-id="065f8-122">[Ensure your 3D model is compatible with the Windows Mixed Reality home](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md).</span></span>
2. <span data-ttu-id="065f8-123"> (本文) ，在您的應用程式或網頁中執行「 *新增模型」通訊協定* 。</span><span class="sxs-lookup"><span data-stu-id="065f8-123">Implement the *add model protocol* in your application or webpage (this article).</span></span>

## <a name="implementing-the-add-model-protocol"></a><span data-ttu-id="065f8-124">執行 *新增模型通訊協定*</span><span class="sxs-lookup"><span data-stu-id="065f8-124">Implementing the *add model protocol*</span></span>

<span data-ttu-id="065f8-125">當您有 [相容的3d 模型](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)之後，您可以從任何網頁或應用程式啟用下列 URI，以執行「 *新增模型」通訊協定* ：</span><span class="sxs-lookup"><span data-stu-id="065f8-125">Once you have a [compatible 3D model](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md), you can implement the *add model protocol* by activating the following URI from any webpage or application:</span></span>

```
ms-mixedreality:addmodel?uri=<Path to a .glb 3D model either local or remote>
```

<span data-ttu-id="065f8-126">如果 URI 指向遠端資源，則會自動下載並放在首頁中。</span><span class="sxs-lookup"><span data-stu-id="065f8-126">If the URI points to a remote resource, then it will automatically be downloaded and placed in the home.</span></span> <span data-ttu-id="065f8-127">本機資源將會先複製到混合實境首頁的應用程式資料夾，然後再放在首頁中。</span><span class="sxs-lookup"><span data-stu-id="065f8-127">Local resources will be copied to the mixed reality home's app data folder before being placed in the home.</span></span> <span data-ttu-id="065f8-128">我們建議您設計體驗，以考慮使用者可能會藉由隱藏按鈕或在可能情況下停用的較舊版本 Windows，來執行不支援這項功能的舊版 Windows。</span><span class="sxs-lookup"><span data-stu-id="065f8-128">We recommend designing your experience to account for scenarios where the user might be running an older version of Windows that doesn't support this feature by hiding the button or disabling it if possible.</span></span> 

### <a name="invoking-the-add-model-protocol-from-a-universal-windows-platform-app"></a><span data-ttu-id="065f8-129">從通用 Windows 平臺應用程式叫用 *新增模型通訊協定* ：</span><span class="sxs-lookup"><span data-stu-id="065f8-129">Invoking the *add model protocol* from a Universal Windows Platform app:</span></span>

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

### <a name="invoking-the-add-model-protocol-from-a-webpage"></a><span data-ttu-id="065f8-130">從網頁叫用 *新增模型通訊協定* ：</span><span class="sxs-lookup"><span data-stu-id="065f8-130">Invoking the *add model protocol* from a webpage:</span></span>

```html
<a class="btn btn-default" href="ms-mixedreality:addModel?uri=sample.glb"> Place 3D Model </a>
```

## <a name="considerations-for-immersive-vr-headsets"></a><span data-ttu-id="065f8-131">沉浸式 (VR) 耳機的考慮</span><span class="sxs-lookup"><span data-stu-id="065f8-131">Considerations for immersive (VR) headsets</span></span>

* <span data-ttu-id="065f8-132">針對沉浸式 (VR) 耳機，混合實境入口不需要在叫用 *新增模型通訊協定* 之前執行。</span><span class="sxs-lookup"><span data-stu-id="065f8-132">For immersive (VR) headsets, the Mixed Reality Portal doesn't have to be running before invoking the *add model protocol*.</span></span> <span data-ttu-id="065f8-133">在此情況下，「 *新增模型」通訊協定* 將會啟動混合實境入口，並在您抵達混合實境首頁之後，直接將物件放在耳機所要查看的位置。</span><span class="sxs-lookup"><span data-stu-id="065f8-133">In this case, the *add model protocol* will launch the Mixed Reality Portal and place the object directly where the headset is looking once you arrive in the mixed reality home.</span></span> 
* <span data-ttu-id="065f8-134">從已執行混合實境入口的桌面叫用 *新增模型通訊協定* 時，請確定耳機為「喚醒」。</span><span class="sxs-lookup"><span data-stu-id="065f8-134">When invoking the *add model protocol* from the desktop with the Mixed Reality Portal already running, ensure that the headset is "awake".</span></span> <span data-ttu-id="065f8-135">如果沒有，則放置將不會成功。</span><span class="sxs-lookup"><span data-stu-id="065f8-135">If not, the placement won't succeed.</span></span> 

## <a name="see-also"></a><span data-ttu-id="065f8-136">請參閱</span><span class="sxs-lookup"><span data-stu-id="065f8-136">See also</span></span>

* [<span data-ttu-id="065f8-137">建立要在 Windows Mixed Reality 首頁中使用的3D 模型</span><span class="sxs-lookup"><span data-stu-id="065f8-137">Creating 3D models for use in the Windows Mixed Reality home</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [<span data-ttu-id="065f8-138">瀏覽 Windows Mixed Reality 住家</span><span class="sxs-lookup"><span data-stu-id="065f8-138">Navigating the Windows Mixed Reality home</span></span>](../discover/navigating-the-windows-mixed-reality-home.md)
