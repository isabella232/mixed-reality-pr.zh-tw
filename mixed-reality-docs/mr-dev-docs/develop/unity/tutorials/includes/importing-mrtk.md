---
ms.openlocfilehash: 0c25f726c391c1485efab26828d2bfe4a6468f8b
ms.sourcegitcommit: bdf4babd13e021f41fb04cdb3611bb759bd77537
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2021
ms.locfileid: "112396995"
---
# <a name="unity-2020--openxr"></a>[<span data-ttu-id="4b890-101">Unity 2020 + OpenXR</span><span class="sxs-lookup"><span data-stu-id="4b890-101">Unity 2020 + OpenXR</span></span>](#tab/openxr)

<span data-ttu-id="4b890-102">**MixedRealityFeatureTool** 開啟後，若要存取預覽版本，請按一下 [**設定**]，然後在 [**功能**] 索引標籤底下啟用 [**顯示預覽版本**]，然後按一下 **[確定]** 儲存設定。</span><span class="sxs-lookup"><span data-stu-id="4b890-102">Once **MixedRealityFeatureTool** is opened, to access preview releases click on **Settings** and enable **Show preview releases** under **Feature** tab, then click on **ok** to save the settings.</span></span>

![MixedRealityFeatureTool 預覽](../images/mr-learning-base/base-02-section4-step1-2-preview.PNG)

<span data-ttu-id="4b890-104">接下來按一下 [ **開始** ]，開始使用 Mixed Reality 功能工具。</span><span class="sxs-lookup"><span data-stu-id="4b890-104">next click on **Start** to get started with Mixed Reality Feature Tool.</span></span>

![MixedRealityFeatureTool](../images/mr-learning-base/base-02-section4-step1-2.png)

<span data-ttu-id="4b890-106">第一個步驟是使用 **省略號** 按鈕將「混合現實」功能工具指向您的 **專案路徑**，按一下專案路徑旁的三個點省略號按鈕，然後在 explorer 中流覽至您的專案資料夾，例如 _D:\MixedRealityLearning\MRTK 教學_ 課程。</span><span class="sxs-lookup"><span data-stu-id="4b890-106">The first step is to point the Mixed Reality Feature Tool to your **Project path** using the **ellipsis** button, click on the Three dots ellipsis button next to the Project path and browse to your project folder in the explorer for example _D:\MixedRealityLearning\MRTK Tutorials_.</span></span>

![新增 MixedRealityFeatureTool 的 Unity 路徑](../images/mr-learning-base/base-02-section4-step1-3.png)

<span data-ttu-id="4b890-108">當您找到專案的資料夾時，請按一下 [開啟] 按鈕以返回 [混合現實] 功能工具。</span><span class="sxs-lookup"><span data-stu-id="4b890-108">When you have located your project's folder, click the Open button to return to the Mixed Reality Feature Tool.</span></span> <span data-ttu-id="4b890-109">然後按一下 [ **探索功能**]。</span><span class="sxs-lookup"><span data-stu-id="4b890-109">Then click on **Discover Features**.</span></span>

> [!NOTE]
> <span data-ttu-id="4b890-110">流覽 Unity 專案資料夾時顯示的對話方塊會包含 ' _ ' 作為檔案名。</span><span class="sxs-lookup"><span data-stu-id="4b890-110">The dialog that's displayed when browsing for the Unity project folder contains '_' as the file name.</span></span> <span data-ttu-id="4b890-111">檔案名必須有一個值，才能選取該資料夾。</span><span class="sxs-lookup"><span data-stu-id="4b890-111">There must be a value for the file name to enable the folder to be selected.</span></span>

> [!Important]
> <span data-ttu-id="4b890-112">「混合現實」功能工具會執行驗證，以確保它已導向至 Unity 專案資料夾。</span><span class="sxs-lookup"><span data-stu-id="4b890-112">The Mixed Reality Feature Tool performs validation to ensure that it has been directed to a Unity project folder.</span></span> <span data-ttu-id="4b890-113">此資料夾必須包含資產、封裝和專案設定資料夾。</span><span class="sxs-lookup"><span data-stu-id="4b890-113">The folder must contain Assets, Packages and Project Settings folders.</span></span>

<span data-ttu-id="4b890-114">功能會依類別目錄分組，讓您更容易尋找，請按一下 [ **Mixed Reality 工具** 組] 下拉式清單來尋找與混合現實工具組相關的套件，然後按一下 [ **平臺支援** ] 下拉式清單，以尋找與各種支援平臺相關的套件。</span><span class="sxs-lookup"><span data-stu-id="4b890-114">Features are grouped by category to make things easier to find, click on **Mixed Reality Toolkit** dropdown to find packages relating to the Mixed Reality Toolkit and click on **Platform Support** dropdown to find packages relating various supporting platforms.</span></span>

![MixedRealityFeatureTool 探索功能](../images/mr-learning-base/base-02-section4-step1-4-openxr.png)

<span data-ttu-id="4b890-116">檢查 **Mixed Reality 工具組 Foundation** ，然後按一下其旁邊的下拉式清單，選取 [ **MRTK 2.7.0**]，也請檢查 **mixed reality OpenXR 外掛程式** ，然後按一下其旁邊的下拉式清單，以選取最新可用的版本，然後按一下 [ **取得功能** ] 按鈕以下載選取的套件。</span><span class="sxs-lookup"><span data-stu-id="4b890-116">check the **Mixed Reality Toolkit Foundation** and click on the dropdown next to it to select **MRTK 2.7.0**, also check the **Mixed Reality OpenXR Plugin** and click on the dropdown next to it to select most recent version available, then click on **Get features** button to download the selected packages.</span></span>

![MixedRealityFeatureTool 開啟 MixedReality](../images/mr-learning-base/base-02-section4-step1-5-openxr.PNG)

<span data-ttu-id="4b890-118">接下來按一下 [ **驗證** ] 按鈕以驗證選取的封裝，您會看到 [偵測 **不到驗證問題** 的快顯視窗 **] 按一下 [確定]** 關閉快顯視窗，然後按一下 [匯 **入** ] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="4b890-118">Next click on the **Validate** button to validate the selected package, you will get a popup with message **No validation issues were detected** click on **OK** to close the popup and click on **Import** button.</span></span>

