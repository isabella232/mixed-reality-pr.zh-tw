---
title: MR Spatial 230 - 空間對應
description: 遵循此程式碼逐步解說，使用 Unity、Visual Studio 和 HoloLens 來瞭解空間對應概念的詳細資料。
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit、mixedrealitytoolkit、mixedrealitytoolkit-unity、學術、教學課程、空間對應、表面重建、網格、HoloLens、混合現實學院、unity、混合現實耳機、windows Mixed reality 耳機、虛擬實境耳機、Windows 10
ms.openlocfilehash: 6b218de239da04190fbf08ff8668fa16009df949
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/20/2021
ms.locfileid: "98582935"
---
# <a name="mr-spatial-230-spatial-mapping"></a><span data-ttu-id="5778b-104">MR Spatial 230：空間對應</span><span class="sxs-lookup"><span data-stu-id="5778b-104">MR Spatial 230: Spatial mapping</span></span>

>[!NOTE]
><span data-ttu-id="5778b-105">混合實境學院教學課程的設計是以 HoloLens (第 1 代) 和混合實境沉浸式頭戴裝置為準。</span><span class="sxs-lookup"><span data-stu-id="5778b-105">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="5778b-106">因此，對於仍在尋找這些裝置開發指引的開發人員而言，我們覺得這些教學課程很重要。</span><span class="sxs-lookup"><span data-stu-id="5778b-106">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="5778b-107">這些教學課程 **_不會_** 使用用於 HoloLens 2 的最新工具組或互動進行更新。</span><span class="sxs-lookup"><span data-stu-id="5778b-107">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="5778b-108">系統會保留這些資訊，以繼續在支援的裝置上運作。</span><span class="sxs-lookup"><span data-stu-id="5778b-108">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="5778b-109">已針對 HoloLens 2 公佈[一系列新的教學課程](./mr-learning-base-01.md)。</span><span class="sxs-lookup"><span data-stu-id="5778b-109">[A new series of tutorials](./mr-learning-base-01.md) has been posted for HoloLens 2.</span></span>

<span data-ttu-id="5778b-110">[空間對應](../../../design/spatial-mapping.md) 結合了真實世界和虛擬世界，藉由教授有關環境的影像。</span><span class="sxs-lookup"><span data-stu-id="5778b-110">[Spatial mapping](../../../design/spatial-mapping.md) combines the real world and virtual world together by teaching holograms about the environment.</span></span> <span data-ttu-id="5778b-111">在 MR 空間 230 (Project 天文館) 我們將瞭解如何：</span><span class="sxs-lookup"><span data-stu-id="5778b-111">In MR Spatial 230 (Project Planetarium) we'll learn how to:</span></span>

* <span data-ttu-id="5778b-112">掃描環境，並將資料從 HoloLens 傳送至您的開發電腦。</span><span class="sxs-lookup"><span data-stu-id="5778b-112">Scan the environment and transfer data from the HoloLens to your development machine.</span></span>
* <span data-ttu-id="5778b-113">探索著色器，並學習如何使用它們來視覺化您的空間。</span><span class="sxs-lookup"><span data-stu-id="5778b-113">Explore shaders and learn how to use them for visualizing your space.</span></span>
* <span data-ttu-id="5778b-114">使用網格處理將房間網格細分為簡單的平面。</span><span class="sxs-lookup"><span data-stu-id="5778b-114">Break down the room mesh into simple planes using mesh processing.</span></span>
* <span data-ttu-id="5778b-115">超越我們在 [MR 基礎 101](../../../develop/unity/tutorials/holograms-101.md)中學習到的放置技術，並提供可在環境中放置全息圖的相關意見反應。</span><span class="sxs-lookup"><span data-stu-id="5778b-115">Go beyond the placement techniques we learned in [MR Basics 101](../../../develop/unity/tutorials/holograms-101.md), and provide feedback about where a hologram can be placed in the environment.</span></span>
* <span data-ttu-id="5778b-116">探索遮蔽效果，如此一來，當您的全像是真實世界的物件之後，您仍然可以透過 x 光線視覺來看到它！</span><span class="sxs-lookup"><span data-stu-id="5778b-116">Explore occlusion effects, so when your hologram is behind a real-world object, you can still see it with x-ray vision!</span></span>

>[!VIDEO https://www.youtube.com/embed/NSNYRkUX6Mw]

## <a name="device-support"></a><span data-ttu-id="5778b-117">裝置支援</span><span class="sxs-lookup"><span data-stu-id="5778b-117">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="5778b-118">課程</span><span class="sxs-lookup"><span data-stu-id="5778b-118">Course</span></span></th><th style="width:150px"> <span data-ttu-id="5778b-119"><a href="/hololens/hololens1-hardware">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="5778b-119"><a href="/hololens/hololens1-hardware">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="5778b-120"><a href="../../../discover/immersive-headset-hardware-details.md">沉浸式頭戴裝置</a></span><span class="sxs-lookup"><span data-stu-id="5778b-120"><a href="../../../discover/immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="5778b-121">MR Spatial 230：空間對應</span><span class="sxs-lookup"><span data-stu-id="5778b-121">MR Spatial 230: Spatial mapping</span></span></td><td style="text-align: center;"> <span data-ttu-id="5778b-122">✔️</span><span class="sxs-lookup"><span data-stu-id="5778b-122">✔️</span></span></td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="5778b-123">在您開始使用 Intune 之前</span><span class="sxs-lookup"><span data-stu-id="5778b-123">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="5778b-124">必要條件</span><span class="sxs-lookup"><span data-stu-id="5778b-124">Prerequisites</span></span>

* <span data-ttu-id="5778b-125">[已安裝正確工具](../../../develop/install-the-tools.md)的 Windows 10 電腦。</span><span class="sxs-lookup"><span data-stu-id="5778b-125">A Windows 10 PC configured with the correct [tools installed](../../../develop/install-the-tools.md).</span></span>
* <span data-ttu-id="5778b-126">一些基本的 c # 程式設計功能。</span><span class="sxs-lookup"><span data-stu-id="5778b-126">Some basic C# programming ability.</span></span>
* <span data-ttu-id="5778b-127">您應已完成 [MR 基本的 101](../../../develop/unity/tutorials/holograms-101.md)。</span><span class="sxs-lookup"><span data-stu-id="5778b-127">You should have completed [MR Basics 101](../../../develop/unity/tutorials/holograms-101.md).</span></span>
* <span data-ttu-id="5778b-128">[針對開發設定](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)的 HoloLens 裝置。</span><span class="sxs-lookup"><span data-stu-id="5778b-128">A HoloLens device [configured for development](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="5778b-129">專案檔</span><span class="sxs-lookup"><span data-stu-id="5778b-129">Project files</span></span>

* <span data-ttu-id="5778b-130">下載專案 [所需的](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-230-SpatialMapping.zip) 檔案。</span><span class="sxs-lookup"><span data-stu-id="5778b-130">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-230-SpatialMapping.zip) required by the project.</span></span> <span data-ttu-id="5778b-131">需要 Unity 2017.2 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="5778b-131">Requires Unity 2017.2 or later.</span></span>
  * <span data-ttu-id="5778b-132">如果您仍然需要 Unity 5.6 支援，請使用 [此版本](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-230.zip)。</span><span class="sxs-lookup"><span data-stu-id="5778b-132">If you still need Unity 5.6 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-230.zip).</span></span>
  * <span data-ttu-id="5778b-133">如果您仍然需要 Unity 5.5 支援，請使用 [此版本](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-230.zip)。</span><span class="sxs-lookup"><span data-stu-id="5778b-133">If you still need Unity 5.5 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-230.zip).</span></span>
  * <span data-ttu-id="5778b-134">如果您仍然需要 Unity 5.4 支援，請使用 [此版本](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-230.zip)。</span><span class="sxs-lookup"><span data-stu-id="5778b-134">If you still need Unity 5.4 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-230.zip).</span></span>
* <span data-ttu-id="5778b-135">取消將檔案封存到您的桌面或其他易於觸及的位置。</span><span class="sxs-lookup"><span data-stu-id="5778b-135">Un-archive the files to your desktop or other easy to reach location.</span></span>

>[!NOTE]
><span data-ttu-id="5778b-136">如果您想要在下載之前查看原始程式碼， [可在 GitHub 上](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-230-SpatialMapping)取得。</span><span class="sxs-lookup"><span data-stu-id="5778b-136">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-230-SpatialMapping).</span></span>

### <a name="notes"></a><span data-ttu-id="5778b-137">備註</span><span class="sxs-lookup"><span data-stu-id="5778b-137">Notes</span></span>

* <span data-ttu-id="5778b-138">在 Visual Studio 中必須停用 [啟用 Just My Code] (*取消* 核取 [工具] > [選項] > [選項] 下的) ，才能在程式碼中叫用中斷點。</span><span class="sxs-lookup"><span data-stu-id="5778b-138">"Enable Just My Code" in Visual Studio needs to be disabled (*unchecked*) under Tools > Options > Debugging in order to hit breakpoints in your code.</span></span>

## <a name="unity-setup"></a><span data-ttu-id="5778b-139">Unity 設定</span><span class="sxs-lookup"><span data-stu-id="5778b-139">Unity setup</span></span>

