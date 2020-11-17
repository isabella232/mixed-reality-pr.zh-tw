---
title: MR 共用 240-多個 HoloLens 裝置
description: 遵循此程式碼逐步解說，使用 Unity、Visual Studio 和 HoloLens 來學習共用全像影像的詳細資料。
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit、mixedrealitytoolkit、mixedrealitytoolkit-unity、共用、網路、學術、教學課程、HoloLens、混合現實學術、unity、混合現實耳機、windows Mixed reality 耳機、虛擬實境耳機、Windows 10
ms.openlocfilehash: f57629e37463c9a05219ebae92bff8870728d688
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2020
ms.locfileid: "94678257"
---
# <a name="mr-sharing-240-multiple-hololens-devices"></a><span data-ttu-id="c9bec-104">MR Sharing 240：多個 HoloLens 裝置</span><span class="sxs-lookup"><span data-stu-id="c9bec-104">MR Sharing 240: Multiple HoloLens devices</span></span>

>[!NOTE]
><span data-ttu-id="c9bec-105">混合實境學院教學課程的設計是以 HoloLens (第 1 代) 和混合實境沉浸式頭戴裝置為準。</span><span class="sxs-lookup"><span data-stu-id="c9bec-105">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="c9bec-106">因此，對於仍在尋找這些裝置開發指引的開發人員而言，我們覺得這些教學課程很重要。</span><span class="sxs-lookup"><span data-stu-id="c9bec-106">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="c9bec-107">這些教學課程 **_不會_** 使用用於 HoloLens 2 的最新工具組或互動進行更新。</span><span class="sxs-lookup"><span data-stu-id="c9bec-107">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="c9bec-108">系統會保留這些資訊，以繼續在支援的裝置上運作。</span><span class="sxs-lookup"><span data-stu-id="c9bec-108">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="c9bec-109">已針對 HoloLens 2 公佈[一系列新的教學課程](../../../mr-learning-base-01.md)。</span><span class="sxs-lookup"><span data-stu-id="c9bec-109">[A new series of tutorials](../../../mr-learning-base-01.md) has been posted for HoloLens 2.</span></span>

<span data-ttu-id="c9bec-110">當我們在空間中移動時，我們會在世界各地提供全像投影。</span><span class="sxs-lookup"><span data-stu-id="c9bec-110">Holograms are given presence in our world by remaining in place as we move about in space.</span></span> <span data-ttu-id="c9bec-111">HoloLens 會使用不同的 [座標系統](../../../design/coordinate-systems.md) 來追蹤物件的位置和方向，以就地保存全像影像。</span><span class="sxs-lookup"><span data-stu-id="c9bec-111">HoloLens keeps holograms in place by using various [coordinate systems](../../../design/coordinate-systems.md) to keep track of the location and orientation of objects.</span></span> <span data-ttu-id="c9bec-112">當我們在裝置之間共用這些座標系統時，我們可以建立共用的體驗，讓我們參與共用的全像世界。</span><span class="sxs-lookup"><span data-stu-id="c9bec-112">When we share these coordinate systems between devices, we can create a shared experience that allows us to take part in a shared holographic world.</span></span>

<span data-ttu-id="c9bec-113">在此教學課程中，我們將：</span><span class="sxs-lookup"><span data-stu-id="c9bec-113">In this tutorial, we will:</span></span>

* <span data-ttu-id="c9bec-114">設定共用體驗的網路。</span><span class="sxs-lookup"><span data-stu-id="c9bec-114">Setup a network for a shared experience.</span></span>
* <span data-ttu-id="c9bec-115">跨 HoloLens 裝置共用全像影像。</span><span class="sxs-lookup"><span data-stu-id="c9bec-115">Share holograms across HoloLens devices.</span></span>
* <span data-ttu-id="c9bec-116">探索共用全像全球的其他人。</span><span class="sxs-lookup"><span data-stu-id="c9bec-116">Discover other people in our shared holographic world.</span></span>
* <span data-ttu-id="c9bec-117">建立可讓您以其他播放程式為目標的共用互動式體驗，並在其上啟動炮彈！</span><span class="sxs-lookup"><span data-stu-id="c9bec-117">Create a shared interactive experience where you can target other players - and launch projectiles at them!</span></span>

## <a name="device-support"></a><span data-ttu-id="c9bec-118">裝置支援</span><span class="sxs-lookup"><span data-stu-id="c9bec-118">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="c9bec-119">課程</span><span class="sxs-lookup"><span data-stu-id="c9bec-119">Course</span></span></th><th style="width:150px"> <span data-ttu-id="c9bec-120"><a href="../../../hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="c9bec-120"><a href="../../../hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="c9bec-121"><a href="../../../discover/immersive-headset-hardware-details.md">沉浸式頭戴裝置</a></span><span class="sxs-lookup"><span data-stu-id="c9bec-121"><a href="../../../discover/immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="c9bec-122">MR Sharing 240：多個 HoloLens 裝置</span><span class="sxs-lookup"><span data-stu-id="c9bec-122">MR Sharing 240: Multiple HoloLens devices</span></span></td><td style="text-align: center;"> <span data-ttu-id="c9bec-123">✔️</span><span class="sxs-lookup"><span data-stu-id="c9bec-123">✔️</span></span></td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="c9bec-124">開始之前</span><span class="sxs-lookup"><span data-stu-id="c9bec-124">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="c9bec-125">先決條件</span><span class="sxs-lookup"><span data-stu-id="c9bec-125">Prerequisites</span></span>

* <span data-ttu-id="c9bec-126">使用隨網際網路存取安裝的正確 [工具](../../../develop/install-the-tools.md) 設定的 Windows 10 電腦。</span><span class="sxs-lookup"><span data-stu-id="c9bec-126">A Windows 10 PC configured with the correct [tools installed](../../../develop/install-the-tools.md) with Internet access.</span></span>
* <span data-ttu-id="c9bec-127">至少有兩個 HoloLens 裝置 [設定用於開發](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)。</span><span class="sxs-lookup"><span data-stu-id="c9bec-127">At least two HoloLens devices [configured for development](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="c9bec-128">專案檔</span><span class="sxs-lookup"><span data-stu-id="c9bec-128">Project files</span></span>

* <span data-ttu-id="c9bec-129">下載專案 [所需的](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-240-SharedHolograms.zip) 檔案。</span><span class="sxs-lookup"><span data-stu-id="c9bec-129">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-240-SharedHolograms.zip) required by the project.</span></span> <span data-ttu-id="c9bec-130">需要 Unity 2017.2 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="c9bec-130">Requires Unity 2017.2 or later.</span></span>
  * <span data-ttu-id="c9bec-131">如果您仍然需要 Unity 5.6 支援，請使用 [此版本](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-240.zip)。</span><span class="sxs-lookup"><span data-stu-id="c9bec-131">If you still need Unity 5.6 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-240.zip).</span></span>
  * <span data-ttu-id="c9bec-132">如果您仍然需要 Unity 5.5 支援，請使用 [此版本](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-240.zip)。</span><span class="sxs-lookup"><span data-stu-id="c9bec-132">If you still need Unity 5.5 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-240.zip).</span></span>
  * <span data-ttu-id="c9bec-133">如果您仍然需要 Unity 5.4 支援，請使用 [此版本](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-240.zip)。</span><span class="sxs-lookup"><span data-stu-id="c9bec-133">If you still need Unity 5.4 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-240.zip).</span></span>
* <span data-ttu-id="c9bec-134">取消將檔案封存到您的桌面或其他易於觸及的位置。</span><span class="sxs-lookup"><span data-stu-id="c9bec-134">Un-archive the files to your desktop or other easy to reach location.</span></span> <span data-ttu-id="c9bec-135">將資料夾名稱保留為 **SharedHolograms**。</span><span class="sxs-lookup"><span data-stu-id="c9bec-135">Keep the folder name as **SharedHolograms**.</span></span>

>[!NOTE]
><span data-ttu-id="c9bec-136">如果您想要在下載之前查看原始程式碼， [可在 GitHub 上](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-240-SharedHolograms)取得。</span><span class="sxs-lookup"><span data-stu-id="c9bec-136">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-240-SharedHolograms).</span></span>

## <a name="chapter-1---holo-world"></a><span data-ttu-id="c9bec-137">第1章-Hololens World</span><span class="sxs-lookup"><span data-stu-id="c9bec-137">Chapter 1 - Holo World</span></span>