![MixedRealityFeatureTool 選取必要套件](../images/mr-learning-base/base-02-section4-step1-6-OpenXR.PNG)

<span data-ttu-id="4b890-120">按一下 [ **核准** ] 按鈕，將 **Mixed Reality 工具** 組新增至專案。</span><span class="sxs-lookup"><span data-stu-id="4b890-120">Click on **Approve** Button to add the **Mixed Reality Toolkit** into the project.</span></span>

![MixedRealityFeatureTool 驗證套件](../images/mr-learning-base/base-02-section4-step1-7-openxr.PNG)

## <a name="configuring-the-unity-project"></a><span data-ttu-id="4b890-122">設定 Unity 專案</span><span class="sxs-lookup"><span data-stu-id="4b890-122">Configuring the Unity project</span></span>

<span data-ttu-id="4b890-123">Unity 完成從上一節匯入封裝之後，會出現一則警告訊息，以重新開機 Unity 編輯器，以便後端新外掛程式系統，請按一下 **[是]** 。</span><span class="sxs-lookup"><span data-stu-id="4b890-123">After Unity has finished importing the package from the previous section, a warning message appears to restart the unity editor to enable to backends for new plugin system, click on **Yes**</span></span>

![Unity 重新開機選項](../images/mr-learning-base/base-02-section5-step1-1-openxr.PNG)

<span data-ttu-id="4b890-125">Unity 重新開機 MRTK 專案配置器視窗應該會出現。</span><span class="sxs-lookup"><span data-stu-id="4b890-125">Once the Unity restarts MRTK Project Configurator window should appear.</span></span> <span data-ttu-id="4b890-126">如果沒有，您可以透過下列方式手動開啟它： MRTK 的 **混合現實**  >  **工具** 組  >  **公用程式**  >  **設定專案**：</span><span class="sxs-lookup"><span data-stu-id="4b890-126">If it doesn't, you can manually open it by going to **Mixed Reality** > **Toolkit** > **Utilities** > **Configure Project for MRTK**:</span></span>

![開啟 MRTK 專案配置器視窗](../images/mr-learning-base/base-02-section5-step1-2-openxr.png)

<span data-ttu-id="4b890-128">按一下 **Unity OpenXR 外掛程式** ，以啟用 XR 外掛程式管理，並將其所需的套件新增至您的專案。</span><span class="sxs-lookup"><span data-stu-id="4b890-128">Click on **Unity OpenXR Plugin** to Enable XR Plugin Management and add its required packages into your project.</span></span>

![<span data-ttu-id="4b890-129">新增 Unity OpenXR 外掛程式</span><span class="sxs-lookup"><span data-stu-id="4b890-129">Add Unity OpenXR Plugin</span></span> ](../images/mr-learning-base/base-02-section5-step1-3-openxr.PNG)

<span data-ttu-id="4b890-130">這會匯入 XR 外掛程式管理所需的 unity 套件，一旦完成，請按一下 [MRTK 專案設定] 中的 [ **顯示 XR Plug-In 管理設定** ]。</span><span class="sxs-lookup"><span data-stu-id="4b890-130">This will import required unity packages for XR Plugin Management, once done click on **Show XR Plug-In Management Settings** in MRTK project Configurator.</span></span>

![<span data-ttu-id="4b890-131">顯示 XR Plug-In 管理設定</span><span class="sxs-lookup"><span data-stu-id="4b890-131">Show XR Plug-In Management Settings</span></span> ](../images/mr-learning-base/base-02-section5-step1-4-openxr.PNG)

<span data-ttu-id="4b890-132">這會開啟 [ **專案設定] 視窗**，</span><span class="sxs-lookup"><span data-stu-id="4b890-132">This opens **Project Settings window**,</span></span>

![啟用 Open XR](../images/mr-learning-base/base-02-section5-step1-5-openxr.PNG)

<span data-ttu-id="4b890-134">在 [ **XR 外掛程式管理** ] 下的 [專案設定] 視窗中，通用 Windows 平臺確定已選取 [ **啟動時初始化 XR** ]，然後核取 [ **開啟 XR** ] 核取方塊，然後 **Microsoft HoloLens [功能集** ] 核取方塊來啟用這些選項。</span><span class="sxs-lookup"><span data-stu-id="4b890-134">In the Project Settings window  under **XR Plug-in Management** Ensure that you are in Universal Windows Platform settings also Ensure **Initialize XR on Startup** is checked, then check **Open XR** checkbox and **Microsoft HoloLens feature set** checkbox to enable them.</span></span>

![專案設定視窗1](../images/mr-learning-base/base-02-section5-step1-6-openxr.PNG)

<span data-ttu-id="4b890-136">如果您在 **OpenXR 外掛程式** 旁邊看到紅色警告圖示，請按一下圖示並選取 [ **全部修正** ]，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="4b890-136">If you see a red warning icon next to **OpenXR Plugin**, click the icon and select **Fix all** before continuing.</span></span> <span data-ttu-id="4b890-137">Unity 編輯器可能需要自行重新開機，變更才會生效。</span><span class="sxs-lookup"><span data-stu-id="4b890-137">The Unity Editor may need to restart itself for the changes to take effect.</span></span>

![專案設定視窗2](../images/mr-learning-base/base-02-section5-step1-7-openxr.PNG)

<span data-ttu-id="4b890-139">解決所有問題之後，請關閉 [ **專案設定** ] 視窗。</span><span class="sxs-lookup"><span data-stu-id="4b890-139">Once all issues are fixed, close the **Project Settings** window.</span></span>

<span data-ttu-id="4b890-140">在功能表列中，流覽至 **Mixed Reality** >  **OpenXR**  >  **HoloLens 2 套用建議的專案設定**，以取得更佳的應用程式效能。</span><span class="sxs-lookup"><span data-stu-id="4b890-140">In the menu bar, navigate to **Mixed Reality**> **OpenXR** > **Apply recommended project settings for HoloLens 2** to get better app performance.</span></span>

![專案設定視窗3](../images/mr-learning-base/base-02-section5-step1-8-openxr.PNG)

<span data-ttu-id="4b890-142">使用 Unity 功能表開啟 [MRTK 專案設定]，在 [MRTK 專案設定] 視窗中，按 [ **下一步**]，然後按一下 [套用] **按鈕以** 套用設定：</span><span class="sxs-lookup"><span data-stu-id="4b890-142">Use the Unity menu to open MRTK Project Configurator, In the MRTK Project Configurator window, click on **next**, then click the **Apply** button to apply the settings:</span></span>

