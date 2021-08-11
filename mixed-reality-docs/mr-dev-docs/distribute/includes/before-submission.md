---
ms.openlocfilehash: d811df7f0dbd7c44a5135ed82c9061e19c1335e3e23dda6398562317f7ee8861
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2021
ms.locfileid: "115198779"
---
# <a name="hololens"></a>[HoloLens](#tab/hololens)

如果您有 HoloLens 的應用程式，請從下表中選擇您慣用的[散發選項](../distribute-overview.md#distribution-options)。 如果您要發佈至 Microsoft Store，可以選擇新增[應用程式內購買](../in-app-purchases.md)來銷售您的內容。

# <a name="windows-mixed-reality"></a>[Windows Mixed Reality](#tab/wmr)

如果您正在使用以 Windows Mixed Reality 耳機為目標的沉浸式應用程式，請建立3d 應用程式啟動器，然後從下表中選擇您慣用的[散發選項](../distribute-overview.md#distribution-options)。 如果您要發佈至 Microsoft Store，可以選擇新增[應用程式內購買](../in-app-purchases.md)來銷售您的內容。

### <a name="designing-3d-app-launchers-for-vr"></a>設計適用于 VR 的3D 應用程式啟動器 

當使用者在沉浸式耳機上出現時，3d 應用程式啟動器會顯示為 Windows Mixed Reality home 環境中的物件。 您可以使用這些物件來建立和自訂這些物件，但建議您先從我們的 [設計指引](../3d-app-launcher-design-guidance.md) 文章著手，以取得良好設計實務的停止回應，包括調整、類型、色彩選擇、紋理和上方，使其在虛擬環境中脫穎而出。

### <a name="modeling-and-exporting-3d-app-launchers"></a>模型化和匯出3D 應用程式啟動器

設定好3d 應用程式啟動程式的概念之後，您必須確定它符合 Microsoft Store 需求，包括資產檔案格式、三角形計數、材質大小、動畫長度和資產優化。 此程式可能具有高度的技術，因此建議使用我們的 [3d 模型建立](../creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) 文章來檢查所有方塊。 不符合此撰寫規格的資產不會在 Windows Mixed Reality 首頁轉譯。

### <a name="adding-3d-app-launchers-in-your-apps"></a>在您的應用程式中新增3D 應用程式啟動器

確定您的3d 應用程式啟動器符合 Windows Mixed Reality 撰寫指導方針之後，您可以在 Windows Mixed Reality home 環境中，使用它來覆寫應用程式的預設2d 啟動器。 將3D 應用程式啟動器整合到您的應用程式的程式取決於您所開發的應用程式類型：

* [UWP 應用程式](../implementing-3d-app-launchers.md)
* [Win32 應用程式](../implementing-3d-app-launchers-win32.md)

### <a name="optional-placing-3d-models-in-the-windows-mixed-reality-home"></a>參數將3d 模型放在 Windows Mixed Reality 首頁

另外還有一些2d 應用程式可讓您將3d 模型直接放入 Windows Mixed Reality 首頁作為裝飾，或是完整的3d 檢查。 「新增模型」通訊協定可讓您將來自網站或應用程式的3d 模型傳送至 Windows Mixed Reality 首頁，它會保存為3d 應用程式啟動器、2d 應用程式和全像影像。 查看[如何在 Windows Mixed Reality 首頁中放置3d 模型](../enable-placement-of-3d-models-in-the-home.md)，以尋找更多詳細資料，以及如何讓您的應用程式更具效率的指示。