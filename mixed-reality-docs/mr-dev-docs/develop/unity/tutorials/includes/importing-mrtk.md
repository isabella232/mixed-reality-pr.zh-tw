---
ms.openlocfilehash: 2420e68a0753739111fc2c5eecfbd1da563f52c2
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175966"
---
# <a name="unity-2020--openxr"></a>[<span data-ttu-id="ff0bd-101">Unity 2020 + OpenXR</span><span class="sxs-lookup"><span data-stu-id="ff0bd-101">Unity 2020 + OpenXR</span></span>](#tab/openxr)

<span data-ttu-id="ff0bd-102">**MixedRealityFeatureTool** 開啟後，按一下 [**開始**] 以開始使用 Mixed Reality 功能工具。</span><span class="sxs-lookup"><span data-stu-id="ff0bd-102">Once **MixedRealityFeatureTool** is opened, click on **Start** to get started with Mixed Reality Feature Tool.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-2.png" width="650px" alt="MixedRealityFeatureTool main screen">

<span data-ttu-id="ff0bd-103">第一個步驟是使用 **省略號** 按鈕將「混合現實」功能工具指向您的 **Project 路徑**，按一下 Project 路徑旁的三個點省略號按鈕，然後流覽至您在瀏覽器中的專案資料夾，例如 _D:\MixedRealityLearning\MRTK 教學_ 課程。</span><span class="sxs-lookup"><span data-stu-id="ff0bd-103">The first step is to point the Mixed Reality Feature Tool to your **Project path** using the **ellipsis** button, click on the Three dots ellipsis button next to the Project path and browse to your project folder in the explorer for example _D:\MixedRealityLearning\MRTK Tutorials_.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-3.png" width="650px" alt="Adding Unity Path for MixedRealityFeatureTool">

<span data-ttu-id="ff0bd-104">當您找到專案的資料夾時，請按一下 [開啟] 按鈕以返回 [混合現實] 功能工具。</span><span class="sxs-lookup"><span data-stu-id="ff0bd-104">When you have located your project's folder, click the Open button to return to the Mixed Reality Feature Tool.</span></span> <span data-ttu-id="ff0bd-105">然後按一下 [ **探索功能**]。</span><span class="sxs-lookup"><span data-stu-id="ff0bd-105">Then click on **Discover Features**.</span></span>

> [!NOTE]
> <span data-ttu-id="ff0bd-106">流覽 Unity 專案資料夾時顯示的對話方塊會包含 ' _ ' 作為檔案名。</span><span class="sxs-lookup"><span data-stu-id="ff0bd-106">The dialog that's displayed when browsing for the Unity project folder contains '_' as the file name.</span></span> <span data-ttu-id="ff0bd-107">檔案名必須有一個值，才能選取該資料夾。</span><span class="sxs-lookup"><span data-stu-id="ff0bd-107">There must be a value for the file name to enable the folder to be selected.</span></span>

> [!Important]
> <span data-ttu-id="ff0bd-108">「混合現實」功能工具會執行驗證，以確保它已導向至 Unity 專案資料夾。</span><span class="sxs-lookup"><span data-stu-id="ff0bd-108">The Mixed Reality Feature Tool performs validation to ensure that it has been directed to a Unity project folder.</span></span> <span data-ttu-id="ff0bd-109">資料夾必須包含資產、封裝和 Project 設定資料夾。</span><span class="sxs-lookup"><span data-stu-id="ff0bd-109">The folder must contain Assets, Packages and Project Settings folders.</span></span>

<span data-ttu-id="ff0bd-110">功能會依類別目錄分組，讓您更容易尋找，請按一下 [ **Mixed Reality 工具** 組] 下拉式清單來尋找與混合現實工具組相關的套件，然後按一下 [ **平臺支援** ] 下拉式清單，以尋找與各種支援平臺相關的套件。</span><span class="sxs-lookup"><span data-stu-id="ff0bd-110">Features are grouped by category to make things easier to find, click on **Mixed Reality Toolkit** dropdown to find packages relating to the Mixed Reality Toolkit and click on **Platform Support** dropdown to find packages relating various supporting platforms.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-4-openxr.png" width="650px" alt="MixedRealityFeatureTool Discover Features">

<span data-ttu-id="ff0bd-111">檢查 **Mixed Reality 工具組 Foundation** ，然後按一下其旁邊的下拉式清單，選取 [ **MRTK 2.7.2**]，同時檢查 **mixed reality OpenXR 外掛程式 1.0.0** ，然後按一下其旁邊的下拉式清單，以選取最新可用的版本，然後按一下 [ **取得功能** ] 按鈕以下載選取的套件。</span><span class="sxs-lookup"><span data-stu-id="ff0bd-111">Check the **Mixed Reality Toolkit Foundation** and click on the dropdown next to it to select **MRTK 2.7.2**, also check the **Mixed Reality OpenXR Plugin 1.0.0** and click on the dropdown next to it to select most recent version available, then click on **Get features** button to download the selected packages.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-5-openxr.png" width="650px" alt="MixedRealityFeatureTool Open MixedReality">

<span data-ttu-id="ff0bd-112">接下來按一下 [ **驗證** ] 按鈕以驗證選取的封裝，您會看到 [偵測 **不到驗證問題** 的快顯視窗 **] 按一下 [確定]** 關閉快顯視窗，然後按一下 [匯 **入** ] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="ff0bd-112">Next click on the **Validate** button to validate the selected package, you will get a popup with message **No validation issues were detected** click on **OK** to close the popup and click on **Import** button.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-6-openxr.png" width="650px" alt="MixedRealityFeatureTool Select required package">


<span data-ttu-id="ff0bd-113">按一下 [ **核准** ] 按鈕，將 **Mixed Reality 工具** 組新增至專案。</span><span class="sxs-lookup"><span data-stu-id="ff0bd-113">Click on **Approve** Button to add the **Mixed Reality Toolkit** into the project.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-7-openxr.png" width="650px" alt="MixedRealityFeatureTool Validate package">

## <a name="configuring-the-unity-project"></a><span data-ttu-id="ff0bd-114">設定 Unity 專案</span><span class="sxs-lookup"><span data-stu-id="ff0bd-114">Configuring the Unity project</span></span>

