---
title: Unreal 中的編輯器延伸模組
description: 瞭解如何使用自訂腳本、腳本動作和公用程式 widget 來擴充 Unreal 引擎編輯器。
author: hferrone
ms.author: safarooq
ms.date: 01/08/2021
ms.topic: article
ms.localizationpriority: high
keywords: Unreal、Unreal Engine 4、editor extensions、Unreal editor、UE4、HoloLens、HoloLens 2、mixed reality、開發、檔、指南、功能、混合現實耳機、windows mixed reality 耳機、虛擬實境耳機、移植、升級
ms.openlocfilehash: ee0ba5d1d60b83dc334204e12283c76a877b4ec8
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "98584796"
---
# <a name="editor-extensions-in-unreal"></a><span data-ttu-id="68890-104">Unreal 中的編輯器延伸模組</span><span class="sxs-lookup"><span data-stu-id="68890-104">Editor extensions in Unreal</span></span>

<span data-ttu-id="68890-105">Unreal 提供一組豐富的功能，可讓您自訂引擎以滿足您的需求。</span><span class="sxs-lookup"><span data-stu-id="68890-105">Unreal provides an extensive set of features that allow you to customize the engine to your needs.</span></span> <span data-ttu-id="68890-106">這些功能的範圍從簡單但有限，到功能強大但複雜。</span><span class="sxs-lookup"><span data-stu-id="68890-106">The features range from simple but limited, to very powerful but complex.</span></span> <span data-ttu-id="68890-107">下列步驟會依複雜度的順序列出。</span><span class="sxs-lookup"><span data-stu-id="68890-107">The following steps are listed in order of increasing complexity.</span></span> <span data-ttu-id="68890-108">一般來說，在移至更複雜的選項之前，您應該先觸及問題的更簡單解決方案，並耗盡其選項。</span><span class="sxs-lookup"><span data-stu-id="68890-108">In general, you should reach for simpler solutions to your problem, and exhausting its options, before moving to a more complex option.</span></span> <span data-ttu-id="68890-109">舉例而言，我們發現基本的結構腳本可以用來代替大部分的外掛程式。</span><span class="sxs-lookup"><span data-stu-id="68890-109">As an example, we have found that the basic Construction Script can be used in lieu of plugins most of the time.</span></span> 

<!-- Also, engine modification should be a last resort, as it is not only complex, but integrating changes back into the engine for simple work-around can take a disproportionately long time. -->

## <a name="construction-scripts"></a><span data-ttu-id="68890-110">結構腳本</span><span class="sxs-lookup"><span data-stu-id="68890-110">Construction scripts</span></span>

<span data-ttu-id="68890-111">您可以使用結構腳本來執行建立藍圖實例時所執行的初始化動作。</span><span class="sxs-lookup"><span data-stu-id="68890-111">You can use construction scripts to perform initialization actions, which run when Blueprint instance are created.</span></span>

