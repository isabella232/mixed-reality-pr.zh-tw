---
title: 指標
description: MRTK 中指標的檔
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
ms.localizationpriority: medium
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、指標、
ms.openlocfilehash: 7b9a92042cb17b8cf5a74f2efda6d642214f85e9
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104688908"
---
# <a name="pointers"></a><span data-ttu-id="a7c08-104">指標</span><span class="sxs-lookup"><span data-stu-id="a7c08-104">Pointers</span></span>

![Pointer](../Images/Pointers/MRTK_Pointer_Main.png)

<span data-ttu-id="a7c08-106">本文說明如何在實務上設定和回應指標輸入（相較于[指標架構](../../architecture/InputSystem/ControllersPointersAndFocus.md)）</span><span class="sxs-lookup"><span data-stu-id="a7c08-106">This article explains how to configure and respond to Pointer input in practice, compared to [Pointer Architecture](../../architecture/InputSystem/ControllersPointersAndFocus.md)</span></span>

<span data-ttu-id="a7c08-107">偵測到新的控制器時，會在執行時間自動具現化指標。</span><span class="sxs-lookup"><span data-stu-id="a7c08-107">Pointers are instanced automatically at runtime when a new controller is detected.</span></span> <span data-ttu-id="a7c08-108">有一個以上的指標可以附加至控制器。</span><span class="sxs-lookup"><span data-stu-id="a7c08-108">More than one pointer can be attached to a controller.</span></span> <span data-ttu-id="a7c08-109">例如，使用預設指標設定檔時，Windows Mixed Reality 控制器會同時取得一般選取和遙傳的行和拋物線指標。</span><span class="sxs-lookup"><span data-stu-id="a7c08-109">For example, with the default pointer profile, Windows Mixed Reality controllers get both a line and a parabolic pointer for normal selection and teleportation respectively.</span></span>

## <a name="pointer-configuration"></a><span data-ttu-id="a7c08-110">指標設定</span><span class="sxs-lookup"><span data-stu-id="a7c08-110">Pointer configuration</span></span>

<span data-ttu-id="a7c08-111">指標會在 MRTK 中透過進行設定為輸入系統的一部分 [`MixedRealityPointerProfile`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityPointerProfile) 。</span><span class="sxs-lookup"><span data-stu-id="a7c08-111">Pointers are configured as part of the Input System in MRTK via a [`MixedRealityPointerProfile`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityPointerProfile).</span></span> <span data-ttu-id="a7c08-112">這種類型的設定檔會指派給 [`MixedRealityInputSystemProfile`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityInputSystemProfile) MRTK Configuration inspector 中的。</span><span class="sxs-lookup"><span data-stu-id="a7c08-112">This type of profile is assigned to a [`MixedRealityInputSystemProfile`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityInputSystemProfile) in the MRTK Configuration inspector.</span></span> <span data-ttu-id="a7c08-113">指標設定檔會判斷游標、執行時間可用的指標類型，以及這些指標如何彼此通訊，以決定哪一個是作用中。</span><span class="sxs-lookup"><span data-stu-id="a7c08-113">The Pointer profile determines the cursor, types of Pointers available at runtime, and how those pointers communicate with each other to decide which one is active.</span></span>

- <span data-ttu-id="a7c08-114">*指向範圍* -定義指標可與 GameObject 互動的最大距離。</span><span class="sxs-lookup"><span data-stu-id="a7c08-114">*Pointing Extent* - Defines the max distance for which a Pointer can interact with a GameObject.</span></span>

- <span data-ttu-id="a7c08-115">*指向 Raycast 圖層遮罩* -這是 LayerMasks 的優先陣列，用來判斷任何指定指標可與其互動的可能 gameobject，以及嘗試的互動順序。</span><span class="sxs-lookup"><span data-stu-id="a7c08-115">*Pointing Raycast Layer Masks* - This is a prioritized array of LayerMasks to determine which possible GameObjects any given Pointer can interact with and the order of interaction to attempt.</span></span> <span data-ttu-id="a7c08-116">這可能有助於確保指標會在其他場景物件之前先與 UI 元素互動。</span><span class="sxs-lookup"><span data-stu-id="a7c08-116">This may be useful to ensure Pointers interact with UI elements first before other scene objects.</span></span>
<span data-ttu-id="a7c08-117">![指標設定檔範例](../Images/Input/Pointers/PointerProfile.PNG)</span><span class="sxs-lookup"><span data-stu-id="a7c08-117">![Pointer Profile Example](../Images/Input/Pointers/PointerProfile.PNG)</span></span>

### <a name="pointer-options-configuration"></a><span data-ttu-id="a7c08-118">指標選項設定</span><span class="sxs-lookup"><span data-stu-id="a7c08-118">Pointer options configuration</span></span>

<span data-ttu-id="a7c08-119">預設的 MRTK 指標設定檔設定包含下列指標類別以及現成關聯的 prefabs。</span><span class="sxs-lookup"><span data-stu-id="a7c08-119">The default MRTK Pointer Profile configuration includes the following pointer classes and associated prefabs out-of-box.</span></span> <span data-ttu-id="a7c08-120">在執行時間可供系統使用的指標清單，是在指標設定檔的 *指標選項* 下定義。</span><span class="sxs-lookup"><span data-stu-id="a7c08-120">The list of pointers available to the system at runtime is defined under *Pointer Options* in the Pointer profile.</span></span> <span data-ttu-id="a7c08-121">開發人員可以利用這份清單來重新設定現有的指標、加入新的指標，或刪除一個指標。</span><span class="sxs-lookup"><span data-stu-id="a7c08-121">Developers can utilize this list to reconfigure existing Pointers, add new Pointers, or delete one.</span></span>

![指標選項設定檔範例](../Images/Input/Pointers/PointerOptionsProfile.PNG)

<span data-ttu-id="a7c08-123">每個指標專案都是由下列資料集所定義：</span><span class="sxs-lookup"><span data-stu-id="a7c08-123">Each Pointer entry is defined by the following set of data:</span></span>

- <span data-ttu-id="a7c08-124">*控制器類型* -指標有效的控制器集。</span><span class="sxs-lookup"><span data-stu-id="a7c08-124">*Controller Type* - The set of controllers that a pointer is valid for.</span></span>
  - <span data-ttu-id="a7c08-125">例如， *PokePointer* 會負責具有手指的 "刺探" 物件，且預設標示為僅支援已標示的手型控制器類型。</span><span class="sxs-lookup"><span data-stu-id="a7c08-125">For example, the *PokePointer* is responsible for "poking" objects with a finger, and is, by default marked as only supporting the articulated hand controller type.</span></span> <span data-ttu-id="a7c08-126">只有當控制器可供使用時，才會具現化指標，而特定 *控制器類型* 則會定義此指標預製專案可以建立的控制器。</span><span class="sxs-lookup"><span data-stu-id="a7c08-126">Pointers are only instantiated when a controller becomes available and in particular the *Controller Type* defines what controllers this pointer prefab can be created with.</span></span>