<span data-ttu-id="ff0bd-115">Unity 完成從上一節匯入封裝之後，會出現一則警告訊息，以重新開機 Unity 編輯器，以便後端新外掛程式系統，請按一下 **[是]** 。</span><span class="sxs-lookup"><span data-stu-id="ff0bd-115">After Unity has finished importing the package from the previous section, a warning message appears to restart the unity editor to enable to backends for new plugin system, click on **Yes**</span></span>

<img src="../images/mr-learning-base/base-02-section5-step1-1-openxr.png" width="650px" alt="Unity Restart Option">

<span data-ttu-id="ff0bd-116">Unity 重新開機後，MRTK Project 的 [配置器] 視窗隨即出現。</span><span class="sxs-lookup"><span data-stu-id="ff0bd-116">Once the Unity restarts MRTK Project Configurator window should appear.</span></span> <span data-ttu-id="ff0bd-117">如果沒有，您可以藉由前往 **混合現實**  >  **工具** 組  >  **公用程式** 來  >  **設定 MRTK 的 Project**，以手動方式開啟它：</span><span class="sxs-lookup"><span data-stu-id="ff0bd-117">If it doesn't, you can manually open it by going to **Mixed Reality** > **Toolkit** > **Utilities** > **Configure Project for MRTK**:</span></span>

![開啟 MRTK 專案配置器視窗](../images/mr-learning-base/base-02-section5-step1-2-openxr.png)

<span data-ttu-id="ff0bd-119">按一下 **Unity OpenXR 外掛程式** ，以啟用 XR 外掛程式管理，並將其所需的套件新增至您的專案。</span><span class="sxs-lookup"><span data-stu-id="ff0bd-119">Click on **Unity OpenXR Plugin** to Enable XR Plugin Management and add its required packages into your project.</span></span>

![<span data-ttu-id="ff0bd-120">新增 Unity OpenXR 外掛程式</span><span class="sxs-lookup"><span data-stu-id="ff0bd-120">Add Unity OpenXR Plugin</span></span> ](../images/mr-learning-base/base-02-section5-step1-3-openxr.png)

<span data-ttu-id="ff0bd-121">這會匯入 XR 外掛程式管理所需的 unity 套件，一旦完成，請按一下 [MRTK 專案] 設定檔中的 [**顯示 XR Plug-In 管理] 設定**。</span><span class="sxs-lookup"><span data-stu-id="ff0bd-121">This will import required unity packages for XR Plugin Management, once done click on **Show XR Plug-In Management Settings** in MRTK project Configurator.</span></span>

![<span data-ttu-id="ff0bd-122">顯示 XR Plug-In 管理設定</span><span class="sxs-lookup"><span data-stu-id="ff0bd-122">Show XR Plug-In Management Settings</span></span> ](../images/mr-learning-base/base-02-section5-step1-4-openxr.png)

<span data-ttu-id="ff0bd-123">這會開啟 **Project 設定] 視窗**。</span><span class="sxs-lookup"><span data-stu-id="ff0bd-123">This opens **Project Settings window**.</span></span> <span data-ttu-id="ff0bd-124">在 [ **XR 外掛程式管理**] 下的 [Project 設定] 視窗中，確定您處於通用 Windows 平臺設定 (Windows 標誌] 索引標籤) 。</span><span class="sxs-lookup"><span data-stu-id="ff0bd-124">In the Project Settings window under **XR Plug-in Management** Ensure that you are in Universal Windows Platform settings (Windows logo tab).</span></span> <span data-ttu-id="ff0bd-125">此外，請確定已核取 [**啟動時初始化 XR** ]，然後按一下 [ **OpenXR** ] 核取方塊並 **Microsoft HoloLens [功能集**] 核取方塊加以啟用。</span><span class="sxs-lookup"><span data-stu-id="ff0bd-125">Also Ensure **Initialize XR on Startup** is checked, then click **OpenXR** checkbox and **Microsoft HoloLens feature set** checkbox to enable them.</span></span>

![啟用 Open XR](../images/mr-learning-base/base-02-section5-step1-5-openxr.png)

<span data-ttu-id="ff0bd-127">核取 [OpenXR] 核取方塊之後，MRTK Project 的 [配置器] 視窗會顯示 [套用 **設定**] 按鈕的更新訊息。</span><span class="sxs-lookup"><span data-stu-id="ff0bd-127">Once you check OpenXR checkbox, MRTK Project Configurator window will show updated message with **Apply Settings** button.</span></span> <span data-ttu-id="ff0bd-128">按一下 [套用]**設定** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="ff0bd-128">Click **Apply Settings** button.</span></span> 

![Project 設定視窗1](../images/mr-learning-base/base-02-section5-step1-6-openxr.png)

<span data-ttu-id="ff0bd-130">當您按一下 [套用] 設定時，您可能會在主控台中看到此錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="ff0bd-130">When you click Apply Settings, you might see this error message in the Console.</span></span> <span data-ttu-id="ff0bd-131">如果這是唯一的錯誤或沒有錯誤，您可以繼續進行。</span><span class="sxs-lookup"><span data-stu-id="ff0bd-131">You can proceed if this is the only error or there is no error.</span></span>

![OpenXR 遠端處理錯誤訊息](../images/mr-learning-base/base-02-section5-step1-6-openxr-Error.png)

<span data-ttu-id="ff0bd-133">若要驗證 OpenXR 設定，請按一下 **[XR 外掛程式管理]** 下的 [ **OpenXR** ]，並檢查下列專案：</span><span class="sxs-lookup"><span data-stu-id="ff0bd-133">To validate OpenXR configuration, click **OpenXR** under **XR Plug-in Management** and check these items:</span></span>
* <span data-ttu-id="ff0bd-134">深度提交模式： **深度16位**</span><span class="sxs-lookup"><span data-stu-id="ff0bd-134">Depth Submission Mode: **Depth 16 Bit**</span></span>
* <span data-ttu-id="ff0bd-135">互動設定檔： **Microsoft 手互動設定檔**</span><span class="sxs-lookup"><span data-stu-id="ff0bd-135">Interaction Profiles: **Microsoft Hand Interaction Profile**</span></span>

