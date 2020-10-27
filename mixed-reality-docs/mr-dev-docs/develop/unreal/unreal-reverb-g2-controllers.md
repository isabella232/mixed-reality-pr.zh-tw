---
title: Unreal 中的 HP 回音 G2 控制器
description: 在 OpenXR 和 SteamVR 中使用 HP 回音 G2 控制器的指示
author: hferrone
ms.author: jacksonf
ms.date: 10/9/2020
ms.topic: article
keywords: Unreal、Unreal Engine 4、UE4、回音、回音、hp-ux、HP 回音、mixed reality、開發、運動控制器、使用者輸入、功能、新專案、模擬器、檔、指南、功能、全像遊戲開發
ms.openlocfilehash: c9d3ea3a8dd52ed0712f9df5c1a789121a68fd35
ms.sourcegitcommit: 4bb5544a0c74ac4e9766bab3401c9b30ee170a71
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2020
ms.locfileid: "92638635"
---
# <a name="hp-reverb-g2-controllers-in-unreal"></a><span data-ttu-id="4177d-104">Unreal 中的 HP 回音 G2 控制器</span><span class="sxs-lookup"><span data-stu-id="4177d-104">HP Reverb G2 Controllers in Unreal</span></span> 

## <a name="getting-started"></a><span data-ttu-id="4177d-105">開始使用</span><span class="sxs-lookup"><span data-stu-id="4177d-105">Getting started</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4177d-106">需要有 Unreal Engine 4.26 及 OpenXR 或 SteamVR，才能存取 hp 運動控制器外掛程式，您必須使用 HP 的「回音」 G2 控制器。</span><span class="sxs-lookup"><span data-stu-id="4177d-106">Unreal Engine 4.26 and either OpenXR or SteamVR is required to access the HP Motion Controller plugin you'll need to work with the HP Reverb G2 controllers.</span></span>

[!INCLUDE[](includes/tabs-g2-controllers-in-unreal.md)]

## <a name="porting-an-existing-openxr-app"></a><span data-ttu-id="4177d-107">移植現有的 OpenXR 應用程式</span><span class="sxs-lookup"><span data-stu-id="4177d-107">Porting an existing OpenXR app</span></span> 

<span data-ttu-id="4177d-108">如果沒有任何控制器系結存在於 HP Mixed Reality 控制器的遊戲中，OpenXR 執行時間會嘗試將現有的系結重新對應到主動控制器。</span><span class="sxs-lookup"><span data-stu-id="4177d-108">If no controller bindings exist in the game for the HP Mixed Reality Controller, the OpenXR runtime will attempt to remap the existing bindings to the active controller.</span></span>  <span data-ttu-id="4177d-109">在此情況下，遊戲已 Oculus 觸控系結，而且沒有任何 HP Mixed Reality 控制器系結。</span><span class="sxs-lookup"><span data-stu-id="4177d-109">In this case, the game has Oculus Touch bindings and no HP Mixed Reality Controller bindings.</span></span>

![沒有控制器系結存在時重新對應現有的系結](images/reverb-g2-img-04.png)

<span data-ttu-id="4177d-111">這些事件仍然會引發，但是如果遊戲需要使用控制器專屬系結，例如右鍵的功能表按鈕，就必須使用 HP Mixed Reality 互動設定檔。</span><span class="sxs-lookup"><span data-stu-id="4177d-111">The events will still fire, but if the game needs to make use of controller specific bindings, like the right menu button, the HP Mixed Reality interaction profile must be used.</span></span>  <span data-ttu-id="4177d-112">您可以針對每個動作指定多個控制器系結，以更妥善支援不同的裝置。</span><span class="sxs-lookup"><span data-stu-id="4177d-112">Multiple controller bindings can be specified per action to better support different devices.</span></span>
   
![使用多個控制器系結](images/reverb-g2-img-05.png)

## <a name="adding-input-action-mappings"></a><span data-ttu-id="4177d-114">新增輸入動作對應</span><span class="sxs-lookup"><span data-stu-id="4177d-114">Adding input action mappings</span></span> 

<span data-ttu-id="4177d-115">定義新的動作，並對應至 [HP Mixed Reality 控制器] 區段中的其中一個按鍵。</span><span class="sxs-lookup"><span data-stu-id="4177d-115">Define a new action and map to one of the key presses in the HP Mixed Reality Controller section.</span></span>

![定義新的動作和對應](images/reverb-g2-img-02.png)

<span data-ttu-id="4177d-117">HP 的殘響 G2 控制器也有類比底框，可用於與「壓縮軸」系結的軸對應中。</span><span class="sxs-lookup"><span data-stu-id="4177d-117">The HP Reverb G2 controller also has an analog grip, which can be used in the axis mappings with the “Squeeze Axis” binding.</span></span>  <span data-ttu-id="4177d-118">有個別的壓縮系結，當您完全按下 [框] 按鈕時，應該將其用於動作對應。</span><span class="sxs-lookup"><span data-stu-id="4177d-118">There is a separate Squeeze binding, which should be used for action mappings when the grip button is fully pressed.</span></span> 

![使用壓縮軸系結](images/reverb-g2-img-03.png)

## <a name="adding-input-events"></a><span data-ttu-id="4177d-120">加入輸入事件</span><span class="sxs-lookup"><span data-stu-id="4177d-120">Adding input events</span></span>

<span data-ttu-id="4177d-121">在藍圖上按一下滑鼠右鍵，並從輸入系統中搜尋新的動作名稱，以新增這些動作的事件。</span><span class="sxs-lookup"><span data-stu-id="4177d-121">Right click on a Blueprint and search for the new action names from the input system to add events for these actions.</span></span>  <span data-ttu-id="4177d-122">在此，藍圖會使用輸出字串來回應事件，並輸出目前的按鈕和軸狀態。</span><span class="sxs-lookup"><span data-stu-id="4177d-122">Here the Blueprint is responding to the events with a print string outputting the current button and axis state.</span></span>

![藍圖會回應事件並輸出目前的按鈕和軸狀態](images/reverb-g2-img-06.png)

### <a name="using-input"></a><span data-ttu-id="4177d-124">使用輸入</span><span class="sxs-lookup"><span data-stu-id="4177d-124">Using input</span></span> 

[!INCLUDE[](includes/tabs-g2-controller-mapping-in-unreal.md)]

## <a name="see-also"></a><span data-ttu-id="4177d-125">請參閱</span><span class="sxs-lookup"><span data-stu-id="4177d-125">See also</span></span>
* [<span data-ttu-id="4177d-126">SteamVR 輸入</span><span class="sxs-lookup"><span data-stu-id="4177d-126">SteamVR Input</span></span>](https://docs.unrealengine.com/Platforms/VR/SteamVR/HowTo/SteamVRInput/index.html)
* [<span data-ttu-id="4177d-127">使用 SteamVR 搭配 Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="4177d-127">Using SteamVR with Windows Mixed Reality</span></span>](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/using-steamvr-with-windows-mixed-reality)
* [<span data-ttu-id="4177d-128">Unreal Player 攝影機</span><span class="sxs-lookup"><span data-stu-id="4177d-128">Unreal Player Camera</span></span>](https://docs.unrealengine.com/Programming/Tutorials/PlayerCamera/3/index.html)