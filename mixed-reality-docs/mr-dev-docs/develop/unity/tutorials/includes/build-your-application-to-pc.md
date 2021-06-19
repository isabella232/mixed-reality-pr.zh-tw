---
ms.openlocfilehash: be4a3243bc00f29f992957de0dfa29416c13284d
ms.sourcegitcommit: bdf4babd13e021f41fb04cdb3611bb759bd77537
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2021
ms.locfileid: "112392534"
---
# <a name="unity-2020--openxr"></a>[<span data-ttu-id="63be1-101">Unity 2020 + OpenXR</span><span class="sxs-lookup"><span data-stu-id="63be1-101">Unity 2020 + OpenXR</span></span>](#tab/openxr)

### <a name="1-switching-build-platform"></a><span data-ttu-id="63be1-102">1. 切換組建平臺</span><span class="sxs-lookup"><span data-stu-id="63be1-102">1. Switching Build Platform</span></span>

<span data-ttu-id="63be1-103">在 Unity 功能表中，選取 [檔案] > [建置設定] 來開啟 [建置設定] 視窗。</span><span class="sxs-lookup"><span data-stu-id="63be1-103">In the Unity menu, select File > Build Settings to open the Build Settings window.</span></span>

<span data-ttu-id="63be1-104">在 [組建設定] 視窗中，選取 [ **PC、Mac & Linux 獨立** 平臺]，然後按一下 [ **切換平臺** ] 按鈕以變更組建平臺：</span><span class="sxs-lookup"><span data-stu-id="63be1-104">In the Build Settings window, select **PC, Mac & Linux Standalone** Platform and click the **Switch Platform** button to change the Build Platform:</span></span>

![切換組建平臺](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-1.PNG)

<span data-ttu-id="63be1-106">當 Unity 完成切換平臺時，請按一下 x 圖示以關閉 [組建設定] 視窗。</span><span class="sxs-lookup"><span data-stu-id="63be1-106">When Unity has finished switching the platform, click the x icon to close the Build Settings window.</span></span>

### <a name="2-set-the-project-settings"></a><span data-ttu-id="63be1-107">2. 設定專案設定</span><span class="sxs-lookup"><span data-stu-id="63be1-107">2. Set the project settings</span></span>

<span data-ttu-id="63be1-108">在 Unity 功能表中，選取 [**編輯**  >  **專案設定**  >  **XR 外掛程式管理**]，確定您位於 [Windows 獨立] 索引標籤，然後核取 [ **OpenXR** ] 和 [ **Windows Mixed Reality 功能集**] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="63be1-108">In the Unity menu, select **Edit** > **Project Settings** > **XR Plug-in Management** ensure that you are in Windows Standalone tab and check the **OpenXR** and **Windows Mixed Reality feature set** checkbox.</span></span>

![啟用 OpenXR 和 Windows Mixed Reality 功能集](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-2.PNG)

<span data-ttu-id="63be1-110">在 [專案設定] 視窗中，選取 [ **OpenXR** ] 並確認您處於 [Windows 獨立] 索引標籤，並將 **深度提交模式** 從 [無] 變更為 [ **深度16位**]。</span><span class="sxs-lookup"><span data-stu-id="63be1-110">In Project Settings window, select **OpenXR** and ensure that you are in Windows Standalone tab and change the **Depth submission mode** from None to **Depth 16 Bit**.</span></span>

<span data-ttu-id="63be1-111">在 [互動設定檔] 索引標籤中，按一下 + 符號，以新增 **眼睛的眼睛互動設定檔** 和 **Microsoft 手互動設定檔** 。</span><span class="sxs-lookup"><span data-stu-id="63be1-111">In interaction profiles tab add **Eye Gaze Interaction Profile** and **Microsoft Hand Interaction Profile** by clicking on the + symbol.</span></span>

![新增眼睛互動設定檔和 Microsoft 手互動設定檔](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-3.PNG)

<span data-ttu-id="63be1-113">在 [**開啟 XR 功能群組**  >  **所有功能**] 下 > 核取 [全像 **應用程式遠端處理**] 核取方塊</span><span class="sxs-lookup"><span data-stu-id="63be1-113">Under **Open XR feature groups** > **All features** > check the **Holographic App Remoting** checkbox.</span></span>

![啟用全像應用程式遠端處理](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-4.PNG)

<span data-ttu-id="63be1-115">接下來，選取 [ **Windows Mixed Reality** ] 核取方塊，然後在 [Windows Mixed Reality 群組] 下，選取 [全像]**應用程式遠端**</span><span class="sxs-lookup"><span data-stu-id="63be1-115">next select the **Windows Mixed Reality**  check box and under Windows Mixed Reality group select the  **Holographic App Remoting** checkbox.</span></span>

