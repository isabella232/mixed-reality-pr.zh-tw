---
title: 設定 Mixed Reality 功能工具
description: 瞭解如何從 HoloLens 和 VR 開發的 MR 功能工具下載並安裝混合現實 Unity 套件。
author: davidkline-ms
ms.author: v-hferrone
ms.date: 04/19/2021
ms.topic: article
ms.localizationpriority: high
keywords: 最新狀態, 開始使用, 基本概念, unity, visual studio, 工具組, 混合實境頭戴式裝置, windows 混合實境頭戴式裝置, 虛擬實境頭戴式裝置, 安裝, Windows, HoloLens, 模擬器, unreal, openxr
ms.openlocfilehash: 419f26f79ca8bdd1998955a2bdf72dfabf73976c89b1abce175ef2cf60c9597b
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2021
ms.locfileid: "115210880"
---
# <a name="configuring-the-mixed-reality-feature-tool"></a>設定 Mixed Reality 功能工具

使用「混合現實」功能時，您可以存取三個不同的設定類別，您可以在此進行自訂：

* [下載設定](#download-settings)
* [功能設定](#feature-settings)
* [匯入設定](#import-settings)

## <a name="download-settings"></a>下載設定

![下載設定](images/FeatureToolSettings-Download.png)

### <a name="overwrite-existing-package-files"></a>覆寫現有封裝檔案

啟用此設定會導致每次取得套件檔案時都會下載。 

* **建議您將此選項保持為停用狀態，以降低網路頻寬使用量**
* 依預設，不會重新下載先前取得的套件檔案

### <a name="package-cache"></a>套件快取

變更此設定以更新功能套件的下載位置。

> [!NOTE]
> 這項設定在此版本中是 **唯讀** 的。 未來的版本可能會讓此設定可供設定。

## <a name="feature-settings"></a>功能設定

![功能設定](images/FeatureToolSettings-Feature.png)

### <a name="show-preview-releases"></a>顯示預覽版本

啟用此設定以取得預覽版本。
* 依預設，預覽版本不會顯示在混合現實功能工具中 

> [!NOTE]
> 預覽版本定義為包含套件版本中的 **"-preview"** 指定。

### <a name="show-early-access-program-features"></a>顯示早期訪問程式功能

啟用此設定可從註冊的早期訪問程式版本取得功能。

* 依預設，「混合現實」功能工具不會顯示早期存取功能 

> [!NOTE]
> `Show early access program features`在不啟用的情況下啟用， `Show preview releases` 可能會導致 eary 存取套件未出現在探索中。

## <a name="import-settings"></a>匯入設定

![匯入設定](images/FeatureToolSettings-Import.png)

### <a name="replace-existing-package-files"></a>取代現有的封裝檔案

依預設，混合現實功能工具會移除匯入之套件的先前複本，以減少檔案大小和不必要的計算。 

* 取消核取此設定以保留所有版本

### <a name="project-relative-import-path"></a>Project 相對匯入路徑

將此設定變更為更新匯入時複製功能套件的專案資料夾路徑。 

* 例如，如果專案資料夾是 **C:\GalaxyExplorer**，則完整的匯入路徑將會是 **C:\GalaxyExplorer\Packages\MixedReality**。

> [!NOTE]
> 這項設定在此版本中是 **唯讀** 的。 未來的版本可能會讓此設定可供設定。

## <a name="early-access-settings"></a>早期存取設定

![早期存取設定](images/FeatureToolSettings-EarlyAccess.png)
 
### <a name="ask-for-confirmation-before-removing-an-early-access-program"></a>移除早期存取程式之前要求確認

這項設定會決定每次移除早期存取程式時，是否要顯示提示。

### <a name="my-previews"></a>我的預覽

已註冊的早期存取程式清單。 使用 `Add` 、 `Edit` 和 `Remove` 來管理已註冊程式的集合。

## <a name="diagnostic-settings"></a>診斷設定

![診斷設定](images/FeatureToolSettings-Diagnostics.png)

### <a name="log-file"></a>記錄檔

顯示診斷記錄檔的路徑。

## <a name="see-also"></a>另請參閱

- [歡迎使用 Mixed Reality 功能工具](welcome-to-mr-feature-tool.md)