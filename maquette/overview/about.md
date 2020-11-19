---
title: 關於 Maquette
description: Maquette 及其功能的簡介。
author: hferrone
ms.author: v-hferrone
ms.date: 10/26/2020
ms.topic: article
keywords: Windows Mixed Reality、Maquette、原型設計、混合現實、虛擬實境、VR、MR、意見反應、意見反應中樞、bug
ms.openlocfilehash: fbc2aee7472a26e508937fa1dedfdac08fadfa10
ms.sourcegitcommit: fae413a2b0420e787671af90f14ee39cde51640f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/19/2020
ms.locfileid: "94935413"
---
# <a name="about-maquette"></a><span data-ttu-id="9af2c-104">關於 Maquette</span><span class="sxs-lookup"><span data-stu-id="9af2c-104">About Maquette</span></span>

<!-- TODO(Harrison): Need consolidated logo with text -->
<span data-ttu-id="9af2c-105">![標誌 ](../images/MaquetteIcon.png) MaquetteScript 簡介</span><span class="sxs-lookup"><span data-stu-id="9af2c-105">![Logo](../images/MaquetteIcon.png) MaquetteScript Introduction</span></span>

<!-- TODO(Harrison/Stefan): Add more high level, less technical explanation of what Maquette is and why it's useful in MR development. 
          - Differentiate between Maquette and MaquetteScript
          - Separate out each of Maquette's main parts and add content
          - Give brief explanations of use case or examples
-->
<span data-ttu-id="9af2c-106">Maquette 整合了標準 ECMA 5.1 JAVAscript，可讓您在 Maquette 場景和物件中投資互動，而這些物件可在 VSCode 內進行編輯和執行。</span><span class="sxs-lookup"><span data-stu-id="9af2c-106">Maquette integrates standard ECMA 5.1 Javascript to enable investment of interactivity in Maquette scenes and objects which can be edited and executed from within VSCode.</span></span> <span data-ttu-id="9af2c-107">從腳本、呼叫的物件方法和物件和系統事件回復中，會公開物件的屬性，以進行讀取和設定。</span><span class="sxs-lookup"><span data-stu-id="9af2c-107">Properties of objects are exposed for reading and setting from within script, object methods called, and object and system events fielded.</span></span> <span data-ttu-id="9af2c-108">腳本也可以透過可透過腳本存取的系統物件，與 Maquette 本身互動。</span><span class="sxs-lookup"><span data-stu-id="9af2c-108">Script can also interact with Maquette itself via system objects accessible via script.</span></span> <span data-ttu-id="9af2c-109">使用者可以與之互動的各種 UI 控制項都是系統的一部分。</span><span class="sxs-lookup"><span data-stu-id="9af2c-109">Various UI controls that the user can interact with are part of the system.</span></span> <span data-ttu-id="9af2c-110">當您在 Maquette 中撰寫或從腳本內建立和管理時，可以加入這些功能。</span><span class="sxs-lookup"><span data-stu-id="9af2c-110">These can be added when authoring in Maquette or created and managed from within script.</span></span> <span data-ttu-id="9af2c-111">使用這些元素的使用者互動事件 (資料輸入、按一下等) 也會公開給腳本做為事件。</span><span class="sxs-lookup"><span data-stu-id="9af2c-111">User interaction events with these elements (data entry, clicks, etc) are also exposed to script as events.</span></span> <span data-ttu-id="9af2c-112">有了這些新增功能，就可以建立簡單到複雜的場景，從實驗到資料視覺效果，到探勘混合的現實使用者案例，以充分瞭解 AR 或 VR 的體驗。</span><span class="sxs-lookup"><span data-stu-id="9af2c-112">With these additions, simple to complex scenes can be built, from experiments to data visualization to explorations of Mixed Reality user scenarios to fully realized experiences in AR or VR.</span></span>

<p align="center">
  <img src="images/ScriptingOverview.png" alt="Scripting overview video screenshot">
</p>

<!-- TODO(Harrison/Stefan): Get this video recorded or create the content in text form until it's available. -->
<span data-ttu-id="9af2c-113">60 second'ish 影片</span><span class="sxs-lookup"><span data-stu-id="9af2c-113">60 second'ish video</span></span>
* <span data-ttu-id="9af2c-114">輸入標題卡</span><span class="sxs-lookup"><span data-stu-id="9af2c-114">Entry Title Card</span></span>
  * <span data-ttu-id="9af2c-115">在 Maquette 中建立互動式混合現實內容</span><span class="sxs-lookup"><span data-stu-id="9af2c-115">Creation of Interactive Mixed Reality Content in Maquette</span></span>
  * <span data-ttu-id="9af2c-116">腳本/互動/UI 系統</span><span class="sxs-lookup"><span data-stu-id="9af2c-116">Scripting/Interactivity/UI System</span></span>
