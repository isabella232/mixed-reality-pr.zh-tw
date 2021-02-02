---
title: 設定 Mixed Reality 功能工具
description: 瞭解如何從 HoloLens 和 VR 開發的 MR 功能工具下載並安裝混合現實 Unity 套件。
author: davidkline-ms
ms.author: v-hferrone
ms.date: 01/27/2021
ms.topic: article
ms.localizationpriority: high
keywords: 最新狀態, 開始使用, 基本概念, unity, visual studio, 工具組, 混合實境頭戴式裝置, windows 混合實境頭戴式裝置, 虛擬實境頭戴式裝置, 安裝, Windows, HoloLens, 模擬器, unreal, openxr
ms.openlocfilehash: 4201f96ac87a6e9ab33607072c0d8f5f50df38a1
ms.sourcegitcommit: cef969ffd22dc1e5a1e9c3c32fbf0646206519a1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/01/2021
ms.locfileid: "99244567"
---
# <a name="configuring-the-mixed-reality-feature-tool"></a>設定 Mixed Reality 功能工具

使用「混合現實」功能時，您可以存取三個不同的設定類別，您可以在此進行自訂：

* [下載設定](#download-settings)
* [功能設定](#feature-settings)
* [匯入設定](#import-settings)

![設定](images/FeatureToolSettings.png)

## <a name="download-settings"></a>下載設定

### <a name="overwrite-existing-package-files"></a>覆寫現有封裝檔案

啟用此設定會導致每次取得套件檔案時都會下載。 
* **建議您將此選項保持為停用狀態，以降低網路頻寬使用量**
* 依預設，不會重新下載先前取得的套件檔案

### <a name="package-cache"></a>套件快取

變更此設定以更新功能套件的下載位置。

> [!NOTE]
> 這項設定在此版本中是 **唯讀** 的。 未來的版本可能會讓此設定可供設定。

## <a name="feature-settings"></a>功能設定

### <a name="include-preview-releases"></a>包含預覽版本

啟用此設定以取得預覽版本。
* 依預設，預覽版本不會顯示在混合現實功能工具中 

> [!NOTE]
> 預覽版本定義為包含套件版本中的 **"-preview"** 指定。

## <a name="import-settings"></a>匯入設定

### <a name="replace-existing-package-files"></a>取代現有的封裝檔案

依預設，混合現實功能工具會移除匯入之套件的先前複本，以減少檔案大小和不必要的計算。 
* 取消核取此設定以保留所有版本

### <a name="project-relative-import-path"></a>專案相對匯入路徑

將此設定變更為更新匯入時複製功能套件的專案資料夾路徑。 
* 例如，如果專案資料夾是 **C:\GalaxyExplorer**，則完整的匯入路徑將會是 **C:\GalaxyExplorer\Packages\MixedReality**。

> [!NOTE]
> 這項設定在此版本中是 **唯讀** 的。 未來的版本可能會讓此設定可供設定。

## <a name="see-also"></a>另請參閱

- [歡迎使用 Mixed Reality 功能工具](welcome-to-mr-feature-tool.md)