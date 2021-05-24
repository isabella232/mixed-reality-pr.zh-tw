---
title: Unity 播放模式
description: 瞭解如何在 Unity 編輯器中使用播放模式，以預覽裝置上的應用程式變更，而不需要部署應用程式。
author: jonmlyons
ms.author: jlyons
ms.date: 03/21/2018
ms.topic: article
keywords: Unity、遠端處理、全像全像攝影、全像遠端播放機、HoloLens、混合現實耳機、windows mixed reality 耳機、虛擬實境耳機、unity play 模式
ms.openlocfilehash: 35f80b0c217adfd5c5d14799dc882d5c504925aa
ms.sourcegitcommit: b195b82f7e83e2ac4f5d8937d169e9dcb865d46d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/24/2021
ms.locfileid: "110333396"
---
# <a name="unity-play-mode"></a><span data-ttu-id="ac5d8-104">Unity 播放模式</span><span class="sxs-lookup"><span data-stu-id="ac5d8-104">Unity Play Mode</span></span>

<span data-ttu-id="ac5d8-105">處理 Unity 專案的快速方式是使用「播放模式」，這會在本機電腦上的 Unity 編輯器中執行您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="ac5d8-105">A fast way to work on your Unity project is to use "Play Mode", which runs your app locally in the Unity editor on your PC.</span></span> <span data-ttu-id="ac5d8-106">Unity 使用全像的遠端處理功能，在實際 HoloLens 裝置上提供快速的預覽內容。</span><span class="sxs-lookup"><span data-stu-id="ac5d8-106">Unity uses Holographic Remoting to provide a fast way to preview your content on a real HoloLens device.</span></span> <span data-ttu-id="ac5d8-107">[播放] 模式也可以與連接至開發電腦的 Windows Mixed Reality 耳機一起使用。</span><span class="sxs-lookup"><span data-stu-id="ac5d8-107">Play Mode can also be used with a Windows Mixed Reality headset attached to your development PC.</span></span>

## <a name="holographic-remoting-setup"></a><span data-ttu-id="ac5d8-108">全像遠端設定</span><span class="sxs-lookup"><span data-stu-id="ac5d8-108">Holographic Remoting setup</span></span>

