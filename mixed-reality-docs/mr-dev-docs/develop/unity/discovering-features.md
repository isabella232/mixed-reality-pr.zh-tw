---
title: 探索和取得功能
description: 探索並下載 Mixed Reality 功能。
author: davidkline-ms
ms.author: v-hferrone
ms.date: 04/19/2021
ms.topic: article
ms.localizationpriority: high
keywords: 最新狀態, 開始使用, 基本概念, unity, visual studio, 工具組, 混合實境頭戴式裝置, windows 混合實境頭戴式裝置, 虛擬實境頭戴式裝置, 安裝, Windows, HoloLens, 模擬器, unreal, openxr
ms.openlocfilehash: fef1edd9e7257985a30739794f4b40164345254e3e76cfa740b3fe9699de79f2
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2021
ms.locfileid: "115203705"
---
# <a name="discovering-and-acquiring-features"></a>探索和取得功能

本文中的各節概述如何在混合現實功能工具中尋找功能套件。 如果您需要指定區段的參考，請參閱下列螢幕擷取畫面：

![探索功能](images/FeatureToolDiscovery.png)

## <a name="available-features"></a>可用的功能

### <a name="category"></a>類別

「混合現實」功能工具會顯示功能分類的集合，讓您輕鬆找到所需的內容。 展開任何類別以顯示其可用功能的集合。

> [!NOTE]
> 如果找不到您要尋找的功能，請檢查 **其他功能**。

![功能分類](images/FeatureCategory.png)

上述螢幕擷取畫面中的分類標頭包含下列屬性，從左至右：

- 展開和折迭按鈕
- 類別名稱 (例如：混合現實工具組) 
- 選取的功能計數
- 可用功能計數
- 區段按鈕

> [!NOTE]
> 選取按鈕會區分內容。 根據類別內的特徵選取狀態，會顯示一或多個 `Select All` 和 `Select None` 按鈕。

### <a name="feature"></a>功能

![功能專案](images/FeatureEntry.png)

功能會列在適當的類別中。 在上述螢幕擷取畫面中，從左至右，功能專案包含：

- 選取核取方塊
- 功能名稱 (例如：混合現實工具組 Foundation) 
- 可用版本清單
- [功能套件詳細資料](viewing-package-details.md)的連結

> [!NOTE]
> 如果功能是由早期存取提供 (也稱為私用預覽) 程式， ![ 則會顯示一則將會提早出現指標圖示 ](images/EarlyAccess.png) 。

## <a name="refresh-the-feature-catalog"></a>重新整理功能目錄

若要檢查是否有新的和更新的功能，請按一下 [重新整理]。 ![重新整理按鈕](images/RefreshButton.png) 按鈕。 這會連接到目錄網站並取得最新資訊。 讀取目錄之後，就會顯示上次更新的日期和時間。

## <a name="select-features"></a>特性選取

藉由展開類別、選取版本，然後按一下核取方塊來選取功能：

![選取的功能](images/SelectedFeatures.png)

若要選取類別內的每個封裝， `Select All` 則會提供按鈕。 `Select None` 將取消選取所有選取的封裝。 

具有一或多個所選功能的每個類別都會更新，以顯示計數。

## <a name="acquiring-features"></a>取得功能

選擇您的功能之後，請選取 [ **取得功能** ] 以開始下載選取的功能套件檔案。

> [!NOTE]
> 根據預設，先前取得的功能套件檔案不會重新下載。 若要變更此行為，請參閱設定 [功能工具](configuring-feature-tool.md)。

下載完成之後，Mixed Reality 功能工具將移至 [匯 [入功能](importing-features.md) ] 步驟。

## <a name="going-back-to-the-previous-step"></a>回到上一個步驟

從 **探索功能**，混合現實功能工具可讓您流覽回專案選取專案。 選取 **返回** 重新開機。

## <a name="see-also"></a>另請參閱

- [歡迎使用 Mixed Reality 功能工具](welcome-to-mr-feature-tool.md)
- [設定功能工具](configuring-feature-tool.md)
- [查看功能套件詳細資料](viewing-package-details.md)
- [匯入選取的封裝](importing-features.md)
