---
title: SpatialObjectMeshObserver
description: MRTK 中的空間網格觀察器檔
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: 90bff1b05555b56227b3abc7626a4ab97e7fdd0d
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104686898"
---
# <a name="configuring-mesh-observers-for-the-editor"></a>設定編輯器的網格觀察器

在 Unity 編輯器中提供環境網格資料的便利方式是使用 [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) 類別。 *空間物件網格觀察* 者是一種僅限編輯器的資料提供者，適用于 [空間感知系統](SpatialAwarenessGettingStarted.md)，可讓您匯入3d 模型資料來代表空間網格。 *空間物件網格觀察* 者的其中一種常見用法是匯入透過 Microsoft HoloLens 掃描的資料，以測試如何從 Unity 內調整不同環境的體驗。

## <a name="getting-started"></a>開始使用

本指南將逐步解說如何設定 *空間物件網格觀察* 者。 啟用這項功能有三個主要步驟。

1. 將 *空間物件網格觀察* 器新增至空間感知系統設定檔
1. 設定環境網格資料物件
1. [設定其他網格觀察者配置檔案屬性](ConfiguringSpatialAwarenessMeshObserver.md)

### <a name="set-up-a-spatial-object-mesh-observer-profile"></a>設定 *空間物件網格觀察* 者設定檔

1. 選取所需的 *混合現實工具* 組設定設定檔，或選取場景中的 *混合現實工具* 組物件
1. 開啟或展開 [ *空間感知系統* ] 索引標籤
1. 按一下 *[新增空間觀察者]* 按鈕

    ![新增空間觀察者](../images/spatial-awareness/AddObserver.png)

1. 選取 *SpatialObjectMeshObserver* 類型

    ![選取空間物件網格觀察者](../images/spatial-awareness/SelectObjectObserver.png)

1. 選取所需的 *空間網格物件*。 根據預設，系統會使用範例模型來設定觀察者。 此模型是使用 Microsoft HoloLens 建立的，但您可以 [建立新的掃描網格物件](#acquiring-environment-scans)。
1. [設定其他網格觀察者配置檔案屬性](ConfiguringSpatialAwarenessMeshObserver.md)

    ![選取網格物件](../images/spatial-awareness/ObjectObserverProfile.png)

### <a name="spatial-object-mesh-observer-profile-notes"></a>空間物件網格觀察器設定檔注意事項

由於 *空間物件網格觀察* 器會從3d 模型載入資料，因此它不會接受以下所述的一些標準網格觀察者設定。

**更新間隔**

當載入模型時，  *空間物件網格觀察* 者會將所有網格傳送至應用程式。 它不會模擬更新之間的時間差異。 應用程式可以藉由呼叫和來重新接收網格 [`myObserver.ClearObservation()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver.ClearObservations) 事件 [`myObserver.Resume()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver.Resume) 。

**為固定觀察者**

*空間物件網格觀察* 者會將所有3d 網格物件視為固定和忽略來源。

**觀察者圖形和範圍**

*空間物件網格觀察* 者會將整個3d 網格傳送至應用程式。 不考慮觀察者圖形與範圍。

**詳細資料層級與三角形/三立方計量表**

將網格傳送至應用程式時，觀察者不會嘗試尋找3D 模型 LODs。

## <a name="acquiring-environment-scans"></a>取得環境掃描

本節將概述用來建立和收集 *空間網格物件* 檔案，以與 *空間物件網格觀察* 者搭配使用的其他資訊。

### <a name="windows-device-portal"></a>Windows 裝置入口網站

[Windows 裝置入口網站](https://docs.microsoft.com/windows/mixed-reality/using-the-windows-device-portal)可以用來從 Microsoft HoloLens 裝置將空間網格下載為 .obj 檔。

1. 藉由使用 HoloLens 來掃描及觀看所需的環境，進行掃描
1. 使用 Windows 裝置入口網站連接到 HoloLens
1. 流覽至 *3D 視圖* 頁面
1. 按一下 [*空間對應*] 區段底下的 [*更新*] 按鈕
1. 按一下 [*空間對應*] 區段下的 [*儲存*] 按鈕，將 OBJ 檔案儲存至 PC

> [!NOTE]
> **HoloToolkit 聊天室檔案**
>
> 許多開發人員先前都會使用 HoloToolkit 來掃描環境，並建立聊天室檔案。 混合現實工具組現在支援將這些檔案匯入為 Unity 中的 Gameobject，並在觀察者中使用它們做為 *空間網格物件* 。

## <a name="see-also"></a>另請參閱

- [設定檔](../profiles/Profiles.md)
- [混合現實工具組設定檔設定指南](../../configuration/MixedRealityConfigurationGuide.md)
- [空間感知入門](SpatialAwarenessGettingStarted.md)
- [設定裝置上的網狀觀察器](ConfiguringSpatialAwarenessMeshObserver.md)
- [透過程式碼設定網格觀察者](UsageGuide.md)
- [使用 Windows 裝置入口網站](https://docs.microsoft.com/windows/mixed-reality/using-the-windows-device-portal)