- <span data-ttu-id="a7c08-127">*Handedness* -允許只針對特定的手具現化指標 (左/右) </span><span class="sxs-lookup"><span data-stu-id="a7c08-127">*Handedness* - allows for a pointer to only being instantiated for a specific hand (left/right)</span></span>

> [!NOTE]
> <span data-ttu-id="a7c08-128">將指標專案的 *Handedness* 屬性設定為 [ *無* ]，將會從系統中有效地停用它，作為從清單中移除該指標的替代方法。</span><span class="sxs-lookup"><span data-stu-id="a7c08-128">Setting the *Handedness* property of a Pointer entry to *None* will effectively disable it from the system as an alternative to removing that Pointer from the list.</span></span>

- <span data-ttu-id="a7c08-129">*指標預製專案* -當符合指定控制器類型和 handedness 的控制器開始追蹤時，會具現化此預製專案資產。</span><span class="sxs-lookup"><span data-stu-id="a7c08-129">*Pointer Prefab* - This prefab asset will be instantiated when a controller matching the specified controller type and handedness starts being tracked.</span></span>

<span data-ttu-id="a7c08-130">您可以有多個與控制器相關聯的指標。</span><span class="sxs-lookup"><span data-stu-id="a7c08-130">It is possible to have multiple pointers associated with a controller.</span></span> <span data-ttu-id="a7c08-131">例如，在 `DefaultHoloLens2InputSystemProfile` (資產/MRTK/SDK/設定檔/HoloLens2/) 中，有向 PokePointer、GrabPointer 和 DefaultControllerPointer 相關聯的、 和 (亦即</span><span class="sxs-lookup"><span data-stu-id="a7c08-131">For example, in `DefaultHoloLens2InputSystemProfile` (Assets/MRTK/SDK/Profiles/HoloLens2/) the articulated hand controller is associated with the *PokePointer*, *GrabPointer*, and the *DefaultControllerPointer* (i.e</span></span> <span data-ttu-id="a7c08-132">) 的手。</span><span class="sxs-lookup"><span data-stu-id="a7c08-132">hand rays).</span></span>

> [!NOTE]
> <span data-ttu-id="a7c08-133">MRTK 在 *資產/MRTK/SDK/Features/UX/prefabs/指標* 中提供一組指標 prefabs。</span><span class="sxs-lookup"><span data-stu-id="a7c08-133">MRTK provides a set of pointer prefabs in *Assets/MRTK/SDK/Features/UX/Prefabs/Pointers*.</span></span> <span data-ttu-id="a7c08-134">只要新的自訂預製專案包含 *資產/MRTK/SDK/功能/UX/腳本/指標* 或任何其他執行的腳本中的其中一個指標腳本，就可以建立新的自訂 [`IMixedRealityPointer`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointer) 。</span><span class="sxs-lookup"><span data-stu-id="a7c08-134">A new custom prefab can be built as long as it contains one of the pointer scripts in *Assets/MRTK/SDK/Features/UX/Scripts/Pointers* or any other script implementing [`IMixedRealityPointer`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointer).</span></span>

### <a name="default-pointer-classes"></a><span data-ttu-id="a7c08-135">預設指標類別</span><span class="sxs-lookup"><span data-stu-id="a7c08-135">Default pointer classes</span></span>

<span data-ttu-id="a7c08-136">下列類別是可用的現成 MRTK 指標，並定義于上面所述的預設 *MRTK 指標設定檔* 中。</span><span class="sxs-lookup"><span data-stu-id="a7c08-136">The following classes are the out-of-box MRTK pointers available and defined in the default *MRTK Pointer Profile* outlined above.</span></span> <span data-ttu-id="a7c08-137">在 *資產/MRTK/SDK/Features/UX/Prefabs/指標* 下提供的每個指標預製專案，都包含其中一個附加的指標元件。</span><span class="sxs-lookup"><span data-stu-id="a7c08-137">Each pointer prefab provided under *Assets/MRTK/SDK/Features/UX/Prefabs/Pointers* contains one of the pointer components attached.</span></span>

![MRTK 預設指標](../Images/Input/Pointers/MRTK_Pointers.png)

#### <a name="far-pointers"></a><span data-ttu-id="a7c08-139">遠指標</span><span class="sxs-lookup"><span data-stu-id="a7c08-139">Far pointers</span></span>

##### [`LinePointer`](xref:Microsoft.MixedReality.Toolkit.Input.LinePointer)

 <span data-ttu-id="a7c08-140">*LinePointer*（基底指標類別）會從輸入的來源繪製一條線 (亦即，控制器) 指標方向，並支援以此方向進行的單一光線轉換。</span><span class="sxs-lookup"><span data-stu-id="a7c08-140">*LinePointer*, a base pointer class, draws a line from the source of the input (i.e. the controller) in the pointer direction and supports a single ray cast in this direction.</span></span> <span data-ttu-id="a7c08-141">一般而言，子類別（例如 [`ShellHandRayPointer`](xref:Microsoft.MixedReality.Toolkit.Input.ShellHandRayPointer) 和傳送指標）會具現化並利用 (也會繪製線條來指出遙傳最後在) 的位置，而不是主要提供一般功能的類別。</span><span class="sxs-lookup"><span data-stu-id="a7c08-141">Generally, children classes such as the [`ShellHandRayPointer`](xref:Microsoft.MixedReality.Toolkit.Input.ShellHandRayPointer) and the teleport pointers are instantiated and utilized (which also draw lines to indicate where teleportation will end up at) instead of this class which primarily provides common functionality.</span></span>

<span data-ttu-id="a7c08-142">針對 Oculus、Vive 和 Windows Mixed Reality 等動作控制器，旋轉將符合控制器的旋轉。</span><span class="sxs-lookup"><span data-stu-id="a7c08-142">For motion controllers like in Oculus, Vive, and Windows Mixed Reality, the rotation will match the rotation of the controller.</span></span> <span data-ttu-id="a7c08-143">針對其他控制器（例如 HoloLens 2 表達的手），旋轉會符合系統提供的手邊指標。</span><span class="sxs-lookup"><span data-stu-id="a7c08-143">For other controllers like HoloLens 2 articulated hands, the rotation matches the system-provided pointing pose of the hand.</span></span>

<img src="../Images/Pointers/MRTK_Pointers_Line.png" width="400">

##### [`CurvePointer`](xref:Microsoft.MixedReality.Toolkit.Input.CurvePointer)

