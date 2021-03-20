---
title: DevDocGuide
description: 適用于 MRTK 的開發人員入口網站 gudie。
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
ms.localizationpriority: medium
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、GitHub
ms.openlocfilehash: 349379af4fa014044b366c852bcdd477ade734da
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104684411"
---
# <a name="developer-portal-generation-guide"></a><span data-ttu-id="03b75-104">開發人員入口網站產生指南</span><span class="sxs-lookup"><span data-stu-id="03b75-104">Developer portal generation guide</span></span>

<span data-ttu-id="03b75-105">MRTK 使用 [docfx](https://dotnet.github.io/docfx/index.html) ，從程式碼中的三個斜線批註，以及 MRTK 存放庫中的 md 檔案產生 html 檔。</span><span class="sxs-lookup"><span data-stu-id="03b75-105">MRTK uses [docfx](https://dotnet.github.io/docfx/index.html) to generate html documentation out of triple slash comments in code and .md files in the MRTK repository.</span></span> <span data-ttu-id="03b75-106">Docfx 檔產生會在 mrtk_development 分支中已完成的 Pr 上由 CI 自動觸發。</span><span class="sxs-lookup"><span data-stu-id="03b75-106">Docfx documentation generation is automatically triggered by CI on completed PRs in the mrtk_development branch.</span></span>
<span data-ttu-id="03b75-107">您可以在 [ [MRTK github.io] 頁面](https://microsoft.github.io/MixedRealityToolkit-Unity/)上找到開發人員檔的目前狀態</span><span class="sxs-lookup"><span data-stu-id="03b75-107">The current state of the developer documentation can be found on the [MRTK github.io page](https://microsoft.github.io/MixedRealityToolkit-Unity/)</span></span>

<span data-ttu-id="03b75-108">Docfx 支援 DFM Docfx Flavored Markdown，其中包括 GFM Github Flavored Markdown。</span><span class="sxs-lookup"><span data-stu-id="03b75-108">Docfx supports DFM Docfx Flavored Markdown which includes GFM Github Flavored Markdown.</span></span> <span data-ttu-id="03b75-109">您可以在[這裡](https://dotnet.github.io/docfx/tutorial/docfx.exe_user_manual.html)找到完整的檔和功能清單</span><span class="sxs-lookup"><span data-stu-id="03b75-109">The full documentation and feature list can be found [here](https://dotnet.github.io/docfx/tutorial/docfx.exe_user_manual.html)</span></span>

<span data-ttu-id="03b75-110">Docfx 不只是轉換，也會檢查檔中所有已使用的本機連結。</span><span class="sxs-lookup"><span data-stu-id="03b75-110">Docfx is not only converting but also checking all used local links in the documentation.</span></span> <span data-ttu-id="03b75-111">如果無法解析路徑，它就不會轉換成其 html 對等專案。</span><span class="sxs-lookup"><span data-stu-id="03b75-111">If a path can't be resolved it won't be converted into its html equivalent.</span></span> <span data-ttu-id="03b75-112">因此在參考其他本機檔案時，請務必只使用相對路徑。</span><span class="sxs-lookup"><span data-stu-id="03b75-112">Therefor it's important to only use relative paths when referring to other local files.</span></span>

## <a name="building-docfx-locally"></a><span data-ttu-id="03b75-113">在本機建立 docfx</span><span class="sxs-lookup"><span data-stu-id="03b75-113">Building docfx locally</span></span>

<span data-ttu-id="03b75-114">MRTK 存放庫中的 docfx 組建檔案可以用來在專案根目錄的 doc/子資料夾中建立開發人員檔的本機版本。</span><span class="sxs-lookup"><span data-stu-id="03b75-114">The docfx build files in the MRTK repo can be used to create a local version of the developer documentation in a doc/ subfolder in the root of the project.</span></span>

### <a name="setup"></a><span data-ttu-id="03b75-115">設定</span><span class="sxs-lookup"><span data-stu-id="03b75-115">Setup</span></span>

* <span data-ttu-id="03b75-116">取得[docfx](https://dotnet.github.io/docfx/index.html)的最新版本</span><span class="sxs-lookup"><span data-stu-id="03b75-116">get the latest version of [docfx](https://dotnet.github.io/docfx/index.html)</span></span>
* <span data-ttu-id="03b75-117">解壓縮電腦資料夾中的檔案</span><span class="sxs-lookup"><span data-stu-id="03b75-117">extract the files in a folder on your computer</span></span>
* <span data-ttu-id="03b75-118">將資料夾新增至您的環境變數中的路徑</span><span class="sxs-lookup"><span data-stu-id="03b75-118">add the folder to your PATH in your environment variables</span></span>

### <a name="generation"></a><span data-ttu-id="03b75-119">世代</span><span class="sxs-lookup"><span data-stu-id="03b75-119">Generation</span></span>

* <span data-ttu-id="03b75-120">在 MRTK 專案的根目錄中開啟 powershell 或命令提示字元</span><span class="sxs-lookup"><span data-stu-id="03b75-120">open a powershell or cmd prompt in the root of the MRTK project</span></span>
* <span data-ttu-id="03b75-121">`docfx docfx.json`使用-f 選項（選擇性）執行 (，以強制重建 doc 檔案) </span><span class="sxs-lookup"><span data-stu-id="03b75-121">execute `docfx docfx.json` (optionally with the -f option to force a rebuild of doc files)</span></span>
* <span data-ttu-id="03b75-122">`docfx serve doc`如果您不想要使用8888預設通訊埠，請使用-p *portnumber* 來執行 (（選擇性）) </span><span class="sxs-lookup"><span data-stu-id="03b75-122">execute `docfx serve doc` (optionally with -p *portnumber* if you don't want to use the 8888 default port)</span></span>
* <span data-ttu-id="03b75-123">以 localhost：*portnumber* 開啟網頁瀏覽器</span><span class="sxs-lookup"><span data-stu-id="03b75-123">open a web browser with localhost:*portnumber*</span></span>

<span data-ttu-id="03b75-124">請注意，在 json 組建檔案 docfx 上執行 docfx 命令時，會在檔中將任何中斷的連結顯示為警告。</span><span class="sxs-lookup"><span data-stu-id="03b75-124">Note that on executing the docfx command on the json build file docfx will show any broken links in the documentation as warning.</span></span>
<span data-ttu-id="03b75-125">當您在任何檔檔案或 API 上執行變更時，請務必要更新所有指向這些文章或程式碼的連結。</span><span class="sxs-lookup"><span data-stu-id="03b75-125">Please make sure whenever you perform changes on any of the documentation files or API to update all links pointing to these articles or code.</span></span>

## <a name="verifying-docfx-on-github"></a><span data-ttu-id="03b75-126">在 github 上驗證 docfx</span><span class="sxs-lookup"><span data-stu-id="03b75-126">Verifying docfx on github</span></span>

<span data-ttu-id="03b75-127">每當 PR 包含可能會影響檔 CI 的變更時，就必須執行這些變更，以針對中斷的連結執行 docfx 檢查。</span><span class="sxs-lookup"><span data-stu-id="03b75-127">Whenever a PR includes a change that might affect documentation CI has to be executed to run a check on docfx for broken links.</span></span> <span data-ttu-id="03b75-128">`/azp run mrtk_docs`如果使用者有足夠的許可權可將命令張貼到 PR 中，就可以將此觸發。</span><span class="sxs-lookup"><span data-stu-id="03b75-128">This can be triggered by posting the command `/azp run mrtk_docs` into the PR if the user has sufficient rights to do so.</span></span> <span data-ttu-id="03b75-129">此命令將會觸發 CI 作業，該作業會將檔組建新增至 PR 的 [檢查] 區段。</span><span class="sxs-lookup"><span data-stu-id="03b75-129">The command will trigger a CI job which will add a docs build to the checks section of the PR.</span></span>

## <a name="using-crefs-and-hrefs-in--documented-code"></a><span data-ttu-id="03b75-130">使用 crefs 和 href in///記錄的程式碼</span><span class="sxs-lookup"><span data-stu-id="03b75-130">Using crefs and hrefs in /// documented code</span></span>

<span data-ttu-id="03b75-131">Docfx 支援 crefs in///記錄的程式碼。</span><span class="sxs-lookup"><span data-stu-id="03b75-131">Docfx supports crefs in /// documented code.</span></span> <span data-ttu-id="03b75-132">它會將這些參考轉譯成指向產生的 api 檔或外部檔網站的連結。</span><span class="sxs-lookup"><span data-stu-id="03b75-132">It will translate those references to links pointing to the generated api documentation or to external documentation websites.</span></span>
<span data-ttu-id="03b75-133">用來解析外部程式庫/api 連結的外部 x 服務可以加入至屬性 *xrefService* 中的組建設定檔案的 docfx.js。</span><span class="sxs-lookup"><span data-stu-id="03b75-133">External xref services for resolving links to external libraries/apis can be added to the docfx.json build settings file in the property *xrefService*.</span></span>

<span data-ttu-id="03b75-134">針對未提供 x 服務 href 至檔網站的外部 api，可新增至批註。</span><span class="sxs-lookup"><span data-stu-id="03b75-134">For external apis that don't provide an xref service hrefs to the documentation website can be added to the comments.</span></span>

<span data-ttu-id="03b75-135">範例：</span><span class="sxs-lookup"><span data-stu-id="03b75-135">Examples:</span></span>

```c#
/// Links to MRTK internal class SystemType
/// <see cref="Microsoft.MixedReality.Toolkit.Utilities.SystemType"/>

/// Links to external API - link provided by xref service
/// <see cref="System.Collections.Generic.ICollection{Type}.Contains"/>

/// Links to Unity web API reference
/// <see href="https://docs.unity3d.com/ScriptReference/EditorGUI.PropertyField.html">EditorGUI.PropertyField</see>
```

## <a name="linking-in-md-documentation-files"></a><span data-ttu-id="03b75-136">連結 md 檔檔案</span><span class="sxs-lookup"><span data-stu-id="03b75-136">Linking in .md documentation files</span></span>

<span data-ttu-id="03b75-137">Docfx 正在轉譯和驗證產生的所有相對本機連結，不需要特殊的語法。</span><span class="sxs-lookup"><span data-stu-id="03b75-137">Docfx is translating and validating all relative local links on generation, there's no special syntax required.</span></span> <span data-ttu-id="03b75-138">參考另一篇檔文章的方法應該一律是參考對應的 md 檔案，永遠不是自動產生的 .html 檔案。</span><span class="sxs-lookup"><span data-stu-id="03b75-138">Referring to another documentation article should always be done by referring to the corresponding .md file, never the auto generated .html file.</span></span> <span data-ttu-id="03b75-139">請注意，本機檔案的所有連結都必須相對於您要修改的檔案。</span><span class="sxs-lookup"><span data-stu-id="03b75-139">Please note that all links to local files need to be relative to the file you're modifying.</span></span>

<span data-ttu-id="03b75-140">您可以使用 [交互參照](https://dotnet.github.io/docfx/tutorial/links_and_cross_references.html)來完成連結至 API 檔。</span><span class="sxs-lookup"><span data-stu-id="03b75-140">Linking to the API documentation can be done by using [cross references](https://dotnet.github.io/docfx/tutorial/links_and_cross_references.html).</span></span> <span data-ttu-id="03b75-141">Docfx 會藉由重整簽章，為所有 API 檔自動產生 Uid。</span><span class="sxs-lookup"><span data-stu-id="03b75-141">Docfx automatically generated UIDs for all API docs by mangling the signature.</span></span>

<span data-ttu-id="03b75-142">範例：</span><span class="sxs-lookup"><span data-stu-id="03b75-142">Example:</span></span>

<span data-ttu-id="03b75-143">這會連結至 [BOUNDARYSYSTEM API](xref:Microsoft.MixedReality.Toolkit.Boundary) 以及這個簡短版本： @Microsoft.MixedReality.Toolkit.Boundary</span><span class="sxs-lookup"><span data-stu-id="03b75-143">This links to the [BoundarySystem API](xref:Microsoft.MixedReality.Toolkit.Boundary) as well as this short version: @Microsoft.MixedReality.Toolkit.Boundary</span></span>

```md
This links to the [BoundarySystem API](xref:Microsoft.MixedReality.Toolkit.Boundary)
as well as this short version: @Microsoft.MixedReality.Toolkit.Boundary
```

## <a name="enumerating-available-xrefs"></a><span data-ttu-id="03b75-144">列舉可用的 xrefs</span><span class="sxs-lookup"><span data-stu-id="03b75-144">Enumerating available xrefs</span></span>

<span data-ttu-id="03b75-145">X 語法很難記住，您可以先在本機執行 docfx 來列舉所有可用的 x 識別碼：</span><span class="sxs-lookup"><span data-stu-id="03b75-145">Xref syntax can be difficult to remember - it's possible to enumerate all of the available xref IDs by first running docfx locally:</span></span>

> <span data-ttu-id="03b75-146">docfx docfx.js開啟</span><span class="sxs-lookup"><span data-stu-id="03b75-146">docfx docfx.json</span></span>

<span data-ttu-id="03b75-147">這會產生 xrefmap yml 檔案，該檔案將位於檔/xrefmap. yml 中。</span><span class="sxs-lookup"><span data-stu-id="03b75-147">This will generate an xrefmap.yml file, which will be located in docs/xrefmap.yml.</span></span>

<span data-ttu-id="03b75-148">例如，為了連結 HandleEvent 的下列多載，語法相當難懂：</span><span class="sxs-lookup"><span data-stu-id="03b75-148">For example, in order to link the following overload of HandleEvent, the syntax is fairly arcane:</span></span>

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

<span data-ttu-id="03b75-149">不過，您很容易就能搜尋名稱，然後使用整個 **uid 欄位** 作為 x。</span><span class="sxs-lookup"><span data-stu-id="03b75-149">It's easy, however, to search for the name and then use the entire **uid field** as the xref.</span></span>

<span data-ttu-id="03b75-150">在此範例中，x 看起來會像這樣： (x： MixedReality. BaseEventSystem. HandleEvent ``1(BaseEventData,ExecuteEvents.EventFunction{`` 0} ) ) </span><span class="sxs-lookup"><span data-stu-id="03b75-150">In this example, the xref would look like: (xref:Microsoft.MixedReality.Toolkit.BaseEventSystem.HandleEvent``1(BaseEventData,ExecuteEvents.EventFunction{``0}))</span></span>

## <a name="adding-new-md-files-to-developer-docs"></a><span data-ttu-id="03b75-151">將新的 md 檔案新增至開發人員檔</span><span class="sxs-lookup"><span data-stu-id="03b75-151">Adding new .md files to developer docs</span></span>

<span data-ttu-id="03b75-152">Docfx 會在 docfx.js的 [組建] 區段中，于新增為內容檔案的資料夾中，挑選任何 md 檔案，並從中產生 html 檔案。</span><span class="sxs-lookup"><span data-stu-id="03b75-152">Docfx will pick up any .md files in folders that are added as content files in the build section of the docfx.json and generate html files out of them.</span></span> <span data-ttu-id="03b75-153">若為新資料夾，則必須加入組建檔案中的對應專案。</span><span class="sxs-lookup"><span data-stu-id="03b75-153">For new folders a corresponding entry in the build file needs to be added.</span></span>

### <a name="navigation-entries"></a><span data-ttu-id="03b75-154">導覽專案</span><span class="sxs-lookup"><span data-stu-id="03b75-154">Navigation entries</span></span>

<span data-ttu-id="03b75-155">若要在開發人員檔 docfx 中判斷導覽的專案，請使用 yml/toc 資料表的內容檔案。</span><span class="sxs-lookup"><span data-stu-id="03b75-155">To determine the entries of the navigation in the developer docs docfx uses toc.yml/toc.md - table of content files.</span></span>
<span data-ttu-id="03b75-156">專案根目錄中的 toc 檔案會定義頂端導覽列中的專案，而存放庫之子資料夾中的 yml 檔案會定義提要欄位導覽中的子主題。</span><span class="sxs-lookup"><span data-stu-id="03b75-156">The toc file in the root of the project defines entries in the top navigation bar whereas the toc.yml files in the subfolders of the repo define subtopics in the sidebar navigation.</span></span>
<span data-ttu-id="03b75-157">yml 檔案可用於結構化，而且可以有任何數量的檔案。</span><span class="sxs-lookup"><span data-stu-id="03b75-157">toc.yml files can be used for structuring and there can be any amount of those files.</span></span> <span data-ttu-id="03b75-158">如需有關為 toc 定義專案的詳細資訊，請 yml 檢查 [toc 上的 docfx 檔專案](https://dotnet.github.io/docfx/tutorial/intro_toc.html)。</span><span class="sxs-lookup"><span data-stu-id="03b75-158">For more info about defining entries for toc.yml check the [docfx documentation entry on toc](https://dotnet.github.io/docfx/tutorial/intro_toc.html).</span></span>

## <a name="resource-files"></a><span data-ttu-id="03b75-159">資源檔</span><span class="sxs-lookup"><span data-stu-id="03b75-159">Resource files</span></span>

<span data-ttu-id="03b75-160">有些檔案（例如，檔可以參考的影像、影片或 Pdf），但不是由 docfx 進行轉換。</span><span class="sxs-lookup"><span data-stu-id="03b75-160">There are some files like images, videos or PDFs that the documentation can refer to but are not converted by docfx.</span></span> <span data-ttu-id="03b75-161">針對這些檔案，docfx.js中有一個資源區段。</span><span class="sxs-lookup"><span data-stu-id="03b75-161">For those files there's a resource section in the docfx.json.</span></span> <span data-ttu-id="03b75-162">該區段中的檔案只會進行複製，而不會在其上執行任何轉換。</span><span class="sxs-lookup"><span data-stu-id="03b75-162">Files in that section will only be copied over without performing any conversion on them.</span></span>

<span data-ttu-id="03b75-163">目前有下列資源類型的定義：</span><span class="sxs-lookup"><span data-stu-id="03b75-163">Currently there's a definition for the following resource types:</span></span>

| <span data-ttu-id="03b75-164">ResourceType</span><span class="sxs-lookup"><span data-stu-id="03b75-164">ResourceType</span></span> | <span data-ttu-id="03b75-165">路徑</span><span class="sxs-lookup"><span data-stu-id="03b75-165">Path</span></span> |
| --- | --- |
| <span data-ttu-id="03b75-166">映像</span><span class="sxs-lookup"><span data-stu-id="03b75-166">Images</span></span> | <span data-ttu-id="03b75-167">檔/影像/</span><span class="sxs-lookup"><span data-stu-id="03b75-167">Documentation/Images/</span></span> |

## <a name="releasing-a-new-version"></a><span data-ttu-id="03b75-168">發行新版本</span><span class="sxs-lookup"><span data-stu-id="03b75-168">Releasing a new version</span></span>

<span data-ttu-id="03b75-169">支援多個版本的開發人員檔，並且可以透過頂端功能表列中的 [版本] 下拉式清單來切換。</span><span class="sxs-lookup"><span data-stu-id="03b75-169">Multiple versions of developer docs are supported and can be switched by the version drop down in the top menu bar.</span></span> <span data-ttu-id="03b75-170">如果您要發行新的版本，請執行下列步驟，在開發人員檔頁面上安裝您的版本。</span><span class="sxs-lookup"><span data-stu-id="03b75-170">If you're releasing a new version perform the following steps to have your version on the developer docs page.</span></span>

1. <span data-ttu-id="03b75-171">選用：調整您的 docfx.js</span><span class="sxs-lookup"><span data-stu-id="03b75-171">Optional: Adjusting your docfx.json</span></span>  
<span data-ttu-id="03b75-172">根據您是否想要讓「改進此檔」以指向特定版本的 github 存放庫，您必須先將下列專案新增至 docfx.json 檔案中的 globalMetaData 區段，然後再呼叫 docfx 命令：</span><span class="sxs-lookup"><span data-stu-id="03b75-172">Depending on whether you want to have the "Improve this doc" to point to a specific version of the github repo you will have to add the following entry to the globalMetaData section in the docfx.json file before calling the docfx command:</span></span>

    ```json
    "_gitContribute": {
        "repo": "https://github.com/Microsoft/MixedRealityToolkit-Unity.git",
        "branch": "mrtk_development"
    }
    ```

    <span data-ttu-id="03b75-173">如果您未設定此設定，docfx 會預設為您正在從中呼叫 docfx 之目前資料夾的分支和存放庫。</span><span class="sxs-lookup"><span data-stu-id="03b75-173">If you don't set this up docfx will default to the branch and repo of the current folder you're calling docfx from.</span></span>

1. <span data-ttu-id="03b75-174">在存放庫的根目錄中呼叫 docfx docfx.js，以建立您的 docfx 檔</span><span class="sxs-lookup"><span data-stu-id="03b75-174">Create your docfx docs by calling docfx docfx.json in the root of the repo</span></span>
1. <span data-ttu-id="03b75-175">在 gh 頁面分支的 [版本] 資料夾中，使用您的版本名稱建立資料夾，並將產生的檔資料夾的內容複寫到該資料夾。</span><span class="sxs-lookup"><span data-stu-id="03b75-175">Create a folder with the name of your version in the version folder of the gh-pages branch and copy the contents of the generated doc folder into that folder</span></span>
1. <span data-ttu-id="03b75-176">將您的版本號碼新增至 web/version.js 中的 versionArray</span><span class="sxs-lookup"><span data-stu-id="03b75-176">Add your version number into the versionArray in web/version.js</span></span>
1. <span data-ttu-id="03b75-177">將修改過的 version.js 推送至 mrtk_development 分支，以及 gh-pages 分支中的變更</span><span class="sxs-lookup"><span data-stu-id="03b75-177">Push the modified version.js to mrtk_development branch and the changes in gh-pages branch</span></span>

<span data-ttu-id="03b75-178">CI 將會挑選對 version.js 檔案所做的變更，並自動更新 [版本] 下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="03b75-178">CI will pick up the changes done to the version.js file and update the version dropdown automatically.</span></span>

### <a name="supporting-development-branches-on-ci"></a><span data-ttu-id="03b75-179">支援 CI 上的開發分支</span><span class="sxs-lookup"><span data-stu-id="03b75-179">Supporting development branches on CI</span></span>

<span data-ttu-id="03b75-180">版本控制系統也可以用來顯示 CI 所建立之其他開發分支的檔版本。</span><span class="sxs-lookup"><span data-stu-id="03b75-180">The versioning system can also be used for showing doc versions from other dev branches that are built by CI.</span></span> <span data-ttu-id="03b75-181">針對其中一個分支設定 CI 時，請確定您在 CI 上的 powershell 腳本將所產生之 docfx 輸出的內容複寫到在您分支之後命名的版本資料夾中，並將對應的版本專案新增至 web/version.js 檔案中。</span><span class="sxs-lookup"><span data-stu-id="03b75-181">When setting up CI for one of those branches make sure your powershell script on CI copies the contents of the generated docfx output into a version folder named after your branch and add the corresponding version entry into the web/version.js file.</span></span>

## <a name="good-practices-for-developers"></a><span data-ttu-id="03b75-182">適用于開發人員的最佳作法</span><span class="sxs-lookup"><span data-stu-id="03b75-182">Good practices for developers</span></span>

* <span data-ttu-id="03b75-183">使用 **相對路徑** （只要參考 MRTK 內部頁面）</span><span class="sxs-lookup"><span data-stu-id="03b75-183">Use **relative paths** whenever referring to MRTK internal pages</span></span>
* <span data-ttu-id="03b75-184">使用已 **損壞的 UID** 連結到任何 MRTK API 頁面的 **交叉參考**</span><span class="sxs-lookup"><span data-stu-id="03b75-184">Use **cross references** for linking to any MRTK API page by using the **mangled UID**</span></span>
* <span data-ttu-id="03b75-185">使用 **crefs 和 href** 連結至 **///批註** 中的內部或外部檔</span><span class="sxs-lookup"><span data-stu-id="03b75-185">Use **crefs and hrefs** to link to internal or external documentation in **/// comments**</span></span>
* <span data-ttu-id="03b75-186">針對資源檔使用此檔中指出的資料夾</span><span class="sxs-lookup"><span data-stu-id="03b75-186">Use the indicated folders in this doc for resource files</span></span>
* <span data-ttu-id="03b75-187">在您修改現有的 Api 或更新檔頁面時，于 **本機執行 docfx** 並檢查輸出中的警告</span><span class="sxs-lookup"><span data-stu-id="03b75-187">**Run docfx locally** and check for warnings in the output whenever you modify existing APIs or update documentation pages</span></span>
* <span data-ttu-id="03b75-188">完成併合並您的 PR 至其中一個官方 MRTK 分支之後，請留意 **CI 上** 的 docfx 警告</span><span class="sxs-lookup"><span data-stu-id="03b75-188">Watch out for docfx **warnings on CI** after completing and merging your PR into one of the official MRTK branches</span></span>

## <a name="common-errors-when-generating-docs"></a><span data-ttu-id="03b75-189">產生檔時的常見錯誤</span><span class="sxs-lookup"><span data-stu-id="03b75-189">Common errors when generating docs</span></span>

* <span data-ttu-id="03b75-190">yml 錯誤：通常發生于移動/重新命名或移除 md 檔案，但內容檔案 (yml) 指向該檔案的資料表未隨之更新。</span><span class="sxs-lookup"><span data-stu-id="03b75-190">toc.yml errors: usually happens when an .md file gets moved/renamed or removed but the table of content file (toc.yml) pointing to that file wasn't updated accordingly.</span></span> <span data-ttu-id="03b75-191">在網站上，這會導致最上層或側邊導覽的連結中斷</span><span class="sxs-lookup"><span data-stu-id="03b75-191">On the website this will result in a broken link on our top level or side navigation</span></span>
* <span data-ttu-id="03b75-192">批註錯誤</span><span class="sxs-lookup"><span data-stu-id="03b75-192">/// comments errors</span></span>
  * <span data-ttu-id="03b75-193">xml 標記錯誤-docfx 與任何其他 xml 剖析器一樣，無法處理格式不正確的 xml 標記。</span><span class="sxs-lookup"><span data-stu-id="03b75-193">xml tag errors - docfx like any other xml parser can't handle malformed xml tags.</span></span>
  * <span data-ttu-id="03b75-194">crefs 中的打字錯誤</span><span class="sxs-lookup"><span data-stu-id="03b75-194">typos in crefs</span></span>
  * <span data-ttu-id="03b75-195">不完整的命名空間識別碼-docfx 不需要完整命名空間至您所參考的符號，而是命名空間的相對部分（不包含在 cref 的周圍命名空間中）。</span><span class="sxs-lookup"><span data-stu-id="03b75-195">incomplete namespace identifiers - docfx won't need the full namespace to the symbol you're referring to but the relative part of the namespace that's not included in the surrounding namespace of the cref.</span></span>
    * <span data-ttu-id="03b75-196">範例：如果您是在 MixedReality 命名空間中，UnityInput 和您想要連結的檔案是 MixedReality。 IMixedRealityServiceRegistrar 您的 cref 看起來會像這樣： cref = "IMixedRealityServiceRegistrar" （）</span><span class="sxs-lookup"><span data-stu-id="03b75-196">Example: if you're in a namespace Microsoft.MixedReality.Toolkit.Core.Providers.UnityInput and the file you want to link in is Microsoft.MixedReality.Toolkit.Core.Interfaces.IMixedRealityServiceRegistrar your cref can look like this: cref="Interfaces.IMixedRealityServiceRegistrar"</span></span>
  * <span data-ttu-id="03b75-197">外部 crefs-只要沒有任何可用的 x 服務 (並列在 docfx 組建檔案中) crefs 至外部程式庫將無法運作。</span><span class="sxs-lookup"><span data-stu-id="03b75-197">External crefs - As long as there's no xref service available (and listed in the docfx build file) crefs to external libraries won't work.</span></span> <span data-ttu-id="03b75-198">如果您仍想要連結到沒有 x 服務但有線上 api 檔的特定外部符號，可以改用 href。</span><span class="sxs-lookup"><span data-stu-id="03b75-198">If you still want to link to a specific external symbol that doesn't have xref service but an online api documentation you can use a href instead.</span></span> <span data-ttu-id="03b75-199">範例：連結到 Unity 的 EditorPrefs： `<see href="https://docs.unity3d.com/ScriptReference/EditorPrefs.html">EditorPrefs</see>`</span><span class="sxs-lookup"><span data-stu-id="03b75-199">Example: linking to EditorPrefs of Unity: `<see href="https://docs.unity3d.com/ScriptReference/EditorPrefs.html">EditorPrefs</see>`</span></span>

## <a name="see-also"></a><span data-ttu-id="03b75-200">另請參閱</span><span class="sxs-lookup"><span data-stu-id="03b75-200">See also</span></span>

* [<span data-ttu-id="03b75-201">MRTK 檔指南</span><span class="sxs-lookup"><span data-stu-id="03b75-201">MRTK documentation guide</span></span>](DocumentationGuide.md)
* [<span data-ttu-id="03b75-202">Github.io 上的 MRTK 開發人員檔</span><span class="sxs-lookup"><span data-stu-id="03b75-202">MRTK developer documentation on github.io</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/)
* [<span data-ttu-id="03b75-203">DocFX</span><span class="sxs-lookup"><span data-stu-id="03b75-203">DocFX</span></span>](https://dotnet.github.io/docfx/index.html)
