---
title: DocumentationGuide
description: MRTK 的檔指導方針和標準。
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: cba239ade685c2f32bca72a11a5ac1afdebb1993
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/03/2021
ms.locfileid: "101780403"
---
# <a name="documentation-guidelines"></a><span data-ttu-id="0e969-104">檔指導方針</span><span class="sxs-lookup"><span data-stu-id="0e969-104">Documentation guidelines</span></span>

<img src="../features/images/MRTK_Logo_Rev.png" alt="MRTK Logo">

<span data-ttu-id="0e969-105">本檔概述混合現實工具組 (MRTK) 的檔指導方針和標準。</span><span class="sxs-lookup"><span data-stu-id="0e969-105">This document outlines the documentation guidelines and standards for the Mixed Reality Toolkit (MRTK).</span></span> <span data-ttu-id="0e969-106">這提供撰寫和產生檔的技術層面簡介、強調常見的陷阱，以及描述建議的書寫樣式。</span><span class="sxs-lookup"><span data-stu-id="0e969-106">This provides an introduction to technical aspects of documentation writing and generation, to highlight common pitfalls, and to describe the recommended writing style.</span></span>

<span data-ttu-id="0e969-107">頁面本身應該作為範例，因此它會使用預期的樣式以及檔的最常見標記功能。</span><span class="sxs-lookup"><span data-stu-id="0e969-107">The page itself is supposed to serve as an example, therefore it uses the intended style and the most common markup features of the documentation.</span></span>

