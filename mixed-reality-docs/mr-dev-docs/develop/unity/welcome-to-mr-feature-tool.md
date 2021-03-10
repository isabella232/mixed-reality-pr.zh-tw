---
title: 歡迎使用 Mixed Reality 功能工具
description: 瞭解 HoloLens 和 VR 開發的 MR 功能工具的基本概念。
author: davidkline-ms
ms.author: v-hferrone
ms.date: 03/04/2021
ms.topic: article
ms.localizationpriority: high
keywords: 最新狀態, 開始使用, 基本概念, unity, visual studio, 工具組, 混合實境頭戴式裝置, windows 混合實境頭戴式裝置, 虛擬實境頭戴式裝置, 安裝, Windows, HoloLens, 模擬器, unreal, openxr
ms.openlocfilehash: 0244c3de51a44ed6d37137a3206b61ca4911f622
ms.sourcegitcommit: ece91dbba40981720fe7e1a7c3b93e8b75ff71ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/10/2021
ms.locfileid: "102547237"
---
# <a name="welcome-to-the-mixed-reality-feature-tool"></a><span data-ttu-id="9a040-104">歡迎使用 Mixed Reality 功能工具</span><span class="sxs-lookup"><span data-stu-id="9a040-104">Welcome to the Mixed Reality Feature Tool</span></span>

![混合現實功能工具橫幅影像](images/feature-tool-banner.png)

> [!IMPORTANT]
> <span data-ttu-id="9a040-106">Mixed Reality 功能工具目前僅適用于 Unity。</span><span class="sxs-lookup"><span data-stu-id="9a040-106">The Mixed Reality Feature Tool is only available for Unity at the moment.</span></span> <span data-ttu-id="9a040-107">如果您是在 Unreal 中進行開發，請參閱 [工具安裝](../install-the-tools.md) 檔。</span><span class="sxs-lookup"><span data-stu-id="9a040-107">If you're developing in Unreal, refer to the [tools installation](../install-the-tools.md) documentation.</span></span>

<span data-ttu-id="9a040-108">「混合現實」功能工具是一種新方法，可讓開發人員探索、更新和新增混合現實功能套件至 Unity 專案。</span><span class="sxs-lookup"><span data-stu-id="9a040-108">The Mixed Reality Feature Tool is a new way for developers to discover, update, and add Mixed Reality feature packages into Unity projects.</span></span> <span data-ttu-id="9a040-109">您可以依名稱或類別搜尋套件、查看其相依性，甚至在匯入之前查看專案資訊清單檔的建議變更。</span><span class="sxs-lookup"><span data-stu-id="9a040-109">You can search packages by name or category, see their dependencies, and even view proposed changes to your projects manifest file before importing.</span></span> <span data-ttu-id="9a040-110">如果您之前從未使用過資訊清單檔，它就是包含所有專案套件的 JSON 檔案。</span><span class="sxs-lookup"><span data-stu-id="9a040-110">If you've never worked with a manifest file before, it's a JSON file containing all your projects packages.</span></span> <span data-ttu-id="9a040-111">驗證您想要的封裝之後，混合現實功能工具會將這些套件下載到您選擇的專案。</span><span class="sxs-lookup"><span data-stu-id="9a040-111">Once you've validated the packages you want, the Mixed Reality Feature tool will download them into the project of your choice.</span></span>

## <a name="system-requirements"></a><span data-ttu-id="9a040-112">系統需求</span><span class="sxs-lookup"><span data-stu-id="9a040-112">System requirements</span></span>

<span data-ttu-id="9a040-113">在您可以執行混合現實功能工具之前，您需要：</span><span class="sxs-lookup"><span data-stu-id="9a040-113">Before you can run the Mixed Reality Feature Tool, you'll need:</span></span>

