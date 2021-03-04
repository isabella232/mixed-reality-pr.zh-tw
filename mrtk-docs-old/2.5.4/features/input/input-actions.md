---
title: InputActions
description: 在 MRTK 中建立輸入動作的檔
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、InputActions、
ms.openlocfilehash: e8d6fd4d68cabe82c3c3d9bf430ff9ac1e31ed43
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/03/2021
ms.locfileid: "101779650"
---
# <a name="input-actions"></a><span data-ttu-id="181f7-104">輸入動作</span><span class="sxs-lookup"><span data-stu-id="181f7-104">Input actions</span></span>

<span data-ttu-id="181f7-105">[**輸入動作**](input-actions.md) 是原始輸入的抽象概念，目的是要協助隔離應用程式邏輯與產生輸入的特定輸入來源。</span><span class="sxs-lookup"><span data-stu-id="181f7-105">[**Input Actions**](input-actions.md) are abstractions over raw inputs meant to help isolating application logic from the specific input sources producing an input.</span></span> <span data-ttu-id="181f7-106">例如，它可能很有用，例如，定義 *選取* 動作並將它對應至滑鼠左鍵、遊戲台中的按鈕，以及6個 DOF 控制器中的觸發程式。</span><span class="sxs-lookup"><span data-stu-id="181f7-106">It can be useful, for example, to define a *Select* action and map it to the left mouse button, a button in a gamepad and a trigger in a 6 DOF controller.</span></span> <span data-ttu-id="181f7-107">然後，您可以讓應用程式邏輯接聽 *選取* 的輸入動作事件，而不需要知道可以產生的所有不同輸入。</span><span class="sxs-lookup"><span data-stu-id="181f7-107">You can then have your application logic listen for *Select* input action events instead of having to be aware of all the different inputs that can produce it.</span></span>

## <a name="creating-an-input-action"></a><span data-ttu-id="181f7-108">建立輸入動作</span><span class="sxs-lookup"><span data-stu-id="181f7-108">Creating an input action</span></span>

<span data-ttu-id="181f7-109">輸入動作是在 **輸入動作設定檔** 中設定，在混合現實工具組元件的 *輸入系統設定檔* 內、指定動作的名稱以及輸入的類型 (*軸條件約束* ，) 它可以對應到：</span><span class="sxs-lookup"><span data-stu-id="181f7-109">Input actions are configured in the **Input Actions Profile**, inside the *Input System Profile* in the Mixed Reality Toolkit component, specifying a name for the action and the type of inputs (*Axis Constraint*) it can be mapped to:</span></span>

<img src="../images/input/InputActions.png" alt="Input Action" style="max-width:100%;">

<span data-ttu-id="181f7-110">這些是 **軸條件約束** 最常使用的值：</span><span class="sxs-lookup"><span data-stu-id="181f7-110">These are the most mostly commonly used values for **Axis Constraint**:</span></span>

<span data-ttu-id="181f7-111">軸條件約束</span><span class="sxs-lookup"><span data-stu-id="181f7-111">Axis Constraint</span></span> | <span data-ttu-id="181f7-112">描述</span><span class="sxs-lookup"><span data-stu-id="181f7-112">Description</span></span>
--- | ---
<span data-ttu-id="181f7-113">Digital</span><span class="sxs-lookup"><span data-stu-id="181f7-113">Digital</span></span> | <span data-ttu-id="181f7-114">開啟/關閉輸入，例如遊戲台或滑鼠中的二進位按鈕。</span><span class="sxs-lookup"><span data-stu-id="181f7-114">On/off input like a binary button in a gamepad or mouse.</span></span>
<span data-ttu-id="181f7-115">單一軸</span><span class="sxs-lookup"><span data-stu-id="181f7-115">Single Axis</span></span> | <span data-ttu-id="181f7-116">單一軸將輸入與遊戲中的類比觸發程式相似。</span><span class="sxs-lookup"><span data-stu-id="181f7-116">Single axis analogue input like an analog trigger in a gamepad.</span></span>
<span data-ttu-id="181f7-117">雙軸</span><span class="sxs-lookup"><span data-stu-id="181f7-117">Dual Axis</span></span> | <span data-ttu-id="181f7-118">雙軸將輸入與操縱杆相似。</span><span class="sxs-lookup"><span data-stu-id="181f7-118">Dual axis analogue input like a thumbstick.</span></span>
<span data-ttu-id="181f7-119">六 Dof</span><span class="sxs-lookup"><span data-stu-id="181f7-119">Six Dof</span></span> | <span data-ttu-id="181f7-120">以6個 DOF 控制器所產生的平移和旋轉進行3D 姿勢。</span><span class="sxs-lookup"><span data-stu-id="181f7-120">3D pose with translation and rotation like the one produced by 6 DOF controllers.</span></span>

