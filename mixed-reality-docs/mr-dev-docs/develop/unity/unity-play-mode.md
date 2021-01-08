---
title: Unity 播放模式
description: 瞭解如何在 Unity 編輯器中使用播放模式，以預覽裝置上的應用程式變更，而不需要部署應用程式。
author: jonmlyons
ms.author: jlyons
ms.date: 03/21/2018
ms.topic: article
keywords: Unity、遠端處理、全像全像攝影、全像遠端播放機、HoloLens、混合現實耳機、windows mixed reality 耳機、虛擬實境耳機、unity play 模式
ms.openlocfilehash: 9f6c2cafd08fca8a5d60f3fcf5832ee74762e173
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009838"
---
# <a name="unity-play-mode"></a><span data-ttu-id="0bf6e-104">Unity 播放模式</span><span class="sxs-lookup"><span data-stu-id="0bf6e-104">Unity Play Mode</span></span>

<span data-ttu-id="0bf6e-105">處理 Unity 專案的快速方式是使用「播放模式」，這會在本機電腦上的 Unity 編輯器中執行您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="0bf6e-105">A fast way to work on your Unity project is to use "Play Mode", which runs your app locally in the Unity editor on your PC.</span></span> <span data-ttu-id="0bf6e-106">Unity 使用全像的遠端處理功能，在實際 HoloLens 裝置上提供快速的預覽內容。</span><span class="sxs-lookup"><span data-stu-id="0bf6e-106">Unity uses Holographic Remoting to provide a fast way to preview your content on a real HoloLens device.</span></span> <span data-ttu-id="0bf6e-107">[播放] 模式也可以與連接至開發電腦的 Windows Mixed Reality 耳機一起使用。</span><span class="sxs-lookup"><span data-stu-id="0bf6e-107">Play Mode can also be used with a Windows Mixed Reality headset attached to your development PC.</span></span>

## <a name="unity-play-mode-with-holographic-remoting"></a><span data-ttu-id="0bf6e-108">使用全像攝影遠端的 Unity 播放模式</span><span class="sxs-lookup"><span data-stu-id="0bf6e-108">Unity Play Mode with Holographic Remoting</span></span>

<span data-ttu-id="0bf6e-109">使用全像全像全像，在您的電腦上的 Unity 編輯器中執行應用程式時，您可以在 HoloLens 上體驗您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="0bf6e-109">With Holographic Remoting, you can experience your app on the HoloLens while it runs in the Unity editor on your PC.</span></span> <span data-ttu-id="0bf6e-110">「注視」、「手勢」、「聲音」和「空間對應」輸入會從 HoloLens 傳送到您的電腦。</span><span class="sxs-lookup"><span data-stu-id="0bf6e-110">Gaze, gesture, voice, and spatial mapping input is sent from your HoloLens to your PC.</span></span> <span data-ttu-id="0bf6e-111">轉譯後的畫面會傳回給您的 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="0bf6e-111">Rendered frames are then sent back to your HoloLens.</span></span> <span data-ttu-id="0bf6e-112">這是快速偵測應用程式，而不需要建立及部署完整專案的絕佳方式。</span><span class="sxs-lookup"><span data-stu-id="0bf6e-112">This is a great way to quickly debug your app without building and deploying a full project.</span></span>
1. <span data-ttu-id="0bf6e-113">在 HoloLens 上，移至 **Microsoft Store** 並安裝全像 **[遠端播放機](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)** 應用程式。</span><span class="sxs-lookup"><span data-stu-id="0bf6e-113">On your HoloLens, go to the **Microsoft Store** and install the **[Holographic Remoting Player](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)** app.</span></span>
2. <span data-ttu-id="0bf6e-114">在您的 HoloLens 上，啟動全像 **Remoting 的播放** 程式應用程式。</span><span class="sxs-lookup"><span data-stu-id="0bf6e-114">On your HoloLens, start the **Holographic Remoting Player** app.</span></span>
3. <span data-ttu-id="0bf6e-115">在 Unity 中，移至 [ **視窗]** 功能表，展開 [ **XR** ] 子功能表，然後選取 [全像] **模擬**。</span><span class="sxs-lookup"><span data-stu-id="0bf6e-115">In Unity, go to the **Window** menu, expand the **XR** submenu, and select **Holographic Emulation**.</span></span>
4. <span data-ttu-id="0bf6e-116">將 **模擬模式** 設定為 [ **遠端裝置**]。</span><span class="sxs-lookup"><span data-stu-id="0bf6e-116">Set **Emulation Mode** to **Remote to Device**.</span></span>
5. <span data-ttu-id="0bf6e-117">針對 [ **遠端電腦**]，輸入 HOLOLENS 的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="0bf6e-117">For **Remote Machine**, enter the IP address of your HoloLens.</span></span>
6. <span data-ttu-id="0bf6e-118">選取 [連接]。</span><span class="sxs-lookup"><span data-stu-id="0bf6e-118">Select **Connect**.</span></span> <span data-ttu-id="0bf6e-119">您應該會看到 [連線 **狀態** ] 變更為 [ **已連接** ]，並在 HoloLens 中看到畫面空白。</span><span class="sxs-lookup"><span data-stu-id="0bf6e-119">You should see **Connection Status** change to **Connected** and see the screen go blank in the HoloLens.</span></span>
7. <span data-ttu-id="0bf6e-120">選取 [ **播放** ] 按鈕以啟動播放模式，並在您的 HoloLens 上體驗應用程式。</span><span class="sxs-lookup"><span data-stu-id="0bf6e-120">Select the **Play** button to start Play Mode and experience the app on your HoloLens.</span></span>

<span data-ttu-id="0bf6e-121">全像遠端處理需要快速的電腦和 Wi-Fi 連接。</span><span class="sxs-lookup"><span data-stu-id="0bf6e-121">Holographic Remoting requires a fast PC and Wi-Fi connection.</span></span> <span data-ttu-id="0bf6e-122">您可以在全像是「全像 [遠端播放機](../platform-capabilities-and-apis/holographic-remoting-player.md) 」檔中找到更多詳細資料。</span><span class="sxs-lookup"><span data-stu-id="0bf6e-122">You can find more details in the [Holographic Remoting Player](../platform-capabilities-and-apis/holographic-remoting-player.md) documentation.</span></span>

<span data-ttu-id="0bf6e-123">為了獲得最佳結果，請確定您的應用程式已正確設定 [焦點點](focus-point-in-unity.md)。</span><span class="sxs-lookup"><span data-stu-id="0bf6e-123">For best results, make sure your app properly sets the [focus point](focus-point-in-unity.md).</span></span> <span data-ttu-id="0bf6e-124">這可協助全像攝影的遠端處理，以最適合您的場景來調整您的無線連線延遲。</span><span class="sxs-lookup"><span data-stu-id="0bf6e-124">This helps Holographic Remoting to best adapt your scene to the latency of your wireless connection.</span></span>

## <a name="see-also"></a><span data-ttu-id="0bf6e-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0bf6e-125">See Also</span></span>
* [<span data-ttu-id="0bf6e-126">全像攝影遠端播放程式</span><span class="sxs-lookup"><span data-stu-id="0bf6e-126">Holographic Remoting Player</span></span>](../platform-capabilities-and-apis/holographic-remoting-player.md)
