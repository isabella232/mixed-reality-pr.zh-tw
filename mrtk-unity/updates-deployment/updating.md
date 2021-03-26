---
title: 更新
description: 從較低版本的 MRTK 遷移的檔。
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: 0cad7b2cf2b9c2afc386467966bfe536e23891b2
ms.sourcegitcommit: ac315c1d35f2b9c431e79bc3f1212215301bb867
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105550818"
---
# <a name="updating-the-microsoft-mixed-reality-toolkit"></a><span data-ttu-id="e12a6-104">更新 Microsoft Mixed Reality 工具組</span><span class="sxs-lookup"><span data-stu-id="e12a6-104">Updating the Microsoft Mixed Reality Toolkit</span></span>

- [<span data-ttu-id="e12a6-105">升級至新版本的 MRTK</span><span class="sxs-lookup"><span data-stu-id="e12a6-105">Upgrading to a new version of MRTK</span></span>](#upgrading-to-a-new-version-of-mrtk)
- [<span data-ttu-id="e12a6-106">2.3.0 至2.4。0</span><span class="sxs-lookup"><span data-stu-id="e12a6-106">2.3.0 to 2.4.0</span></span>](#updating-230-to-240)
- [<span data-ttu-id="e12a6-107">2.2.0 至2.3。0</span><span class="sxs-lookup"><span data-stu-id="e12a6-107">2.2.0 to 2.3.0</span></span>](#updating-220-to-230)
- [<span data-ttu-id="e12a6-108">2.1.0 至2.2。0</span><span class="sxs-lookup"><span data-stu-id="e12a6-108">2.1.0 to 2.2.0</span></span>](#updating-210-to-220)
- [<span data-ttu-id="e12a6-109">2.0.0 至2.1。0</span><span class="sxs-lookup"><span data-stu-id="e12a6-109">2.0.0 to 2.1.0</span></span>](#updating-200-to-210)
- [<span data-ttu-id="e12a6-110">RC2 至2.0。0</span><span class="sxs-lookup"><span data-stu-id="e12a6-110">RC2 to 2.0.0</span></span>](#updating-rc2-to-200)

## <a name="finding-the-current-version"></a><span data-ttu-id="e12a6-111">尋找目前的版本</span><span class="sxs-lookup"><span data-stu-id="e12a6-111">Finding the current version</span></span> 

<span data-ttu-id="e12a6-112">請遵循下列指示，找出您目前所使用的 MRTK 版本：</span><span class="sxs-lookup"><span data-stu-id="e12a6-112">Follow these instructions to figure out which version of the MRTK you're currently using:</span></span>

1. <span data-ttu-id="e12a6-113">在 Unity 中開啟您的 MRTK 專案</span><span class="sxs-lookup"><span data-stu-id="e12a6-113">Open your MRTK project in Unity</span></span>
2. <span data-ttu-id="e12a6-114">在您的 [專案] 視窗中，流覽至 "MixedRealityToolkit" 資料夾</span><span class="sxs-lookup"><span data-stu-id="e12a6-114">Navigate to the "MixedRealityToolkit" folder in your Project window</span></span>
3. <span data-ttu-id="e12a6-115">開啟名為「版本」的檔案</span><span class="sxs-lookup"><span data-stu-id="e12a6-115">Open the file called "Version"</span></span>

<span data-ttu-id="e12a6-116">如果上述的檔案和資料夾不存在，您就會使用較新版本的 MRTK。</span><span class="sxs-lookup"><span data-stu-id="e12a6-116">If the file and folder above doesn't exist, you're on a newer version of the MRTK.</span></span> <span data-ttu-id="e12a6-117">在此情況下，請嘗試下列動作：</span><span class="sxs-lookup"><span data-stu-id="e12a6-117">In that case, try the following:</span></span>

1. <span data-ttu-id="e12a6-118">流覽至「混合現實工具組基礎」資料夾</span><span class="sxs-lookup"><span data-stu-id="e12a6-118">Navigate to the "Mixed Reality Toolkit Foundation" folder</span></span>
2. <span data-ttu-id="e12a6-119">按一下 [package.js開啟] 以查看 Unity 中的預覽，或使用文字編輯器來開啟該預覽版</span><span class="sxs-lookup"><span data-stu-id="e12a6-119">Click on the "package.json" to see a preview in Unity or open it with a text editor</span></span>
3. <span data-ttu-id="e12a6-120">尋找含有 "version：" 這個字的行</span><span class="sxs-lookup"><span data-stu-id="e12a6-120">Look for the line with the word "version:"</span></span> 

## <a name="upgrading-to-a-new-version-of-mrtk"></a><span data-ttu-id="e12a6-121">升級至新版本的 MRTK</span><span class="sxs-lookup"><span data-stu-id="e12a6-121">Upgrading to a new version of MRTK</span></span>

<span data-ttu-id="e12a6-122">*強烈建議您在取得 MRTK 更新 [](../features/tools/migration-window.md)* 以自動修正，並從已淘汰的元件升級並進行升級時，執行遷移工具以進行中斷變更。</span><span class="sxs-lookup"><span data-stu-id="e12a6-122">*It is strongly recommended to run the [migration tool](../features/tools/migration-window.md) after getting the MRTK update* to auto-fix and upgrade from deprecated components and adjust to breaking changes.</span></span> <span data-ttu-id="e12a6-123">遷移工具是 **工具** 套件的一部分。</span><span class="sxs-lookup"><span data-stu-id="e12a6-123">The migration tool is part of the **Tools** package.</span></span>

<span data-ttu-id="e12a6-124">下列指示說明2.5.0 升級路徑的2.4.0。</span><span class="sxs-lookup"><span data-stu-id="e12a6-124">The instructions below describe the 2.4.0 to 2.5.0 upgrade path.</span></span> <span data-ttu-id="e12a6-125">如果您的專案是在2.3.0 或更早版本上，請閱讀各 [版本之間](#updating-230-to-240) 的變更，以瞭解升級路徑，或閱讀先前版本 [的指示](https://microsoft.github.io/MixedRealityToolkit-Unity/version/releases/2.4.0/Documentation/Updating.html) ，以進行版本版本的升級。</span><span class="sxs-lookup"><span data-stu-id="e12a6-125">If your project is on 2.3.0 or earlier, read on to the changes [between versions](#updating-230-to-240) to understand the upgrade path, or read the previous [release's instructions](https://microsoft.github.io/MixedRealityToolkit-Unity/version/releases/2.4.0/Documentation/Updating.html) to do a version-by-version upgrade.</span></span>

### <a name="mixed-reality-feature-tool"></a><span data-ttu-id="e12a6-126">混合現實功能工具</span><span class="sxs-lookup"><span data-stu-id="e12a6-126">Mixed Reality Feature Tool</span></span>
<span data-ttu-id="e12a6-127">將 MRTK 升級至較新版本的 MRTK 最簡單的方式，就是使用「 [混合現實」功能工具](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool) 來下載最新的套件，並將它們直接載入至 Unity 專案。</span><span class="sxs-lookup"><span data-stu-id="e12a6-127">The easiest way to upgrade MRTK to a newer version MRTK is by using the [Mixed Reality Feature Tool](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool) to download the latest packages and load them directly to your Unity project.</span></span>

### <a name="unity-asset-unitypackage-files"></a><span data-ttu-id="e12a6-128">Unity 資產 (. unitypackage) 檔案</span><span class="sxs-lookup"><span data-stu-id="e12a6-128">Unity asset (.unitypackage) files</span></span>

<span data-ttu-id="e12a6-129">另一個升級路徑是手動下載 MRTK Unity 套件，並將其套用至您的專案。</span><span class="sxs-lookup"><span data-stu-id="e12a6-129">Another upgrade path is to manually download MRTK Unity packages and apply them to your project.</span></span> <span data-ttu-id="e12a6-130">請參閱下列步驟：</span><span class="sxs-lookup"><span data-stu-id="e12a6-130">See the steps below,</span></span>

1. <span data-ttu-id="e12a6-131">如果您在升級步驟中的任何時間點遇到任何阻礙，請儲存目前專案的複本。</span><span class="sxs-lookup"><span data-stu-id="e12a6-131">Save a copy of your current project, in case you hit any snags at any point in the upgrade steps.</span></span>
1. <span data-ttu-id="e12a6-132">關閉 Unity</span><span class="sxs-lookup"><span data-stu-id="e12a6-132">Close Unity</span></span>
1. <span data-ttu-id="e12a6-133">在 [ *資產* ] 資料夾內，刪除下列 **MRTK** 資料夾以及其 (專案可能沒有所有列出的資料夾) </span><span class="sxs-lookup"><span data-stu-id="e12a6-133">Inside the *Assets* folder, delete the following **MRTK** folders, along with their .meta files (the project may not have all listed folders)</span></span>
    - <span data-ttu-id="e12a6-134">MRTK/核心</span><span class="sxs-lookup"><span data-stu-id="e12a6-134">MRTK/Core</span></span>
    - <span data-ttu-id="e12a6-135">MRTK/範例</span><span class="sxs-lookup"><span data-stu-id="e12a6-135">MRTK/Examples</span></span>
    - <span data-ttu-id="e12a6-136">MRTK/擴充功能</span><span class="sxs-lookup"><span data-stu-id="e12a6-136">MRTK/Extensions</span></span>
    > [!NOTE]
    > <span data-ttu-id="e12a6-137">如果已安裝其他延伸模組，請在刪除這些資料夾之前進行備份。</span><span class="sxs-lookup"><span data-stu-id="e12a6-137">If additional extensions have been installed, please make a backup prior to deleting these folders.</span></span>
    - <span data-ttu-id="e12a6-138">MRTK/提供者</span><span class="sxs-lookup"><span data-stu-id="e12a6-138">MRTK/Providers</span></span>
    - <span data-ttu-id="e12a6-139">MRTK/SDK</span><span class="sxs-lookup"><span data-stu-id="e12a6-139">MRTK/SDK</span></span>
    - <span data-ttu-id="e12a6-140">MRTK/服務</span><span class="sxs-lookup"><span data-stu-id="e12a6-140">MRTK/Services</span></span>
    - <span data-ttu-id="e12a6-141">MRTK/工具</span><span class="sxs-lookup"><span data-stu-id="e12a6-141">MRTK/Tools</span></span>
    > [!IMPORTANT]
    > <span data-ttu-id="e12a6-142">請勿刪除 **MixedRealityToolkit 產生** 的資料夾或其中繼檔案。</span><span class="sxs-lookup"><span data-stu-id="e12a6-142">Do NOT delete the **MixedRealityToolkit.Generated** folder, or its .meta file.</span></span>
1. <span data-ttu-id="e12a6-143">刪除連結 **庫** 資料夾</span><span class="sxs-lookup"><span data-stu-id="e12a6-143">Delete the **Library** folder</span></span>
    > [!IMPORTANT]
    > <span data-ttu-id="e12a6-144">某些 Unity 工具（例如 Unity Collaboration）會將設定資訊儲存至程式庫資料夾。</span><span class="sxs-lookup"><span data-stu-id="e12a6-144">Some Unity tools, like Unity Collab, save configuration info to the Library folder.</span></span> <span data-ttu-id="e12a6-145">如果使用執行這項工作的工具，請先從程式庫複製工具的 [資料] 資料夾，然後再進行刪除，然後在重新產生程式庫之後將其還原。</span><span class="sxs-lookup"><span data-stu-id="e12a6-145">If using a tool that does this, first copy the tool's data folder from Library before deleting, then restore it after Library is regenerated.</span></span>
1. <span data-ttu-id="e12a6-146">在 Unity 中重新開啟專案</span><span class="sxs-lookup"><span data-stu-id="e12a6-146">Re-open the project in Unity</span></span>
1. <span data-ttu-id="e12a6-147">匯入新的 unity 套件</span><span class="sxs-lookup"><span data-stu-id="e12a6-147">Import the new unity packages</span></span>
    - <span data-ttu-id="e12a6-148">基礎- _先匯入此套件_</span><span class="sxs-lookup"><span data-stu-id="e12a6-148">Foundation - _Import this package first_</span></span>
    - <span data-ttu-id="e12a6-149">工具</span><span class="sxs-lookup"><span data-stu-id="e12a6-149">Tools</span></span>
    - <span data-ttu-id="e12a6-150"> (選用) 擴充功能</span><span class="sxs-lookup"><span data-stu-id="e12a6-150">(Optional) Extensions</span></span>
    > [!NOTE]
    > <span data-ttu-id="e12a6-151">如果已安裝其他延伸模組，則可能需要重新匯入。</span><span class="sxs-lookup"><span data-stu-id="e12a6-151">If additional extensions had been installed, they may need to be re-imported.</span></span>
    - <span data-ttu-id="e12a6-152"> (選擇性) 範例</span><span class="sxs-lookup"><span data-stu-id="e12a6-152">(Optional) Examples</span></span>
1. <span data-ttu-id="e12a6-153">關閉 Unity 並刪除連結 **庫** 資料夾 (先閱讀以下的附注！ ) 。</span><span class="sxs-lookup"><span data-stu-id="e12a6-153">Close Unity and delete the **Library** folder (read the note below first!).</span></span> <span data-ttu-id="e12a6-154">必須執行此步驟，才能強制 Unity 重新整理其資產資料庫，並協調現有的自訂設定檔。</span><span class="sxs-lookup"><span data-stu-id="e12a6-154">This step is necessary to force Unity to refresh its asset database and reconcile existing custom profiles.</span></span>
1. <span data-ttu-id="e12a6-155">啟動 Unity，然後針對專案中的每個場景</span><span class="sxs-lookup"><span data-stu-id="e12a6-155">Launch Unity, and for each scene in the project</span></span>
    - <span data-ttu-id="e12a6-156">從階層中刪除 **MixedRealityToolkit** 和 **MixedRealityPlayspace**（如果有的話）。</span><span class="sxs-lookup"><span data-stu-id="e12a6-156">Delete **MixedRealityToolkit** and **MixedRealityPlayspace**, if present, from the hierarchy.</span></span> <span data-ttu-id="e12a6-157">這將會刪除主要相機，但會在下一個步驟中重新建立。</span><span class="sxs-lookup"><span data-stu-id="e12a6-157">This will delete the main camera, but it will be re-created in the next step.</span></span> <span data-ttu-id="e12a6-158">如果已手動變更主要相機的任何內容，則在建立新的相機之後，必須手動重新套用這些屬性。</span><span class="sxs-lookup"><span data-stu-id="e12a6-158">If any properties of the main camera have been manually changed, these will have to be re-applied manually once the new camera is created.</span></span>
    - <span data-ttu-id="e12a6-159">選取 **MixedRealityToolkit-> 新增至場景並設定**</span><span class="sxs-lookup"><span data-stu-id="e12a6-159">Select **MixedRealityToolkit -> Add to Scene and Configure**</span></span>
    - <span data-ttu-id="e12a6-160">選取 **MixedRealityToolkit-> 公用程式-> update-> 控制器對應設定檔** (只需要進行一次) -這會以更新的座標軸和資料更新任何自訂控制器對應設定檔，同時讓您的自訂指派輸入動作保持不變</span><span class="sxs-lookup"><span data-stu-id="e12a6-160">Select **MixedRealityToolkit -> Utilities -> Update -> Controller Mapping Profiles** (only needs to be done once)       - This will update any custom controller mapping profiles with updated axes and data, while leaving your custom-assigned input actions intact</span></span>
1. <span data-ttu-id="e12a6-161">執行 [遷移工具](../features/tools/migration-window.md) 並在 *完整的專案* 上執行工具，以確保您的所有程式碼都更新為最新版本。</span><span class="sxs-lookup"><span data-stu-id="e12a6-161">Run the [migration tool](../features/tools/migration-window.md) and run the tool on the *Full Project* to ensure that all of your code is updated to the latest.</span></span>
   <span data-ttu-id="e12a6-162">[遷移] 視窗包含許多不同的遷移處理常式，每個處理常式都必須自行執行。</span><span class="sxs-lookup"><span data-stu-id="e12a6-162">The migration window contains a number of different migration handlers, which must each be run on their own.</span></span> <span data-ttu-id="e12a6-163">此步驟包含：</span><span class="sxs-lookup"><span data-stu-id="e12a6-163">This step involves:</span></span>
   - <span data-ttu-id="e12a6-164">從 [ **遷移處理常式選取專案** ] 下拉式清單中，選取第一個遷移處理常式。</span><span class="sxs-lookup"><span data-stu-id="e12a6-164">Select the first migration handler from the **Migration Handler Selection** dropdown.</span></span>
   - <span data-ttu-id="e12a6-165">按一下 [完整專案] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="e12a6-165">Click the "Full Project" button.</span></span>
   - <span data-ttu-id="e12a6-166">按一下 [新增要遷移的完整專案] 按鈕 (這會掃描整個專案以取得要遷移) 的物件。</span><span class="sxs-lookup"><span data-stu-id="e12a6-166">Click the "Add full project for migration" button (this will scan the entire project for objects to migrate).</span></span>
   - <span data-ttu-id="e12a6-167">按一下 [遷移] 按鈕，如果找到任何 migrateable 物件，則應啟用此按鈕。</span><span class="sxs-lookup"><span data-stu-id="e12a6-167">Click the "Migrate" button which should be enabled if any migrateable objects were found.</span></span>
   - <span data-ttu-id="e12a6-168">針對下拉式清單中的每個遷移處理常式重複上述三個步驟。</span><span class="sxs-lookup"><span data-stu-id="e12a6-168">Repeat the previous three steps for each of the migration handlers within the dropdown.</span></span>
     <span data-ttu-id="e12a6-169"> (看到 [此問題](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8552) ，其中涵蓋可在未來版本中簡化此遷移程式的工作) </span><span class="sxs-lookup"><span data-stu-id="e12a6-169">(See [this issue](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8552) which covers work that can be done to simplify this migration process in a future release)</span></span>

## <a name="updating-230-to-240"></a><span data-ttu-id="e12a6-170">將2.3.0 更新為2.4。0</span><span class="sxs-lookup"><span data-stu-id="e12a6-170">Updating 2.3.0 to 2.4.0</span></span>

<span data-ttu-id="e12a6-171">[資料夾重新命名](#folder-renames-in-240) 
[API 變更](#api-changes-in-240)</span><span class="sxs-lookup"><span data-stu-id="e12a6-171">[Folder renames](#folder-renames-in-240)
[API changes](#api-changes-in-240)</span></span>

### <a name="folder-renames-in-240"></a><span data-ttu-id="e12a6-172">2.4.0 中的資料夾重新命名</span><span class="sxs-lookup"><span data-stu-id="e12a6-172">Folder renames in 2.4.0</span></span>

<span data-ttu-id="e12a6-173">MixedRealityToolkit 資料夾已重新命名並移至2.4 版中的通用階層。</span><span class="sxs-lookup"><span data-stu-id="e12a6-173">The MixedRealityToolkit folders have been renamed and moved into a common hierarchy in version 2.4.</span></span> <span data-ttu-id="e12a6-174">如果應用程式使用硬式編碼路徑來 MRTK 資源，則必須根據下表進行更新。</span><span class="sxs-lookup"><span data-stu-id="e12a6-174">If an application uses hard coded paths to MRTK resources, they will need to be updated per the following table.</span></span>

| <span data-ttu-id="e12a6-175">上一個資料夾</span><span class="sxs-lookup"><span data-stu-id="e12a6-175">Previous Folder</span></span> | <span data-ttu-id="e12a6-176">新增資料夾</span><span class="sxs-lookup"><span data-stu-id="e12a6-176">New Folder</span></span> |
| --- | --- |
| <span data-ttu-id="e12a6-177">MixedRealityToolkit</span><span class="sxs-lookup"><span data-stu-id="e12a6-177">MixedRealityToolkit</span></span> | <span data-ttu-id="e12a6-178">MRTK/核心</span><span class="sxs-lookup"><span data-stu-id="e12a6-178">MRTK/Core</span></span> |
| <span data-ttu-id="e12a6-179">MixedRealityToolkit 範例</span><span class="sxs-lookup"><span data-stu-id="e12a6-179">MixedRealityToolkit.Examples</span></span> | <span data-ttu-id="e12a6-180">MRTK/範例</span><span class="sxs-lookup"><span data-stu-id="e12a6-180">MRTK/Examples</span></span> |
| <span data-ttu-id="e12a6-181">MixedRealityToolkit 副檔名</span><span class="sxs-lookup"><span data-stu-id="e12a6-181">MixedRealityToolkit.Extensions</span></span> | <span data-ttu-id="e12a6-182">MRTK/擴充功能</span><span class="sxs-lookup"><span data-stu-id="e12a6-182">MRTK/Extensions</span></span> |
| <span data-ttu-id="e12a6-183">MixedRealityToolkit。提供者</span><span class="sxs-lookup"><span data-stu-id="e12a6-183">MixedRealityToolkit.Providers</span></span> | <span data-ttu-id="e12a6-184">MRTK/提供者</span><span class="sxs-lookup"><span data-stu-id="e12a6-184">MRTK/Providers</span></span> |
| <span data-ttu-id="e12a6-185">MixedRealityToolkit SDK</span><span class="sxs-lookup"><span data-stu-id="e12a6-185">MixedRealityToolkit.SDK</span></span> | <span data-ttu-id="e12a6-186">MRTK/SDK</span><span class="sxs-lookup"><span data-stu-id="e12a6-186">MRTK/SDK</span></span> |
| <span data-ttu-id="e12a6-187">MixedRealityToolkit 服務</span><span class="sxs-lookup"><span data-stu-id="e12a6-187">MixedRealityToolkit.Services</span></span> | <span data-ttu-id="e12a6-188">MRTK/服務</span><span class="sxs-lookup"><span data-stu-id="e12a6-188">MRTK/Services</span></span> |
| <span data-ttu-id="e12a6-189">MixedRealityToolkit。測試</span><span class="sxs-lookup"><span data-stu-id="e12a6-189">MixedRealityToolkit.Tests</span></span> | <span data-ttu-id="e12a6-190">MRTK/測試</span><span class="sxs-lookup"><span data-stu-id="e12a6-190">MRTK/Tests</span></span> |
| <span data-ttu-id="e12a6-191">MixedRealityToolkit 工具</span><span class="sxs-lookup"><span data-stu-id="e12a6-191">MixedRealityToolkit.Tools</span></span> | <span data-ttu-id="e12a6-192">MRTK/工具</span><span class="sxs-lookup"><span data-stu-id="e12a6-192">MRTK/Tools</span></span> |

> [!IMPORTANT]
> <span data-ttu-id="e12a6-193">`MixedRealityToolkit.Generated`包含客戶產生的檔案，且保持不變。</span><span class="sxs-lookup"><span data-stu-id="e12a6-193">The `MixedRealityToolkit.Generated` contains customer generated files and remains unchanged.</span></span>

### <a name="eye-gaze-setup-in-240"></a><span data-ttu-id="e12a6-194">2.4.0 中的眼睛設定</span><span class="sxs-lookup"><span data-stu-id="e12a6-194">Eye gaze setup in 2.4.0</span></span>

<span data-ttu-id="e12a6-195">此版本的 MRTK 會修改眼睛設定所需的步驟。</span><span class="sxs-lookup"><span data-stu-id="e12a6-195">This version of MRTK modifies the steps required for eye gaze setup.</span></span> <span data-ttu-id="e12a6-196">您可以在輸入指標設定檔的注視設定中找到 [ _IsEyeTrackingEnabled_ ] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="e12a6-196">The _'IsEyeTrackingEnabled'_ checkbox can be found in the gaze settings of the input pointer profile.</span></span> <span data-ttu-id="e12a6-197">核取此方塊將會啟用以眼睛為基礎的眼睛，而不是預設的標頭。</span><span class="sxs-lookup"><span data-stu-id="e12a6-197">Checking this box will enable eye based gaze, rather then the default head based gaze.</span></span>

<span data-ttu-id="e12a6-198">如需有關這些變更的詳細資訊，以及適用于眼睛追蹤設定的完整指示，請參閱 [眼睛追蹤](../features/input/eye-tracking/eye-tracking-basic-setup.md) 文章。</span><span class="sxs-lookup"><span data-stu-id="e12a6-198">For more information on these changes and complete instructions for eye tracking setup, please see the [eye tracking](../features/input/eye-tracking/eye-tracking-basic-setup.md) article.</span></span>

### <a name="eye-gaze-pointer-behavior-in-240"></a><span data-ttu-id="e12a6-199">2.4.0 中的眼睛指標行為</span><span class="sxs-lookup"><span data-stu-id="e12a6-199">Eye gaze pointer behavior in 2.4.0</span></span>

<span data-ttu-id="e12a6-200">眼睛的預設指標行為已經過修改，以符合標頭的預設指標行為。</span><span class="sxs-lookup"><span data-stu-id="e12a6-200">The eye gaze default pointer behavior have been modified to match the head gaze default pointer behavior.</span></span> <span data-ttu-id="e12a6-201">一旦偵測到手中，就會自動抑制眼睛指標。</span><span class="sxs-lookup"><span data-stu-id="e12a6-201">An eye gaze pointer will automatically be suppressed once a hand is detected.</span></span> <span data-ttu-id="e12a6-202">出現「選取」之後，眼睛指標將會再次顯示。</span><span class="sxs-lookup"><span data-stu-id="e12a6-202">The eye gaze pointer will become visible again after saying "Select".</span></span>

<span data-ttu-id="e12a6-203">有關注視和手的詳細資訊，請參閱 [眼睛和手](../features/input/eye-tracking/eye-tracking-eyes-and-hands.md#how-to-keep-gaze-pointer-always-on) 中的文章。</span><span class="sxs-lookup"><span data-stu-id="e12a6-203">Details about gaze and hand setups can be found in the [eyes and hands](../features/input/eye-tracking/eye-tracking-eyes-and-hands.md#how-to-keep-gaze-pointer-always-on) article.</span></span>

### <a name="api-changes-in-240"></a><span data-ttu-id="e12a6-204">2.4.0 中的 API 變更</span><span class="sxs-lookup"><span data-stu-id="e12a6-204">API changes in 2.4.0</span></span>

<span data-ttu-id="e12a6-205">**自訂控制器類別**</span><span class="sxs-lookup"><span data-stu-id="e12a6-205">**Custom controller classes**</span></span>

<span data-ttu-id="e12a6-206">自訂控制器類別先前必須定義 `SetupDefaultInteractions(Handedness)` 。</span><span class="sxs-lookup"><span data-stu-id="e12a6-206">Custom controller classes previously had to define `SetupDefaultInteractions(Handedness)`.</span></span> <span data-ttu-id="e12a6-207">此方法已在2.4 中淘汰，因為 handedness 參數對控制器類別的 handedness 是多餘的。</span><span class="sxs-lookup"><span data-stu-id="e12a6-207">This method has been made obsolete in 2.4, as the handedness parameter was redundant with the controller class' own handedness.</span></span> <span data-ttu-id="e12a6-208">新方法沒有任何參數。</span><span class="sxs-lookup"><span data-stu-id="e12a6-208">The new method has no parameters.</span></span> <span data-ttu-id="e12a6-209">此外，許多控制器類別的定義方式和 () 的方式相同 `AssignControllerMappings(DefaultInteractions);` ，因此完整的呼叫已細分成 `BaseController` 並進行選擇性的覆寫，而不是必要的。</span><span class="sxs-lookup"><span data-stu-id="e12a6-209">Additionally, many controller classes defined this the same way (`AssignControllerMappings(DefaultInteractions);`), so the full call has been refactored down into `BaseController` and made an optional override instead of required.</span></span>

<span data-ttu-id="e12a6-210">**眼睛眼屬性**</span><span class="sxs-lookup"><span data-stu-id="e12a6-210">**Eye Gaze properties**</span></span>

<span data-ttu-id="e12a6-211">`UseEyeTracking`從執行的屬性 `GazeProvider` 已重新 `IMixedRealityEyeGazeProvider` 命名為 `IsEyeTrackingEnabled` 。</span><span class="sxs-lookup"><span data-stu-id="e12a6-211">The `UseEyeTracking` property from `GazeProvider` implementation of `IMixedRealityEyeGazeProvider` was renamed to `IsEyeTrackingEnabled`.</span></span>

<span data-ttu-id="e12a6-212">如果您先前已執行此操作 .。。</span><span class="sxs-lookup"><span data-stu-id="e12a6-212">If you did this previously...</span></span>

```csharp
if (CoreServices.InputSystem.GazeProvider is GazeProvider gazeProvider)
{
    gazeProvider.UseEyeTracking = true;
}
```

<span data-ttu-id="e12a6-213">現在就完成了 .。。</span><span class="sxs-lookup"><span data-stu-id="e12a6-213">Do this now...</span></span>

```csharp
if (CoreServices.InputSystem.GazeProvider is GazeProvider gazeProvider)
{
    gazeProvider.IsEyeTrackingEnabled = true;
}
```

<span data-ttu-id="e12a6-214">**WindowsApiChecker 屬性**</span><span class="sxs-lookup"><span data-stu-id="e12a6-214">**WindowsApiChecker properties**</span></span>

<span data-ttu-id="e12a6-215">下列 WindowsApiChecker 屬性已標示為過時。</span><span class="sxs-lookup"><span data-stu-id="e12a6-215">The following WindowsApiChecker properties have been marked as obsolete.</span></span> <span data-ttu-id="e12a6-216">請使用 `IsMethodAvailable` 、 `IsPropertyAvailable` 或 `IsTypeAvailable` 。</span><span class="sxs-lookup"><span data-stu-id="e12a6-216">Please use `IsMethodAvailable`, `IsPropertyAvailable` or `IsTypeAvailable`.</span></span>

- <span data-ttu-id="e12a6-217">UniversalApiContractV8_IsAvailable</span><span class="sxs-lookup"><span data-stu-id="e12a6-217">UniversalApiContractV8_IsAvailable</span></span>
- <span data-ttu-id="e12a6-218">UniversalApiContractV7_IsAvailable</span><span class="sxs-lookup"><span data-stu-id="e12a6-218">UniversalApiContractV7_IsAvailable</span></span>
- <span data-ttu-id="e12a6-219">UniversalApiContractV6_IsAvailable</span><span class="sxs-lookup"><span data-stu-id="e12a6-219">UniversalApiContractV6_IsAvailable</span></span>
- <span data-ttu-id="e12a6-220">UniversalApiContractV5_IsAvailable</span><span class="sxs-lookup"><span data-stu-id="e12a6-220">UniversalApiContractV5_IsAvailable</span></span>
- <span data-ttu-id="e12a6-221">UniversalApiContractV4_IsAvailable</span><span class="sxs-lookup"><span data-stu-id="e12a6-221">UniversalApiContractV4_IsAvailable</span></span>
- <span data-ttu-id="e12a6-222">UniversalApiContractV3_IsAvailable</span><span class="sxs-lookup"><span data-stu-id="e12a6-222">UniversalApiContractV3_IsAvailable</span></span>

<span data-ttu-id="e12a6-223">基於未來的 API 合約版本，不打算將屬性新增至 WindowsApiChecker。</span><span class="sxs-lookup"><span data-stu-id="e12a6-223">There are no plans to add properties to WindowsApiChecker for future API contract versions.</span></span>

<span data-ttu-id="e12a6-224">**GltfMeshPrimitiveAttributes 唯讀**</span><span class="sxs-lookup"><span data-stu-id="e12a6-224">**GltfMeshPrimitiveAttributes read-only**</span></span>

<span data-ttu-id="e12a6-225">Gltf 網格基本屬性是用來設定的，現在它們是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="e12a6-225">The gltf mesh primitive attributes used to be settable, they are now read-only.</span></span> <span data-ttu-id="e12a6-226">還原序列化時，它們的值會設定一次。</span><span class="sxs-lookup"><span data-stu-id="e12a6-226">Their values will be set once when deserialized.</span></span>

### <a name="custom-button-icon-migration"></a><span data-ttu-id="e12a6-227">自訂按鈕圖示遷移</span><span class="sxs-lookup"><span data-stu-id="e12a6-227">Custom Button Icon Migration</span></span>

<span data-ttu-id="e12a6-228">先前的自訂按鈕圖示需要將新的材質指派給按鈕的四轉譯器。</span><span class="sxs-lookup"><span data-stu-id="e12a6-228">Previously custom button icons required assigning a new material to the button's quad renderer.</span></span> <span data-ttu-id="e12a6-229">這已不再是必要的，建議您將自訂圖示材質移至 IconSet。</span><span class="sxs-lookup"><span data-stu-id="e12a6-229">This is no longer necessary and we recommend moving custom icon textures into an IconSet.</span></span> <span data-ttu-id="e12a6-230">系統會保留現有的自訂材質和圖示。</span><span class="sxs-lookup"><span data-stu-id="e12a6-230">Existing custom materials and icons are preserved.</span></span> <span data-ttu-id="e12a6-231">不過，在升級之前，它們將會較不理想。</span><span class="sxs-lookup"><span data-stu-id="e12a6-231">However they will be less optimal until upgraded.</span></span>
<span data-ttu-id="e12a6-232">若要將專案中所有按鈕的資產升級為新的建議格式，請使用 ButtonConfigHelperMigrationHandler。</span><span class="sxs-lookup"><span data-stu-id="e12a6-232">To upgrade the assets on all buttons in the project to the new recommended format, use the ButtonConfigHelperMigrationHandler.</span></span>
<span data-ttu-id="e12a6-233"> (混合現實工具組-> 公用程式-> 的遷移視窗-> 的遷移處理常式選取範圍-> MixedReality) </span><span class="sxs-lookup"><span data-stu-id="e12a6-233">(Mixed Reality Toolkit -> Utilities -> Migration Window -> Migration Handler Selection -> Microsoft.MixedReality.Toolkit.Utilities.ButtonConfigHelperMigrationHandler)</span></span>

![升級視窗對話方塊](https://user-images.githubusercontent.com/39840334/82096923-bd28bf80-96b6-11ea-93a9-ceafcb822242.png)

<span data-ttu-id="e12a6-235">如果在遷移期間于預設的圖示集中找不到圖示，則會在 MixedRealityToolkit 中建立自訂圖示集。產生/CustomIconSets。</span><span class="sxs-lookup"><span data-stu-id="e12a6-235">If an icon is not found in the default icon set during migration, a custom icon set will be created in MixedRealityToolkit.Generated/CustomIconSets.</span></span> <span data-ttu-id="e12a6-236">對話方塊會指出已發生此情況。</span><span class="sxs-lookup"><span data-stu-id="e12a6-236">A dialog will indicate that this has taken place.</span></span>

![自訂圖示通知](https://user-images.githubusercontent.com/9789716/82093856-c57dfc00-96b0-11ea-83ab-4df57446d661.PNG)

## <a name="updating-220-to-230"></a><span data-ttu-id="e12a6-238">將2.2.0 更新為2.3。0</span><span class="sxs-lookup"><span data-stu-id="e12a6-238">Updating 2.2.0 to 2.3.0</span></span>

- [<span data-ttu-id="e12a6-239">API 變更</span><span class="sxs-lookup"><span data-stu-id="e12a6-239">API changes</span></span>](#api-changes-in-230)

### <a name="api-changes-in-230"></a><span data-ttu-id="e12a6-240">2.3.0 中的 API 變更</span><span class="sxs-lookup"><span data-stu-id="e12a6-240">API changes in 2.3.0</span></span>

<span data-ttu-id="e12a6-241">**ControllerPoseSynchronizer**</span><span class="sxs-lookup"><span data-stu-id="e12a6-241">**ControllerPoseSynchronizer**</span></span>

<span data-ttu-id="e12a6-242">私用 ControllerPoseSynchronizer. handedness 欄位已標示為過時。</span><span class="sxs-lookup"><span data-stu-id="e12a6-242">The private ControllerPoseSynchronizer.handedness field has been marked as obsolete.</span></span> <span data-ttu-id="e12a6-243">這應該會對應用程式造成最大影響，因為欄位不會顯示在其類別之外。</span><span class="sxs-lookup"><span data-stu-id="e12a6-243">This should have minimal impact on applications as the field is not visible outside of its class.</span></span>

<span data-ttu-id="e12a6-244">已 ([#7012](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/7012)) 移除 public ControllerPoseSynchronizer. Handedness 屬性的 setter。</span><span class="sxs-lookup"><span data-stu-id="e12a6-244">The public ControllerPoseSynchronizer.Handedness property's setter has been removed ([#7012](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/7012)).</span></span>

<span data-ttu-id="e12a6-245">**適用于 Unity 的 MSBuild**</span><span class="sxs-lookup"><span data-stu-id="e12a6-245">**MSBuild for Unity**</span></span>

<span data-ttu-id="e12a6-246">此版本的 MRTK 使用與舊版 MSBuild for Unity 的較新版本。</span><span class="sxs-lookup"><span data-stu-id="e12a6-246">This version of MRTK uses a newer version of MSBuild for Unity than previous releases.</span></span> <span data-ttu-id="e12a6-247">在專案載入期間，如果較舊的版本列在 Unity 套件管理員資訊清單中，則會顯示 [設定] 對話方塊，並核取 [啟用 MSBuild for Unity] 選項。</span><span class="sxs-lookup"><span data-stu-id="e12a6-247">During project load, if the older version is listed in the Unity Package Manger manifest, the configuration dialog will appear, with the Enable MSBuild for Unity option checked.</span></span> <span data-ttu-id="e12a6-248">應用程式將會執行升級。</span><span class="sxs-lookup"><span data-stu-id="e12a6-248">Applying will perform an upgrade.</span></span>

<span data-ttu-id="e12a6-249">**ScriptingUtilities**</span><span class="sxs-lookup"><span data-stu-id="e12a6-249">**ScriptingUtilities**</span></span>

<span data-ttu-id="e12a6-250">ScriptingUtilities 類別已標示為已淘汰，且已由 ScriptUtilities 取代，位於 MixedReality 元件中。</span><span class="sxs-lookup"><span data-stu-id="e12a6-250">The ScriptingUtilities class has been marked as obsolete and has been replaced by ScriptUtilities, in the Microsoft.MixedReality.Toolkit.Editor.Utilities assembly.</span></span> <span data-ttu-id="e12a6-251">新的類別會改善先前的行為，並加入移除腳本定義的支援。</span><span class="sxs-lookup"><span data-stu-id="e12a6-251">The new class refines previous behavior and adds support for removing scripting definitions.</span></span>

<span data-ttu-id="e12a6-252">雖然現有的程式碼在版本2.3.0 中仍可繼續運作，但建議您更新至新的類別。</span><span class="sxs-lookup"><span data-stu-id="e12a6-252">While existing code will continue to function in version 2.3.0, it is recommended to update to the new class.</span></span>

<span data-ttu-id="e12a6-253">**ShellHandRayPointer**</span><span class="sxs-lookup"><span data-stu-id="e12a6-253">**ShellHandRayPointer**</span></span>

<span data-ttu-id="e12a6-254">ShellHandRayPointer 類別的 lineRendererSelected 和 lineRendererNoTarget 成員已由 lineMaterialSelected 和 lineMaterialNoTarget 分別取代 ([#6863](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6863)) 。</span><span class="sxs-lookup"><span data-stu-id="e12a6-254">The lineRendererSelected and lineRendererNoTarget members of the ShellHandRayPointer class have been replaced by lineMaterialSelected and lineMaterialNoTarget, respectively ([#6863](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6863)).</span></span>

<span data-ttu-id="e12a6-255">請將 lineRendererSelected 取代為 lineMaterialSelected 和/或 lineRendererNoTarget with lineMaterialNoTarget，以解決編譯錯誤。</span><span class="sxs-lookup"><span data-stu-id="e12a6-255">Please replace lineRendererSelected with lineMaterialSelected and/or lineRendererNoTarget with lineMaterialNoTarget to resolve compile errors.</span></span>

<span data-ttu-id="e12a6-256">**空間觀察者讓 microsoft.systemforcrossdomainidentitymanagement.iprovider.startupbehavior**</span><span class="sxs-lookup"><span data-stu-id="e12a6-256">**Spatial observer StartupBehavior**</span></span>

<span data-ttu-id="e12a6-257">以類別為基礎的空間觀察者現在會在 `BaseSpatialObserver` 重新啟用 ([#6919](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6919)) 時，接受讓 microsoft.systemforcrossdomainidentitymanagement.iprovider.startupbehavior 的值。</span><span class="sxs-lookup"><span data-stu-id="e12a6-257">Spatial observers built upon the `BaseSpatialObserver` class now honor the value of StartupBehavior when re-enabled ([#6919](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6919)).</span></span>

<span data-ttu-id="e12a6-258">不需要進行任何變更，即可充分利用此修正。</span><span class="sxs-lookup"><span data-stu-id="e12a6-258">No changes are required to take advantage of this fix.</span></span>

<span data-ttu-id="e12a6-259">**UX 控制項 prefabs 已更新為使用 PressableButton**</span><span class="sxs-lookup"><span data-stu-id="e12a6-259">**UX control prefabs updated to use PressableButton**</span></span>

<span data-ttu-id="e12a6-260">下列 prefabs 現在使用 PressableButton 元件，而不是 TouchHandler 接近互動 ([7070](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/7070)) </span><span class="sxs-lookup"><span data-stu-id="e12a6-260">The following prefabs are now using the PressableButton component instead of TouchHandler for near interaction ([7070](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/7070))</span></span>

- <span data-ttu-id="e12a6-261">AnimationButton</span><span class="sxs-lookup"><span data-stu-id="e12a6-261">AnimationButton</span></span>
- <span data-ttu-id="e12a6-262">按鈕</span><span class="sxs-lookup"><span data-stu-id="e12a6-262">Button</span></span>
- <span data-ttu-id="e12a6-263">ButtonHoloLens1</span><span class="sxs-lookup"><span data-stu-id="e12a6-263">ButtonHoloLens1</span></span>
- <span data-ttu-id="e12a6-264">ButtonHoloLens1Toggle</span><span class="sxs-lookup"><span data-stu-id="e12a6-264">ButtonHoloLens1Toggle</span></span>
- <span data-ttu-id="e12a6-265">核取方塊</span><span class="sxs-lookup"><span data-stu-id="e12a6-265">CheckBox</span></span>
- <span data-ttu-id="e12a6-266">RadialSet</span><span class="sxs-lookup"><span data-stu-id="e12a6-266">RadialSet</span></span>
- <span data-ttu-id="e12a6-267">ToggleButton</span><span class="sxs-lookup"><span data-stu-id="e12a6-267">ToggleButton</span></span>
- <span data-ttu-id="e12a6-268">ToggleSwitch</span><span class="sxs-lookup"><span data-stu-id="e12a6-268">ToggleSwitch</span></span>
- <span data-ttu-id="e12a6-269">UnityUIButton</span><span class="sxs-lookup"><span data-stu-id="e12a6-269">UnityUIButton</span></span>
- <span data-ttu-id="e12a6-270">UnityUICheckboxButton</span><span class="sxs-lookup"><span data-stu-id="e12a6-270">UnityUICheckboxButton</span></span>
- <span data-ttu-id="e12a6-271">UnityUIRadialButton</span><span class="sxs-lookup"><span data-stu-id="e12a6-271">UnityUIRadialButton</span></span>
- <span data-ttu-id="e12a6-272">UnityUIToggleButton</span><span class="sxs-lookup"><span data-stu-id="e12a6-272">UnityUIToggleButton</span></span>

<span data-ttu-id="e12a6-273">應用程式程式碼可能會因為這種變更而需要更新。</span><span class="sxs-lookup"><span data-stu-id="e12a6-273">Application code may require updating due to this change.</span></span>

<span data-ttu-id="e12a6-274">**WindowsMixedRealityUtilities 命名空間**</span><span class="sxs-lookup"><span data-stu-id="e12a6-274">**WindowsMixedRealityUtilities namespace**</span></span>

<span data-ttu-id="e12a6-275">WindowsMixedRealityUtilities 的命名空間已從 MixedReality 變更為 WindowsMixedReality， [#6863](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6989))  (的命名空間。</span><span class="sxs-lookup"><span data-stu-id="e12a6-275">The namespace of WindowsMixedRealityUtilities changed from Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input to Microsoft.MixedReality.Toolkit.WindowsMixedReality ([#6863](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6989)).</span></span>

<span data-ttu-id="e12a6-276">請更新 #using 語句，以解決編譯錯誤。</span><span class="sxs-lookup"><span data-stu-id="e12a6-276">Please update #using statements to resolve compile errors.</span></span>

## <a name="updating-210-to-220"></a><span data-ttu-id="e12a6-277">將2.1.0 更新為2.2。0</span><span class="sxs-lookup"><span data-stu-id="e12a6-277">Updating 2.1.0 to 2.2.0</span></span>

- [<span data-ttu-id="e12a6-278">API 變更</span><span class="sxs-lookup"><span data-stu-id="e12a6-278">API changes</span></span>](#api-changes-in-220)

### <a name="api-changes-in-220"></a><span data-ttu-id="e12a6-279">2.2.0 中的 API 變更</span><span class="sxs-lookup"><span data-stu-id="e12a6-279">API changes in 2.2.0</span></span>

<span data-ttu-id="e12a6-280">**IMixedRealityBoundarySystem。 Contains**</span><span class="sxs-lookup"><span data-stu-id="e12a6-280">**IMixedRealityBoundarySystem.Contains**</span></span>

<span data-ttu-id="e12a6-281">這個方法先前採用特定的 Unity 定義實驗列舉。</span><span class="sxs-lookup"><span data-stu-id="e12a6-281">This method previously took in a specific, Unity-defined experimental enum.</span></span> <span data-ttu-id="e12a6-282">它現在會採用與 Unity 列舉完全相同的 MRTK 定義列舉。</span><span class="sxs-lookup"><span data-stu-id="e12a6-282">It now takes in an MRTK-defined enum that's identical to the Unity enum.</span></span> <span data-ttu-id="e12a6-283">這種變更有助於為 Unity 未來的界限 Api 做好 MRTK 準備。</span><span class="sxs-lookup"><span data-stu-id="e12a6-283">This change helps prepare the MRTK for Unity's future boundary APIs.</span></span>

<span data-ttu-id="e12a6-284">**MixedRealityServiceProfileAttribute**</span><span class="sxs-lookup"><span data-stu-id="e12a6-284">**MixedRealityServiceProfileAttribute**</span></span>

<span data-ttu-id="e12a6-285">為了更清楚地描述支援設定檔的需求，已更新 MixedRealityServiceProfileAttribute 以新增選擇性的排除類型集合。</span><span class="sxs-lookup"><span data-stu-id="e12a6-285">To better describe the requirements for supporting a profile, the MixedRealityServiceProfileAttribute has been updated to add an optional collection of excluded types.</span></span> <span data-ttu-id="e12a6-286">作為這項變更的一部分，ServiceType 屬性已從類型變更為類型 []，並已重新命名為 RequiredTypes。</span><span class="sxs-lookup"><span data-stu-id="e12a6-286">As part of this change, the ServiceType property has been changed from Type to Type[] and been renamed to RequiredTypes.</span></span>

<span data-ttu-id="e12a6-287">第二個屬性（ExcludedTypes）也已加入。</span><span class="sxs-lookup"><span data-stu-id="e12a6-287">A second property, ExcludedTypes has also been added.</span></span>

## <a name="updating-200-to-210"></a><span data-ttu-id="e12a6-288">將2.0.0 更新為2.1。0</span><span class="sxs-lookup"><span data-stu-id="e12a6-288">Updating 2.0.0 to 2.1.0</span></span>

- [<span data-ttu-id="e12a6-289">API 變更</span><span class="sxs-lookup"><span data-stu-id="e12a6-289">API changes</span></span>](#api-changes-in-210)
- [<span data-ttu-id="e12a6-290">設定檔變更</span><span class="sxs-lookup"><span data-stu-id="e12a6-290">Profile changes</span></span>](#profile-changes-in-210)

### <a name="api-changes-in-210"></a><span data-ttu-id="e12a6-291">2.1.0 中的 API 變更</span><span class="sxs-lookup"><span data-stu-id="e12a6-291">API changes in 2.1.0</span></span>

<span data-ttu-id="e12a6-292">**BaseNearInteractionTouchable**</span><span class="sxs-lookup"><span data-stu-id="e12a6-292">**BaseNearInteractionTouchable**</span></span>

<span data-ttu-id="e12a6-293">已 `BaseNearInteractionTouchable` 修改為將 `OnValidate` 方法標示為虛擬。</span><span class="sxs-lookup"><span data-stu-id="e12a6-293">The `BaseNearInteractionTouchable` has been modified to mark the `OnValidate` method as virtual.</span></span> <span data-ttu-id="e12a6-294">延伸 `BaseNearInteractionTouchable` (例如：) 的類別已 `NearInteractionTouchableUnityUI` 更新以反映此變更。</span><span class="sxs-lookup"><span data-stu-id="e12a6-294">Classes that extend `BaseNearInteractionTouchable` (ex: `NearInteractionTouchableUnityUI`) have been updated to reflect this change.</span></span>

<span data-ttu-id="e12a6-295">**ColliderNearInteractionTouchable**</span><span class="sxs-lookup"><span data-stu-id="e12a6-295">**ColliderNearInteractionTouchable**</span></span>

<span data-ttu-id="e12a6-296">`ColliderNearInteractionTouchable` 類別已被取代。</span><span class="sxs-lookup"><span data-stu-id="e12a6-296">The `ColliderNearInteractionTouchable` class has been deprecated.</span></span> <span data-ttu-id="e12a6-297">請更新要使用的程式碼參考 `BaseNearInteractionTouchable` 。</span><span class="sxs-lookup"><span data-stu-id="e12a6-297">Please update code references to use `BaseNearInteractionTouchable`.</span></span>

<span data-ttu-id="e12a6-298">**IMixedRealityMouseDeviceManager**</span><span class="sxs-lookup"><span data-stu-id="e12a6-298">**IMixedRealityMouseDeviceManager**</span></span>

<span data-ttu-id="e12a6-299">**_添加_**</span><span class="sxs-lookup"><span data-stu-id="e12a6-299">**_Added_**</span></span>

<span data-ttu-id="e12a6-300">`IMixedRealityMouseDeviceManager` 已新增 `CursorSpeed` 並具有 `WheelSpeed` 屬性。</span><span class="sxs-lookup"><span data-stu-id="e12a6-300">`IMixedRealityMouseDeviceManager` has been added `CursorSpeed` and `WheelSpeed` properties.</span></span> <span data-ttu-id="e12a6-301">這些屬性可讓應用程式指定乘數，也就是資料指標和滾輪的速度會分別調整。</span><span class="sxs-lookup"><span data-stu-id="e12a6-301">These properties allow applications to specify a multiplier value by which the speed of the cursor and wheel, respectively will be scaled.</span></span>

<span data-ttu-id="e12a6-302">這是中斷性變更，需要修改現有的滑鼠裝置管理員。</span><span class="sxs-lookup"><span data-stu-id="e12a6-302">This is a breaking change and requires existing mouse device manager implementations to be modified .</span></span>

>[!NOTE]
><span data-ttu-id="e12a6-303">這項變更與版本2.0.0 不相容。</span><span class="sxs-lookup"><span data-stu-id="e12a6-303">This change is not backwards compatible with version 2.0.0.</span></span>

<span data-ttu-id="e12a6-304">**_廢棄_**</span><span class="sxs-lookup"><span data-stu-id="e12a6-304">**_Deprecated_**</span></span>

<span data-ttu-id="e12a6-305">`MouseInputProfile`屬性已標示為已淘汰，將會從 Microsoft 混合現實工具組的未來版本中移除。</span><span class="sxs-lookup"><span data-stu-id="e12a6-305">The `MouseInputProfile` property has been marked as obsolete and will be removed from a future version of the Microsoft Mixed Reality Toolkit.</span></span> <span data-ttu-id="e12a6-306">建議應用程式程式碼不再使用此屬性。</span><span class="sxs-lookup"><span data-stu-id="e12a6-306">It is recommended that application code no longer use this property.</span></span>

<span data-ttu-id="e12a6-307">**互動**</span><span class="sxs-lookup"><span data-stu-id="e12a6-307">**Interactable**</span></span>

<span data-ttu-id="e12a6-308">以下是已淘汰的方法和屬性，將會從未來版本的 Microsoft Mixed Reality 工具組中移除。</span><span class="sxs-lookup"><span data-stu-id="e12a6-308">The following methods and properties have been deprecated and will be removed from a future version of the Microsoft Mixed Reality Toolkit.</span></span> <span data-ttu-id="e12a6-309">建議您根據 [過時] 屬性中包含的指導方針來更新應用程式程式碼，並在主控台中顯示。</span><span class="sxs-lookup"><span data-stu-id="e12a6-309">The recommendation is to update application code per the guidance contained in the Obsolete attribute and displayed in the console.</span></span>

- `public bool Enabled`
- `public bool FocusEnabled`
- `public void ForceUpdateThemes()`
- `public bool IsDisabled`
- `public bool IsToggleButton`
- `public int GetDimensionIndex()`
- `public State[] GetStates()`
- `public bool RequiresFocus`
- `public void ResetBaseStates()`
- `public virtual void SetCollision(bool collision)`
- `public virtual void SetCustom(bool custom)`
- `public void SetDimensionIndex(int index)`
- `public virtual void SetDisabled(bool disabled)`
- `public virtual void SetFocus(bool focus)`
- `public virtual void SetGesture(bool gesture)`
- `public virtual void SetGestureMax(bool gesture)`
- `public virtual void SetGrab(bool grab)`
- `public virtual void SetInteractive(bool interactive)`
- `public virtual void SetObservation(bool observation)`
- `public virtual void SetObservationTargeted(bool targeted)`
- `public virtual void SetPhysicalTouch(bool touch)`
- `public virtual void SetPress(bool press)`
- `public virtual void SetTargeted(bool targeted)`
- `public virtual void SetToggled(bool toggled)`
- `public virtual void SetVisited(bool visited)`
- `public virtual void SetVoiceCommand(bool voice)`

<span data-ttu-id="e12a6-310">**NearInteractionTouchableSurface**</span><span class="sxs-lookup"><span data-stu-id="e12a6-310">**NearInteractionTouchableSurface**</span></span>

<span data-ttu-id="e12a6-311">`NearInteractionTouchableSurface`類別已加入，現在可作為和的基類 `NearInteractionTouchable` `NearInteractionTouchableUnityUI` 。</span><span class="sxs-lookup"><span data-stu-id="e12a6-311">The `NearInteractionTouchableSurface` class has been added and now serves as the base class for `NearInteractionTouchable` and `NearInteractionTouchableUnityUI`.</span></span>

### <a name="profile-changes-in-210"></a><span data-ttu-id="e12a6-312">2.1.0 中的設定檔變更</span><span class="sxs-lookup"><span data-stu-id="e12a6-312">Profile changes in 2.1.0</span></span>

<span data-ttu-id="e12a6-313">**手動追蹤設定檔**</span><span class="sxs-lookup"><span data-stu-id="e12a6-313">**Hand tracking profile**</span></span>

<span data-ttu-id="e12a6-314">手網格和聯合視覺效果現在有個別的編輯器和播放機設定。</span><span class="sxs-lookup"><span data-stu-id="e12a6-314">The hand mesh and joint visualizations now have a separate editor and player settings.</span></span> <span data-ttu-id="e12a6-315">已更新手形追蹤設定檔，以允許將這些視覺效果設定為;Nothing、所有專案、編輯器或播放機。</span><span class="sxs-lookup"><span data-stu-id="e12a6-315">The hand tracking profile has been updated to allow for setting these visualizations to; Nothing, Everything, Editor or Player.</span></span>

![手形視覺效果模式](../release-notes/images/HandTrackingVisualizationModes.png)

<span data-ttu-id="e12a6-317">自訂的手追蹤設定檔可能需要更新，才能與版本2.1.0 正常搭配運作。</span><span class="sxs-lookup"><span data-stu-id="e12a6-317">Custom hand tracking profiles may need to be updated to work correctly with version 2.1.0.</span></span>

>[!NOTE]
><span data-ttu-id="e12a6-318">這項變更與版本2.0.0 不相容。</span><span class="sxs-lookup"><span data-stu-id="e12a6-318">This change is not backwards compatible with version 2.0.0.</span></span>

<span data-ttu-id="e12a6-319">**輸入模擬設定檔**</span><span class="sxs-lookup"><span data-stu-id="e12a6-319">**Input simulation profile**</span></span>

<span data-ttu-id="e12a6-320">輸入模擬系統已升級，這會變更輸入模擬設定檔中的幾項設定。</span><span class="sxs-lookup"><span data-stu-id="e12a6-320">The input simulation system has been upgraded, which changes a few settings in the input simulation profile.</span></span> <span data-ttu-id="e12a6-321">某些變更無法自動遷移，而使用者可能會發現設定檔使用預設值。</span><span class="sxs-lookup"><span data-stu-id="e12a6-321">Some changes can not be migrated automatically and users may find that profiles are using default values.</span></span>

1. <span data-ttu-id="e12a6-322">設定檔中的所有 KeyCode 和滑鼠按鍵系結都已取代為泛型 `KeyBinding` 結構，此結構會儲存系結類型 (按鍵或滑鼠) 以及實際的系結程式碼， (KeyCode 或滑鼠按鍵編號分別) 。</span><span class="sxs-lookup"><span data-stu-id="e12a6-322">All KeyCode and mouse button bindings in the profile have been replaced with a generic `KeyBinding` struct, which stores the type of binding (key or mouse) as well as the actual binding code (KeyCode or mouse button number respectively).</span></span> <span data-ttu-id="e12a6-323">此結構有自己的偵測器，可允許統一顯示並提供「自動系結」工具，只要按下個別的按鍵即可快速設定按鍵系結，而不需要從大型的下拉式清單中選取。</span><span class="sxs-lookup"><span data-stu-id="e12a6-323">The struct has its own inspector, which allows unified display and offers an "auto-bind" tool to quickly set key bindings by pressing the respective key instead of selecting from a huge dropdown list.</span></span>

    - <span data-ttu-id="e12a6-324">FastControlKey</span><span class="sxs-lookup"><span data-stu-id="e12a6-324">FastControlKey</span></span>
    - <span data-ttu-id="e12a6-325">ToggleLeftHandKey</span><span class="sxs-lookup"><span data-stu-id="e12a6-325">ToggleLeftHandKey</span></span>
    - <span data-ttu-id="e12a6-326">ToggleRightHandKey</span><span class="sxs-lookup"><span data-stu-id="e12a6-326">ToggleRightHandKey</span></span>
    - <span data-ttu-id="e12a6-327">LeftHandManipulationKey</span><span class="sxs-lookup"><span data-stu-id="e12a6-327">LeftHandManipulationKey</span></span>
    - <span data-ttu-id="e12a6-328">RightHandManipulationKey</span><span class="sxs-lookup"><span data-stu-id="e12a6-328">RightHandManipulationKey</span></span>

1. <span data-ttu-id="e12a6-329">`MouseLookToggle` 先前已包含在 `MouseLookButton` 列舉中 `InputSimulationMouseButton.Focused` ，它現在是個別的選項。</span><span class="sxs-lookup"><span data-stu-id="e12a6-329">`MouseLookToggle` was previously included in the `MouseLookButton` enum as `InputSimulationMouseButton.Focused`, it is now a separate option.</span></span> <span data-ttu-id="e12a6-330">啟用時，在放開按鈕之後，相機會繼續以滑鼠旋轉，直到按下 esc 鍵為止。</span><span class="sxs-lookup"><span data-stu-id="e12a6-330">When enabled, the camera will keep rotating with the mouse after releasing the button, until the escape key is pressed.</span></span>
1. <span data-ttu-id="e12a6-331">`HandDepthMultiplier` 預設值已從0.1 降至0.03，以配合輸入模擬的某些變更。</span><span class="sxs-lookup"><span data-stu-id="e12a6-331">`HandDepthMultiplier` default value has been lowered from 0.1 to 0.03 to accommodate some changes to the input simulation.</span></span> <span data-ttu-id="e12a6-332">如果相機在滾動時移動速度太快，請嘗試降低此值。</span><span class="sxs-lookup"><span data-stu-id="e12a6-332">If the camera moves too fast when scrolling, try lowering this value.</span></span>
1. <span data-ttu-id="e12a6-333">旋轉手的按鍵已經被移除，手旋轉現在也是由滑鼠所控制。</span><span class="sxs-lookup"><span data-stu-id="e12a6-333">Keys for rotating hands have been removed, hand rotation is now controlled by the mouse as well.</span></span> <span data-ttu-id="e12a6-334">按住 `HandRotateButton` (Ctrl) ，以及左/右操作金鑰 (LShift/空格鍵) 將會啟用手旋轉。</span><span class="sxs-lookup"><span data-stu-id="e12a6-334">Holding `HandRotateButton` (Ctrl) together with the left/right hand manipulation key (LShift/Space) will enable hand rotation.</span></span>
1. <span data-ttu-id="e12a6-335">已將新的軸 "上下按鈕" 引進至輸入軸清單。</span><span class="sxs-lookup"><span data-stu-id="e12a6-335">A new axis "UpDown" has been introduced to the input axis list.</span></span> <span data-ttu-id="e12a6-336">這會控制垂直和預設為 Q/E 按鍵以及控制器觸發程式按鈕的相機移動。</span><span class="sxs-lookup"><span data-stu-id="e12a6-336">This controls camera movement in the vertical and defaults to Q/E keys as well as the controller trigger buttons.</span></span>

<span data-ttu-id="e12a6-337">如需這些變更的詳細資訊，請參閱「 [輸入模擬服務](../features/input-simulation/input-simulation-service.md) 」一文。</span><span class="sxs-lookup"><span data-stu-id="e12a6-337">For more information on these changes, please see the [input simulation service](../features/input-simulation/input-simulation-service.md) article.</span></span>

<span data-ttu-id="e12a6-338">**滑鼠資料提供者設定檔**</span><span class="sxs-lookup"><span data-stu-id="e12a6-338">**Mouse data provider profile**</span></span>

<span data-ttu-id="e12a6-339">滑鼠資料提供者設定檔已經更新，以公開新的 `CursorSpeed` 和 `WheelSpeed` 屬性。</span><span class="sxs-lookup"><span data-stu-id="e12a6-339">The mouse data provider profile has been updated to expose the new `CursorSpeed` and `WheelSpeed` properties.</span></span> <span data-ttu-id="e12a6-340">現有的自訂設定檔會自動提供預設值。</span><span class="sxs-lookup"><span data-stu-id="e12a6-340">Existing custom profiles will automatically have default values provided.</span></span> <span data-ttu-id="e12a6-341">儲存設定檔時，將會保存這些新值。</span><span class="sxs-lookup"><span data-stu-id="e12a6-341">When the profile is saved, these new values will be persisted.</span></span>

<span data-ttu-id="e12a6-342">**控制器對應設定檔**</span><span class="sxs-lookup"><span data-stu-id="e12a6-342">**Controller mapping profile**</span></span>

<span data-ttu-id="e12a6-343">某些軸和輸入類型已在2.1.0 中更新，尤其是在 OpenVR 平臺上。</span><span class="sxs-lookup"><span data-stu-id="e12a6-343">Some axes and input types have been updated in 2.1.0, especially around the OpenVR platform.</span></span> <span data-ttu-id="e12a6-344">升級時，請務必選取 [ **MixedRealityToolkit-> 公用程式-> 更新 > 控制器對應設定檔** ]。</span><span class="sxs-lookup"><span data-stu-id="e12a6-344">Please be sure to select **MixedRealityToolkit -> Utilities -> Update -> Controller Mapping Profiles** when upgrading.</span></span> <span data-ttu-id="e12a6-345">這會將任何自訂控制器對應設定檔更新為更新的座標軸和資料，同時讓您的自訂指派輸入動作保持不變。</span><span class="sxs-lookup"><span data-stu-id="e12a6-345">This will update any custom Controller Mapping Profiles with the updated axes and data, while leaving your custom-assigned input actions intact.</span></span>

## <a name="updating-rc2-to-200"></a><span data-ttu-id="e12a6-346">正在將 RC2 更新至2.0。0</span><span class="sxs-lookup"><span data-stu-id="e12a6-346">Updating RC2 to 2.0.0</span></span>

<span data-ttu-id="e12a6-347">在 Microsoft Mixed Reality 工具組的 RC2 與2.0.0 版本之間，變更可能會影響現有的專案。</span><span class="sxs-lookup"><span data-stu-id="e12a6-347">Between the RC2 and 2.0.0 releases of the Microsoft Mixed Reality Toolkit, changes were made that may impact existing projects.</span></span> <span data-ttu-id="e12a6-348">本檔將說明這些變更，以及如何將專案更新至2.0.0 版本。</span><span class="sxs-lookup"><span data-stu-id="e12a6-348">This document describes those changes and how to update projects to the 2.0.0 release.</span></span>

- [<span data-ttu-id="e12a6-349">API 變更</span><span class="sxs-lookup"><span data-stu-id="e12a6-349">API changes</span></span>](#api-changes-in-200)
- [<span data-ttu-id="e12a6-350">元件名稱變更</span><span class="sxs-lookup"><span data-stu-id="e12a6-350">Assembly name changes</span></span>](#assembly-name-changes-in-200)

### <a name="api-changes-in-200"></a><span data-ttu-id="e12a6-351">2.0.0 中的 API 變更</span><span class="sxs-lookup"><span data-stu-id="e12a6-351">API changes in 2.0.0</span></span>

<span data-ttu-id="e12a6-352">自 RC2 發行以來，有許多 API 變更，包括可能會中斷現有專案的部分。</span><span class="sxs-lookup"><span data-stu-id="e12a6-352">Since the release of RC2, there have been a number of API changes including some that may break existing projects.</span></span> <span data-ttu-id="e12a6-353">下列章節說明 RC2 與2.0.0 版本之間的變更。</span><span class="sxs-lookup"><span data-stu-id="e12a6-353">The following sections describe the changes that have occurred between the RC2 and 2.0.0 releases.</span></span>

<span data-ttu-id="e12a6-354">**MixedRealityToolkit**</span><span class="sxs-lookup"><span data-stu-id="e12a6-354">**MixedRealityToolkit**</span></span>

<span data-ttu-id="e12a6-355">MixedRealityToolkit 物件上的下列公用屬性已被取代。</span><span class="sxs-lookup"><span data-stu-id="e12a6-355">The following public properties on the MixedRealityToolkit object have been deprecated.</span></span>

- <span data-ttu-id="e12a6-356">`RegisteredMixedRealityServices` 不再包含已註冊延伸模組服務和資料提供者的集合。</span><span class="sxs-lookup"><span data-stu-id="e12a6-356">`RegisteredMixedRealityServices` no longer contains the collection of registered extensions services and data providers.</span></span>

<span data-ttu-id="e12a6-357">若要存取擴充服務，請使用 `MixedRealityServiceRegistry.TryGetService<T>` 。</span><span class="sxs-lookup"><span data-stu-id="e12a6-357">To access extension services, use `MixedRealityServiceRegistry.TryGetService<T>`.</span></span> <span data-ttu-id="e12a6-358">若要存取資料提供者，請將服務實例轉換為 [`IMixedRealityDataProviderAccess`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProviderAccess) 和使用 `GetDataProvider<T>` 。</span><span class="sxs-lookup"><span data-stu-id="e12a6-358">To access data providers, cast the service instance to [`IMixedRealityDataProviderAccess`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProviderAccess) and use `GetDataProvider<T>`.</span></span>

<span data-ttu-id="e12a6-359">使用 [`MixedRealityServiceRegistry`](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry) 或 [`CoreServices`](xref:Microsoft.MixedReality.Toolkit.CoreServices) 取代下列已被取代的屬性</span><span class="sxs-lookup"><span data-stu-id="e12a6-359">Use [`MixedRealityServiceRegistry`](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry) or [`CoreServices`](xref:Microsoft.MixedReality.Toolkit.CoreServices) instead for the following deprecated properties</span></span>

- `ActiveSystems`
- `InputSystem`
- `BoundarySystem`
- `CameraSystem`
- `SpatialAwarenessSystem`
- `TeleportSystem`
- `DiagnosticsSystem`
- `SceneSystem`

<span data-ttu-id="e12a6-360">**CoreServices**</span><span class="sxs-lookup"><span data-stu-id="e12a6-360">**CoreServices**</span></span>

<span data-ttu-id="e12a6-361">[`CoreServices`](xref:Microsoft.MixedReality.Toolkit.CoreServices)類別是靜態系統存取子的取代 (例如在物件中找到的 BoundarySystem) `MixedRealityToolkit` 。</span><span class="sxs-lookup"><span data-stu-id="e12a6-361">The [`CoreServices`](xref:Microsoft.MixedReality.Toolkit.CoreServices) class is the replacement for the static system accessors (ex: BoundarySystem) found in the `MixedRealityToolkit` object.</span></span>

>[!IMPORTANT]
><span data-ttu-id="e12a6-362">`MixedRealityToolkit`系統存取子在版本2.0.0 中已被取代，而且將在 MRTK 的未來版本中移除。</span><span class="sxs-lookup"><span data-stu-id="e12a6-362">The `MixedRealityToolkit` system accessors have been deprecated in version 2.0.0 and will be removed in a future release of the MRTK.</span></span>

<span data-ttu-id="e12a6-363">下列程式碼範例說明舊的和新的模式。</span><span class="sxs-lookup"><span data-stu-id="e12a6-363">The following code example illustrates the old and the new pattern.</span></span>

``` c#
// Old
GameObject playAreaVisualization = MixedRealityToolkit.BoundarySystem?.GetPlayAreaVisualization();

// New
GameObject playAreaVisualization = CoreServices.BoundarySystem?.GetPlayAreaVisualization();
```

<span data-ttu-id="e12a6-364">使用新的 CoreSystem 類別可確保您的應用程式程式碼在您將應用程式變更為使用不同的服務註冊機構時，不需要更新 (例如：其中一個實驗性服務管理員) 。</span><span class="sxs-lookup"><span data-stu-id="e12a6-364">Using the new CoreSystem class will ensure that your application code will not need updating if you change the application to use a different service registrar (ex: one of the experimental service managers).</span></span>

<span data-ttu-id="e12a6-365">**IMixedRealityRaycastProvider**</span><span class="sxs-lookup"><span data-stu-id="e12a6-365">**IMixedRealityRaycastProvider**</span></span>

<span data-ttu-id="e12a6-366">新增 IMixedRealityRaycastProvider 之後，就會變更輸入系統設定檔。</span><span class="sxs-lookup"><span data-stu-id="e12a6-366">With the addition of the IMixedRealityRaycastProvider, the input system configuration profile was changed.</span></span> <span data-ttu-id="e12a6-367">如果您有自訂設定檔，當您執行應用程式時，可能會收到下列影像中的錯誤。</span><span class="sxs-lookup"><span data-stu-id="e12a6-367">If you have a custom profile, you may receive the errors in the following image when you run your application.</span></span>

![選取 Raycast 提供者1](../release-notes/images/UnableToRegisterRaycastProvider.png)

<span data-ttu-id="e12a6-369">若要修正這些問題，請將 IMixedRealityRaycastProvider 實例新增至輸入系統設定檔。</span><span class="sxs-lookup"><span data-stu-id="e12a6-369">To fix these, please add an IMixedRealityRaycastProvider instance to your input system profile.</span></span>

![選取 Raycast 提供者2](../release-notes/images/SelectRaycastProvider.png)

<span data-ttu-id="e12a6-371">**事件系統**</span><span class="sxs-lookup"><span data-stu-id="e12a6-371">**Event System**</span></span>

- <span data-ttu-id="e12a6-372">`IMixedRealityEventSystem`舊的 API 方法 `Register` 和 `Unregister` 都已標示為過時。</span><span class="sxs-lookup"><span data-stu-id="e12a6-372">The `IMixedRealityEventSystem` old API methods `Register` and `Unregister` have been marked as obsolete.</span></span> <span data-ttu-id="e12a6-373">它們是為了回溯相容性而保留。</span><span class="sxs-lookup"><span data-stu-id="e12a6-373">They are preserved for backwards compatibility.</span></span>
- <span data-ttu-id="e12a6-374">`InputSystemGlobalListener` 已標示為過時。</span><span class="sxs-lookup"><span data-stu-id="e12a6-374">`InputSystemGlobalListener` has been marked as obsolete.</span></span> <span data-ttu-id="e12a6-375">其功能尚未變更。</span><span class="sxs-lookup"><span data-stu-id="e12a6-375">Its functionality has not changed.</span></span>
- <span data-ttu-id="e12a6-376">`BaseInputHandler` 基類已從變更 `InputSystemGlobalListener` 為 `InputSystemGlobalHandlerListener` 。</span><span class="sxs-lookup"><span data-stu-id="e12a6-376">`BaseInputHandler` base class has been changed from `InputSystemGlobalListener` to `InputSystemGlobalHandlerListener`.</span></span> <span data-ttu-id="e12a6-377">這是的任何子代的重大變更 `BaseInputHandler` 。</span><span class="sxs-lookup"><span data-stu-id="e12a6-377">This is a breaking change for any descendants of `BaseInputHandler`.</span></span>

<span data-ttu-id="e12a6-378">**_變更背後的動機_**</span><span class="sxs-lookup"><span data-stu-id="e12a6-378">**_Motivation behind the change_**</span></span>

<span data-ttu-id="e12a6-379">舊的事件系統 API `Register` 可能 `Unregister` 會在執行時間中造成多個問題，主要是：</span><span class="sxs-lookup"><span data-stu-id="e12a6-379">The old event system API `Register` and `Unregister` could potentially cause multiple issues in runtime, main being:</span></span>

- <span data-ttu-id="e12a6-380">如果元件註冊全域事件，則會接收 *所有* 類型的全域輸入事件。</span><span class="sxs-lookup"><span data-stu-id="e12a6-380">If a component registers for global events, it would receive global input events of *all* types.</span></span>
- <span data-ttu-id="e12a6-381">如果物件上的其中一個元件註冊全域輸入事件，此物件上的所有元件都會接收 *所有* 類型的全域輸入事件。</span><span class="sxs-lookup"><span data-stu-id="e12a6-381">If one of the components on an object registers for global input events, all components on this object will receive global input events of *all* types.</span></span>
- <span data-ttu-id="e12a6-382">如果同一個物件上的兩個元件註冊到全域事件，然後在執行時間中停用其中一個，則第二個元件會停止接收全域事件。</span><span class="sxs-lookup"><span data-stu-id="e12a6-382">If two components on the same object register to global events, and then one is disabled in runtime, the second one stops receiving global events.</span></span>

<span data-ttu-id="e12a6-383">新 `RegisterHandler` 的 API 和 `UnregisterHandler` ：</span><span class="sxs-lookup"><span data-stu-id="e12a6-383">New API `RegisterHandler` and `UnregisterHandler`:</span></span>

- <span data-ttu-id="e12a6-384">提供明確且細微的控制，以明確且細微地控制要對哪些輸入事件進行全域接聽，且應以焦點為基礎。</span><span class="sxs-lookup"><span data-stu-id="e12a6-384">Provides an explicit and granular control over which input events should be listened to globally and which should be focused-based.</span></span>
- <span data-ttu-id="e12a6-385">允許相同物件上的多個元件彼此獨立接聽全域事件。</span><span class="sxs-lookup"><span data-stu-id="e12a6-385">Allows multiple components on the same object to listen to global events independently on each other.</span></span>

<span data-ttu-id="e12a6-386">**_如何遷移_**</span><span class="sxs-lookup"><span data-stu-id="e12a6-386">**_How to migrate_**</span></span>

- <span data-ttu-id="e12a6-387">如果您之前曾經呼叫過 `Register` / `Unregister` API，請將這些呼叫取代為的呼叫 `RegisterHandler` / `UnregisterHandler` 。</span><span class="sxs-lookup"><span data-stu-id="e12a6-387">If you have been calling `Register`/`Unregister` API directly before, replace these calls with calls to `RegisterHandler`/`UnregisterHandler`.</span></span> <span data-ttu-id="e12a6-388">使用您實作為泛型參數的處理常式介面。</span><span class="sxs-lookup"><span data-stu-id="e12a6-388">Use handler interfaces you implement as generic parameters.</span></span> <span data-ttu-id="e12a6-389">如果您執行多個介面，且其中有數個接聽全域輸入事件，請呼叫 `RegisterHandler` 多次。</span><span class="sxs-lookup"><span data-stu-id="e12a6-389">If you implement multiple interfaces, and several of them listen to global input events, call `RegisterHandler` multiple times.</span></span>
- <span data-ttu-id="e12a6-390">如果您繼承自 `InputSystemGlobalListener` ，請將繼承變更為 `InputSystemGlobalHandlerListener` 。</span><span class="sxs-lookup"><span data-stu-id="e12a6-390">If you have been inheriting from `InputSystemGlobalListener`, change inheritance to `InputSystemGlobalHandlerListener`.</span></span> <span data-ttu-id="e12a6-391">執行 `RegisterHandlers` 和 `UnregisterHandlers` 抽象方法。</span><span class="sxs-lookup"><span data-stu-id="e12a6-391">Implement `RegisterHandlers` and `UnregisterHandlers` abstract methods.</span></span> <span data-ttu-id="e12a6-392">在「執行」呼叫中 `inputSystem.RegisterHandler` (`inputSystem.UnregisterHandler`) 在您要接聽全域事件的所有處理常式介面上註冊。</span><span class="sxs-lookup"><span data-stu-id="e12a6-392">In the implementation call `inputSystem.RegisterHandler` (`inputSystem.UnregisterHandler`) to register on all handler interfaces you want to listen global events for.</span></span>
- <span data-ttu-id="e12a6-393">如果您繼承自、實 `BaseInputHandler` `RegisterHandlers` 和 `UnregisterHandlers` 抽象方法 (與 `InputSystemGlobalListener`) 相同。</span><span class="sxs-lookup"><span data-stu-id="e12a6-393">If you have been inheriting from `BaseInputHandler`, implement `RegisterHandlers` and `UnregisterHandlers` abstract methods (same as for `InputSystemGlobalListener`).</span></span>

<span data-ttu-id="e12a6-394">**_遷移範例_**</span><span class="sxs-lookup"><span data-stu-id="e12a6-394">**_Examples of migration_**</span></span>

```c#
// Old
class SampleHandler : MonoBehaviour, IMixedRealitySourceStateHandler, IMixedRealityHandJointHandler
{
    private void OnEnable()
    {
        InputSystem?.Register(gameObject);
    }

    private void OnDisable()
    {
        InputSystem?.Unregister(gameObject);
    }
}

// Migrated
class SampleHandler : MonoBehaviour, IMixedRealitySourceStateHandler, IMixedRealityHandJointHandler
{
    private void OnEnable()
    {
        InputSystem?.RegisterHandler<IMixedRealitySourceStateHandler>(this);
        InputSystem?.RegisterHandler<IMixedRealityHandJointHandler>(this);
    }

    private void OnDisable()
    {
        InputSystem?.UnregisterHandler<IMixedRealitySourceStateHandler>(this);
        InputSystem?.UnregisterHandler<IMixedRealityHandJointHandler>(this);
    }
}
```

```c#
// Old
class SampleHandler2 : InputSystemGlobalListener, IMixedRealitySpeechHandler
{
}

// Migrated
class SampleHandler2 : InputSystemGlobalHandlerListener, IMixedRealitySpeechHandler
{
    private void RegisterHandlers()
    {
        InputSystem?.RegisterHandler<IMixedRealitySpeechHandler>(this);
    }

    private void UnregisterHandlers()
    {
        InputSystem?.UnregisterHandler<IMixedRealitySpeechHandler>(this);
    }
}

// Alternative migration
class SampleHandler2 : MonoBehaviour, IMixedRealitySpeechHandler
{
    private void OnEnable()
    {
        IMixedRealityInputSystem inputSystem;
        if (MixedRealityServiceRegistry.TryGetService<IMixedRealityInputSystem>(out inputSystem))
        {
            inputSystem?.RegisterHandler<IMixedRealitySpeechHandler>(this);
        }
    }

    private void OnDisable()
    {
        IMixedRealityInputSystem inputSystem;
        if (MixedRealityServiceRegistry.TryGetService<IMixedRealityInputSystem>(out inputSystem))
        {
            inputSystem?.UnregisterHandler<IMixedRealitySpeechHandler>(this);
        }
    }
}
```

<span data-ttu-id="e12a6-395">**空間感知**</span><span class="sxs-lookup"><span data-stu-id="e12a6-395">**Spatial Awareness**</span></span>

<span data-ttu-id="e12a6-396">IMixedRealitySpatialAwarenessSystem 和 IMixedRealitySpatialAwarenessObserver 介面採用多個中斷變更，如下所述。</span><span class="sxs-lookup"><span data-stu-id="e12a6-396">The IMixedRealitySpatialAwarenessSystem and IMixedRealitySpatialAwarenessObserver interfaces have taken multiple breaking changes as described below.</span></span>

<span data-ttu-id="e12a6-397">**_變更_**</span><span class="sxs-lookup"><span data-stu-id="e12a6-397">**_Changes_**</span></span>

<span data-ttu-id="e12a6-398">下列方法 (s) 已重新命名，以更清楚地描述其使用方式。</span><span class="sxs-lookup"><span data-stu-id="e12a6-398">The following method(s) have been renamed to better describe their usage.</span></span>

- <span data-ttu-id="e12a6-399">`IMixedRealitySpatialAwarenessSystem.CreateSpatialObjectParent` 已重新命名為以 `IMixedRealitySpatialAwarenessSystem.CreateSpatialAwarenessObservationParent` 明確說明其使用方式。</span><span class="sxs-lookup"><span data-stu-id="e12a6-399">`IMixedRealitySpatialAwarenessSystem.CreateSpatialObjectParent` has been renamed to `IMixedRealitySpatialAwarenessSystem.CreateSpatialAwarenessObservationParent` to clarify its usage.</span></span>

<span data-ttu-id="e12a6-400">**_新增項目_**</span><span class="sxs-lookup"><span data-stu-id="e12a6-400">**_Additions_**</span></span>

<span data-ttu-id="e12a6-401">根據客戶的意見反應，我們已新增可輕鬆移除先前觀察到的空間感知資料的支援。</span><span class="sxs-lookup"><span data-stu-id="e12a6-401">Based on customer feedback, support for easy removal of previously observed spatial awareness data has been added.</span></span>

- `IMixedRealitySpatialAwarenessSystem.ClearObservations()`
- `IMixedRealitySpatialAwarenessSystem.ClearObservations<T>(string name)`
- `IMixedRealitySpatialAwarenessObserver.ClearObservations()`

<span data-ttu-id="e12a6-402">**解算器**</span><span class="sxs-lookup"><span data-stu-id="e12a6-402">**Solvers**</span></span>

<span data-ttu-id="e12a6-403">部分的規劃求解元件和 SolverHandler manager 類別已變更，以修正各種 bug，並以更直覺的方式使用。</span><span class="sxs-lookup"><span data-stu-id="e12a6-403">Some solver components and the SolverHandler manager class has changed to fix various bugs and for more intuitive usage.</span></span>

<span data-ttu-id="e12a6-404">**_SolverHandler_**</span><span class="sxs-lookup"><span data-stu-id="e12a6-404">**_SolverHandler_**</span></span>

- <span data-ttu-id="e12a6-405">類別不再延伸來源 `ControllerFinder`</span><span class="sxs-lookup"><span data-stu-id="e12a6-405">Class no longer extends from `ControllerFinder`</span></span>
- <span data-ttu-id="e12a6-406">`TrackedObjectToReference` 公用屬性已被取代，並已重新命名為 `TrackedTargetType`</span><span class="sxs-lookup"><span data-stu-id="e12a6-406">`TrackedObjectToReference` public property deprecated and has been renamed to `TrackedTargetType`</span></span>
- <span data-ttu-id="e12a6-407">`TrackedObjectType` 淘汰靠左 & 右控制器值。</span><span class="sxs-lookup"><span data-stu-id="e12a6-407">`TrackedObjectType` deprecates left & right controller values.</span></span> <span data-ttu-id="e12a6-408">改為使用 `MotionController` 或 `HandJoint` 值，並更新新 `TrackedHandedness` 屬性以將追蹤限制在左方或右控制器</span><span class="sxs-lookup"><span data-stu-id="e12a6-408">Instead use `MotionController` or `HandJoint` values and update new `TrackedHandedness` property to limit tracking to left or right controller</span></span>

<span data-ttu-id="e12a6-409">**_Receivebegindoc_**</span><span class="sxs-lookup"><span data-stu-id="e12a6-409">**_InBetween_**</span></span>

- <span data-ttu-id="e12a6-410">`TrackedObjectForSecondTransform` 公用屬性已被取代，並已重新命名為 `SecondTrackedObjectType`</span><span class="sxs-lookup"><span data-stu-id="e12a6-410">`TrackedObjectForSecondTransform` public property deprecated and has been renamed to `SecondTrackedObjectType`</span></span>
- <span data-ttu-id="e12a6-411">`AttachSecondTransformToNewTrackedObject()` 已移除。</span><span class="sxs-lookup"><span data-stu-id="e12a6-411">`AttachSecondTransformToNewTrackedObject()` has been removed.</span></span> <span data-ttu-id="e12a6-412">若要更新規劃求解，請修改公用屬性 (例如</span><span class="sxs-lookup"><span data-stu-id="e12a6-412">To update the solver, modify the public properties (i.e</span></span> <span data-ttu-id="e12a6-413">`SecondTrackedObjectType`)</span><span class="sxs-lookup"><span data-stu-id="e12a6-413">`SecondTrackedObjectType`)</span></span>

<span data-ttu-id="e12a6-414">**_SurfaceMagnetism_**</span><span class="sxs-lookup"><span data-stu-id="e12a6-414">**_SurfaceMagnetism_**</span></span>

- <span data-ttu-id="e12a6-415">`MaxDistance` 公用屬性已被取代，並已重新命名為 `MaxRaycastDistance`</span><span class="sxs-lookup"><span data-stu-id="e12a6-415">`MaxDistance` public property deprecated and has been renamed to `MaxRaycastDistance`</span></span>
- <span data-ttu-id="e12a6-416">`CloseDistance` 公用屬性已被取代，並已重新命名為 `ClosestDistance`</span><span class="sxs-lookup"><span data-stu-id="e12a6-416">`CloseDistance` public property deprecated and has been renamed to `ClosestDistance`</span></span>
- <span data-ttu-id="e12a6-417">的預設值 `RaycastDirectionMode` 現在會 `TrackedTargetForward` 以追蹤的目標轉換方向向前 raycasts</span><span class="sxs-lookup"><span data-stu-id="e12a6-417">Default value for `RaycastDirectionMode` is now `TrackedTargetForward` which raycasts in the direction of the tracked target transform forward</span></span>
- <span data-ttu-id="e12a6-418">`OrientationMode`列舉值 `Vertical` 和 `Full` 都已 `TrackedTarget` 分別重新命名為 `SurfaceNormal`</span><span class="sxs-lookup"><span data-stu-id="e12a6-418">`OrientationMode` enum values, `Vertical` and `Full`, have been renamed to `TrackedTarget` and `SurfaceNormal` respectively</span></span>
- <span data-ttu-id="e12a6-419">`KeepOrientationVertical` 已新增公用屬性，以控制相關聯 GameObject 的方向是否維持垂直</span><span class="sxs-lookup"><span data-stu-id="e12a6-419">`KeepOrientationVertical` public property has been added to control whether orientation of associated GameObject remains vertical</span></span>

<span data-ttu-id="e12a6-420">**按鈕**</span><span class="sxs-lookup"><span data-stu-id="e12a6-420">**Buttons**</span></span>

- <span data-ttu-id="e12a6-421">[`PressableButton`](xref:Microsoft.MixedReality.Toolkit.UI.PressableButton) 現在 `DistanceSpaceMode` 將屬性設為 `Local` 預設值。</span><span class="sxs-lookup"><span data-stu-id="e12a6-421">[`PressableButton`](xref:Microsoft.MixedReality.Toolkit.UI.PressableButton) now has `DistanceSpaceMode` property set to `Local` as default.</span></span> <span data-ttu-id="e12a6-422">這可讓按鈕進行調整，同時仍 pressable</span><span class="sxs-lookup"><span data-stu-id="e12a6-422">This allows buttons to be scaled while still be pressable</span></span>

<span data-ttu-id="e12a6-423">**剪出球體**</span><span class="sxs-lookup"><span data-stu-id="e12a6-423">**Clipping Sphere**</span></span>

<span data-ttu-id="e12a6-424">ClippingSphere 介面已變更，以反映在 ClippingBox 和 ClippingPlane 中找到的 Api。</span><span class="sxs-lookup"><span data-stu-id="e12a6-424">The ClippingSphere interface has changed to mirror the APIs found in the ClippingBox and ClippingPlane.</span></span>

<span data-ttu-id="e12a6-425">現在會根據轉換比例，以隱含的方式來計算 ClippingSphere 的 Radius 屬性。</span><span class="sxs-lookup"><span data-stu-id="e12a6-425">The ClippingSphere's Radius property is now implicitly calculated based on the transform scale.</span></span> <span data-ttu-id="e12a6-426">開發人員必須先在偵測器中指定 ClippingSphere 的半徑。</span><span class="sxs-lookup"><span data-stu-id="e12a6-426">Before developers would have to specify the radius of the ClippingSphere in the inspector.</span></span> <span data-ttu-id="e12a6-427">如果您想要變更半徑，只要以平常的方式更新轉換的轉換規模。</span><span class="sxs-lookup"><span data-stu-id="e12a6-427">If you want to change the radius, just update the transform scale of the transform as you normally would.</span></span>

<span data-ttu-id="e12a6-428">**NearInteractionTouchable 和 PokePointer**</span><span class="sxs-lookup"><span data-stu-id="e12a6-428">**NearInteractionTouchable and PokePointer**</span></span>

- <span data-ttu-id="e12a6-429">NearInteractionTouchable 不會處理 Unity UI 畫布的任何時間。</span><span class="sxs-lookup"><span data-stu-id="e12a6-429">NearInteractionTouchable does not handle Unity UI canvas touching any longer.</span></span> <span data-ttu-id="e12a6-430">NearInteractionTouchableUnityUI 類別必須立即用於 Unity UI touchables。</span><span class="sxs-lookup"><span data-stu-id="e12a6-430">The NearInteractionTouchableUnityUI class must be used for Unity UI touchables now.</span></span>
- <span data-ttu-id="e12a6-431">ColliderNearInteractionTouchable 是以 colliders 為基礎之 touchables 的新基類，也就是 NearInteractionTouchableUnityUI 以外的每個可觸式。</span><span class="sxs-lookup"><span data-stu-id="e12a6-431">ColliderNearInteractionTouchable is the new base class for touchables based on colliders, i.e. every touchable except NearInteractionTouchableUnityUI.</span></span>
- <span data-ttu-id="e12a6-432">BaseNearInteractionTouchable. DistFront 已移動並重新命名為 PokePointer。 TouchableDistance 這是 PokePointer 可以與 touchables 互動的距離。</span><span class="sxs-lookup"><span data-stu-id="e12a6-432">BaseNearInteractionTouchable.DistFront has been moved and renamed to PokePointer.TouchableDistance This is the distance and which the PokePointer can interact with touchables.</span></span> <span data-ttu-id="e12a6-433">先前每個可觸式都有自己的最大互動距離，但現在會在 PokePointer 中定義，以提供更佳的優化。</span><span class="sxs-lookup"><span data-stu-id="e12a6-433">Previously each touchable had its own maximum interaction distance, but now this is defined in the PokePointer which allows better optimization.</span></span>
- <span data-ttu-id="e12a6-434">BaseNearInteractionTouchable 已重新命名為 PokeThreshold，因此它會清楚指出 PokeThreshold 是 DebounceThreshold 的對應項。</span><span class="sxs-lookup"><span data-stu-id="e12a6-434">BaseNearInteractionTouchable.DistBack has been renamed to PokeThreshold This makes it clear that PokeThreshold is the counterpart to DebounceThreshold.</span></span> <span data-ttu-id="e12a6-435">當超過 PokeThreshold 時，即會啟動可觸式，並在超過 DebounceThreshold 時釋放。</span><span class="sxs-lookup"><span data-stu-id="e12a6-435">A touchable is activated when the PokeThreshold is crossed, and released when DebounceThreshold is crossed.</span></span>

<span data-ttu-id="e12a6-436">**ReadOnlyAttribute**</span><span class="sxs-lookup"><span data-stu-id="e12a6-436">**ReadOnlyAttribute**</span></span>

<span data-ttu-id="e12a6-437">已將 `Microsoft.MixedReality.Toolkit` 命名空間加入至 `ReadOnlyAttribute` 、 `BeginReadOnlyGroupAttribute` 和 `EndReadOnlyGroupAttribute` 。</span><span class="sxs-lookup"><span data-stu-id="e12a6-437">The `Microsoft.MixedReality.Toolkit` namespace has been added to `ReadOnlyAttribute`, `BeginReadOnlyGroupAttribute`, and `EndReadOnlyGroupAttribute`.</span></span>

<span data-ttu-id="e12a6-438">**PointerClickHandler**</span><span class="sxs-lookup"><span data-stu-id="e12a6-438">**PointerClickHandler**</span></span>

<span data-ttu-id="e12a6-439">`PointerClickHandler` 類別已被取代。</span><span class="sxs-lookup"><span data-stu-id="e12a6-439">The `PointerClickHandler` class has been deprecated.</span></span> <span data-ttu-id="e12a6-440">您 `PointerHandler` 應該改為使用，它會提供相同的功能。</span><span class="sxs-lookup"><span data-stu-id="e12a6-440">The `PointerHandler` should be used instead, it provides the same functionality.</span></span>

<span data-ttu-id="e12a6-441">**HoloLens clicker 支援**</span><span class="sxs-lookup"><span data-stu-id="e12a6-441">**HoloLens clicker support**</span></span>

<span data-ttu-id="e12a6-442">HoloLens clicker 的控制器對應已從狀況變更 [`WindowsMixedRealityController`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityController) 為狀況 [`WindowsMixedRealityGGVHand`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityGGVHand) 。</span><span class="sxs-lookup"><span data-stu-id="e12a6-442">The HoloLens clicker's controller mappings have changed from being an unhanded [`WindowsMixedRealityController`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityController) to being an unhanded [`WindowsMixedRealityGGVHand`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityGGVHand).</span></span> <span data-ttu-id="e12a6-443">為了因應此情況，當您第一次開啟 ControllerMapping 設定檔時，會執行自動更新程式。</span><span class="sxs-lookup"><span data-stu-id="e12a6-443">To account for this, an automatic updater will run the first time you open your ControllerMapping profile.</span></span> <span data-ttu-id="e12a6-444">請至少在升級至2.0.0 之後開啟任何自訂設定檔一次，以觸發這個一次性的遷移步驟。</span><span class="sxs-lookup"><span data-stu-id="e12a6-444">Please open any custom profiles at least once after upgrading to 2.0.0 in order to trigger this one-time migration step.</span></span>

<span data-ttu-id="e12a6-445">**InteractableHighlight**</span><span class="sxs-lookup"><span data-stu-id="e12a6-445">**InteractableHighlight**</span></span>

<span data-ttu-id="e12a6-446">`InteractableHighlight` 類別已被取代。</span><span class="sxs-lookup"><span data-stu-id="e12a6-446">The `InteractableHighlight` class has been deprecated.</span></span> <span data-ttu-id="e12a6-447">`InteractableOnFocus` `FocusInteractableStates` 應改為使用類別和資產。</span><span class="sxs-lookup"><span data-stu-id="e12a6-447">The `InteractableOnFocus` class and `FocusInteractableStates` asset should be used instead.</span></span> <span data-ttu-id="e12a6-448">若要為建立新的 `Theme` 資產 `InteractableOnFocus` ，請在 [專案] 視窗中按一下滑鼠右鍵，然後選取 [*建立*  >  *混合現實工具* 組  >  *互動*  >  *主題*]。</span><span class="sxs-lookup"><span data-stu-id="e12a6-448">To create a new `Theme` asset for the `InteractableOnFocus`, right click in the project window and select *Create* > *Mixed Reality Toolkit* > *Interactable* > *Theme*.</span></span>

<span data-ttu-id="e12a6-449">**HandInteractionPanZoom**</span><span class="sxs-lookup"><span data-stu-id="e12a6-449">**HandInteractionPanZoom**</span></span>

<span data-ttu-id="e12a6-450">`HandInteractionPanZoom` 已移至 UI 命名空間，因為它不是輸入元件。</span><span class="sxs-lookup"><span data-stu-id="e12a6-450">`HandInteractionPanZoom` has been moved to the UI namespace as it was not an input component.</span></span> <span data-ttu-id="e12a6-451">`HandPanEventData` 也已移至此命名空間，並簡化為與其他 UI 事件資料對應。</span><span class="sxs-lookup"><span data-stu-id="e12a6-451">`HandPanEventData` has also been moved into this namespace, and simplified to correspond with other UI event data.</span></span>

### <a name="assembly-name-changes-in-200"></a><span data-ttu-id="e12a6-452">2.0.0 中的元件名稱變更</span><span class="sxs-lookup"><span data-stu-id="e12a6-452">Assembly name changes in 2.0.0</span></span>

<span data-ttu-id="e12a6-453">在2.0.0 版本中，所有的官方混合現實工具組元件名稱及其相關聯的元件定義 (. asmdef) 檔案都已更新為符合下列模式。</span><span class="sxs-lookup"><span data-stu-id="e12a6-453">In The 2.0.0 release, all of the official Mixed Reality Toolkit assembly names and their associated assembly definition (.asmdef) files have been updated to fit the following pattern.</span></span>

```c#
Microsoft.MixedReality.Toolkit[.<name>]
```

<span data-ttu-id="e12a6-454">在某些情況下，已合併多個元件以建立更好的 unity 內容。</span><span class="sxs-lookup"><span data-stu-id="e12a6-454">In some instances, multiple assemblies have been merged to create better unity of their contents.</span></span> <span data-ttu-id="e12a6-455">如果您的專案使用自訂的 asmdef 檔案，則可能需要更新。</span><span class="sxs-lookup"><span data-stu-id="e12a6-455">If your project uses custom .asmdef files, they may require updating.</span></span>

<span data-ttu-id="e12a6-456">下表說明 RC2 asmdef 檔案名如何對應至2.0.0 版本。</span><span class="sxs-lookup"><span data-stu-id="e12a6-456">The following tables describe how the RC2 .asmdef file names map to the 2.0.0 release.</span></span> <span data-ttu-id="e12a6-457">所有元件名稱都符合 asmdef 檔案名。</span><span class="sxs-lookup"><span data-stu-id="e12a6-457">All assembly names match the .asmdef file name.</span></span>

<span data-ttu-id="e12a6-458">**MixedRealityToolkit**</span><span class="sxs-lookup"><span data-stu-id="e12a6-458">**MixedRealityToolkit**</span></span>

| <span data-ttu-id="e12a6-459">RC2</span><span class="sxs-lookup"><span data-stu-id="e12a6-459">RC2</span></span> | <span data-ttu-id="e12a6-460">2.0.0</span><span class="sxs-lookup"><span data-stu-id="e12a6-460">2.0.0</span></span> |
| --- | --- |
| <span data-ttu-id="e12a6-461">MixedRealityToolkit.asmdef</span><span class="sxs-lookup"><span data-stu-id="e12a6-461">MixedRealityToolkit.asmdef</span></span> | <span data-ttu-id="e12a6-462">MixedReality 工具組. asmdef</span><span class="sxs-lookup"><span data-stu-id="e12a6-462">Microsoft.MixedReality.Toolkit.asmdef</span></span> |
| <span data-ttu-id="e12a6-463">MixedRealityToolkit. BuildAndDeploy. asmdef</span><span class="sxs-lookup"><span data-stu-id="e12a6-463">MixedRealityToolkit.Core.BuildAndDeploy.asmdef</span></span> | <span data-ttu-id="e12a6-464">MixedReality. BuildAndDeploy. asmdef</span><span class="sxs-lookup"><span data-stu-id="e12a6-464">Microsoft.MixedReality.Toolkit.Editor.BuildAndDeploy.asmdef</span></span> |
| <span data-ttu-id="e12a6-465">MixedRealityToolkit，asmdef 的</span><span class="sxs-lookup"><span data-stu-id="e12a6-465">MixedRealityToolkit.Core.Definitions.Utilities.Editor.asmdef</span></span> | <span data-ttu-id="e12a6-466">已移除，請使用 MixedReality 工具組。 asmdef</span><span class="sxs-lookup"><span data-stu-id="e12a6-466">Removed, use Microsoft.MixedReality.Toolkit.Editor.Utilities.asmdef</span></span> |
| <span data-ttu-id="e12a6-467">MixedRealityToolkit. EditorClassExtensions. asmdef</span><span class="sxs-lookup"><span data-stu-id="e12a6-467">MixedRealityToolkit.Core.Extensions.EditorClassExtensions.asmdef</span></span> | <span data-ttu-id="e12a6-468">MixedReality. ClassExtensions. asmdef</span><span class="sxs-lookup"><span data-stu-id="e12a6-468">Microsoft.MixedReality.Toolkit.Editor.ClassExtensions.asmdef</span></span>
| <span data-ttu-id="e12a6-469">MixedRealityToolkit asmdef</span><span class="sxs-lookup"><span data-stu-id="e12a6-469">MixedRealityToolkit.Core.Inspectors.asmdef</span></span> | <span data-ttu-id="e12a6-470">MixedReality. asmdef。</span><span class="sxs-lookup"><span data-stu-id="e12a6-470">Microsoft.MixedReality.Toolkit.Editor.Inspectors.asmdef</span></span> |
| <span data-ttu-id="e12a6-471">MixedRealityToolkit ServiceInspectors. asmdef</span><span class="sxs-lookup"><span data-stu-id="e12a6-471">MixedRealityToolkit.Core.Inspectors.ServiceInspectors.asmdef</span></span> | <span data-ttu-id="e12a6-472">MixedReality. ServiceInspectors. asmdef</span><span class="sxs-lookup"><span data-stu-id="e12a6-472">Microsoft.MixedReality.Toolkit.Editor.ServiceInspectors.asmdef</span></span> |
| <span data-ttu-id="e12a6-473">MixedRealityToolkit. UtilitiesAsync. asmdef</span><span class="sxs-lookup"><span data-stu-id="e12a6-473">MixedRealityToolkit.Core.UtilitiesAsync.asmdef</span></span> | <span data-ttu-id="e12a6-474">MixedReality. asmdef。</span><span class="sxs-lookup"><span data-stu-id="e12a6-474">Microsoft.MixedReality.Toolkit.Async.asmdef</span></span> |
| <span data-ttu-id="e12a6-475">Asmdef 的 MixedRealityToolkit。</span><span class="sxs-lookup"><span data-stu-id="e12a6-475">MixedRealityToolkit.Core.Utilities.Editor.asmdef</span></span> | <span data-ttu-id="e12a6-476">MixedReality 工具組。 asmdef</span><span class="sxs-lookup"><span data-stu-id="e12a6-476">Microsoft.MixedReality.Toolkit.Editor.Utilities.asmdef</span></span> |
| <span data-ttu-id="e12a6-477">MixedRealityToolkit Gltf. asmdef</span><span class="sxs-lookup"><span data-stu-id="e12a6-477">MixedRealityToolkit.Utilities.Gltf.asmdef</span></span> | <span data-ttu-id="e12a6-478">MixedReality. Gltf. asmdef</span><span class="sxs-lookup"><span data-stu-id="e12a6-478">Microsoft.MixedReality.Toolkit.Gltf.asmdef</span></span> |
| <span data-ttu-id="e12a6-479">MixedRealityToolkit，Gltf asmdef</span><span class="sxs-lookup"><span data-stu-id="e12a6-479">MixedRealityToolkit.Utilities.Gltf.Importers.asmdef</span></span> | <span data-ttu-id="e12a6-480">MixedReality. Gltf. asmdef</span><span class="sxs-lookup"><span data-stu-id="e12a6-480">Microsoft.MixedReality.Toolkit.Gltf.Importers.asmdef</span></span> |

<span data-ttu-id="e12a6-481">**MixedRealityToolkit。提供者**</span><span class="sxs-lookup"><span data-stu-id="e12a6-481">**MixedRealityToolkit.Providers**</span></span>

| <span data-ttu-id="e12a6-482">RC2</span><span class="sxs-lookup"><span data-stu-id="e12a6-482">RC2</span></span> | <span data-ttu-id="e12a6-483">2.0.0</span><span class="sxs-lookup"><span data-stu-id="e12a6-483">2.0.0</span></span> |
| --- | --- |
| <span data-ttu-id="e12a6-484">MixedRealityToolkit. OpenVR. asmdef</span><span class="sxs-lookup"><span data-stu-id="e12a6-484">MixedRealityToolkit.Providers.OpenVR.asmdef</span></span> | <span data-ttu-id="e12a6-485">MixedReality. OpenVR. asmdef</span><span class="sxs-lookup"><span data-stu-id="e12a6-485">Microsoft.MixedReality.Toolkit.Providers.OpenVR.asmdef</span></span> |
| <span data-ttu-id="e12a6-486">MixedRealityToolkit. WindowsMixedReality. asmdef</span><span class="sxs-lookup"><span data-stu-id="e12a6-486">MixedRealityToolkit.Providers.WindowsMixedReality.asmdef</span></span> | <span data-ttu-id="e12a6-487">MixedReality. WindowsMixedReality. asmdef</span><span class="sxs-lookup"><span data-stu-id="e12a6-487">Microsoft.MixedReality.Toolkit.Providers.WindowsMixedReality.asmdef</span></span> |
| <span data-ttu-id="e12a6-488">MixedRealityToolkit. WindowsVoiceInput. asmdef</span><span class="sxs-lookup"><span data-stu-id="e12a6-488">MixedRealityToolkit.Providers.WindowsVoiceInput.asmdef</span></span> | <span data-ttu-id="e12a6-489">MixedReality. WindowsVoiceInput. asmdef</span><span class="sxs-lookup"><span data-stu-id="e12a6-489">Microsoft.MixedReality.Toolkit.Providers.WindowsVoiceInput.asmdef</span></span> |

<span data-ttu-id="e12a6-490">**MixedRealityToolkit 服務**</span><span class="sxs-lookup"><span data-stu-id="e12a6-490">**MixedRealityToolkit.Services**</span></span>

| <span data-ttu-id="e12a6-491">RC2</span><span class="sxs-lookup"><span data-stu-id="e12a6-491">RC2</span></span> | <span data-ttu-id="e12a6-492">2.0.0</span><span class="sxs-lookup"><span data-stu-id="e12a6-492">2.0.0</span></span> |
| --- | --- |
| <span data-ttu-id="e12a6-493">MixedRealityToolkit. BoundarySystem. asmdef</span><span class="sxs-lookup"><span data-stu-id="e12a6-493">MixedRealityToolkit.Services.BoundarySystem.asmdef</span></span> | <span data-ttu-id="e12a6-494">MixedReality. BoundarySystem. asmdef</span><span class="sxs-lookup"><span data-stu-id="e12a6-494">Microsoft.MixedReality.Toolkit.Services.BoundarySystem.asmdef</span></span> |
| <span data-ttu-id="e12a6-495">MixedRealityToolkit. CameraSystem. asmdef</span><span class="sxs-lookup"><span data-stu-id="e12a6-495">MixedRealityToolkit.Services.CameraSystem.asmdef</span></span> | <span data-ttu-id="e12a6-496">MixedReality. CameraSystem. asmdef</span><span class="sxs-lookup"><span data-stu-id="e12a6-496">Microsoft.MixedReality.Toolkit.Services.CameraSystem.asmdef</span></span> |
| <span data-ttu-id="e12a6-497">MixedRealityToolkit. DiagnosticsSystem. asmdef</span><span class="sxs-lookup"><span data-stu-id="e12a6-497">MixedRealityToolkit.Services.DiagnosticsSystem.asmdef</span></span> | <span data-ttu-id="e12a6-498">MixedReality. DiagnosticsSystem. asmdef</span><span class="sxs-lookup"><span data-stu-id="e12a6-498">Microsoft.MixedReality.Toolkit.Services.DiagnosticsSystem.asmdef</span></span> |
| <span data-ttu-id="e12a6-499">MixedRealityToolkit. InputSimulation. asmdef</span><span class="sxs-lookup"><span data-stu-id="e12a6-499">MixedRealityToolkit.Services.InputSimulation.asmdef</span></span> | <span data-ttu-id="e12a6-500">MixedReality. InputSimulation. asmdef</span><span class="sxs-lookup"><span data-stu-id="e12a6-500">Microsoft.MixedReality.Toolkit.Services.InputSimulation.asmdef</span></span> |
| <span data-ttu-id="e12a6-501">MixedRealityToolkit. InputSimulation. asmdef</span><span class="sxs-lookup"><span data-stu-id="e12a6-501">MixedRealityToolkit.Services.InputSimulation.Editor.asmdef</span></span> | <span data-ttu-id="e12a6-502">MixedReality. InputSimulation. asmdef。</span><span class="sxs-lookup"><span data-stu-id="e12a6-502">Microsoft.MixedReality.Toolkit.Services.InputSimulation.Editor.asmdef</span></span> |
| <span data-ttu-id="e12a6-503">MixedRealityToolkit. InputSystem. asmdef</span><span class="sxs-lookup"><span data-stu-id="e12a6-503">MixedRealityToolkit.Services.InputSystem.asmdef</span></span> | <span data-ttu-id="e12a6-504">MixedReality. InputSystem. asmdef</span><span class="sxs-lookup"><span data-stu-id="e12a6-504">Microsoft.MixedReality.Toolkit.Services.InputSystem.asmdef</span></span> |
| <span data-ttu-id="e12a6-505">MixedRealityToolkit asmdef</span><span class="sxs-lookup"><span data-stu-id="e12a6-505">MixedRealityToolkit.Services.Inspectors.asmdef</span></span> | <span data-ttu-id="e12a6-506">MixedReality. InputSystem. asmdef。</span><span class="sxs-lookup"><span data-stu-id="e12a6-506">Microsoft.MixedReality.Toolkit.Services.InputSystem.Editor.asmdef</span></span> |
| <span data-ttu-id="e12a6-507">MixedRealityToolkit. SceneSystem. asmdef</span><span class="sxs-lookup"><span data-stu-id="e12a6-507">MixedRealityToolkit.Services.SceneSystem.asmdef</span></span> | <span data-ttu-id="e12a6-508">MixedReality. SceneSystem. asmdef</span><span class="sxs-lookup"><span data-stu-id="e12a6-508">Microsoft.MixedReality.Toolkit.Services.SceneSystem.asmdef</span></span> |
| <span data-ttu-id="e12a6-509">MixedRealityToolkit. SpatialAwarenessSystem. asmdef</span><span class="sxs-lookup"><span data-stu-id="e12a6-509">MixedRealityToolkit.Services.SpatialAwarenessSystem.asmdef</span></span> | <span data-ttu-id="e12a6-510">MixedReality. SpatialAwarenessSystem. asmdef</span><span class="sxs-lookup"><span data-stu-id="e12a6-510">Microsoft.MixedReality.Toolkit.Services.SpatialAwarenessSystem.asmdef</span></span> |
| <span data-ttu-id="e12a6-511">MixedRealityToolkit. TeleportSystem. asmdef</span><span class="sxs-lookup"><span data-stu-id="e12a6-511">MixedRealityToolkit.Services.TeleportSystem.asmdef</span></span> | <span data-ttu-id="e12a6-512">MixedReality. TeleportSystem. asmdef</span><span class="sxs-lookup"><span data-stu-id="e12a6-512">Microsoft.MixedReality.Toolkit.Services.TeleportSystem.asmdef</span></span> |

<span data-ttu-id="e12a6-513">**MixedRealityToolkit SDK**</span><span class="sxs-lookup"><span data-stu-id="e12a6-513">**MixedRealityToolkit.SDK**</span></span>

| <span data-ttu-id="e12a6-514">RC2</span><span class="sxs-lookup"><span data-stu-id="e12a6-514">RC2</span></span> | <span data-ttu-id="e12a6-515">2.0.0</span><span class="sxs-lookup"><span data-stu-id="e12a6-515">2.0.0</span></span> |
| --- | --- |
| <span data-ttu-id="e12a6-516">MixedRealityToolkit. asmdef</span><span class="sxs-lookup"><span data-stu-id="e12a6-516">MixedRealityToolkit.SDK.asmdef</span></span> | <span data-ttu-id="e12a6-517">MixedReality 工具組. asmdef</span><span class="sxs-lookup"><span data-stu-id="e12a6-517">Microsoft.MixedReality.Toolkit.SDK.asmdef</span></span> |
| <span data-ttu-id="e12a6-518">MixedRealityToolkit asmdef</span><span class="sxs-lookup"><span data-stu-id="e12a6-518">MixedRealityToolkit.SDK.Inspectors.asmdef</span></span> | <span data-ttu-id="e12a6-519">MixedReality 工具組. asmdef</span><span class="sxs-lookup"><span data-stu-id="e12a6-519">Microsoft.MixedReality.Toolkit.SDK.Inspectors.asmdef</span></span> |

<span data-ttu-id="e12a6-520">**MixedRealityToolkit 範例**</span><span class="sxs-lookup"><span data-stu-id="e12a6-520">**MixedRealityToolkit.Examples**</span></span>

| <span data-ttu-id="e12a6-521">RC2</span><span class="sxs-lookup"><span data-stu-id="e12a6-521">RC2</span></span> | <span data-ttu-id="e12a6-522">2.0.0</span><span class="sxs-lookup"><span data-stu-id="e12a6-522">2.0.0</span></span> |
| --- | --- |
| <span data-ttu-id="e12a6-523">MixedRealityToolkit。例如 asmdef</span><span class="sxs-lookup"><span data-stu-id="e12a6-523">MixedRealityToolkit.Examples.asmdef</span></span> | <span data-ttu-id="e12a6-524">MixedReality，例如 asmdef</span><span class="sxs-lookup"><span data-stu-id="e12a6-524">Microsoft.MixedReality.Toolkit.Examples.asmdef</span></span> |
| <span data-ttu-id="e12a6-525">MixedRealityToolkit. Gltf. asmdef</span><span class="sxs-lookup"><span data-stu-id="e12a6-525">MixedRealityToolkit.Examples.Demos.Gltf.asmdef</span></span> | <span data-ttu-id="e12a6-526">MixedReality. Gltf. asmdef</span><span class="sxs-lookup"><span data-stu-id="e12a6-526">Microsoft.MixedReality.Toolkit.Demos.Gltf.asmdef</span></span> |
| <span data-ttu-id="e12a6-527">MixedRealityToolkit，例如 StandardShader asmdef</span><span class="sxs-lookup"><span data-stu-id="e12a6-527">MixedRealityToolkit.Examples.Demos.StandardShader.Inspectors.asmdef</span></span> | <span data-ttu-id="e12a6-528">MixedReality. StandardShader. asmdef。</span><span class="sxs-lookup"><span data-stu-id="e12a6-528">Microsoft.MixedReality.Toolkit.Demos.StandardShader.Inspectors.asmdef</span></span> |
| <span data-ttu-id="e12a6-529">MixedRealityToolkit，InspectorFields. asmdef</span><span class="sxs-lookup"><span data-stu-id="e12a6-529">MixedRealityToolkit.Examples.Demos.Utilities.InspectorFields.asmdef</span></span> | <span data-ttu-id="e12a6-530">MixedReality. InspectorFields. asmdef</span><span class="sxs-lookup"><span data-stu-id="e12a6-530">Microsoft.MixedReality.Toolkit.Demos.InspectorFields.asmdef</span></span> |
| <span data-ttu-id="e12a6-531">MixedRealityToolkit，例如 InspectorFields asmdef。</span><span class="sxs-lookup"><span data-stu-id="e12a6-531">MixedRealityToolkit.Examples.Demos.Utilities.InspectorFields.Inspectors.asmdef</span></span> | <span data-ttu-id="e12a6-532">MixedReality. InspectorFields. asmdef。</span><span class="sxs-lookup"><span data-stu-id="e12a6-532">Microsoft.MixedReality.Toolkit.Demos.InspectorFields.Inspectors.asmdef</span></span> |
| <span data-ttu-id="e12a6-533">MixedRealityToolkit，例如 Interactables. asmdef</span><span class="sxs-lookup"><span data-stu-id="e12a6-533">MixedRealityToolkit.Examples.Demos.UX.Interactables.asmdef</span></span> | <span data-ttu-id="e12a6-534">MixedReality. Interactables. asmdef。</span><span class="sxs-lookup"><span data-stu-id="e12a6-534">Microsoft.MixedReality.Toolkit.Demos.UX.Interactables.asmdef</span></span> |