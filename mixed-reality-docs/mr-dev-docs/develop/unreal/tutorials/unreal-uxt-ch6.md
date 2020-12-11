---
title: 6. 封裝並部署至裝置或模擬器
description: 教學課程系列的第 6 部分 (共有 6 部分)，使用 Unreal Engine 4 和混合實境工具組 UX 工具外掛程式來建置國際象棋應用程式
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 混合實境, 教學課程, 開始使用, mrtk, uxt, UX 工具, 文件, 混合實境頭戴式裝置, windows 混合實境頭戴式裝置, 虛擬實境頭戴式裝置
ms.openlocfilehash: 4319b1171090b8ca7a320e98867bfb3635bab005
ms.sourcegitcommit: 32cb81eee976e73cd661c2b347691c37865a60bc
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/04/2020
ms.locfileid: "96609489"
---
# <a name="6-packaging--deploying-to-device-or-emulator"></a><span data-ttu-id="25451-104">6.封裝並部署至裝置或模擬器</span><span class="sxs-lookup"><span data-stu-id="25451-104">6. Packaging & deploying to device or emulator</span></span>

<span data-ttu-id="25451-105">在上一個教學課程中，您已新增一個簡單按鈕，將棋子重設為其原始位置。</span><span class="sxs-lookup"><span data-stu-id="25451-105">In the previous tutorial, you added a simple button that resets the chess piece to its original position.</span></span> <span data-ttu-id="25451-106">在此最後一節中，您將會準備好要在 HoloLens 2 或模擬器上執行的應用程式。</span><span class="sxs-lookup"><span data-stu-id="25451-106">In this final section, you'll get the app ready to run on a HoloLens 2 or an Emulator.</span></span> <span data-ttu-id="25451-107">若有 HoloLens 2，您可以從電腦串流或封裝應用程式，以直接在裝置上執行。</span><span class="sxs-lookup"><span data-stu-id="25451-107">If you have a HoloLens 2, you can either stream from your computer or package the app to run directly on the device.</span></span> <span data-ttu-id="25451-108">如果沒有裝置，您會封裝應用程式以在模擬器上執行。</span><span class="sxs-lookup"><span data-stu-id="25451-108">If you don't have a device, you'll be packaging the app to run on the Emulator.</span></span> <span data-ttu-id="25451-109">本節結束時，您將會有一個可以播放的已部署混合實境應用程式，這是透過互動和 UI 完成的。</span><span class="sxs-lookup"><span data-stu-id="25451-109">By the end of this section, you'll have a deployed mixed reality app that you can play, complete with interactions and UI.</span></span>

## <a name="objectives"></a><span data-ttu-id="25451-110">目標</span><span class="sxs-lookup"><span data-stu-id="25451-110">Objectives</span></span>

* <span data-ttu-id="25451-111">[僅限裝置] 利用全像應用程式遠端處理串流至 HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="25451-111">[Device only] Streaming to HoloLens 2 with holographic app remoting</span></span>
* <span data-ttu-id="25451-112">封裝應用程式並將其部署至 HoloLens 2 裝置或模擬器</span><span class="sxs-lookup"><span data-stu-id="25451-112">Packaging and deploying the app to a HoloLens 2 device or emulator</span></span>

## <a name="device-only-streaming"></a><span data-ttu-id="25451-113">[僅限裝置] 串流</span><span class="sxs-lookup"><span data-stu-id="25451-113">[Device Only] Streaming</span></span>

