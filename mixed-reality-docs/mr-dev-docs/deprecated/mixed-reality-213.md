---
title: MR Input 213
description: 遵循此編碼教學課程，使用 Unity、Visual Studio 和沉浸式耳機來瞭解運動控制器的詳細資料。
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit、mixedrealitytoolkit、mixedrealitytoolkit-unity、沉浸式、移動控制器、學院、教學課程
ms.openlocfilehash: 1f747c73846f59fdc62a0559068123a50f8a1b07
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583054"
---
# <a name="mr-input-213-motion-controllers"></a><span data-ttu-id="de425-104">MR Input 213：運動控制器</span><span class="sxs-lookup"><span data-stu-id="de425-104">MR Input 213: Motion controllers</span></span>

>[!NOTE]
><span data-ttu-id="de425-105">混合實境學院教學課程的設計是以 HoloLens (第 1 代) 和混合實境沉浸式頭戴裝置為準。</span><span class="sxs-lookup"><span data-stu-id="de425-105">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="de425-106">因此，對於仍在尋找這些裝置開發指引的開發人員而言，我們覺得這些教學課程很重要。</span><span class="sxs-lookup"><span data-stu-id="de425-106">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="de425-107">這些教學課程 **_不會_** 使用用於 HoloLens 2 的最新工具組或互動進行更新。</span><span class="sxs-lookup"><span data-stu-id="de425-107">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="de425-108">系統會保留這些資訊，以繼續在支援的裝置上運作。</span><span class="sxs-lookup"><span data-stu-id="de425-108">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="de425-109">已針對 HoloLens 2 公佈[一系列新的教學課程](../develop/unity/tutorials/mr-learning-base-01.md)。</span><span class="sxs-lookup"><span data-stu-id="de425-109">[A new series of tutorials](../develop/unity/tutorials/mr-learning-base-01.md) has been posted for HoloLens 2.</span></span>

<span data-ttu-id="de425-110">混合現實世界中的運動控制器會新增另一個層級的互動。</span><span class="sxs-lookup"><span data-stu-id="de425-110">Motion controllers in the mixed reality world add another level of interactivity.</span></span> <span data-ttu-id="de425-111">有了 [運動控制器](../design/motion-controllers.md)，我們就能以更自然的方式直接與物件互動，類似于真實生活中的實際互動，在您的應用程式體驗中增加深度和取悅。</span><span class="sxs-lookup"><span data-stu-id="de425-111">With [motion controllers](../design/motion-controllers.md), we can directly interact with objects in a more natural way, similar to our physical interactions in real life, increasing immersion and delight in your app experience.</span></span>

<span data-ttu-id="de425-112">在 MR 輸入213中，我們會藉由建立簡單的空間繪製體驗來探索移動控制器的輸入事件。</span><span class="sxs-lookup"><span data-stu-id="de425-112">In MR Input 213, we will explore the motion controller's input events by creating a simple spatial painting experience.</span></span> <span data-ttu-id="de425-113">使用此應用程式，使用者可以使用各種類型的筆刷和色彩，在三維空間中進行繪製。</span><span class="sxs-lookup"><span data-stu-id="de425-113">With this app, users can paint in three-dimensional space with various types of brushes and colors.</span></span>

## <a name="topics-covered-in-this-tutorial"></a><span data-ttu-id="de425-114">本教學課程中涵蓋的主題</span><span class="sxs-lookup"><span data-stu-id="de425-114">Topics covered in this tutorial</span></span>

|![MixedReality213 Topic1](images/mr213-topic1.png)|![MixedReality213 Topic2](images/mr213-topic2.png)|![MixedReality213 Topic3](images/mr213-topic3.png)|
| :--- | :--- | :--- |
|<span data-ttu-id="de425-118">**控制器視覺效果**</span><span class="sxs-lookup"><span data-stu-id="de425-118">**Controller visualization**</span></span>|<span data-ttu-id="de425-119">**控制器輸入事件**</span><span class="sxs-lookup"><span data-stu-id="de425-119">**Controller input events**</span></span>|<span data-ttu-id="de425-120">**自訂控制器和 UI**</span><span class="sxs-lookup"><span data-stu-id="de425-120">**Custom controller and UI**</span></span>|
|<span data-ttu-id="de425-121">瞭解如何在 Unity 的遊戲模式和執行時間中呈現移動控制器模型。</span><span class="sxs-lookup"><span data-stu-id="de425-121">Learn how to render motion controller models in Unity's game mode and runtime.</span></span>|<span data-ttu-id="de425-122">瞭解不同類型的按鈕事件和其應用程式。</span><span class="sxs-lookup"><span data-stu-id="de425-122">Understand different types of button events and their applications.</span></span>|<span data-ttu-id="de425-123">瞭解如何將 UI 元素重迭在控制器上，或完全自訂。</span><span class="sxs-lookup"><span data-stu-id="de425-123">Learn how to overlay UI elements on top of the controller or fully customize it.</span></span>|

## <a name="device-support"></a><span data-ttu-id="de425-124">裝置支援</span><span class="sxs-lookup"><span data-stu-id="de425-124">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="de425-125">課程</span><span class="sxs-lookup"><span data-stu-id="de425-125">Course</span></span></th><th style="width:150px"> <span data-ttu-id="de425-126"><a href="/hololens/hololens1-hardware">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="de425-126"><a href="/hololens/hololens1-hardware">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="de425-127"><a href="../discover/immersive-headset-hardware-details.md">沉浸式頭戴裝置</a></span><span class="sxs-lookup"><span data-stu-id="de425-127"><a href="../discover/immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="de425-128">MR Input 213：運動控制器</span><span class="sxs-lookup"><span data-stu-id="de425-128">MR Input 213: Motion controllers</span></span></td><td style="text-align: center;"> </td><td style="text-align: center;"> <span data-ttu-id="de425-129">✔️</span><span class="sxs-lookup"><span data-stu-id="de425-129">✔️</span></span></td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="de425-130">在您開始使用 Intune 之前</span><span class="sxs-lookup"><span data-stu-id="de425-130">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="de425-131">必要條件</span><span class="sxs-lookup"><span data-stu-id="de425-131">Prerequisites</span></span>

<span data-ttu-id="de425-132">請參閱 [此頁面](../develop/install-the-tools.md)上的沉浸式耳機安裝檢查清單。</span><span class="sxs-lookup"><span data-stu-id="de425-132">See the installation checklist for immersive headsets on [this page](../develop/install-the-tools.md).</span></span>