![Project 設定視窗2](../images/mr-learning-base/base-02-section5-step1-7-openxr.png)

> [!TIP]
> <span data-ttu-id="ff0bd-137">您可以選擇是否將 [深度格式] 減少為 16 位元，但這麼做可協助改善專案中的圖形效能。</span><span class="sxs-lookup"><span data-stu-id="ff0bd-137">Reducing the Depth Format to 16-bit is optional but may help improve graphics performance in your project.</span></span> <span data-ttu-id="ff0bd-138">若要深入了解本主題，您可以參閱 MRTK 效能文件中的<a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering" target="_blank">深度緩衝區共用 (HoloLens)</a> 一節。</span><span class="sxs-lookup"><span data-stu-id="ff0bd-138">To learn more about this topic, you can refer to the <a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering" target="_blank">Depth buffer sharing (HoloLens)</a> section of MRTK's Performance documentation.</span></span>


<span data-ttu-id="ff0bd-139">在 [ **MRTK Project** 設定器] 視窗中，按一下 [**下一步**]，然後按一下 [套用]**按鈕以** 套用設定。</span><span class="sxs-lookup"><span data-stu-id="ff0bd-139">In the **MRTK Project Configurator** window, click on **Next**, then click the **Apply** button to apply the settings.</span></span> <span data-ttu-id="ff0bd-140"> (如果您將其關閉，您可以藉由前往 **混合現實**  >  **工具** 組  >  **公用程式**  >  **設定 Project 進行 MRTK** ，以手動方式開啟它) </span><span class="sxs-lookup"><span data-stu-id="ff0bd-140">(If you closed it, you can manually open it by going to **Mixed Reality** > **Toolkit** > **Utilities** > **Configure Project for MRTK**)</span></span>

![Project 設定視窗3](../images/mr-learning-base/base-02-section5-step1-8-openxr.png)

![Project 設定視窗4](../images/mr-learning-base/base-02-section5-step1-9-openxr.png)

<span data-ttu-id="ff0bd-143">當您按一下 [套用] 之後，Unity 將會嘗試重新開機，輸入系統才會生效，請按一下 [套用 **] 以重新** 啟動 Unity 編輯器</span><span class="sxs-lookup"><span data-stu-id="ff0bd-143">Once you click on Apply, Unity will try to restart for the input system to take into effect, click on **Apply** to restart the Unity editor</span></span>

### <a name="configure-additional-project-settings"></a><span data-ttu-id="ff0bd-144">設定其他專案設定</span><span class="sxs-lookup"><span data-stu-id="ff0bd-144">Configure additional project settings</span></span>

<span data-ttu-id="ff0bd-145">在 Unity 功能表中，選取 [**編輯**  >  **Project 設定 ...** ] 以開啟 Project 設定視窗。</span><span class="sxs-lookup"><span data-stu-id="ff0bd-145">In the Unity menu, select **Edit** > **Project Settings...** to open the Project Settings window.</span></span>

<span data-ttu-id="ff0bd-146">在 [專案設定] 視窗中，選取 [播放程式] > [發佈設定]，然後在 **套件名稱** 欄位中輸入適當的名稱，例如 _MRTKTutorials-GettingStarted_：</span><span class="sxs-lookup"><span data-stu-id="ff0bd-146">In the Project Settings window, select **Player** > **Publishing Settings**, then in the **Package name** field, enter a suitable name, for example, _MRTKTutorials-GettingStarted_:</span></span>

![Unity 發佈設定。](../images/mr-learning-base/base-02-section5-step2-2.png)

> [!NOTE]
> <span data-ttu-id="ff0bd-149">「套件名稱」是應用程式的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="ff0bd-149">The 'Package name' is the unique identifier for the app.</span></span> <span data-ttu-id="ff0bd-150">您應該在部署應用程式之前變更此識別碼，以避免覆寫先前安裝的應用程式。</span><span class="sxs-lookup"><span data-stu-id="ff0bd-150">You should change this identifier before deploying the app to avoid overwriting previously installed apps.</span></span>

> [!TIP]
> <span data-ttu-id="ff0bd-151">「產品名稱」是 HoloLens 開始功能表中顯示的名稱。</span><span class="sxs-lookup"><span data-stu-id="ff0bd-151">The 'Product Name' is the name displayed in the HoloLens Start menu.</span></span> <span data-ttu-id="ff0bd-152">若要在開發期間更容易找到應用程式，請在名稱前面加上底線，將其排序到頂端。</span><span class="sxs-lookup"><span data-stu-id="ff0bd-152">To make the app easier to locate during development, add an underscore in front of the name to sort it to the top.</span></span>

# <a name="unity-20192020--windows-xr-plugin"></a>[<span data-ttu-id="ff0bd-153">Unity 2019/2020 + Windows XR 外掛程式</span><span class="sxs-lookup"><span data-stu-id="ff0bd-153">Unity 2019/2020 + Windows XR Plugin</span></span>](#tab/winxr)

<span data-ttu-id="ff0bd-154">**MixedRealityFeatureTool** 開啟後，按一下 [**開始**] 以開始使用 Mixed Reality 功能工具。</span><span class="sxs-lookup"><span data-stu-id="ff0bd-154">Once **MixedRealityFeatureTool** is opened, click on **Start** to get started with Mixed Reality Feature Tool.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-2.png" width="650px" alt="MixedRealityFeatureTool main screen">

<span data-ttu-id="ff0bd-155">第一個步驟是使用 **省略號** 按鈕將「混合現實」功能工具指向您的 **Project 路徑**，按一下 Project 路徑旁的三個點省略號按鈕，然後流覽至您在瀏覽器中的專案資料夾，例如 _D:\MixedRealityLearning\MRTK 教學_ 課程。</span><span class="sxs-lookup"><span data-stu-id="ff0bd-155">The first step is to point the Mixed Reality Feature Tool to your **Project path** using the **ellipsis** button, click on the Three dots ellipsis button next to the Project path and browse to your project folder in the explorer for example _D:\MixedRealityLearning\MRTK Tutorials_.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-3.png" width="650px" alt="Adding Unity Path for MixedRealityFeatureTool">


