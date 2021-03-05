---
title: 授權專案變更
description: 瞭解如何授權專案變更適用于 HoloLens 和 VR 開發的 MR 功能工具。
author: davidkline-ms
ms.author: v-hferrone
ms.date: 03/04/2021
ms.topic: article
ms.localizationpriority: high
keywords: 最新狀態, 開始使用, 基本概念, unity, visual studio, 工具組, 混合實境頭戴式裝置, windows 混合實境頭戴式裝置, 虛擬實境頭戴式裝置, 安裝, Windows, HoloLens, 模擬器, unreal, openxr
ms.openlocfilehash: db7ae079e19c7739f57f0b9e4a375a3e6f9a3cdd
ms.sourcegitcommit: 4647712788a91a2b26d4b01e62285c2942bb0bd2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102230758"
---
# <a name="authorizing-project-changes"></a>授權專案變更

在修改 Unity 專案之前，必須先審核並核准資訊清單和專案檔的變更：

![要求授權](images/FeatureToolApprovalRequest.png)

## <a name="manifest"></a>file:///

建議的資訊清單變更可以在左邊的 **資訊清單** 欄中查看。 內容就是要寫入專案資訊清單 (**套件/manifest.js在) 上** 的內容：

![資訊清單預覽](images/ManifestPreview.png)

## <a name="files-to-be-copied-into-the-project"></a>要複製到專案中的檔案

**要複製到右邊專案** 區段的檔案，會列出將複製到 Unity 專案的特定功能套件檔案：

![具有要複製之檔案的資訊清單預覽](images/FilesToCopy.png)

## <a name="compare-manifests"></a>比較資訊清單

您可以藉由選取 [ **比較**]，查看所有建議變更的並列比較：

![比較資訊清單](images/FeatureToolCompareManifest.png)

## <a name="approving-changes"></a>核准變更

當建議的變更通過核准時，所列出的檔案將會複製到 Unity 專案中，而資訊清單會以這些檔案的參考進行更新。

> [!NOTE]
> 應將功能套件 ( *. tgz) 檔案新增至原始檔控制。 它們是使用相對路徑來參考，讓開發小組能夠輕鬆地共用功能和資訊清單變更。

 在修改過程中，會備份目前的檔案 **manifest.js** 。

> [!IMPORTANT]
> 在觀看資訊清單備份時，最舊的 **manifest.js會在備份上呼叫。** 較新的備份會以數值標注，從零開始 (0) 。

## <a name="going-back-to-the-previous-step"></a>回到上一個步驟

如果您需要變更您的功能選項， **請使用 [返回]** 返回匯 [入](importing-features.md) 步驟。

## <a name="see-also"></a>另請參閱

- [歡迎使用 Mixed Reality 功能工具](welcome-to-mr-feature-tool.md)
- [匯入選取的封裝](importing-features.md)
