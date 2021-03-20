---
title: MRTKNuGetPakages
description: MRTK 中的 NuGet 套件。
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
ms.localizationpriority: medium
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: eb41896977bded6dd5b1aec7c4b17632435c6b94
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104692725"
---
# <a name="mixed-reality-toolkit-nuget-package"></a><span data-ttu-id="c0a4f-104">混合現實工具組 NuGet 套件</span><span class="sxs-lookup"><span data-stu-id="c0a4f-104">Mixed Reality Toolkit NuGet package</span></span>

<span data-ttu-id="c0a4f-105">混合現實工具組 (MRTK) 現已在 NuGet.org 上以 NuGet 套件的形式提供。使用 NuGet 版本的 MRTK 而不是 unitypackage 時，有一些差異，請參閱下面的 [Nuget 套件考慮](#nuget-package-considerations) 。</span><span class="sxs-lookup"><span data-stu-id="c0a4f-105">Mixed Reality Toolkit (MRTK) is now available as a NuGet package on NuGet.org. There are some differences when it comes to consuming NuGet version of MRTK as opposed to a .unitypackage, read [NuGet Package Considerations](#nuget-package-considerations) below.</span></span> <span data-ttu-id="c0a4f-106">如果遇到任何問題，請使用此 [範本](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/new?assignees=&labels=Bug,Package%20Management%20-%20NuGet&template=bug-report.md&title=)提出問題。</span><span class="sxs-lookup"><span data-stu-id="c0a4f-106">If any issues are encountered, file an issue using this [template](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/new?assignees=&labels=Bug,Package%20Management%20-%20NuGet&template=bug-report.md&title=).</span></span>

> [!NOTE]
> <span data-ttu-id="c0a4f-107">尚不支援將現有專案遷移至使用 MRTK 作為 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="c0a4f-107">Migration of existing projects to consume MRTK as a NuGet package is not yet supported.</span></span> <span data-ttu-id="c0a4f-108">僅針對新的專案使用 MRTK via NuGet。</span><span class="sxs-lookup"><span data-stu-id="c0a4f-108">Use MRTK via NuGet only for new projects.</span></span>

## <a name="installing-the-nuget-package"></a><span data-ttu-id="c0a4f-109">安裝 NuGet 封裝</span><span class="sxs-lookup"><span data-stu-id="c0a4f-109">Installing the NuGet package</span></span>

<span data-ttu-id="c0a4f-110">遵循這些指示，將混合現實工具組新增為您專案的 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="c0a4f-110">Follow these instructions to add the Mixed Reality Toolkit as a NuGet package to your project.</span></span>

1. <span data-ttu-id="c0a4f-111">下載最新的 [NuGetForUnity](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest) . unitypackage。</span><span class="sxs-lookup"><span data-stu-id="c0a4f-111">Download the latest [NuGetForUnity](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest) .unitypackage.</span></span>
    1. <span data-ttu-id="c0a4f-112">如果已安裝 *NuGetForUnity* ，請確定其版本為 **2.0.0 或更新** 版本。</span><span class="sxs-lookup"><span data-stu-id="c0a4f-112">If *NuGetForUnity* is already installed, please ensure it is version **2.0.0 or newer**.</span></span>
1. <span data-ttu-id="c0a4f-113">將封裝匯入 Unity 專案中， [指示](https://docs.unity3d.com/Manual/AssetPackages.html)。</span><span class="sxs-lookup"><span data-stu-id="c0a4f-113">Import the package into the Unity project, [instructions](https://docs.unity3d.com/Manual/AssetPackages.html).</span></span>
1. <span data-ttu-id="c0a4f-114">在 Unity 功能表列中，按一下 [ **nuget**  >  **管理 nuget 封裝**]。</span><span class="sxs-lookup"><span data-stu-id="c0a4f-114">In the Unity menu bar, click on **NuGet** > **Manage NuGet Packages**.</span></span>

    ![Manage NuGet Packages](../Images/NuGet/ManageNuGetPackages.png)
1. <span data-ttu-id="c0a4f-116">在搜尋方塊中，輸入 **MixedReality 工具** 組。</span><span class="sxs-lookup"><span data-stu-id="c0a4f-116">In the Search box, enter **Microsoft.MixedReality.Toolkit**.</span></span>

    ![Manage NuGet Packages](../Images/NuGet/SearchBox.png)
1. <span data-ttu-id="c0a4f-118">選擇 MRTK core 套件：</span><span class="sxs-lookup"><span data-stu-id="c0a4f-118">Choose the MRTK core package:</span></span>
    - <span data-ttu-id="c0a4f-119">**MixedReality** – MRTK 的核心套件。</span><span class="sxs-lookup"><span data-stu-id="c0a4f-119">**Microsoft.MixedReality.Toolkit.Foundation** – The core package for MRTK.</span></span>
1. <span data-ttu-id="c0a4f-120"> (選擇性的) 選擇 MRTK 選用套件。</span><span class="sxs-lookup"><span data-stu-id="c0a4f-120">(Optional) Choose the MRTK optional packages.</span></span>
    - <span data-ttu-id="c0a4f-121">**MixedReality-範例** -包含所有範例的封裝。</span><span class="sxs-lookup"><span data-stu-id="c0a4f-121">**Microsoft.MixedReality.Toolkit.Examples** – The package that contains all of our examples.</span></span>
    - <span data-ttu-id="c0a4f-122">**MixedReality** ：包含擴充服務和（或）資料提供者的封裝。</span><span class="sxs-lookup"><span data-stu-id="c0a4f-122">**Microsoft.MixedReality.Toolkit.Extensions** – The package that contains extensions services and/or data providers.</span></span>
    - <span data-ttu-id="c0a4f-123">**MixedReality** ：包含一些 MRTK (組建視窗等等的工具，也就是) 。</span><span class="sxs-lookup"><span data-stu-id="c0a4f-123">**Microsoft.MixedReality.Toolkit.Tools** – Contains some of the tooling that comes with MRTK (Build Window, etc).</span></span>

### <a name="updating-mrtk-nuget-packages"></a><span data-ttu-id="c0a4f-124">更新 MRTK NuGet 套件</span><span class="sxs-lookup"><span data-stu-id="c0a4f-124">Updating MRTK NuGet packages</span></span>

<span data-ttu-id="c0a4f-125">上述步驟1-2 只需要針對專案執行一次，而更新是更簡單的步驟。</span><span class="sxs-lookup"><span data-stu-id="c0a4f-125">Steps 1-2 above will only need to be done once for the project, and the update is a much simpler step.</span></span> <span data-ttu-id="c0a4f-126">一旦 NuGet.org 上有較新的套件可用 (（包括發行前版本) ），請遵循下列步驟：</span><span class="sxs-lookup"><span data-stu-id="c0a4f-126">Once newer packages are available on NuGet.org (including prerelease), follow these steps:</span></span>

1. <span data-ttu-id="c0a4f-127">在 Unity 功能表列中，按一下 [ **nuget**  >  **管理 nuget 套件**]</span><span class="sxs-lookup"><span data-stu-id="c0a4f-127">In the Unity menu bar, click on **NuGet** > **Manage NuGet Packages**</span></span>
1. <span data-ttu-id="c0a4f-128">切換至 [ **更新** ] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="c0a4f-128">Switch to the **Updates** tab.</span></span>
    - <span data-ttu-id="c0a4f-129">如果您想要取得最新的發行前版本，請勾選 [ **顯示發行** 前版本] 方塊。</span><span class="sxs-lookup"><span data-stu-id="c0a4f-129">Check the **Show prerelease** box if you want to get latest prerelease version.</span></span>
1. <span data-ttu-id="c0a4f-130">更新所需的套件。</span><span class="sxs-lookup"><span data-stu-id="c0a4f-130">Update the packages desired.</span></span>

## <a name="nuget-package-considerations"></a><span data-ttu-id="c0a4f-131">NuGet 套件考慮</span><span class="sxs-lookup"><span data-stu-id="c0a4f-131">NuGet package considerations</span></span>

<span data-ttu-id="c0a4f-132">以 NuGet 套件的形式發行 MRTK 是一種新的傳遞機制，而且在選擇是否要使用 NuGet 版本的 MRTK 時，有幾個重要的優點和考慮需要進行。</span><span class="sxs-lookup"><span data-stu-id="c0a4f-132">The release of MRTK as NuGet package is a new delivery mechanism being explored and there are a couple of key benefits and considerations one must make when choosing whether to consume the NuGet version of MRTK.</span></span>

### <a name="migrating-to-nuget-from-unitypackage-or-source-not-yet-supported"></a><span data-ttu-id="c0a4f-133">尚未支援從 unitypackage 或來源遷移至 NuGet () </span><span class="sxs-lookup"><span data-stu-id="c0a4f-133">Migrating to NuGet from .unitypackage or source (not yet supported)</span></span>

<span data-ttu-id="c0a4f-134">NuGet 封裝包含編譯過的二進位檔，而不是鬆散的腳本檔案，而且 c # 腳本資產識別碼不同。</span><span class="sxs-lookup"><span data-stu-id="c0a4f-134">NuGet package consists of compiled binaries as opposed to loose script files, and the C# script asset identifiers are different.</span></span> <span data-ttu-id="c0a4f-135">因此，MRTK 套件中的 prefabs 等資產已更新為參考適當的已編譯腳本。</span><span class="sxs-lookup"><span data-stu-id="c0a4f-135">As such, the assets like prefabs in the MRTK package have been updated to reference the appropriate compiled script.</span></span> <span data-ttu-id="c0a4f-136">使用 unitypackage 或 MRTK 來源版本的專案也必須重新設定其資產的目標，雖然有程式碼，但這並不是支援的案例。</span><span class="sxs-lookup"><span data-stu-id="c0a4f-136">A project using the .unitypackage or source version of MRTK will have to re-target its assets as well, and although there is code for it this is not a supported scenario, yet.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c0a4f-137">目前不支援從 unitypackage 或來源遷移至 NuGet 的方式。</span><span class="sxs-lookup"><span data-stu-id="c0a4f-137">There is no currently supported way of migrating to NuGet from .unitypackage or source.</span></span> <span data-ttu-id="c0a4f-138">當我們繼續開發此傳遞機制時，這將會改變。</span><span class="sxs-lookup"><span data-stu-id="c0a4f-138">This will change as we continue development on this delivery mechanism.</span></span>

### <a name="compiled-binaries-nuget-vs-source-files-unitypackage"></a><span data-ttu-id="c0a4f-139">已編譯的二進位檔 (NuGet) 與來源檔案 (. unitypackage) </span><span class="sxs-lookup"><span data-stu-id="c0a4f-139">Compiled binaries (NuGet) vs source files (.unitypackage)</span></span>

<span data-ttu-id="c0a4f-140">由於 NuGet 套件包含已編譯的二進位檔，而不是腳本，因此有兩個主要優點：</span><span class="sxs-lookup"><span data-stu-id="c0a4f-140">Since the NuGet package contains the compiled binaries instead of scripts, this has two major advantages:</span></span>

- <span data-ttu-id="c0a4f-141">縮短編譯時間</span><span class="sxs-lookup"><span data-stu-id="c0a4f-141">Reduced compilation time</span></span>
- <span data-ttu-id="c0a4f-142">Visual Studio 中的 c # 專案檔大幅減少</span><span class="sxs-lookup"><span data-stu-id="c0a4f-142">Considerably fewer C# project files in Visual Studio</span></span>

### <a name="debugging-mixed-reality-toolkit"></a><span data-ttu-id="c0a4f-143">調試混合現實工具組</span><span class="sxs-lookup"><span data-stu-id="c0a4f-143">Debugging Mixed Reality Toolkit</span></span>

<span data-ttu-id="c0a4f-144">Unity & 有已知的問題，Visual Studio Tools for Unity 防止 PDB 在 Visual Studio 偵錯工具中輕鬆地進行調試。</span><span class="sxs-lookup"><span data-stu-id="c0a4f-144">There are known issues with Unity & Visual Studio Tools for Unity that prevent a PDB from being easily debugged in Visual Studio Debugger.</span></span> <span data-ttu-id="c0a4f-145">因此，雖然封裝隨附 Pdb 和來源內嵌，但如果 Dll 是在本機建立的 (讀取) ，就可能會進行偵錯工具的偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="c0a4f-145">So although the package comes with PDBs and source embedded, debugging the DLLs is possible only if it was locally built (read further).</span></span> <span data-ttu-id="c0a4f-146">有一項因應措施是建立為 [MSBuildForUnity](https://github.com/microsoft/MSBuildForUnity/)的一部分，稍後會有更多更新。</span><span class="sxs-lookup"><span data-stu-id="c0a4f-146">There is a workaround being built as part of [MSBuildForUnity](https://github.com/microsoft/MSBuildForUnity/), more updates on that later.</span></span>

## <a name="locally-building-the-nuget-package"></a><span data-ttu-id="c0a4f-147">在本機建立 NuGet 套件</span><span class="sxs-lookup"><span data-stu-id="c0a4f-147">Locally building the NuGet package</span></span>

<span data-ttu-id="c0a4f-148">使用 MRTK 的最新來源，您可以在本機建立 NuGet 套件，並設定 NuGetForUnity 來挑選它。</span><span class="sxs-lookup"><span data-stu-id="c0a4f-148">With the latest source from MRTK, you can build the NuGet package locally and configure NuGetForUnity to pick it up.</span></span>

1. <span data-ttu-id="c0a4f-149">下載最新的 MRTK 來源。</span><span class="sxs-lookup"><span data-stu-id="c0a4f-149">Download the latest MRTK source.</span></span>
1. <span data-ttu-id="c0a4f-150">執行 `scripts\packaging\createnugetpackages.ps1` powershell 腳本。</span><span class="sxs-lookup"><span data-stu-id="c0a4f-150">Execute the `scripts\packaging\createnugetpackages.ps1` powershell script.</span></span>
    - <span data-ttu-id="c0a4f-151">藉 `-UnityDirectory` 由傳遞 Unity 安裝的編輯器資料夾來指定旗標</span><span class="sxs-lookup"><span data-stu-id="c0a4f-151">Specify the `-UnityDirectory` flag by passing the Editor folder of your Unity installation</span></span>
    - <span data-ttu-id="c0a4f-152">以 `-Version` x.x 格式指定要建立之封裝的。</span><span class="sxs-lookup"><span data-stu-id="c0a4f-152">Specify the `-Version` of the package to create, in x.x.x format.</span></span> <span data-ttu-id="c0a4f-153">**請確定版本高於 NuGet.org 的可用版本**</span><span class="sxs-lookup"><span data-stu-id="c0a4f-153">**Make sure the version is higher than available on NuGet.org**</span></span>
    - <span data-ttu-id="c0a4f-154">**範例：** `.\createnugetpackages.ps1 -UnityDirectory "C:\Program Files\Unity\Hub\Editor\2018.4.14f1\Editor" -Version 2.3.2`</span><span class="sxs-lookup"><span data-stu-id="c0a4f-154">**Example:** `.\createnugetpackages.ps1 -UnityDirectory "C:\Program Files\Unity\Hub\Editor\2018.4.14f1\Editor" -Version 2.3.2`</span></span>
1. <span data-ttu-id="c0a4f-155">組建成功之後，請使用 NuGet 套件開啟目的地專案。</span><span class="sxs-lookup"><span data-stu-id="c0a4f-155">After the build succeeds, open the destination project with NuGet packages.</span></span>
    - <span data-ttu-id="c0a4f-156">按一下功能表 **編輯**  >  **喜好** 設定 .。。</span><span class="sxs-lookup"><span data-stu-id="c0a4f-156">Click on the menu **Edit** > **Preferences...**</span></span>

        ![編輯喜好設定功能表項目](../Images/NuGet/ProjectPreferences.png)
    - <span data-ttu-id="c0a4f-158">在左側尋找 [ **適用于 Unity 的 NuGet** ] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="c0a4f-158">On the left, find **NuGet for Unity** tab.</span></span>

        ![編輯喜好設定功能表項目](../Images/NuGet/NuGetForUnityPreferencesTab.png)
    - <span data-ttu-id="c0a4f-160">按下 [ **新增來源** ]，並將 **source_path** 取代為 `<Path to your Repository>\NuGet\artifacts`</span><span class="sxs-lookup"><span data-stu-id="c0a4f-160">Press **Add New Source** and replace **source_path** with the `<Path to your Repository>\NuGet\artifacts`</span></span>

        ![編輯喜好設定功能表項目](../Images/NuGet/AddNewSource.png)
    - <span data-ttu-id="c0a4f-162">按一下底部的 [ **儲存** ] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="c0a4f-162">At the bottom, press the **Save** button.</span></span>

        ![編輯喜好設定功能表項目](../Images/NuGet/SaveNewSource.png)
1. <span data-ttu-id="c0a4f-164">如果這是您第一次建立或版本已遞增，請遵循更新程式：</span><span class="sxs-lookup"><span data-stu-id="c0a4f-164">If this your first time building, or the version was incremented, follow the update process:</span></span>
    1. <span data-ttu-id="c0a4f-165">在 Unity 功能表列中，按一下 [ **nuget**  >  **管理 nuget 封裝**]。</span><span class="sxs-lookup"><span data-stu-id="c0a4f-165">In the Unity menu bar, click on **NuGet** > **Manage NuGet Packages**.</span></span>

        ![Manage NuGet Packages](../Images/NuGet/ManageNuGetPackages.png)
    1. <span data-ttu-id="c0a4f-167">切換至 [ **更新** ] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="c0a4f-167">Switch to the **Updates** tab.</span></span>

        ![Manage NuGet Packages](../Images/NuGet/UpdatesTab.png)
    1. <span data-ttu-id="c0a4f-169">將套件更新為您剛剛所建立的版本。</span><span class="sxs-lookup"><span data-stu-id="c0a4f-169">Update the packages to the version you just built desired.</span></span>
1. <span data-ttu-id="c0a4f-170">否則，只需刪除 `Assets\Packages` 資料夾並讓 NuGetForUnity 還原封裝即可。</span><span class="sxs-lookup"><span data-stu-id="c0a4f-170">Otherwise, just delete the `Assets\Packages` folder and let NuGetForUnity restore the packages.</span></span>

## <a name="see-also"></a><span data-ttu-id="c0a4f-171">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c0a4f-171">See also</span></span>

- [<span data-ttu-id="c0a4f-172">建立和部署 MRTK</span><span class="sxs-lookup"><span data-stu-id="c0a4f-172">Building and Deploying MRTK</span></span>](../../updates-deployment/BuildAndDeploy.md)
- [<span data-ttu-id="c0a4f-173">MRTK 套件內容</span><span class="sxs-lookup"><span data-stu-id="c0a4f-173">MRTK Package Contents</span></span>](MRTK_PackageContents.md)
