---
title: HoloLens (第1代) 基本概念 100-開始使用 Unity
description: 瞭解如何建立您的第一個適用于 HoloLens 和 Windows Mixed Reality 裝置的基本混合現實 "hello world" 應用程式。
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: mixed reality、Windows Mixed Reality、HoloLens、沉浸式、vr、mr、入門、全息圖、學術、教學課程、混合現實學術、unity、混合現實耳機、Windows mixed reality 耳機、虛擬實境耳機
ms.openlocfilehash: 999ab7dc87a639f10aad9eaf2a7ef8de2cf92633
ms.sourcegitcommit: 35bd43624be33afdb1bf6ba4ddbe36d268eb9bda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/20/2021
ms.locfileid: "104730355"
---
# <a name="hololens-1st-gen-basics-100-getting-started-with-unity"></a><span data-ttu-id="a36c1-104">HoloLens (第1代) 基本概念100：開始使用 Unity</span><span class="sxs-lookup"><span data-stu-id="a36c1-104">HoloLens (1st gen) Basics 100: Getting started with Unity</span></span>

>[!IMPORTANT]
><span data-ttu-id="a36c1-105">混合實境學院教學課程的設計是以 HoloLens (第 1 代) 和混合實境沉浸式頭戴裝置為準。</span><span class="sxs-lookup"><span data-stu-id="a36c1-105">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="a36c1-106">因此，對於仍在尋找這些裝置開發指引的開發人員而言，我們覺得這些教學課程很重要。</span><span class="sxs-lookup"><span data-stu-id="a36c1-106">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="a36c1-107">這些教學課程 **_不會_** 使用用於 HoloLens 2 的最新工具組或互動進行更新。</span><span class="sxs-lookup"><span data-stu-id="a36c1-107">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="a36c1-108">系統會保留這些資訊，以繼續在支援的裝置上運作。</span><span class="sxs-lookup"><span data-stu-id="a36c1-108">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="a36c1-109">已針對 HoloLens 2 公佈[一系列新的教學課程](mrlearning-base.md)。</span><span class="sxs-lookup"><span data-stu-id="a36c1-109">[A new series of tutorials](mrlearning-base.md) has been posted for HoloLens 2.</span></span>

<span data-ttu-id="a36c1-110">本教學課程將逐步引導您建立以 Unity 建立的基本混合現實應用程式。</span><span class="sxs-lookup"><span data-stu-id="a36c1-110">This tutorial will walk you through creating a basic mixed reality app built with Unity.</span></span>

## <a name="device-support"></a><span data-ttu-id="a36c1-111">裝置支援</span><span class="sxs-lookup"><span data-stu-id="a36c1-111">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="a36c1-112">課程</span><span class="sxs-lookup"><span data-stu-id="a36c1-112">Course</span></span></th><th style="width:150px"> <span data-ttu-id="a36c1-113"><a href="/hololens/hololens1-hardware">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="a36c1-113"><a href="/hololens/hololens1-hardware">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="a36c1-114"><a href="../../../discover/immersive-headset-hardware-details.md">沉浸式頭戴裝置</a></span><span class="sxs-lookup"><span data-stu-id="a36c1-114"><a href="../../../discover/immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="a36c1-115">MR Basics 100：開始使用 Unity</span><span class="sxs-lookup"><span data-stu-id="a36c1-115">MR Basics 100: Getting started with Unity</span></span></td><td style="text-align: center;"> <span data-ttu-id="a36c1-116">✔️</span><span class="sxs-lookup"><span data-stu-id="a36c1-116">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="a36c1-117">✔️</span><span class="sxs-lookup"><span data-stu-id="a36c1-117">✔️</span></span></td>
</tr>
</table>

## <a name="prerequisites"></a><span data-ttu-id="a36c1-118">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="a36c1-118">Prerequisites</span></span>

* <span data-ttu-id="a36c1-119">[已安裝正確工具](../../install-the-tools.md)的 Windows 10 電腦。</span><span class="sxs-lookup"><span data-stu-id="a36c1-119">A Windows 10 PC configured with the correct [tools installed](../../install-the-tools.md).</span></span>

## <a name="chapter-1---create-a-new-project"></a><span data-ttu-id="a36c1-120">第1章-建立新專案</span><span class="sxs-lookup"><span data-stu-id="a36c1-120">Chapter 1 - Create a New Project</span></span>

