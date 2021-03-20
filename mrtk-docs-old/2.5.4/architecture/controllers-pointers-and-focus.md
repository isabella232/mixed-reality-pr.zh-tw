---
title: ControllersPointersAndFocus
description: 與控制器、指標和焦點互動。
author: cDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、指標、控制器
ms.openlocfilehash: f656089b8ecd78e0f847c777baf63ae67f957802
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104685671"
---
# <a name="controllers-pointers-and-focus"></a><span data-ttu-id="a18d7-104">控制器、指標和焦點</span><span class="sxs-lookup"><span data-stu-id="a18d7-104">Controllers, pointers, and focus</span></span>

<span data-ttu-id="a18d7-105">控制器、指標和焦點是以核心輸入系統所建立的基礎為基礎所建立的較高層級概念。</span><span class="sxs-lookup"><span data-stu-id="a18d7-105">Controllers, pointers, and focus are higher-level concepts that build upon the foundation established by the core input system.</span></span> <span data-ttu-id="a18d7-106">兩者結合在一起，可提供一大部分機制來與場景中的物件互動。</span><span class="sxs-lookup"><span data-stu-id="a18d7-106">Together, they provide a large portion of the mechanism for interacting with objects in the scene.</span></span>

## <a name="controllers"></a><span data-ttu-id="a18d7-107">控制器</span><span class="sxs-lookup"><span data-stu-id="a18d7-107">Controllers</span></span>

<span data-ttu-id="a18d7-108">控制器是實體控制器的代表 (6 度的自由、明確的手) 等等。</span><span class="sxs-lookup"><span data-stu-id="a18d7-108">Controllers are representations of a physical controller (6-degrees of freedom, articulated hand, etc).</span></span> <span data-ttu-id="a18d7-109">它們是由裝置管理員所建立，負責與對應的基礎系統進行通訊，並將該資料轉譯成 MRTK 狀的資料和事件。</span><span class="sxs-lookup"><span data-stu-id="a18d7-109">They are created by device managers and are responsible for communicating with the corresponding underlying system and translating that data into MRTK-shaped data and events.</span></span>

<span data-ttu-id="a18d7-110">例如，在 Windows Mixed Reality 平臺上， [`WindowsMixedRealityArticulatedHand`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityArticulatedHand) 是負責與基礎 Windows [手形追蹤 api](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) 互動的控制器，以取得關於接點、姿勢和其他屬性的資訊。</span><span class="sxs-lookup"><span data-stu-id="a18d7-110">For example, on the Windows Mixed Reality platform, the [`WindowsMixedRealityArticulatedHand`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityArticulatedHand) is a controller that is responsible for interfacing with the underlying Windows [hand tracking APIs](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) to get information about the joints, pose, and other properties of the hand.</span></span> <span data-ttu-id="a18d7-111">它負責將這項資料轉換成相關的 MRTK 事件 (例如，藉由呼叫 RaisePoseInputChanged 或 RaiseHandJointsUpdated) ，以及藉由更新其本身的內部狀態，讓的查詢傳回 [`TryGetJointPose`](xref:Microsoft.MixedReality.Toolkit.Input.HandJointUtils.TryGetJointPose(TrackedHandJoint,Handedness,MixedRealityPose@)) 正確的資料。</span><span class="sxs-lookup"><span data-stu-id="a18d7-111">It is responsible for turning this data into relevant MRTK events (for example, by calling RaisePoseInputChanged or RaiseHandJointsUpdated) and by updating its own internal state so that queries for [`TryGetJointPose`](xref:Microsoft.MixedReality.Toolkit.Input.HandJointUtils.TryGetJointPose(TrackedHandJoint,Handedness,MixedRealityPose@)) will return correct data.</span></span>

<span data-ttu-id="a18d7-112">一般而言，控制器的生命週期會涉及：</span><span class="sxs-lookup"><span data-stu-id="a18d7-112">Generally, a controller's lifecycle will involve:</span></span>

1. <span data-ttu-id="a18d7-113">在偵測到新的來源時，裝置管理員會建立一個控制器 (例如，裝置管理員會偵測並開始追蹤) 。</span><span class="sxs-lookup"><span data-stu-id="a18d7-113">A controller gets created by a device manager upon detection of a new source (for example, the device manager detects and starts tracking a hand).</span></span>

