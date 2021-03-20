---
title: 詞彙
description: MRTK 中的不同輸入系統。
author: cDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、輸入、
ms.openlocfilehash: d06e37185b44796d2a95645f78c735e849bab7b4
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104682401"
---
# <a name="input-system"></a><span data-ttu-id="06f22-104">輸入系統</span><span class="sxs-lookup"><span data-stu-id="06f22-104">Input system</span></span>

<span data-ttu-id="06f22-105">輸入系統是 MRTK 所提供的所有功能的其中一個最大系統。</span><span class="sxs-lookup"><span data-stu-id="06f22-105">The input system is one of the largest systems out of all features offered by the MRTK.</span></span>
<span data-ttu-id="06f22-106">工具組內的許多專案都是以 it 為基礎 (指標、焦點、prefabs) 。</span><span class="sxs-lookup"><span data-stu-id="06f22-106">So many things within the toolkit build on top of it (pointers, focus, prefabs).</span></span> <span data-ttu-id="06f22-107">輸入系統內的程式碼可讓您進行自然互動，例如跨平臺抓取和旋轉。</span><span class="sxs-lookup"><span data-stu-id="06f22-107">The code within the input system is what allows for natural interactions like grab and rotate across platforms.</span></span>

<span data-ttu-id="06f22-108">輸入系統有一些值得定義的術語：</span><span class="sxs-lookup"><span data-stu-id="06f22-108">The input system has some of its own terminology that are worth defining:</span></span>

- <span data-ttu-id="06f22-109">**資料提供者**</span><span class="sxs-lookup"><span data-stu-id="06f22-109">**Data providers**</span></span>

    <span data-ttu-id="06f22-110">輸入設定檔中的輸入設定會參考稱為資料提供者的實體，另一個描述這些專案的單字是裝置管理員。</span><span class="sxs-lookup"><span data-stu-id="06f22-110">The input settings in the input profile have references to entities known as data providers - another word that describes these are device managers.</span></span> <span data-ttu-id="06f22-111">這些元件的工作是藉由與特定基礎系統互動來擴充 MRTK 輸入系統。</span><span class="sxs-lookup"><span data-stu-id="06f22-111">These are components whose job is to extend the MRTK input system by interfacing with a specific underlying system.</span></span> <span data-ttu-id="06f22-112">提供者的範例是 Windows Mixed Reality 的提供者，它的工作是要與基礎 Windows Mixed Reality Api 溝通，然後將這些 Api 的資料轉譯為下面的 MRTK 特定輸入概念。</span><span class="sxs-lookup"><span data-stu-id="06f22-112">An example of a provider is the Windows Mixed Reality provider, whose job it is to talk with the underlying Windows Mixed Reality APIs and then translate the data from those APIs into MRTK-specific input concepts below.</span></span> <span data-ttu-id="06f22-113">另一個範例是 OpenVR 提供者 (其作業是與 Unity 抽象版本的 OpenVR Api 溝通，然後將該資料轉譯成 MRTK 輸入概念) 。</span><span class="sxs-lookup"><span data-stu-id="06f22-113">Another example would be the OpenVR provider (whose job it is to talk to Unity-abstracted version of OpenVR APIs and then translate that data into MRTK input concepts).</span></span>