<span data-ttu-id="ff0bd-156">當您找到專案的資料夾時，請按一下 [開啟] 按鈕以返回 [混合現實] 功能工具。</span><span class="sxs-lookup"><span data-stu-id="ff0bd-156">When you have located your project's folder, click the Open button to return to the Mixed Reality Feature Tool.</span></span> <span data-ttu-id="ff0bd-157">然後按一下 [ **探索功能**]。</span><span class="sxs-lookup"><span data-stu-id="ff0bd-157">Then click on **Discover Features**.</span></span>

> [!NOTE]
> <span data-ttu-id="ff0bd-158">流覽 Unity 專案資料夾時顯示的對話方塊會包含 ' _ ' 作為檔案名。</span><span class="sxs-lookup"><span data-stu-id="ff0bd-158">The dialog that's displayed when browsing for the Unity project folder contains '_' as the file name.</span></span> <span data-ttu-id="ff0bd-159">檔案名必須有一個值，才能選取該資料夾。</span><span class="sxs-lookup"><span data-stu-id="ff0bd-159">There must be a value for the file name to enable the folder to be selected.</span></span>

> [!Important]
> <span data-ttu-id="ff0bd-160">「混合現實」功能工具會執行驗證，以確保它已導向至 Unity 專案資料夾。</span><span class="sxs-lookup"><span data-stu-id="ff0bd-160">The Mixed Reality Feature Tool performs validation to ensure that it has been directed to a Unity project folder.</span></span> <span data-ttu-id="ff0bd-161">資料夾必須包含資產、封裝和 Project 設定資料夾。</span><span class="sxs-lookup"><span data-stu-id="ff0bd-161">The folder must contain Assets, Packages and Project Settings folders.</span></span>

<span data-ttu-id="ff0bd-162">功能會依類別目錄分組，讓您更容易找到這些專案，請按一下 [ **Mixed Reality 工具** 組] 下拉式清單，以尋找與混合現實工具組相關的套件。</span><span class="sxs-lookup"><span data-stu-id="ff0bd-162">Features are grouped by category to make things easier to find, click on **Mixed Reality Toolkit** dropdown to find packages relating to the Mixed Reality Toolkit.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-4.PNG" width="650px" alt="MixedRealityFeatureTool Discover Features">

<span data-ttu-id="ff0bd-163">核取 [ **混合現實工具組 Foundation**] 的方塊，然後按一下其旁邊的下拉式清單，選取 [ **MRTK 2.7.0**]，然後按一下 [ **取得功能** ] 按鈕以下載選取的套件。</span><span class="sxs-lookup"><span data-stu-id="ff0bd-163">Check the box for **Mixed Reality Toolkit Foundation**, and click on the dropdown next to it to select **MRTK 2.7.0**, then click on **Get features** button to download the selected packages.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-5.PNG" width="650px" alt="MixedRealityFeatureTool Open Mixed Reality">

<span data-ttu-id="ff0bd-164">接下來按一下 [ **驗證** ] 按鈕以驗證選取的封裝，您會看到 [偵測 **不到驗證問題** 的快顯視窗 **] 按一下 [確定]** 關閉快顯視窗，然後按一下 [匯 **入** ] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="ff0bd-164">Next click on the **Validate** button to validate the selected package, you will get a popup with message **No validation issues were detected** click on **OK** to close the popup and click on **Import** button.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-6.PNG" width="650px" alt="MixedRealityFeatureTool Select required package">


<span data-ttu-id="ff0bd-165">按一下 [ **核准** ] 按鈕，將 **Mixed Reality 工具** 組新增至專案。</span><span class="sxs-lookup"><span data-stu-id="ff0bd-165">Click on **Approve** Button to add the **Mixed Reality Toolkit** into the project.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-7.PNG" width="650px" alt="MixedRealityFeatureTool Validate package">


## <a name="configuring-the-unity-project"></a><span data-ttu-id="ff0bd-166">設定 Unity 專案</span><span class="sxs-lookup"><span data-stu-id="ff0bd-166">Configuring the Unity project</span></span>

<span data-ttu-id="ff0bd-167">Unity 完成上一節中提到的匯入封裝後，應該會出現 [MRTK 專案配置器] 視窗。</span><span class="sxs-lookup"><span data-stu-id="ff0bd-167">After Unity has finished importing the package from the previous section, the MRTK Project Configurator window should appear.</span></span> <span data-ttu-id="ff0bd-168">如果沒有，您可以藉由前往 **混合現實**  >  **工具** 組  >  **公用程式** 來  >  **設定 MRTK 的 Project**，以手動方式開啟它：</span><span class="sxs-lookup"><span data-stu-id="ff0bd-168">If it doesn't, you can manually open it by going to **Mixed Reality** > **Toolkit** > **Utilities** > **Configure Project for MRTK**:</span></span>

![開啟 MRTK 的配置器工具](../images/mr-learning-base/base-02-section5-step1-1xrsdk.PNG)

<span data-ttu-id="ff0bd-170">按一下 **內建 Unity 外掛程式 (非 OpenXR)** ，以啟用 XR 外掛程式管理，並將其所需的套件新增至您的專案。</span><span class="sxs-lookup"><span data-stu-id="ff0bd-170">Click on **Built-in Unity Plugin(non-OpenXR)** to Enable XR Plugin Management and add its required packages into your project.</span></span>

![ <span data-ttu-id="ff0bd-171">MRTK 配置器工具</span><span class="sxs-lookup"><span data-stu-id="ff0bd-171">MRTK configurator tool</span></span>](../images/mr-learning-base/base-02-section5-step1-2xrsdk.PNG)

> [!NOTE]
> <span data-ttu-id="ff0bd-172">上述螢幕擷取畫面是來自 Unity 2020，如果您使用 Unity 2019，請選取 **XR SDK/XR 管理**</span><span class="sxs-lookup"><span data-stu-id="ff0bd-172">The above screenshot is from Unity 2020, if you using Unity 2019 please select **XR SDK/XR Management**</span></span>