![啟用 Windows Mixed Reality 全息版應用程式遠端處理](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-5.PNG)

### <a name="3-build-the-unity-project"></a><span data-ttu-id="63be1-117">3. 建立 Unity 專案</span><span class="sxs-lookup"><span data-stu-id="63be1-117">3. Build the Unity Project</span></span>

<span data-ttu-id="63be1-118">在 Unity 功能表中，選取 [檔案] > [建置設定] 來開啟 [建置設定] 視窗。</span><span class="sxs-lookup"><span data-stu-id="63be1-118">In the Unity menu, select File > Build Settings to open the Build Settings window.</span></span>

<span data-ttu-id="63be1-119">在 [組建設定] 視窗中，按一下 [**新增開啟的場景** _] 按鈕，將您目前的場景新增至幕後。</span><span class="sxs-lookup"><span data-stu-id="63be1-119">In the Build Settings window, click the \***Add Open Scenes** _ button to add your current scene to the Scenes.</span></span> <span data-ttu-id="63be1-120">在 [組建] 清單中，按一下 [_ *組建*] 按鈕：</span><span class="sxs-lookup"><span data-stu-id="63be1-120">In the Build list, then click the _ *Build*\* button:</span></span>

![已新增場景的 Unity [建置設定] 視窗](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-6.PNG)

<span data-ttu-id="63be1-122">選擇適當的位置來儲存您的組建，例如 Documents\MixedRealityLearning。</span><span class="sxs-lookup"><span data-stu-id="63be1-122">choose a suitable location to store your build, for example, Documents\MixedRealityLearning.</span></span> <span data-ttu-id="63be1-123">建立新的資料夾，並為其指定適當的名稱，例如 PCHolographicRemoting。</span><span class="sxs-lookup"><span data-stu-id="63be1-123">Create a new folder and give it a suitable name, for example, PCHolographicRemoting.</span></span> <span data-ttu-id="63be1-124">然後按一下 [選取資料夾] 按鈕來啟動建置程序：</span><span class="sxs-lookup"><span data-stu-id="63be1-124">Then click the ***Select Folder*** button to start the build process:</span></span>

![具有 [選取資料夾] 提示視窗的 Unity [建置設定] 視窗](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-7.png)

<span data-ttu-id="63be1-126">等候 Unity 完成建置程序。</span><span class="sxs-lookup"><span data-stu-id="63be1-126">Wait for Unity to finish the build process.</span></span>

![Unity 正在進行建置程序](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-8.png)

<span data-ttu-id="63be1-128">按兩下可執行檔，以在您的電腦上開啟電腦全像遠端應用程式。</span><span class="sxs-lookup"><span data-stu-id="63be1-128">double click on the Executable file to open the PC Holographic Remoting Application in your PC.</span></span>

> [!NOTE]
> <span data-ttu-id="63be1-129">由於電腦上建作為 UWP 的電腦應用程式的一些已知問題，我們會將電腦應用程式建立為 Windows 獨立進行 OpenXR。</span><span class="sxs-lookup"><span data-stu-id="63be1-129">Due to some known issues in Holographic Remoting for PC app Built as UWP we are Building the PC App as Windows Standalone for OpenXR.</span></span>


# <a name="legacy-wsa"></a>[<span data-ttu-id="63be1-130">舊版 WSA</span><span class="sxs-lookup"><span data-stu-id="63be1-130">Legacy WSA</span></span>](#tab/wsa)

### <a name="1-set-the-player-settings"></a><span data-ttu-id="63be1-131">1.設定玩家設定</span><span class="sxs-lookup"><span data-stu-id="63be1-131">1. Set the player settings</span></span>

<span data-ttu-id="63be1-132">在 [XR 設定] 區段中，選取 [支援的 WSA 全像攝影遠端處理] 核取方塊，並啟用全像攝影遠端處理。</span><span class="sxs-lookup"><span data-stu-id="63be1-132">In the **XR Settings** section, select the **WSA Holographic Remoting Supported** checkbox and enable the Holographic Remoting.</span></span>

![已啟用 WSA 全像攝影遠端處理支援的 Unity [XR 設定] 視窗](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step1-1.png)

### <a name="2-build-the-unity-project"></a><span data-ttu-id="63be1-134">2.建置 Unity 專案</span><span class="sxs-lookup"><span data-stu-id="63be1-134">2. Build the Unity Project</span></span>

