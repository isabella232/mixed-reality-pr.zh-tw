---
title: 程式設計總覽
description: 瞭解如何使用腳本來存取 Maquette 物件和介面。
author: hferrone
ms.author: v-hferrone
ms.date: 10/26/2020
ms.topic: article
keywords: Windows Mixed Reality、Maquette、原型設計、混合現實、虛擬實境、VR、MR、意見反應、意見反應中樞、bug
ms.openlocfilehash: 6761ed0fab70b0d497ad1e1398cbd6c1af6ab38b
ms.sourcegitcommit: fae413a2b0420e787671af90f14ee39cde51640f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/19/2020
ms.locfileid: "94935405"
---
# <a name="programming-overview"></a><span data-ttu-id="1adf2-104">程式設計總覽</span><span class="sxs-lookup"><span data-stu-id="1adf2-104">Programming overview</span></span>

<!-- TODO(Harrison): Need consolidated logo with text -->

![標誌](../images/MaquetteIcon.png) <span data-ttu-id="1adf2-106">程式設計總覽</span><span class="sxs-lookup"><span data-stu-id="1adf2-106">Programming Overview</span></span>

<span data-ttu-id="1adf2-107">Microsoft Maquette 會根據 [Jint](https://github.com/sebastienros/jint) 解譯器，使用 JavaScript (ECMAScript 5.1 與延伸模組) 。</span><span class="sxs-lookup"><span data-stu-id="1adf2-107">Microsoft Maquette uses JavaScript (ECMAScript 5.1 with extensions) based on the [Jint](https://github.com/sebastienros/jint) interpreter.</span></span> <span data-ttu-id="1adf2-108">此延伸模組 `.mqjs` 是用來區別 Maquette javascript 檔案與一般 javascript。</span><span class="sxs-lookup"><span data-stu-id="1adf2-108">The extension `.mqjs` is used to distinguish Maquette javascript files from normal JavaScript.</span></span>

<!-- TODO(Stefan): Need more context and high-level explanation of Maquette objects, their accessible interfaces, and functionality. 
                   - What can they do and what problems can they solve?
                   - Is there a specific link to the Maquette object API that can be included here?  
-->
<span data-ttu-id="1adf2-109">Maquette 物件和介面可透過物件存取及編寫腳本 `Maquette` 。</span><span class="sxs-lookup"><span data-stu-id="1adf2-109">Maquette objects and interfaces are accessible and scriptable via the `Maquette` Object.</span></span> <span data-ttu-id="1adf2-110">Maquette 的 API 參考中提供 Maquette 物件和介面的相關檔。</span><span class="sxs-lookup"><span data-stu-id="1adf2-110">Documentation on Maquette Objects and interfaces are provided in Maquette's API Reference.</span></span>

<!-- TODO(Stefan): Link to roadmap information, which hasn't been documented yet. -->
<span data-ttu-id="1adf2-111">MaquetteScript 是新的加法和 flux，因此應該要有變更。</span><span class="sxs-lookup"><span data-stu-id="1adf2-111">MaquetteScript is a new addition and in flux so changes should be expected.</span></span> <span data-ttu-id="1adf2-112">即將提供更詳細的檔和更新。</span><span class="sxs-lookup"><span data-stu-id="1adf2-112">More detailed documentation and updates available soon.</span></span>

<!-- TODO(Stefan): Is Spotlights a component or added functionality of Maquette? -->
## <a name="spotlights-on-scripting"></a><span data-ttu-id="1adf2-113">腳本的聚光燈</span><span class="sxs-lookup"><span data-stu-id="1adf2-113">Spotlights on Scripting</span></span>

* <span data-ttu-id="1adf2-114">TBD-以範例/教學課程為焦點的腳本編寫焦點</span><span class="sxs-lookup"><span data-stu-id="1adf2-114">TBD - Scripting Spotlights focused as Samples/Tutorials</span></span>
  * <span data-ttu-id="1adf2-115">2x 影像/標題–連結至焦點頁面</span><span class="sxs-lookup"><span data-stu-id="1adf2-115">2x Images/Caption – link to spotlight page</span></span>

<!-- TODO(Stefan): Each of these bullets need to be fleshed out. -->
## <a name="getting-started-with-maquettescript"></a><span data-ttu-id="1adf2-116">開始使用 MaquetteScript</span><span class="sxs-lookup"><span data-stu-id="1adf2-116">Getting started with MaquetteScript</span></span>

* <span data-ttu-id="1adf2-117">Mqjs 與 .JS 的比較</span><span class="sxs-lookup"><span data-stu-id="1adf2-117">Mqjs vs. JS</span></span>
* <span data-ttu-id="1adf2-118">程式設計模型</span><span class="sxs-lookup"><span data-stu-id="1adf2-118">Programming Model</span></span>
  * <span data-ttu-id="1adf2-119">編輯 vs. 正在執行</span><span class="sxs-lookup"><span data-stu-id="1adf2-119">Editing vs. Running</span></span>
* <span data-ttu-id="1adf2-120">連結至程式設計工作流程</span><span class="sxs-lookup"><span data-stu-id="1adf2-120">Link to Programming Workflow</span></span>
* <span data-ttu-id="1adf2-121">共用結果的連結</span><span class="sxs-lookup"><span data-stu-id="1adf2-121">Link to Sharing Results</span></span>

## <a name="programming-workflow"></a><span data-ttu-id="1adf2-122">程式設計工作流程</span><span class="sxs-lookup"><span data-stu-id="1adf2-122">Programming workflow</span></span>

<!-- TODO(Stefan): Which of these bullets are no longer TBD? We only want to include documentation on existing content. -->
<span data-ttu-id="1adf2-123">TBD</span><span class="sxs-lookup"><span data-stu-id="1adf2-123">TBD</span></span>
* <span data-ttu-id="1adf2-124">REPL</span><span class="sxs-lookup"><span data-stu-id="1adf2-124">REPL</span></span>
* <span data-ttu-id="1adf2-125">腳本作業</span><span class="sxs-lookup"><span data-stu-id="1adf2-125">Scripting operation</span></span>
* <span data-ttu-id="1adf2-126">偵錯工具操作</span><span class="sxs-lookup"><span data-stu-id="1adf2-126">Debugger operation</span></span>
* <span data-ttu-id="1adf2-127">調試迴圈</span><span class="sxs-lookup"><span data-stu-id="1adf2-127">Debugging loop</span></span>
* <span data-ttu-id="1adf2-128">複製/貼上程式碼？</span><span class="sxs-lookup"><span data-stu-id="1adf2-128">Copy/Paste of code?</span></span>

## <a name="running-mqjs-scripts"></a><span data-ttu-id="1adf2-129">正在執行. mqjs 腳本</span><span class="sxs-lookup"><span data-stu-id="1adf2-129">Running .mqjs scripts</span></span>

<!-- TODO(Stefan): Need screenshot -->
<span data-ttu-id="1adf2-130">若要執行 MaquetteScript mqjs 檔案，請移至 Maquette 的隨附視窗，然後開啟 [腳本] 索引標籤以找出腳本。</span><span class="sxs-lookup"><span data-stu-id="1adf2-130">To run a MaquetteScript .mqjs file, go to the companion windows of Maquette and open the scripting tab to locate scripts.</span></span>

> [!NOTE] 
> <span data-ttu-id="1adf2-131">某些選項將無法運作，因為我們尚未傳送腳本。</span><span class="sxs-lookup"><span data-stu-id="1adf2-131">Some options will not work yet because we have not ship the scripts.</span></span>

## <a name="vscode-editor-workflow"></a><span data-ttu-id="1adf2-132">VSCode 編輯器工作流程</span><span class="sxs-lookup"><span data-stu-id="1adf2-132">VSCode Editor Workflow</span></span>

<span data-ttu-id="1adf2-133">若要從 VSCode 內評估 Maquette 中的腳本，使用者必須知道兩個命令：</span><span class="sxs-lookup"><span data-stu-id="1adf2-133">To evaluate script in Maquette from within VSCode, the user needs to know two commands:</span></span>

   <span data-ttu-id="1adf2-134">`CTRL-5` 評估選取的文字或游標所在的整個行。</span><span class="sxs-lookup"><span data-stu-id="1adf2-134">`CTRL-5` evaluates the selected text or the entire line where the cursor is located.</span></span> 

   <span data-ttu-id="1adf2-135">`CTRL-SHIFT-5` 評估整個檔案。</span><span class="sxs-lookup"><span data-stu-id="1adf2-135">`CTRL-SHIFT-5` evaluates the entire file.</span></span>

<!-- TODO(Stefan): This could use a nice simple infographic of the REPL loop. -->
<span data-ttu-id="1adf2-136">文字會傳送至 Maquette，並在 JavaScript 環境中進行評估，並將結果傳回至 VSCode 的輸出主控台。</span><span class="sxs-lookup"><span data-stu-id="1adf2-136">Text is sent to Maquette, evaluated in the JavaScript environment, and the result is sent back to the output console of VSCode.</span></span> <span data-ttu-id="1adf2-137">這可以用來做為複寫 (讀取-評估-列印迴圈) 。</span><span class="sxs-lookup"><span data-stu-id="1adf2-137">This can be used as a REPL (read-eval-print-loop).</span></span>

## <a name="example-first-step"></a><span data-ttu-id="1adf2-138">範例第一個步驟</span><span class="sxs-lookup"><span data-stu-id="1adf2-138">Example First Step</span></span>

<!-- TODO(Stefan): What kind of file, a C# or .mqjs file? -->
<span data-ttu-id="1adf2-139">將下列程式碼複製到 VSCode 中的檔案：</span><span class="sxs-lookup"><span data-stu-id="1adf2-139">Copy the following code into a file in VSCode:</span></span>

```csharp
var myCube = Maquette.CreateCube();
myCube.position = Maquette.User.GetPositionInFront(0.6);
myCube.color = Color(1.0, 0.5, 0.0);
```

<!-- TODO(Stefan): Need screenshot. -->
<span data-ttu-id="1adf2-140">選取程式碼，或只選取區段，然後按 [ `CTRL-5` 執行]。</span><span class="sxs-lookup"><span data-stu-id="1adf2-140">Select the code or just sections and hit `CTRL-5` to execute.</span></span> <span data-ttu-id="1adf2-141">這應該會建立一個 cube，將它放在您的前方，然後變更其色彩。</span><span class="sxs-lookup"><span data-stu-id="1adf2-141">This should create a cube, place it in front of you and change its color.</span></span>

<span data-ttu-id="1adf2-142">還有更多範例可透過擴充功能來尋找。</span><span class="sxs-lookup"><span data-stu-id="1adf2-142">There are more examples to find through the extension.</span></span>

## <a name="sharing-results"></a><span data-ttu-id="1adf2-143">共用結果</span><span class="sxs-lookup"><span data-stu-id="1adf2-143">Sharing Results</span></span>

<!-- TODO(Stefan): Need to fill in content/context for these bullets. If there's a lot of content, we might consider breaking this out into it's own doc. -->
<span data-ttu-id="1adf2-144">如何在使用者/小組之間共用</span><span class="sxs-lookup"><span data-stu-id="1adf2-144">How to share between users/teams</span></span>
* <span data-ttu-id="1adf2-145">檔目錄中的 Zip 專案</span><span class="sxs-lookup"><span data-stu-id="1adf2-145">Zip project in documents directory</span></span>
* <span data-ttu-id="1adf2-146">將專案複製到檔案共用</span><span class="sxs-lookup"><span data-stu-id="1adf2-146">Copy project to file share</span></span>
* <span data-ttu-id="1adf2-147">將小組共用提交的檔案位置新增至 Maquette 小組</span><span class="sxs-lookup"><span data-stu-id="1adf2-147">Adding file location of team share Submissions to Maquette Team</span></span>

<!-- TODO(Stefan): Need to break these out into their own sections and fill in the missing content/context. 
                   - Which of these is accessible now and not TBD?
-->
<span data-ttu-id="1adf2-148">TBD</span><span class="sxs-lookup"><span data-stu-id="1adf2-148">TBD</span></span>
* <span data-ttu-id="1adf2-149">包含，以相對/絕對路徑、模組參考其他位置的程式碼</span><span class="sxs-lookup"><span data-stu-id="1adf2-149">Includes, reference to code elsewhere with relative/absolute paths, modules</span></span>
* <span data-ttu-id="1adf2-150">圖書館？</span><span class="sxs-lookup"><span data-stu-id="1adf2-150">Libraries?</span></span>
* <span data-ttu-id="1adf2-151">執行階段支援</span><span class="sxs-lookup"><span data-stu-id="1adf2-151">Runtime support</span></span>
* <span data-ttu-id="1adf2-152">未解析的外部-當專案遺失/損毀時的行為</span><span class="sxs-lookup"><span data-stu-id="1adf2-152">Unresolved Externals - Behavior when entries missing/crashing</span></span>
* <span data-ttu-id="1adf2-153">我們可以新增/編輯/觀察與特定物件相關的腳本嗎？</span><span class="sxs-lookup"><span data-stu-id="1adf2-153">Can we add/edit/observe script associated with specific objects?</span></span>
  * <span data-ttu-id="1adf2-154">我們可以在其他地方複製/貼上此腳本嗎？</span><span class="sxs-lookup"><span data-stu-id="1adf2-154">Can we copy/paste this script elsewhere?</span></span>
  * <span data-ttu-id="1adf2-155">物件屬性呢？</span><span class="sxs-lookup"><span data-stu-id="1adf2-155">What about object properties?</span></span>
  * <span data-ttu-id="1adf2-156">在我的場景中命名物件？</span><span class="sxs-lookup"><span data-stu-id="1adf2-156">Naming objects in my scene?</span></span> <span data-ttu-id="1adf2-157"> (將腳本重新命名) </span><span class="sxs-lookup"><span data-stu-id="1adf2-157">(renaming script with it)</span></span>
  * <span data-ttu-id="1adf2-158">與物件相關聯之腳本的這個或本身關鍵字</span><span class="sxs-lookup"><span data-stu-id="1adf2-158">THIS or SELF keyword for script associated with an object</span></span>
  * <span data-ttu-id="1adf2-159">如果我在物件上按一下滑鼠右鍵，可以看到與它相關聯的程式碼 (與其所有階層) </span><span class="sxs-lookup"><span data-stu-id="1adf2-159">If I right click on an object, can I see code associated with it (and all it's hierarchy)</span></span>
  * <span data-ttu-id="1adf2-160">我可以在 UI 中選取，並且在 VSCode 的程式碼中啟動嗎？</span><span class="sxs-lookup"><span data-stu-id="1adf2-160">Can I select in UI and be brought up at the code in VSCode?</span></span>
  * <span data-ttu-id="1adf2-161">在腳本來源檔案中將與物件相關聯的程式碼保持在一起？</span><span class="sxs-lookup"><span data-stu-id="1adf2-161">Keeping code associated with an object "together" in the script source file?</span></span>
  * <span data-ttu-id="1adf2-162">當我按一下物件時，將屬性視窗帶到該物件的上方？</span><span class="sxs-lookup"><span data-stu-id="1adf2-162">Bring property window up of an object when I click on it?</span></span> <span data-ttu-id="1adf2-163">在 VR 和主要索引標籤中？</span><span class="sxs-lookup"><span data-stu-id="1adf2-163">In VR and in main tab?</span></span>
* <span data-ttu-id="1adf2-164">安全性問題</span><span class="sxs-lookup"><span data-stu-id="1adf2-164">Security Issues</span></span>
* <span data-ttu-id="1adf2-165">測試–可能是待定的，但我們可以建議以腳本的方式抓取影片或畫面格</span><span class="sxs-lookup"><span data-stu-id="1adf2-165">Testing – might be TBD but we could suggest video or frame grab by script</span></span>
* <span data-ttu-id="1adf2-166">如果我們有錯誤報表機制，我們可能會透過腳本讓他人存取 (？ ) .。。後</span><span class="sxs-lookup"><span data-stu-id="1adf2-166">If we have a bug reporting mechanism, we might make that accessible via script for others (?) …later</span></span>
* <span data-ttu-id="1adf2-167">部署–如何「共用」結果，套件為 EXE</span><span class="sxs-lookup"><span data-stu-id="1adf2-167">Deployment – how to “share” the result, package as EXE</span></span>
* <span data-ttu-id="1adf2-168">執行/控制示範或 spectating/監視</span><span class="sxs-lookup"><span data-stu-id="1adf2-168">Running/controlling a demo or spectating/monitoring</span></span>
* <span data-ttu-id="1adf2-169">播放機模式</span><span class="sxs-lookup"><span data-stu-id="1adf2-169">Player mode</span></span>
* <span data-ttu-id="1adf2-170">我們可能會有一段有關如何讓「元件」進行共用的區段？</span><span class="sxs-lookup"><span data-stu-id="1adf2-170">We might have a segment on how to make “components” for sharing?</span></span> <span data-ttu-id="1adf2-171"> (可能是 tbd) </span><span class="sxs-lookup"><span data-stu-id="1adf2-171">(might  be tbd)</span></span>
  * <span data-ttu-id="1adf2-172">有 #include 嗎？</span><span class="sxs-lookup"><span data-stu-id="1adf2-172">Is there #include?</span></span> <span data-ttu-id="1adf2-173">這會處理純 JS，但可能會有命名空間衝突。</span><span class="sxs-lookup"><span data-stu-id="1adf2-173">This handles pure JS I suppose but may have namespace conflicts.</span></span>
  * <span data-ttu-id="1adf2-174">有什麼我們可以針對 maquette 合併其他具有命名物件的 maquette，以符合 JS 程式碼？</span><span class="sxs-lookup"><span data-stu-id="1adf2-174">Is there anything we could do for a maquette to incorporate some other maquette with named objects to match JS code?</span></span>