<span data-ttu-id="181f7-121">您可以在中找到完整清單 [`AxisType`](xref:Microsoft.MixedReality.Toolkit.Utilities.AxisType) 。</span><span class="sxs-lookup"><span data-stu-id="181f7-121">You can find the full list in [`AxisType`](xref:Microsoft.MixedReality.Toolkit.Utilities.AxisType).</span></span>

## <a name="mapping-input-to-actions"></a><span data-ttu-id="181f7-122">將輸入對應至動作</span><span class="sxs-lookup"><span data-stu-id="181f7-122">Mapping input to actions</span></span>

<span data-ttu-id="181f7-123">您對應輸入和動作的方式取決於輸入來源的類型：</span><span class="sxs-lookup"><span data-stu-id="181f7-123">The way you map an input to and action depends on the type of the input source:</span></span>

### <a name="controller-input"></a><span data-ttu-id="181f7-124">控制器輸入</span><span class="sxs-lookup"><span data-stu-id="181f7-124">Controller input</span></span>

<span data-ttu-id="181f7-125">移至 [*輸入系統設定檔*] 下的 [**控制器輸入對應設定檔**]。</span><span class="sxs-lookup"><span data-stu-id="181f7-125">Go to the **Controller Input Mapping Profile**, under the *Input System Profile*.</span></span> <span data-ttu-id="181f7-126">您會在這裡找到所有支援的控制器清單：</span><span class="sxs-lookup"><span data-stu-id="181f7-126">There you will find a list of all supported controllers:</span></span>

<img src="../images/input/ControllerInputMappingProfile.PNG" alt="Input maping profile" style="max-width:100%;">

<span data-ttu-id="181f7-127">選取您要設定的專案，其中會出現一個對話方塊視窗與所有控制器輸入，讓您為每個控制器輸入設定動作：</span><span class="sxs-lookup"><span data-stu-id="181f7-127">Select the one you want to configure and a dialog window will appear with all the controller inputs, allowing you to set an action for each of them:</span></span>

<img src="../images/input/InputActionAssignment.PNG" alt="Input Action Assignment" style="max-width:100%;">

### <a name="speech-input"></a><span data-ttu-id="181f7-128">語音輸入</span><span class="sxs-lookup"><span data-stu-id="181f7-128">Speech input</span></span>

<span data-ttu-id="181f7-129">在 **語音命令設定檔** 的 *輸入系統設定檔* 下，您可以找到目前定義的語音命令清單。</span><span class="sxs-lookup"><span data-stu-id="181f7-129">In the **Speech Command Profile**, under the *Input System Profile*, you'll find the list of currently defined speech commands.</span></span> <span data-ttu-id="181f7-130">若要將其中一個對應至動作，只需在 [ *動作* ] 下拉式清單中選取它。</span><span class="sxs-lookup"><span data-stu-id="181f7-130">To map one of them to an action, just select it in the *Action* drop down.</span></span>

<img src="../images/input/SpeechCommandsProfile.png" alt="Speech Commands profile" style="max-width:100%;">

### <a name="gesture-input"></a><span data-ttu-id="181f7-131">手勢輸入</span><span class="sxs-lookup"><span data-stu-id="181f7-131">Gesture input</span></span>

