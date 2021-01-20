---
title: MR Basics 101 - 使用裝置完成專案
description: 遵循此程式碼逐步解說，使用 Unity、Visual Studio 和 HoloLens 來瞭解 Windows Mixed Reality 的基本概念。
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: mixed reality、Windows Mixed Reality、HoloLens、全息圖、學術、教學課程、HoloLens、混合的現實學術、unity、混合現實耳機、Windows Mixed reality 耳機、虛擬實境耳機、Windows 10
ms.openlocfilehash: 4ca16542060e1cee746ba5095a7bf68ca8136267
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583714"
---
# <a name="mr-basics-101-complete-project-with-device"></a><span data-ttu-id="0cdd8-104">MR Basics 101：使用裝置完成專案</span><span class="sxs-lookup"><span data-stu-id="0cdd8-104">MR Basics 101: Complete project with device</span></span>

<br>

>[!NOTE]
><span data-ttu-id="0cdd8-105">混合實境學院教學課程的設計是以 HoloLens (第 1 代) 和混合實境沉浸式頭戴裝置為準。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-105">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="0cdd8-106">因此，對於仍在尋找這些裝置開發指引的開發人員而言，我們覺得這些教學課程很重要。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-106">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="0cdd8-107">這些教學課程 **_不會_** 使用用於 HoloLens 2 的最新工具組或互動進行更新。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-107">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="0cdd8-108">系統會保留這些資訊，以繼續在支援的裝置上運作。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-108">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="0cdd8-109">已針對 HoloLens 2 公佈[一系列新的教學課程](mrlearning-base.md)。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-109">[A new series of tutorials](mrlearning-base.md) has been posted for HoloLens 2.</span></span>

<br>