![專案設定視窗4](../images/mr-learning-base/base-02-section5-step1-9-openxr.png)

<span data-ttu-id="4b890-144">當您按一下 [套用] 之後，Unity 將會嘗試重新開機，輸入系統才會生效，請按一下 [套用 **] 以重新** 啟動 Unity 編輯器</span><span class="sxs-lookup"><span data-stu-id="4b890-144">Once you click on Apply, Unity will try to restart for the input system to take into effect, click on **Apply** to restart the Unity editor</span></span>

![專案設定視窗5](../images/mr-learning-base/base-02-section5-step1-10-openxr.PNG)

<span data-ttu-id="4b890-146">Unity 重新開機後，請從 unity 功能表開啟 MRTK 專案設定程式，然後按 [ **下一步** ]，然後按一下 **[完成] 以完成 OpenXR** 的 Unity 專案設定。</span><span class="sxs-lookup"><span data-stu-id="4b890-146">Once the Unity restarts open MRTK Project Configurator from the unity menu and Click on **Next** then click on **Done** finish the Unity project configuration for OpenXR.</span></span>

### <a name="configure-additional-project-settings"></a><span data-ttu-id="4b890-147">設定其他專案設定</span><span class="sxs-lookup"><span data-stu-id="4b890-147">Configure additional project settings</span></span>

<span data-ttu-id="4b890-148">在 Unity 功能表中，選取 [編輯] >  [專案設定...] 來開啟 [專案設定] 視窗：</span><span class="sxs-lookup"><span data-stu-id="4b890-148">In the Unity menu, select **Edit** > **Project Settings...** to open the Project Settings window:</span></span>

<span data-ttu-id="4b890-149">在 [專案設定] 視窗中，選取 [ **XR 外掛程式管理**  >  **OpenXR**]，然後使用 [**深度提交模式**] 下拉式清單選取 [**深度 16** 位]：</span><span class="sxs-lookup"><span data-stu-id="4b890-149">In the Project Settings window, select **XR Plug-in Management** > **OpenXR**, then use the **Depth Submission Mode** dropdown to select **Depth 16-bit**:</span></span>

![Unity 啟用16深度](../images/mr-learning-base/base-02-section5-step2-1-openxr.PNG)

> [!TIP]
> <span data-ttu-id="4b890-151">您可以選擇是否將 [深度格式] 減少為 16 位元，但這麼做可協助改善專案中的圖形效能。</span><span class="sxs-lookup"><span data-stu-id="4b890-151">Reducing the Depth Format to 16-bit is optional but my help improve graphics performance in your project.</span></span> <span data-ttu-id="4b890-152">若要深入了解本主題，您可以參閱 MRTK 效能文件中的<a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering" target="_blank">深度緩衝區共用 (HoloLens)</a> 一節。</span><span class="sxs-lookup"><span data-stu-id="4b890-152">To learn more about this topic, you can refer to the <a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering" target="_blank">Depth buffer sharing (HoloLens)</a> section of MRTK's Performance documentation.</span></span>

<span data-ttu-id="4b890-153">在 [專案設定] 視窗中，選取 [播放程式] > [發佈設定]，然後在 **套件名稱** 欄位中輸入適當的名稱，例如 _MRTKTutorials-GettingStarted_：</span><span class="sxs-lookup"><span data-stu-id="4b890-153">In the Project Settings window, select **Player** > **Publishing Settings**, then in the **Package name** field, enter a suitable name, for example, _MRTKTutorials-GettingStarted_:</span></span>

![Unity 發行設定。](../images/mr-learning-base/base-02-section5-step2-2.png)

> [!NOTE]
> <span data-ttu-id="4b890-156">「套件名稱」是應用程式的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="4b890-156">The 'Package name' is the unique identifier for the app.</span></span> <span data-ttu-id="4b890-157">您應該在部署應用程式之前變更此識別碼，以避免覆寫先前安裝的應用程式。</span><span class="sxs-lookup"><span data-stu-id="4b890-157">You should change this identifier before deploying the app to avoid overwriting previously installed apps.</span></span>

> [!TIP]
> <span data-ttu-id="4b890-158">「產品名稱」是 HoloLens 開始功能表中顯示的名稱。</span><span class="sxs-lookup"><span data-stu-id="4b890-158">The 'Product Name' is the name displayed in the HoloLens Start menu.</span></span> <span data-ttu-id="4b890-159">若要在開發期間更容易找到應用程式，請在名稱前面加上底線，將其排序到頂端。</span><span class="sxs-lookup"><span data-stu-id="4b890-159">To make the app easier to locate during development, add an underscore in front of the name to sort it to the top.</span></span>

# <a name="unity-20192020--windows-xr-plugin"></a>[<span data-ttu-id="4b890-160">Unity 2019/2020 + Windows XR 外掛程式</span><span class="sxs-lookup"><span data-stu-id="4b890-160">Unity 2019/2020 + Windows XR Plugin</span></span>](#tab/winxr)

<span data-ttu-id="4b890-161">**MixedRealityFeatureTool** 開啟後，若要存取預覽版本，請按一下 [**設定**]，然後在 [**功能**] 索引標籤底下啟用 [**顯示預覽版本**]，然後按一下 **[確定]** 儲存設定。</span><span class="sxs-lookup"><span data-stu-id="4b890-161">Once **MixedRealityFeatureTool** is opened, to access preview releases click on **Settings** and enable **Show preview releases** under **Feature** tab, then click on **ok** to save the settings.</span></span>

![MixedRealityFeatureTool for preview](../images/mr-learning-base/base-02-section4-step1-2-preview.PNG)

<span data-ttu-id="4b890-163">接著，按一下 [ **開始** ] 以開始使用 Mixed Reality 功能工具。</span><span class="sxs-lookup"><span data-stu-id="4b890-163">Next, click on **Start** to get started with Mixed Reality Feature Tool.</span></span>

![<span data-ttu-id="4b890-164">MixedRealityFeatureTool</span><span class="sxs-lookup"><span data-stu-id="4b890-164">MixedRealityFeatureTool</span></span> ](../images/mr-learning-base/base-02-section4-step1-2.png)

