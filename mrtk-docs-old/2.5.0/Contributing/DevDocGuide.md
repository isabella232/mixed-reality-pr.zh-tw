---
title: DevDocGuide
description: 適用于 MRTK 的開發人員入口網站 gudie。
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、GitHub
ms.openlocfilehash: e752508bf111169c91a2d7d96e1adaace86a64e7
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/03/2021
ms.locfileid: "101780432"
---
# <a name="developer-portal-generation-guide"></a>開發人員入口網站產生指南

MRTK 使用 [docfx](https://dotnet.github.io/docfx/index.html) ，從程式碼中的三個斜線批註，以及 MRTK 存放庫中的 md 檔案產生 html 檔。 Docfx 檔產生會在 mrtk_development 分支中已完成的 Pr 上由 CI 自動觸發。
您可以在 [ [MRTK github.io] 頁面](https://microsoft.github.io/MixedRealityToolkit-Unity/)上找到開發人員檔的目前狀態

Docfx 支援 DFM Docfx Flavored Markdown，其中包括 GFM Github Flavored Markdown。 您可以在[這裡](https://dotnet.github.io/docfx/tutorial/docfx.exe_user_manual.html)找到完整的檔和功能清單

Docfx 不只是轉換，也會檢查檔中所有已使用的本機連結。 如果無法解析路徑，它就不會轉換成其 html 對等專案。 因此在參考其他本機檔案時，請務必只使用相對路徑。

## <a name="building-docfx-locally"></a>在本機建立 docfx

MRTK 存放庫中的 docfx 組建檔案可以用來在專案根目錄的 doc/子資料夾中建立開發人員檔的本機版本。

### <a name="setup"></a>安裝程式

* 取得[docfx](https://dotnet.github.io/docfx/index.html)的最新版本
* 解壓縮電腦資料夾中的檔案
* 將資料夾新增至您的環境變數中的路徑

### <a name="generation"></a>世代

* 在 MRTK 專案的根目錄中開啟 powershell 或命令提示字元
* `docfx docfx.json`使用-f 選項（選擇性）執行 (，以強制重建 doc 檔案) 
* `docfx serve doc`如果您不想要使用8888預設通訊埠，請使用-p *portnumber* 來執行 (（選擇性）) 
* 以 localhost：*portnumber* 開啟網頁瀏覽器

請注意，在 json 組建檔案 docfx 上執行 docfx 命令時，會在檔中將任何中斷的連結顯示為警告。
當您在任何檔檔案或 API 上執行變更時，請務必要更新所有指向這些文章或程式碼的連結。

## <a name="verifying-docfx-on-github"></a>在 github 上驗證 docfx

每當 PR 包含可能會影響檔 CI 的變更時，就必須執行這些變更，以針對中斷的連結執行 docfx 檢查。 `/azp run mrtk_docs`如果使用者有足夠的許可權可將命令張貼到 PR 中，就可以將此觸發。 此命令將會觸發 CI 作業，該作業會將檔組建新增至 PR 的 [檢查] 區段。

## <a name="using-crefs-and-hrefs-in--documented-code"></a>使用 crefs 和 href in///記錄的程式碼

Docfx 支援 crefs in///記錄的程式碼。 它會將這些參考轉譯成指向產生的 api 檔或外部檔網站的連結。
用來解析外部程式庫/api 連結的外部 x 服務可以加入至屬性 *xrefService* 中的組建設定檔案的 docfx.js。

針對未提供 x 服務 href 至檔網站的外部 api，可新增至批註。

範例：

```c#
/// Links to MRTK internal class SystemType
/// <see cref="Microsoft.MixedReality.Toolkit.Utilities.SystemType"/>

/// Links to external API - link provided by xref service
/// <see cref="System.Collections.Generic.ICollection{Type}.Contains"/>

/// Links to Unity web API reference
/// <see href="https://docs.unity3d.com/ScriptReference/EditorGUI.PropertyField.html">EditorGUI.PropertyField</see>
```

## <a name="linking-in-md-documentation-files"></a>連結 md 檔檔案

Docfx 正在轉譯和驗證產生的所有相對本機連結，不需要特殊的語法。 參考另一篇檔文章的方法應該一律是參考對應的 md 檔案，永遠不是自動產生的 .html 檔案。 請注意，本機檔案的所有連結都必須相對於您要修改的檔案。

您可以使用 [交互參照](https://dotnet.github.io/docfx/tutorial/links_and_cross_references.html)來完成連結至 API 檔。 Docfx 會藉由重整簽章，為所有 API 檔自動產生 Uid。

範例：

這會連結至 [BOUNDARYSYSTEM API](xref:Microsoft.MixedReality.Toolkit.Boundary) 以及這個簡短版本： @Microsoft.MixedReality.Toolkit.Boundary

```md
This links to the [BoundarySystem API](xref:Microsoft.MixedReality.Toolkit.Boundary)
as well as this short version: @Microsoft.MixedReality.Toolkit.Boundary
```

## <a name="enumerating-available-xrefs"></a>列舉可用的 xrefs

X 語法很難記住，您可以先在本機執行 docfx 來列舉所有可用的 x 識別碼：

> docfx docfx.js開啟

這會產生 xrefmap yml 檔案，該檔案將位於檔/xrefmap. yml 中。

例如，為了連結 HandleEvent 的下列多載，語法相當難懂：

```yml
- uid: Microsoft.MixedReality.Toolkit.BaseEventSystem.HandleEvent``1(BaseEventData,ExecuteEvents.EventFunction{``0})
  name: HandleEvent<T>(BaseEventData, ExecuteEvents.EventFunction<T>)
  href: api/Microsoft.MixedReality.Toolkit.BaseEventSystem.html#Microsoft_MixedReality_Toolkit_BaseEventSystem_HandleEvent__1_BaseEventData_ExecuteEvents_EventFunction___0__
  commentId: M:Microsoft.MixedReality.Toolkit.BaseEventSystem.HandleEvent``1(BaseEventData,ExecuteEvents.EventFunction{``0})
  name.vb: HandleEvent(Of T)(BaseEventData, ExecuteEvents.EventFunction(Of T))
  fullName: Microsoft.MixedReality.Toolkit.BaseEventSystem.HandleEvent<T>(BaseEventData, ExecuteEvents.EventFunction<T>)
  fullName.vb: Microsoft.MixedReality.Toolkit.BaseEventSystem.HandleEvent(Of T)(BaseEventData, ExecuteEvents.EventFunction(Of T))
  nameWithType: BaseEventSystem.HandleEvent<T>(BaseEventData, ExecuteEvents.EventFunction<T>)
  nameWithType.vb: BaseEventSystem.HandleEvent(Of T)(BaseEventData, ExecuteEvents.EventFunction(Of T))
```

不過，您很容易就能搜尋名稱，然後使用整個 **uid 欄位** 作為 x。

在此範例中，x 看起來會像這樣： (x： MixedReality. BaseEventSystem. HandleEvent ``1(BaseEventData,ExecuteEvents.EventFunction{`` 0} ) ) 

## <a name="adding-new-md-files-to-developer-docs"></a>將新的 md 檔案新增至開發人員檔

Docfx 會在 docfx.js的 [組建] 區段中，于新增為內容檔案的資料夾中，挑選任何 md 檔案，並從中產生 html 檔案。 若為新資料夾，則必須加入組建檔案中的對應專案。

### <a name="navigation-entries"></a>導覽專案

若要在開發人員檔 docfx 中判斷導覽的專案，請使用 yml/toc 資料表的內容檔案。
專案根目錄中的 toc 檔案會定義頂端導覽列中的專案，而存放庫之子資料夾中的 yml 檔案會定義提要欄位導覽中的子主題。
yml 檔案可用於結構化，而且可以有任何數量的檔案。 如需有關為 toc 定義專案的詳細資訊，請 yml 檢查 [toc 上的 docfx 檔專案](https://dotnet.github.io/docfx/tutorial/intro_toc.html)。

## <a name="resource-files"></a>資源檔

有些檔案（例如，檔可以參考的影像、影片或 Pdf），但不是由 docfx 進行轉換。 針對這些檔案，docfx.js中有一個資源區段。 該區段中的檔案只會進行複製，而不會在其上執行任何轉換。

目前有下列資源類型的定義：

| ResourceType | 路徑 |
| --- | --- |
| 映像 | 檔/影像/ |

## <a name="releasing-a-new-version"></a>發行新版本

支援多個版本的開發人員檔，並且可以透過頂端功能表列中的 [版本] 下拉式清單來切換。 如果您要發行新的版本，請執行下列步驟，在開發人員檔頁面上安裝您的版本。

1. 選用：調整您的 docfx.js  
根據您是否想要讓「改進此檔」以指向特定版本的 github 存放庫，您必須先將下列專案新增至 docfx.json 檔案中的 globalMetaData 區段，然後再呼叫 docfx 命令：

    ```json
    "_gitContribute": {
        "repo": "https://github.com/Microsoft/MixedRealityToolkit-Unity.git",
        "branch": "mrtk_development"
    }
    ```

    如果您未設定此設定，docfx 會預設為您正在從中呼叫 docfx 之目前資料夾的分支和存放庫。

1. 在存放庫的根目錄中呼叫 docfx docfx.js，以建立您的 docfx 檔
1. 在 gh 頁面分支的 [版本] 資料夾中，使用您的版本名稱建立資料夾，並將產生的檔資料夾的內容複寫到該資料夾。
1. 將您的版本號碼新增至 web/version.js 中的 versionArray
1. 將修改過的 version.js 推送至 mrtk_development 分支，以及 gh-pages 分支中的變更

CI 將會挑選對 version.js 檔案所做的變更，並自動更新 [版本] 下拉式清單。

### <a name="supporting-development-branches-on-ci"></a>支援 CI 上的開發分支

版本控制系統也可以用來顯示 CI 所建立之其他開發分支的檔版本。 針對其中一個分支設定 CI 時，請確定您在 CI 上的 powershell 腳本將所產生之 docfx 輸出的內容複寫到在您分支之後命名的版本資料夾中，並將對應的版本專案新增至 web/version.js 檔案中。

## <a name="good-practices-for-developers"></a>適用于開發人員的最佳作法

* 使用 **相對路徑** （只要參考 MRTK 內部頁面）
* 使用已 **損壞的 UID** 連結到任何 MRTK API 頁面的 **交叉參考**
* 使用 **crefs 和 href** 連結至 **///批註** 中的內部或外部檔
* 針對資源檔使用此檔中指出的資料夾
* 在您修改現有的 Api 或更新檔頁面時，于 **本機執行 docfx** 並檢查輸出中的警告
* 完成併合並您的 PR 至其中一個官方 MRTK 分支之後，請留意 **CI 上** 的 docfx 警告

## <a name="common-errors-when-generating-docs"></a>產生檔時的常見錯誤

* yml 錯誤：通常發生于移動/重新命名或移除 md 檔案，但內容檔案 (yml) 指向該檔案的資料表未隨之更新。 在網站上，這會導致最上層或側邊導覽的連結中斷
* 批註錯誤
  * xml 標記錯誤-docfx 與任何其他 xml 剖析器一樣，無法處理格式不正確的 xml 標記。
  * crefs 中的打字錯誤
  * 不完整的命名空間識別碼-docfx 不需要完整命名空間至您所參考的符號，而是命名空間的相對部分（不包含在 cref 的周圍命名空間中）。
    * 範例：如果您是在 MixedReality 命名空間中，UnityInput 和您想要連結的檔案是 MixedReality。 IMixedRealityServiceRegistrar 您的 cref 看起來會像這樣： cref = "IMixedRealityServiceRegistrar" （）
  * 外部 crefs-只要沒有任何可用的 x 服務 (並列在 docfx 組建檔案中) crefs 至外部程式庫將無法運作。 如果您仍想要連結到沒有 x 服務但有線上 api 檔的特定外部符號，可以改用 href。 範例：連結到 Unity 的 EditorPrefs： `<see href="https://docs.unity3d.com/ScriptReference/EditorPrefs.html">EditorPrefs</see>`

## <a name="see-also"></a>另請參閱

* [MRTK 檔指南](DocumentationGuide.md)
* [Github.io 上的 MRTK 開發人員檔](https://microsoft.github.io/MixedRealityToolkit-Unity/)
* [DocFX](https://dotnet.github.io/docfx/index.html)