- [<span data-ttu-id="0e969-108">來源</span><span class="sxs-lookup"><span data-stu-id="0e969-108">Source</span></span>](#source-documentation)
- [<span data-ttu-id="0e969-109">How to</span><span class="sxs-lookup"><span data-stu-id="0e969-109">How-to</span></span>](#how-to-documentation)
- [<span data-ttu-id="0e969-110">設計</span><span class="sxs-lookup"><span data-stu-id="0e969-110">Design</span></span>](#design-documentation)
- [<span data-ttu-id="0e969-111">效能注意事項</span><span class="sxs-lookup"><span data-stu-id="0e969-111">Performance notes</span></span>](#performance-notes)
- [<span data-ttu-id="0e969-112">重大變更</span><span class="sxs-lookup"><span data-stu-id="0e969-112">Breaking changes</span></span>](#breaking-changes)

---

## <a name="functionality-and-markup"></a><span data-ttu-id="0e969-113">功能和標記</span><span class="sxs-lookup"><span data-stu-id="0e969-113">Functionality and markup</span></span>

<span data-ttu-id="0e969-114">本節將描述經常需要的功能。</span><span class="sxs-lookup"><span data-stu-id="0e969-114">This section describes frequently needed features.</span></span> <span data-ttu-id="0e969-115">若要查看其運作方式，請查看頁面的原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="0e969-115">To see how they work, look at the source code of the page.</span></span>

1. <span data-ttu-id="0e969-116">編號清單</span><span class="sxs-lookup"><span data-stu-id="0e969-116">Numbered lists</span></span>
   1. <span data-ttu-id="0e969-117">具有至少3個前置空格的嵌套編號清單</span><span class="sxs-lookup"><span data-stu-id="0e969-117">Nested numbered lists with at least 3 leading blank spaces</span></span>
   1. <span data-ttu-id="0e969-118">程式碼中的實際數位不相關;剖析將會負責設定正確的專案編號。</span><span class="sxs-lookup"><span data-stu-id="0e969-118">The actual number in code is irrelevant; parsing will take care of setting the correct item number.</span></span>

- <span data-ttu-id="0e969-119">專案符號點清單</span><span class="sxs-lookup"><span data-stu-id="0e969-119">Bullet point lists</span></span>
  - <span data-ttu-id="0e969-120">嵌套的專案符號點清單</span><span class="sxs-lookup"><span data-stu-id="0e969-120">Nested bullet point lists</span></span>
- <span data-ttu-id="0e969-121">以 **粗體顯示** 的文字（含 \* \* 雙星號）\*\*</span><span class="sxs-lookup"><span data-stu-id="0e969-121">Text in **bold** with \*\*double asterisk\*\*</span></span>
- <span data-ttu-id="0e969-122"> 具有 \_ 底線 \_ 或 \* 單一星號的斜體文字\*</span><span class="sxs-lookup"><span data-stu-id="0e969-122">_italic_ *text* with \_underscore\_ or \*single asterisk\*</span></span>
- <span data-ttu-id="0e969-123">`highlighted as code`使用 backquotes 的句子中的文字 \`\`</span><span class="sxs-lookup"><span data-stu-id="0e969-123">Text `highlighted as code` within a sentence \`using backquotes\`</span></span>
- <span data-ttu-id="0e969-124">檔頁面連結 [MRTK 檔指導方針](DocumentationGuide.md)</span><span class="sxs-lookup"><span data-stu-id="0e969-124">Links to docs pages [MRTK documentation guidelines](DocumentationGuide.md)</span></span>
- <span data-ttu-id="0e969-125">[頁面內錨點](#style)的連結;錨點的形成方式是以連字號取代空格，然後轉換成小寫</span><span class="sxs-lookup"><span data-stu-id="0e969-125">Links to [anchors within a page](#style); anchors are formed by replacing spaces with dashes, and converting to lowercase</span></span>

<span data-ttu-id="0e969-126">在程式碼範例中，我們會使用具有三個倒引號的區塊 \` \` \` ，並將 *csharp* 指定為語法醒目提示的語言：</span><span class="sxs-lookup"><span data-stu-id="0e969-126">For code samples we use the blocks with three backticks \`\`\` and specify *csharp* as the language for syntax highlighting:</span></span>

```c#
int SampleFunction(int i)
{
   return i + 42;
}
```

<span data-ttu-id="0e969-127">在句子內提及程式碼時 `use a single backtick` 。</span><span class="sxs-lookup"><span data-stu-id="0e969-127">When mentioning code within a sentence `use a single backtick`.</span></span>

### <a name="todos"></a><span data-ttu-id="0e969-128">待辦事項</span><span class="sxs-lookup"><span data-stu-id="0e969-128">TODOs</span></span>

<span data-ttu-id="0e969-129">避免在檔中使用待辦事項，因為在經過一段時間後，這些待辦事項 (（例如程式碼) 待辦事項）通常會累積，以及應如何更新它們以及遺失原因的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="0e969-129">Avoid using TODOs in docs, as over time these TODOs (like code TODOs) tend to accumulate and information about how they should be updated and why gets lost.</span></span>

<span data-ttu-id="0e969-130">如果絕對需要新增 TODO，請遵循下列步驟：</span><span class="sxs-lookup"><span data-stu-id="0e969-130">If it is absolutely necessary to add a TODO, follow these steps:</span></span>

1. <span data-ttu-id="0e969-131">在 Github 上提出新的問題，描述 TODO 背後的內容，並提供足夠的背景，讓其他參與者能夠瞭解並解決 TODO 問題。</span><span class="sxs-lookup"><span data-stu-id="0e969-131">File a new issue on Github describing the context behind the TODO, and provide enough background that another contributor would be able to understand and then address the TODO.</span></span>
2. <span data-ttu-id="0e969-132">參考檔中 todo 的問題 URL。</span><span class="sxs-lookup"><span data-stu-id="0e969-132">Reference the issue URL in the todo in the docs.</span></span>

\<\!-- TODO [https://github.com/microsoft/MixedRealityToolkit-Unity/issues/ISSUE_NUMBER_HERE](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/ISSUE_NUMBER_HERE): A brief blurb on the issue --\>

### <a name="highlighted-sections"></a><span data-ttu-id="0e969-133">反白顯示的區段</span><span class="sxs-lookup"><span data-stu-id="0e969-133">Highlighted sections</span></span>

<span data-ttu-id="0e969-134">若要反白顯示讀取器的特定點，請使用 *> [!NOTE]* 、 *> [!WARNING]* 和 *> [!IMPORTANT]* 來產生下列樣式。</span><span class="sxs-lookup"><span data-stu-id="0e969-134">To highlight specific points to the reader, use *> [!NOTE]* , *> [!WARNING]* , and *> [!IMPORTANT]* to produce the following styles.</span></span> <span data-ttu-id="0e969-135">建議您僅針對特殊的相關案例，使用一般點的附注和警告/重要點。</span><span class="sxs-lookup"><span data-stu-id="0e969-135">It is recommended to use notes for general points and warning/important points only for special relevant cases.</span></span>

> [!NOTE]
> <span data-ttu-id="0e969-136">附注範例</span><span class="sxs-lookup"><span data-stu-id="0e969-136">Example of a note</span></span>

> [!WARNING]
> <span data-ttu-id="0e969-137">警告範例</span><span class="sxs-lookup"><span data-stu-id="0e969-137">Example of a warning</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0e969-138">重要批註的範例</span><span class="sxs-lookup"><span data-stu-id="0e969-138">Example of an important comment</span></span>

## <a name="page-layout"></a><span data-ttu-id="0e969-139">頁面配置</span><span class="sxs-lookup"><span data-stu-id="0e969-139">Page layout</span></span>

### <a name="introduction"></a><span data-ttu-id="0e969-140">簡介</span><span class="sxs-lookup"><span data-stu-id="0e969-140">Introduction</span></span>

<span data-ttu-id="0e969-141">主要章節標題後面的部分應該會是本章所述的簡短簡介。</span><span class="sxs-lookup"><span data-stu-id="0e969-141">The part right after the main chapter title should serve as a short introduction what the chapter is about.</span></span> <span data-ttu-id="0e969-142">請勿將此值設得太長，而是新增子頭條新聞。</span><span class="sxs-lookup"><span data-stu-id="0e969-142">Do not make this too long, instead add sub headlines.</span></span> <span data-ttu-id="0e969-143">這些可讓您連結至區段，並可儲存為書簽。</span><span class="sxs-lookup"><span data-stu-id="0e969-143">These allow to link to sections and can be saved as bookmarks.</span></span>

### <a name="main-body"></a><span data-ttu-id="0e969-144">主體</span><span class="sxs-lookup"><span data-stu-id="0e969-144">Main body</span></span>

<span data-ttu-id="0e969-145">使用雙層級和三層級的頭條來結構其餘部分。</span><span class="sxs-lookup"><span data-stu-id="0e969-145">Use two-level and three-level headlines to structure the rest.</span></span>

<span data-ttu-id="0e969-146">**迷你區段**</span><span class="sxs-lookup"><span data-stu-id="0e969-146">**Mini Sections**</span></span>

<span data-ttu-id="0e969-147">使用粗體的文字來表示應該要注意的區塊。我們可能會在某個時間點以四個層級的頭條新聞來取代此項。</span><span class="sxs-lookup"><span data-stu-id="0e969-147">Use a bold line of text for blocks that should stand out. We might replace this by four-level headlines at some point.</span></span>

### <a name="see-also-section"></a><span data-ttu-id="0e969-148">「另請參閱」一節</span><span class="sxs-lookup"><span data-stu-id="0e969-148">'See also' section</span></span>

<span data-ttu-id="0e969-149">大部分的頁面最後應該會有一個稱為 [ *另請參閱*] 的章節。</span><span class="sxs-lookup"><span data-stu-id="0e969-149">Most pages should end with a chapter called *See also*.</span></span> <span data-ttu-id="0e969-150">這一章只是一個專案符號，指向與此主題相關的頁面連結清單。</span><span class="sxs-lookup"><span data-stu-id="0e969-150">This chapter is simply a bullet pointed list of links to pages related to this topic.</span></span> <span data-ttu-id="0e969-151">這些連結可能也會出現在適當的頁面文字內，但不是必要的。</span><span class="sxs-lookup"><span data-stu-id="0e969-151">These links may also appear within the page text where appropriate, but this is not required.</span></span> <span data-ttu-id="0e969-152">同樣地，頁面文字可能包含與主要主題沒有關聯之頁面的連結，這些連結也不應該包含在 [ *請參閱* ] 清單中。</span><span class="sxs-lookup"><span data-stu-id="0e969-152">Similarly, the page text may contain links to pages that are not related to the main topic, these should not be included in the *See also* list.</span></span> <span data-ttu-id="0e969-153">請參閱 [此頁面的「另請參閱」一章](#see-also) ，以選擇連結的範例。</span><span class="sxs-lookup"><span data-stu-id="0e969-153">See [this page's ''See also'' chapter](#see-also) as an example for the choice of links.</span></span>

## <a name="table-of-contents-toc"></a><span data-ttu-id="0e969-154">目錄 (TOC) </span><span class="sxs-lookup"><span data-stu-id="0e969-154">Table of Contents (TOC)</span></span>

<span data-ttu-id="0e969-155">在 MRTK github.io 檔中，會使用 Toc 檔案來產生巡覽列。</span><span class="sxs-lookup"><span data-stu-id="0e969-155">Toc files are used for generating the navigation bars in the MRTK github.io documentation.</span></span>
<span data-ttu-id="0e969-156">每當新增檔檔案時，請確定檔資料夾的其中一個 yml 檔案中有該檔案的專案。</span><span class="sxs-lookup"><span data-stu-id="0e969-156">Whenever a new documentation file is added, make sure that there's an entry for that file in one of the toc.yml files of the documentation folder.</span></span> <span data-ttu-id="0e969-157">只有目錄檔案中列出的文章會顯示在開發人員檔的導覽中。[檔] 資料夾中的每個子資料夾都可以有一個 toc 檔案，您可以將它連結到任何現有的 toc 檔案，將它做為子區段加入至導覽的對應部分。</span><span class="sxs-lookup"><span data-stu-id="0e969-157">Only articles listed in the toc files will show up in the navigation of the developer docs. There can be a toc file for every subfolder in the documentation folder which can be linked into any existing toc file to add it as a subsection to the corresponding part of the navigation.</span></span>

## <a name="style"></a><span data-ttu-id="0e969-158">樣式</span><span class="sxs-lookup"><span data-stu-id="0e969-158">Style</span></span>

### <a name="writing-style"></a><span data-ttu-id="0e969-159">撰寫樣式</span><span class="sxs-lookup"><span data-stu-id="0e969-159">Writing style</span></span>

<span data-ttu-id="0e969-160">一般經驗法則：嘗試 **音效 professional**。</span><span class="sxs-lookup"><span data-stu-id="0e969-160">General rule of thumb: Try to **sound professional**.</span></span> <span data-ttu-id="0e969-161">這通常表示要避免「對話式語氣」。</span><span class="sxs-lookup"><span data-stu-id="0e969-161">That usually means to avoid a 'conversational tone'.</span></span> <span data-ttu-id="0e969-162">也請嘗試避免 hyperbole 和 sensationalism。</span><span class="sxs-lookup"><span data-stu-id="0e969-162">Also try to avoid hyperbole and sensationalism.</span></span>

1. <span data-ttu-id="0e969-163">請勿嘗試 (過於有趣的) 。</span><span class="sxs-lookup"><span data-stu-id="0e969-163">Don't try to be (overly) funny.</span></span>
2. <span data-ttu-id="0e969-164">絕不寫入 ' I '</span><span class="sxs-lookup"><span data-stu-id="0e969-164">Never write 'I'</span></span>
3. <span data-ttu-id="0e969-165">避免「我們」。</span><span class="sxs-lookup"><span data-stu-id="0e969-165">Avoid 'we'.</span></span> <span data-ttu-id="0e969-166">這通常可以使用 ' MRTK ' 來輕鬆改換措辭。</span><span class="sxs-lookup"><span data-stu-id="0e969-166">This can usually be rephrased easily, using 'MRTK' instead.</span></span> <span data-ttu-id="0e969-167">範例：「我們支援這項功能」-> 「MRTK 支援這項功能」或「支援下列功能 ...」。</span><span class="sxs-lookup"><span data-stu-id="0e969-167">Example: "we support this feature" -> "MRTK supports this feature" or "the following features are supported ...".</span></span>
4. <span data-ttu-id="0e969-168">同樣地，請試著避免「您」。</span><span class="sxs-lookup"><span data-stu-id="0e969-168">Similarly, try to avoid 'you'.</span></span> <span data-ttu-id="0e969-169">範例：「有了這個簡單的變更，您的著色器就變成可設定的！」</span><span class="sxs-lookup"><span data-stu-id="0e969-169">Example: "With this simple change your shader becomes configurable!"</span></span> <span data-ttu-id="0e969-170">-> 「可以輕鬆設定著色器」。</span><span class="sxs-lookup"><span data-stu-id="0e969-170">-> "Shaders can be made configurable with little effort."</span></span>
5. <span data-ttu-id="0e969-171">請勿使用 ' 草率片語 '。</span><span class="sxs-lookup"><span data-stu-id="0e969-171">Do not use 'sloppy phrases'.</span></span>
6. <span data-ttu-id="0e969-172">避免發音太興奮，我們不需要銷售任何事物。</span><span class="sxs-lookup"><span data-stu-id="0e969-172">Avoid sounding overly excited, we do not need to sell anything.</span></span>
7. <span data-ttu-id="0e969-173">同樣地，請避免過度大幅。</span><span class="sxs-lookup"><span data-stu-id="0e969-173">Similarly, avoid being overly dramatic.</span></span> <span data-ttu-id="0e969-174">驚嘆號很少需要用到。</span><span class="sxs-lookup"><span data-stu-id="0e969-174">Exclamation marks are rarely needed.</span></span>

### <a name="capitalization"></a><span data-ttu-id="0e969-175">大寫</span><span class="sxs-lookup"><span data-stu-id="0e969-175">Capitalization</span></span>

- <span data-ttu-id="0e969-176">將 **句子案例用於頭條新聞**。</span><span class="sxs-lookup"><span data-stu-id="0e969-176">Use **Sentence case for headlines**.</span></span> <span data-ttu-id="0e969-177">亦即</span><span class="sxs-lookup"><span data-stu-id="0e969-177">Ie.</span></span> <span data-ttu-id="0e969-178">將第一個字母和名稱大寫，但不需要其他任何專案。</span><span class="sxs-lookup"><span data-stu-id="0e969-178">capitalize the first letter and names, but nothing else.</span></span>
- <span data-ttu-id="0e969-179">針對其他所有專案使用一般英文。</span><span class="sxs-lookup"><span data-stu-id="0e969-179">Use regular English for everything else.</span></span> <span data-ttu-id="0e969-180">這表示 **不會將任意字組大寫**，即使它們在該內容中有特殊意義也一樣。</span><span class="sxs-lookup"><span data-stu-id="0e969-180">That means **do not capitalize arbitrary words**, even if they hold a special meaning in that context.</span></span> <span data-ttu-id="0e969-181">偏好 *斜體文字* 以醒目提示特定文字， [請參閱下文](#emphasis-and-highlighting)。</span><span class="sxs-lookup"><span data-stu-id="0e969-181">Prefer *italic text* for highlighting certain words, [see below](#emphasis-and-highlighting).</span></span>
- <span data-ttu-id="0e969-182">當連結內嵌于句子 (（) 慣用的方法）時，標準章節名稱一律會使用大寫字母，因此會中斷文字內部沒有任意大小寫的規則。</span><span class="sxs-lookup"><span data-stu-id="0e969-182">When a link is embedded in a sentence (which is the preferred method), the standard chapter name always uses capital letters, thus breaking the rule of no arbitrary capitalization inside text.</span></span> <span data-ttu-id="0e969-183">因此，請使用自訂連結名稱來修正大小寫。</span><span class="sxs-lookup"><span data-stu-id="0e969-183">Therefore use a custom link name to fix the capitalization.</span></span> <span data-ttu-id="0e969-184">例如，以下是 [界限控制項](../features/ux-building-blocks/BoundsControl.md) 檔的連結。</span><span class="sxs-lookup"><span data-stu-id="0e969-184">As an example, here is a link to the [bounds control](../features/ux-building-blocks/BoundsControl.md) documentation.</span></span>
- <span data-ttu-id="0e969-185">請將名稱大寫，例如 *Unity*。</span><span class="sxs-lookup"><span data-stu-id="0e969-185">Do capitalize names, such as *Unity*.</span></span>
- <span data-ttu-id="0e969-186">撰寫 *Unity 編輯器* 時，請勿將「編輯器」變成大寫。</span><span class="sxs-lookup"><span data-stu-id="0e969-186">Do NOT capitalize "editor" when writing *Unity editor*.</span></span>

### <a name="emphasis-and-highlighting"></a><span data-ttu-id="0e969-187">強調和反白顯示</span><span class="sxs-lookup"><span data-stu-id="0e969-187">Emphasis and highlighting</span></span>

<span data-ttu-id="0e969-188">有兩種方式可以強調或反白顯示字組，使其變成粗體或使其成為斜體。</span><span class="sxs-lookup"><span data-stu-id="0e969-188">There are two ways to emphasize or highlight words, making them bold or making them italic.</span></span> <span data-ttu-id="0e969-189">粗體文字的效果是 **粗體文字** ，因此可以在 skimming 一段文字，或甚至只是在頁面上顯示時，輕易注意到。</span><span class="sxs-lookup"><span data-stu-id="0e969-189">The effect of bold text is that **bold text sticks out** and therefore can easily be noticed while skimming a piece of text or even just scrolling over a page.</span></span> <span data-ttu-id="0e969-190">粗體很適合用來醒目提示人們應記住的片語。</span><span class="sxs-lookup"><span data-stu-id="0e969-190">Bold is great to highlight phrases that people should remember.</span></span> <span data-ttu-id="0e969-191">不過， **很少使用粗體文字**，因為通常會造成干擾。</span><span class="sxs-lookup"><span data-stu-id="0e969-191">However, **use bold text rarely**, because it is generally distracting.</span></span>

<span data-ttu-id="0e969-192">通常會有一個「群組」是以邏輯方式存在的內容，或反白顯示特定詞彙，因為它具有特殊意義。</span><span class="sxs-lookup"><span data-stu-id="0e969-192">Often one wants to either 'group' something that belongs logically together or highlight a specific term, because it has a special meaning.</span></span> <span data-ttu-id="0e969-193">這類專案不需要與整體文字相關。</span><span class="sxs-lookup"><span data-stu-id="0e969-193">Such things do not need to stand out of the overall text.</span></span> <span data-ttu-id="0e969-194">使用斜體文字作為 *輕量方法* ，以反白顯示某個東西。</span><span class="sxs-lookup"><span data-stu-id="0e969-194">Use italic text as a *lightweight method* to highlight something.</span></span>

<span data-ttu-id="0e969-195">同樣地，在文字中提及檔案名、路徑或功能表項目時，最好將它設為斜體以進行邏輯分組，而不會造成干擾。</span><span class="sxs-lookup"><span data-stu-id="0e969-195">Similarly, when a filename, a path or a menu-entry is mentioned in text, prefer to make it italic to logically group it, without being distracting.</span></span>

<span data-ttu-id="0e969-196">一般情況下，請嘗試 **避免不必要的文字** 反白顯示。</span><span class="sxs-lookup"><span data-stu-id="0e969-196">In general, try to **avoid unnecessary text highlighting**.</span></span> <span data-ttu-id="0e969-197">特殊字詞可以反白顯示，讓讀者知道，當它不再有目的，而且只是 distracts 時，請不要在整個文字中重複這類的反白顯示。</span><span class="sxs-lookup"><span data-stu-id="0e969-197">Special terms can be highlighted once to make the reader aware, do not repeat such highlighting throughout the text, when it serves no purpose anymore and only distracts.</span></span>

### <a name="mentioning-menu-entries"></a><span data-ttu-id="0e969-198">提及功能表項目</span><span class="sxs-lookup"><span data-stu-id="0e969-198">Mentioning menu entries</span></span>

<span data-ttu-id="0e969-199">提及使用者應該按一下的功能表項目時，目前的慣例是： *Project > Files > 建立 > 分葉*</span><span class="sxs-lookup"><span data-stu-id="0e969-199">When mentioning a menu entry that a user should click, the current convention is: *Project > Files > Create > Leaf*</span></span>

### <a name="links"></a><span data-ttu-id="0e969-200">連結</span><span class="sxs-lookup"><span data-stu-id="0e969-200">Links</span></span>

<span data-ttu-id="0e969-201">盡可能將許多有用的連結插入至其他頁面，但每個連結只會出現一次。</span><span class="sxs-lookup"><span data-stu-id="0e969-201">Insert as many useful links to other pages as possible, but each link only once.</span></span> <span data-ttu-id="0e969-202">假設讀者按一下頁面中的每個連結，並思考它的麻煩程度，如果同一個頁面開啟了20次。</span><span class="sxs-lookup"><span data-stu-id="0e969-202">Assume a reader clicks on every link in the page, and think about how annoying it would be, if the same page opens 20 times.</span></span>

<span data-ttu-id="0e969-203">偏好內嵌于句子中的連結：</span><span class="sxs-lookup"><span data-stu-id="0e969-203">Prefer links embedded in a sentence:</span></span>

- <span data-ttu-id="0e969-204">錯誤：指導方針很有用。</span><span class="sxs-lookup"><span data-stu-id="0e969-204">BAD: Guidelines are useful.</span></span> <span data-ttu-id="0e969-205">如需詳細資訊，請參閱 [這一章](DocumentationGuide.md) 。</span><span class="sxs-lookup"><span data-stu-id="0e969-205">See [this chapter](DocumentationGuide.md) for details.</span></span>
- <span data-ttu-id="0e969-206">好： [指導方針](DocumentationGuide.md) 很有用。</span><span class="sxs-lookup"><span data-stu-id="0e969-206">GOOD: [Guidelines](DocumentationGuide.md) are useful.</span></span>

<span data-ttu-id="0e969-207">避免外部連結，它們可能會變成過期或包含受著作權的內容。</span><span class="sxs-lookup"><span data-stu-id="0e969-207">Avoid external links, they can become outdated or contain copyrighted content.</span></span>

<span data-ttu-id="0e969-208">新增連結時，請考慮它是否也應該列在 [ [另請參閱](#see-also) ] 區段中。</span><span class="sxs-lookup"><span data-stu-id="0e969-208">When adding a link, consider whether it should also be listed in the [See also](#see-also) section.</span></span> <span data-ttu-id="0e969-209">同樣地，檢查是否應將新頁面的連結加入至連結的頁面。</span><span class="sxs-lookup"><span data-stu-id="0e969-209">Similarly, check whether a link to the new page should be added to the linked-to page.</span></span>

### <a name="images--screenshots"></a><span data-ttu-id="0e969-210">影像/螢幕擷取畫面</span><span class="sxs-lookup"><span data-stu-id="0e969-210">Images / screenshots</span></span>

<span data-ttu-id="0e969-211">**請謹慎使用螢幕擷取畫面。**</span><span class="sxs-lookup"><span data-stu-id="0e969-211">**Use screenshots sparingly.**</span></span> <span data-ttu-id="0e969-212">在檔中維護映射是很多工作，小型 UI 的變更可能會導致許多螢幕擷取畫面過期。</span><span class="sxs-lookup"><span data-stu-id="0e969-212">Maintaining images in documentation is a lot of work, small UI changes can make a lot of screenshots outdated.</span></span> <span data-ttu-id="0e969-213">下列規則將減少維護工作：</span><span class="sxs-lookup"><span data-stu-id="0e969-213">The following rules will reduce maintenance effort:</span></span>

1. <span data-ttu-id="0e969-214">請勿針對可在文字中描述的專案使用螢幕擷取畫面。</span><span class="sxs-lookup"><span data-stu-id="0e969-214">Do not use screenshots for things that can be described in text.</span></span> <span data-ttu-id="0e969-215">尤其是， **絕對不會顯示內容方格的螢幕擷取畫面** ，以顯示內容名稱和值的唯一用途。</span><span class="sxs-lookup"><span data-stu-id="0e969-215">Especially, **never screenshot a property grid** for the sole purpose of showing property names and values.</span></span>
2. <span data-ttu-id="0e969-216">請勿在與顯示內容無關的螢幕擷取畫面中包含專案。</span><span class="sxs-lookup"><span data-stu-id="0e969-216">Do not include things in a screenshot that are irrelevant to what is shown.</span></span> <span data-ttu-id="0e969-217">例如，顯示轉譯效果時，請建立該區的螢幕擷取畫面，但在其周圍排除任何 UI。</span><span class="sxs-lookup"><span data-stu-id="0e969-217">For instance, when a rendering effect is shown, make a screenshot of the viewport, but exclude any UI around it.</span></span> <span data-ttu-id="0e969-218">在顯示某些 UI 的情況下，請試著四處移動視窗，如此一來，只有該重要部分才會在影像中。</span><span class="sxs-lookup"><span data-stu-id="0e969-218">Showing some UI, try to move windows around such that only that important part is in the image.</span></span>
3. <span data-ttu-id="0e969-219">包含螢幕擷取畫面 UI 時，只會顯示重要的部分。</span><span class="sxs-lookup"><span data-stu-id="0e969-219">When including screenshot UI, only show the important parts.</span></span> <span data-ttu-id="0e969-220">例如，在討論工具列中的按鈕時，請建立一個小影像來顯示重要的工具列按鈕，但是排除它周圍的所有專案。</span><span class="sxs-lookup"><span data-stu-id="0e969-220">For example, when talking about buttons in a toolbar, make a small image that shows the important toolbar buttons, but exclude everything around it.</span></span>
4. <span data-ttu-id="0e969-221">只使用容易重現的映射。</span><span class="sxs-lookup"><span data-stu-id="0e969-221">Only use images that are easy to reproduce.</span></span> <span data-ttu-id="0e969-222">這表示不會在螢幕擷取畫面中繪製標記或反白顯示。</span><span class="sxs-lookup"><span data-stu-id="0e969-222">That means do not paint markers or highlights into screenshots.</span></span> <span data-ttu-id="0e969-223">首先，這些都不會有一致的規則。</span><span class="sxs-lookup"><span data-stu-id="0e969-223">First, there are no consistent rules how these should look, anyway.</span></span> <span data-ttu-id="0e969-224">其次，重新產生這類螢幕擷取畫面是額外的工作。</span><span class="sxs-lookup"><span data-stu-id="0e969-224">Second, reproducing such a screenshot is additional effort.</span></span> <span data-ttu-id="0e969-225">相反地，請描述文字中的重要部分。</span><span class="sxs-lookup"><span data-stu-id="0e969-225">Instead, describe the important parts in text.</span></span> <span data-ttu-id="0e969-226">這項規則有一些例外狀況，但很罕見。</span><span class="sxs-lookup"><span data-stu-id="0e969-226">There are exceptions to this rule, but they are rare.</span></span>
5. <span data-ttu-id="0e969-227">很明顯地，重新建立動畫 GIF 的工作更多。</span><span class="sxs-lookup"><span data-stu-id="0e969-227">Obviously, it is much more effort to recreate an animated GIF.</span></span> <span data-ttu-id="0e969-228">如果不想花時間，就必須負責重新建立，直到時間結束為止，或希望人們擲出它。</span><span class="sxs-lookup"><span data-stu-id="0e969-228">Expect to be responsible to recreate it until the end of time, or expect people to throw it out, if they don't want to spend that time.</span></span>
6. <span data-ttu-id="0e969-229">讓文章中的影像數目減少。</span><span class="sxs-lookup"><span data-stu-id="0e969-229">Keep the number of images in an article low.</span></span> <span data-ttu-id="0e969-230">通常，最好的方法是為某些工具提供一個整體的螢幕擷取畫面，以顯示所有專案，然後在文字中描述其餘部分。</span><span class="sxs-lookup"><span data-stu-id="0e969-230">Often a good method is to make one overall screenshot of some tool, that shows everything, and then describe the rest in text.</span></span> <span data-ttu-id="0e969-231">這可讓您視需要輕鬆地取代螢幕擷取畫面。</span><span class="sxs-lookup"><span data-stu-id="0e969-231">This makes it easy to replace the screenshot when necessary.</span></span>

<span data-ttu-id="0e969-232">其他方面：</span><span class="sxs-lookup"><span data-stu-id="0e969-232">Some other aspects:</span></span>

- <span data-ttu-id="0e969-233">螢幕擷取畫面的編輯器 UI 應該使用淺灰色主題編輯器，因為並非所有使用者都有深色主題的存取權，而且我們想要盡可能保持一致的專案。</span><span class="sxs-lookup"><span data-stu-id="0e969-233">The editor UI for screenshots should use light gray theme editor as not all users have access to the dark theme and we'd like to keep things as consistent as possible.</span></span>
- <span data-ttu-id="0e969-234">預設影像寬度為500圖元，因為這會在大部分監視器上顯示得很好。</span><span class="sxs-lookup"><span data-stu-id="0e969-234">Default image width is 500 pixels, as this displays well on most monitors.</span></span> <span data-ttu-id="0e969-235">不要再從它偏離太多。</span><span class="sxs-lookup"><span data-stu-id="0e969-235">Try not to deviate too much from it.</span></span> <span data-ttu-id="0e969-236">800圖元的寬度應為最大值。</span><span class="sxs-lookup"><span data-stu-id="0e969-236">800 pixels width should be the maximum.</span></span>
- <span data-ttu-id="0e969-237">使用 Png 來取得 UI 的螢幕擷取畫面。</span><span class="sxs-lookup"><span data-stu-id="0e969-237">Use PNGs for screenshots of UI.</span></span>
- <span data-ttu-id="0e969-238">將 Png 或 Jpg 用於3D 視窗圖的螢幕擷取畫面。</span><span class="sxs-lookup"><span data-stu-id="0e969-238">Use PNGs or JPGs for 3D viewport screenshots.</span></span> <span data-ttu-id="0e969-239">偏好超過壓縮比例的品質。</span><span class="sxs-lookup"><span data-stu-id="0e969-239">Prefer quality over compression ratio.</span></span>

### <a name="list-of-component-properties"></a><span data-ttu-id="0e969-240">元件屬性清單</span><span class="sxs-lookup"><span data-stu-id="0e969-240">List of component properties</span></span>

<span data-ttu-id="0e969-241">記錄屬性清單時，請使用粗體文字來反白顯示內容名稱、分行符號號和一般文字來描述它們。</span><span class="sxs-lookup"><span data-stu-id="0e969-241">When documenting a list of properties, use bold text to highlight the property name, then line breaks and regular text to describe them.</span></span> <span data-ttu-id="0e969-242">請勿使用子章節或專案符號點清單。</span><span class="sxs-lookup"><span data-stu-id="0e969-242">Do not use sub-chapters or bullet point lists.</span></span>

<span data-ttu-id="0e969-243">此外，別忘了以句號完成所有句子。</span><span class="sxs-lookup"><span data-stu-id="0e969-243">Also, don't forget to finish all sentences with a period.</span></span>

## <a name="page-completion-checklist"></a><span data-ttu-id="0e969-244">頁面完成檢查清單</span><span class="sxs-lookup"><span data-stu-id="0e969-244">Page completion checklist</span></span>

1. <span data-ttu-id="0e969-245">確定已遵循本檔的指導方針。</span><span class="sxs-lookup"><span data-stu-id="0e969-245">Ensure that this document's guidelines were followed.</span></span>
1. <span data-ttu-id="0e969-246">流覽檔結構，並查看是否可在其他頁面的 [另 [請參閱](#see-also) ] 區段下提及新檔。</span><span class="sxs-lookup"><span data-stu-id="0e969-246">Browse the document structure and see if the new document could be mentioned under the [See also](#see-also) section of other pages.</span></span>
1. <span data-ttu-id="0e969-247">如果有的話，請讓有人瞭解如何證明頁面的技術正確性。</span><span class="sxs-lookup"><span data-stu-id="0e969-247">If available, have someone with knowledge of the topic proof-read the page for technical correctness.</span></span>
1. <span data-ttu-id="0e969-248">讓他人證明頁面的樣式和格式。</span><span class="sxs-lookup"><span data-stu-id="0e969-248">Have someone proof-read the page for style and formatting.</span></span> <span data-ttu-id="0e969-249">這可能是主題中不熟悉的使用者，這也是取得檔瞭解如何理解的建議。</span><span class="sxs-lookup"><span data-stu-id="0e969-249">This can be someone unfamiliar with the topic, which is also a good idea to get feedback about how understandable the documentation is.</span></span>

## <a name="source-documentation"></a><span data-ttu-id="0e969-250">來原始檔案</span><span class="sxs-lookup"><span data-stu-id="0e969-250">Source documentation</span></span>

<span data-ttu-id="0e969-251">API 檔將會自動從 MRTK 原始檔產生。</span><span class="sxs-lookup"><span data-stu-id="0e969-251">API documentation will be generated automatically from the MRTK source files.</span></span> <span data-ttu-id="0e969-252">為了方便進行，來源檔案必須包含下列各項：</span><span class="sxs-lookup"><span data-stu-id="0e969-252">To facilitate this, source files are required to contain the following:</span></span>

- [<span data-ttu-id="0e969-253">類別、結構、列舉摘要區塊</span><span class="sxs-lookup"><span data-stu-id="0e969-253">Class, struct, enum summary blocks</span></span>](#class-struct-enum-summary-blocks)
- [<span data-ttu-id="0e969-254">屬性、方法、事件摘要區塊</span><span class="sxs-lookup"><span data-stu-id="0e969-254">Property, method, event summary blocks</span></span>](#property-method-event-summary-blocks)
- [<span data-ttu-id="0e969-255">功能簡介版本和相依性</span><span class="sxs-lookup"><span data-stu-id="0e969-255">Feature introduction version and dependencies</span></span>](#feature-introduction-version-and-dependencies)
- [<span data-ttu-id="0e969-256">序列化欄位</span><span class="sxs-lookup"><span data-stu-id="0e969-256">Serialized fields</span></span>](#serialized-fields)
- [<span data-ttu-id="0e969-257">列舉值</span><span class="sxs-lookup"><span data-stu-id="0e969-257">Enumeration values</span></span>](#enumeration-values)

<span data-ttu-id="0e969-258">除了上述的程式碼，程式碼應該有適當的批註，以便進行維護、bug 修正和自訂的簡化。</span><span class="sxs-lookup"><span data-stu-id="0e969-258">In addition to the above, the code should be well commented to allow for maintenance, bug fixes and ease of customization.</span></span>

### <a name="class-struct-enum-summary-blocks"></a><span data-ttu-id="0e969-259">類別、結構、列舉摘要區塊</span><span class="sxs-lookup"><span data-stu-id="0e969-259">Class, struct, enum summary blocks</span></span>

<span data-ttu-id="0e969-260">如果將類別、結構或列舉新增至 MRTK，就必須描述其用途。</span><span class="sxs-lookup"><span data-stu-id="0e969-260">If a class, struct or enum is being added to the MRTK, its purpose must be described.</span></span> <span data-ttu-id="0e969-261">這是採用類別之上的摘要區塊形式。</span><span class="sxs-lookup"><span data-stu-id="0e969-261">This is to take the form of a summary block above the class.</span></span>

```c#
/// <summary>
/// AudioOccluder implements IAudioInfluencer to provide an occlusion effect.
/// </summary>
```

<span data-ttu-id="0e969-262">如果有任何類別層級相依性，這些相依性應該記錄在備註區塊中，緊接在摘要下方。</span><span class="sxs-lookup"><span data-stu-id="0e969-262">If there are any class level dependencies, they should be documented in a remarks block, immediately below the summary.</span></span>

```c#
/// <remarks>
/// Ensure that all sound emitting objects have an attached AudioInfluencerController.
/// Failing to do so will result in the desired effect not being applied to the sound.
/// </remarks>
```

<span data-ttu-id="0e969-263">如果沒有類別、結構或列舉的摘要，提交的提取要求將不會獲得核准。</span><span class="sxs-lookup"><span data-stu-id="0e969-263">Pull Requests submitted without summaries for classes, structures or enums will not be approved.</span></span>

### <a name="property-method-event-summary-blocks"></a><span data-ttu-id="0e969-264">屬性、方法、事件摘要區塊</span><span class="sxs-lookup"><span data-stu-id="0e969-264">Property, method, event summary blocks</span></span>

<span data-ttu-id="0e969-265">屬性、方法和事件 (PMEs) 以及欄位都要記錄在摘要區塊中，不論程式碼可見度 (公用、私用、受保護和內部) 。</span><span class="sxs-lookup"><span data-stu-id="0e969-265">Properties, methods and events (PMEs) as well as fields are to be documented with summary blocks, regardless of code visibility (public, private, protected and internal).</span></span> <span data-ttu-id="0e969-266">檔產生工具會負責篩選出和只發行公用和受保護的功能。</span><span class="sxs-lookup"><span data-stu-id="0e969-266">The documentation generation tool is responsible for filtering out and publishing only the public and protected features.</span></span>

<span data-ttu-id="0e969-267">注意： Unity 方法 **不** 需要摘要區塊 (例如：喚醒、啟動、更新) 。</span><span class="sxs-lookup"><span data-stu-id="0e969-267">NOTE: A summary block is **not** required for Unity methods (ex: Awake, Start, Update).</span></span>

<span data-ttu-id="0e969-268">**需要** 有 PME 檔才能核准提取要求。</span><span class="sxs-lookup"><span data-stu-id="0e969-268">PME documentation is **required** for a pull request to be approved.</span></span>

<span data-ttu-id="0e969-269">作為 PME 摘要區塊的一部分，需要參數和傳回資料的意義和用途。</span><span class="sxs-lookup"><span data-stu-id="0e969-269">As part of a PME summary block, the meaning and purpose of parameters and returned data is required.</span></span>

```c#
/// <summary>
/// Sets the cached native cutoff frequency of the attached low pass filter.
/// </summary>
/// <param name="frequency">The new low pass filter cutoff frequency.</param>
/// <returns>The new cutoff frequency value.</returns>
```

### <a name="feature-introduction-version-and-dependencies"></a><span data-ttu-id="0e969-270">功能簡介版本和相依性</span><span class="sxs-lookup"><span data-stu-id="0e969-270">Feature introduction version and dependencies</span></span>

<span data-ttu-id="0e969-271">作為 API 摘要檔的一部分，這是引入功能的 MRTK 版本相關資訊，而任何相依性都應記載于備註區塊中。</span><span class="sxs-lookup"><span data-stu-id="0e969-271">As part of the API summary documentation, information regarding the MRTK version in which the feature was introduced and any dependencies should be documented in a remarks block.</span></span>

<span data-ttu-id="0e969-272">相依性應該包含擴充功能和/或平臺相依性。</span><span class="sxs-lookup"><span data-stu-id="0e969-272">Dependencies should include extension and/or platform dependencies.</span></span>

```c#
/// <remarks>
/// Introduced in MRTK version: 2018.06.0
/// Minimum Unity version: 2018.0.0f1
/// Minimum Operating System: Windows 10.0.11111.0
/// Requires installation of: ImaginarySDK v2.1
/// </remarks>
```

### <a name="serialized-fields"></a><span data-ttu-id="0e969-273">序列化欄位</span><span class="sxs-lookup"><span data-stu-id="0e969-273">Serialized fields</span></span>

<span data-ttu-id="0e969-274">使用 Unity 的 tooltip 屬性來提供偵測器中腳本欄位的執行時間檔是很好的作法。</span><span class="sxs-lookup"><span data-stu-id="0e969-274">It is a good practice to use Unity's tooltip attribute to provide runtime documentation for a script's fields in the inspector.</span></span>

<span data-ttu-id="0e969-275">為了讓設定選項包含在 API 檔中，腳本必須 *至少* 包含摘要區塊中的工具提示內容。</span><span class="sxs-lookup"><span data-stu-id="0e969-275">So that configuration options are included in the API documentation, scripts are required to include *at least* the tooltip contents in a summary block.</span></span>

```c#
/// <summary>
/// The quality level of the simulated audio source (ex: AM radio).
/// </summary>
[Tooltip("The quality level of the simulated audio source.")]
```

### <a name="enumeration-values"></a><span data-ttu-id="0e969-276">列舉值</span><span class="sxs-lookup"><span data-stu-id="0e969-276">Enumeration values</span></span>

<span data-ttu-id="0e969-277">在定義和列舉時，程式碼也必須使用摘要區塊來記錄列舉值的意義。</span><span class="sxs-lookup"><span data-stu-id="0e969-277">When defining and enumeration, code must also document the meaning of the enum values using a summary block.</span></span> <span data-ttu-id="0e969-278">您可以選擇性地使用備註區塊來提供其他詳細資料，以增強理解。</span><span class="sxs-lookup"><span data-stu-id="0e969-278">Remarks blocks can optionally be used to provide additional details to enhance understanding.</span></span>

```c#
/// <summary>
/// Full range of human hearing.
/// </summary>
/// <remarks>
/// The frequency range used is a bit wider than that of human
/// hearing. It closely resembles the range used for audio CDs.
/// </remarks>
```

## <a name="how-to-documentation"></a><span data-ttu-id="0e969-279">How to 檔</span><span class="sxs-lookup"><span data-stu-id="0e969-279">How-to documentation</span></span>

<span data-ttu-id="0e969-280">混合現實工具組的許多使用者可能不需要使用 API 檔。</span><span class="sxs-lookup"><span data-stu-id="0e969-280">Many users of the Mixed Reality Toolkit may not need to use the API documentation.</span></span> <span data-ttu-id="0e969-281">這些使用者將利用我們預先製作的可重複使用 prefabs 和腳本，來建立他們的體驗。</span><span class="sxs-lookup"><span data-stu-id="0e969-281">These users will take advantage of our pre-made, reusable prefabs and scripts to create their experiences.</span></span>

<span data-ttu-id="0e969-282">每個功能區域將包含一或多個 markdown ( md) 檔案，這些檔案會以相當高的層級來描述。</span><span class="sxs-lookup"><span data-stu-id="0e969-282">Each feature area will contain one or more markdown (.md) files that describe at a fairly high level, what is provided.</span></span> <span data-ttu-id="0e969-283">視指定功能區域的大小和/或複雜度而定，可能需要額外的檔案，每個功能提供最多一個檔案。</span><span class="sxs-lookup"><span data-stu-id="0e969-283">Depending on the size and/or complexity of a given feature area, there may be a need for additional files, up to one per feature provided.</span></span>

<span data-ttu-id="0e969-284">當 (新增功能或變更使用方式時) ，就必須提供總覽檔。</span><span class="sxs-lookup"><span data-stu-id="0e969-284">When a feature is added (or the usage is changed), overview documentation must be provided.</span></span>

<span data-ttu-id="0e969-285">在本檔中，您應該提供「如何」區段（包括圖例），以協助新的客戶開始使用功能或概念。</span><span class="sxs-lookup"><span data-stu-id="0e969-285">As part of this documentation, how-to sections, including illustrations, should be provided to assist customers new to a feature or concept in getting started.</span></span>

## <a name="design-documentation"></a><span data-ttu-id="0e969-286">設計檔</span><span class="sxs-lookup"><span data-stu-id="0e969-286">Design documentation</span></span>

<span data-ttu-id="0e969-287">Mixed Reality 讓您有機會建立全新的領域。</span><span class="sxs-lookup"><span data-stu-id="0e969-287">Mixed Reality provides an opportunity to create entirely new worlds.</span></span> <span data-ttu-id="0e969-288">這可能牽涉到建立自訂資產以與 MRTK 搭配使用。</span><span class="sxs-lookup"><span data-stu-id="0e969-288">Part of this is likely to involve the creation of custom assets for use with the MRTK.</span></span> <span data-ttu-id="0e969-289">為了讓客戶能更輕鬆地釋出這種情況，元件應該提供描述任何格式或其他藝術資產需求的設計檔。</span><span class="sxs-lookup"><span data-stu-id="0e969-289">To make this as friction free as possible for customers, components should provide design documentation describing any formatting or other requirements for art assets.</span></span>

<span data-ttu-id="0e969-290">設計檔可能會有説明的一些範例：</span><span class="sxs-lookup"><span data-stu-id="0e969-290">Some examples where design documentation can be helpful:</span></span>

- <span data-ttu-id="0e969-291">資料指標模型</span><span class="sxs-lookup"><span data-stu-id="0e969-291">Cursor models</span></span>
- <span data-ttu-id="0e969-292">空間對應視覺效果</span><span class="sxs-lookup"><span data-stu-id="0e969-292">Spatial mapping visualizations</span></span>
- <span data-ttu-id="0e969-293">音效效果檔案</span><span class="sxs-lookup"><span data-stu-id="0e969-293">Sound effect files</span></span>

<span data-ttu-id="0e969-294">**強烈** 建議您採用這種類型的檔，而且 **可能** 會在提取要求審核過程中要求。</span><span class="sxs-lookup"><span data-stu-id="0e969-294">This type of documentation is **strongly** recommended, and **may** be requested as part of a pull request review.</span></span>

<span data-ttu-id="0e969-295">這不一定與[MS 開發人員網站](https://docs.microsoft.com/windows/mixed-reality/design)上的設計建議不同</span><span class="sxs-lookup"><span data-stu-id="0e969-295">This may or may not be different from the design recommendation on the [MS Developer site](https://docs.microsoft.com/windows/mixed-reality/design)</span></span>

## <a name="performance-notes"></a><span data-ttu-id="0e969-296">效能注意事項</span><span class="sxs-lookup"><span data-stu-id="0e969-296">Performance notes</span></span>

<span data-ttu-id="0e969-297">有一些重要功能會產生效能成本。</span><span class="sxs-lookup"><span data-stu-id="0e969-297">Some important features come at a performance cost.</span></span> <span data-ttu-id="0e969-298">這段程式碼通常會根據其設定方式而定。</span><span class="sxs-lookup"><span data-stu-id="0e969-298">Often this code will very depending how they are configured.</span></span>

<span data-ttu-id="0e969-299">例如：</span><span class="sxs-lookup"><span data-stu-id="0e969-299">For example:</span></span>

```md
When using the spatial mapping component, the performance impact will increase with the level of detail requested.  
It is recommended to use the least detail possible for the desired experience.
```

<span data-ttu-id="0e969-300">建議針對 CPU 和/或 GPU 繁重的元件使用效能注意事項，而且 **可能** 會在提取要求審核過程中要求。</span><span class="sxs-lookup"><span data-stu-id="0e969-300">Performance notes are recommended for CPU and/or GPU heavy components and **may** be requested as part of a pull request review.</span></span> <span data-ttu-id="0e969-301">任何適用的效能注意事項都會包含在 API **和** 總覽檔中。</span><span class="sxs-lookup"><span data-stu-id="0e969-301">Any applicable performance notes are to be included in API **and** overview documentation.</span></span>

## <a name="breaking-changes"></a><span data-ttu-id="0e969-302">重大變更</span><span class="sxs-lookup"><span data-stu-id="0e969-302">Breaking changes</span></span>

<span data-ttu-id="0e969-303">重大變更 [檔](BreakingChanges.md) 是由最上層的檔案所組成，其會連結至每個功能區域的個別 [BreakingChanges.md](BreakingChanges.md)。</span><span class="sxs-lookup"><span data-stu-id="0e969-303">Breaking changes documentation is to consist of a top level [file](BreakingChanges.md) which links to each feature area's individual [BreakingChanges.md](BreakingChanges.md).</span></span>

<span data-ttu-id="0e969-304">功能區 [BreakingChanges.md](BreakingChanges.md) 檔包含特定版本的所有已知中斷變更清單 **，以及過去** 版本的重大變更歷程記錄。</span><span class="sxs-lookup"><span data-stu-id="0e969-304">The feature area [BreakingChanges.md](BreakingChanges.md) files are to contain the list of all known breaking changes for a given release **as well as** the history of breaking changes from past releases.</span></span>

<span data-ttu-id="0e969-305">例如：</span><span class="sxs-lookup"><span data-stu-id="0e969-305">For example:</span></span>

```md
Spatial sound breaking changes

2018.07.2
* Spatialization of the imaginary effect is now required.
* Management of randomized AudioClip files requires an entropy value in the manager node.

2018.07.1
No known breaking changes

2018.07.0
...
```

<span data-ttu-id="0e969-306">包含在功能層級 BreakingChanges.md 檔案中的資訊，將會匯總為每個新 MRTK 版本的版本資訊。</span><span class="sxs-lookup"><span data-stu-id="0e969-306">The information contained within the feature level BreakingChanges.md files will be aggregated to the release notes for each new MRTK release.</span></span>

<span data-ttu-id="0e969-307">任何屬於變更一部分的重大變更都 **必須** 記載為提取要求的一部分。</span><span class="sxs-lookup"><span data-stu-id="0e969-307">Any breaking changes that are part of a change **must** be documented as part of a Pull Request.</span></span>

## <a name="tools-for-editing-markdown"></a><span data-ttu-id="0e969-308">用來編輯 MarkDown 的工具</span><span class="sxs-lookup"><span data-stu-id="0e969-308">Tools for editing MarkDown</span></span>

<span data-ttu-id="0e969-309">[Visual Studio Code](https://code.visualstudio.com/) 是很棒的工具，可讓您編輯屬於 MRTK 檔的 markdown 檔案。</span><span class="sxs-lookup"><span data-stu-id="0e969-309">[Visual Studio Code](https://code.visualstudio.com/) is a great tool for editing markdown files that are part of MRTK's documentation.</span></span>

<span data-ttu-id="0e969-310">撰寫檔時，也強烈建議您安裝下列兩個延伸模組：</span><span class="sxs-lookup"><span data-stu-id="0e969-310">When writing documentation, installing the following two extensions is also highly recommended:</span></span>

- <span data-ttu-id="0e969-311">Visual Studio Code 的檔 Markdown 擴充功能-使用 Alt + M 來顯示檔撰寫選項的功能表。</span><span class="sxs-lookup"><span data-stu-id="0e969-311">Docs Markdown Extension for Visual Studio Code - Use Alt+M to bring up a menu of docs authoring options.</span></span>

- <span data-ttu-id="0e969-312">程式碼拼寫檢查-拼錯的單字會加上底線;以滑鼠右鍵按一下拼錯的字組來變更它，或將它儲存至字典。</span><span class="sxs-lookup"><span data-stu-id="0e969-312">Code Spell Checker - misspelled words will be underlined; right-click on a misspelled word to change it or save it to the dictionary.</span></span>

<span data-ttu-id="0e969-313">這兩個套件都封裝在 Microsoft 發行的檔撰寫套件中。</span><span class="sxs-lookup"><span data-stu-id="0e969-313">Both of these come packaged in the Microsoft published Docs Authoring Pack.</span></span>

## <a name="see-also"></a><span data-ttu-id="0e969-314">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0e969-314">See also</span></span>

- [<span data-ttu-id="0e969-315">檔入口網站產生指南</span><span class="sxs-lookup"><span data-stu-id="0e969-315">Documentation portal generation guide</span></span>](DevDocGuide.md)
