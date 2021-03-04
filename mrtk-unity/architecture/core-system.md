---
title: CoreSystem
description: MRTK 中的輸入系統、裝置管理員和資料提供者
author: cDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、事件
ms.openlocfilehash: 7469a9764a88e5a431f7c270ee17caa7b0bc2119
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/03/2021
ms.locfileid: "101780302"
---
# <a name="core-system"></a><span data-ttu-id="93e79-104">核心系統</span><span class="sxs-lookup"><span data-stu-id="93e79-104">Core system</span></span>

<span data-ttu-id="93e79-105">輸入系統的核心是 [InputSystem](../features/input/overview.md)，也就是負責初始化和操作所有與 MRTK 相關聯之輸入相關功能的服務。</span><span class="sxs-lookup"><span data-stu-id="93e79-105">At the heart of the input system is the [InputSystem](../features/input/overview.md), which is a service that is responsible for initializing and operating all of the input related functionality associated with the MRTK.</span></span>

> [!NOTE]
> <span data-ttu-id="93e79-106">假設讀者已經讀過，並對 [術語](terminology.md) 區段有基本的瞭解。</span><span class="sxs-lookup"><span data-stu-id="93e79-106">It is assumed that readers have already read and have a basic understanding of the [terminology](terminology.md) section.</span></span>

<span data-ttu-id="93e79-107">此服務負責：</span><span class="sxs-lookup"><span data-stu-id="93e79-107">This service is responsible for:</span></span>

