---
ms.openlocfilehash: 40d24083ec83b9d6faebc00cf801d1f6f55fddd7
ms.sourcegitcommit: bdf4babd13e021f41fb04cdb3611bb759bd77537
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2021
ms.locfileid: "112392288"
---
# <a name="unity-2020--openxr"></a>[<span data-ttu-id="afc7a-101">Unity 2020 + OpenXR</span><span class="sxs-lookup"><span data-stu-id="afc7a-101">Unity 2020 + OpenXR</span></span>](#tab/openxr)

1. <span data-ttu-id="afc7a-102">在 HoloLens 上，移至 **Microsoft Store** 並安裝全像 **[遠端播放機](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)** 應用程式。</span><span class="sxs-lookup"><span data-stu-id="afc7a-102">On your HoloLens, go to the **Microsoft Store** and install the **[Holographic Remoting Player](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)** app.</span></span>
1. <span data-ttu-id="afc7a-103">在您的 HoloLens 上，啟動全像 **Remoting 的播放** 程式應用程式。</span><span class="sxs-lookup"><span data-stu-id="afc7a-103">On your HoloLens, start the **Holographic Remoting Player** app.</span></span>
1. <span data-ttu-id="afc7a-104">在 Unity 中，移至 [ **編輯** ] 功能表，然後選取 [ **專案設定**]。</span><span class="sxs-lookup"><span data-stu-id="afc7a-104">In Unity, go to the **Edit** menu and select **Project Settings**.</span></span>
1. <span data-ttu-id="afc7a-105">選取 **XR 外掛程式管理**。</span><span class="sxs-lookup"><span data-stu-id="afc7a-105">Select **XR Plug-in Management**.</span></span>
1. <span data-ttu-id="afc7a-106">確定已選取 [ **Windows 獨立** ] 索引標籤，並在清單中尋找 **OpenXR** 和 **Windows Mixed Reality 功能集** ，然後檢查其核取方塊。</span><span class="sxs-lookup"><span data-stu-id="afc7a-106">Ensure the **Windows Standalone** tab is selected, find **OpenXR** and **Windows Mixed Reality feature set** in the list, and check their checkboxes.</span></span>
1. <span data-ttu-id="afc7a-107">接下來，移至 [ **視窗]** 功能表，展開 [ **XR** ] 子功能表，然後選取 [ **OpenXR 編輯器遠端**]。</span><span class="sxs-lookup"><span data-stu-id="afc7a-107">Next, go to the **Window** menu, expand the **XR** submenu, and select **OpenXR Editor Remoting**.</span></span>

    ![醒目提示 XR 外掛程式管理的 Unity 編輯器中開啟之 [專案設定] 面板的螢幕擷取畫面](../images/openxr-features-img-02.png)

1. <span data-ttu-id="afc7a-109">按一下 [ **啟用編輯器遠端** 功能]。</span><span class="sxs-lookup"><span data-stu-id="afc7a-109">Click **Enable Editor Remoting**.</span></span>

    ![在 Unity 編輯器中開啟專案設定面板的螢幕擷取畫面，其中已醒目提示功能](../images/openxr-features-img-03.png)

1. <span data-ttu-id="afc7a-111">如果出現 [ **啟用遺失** 相依性] 按鈕，請按一下該按鈕。</span><span class="sxs-lookup"><span data-stu-id="afc7a-111">If the **Enable Missing Dependencies** button appears, click that as well.</span></span> <span data-ttu-id="afc7a-112">按鈕上方的錯誤方塊描述其啟用的功能以及原因。</span><span class="sxs-lookup"><span data-stu-id="afc7a-112">The error box above the button describes the features it's enabling and why.</span></span>
1. <span data-ttu-id="afc7a-113">針對 [ **遠端主機名**]，輸入 HOLOLENS 的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="afc7a-113">For **Remote Host Name**, enter the IP address of your HoloLens.</span></span>
   1. <span data-ttu-id="afc7a-114">視需要變更其他設定。</span><span class="sxs-lookup"><span data-stu-id="afc7a-114">Change other settings as needed.</span></span>
   1. <span data-ttu-id="afc7a-115">在啟動播放模式之後，編輯器會嘗試連接。</span><span class="sxs-lookup"><span data-stu-id="afc7a-115">The editor will attempt to connect once Play Mode is started.</span></span>
