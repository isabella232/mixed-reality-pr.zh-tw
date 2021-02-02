---
title: 歡迎使用 Mixed Reality 功能工具
description: 瞭解 HoloLens 和 VR 開發的 MR 功能工具的基本概念。
author: davidkline-ms
ms.author: v-hferrone
ms.date: 01/27/2021
ms.topic: article
ms.localizationpriority: high
keywords: 最新狀態, 開始使用, 基本概念, unity, visual studio, 工具組, 混合實境頭戴式裝置, windows 混合實境頭戴式裝置, 虛擬實境頭戴式裝置, 安裝, Windows, HoloLens, 模擬器, unreal, openxr
ms.openlocfilehash: b9d54edb251cfe22d4f5fbea6fa8c923f6ff2d69
ms.sourcegitcommit: cef969ffd22dc1e5a1e9c3c32fbf0646206519a1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/01/2021
ms.locfileid: "99244580"
---
# <a name="welcome-to-the-mixed-reality-feature-tool"></a><span data-ttu-id="6c994-104">歡迎使用 Mixed Reality 功能工具</span><span class="sxs-lookup"><span data-stu-id="6c994-104">Welcome to the Mixed Reality Feature Tool</span></span>

![混合現實功能工具橫幅影像](images/feature-tool-banner.png)

> [!IMPORTANT]
> <span data-ttu-id="6c994-106">Mixed Reality 功能工具目前僅適用于 Unity。</span><span class="sxs-lookup"><span data-stu-id="6c994-106">The Mixed Reality Feature Tool is only available for Unity at the moment.</span></span> <span data-ttu-id="6c994-107">如果您是在 Unreal 中進行開發，請參閱 [工具安裝](../install-the-tools.md) 檔。</span><span class="sxs-lookup"><span data-stu-id="6c994-107">If you're developing in Unreal, refer to the [tools installation](../install-the-tools.md) documentation.</span></span>

<span data-ttu-id="6c994-108">「混合現實」功能工具是一種新方法，可讓開發人員探索、更新和新增混合現實功能套件至 Unity 專案。</span><span class="sxs-lookup"><span data-stu-id="6c994-108">The Mixed Reality Feature Tool is a new way for developers to discover, update, and add Mixed Reality feature packages into Unity projects.</span></span> <span data-ttu-id="6c994-109">您可以依名稱或類別搜尋套件、查看其相依性，甚至在匯入之前查看專案資訊清單檔的建議變更。</span><span class="sxs-lookup"><span data-stu-id="6c994-109">You can search packages by name or category, see their dependencies, and even view proposed changes to your projects manifest file before importing.</span></span> <span data-ttu-id="6c994-110">如果您之前從未使用過資訊清單檔，它就是包含所有專案套件的 JSON 檔案。</span><span class="sxs-lookup"><span data-stu-id="6c994-110">If you've never worked with a manifest file before, it's a JSON file containing all your projects packages.</span></span> <span data-ttu-id="6c994-111">驗證您想要的封裝之後，混合現實功能工具會將這些套件下載到您選擇的專案。</span><span class="sxs-lookup"><span data-stu-id="6c994-111">Once you've validated the packages you want, the Mixed Reality Feature tool will download them into the project of your choice.</span></span>

## <a name="system-requirements"></a><span data-ttu-id="6c994-112">系統需求</span><span class="sxs-lookup"><span data-stu-id="6c994-112">System requirements</span></span>

<span data-ttu-id="6c994-113">在您可以執行混合現實功能工具之前，您需要：</span><span class="sxs-lookup"><span data-stu-id="6c994-113">Before you can run the Mixed Reality Feature Tool, you'll need:</span></span>