- <span data-ttu-id="06f22-114">**控制器**</span><span class="sxs-lookup"><span data-stu-id="06f22-114">**Controller**</span></span>

    <span data-ttu-id="06f22-115">實體控制器的表示 (是否為6度自由度控制器、具有手勢支援的 HoloLens 1 樣式的手、是否有完全明確陳述的手、閏運動控制器等 ) 。</span><span class="sxs-lookup"><span data-stu-id="06f22-115">A representation of a physical controller (whether it's a 6-degree-of-freedom controller, a HoloLens 1-style hand with gesture support, a fully articulated hand, a leap motion controller, etc.).</span></span> <span data-ttu-id="06f22-116">控制器是由裝置管理員所產生 (亦即，WMR 裝置管理員會產生一個控制器，並在看到有明確的手) 時管理其存留期。</span><span class="sxs-lookup"><span data-stu-id="06f22-116">Controllers are spawned by device managers (i.e. the WMR device manager will spawn a controller and manage its lifetime when it sees an articulated hand coming into existence).</span></span>

- <span data-ttu-id="06f22-117">**指標**</span><span class="sxs-lookup"><span data-stu-id="06f22-117">**Pointer**</span></span>

    <span data-ttu-id="06f22-118">控制器會使用指標來與遊戲物件互動。</span><span class="sxs-lookup"><span data-stu-id="06f22-118">Controllers use pointers to interact with game objects.</span></span> <span data-ttu-id="06f22-119">例如，近距離互動指標負責偵測 (是控制器) 接近的物件，這些物件會將本身公告為支援「接近互動」。</span><span class="sxs-lookup"><span data-stu-id="06f22-119">For example, the near interaction pointer is responsible for detecting when the hand (which is a controller) is close to objects that advertise themselves as supporting 'near interaction'.</span></span> <span data-ttu-id="06f22-120">指標的其他範例是遙傳或遠指標 (也就是使用最多 raycasts 的 shell 手光線指標) ，與使用者的距離長度相比，可使用的內容遠超過手臂長度。</span><span class="sxs-lookup"><span data-stu-id="06f22-120">Other examples for pointers are teleportation or far pointers (i.e. the shell hand ray pointer) that use far raycasts to engage with content that is longer than arms-length from the user.</span></span>

    <span data-ttu-id="06f22-121">指標是由裝置管理員所建立，然後附加至輸入來源。</span><span class="sxs-lookup"><span data-stu-id="06f22-121">Pointers are created by the device manager and then attached to an input source.</span></span> <span data-ttu-id="06f22-122">若要取得控制器的所有指標，請執行： `controller.InputSource.Pointers`</span><span class="sxs-lookup"><span data-stu-id="06f22-122">To get all of the pointers for a controller, do: `controller.InputSource.Pointers`</span></span>

    <span data-ttu-id="06f22-123">請注意，控制器可以同時與許多不同的指標相關聯。</span><span class="sxs-lookup"><span data-stu-id="06f22-123">Note that a controller can be associated with many different pointers at the same time.</span></span> <span data-ttu-id="06f22-124">為了確保這不會 devolve 混亂，有一個指標中繼程式可控制哪些指標可供使用 (例如，當偵測到接近互動時，中繼程式將會停用目前的互動指標) 。</span><span class="sxs-lookup"><span data-stu-id="06f22-124">In order to ensure that this doesn't devolve into chaos, there is a pointer mediator which controls which pointers are allowed to be active (for example, the mediator will disable far interaction pointers when near interaction is detected).</span></span>

- <span data-ttu-id="06f22-125">**重點**</span><span class="sxs-lookup"><span data-stu-id="06f22-125">**Focus**</span></span>

    <span data-ttu-id="06f22-126">指標事件會傳送至 **焦點** 的物件。</span><span class="sxs-lookup"><span data-stu-id="06f22-126">Pointer events are sent to objects in **focus**.</span></span> <span data-ttu-id="06f22-127">焦點選取專案將依指標類型而有所不同;手光線指標會使用 raycasts，而指標會使用 spherecasts。</span><span class="sxs-lookup"><span data-stu-id="06f22-127">Focus selection will vary by pointer type; a hand ray pointer will use raycasts, while a poke pointer will use spherecasts.</span></span> <span data-ttu-id="06f22-128">物件必須執行 IMixedRealityFocusHandler 以取得焦點。</span><span class="sxs-lookup"><span data-stu-id="06f22-128">An object must implement IMixedRealityFocusHandler to receive focus.</span></span> <span data-ttu-id="06f22-129">您可以全域註冊物件以接收未篩選的指標事件，但不建議使用此方法。</span><span class="sxs-lookup"><span data-stu-id="06f22-129">It's possible to globally register an object to receive unfiltered pointer events, but this approach is not recommended.</span></span>

    <span data-ttu-id="06f22-130">用來更新物件焦點的元件是 [FocusProvider](xref:Microsoft.MixedReality.Toolkit.Input.FocusProvider)</span><span class="sxs-lookup"><span data-stu-id="06f22-130">The component that updates which objects are in focus is the [FocusProvider](xref:Microsoft.MixedReality.Toolkit.Input.FocusProvider)</span></span>

- <span data-ttu-id="06f22-131">**資料指標**</span><span class="sxs-lookup"><span data-stu-id="06f22-131">**Cursor**</span></span>

    <span data-ttu-id="06f22-132">與指標相關聯的實體，可針對指標互動提供額外的視覺提示。</span><span class="sxs-lookup"><span data-stu-id="06f22-132">An entity associated with a pointer that gives additional visual cues around pointer interaction.</span></span> <span data-ttu-id="06f22-133">例如，FingerCursor 會在您的手指周圍呈現環形，而當手指接近「近端互動」物件時，可能會旋轉該環形。</span><span class="sxs-lookup"><span data-stu-id="06f22-133">For example, the FingerCursor will render a ring around your finger and may rotate that ring when your finger is close to 'near interactable' objects.</span></span> <span data-ttu-id="06f22-134">指標可以一次與單一資料指標產生關聯。</span><span class="sxs-lookup"><span data-stu-id="06f22-134">A pointer can be associated with a single cursor at time.</span></span>

- <span data-ttu-id="06f22-135">**互動和操作**</span><span class="sxs-lookup"><span data-stu-id="06f22-135">**Interaction and Manipulation**</span></span>

    <span data-ttu-id="06f22-136">物件可以使用互動或操作腳本來標記。</span><span class="sxs-lookup"><span data-stu-id="06f22-136">Objects can be tagged with an interaction or manipulation script.</span></span> <span data-ttu-id="06f22-137">這可能是 [`Interactable`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) 透過或類似的方式 [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) / [`ManipulationHandler`](xref:Microsoft.MixedReality.Toolkit.UI.ManipulationHandler) 。</span><span class="sxs-lookup"><span data-stu-id="06f22-137">This may be via a [`Interactable`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable), or something like [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable)/[`ManipulationHandler`](xref:Microsoft.MixedReality.Toolkit.UI.ManipulationHandler).</span></span>

    <span data-ttu-id="06f22-138">例如，NearInteractionGrabbable 和 NearInteractionTouchable 允許某些指標 (特別是近距離的互動指標) 知道哪些物件可專注于。</span><span class="sxs-lookup"><span data-stu-id="06f22-138">For example, NearInteractionGrabbable and NearInteractionTouchable allow for certain pointers (especially   near interaction pointers) to know which objects can be focused on.</span></span>

    <span data-ttu-id="06f22-139">互動和 ManipulationHandler 是接聽指標事件以修改 UI 視覺效果或移動/調整/旋轉遊戲物件的元件範例。</span><span class="sxs-lookup"><span data-stu-id="06f22-139">Interactable and ManipulationHandler are examples of components that listen to pointer events to modify   UI visuals or move/scale/rotate game objects.</span></span>

<span data-ttu-id="06f22-140">下圖從 MRTK 輸入堆疊的下) 中，將概要組建 (：</span><span class="sxs-lookup"><span data-stu-id="06f22-140">The image below captures the high level build up (from bottom up) of the MRTK input stack:</span></span>

![輸入系統圖表](../features/images/input/MRTK_InputSystem.png)