- <span data-ttu-id="93e79-108">讀取 [輸入系統設定檔](../configuration/mixed-reality-configuration-guide.md#input-system-settings)</span><span class="sxs-lookup"><span data-stu-id="93e79-108">Reading the [input system profile](../configuration/mixed-reality-configuration-guide.md#input-system-settings)</span></span>
- <span data-ttu-id="93e79-109">例如，啟動已設定的 [資料提供者](../features/input/input-providers.md) (， `Windows Mixed Reality Device Manager` 並 `OpenVR Device Manager`) 。</span><span class="sxs-lookup"><span data-stu-id="93e79-109">Starting the configured [data providers](../features/input/input-providers.md) (for example, `Windows Mixed Reality Device Manager` and `OpenVR Device Manager`).</span></span>
- <span data-ttu-id="93e79-110">[GazeProvider](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGazeProvider)的具現化，它是一種元件，負責提供 hololens (第一代) 樣式的列印頭資訊，以及 hololens 2 樣式的眼睛資訊。</span><span class="sxs-lookup"><span data-stu-id="93e79-110">Instantiation of the [GazeProvider](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGazeProvider), which is a component that is responsible for providing HoloLens (1st generation) style head gaze information in addition to HoloLens 2 style eye gaze information.</span></span>
- <span data-ttu-id="93e79-111">[FocusProvider](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityFocusProvider)的具現化，這是負責判斷具有焦點之物件的元件。</span><span class="sxs-lookup"><span data-stu-id="93e79-111">Instantiation of the [FocusProvider](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityFocusProvider), which is a component that is responsible for determining objects that have focus.</span></span> <span data-ttu-id="93e79-112">這在檔的 [ [指標和焦點](controllers-pointers-and-focus.md#pointers-and-focus) ] 區段中有更深入的說明。</span><span class="sxs-lookup"><span data-stu-id="93e79-112">This is described in more depth in the [pointers and focus](controllers-pointers-and-focus.md#pointers-and-focus) section of the documentation.</span></span>
- <span data-ttu-id="93e79-113">將所有輸入事件的登錄點提供給 ([全域](#global-listeners) 接聽程式) 。</span><span class="sxs-lookup"><span data-stu-id="93e79-113">Providing registration points for all input events (as [global listeners](#global-listeners)).</span></span>
- <span data-ttu-id="93e79-114">提供這些輸入事件的事件分派功能。</span><span class="sxs-lookup"><span data-stu-id="93e79-114">Providing event dispatch capabilities for those input events.</span></span>

## <a name="input-events"></a><span data-ttu-id="93e79-115">輸入事件</span><span class="sxs-lookup"><span data-stu-id="93e79-115">Input events</span></span>

<span data-ttu-id="93e79-116">輸入事件通常會在兩個不同的通道上引發：</span><span class="sxs-lookup"><span data-stu-id="93e79-116">Input events are generally fired on two different channels:</span></span>

### <a name="objects-in-focus"></a><span data-ttu-id="93e79-117">焦點物件</span><span class="sxs-lookup"><span data-stu-id="93e79-117">Objects in focus</span></span>

<span data-ttu-id="93e79-118">事件可以直接傳送至具有焦點的 GameObject。</span><span class="sxs-lookup"><span data-stu-id="93e79-118">Events can be sent directly to a GameObject that has focus.</span></span> <span data-ttu-id="93e79-119">例如，物件可能具有可執行檔腳本 [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) 。</span><span class="sxs-lookup"><span data-stu-id="93e79-119">For example, an object might have a script that implements [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler).</span></span>
<span data-ttu-id="93e79-120">這個物件會在焦點在其附近的手邊時取得觸控事件。</span><span class="sxs-lookup"><span data-stu-id="93e79-120">This object would get touch events when focused by a hand that is near it.</span></span> <span data-ttu-id="93e79-121">這些事件種類會「up」 GameObject 階層，直到找到能夠處理事件的 GameObject 為止。</span><span class="sxs-lookup"><span data-stu-id="93e79-121">These types of events go "up" the GameObject hierarchy until it finds a GameObject that is capable of handling the event.</span></span>

<span data-ttu-id="93e79-122">這是透過從預設的輸入系統執行中使用 [ExecuteHierarchy](https://docs.unity3d.com/ScriptReference/EventSystems.ExecuteEvents.ExecuteHierarchy.html) 來完成。</span><span class="sxs-lookup"><span data-stu-id="93e79-122">This is done by using [ExecuteHierarchy](https://docs.unity3d.com/ScriptReference/EventSystems.ExecuteEvents.ExecuteHierarchy.html) from within the default input system implementation.</span></span>

### <a name="global-listeners"></a><span data-ttu-id="93e79-123">全域接聽程式</span><span class="sxs-lookup"><span data-stu-id="93e79-123">Global listeners</span></span>

<span data-ttu-id="93e79-124">事件可以傳送給全域接聽程式。</span><span class="sxs-lookup"><span data-stu-id="93e79-124">Events can be sent to global listeners.</span></span> <span data-ttu-id="93e79-125">您可以使用輸入系統的介面來註冊所有輸入事件 [`IMixedRealityEventSystem`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityEventSystem) 。</span><span class="sxs-lookup"><span data-stu-id="93e79-125">It's possible to register for all input events by using the input system's [`IMixedRealityEventSystem`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityEventSystem) interface.</span></span> <span data-ttu-id="93e79-126">建議使用 [RegisterHandler](xref:Microsoft.MixedReality.Toolkit.IMixedRealityEventSystem.RegisterHandler``1(IEventSystemHandler)) 方法來註冊全域事件-已被取代的函式會導致接聽程式收到 `Register` 所有輸入事件的通知，而不只是特定類型的輸入事件，而是由事件介面) 所定義的型別 (。</span><span class="sxs-lookup"><span data-stu-id="93e79-126">It's recommended to use the [RegisterHandler](xref:Microsoft.MixedReality.Toolkit.IMixedRealityEventSystem.RegisterHandler``1(IEventSystemHandler)) method for registering for global events - the deprecated `Register` function will cause listeners to get notified of ALL input events, rather than just input events of a particular type (where type is defined by the event interface).</span></span>

<span data-ttu-id="93e79-127">請注意 [，「](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityInputSystem.PushFallbackInputHandler(GameObject)) 回溯接聽程式」是另一種全域接聽程式，也不建議這樣做，因為它們會接收未在場景中的其他地方處理的每個單一輸入事件。</span><span class="sxs-lookup"><span data-stu-id="93e79-127">Note that [fallback listeners](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityInputSystem.PushFallbackInputHandler(GameObject)) are another type of global listeners which are also discouraged because they will receive every single input event that hasn't been handled elsewhere in the scene.</span></span>

### <a name="order-of-event-dispatch"></a><span data-ttu-id="93e79-128">事件分派的順序</span><span class="sxs-lookup"><span data-stu-id="93e79-128">Order of event dispatch</span></span>

<span data-ttu-id="93e79-129">一般情況下，事件會以下列方式傳送至接聽程式。</span><span class="sxs-lookup"><span data-stu-id="93e79-129">Generally, events are sent to listeners in the following way.</span></span> <span data-ttu-id="93e79-130">請注意，如果下列任何步驟將事件標示為已 [處理](https://docs.unity3d.com/ScriptReference/EventSystems.AbstractEventData-used.html)，事件分派進程就會停止。</span><span class="sxs-lookup"><span data-stu-id="93e79-130">Note that if any of the steps below mark the event as [handled](https://docs.unity3d.com/ScriptReference/EventSystems.AbstractEventData-used.html), the event dispatch process stops.</span></span>

1. <span data-ttu-id="93e79-131">事件會傳送至全域接聽程式。</span><span class="sxs-lookup"><span data-stu-id="93e79-131">Event is sent to global listeners.</span></span>
2. <span data-ttu-id="93e79-132">事件會傳送至焦點物件的強制回應對話方塊。</span><span class="sxs-lookup"><span data-stu-id="93e79-132">Event is sent to modal dialogs of the focused object.</span></span>
3. <span data-ttu-id="93e79-133">事件會傳送至焦點物件。</span><span class="sxs-lookup"><span data-stu-id="93e79-133">Event is sent to the focused object.</span></span>
4. <span data-ttu-id="93e79-134">事件會傳送至回溯接聽項。</span><span class="sxs-lookup"><span data-stu-id="93e79-134">Event is sent to fallback listeners.</span></span>

## <a name="device-managers-and-data-providers"></a><span data-ttu-id="93e79-135">裝置管理員和資料提供者</span><span class="sxs-lookup"><span data-stu-id="93e79-135">Device managers and data providers</span></span>

<span data-ttu-id="93e79-136">這些實體負責與較低層級的 (Api （例如 Windows Mixed Reality Api）進行互動，或 OpenVR Api) ，並將這些系統中的資料轉譯成符合 MRTK 較高層級輸入抽象的資料。</span><span class="sxs-lookup"><span data-stu-id="93e79-136">These entities are responsible for interfacing with lower-level APIs (such as Windows Mixed Reality APIs, or OpenVR APIs) and translating data from those systems into ones that fit the MRTK's higher level input abstractions.</span></span> <span data-ttu-id="93e79-137">它們負責偵測、建立和管理 [控制器](controllers-pointers-and-focus.md#controllers)的存留期。</span><span class="sxs-lookup"><span data-stu-id="93e79-137">They are responsible for detecting, creating, and managing the lifetime of [controllers](controllers-pointers-and-focus.md#controllers).</span></span>

<span data-ttu-id="93e79-138">裝置管理員的基本流程包括：</span><span class="sxs-lookup"><span data-stu-id="93e79-138">The basic flow of a device manager involves:</span></span>

1. <span data-ttu-id="93e79-139">裝置管理員由輸入系統服務具現化。</span><span class="sxs-lookup"><span data-stu-id="93e79-139">The device manager is instantiated by the input system service.</span></span>
2. <span data-ttu-id="93e79-140">裝置管理員會向其基礎系統註冊 (例如，Windows Mixed Reality 裝置管理員會註冊 [輸入](../features/input/input-events.md) 和 [手勢](../features/input/gestures.md#gesture-events) 事件。</span><span class="sxs-lookup"><span data-stu-id="93e79-140">The device manager registers with its underlying system (for example, the Windows Mixed Reality device manager will register for [input](../features/input/input-events.md) and [gesture](../features/input/gestures.md#gesture-events) events.</span></span>
3. <span data-ttu-id="93e79-141">它會建立它從基礎系統中探索的控制器 (例如，提供者可以偵測出有明確的手) </span><span class="sxs-lookup"><span data-stu-id="93e79-141">It creates controllers that it discovers from the underlying system (for example the provider could detect the presence of articulated hands)</span></span>
4. <span data-ttu-id="93e79-142">在其更新 () 迴圈中，呼叫 UpdateController () 輪詢基礎系統的新狀態，並更新其控制器標記法。</span><span class="sxs-lookup"><span data-stu-id="93e79-142">In its Update() loop, call UpdateController() to poll for the new state of the underlying system and update its controller representation.</span></span>
