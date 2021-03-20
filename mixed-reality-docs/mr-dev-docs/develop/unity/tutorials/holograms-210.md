---
title: HoloLens (第1代) 輸入 210-注視
description: 遵循此程式碼逐步解說，使用 Unity、Visual Studio 和 HoloLens 來瞭解注視概念的詳細資料。
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit、mixedrealitytoolkit、mixedrealitytoolkit-unity、學術、教學課程、注視、HoloLens、Mixed Reality 學院、unity、Mixed reality 耳機、windows Mixed Reality 耳機、虛擬實境耳機、Windows 10
ms.openlocfilehash: 99c0d2ae00416f5d26e99e6d7d00c73ea07e5fb3
ms.sourcegitcommit: 35bd43624be33afdb1bf6ba4ddbe36d268eb9bda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/20/2021
ms.locfileid: "104730325"
---
# <a name="hololens-1st-gen-input-210-gaze"></a><span data-ttu-id="521cf-104">HoloLens (第1代) 輸入210：注視</span><span class="sxs-lookup"><span data-stu-id="521cf-104">HoloLens (1st gen) Input 210: Gaze</span></span>

>[!NOTE]
><span data-ttu-id="521cf-105">混合實境學院教學課程的設計是以 HoloLens (第 1 代) 和混合實境沉浸式頭戴裝置為準。</span><span class="sxs-lookup"><span data-stu-id="521cf-105">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="521cf-106">因此，對於仍在尋找這些裝置開發指引的開發人員而言，我們覺得這些教學課程很重要。</span><span class="sxs-lookup"><span data-stu-id="521cf-106">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="521cf-107">這些教學課程 **_不會_** 使用用於 HoloLens 2 的最新工具組或互動進行更新。</span><span class="sxs-lookup"><span data-stu-id="521cf-107">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="521cf-108">系統會保留這些資訊，以繼續在支援的裝置上運作。</span><span class="sxs-lookup"><span data-stu-id="521cf-108">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="521cf-109">已針對 HoloLens 2 公佈[一系列新的教學課程](./mr-learning-base-01.md)。</span><span class="sxs-lookup"><span data-stu-id="521cf-109">[A new series of tutorials](./mr-learning-base-01.md) has been posted for HoloLens 2.</span></span>

<span data-ttu-id="521cf-110">[注視](../../../design/gaze-and-commit.md) 是輸入的第一種形式，會顯示使用者的意圖和認知。</span><span class="sxs-lookup"><span data-stu-id="521cf-110">[Gaze](../../../design/gaze-and-commit.md) is the first form of input and reveals the user's intent and awareness.</span></span> <span data-ttu-id="521cf-111">MR 輸入 210 (也稱為 Project Explorer) 是 Windows Mixed Reality 的注視相關概念深入探討。</span><span class="sxs-lookup"><span data-stu-id="521cf-111">MR Input 210 (aka Project Explorer) is a deep dive into gaze-related concepts for Windows Mixed Reality.</span></span> <span data-ttu-id="521cf-112">我們會將內容感知新增至游標和全像投影，以充分利用您的應用程式對使用者的注視有何認識。</span><span class="sxs-lookup"><span data-stu-id="521cf-112">We will be adding contextual awareness to our cursor and holograms, taking full advantage of what your app knows about the user's gaze.</span></span>

>[!VIDEO https://www.youtube.com/embed/yKAttGduVp0]

<span data-ttu-id="521cf-113">我們在這裡有一個很好用的太空人，可協助您瞭解一些概念。</span><span class="sxs-lookup"><span data-stu-id="521cf-113">We have a friendly astronaut here to help you learn gaze concepts.</span></span> <span data-ttu-id="521cf-114">在 [MR 基本的 101](../../../develop/unity/tutorials/holograms-101.md)中，我們有一個簡單的游標，也就是您的注視。</span><span class="sxs-lookup"><span data-stu-id="521cf-114">In [MR Basics 101](../../../develop/unity/tutorials/holograms-101.md), we had a simple cursor that just followed your gaze.</span></span> <span data-ttu-id="521cf-115">今天，我們要將一個步驟移至簡單資料指標之外：</span><span class="sxs-lookup"><span data-stu-id="521cf-115">Today we're moving a step beyond the simple cursor:</span></span>

* <span data-ttu-id="521cf-116">我們會將游標和我們的全像是注視：這兩者都會根據使用者的查看位置，或 *使用者不在尋找的* 位置而變更。</span><span class="sxs-lookup"><span data-stu-id="521cf-116">We're making the cursor and our holograms gaze-aware: both will change based on where the user is looking - or where the user is *not* looking.</span></span> <span data-ttu-id="521cf-117">這樣就能感知它們的內容。</span><span class="sxs-lookup"><span data-stu-id="521cf-117">This makes them context-aware.</span></span>
* <span data-ttu-id="521cf-118">我們會將意見反應新增至游標和全像影像，以提供使用者更多有關目標的內容。</span><span class="sxs-lookup"><span data-stu-id="521cf-118">We will add feedback to our cursor and holograms to give the user more context on what is being targeted.</span></span> <span data-ttu-id="521cf-119">這種意見反應可以是音訊和視覺效果。</span><span class="sxs-lookup"><span data-stu-id="521cf-119">This feedback can be audio and visual.</span></span>
* <span data-ttu-id="521cf-120">我們將為您示範以協助使用者達到較小目標的目標技術。</span><span class="sxs-lookup"><span data-stu-id="521cf-120">We'll show you targeting techniques to help users hit smaller targets.</span></span>
* <span data-ttu-id="521cf-121">我們將示範如何使用方向指標將使用者的注意力吸引到您的全像投影。</span><span class="sxs-lookup"><span data-stu-id="521cf-121">We'll show you how to draw the user's attention to your holograms with a directional indicator.</span></span>
* <span data-ttu-id="521cf-122">我們將會教您如何在您的世界各地，讓您的隨用隨之移動。</span><span class="sxs-lookup"><span data-stu-id="521cf-122">We'll teach you techniques to take your holograms with the user as she moves around in your world.</span></span>

>[!IMPORTANT]
><span data-ttu-id="521cf-123">下列各章節中內嵌的影片是使用較舊版本的 Unity 和混合現實工具組所記錄。</span><span class="sxs-lookup"><span data-stu-id="521cf-123">The videos embedded in each of the chapters below were recorded using an older version of Unity and the Mixed Reality Toolkit.</span></span> <span data-ttu-id="521cf-124">雖然逐步指示是正確且最新的，但您可能會在相對應的影片中看到已過期的腳本和視覺效果。</span><span class="sxs-lookup"><span data-stu-id="521cf-124">While the step-by-step instructions are accurate and current, you may see scripts and visuals in the corresponding videos that are out-of-date.</span></span> <span data-ttu-id="521cf-125">影片仍隨附于 posterity，因為所涵蓋的概念仍然適用。</span><span class="sxs-lookup"><span data-stu-id="521cf-125">The videos remain included for posterity and because the concepts covered still apply.</span></span>

## <a name="device-support"></a><span data-ttu-id="521cf-126">裝置支援</span><span class="sxs-lookup"><span data-stu-id="521cf-126">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="521cf-127">課程</span><span class="sxs-lookup"><span data-stu-id="521cf-127">Course</span></span></th><th style="width:150px"> <span data-ttu-id="521cf-128"><a href="/hololens/hololens1-hardware">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="521cf-128"><a href="/hololens/hololens1-hardware">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="521cf-129"><a href="../../../discover/immersive-headset-hardware-details.md">沉浸式頭戴裝置</a></span><span class="sxs-lookup"><span data-stu-id="521cf-129"><a href="../../../discover/immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="521cf-130">MR Input 210：注視</span><span class="sxs-lookup"><span data-stu-id="521cf-130">MR Input 210: Gaze</span></span></td><td style="text-align: center;"> <span data-ttu-id="521cf-131">✔️</span><span class="sxs-lookup"><span data-stu-id="521cf-131">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="521cf-132">✔️</span><span class="sxs-lookup"><span data-stu-id="521cf-132">✔️</span></span></td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="521cf-133">在您開始使用 Intune 之前</span><span class="sxs-lookup"><span data-stu-id="521cf-133">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="521cf-134">必要條件</span><span class="sxs-lookup"><span data-stu-id="521cf-134">Prerequisites</span></span>

* <span data-ttu-id="521cf-135">[已安裝正確工具](../../../develop/install-the-tools.md)的 Windows 10 電腦。</span><span class="sxs-lookup"><span data-stu-id="521cf-135">A Windows 10 PC configured with the correct [tools installed](../../../develop/install-the-tools.md).</span></span>
* <span data-ttu-id="521cf-136">一些基本的 c # 程式設計功能。</span><span class="sxs-lookup"><span data-stu-id="521cf-136">Some basic C# programming ability.</span></span>
* <span data-ttu-id="521cf-137">您應已完成 [MR 基本的 101](../../../develop/unity/tutorials/holograms-101.md)。</span><span class="sxs-lookup"><span data-stu-id="521cf-137">You should have completed [MR Basics 101](../../../develop/unity/tutorials/holograms-101.md).</span></span>
* <span data-ttu-id="521cf-138">[針對開發設定](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)的 HoloLens 裝置。</span><span class="sxs-lookup"><span data-stu-id="521cf-138">A HoloLens device [configured for development](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="521cf-139">專案檔</span><span class="sxs-lookup"><span data-stu-id="521cf-139">Project files</span></span>

* <span data-ttu-id="521cf-140">下載專案 [所需的](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-210-Gaze.zip) 檔案。</span><span class="sxs-lookup"><span data-stu-id="521cf-140">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-210-Gaze.zip) required by the project.</span></span> <span data-ttu-id="521cf-141">需要 Unity 2017.2 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="521cf-141">Requires Unity 2017.2 or later.</span></span>
* <span data-ttu-id="521cf-142">取消將檔案封存到您的桌面或其他易於觸及的位置。</span><span class="sxs-lookup"><span data-stu-id="521cf-142">Un-archive the files to your desktop or other easy to reach location.</span></span>

>[!NOTE]
><span data-ttu-id="521cf-143">如果您想要在下載之前查看原始程式碼， [可在 GitHub 上](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-210-Gaze)取得。</span><span class="sxs-lookup"><span data-stu-id="521cf-143">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-210-Gaze).</span></span>