* [<span data-ttu-id="9a040-114">.NET 5.0 執行時間</span><span class="sxs-lookup"><span data-stu-id="9a040-114">.NET 5.0 runtime</span></span>](https://dotnet.microsoft.com/download/dotnet/5.0)
* [<span data-ttu-id="9a040-115">Windows 10</span><span class="sxs-lookup"><span data-stu-id="9a040-115">Windows 10</span></span>](https://www.microsoft.com/software-download/windows10ISO)

> [!NOTE]
> <span data-ttu-id="9a040-116">Mixed Reality 功能工具目前僅在 Windows 上執行，但 MacOS 支援即將推出！</span><span class="sxs-lookup"><span data-stu-id="9a040-116">The Mixed Reality Feature Tool currently only runs on Windows, but MacOS support is coming soon!</span></span>

## <a name="download"></a><span data-ttu-id="9a040-117">下載</span><span class="sxs-lookup"><span data-stu-id="9a040-117">Download</span></span>

<span data-ttu-id="9a040-118">設定好環境之後：</span><span class="sxs-lookup"><span data-stu-id="9a040-118">Once you have your environment set up:</span></span>

* <span data-ttu-id="9a040-119">請從 Microsoft 下載中心[下載最新版本的混合現實功能工具](https://aka.ms/MRFeatureTool)。</span><span class="sxs-lookup"><span data-stu-id="9a040-119">[Download the latest version of the Mixed Reality Feature Tool](https://aka.ms/MRFeatureTool) from the Microsoft Download Center.</span></span>
* <span data-ttu-id="9a040-120">當下載完成時，請將檔案解壓縮，並將它儲存到您的桌面</span><span class="sxs-lookup"><span data-stu-id="9a040-120">When the download completes, unzip the file and save it to your desktop</span></span>
    * <span data-ttu-id="9a040-121">建議您建立可執行檔的快捷方式，以加快存取的速度</span><span class="sxs-lookup"><span data-stu-id="9a040-121">We recommend creating a shortcut to the executable file for faster access</span></span>

> [!NOTE]
> <span data-ttu-id="9a040-122">如果您不熟悉使用 Unity 套件管理員，請遵循我們的 [UPM 指示](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/configuration/usingupm#managing-mixed-reality-features-with-the-unity-package-manager)。</span><span class="sxs-lookup"><span data-stu-id="9a040-122">If you're new to using the Unity Package Manager, follow our [UPM instructions](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/configuration/usingupm#managing-mixed-reality-features-with-the-unity-package-manager).</span></span>

## <a name="changes-in-this-release"></a><span data-ttu-id="9a040-123">此版本中的變更</span><span class="sxs-lookup"><span data-stu-id="9a040-123">Changes in this release</span></span>

<span data-ttu-id="9a040-124">版本 1.0.2103 Beta 包含下列修正：</span><span class="sxs-lookup"><span data-stu-id="9a040-124">Version 1.0.2103 Beta includes the following fixes:</span></span>

* <span data-ttu-id="9a040-125">下載錯誤偵測的改進。</span><span class="sxs-lookup"><span data-stu-id="9a040-125">Improvements to download error detection.</span></span>
* <span data-ttu-id="9a040-126">更新資訊清單如何寫入，以避免無法正確更新。</span><span class="sxs-lookup"><span data-stu-id="9a040-126">Updates on how manifests are written to avoid failure to update correctly.</span></span>
* <span data-ttu-id="9a040-127">Escpaing 已從專案資訊清單中的檔案路徑移除。</span><span class="sxs-lookup"><span data-stu-id="9a040-127">Escpaing has been removed from file paths in the project manifest.</span></span>

<span data-ttu-id="9a040-128">此版本已新增下列功能：</span><span class="sxs-lookup"><span data-stu-id="9a040-128">The following features have been added in this release:</span></span>

* <span data-ttu-id="9a040-129">現在會快取功能目錄。</span><span class="sxs-lookup"><span data-stu-id="9a040-129">The feature catalog is now cached.</span></span> <span data-ttu-id="9a040-130">若要檢查是否有新功能和更新，請使用探索中的 [重新整理] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="9a040-130">To check for new features and updates, please use the refresh button in Discovery.</span></span>
* <span data-ttu-id="9a040-131">將專案選取從匯入步驟移至探索之前。</span><span class="sxs-lookup"><span data-stu-id="9a040-131">Move project selection from the Import step to before Discovery.</span></span>
* <span data-ttu-id="9a040-132">可用的套件會依專案的指定 Unity 版本進行篩選。</span><span class="sxs-lookup"><span data-stu-id="9a040-132">Available packages are filtered by the project's specified Unity version.</span></span>
* <span data-ttu-id="9a040-133">探索視圖現在會顯示目前已安裝的套件。</span><span class="sxs-lookup"><span data-stu-id="9a040-133">The discovery view now displays currently installed packages.</span></span>

## <a name="1-getting-started"></a><span data-ttu-id="9a040-134">1.開始使用</span><span class="sxs-lookup"><span data-stu-id="9a040-134">1. Getting started</span></span>

<span data-ttu-id="9a040-135">從可執行檔啟動「混合現實」功能工具，其會在第一次啟動時顯示起始頁：</span><span class="sxs-lookup"><span data-stu-id="9a040-135">Launch the Mixed Reality Feature Tool from the executable file, which displays the start page on first launch:</span></span>

![開始使用](images/FeatureToolStart.png)

<span data-ttu-id="9a040-137">從 [開始] 頁面，您可以：</span><span class="sxs-lookup"><span data-stu-id="9a040-137">From the start page, you can:</span></span>

* <span data-ttu-id="9a040-138">使用 **齒輪圖示** 按鈕 [設定](configuring-feature-tool.md)工具設定</span><span class="sxs-lookup"><span data-stu-id="9a040-138">[Configure](configuring-feature-tool.md) tool settings using the **gear icon** button</span></span>
* <span data-ttu-id="9a040-139">使用 **問號** 按鈕來啟動預設的網頁瀏覽器，並顯示我們的檔</span><span class="sxs-lookup"><span data-stu-id="9a040-139">Use the **question mark** button to launch the default web browser and display our documentation</span></span>
* <span data-ttu-id="9a040-140">選取 [ **開始** ] 以開始探索功能套件</span><span class="sxs-lookup"><span data-stu-id="9a040-140">Select **Start** to begin discovering feature packages</span></span>

## <a name="2-selecting-your-unity-project"></a><span data-ttu-id="9a040-141">2. 選取您的 Unity 專案</span><span class="sxs-lookup"><span data-stu-id="9a040-141">2. Selecting your Unity project</span></span>

<span data-ttu-id="9a040-142">為確保您專案的 Unity 版本支援所有探索到的功能，第一個步驟是使用 [專案路徑] 欄位) 左邊的 **省略號** 按鈕 (，將 [Mixed Reality] 功能工具指向您的專案。</span><span class="sxs-lookup"><span data-stu-id="9a040-142">To ensure that all discovered features are supported on your project's version of Unity, the fist step is to point the Mixed Reality Feature Tool to your project using the **ellipsis** button (to the left of the project path field).</span></span>

![選取 Unity 專案](images/FeatureToolSelectUnityProject.png)

> [!NOTE]
> <span data-ttu-id="9a040-144">流覽 Unity 專案資料夾時顯示的對話方塊會包含 ' _ ' 作為檔案名。</span><span class="sxs-lookup"><span data-stu-id="9a040-144">The dialog that's displayed when browsing for the Unity project folder contains '_' as the file name.</span></span> <span data-ttu-id="9a040-145">檔案名必須有一個值，才能選取該資料夾。</span><span class="sxs-lookup"><span data-stu-id="9a040-145">There must be a value for the file name to enable the folder to be selected.</span></span>

<span data-ttu-id="9a040-146">當您找到專案的資料夾時，請按一下 [開啟] 按鈕以返回 [混合現實] 功能工具。</span><span class="sxs-lookup"><span data-stu-id="9a040-146">When you have located your project's folder, click the Open button to return to the Mixed Reality Feature Tool.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9a040-147">「混合現實」功能工具會執行驗證，以確保它已導向至 Unity 專案資料夾。</span><span class="sxs-lookup"><span data-stu-id="9a040-147">The Mixed Reality Feature Tool performs validation to ensure that it has been directed to a Unity project folder.</span></span> <span data-ttu-id="9a040-148">資料夾必須包含 `Assets` `Packages` 和 `Project Settings` 資料夾。</span><span class="sxs-lookup"><span data-stu-id="9a040-148">The folder must contain `Assets`, `Packages` and `Project Settings` folders.</span></span>

## <a name="3-discovering-and-acquiring-feature-packages"></a><span data-ttu-id="9a040-149">3. 探索和取得功能套件</span><span class="sxs-lookup"><span data-stu-id="9a040-149">3. Discovering and acquiring feature packages</span></span>

> [!NOTE]
> <span data-ttu-id="9a040-150">版本 1.0.2103 Beta 現在會在每次存取伺服器時，快取功能目錄內容。</span><span class="sxs-lookup"><span data-stu-id="9a040-150">Version 1.0.2103 Beta now caches the feature catalog contents whenever the server is accessed.</span></span> <span data-ttu-id="9a040-151">這項變更可讓您快速存取可用的功能，代價是顯示絕對最新的資料。</span><span class="sxs-lookup"><span data-stu-id="9a040-151">This change enables fast access to available features, at the expense of displaying the absolute latest data.</span></span> <span data-ttu-id="9a040-152">若要更新目錄，請 **使用 [重新** 整理] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="9a040-152">To update the catalog, please use the **Refresh** button.</span></span>

<span data-ttu-id="9a040-153">功能會依類別目錄分組，讓您更容易找到專案。</span><span class="sxs-lookup"><span data-stu-id="9a040-153">Features are grouped by category to make things easier to find.</span></span> <span data-ttu-id="9a040-154">例如， **Mixed Reality 工具** 組類別有數個功能可供您選擇：</span><span class="sxs-lookup"><span data-stu-id="9a040-154">For example, the **Mixed Reality Toolkit** category has several features for you to choose from:</span></span>

![探索和收購](images/FeatureToolDiscovery.png)

<span data-ttu-id="9a040-156">當「混合現實」功能工具辨識先前匯入的功能 (s) 時，它會顯示通知訊息。</span><span class="sxs-lookup"><span data-stu-id="9a040-156">When the Mixed Reality Feature Tool recognizes previously imported feature(s), it displays a notification message by each.</span></span>

![匯入功能的通知](images/feature-tool-imported-note.png)


<span data-ttu-id="9a040-158">完成選擇之後，請選取 [ **取得功能** ]，從目錄中提取所有必要的套件。</span><span class="sxs-lookup"><span data-stu-id="9a040-158">Once you've made your choices, select **Get features** to fetch all the required packages from the catalog.</span></span> <span data-ttu-id="9a040-159">如需詳細資訊，請參閱 [探索和取得功能](discovering-features.md)。</span><span class="sxs-lookup"><span data-stu-id="9a040-159">For more information, please see [discovering and acquiring features](discovering-features.md).</span></span>

## <a name="4-importing-feature-packages"></a><span data-ttu-id="9a040-160">4. 匯入功能套件</span><span class="sxs-lookup"><span data-stu-id="9a040-160">4. Importing feature packages</span></span>

<span data-ttu-id="9a040-161">取得後，會顯示一組完整的封裝，以及必要的相依性清單。</span><span class="sxs-lookup"><span data-stu-id="9a040-161">Following acquisition, the complete set of packages is presented, along with a list of required dependencies.</span></span> <span data-ttu-id="9a040-162">如果您需要變更任何功能或封裝選項，這是時間：</span><span class="sxs-lookup"><span data-stu-id="9a040-162">If you need to change any feature or package selections, this is the time:</span></span>

![匯入封裝](images/FeatureToolImport.png)

<span data-ttu-id="9a040-164">強烈建議使用 [ **驗證** ] 按鈕，以確保 Unity 專案可以成功匯入選取的功能。</span><span class="sxs-lookup"><span data-stu-id="9a040-164">We highly recommend using the **Validate** button to ensure the Unity project can successfully import the selected features.</span></span> <span data-ttu-id="9a040-165">驗證之後，您會看到一個快顯對話方塊，其中包含成功訊息或已識別問題的清單。</span><span class="sxs-lookup"><span data-stu-id="9a040-165">After validation, you'll see a pop-up dialog with a success message or a list of identified issues.</span></span>

<span data-ttu-id="9a040-166">選取 [匯 **入** ] 以繼續。</span><span class="sxs-lookup"><span data-stu-id="9a040-166">Select **Import** to continue.</span></span>

> [!NOTE]
> <span data-ttu-id="9a040-167">按一下 [匯 **入** ] 按鈕之後，如果有任何問題，則會顯示簡單的訊息。</span><span class="sxs-lookup"><span data-stu-id="9a040-167">After clicking the **Import** button, if any issues remain a simple message will be displayed.</span></span> <span data-ttu-id="9a040-168">建議您按一下 [否]，並使用 [ **驗證** ] 按鈕來查看和解決問題。</span><span class="sxs-lookup"><span data-stu-id="9a040-168">The recommendation is to click No and to use the **Validate** button to view and resolve the issues.</span></span>

<span data-ttu-id="9a040-169">如需詳細資訊，請參閱匯 [入功能](importing-features.md)。</span><span class="sxs-lookup"><span data-stu-id="9a040-169">For more information, please see [importing features](importing-features.md).</span></span>

## <a name="5-reviewing-and-approving-project-changes"></a><span data-ttu-id="9a040-170">5. 審核和核准專案變更</span><span class="sxs-lookup"><span data-stu-id="9a040-170">5. Reviewing and approving project changes</span></span>

<span data-ttu-id="9a040-171">最後一個步驟是檢查並核准資訊清單和專案檔案的建議變更：</span><span class="sxs-lookup"><span data-stu-id="9a040-171">The final step is reviewing and approving the proposed changes to the manifest and project files:</span></span>

* <span data-ttu-id="9a040-172">建議的資訊清單變更會顯示在左側</span><span class="sxs-lookup"><span data-stu-id="9a040-172">The proposed changes to the manifest are displayed on the left</span></span>
* <span data-ttu-id="9a040-173">要加入至專案的檔案會列在右邊</span><span class="sxs-lookup"><span data-stu-id="9a040-173">The files to be added to the project are listed to the right</span></span>
* <span data-ttu-id="9a040-174">[ **比較** ] 按鈕允許並排查看目前的資訊清單和建議的變更</span><span class="sxs-lookup"><span data-stu-id="9a040-174">The **Compare** button allows for side by side viewing of the current manifest and the proposed changes</span></span>

![授權](images/FeatureToolApprovalRequest.png)

<span data-ttu-id="9a040-176">如需詳細資訊，請參閱 [審核和核准專案修改](reviewing-changes.md)。</span><span class="sxs-lookup"><span data-stu-id="9a040-176">For more information, see [reviewing and approving project modifications](reviewing-changes.md).</span></span>

## <a name="6-project-updated"></a><span data-ttu-id="9a040-177">6. 更新專案</span><span class="sxs-lookup"><span data-stu-id="9a040-177">6. Project updated</span></span>

<span data-ttu-id="9a040-178">當建議的變更經過核准後，您的目標 Unity 專案就會更新，以參考選取的混合現實功能。</span><span class="sxs-lookup"><span data-stu-id="9a040-178">When the proposed changes are approved, your target Unity project is updated to reference the selected Mixed Reality features.</span></span>

![專案已更新](images/FeatureToolProjectUpdated.png)

<span data-ttu-id="9a040-180">Unity 專案的 [ **套件** ] 資料夾現在有一個 **MixedReality** 子資料夾，其中包含功能套件檔案 (s) ，資訊清單會包含適當的參考 (s) 。</span><span class="sxs-lookup"><span data-stu-id="9a040-180">The Unity project's **Packages** folder now has a **MixedReality** subfolder with the feature package file(s) and the manifest will contain the appropriate reference(s).</span></span>

<span data-ttu-id="9a040-181">返回 Unity、等候新選取的功能載入，然後開始建立！</span><span class="sxs-lookup"><span data-stu-id="9a040-181">Return to Unity, wait for the new selected features to load, and start building!</span></span>

## <a name="see-also"></a><span data-ttu-id="9a040-182">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9a040-182">See also</span></span>

- [<span data-ttu-id="9a040-183">設定功能工具</span><span class="sxs-lookup"><span data-stu-id="9a040-183">Configuring the feature tool</span></span>](configuring-feature-tool.md)
- [<span data-ttu-id="9a040-184">探索和收購</span><span class="sxs-lookup"><span data-stu-id="9a040-184">Discovery and acquisition</span></span>](discovering-features.md)
- [<span data-ttu-id="9a040-185">查看功能套件詳細資料</span><span class="sxs-lookup"><span data-stu-id="9a040-185">Viewing feature package details</span></span>](viewing-package-details.md)
- [<span data-ttu-id="9a040-186">匯入選取的封裝</span><span class="sxs-lookup"><span data-stu-id="9a040-186">Importing selected packages</span></span>](importing-features.md)
- [<span data-ttu-id="9a040-187">審核和核准專案修改</span><span class="sxs-lookup"><span data-stu-id="9a040-187">Reviewing and approving project modifications</span></span>](reviewing-changes.md)