<span data-ttu-id="a7c08-144">*CurvePointer* 延伸 *LinePointer* 類別的方式，是允許沿著曲線的多重步驟光線轉換。</span><span class="sxs-lookup"><span data-stu-id="a7c08-144">*CurvePointer* extends the *LinePointer* class by allowing for multi-step ray casts along a curve.</span></span> <span data-ttu-id="a7c08-145">這個基底指標類別適用于彎曲的實例，例如遙傳指標，其中的線條會一直彎曲至 parabola。</span><span class="sxs-lookup"><span data-stu-id="a7c08-145">This base pointer class is useful for curved instances such as teleportation pointers where the line consistently bends into a parabola.</span></span>

##### [`ShellHandRayPointer`](xref:Microsoft.MixedReality.Toolkit.Input.ShellHandRayPointer)

<span data-ttu-id="a7c08-146">*ShellHandRayPointer* 的實值（延伸自 [`LinePointer`](xref:Microsoft.MixedReality.Toolkit.Input.MousePointer) ）是用來做為 *MRTK 指標設定檔* 的預設值。</span><span class="sxs-lookup"><span data-stu-id="a7c08-146">The implementation of *ShellHandRayPointer*, which extends from [`LinePointer`](xref:Microsoft.MixedReality.Toolkit.Input.MousePointer), is used as the default for the *MRTK Pointer Profile*.</span></span> <span data-ttu-id="a7c08-147">*DefaultControllerPointer* 預製專案會實作為 [`ShellHandRayPointer`](xref:Microsoft.MixedReality.Toolkit.Input.ShellHandRayPointer) 類別。</span><span class="sxs-lookup"><span data-stu-id="a7c08-147">The *DefaultControllerPointer* prefab implements the [`ShellHandRayPointer`](xref:Microsoft.MixedReality.Toolkit.Input.ShellHandRayPointer) class.</span></span>

##### [`GGVPointer`](xref:Microsoft.MixedReality.Toolkit.Input.GGVPointer)

<span data-ttu-id="a7c08-148">GGVPointer 也稱為「 *注視/手勢/語音」 (GGV)* 指標，其可支援 HoloLens 1 樣式的外觀和點一下互動，主要是透過注視和點擊，或注視和語音選取互動。</span><span class="sxs-lookup"><span data-stu-id="a7c08-148">Also known as the *Gaze/Gesture/Voice (GGV)* pointer, the GGVPointer powers HoloLens 1-style look and tap interactions, primarily via Gaze and Air Tap or Gaze and voice Select interaction.</span></span> <span data-ttu-id="a7c08-149">GGV 指標的位置和方向是由標頭的位置和旋轉所驅動。</span><span class="sxs-lookup"><span data-stu-id="a7c08-149">The GGV pointer's position and direction is driven by the head's position and rotation.</span></span>

##### [`TouchPointer`](xref:Microsoft.MixedReality.Toolkit.Input.TouchPointer)

<span data-ttu-id="a7c08-150">*TouchPointer* 負責使用 Unity 觸控輸入 (也就是觸控式螢幕) 。</span><span class="sxs-lookup"><span data-stu-id="a7c08-150">The *TouchPointer* is responsible for working with Unity Touch input (i.e. touchscreen).</span></span> <span data-ttu-id="a7c08-151">這些都是「遠的互動」，因為觸及螢幕的動作會將攝影機的光線轉換成場景中可能的位置。</span><span class="sxs-lookup"><span data-stu-id="a7c08-151">These are 'far interactions' because the act of touching the screen will cast a ray from the camera to a potentially far location in the scene.</span></span>

##### [`MousePointer`](xref:Microsoft.MixedReality.Toolkit.Input.MousePointer)

<span data-ttu-id="a7c08-152">*MousePointer* 可讓螢幕到世界 raycast，以進行遠距離的互動，而非觸控。</span><span class="sxs-lookup"><span data-stu-id="a7c08-152">The *MousePointer* powers a screen to world raycast for far interactions, but for mouse instead of touch.</span></span>

![滑鼠指標](../Images/Pointers/MRTK_MousePointer.png)

> [!NOTE]
> <span data-ttu-id="a7c08-154">依預設，在 MRTK 中並不提供滑鼠支援，但可以藉由將類型的新 *輸入 Data Provider* 新增 [`MouseDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput.MouseDeviceManager) 至 MRTK 輸入設定檔，並將指派 [`MixedRealityMouseInputProfile`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityMouseInputProfile) 給資料提供者來啟用。</span><span class="sxs-lookup"><span data-stu-id="a7c08-154">Mouse support is not available by default in MRTK but can be enabled by adding a new *Input Data Provider* of type [`MouseDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput.MouseDeviceManager) to the MRTK input profile and assigning the [`MixedRealityMouseInputProfile`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityMouseInputProfile) to the data provider.</span></span>

#### <a name="near-pointers"></a><span data-ttu-id="a7c08-155">近端指標</span><span class="sxs-lookup"><span data-stu-id="a7c08-155">Near pointers</span></span>

##### [`PokePointer`](xref:Microsoft.MixedReality.Toolkit.Input.PokePointer)

<span data-ttu-id="a7c08-156">*[PokePointer](xref:Microsoft.MixedReality.Toolkit.Input.PokePointer)* 是用來與支援「近距離互動可觸式」的遊戲物件互動。</span><span class="sxs-lookup"><span data-stu-id="a7c08-156">The *[PokePointer](xref:Microsoft.MixedReality.Toolkit.Input.PokePointer)* is used to interact with game objects that support “near interaction touchable.”</span></span> <span data-ttu-id="a7c08-157">具有附加腳本的 Gameobject [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) 。</span><span class="sxs-lookup"><span data-stu-id="a7c08-157">which are GameObjects that have an attached [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) script.</span></span> <span data-ttu-id="a7c08-158">在 UnityUI 的案例中，此指標會尋找 NearInteractionTouchableUnityUIs。</span><span class="sxs-lookup"><span data-stu-id="a7c08-158">In the case of UnityUI, this pointer looks for NearInteractionTouchableUnityUIs.</span></span>  <span data-ttu-id="a7c08-159">PokePointer 會使用 SphereCast 來決定最接近的可觸式元素，並用它來開啟 pressable 按鈕之類的功能。</span><span class="sxs-lookup"><span data-stu-id="a7c08-159">The PokePointer uses a SphereCast to determine the closest touchable element and is used to power things like the pressable buttons.</span></span>

 <span data-ttu-id="a7c08-160">使用元件設定 GameObject 時 [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) ，請務必將 *localForward* 參數設定為指向按鈕或其他應設為可觸式之物件的前方。</span><span class="sxs-lookup"><span data-stu-id="a7c08-160">When configuring the GameObject with the [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) component, make sure to configure the *localForward* parameter to point out of the front of the button or other object that should be made touchable.</span></span> <span data-ttu-id="a7c08-161">也請確定可觸式的 *界限* 符合可觸式物件的界限。</span><span class="sxs-lookup"><span data-stu-id="a7c08-161">Also make sure that the touchable's *bounds* matches the bounds of the touchable object.</span></span>

<span data-ttu-id="a7c08-162">有用的連結指標屬性：</span><span class="sxs-lookup"><span data-stu-id="a7c08-162">Useful Poke Pointer properties:</span></span>

