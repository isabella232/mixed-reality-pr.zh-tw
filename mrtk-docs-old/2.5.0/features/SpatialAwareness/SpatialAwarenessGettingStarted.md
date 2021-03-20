---
title: SpatialAwarenessGettingStarted
description: 描述 MRTK 中的空間感知
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: e4a2112255bed5367f9cc4a2143e227e9928aae0
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104689708"
---
# <a name="spatial-awareness"></a>空間感知

![空間感知](../Images/SpatialAwareness/MRTK_SpatialAwareness_Main.png)

空間感知系統可在混合現實應用程式中提供真實世界的環境感知。 當您在 Microsoft HoloLens 上引進時，空間感知會提供網格的集合，代表環境的幾何，可在全像全像全球的互動之間進行吸引人的互動。

> [!NOTE]
> 目前，「混合現實」工具組不會隨附空間理解演算法，如同最初封裝在 HoloToolkit 中。 空間理解通常涉及轉換空間網格資料，以建立簡化和/或群組的網格資料，例如平面、牆壁、樓層、上限等。

## <a name="getting-started"></a>開始使用

新增空間感知的支援需要混合現實工具組的兩個主要元件：空間感知系統和支援的平臺提供者。

1. [啟用](#enable-the-spatial-awareness-system) 空間感知系統
2. [註冊](#register-observers) 並 [設定](ConfiguringSpatialAwarenessMeshObserver.md) 一或多個空間觀察者，以提供網格資料
3. [建立並部署](#build-and-deploy) 至支援空間感知的平臺

### <a name="enable-the-spatial-awareness-system"></a>啟用空間感知系統

空間感知系統是由 MixedRealityToolkit 物件 (或另一個 [服務註冊機構](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) 元件) 所管理。 遵循下列步驟來啟用或停用 *MixedRealityToolkit* 設定檔中的 *空間感知系統*。

混合現實工具組隨附一些預設預先設定的設定檔。 其中有些是預設啟用或停用空間感知系統。 此預先設定的目的（特別是在停用時），是為了避免計算和轉譯網格的視覺負擔。

| 設定檔 | 預設啟用的系統 |
| --- | --- |
| `DefaultHoloLens1ConfigurationProfile` (資產/MRTK/SDK/設定檔/HoloLens1)  | 否 |
| `DefaultHoloLens2ConfigurationProfile` (資產/MRTK/SDK/設定檔/HoloLens2)  | 否 |
| `DefaultMixedRealityToolkitConfigurationProfile` (資產/MRTK/SDK/設定檔)  | 對 |

1. 在場景階層中選取要在 [偵測器] 面板中開啟的 MixedRealityToolkit 物件。

    ![MRTK 設定的場景階層](../Images/MRTK_ConfiguredHierarchy.png)

1. 流覽至 *空間感知系統* 區段，並檢查 *啟用空間感知系統*

    ![啟用空間感知](../Images/SpatialAwareness/MRTKConfig_SpatialAwareness.png)

1. 選取所需的空間感知系統執行類型。 [`MixedRealitySpatialAwarenessSystem`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.MixedRealitySpatialAwarenessSystem)是提供的預設值。

    ![選取空間感知系統的執行](../Images/SpatialAwareness/SpatialAwarenessSelectSystemType.png)

### <a name="register-observers"></a>註冊觀察者

Mixed Reality 工具組中的服務可以有 [Data Provider 服務](../../architecture/SystemsExtensionsProviders.md) ，使用平臺特定資料和實行控制來補充主要服務。 其中一個範例是混合的現實輸入系統，具有 [多個資料提供者](../Input/InputProviders.md) ，可從各種平臺特定 api 取得控制器和其他相關的輸入資訊。

空間感知系統很類似，因為資料提供者會為系統提供真實世界的網格資料。 空間感知設定檔至少必須註冊一個空間觀察者。 空間觀察者通常是平臺特定的元件，可作為提供者，從特定平臺的端點呈現各種類型的網格資料 (例如 HoloLens) 。

1. 開啟或展開 *空間感知系統設定檔*

    ![空間感知系統設定檔](../Images/SpatialAwareness/SpatialAwarenessProfile.png)

1. 按一下 [ *新增空間觀察者]* 按鈕
1. 選取所需的 *空間觀察者實類型*

    ![選取空間觀察者的執行](../Images/SpatialAwareness/SpatialAwarenessSelectObserver.png)

1. 視需要[修改觀察者的設定屬性](ConfiguringSpatialAwarenessMeshObserver.md)

> [!NOTE]
> `DefaultMixedRealityToolkitConfigurationProfile` (資產/MRTK/SDK/設定檔) 的使用者將會為使用類別的 Windows Mixed Reality 平臺預先設定空間感知系統 [`WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver) 。

### <a name="build-and-deploy"></a>建置及部署

一旦空間感知系統設定為所需的觀察者 (s) ，就可以建立專案，並將其部署至目標平臺。

> [!IMPORTANT]
> 如果以 Windows Mixed Reality 平臺為目標 (例如： HoloLens) ，請務必確定已啟用 [空間感知功能](https://docs.microsoft.com/windows/mixed-reality/spatial-mapping-in-unity) ，才能在裝置上使用空間感知系統。

> [!WARNING]
> 某些平臺（包括 Microsoft HoloLens）提供從 Unity 內遠端執行的支援。 這項功能可讓您快速開發和測試，而不需要建立和部署步驟。 請務必使用在目標硬體和平臺上執行的應用程式建立和部署版本，進行最終的接受度測試。

## <a name="next-steps"></a>下一步

遵循上述程式來啟用空間感知系統之後，就可以更詳細地設定和控制系統。

在偵測器中設定觀察者的資訊：

- [設定裝置使用的觀察者](ConfiguringSpatialAwarenessMeshObserver.md)
- [為編輯器中的使用方式設定觀察者](SpatialObjectMeshObserver.md)

透過程式碼控制和延伸觀察者的資訊：

- [透過程式碼設定觀察者](UsageGuide.md)
- [建立自訂觀察者](CreateDataProvider.md)

## <a name="see-also"></a>另請參閱

- [空間感知 API 檔](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness)
- [空間對應總覽 WMR](https://docs.microsoft.com/windows/mixed-reality/spatial-mapping)
- [Unity WMR 中的空間對應](https://docs.microsoft.com/windows/mixed-reality/spatial-mapping-in-unity)