<span data-ttu-id="4b890-165">第一個步驟是使用 **省略號** 按鈕將「混合現實」功能工具指向您的 **專案路徑**，按一下專案路徑旁的三個點省略號按鈕，然後在 explorer 中流覽至您的專案資料夾，例如 _D:\MixedRealityLearning\MRTK 教學_ 課程。</span><span class="sxs-lookup"><span data-stu-id="4b890-165">The first step is to point the Mixed Reality Feature Tool to your **Project path** using the **ellipsis** button, click on the Three dots ellipsis button next to the Project path and browse to your project folder in the explorer for example _D:\MixedRealityLearning\MRTK Tutorials_.</span></span>

![新增 MixedRealityFeatureTool 的 Unity 路徑](../images/mr-learning-base/base-02-section4-step1-3.png)

<span data-ttu-id="4b890-167">當您找到專案的資料夾時，請按一下 [開啟] 按鈕以返回 [混合現實] 功能工具。</span><span class="sxs-lookup"><span data-stu-id="4b890-167">When you have located your project's folder, click the Open button to return to the Mixed Reality Feature Tool.</span></span> <span data-ttu-id="4b890-168">然後按一下 [ **探索功能**]。</span><span class="sxs-lookup"><span data-stu-id="4b890-168">Then click on **Discover Features**.</span></span>

> [!NOTE]
> <span data-ttu-id="4b890-169">流覽 Unity 專案資料夾時顯示的對話方塊會包含 ' _ ' 作為檔案名。</span><span class="sxs-lookup"><span data-stu-id="4b890-169">The dialog that's displayed when browsing for the Unity project folder contains '_' as the file name.</span></span> <span data-ttu-id="4b890-170">檔案名必須有一個值，才能選取該資料夾。</span><span class="sxs-lookup"><span data-stu-id="4b890-170">There must be a value for the file name to enable the folder to be selected.</span></span>

> [!Important]
> <span data-ttu-id="4b890-171">「混合現實」功能工具會執行驗證，以確保它已導向至 Unity 專案資料夾。</span><span class="sxs-lookup"><span data-stu-id="4b890-171">The Mixed Reality Feature Tool performs validation to ensure that it has been directed to a Unity project folder.</span></span> <span data-ttu-id="4b890-172">此資料夾必須包含資產、封裝和專案設定資料夾。</span><span class="sxs-lookup"><span data-stu-id="4b890-172">The folder must contain Assets, Packages and Project Settings folders.</span></span>

<span data-ttu-id="4b890-173">功能會依類別目錄分組，讓您更容易找到這些專案，請按一下 [ **Mixed Reality 工具** 組] 下拉式清單，以尋找與混合現實工具組相關的套件。</span><span class="sxs-lookup"><span data-stu-id="4b890-173">Features are grouped by category to make things easier to find, click on **Mixed Reality Toolkit** dropdown to find packages relating to the Mixed Reality Toolkit.</span></span>

![MixedRealityFeatureTool 探索功能](../images/mr-learning-base/base-02-section4-step1-4.PNG)

<span data-ttu-id="4b890-175">核取 [ **混合現實工具組 Foundation**] 的方塊，然後按一下其旁邊的下拉式清單，選取 [ **MRTK 2.7.0**]，然後按一下 [ **取得功能** ] 按鈕以下載選取的套件。</span><span class="sxs-lookup"><span data-stu-id="4b890-175">Check the box for **Mixed Reality Toolkit Foundation**, and click on the dropdown next to it to select **MRTK 2.7.0**, then click on **Get features** button to download the selected packages.</span></span>

![MixedRealityFeatureTool 開啟 MixedReality](../images/mr-learning-base/base-02-section4-step1-5.PNG)

<span data-ttu-id="4b890-177">接下來按一下 [ **驗證** ] 按鈕以驗證選取的封裝，您會看到 [偵測 **不到驗證問題** 的快顯視窗 **] 按一下 [確定]** 關閉快顯視窗，然後按一下 [匯 **入** ] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="4b890-177">Next click on the **Validate** button to validate the selected package, you will get a popup with message **No validation issues were detected** click on **OK** to close the popup and click on **Import** button.</span></span>

![MixedRealityFeatureTool 選取必要套件](../images/mr-learning-base/base-02-section4-step1-6.PNG)

<span data-ttu-id="4b890-179">按一下 [ **核准** ] 按鈕，將 **Mixed Reality 工具** 組新增至專案。</span><span class="sxs-lookup"><span data-stu-id="4b890-179">Click on **Approve** Button to add the **Mixed Reality Toolkit** into the project.</span></span>

![MixedRealityFeatureTool 驗證套件](../images/mr-learning-base/base-02-section4-step1-7.PNG)

## <a name="configuring-the-unity-project"></a><span data-ttu-id="4b890-181">設定 Unity 專案</span><span class="sxs-lookup"><span data-stu-id="4b890-181">Configuring the Unity project</span></span>

<span data-ttu-id="4b890-182">Unity 完成上一節中提到的匯入封裝後，應該會出現 [MRTK 專案配置器] 視窗。</span><span class="sxs-lookup"><span data-stu-id="4b890-182">After Unity has finished importing the package from the previous section, the MRTK Project Configurator window should appear.</span></span> <span data-ttu-id="4b890-183">如果沒有，您可以透過下列方式手動開啟它： MRTK 的 **混合現實**  >  **工具** 組  >  **公用程式**  >  **設定專案**：</span><span class="sxs-lookup"><span data-stu-id="4b890-183">If it doesn't, you can manually open it by going to **Mixed Reality** > **Toolkit** > **Utilities** > **Configure Project for MRTK**:</span></span>

![開啟 MRTK 的配置器工具](../images/mr-learning-base/base-02-section5-step1-1xrsdk.PNG)

<span data-ttu-id="4b890-185">按一下 **內建 Unity 外掛程式 (非 OpenXR)** ，以啟用 XR 外掛程式管理，並將其所需的套件新增至您的專案。</span><span class="sxs-lookup"><span data-stu-id="4b890-185">Click on **Built-in Unity Plugin(non-OpenXR)** to Enable XR Plugin Management and add its required packages into your project.</span></span>

![ <span data-ttu-id="4b890-186">MRTK 配置器工具</span><span class="sxs-lookup"><span data-stu-id="4b890-186">MRTK configurator tool</span></span>](../images/mr-learning-base/base-02-section5-step1-2xrsdk.PNG)

