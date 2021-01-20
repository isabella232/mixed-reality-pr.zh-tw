---
title: MR Spatial 220 - 空間音效
description: 遵循此程式碼逐步解說，使用 Unity、Visual Studio 和 HoloLens 來學習空間音效概念的詳細資料。
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit、mixedrealitytoolkit、mixedrealitytoolkit-unity、學術、教學課程、空間音效、HoloLens、混合現實學院、unity、混合現實耳機、windows Mixed Reality 耳機、虛擬實境耳機、Windows 10
ms.openlocfilehash: da130a5a93ec261d2e767874faa31dbc50d51b12
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/20/2021
ms.locfileid: "98582759"
---
# <a name="mr-spatial-220-spatial-sound"></a><span data-ttu-id="aa5be-104">MR Spatial 220：空間音效</span><span class="sxs-lookup"><span data-stu-id="aa5be-104">MR Spatial 220: Spatial sound</span></span>

>[!NOTE]
><span data-ttu-id="aa5be-105">混合實境學院教學課程的設計是以 HoloLens (第 1 代) 和混合實境沉浸式頭戴裝置為準。</span><span class="sxs-lookup"><span data-stu-id="aa5be-105">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="aa5be-106">因此，對於仍在尋找這些裝置開發指引的開發人員而言，我們覺得這些教學課程很重要。</span><span class="sxs-lookup"><span data-stu-id="aa5be-106">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="aa5be-107">這些教學課程 **_不會_** 使用用於 HoloLens 2 的最新工具組或互動進行更新。</span><span class="sxs-lookup"><span data-stu-id="aa5be-107">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="aa5be-108">系統會保留這些資訊，以繼續在支援的裝置上運作。</span><span class="sxs-lookup"><span data-stu-id="aa5be-108">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="aa5be-109">已針對 HoloLens 2 公佈[一系列新的教學課程](./mr-learning-base-01.md)。</span><span class="sxs-lookup"><span data-stu-id="aa5be-109">[A new series of tutorials](./mr-learning-base-01.md) has been posted for HoloLens 2.</span></span>

<span data-ttu-id="aa5be-110">[空間音效](../../../design/spatial-sound.md) breathes 生活進入全像全球，並讓他們在世界各地都存在。</span><span class="sxs-lookup"><span data-stu-id="aa5be-110">[Spatial sound](../../../design/spatial-sound.md) breathes life into holograms and gives them presence in our world.</span></span> <span data-ttu-id="aa5be-111">全像投影是由光線和音效所組成，如果您似乎無法看見您的全像影像，空間音效可以協助您找到它們。</span><span class="sxs-lookup"><span data-stu-id="aa5be-111">Holograms are composed of both light and sound, and if you happen to lose sight of your holograms, spatial sound can help you find them.</span></span> <span data-ttu-id="aa5be-112">空間音效與您在無線電上聽到的一般音效不一樣，它是位於3D 空間的音效。</span><span class="sxs-lookup"><span data-stu-id="aa5be-112">Spatial sound is not like the typical sound that you would hear on the radio, it is sound that is positioned in 3D space.</span></span> <span data-ttu-id="aa5be-113">有了空間音效，您就可以讓像是在您後方、您或甚至是在您的頭上的全像投影一樣：</span><span class="sxs-lookup"><span data-stu-id="aa5be-113">With spatial sound, you can make holograms sound like they're behind you, next to you, or even on your head!</span></span> <span data-ttu-id="aa5be-114">在此課程中，您將會：</span><span class="sxs-lookup"><span data-stu-id="aa5be-114">In this course, you will:</span></span>

* <span data-ttu-id="aa5be-115">設定您的開發環境以使用 Microsoft 空間音效。</span><span class="sxs-lookup"><span data-stu-id="aa5be-115">Configure your development environment to use Microsoft Spatial Sound.</span></span>
* <span data-ttu-id="aa5be-116">使用空間音效來增強互動。</span><span class="sxs-lookup"><span data-stu-id="aa5be-116">Use Spatial Sound to enhance interactions.</span></span>
* <span data-ttu-id="aa5be-117">使用空間音效搭配 [空間對應](../../../design/spatial-mapping.md)。</span><span class="sxs-lookup"><span data-stu-id="aa5be-117">Use Spatial Sound in conjunction with [Spatial Mapping](../../../design/spatial-mapping.md).</span></span>
* <span data-ttu-id="aa5be-118">瞭解音效設計和混合最佳做法。</span><span class="sxs-lookup"><span data-stu-id="aa5be-118">Understand sound design and mixing best practices.</span></span>
* <span data-ttu-id="aa5be-119">使用音效強化特殊效果，並讓使用者進入混合現實世界。</span><span class="sxs-lookup"><span data-stu-id="aa5be-119">Use sound to enhance special effects and bring the user into the Mixed Reality world.</span></span>

## <a name="device-support"></a><span data-ttu-id="aa5be-120">裝置支援</span><span class="sxs-lookup"><span data-stu-id="aa5be-120">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="aa5be-121">課程</span><span class="sxs-lookup"><span data-stu-id="aa5be-121">Course</span></span></th><th style="width:150px"> <span data-ttu-id="aa5be-122"><a href="/hololens/hololens1-hardware">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="aa5be-122"><a href="/hololens/hololens1-hardware">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="aa5be-123"><a href="../../../discover/immersive-headset-hardware-details.md">沉浸式頭戴裝置</a></span><span class="sxs-lookup"><span data-stu-id="aa5be-123"><a href="../../../discover/immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="aa5be-124">MR Spatial 220：空間音效</span><span class="sxs-lookup"><span data-stu-id="aa5be-124">MR Spatial 220: Spatial sound</span></span></td><td style="text-align: center;"> <span data-ttu-id="aa5be-125">✔️</span><span class="sxs-lookup"><span data-stu-id="aa5be-125">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="aa5be-126">✔️</span><span class="sxs-lookup"><span data-stu-id="aa5be-126">✔️</span></span></td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="aa5be-127">在您開始使用 Intune 之前</span><span class="sxs-lookup"><span data-stu-id="aa5be-127">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="aa5be-128">必要條件</span><span class="sxs-lookup"><span data-stu-id="aa5be-128">Prerequisites</span></span>

* <span data-ttu-id="aa5be-129">[已安裝正確工具](../../../develop/install-the-tools.md)的 Windows 10 電腦。</span><span class="sxs-lookup"><span data-stu-id="aa5be-129">A Windows 10 PC configured with the correct [tools installed](../../../develop/install-the-tools.md).</span></span>
* <span data-ttu-id="aa5be-130">一些基本的 c # 程式設計功能。</span><span class="sxs-lookup"><span data-stu-id="aa5be-130">Some basic C# programming ability.</span></span>
* <span data-ttu-id="aa5be-131">您應已完成 [MR 基本的 101](../../../develop/unity/tutorials/holograms-101.md)。</span><span class="sxs-lookup"><span data-stu-id="aa5be-131">You should have completed [MR Basics 101](../../../develop/unity/tutorials/holograms-101.md).</span></span>
* <span data-ttu-id="aa5be-132">[針對開發設定](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)的 HoloLens 裝置。</span><span class="sxs-lookup"><span data-stu-id="aa5be-132">A HoloLens device [configured for development](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="aa5be-133">專案檔</span><span class="sxs-lookup"><span data-stu-id="aa5be-133">Project files</span></span>

* <span data-ttu-id="aa5be-134">下載專案 [所需的](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-220-SpatialSound.zip) 檔案。</span><span class="sxs-lookup"><span data-stu-id="aa5be-134">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-220-SpatialSound.zip) required by the project.</span></span> <span data-ttu-id="aa5be-135">需要 Unity 2017.2 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="aa5be-135">Requires Unity 2017.2 or later.</span></span>
  * <span data-ttu-id="aa5be-136">如果您仍然需要 Unity 5.6 支援，請使用 [此版本](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-220.zip)。</span><span class="sxs-lookup"><span data-stu-id="aa5be-136">If you still need Unity 5.6 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-220.zip).</span></span> <span data-ttu-id="aa5be-137">此版本可能不再是最新版本。</span><span class="sxs-lookup"><span data-stu-id="aa5be-137">This release may no longer be up-to-date.</span></span>
  * <span data-ttu-id="aa5be-138">如果您仍然需要 Unity 5.5 支援，請使用 [此版本](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-220.zip)。</span><span class="sxs-lookup"><span data-stu-id="aa5be-138">If you still need Unity 5.5 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-220.zip).</span></span> <span data-ttu-id="aa5be-139">此版本可能不再是最新版本。</span><span class="sxs-lookup"><span data-stu-id="aa5be-139">This release may no longer be up-to-date.</span></span>
  * <span data-ttu-id="aa5be-140">如果您仍然需要 Unity 5.4 支援，請使用 [此版本](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-220.zip)。</span><span class="sxs-lookup"><span data-stu-id="aa5be-140">If you still need Unity 5.4 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-220.zip).</span></span> <span data-ttu-id="aa5be-141">此版本可能不再是最新版本。</span><span class="sxs-lookup"><span data-stu-id="aa5be-141">This release may no longer be up-to-date.</span></span>
* <span data-ttu-id="aa5be-142">取消將檔案封存到您的桌面或其他易於觸及的位置。</span><span class="sxs-lookup"><span data-stu-id="aa5be-142">Un-archive the files to your desktop or other easy to reach location.</span></span>

>[!NOTE]
><span data-ttu-id="aa5be-143">如果您想要在下載之前查看原始程式碼， [可在 GitHub 上](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-220-SpatialSound)取得。</span><span class="sxs-lookup"><span data-stu-id="aa5be-143">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-220-SpatialSound).</span></span>

### <a name="errata-and-notes"></a><span data-ttu-id="aa5be-144">勘誤表和記事</span><span class="sxs-lookup"><span data-stu-id="aa5be-144">Errata and Notes</span></span>

* <span data-ttu-id="aa5be-145">您必須在 [工具]-[>選項] 下的 Visual Studio 中停用 [啟用 Just My Code] (*未* 核取) ，才能在程式碼中叫用中斷點。</span><span class="sxs-lookup"><span data-stu-id="aa5be-145">"Enable Just My Code" needs to be disabled (*unchecked*) in Visual Studio under Tools->Options->Debugging in order to hit breakpoints in your code.</span></span>

## <a name="chapter-1---unity-setup"></a><span data-ttu-id="aa5be-146">第1章-Unity 設定</span><span class="sxs-lookup"><span data-stu-id="aa5be-146">Chapter 1 - Unity Setup</span></span>

### <a name="objectives"></a><span data-ttu-id="aa5be-147">目標</span><span class="sxs-lookup"><span data-stu-id="aa5be-147">Objectives</span></span>

* <span data-ttu-id="aa5be-148">變更 Unity 的音效設定以使用 Microsoft 空間音效。</span><span class="sxs-lookup"><span data-stu-id="aa5be-148">Change Unity's sound configuration to use Microsoft Spatial Sound.</span></span>
* <span data-ttu-id="aa5be-149">將3D 音效新增至 Unity 中的物件。</span><span class="sxs-lookup"><span data-stu-id="aa5be-149">Add 3D sound to an object in Unity.</span></span>

### <a name="instructions"></a><span data-ttu-id="aa5be-150">指示</span><span class="sxs-lookup"><span data-stu-id="aa5be-150">Instructions</span></span>