<span data-ttu-id="ff0bd-173">這會匯入 XR 外掛程式管理所需的 unity 套件，一旦完成，請按一下 [MRTK 專案] 設定檔中的 [**顯示設定**。</span><span class="sxs-lookup"><span data-stu-id="ff0bd-173">This will import required unity packages for XR Plugin Management, once done click on **Show Settings** in MRTK project Configurator.</span></span>

![播放機設定視窗](../images/mr-learning-base/base-02-section5-step1-3xrsdk.PNG)

<span data-ttu-id="ff0bd-175">這會開啟 **Project 設定] 視窗** 中，在 [ **XR 外掛程式管理**] 下的 [Project 設定] 視窗中，確定您是在 [**啟動時初始化 XR** ] 核取方塊，然後核取 [**通用 Windows 平臺**] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="ff0bd-175">This opens **Project Settings window**, In the Project Settings window under **XR Plug-in Management** Ensure that you are in Universal Windows Platform settings also Ensure **Initialize XR on Startup** is checked, and check **Windows Mixed Reality** checkbox.</span></span>

![[播放機設定] 視窗啟用混合現實-xrsdk](../images/mr-learning-base/base-02-section5-step1-4xrsdk.PNG)

<span data-ttu-id="ff0bd-177">Unity 完成匯入 Windows Mixed Reality SDK 後，應該會再次出現 [MRTK 專案配置器] 視窗。</span><span class="sxs-lookup"><span data-stu-id="ff0bd-177">After Unity has finished importing the Windows Mixed Reality SDK, the MRTK Project Configurator window should appear again.</span></span> <span data-ttu-id="ff0bd-178">如果沒有出現，請使用 Unity 功能表開啟。</span><span class="sxs-lookup"><span data-stu-id="ff0bd-178">If it doesn't, use the Unity menu to open it.</span></span>

<span data-ttu-id="ff0bd-179">在 [MRTK Project 設定] 視窗中，按一下 **[下一步**]，然後使用 [音訊空間定位器] 下拉式清單選取 **MS HRTF 空間定位器**，然後按一下 [套用 **] 按鈕以** 套用設定：</span><span class="sxs-lookup"><span data-stu-id="ff0bd-179">In the MRTK Project Configurator window, click on **next** then use the Audio spatializer dropdown to select the **MS HRTF Spatializer**, then click the **Apply** button to apply the setting:</span></span>

![MRTK 專案配置器-xrsdk](../images/mr-learning-base/base-02-section5-step1-5xrsdk.PNG)

> [!TIP]
> <span data-ttu-id="ff0bd-181">您可以選擇是否套用 MRTK 預設設定，但強烈建議您這麼做，因為這可協助您設定一些建議的 Unity 設定：</span><span class="sxs-lookup"><span data-stu-id="ff0bd-181">Applying the MRTK Default Settings is optional but strongly recommended as it will help configure some recommended Unity settings:</span></span>

> * <span data-ttu-id="ff0bd-182">設定單一階段執行個體化轉譯路徑：藉由在相同的繪製呼叫中為雙眼執行轉譯管線，來改善圖形效能。</span><span class="sxs-lookup"><span data-stu-id="ff0bd-182">Set Single Pass Instanced rendering path: Improves graphics performance by executing the render pipeline for both eyes in the same draw call.</span></span> <span data-ttu-id="ff0bd-183">若要深入了解本主題，您可以參閱 MRTK [效能](/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering)文件中的[單一階段執行個體化轉譯](/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering)一節。</span><span class="sxs-lookup"><span data-stu-id="ff0bd-183">To learn more about this topic, you can refer to the [Single-Pass Instanced rendering](/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering) section of MRTK's [Performance](/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering) documentation.</span></span>
> * <span data-ttu-id="ff0bd-184">設定預設空間感知層：建立名為「空間感知」的 Unity 圖層，並將 MRTK 設定為將此圖層用於空間感知網格。</span><span class="sxs-lookup"><span data-stu-id="ff0bd-184">Set default Spatial Awareness layer: Creates a Unity Layer named Spatial Awareness and configures MRTK to use this layer for the spatial awareness mesh.</span></span> <span data-ttu-id="ff0bd-185">若要深入了解 Unity 圖層，您可以參閱 Unity 的<a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">自訂您的工作區</a>文件。</span><span class="sxs-lookup"><span data-stu-id="ff0bd-185">To learn more about Unity Layers, you can refer to Unity's <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">Customizing Your Workspace</a> documentation.</span></span>

> [!TIP]
> <span data-ttu-id="ff0bd-186">您可以選擇是否設定 [音訊空間定位器] 屬性，但這麼做可以改善專案中的音訊體驗。</span><span class="sxs-lookup"><span data-stu-id="ff0bd-186">Setting the Audio spatializer property is optional but may improve the audio experience in your project.</span></span> <span data-ttu-id="ff0bd-187">如果您將此屬性設定為 [MS HRTF 空間定位器]，當 Unity 的 AudioSource.spatialize 屬性啟用時，便會使用此空間定位器外掛程式。</span><span class="sxs-lookup"><span data-stu-id="ff0bd-187">If you set it to MS HRTF Spatializer, this spatializer plugin will be used when Unity's AudioSource.spatialize property is enabled.</span></span> <span data-ttu-id="ff0bd-188">若要深入瞭解本主題，您可以參考  <a href="//windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank"> 空間音訊教學</a>課程。</span><span class="sxs-lookup"><span data-stu-id="ff0bd-188">To learn more about this topic, you can refer to the  <a href="//windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank"> Spatial audio tutorials</a>.</span></span>

<span data-ttu-id="ff0bd-189">按一下 [**下一步**]，然後按一下 [MRTK Project 設定] 視窗中的 [**完成**]，完成 XRSDK 的 Unity 專案設定。</span><span class="sxs-lookup"><span data-stu-id="ff0bd-189">Click on **Next** then click on **Done** in the MRTK Project Configurator window to finish the Unity project configuration for XRSDK.</span></span>

### <a name="configure-additional-project-settings"></a><span data-ttu-id="ff0bd-190">設定其他專案設定</span><span class="sxs-lookup"><span data-stu-id="ff0bd-190">Configure additional project settings</span></span>

