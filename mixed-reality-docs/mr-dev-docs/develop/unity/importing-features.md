---
title: 匯入功能
description: 瞭解如何從 HoloLens 和 VR 開發的 MR 功能工具匯入和安裝功能。
author: davidkline-ms
ms.author: v-hferrone
ms.date: 03/04/2021
ms.topic: article
ms.localizationpriority: high
keywords: 最新狀態, 開始使用, 基本概念, unity, visual studio, 工具組, 混合實境頭戴式裝置, windows 混合實境頭戴式裝置, 虛擬實境頭戴式裝置, 安裝, Windows, HoloLens, 模擬器, unreal, openxr
ms.openlocfilehash: 6cf3712ce8029695076ceaec4191df53eb72789c62568206c056f1afc6c04c3b
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2021
ms.locfileid: "115225778"
---
# <a name="importing-features"></a>匯入功能

下載您的功能之後，您就可以檢查並匯入至 Unity 專案。 在這個步驟中，您的應用程式視窗看起來應該如下圖所示：

![匯入功能](images/FeatureToolImport.png)

## <a name="features-list"></a>功能清單

[ **功能** ] 清單包含探索期間選取的封裝集合。 您可以在匯入之前選取或取消選取每項功能。 您可以使用如下所示的 **詳細資料** 連結來查看套件詳細資料

![功能清單](images/FeaturesList.png)

## <a name="required-dependencies-list"></a>必要相依性清單

**必要** 的相依性清單包含一或多個所選功能需要運作的封裝。 這份清單也會包含相依性的相依性。 您可以選取或取消選取每個相依性，然後再匯入。 您可以使用如下所示的 **詳細資料** 連結來查看套件詳細資料

![相依性清單](images/RequiredDependencyList.png)

> [!NOTE]
> 當您在 Unity 中載入專案時，取消選擇必要的相依性將會導致一個或多個遺失的相依性錯誤。 這些功能無法在專案中使用。

## <a name="validating-selections"></a>驗證選取專案

我們強烈建議您在匯入之前驗證特徵選取。 此步驟會引發任何可能妨礙專案開發成功的問題。

![驗證問題](images/ValidationIssues.png)

Mixed Reality 功能工具提供兩個自動問題解決方式，如下列各節) 所述，以及手動取消和解決問題的選項。

### <a name="enable-dependencies"></a>啟用相依性

[ **啟用** 相依性] 按鈕將會自動重新選取遺失的相依性。 這適用于明確選取的相依性 (出現在 [ **功能** 清單]) 中，以及根據所選功能的需求隱含選取的相依性。

### <a name="disable-features"></a>停用功能

選取 [ **停用功能** ] 將會自動取消選取相依于一或多個已取消選取之相依性的任何功能。 這適用于隱含選取的相依性封裝和明確選取的功能。

## <a name="importing"></a>匯入

選取 [匯 **入** ] 以新增您選取的功能，並在更新目標專案前提供 [最終核准](reviewing-changes.md) 。

> [!IMPORTANT]
> 如果在匯入時仍有驗證問題，則會顯示警告訊息。 建議您選取 [否]，然後按一下 [ **驗證** ] 並解決任何出現的問題。
>
> ![繼續進行驗證問題](images/ValidationContinueAnyway.png)

## <a name="going-back-to-the-previous-step"></a>回到上一個步驟

從匯 **入功能**，混合現實功能工具可讓您回頭流覽至 [探索](discovering-features.md)。 選取 **返回** 下載其他功能套件。

## <a name="see-also"></a>另請參閱

- [歡迎使用 Mixed Reality 功能工具](welcome-to-mr-feature-tool.md)
- [探索和收購](discovering-features.md)
- [查看功能套件詳細資料](viewing-package-details.md)
- [審核和核准專案修改](reviewing-changes.md)