* <span data-ttu-id="aa5be-151">啟動 Unity。</span><span class="sxs-lookup"><span data-stu-id="aa5be-151">Start Unity.</span></span>
* <span data-ttu-id="aa5be-152">選取 [開啟]  。</span><span class="sxs-lookup"><span data-stu-id="aa5be-152">Select **Open**.</span></span>
* <span data-ttu-id="aa5be-153">流覽至您的桌面，並尋找您先前取消封存的資料夾。</span><span class="sxs-lookup"><span data-stu-id="aa5be-153">Navigate to your Desktop and find the folder you previously un-archived.</span></span>
* <span data-ttu-id="aa5be-154">按一下 [ **Starting\Decibel** ] 資料夾，然後按下 [ **選取資料夾** ] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="aa5be-154">Click on the **Starting\Decibel** folder and then press the **Select Folder** button.</span></span>
* <span data-ttu-id="aa5be-155">等候專案在 Unity 中載入。</span><span class="sxs-lookup"><span data-stu-id="aa5be-155">Wait for the project to load in Unity.</span></span>
* <span data-ttu-id="aa5be-156">在 [ **專案** ] 面板中，開啟 [ **Scenes\Decibel.unity**]。</span><span class="sxs-lookup"><span data-stu-id="aa5be-156">In the **Project** panel, open **Scenes\Decibel.unity**.</span></span>
* <span data-ttu-id="aa5be-157">**在 [階層**] 面板中，展開 [ **HologramCollection** ]，然後選取 [ **P0LY**]。</span><span class="sxs-lookup"><span data-stu-id="aa5be-157">In the **Hierarchy** panel, expand **HologramCollection** and select **P0LY**.</span></span>
* <span data-ttu-id="aa5be-158">在 [偵測器] 中，展開 [ **spatialize** ]，並注意 [沒有 **Spatialize** ] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="aa5be-158">In the Inspector, expand **AudioSource** and notice that there is no **Spatialize** check box.</span></span>

<span data-ttu-id="aa5be-159">根據預設，Unity 不會載入空間定位器外掛程式。</span><span class="sxs-lookup"><span data-stu-id="aa5be-159">By default, Unity does not load a spatializer plugin.</span></span> <span data-ttu-id="aa5be-160">下列步驟將會在專案中啟用空間音效。</span><span class="sxs-lookup"><span data-stu-id="aa5be-160">The following steps will enable Spatial Sound in the project.</span></span>

* <span data-ttu-id="aa5be-161">在 Unity 的頂端功能表中，移至 [ **編輯 > 專案設定 > 音訊**]。</span><span class="sxs-lookup"><span data-stu-id="aa5be-161">In Unity's top menu, go to **Edit > Project Settings > Audio**.</span></span>
* <span data-ttu-id="aa5be-162">尋找 [ **空間定位器外掛程式** ] 下拉式清單，然後選取 [ **MS HRTF 空間定位器**]。</span><span class="sxs-lookup"><span data-stu-id="aa5be-162">Find the **Spatializer Plugin** dropdown, and select **MS HRTF Spatializer**.</span></span>
* <span data-ttu-id="aa5be-163">**在 [階層**] 面板中，選取 [ **HologramCollection > P0LY**]。</span><span class="sxs-lookup"><span data-stu-id="aa5be-163">In the **Hierarchy** panel, select **HologramCollection > P0LY**.</span></span>
* <span data-ttu-id="aa5be-164">在 [偵測 **器** ] 面板中，尋找 **音訊來源** 元件。</span><span class="sxs-lookup"><span data-stu-id="aa5be-164">In the **Inspector** panel, find the **Audio Source** component.</span></span>
* <span data-ttu-id="aa5be-165">核取 [ **Spatialize** ] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="aa5be-165">Check the **Spatialize** checkbox.</span></span>
* <span data-ttu-id="aa5be-166">將 **空間 Blend** 滑杆拖曳至 **3d**，或在編輯方塊中輸入 **1** 。</span><span class="sxs-lookup"><span data-stu-id="aa5be-166">Drag the **Spatial Blend** slider all the way to **3D**, or enter **1** in the edit box.</span></span>

<span data-ttu-id="aa5be-167">我們現在會在 Unity 中建立專案，並在 Visual Studio 中設定解決方案。</span><span class="sxs-lookup"><span data-stu-id="aa5be-167">We will now build the project in Unity and configure the solution in Visual Studio.</span></span>

