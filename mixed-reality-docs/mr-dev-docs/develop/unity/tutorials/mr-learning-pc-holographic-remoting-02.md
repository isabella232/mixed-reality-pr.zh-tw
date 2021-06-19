---
title: 建立全像攝影遠端處理電腦應用程式
description: 完成此課程，以了解如何建立電腦應用程式，以遠端處理從您的電腦到 HoloLens 2 的混合實境體驗。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens, 電腦全像攝影遠端處理, Visual Studio
ms.localizationpriority: high
ms.openlocfilehash: ca0efe13acac4408a05ab89eb98b508e9993c5a4
ms.sourcegitcommit: bdf4babd13e021f41fb04cdb3611bb759bd77537
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2021
ms.locfileid: "112392495"
---
# <a name="2-creating-a-holographic-remoting-pc-application"></a><span data-ttu-id="e895e-104">2.建立全像攝影遠端處理電腦應用程式</span><span class="sxs-lookup"><span data-stu-id="e895e-104">2. Creating a Holographic Remoting PC application</span></span>

<span data-ttu-id="e895e-105">在本教學課程中，您將了解如何建立電腦應用程式來進行全像攝影遠端處理，並在任何時間點連線 HoloLens 2，進而提供一種在混合實境中將 3D 內容視覺化的方式。</span><span class="sxs-lookup"><span data-stu-id="e895e-105">In this tutorial, you will learn how to create a PC app for Holographic Remoting and connect to HoloLens 2 at any point, providing a way to visualize 3D content in mixed reality.</span></span>

## <a name="objectives"></a><span data-ttu-id="e895e-106">目標</span><span class="sxs-lookup"><span data-stu-id="e895e-106">Objectives</span></span>

* <span data-ttu-id="e895e-107">設定適用於全像攝影遠端處理的 Unity</span><span class="sxs-lookup"><span data-stu-id="e895e-107">Configure Unity for Holographic Remoting</span></span>
* <span data-ttu-id="e895e-108">了解如何使用 Visual Studio 建立及部署應用程式</span><span class="sxs-lookup"><span data-stu-id="e895e-108">Learn how to build and deploy the application with Visual Studio</span></span>
* <span data-ttu-id="e895e-109">開發全像攝影遠端處理應用程式並連線到 HoloLens</span><span class="sxs-lookup"><span data-stu-id="e895e-109">Developing Holographic Remoting application and connecting to HoloLens</span></span>

## <a name="configuring-the-capabilities"></a><span data-ttu-id="e895e-110">設定功能</span><span class="sxs-lookup"><span data-stu-id="e895e-110">Configuring the capabilities</span></span>

<span data-ttu-id="e895e-111">在 [ **專案設定** ] 視窗中，展開 [ **發行設定**]，向下滾動至 [功能] 區段，並選取 [除了現有的功能之外] 下顯示的 [功能] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="e895e-111">In the **Project Settings** window, expand the **Publishing Settings**, scroll down to the Capabilities section and select the below-shown capability checkbox in addition to the existing capabilities.</span></span>

* <span data-ttu-id="e895e-112">網際網路用戶端伺服器</span><span class="sxs-lookup"><span data-stu-id="e895e-112">Internet Clint server</span></span>
* <span data-ttu-id="e895e-113">私人網路用戶端伺服器</span><span class="sxs-lookup"><span data-stu-id="e895e-113">Private Network Client Server</span></span>

![啟用功能](images/mrlearning-pc-holographic-remoting/tutorial2-section0-step1-1.png)

[!INCLUDE[](includes/configuring-scene-for-holographic-remoting.md)]

## <a name="build-your-application-to-pc"></a><span data-ttu-id="e895e-115">在電腦中建置應用程式</span><span class="sxs-lookup"><span data-stu-id="e895e-115">Build your application to PC</span></span>

<span data-ttu-id="e895e-116">您的全像攝影遠端處理應用程式現在已準備好在電腦上建置。</span><span class="sxs-lookup"><span data-stu-id="e895e-116">Your Holographic Remoting app is now ready to build on your PC.</span></span> <span data-ttu-id="e895e-117">請遵循下列步驟來進行這些變更，以將此應用程式建立到您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="e895e-117">Follow the below steps and make these changes to build this application on to your PC.</span></span>

[!INCLUDE[](includes/build-your-application-to-pc.md)]

