---
title: MR Basics 101E - 使用模擬器完成專案
description: 遵循此程式碼逐步解說，以使用 Unity、Visual Studio 和 HoloLens 模擬器來學習全像全像攝影應用程式的基本概念。
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: mixed reality、Windows Mixed Reality、全息圖、學術、教學課程、模擬器、HoloLens、混合的現實學術、unity、混合現實耳機、Windows Mixed reality 耳機、虛擬實境耳機、Windows 10、注視、手勢、語音輸入、空間音效、空間對應
ms.openlocfilehash: afe62dbc3385b41d08011bf7893672272f25485b
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583697"
---
# <a name="mr-basics-101e-complete-project-with-emulator"></a><span data-ttu-id="66926-104">MR Basics 101E：使用模擬器完成專案</span><span class="sxs-lookup"><span data-stu-id="66926-104">MR Basics 101E: Complete project with emulator</span></span>

>[!NOTE]
><span data-ttu-id="66926-105">混合實境學院教學課程的設計是以 HoloLens (第 1 代) 和混合實境沉浸式頭戴裝置為準。</span><span class="sxs-lookup"><span data-stu-id="66926-105">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="66926-106">因此，對於仍在尋找這些裝置開發指引的開發人員而言，我們覺得這些教學課程很重要。</span><span class="sxs-lookup"><span data-stu-id="66926-106">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="66926-107">這些教學課程 **_不會_** 使用用於 HoloLens 2 的最新工具組或互動進行更新。</span><span class="sxs-lookup"><span data-stu-id="66926-107">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="66926-108">系統會保留這些資訊，以繼續在支援的裝置上運作。</span><span class="sxs-lookup"><span data-stu-id="66926-108">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="66926-109">已針對 HoloLens 2 公佈[一系列新的教學課程](mrlearning-base.md)。</span><span class="sxs-lookup"><span data-stu-id="66926-109">[A new series of tutorials](mrlearning-base.md) has been posted for HoloLens 2.</span></span>

<br>

 >[!VIDEO https://www.youtube.com/embed/Xzm8_s05mm8]

<span data-ttu-id="66926-110">本教學課程將逐步引導您完成內建 Unity 的完整專案，以示範 HoloLens 上的核心 Windows Mixed Reality 功能，包括 [注視](../../../design/gaze-and-commit.md)、 [手勢](../../../design/gaze-and-commit.md#composite-gestures)、 [語音輸入](../../../design/voice-input.md)、 [空間音效](../../../design/spatial-sound.md) 和 [空間對應](../../../design/spatial-mapping.md)。</span><span class="sxs-lookup"><span data-stu-id="66926-110">This tutorial will walk you through a complete project, built in Unity, that demonstrates core Windows Mixed Reality features on HoloLens including [gaze](../../../design/gaze-and-commit.md), [gestures](../../../design/gaze-and-commit.md#composite-gestures), [voice input](../../../design/voice-input.md), [spatial sound](../../../design/spatial-sound.md) and [spatial mapping](../../../design/spatial-mapping.md).</span></span> <span data-ttu-id="66926-111">本教學課程需要大約1小時才能完成。</span><span class="sxs-lookup"><span data-stu-id="66926-111">The tutorial will take approximately 1 hour to complete.</span></span>

## <a name="device-support"></a><span data-ttu-id="66926-112">裝置支援</span><span class="sxs-lookup"><span data-stu-id="66926-112">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="66926-113">課程</span><span class="sxs-lookup"><span data-stu-id="66926-113">Course</span></span></th><th style="width:150px"> <span data-ttu-id="66926-114"><a href="/hololens/hololens1-hardware">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="66926-114"><a href="/hololens/hololens1-hardware">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="66926-115"><a href="../../../discover/immersive-headset-hardware-details.md">沉浸式頭戴裝置</a></span><span class="sxs-lookup"><span data-stu-id="66926-115"><a href="../../../discover/immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="66926-116">MR Basics 101E：使用模擬器完成專案</span><span class="sxs-lookup"><span data-stu-id="66926-116">MR Basics 101E: Complete project with emulator</span></span></td><td style="text-align: center;"> <span data-ttu-id="66926-117">✔️</span><span class="sxs-lookup"><span data-stu-id="66926-117">✔️</span></span></td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="66926-118">在您開始使用 Intune 之前</span><span class="sxs-lookup"><span data-stu-id="66926-118">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="66926-119">必要條件</span><span class="sxs-lookup"><span data-stu-id="66926-119">Prerequisites</span></span>

* <span data-ttu-id="66926-120">[已安裝正確工具](../../install-the-tools.md)的 Windows 10 電腦。</span><span class="sxs-lookup"><span data-stu-id="66926-120">A Windows 10 PC configured with the correct [tools installed](../../install-the-tools.md).</span></span>

### <a name="project-files"></a><span data-ttu-id="66926-121">專案檔</span><span class="sxs-lookup"><span data-stu-id="66926-121">Project files</span></span>

* <span data-ttu-id="66926-122">下載專案 [所需的](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-101.zip) 檔案。</span><span class="sxs-lookup"><span data-stu-id="66926-122">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-101.zip) required by the project.</span></span> <span data-ttu-id="66926-123">需要 Unity 2017.2 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="66926-123">Requires Unity 2017.2 or later.</span></span>
  * <span data-ttu-id="66926-124">如果您仍然需要 Unity 5.6 支援，請使用 [此版本](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-101.zip)。</span><span class="sxs-lookup"><span data-stu-id="66926-124">If you still need Unity 5.6 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-101.zip).</span></span>
  * <span data-ttu-id="66926-125">如果您仍然需要 Unity 5.5 支援，請使用 [此版本](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-101.zip)。</span><span class="sxs-lookup"><span data-stu-id="66926-125">If you still need Unity 5.5 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-101.zip).</span></span>
  * <span data-ttu-id="66926-126">如果您仍然需要 Unity 5.4 支援，請使用 [此版本](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-101.zip)。</span><span class="sxs-lookup"><span data-stu-id="66926-126">If you still need Unity 5.4 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-101.zip).</span></span>
* <span data-ttu-id="66926-127">取消將檔案封存到您的桌面或其他易於觸及的位置。</span><span class="sxs-lookup"><span data-stu-id="66926-127">Un-archive the files to your desktop or other easy to reach location.</span></span> <span data-ttu-id="66926-128">將資料夾名稱保留為 **日式**。</span><span class="sxs-lookup"><span data-stu-id="66926-128">Keep the folder name as **Origami**.</span></span>

>[!NOTE]
><span data-ttu-id="66926-129">如果您想要在下載之前查看原始程式碼， [可在 GitHub 上](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-101)取得。</span><span class="sxs-lookup"><span data-stu-id="66926-129">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-101).</span></span>

## <a name="chapter-1---holo-world"></a><span data-ttu-id="66926-130">第1章-「Hololens」世界</span><span class="sxs-lookup"><span data-stu-id="66926-130">Chapter 1 - "Holo" world</span></span>