>[!VIDEO https://www.youtube.com/embed/XKIIEC5BMWg]

<span data-ttu-id="0cdd8-110">本教學課程將逐步引導您完成內建 Unity 的完整專案，以示範 HoloLens 上的核心 Windows Mixed Reality 功能，包括 [注視](../../../design/gaze-and-commit.md)、 [手勢](../../../design/gaze-and-commit.md#composite-gestures)、 [語音輸入](../../../design/voice-input.md)、 [空間音效](../../../design/spatial-sound.md) 和 [空間對應](../../../design/spatial-mapping.md)。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-110">This tutorial will walk you through a complete project, built in Unity, that demonstrates core Windows Mixed Reality features on HoloLens including [gaze](../../../design/gaze-and-commit.md), [gestures](../../../design/gaze-and-commit.md#composite-gestures), [voice input](../../../design/voice-input.md), [spatial sound](../../../design/spatial-sound.md) and [spatial mapping](../../../design/spatial-mapping.md).</span></span>

<span data-ttu-id="0cdd8-111">本教學課程需要大約1小時才能完成。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-111">The tutorial will take approximately 1 hour to complete.</span></span>

## <a name="device-support"></a><span data-ttu-id="0cdd8-112">裝置支援</span><span class="sxs-lookup"><span data-stu-id="0cdd8-112">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="0cdd8-113">課程</span><span class="sxs-lookup"><span data-stu-id="0cdd8-113">Course</span></span></th><th style="width:150px"> <span data-ttu-id="0cdd8-114"><a href="/hololens/hololens1-hardware">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="0cdd8-114"><a href="/hololens/hololens1-hardware">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="0cdd8-115"><a href="../../../discover/immersive-headset-hardware-details.md">沉浸式頭戴裝置</a></span><span class="sxs-lookup"><span data-stu-id="0cdd8-115"><a href="../../../discover/immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="0cdd8-116">MR Basics 101：使用裝置完成專案</span><span class="sxs-lookup"><span data-stu-id="0cdd8-116">MR Basics 101: Complete project with device</span></span></td><td style="text-align: center;"> <span data-ttu-id="0cdd8-117">✔️</span><span class="sxs-lookup"><span data-stu-id="0cdd8-117">✔️</span></span></td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="0cdd8-118">在您開始使用 Intune 之前</span><span class="sxs-lookup"><span data-stu-id="0cdd8-118">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="0cdd8-119">必要條件</span><span class="sxs-lookup"><span data-stu-id="0cdd8-119">Prerequisites</span></span>

* <span data-ttu-id="0cdd8-120">[已安裝正確工具](../../install-the-tools.md)的 Windows 10 電腦。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-120">A Windows 10 PC configured with the correct [tools installed](../../install-the-tools.md).</span></span>
* <span data-ttu-id="0cdd8-121">[針對開發設定](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)的 HoloLens 裝置。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-121">A HoloLens device [configured for development](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="0cdd8-122">專案檔</span><span class="sxs-lookup"><span data-stu-id="0cdd8-122">Project files</span></span>

* <span data-ttu-id="0cdd8-123">下載專案 [所需的](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-101.zip) 檔案。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-123">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-101.zip) required by the project.</span></span> <span data-ttu-id="0cdd8-124">需要 Unity 2017.2 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-124">Requires Unity 2017.2 or later.</span></span>
  * <span data-ttu-id="0cdd8-125">如果您仍然需要 Unity 5.6 支援，請使用 [此版本](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-101.zip)。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-125">If you still need Unity 5.6 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-101.zip).</span></span>
  * <span data-ttu-id="0cdd8-126">如果您仍然需要 Unity 5.5 支援，請使用 [此版本](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-101.zip)。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-126">If you still need Unity 5.5 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-101.zip).</span></span>
  * <span data-ttu-id="0cdd8-127">如果您仍然需要 Unity 5.4 支援，請使用 [此版本](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-101.zip)。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-127">If you still need Unity 5.4 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-101.zip).</span></span>
* <span data-ttu-id="0cdd8-128">取消將檔案封存到您的桌面或其他易於觸及的位置。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-128">Un-archive the files to your desktop or other easy to reach location.</span></span> <span data-ttu-id="0cdd8-129">將資料夾名稱保留為 **日式**。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-129">Keep the folder name as **Origami**.</span></span>

>[!NOTE]
><span data-ttu-id="0cdd8-130">如果您想要在下載之前查看原始程式碼， [可在 GitHub 上](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-101)取得。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-130">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-101).</span></span>

## <a name="chapter-1---holo-world"></a><span data-ttu-id="0cdd8-131">第1章-「Hololens」世界</span><span class="sxs-lookup"><span data-stu-id="0cdd8-131">Chapter 1 - "Holo" world</span></span>

>[!VIDEO https://www.youtube.com/embed/PmtZGjYFroY]

<span data-ttu-id="0cdd8-132">在本章中，我們將設定第一個 Unity 專案，並逐步執行組建和部署程式。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-132">In this chapter, we'll setup our first Unity project and step through the build and deploy process.</span></span>

### <a name="objectives"></a><span data-ttu-id="0cdd8-133">目標</span><span class="sxs-lookup"><span data-stu-id="0cdd8-133">Objectives</span></span>

* <span data-ttu-id="0cdd8-134">設定 Unity 進行全像開發。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-134">Set up Unity for holographic development.</span></span>
* <span data-ttu-id="0cdd8-135">製作全像影像。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-135">Make a hologram.</span></span>
* <span data-ttu-id="0cdd8-136">查看您製作的全像影像。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-136">See a hologram that you made.</span></span>

### <a name="instructions"></a><span data-ttu-id="0cdd8-137">指示</span><span class="sxs-lookup"><span data-stu-id="0cdd8-137">Instructions</span></span>

* <span data-ttu-id="0cdd8-138">啟動 Unity。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-138">Start Unity.</span></span>
* <span data-ttu-id="0cdd8-139">選取 [開啟]  。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-139">Select **Open**.</span></span>
* <span data-ttu-id="0cdd8-140">輸入 [位置] 作為您先前取消封存的 [ **折紙** ] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-140">Enter location as the **Origami** folder you previously un-archived.</span></span>
* <span data-ttu-id="0cdd8-141">選取 [ **折紙** ]，然後按一下 [ **選取資料夾**]。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-141">Select **Origami** and click **Select Folder**.</span></span>
* <span data-ttu-id="0cdd8-142">由於 **日式** 投影專案不包含場景，請使用： **file**  /  **save 場景 As**，將空的預設場景儲存至新檔案。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-142">Since the **Origami** project does not contain a scene, save the empty default scene to a new file using: **File** / **Save Scene As**.</span></span>
* <span data-ttu-id="0cdd8-143">將新的場景命名為 **日式** ，然後按下 [ **儲存** ] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-143">Name the new scene **Origami** and press the **Save** button.</span></span>

#### <a name="setup-the-main-virtual-camera"></a><span data-ttu-id="0cdd8-144">設定主要虛擬攝影機</span><span class="sxs-lookup"><span data-stu-id="0cdd8-144">Setup the main virtual camera</span></span>

* <span data-ttu-id="0cdd8-145">在 [階層面板] 中，選取 [主要相機]。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-145">In the **Hierarchy Panel**, select **Main Camera**.</span></span>
* <span data-ttu-id="0cdd8-146">在偵測 **器** 中，將其轉換位置設定為 **0、0、0**。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-146">In the **Inspector** set its transform position to **0,0,0**.</span></span>
* <span data-ttu-id="0cdd8-147">尋找 [ **清除旗標** ] 屬性，並將下拉式清單從 [ **Skybox** ] 變更為 [ **純色**]。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-147">Find the **Clear Flags** property, and change the dropdown from **Skybox** to **Solid color**.</span></span>
* <span data-ttu-id="0cdd8-148">按一下 [背景] 欄位，以開啟色彩選擇器。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-148">Click on the **Background** field to open a color picker.</span></span>
* <span data-ttu-id="0cdd8-149">將 **R、G、B 和 A** 設為 **0**。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-149">Set **R, G, B, and A** to **0**.</span></span>

#### <a name="setup-the-scene"></a><span data-ttu-id="0cdd8-150">設定場景</span><span class="sxs-lookup"><span data-stu-id="0cdd8-150">Setup the scene</span></span>

* <span data-ttu-id="0cdd8-151">在 [階層] **面板** 中，按一下 [ **建立** ] 並 **建立空白**。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-151">In the **Hierarchy Panel**, click on **Create** and **Create Empty**.</span></span>
* <span data-ttu-id="0cdd8-152">以滑鼠右鍵按一下新的 **GameObject** ，然後選取 [重新命名]。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-152">Right-click the new **GameObject** and select Rename.</span></span> <span data-ttu-id="0cdd8-153">將 GameObject 重新命名為 **OrigamiCollection**。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-153">Rename the GameObject to **OrigamiCollection**.</span></span>
* <span data-ttu-id="0cdd8-154">從 [專案] 面板中 **的 [全** 像] 資料夾 (展開 [資產]，然後選取 [全選]，然後在 [專案]) 面板中，按兩下 [全像</span><span class="sxs-lookup"><span data-stu-id="0cdd8-154">From the **Holograms** folder in the Project Panel (expand Assets and select Holograms or double click the Holograms folder in the Project Panel):</span></span>
  * <span data-ttu-id="0cdd8-155">將 [ **階段** ] 拖曳到階層中，成為 **OrigamiCollection** 的子系。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-155">Drag **Stage** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
  * <span data-ttu-id="0cdd8-156">將 **Sphere1** 拖曳到階層中，以成為 **OrigamiCollection** 的子系。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-156">Drag **Sphere1** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
  * <span data-ttu-id="0cdd8-157">將 **Sphere2** 拖曳到階層中，以成為 **OrigamiCollection** 的子系。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-157">Drag **Sphere2** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
* <span data-ttu-id="0cdd8-158">以滑鼠右鍵按一下 [階層]**面板** 中的 **方向光源** 物件，然後選取 [**刪除**]。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-158">Right-click the **Directional Light** object in the **Hierarchy Panel** and select **Delete**.</span></span>
* <span data-ttu-id="0cdd8-159">從 [全像 **] 資料夾，將\*\*\*\*燈光** 拖曳到階層 **面板** 的根目錄中。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-159">From the **Holograms** folder, drag **Lights** into the root of the **Hierarchy Panel**.</span></span>
* <span data-ttu-id="0cdd8-160">**在階層中，選取** **OrigamiCollection**。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-160">In the **Hierarchy**, select the **OrigamiCollection**.</span></span>
* <span data-ttu-id="0cdd8-161">在偵測 **器** 中，將轉換位置設定為 **0、-0.5、2.0**。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-161">In the **Inspector**, set the transform position to **0, -0.5, 2.0**.</span></span>
* <span data-ttu-id="0cdd8-162">按下 Unity 中的 [ **播放** ] 按鈕，以預覽您的全像影像。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-162">Press the **Play** button in Unity to preview your holograms.</span></span>
* <span data-ttu-id="0cdd8-163">您應該會在預覽視窗中看到 [折紙] 物件。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-163">You should see the Origami objects in the preview window.</span></span>
* <span data-ttu-id="0cdd8-164">按第二次 [ **播放** ] 以停止預覽模式。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-164">Press **Play** a second time to stop preview mode.</span></span>

#### <a name="export-the-project-from-unity-to-visual-studio"></a><span data-ttu-id="0cdd8-165">將專案從 Unity 匯出至 Visual Studio</span><span class="sxs-lookup"><span data-stu-id="0cdd8-165">Export the project from Unity to Visual Studio</span></span>

* <span data-ttu-id="0cdd8-166">在 Unity 中，選取 [ **File > Build Settings**]。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-166">In Unity select **File > Build Settings**.</span></span>
* <span data-ttu-id="0cdd8-167">在 [**平臺**] 清單中選取 **通用 Windows 平臺**，然後按一下 [**切換平臺**]。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-167">Select **Universal Windows Platform** in the **Platform** list and click **Switch Platform**.</span></span>
* <span data-ttu-id="0cdd8-168">將 **SDK** 設定為 **通用 10** ，並將 **組建類型** 設定為 **D3D**。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-168">Set **SDK** to **Universal 10** and **Build Type** to **D3D**.</span></span>
* <span data-ttu-id="0cdd8-169">檢查 **Unity c # 專案**。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-169">Check **Unity C# Projects**.</span></span>
* <span data-ttu-id="0cdd8-170">按一下 [ **新增開啟場景** ] 以加入場景。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-170">Click **Add Open Scenes** to add the scene.</span></span>
* <span data-ttu-id="0cdd8-171">按一下 [建置]。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-171">Click **Build**.</span></span>
* <span data-ttu-id="0cdd8-172">在出現的 [檔案瀏覽器] 視窗中，建立名為 "App" 的 **新資料夾** 。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-172">In the file explorer window that appears, create a **New Folder** named "App".</span></span>
* <span data-ttu-id="0cdd8-173">按一下 **應用程式資料夾**。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-173">Single click the **App Folder**.</span></span>
* <span data-ttu-id="0cdd8-174">按下 [ **選取資料夾**]。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-174">Press **Select Folder**.</span></span>
* <span data-ttu-id="0cdd8-175">當 Unity 完成時，將會出現檔案總管視窗。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-175">When Unity is done, a File Explorer window will appear.</span></span>
* <span data-ttu-id="0cdd8-176">開啟 **應用程式** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-176">Open the **App** folder.</span></span>
* <span data-ttu-id="0cdd8-177">開啟 (按兩下) **的折紙**。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-177">Open (double click) **Origami.sln**.</span></span>
* <span data-ttu-id="0cdd8-178">使用 Visual Studio 中的頂端工具列，將目標從 Debug 變更為 **Release** ，以及從 ARM 變更為 **X86**。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-178">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **X86**.</span></span>
* <span data-ttu-id="0cdd8-179">按一下 [裝置] 按鈕旁邊的箭號，然後選取 [ **遠端電腦** ] 以透過 wi-fi 進行部署。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-179">Click on the arrow next to the Device button, and select **Remote Machine** to deploy over Wi-Fi.</span></span>
  * <span data-ttu-id="0cdd8-180">將 **位址** 設定為 HoloLens 的名稱或 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-180">Set the **Address** to the name or IP address of your HoloLens.</span></span> <span data-ttu-id="0cdd8-181">如果您不知道您的裝置 IP 位址，請查看 [ **設定] > 網路 & 網際網路 > [Advanced Options** ] 或 [問 Cortana **] 嗨 Cortana，我的 IP 位址為何？**</span><span class="sxs-lookup"><span data-stu-id="0cdd8-181">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options** or ask Cortana **"Hey Cortana, What's my IP address?"**</span></span>
  * <span data-ttu-id="0cdd8-182">如果 HoloLens 是透過 USB 連接，您可以改為選取要透過 USB 部署的 **裝置** 。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-182">If the HoloLens is attached over USB, you may instead select **Device** to deploy over USB.</span></span>
  * <span data-ttu-id="0cdd8-183">將 [ **驗證模式]** 設定為 [ **通用**]。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-183">Leave the **Authentication Mode** set to **Universal**.</span></span>
  * <span data-ttu-id="0cdd8-184">按一下 [**選取**]</span><span class="sxs-lookup"><span data-stu-id="0cdd8-184">Click **Select**</span></span>

* <span data-ttu-id="0cdd8-185">按一下 [ **Debug > 啟動但不進行調試** ]，或按 **Ctrl + F5**。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-185">Click **Debug > Start Without debugging** or press **Ctrl + F5**.</span></span> <span data-ttu-id="0cdd8-186">如果這是您第一次部署至您的裝置，您必須將 [它與 Visual Studio 配對](../../platform-capabilities-and-apis/using-visual-studio.md#pairing-your-device)。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-186">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](../../platform-capabilities-and-apis/using-visual-studio.md#pairing-your-device).</span></span>

* <span data-ttu-id="0cdd8-187">現在，將會建立日式的專案，並部署到您的 HoloLens，然後執行。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-187">The Origami project will now build, deploy to your HoloLens, and then run.</span></span>
* <span data-ttu-id="0cdd8-188">放在 HoloLens 上，看看看看您的新全息。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-188">Put on your HoloLens and look around to see your new holograms.</span></span>

## <a name="chapter-2---gaze"></a><span data-ttu-id="0cdd8-189">第2章-注視</span><span class="sxs-lookup"><span data-stu-id="0cdd8-189">Chapter 2 - Gaze</span></span>

>[!VIDEO https://www.youtube.com/embed/MSO2BoFSQbM]

<span data-ttu-id="0cdd8-190">在本章中，我們將介紹三種與您的全像的影像互動的第一種方式： [注視](../../../design/gaze-and-commit.md)。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-190">In this chapter, we are going to introduce the first of three ways of interacting with your holograms -- [gaze](../../../design/gaze-and-commit.md).</span></span>

### <a name="objectives"></a><span data-ttu-id="0cdd8-191">目標</span><span class="sxs-lookup"><span data-stu-id="0cdd8-191">Objectives</span></span>

* <span data-ttu-id="0cdd8-192">使用世界鎖定的資料指標將您的注視視覺化。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-192">Visualize your gaze using a world-locked cursor.</span></span>

### <a name="instructions"></a><span data-ttu-id="0cdd8-193">指示</span><span class="sxs-lookup"><span data-stu-id="0cdd8-193">Instructions</span></span>

* <span data-ttu-id="0cdd8-194">返回至您的 Unity 專案，如果仍然開啟 [組建設定] 視窗，請加以關閉。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-194">Go back to your Unity project, and close the Build Settings window if it's still open.</span></span>
* <span data-ttu-id="0cdd8-195">在 [**專案] 面板** 中，選取 [全像 **] 資料夾。**</span><span class="sxs-lookup"><span data-stu-id="0cdd8-195">Select the **Holograms** folder in the **Project panel**.</span></span>
* <span data-ttu-id="0cdd8-196">將資料 **指標** 物件拖曳至根層級的階層 **面板** 中。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-196">Drag the **Cursor** object into the **Hierarchy panel** at the root level.</span></span>
* <span data-ttu-id="0cdd8-197">按兩下資料 **指標** 物件，深入瞭解它。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-197">Double-click on the **Cursor** object to take a closer look at it.</span></span>
* <span data-ttu-id="0cdd8-198">以滑鼠右鍵按一下 [專案] 面板中的 [ **腳本** ] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-198">Right-click on the **Scripts** folder in the Project panel.</span></span>
* <span data-ttu-id="0cdd8-199">按一下 [ **建立** ] 子功能表。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-199">Click the **Create** sub-menu.</span></span>
* <span data-ttu-id="0cdd8-200">選取 **c # 腳本**。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-200">Select **C# Script**.</span></span>
* <span data-ttu-id="0cdd8-201">將腳本命名為 **WorldCursor**。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-201">Name the script **WorldCursor**.</span></span> <span data-ttu-id="0cdd8-202">注意：名稱會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-202">Note: The name is case-sensitive.</span></span> <span data-ttu-id="0cdd8-203">您不需要新增 .cs 副檔名。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-203">You do not need to add the .cs extension.</span></span>
* <span data-ttu-id="0cdd8-204">在 [階層]**面板** 中選取資料 **指標** 物件。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-204">Select the **Cursor** object in the **Hierarchy panel**.</span></span>
* <span data-ttu-id="0cdd8-205">將 **WorldCursor** 腳本拖放到 [ **檢查] 面板** 中。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-205">Drag and drop the **WorldCursor** script into the **Inspector panel**.</span></span>
* <span data-ttu-id="0cdd8-206">按兩下 **WorldCursor** 腳本，在 Visual Studio 中開啟它。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-206">Double-click the **WorldCursor** script to open it in Visual Studio.</span></span>
* <span data-ttu-id="0cdd8-207">將此程式碼複製並貼到 **WorldCursor.cs** 中，並 **全部儲存**。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-207">Copy and paste this code into **WorldCursor.cs** and **Save All**.</span></span>

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

            // Move the cursor to the point where the raycast hit.
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

* <span data-ttu-id="0cdd8-208">從檔案 **> 組建設定** 重建應用程式。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-208">Rebuild the app from **File > Build Settings**.</span></span>
* <span data-ttu-id="0cdd8-209">返回先前用來部署到 HoloLens 的 Visual Studio 方案。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-209">Return to the Visual Studio solution previously used to deploy to your HoloLens.</span></span>
* <span data-ttu-id="0cdd8-210">出現提示時，請選取 [全部重載]。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-210">Select 'Reload All' when prompted.</span></span>
* <span data-ttu-id="0cdd8-211">按一下 [ **Debug-> 啟動但不進行調試]，** 或按 **Ctrl + F5**。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-211">Click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
* <span data-ttu-id="0cdd8-212">現在看看場景，並注意游標如何與物件的形狀互動。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-212">Now look around the scene and notice how the cursor interacts with the shape of objects.</span></span>

## <a name="chapter-3---gestures"></a><span data-ttu-id="0cdd8-213">第3章-手勢</span><span class="sxs-lookup"><span data-stu-id="0cdd8-213">Chapter 3 - Gestures</span></span>

>[!VIDEO https://www.youtube.com/embed/kW3ThJ2MbvQ]

<span data-ttu-id="0cdd8-214">在本章中，我們將新增 [手勢](../../../design/gaze-and-commit.md#composite-gestures)的支援。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-214">In this chapter, we'll add support for [gestures](../../../design/gaze-and-commit.md#composite-gestures).</span></span> <span data-ttu-id="0cdd8-215">當使用者選取紙球體時，我們會使用 Unity 的物理引擎來開啟重力來使球體落在心。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-215">When the user selects a paper sphere, we'll make the sphere fall by turning on gravity using Unity's physics engine.</span></span>

### <a name="objectives"></a><span data-ttu-id="0cdd8-216">目標</span><span class="sxs-lookup"><span data-stu-id="0cdd8-216">Objectives</span></span>

* <span data-ttu-id="0cdd8-217">使用選取手勢來控制您的全像影像。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-217">Control your holograms with the Select gesture.</span></span>

### <a name="instructions"></a><span data-ttu-id="0cdd8-218">指示</span><span class="sxs-lookup"><span data-stu-id="0cdd8-218">Instructions</span></span>

<span data-ttu-id="0cdd8-219">我們將從建立腳本開始，然後偵測到選取的手勢。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-219">We'll start by creating a script then can detect the Select gesture.</span></span>

* <span data-ttu-id="0cdd8-220">在 [ **腳本** ] 資料夾中，建立名為 **GazeGestureManager** 的腳本。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-220">In the **Scripts** folder, create a script named **GazeGestureManager**.</span></span>
* <span data-ttu-id="0cdd8-221">將 **GazeGestureManager** 腳本拖曳至階層中的 **OrigamiCollection** 物件。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-221">Drag the **GazeGestureManager** script onto the **OrigamiCollection** object in the Hierarchy.</span></span>
* <span data-ttu-id="0cdd8-222">在 Visual Studio 中開啟 **GazeGestureManager** 腳本，並加入下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="0cdd8-222">Open the **GazeGestureManager** script in Visual Studio and add the following code:</span></span>

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
    void Awake()
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

* <span data-ttu-id="0cdd8-223">在腳本資料夾中建立另一個腳本，這次名為 **SphereCommands**。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-223">Create another script in the Scripts folder, this time named **SphereCommands**.</span></span>
* <span data-ttu-id="0cdd8-224">展開階層視圖中的 [ **OrigamiCollection** ] 物件。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-224">Expand the **OrigamiCollection** object in the Hierarchy view.</span></span>
* <span data-ttu-id="0cdd8-225">將 **SphereCommands** 腳本拖曳至 [階層] 面板中的 **Sphere1** 物件。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-225">Drag the **SphereCommands** script onto the **Sphere1** object in the Hierarchy panel.</span></span>
* <span data-ttu-id="0cdd8-226">將 **SphereCommands** 腳本拖曳至 [階層] 面板中的 **Sphere2** 物件。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-226">Drag the **SphereCommands** script onto the **Sphere2** object in the Hierarchy panel.</span></span>
* <span data-ttu-id="0cdd8-227">在 Visual Studio 中開啟腳本進行編輯，並將預設程式碼取代為下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="0cdd8-227">Open the script in Visual Studio for editing, and replace the default code with this:</span></span>

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

* <span data-ttu-id="0cdd8-228">匯出、建立應用程式，並將其部署到 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-228">Export, build and deploy the app to your HoloLens.</span></span>
* <span data-ttu-id="0cdd8-229">查看其中一個球體。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-229">Look at one of the spheres.</span></span>
* <span data-ttu-id="0cdd8-230">執行 [選取手勢]，並監看下圖上的球體。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-230">Perform the select gesture and watch the sphere drop onto the surface below.</span></span>

## <a name="chapter-4---voice"></a><span data-ttu-id="0cdd8-231">第4章-語音</span><span class="sxs-lookup"><span data-stu-id="0cdd8-231">Chapter 4 - Voice</span></span>

>[!VIDEO https://www.youtube.com/embed/1-Aq0VVtHM8]

<span data-ttu-id="0cdd8-232">在本章中，我們將新增兩個 [語音命令](../../../design/voice-input.md)的支援：「重設世界」以將捨棄的球體傳回其原始位置，以及「捨棄球體」以使球體落在外。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-232">In this chapter, we'll add support for two [voice commands](../../../design/voice-input.md): "Reset world" to return the dropped spheres to their original location, and "Drop sphere" to make the sphere fall.</span></span>

### <a name="objectives"></a><span data-ttu-id="0cdd8-233">目標</span><span class="sxs-lookup"><span data-stu-id="0cdd8-233">Objectives</span></span>

* <span data-ttu-id="0cdd8-234">新增一律在背景中接聽的語音命令。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-234">Add voice commands that always listen in the background.</span></span>
* <span data-ttu-id="0cdd8-235">建立可回應語音命令的全像影像。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-235">Create a hologram that reacts to a voice command.</span></span>

### <a name="instructions"></a><span data-ttu-id="0cdd8-236">指示</span><span class="sxs-lookup"><span data-stu-id="0cdd8-236">Instructions</span></span>

* <span data-ttu-id="0cdd8-237">在 [ **腳本** ] 資料夾中，建立名為 **SpeechManager** 的腳本。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-237">In the **Scripts** folder, create a script named **SpeechManager**.</span></span>
* <span data-ttu-id="0cdd8-238">將 **SpeechManager** 腳本拖曳至階層中的 **OrigamiCollection** 物件</span><span class="sxs-lookup"><span data-stu-id="0cdd8-238">Drag the **SpeechManager** script onto the **OrigamiCollection** object in the Hierarchy</span></span>
* <span data-ttu-id="0cdd8-239">在 Visual Studio 中開啟 **SpeechManager** 腳本。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-239">Open the **SpeechManager** script in Visual Studio.</span></span>
* <span data-ttu-id="0cdd8-240">將此程式碼複製並貼到 **SpeechManager.cs** 中，並 **全部儲存**：</span><span class="sxs-lookup"><span data-stu-id="0cdd8-240">Copy and paste this code into **SpeechManager.cs** and **Save All**:</span></span>

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

* <span data-ttu-id="0cdd8-241">在 Visual Studio 中開啟 **SphereCommands** 腳本。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-241">Open the **SphereCommands** script in Visual Studio.</span></span>
* <span data-ttu-id="0cdd8-242">更新腳本以進行讀取，如下所示：</span><span class="sxs-lookup"><span data-stu-id="0cdd8-242">Update the script to read as follows:</span></span>

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

* <span data-ttu-id="0cdd8-243">匯出、建立應用程式，並將其部署到 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-243">Export, build and deploy the app to your HoloLens.</span></span>
* <span data-ttu-id="0cdd8-244">查看其中一個球體，然後說出「**捨棄球體**」。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-244">Look at one of the spheres, and say "**Drop Sphere**".</span></span>
* <span data-ttu-id="0cdd8-245">說「**重設世界**」將它們帶回其初始位置。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-245">Say "**Reset World**" to bring them back to their initial positions.</span></span>

## <a name="chapter-5---spatial-sound"></a><span data-ttu-id="0cdd8-246">第5章-空間音效</span><span class="sxs-lookup"><span data-stu-id="0cdd8-246">Chapter 5 - Spatial sound</span></span>

>[!VIDEO https://www.youtube.com/embed/Aj4de5Ncbfo]

<span data-ttu-id="0cdd8-247">在本章中，我們會將音樂新增至應用程式，然後觸發對某些動作的音效效果。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-247">In this chapter, we'll add music to the app, and then trigger sound effects on certain actions.</span></span> <span data-ttu-id="0cdd8-248">我們會使用 [空間音效](../../../design/spatial-sound.md) ，在3d 空間中提供音效的特定位置。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-248">We'll be using [spatial sound](../../../design/spatial-sound.md) to give sounds a specific location in 3D space.</span></span>

### <a name="objectives"></a><span data-ttu-id="0cdd8-249">目標</span><span class="sxs-lookup"><span data-stu-id="0cdd8-249">Objectives</span></span>

* <span data-ttu-id="0cdd8-250">聽聽您的全球全像投影。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-250">Hear holograms in your world.</span></span>

### <a name="instructions"></a><span data-ttu-id="0cdd8-251">指示</span><span class="sxs-lookup"><span data-stu-id="0cdd8-251">Instructions</span></span>

* <span data-ttu-id="0cdd8-252">在 Unity 中，從頂端功能表中選取 [ **編輯] > 專案設定 > 音訊**</span><span class="sxs-lookup"><span data-stu-id="0cdd8-252">In Unity select from the top menu **Edit > Project Settings > Audio**</span></span>
* <span data-ttu-id="0cdd8-253">在右側的 [偵測器] 面板中，尋找 **空間定位器外掛程式** 設定，然後選取 **MS HRTF 空間定位器**。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-253">In the Inspector Panel on the right side, find the **Spatializer Plugin** setting and select **MS HRTF Spatializer**.</span></span>
* <span data-ttu-id="0cdd8-254">從 [專案] 面板中的 [全像 **] 資料夾，** 將 [ **環境** ] 物件拖曳至 [階層] 面板中的 [ **OrigamiCollection** ] 物件。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-254">From the **Holograms** folder in the Project panel, drag the **Ambience** object onto the **OrigamiCollection** object in the Hierarchy Panel.</span></span>
* <span data-ttu-id="0cdd8-255">選取 [ **OrigamiCollection** ]，然後在 [偵測器] 面板中尋找 **音訊來源** 元件。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-255">Select **OrigamiCollection** and find the **Audio Source** component in the Inspector panel.</span></span> <span data-ttu-id="0cdd8-256">變更這些屬性：</span><span class="sxs-lookup"><span data-stu-id="0cdd8-256">Change these properties:</span></span>
  * <span data-ttu-id="0cdd8-257">檢查 **Spatialize** 屬性。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-257">Check the **Spatialize** property.</span></span>
  * <span data-ttu-id="0cdd8-258">檢查是否 **在喚醒時播放**。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-258">Check the **Play On Awake**.</span></span>
  * <span data-ttu-id="0cdd8-259">將滑杆向右拖曳，以將 **空間 Blend** 變更為 **3d** 。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-259">Change **Spatial Blend** to **3D** by dragging the slider all the way to the right.</span></span> <span data-ttu-id="0cdd8-260">當您移動滑杆時，值應該會從0變更為1。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-260">The value should change from 0 to 1 when you move the slider.</span></span>
  * <span data-ttu-id="0cdd8-261">檢查 **迴圈** 屬性。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-261">Check the **Loop** property.</span></span>
  * <span data-ttu-id="0cdd8-262">展開 [ **3D 音效設定**]，然後輸入 **0.1** 作為 **Doppler 等級**。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-262">Expand **3D Sound Settings**, and enter **0.1** for **Doppler Level**.</span></span>
  * <span data-ttu-id="0cdd8-263">將 **Volume Rolloff** 設為 **對數 Rolloff**。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-263">Set **Volume Rolloff** to **Logarithmic Rolloff**.</span></span>
  * <span data-ttu-id="0cdd8-264">將 **最大距離** 設定為 **20**。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-264">Set **Max Distance** to **20**.</span></span>
* <span data-ttu-id="0cdd8-265">在 [ **腳本** ] 資料夾中，建立名為 **SphereSounds** 的腳本。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-265">In the **Scripts** folder, create a script named **SphereSounds**.</span></span>
* <span data-ttu-id="0cdd8-266">將 **SphereSounds** 拖放到階層中的 **Sphere1** 和 **Sphere2** 物件。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-266">Drag and drop **SphereSounds** to the **Sphere1** and **Sphere2** objects in the Hierarchy.</span></span>
* <span data-ttu-id="0cdd8-267">在 Visual Studio 中開啟 **SphereSounds** ，更新下列程式碼並 **全部儲存**。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-267">Open **SphereSounds** in Visual Studio, update the following code and **Save All**.</span></span>

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

* <span data-ttu-id="0cdd8-268">儲存腳本，並回到 Unity。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-268">Save the script, and return to Unity.</span></span>
* <span data-ttu-id="0cdd8-269">匯出、建立應用程式，並將其部署到 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-269">Export, build and deploy the app to your HoloLens.</span></span>
* <span data-ttu-id="0cdd8-270">從這個階段中更深入且更進一步的移動，然後輪流以聆聽音效的變化。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-270">Move closer and further from the Stage and turn side-to-side to hear the sounds change.</span></span>

## <a name="chapter-6---spatial-mapping"></a><span data-ttu-id="0cdd8-271">第6章-空間對應</span><span class="sxs-lookup"><span data-stu-id="0cdd8-271">Chapter 6 - Spatial mapping</span></span>

>[!VIDEO https://www.youtube.com/embed/Pkt1_wNLLXY]

<span data-ttu-id="0cdd8-272">現在我們要使用 [空間對應](../../../design/spatial-mapping.md) ，將遊戲台放在真實世界中的真實物件上。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-272">Now we are going to use [spatial mapping](../../../design/spatial-mapping.md) to place the game board on a real object in the real world.</span></span>

### <a name="objectives"></a><span data-ttu-id="0cdd8-273">目標</span><span class="sxs-lookup"><span data-stu-id="0cdd8-273">Objectives</span></span>

* <span data-ttu-id="0cdd8-274">將您的真實世界帶入虛擬世界。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-274">Bring your real world into the virtual world.</span></span>
* <span data-ttu-id="0cdd8-275">將您的全像放在最重要的地方。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-275">Place your holograms where they matter most to you.</span></span>

### <a name="instructions"></a><span data-ttu-id="0cdd8-276">指示</span><span class="sxs-lookup"><span data-stu-id="0cdd8-276">Instructions</span></span>

* <span data-ttu-id="0cdd8-277">在 Unity 中，按一下 [專案] 面板中的 [ **全息** 全像] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-277">In Unity, click on the **Holograms** folder in the Project panel.</span></span>
* <span data-ttu-id="0cdd8-278">將 **空間對應** 資產拖曳至 **階層的根目錄。**</span><span class="sxs-lookup"><span data-stu-id="0cdd8-278">Drag the **Spatial Mapping** asset into the root of the **Hierarchy**.</span></span>
* <span data-ttu-id="0cdd8-279">按一下階層中的 **空間對應** 物件。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-279">Click on the **Spatial Mapping** object in the Hierarchy.</span></span>
* <span data-ttu-id="0cdd8-280">在 [偵測 **器] 面板** 中，變更下列屬性：</span><span class="sxs-lookup"><span data-stu-id="0cdd8-280">In the **Inspector panel**, change the following properties:</span></span>
  * <span data-ttu-id="0cdd8-281">選取 [ **繪製視覺網格** ] 方塊。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-281">Check the **Draw Visual Meshes** box.</span></span>
  * <span data-ttu-id="0cdd8-282">找出 **繪製材質** ，然後按一下右側的圓形。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-282">Locate **Draw Material** and click the circle on the right.</span></span> <span data-ttu-id="0cdd8-283">在頂端的搜尋欄位中輸入「**線框**」。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-283">Type "**wireframe**" into the search field at the top.</span></span> <span data-ttu-id="0cdd8-284">按一下結果，然後關閉視窗。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-284">Click on the result and then close the window.</span></span> <span data-ttu-id="0cdd8-285">當您這樣做時，繪製材質的值應該會設定為線框。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-285">When you do this, the value for Draw Material should get set to Wireframe.</span></span>
* <span data-ttu-id="0cdd8-286">匯出、建立應用程式，並將其部署到 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-286">Export, build and deploy the app to your HoloLens.</span></span>
* <span data-ttu-id="0cdd8-287">當應用程式執行時，線框網格會與您的真實世界重迭。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-287">When the app runs, a wireframe mesh will overlay your real world.</span></span>
* <span data-ttu-id="0cdd8-288">觀賞輪流球體將如何落在此階段，並進入地面上！</span><span class="sxs-lookup"><span data-stu-id="0cdd8-288">Watch how a rolling sphere will fall off the stage, and onto the floor!</span></span>

<span data-ttu-id="0cdd8-289">現在，我們將示範如何將 OrigamiCollection 移至新位置：</span><span class="sxs-lookup"><span data-stu-id="0cdd8-289">Now we'll show you how to move the OrigamiCollection to a new location:</span></span>

* <span data-ttu-id="0cdd8-290">在 [ **腳本** ] 資料夾中，建立名為 **TapToPlaceParent** 的腳本。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-290">In the **Scripts** folder, create a script named **TapToPlaceParent**.</span></span>
* <span data-ttu-id="0cdd8-291">在階層 **中，展開**[ **OrigamiCollection** ]，然後選取 [ **階段** ] 物件。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-291">In the **Hierarchy**, expand the **OrigamiCollection** and select the **Stage** object.</span></span>
* <span data-ttu-id="0cdd8-292">將 **TapToPlaceParent** 腳本拖曳至階段物件。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-292">Drag the **TapToPlaceParent** script onto the Stage object.</span></span>
* <span data-ttu-id="0cdd8-293">在 Visual Studio 中開啟 **TapToPlaceParent** 腳本，並將其更新為下列內容：</span><span class="sxs-lookup"><span data-stu-id="0cdd8-293">Open the **TapToPlaceParent** script in Visual Studio, and update it to be the following:</span></span>

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

* <span data-ttu-id="0cdd8-294">匯出、建立及部署應用程式。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-294">Export, build and deploy the app.</span></span>
* <span data-ttu-id="0cdd8-295">現在，您應該可以使用 Select 手勢，然後移至新位置，然後再使用 [選取手勢]，將遊戲放在特定的位置撥雲見日。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-295">Now you should now be able to place the game in a specific location by gazing at it, using the Select gesture and then moving to a new location, and using the Select gesture again.</span></span>

## <a name="chapter-7---holographic-fun"></a><span data-ttu-id="0cdd8-296">第7章-全像愉快</span><span class="sxs-lookup"><span data-stu-id="0cdd8-296">Chapter 7 - Holographic fun</span></span>

### <a name="objectives"></a><span data-ttu-id="0cdd8-297">目標</span><span class="sxs-lookup"><span data-stu-id="0cdd8-297">Objectives</span></span>

* <span data-ttu-id="0cdd8-298">顯示全像 underworld 的進入。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-298">Reveal the entrance to a holographic underworld.</span></span>

### <a name="instructions"></a><span data-ttu-id="0cdd8-299">指示</span><span class="sxs-lookup"><span data-stu-id="0cdd8-299">Instructions</span></span>

<span data-ttu-id="0cdd8-300">現在，我們將示範如何發掘全像 underworld：</span><span class="sxs-lookup"><span data-stu-id="0cdd8-300">Now we'll show you how to uncover the holographic underworld:</span></span>

* <span data-ttu-id="0cdd8-301">從 [專案] 面板中 **的 [全** 像全像] 資料夾：</span><span class="sxs-lookup"><span data-stu-id="0cdd8-301">From the **Holograms** folder in the Project Panel:</span></span>
  * <span data-ttu-id="0cdd8-302">將 **Underworld** 拖曳到階層中，以成為 **OrigamiCollection** 的子系。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-302">Drag **Underworld** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
* <span data-ttu-id="0cdd8-303">在 [ **腳本** ] 資料夾中，建立名為 **HitTarget** 的腳本。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-303">In the **Scripts** folder, create a script named **HitTarget**.</span></span>
* <span data-ttu-id="0cdd8-304">**在階層中，展開**[ **OrigamiCollection**]。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-304">In the **Hierarchy**, expand the **OrigamiCollection**.</span></span>
* <span data-ttu-id="0cdd8-305">展開 [ **階段** ] 物件，然後選取 [ **目標** 物件] (藍色風扇) 。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-305">Expand the **Stage** object and select the **Target** object (blue fan).</span></span>
* <span data-ttu-id="0cdd8-306">將 **HitTarget** 腳本拖曳至 **目標** 物件。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-306">Drag the **HitTarget** script onto the **Target** object.</span></span>
* <span data-ttu-id="0cdd8-307">在 Visual Studio 中開啟 **HitTarget** 腳本，並將其更新為下列內容：</span><span class="sxs-lookup"><span data-stu-id="0cdd8-307">Open the **HitTarget** script in Visual Studio, and update it to be the following:</span></span>

```cs
using UnityEngine;

public class HitTarget : MonoBehaviour
{
    // These public fields become settable properties in the Unity editor.
    public GameObject underworld;
    public GameObject objectToHide;

    // Occurs when this object starts colliding with another object
    void OnCollisionEnter(Collision collision)
    {
        // Hide the stage and show the underworld.
        objectToHide.SetActive(false);
        underworld.SetActive(true);

        // Disable Spatial Mapping to let the spheres enter the underworld.
        SpatialMapping.Instance.MappingEnabled = false;
    }
}
```

* <span data-ttu-id="0cdd8-308">在 Unity 中，選取 **目標** 物件。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-308">In Unity, select the **Target** object.</span></span>
* <span data-ttu-id="0cdd8-309">兩個公用屬性現在會顯示在 **點擊目標** 元件中，而且必須參考場景中的物件：</span><span class="sxs-lookup"><span data-stu-id="0cdd8-309">Two public properties are now visible on the **Hit Target** component and need to reference objects in our scene:</span></span>
  * <span data-ttu-id="0cdd8-310">將 [ **Underworld** ] 從 [階層 **] 面板拖曳** 至 [**點擊目標**] 元件上的 **Underworld** 屬性。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-310">Drag **Underworld** from the **Hierarchy** panel to the **Underworld** property on the **Hit Target** component.</span></span>
  * <span data-ttu-id="0cdd8-311">將 [階層]**面板中的 [** **階段**] 拖曳至 **物件，以隱藏\*\*\*\*點擊目標** 元件上的屬性。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-311">Drag **Stage** from the **Hierarchy** panel to the **Object to Hide** property on the **Hit Target** component.</span></span>
* <span data-ttu-id="0cdd8-312">匯出、建立及部署應用程式。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-312">Export, build and deploy the app.</span></span>
* <span data-ttu-id="0cdd8-313">將折紙集合放在樓層，然後使用 Select 手勢來放置球體。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-313">Place the Origami Collection on the floor, and then use the Select gesture to make a sphere drop.</span></span>
* <span data-ttu-id="0cdd8-314">當球體達到目標 (藍色風扇) 時，將會發生爆炸。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-314">When the sphere hits the target (blue fan), an explosion will occur.</span></span> <span data-ttu-id="0cdd8-315">將會隱藏此集合，並顯示 underworld 的孔洞。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-315">The collection will be hidden and a hole to the underworld will appear.</span></span>

## <a name="the-end"></a><span data-ttu-id="0cdd8-316">結束</span><span class="sxs-lookup"><span data-stu-id="0cdd8-316">The end</span></span>

<span data-ttu-id="0cdd8-317">這就是本教學課程的結尾！</span><span class="sxs-lookup"><span data-stu-id="0cdd8-317">And that's the end of this tutorial!</span></span>

<span data-ttu-id="0cdd8-318">您已了解︰</span><span class="sxs-lookup"><span data-stu-id="0cdd8-318">You learned:</span></span>

* <span data-ttu-id="0cdd8-319">如何在 Unity 中建立全像內建應用程式。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-319">How to create a holographic app in Unity.</span></span>
* <span data-ttu-id="0cdd8-320">如何利用注視、手勢、語音、音效和空間對應。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-320">How to make use of gaze, gesture, voice, sound, and spatial mapping.</span></span>
* <span data-ttu-id="0cdd8-321">如何使用 Visual Studio 來建立和部署應用程式。</span><span class="sxs-lookup"><span data-stu-id="0cdd8-321">How to build and deploy an app using Visual Studio.</span></span>

<span data-ttu-id="0cdd8-322">您現在已準備好開始建立自己的全像攝影體驗！</span><span class="sxs-lookup"><span data-stu-id="0cdd8-322">You are now ready to start creating your own holographic experience!</span></span>

## <a name="see-also"></a><span data-ttu-id="0cdd8-323">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0cdd8-323">See also</span></span>

* [<span data-ttu-id="0cdd8-324">MR Basics 101E：使用模擬器完成專案</span><span class="sxs-lookup"><span data-stu-id="0cdd8-324">MR Basics 101E: Complete project with emulator</span></span>](holograms-101e.md)
* [<span data-ttu-id="0cdd8-325">目光</span><span class="sxs-lookup"><span data-stu-id="0cdd8-325">Gaze</span></span>](../../../design/gaze-and-commit.md)
* [<span data-ttu-id="0cdd8-326">頭部目光和行動</span><span class="sxs-lookup"><span data-stu-id="0cdd8-326">Head-gaze and commit</span></span>](../../../design/gaze-and-commit.md)
* [<span data-ttu-id="0cdd8-327">語音輸入</span><span class="sxs-lookup"><span data-stu-id="0cdd8-327">Voice input</span></span>](../../../design/voice-input.md)
* [<span data-ttu-id="0cdd8-328">空間音效</span><span class="sxs-lookup"><span data-stu-id="0cdd8-328">Spatial sound</span></span>](../../../design/spatial-sound.md)
* [<span data-ttu-id="0cdd8-329">空間對應</span><span class="sxs-lookup"><span data-stu-id="0cdd8-329">Spatial mapping</span></span>](../../../design/spatial-mapping.md)