2. <span data-ttu-id="a18d7-114">在控制器的更新 () 迴圈中，它會呼叫其基礎 API 系統。</span><span class="sxs-lookup"><span data-stu-id="a18d7-114">In the controller's Update() loop, it calls into its underlying API system.</span></span>

3. <span data-ttu-id="a18d7-115">在相同的更新迴圈中，它會藉由直接呼叫核心輸入系統本身來引發輸入事件變更 (例如，引發 HandMeshUpdated 或 HandJointsUpdated) 。</span><span class="sxs-lookup"><span data-stu-id="a18d7-115">In the same update loop, it raises input event changes by calling directly into the core input system itself (for example, raising HandMeshUpdated, or HandJointsUpdated).</span></span>

## <a name="pointers-and-focus"></a><span data-ttu-id="a18d7-116">指標和焦點</span><span class="sxs-lookup"><span data-stu-id="a18d7-116">Pointers and focus</span></span>

<span data-ttu-id="a18d7-117">指標是用來與遊戲物件互動。</span><span class="sxs-lookup"><span data-stu-id="a18d7-117">Pointers are used to interact with game objects.</span></span> <span data-ttu-id="a18d7-118">本節說明如何建立指標、如何更新它們，以及它們如何判斷焦點) 的物件 (。</span><span class="sxs-lookup"><span data-stu-id="a18d7-118">This section describes how pointers are created, how they get updated, and how they determine the object(s) that are in focus.</span></span> <span data-ttu-id="a18d7-119">此外，它也會涵蓋存在的不同指標類型，以及它們處於作用中狀態的案例。</span><span class="sxs-lookup"><span data-stu-id="a18d7-119">It will also cover the different types of pointers that exist and the scenarios in which they are active.</span></span>

### <a name="pointer-categories"></a><span data-ttu-id="a18d7-120">指標分類</span><span class="sxs-lookup"><span data-stu-id="a18d7-120">Pointer categories</span></span>

<span data-ttu-id="a18d7-121">指標通常屬於下列其中一個類別：</span><span class="sxs-lookup"><span data-stu-id="a18d7-121">Pointers generally fall into one of the following categories:</span></span>

- <span data-ttu-id="a18d7-122">**遠指標**</span><span class="sxs-lookup"><span data-stu-id="a18d7-122">**Far pointers**</span></span>

  <span data-ttu-id="a18d7-123">這些類型的指標會用來與使用者遠離使用者 (的物件互動，而不是定義為「不接近」 ) 。</span><span class="sxs-lookup"><span data-stu-id="a18d7-123">These types of pointers are used to interact with objects that are far away from the user (far away is defined as simply “not near”).</span></span> <span data-ttu-id="a18d7-124">這些類型的指標通常會將可移至世界各地的線條轉型，並可讓使用者與不緊接在其旁邊的物件互動和操作。</span><span class="sxs-lookup"><span data-stu-id="a18d7-124">These types of pointers generally cast lines that can go far into the world and allow the user to interact with and manipulate objects that are not immediately next to them.</span></span>

- <span data-ttu-id="a18d7-125">**近端指標**</span><span class="sxs-lookup"><span data-stu-id="a18d7-125">**Near pointers**</span></span>

  <span data-ttu-id="a18d7-126">這些類型的指標是用來與接近使用者的物件互動，以抓取、觸控和操作。</span><span class="sxs-lookup"><span data-stu-id="a18d7-126">These types of pointers are used to interact with objects that are close enough to the user to grab, touch, and manipulate.</span></span> <span data-ttu-id="a18d7-127">一般而言，這些類型的指標會藉由尋找鄰近區域中的物件來與物件互動 (方法是在較小的距離執行 raycasting、執行球形轉型以尋找鄰近區域中的物件，或列舉視為 grabbable/可觸式) 的物件清單。</span><span class="sxs-lookup"><span data-stu-id="a18d7-127">Generally, these types of pointers interact with objects by looking for objects in the nearby vicinity (either by doing raycasting at small distances, doing spherical casting looking for objects in the vicinity, or enumerating lists of objects that are considered grabbable/touchable).</span></span>

- <span data-ttu-id="a18d7-128">**傳送指標**</span><span class="sxs-lookup"><span data-stu-id="a18d7-128">**Teleport pointers**</span></span>

  <span data-ttu-id="a18d7-129">這些類型的指標會插入遙傳系統，以處理將使用者移至指標的目標位置。</span><span class="sxs-lookup"><span data-stu-id="a18d7-129">These types of pointers plug into the teleportation system to handle moving the user to the location targeted by the pointer.</span></span>

## <a name="pointer-mediation"></a><span data-ttu-id="a18d7-130">指標中繼</span><span class="sxs-lookup"><span data-stu-id="a18d7-130">Pointer mediation</span></span>

<span data-ttu-id="a18d7-131">由於單一控制器可能會有多個指標 (例如，有向的手勢可以) 接近且遠的互動指標，因此有一個元件負責調節應使用中的指標。</span><span class="sxs-lookup"><span data-stu-id="a18d7-131">Because a single controller can have multiple pointers (for example, the articulated hand can have both near and far interaction pointers), there exists a component that is responsible for mediating which pointer should be active.</span></span>

<span data-ttu-id="a18d7-132">例如，當使用者的手中使用 pressable 按鈕時， [`ShellHandRayPointer`](xref:Microsoft.MixedReality.Toolkit.Input.ShellHandRayPointer) 應該會停止顯示，且 [`PokePointer`](xref:Microsoft.MixedReality.Toolkit.Input.PokePointer) 應該參與。</span><span class="sxs-lookup"><span data-stu-id="a18d7-132">For example, as the user’s hand approaches a pressable button, the [`ShellHandRayPointer`](xref:Microsoft.MixedReality.Toolkit.Input.ShellHandRayPointer) should stop showing, and the [`PokePointer`](xref:Microsoft.MixedReality.Toolkit.Input.PokePointer) should be engaged.</span></span>

<span data-ttu-id="a18d7-133">這是由所處理 [`DefaultPointerMediator`](xref:Microsoft.MixedReality.Toolkit.Input.DefaultPointerMediator) ，它負責根據所有指標的狀態判斷哪些指標是作用中。</span><span class="sxs-lookup"><span data-stu-id="a18d7-133">This is handled by the [`DefaultPointerMediator`](xref:Microsoft.MixedReality.Toolkit.Input.DefaultPointerMediator), which is responsible for determining which pointers are active, based on the state of all pointers.</span></span> <span data-ttu-id="a18d7-134">這項作業的其中一個重要功能是，當接近的指標接近物件時，會停用遠指標 (請參閱 [`DefaultPointerMediator`](xref:Microsoft.MixedReality.Toolkit.Input.DefaultPointerMediator)) 。</span><span class="sxs-lookup"><span data-stu-id="a18d7-134">One of the key things this does is disable far pointers when a near pointer is close to an object (please see [`DefaultPointerMediator`](xref:Microsoft.MixedReality.Toolkit.Input.DefaultPointerMediator)).</span></span>

<span data-ttu-id="a18d7-135">您可以藉由變更 [`PointerMediator`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityPointerProfile.PointerMediator) 指標設定檔上的屬性，提供指標中繼程式的替代實。</span><span class="sxs-lookup"><span data-stu-id="a18d7-135">It's possible to provide an alternate implementation of the pointer mediator by changing the [`PointerMediator`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityPointerProfile.PointerMediator) property on the pointer profile.</span></span>

### <a name="how-to-disable-pointers"></a><span data-ttu-id="a18d7-136">如何停用指標</span><span class="sxs-lookup"><span data-stu-id="a18d7-136">How to disable pointers</span></span>

<span data-ttu-id="a18d7-137">因為指標中繼程式會執行每個畫面格，所以最後會控制所有指標的作用中/非作用中狀態。</span><span class="sxs-lookup"><span data-stu-id="a18d7-137">Because the pointer mediator runs every frame, it ends up controlling the active / inactive state of all pointers.</span></span> <span data-ttu-id="a18d7-138">因此，如果您在程式碼中設定指標的 IsInteractionEnabled 屬性，則會在每個畫面格的指標中繼程式中覆寫它。</span><span class="sxs-lookup"><span data-stu-id="a18d7-138">Therefore, if you set a pointer's IsInteractionEnabled property in code, it will get overwritten by the pointer mediator every frame.</span></span> <span data-ttu-id="a18d7-139">相反地，您可以指定 [`PointerBehavior`](xref:Microsoft.MixedReality.Toolkit.Input.PointerBehavior) 來控制指標應該自行開啟或關閉。</span><span class="sxs-lookup"><span data-stu-id="a18d7-139">Instead, you can specify the [`PointerBehavior`](xref:Microsoft.MixedReality.Toolkit.Input.PointerBehavior) to control whether pointers should be on or off yourself.</span></span> <span data-ttu-id="a18d7-140">請注意，只有在您使用預設值和 MRTK 時，才能使用此功能 [`FocusProvider`](xref:Microsoft.MixedReality.Toolkit.Input.FocusProvider) [`DefaultPointerMediator`](xref:Microsoft.MixedReality.Toolkit.Input.DefaultPointerMediator) 。</span><span class="sxs-lookup"><span data-stu-id="a18d7-140">Note that this will only work if you are using the default [`FocusProvider`](xref:Microsoft.MixedReality.Toolkit.Input.FocusProvider) and [`DefaultPointerMediator`](xref:Microsoft.MixedReality.Toolkit.Input.DefaultPointerMediator) in MRTK.</span></span>

#### <a name="example-disable-hand-rays-in-mrtk"></a><span data-ttu-id="a18d7-141">範例：停用 MRTK 中的手光線</span><span class="sxs-lookup"><span data-stu-id="a18d7-141">Example: Disable hand rays in MRTK</span></span>

<span data-ttu-id="a18d7-142">下列程式碼會關閉 MRTK 中的手光：</span><span class="sxs-lookup"><span data-stu-id="a18d7-142">The following code will turn off the hand rays in MRTK:</span></span>

```c#
// Turn off all hand rays
PointerUtils.SetHandRayPointerBehavior(PointerBehavior.AlwaysOff);

// Turn off hand rays for the right hand only
PointerUtils.SetHandRayPointerBehavior(PointerBehavior.AlwaysOff, Handedness.Right);
```

<span data-ttu-id="a18d7-143">下列程式碼將會在 MRTK 中將手片的預設行為傳回：</span><span class="sxs-lookup"><span data-stu-id="a18d7-143">The following code will return hand rays to their default behavior in MRTK:</span></span>

```c#
PointerUtils.SetHandRayPointerBehavior(PointerBehavior.Default);
```

<span data-ttu-id="a18d7-144">不論是否接近 grabbable，下列程式碼都會強制讓手的光線開啟：</span><span class="sxs-lookup"><span data-stu-id="a18d7-144">The following code will force hand rays to be on, regardless if near a grabbable:</span></span>

```c#
// Turn off all hand rays
PointerUtils.SetHandRayPointerBehavior(PointerBehavior.AlwaysOn);
```

<span data-ttu-id="a18d7-145">[`PointerUtils`](xref:Microsoft.MixedReality.Toolkit.Input.PointerUtils)如需 [`TurnPointersOnOff`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.DisablePointersExample) 更多範例，請參閱和。</span><span class="sxs-lookup"><span data-stu-id="a18d7-145">See [`PointerUtils`](xref:Microsoft.MixedReality.Toolkit.Input.PointerUtils) and [`TurnPointersOnOff`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.DisablePointersExample) for more examples.</span></span>

### <a name="focusprovider"></a><span data-ttu-id="a18d7-146">FocusProvider</span><span class="sxs-lookup"><span data-stu-id="a18d7-146">FocusProvider</span></span>

<span data-ttu-id="a18d7-147">[`FocusProvider`](xref:Microsoft.MixedReality.Toolkit.Input.FocusProvider)是主力，負責逐一查看所有指標的清單，並找出每個指標的焦點物件。</span><span class="sxs-lookup"><span data-stu-id="a18d7-147">The [`FocusProvider`](xref:Microsoft.MixedReality.Toolkit.Input.FocusProvider) is the workhorse that is responsible for iterating over the list of all pointers and figuring out what the focused object is for each pointer.</span></span>

<span data-ttu-id="a18d7-148">在每次 `Update()` 呼叫中，這將會：</span><span class="sxs-lookup"><span data-stu-id="a18d7-148">In each `Update()` call, this will:</span></span>

1. <span data-ttu-id="a18d7-149">藉由 raycasting 和執行指標本身所設定的點擊偵測來更新所有指標 (例如，球體指標可指定 SphereOverlap raycastMode，因此 FocusProvider 會執行以球體為基礎的衝突) </span><span class="sxs-lookup"><span data-stu-id="a18d7-149">Update all of the pointers, by raycasting and doing hit detection as-configured by the pointer itself (for example, the sphere pointer could specify the SphereOverlap raycastMode, so FocusProvider will do a sphere-based collision)</span></span>

2. <span data-ttu-id="a18d7-150">以個別指標為基礎更新焦點物件 (也就是，如果物件取得焦點，它也會觸發這些物件的事件，如果物件遺失焦點，則會觸發焦點遺失等) 。</span><span class="sxs-lookup"><span data-stu-id="a18d7-150">Update the focused object on a per-pointer basis (i.e. if an object gained focus, it would also trigger events to those object, if an object lost focus, it would trigger focus lost, etc).</span></span>

### <a name="pointer-configuration-and-lifecycle"></a><span data-ttu-id="a18d7-151">指標設定和生命週期</span><span class="sxs-lookup"><span data-stu-id="a18d7-151">Pointer configuration and lifecycle</span></span>

<span data-ttu-id="a18d7-152">[指標可以](../features/input/pointers.md) 在輸入系統設定檔的 [ *指標* ] 區段中設定。</span><span class="sxs-lookup"><span data-stu-id="a18d7-152">[Pointers can be configured](../features/input/pointers.md) in the *Pointers* section of the input system profile.</span></span>

<span data-ttu-id="a18d7-153">指標的存留期通常如下所示：</span><span class="sxs-lookup"><span data-stu-id="a18d7-153">The lifetime of a pointer is generally the following:</span></span>

1. <span data-ttu-id="a18d7-154">裝置管理員會偵測到控制器是否存在。</span><span class="sxs-lookup"><span data-stu-id="a18d7-154">A device manager will detect the presence of a controller.</span></span> <span data-ttu-id="a18d7-155">此裝置管理員接著會透過的呼叫，建立與控制器相關聯的指標集 [`RequestPointers`](xref:Microsoft.MixedReality.Toolkit.Input.BaseInputDeviceManager) 。</span><span class="sxs-lookup"><span data-stu-id="a18d7-155">This device manager will then create the set of pointers associated with the controller via a call to [`RequestPointers`](xref:Microsoft.MixedReality.Toolkit.Input.BaseInputDeviceManager).</span></span>

2. <span data-ttu-id="a18d7-156">FocusProvider 會在其 Update () 迴圈中逐一查看所有有效的指標，並執行相關聯的 raycast 或點擊偵測邏輯。</span><span class="sxs-lookup"><span data-stu-id="a18d7-156">The FocusProvider, in its Update() loop, will iterate over all of the valid pointers and do the associated raycast or hit detection logic.</span></span> <span data-ttu-id="a18d7-157">這是用來判斷每個特定指標所專注的物件。</span><span class="sxs-lookup"><span data-stu-id="a18d7-157">This is used to determine the object that is focused by each particular pointer.</span></span>

    - <span data-ttu-id="a18d7-158">因為可以同時使用多個輸入來源 (例如，有兩個實際操作) ，所以也可以有多個具有焦點的物件。</span><span class="sxs-lookup"><span data-stu-id="a18d7-158">Because it's possible to have multiple sources of input active at the same time (for example, two hands active present), it's also possible to have multiple objects that have focus at the same time.</span></span>

3. <span data-ttu-id="a18d7-159">裝置管理員在發現控制器來源遺失時，將會中斷與遺失控制器相關聯的指標。</span><span class="sxs-lookup"><span data-stu-id="a18d7-159">The device manager, upon discovering that a controller source was lost, will tear down the pointers associated with the lost controller.</span></span>