- <span data-ttu-id="a7c08-163">*TouchableDistance*：可與可觸式介面互動的最大距離</span><span class="sxs-lookup"><span data-stu-id="a7c08-163">*TouchableDistance*: Maximum distance in which a touchable surface can be interacted with</span></span>
- <span data-ttu-id="a7c08-164">*視覺效果*：用來轉譯手指視覺 () 的遊戲物件，預設為。</span><span class="sxs-lookup"><span data-stu-id="a7c08-164">*Visuals*: Game object used to render finger tip visual (the ring on finger, by default).</span></span>
- <span data-ttu-id="a7c08-165">*Line*：從 fingertip 到現用輸入介面所要繪製的選擇性線條。</span><span class="sxs-lookup"><span data-stu-id="a7c08-165">*Line*: Optional line to draw from fingertip to the active input surface.</span></span>
- <span data-ttu-id="a7c08-166">LayerMasks *圖層遮罩*-優先順序較高的陣列，以判斷指標可與其互動的可能 gameobject，以及嘗試的互動順序。</span><span class="sxs-lookup"><span data-stu-id="a7c08-166">*Poke Layer Masks* - A prioritized array of LayerMasks to determine which possible GameObjects the pointer can interact with and the order of interaction to attempt.</span></span> <span data-ttu-id="a7c08-167">請注意，GameObject 也必須有 `NearInteractionTouchable` 元件，才能與處理常式指標互動。</span><span class="sxs-lookup"><span data-stu-id="a7c08-167">Note that a GameObject must also have a `NearInteractionTouchable` component in order to interact with a poke pointer.</span></span>

<img src="../Images/Pointers/MRTK_PokePointer.png" width="400">

##### [`SpherePointer`](xref:Microsoft.MixedReality.Toolkit.Input.SpherePointer)