## <a name="testing-holographic-remoting-remote-application"></a><span data-ttu-id="e895e-118">測試全像攝影遠端處理應用程式</span><span class="sxs-lookup"><span data-stu-id="e895e-118">Testing Holographic Remoting remote application</span></span>

<span data-ttu-id="e895e-119">若要將您的電腦應用程式連線到 HoloLens 2，請遵循下列程序：</span><span class="sxs-lookup"><span data-stu-id="e895e-119">To connect your PC application to your HoloLens 2, follow the below process:</span></span>

### <a name="1-install-the-remoting-player-application-on-hololens-2-device"></a><span data-ttu-id="e895e-120">1.在 HoloLens 2 裝置上安裝遠端播放程式應用程式</span><span class="sxs-lookup"><span data-stu-id="e895e-120">1. Install the Remoting Player application on HoloLens 2 device</span></span>

* <span data-ttu-id="e895e-121">在您的 HoloLens 2 上，瀏覽市集應用程式並搜尋「遠端播放程式」。</span><span class="sxs-lookup"><span data-stu-id="e895e-121">On your HoloLens 2, visit the Store app and search for "**Remoting Player**."</span></span>
* <span data-ttu-id="e895e-122">選取 **遠端處理播放程式** 應用程式。</span><span class="sxs-lookup"><span data-stu-id="e895e-122">Select the **Remoting Player** app.</span></span>
* <span data-ttu-id="e895e-123">請點選 [安裝] 來下載並安裝應用程式。</span><span class="sxs-lookup"><span data-stu-id="e895e-123">Tap **Install** to download and install the app.</span></span>

### <a name="2-connect-the-holographic-remoting-pc-app-to-the-remoting-player"></a><span data-ttu-id="e895e-124">2.將全像攝影遠端處理電腦應用程式連線到遠端播放程式</span><span class="sxs-lookup"><span data-stu-id="e895e-124">2. Connect the Holographic remoting PC app to the Remoting Player</span></span>

* <span data-ttu-id="e895e-125">啟動 HoloLens 上的 **遠端播放程式**。</span><span class="sxs-lookup"><span data-stu-id="e895e-125">Start the **Remoting Player** on your HoloLens.</span></span>
* <span data-ttu-id="e895e-126">記下 HoloLens 的 **IP 位址**。</span><span class="sxs-lookup"><span data-stu-id="e895e-126">Take note of the HoloLens **IP address**.</span></span> <span data-ttu-id="e895e-127">**遠端播放程式** 會在啟動時，將其顯示為全像投影。</span><span class="sxs-lookup"><span data-stu-id="e895e-127">It will be displayed as a hologram by the **Remoting Player** as soon as it launches.</span></span>
* <span data-ttu-id="e895e-128">在您的電腦上開啟全像攝影遠端處理電腦應用程式。</span><span class="sxs-lookup"><span data-stu-id="e895e-128">Open the Holographic Remoting PC application on your PC.</span></span>
* <span data-ttu-id="e895e-129">啟動應用程式之後，輸入 **IP 位址**，然後按一下 [連線] 按鈕以進行連線。</span><span class="sxs-lookup"><span data-stu-id="e895e-129">Once the application is launched, enter the **IP address** and click on the **Connect**  button to connect.</span></span>

## <a name="congratulations"></a><span data-ttu-id="e895e-130">恭喜！</span><span class="sxs-lookup"><span data-stu-id="e895e-130">Congratulations</span></span>

<span data-ttu-id="e895e-131">在本教學課程中，您已了解如何建立全像攝影遠端處理應用程式，並在任何時間點連線 HoloLens 2，進而提供一種在混合實境中將 3D 內容視覺化的方式。</span><span class="sxs-lookup"><span data-stu-id="e895e-131">In this tutorial, you learned how to create a Holographic Remoting remote app and connect to HoloLens 2 at any point, providing a way to visualize 3D content in mixed reality.</span></span> <span data-ttu-id="e895e-132">當 HoloLens 連線到全像攝影遠端處理電腦應用程式之後，您應該會看到混合實境體驗串流至您的 HoloLens 2 裝置。</span><span class="sxs-lookup"><span data-stu-id="e895e-132">Once the HoloLens connected to the Holographic Remoting PC application, you should see the mixed reality experience streaming into your HoloLens 2 device.</span></span>
