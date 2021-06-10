---
ms.openlocfilehash: 17719d2547aa10981e7b8cdf0d2c7d56823e6da5
ms.sourcegitcommit: bb9f54f3e872a5464a5d9ba88b7ab5b8896efd82
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/25/2021
ms.locfileid: "110345104"
---
# <a name="unity-2020--openxr"></a>[<span data-ttu-id="28939-101">Unity 2020 + OpenXR</span><span class="sxs-lookup"><span data-stu-id="28939-101">Unity 2020 + OpenXR</span></span>](#tab/openxr)

1. <span data-ttu-id="28939-102">在 HoloLens 上，移至 **Microsoft Store** 並安裝全像 **[遠端播放機](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)** 應用程式。</span><span class="sxs-lookup"><span data-stu-id="28939-102">On your HoloLens, go to the **Microsoft Store** and install the **[Holographic Remoting Player](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)** app.</span></span>
1. <span data-ttu-id="28939-103">在您的 HoloLens 上，啟動全像 **Remoting 的播放** 程式應用程式。</span><span class="sxs-lookup"><span data-stu-id="28939-103">On your HoloLens, start the **Holographic Remoting Player** app.</span></span>
1. <span data-ttu-id="28939-104">在 Unity 中，移至 [ **編輯** ] 功能表，然後選取 [ **專案設定**]。</span><span class="sxs-lookup"><span data-stu-id="28939-104">In Unity, go to the **Edit** menu and select **Project Settings**.</span></span>
1. <span data-ttu-id="28939-105">選取 **XR 外掛程式管理**。</span><span class="sxs-lookup"><span data-stu-id="28939-105">Select **XR Plug-in Management**.</span></span>
1. <span data-ttu-id="28939-106">確定已選取 [ **Windows 獨立** ] 索引標籤，並在清單中尋找 **OpenXR** 和 **Windows Mixed Reality 功能集** ，然後檢查其核取方塊。</span><span class="sxs-lookup"><span data-stu-id="28939-106">Ensure the **Windows Standalone** tab is selected, find **OpenXR** and **Windows Mixed Reality feature set** in the list, and check their checkboxes.</span></span>
1. <span data-ttu-id="28939-107">接下來，移至 [ **視窗]** 功能表，展開 [ **XR** ] 子功能表，然後選取 [ **OpenXR 編輯器遠端**]。</span><span class="sxs-lookup"><span data-stu-id="28939-107">Next, go to the **Window** menu, expand the **XR** submenu, and select **OpenXR Editor Remoting**.</span></span>
1. <span data-ttu-id="28939-108">按一下 [ **啟用編輯器遠端** 功能]。</span><span class="sxs-lookup"><span data-stu-id="28939-108">Click **Enable Editor Remoting**.</span></span>
1. <span data-ttu-id="28939-109">如果出現 [ **啟用遺失** 相依性] 按鈕，請按一下該按鈕。</span><span class="sxs-lookup"><span data-stu-id="28939-109">If the **Enable Missing Dependencies** button appears, click that as well.</span></span> <span data-ttu-id="28939-110">按鈕上方的錯誤方塊描述其啟用的功能以及原因。</span><span class="sxs-lookup"><span data-stu-id="28939-110">The error box above the button describes the features it's enabling and why.</span></span>
1. <span data-ttu-id="28939-111">針對 [ **遠端主機名**]，輸入 HOLOLENS 的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="28939-111">For **Remote Host Name**, enter the IP address of your HoloLens.</span></span>
   1. <span data-ttu-id="28939-112">視需要變更其他設定。</span><span class="sxs-lookup"><span data-stu-id="28939-112">Change other settings as needed.</span></span>
   1. <span data-ttu-id="28939-113">在啟動播放模式之後，編輯器會嘗試連接。</span><span class="sxs-lookup"><span data-stu-id="28939-113">The editor will attempt to connect once Play Mode is started.</span></span>
1. <span data-ttu-id="28939-114">選取 [ **播放** ] 按鈕以啟動播放模式，並在您的 HoloLens 上體驗應用程式。</span><span class="sxs-lookup"><span data-stu-id="28939-114">Select the **Play** button to start Play Mode and experience the app on your HoloLens.</span></span>

# <a name="unity-20192020--windows-xr-plugin"></a>[<span data-ttu-id="28939-115">Unity 2019/2020 + Windows XR 外掛程式</span><span class="sxs-lookup"><span data-stu-id="28939-115">Unity 2019/2020 + Windows XR Plugin</span></span>](#tab/winxr)

