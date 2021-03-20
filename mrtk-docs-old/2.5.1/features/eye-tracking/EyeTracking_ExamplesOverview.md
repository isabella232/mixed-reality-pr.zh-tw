---
title: EyeTracking_ExampleOverview
description: 在 MRTK 中建立 eyetracking 的範例
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、EyeTracking、
ms.openlocfilehash: 2b9d373363bee8d7ad3482fc234c8966f6258706
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104682441"
---
# <a name="eye-tracking-examples"></a><span data-ttu-id="7d917-104">目視追蹤範例</span><span class="sxs-lookup"><span data-stu-id="7d917-104">Eye tracking examples</span></span>

<span data-ttu-id="7d917-105">本主題說明如何在 MRTK 中建立 MRTK 眼睛追蹤範例（ (資產/MRTK/範例/示範/EyeTracking) ），以快速開始使用眼睛追蹤。</span><span class="sxs-lookup"><span data-stu-id="7d917-105">This topic describes how to quickly get started with eye tracking in MRTK by building on MRTK eye tracking examples (Assets/MRTK/Examples/Demos/EyeTracking).</span></span>
<span data-ttu-id="7d917-106">這些範例可讓您體驗其中一個新的神奇輸入功能： **眼睛追蹤**！</span><span class="sxs-lookup"><span data-stu-id="7d917-106">These samples let you experience one of our new magical input capabilities: **Eye tracking**!</span></span>
<span data-ttu-id="7d917-107">此示範包含各種使用案例，範圍從隱含的眼睛型啟用到如何順暢地結合您正在尋找的資訊與 **語音** 和 **手寫** 輸入相關資訊。</span><span class="sxs-lookup"><span data-stu-id="7d917-107">The demo includes various use cases, ranging from implicit eye-based activations to how to seamlessly combine information about what you are looking at with **voice** and **hand** input.</span></span>
<span data-ttu-id="7d917-108">如此一來，使用者就可以透過查看目標並說出「 _選取_ 」或執行手勢，快速且輕鬆地在其觀點中選取和移動全像攝影內容。</span><span class="sxs-lookup"><span data-stu-id="7d917-108">This enables users to quickly and effortlessly select and move holographic content across their view simply by looking at a target and saying _'Select'_ or performing a hand gesture.</span></span>
<span data-ttu-id="7d917-109">示範中也包含了眼睛導向滾動、文字的平移和縮放，以及平板的影像。</span><span class="sxs-lookup"><span data-stu-id="7d917-109">The demos also include an example for eye-gaze-directed scroll, pan and zoom of text and images on a slate.</span></span>
<span data-ttu-id="7d917-110">最後，會提供一個範例來錄製和視覺化使用者對2D 平板的視覺效果。</span><span class="sxs-lookup"><span data-stu-id="7d917-110">Finally, an example is provided for recording and visualizing the user's visual attention on a 2D slate.</span></span>
<span data-ttu-id="7d917-111">在下一節中，您將會在 MRTK 眼睛追蹤範例套件 (資產/MRTK/範例/示範/EyeTracking) 包含的每個不同範例中，找到更多詳細資料：</span><span class="sxs-lookup"><span data-stu-id="7d917-111">In the following section, you will find more details on what each of the different samples in the MRTK eye tracking example package (Assets/MRTK/Examples/Demos/EyeTracking) includes:</span></span>

![眼睛追蹤場景清單](../images/eye-tracking/mrtk_et_list_et_scenes.jpg)