>[!VIDEO https://www.youtube.com/embed/y2Y4LhK6TEM]

* <span data-ttu-id="5778b-140">啟動 **Unity**。</span><span class="sxs-lookup"><span data-stu-id="5778b-140">Start **Unity**.</span></span>
* <span data-ttu-id="5778b-141">選取 [ **新增** ] 以建立新專案。</span><span class="sxs-lookup"><span data-stu-id="5778b-141">Select **New** to create a new project.</span></span>
* <span data-ttu-id="5778b-142">將專案命名為 **天文館**。</span><span class="sxs-lookup"><span data-stu-id="5778b-142">Name the project **Planetarium**.</span></span>
* <span data-ttu-id="5778b-143">確認已選取 [ **3d** ] 設定。</span><span class="sxs-lookup"><span data-stu-id="5778b-143">Verify that the **3D** setting is selected.</span></span>
* <span data-ttu-id="5778b-144">按一下 [ **建立專案**]。</span><span class="sxs-lookup"><span data-stu-id="5778b-144">Click **Create Project**.</span></span>
* <span data-ttu-id="5778b-145">Unity 啟動後，請移至 **> Player 的 [編輯 > 專案設定**]。</span><span class="sxs-lookup"><span data-stu-id="5778b-145">Once Unity launches, go to **Edit > Project Settings > Player**.</span></span>
* <span data-ttu-id="5778b-146">在 [偵測 **器** ] 面板中，尋找並選取綠色的 **Windows 商店** 圖示。</span><span class="sxs-lookup"><span data-stu-id="5778b-146">In the **Inspector** panel, find and select the green **Windows Store** icon.</span></span>
* <span data-ttu-id="5778b-147">展開 [ **其他設定**]。</span><span class="sxs-lookup"><span data-stu-id="5778b-147">Expand **Other Settings**.</span></span>
* <span data-ttu-id="5778b-148">**在 [轉譯] 區段中**，檢查 **虛擬實境支援** 的選項。</span><span class="sxs-lookup"><span data-stu-id="5778b-148">In the **Rendering** section, check the **Virtual Reality Supported** option.</span></span>
* <span data-ttu-id="5778b-149">確認 **Windows** 全像是出現在 **虛擬實境 sdk** 清單中。</span><span class="sxs-lookup"><span data-stu-id="5778b-149">Verify that **Windows Holographic** appears in the list of **Virtual Reality SDKs**.</span></span> <span data-ttu-id="5778b-150">如果沒有，請選取 **+** 清單底部的按鈕，然後選擇 [ **Windows** 全像]。</span><span class="sxs-lookup"><span data-stu-id="5778b-150">If not, select the **+** button at the bottom of the list and choose **Windows Holographic**.</span></span>
* <span data-ttu-id="5778b-151">展開 [ **發行設定**]。</span><span class="sxs-lookup"><span data-stu-id="5778b-151">Expand **Publishing Settings**.</span></span>
* <span data-ttu-id="5778b-152">在 [ **功能** ] 區段中，檢查下列設定：</span><span class="sxs-lookup"><span data-stu-id="5778b-152">In the **Capabilities** section, check the following settings:</span></span>
    * <span data-ttu-id="5778b-153">InternetClientServer</span><span class="sxs-lookup"><span data-stu-id="5778b-153">InternetClientServer</span></span>
    * <span data-ttu-id="5778b-154">PrivateNetworkClientServer</span><span class="sxs-lookup"><span data-stu-id="5778b-154">PrivateNetworkClientServer</span></span>
    * <span data-ttu-id="5778b-155">麥克風</span><span class="sxs-lookup"><span data-stu-id="5778b-155">Microphone</span></span>
    * <span data-ttu-id="5778b-156">SpatialPerception</span><span class="sxs-lookup"><span data-stu-id="5778b-156">SpatialPerception</span></span>
* <span data-ttu-id="5778b-157">移至 [ **編輯] > 專案設定 > 品質**</span><span class="sxs-lookup"><span data-stu-id="5778b-157">Go to **Edit > Project Settings > Quality**</span></span>
* <span data-ttu-id="5778b-158">在 [偵測 **器** ] 面板的 [Windows 市集中] 圖示底下，選取 [預設] 資料列底下的黑色下拉箭號，並將預設設定變更為 [ **非常低**]。</span><span class="sxs-lookup"><span data-stu-id="5778b-158">In the **Inspector** panel, under the Windows Store icon, select the black drop-down arrow under the 'Default' row and change the default setting to **Very Low**.</span></span>
* <span data-ttu-id="5778b-159">移至 [ **資產] > 匯入套件 > 自訂套件**。</span><span class="sxs-lookup"><span data-stu-id="5778b-159">Go to **Assets > Import Package > Custom Package**.</span></span>
* <span data-ttu-id="5778b-160">流覽至 **..\holographicacademy-holograms-230-SpatialMapping\Starting** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="5778b-160">Navigate to the **...\HolographicAcademy-Holograms-230-SpatialMapping\Starting** folder.</span></span>
* <span data-ttu-id="5778b-161">按一下 [ **天文館 unitypackage**]。</span><span class="sxs-lookup"><span data-stu-id="5778b-161">Click on **Planetarium.unitypackage**.</span></span>
* <span data-ttu-id="5778b-162">按一下 [開啟]。</span><span class="sxs-lookup"><span data-stu-id="5778b-162">Click **Open**.</span></span>
* <span data-ttu-id="5778b-163">隨即出現 [匯 **入 Unity 套件** ] 視窗，請按一下 [匯 **入** ] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="5778b-163">An **Import Unity Package** window should appear, click on the **Import** button.</span></span>
* <span data-ttu-id="5778b-164">等候 Unity 匯入完成此專案所需的所有資產。</span><span class="sxs-lookup"><span data-stu-id="5778b-164">Wait for Unity to import all of the assets that we will need to complete this project.</span></span>
* <span data-ttu-id="5778b-165">**在 [階層] 面板中**，刪除 **主要攝影機**。</span><span class="sxs-lookup"><span data-stu-id="5778b-165">In the **Hierarchy** panel, delete the **Main Camera**.</span></span>
* <span data-ttu-id="5778b-166">在 [ **專案** ] 面板的 [ **HoloToolkit-SpatialMapping-230\Utilities\Prefabs** ] 資料夾中，尋找 [ **主要攝影機** ] 物件。</span><span class="sxs-lookup"><span data-stu-id="5778b-166">In the **Project** panel, **HoloToolkit-SpatialMapping-230\Utilities\Prefabs** folder, find the **Main Camera** object.</span></span>
* <span data-ttu-id="5778b-167">將 **主要攝影機** 預製專案拖放到 [階層 **] 面板中** 。</span><span class="sxs-lookup"><span data-stu-id="5778b-167">Drag and drop the **Main Camera** prefab into the **Hierarchy** panel.</span></span>
* <span data-ttu-id="5778b-168">**在 [階層] 面板中**，刪除 **方向光源** 物件。</span><span class="sxs-lookup"><span data-stu-id="5778b-168">In the **Hierarchy** panel, delete the **Directional Light** object.</span></span>
* <span data-ttu-id="5778b-169">在 [ **專案** ] 面板的 [全像 **] 資料夾中，找** 出 **游標** 物件。</span><span class="sxs-lookup"><span data-stu-id="5778b-169">In the **Project** panel, **Holograms** folder, locate the **Cursor** object.</span></span>
* <span data-ttu-id="5778b-170">拖曳 & 將資料 **指標** 預製專案拖放到階層 **中。**</span><span class="sxs-lookup"><span data-stu-id="5778b-170">Drag & drop the **Cursor** prefab into the **Hierarchy**.</span></span>
* <span data-ttu-id="5778b-171">**在 [階層] 面板中**，選取 [資料 **指標**] 物件。</span><span class="sxs-lookup"><span data-stu-id="5778b-171">In the **Hierarchy** panel, select the **Cursor** object.</span></span>
* <span data-ttu-id="5778b-172">在 [偵測 **器** ] 面板中，按一下 [ **圖層** ] 下拉式清單，然後選取 [ **編輯圖層**]。</span><span class="sxs-lookup"><span data-stu-id="5778b-172">In the **Inspector** panel, click the **Layer** drop-down and select **Edit Layers...**.</span></span>
* <span data-ttu-id="5778b-173">將 **使用者第 31** 名命名為 "**SpatialMapping**"。</span><span class="sxs-lookup"><span data-stu-id="5778b-173">Name **User Layer 31** as "**SpatialMapping**".</span></span>
* <span data-ttu-id="5778b-174">儲存新場景： **File > 另存場景為**.。。</span><span class="sxs-lookup"><span data-stu-id="5778b-174">Save the new scene: **File > Save Scene As...**</span></span>
* <span data-ttu-id="5778b-175">按一下 [ **新增資料夾** ]，然後將資料夾命名為 **幕後**。</span><span class="sxs-lookup"><span data-stu-id="5778b-175">Click **New Folder** and name the folder **Scenes**.</span></span>
* <span data-ttu-id="5778b-176">將檔案命名為 "**天文館**"，並將它儲存在 **幕後** 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="5778b-176">Name the file "**Planetarium**" and save it in the **Scenes** folder.</span></span>

## <a name="chapter-1---scanning"></a><span data-ttu-id="5778b-177">第1章-掃描</span><span class="sxs-lookup"><span data-stu-id="5778b-177">Chapter 1 - Scanning</span></span>

>[!VIDEO https://www.youtube.com/embed/888oW51z_cE]

<span data-ttu-id="5778b-178">**目標**</span><span class="sxs-lookup"><span data-stu-id="5778b-178">**Objectives**</span></span>

* <span data-ttu-id="5778b-179">瞭解 SurfaceObserver 及其設定如何影響體驗和效能。</span><span class="sxs-lookup"><span data-stu-id="5778b-179">Learn about the SurfaceObserver and how its settings impact experience and performance.</span></span>
* <span data-ttu-id="5778b-180">建立房間掃描體驗來收集房間的網格。</span><span class="sxs-lookup"><span data-stu-id="5778b-180">Create a room scanning experience to collect the meshes of your room.</span></span>

<span data-ttu-id="5778b-181">**指示**</span><span class="sxs-lookup"><span data-stu-id="5778b-181">**Instructions**</span></span>

* <span data-ttu-id="5778b-182">在 **專案** 面板的 [ **HoloToolkit-SpatialMapping-230\SpatialMapping\Prefabs** ] 資料夾中，尋找 **SpatialMapping** 預製專案。</span><span class="sxs-lookup"><span data-stu-id="5778b-182">In the **Project** panel **HoloToolkit-SpatialMapping-230\SpatialMapping\Prefabs** folder, find the **SpatialMapping** prefab.</span></span>
* <span data-ttu-id="5778b-183">將 [ **SpatialMapping** ] 預製專案拖曳 & 放入 [階層 **] 面板中** 。</span><span class="sxs-lookup"><span data-stu-id="5778b-183">Drag & drop the **SpatialMapping** prefab into the **Hierarchy** panel.</span></span>

<span data-ttu-id="5778b-184">**組建和部署 (第1部)**</span><span class="sxs-lookup"><span data-stu-id="5778b-184">**Build and Deploy (part 1)**</span></span>

* <span data-ttu-id="5778b-185">在 Unity 中，選取 [ **File > Build Settings**]。</span><span class="sxs-lookup"><span data-stu-id="5778b-185">In Unity, select **File > Build Settings**.</span></span>
* <span data-ttu-id="5778b-186">按一下 [ **新增開啟的場景** ]，將 **天文館** 場景新增至組建。</span><span class="sxs-lookup"><span data-stu-id="5778b-186">Click **Add Open Scenes** to add the **Planetarium** scene to the build.</span></span>
* <span data-ttu-id="5778b-187">在 [**平臺**] 清單中選取 **通用 Windows 平臺**，然後按一下 [**切換平臺**]。</span><span class="sxs-lookup"><span data-stu-id="5778b-187">Select **Universal Windows Platform** in the **Platform** list and click **Switch Platform**.</span></span>
* <span data-ttu-id="5778b-188">將 **SDK** 設定為 **通用 10** ，並將 **UWP 組建類型** 設定為 **D3D**。</span><span class="sxs-lookup"><span data-stu-id="5778b-188">Set **SDK** to **Universal 10** and **UWP Build Type** to **D3D**.</span></span>
* <span data-ttu-id="5778b-189">檢查 **Unity c # 專案**。</span><span class="sxs-lookup"><span data-stu-id="5778b-189">Check **Unity C# Projects**.</span></span>
* <span data-ttu-id="5778b-190">按一下 [建置]。</span><span class="sxs-lookup"><span data-stu-id="5778b-190">Click **Build**.</span></span>
* <span data-ttu-id="5778b-191">建立名為 "App" 的 **新資料夾** 。</span><span class="sxs-lookup"><span data-stu-id="5778b-191">Create a **New Folder** named "App".</span></span>
* <span data-ttu-id="5778b-192">按一下 **應用程式** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="5778b-192">Single click the **App** folder.</span></span>
* <span data-ttu-id="5778b-193">按下 [ **選取資料夾** ] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="5778b-193">Press the **Select Folder** button.</span></span>
* <span data-ttu-id="5778b-194">當 Unity 完成建立時，將會出現檔案總管視窗。</span><span class="sxs-lookup"><span data-stu-id="5778b-194">When Unity is done building, a File Explorer window will appear.</span></span>
* <span data-ttu-id="5778b-195">按兩下 **應用程式** 資料夾以開啟它。</span><span class="sxs-lookup"><span data-stu-id="5778b-195">Double-click on the **App** folder to open it.</span></span>
* <span data-ttu-id="5778b-196">按兩下 [ **天文館** ]，在 Visual Studio 中載入專案。</span><span class="sxs-lookup"><span data-stu-id="5778b-196">Double-click on **Planetarium.sln** to load the project in Visual Studio.</span></span>
* <span data-ttu-id="5778b-197">在 Visual Studio 中，使用頂端工具列將設定變更為 [ **發行**]。</span><span class="sxs-lookup"><span data-stu-id="5778b-197">In Visual Studio, use the top toolbar to change the Configuration to **Release**.</span></span>
* <span data-ttu-id="5778b-198">將平臺變更為 **x86**。</span><span class="sxs-lookup"><span data-stu-id="5778b-198">Change the Platform to **x86**.</span></span>
* <span data-ttu-id="5778b-199">按一下 [本機電腦] 右邊的下拉箭號，然後選取 [ **遠端電腦**]。</span><span class="sxs-lookup"><span data-stu-id="5778b-199">Click on the drop-down arrow to the right of 'Local Machine', and select **Remote Machine**.</span></span>
* <span data-ttu-id="5778b-200">在 [位址] 欄位中輸入 [您裝置的 IP 位址](/hololens/hololens-network#identifying-the-ip-address-of-your-hololens-on-the-wi-fi-network) ，並將驗證模式變更為 **通用 (未加密的通訊協定)**。</span><span class="sxs-lookup"><span data-stu-id="5778b-200">Enter [your device's IP address](/hololens/hololens-network#identifying-the-ip-address-of-your-hololens-on-the-wi-fi-network) in the Address field and change Authentication Mode to **Universal (Unencrypted Protocol)**.</span></span>
* <span data-ttu-id="5778b-201">按一下 [ **Debug-> 啟動但不進行調試]，** 或按 **Ctrl + F5**。</span><span class="sxs-lookup"><span data-stu-id="5778b-201">Click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
* <span data-ttu-id="5778b-202">觀賞 Visual Studio 中的 [ **輸出** ] 面板，以取得組建和部署狀態。</span><span class="sxs-lookup"><span data-stu-id="5778b-202">Watch the **Output** panel in Visual Studio for build and deploy status.</span></span>
* <span data-ttu-id="5778b-203">當您的應用程式部署完成後，請四處移動空間。</span><span class="sxs-lookup"><span data-stu-id="5778b-203">Once your app has deployed, walk around the room.</span></span> <span data-ttu-id="5778b-204">您將會看到黑色和白色線框網格所涵蓋的周圍表面。</span><span class="sxs-lookup"><span data-stu-id="5778b-204">You will see the surrounding surfaces covered by black and white wireframe meshes.</span></span>
* <span data-ttu-id="5778b-205">掃描您的環境。</span><span class="sxs-lookup"><span data-stu-id="5778b-205">Scan your surroundings.</span></span> <span data-ttu-id="5778b-206">請務必查看牆、上限和樓層。</span><span class="sxs-lookup"><span data-stu-id="5778b-206">Be sure to look at walls, ceilings, and floors.</span></span>

<span data-ttu-id="5778b-207">**組建和部署 (第2部分)**</span><span class="sxs-lookup"><span data-stu-id="5778b-207">**Build and Deploy (part 2)**</span></span>

<span data-ttu-id="5778b-208">現在讓我們來探索空間對應會如何影響效能。</span><span class="sxs-lookup"><span data-stu-id="5778b-208">Now let's explore how Spatial Mapping can affect performance.</span></span>

* <span data-ttu-id="5778b-209">在 Unity 中，選取 [ **Window > Profiler]**。</span><span class="sxs-lookup"><span data-stu-id="5778b-209">In Unity, select **Window > Profiler**.</span></span>
* <span data-ttu-id="5778b-210">按一下 [ **新增 Profiler > GPU**]。</span><span class="sxs-lookup"><span data-stu-id="5778b-210">Click **Add Profiler > GPU**.</span></span>
* <span data-ttu-id="5778b-211">按一下 [ **Active Profiler <Enter IP> >**]。</span><span class="sxs-lookup"><span data-stu-id="5778b-211">Click **Active Profiler > <Enter IP>**.</span></span>
* <span data-ttu-id="5778b-212">輸入 HoloLens 的 **IP 位址** 。</span><span class="sxs-lookup"><span data-stu-id="5778b-212">Enter the **IP address** of your HoloLens.</span></span>
* <span data-ttu-id="5778b-213">按一下 [連線]。</span><span class="sxs-lookup"><span data-stu-id="5778b-213">Click **Connect**.</span></span>
* <span data-ttu-id="5778b-214">觀察 GPU 呈現框架所需的毫秒數。</span><span class="sxs-lookup"><span data-stu-id="5778b-214">Observe the number of milliseconds it takes for the GPU to render a frame.</span></span>
* <span data-ttu-id="5778b-215">停止應用程式在裝置上執行。</span><span class="sxs-lookup"><span data-stu-id="5778b-215">Stop the application from running on the device.</span></span>
* <span data-ttu-id="5778b-216">返回 Visual Studio 並開啟 **SpatialMappingObserver.cs**。</span><span class="sxs-lookup"><span data-stu-id="5778b-216">Return to Visual Studio and open **SpatialMappingObserver.cs**.</span></span> <span data-ttu-id="5778b-217">您會在 Assembly-CSharp (通用 Windows) 專案的 HoloToolkit\SpatialMapping 資料夾中找到它。</span><span class="sxs-lookup"><span data-stu-id="5778b-217">You will find it in the HoloToolkit\SpatialMapping folder of the Assembly-CSharp (Universal Windows) project.</span></span>
* <span data-ttu-id="5778b-218">尋找 **喚醒的 ( # B1** 函數，並加入下列程式程式碼： **TrianglesPerCubicMeter = 1200;**</span><span class="sxs-lookup"><span data-stu-id="5778b-218">Find the **Awake()** function, and add the following line of code: **TrianglesPerCubicMeter = 1200;**</span></span>
* <span data-ttu-id="5778b-219">將專案重新部署至您的裝置，然後 **重新連接** 分析工具。</span><span class="sxs-lookup"><span data-stu-id="5778b-219">Re-deploy the project to your device, and then **reconnect the profiler**.</span></span> <span data-ttu-id="5778b-220">觀察轉譯畫面格的毫秒數變更。</span><span class="sxs-lookup"><span data-stu-id="5778b-220">Observe the change in the number of milliseconds to render a frame.</span></span>
* <span data-ttu-id="5778b-221">停止應用程式在裝置上執行。</span><span class="sxs-lookup"><span data-stu-id="5778b-221">Stop the application from running on the device.</span></span>

<span data-ttu-id="5778b-222">**在 Unity 中儲存和載入**</span><span class="sxs-lookup"><span data-stu-id="5778b-222">**Save and load in Unity**</span></span>

<span data-ttu-id="5778b-223">最後，讓我們來儲存房間網格並將它載入 Unity 中。</span><span class="sxs-lookup"><span data-stu-id="5778b-223">Finally, let's save our room mesh and load it into Unity.</span></span>

* <span data-ttu-id="5778b-224">返回 Visual Studio，並移除您在上一節中于 **喚醒 ( # B1** 函數中新增的 **TrianglesPerCubicMeter** 行。</span><span class="sxs-lookup"><span data-stu-id="5778b-224">Return to Visual Studio and remove the **TrianglesPerCubicMeter** line that you added in the **Awake()** function during the previous section.</span></span>
* <span data-ttu-id="5778b-225">將專案重新部署至您的裝置。</span><span class="sxs-lookup"><span data-stu-id="5778b-225">Redeploy the project to your device.</span></span> <span data-ttu-id="5778b-226">我們現在應該以每個三立方計量的 **500** 三角形來執行。</span><span class="sxs-lookup"><span data-stu-id="5778b-226">We should now be running with **500** triangles per cubic meter.</span></span>
* <span data-ttu-id="5778b-227">開啟瀏覽器並輸入您的 HoloLens IPAddress，以流覽至 **Windows 裝置入口網站**。</span><span class="sxs-lookup"><span data-stu-id="5778b-227">Open a browser and enter in your HoloLens IPAddress to navigate to the **Windows Device Portal**.</span></span>
* <span data-ttu-id="5778b-228">選取左面板中的 [ **3D 視圖** ] 選項。</span><span class="sxs-lookup"><span data-stu-id="5778b-228">Select the **3D View** option in the left panel.</span></span>
* <span data-ttu-id="5778b-229">在 [ **表面重建** ] 下，選取 [ **更新** ] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="5778b-229">Under **Surface reconstruction** select the **Update** button.</span></span>
* <span data-ttu-id="5778b-230">請注意，您在 HoloLens 上掃描的區域會出現在 [顯示] 視窗中。</span><span class="sxs-lookup"><span data-stu-id="5778b-230">Watch as the areas that you have scanned on your HoloLens appear in the display window.</span></span>
* <span data-ttu-id="5778b-231">若要儲存您的房間掃描，請按 [ **儲存** ] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="5778b-231">To save your room scan, press the **Save** button.</span></span>
* <span data-ttu-id="5778b-232">開啟您的 [**下載**] 資料夾，以尋找已儲存的房間模型 **SRMesh。**</span><span class="sxs-lookup"><span data-stu-id="5778b-232">Open your **Downloads** folder to find the saved room model **SRMesh.obj**.</span></span>
* <span data-ttu-id="5778b-233">將 **SRMesh** 複製到 Unity 專案的 [ **資產** ] 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="5778b-233">Copy **SRMesh.obj** to the **Assets** folder of your Unity project.</span></span>
* <span data-ttu-id="5778b-234">在 Unity 中，選取 **階層面板中的 [** **SpatialMapping** ] 物件。</span><span class="sxs-lookup"><span data-stu-id="5778b-234">In Unity, select the **SpatialMapping** object in the **Hierarchy** panel.</span></span>
* <span data-ttu-id="5778b-235">找出 **物件介面觀察器 (腳本)** 元件。</span><span class="sxs-lookup"><span data-stu-id="5778b-235">Locate the **Object Surface Observer (Script)** component.</span></span>
* <span data-ttu-id="5778b-236">按一下 [ **房間模型** ] 屬性右邊的圓形。</span><span class="sxs-lookup"><span data-stu-id="5778b-236">Click the circle to the right of the **Room Model** property.</span></span>
* <span data-ttu-id="5778b-237">尋找並選取 [ **SRMesh** ] 物件，然後關閉視窗。</span><span class="sxs-lookup"><span data-stu-id="5778b-237">Find and select the **SRMesh** object and then close the window.</span></span>
* <span data-ttu-id="5778b-238">確認 [**檢查**] 面板中的 [**房間模型**] 屬性現在已設定為 [ **SRMesh**]。</span><span class="sxs-lookup"><span data-stu-id="5778b-238">Verify that the **Room Model** property in the **Inspector** panel is now set to **SRMesh**.</span></span>
* <span data-ttu-id="5778b-239">按下 [ **播放** ] 按鈕以進入 Unity 的預覽模式。</span><span class="sxs-lookup"><span data-stu-id="5778b-239">Press the **Play** button to enter Unity's preview mode.</span></span>
* <span data-ttu-id="5778b-240">SpatialMapping 元件會從已儲存的房間模型載入網格，讓您可以在 Unity 中使用它們。</span><span class="sxs-lookup"><span data-stu-id="5778b-240">The SpatialMapping component will load the meshes from the saved room model so you can use them in Unity.</span></span>
* <span data-ttu-id="5778b-241">切換至 **場景** 視圖，以查看以線框著色器顯示的所有房間模型。</span><span class="sxs-lookup"><span data-stu-id="5778b-241">Switch to **Scene** view to see all of your room model displayed with the wireframe shader.</span></span>
* <span data-ttu-id="5778b-242">再按一次 [ **播放** ] 按鈕以結束預覽模式。</span><span class="sxs-lookup"><span data-stu-id="5778b-242">Press the **Play** button again to exit preview mode.</span></span>

<span data-ttu-id="5778b-243">**注意：** 下次您在 Unity 中進入預覽模式時，預設會載入儲存的房間網格。</span><span class="sxs-lookup"><span data-stu-id="5778b-243">**NOTE:** The next time that you enter preview mode in Unity, it will load the saved room mesh by default.</span></span>

## <a name="chapter-2---visualization"></a><span data-ttu-id="5778b-244">第2章-視覺效果</span><span class="sxs-lookup"><span data-stu-id="5778b-244">Chapter 2 - Visualization</span></span>

>[!VIDEO https://www.youtube.com/embed/RnkvXl-aXD4]

<span data-ttu-id="5778b-245">**目標**</span><span class="sxs-lookup"><span data-stu-id="5778b-245">**Objectives**</span></span>

* <span data-ttu-id="5778b-246">瞭解著色器的基本概念。</span><span class="sxs-lookup"><span data-stu-id="5778b-246">Learn the basics of shaders.</span></span>
* <span data-ttu-id="5778b-247">視覺化您的環境。</span><span class="sxs-lookup"><span data-stu-id="5778b-247">Visualize your surroundings.</span></span>

<span data-ttu-id="5778b-248">**指示**</span><span class="sxs-lookup"><span data-stu-id="5778b-248">**Instructions**</span></span>

* <span data-ttu-id="5778b-249">在 Unity 的 **階層面板中** ，選取 [ **SpatialMapping** ] 物件。</span><span class="sxs-lookup"><span data-stu-id="5778b-249">In Unity's **Hierarchy** panel, select the **SpatialMapping** object.</span></span>
* <span data-ttu-id="5778b-250">在 [偵測 **器** ] 面板中，尋找 **(腳本) 元件的空間對應管理員** 。</span><span class="sxs-lookup"><span data-stu-id="5778b-250">In the **Inspector** panel, find the **Spatial Mapping Manager (Script)** component.</span></span>
* <span data-ttu-id="5778b-251">按一下 [ **Surface 材質** ] 屬性右邊的圓形。</span><span class="sxs-lookup"><span data-stu-id="5778b-251">Click the circle to the right of the **Surface Material** property.</span></span>
* <span data-ttu-id="5778b-252">尋找並選取 **BlueLinesOnWalls** 材質，然後關閉視窗。</span><span class="sxs-lookup"><span data-stu-id="5778b-252">Find and select the **BlueLinesOnWalls** material and close the window.</span></span>
* <span data-ttu-id="5778b-253">在 [ **專案** 面板 **著色** 器] 資料夾中，按兩下 [ **BlueLinesOnWalls** ] 以開啟 Visual Studio 中的著色器。</span><span class="sxs-lookup"><span data-stu-id="5778b-253">In the **Project** panel **Shaders** folder, double-click on **BlueLinesOnWalls** to open the shader in Visual Studio.</span></span>
* <span data-ttu-id="5778b-254">這是一個簡單的圖元 (頂點到片段) 著色器，它會完成下列工作：</span><span class="sxs-lookup"><span data-stu-id="5778b-254">This is a simple pixel (vertex to fragment) shader, which accomplishes the following tasks:</span></span>
    1. <span data-ttu-id="5778b-255">將頂點的位置轉換成世界空間。</span><span class="sxs-lookup"><span data-stu-id="5778b-255">Converts a vertex's location to world space.</span></span>
    2. <span data-ttu-id="5778b-256">檢查頂點的一般，以判斷圖元是否為垂直。</span><span class="sxs-lookup"><span data-stu-id="5778b-256">Checks the vertex's normal to determine if a pixel is vertical.</span></span>
    3. <span data-ttu-id="5778b-257">設定用來呈現的圖元色彩。</span><span class="sxs-lookup"><span data-stu-id="5778b-257">Sets the color of the pixel for rendering.</span></span>

<span data-ttu-id="5778b-258">**組建和部署**</span><span class="sxs-lookup"><span data-stu-id="5778b-258">**Build and Deploy**</span></span>

* <span data-ttu-id="5778b-259">返回 Unity，然後按下 [ **播放** ] 進入預覽模式。</span><span class="sxs-lookup"><span data-stu-id="5778b-259">Return to Unity and press **Play** to enter preview mode.</span></span>
* <span data-ttu-id="5778b-260">系統會在房間網格的所有垂直表面上轉譯藍線 (這會從已儲存的掃描資料) 自動載入。</span><span class="sxs-lookup"><span data-stu-id="5778b-260">Blue lines will be rendered on all vertical surfaces of the room mesh (which automatically loaded from our saved scanning data).</span></span>
* <span data-ttu-id="5778b-261">切換至 [ **場景** ] 索引標籤，以調整您的房間視圖，並查看整個房間網格在 Unity 中的顯示方式。</span><span class="sxs-lookup"><span data-stu-id="5778b-261">Switch to the **Scene** tab to adjust your view of the room and see how the entire room mesh appears in Unity.</span></span>
* <span data-ttu-id="5778b-262">在 [ **專案** ] 面板中，尋找 [ **材質** ] 資料夾，並選取 **BlueLinesOnWalls** 材質。</span><span class="sxs-lookup"><span data-stu-id="5778b-262">In the **Project** panel, find the **Materials** folder and select the **BlueLinesOnWalls** material.</span></span>
* <span data-ttu-id="5778b-263">修改某些屬性，並查看如何在 Unity 編輯器中顯示變更。</span><span class="sxs-lookup"><span data-stu-id="5778b-263">Modify some properties and see how the changes appear in the Unity editor.</span></span>
    * <span data-ttu-id="5778b-264">在 [偵測 **器** ] 面板中，調整 **LineScale** 值，讓線條顯示為較粗或更細。</span><span class="sxs-lookup"><span data-stu-id="5778b-264">In the **Inspector** panel, adjust the **LineScale** value to make the lines appear thicker or thinner.</span></span>
    * <span data-ttu-id="5778b-265">在 [偵測 **器** ] 面板中，調整 **LinesPerMeter** 值以變更每個牆上出現的行數。</span><span class="sxs-lookup"><span data-stu-id="5778b-265">In the **Inspector** panel, adjust the **LinesPerMeter** value to change how many lines appear on each wall.</span></span>
* <span data-ttu-id="5778b-266">按一下 [ **播放** ] 以結束預覽模式。</span><span class="sxs-lookup"><span data-stu-id="5778b-266">Click **Play** again to exit preview mode.</span></span>
* <span data-ttu-id="5778b-267">建立並部署至 HoloLens，並觀察著色器轉譯如何顯示在實際表面上。</span><span class="sxs-lookup"><span data-stu-id="5778b-267">Build and deploy to the HoloLens and observe how the shader rendering appears on real surfaces.</span></span>

<span data-ttu-id="5778b-268">Unity 有很大的預覽材質，但最好是在裝置中簽出轉譯的好主意。</span><span class="sxs-lookup"><span data-stu-id="5778b-268">Unity does a great job of previewing materials, but it's always a good idea to check-out rendering in the device.</span></span>

## <a name="chapter-3---processing"></a><span data-ttu-id="5778b-269">第3章-處理</span><span class="sxs-lookup"><span data-stu-id="5778b-269">Chapter 3 - Processing</span></span>

>[!VIDEO https://www.youtube.com/embed/kaUKiNiDxwY]

<span data-ttu-id="5778b-270">**目標**</span><span class="sxs-lookup"><span data-stu-id="5778b-270">**Objectives**</span></span>

* <span data-ttu-id="5778b-271">瞭解處理空間對應資料以在應用程式中使用的技術。</span><span class="sxs-lookup"><span data-stu-id="5778b-271">Learn techniques to process spatial mapping data for use in your application.</span></span>
* <span data-ttu-id="5778b-272">分析空間對應資料以尋找平面和移除三角形。</span><span class="sxs-lookup"><span data-stu-id="5778b-272">Analyze spatial mapping data to find planes and remove triangles.</span></span>
* <span data-ttu-id="5778b-273">使用平面來放置全息圖。</span><span class="sxs-lookup"><span data-stu-id="5778b-273">Use planes for hologram placement.</span></span>

<span data-ttu-id="5778b-274">**指示**</span><span class="sxs-lookup"><span data-stu-id="5778b-274">**Instructions**</span></span>

* <span data-ttu-id="5778b-275">在 Unity 的 [ **專案** ] **面板中，** [全像] 資料夾中，尋找 **SpatialProcessing** 物件。</span><span class="sxs-lookup"><span data-stu-id="5778b-275">In Unity's **Project** panel, **Holograms** folder, find the **SpatialProcessing** object.</span></span>
* <span data-ttu-id="5778b-276">將 **SpatialProcessing** 物件拖曳 & 放入 [階層 **] 面板中** 。</span><span class="sxs-lookup"><span data-stu-id="5778b-276">Drag & drop the **SpatialProcessing** object into the **Hierarchy** panel.</span></span>

<span data-ttu-id="5778b-277">SpatialProcessing 預製專案包含處理空間對應資料的元件。</span><span class="sxs-lookup"><span data-stu-id="5778b-277">The SpatialProcessing prefab includes components for processing the spatial mapping data.</span></span> <span data-ttu-id="5778b-278">**SurfaceMeshesToPlanes.cs** 會根據空間對應資料尋找並產生平面。</span><span class="sxs-lookup"><span data-stu-id="5778b-278">**SurfaceMeshesToPlanes.cs** will find and generate planes based on the spatial mapping data.</span></span> <span data-ttu-id="5778b-279">我們將在應用程式中使用平面來代表牆壁、樓層和上限。</span><span class="sxs-lookup"><span data-stu-id="5778b-279">We will use planes in our application to represent walls, floors and ceilings.</span></span> <span data-ttu-id="5778b-280">此預製專案也包含可從空間對應網格中移除頂點的 **RemoveSurfaceVertices.cs** 。</span><span class="sxs-lookup"><span data-stu-id="5778b-280">This prefab also includes **RemoveSurfaceVertices.cs** which can remove vertices from the spatial mapping mesh.</span></span> <span data-ttu-id="5778b-281">這可以用來在網格中建立洞，或移除不再需要的多餘三角形 (因為可以改用平面來取代) 。</span><span class="sxs-lookup"><span data-stu-id="5778b-281">This can be used to create holes in the mesh, or to remove excess triangles that are no longer needed (because planes can be used instead).</span></span>

* <span data-ttu-id="5778b-282">在 Unity 的 [ **專案** ] **面板中，** [全像] 資料夾中，尋找 **SpaceCollection** 物件。</span><span class="sxs-lookup"><span data-stu-id="5778b-282">In Unity's **Project** panel, **Holograms** folder, find the **SpaceCollection** object.</span></span>
* <span data-ttu-id="5778b-283">將 **SpaceCollection** 物件拖放 **到 [階層** ] 面板中。</span><span class="sxs-lookup"><span data-stu-id="5778b-283">Drag and drop the **SpaceCollection** object into the **Hierarchy** panel.</span></span>
* <span data-ttu-id="5778b-284">**在 [階層] 面板中**，選取 [ **SpatialProcessing** ] 物件。</span><span class="sxs-lookup"><span data-stu-id="5778b-284">In the **Hierarchy** panel, select the **SpatialProcessing** object.</span></span>
* <span data-ttu-id="5778b-285">在 [偵測 **器** ] 面板中，尋找 [ **播放空間管理員] (腳本)** 元件。</span><span class="sxs-lookup"><span data-stu-id="5778b-285">In the **Inspector** panel, find the **Play Space Manager (Script)** component.</span></span>
* <span data-ttu-id="5778b-286">按兩下 [ **PlaySpaceManager.cs** ]，在 Visual Studio 中開啟。</span><span class="sxs-lookup"><span data-stu-id="5778b-286">Double-click on **PlaySpaceManager.cs** to open it in Visual Studio.</span></span>

<span data-ttu-id="5778b-287">PlaySpaceManager.cs 包含應用程式特定的程式碼。</span><span class="sxs-lookup"><span data-stu-id="5778b-287">PlaySpaceManager.cs contains application-specific code.</span></span> <span data-ttu-id="5778b-288">我們將在此腳本中新增功能，以啟用下列行為：</span><span class="sxs-lookup"><span data-stu-id="5778b-288">We will add functionality to this script to enable the following behavior:</span></span>

1. <span data-ttu-id="5778b-289">超過掃描時間限制 (10 秒) 之後，停止收集空間對應資料。</span><span class="sxs-lookup"><span data-stu-id="5778b-289">Stop collecting spatial mapping data after we exceed the scanning time limit (10 seconds).</span></span>
2. <span data-ttu-id="5778b-290">處理空間對應資料：</span><span class="sxs-lookup"><span data-stu-id="5778b-290">Process the spatial mapping data:</span></span>
    1. <span data-ttu-id="5778b-291">使用 SurfaceMeshesToPlanes 來建立更簡單的世界表示，作為平面 (牆壁、樓層、上限等) 。</span><span class="sxs-lookup"><span data-stu-id="5778b-291">Use SurfaceMeshesToPlanes to create a simpler representation of the world as planes (walls, floors, ceilings, etc).</span></span>
    2. <span data-ttu-id="5778b-292">使用 RemoveSurfaceVertices 來移除落在平面邊界內的表面三角形。</span><span class="sxs-lookup"><span data-stu-id="5778b-292">Use RemoveSurfaceVertices to remove surface triangles that fall within plane boundaries.</span></span>
3. <span data-ttu-id="5778b-293">產生世界各地的全像投影集合，並將它們放在靠近使用者的牆和地面平面上。</span><span class="sxs-lookup"><span data-stu-id="5778b-293">Generate a collection of holograms in the world and place them on wall and floor planes near the user.</span></span>

<span data-ttu-id="5778b-294">完成標示于 PlaySpaceManager.cs 中的程式碼撰寫練習，或將腳本取代為以下的完成解決方案：</span><span class="sxs-lookup"><span data-stu-id="5778b-294">Complete the coding exercises marked in PlaySpaceManager.cs, or replace the script with the finished solution from below:</span></span>

```cs
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.Windows.Speech;
using Academy.HoloToolkit.Unity;

/// <summary>
/// The SurfaceManager class allows applications to scan the environment for a specified amount of time 
/// and then process the Spatial Mapping Mesh (find planes, remove vertices) after that time has expired.
/// </summary>
public class PlaySpaceManager : Singleton<PlaySpaceManager>
{
    [Tooltip("When checked, the SurfaceObserver will stop running after a specified amount of time.")]
    public bool limitScanningByTime = true;

    [Tooltip("How much time (in seconds) that the SurfaceObserver will run after being started; used when 'Limit Scanning By Time' is checked.")]
    public float scanTime = 30.0f;

    [Tooltip("Material to use when rendering Spatial Mapping meshes while the observer is running.")]
    public Material defaultMaterial;

    [Tooltip("Optional Material to use when rendering Spatial Mapping meshes after the observer has been stopped.")]
    public Material secondaryMaterial;

    [Tooltip("Minimum number of floor planes required in order to exit scanning/processing mode.")]
    public uint minimumFloors = 1;

    [Tooltip("Minimum number of wall planes required in order to exit scanning/processing mode.")]
    public uint minimumWalls = 1;

    /// <summary>
    /// Indicates if processing of the surface meshes is complete.
    /// </summary>
    private bool meshesProcessed = false;

    /// <summary>
    /// GameObject initialization.
    /// </summary>
    private void Start()
    {
        // Update surfaceObserver and storedMeshes to use the same material during scanning.
        SpatialMappingManager.Instance.SetSurfaceMaterial(defaultMaterial);

        // Register for the MakePlanesComplete event.
        SurfaceMeshesToPlanes.Instance.MakePlanesComplete += SurfaceMeshesToPlanes_MakePlanesComplete;
    }

    /// <summary>
    /// Called once per frame.
    /// </summary>
    private void Update()
    {
        // Check to see if the spatial mapping data has been processed
        // and if we are limiting how much time the user can spend scanning.
        if (!meshesProcessed && limitScanningByTime)
        {
            // If we have not processed the spatial mapping data
            // and scanning time is limited...

            // Check to see if enough scanning time has passed
            // since starting the observer.
            if (limitScanningByTime && ((Time.time - SpatialMappingManager.Instance.StartTime) < scanTime))
            {
                // If we have a limited scanning time, then we should wait until
                // enough time has passed before processing the mesh.
            }
            else
            {
                // The user should be done scanning their environment,
                // so start processing the spatial mapping data...

                /* TODO: 3.a DEVELOPER CODING EXERCISE 3.a */

                // 3.a: Check if IsObserverRunning() is true on the
                // SpatialMappingManager.Instance.
                if(SpatialMappingManager.Instance.IsObserverRunning())
                {
                    // 3.a: If running, Stop the observer by calling
                    // StopObserver() on the SpatialMappingManager.Instance.
                    SpatialMappingManager.Instance.StopObserver();
                }

                // 3.a: Call CreatePlanes() to generate planes.
                CreatePlanes();

                // 3.a: Set meshesProcessed to true.
                meshesProcessed = true;
            }
        }
    }

    /// <summary>
    /// Handler for the SurfaceMeshesToPlanes MakePlanesComplete event.
    /// </summary>
    /// <param name="source">Source of the event.</param>
    /// <param name="args">Args for the event.</param>
    private void SurfaceMeshesToPlanes_MakePlanesComplete(object source, System.EventArgs args)
    {
        /* TODO: 3.a DEVELOPER CODING EXERCISE 3.a */

        // Collection of floor and table planes that we can use to set horizontal items on.
        List<GameObject> horizontal = new List<GameObject>();

        // Collection of wall planes that we can use to set vertical items on.
        List<GameObject> vertical = new List<GameObject>();

        // 3.a: Get all floor and table planes by calling
        // SurfaceMeshesToPlanes.Instance.GetActivePlanes().
        // Assign the result to the 'horizontal' list.
        horizontal = SurfaceMeshesToPlanes.Instance.GetActivePlanes(PlaneTypes.Table | PlaneTypes.Floor);

        // 3.a: Get all wall planes by calling
        // SurfaceMeshesToPlanes.Instance.GetActivePlanes().
        // Assign the result to the 'vertical' list.
        vertical = SurfaceMeshesToPlanes.Instance.GetActivePlanes(PlaneTypes.Wall);

        // Check to see if we have enough horizontal planes (minimumFloors)
        // and vertical planes (minimumWalls), to set holograms on in the world.
        if (horizontal.Count >= minimumFloors && vertical.Count >= minimumWalls)
        {
            // We have enough floors and walls to place our holograms on...

            // 3.a: Let's reduce our triangle count by removing triangles
            // from SpatialMapping meshes that intersect with our active planes.
            // Call RemoveVertices().
            // Pass in all activePlanes found by SurfaceMeshesToPlanes.Instance.
            RemoveVertices(SurfaceMeshesToPlanes.Instance.ActivePlanes);

            // 3.a: We can indicate to the user that scanning is over by
            // changing the material applied to the Spatial Mapping meshes.
            // Call SpatialMappingManager.Instance.SetSurfaceMaterial().
            // Pass in the secondaryMaterial.
            SpatialMappingManager.Instance.SetSurfaceMaterial(secondaryMaterial);

            // 3.a: We are all done processing the mesh, so we can now
            // initialize a collection of Placeable holograms in the world
            // and use horizontal/vertical planes to set their starting positions.
            // Call SpaceCollectionManager.Instance.GenerateItemsInWorld().
            // Pass in the lists of horizontal and vertical planes that we found earlier.
            SpaceCollectionManager.Instance.GenerateItemsInWorld(horizontal, vertical);
        }
        else
        {
            // We do not have enough floors/walls to place our holograms on...

            // 3.a: Re-enter scanning mode so the user can find more surfaces by
            // calling StartObserver() on the SpatialMappingManager.Instance.
            SpatialMappingManager.Instance.StartObserver();

            // 3.a: Re-process spatial data after scanning completes by
            // re-setting meshesProcessed to false.
            meshesProcessed = false;
        }
    }

    /// <summary>
    /// Creates planes from the spatial mapping surfaces.
    /// </summary>
    private void CreatePlanes()
    {
        // Generate planes based on the spatial map.
        SurfaceMeshesToPlanes surfaceToPlanes = SurfaceMeshesToPlanes.Instance;
        if (surfaceToPlanes != null && surfaceToPlanes.enabled)
        {
            surfaceToPlanes.MakePlanes();
        }
    }

    /// <summary>
    /// Removes triangles from the spatial mapping surfaces.
    /// </summary>
    /// <param name="boundingObjects"></param>
    private void RemoveVertices(IEnumerable<GameObject> boundingObjects)
    {
        RemoveSurfaceVertices removeVerts = RemoveSurfaceVertices.Instance;
        if (removeVerts != null && removeVerts.enabled)
        {
            removeVerts.RemoveSurfaceVerticesWithinBounds(boundingObjects);
        }
    }

    /// <summary>
    /// Called when the GameObject is unloaded.
    /// </summary>
    private void OnDestroy()
    {
        if (SurfaceMeshesToPlanes.Instance != null)
        {
            SurfaceMeshesToPlanes.Instance.MakePlanesComplete -= SurfaceMeshesToPlanes_MakePlanesComplete;
        }
    }
}
```

<span data-ttu-id="5778b-295">**組建和部署**</span><span class="sxs-lookup"><span data-stu-id="5778b-295">**Build and Deploy**</span></span>

* <span data-ttu-id="5778b-296">部署到 HoloLens 之前，請按 Unity 中的 [ **播放** ] 按鈕進入播放模式。</span><span class="sxs-lookup"><span data-stu-id="5778b-296">Before deploying to the HoloLens, press the **Play** button in Unity to enter play mode.</span></span>
* <span data-ttu-id="5778b-297">從檔案載入空間網格之後，請等候10秒鐘，然後在空間對應網格上開始處理。</span><span class="sxs-lookup"><span data-stu-id="5778b-297">After the room mesh is loaded from file, wait for 10 seconds before processing starts on the spatial mapping mesh.</span></span>
* <span data-ttu-id="5778b-298">當處理完成時，平面會顯示為代表樓層、牆壁、上限等等。</span><span class="sxs-lookup"><span data-stu-id="5778b-298">When processing is complete, planes will appear to represent the floor, walls, ceiling, etc.</span></span>
* <span data-ttu-id="5778b-299">找到所有的平面之後，您應該會看到日光系統出現在相機附近的桌子上。</span><span class="sxs-lookup"><span data-stu-id="5778b-299">After all of the planes have been found, you should see a solar system appear on a table of floor near the camera.</span></span>
* <span data-ttu-id="5778b-300">兩個海報也應該出現在相機附近的牆上。</span><span class="sxs-lookup"><span data-stu-id="5778b-300">Two posters should appear on walls near the camera too.</span></span> <span data-ttu-id="5778b-301">如果您無法在 **遊戲** 模式中看到，請切換至 [**場景**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="5778b-301">Switch to the **Scene** tab if you cannot see them in **Game** mode.</span></span>
* <span data-ttu-id="5778b-302">再按一次 [ **播放** ] 按鈕以結束播放模式。</span><span class="sxs-lookup"><span data-stu-id="5778b-302">Press the **Play** button again to exit play mode.</span></span>
* <span data-ttu-id="5778b-303">照常建立並部署到 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="5778b-303">Build and deploy to the HoloLens, as usual.</span></span>
* <span data-ttu-id="5778b-304">等候空間對應資料的掃描和處理完成。</span><span class="sxs-lookup"><span data-stu-id="5778b-304">Wait for scanning and processing of the spatial mapping data to complete.</span></span>
* <span data-ttu-id="5778b-305">一旦您看到了飛機，請試著找出您世界中的日光系統和海報。</span><span class="sxs-lookup"><span data-stu-id="5778b-305">Once you see planes, try to find the solar system and posters in your world.</span></span>

## <a name="chapter-4---placement"></a><span data-ttu-id="5778b-306">第4章-放置</span><span class="sxs-lookup"><span data-stu-id="5778b-306">Chapter 4 - Placement</span></span>

>[!VIDEO https://www.youtube.com/embed/Srhtpid1uZc]

<span data-ttu-id="5778b-307">**目標**</span><span class="sxs-lookup"><span data-stu-id="5778b-307">**Objectives**</span></span>

* <span data-ttu-id="5778b-308">判斷是否要在表面上容納全像影像。</span><span class="sxs-lookup"><span data-stu-id="5778b-308">Determine if a hologram will fit on a surface.</span></span>
* <span data-ttu-id="5778b-309">當您的影像可在表面上無法容納時，為使用者提供意見反應。</span><span class="sxs-lookup"><span data-stu-id="5778b-309">Provide feedback to the user when a hologram can/cannot fit on a surface.</span></span>

<span data-ttu-id="5778b-310">**指示**</span><span class="sxs-lookup"><span data-stu-id="5778b-310">**Instructions**</span></span>

* <span data-ttu-id="5778b-311">在 Unity 的 **階層面板中** ，選取 [ **SpatialProcessing** ] 物件。</span><span class="sxs-lookup"><span data-stu-id="5778b-311">In Unity's **Hierarchy** panel, select the **SpatialProcessing** object.</span></span>
* <span data-ttu-id="5778b-312">在 [偵測 **器** ] 面板中，尋找 **平面網格以 (腳本)** 元件。</span><span class="sxs-lookup"><span data-stu-id="5778b-312">In the **Inspector** panel, find the **Surface Meshes To Planes (Script)** component.</span></span>
* <span data-ttu-id="5778b-313">將 [ **繪製平面** ] 屬性變更為 [ **Nothing** ] 以清除選取專案。</span><span class="sxs-lookup"><span data-stu-id="5778b-313">Change the **Draw Planes** property to **Nothing** to clear the selection.</span></span>
* <span data-ttu-id="5778b-314">將 **Draw 平面** 屬性變更為 **牆**，如此就只會轉譯牆壁平面。</span><span class="sxs-lookup"><span data-stu-id="5778b-314">Change the **Draw Planes** property to **Wall**, so that only wall planes will be rendered.</span></span>
* <span data-ttu-id="5778b-315">在 [ **專案** ] 面板的 [ **腳本** ] 資料夾中，按兩下 [ **Placeable.cs** ]，在 Visual Studio 中開啟。</span><span class="sxs-lookup"><span data-stu-id="5778b-315">In the **Project** panel, **Scripts** folder, double-click on **Placeable.cs** to open it in Visual Studio.</span></span>

<span data-ttu-id="5778b-316">可 **放置** 的腳本已附加至在完成平面尋找之後所建立的海報和投影方塊。</span><span class="sxs-lookup"><span data-stu-id="5778b-316">The **Placeable** script is already attached to the posters and projection box that are created after plane finding completes.</span></span> <span data-ttu-id="5778b-317">我們只需要取消批註一些程式碼，這個腳本就能達成下列目標：</span><span class="sxs-lookup"><span data-stu-id="5778b-317">All we need to do is uncomment some code, and this script will achieve the following:</span></span>

1. <span data-ttu-id="5778b-318">從周框 cube 的中央和四個角落 raycasting，判斷是否要在表面上容納全像影像。</span><span class="sxs-lookup"><span data-stu-id="5778b-318">Determine if a hologram will fit on a surface by raycasting from the center and four corners of the bounding cube.</span></span>
2. <span data-ttu-id="5778b-319">檢查 surface normal，判斷是否有足夠的空間可讓全像影像排清。</span><span class="sxs-lookup"><span data-stu-id="5778b-319">Check the surface normal to determine if it is smooth enough for the hologram to sit flush on.</span></span>
3. <span data-ttu-id="5778b-320">轉譯影像周圍的周框 cube，以在放置時顯示其實際大小。</span><span class="sxs-lookup"><span data-stu-id="5778b-320">Render a bounding cube around the hologram to show its actual size while being placed.</span></span>
4. <span data-ttu-id="5778b-321">將陰影轉換下/後方的陰影，以顯示將放置在地面/牆上的位置。</span><span class="sxs-lookup"><span data-stu-id="5778b-321">Cast a shadow under/behind the hologram to show where it will be placed on the floor/wall.</span></span>
5. <span data-ttu-id="5778b-322">如果無法在表面上放置全像影像，則將陰影轉譯為紅色，如果可能的話，則呈現綠色。</span><span class="sxs-lookup"><span data-stu-id="5778b-322">Render the shadow as red, if the hologram cannot be placed on the surface, or green, if it can.</span></span>
6. <span data-ttu-id="5778b-323">重新排列影像的方向，使其與具有親和性的表面類型 (垂直或水準) 對齊。</span><span class="sxs-lookup"><span data-stu-id="5778b-323">Re-orient the hologram to align with the surface type (vertical or horizontal) that it has affinity to.</span></span>
7. <span data-ttu-id="5778b-324">順暢地將全像放置在選取的介面上，以避免跳躍或貼齊行為。</span><span class="sxs-lookup"><span data-stu-id="5778b-324">Smoothly place the hologram on the selected surface to avoid jumping or snapping behavior.</span></span>

<span data-ttu-id="5778b-325">取消批註下列程式碼撰寫練習中的所有程式碼，或在 **Placeable.cs** 中使用此已完成的解決方案：</span><span class="sxs-lookup"><span data-stu-id="5778b-325">Uncomment all code in the coding exercise below, or use this completed solution in **Placeable.cs**:</span></span>

```cs
using System.Collections.Generic;
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Enumeration containing the surfaces on which a GameObject
/// can be placed.  For simplicity of this sample, only one
/// surface type is allowed to be selected.
/// </summary>
public enum PlacementSurfaces
{
    // Horizontal surface with an upward pointing normal.
    Horizontal = 1,

    // Vertical surface with a normal facing the user.
    Vertical = 2,
}

/// <summary>
/// The Placeable class implements the logic used to determine if a GameObject
/// can be placed on a target surface. Constraints for placement include:
/// * No part of the GameObject's box collider impacts with another object in the scene
/// * The object lays flat (within specified tolerances) against the surface
/// * The object would not fall off of the surface if gravity were enabled.
/// This class also provides the following visualizations.
/// * A transparent cube representing the object's box collider.
/// * Shadow on the target surface indicating whether or not placement is valid.
/// </summary>
public class Placeable : MonoBehaviour
{
    [Tooltip("The base material used to render the bounds asset when placement is allowed.")]
    public Material PlaceableBoundsMaterial = null;

    [Tooltip("The base material used to render the bounds asset when placement is not allowed.")]
    public Material NotPlaceableBoundsMaterial = null;

    [Tooltip("The material used to render the placement shadow when placement it allowed.")]
    public Material PlaceableShadowMaterial = null;

    [Tooltip("The material used to render the placement shadow when placement it not allowed.")]
    public Material NotPlaceableShadowMaterial = null;

    [Tooltip("The type of surface on which the object can be placed.")]
    public PlacementSurfaces PlacementSurface = PlacementSurfaces.Horizontal;

    [Tooltip("The child object(s) to hide during placement.")]
    public List<GameObject> ChildrenToHide = new List<GameObject>();

    /// <summary>
    /// Indicates if the object is in the process of being placed.
    /// </summary>
    public bool IsPlacing { get; private set; }

    // The most recent distance to the surface.  This is used to 
    // locate the object when the user's gaze does not intersect
    // with the Spatial Mapping mesh.
    private float lastDistance = 2.0f;

    // The distance away from the target surface that the object should hover prior while being placed.
    private float hoverDistance = 0.15f;

    // Threshold (the closer to 0, the stricter the standard) used to determine if a surface is flat.
    private float distanceThreshold = 0.02f;

    // Threshold (the closer to 1, the stricter the standard) used to determine if a surface is vertical.
    private float upNormalThreshold = 0.9f;

    // Maximum distance, from the object, that placement is allowed.
    // This is used when raycasting to see if the object is near a placeable surface.
    private float maximumPlacementDistance = 5.0f;

    // Speed (1.0 being fastest) at which the object settles to the surface upon placement.
    private float placementVelocity = 0.06f;

    // Indicates whether or not this script manages the object's box collider.
    private bool managingBoxCollider = false;

    // The box collider used to determine of the object will fit in the desired location.
    // It is also used to size the bounding cube.
    private BoxCollider boxCollider = null;

    // Visible asset used to show the dimensions of the object. This asset is sized
    // using the box collider's bounds.
    private GameObject boundsAsset = null;

    // Visible asset used to show the where the object is attempting to be placed.
    // This asset is sized using the box collider's bounds.
    private GameObject shadowAsset = null;

    // The location at which the object will be placed.
    private Vector3 targetPosition;

    /// <summary>
    /// Called when the GameObject is created.
    /// </summary>
    private void Awake()
    {
        targetPosition = gameObject.transform.position;

        // Get the object's collider.
        boxCollider = gameObject.GetComponent<BoxCollider>();
        if (boxCollider == null)
        {
            // The object does not have a collider, create one and remember that
            // we are managing it.
            managingBoxCollider = true;
            boxCollider = gameObject.AddComponent<BoxCollider>();
            boxCollider.enabled = false;
        }

        // Create the object that will be used to indicate the bounds of the GameObject.
        boundsAsset = GameObject.CreatePrimitive(PrimitiveType.Cube);
        boundsAsset.transform.parent = gameObject.transform;
        boundsAsset.SetActive(false);

        // Create a object that will be used as a shadow.
        shadowAsset = GameObject.CreatePrimitive(PrimitiveType.Quad);
        shadowAsset.transform.parent = gameObject.transform;
        shadowAsset.SetActive(false);
    }

    /// <summary>
    /// Called when our object is selected.  Generally called by
    /// a gesture management component.
    /// </summary>
    public void OnSelect()
    {
        /* TODO: 4.a CODE ALONG 4.a */

        if (!IsPlacing)
        {
            OnPlacementStart();
        }
        else
        {
            OnPlacementStop();
        }
    }

    /// <summary>
    /// Called once per frame.
    /// </summary>
    private void Update()
    {
        /* TODO: 4.a CODE ALONG 4.a */

        if (IsPlacing)
        {
            // Move the object.
            Move();

            // Set the visual elements.
            Vector3 targetPosition;
            Vector3 surfaceNormal;
            bool canBePlaced = ValidatePlacement(out targetPosition, out surfaceNormal);
            DisplayBounds(canBePlaced);
            DisplayShadow(targetPosition, surfaceNormal, canBePlaced);
        }
        else
        {
            // Disable the visual elements.
            boundsAsset.SetActive(false);
            shadowAsset.SetActive(false);

            // Gracefully place the object on the target surface.
            float dist = (gameObject.transform.position - targetPosition).magnitude;
            if (dist > 0)
            {
                gameObject.transform.position = Vector3.Lerp(gameObject.transform.position, targetPosition, placementVelocity / dist);
            }
            else
            {
                // Unhide the child object(s) to make placement easier.
                for (int i = 0; i < ChildrenToHide.Count; i++)
                {
                    ChildrenToHide[i].SetActive(true);
                }
            }
        }
    }

    /// <summary>
    /// Verify whether or not the object can be placed.
    /// </summary>
    /// <param name="position">
    /// The target position on the surface.
    /// </param>
    /// <param name="surfaceNormal">
    /// The normal of the surface on which the object is to be placed.
    /// </param>
    /// <returns>
    /// True if the target position is valid for placing the object, otherwise false.
    /// </returns>
    private bool ValidatePlacement(out Vector3 position, out Vector3 surfaceNormal)
    {
        Vector3 raycastDirection = gameObject.transform.forward;

        if (PlacementSurface == PlacementSurfaces.Horizontal)
        {
            // Placing on horizontal surfaces.
            // Raycast from the bottom face of the box collider.
            raycastDirection = -(Vector3.up);
        }

        // Initialize out parameters.
        position = Vector3.zero;
        surfaceNormal = Vector3.zero;

        Vector3[] facePoints = GetColliderFacePoints();

        // The origin points we receive are in local space and we 
        // need to raycast in world space.
        for (int i = 0; i < facePoints.Length; i++)
        {
            facePoints[i] = gameObject.transform.TransformVector(facePoints[i]) + gameObject.transform.position;
        }

        // Cast a ray from the center of the box collider face to the surface.
        RaycastHit centerHit;
        if (!Physics.Raycast(facePoints[0],
                        raycastDirection,
                        out centerHit,
                        maximumPlacementDistance,
                        SpatialMappingManager.Instance.LayerMask))
        {
            // If the ray failed to hit the surface, we are done.
            return false;
        }

        // We have found a surface.  Set position and surfaceNormal.
        position = centerHit.point;
        surfaceNormal = centerHit.normal;

        // Cast a ray from the corners of the box collider face to the surface.
        for (int i = 1; i < facePoints.Length; i++)
        {
            RaycastHit hitInfo;
            if (Physics.Raycast(facePoints[i],
                                raycastDirection,
                                out hitInfo,
                                maximumPlacementDistance,
                                SpatialMappingManager.Instance.LayerMask))
            {
                // To be a valid placement location, each of the corners must have a similar
                // enough distance to the surface as the center point
                if (!IsEquivalentDistance(centerHit.distance, hitInfo.distance))
                {
                    return false;
                }
            }
            else
            {
                // The raycast failed to intersect with the target layer.
                return false;
            }
        }

        return true;
    }

    /// <summary>
    /// Determine the coordinates, in local space, of the box collider face that 
    /// will be placed against the target surface.
    /// </summary>
    /// <returns>
    /// Vector3 array with the center point of the face at index 0.
    /// </returns>
    private Vector3[] GetColliderFacePoints()
    {
        // Get the collider extents.  
        // The size values are twice the extents.
        Vector3 extents = boxCollider.size / 2;

        // Calculate the min and max values for each coordinate.
        float minX = boxCollider.center.x - extents.x;
        float maxX = boxCollider.center.x + extents.x;
        float minY = boxCollider.center.y - extents.y;
        float maxY = boxCollider.center.y + extents.y;
        float minZ = boxCollider.center.z - extents.z;
        float maxZ = boxCollider.center.z + extents.z;

        Vector3 center;
        Vector3 corner0;
        Vector3 corner1;
        Vector3 corner2;
        Vector3 corner3;

        if (PlacementSurface == PlacementSurfaces.Horizontal)
        {
            // Placing on horizontal surfaces.
            center = new Vector3(boxCollider.center.x, minY, boxCollider.center.z);
            corner0 = new Vector3(minX, minY, minZ);
            corner1 = new Vector3(minX, minY, maxZ);
            corner2 = new Vector3(maxX, minY, minZ);
            corner3 = new Vector3(maxX, minY, maxZ);
        }
        else
        {
            // Placing on vertical surfaces.
            center = new Vector3(boxCollider.center.x, boxCollider.center.y, maxZ);
            corner0 = new Vector3(minX, minY, maxZ);
            corner1 = new Vector3(minX, maxY, maxZ);
            corner2 = new Vector3(maxX, minY, maxZ);
            corner3 = new Vector3(maxX, maxY, maxZ);
        }

        return new Vector3[] { center, corner0, corner1, corner2, corner3 };
    }

    /// <summary>
    /// Put the object into placement mode.
    /// </summary>
    public void OnPlacementStart()
    {
        // If we are managing the collider, enable it. 
        if (managingBoxCollider)
        {
            boxCollider.enabled = true;
        }

        // Hide the child object(s) to make placement easier.
        for (int i = 0; i < ChildrenToHide.Count; i++)
        {
            ChildrenToHide[i].SetActive(false);
        }

        // Tell the gesture manager that it is to assume
        // all input is to be given to this object.
        GestureManager.Instance.OverrideFocusedObject = gameObject;

        // Enter placement mode.
        IsPlacing = true;
    }

    /// <summary>
    /// Take the object out of placement mode.
    /// </summary>
    /// <remarks>
    /// This method will leave the object in placement mode if called while
    /// the object is in an invalid location.  To determine whether or not
    /// the object has been placed, check the value of the IsPlacing property.
    /// </remarks>
    public void OnPlacementStop()
    {
        // ValidatePlacement requires a normal as an out parameter.
        Vector3 position;
        Vector3 surfaceNormal;

        // Check to see if we can exit placement mode.
        if (!ValidatePlacement(out position, out surfaceNormal))
        {
            return;
        }

        // The object is allowed to be placed.
        // We are placing at a small buffer away from the surface.
        targetPosition = position + (0.01f * surfaceNormal);

        OrientObject(true, surfaceNormal);

        // If we are managing the collider, disable it. 
        if (managingBoxCollider)
        {
            boxCollider.enabled = false;
        }

        // Tell the gesture manager that it is to resume
        // its normal behavior.
        GestureManager.Instance.OverrideFocusedObject = null;

        // Exit placement mode.
        IsPlacing = false;
    }

    /// <summary>
    /// Positions the object along the surface toward which the user is gazing.
    /// </summary>
    /// <remarks>
    /// If the user's gaze does not intersect with a surface, the object
    /// will remain at the most recently calculated distance.
    /// </remarks>
    private void Move()
    {
        Vector3 moveTo = gameObject.transform.position;
        Vector3 surfaceNormal = Vector3.zero;
        RaycastHit hitInfo;

        bool hit = Physics.Raycast(Camera.main.transform.position,
                                Camera.main.transform.forward,
                                out hitInfo,
                                20f,
                                SpatialMappingManager.Instance.LayerMask);

        if (hit)
        {
            float offsetDistance = hoverDistance;

            // Place the object a small distance away from the surface while keeping 
            // the object from going behind the user.
            if (hitInfo.distance <= hoverDistance)
            {
                offsetDistance = 0f;
            }

            moveTo = hitInfo.point + (offsetDistance * hitInfo.normal);

            lastDistance = hitInfo.distance;
            surfaceNormal = hitInfo.normal;
        }
        else
        {
            // The raycast failed to hit a surface.  In this case, keep the object at the distance of the last
            // intersected surface.
            moveTo = Camera.main.transform.position + (Camera.main.transform.forward * lastDistance);
        }

        // Follow the user's gaze.
        float dist = Mathf.Abs((gameObject.transform.position - moveTo).magnitude);
        gameObject.transform.position = Vector3.Lerp(gameObject.transform.position, moveTo, placementVelocity / dist);

        // Orient the object.
        // We are using the return value from Physics.Raycast to instruct
        // the OrientObject function to align to the vertical surface if appropriate.
        OrientObject(hit, surfaceNormal);
    }

    /// <summary>
    /// Orients the object so that it faces the user.
    /// </summary>
    /// <param name="alignToVerticalSurface">
    /// If true and the object is to be placed on a vertical surface, 
    /// orient parallel to the target surface.  If false, orient the object 
    /// to face the user.
    /// </param>
    /// <param name="surfaceNormal">
    /// The target surface's normal vector.
    /// </param>
    /// <remarks>
    /// The alignToVerticalSurface parameter is ignored if the object
    /// is to be placed on a horizontalSurface
    /// </remarks>
    private void OrientObject(bool alignToVerticalSurface, Vector3 surfaceNormal)
    {
        Quaternion rotation = Camera.main.transform.localRotation;

        // If the user's gaze does not intersect with the Spatial Mapping mesh,
        // orient the object towards the user.
        if (alignToVerticalSurface && (PlacementSurface == PlacementSurfaces.Vertical))
        {
            // We are placing on a vertical surface.
            // If the normal of the Spatial Mapping mesh indicates that the
            // surface is vertical, orient parallel to the surface.
            if (Mathf.Abs(surfaceNormal.y) <= (1 - upNormalThreshold))
            {
                rotation = Quaternion.LookRotation(-surfaceNormal, Vector3.up);
            }
        }
        else
        {
            rotation.x = 0f;
            rotation.z = 0f;
        }

        gameObject.transform.rotation = rotation;
    }

    /// <summary>
    /// Displays the bounds asset.
    /// </summary>
    /// <param name="canBePlaced">
    /// Specifies if the object is in a valid placement location.
    /// </param>
    private void DisplayBounds(bool canBePlaced)
    {
        // Ensure the bounds asset is sized and positioned correctly.
        boundsAsset.transform.localPosition = boxCollider.center;
        boundsAsset.transform.localScale = boxCollider.size;
        boundsAsset.transform.rotation = gameObject.transform.rotation;

        // Apply the appropriate material.
        if (canBePlaced)
        {
            boundsAsset.GetComponent<Renderer>().sharedMaterial = PlaceableBoundsMaterial;
        }
        else
        {
            boundsAsset.GetComponent<Renderer>().sharedMaterial = NotPlaceableBoundsMaterial;
        }

        // Show the bounds asset.
        boundsAsset.SetActive(true);
    }

    /// <summary>
    /// Displays the placement shadow asset.
    /// </summary>
    /// <param name="position">
    /// The position at which to place the shadow asset.
    /// </param>
    /// <param name="surfaceNormal">
    /// The normal of the surface on which the asset will be placed
    /// </param>
    /// <param name="canBePlaced">
    /// Specifies if the object is in a valid placement location.
    /// </param>
    private void DisplayShadow(Vector3 position,
                            Vector3 surfaceNormal,
                            bool canBePlaced)
    {
        // Rotate and scale the shadow so that it is displayed on the correct surface and matches the object.
        float rotationX = 0.0f;

        if (PlacementSurface == PlacementSurfaces.Horizontal)
        {
            rotationX = 90.0f;
            shadowAsset.transform.localScale = new Vector3(boxCollider.size.x, boxCollider.size.z, 1);
        }
        else
        {
            shadowAsset.transform.localScale = boxCollider.size;
        }

        Quaternion rotation = Quaternion.Euler(rotationX, gameObject.transform.rotation.eulerAngles.y, 0);
        shadowAsset.transform.rotation = rotation;

        // Apply the appropriate material.
        if (canBePlaced)
        {
            shadowAsset.GetComponent<Renderer>().sharedMaterial = PlaceableShadowMaterial;
        }
        else
        {
            shadowAsset.GetComponent<Renderer>().sharedMaterial = NotPlaceableShadowMaterial;
        }

        // Show the shadow asset as appropriate.
        if (position != Vector3.zero)
        {
            // Position the shadow a small distance from the target surface, along the normal.
            shadowAsset.transform.position = position + (0.01f * surfaceNormal);
            shadowAsset.SetActive(true);
        }
        else
        {
            shadowAsset.SetActive(false);
        }
    }

    /// <summary>
    /// Determines if two distance values should be considered equivalent. 
    /// </summary>
    /// <param name="d1">
    /// Distance to compare.
    /// </param>
    /// <param name="d2">
    /// Distance to compare.
    /// </param>
    /// <returns>
    /// True if the distances are within the desired tolerance, otherwise false.
    /// </returns>
    private bool IsEquivalentDistance(float d1, float d2)
    {
        float dist = Mathf.Abs(d1 - d2);
        return (dist <= distanceThreshold);
    }

    /// <summary>
    /// Called when the GameObject is unloaded.
    /// </summary>
    private void OnDestroy()
    {
        // Unload objects we have created.
        Destroy(boundsAsset);
        boundsAsset = null;
        Destroy(shadowAsset);
        shadowAsset = null;
    }
}
```

<span data-ttu-id="5778b-326">**組建和部署**</span><span class="sxs-lookup"><span data-stu-id="5778b-326">**Build and Deploy**</span></span>

* <span data-ttu-id="5778b-327">同樣地，建立專案並部署到 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="5778b-327">As before, build the project and deploy to the HoloLens.</span></span>
* <span data-ttu-id="5778b-328">等候空間對應資料的掃描和處理完成。</span><span class="sxs-lookup"><span data-stu-id="5778b-328">Wait for scanning and processing of the spatial mapping data to complete.</span></span>
* <span data-ttu-id="5778b-329">當您看到日光系統時，請在下方的投射方塊中看看，並執行選取手勢來四處移動。</span><span class="sxs-lookup"><span data-stu-id="5778b-329">When you see the solar system, gaze at the projection box below and perform a select gesture to move it around.</span></span> <span data-ttu-id="5778b-330">選取 [投射] 方塊時，會在投影方塊周圍顯示周框 cube。</span><span class="sxs-lookup"><span data-stu-id="5778b-330">While the projection box is selected, a bounding cube will be visible around the projection box.</span></span>
* <span data-ttu-id="5778b-331">將您移至房間的不同地點。</span><span class="sxs-lookup"><span data-stu-id="5778b-331">Move you head to gaze at a different location in the room.</span></span> <span data-ttu-id="5778b-332">投影方塊應在您的注視之後。</span><span class="sxs-lookup"><span data-stu-id="5778b-332">The projection box should follow your gaze.</span></span> <span data-ttu-id="5778b-333">當投影方塊下方的陰影變成紅色時，您就無法將全像放在表面上。</span><span class="sxs-lookup"><span data-stu-id="5778b-333">When the shadow below the projection box turns red, you cannot place the hologram on that surface.</span></span> <span data-ttu-id="5778b-334">當投影方塊下方的陰影變成綠色時，您可以藉由執行另一個選取手勢來放置全像投影。</span><span class="sxs-lookup"><span data-stu-id="5778b-334">When the shadow below the projection box turns green, you can place the hologram by performing another select gesture.</span></span>
* <span data-ttu-id="5778b-335">尋找並選取牆上的其中一個全息海報，將其移至新位置。</span><span class="sxs-lookup"><span data-stu-id="5778b-335">Find and select one of the holographic posters on a wall to move it to a new location.</span></span> <span data-ttu-id="5778b-336">請注意，您不能將海報放在地面或最上方，而且當您四處移動時，它仍會正確地導向每個牆。</span><span class="sxs-lookup"><span data-stu-id="5778b-336">Notice that you cannot place the poster on the floor or ceiling, and that it stays correctly oriented to each wall as you move around.</span></span>

## <a name="chapter-5---occlusion"></a><span data-ttu-id="5778b-337">第5章-遮蔽</span><span class="sxs-lookup"><span data-stu-id="5778b-337">Chapter 5 - Occlusion</span></span>

>[!VIDEO https://www.youtube.com/embed/6Xrzh_w-7SE]

<span data-ttu-id="5778b-338">**目標**</span><span class="sxs-lookup"><span data-stu-id="5778b-338">**Objectives**</span></span>

* <span data-ttu-id="5778b-339">判斷空間對應網格是否 pixels occluded 全像影像。</span><span class="sxs-lookup"><span data-stu-id="5778b-339">Determine if a hologram is occluded by the spatial mapping mesh.</span></span>
* <span data-ttu-id="5778b-340">套用不同的遮蔽技術，以達成有趣的效果。</span><span class="sxs-lookup"><span data-stu-id="5778b-340">Apply different occlusion techniques to achieve a fun effect.</span></span>

<span data-ttu-id="5778b-341">**指示**</span><span class="sxs-lookup"><span data-stu-id="5778b-341">**Instructions**</span></span>

<span data-ttu-id="5778b-342">首先，我們要讓空間對應網格遮蔽其他的全像不遮蔽真實世界的影像：</span><span class="sxs-lookup"><span data-stu-id="5778b-342">First, we are going to allow the spatial mapping mesh to occlude other holograms without occluding the real world:</span></span>

* <span data-ttu-id="5778b-343">**在 [階層] 面板中**，選取 [ **SpatialProcessing** ] 物件。</span><span class="sxs-lookup"><span data-stu-id="5778b-343">In the **Hierarchy** panel, select the **SpatialProcessing** object.</span></span>
* <span data-ttu-id="5778b-344">在 [偵測 **器** ] 面板中，尋找 [ **播放空間管理員] (腳本)** 元件。</span><span class="sxs-lookup"><span data-stu-id="5778b-344">In the **Inspector** panel, find the **Play Space Manager (Script)** component.</span></span>
* <span data-ttu-id="5778b-345">按一下 **次要材質** 屬性右邊的圓形。</span><span class="sxs-lookup"><span data-stu-id="5778b-345">Click the circle to the right of the **Secondary Material** property.</span></span>
* <span data-ttu-id="5778b-346">尋找並選取 **遮蔽** 材質，然後關閉視窗。</span><span class="sxs-lookup"><span data-stu-id="5778b-346">Find and select the **Occlusion** material and close the window.</span></span>

<span data-ttu-id="5778b-347">接下來，我們要將特殊行為新增至地球，使其在另一個全息圖 (（例如 sun) 或空間對應網格） pixels occluded 時有藍色反白顯示：</span><span class="sxs-lookup"><span data-stu-id="5778b-347">Next, we are going to add a special behavior to Earth, so that it has a blue highlight whenever it becomes occluded by another hologram (like the sun), or by the spatial mapping mesh:</span></span>

* <span data-ttu-id="5778b-348">在 [ **專案** ] 面板的 [全像 **] 資料夾中** ，展開 [ **SolarSystem** ] 物件。</span><span class="sxs-lookup"><span data-stu-id="5778b-348">In the **Project** panel, in the **Holograms** folder, expand the **SolarSystem** object.</span></span>
* <span data-ttu-id="5778b-349">按一下 [ **地球**]。</span><span class="sxs-lookup"><span data-stu-id="5778b-349">Click on **Earth**.</span></span>
* <span data-ttu-id="5778b-350">在 [偵測 **器** ] 面板中，找出地球的材質 (底部的元件) 。</span><span class="sxs-lookup"><span data-stu-id="5778b-350">In the **Inspector** panel, find the Earth's material (bottom component).</span></span>
* <span data-ttu-id="5778b-351">在 [ **著色器] 下拉式** 清單中，將著色器變更為 **自訂 > OcclusionRim**。</span><span class="sxs-lookup"><span data-stu-id="5778b-351">In the **Shader drop-down**, change the shader to **Custom > OcclusionRim**.</span></span> <span data-ttu-id="5778b-352">如果有另一個物件 pixels occluded，這會在地球周圍呈現藍色醒目提示。</span><span class="sxs-lookup"><span data-stu-id="5778b-352">This will render a blue highlight around Earth whenever it is occluded by another object.</span></span>

<span data-ttu-id="5778b-353">最後，我們要為日光系統中的行星啟用 x 光線視覺效果。</span><span class="sxs-lookup"><span data-stu-id="5778b-353">Finally, we are going to enable an x-ray vision effect for planets in our solar system.</span></span> <span data-ttu-id="5778b-354">我們必須編輯在 Scripts\SolarSystem 資料夾) 中找到的 **PlanetOcclusion.cs** (，才能達到下列目標：</span><span class="sxs-lookup"><span data-stu-id="5778b-354">We will need to edit **PlanetOcclusion.cs** (found in the Scripts\SolarSystem folder) in order to achieve the following:</span></span>

1. <span data-ttu-id="5778b-355">判斷 SpatialMapping 層是否 pixels occluded 行星 (房間網格和平面) 。</span><span class="sxs-lookup"><span data-stu-id="5778b-355">Determine if a planet is occluded by the SpatialMapping layer (room meshes and planes).</span></span>
2. <span data-ttu-id="5778b-356">當 SpatialMapping 圖層 pixels occluded 時，顯示行星的線框表示。</span><span class="sxs-lookup"><span data-stu-id="5778b-356">Show the wireframe representation of a planet whenever it is occluded by the SpatialMapping layer.</span></span>
3. <span data-ttu-id="5778b-357">隱藏 SpatialMapping 圖層未封鎖之行星的線框表示。</span><span class="sxs-lookup"><span data-stu-id="5778b-357">Hide the wireframe representation of a planet when it is not blocked by the SpatialMapping layer.</span></span>

<span data-ttu-id="5778b-358">遵循 PlanetOcclusion.cs 中的編碼練習，或使用下列解決方案：</span><span class="sxs-lookup"><span data-stu-id="5778b-358">Follow the coding exercise in PlanetOcclusion.cs, or use the following solution:</span></span>

```cs
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Determines when the occluded version of the planet should be visible.
/// This script allows us to do selective occlusion, so the occlusionObject
/// will only be rendered when a Spatial Mapping surface is occluding the planet,
/// not when another hologram is responsible for the occlusion.
/// </summary>
public class PlanetOcclusion : MonoBehaviour
{
    [Tooltip("Object to display when the planet is occluded.")]
    public GameObject occlusionObject;

    /// <summary>
    /// Points to raycast to when checking for occlusion.
    /// </summary>
    private Vector3[] checkPoints;

    // Use this for initialization
    void Start()
    {
        occlusionObject.SetActive(false);

        // Set the check points to use when testing for occlusion.
        MeshFilter filter = gameObject.GetComponent<MeshFilter>();
        Vector3 extents = filter.mesh.bounds.extents;
        Vector3 center = filter.mesh.bounds.center;
        Vector3 top = new Vector3(center.x, center.y + extents.y, center.z);
        Vector3 left = new Vector3(center.x - extents.x, center.y, center.z);
        Vector3 right = new Vector3(center.x + extents.x, center.y, center.z);
        Vector3 bottom = new Vector3(center.x, center.y - extents.y, center.z);

        checkPoints = new Vector3[] { center, top, left, right, bottom };
    }

    // Update is called once per frame
    void Update()
    {
        /* TODO: 5.a DEVELOPER CODING EXERCISE 5.a */

        // Check to see if any of the planet's boundary points are occluded.
        for (int i = 0; i < checkPoints.Length; i++)
        {
            // 5.a: Convert the current checkPoint to world coordinates.
            // Call gameObject.transform.TransformPoint(checkPoints[i]).
            // Assign the result to a new Vector3 variable called 'checkPt'.
            Vector3 checkPt = gameObject.transform.TransformPoint(checkPoints[i]);

            // 5.a: Call Vector3.Distance() to calculate the distance
            // between the Main Camera's position and 'checkPt'.
            // Assign the result to a new float variable called 'distance'.
            float distance = Vector3.Distance(Camera.main.transform.position, checkPt);

            // 5.a: Take 'checkPt' and subtract the Main Camera's position from it.
            // Assign the result to a new Vector3 variable called 'direction'.
            Vector3 direction = checkPt - Camera.main.transform.position;

            // Used to indicate if the call to Physics.Raycast() was successful.
            bool raycastHit = false;

            // 5.a: Check if the planet is occluded by a spatial mapping surface.
            // Call Physics.Raycast() with the following arguments:
            // - Pass in the Main Camera's position as the origin.
            // - Pass in 'direction' for the direction.
            // - Pass in 'distance' for the maxDistance.
            // - Pass in SpatialMappingManager.Instance.LayerMask as layerMask.
            // Assign the result to 'raycastHit'.
            raycastHit = Physics.Raycast(Camera.main.transform.position, direction, distance, SpatialMappingManager.Instance.LayerMask);

            if (raycastHit)
            {
                // 5.a: Our raycast hit a surface, so the planet is occluded.
                // Set the occlusionObject to active.
                occlusionObject.SetActive(true);

                // At least one point is occluded, so break from the loop.
                break;
            }
            else
            {
                // 5.a: The Raycast did not hit, so the planet is not occluded.
                // Deactivate the occlusionObject.
                occlusionObject.SetActive(false);
            }
        }
    }
}
```

<span data-ttu-id="5778b-359">**組建和部署**</span><span class="sxs-lookup"><span data-stu-id="5778b-359">**Build and Deploy**</span></span>

* <span data-ttu-id="5778b-360">照常建立應用程式，並將其部署到 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="5778b-360">Build and deploy the application to HoloLens, as usual.</span></span>
* <span data-ttu-id="5778b-361">等候空間對應資料的掃描和處理完成， (您應該會看到藍線出現在) 的牆上。</span><span class="sxs-lookup"><span data-stu-id="5778b-361">Wait for scanning and processing of the spatial mapping data to be complete (you should see blue lines appear on walls).</span></span>
* <span data-ttu-id="5778b-362">尋找並選取日光系統的投射方塊，然後在某個牆旁邊或在計數器後方設定方塊。</span><span class="sxs-lookup"><span data-stu-id="5778b-362">Find and select the solar system's projection box and then set the box next to a wall or behind a counter.</span></span>
* <span data-ttu-id="5778b-363">您可以藉由在海報或投影方塊上隱藏對等的背後表面來查看基本遮蔽。</span><span class="sxs-lookup"><span data-stu-id="5778b-363">You can view basic occlusion by hiding behind surfaces to peer at the poster or projection box.</span></span>
* <span data-ttu-id="5778b-364">找出地球，每次出現在另一個全息圖或表面上時，應該會有藍色的強調效果。</span><span class="sxs-lookup"><span data-stu-id="5778b-364">Look for the Earth, there should be a blue highlight effect whenever it goes behind another hologram or surface.</span></span>
* <span data-ttu-id="5778b-365">當行星在房間後方或其他表面上移動時，請觀賞。</span><span class="sxs-lookup"><span data-stu-id="5778b-365">Watch as the planets move behind the wall or other surfaces in the room.</span></span> <span data-ttu-id="5778b-366">您現在有 x 光願景，可以看到它們的線框骨架！</span><span class="sxs-lookup"><span data-stu-id="5778b-366">You now have x-ray vision and can see their wireframe skeletons!</span></span>

## <a name="the-end"></a><span data-ttu-id="5778b-367">結束</span><span class="sxs-lookup"><span data-stu-id="5778b-367">The End</span></span>

<span data-ttu-id="5778b-368">恭喜！</span><span class="sxs-lookup"><span data-stu-id="5778b-368">Congratulations!</span></span> <span data-ttu-id="5778b-369">您現在已完成 **MR 空間230：空間對應**。</span><span class="sxs-lookup"><span data-stu-id="5778b-369">You have now completed **MR Spatial 230: Spatial mapping**.</span></span>

* <span data-ttu-id="5778b-370">您知道如何掃描您的環境，並將空間對應資料載入至 Unity。</span><span class="sxs-lookup"><span data-stu-id="5778b-370">You know how to scan your environment and load spatial mapping data to Unity.</span></span>
* <span data-ttu-id="5778b-371">您瞭解著色器的基本概念，以及如何使用材質重新將世界視覺化。</span><span class="sxs-lookup"><span data-stu-id="5778b-371">You understand the basics of shaders and how materials can be used to re-visualize the world.</span></span>
* <span data-ttu-id="5778b-372">您已瞭解用來尋找平面和從網格中移除三角形的新處理技巧。</span><span class="sxs-lookup"><span data-stu-id="5778b-372">You learned of new processing techniques for finding planes and removing triangles from a mesh.</span></span>
* <span data-ttu-id="5778b-373">您可以移動影像並將其放在合理的表面上。</span><span class="sxs-lookup"><span data-stu-id="5778b-373">You were able to move and place holograms on surfaces that made sense.</span></span>
* <span data-ttu-id="5778b-374">您遇到了不同的遮蔽技術，並和轉型了 x 光線願景的威力！</span><span class="sxs-lookup"><span data-stu-id="5778b-374">You experienced different occlusion techniques and harnessed the power of x-ray vision!</span></span>