> [!NOTE]
> <span data-ttu-id="4b890-187">上述螢幕擷取畫面是來自 Unity 2020，如果您使用 Unity 2019，請選取 **XR SDK/XR 管理**</span><span class="sxs-lookup"><span data-stu-id="4b890-187">The above screenshot is from Unity 2020, if you using Unity 2019 please select **XR SDK/XR Management**</span></span>

<span data-ttu-id="4b890-188">這會匯入 XR 外掛程式管理所需的 unity 套件，然後按一下 [MRTK 專案設定] 中的 [ **顯示設定** ]。</span><span class="sxs-lookup"><span data-stu-id="4b890-188">This will import required unity packages for XR Plugin Management, once done click on **Show Settings** in MRTK project Configurator.</span></span>

![播放機設定視窗](../images/mr-learning-base/base-02-section5-step1-3xrsdk.PNG)

<span data-ttu-id="4b890-190">這會開啟 [ **專案設定] 視窗**，在 [ **XR 外掛程式管理** ] 下的 [專案設定] 視窗中，確定您處於通用 Windows 平臺設定也確認已核取 [ **啟動時 XR** ]，然後選取 [ **Windows Mixed Reality** ] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="4b890-190">This opens **Project Settings window**, In the Project Settings window under **XR Plug-in Management** Ensure that you are in Universal Windows Platform settings also Ensure **Initialize XR on Startup** is checked, and check **Windows Mixed Reality** checkbox.</span></span>

![[播放機設定] 視窗啟用混合現實-xrsdk](../images/mr-learning-base/base-02-section5-step1-4xrsdk.PNG)

<span data-ttu-id="4b890-192">Unity 完成匯入 Windows Mixed Reality SDK 後，應該會再次出現 [MRTK 專案配置器] 視窗。</span><span class="sxs-lookup"><span data-stu-id="4b890-192">After Unity has finished importing the Windows Mixed Reality SDK, the MRTK Project Configurator window should appear again.</span></span> <span data-ttu-id="4b890-193">如果沒有出現，請使用 Unity 功能表開啟。</span><span class="sxs-lookup"><span data-stu-id="4b890-193">If it doesn't, use the Unity menu to open it.</span></span>

<span data-ttu-id="4b890-194">在 [MRTK 專案設定] 視窗中，按 **[下一步** ]，然後使用 [音訊空間定位器] 下拉式清單來選取 **MS HRTF 空間定位器**，然後 **按一下 [套用** ] 按鈕以套用設定：</span><span class="sxs-lookup"><span data-stu-id="4b890-194">In the MRTK Project Configurator window, click on **next** then use the Audio spatializer dropdown to select the **MS HRTF Spatializer**, then click the **Apply** button to apply the setting:</span></span>

![MRTK 專案配置器-xrsdk](../images/mr-learning-base/base-02-section5-step1-5xrsdk.PNG)

> [!TIP]
> <span data-ttu-id="4b890-196">您可以選擇是否套用 MRTK 預設設定，但強烈建議您這麼做，因為這可協助您設定一些建議的 Unity 設定：</span><span class="sxs-lookup"><span data-stu-id="4b890-196">Applying the MRTK Default Settings is optional but strongly recommended as it will help configure some recommended Unity settings:</span></span>

> * <span data-ttu-id="4b890-197">設定單一階段執行個體化轉譯路徑：藉由在相同的繪製呼叫中為雙眼執行轉譯管線，來改善圖形效能。</span><span class="sxs-lookup"><span data-stu-id="4b890-197">Set Single Pass Instanced rendering path: Improves graphics performance by executing the render pipeline for both eyes in the same draw call.</span></span> <span data-ttu-id="4b890-198">若要深入了解本主題，您可以參閱 MRTK [效能](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering)文件中的[單一階段執行個體化轉譯](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering)一節。</span><span class="sxs-lookup"><span data-stu-id="4b890-198">To learn more about this topic, you can refer to the [Single-Pass Instanced rendering](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering) section of MRTK's [Performance](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering) documentation.</span></span>
> * <span data-ttu-id="4b890-199">設定預設空間感知層：建立名為「空間感知」的 Unity 圖層，並將 MRTK 設定為將此圖層用於空間感知網格。</span><span class="sxs-lookup"><span data-stu-id="4b890-199">Set default Spatial Awareness layer: Creates a Unity Layer named Spatial Awareness and configures MRTK to use this layer for the spatial awareness mesh.</span></span> <span data-ttu-id="4b890-200">若要深入了解 Unity 圖層，您可以參閱 Unity 的<a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">自訂您的工作區</a>文件。</span><span class="sxs-lookup"><span data-stu-id="4b890-200">To learn more about Unity Layers, you can refer to Unity's <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">Customizing Your Workspace</a> documentation.</span></span>

> [!TIP]
> <span data-ttu-id="4b890-201">您可以選擇是否設定 [音訊空間定位器] 屬性，但這麼做可以改善專案中的音訊體驗。</span><span class="sxs-lookup"><span data-stu-id="4b890-201">Setting the Audio spatializer property is optional but may improve the audio experience in your project.</span></span> <span data-ttu-id="4b890-202">如果您將此屬性設定為 [MS HRTF 空間定位器]，當 Unity 的 AudioSource.spatialize 屬性啟用時，便會使用此空間定位器外掛程式。</span><span class="sxs-lookup"><span data-stu-id="4b890-202">If you set it to MS HRTF Spatializer, this spatializer plugin will be used when Unity's AudioSource.spatialize property is enabled.</span></span> <span data-ttu-id="4b890-203">若要深入瞭解本主題，您可以參考  <a href="//windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank"> 空間音訊教學</a>課程。</span><span class="sxs-lookup"><span data-stu-id="4b890-203">To learn more about this topic, you can refer to the  <a href="//windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank"> Spatial audio tutorials</a>.</span></span>

<span data-ttu-id="4b890-204">按一下 [ **下一步** ]，然後按一下 [MRTK 專案設定] 視窗中的 [ **完成** ]，完成 XRSDK 的 Unity 專案設定。</span><span class="sxs-lookup"><span data-stu-id="4b890-204">Click on **Next** then click on **Done** in the MRTK Project Configurator window to finish the Unity project configuration for XRSDK.</span></span>