<span data-ttu-id="a7c08-168">*[SpherePointer](xref:Microsoft.MixedReality.Toolkit.Input.SpherePointer)* 會使用 [UnityEngine](https://docs.unity3d.com/ScriptReference/Physics.OverlapSphere.html)來識別最接近的 [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) 互動物件，這對類似的 "grabbable" 輸入很有用 `ManipulationHandler` 。</span><span class="sxs-lookup"><span data-stu-id="a7c08-168">The *[SpherePointer](xref:Microsoft.MixedReality.Toolkit.Input.SpherePointer)* uses [UnityEngine.Physics.OverlapSphere](https://docs.unity3d.com/ScriptReference/Physics.OverlapSphere.html) in order to identify the closest [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) object for interaction, which is useful for "grabbable" input like the `ManipulationHandler`.</span></span> <span data-ttu-id="a7c08-169">與 [`PokePointer`](xref:Microsoft.MixedReality.Toolkit.Input.PokePointer) / [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) 功能配對類似，為了與球體指標互動，遊戲物件必須包含腳本的元件 [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) 。</span><span class="sxs-lookup"><span data-stu-id="a7c08-169">Similar to the [`PokePointer`](xref:Microsoft.MixedReality.Toolkit.Input.PokePointer)/[`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) functional pair, in order to be interactable with the Sphere Pointer, the game object must contain a component that is the [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) script.</span></span>

<img src="../Images/Pointers/MRTK_GrabPointer.jpg" width="400">

<span data-ttu-id="a7c08-170">實用的球體指標屬性：</span><span class="sxs-lookup"><span data-stu-id="a7c08-170">Useful Sphere Pointer properties:</span></span>

- <span data-ttu-id="a7c08-171">*球體轉換半徑*：用來查詢 grabbable 物件之球體的半徑。</span><span class="sxs-lookup"><span data-stu-id="a7c08-171">*Sphere Cast Radius*: The radius for the sphere used to query for grabbable objects.</span></span>
- <span data-ttu-id="a7c08-172">*抓取圖層遮罩* -LayerMasks 的優先陣列，以判斷指標可與其互動的可能 gameobject，以及嘗試的互動順序。</span><span class="sxs-lookup"><span data-stu-id="a7c08-172">*Grab Layer Masks* - A prioritized array of LayerMasks to determine which possible GameObjects the pointer can interact with and the order of interaction to attempt.</span></span> <span data-ttu-id="a7c08-173">請注意，GameObject 也必須有 `NearInteractionGrabbable` ，才能與 SpherePointer 互動。</span><span class="sxs-lookup"><span data-stu-id="a7c08-173">Note that a GameObject must also have a `NearInteractionGrabbable` to interact with a SpherePointer.</span></span>
    > [!NOTE]
    > <span data-ttu-id="a7c08-174">空間感知層會在 MRTK 提供的預設 GrabPointer 預製專案中停用。</span><span class="sxs-lookup"><span data-stu-id="a7c08-174">The Spatial Awareness layer is disabled in the default GrabPointer prefab provided by MRTK.</span></span> <span data-ttu-id="a7c08-175">這樣做的目的是為了降低使用空間網格來執行球體重迭查詢的效能影響。</span><span class="sxs-lookup"><span data-stu-id="a7c08-175">This is done to reduce performance impact of doing a sphere overlap query with the spatial mesh.</span></span> <span data-ttu-id="a7c08-176">您可以藉由修改 GrabPointer 預製專案來啟用此項。</span><span class="sxs-lookup"><span data-stu-id="a7c08-176">You can enable this by modifying the GrabPointer prefab.</span></span>
- <span data-ttu-id="a7c08-177">*忽略不在 FOV 中的 Colliders* -是否忽略可能接近指標的 Colliders，而不是實際在視覺效果 FOV 中的。</span><span class="sxs-lookup"><span data-stu-id="a7c08-177">*Ignore Colliders Not in FOV* - Whether to ignore colliders that may be near the pointer, but not actually in the visual FOV.</span></span>
<span data-ttu-id="a7c08-178">這可能會導致意外的抓取，並可讓您在接近 grabbable 但看不到時，可以開啟手片。</span><span class="sxs-lookup"><span data-stu-id="a7c08-178">This can prevent accidental grabs, and will allow hand rays to turn on when you may be near a grabbable but cannot see it.</span></span> <span data-ttu-id="a7c08-179">*視覺效果 FOV* 是透過錐形來定義，而不是基於效能考慮而使用一般的錐。</span><span class="sxs-lookup"><span data-stu-id="a7c08-179">The *Visual FOV* is defined via a cone instead of the the typical frustum for performance reasons.</span></span> <span data-ttu-id="a7c08-180">這個錐形的中心和方向與相機的錐狀相同，半徑等於半顯示器高度 (或垂直 FOV) 。</span><span class="sxs-lookup"><span data-stu-id="a7c08-180">This cone is centered and oriented the same as the camera's frustum with a radius equal to half display height(or vertical FOV).</span></span>

<img src="../Images/Input/Pointers/SpherePointer_VisualFOV.png" width="200">

#### <a name="teleport-pointers"></a><span data-ttu-id="a7c08-181">傳送指標</span><span class="sxs-lookup"><span data-stu-id="a7c08-181">Teleport pointers</span></span>

- <span data-ttu-id="a7c08-182">[`TeleportPointer`](xref:Microsoft.MixedReality.Toolkit.Teleport.TeleportPointer) 會在採取動作時引發傳送要求 (例如</span><span class="sxs-lookup"><span data-stu-id="a7c08-182">[`TeleportPointer`](xref:Microsoft.MixedReality.Toolkit.Teleport.TeleportPointer) will raise a teleport request when action is taken (i.e</span></span> <span data-ttu-id="a7c08-183">您可以按下 [傳送] 按鈕) ，以移動使用者。</span><span class="sxs-lookup"><span data-stu-id="a7c08-183">the teleport button is pressed) in order to move the user.</span></span>
- <span data-ttu-id="a7c08-184">[`ParabolicTeleportPointer`](xref:Microsoft.MixedReality.Toolkit.Teleport.ParabolicTeleportPointer) 會在採取動作時引發傳送要求 (例如</span><span class="sxs-lookup"><span data-stu-id="a7c08-184">[`ParabolicTeleportPointer`](xref:Microsoft.MixedReality.Toolkit.Teleport.ParabolicTeleportPointer) will raise a teleport request when action is taken (i.e</span></span> <span data-ttu-id="a7c08-185">[傳送] 按鈕會按下) 拋物線行 raycast，以便移動使用者。</span><span class="sxs-lookup"><span data-stu-id="a7c08-185">the teleport button is pressed) with a parabolic line raycast in order to move the user.</span></span>

<img src="../Images/Pointers/MRTK_Pointers_Parabolic.png" width="400">

## <a name="pointer-support-for-mixed-reality-platforms"></a><span data-ttu-id="a7c08-186">混合現實平臺的指標支援</span><span class="sxs-lookup"><span data-stu-id="a7c08-186">Pointer support for mixed reality platforms</span></span>

<span data-ttu-id="a7c08-187">下表詳細說明通常用於 MRTK 中常見平臺的指標類型。</span><span class="sxs-lookup"><span data-stu-id="a7c08-187">The following table details the pointer types that are typically used for the common platforms in MRTK.</span></span> <span data-ttu-id="a7c08-188">注意：您可以將不同的指標類型加入至這些平臺。</span><span class="sxs-lookup"><span data-stu-id="a7c08-188">NOTE: it's possible to add different pointer types to these platforms.</span></span> <span data-ttu-id="a7c08-189">例如，您可以將「前往指標」或「球體」指標加入至 VR。</span><span class="sxs-lookup"><span data-stu-id="a7c08-189">For example, you could add a Poke pointer or Sphere pointer to VR.</span></span> <span data-ttu-id="a7c08-190">此外，使用遊戲台的 VR 裝置可以使用 GGV 指標。</span><span class="sxs-lookup"><span data-stu-id="a7c08-190">Additionally, VR devices with a gamepad could use the GGV pointer.</span></span>

|                     | <span data-ttu-id="a7c08-191">OpenVR</span><span class="sxs-lookup"><span data-stu-id="a7c08-191">OpenVR</span></span>  | <span data-ttu-id="a7c08-192">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="a7c08-192">Windows Mixed Reality</span></span> | <span data-ttu-id="a7c08-193">HoloLens 1</span><span class="sxs-lookup"><span data-stu-id="a7c08-193">HoloLens 1</span></span> | <span data-ttu-id="a7c08-194">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="a7c08-194">HoloLens 2</span></span> |
|---------------------|---------|-----------------------|------------|------------|
| <span data-ttu-id="a7c08-195">ShellHandRayPointer</span><span class="sxs-lookup"><span data-stu-id="a7c08-195">ShellHandRayPointer</span></span> | <span data-ttu-id="a7c08-196">有效</span><span class="sxs-lookup"><span data-stu-id="a7c08-196">Valid</span></span>   | <span data-ttu-id="a7c08-197">有效</span><span class="sxs-lookup"><span data-stu-id="a7c08-197">Valid</span></span>                 |            | <span data-ttu-id="a7c08-198">有效</span><span class="sxs-lookup"><span data-stu-id="a7c08-198">Valid</span></span>      |
| <span data-ttu-id="a7c08-199">TeleportPointer</span><span class="sxs-lookup"><span data-stu-id="a7c08-199">TeleportPointer</span></span>     | <span data-ttu-id="a7c08-200">有效</span><span class="sxs-lookup"><span data-stu-id="a7c08-200">Valid</span></span>   | <span data-ttu-id="a7c08-201">有效</span><span class="sxs-lookup"><span data-stu-id="a7c08-201">Valid</span></span>                 |            |            |
| <span data-ttu-id="a7c08-202">GGVPointer</span><span class="sxs-lookup"><span data-stu-id="a7c08-202">GGVPointer</span></span>          |         |                       | <span data-ttu-id="a7c08-203">有效</span><span class="sxs-lookup"><span data-stu-id="a7c08-203">Valid</span></span>      |            |
| <span data-ttu-id="a7c08-204">SpherePointer</span><span class="sxs-lookup"><span data-stu-id="a7c08-204">SpherePointer</span></span>       |         |                       |            | <span data-ttu-id="a7c08-205">有效</span><span class="sxs-lookup"><span data-stu-id="a7c08-205">Valid</span></span>      |
| <span data-ttu-id="a7c08-206">PokePointer</span><span class="sxs-lookup"><span data-stu-id="a7c08-206">PokePointer</span></span>         |         |                       |            | <span data-ttu-id="a7c08-207">有效</span><span class="sxs-lookup"><span data-stu-id="a7c08-207">Valid</span></span>      |

## <a name="pointer-interactions-via-code"></a><span data-ttu-id="a7c08-208">透過程式碼的指標互動</span><span class="sxs-lookup"><span data-stu-id="a7c08-208">Pointer interactions via code</span></span>

### <a name="pointer-event-interfaces"></a><span data-ttu-id="a7c08-209">指標事件介面</span><span class="sxs-lookup"><span data-stu-id="a7c08-209">Pointer event interfaces</span></span>

<span data-ttu-id="a7c08-210">MonoBehaviours，它會執行下列一或多個介面，並將其指派給包含 `Collider` 相關聯介面所定義之指標互動事件的 GameObject。</span><span class="sxs-lookup"><span data-stu-id="a7c08-210">MonoBehaviours that implement one or more of the following interfaces and are assigned to a GameObject with a `Collider` will receive Pointer interactions events as defined by the associated interface.</span></span>

| <span data-ttu-id="a7c08-211">事件</span><span class="sxs-lookup"><span data-stu-id="a7c08-211">Event</span></span> | <span data-ttu-id="a7c08-212">描述</span><span class="sxs-lookup"><span data-stu-id="a7c08-212">Description</span></span> | <span data-ttu-id="a7c08-213">處理常式</span><span class="sxs-lookup"><span data-stu-id="a7c08-213">Handler</span></span> |
| --- | --- | --- |
| <span data-ttu-id="a7c08-214">焦點變更/焦點變更前</span><span class="sxs-lookup"><span data-stu-id="a7c08-214">Before Focus Changed / Focus Changed</span></span> | <span data-ttu-id="a7c08-215">在遊戲物件上引發焦點，並在每次指標改變焦點時取得。</span><span class="sxs-lookup"><span data-stu-id="a7c08-215">Raised on both the game object losing focus and the one gaining it every time a pointer changes focus.</span></span> | [`IMixedRealityFocusChangedHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityFocusChangedHandler) |
<span data-ttu-id="a7c08-216">焦點進入/離開</span><span class="sxs-lookup"><span data-stu-id="a7c08-216">Focus Enter / Exit</span></span> | <span data-ttu-id="a7c08-217">當第一個指標進入焦點時，會在遊戲物件上引發焦點，並在最後一個指標離開焦點時取得焦點。</span><span class="sxs-lookup"><span data-stu-id="a7c08-217">Raised on the game object gaining focus when the first pointer enters it and on the one losing focus when the last pointer leaves it.</span></span> | [`IMixedRealityFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityFocusHandler)
<span data-ttu-id="a7c08-218">指標向下/拖曳/向上/按一下</span><span class="sxs-lookup"><span data-stu-id="a7c08-218">Pointer Down / Dragged / Up / Clicked</span></span> | <span data-ttu-id="a7c08-219">引發至報表指標按下、拖曳和釋放。</span><span class="sxs-lookup"><span data-stu-id="a7c08-219">Raised to report pointer press, drag and release.</span></span> | [`IMixedRealityPointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointerHandler)
<span data-ttu-id="a7c08-220">Touch 已開始/更新/已完成</span><span class="sxs-lookup"><span data-stu-id="a7c08-220">Touch Started / Updated / Completed</span></span> | <span data-ttu-id="a7c08-221">由觸控感知指標引發，例如 [`PokePointer`](xref:Microsoft.MixedReality.Toolkit.Input.PokePointer) 報告觸控活動。</span><span class="sxs-lookup"><span data-stu-id="a7c08-221">Raised by touch-aware pointers like [`PokePointer`](xref:Microsoft.MixedReality.Toolkit.Input.PokePointer) to report touch activity.</span></span> | [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler)

> [!NOTE]
> <span data-ttu-id="a7c08-222">[`IMixedRealityFocusChangedHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityFocusChangedHandler) 而且 [`IMixedRealityFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityFocusHandler) 應該在引發它們的物件中處理。</span><span class="sxs-lookup"><span data-stu-id="a7c08-222">[`IMixedRealityFocusChangedHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityFocusChangedHandler) and [`IMixedRealityFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityFocusHandler) should be handled in the objects they are raised on.</span></span> <span data-ttu-id="a7c08-223">您可以全域接收焦點事件，但是與其他輸入事件不同的是，全域事件處理常式不會根據焦點封鎖接收事件 (事件將會由全域處理常式和焦點) 中的對應物件接收。</span><span class="sxs-lookup"><span data-stu-id="a7c08-223">It is possible to receive focus events globally but, unlike other input events, global event handler won't block receiving events based on focus (the event will be received by both global handler and a corresponding object in focus).</span></span>

#### <a name="pointer-input-events-in-action"></a><span data-ttu-id="a7c08-224">作用中的指標輸入事件</span><span class="sxs-lookup"><span data-stu-id="a7c08-224">Pointer input events in action</span></span>

<span data-ttu-id="a7c08-225">MRTK 輸入系統可辨識並處理指標輸入事件，與 [一般輸入事件](InputEvents.md#input-events-in-action)的方式類似。</span><span class="sxs-lookup"><span data-stu-id="a7c08-225">Pointer input events are recognized and handled by the MRTK input system in a similar way as [regular input events](InputEvents.md#input-events-in-action).</span></span> <span data-ttu-id="a7c08-226">不同之處在于指標輸入事件只會由引發輸入事件的指標，以及任何全域輸入處理常式的 GameObject 來處理。</span><span class="sxs-lookup"><span data-stu-id="a7c08-226">The difference being that pointer input events are handled only by the GameObject in focus by the pointer that fired the input event, as well as any global input handlers.</span></span> <span data-ttu-id="a7c08-227">一般輸入事件是由所有使用中指標的焦點 Gameobject 來處理。</span><span class="sxs-lookup"><span data-stu-id="a7c08-227">Regular input events are handled by GameObjects in focus for all active pointers.</span></span>

1. <span data-ttu-id="a7c08-228">MRTK 輸入系統可識別輸入事件已發生</span><span class="sxs-lookup"><span data-stu-id="a7c08-228">The MRTK input system recognizes an input event has occurred</span></span>
1. <span data-ttu-id="a7c08-229">MRTK 輸入系統會將輸入事件的相關介面函式引發至所有已註冊的全域輸入處理常式</span><span class="sxs-lookup"><span data-stu-id="a7c08-229">The MRTK input system fires the relevant interface function for the input event to all registered global input handlers</span></span>
1. <span data-ttu-id="a7c08-230">輸入系統會決定要將哪些 GameObject 放在引發事件的指標</span><span class="sxs-lookup"><span data-stu-id="a7c08-230">The input system determines which GameObject is in focus for the pointer that fired the event</span></span>
    1. <span data-ttu-id="a7c08-231">輸入系統會利用 [Unity 的事件系統](https://docs.unity3d.com/Manual/EventSystem.html) 來引發焦點 GameObject 上所有相符元件的相關介面函式</span><span class="sxs-lookup"><span data-stu-id="a7c08-231">The input system utilizes the [Unity's Event System](https://docs.unity3d.com/Manual/EventSystem.html) to fire the relevant interface function for all matching components on the focused GameObject</span></span>
    1. <span data-ttu-id="a7c08-232">如果您在任何時間點輸入事件已 [標示為已使用](inputevents.md#how-to-stop-input-events)，進程將會結束，且不會有進一步的 gameobject 接收回呼。</span><span class="sxs-lookup"><span data-stu-id="a7c08-232">If at any point an input event has been [marked as used](inputevents.md#how-to-stop-input-events), the process will end and no further GameObjects will receive callbacks.</span></span>
        - <span data-ttu-id="a7c08-233">範例：將會搜尋執行介面的元件 [`IMixedRealityFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) ，以取得 GameObject 或失去焦點</span><span class="sxs-lookup"><span data-stu-id="a7c08-233">Example: Components implementing the interface [`IMixedRealityFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) will be searched for a GameObject gains or loses focus</span></span>
        - <span data-ttu-id="a7c08-234">注意：如果在目前的 GameObject 上找不到符合所需介面的元件，Unity 事件系統將會反升搜尋父 GameObject。</span><span class="sxs-lookup"><span data-stu-id="a7c08-234">Note: The Unity Event System will bubble up to search the parent GameObject if no components matching the desired interface are found on the current GameObject..</span></span>
1. <span data-ttu-id="a7c08-235">如果未註冊任何全域輸入處理常式，且找不到具有相符元件/介面的 GameObject，則輸入系統會呼叫每個已註冊的回溯輸入處理常式</span><span class="sxs-lookup"><span data-stu-id="a7c08-235">If no global input handlers are registered and no GameObject is found with a matching component/interface, then the input system will call each fallback registered input handlers</span></span>

#### <a name="example"></a><span data-ttu-id="a7c08-236">範例</span><span class="sxs-lookup"><span data-stu-id="a7c08-236">Example</span></span>

<span data-ttu-id="a7c08-237">以下範例腳本會在指標取得或離開焦點或指標選取物件時，變更附加轉譯器的色彩。</span><span class="sxs-lookup"><span data-stu-id="a7c08-237">Below is an example script that changes the color of the attached renderer when a pointer takes or leaves focus or when a pointer selects the object.</span></span>

```c#
public class ColorTap : MonoBehaviour, IMixedRealityFocusHandler, IMixedRealityPointerHandler
{
    private Color color_IdleState = Color.cyan;
    private Color color_OnHover = Color.white;
    private Color color_OnSelect = Color.blue;
    private Material material;

    private void Awake()
    {
        material = GetComponent<Renderer>().material;
    }

    void IMixedRealityFocusHandler.OnFocusEnter(FocusEventData eventData)
    {
        material.color = color_OnHover;
    }

    void IMixedRealityFocusHandler.OnFocusExit(FocusEventData eventData)
    {
        material.color = color_IdleState;
    }

    void IMixedRealityPointerHandler.OnPointerDown(
         MixedRealityPointerEventData eventData) { }

    void IMixedRealityPointerHandler.OnPointerDragged(
         MixedRealityPointerEventData eventData) { }

    void IMixedRealityPointerHandler.OnPointerClicked(MixedRealityPointerEventData eventData)
    {
        material.color = color_OnSelect;
    }
}
```

### <a name="query-pointers"></a><span data-ttu-id="a7c08-238">查詢指標</span><span class="sxs-lookup"><span data-stu-id="a7c08-238">Query pointers</span></span>

<span data-ttu-id="a7c08-239">您可以藉由迴圈查看可用的輸入來源，來收集目前作用中的所有指標 (例如</span><span class="sxs-lookup"><span data-stu-id="a7c08-239">It is possible to gather all pointers currently active by looping through the available input sources (i.e</span></span> <span data-ttu-id="a7c08-240">可用的控制器和輸入) 探索哪些指標附加至它們。</span><span class="sxs-lookup"><span data-stu-id="a7c08-240">controllers and inputs available) to discover which pointers are attached to them.</span></span>

```c#
var pointers = new HashSet<IMixedRealityPointer>();

// Find all valid pointers
foreach (var inputSource in CoreServices.InputSystem.DetectedInputSources)
{
    foreach (var pointer in inputSource.Pointers)
    {
        if (pointer.IsInteractionEnabled && !pointers.Contains(pointer))
        {
            pointers.Add(pointer);
        }
    }
}
```

#### <a name="primary-pointer"></a><span data-ttu-id="a7c08-241">主要指標</span><span class="sxs-lookup"><span data-stu-id="a7c08-241">Primary pointer</span></span>

<span data-ttu-id="a7c08-242">開發人員可以訂閱 FocusProviders PrimaryPointerChanged 事件，以在焦點的主要指標變更時收到通知。</span><span class="sxs-lookup"><span data-stu-id="a7c08-242">Developers can subscribe to the FocusProviders PrimaryPointerChanged event to be notified when the primary pointer in focus has changed.</span></span> <span data-ttu-id="a7c08-243">這項功能非常適合用來識別使用者目前是否透過注視或手的光線或其他輸入來源與場景互動。</span><span class="sxs-lookup"><span data-stu-id="a7c08-243">This can be extremely useful to identify if the user is currently interacting with a scene via gaze or a hand ray or another input source.</span></span>

```c#
private void OnEnable()
{
    var focusProvider = CoreServices.InputSystem?.FocusProvider;
    focusProvider?.SubscribeToPrimaryPointerChanged(OnPrimaryPointerChanged, true);
}

private void OnPrimaryPointerChanged(IMixedRealityPointer oldPointer, IMixedRealityPointer newPointer)
{
    ...
}

private void OnDisable()
{
    var focusProvider = CoreServices.InputSystem?.FocusProvider;
    focusProvider?.UnsubscribeFromPrimaryPointerChanged(OnPrimaryPointerChanged);

    // This flushes out the current primary pointer
    OnPrimaryPointerChanged(null, null);
}
```

<span data-ttu-id="a7c08-244">`PrimaryPointerExample` (資產/MRTK/範例/示範/輸入/場景/PrimaryPointer) 場景顯示如何使用 [`PrimaryPointerChangedHandler`](xref:Microsoft.MixedReality.Toolkit.Input.PrimaryPointerChangedHandler) for 事件來回應新的主要指標。</span><span class="sxs-lookup"><span data-stu-id="a7c08-244">The `PrimaryPointerExample` (Assets/MRTK/Examples/Demos/Input/Scenes/PrimaryPointer) scene shows how to use the [`PrimaryPointerChangedHandler`](xref:Microsoft.MixedReality.Toolkit.Input.PrimaryPointerChangedHandler) for events to respond to a new primary pointer.</span></span>

<img src="../../Documentation/Images/Pointers/PrimaryPointerExample.png" style="max-width:100%;">

### <a name="pointer-result"></a><span data-ttu-id="a7c08-245">指標結果</span><span class="sxs-lookup"><span data-stu-id="a7c08-245">Pointer result</span></span>

<span data-ttu-id="a7c08-246">指標 [`Result`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointer.Result) 屬性包含用來判斷具有焦點之物件的場景查詢目前的結果。</span><span class="sxs-lookup"><span data-stu-id="a7c08-246">The pointer [`Result`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointer.Result) property contains the current result for the scene query used to determine the object with focus.</span></span> <span data-ttu-id="a7c08-247">針對 raycast 指標，例如動作控制器預設所建立的指標、注視輸入和手光線，它會包含 raycast 點擊的位置和正常。</span><span class="sxs-lookup"><span data-stu-id="a7c08-247">For a raycast pointer, like the ones created by default for motion controllers, gaze input and hand rays, it will contain the location and normal of the raycast hit.</span></span>

```c#
private void IMixedRealityPointerHandler.OnPointerClicked(MixedRealityPointerEventData eventData)
{
    var result = eventData.Pointer.Result;
    var spawnPosition = result.Details.Point;
    var spawnRotation = Quaternion.LookRotation(result.Details.Normal);
    Instantiate(MyPrefab, spawnPosition, spawnRotation);
}
```

<span data-ttu-id="a7c08-248">`PointerResultExample`場景 (資產/MRTK/範例/示範/輸入/場景/PointerResult/PointerResultExample unity) 示範如何使用指標在叫用 [`Result`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointer.Result) 位置產生物件。</span><span class="sxs-lookup"><span data-stu-id="a7c08-248">The `PointerResultExample` scene (Assets/MRTK/Examples/Demos/Input/Scenes/PointerResult/PointerResultExample.unity) shows how to use the pointer [`Result`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointer.Result) to spawn an object at the hit location.</span></span>

<img src="../../Documentation/Images/Input/PointerResultExample.png" style="max-width:100%;">

### <a name="disable-pointers"></a><span data-ttu-id="a7c08-249">停用指標</span><span class="sxs-lookup"><span data-stu-id="a7c08-249">Disable pointers</span></span>

<span data-ttu-id="a7c08-250">若要啟用和停用指標 (例如，若要停用手光線) ，請透過設定 [`PointerBehavior`](xref:Microsoft.MixedReality.Toolkit.Input.PointerBehavior) 指定指標類型的 [`PointerUtils`](xref:Microsoft.MixedReality.Toolkit.Input.PointerUtils) 。</span><span class="sxs-lookup"><span data-stu-id="a7c08-250">To turn enable and disable pointers (for example, to disable the hand ray), set the [`PointerBehavior`](xref:Microsoft.MixedReality.Toolkit.Input.PointerBehavior) for a given pointer type via [`PointerUtils`](xref:Microsoft.MixedReality.Toolkit.Input.PointerUtils).</span></span>

```c#
// Disable the hand rays
PointerUtils.SetHandRayPointerBehavior(PointerBehavior.AlwaysOff);

// Disable hand rays for the right hand only
PointerUtils.SetHandRayPointerBehavior(PointerBehavior.AlwaysOff, Handedness.Right);

// Disable the gaze pointer
PointerUtils.SetGazePointerBehavior(PointerBehavior.AlwaysOff);

// Set the behavior to match HoloLens 1
// Note, if on HoloLens 2, you must configure your pointer profile to make the GGV pointer show up for articulated hands.
public void SetHoloLens1()
{
    PointerUtils.SetPokePointerBehavior(PointerBehavior.AlwaysOff, Handedness.Any);
    PointerUtils.SetGrabPointerBehavior(PointerBehavior.AlwaysOff, Handedness.Any);
    PointerUtils.SetRayPointerBehavior(PointerBehavior.AlwaysOff, Handedness.Any);
    PointerUtils.SetGGVBehavior(PointerBehavior.Default);
}
```

<span data-ttu-id="a7c08-251">[`PointerUtils`](xref:Microsoft.MixedReality.Toolkit.Input.PointerUtils)如需 [`TurnPointersOnOff`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.DisablePointersExample) 更多範例，請參閱和。</span><span class="sxs-lookup"><span data-stu-id="a7c08-251">See [`PointerUtils`](xref:Microsoft.MixedReality.Toolkit.Input.PointerUtils) and [`TurnPointersOnOff`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.DisablePointersExample) for more examples.</span></span>

## <a name="pointer-interactions-via-editor"></a><span data-ttu-id="a7c08-252">經由編輯器的指標互動</span><span class="sxs-lookup"><span data-stu-id="a7c08-252">Pointer interactions via editor</span></span>

<span data-ttu-id="a7c08-253">若為所處理的指標事件 [`IMixedRealityPointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointerHandler) ，MRTK 會以元件的形式提供進一步的便利性 [`PointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.PointerHandler) ，讓指標事件可以透過 Unity 事件直接處理。</span><span class="sxs-lookup"><span data-stu-id="a7c08-253">For pointer events handled by [`IMixedRealityPointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointerHandler), MRTK provides further convenience in the form of the [`PointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.PointerHandler) component, which allows pointer events to be handled directly via Unity Events.</span></span>

<img src="../Images/Pointers/PointerHandler.png" style="max-width:100%;">

## <a name="pointer-extent"></a><span data-ttu-id="a7c08-254">指標範圍</span><span class="sxs-lookup"><span data-stu-id="a7c08-254">Pointer extent</span></span>

<span data-ttu-id="a7c08-255">大部分的指標都有設定，這些設定會限制它們在場景中 raycast 和與其他物件互動的程度。</span><span class="sxs-lookup"><span data-stu-id="a7c08-255">Far pointers have settings which limit how far they will raycast and interact with other objects in the scene.</span></span>
<span data-ttu-id="a7c08-256">依預設，此值設定為10個計量。</span><span class="sxs-lookup"><span data-stu-id="a7c08-256">By default, this value is set to 10 meters.</span></span> <span data-ttu-id="a7c08-257">選擇這個值與 HoloLens shell 的行為保持一致。</span><span class="sxs-lookup"><span data-stu-id="a7c08-257">This value was chosen to remain consistent with the behavior of the HoloLens shell.</span></span>

<span data-ttu-id="a7c08-258">這可以藉由更新 `DefaultControllerPointer` 預製專案 [`ShellHandRayPointer`](xref:Microsoft.MixedReality.Toolkit.Input.ShellHandRayPointer) 元件的欄位來變更：</span><span class="sxs-lookup"><span data-stu-id="a7c08-258">This can be changed by updating the `DefaultControllerPointer` prefab's [`ShellHandRayPointer`](xref:Microsoft.MixedReality.Toolkit.Input.ShellHandRayPointer) component's fields:</span></span>

<span data-ttu-id="a7c08-259">*指標範圍* -這會控制指標會與之互動的最大距離。</span><span class="sxs-lookup"><span data-stu-id="a7c08-259">*Pointer Extent* - This controls the maximum distance that pointers will interact with.</span></span>

<span data-ttu-id="a7c08-260">*預設指標範圍* -這會控制當指標不與任何互動時，將呈現的指標光線/行長度。</span><span class="sxs-lookup"><span data-stu-id="a7c08-260">*Default Pointer Extent* - This controls the length of the pointer ray/line that will render when the pointer is not interacting with anything.</span></span>

## <a name="see-also"></a><span data-ttu-id="a7c08-261">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a7c08-261">See also</span></span>

- [<span data-ttu-id="a7c08-262">指標架構</span><span class="sxs-lookup"><span data-stu-id="a7c08-262">Pointer Architecture</span></span>](../Architecture/InputSystem/ControllersPointersAndFocus.md)
- [<span data-ttu-id="a7c08-263">輸入事件</span><span class="sxs-lookup"><span data-stu-id="a7c08-263">Input Events</span></span>](InputEvents.md)