<span data-ttu-id="63be1-135">在 Unity 功能表中，選取 [檔案] > [建置設定] 來開啟 [建置設定] 視窗。</span><span class="sxs-lookup"><span data-stu-id="63be1-135">In the Unity menu, select File > Build Settings to open the Build Settings window.</span></span>

<span data-ttu-id="63be1-136">在 [組建設定] 視窗中，按一下 [**新增開啟的場景** _] 按鈕，將您目前的場景新增至幕後。</span><span class="sxs-lookup"><span data-stu-id="63be1-136">In the Build Settings window, click the \***Add Open Scenes** _ button to add your current scene to the Scenes.</span></span> <span data-ttu-id="63be1-137">在 [組建] 清單中，按一下 [_ *_組建] 按鈕_*\* 以開啟組建通用 Windows 平臺視窗：</span><span class="sxs-lookup"><span data-stu-id="63be1-137">In the Build list, then click the _ *_Build button_*\* to open the Build Universal Windows Platform window:</span></span>

![已新增場景的 Unity [建置設定] 視窗](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step2-1.png)

<span data-ttu-id="63be1-139">在 [建置通用 Windows 平台] 視窗中，選擇適當的位置來儲存您的建置，例如 Documents\MixedRealityLearning。</span><span class="sxs-lookup"><span data-stu-id="63be1-139">In the Build Universal Windows Platform window, choose a suitable location to store your build, for example, Documents\MixedRealityLearning.</span></span> <span data-ttu-id="63be1-140">建立新的資料夾，並為其指定適當的名稱，例如 PCHolographicRemoting。</span><span class="sxs-lookup"><span data-stu-id="63be1-140">Create a new folder and give it a suitable name, for example, PCHolographicRemoting.</span></span> <span data-ttu-id="63be1-141">然後按一下 [選取資料夾] 按鈕來啟動建置程序：</span><span class="sxs-lookup"><span data-stu-id="63be1-141">Then click the ***Select Folder*** button to start the build process:</span></span>

![具有 [選取資料夾] 提示視窗的 Unity [建置設定] 視窗](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step2-2.png)

<span data-ttu-id="63be1-143">等候 Unity 完成建置程序。</span><span class="sxs-lookup"><span data-stu-id="63be1-143">Wait for Unity to finish the build process.</span></span>

![Unity 正在進行建置程序](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step2-3.png)

### <a name="3-build-and-deploy-the-application"></a><span data-ttu-id="63be1-145">3.組建和部署應用程式</span><span class="sxs-lookup"><span data-stu-id="63be1-145">3. Build and deploy the application</span></span>

<span data-ttu-id="63be1-146">當組建程序完成時，Unity 會提示 Windows 檔案總管開啟您儲存組建的位置。</span><span class="sxs-lookup"><span data-stu-id="63be1-146">When the build process is completed, Unity will prompt Windows File Explorer to open the location you stored the build.</span></span> <span data-ttu-id="63be1-147">瀏覽該資料夾，按兩下 .sln 檔案即可在 Visual Studio 中開啟該檔案：</span><span class="sxs-lookup"><span data-stu-id="63be1-147">Navigate inside the folder, and double-click the .sln file to open it in Visual Studio:</span></span>

![Windows 檔案總管，其中已選取新建立的 Visual Studio 解決方案](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step3-1.png)

> [!NOTE]
> <span data-ttu-id="63be1-149">如果 Visual Studio 要求您安裝新元件，請花一些時間確認是否已安裝所有必要元件，如同＜安裝工具＞文件中所指定。</span><span class="sxs-lookup"><span data-stu-id="63be1-149">If Visual Studio asks you to install new components, take a moment to ensure that all prerequisite components are installed as specified in the Install the Tools documentation.</span></span>

<span data-ttu-id="63be1-150">藉由選取 x64 架構的發行設定，以及選取本機電腦作為目標，來設定電腦的 Visual Studio：</span><span class="sxs-lookup"><span data-stu-id="63be1-150">Configure Visual Studio for PC by selecting the Release configuration, the x64 architecture, and Local Machine as target:</span></span>

![為本機電腦設定的 Visual Studio](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step3-2.png)

<span data-ttu-id="63be1-152">按一下顯示 [本機電腦] 的按鈕。</span><span class="sxs-lookup"><span data-stu-id="63be1-152">Click the button that says ***Local Machine***.</span></span> <span data-ttu-id="63be1-153">其會開始建置應用程式，並將其部署到您的電腦。</span><span class="sxs-lookup"><span data-stu-id="63be1-153">It starts to build and deploy the application on to your PC.</span></span> <span data-ttu-id="63be1-154">應用程式會預設安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="63be1-154">The application will be installed in your PC by default.</span></span>