* <span data-ttu-id="9af2c-117">您可以使用小組或影片標題的 [歡迎使用]</span><span class="sxs-lookup"><span data-stu-id="9af2c-117">VO welcome by team or video captions?</span></span>  <span data-ttu-id="9af2c-118">解釋：</span><span class="sxs-lookup"><span data-stu-id="9af2c-118">explaining:</span></span>
  * <span data-ttu-id="9af2c-119">編寫腳本的理由，以啟用互動式 MR 內容的建立</span><span class="sxs-lookup"><span data-stu-id="9af2c-119">reasoning behind scripting to enable creation of interactive MR content</span></span>
  * <span data-ttu-id="9af2c-120">接觸如何在非常廣泛的筆刷筆劃中使用</span><span class="sxs-lookup"><span data-stu-id="9af2c-120">touch on how it can be used in very broad brush strokes</span></span>
* <span data-ttu-id="9af2c-121">腳本 vingette 的實際運作</span><span class="sxs-lookup"><span data-stu-id="9af2c-121">Scripting vingette’s in action</span></span>
  * <span data-ttu-id="9af2c-122">撰寫對話方塊</span><span class="sxs-lookup"><span data-stu-id="9af2c-122">Composing dialog box</span></span>
  * <span data-ttu-id="9af2c-123">從大綱建立應用程式 (烹飪應用程式示範) </span><span class="sxs-lookup"><span data-stu-id="9af2c-123">Building app from outline (cooking app demo)</span></span>
  * <span data-ttu-id="9af2c-124">在攝影測量模型中撰寫</span><span class="sxs-lookup"><span data-stu-id="9af2c-124">Composing in photogrammetry model</span></span>
  * <span data-ttu-id="9af2c-125">與疑難排解指南互動</span><span class="sxs-lookup"><span data-stu-id="9af2c-125">Interacting with troubleshooting guide</span></span>
  * <span data-ttu-id="9af2c-126">在 VSCode 中偵錯工具腳本的螢幕視圖</span><span class="sxs-lookup"><span data-stu-id="9af2c-126">Screen view of debugging scripting in VSCode</span></span>
  * <span data-ttu-id="9af2c-127">從場景中的物件取得腳本的存取權</span><span class="sxs-lookup"><span data-stu-id="9af2c-127">Getting access to script from an object in scene</span></span>
  * <span data-ttu-id="9af2c-128">等。。。</span><span class="sxs-lookup"><span data-stu-id="9af2c-128">Etc...</span></span>
* <span data-ttu-id="9af2c-129">摘要標題卡片結束</span><span class="sxs-lookup"><span data-stu-id="9af2c-129">Summary Title card at end</span></span>
  * <span data-ttu-id="9af2c-130">連結至 Maquette</span><span class="sxs-lookup"><span data-stu-id="9af2c-130">Link to Maquette</span></span>
  * <span data-ttu-id="9af2c-131">開始使用腳本的位置</span><span class="sxs-lookup"><span data-stu-id="9af2c-131">Where to go to get started with scripting</span></span>
  * <span data-ttu-id="9af2c-132">公告/狀態/群體</span><span class="sxs-lookup"><span data-stu-id="9af2c-132">Announcements/status/community</span></span>
  * <span data-ttu-id="9af2c-133">想看看您可以如何 (？ ) </span><span class="sxs-lookup"><span data-stu-id="9af2c-133">Look forward to seeing what you can do/submissions(?)</span></span>
  * <span data-ttu-id="9af2c-134">意見反應，以及我們如何為您提供更好的服務</span><span class="sxs-lookup"><span data-stu-id="9af2c-134">Feedback and how we can serve you better</span></span>

<!-- TODO(Harrison): Consider breaking this out into a Maquette journey doc or section as applicable. -->
* [<span data-ttu-id="9af2c-135">快速入門</span><span class="sxs-lookup"><span data-stu-id="9af2c-135">Getting Started</span></span>](installation.md)
* [<span data-ttu-id="9af2c-136">範例和範例應用程式</span><span class="sxs-lookup"><span data-stu-id="9af2c-136">Examples and Sample Apps</span></span>](../samples/overview.md)
* [<span data-ttu-id="9af2c-137">支援</span><span class="sxs-lookup"><span data-stu-id="9af2c-137">Support</span></span>](../resources/support.md)

<!-- TODO(Harrison): Need to find out why docs feedback footer isn't appearing. -->
## <a name="send-us-feedback"></a><span data-ttu-id="9af2c-138">傳送意見反應</span><span class="sxs-lookup"><span data-stu-id="9af2c-138">Send us feedback</span></span>

<span data-ttu-id="9af2c-139">我們期待收到您的體驗和結果。</span><span class="sxs-lookup"><span data-stu-id="9af2c-139">We look forward to hearing about your experiences and results.</span></span> <span data-ttu-id="9af2c-140">意見反應、建議和錯誤報表一律歡迎使用！</span><span class="sxs-lookup"><span data-stu-id="9af2c-140">Feedback, suggestions and bug reports always welcome!</span></span>
<span data-ttu-id="9af2c-141"><連結？ ></span><span class="sxs-lookup"><span data-stu-id="9af2c-141"><Link?></span></span>