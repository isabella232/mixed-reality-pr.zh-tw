---
title: 貢獻
description: 參與 MRTK 的群體。
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、Bug 報告、
ms.openlocfilehash: 3d829f6887d2672c72dc8fafe95943fd9f8555a6
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/03/2021
ms.locfileid: "101783410"
---
# <a name="contributing"></a>參與

「混合現實」工具組 (MRTK) 歡迎來自社區的投稿。 所有變更都很小或很大，需要遵守 MRTK 的 [編碼標準](CodingGuidelines.md)，因此請確定您在進行開發時熟悉這些變更，以避免在變更變更時延遲。

如果您有任何問題，請在「 [混合現實-工具組頻道」上](https://holodevelopers.slack.com/messages/C2H4HT858)找到您的時差。
您可以透過 [自動邀請寄件者](https://holodevelopersslack.azurewebsites.net/)來加入「時差」群。

## <a name="submission-process"></a>提交程序

我們提供數個途徑，讓開發人員能夠參與混合現實工具組，並從 [建立新的問題](https://github.com/Microsoft/MixedRealityToolkit-Unity/issues/new/choose)開始。

![問題類型](../features/images/contributing/SelectIssueType.png)

您可以從這裡的檔案：

- **Bug 報告** -其中一個混合現實工具組元件的功能問題
- **檔問題**-混合現實工具組 [檔](https://microsoft.github.io/MixedRealityToolkit-Unity)的問題
- **功能要求** -全新混合現實工具組功能的提案

## <a name="proposing-feature-requests"></a>建議功能要求

要求新的混合現實工具組功能時，請務必記錄要解決的客戶權益/問題。 提交之後，會在 GitHub 上審核並討論功能要求。 我們鼓勵各項功能提案的開放且建設性的討論，以確保工作對大型客戶的部門有利。

為了避免需要重新修改功能，通常建議在審核階段中不會開始開發功能。 在許多情況下，「社區審核」程式會發現一或多個可能需要在建議的執行中進行重大變更的問題。

> [!NOTE]
> 如果您想要處理已經存在於待處理專案上的專案，您可以使用該工作專案作為提案。 請務必同時對工作發出批註，通知維護人員您正在完成該工作。

## <a name="contribution-process"></a>投稿流程

若要開始，只要遵循下列步驟即可：

1. 分叉存放庫。 按一下頁面右上方的 [分支] 按鈕，然後遵循流程。
1. 在您的分叉中建立分支 (從 [mrtk_development](https://github.com/microsoft/mixedrealitytoolkit-unity/tree/mrtk_development) 分支) ，讓您能夠更輕鬆地隔離任何變更，直到準備好提交為止。 針對舊版 HoloToolkit，請使用 [htk_development](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_development) 分支。

如果您不熟悉 Git 工作流程，請 [參閱 Github 的簡介](https://guides.github.com/activities/hello-world/)。

新增 bug 修正或功能時，請遵循下列步驟：

1. 執行 bug 修正或功能。 建立和部署 MRTK 的指示位於 [BuildAndDeploy](../updates-deployment/BuildAndDeploy.md)。 請記得遵循程式 [代碼撰寫方針](CodingGuidelines.md)。
1. 如果加入功能，也請新增示範功能的範例場景。
1. 如果新增實驗性功能，則不需要撰寫測試和檔。 相反地，請依照 [實驗性功能指導方針](ExperimentalFeatures.md)進行。
1. 加入測試以確認 bug 修正/功能。 撰寫和執行測試的指示位於 [>--run-unittests](UnitTests.md)。
1. 請確定) 的程式碼和功能 (記載于 [檔指導方針](DocumentationGuide.md)中所述。
1. 確定程式碼在所有平臺上都能以預期的方式運作。 請參閱 [版本](../packages-releases/ReleaseNotes.md) 資訊以取得支援的平臺清單。 針對 Windows UWP 專案，程式碼必須 [符合 WACK 規範](https://developer.microsoft.com/windows/develop/app-certification-kit)。 若要這樣做，請產生 Visual Studio 方案，以滑鼠右鍵按一下專案;**存放區**  > **建立應用程式套件**。 遵循提示並執行 WACK 測試。 請確定它們都成功。
1. 提出提取要求時，請遵循 [提取要求](PullRequests.md) 中的指示。