<span data-ttu-id="ff0bd-191">在 Unity 功能表中，選取 [編輯] >  [專案設定...] 來開啟 [專案設定] 視窗：</span><span class="sxs-lookup"><span data-stu-id="ff0bd-191">In the Unity menu, select **Edit** > **Project Settings...** to open the Project Settings window:</span></span>

<span data-ttu-id="ff0bd-192">在 [Project 設定] 視窗中，選取 **[XR 外掛程式管理**  >  **Windows Mixed Reality**  >  **運行** 時間] 設定，然後使用 [**深度緩衝區格式**] 下拉式清單選取 **16 位深度**：</span><span class="sxs-lookup"><span data-stu-id="ff0bd-192">In the Project Settings window, select **XR Plug-in Management** > **Windows Mixed Reality** > **Runtime Settings**, then use the **Depth Buffer Format** dropdown to select **16-bit depth**:</span></span>

![Unity 啟用16深度](../images/mr-learning-base/base-02-section5-step2-1xrsdk.PNG)

> [!TIP]
> <span data-ttu-id="ff0bd-194">您可以選擇是否將 [深度格式] 減少為 16 位元，但這麼做可協助改善專案中的圖形效能。</span><span class="sxs-lookup"><span data-stu-id="ff0bd-194">Reducing the Depth Format to 16-bit is optional but my help improve graphics performance in your project.</span></span> <span data-ttu-id="ff0bd-195">若要深入了解本主題，您可以參閱 MRTK 效能文件中的<a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering" target="_blank">深度緩衝區共用 (HoloLens)</a> 一節。</span><span class="sxs-lookup"><span data-stu-id="ff0bd-195">To learn more about this topic, you can refer to the <a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering" target="_blank">Depth buffer sharing (HoloLens)</a> section of MRTK's Performance documentation.</span></span>

<span data-ttu-id="ff0bd-196">在 [專案設定] 視窗中，選取 [播放程式] > [發佈設定]，然後在 **套件名稱** 欄位中輸入適當的名稱，例如 _MRTKTutorials-GettingStarted_：</span><span class="sxs-lookup"><span data-stu-id="ff0bd-196">In the Project Settings window, select **Player** > **Publishing Settings**, then in the **Package name** field, enter a suitable name, for example, _MRTKTutorials-GettingStarted_:</span></span>

![Unity 發佈設定。](../images/mr-learning-base/base-02-section5-step2-2.png)

> [!NOTE]
> <span data-ttu-id="ff0bd-199">「套件名稱」是應用程式的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="ff0bd-199">The 'Package name' is the unique identifier for the app.</span></span> <span data-ttu-id="ff0bd-200">您應該在部署應用程式之前變更此識別碼，以避免覆寫先前安裝的應用程式。</span><span class="sxs-lookup"><span data-stu-id="ff0bd-200">You should change this identifier before deploying the app to avoid overwriting previously installed apps.</span></span>

> [!TIP]
> <span data-ttu-id="ff0bd-201">「產品名稱」是 HoloLens 開始功能表中顯示的名稱。</span><span class="sxs-lookup"><span data-stu-id="ff0bd-201">The 'Product Name' is the name displayed in the HoloLens Start menu.</span></span> <span data-ttu-id="ff0bd-202">若要在開發期間更容易找到應用程式，請在名稱前面加上底線，將其排序到頂端。</span><span class="sxs-lookup"><span data-stu-id="ff0bd-202">To make the app easier to locate during development, add an underscore in front of the name to sort it to the top.</span></span>

# <a name="legacy-wsa"></a>[<span data-ttu-id="ff0bd-203">舊版 WSA</span><span class="sxs-lookup"><span data-stu-id="ff0bd-203">Legacy WSA</span></span>](#tab/wsa)

<span data-ttu-id="ff0bd-204">**MixedRealityFeatureTool** 開啟後，按一下 [**開始**] 以開始使用 Mixed Reality 功能工具。</span><span class="sxs-lookup"><span data-stu-id="ff0bd-204">Once **MixedRealityFeatureTool** is opened, click on **Start** to get started with Mixed Reality Feature Tool.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-2.png" width="650px" alt="MixedRealityFeatureTool main screen">

<span data-ttu-id="ff0bd-205">第一個步驟是使用 **省略號** 按鈕將「混合現實」功能工具指向您的 **Project 路徑**，按一下 Project 路徑旁的三個點省略號按鈕，然後流覽至您在瀏覽器中的專案資料夾，例如 _D:\MixedRealityLearning\MRTK 教學_ 課程。</span><span class="sxs-lookup"><span data-stu-id="ff0bd-205">The first step is to point the Mixed Reality Feature Tool to your **Project path** using the **ellipsis** button, click on the Three dots ellipsis button next to the Project path and browse to your project folder in the explorer for example _D:\MixedRealityLearning\MRTK Tutorials_.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-3.png" width="650px" alt="Adding Unity Path for MixedRealityFeatureTool">

<span data-ttu-id="ff0bd-206">當您找到專案的資料夾時，請按一下 [開啟] 按鈕以返回 [混合現實] 功能工具。</span><span class="sxs-lookup"><span data-stu-id="ff0bd-206">When you have located your project's folder, click the Open button to return to the Mixed Reality Feature Tool.</span></span> <span data-ttu-id="ff0bd-207">然後按一下 [ **探索功能**]。</span><span class="sxs-lookup"><span data-stu-id="ff0bd-207">Then click on **Discover Features**.</span></span>

> [!NOTE]
> <span data-ttu-id="ff0bd-208">流覽 Unity 專案資料夾時顯示的對話方塊會包含 ' _ ' 作為檔案名。</span><span class="sxs-lookup"><span data-stu-id="ff0bd-208">The dialog that's displayed when browsing for the Unity project folder contains '_' as the file name.</span></span> <span data-ttu-id="ff0bd-209">檔案名必須有一個值，才能選取該資料夾。</span><span class="sxs-lookup"><span data-stu-id="ff0bd-209">There must be a value for the file name to enable the folder to be selected.</span></span>