1. <span data-ttu-id="28939-116">在 HoloLens 上，移至 **Microsoft Store** 並安裝全像 **[遠端播放機](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)** 應用程式。</span><span class="sxs-lookup"><span data-stu-id="28939-116">On your HoloLens, go to the **Microsoft Store** and install the **[Holographic Remoting Player](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)** app.</span></span>
1. <span data-ttu-id="28939-117">在您的 HoloLens 上，啟動全像 **Remoting 的播放** 程式應用程式。</span><span class="sxs-lookup"><span data-stu-id="28939-117">On your HoloLens, start the **Holographic Remoting Player** app.</span></span>
1. <span data-ttu-id="28939-118">在 Unity 中，移至 [ **編輯** ] 功能表，然後選取 [ **專案設定**]。</span><span class="sxs-lookup"><span data-stu-id="28939-118">In Unity, go to the **Edit** menu and select **Project Settings**.</span></span>
1. <span data-ttu-id="28939-119">選取 **XR 外掛程式管理**。</span><span class="sxs-lookup"><span data-stu-id="28939-119">Select **XR Plug-in Management**.</span></span>
1. <span data-ttu-id="28939-120">確定已選取 [ **Windows 獨立** ] 索引標籤，並在清單中尋找 **Windows Mixed Reality** ，然後選取其核取方塊。</span><span class="sxs-lookup"><span data-stu-id="28939-120">Ensure the **Windows Standalone** tab is selected, find **Windows Mixed Reality** in the list, and check its checkbox.</span></span>
1. <span data-ttu-id="28939-121">接下來，移至 [ **視窗]** 功能表，展開 [ **XR** ] 子功能表，然後選取 [ **Windows XR 外掛程式遠端處理**]。</span><span class="sxs-lookup"><span data-stu-id="28939-121">Next, go to the **Window** menu, expand the **XR** submenu, and select **Windows XR Plugin Remoting**.</span></span>
1. <span data-ttu-id="28939-122">將 **模擬模式** 設定為 [ **遠端裝置**]。</span><span class="sxs-lookup"><span data-stu-id="28939-122">Set **Emulation Mode** to **Remote to Device**.</span></span>
1. <span data-ttu-id="28939-123">針對 [ **遠端電腦**]，輸入 HOLOLENS 的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="28939-123">For **Remote Machine**, enter the IP address of your HoloLens.</span></span>
1. <span data-ttu-id="28939-124">若要連接，請執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="28939-124">To connect, either:</span></span>
   1. <span data-ttu-id="28939-125">若要手動連接，請取消核取 **[播放]**，然後選取 **[連接**]。</span><span class="sxs-lookup"><span data-stu-id="28939-125">To manually connect, uncheck **Connect on Play**, and select **Connect**.</span></span> <span data-ttu-id="28939-126">您應該會看到 [連線 **狀態** ] 變更為 [ **已連接** ]，並在 HoloLens 中看到畫面空白。</span><span class="sxs-lookup"><span data-stu-id="28939-126">You should see **Connection Status** change to **Connected** and see the screen go blank in the HoloLens.</span></span>
   1. <span data-ttu-id="28939-127">若要自動連接，請 **在播放時檢查 connect**。</span><span class="sxs-lookup"><span data-stu-id="28939-127">To automatically connect, check **Connect on Play**.</span></span> <span data-ttu-id="28939-128">在啟動播放模式之後，編輯器會嘗試連接。</span><span class="sxs-lookup"><span data-stu-id="28939-128">The editor will attempt to connect once Play Mode is started.</span></span>
1. <span data-ttu-id="28939-129">選取 [ **播放** ] 按鈕以啟動播放模式，並在您的 HoloLens 上體驗應用程式。</span><span class="sxs-lookup"><span data-stu-id="28939-129">Select the **Play** button to start Play Mode and experience the app on your HoloLens.</span></span>

# <a name="legacy-wsa"></a>[<span data-ttu-id="28939-130">舊版 WSA</span><span class="sxs-lookup"><span data-stu-id="28939-130">Legacy WSA</span></span>](#tab/wsa)

1. <span data-ttu-id="28939-131">在 HoloLens 上，移至 **Microsoft Store** 並安裝全像 **[遠端播放機](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)** 應用程式。</span><span class="sxs-lookup"><span data-stu-id="28939-131">On your HoloLens, go to the **Microsoft Store** and install the **[Holographic Remoting Player](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)** app.</span></span>
1. <span data-ttu-id="28939-132">在您的 HoloLens 上，啟動全像 **Remoting 的播放** 程式應用程式。</span><span class="sxs-lookup"><span data-stu-id="28939-132">On your HoloLens, start the **Holographic Remoting Player** app.</span></span>
1. <span data-ttu-id="28939-133">在 Unity 中，移至 [ **視窗]** 功能表，展開 [ **XR** ] 子功能表，然後選取在 Unity 2019) 中標示為已淘汰 (的全像 **模擬** 。</span><span class="sxs-lookup"><span data-stu-id="28939-133">In Unity, go to the **Window** menu, expand the **XR** submenu, and select **Holographic Emulation** (marked as deprecated in Unity 2019).</span></span>
1. <span data-ttu-id="28939-134">將 **模擬模式** 設定為 [ **遠端裝置**]。</span><span class="sxs-lookup"><span data-stu-id="28939-134">Set **Emulation Mode** to **Remote to Device**.</span></span>
1. <span data-ttu-id="28939-135">根據您使用的是第一代 HoloLens 或 HoloLens 2，設定 **裝置版本** 。</span><span class="sxs-lookup"><span data-stu-id="28939-135">Set **Device Version** according to if you're using a first generation HoloLens or a HoloLens 2.</span></span>
1. <span data-ttu-id="28939-136">針對 [ **遠端電腦**]，輸入 HOLOLENS 的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="28939-136">For **Remote Machine**, enter the IP address of your HoloLens.</span></span>
1. <span data-ttu-id="28939-137">選取 [連接]。</span><span class="sxs-lookup"><span data-stu-id="28939-137">Select **Connect**.</span></span> <span data-ttu-id="28939-138">您應該會看到 [連線 **狀態** ] 變更為 [ **已連接** ]，並在 HoloLens 中看到畫面空白。</span><span class="sxs-lookup"><span data-stu-id="28939-138">You should see **Connection Status** change to **Connected** and see the screen go blank in the HoloLens.</span></span>
1. <span data-ttu-id="28939-139">選取 [ **播放** ] 按鈕以啟動播放模式，並在您的 HoloLens 上體驗應用程式。</span><span class="sxs-lookup"><span data-stu-id="28939-139">Select the **Play** button to start Play Mode and experience the app on your HoloLens.</span></span>