>[!VIDEO https://www.youtube.com/embed/2L5IFO0hnYA]

<span data-ttu-id="a36c1-121">若要使用 Unity 建立應用程式，您必須先建立專案。</span><span class="sxs-lookup"><span data-stu-id="a36c1-121">To build an app with Unity, you first need to create a project.</span></span> <span data-ttu-id="a36c1-122">此專案會組織成幾個資料夾，最重要的就是您的資產資料夾。</span><span class="sxs-lookup"><span data-stu-id="a36c1-122">This project is organized into a few folders, the most important of which is your Assets folder.</span></span> <span data-ttu-id="a36c1-123">此資料夾會保存您從數位內容建立工具（例如 Maya、最大電影4D 或 Photoshop）匯入的所有資產、使用 Visual Studio 或您最愛的程式碼編輯器建立的所有程式碼，以及當您在編輯器中撰寫場景、動畫和其他 Unity 資產類型時，Unity 所建立的任何內容檔案數目。</span><span class="sxs-lookup"><span data-stu-id="a36c1-123">This is the folder that holds all assets you import from digital content creation tools such as Maya, Max Cinema 4D or Photoshop, all code you create with Visual Studio or your favorite code editor, and any number of content files that Unity creates as you compose scenes, animations and other Unity asset types in the editor.</span></span>

<span data-ttu-id="a36c1-124">若要建立及部署 UWP 應用程式，Unity 可以將專案匯出為 Visual Studio 方案，其中包含所有必要的資產和程式碼檔案。</span><span class="sxs-lookup"><span data-stu-id="a36c1-124">To build and deploy UWP apps, Unity can export the project as a Visual Studio solution that will contain all necessary asset and code files.</span></span>

1. <span data-ttu-id="a36c1-125">啟動 Unity</span><span class="sxs-lookup"><span data-stu-id="a36c1-125">Start Unity</span></span>
2. <span data-ttu-id="a36c1-126">選取 [新增]</span><span class="sxs-lookup"><span data-stu-id="a36c1-126">Select **New**</span></span>
3. <span data-ttu-id="a36c1-127">輸入 (的專案名稱，例如 "MixedRealityIntroduction" ) </span><span class="sxs-lookup"><span data-stu-id="a36c1-127">Enter a project name (e.g. "MixedRealityIntroduction")</span></span>
4. <span data-ttu-id="a36c1-128">輸入儲存專案的位置</span><span class="sxs-lookup"><span data-stu-id="a36c1-128">Enter a location to save your project</span></span>
5. <span data-ttu-id="a36c1-129">確定已選取 **3d** 切換</span><span class="sxs-lookup"><span data-stu-id="a36c1-129">Ensure the **3D** toggle is selected</span></span>
6. <span data-ttu-id="a36c1-130">選取 [**建立專案**]</span><span class="sxs-lookup"><span data-stu-id="a36c1-130">Select **Create project**</span></span>

<span data-ttu-id="a36c1-131">恭喜，您現在已設定好開始使用您的混合現實自訂。</span><span class="sxs-lookup"><span data-stu-id="a36c1-131">Congrats, you are all setup to get started with your mixed reality customizations now.</span></span>

## <a name="chapter-2---setup-the-camera"></a><span data-ttu-id="a36c1-132">第2章-設定相機</span><span class="sxs-lookup"><span data-stu-id="a36c1-132">Chapter 2 - Setup the Camera</span></span>

>[!VIDEO https://www.youtube.com/embed/eP1ZwB4wSNA]

<span data-ttu-id="a36c1-133">Unity 主要攝影機會處理前端追蹤和 stereoscopic 轉譯。</span><span class="sxs-lookup"><span data-stu-id="a36c1-133">The Unity Main Camera handles head tracking and stereoscopic rendering.</span></span> <span data-ttu-id="a36c1-134">主要攝影機有一些變更，可將其用於混合現實。</span><span class="sxs-lookup"><span data-stu-id="a36c1-134">There are a few changes to make to the Main Camera to use it with mixed reality.</span></span>

1. <span data-ttu-id="a36c1-135">選取檔案 > 新場景</span><span class="sxs-lookup"><span data-stu-id="a36c1-135">Select File > New Scene</span></span>

<span data-ttu-id="a36c1-136">首先，如果您想像使用者的開始位置是 (**X**：0， **Y**：0， **Z**： 0) ，將會比較容易配置您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="a36c1-136">First, it will be easier to lay out your app if you imagine the starting position of the user as (**X**: 0, **Y**: 0, **Z**: 0).</span></span> <span data-ttu-id="a36c1-137">因為主要攝影機正在追蹤使用者的標頭移動，所以可以設定主要攝影機的開始位置來設定使用者的開始位置。</span><span class="sxs-lookup"><span data-stu-id="a36c1-137">Since the Main Camera is tracking movement of the user's head, the starting position of the user can be set by setting the starting position of the Main Camera.</span></span>

1. <span data-ttu-id="a36c1-138">選取 **[階層**] 面板中的 [**主要攝影機**]</span><span class="sxs-lookup"><span data-stu-id="a36c1-138">Select **Main Camera** in the **Hierarchy** panel</span></span>
2. <span data-ttu-id="a36c1-139">在 [偵測 **器** ] 面板中，尋找 [ **轉換** ] 元件，並將 **位置** 從 (**X**：0， **Y**：1， **Z**：-10) 變更為 (**X**：0， **y**：0， **Z**： 0) </span><span class="sxs-lookup"><span data-stu-id="a36c1-139">In the **Inspector** panel, find the **Transform** component and change the **Position** from (**X**: 0, **Y**: 1, **Z**: -10) to (**X**: 0, **Y**: 0, **Z**: 0)</span></span>

<span data-ttu-id="a36c1-140">其次，預設攝影機背景需要一些思考。</span><span class="sxs-lookup"><span data-stu-id="a36c1-140">Second, the default Camera background needs some thought.</span></span>

<span data-ttu-id="a36c1-141">**針對 HoloLens 應用程式**，真實世界應該會出現在相機呈現的所有專案，而不是 Skybox 材質的後方。</span><span class="sxs-lookup"><span data-stu-id="a36c1-141">**For HoloLens applications**, the real world should appear behind everything the camera renders, not a Skybox texture.</span></span>

1. <span data-ttu-id="a36c1-142">當 **主要攝影機** 仍在 [階層]**面板中** 選取時，請在 [**檢查**] 面板中尋找 **相機** 元件，並將 [**清除旗標**] 下拉式清單從 [ **Skybox** ] 變更為 [**純色**]。</span><span class="sxs-lookup"><span data-stu-id="a36c1-142">With the **Main Camera** still selected in the **Hierarchy** panel, find the **Camera** component in the **Inspector** panel and change the **Clear Flags** dropdown from **Skybox** to **Solid Color**.</span></span>
2. <span data-ttu-id="a36c1-143">選取 **背景** 色彩選擇器，並將 **RGBA** 值變更為 (0、0、0、0) </span><span class="sxs-lookup"><span data-stu-id="a36c1-143">Select the **Background** color picker and change the **RGBA** values to (0, 0, 0, 0)</span></span>

<span data-ttu-id="a36c1-144">**針對以沉浸式耳機為目標的混合現實應用程式**，我們可以使用 Unity 提供的預設 Skybox 材質。</span><span class="sxs-lookup"><span data-stu-id="a36c1-144">**For mixed reality applications targeted to immersive headsets**, we can use the default Skybox texture that Unity provides.</span></span>

1. <span data-ttu-id="a36c1-145">當 **主要攝影機** 仍在 [階層]**面板中** 選取時，請在 [偵測 **器**] 面板中尋找 **相機** 元件，並保留 [**清除旗標**] 下拉式清單以進行 **Skybox**。</span><span class="sxs-lookup"><span data-stu-id="a36c1-145">With the **Main Camera** still selected in the **Hierarchy** panel, find the **Camera** component in the **Inspector** panel and keep the **Clear Flags** dropdown to **Skybox**.</span></span>

<span data-ttu-id="a36c1-146">第三，讓我們考慮 Unity 中的近接裁剪平面，並防止在使用者接近使用者的情況下，將物件呈現太接近使用者眼睛。</span><span class="sxs-lookup"><span data-stu-id="a36c1-146">Third, let us consider the near clip plane in Unity and prevent objects from being rendered too close to the users eyes as a user approaches an object or an object approaches a user.</span></span>

<span data-ttu-id="a36c1-147">**針對 hololens 應用程式**，接近的裁剪平面可以設定為 [hololens 建議](../camera-in-unity.md#clip-planes) 的0.85 計量。</span><span class="sxs-lookup"><span data-stu-id="a36c1-147">**For HoloLens applications**, the near clip plane can be set to the [HoloLens recommended](../camera-in-unity.md#clip-planes) 0.85 meters.</span></span>

1. <span data-ttu-id="a36c1-148">當 **主要攝影機** 仍在 [階層]**面板中** 選取時，請在 [偵測 **器**] 面板中尋找 **相機** 元件，並將 **接近的剪輯平面** 欄位從預設的 **0.3** 變更為 HoloLens 建議的 **0.85**。</span><span class="sxs-lookup"><span data-stu-id="a36c1-148">With the **Main Camera** still selected in the **Hierarchy** panel, find the **Camera** component in the **Inspector** panel and change the **Near Clip Plane** field from the default **0.3** to the HoloLens recommended **0.85**.</span></span>

<span data-ttu-id="a36c1-149">**針對以沉浸式耳機為目標的混合現實應用程式**，我們可以使用 Unity 提供的預設設定。</span><span class="sxs-lookup"><span data-stu-id="a36c1-149">**For mixed reality applications targeted to immersive headsets**, we can use the default setting that Unity provides.</span></span>

1. <span data-ttu-id="a36c1-150">當 **主要攝影機** 仍在 [階層]**面板中** 選取時，請在 [偵測 **器**] 面板中尋找 **相機** 元件，並將 **接近的裁剪平面** 欄位保留為預設值 **0.3**。</span><span class="sxs-lookup"><span data-stu-id="a36c1-150">With the **Main Camera** still selected in the **Hierarchy** panel, find the **Camera** component in the **Inspector** panel and keep the **Near Clip Plane** field to the default **0.3**.</span></span>

<span data-ttu-id="a36c1-151">最後，讓我們來節省目前的進度。</span><span class="sxs-lookup"><span data-stu-id="a36c1-151">Finally, let us save our progress so far.</span></span> <span data-ttu-id="a36c1-152">若要儲存場景變更，請選取 [檔案] **> [另存場景**]、將場景命名為 **主要**，然後選取 [ **儲存**]。</span><span class="sxs-lookup"><span data-stu-id="a36c1-152">To save the scene changes, select **File > Save Scene As**, name the scene **Main**, and select **Save**.</span></span>

## <a name="chapter-3---setup-the-project-settings"></a><span data-ttu-id="a36c1-153">第3章-設定專案設定</span><span class="sxs-lookup"><span data-stu-id="a36c1-153">Chapter 3 - Setup the Project Settings</span></span>

>[!VIDEO https://www.youtube.com/embed/ItRoiXccC0g]

<span data-ttu-id="a36c1-154">在本章中，我們將設定一些 Unity 專案設定，以協助我們以 Windows 全像開發版 SDK 為目標。</span><span class="sxs-lookup"><span data-stu-id="a36c1-154">In this chapter, we will set some Unity project settings that help us target the Windows Holographic SDK for development.</span></span> <span data-ttu-id="a36c1-155">我們也會為應用程式設定一些品質設定。</span><span class="sxs-lookup"><span data-stu-id="a36c1-155">We will also set some quality settings for our application.</span></span> <span data-ttu-id="a36c1-156">最後，我們會確保組建目標設定為通用 Windows 平臺。</span><span class="sxs-lookup"><span data-stu-id="a36c1-156">Finally, we will ensure our build targets are set to Universal Windows Platform.</span></span>

### <a name="unity-performance-and-quality-settings"></a><span data-ttu-id="a36c1-157">Unity 效能和品質設定</span><span class="sxs-lookup"><span data-stu-id="a36c1-157">Unity performance and quality settings</span></span>

<span data-ttu-id="a36c1-158">**適用于 HoloLens 的 Unity 品質設定**</span><span class="sxs-lookup"><span data-stu-id="a36c1-158">**Unity quality settings for HoloLens**</span></span>

![適用于 HoloLens 的 Unity 品質設定](images/qualitysettings.png)

<span data-ttu-id="a36c1-160">由於在 HoloLens 上維持高幀率很重要，我們想要調整品質設定以獲得最快的效能。</span><span class="sxs-lookup"><span data-stu-id="a36c1-160">Since maintaining high framerate on HoloLens is so important, we want the quality settings tuned for fastest performance.</span></span> <span data-ttu-id="a36c1-161">如需更詳細的效能資訊，請瞭解 [Unity 的效能建議](../performance-recommendations-for-unity.md)。</span><span class="sxs-lookup"><span data-stu-id="a36c1-161">For more detailed performance information, [Performance recommendations for Unity](../performance-recommendations-for-unity.md).</span></span>

1. <span data-ttu-id="a36c1-162">選取 [ **編輯] > 專案設定 > 品質**</span><span class="sxs-lookup"><span data-stu-id="a36c1-162">Select **Edit > Project Settings > Quality**</span></span>
2. <span data-ttu-id="a36c1-163">選取 **通用 Windows 平臺** 標誌底下的 **下拉式清單**，然後選取 [**非常低**]。</span><span class="sxs-lookup"><span data-stu-id="a36c1-163">Select the **dropdown** under the **Universal Windows Platform** logo and select **Very Low**.</span></span> <span data-ttu-id="a36c1-164">當通用 Windows 平臺資料行中的方塊和 **非常低** 的資料列都是綠色時，您將會知道此設定已正確套用。</span><span class="sxs-lookup"><span data-stu-id="a36c1-164">You'll know the setting is applied correctly when the box in the Universal Windows Platform column and **Very Low** row is green.</span></span>

<span data-ttu-id="a36c1-165">**對於以 pixels occluded 顯示為目標的混合現實應用程式**，您可以將品質設定保留為其預設值。</span><span class="sxs-lookup"><span data-stu-id="a36c1-165">**For mixed reality applications targeted to occluded displays**, you can leave the quality settings to its default values.</span></span>

### <a name="target-windows-10-sdk"></a><span data-ttu-id="a36c1-166">目標 Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="a36c1-166">Target Windows 10 SDK</span></span>

<span data-ttu-id="a36c1-167">**以 Windows 全像攝影 SDK 為目標**</span><span class="sxs-lookup"><span data-stu-id="a36c1-167">**Target Windows Holographic SDK**</span></span>

![以 Windows 全像攝影 SDK 為目標](../images/xrsettings.png)

<span data-ttu-id="a36c1-169">我們需要讓 Unity 知道我們想要匯出的應用程式應該建立一個 [沉浸式視圖](../../../design/app-views.md) ，而不是2d 視圖。</span><span class="sxs-lookup"><span data-stu-id="a36c1-169">We need to let Unity know that the app we are trying to export should create an [immersive view](../../../design/app-views.md) instead of a 2D view.</span></span> <span data-ttu-id="a36c1-170">若要這麼做，請在以 Windows 10 SDK 為目標的 Unity 上啟用虛擬實境支援。</span><span class="sxs-lookup"><span data-stu-id="a36c1-170">We do this by enabling Virtual Reality support on Unity targeting the Windows 10 SDK.</span></span>

1. <span data-ttu-id="a36c1-171">移至 **> Player 的 [編輯 > 專案設定**]。</span><span class="sxs-lookup"><span data-stu-id="a36c1-171">Go to **Edit > Project Settings > Player**.</span></span>
2. <span data-ttu-id="a36c1-172">在 [播放程式設定] 的 [偵測 **器] 面板** 中，選取 **通用 Windows 平臺** 圖示。</span><span class="sxs-lookup"><span data-stu-id="a36c1-172">In the **Inspector Panel** for Player Settings, select the **Universal Windows Platform** icon.</span></span>
3. <span data-ttu-id="a36c1-173">展開 [XR 設定] 群組。</span><span class="sxs-lookup"><span data-stu-id="a36c1-173">Expand the **XR Settings** group.</span></span>
4. <span data-ttu-id="a36c1-174">在 [轉譯] 區段中核取 [支援虛擬實境] 核取方塊，以新增 [虛擬實境 SDK] 清單。</span><span class="sxs-lookup"><span data-stu-id="a36c1-174">In the **Rendering** section, check the **Virtual Reality Supported** checkbox to add a new **Virtual Reality SDKs** list.</span></span>
5. <span data-ttu-id="a36c1-175">確認 **Windows Mixed Reality** 出現在清單中。</span><span class="sxs-lookup"><span data-stu-id="a36c1-175">Verify that **Windows Mixed Reality** appears in the list.</span></span> <span data-ttu-id="a36c1-176">如果沒有，請選取清單底部的 **+** 按鈕，然後選擇 [Windows Mixed Reality]。</span><span class="sxs-lookup"><span data-stu-id="a36c1-176">If not, select the **+** button at the bottom of the list and choose **Windows Mixed Reality**.</span></span>

>[!NOTE]
><span data-ttu-id="a36c1-177">如果您看不到 **通用 Windows 平臺** 圖示，請再次檢查以確定您已在安裝期間選取通用 Windows 平臺組建支援。</span><span class="sxs-lookup"><span data-stu-id="a36c1-177">If you do not see the **Universal Windows Platform** icon, double check to make sure you selected Universal Windows Platform Build Support during installation.</span></span> <span data-ttu-id="a36c1-178">如果沒有，您可能需要以正確的 Windows 安裝重新安裝 Unity。</span><span class="sxs-lookup"><span data-stu-id="a36c1-178">If not, you may need to reinstall Unity with the correct Windows installation.</span></span>

<span data-ttu-id="a36c1-179">取得所有專案設定的絕佳工作。</span><span class="sxs-lookup"><span data-stu-id="a36c1-179">Awesome job on getting all the project settings applied.</span></span> <span data-ttu-id="a36c1-180">接下來，我們要新增一張全像</span><span class="sxs-lookup"><span data-stu-id="a36c1-180">Next, let us add a hologram!</span></span>

## <a name="chapter-4---create-a-cube"></a><span data-ttu-id="a36c1-181">第4章-建立 cube</span><span class="sxs-lookup"><span data-stu-id="a36c1-181">Chapter 4 - Create a cube</span></span>

>[!VIDEO https://www.youtube.com/embed/qKcK1Yuj-HQ]

<span data-ttu-id="a36c1-182">在 Unity 專案中建立 cube 就像是在 Unity 中建立任何其他物件一樣。</span><span class="sxs-lookup"><span data-stu-id="a36c1-182">Creating a cube in your Unity project is just like creating any other object in Unity.</span></span> <span data-ttu-id="a36c1-183">將 cube 放在使用者的前方很容易，因為 Unity 的座標系統對應到真實世界，其中一個在 Unity 中的計量大約是真實世界中的一個計量。</span><span class="sxs-lookup"><span data-stu-id="a36c1-183">Placing a cube in front of the user is easy because Unity's coordinate system is mapped to the real world - where one meter in Unity is approximately one meter in the real world.</span></span>

1. <span data-ttu-id="a36c1-184">**在 [階層] 面板左上** 角，選取 [**建立**] 下拉式清單，然後選擇 [ **3d 物件 > Cube**]。</span><span class="sxs-lookup"><span data-stu-id="a36c1-184">In the top left corner of the **Hierarchy** panel, select the **Create** dropdown and choose **3D Object > Cube**.</span></span>
2. <span data-ttu-id="a36c1-185">**在 [階層] 面板中** 選取新建立的 **Cube**</span><span class="sxs-lookup"><span data-stu-id="a36c1-185">Select the newly created **Cube** in the **Hierarchy** panel</span></span>
3. <span data-ttu-id="a36c1-186">在偵測 **器** 中找出 **轉換** 元件，並將 **位置** 變更為 (**X**：0， **Y**：0， **Z**： 2) 。</span><span class="sxs-lookup"><span data-stu-id="a36c1-186">In the **Inspector** find the **Transform** component and change **Position** to (**X**: 0, **Y**: 0, **Z**: 2).</span></span> <span data-ttu-id="a36c1-187">*這會將 cube 2 計量置於使用者開始位置的前方。*</span><span class="sxs-lookup"><span data-stu-id="a36c1-187">*This positions the cube 2 meters in front of the user's starting position.*</span></span>
4. <span data-ttu-id="a36c1-188">在 **轉換** 元件中，將 **旋轉** 變更為 (**X**：45、 **Y**：45、 **Z**： 45) ，然後將 **比例** 變更為 (**X**：0.25， **y**：0.25， **Z**： 0.25) 。</span><span class="sxs-lookup"><span data-stu-id="a36c1-188">In the **Transform** component, change **Rotation** to (**X**: 45, **Y**: 45, **Z**: 45) and change **Scale** to (**X**: 0.25, **Y**: 0.25, **Z**: 0.25).</span></span> <span data-ttu-id="a36c1-189">*這會將 cube 調整為0.25 計量。*</span><span class="sxs-lookup"><span data-stu-id="a36c1-189">*This scales the cube to 0.25 meters.*</span></span>
5. <span data-ttu-id="a36c1-190">若要儲存場景變更，請選取 [檔案] **> 儲存場景**]。</span><span class="sxs-lookup"><span data-stu-id="a36c1-190">To save the scene changes, select **File > Save Scene**.</span></span>

## <a name="chapter-5---verify-on-device-from-unity-editor"></a><span data-ttu-id="a36c1-191">第5章-從 Unity 編輯器確認裝置</span><span class="sxs-lookup"><span data-stu-id="a36c1-191">Chapter 5 - Verify on device from Unity editor</span></span>

>[!VIDEO https://www.youtube.com/embed/vmCfiIdRb6Q]

<span data-ttu-id="a36c1-192">既然我們已建立了 cube，現在就可以快速檢查裝置。</span><span class="sxs-lookup"><span data-stu-id="a36c1-192">Now that we have created our cube, it is time to do a quick check in device.</span></span> <span data-ttu-id="a36c1-193">您可以直接從 Unity 編輯器內進行此作業。</span><span class="sxs-lookup"><span data-stu-id="a36c1-193">You can do this directly from within the Unity editor.</span></span>

### <a name="initial-setup"></a><span data-ttu-id="a36c1-194">初始設定</span><span class="sxs-lookup"><span data-stu-id="a36c1-194">Initial setup</span></span>

1. <span data-ttu-id="a36c1-195">在您的開發電腦上，于 Unity 的 [ **組建設定** ] 視窗中開啟 [檔案] >。</span><span class="sxs-lookup"><span data-stu-id="a36c1-195">On your development PC, in Unity, open **File > Build Settings** window.</span></span>
2. <span data-ttu-id="a36c1-196">將 **平臺** 變更為 **通用 Windows 平臺**，然後按一下 [**切換平臺**]</span><span class="sxs-lookup"><span data-stu-id="a36c1-196">Change **Platform** to **Universal Windows Platform** and click **Switch Platform**</span></span>

### <a name="for-hololens-use-unity-remoting"></a><span data-ttu-id="a36c1-197">針對 HoloLens，請使用 Unity Remoting</span><span class="sxs-lookup"><span data-stu-id="a36c1-197">For HoloLens use Unity Remoting</span></span>

1. <span data-ttu-id="a36c1-198">在 HoloLens 上，安裝並執行可從 Windows 市集中取得的全像 [遠端播放機](../../platform-capabilities-and-apis/holographic-remoting-player.md)。</span><span class="sxs-lookup"><span data-stu-id="a36c1-198">On your HoloLens, install and run the [Holographic Remoting Player](../../platform-capabilities-and-apis/holographic-remoting-player.md), available from the Windows Store.</span></span> <span data-ttu-id="a36c1-199">在裝置上啟動應用程式，它會進入等候狀態，並顯示裝置的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="a36c1-199">Launch the application on the device, and it will enter a waiting state and show the IP address of the device.</span></span> <span data-ttu-id="a36c1-200">記下 IP。</span><span class="sxs-lookup"><span data-stu-id="a36c1-200">Note down the IP.</span></span>
2. <span data-ttu-id="a36c1-201">開啟 **Window > XR >** 全像全像模擬。</span><span class="sxs-lookup"><span data-stu-id="a36c1-201">Open **Window > XR > Holographic Emulation**.</span></span>
3. <span data-ttu-id="a36c1-202">將 **模擬模式** 從 [ **無** ] 變更為 [ **遠端] 至 [裝置**]。</span><span class="sxs-lookup"><span data-stu-id="a36c1-202">Change **Emulation Mode** from **None** to **Remote to Device**.</span></span>
4. <span data-ttu-id="a36c1-203">在 [ **遠端電腦**] 中，輸入您先前記下的 HoloLens IP 位址。</span><span class="sxs-lookup"><span data-stu-id="a36c1-203">In **Remote Machine**, enter the IP address of your HoloLens noted earlier.</span></span>
5. <span data-ttu-id="a36c1-204">按一下 [連線]。</span><span class="sxs-lookup"><span data-stu-id="a36c1-204">Click **Connect**.</span></span>
6. <span data-ttu-id="a36c1-205">確定連線 **狀態** 變更為綠色 **已連線**。</span><span class="sxs-lookup"><span data-stu-id="a36c1-205">Ensure the **Connection Status** changes to green **Connected**.</span></span>
7. <span data-ttu-id="a36c1-206">現在您可以在 Unity 編輯器中按一下 [ **播放** ]。</span><span class="sxs-lookup"><span data-stu-id="a36c1-206">Now you can now click **Play** in the Unity editor.</span></span>

<span data-ttu-id="a36c1-207">您現在可以在 [裝置] 和編輯器中看到 cube。</span><span class="sxs-lookup"><span data-stu-id="a36c1-207">You will now be able to see the cube in device and in the editor.</span></span> <span data-ttu-id="a36c1-208">您可以像在編輯器中執行應用程式一樣暫停、檢查物件和進行偵錯工具，因為這基本上是發生的情況，但在主機電腦與裝置之間的網路上來回傳輸了影片、音訊和裝置輸入。</span><span class="sxs-lookup"><span data-stu-id="a36c1-208">You can pause, inspect objects, and debug just like you are running an app in the editor, because that's essentially what's happening, but with video, audio, and device input transmitted back and forth across the network between the host machine and the device.</span></span>

### <a name="for-other-mixed-reality-supported-headsets"></a><span data-ttu-id="a36c1-209">適用于其他 mixed reality 支援的耳機</span><span class="sxs-lookup"><span data-stu-id="a36c1-209">For other mixed reality supported headsets</span></span>

1. <span data-ttu-id="a36c1-210">使用 USB 纜線和 HDMI 或顯示器埠纜線，將耳機連接到您的開發電腦。</span><span class="sxs-lookup"><span data-stu-id="a36c1-210">Connect the headset to your development PC using the USB cable and the HDMI or display port cable.</span></span>
2. <span data-ttu-id="a36c1-211">啟動 **混合實境入口** ，並確定您已完成第一次執行體驗。</span><span class="sxs-lookup"><span data-stu-id="a36c1-211">Launch the **Mixed Reality Portal** and ensure you have completed the first run experience.</span></span>
3. <span data-ttu-id="a36c1-212">您現在可以從 Unity 按下 [播放] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="a36c1-212">From Unity, you can now press the Play button.</span></span>

<span data-ttu-id="a36c1-213">您現在可以在混合現實耳機和編輯器中看到 cube 轉譯。</span><span class="sxs-lookup"><span data-stu-id="a36c1-213">You will now be able to see the cube rendering in your mixed reality headset and in the editor.</span></span>

## <a name="chapter-6---build-and-deploy-to-device-from-visual-studio"></a><span data-ttu-id="a36c1-214">第6章-從 Visual Studio 建立並部署至裝置</span><span class="sxs-lookup"><span data-stu-id="a36c1-214">Chapter 6 - Build and deploy to device from Visual Studio</span></span>

>[!VIDEO https://www.youtube.com/embed/USSu8yHUdbk]

<span data-ttu-id="a36c1-215">我們現在已準備好要編譯專案，以 Visual Studio 並部署至目標裝置。</span><span class="sxs-lookup"><span data-stu-id="a36c1-215">We are now ready to compile our project to Visual Studio and deploy to our target device.</span></span>

### <a name="export-to-the-visual-studio-solution"></a><span data-ttu-id="a36c1-216">匯出至 Visual Studio 解決方案</span><span class="sxs-lookup"><span data-stu-id="a36c1-216">Export to the Visual Studio solution</span></span>

1. <span data-ttu-id="a36c1-217">開啟 [檔案 **> 組建設定** ] 視窗。</span><span class="sxs-lookup"><span data-stu-id="a36c1-217">Open **File > Build Settings** window.</span></span>
1. <span data-ttu-id="a36c1-218">按一下 [ **新增開啟場景** ] 以加入場景。</span><span class="sxs-lookup"><span data-stu-id="a36c1-218">Click **Add Open Scenes** to add the scene.</span></span>
1. <span data-ttu-id="a36c1-219">將 **平臺** 變更為 **通用 Windows 平臺** ，然後按一下 [ **切換平臺**]。</span><span class="sxs-lookup"><span data-stu-id="a36c1-219">Change **Platform** to **Universal Windows Platform** and click **Switch Platform**.</span></span>
1. <span data-ttu-id="a36c1-220">在 **通用 Windows 平臺** 設定] 中，確定 [ **SDK** ] 是 [ **通用] 10**。</span><span class="sxs-lookup"><span data-stu-id="a36c1-220">In **Universal Windows Platform** settings, ensure **SDK** is **Universal 10**.</span></span>
1. <span data-ttu-id="a36c1-221">針對目標裝置，請離開 **任何裝置** 以進行 pixels occluded 顯示或切換至 **HoloLens**。</span><span class="sxs-lookup"><span data-stu-id="a36c1-221">For Target device, leave to **Any Device** for occluded displays or switch to **HoloLens**.</span></span>
1. <span data-ttu-id="a36c1-222">**UWP 組建類型** 應該是 **D3D**。</span><span class="sxs-lookup"><span data-stu-id="a36c1-222">**UWP Build Type** should be **D3D**.</span></span>
1. <span data-ttu-id="a36c1-223">**UWP SDK** 可以保留 **最新的安裝**。</span><span class="sxs-lookup"><span data-stu-id="a36c1-223">**UWP SDK** could be left at **Latest installed**.</span></span>
1. <span data-ttu-id="a36c1-224">按一下 [建置]。</span><span class="sxs-lookup"><span data-stu-id="a36c1-224">Click **Build**.</span></span>
1. <span data-ttu-id="a36c1-225">在 [檔案瀏覽器] 中，按一下 [ **新增資料夾** ]，然後將資料夾命名為 **"App"**。</span><span class="sxs-lookup"><span data-stu-id="a36c1-225">In the file explorer, click **New Folder** and name the folder **"App"**.</span></span>
1. <span data-ttu-id="a36c1-226">選取 **應用程式** 資料夾，然後按一下 [ **選取資料夾** ] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="a36c1-226">With the **App** folder selected, click the **Select Folder** button.</span></span>
1. <span data-ttu-id="a36c1-227">當 Unity 完成建立時，將會出現 Windows 檔案總管視窗。</span><span class="sxs-lookup"><span data-stu-id="a36c1-227">When Unity is done building, a Windows File Explorer window will appear.</span></span>
1. <span data-ttu-id="a36c1-228">在 [檔案瀏覽器] 中開啟 **應用程式** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="a36c1-228">Open the **App** folder in file explorer.</span></span>
1. <span data-ttu-id="a36c1-229">在此範例中， (MixedRealityIntroduction 開啟產生的 Visual Studio 方案) </span><span class="sxs-lookup"><span data-stu-id="a36c1-229">Open the generated Visual Studio solution (MixedRealityIntroduction.sln in this example)</span></span>

### <a name="compile-the-visual-studio-solution"></a><span data-ttu-id="a36c1-230">編譯 Visual Studio 解決方案</span><span class="sxs-lookup"><span data-stu-id="a36c1-230">Compile the Visual Studio solution</span></span>

<span data-ttu-id="a36c1-231">最後，我們將編譯匯出的 Visual Studio 解決方案、加以部署，然後在裝置上試用。</span><span class="sxs-lookup"><span data-stu-id="a36c1-231">Finally, we will compile the exported Visual Studio solution, deploy it, and try it out on the device.</span></span>

1. <span data-ttu-id="a36c1-232">使用 Visual Studio 中的頂端工具列，將目標從 **Debug** 變更為 **Release** ，以及從 **ARM** 變更為 **X86**。</span><span class="sxs-lookup"><span data-stu-id="a36c1-232">Using the top toolbar in Visual Studio, change the target from **Debug** to **Release** and from **ARM** to **X86**.</span></span>

<span data-ttu-id="a36c1-233">部署至裝置與模擬器的指示不同。</span><span class="sxs-lookup"><span data-stu-id="a36c1-233">The instructions differ for deploying to a device versus the emulator.</span></span> <span data-ttu-id="a36c1-234">遵循符合您設定的指示進行。</span><span class="sxs-lookup"><span data-stu-id="a36c1-234">Follow the instructions that match your setup.</span></span>

### <a name="deploy-to-mixed-reality-device-over-wi-fi"></a><span data-ttu-id="a36c1-235">透過 Wi-Fi 部署至混合現實裝置</span><span class="sxs-lookup"><span data-stu-id="a36c1-235">Deploy to mixed reality device over Wi-Fi</span></span>

1. <span data-ttu-id="a36c1-236">按一下 [ **本機電腦** ] 按鈕旁的箭號，然後將部署目標變更為 [ **遠端電腦**]。</span><span class="sxs-lookup"><span data-stu-id="a36c1-236">Click on the arrow next to the **Local Machine** button, and change the deployment target to **Remote Machine**.</span></span>
2. <span data-ttu-id="a36c1-237">輸入您的混合現實裝置的 IP 位址，並將 **驗證模式** 變更為適用于 HoloLens 和 **Windows** 的通用 (未加密通訊協定) 的其他裝置。</span><span class="sxs-lookup"><span data-stu-id="a36c1-237">Enter the IP address of your mixed reality device and change **Authentication Mode** to Universal (Unencrypted Protocol) for HoloLens and **Windows** for other devices.</span></span>
3. <span data-ttu-id="a36c1-238">按一下 [ **Debug] > 啟動但不進行調試**。</span><span class="sxs-lookup"><span data-stu-id="a36c1-238">Click **Debug > Start without debugging**.</span></span>

<span data-ttu-id="a36c1-239">**針對 HoloLens**，如果這是您第一次部署至您的裝置，您必須 [使用 Visual Studio](../../platform-capabilities-and-apis/using-visual-studio.md)配對。</span><span class="sxs-lookup"><span data-stu-id="a36c1-239">**For HoloLens**, If this is the first time deploying to your device, you will need to pair [using Visual Studio](../../platform-capabilities-and-apis/using-visual-studio.md).</span></span>

### <a name="deploy-to-mixed-reality-device-over-usb"></a><span data-ttu-id="a36c1-240">透過 USB 部署至混合現實裝置</span><span class="sxs-lookup"><span data-stu-id="a36c1-240">Deploy to mixed reality device over USB</span></span>

<span data-ttu-id="a36c1-241">確定您已透過 USB 纜線插入裝置。</span><span class="sxs-lookup"><span data-stu-id="a36c1-241">Ensure you device is plugged in via the USB cable.</span></span>

1. <span data-ttu-id="a36c1-242">若 **為 HoloLens**，請按一下 [**本機電腦**] 按鈕旁的箭號，然後將部署目標變更為 [**裝置**]。</span><span class="sxs-lookup"><span data-stu-id="a36c1-242">**For HoloLens**, click on the arrow next to the **Local Machine** button, and change the deployment target to **Device**.</span></span>
2. <span data-ttu-id="a36c1-243">**針對連接到您電腦的 pixels occluded 裝置**，將設定保留在 [本機電腦]。</span><span class="sxs-lookup"><span data-stu-id="a36c1-243">**For targeting occluded devices attached to your PC**, keep the setting to Local Machine.</span></span> <span data-ttu-id="a36c1-244">確定您的 **混合實境入口** 正在執行。</span><span class="sxs-lookup"><span data-stu-id="a36c1-244">Ensure you have the **Mixed Reality Portal** running.</span></span>
3. <span data-ttu-id="a36c1-245">按一下 [ **Debug] > 啟動但不進行調試**。</span><span class="sxs-lookup"><span data-stu-id="a36c1-245">Click **Debug > Start without debugging**.</span></span>

### <a name="deploy-to-emulator"></a><span data-ttu-id="a36c1-246">部署至模擬器</span><span class="sxs-lookup"><span data-stu-id="a36c1-246">Deploy to Emulator</span></span>

1. <span data-ttu-id="a36c1-247">按一下 [ **裝置** ] 按鈕旁邊的箭號，然後從下拉式清單中選取 [ **HoloLens 模擬器**]。</span><span class="sxs-lookup"><span data-stu-id="a36c1-247">Click on the arrow next to the **Device** button, and from drop down select **HoloLens Emulator**.</span></span>
2. <span data-ttu-id="a36c1-248">按一下 [ **Debug] > 啟動但不進行調試**。</span><span class="sxs-lookup"><span data-stu-id="a36c1-248">Click **Debug > Start without debugging**.</span></span>

### <a name="try-out-your-app"></a><span data-ttu-id="a36c1-249">試用您的應用程式</span><span class="sxs-lookup"><span data-stu-id="a36c1-249">Try out your app</span></span>

<span data-ttu-id="a36c1-250">現在已部署您的應用程式，請嘗試在整個 cube 周圍移動，然後觀察它是否存在於世界的前方。</span><span class="sxs-lookup"><span data-stu-id="a36c1-250">Now that your app is deployed, try moving all around the cube and observe that it stays in the world in front of you.</span></span>

## <a name="see-also"></a><span data-ttu-id="a36c1-251">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a36c1-251">See also</span></span>

* [<span data-ttu-id="a36c1-252">Unity 開發概觀</span><span class="sxs-lookup"><span data-stu-id="a36c1-252">Unity development overview</span></span>](../unity-development-overview.md)
* [<span data-ttu-id="a36c1-253">使用 Unity 和 Visual Studio 的最佳作法</span><span class="sxs-lookup"><span data-stu-id="a36c1-253">Best practices for working with Unity and Visual Studio</span></span>](../best-practices-for-working-with-unity-and-visual-studio.md)
* [<span data-ttu-id="a36c1-254">MR Basics 101</span><span class="sxs-lookup"><span data-stu-id="a36c1-254">MR Basics 101</span></span>](holograms-101.md)
* [<span data-ttu-id="a36c1-255">MR Basics 101E</span><span class="sxs-lookup"><span data-stu-id="a36c1-255">MR Basics 101E</span></span>](holograms-101e.md)