### <a name="configure-additional-project-settings"></a><span data-ttu-id="4b890-205">設定其他專案設定</span><span class="sxs-lookup"><span data-stu-id="4b890-205">Configure additional project settings</span></span>

<span data-ttu-id="4b890-206">在 Unity 功能表中，選取 [編輯] >  [專案設定...] 來開啟 [專案設定] 視窗：</span><span class="sxs-lookup"><span data-stu-id="4b890-206">In the Unity menu, select **Edit** > **Project Settings...** to open the Project Settings window:</span></span>

<span data-ttu-id="4b890-207">在 [專案設定] 視窗中，選取 **[XR 外掛程式管理**  >  **Windows Mixed Reality**  >  **執行時間設定**]，然後使用 [**深度緩衝區格式**] 下拉式清單選取 **16 位深度**：</span><span class="sxs-lookup"><span data-stu-id="4b890-207">In the Project Settings window, select **XR Plug-in Management** > **Windows Mixed Reality** > **Runtime Settings**, then use the **Depth Buffer Format** dropdown to select **16-bit depth**:</span></span>

![Unity 啟用16深度](../images/mr-learning-base/base-02-section5-step2-1xrsdk.PNG)

> [!TIP]
> <span data-ttu-id="4b890-209">您可以選擇是否將 [深度格式] 減少為 16 位元，但這麼做可協助改善專案中的圖形效能。</span><span class="sxs-lookup"><span data-stu-id="4b890-209">Reducing the Depth Format to 16-bit is optional but my help improve graphics performance in your project.</span></span> <span data-ttu-id="4b890-210">若要深入了解本主題，您可以參閱 MRTK 效能文件中的<a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering" target="_blank">深度緩衝區共用 (HoloLens)</a> 一節。</span><span class="sxs-lookup"><span data-stu-id="4b890-210">To learn more about this topic, you can refer to the <a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering" target="_blank">Depth buffer sharing (HoloLens)</a> section of MRTK's Performance documentation.</span></span>

<span data-ttu-id="4b890-211">在 [專案設定] 視窗中，選取 [播放程式] > [發佈設定]，然後在 **套件名稱** 欄位中輸入適當的名稱，例如 _MRTKTutorials-GettingStarted_：</span><span class="sxs-lookup"><span data-stu-id="4b890-211">In the Project Settings window, select **Player** > **Publishing Settings**, then in the **Package name** field, enter a suitable name, for example, _MRTKTutorials-GettingStarted_:</span></span>

![Unity 發行設定。](../images/mr-learning-base/base-02-section5-step2-2.png)

> [!NOTE]
> <span data-ttu-id="4b890-214">「套件名稱」是應用程式的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="4b890-214">The 'Package name' is the unique identifier for the app.</span></span> <span data-ttu-id="4b890-215">您應該在部署應用程式之前變更此識別碼，以避免覆寫先前安裝的應用程式。</span><span class="sxs-lookup"><span data-stu-id="4b890-215">You should change this identifier before deploying the app to avoid overwriting previously installed apps.</span></span>

> [!TIP]
> <span data-ttu-id="4b890-216">「產品名稱」是 HoloLens 開始功能表中顯示的名稱。</span><span class="sxs-lookup"><span data-stu-id="4b890-216">The 'Product Name' is the name displayed in the HoloLens Start menu.</span></span> <span data-ttu-id="4b890-217">若要在開發期間更容易找到應用程式，請在名稱前面加上底線，將其排序到頂端。</span><span class="sxs-lookup"><span data-stu-id="4b890-217">To make the app easier to locate during development, add an underscore in front of the name to sort it to the top.</span></span>

# <a name="legacy-wsa"></a>[<span data-ttu-id="4b890-218">舊版 WSA</span><span class="sxs-lookup"><span data-stu-id="4b890-218">Legacy WSA</span></span>](#tab/wsa)

<span data-ttu-id="4b890-219">**MixedRealityFeatureTool** 開啟後，若要存取預覽版本，請按一下 [**設定**]，然後在 [**功能**] 索引標籤底下啟用 [**顯示預覽版本**]，然後按一下 **[確定]** 儲存設定。</span><span class="sxs-lookup"><span data-stu-id="4b890-219">Once **MixedRealityFeatureTool** is opened, to access preview releases click on **Settings** and enable **Show preview releases** under **Feature** tab, then click on **ok** to save the settings.</span></span>

![MixedRealityFeatureTool 預覽](../images/mr-learning-base/base-02-section4-step1-2-preview.PNG)

<span data-ttu-id="4b890-221">接下來按一下 [ **開始** ]，開始使用 Mixed Reality 功能工具。</span><span class="sxs-lookup"><span data-stu-id="4b890-221">next click on **Start** to get started with Mixed Reality Feature Tool.</span></span>

![MixedRealityFeatureTool](../images/mr-learning-base/base-02-section4-step1-2.png)

<span data-ttu-id="4b890-223">第一個步驟是使用 **省略號** 按鈕將「混合現實」功能工具指向您的 **專案路徑**，按一下專案路徑旁的三個點省略號按鈕，然後在 explorer 中流覽至您的專案資料夾，例如 _D:\MixedRealityLearning\MRTK 教學_ 課程。</span><span class="sxs-lookup"><span data-stu-id="4b890-223">The first step is to point the Mixed Reality Feature Tool to your **Project path** using the **ellipsis** button, click on the Three dots ellipsis button next to the Project path and browse to your project folder in the explorer for example _D:\MixedRealityLearning\MRTK Tutorials_.</span></span>

![新增 MixedRealityFeatureTool 的 Unity 路徑](../images/mr-learning-base/base-02-section4-step1-3.png)

<span data-ttu-id="4b890-225">當您找到專案的資料夾時，請按一下 [開啟] 按鈕以返回 [混合現實] 功能工具。</span><span class="sxs-lookup"><span data-stu-id="4b890-225">When you have located your project's folder, click the Open button to return to the Mixed Reality Feature Tool.</span></span> <span data-ttu-id="4b890-226">然後按一下 [ **探索功能**]。</span><span class="sxs-lookup"><span data-stu-id="4b890-226">Then click on **Discover Features**.</span></span>