* [<span data-ttu-id="6c994-114">.NET 5.0 執行時間</span><span class="sxs-lookup"><span data-stu-id="6c994-114">.NET 5.0 runtime</span></span>](https://dotnet.microsoft.com/download/dotnet/5.0)
* [<span data-ttu-id="6c994-115">Windows 10</span><span class="sxs-lookup"><span data-stu-id="6c994-115">Windows 10</span></span>](https://www.microsoft.com/software-download/windows10ISO)

> [!NOTE]
> <span data-ttu-id="6c994-116">Mixed Reality 功能工具目前僅在 Windows 上執行，但 MacOS 支援即將推出！</span><span class="sxs-lookup"><span data-stu-id="6c994-116">The Mixed Reality Feature Tool currently only runs on Windows, but MacOS support is coming soon!</span></span>

<span data-ttu-id="6c994-117">設定好環境之後：</span><span class="sxs-lookup"><span data-stu-id="6c994-117">Once you have your environment set up:</span></span>

* <span data-ttu-id="6c994-118">請從 [Microsoft 下載中心](https://aka.ms/MRFeatureTool)下載最新版本的混合現實功能工具。</span><span class="sxs-lookup"><span data-stu-id="6c994-118">Download the latest version of the Mixed Reality Feature Tool from the [Microsoft Download Center](https://aka.ms/MRFeatureTool).</span></span>
* <span data-ttu-id="6c994-119">當下載完成時，請將檔案解壓縮，並將它儲存到您的桌面</span><span class="sxs-lookup"><span data-stu-id="6c994-119">When the download completes, unzip the file and save it to your desktop</span></span>
    * <span data-ttu-id="6c994-120">建議您建立可執行檔的快捷方式，以加快存取的速度</span><span class="sxs-lookup"><span data-stu-id="6c994-120">We recommend creating a shortcut to the executable file for faster access</span></span>

## <a name="1-getting-started"></a><span data-ttu-id="6c994-121">1.開始使用</span><span class="sxs-lookup"><span data-stu-id="6c994-121">1. Getting started</span></span>

<span data-ttu-id="6c994-122">從可執行檔啟動「混合現實」功能工具，其會在第一次啟動時顯示起始頁：</span><span class="sxs-lookup"><span data-stu-id="6c994-122">Launch the Mixed Reality Feature Tool from the executable file, which displays the start page on first launch:</span></span>

![開始使用](images/FeatureToolStart.png)

<span data-ttu-id="6c994-124">從 [開始] 頁面，您可以：</span><span class="sxs-lookup"><span data-stu-id="6c994-124">From the start page, you can:</span></span>

* <span data-ttu-id="6c994-125">使用 **齒輪圖示** 按鈕 [設定](configuring-feature-tool.md)工具設定</span><span class="sxs-lookup"><span data-stu-id="6c994-125">[Configure](configuring-feature-tool.md) tool settings using the **gear icon** button</span></span>
* <span data-ttu-id="6c994-126">使用 **問號** 按鈕來啟動預設的網頁瀏覽器，並顯示我們的檔</span><span class="sxs-lookup"><span data-stu-id="6c994-126">Use the **question mark** button to launch the default web browser and display our documentation</span></span>
* <span data-ttu-id="6c994-127">選取 [ **開始** ] 以開始探索功能套件</span><span class="sxs-lookup"><span data-stu-id="6c994-127">Select **Start** to begin discovering feature packages</span></span>

## <a name="2-discovering-and-acquiring-feature-packages"></a><span data-ttu-id="6c994-128">2. 探索和取得功能套件</span><span class="sxs-lookup"><span data-stu-id="6c994-128">2. Discovering and acquiring feature packages</span></span>

<span data-ttu-id="6c994-129">當您按下 [啟動] 時，就會立即取出功能套件目錄。</span><span class="sxs-lookup"><span data-stu-id="6c994-129">The feature package catalog is retrieved as soon as you press Start.</span></span> <span data-ttu-id="6c994-130">功能會依類別目錄分組，讓您更容易找到專案。</span><span class="sxs-lookup"><span data-stu-id="6c994-130">Features are grouped by category to make things easier to find.</span></span> <span data-ttu-id="6c994-131">例如， **Mixed Reality 工具** 組類別有數個功能可供您選擇：</span><span class="sxs-lookup"><span data-stu-id="6c994-131">For example, the **Mixed Reality Toolkit** category has several features for you to choose from:</span></span>

![探索和收購](images/FeatureToolDiscovery.png)

<span data-ttu-id="6c994-133">完成選擇之後，請選取 [ **取得功能** ]，從目錄中提取所有必要的套件。</span><span class="sxs-lookup"><span data-stu-id="6c994-133">Once you've made your choices, select **Get features** to fetch all the required packages from the catalog.</span></span> <span data-ttu-id="6c994-134">如需詳細資訊，請參閱 [探索和取得功能](discovering-features.md)。</span><span class="sxs-lookup"><span data-stu-id="6c994-134">For more information, please see [discovering and acquiring features](discovering-features.md).</span></span>

## <a name="3-importing-feature-packages"></a><span data-ttu-id="6c994-135">3. 匯入功能套件</span><span class="sxs-lookup"><span data-stu-id="6c994-135">3. Importing feature packages</span></span>

<span data-ttu-id="6c994-136">取得後，會顯示一組完整的封裝，以及必要的相依性清單。</span><span class="sxs-lookup"><span data-stu-id="6c994-136">Following acquisition, the complete set of packages is presented, along with a list of required dependencies.</span></span> <span data-ttu-id="6c994-137">如果您需要變更任何功能或封裝選項，這是時間：</span><span class="sxs-lookup"><span data-stu-id="6c994-137">If you need to change any feature or package selections, this is the time:</span></span>

![匯入封裝](images/FeatureToolImport.png)

<span data-ttu-id="6c994-139">強烈建議使用 [ **驗證** ] 按鈕，以確保 Unity 專案可以成功匯入選取的功能。</span><span class="sxs-lookup"><span data-stu-id="6c994-139">We highly recommend using the **Validate** button to ensure the Unity project can successfully import the selected features.</span></span> <span data-ttu-id="6c994-140">驗證之後，您會看到一個快顯對話方塊，其中包含成功訊息或已識別問題的清單。</span><span class="sxs-lookup"><span data-stu-id="6c994-140">After validation, you'll see a pop-up dialog with a success message or a list of identified issues.</span></span>

<span data-ttu-id="6c994-141">您也必須先設定目標 Unity 專案的位置，才能匯入。</span><span class="sxs-lookup"><span data-stu-id="6c994-141">You also need to set the location of the target Unity project before you import.</span></span> <span data-ttu-id="6c994-142">使用 [專案路徑] 欄位左側的 **省略號** 按鈕進行流覽。</span><span class="sxs-lookup"><span data-stu-id="6c994-142">Use the **ellipsis** button to the left of the project path field to browse.</span></span> <span data-ttu-id="6c994-143">當您完成流覽檔案系統時，請開啟包含目標 Unity 專案的資料夾。</span><span class="sxs-lookup"><span data-stu-id="6c994-143">When you're done navigating your file system, open the folder containing your target Unity project.</span></span>

> [!NOTE]
> <span data-ttu-id="6c994-144">流覽 Unity 專案資料夾時顯示的對話方塊會包含 ' _ ' 作為檔案名。</span><span class="sxs-lookup"><span data-stu-id="6c994-144">The dialog that's displayed when browsing for the Unity project folder contains '_' as the file name.</span></span> <span data-ttu-id="6c994-145">檔案名必須有一個值，才能選取該資料夾。</span><span class="sxs-lookup"><span data-stu-id="6c994-145">There must be a value for the file name to enable the folder to be selected.</span></span>

<span data-ttu-id="6c994-146">選取 [匯 **入** ] 以繼續。</span><span class="sxs-lookup"><span data-stu-id="6c994-146">Select **Import** to continue.</span></span>

> [!NOTE]
> <span data-ttu-id="6c994-147">按一下 [匯 **入** ] 按鈕之後，如果有任何問題，則會顯示簡單的訊息。</span><span class="sxs-lookup"><span data-stu-id="6c994-147">After clicking the **Import** button, if any issues remain a simple message will be displayed.</span></span> <span data-ttu-id="6c994-148">建議您按一下 [否]，並使用 [ **驗證** ] 按鈕來查看和解決問題。</span><span class="sxs-lookup"><span data-stu-id="6c994-148">The recommendation is to click No and to use the **Validate** button to view and resolve the issues.</span></span>

<span data-ttu-id="6c994-149">如需詳細資訊，請參閱匯 [入功能](importing-features.md)。</span><span class="sxs-lookup"><span data-stu-id="6c994-149">For more information, please see [importing features](importing-features.md).</span></span>

## <a name="4-reviewing-and-approving-project-changes"></a><span data-ttu-id="6c994-150">4. 審核和核准專案變更</span><span class="sxs-lookup"><span data-stu-id="6c994-150">4. Reviewing and approving project changes</span></span>

<span data-ttu-id="6c994-151">最後一個步驟是檢查並核准資訊清單和專案檔案的建議變更：</span><span class="sxs-lookup"><span data-stu-id="6c994-151">The final step is reviewing and approving the proposed changes to the manifest and project files:</span></span>

* <span data-ttu-id="6c994-152">建議的資訊清單變更會顯示在左側</span><span class="sxs-lookup"><span data-stu-id="6c994-152">The proposed changes to the manifest are displayed on the left</span></span>
* <span data-ttu-id="6c994-153">要加入至專案的檔案會列在右邊</span><span class="sxs-lookup"><span data-stu-id="6c994-153">The files to be added to the project are listed to the right</span></span>
* <span data-ttu-id="6c994-154">[ **比較** ] 按鈕允許並排查看目前的資訊清單和建議的變更</span><span class="sxs-lookup"><span data-stu-id="6c994-154">The **Compare** button allows for side by side viewing of the current manifest and the proposed changes</span></span>

![授權](images/FeatureToolApprovalRequest.png)

<span data-ttu-id="6c994-156">如需詳細資訊，請參閱 [審核和核准專案修改](reviewing-changes.md)。</span><span class="sxs-lookup"><span data-stu-id="6c994-156">For more information, see [reviewing and approving project modifications](reviewing-changes.md).</span></span>

## <a name="5-project-updated"></a><span data-ttu-id="6c994-157">5. 更新專案</span><span class="sxs-lookup"><span data-stu-id="6c994-157">5. Project updated</span></span>

<span data-ttu-id="6c994-158">當建議的變更經過核准後，您的目標 Unity 專案就會更新，以參考選取的混合現實功能：</span><span class="sxs-lookup"><span data-stu-id="6c994-158">When the proposed changes are approved, your target Unity project is updated to reference the selected Mixed Reality features:</span></span>

![專案已更新](images/FeatureToolProjectUpdated.png)

<span data-ttu-id="6c994-160">Unity 專案的 [ **套件** ] 資料夾現在有一個 **MixedReality** 子資料夾，其中包含功能套件檔案 (s) ，資訊清單會包含適當的參考 (s) 。</span><span class="sxs-lookup"><span data-stu-id="6c994-160">The Unity project's **Packages** folder now has a **MixedReality** subfolder with the feature package file(s) and the manifest will contain the appropriate reference(s).</span></span>

<span data-ttu-id="6c994-161">返回 Unity、等候新選取的功能載入，然後開始建立！</span><span class="sxs-lookup"><span data-stu-id="6c994-161">Return to Unity, wait for the new selected features to load, and start building!</span></span>

## <a name="see-also"></a><span data-ttu-id="6c994-162">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6c994-162">See also</span></span>

- [<span data-ttu-id="6c994-163">設定功能工具</span><span class="sxs-lookup"><span data-stu-id="6c994-163">Configuring the feature tool</span></span>](configuring-feature-tool.md)
- [<span data-ttu-id="6c994-164">探索和收購</span><span class="sxs-lookup"><span data-stu-id="6c994-164">Discovery and acquisition</span></span>](discovering-features.md)
- [<span data-ttu-id="6c994-165">查看功能套件詳細資料</span><span class="sxs-lookup"><span data-stu-id="6c994-165">Viewing feature package details</span></span>](viewing-package-details.md)
- [<span data-ttu-id="6c994-166">匯入選取的封裝</span><span class="sxs-lookup"><span data-stu-id="6c994-166">Importing selected packages</span></span>](importing-features.md)
- [<span data-ttu-id="6c994-167">審核和核准專案修改</span><span class="sxs-lookup"><span data-stu-id="6c994-167">Reviewing and approving project modifications</span></span>](reviewing-changes.md)