>[!VIDEO https://www.youtube.com/embed/qotpUpIQxVU]

<span data-ttu-id="66926-131">在本章中，我們將設定第一個 Unity 專案，並逐步執行組建和部署程式。</span><span class="sxs-lookup"><span data-stu-id="66926-131">In this chapter, we'll setup our first Unity project and step through the build and deploy process.</span></span>

### <a name="objectives"></a><span data-ttu-id="66926-132">目標</span><span class="sxs-lookup"><span data-stu-id="66926-132">Objectives</span></span>

* <span data-ttu-id="66926-133">設定 Unity 進行全像開發。</span><span class="sxs-lookup"><span data-stu-id="66926-133">Set up Unity for holographic development.</span></span>
* <span data-ttu-id="66926-134">製作全像影像。</span><span class="sxs-lookup"><span data-stu-id="66926-134">Make a hologram.</span></span>
* <span data-ttu-id="66926-135">查看您製作的全像影像。</span><span class="sxs-lookup"><span data-stu-id="66926-135">See a hologram that you made.</span></span>

### <a name="instructions"></a><span data-ttu-id="66926-136">指示</span><span class="sxs-lookup"><span data-stu-id="66926-136">Instructions</span></span>

* <span data-ttu-id="66926-137">啟動 Unity。</span><span class="sxs-lookup"><span data-stu-id="66926-137">Start Unity.</span></span>
* <span data-ttu-id="66926-138">選取 [開啟]  。</span><span class="sxs-lookup"><span data-stu-id="66926-138">Select **Open**.</span></span>
* <span data-ttu-id="66926-139">輸入 [位置] 作為您先前取消封存的 [ **折紙** ] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="66926-139">Enter location as the **Origami** folder you previously un-archived.</span></span>
* <span data-ttu-id="66926-140">選取 [ **折紙** ]，然後按一下 [ **選取資料夾**]。</span><span class="sxs-lookup"><span data-stu-id="66926-140">Select **Origami** and click **Select Folder**.</span></span>
* <span data-ttu-id="66926-141">儲存新場景： **File**  /  **Save 場景 As**。</span><span class="sxs-lookup"><span data-stu-id="66926-141">Save the new scene: **File** / **Save Scene As**.</span></span>
* <span data-ttu-id="66926-142">將場景命名為 **日式** ，然後按下 [ **儲存** ] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="66926-142">Name the scene **Origami** and press the **Save** button.</span></span>

#### <a name="setup-the-main-camera"></a><span data-ttu-id="66926-143">設定主要攝影機</span><span class="sxs-lookup"><span data-stu-id="66926-143">Setup the main camera</span></span>

* <span data-ttu-id="66926-144">在 [階層面板] 中，選取 [主要相機]。</span><span class="sxs-lookup"><span data-stu-id="66926-144">In the **Hierarchy Panel**, select **Main Camera**.</span></span>
* <span data-ttu-id="66926-145">在偵測 **器** 中，將其轉換位置設定為 **0、0、0**。</span><span class="sxs-lookup"><span data-stu-id="66926-145">In the **Inspector** set its transform position to **0,0,0**.</span></span>
* <span data-ttu-id="66926-146">尋找 [ **清除旗標** ] 屬性，並將下拉式清單從 [ **Skybox** ] 變更為 [ **純色**]。</span><span class="sxs-lookup"><span data-stu-id="66926-146">Find the **Clear Flags** property, and change the dropdown from **Skybox** to **Solid color**.</span></span>
* <span data-ttu-id="66926-147">按一下 [背景] 欄位，以開啟色彩選擇器。</span><span class="sxs-lookup"><span data-stu-id="66926-147">Click on the **Background** field to open a color picker.</span></span>
* <span data-ttu-id="66926-148">將 **R、G、B 和 A** 設為 **0**。</span><span class="sxs-lookup"><span data-stu-id="66926-148">Set **R, G, B, and A** to **0**.</span></span>

#### <a name="setup-the-scene"></a><span data-ttu-id="66926-149">設定場景</span><span class="sxs-lookup"><span data-stu-id="66926-149">Setup the scene</span></span>

* <span data-ttu-id="66926-150">在 [階層] **面板** 中，按一下 [ **建立** ] 並 **建立空白**。</span><span class="sxs-lookup"><span data-stu-id="66926-150">In the **Hierarchy Panel**, click on **Create** and **Create Empty**.</span></span>
* <span data-ttu-id="66926-151">以滑鼠右鍵按一下新的 **GameObject** ，然後選取 [重新命名]。</span><span class="sxs-lookup"><span data-stu-id="66926-151">Right-click the new **GameObject** and select Rename.</span></span> <span data-ttu-id="66926-152">將 GameObject 重新命名為 **OrigamiCollection**。</span><span class="sxs-lookup"><span data-stu-id="66926-152">Rename the GameObject to **OrigamiCollection**.</span></span>
* <span data-ttu-id="66926-153">從 [**專案] 面板** 中 **的 [全** 像全像] 資料夾：</span><span class="sxs-lookup"><span data-stu-id="66926-153">From the **Holograms** folder in the **Project Panel**:</span></span>
  * <span data-ttu-id="66926-154">將 [ **階段** ] 拖曳到階層中，成為 **OrigamiCollection** 的子系。</span><span class="sxs-lookup"><span data-stu-id="66926-154">Drag **Stage** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
  * <span data-ttu-id="66926-155">將 **Sphere1** 拖曳到階層中，以成為 **OrigamiCollection** 的子系。</span><span class="sxs-lookup"><span data-stu-id="66926-155">Drag **Sphere1** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
  * <span data-ttu-id="66926-156">將 **Sphere2** 拖曳到階層中，以成為 **OrigamiCollection** 的子系。</span><span class="sxs-lookup"><span data-stu-id="66926-156">Drag **Sphere2** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
* <span data-ttu-id="66926-157">以滑鼠右鍵按一下 [階層]**面板** 中的 **方向光源** 物件，然後選取 [**刪除**]。</span><span class="sxs-lookup"><span data-stu-id="66926-157">Right-click the **Directional Light** object in the **Hierarchy Panel** and select **Delete**.</span></span>
* <span data-ttu-id="66926-158">從 [全像 **] 資料夾，將\*\*\*\*燈光** 拖曳到階層 **面板** 的根目錄中。</span><span class="sxs-lookup"><span data-stu-id="66926-158">From the **Holograms** folder, drag **Lights** into the root of the **Hierarchy Panel**.</span></span>
* <span data-ttu-id="66926-159">**在階層中，選取** **OrigamiCollection**。</span><span class="sxs-lookup"><span data-stu-id="66926-159">In the **Hierarchy**, select the **OrigamiCollection**.</span></span>
* <span data-ttu-id="66926-160">在偵測 **器** 中，將轉換位置設定為 **0、-0.5、2.0**。</span><span class="sxs-lookup"><span data-stu-id="66926-160">In the **Inspector**, set the transform position to **0, -0.5, 2.0**.</span></span>
* <span data-ttu-id="66926-161">按下 Unity 中的 [ **播放** ] 按鈕，以預覽您的全像影像。</span><span class="sxs-lookup"><span data-stu-id="66926-161">Press the **Play** button in Unity to preview your holograms.</span></span>
* <span data-ttu-id="66926-162">您應該會在預覽視窗中看到 [折紙] 物件。</span><span class="sxs-lookup"><span data-stu-id="66926-162">You should see the Origami objects in the preview window.</span></span>
* <span data-ttu-id="66926-163">按第二次 [ **播放** ] 以停止預覽模式。</span><span class="sxs-lookup"><span data-stu-id="66926-163">Press **Play** a second time to stop preview mode.</span></span>

#### <a name="export-the-project-from-unity-to-visual-studio"></a><span data-ttu-id="66926-164">將專案從 Unity 匯出至 Visual Studio</span><span class="sxs-lookup"><span data-stu-id="66926-164">Export the project from Unity to Visual Studio</span></span>

* <span data-ttu-id="66926-165">在 Unity 中，選取 [ **File > Build Settings**]。</span><span class="sxs-lookup"><span data-stu-id="66926-165">In Unity select **File > Build Settings**.</span></span>
* <span data-ttu-id="66926-166">在 [**平臺**] 清單中選取 [ **Windows 存放區**]，然後按一下 [**切換平臺**]。</span><span class="sxs-lookup"><span data-stu-id="66926-166">Select **Windows Store** in the **Platform** list and click **Switch Platform**.</span></span>
* <span data-ttu-id="66926-167">將 **SDK** 設定為 **通用 10** ，並將 **組建類型** 設定為 **D3D**。</span><span class="sxs-lookup"><span data-stu-id="66926-167">Set **SDK** to **Universal 10** and **Build Type** to **D3D**.</span></span>
* <span data-ttu-id="66926-168">檢查 **Unity c # 專案**。</span><span class="sxs-lookup"><span data-stu-id="66926-168">Check **Unity C# Projects**.</span></span>
* <span data-ttu-id="66926-169">按一下 [ **新增開啟場景** ] 以加入場景。</span><span class="sxs-lookup"><span data-stu-id="66926-169">Click **Add Open Scenes** to add the scene.</span></span>
* <span data-ttu-id="66926-170">按一下 [ **播放的設定 ...**]。</span><span class="sxs-lookup"><span data-stu-id="66926-170">Click **Player Settings...**.</span></span>
* <span data-ttu-id="66926-171">在 [偵測器] 面板中，選取 [ **Windows Store] 標誌**。</span><span class="sxs-lookup"><span data-stu-id="66926-171">In the Inspector Panel select the **Windows Store logo**.</span></span> <span data-ttu-id="66926-172">然後選取 [ **發佈設定**]。</span><span class="sxs-lookup"><span data-stu-id="66926-172">Then select **Publishing Settings**.</span></span>
* <span data-ttu-id="66926-173">在 [ **功能** ] 區段中，選取 [ **麥克風** ] 和 [ **>spatialperception** ] 功能。</span><span class="sxs-lookup"><span data-stu-id="66926-173">In the **Capabilities** section, select the **Microphone** and **SpatialPerception** capabilities.</span></span>
* <span data-ttu-id="66926-174">回到 [組建設定] 視窗中，按一下 [ **建立**]。</span><span class="sxs-lookup"><span data-stu-id="66926-174">Back in the Build Settings window, click **Build**.</span></span>
* <span data-ttu-id="66926-175">建立名為 "App" 的 **新資料夾** 。</span><span class="sxs-lookup"><span data-stu-id="66926-175">Create a **New Folder** named "App".</span></span>
* <span data-ttu-id="66926-176">按一下 **應用程式資料夾**。</span><span class="sxs-lookup"><span data-stu-id="66926-176">Single click the **App Folder**.</span></span>
* <span data-ttu-id="66926-177">按下 [ **選取資料夾**]。</span><span class="sxs-lookup"><span data-stu-id="66926-177">Press **Select Folder**.</span></span>
* <span data-ttu-id="66926-178">當 Unity 完成時，將會出現檔案總管視窗。</span><span class="sxs-lookup"><span data-stu-id="66926-178">When Unity is done, a File Explorer window will appear.</span></span>
* <span data-ttu-id="66926-179">開啟 **應用程式** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="66926-179">Open the **App** folder.</span></span>
* <span data-ttu-id="66926-180">開啟 [ **日式 Visual Studio] 方案**。</span><span class="sxs-lookup"><span data-stu-id="66926-180">Open the **Origami Visual Studio Solution**.</span></span>
* <span data-ttu-id="66926-181">使用 Visual Studio 中的頂端工具列，將目標從 Debug 變更為 **Release** ，以及從 ARM 變更為 **X86**。</span><span class="sxs-lookup"><span data-stu-id="66926-181">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **X86**.</span></span>
  * <span data-ttu-id="66926-182">按一下 [裝置] 按鈕旁邊的箭號，然後選取 [ **HoloLens 模擬器**]。</span><span class="sxs-lookup"><span data-stu-id="66926-182">Click on the arrow next to the Device button, and select **HoloLens Emulator**.</span></span>
  * <span data-ttu-id="66926-183">按一下 [ **Debug-> 啟動但不進行調試]，** 或按 **Ctrl + F5**。</span><span class="sxs-lookup"><span data-stu-id="66926-183">Click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
  * <span data-ttu-id="66926-184">經過一段時間之後，模擬器就會以日式的專案開始。</span><span class="sxs-lookup"><span data-stu-id="66926-184">After some time the emulator will start with the Origami project.</span></span> <span data-ttu-id="66926-185">第一次啟動 [模擬器](../../platform-capabilities-and-apis/using-the-hololens-emulator.md)時，可能需要15分鐘的時間來啟動模擬器。</span><span class="sxs-lookup"><span data-stu-id="66926-185">When first launching the [emulator](../../platform-capabilities-and-apis/using-the-hololens-emulator.md), it can take as long as 15 minutes for the emulator to start up.</span></span> <span data-ttu-id="66926-186">一旦啟動，請不要關閉它。</span><span class="sxs-lookup"><span data-stu-id="66926-186">Once it starts, do not close it.</span></span>

## <a name="chapter-2---gaze"></a><span data-ttu-id="66926-187">第2章-注視</span><span class="sxs-lookup"><span data-stu-id="66926-187">Chapter 2 - Gaze</span></span>

>[!VIDEO https://www.youtube.com/embed/BPWTbAC210k]

<span data-ttu-id="66926-188">在本章中，我們將介紹三種與您的全像的影像互動的第一種方式： [注視](../../../design/gaze-and-commit.md)。</span><span class="sxs-lookup"><span data-stu-id="66926-188">In this chapter, we are going to introduce the first of three ways of interacting with your holograms -- [gaze](../../../design/gaze-and-commit.md).</span></span>

### <a name="objectives"></a><span data-ttu-id="66926-189">目標</span><span class="sxs-lookup"><span data-stu-id="66926-189">Objectives</span></span>

* <span data-ttu-id="66926-190">使用世界鎖定的資料指標將您的注視視覺化。</span><span class="sxs-lookup"><span data-stu-id="66926-190">Visualize your gaze using a world-locked cursor.</span></span>

### <a name="instructions"></a><span data-ttu-id="66926-191">指示</span><span class="sxs-lookup"><span data-stu-id="66926-191">Instructions</span></span>

* <span data-ttu-id="66926-192">返回至您的 Unity 專案，如果仍然開啟 [組建設定] 視窗，請加以關閉。</span><span class="sxs-lookup"><span data-stu-id="66926-192">Go back to your Unity project, and close the Build Settings window if it's still open.</span></span>
* <span data-ttu-id="66926-193">在 [**專案] 面板** 中，選取 [全像 **] 資料夾。**</span><span class="sxs-lookup"><span data-stu-id="66926-193">Select the **Holograms** folder in the **Project panel**.</span></span>
* <span data-ttu-id="66926-194">將資料 **指標** 物件拖曳至根層級的階層 **面板** 中。</span><span class="sxs-lookup"><span data-stu-id="66926-194">Drag the **Cursor** object into the **Hierarchy panel** at the root level.</span></span>
* <span data-ttu-id="66926-195">按兩下資料 **指標** 物件，深入瞭解它。</span><span class="sxs-lookup"><span data-stu-id="66926-195">Double-click on the **Cursor** object to take a closer look at it.</span></span>
* <span data-ttu-id="66926-196">以滑鼠右鍵按一下 [專案] 面板中的 [ **腳本** ] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="66926-196">Right-click on the **Scripts** folder in the Project panel.</span></span>
* <span data-ttu-id="66926-197">按一下 [ **建立** ] 子功能表。</span><span class="sxs-lookup"><span data-stu-id="66926-197">Click the **Create** sub-menu.</span></span>
* <span data-ttu-id="66926-198">選取 **c # 腳本**。</span><span class="sxs-lookup"><span data-stu-id="66926-198">Select **C# Script**.</span></span>
* <span data-ttu-id="66926-199">將腳本命名為 **WorldCursor**。</span><span class="sxs-lookup"><span data-stu-id="66926-199">Name the script **WorldCursor**.</span></span> <span data-ttu-id="66926-200">注意：名稱會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="66926-200">Note: The name is case-sensitive.</span></span> <span data-ttu-id="66926-201">您不需要新增 .cs 副檔名。</span><span class="sxs-lookup"><span data-stu-id="66926-201">You do not need to add the .cs extension.</span></span>
* <span data-ttu-id="66926-202">在 [階層]**面板** 中選取資料 **指標** 物件。</span><span class="sxs-lookup"><span data-stu-id="66926-202">Select the **Cursor** object in the **Hierarchy panel**.</span></span>
* <span data-ttu-id="66926-203">將 **WorldCursor** 腳本拖放到 [ **檢查] 面板** 中。</span><span class="sxs-lookup"><span data-stu-id="66926-203">Drag and drop the **WorldCursor** script into the **Inspector panel**.</span></span>
* <span data-ttu-id="66926-204">按兩下 **WorldCursor** 腳本，在 Visual Studio 中開啟它。</span><span class="sxs-lookup"><span data-stu-id="66926-204">Double-click the **WorldCursor** script to open it in Visual Studio.</span></span>
* <span data-ttu-id="66926-205">將此程式碼複製並貼到 **WorldCursor.cs** 中，並 **全部儲存**。</span><span class="sxs-lookup"><span data-stu-id="66926-205">Copy and paste this code into **WorldCursor.cs** and **Save All**.</span></span>

```cs
using UnityEngine;

public class WorldCursor : MonoBehaviour
{
    private MeshRenderer meshRenderer;

    // Use this for initialization
    void Start()
    {
        // Grab the mesh renderer that's on the same object as this script.
        meshRenderer = this.gameObject.GetComponentInChildren<MeshRenderer>();
    }

    // Update is called once per frame
    void Update()
    {
        // Do a raycast into the world based on the user's
        // head position and orientation.
        var headPosition = Camera.main.transform.position;
        var gazeDirection = Camera.main.transform.forward;

        RaycastHit hitInfo;

        if (Physics.Raycast(headPosition, gazeDirection, out hitInfo))
        {
            // If the raycast hit a hologram...
            // Display the cursor mesh.
            meshRenderer.enabled = true;

            // Move thecursor to the point where the raycast hit.
            this.transform.position = hitInfo.point;

            // Rotate the cursor to hug the surface of the hologram.
            this.transform.rotation = Quaternion.FromToRotation(Vector3.up, hitInfo.normal);
        }
        else
        {
            // If the raycast did not hit a hologram, hide the cursor mesh.
            meshRenderer.enabled = false;
        }
    }
}
```

* <span data-ttu-id="66926-206">從檔案 **> 組建設定** 重建應用程式。</span><span class="sxs-lookup"><span data-stu-id="66926-206">Rebuild the app from **File > Build Settings**.</span></span>
* <span data-ttu-id="66926-207">返回先前用來部署至模擬器的 Visual Studio 方案。</span><span class="sxs-lookup"><span data-stu-id="66926-207">Return to the Visual Studio solution previously used to deploy to the emulator.</span></span>
* <span data-ttu-id="66926-208">出現提示時，請選取 [全部重載]。</span><span class="sxs-lookup"><span data-stu-id="66926-208">Select 'Reload All' when prompted.</span></span>
* <span data-ttu-id="66926-209">按一下 [ **Debug-> 啟動但不進行調試]，** 或按 **Ctrl + F5**。</span><span class="sxs-lookup"><span data-stu-id="66926-209">Click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
* <span data-ttu-id="66926-210">使用 Xbox 控制器來查看場景。</span><span class="sxs-lookup"><span data-stu-id="66926-210">Use the Xbox controller to look around the scene.</span></span> <span data-ttu-id="66926-211">請注意游標如何與物件的形狀互動。</span><span class="sxs-lookup"><span data-stu-id="66926-211">Notice how the cursor interacts with the shape of objects.</span></span>

## <a name="chapter-3---gestures"></a><span data-ttu-id="66926-212">第3章-手勢</span><span class="sxs-lookup"><span data-stu-id="66926-212">Chapter 3 - Gestures</span></span>

>[!VIDEO https://www.youtube.com/embed/6d-0RHeKHq4]

<span data-ttu-id="66926-213">在本章中，我們將新增 [手勢](../../../design/gaze-and-commit.md#composite-gestures)的支援。</span><span class="sxs-lookup"><span data-stu-id="66926-213">In this chapter, we'll add support for [gestures](../../../design/gaze-and-commit.md#composite-gestures).</span></span> <span data-ttu-id="66926-214">當使用者選取紙球體時，我們會使用 Unity 的物理引擎來開啟重力來使球體落在心。</span><span class="sxs-lookup"><span data-stu-id="66926-214">When the user selects a paper sphere, we'll make the sphere fall by turning on gravity using Unity's physics engine.</span></span>

### <a name="objectives"></a><span data-ttu-id="66926-215">目標</span><span class="sxs-lookup"><span data-stu-id="66926-215">Objectives</span></span>

* <span data-ttu-id="66926-216">使用選取手勢來控制您的全像影像。</span><span class="sxs-lookup"><span data-stu-id="66926-216">Control your holograms with the Select gesture.</span></span>

### <a name="instructions"></a><span data-ttu-id="66926-217">指示</span><span class="sxs-lookup"><span data-stu-id="66926-217">Instructions</span></span>

<span data-ttu-id="66926-218">我們將從建立腳本開始，而不會偵測到選取的手勢。</span><span class="sxs-lookup"><span data-stu-id="66926-218">We'll start by creating a script than can detect the Select gesture.</span></span>

* <span data-ttu-id="66926-219">在 [ **腳本** ] 資料夾中，建立名為 **GazeGestureManager** 的腳本。</span><span class="sxs-lookup"><span data-stu-id="66926-219">In the **Scripts** folder, create a script named **GazeGestureManager**.</span></span>
* <span data-ttu-id="66926-220">將 **GazeGestureManager** 腳本拖曳至階層中的 **OrigamiCollection** 物件。</span><span class="sxs-lookup"><span data-stu-id="66926-220">Drag the **GazeGestureManager** script onto the **OrigamiCollection** object in the Hierarchy.</span></span>
* <span data-ttu-id="66926-221">在 Visual Studio 中開啟 **GazeGestureManager** 腳本，並加入下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="66926-221">Open the **GazeGestureManager** script in Visual Studio and add the following code:</span></span>

```cs
using UnityEngine;
using UnityEngine.XR.WSA.Input;

public class GazeGestureManager : MonoBehaviour
{
    public static GazeGestureManager Instance { get; private set; }

    // Represents the hologram that is currently being gazed at.
    public GameObject FocusedObject { get; private set; }

    GestureRecognizer recognizer;

    // Use this for initialization
    void Start()
    {
        Instance = this;

        // Set up a GestureRecognizer to detect Select gestures.
        recognizer = new GestureRecognizer();
        recognizer.Tapped += (args) =>
        {
            // Send an OnSelect message to the focused object and its ancestors.
            if (FocusedObject != null)
            {
                FocusedObject.SendMessageUpwards("OnSelect", SendMessageOptions.DontRequireReceiver);
            }
        };
        recognizer.StartCapturingGestures();
    }

    // Update is called once per frame
    void Update()
    {
        // Figure out which hologram is focused this frame.
        GameObject oldFocusObject = FocusedObject;

        // Do a raycast into the world based on the user's
        // head position and orientation.
        var headPosition = Camera.main.transform.position;
        var gazeDirection = Camera.main.transform.forward;

        RaycastHit hitInfo;
        if (Physics.Raycast(headPosition, gazeDirection, out hitInfo))
        {
            // If the raycast hit a hologram, use that as the focused object.
            FocusedObject = hitInfo.collider.gameObject;
        }
        else
        {
            // If the raycast did not hit a hologram, clear the focused object.
            FocusedObject = null;
        }

        // If the focused object changed this frame,
        // start detecting fresh gestures again.
        if (FocusedObject != oldFocusObject)
        {
            recognizer.CancelGestures();
            recognizer.StartCapturingGestures();
        }
    }
}
```

* <span data-ttu-id="66926-222">在腳本資料夾中建立另一個腳本，這次名為 **SphereCommands**。</span><span class="sxs-lookup"><span data-stu-id="66926-222">Create another script in the Scripts folder, this time named **SphereCommands**.</span></span>
* <span data-ttu-id="66926-223">展開階層視圖中的 [ **OrigamiCollection** ] 物件。</span><span class="sxs-lookup"><span data-stu-id="66926-223">Expand the **OrigamiCollection** object in the Hierarchy view.</span></span>
* <span data-ttu-id="66926-224">將 **SphereCommands** 腳本拖曳至 [階層] 面板中的 **Sphere1** 物件。</span><span class="sxs-lookup"><span data-stu-id="66926-224">Drag the **SphereCommands** script onto the **Sphere1** object in the Hierarchy panel.</span></span>
* <span data-ttu-id="66926-225">將 **SphereCommands** 腳本拖曳至 [階層] 面板中的 **Sphere2** 物件。</span><span class="sxs-lookup"><span data-stu-id="66926-225">Drag the **SphereCommands** script onto the **Sphere2** object in the Hierarchy panel.</span></span>
* <span data-ttu-id="66926-226">在 Visual Studio 中開啟腳本進行編輯，並將預設程式碼取代為下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="66926-226">Open the script in Visual Studio for editing, and replace the default code with this:</span></span>

```cs
using UnityEngine;

public class SphereCommands : MonoBehaviour
{
    // Called by GazeGestureManager when the user performs a Select gesture
    void OnSelect()
    {
        // If the sphere has no Rigidbody component, add one to enable physics.
        if (!this.GetComponent<Rigidbody>())
        {
            var rigidbody = this.gameObject.AddComponent<Rigidbody>();
            rigidbody.collisionDetectionMode = CollisionDetectionMode.Continuous;
        }
    }
}
```

* <span data-ttu-id="66926-227">匯出、建立應用程式，並將其部署到 HoloLens 模擬器。</span><span class="sxs-lookup"><span data-stu-id="66926-227">Export, build and deploy the app to the HoloLens emulator.</span></span>
* <span data-ttu-id="66926-228">查看場景，並將其中一個球體置中。</span><span class="sxs-lookup"><span data-stu-id="66926-228">Look around the scene, and center on one of the spheres.</span></span>
* <span data-ttu-id="66926-229">按下 Xbox 控制器上 **的按鈕，** 或按空格鍵以模擬選取手勢。</span><span class="sxs-lookup"><span data-stu-id="66926-229">Press the **A** button on the Xbox controller or press the Spacebar to simulate the Select gesture.</span></span>

## <a name="chapter-4---voice"></a><span data-ttu-id="66926-230">第4章-語音</span><span class="sxs-lookup"><span data-stu-id="66926-230">Chapter 4 - Voice</span></span>

>[!VIDEO https://www.youtube.com/embed/LxbOhnd2_GM]

<span data-ttu-id="66926-231">在本章中，我們將新增兩個 [語音命令](../../../design/voice-input.md)的支援：「重設世界」以將捨棄的球體傳回其原始位置，以及「捨棄球體」以使球體落在外。</span><span class="sxs-lookup"><span data-stu-id="66926-231">In this chapter, we'll add support for two [voice commands](../../../design/voice-input.md): "Reset world" to returns the dropped spheres to their original location, and "Drop sphere" to make the sphere fall.</span></span>

### <a name="objectives"></a><span data-ttu-id="66926-232">目標</span><span class="sxs-lookup"><span data-stu-id="66926-232">Objectives</span></span>

* <span data-ttu-id="66926-233">新增一律在背景中接聽的語音命令。</span><span class="sxs-lookup"><span data-stu-id="66926-233">Add voice commands that always listen in the background.</span></span>
* <span data-ttu-id="66926-234">建立可回應語音命令的全像影像。</span><span class="sxs-lookup"><span data-stu-id="66926-234">Create a hologram that reacts to a voice command.</span></span>

### <a name="instructions"></a><span data-ttu-id="66926-235">指示</span><span class="sxs-lookup"><span data-stu-id="66926-235">Instructions</span></span>

* <span data-ttu-id="66926-236">在 [ **腳本** ] 資料夾中，建立名為 **SpeechManager** 的腳本。</span><span class="sxs-lookup"><span data-stu-id="66926-236">In the **Scripts** folder, create a script named **SpeechManager**.</span></span>
* <span data-ttu-id="66926-237">將 **SpeechManager** 腳本拖曳至階層中的 **OrigamiCollection** 物件</span><span class="sxs-lookup"><span data-stu-id="66926-237">Drag the **SpeechManager** script onto the **OrigamiCollection** object in the Hierarchy</span></span>
* <span data-ttu-id="66926-238">在 Visual Studio 中開啟 **SpeechManager** 腳本。</span><span class="sxs-lookup"><span data-stu-id="66926-238">Open the **SpeechManager** script in Visual Studio.</span></span>
* <span data-ttu-id="66926-239">將此程式碼複製並貼到 **SpeechManager.cs** 中，並 **全部儲存**：</span><span class="sxs-lookup"><span data-stu-id="66926-239">Copy and paste this code into **SpeechManager.cs** and **Save All**:</span></span>

```cs
using System.Collections.Generic;
using System.Linq;
using UnityEngine;
using UnityEngine.Windows.Speech;

public class SpeechManager : MonoBehaviour
{
    KeywordRecognizer keywordRecognizer = null;
    Dictionary<string, System.Action> keywords = new Dictionary<string, System.Action>();

    // Use this for initialization
    void Start()
    {
        keywords.Add("Reset world", () =>
        {
            // Call the OnReset method on every descendant object.
            this.BroadcastMessage("OnReset");
        });

        keywords.Add("Drop Sphere", () =>
        {
            var focusObject = GazeGestureManager.Instance.FocusedObject;
            if (focusObject != null)
            {
                // Call the OnDrop method on just the focused object.
                focusObject.SendMessage("OnDrop", SendMessageOptions.DontRequireReceiver);
            }
        });

        // Tell the KeywordRecognizer about our keywords.
        keywordRecognizer = new KeywordRecognizer(keywords.Keys.ToArray());

        // Register a callback for the KeywordRecognizer and start recognizing!
        keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
        keywordRecognizer.Start();
    }

    private void KeywordRecognizer_OnPhraseRecognized(PhraseRecognizedEventArgs args)
    {
        System.Action keywordAction;
        if (keywords.TryGetValue(args.text, out keywordAction))
        {
            keywordAction.Invoke();
        }
    }
}
```

* <span data-ttu-id="66926-240">在 Visual Studio 中開啟 **SphereCommands** 腳本。</span><span class="sxs-lookup"><span data-stu-id="66926-240">Open the **SphereCommands** script in Visual Studio.</span></span>
* <span data-ttu-id="66926-241">更新腳本以進行讀取，如下所示：</span><span class="sxs-lookup"><span data-stu-id="66926-241">Update the script to read as follows:</span></span>

```cs
using UnityEngine;

public class SphereCommands : MonoBehaviour
{
    Vector3 originalPosition;

    // Use this for initialization
    void Start()
    {
        // Grab the original local position of the sphere when the app starts.
        originalPosition = this.transform.localPosition;
    }

    // Called by GazeGestureManager when the user performs a Select gesture
    void OnSelect()
    {
        // If the sphere has no Rigidbody component, add one to enable physics.
        if (!this.GetComponent<Rigidbody>())
        {
            var rigidbody = this.gameObject.AddComponent<Rigidbody>();
            rigidbody.collisionDetectionMode = CollisionDetectionMode.Continuous;
        }
    }

    // Called by SpeechManager when the user says the "Reset world" command
    void OnReset()
    {
        // If the sphere has a Rigidbody component, remove it to disable physics.
        var rigidbody = this.GetComponent<Rigidbody>();
        if (rigidbody != null)
        {
            rigidbody.isKinematic = true;
            Destroy(rigidbody);
        }

        // Put the sphere back into its original local position.
        this.transform.localPosition = originalPosition;
    }

    // Called by SpeechManager when the user says the "Drop sphere" command
    void OnDrop()
    {
        // Just do the same logic as a Select gesture.
        OnSelect();
    }
}
```

* <span data-ttu-id="66926-242">匯出、建立應用程式，並將其部署到 HoloLens 模擬器。</span><span class="sxs-lookup"><span data-stu-id="66926-242">Export, build and deploy the app to the HoloLens emulator.</span></span>
* <span data-ttu-id="66926-243">模擬器將支援您電腦的麥克風，並回應您的聲音：調整視圖，讓游標位於其中一個球體上，然後說出「捨棄球體」。</span><span class="sxs-lookup"><span data-stu-id="66926-243">The emulator will support your PC's microphone and respond to your voice: adjust the view so the cursor is on one of the spheres, and say "Drop Sphere".</span></span>
* <span data-ttu-id="66926-244">說「**重設世界**」將它們帶回其初始位置。</span><span class="sxs-lookup"><span data-stu-id="66926-244">Say "**Reset World**" to bring them back to their initial positions.</span></span>

## <a name="chapter-5---spatial-sound"></a><span data-ttu-id="66926-245">第5章-空間音效</span><span class="sxs-lookup"><span data-stu-id="66926-245">Chapter 5 - Spatial sound</span></span>

>[!VIDEO https://www.youtube.com/embed/Xc3C4VA10w4]

<span data-ttu-id="66926-246">在本章中，我們會將音樂新增至應用程式，然後觸發對某些動作的音效效果。</span><span class="sxs-lookup"><span data-stu-id="66926-246">In this chapter, we'll add music to the app, and then trigger sound effects on certain actions.</span></span> <span data-ttu-id="66926-247">我們會使用 [空間音效](../../../design/spatial-sound.md) ，在3d 空間中提供音效的特定位置。</span><span class="sxs-lookup"><span data-stu-id="66926-247">We'll be using [spatial sound](../../../design/spatial-sound.md) to give sounds a specific location in 3D space.</span></span>

### <a name="objectives"></a><span data-ttu-id="66926-248">目標</span><span class="sxs-lookup"><span data-stu-id="66926-248">Objectives</span></span>

* <span data-ttu-id="66926-249">聽聽您的全球全像投影。</span><span class="sxs-lookup"><span data-stu-id="66926-249">Hear holograms in your world.</span></span>

### <a name="instructions"></a><span data-ttu-id="66926-250">指示</span><span class="sxs-lookup"><span data-stu-id="66926-250">Instructions</span></span>

* <span data-ttu-id="66926-251">在 Unity 中，選取上方功能表的 [ **編輯] > 專案設定 > 音訊**</span><span class="sxs-lookup"><span data-stu-id="66926-251">In the Unity select from the top menu **Edit > Project Settings > Audio**</span></span>
* <span data-ttu-id="66926-252">尋找 **空間定位器外掛程式** 設定，然後選取 **MS HRTF 空間定位器**。</span><span class="sxs-lookup"><span data-stu-id="66926-252">Find the **Spatializer Plugin** setting and select **MS HRTF Spatializer**.</span></span>
* <span data-ttu-id="66926-253">從 [全像 **] 資料夾，將 [** **環境** ] 物件拖曳至 [階層] 面板中的 **OrigamiCollection** 物件。</span><span class="sxs-lookup"><span data-stu-id="66926-253">From the **Holograms** folder, drag the **Ambience** object onto the **OrigamiCollection** object in the Hierarchy Panel.</span></span>
* <span data-ttu-id="66926-254">選取 [ **OrigamiCollection** ]，然後尋找 **音訊來源** 元件。</span><span class="sxs-lookup"><span data-stu-id="66926-254">Select **OrigamiCollection** and find the **Audio Source** component.</span></span> <span data-ttu-id="66926-255">變更這些屬性：</span><span class="sxs-lookup"><span data-stu-id="66926-255">Change these properties:</span></span>
  * <span data-ttu-id="66926-256">檢查 **Spatialize** 屬性。</span><span class="sxs-lookup"><span data-stu-id="66926-256">Check the **Spatialize** property.</span></span>
  * <span data-ttu-id="66926-257">檢查是否 **在喚醒時播放**。</span><span class="sxs-lookup"><span data-stu-id="66926-257">Check the **Play On Awake**.</span></span>
  * <span data-ttu-id="66926-258">將滑杆向右拖曳，以將 **空間 Blend** 變更為 **3d** 。</span><span class="sxs-lookup"><span data-stu-id="66926-258">Change **Spatial Blend** to **3D** by dragging the slider all the way to the right.</span></span>
  * <span data-ttu-id="66926-259">檢查 **迴圈** 屬性。</span><span class="sxs-lookup"><span data-stu-id="66926-259">Check the **Loop** property.</span></span>
  * <span data-ttu-id="66926-260">展開 [ **3D 音效設定**]，然後輸入 **0.1** 作為 **Doppler 等級**。</span><span class="sxs-lookup"><span data-stu-id="66926-260">Expand **3D Sound Settings**, and enter **0.1** for **Doppler Level**.</span></span>
  * <span data-ttu-id="66926-261">將 **Volume Rolloff** 設為 **對數 Rolloff**。</span><span class="sxs-lookup"><span data-stu-id="66926-261">Set **Volume Rolloff** to **Logarithmic Rolloff**.</span></span>
  * <span data-ttu-id="66926-262">將 **最大距離** 設定為 **20**。</span><span class="sxs-lookup"><span data-stu-id="66926-262">Set **Max Distance** to **20**.</span></span>
* <span data-ttu-id="66926-263">在 [ **腳本** ] 資料夾中，建立名為 **SphereSounds** 的腳本。</span><span class="sxs-lookup"><span data-stu-id="66926-263">In the **Scripts** folder, create a script named **SphereSounds**.</span></span>
* <span data-ttu-id="66926-264">將 **SphereSounds** 拖曳到階層中的 **Sphere1** 和 **Sphere2** 物件。</span><span class="sxs-lookup"><span data-stu-id="66926-264">Drag **SphereSounds** to the **Sphere1** and **Sphere2** objects in the Hierarchy.</span></span>
* <span data-ttu-id="66926-265">在 Visual Studio 中開啟 **SphereSounds** ，更新下列程式碼並 **全部儲存**。</span><span class="sxs-lookup"><span data-stu-id="66926-265">Open **SphereSounds** in Visual Studio, update the following code and **Save All**.</span></span>

```cs
using UnityEngine;

public class SphereSounds : MonoBehaviour
{
    AudioSource impactAudioSource = null;
    AudioSource rollingAudioSource = null;

    bool rolling = false;

    void Start()
    {
        // Add an AudioSource component and set up some defaults
        impactAudioSource = gameObject.AddComponent<AudioSource>();
        impactAudioSource.playOnAwake = false;
        impactAudioSource.spatialize = true;
        impactAudioSource.spatialBlend = 1.0f;
        impactAudioSource.dopplerLevel = 0.0f;
        impactAudioSource.rolloffMode = AudioRolloffMode.Logarithmic;
        impactAudioSource.maxDistance = 20f;

        rollingAudioSource = gameObject.AddComponent<AudioSource>();
        rollingAudioSource.playOnAwake = false;
        rollingAudioSource.spatialize = true;
        rollingAudioSource.spatialBlend = 1.0f;
        rollingAudioSource.dopplerLevel = 0.0f;
        rollingAudioSource.rolloffMode = AudioRolloffMode.Logarithmic;
        rollingAudioSource.maxDistance = 20f;
        rollingAudioSource.loop = true;

        // Load the Sphere sounds from the Resources folder
        impactAudioSource.clip = Resources.Load<AudioClip>("Impact");
        rollingAudioSource.clip = Resources.Load<AudioClip>("Rolling");
    }

    // Occurs when this object starts colliding with another object
    void OnCollisionEnter(Collision collision)
    {
        // Play an impact sound if the sphere impacts strongly enough.
        if (collision.relativeVelocity.magnitude >= 0.1f)
        {
            impactAudioSource.Play();
        }
    }

    // Occurs each frame that this object continues to collide with another object
    void OnCollisionStay(Collision collision)
    {
        Rigidbody rigid = gameObject.GetComponent<Rigidbody>();

        // Play a rolling sound if the sphere is rolling fast enough.
        if (!rolling && rigid.velocity.magnitude >= 0.01f)
        {
            rolling = true;
            rollingAudioSource.Play();
        }
        // Stop the rolling sound if rolling slows down.
        else if (rolling && rigid.velocity.magnitude < 0.01f)
        {
            rolling = false;
            rollingAudioSource.Stop();
        }
    }

    // Occurs when this object stops colliding with another object
    void OnCollisionExit(Collision collision)
    {
        // Stop the rolling sound if the object falls off and stops colliding.
        if (rolling)
        {
            rolling = false;
            impactAudioSource.Stop();
            rollingAudioSource.Stop();
        }
    }
}
```

* <span data-ttu-id="66926-266">儲存腳本，並回到 Unity。</span><span class="sxs-lookup"><span data-stu-id="66926-266">Save the script, and return to Unity.</span></span>
* <span data-ttu-id="66926-267">匯出、建立應用程式，並將其部署到 HoloLens 模擬器。</span><span class="sxs-lookup"><span data-stu-id="66926-267">Export, build and deploy the app to the HoloLens emulator.</span></span>
* <span data-ttu-id="66926-268">戴耳機以取得完整效果，並從階段更接近且更深入地聆聽音效變更。</span><span class="sxs-lookup"><span data-stu-id="66926-268">Wear headphones to get the full effect, and move closer and further from the Stage to hear the sounds change.</span></span>

## <a name="chapter-6---spatial-mapping"></a><span data-ttu-id="66926-269">第6章-空間對應</span><span class="sxs-lookup"><span data-stu-id="66926-269">Chapter 6 - Spatial mapping</span></span>

>[!VIDEO https://www.youtube.com/embed/S-517Y63Cnk]

<span data-ttu-id="66926-270">現在我們要使用 [空間對應](../../../design/spatial-mapping.md) ，將遊戲台放在真實世界中的真實物件上。</span><span class="sxs-lookup"><span data-stu-id="66926-270">Now we are going to use [spatial mapping](../../../design/spatial-mapping.md) to place the game board on a real object in the real world.</span></span>

### <a name="objectives"></a><span data-ttu-id="66926-271">目標</span><span class="sxs-lookup"><span data-stu-id="66926-271">Objectives</span></span>

* <span data-ttu-id="66926-272">將您的真實世界帶入虛擬世界。</span><span class="sxs-lookup"><span data-stu-id="66926-272">Bring your real world into the virtual world.</span></span>
* <span data-ttu-id="66926-273">將您的全像放在最重要的地方。</span><span class="sxs-lookup"><span data-stu-id="66926-273">Place your holograms where they matter most to you.</span></span>

### <a name="instructions"></a><span data-ttu-id="66926-274">指示</span><span class="sxs-lookup"><span data-stu-id="66926-274">Instructions</span></span>

* <span data-ttu-id="66926-275">在 [專案] 面板中，按一下 [全像全像 **] 資料夾。**</span><span class="sxs-lookup"><span data-stu-id="66926-275">Click on the **Holograms** folder in the Project panel.</span></span>
* <span data-ttu-id="66926-276">將 **空間對應** 資產拖曳至 **階層的根目錄。**</span><span class="sxs-lookup"><span data-stu-id="66926-276">Drag the **Spatial Mapping** asset into the root of the **Hierarchy**.</span></span>
* <span data-ttu-id="66926-277">按一下階層中的 **空間對應** 物件。</span><span class="sxs-lookup"><span data-stu-id="66926-277">Click on the **Spatial Mapping** object in the Hierarchy.</span></span>
* <span data-ttu-id="66926-278">在 [偵測 **器] 面板** 中，變更下列屬性：</span><span class="sxs-lookup"><span data-stu-id="66926-278">In the **Inspector panel**, change the following properties:</span></span>
  * <span data-ttu-id="66926-279">選取 [ **繪製視覺網格** ] 方塊。</span><span class="sxs-lookup"><span data-stu-id="66926-279">Check the **Draw Visual Meshes** box.</span></span>
  * <span data-ttu-id="66926-280">找出 **繪製材質** ，然後按一下右側的圓形。</span><span class="sxs-lookup"><span data-stu-id="66926-280">Locate **Draw Material** and click the circle on the right.</span></span> <span data-ttu-id="66926-281">在頂端的搜尋欄位中輸入「**線框**」。</span><span class="sxs-lookup"><span data-stu-id="66926-281">Type "**wireframe**" into the search field at the top.</span></span> <span data-ttu-id="66926-282">按一下結果，然後關閉視窗。</span><span class="sxs-lookup"><span data-stu-id="66926-282">Click on the result and then close the window.</span></span>
* <span data-ttu-id="66926-283">匯出、建立應用程式，並將其部署到 HoloLens 模擬器。</span><span class="sxs-lookup"><span data-stu-id="66926-283">Export, build and deploy the app to the HoloLens emulator.</span></span>
* <span data-ttu-id="66926-284">當應用程式執行時，系統會以線框呈現先前掃描的真實世界空間網格。</span><span class="sxs-lookup"><span data-stu-id="66926-284">When the app runs, a mesh of a previously scanned real-world living room will be rendered in wireframe.</span></span>
* <span data-ttu-id="66926-285">觀賞輪流球體將如何落在此階段，並進入地面上！</span><span class="sxs-lookup"><span data-stu-id="66926-285">Watch how a rolling sphere will fall off the stage, and onto the floor!</span></span>

<span data-ttu-id="66926-286">現在，我們將示範如何將 OrigamiCollection 移至新位置：</span><span class="sxs-lookup"><span data-stu-id="66926-286">Now we'll show you how to move the OrigamiCollection to a new location:</span></span>

* <span data-ttu-id="66926-287">在 [ **腳本** ] 資料夾中，建立名為 **TapToPlaceParent** 的腳本。</span><span class="sxs-lookup"><span data-stu-id="66926-287">In the **Scripts** folder, create a script named **TapToPlaceParent**.</span></span>
* <span data-ttu-id="66926-288">在階層 **中，展開**[ **OrigamiCollection** ]，然後選取 [ **階段** ] 物件。</span><span class="sxs-lookup"><span data-stu-id="66926-288">In the **Hierarchy**, expand the **OrigamiCollection** and select the **Stage** object.</span></span>
* <span data-ttu-id="66926-289">將 **TapToPlaceParent** 腳本拖曳至階段物件。</span><span class="sxs-lookup"><span data-stu-id="66926-289">Drag the **TapToPlaceParent** script onto the Stage object.</span></span>
* <span data-ttu-id="66926-290">在 Visual Studio 中開啟 **TapToPlaceParent** 腳本，並將其更新為下列內容：</span><span class="sxs-lookup"><span data-stu-id="66926-290">Open the **TapToPlaceParent** script in Visual Studio, and update it to be the following:</span></span>

```cs
using UnityEngine;

public class TapToPlaceParent : MonoBehaviour
{
    bool placing = false;

    // Called by GazeGestureManager when the user performs a Select gesture
    void OnSelect()
    {
        // On each Select gesture, toggle whether the user is in placing mode.
        placing = !placing;

        // If the user is in placing mode, display the spatial mapping mesh.
        if (placing)
        {
            SpatialMapping.Instance.DrawVisualMeshes = true;
        }
        // If the user is not in placing mode, hide the spatial mapping mesh.
        else
        {
            SpatialMapping.Instance.DrawVisualMeshes = false;
        }
    }

    // Update is called once per frame
    void Update()
    {
        // If the user is in placing mode,
        // update the placement to match the user's gaze.

        if (placing)
        {
            // Do a raycast into the world that will only hit the Spatial Mapping mesh.
            var headPosition = Camera.main.transform.position;
            var gazeDirection = Camera.main.transform.forward;

            RaycastHit hitInfo;
            if (Physics.Raycast(headPosition, gazeDirection, out hitInfo,
                30.0f, SpatialMapping.PhysicsRaycastMask))
            {
                // Move this object's parent object to
                // where the raycast hit the Spatial Mapping mesh.
                this.transform.parent.position = hitInfo.point;

                // Rotate this object's parent object to face the user.
                Quaternion toQuat = Camera.main.transform.localRotation;
                toQuat.x = 0;
                toQuat.z = 0;
                this.transform.parent.rotation = toQuat;
            }
        }
    }
}
```

* <span data-ttu-id="66926-291">匯出、建立及部署應用程式。</span><span class="sxs-lookup"><span data-stu-id="66926-291">Export, build and deploy the app.</span></span>
* <span data-ttu-id="66926-292">現在，您應該可以使用 Select 手勢 (**a** 或空格鍵) ，然後移至新位置，然後再使用 [選取手勢]，將遊戲放在特定位置。</span><span class="sxs-lookup"><span data-stu-id="66926-292">Now you should now be able to place the game in a specific location by gazing at it, using the Select gesture (**A** or Spacebar) and then moving to a new location, and using the Select gesture again.</span></span>

## <a name="the-end"></a><span data-ttu-id="66926-293">結束</span><span class="sxs-lookup"><span data-stu-id="66926-293">The end</span></span>

<span data-ttu-id="66926-294">這就是本教學課程的結尾！</span><span class="sxs-lookup"><span data-stu-id="66926-294">And that's the end of this tutorial!</span></span>

<span data-ttu-id="66926-295">您已了解︰</span><span class="sxs-lookup"><span data-stu-id="66926-295">You learned:</span></span>

* <span data-ttu-id="66926-296">如何在 Unity 中建立全像內建應用程式。</span><span class="sxs-lookup"><span data-stu-id="66926-296">How to create a holographic app in Unity.</span></span>
* <span data-ttu-id="66926-297">如何利用注視、手勢、聲音、音效和空間對應。</span><span class="sxs-lookup"><span data-stu-id="66926-297">How to make use of gaze, gesture, voice, sounds, and spatial mapping.</span></span>
* <span data-ttu-id="66926-298">如何使用 Visual Studio 來建立和部署應用程式。</span><span class="sxs-lookup"><span data-stu-id="66926-298">How to build and deploy an app using Visual Studio.</span></span>

<span data-ttu-id="66926-299">您現在已準備好開始建立自己的全像攝影應用程式！</span><span class="sxs-lookup"><span data-stu-id="66926-299">You are now ready to start creating your own holographic apps!</span></span>

## <a name="see-also"></a><span data-ttu-id="66926-300">另請參閱</span><span class="sxs-lookup"><span data-stu-id="66926-300">See also</span></span>

* [<span data-ttu-id="66926-301">MR Basics 101：使用裝置完成專案</span><span class="sxs-lookup"><span data-stu-id="66926-301">MR Basics 101: Complete project with device</span></span>](holograms-101.md)
* [<span data-ttu-id="66926-302">目光</span><span class="sxs-lookup"><span data-stu-id="66926-302">Gaze</span></span>](../../../design/gaze-and-commit.md)
* [<span data-ttu-id="66926-303">頭部目光和行動</span><span class="sxs-lookup"><span data-stu-id="66926-303">Head-gaze and commit</span></span>](../../../design/gaze-and-commit.md)
* [<span data-ttu-id="66926-304">語音輸入</span><span class="sxs-lookup"><span data-stu-id="66926-304">Voice input</span></span>](../../../design/voice-input.md)
* [<span data-ttu-id="66926-305">空間音效</span><span class="sxs-lookup"><span data-stu-id="66926-305">Spatial sound</span></span>](../../../design/spatial-sound.md)
* [<span data-ttu-id="66926-306">空間對應</span><span class="sxs-lookup"><span data-stu-id="66926-306">Spatial mapping</span></span>](../../../design/spatial-mapping.md)