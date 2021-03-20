---
title: Unreal 中的 QR 代碼
description: 了解如何在 Unreal 混合實境應用程式中設定、使用及追蹤 QR 代碼。
author: hferrone
ms.author: v-hferrone
ms.date: 12/9/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 混合實境, 開發, 功能, 文件, 指南, 全像投影, qr 代碼, 混合實境頭戴式裝置, windows 混合實境頭戴式裝置, 虛擬實境頭戴式裝置
ms.openlocfilehash: d9f23bacf31b310da6d49e74de2153b50e642c7d
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "98582661"
---
# <a name="qr-codes-in-unreal"></a>Unreal 中的 QR 代碼

HoloLens 2 可以使用網路攝影機查看世界空間中的 QR 代碼，這會在每個代碼的真實世界位置中將其呈現為全息投影。 HoloLens 2 也可以在相同位置的多個裝置上呈現全像投影，以建立共用體驗。 確定您遵循將 QR 代碼新增至應用程式的最佳作法：

- 寧靜區域
- 光源和底圖
- 大小、距離和角度位置

將 QR 代碼放在您的應用程式時，請特別注意[環境考量](/hololens/hololens-environment-considerations)。 您可以在其中每一個主題上找到詳細資訊，以及在主要 [QR 代碼追蹤](../platform-capabilities-and-apis/qr-code-tracking.md)文件中找到如何下載所需 NuGet 套件的指示。

> [!CAUTION]
> QR 代碼是現成可供 HoloLens 追蹤的唯一影像類型，HoloLens 上不支援 Unreal 的 **UARTrackedImage** 模組。 如果您需要追蹤自訂影像，則可以使用第三方影像辨識程式庫來存取裝置的[網路攝影機](unreal-hololens-camera.md)並處理影像。 

## <a name="enabling-qr-detection"></a>啟用 QR 偵測

因為 HoloLens 2 需要使用網路攝影機來查看 QR 代碼，所以您必須在專案設定中將其啟用：
- 開啟 [編輯] > [專案設定]捲動至 [平台] 區段，然後選取 [HoloLens]。
    + 展開 [功能] 區段，並勾選 [網路攝影機]。  
- 您也必須[新增 ARSessionConfig 資產](/windows/mixed-reality/unreal-uxt-ch3#adding-the-session-asset)，來加入 QR 代碼追蹤。

[!INCLUDE[](includes/tabs-qr-codes-1.md)]

## <a name="setting-up-a-tracked-qr-code"></a>設定已追蹤的 QR 代碼

QR 代碼會透過 Unreal 的 AR 追蹤幾何系統呈現為追蹤的影像。 若要讓此作業運作，您必須：
1. 建立動作項目藍圖並新增 **ARTrackableNotify** 元件：

![QR AR 可追蹤通知](images/unreal-spatialmapping-artrackablenotify.PNG)

2. 選取 [ARTrackableNotify]，然後展開 [詳細資料] 面板中的 [事件] 區段：

![QR 事件](images/unreal-spatialmapping-events.PNG)

3. 按一下 [On Add Tracked Geometry] 旁邊的 **+** ，將節點新增至事件圖形。
    - 您可以在 [UARTrackableNotify](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackableNotifyComponent/index.html) 元件 API 中找到完整的事件清單。

![將節點新增至 On Add Tracked Geometry](images/unreal-qr-codes-tracked-geometry.png)

## <a name="using-a-tracked-qr-code"></a>使用已追蹤的 QR 代碼

下圖中的事件圖形會顯示用來在 QR 代碼中心呈現點的 **OnUpdateTrackedImage** 事件，並印出其資料。

[!INCLUDE[](includes/tabs-qr-codes-2.md)]

以下是後續動作：
1. 首先，追蹤的影像會強制轉型為 **ARTrackedQRCode**，以檢查目前更新的影像是否為 QR 代碼。  
2. 編碼的資料是從 **QRCode** 變數中擷取的。 您可以從 **GetLocalToWorldTransform** 的位置，以及具有 **GetEstimateSize** 的維度，到達 QR 代碼的左上角。

您也可以在程式碼中[取得 QR 代碼的座標系統](/windows/mixed-reality/qr-code-tracking#getting-the-coordinate-system-for-a-qr-code)。

## <a name="finding-the-unique-id"></a>尋找唯一識別碼

每個 QR 代碼都有唯一的 guid 識別碼，您可以透過下列方式找到該識別碼：
- 拖放 **As ARTracked QRCode** 釘選並搜尋 [取得唯一識別碼]。

![QR GUID](images/unreal-qr-guid.PNG)

QR 代碼在幕後還有很多工作要做，因此您的體驗尚未結束。 請務必查看下列連結，以取得有關幕後內容的詳細資訊。

## <a name="next-development-checkpoint"></a>下一個開發檢查點

依循我們配置的 Unreal 開發檢查點旅程，此時您會探索混合實境平台功能和 API。 接下來，您可以繼續進行下一個主題：

> [!div class="nextstepaction"]
> [WinRT](unreal-winRT.md)

或者，直接跳到在裝置或模擬器上部署應用程式的主題：

> [!div class="nextstepaction"]
> [部署至裝置](unreal-deploying.md)

您可以隨時回到 [Unreal 開發檢查點](unreal-development-overview.md#3-advanced-features)。

## <a name="see-also"></a>另請參閱
* [空間對應](../../design/spatial-mapping.md)
* [全像投影](../../discover/hologram.md)
* [座標系統](../../design/coordinate-systems.md)