### <a name="errata-and-notes"></a><span data-ttu-id="521cf-144">勘誤表和記事</span><span class="sxs-lookup"><span data-stu-id="521cf-144">Errata and Notes</span></span>

* <span data-ttu-id="521cf-145">在 Visual Studio 中，必須停用 [工具]-[>選項] 下的 [Just My Code] (未核取) ，才能在程式碼中叫用中斷點。</span><span class="sxs-lookup"><span data-stu-id="521cf-145">In Visual Studio, "Just My Code" needs to be disabled (unchecked) under Tools->Options->Debugging in order to hit breakpoints in your code.</span></span>

## <a name="chapter-1---unity-setup"></a><span data-ttu-id="521cf-146">第1章-Unity 設定</span><span class="sxs-lookup"><span data-stu-id="521cf-146">Chapter 1 - Unity Setup</span></span>

>[!VIDEO https://www.youtube.com/embed/_Ccn6riQ6vU]

### <a name="objectives"></a><span data-ttu-id="521cf-147">目標</span><span class="sxs-lookup"><span data-stu-id="521cf-147">Objectives</span></span>

* <span data-ttu-id="521cf-148">最佳化 Unity 以用於 HoloLens 開發。</span><span class="sxs-lookup"><span data-stu-id="521cf-148">Optimize Unity for HoloLens development.</span></span>
* <span data-ttu-id="521cf-149">匯入資產並設定場景。</span><span class="sxs-lookup"><span data-stu-id="521cf-149">Import assets and setup the scene.</span></span>
* <span data-ttu-id="521cf-150">查看 HoloLens 中的太空人。</span><span class="sxs-lookup"><span data-stu-id="521cf-150">View the astronaut in the HoloLens.</span></span>

### <a name="instructions"></a><span data-ttu-id="521cf-151">指示</span><span class="sxs-lookup"><span data-stu-id="521cf-151">Instructions</span></span>

1. <span data-ttu-id="521cf-152">啟動 Unity。</span><span class="sxs-lookup"><span data-stu-id="521cf-152">Start Unity.</span></span>
2. <span data-ttu-id="521cf-153">選取 [新增專案]。</span><span class="sxs-lookup"><span data-stu-id="521cf-153">Select **New Project**.</span></span>
3. <span data-ttu-id="521cf-154">將專案命名為 **ModelExplorer**。</span><span class="sxs-lookup"><span data-stu-id="521cf-154">Name the project **ModelExplorer**.</span></span>
4. <span data-ttu-id="521cf-155">輸入 [位置] 作為先前未封存的 [ **注視** ] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="521cf-155">Enter location as the **Gaze** folder you previously un-archived.</span></span>
5. <span data-ttu-id="521cf-156">確定專案已設定為 **3D**。</span><span class="sxs-lookup"><span data-stu-id="521cf-156">Make sure the project is set to **3D**.</span></span>
6. <span data-ttu-id="521cf-157">按一下 [ **建立專案**]。</span><span class="sxs-lookup"><span data-stu-id="521cf-157">Click **Create Project**.</span></span>

### <a name="unity-settings-for-hololens"></a><span data-ttu-id="521cf-158">HoloLens 的 Unity 設定</span><span class="sxs-lookup"><span data-stu-id="521cf-158">Unity settings for HoloLens</span></span>

<span data-ttu-id="521cf-159">我們需要讓 Unity 知道我們想要匯出的應用程式應該建立一個 [沉浸式視圖](../../../design/app-views.md) ，而不是2d 視圖。</span><span class="sxs-lookup"><span data-stu-id="521cf-159">We need to let Unity know that the app we are trying to export should create an [immersive view](../../../design/app-views.md) instead of a 2D view.</span></span> <span data-ttu-id="521cf-160">做法是將 HoloLens 新增為虛擬實境裝置。</span><span class="sxs-lookup"><span data-stu-id="521cf-160">We do that by adding HoloLens as a virtual reality device.</span></span>

1. <span data-ttu-id="521cf-161">移至 **> Player 的 [編輯 > 專案設定**]。</span><span class="sxs-lookup"><span data-stu-id="521cf-161">Go to **Edit > Project Settings > Player**.</span></span>
2. <span data-ttu-id="521cf-162">在 [播放程式設定] 的 [偵測 **器] 面板** 中，選取 [ **Windows Store** ] 圖示。</span><span class="sxs-lookup"><span data-stu-id="521cf-162">In the **Inspector Panel** for Player Settings, select the **Windows Store** icon.</span></span>
3. <span data-ttu-id="521cf-163">展開 [XR 設定] 群組。</span><span class="sxs-lookup"><span data-stu-id="521cf-163">Expand the **XR Settings** group.</span></span>
4. <span data-ttu-id="521cf-164">在 [轉譯] 區段中核取 [支援虛擬實境] 核取方塊，以新增 [虛擬實境 SDK] 清單。</span><span class="sxs-lookup"><span data-stu-id="521cf-164">In the **Rendering** section, check the **Virtual Reality Supported** checkbox to add a new **Virtual Reality SDKs** list.</span></span>
5. <span data-ttu-id="521cf-165">確認 **Windows Mixed Reality** 出現在清單中。</span><span class="sxs-lookup"><span data-stu-id="521cf-165">Verify that **Windows Mixed Reality** appears in the list.</span></span> <span data-ttu-id="521cf-166">如果沒有，請選取 **+** 清單底部的按鈕，然後選擇 [ **Windows** 全像]。</span><span class="sxs-lookup"><span data-stu-id="521cf-166">If not, select the **+** button at the bottom of the list and choose **Windows Holographic**.</span></span>

<span data-ttu-id="521cf-167">接下來，我們需要將腳本後端設定為 .NET。</span><span class="sxs-lookup"><span data-stu-id="521cf-167">Next, we need to set our scripting backend to .NET.</span></span>

1. <span data-ttu-id="521cf-168">移至 **> Player 的 [編輯] > 專案設定** (您可能仍已從上一個步驟) 。</span><span class="sxs-lookup"><span data-stu-id="521cf-168">Go to **Edit > Project Settings > Player** (you may still have this up from the previous step).</span></span>
2. <span data-ttu-id="521cf-169">在 [播放程式設定] 的 [偵測 **器] 面板** 中，選取 [ **Windows Store** ] 圖示。</span><span class="sxs-lookup"><span data-stu-id="521cf-169">In the **Inspector Panel** for Player Settings, select the **Windows Store** icon.</span></span>
3. <span data-ttu-id="521cf-170">在 [**其他設定**] 設定區段中，確定 [**腳本後端**] 設定為 [ **.net** ]</span><span class="sxs-lookup"><span data-stu-id="521cf-170">In the **Other Settings** Configuration section, make sure that **Scripting Backend** is set to **.NET**</span></span>

<span data-ttu-id="521cf-171">最後，我們會更新品質設定，以在 HoloLens 上達成更快速的效能。</span><span class="sxs-lookup"><span data-stu-id="521cf-171">Finally, we'll update our quality settings to achieve a fast performance on HoloLens.</span></span>

1. <span data-ttu-id="521cf-172">移至 [ **編輯 > 專案設定 > 品質**]。</span><span class="sxs-lookup"><span data-stu-id="521cf-172">Go to **Edit > Project Settings > Quality**.</span></span>
2. <span data-ttu-id="521cf-173">按一下 [Windows 市集中] 圖示底下 **預設** 資料列中的向下箭號。</span><span class="sxs-lookup"><span data-stu-id="521cf-173">Click on downward pointing arrow in the **Default** row under the Windows Store icon.</span></span>
3. <span data-ttu-id="521cf-174">針對 **Windows Store 應用程式** 選取 [**非常低**]。</span><span class="sxs-lookup"><span data-stu-id="521cf-174">Select **Very Low** for **Windows Store Apps**.</span></span>

### <a name="import-project-assets"></a><span data-ttu-id="521cf-175">匯入專案資產</span><span class="sxs-lookup"><span data-stu-id="521cf-175">Import project assets</span></span>

1. <span data-ttu-id="521cf-176">以滑鼠右鍵按一下 [**專案**] 面板中的 [**資產**] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="521cf-176">Right click the **Assets** folder in the **Project** panel.</span></span>
2. <span data-ttu-id="521cf-177">按一下 [匯 **入封裝 > 自訂套件**]。</span><span class="sxs-lookup"><span data-stu-id="521cf-177">Click on **Import Package > Custom Package**.</span></span>
3. <span data-ttu-id="521cf-178">流覽至您所下載的專案檔，然後按一下 [ **ModelExplorer unitypackage**]。</span><span class="sxs-lookup"><span data-stu-id="521cf-178">Navigate to the project files you downloaded and click on **ModelExplorer.unitypackage**.</span></span>
4. <span data-ttu-id="521cf-179">按一下 [開啟]。</span><span class="sxs-lookup"><span data-stu-id="521cf-179">Click **Open**.</span></span>
5. <span data-ttu-id="521cf-180">載入封裝之後，請按一下 [匯 **入** ] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="521cf-180">After the package loads, click on the **Import** button.</span></span>

### <a name="setup-the-scene"></a><span data-ttu-id="521cf-181">設定場景</span><span class="sxs-lookup"><span data-stu-id="521cf-181">Setup the scene</span></span>

1. <span data-ttu-id="521cf-182">在階層中，刪除 **主要攝影機**。</span><span class="sxs-lookup"><span data-stu-id="521cf-182">In the Hierarchy, delete the **Main Camera**.</span></span>
2. <span data-ttu-id="521cf-183">在 **HoloToolkit** 資料夾中，開啟 **輸入** 資料夾，然後開啟 **Prefabs** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="521cf-183">In the **HoloToolkit** folder, open the **Input** folder, then open the **Prefabs** folder.</span></span>
3. <span data-ttu-id="521cf-184">將 **MixedRealityCameraParent** 預製專案從 **Prefabs** 資料夾拖 **放到階層中。**</span><span class="sxs-lookup"><span data-stu-id="521cf-184">Drag and drop the **MixedRealityCameraParent** prefab from the **Prefabs** folder into the **Hierarchy**.</span></span>
4. <span data-ttu-id="521cf-185">以滑鼠右鍵按一下階層中的 **方向燈** ，然後選取 [ **刪除**]。</span><span class="sxs-lookup"><span data-stu-id="521cf-185">Right-click the **Directional Light** in the Hierarchy and select **Delete**.</span></span>
5. <span data-ttu-id="521cf-186">在 [全像 **] 資料夾中**，將下列資產拖放到 **階層的根目錄中：**</span><span class="sxs-lookup"><span data-stu-id="521cf-186">In the **Holograms** folder, drag and drop the following assets into the root of the **Hierarchy**:</span></span>
    * <span data-ttu-id="521cf-187">**AstroMan**</span><span class="sxs-lookup"><span data-stu-id="521cf-187">**AstroMan**</span></span>
    * <span data-ttu-id="521cf-188">**光線**</span><span class="sxs-lookup"><span data-stu-id="521cf-188">**Lights**</span></span>
    * <span data-ttu-id="521cf-189">**SpaceAudioSource**</span><span class="sxs-lookup"><span data-stu-id="521cf-189">**SpaceAudioSource**</span></span>
    * <span data-ttu-id="521cf-190">**SpaceBackground**</span><span class="sxs-lookup"><span data-stu-id="521cf-190">**SpaceBackground**</span></span>
6. <span data-ttu-id="521cf-191">啟動 **播放模式** ▶以查看太空人。</span><span class="sxs-lookup"><span data-stu-id="521cf-191">Start **Play Mode** ▶ to view the astronaut.</span></span>
7. <span data-ttu-id="521cf-192">按一下 [ **播放模式▶]** 以 **停止**。</span><span class="sxs-lookup"><span data-stu-id="521cf-192">Click **Play Mode** ▶ again to **Stop**.</span></span>
8. <span data-ttu-id="521cf-193">在 [全像 **] 資料夾中**，尋找 **Fitbox** 資產，然後將它拖曳到 **階層的根目錄。**</span><span class="sxs-lookup"><span data-stu-id="521cf-193">In the **Holograms** folder, find the **Fitbox** asset and drag it to the root of the **Hierarchy**.</span></span>
9. <span data-ttu-id="521cf-194">**在 [階層] 面板中** 選取 **Fitbox** 。</span><span class="sxs-lookup"><span data-stu-id="521cf-194">Select the **Fitbox** in the **Hierarchy** panel.</span></span>
10. <span data-ttu-id="521cf-195">將 **AstroMan** 集合從階層拖曳 **至 [** 偵測 **器**] 面板中 Fitbox 的 [**全息圖集合**] 屬性。</span><span class="sxs-lookup"><span data-stu-id="521cf-195">Drag the **AstroMan** collection from the **Hierarchy** to the **Hologram Collection** property of the Fitbox in the **Inspector** panel.</span></span>

### <a name="save-the-project"></a><span data-ttu-id="521cf-196">儲存專案</span><span class="sxs-lookup"><span data-stu-id="521cf-196">Save the project</span></span>

1. <span data-ttu-id="521cf-197">儲存新場景： **File > 另存場景**。</span><span class="sxs-lookup"><span data-stu-id="521cf-197">Save the new scene: **File > Save Scene As**.</span></span>
2. <span data-ttu-id="521cf-198">按一下 [ **新增資料夾** ]，然後將資料夾命名為 **幕後**。</span><span class="sxs-lookup"><span data-stu-id="521cf-198">Click **New Folder** and name the folder **Scenes**.</span></span>
3. <span data-ttu-id="521cf-199">將檔案命名為 "**ModelExplorer**"，並將它儲存在 **幕後** 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="521cf-199">Name the file “**ModelExplorer**” and save it in the **Scenes** folder.</span></span>

### <a name="build-the-project"></a><span data-ttu-id="521cf-200">建置專案</span><span class="sxs-lookup"><span data-stu-id="521cf-200">Build the project</span></span>

1. <span data-ttu-id="521cf-201">在 Unity 中，選取 [ **File > Build Settings**]。</span><span class="sxs-lookup"><span data-stu-id="521cf-201">In Unity, select **File > Build Settings**.</span></span>
2. <span data-ttu-id="521cf-202">按一下 [ **新增開啟場景** ] 以加入場景。</span><span class="sxs-lookup"><span data-stu-id="521cf-202">Click **Add Open Scenes** to add the scene.</span></span>
3. <span data-ttu-id="521cf-203">在 [**平臺**] 清單中選取 **通用 Windows 平臺**，然後按一下 [**切換平臺**]。</span><span class="sxs-lookup"><span data-stu-id="521cf-203">Select **Universal Windows Platform** in the **Platform** list and click **Switch Platform**.</span></span>
4. <span data-ttu-id="521cf-204">如果您是特別針對 HoloLens 進行開發，請將 **目標裝置** 設定為 **hololens**。</span><span class="sxs-lookup"><span data-stu-id="521cf-204">If you're specifically developing for HoloLens, set **Target device** to **HoloLens**.</span></span> <span data-ttu-id="521cf-205">否則，請將它保留在 **任何裝置** 上。</span><span class="sxs-lookup"><span data-stu-id="521cf-205">Otherwise, leave it on **Any device**.</span></span>
5. <span data-ttu-id="521cf-206">請確定 **組建類型** 設定為 [ **D3D** ]，並將 [ **Sdk** ] 設定為 [ **最新安裝** 的 (，其應為 SDK 16299 或更新版本的) 。</span><span class="sxs-lookup"><span data-stu-id="521cf-206">Ensure **Build Type** is set to **D3D** and **SDK** is set to **Latest installed** (which should be SDK 16299 or newer).</span></span>
6. <span data-ttu-id="521cf-207">按一下 [建置]。</span><span class="sxs-lookup"><span data-stu-id="521cf-207">Click **Build**.</span></span>
7. <span data-ttu-id="521cf-208">建立名為 "App" 的 **新資料夾** 。</span><span class="sxs-lookup"><span data-stu-id="521cf-208">Create a **New Folder** named "App".</span></span>
8. <span data-ttu-id="521cf-209">按一下 **應用程式** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="521cf-209">Single click the **App** folder.</span></span>
9. <span data-ttu-id="521cf-210">按下 [ **選取資料夾**]。</span><span class="sxs-lookup"><span data-stu-id="521cf-210">Press **Select Folder**.</span></span>

<span data-ttu-id="521cf-211">當 Unity 完成時，將會出現檔案總管視窗。</span><span class="sxs-lookup"><span data-stu-id="521cf-211">When Unity is done, a File Explorer window will appear.</span></span>

1. <span data-ttu-id="521cf-212">開啟 **應用程式** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="521cf-212">Open the **App** folder.</span></span>
2. <span data-ttu-id="521cf-213">開啟 **ModelExplorer Visual Studio 方案**。</span><span class="sxs-lookup"><span data-stu-id="521cf-213">Open the **ModelExplorer Visual Studio Solution**.</span></span>

<span data-ttu-id="521cf-214">如果要部署到 HoloLens：</span><span class="sxs-lookup"><span data-stu-id="521cf-214">If deploying to HoloLens:</span></span>

1. <span data-ttu-id="521cf-215">使用 Visual Studio 中的頂端工具列，將目標從 Debug 變更為 **Release** ，以及從 ARM 變更為 **x86**。</span><span class="sxs-lookup"><span data-stu-id="521cf-215">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x86**.</span></span>
2. <span data-ttu-id="521cf-216">按一下 [本機電腦] 按鈕旁的下拉箭號，然後選取 [ **遠端電腦**]。</span><span class="sxs-lookup"><span data-stu-id="521cf-216">Click on the drop down arrow next to the Local Machine button, and select **Remote Machine**.</span></span>
3. <span data-ttu-id="521cf-217">輸入 **您的 HoloLens 裝置 IP 位址** ，並將驗證模式設定為 **通用 (未加密的通訊協定)**。</span><span class="sxs-lookup"><span data-stu-id="521cf-217">Enter **your HoloLens device IP address** and set Authentication Mode to **Universal (Unencrypted Protocol)**.</span></span> <span data-ttu-id="521cf-218">按一下 [選取]。</span><span class="sxs-lookup"><span data-stu-id="521cf-218">Click **Select**.</span></span> <span data-ttu-id="521cf-219">如果您不知道您的裝置 IP 位址，請查看 [ **設定] > Network & Internet > Advanced 選項**。</span><span class="sxs-lookup"><span data-stu-id="521cf-219">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options**.</span></span>
4. <span data-ttu-id="521cf-220">在頂端功能表列中，按一下 [ **Debug-> 啟動但不進行調試** ]，或按 **Ctrl + F5**。</span><span class="sxs-lookup"><span data-stu-id="521cf-220">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span> <span data-ttu-id="521cf-221">如果這是您第一次部署至您的裝置，您必須將 [它與 Visual Studio 配對](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#pairing-your-device)。</span><span class="sxs-lookup"><span data-stu-id="521cf-221">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#pairing-your-device).</span></span>
5. <span data-ttu-id="521cf-222">部署應用程式之後，請使用 **選取手勢** 來關閉 **Fitbox** 。</span><span class="sxs-lookup"><span data-stu-id="521cf-222">When the app has deployed, dismiss the **Fitbox** with a **select gesture**.</span></span>

<span data-ttu-id="521cf-223">如果部署到沉浸式耳機：</span><span class="sxs-lookup"><span data-stu-id="521cf-223">If deploying to an immersive headset:</span></span>

1. <span data-ttu-id="521cf-224">使用 Visual Studio 中的頂端工具列，將目標從 Debug 變更為 **Release** ，以及從 ARM 變更為 **x64**。</span><span class="sxs-lookup"><span data-stu-id="521cf-224">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x64**.</span></span>
2. <span data-ttu-id="521cf-225">請確定部署目標設定為 [ **本機電腦**]。</span><span class="sxs-lookup"><span data-stu-id="521cf-225">Make sure the deployment target is set to **Local Machine**.</span></span>
3. <span data-ttu-id="521cf-226">在頂端功能表列中，按一下 [ **Debug-> 啟動但不進行調試** ]，或按 **Ctrl + F5**。</span><span class="sxs-lookup"><span data-stu-id="521cf-226">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
4. <span data-ttu-id="521cf-227">部署應用程式之後，請在動作控制器上提取觸發程式來關閉 **Fitbox** 。</span><span class="sxs-lookup"><span data-stu-id="521cf-227">When the app has deployed, dismiss the **Fitbox** by pulling the trigger on a motion controller.</span></span>

## <a name="chapter-2---cursor-and-target-feedback"></a><span data-ttu-id="521cf-228">第2章-游標和目標意見反應</span><span class="sxs-lookup"><span data-stu-id="521cf-228">Chapter 2 - Cursor and target feedback</span></span>

>[!VIDEO https://www.youtube.com/embed/S24u0V_T7ZI]

### <a name="objectives"></a><span data-ttu-id="521cf-229">目標</span><span class="sxs-lookup"><span data-stu-id="521cf-229">Objectives</span></span>

* <span data-ttu-id="521cf-230">資料指標視覺化設計和行為。</span><span class="sxs-lookup"><span data-stu-id="521cf-230">Cursor visual design and behavior.</span></span>
* <span data-ttu-id="521cf-231">以注視為基礎的資料指標意見反應。</span><span class="sxs-lookup"><span data-stu-id="521cf-231">Gaze-based cursor feedback.</span></span>
* <span data-ttu-id="521cf-232">注視的全像影像意見反應。</span><span class="sxs-lookup"><span data-stu-id="521cf-232">Gaze-based hologram feedback.</span></span>

<span data-ttu-id="521cf-233">我們將以一些資料指標設計原則做為基礎，也就是：</span><span class="sxs-lookup"><span data-stu-id="521cf-233">We're going to base our work on some cursor design principles, namely:</span></span>

* <span data-ttu-id="521cf-234">資料指標一律會存在。</span><span class="sxs-lookup"><span data-stu-id="521cf-234">The cursor is always present.</span></span>
* <span data-ttu-id="521cf-235">不要讓資料指標變得太小或太大。</span><span class="sxs-lookup"><span data-stu-id="521cf-235">Don't let the cursor get too small or big.</span></span>
* <span data-ttu-id="521cf-236">避免阻礙內容。</span><span class="sxs-lookup"><span data-stu-id="521cf-236">Avoid obstructing content.</span></span>

### <a name="instructions"></a><span data-ttu-id="521cf-237">指示</span><span class="sxs-lookup"><span data-stu-id="521cf-237">Instructions</span></span>

1. <span data-ttu-id="521cf-238">在 [ **HoloToolkit\Input\Prefabs** ] 資料夾中，尋找 **InputManager** 資產。</span><span class="sxs-lookup"><span data-stu-id="521cf-238">In the **HoloToolkit\Input\Prefabs** folder, find the **InputManager** asset.</span></span>
2. <span data-ttu-id="521cf-239">將 **InputManager** 拖放到階層上 **。**</span><span class="sxs-lookup"><span data-stu-id="521cf-239">Drag and drop the **InputManager** onto the **Hierarchy**.</span></span>
3. <span data-ttu-id="521cf-240">在 [ **HoloToolkit\Input\Prefabs** ] 資料夾中，尋找資料 **指標** 資產。</span><span class="sxs-lookup"><span data-stu-id="521cf-240">In the **HoloToolkit\Input\Prefabs** folder, find the **Cursor** asset.</span></span>
4. <span data-ttu-id="521cf-241">將 **游標** 拖放到階層上 **。**</span><span class="sxs-lookup"><span data-stu-id="521cf-241">Drag and drop the **Cursor** onto the **Hierarchy**.</span></span>
5. <span data-ttu-id="521cf-242">選取階層中的 **InputManager** 物件 **。**</span><span class="sxs-lookup"><span data-stu-id="521cf-242">Select the **InputManager** object in the **Hierarchy**.</span></span>
6. <span data-ttu-id="521cf-243">將資料 **指標** 物件從階層 **拖曳至偵測\*\*\*\*器** 底部的 InputManager **SimpleSinglePointerSelector** 資料 **指標** 欄位。</span><span class="sxs-lookup"><span data-stu-id="521cf-243">Drag the **Cursor** object from the **Hierarchy** into the InputManager's **SimpleSinglePointerSelector**'s **Cursor** field, at the bottom of the **Inspector**.</span></span>

![簡單的單一指標選取器設定](images/holograms210-ssps.png)

### <a name="build-and-deploy"></a><span data-ttu-id="521cf-245">建置和部署</span><span class="sxs-lookup"><span data-stu-id="521cf-245">Build and Deploy</span></span>

1. <span data-ttu-id="521cf-246">從檔案 **> 組建設定** 重建應用程式。</span><span class="sxs-lookup"><span data-stu-id="521cf-246">Rebuild the app from **File > Build Settings**.</span></span>
2. <span data-ttu-id="521cf-247">開啟 **應用程式資料夾**。</span><span class="sxs-lookup"><span data-stu-id="521cf-247">Open the **App folder**.</span></span>
3. <span data-ttu-id="521cf-248">開啟 **ModelExplorer Visual Studio 方案**。</span><span class="sxs-lookup"><span data-stu-id="521cf-248">Open the **ModelExplorer Visual Studio Solution**.</span></span>
4. <span data-ttu-id="521cf-249">按一下 [ **Debug-> 啟動但不進行調試]，** 或按 **Ctrl + F5**。</span><span class="sxs-lookup"><span data-stu-id="521cf-249">Click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
5. <span data-ttu-id="521cf-250">觀察資料指標的繪製方式，以及它如何在觸碰全像影像時變更外觀。</span><span class="sxs-lookup"><span data-stu-id="521cf-250">Observe how the cursor is drawn, and how it changes appearance if it is touching a hologram.</span></span>

### <a name="instructions"></a><span data-ttu-id="521cf-251">指示</span><span class="sxs-lookup"><span data-stu-id="521cf-251">Instructions</span></span>

1. <span data-ttu-id="521cf-252">**在 [階層] 面板中**，展開 [ **AstroMan** -> **GEO_G**] -> **Back_Center** 物件。</span><span class="sxs-lookup"><span data-stu-id="521cf-252">In the **Hierarchy** panel, expand the **AstroMan**->**GEO_G**->**Back_Center** object.</span></span>
2. <span data-ttu-id="521cf-253">按兩下 **Interactible** ，在 Visual Studio 中開啟。</span><span class="sxs-lookup"><span data-stu-id="521cf-253">Double click on **Interactible.cs** to open it in Visual Studio.</span></span>
3. <span data-ttu-id="521cf-254">取消批註 **IFocusable. OnFocusEnter ()** 中的行，以及 **Interactible** 中的 **IFocusable OnFocusExit ()** 回呼。</span><span class="sxs-lookup"><span data-stu-id="521cf-254">Uncomment the lines in the **IFocusable.OnFocusEnter()** and **IFocusable.OnFocusExit()** callbacks in **Interactible.cs**.</span></span> <span data-ttu-id="521cf-255">當焦點 (于) 進入和結束特定 GameObject 的碰撞器時，混合現實工具組的 InputManager 就會呼叫這些方法。</span><span class="sxs-lookup"><span data-stu-id="521cf-255">These are called by the Mixed Reality Toolkit's InputManager when focus (either by gaze or by controller pointing) enters and exits the specific GameObject's collider.</span></span>

```cs
/* TODO: DEVELOPER CODING EXERCISE 2.d */

void IFocusable.OnFocusEnter()
{
    for (int i = 0; i < defaultMaterials.Length; i++)
    {
        // 2.d: Uncomment the below line to highlight the material when gaze enters.
        defaultMaterials[i].EnableKeyword("_ENVIRONMENT_COLORING");
    }
}

void IFocusable.OnFocusExit()
{
    for (int i = 0; i < defaultMaterials.Length; i++)
    {
        // 2.d: Uncomment the below line to remove highlight on material when gaze exits.
        defaultMaterials[i].DisableKeyword("_ENVIRONMENT_COLORING");
    }
}
```

>[!NOTE]
><span data-ttu-id="521cf-256">我們使用 `EnableKeyword` 和更新版本 `DisableKeyword` 。</span><span class="sxs-lookup"><span data-stu-id="521cf-256">We use `EnableKeyword` and `DisableKeyword` above.</span></span> <span data-ttu-id="521cf-257">為了在您自己的應用程式中使用工具組的標準著色器來使用這些功能，您必須遵循 [Unity 指導方針，透過腳本存取材質](https://docs.unity3d.com/Manual/MaterialsAccessingViaScript.html)。</span><span class="sxs-lookup"><span data-stu-id="521cf-257">In order to make use of these in your own app with the Toolkit's Standard shader, you'll need to follow the [Unity guidelines for accessing materials via script](https://docs.unity3d.com/Manual/MaterialsAccessingViaScript.html).</span></span> <span data-ttu-id="521cf-258">在此情況下，我們已在 [資源] 資料夾中包含三個醒目提示 [的材質](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-210-Gaze/Completed/ModelExplorer/Assets/Resources/Models/AstroMan/Materials) 變化 (尋找名稱) 中醒目提示的三個材質。</span><span class="sxs-lookup"><span data-stu-id="521cf-258">In this case, we've already included the [three variants of highlighted material](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-210-Gaze/Completed/ModelExplorer/Assets/Resources/Models/AstroMan/Materials) needed in the Resources folder (look for the three materials with highlight in the name).</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="521cf-259">建置和部署</span><span class="sxs-lookup"><span data-stu-id="521cf-259">Build and Deploy</span></span>

1. <span data-ttu-id="521cf-260">同樣地，建立專案並部署到 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="521cf-260">As before, build the project and deploy to the HoloLens.</span></span>
2. <span data-ttu-id="521cf-261">觀察當注視的目標物件和不是時，會發生什麼事。</span><span class="sxs-lookup"><span data-stu-id="521cf-261">Observe what happens when the gaze is aimed at an object and when it's not.</span></span>

## <a name="chapter-3---targeting-techniques"></a><span data-ttu-id="521cf-262">第3章-目標技術</span><span class="sxs-lookup"><span data-stu-id="521cf-262">Chapter 3 - Targeting Techniques</span></span>

>[!VIDEO https://www.youtube.com/embed/TFnuLva4VJ0]

### <a name="objectives"></a><span data-ttu-id="521cf-263">目標</span><span class="sxs-lookup"><span data-stu-id="521cf-263">Objectives</span></span>

* <span data-ttu-id="521cf-264">讓您更輕鬆地鎖定全像影像。</span><span class="sxs-lookup"><span data-stu-id="521cf-264">Make it easier to target holograms.</span></span>
* <span data-ttu-id="521cf-265">穩定的自然標頭移動。</span><span class="sxs-lookup"><span data-stu-id="521cf-265">Stabilize natural head movements.</span></span>

### <a name="instructions"></a><span data-ttu-id="521cf-266">指示</span><span class="sxs-lookup"><span data-stu-id="521cf-266">Instructions</span></span>

1. <span data-ttu-id="521cf-267">**在 [階層] 面板中**，選取 [ **InputManager** ] 物件。</span><span class="sxs-lookup"><span data-stu-id="521cf-267">In the **Hierarchy** panel, select the **InputManager** object.</span></span>
2. <span data-ttu-id="521cf-268">在 [偵測 **器** ] 面板中，尋找「 **注視的穩定** 」腳本。</span><span class="sxs-lookup"><span data-stu-id="521cf-268">In the **Inspector** panel, find the **Gaze Stabilizer** script.</span></span> <span data-ttu-id="521cf-269">如果您想要查看，請按一下該檔案以在 Visual Studio 中開啟。</span><span class="sxs-lookup"><span data-stu-id="521cf-269">Click it to open in Visual Studio, if you want to take a look.</span></span>
    * <span data-ttu-id="521cf-270">此腳本會反復查看 Raycast 資料的範例，並協助穩定使用者的注視精確度目標。</span><span class="sxs-lookup"><span data-stu-id="521cf-270">This script iterates over samples of Raycast data and helps stabilize the user's gaze for precision targeting.</span></span>
3. <span data-ttu-id="521cf-271">在偵測 **器** 中，您可以編輯已 **儲存的穩定性範例** 值。</span><span class="sxs-lookup"><span data-stu-id="521cf-271">In the **Inspector**, you can edit the **Stored Stability Samples** value.</span></span> <span data-ttu-id="521cf-272">此值代表穩定程式反覆運算以計算穩定值的樣本數。</span><span class="sxs-lookup"><span data-stu-id="521cf-272">This value represents the number of samples that the stabilizer iterates on to calculate the stabilized value.</span></span>

## <a name="chapter-4---directional-indicator"></a><span data-ttu-id="521cf-273">第4章-方向指標</span><span class="sxs-lookup"><span data-stu-id="521cf-273">Chapter 4 - Directional indicator</span></span>

>[!VIDEO https://www.youtube.com/embed/htVbJCMlj64]

### <a name="objectives"></a><span data-ttu-id="521cf-274">目標</span><span class="sxs-lookup"><span data-stu-id="521cf-274">Objectives</span></span>

* <span data-ttu-id="521cf-275">在游標處新增方向指標，以協助尋找全像影像。</span><span class="sxs-lookup"><span data-stu-id="521cf-275">Add a directional indicator on the cursor to help find holograms.</span></span>

### <a name="instructions"></a><span data-ttu-id="521cf-276">指示</span><span class="sxs-lookup"><span data-stu-id="521cf-276">Instructions</span></span>

<span data-ttu-id="521cf-277">我們將使用 **DirectionIndicator .cs** 檔案，此檔案將：</span><span class="sxs-lookup"><span data-stu-id="521cf-277">We're going to use the **DirectionIndicator.cs** file which will:</span></span>

1. <span data-ttu-id="521cf-278">如果使用者不是在全像撥雲見日，則顯示方向指標。</span><span class="sxs-lookup"><span data-stu-id="521cf-278">Show the directional indicator if the user is not gazing at the holograms.</span></span>
2. <span data-ttu-id="521cf-279">如果使用者是在全像撥雲見日，則隱藏方向指標。</span><span class="sxs-lookup"><span data-stu-id="521cf-279">Hide the directional indicator if the user is gazing at the holograms.</span></span>
3. <span data-ttu-id="521cf-280">更新方向指標以指向全像影像。</span><span class="sxs-lookup"><span data-stu-id="521cf-280">Update the directional indicator to point to the holograms.</span></span>

<span data-ttu-id="521cf-281">讓我們開始這次的教學。</span><span class="sxs-lookup"><span data-stu-id="521cf-281">Let's get started.</span></span>

1. <span data-ttu-id="521cf-282">按一下 [階層 **] 面板中的 [** **AstroMan** ] 物件，然後 **按一下箭** 號將其展開。</span><span class="sxs-lookup"><span data-stu-id="521cf-282">Click on the **AstroMan** object in the **Hierarchy** panel and **click the arrow** to expand it.</span></span>
2. <span data-ttu-id="521cf-283">**在 [階層**] 面板中，選取 [ **AstroMan**] 底下的 [ **DirectionalIndicator** ] 物件。</span><span class="sxs-lookup"><span data-stu-id="521cf-283">In the **Hierarchy** panel, select the **DirectionalIndicator** object under **AstroMan**.</span></span>
3. <span data-ttu-id="521cf-284">在 [偵測 **器** ] 面板中，按一下 [ **新增元件** ] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="521cf-284">In the **Inspector** panel, click the **Add Component** button.</span></span>
4. <span data-ttu-id="521cf-285">在功能表中，輸入搜尋方塊 **方向指標**。</span><span class="sxs-lookup"><span data-stu-id="521cf-285">In the menu, type in the search box **Direction Indicator**.</span></span> <span data-ttu-id="521cf-286">選取搜尋結果。</span><span class="sxs-lookup"><span data-stu-id="521cf-286">Select the search result.</span></span>
5. <span data-ttu-id="521cf-287">**在 [階層] 面板中**，將資料 **指標** 物件拖放至偵測 **器** 中的資料 **指標** 屬性。</span><span class="sxs-lookup"><span data-stu-id="521cf-287">In the **Hierarchy** panel, drag and drop the **Cursor** object onto the **Cursor** property in the **Inspector**.</span></span>
6. <span data-ttu-id="521cf-288">在 [**專案**] 面板的 [全像 **] 資料夾中**，將 **DirectionalIndicator** 資產拖放到偵測 **器** 的 **方向指標** 屬性。</span><span class="sxs-lookup"><span data-stu-id="521cf-288">In the **Project** panel, in the **Holograms** folder, drag and drop the **DirectionalIndicator** asset onto the **Directional Indicator** property in the **Inspector**.</span></span>
7. <span data-ttu-id="521cf-289">建立並部署應用程式。</span><span class="sxs-lookup"><span data-stu-id="521cf-289">Build and deploy the app.</span></span>
8. <span data-ttu-id="521cf-290">觀賞方向指標物件如何協助您尋找太空人。</span><span class="sxs-lookup"><span data-stu-id="521cf-290">Watch how the directional indicator object helps you find the astronaut.</span></span>

## <a name="chapter-5---billboarding"></a><span data-ttu-id="521cf-291">第5章-Billboarding</span><span class="sxs-lookup"><span data-stu-id="521cf-291">Chapter 5 - Billboarding</span></span>

>[!VIDEO https://www.youtube.com/embed/qFiLr_LUACE]

### <a name="objectives"></a><span data-ttu-id="521cf-292">目標</span><span class="sxs-lookup"><span data-stu-id="521cf-292">Objectives</span></span>

* <span data-ttu-id="521cf-293">使用 billboarding 讓全像投影都能朝您面對。</span><span class="sxs-lookup"><span data-stu-id="521cf-293">Use billboarding to have holograms always face towards you.</span></span>

<span data-ttu-id="521cf-294">我們將使用 **佈告欄** 檔案來保持 GameObject 導向，讓使用者隨時都能與使用者互動。</span><span class="sxs-lookup"><span data-stu-id="521cf-294">We will be using the **Billboard.cs** file to keep a GameObject oriented such that it is facing the user at all times.</span></span>

1. <span data-ttu-id="521cf-295">**在 [階層] 面板中**，選取 [ **AstroMan** ] 物件。</span><span class="sxs-lookup"><span data-stu-id="521cf-295">In the **Hierarchy** panel, select the **AstroMan** object.</span></span>
2. <span data-ttu-id="521cf-296">在 [偵測 **器** ] 面板中，按一下 [ **新增元件** ] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="521cf-296">In the **Inspector** panel, click the **Add Component** button.</span></span>
3. <span data-ttu-id="521cf-297">在功能表中，輸入搜尋方塊 **佈告欄**。</span><span class="sxs-lookup"><span data-stu-id="521cf-297">In the menu, type in the search box **Billboard**.</span></span> <span data-ttu-id="521cf-298">選取搜尋結果。</span><span class="sxs-lookup"><span data-stu-id="521cf-298">Select the search result.</span></span>
4. <span data-ttu-id="521cf-299">在 [偵測 **器** ] 中，將 **Pivot 軸** 設定為 **Y**。</span><span class="sxs-lookup"><span data-stu-id="521cf-299">In the **Inspector** set the **Pivot Axis** to **Y**.</span></span>
5. <span data-ttu-id="521cf-300">試試看！</span><span class="sxs-lookup"><span data-stu-id="521cf-300">Try it!</span></span> <span data-ttu-id="521cf-301">如同之前一樣建立及部署應用程式。</span><span class="sxs-lookup"><span data-stu-id="521cf-301">Build and deploy the app as before.</span></span>
6. <span data-ttu-id="521cf-302">無論您如何改變觀點，都能看到佈告欄物件的臉部。</span><span class="sxs-lookup"><span data-stu-id="521cf-302">See how the Billboard object faces you no matter how you change the viewpoint.</span></span>
7. <span data-ttu-id="521cf-303">請立即從 **AstroMan** 刪除腳本。</span><span class="sxs-lookup"><span data-stu-id="521cf-303">Delete the script from the **AstroMan** for now.</span></span>

## <a name="chapter-6---tag-along"></a><span data-ttu-id="521cf-304">第6章-Tag-Along</span><span class="sxs-lookup"><span data-stu-id="521cf-304">Chapter 6 - Tag-Along</span></span>

>[!VIDEO https://www.youtube.com/embed/Ct8ORZAX5JU]

### <a name="objectives"></a><span data-ttu-id="521cf-305">目標</span><span class="sxs-lookup"><span data-stu-id="521cf-305">Objectives</span></span>

* <span data-ttu-id="521cf-306">使用 Tag-Along，讓我們的全像是在房間的地方接住。</span><span class="sxs-lookup"><span data-stu-id="521cf-306">Use Tag-Along to have our holograms follow us around the room.</span></span>

<span data-ttu-id="521cf-307">當我們處理此問題時，我們將會以下列設計條件約束為導向：</span><span class="sxs-lookup"><span data-stu-id="521cf-307">As we work on this issue, we'll be guided by the following design constraints:</span></span>

* <span data-ttu-id="521cf-308">內容應該一律一目了然。</span><span class="sxs-lookup"><span data-stu-id="521cf-308">Content should always be a glance away.</span></span>
* <span data-ttu-id="521cf-309">內容不能以這種方式進行。</span><span class="sxs-lookup"><span data-stu-id="521cf-309">Content should not be in the way.</span></span>
* <span data-ttu-id="521cf-310">標頭鎖定內容不舒服。</span><span class="sxs-lookup"><span data-stu-id="521cf-310">Head-locking content is uncomfortable.</span></span>

<span data-ttu-id="521cf-311">此處所用的解決方案是使用「加上標籤」的方法。</span><span class="sxs-lookup"><span data-stu-id="521cf-311">The solution used here is to use a "tag-along" approach.</span></span>

<span data-ttu-id="521cf-312">標記物件永遠不會完全離開使用者的觀點。</span><span class="sxs-lookup"><span data-stu-id="521cf-312">A tag-along object never fully leaves the user's view.</span></span> <span data-ttu-id="521cf-313">您可以將標籤與使用者的標頭相關聯的物件視為使用者的標頭。</span><span class="sxs-lookup"><span data-stu-id="521cf-313">You can think of the a tag-along as being an object attached to the user's head by rubber bands.</span></span> <span data-ttu-id="521cf-314">當使用者移動時，內容會在觀看視野的邊緣時保持不變，而不需要完全離開。</span><span class="sxs-lookup"><span data-stu-id="521cf-314">As the user moves, the content will stay within an easy glance by sliding towards the edge of the view without completely leaving.</span></span> <span data-ttu-id="521cf-315">當使用者 gazes 到加上標籤的物件時，它會更完整地顯示。</span><span class="sxs-lookup"><span data-stu-id="521cf-315">When the user gazes towards the tag-along object, it comes more fully into view.</span></span>

<span data-ttu-id="521cf-316">我們將使用 **SimpleTagalong .cs** 檔案，此檔案將：</span><span class="sxs-lookup"><span data-stu-id="521cf-316">We're going to use the **SimpleTagalong.cs** file which will:</span></span>

1. <span data-ttu-id="521cf-317">判斷 Tag-Along 物件是否在相機界限內。</span><span class="sxs-lookup"><span data-stu-id="521cf-317">Determine if the Tag-Along object is within the camera bounds.</span></span>
2. <span data-ttu-id="521cf-318">如果不在 view （視圖）的範圍內，請將 Tag-Along 定位於 view （視圖）中的部分。</span><span class="sxs-lookup"><span data-stu-id="521cf-318">If not within the view frustum, position the Tag-Along to partially within the view frustum.</span></span>
3. <span data-ttu-id="521cf-319">否則，請將 Tag-Along 定位至使用者的預設距離。</span><span class="sxs-lookup"><span data-stu-id="521cf-319">Otherwise, position the Tag-Along to a default distance from the user.</span></span>

<span data-ttu-id="521cf-320">若要這樣做，我們必須先變更 **Interactible .cs** 腳本來呼叫 **TagalongAction**。</span><span class="sxs-lookup"><span data-stu-id="521cf-320">To do this, we first must change the **Interactible.cs** script to call the **TagalongAction**.</span></span>

1. <span data-ttu-id="521cf-321">完成編碼練習6來編輯 **Interactible。** a (取消批註行84至 87) 。</span><span class="sxs-lookup"><span data-stu-id="521cf-321">Edit **Interactible.cs** by completing coding exercise 6.a (uncommenting lines 84 to 87).</span></span>

```cs
/* TODO: DEVELOPER CODING EXERCISE 6.a */
// 6.a: Uncomment the lines below to perform a Tagalong action.
if (interactibleAction != null)
{
    interactibleAction.PerformAction();
}
```

<span data-ttu-id="521cf-322">**InteractibleAction** 與 **Interactible** 配對的腳本會在您點擊全像影像時執行自訂動作。</span><span class="sxs-lookup"><span data-stu-id="521cf-322">The **InteractibleAction.cs** script, paired with **Interactible.cs** performs custom actions when you tap on holograms.</span></span> <span data-ttu-id="521cf-323">在此情況下，我們將特別針對標記使用一個。</span><span class="sxs-lookup"><span data-stu-id="521cf-323">In this case, we'll use one specifically for tag-along.</span></span>

* <span data-ttu-id="521cf-324">在 [ **腳本** ] 資料夾中，按一下 [ **TagalongAction** ] 資產以在 Visual Studio 中開啟。</span><span class="sxs-lookup"><span data-stu-id="521cf-324">In the **Scripts** folder click on **TagalongAction.cs** asset to open in Visual Studio.</span></span>
* <span data-ttu-id="521cf-325">完成程式碼撰寫練習，或將其變更為：</span><span class="sxs-lookup"><span data-stu-id="521cf-325">Complete the coding exercise or change it to this:</span></span>
  * <span data-ttu-id="521cf-326">在階層 **頂端的搜尋列中，輸入** **ChestButton_Center** 並選取結果。</span><span class="sxs-lookup"><span data-stu-id="521cf-326">At the top of the **Hierarchy**, in the search bar type **ChestButton_Center** and select the result.</span></span>
  * <span data-ttu-id="521cf-327">在 [偵測 **器** ] 面板中，按一下 [ **新增元件** ] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="521cf-327">In the **Inspector** panel, click the **Add Component** button.</span></span>
  * <span data-ttu-id="521cf-328">在功能表中，輸入搜尋方塊 **Tagalong 動作**。</span><span class="sxs-lookup"><span data-stu-id="521cf-328">In the menu, type in the search box **Tagalong Action**.</span></span> <span data-ttu-id="521cf-329">選取搜尋結果。</span><span class="sxs-lookup"><span data-stu-id="521cf-329">Select the search result.</span></span>
  * <span data-ttu-id="521cf-330">在 [全像 **] 資料夾中** 尋找 **Tagalong** 資產。</span><span class="sxs-lookup"><span data-stu-id="521cf-330">In **Holograms** folder find the **Tagalong** asset.</span></span>
  * <span data-ttu-id="521cf-331">選取階層中的 **ChestButton_Center** 物件 **。**</span><span class="sxs-lookup"><span data-stu-id="521cf-331">Select the **ChestButton_Center** object in the **Hierarchy**.</span></span> <span data-ttu-id="521cf-332">將 **TagAlong** 物件從 **專案** 面板拖放到偵測 **器** 的 [ **要 TagAlong 的物件** ] 屬性中。</span><span class="sxs-lookup"><span data-stu-id="521cf-332">Drag and drop the **TagAlong** object from the **Project** panel onto the **Inspector** into the **Object To Tagalong** property.</span></span>
  * <span data-ttu-id="521cf-333">將 **Tagalong 動作** 物件從偵測 **器** 拖曳到 **Interactible** 腳本的 **Interactible 動作** 欄位中。</span><span class="sxs-lookup"><span data-stu-id="521cf-333">Drag the **Tagalong Action** object from the **Inspector** into the **Interactible Action** field on the **Interactible** script.</span></span>
* <span data-ttu-id="521cf-334">按兩下 **TagalongAction** 腳本，在 Visual Studio 中開啟它。</span><span class="sxs-lookup"><span data-stu-id="521cf-334">Double click the **TagalongAction** script to open it in Visual Studio.</span></span>

![Interactible 設定](images/holograms210-interactible.png)

<span data-ttu-id="521cf-336">我們需要新增下列內容：</span><span class="sxs-lookup"><span data-stu-id="521cf-336">We need to add the following:</span></span>

* <span data-ttu-id="521cf-337">將功能加入至 TagalongAction 腳本中的 PerformAction 函式， (繼承自 InteractibleAction) 。</span><span class="sxs-lookup"><span data-stu-id="521cf-337">Add functionality to the PerformAction function in the TagalongAction script (inherited from InteractibleAction).</span></span>
* <span data-ttu-id="521cf-338">將 billboarding 加入至 gazed 物件，並將 pivot 軸設定為 XY。</span><span class="sxs-lookup"><span data-stu-id="521cf-338">Add billboarding to the gazed-upon object, and set the pivot axis to XY.</span></span>
* <span data-ttu-id="521cf-339">然後將簡單 Tag-Along 新增至物件。</span><span class="sxs-lookup"><span data-stu-id="521cf-339">Then add simple Tag-Along to the object.</span></span>

<span data-ttu-id="521cf-340">以下是 **TagalongAction** 的解決方案：</span><span class="sxs-lookup"><span data-stu-id="521cf-340">Here's our solution, from **TagalongAction.cs**:</span></span>

```cs
// Copyright (c) Microsoft Corporation. All rights reserved.
// Licensed under the MIT License. See LICENSE in the project root for license information.

using HoloToolkit.Unity;
using UnityEngine;

public class TagalongAction : InteractibleAction
{
    [SerializeField]
    [Tooltip("Drag the Tagalong prefab asset you want to display.")]
    private GameObject objectToTagalong;

    private void Awake()
    {
        if (objectToTagalong != null)
        {
            objectToTagalong = Instantiate(objectToTagalong);
            objectToTagalong.SetActive(false);

            /* TODO: DEVELOPER CODING EXERCISE 6.b */

            // 6.b: AddComponent Billboard to objectToTagAlong,
            // so it's always facing the user as they move.
            Billboard billboard = objectToTagalong.AddComponent<Billboard>();

            // 6.b: AddComponent SimpleTagalong to objectToTagAlong,
            // so it's always following the user as they move.
            objectToTagalong.AddComponent<SimpleTagalong>();

            // 6.b: Set any public properties you wish to experiment with.
            billboard.PivotAxis = PivotAxis.XY; // Already the default, but provided in case you want to edit
        }
    }

    public override void PerformAction()
    {
        // Recommend having only one tagalong.
        if (objectToTagalong == null || objectToTagalong.activeSelf)
        {
            return;
        }

        objectToTagalong.SetActive(true);
    }
}
```

* <span data-ttu-id="521cf-341">試試看！</span><span class="sxs-lookup"><span data-stu-id="521cf-341">Try it!</span></span> <span data-ttu-id="521cf-342">建立並部署應用程式。</span><span class="sxs-lookup"><span data-stu-id="521cf-342">Build and deploy the app.</span></span>
* <span data-ttu-id="521cf-343">觀賞內容如何沿著注視點的中心，但不會持續而不會封鎖。</span><span class="sxs-lookup"><span data-stu-id="521cf-343">Watch how the content follows the center of the gaze point, but not continuously and without blocking it.</span></span>