* [<span data-ttu-id="68890-112">使用者結構腳本</span><span class="sxs-lookup"><span data-stu-id="68890-112">User Constructions script</span></span>](https://docs.unrealengine.com/ProgrammingAndScripting/Blueprints/UserGuide/UserConstructionScript/index.html)
* [<span data-ttu-id="68890-113">藍圖範例</span><span class="sxs-lookup"><span data-stu-id="68890-113">Blueprint example</span></span>](https://docs.unrealengine.com/Resources/ContentExamples/Blueprints/1_4/index.html)
* [<span data-ttu-id="68890-114">影片教學課程</span><span class="sxs-lookup"><span data-stu-id="68890-114">Video tutorial</span></span>](https://www.youtube.com/watch?v=z1SD-d9yJmQ&ab_channel=UnrealEngine)

## <a name="scripted-actions"></a><span data-ttu-id="68890-115">腳本的動作</span><span class="sxs-lookup"><span data-stu-id="68890-115">Scripted actions</span></span>

<span data-ttu-id="68890-116">編寫腳本的動作為編輯器公用程式藍圖。</span><span class="sxs-lookup"><span data-stu-id="68890-116">Scripted Actions are Editor Utility Blueprints.</span></span> <span data-ttu-id="68890-117">您可以在 [Unreal 編輯器] 中啟動它們，方法如下：</span><span class="sxs-lookup"><span data-stu-id="68890-117">You can launch them in the Unreal Editor by:</span></span>
* <span data-ttu-id="68890-118">在內容瀏覽器中以滑鼠右鍵按一下 [ **資產** ]</span><span class="sxs-lookup"><span data-stu-id="68890-118">Right-clicking **Assets** in the Content Browser</span></span>
* <span data-ttu-id="68890-119">或者，以滑鼠右鍵 **按一下層** 級區或世界 Outliner 中的動作專案</span><span class="sxs-lookup"><span data-stu-id="68890-119">Or by right-clicking **Actors** either in the Level Viewport or in the World Outliner</span></span>

<span data-ttu-id="68890-120">當您需要藍圖邏輯對資產或動作專案的集合具有內容感知時，腳本的動作是唯一適用的時機。</span><span class="sxs-lookup"><span data-stu-id="68890-120">Scripted Actions are uniquely suited for times when you need your Blueprint logic to have contextual awareness about sets of Assets or Actors.</span></span> <span data-ttu-id="68890-121">一般而言，已編寫腳本的動作會取得您在執行動作時選取的資產或動作專案清單，然後修改這些物件，或將它們視為其圖形。</span><span class="sxs-lookup"><span data-stu-id="68890-121">Typically, a Scripted Action gets a list of Assets or Actors that you've selected when the action is executed, then modifies those objects or considers them in its graph.</span></span>

* [<span data-ttu-id="68890-122">腳本的動作</span><span class="sxs-lookup"><span data-stu-id="68890-122">Scripted Actions</span></span>](https://docs.unrealengine.com/ProductionPipelines/ScriptingAndAutomation/Blueprints/ScriptedActions/index.html)
* [<span data-ttu-id="68890-123">在專案啟動時執行腳本的動作</span><span class="sxs-lookup"><span data-stu-id="68890-123">Running scripted actions on project startup</span></span>](https://docs.unrealengine.com/ProductionPipelines/ScriptingAndAutomation/Blueprints/StartupObjects/index.html)

## <a name="editor-utility-widgets"></a><span data-ttu-id="68890-124">編輯器公用程式小工具</span><span class="sxs-lookup"><span data-stu-id="68890-124">Editor utility widgets</span></span>

<span data-ttu-id="68890-125">每當您想要加入新的 UI 元素，以修改 Unreal 編輯器的消費者介面 (UI) 時，您都可以使用 [編輯器公用程式小工具](https://docs.unrealengine.com/InteractiveExperiences/UMG/UserGuide/EditorUtilityWidgets/index.html) 。</span><span class="sxs-lookup"><span data-stu-id="68890-125">You can use [Editor Utility Widgets](https://docs.unrealengine.com/InteractiveExperiences/UMG/UserGuide/EditorUtilityWidgets/index.html) anytime you want to add new UI elements to modify the User Interface (UI) of the Unreal Editor.</span></span> <span data-ttu-id="68890-126">編輯器公用程式 widget 以 Unreal 動畫圖形為基礎， (UMG) ，因此您可以在藍圖中設定 widget，如同任何其他 UMG Widget 藍圖一樣。</span><span class="sxs-lookup"><span data-stu-id="68890-126">Editor Utility Widgets are based on Unreal Motion Graphics (UMG), so you can set up Widgets in a Blueprint like you would for any other UMG Widget Blueprint.</span></span>

<span data-ttu-id="68890-127">這些小工具專為編輯器 UI 而設計，您可以使用它們來建立自訂編輯器索引標籤。</span><span class="sxs-lookup"><span data-stu-id="68890-127">These Widgets are specifically for the Editor UI, and you can use them to create custom Editor tabs.</span></span> <span data-ttu-id="68890-128">然後，您可以從 Windows 功能表選取這些自訂索引標籤，就像您選取現有的編輯器索引標籤一樣。</span><span class="sxs-lookup"><span data-stu-id="68890-128">You can then select these custom tabs from the Windows menu, like you would select existing Editor tabs.</span></span>

## <a name="plugins"></a><span data-ttu-id="68890-129">外掛程式</span><span class="sxs-lookup"><span data-stu-id="68890-129">Plugins</span></span>

<span data-ttu-id="68890-130">Unreal 可讓您開發及管理您自己的自訂 [外掛程式](https://docs.unrealengine.com/ProductionPipelines/Plugins/index.html) ，以搭配 UE4 工具和執行時間使用。</span><span class="sxs-lookup"><span data-stu-id="68890-130">Unreal lets you develop and manage your own custom [plugins](https://docs.unrealengine.com/ProductionPipelines/Plugins/index.html) for use with UE4 tools and runtime.</span></span> <span data-ttu-id="68890-131">您可以隨時在 [Unreal 編輯器] 中啟用或停用外掛程式。</span><span class="sxs-lookup"><span data-stu-id="68890-131">You can enable or disable your plugins at any time in the Unreal Editor.</span></span> <span data-ttu-id="68890-132">外掛程式可以新增執行時間遊戲功能、修改內建引擎功能、建立新的檔案類型，以及擴充編輯器的功能。</span><span class="sxs-lookup"><span data-stu-id="68890-132">Plugins can add runtime gameplay functionality, modify built-in Engine features, create new file types, and extend the capabilities of the Editor.</span></span>

<!-- ## Engine modifications -->

