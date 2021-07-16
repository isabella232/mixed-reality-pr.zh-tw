---
title: 設定裝置的網狀觀察器
description: 如何在 MRTK 中設定現成的空間網格觀察者
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: aba49e88d4fc555a88fe42e4b09858f1d2453ddc
ms.sourcegitcommit: 912fa204ef79e9b973eab9b862846ba5ed5cd69f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/16/2021
ms.locfileid: "114281935"
---
# <a name="configuring-mesh-observers-for-device"></a>設定裝置的網狀觀察器

本指南將逐步解說如何在 MRTK 中設定現成可用的空間網格觀察器，以支援 Windows Mixed Reality 平臺 (亦即 HoloLens) 。 混合現實工具組所提供的預設實作為 [WindowsMixedRealitySpatialMeshObserver](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver) 類別。 不過，本文中的許多屬性都適用于其他 [自訂觀察](create-data-provider.md)者的實施。

## <a name="profile-settings"></a>設定檔設定

針對 [空間感知系統](spatial-awareness-getting-started.md)設定空間網格觀察者設定檔時，必須先定義下列兩個專案。

1. 具體觀察者類型的實
1. 執行此觀察者) 支援的平臺 (的清單

> [!NOTE]
> 所有觀察者都必須延伸 [IMixedRealitySpatialAwarenessObserver](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver) 介面。

![網格觀察者一般設定平臺類型](../images/spatial-awareness/SpatialAwarenessMeshObserverProfile_TypesPlatforms.png)

### <a name="general-settings"></a>一般設定

![網格觀察器一般設定一般設定](../images/spatial-awareness/MeshObserverGeneralSettings.png)

**啟動行為**

啟動行為會指定觀察者是否會在第一次具現化時開始執行。 這兩個選項是：

* *自動啟動* -預設值，讓觀察者在初始化之後開始作業
* *手動啟動* -觀察者將等候導向開始

如果使用 *手動啟動*，必須 [在執行時間透過程式碼繼續並暫停](usage-guide.md#starting-and-stopping-mesh-observation)。

**更新間隔**

對平臺提出更新空間網格資料的要求之間的時間（以秒為單位）。 一般值落在0.1 和5.0 秒的範圍內。

**為固定觀察者**

指出觀察者是否要保持不變，或移動和更新使用者。 若為 true，觀察範圍所定義之磁片 *區* 的 *觀察者圖形* 將在啟動時保留在來源上。 如果為 false，觀察者空間將會遵循使用者的標頭做為圖形的來源。

系統不會針對觀察者空間以外的任何實體區域計算任何網格資料，如這些屬性所定義： *是固定的觀察* 者、* 觀察者圖形 * *，以及 *觀察範圍*。

**觀察者圖形**

觀察者圖形會定義網格觀察器在觀察網格時將使用的磁片區類型。 支援的選項如下：

* *軸對齊 Cube* -矩形圖形，與全球座標系統的軸保持一致，如同在應用程式啟動時所決定。
* *使用者對齊的 Cube* -矩形圖形，可旋轉以配合使用者的本機座標系統。
* *球體* -中央位於世界空間原點的球形音量。 [ *觀察範圍* ] 屬性的 X 值將用作球體的半徑。

**觀察範圍**

觀察範圍會定義觀察到網格的觀察點距離。

### <a name="physics-settings"></a>物理設定

![網格觀察者物理設定](../images/spatial-awareness/MeshObserverPhysicsSettings.png)

**實體層**

將放置空間網格物件以與 Unity 物理學和 RayCast 系統互動的實體層。

> [!NOTE]
> 混合現實工具組預設會保留 *第31層* ，供空間感知觀察者使用。

**重新計演算法線**

指定網格觀察者是否會在觀察之後重新計算網格的法線。 這項設定可用來確保應用程式在不會以網格傳回的平臺上，接收包含有效的法線資料的網格。

### <a name="level-of-detail-settings"></a>詳細資料設定層級

![詳細設定的網格觀察者層級](../images/spatial-awareness/MeshObserverLevelOfDetailSettings.png)

**詳細資料層級**

指定空間網格資料 (」 LOD) 的詳細層級。 目前定義的值為粗略、精細和自訂。

* *粗略* 地對應用程式效能產生較小的影響，這是導覽/平面尋找的絕佳選擇。

* *適中* 的設定通常適用于持續掃描環境中的大型功能、地面和牆，以及遮蔽詳細資料的體驗。

* 一般 exacts 對應用程式效能的影響較高，而且是遮蔽網格的絕佳選項。

* *自訂* -要求應用程式指定 *三角形/三次計量* 屬性，並讓應用程式調整精確度和空間網格觀察者的效能影響。

> [!NOTE]
> 不保證所有的 *三角形/立方計量* 值都能由所有平臺接受。 使用自訂」 LOD 時，強烈建議使用測試和分析。

**每一立方計量的三角形**

在使用 **詳細資料屬性層級** 的 *自訂* 設定，並指定空間網格的三角形密度時有效。

### <a name="display-settings"></a>顯示器設定

![網格觀察者顯示設定](../images/spatial-awareness/MeshObserverDisplaySettings.png)

**顯示選項**

指定觀察者如何顯示空間網格。 支援的值為：

* *無* -觀察者不會呈現網格
* 可見 *的資料* 會使用 *可見的材質* 顯示
* *遮蔽*-網格資料會在場景中使用 *遮蔽材質* 遮蔽專案

![選取空間感知系統的執行](../images/spatial-awareness/MRTK_SpatialAwareness_DisplayOptions.jpg)

空間觀察者可以透過程式 [代碼在執行時間繼續/暫停。](usage-guide.md#starting-and-stopping-mesh-observation)

> [!WARNING]
> 將 *顯示選項* 設定為 [ *無* ] 時， **不** 會停止執行觀察器。 如果您想要停止所有觀察者，則應用程式必須透過 [`CoreServices.SpatialAwareness.SuspendObservers()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessSystem.SuspendObservers)

**可見的材質**

指出將空間網格視覺化時要使用的材質。

**遮蔽材質**

指出要用來讓空間網格遮蔽全像影像的材質。

## <a name="see-also"></a>另請參閱

* [空間感知系統](spatial-awareness-getting-started.md)
* [透過程式碼設定空間感知系統](usage-guide.md)
* [IMixedRealitySpatialAwarenessObserver API 檔](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver)
* [IMixedRealitySpatialAwarenessMeshObserver API 檔](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessMeshObserver)
* [BaseSpatialObserver API 檔](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialObserver)