> [!Important]
> <span data-ttu-id="ff0bd-210">「混合現實」功能工具會執行驗證，以確保它已導向至 Unity 專案資料夾。</span><span class="sxs-lookup"><span data-stu-id="ff0bd-210">The Mixed Reality Feature Tool performs validation to ensure that it has been directed to a Unity project folder.</span></span> <span data-ttu-id="ff0bd-211">資料夾必須包含資產、封裝和 Project 設定資料夾。</span><span class="sxs-lookup"><span data-stu-id="ff0bd-211">The folder must contain Assets, Packages and Project Settings folders.</span></span>

<span data-ttu-id="ff0bd-212">功能會依類別目錄分組，讓您更容易找到這些專案，請按一下 [ **Mixed Reality 工具** 組] 下拉式清單，以尋找與混合現實工具組相關的套件。</span><span class="sxs-lookup"><span data-stu-id="ff0bd-212">Features are grouped by category to make things easier to find, click on **Mixed Reality Toolkit** dropdown to find packages relating to the Mixed Reality Toolkit.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-4.PNG" width="650px" alt="MixedRealityFeatureTool Discover Features">

<span data-ttu-id="ff0bd-213">檢查 **Mixed Reality 工具組 Foundation**，然後按一下其旁邊的下拉式清單，選取 [ **MRTK 2.7.0**]，然後按一下 [ **取得功能** ] 按鈕以下載選取的套件。</span><span class="sxs-lookup"><span data-stu-id="ff0bd-213">check the **Mixed Reality Toolkit Foundation**, and click on the dropdown next to it to select **MRTK 2.7.0**, then click on **Get features** button to download the selected packages.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-5.PNG" width="650px" alt="MixedRealityFeatureTool Open Mixed Reality">

<span data-ttu-id="ff0bd-214">接下來按一下 [ **驗證** ] 按鈕以驗證選取的封裝，您會看到 [偵測 **不到驗證問題** 的快顯視窗 **] 按一下 [確定]** 關閉快顯視窗，然後按一下 [匯 **入** ] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="ff0bd-214">Next click on the **Validate** button to validate the selected package, you will get a popup with message **No validation issues were detected** click on **OK** to close the popup and click on **Import** button.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-6.PNG" width="650px" alt="MixedRealityFeatureTool Select required package">

<span data-ttu-id="ff0bd-215">按一下 [ **核准** ] 按鈕，將 **Mixed Reality 工具** 組新增至專案。</span><span class="sxs-lookup"><span data-stu-id="ff0bd-215">Click on **Approve** Button to add the **Mixed Reality Toolkit** into the project.</span></span>

<img src="../images/mr-learning-base/base-02-section4-step1-7.PNG" width="650px" alt="MixedRealityFeatureTool Validate package">


## <a name="configuring-the-unity-project"></a><span data-ttu-id="ff0bd-216">設定 Unity 專案</span><span class="sxs-lookup"><span data-stu-id="ff0bd-216">Configuring the Unity project</span></span>

<span data-ttu-id="ff0bd-217">Unity 完成上一節中提到的匯入封裝後，應該會出現 [MRTK 專案配置器] 視窗。</span><span class="sxs-lookup"><span data-stu-id="ff0bd-217">After Unity has finished importing the package from the previous section, the MRTK Project Configurator window should appear.</span></span> <span data-ttu-id="ff0bd-218">如果沒有，您可以藉由前往 **混合現實**  >  **工具** 組  >  **公用程式** 來  >  **設定 MRTK 的 Project**，以手動方式開啟它：</span><span class="sxs-lookup"><span data-stu-id="ff0bd-218">If it doesn't, you can manually open it by going to **Mixed Reality** > **Toolkit** > **Utilities** > **Configure Project for MRTK**:</span></span>

![Unity [設定 Unity 專案] 功能表路徑](../images/mr-learning-base/base-02-section5-step1-1.png)

<span data-ttu-id="ff0bd-220">按一下 **舊版 XR** 可啟用舊版 XR，並將其所需的套件新增至您的專案。</span><span class="sxs-lookup"><span data-stu-id="ff0bd-220">Click on **Legacy XR** to enable Legacy XR and to add its required packages  into your project.</span></span>

![s](../images/mr-learning-base/base-02-section5-step1-2.png)

<span data-ttu-id="ff0bd-222">按一下 [下一步] 按鈕，為舊版 XR 啟用 XR 管線設定。</span><span class="sxs-lookup"><span data-stu-id="ff0bd-222">Click on next button to enable XR pipeline settings for Legacy XR.</span></span>

![Unity MRTK 設定視窗](../images/mr-learning-base/base-02-section5-step1-3.PNG)

<span data-ttu-id="ff0bd-224">在 [MRTK Project 設定器] 視窗中，確定已核取所有選項，並且使用 [**音訊空間定位器**] 下拉式清單來選取 **MS HRTF 空間定位器**，然後 **按一下 [套用**] 按鈕以套用設定：</span><span class="sxs-lookup"><span data-stu-id="ff0bd-224">In the MRTK Project Configurator window, ensure all options are checked and also use the **Audio spatializer** dropdown to select the **MS HRTF Spatializer**, then click the **Apply** button to apply the setting:</span></span>

![MRTK 設定視窗](../images/mr-learning-base/base-02-section5-step1-4.PNG)

> [!TIP]
> <span data-ttu-id="ff0bd-226">您可以選擇是否套用 MRTK 預設設定，但強烈建議您這麼做，因為這可協助您設定一些建議的 Unity 設定：</span><span class="sxs-lookup"><span data-stu-id="ff0bd-226">Applying the MRTK Default Settings is optional but strongly recommended as it will help configure some recommended Unity settings:</span></span>