> [!NOTE]
> <span data-ttu-id="4b890-227">流覽 Unity 專案資料夾時顯示的對話方塊會包含 ' _ ' 作為檔案名。</span><span class="sxs-lookup"><span data-stu-id="4b890-227">The dialog that's displayed when browsing for the Unity project folder contains '_' as the file name.</span></span> <span data-ttu-id="4b890-228">檔案名必須有一個值，才能選取該資料夾。</span><span class="sxs-lookup"><span data-stu-id="4b890-228">There must be a value for the file name to enable the folder to be selected.</span></span>

> [!Important]
> <span data-ttu-id="4b890-229">「混合現實」功能工具會執行驗證，以確保它已導向至 Unity 專案資料夾。</span><span class="sxs-lookup"><span data-stu-id="4b890-229">The Mixed Reality Feature Tool performs validation to ensure that it has been directed to a Unity project folder.</span></span> <span data-ttu-id="4b890-230">此資料夾必須包含資產、封裝和專案設定資料夾。</span><span class="sxs-lookup"><span data-stu-id="4b890-230">The folder must contain Assets, Packages and Project Settings folders.</span></span>

<span data-ttu-id="4b890-231">功能會依類別目錄分組，讓您更容易找到這些專案，請按一下 [ **Mixed Reality 工具** 組] 下拉式清單，以尋找與混合現實工具組相關的套件。</span><span class="sxs-lookup"><span data-stu-id="4b890-231">Features are grouped by category to make things easier to find, click on **Mixed Reality Toolkit** dropdown to find packages relating to the Mixed Reality Toolkit.</span></span>

![MixedRealityFeatureTool 探索功能](../images/mr-learning-base/base-02-section4-step1-4.PNG)

<span data-ttu-id="4b890-233">檢查 **Mixed Reality 工具組 Foundation**，然後按一下其旁邊的下拉式清單，選取 [ **MRTK 2.7.0**]，然後按一下 [ **取得功能** ] 按鈕以下載選取的套件。</span><span class="sxs-lookup"><span data-stu-id="4b890-233">check the **Mixed Reality Toolkit Foundation**, and click on the dropdown next to it to select **MRTK 2.7.0**, then click on **Get features** button to download the selected packages.</span></span>

![MixedRealityFeatureTool 開啟 MixedReality](../images/mr-learning-base/base-02-section4-step1-5.PNG)

<span data-ttu-id="4b890-235">接下來按一下 [ **驗證** ] 按鈕以驗證選取的封裝，您會看到 [偵測 **不到驗證問題** 的快顯視窗 **] 按一下 [確定]** 關閉快顯視窗，然後按一下 [匯 **入** ] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="4b890-235">Next click on the **Validate** button to validate the selected package, you will get a popup with message **No validation issues were detected** click on **OK** to close the popup and click on **Import** button.</span></span>

![MixedRealityFeatureTool 選取必要套件](../images/mr-learning-base/base-02-section4-step1-6.PNG)

<span data-ttu-id="4b890-237">按一下 [ **核准** ] 按鈕，將 **Mixed Reality 工具** 組新增至專案。</span><span class="sxs-lookup"><span data-stu-id="4b890-237">Click on **Approve** Button to add the **Mixed Reality Toolkit** into the project.</span></span>

![MixedRealityFeatureTool 驗證套件](../images/mr-learning-base/base-02-section4-step1-7.PNG)

## <a name="configuring-the-unity-project"></a><span data-ttu-id="4b890-239">設定 Unity 專案</span><span class="sxs-lookup"><span data-stu-id="4b890-239">Configuring the Unity project</span></span>

<span data-ttu-id="4b890-240">Unity 完成上一節中提到的匯入封裝後，應該會出現 [MRTK 專案配置器] 視窗。</span><span class="sxs-lookup"><span data-stu-id="4b890-240">After Unity has finished importing the package from the previous section, the MRTK Project Configurator window should appear.</span></span> <span data-ttu-id="4b890-241">如果沒有，您可以透過下列方式手動開啟它： MRTK 的 **混合現實**  >  **工具** 組  >  **公用程式**  >  **設定專案**：</span><span class="sxs-lookup"><span data-stu-id="4b890-241">If it doesn't, you can manually open it by going to **Mixed Reality** > **Toolkit** > **Utilities** > **Configure Project for MRTK**:</span></span>

![Unity [設定 Unity 專案] 功能表路徑](../images/mr-learning-base/base-02-section5-step1-1.png)

<span data-ttu-id="4b890-243">按一下 **舊版 XR** 可啟用舊版 XR，並將其所需的套件新增至您的專案。</span><span class="sxs-lookup"><span data-stu-id="4b890-243">Click on **Legacy XR** to enable Legacy XR and to add its required packages  into your project.</span></span>

![s](../images/mr-learning-base/base-02-section5-step1-2.png)

<span data-ttu-id="4b890-245">按一下 [下一步] 按鈕，為舊版 XR 啟用 XR 管線設定。</span><span class="sxs-lookup"><span data-stu-id="4b890-245">Click on next button to enable XR pipeline settings for Legacy XR.</span></span>

![Unity MRTK 設定視窗](../images/mr-learning-base/base-02-section5-step1-3.PNG)

<span data-ttu-id="4b890-247">在 [MRTK 專案設定器] 視窗中，確定已核取所有選項，並且使用 [ **音訊空間定位器** ] 下拉式清單來選取 **MS HRTF 空間定位器**，然後 **按一下 [套用** ] 按鈕以套用設定：</span><span class="sxs-lookup"><span data-stu-id="4b890-247">In the MRTK Project Configurator window, ensure all options are checked and also use the **Audio spatializer** dropdown to select the **MS HRTF Spatializer**, then click the **Apply** button to apply the setting:</span></span>

![MRTK 設定視窗](../images/mr-learning-base/base-02-section5-step1-4.PNG)

> [!TIP]
> <span data-ttu-id="4b890-249">您可以選擇是否套用 MRTK 預設設定，但強烈建議您這麼做，因為這可協助您設定一些建議的 Unity 設定：</span><span class="sxs-lookup"><span data-stu-id="4b890-249">Applying the MRTK Default Settings is optional but strongly recommended as it will help configure some recommended Unity settings:</span></span>

