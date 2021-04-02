---
title: 開始使用電腦全像攝影遠端處理
description: 完成此課程，以了解如何從遠端將混合實境應用程式從電腦串流到 HoloLens 2。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens, 電腦全像攝影遠端處理, 工具提示, 眼球追蹤
ms.localizationpriority: high
ms.openlocfilehash: 3c564c28485ca7e0595b9fd438af961dc5bc5986
ms.sourcegitcommit: 4fb961beeebd158e2f65b7c714c5e471454400a3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/30/2021
ms.locfileid: "105982961"
---
# <a name="1-getting-started-with-pc-holographic-remoting"></a><span data-ttu-id="a0c40-104">1.開始使用電腦全像攝影遠端處理</span><span class="sxs-lookup"><span data-stu-id="a0c40-104">1. Getting started with PC Holographic Remoting</span></span>

<span data-ttu-id="a0c40-105">歡迎使用 HoloLens 2 教學課程。</span><span class="sxs-lookup"><span data-stu-id="a0c40-105">Welcome to the HoloLens 2 tutorials.</span></span> <span data-ttu-id="a0c40-106">在這個兩部分的教學課程系列中，您將了解如何建立混合實境體驗示範，以及如何建立適用於全像攝影遠端的電腦應用程式。</span><span class="sxs-lookup"><span data-stu-id="a0c40-106">In this two-part tutorial series, you will learn how to create a mixed reality experience demonstration and how to create a PC app for Holographic Remoting.</span></span>

<span data-ttu-id="a0c40-107">在本教學課程中，您將了解如何建立混合實境體驗。</span><span class="sxs-lookup"><span data-stu-id="a0c40-107">In this tutorial, you'll learn how to create a mixed reality experience.</span></span> <span data-ttu-id="a0c40-108">本教學課程將示範 UI 元素、3D 模型操作、模型裁剪，以及眼球追蹤功能。</span><span class="sxs-lookup"><span data-stu-id="a0c40-108">It will demonstrate UI elements, 3D model manipulation, model clipping, and eye-tracking features.</span></span>

<span data-ttu-id="a0c40-109">在第二個教學課程 ([建立全像攝影遠端處理應用程式](mr-learning-pc-holographic-remoting-02.md)) 中，您將了解如何建立適用於全像攝影遠端處理的電腦應用程式。</span><span class="sxs-lookup"><span data-stu-id="a0c40-109">In the second tutorial, [Create a Holographic Remoting application](mr-learning-pc-holographic-remoting-02.md), you will learn how to create a PC app for Holographic Remoting.</span></span> <span data-ttu-id="a0c40-110">並且隨時連線至 HoloLens 2，以提供在混合實境中視覺化 3D 內容的方法。</span><span class="sxs-lookup"><span data-stu-id="a0c40-110">And connect to HoloLens 2 at any point, providing a way to visualize 3D content in mixed reality.</span></span>

## <a name="objectives"></a><span data-ttu-id="a0c40-111">目標</span><span class="sxs-lookup"><span data-stu-id="a0c40-111">Objectives</span></span>

* <span data-ttu-id="a0c40-112">匯入資產並設定場景</span><span class="sxs-lookup"><span data-stu-id="a0c40-112">Import assets and set up the scene</span></span>
* <span data-ttu-id="a0c40-113">使用 UI 元素和按鈕來與全像投影互動</span><span class="sxs-lookup"><span data-stu-id="a0c40-113">Interact with holograms using UI elements and buttons</span></span>
* <span data-ttu-id="a0c40-114">設定 3D 物件的裁剪功能</span><span class="sxs-lookup"><span data-stu-id="a0c40-114">Configure 3D objects for the clipping feature</span></span>
* <span data-ttu-id="a0c40-115">了解眼球追蹤的啟用工具提示</span><span class="sxs-lookup"><span data-stu-id="a0c40-115">Learn about activating tooltips with eye-tracking</span></span>

## <a name="prerequisites"></a><span data-ttu-id="a0c40-116">必要條件</span><span class="sxs-lookup"><span data-stu-id="a0c40-116">Prerequisites</span></span>