<span data-ttu-id="25451-114">[全像遠端處理](https://docs.microsoft.com/windows/mixed-reality/add-holographic-remoting)表示將電腦或獨立 UWP 裝置中的資料串流至 HoloLens 2，而不是切換管道。</span><span class="sxs-lookup"><span data-stu-id="25451-114">[Holographic Remoting](https://docs.microsoft.com/windows/mixed-reality/add-holographic-remoting) means streaming data from a PC or standalone UWP device to the HoloLens 2, not switching the channel.</span></span> <span data-ttu-id="25451-115">遠端主機應用程式會從 HoloLens 接收輸入資料流程、在虛擬沉浸式檢視中呈現內容，以及透過 Wi-fi 將內容框架串流回 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="25451-115">A remoting host app receives an input data stream from a HoloLens, renders content in a virtual immersive view, and streams content frames back to HoloLens over Wi-Fi.</span></span> <span data-ttu-id="25451-116">串流可讓您將遠端沉浸式檢視新增至現有的桌上型電腦軟體，並可存取更多系統資源。</span><span class="sxs-lookup"><span data-stu-id="25451-116">Streaming lets you add remote immersive views into existing desktop PC software and has access to more system resources.</span></span>

<span data-ttu-id="25451-117">如果您是使用國際象棋應用程式前往此路由，將需要進行一些事項：</span><span class="sxs-lookup"><span data-stu-id="25451-117">If you're going this route with the chess app, you'll need a few things:</span></span>

1.  <span data-ttu-id="25451-118">從您的 HoloLens 2 上的 Microsoft Store 安裝 **全像攝影遠端播放程式** 並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="25451-118">Install the **Holographic Remoting Player** from the Microsoft Store on your HoloLens 2 and run the app.</span></span> <span data-ttu-id="25451-119">請記下應用程式中顯示的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="25451-119">Note your IP address displayed in the app.</span></span>

2.  <span data-ttu-id="25451-120">回到 Unreal 編輯器，移至 [編輯] > [專案設定]，然後勾選 [全像攝影遠端處理] 區段中的 [啟用遠端處理]。</span><span class="sxs-lookup"><span data-stu-id="25451-120">Back in the Unreal editor, go to **Edit > Project Settings** and check **Enable Remoting** in the **Holographic Remoting** section.</span></span>

3.  <span data-ttu-id="25451-121">重新啟動編輯器，然後輸入您裝置的 IP 位址 (如全像遠端處理播放程式中所顯示)，接著按一下 [連線]。</span><span class="sxs-lookup"><span data-stu-id="25451-121">Restart the editor, then enter your device's IP address (as displayed in the Holographic Remoting Player app), then click **Connect**.</span></span>

<span data-ttu-id="25451-122">連線之後，請按一下 [播放] 按鈕右邊的下拉箭號，然後選取 [VR 預覽]。</span><span class="sxs-lookup"><span data-stu-id="25451-122">Once you’re connected, click the drop-down arrow to the right of the **Play** button and select **VR Preview**.</span></span> <span data-ttu-id="25451-123">應用程式會在 [VR 預覽] 視窗中執行，進而串流至 HoloLens 頭戴式裝置。</span><span class="sxs-lookup"><span data-stu-id="25451-123">The app will run in the VR Preview window, which is streamed to the HoloLens headset.</span></span>

## <a name="packaging-and-deploying-the-app-via-device-portal"></a><span data-ttu-id="25451-124">透過裝置入口網站封裝和部署應用程式</span><span class="sxs-lookup"><span data-stu-id="25451-124">Packaging and deploying the app via device portal</span></span>

>[!NOTE]
><span data-ttu-id="25451-125">如果這是您第一次為適用於 HoloLens 的 Unreal 應用程式進行封裝，則需從 Epic Launcher 下載支援的檔案。</span><span class="sxs-lookup"><span data-stu-id="25451-125">If this is your first time packaging an Unreal app for HoloLens, you'll need to download supporting files from the Epic Launcher.</span></span>
>- <span data-ttu-id="25451-126">移至 [編輯器喜好設定] > [一般] > [原始程式碼] > [原始程式碼編輯器]，並確認已選取 [Visual Studio 2019]。</span><span class="sxs-lookup"><span data-stu-id="25451-126">Go to **Editor Preferences > General > Source Code > Source Code Editor** and check that Visual Studio 2019 is selected.</span></span>
>- <span data-ttu-id="25451-127">移至 Epic Games Launcher 中的 [程式庫] 索引標籤、選取 [啟動] 旁邊的下拉箭號，然後按一下 [選項]。</span><span class="sxs-lookup"><span data-stu-id="25451-127">Go to the **Library** tab in the Epic Games Launcher, select the dropdown arrow next to **Launch** >and click **Options**.</span></span>
>- <span data-ttu-id="25451-128">在 [目標平台] 中，選取 **HoloLens 2**，然後按一下 [套用]。</span><span class="sxs-lookup"><span data-stu-id="25451-128">Under **Target Platforms**, select **HoloLens 2** and click **Apply**.</span></span>
><span data-ttu-id="25451-129">![變更專案設定中的目標平台](images/unreal-uxt/6-installationoptions.PNG)</span><span class="sxs-lookup"><span data-stu-id="25451-129">![Change target platform in project settings](images/unreal-uxt/6-installationoptions.PNG)</span></span>

1.  <span data-ttu-id="25451-130">移至 [編輯] > [專案設定]。</span><span class="sxs-lookup"><span data-stu-id="25451-130">Go to **Edit > Project Settings**.</span></span>
    * <span data-ttu-id="25451-131">在 [專案] > [描述] > [關於] > [專案名稱] 底下，新增專案名稱。</span><span class="sxs-lookup"><span data-stu-id="25451-131">Add a project name under **Project > Description > About > Project Name**.</span></span>
    * <span data-ttu-id="25451-132">在 [專案] > [描述] > [發行者] > [公司辨別名稱] 底下，新增 **CN=YourCompanyName**。</span><span class="sxs-lookup"><span data-stu-id="25451-132">Add **CN=YourCompanyName** under **Project > Description > Publisher > Company Distinguished Name**.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="25451-133">當您嘗試在步驟 3 中產生新的憑證時，將其中一個欄位留空會導致錯誤。</span><span class="sxs-lookup"><span data-stu-id="25451-133">Leaving either of these fields blank will result in an error when you try and generate a new certificate in step 3.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="25451-134">發行者的名稱必須採用 [LADPv3 辨別名稱格式](https://www.ietf.org/rfc/rfc2253.txt)。</span><span class="sxs-lookup"><span data-stu-id="25451-134">The publisher's name must be in [LADPv3 Distinguished Names Format](https://www.ietf.org/rfc/rfc2253.txt).</span></span> <span data-ttu-id="25451-135">若發行者名稱的格式不正確，在封裝時將會導致「找不到簽署金鑰。</span><span class="sxs-lookup"><span data-stu-id="25451-135">A malformed publisher's name leads to the "Signing key not found.</span></span> <span data-ttu-id="25451-136">無法以數位方式簽署應用程式。」</span><span class="sxs-lookup"><span data-stu-id="25451-136">The app could not be digitally signed."</span></span> <span data-ttu-id="25451-137">錯誤。</span><span class="sxs-lookup"><span data-stu-id="25451-137">error upon packaging.</span></span>

![專案設定 - 描述](images/unreal-uxt/6-cn.PNG)

2.  <span data-ttu-id="25451-139">在 [平台] > [HoloLens] 底下，啟用 [針對 HoloLens 模擬進行建置] 和/或 [針對 HoloLens 裝置進行建置]。</span><span class="sxs-lookup"><span data-stu-id="25451-139">Enable **Build for HoloLens Emulation** and/or **Build for HoloLens Device** under **Platforms > HoloLens**.</span></span>

3.  <span data-ttu-id="25451-140">按一下 [封裝] 區段 (在 [簽署憑證] 旁邊) 中的 [產生新項目]。</span><span class="sxs-lookup"><span data-stu-id="25451-140">Click **Generate new** in the **Packaging** section (next to **Signing Certificate**).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="25451-141">如果您使用的是已產生的憑證，則憑證的發行者名稱必須與應用程式的發行者名稱相同。</span><span class="sxs-lookup"><span data-stu-id="25451-141">If you're using an already generated certificate, then the certificate's publisher name must be the same as the application's publisher name.</span></span> <span data-ttu-id="25451-142">否則將會導致「找不到簽署金鑰。</span><span class="sxs-lookup"><span data-stu-id="25451-142">Otherwise it leads to the "Signing key not found.</span></span> <span data-ttu-id="25451-143">無法以數位方式簽署應用程式。」</span><span class="sxs-lookup"><span data-stu-id="25451-143">The app could not be digitally signed."</span></span> <span data-ttu-id="25451-144">錯誤內容。</span><span class="sxs-lookup"><span data-stu-id="25451-144">error.</span></span>

![專案設定 - 平台 - HoloLens](images/unreal-uxt/6-packaging.PNG)

4. <span data-ttu-id="25451-146">當系統提示您建立私密金鑰密碼時，請按一下 [無] 以供測試之用。</span><span class="sxs-lookup"><span data-stu-id="25451-146">Click **None** for testing purposes when you're prompted to create a Private Key Password.</span></span>

![產生新的憑證](images/unreal-uxt/6-private-key-testing.png)

5. <span data-ttu-id="25451-148">移至 [檔案] > [封裝專案]，然後選取 [HoloLens]。</span><span class="sxs-lookup"><span data-stu-id="25451-148">Go to **File > Package Project** and select **HoloLens**.</span></span>
    * <span data-ttu-id="25451-149">建立新資料夾來儲存您的封裝，然後按一下 [選取資料夾]。</span><span class="sxs-lookup"><span data-stu-id="25451-149">Create a new folder to save your package in and click **Select Folder**.</span></span>

6.  <span data-ttu-id="25451-150">一旦封裝了應用程式後，請開啟 [Windows 裝置入口網站](https://docs.microsoft.com/windows/mixed-reality/using-the-windows-device-portal)移至 [檢視] > [應用程式]，然後尋找 [部署應用程式] 區段。</span><span class="sxs-lookup"><span data-stu-id="25451-150">Open the [Windows Device Portal](https://docs.microsoft.com/windows/mixed-reality/using-the-windows-device-portal) once the app is packaged, go to **Views > Apps** and find the **Deploy apps** section.</span></span>

7.  <span data-ttu-id="25451-151">按一下 [瀏覽 ...]、移至您的 **ChessApp.appxbundle** 檔案，然後按一下 [開啟]。</span><span class="sxs-lookup"><span data-stu-id="25451-151">Click **Browse...**, go to your **ChessApp.appxbundle** file and click **Open**.</span></span>

    * <span data-ttu-id="25451-152">如果這是您第一次在裝置上安裝應用程式，請勾選 [允許我選取架構套件] 旁的方塊。</span><span class="sxs-lookup"><span data-stu-id="25451-152">Check the box next to **Allow me to select framework packages** if you're installing the app on your device for the first time.</span></span>
    * <span data-ttu-id="25451-153">在下一個對話方塊中，包含適當的 **VCLibs** 和 **appx** 檔案 (若為裝置則為 **arm64**，若為模擬器則為 **x64**)。</span><span class="sxs-lookup"><span data-stu-id="25451-153">In the next dialogue, include the appropriate **VCLibs** and **appx** files, **arm64** for device and **x64** for emulator.</span></span> <span data-ttu-id="25451-154">您可以在儲存套件的資料夾內 **HoloLens** 底下找到這些檔案。</span><span class="sxs-lookup"><span data-stu-id="25451-154">You can find the files under **HoloLens** inside the folder where you saved your package.</span></span>

8.  <span data-ttu-id="25451-155">按一下 [安裝]</span><span class="sxs-lookup"><span data-stu-id="25451-155">Click **Install**</span></span>
    * <span data-ttu-id="25451-156">您現在可以移至 [所有應用程式]，然後點選新安裝的應用程式來執行，或直接從 **Windows 裝置入口網站** 啟動應用程式。</span><span class="sxs-lookup"><span data-stu-id="25451-156">You can now go to **All Apps** and tap the newly installed app to run it, or start the app directly from the **Windows Device Portal**.</span></span> 

<span data-ttu-id="25451-157">恭喜！</span><span class="sxs-lookup"><span data-stu-id="25451-157">Congratulations!</span></span> <span data-ttu-id="25451-158">您的 HoloLens 混合實境應用程式已完成，且已可開始使用。</span><span class="sxs-lookup"><span data-stu-id="25451-158">Your HoloLens mixed reality application is finished and ready to go.</span></span> <span data-ttu-id="25451-159">不過，您的體驗尚未結束。</span><span class="sxs-lookup"><span data-stu-id="25451-159">However, you're not at the end of the road.</span></span> <span data-ttu-id="25451-160">MRTK 有許多獨立功能，您可以將其新增至專案，包括空間對應、注視和語音輸入，甚至是 QR 代碼。</span><span class="sxs-lookup"><span data-stu-id="25451-160">MRTK has lots of standalone features that you can add to your projects, including spatial mapping, gaze and voice input, and even QR codes.</span></span> <span data-ttu-id="25451-161">如需這些功能的詳細資訊，請參閱 [Unreal 開發概觀](https://docs.microsoft.com/windows/mixed-reality/unreal-development-overview)。</span><span class="sxs-lookup"><span data-stu-id="25451-161">More information on these features can be found in the [Unreal development overview](https://docs.microsoft.com/windows/mixed-reality/unreal-development-overview).</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="25451-162">下一個開發檢查點</span><span class="sxs-lookup"><span data-stu-id="25451-162">Next Development Checkpoint</span></span>

<span data-ttu-id="25451-163">依循我們配置的 Unreal 開發旅程，此時您會探索 MRTK核心建置組塊。</span><span class="sxs-lookup"><span data-stu-id="25451-163">If you're following the Unreal development journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="25451-164">接下來，您可以繼續進行下一個建置組塊：</span><span class="sxs-lookup"><span data-stu-id="25451-164">From here, you can continue to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="25451-165">注視輸入</span><span class="sxs-lookup"><span data-stu-id="25451-165">Gaze input</span></span>](../unreal-gaze-input.md)

<span data-ttu-id="25451-166">或者，直接跳到混合實境平台功能和 API 的主題：</span><span class="sxs-lookup"><span data-stu-id="25451-166">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="25451-167">HoloLens 相機</span><span class="sxs-lookup"><span data-stu-id="25451-167">HoloLens camera</span></span>](../unreal-hololens-camera.md)

<span data-ttu-id="25451-168">您可以隨時回到 [Unreal 開發檢查點](../unreal-development-overview.md#2-core-building-blocks)。</span><span class="sxs-lookup"><span data-stu-id="25451-168">You can always go back to the [Unreal development checkpoints](../unreal-development-overview.md#2-core-building-blocks) at any time.</span></span>
