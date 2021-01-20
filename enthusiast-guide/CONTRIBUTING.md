---
title: 參與指示
description: 瞭解參與 Windows Mixed Reality 愛好者指南的基本步驟和指導方針。 我們非常感謝您提供意見反應、編輯、新增和協助。
author: mattwojo
ms.author: mattwoj
ms.date: 09/16/2020
ms.topic: article
keywords: Windows Mixed Reality，混合的現實，虛擬實境，VR，MR，意見反應，意見反應中樞，bug
appliesto:
- Windows 10
ms.openlocfilehash: 28ca1653019252c749fe5977a06bff4503800c10
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/20/2021
ms.locfileid: "98580188"
---
# <a name="contributing-to-the-mixed-reality-enthusiast-guide"></a><span data-ttu-id="eeb97-105">參與混合現實愛好者指南</span><span class="sxs-lookup"><span data-stu-id="eeb97-105">Contributing to the Mixed Reality Enthusiast Guide</span></span>

<span data-ttu-id="eeb97-106">感謝您對愛好者指南的興趣。</span><span class="sxs-lookup"><span data-stu-id="eeb97-106">Thank you for your interest in the Enthusiast Guide.</span></span> <span data-ttu-id="eeb97-107">我們非常感謝您的意見反應、編輯、新增專案，以及協助改進我們的檔。本頁面涵蓋參與的基本步驟和指導方針。</span><span class="sxs-lookup"><span data-stu-id="eeb97-107">We appreciate your feedback, edits, additions and help with improving our docs. This page covers the basic steps and guidelines for contributing.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="eeb97-108">所有發佈至 docs.microsoft.com 的存放庫皆採用 [Microsoft 開放原始碼管理辦法](https://opensource.microsoft.com/codeofconduct/) \(英文\)。</span><span class="sxs-lookup"><span data-stu-id="eeb97-108">All repositories that publish to docs.microsoft.com have adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/).</span></span> <span data-ttu-id="eeb97-109">如需詳細資訊，請參閱[管理辦法常見問題集](https://opensource.microsoft.com/codeofconduct/faq/) \(英文\)。如有任何問題或意見，請連絡 [opencode@microsoft.com](mailto:opencode@microsoft.com)。</span><span class="sxs-lookup"><span data-stu-id="eeb97-109">For more information see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) or contact [opencode@microsoft.com](mailto:opencode@microsoft.com) with any questions or comments.</span></span><br>
>
> <span data-ttu-id="eeb97-110">您在公用存放庫中針對文件和程式碼範例所提交的次要修正或釐清，將受到 [docs.microsoft.com 使用條款](/legal/termsofuse)的約束。</span><span class="sxs-lookup"><span data-stu-id="eeb97-110">Minor corrections or clarifications to documentation and code examples in public repositories are covered by the [docs.microsoft.com Terms of Use](/legal/termsofuse).</span></span> <span data-ttu-id="eeb97-111">如果您不是 Microsoft 的員工，在做出全新或重要的變更時，系統將會在提取要求中產生註解，要求您提交線上版的貢獻授權合約 (CLA)。</span><span class="sxs-lookup"><span data-stu-id="eeb97-111">New or significant changes will generate a comment in the pull request asking you to submit an online Contribution License Agreement (CLA) if you are not an employee of Microsoft.</span></span> <span data-ttu-id="eeb97-112">您必須先填寫線上表單，我們才會接受您的提取要求。</span><span class="sxs-lookup"><span data-stu-id="eeb97-112">We need you to complete the online form before we can accept your pull request.</span></span>

## <a name="before-you-start"></a><span data-ttu-id="eeb97-113">在您開始使用 Intune 之前</span><span class="sxs-lookup"><span data-stu-id="eeb97-113">Before you start</span></span>

<span data-ttu-id="eeb97-114">如果您還沒有帳戶，則必須 [建立一個 GitHub 帳戶](https://github.com/join)。</span><span class="sxs-lookup"><span data-stu-id="eeb97-114">If you don't already have one, you'll need to [create a GitHub account](https://github.com/join).</span></span>

>[!NOTE]
><span data-ttu-id="eeb97-115">如果您是 Microsoft 員工，請將您的 GitHub 帳戶連結到 [Microsoft 開放原始碼入口網站](https://repos.opensource.microsoft.com/)上的 microsoft 別名。</span><span class="sxs-lookup"><span data-stu-id="eeb97-115">If you're a Microsoft employee, link your GitHub account to your Microsoft alias on the [Microsoft Open Source portal](https://repos.opensource.microsoft.com/).</span></span> <span data-ttu-id="eeb97-116">加入「 **Microsoft** 」和「 **MicrosoftDocs** 」組織。</span><span class="sxs-lookup"><span data-stu-id="eeb97-116">Join the **"Microsoft"** and **"MicrosoftDocs"** organizations.</span></span>

<span data-ttu-id="eeb97-117">設定您的 GitHub 帳戶時，我們也建議這些安全性預防措施：</span><span class="sxs-lookup"><span data-stu-id="eeb97-117">When setting up your GitHub account, we also recommend these security precautions:</span></span>
- <span data-ttu-id="eeb97-118">[為您的 Github 帳戶建立強式密碼](https://github.com/settings/admin)。</span><span class="sxs-lookup"><span data-stu-id="eeb97-118">Create a [strong password for your Github account](https://github.com/settings/admin).</span></span>
- <span data-ttu-id="eeb97-119">啟用 [雙因素驗證](https://github.com/settings/two_factor_authentication/configure)。</span><span class="sxs-lookup"><span data-stu-id="eeb97-119">Enable [two-factor authentication](https://github.com/settings/two_factor_authentication/configure).</span></span>
- <span data-ttu-id="eeb97-120">將您的復原 [碼](https://github.com/settings/auth/recovery-codes) 儲存在安全的地方。</span><span class="sxs-lookup"><span data-stu-id="eeb97-120">Save your [recovery codes](https://github.com/settings/auth/recovery-codes) in a safe place.</span></span>
- <span data-ttu-id="eeb97-121">更新您的 [公用設定檔設定](https://github.com/settings/profile)。</span><span class="sxs-lookup"><span data-stu-id="eeb97-121">Update your [public profile settings](https://github.com/settings/profile).</span></span>
   - <span data-ttu-id="eeb97-122">設定您的名稱，並考慮將您的 *公用電子郵件* 設定為 *不顯示我的電子郵件地址*。</span><span class="sxs-lookup"><span data-stu-id="eeb97-122">Set your name, and consider setting your *Public email* to *Don't show my email address*.</span></span>
   - <span data-ttu-id="eeb97-123">建議您上傳個人資料圖片，因為您所參與的檔頁面上會顯示縮圖。</span><span class="sxs-lookup"><span data-stu-id="eeb97-123">We recommend you upload a profile picture because a thumbnail is shown on docs pages you contribute to.</span></span>
- <span data-ttu-id="eeb97-124">如果您打算使用命令列，請考慮設定 [適用于 Windows 的 Git 認證管理員](https://github.com/Microsoft/Git-Credential-Manager-for-Windows/releases/latest)。</span><span class="sxs-lookup"><span data-stu-id="eeb97-124">If you plan to use the command line, consider setting up [Git Credential Manager for Windows](https://github.com/Microsoft/Git-Credential-Manager-for-Windows/releases/latest).</span></span> <span data-ttu-id="eeb97-125">如此一來，您就不需要在每次進行投稿時輸入您的密碼。</span><span class="sxs-lookup"><span data-stu-id="eeb97-125">That way, you won't have to enter your password every time you make a contribution.</span></span>

<span data-ttu-id="eeb97-126">發佈系統系結至 GitHub，因此這些步驟非常重要。</span><span class="sxs-lookup"><span data-stu-id="eeb97-126">The publishing system is tied to GitHub, so these steps are important.</span></span> <span data-ttu-id="eeb97-127">您將會使用您的 GitHub 別名，列為每篇文章的作者或參與者。</span><span class="sxs-lookup"><span data-stu-id="eeb97-127">You'll be listed as either author or contributor to each article using your GitHub alias.</span></span>

## <a name="how-to-make-a-change"></a><span data-ttu-id="eeb97-128">如何進行變更</span><span class="sxs-lookup"><span data-stu-id="eeb97-128">How to make a change</span></span>

| <span data-ttu-id="eeb97-129">若要建議變更文件，請遵循下列步驟：</span><span class="sxs-lookup"><span data-stu-id="eeb97-129">To suggest a change to the docs, follow these steps:</span></span> | <span data-ttu-id="eeb97-130">螢幕擷取畫面</span><span class="sxs-lookup"><span data-stu-id="eeb97-130">Screenshots</span></span> |
| :------------------- | :--------: |
| <span data-ttu-id="eeb97-131">1. 如果您要查看 Docs.microsoft.com 頁面，請按一下頁面右上方的 [ **編輯** ] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="eeb97-131">1. If you're viewing a Docs.microsoft.com page, click the **Edit** button in the upper right of the page.</span></span>  <span data-ttu-id="eeb97-132">您將重新導向至 [GitHub 存放庫](https://github.com/MicrosoftDocs/mixedreality-enthusiast-guide)中對應的 Markdown 原始程式檔。</span><span class="sxs-lookup"><span data-stu-id="eeb97-132">You will be redirected to the corresponding Markdown source file in the [GitHub repository](https://github.com/MicrosoftDocs/mixedreality-enthusiast-guide).</span></span> | ![編輯按鈕](images/edit_button.jpg) |
| <span data-ttu-id="eeb97-134">2. 如果您還沒有 GitHub 帳戶，請按一下右上方的 [ **註冊** ]，然後建立新的帳戶。</span><span class="sxs-lookup"><span data-stu-id="eeb97-134">2. If you don't already have a GitHub account, click **Sign Up** in the upper right and create a new account.</span></span> | ![註冊按鈕](images/signup-for-github-button.png)|
| <span data-ttu-id="eeb97-136">3. 在開啟的對應 GitHub 頁面上，按一下 [編輯] (鉛筆圖示) 。</span><span class="sxs-lookup"><span data-stu-id="eeb97-136">3. On the corresponding GitHub page that opens, click Edit (the pencil icon).</span></span> | ![鉛筆按鈕](images/pencil_button.jpg)|
| <span data-ttu-id="eeb97-138">4. 在 [編輯檔案] 窗格中， [更新檔案中繼資料](#updating-metadata) ，並使用 Markdown 語言來變更內容。</span><span class="sxs-lookup"><span data-stu-id="eeb97-138">4. In the Edit file pane, [update the files metadata](#updating-metadata) and use Markdown language to change the content.</span></span> <span data-ttu-id="eeb97-139"> ([如何寫入 markdown。](https://help.github.com/articles/basic-writing-and-formatting-syntax/)) </span><span class="sxs-lookup"><span data-stu-id="eeb97-139">([How to write markdown.](https://help.github.com/articles/basic-writing-and-formatting-syntax/))</span></span>| ![編輯檔案](images/edit-in-github.png)|
| <span data-ttu-id="eeb97-141">5. 按一下 [預覽變更] 以確認格式如預期般顯示。</span><span class="sxs-lookup"><span data-stu-id="eeb97-141">5. Click Preview changes to verify the formatting looks as expected.</span></span> | ![預覽變更](images/edit-in-github.png)|
| <span data-ttu-id="eeb97-143">6. 當您完成時，請滾動到頁面底部，然後按一下 [建議檔案變更]，您會看到 [比較變更] 頁面，讓您驗證變更。</span><span class="sxs-lookup"><span data-stu-id="eeb97-143">6. When you're done, scroll to the bottom of the page and click "Propose file change", you will be presented with a "Comparing changes" page, allowing you to verify your changes.</span></span> <span data-ttu-id="eeb97-144">然後按一下 [建立提取要求] 按鈕來提交您的變更。</span><span class="sxs-lookup"><span data-stu-id="eeb97-144">Then click the "Create pull request" button to submit your changes.</span></span> <span data-ttu-id="eeb97-145">而到這裡您就已經完成了！</span><span class="sxs-lookup"><span data-stu-id="eeb97-145">At this point you are finished!</span></span> | ![提議變更](images/propose.jpg)|

<span data-ttu-id="eeb97-147">當您透過提取) 要求 (提交變更之後，將會由檔團隊的成員進行審核。</span><span class="sxs-lookup"><span data-stu-id="eeb97-147">After you submit changes (via a pull request), they will be reviewed by a member of the documentation team.</span></span> <span data-ttu-id="eeb97-148">如果接受您的要求，則會將更新發行至 [https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide](/windows/mixed-reality/enthusiast-guide) 。</span><span class="sxs-lookup"><span data-stu-id="eeb97-148">If your request is accepted, updates are published to [https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide](/windows/mixed-reality/enthusiast-guide).</span></span>

<span data-ttu-id="eeb97-149">\* 僅供內部審核之用，您可以在中看到您的變更 [https://review.docs.microsoft.com/windows/mixed-reality/enthusiast-guide](https://review.docs.microsoft.com/en-us/windows/mixed-reality/enthusiast-guide/?branch=master) 。</span><span class="sxs-lookup"><span data-stu-id="eeb97-149">\*For internal review only, you can see your changes at [https://review.docs.microsoft.com/windows/mixed-reality/enthusiast-guide](https://review.docs.microsoft.com/en-us/windows/mixed-reality/enthusiast-guide/?branch=master).</span></span>

### <a name="updating-metadata"></a><span data-ttu-id="eeb97-150">更新中繼資料</span><span class="sxs-lookup"><span data-stu-id="eeb97-150">Updating Metadata</span></span>

<span data-ttu-id="eeb97-151">更新每篇文章頂端的中繼資料：</span><span class="sxs-lookup"><span data-stu-id="eeb97-151">Update metadata at the top of each article:</span></span>
   * <span data-ttu-id="eeb97-152">**標題**：在瀏覽器索引標籤中看到的頁面標題。</span><span class="sxs-lookup"><span data-stu-id="eeb97-152">**title**: Page title that appears in the browser tab when the article is being viewed.</span></span> <span data-ttu-id="eeb97-153">頁面標題適用于 SEO 和索引編制，因此除非必要，否則請不要變更標題 (但在檔變成公用) 之前，這一點較不重要。</span><span class="sxs-lookup"><span data-stu-id="eeb97-153">Page titles are used for SEO and indexing, so don't change the title unless necessary (though this is less critical before documentation goes public).</span></span>
   * <span data-ttu-id="eeb97-154">**描述**：撰寫文章內容的簡短描述，以提升 SEO 和探索。</span><span class="sxs-lookup"><span data-stu-id="eeb97-154">**description**: Write a brief description of the article's content, which boosts SEO and discovery.</span></span>
   * <span data-ttu-id="eeb97-155">**作者**：如果您是頁面的主要擁有者，請在此新增您的 GitHub 別名。</span><span class="sxs-lookup"><span data-stu-id="eeb97-155">**author**: If you're the primary owner of the page, add your GitHub alias here.</span></span>
   * <span data-ttu-id="eeb97-156">**ms. 作者**：如果您是頁面的主要擁有者，請在這裡新增您的 Microsoft 別名， (您不需要 @microsoft.com 的別名) 。</span><span class="sxs-lookup"><span data-stu-id="eeb97-156">**ms.author**: If you're the primary owner of the page, add your Microsoft alias here (you don't need @microsoft.com, just the alias).</span></span>
   * <span data-ttu-id="eeb97-157">**ms. 日期**：如果您要將主要內容新增至頁面，請更新日期，而不是針對像是澄清、格式化、文法或拼寫的修正。</span><span class="sxs-lookup"><span data-stu-id="eeb97-157">**ms.date**: Update the date if you're adding major content to the page, but not for fixes like clarification, formatting, grammar, or spelling.</span></span>
   * <span data-ttu-id="eeb97-158">**關鍵字**：關鍵字有助於 SEO (搜尋引擎優化) 。</span><span class="sxs-lookup"><span data-stu-id="eeb97-158">**keywords**: Keywords aid in SEO (search engine optimization).</span></span> <span data-ttu-id="eeb97-159">新增您的文章所特有的關鍵字（以逗號和空格分隔），但在清單中的最後一個關鍵字之後不會有任何標點符號。</span><span class="sxs-lookup"><span data-stu-id="eeb97-159">Add keywords, separated by a comma and a space, that are specific to your article, but no punctuation after the last keyword in your list.</span></span> <span data-ttu-id="eeb97-160">您不需要新增套用至所有文章的全域關鍵字，因為這些都是在其他地方管理。</span><span class="sxs-lookup"><span data-stu-id="eeb97-160">You don't need to add global keywords that apply to all articles, as those are managed elsewhere.</span></span> 

### <a name="renaming-or-deleting-an-existing-article"></a><span data-ttu-id="eeb97-161">重新命名或刪除現有文章</span><span class="sxs-lookup"><span data-stu-id="eeb97-161">Renaming or deleting an existing article</span></span>

<span data-ttu-id="eeb97-162">如果您的變更將重新命名或刪除現有的文章，請務必新增重新導向。</span><span class="sxs-lookup"><span data-stu-id="eeb97-162">If your change will rename or delete an existing article, be sure to add a redirect.</span></span> <span data-ttu-id="eeb97-163">如此一來，任何人只要有現有文章的連結，就都能在正確的位置結束。</span><span class="sxs-lookup"><span data-stu-id="eeb97-163">That way, anyone with a link to the existing article will still end up in the right place.</span></span> <span data-ttu-id="eeb97-164">重新導向是由存放庫根目錄中的 .openpublishing.redirection.json 檔案來管理。</span><span class="sxs-lookup"><span data-stu-id="eeb97-164">Redirects are managed by the .openpublishing.redirection.json file in the root of the repo.</span></span>

<span data-ttu-id="eeb97-165">若要將重新導向新增至 .openpublishing.redirection.js，請將專案新增至 `redirections` 陣列：</span><span class="sxs-lookup"><span data-stu-id="eeb97-165">To add a redirect to .openpublishing.redirection.json, add an entry to the `redirections` array:</span></span>

```json
{
    "redirections": [
        {
            "source_path": "mixed-reality-docs/enthusiast-guide/old-article.md",
            "redirect_url": "new-article#section-about-old-topic",
            "redirect_document_id": false
        },
```

- <span data-ttu-id="eeb97-166">`source_path`是您即將移除之舊發行項的相對存放庫路徑。</span><span class="sxs-lookup"><span data-stu-id="eeb97-166">The `source_path` is the relative repository path to the old article that you're removing.</span></span> <span data-ttu-id="eeb97-167">請確定路徑的開頭為 `mixed-reality-docs/enthusiast-guide` 且結尾為 `.md` 。</span><span class="sxs-lookup"><span data-stu-id="eeb97-167">Be sure the path starts with `mixed-reality-docs/enthusiast-guide` and ends with `.md`.</span></span>
- <span data-ttu-id="eeb97-168">`redirect_url`是舊發行項到新文章的相對公用 URL。</span><span class="sxs-lookup"><span data-stu-id="eeb97-168">The `redirect_url` is the relative public URL from the old article to the new article.</span></span> <span data-ttu-id="eeb97-169">請確定此 URL **不** 包含 `mixed-reality-docs/enthusiast-guide` 或 `.md` ，因為它參考的是公用 URL，而不是存放庫路徑。</span><span class="sxs-lookup"><span data-stu-id="eeb97-169">Be sure that this URL **doesn't** contain `mixed-reality-docs/enthusiast-guide` or `.md`, as it refers to the public URL and not the repository path.</span></span> <span data-ttu-id="eeb97-170">允許使用連結至新文章內的區段 `#section` 。</span><span class="sxs-lookup"><span data-stu-id="eeb97-170">Linking to a section within the new article using `#section` is allowed.</span></span> <span data-ttu-id="eeb97-171">如有必要，您也可以在此處使用其他網站的絕對路徑。</span><span class="sxs-lookup"><span data-stu-id="eeb97-171">You can also use an absolute path to another site here, if necessary.</span></span>
- <span data-ttu-id="eeb97-172">`redirect_document_id` 指出您是否要保留先前檔案中的檔識別碼。</span><span class="sxs-lookup"><span data-stu-id="eeb97-172">`redirect_document_id` indicates whether you would like to keep the document ID from the previous file.</span></span> <span data-ttu-id="eeb97-173">預設為 `false`。</span><span class="sxs-lookup"><span data-stu-id="eeb97-173">The default is `false`.</span></span> <span data-ttu-id="eeb97-174">`true`如果您想要保留重新導向之發行項的屬性值，請使用 `ms.documentid` 。</span><span class="sxs-lookup"><span data-stu-id="eeb97-174">Use `true` if you want to preserve the `ms.documentid` attribute value from the redirected article.</span></span> <span data-ttu-id="eeb97-175">如果您保留檔識別碼，資料（例如頁面流覽和排名）將會傳送至目標文章。</span><span class="sxs-lookup"><span data-stu-id="eeb97-175">If you preserve the document ID, data, such as page views and rankings, will be transferred to the target article.</span></span> <span data-ttu-id="eeb97-176">如果重新導向主要是重新命名，而不是僅涵蓋部分相同內容之不同文章的指標，請這麼做。</span><span class="sxs-lookup"><span data-stu-id="eeb97-176">Do this if the redirect is primarily a rename, and not a pointer to different article that only covers some of the same content.</span></span>

<span data-ttu-id="eeb97-177">如果您新增重新導向，也請務必刪除舊的檔案。</span><span class="sxs-lookup"><span data-stu-id="eeb97-177">If you add a redirect, be sure to delete the old file as well.</span></span>

### <a name="creating-a-new-article"></a><span data-ttu-id="eeb97-178">建立新文章</span><span class="sxs-lookup"><span data-stu-id="eeb97-178">Creating a new article</span></span>

<span data-ttu-id="eeb97-179">使用下列工作流程，在網頁瀏覽器中透過 GitHub 建立檔儲存機制中的 *新文章* ：</span><span class="sxs-lookup"><span data-stu-id="eeb97-179">Use the following workflow to *create new articles* in the documentation repo via GitHub in a web browser:</span></span>

1. <span data-ttu-id="eeb97-180">使用右上方) 中的 [ **分叉** ] 按鈕，建立從 MicrosoftDocs/mixed-reality/tree/檔/愛好者指南 ' master ' 分支 (的分叉。</span><span class="sxs-lookup"><span data-stu-id="eeb97-180">Create a fork off the MicrosoftDocs/mixed-reality/tree/docs/enthusiast-guide 'master' branch (using the **Fork** button in the top right).</span></span>

   ![分叉 master 分支。](images/forkbranch.png)
2. <span data-ttu-id="eeb97-182">在 [mixed-reality/愛好者指南] 資料夾中，選取右上方的 [ **建立新** 檔案]。</span><span class="sxs-lookup"><span data-stu-id="eeb97-182">In the "mixed-reality/enthusiast-guide" folder, select **Create new file** in the top right.</span></span>
3. <span data-ttu-id="eeb97-183">建立發行項的頁面名稱 (使用連字號，而不是空格，而且不使用標點符號或單引號) 並附加 "md"</span><span class="sxs-lookup"><span data-stu-id="eeb97-183">Create a page name for the article (use hyphens instead of spaces and don't use punctuation or apostrophes) and append ".md"</span></span>

   ![命名您的新頁面。](images/newpagetitle.PNG)
   
   >[!IMPORTANT]
   ><span data-ttu-id="eeb97-185">請確定您是從「混合式事實-檔/愛好者」資料夾內建立新的文章。</span><span class="sxs-lookup"><span data-stu-id="eeb97-185">Make sure you create the new article from within the "mixed-reality-docs/enthusiast" folder.</span></span> <span data-ttu-id="eeb97-186">您可以在新的檔案名行中檢查 "/mixed-reality-docs/enthusiast-guide" 來確認這一點。</span><span class="sxs-lookup"><span data-stu-id="eeb97-186">You can confirm this by checking for "/mixed-reality-docs/enthusiast-guide" in the new file name line.</span></span>

4. <span data-ttu-id="eeb97-187">在新頁面的頂端，加入下列中繼資料區塊：</span><span class="sxs-lookup"><span data-stu-id="eeb97-187">At the top of your new page, add the following metadata block:</span></span>

   ```md
   ---
   title:
   description:
   author:
   ms.author:
   ms.date:
   ms.topic: article
   keywords:
   ---
   ```

5. <span data-ttu-id="eeb97-188">根據 [上一節](#updating-metadata)中的指示，填寫相關的元資料欄位。</span><span class="sxs-lookup"><span data-stu-id="eeb97-188">Fill in the relevant metadata fields per the instructions in the [section above](#updating-metadata).</span></span>
6. <span data-ttu-id="eeb97-189">使用 [Markdown 基本概念](#markdown-basics)來撰寫文章內容。</span><span class="sxs-lookup"><span data-stu-id="eeb97-189">Write article content using [Markdown basics](#markdown-basics).</span></span>
7. <span data-ttu-id="eeb97-190">在 `## See also` 文章底部新增一個區段，並提供其他相關文章的連結。</span><span class="sxs-lookup"><span data-stu-id="eeb97-190">Add a `## See also` section at the bottom of the article with links to other relevant articles.</span></span>
8. <span data-ttu-id="eeb97-191">完成時，選取 [ **認可新** 檔案]。</span><span class="sxs-lookup"><span data-stu-id="eeb97-191">When finished, select **Commit new file**.</span></span>
9. <span data-ttu-id="eeb97-192">選取 **新的提取要求** ，並將您分支的「主要」分支合併為 MicrosoftDocs/mixed-現實/愛好者指南 ' master ' (確定箭號指向) 的正確方式。</span><span class="sxs-lookup"><span data-stu-id="eeb97-192">Select **New pull request** and merge your fork's 'master' branch into MicrosoftDocs/mixed-reality/enthusiast-guide 'master' (make sure the arrow is pointing the correct way).</span></span>

   ![從您的分支建立提取要求至 MicrosoftDocs/混合-現實/愛好者指南](images/pr_to_master.PNG)

## <a name="working-with-branches"></a><span data-ttu-id="eeb97-194">使用分支</span><span class="sxs-lookup"><span data-stu-id="eeb97-194">Working with Branches</span></span>

<span data-ttu-id="eeb97-195">[混合現實愛好者指南 GitHub 存放庫](https://github.com/MicrosoftDocs/mixedreality-enthusiast-guide)會使用兩個主要的父分支：[主要](https://github.com/MicrosoftDocs/mixedreality-enthusiast-guide/tree/master)，此內容可在[預備網站](https://review.docs.microsoft.com/windows/mixed-reality/enthusiast-guide)上以及[即時](https://github.com/MicrosoftDocs/mixedreality-enthusiast-guide/tree/live)[網站](/windows/mixed-reality/enthusiast-guide)上的內容中進行檢查。</span><span class="sxs-lookup"><span data-stu-id="eeb97-195">The [Mixed Reality Enthusiast Guide GitHub repository](https://github.com/MicrosoftDocs/mixedreality-enthusiast-guide) utilizes two main parent branches: [Master](https://github.com/MicrosoftDocs/mixedreality-enthusiast-guide/tree/master), this content can be reviewed on the [staging site](https://review.docs.microsoft.com/windows/mixed-reality/enthusiast-guide), and [Live](https://github.com/MicrosoftDocs/mixedreality-enthusiast-guide/tree/live), for content appearing on the [live site](/windows/mixed-reality/enthusiast-guide).</span></span>

<span data-ttu-id="eeb97-196">參與時，請 (PR) 提交您的提取要求至 **主要** 分支。</span><span class="sxs-lookup"><span data-stu-id="eeb97-196">When making contributions, please submit your Pull Request (PR) to the **Master** branch.</span></span> <span data-ttu-id="eeb97-197">此分支可在預備網站上檢視，且應只包含已準備好要即時發佈的投稿。</span><span class="sxs-lookup"><span data-stu-id="eeb97-197">This branch can be viewed on the staging site and should only contain contributions that are ready to be published live.</span></span> <span data-ttu-id="eeb97-198">您也可以使用您自己的唯一分支名稱來建立並提交分支，以供在預備網站中選取和查看。</span><span class="sxs-lookup"><span data-stu-id="eeb97-198">You may also create and submit a branch with your own unique branch name which can be selected and viewed in the staging site.</span></span> <span data-ttu-id="eeb97-199"> (**Live** 分支只允許供內容管理員使用。 ) </span><span class="sxs-lookup"><span data-stu-id="eeb97-199">(The **Live** branch is only allowed for use by the content administrators.)</span></span>

## <a name="markdown-basics"></a><span data-ttu-id="eeb97-200">Markdown 基本概念</span><span class="sxs-lookup"><span data-stu-id="eeb97-200">Markdown basics</span></span>

<span data-ttu-id="eeb97-201">下列資源將協助您瞭解如何使用 Markdown 語言來編輯檔：</span><span class="sxs-lookup"><span data-stu-id="eeb97-201">The following resources will help you learn how to edit documentation using the Markdown language:</span></span>

- [<span data-ttu-id="eeb97-202">Markdown 基本概念</span><span class="sxs-lookup"><span data-stu-id="eeb97-202">Markdown basics</span></span>](https://help.github.com/articles/basic-writing-and-formatting-syntax/)
- [<span data-ttu-id="eeb97-203">Markdown 的參考海報</span><span class="sxs-lookup"><span data-stu-id="eeb97-203">Markdown-at-a-glance reference poster</span></span>](images/MarkdownPoster.pdf)
- [<span data-ttu-id="eeb97-204">針對 docs.microsoft.com 撰寫 Markdown 的其他資源</span><span class="sxs-lookup"><span data-stu-id="eeb97-204">Additional resources for writing Markdown for docs.microsoft.com</span></span>](/contribute/how-to-write-use-markdown)

### <a name="adding-tables"></a><span data-ttu-id="eeb97-205">加入資料表</span><span class="sxs-lookup"><span data-stu-id="eeb97-205">Adding tables</span></span>

<span data-ttu-id="eeb97-206">由於 docs.microsoft.com 樣式表的方式，即使您嘗試內嵌 CSS，它們也不會有框線或自訂樣式。</span><span class="sxs-lookup"><span data-stu-id="eeb97-206">Because of the way docs.microsoft.com styles tables, they won’t have borders or custom styles, even if you try inline CSS.</span></span> <span data-ttu-id="eeb97-207">這項作業會在一小段時間內正常運作，但最終平臺會從資料表中去除樣式。</span><span class="sxs-lookup"><span data-stu-id="eeb97-207">It will appear to work for a short period of time, but eventually the platform will strip the styling out of the table.</span></span> <span data-ttu-id="eeb97-208">所以事先規劃，讓您的資料表保持簡單明瞭。</span><span class="sxs-lookup"><span data-stu-id="eeb97-208">So plan ahead and keep your tables simple.</span></span> <span data-ttu-id="eeb97-209">[以下是讓 Markdown 資料表更簡單的網站](https://www.tablesgenerator.com/markdown_tables)。</span><span class="sxs-lookup"><span data-stu-id="eeb97-209">[Here’s a site that makes Markdown tables easy](https://www.tablesgenerator.com/markdown_tables).</span></span>

<span data-ttu-id="eeb97-210">如果您使用 Visual Studio Code， [適用于 Visual Studio Code 的檔 Markdown 延伸](/teamblog/docs-extension) 模組也可讓您輕鬆地產生資料表， [ (請參閱下方) ](#using-visual-studio-code) 以編輯檔。</span><span class="sxs-lookup"><span data-stu-id="eeb97-210">The [Docs Markdown Extension for Visual Studio Code](/teamblog/docs-extension) also makes table generation easy if you're using [Visual Studio Code (see below)](#using-visual-studio-code) to edit the documentation.</span></span>

### <a name="adding-images"></a><span data-ttu-id="eeb97-211">新增影像</span><span class="sxs-lookup"><span data-stu-id="eeb97-211">Adding images</span></span>

<span data-ttu-id="eeb97-212">您必須將映射上傳至存放庫中的「混合式事實-檔/映射」資料夾，然後在文章中適當地參考它們。</span><span class="sxs-lookup"><span data-stu-id="eeb97-212">You’ll need to upload your images to the "mixed-reality-docs/images" folder in the repo, and then reference them appropriately in the article.</span></span> <span data-ttu-id="eeb97-213">影像會自動以完整大小顯示，這表示大型影像將會填滿整篇文章的寬度。</span><span class="sxs-lookup"><span data-stu-id="eeb97-213">Images will automatically show up at full-size, which means large images will fill the entire width of the article.</span></span> <span data-ttu-id="eeb97-214">建議您先預先調整映射大小，然後再上傳。</span><span class="sxs-lookup"><span data-stu-id="eeb97-214">We recommend pre-sizing your images before uploading them.</span></span> <span data-ttu-id="eeb97-215">建議的寬度介於600到700圖元之間，不過如果是更大的螢幕擷取畫面或螢幕擷取畫面的一部分，您應該相應增加或減少。</span><span class="sxs-lookup"><span data-stu-id="eeb97-215">The recommended width is between 600 and 700 pixels, though you should size up or down if it’s a dense screenshot or a fraction of a screenshot, respectively.</span></span>

>[!IMPORTANT]
><span data-ttu-id="eeb97-216">在合併之前，您只能將影像上傳至您的分支存放庫。</span><span class="sxs-lookup"><span data-stu-id="eeb97-216">You can only upload images to your forked repo before merging.</span></span> <span data-ttu-id="eeb97-217">因此，如果您打算將影像加入至文章，則必須先 [使用 Visual Studio Code](#using-visual-studio-code) 將影像新增至分叉的 "images" 資料夾，或確定您已在網頁瀏覽器中完成下列動作：</span><span class="sxs-lookup"><span data-stu-id="eeb97-217">So, if you plan on adding images to an article, you'll need to [use Visual Studio Code](#using-visual-studio-code) to add the images to your fork's "images" folder first or make sure you've done the following in a web browser:</span></span>
>
>1. <span data-ttu-id="eeb97-218">派生 MicrosoftDocs/mixed 事實存放庫。</span><span class="sxs-lookup"><span data-stu-id="eeb97-218">Forked the MicrosoftDocs/mixed-reality repo.</span></span>
>2. <span data-ttu-id="eeb97-219">已在您的分叉中編輯文章。</span><span class="sxs-lookup"><span data-stu-id="eeb97-219">Edited the article in your fork.</span></span>
>3. <span data-ttu-id="eeb97-220">將您在文章中參考的影像上傳至您分叉中的「混合式事實-檔/影像」資料夾。</span><span class="sxs-lookup"><span data-stu-id="eeb97-220">Uploaded the images you're referencing in your article to the "mixed-reality-docs/images" folder in your fork.</span></span>
>4. <span data-ttu-id="eeb97-221">建立 **提取要求** ，以將您的分支合併至 MicrosoftDocs/mixed 事實 ' master ' 分支。</span><span class="sxs-lookup"><span data-stu-id="eeb97-221">Created a **pull request** to merge your fork into the MicrosoftDocs/mixed-reality 'master' branch.</span></span>
>
><span data-ttu-id="eeb97-222">若要瞭解如何設定您自己的分支存放庫，請依照指示來 [建立新的文章](#creating-a-new-article)。</span><span class="sxs-lookup"><span data-stu-id="eeb97-222">To learn how to set up your own forked repo, follow the instructions for [creating a new article](#creating-a-new-article).</span></span>

## <a name="previewing-your-work"></a><span data-ttu-id="eeb97-223">預覽您的工作</span><span class="sxs-lookup"><span data-stu-id="eeb97-223">Previewing your work</span></span>

<span data-ttu-id="eeb97-224">透過網頁瀏覽器在 GitHub 中進行編輯時，您可以選取接近頁面頂端的 [ **預覽** ] 索引標籤，以在認可之前預覽您的工作。</span><span class="sxs-lookup"><span data-stu-id="eeb97-224">While editing in GitHub via a web browser, you can select the **Preview** tab near the top of the page to preview your work before committing.</span></span> 

>[!NOTE]
><span data-ttu-id="eeb97-225">在 review.docs.microsoft.com 上預覽您的變更只適用于 Microsoft 員工</span><span class="sxs-lookup"><span data-stu-id="eeb97-225">Previewing your changes on review.docs.microsoft.com is only available to Microsoft employees</span></span>

<span data-ttu-id="eeb97-226">Microsoft 員工：一旦您的投稿合併到「主要」分支之後，您就可以在內容公開之前，先進行審核 https://review.docs.microsoft.com/windows/mixed-reality/enthusiast-guide?branch=master 。</span><span class="sxs-lookup"><span data-stu-id="eeb97-226">Microsoft employees: once your contributions have been merged into the 'master' branch, you can review the content before it goes public at https://review.docs.microsoft.com/windows/mixed-reality/enthusiast-guide?branch=master.</span></span> <span data-ttu-id="eeb97-227">使用左邊資料行中的目錄來尋找您的文章。</span><span class="sxs-lookup"><span data-stu-id="eeb97-227">Find your article using the table of contents in the left column.</span></span>

## <a name="editing-in-the-browser-vs-editing-with-a-desktop-client"></a><span data-ttu-id="eeb97-228">在瀏覽器中編輯和使用桌面用戶端編輯</span><span class="sxs-lookup"><span data-stu-id="eeb97-228">Editing in the browser vs. editing with a desktop client</span></span>

<span data-ttu-id="eeb97-229">在瀏覽器中編輯是進行快速變更的最簡單方式，不過，有幾個缺點：</span><span class="sxs-lookup"><span data-stu-id="eeb97-229">Editing in the browser is the easiest way to make quick changes, however, there are a few disadvantages:</span></span>

- <span data-ttu-id="eeb97-230">您不會收到拼寫檢查。</span><span class="sxs-lookup"><span data-stu-id="eeb97-230">You don't get spell-check.</span></span>
- <span data-ttu-id="eeb97-231">您不會在其他文章中取得任何智慧連結 (您必須手動輸入文章的檔案名) 。</span><span class="sxs-lookup"><span data-stu-id="eeb97-231">You don't get any smart-linking to other articles (you have to manually type the article's filename).</span></span>
- <span data-ttu-id="eeb97-232">上傳和參考影像可能很麻煩。</span><span class="sxs-lookup"><span data-stu-id="eeb97-232">It can be a hassle to upload and reference images.</span></span>

<span data-ttu-id="eeb97-233">如果您不想處理這些問題，請使用桌面用戶端（例如 [Visual Studio Code](https://code.visualstudio.com/) ），並在參與時提供一些 [實用的擴充](#useful-extensions) 功能。</span><span class="sxs-lookup"><span data-stu-id="eeb97-233">If you'd rather not deal with these issues, use a desktop client like [Visual Studio Code](https://code.visualstudio.com/) with a couple [helpful extensions](#useful-extensions) when contributing.</span></span>

## <a name="using-visual-studio-code"></a><span data-ttu-id="eeb97-234">使用 Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="eeb97-234">Using Visual Studio Code</span></span>

<span data-ttu-id="eeb97-235">基於 [上述](#editing-in-the-browser-vs-editing-with-a-desktop-client)原因，您可能會偏好使用桌面用戶端來編輯檔，而不是使用網頁瀏覽器。</span><span class="sxs-lookup"><span data-stu-id="eeb97-235">For the reasons listed [above](#editing-in-the-browser-vs-editing-with-a-desktop-client), you may prefer using a desktop client to edit documentation instead of a web browser.</span></span> <span data-ttu-id="eeb97-236">我們建議使用 [Visual Studio Code](https://code.visualstudio.com/)。</span><span class="sxs-lookup"><span data-stu-id="eeb97-236">We recommend using [Visual Studio Code](https://code.visualstudio.com/).</span></span>

### <a name="setup"></a><span data-ttu-id="eeb97-237">安裝程式</span><span class="sxs-lookup"><span data-stu-id="eeb97-237">Setup</span></span>

<span data-ttu-id="eeb97-238">請依照下列步驟設定 Visual Studio Code，以使用此存放庫：</span><span class="sxs-lookup"><span data-stu-id="eeb97-238">Follow these steps to configure Visual Studio Code to work with this repo:</span></span>

1. <span data-ttu-id="eeb97-239">在網頁瀏覽器中：</span><span class="sxs-lookup"><span data-stu-id="eeb97-239">In a web browser:</span></span>
    1. <span data-ttu-id="eeb97-240">[為您的電腦安裝 Git](https://git-scm.com/downloads)。</span><span class="sxs-lookup"><span data-stu-id="eeb97-240">Install [Git for your PC](https://git-scm.com/downloads).</span></span>
    2. <span data-ttu-id="eeb97-241">安裝 [Visual Studio Code](https://code.visualstudio.com/)。</span><span class="sxs-lookup"><span data-stu-id="eeb97-241">Install [Visual Studio Code](https://code.visualstudio.com/).</span></span>
    3. <span data-ttu-id="eeb97-242">如果您尚未這麼做，請先將[MicrosoftDocs/混合的分支](#creating-a-new-article)。</span><span class="sxs-lookup"><span data-stu-id="eeb97-242">[Fork MicrosoftDocs/mixed-reality](#creating-a-new-article) if you haven't already.</span></span>
    4. <span data-ttu-id="eeb97-243">在您的分支中，選取 [ **複製] 或 [下載** ] 並複製 URL。</span><span class="sxs-lookup"><span data-stu-id="eeb97-243">In your fork, select **Clone or download** and copy the URL.</span></span>
2. <span data-ttu-id="eeb97-244">在 Visual Studio Code 中建立分支的本機複製：</span><span class="sxs-lookup"><span data-stu-id="eeb97-244">Create a local clone of your fork in Visual Studio Code:</span></span>
    1. <span data-ttu-id="eeb97-245">從 [ **View** ] 功能表選取 [ **命令** 選擇區]。</span><span class="sxs-lookup"><span data-stu-id="eeb97-245">From the **View** menu, select **Command Palette**.</span></span>
    2. <span data-ttu-id="eeb97-246">輸入 "Git： Clone"。</span><span class="sxs-lookup"><span data-stu-id="eeb97-246">Type "Git: Clone."</span></span>
    3. <span data-ttu-id="eeb97-247">貼上您複製的 URL。</span><span class="sxs-lookup"><span data-stu-id="eeb97-247">Paste the URL you copied.</span></span>
    4. <span data-ttu-id="eeb97-248">選擇要在電腦上儲存複本的位置。</span><span class="sxs-lookup"><span data-stu-id="eeb97-248">Choose where to save the clone on your PC.</span></span>
    5. <span data-ttu-id="eeb97-249">在快顯視窗中選取 [ **開啟** 存放庫]。</span><span class="sxs-lookup"><span data-stu-id="eeb97-249">Select **Open repo** in the pop-up.</span></span>

### <a name="editing-documentation"></a><span data-ttu-id="eeb97-250">編輯檔</span><span class="sxs-lookup"><span data-stu-id="eeb97-250">Editing documentation</span></span>

<span data-ttu-id="eeb97-251">您可以使用下列工作流程，利用 Visual Studio Code 對檔進行變更：</span><span class="sxs-lookup"><span data-stu-id="eeb97-251">Use the following workflow to make changes to the documentation with Visual Studio Code:</span></span>

>[!NOTE]
><span data-ttu-id="eeb97-252">使用 Visual Studio Code 也適用于 [編輯](#how-to-make-a-change) 和 [建立](#creating-a-new-article) 文章的所有指導方針，以及 [編輯 Markdown 的基本概念](#markdown-basics)。</span><span class="sxs-lookup"><span data-stu-id="eeb97-252">All the guidance for [editing](#how-to-make-a-change) and [creating](#creating-a-new-article) articles, and the [basics of editing Markdown](#markdown-basics), from above applies when using Visual Studio Code as well.</span></span>

1. <span data-ttu-id="eeb97-253">請確定您複製的分支是最新的官方存放庫。</span><span class="sxs-lookup"><span data-stu-id="eeb97-253">Make sure your cloned fork is up to date with the official repo.</span></span>
   1. <span data-ttu-id="eeb97-254">在網頁瀏覽器中，建立提取要求，以將最近的變更從 MicrosoftDocs/mixed 事實 ' master ' 中的其他參與者同步至您的分支 (確定箭號指向正確的) 方式。</span><span class="sxs-lookup"><span data-stu-id="eeb97-254">In a web browser, create a pull request to sync recent changes from other contributors in MicrosoftDocs/mixed-reality 'master' to your fork (make sure the arrow is pointing the right way).</span></span>
      
      ![將 MicrosoftDocs/mixed 的變更同步至您的分叉](images/sync_repos.PNG)
   2. <span data-ttu-id="eeb97-256">在 Visual Studio Code 中，選取 [同步處理] 按鈕，將新的已更新分支同步至本機複製。</span><span class="sxs-lookup"><span data-stu-id="eeb97-256">In Visual Studio Code, select the sync button to sync your freshly updated fork to the local clone.</span></span>
      
      ![按一下 [同步處理] 按鈕影像](images/sync_clone.png)
2. <span data-ttu-id="eeb97-258">使用 Visual Studio Code 在複製的存放庫中建立或編輯文章。</span><span class="sxs-lookup"><span data-stu-id="eeb97-258">Create or edit articles in your cloned repo using Visual Studio Code.</span></span>
   1. <span data-ttu-id="eeb97-259">如有必要，請編輯一或多個發行項 (將影像新增至 [images] 資料夾) 。</span><span class="sxs-lookup"><span data-stu-id="eeb97-259">Edit one or more articles (add images to “images” folder if necessary).</span></span>
   2. <span data-ttu-id="eeb97-260">**儲存** **Explorer** 中的變更。</span><span class="sxs-lookup"><span data-stu-id="eeb97-260">**Save** changes in **Explorer**.</span></span>
      
      ![在 Explorer 中選擇 [全部儲存]](images/explorer_save.png)
   3. <span data-ttu-id="eeb97-262">當系統提示) 時，認可 **原始檔控制** 中的 **所有** 變更 (寫入認可訊息。</span><span class="sxs-lookup"><span data-stu-id="eeb97-262">**Commit all** changes in **Source Control** (write commit message when prompted).</span></span>
      
      ![在原始檔控制中選擇 [全部認可]](images/source_control_commit.png)
   4. <span data-ttu-id="eeb97-264">選取 [ **同步** 處理] 按鈕，將您的變更同步至 GitHub) 上 (您的原始來源。</span><span class="sxs-lookup"><span data-stu-id="eeb97-264">Select the **sync** button to sync your changes back to origin (your fork on GitHub).</span></span>
      
      ![按一下 [同步] 按鈕](images/sync_back.png)
3. <span data-ttu-id="eeb97-266">在網頁瀏覽器中，建立提取要求，將您分支中的新變更同步處理回 MicrosoftDocs/mixed 事實 ' master ' (確定箭號指向正確的) 方式。</span><span class="sxs-lookup"><span data-stu-id="eeb97-266">In a web browser, create a pull request to sync new changes in your fork back to MicrosoftDocs/mixed-reality 'master' (make sure the arrow is pointing the correct way).</span></span>

   ![從您的分支建立提取要求至 MicrosoftDocs/mixed-事實](images/pr_to_master.PNG)

### <a name="useful-extensions"></a><span data-ttu-id="eeb97-268">有用的延伸模組</span><span class="sxs-lookup"><span data-stu-id="eeb97-268">Useful extensions</span></span>

<span data-ttu-id="eeb97-269">編輯檔時，下列 Visual Studio Code 擴充功能很有用：</span><span class="sxs-lookup"><span data-stu-id="eeb97-269">The following Visual Studio Code extensions are useful when editing documentation:</span></span>

- <span data-ttu-id="eeb97-270">[Visual Studio Code 的檔 Markdown 延伸](https://marketplace.visualstudio.com/items?itemName=docsmsft.docs-authoring-pack) 模組：使用 **Alt + M** 來顯示檔撰寫選項的功能表，例如：</span><span class="sxs-lookup"><span data-stu-id="eeb97-270">[Docs Markdown Extension for Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=docsmsft.docs-authoring-pack) - Use **Alt+M** to bring up a menu of docs authoring options like:</span></span>
   - <span data-ttu-id="eeb97-271">搜尋及參考您已上傳的影像。</span><span class="sxs-lookup"><span data-stu-id="eeb97-271">Search and reference images you've uploaded.</span></span>
   - <span data-ttu-id="eeb97-272">新增像這樣的格式：清單、資料表和檔特定的呼叫 `>[!NOTE]` 。</span><span class="sxs-lookup"><span data-stu-id="eeb97-272">Add formatting like lists, tables, and docs-specific call-outs like `>[!NOTE]`.</span></span>
   - <span data-ttu-id="eeb97-273">搜尋和參考內部連結和書簽 (頁面) 中特定區段的連結。</span><span class="sxs-lookup"><span data-stu-id="eeb97-273">Search and reference internal links and bookmarks (links to specific sections within a page).</span></span>
   - <span data-ttu-id="eeb97-274">格式化錯誤會反白顯示 (將滑鼠停留在錯誤上方，以深入瞭解) 。</span><span class="sxs-lookup"><span data-stu-id="eeb97-274">Formatting errors are highlighted (hover your mouse over the error to learn more).</span></span>
- <span data-ttu-id="eeb97-275">程式[代碼拼寫檢查](https://marketplace.visualstudio.com/items?itemName=streetsidesoftware.code-spell-checker)-拼錯的單字會加上底線;以滑鼠右鍵按一下拼錯的字組來變更它，或將它儲存至字典。</span><span class="sxs-lookup"><span data-stu-id="eeb97-275">[Code Spell Checker](https://marketplace.visualstudio.com/items?itemName=streetsidesoftware.code-spell-checker) - misspelled words will be underlined; right-click on a misspelled word to change it or save it to the dictionary.</span></span>

## <a name="using-issues-to-provide-feedback-on-windows-mixed-reality-enthusiast-guide"></a><span data-ttu-id="eeb97-276">使用問題提供 Windows Mixed Reality 愛好者指南的意見反應</span><span class="sxs-lookup"><span data-stu-id="eeb97-276">Using issues to provide feedback on Windows Mixed Reality Enthusiast Guide</span></span>

<span data-ttu-id="eeb97-277">若要提供意見反應或指出問題，而不是直接修改實際的檔頁面，請 [建立問題](https://github.com/MicrosoftDocs/mixedreality-enthusiast-guide/issues) ，內容擁有者將會以及時的方式解決問題。</span><span class="sxs-lookup"><span data-stu-id="eeb97-277">To provide feedback, or point out a problem, rather than directly modifying actual documentation pages, [create an issue](https://github.com/MicrosoftDocs/mixedreality-enthusiast-guide/issues) and the content owners will do their best to address the issue in a timely fashion.</span></span>

<span data-ttu-id="eeb97-278">如果您要建立有關特定頁面的問題，請務必包含主題標題和 URL。</span><span class="sxs-lookup"><span data-stu-id="eeb97-278">Be sure to include the topic title and the URL if you are creating an issue regarding a specific page.</span></span>

<span data-ttu-id="eeb97-279">感謝您支援這種內容！</span><span class="sxs-lookup"><span data-stu-id="eeb97-279">Thank you for supporting this content!</span></span>