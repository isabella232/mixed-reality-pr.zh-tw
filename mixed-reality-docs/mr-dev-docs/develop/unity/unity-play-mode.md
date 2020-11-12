---
title: Unity 播放模式
description: 在 Unity 編輯器中使用播放模式，以預覽裝置上的變更，而不需要部署應用程式。
author: jonmlyons
ms.author: jlyons
ms.date: 03/21/2018
ms.topic: article
keywords: Unity、遠端、全像全像全像攝影遠端播放
ms.openlocfilehash: 4239eba84bd94c0bdc596392fdf7a0c780778850
ms.sourcegitcommit: 520c69eb761ad6083b36f448bbcfab89e343e40d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/12/2020
ms.locfileid: "94549091"
---
# <a name="unity-play-mode"></a><span data-ttu-id="b2ca6-104">Unity 播放模式</span><span class="sxs-lookup"><span data-stu-id="b2ca6-104">Unity Play Mode</span></span>

<span data-ttu-id="b2ca6-105">處理 Unity 專案的快速方式是使用「播放模式」。</span><span class="sxs-lookup"><span data-stu-id="b2ca6-105">A fast way to work on your Unity project is to use "Play Mode".</span></span> <span data-ttu-id="b2ca6-106">這會在電腦的 Unity 編輯器中本機執行您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="b2ca6-106">This runs your app locally in the Unity editor on your PC.</span></span> <span data-ttu-id="b2ca6-107">Unity 使用全像的遠端處理功能，在實際 HoloLens 裝置上提供快速的預覽內容。</span><span class="sxs-lookup"><span data-stu-id="b2ca6-107">Unity uses Holographic Remoting to provide a fast way to preview your content on a real HoloLens device.</span></span> <span data-ttu-id="b2ca6-108">[播放] 模式也可以與連接至開發電腦的 Windows Mixed Reality 耳機一起使用。</span><span class="sxs-lookup"><span data-stu-id="b2ca6-108">Play Mode can also be used with a Windows Mixed Reality headset attached to your development PC.</span></span>

## <a name="unity-play-mode-with-holographic-remoting"></a><span data-ttu-id="b2ca6-109">使用全像攝影遠端的 Unity 播放模式</span><span class="sxs-lookup"><span data-stu-id="b2ca6-109">Unity Play Mode with Holographic Remoting</span></span>

<span data-ttu-id="b2ca6-110">使用全像全像攝影版，您可以在 HoloLens 上體驗您的應用程式，同時在您的電腦上的 Unity 編輯器中執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="b2ca6-110">With Holographic Remoting, you can experience your app on the HoloLens, while it runs in the Unity editor on your PC.</span></span> <span data-ttu-id="b2ca6-111">「注視」、「手勢」、「聲音」和「空間對應」輸入會從 HoloLens 傳送到您的電腦。</span><span class="sxs-lookup"><span data-stu-id="b2ca6-111">Gaze, gesture, voice, and spatial mapping input is sent from your HoloLens to your PC.</span></span> <span data-ttu-id="b2ca6-112">轉譯後的畫面會傳回給您的 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="b2ca6-112">Rendered frames are then sent back to your HoloLens.</span></span> <span data-ttu-id="b2ca6-113">這是快速偵測應用程式，而不需要建立及部署完整專案的絕佳方式。</span><span class="sxs-lookup"><span data-stu-id="b2ca6-113">This is a great way to quickly debug your app without building and deploying a full project.</span></span>
1. <span data-ttu-id="b2ca6-114">在 HoloLens 上，移至 **Microsoft Store** 並安裝全像 **[遠端播放機](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)** 應用程式。</span><span class="sxs-lookup"><span data-stu-id="b2ca6-114">On your HoloLens, go to the **Microsoft Store** and install the **[Holographic Remoting Player](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)** app.</span></span>
2. <span data-ttu-id="b2ca6-115">在您的 HoloLens 上，啟動全像 **Remoting 的播放** 程式應用程式。</span><span class="sxs-lookup"><span data-stu-id="b2ca6-115">On your HoloLens, start the **Holographic Remoting Player** app.</span></span>
3. <span data-ttu-id="b2ca6-116">在 Unity 中，移至 [ **視窗]** 功能表，展開 [ **XR** ] 子功能表，然後選取 [全像] **模擬** 。</span><span class="sxs-lookup"><span data-stu-id="b2ca6-116">In Unity, go to the **Window** menu, expand the **XR** sub-menu, and select **Holographic Emulation**.</span></span>
4. <span data-ttu-id="b2ca6-117">將 **模擬模式** 設定為 [ **遠端裝置** ]。</span><span class="sxs-lookup"><span data-stu-id="b2ca6-117">Set **Emulation Mode** to **Remote to Device**.</span></span>
5. <span data-ttu-id="b2ca6-118">針對 [ **遠端電腦** ]，輸入 HOLOLENS 的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="b2ca6-118">For **Remote Machine** , enter the IP address of your HoloLens.</span></span>
6. <span data-ttu-id="b2ca6-119">按一下 [ **連接** ]。</span><span class="sxs-lookup"><span data-stu-id="b2ca6-119">Click **Connect**.</span></span> <span data-ttu-id="b2ca6-120">您應該會看到 [連線 **狀態** ] 變更為 [ **已連接** ]，並在 HoloLens 中看到畫面空白。</span><span class="sxs-lookup"><span data-stu-id="b2ca6-120">You should see **Connection Status** change to **Connected** and see the screen go blank in the HoloLens.</span></span>
7. <span data-ttu-id="b2ca6-121">按一下 [ **播放** ] 按鈕以啟動播放模式，並在您的 HoloLens 上體驗應用程式。</span><span class="sxs-lookup"><span data-stu-id="b2ca6-121">Click the **Play** button to start Play Mode and experience the app on your HoloLens.</span></span>

<span data-ttu-id="b2ca6-122">全像遠端處理需要快速的電腦和 Wi-Fi 連接。</span><span class="sxs-lookup"><span data-stu-id="b2ca6-122">Holographic Remoting requires a fast PC and Wi-Fi connection.</span></span> <span data-ttu-id="b2ca6-123">如需完整的詳細資料，請參閱全像全像[遠端播放機](../platform-capabilities-and-apis/holographic-remoting-player.md)</span><span class="sxs-lookup"><span data-stu-id="b2ca6-123">See [Holographic Remoting Player](../platform-capabilities-and-apis/holographic-remoting-player.md) for full details.</span></span>

<span data-ttu-id="b2ca6-124">為了獲得最佳結果，請確定您的應用程式已正確設定 [焦點點](focus-point-in-unity.md)。</span><span class="sxs-lookup"><span data-stu-id="b2ca6-124">For best results, make sure your app properly sets the [focus point](focus-point-in-unity.md).</span></span> <span data-ttu-id="b2ca6-125">這可協助全像攝影的遠端處理，以最適合您的場景來調整您的無線連線延遲。</span><span class="sxs-lookup"><span data-stu-id="b2ca6-125">This helps Holographic Remoting to best adapt your scene to the latency of your wireless connection.</span></span>

## <a name="see-also"></a><span data-ttu-id="b2ca6-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b2ca6-126">See Also</span></span>
* [<span data-ttu-id="b2ca6-127">全像攝影遠端播放程式</span><span class="sxs-lookup"><span data-stu-id="b2ca6-127">Holographic Remoting Player</span></span>](../platform-capabilities-and-apis/holographic-remoting-player.md)
