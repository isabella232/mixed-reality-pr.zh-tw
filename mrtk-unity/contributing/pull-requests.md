---
title: 提取要求
description: GitHub 提取要求的相關詳細資料。
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、PR、
ms.openlocfilehash: ffaba25a42566d6e48be7db2c5b599443b24831f8f353fe1bd59beb062a7b87e
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2021
ms.locfileid: "115200109"
---
# <a name="pull-requests"></a>提取要求

## <a name="prerequisites"></a>必要條件

如果您之前尚未參與 Microsoft 專案，系統可能會要求您簽署 [投稿授權合約](https://cla.microsoft.com/)。
PR 中的批註可讓您知道您的做法。

> [!IMPORTANT]
> 如果您是 microsoft 員工，而且不是[microsoft 組織的 GitHub](https://github.com/Microsoft)的成員，請在公司網路上造訪[開放原始碼以](https://opensource.microsoft.com/)連結 microsoft 和 GitHub 帳戶，然後再開始您的提取要求。 您必須事先進行一些處理。

## <a name="creating-a-pull-request"></a>建立提取要求

當您準備好提交提取要求時，請建立以[主要](https://github.com/microsoft/mixedrealitytoolkit-unity/tree/main)分支為目標的[提取要求](https://github.com/microsoft/MixedRealityToolkit-Unity/compare/main...main?expand=1)。 若要在發行穩定期間內修正錯誤，請尋找最新的 `prerelease/*` 分支。 新功能應該隨時進入 `main` 。

閱讀指導方針，並確保您的提取要求符合指導方針。

* 請務必參考 PR 相關的任何問題/功能要求或工作。
* 檢查提取要求只包含與 PR 相關的檔案/變更。
* 檢查檔是最新的，並且包含在內。 檢查所有公用欄位都有批註。
* 如果加入新的功能，請檢查是否包含測試以驗證功能 (查看 [>--run-unittests](../contributing/unit-tests.md)) 。
* 如果要修正錯誤，請撰寫測試來確認 bug 修正。

專案維護人員會檢查您的變更。 我們的目標是要在三個工作天內檢查所有變更。 請解決任何審核批註、將其推送至您的主題分支，並張貼留言，讓我們知道有新的內容可以複習。

> [!NOTE]
> 所有提交至專案的 PR 也會根據 [MRTK 編碼標準指南](../contributing/coding-guidelines.md)進行通過，因此請在提交您的 pr 之前先進行檢查，以確保順暢的流程。

## <a name="pull-request-guidelines"></a>提取要求指導方針

這些指導方針是以 [Google 的工程實務](https://google.github.io/eng-practices/review/developer/small-cls.html)為基礎。

### <a name="keep-pull-requests-small"></a>保持提取要求的大小

較小的 Pr 會更快速且詳盡地進行檢查，較不可能引進 bug、更容易復原，而且更容易合併。

提取要求應該夠小，工程師可以在30分鐘內進行審核。 請嘗試進行不只解決一個問題的基本變更。 如果您必須建立大型 PR，請將它分割成多個 Pr，以進入您的本機分支或 MRTK 的功能分支。 避免將新資產 (例如 fbx、obj 檔案) ，而改為重複使用現有的資產。

### <a name="tests-should-be-added-in-the-same-pr-as-your-fix--feature-except-for-emergencies"></a>測試應新增至與您的修正/功能相同的 PR 中，但緊急情況除外

測試是確保變更不會回歸現有程式碼的最佳方式，但在提交提取要求時，也很容易忘記測試。 要求他們進入您的 PR，是確保測試可被撰寫的絕佳方式。

每項功能和錯誤修正都應該有相關聯的測試。 如果您沒有撰寫測試的專業知識或時間，請建立一個問題來撰寫測試，並將其標示 **為目前反覆運算** 的標籤。

### <a name="documentation-should-be-added-in-the-same-pull-request-as-a-fix--feature"></a>檔應新增至與修正/功能相同的提取要求中

大部分的開發人員在瞭解如何使用某項功能時，會先查看檔，而不是程式碼。 確保檔是最新的，讓人們更容易取用和信賴 MRTK。  檔應一律與相關的提取配套，以確保專案保持在最新狀態且一致。

確定每個公用欄位、方法、屬性都有 [三個斜線的摘要批註](https://dotnet.github.io/docfx/spec/triple_slash_comments_spec.html) ，讓我們的 docfx 網站可以產生欄位/方法的描述。 如有需要，請更新檔資料夾中的 markdown 檔。

### <a name="pull-request-descriptions-should-clearly-and-completely-describe-changes"></a>提取要求描述應該清楚且完整地描述變更

清除並完成提取要求的說明，以確保審核者瞭解他們正在審核的內容。

如果加入的功能包含 UX，請新增您要變更之功能的影像/gif。 [以下是一個很好的範例](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/4532)。 另一個建議是 [在此提取要求中使用 gif，例如在此提取要求中](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/5896)。 我們建議您從螢幕擷取畫面產生 gif 的工具是 [ScreenToGif](https://www.screentogif.com/)。
