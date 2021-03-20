---
title: BoundarySystemGettingStarted
description: MRTK 中界限系統的登陸頁面
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、界限系統、
ms.openlocfilehash: 4f1fd3a3b990fa3a4bf5cb2260ca7762ed120292
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104686431"
---
# <a name="boundary-system"></a>界限系統

界限系統提供在混合現實應用程式中視覺化虛擬實境界限元件的支援。 界限定義使用者可以在佩戴 VR 耳機時安全地四處移動的區域。 界限是混合現實體驗的重要元件，可協助使用者在佩戴 VR 耳機時避免看不見的障礙。

許多虛擬實境平臺會提供自動顯示，例如，當使用者或其控制器接近界限時，在虛擬世界上重迭的白色輪廓。 混合現實工具組的界限系統會擴充這項功能，讓您能夠顯示追蹤區域的大綱、地面平面，以及可用來提供其他資訊給使用者的其他功能。

## <a name="getting-started"></a>開始使用

新增界限的支援需要混合現實工具組的兩個主要元件：界限系統和使用界限設定的虛擬實境平臺。

1. [啟用](#enable-boundary-system) 界限系統
2. [設定](#configure-boundary-visualization) 界限視覺效果
3. 使用已設定的界限來[建立並部署](#build-and-deploy)到 VR 平臺

## <a name="enable-boundary-system"></a>啟用界限系統

界限系統由 MixedRealityToolkit 物件 (或另一個 [服務註冊機構](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) 元件) 管理。

下列步驟假設使用 MixedRealityToolkit 物件。 其他服務註冊機構所需的步驟可能會不同。

1. 選取場景階層中的 MixedRealityToolkit 物件。

    ![MRTK 設定的場景階層](../images/MRTK_ConfiguredHierarchy.png)

1. 將 [偵測器] 面板移至 [界限系統] 區段，然後勾選 [啟用]

    ![啟用界限系統](../images/boundary/MRTKConfig_Boundary.png)

1. 選取界限系統執行。 MRTK 提供的預設類別實作為 [`MixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.MixedRealityBoundarySystem)

    ![選取界限系統執行](../images/boundary/BoundarySelectSystemType.png)

> [!NOTE]
> 所有界限系統的執行都必須擴充 [`IMixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.IMixedRealityBoundarySystem)

## <a name="configure-boundary-visualization"></a>設定界限視覺效果

[界限系統會使用設定檔](configuring-boundary-visualization.md)來指定要顯示的界限元件，並設定其外觀。

![界限視覺效果選項](../images/boundary/BoundaryVisualizationProfile.png)

> [!NOTE]
> 預設設定檔、 `DefaultMixedRealityBoundaryVisualizationProfile` (資產/MRTK/SDK/設定檔) 的使用者將會將界限系統預先設定為顯示樓層平面、播放區域和追蹤的區域。

## <a name="build-and-deploy"></a>建置及部署

使用所需的視覺效果選項設定界限系統之後，就可以將專案部署至目標平臺。

> [!NOTE]
> Unity Play 模式可讓您在編輯器中進行已設定界限的視覺效果。 這項功能可讓您快速開發和測試，而不需要建立和部署步驟。 請務必使用在目標硬體和平臺上執行的應用程式建立和部署版本，進行最終的接受度測試。

## <a name="accessing-boundary-system-via-code"></a>透過程式碼存取界限系統

如果啟用並設定，則可以透過 CoreServices 靜態協助程式類別來存取界限系統。 然後，您可以使用該參考動態變更界限參數，並存取系統所管理的相關 Gameobject。

```c#
// Hide Boundary Walls at runtime
CoreServices.BoundarySystem.ShowBoundaryWalls = false;

// Get Unity GameObject for the floor visualization in scene
GameObject floorVisual = CoreServices.BoundarySystem.GetFloorVisualization();
```

## <a name="see-also"></a>另請參閱

- [界限 API 檔](xref:Microsoft.MixedReality.Toolkit.Boundary)
- [設定界限視覺效果](configuring-boundary-visualization.md)