* <span data-ttu-id="de425-133">本教學課程需要 [Unity 2017.2.1 p2](https://beta.unity3d.com/download/1dc514532f08/UnityDownloadAssistant-2017.2.1p2.exe)</span><span class="sxs-lookup"><span data-stu-id="de425-133">This tutorial requires [Unity 2017.2.1p2](https://beta.unity3d.com/download/1dc514532f08/UnityDownloadAssistant-2017.2.1p2.exe)</span></span>

### <a name="project-files"></a><span data-ttu-id="de425-134">專案檔</span><span class="sxs-lookup"><span data-stu-id="de425-134">Project files</span></span>

* <span data-ttu-id="de425-135">[下載](https://github.com/Microsoft/MixedReality213/archive/master.zip) 專案所需的檔案，並將檔案解壓縮至桌面。</span><span class="sxs-lookup"><span data-stu-id="de425-135">[Download the files](https://github.com/Microsoft/MixedReality213/archive/master.zip) required by the project and extract the files to the Desktop.</span></span>

>[!NOTE]
><span data-ttu-id="de425-136">如果您想要在下載之前查看原始程式碼， [可在 GitHub 上](https://github.com/Microsoft/MixedReality213)取得。</span><span class="sxs-lookup"><span data-stu-id="de425-136">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/MixedReality213).</span></span>

## <a name="unity-setup"></a><span data-ttu-id="de425-137">Unity 設定</span><span class="sxs-lookup"><span data-stu-id="de425-137">Unity setup</span></span>

>[!VIDEO https://www.youtube.com/embed/cBAOALaHys4]

### <a name="objectives"></a><span data-ttu-id="de425-138">目標</span><span class="sxs-lookup"><span data-stu-id="de425-138">Objectives</span></span>

* <span data-ttu-id="de425-139">針對 Windows Mixed Reality 開發優化 Unity</span><span class="sxs-lookup"><span data-stu-id="de425-139">Optimize Unity for Windows Mixed Reality development</span></span>
* <span data-ttu-id="de425-140">安裝混合實境相機</span><span class="sxs-lookup"><span data-stu-id="de425-140">Setup Mixed Reality Camera</span></span>
* <span data-ttu-id="de425-141">設定環境</span><span class="sxs-lookup"><span data-stu-id="de425-141">Setup environment</span></span>

### <a name="instructions"></a><span data-ttu-id="de425-142">指示</span><span class="sxs-lookup"><span data-stu-id="de425-142">Instructions</span></span>

* <span data-ttu-id="de425-143">啟動 Unity。</span><span class="sxs-lookup"><span data-stu-id="de425-143">Start Unity.</span></span>
* <span data-ttu-id="de425-144">選取 [開啟]  。</span><span class="sxs-lookup"><span data-stu-id="de425-144">Select **Open**.</span></span>
* <span data-ttu-id="de425-145">流覽至您的桌面，並尋找您先前 unarchived 的 **MixedReality213 主** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="de425-145">Navigate to your Desktop and find the **MixedReality213-master** folder you previously unarchived.</span></span>
* <span data-ttu-id="de425-146">按一下 [選擇資料夾]。</span><span class="sxs-lookup"><span data-stu-id="de425-146">Click **Select Folder**.</span></span>
* <span data-ttu-id="de425-147">Unity 完成載入專案檔之後，您就能夠看到 Unity 編輯器。</span><span class="sxs-lookup"><span data-stu-id="de425-147">Once Unity finishes loading project files, you will be able to see Unity editor.</span></span>
* <span data-ttu-id="de425-148">在 Unity 中，選取 [ **File > Build Settings**]。</span><span class="sxs-lookup"><span data-stu-id="de425-148">In Unity, select **File > Build Settings**.</span></span>

    ![MR213_BuildSettings](images/mr213-buildsettings-450px.png)

* <span data-ttu-id="de425-150">在 [**平臺**] 清單中選取 **通用 Windows 平臺**，然後按一下 [**切換平臺**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="de425-150">Select **Universal Windows Platform** in the **Platform** list and click the **Switch Platform** button.</span></span>
* <span data-ttu-id="de425-151">將目標裝置設定為 **任何裝置**</span><span class="sxs-lookup"><span data-stu-id="de425-151">Set Target Device to **Any device**</span></span>
* <span data-ttu-id="de425-152">將組建類型設定為 **D3D**</span><span class="sxs-lookup"><span data-stu-id="de425-152">Set Build Type to **D3D**</span></span>
* <span data-ttu-id="de425-153">將 SDK 設定為 **最新安裝**</span><span class="sxs-lookup"><span data-stu-id="de425-153">Set SDK to **Latest Installed**</span></span>
* <span data-ttu-id="de425-154">檢查 **Unity c # 專案**</span><span class="sxs-lookup"><span data-stu-id="de425-154">Check **Unity C# Projects**</span></span>
    * <span data-ttu-id="de425-155">這可讓您修改 Visual Studio 專案中的指令檔，而不需要重建 Unity 專案。</span><span class="sxs-lookup"><span data-stu-id="de425-155">This allows you modify script files in the Visual Studio project without rebuilding Unity project.</span></span>
* <span data-ttu-id="de425-156">按一下 [ **玩家設定**]。</span><span class="sxs-lookup"><span data-stu-id="de425-156">Click **Player Settings**.</span></span>
* <span data-ttu-id="de425-157">在 [偵測 **器** ] 面板中，向下滾動至底部</span><span class="sxs-lookup"><span data-stu-id="de425-157">In the **Inspector** panel, scroll down to the bottom</span></span>
* <span data-ttu-id="de425-158">在 [XR 設定] 中，檢查 **支援的虛擬實境**</span><span class="sxs-lookup"><span data-stu-id="de425-158">In XR Settings, check **Virtual Reality Supported**</span></span>
* <span data-ttu-id="de425-159">在 [虛擬實境 Sdk] 下，選取 **Windows Mixed Reality**</span><span class="sxs-lookup"><span data-stu-id="de425-159">Under Virtual Reality SDKs, select **Windows Mixed Reality**</span></span>

    ![MR213_XRSettings](images/mr213-xrsettings-500px.png)

* <span data-ttu-id="de425-161">關閉 [ **組建設定** ] 視窗。</span><span class="sxs-lookup"><span data-stu-id="de425-161">Close **Build Settings** window.</span></span>

### <a name="project-structure"></a><span data-ttu-id="de425-162">專案結構</span><span class="sxs-lookup"><span data-stu-id="de425-162">Project structure</span></span>

<span data-ttu-id="de425-163">本教學課程使用 **[混合現實工具組-Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)**。</span><span class="sxs-lookup"><span data-stu-id="de425-163">This tutorial uses **[Mixed Reality Toolkit - Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)**.</span></span> <span data-ttu-id="de425-164">您可以在 [此頁面](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases)上找到這些版本。</span><span class="sxs-lookup"><span data-stu-id="de425-164">You can find the releases on [this page](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases).</span></span>

![ProjectStructure](images/mr213-projectstructure-650px.png)

<span data-ttu-id="de425-166">**針對您的參考完成的場景**</span><span class="sxs-lookup"><span data-stu-id="de425-166">**Completed scenes for your reference**</span></span>

* <span data-ttu-id="de425-167">您會在 **幕後** 資料夾中找到兩個已完成的 Unity 幕後。</span><span class="sxs-lookup"><span data-stu-id="de425-167">You will find two completed Unity scenes under **Scenes** folder.</span></span>
    * <span data-ttu-id="de425-168">**MixedReality213**：已完成場景與單一筆刷</span><span class="sxs-lookup"><span data-stu-id="de425-168">**MixedReality213**: Completed scene with single brush</span></span>
    * <span data-ttu-id="de425-169">**MixedReality213Advanced**：使用多筆刷完成適用于 advanced design 的場景</span><span class="sxs-lookup"><span data-stu-id="de425-169">**MixedReality213Advanced**: Completed scene for advanced design with multiple brushes</span></span>

<span data-ttu-id="de425-170">**教學課程的新場景設定**</span><span class="sxs-lookup"><span data-stu-id="de425-170">**New Scene setup for the tutorial**</span></span>

* <span data-ttu-id="de425-171">在 Unity 中，按一下 [檔案] **> 新增場景**</span><span class="sxs-lookup"><span data-stu-id="de425-171">In Unity, click **File > New Scene**</span></span>
* <span data-ttu-id="de425-172">刪除 **主要攝影機** 和 **方向光線**</span><span class="sxs-lookup"><span data-stu-id="de425-172">Delete **Main Camera** and **Directional Light**</span></span>
* <span data-ttu-id="de425-173">在 [ **專案] 面板** 中，搜尋下列 prefabs，並將 **其拖曳** 到 [階層] 面板中：</span><span class="sxs-lookup"><span data-stu-id="de425-173">From the **Project panel**, search and drag the following prefabs into the **Hierarchy** panel:</span></span>
    * <span data-ttu-id="de425-174">資產/HoloToolkit/Input/Prefabs/**MixedRealityCamera**</span><span class="sxs-lookup"><span data-stu-id="de425-174">Assets/HoloToolkit/Input/Prefabs/**MixedRealityCamera**</span></span>
    * <span data-ttu-id="de425-175">資產/AppPrefabs/**環境**</span><span class="sxs-lookup"><span data-stu-id="de425-175">Assets/AppPrefabs/**Environment**</span></span>

    ![攝影機和環境](images/mr213-cameraenvironment-300px.jpg)

* <span data-ttu-id="de425-177">混合現實工具組中有兩種攝影機 prefabs：</span><span class="sxs-lookup"><span data-stu-id="de425-177">There are two camera prefabs in Mixed Reality Toolkit:</span></span>
    * <span data-ttu-id="de425-178">**MixedRealityCamera. 預製專案**：僅限相機</span><span class="sxs-lookup"><span data-stu-id="de425-178">**MixedRealityCamera.prefab**: Camera only</span></span>
    * <span data-ttu-id="de425-179">**MixedRealityCameraParent. 預製專案**：相機 + 遙傳 + 界限</span><span class="sxs-lookup"><span data-stu-id="de425-179">**MixedRealityCameraParent.prefab**: Camera + Teleportation + Boundary</span></span>
    * <span data-ttu-id="de425-180">在本教學課程中，我們將使用 **MixedRealityCamera** 而不使用遙傳功能。</span><span class="sxs-lookup"><span data-stu-id="de425-180">In this tutorial, we will use **MixedRealityCamera** without teleportation feature.</span></span> <span data-ttu-id="de425-181">因此，我們新增了簡單的 **環境** 預製專案，其中包含讓使用者感覺更接地的基本樓層。</span><span class="sxs-lookup"><span data-stu-id="de425-181">Because of this, we added simple **Environment** prefab which contains a basic floor to make the user feel grounded.</span></span>
    * <span data-ttu-id="de425-182">若要深入瞭解遙傳 with **MixedRealityCameraParent**，請參閱 [Advanced design-遙傳 and locomotion](#advanced-design---teleportation-and-locomotion)</span><span class="sxs-lookup"><span data-stu-id="de425-182">To learn more about the teleportation with **MixedRealityCameraParent**, see [Advanced design - Teleportation and locomotion](#advanced-design---teleportation-and-locomotion)</span></span>

<span data-ttu-id="de425-183">**Skybox 設定**</span><span class="sxs-lookup"><span data-stu-id="de425-183">**Skybox setup**</span></span>

* <span data-ttu-id="de425-184">按一下 [ **視窗] > 光源 > 設定**</span><span class="sxs-lookup"><span data-stu-id="de425-184">Click **Window > Lighting > Settings**</span></span>
* <span data-ttu-id="de425-185">按一下 [ **Skybox 材質] 欄位** 右邊的圓形</span><span class="sxs-lookup"><span data-stu-id="de425-185">Click the circle on the right side of the **Skybox Material field**</span></span>
* <span data-ttu-id="de425-186">輸入「灰色」並選取 **SkyboxGray** (資產/AppPrefabs/支援/材質/SkyboxGray) </span><span class="sxs-lookup"><span data-stu-id="de425-186">Type in ‘gray’ and select **SkyboxGray** (Assets/AppPrefabs/Support/Materials/SkyboxGray.mat)</span></span>

    ![設定 skybox](images/mr123-skyboxsetting-400px.jpg)

* <span data-ttu-id="de425-188">檢查 **Skybox** 選項，以查看指派的灰色漸層 Skybox</span><span class="sxs-lookup"><span data-stu-id="de425-188">Check **Skybox** option to be able to see assigned gray gradient skybox</span></span>

    ![切換 skybox 選項](images/mr213-skyboxcheck-400px.jpg)

* <span data-ttu-id="de425-190">具有 MixedRealityCamera、環境和灰色 skybox 的場景看起來會像這樣。</span><span class="sxs-lookup"><span data-stu-id="de425-190">The scene with MixedRealityCamera, Environment and gray skybox will look like this.</span></span>

    ![MixedReality213 環境](images/mr213-environment-600px.jpg)

* <span data-ttu-id="de425-192">按一下 [檔案] **> 另存場景**</span><span class="sxs-lookup"><span data-stu-id="de425-192">Click **File > Save Scene as**</span></span>
* <span data-ttu-id="de425-193">以任何名稱 **將場景儲存** 在場景資料夾下</span><span class="sxs-lookup"><span data-stu-id="de425-193">**Save** your scene under Scenes folder with any name</span></span>

## <a name="chapter-1---controller-visualization"></a><span data-ttu-id="de425-194">第1章-控制器視覺效果</span><span class="sxs-lookup"><span data-stu-id="de425-194">Chapter 1 - Controller visualization</span></span>

>[!VIDEO https://www.youtube.com/embed/Kw0bf5NqyRg]

### <a name="objectives"></a><span data-ttu-id="de425-195">目標</span><span class="sxs-lookup"><span data-stu-id="de425-195">Objectives</span></span>

* <span data-ttu-id="de425-196">瞭解如何在 Unity 的遊戲模式和執行時間轉譯移動控制器模型。</span><span class="sxs-lookup"><span data-stu-id="de425-196">Learn how to render motion controller models in Unity's game mode and at runtime.</span></span>

<span data-ttu-id="de425-197">Windows Mixed Reality 提供適用于控制器視覺效果的動畫控制器模型。</span><span class="sxs-lookup"><span data-stu-id="de425-197">Windows Mixed Reality provides an animated controller model for controller visualization.</span></span> <span data-ttu-id="de425-198">您可以針對應用程式中的控制器視覺效果採用幾種方法：</span><span class="sxs-lookup"><span data-stu-id="de425-198">There are several approaches you can take for controller visualization in your app:</span></span>

* <span data-ttu-id="de425-199">預設-使用預設控制器而不修改</span><span class="sxs-lookup"><span data-stu-id="de425-199">Default - Using default controller without modification</span></span>
* <span data-ttu-id="de425-200">混合式使用預設控制器，但自訂其部分元素或覆迭 UI 元件</span><span class="sxs-lookup"><span data-stu-id="de425-200">Hybrid - Using default controller, but customizing some of its elements or overlaying UI components</span></span>
* <span data-ttu-id="de425-201">取代-為控制器使用您自己的自訂3D 模型</span><span class="sxs-lookup"><span data-stu-id="de425-201">Replacement - Using your own customized 3D model for the controller</span></span>

<span data-ttu-id="de425-202">在本章中，我們將瞭解這些控制器自訂的範例。</span><span class="sxs-lookup"><span data-stu-id="de425-202">In this chapter, we will learn about the examples of these controller customizations.</span></span>

### <a name="instructions"></a><span data-ttu-id="de425-203">指示</span><span class="sxs-lookup"><span data-stu-id="de425-203">Instructions</span></span>

* <span data-ttu-id="de425-204">在 [ **專案** ] 面板的 [搜尋] 方塊中，輸入 **MotionControllers** 。</span><span class="sxs-lookup"><span data-stu-id="de425-204">In the **Project** panel, type **MotionControllers** in the search box .</span></span> <span data-ttu-id="de425-205">您也可以在 [資產/HoloToolkit/輸入/Prefabs/] 下找到它。</span><span class="sxs-lookup"><span data-stu-id="de425-205">You can also find it under Assets/HoloToolkit/Input/Prefabs/.</span></span>
* <span data-ttu-id="de425-206">將 **MotionControllers** 預製專案拖曳到 [階層 **] 面板中** 。</span><span class="sxs-lookup"><span data-stu-id="de425-206">Drag the **MotionControllers** prefab into the **Hierarchy** panel.</span></span>
* <span data-ttu-id="de425-207">按一下 [階層 **] 面板中的 [** **MotionControllers** ] 預製專案。</span><span class="sxs-lookup"><span data-stu-id="de425-207">Click on the **MotionControllers** prefab in the **Hierarchy** panel.</span></span>

<span data-ttu-id="de425-208">**MotionControllers 預製專案**</span><span class="sxs-lookup"><span data-stu-id="de425-208">**MotionControllers prefab**</span></span>

<span data-ttu-id="de425-209">**MotionControllers** 預製專案具有 **MotionControllerVisualizer** 腳本，可提供替代控制器模型的位置。</span><span class="sxs-lookup"><span data-stu-id="de425-209">**MotionControllers** prefab has a **MotionControllerVisualizer** script which provides the slots for alternate controller models.</span></span> <span data-ttu-id="de425-210">如果您指派自己的自訂3D 模型（例如手或寶劍）並核取 [一律使用替代模型]，則會看到它們，而不是預設模型。</span><span class="sxs-lookup"><span data-stu-id="de425-210">If you assign your own custom 3D models such as a hand or a sword and check 'Always Use Alternate Left/Right Model', you will see them instead of the default model.</span></span> <span data-ttu-id="de425-211">我們將在第4章中使用這個位置，以筆刷取代控制器模型。</span><span class="sxs-lookup"><span data-stu-id="de425-211">We will use this slot in Chapter 4 to replace the controller model with a brush.</span></span>

![MR213_ControllerVisualizer](images/mr213-controllervisualizer-600px.png)

<span data-ttu-id="de425-213">**指示**</span><span class="sxs-lookup"><span data-stu-id="de425-213">**Instructions**</span></span>

* <span data-ttu-id="de425-214">在 [偵測 **器** ] 面板中，按兩下 [ **MotionControllerVisualizer** 腳本] 以查看 Visual Studio 中的程式碼</span><span class="sxs-lookup"><span data-stu-id="de425-214">In the **Inspector** panel, double click **MotionControllerVisualizer** script to see the code in the Visual Studio</span></span>

<span data-ttu-id="de425-215">**MotionControllerVisualizer 腳本**</span><span class="sxs-lookup"><span data-stu-id="de425-215">**MotionControllerVisualizer script**</span></span>

<span data-ttu-id="de425-216">**MotionControllerVisualizer** 和 **MotionControllerInfo** 類別提供存取 & 修改預設控制器模型的方法。</span><span class="sxs-lookup"><span data-stu-id="de425-216">The **MotionControllerVisualizer** and **MotionControllerInfo** classes provide the means to access & modify the default controller models.</span></span> <span data-ttu-id="de425-217">**MotionControllerVisualizer** 會訂閱 Unity 的 **InteractionSourceDetected** 事件，並且在找到控制器模型時自動將其具現化。</span><span class="sxs-lookup"><span data-stu-id="de425-217">**MotionControllerVisualizer** subscribes to Unity's **InteractionSourceDetected** event and automatically instantiates controller models when they are found.</span></span>

```cs
protected override void Awake()
{
    ...
    InteractionManager.InteractionSourceDetected += InteractionManager_InteractionSourceDetected;
    InteractionManager.InteractionSourceLost += InteractionManager_InteractionSourceLost;
    ...
}
```

<span data-ttu-id="de425-218">控制器模型是根據 [glTF 規格](https://github.com/KhronosGroup/glTF)來傳遞。</span><span class="sxs-lookup"><span data-stu-id="de425-218">The controller models are delivered according to [the glTF specification](https://github.com/KhronosGroup/glTF).</span></span> <span data-ttu-id="de425-219">這種格式的建立是為了提供通用格式，同時改進了傳輸和解除包裝3D 資產的程式。</span><span class="sxs-lookup"><span data-stu-id="de425-219">This format has been created to provide a common format, while improving the process behind transmitting and unpacking 3D assets.</span></span> <span data-ttu-id="de425-220">在此情況下，我們需要在執行時間取出和載入控制器模型，因為我們想要讓使用者的體驗盡可能順暢，而且不保證使用者可能使用的動作控制器版本。</span><span class="sxs-lookup"><span data-stu-id="de425-220">In this case, we need to retrieve and load the controller models at runtime, as we want to make the user's experience as seamless as possible, and it's not guaranteed which version of the motion controllers the user might be using.</span></span> <span data-ttu-id="de425-221">此課程透過混合現實工具組，使用 Khronos 群組的 [UnityGLTF 專案](https://github.com/KhronosGroup/UnityGLTF)版本。</span><span class="sxs-lookup"><span data-stu-id="de425-221">This course, via the Mixed Reality Toolkit, uses a version of the Khronos Group's [UnityGLTF project](https://github.com/KhronosGroup/UnityGLTF).</span></span>

<span data-ttu-id="de425-222">一旦傳遞控制器，腳本就可以使用 **MotionControllerInfo** 來尋找特定控制器元素的轉換，讓它們可以正確地定位。</span><span class="sxs-lookup"><span data-stu-id="de425-222">Once the controller has been delivered, scripts can use **MotionControllerInfo** to find the transforms for specific controller elements so they can correctly position themselves.</span></span>

<span data-ttu-id="de425-223">在稍後的章節中，我們將瞭解如何使用這些腳本，將 UI 元素附加至控制器。</span><span class="sxs-lookup"><span data-stu-id="de425-223">In a later chapter, we will learn how to use these scripts to attach UI elements to the controllers.</span></span>

<span data-ttu-id="de425-224">*在某些腳本中，您會發現具有 #if 的程式碼區塊 **！UNITY_EDITOR** 或 **UNITY_WSA**。這些程式碼區塊只會在您部署至 Windows 時于 UWP 執行時間上執行。這是因為 Unity 編輯器和 UWP 應用程式執行時間所使用的 Api 集不同。*</span><span class="sxs-lookup"><span data-stu-id="de425-224">*In some scripts, you will find code blocks with **#if !UNITY_EDITOR** or **UNITY_WSA**. These code blocks run only on the UWP runtime when you deploy to Windows. This is because the set of APIs used by the Unity editor and the UWP app runtime are different.*</span></span>

* <span data-ttu-id="de425-225">**儲存** 場景，然後按一下 [ **播放** ] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="de425-225">**Save** the scene and click the **play** button.</span></span>

<span data-ttu-id="de425-226">您將能夠在耳機中看到有移動控制器的場景。</span><span class="sxs-lookup"><span data-stu-id="de425-226">You will be able to see the scene with motion controllers in your headset.</span></span> <span data-ttu-id="de425-227">您可以看到按鈕點擊、操縱杆移動和觸控板觸控醒目提示的詳細動畫。</span><span class="sxs-lookup"><span data-stu-id="de425-227">You can see detailed animations for button clicks, thumbstick movement, and touchpad touch highlighting.</span></span>

![MR213_Controller 視覺效果預設](images/mr213-controllervisualizationdefault-500px.jpg)

## <a name="chapter-2---attaching-ui-elements-to-the-controller"></a><span data-ttu-id="de425-229">第2章-將 UI 元素附加至控制器</span><span class="sxs-lookup"><span data-stu-id="de425-229">Chapter 2 - Attaching UI elements to the controller</span></span>

>[!VIDEO https://www.youtube.com/embed/e-mLlwmTzJo]

### <a name="objectives"></a><span data-ttu-id="de425-230">目標</span><span class="sxs-lookup"><span data-stu-id="de425-230">Objectives</span></span>

* <span data-ttu-id="de425-231">瞭解動作控制器的元素</span><span class="sxs-lookup"><span data-stu-id="de425-231">Learn about the elements of the motion controllers</span></span>
* <span data-ttu-id="de425-232">瞭解如何將物件附加至控制器的特定部分</span><span class="sxs-lookup"><span data-stu-id="de425-232">Learn how to attach objects to specific parts of the controllers</span></span>

<span data-ttu-id="de425-233">在本章中，您將瞭解如何將使用者介面專案新增至控制器，讓使用者隨時都能輕鬆地存取和操作。</span><span class="sxs-lookup"><span data-stu-id="de425-233">In this chapter, you will learn how to add user interface elements to the controller which the user can easily access and manipulate at anytime.</span></span> <span data-ttu-id="de425-234">您也將瞭解如何使用觸控板輸入來新增簡單的色彩選擇器 UI。</span><span class="sxs-lookup"><span data-stu-id="de425-234">You will also learn how to add a simple color picker UI using the touchpad input.</span></span>

### <a name="instructions"></a><span data-ttu-id="de425-235">指示</span><span class="sxs-lookup"><span data-stu-id="de425-235">Instructions</span></span>

* <span data-ttu-id="de425-236">在 [ **專案** ] 面板中，搜尋 **MotionControllerInfo** 腳本。</span><span class="sxs-lookup"><span data-stu-id="de425-236">In the **Project** panel, search **MotionControllerInfo** script.</span></span>
* <span data-ttu-id="de425-237">從搜尋結果中，按兩下 [ **MotionControllerInfo** 腳本] 以查看 Visual Studio 中的程式碼。</span><span class="sxs-lookup"><span data-stu-id="de425-237">From the search result, double click **MotionControllerInfo** script to see the code in Visual Studio.</span></span>

<span data-ttu-id="de425-238">**MotionControllerInfo 腳本**</span><span class="sxs-lookup"><span data-stu-id="de425-238">**MotionControllerInfo script**</span></span>

<span data-ttu-id="de425-239">第一個步驟是選擇您要讓 UI 附加至哪個控制器元素。</span><span class="sxs-lookup"><span data-stu-id="de425-239">The first step is to choose which element of the controller you want the UI to attach to.</span></span> <span data-ttu-id="de425-240">這些元素是在 **MotionControllerInfo.cs** 的 **ControllerElementEnum** 中定義。</span><span class="sxs-lookup"><span data-stu-id="de425-240">These elements are defined in **ControllerElementEnum** in **MotionControllerInfo.cs**.</span></span>

![MR213 MotionControllerElements](images/mr213-motioncontrollerelements-1000px.jpg)

* <span data-ttu-id="de425-242">**首頁**</span><span class="sxs-lookup"><span data-stu-id="de425-242">**Home**</span></span>
* <span data-ttu-id="de425-243">**功能表**</span><span class="sxs-lookup"><span data-stu-id="de425-243">**Menu**</span></span>
* <span data-ttu-id="de425-244">**把握**</span><span class="sxs-lookup"><span data-stu-id="de425-244">**Grasp**</span></span>
* <span data-ttu-id="de425-245">**操縱杆**</span><span class="sxs-lookup"><span data-stu-id="de425-245">**Thumbstick**</span></span>
* <span data-ttu-id="de425-246">**選取**</span><span class="sxs-lookup"><span data-stu-id="de425-246">**Select**</span></span>
* <span data-ttu-id="de425-247">**觸控板**</span><span class="sxs-lookup"><span data-stu-id="de425-247">**Touchpad**</span></span>
* <span data-ttu-id="de425-248">**指標姿勢** –此元素表示控制器指向正向方向的秘訣。</span><span class="sxs-lookup"><span data-stu-id="de425-248">**Pointing pose** – this element represents the tip of the controller pointing forward direction.</span></span>

<span data-ttu-id="de425-249">**指示**</span><span class="sxs-lookup"><span data-stu-id="de425-249">**Instructions**</span></span>

* <span data-ttu-id="de425-250">在 [ **專案** ] 面板中，搜尋 **AttachToController** 腳本。</span><span class="sxs-lookup"><span data-stu-id="de425-250">In the **Project** panel, search **AttachToController** script.</span></span>
* <span data-ttu-id="de425-251">從搜尋結果中，按兩下 [ **AttachToController** 腳本] 以查看 Visual Studio 中的程式碼。</span><span class="sxs-lookup"><span data-stu-id="de425-251">From the search result, double click **AttachToController** script to see the code in Visual Studio.</span></span>

<span data-ttu-id="de425-252">**AttachToController 腳本**</span><span class="sxs-lookup"><span data-stu-id="de425-252">**AttachToController script**</span></span>

<span data-ttu-id="de425-253">**AttachToController** 腳本提供簡單的方式，將任何物件附加至指定的控制器 handedness 和元素。</span><span class="sxs-lookup"><span data-stu-id="de425-253">The **AttachToController** script provides a simple way to attach any objects to a specified controller handedness and element.</span></span>

<span data-ttu-id="de425-254">在 **AttachElementToController ( # B1** 中，</span><span class="sxs-lookup"><span data-stu-id="de425-254">In **AttachElementToController()**,</span></span>

* <span data-ttu-id="de425-255">使用 **MotionControllerInfo. handedness** 檢查 handedness</span><span class="sxs-lookup"><span data-stu-id="de425-255">Check handedness using **MotionControllerInfo.Handedness**</span></span>
* <span data-ttu-id="de425-256">使用 MotionControllerInfo. TryGetElement 取得控制器的特定元素 **( # B1**</span><span class="sxs-lookup"><span data-stu-id="de425-256">Get specific element of the controller using **MotionControllerInfo.TryGetElement()**</span></span>
* <span data-ttu-id="de425-257">從控制器模型中抓取專案的轉換之後，父物件下的物件和設定物件的本機位置 & 旋轉為零。</span><span class="sxs-lookup"><span data-stu-id="de425-257">After retrieving the element's transform from the controller model, parent the object under it and set object's local position & rotation to zero.</span></span>

```cs
public MotionControllerInfo.ControllerElementEnum Element { get { return element; } }

private void AttachElementToController(MotionControllerInfo newController)
{
     if (!IsAttached && newController.Handedness == handedness)
     {
          if (!newController.TryGetElement(element, out elementTransform))
          {
               Debug.LogError("Unable to find element of type " + element + " under controller " + newController.ControllerParent.name + "; not attaching.");
               return;
          }

          controller = newController;

          SetChildrenActive(true);

          // Parent ourselves under the element and set our offsets
          transform.parent = elementTransform;
          transform.localPosition = positionOffset;
          transform.localEulerAngles = rotationOffset;
          if (setScaleOnAttach)
          {
               transform.localScale = scale;
          }

          // Announce that we're attached
          OnAttachToController();
          IsAttached = true;
     }
}
```

<span data-ttu-id="de425-258">使用 **AttachToController** 腳本最簡單的方式就是從它繼承，如同我們在 ColorPickerWheel 的案例中所做的一樣 **。**</span><span class="sxs-lookup"><span data-stu-id="de425-258">The simplest way to use **AttachToController** script is to inherit from it, as we've done in the case of **ColorPickerWheel.**</span></span> <span data-ttu-id="de425-259">只要覆寫 **OnAttachToController** 和 **OnDetachFromController** 函式，就可以在偵測到控制器/中斷連線時執行您的設定/細目。</span><span class="sxs-lookup"><span data-stu-id="de425-259">Simply override the **OnAttachToController** and **OnDetachFromController** functions to perform your setup / breakdown when the controller is detected / disconnected.</span></span>

<span data-ttu-id="de425-260">**指示**</span><span class="sxs-lookup"><span data-stu-id="de425-260">**Instructions**</span></span>

* <span data-ttu-id="de425-261">在 [ **專案** ] 面板中，輸入搜尋方塊 **ColorPickerWheel**。</span><span class="sxs-lookup"><span data-stu-id="de425-261">In the **Project** panel, type in the search box **ColorPickerWheel**.</span></span> <span data-ttu-id="de425-262">您也可以在 [資產/AppPrefabs/] 下找到它。</span><span class="sxs-lookup"><span data-stu-id="de425-262">You can also find it under Assets/AppPrefabs/.</span></span>
* <span data-ttu-id="de425-263">將 **ColorPickerWheel** 預製專案拖曳到 **[階層** ] 面板中。</span><span class="sxs-lookup"><span data-stu-id="de425-263">Drag **ColorPickerWheel** prefab into the **Hierarchy** panel.</span></span>
* <span data-ttu-id="de425-264">按一下 [階層 **] 面板中的 [** **ColorPickerWheel** ] 預製專案。</span><span class="sxs-lookup"><span data-stu-id="de425-264">Click the **ColorPickerWheel** prefab in the **Hierarchy** panel.</span></span>
* <span data-ttu-id="de425-265">在 [偵測 **器** ] 面板中，按兩下 [ **ColorPickerWheel** 腳本] 以查看 Visual Studio 中的程式碼。</span><span class="sxs-lookup"><span data-stu-id="de425-265">In the **Inspector** panel, double click **ColorPickerWheel** Script to see the code in Visual Studio.</span></span>

![ColorPickerWheel 預製專案](images/mr213-colorpickerwheel-1000px.jpg)

<span data-ttu-id="de425-267">**ColorPickerWheel 腳本**</span><span class="sxs-lookup"><span data-stu-id="de425-267">**ColorPickerWheel script**</span></span>

<span data-ttu-id="de425-268">因為 **ColorPickerWheel** 會繼承 **AttachToController**，所以它會在 [偵測 **器**] 面板中顯示 **Handedness** 和 **元素**。</span><span class="sxs-lookup"><span data-stu-id="de425-268">Since **ColorPickerWheel** inherits **AttachToController**, it shows **Handedness** and **Element** in the **Inspector** panel.</span></span> <span data-ttu-id="de425-269">我們會將 UI 附加至左方控制器上的「觸控板」元素。</span><span class="sxs-lookup"><span data-stu-id="de425-269">We'll be attaching the UI to the Touchpad element on the left controller.</span></span>

![ColorPickerWheel 腳本](images/mr213-attachtocontroller-300px.jpg)

<span data-ttu-id="de425-271">**ColorPickerWheel** 會覆寫 **OnAttachToController** 和 **OnDetachFromController** ，以訂閱將在下一章中用來選取觸控板輸入之色彩的輸入事件。</span><span class="sxs-lookup"><span data-stu-id="de425-271">**ColorPickerWheel** overrides the **OnAttachToController** and **OnDetachFromController** to subscribe to the input event which will be used in next chapter for color selection with touchpad input.</span></span>

```cs
public class ColorPickerWheel : AttachToController, IPointerTarget
{
    protected override void OnAttachToController()
    {
        // Subscribe to input now that we're parented under the controller
        InteractionManager.InteractionSourceUpdated += InteractionSourceUpdated;
    }

    protected override void OnDetachFromController()
    {
        Visible = false;

        // Unsubscribe from input now that we've detached from the controller
        InteractionManager.InteractionSourceUpdated -= InteractionSourceUpdated;
    }
    ...
}
```

* <span data-ttu-id="de425-272">**儲存** 場景，然後按一下 [ **播放** ] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="de425-272">**Save** the scene and click the **play** button.</span></span>

<span data-ttu-id="de425-273">**將物件附加至控制器的替代方法**</span><span class="sxs-lookup"><span data-stu-id="de425-273">**Alternative method for attaching objects to the controllers**</span></span>

<span data-ttu-id="de425-274">建議您的腳本繼承自 **AttachToController** 並覆寫 **OnAttachToController**。</span><span class="sxs-lookup"><span data-stu-id="de425-274">We recommend that your scripts inherit from **AttachToController** and override **OnAttachToController**.</span></span> <span data-ttu-id="de425-275">不過，這可能不一定可行。</span><span class="sxs-lookup"><span data-stu-id="de425-275">However, this may not always be possible.</span></span> <span data-ttu-id="de425-276">替代方法是使用它作為獨立元件。</span><span class="sxs-lookup"><span data-stu-id="de425-276">An alternative is using it as a standalone component.</span></span> <span data-ttu-id="de425-277">當您想要在不重構腳本的情況下，將現有的預製專案附加至控制器時，這會很有用。</span><span class="sxs-lookup"><span data-stu-id="de425-277">This can be useful when you want to attach an existing prefab to a controller without refactoring your scripts.</span></span> <span data-ttu-id="de425-278">您只需在執行任何安裝程式之前，讓您的類別等待 IsAttached 設為 true。</span><span class="sxs-lookup"><span data-stu-id="de425-278">Simply have your class wait for IsAttached to be set to true before performing any setup.</span></span> <span data-ttu-id="de425-279">最簡單的方法是使用協同程式作為「開始」。</span><span class="sxs-lookup"><span data-stu-id="de425-279">The simplest way to do this is by using a coroutine for 'Start.'</span></span>

```cs
private IEnumerator Start() {
    AttachToController attach = gameObject.GetComponent<AttachToController>();

    while (!attach.IsAttached) {
        yield return null;
    }

    // Perform setup here
}
```

## <a name="chapter-3---working-with-touchpad-input"></a><span data-ttu-id="de425-280">第3章-使用觸控板輸入</span><span class="sxs-lookup"><span data-stu-id="de425-280">Chapter 3 - Working with touchpad input</span></span>

>[!VIDEO https://www.youtube.com/embed/SUyw0kxZPFw]

### <a name="objectives"></a><span data-ttu-id="de425-281">目標</span><span class="sxs-lookup"><span data-stu-id="de425-281">Objectives</span></span>

* <span data-ttu-id="de425-282">瞭解如何取得觸控板輸入資料事件</span><span class="sxs-lookup"><span data-stu-id="de425-282">Learn how to get touchpad input data events</span></span>
* <span data-ttu-id="de425-283">瞭解如何為您的應用程式體驗使用觸控板軸位置資訊</span><span class="sxs-lookup"><span data-stu-id="de425-283">Learn how to use touchpad axis position information for your app experience</span></span>

### <a name="instructions"></a><span data-ttu-id="de425-284">指示</span><span class="sxs-lookup"><span data-stu-id="de425-284">Instructions</span></span>

* <span data-ttu-id="de425-285">**在 [階層**] 面板中，按一下 [ **ColorPickerWheel** ]</span><span class="sxs-lookup"><span data-stu-id="de425-285">In the **Hierarchy** panel, click **ColorPickerWheel**</span></span>
* <span data-ttu-id="de425-286">在 [偵測 **器**] 面板的 [ **Animator**] 底下，按兩下 [ **ColorPickerWheelController** ]</span><span class="sxs-lookup"><span data-stu-id="de425-286">In the **Inspector** panel, under **Animator**, double click **ColorPickerWheelController**</span></span>
* <span data-ttu-id="de425-287">您將能夠看到開啟的 **Animator** 索引標籤</span><span class="sxs-lookup"><span data-stu-id="de425-287">You will be able to see **Animator** tab opened</span></span>

<span data-ttu-id="de425-288">**使用 Unity 的動畫控制器顯示/隱藏 UI**</span><span class="sxs-lookup"><span data-stu-id="de425-288">**Showing/hiding UI with Unity's Animation controller**</span></span>

<span data-ttu-id="de425-289">若要使用動畫來顯示及隱藏 **ColorPickerWheel** UI，我們會使用 [Unity 的動畫系統](https://docs.unity3d.com/Manual/AnimationOverview.html)。</span><span class="sxs-lookup"><span data-stu-id="de425-289">To show and hide the **ColorPickerWheel** UI with animation, we are using [Unity's animation system](https://docs.unity3d.com/Manual/AnimationOverview.html).</span></span> <span data-ttu-id="de425-290">將 **ColorPickerWheel** 的 **Visible** 屬性設定為 true 或 false 時，觸發程式會 **顯示** 並 **隱藏** 動畫觸發程式。</span><span class="sxs-lookup"><span data-stu-id="de425-290">Setting the **ColorPickerWheel**'s **Visible** property to true or false triggers **Show** and **Hide** animation triggers.</span></span> <span data-ttu-id="de425-291">**顯示** 和 **隱藏** 參數定義于 **ColorPickerWheelController** 動畫控制器中。</span><span class="sxs-lookup"><span data-stu-id="de425-291">**Show** and **Hide** parameters are defined in the **ColorPickerWheelController** animation controller.</span></span>

![Unity 動畫控制器](images/mr123-animationcontroller-550px.jpg)

<span data-ttu-id="de425-293">**指示**</span><span class="sxs-lookup"><span data-stu-id="de425-293">**Instructions**</span></span>

* <span data-ttu-id="de425-294">**在 [階層**] 面板中，選取 [ **ColorPickerWheel** 預製專案</span><span class="sxs-lookup"><span data-stu-id="de425-294">In the **Hierarchy** panel, select **ColorPickerWheel** prefab</span></span>
* <span data-ttu-id="de425-295">在 [偵測 **器** ] 面板中，按兩下 [ **ColorPickerWheel** 腳本] 以查看 Visual Studio 中的程式碼</span><span class="sxs-lookup"><span data-stu-id="de425-295">In the **Inspector** panel, double click **ColorPickerWheel** script to see the code in the Visual Studio</span></span>

<span data-ttu-id="de425-296">**ColorPickerWheel 腳本**</span><span class="sxs-lookup"><span data-stu-id="de425-296">**ColorPickerWheel script**</span></span>

<span data-ttu-id="de425-297">**ColorPickerWheel** 訂閱 Unity 的 **InteractionSourceUpdated** 事件以接聽觸控板事件。</span><span class="sxs-lookup"><span data-stu-id="de425-297">**ColorPickerWheel** subscribes to Unity's **InteractionSourceUpdated** event to listen for touchpad events.</span></span>

<span data-ttu-id="de425-298">在 **InteractionSourceUpdated ( # B1** 中，腳本會先檢查以確定它：</span><span class="sxs-lookup"><span data-stu-id="de425-298">In **InteractionSourceUpdated()**, the script first checks to ensure that it:</span></span>

* <span data-ttu-id="de425-299">實際上是 (obj 的「觸控板」事件。**touchpadTouched**) </span><span class="sxs-lookup"><span data-stu-id="de425-299">is actually a touchpad event (obj.state.**touchpadTouched**)</span></span>
* <span data-ttu-id="de425-300">源自左方控制器 (的 obj。**handedness**) </span><span class="sxs-lookup"><span data-stu-id="de425-300">originates from the left controller (obj.state.source.**handedness**)</span></span>

<span data-ttu-id="de425-301">如果兩者都是 true，表示觸控板位置 (obj。**touchpadPosition**) 會指派給 **selectorPosition**。</span><span class="sxs-lookup"><span data-stu-id="de425-301">If both are true, the touchpad position (obj.state.**touchpadPosition**) is assigned to **selectorPosition**.</span></span>

```cs
private void InteractionSourceUpdated(InteractionSourceUpdatedEventArgs obj)
{
    if (obj.state.source.handedness == handedness && obj.state.touchpadTouched)
    {
        Visible = true;
        selectorPosition = obj.state.touchpadPosition;
    }
}
```

<span data-ttu-id="de425-302">在 **Update ( # B1** 中，根據 **visible** 屬性，它會觸發在色彩選擇器的 animator 元件中顯示和隱藏動畫觸發程式</span><span class="sxs-lookup"><span data-stu-id="de425-302">In **Update()**, based on **visible** property, it triggers Show and Hide animation triggers in the color picker's animator component</span></span>

```cs
if (visible != visibleLastFrame)
{
    if (visible)
    {
        animator.SetTrigger("Show");
    }
    else
    {
        animator.SetTrigger("Hide");
    }
}
```

<span data-ttu-id="de425-303">在 **Update ( # B1** 中， **selectorPosition** 是用來將光線轉換成色輪的網格碰撞器，它會傳回一個 UV 位置。</span><span class="sxs-lookup"><span data-stu-id="de425-303">In **Update()**, **selectorPosition** is used to cast a ray at the color wheel's mesh collider, which returns a UV position.</span></span> <span data-ttu-id="de425-304">然後，您可以使用這個位置來尋找色輪材質的圖元座標和色彩值。</span><span class="sxs-lookup"><span data-stu-id="de425-304">This position can then be used to find the pixel coordinate and color value of the color wheel's texture.</span></span> <span data-ttu-id="de425-305">透過 **SelectedColor** 屬性可存取其他腳本的這個值。</span><span class="sxs-lookup"><span data-stu-id="de425-305">This value is accessible to other scripts via the **SelectedColor** property.</span></span>

![色彩選擇器滾輪 Raycasting](images/mr213-colorpickerwheel-raycast-700px.png)

```cs
...
    // Clamp selector position to a radius of 1
    Vector3 localPosition = new Vector3(selectorPosition.x * inputScale, 0.15f, selectorPosition.y * inputScale);
    if (localPosition.magnitude > 1)
    {
        localPosition = localPosition.normalized;
    }
    selectorTransform.localPosition = localPosition;

    // Raycast the wheel mesh and get its UV coordinates
    Vector3 raycastStart = selectorTransform.position + selectorTransform.up * 0.15f;
    RaycastHit hit;
    Debug.DrawLine(raycastStart, raycastStart - (selectorTransform.up * 0.25f));

    if (Physics.Raycast(raycastStart, -selectorTransform.up, out hit, 0.25f, 1 << colorWheelObject.layer, QueryTriggerInteraction.Ignore))
    {
        // Get pixel from the color wheel texture using UV coordinates
        Vector2 uv = hit.textureCoord;
        int pixelX = Mathf.FloorToInt(colorWheelTexture.width * uv.x);
        int pixelY = Mathf.FloorToInt(colorWheelTexture.height * uv.y);
        selectedColor = colorWheelTexture.GetPixel(pixelX, pixelY);
        selectedColor.a = 1f;
    }
    // Set the selector's color and blend it with white to make it visible on top of the wheel
    selectorRenderer.material.color = Color.Lerp (selectedColor, Color.white, 0.5f);
}
```

## <a name="chapter-4---overriding-controller-model"></a><span data-ttu-id="de425-307">第4章-覆寫控制器模型</span><span class="sxs-lookup"><span data-stu-id="de425-307">Chapter 4 - Overriding controller model</span></span>

>[!VIDEO https://www.youtube.com/embed/8gBFqA_DZ_U]

### <a name="objectives"></a><span data-ttu-id="de425-308">目標</span><span class="sxs-lookup"><span data-stu-id="de425-308">Objectives</span></span>

* <span data-ttu-id="de425-309">瞭解如何使用自訂3D 模型覆寫控制器模型。</span><span class="sxs-lookup"><span data-stu-id="de425-309">Learn how to override the controller model with a custom 3D model.</span></span>

![MR213_BrushToolOverride](images/mr213-brushtooloverride-500px.jpg)

### <a name="instructions"></a><span data-ttu-id="de425-311">指示</span><span class="sxs-lookup"><span data-stu-id="de425-311">Instructions</span></span>

* <span data-ttu-id="de425-312">按一下 **[階層**] 面板中的 [ **MotionControllers** ]。</span><span class="sxs-lookup"><span data-stu-id="de425-312">Click **MotionControllers** in the **Hierarchy** panel.</span></span>
* <span data-ttu-id="de425-313">按一下 **替代右邊控制器** 欄位右邊的圓形。</span><span class="sxs-lookup"><span data-stu-id="de425-313">Click the circle on the right side of the **Alternate Right Controller** field.</span></span>
* <span data-ttu-id="de425-314">輸入 **' BrushController**'，然後從結果中選取預製專案。</span><span class="sxs-lookup"><span data-stu-id="de425-314">Type in **'BrushController**' and select the prefab from the result.</span></span> <span data-ttu-id="de425-315">您可以在資產/AppPrefabs/**BrushController** 中找到它。</span><span class="sxs-lookup"><span data-stu-id="de425-315">You can find it under Assets/AppPrefabs/**BrushController**.</span></span>
* <span data-ttu-id="de425-316">勾選 [**一律使用替代模型**]</span><span class="sxs-lookup"><span data-stu-id="de425-316">Check **Always Use Alternate Right Model**</span></span>

![MR213_BrushToolOverrideSlot](images/mr213-motioncontrollersoverride-700px.jpg)

<span data-ttu-id="de425-318">**BrushController** 預製專案不一定要 **包含在階層面板中**。</span><span class="sxs-lookup"><span data-stu-id="de425-318">The **BrushController** prefab does not have to be included in the **Hierarchy** panel.</span></span> <span data-ttu-id="de425-319">不過，若要簽出其子元件：</span><span class="sxs-lookup"><span data-stu-id="de425-319">However, to check out its child components:</span></span>

* <span data-ttu-id="de425-320">在 [ **專案** ] 面板中，輸入 **BrushController** ，並將 **BrushController** 預製專案拖曳 **到 [階層** ] 面板中。</span><span class="sxs-lookup"><span data-stu-id="de425-320">In the **Project** panel, type in **BrushController** and drag **BrushController** prefab into the **Hierarchy** panel.</span></span>

![MR213_BrushTool_Prefab2](images/mr213-brushtool-prefab-1000px.jpg)

<span data-ttu-id="de425-322">您將會在 **BrushController** 中找到 **Tip** 元件。</span><span class="sxs-lookup"><span data-stu-id="de425-322">You will find the **Tip** component in **BrushController**.</span></span> <span data-ttu-id="de425-323">我們會使用其轉換來啟動/停止繪製線條。</span><span class="sxs-lookup"><span data-stu-id="de425-323">We will use its transform to start/stop drawing lines.</span></span>

* <span data-ttu-id="de425-324">從 **階層面板中** 刪除 **BrushController** 。</span><span class="sxs-lookup"><span data-stu-id="de425-324">Delete the **BrushController** from the **Hierarchy** panel.</span></span>
* <span data-ttu-id="de425-325">**儲存** 場景，然後按一下 [ **播放** ] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="de425-325">**Save** the scene and click the **play** button.</span></span> <span data-ttu-id="de425-326">您將能夠看到筆刷模型取代右手邊的移動控制器。</span><span class="sxs-lookup"><span data-stu-id="de425-326">You will be able to see the brush model replaced the right-hand motion controller.</span></span>

## <a name="chapter-5---painting-with-select-input"></a><span data-ttu-id="de425-327">第5章-使用選取輸入進行繪製</span><span class="sxs-lookup"><span data-stu-id="de425-327">Chapter 5 - Painting with Select input</span></span>

>[!VIDEO https://www.youtube.com/embed/QTrYaMHIs7w]

### <a name="objectives"></a><span data-ttu-id="de425-328">目標</span><span class="sxs-lookup"><span data-stu-id="de425-328">Objectives</span></span>

* <span data-ttu-id="de425-329">瞭解如何使用選取按鈕事件來啟動和停止線條繪圖</span><span class="sxs-lookup"><span data-stu-id="de425-329">Learn how to use the Select button event to start and stop a line drawing</span></span>

### <a name="instructions"></a><span data-ttu-id="de425-330">指示</span><span class="sxs-lookup"><span data-stu-id="de425-330">Instructions</span></span>

* <span data-ttu-id="de425-331">在 [**專案**] 面板中搜尋 **BrushController** 預製專案。</span><span class="sxs-lookup"><span data-stu-id="de425-331">Search **BrushController** prefab in the **Project** panel.</span></span>
* <span data-ttu-id="de425-332">在 [偵測 **器** ] 面板中，按兩下 [ **BrushController** 腳本] 以查看 Visual Studio 中的程式碼</span><span class="sxs-lookup"><span data-stu-id="de425-332">In the **Inspector** panel, double click **BrushController** Script to see the code in Visual Studio</span></span>

<span data-ttu-id="de425-333">**BrushController 腳本**</span><span class="sxs-lookup"><span data-stu-id="de425-333">**BrushController script**</span></span>

<span data-ttu-id="de425-334">**BrushController** 訂閱 InteractionManager 的 **InteractionSourcePressed** 和 **InteractionSourceReleased** 事件。</span><span class="sxs-lookup"><span data-stu-id="de425-334">**BrushController** subscribes to the InteractionManager's **InteractionSourcePressed** and **InteractionSourceReleased** events.</span></span> <span data-ttu-id="de425-335">觸發 **InteractionSourcePressed** 事件時，筆刷的 **Draw** 屬性會設定為 true;觸發 **InteractionSourceReleased** 事件時，筆刷的 **Draw** 屬性會設定為 false。</span><span class="sxs-lookup"><span data-stu-id="de425-335">When **InteractionSourcePressed** event is triggered, the brush's **Draw** property is set to true; when **InteractionSourceReleased** event is triggered, the brush's **Draw** property is set to false.</span></span>

```cs
private void InteractionSourcePressed(InteractionSourcePressedEventArgs obj)
{
    if (obj.state.source.handedness == InteractionSourceHandedness.Right && obj.pressType == InteractionSourcePressType.Select)
    {
        Draw = true;
    }
}

private void InteractionSourceReleased(InteractionSourceReleasedEventArgs obj)
{
    if (obj.state.source.handedness == InteractionSourceHandedness.Right && obj.pressType == InteractionSourcePressType.Select)
    {
        Draw = false;
    }
}
```

<span data-ttu-id="de425-336">當 **Draw** 設定為 true 時，筆刷會在具現化的 Unity **LineRenderer** 中產生點。</span><span class="sxs-lookup"><span data-stu-id="de425-336">While **Draw** is set to true, the brush will generate points in an instantiated Unity **LineRenderer**.</span></span> <span data-ttu-id="de425-337">此預製專案的參考會保留在筆刷的 [ **筆觸預製專案** ] 欄位中。</span><span class="sxs-lookup"><span data-stu-id="de425-337">A reference to this prefab is kept in the brush's **Stroke Prefab** field.</span></span>

```cs
private IEnumerator DrawOverTime()
{
    // Get the position of the tip
    Vector3 lastPointPosition = tip.position;

    ...

    // Create a new brush stroke
    GameObject newStroke = Instantiate(strokePrefab);
    LineRenderer line = newStroke.GetComponent<LineRenderer>();
    newStroke.transform.position = startPosition;
    line.SetPosition(0, tip.position);
    float initialWidth = line.widthMultiplier;

    // Generate points in an instantiated Unity LineRenderer
    while (draw)
    {
        // Move the last point to the draw point position
        line.SetPosition(line.positionCount - 1, tip.position);
        line.material.color = colorPicker.SelectedColor;
        brushRenderer.material.color = colorPicker.SelectedColor;
        lastPointAddedTime = Time.unscaledTime;
        // Adjust the width between 1x and 2x width based on strength of trigger pull
        line.widthMultiplier = Mathf.Lerp(initialWidth, initialWidth * 2, width);

        if (Vector3.Distance(lastPointPosition, tip.position) > minPositionDelta || Time.unscaledTime > lastPointAddedTime + maxTimeDelta)
        {
            // Spawn a new point
            lastPointAddedTime = Time.unscaledTime;
            lastPointPosition = tip.position;
            line.positionCount += 1;
            line.SetPosition(line.positionCount - 1, lastPointPosition);
        }
        yield return null;
    }
}
```

<span data-ttu-id="de425-338">若要從色彩選擇器滾輪 UI 使用目前選取的色彩， **BrushController** 需要有 **ColorPickerWheel** 物件的參考。</span><span class="sxs-lookup"><span data-stu-id="de425-338">To use the currently selected color from the color picker wheel UI, **BrushController** needs to have a reference to the **ColorPickerWheel** object.</span></span> <span data-ttu-id="de425-339">因為 **BrushController** 預製專案在執行時間具現化為取代控制器，所以在執行時間必須設定任何對場景中物件的參考。</span><span class="sxs-lookup"><span data-stu-id="de425-339">Because the **BrushController** prefab is instantiated at runtime as a replacement controller, any references to objects in the scene will have to be set at runtime.</span></span> <span data-ttu-id="de425-340">在此情況下，我們會使用 **GameObject FindObjectOfType** 來找出 **ColorPickerWheel**：</span><span class="sxs-lookup"><span data-stu-id="de425-340">In this case we use **GameObject.FindObjectOfType** to locate the **ColorPickerWheel**:</span></span>

```cs
private void OnEnable()
{
    // Locate the ColorPickerWheel
    colorPicker = FindObjectOfType<ColorPickerWheel>();

    // Assign currently selected color to the brush’s material color
    brushRenderer.material.color = colorPicker.SelectedColor;
    ...
}
```

* <span data-ttu-id="de425-341">**儲存** 場景，然後按一下 [ **播放** ] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="de425-341">**Save** the scene and click the **play** button.</span></span> <span data-ttu-id="de425-342">您將可以使用右邊控制器上的 [選取] 按鈕來繪製線條和繪圖。</span><span class="sxs-lookup"><span data-stu-id="de425-342">You will be able to draw the lines and paint using the select button on the right-hand controller.</span></span>

## <a name="chapter-6---object-spawning-with-select-input"></a><span data-ttu-id="de425-343">第6章-使用 Select 輸入的物件產生</span><span class="sxs-lookup"><span data-stu-id="de425-343">Chapter 6 - Object spawning with Select input</span></span>

>[!VIDEO https://www.youtube.com/embed/z4IxyzFHP0U]

### <a name="objectives"></a><span data-ttu-id="de425-344">目標</span><span class="sxs-lookup"><span data-stu-id="de425-344">Objectives</span></span>

* <span data-ttu-id="de425-345">瞭解如何使用 Select 和抓住按鈕輸入事件</span><span class="sxs-lookup"><span data-stu-id="de425-345">Learn how to use Select and Grasp button input events</span></span>
* <span data-ttu-id="de425-346">瞭解如何將物件具現化</span><span class="sxs-lookup"><span data-stu-id="de425-346">Learn how to instantiate objects</span></span>

### <a name="instructions"></a><span data-ttu-id="de425-347">指示</span><span class="sxs-lookup"><span data-stu-id="de425-347">Instructions</span></span>

* <span data-ttu-id="de425-348">在 [ **專案** ] 面板的 [搜尋] 方塊中，輸入 **ObjectSpawner** 。</span><span class="sxs-lookup"><span data-stu-id="de425-348">In the **Project** panel, type **ObjectSpawner** in the search box.</span></span> <span data-ttu-id="de425-349">您也可以在資產/AppPrefabs/上找到它</span><span class="sxs-lookup"><span data-stu-id="de425-349">You can also find it under Assets/AppPrefabs/</span></span>
* <span data-ttu-id="de425-350">將 **ObjectSpawner** 預製專案拖曳到 [階層 **] 面板中** 。</span><span class="sxs-lookup"><span data-stu-id="de425-350">Drag the **ObjectSpawner** prefab into the **Hierarchy** panel.</span></span>
* <span data-ttu-id="de425-351">按一下 **[階層**] 面板中的 [ **ObjectSpawner** ]。</span><span class="sxs-lookup"><span data-stu-id="de425-351">Click **ObjectSpawner** in the **Hierarchy** panel.</span></span>
* <span data-ttu-id="de425-352">**ObjectSpawner** 有一個名為 **Color Source** 的欄位。</span><span class="sxs-lookup"><span data-stu-id="de425-352">**ObjectSpawner** has a field named **Color Source**.</span></span>
* <span data-ttu-id="de425-353">從 [階層 **] 面板中** ，將 [ **ColorPickerWheel** ] 參考拖曳到此欄位中。</span><span class="sxs-lookup"><span data-stu-id="de425-353">From the **Hierarchy** panel, drag the **ColorPickerWheel** reference into this field.</span></span>

    ![物件 Spawner 偵測器](images/mr213-objectspawnercolorpickerwheel-650px.jpg)

* <span data-ttu-id="de425-355">按一下 [階層 **] 面板中的 [** **ObjectSpawner** ] 預製專案。</span><span class="sxs-lookup"><span data-stu-id="de425-355">Click the **ObjectSpawner** prefab in the **Hierarchy** panel.</span></span>
* <span data-ttu-id="de425-356">在 [偵測 **器** ] 面板中，按兩下 [ **ObjectSpawner** 腳本] 以查看 Visual Studio 中的程式碼。</span><span class="sxs-lookup"><span data-stu-id="de425-356">In the **Inspector** panel, double click **ObjectSpawner** Script to see the code in Visual Studio.</span></span>

<span data-ttu-id="de425-357">**ObjectSpawner 腳本**</span><span class="sxs-lookup"><span data-stu-id="de425-357">**ObjectSpawner script**</span></span>

<span data-ttu-id="de425-358">**ObjectSpawner** 會將基本網格 (cube、球體、圓柱) 的複本具現化到空間中。</span><span class="sxs-lookup"><span data-stu-id="de425-358">The **ObjectSpawner** instantiates copies of a primitive mesh (cube, sphere, cylinder) into the space.</span></span> <span data-ttu-id="de425-359">偵測到 **InteractionSourcePressed** 時，它會檢查 handedness，如果是 **InteractionSourcePressType** ， **請選取** [事件]。</span><span class="sxs-lookup"><span data-stu-id="de425-359">When a **InteractionSourcePressed** is detected it checks the handedness and if it's an **InteractionSourcePressType.Grasp** or **InteractionSourcePressType.Select** event.</span></span>

<span data-ttu-id="de425-360">針對 **理解** 事件，它會將目前網格類型的索引遞增 (球體、cube、圓柱) </span><span class="sxs-lookup"><span data-stu-id="de425-360">For a **Grasp** event, it increments the index of current mesh type (sphere, cube, cylinder)</span></span>

```cs
private void InteractionSourcePressed(InteractionSourcePressedEventArgs obj)
{
    // Check handedness, see if it is left controller
    if (obj.state.source.handedness == handedness)
    {
        switch (obj.pressType)
        {
            // If it is Select button event, spawn object
            case InteractionSourcePressType.Select:
                if (state == StateEnum.Idle)
                {
                    // We've pressed the grasp - enter spawning state
                    state = StateEnum.Spawning;
                    SpawnObject();
                }
                break;

            // If it is Grasp button event
            case InteractionSourcePressType.Grasp:

                // Increment the index of current mesh type (sphere, cube, cylinder)
                meshIndex++;
                if (meshIndex >= NumAvailableMeshes)
                {
                    meshIndex = 0;
                }
                break;

            default:
                break;
        }
    }
}
```

<span data-ttu-id="de425-361">針對 **Select** 事件，在 **SpawnObject ( # B1** 中，會具現化新的物件，並將其具現化，並釋出到全世界。</span><span class="sxs-lookup"><span data-stu-id="de425-361">For a **Select** event, in **SpawnObject()**, a new object is instantiated, un-parented and released into the world.</span></span>

```cs
private void SpawnObject()
{
    // Instantiate the spawned object
    GameObject newObject = Instantiate(displayObject.gameObject, spawnParent);
    // Detach the newly spawned object
    newObject.transform.parent = null;
    // Reset the scale transform to 1
    scaleParent.localScale = Vector3.one;
    // Set its material color so its material gets instantiated
    newObject.GetComponent<Renderer>().material.color = colorSource.SelectedColor;
}
```

<span data-ttu-id="de425-362">**ObjectSpawner** 會使用 **ColorPickerWheel** 來設定顯示物件材質的色彩。</span><span class="sxs-lookup"><span data-stu-id="de425-362">The **ObjectSpawner** uses the **ColorPickerWheel** to set the color of the display object's material.</span></span> <span data-ttu-id="de425-363">產生的物件會被授與此材質的實例，以保留其色彩。</span><span class="sxs-lookup"><span data-stu-id="de425-363">Spawned objects are given an instance of this material so they will retain their color.</span></span>

* <span data-ttu-id="de425-364">**儲存** 場景，然後按一下 [ **播放** ] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="de425-364">**Save** the scene and click the **play** button.</span></span>

<span data-ttu-id="de425-365">您將可以使用 [理解] 按鈕來變更物件，並使用 [選取] 按鈕產生物件。</span><span class="sxs-lookup"><span data-stu-id="de425-365">You will be able to change the objects with the Grasp button and spawn objects with the Select button.</span></span>

## <a name="build-and-deploy-app-to-mixed-reality-portal"></a><span data-ttu-id="de425-366">建立應用程式並部署到混合實境入口</span><span class="sxs-lookup"><span data-stu-id="de425-366">Build and deploy app to Mixed Reality Portal</span></span>

* <span data-ttu-id="de425-367">在 Unity 中，選取 [ **File > Build Settings**]。</span><span class="sxs-lookup"><span data-stu-id="de425-367">In Unity, select **File > Build Settings**.</span></span>
* <span data-ttu-id="de425-368">按一下 [ **新增開啟的場景** ]，將目前的場景加入 **組建中的場景**。</span><span class="sxs-lookup"><span data-stu-id="de425-368">Click **Add Open Scenes** to add current scene to the **Scenes In Build**.</span></span>
* <span data-ttu-id="de425-369">按一下 [建置]。</span><span class="sxs-lookup"><span data-stu-id="de425-369">Click **Build**.</span></span>
* <span data-ttu-id="de425-370">建立名為 "App" 的 **新資料夾** 。</span><span class="sxs-lookup"><span data-stu-id="de425-370">Create a **New Folder** named "App".</span></span>
* <span data-ttu-id="de425-371">按一下 **應用程式** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="de425-371">Single click the **App** folder.</span></span>
* <span data-ttu-id="de425-372">按一下 [選擇資料夾]。</span><span class="sxs-lookup"><span data-stu-id="de425-372">Click **Select Folder**.</span></span>
* <span data-ttu-id="de425-373">當 Unity 完成時，將會出現檔案總管視窗。</span><span class="sxs-lookup"><span data-stu-id="de425-373">When Unity is done, a File Explorer window will appear.</span></span>
* <span data-ttu-id="de425-374">開啟 **應用程式** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="de425-374">Open the **App** folder.</span></span>
* <span data-ttu-id="de425-375">按兩下 [ **YourSceneName** ] Visual Studio 方案檔。</span><span class="sxs-lookup"><span data-stu-id="de425-375">Double click **YourSceneName.sln** Visual Studio Solution file.</span></span>
* <span data-ttu-id="de425-376">使用 Visual Studio 中的頂端工具列，將目標從 Debug 變更為 **Release** ，以及從 ARM 變更為 **X64**。</span><span class="sxs-lookup"><span data-stu-id="de425-376">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **X64**.</span></span>
* <span data-ttu-id="de425-377">按一下 [裝置] 按鈕旁邊的下拉箭號，然後選取 [ **本機電腦**]。</span><span class="sxs-lookup"><span data-stu-id="de425-377">Click on the drop-down arrow next to the Device button, and select **Local Machine**.</span></span>
* <span data-ttu-id="de425-378">按一下 [ **Debug-> 啟動但不** 在功能表中進行調試]，或按 **Ctrl + F5**。</span><span class="sxs-lookup"><span data-stu-id="de425-378">Click **Debug -> Start Without debugging** in the menu or press **Ctrl + F5**.</span></span>

<span data-ttu-id="de425-379">現在，應用程式已建立並安裝在混合實境入口中。</span><span class="sxs-lookup"><span data-stu-id="de425-379">Now the app is built and installed in Mixed Reality Portal.</span></span> <span data-ttu-id="de425-380">您可以透過混合實境入口中的 [開始] 功能表再次啟動它。</span><span class="sxs-lookup"><span data-stu-id="de425-380">You can launch it again through Start menu in Mixed Reality Portal.</span></span>

## <a name="advanced-design---brush-tools-with-radial-layout"></a><span data-ttu-id="de425-381">先進的設計-具有放射狀配置的筆刷工具</span><span class="sxs-lookup"><span data-stu-id="de425-381">Advanced design - Brush tools with radial layout</span></span>

![MixedReality213 Main](images/mr213-main-600px.jpg)

<span data-ttu-id="de425-383">在本章中，您將瞭解如何使用自訂筆刷工具集合來取代預設的動作控制器模型。</span><span class="sxs-lookup"><span data-stu-id="de425-383">In this chapter, you will learn how to replace the default motion controller model with a custom brush tool collection.</span></span> <span data-ttu-id="de425-384">針對您的參考，您可以在 [**場景**] 資料夾下找到完成的場景 **MixedReality213Advanced** 。</span><span class="sxs-lookup"><span data-stu-id="de425-384">For your reference, you can find the completed scene **MixedReality213Advanced** under **Scenes** folder.</span></span>

### <a name="instructions"></a><span data-ttu-id="de425-385">指示</span><span class="sxs-lookup"><span data-stu-id="de425-385">Instructions</span></span>

* <span data-ttu-id="de425-386">在 [ **專案** ] 面板的 [搜尋] 方塊中，輸入 **BrushSelector** 。</span><span class="sxs-lookup"><span data-stu-id="de425-386">In the **Project** panel, type **BrushSelector** in the search box .</span></span> <span data-ttu-id="de425-387">您也可以在資產/AppPrefabs/上找到它</span><span class="sxs-lookup"><span data-stu-id="de425-387">You can also find it under Assets/AppPrefabs/</span></span>
* <span data-ttu-id="de425-388">將 **BrushSelector** 預製專案拖曳到 [階層 **] 面板中** 。</span><span class="sxs-lookup"><span data-stu-id="de425-388">Drag the **BrushSelector** prefab into the **Hierarchy** panel.</span></span>
* <span data-ttu-id="de425-389">針對組織，建立稱為 **筆刷** 的空白 GameObject</span><span class="sxs-lookup"><span data-stu-id="de425-389">For organization, create an empty GameObject called **Brushes**</span></span>
* <span data-ttu-id="de425-390">將下列 prefabs 從 [ **專案** ] 面板拖曳至 **筆刷**</span><span class="sxs-lookup"><span data-stu-id="de425-390">Drag following prefabs from the **Project** panel into **Brushes**</span></span>
    * <span data-ttu-id="de425-391">資產/AppPrefabs/**BrushFat**</span><span class="sxs-lookup"><span data-stu-id="de425-391">Assets/AppPrefabs/**BrushFat**</span></span>
    * <span data-ttu-id="de425-392">資產/AppPrefabs/**BrushThin**</span><span class="sxs-lookup"><span data-stu-id="de425-392">Assets/AppPrefabs/**BrushThin**</span></span>
    * <span data-ttu-id="de425-393">資產/AppPrefabs/**橡皮擦**</span><span class="sxs-lookup"><span data-stu-id="de425-393">Assets/AppPrefabs/**Eraser**</span></span>
    * <span data-ttu-id="de425-394">資產/AppPrefabs/**MarkerFat**</span><span class="sxs-lookup"><span data-stu-id="de425-394">Assets/AppPrefabs/**MarkerFat**</span></span>
    * <span data-ttu-id="de425-395">資產/AppPrefabs/**MarkerThin**</span><span class="sxs-lookup"><span data-stu-id="de425-395">Assets/AppPrefabs/**MarkerThin**</span></span>
    * <span data-ttu-id="de425-396">資產/AppPrefabs/**鉛筆**</span><span class="sxs-lookup"><span data-stu-id="de425-396">Assets/AppPrefabs/**Pencil**</span></span>

    ![筆刷](images/mixedreality213-brushes-250px.png)

* <span data-ttu-id="de425-398">按一下 **[階層**] 面板中的 [ **MotionControllers** 預製專案]。</span><span class="sxs-lookup"><span data-stu-id="de425-398">Click **MotionControllers** prefab in the **Hierarchy** panel.</span></span>
* <span data-ttu-id="de425-399">在 [偵測 **器**] 面板中，取消核取 [**移動控制器] 視覺化檢視** 上的 [**永遠使用替代模型**]</span><span class="sxs-lookup"><span data-stu-id="de425-399">In the **Inspector** panel, uncheck **Always Use Alternate Right Model** on the **Motion Controller Visualizer**</span></span>
* <span data-ttu-id="de425-400">**在 [階層**] 面板中，按一下 [ **BrushSelector** ]</span><span class="sxs-lookup"><span data-stu-id="de425-400">In the **Hierarchy** panel, click **BrushSelector**</span></span>
* <span data-ttu-id="de425-401">**BrushSelector** 有一個名為 **ColorPicker** 的欄位</span><span class="sxs-lookup"><span data-stu-id="de425-401">**BrushSelector** has a field named **ColorPicker**</span></span>
* <span data-ttu-id="de425-402">從 [階層] 面板中，將 [ **ColorPickerWheel** ] 拖曳至 [偵測 **器** **] 面板中** 的 [ **ColorPicker** ] 欄位。</span><span class="sxs-lookup"><span data-stu-id="de425-402">From the **Hierarchy** panel, drag the **ColorPickerWheel** into **ColorPicker** field in the **Inspector** panel.</span></span>

    ![將 ColorPickerWheel 指派給筆刷選取器](images/mr213-brushselector-500px.jpg)

* <span data-ttu-id="de425-404">在 [ **階層** ] 面板中，選取 [ **BrushSelector** 預製專案] 底下的 **功能表** 物件。</span><span class="sxs-lookup"><span data-stu-id="de425-404">In the **Hierarchy** panel, under **BrushSelector** prefab, select the **Menu** object.</span></span>
* <span data-ttu-id="de425-405">在 [偵測 **器** ] 面板的 [ **LineObjectCollection** ] 元件底下，開啟 [ **物件** 陣列] 下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="de425-405">In the **Inspector** panel, under the **LineObjectCollection** component, open the **Objects** array dropdown.</span></span> <span data-ttu-id="de425-406">您會看到6個空的插槽。</span><span class="sxs-lookup"><span data-stu-id="de425-406">You will see 6 empty slots.</span></span>
* <span data-ttu-id="de425-407">從 [階層 **] 面板中** ，將 [ **筆刷** ] GameObject 下的每個 prefabs 以任何順序拖曳至這些位置。</span><span class="sxs-lookup"><span data-stu-id="de425-407">From the **Hierarchy** panel, drag each of the prefabs parented under the **Brushes** GameObject into these slots in any order.</span></span> <span data-ttu-id="de425-408"> (確定您是從場景拖曳 prefabs，而不是從專案資料夾中的 prefabs。 ) </span><span class="sxs-lookup"><span data-stu-id="de425-408">(Make sure you're dragging the prefabs from the scene, not the prefabs in the project folder.)</span></span>

![筆刷選取器](images/mr213-brushselectorbrushes-700px.jpg)

<span data-ttu-id="de425-410">**BrushSelector 預製專案**</span><span class="sxs-lookup"><span data-stu-id="de425-410">**BrushSelector prefab**</span></span>

<span data-ttu-id="de425-411">因為 **BrushSelector** 會繼承 **AttachToController**，所以它會在 [偵測 **器**] 面板中顯示 **Handedness** 和 **元素** 選項。</span><span class="sxs-lookup"><span data-stu-id="de425-411">Since the **BrushSelector** inherits **AttachToController**, it shows **Handedness** and **Element** options in the **Inspector** panel.</span></span> <span data-ttu-id="de425-412">我們選取了 [ **右** ]，並 **指向** [順向]，將筆刷工具附加至右邊控制器。</span><span class="sxs-lookup"><span data-stu-id="de425-412">We selected **Right** and **Pointing Pose** to attach brush tools to the right hand controller with forward direction.</span></span>

<span data-ttu-id="de425-413">**BrushSelector** 會使用兩個公用程式：</span><span class="sxs-lookup"><span data-stu-id="de425-413">The **BrushSelector** makes use of two utilities:</span></span>

* <span data-ttu-id="de425-414">**橢圓形**：用來沿著橢圓形圖形來產生空間中的點。</span><span class="sxs-lookup"><span data-stu-id="de425-414">**Ellipse**: used to generate points in space along an ellipse shape.</span></span>
* <span data-ttu-id="de425-415">**LineObjectCollection**：使用任何線條類別產生的點來散發物件 (例如橢圓形) 。</span><span class="sxs-lookup"><span data-stu-id="de425-415">**LineObjectCollection**: distributes objects using the points generated by any Line class (eg, Ellipse).</span></span> <span data-ttu-id="de425-416">這是我們將用來沿著橢圓形圖形來放置筆刷的內容。</span><span class="sxs-lookup"><span data-stu-id="de425-416">This is what we'll be using to place our brushes along the Ellipse shape.</span></span>

<span data-ttu-id="de425-417">結合之後，這些公用程式可以用來建立放射狀功能表。</span><span class="sxs-lookup"><span data-stu-id="de425-417">When combined, these utilities can be used to create a radial menu.</span></span>

<span data-ttu-id="de425-418">**LineObjectCollection 腳本**</span><span class="sxs-lookup"><span data-stu-id="de425-418">**LineObjectCollection script**</span></span>

<span data-ttu-id="de425-419">**LineObjectCollection** 具有控制項的大小、位置和旋轉，以及沿著線條分佈的物件。</span><span class="sxs-lookup"><span data-stu-id="de425-419">**LineObjectCollection** has controls for the size, position and rotation of objects distributed along its line.</span></span> <span data-ttu-id="de425-420">這對於建立星形功能表（例如筆刷選取器）很有用。</span><span class="sxs-lookup"><span data-stu-id="de425-420">This is useful for creating radial menus like the brush selector.</span></span> <span data-ttu-id="de425-421">若要建立筆刷的外觀，而不會在接近中心選取的位置時相應增加，則 **ObjectScale** 曲線會尖峰于中間，並在邊緣 tapers。</span><span class="sxs-lookup"><span data-stu-id="de425-421">To create the appearance of brushes that scale up from nothing as they approach the center selected position, the **ObjectScale** curve peaks in the center and tapers off at the edges.</span></span>

<span data-ttu-id="de425-422">**BrushSelector 腳本**</span><span class="sxs-lookup"><span data-stu-id="de425-422">**BrushSelector script**</span></span>

<span data-ttu-id="de425-423">在 **BrushSelector** 的案例中，我們選擇使用程式動畫。</span><span class="sxs-lookup"><span data-stu-id="de425-423">In the case of the **BrushSelector**, we've chosen to use procedural animation.</span></span> <span data-ttu-id="de425-424">首先， **LineObjectCollection** 腳本會將筆刷模型散發在橢圓形中。</span><span class="sxs-lookup"><span data-stu-id="de425-424">First, brush models are distributed in an ellipse by the **LineObjectCollection** script.</span></span> <span data-ttu-id="de425-425">然後，每個筆刷都會根據選取專案，負責 **維護其在** 使用者手中的位置（視選取專案而定）。</span><span class="sxs-lookup"><span data-stu-id="de425-425">Then, each brush is responsible for maintaining its position in the user's hand based on its **DisplayMode** value, which changes based on the selection.</span></span> <span data-ttu-id="de425-426">我們選擇了程式性方法，因為當使用者選取筆刷時，筆刷位置轉換會中斷的機率很高。</span><span class="sxs-lookup"><span data-stu-id="de425-426">We chose a procedural approach because of the high probability of brush position transitions being interrupted as the user selects brushes.</span></span> <span data-ttu-id="de425-427">Mecanim 動畫可以正常地處理中斷情形，但通常比簡單的 Lerp 作業更複雜。</span><span class="sxs-lookup"><span data-stu-id="de425-427">Mecanim animations can handle interruptions gracefully, but it tends to be more complicated than a simple Lerp operation.</span></span>

<span data-ttu-id="de425-428">**BrushSelector** 會使用這兩者的組合。</span><span class="sxs-lookup"><span data-stu-id="de425-428">**BrushSelector** uses a combination of both.</span></span> <span data-ttu-id="de425-429">當偵測到觸控板輸入時，筆刷選項會變成可見，並沿著放射狀功能表向上擴充。</span><span class="sxs-lookup"><span data-stu-id="de425-429">When touchpad input is detected, brush options become visible and scale up along the radial menu.</span></span> <span data-ttu-id="de425-430">在超時期間 (，表示使用者已進行選取) 筆刷選項調整大小，只留下選取的筆刷。</span><span class="sxs-lookup"><span data-stu-id="de425-430">After a timeout period (which indicates that the user has made a selection) the brush options scale down again, leaving only the selected brush.</span></span>

<span data-ttu-id="de425-431">**視覺化觸控板輸入**</span><span class="sxs-lookup"><span data-stu-id="de425-431">**Visualizing touchpad input**</span></span>

<span data-ttu-id="de425-432">即使已完全取代控制器模型，在原始模型輸入上顯示輸入可能會很有説明。</span><span class="sxs-lookup"><span data-stu-id="de425-432">Even in cases where the controller model has been completely replaced, it can be helpful to show input on the original model inputs.</span></span> <span data-ttu-id="de425-433">這有助於實現使用者的動作。</span><span class="sxs-lookup"><span data-stu-id="de425-433">This helps to ground the user's actions in reality.</span></span> <span data-ttu-id="de425-434">針對 **BrushSelector** ，我們選擇讓觸控板在收到輸入時短暫顯示。</span><span class="sxs-lookup"><span data-stu-id="de425-434">For the **BrushSelector** we've chosen to make the touchpad briefly visible when the input is received.</span></span> <span data-ttu-id="de425-435">這是藉由從控制器中取出觸控板元素、將其材質取代為自訂材質來完成，然後根據收到的前次觸控板輸入將漸層套用至該材質的色彩。</span><span class="sxs-lookup"><span data-stu-id="de425-435">This was done by retrieving the Touchpad element from the controller, replacing its material with a custom material, then applying a gradient to that material's color based on the last time touchpad input was received.</span></span>

```cs
protected override void OnAttachToController()
{
    // Turn off the default controller's renderers
    controller.SetRenderersVisible(false);

    // Get the touchpad and assign our custom material to it
    Transform touchpad;
    if (controller.TryGetElement(MotionControllerInfo.ControllerElementEnum.Touchpad, out touchpad))
    {
        touchpadRenderer = touchpad.GetComponentInChildren<MeshRenderer>();
        originalTouchpadMaterial = touchpadRenderer.material;
        touchpadRenderer.material = touchpadMaterial;
        touchpadRenderer.enabled = true;
    }

    // Subscribe to input now that we're parented under the controller
    InteractionManager.InteractionSourceUpdated += InteractionSourceUpdated;
}

private void Update()
{
    ...
    // Update our touchpad material
    Color glowColor = touchpadColor.Evaluate((Time.unscaledTime - touchpadTouchTime) / touchpadGlowLossTime);
    touchpadMaterial.SetColor("_EmissionColor", glowColor);
    touchpadMaterial.SetColor("_Color", glowColor);
    ...
}
```

<span data-ttu-id="de425-436">**使用觸控板輸入的筆刷工具選項**</span><span class="sxs-lookup"><span data-stu-id="de425-436">**Brush tool selection with touchpad input**</span></span>

<span data-ttu-id="de425-437">當筆刷選取器偵測到觸控板的已按下輸入時，它會檢查輸入的位置，以判斷其是否為左方或右方。</span><span class="sxs-lookup"><span data-stu-id="de425-437">When the brush selector detects touchpad's pressed input, it checks the position of the input to determine if it was to the left or right.</span></span>

<span data-ttu-id="de425-438">**使用 selectPressedAmount 的筆觸粗細**</span><span class="sxs-lookup"><span data-stu-id="de425-438">**Stroke thickness with selectPressedAmount**</span></span>

<span data-ttu-id="de425-439">而不是 **InteractionSourcePressType。請選取** **InteractionSourcePressed ( # B1** 中的事件，您可以透過 **selectPressedAmount** 取得按下數量的類比值。</span><span class="sxs-lookup"><span data-stu-id="de425-439">Instead of the **InteractionSourcePressType.Select** event in the **InteractionSourcePressed()**, you can get the analog value of the pressed amount through **selectPressedAmount**.</span></span> <span data-ttu-id="de425-440">您可以在 **InteractionSourceUpdated ( # B1** 中取出此值。</span><span class="sxs-lookup"><span data-stu-id="de425-440">This value can be retrieved in **InteractionSourceUpdated()**.</span></span>

```cs
private void InteractionSourceUpdated(InteractionSourceUpdatedEventArgs obj)
{
    if (obj.state.source.handedness == handedness)
    {
        if (obj.state.touchpadPressed)
        {
            // Check which side we clicked
            if (obj.state.touchpadPosition.x < 0)
            {
                currentAction = SwipeEnum.Left;
            }
            else
            {
                currentAction = SwipeEnum.Right;
            }

            // Ping the touchpad material so it gets bright
            touchpadTouchTime = Time.unscaledTime;
        }

        if (activeBrush != null)
        {
            // If the pressed amount is greater than our threshold, draw
            if (obj.state.selectPressedAmount >= selectPressedDrawThreshold)
            {
                activeBrush.Draw = true;
                activeBrush.Width = ProcessSelectPressedAmount(obj.state.selectPressedAmount);
            }
            else
            {
                // Otherwise, stop drawing
                activeBrush.Draw = false;
                selectPressedSmooth = 0f;
            }
        }
    }
}
```

<span data-ttu-id="de425-441">**橡皮擦腳本**</span><span class="sxs-lookup"><span data-stu-id="de425-441">**Eraser script**</span></span>

<span data-ttu-id="de425-442">**橡皮擦** 是一種特殊類型的筆刷，會覆寫基底 **筆刷** 的 **DrawOverTime ( # B1** 函數。</span><span class="sxs-lookup"><span data-stu-id="de425-442">**Eraser** is a special type of brush that overrides the base **Brush**'s **DrawOverTime()** function.</span></span> <span data-ttu-id="de425-443">當 Draw 為 true 時，橡皮擦會檢查其提示是否與任何現有的筆刷筆劃相交。</span><span class="sxs-lookup"><span data-stu-id="de425-443">While Draw is true, the eraser checks to see if its tip intersects with any existing brush strokes.</span></span> <span data-ttu-id="de425-444">如果有，則會將它們加入至要壓縮和刪除的佇列。</span><span class="sxs-lookup"><span data-stu-id="de425-444">If it does, they are added to a queue to be shrunk down and deleted.</span></span>

## <a name="advanced-design---teleportation-and-locomotion"></a><span data-ttu-id="de425-445">Advanced design-遙傳和 locomotion</span><span class="sxs-lookup"><span data-stu-id="de425-445">Advanced design - Teleportation and locomotion</span></span>

<span data-ttu-id="de425-446">如果您想要允許使用者透過遙傳使用操縱杆來移動場景，請使用 **MixedRealityCameraParent** 而不是 **MixedRealityCamera**。</span><span class="sxs-lookup"><span data-stu-id="de425-446">If you want to allow the user to move around the scene with teleportation using thumbstick, use **MixedRealityCameraParent** instead of **MixedRealityCamera**.</span></span> <span data-ttu-id="de425-447">您也需要新增 **InputManager** 和 **DefaultCursor**。</span><span class="sxs-lookup"><span data-stu-id="de425-447">You also need to add **InputManager** and **DefaultCursor**.</span></span> <span data-ttu-id="de425-448">因為 **MixedRealityCameraParent** 已經將 **MotionControllers** 和 **界限** 包含為子元件，所以您應該移除現有的 **MotionControllers** 和 **環境** 預製專案。</span><span class="sxs-lookup"><span data-stu-id="de425-448">Since **MixedRealityCameraParent** already includes **MotionControllers** and **Boundary** as child components, you should remove existing **MotionControllers** and **Environment** prefab.</span></span>

### <a name="instructions"></a><span data-ttu-id="de425-449">指示</span><span class="sxs-lookup"><span data-stu-id="de425-449">Instructions</span></span>

* <span data-ttu-id="de425-450">**在 [階層**] 面板中，刪除 [ **MixedRealityCamera**]、[**環境**] 和 [ **MotionControllers** ]</span><span class="sxs-lookup"><span data-stu-id="de425-450">In the **Hierarchy** panel, delete **MixedRealityCamera**, **Environment** and **MotionControllers**</span></span>
* <span data-ttu-id="de425-451">在 [ **專案] 面板** 中，搜尋下列 prefabs，並將 **其拖曳** 到 [階層] 面板中：</span><span class="sxs-lookup"><span data-stu-id="de425-451">From the **Project panel**, search and drag the following prefabs into the **Hierarchy** panel:</span></span>
    * <span data-ttu-id="de425-452">資產/AppPrefabs/Input/Prefabs/**MixedRealityCameraParent**</span><span class="sxs-lookup"><span data-stu-id="de425-452">Assets/AppPrefabs/Input/Prefabs/**MixedRealityCameraParent**</span></span>
    * <span data-ttu-id="de425-453">資產/AppPrefabs/Input/Prefabs/**InputManager**</span><span class="sxs-lookup"><span data-stu-id="de425-453">Assets/AppPrefabs/Input/Prefabs/**InputManager**</span></span>
    * <span data-ttu-id="de425-454">資產/AppPrefabs/Input/Prefabs/Cursor/**DefaultCursor**</span><span class="sxs-lookup"><span data-stu-id="de425-454">Assets/AppPrefabs/Input/Prefabs/Cursor/**DefaultCursor**</span></span>

    ![混合實境相機父系](images/mr213-cameraparent-300px.png)

* <span data-ttu-id="de425-456">**在 [階層**] 面板中，按一下 [**輸入管理員**]</span><span class="sxs-lookup"><span data-stu-id="de425-456">In the **Hierarchy** panel, click **Input Manager**</span></span>
* <span data-ttu-id="de425-457">在 [偵測 **器** ] 面板中，向下滾動至 **簡單的單一指標選取器** 區段</span><span class="sxs-lookup"><span data-stu-id="de425-457">In the **Inspector** panel, scroll down to the **Simple Single Pointer Selector** section</span></span>
* <span data-ttu-id="de425-458">從 [ **階層** ] 面板中，將 [ **DefaultCursor** ] 拖曳至 [ **游標** ] 欄位</span><span class="sxs-lookup"><span data-stu-id="de425-458">From the **Hierarchy** panel, drag **DefaultCursor** into **Cursor** field</span></span>

    ![指派 DefaultCursor](images/mr213-defaultcursor-500px.png)

* <span data-ttu-id="de425-460">**儲存** 場景，然後按一下 [ **播放** ] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="de425-460">**Save** the scene and click the **play** button.</span></span> <span data-ttu-id="de425-461">您將能夠使用操縱杆來旋轉左右或傳送。</span><span class="sxs-lookup"><span data-stu-id="de425-461">You will be able to use the thumbstick to rotate left/right or teleport.</span></span>

## <a name="the-end"></a><span data-ttu-id="de425-462">結束</span><span class="sxs-lookup"><span data-stu-id="de425-462">The end</span></span>

<span data-ttu-id="de425-463">這就是本教學課程的結尾！</span><span class="sxs-lookup"><span data-stu-id="de425-463">And that's the end of this tutorial!</span></span> <span data-ttu-id="de425-464">您已了解︰</span><span class="sxs-lookup"><span data-stu-id="de425-464">You learned:</span></span>

* <span data-ttu-id="de425-465">如何在 Unity 的遊戲模式和執行時間中使用移動控制器模型。</span><span class="sxs-lookup"><span data-stu-id="de425-465">How to work with motion controller models in Unity's game mode and runtime.</span></span>
* <span data-ttu-id="de425-466">如何使用不同類型的按鈕事件和其應用程式。</span><span class="sxs-lookup"><span data-stu-id="de425-466">How to use different types of button events and their applications.</span></span>
* <span data-ttu-id="de425-467">如何覆迭控制器頂端的 UI 元素或完全自訂。</span><span class="sxs-lookup"><span data-stu-id="de425-467">How to overlay UI elements on top of the controller or fully customize it.</span></span>

<span data-ttu-id="de425-468">您現在已準備好開始使用移動控制器來建立您自己的沉浸式體驗！</span><span class="sxs-lookup"><span data-stu-id="de425-468">You are now ready to start creating your own immersive experience with motion controllers!</span></span>

## <a name="completed-scenes"></a><span data-ttu-id="de425-469">完成的場景</span><span class="sxs-lookup"><span data-stu-id="de425-469">Completed scenes</span></span>

* <span data-ttu-id="de425-470">在 Unity 的 [ **專案** ] 面板中，按一下 [ **場景** ] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="de425-470">In Unity's **Project** panel click on the **Scenes** folder.</span></span>
* <span data-ttu-id="de425-471">您會發現兩個 Unity 場景 **MixedReality213** 和 **MixedReality213Advanced**。</span><span class="sxs-lookup"><span data-stu-id="de425-471">You will find two Unity scenes **MixedReality213** and **MixedReality213Advanced**.</span></span>
    * <span data-ttu-id="de425-472">**MixedReality213**：已完成場景與單一筆刷</span><span class="sxs-lookup"><span data-stu-id="de425-472">**MixedReality213**: Completed scene with single brush</span></span>
    * <span data-ttu-id="de425-473">**MixedReality213Advanced**：已完成場景，具有具有 select 按鈕的按量範例的多筆刷</span><span class="sxs-lookup"><span data-stu-id="de425-473">**MixedReality213Advanced**: Completed scene with multiple brush with select button's press amount example</span></span>

## <a name="see-also"></a><span data-ttu-id="de425-474">另請參閱</span><span class="sxs-lookup"><span data-stu-id="de425-474">See also</span></span>

* [<span data-ttu-id="de425-475">MR 輸入213專案檔</span><span class="sxs-lookup"><span data-stu-id="de425-475">MR Input 213 project files</span></span>](https://github.com/Microsoft/MixedReality213)
* [<span data-ttu-id="de425-476">混合現實工具組-移動控制器測試場景</span><span class="sxs-lookup"><span data-stu-id="de425-476">Mixed Reality Toolkit - Motion Controller Test scene</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/Input/Scenes)
* [<span data-ttu-id="de425-477">混合現實工具組-抓取機制</span><span class="sxs-lookup"><span data-stu-id="de425-477">Mixed Reality Toolkit - Grab Mechanics</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/MotionControllers-GrabMechanics)
* [<span data-ttu-id="de425-478">移動控制器開發指導方針</span><span class="sxs-lookup"><span data-stu-id="de425-478">Motion controller development guidelines</span></span>](../design/motion-controllers.md)