> * <span data-ttu-id="ff0bd-227">設定單一階段執行個體化轉譯路徑：藉由在相同的繪製呼叫中為雙眼執行轉譯管線，來改善圖形效能。</span><span class="sxs-lookup"><span data-stu-id="ff0bd-227">Set Single Pass Instanced rendering path: Improves graphics performance by executing the render pipeline for both eyes in the same draw call.</span></span> <span data-ttu-id="ff0bd-228">若要深入了解本主題，您可以參閱 MRTK [效能](/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering)文件中的[單一階段執行個體化轉譯](/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering)一節。</span><span class="sxs-lookup"><span data-stu-id="ff0bd-228">To learn more about this topic, you can refer to the [Single-Pass Instanced rendering](/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering) section of MRTK's [Performance](/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering) documentation.</span></span>
> * <span data-ttu-id="ff0bd-229">設定預設空間感知層：建立名為「空間感知」的 Unity 圖層，並將 MRTK 設定為將此圖層用於空間感知網格。</span><span class="sxs-lookup"><span data-stu-id="ff0bd-229">Set default Spatial Awareness layer: Creates a Unity Layer named Spatial Awareness and configures MRTK to use this layer for the spatial awareness mesh.</span></span> <span data-ttu-id="ff0bd-230">若要深入了解 Unity 圖層，您可以參閱 Unity 的<a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">自訂您的工作區</a>文件。</span><span class="sxs-lookup"><span data-stu-id="ff0bd-230">To learn more about Unity Layers, you can refer to Unity's <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">Customizing Your Workspace</a> documentation.</span></span>

> [!TIP]
> <span data-ttu-id="ff0bd-231">您可以選擇是否設定 [音訊空間定位器] 屬性，但這麼做可以改善專案中的音訊體驗。</span><span class="sxs-lookup"><span data-stu-id="ff0bd-231">Setting the Audio spatializer property is optional but may improve the audio experience in your project.</span></span> <span data-ttu-id="ff0bd-232">如果您將此屬性設定為 [MS HRTF 空間定位器]，當 Unity 的 AudioSource.spatialize 屬性啟用時，便會使用此空間定位器外掛程式。</span><span class="sxs-lookup"><span data-stu-id="ff0bd-232">If you set it to MS HRTF Spatializer, this spatializer plugin will be used when Unity's AudioSource.spatialize property is enabled.</span></span> <span data-ttu-id="ff0bd-233">若要深入瞭解本主題，您可以參考  <a href="//windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank"> 空間音訊教學</a>課程。</span><span class="sxs-lookup"><span data-stu-id="ff0bd-233">To learn more about this topic, you can refer to the  <a href="//windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank"> Spatial audio tutorials</a>.</span></span>

<span data-ttu-id="ff0bd-234">按一下 **[下一步**]，然後按一下 [MRTK Project 設定] 視窗中的 [**完成**] 按鈕，以完成舊版 XR 的 Unity 專案設定。</span><span class="sxs-lookup"><span data-stu-id="ff0bd-234">Click on **Next** then click on **Done** button in MRTK Project Configurator window to finish the Unity project configuration for Legacy XR.</span></span>

### <a name="configure-additional-project-settings"></a><span data-ttu-id="ff0bd-235">設定其他專案設定</span><span class="sxs-lookup"><span data-stu-id="ff0bd-235">Configure additional project settings</span></span>

<span data-ttu-id="ff0bd-236">在 Unity 功能表中，選取 [編輯] >  [專案設定...] 來開啟 [專案設定] 視窗：</span><span class="sxs-lookup"><span data-stu-id="ff0bd-236">In the Unity menu, select **Edit** > **Project Settings...** to open the Project Settings window:</span></span>

<span data-ttu-id="ff0bd-237">在 [專案設定] 視窗中，選取 [播放程式] > [XR 設定]，然後使用 **深度格式** 下拉式清單選取 **16 位元深度**：</span><span class="sxs-lookup"><span data-stu-id="ff0bd-237">In the Project Settings window, select **Player** > **XR Settings**, then use the **Depth Format** dropdown to select **16-bit depth**:</span></span>

![Unity 啟用16深度](../images/mr-learning-base/base-02-section5-step2-1.png)

> [!TIP]
> <span data-ttu-id="ff0bd-239">您可以選擇是否將 [深度格式] 減少為 16 位元，但這麼做可協助改善專案中的圖形效能。</span><span class="sxs-lookup"><span data-stu-id="ff0bd-239">Reducing the Depth Format to 16-bit is optional but my help improve graphics performance in your project.</span></span> <span data-ttu-id="ff0bd-240">若要深入了解本主題，您可以參閱 MRTK 效能文件中的<a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering" target="_blank">深度緩衝區共用 (HoloLens)</a> 一節。</span><span class="sxs-lookup"><span data-stu-id="ff0bd-240">To learn more about this topic, you can refer to the <a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering" target="_blank">Depth buffer sharing (HoloLens)</a> section of MRTK's Performance documentation.</span></span>

<span data-ttu-id="ff0bd-241">在 [專案設定] 視窗中，選取 [播放程式] > [發佈設定]，然後在 **套件名稱** 欄位中輸入適當的名稱，例如 _MRTKTutorials-GettingStarted_：</span><span class="sxs-lookup"><span data-stu-id="ff0bd-241">In the Project Settings window, select **Player** > **Publishing Settings**, then in the **Package name** field, enter a suitable name, for example, _MRTKTutorials-GettingStarted_:</span></span>

![Unity 發佈設定。](../images/mr-learning-base/base-02-section5-step2-2.png)

> [!NOTE]
> <span data-ttu-id="ff0bd-244">「套件名稱」是應用程式的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="ff0bd-244">The 'Package name' is the unique identifier for the app.</span></span> <span data-ttu-id="ff0bd-245">您應該在部署應用程式之前變更此識別碼，以避免覆寫先前安裝的應用程式。</span><span class="sxs-lookup"><span data-stu-id="ff0bd-245">You should change this identifier before deploying the app to avoid overwriting previously installed apps.</span></span>

> [!TIP]
> <span data-ttu-id="ff0bd-246">「產品名稱」是 HoloLens 開始功能表中顯示的名稱。</span><span class="sxs-lookup"><span data-stu-id="ff0bd-246">The 'Product Name' is the name displayed in the HoloLens Start menu.</span></span> <span data-ttu-id="ff0bd-247">若要在開發期間更容易找到應用程式，請在名稱前面加上底線，將其排序到頂端。</span><span class="sxs-lookup"><span data-stu-id="ff0bd-247">To make the app easier to locate during development, add an underscore in front of the name to sort it to the top.</span></span>