>[!VIDEO https://www.youtube.com/embed/c7qHYYW8rxQ]

<span data-ttu-id="c9bec-138">在本章中，我們將設定第一個 Unity 專案，並逐步執行組建和部署程式。</span><span class="sxs-lookup"><span data-stu-id="c9bec-138">In this chapter, we'll setup our first Unity project and step through the build and deploy process.</span></span>

### <a name="objectives"></a><span data-ttu-id="c9bec-139">目標</span><span class="sxs-lookup"><span data-stu-id="c9bec-139">Objectives</span></span>

* <span data-ttu-id="c9bec-140">設定 Unity 以開發全息型應用程式。</span><span class="sxs-lookup"><span data-stu-id="c9bec-140">Setup Unity to develop holographic apps.</span></span>
* <span data-ttu-id="c9bec-141">查看您的全像影像！</span><span class="sxs-lookup"><span data-stu-id="c9bec-141">See your hologram!</span></span>

### <a name="instructions"></a><span data-ttu-id="c9bec-142">指示</span><span class="sxs-lookup"><span data-stu-id="c9bec-142">Instructions</span></span>

* <span data-ttu-id="c9bec-143">啟動 Unity。</span><span class="sxs-lookup"><span data-stu-id="c9bec-143">Start Unity.</span></span>
* <span data-ttu-id="c9bec-144">選取 [開啟]  。</span><span class="sxs-lookup"><span data-stu-id="c9bec-144">Select **Open**.</span></span>
* <span data-ttu-id="c9bec-145">輸入位置作為您先前 unarchived 的 **SharedHolograms** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="c9bec-145">Enter location as the **SharedHolograms** folder you previously unarchived.</span></span>
* <span data-ttu-id="c9bec-146">選取 [ **專案名稱** ]，然後按一下 [ **選取資料夾**]。</span><span class="sxs-lookup"><span data-stu-id="c9bec-146">Select **Project Name** and click **Select Folder**.</span></span>
* <span data-ttu-id="c9bec-147">**在階層中，以** 滑鼠右鍵按一下 **主要攝影機**，然後選取 [**刪除**]。</span><span class="sxs-lookup"><span data-stu-id="c9bec-147">In the **Hierarchy**, right-click the **Main Camera** and select **Delete**.</span></span>
* <span data-ttu-id="c9bec-148">在 [ **HoloToolkit-共用-240/Prefabs/攝影機** ] 資料夾中，尋找 **主要相機** 預製專案。</span><span class="sxs-lookup"><span data-stu-id="c9bec-148">In the **HoloToolkit-Sharing-240/Prefabs/Camera** folder, find the **Main Camera** prefab.</span></span>
* <span data-ttu-id="c9bec-149">將 [**主要攝影機**] 拖放到階層 **中。**</span><span class="sxs-lookup"><span data-stu-id="c9bec-149">Drag and drop the **Main Camera** into the **Hierarchy**.</span></span>
* <span data-ttu-id="c9bec-150">在階層 **中，按一下**[ **建立** ] 並 **建立空白**。</span><span class="sxs-lookup"><span data-stu-id="c9bec-150">In the **Hierarchy**, click on **Create** and **Create Empty**.</span></span>
* <span data-ttu-id="c9bec-151">以滑鼠右鍵按一下新的 **GameObject** ，然後選取 [ **重新命名**]。</span><span class="sxs-lookup"><span data-stu-id="c9bec-151">Right-click the new **GameObject** and select **Rename**.</span></span>
* <span data-ttu-id="c9bec-152">將 GameObject 重新命名為 **HologramCollection**。</span><span class="sxs-lookup"><span data-stu-id="c9bec-152">Rename the GameObject to **HologramCollection**.</span></span>
* <span data-ttu-id="c9bec-153">選取階層中的 **HologramCollection** 物件 **。**</span><span class="sxs-lookup"><span data-stu-id="c9bec-153">Select the **HologramCollection** object in the **Hierarchy**.</span></span>
* <span data-ttu-id="c9bec-154">在偵測 **器** 中，將 **轉換位置** 設定為： **X：0，Y：-0.25，Z： 2**。</span><span class="sxs-lookup"><span data-stu-id="c9bec-154">In the **Inspector** set the **transform position** to: **X: 0, Y: -0.25, Z: 2**.</span></span>
* <span data-ttu-id="c9bec-155">在 [**專案] 面板** 的 [全像全像 **] 資料夾中**，尋找 **EnergyHub** 資產。</span><span class="sxs-lookup"><span data-stu-id="c9bec-155">In the **Holograms** folder in the **Project panel**, find the **EnergyHub** asset.</span></span>
* <span data-ttu-id="c9bec-156">將 **EnergyHub** 物件從 **專案面板** 拖放到階層中， **做為** **HologramCollection 的子** 系。</span><span class="sxs-lookup"><span data-stu-id="c9bec-156">Drag and drop the **EnergyHub** object from the **Project panel** to the **Hierarchy** as a **child of HologramCollection**.</span></span>
* <span data-ttu-id="c9bec-157">選取 [檔案 **> 另存場景為**...]</span><span class="sxs-lookup"><span data-stu-id="c9bec-157">Select **File > Save Scene As...**</span></span>
* <span data-ttu-id="c9bec-158">命名場景 **SharedHolograms** ，然後按一下 [ **儲存**]。</span><span class="sxs-lookup"><span data-stu-id="c9bec-158">Name the scene **SharedHolograms** and click **Save**.</span></span>
* <span data-ttu-id="c9bec-159">按下 Unity 中的 [ **播放** ] 按鈕，以預覽您的全像影像。</span><span class="sxs-lookup"><span data-stu-id="c9bec-159">Press the **Play** button in Unity to preview your holograms.</span></span>
* <span data-ttu-id="c9bec-160">按第二次 [ **播放** ] 以停止預覽模式。</span><span class="sxs-lookup"><span data-stu-id="c9bec-160">Press **Play** a second time to stop preview mode.</span></span>

<span data-ttu-id="c9bec-161">**將專案從 Unity 匯出至 Visual Studio**</span><span class="sxs-lookup"><span data-stu-id="c9bec-161">**Export the project from Unity to Visual Studio**</span></span>

* <span data-ttu-id="c9bec-162">在 Unity 中，選取 [ **File > Build Settings**]。</span><span class="sxs-lookup"><span data-stu-id="c9bec-162">In Unity select **File > Build Settings**.</span></span>
* <span data-ttu-id="c9bec-163">按一下 [ **新增開啟場景** ] 以加入場景。</span><span class="sxs-lookup"><span data-stu-id="c9bec-163">Click **Add Open Scenes** to add the scene.</span></span>
* <span data-ttu-id="c9bec-164">在 [**平臺**] 清單中選取 **通用 Windows 平臺**，然後按一下 [**切換平臺**]。</span><span class="sxs-lookup"><span data-stu-id="c9bec-164">Select **Universal Windows Platform** in the **Platform** list and click **Switch Platform**.</span></span>
* <span data-ttu-id="c9bec-165">將 **SDK** 設定為 **通用 10**。</span><span class="sxs-lookup"><span data-stu-id="c9bec-165">Set **SDK** to **Universal 10**.</span></span>
* <span data-ttu-id="c9bec-166">將 **目標裝置** 設定為 **HoloLens** ，並將 **UWP 組建類型** 設定為 **D3D**。</span><span class="sxs-lookup"><span data-stu-id="c9bec-166">Set **Target device** to **HoloLens** and **UWP Build Type** to **D3D**.</span></span>
* <span data-ttu-id="c9bec-167">檢查 **Unity c # 專案**。</span><span class="sxs-lookup"><span data-stu-id="c9bec-167">Check **Unity C# Projects**.</span></span>
* <span data-ttu-id="c9bec-168">按一下 [建置]。</span><span class="sxs-lookup"><span data-stu-id="c9bec-168">Click **Build**.</span></span>
* <span data-ttu-id="c9bec-169">在出現的 [檔案瀏覽器] 視窗中，建立名為 "App" 的 **新資料夾** 。</span><span class="sxs-lookup"><span data-stu-id="c9bec-169">In the file explorer window that appears, create a **New Folder** named "App".</span></span>
* <span data-ttu-id="c9bec-170">按一下 **應用程式** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="c9bec-170">Single click the **App** folder.</span></span>
* <span data-ttu-id="c9bec-171">按下 [ **選取資料夾**]。</span><span class="sxs-lookup"><span data-stu-id="c9bec-171">Press **Select Folder**.</span></span>
* <span data-ttu-id="c9bec-172">當 Unity 完成時，將會出現檔案總管視窗。</span><span class="sxs-lookup"><span data-stu-id="c9bec-172">When Unity is done, a File Explorer window will appear.</span></span>
* <span data-ttu-id="c9bec-173">開啟 **應用程式** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="c9bec-173">Open the **App** folder.</span></span>
* <span data-ttu-id="c9bec-174">開啟 **SharedHolograms** 以啟動 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="c9bec-174">Open **SharedHolograms.sln** to launch Visual Studio.</span></span>
* <span data-ttu-id="c9bec-175">使用 Visual Studio 中的頂端工具列，將目標從 Debug 變更為 **Release** ，以及從 ARM 變更為 **X86**。</span><span class="sxs-lookup"><span data-stu-id="c9bec-175">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **X86**.</span></span>
* <span data-ttu-id="c9bec-176">按一下 [本機電腦] 旁的下拉箭號，然後選取 [ **遠端裝置**]。</span><span class="sxs-lookup"><span data-stu-id="c9bec-176">Click on the drop-down arrow next to Local Machine, and select **Remote Device**.</span></span>
    * <span data-ttu-id="c9bec-177">將 **位址** 設定為 HoloLens 的名稱或 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="c9bec-177">Set the **Address** to the name or IP address of your HoloLens.</span></span> <span data-ttu-id="c9bec-178">如果您不知道您的裝置 IP 位址，請查看 [ **設定] > 網路 & 網際網路 > [Advanced Options** ] 或 [問 Cortana **] 嗨 Cortana，我的 IP 位址為何？**</span><span class="sxs-lookup"><span data-stu-id="c9bec-178">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options** or ask Cortana **"Hey Cortana, What's my IP address?"**</span></span>
    * <span data-ttu-id="c9bec-179">將 [ **驗證模式]** 設定為 [ **通用**]。</span><span class="sxs-lookup"><span data-stu-id="c9bec-179">Leave the **Authentication Mode** set to **Universal**.</span></span>
    * <span data-ttu-id="c9bec-180">按一下 [**選取**]</span><span class="sxs-lookup"><span data-stu-id="c9bec-180">Click **Select**</span></span>
* <span data-ttu-id="c9bec-181">按一下 [ **Debug > 啟動但不進行調試** ]，或按 **Ctrl + F5**。</span><span class="sxs-lookup"><span data-stu-id="c9bec-181">Click **Debug > Start Without debugging** or press **Ctrl + F5**.</span></span> <span data-ttu-id="c9bec-182">如果這是您第一次部署至您的裝置，您必須將 [它與 Visual Studio 配對](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#pairing-your-device)。</span><span class="sxs-lookup"><span data-stu-id="c9bec-182">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#pairing-your-device).</span></span>
* <span data-ttu-id="c9bec-183">放在 HoloLens 上，找出 EnergyHub 的全息圖。</span><span class="sxs-lookup"><span data-stu-id="c9bec-183">Put on your HoloLens and find the EnergyHub hologram.</span></span>

## <a name="chapter-2---interaction"></a><span data-ttu-id="c9bec-184">第2章-互動</span><span class="sxs-lookup"><span data-stu-id="c9bec-184">Chapter 2 - Interaction</span></span>

>[!VIDEO https://www.youtube.com/embed/W60xG15a8gc]

<span data-ttu-id="c9bec-185">在本章中，我們將會與我們的全像投影互動。</span><span class="sxs-lookup"><span data-stu-id="c9bec-185">In this chapter, we'll interact with our holograms.</span></span> <span data-ttu-id="c9bec-186">首先，我們會新增一個資料指標來視覺化我們的 [注視](../../../design/gaze-and-commit.md)。</span><span class="sxs-lookup"><span data-stu-id="c9bec-186">First, we'll add a cursor to visualize our [Gaze](../../../design/gaze-and-commit.md).</span></span> <span data-ttu-id="c9bec-187">接著，我們將新增 [手勢](../../../design/gaze-and-commit.md#composite-gestures) ，並使用我們的手將全息的空間放在空間中。</span><span class="sxs-lookup"><span data-stu-id="c9bec-187">Then, we'll add [Gestures](../../../design/gaze-and-commit.md#composite-gestures) and use our hand to place our holograms in space.</span></span>

### <a name="objectives"></a><span data-ttu-id="c9bec-188">目標</span><span class="sxs-lookup"><span data-stu-id="c9bec-188">Objectives</span></span>

* <span data-ttu-id="c9bec-189">使用「注視輸入」來控制資料指標。</span><span class="sxs-lookup"><span data-stu-id="c9bec-189">Use gaze input to control a cursor.</span></span>
* <span data-ttu-id="c9bec-190">使用手勢輸入與全像影像互動。</span><span class="sxs-lookup"><span data-stu-id="c9bec-190">Use gesture input to interact with holograms.</span></span>

### <a name="instructions"></a><span data-ttu-id="c9bec-191">指示</span><span class="sxs-lookup"><span data-stu-id="c9bec-191">Instructions</span></span>

<span data-ttu-id="c9bec-192">**目光**</span><span class="sxs-lookup"><span data-stu-id="c9bec-192">**Gaze**</span></span>

* <span data-ttu-id="c9bec-193">在 [階層] **面板** 中，選取 [ **HologramCollection** ] 物件。</span><span class="sxs-lookup"><span data-stu-id="c9bec-193">In the **Hierarchy panel** select the **HologramCollection** object.</span></span>
* <span data-ttu-id="c9bec-194">在 [偵測 **器] 面板** 中，按一下 [ **新增元件** ] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="c9bec-194">In the **Inspector panel** click the **Add Component** button.</span></span>
* <span data-ttu-id="c9bec-195">在功能表中，于 [搜尋] 方塊中輸入 **注視 Manager**。</span><span class="sxs-lookup"><span data-stu-id="c9bec-195">In the menu, type in the search box **Gaze Manager**.</span></span> <span data-ttu-id="c9bec-196">選取搜尋結果。</span><span class="sxs-lookup"><span data-stu-id="c9bec-196">Select the search result.</span></span>
* <span data-ttu-id="c9bec-197">在 [ **HoloToolkit-Sharing-240\Prefabs\Input** ] 資料夾中，尋找資料 **指標** 資產。</span><span class="sxs-lookup"><span data-stu-id="c9bec-197">In the **HoloToolkit-Sharing-240\Prefabs\Input** folder, find the **Cursor** asset.</span></span>
* <span data-ttu-id="c9bec-198">將資料 **指標** 資產拖放到階層 **上。**</span><span class="sxs-lookup"><span data-stu-id="c9bec-198">Drag and drop the **Cursor** asset onto the **Hierarchy**.</span></span>

<span data-ttu-id="c9bec-199">**手勢**</span><span class="sxs-lookup"><span data-stu-id="c9bec-199">**Gesture**</span></span>

* <span data-ttu-id="c9bec-200">在 [階層] **面板** 中，選取 [ **HologramCollection** ] 物件。</span><span class="sxs-lookup"><span data-stu-id="c9bec-200">In the **Hierarchy panel** select the **HologramCollection** object.</span></span>
* <span data-ttu-id="c9bec-201">按一下 [ **新增元件** ]，然後在 [搜尋] 欄位中輸入 **手勢管理員** 。</span><span class="sxs-lookup"><span data-stu-id="c9bec-201">Click **Add Component** and type **Gesture Manager** in the search field.</span></span> <span data-ttu-id="c9bec-202">選取搜尋結果。</span><span class="sxs-lookup"><span data-stu-id="c9bec-202">Select the search result.</span></span>
* <span data-ttu-id="c9bec-203">在 [階層] **面板** 中，展開 [ **HologramCollection**]。</span><span class="sxs-lookup"><span data-stu-id="c9bec-203">In the **Hierarchy panel**, expand **HologramCollection**.</span></span>
* <span data-ttu-id="c9bec-204">選取子 **EnergyHub** 物件。</span><span class="sxs-lookup"><span data-stu-id="c9bec-204">Select the child **EnergyHub** object.</span></span>
* <span data-ttu-id="c9bec-205">在 [偵測 **器] 面板** 中，按一下 [ **新增元件** ] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="c9bec-205">In the **Inspector panel** click the **Add Component** button.</span></span>
* <span data-ttu-id="c9bec-206">在功能表中，輸入搜尋方塊全息圖 **放置**。</span><span class="sxs-lookup"><span data-stu-id="c9bec-206">In the menu, type in the search box **Hologram Placement**.</span></span> <span data-ttu-id="c9bec-207">選取搜尋結果。</span><span class="sxs-lookup"><span data-stu-id="c9bec-207">Select the search result.</span></span>
* <span data-ttu-id="c9bec-208">選取 [檔案] **> 儲存場景** 來儲存場景。</span><span class="sxs-lookup"><span data-stu-id="c9bec-208">Save the scene by selecting **File > Save Scene**.</span></span>

<span data-ttu-id="c9bec-209">**部署及享用**</span><span class="sxs-lookup"><span data-stu-id="c9bec-209">**Deploy and enjoy**</span></span>

* <span data-ttu-id="c9bec-210">使用上一章的指示，建立並部署至您的 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="c9bec-210">Build and deploy to your HoloLens, using the instructions from the previous chapter.</span></span>
* <span data-ttu-id="c9bec-211">在您的 HoloLens 上啟動應用程式後，請移至您的開端，並留意 EnergyHub 接在您注視的方式。</span><span class="sxs-lookup"><span data-stu-id="c9bec-211">Once the app launches on your HoloLens, move your head around and notice how the EnergyHub follows your gaze.</span></span>
* <span data-ttu-id="c9bec-212">請注意，當您注視全像全像投影時，游標會如何出現，並在不撥雲見日于全像點時變更點燈。</span><span class="sxs-lookup"><span data-stu-id="c9bec-212">Notice how the cursor appears when you gaze upon the hologram, and changes to a point light when not gazing at a hologram.</span></span>
* <span data-ttu-id="c9bec-213">執行點一下來放置全像。</span><span class="sxs-lookup"><span data-stu-id="c9bec-213">Perform an air-tap to place the hologram.</span></span> <span data-ttu-id="c9bec-214">目前，在我們的專案中，您只可以在 (重新部署時放置全像) ，然後再試一次。</span><span class="sxs-lookup"><span data-stu-id="c9bec-214">At this time in our project, you can only place the hologram once (redeploy to try again).</span></span>

## <a name="chapter-3---shared-coordinates"></a><span data-ttu-id="c9bec-215">第3章-共用座標</span><span class="sxs-lookup"><span data-stu-id="c9bec-215">Chapter 3 - Shared Coordinates</span></span>

>[!VIDEO https://www.youtube.com/embed/Ey8yBgWiqtg]

<span data-ttu-id="c9bec-216">您可以輕鬆查看全像影像，並與之互動，但讓我們繼續進行。</span><span class="sxs-lookup"><span data-stu-id="c9bec-216">It's fun to see and interact with holograms, but let's go further.</span></span> <span data-ttu-id="c9bec-217">我們會設定我們的第一個共用體驗，每個人都可以一起查看。</span><span class="sxs-lookup"><span data-stu-id="c9bec-217">We'll set up our first shared experience - a hologram everyone can see together.</span></span>

### <a name="objectives"></a><span data-ttu-id="c9bec-218">目標</span><span class="sxs-lookup"><span data-stu-id="c9bec-218">Objectives</span></span>

* <span data-ttu-id="c9bec-219">設定共用體驗的網路。</span><span class="sxs-lookup"><span data-stu-id="c9bec-219">Setup a network for a shared experience.</span></span>
* <span data-ttu-id="c9bec-220">建立共同的參考點。</span><span class="sxs-lookup"><span data-stu-id="c9bec-220">Establish a common reference point.</span></span>
* <span data-ttu-id="c9bec-221">跨裝置共用座標系統。</span><span class="sxs-lookup"><span data-stu-id="c9bec-221">Share coordinate systems across devices.</span></span>
* <span data-ttu-id="c9bec-222">每個人都看到相同的全息圖！</span><span class="sxs-lookup"><span data-stu-id="c9bec-222">Everyone sees the same hologram!</span></span>

>[!NOTE]
><span data-ttu-id="c9bec-223">您必須為應用程式宣告 **InternetClientServer** 和 **PrivateNetworkClientServer** 功能，才能連接到共用伺服器。</span><span class="sxs-lookup"><span data-stu-id="c9bec-223">The **InternetClientServer** and **PrivateNetworkClientServer** capabilities must be declared for an app to connect to the sharing server.</span></span> <span data-ttu-id="c9bec-224">這是針對您已在全像240的電腦上完成的，但請記住您自己的專案。</span><span class="sxs-lookup"><span data-stu-id="c9bec-224">This is done for you already in Holograms 240, but keep this in mind for your own projects.</span></span>

>1. <span data-ttu-id="c9bec-225">在 Unity 編輯器中，流覽至 [> Player 編輯 > 專案設定]，移至播放機設定</span><span class="sxs-lookup"><span data-stu-id="c9bec-225">In the Unity Editor, go to the player settings by navigating to "Edit > Project Settings > Player"</span></span>
>2. <span data-ttu-id="c9bec-226">按一下 [Windows 市存放區] 索引標籤</span><span class="sxs-lookup"><span data-stu-id="c9bec-226">Click on the "Windows Store" tab</span></span>
>3. <span data-ttu-id="c9bec-227">在 [發佈設定 > 功能] 區段中，檢查 **InternetClientServer** 功能和 **PrivateNetworkClientServer** 功能</span><span class="sxs-lookup"><span data-stu-id="c9bec-227">In the "Publishing Settings > Capabilities" section, check the **InternetClientServer** capability and the **PrivateNetworkClientServer** capability</span></span>

### <a name="instructions"></a><span data-ttu-id="c9bec-228">指示</span><span class="sxs-lookup"><span data-stu-id="c9bec-228">Instructions</span></span>

* <span data-ttu-id="c9bec-229">在 [ **專案] 面板** 中，流覽至 [ **HoloToolkit-Sharing-240\Prefabs\Sharing** ] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="c9bec-229">In the **Project panel** navigate to the **HoloToolkit-Sharing-240\Prefabs\Sharing** folder.</span></span>
* <span data-ttu-id="c9bec-230">將 **共用** 預製專案拖放到 [階層] **面板** 中。</span><span class="sxs-lookup"><span data-stu-id="c9bec-230">Drag and drop the **Sharing** prefab into the **Hierarchy panel**.</span></span>

<span data-ttu-id="c9bec-231">接下來我們需要啟動共用服務。</span><span class="sxs-lookup"><span data-stu-id="c9bec-231">Next we need to launch the sharing service.</span></span> <span data-ttu-id="c9bec-232">只有 **一部電腦** 在共用體驗中需要執行這個步驟。</span><span class="sxs-lookup"><span data-stu-id="c9bec-232">Only **one PC** in the shared experience needs to do this step.</span></span>

* <span data-ttu-id="c9bec-233">在 Unity 中-在最上層功能表中，選取 [ **HoloToolkit-共用-240] 功能表**。</span><span class="sxs-lookup"><span data-stu-id="c9bec-233">In Unity - in the top-hand menu - select the **HoloToolkit-Sharing-240 menu**.</span></span>
* <span data-ttu-id="c9bec-234">在下拉式清單中選取 [ **啟動共用服務** ] 專案。</span><span class="sxs-lookup"><span data-stu-id="c9bec-234">Select the **Launch Sharing Service** item in the drop-down.</span></span>
* <span data-ttu-id="c9bec-235">核取 [ **私人網路** ] 選項，然後在出現防火牆提示時按一下 [ **允許存取** ]。</span><span class="sxs-lookup"><span data-stu-id="c9bec-235">Check the **Private Network** option and click **Allow Access** when the firewall prompt appears.</span></span>
* <span data-ttu-id="c9bec-236">記下 [共用服務主控台] 視窗中顯示的 IPv4 位址。</span><span class="sxs-lookup"><span data-stu-id="c9bec-236">Note down the IPv4 address displayed in the Sharing Service console window.</span></span> <span data-ttu-id="c9bec-237">這與執行服務的電腦是相同的 IP。</span><span class="sxs-lookup"><span data-stu-id="c9bec-237">This is the same IP as the machine the service is being run on.</span></span>

<span data-ttu-id="c9bec-238">遵循將加入共用體驗的 **所有電腦** 上的其他指示。</span><span class="sxs-lookup"><span data-stu-id="c9bec-238">Follow the rest of the instructions on **all PCs** that will join the shared experience.</span></span>

* <span data-ttu-id="c9bec-239">**在階層中，選取\*\*\*\*共用** 物件。</span><span class="sxs-lookup"><span data-stu-id="c9bec-239">In the **Hierarchy**, select the **Sharing** object.</span></span>
* <span data-ttu-id="c9bec-240">在偵測 **器** 的 **共用階段** 元件上，將 **伺服器位址** 從 ' localhost ' 變更為執行 SharingService.exe 之電腦的 IPv4 位址。</span><span class="sxs-lookup"><span data-stu-id="c9bec-240">In the **Inspector**, on the **Sharing Stage** component, change the **Server Address** from 'localhost' to the IPv4 address of the machine running SharingService.exe.</span></span>
* <span data-ttu-id="c9bec-241">**在階層中選取**[ **HologramCollection** ] 物件。</span><span class="sxs-lookup"><span data-stu-id="c9bec-241">In the **Hierarchy** select the **HologramCollection** object.</span></span>
* <span data-ttu-id="c9bec-242">在 [偵測 **器** ] 中，按一下 [ **新增元件** ] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="c9bec-242">In the **Inspector** click the **Add Component** button.</span></span>
* <span data-ttu-id="c9bec-243">在搜尋方塊中，輸入匯 **入匯出錨點管理員**。</span><span class="sxs-lookup"><span data-stu-id="c9bec-243">In the search box, type **Import Export Anchor Manager**.</span></span> <span data-ttu-id="c9bec-244">選取搜尋結果。</span><span class="sxs-lookup"><span data-stu-id="c9bec-244">Select the search result.</span></span>
* <span data-ttu-id="c9bec-245">在 [ **專案] 面板** 中，流覽至 [ **腳本** ] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="c9bec-245">In the **Project panel** navigate to the **Scripts** folder.</span></span>
* <span data-ttu-id="c9bec-246">按兩下 **HologramPlacement** 腳本，在 Visual Studio 中開啟它。</span><span class="sxs-lookup"><span data-stu-id="c9bec-246">Double-click the **HologramPlacement** script to open it in Visual Studio.</span></span>
* <span data-ttu-id="c9bec-247">使用以下列程式碼取代內容。</span><span class="sxs-lookup"><span data-stu-id="c9bec-247">Replace the contents with the code below.</span></span>

```cs
using UnityEngine;
using System.Collections.Generic;
using UnityEngine.Windows.Speech;
using Academy.HoloToolkit.Unity;
using Academy.HoloToolkit.Sharing;

public class HologramPlacement : Singleton<HologramPlacement>
{
    /// <summary>
    /// Tracks if we have been sent a transform for the anchor model.
    /// The anchor model is rendered relative to the actual anchor.
    /// </summary>
    public bool GotTransform { get; private set; }

    private bool animationPlayed = false;

    void Start()
    {
        // We care about getting updates for the anchor transform.
        CustomMessages.Instance.MessageHandlers[CustomMessages.TestMessageID.StageTransform] = this.OnStageTransform;

        // And when a new user join we will send the anchor transform we have.
        SharingSessionTracker.Instance.SessionJoined += Instance_SessionJoined;
    }

    /// <summary>
    /// When a new user joins we want to send them the relative transform for the anchor if we have it.
    /// </summary>
    /// <param name="sender"></param>
    /// <param name="e"></param>
    private void Instance_SessionJoined(object sender, SharingSessionTracker.SessionJoinedEventArgs e)
    {
        if (GotTransform)
        {
            CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
        }
    }

    void Update()
    {
        if (GotTransform)
        {
            if (ImportExportAnchorManager.Instance.AnchorEstablished &&
                animationPlayed == false)
            {
                // This triggers the animation sequence for the anchor model and 
                // puts the cool materials on the model.
                GetComponent<EnergyHubBase>().SendMessage("OnSelect");
                animationPlayed = true;
            }
        }
        else
        {
            transform.position = Vector3.Lerp(transform.position, ProposeTransformPosition(), 0.2f);
        }
    }

    Vector3 ProposeTransformPosition()
    {
        // Put the anchor 2m in front of the user.
        Vector3 retval = Camera.main.transform.position + Camera.main.transform.forward * 2;

        return retval;
    }

    public void OnSelect()
    {
        // Note that we have a transform.
        GotTransform = true;

        // And send it to our friends.
        CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
    }

    /// <summary>
    /// When a remote system has a transform for us, we'll get it here.
    /// </summary>
    /// <param name="msg"></param>
    void OnStageTransform(NetworkInMessage msg)
    {
        // We read the user ID but we don't use it here.
        msg.ReadInt64();

        transform.localPosition = CustomMessages.Instance.ReadVector3(msg);
        transform.localRotation = CustomMessages.Instance.ReadQuaternion(msg);

        // The first time, we'll want to send the message to the anchor to do its animation and
        // swap its materials.
        if (GotTransform == false)
        {
            GetComponent<EnergyHubBase>().SendMessage("OnSelect");
        }

        GotTransform = true;
    }

    public void ResetStage()
    {
        // We'll use this later.
    }
}
```

* <span data-ttu-id="c9bec-248">回到 Unity，在 [階層]**面板** 中選取 **HologramCollection** 。</span><span class="sxs-lookup"><span data-stu-id="c9bec-248">Back in Unity, select the **HologramCollection** in the **Hierarchy panel**.</span></span>
* <span data-ttu-id="c9bec-249">在 [偵測 **器] 面板** 中，按一下 [ **新增元件** ] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="c9bec-249">In the **Inspector panel** click the **Add Component** button.</span></span>
* <span data-ttu-id="c9bec-250">在功能表中，輸入搜尋 box **應用程式狀態管理員**。</span><span class="sxs-lookup"><span data-stu-id="c9bec-250">In the menu, type in the search box **App State Manager**.</span></span> <span data-ttu-id="c9bec-251">選取搜尋結果。</span><span class="sxs-lookup"><span data-stu-id="c9bec-251">Select the search result.</span></span>

<span data-ttu-id="c9bec-252">**部署及享用**</span><span class="sxs-lookup"><span data-stu-id="c9bec-252">**Deploy and enjoy**</span></span>

* <span data-ttu-id="c9bec-253">建立 HoloLens 裝置的專案。</span><span class="sxs-lookup"><span data-stu-id="c9bec-253">Build the project for your HoloLens devices.</span></span>
* <span data-ttu-id="c9bec-254">指定一個 HoloLens 以先部署到其中。</span><span class="sxs-lookup"><span data-stu-id="c9bec-254">Designate one HoloLens to deploy to first.</span></span> <span data-ttu-id="c9bec-255">您必須等待錨點上傳至服務，才能放置 EnergyHub (這可能需要大約30-60 秒的時間) 。</span><span class="sxs-lookup"><span data-stu-id="c9bec-255">You will need to wait for the Anchor to be uploaded to the service before you can place the EnergyHub (this can take ~30-60 seconds).</span></span> <span data-ttu-id="c9bec-256">在上傳完成之前，您的分流手勢將會被忽略。</span><span class="sxs-lookup"><span data-stu-id="c9bec-256">Until the upload is done, your tap gestures will be ignored.</span></span>
* <span data-ttu-id="c9bec-257">放置 EnergyHub 之後，其位置會上傳至服務，然後您就可以部署到所有其他 HoloLens 裝置。</span><span class="sxs-lookup"><span data-stu-id="c9bec-257">After the EnergyHub has been placed, its location will be uploaded to the service and you can then deploy to all other HoloLens devices.</span></span>
* <span data-ttu-id="c9bec-258">當新的 HoloLens 首次加入會話時，該裝置上的 EnergyHub 位置可能不正確。</span><span class="sxs-lookup"><span data-stu-id="c9bec-258">When a new HoloLens first joins the session, the location of the EnergyHub may not be correct on that device.</span></span> <span data-ttu-id="c9bec-259">不過，一旦從服務下載錨點和 EnergyHub 位置，EnergyHub 應該會跳至新的共用位置。</span><span class="sxs-lookup"><span data-stu-id="c9bec-259">However, as soon as the anchor and EnergyHub locations have been downloaded from the service, the EnergyHub should jump to the new, shared location.</span></span> <span data-ttu-id="c9bec-260">如果這不是在 ~ 30-60 秒內發生，請在設定錨點以收集更多環境線索時，逐步解說原始 HoloLens 的所在位置。</span><span class="sxs-lookup"><span data-stu-id="c9bec-260">If this does not happen within ~30-60 seconds, walk to where the original HoloLens was when setting the anchor to gather more environment clues.</span></span> <span data-ttu-id="c9bec-261">如果位置仍未鎖定，請重新部署至裝置。</span><span class="sxs-lookup"><span data-stu-id="c9bec-261">If the location still does not lock on, redeploy to the device.</span></span>
* <span data-ttu-id="c9bec-262">當裝置都已就緒且正在執行應用程式時，請尋找 EnergyHub。</span><span class="sxs-lookup"><span data-stu-id="c9bec-262">When the devices are all ready and running the app, look for the EnergyHub.</span></span> <span data-ttu-id="c9bec-263">您是否同意全像全像全像全像全像全像全庫存的位置，以及文字面向的方向？</span><span class="sxs-lookup"><span data-stu-id="c9bec-263">Can you all agree on the hologram's location and which direction the text is facing?</span></span>

## <a name="chapter-4---discovery"></a><span data-ttu-id="c9bec-264">第4章-探索</span><span class="sxs-lookup"><span data-stu-id="c9bec-264">Chapter 4 - Discovery</span></span>

>[!VIDEO https://www.youtube.com/embed/5NxJWMV4BP8]

<span data-ttu-id="c9bec-265">每個人現在都可以看到相同的全息圖！</span><span class="sxs-lookup"><span data-stu-id="c9bec-265">Everyone can now see the same hologram!</span></span> <span data-ttu-id="c9bec-266">現在讓我們看看其他人連線到我們分享的全像全球。</span><span class="sxs-lookup"><span data-stu-id="c9bec-266">Now let's see everyone else connected to our shared holographic world.</span></span> <span data-ttu-id="c9bec-267">在本章中，我們將在相同的共用會話中抓取所有其他 HoloLens 裝置的前端位置和旋轉。</span><span class="sxs-lookup"><span data-stu-id="c9bec-267">In this chapter, we'll grab the head location and rotation of all other HoloLens devices in the same sharing session.</span></span>

### <a name="objectives"></a><span data-ttu-id="c9bec-268">目標</span><span class="sxs-lookup"><span data-stu-id="c9bec-268">Objectives</span></span>

* <span data-ttu-id="c9bec-269">在我們的共用體驗中找到彼此。</span><span class="sxs-lookup"><span data-stu-id="c9bec-269">Discover each other in our shared experience.</span></span>
* <span data-ttu-id="c9bec-270">選擇並分享玩家頭像。</span><span class="sxs-lookup"><span data-stu-id="c9bec-270">Choose and share a player avatar.</span></span>
* <span data-ttu-id="c9bec-271">將玩家頭像附加到每個人的標題旁邊。</span><span class="sxs-lookup"><span data-stu-id="c9bec-271">Attach the player avatar next to everyone's heads.</span></span>

### <a name="instructions"></a><span data-ttu-id="c9bec-272">指示</span><span class="sxs-lookup"><span data-stu-id="c9bec-272">Instructions</span></span>

* <span data-ttu-id="c9bec-273">在 [ **專案] 面板** 中，流覽至 [ **全息** 全像] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="c9bec-273">In the **Project panel** navigate to the **Holograms** folder.</span></span>
* <span data-ttu-id="c9bec-274">將 **PlayerAvatarStore** 拖放到階層中 **。**</span><span class="sxs-lookup"><span data-stu-id="c9bec-274">Drag and drop the **PlayerAvatarStore** into the **Hierarchy**.</span></span>
* <span data-ttu-id="c9bec-275">在 [ **專案] 面板** 中，流覽至 [ **腳本** ] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="c9bec-275">In the **Project panel** navigate to the **Scripts** folder.</span></span>
* <span data-ttu-id="c9bec-276">按兩下 **AvatarSelector** 腳本，在 Visual Studio 中開啟它。</span><span class="sxs-lookup"><span data-stu-id="c9bec-276">Double-click the **AvatarSelector** script to open it in Visual Studio.</span></span>
* <span data-ttu-id="c9bec-277">使用以下列程式碼取代內容。</span><span class="sxs-lookup"><span data-stu-id="c9bec-277">Replace the contents with the code below.</span></span>

```cs
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Script to handle the user selecting the avatar.
/// </summary>
public class AvatarSelector : MonoBehaviour
{
    /// <summary>
    /// This is the index set by the PlayerAvatarStore for the avatar.
    /// </summary>
    public int AvatarIndex { get; set; }

    /// <summary>
    /// Called when the user is gazing at this avatar and air-taps it.
    /// This sends the user's selection to the rest of the devices in the experience.
    /// </summary>
    void OnSelect()
    {
        PlayerAvatarStore.Instance.DismissAvatarPicker();

        LocalPlayerManager.Instance.SetUserAvatar(AvatarIndex);
    }

    void Start()
    {
        // Add Billboard component so the avatar always faces the user.
        Billboard billboard = gameObject.GetComponent<Billboard>();
        if (billboard == null)
        {
            billboard = gameObject.AddComponent<Billboard>();
        }

        // Lock rotation along the Y axis.
        billboard.PivotAxis = PivotAxis.Y;
    }
}
```

* <span data-ttu-id="c9bec-278">**在階層中選取**[ **HologramCollection** ] 物件。</span><span class="sxs-lookup"><span data-stu-id="c9bec-278">In the **Hierarchy** select the **HologramCollection** object.</span></span>
* <span data-ttu-id="c9bec-279">在 [偵測 **器** ] 中按一下 [ **新增元件**]。</span><span class="sxs-lookup"><span data-stu-id="c9bec-279">In the **Inspector** click **Add Component**.</span></span>
* <span data-ttu-id="c9bec-280">在 [搜尋] 方塊中，輸入「 **本機播放機管理員**」。</span><span class="sxs-lookup"><span data-stu-id="c9bec-280">In the search box, type **Local Player Manager**.</span></span> <span data-ttu-id="c9bec-281">選取搜尋結果。</span><span class="sxs-lookup"><span data-stu-id="c9bec-281">Select the search result.</span></span>
* <span data-ttu-id="c9bec-282">**在階層中選取**[ **HologramCollection** ] 物件。</span><span class="sxs-lookup"><span data-stu-id="c9bec-282">In the **Hierarchy** select the **HologramCollection** object.</span></span>
* <span data-ttu-id="c9bec-283">在 [偵測 **器** ] 中按一下 [ **新增元件**]。</span><span class="sxs-lookup"><span data-stu-id="c9bec-283">In the **Inspector** click **Add Component**.</span></span>
* <span data-ttu-id="c9bec-284">在 [搜尋] 方塊中，輸入 **Remote Player Manager**。</span><span class="sxs-lookup"><span data-stu-id="c9bec-284">In the search box, type **Remote Player Manager**.</span></span> <span data-ttu-id="c9bec-285">選取搜尋結果。</span><span class="sxs-lookup"><span data-stu-id="c9bec-285">Select the search result.</span></span>
* <span data-ttu-id="c9bec-286">在 Visual Studio 中開啟 **HologramPlacement** 腳本。</span><span class="sxs-lookup"><span data-stu-id="c9bec-286">Open the **HologramPlacement** script in Visual Studio.</span></span>
* <span data-ttu-id="c9bec-287">使用以下列程式碼取代內容。</span><span class="sxs-lookup"><span data-stu-id="c9bec-287">Replace the contents with the code below.</span></span>

```cs
using UnityEngine;
using System.Collections.Generic;
using UnityEngine.Windows.Speech;
using Academy.HoloToolkit.Unity;
using Academy.HoloToolkit.Sharing;

public class HologramPlacement : Singleton<HologramPlacement>
{
    /// <summary>
    /// Tracks if we have been sent a transform for the model.
    /// The model is rendered relative to the actual anchor.
    /// </summary>
    public bool GotTransform { get; private set; }

    /// <summary>
    /// When the experience starts, we disable all of the rendering of the model.
    /// </summary>
    List<MeshRenderer> disabledRenderers = new List<MeshRenderer>();

    void Start()
    {
        // When we first start, we need to disable the model to avoid it obstructing the user picking a hat.
        DisableModel();

        // We care about getting updates for the model transform.
        CustomMessages.Instance.MessageHandlers[CustomMessages.TestMessageID.StageTransform] = this.OnStageTransform;

        // And when a new user join we will send the model transform we have.
        SharingSessionTracker.Instance.SessionJoined += Instance_SessionJoined;
    }

    /// <summary>
    /// When a new user joins we want to send them the relative transform for the model if we have it.
    /// </summary>
    /// <param name="sender"></param>
    /// <param name="e"></param>
    private void Instance_SessionJoined(object sender, SharingSessionTracker.SessionJoinedEventArgs e)
    {
        if (GotTransform)
        {
            CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
        }
    }

    /// <summary>
    /// Turns off all renderers for the model.
    /// </summary>
    void DisableModel()
    {
        foreach (MeshRenderer renderer in gameObject.GetComponentsInChildren<MeshRenderer>())
        {
            if (renderer.enabled)
            {
                renderer.enabled = false;
                disabledRenderers.Add(renderer);
            }
        }

        foreach (MeshCollider collider in gameObject.GetComponentsInChildren<MeshCollider>())
        {
            collider.enabled = false;
        }
    }

    /// <summary>
    /// Turns on all renderers that were disabled.
    /// </summary>
    void EnableModel()
    {
        foreach (MeshRenderer renderer in disabledRenderers)
        {
            renderer.enabled = true;
        }

        foreach (MeshCollider collider in gameObject.GetComponentsInChildren<MeshCollider>())
        {
            collider.enabled = true;
        }

        disabledRenderers.Clear();
    }


    void Update()
    {
        // Wait till users pick an avatar to enable renderers.
        if (disabledRenderers.Count > 0)
        {
            if (!PlayerAvatarStore.Instance.PickerActive &&
            ImportExportAnchorManager.Instance.AnchorEstablished)
            {
                // After which we want to start rendering.
                EnableModel();

                // And if we've already been sent the relative transform, we will use it.
                if (GotTransform)
                {
                    // This triggers the animation sequence for the model and
                    // puts the cool materials on the model.
                    GetComponent<EnergyHubBase>().SendMessage("OnSelect");
                }
            }
        }
        else if (GotTransform == false)
        {
            transform.position = Vector3.Lerp(transform.position, ProposeTransformPosition(), 0.2f);
        }
    }

    Vector3 ProposeTransformPosition()
    {
        // Put the model 2m in front of the user.
        Vector3 retval = Camera.main.transform.position + Camera.main.transform.forward * 2;

        return retval;
    }

    public void OnSelect()
    {
        // Note that we have a transform.
        GotTransform = true;

        // And send it to our friends.
        CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
    }

    /// <summary>
    /// When a remote system has a transform for us, we'll get it here.
    /// </summary>
    /// <param name="msg"></param>
    void OnStageTransform(NetworkInMessage msg)
    {
        // We read the user ID but we don't use it here.
        msg.ReadInt64();

        transform.localPosition = CustomMessages.Instance.ReadVector3(msg);
        transform.localRotation = CustomMessages.Instance.ReadQuaternion(msg);

        // The first time, we'll want to send the message to the model to do its animation and
        // swap its materials.
        if (disabledRenderers.Count == 0 && GotTransform == false)
        {
            GetComponent<EnergyHubBase>().SendMessage("OnSelect");
        }

        GotTransform = true;
    }

    public void ResetStage()
    {
        // We'll use this later.
    }
}
```

* <span data-ttu-id="c9bec-288">在 Visual Studio 中開啟 **AppStateManager** 腳本。</span><span class="sxs-lookup"><span data-stu-id="c9bec-288">Open the **AppStateManager** script in Visual Studio.</span></span>
* <span data-ttu-id="c9bec-289">使用以下列程式碼取代內容。</span><span class="sxs-lookup"><span data-stu-id="c9bec-289">Replace the contents with the code below.</span></span>

```cs
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Keeps track of the current state of the experience.
/// </summary>
public class AppStateManager : Singleton<AppStateManager>
{
    /// <summary>
    /// Enum to track progress through the experience.
    /// </summary>
    public enum AppState
    {
        Starting = 0,
        WaitingForAnchor,
        WaitingForStageTransform,
        PickingAvatar,
        Ready
    }

    /// <summary>
    /// Tracks the current state in the experience.
    /// </summary>
    public AppState CurrentAppState { get; set; }

    void Start()
    {
        // We start in the 'picking avatar' mode.
        CurrentAppState = AppState.PickingAvatar;

        // We start by showing the avatar picker.
        PlayerAvatarStore.Instance.SpawnAvatarPicker();
    }

    void Update()
    {
        switch (CurrentAppState)
        {
            case AppState.PickingAvatar:
                // Avatar picking is done when the avatar picker has been dismissed.
                if (PlayerAvatarStore.Instance.PickerActive == false)
                {
                    CurrentAppState = AppState.WaitingForAnchor;
                }
                break;
            case AppState.WaitingForAnchor:
                if (ImportExportAnchorManager.Instance.AnchorEstablished)
                {
                    CurrentAppState = AppState.WaitingForStageTransform;
                    GestureManager.Instance.OverrideFocusedObject = HologramPlacement.Instance.gameObject;
                }
                break;
            case AppState.WaitingForStageTransform:
                // Now if we have the stage transform we are ready to go.
                if (HologramPlacement.Instance.GotTransform)
                {
                    CurrentAppState = AppState.Ready;
                    GestureManager.Instance.OverrideFocusedObject = null;
                }
                break;
        }
    }
}
```

<span data-ttu-id="c9bec-290">**部署及享用**</span><span class="sxs-lookup"><span data-stu-id="c9bec-290">**Deploy and Enjoy**</span></span>

* <span data-ttu-id="c9bec-291">建立專案，並將其部署到您的 HoloLens 裝置。</span><span class="sxs-lookup"><span data-stu-id="c9bec-291">Build and deploy the project to your HoloLens devices.</span></span>
* <span data-ttu-id="c9bec-292">當您聽到 ping 音效時，請尋找 [顯示圖片] 的 [選取專案] 功能表，並選取具有 [點一下] 手勢的圖片。</span><span class="sxs-lookup"><span data-stu-id="c9bec-292">When you hear a pinging sound, find the avatar selection menu and select an avatar with the air-tap gesture.</span></span>
* <span data-ttu-id="c9bec-293">如果您不想查看任何全息體，則當 HoloLens 與服務進行通訊時，游標周圍的點燈將會變成不同的色彩：初始化 (深紫色) 、將錨點下載 (綠色) 、匯入/匯出位置資料 (黃色) 、將錨點上傳 (藍色) 。</span><span class="sxs-lookup"><span data-stu-id="c9bec-293">If you're not looking at any holograms, the point light around your cursor will turn a different color when your HoloLens is communicating with the service: initializing (dark purple), downloading the anchor (green), importing/exporting location data (yellow), uploading the anchor (blue).</span></span> <span data-ttu-id="c9bec-294">如果游標周圍的點燈是預設色彩 (淺紫色) ，您就可以開始與會話中的其他玩家互動！</span><span class="sxs-lookup"><span data-stu-id="c9bec-294">If your point light around your cursor is the default color (light purple), then you are ready to interact with other players in your session!</span></span>
* <span data-ttu-id="c9bec-295">查看連接到您空間的其他人-將會有一位全像的機器人，並模擬其頭部運動！</span><span class="sxs-lookup"><span data-stu-id="c9bec-295">Look at other people connected to your space - there will be a holographic robot floating above their shoulder and mimicking their head motions!</span></span>

## <a name="chapter-5---placement"></a><span data-ttu-id="c9bec-296">第5章-放置</span><span class="sxs-lookup"><span data-stu-id="c9bec-296">Chapter 5 - Placement</span></span>

>[!VIDEO https://www.youtube.com/embed/afFTwHQIw0s]

<span data-ttu-id="c9bec-297">在本章中，我們會讓錨點放在實際的表面上。</span><span class="sxs-lookup"><span data-stu-id="c9bec-297">In this chapter, we'll make the anchor able to be placed on real-world surfaces.</span></span> <span data-ttu-id="c9bec-298">我們將使用共用座標，將該錨點放在所有連線到共用體驗的人之間的中間點。</span><span class="sxs-lookup"><span data-stu-id="c9bec-298">We'll use shared coordinates to place that anchor in the middle point between everyone connected to the shared experience.</span></span>

### <a name="objectives"></a><span data-ttu-id="c9bec-299">目標</span><span class="sxs-lookup"><span data-stu-id="c9bec-299">Objectives</span></span>

* <span data-ttu-id="c9bec-300">根據玩家的標頭位置，在空間對應網格上放置全像影像。</span><span class="sxs-lookup"><span data-stu-id="c9bec-300">Place holograms on the spatial mapping mesh based on players’ head position.</span></span>

### <a name="instructions"></a><span data-ttu-id="c9bec-301">指示</span><span class="sxs-lookup"><span data-stu-id="c9bec-301">Instructions</span></span>

* <span data-ttu-id="c9bec-302">在 [ **專案] 面板** 中，流覽至 [ **全息** 全像] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="c9bec-302">In the **Project panel** navigate to the **Holograms** folder.</span></span>
* <span data-ttu-id="c9bec-303">將 **CustomSpatialMapping** 預製專案拖放到階層上 **。**</span><span class="sxs-lookup"><span data-stu-id="c9bec-303">Drag and drop the **CustomSpatialMapping** prefab onto the **Hierarchy**.</span></span>
* <span data-ttu-id="c9bec-304">在 [ **專案] 面板** 中，流覽至 [ **腳本** ] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="c9bec-304">In the **Project panel** navigate to the **Scripts** folder.</span></span>
* <span data-ttu-id="c9bec-305">按兩下 **AppStateManager** 腳本，在 Visual Studio 中開啟它。</span><span class="sxs-lookup"><span data-stu-id="c9bec-305">Double-click the **AppStateManager** script to open it in Visual Studio.</span></span>
* <span data-ttu-id="c9bec-306">使用以下列程式碼取代內容。</span><span class="sxs-lookup"><span data-stu-id="c9bec-306">Replace the contents with the code below.</span></span>

```cs
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Keeps track of the current state of the experience.
/// </summary>
public class AppStateManager : Singleton<AppStateManager>
{
    /// <summary>
    /// Enum to track progress through the experience.
    /// </summary>
    public enum AppState
    {
        Starting = 0,
        PickingAvatar,
        WaitingForAnchor,
        WaitingForStageTransform,
        Ready
    }

    // The object to call to make a projectile.
    GameObject shootHandler = null;

    /// <summary>
    /// Tracks the current state in the experience.
    /// </summary>
    public AppState CurrentAppState { get; set; }

    void Start()
    {
        // The shootHandler shoots projectiles.
        if (GetComponent<ProjectileLauncher>() != null)
        {
            shootHandler = GetComponent<ProjectileLauncher>().gameObject;
        }

        // We start in the 'picking avatar' mode.
        CurrentAppState = AppState.PickingAvatar;

        // Spatial mapping should be disabled when we start up so as not
        // to distract from the avatar picking.
        SpatialMappingManager.Instance.StopObserver();
        SpatialMappingManager.Instance.gameObject.SetActive(false);

        // On device we start by showing the avatar picker.
        PlayerAvatarStore.Instance.SpawnAvatarPicker();
    }

    public void ResetStage()
    {
        // If we fall back to waiting for anchor, everything needed to
        // get us into setting the target transform state will be setup.
        if (CurrentAppState != AppState.PickingAvatar)
        {
            CurrentAppState = AppState.WaitingForAnchor;
        }

        // Reset the underworld.
        if (UnderworldBase.Instance)
        {
            UnderworldBase.Instance.ResetUnderworld();
        }
    }

    void Update()
    {
        switch (CurrentAppState)
        {
            case AppState.PickingAvatar:
                // Avatar picking is done when the avatar picker has been dismissed.
                if (PlayerAvatarStore.Instance.PickerActive == false)
                {
                    CurrentAppState = AppState.WaitingForAnchor;
                }
                break;
            case AppState.WaitingForAnchor:
                // Once the anchor is established we need to run spatial mapping for a
                // little while to build up some meshes.
                if (ImportExportAnchorManager.Instance.AnchorEstablished)
                {
                    CurrentAppState = AppState.WaitingForStageTransform;
                    GestureManager.Instance.OverrideFocusedObject = HologramPlacement.Instance.gameObject;

                    SpatialMappingManager.Instance.gameObject.SetActive(true);
                    SpatialMappingManager.Instance.DrawVisualMeshes = true;
                    SpatialMappingDeformation.Instance.ResetGlobalRendering();
                    SpatialMappingManager.Instance.StartObserver();
                }
                break;
            case AppState.WaitingForStageTransform:
                // Now if we have the stage transform we are ready to go.
                if (HologramPlacement.Instance.GotTransform)
                {
                    CurrentAppState = AppState.Ready;
                    GestureManager.Instance.OverrideFocusedObject = shootHandler;
                }
                break;
        }
    }
}
```

* <span data-ttu-id="c9bec-307">在 [ **專案] 面板** 中，流覽至 [ **腳本** ] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="c9bec-307">In the **Project panel** navigate to the **Scripts** folder.</span></span>
* <span data-ttu-id="c9bec-308">按兩下 **HologramPlacement** 腳本，在 Visual Studio 中開啟它。</span><span class="sxs-lookup"><span data-stu-id="c9bec-308">Double-click the **HologramPlacement** script to open it in Visual Studio.</span></span>
* <span data-ttu-id="c9bec-309">使用以下列程式碼取代內容。</span><span class="sxs-lookup"><span data-stu-id="c9bec-309">Replace the contents with the code below.</span></span>

```cs
using UnityEngine;
using System.Collections.Generic;
using UnityEngine.Windows.Speech;
using Academy.HoloToolkit.Unity;
using Academy.HoloToolkit.Sharing;

public class HologramPlacement : Singleton<HologramPlacement>
{
    /// <summary>
    /// Tracks if we have been sent a transform for the model.
    /// The model is rendered relative to the actual anchor.
    /// </summary>
    public bool GotTransform { get; private set; }

    /// <summary>
    /// When the experience starts, we disable all of the rendering of the model.
    /// </summary>
    List<MeshRenderer> disabledRenderers = new List<MeshRenderer>();

    /// <summary>
    /// We use a voice command to enable moving the target.
    /// </summary>
    KeywordRecognizer keywordRecognizer;

    void Start()
    {
        // When we first start, we need to disable the model to avoid it obstructing the user picking a hat.
        DisableModel();

        // We care about getting updates for the model transform.
        CustomMessages.Instance.MessageHandlers[CustomMessages.TestMessageID.StageTransform] = this.OnStageTransform;

        // And when a new user join we will send the model transform we have.
        SharingSessionTracker.Instance.SessionJoined += Instance_SessionJoined;

        // And if the users want to reset the stage transform.
        CustomMessages.Instance.MessageHandlers[CustomMessages.TestMessageID.ResetStage] = this.OnResetStage;

        // Setup a keyword recognizer to enable resetting the target location.
        List<string> keywords = new List<string>();
        keywords.Add("Reset Target");
        keywordRecognizer = new KeywordRecognizer(keywords.ToArray());
        keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
        keywordRecognizer.Start();
    }

    /// <summary>
    /// When the keyword recognizer hears a command this will be called.  
    /// In this case we only have one keyword, which will re-enable moving the
    /// target.
    /// </summary>
    /// <param name="args">information to help route the voice command.</param>
    private void KeywordRecognizer_OnPhraseRecognized(PhraseRecognizedEventArgs args)
    {
        ResetStage();
    }

    /// <summary>
    /// Resets the stage transform, so users can place the target again.
    /// </summary>
    public void ResetStage()
    {
        GotTransform = false;

        // AppStateManager needs to know about this so that
        // the right objects get input routed to them.
        AppStateManager.Instance.ResetStage();

        // Other devices in the experience need to know about this as well.
        CustomMessages.Instance.SendResetStage();

        // And we need to reset the object to its start animation state.
        GetComponent<EnergyHubBase>().ResetAnimation();
    }

    /// <summary>
    /// When a new user joins we want to send them the relative transform for the model if we have it.
    /// </summary>
    /// <param name="sender"></param>
    /// <param name="e"></param>
    private void Instance_SessionJoined(object sender, SharingSessionTracker.SessionJoinedEventArgs e)
    {
        if (GotTransform)
        {
            CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
        }
    }

    /// <summary>
    /// Turns off all renderers for the model.
    /// </summary>
    void DisableModel()
    {
        foreach (MeshRenderer renderer in gameObject.GetComponentsInChildren<MeshRenderer>())
        {
            if (renderer.enabled)
            {
                renderer.enabled = false;
                disabledRenderers.Add(renderer);
            }
        }

        foreach (MeshCollider collider in gameObject.GetComponentsInChildren<MeshCollider>())
        {
            collider.enabled = false;
        }
    }

    /// <summary>
    /// Turns on all renderers that were disabled.
    /// </summary>
    void EnableModel()
    {
        foreach (MeshRenderer renderer in disabledRenderers)
        {
            renderer.enabled = true;
        }

        foreach (MeshCollider collider in gameObject.GetComponentsInChildren<MeshCollider>())
        {
            collider.enabled = true;
        }

        disabledRenderers.Clear();
    }


    void Update()
    {
        // Wait till users pick an avatar to enable renderers.
        if (disabledRenderers.Count > 0)
        {
            if (!PlayerAvatarStore.Instance.PickerActive &&
            ImportExportAnchorManager.Instance.AnchorEstablished)
            {
                // After which we want to start rendering.
                EnableModel();

                // And if we've already been sent the relative transform, we will use it.
                if (GotTransform)
                {
                    // This triggers the animation sequence for the model and
                    // puts the cool materials on the model.
                    GetComponent<EnergyHubBase>().SendMessage("OnSelect");
                }
            }
        }
        else if (GotTransform == false)
        {
            transform.position = Vector3.Lerp(transform.position, ProposeTransformPosition(), 0.2f);
        }
    }

    Vector3 ProposeTransformPosition()
    {
        Vector3 retval;
        // We need to know how many users are in the experience with good transforms.
        Vector3 cumulatedPosition = Camera.main.transform.position;
        int playerCount = 1;
        foreach (RemotePlayerManager.RemoteHeadInfo remoteHead in RemotePlayerManager.Instance.remoteHeadInfos)
        {
            if (remoteHead.Anchored && remoteHead.Active)
            {
                playerCount++;
                cumulatedPosition += remoteHead.HeadObject.transform.position;
            }
        }

        // If we have more than one player ...
        if (playerCount > 1)
        {
            // Put the transform in between the players.
            retval = cumulatedPosition / playerCount;
            RaycastHit hitInfo;

            // And try to put the transform on a surface below the midpoint of the players.
            if (Physics.Raycast(retval, Vector3.down, out hitInfo, 5, SpatialMappingManager.Instance.LayerMask))
            {
                retval = hitInfo.point;
            }
        }
        // If we are the only player, have the model act as the 'cursor' ...
        else
        {
            // We prefer to put the model on a real world surface.
            RaycastHit hitInfo;

            if (Physics.Raycast(Camera.main.transform.position, Camera.main.transform.forward, out hitInfo, 30, SpatialMappingManager.Instance.LayerMask))
            {
                retval = hitInfo.point;
            }
            else
            {
                // But if we don't have a ray that intersects the real world, just put the model 2m in
                // front of the user.
                retval = Camera.main.transform.position + Camera.main.transform.forward * 2;
            }
        }
        return retval;
    }

    public void OnSelect()
    {
        // Note that we have a transform.
        GotTransform = true;

        // And send it to our friends.
        CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
    }

    /// <summary>
    /// When a remote system has a transform for us, we'll get it here.
    /// </summary>
    /// <param name="msg"></param>
    void OnStageTransform(NetworkInMessage msg)
    {
        // We read the user ID but we don't use it here.
        msg.ReadInt64();

        transform.localPosition = CustomMessages.Instance.ReadVector3(msg);
        transform.localRotation = CustomMessages.Instance.ReadQuaternion(msg);

        // The first time, we'll want to send the message to the model to do its animation and
        // swap its materials.
        if (disabledRenderers.Count == 0 && GotTransform == false)
        {
            GetComponent<EnergyHubBase>().SendMessage("OnSelect");
        }

        GotTransform = true;
    }

    /// <summary>
    /// When a remote system has a transform for us, we'll get it here.
    /// </summary>
    void OnResetStage(NetworkInMessage msg)
    {
        GotTransform = false;

        GetComponent<EnergyHubBase>().ResetAnimation();
        AppStateManager.Instance.ResetStage();
    }
}
```

<span data-ttu-id="c9bec-310">**部署及享用**</span><span class="sxs-lookup"><span data-stu-id="c9bec-310">**Deploy and enjoy**</span></span>

* <span data-ttu-id="c9bec-311">建立專案，並將其部署到您的 HoloLens 裝置。</span><span class="sxs-lookup"><span data-stu-id="c9bec-311">Build and deploy the project to your HoloLens devices.</span></span>
* <span data-ttu-id="c9bec-312">當應用程式準備就緒時，請將其放在圓形中，並注意 EnergyHub 如何顯示在每個人的中心。</span><span class="sxs-lookup"><span data-stu-id="c9bec-312">When the app is ready, stand in a circle and notice how the EnergyHub appears in the center of everyone.</span></span>
* <span data-ttu-id="c9bec-313">點擊以放置 EnergyHub。</span><span class="sxs-lookup"><span data-stu-id="c9bec-313">Tap to place the EnergyHub.</span></span>
* <span data-ttu-id="c9bec-314">請嘗試語音命令「重設目標」來挑選 EnergyHub 備份，並以群組方式一起工作，以將全息圖移至新位置。</span><span class="sxs-lookup"><span data-stu-id="c9bec-314">Try the voice command 'Reset Target' to pick the EnergyHub back up and work together as a group to move the hologram to a new location.</span></span>

## <a name="chapter-6---real-world-physics"></a><span data-ttu-id="c9bec-315">第6章-Real-World 物理</span><span class="sxs-lookup"><span data-stu-id="c9bec-315">Chapter 6 - Real-World Physics</span></span>

>[!VIDEO https://www.youtube.com/embed/XNpQVSyXwMo]

<span data-ttu-id="c9bec-316">在本章中，我們將新增可從真實世界表面中跳動的全息影像。</span><span class="sxs-lookup"><span data-stu-id="c9bec-316">In this chapter we'll add holograms that bounce off real-world surfaces.</span></span> <span data-ttu-id="c9bec-317">觀賞您和您的朋友所推出的專案，看看您的空間填滿！</span><span class="sxs-lookup"><span data-stu-id="c9bec-317">Watch your space fill up with projects launched by both you and your friends!</span></span>

### <a name="objectives"></a><span data-ttu-id="c9bec-318">目標</span><span class="sxs-lookup"><span data-stu-id="c9bec-318">Objectives</span></span>

* <span data-ttu-id="c9bec-319">啟動炮彈，以將實際表面彈開。</span><span class="sxs-lookup"><span data-stu-id="c9bec-319">Launch projectiles that bounce off real-world surfaces.</span></span>
* <span data-ttu-id="c9bec-320">共用炮彈，讓其他玩家可以看到它們。</span><span class="sxs-lookup"><span data-stu-id="c9bec-320">Share the projectiles so other players can see them.</span></span>

### <a name="instructions"></a><span data-ttu-id="c9bec-321">指示</span><span class="sxs-lookup"><span data-stu-id="c9bec-321">Instructions</span></span>

* <span data-ttu-id="c9bec-322">**在階層中選取**[ **HologramCollection** ] 物件。</span><span class="sxs-lookup"><span data-stu-id="c9bec-322">In the **Hierarchy** select the **HologramCollection** object.</span></span>
* <span data-ttu-id="c9bec-323">在 [偵測 **器** ] 中按一下 [ **新增元件**]。</span><span class="sxs-lookup"><span data-stu-id="c9bec-323">In the **Inspector** click **Add Component**.</span></span>
* <span data-ttu-id="c9bec-324">在搜尋方塊中，輸入 **Projectile 啟動器**。</span><span class="sxs-lookup"><span data-stu-id="c9bec-324">In the search box, type **Projectile Launcher**.</span></span> <span data-ttu-id="c9bec-325">選取搜尋結果。</span><span class="sxs-lookup"><span data-stu-id="c9bec-325">Select the search result.</span></span>

<span data-ttu-id="c9bec-326">**部署及享用**</span><span class="sxs-lookup"><span data-stu-id="c9bec-326">**Deploy and enjoy**</span></span>

* <span data-ttu-id="c9bec-327">建立並部署到您的 HoloLens 裝置。</span><span class="sxs-lookup"><span data-stu-id="c9bec-327">Build and deploy to your HoloLens devices.</span></span>
* <span data-ttu-id="c9bec-328">當應用程式在所有裝置上執行時，請執行點一下以在真實世界表面上啟動 projectile。</span><span class="sxs-lookup"><span data-stu-id="c9bec-328">When the app is running on all devices, perform an air-tap to launch projectile at real world surfaces.</span></span>
* <span data-ttu-id="c9bec-329">查看當 projectile 與另一個玩家的頭像衝突時，會發生什麼事！</span><span class="sxs-lookup"><span data-stu-id="c9bec-329">See what happens when your projectile collides with another player's avatar!</span></span>

## <a name="chapter-7---grand-finale"></a><span data-ttu-id="c9bec-330">第7章-總計 Finale</span><span class="sxs-lookup"><span data-stu-id="c9bec-330">Chapter 7 - Grand Finale</span></span>

>[!VIDEO https://www.youtube.com/embed/kDUPUvZEqRg]

<span data-ttu-id="c9bec-331">在本章中，我們將發現只能透過共同作業探索的入口網站。</span><span class="sxs-lookup"><span data-stu-id="c9bec-331">In this chapter, we'll uncover a portal that can only be discovered with collaboration.</span></span>

### <a name="objectives"></a><span data-ttu-id="c9bec-332">目標</span><span class="sxs-lookup"><span data-stu-id="c9bec-332">Objectives</span></span>

* <span data-ttu-id="c9bec-333">共同作業以在錨點上啟動足夠的炮彈來發現秘密入口網站！</span><span class="sxs-lookup"><span data-stu-id="c9bec-333">Work together to launch enough projectiles at the anchor to uncover a secret portal!</span></span>

### <a name="instructions"></a><span data-ttu-id="c9bec-334">指示</span><span class="sxs-lookup"><span data-stu-id="c9bec-334">Instructions</span></span>

* <span data-ttu-id="c9bec-335">在 [ **專案] 面板** 中，流覽至 [ **全息** 全像] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="c9bec-335">In the **Project panel** navigate to the **Holograms** folder.</span></span>
* <span data-ttu-id="c9bec-336">將 **Underworld** 資產拖放為 HologramCollection 的 **子** 系。</span><span class="sxs-lookup"><span data-stu-id="c9bec-336">Drag and drop the **Underworld** asset as a **child of HologramCollection**.</span></span>
* <span data-ttu-id="c9bec-337">選取 **HologramCollection** 後，按一下 [**檢查**] 中的 [**新增元件**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="c9bec-337">With **HologramCollection** selected, click the **Add Component** button in the **Inspector**.</span></span>
* <span data-ttu-id="c9bec-338">在功能表的 [搜尋] 方塊中，輸入 **ExplodeTarget**。</span><span class="sxs-lookup"><span data-stu-id="c9bec-338">In the menu, type in the search box **ExplodeTarget**.</span></span> <span data-ttu-id="c9bec-339">選取搜尋結果。</span><span class="sxs-lookup"><span data-stu-id="c9bec-339">Select the search result.</span></span>
* <span data-ttu-id="c9bec-340">選取 **HologramCollection** 後，從階層中，將 **EnergyHub** **物件拖曳至** 偵測 **器** 中的 **目標** 欄位。</span><span class="sxs-lookup"><span data-stu-id="c9bec-340">With **HologramCollection** selected, from the **Hierarchy** drag the **EnergyHub** object to the **Target** field in the **Inspector**.</span></span>
* <span data-ttu-id="c9bec-341">選取 **HologramCollection** 後，從階層中，將 **Underworld** **物件拖曳至** 偵測 **器** 中的 [ **Underworld** ] 欄位。</span><span class="sxs-lookup"><span data-stu-id="c9bec-341">With **HologramCollection** selected, from the **Hierarchy** drag the **Underworld** object to the **Underworld** field in the **Inspector**.</span></span>

<span data-ttu-id="c9bec-342">**部署及享用**</span><span class="sxs-lookup"><span data-stu-id="c9bec-342">**Deploy and enjoy**</span></span>

* <span data-ttu-id="c9bec-343">建立並部署到您的 HoloLens 裝置。</span><span class="sxs-lookup"><span data-stu-id="c9bec-343">Build and deploy to your HoloLens devices.</span></span>
* <span data-ttu-id="c9bec-344">當應用程式啟動時，請共同合作，以在 EnergyHub 上啟動炮彈。</span><span class="sxs-lookup"><span data-stu-id="c9bec-344">When the app has launched, collaborate together to launch projectiles at the EnergyHub.</span></span>
* <span data-ttu-id="c9bec-345">當 underworld 出現時，請在 underworld 機器人上啟動炮彈 (按下機器人三次，以提供更有趣的) 。</span><span class="sxs-lookup"><span data-stu-id="c9bec-345">When the underworld appears, launch projectiles at underworld robots (hit a robot three times for extra fun).</span></span>