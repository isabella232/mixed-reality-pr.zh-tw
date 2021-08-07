---
title: Unreal 中的本機空間錨點
description: 了解如何在 Unreal 混合實境應用程式中使用、儲存及管理空間錨點。
author: hferrone
ms.author: v-hferrone
ms.date: 12/9/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 混合實境, 開發, 功能, 文件, 指南, 全像投影, 空間錨點, 混合實境頭戴式裝置, windows 混合實境頭戴式裝置, 虛擬實境頭戴式裝置
ms.openlocfilehash: c8fe7fef5af247663eefed097d3494d6187195272967434ecc7696349e1e6889
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2021
ms.locfileid: "115213560"
---
# <a name="local-spatial-anchors-in-unreal"></a>Unreal 中的本機空間錨點

空間錨點能夠以 **ARPin** 的形式將全像投影儲存在應用程式工作階段之間的真實世界空間中。 ARPin 儲存在 HoloLens 的錨定存放區之後，就可以在未來的工作階段中載入，且在沒有網際網路連線時，將是理想的備用選項。

> [!NOTE]
> UE 4.25 的錨點函式在 4.26 已過時，請以較新的函式加以取代。 

> [!IMPORTANT]
> 本機錨點會儲存在裝置上，而 Azure Spatial Anchors 會儲存在雲端。 如果您想要使用 Azure 雲端服務來儲存您的錨點，我們有一份文件可引導您整合 [Azure Spatial Anchors](unreal-azure-spatial-anchors.md)。 請注意，您在同一個專案中可以有本機和 Azure 錨點，而不會發生衝突。

## <a name="checking-the-anchor-store"></a>檢查錨定存放區

在儲存或載入錨點之前，必須先檢查錨點存放區是否準備就緒。  在錨點存放區準備就緒之前，呼叫任何 HoloLens 錨點功能將會失敗。  

[!INCLUDE[](includes/tabs-sa-1.md)]

## <a name="saving-anchors"></a>儲存錨點

一旦應用程式具有您需要釘選到世界的元件，就可以下列序列儲存到錨點存放區： 

[!INCLUDE[](includes/tabs-sa-2.md)]

將此細分：
1. 在已知位置繁衍動作項目。
2. 根據動作項目的類別，建立具有該位置和名稱的 **ARPin**。 
3. 將動作項目新增至 **ARPin**，並將圖釘儲存至 HoloLens 錨點存放區。  
    * 您選擇的錨點名稱必須是唯一的，在這個範例中，其為目前的時間戳記。 

4. 如果錨點成功儲存至錨點存放區，則您可以在 [系統] > [對應管理員] > [裝置上儲存的錨點檔案] 底下的 HoloLens 裝置入口網站中查看該錨點。 

## <a name="loading-anchors"></a>載入錨點

當應用程式啟動時，您可以使用下列藍圖來將元件還原至其錨點位置：

[!INCLUDE[](includes/tabs-sa-3.md)]

將此細分：
1. 逐一查看錨點存放區中的所有錨點。 
2. 在身分識別中繁衍動作項目。
3. 從錨點存放區將該動作項目釘選到 **ARPin**。  

    * 請務必在身分識別繁衍動作項目，因為錨點會負責根據儲存位置在世界中重新放置全像投影。 此處新增的任何轉換都會將位移新增至錨點。 

也會查詢錨點識別碼，以便根據錨點的儲存名稱來繁衍不同的動作項目。 

## <a name="removing-anchors"></a>移除錨點 

當您完成錨點時，可以使用 **Remove ARPin from WMRAnchor Store** 和 **Remove All ARPins from WMRAnchor Store** 元件，清除個別錨點或整個錨點存放區。

[!INCLUDE[](includes/tabs-sa-4.md)]

> [!NOTE]
> 請記住，空間錨點仍是 Beta 版，因此請務必回頭查看是否有更新的資訊和功能。

## <a name="next-development-checkpoint"></a>下一個開發檢查點

依循我們配置的 Unreal 開發旅程，此時您會探索 MRTK核心建置組塊。 接下來，您可以繼續進行下一個建置組塊： 

> [!div class="nextstepaction"]
> [Azure Spatial Anchors](unreal-azure-spatial-anchors.md)

或者，直接跳到混合實境平台功能和 API 的主題：

> [!div class="nextstepaction"]
> [HoloLens 相機](unreal-hololens-camera.md)

您可以隨時回到 [Unreal 開發檢查點](unreal-development-overview.md#2-core-building-blocks)。

## <a name="see-also"></a>另請參閱

* [Azure Spatial Anchors](unreal-azure-spatial-anchors.md)
* [空間錨點](../../design/spatial-anchors.md)
* [座標系統](../../design/coordinate-systems.md)