1. <span data-ttu-id="aa5be-168">在 Unity 中，選取 [ **File > Build Settings**]。</span><span class="sxs-lookup"><span data-stu-id="aa5be-168">In Unity, select **File > Build Settings**.</span></span>
2. <span data-ttu-id="aa5be-169">按一下 [ **新增開啟場景** ] 以加入場景。</span><span class="sxs-lookup"><span data-stu-id="aa5be-169">Click **Add Open Scenes** to add the scene.</span></span>
3. <span data-ttu-id="aa5be-170">在 [**平臺**] 清單中選取 **通用 Windows 平臺**，然後按一下 [**切換平臺**]。</span><span class="sxs-lookup"><span data-stu-id="aa5be-170">Select **Universal Windows Platform** in the **Platform** list and click **Switch Platform**.</span></span>
4. <span data-ttu-id="aa5be-171">如果您是特別針對 HoloLens 進行開發，請將 **目標裝置** 設定為 **hololens**。</span><span class="sxs-lookup"><span data-stu-id="aa5be-171">If you're specifically developing for HoloLens, set **Target device** to **HoloLens**.</span></span> <span data-ttu-id="aa5be-172">否則，請將它保留在 **任何裝置** 上。</span><span class="sxs-lookup"><span data-stu-id="aa5be-172">Otherwise, leave it on **Any device**.</span></span>
5. <span data-ttu-id="aa5be-173">請確定 **組建類型** 設定為 [ **D3D** ]，並將 [ **Sdk** ] 設定為 [ **最新安裝** 的 (，其應為 SDK 16299 或更新版本的) 。</span><span class="sxs-lookup"><span data-stu-id="aa5be-173">Ensure **Build Type** is set to **D3D** and **SDK** is set to **Latest installed** (which should be SDK 16299 or newer).</span></span>
6. <span data-ttu-id="aa5be-174">按一下 [建置]。</span><span class="sxs-lookup"><span data-stu-id="aa5be-174">Click **Build**.</span></span>
7. <span data-ttu-id="aa5be-175">建立名為 "App" 的 **新資料夾** 。</span><span class="sxs-lookup"><span data-stu-id="aa5be-175">Create a **New Folder** named "App".</span></span>
8. <span data-ttu-id="aa5be-176">按一下 **應用程式** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="aa5be-176">Single click the **App** folder.</span></span>
9. <span data-ttu-id="aa5be-177">按下 [ **選取資料夾**]。</span><span class="sxs-lookup"><span data-stu-id="aa5be-177">Press **Select Folder**.</span></span>

<span data-ttu-id="aa5be-178">當 Unity 完成時，將會出現檔案總管視窗。</span><span class="sxs-lookup"><span data-stu-id="aa5be-178">When Unity is done, a File Explorer window will appear.</span></span>

1. <span data-ttu-id="aa5be-179">開啟 **應用程式** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="aa5be-179">Open the **App** folder.</span></span>
2. <span data-ttu-id="aa5be-180">開啟 [ **分貝 Visual Studio] 解決方案**。</span><span class="sxs-lookup"><span data-stu-id="aa5be-180">Open the **Decibel Visual Studio Solution**.</span></span>

<span data-ttu-id="aa5be-181">如果要部署到 HoloLens：</span><span class="sxs-lookup"><span data-stu-id="aa5be-181">If deploying to HoloLens:</span></span>

1. <span data-ttu-id="aa5be-182">使用 Visual Studio 中的頂端工具列，將目標從 Debug 變更為 **Release** ，以及從 ARM 變更為 **x86**。</span><span class="sxs-lookup"><span data-stu-id="aa5be-182">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x86**.</span></span>
2. <span data-ttu-id="aa5be-183">按一下 [本機電腦] 按鈕旁的下拉箭號，然後選取 [ **遠端電腦**]。</span><span class="sxs-lookup"><span data-stu-id="aa5be-183">Click on the drop down arrow next to the Local Machine button, and select **Remote Machine**.</span></span>
3. <span data-ttu-id="aa5be-184">輸入 **您的 HoloLens 裝置 IP 位址** ，並將驗證模式設定為 **通用 (未加密的通訊協定)**。</span><span class="sxs-lookup"><span data-stu-id="aa5be-184">Enter **your HoloLens device IP address** and set Authentication Mode to **Universal (Unencrypted Protocol)**.</span></span> <span data-ttu-id="aa5be-185">按一下 [選取]。</span><span class="sxs-lookup"><span data-stu-id="aa5be-185">Click **Select**.</span></span> <span data-ttu-id="aa5be-186">如果您不知道您的裝置 IP 位址，請查看 [ **設定] > Network & Internet > Advanced 選項**。</span><span class="sxs-lookup"><span data-stu-id="aa5be-186">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options**.</span></span>
4. <span data-ttu-id="aa5be-187">在頂端功能表列中，按一下 [ **Debug-> 啟動但不進行調試** ]，或按 **Ctrl + F5**。</span><span class="sxs-lookup"><span data-stu-id="aa5be-187">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span> <span data-ttu-id="aa5be-188">如果這是您第一次部署至您的裝置，您必須將 [它與 Visual Studio 配對](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#pairing-your-device)。</span><span class="sxs-lookup"><span data-stu-id="aa5be-188">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#pairing-your-device).</span></span>

<span data-ttu-id="aa5be-189">如果部署到沉浸式耳機：</span><span class="sxs-lookup"><span data-stu-id="aa5be-189">If deploying to an immersive headset:</span></span>

1. <span data-ttu-id="aa5be-190">使用 Visual Studio 中的頂端工具列，將目標從 Debug 變更為 **Release** ，以及從 ARM 變更為 **x64**。</span><span class="sxs-lookup"><span data-stu-id="aa5be-190">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x64**.</span></span>
2. <span data-ttu-id="aa5be-191">請確定部署目標設定為 [ **本機電腦**]。</span><span class="sxs-lookup"><span data-stu-id="aa5be-191">Make sure the deployment target is set to **Local Machine**.</span></span>
3. <span data-ttu-id="aa5be-192">在頂端功能表列中，按一下 [ **Debug-> 啟動但不進行調試** ]，或按 **Ctrl + F5**。</span><span class="sxs-lookup"><span data-stu-id="aa5be-192">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>

## <a name="chapter-2---spatial-sound-and-interaction"></a><span data-ttu-id="aa5be-193">第2章-空間音效和互動</span><span class="sxs-lookup"><span data-stu-id="aa5be-193">Chapter 2 - Spatial Sound and Interaction</span></span>

### <a name="objectives"></a><span data-ttu-id="aa5be-194">目標</span><span class="sxs-lookup"><span data-stu-id="aa5be-194">Objectives</span></span>

* <span data-ttu-id="aa5be-195">使用音效增強全像配音。</span><span class="sxs-lookup"><span data-stu-id="aa5be-195">Enhance hologram realism using sound.</span></span>
* <span data-ttu-id="aa5be-196">使用音效指示使用者的注視。</span><span class="sxs-lookup"><span data-stu-id="aa5be-196">Direct the user's gaze using sound.</span></span>
* <span data-ttu-id="aa5be-197">使用音效提供手勢意見反應。</span><span class="sxs-lookup"><span data-stu-id="aa5be-197">Provide gesture feedback using sound.</span></span>

### <a name="part-1---enhancing-realism"></a><span data-ttu-id="aa5be-198">第1部分-增強真實感</span><span class="sxs-lookup"><span data-stu-id="aa5be-198">Part 1 - Enhancing Realism</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="aa5be-199">重要概念</span><span class="sxs-lookup"><span data-stu-id="aa5be-199">Key Concepts</span></span>

* <span data-ttu-id="aa5be-200">Spatialize 全像音效。</span><span class="sxs-lookup"><span data-stu-id="aa5be-200">Spatialize hologram sounds.</span></span>
* <span data-ttu-id="aa5be-201">音效來源應放置於全息圖的適當位置。</span><span class="sxs-lookup"><span data-stu-id="aa5be-201">Sound sources should be placed at an appropriate location on the hologram.</span></span>

<span data-ttu-id="aa5be-202">音效的適當位置將會取決於全像影像。</span><span class="sxs-lookup"><span data-stu-id="aa5be-202">The appropriate location for the sound is going to depend on the hologram.</span></span> <span data-ttu-id="aa5be-203">比方說，如果全息圖是人類的，則音效來源應該位於嘴附近，而不是距離。</span><span class="sxs-lookup"><span data-stu-id="aa5be-203">For example, if the hologram is of a human, the sound source should be located near the mouth and not the feet.</span></span>

#### <a name="instructions"></a><span data-ttu-id="aa5be-204">指示</span><span class="sxs-lookup"><span data-stu-id="aa5be-204">Instructions</span></span>

<span data-ttu-id="aa5be-205">下列指示會將 hrtf 音效附加至全像影像。</span><span class="sxs-lookup"><span data-stu-id="aa5be-205">The following instructions will attach a spatialized sound to a hologram.</span></span>

* <span data-ttu-id="aa5be-206">**在 [階層**] 面板中，展開 [ **HologramCollection** ]，然後選取 [ **P0LY**]。</span><span class="sxs-lookup"><span data-stu-id="aa5be-206">In the **Hierarchy** panel, expand **HologramCollection** and select **P0LY**.</span></span>
* <span data-ttu-id="aa5be-207">在 [偵測 **器** ] 面板的 [ **spatialize**] 中，按一下 [ **AudioClip** ] 旁的圓形，然後從快顯視窗中選取 [ **PolyHover** ]。</span><span class="sxs-lookup"><span data-stu-id="aa5be-207">In the **Inspector** panel, in the **AudioSource**, click the circle next to **AudioClip** and select **PolyHover** from the pop-up.</span></span>
* <span data-ttu-id="aa5be-208">按一下 [ **輸出** ] 旁的圓形，然後從快顯視窗中選取 [ **SoundEffects** ]。</span><span class="sxs-lookup"><span data-stu-id="aa5be-208">Click the circle next to **Output** and select **SoundEffects** from the pop-up.</span></span>

<span data-ttu-id="aa5be-209">專案分貝會使用 Unity **AudioMixer** 元件來調整音效群組的音效等級。</span><span class="sxs-lookup"><span data-stu-id="aa5be-209">Project Decibel uses a Unity **AudioMixer** component to enable adjusting sound levels for groups of sounds.</span></span> <span data-ttu-id="aa5be-210">藉由以這種方式將聲音分組，可以調整整體磁片區，同時維持每個音效的相對音量。</span><span class="sxs-lookup"><span data-stu-id="aa5be-210">By grouping sounds this way, the overall volume can be adjusted while maintaining the relative volume of each sound.</span></span>

* <span data-ttu-id="aa5be-211">在 **spatialize** 中，展開 [ **3d 音效設定**]。</span><span class="sxs-lookup"><span data-stu-id="aa5be-211">In the **AudioSource**, expand **3D Sound Settings**.</span></span>
* <span data-ttu-id="aa5be-212">將 **Doppler 層級** 設定為 **0**。</span><span class="sxs-lookup"><span data-stu-id="aa5be-212">Set **Doppler Level** to **0**.</span></span>

<span data-ttu-id="aa5be-213">將 Doppler 層級設定為 [零] 會停用 (由全像影像或使用者) 的移動所造成的音調變化。</span><span class="sxs-lookup"><span data-stu-id="aa5be-213">Setting Doppler level to zero disables changes in pitch caused by motion (either of the hologram or the user).</span></span> <span data-ttu-id="aa5be-214">Doppler 的典型範例是快速移動的汽車。</span><span class="sxs-lookup"><span data-stu-id="aa5be-214">A classic example of Doppler is a fast-moving car.</span></span> <span data-ttu-id="aa5be-215">當汽車採用固定的接聽程式時，引擎的音調也會上升。</span><span class="sxs-lookup"><span data-stu-id="aa5be-215">As the car approaches a stationary listener, the pitch of the engine rises.</span></span> <span data-ttu-id="aa5be-216">當它通過接聽程式時，會降低距離。</span><span class="sxs-lookup"><span data-stu-id="aa5be-216">When it passes the listener, the pitch lowers with distance.</span></span>

### <a name="part-2---directing-the-users-gaze"></a><span data-ttu-id="aa5be-217">第2部分-引導使用者的注視</span><span class="sxs-lookup"><span data-stu-id="aa5be-217">Part 2 - Directing the User's Gaze</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="aa5be-218">重要概念</span><span class="sxs-lookup"><span data-stu-id="aa5be-218">Key Concepts</span></span>

* <span data-ttu-id="aa5be-219">使用音效呼叫重要的全像投影。</span><span class="sxs-lookup"><span data-stu-id="aa5be-219">Use sound to call attention to important holograms.</span></span>
* <span data-ttu-id="aa5be-220">此耳可協助引導眼睛的外觀。</span><span class="sxs-lookup"><span data-stu-id="aa5be-220">The ears help direct where the eyes should look.</span></span>
* <span data-ttu-id="aa5be-221">大腦有一些學習的期望。</span><span class="sxs-lookup"><span data-stu-id="aa5be-221">The brain has some learned expectations.</span></span>

<span data-ttu-id="aa5be-222">瞭解預期的其中一個範例是，鳥通常會高於人類的標題。</span><span class="sxs-lookup"><span data-stu-id="aa5be-222">One example of learned expectations is that birds are generally above the heads of humans.</span></span> <span data-ttu-id="aa5be-223">如果使用者聽到鳥音效，他們的初始反應就是查閱。</span><span class="sxs-lookup"><span data-stu-id="aa5be-223">If a user hears a bird sound, their initial reaction is to look up.</span></span> <span data-ttu-id="aa5be-224">將鳥放在使用者的下方，可能會讓他們面對正確的音效方向，但根據預期需要查閱，找不到影像。</span><span class="sxs-lookup"><span data-stu-id="aa5be-224">Placing a bird below the user can lead to them facing the correct direction of the sound, but being unable to find the hologram based on the expectation of needing to look up.</span></span>

#### <a name="instructions"></a><span data-ttu-id="aa5be-225">指示</span><span class="sxs-lookup"><span data-stu-id="aa5be-225">Instructions</span></span>

<span data-ttu-id="aa5be-226">下列指示可讓 P0LY 在您後方隱藏，讓您可以使用音效找出全像影像。</span><span class="sxs-lookup"><span data-stu-id="aa5be-226">The following instructions enable P0LY to hide behind you, so that you can use sound to locate the hologram.</span></span>

* <span data-ttu-id="aa5be-227">**在 [階層**] 面板中，選取 [**管理員**]。</span><span class="sxs-lookup"><span data-stu-id="aa5be-227">In the **Hierarchy** panel, select **Managers**.</span></span>
* <span data-ttu-id="aa5be-228">在 [偵測 **器** ] 面板中，尋找 [ **語音輸入處理常式**]。</span><span class="sxs-lookup"><span data-stu-id="aa5be-228">In the **Inspector** panel, find **Speech Input Handler**.</span></span>
* <span data-ttu-id="aa5be-229">在 [ **語音輸入處理常式**] 中，展開 [ **移至隱藏**]。</span><span class="sxs-lookup"><span data-stu-id="aa5be-229">In **Speech Input Handler**, expand **Go Hide**.</span></span>
* <span data-ttu-id="aa5be-230">將 **函數** 變更為 **PolyActions. GoHide**。</span><span class="sxs-lookup"><span data-stu-id="aa5be-230">Change **No Function** to **PolyActions.GoHide**.</span></span>

![關鍵字：移至隱藏](images/gohide.png)

### <a name="part-3---gesture-feedback"></a><span data-ttu-id="aa5be-232">第3部分-手勢意見反應</span><span class="sxs-lookup"><span data-stu-id="aa5be-232">Part 3 - Gesture Feedback</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="aa5be-233">重要概念</span><span class="sxs-lookup"><span data-stu-id="aa5be-233">Key Concepts</span></span>

* <span data-ttu-id="aa5be-234">使用音效為使用者提供正面的手勢確認</span><span class="sxs-lookup"><span data-stu-id="aa5be-234">Provide the user with positive gesture confirmation using sound</span></span>
* <span data-ttu-id="aa5be-235">不要讓使用者過高的聲音變得太過</span><span class="sxs-lookup"><span data-stu-id="aa5be-235">Do not overwhelm the user - overly loud sounds get in the way</span></span>
* <span data-ttu-id="aa5be-236">微妙的音效效果最佳-請勿失色經驗</span><span class="sxs-lookup"><span data-stu-id="aa5be-236">Subtle sounds work best - do not overshadow the experience</span></span>

#### <a name="instructions"></a><span data-ttu-id="aa5be-237">指示</span><span class="sxs-lookup"><span data-stu-id="aa5be-237">Instructions</span></span>

* <span data-ttu-id="aa5be-238">**在 [階層**] 面板中，展開 [ **HologramCollection**]。</span><span class="sxs-lookup"><span data-stu-id="aa5be-238">In the **Hierarchy** panel, expand **HologramCollection**.</span></span>
* <span data-ttu-id="aa5be-239">展開 [ **EnergyHub** ]，然後選取 [ **基底**]。</span><span class="sxs-lookup"><span data-stu-id="aa5be-239">Expand **EnergyHub** and select **Base**.</span></span>
* <span data-ttu-id="aa5be-240">在 [偵測 **器** ] 面板中，按一下 [ **新增元件** ] 並加入 **手勢音效處理常式**。</span><span class="sxs-lookup"><span data-stu-id="aa5be-240">In the **Inspector** panel, click **Add Component** and add **Gesture Sound Handler**.</span></span>
* <span data-ttu-id="aa5be-241">在 [ **手勢音效處理常式**] 中，按一下 [ **導覽開始的剪輯** ] 和 [ **導覽更新的剪輯** ] 旁的圓形，然後從快顯視窗中選取 [ **RotateClick** ]。</span><span class="sxs-lookup"><span data-stu-id="aa5be-241">In **Gesture Sound Handler**, click the circle next to **Navigation Started Clip** and **Navigation Updated Clip** and select **RotateClick** from the pop-up for both.</span></span>
* <span data-ttu-id="aa5be-242">按兩下 [GestureSoundHandler] 以 Visual Studio 載入。</span><span class="sxs-lookup"><span data-stu-id="aa5be-242">Double click on "GestureSoundHandler" to load in Visual Studio.</span></span>

<span data-ttu-id="aa5be-243">手勢音效處理常式會執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="aa5be-243">Gesture Sound Handler performs the following tasks:</span></span>

* <span data-ttu-id="aa5be-244">建立並設定 **spatialize**。</span><span class="sxs-lookup"><span data-stu-id="aa5be-244">Create and configure an **AudioSource**.</span></span>
* <span data-ttu-id="aa5be-245">將 **spatialize** 放在適當 **GameObject** 的位置。</span><span class="sxs-lookup"><span data-stu-id="aa5be-245">Place the **AudioSource** at the location of the appropriate **GameObject**.</span></span>
* <span data-ttu-id="aa5be-246">播放與手勢相關聯的 **AudioClip** 。</span><span class="sxs-lookup"><span data-stu-id="aa5be-246">Plays the **AudioClip** associated with the gesture.</span></span>

#### <a name="build-and-deploy"></a><span data-ttu-id="aa5be-247">建置和部署</span><span class="sxs-lookup"><span data-stu-id="aa5be-247">Build and Deploy</span></span>

1. <span data-ttu-id="aa5be-248">在 Unity 中，選取 [ **File > Build Settings**]。</span><span class="sxs-lookup"><span data-stu-id="aa5be-248">In Unity, select **File > Build Settings**.</span></span>
2. <span data-ttu-id="aa5be-249">按一下 [建置]。</span><span class="sxs-lookup"><span data-stu-id="aa5be-249">Click **Build**.</span></span>
3. <span data-ttu-id="aa5be-250">按一下 **應用程式** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="aa5be-250">Single click the **App** folder.</span></span>
4. <span data-ttu-id="aa5be-251">按下 [ **選取資料夾**]。</span><span class="sxs-lookup"><span data-stu-id="aa5be-251">Press **Select Folder**.</span></span>

<span data-ttu-id="aa5be-252">確認工具列中顯示的是「發行」、「x86」、「x64」和「遠端裝置」。</span><span class="sxs-lookup"><span data-stu-id="aa5be-252">Check that the Toolbar says "Release", "x86" or "x64", and "Remote Device".</span></span> <span data-ttu-id="aa5be-253">如果沒有，這就是 Visual Studio 的編碼實例。</span><span class="sxs-lookup"><span data-stu-id="aa5be-253">If not, this is the coding instance of Visual Studio.</span></span> <span data-ttu-id="aa5be-254">您可能需要從應用程式資料夾重新開啟方案。</span><span class="sxs-lookup"><span data-stu-id="aa5be-254">You may need to re-open the solution from the App folder.</span></span>

* <span data-ttu-id="aa5be-255">出現提示時，請重載專案檔。</span><span class="sxs-lookup"><span data-stu-id="aa5be-255">If prompted, reload the project files.</span></span>
* <span data-ttu-id="aa5be-256">同樣地，從 Visual Studio 部署。</span><span class="sxs-lookup"><span data-stu-id="aa5be-256">As before, deploy from Visual Studio.</span></span>

<span data-ttu-id="aa5be-257">部署應用程式之後：</span><span class="sxs-lookup"><span data-stu-id="aa5be-257">After the application is deployed:</span></span>

* <span data-ttu-id="aa5be-258">觀察當您在 P0LY 上移動時的音效變化。</span><span class="sxs-lookup"><span data-stu-id="aa5be-258">Observe how the sound changes as you move around P0LY.</span></span>
* <span data-ttu-id="aa5be-259">說「 *Go 隱藏* 」讓 P0LY 移至您後方的位置。</span><span class="sxs-lookup"><span data-stu-id="aa5be-259">Say *"Go Hide"* to make P0LY move to a location behind you.</span></span> <span data-ttu-id="aa5be-260">依音效找出它。</span><span class="sxs-lookup"><span data-stu-id="aa5be-260">Find it by the sound.</span></span>
* <span data-ttu-id="aa5be-261">注視能源中樞的基底。</span><span class="sxs-lookup"><span data-stu-id="aa5be-261">Gaze at the base of the Energy Hub.</span></span> <span data-ttu-id="aa5be-262">您可以用滑鼠左鍵或向右拖曳來旋轉全像投影，然後留意一下按一下音效如何確認手勢。</span><span class="sxs-lookup"><span data-stu-id="aa5be-262">Tap and drag left or right to rotate the hologram and notice how the clicking sound confirms the gesture.</span></span>

<span data-ttu-id="aa5be-263">注意：有一個文字面板會與您一起標記。</span><span class="sxs-lookup"><span data-stu-id="aa5be-263">Note: There is a text panel that will tag-along with you.</span></span> <span data-ttu-id="aa5be-264">這將包含可在整個課程中使用的語音命令。</span><span class="sxs-lookup"><span data-stu-id="aa5be-264">This will contain the available voice commands that you can use throughout this course.</span></span>

## <a name="chapter-3---spatial-sound-and-spatial-mapping"></a><span data-ttu-id="aa5be-265">第3章-空間音效和空間對應</span><span class="sxs-lookup"><span data-stu-id="aa5be-265">Chapter 3 - Spatial Sound and Spatial Mapping</span></span>

### <a name="objectives"></a><span data-ttu-id="aa5be-266">目標</span><span class="sxs-lookup"><span data-stu-id="aa5be-266">Objectives</span></span>

* <span data-ttu-id="aa5be-267">使用音效確認全像全息和真實世界之間的互動。</span><span class="sxs-lookup"><span data-stu-id="aa5be-267">Confirm interaction between holograms and the real world using sound.</span></span>
* <span data-ttu-id="aa5be-268">使用實體世界遮蔽音效。</span><span class="sxs-lookup"><span data-stu-id="aa5be-268">Occlude sound using the physical world.</span></span>

### <a name="part-1---physical-world-interaction"></a><span data-ttu-id="aa5be-269">第1部分-實體世界互動</span><span class="sxs-lookup"><span data-stu-id="aa5be-269">Part 1 - Physical World Interaction</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="aa5be-270">重要概念</span><span class="sxs-lookup"><span data-stu-id="aa5be-270">Key Concepts</span></span>

* <span data-ttu-id="aa5be-271">實體物件通常會在遇到表面或另一個物件時產生音效。</span><span class="sxs-lookup"><span data-stu-id="aa5be-271">Physical objects generally make a sound when encountering a surface or another object.</span></span>
* <span data-ttu-id="aa5be-272">音效應該在體驗中是適當的內容。</span><span class="sxs-lookup"><span data-stu-id="aa5be-272">Sounds should be context appropriate within the experience.</span></span>

<span data-ttu-id="aa5be-273">例如，在資料表上設定杯的音效應該會比將科羅拉多放在金屬片上的音效更安靜。</span><span class="sxs-lookup"><span data-stu-id="aa5be-273">For example, setting a cup on a table should make a quieter sound than dropping a boulder on a piece of metal.</span></span>

#### <a name="instructions"></a><span data-ttu-id="aa5be-274">指示</span><span class="sxs-lookup"><span data-stu-id="aa5be-274">Instructions</span></span>

* <span data-ttu-id="aa5be-275">**在 [階層**] 面板中，展開 [ **HologramCollection**]。</span><span class="sxs-lookup"><span data-stu-id="aa5be-275">In the **Hierarchy** panel, expand **HologramCollection**.</span></span>
* <span data-ttu-id="aa5be-276">展開 [ **EnergyHub**]，選取 [ **基底**]。</span><span class="sxs-lookup"><span data-stu-id="aa5be-276">Expand **EnergyHub**, select **Base**.</span></span>
* <span data-ttu-id="aa5be-277">在 [偵測 **器** ] 面板中，按一下 [ **新增元件** ]，然後 **以音效和動作** 新增點一下。</span><span class="sxs-lookup"><span data-stu-id="aa5be-277">In the **Inspector** panel, click **Add Component** and add **Tap To Place With Sound and Action**.</span></span>
* <span data-ttu-id="aa5be-278">利用 **音效和動作來放置**：</span><span class="sxs-lookup"><span data-stu-id="aa5be-278">In **Tap To Place With Sound and Action**:</span></span>
  * <span data-ttu-id="aa5be-279">選取 **[在點處放置父系**]。</span><span class="sxs-lookup"><span data-stu-id="aa5be-279">Check **Place Parent On Tap**.</span></span>
  * <span data-ttu-id="aa5be-280">設定放置 **音效** 以 **放置**。</span><span class="sxs-lookup"><span data-stu-id="aa5be-280">Set **Placement Sound** to **Place**.</span></span>
  * <span data-ttu-id="aa5be-281">將 **取貨音效** 設定為 **收取**。</span><span class="sxs-lookup"><span data-stu-id="aa5be-281">Set **Pickup Sound** to **Pickup**.</span></span>
  * <span data-ttu-id="aa5be-282">在 [ **取貨動作** ] 和 [ **放置] 動作** 下，按右下方的 +。</span><span class="sxs-lookup"><span data-stu-id="aa5be-282">Press the + in the bottom right under both **On Pickup Action** and **On Placement Action**.</span></span> <span data-ttu-id="aa5be-283">將 EnergyHub 從場景拖曳至 [ **無] (物件)** 欄位。</span><span class="sxs-lookup"><span data-stu-id="aa5be-283">Drag EnergyHub from the scene into the **None (Object)** fields.</span></span>
    * <span data-ttu-id="aa5be-284">在 [**裝貨] 動作** 底下，按一下 [**沒有函數**  ->  **EnergyHubBase**  ->  **ResetAnimation**]。</span><span class="sxs-lookup"><span data-stu-id="aa5be-284">Under **On Pickup Action**, click on **No Function** -> **EnergyHubBase** -> **ResetAnimation**.</span></span>
    * <span data-ttu-id="aa5be-285">在 [**放置動作**] 下方，按一下 [**沒有函數**  ->  **EnergyHubBase**  ->  **>onselect**]。</span><span class="sxs-lookup"><span data-stu-id="aa5be-285">Under **On Placement Action**, click on **No Function** -> **EnergyHubBase** -> **OnSelect**.</span></span>

![利用音效和動作來放置](images/holograms220-taptoplace.png)

### <a name="part-2---sound-occlusion"></a><span data-ttu-id="aa5be-287">第2部分-音效遮蔽</span><span class="sxs-lookup"><span data-stu-id="aa5be-287">Part 2 - Sound Occlusion</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="aa5be-288">重要概念</span><span class="sxs-lookup"><span data-stu-id="aa5be-288">Key Concepts</span></span>

* <span data-ttu-id="aa5be-289">像光一樣的音效可以是 pixels occluded。</span><span class="sxs-lookup"><span data-stu-id="aa5be-289">Sound, like light, can be occluded.</span></span>

<span data-ttu-id="aa5be-290">典型的範例是音樂會廳。</span><span class="sxs-lookup"><span data-stu-id="aa5be-290">A classic example is a concert hall.</span></span> <span data-ttu-id="aa5be-291">當接聽程式位於大廳之外且門已關閉時，音樂音效會 muffled。</span><span class="sxs-lookup"><span data-stu-id="aa5be-291">When a listener is standing outside of the hall and the door is closed, the music sounds muffled.</span></span> <span data-ttu-id="aa5be-292">通常磁片區也會減少。</span><span class="sxs-lookup"><span data-stu-id="aa5be-292">There is also typically a reduction in volume.</span></span> <span data-ttu-id="aa5be-293">當大門開啟時，就會在實際的音量聽到音效的整個範圍。</span><span class="sxs-lookup"><span data-stu-id="aa5be-293">When the door is opened, the full spectrum of the sound is heard at the actual volume.</span></span> <span data-ttu-id="aa5be-294">高頻率音效通常會吸收較低的頻率。</span><span class="sxs-lookup"><span data-stu-id="aa5be-294">High frequency sounds are generally absorbed more than low frequencies.</span></span>

#### <a name="instructions"></a><span data-ttu-id="aa5be-295">指示</span><span class="sxs-lookup"><span data-stu-id="aa5be-295">Instructions</span></span>

* <span data-ttu-id="aa5be-296">**在 [階層**] 面板中，展開 [ **HologramCollection** ]，然後選取 [ **P0LY**]。</span><span class="sxs-lookup"><span data-stu-id="aa5be-296">In the **Hierarchy** panel, expand **HologramCollection** and select **P0LY**.</span></span>
* <span data-ttu-id="aa5be-297">在 [偵測 **器** ] 面板中，按一下 [ **新增元件** ]，然後新增 **音訊發射器**。</span><span class="sxs-lookup"><span data-stu-id="aa5be-297">In the **Inspector** panel, click **Add Component** and add **Audio Emitter**.</span></span>

<span data-ttu-id="aa5be-298">音訊發射器類別提供下列功能：</span><span class="sxs-lookup"><span data-stu-id="aa5be-298">The Audio Emitter class provides the following features:</span></span>

* <span data-ttu-id="aa5be-299">還原 **spatialize** 磁片區的任何變更。</span><span class="sxs-lookup"><span data-stu-id="aa5be-299">Restores any changes to the volume of the **AudioSource**.</span></span>
* <span data-ttu-id="aa5be-300">從使用者的位置，以 **AudioEmitter** 附加的 **GameObject** 方向來執行 **RaycastNonAlloc** 。</span><span class="sxs-lookup"><span data-stu-id="aa5be-300">Performs a **Physics.RaycastNonAlloc** from the user's position in the direction of the **GameObject** to which the **AudioEmitter** is attached.</span></span>

<span data-ttu-id="aa5be-301">RaycastNonAlloc 方法會用來做為效能優化，以限制配置以及傳回的結果數目。</span><span class="sxs-lookup"><span data-stu-id="aa5be-301">The RaycastNonAlloc method is used as a performance optimization to limit allocations as well as the number of results returned.</span></span>

* <span data-ttu-id="aa5be-302">針對每個遇到的 **IAudioInfluencer** ，會呼叫 **ApplyEffect** 方法。</span><span class="sxs-lookup"><span data-stu-id="aa5be-302">For each **IAudioInfluencer** encountered, calls the **ApplyEffect** method.</span></span>
* <span data-ttu-id="aa5be-303">針對不再遇到的每個先前 **IAudioInfluencer** ，請呼叫 **RemoveEffect** 方法。</span><span class="sxs-lookup"><span data-stu-id="aa5be-303">For each previous **IAudioInfluencer** that is no longer encountered, call the **RemoveEffect** method.</span></span>

<span data-ttu-id="aa5be-304">請注意，AudioEmitter 會更新人為時間刻度，而不是每個畫面上的。</span><span class="sxs-lookup"><span data-stu-id="aa5be-304">Note that AudioEmitter updates on human time scales, as opposed to on a per frame basis.</span></span> <span data-ttu-id="aa5be-305">這樣做的原因是因為人們通常不會移動到足夠的速度，因此效果必須比每一季或半秒更頻繁地更新。</span><span class="sxs-lookup"><span data-stu-id="aa5be-305">This is done because humans generally do not move fast enough for the effect to need to be updated more frequently than every quarter or half of a second.</span></span> <span data-ttu-id="aa5be-306">從某個位置快速傳送到另一個位置的全像影像，可能會破壞假像。</span><span class="sxs-lookup"><span data-stu-id="aa5be-306">Holograms that teleport rapidly from one location to another can break the illusion.</span></span>

* <span data-ttu-id="aa5be-307">**在 [階層**] 面板中，展開 [ **HologramCollection**]。</span><span class="sxs-lookup"><span data-stu-id="aa5be-307">In the **Hierarchy** panel, expand **HologramCollection**.</span></span>
* <span data-ttu-id="aa5be-308">展開 [ **EnergyHub** ]，然後選取 [ **BlobOutside**]。</span><span class="sxs-lookup"><span data-stu-id="aa5be-308">Expand **EnergyHub** and select **BlobOutside**.</span></span>
* <span data-ttu-id="aa5be-309">在 [偵測 **器** ] 面板中，按一下 [ **新增元件** ]，然後新增 **音訊 Occluder**。</span><span class="sxs-lookup"><span data-stu-id="aa5be-309">In the **Inspector** panel, click **Add Component** and add **Audio Occluder**.</span></span>
* <span data-ttu-id="aa5be-310">在 [ **音訊 Occluder**] 中，將 **截止頻率** 設定為 **1500**。</span><span class="sxs-lookup"><span data-stu-id="aa5be-310">In **Audio Occluder**, set **Cutoff Frequency** to **1500**.</span></span>

<span data-ttu-id="aa5be-311">此設定會將 Spatialize 頻率限制為 1500 Hz 和以下。</span><span class="sxs-lookup"><span data-stu-id="aa5be-311">This setting limits the AudioSource frequencies to 1500 Hz and below.</span></span>

* <span data-ttu-id="aa5be-312">將 **磁片區傳遞** 至 **0.9**。</span><span class="sxs-lookup"><span data-stu-id="aa5be-312">Set **Volume Pass Through** to **0.9**.</span></span>

<span data-ttu-id="aa5be-313">這項設定會將 Spatialize 的磁片區縮減為其目前層級的90%。</span><span class="sxs-lookup"><span data-stu-id="aa5be-313">This setting reduces the volume of the AudioSource to 90% of it's current level.</span></span>

<span data-ttu-id="aa5be-314">音訊 Occluder 會將 IAudioInfluencer 實作為：</span><span class="sxs-lookup"><span data-stu-id="aa5be-314">Audio Occluder implements IAudioInfluencer to:</span></span>

* <span data-ttu-id="aa5be-315">使用附加至 **spatialize** 受控購買 **AudioEmitter** 的 **AudioLowPassFilter** 來套用遮蔽效果。</span><span class="sxs-lookup"><span data-stu-id="aa5be-315">Apply an occlusion effect using an **AudioLowPassFilter** which gets attached to the **AudioSource** managed buy the **AudioEmitter**.</span></span>
* <span data-ttu-id="aa5be-316">將磁片區衰減套用至 Spatialize。</span><span class="sxs-lookup"><span data-stu-id="aa5be-316">Applies volume attenuation to the AudioSource.</span></span>
* <span data-ttu-id="aa5be-317">藉由設定中性截止頻率和停用篩選來停用效果。</span><span class="sxs-lookup"><span data-stu-id="aa5be-317">Disables the effect by setting a neutral cutoff frequency and disabling the filter.</span></span>

<span data-ttu-id="aa5be-318">使用中性的頻率是 22 kHz (22000 Hz) 。</span><span class="sxs-lookup"><span data-stu-id="aa5be-318">The frequency used as neutral is 22 kHz (22000 Hz).</span></span> <span data-ttu-id="aa5be-319">選擇此頻率的原因，是因為它高於可由人類 ear 聽到的最大頻率，所以不會對音效造成明顯影響。</span><span class="sxs-lookup"><span data-stu-id="aa5be-319">This frequency was chosen due to it being above the nominal maximum frequency that can be heard by the human ear, this making no discernable impact to the sound.</span></span>

* <span data-ttu-id="aa5be-320">**在 [階層**] 面板中，選取 [ **SpatialMapping**]。</span><span class="sxs-lookup"><span data-stu-id="aa5be-320">In the **Hierarchy** panel, select **SpatialMapping**.</span></span>
* <span data-ttu-id="aa5be-321">在 [偵測 **器** ] 面板中，按一下 [ **新增元件** ]，然後新增 **音訊 Occluder**。</span><span class="sxs-lookup"><span data-stu-id="aa5be-321">In the **Inspector** panel, click **Add Component** and add **Audio Occluder**.</span></span>
* <span data-ttu-id="aa5be-322">在 [ **音訊 Occluder**] 中，將 **截止頻率** 設定為 **750**。</span><span class="sxs-lookup"><span data-stu-id="aa5be-322">In **Audio Occluder**, set **Cutoff Frequency** to **750**.</span></span>

<span data-ttu-id="aa5be-323">當使用者與 **AudioEmitter** 之間的路徑中有多個阻隔器時，會將最低頻率套用至篩選準則。</span><span class="sxs-lookup"><span data-stu-id="aa5be-323">When multiple occluders are in the path between the user and the **AudioEmitter**, the lowest frequency is applied to the filter.</span></span>

* <span data-ttu-id="aa5be-324">將 **磁片區傳遞** 至 **0.75**。</span><span class="sxs-lookup"><span data-stu-id="aa5be-324">Set **Volume Pass Through** to **0.75**.</span></span>

<span data-ttu-id="aa5be-325">當使用者與 **AudioEmitter** 之間的路徑中有多個阻隔器時，會套用額外的大量傳遞。</span><span class="sxs-lookup"><span data-stu-id="aa5be-325">When multiple occluders are in the path between the user and the **AudioEmitter**, the volume pass through is applied additively.</span></span>

* <span data-ttu-id="aa5be-326">**在 [階層**] 面板中，選取 [**管理員**]。</span><span class="sxs-lookup"><span data-stu-id="aa5be-326">In the **Hierarchy** panel, select **Managers**.</span></span>
* <span data-ttu-id="aa5be-327">在 [偵測 **器** ] 面板中，展開 [ **語音輸入處理常式**]。</span><span class="sxs-lookup"><span data-stu-id="aa5be-327">In the **Inspector** panel, expand **Speech Input Handler**.</span></span>
* <span data-ttu-id="aa5be-328">在 [ **語音輸入處理常式**] 中，展開 [ **繼續收費**]。</span><span class="sxs-lookup"><span data-stu-id="aa5be-328">In **Speech Input Handler**, expand **Go Charge**.</span></span>
* <span data-ttu-id="aa5be-329">將 **函數** 變更為 **PolyActions. GoCharge**。</span><span class="sxs-lookup"><span data-stu-id="aa5be-329">Change **No Function** to **PolyActions.GoCharge**.</span></span>

![關鍵字： Go 收費](images/gocharge.png)

* <span data-ttu-id="aa5be-331">展開 **這裡**。</span><span class="sxs-lookup"><span data-stu-id="aa5be-331">Expand **Come Here**.</span></span>
* <span data-ttu-id="aa5be-332">將 **函數** 變更為 **PolyActions. 撰寫復活**。</span><span class="sxs-lookup"><span data-stu-id="aa5be-332">Change **No Function** to **PolyActions.ComeBack**.</span></span>

![關鍵字：這裡](images/comehere.png)

#### <a name="build-and-deploy"></a><span data-ttu-id="aa5be-334">建置和部署</span><span class="sxs-lookup"><span data-stu-id="aa5be-334">Build and Deploy</span></span>

* <span data-ttu-id="aa5be-335">同樣地，在 Unity 中建立專案，並在 Visual Studio 中部署。</span><span class="sxs-lookup"><span data-stu-id="aa5be-335">As before, build the project in Unity and deploy in Visual Studio.</span></span>

<span data-ttu-id="aa5be-336">部署應用程式之後：</span><span class="sxs-lookup"><span data-stu-id="aa5be-336">After the application is deployed:</span></span>

* <span data-ttu-id="aa5be-337">說「 *繼續收費* 」以 P0LY 輸入能源中樞。</span><span class="sxs-lookup"><span data-stu-id="aa5be-337">Say *"Go Charge"* to have P0LY enter the Energy Hub.</span></span>

<span data-ttu-id="aa5be-338">請注意音效中的變更。</span><span class="sxs-lookup"><span data-stu-id="aa5be-338">Note the change in the sound.</span></span> <span data-ttu-id="aa5be-339">它應該聽起來 muffled，而且有點安靜。</span><span class="sxs-lookup"><span data-stu-id="aa5be-339">It should sound muffled and a little quieter.</span></span> <span data-ttu-id="aa5be-340">如果您可以將自己放在您和能源中樞之間的牆或其他物件，您應該會注意到因為真實世界遮蔽而 muffling 的音效。</span><span class="sxs-lookup"><span data-stu-id="aa5be-340">If you are able to position yourself with a wall or other object between you and the Energy Hub, you should notice a further muffling of the sound due to the occlusion by the real world.</span></span>

* <span data-ttu-id="aa5be-341">說「 *來到這裡* 」讓 P0LY 離開能源中樞，並將它放在您的前方。</span><span class="sxs-lookup"><span data-stu-id="aa5be-341">Say *"Come Here"* to have P0LY leave the Energy Hub and position itself in front of you.</span></span>

<span data-ttu-id="aa5be-342">請注意，P0LY 結束能源中樞後，就會移除音效遮蔽。</span><span class="sxs-lookup"><span data-stu-id="aa5be-342">Note that the sound occlusion is removed once P0LY exits the Energy Hub.</span></span> <span data-ttu-id="aa5be-343">如果您仍在聽到遮蔽，P0LY 可能會受到真實世界的 pixels occluded。</span><span class="sxs-lookup"><span data-stu-id="aa5be-343">If you are still hearing occlusion, P0LY may be occluded by the real world.</span></span> <span data-ttu-id="aa5be-344">請嘗試移動以確保您有清楚的 P0LY。</span><span class="sxs-lookup"><span data-stu-id="aa5be-344">Try moving to ensure you have a clear line of sight to P0LY.</span></span>

### <a name="part-3---room-models"></a><span data-ttu-id="aa5be-345">第3部分-房間模型</span><span class="sxs-lookup"><span data-stu-id="aa5be-345">Part 3 - Room Models</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="aa5be-346">重要概念</span><span class="sxs-lookup"><span data-stu-id="aa5be-346">Key Concepts</span></span>

* <span data-ttu-id="aa5be-347">空間大小提供可提供音效當地語系化的 subliminal 佇列。</span><span class="sxs-lookup"><span data-stu-id="aa5be-347">The size of the space provides subliminal queues that contribute to sound localization.</span></span>
* <span data-ttu-id="aa5be-348">每個 **spatialize** 都會設定房間模型。</span><span class="sxs-lookup"><span data-stu-id="aa5be-348">Room models are set per-**AudioSource**.</span></span>
* <span data-ttu-id="aa5be-349">[MixedRealityToolkit For Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)提供用來設定房間模型的程式碼。</span><span class="sxs-lookup"><span data-stu-id="aa5be-349">The [MixedRealityToolkit for Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity) provides code for setting the room model.</span></span>
* <span data-ttu-id="aa5be-350">針對混合現實體驗，請選取最適合真實世界空間的房間模型。</span><span class="sxs-lookup"><span data-stu-id="aa5be-350">For Mixed Reality experiences, select the room model that best fits the real world space.</span></span>

<span data-ttu-id="aa5be-351">如果您要建立虛擬實境案例，請選取最適合虛擬環境的房間模型。</span><span class="sxs-lookup"><span data-stu-id="aa5be-351">If you are creating a Virtual Reality scenario, select the room model that best fits the virtual environment.</span></span>

## <a name="chapter-4---sound-design"></a><span data-ttu-id="aa5be-352">第4章-音效設計</span><span class="sxs-lookup"><span data-stu-id="aa5be-352">Chapter 4 - Sound Design</span></span>

### <a name="objectives"></a><span data-ttu-id="aa5be-353">目標</span><span class="sxs-lookup"><span data-stu-id="aa5be-353">Objectives</span></span>

* <span data-ttu-id="aa5be-354">瞭解有效音效設計的考慮。</span><span class="sxs-lookup"><span data-stu-id="aa5be-354">Understand considerations for effective sound design.</span></span>
* <span data-ttu-id="aa5be-355">學習混合技術與指導方針。</span><span class="sxs-lookup"><span data-stu-id="aa5be-355">Learn mixing techniques and guidelines.</span></span>

### <a name="part-1---sound-and-experience-design"></a><span data-ttu-id="aa5be-356">第1部分-音效和體驗設計</span><span class="sxs-lookup"><span data-stu-id="aa5be-356">Part 1 - Sound and Experience Design</span></span>

<span data-ttu-id="aa5be-357">本節將討論主要音效，以及體驗設計考慮與指導方針。</span><span class="sxs-lookup"><span data-stu-id="aa5be-357">This section discusses key sound and experience design considerations and guidelines.</span></span>

#### <a name="normalize-all-sounds"></a><span data-ttu-id="aa5be-358">標準化所有音效</span><span class="sxs-lookup"><span data-stu-id="aa5be-358">Normalize all sounds</span></span>

<span data-ttu-id="aa5be-359">如此一來，就不需要特殊案例的程式碼來調整每個音效的音量層級，這可能相當耗時，而且會限制輕鬆更新音效檔的能力。</span><span class="sxs-lookup"><span data-stu-id="aa5be-359">This avoids the need for special case code to adjust volume levels per sound, which can be time consuming and limits the ability to easily update sound files.</span></span>

#### <a name="design-for-an-untethered-experience"></a><span data-ttu-id="aa5be-360">非網路共用體驗的設計</span><span class="sxs-lookup"><span data-stu-id="aa5be-360">Design for an untethered experience</span></span>

<span data-ttu-id="aa5be-361">HoloLens 是完全獨立的非網路共用全像電腦。</span><span class="sxs-lookup"><span data-stu-id="aa5be-361">HoloLens is a fully contained, untethered holographic computer.</span></span> <span data-ttu-id="aa5be-362">在移動時，您的使用者可以和將會使用您的體驗。</span><span class="sxs-lookup"><span data-stu-id="aa5be-362">Your users can and will use your experiences while moving.</span></span> <span data-ttu-id="aa5be-363">請務必四處流覽，以測試您的音訊組合。</span><span class="sxs-lookup"><span data-stu-id="aa5be-363">Be sure to test your audio mix by walking around.</span></span>

#### <a name="emit-sound-from-logical-locations-on-your-holograms"></a><span data-ttu-id="aa5be-364">從您的全像位置的邏輯位置發出音效</span><span class="sxs-lookup"><span data-stu-id="aa5be-364">Emit sound from logical locations on your holograms</span></span>

<span data-ttu-id="aa5be-365">在真實世界中，狗不會從其尾端吠，而人類的語音也不會來自于其腳。</span><span class="sxs-lookup"><span data-stu-id="aa5be-365">In the real world, a dog does not bark from its tail and a human's voice does not come from his/her feet.</span></span> <span data-ttu-id="aa5be-366">避免讓您的音效從非預期的全息部分發出。</span><span class="sxs-lookup"><span data-stu-id="aa5be-366">Avoid having your sounds emit from unexpected portions of your holograms.</span></span>

<span data-ttu-id="aa5be-367">針對小型全像影像，從幾何中央開始發出音效是合理的。</span><span class="sxs-lookup"><span data-stu-id="aa5be-367">For small holograms, it is reasonable to have sound emit from the center of the geometry.</span></span>

#### <a name="familiar-sounds-are-most-localizable"></a><span data-ttu-id="aa5be-368">熟悉的音效最能當地語系化</span><span class="sxs-lookup"><span data-stu-id="aa5be-368">Familiar sounds are most localizable</span></span>

<span data-ttu-id="aa5be-369">人類心聲和音樂很容易當地語系化。</span><span class="sxs-lookup"><span data-stu-id="aa5be-369">The human voice and music are very easy to localize.</span></span> <span data-ttu-id="aa5be-370">如果有人呼叫您的名字，您可以非常精確地判斷聲音的出現方向和距離。</span><span class="sxs-lookup"><span data-stu-id="aa5be-370">If someone calls your name, you are able to very accurately determine from what direction the voice came and from how far away.</span></span> <span data-ttu-id="aa5be-371">簡短的是，不熟悉的音效也難以當地語系化。</span><span class="sxs-lookup"><span data-stu-id="aa5be-371">Short, unfamiliar sounds are harder to localize.</span></span>

#### <a name="be-cognizant-of-user-expectations"></a><span data-ttu-id="aa5be-372">Cognizant 使用者期望</span><span class="sxs-lookup"><span data-stu-id="aa5be-372">Be cognizant of user expectations</span></span>

<span data-ttu-id="aa5be-373">生命體驗讓我們能夠找出音效的位置。</span><span class="sxs-lookup"><span data-stu-id="aa5be-373">Life experience plays a part in our ability to identify the location of a sound.</span></span> <span data-ttu-id="aa5be-374">這是人們的聲音特別容易當地語系化的原因之一。</span><span class="sxs-lookup"><span data-stu-id="aa5be-374">This is one reason why the human voice is particularly easy to localize.</span></span> <span data-ttu-id="aa5be-375">在放置音效時，請務必留意使用者的預期期望。</span><span class="sxs-lookup"><span data-stu-id="aa5be-375">It is important to be aware of your user's learned expectations when placing your sounds.</span></span>

<span data-ttu-id="aa5be-376">例如，當有人聽到鳥的歌曲時，通常會進行查閱，因為鳥通常會在 (飛出或在樹狀結構) 上。</span><span class="sxs-lookup"><span data-stu-id="aa5be-376">For example, when someone hears a bird song they generally look up, as birds tend to be above the line of sight (flying or in a tree).</span></span> <span data-ttu-id="aa5be-377">使用者開啟正確的音效方向並不常見，但請查看錯誤的垂直方向，並在找不到全像時感到混淆或感到挫折。</span><span class="sxs-lookup"><span data-stu-id="aa5be-377">It is not uncommon for a user to turn in the correct direction of a sound, but look in the wrong vertical direction and become confused or frustrated when they are unable to find the hologram.</span></span>

#### <a name="avoid-hidden-emitters"></a><span data-ttu-id="aa5be-378">避免隱藏的發射器</span><span class="sxs-lookup"><span data-stu-id="aa5be-378">Avoid hidden emitters</span></span>

<span data-ttu-id="aa5be-379">在真實世界中，如果聽到音效，我們通常可以找出發出音效的物件。</span><span class="sxs-lookup"><span data-stu-id="aa5be-379">In the real world, if we hear a sound, we can generally identify the object that is emitting the sound.</span></span> <span data-ttu-id="aa5be-380">這也應該在您的體驗中成立。</span><span class="sxs-lookup"><span data-stu-id="aa5be-380">This should also hold true in your experiences.</span></span> <span data-ttu-id="aa5be-381">這可能很令人不安，讓使用者聽聽音效，從音效的來源，到無法查看物件。</span><span class="sxs-lookup"><span data-stu-id="aa5be-381">It can be very disconcerting for users to hear a sound, know from where the sound originates and be unable to see an object.</span></span>

<span data-ttu-id="aa5be-382">此指導方針有一些例外。</span><span class="sxs-lookup"><span data-stu-id="aa5be-382">There are some exceptions to this guideline.</span></span> <span data-ttu-id="aa5be-383">例如，欄位中的 crickets 等環境音效不需要可見。</span><span class="sxs-lookup"><span data-stu-id="aa5be-383">For example, ambient sounds such as crickets in a field need not be visible.</span></span> <span data-ttu-id="aa5be-384">生命體驗讓我們熟悉這些音效的來源，而不需要加以查看。</span><span class="sxs-lookup"><span data-stu-id="aa5be-384">Life experience gives us familiarity with the source of these sounds without the need to see it.</span></span>

### <a name="part-2---sound-mixing"></a><span data-ttu-id="aa5be-385">第2部分-音效混合</span><span class="sxs-lookup"><span data-stu-id="aa5be-385">Part 2 - Sound Mixing</span></span>

#### <a name="target-your-mix-for-70-volume-on-the-hololens"></a><span data-ttu-id="aa5be-386">將您在 HoloLens 上的70% 磁片區混合設為目標</span><span class="sxs-lookup"><span data-stu-id="aa5be-386">Target your mix for 70% volume on the HoloLens</span></span>

<span data-ttu-id="aa5be-387">混合現實體驗可讓您在真實世界中看到全像影像。</span><span class="sxs-lookup"><span data-stu-id="aa5be-387">Mixed Reality experiences allow holograms to be seen in the real world.</span></span> <span data-ttu-id="aa5be-388">它們也應該讓真實的聲音聽起來。</span><span class="sxs-lookup"><span data-stu-id="aa5be-388">They should also allow real world sounds to be heard.</span></span> <span data-ttu-id="aa5be-389">70% 的磁片區目標可讓使用者在世界各地聆聽您的體驗。</span><span class="sxs-lookup"><span data-stu-id="aa5be-389">A 70% volume target enables the user to hear the world around them along with the sound of your experience.</span></span>

#### <a name="hololens-at-100-volume-should-drown-out-external-sounds"></a><span data-ttu-id="aa5be-390">100% 磁片區的 HoloLens 應下拉式清單外部聲音</span><span class="sxs-lookup"><span data-stu-id="aa5be-390">HoloLens at 100% volume should drown out external sounds</span></span>

<span data-ttu-id="aa5be-391">磁片區層級100% 類似于虛擬實境體驗。</span><span class="sxs-lookup"><span data-stu-id="aa5be-391">A volume level of 100% is akin to a Virtual Reality experience.</span></span> <span data-ttu-id="aa5be-392">使用者會以視覺化方式傳送到不同的世界。</span><span class="sxs-lookup"><span data-stu-id="aa5be-392">Visually, the user is transported to a different world.</span></span> <span data-ttu-id="aa5be-393">相同的語音也是如此。</span><span class="sxs-lookup"><span data-stu-id="aa5be-393">The same should hold true audibly.</span></span>

#### <a name="use-the-unity-audiomixer-to-adjust-categories-of-sounds"></a><span data-ttu-id="aa5be-394">使用 Unity AudioMixer 來調整聲音的類別</span><span class="sxs-lookup"><span data-stu-id="aa5be-394">Use the Unity AudioMixer to adjust categories of sounds</span></span>

<span data-ttu-id="aa5be-395">設計混合時，建立音效類別以及能夠將其磁片區增加或減少為一個單位通常會很有説明。</span><span class="sxs-lookup"><span data-stu-id="aa5be-395">When designing your mix, it is often helpful to create sound categories and have the ability to increase or decrease their volume as a unit.</span></span> <span data-ttu-id="aa5be-396">這會保留每個音效的相對層級，同時讓整體混合的快速且輕鬆地進行變更。</span><span class="sxs-lookup"><span data-stu-id="aa5be-396">This retains the relative levels of each sound while enabling quick and easy changes to the overall mix.</span></span> <span data-ttu-id="aa5be-397">常見類別包括：音效、環境、語音轉移和背景音樂。</span><span class="sxs-lookup"><span data-stu-id="aa5be-397">Common categories include; sound effects, ambience, voice overs and background music.</span></span>

#### <a name="mix-sounds-based-on-the-users-gaze"></a><span data-ttu-id="aa5be-398">根據使用者的注視來混合音效</span><span class="sxs-lookup"><span data-stu-id="aa5be-398">Mix sounds based on the user's gaze</span></span>

<span data-ttu-id="aa5be-399">根據使用者在 (或不) 的情況下，變更您體驗的音效通常會很有用。</span><span class="sxs-lookup"><span data-stu-id="aa5be-399">It can often be useful to change the sound mix in your experience based on where a user is (or is not) looking.</span></span> <span data-ttu-id="aa5be-400">這項技術的其中一種常見用途是減少全像全像攝影框架外的全息體音量層級，讓使用者更容易專注于他們之前的資訊。</span><span class="sxs-lookup"><span data-stu-id="aa5be-400">One common use for this technique are to reduce the volume level for holograms that are outside of the Holographic Frame to make it easier for the user to focus on the information in front of them.</span></span> <span data-ttu-id="aa5be-401">另一種用途是增加音效的音量，將使用者的注意力吸引到重要的活動。</span><span class="sxs-lookup"><span data-stu-id="aa5be-401">Another use is to increase the volume of a sound to draw the user's attention to an important event.</span></span>

#### <a name="building-your-mix"></a><span data-ttu-id="aa5be-402">打造您的混合</span><span class="sxs-lookup"><span data-stu-id="aa5be-402">Building your mix</span></span>

<span data-ttu-id="aa5be-403">建立混合時，建議您從經驗的背景音訊著手，並根據重要性新增圖層。</span><span class="sxs-lookup"><span data-stu-id="aa5be-403">When building your mix, it is recommended to start with your experience's background audio and add layers based on importance.</span></span> <span data-ttu-id="aa5be-404">這通常會導致每個圖層比上一個層更大。</span><span class="sxs-lookup"><span data-stu-id="aa5be-404">Often, this results in each layer being louder than the previous.</span></span>

<span data-ttu-id="aa5be-405">將您的混合想像為反向漏斗圖，其中最重要的 (，且通常會在底部) quietest 音效，建議您以類似下圖的方式來結構您的混合。</span><span class="sxs-lookup"><span data-stu-id="aa5be-405">Imagining your mix as an inverted funnel, with the least important (and generally quietest sounds) at the bottom, it is recommended to structure your mix similar to the following diagram.</span></span>

![音效混合結構](images/soundlevels.png)

<span data-ttu-id="aa5be-407">語音轉移是一種有趣的案例。</span><span class="sxs-lookup"><span data-stu-id="aa5be-407">Voice overs are an interesting scenario.</span></span> <span data-ttu-id="aa5be-408">根據您所建立的體驗，您可能會想要有身歷聲 (未當地語系化) 音效或 spatialize 語音轉移。</span><span class="sxs-lookup"><span data-stu-id="aa5be-408">Based on the experience you are creating you may wish to have a stereo (not localized) sound or to spatialize your voice overs.</span></span> <span data-ttu-id="aa5be-409">兩個 Microsoft 發佈的經驗說明每個案例的絕佳範例。</span><span class="sxs-lookup"><span data-stu-id="aa5be-409">Two Microsoft published experiences illustrate excellent examples of each scenario.</span></span>

<span data-ttu-id="aa5be-410">[HoloTour](https://www.microsoft.com/store/p/holotour/9nblggh5pj87) 使用身歷聲語音。</span><span class="sxs-lookup"><span data-stu-id="aa5be-410">[HoloTour](https://www.microsoft.com/store/p/holotour/9nblggh5pj87) uses a stereo voice over.</span></span> <span data-ttu-id="aa5be-411">當朗讀程式描述所要查看的位置時，音效是一致的，而且不會根據使用者的位置而有所不同。</span><span class="sxs-lookup"><span data-stu-id="aa5be-411">When the narrator is describing the location being viewed, the sound is consistent and does not vary based on the user's position.</span></span> <span data-ttu-id="aa5be-412">這可讓朗讀程式描述場景，而不需要離開環境的 hrtf 音效。</span><span class="sxs-lookup"><span data-stu-id="aa5be-412">This enables the narrator to describe the scene without taking away from the spatialized sounds of the environment.</span></span>

<span data-ttu-id="aa5be-413">[片段](https://www.microsoft.com/store/p/fragments/9nblggh5ggm8) 會利用 hrtf 的語音，以偵探的形式來使用。</span><span class="sxs-lookup"><span data-stu-id="aa5be-413">[Fragments](https://www.microsoft.com/store/p/fragments/9nblggh5ggm8) utilizes a spatialized voice over in the form of a detective.</span></span> <span data-ttu-id="aa5be-414">您可以使用偵探的聲音來協助使用者關注重要的線索，就像實際的人在房間裡一樣。</span><span class="sxs-lookup"><span data-stu-id="aa5be-414">The detective's voice is used to help bring the user's attention to an important clue as if an actual human was in the room.</span></span> <span data-ttu-id="aa5be-415">這可讓您更清楚地深度解決謎的體驗。</span><span class="sxs-lookup"><span data-stu-id="aa5be-415">This enables an even greater sense of immersion into the experience of solving the mystery.</span></span>

### <a name="part-3--performance"></a><span data-ttu-id="aa5be-416">第3部分-效能</span><span class="sxs-lookup"><span data-stu-id="aa5be-416">Part 3 -Performance</span></span>

#### <a name="cpu-usage"></a><span data-ttu-id="aa5be-417">CPU 使用量</span><span class="sxs-lookup"><span data-stu-id="aa5be-417">CPU usage</span></span>

<span data-ttu-id="aa5be-418">使用空間音效時，10-12 發射器將耗用大約12% 的 CPU。</span><span class="sxs-lookup"><span data-stu-id="aa5be-418">When using Spatial Sound, 10 - 12 emitters will consume approximately 12% of the CPU.</span></span>

#### <a name="stream-long-audio-files"></a><span data-ttu-id="aa5be-419">串流長音訊檔案</span><span class="sxs-lookup"><span data-stu-id="aa5be-419">Stream long audio files</span></span>

<span data-ttu-id="aa5be-420">音訊資料可能很大，尤其是常見的取樣率 (44.1 和 48 kHz) 。</span><span class="sxs-lookup"><span data-stu-id="aa5be-420">Audio data can be large, especially at common sample rates (44.1 and 48 kHz).</span></span> <span data-ttu-id="aa5be-421">一般規則是，應串流處理超過 5-10 秒的音訊檔案，以減少應用程式記憶體使用量。</span><span class="sxs-lookup"><span data-stu-id="aa5be-421">A general rule is that audio files longer than 5 - 10 seconds should be streamed to reduce application memory usage.</span></span>

<span data-ttu-id="aa5be-422">在 Unity 中，您可以在檔案的匯入設定中標示要串流處理的音訊檔案。</span><span class="sxs-lookup"><span data-stu-id="aa5be-422">In Unity, you can mark an audio file for streaming in the file's import settings.</span></span>

![音訊匯入設定](images/audioimportsettings.png)

## <a name="chapter-5---special-effects"></a><span data-ttu-id="aa5be-424">第5章-特殊效果</span><span class="sxs-lookup"><span data-stu-id="aa5be-424">Chapter 5 - Special Effects</span></span>

### <a name="objectives"></a><span data-ttu-id="aa5be-425">目標</span><span class="sxs-lookup"><span data-stu-id="aa5be-425">Objectives</span></span>

* <span data-ttu-id="aa5be-426">將深度新增至「魔術視窗」。</span><span class="sxs-lookup"><span data-stu-id="aa5be-426">Add depth to "Magic Windows".</span></span>
* <span data-ttu-id="aa5be-427">將使用者帶入虛擬世界。</span><span class="sxs-lookup"><span data-stu-id="aa5be-427">Bring the user into the virtual world.</span></span>

### <a name="magic-windows"></a><span data-ttu-id="aa5be-428">魔術視窗</span><span class="sxs-lookup"><span data-stu-id="aa5be-428">Magic Windows</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="aa5be-429">重要概念</span><span class="sxs-lookup"><span data-stu-id="aa5be-429">Key Concepts</span></span>

* <span data-ttu-id="aa5be-430">以視覺效果吸引人，將視圖建立到隱藏的世界中。</span><span class="sxs-lookup"><span data-stu-id="aa5be-430">Creating views into a hidden world, is visually compelling.</span></span>
* <span data-ttu-id="aa5be-431">藉由在隱藏體或使用者接近隱藏的世界時新增音訊效果，以增強真實感。</span><span class="sxs-lookup"><span data-stu-id="aa5be-431">Enhance realism by adding audio effects when a hologram or the user is near the hidden world.</span></span>

#### <a name="instructions"></a><span data-ttu-id="aa5be-432">指示</span><span class="sxs-lookup"><span data-stu-id="aa5be-432">Instructions</span></span>

* <span data-ttu-id="aa5be-433">**在 [階層**] 面板中，展開 [ **HologramCollection** ]，然後選取 [ **Underworld**]。</span><span class="sxs-lookup"><span data-stu-id="aa5be-433">In the **Hierarchy** panel, expand **HologramCollection** and select **Underworld**.</span></span>
* <span data-ttu-id="aa5be-434">展開 [ **Underworld** ]，然後選取 [ **VoiceSource**]。</span><span class="sxs-lookup"><span data-stu-id="aa5be-434">Expand **Underworld** and select **VoiceSource**.</span></span>
* <span data-ttu-id="aa5be-435">在 [偵測 **器** ] 面板中，按一下 [ **新增元件** ] 和 [新增 **使用者語音效果**]。</span><span class="sxs-lookup"><span data-stu-id="aa5be-435">In the **Inspector** panel, click **Add Component** and add **User Voice Effect**.</span></span>

<span data-ttu-id="aa5be-436">**Spatialize** 元件將會新增至 **VoiceSource**。</span><span class="sxs-lookup"><span data-stu-id="aa5be-436">An **AudioSource** component will be added to **VoiceSource**.</span></span>

* <span data-ttu-id="aa5be-437">在 **spatialize** 中，將 [ **輸出** ] 設定為 **UserVoice (混音器)**。</span><span class="sxs-lookup"><span data-stu-id="aa5be-437">In **AudioSource**, set **Output** to **UserVoice (Mixer)**.</span></span>
* <span data-ttu-id="aa5be-438">核取 [ **Spatialize** ] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="aa5be-438">Check the **Spatialize** checkbox.</span></span>
* <span data-ttu-id="aa5be-439">將 **空間 Blend** 滑杆拖曳至 **3d**，或在編輯方塊中輸入 **1** 。</span><span class="sxs-lookup"><span data-stu-id="aa5be-439">Drag the **Spatial Blend** slider all the way to **3D**, or enter **1** in the edit box.</span></span>
* <span data-ttu-id="aa5be-440">展開 [ **3D 音效設定**]。</span><span class="sxs-lookup"><span data-stu-id="aa5be-440">Expand **3D Sound Settings**.</span></span>
* <span data-ttu-id="aa5be-441">將 **Doppler 層級** 設定為 **0**。</span><span class="sxs-lookup"><span data-stu-id="aa5be-441">Set **Doppler Level** to **0**.</span></span>
* <span data-ttu-id="aa5be-442">在 [ **使用者心聲效果**] 中，將 **父物件** 從場景設定為 **Underworld** 。</span><span class="sxs-lookup"><span data-stu-id="aa5be-442">In **User Voice Effect**, set **Parent Object** to the **Underworld** from the scene.</span></span>
* <span data-ttu-id="aa5be-443">將 **最大距離** 設定為 **1**。</span><span class="sxs-lookup"><span data-stu-id="aa5be-443">Set **Max Distance** to **1**.</span></span>

<span data-ttu-id="aa5be-444">設定 [ **最大距離** ] 會告知 **使用者語音效果** 在啟用效果之前，使用者必須在父物件中的距離。</span><span class="sxs-lookup"><span data-stu-id="aa5be-444">Setting **Max Distance** tells **User Voice Effect** how close the user must be to the parent object before the effect is enabled.</span></span>

* <span data-ttu-id="aa5be-445">在 [ **使用者語音效果**] 中，展開 [ **一首哀歌參數**]。</span><span class="sxs-lookup"><span data-stu-id="aa5be-445">In **User Voice Effect**, expand **Chorus Parameters**.</span></span>
* <span data-ttu-id="aa5be-446">將 **深度** 設定為 **0.1**。</span><span class="sxs-lookup"><span data-stu-id="aa5be-446">Set **Depth** to **0.1**.</span></span>
* <span data-ttu-id="aa5be-447">設定一下 **1 個磁片** 區，再按2個 **音量** ，然後將3個 **磁片區分** 到 **0.8**。</span><span class="sxs-lookup"><span data-stu-id="aa5be-447">Set **Tap 1 Volume**, **Tap 2 Volume** and **Tap 3 Volume** to **0.8**.</span></span>
* <span data-ttu-id="aa5be-448">將 **原始音效磁片** 區設定為 **0.5**。</span><span class="sxs-lookup"><span data-stu-id="aa5be-448">Set **Original Sound Volume** to **0.5**.</span></span>

<span data-ttu-id="aa5be-449">先前的設定會設定 Unity **AudioChorusFilter** 的參數，這些參數是用來為使用者的語音新增豐富的聲音。</span><span class="sxs-lookup"><span data-stu-id="aa5be-449">The previous settings configure the parameters of the Unity **AudioChorusFilter** used to add richness to the user's voice.</span></span>

* <span data-ttu-id="aa5be-450">在 [ **使用者語音效果**] 中，展開 [ **Echo 參數**]。</span><span class="sxs-lookup"><span data-stu-id="aa5be-450">In **User Voice Effect**, expand **Echo Parameters**.</span></span>
* <span data-ttu-id="aa5be-451">將 **延遲** 設定為 **300**</span><span class="sxs-lookup"><span data-stu-id="aa5be-451">Set **Delay** to **300**</span></span>
* <span data-ttu-id="aa5be-452">將 **衰減比例** 設定為 **0.2**。</span><span class="sxs-lookup"><span data-stu-id="aa5be-452">Set **Decay Ratio** to **0.2**.</span></span>
* <span data-ttu-id="aa5be-453">將 **原始音效音量** 設定為 **0**。</span><span class="sxs-lookup"><span data-stu-id="aa5be-453">Set **Original Sound Volume** to **0**.</span></span>

<span data-ttu-id="aa5be-454">先前的設定會設定用來讓使用者的語音回應的 Unity **AudioEchoFilter** 參數。</span><span class="sxs-lookup"><span data-stu-id="aa5be-454">The previous settings configure the parameters of the Unity **AudioEchoFilter** used to cause the user's voice to echo.</span></span>

<span data-ttu-id="aa5be-455">使用者心聲效果腳本負責：</span><span class="sxs-lookup"><span data-stu-id="aa5be-455">The User Voice Effect script is responsible for:</span></span>

* <span data-ttu-id="aa5be-456">測量使用者與附加腳本的 **GameObject** 之間的距離。</span><span class="sxs-lookup"><span data-stu-id="aa5be-456">Measuring the distance between the user and the **GameObject** to which the script is attached.</span></span>
* <span data-ttu-id="aa5be-457">判斷使用者是否遇到 **GameObject**。</span><span class="sxs-lookup"><span data-stu-id="aa5be-457">Determining whether or not the user is facing the **GameObject**.</span></span>

<span data-ttu-id="aa5be-458">無論距離為何，使用者都必須面對 GameObject，才能啟用效果。</span><span class="sxs-lookup"><span data-stu-id="aa5be-458">The user must be facing the GameObject, regardless of distance, for the effect to be enabled.</span></span>

* <span data-ttu-id="aa5be-459">將 **AudioChorusFilter** 和 **AudioEchoFilter** 套用至 **spatialize**。</span><span class="sxs-lookup"><span data-stu-id="aa5be-459">Applying and configuring an **AudioChorusFilter** and an **AudioEchoFilter** to the **AudioSource**.</span></span>
* <span data-ttu-id="aa5be-460">停用篩選以停用效果。</span><span class="sxs-lookup"><span data-stu-id="aa5be-460">Disabling the effect by disabling the filters.</span></span>

<span data-ttu-id="aa5be-461">使用者心聲效果會使用來自 [MixedRealityToolkit For Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)的 Mic 串流選取器元件，來選取高品質的語音串流，並將其路由傳送至 Unity 的音訊系統。</span><span class="sxs-lookup"><span data-stu-id="aa5be-461">User Voice Effect uses the Mic Stream Selector component, from the [MixedRealityToolkit for Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity), to select the high quality voice stream and route it into Unity's audio system.</span></span>

* <span data-ttu-id="aa5be-462">**在 [階層**] 面板中，選取 [**管理員**]。</span><span class="sxs-lookup"><span data-stu-id="aa5be-462">In the **Hierarchy** panel, select **Managers**.</span></span>
* <span data-ttu-id="aa5be-463">在 [偵測 **器** ] 面板中，展開 [ **語音輸入處理常式**]。</span><span class="sxs-lookup"><span data-stu-id="aa5be-463">In the **Inspector** panel, expand **Speech Input Handler**.</span></span>
* <span data-ttu-id="aa5be-464">在 [ **語音輸入處理常式**] 中，展開 [ **顯示 Underworld**]。</span><span class="sxs-lookup"><span data-stu-id="aa5be-464">In **Speech Input Handler**, expand **Show Underworld**.</span></span>
* <span data-ttu-id="aa5be-465">將 **函數** 變更為 **UnderworldBase. OnEnable**。</span><span class="sxs-lookup"><span data-stu-id="aa5be-465">Change **No Function** to **UnderworldBase.OnEnable**.</span></span>

![關鍵字：顯示 Underworld](images/showunderworld.png)

* <span data-ttu-id="aa5be-467">展開 [ **隱藏 Underworld**]。</span><span class="sxs-lookup"><span data-stu-id="aa5be-467">Expand **Hide Underworld**.</span></span>
* <span data-ttu-id="aa5be-468">將 **函數** 變更為 **UnderworldBase. OnDisable**。</span><span class="sxs-lookup"><span data-stu-id="aa5be-468">Change **No Function** to **UnderworldBase.OnDisable**.</span></span>

![關鍵字：隱藏 Underworld](images/hideunderworld.png)

#### <a name="build-and-deploy"></a><span data-ttu-id="aa5be-470">建置和部署</span><span class="sxs-lookup"><span data-stu-id="aa5be-470">Build and Deploy</span></span>

* <span data-ttu-id="aa5be-471">同樣地，在 Unity 中建立專案，並在 Visual Studio 中部署。</span><span class="sxs-lookup"><span data-stu-id="aa5be-471">As before, build the project in Unity and deploy in Visual Studio.</span></span>

<span data-ttu-id="aa5be-472">部署應用程式之後：</span><span class="sxs-lookup"><span data-stu-id="aa5be-472">After the application is deployed:</span></span>

* <span data-ttu-id="aa5be-473">臉部 (牆壁、樓層、表格) ，然後說出 *"Show Underworld"*。</span><span class="sxs-lookup"><span data-stu-id="aa5be-473">Face a surface (wall, floor, table) and say *"Show Underworld"*.</span></span>

<span data-ttu-id="aa5be-474">將會顯示 underworld，並隱藏所有其他的全像投影。</span><span class="sxs-lookup"><span data-stu-id="aa5be-474">The underworld will be shown and all other holograms will be hidden.</span></span> <span data-ttu-id="aa5be-475">如果看不到 underworld，請確定您面對的是真實世界表面。</span><span class="sxs-lookup"><span data-stu-id="aa5be-475">If you do not see the underworld, ensure that you are facing a real-world surface.</span></span>

* <span data-ttu-id="aa5be-476">Underworld 全像1計量中的方法，並開始討論。</span><span class="sxs-lookup"><span data-stu-id="aa5be-476">Approach within 1 meter of the underworld hologram and start talking.</span></span>

<span data-ttu-id="aa5be-477">現在音訊效果已套用至您的語音！</span><span class="sxs-lookup"><span data-stu-id="aa5be-477">There are now audio effects applied to your voice!</span></span>

* <span data-ttu-id="aa5be-478">關閉 underworld，並注意效果不再適用的方式。</span><span class="sxs-lookup"><span data-stu-id="aa5be-478">Turn away from the underworld and notice how the effect is no longer applied.</span></span>
* <span data-ttu-id="aa5be-479">說「 *隱藏 Underworld* 」以隱藏 Underworld。</span><span class="sxs-lookup"><span data-stu-id="aa5be-479">Say *"Hide Underworld"* to hide the underworld.</span></span>

<span data-ttu-id="aa5be-480">Underworld 將會隱藏，而先前隱藏的全像全像投影會再度出現。</span><span class="sxs-lookup"><span data-stu-id="aa5be-480">The underworld will be hidden and the previously hidden holograms will reappear.</span></span>

## <a name="the-end"></a><span data-ttu-id="aa5be-481">結束</span><span class="sxs-lookup"><span data-stu-id="aa5be-481">The End</span></span>

<span data-ttu-id="aa5be-482">恭喜！</span><span class="sxs-lookup"><span data-stu-id="aa5be-482">Congratulations!</span></span> <span data-ttu-id="aa5be-483">您現在已完成 **MR 空間220：空間音效**。</span><span class="sxs-lookup"><span data-stu-id="aa5be-483">You have now completed **MR Spatial 220: Spatial sound**.</span></span>

<span data-ttu-id="aa5be-484">聽聽全世界的音效，利用音效讓您的生活體驗！</span><span class="sxs-lookup"><span data-stu-id="aa5be-484">Listen to the world and bring your experiences to life with sound!</span></span>