1. <span data-ttu-id="afc7a-116">選取 [ **播放** ] 按鈕以啟動播放模式，並在您的 HoloLens 上體驗應用程式。</span><span class="sxs-lookup"><span data-stu-id="afc7a-116">Select the **Play** button to start Play Mode and experience the app on your HoloLens.</span></span> <span data-ttu-id="afc7a-117">若要在播放模式中 debug c # 腳本，請 [將 Visual Studio 附加至 Unity](/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows)。</span><span class="sxs-lookup"><span data-stu-id="afc7a-117">To debug C# scripts in play mode, [attach Visual Studio to Unity](/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows).</span></span>

> [!NOTE]
> <span data-ttu-id="afc7a-118">從0.1.0 版起，全像「全像」遠端執行時間不支援錨點，而 ARAnchorManager 功能將無法透過遠端處理。</span><span class="sxs-lookup"><span data-stu-id="afc7a-118">As of version 0.1.0, the Holographic Remoting runtime doesn’t support Anchors, and ARAnchorManager functionalities will not work through remoting.</span></span>  <span data-ttu-id="afc7a-119">這項功能會在未來的版本中推出。</span><span class="sxs-lookup"><span data-stu-id="afc7a-119">This feature is coming in future releases.</span></span>

# <a name="unity-20192020--windows-xr-plugin"></a>[<span data-ttu-id="afc7a-120">Unity 2019/2020 + Windows XR 外掛程式</span><span class="sxs-lookup"><span data-stu-id="afc7a-120">Unity 2019/2020 + Windows XR Plugin</span></span>](#tab/winxr)

1. <span data-ttu-id="afc7a-121">在 HoloLens 上，移至 **Microsoft Store** 並安裝全像 **[遠端播放機](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)** 應用程式。</span><span class="sxs-lookup"><span data-stu-id="afc7a-121">On your HoloLens, go to the **Microsoft Store** and install the **[Holographic Remoting Player](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)** app.</span></span>
1. <span data-ttu-id="afc7a-122">在您的 HoloLens 上，啟動全像 **Remoting 的播放** 程式應用程式。</span><span class="sxs-lookup"><span data-stu-id="afc7a-122">On your HoloLens, start the **Holographic Remoting Player** app.</span></span>
1. <span data-ttu-id="afc7a-123">在 Unity 中，移至 [ **編輯** ] 功能表，然後選取 [ **專案設定**]。</span><span class="sxs-lookup"><span data-stu-id="afc7a-123">In Unity, go to the **Edit** menu and select **Project Settings**.</span></span>
1. <span data-ttu-id="afc7a-124">選取 **XR 外掛程式管理**。</span><span class="sxs-lookup"><span data-stu-id="afc7a-124">Select **XR Plug-in Management**.</span></span>
1. <span data-ttu-id="afc7a-125">確定已選取 [ **Windows 獨立** ] 索引標籤，並在清單中尋找 **Windows Mixed Reality** ，然後選取其核取方塊。</span><span class="sxs-lookup"><span data-stu-id="afc7a-125">Ensure the **Windows Standalone** tab is selected, find **Windows Mixed Reality** in the list, and check its checkbox.</span></span>
1. <span data-ttu-id="afc7a-126">接下來，移至 [ **視窗]** 功能表，展開 [ **XR** ] 子功能表，然後選取 [ **Windows XR 外掛程式遠端處理**]。</span><span class="sxs-lookup"><span data-stu-id="afc7a-126">Next, go to the **Window** menu, expand the **XR** submenu, and select **Windows XR Plugin Remoting**.</span></span>
1. <span data-ttu-id="afc7a-127">將 **模擬模式** 設定為 [ **遠端裝置**]。</span><span class="sxs-lookup"><span data-stu-id="afc7a-127">Set **Emulation Mode** to **Remote to Device**.</span></span>
1. <span data-ttu-id="afc7a-128">針對 [ **遠端電腦**]，輸入 HOLOLENS 的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="afc7a-128">For **Remote Machine**, enter the IP address of your HoloLens.</span></span>
1. <span data-ttu-id="afc7a-129">若要連接，請執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="afc7a-129">To connect, either:</span></span>
   1. <span data-ttu-id="afc7a-130">若要手動連接，請取消核取 **[播放]**，然後選取 **[連接**]。</span><span class="sxs-lookup"><span data-stu-id="afc7a-130">To manually connect, uncheck **Connect on Play**, and select **Connect**.</span></span> <span data-ttu-id="afc7a-131">您應該會看到 [連線 **狀態** ] 變更為 [ **已連接** ]，並在 HoloLens 中看到畫面空白。</span><span class="sxs-lookup"><span data-stu-id="afc7a-131">You should see **Connection Status** change to **Connected** and see the screen go blank in the HoloLens.</span></span>
   1. <span data-ttu-id="afc7a-132">若要自動連接，請 **在播放時檢查 connect**。</span><span class="sxs-lookup"><span data-stu-id="afc7a-132">To automatically connect, check **Connect on Play**.</span></span> <span data-ttu-id="afc7a-133">在啟動播放模式之後，編輯器會嘗試連接。</span><span class="sxs-lookup"><span data-stu-id="afc7a-133">The editor will attempt to connect once Play Mode is started.</span></span>