* <span data-ttu-id="a0c40-117">已[安裝正確工具](../../install-the-tools.md)的 Windows 10 電腦</span><span class="sxs-lookup"><span data-stu-id="a0c40-117">A Windows 10 PC configured with the correct [tools installed](../../install-the-tools.md)</span></span>
* <span data-ttu-id="a0c40-118">基本 C# 程式設計知識</span><span class="sxs-lookup"><span data-stu-id="a0c40-118">Basic c# programming knowledge</span></span>
* <span data-ttu-id="a0c40-119">已[針對開發而設定](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)的 HoloLens 2 裝置</span><span class="sxs-lookup"><span data-stu-id="a0c40-119">A HoloLens 2 device [configured for development](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="a0c40-120"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a>，已掛接 Unity 2019 LTS，且已新增通用 Windows 平台組建支援模組</span><span class="sxs-lookup"><span data-stu-id="a0c40-120"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019 LTS mounted, and the Universal Windows Platform Build Support module added</span></span>

<span data-ttu-id="a0c40-121">**強烈建議** 先完成 [使用者入門](mr-learning-base-01.md)教學課程系列或一些基本的 Unity 和 MRTK 體驗，再繼續執行。</span><span class="sxs-lookup"><span data-stu-id="a0c40-121">We **strongly recommend** completing the [Getting started](mr-learning-base-01.md) tutorials series or some basic prior experience with Unity and MRTK before continuing.</span></span>

> [!IMPORTANT]
> * <span data-ttu-id="a0c40-122">本教學課程系列的建議 Unity 版本是 Unity 2019 LTS。</span><span class="sxs-lookup"><span data-stu-id="a0c40-122">The recommended Unity version for this tutorial series is Unity 2019 LTS.</span></span> <span data-ttu-id="a0c40-123">這個版本能取代上述連結必要條件中所述的任何 Unity 版本需求或建議。</span><span class="sxs-lookup"><span data-stu-id="a0c40-123">It supersedes any Unity version requirements or recommendations stated in the prerequisites linked above.</span></span>
> * <span data-ttu-id="a0c40-124">透過 MRTK 專案進行全像攝影遠端處理只會使用舊版 XR。</span><span class="sxs-lookup"><span data-stu-id="a0c40-124">Holographic Remoting with MRTK projects will only work with legacy XR.</span></span> <span data-ttu-id="a0c40-125">目前不支援 XR SDK。</span><span class="sxs-lookup"><span data-stu-id="a0c40-125">XR SDK is not supported at this time.</span></span>

## <a name="creating-and-preparing-the-unity-project"></a><span data-ttu-id="a0c40-126">建立和準備 Unity 專案</span><span class="sxs-lookup"><span data-stu-id="a0c40-126">Creating and preparing the Unity project</span></span>

<span data-ttu-id="a0c40-127">在本節中，您將建立新的 Unity 專案，並使該專案準備好進行 MRTK 開發。</span><span class="sxs-lookup"><span data-stu-id="a0c40-127">In this section, you will create a new Unity project and get it ready for MRTK development.</span></span>

<span data-ttu-id="a0c40-128">為此，請先遵循[初始化您的專案和第一個應用程式](mr-learning-base-02.md) (但不包括[對您的裝置建置應用程式](mr-learning-base-02.md#building-your-application-to-your-hololens-2)的指示)，其中包括下列步驟：</span><span class="sxs-lookup"><span data-stu-id="a0c40-128">For this, first follow the [Initializing your project and first application](mr-learning-base-02.md), excluding the [Build your application to your device](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions, which includes the following steps:</span></span>

1. <span data-ttu-id="a0c40-129">[建立 Unity 專案](mr-learning-base-02.md#creating-the-unity-project)，並為其提供適當的名稱，例如「MRTK 教學課程」</span><span class="sxs-lookup"><span data-stu-id="a0c40-129">[Creating the Unity project](mr-learning-base-02.md#creating-the-unity-project) and give it a suitable name, for example, *MRTK Tutorials*</span></span>

2. [<span data-ttu-id="a0c40-130">切換建置平台</span><span class="sxs-lookup"><span data-stu-id="a0c40-130">Switching the build platform</span></span>](mr-learning-base-02.md#switching-the-build-platform)

3. [<span data-ttu-id="a0c40-131">匯入 TextMeshPro 基本資源</span><span class="sxs-lookup"><span data-stu-id="a0c40-131">Importing the TextMeshPro Essential Resources</span></span>](mr-learning-base-02.md#importing-the-textmeshpro-essential-resources)

4. [<span data-ttu-id="a0c40-132">匯入混合實境工具組</span><span class="sxs-lookup"><span data-stu-id="a0c40-132">Importing the Mixed Reality Toolkit</span></span>](mr-learning-base-02.md#importing-the-mixed-reality-toolkit)

5. [<span data-ttu-id="a0c40-133">設定 Unity 專案</span><span class="sxs-lookup"><span data-stu-id="a0c40-133">Configuring the Unity project</span></span>](mr-learning-base-02.md#configuring-the-unity-project)

6. <span data-ttu-id="a0c40-134">[建立和設定場景](mr-learning-base-02.md#creating-and-configuring-the-scene)並為場景提供適當的名稱，例如「電腦全像攝影遠端處理」</span><span class="sxs-lookup"><span data-stu-id="a0c40-134">[Creating and setting the scene](mr-learning-base-02.md#creating-and-configuring-the-scene) and give the scene a suitable name, for example, **PC Holographic Remoting**</span></span>

<span data-ttu-id="a0c40-135">然後遵循 [變更空間感知顯示選項](mr-learning-base-03.md#changing-the-spatial-awareness-display-option)指示，將場景的 MRTK 設定檔變更為 **DefaultHoloLens2ConfigurationProfile**。</span><span class="sxs-lookup"><span data-stu-id="a0c40-135">Then follow the [Changing the Spatial Awareness Display Option](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) instructions to change the MRTK configuration profile for your scene to the **DefaultHoloLens2ConfigurationProfile**.</span></span> <span data-ttu-id="a0c40-136">將空間感知網格的顯示選項變更為 **遮蔽**。</span><span class="sxs-lookup"><span data-stu-id="a0c40-136">Change the display options for the spatial awareness mesh to **Occlusion**.</span></span>

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="a0c40-137">匯入教學課程資產</span><span class="sxs-lookup"><span data-stu-id="a0c40-137">Importing the tutorial assets</span></span>

<span data-ttu-id="a0c40-138">下載並 **匯入** [MRTK.Tutorials.PCHolographicRemoting.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/pc-holographic-remoting-v2.4.0/MRTK.Tutorials.PCHolographicRemoting.unitypackage)。</span><span class="sxs-lookup"><span data-stu-id="a0c40-138">Download and **import** the [MRTK.Tutorials.PCHolographicRemoting.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/pc-holographic-remoting-v2.4.0/MRTK.Tutorials.PCHolographicRemoting.unitypackage).</span></span>

>[!TIP]
> <span data-ttu-id="a0c40-139">如需有關如何匯入 Unity 自訂套件的提醒，您可以參考匯 [入教學課程資產](mr-learning-base-02.md#importing-the-tutorial-assets) 的指示。</span><span class="sxs-lookup"><span data-stu-id="a0c40-139">For a reminder on how to import a Unity custom package, you can refer to the [Importing the tutorial assets](mr-learning-base-02.md#importing-the-tutorial-assets) instructions.</span></span>

<span data-ttu-id="a0c40-140">匯入教學課程資產之後，您的 [專案] 視窗看起來應該會像這樣：</span><span class="sxs-lookup"><span data-stu-id="a0c40-140">After importing the tutorial assets, your Project window should look similar to this:</span></span>

![匯入教學課程資產後的 Unity 階層、場景和專案視窗](images/mrlearning-pc-holographic-remoting/Tutorial1-Section2-Step1-1.png)

## <a name="configuring-and-preparing-the-scene"></a><span data-ttu-id="a0c40-142">設定和準備場景</span><span class="sxs-lookup"><span data-stu-id="a0c40-142">Configuring and preparing the scene</span></span>

<span data-ttu-id="a0c40-143">在本節中，您將藉由新增一些教學課程 Prefab 來準備場景。</span><span class="sxs-lookup"><span data-stu-id="a0c40-143">In this section, you will prepare the scene by adding some of the tutorial prefabs.</span></span>

<span data-ttu-id="a0c40-144">在 [專案] 視窗中，瀏覽至 [資產] > [MRTK.Tutorials.PCHolograhicRemoting] > [Prefabs] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="a0c40-144">In the Project window, navigate to **Assets** > **MRTK.Tutorials.PCHolograhicRemoting** > **Prefabs** folder.</span></span> <span data-ttu-id="a0c40-145">按住 CTRL 鍵時，按一下下列六個 prefabs。</span><span class="sxs-lookup"><span data-stu-id="a0c40-145">While holding down the CTRL button, click on the below six prefabs.</span></span>

* <span data-ttu-id="a0c40-146">ButtonParent</span><span class="sxs-lookup"><span data-stu-id="a0c40-146">ButtonParent</span></span>
* <span data-ttu-id="a0c40-147">ClippingObjects</span><span class="sxs-lookup"><span data-stu-id="a0c40-147">ClippingObjects</span></span>
* <span data-ttu-id="a0c40-148">HandSpatialMapButton</span><span class="sxs-lookup"><span data-stu-id="a0c40-148">HandSpatialMapButton</span></span>
* <span data-ttu-id="a0c40-149">指示</span><span class="sxs-lookup"><span data-stu-id="a0c40-149">Instructions</span></span>
* <span data-ttu-id="a0c40-150">ModelParent</span><span class="sxs-lookup"><span data-stu-id="a0c40-150">ModelParent</span></span>
* <span data-ttu-id="a0c40-151">平台</span><span class="sxs-lookup"><span data-stu-id="a0c40-151">Platform</span></span>

![Unity，已選取要新增至場景的 Prefabs](images/mrlearning-pc-holographic-remoting/Tutorial1-Section3-Step1-1.png)

<span data-ttu-id="a0c40-153">將這些模型從 [Prefabs] 資料夾拖放到 [階層] 視窗中。</span><span class="sxs-lookup"><span data-stu-id="a0c40-153">Drag-and-drop these models from the prefabs folder into the **Hierarchy window**.</span></span>

![新增的 Prefabs 仍保持選取狀態的 Unity](images/mrlearning-pc-holographic-remoting/Tutorial1-Section3-Step1-2.png)

<span data-ttu-id="a0c40-155">若要將焦點放在場景中的物件上，您可以按兩下 **ModelParent** 物件，然後再次將場景稍微縮小：</span><span class="sxs-lookup"><span data-stu-id="a0c40-155">To focus in on the objects in the scene, you can double-click on the **ModelParent** object, and then zoom slightly in again:</span></span>

![焦點位於 ModelParent 物件的 Unity](images/mrlearning-pc-holographic-remoting/Tutorial1-Section3-Step1-3.png)

> [!TIP]
> <span data-ttu-id="a0c40-157">如果您發現場景中的大圖示 (例如大型邊框的 'T' 圖示) 會造成干擾，您可以藉由<a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">切換 Gizmo</a> 到關閉位置來將其隱藏。</span><span class="sxs-lookup"><span data-stu-id="a0c40-157">If you find the large icons in your scene, such as, the large framed 'T' icons distracting, you can hide these by <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">toggling the Gizmos</a> to the off position.</span></span>

## <a name="configuring-the-buttons-to-operate-the-scene"></a><span data-ttu-id="a0c40-158">設定按鈕以操作場景</span><span class="sxs-lookup"><span data-stu-id="a0c40-158">Configuring the buttons to operate the scene</span></span>

<span data-ttu-id="a0c40-159">在本節中，您會將指令碼新增至場景中，以建立會示範模型切換和裁剪功能基本概念的按鈕事件。</span><span class="sxs-lookup"><span data-stu-id="a0c40-159">In this section, you will add scripts into the scene to create button events demonstrating the fundamentals of model switching and clipping functionality.</span></span>

### <a name="1-configuring-the-interactable-script-component"></a><span data-ttu-id="a0c40-160">1.設定 Interactable (指令碼) 元件</span><span class="sxs-lookup"><span data-stu-id="a0c40-160">1. Configuring the Interactable (Script) component</span></span>

<span data-ttu-id="a0c40-161">在 [階層] 視窗中，展開 **ButtonParent** 物件，然後選取 **NextButton**。</span><span class="sxs-lookup"><span data-stu-id="a0c40-161">In the Hierarchy window, expand the **ButtonParent** object and select the **NextButton**.</span></span> <span data-ttu-id="a0c40-162">在 [偵測器] 視窗中，找出 **Interactable (指令碼)** 元件，然後按一下 **OnClick ()+ 事件底下的**  圖示。</span><span class="sxs-lookup"><span data-stu-id="a0c40-162">In the Inspector window, locate the **Interactable (Script)** component and click on **+** icon under **OnClick ()** event.</span></span>

![已新增 NextButton OnClick 事件的 Unity](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step1-1.png)

<span data-ttu-id="a0c40-164">在 [階層] 視窗中保持選取 **NextButton** 物件，按一下 **ButtonParent** 物件並將其從 [階層] 視窗拖曳至您剛才所新增事件的空白 [無 (物件)] 欄位，讓 ButtonParent 物件可以從此按鈕接聽按下按鈕的事件：</span><span class="sxs-lookup"><span data-stu-id="a0c40-164">With the **NextButton** object still selected in the Hierarchy window, click-and-drag the **ButtonParent** object from the Hierarchy window into the empty **None (Object)** field of the event you just added to make the ButtonParent object listen for button click event from this button:</span></span>

![已設定 NextButton OnClick 事件接聽程式的 Unity](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step1-2.png)

<span data-ttu-id="a0c40-166">按一下相同事件的 [沒有函式] 下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="a0c40-166">Click the **No Function** dropdown of the same event.</span></span> <span data-ttu-id="a0c40-167">然後選取 [ViewButtonControl]  >  [NextModel ()]，將 [NextModel ()] 函式設定為從這個按鈕引發按下按鈕事件時所觸發的動作：</span><span class="sxs-lookup"><span data-stu-id="a0c40-167">Then select **ViewButtonControl** > **NextModel ()** to set the **NextModel ()** function as the action that is triggered when the button pressed events is fired from this button:</span></span>

![具有 NextButton OnClick 事件動作選取路徑的 Unity](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step1-3.png)

### <a name="2-configuring-the-remaining-buttons"></a><span data-ttu-id="a0c40-169">2.設定其餘按鈕</span><span class="sxs-lookup"><span data-stu-id="a0c40-169">2. Configuring the remaining buttons</span></span>

<span data-ttu-id="a0c40-170">針對其餘的每個按鈕，完成上述程序，將函式指派給 **OnClick ()** 事件：</span><span class="sxs-lookup"><span data-stu-id="a0c40-170">For each of the remaining buttons, complete the process outlined above to assign functions to the **OnClick ()** events:</span></span>

* <span data-ttu-id="a0c40-171">針對 PreviousButton 物件，指派 **ViewButtonContro** l > **PreviousModel ()** 函式。</span><span class="sxs-lookup"><span data-stu-id="a0c40-171">For PreviousButton object, assign the **ViewButtonContro** l > **PreviousModel ()** function.</span></span>

* <span data-ttu-id="a0c40-172">針對 ClippingButton，選取 **ToggleButton**  >  **ToggleClipping ()** 函式。</span><span class="sxs-lookup"><span data-stu-id="a0c40-172">For ClippingButton select **ToggleButton** > **ToggleClipping ()** function.</span></span>

### <a name="3-configuring-the-view-button-control-script--and-toggle-button-script-components"></a><span data-ttu-id="a0c40-173">3.設定 View Button Control (指令碼) 和 Toggle Button (指令碼) 元件</span><span class="sxs-lookup"><span data-stu-id="a0c40-173">3. Configuring the View Button Control (Script)  and Toggle Button (Script) components</span></span>

<span data-ttu-id="a0c40-174">現在您的按鈕已設定為示範模型切換和裁剪功能。</span><span class="sxs-lookup"><span data-stu-id="a0c40-174">Now your buttons are configured to demonstrate the model switching and clipping functionality.</span></span> <span data-ttu-id="a0c40-175">現在可以將 3D 模型和裁剪物件新增至指令碼。</span><span class="sxs-lookup"><span data-stu-id="a0c40-175">It is time to add 3D models and the clipping objects to the script.</span></span>

<span data-ttu-id="a0c40-176">我們提供六種不同的 3D 模型作為示範，請展開 ***ModelParentobject*** 以公開這些 3D 模型。</span><span class="sxs-lookup"><span data-stu-id="a0c40-176">We have provided six different 3D models for demonstration, expand the ***ModelParentobject*** to expose these 3D models.</span></span>

<span data-ttu-id="a0c40-177">在 [階層] 視窗中保持選取 ButtonParent 物件，在 [偵測器] 視窗中，找出 **View Button Control (指令碼)** 元件，然後展開 **Models** 變數。</span><span class="sxs-lookup"><span data-stu-id="a0c40-177">With the ButtonParent object still selected in the Hierarchy window, in the Inspector window, locate the **View Button Control (Script)** component and expand the **Models** variable.</span></span>

<span data-ttu-id="a0c40-178">在 [大小] 欄位中，輸入您想要在場景中擁有的 3D 模型數目。</span><span class="sxs-lookup"><span data-stu-id="a0c40-178">In the **Size** field, enter the number of 3D models you would like to have in your scene.</span></span> <span data-ttu-id="a0c40-179">在此案例中，此值會是 6。</span><span class="sxs-lookup"><span data-stu-id="a0c40-179">In this case, it would be six.</span></span> <span data-ttu-id="a0c40-180">會建立欄位以新增新的 3D 模型。</span><span class="sxs-lookup"><span data-stu-id="a0c40-180">It will create fields for adding new 3D models.</span></span>

![具有 ViewButtonControl 指令碼元件欄位的 Unity](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step3-1.png)

<span data-ttu-id="a0c40-182">將 ModelParent 物件的每個子物件拖放到這些欄位。</span><span class="sxs-lookup"><span data-stu-id="a0c40-182">Drag and drop each child object of ModelParent Object into these fields.</span></span>

![已設定 ViewButtonControl 指令碼元件欄位的 Unity](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step3-2.png)

<span data-ttu-id="a0c40-184">從 [階層] 視窗中，將 **ClippingObjects** 物件拖放至 **Toggle Button (指令碼)** 元件的 [裁剪物件] 欄位。</span><span class="sxs-lookup"><span data-stu-id="a0c40-184">Drag and drop the  **ClippingObjects** object from the Hierarchy window to the  **Toggle Button (Script)** component **Clipping Object** field.</span></span>
>[!NOTE]
><span data-ttu-id="a0c40-185">只停留在按鈕父物件。</span><span class="sxs-lookup"><span data-stu-id="a0c40-185">Stay in button parent object only.</span></span>

![已設定 ToggleButton 指令碼元件欄位的 Unity](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step3-3.png)

<span data-ttu-id="a0c40-187">在 [階層] 視窗中，選取 [ClippingObjects] prefab，並在 [偵測器] 視窗中啟用以開啟裁剪物件。</span><span class="sxs-lookup"><span data-stu-id="a0c40-187">In the Hierarchy window, select the **ClippingObjects** prefab and enable it in the Inspector window to turn on the Clipping objects.</span></span>

## <a name="configuring-the-clipping-objects-to-enable-clipping-feature"></a><span data-ttu-id="a0c40-188">設定裁剪物件以啟用裁剪功能</span><span class="sxs-lookup"><span data-stu-id="a0c40-188">Configuring the clipping objects to enable clipping feature</span></span>

<span data-ttu-id="a0c40-189">在本節中，您會將 MarsCuriosityRover 物件的子物件轉譯器新增至個別的裁剪物件，以示範 MarsCuriosityRover 模型的裁剪。</span><span class="sxs-lookup"><span data-stu-id="a0c40-189">In this section, you will add MarsCuriosityRover object's child objects renderer into an individual clipping object to demonstrate the clipping of the MarsCuriosityRover model.</span></span>

<span data-ttu-id="a0c40-190">在 [階層] 視窗中，展開 **ClippingObjects** 物件，以公開您將在此專案中使用的三個不同裁剪物件。</span><span class="sxs-lookup"><span data-stu-id="a0c40-190">In the Hierarchy window, expand the **ClippingObjects** object to expose the three different clipping objects that you will be using in this project.</span></span>

<span data-ttu-id="a0c40-191">若要設定 **ClippingSphere** 物件，請按一下該物件，然後在 [偵測器] 視窗中，找出 **Clipping Sphere (指令碼)** 元件。</span><span class="sxs-lookup"><span data-stu-id="a0c40-191">To configure the **ClippingSphere** object, click on it, and in the Inspector window, locate the **Clipping Sphere (Script)** component.</span></span> <span data-ttu-id="a0c40-192">在 [大小] 欄位中輸入您需要為 3D 模型新增的轉譯器數目。</span><span class="sxs-lookup"><span data-stu-id="a0c40-192">Enter the number of renderers in the size field that you need to add for your 3D model.</span></span> <span data-ttu-id="a0c40-193">在此案例中，請為 MarsCuriosityRover 子物件新增 10 個。</span><span class="sxs-lookup"><span data-stu-id="a0c40-193">In this case, add 10 for MarsCuriosityRover child objects.</span></span> <span data-ttu-id="a0c40-194">會建立欄位以新增轉譯器，並將 MarsCuriosityRover 物件的子模型物件拖放到這些欄位。</span><span class="sxs-lookup"><span data-stu-id="a0c40-194">It will create fields for adding renderers, drag and drop MarsCuriosityRover Object's child model objects into these fields.</span></span>

![已設定 ClippingSphere 指令碼元件欄位的 Unity](images/mrlearning-pc-holographic-remoting/Tutorial1-Section5-Step1-1.png)

<span data-ttu-id="a0c40-196">遵循相同的程序，並將 MarsCuriosityRover 的子物件轉譯器新增至 **ClippingBox** 和 **ClippingPlane** 物件。</span><span class="sxs-lookup"><span data-stu-id="a0c40-196">Follow the same process and add MarsCuriosityRover's child objects renderers to the **ClippingBox** and **ClippingPlane** objects.</span></span>

<span data-ttu-id="a0c40-197">在本教學課程中，只會使用 MarsCuriosityRover 模型來示範裁剪功能。</span><span class="sxs-lookup"><span data-stu-id="a0c40-197">In this tutorial, only the MarsCuriosityRover model will be used for demonstrating the clipping feature.</span></span> <span data-ttu-id="a0c40-198">這些模型會將裁剪功能新增至更多模型、增加轉譯器的大小，以及新增其個別的網格轉譯器。</span><span class="sxs-lookup"><span data-stu-id="a0c40-198">They were adding clipping features to more models, increasing the size of the renderer, and adding their individual mesh renderers.</span></span>

## <a name="configuring-eye-tracking-to-highlight-tooltips"></a><span data-ttu-id="a0c40-199">設定眼球追蹤以醒目提示工具提示</span><span class="sxs-lookup"><span data-stu-id="a0c40-199">Configuring eye-tracking to highlight tooltips</span></span>

<span data-ttu-id="a0c40-200">在本節中，您將探索如何在專案中啟用眼球追蹤。</span><span class="sxs-lookup"><span data-stu-id="a0c40-200">In this section, you will explore how to enable eye tracking in your project.</span></span> <span data-ttu-id="a0c40-201">例如，您將會實作功能以在查看 MarsCuriosityRover 組件時醒目提示附加至其中的工具提示，並且在您移開視線時將其隱藏。</span><span class="sxs-lookup"><span data-stu-id="a0c40-201">For example, you will implement the functionality to highlight tooltips attached to MarsCuriosityRover's parts while looking at them and hiding them, while you are looking away from them.</span></span>

### <a name="1-identify-target-objects-and-associated-tooltips"></a><span data-ttu-id="a0c40-202">1.識別目標物件和相關聯的工具提示</span><span class="sxs-lookup"><span data-stu-id="a0c40-202">1. Identify target objects and associated tooltips</span></span>

<span data-ttu-id="a0c40-203">在 [階層] 視窗中，選取 [ModelParent] 物件。</span><span class="sxs-lookup"><span data-stu-id="a0c40-203">In the Hierarchy window, select the ModelParent object.</span></span> <span data-ttu-id="a0c40-204">展開 \***MarsCuriosity-> Rover** _ 以找出 MarsCuriosityRover 的五個主要部分： _ \* POI-攝影機 \* \*、 **POI-輪子**、 **POI-Antena**、 **POI-Spectrometer**、 **POI-RUHF 天線**。</span><span class="sxs-lookup"><span data-stu-id="a0c40-204">Expand the ***MarsCuriosity -> Rover** _ to find five main parts of the MarsCuriosityRover: _*POI-Camera\*\*, **POI-Wheels**, **POI-Antena**, **POI-Spectrometer**, **POI-RUHF Antenna**.</span></span>

* <span data-ttu-id="a0c40-205">觀察與 [階層] 視窗中 MarsCuriosityRover 組件相關聯的五個對應工具提示物件。</span><span class="sxs-lookup"><span data-stu-id="a0c40-205">Observe five corresponding tooltip objects associated with MarsCuriosityRover parts in the Hierarchy window.</span></span>
* <span data-ttu-id="a0c40-206">當您查看 MarsCuriosityRover 組件時，將會設定這些物件以醒目提示體驗。</span><span class="sxs-lookup"><span data-stu-id="a0c40-206">You will be configuring these objects to highlight the experience when you look at the MarsCuriosityRover parts.</span></span>

![已選取並展開 Rover 物件的 Unity](images/mrlearning-pc-holographic-remoting/Tutorial1-Section6-Step1-1.png)

### <a name="2-implement-while-looking-at-target-----on-look-away--events"></a><span data-ttu-id="a0c40-208">2.在發生 Looking At Target () 和 On Look Away () 事件時實作</span><span class="sxs-lookup"><span data-stu-id="a0c40-208">2. Implement While Looking At Target ()  &  On Look Away () events</span></span>

<span data-ttu-id="a0c40-209">在 [階層] 視窗中，選取 [POI-Camera] 物件。</span><span class="sxs-lookup"><span data-stu-id="a0c40-209">In the Hierarchy window, select the \***POI-Camera** _ object.</span></span> <span data-ttu-id="a0c40-210">在 [偵測器] 視窗中，找出 *Eye Tracking Target (指令碼)* 元件，並且設定 **While Looking At Target ()** 和 **On Look Away ()** 事件，如下所示：</span><span class="sxs-lookup"><span data-stu-id="a0c40-210">In the Inspector window, locate the _ *Eye Tracking Target (Script)*\* component and configure the **While Looking At Target ()** & **On Look Away ()** events as follows:</span></span>

* <span data-ttu-id="a0c40-211">對 [無 (物件)] 欄位，指派 **POI-Camera ToolTip** 物件</span><span class="sxs-lookup"><span data-stu-id="a0c40-211">To **None (Object)** field, assign the **POI-Camera ToolTip** object</span></span>
* <span data-ttu-id="a0c40-212">從 **While Looking At Target ()** 事件的 [沒有函式] 下拉式清單中，選取 [GameObject]  >  [SetActive (bool)]。</span><span class="sxs-lookup"><span data-stu-id="a0c40-212">From **No Function** dropdown of **While Looking At Target ()** event, select **GameObject** > **SetActive (bool).**</span></span> <span data-ttu-id="a0c40-213">選取其底下的 **核取方塊**，將工具提示醒目提示為當您查看目標物件時所觸發的動作。</span><span class="sxs-lookup"><span data-stu-id="a0c40-213">Select the **Checkbox** under it to highlight the tooltip as the action that is triggered when you look at the target object.</span></span>

![正在進行 EyeTrackingTarget WhileLookingAtTarget 事件設定的 Unity](images/mrlearning-pc-holographic-remoting/Tutorial1-Section6-Step2-1.png)

* <span data-ttu-id="a0c40-215">遵循相同的程序，然後按一下 **On Look Away ()** 事件接聽程式的 [沒有函式] 下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="a0c40-215">Follow the same process and click on the **No Function** dropdown of the **On Look Away ()** event listener.</span></span> <span data-ttu-id="a0c40-216">然後選取 [GameObject]  >  [SetActive (bool)]，並將 [核取方塊] 保留空白以隱藏工具提示，作為當您將視線移開目標物件時所觸發的動作。</span><span class="sxs-lookup"><span data-stu-id="a0c40-216">Then select **GameObject** > **SetActive (bool**) and leave the **Checkbox** empty to hide the tooltip as the action that is triggered when you look away from the target object.</span></span>

![已設定 EyeTrackingTarget OnLookAway 事件的 Unity](images/mrlearning-pc-holographic-remoting/Tutorial1-Section6-Step2-2.png)

<span data-ttu-id="a0c40-218">遵循相同的程序，並且將個別的工具提示物件指派給其相同的 **MarsCuriosityRover** 組件 **While Looking At Target ()** 和 **On Look Away ()** 事件。</span><span class="sxs-lookup"><span data-stu-id="a0c40-218">Follow the same process and assign respective tooltip objects to their same **MarsCuriosityRover** parts **While Looking At Target ()** & **On Look Away ()** events.</span></span>

<span data-ttu-id="a0c40-219">若要啟用眼球追蹤，請遵循這些[指導方針](/windows/mixed-reality/mrlearning-base-ch5#5-enable-simulated-eye-tracking-for-in-editor-simulations)。</span><span class="sxs-lookup"><span data-stu-id="a0c40-219">To enable eye tracking, please follow these [guidelines](/windows/mixed-reality/mrlearning-base-ch5#5-enable-simulated-eye-tracking-for-in-editor-simulations).</span></span>

## <a name="congratulations"></a><span data-ttu-id="a0c40-220">恭喜！</span><span class="sxs-lookup"><span data-stu-id="a0c40-220">Congratulations</span></span>

<span data-ttu-id="a0c40-221">在本教學課程中，您已了解如何建立混合實境體驗，以示範 UI 元素、3D 模型操作、模型裁剪和眼球追蹤功能。</span><span class="sxs-lookup"><span data-stu-id="a0c40-221">In this tutorial, you learned to build a mixed reality experience demonstrating UI elements, 3D model manipulation, model clipping, and eye-tracking features.</span></span> <span data-ttu-id="a0c40-222">本教學課程提供您 NextButton 和 PreviousButton，可讓您探索 3D 模型檢視器體驗。</span><span class="sxs-lookup"><span data-stu-id="a0c40-222">The tutorial provided you with NextButton and PreviousButton that let you explore the 3D model viewer experience.</span></span> <span data-ttu-id="a0c40-223">ClippingObjectButton 讓您開啟裁剪物件和體驗裁剪功能。</span><span class="sxs-lookup"><span data-stu-id="a0c40-223">The ClippingObjectButton made you turn on clipping objects and experience clipping feature.</span></span> <span data-ttu-id="a0c40-224">本教學課程也提供您一個眼球追蹤元素，讓您在體驗中醒目提示工具提示。</span><span class="sxs-lookup"><span data-stu-id="a0c40-224">The tutorial also provided you with an eye-tracking element to enable highlighting the tooltips in the experience.</span></span>

<span data-ttu-id="a0c40-225">在下一課中，您將學習如何為電腦建立全像攝影遠端處理應用程式，以在任何時間點連線 HoloLens 2，提供一種在混合實境中將 3D 內容視覺化的方式。</span><span class="sxs-lookup"><span data-stu-id="a0c40-225">In the next lesson, you will learn how to create a Holographic Remoting application for PC to connect HoloLens 2 at any point, providing a way to Visualize 3D content in mixed reality.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="a0c40-226">下一課：2.建立全像攝影遠端處理應用程式</span><span class="sxs-lookup"><span data-stu-id="a0c40-226">Next Lesson: 2. Create Holographic Remoting application</span></span>](mr-learning-pc-holographic-remoting-02.md)