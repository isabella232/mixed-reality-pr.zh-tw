---
title: Unity 播放模式
description: 瞭解如何在 Unity 編輯器中使用播放模式，以預覽裝置上的應用程式變更，而不需要部署應用程式。
author: keveleigh
ms.author: kurtie
ms.date: 05/21/2021
ms.topic: article
keywords: Unity、遠端處理、全像全像攝影、全像遠端播放機、HoloLens、混合現實耳機、windows mixed reality 耳機、虛擬實境耳機、unity play 模式
ms.openlocfilehash: b998233fda34beee0c98795a1efa2c86a53541ba
ms.sourcegitcommit: bdf4babd13e021f41fb04cdb3611bb759bd77537
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2021
ms.locfileid: "112392287"
---
# <a name="unity-play-mode"></a><span data-ttu-id="1890a-104">Unity 播放模式</span><span class="sxs-lookup"><span data-stu-id="1890a-104">Unity Play Mode</span></span>

<span data-ttu-id="1890a-105">處理 Unity 專案的快速方式是使用「播放模式」，這會在本機電腦上的 Unity 編輯器中執行您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="1890a-105">A fast way to work on your Unity project is to use "Play Mode", which runs your app locally in the Unity editor on your PC.</span></span> <span data-ttu-id="1890a-106">Unity 使用全像的遠端處理功能，在實際 HoloLens 裝置上提供快速的預覽內容。</span><span class="sxs-lookup"><span data-stu-id="1890a-106">Unity uses Holographic Remoting to provide a fast way to preview your content on a real HoloLens device.</span></span> <span data-ttu-id="1890a-107">[播放] 模式也可以與連接至開發電腦的 Windows Mixed Reality 耳機一起使用。</span><span class="sxs-lookup"><span data-stu-id="1890a-107">Play Mode can also be used with a Windows Mixed Reality headset attached to your development PC.</span></span>

## <a name="holographic-remoting-setup"></a><span data-ttu-id="1890a-108">全像遠端設定</span><span class="sxs-lookup"><span data-stu-id="1890a-108">Holographic Remoting setup</span></span>

1. <span data-ttu-id="1890a-109">首先，您必須從 HoloLens 2 上的 Microsoft Store 安裝全像[遠端播放機應用程式](https://www.microsoft.com/store/productId/9NBLGGH4SV40)</span><span class="sxs-lookup"><span data-stu-id="1890a-109">First, you need to [install the Holographic Remoting Player app](https://www.microsoft.com/store/productId/9NBLGGH4SV40) from the Microsoft Store on your HoloLens 2</span></span>
2. <span data-ttu-id="1890a-110">在 HoloLens 2 上執行全像遠端播放播放程式應用程式，您會看到要連接的版本號碼和 IP 位址</span><span class="sxs-lookup"><span data-stu-id="1890a-110">Run the Holographic Remoting Player app on HoloLens 2 and you'll see the version number and IP address to connect to</span></span>
    * <span data-ttu-id="1890a-111">您將需要2.4 或更新版本才能使用 OpenXR 外掛程式</span><span class="sxs-lookup"><span data-stu-id="1890a-111">You'll need v2.4 or later to work with the OpenXR plugin</span></span>

    ![HoloLens 中執行的全像 Remoting 播放程式的螢幕擷取畫面](images/openxr-features-img-01.png)

## <a name="unity-play-mode-with-holographic-remoting"></a><span data-ttu-id="1890a-113">使用全像攝影遠端的 Unity 播放模式</span><span class="sxs-lookup"><span data-stu-id="1890a-113">Unity Play Mode with Holographic Remoting</span></span>

<span data-ttu-id="1890a-114">使用全像全像全像，在您的電腦上的 Unity 編輯器中執行應用程式時，您可以在 HoloLens 上體驗您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="1890a-114">With Holographic Remoting, you can experience your app on the HoloLens while it runs in the Unity editor on your PC.</span></span> <span data-ttu-id="1890a-115">「注視」、「手勢」、「聲音」和「空間對應」輸入會從 HoloLens 傳送到您的電腦。</span><span class="sxs-lookup"><span data-stu-id="1890a-115">Gaze, gesture, voice, and spatial mapping input is sent from your HoloLens to your PC.</span></span> <span data-ttu-id="1890a-116">轉譯後的畫面會傳回給您的 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="1890a-116">Rendered frames are then sent back to your HoloLens.</span></span> <span data-ttu-id="1890a-117">這是快速偵測應用程式，而不需要建立及部署完整專案的絕佳方式。</span><span class="sxs-lookup"><span data-stu-id="1890a-117">This is a great way to quickly debug your app without building and deploying a full project.</span></span>

[!INCLUDE[](includes/unity-play-mode.md)]

<span data-ttu-id="1890a-118">全像遠端處理需要快速的電腦和 Wi-Fi 連接。</span><span class="sxs-lookup"><span data-stu-id="1890a-118">Holographic Remoting requires a fast PC and Wi-Fi connection.</span></span> <span data-ttu-id="1890a-119">您可以在全像是「全像 [遠端播放機](../platform-capabilities-and-apis/holographic-remoting-player.md) 」檔中找到更多詳細資料。</span><span class="sxs-lookup"><span data-stu-id="1890a-119">You can find more details in the [Holographic Remoting Player](../platform-capabilities-and-apis/holographic-remoting-player.md) documentation.</span></span>

<span data-ttu-id="1890a-120">為了獲得最佳結果，請確定您的應用程式已正確設定 [焦點點](focus-point-in-unity.md)。</span><span class="sxs-lookup"><span data-stu-id="1890a-120">For best results, make sure your app properly sets the [focus point](focus-point-in-unity.md).</span></span> <span data-ttu-id="1890a-121">這可協助全像攝影的遠端處理，以最適合您的場景來調整您的無線連線延遲。</span><span class="sxs-lookup"><span data-stu-id="1890a-121">This helps Holographic Remoting to best adapt your scene to the latency of your wireless connection.</span></span>

## <a name="see-also"></a><span data-ttu-id="1890a-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1890a-122">See Also</span></span>

* [<span data-ttu-id="1890a-123">全像攝影遠端播放程式</span><span class="sxs-lookup"><span data-stu-id="1890a-123">Holographic Remoting Player</span></span>](../platform-capabilities-and-apis/holographic-remoting-player.md)