<span data-ttu-id="181f7-132">*輸入系統設定檔* 底下的 **手勢設定檔** 包含所有已定義的手勢。</span><span class="sxs-lookup"><span data-stu-id="181f7-132">The **Gestures Profile**, under the *Input System Profile*, contains all defined gestures.</span></span> <span data-ttu-id="181f7-133">您可以在 [ *動作* ] 下拉式清單中選取每個動作，以將其對應至動作。</span><span class="sxs-lookup"><span data-stu-id="181f7-133">You can map each of them to an action by selecting it in the *Action* drop down.</span></span>

<img src="../images/input/GestureProfile.png" alt="Gesture profile" style="max-width:100%;">

## <a name="handling-input-actions"></a><span data-ttu-id="181f7-134">處理輸入動作</span><span class="sxs-lookup"><span data-stu-id="181f7-134">Handling input actions</span></span>

> [!WARNING]
> <span data-ttu-id="181f7-135">目前只能使用本節所述的方法來處理 *數位* 類型的輸入動作。</span><span class="sxs-lookup"><span data-stu-id="181f7-135">Currently only input actions of *Digital* type can be handled using the methods described in this section.</span></span> <span data-ttu-id="181f7-136">針對其他動作類型，您必須改為直接處理對應輸入的事件。</span><span class="sxs-lookup"><span data-stu-id="181f7-136">For other action types, you'll have to handle directly the events for the corresponding inputs instead.</span></span> <span data-ttu-id="181f7-137">例如，若要處理對應至控制器輸入的6個 DOF 動作，您必須搭配 [`IMixedRealityGestureHandler<T>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler`1) T = 使用 [`MixedRealityPose`](xref:Microsoft.MixedReality.Toolkit.Utilities.MixedRealityPose) 。</span><span class="sxs-lookup"><span data-stu-id="181f7-137">For example, to handle a 6 DOF action mapped to controller inputs, you'll have to use [`IMixedRealityGestureHandler<T>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler`1) with T = [`MixedRealityPose`](xref:Microsoft.MixedReality.Toolkit.Utilities.MixedRealityPose).</span></span>

<span data-ttu-id="181f7-138">處理輸入動作最簡單的方式就是利用 [`InputActionHandler`](xref:Microsoft.MixedReality.Toolkit.Input.InputActionHandler) 腳本。</span><span class="sxs-lookup"><span data-stu-id="181f7-138">The easiest way to handle input actions is to make use of the [`InputActionHandler`](xref:Microsoft.MixedReality.Toolkit.Input.InputActionHandler) script.</span></span> <span data-ttu-id="181f7-139">這可讓您定義您想要接聽的動作，並使用 Unity 事件回應動作開始和結束事件。</span><span class="sxs-lookup"><span data-stu-id="181f7-139">This allows you to define the action you want to listen to and react to action started and ended events using Unity Events.</span></span>

<img src="../images/input/InputActionHandler.PNG" alt="Acton Handler" style="max-width:100%;">

<span data-ttu-id="181f7-140">如果您想要更多控制，您可以 [`IMixedRealityInputActionHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputActionHandler) 直接在腳本中執行介面。</span><span class="sxs-lookup"><span data-stu-id="181f7-140">If you want more control, you can implement the [`IMixedRealityInputActionHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputActionHandler) interface directly in your script.</span></span> <span data-ttu-id="181f7-141">如需透過處理常式介面處理事件的詳細資訊，請參閱 [**輸入事件**](input-events.md) 一節。</span><span class="sxs-lookup"><span data-stu-id="181f7-141">See the [**Input Events**](input-events.md) section for more details on event handling via handler interfaces.</span></span>

## <a name="examples"></a><span data-ttu-id="181f7-142">範例</span><span class="sxs-lookup"><span data-stu-id="181f7-142">Examples</span></span>

<span data-ttu-id="181f7-143">如需示範 `MRTK/Examples/Demos/Input/Scenes/InputActions` 如何建立動作、將其對應至控制器、語音和手勢輸入，以及用來在命令上旋轉物件的範例場景，請參閱。</span><span class="sxs-lookup"><span data-stu-id="181f7-143">See `MRTK/Examples/Demos/Input/Scenes/InputActions` for an example scene showing how to create an action, map it to controller, speech and gesture inputs and use it to rotate an object on command.</span></span>

<img src="../images/input/InputActionsExample.PNG" alt="Input action example" style="max-width:100%;">