1. <span data-ttu-id="ac5d8-109">首先，您必須從 HoloLens 2 上的 Microsoft Store 安裝全像[遠端播放機應用程式](https://www.microsoft.com/store/productId/9NBLGGH4SV40)</span><span class="sxs-lookup"><span data-stu-id="ac5d8-109">First, you need to [install the Holographic Remoting Player app](https://www.microsoft.com/store/productId/9NBLGGH4SV40) from the Microsoft Store on your HoloLens 2</span></span>
2. <span data-ttu-id="ac5d8-110">在 HoloLens 2 上執行全像遠端播放播放程式應用程式，您會看到要連接的版本號碼和 IP 位址</span><span class="sxs-lookup"><span data-stu-id="ac5d8-110">Run the Holographic Remoting Player app on HoloLens 2 and you'll see the version number and IP address to connect to</span></span>
    * <span data-ttu-id="ac5d8-111">您將需要2.4 或更新版本才能使用 OpenXR 外掛程式</span><span class="sxs-lookup"><span data-stu-id="ac5d8-111">You'll need v2.4 or later to work with the OpenXR plugin</span></span>

    ![HoloLens 中執行的全像 Remoting 播放程式的螢幕擷取畫面](images/openxr-features-img-01.png)

## <a name="holographic-remoting-in-unity-editor-play-mode"></a><span data-ttu-id="ac5d8-113">Unity 編輯器 play 模式的全像遠端功能</span><span class="sxs-lookup"><span data-stu-id="ac5d8-113">Holographic Remoting in Unity Editor play mode</span></span>

<span data-ttu-id="ac5d8-114">在 Visual Studio 專案中建立 UWP Unity 專案，然後將它封裝並部署到 HoloLens 2 裝置，可能需要一些時間。</span><span class="sxs-lookup"><span data-stu-id="ac5d8-114">Building a UWP Unity project in Visual Studio project and then packaging and deploying it to a HoloLens 2 device can take some time.</span></span> <span data-ttu-id="ac5d8-115">其中一個解決方法是啟用全像「全像」編輯器遠端功能，讓您透過網路直接使用「播放」模式來將 c # 腳本進行 HoloLens 2 裝置的偵測。</span><span class="sxs-lookup"><span data-stu-id="ac5d8-115">One solution is to enable the Holographic Editor Remoting feature, which lets you debug your C# script using “Play” mode directly to a HoloLens 2 device over your network.</span></span> <span data-ttu-id="ac5d8-116">此案例可避免建立 UWP 套件並將其部署至遠端裝置的額外負荷。</span><span class="sxs-lookup"><span data-stu-id="ac5d8-116">This scenario avoids the overhead of building and deploying a UWP package to remote device.</span></span>

1. <span data-ttu-id="ac5d8-117">遵循全像全像[遠端設定](#holographic-remoting-setup)的步驟</span><span class="sxs-lookup"><span data-stu-id="ac5d8-117">Follow the steps in [Holographic Remoting setup](#holographic-remoting-setup)</span></span>
2. <span data-ttu-id="ac5d8-118">開啟 **Windows > XR > OpenXR 編輯器遠端** 執行：</span><span class="sxs-lookup"><span data-stu-id="ac5d8-118">Open **Windows > XR > OpenXR Editor Remoting**:</span></span>

    ![醒目提示 XR 外掛程式管理的 Unity 編輯器中開啟之 [專案設定] 面板的螢幕擷取畫面](images/openxr-features-img-02.png)

3. <span data-ttu-id="ac5d8-120">輸入您從全像全像遠端應用程式取得的 IP 位址，然後選取 [**啟用編輯器遠端**]</span><span class="sxs-lookup"><span data-stu-id="ac5d8-120">Input the IP address you get from the Holographic Remoting app, and select **Enable Editor Remoting**</span></span>

    ![在 Unity 編輯器中開啟專案設定面板的螢幕擷取畫面，其中已醒目提示功能](images/openxr-features-img-03.png)

<span data-ttu-id="ac5d8-122">現在您可以按一下 [播放] 按鈕，以在 HoloLens 上的全像遠端應用程式中播放 Unity 應用程式。</span><span class="sxs-lookup"><span data-stu-id="ac5d8-122">Now you can click the “Play” button to play your Unity app into the Holographic Remoting app on your HoloLens.</span></span> <span data-ttu-id="ac5d8-123">您也可以 [將 Visual Studio 附加至 Unity](/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows) ，以在播放模式中進行 c # 腳本的調試。</span><span class="sxs-lookup"><span data-stu-id="ac5d8-123">You can also [attach Visual Studio to Unity](/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows) to debug C# scripts in the play mode.</span></span>

> [!NOTE]
> <span data-ttu-id="ac5d8-124">從0.1.0 版起，全像「全像」遠端執行時間不支援錨點，而 ARAnchorManager 功能將無法透過遠端處理。</span><span class="sxs-lookup"><span data-stu-id="ac5d8-124">As of version 0.1.0, the Holographic Remoting runtime doesn’t support Anchors, and ARAnchorManager functionalities will not work through remoting.</span></span>  <span data-ttu-id="ac5d8-125">這項功能會在未來的版本中推出。</span><span class="sxs-lookup"><span data-stu-id="ac5d8-125">This feature is coming in future releases.</span></span>

## <a name="unity-play-mode-with-holographic-remoting"></a><span data-ttu-id="ac5d8-126">使用全像攝影遠端的 Unity 播放模式</span><span class="sxs-lookup"><span data-stu-id="ac5d8-126">Unity Play Mode with Holographic Remoting</span></span>

<span data-ttu-id="ac5d8-127">使用全像全像全像，在您的電腦上的 Unity 編輯器中執行應用程式時，您可以在 HoloLens 上體驗您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="ac5d8-127">With Holographic Remoting, you can experience your app on the HoloLens while it runs in the Unity editor on your PC.</span></span> <span data-ttu-id="ac5d8-128">「注視」、「手勢」、「聲音」和「空間對應」輸入會從 HoloLens 傳送到您的電腦。</span><span class="sxs-lookup"><span data-stu-id="ac5d8-128">Gaze, gesture, voice, and spatial mapping input is sent from your HoloLens to your PC.</span></span> <span data-ttu-id="ac5d8-129">轉譯後的畫面會傳回給您的 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="ac5d8-129">Rendered frames are then sent back to your HoloLens.</span></span> <span data-ttu-id="ac5d8-130">這是快速偵測應用程式，而不需要建立及部署完整專案的絕佳方式。</span><span class="sxs-lookup"><span data-stu-id="ac5d8-130">This is a great way to quickly debug your app without building and deploying a full project.</span></span>
1. <span data-ttu-id="ac5d8-131">在 HoloLens 上，移至 **Microsoft Store** 並安裝全像 **[遠端播放機](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)** 應用程式。</span><span class="sxs-lookup"><span data-stu-id="ac5d8-131">On your HoloLens, go to the **Microsoft Store** and install the **[Holographic Remoting Player](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)** app.</span></span>
2. <span data-ttu-id="ac5d8-132">在您的 HoloLens 上，啟動全像 **Remoting 的播放** 程式應用程式。</span><span class="sxs-lookup"><span data-stu-id="ac5d8-132">On your HoloLens, start the **Holographic Remoting Player** app.</span></span>
3. <span data-ttu-id="ac5d8-133">在 Unity 中，移至 [ **視窗]** 功能表，展開 [ **XR** ] 子功能表，然後選取 [全像] **模擬**。</span><span class="sxs-lookup"><span data-stu-id="ac5d8-133">In Unity, go to the **Window** menu, expand the **XR** submenu, and select **Holographic Emulation**.</span></span>
4. <span data-ttu-id="ac5d8-134">將 **模擬模式** 設定為 [ **遠端裝置**]。</span><span class="sxs-lookup"><span data-stu-id="ac5d8-134">Set **Emulation Mode** to **Remote to Device**.</span></span>
5. <span data-ttu-id="ac5d8-135">針對 [ **遠端電腦**]，輸入 HOLOLENS 的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="ac5d8-135">For **Remote Machine**, enter the IP address of your HoloLens.</span></span>
6. <span data-ttu-id="ac5d8-136">選取 [連線]。</span><span class="sxs-lookup"><span data-stu-id="ac5d8-136">Select **Connect**.</span></span> <span data-ttu-id="ac5d8-137">您應該會看到 [連線 **狀態** ] 變更為 [ **已連接** ]，並在 HoloLens 中看到畫面空白。</span><span class="sxs-lookup"><span data-stu-id="ac5d8-137">You should see **Connection Status** change to **Connected** and see the screen go blank in the HoloLens.</span></span>
7. <span data-ttu-id="ac5d8-138">選取 [ **播放** ] 按鈕以啟動播放模式，並在您的 HoloLens 上體驗應用程式。</span><span class="sxs-lookup"><span data-stu-id="ac5d8-138">Select the **Play** button to start Play Mode and experience the app on your HoloLens.</span></span>

<span data-ttu-id="ac5d8-139">全像遠端處理需要快速的電腦和 Wi-Fi 連接。</span><span class="sxs-lookup"><span data-stu-id="ac5d8-139">Holographic Remoting requires a fast PC and Wi-Fi connection.</span></span> <span data-ttu-id="ac5d8-140">您可以在全像是「全像 [遠端播放機](../platform-capabilities-and-apis/holographic-remoting-player.md) 」檔中找到更多詳細資料。</span><span class="sxs-lookup"><span data-stu-id="ac5d8-140">You can find more details in the [Holographic Remoting Player](../platform-capabilities-and-apis/holographic-remoting-player.md) documentation.</span></span>

<span data-ttu-id="ac5d8-141">為了獲得最佳結果，請確定您的應用程式已正確設定 [焦點點](focus-point-in-unity.md)。</span><span class="sxs-lookup"><span data-stu-id="ac5d8-141">For best results, make sure your app properly sets the [focus point](focus-point-in-unity.md).</span></span> <span data-ttu-id="ac5d8-142">這可協助全像攝影的遠端處理，以最適合您的場景來調整您的無線連線延遲。</span><span class="sxs-lookup"><span data-stu-id="ac5d8-142">This helps Holographic Remoting to best adapt your scene to the latency of your wireless connection.</span></span>

## <a name="see-also"></a><span data-ttu-id="ac5d8-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ac5d8-143">See Also</span></span>
* [<span data-ttu-id="ac5d8-144">全像攝影遠端播放程式</span><span class="sxs-lookup"><span data-stu-id="ac5d8-144">Holographic Remoting Player</span></span>](../platform-capabilities-and-apis/holographic-remoting-player.md)