<span data-ttu-id="7d917-113">下一節簡要說明個別的眼睛追蹤示範場景。</span><span class="sxs-lookup"><span data-stu-id="7d917-113">The following section is a quick overview of what the individual eye tracking demo scenes are about.</span></span>
<span data-ttu-id="7d917-114">MRTK 眼追蹤示範場景已 [載入額外](https://docs.unity3d.com/ScriptReference/SceneManagement.LoadSceneMode.Additive.html)，我們將在下面說明如何進行設定。</span><span class="sxs-lookup"><span data-stu-id="7d917-114">The MRTK eye tracking demo scenes are [loaded additively](https://docs.unity3d.com/ScriptReference/SceneManagement.LoadSceneMode.Additive.html), which we will explain below how to set up.</span></span>

## <a name="overview-of-the-eye-tracking-demo-samples"></a><span data-ttu-id="7d917-115">目視追蹤示範範例簡介</span><span class="sxs-lookup"><span data-stu-id="7d917-115">Overview of the eye tracking demo samples</span></span>

### <a name="eye-supported-target-selection"></a>[<span data-ttu-id="7d917-116">**目視支援的目標選取範圍**</span><span class="sxs-lookup"><span data-stu-id="7d917-116">**Eye-Supported Target Selection**</span></span>](EyeTracking_TargetSelection.md)

<span data-ttu-id="7d917-117">本教學課程示範如何輕鬆地存取眼睛資料來選取目標。</span><span class="sxs-lookup"><span data-stu-id="7d917-117">This tutorial showcases the ease of accessing eye gaze data to select targets.</span></span>
<span data-ttu-id="7d917-118">其中包含微妙但功能強大的意見反應範例，可讓使用者確信目標的焦點不會變大。</span><span class="sxs-lookup"><span data-stu-id="7d917-118">It includes an example for subtle yet powerful feedback to provide the user with the confidence that a target is focused without being overwhelming.</span></span>
<span data-ttu-id="7d917-119">此外，也有一個簡單的智慧型通知範例，會在讀取後自動消失。</span><span class="sxs-lookup"><span data-stu-id="7d917-119">In addition, there is a simple example of smart notifications that automatically disappear after being read.</span></span>

<span data-ttu-id="7d917-120">**摘要**：使用眼睛、語音和手寫輸入的組合，快速且輕鬆地選取目標。</span><span class="sxs-lookup"><span data-stu-id="7d917-120">**Summary**: Fast and effortless target selections using a combination of eyes, voice and hand input.</span></span>

### <a name="eye-supported-navigation"></a>[<span data-ttu-id="7d917-121">**目視支援的導覽**</span><span class="sxs-lookup"><span data-stu-id="7d917-121">**Eye-Supported Navigation**</span></span>](EyeTracking_Navigation.md)

<span data-ttu-id="7d917-122">假設您正在閱讀有關遠處顯示器或電子讀者的一些資訊，當您到達顯示文字的結尾時，文字會自動向上滾動以顯示更多內容。</span><span class="sxs-lookup"><span data-stu-id="7d917-122">Imagine that you are reading some information on a distant display or your e-reader and when you reach the end of the displayed text, the text automatically scrolls up to reveal more content.</span></span>
<span data-ttu-id="7d917-123">或者，如何以神奇的方式直接縮放至您所看到的位置？</span><span class="sxs-lookup"><span data-stu-id="7d917-123">Or how about magically zooming directly toward where you were looking at?</span></span>
<span data-ttu-id="7d917-124">以下是本教學課程中展示有關眼睛支援導覽的一些範例。</span><span class="sxs-lookup"><span data-stu-id="7d917-124">These are some of the examples showcased in this tutorial regarding eye-supported navigation.</span></span>
<span data-ttu-id="7d917-125">此外，也有一個範例，可讓您根據目前的焦點自動旋轉，來旋轉3D 全像投影。</span><span class="sxs-lookup"><span data-stu-id="7d917-125">In addition, there is an example for hands-free rotation of 3D holograms by making them automatically rotate based on your current focus.</span></span>

<span data-ttu-id="7d917-126">**摘要**：使用眼睛、語音和手寫輸入的組合來移動捲軸、平移、縮放、3d 旋轉。</span><span class="sxs-lookup"><span data-stu-id="7d917-126">**Summary**: Scroll, pan, zoom, 3D rotation using a combination of eyes, voice and hand input.</span></span>

### <a name="eye-supported-positioning"></a>[<span data-ttu-id="7d917-127">**目視支援的定位**</span><span class="sxs-lookup"><span data-stu-id="7d917-127">**Eye-Supported Positioning**</span></span>](EyeTracking_Positioning.md)

<span data-ttu-id="7d917-128">本教學課程會顯示稱為 [Put-的](https://youtu.be/CbIn8p4_4CQ) 輸入案例，也就是在早期的1980和語音輸入中，從 MIT 媒體實驗室的可追溯回到研究。</span><span class="sxs-lookup"><span data-stu-id="7d917-128">This tutorial shows an input scenario called [Put-That-There](https://youtu.be/CbIn8p4_4CQ) dating back to research from the MIT Media Lab in the early 1980's with eye, hand and voice input.</span></span>
<span data-ttu-id="7d917-129">這是很簡單的概念：從您的眼睛中獲益，以提供快速目標選擇和定位。</span><span class="sxs-lookup"><span data-stu-id="7d917-129">The idea is simple: Benefit from your eyes for fast target selection and positioning.</span></span>
<span data-ttu-id="7d917-130">只要看一下一個全息圖，然後說 [ _put this （放置這_ 一點）]，再看一下您要放置它的位置，然後說「 _有！_」。</span><span class="sxs-lookup"><span data-stu-id="7d917-130">Simply look at a hologram and say _'put this'_, look over where you want to place it and say _'there!'_.</span></span>
<span data-ttu-id="7d917-131">若要更精確地放置全息圖，您可以使用來自您手、語音或控制器的其他輸入。</span><span class="sxs-lookup"><span data-stu-id="7d917-131">For more precisely positioning your hologram, you can use additional input from your hands, voice or controllers.</span></span>

<span data-ttu-id="7d917-132">**摘要**：使用眼睛、語音和手輸入來定位全息 (*拖放*) 。</span><span class="sxs-lookup"><span data-stu-id="7d917-132">**Summary**: Positioning holograms using eyes, voice and hand input (*drag-and-drop*).</span></span> <span data-ttu-id="7d917-133">使用眼睛 + 手的眼睛支援滑杆。</span><span class="sxs-lookup"><span data-stu-id="7d917-133">Eye-supported sliders using eyes + hands.</span></span>

### <a name="visualization-of-visual-attention"></a><span data-ttu-id="7d917-134">**視覺效果的視覺效果**</span><span class="sxs-lookup"><span data-stu-id="7d917-134">**Visualization of visual attention**</span></span>

<span data-ttu-id="7d917-135">以使用者外觀為基礎的資料，可讓您以極強大的工具來評估設計的可用性，並在有效率的工作資料流程中找出問題。</span><span class="sxs-lookup"><span data-stu-id="7d917-135">Data based on where users look makes an immensely powerful tool to assess usability of a design and to identify problems in efficient work streams.</span></span>
<span data-ttu-id="7d917-136">本教學課程會討論不同的眼睛追蹤視覺效果，以及它們如何符合不同的需求。</span><span class="sxs-lookup"><span data-stu-id="7d917-136">This tutorial discusses different eye tracking visualizations and how they fit different needs.</span></span>
<span data-ttu-id="7d917-137">我們提供記錄和載入眼睛追蹤資料的基本範例，以及如何將其視覺化的範例。</span><span class="sxs-lookup"><span data-stu-id="7d917-137">We provide basic examples for logging and loading eye tracking data and examples for how to visualize them.</span></span>

<span data-ttu-id="7d917-138">**摘要**：在平板上 (熱度圖) 的二維強調地圖。</span><span class="sxs-lookup"><span data-stu-id="7d917-138">**Summary**: Two-dimensional attention map (heatmaps) on slates.</span></span> <span data-ttu-id="7d917-139">錄製 & 重新執行眼睛追蹤資料。</span><span class="sxs-lookup"><span data-stu-id="7d917-139">Recording & replaying eye tracking data.</span></span>

## <a name="setting-up-the-mrtk-eye-tracking-samples"></a><span data-ttu-id="7d917-140">設定 MRTK 眼追蹤範例</span><span class="sxs-lookup"><span data-stu-id="7d917-140">Setting up the MRTK eye tracking samples</span></span>

### <a name="prerequisites"></a><span data-ttu-id="7d917-141">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="7d917-141">Prerequisites</span></span>

<span data-ttu-id="7d917-142">請注意，在裝置上使用眼睛追蹤範例需要 HoloLens 2，以及使用套件 Package.appxmanifest 上的「注視輸入」功能建立的範例應用程式套件。</span><span class="sxs-lookup"><span data-stu-id="7d917-142">Note that using the eye tracking samples on device requires a HoloLens 2 and a sample app package that is built with the "Gaze Input" capability on the package's AppXManifest.</span></span>

<span data-ttu-id="7d917-143">為了在裝置上使用這些眼睛追蹤範例，請務必遵循 [這些步驟](EyeTracking_BasicSetup.md#testing-your-unity-app-on-a-hololens-2) ，然後再 Visual Studio 中建立應用程式。</span><span class="sxs-lookup"><span data-stu-id="7d917-143">In order to use these eye tracking samples on device, make sure to follow [these steps](EyeTracking_BasicSetup.md#testing-your-unity-app-on-a-hololens-2) prior to building the app in Visual Studio.</span></span>

### <a name="1-load-eyetrackingdemo-00-rootsceneunity"></a><span data-ttu-id="7d917-144">1. Load EyeTrackingDemo-00-RootScene unity</span><span class="sxs-lookup"><span data-stu-id="7d917-144">1. Load EyeTrackingDemo-00-RootScene.unity</span></span>

<span data-ttu-id="7d917-145">*EyeTrackingDemo-00-RootScene* 是基底 (_根_) 場景，其中包含所有核心 MRTK 元件。</span><span class="sxs-lookup"><span data-stu-id="7d917-145">The *EyeTrackingDemo-00-RootScene* is the base (_root_) scene that has all the core MRTK components included.</span></span>
<span data-ttu-id="7d917-146">這是您必須先載入的場景，您將在其中執行眼睛追蹤示範。</span><span class="sxs-lookup"><span data-stu-id="7d917-146">This is the scene that you need to load first and from which you will run the eye tracking demos.</span></span>
<span data-ttu-id="7d917-147">它有一個圖形化的場景功能表，可讓您輕鬆地在將 [載入額外](https://docs.unity3d.com/ScriptReference/SceneManagement.LoadSceneMode.Additive.html)的不同眼睛追蹤範例之間切換。</span><span class="sxs-lookup"><span data-stu-id="7d917-147">It features a graphical scene menu that allows you to easily switch between the different eye tracking samples which will be [loaded additively](https://docs.unity3d.com/ScriptReference/SceneManagement.LoadSceneMode.Additive.html).</span></span>

![目視追蹤範例中的場景功能表](../images/eye-tracking/mrtk_et_scenemenu.jpg)

<span data-ttu-id="7d917-149">根場景包含一些核心元件，這些元件會跨額外載入的場景保存，例如 MRTK 設定的設定檔和場景相機。</span><span class="sxs-lookup"><span data-stu-id="7d917-149">The root scene includes a few core components that will persist across the additively loaded scenes, such as the MRTK configured profiles and scene camera.</span></span>
<span data-ttu-id="7d917-150">_MixedRealityBasicSceneSetup_ (請參閱下面的螢幕擷取畫面) 包含會在啟動時自動載入參考場景的腳本。</span><span class="sxs-lookup"><span data-stu-id="7d917-150">The _MixedRealityBasicSceneSetup_ (see screenshot below) includes a script that will automatically load the referenced scene on startup.</span></span>
<span data-ttu-id="7d917-151">根據預設，這是 _EyeTrackingDemo-02-TargetSelection_。</span><span class="sxs-lookup"><span data-stu-id="7d917-151">By default, this is _EyeTrackingDemo-02-TargetSelection_.</span></span>  

![OnLoadStartScene 腳本的範例](../images/eye-tracking/mrtk_et_onloadstartscene.jpg)

### <a name="2-adding-scenes-to-the-build-menu"></a><span data-ttu-id="7d917-153">2. 將場景新增至 [組建] 功能表</span><span class="sxs-lookup"><span data-stu-id="7d917-153">2. Adding scenes to the build menu</span></span>

<span data-ttu-id="7d917-154">若要在執行時間載入加法場景，您必須先在組建功能表中將這些場景新增至 _組建設定-> 場景_ 。</span><span class="sxs-lookup"><span data-stu-id="7d917-154">To load additive scenes during runtime, you must add these scenes to your _Build Settings -> Scenes in Build_ menu first.</span></span>
<span data-ttu-id="7d917-155">將根場景顯示為清單中的第一個場景是很重要的：</span><span class="sxs-lookup"><span data-stu-id="7d917-155">It is important that the root scene is shown as the first scene in the list:</span></span>

![目視追蹤範例的組建設定場景功能表](../images/eye-tracking/mrtk_et_build_settings.jpg)

### <a name="3-play-the-eye-tracking-samples-in-the-unity-editor"></a><span data-ttu-id="7d917-157">3. 在 Unity 編輯器中播放眼睛追蹤範例</span><span class="sxs-lookup"><span data-stu-id="7d917-157">3. Play the eye tracking samples in the Unity editor</span></span>

<span data-ttu-id="7d917-158">將眼睛追蹤場景新增至組建設定並載入 _EyeTrackingDemo-00-RootScene_ 之後，您可能會想要檢查的最後一件事：是否已啟用附加至 _MixedRealityBasicSceneSetup_ GameObject 的 _' OnLoadStartScene '_ 腳本？</span><span class="sxs-lookup"><span data-stu-id="7d917-158">After adding the eye tracking scenes to the Build Settings and loading the _EyeTrackingDemo-00-RootScene_, there is one last thing you may want to check: Is the _'OnLoadStartScene'_ script that is attached to the _MixedRealityBasicSceneSetup_ GameObject enabled?</span></span> <span data-ttu-id="7d917-159">這是為了讓根場景知道要先載入的示範場景。</span><span class="sxs-lookup"><span data-stu-id="7d917-159">This is to let the root scene know which demo scene to load first.</span></span>

![OnLoad_StartScene 腳本的範例](../images/eye-tracking/mrtk_et_onloadstartscene.jpg)

<span data-ttu-id="7d917-161">現在就開始吧！</span><span class="sxs-lookup"><span data-stu-id="7d917-161">Let's roll!</span></span> <span data-ttu-id="7d917-162">點擊「 _Play_」！</span><span class="sxs-lookup"><span data-stu-id="7d917-162">Hit _"Play"_!</span></span>
<span data-ttu-id="7d917-163">您應該會看到數個 gem，以及頂端的場景功能表。</span><span class="sxs-lookup"><span data-stu-id="7d917-163">You should see several gems appear and the scene menu at the top.</span></span>

![ET 目標選取場景的範例螢幕擷取畫面](../images/eye-tracking/mrtk_et_targetselect.png)

<span data-ttu-id="7d917-165">您也應該會在遊戲視圖的中央看到一個小型半透明圓圈。</span><span class="sxs-lookup"><span data-stu-id="7d917-165">You should also notice a small semitransparent circle at the center of your game view.</span></span>
<span data-ttu-id="7d917-166">這可做為 _模擬眼睛_ (游標) 的指標：只要按下滑鼠 _右鍵_ 並移動滑鼠，即可變更其位置。</span><span class="sxs-lookup"><span data-stu-id="7d917-166">This acts as an indicator (cursor) of your _simulated eye gaze_: Simply press down the _right mouse button_ and move the mouse to change its position.</span></span>
<span data-ttu-id="7d917-167">當游標停留在 gem 上方時，您會發現它會貼齊到目前所觀看 gem 的中央。</span><span class="sxs-lookup"><span data-stu-id="7d917-167">When the cursor is hovering over the gems, you will notice that it will snap to the center of the currently viewed gem.</span></span>
<span data-ttu-id="7d917-168">這是一個很好的方法，可以測試在目標上「 _尋找_ 」事件是否如預期般觸發。</span><span class="sxs-lookup"><span data-stu-id="7d917-168">This is a great way to test if events are triggered as expected when _"looking"_ at a target.</span></span>
<span data-ttu-id="7d917-169">請注意，透過滑鼠控制的 _模擬眼睛_ 是對我們的快速和意外眼睛的補充，相當不良。</span><span class="sxs-lookup"><span data-stu-id="7d917-169">Be aware that the _simulated eye gaze_ via mouse control is a rather poor supplement to our rapid and unintentional eye movements.</span></span>
<span data-ttu-id="7d917-170">不過，它很適合用來測試基本功能，然後再將其部署到 HoloLens 2 裝置上，然後再逐一查看設計。</span><span class="sxs-lookup"><span data-stu-id="7d917-170">However, it is great for testing the basic functionality before iterating on the design by deploying it to the HoloLens 2 device.</span></span>
<span data-ttu-id="7d917-171">回到我們的眼睛追蹤範例場景： gem 會旋轉一段時間，只要經過查看，並可在其上「查看」和 .。。</span><span class="sxs-lookup"><span data-stu-id="7d917-171">Returning to our eye tracking sample scene: The gem rotates as long as being looked at and can be destroyed by "looking" at it and ...</span></span>

- <span data-ttu-id="7d917-172">按 _enter_ (模擬說「select」 ) </span><span class="sxs-lookup"><span data-stu-id="7d917-172">Pressing _Enter_ (which simulates saying "select")</span></span>
- <span data-ttu-id="7d917-173">說「 _選取_ 」您的麥克風</span><span class="sxs-lookup"><span data-stu-id="7d917-173">Saying _"select"_ into your microphone</span></span>
- <span data-ttu-id="7d917-174">當按下 _空格鍵_ 顯示模擬的手輸入時，請按一下滑鼠左鍵來執行模擬的縮小</span><span class="sxs-lookup"><span data-stu-id="7d917-174">While pressing _Space_ to show the simulated hand input, click the left mouse button to perform a simulated pinch</span></span>

<span data-ttu-id="7d917-175">我們會更詳細地說明如何在 [**支援的目標選擇**](EyeTracking_TargetSelection.md) 教學課程中達成這些互動。</span><span class="sxs-lookup"><span data-stu-id="7d917-175">We describe in more detail how you can achieve these interactions in our [**Eye-Supported Target Selection**](EyeTracking_TargetSelection.md) tutorial.</span></span>

<span data-ttu-id="7d917-176">將游標移到場景的頂端功能表列時，您會發現目前的動態顯示專案會稍微反白顯示。</span><span class="sxs-lookup"><span data-stu-id="7d917-176">When moving the cursor up to the top menu bar in the scene, you will notice that the currently hovered item will highlight subtly.</span></span>
<span data-ttu-id="7d917-177">您可以使用上述其中一個描述的 commit 方法來選取目前反白顯示的專案 (例如，按 _enter_) 。</span><span class="sxs-lookup"><span data-stu-id="7d917-177">You can select the currently highlighted item by using one of the above described commit methods (e.g., pressing _Enter_).</span></span>
<span data-ttu-id="7d917-178">如此一來，您就可以在不同的眼睛追蹤範例場景之間切換。</span><span class="sxs-lookup"><span data-stu-id="7d917-178">This way you can switch between the different eye tracking sample scenes.</span></span>

### <a name="4-how-to-test-specific-sub-scenes"></a><span data-ttu-id="7d917-179">4. 如何測試特定的 sub 場景</span><span class="sxs-lookup"><span data-stu-id="7d917-179">4. How to test specific sub scenes</span></span>

<span data-ttu-id="7d917-180">在特定案例中，您可能不會想要每次都經過場景功能表。</span><span class="sxs-lookup"><span data-stu-id="7d917-180">When working on a specific scenario, you may not want to go through the scene menu every time.</span></span>
<span data-ttu-id="7d917-181">相反地，您可能會想要在按下 [ _播放_ ] 按鈕時，直接從您目前正在處理的場景中開始。</span><span class="sxs-lookup"><span data-stu-id="7d917-181">Instead, you may want to start directly from the scene that you are currently working on when pressing the _Play_ button.</span></span>
<span data-ttu-id="7d917-182">沒問題！</span><span class="sxs-lookup"><span data-stu-id="7d917-182">No problem!</span></span> <span data-ttu-id="7d917-183">以下是您可以執行的動作：</span><span class="sxs-lookup"><span data-stu-id="7d917-183">Here is what you can do:</span></span>

1. <span data-ttu-id="7d917-184">載入 _根_ 場景</span><span class="sxs-lookup"><span data-stu-id="7d917-184">Load the _root_ scene</span></span>
2. <span data-ttu-id="7d917-185">在 _根_ 場景中，停用 _' OnLoadStartScene '_ 腳本</span><span class="sxs-lookup"><span data-stu-id="7d917-185">In the _root_ scene, disable the _'OnLoadStartScene'_ script</span></span>
3. <span data-ttu-id="7d917-186">將下列 (或任何其他場景) 所述的眼睛追蹤測試場景 _拖放_ 到 _階層視圖中_，如下列螢幕擷取畫面所示。</span><span class="sxs-lookup"><span data-stu-id="7d917-186">_Drag and drop_ one of the eye tracking test scenes that are described below (or any other scene) into your _Hierarchy_ view as shown in the screenshot below.</span></span>

    ![加法場景範例](../images/eye-tracking/mrtk_et_additivescene.jpg)

4. <span data-ttu-id="7d917-188">按下 _播放_</span><span class="sxs-lookup"><span data-stu-id="7d917-188">Press _Play_</span></span>

<span data-ttu-id="7d917-189">請注意，載入這類的子場景並非持續性：這表示如果您將應用程式部署至 HoloLens 2 裝置，則只會載入根場景， (假設它出現在您的組建設定) 的上方。</span><span class="sxs-lookup"><span data-stu-id="7d917-189">Please note that loading the sub scene like this is not persistent: This means that if you deploy your app to the HoloLens 2 device, it will only load the root scene (assuming it appears at the top of your Build Settings).</span></span>
<span data-ttu-id="7d917-190">此外，當您與其他人共用您的專案時，不會自動載入子場景。</span><span class="sxs-lookup"><span data-stu-id="7d917-190">Also, when you share your project with others, the sub scenes are not automatically loaded.</span></span>

---

<span data-ttu-id="7d917-191">現在您已經知道如何讓 MRTK 眼追蹤範例幕後運作，接下來讓我們繼續深入探討如何使用眼睛來選取全像投影： [支援的目標選擇](EyeTracking_TargetSelection.md)。</span><span class="sxs-lookup"><span data-stu-id="7d917-191">Now that you know how to get the MRTK eye tracking example scenes to work, let's continue with diving deeper into how to select holograms with your eyes: [Eye-supported target selection](EyeTracking_TargetSelection.md).</span></span>

---
[<span data-ttu-id="7d917-192">回到「MixedRealityToolkit 中的眼睛追蹤」</span><span class="sxs-lookup"><span data-stu-id="7d917-192">Back to "Eye tracking in the MixedRealityToolkit"</span></span>](EyeTracking_Main.md)