1. <span data-ttu-id="afc7a-134">選取 [ **播放** ] 按鈕以啟動播放模式，並在您的 HoloLens 上體驗應用程式。</span><span class="sxs-lookup"><span data-stu-id="afc7a-134">Select the **Play** button to start Play Mode and experience the app on your HoloLens.</span></span> <span data-ttu-id="afc7a-135">若要在播放模式中 debug c # 腳本，請 [將 Visual Studio 附加至 Unity](/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows)。</span><span class="sxs-lookup"><span data-stu-id="afc7a-135">To debug C# scripts in play mode, [attach Visual Studio to Unity](/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows).</span></span>

# <a name="legacy-wsa"></a>[<span data-ttu-id="afc7a-136">舊版 WSA</span><span class="sxs-lookup"><span data-stu-id="afc7a-136">Legacy WSA</span></span>](#tab/wsa)

1. <span data-ttu-id="afc7a-137">在 HoloLens 上，移至 **Microsoft Store** 並安裝全像 **[遠端播放機](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)** 應用程式。</span><span class="sxs-lookup"><span data-stu-id="afc7a-137">On your HoloLens, go to the **Microsoft Store** and install the **[Holographic Remoting Player](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)** app.</span></span>
1. <span data-ttu-id="afc7a-138">在您的 HoloLens 上，啟動全像 **Remoting 的播放** 程式應用程式。</span><span class="sxs-lookup"><span data-stu-id="afc7a-138">On your HoloLens, start the **Holographic Remoting Player** app.</span></span>
1. <span data-ttu-id="afc7a-139">在 Unity 中，移至 [ **視窗]** 功能表，展開 [ **XR** ] 子功能表，然後選取在 Unity 2019) 中標示為已淘汰 (的全像 **模擬** 。</span><span class="sxs-lookup"><span data-stu-id="afc7a-139">In Unity, go to the **Window** menu, expand the **XR** submenu, and select **Holographic Emulation** (marked as deprecated in Unity 2019).</span></span>
1. <span data-ttu-id="afc7a-140">將 **模擬模式** 設定為 [ **遠端裝置**]。</span><span class="sxs-lookup"><span data-stu-id="afc7a-140">Set **Emulation Mode** to **Remote to Device**.</span></span>
1. <span data-ttu-id="afc7a-141">根據您使用的是第一代 HoloLens 或 HoloLens 2，設定 **裝置版本** 。</span><span class="sxs-lookup"><span data-stu-id="afc7a-141">Set **Device Version** according to if you're using a first generation HoloLens or a HoloLens 2.</span></span>
1. <span data-ttu-id="afc7a-142">針對 [ **遠端電腦**]，輸入 HOLOLENS 的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="afc7a-142">For **Remote Machine**, enter the IP address of your HoloLens.</span></span>
1. <span data-ttu-id="afc7a-143">選取 [連接]。</span><span class="sxs-lookup"><span data-stu-id="afc7a-143">Select **Connect**.</span></span> <span data-ttu-id="afc7a-144">您應該會看到 [連線 **狀態** ] 變更為 [ **已連接** ]，並在 HoloLens 中看到畫面空白。</span><span class="sxs-lookup"><span data-stu-id="afc7a-144">You should see **Connection Status** change to **Connected** and see the screen go blank in the HoloLens.</span></span>
1. <span data-ttu-id="afc7a-145">選取 [ **播放** ] 按鈕以啟動播放模式，並在您的 HoloLens 上體驗應用程式。</span><span class="sxs-lookup"><span data-stu-id="afc7a-145">Select the **Play** button to start Play Mode and experience the app on your HoloLens.</span></span> <span data-ttu-id="afc7a-146">若要在播放模式中 debug c # 腳本，請 [將 Visual Studio 附加至 Unity](/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows)。</span><span class="sxs-lookup"><span data-stu-id="afc7a-146">To debug C# scripts in play mode, [attach Visual Studio to Unity](/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows).</span></span>