> * <span data-ttu-id="4b890-250">設定單一階段執行個體化轉譯路徑：藉由在相同的繪製呼叫中為雙眼執行轉譯管線，來改善圖形效能。</span><span class="sxs-lookup"><span data-stu-id="4b890-250">Set Single Pass Instanced rendering path: Improves graphics performance by executing the render pipeline for both eyes in the same draw call.</span></span> <span data-ttu-id="4b890-251">若要深入了解本主題，您可以參閱 MRTK [效能](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering)文件中的[單一階段執行個體化轉譯](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering)一節。</span><span class="sxs-lookup"><span data-stu-id="4b890-251">To learn more about this topic, you can refer to the [Single-Pass Instanced rendering](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering) section of MRTK's [Performance](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering) documentation.</span></span>
> * <span data-ttu-id="4b890-252">設定預設空間感知層：建立名為「空間感知」的 Unity 圖層，並將 MRTK 設定為將此圖層用於空間感知網格。</span><span class="sxs-lookup"><span data-stu-id="4b890-252">Set default Spatial Awareness layer: Creates a Unity Layer named Spatial Awareness and configures MRTK to use this layer for the spatial awareness mesh.</span></span> <span data-ttu-id="4b890-253">若要深入了解 Unity 圖層，您可以參閱 Unity 的<a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">自訂您的工作區</a>文件。</span><span class="sxs-lookup"><span data-stu-id="4b890-253">To learn more about Unity Layers, you can refer to Unity's <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">Customizing Your Workspace</a> documentation.</span></span>

> [!TIP]
> <span data-ttu-id="4b890-254">您可以選擇是否設定 [音訊空間定位器] 屬性，但這麼做可以改善專案中的音訊體驗。</span><span class="sxs-lookup"><span data-stu-id="4b890-254">Setting the Audio spatializer property is optional but may improve the audio experience in your project.</span></span> <span data-ttu-id="4b890-255">如果您將此屬性設定為 [MS HRTF 空間定位器]，當 Unity 的 AudioSource.spatialize 屬性啟用時，便會使用此空間定位器外掛程式。</span><span class="sxs-lookup"><span data-stu-id="4b890-255">If you set it to MS HRTF Spatializer, this spatializer plugin will be used when Unity's AudioSource.spatialize property is enabled.</span></span> <span data-ttu-id="4b890-256">若要深入瞭解本主題，您可以參考  <a href="//windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank"> 空間音訊教學</a>課程。</span><span class="sxs-lookup"><span data-stu-id="4b890-256">To learn more about this topic, you can refer to the  <a href="//windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank"> Spatial audio tutorials</a>.</span></span>

<span data-ttu-id="4b890-257">按一下 **[下一步** ]，然後按一下 [MRTK 專案設定] 視窗中的 [**完成** ] 按鈕，完成舊版 XR 的 Unity 專案設定。</span><span class="sxs-lookup"><span data-stu-id="4b890-257">Click on **Next** then click on **Done** button in MRTK Project Configurator window to finish the Unity project configuration for Legacy XR.</span></span>

### <a name="configure-additional-project-settings"></a><span data-ttu-id="4b890-258">設定其他專案設定</span><span class="sxs-lookup"><span data-stu-id="4b890-258">Configure additional project settings</span></span>

<span data-ttu-id="4b890-259">在 Unity 功能表中，選取 [編輯] >  [專案設定...] 來開啟 [專案設定] 視窗：</span><span class="sxs-lookup"><span data-stu-id="4b890-259">In the Unity menu, select **Edit** > **Project Settings...** to open the Project Settings window:</span></span>

<span data-ttu-id="4b890-260">在 [專案設定] 視窗中，選取 [播放程式] > [XR 設定]，然後使用 **深度格式** 下拉式清單選取 **16 位元深度**：</span><span class="sxs-lookup"><span data-stu-id="4b890-260">In the Project Settings window, select **Player** > **XR Settings**, then use the **Depth Format** dropdown to select **16-bit depth**:</span></span>

![Unity 啟用16深度](../images/mr-learning-base/base-02-section5-step2-1.png)

> [!TIP]
> <span data-ttu-id="4b890-262">您可以選擇是否將 [深度格式] 減少為 16 位元，但這麼做可協助改善專案中的圖形效能。</span><span class="sxs-lookup"><span data-stu-id="4b890-262">Reducing the Depth Format to 16-bit is optional but my help improve graphics performance in your project.</span></span> <span data-ttu-id="4b890-263">若要深入了解本主題，您可以參閱 MRTK 效能文件中的<a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering" target="_blank">深度緩衝區共用 (HoloLens)</a> 一節。</span><span class="sxs-lookup"><span data-stu-id="4b890-263">To learn more about this topic, you can refer to the <a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering" target="_blank">Depth buffer sharing (HoloLens)</a> section of MRTK's Performance documentation.</span></span>

<span data-ttu-id="4b890-264">在 [專案設定] 視窗中，選取 [播放程式] > [發佈設定]，然後在 **套件名稱** 欄位中輸入適當的名稱，例如 _MRTKTutorials-GettingStarted_：</span><span class="sxs-lookup"><span data-stu-id="4b890-264">In the Project Settings window, select **Player** > **Publishing Settings**, then in the **Package name** field, enter a suitable name, for example, _MRTKTutorials-GettingStarted_:</span></span>

![Unity 發行設定。](../images/mr-learning-base/base-02-section5-step2-2.png)

> [!NOTE]
> <span data-ttu-id="4b890-267">「套件名稱」是應用程式的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="4b890-267">The 'Package name' is the unique identifier for the app.</span></span> <span data-ttu-id="4b890-268">您應該在部署應用程式之前變更此識別碼，以避免覆寫先前安裝的應用程式。</span><span class="sxs-lookup"><span data-stu-id="4b890-268">You should change this identifier before deploying the app to avoid overwriting previously installed apps.</span></span>

> [!TIP]
> <span data-ttu-id="4b890-269">「產品名稱」是 HoloLens 開始功能表中顯示的名稱。</span><span class="sxs-lookup"><span data-stu-id="4b890-269">The 'Product Name' is the name displayed in the HoloLens Start menu.</span></span> <span data-ttu-id="4b890-270">若要在開發期間更容易找到應用程式，請在名稱前面加上底線，將其排序到頂端。</span><span class="sxs-lookup"><span data-stu-id="4b890-270">To make the app easier to locate during development, add an underscore in front of the name to sort it to the top.</span></span>
