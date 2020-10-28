---
title: Unity 中的筆勢和運動控制器
description: 瞭解如何在 Unity 中使用手手勢和移動控制器來採取行動。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: 手勢、動作控制器、unity、注視、輸入
ms.openlocfilehash: 6b132e56e5d60e59fda53b95328580ed861ce75c
ms.sourcegitcommit: 4bb5544a0c74ac4e9766bab3401c9b30ee170a71
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2020
ms.locfileid: "92638555"
---
# <a name="gestures-and-motion-controllers-in-unity"></a><span data-ttu-id="b28c4-104">Unity 中的筆勢和運動控制器</span><span class="sxs-lookup"><span data-stu-id="b28c4-104">Gestures and motion controllers in Unity</span></span>

<span data-ttu-id="b28c4-105">您可以透過兩種主要方式，在您 [的 [Unity](gaze-in-unity.md)]、[ [手手勢](../../design/gaze-and-commit.md#composite-gestures) ] 和 [ [運動] 控制器](../../design/motion-controllers.md) 中針對 HoloLens 和沉浸式 HMD 採取行動。</span><span class="sxs-lookup"><span data-stu-id="b28c4-105">There are two key ways to take action on your [gaze in Unity](gaze-in-unity.md), [hand gestures](../../design/gaze-and-commit.md#composite-gestures) and [motion controllers](../../design/motion-controllers.md) in HoloLens and Immersive HMD.</span></span> <span data-ttu-id="b28c4-106">您可以透過 Unity 中的相同 Api，存取兩個空間輸入來源的資料。</span><span class="sxs-lookup"><span data-stu-id="b28c4-106">You access the data for both sources of spatial input through the same APIs in Unity.</span></span>

<span data-ttu-id="b28c4-107">Unity 提供兩種主要方式來存取 Windows Mixed Reality 的空間輸入資料、 *GetButton/輸入 GetAxis* api （可跨多個 Unity XR sdk 運作），以及 Windows Mixed Reality 的特定 *InteractionManager/GestureRecognizer* api，該 api 會公開可用的完整空間輸入資料集。</span><span class="sxs-lookup"><span data-stu-id="b28c4-107">Unity provides two primary ways to access spatial input data for Windows Mixed Reality, the common *Input.GetButton/Input.GetAxis* APIs that work across multiple Unity XR SDKs, and an *InteractionManager/GestureRecognizer* API specific to Windows Mixed Reality that exposes the full set of spatial input data available.</span></span>

## <a name="unity-buttonaxis-mapping-table"></a><span data-ttu-id="b28c4-108">Unity 按鈕/軸對應表</span><span class="sxs-lookup"><span data-stu-id="b28c4-108">Unity button/axis mapping table</span></span>

<span data-ttu-id="b28c4-109">下表中的按鈕和軸識別碼可透過 *GetButton/GetAxis* api，在 Unity 的輸入管理員中受到支援，而「Windows MR 特定」資料行則是指可從 *InteractionSourceState* 類型中 Windows Mixed Reality 取得的屬性。</span><span class="sxs-lookup"><span data-stu-id="b28c4-109">The button and axis IDs in the table below are supported in Unity's Input Manager for Windows Mixed Reality motion controllers through the *Input.GetButton/GetAxis* APIs, while the "Windows MR-specific" column refers to properties available off of the *InteractionSourceState* type.</span></span> <span data-ttu-id="b28c4-110">下列各節將詳細說明每個 Api。</span><span class="sxs-lookup"><span data-stu-id="b28c4-110">Each of these APIs are described in detail in the sections below.</span></span>

<span data-ttu-id="b28c4-111">Windows Mixed Reality 的按鈕/軸識別碼對應通常會符合 Oculus 按鈕/軸識別碼。</span><span class="sxs-lookup"><span data-stu-id="b28c4-111">The button/axis ID mappings for Windows Mixed Reality generally match the Oculus button/axis IDs.</span></span>

<span data-ttu-id="b28c4-112">Windows Mixed Reality 的按鈕/軸識別碼對應有兩種不同于 OpenVR 的對應：</span><span class="sxs-lookup"><span data-stu-id="b28c4-112">The button/axis ID mappings for Windows Mixed Reality differ from OpenVR's mappings in two ways:</span></span>
1. <span data-ttu-id="b28c4-113">對應會使用與操縱杆不同的觸控板識別碼，以支援具有 thumbsticks 和 touchpads 的控制器。</span><span class="sxs-lookup"><span data-stu-id="b28c4-113">The mapping uses touchpad IDs that are distinct from thumbstick, to support controllers with both thumbsticks and touchpads.</span></span>
2. <span data-ttu-id="b28c4-114">對應可避免多載功能表按鈕的 A 和 X 按鈕識別碼，讓它們可用於實體 ABXY 按鈕。</span><span class="sxs-lookup"><span data-stu-id="b28c4-114">The mapping avoids overloading the A and X button IDs for the Menu buttons, to leave those available for physical ABXY buttons.</span></span>

<table>
<tr>
<th rowspan="2"><span data-ttu-id="b28c4-115">輸入</span><span class="sxs-lookup"><span data-stu-id="b28c4-115">Input</span></span> </th><th colspan="2"><span data-ttu-id="b28c4-116"><a href="gestures-and-motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis">通用 Unity API</a></span><span class="sxs-lookup"><span data-stu-id="b28c4-116"><a href="gestures-and-motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis">Common Unity APIs</a></span></span><br /><span data-ttu-id="b28c4-117"> (輸入. GetButton/GetAxis) </span><span class="sxs-lookup"><span data-stu-id="b28c4-117">(Input.GetButton/GetAxis)</span></span> </th><th rowspan="2"><span data-ttu-id="b28c4-118"><a href="gestures-and-motion-controllers-in-unity.md#">Windows MR 專用輸入 API</a></span><span class="sxs-lookup"><span data-stu-id="b28c4-118"><a href="gestures-and-motion-controllers-in-unity.md#">Windows MR-specific Input API</a></span></span><br /><span data-ttu-id="b28c4-119"> (XR。Wsa。輸入) </span><span class="sxs-lookup"><span data-stu-id="b28c4-119">(XR.WSA.Input)</span></span></th>
</tr><tr>
<th> <span data-ttu-id="b28c4-120">左手</span><span class="sxs-lookup"><span data-stu-id="b28c4-120">Left hand</span></span> </th><th> <span data-ttu-id="b28c4-121">右手</span><span class="sxs-lookup"><span data-stu-id="b28c4-121">Right hand</span></span></th>
</tr><tr>
<td> <span data-ttu-id="b28c4-122">已按下 Select 觸發程式</span><span class="sxs-lookup"><span data-stu-id="b28c4-122">Select trigger pressed</span></span> </td><td> <span data-ttu-id="b28c4-123">軸 9 = 1。0</span><span class="sxs-lookup"><span data-stu-id="b28c4-123">Axis 9 = 1.0</span></span> </td><td> <span data-ttu-id="b28c4-124">軸 10 = 1。0</span><span class="sxs-lookup"><span data-stu-id="b28c4-124">Axis 10 = 1.0</span></span> </td><td> <span data-ttu-id="b28c4-125">selectPressed</span><span class="sxs-lookup"><span data-stu-id="b28c4-125">selectPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="b28c4-126">選取觸發程式類比值</span><span class="sxs-lookup"><span data-stu-id="b28c4-126">Select trigger analog value</span></span> </td><td> <span data-ttu-id="b28c4-127">軸9</span><span class="sxs-lookup"><span data-stu-id="b28c4-127">Axis 9</span></span> </td><td> <span data-ttu-id="b28c4-128">軸10</span><span class="sxs-lookup"><span data-stu-id="b28c4-128">Axis 10</span></span> </td><td> <span data-ttu-id="b28c4-129">selectPressedAmount</span><span class="sxs-lookup"><span data-stu-id="b28c4-129">selectPressedAmount</span></span></td>
</tr><tr>
<td> <span data-ttu-id="b28c4-130">選取觸發程式部分按下</span><span class="sxs-lookup"><span data-stu-id="b28c4-130">Select trigger partially pressed</span></span> </td><td> <span data-ttu-id="b28c4-131">按鈕 14 <i> (遊戲台相容性) </i> </span><span class="sxs-lookup"><span data-stu-id="b28c4-131">Button 14 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="b28c4-132">按鈕 15 <i> (遊戲台相容性) </i> </span><span class="sxs-lookup"><span data-stu-id="b28c4-132">Button 15 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="b28c4-133">selectPressedAmount &gt; 0。0</span><span class="sxs-lookup"><span data-stu-id="b28c4-133">selectPressedAmount &gt; 0.0</span></span></td>
</tr><tr>
<td> <span data-ttu-id="b28c4-134">已按下功能表按鈕</span><span class="sxs-lookup"><span data-stu-id="b28c4-134">Menu button pressed</span></span> </td><td> <span data-ttu-id="b28c4-135">按鈕 6 \*</span><span class="sxs-lookup"><span data-stu-id="b28c4-135">Button 6\*</span></span> </td><td> <span data-ttu-id="b28c4-136">按鈕 7 \*</span><span class="sxs-lookup"><span data-stu-id="b28c4-136">Button 7\*</span></span> </td><td> <span data-ttu-id="b28c4-137">menuPressed</span><span class="sxs-lookup"><span data-stu-id="b28c4-137">menuPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="b28c4-138">已按下手柄按鈕</span><span class="sxs-lookup"><span data-stu-id="b28c4-138">Grip button pressed</span></span> </td><td> <span data-ttu-id="b28c4-139">軸 11 = 1.0 (沒有類比值) </span><span class="sxs-lookup"><span data-stu-id="b28c4-139">Axis 11 = 1.0 (no analog values)</span></span><br /><span data-ttu-id="b28c4-140">按鈕 4 <i> (遊戲台相容性) </i> </span><span class="sxs-lookup"><span data-stu-id="b28c4-140">Button 4 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="b28c4-141">軸 12 = 1.0 (沒有類比值) </span><span class="sxs-lookup"><span data-stu-id="b28c4-141">Axis 12 = 1.0 (no analog values)</span></span><br /><span data-ttu-id="b28c4-142">按鈕 5 <i> (遊戲台相容性) </i> </span><span class="sxs-lookup"><span data-stu-id="b28c4-142">Button 5 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="b28c4-143">抓住</span><span class="sxs-lookup"><span data-stu-id="b28c4-143">grasped</span></span></td>
</tr><tr>
<td> <span data-ttu-id="b28c4-144">操縱杆 X <i> (左：-1.0，右： 1.0) </i> </span><span class="sxs-lookup"><span data-stu-id="b28c4-144">Thumbstick X <i>(left: -1.0, right: 1.0)</i> </span></span></td><td> <span data-ttu-id="b28c4-145">軸1</span><span class="sxs-lookup"><span data-stu-id="b28c4-145">Axis 1</span></span> </td><td> <span data-ttu-id="b28c4-146">軸4</span><span class="sxs-lookup"><span data-stu-id="b28c4-146">Axis 4</span></span> </td><td> <span data-ttu-id="b28c4-147">thumbstickPosition. x</span><span class="sxs-lookup"><span data-stu-id="b28c4-147">thumbstickPosition.x</span></span></td>
</tr><tr>
<td> <span data-ttu-id="b28c4-148">操縱杆 Y <i> (top：-1.0，底端： 1.0) </i> </span><span class="sxs-lookup"><span data-stu-id="b28c4-148">Thumbstick Y <i>(top: -1.0, bottom: 1.0)</i> </span></span></td><td> <span data-ttu-id="b28c4-149">軸2</span><span class="sxs-lookup"><span data-stu-id="b28c4-149">Axis 2</span></span> </td><td> <span data-ttu-id="b28c4-150">軸5</span><span class="sxs-lookup"><span data-stu-id="b28c4-150">Axis 5</span></span> </td><td> <span data-ttu-id="b28c4-151">thumbstickPosition. y</span><span class="sxs-lookup"><span data-stu-id="b28c4-151">thumbstickPosition.y</span></span></td>
</tr><tr>
<td> <span data-ttu-id="b28c4-152">已按下操縱杆</span><span class="sxs-lookup"><span data-stu-id="b28c4-152">Thumbstick pressed</span></span> </td><td> <span data-ttu-id="b28c4-153">按鈕8</span><span class="sxs-lookup"><span data-stu-id="b28c4-153">Button 8</span></span> </td><td> <span data-ttu-id="b28c4-154">按鈕9</span><span class="sxs-lookup"><span data-stu-id="b28c4-154">Button 9</span></span> </td><td> <span data-ttu-id="b28c4-155">thumbstickPressed</span><span class="sxs-lookup"><span data-stu-id="b28c4-155">thumbstickPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="b28c4-156">觸控板 X <i> (左：-1.0、右邊： 1.0) </i> </span><span class="sxs-lookup"><span data-stu-id="b28c4-156">Touchpad X <i>(left: -1.0, right: 1.0)</i> </span></span></td><td> <span data-ttu-id="b28c4-157">軸 17 \*</span><span class="sxs-lookup"><span data-stu-id="b28c4-157">Axis 17\*</span></span> </td><td> <span data-ttu-id="b28c4-158">軸 19 \*</span><span class="sxs-lookup"><span data-stu-id="b28c4-158">Axis 19\*</span></span> </td><td> <span data-ttu-id="b28c4-159">touchpadPosition. x</span><span class="sxs-lookup"><span data-stu-id="b28c4-159">touchpadPosition.x</span></span></td>
</tr><tr>
<td> <span data-ttu-id="b28c4-160">觸控板 Y <i> (頂端：-1.0、底部： 1.0) </i> </span><span class="sxs-lookup"><span data-stu-id="b28c4-160">Touchpad Y <i>(top: -1.0, bottom: 1.0)</i> </span></span></td><td> <span data-ttu-id="b28c4-161">軸 18 \*</span><span class="sxs-lookup"><span data-stu-id="b28c4-161">Axis 18\*</span></span> </td><td> <span data-ttu-id="b28c4-162">軸 20 \*</span><span class="sxs-lookup"><span data-stu-id="b28c4-162">Axis 20\*</span></span> </td><td> <span data-ttu-id="b28c4-163">touchpadPosition. y</span><span class="sxs-lookup"><span data-stu-id="b28c4-163">touchpadPosition.y</span></span></td>
</tr><tr>
<td> <span data-ttu-id="b28c4-164">觸及觸控板</span><span class="sxs-lookup"><span data-stu-id="b28c4-164">Touchpad touched</span></span> </td><td> <span data-ttu-id="b28c4-165">按鈕 18 \*</span><span class="sxs-lookup"><span data-stu-id="b28c4-165">Button 18\*</span></span> </td><td> <span data-ttu-id="b28c4-166">按鈕 19 \*</span><span class="sxs-lookup"><span data-stu-id="b28c4-166">Button 19\*</span></span> </td><td> <span data-ttu-id="b28c4-167">touchpadTouched</span><span class="sxs-lookup"><span data-stu-id="b28c4-167">touchpadTouched</span></span></td>
</tr><tr>
<td> <span data-ttu-id="b28c4-168">已按下觸控板</span><span class="sxs-lookup"><span data-stu-id="b28c4-168">Touchpad pressed</span></span> </td><td> <span data-ttu-id="b28c4-169">按鈕 16 \*</span><span class="sxs-lookup"><span data-stu-id="b28c4-169">Button 16\*</span></span> </td><td> <span data-ttu-id="b28c4-170">按鈕 17 \*</span><span class="sxs-lookup"><span data-stu-id="b28c4-170">Button 17\*</span></span> </td><td> <span data-ttu-id="b28c4-171">touchpadPressed</span><span class="sxs-lookup"><span data-stu-id="b28c4-171">touchpadPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="b28c4-172">6DoF 抓住姿勢或指標姿勢</span><span class="sxs-lookup"><span data-stu-id="b28c4-172">6DoF grip pose or pointer pose</span></span> </td><td colspan="2"> <span data-ttu-id="b28c4-173">僅限<i>握</i>姿勢： <a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html">XR。InputTracking. GetLocalPosition</a></span><span class="sxs-lookup"><span data-stu-id="b28c4-173"><i>Grip</i> pose only: <a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html">XR.InputTracking.GetLocalPosition</a></span></span><br /><span data-ttu-id="b28c4-174"><a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalRotation.html">XR.InputTracking.GetLocalRotation</a></span><span class="sxs-lookup"><span data-stu-id="b28c4-174"><a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalRotation.html">XR.InputTracking.GetLocalRotation</a></span></span></td><td> <span data-ttu-id="b28c4-175">以引數 <i>形式傳遞底</i> 框或 <i>指標</i> ： SourceState. sourcePose. TryGetPosition</span><span class="sxs-lookup"><span data-stu-id="b28c4-175">Pass <i>Grip</i> or <i>Pointer</i> as an argument: sourceState.sourcePose.TryGetPosition</span></span><br /><span data-ttu-id="b28c4-176">sourceState.sourcePose.TryGetRotation</span><span class="sxs-lookup"><span data-stu-id="b28c4-176">sourceState.sourcePose.TryGetRotation</span></span><br /></td>
</tr><tr>
<td> <span data-ttu-id="b28c4-177">追蹤狀態</span><span class="sxs-lookup"><span data-stu-id="b28c4-177">Tracking state</span></span> </td><td colspan="2"> <span data-ttu-id="b28c4-178"><i>職位精確度和來源遺失風險僅可透過 MR 專屬 API 取得</i> </span><span class="sxs-lookup"><span data-stu-id="b28c4-178"><i>Position accuracy and source loss risk only available through MR-specific API</i> </span></span></td><td> <span data-ttu-id="b28c4-179"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourcePose-positionAccuracy.html">sourceState.sourcePose.positionAccuracy</a></span><span class="sxs-lookup"><span data-stu-id="b28c4-179"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourcePose-positionAccuracy.html">sourceState.sourcePose.positionAccuracy</a></span></span><br /><span data-ttu-id="b28c4-180"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourceProperties-sourceLossRisk.html">sourceState。 sourceLossRisk</a></span><span class="sxs-lookup"><span data-stu-id="b28c4-180"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourceProperties-sourceLossRisk.html">sourceState.properties.sourceLossRisk</a></span></span></td>
</tr>
</table>

>[!NOTE]
><span data-ttu-id="b28c4-181">這些按鈕/軸識別碼與 Unity 針對 OpenVR 所使用的識別碼不同，因為 gamepads、Oculus Touch 和 OpenVR 所使用的對應中發生衝突。</span><span class="sxs-lookup"><span data-stu-id="b28c4-181">These button/axis IDs differ from the IDs that Unity uses for OpenVR due to collisions in the mappings used by gamepads, Oculus Touch and OpenVR.</span></span>

### <a name="using-hp-reverb-g2-controllers"></a><span data-ttu-id="b28c4-182">使用 HP-UX 的 G2 控制器</span><span class="sxs-lookup"><span data-stu-id="b28c4-182">Using HP Reverb G2 controllers</span></span>

<span data-ttu-id="b28c4-183">如果您使用的是「HP 回音」 G2 控制器，請參閱下表中的按鈕和軸識別碼。</span><span class="sxs-lookup"><span data-stu-id="b28c4-183">If you're using the HP Reverb G2 controllers, refer to the table below for button and axis IDs.</span></span>

<table>
<tr>
<th rowspan="2"><span data-ttu-id="b28c4-184"><a href="https://docs.unity3d.com/ScriptReference/XR.CommonUsages.html">輸入</span><span class="sxs-lookup"><span data-stu-id="b28c4-184"><a href="https://docs.unity3d.com/ScriptReference/XR.CommonUsages.html">Input</span></span> </th><span data-ttu-id="b28c4-185"><th colspan="2">通用 Unity Api</span><span class="sxs-lookup"><span data-stu-id="b28c4-185"><th colspan="2">Common Unity APIs</span></span></a><br /><span data-ttu-id="b28c4-186"> (輸入. GetButton/GetAxis) </span><span class="sxs-lookup"><span data-stu-id="b28c4-186">(Input.GetButton/GetAxis)</span></span> </th><span data-ttu-id="b28c4-187"><th rowspan="2">HP 回音 G2 輸入 API</span><span class="sxs-lookup"><span data-stu-id="b28c4-187"><th rowspan="2">HP Reverb G2 Input API</span></span></a></th>
</tr><tr>
<th> <span data-ttu-id="b28c4-188">左手</span><span class="sxs-lookup"><span data-stu-id="b28c4-188">Left hand</span></span> </th><th> <span data-ttu-id="b28c4-189">右手</span><span class="sxs-lookup"><span data-stu-id="b28c4-189">Right hand</span></span></th>
</tr><tr>
<td> <span data-ttu-id="b28c4-190">Primary2DAxis</span><span class="sxs-lookup"><span data-stu-id="b28c4-190">Primary2DAxis</span></span> </td><td> <span data-ttu-id="b28c4-191">軸 1 (X) /軸 2 (Y) </span><span class="sxs-lookup"><span data-stu-id="b28c4-191">Axis 1 (X) / Axis 2 (Y)</span></span> </td><td> <span data-ttu-id="b28c4-192">軸 4 (X) /軸 5 (Y) </span><span class="sxs-lookup"><span data-stu-id="b28c4-192">Axis 4 (X) / Axis 5(Y)</span></span> </td><td> <span data-ttu-id="b28c4-193">操縱杆</span><span class="sxs-lookup"><span data-stu-id="b28c4-193">Thumbstick</span></span></td>
</tr><tr>
<td> <span data-ttu-id="b28c4-194">已按下觸發程式</span><span class="sxs-lookup"><span data-stu-id="b28c4-194">Trigger pressed</span></span> </td><td> <span data-ttu-id="b28c4-195">軸9</span><span class="sxs-lookup"><span data-stu-id="b28c4-195">Axis 9</span></span> </td><td> <span data-ttu-id="b28c4-196">軸10</span><span class="sxs-lookup"><span data-stu-id="b28c4-196">Axis 10</span></span> </td><td> <span data-ttu-id="b28c4-197">索引觸發程式</span><span class="sxs-lookup"><span data-stu-id="b28c4-197">Index trigger</span></span></td>
</tr><tr>
<td> <span data-ttu-id="b28c4-198">握</span><span class="sxs-lookup"><span data-stu-id="b28c4-198">Grip</span></span> </td><td> <span data-ttu-id="b28c4-199">軸11d</span><span class="sxs-lookup"><span data-stu-id="b28c4-199">Axis 11d</span></span> </td><td> <span data-ttu-id="b28c4-200">軸12</span><span class="sxs-lookup"><span data-stu-id="b28c4-200">Axis 12</span></span> </td><td> <span data-ttu-id="b28c4-201">握住觸發程式</span><span class="sxs-lookup"><span data-stu-id="b28c4-201">Grip trigger</span></span></td>
</tr><tr>
<td> <span data-ttu-id="b28c4-202">已按下 PrimaryButton</span><span class="sxs-lookup"><span data-stu-id="b28c4-202">PrimaryButton pressed</span></span> </td><td> <span data-ttu-id="b28c4-203">按鈕2</span><span class="sxs-lookup"><span data-stu-id="b28c4-203">Button 2</span></span> </td><td> <span data-ttu-id="b28c4-204">按鈕0</span><span class="sxs-lookup"><span data-stu-id="b28c4-204">Button 0</span></span> </td><td> <span data-ttu-id="b28c4-205">已按下功能表按鈕</span><span class="sxs-lookup"><span data-stu-id="b28c4-205">Menu button pressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="b28c4-206">已按下 SecondaryButton</span><span class="sxs-lookup"><span data-stu-id="b28c4-206">SecondaryButton pressed</span></span> </td><td> <span data-ttu-id="b28c4-207">按鈕3</span><span class="sxs-lookup"><span data-stu-id="b28c4-207">Button 3</span></span> </td><td> <span data-ttu-id="b28c4-208">按鈕1</span><span class="sxs-lookup"><span data-stu-id="b28c4-208">Button 1</span></span> </td><td> <span data-ttu-id="b28c4-209">A/X 按鈕</span><span class="sxs-lookup"><span data-stu-id="b28c4-209">A/X button</span></span></td>
</tr><tr>
<td> <span data-ttu-id="b28c4-210">GripButton</span><span class="sxs-lookup"><span data-stu-id="b28c4-210">GripButton</span></span> </td><td> <span data-ttu-id="b28c4-211">按鈕4</span><span class="sxs-lookup"><span data-stu-id="b28c4-211">Button 4</span></span> </td><td> <span data-ttu-id="b28c4-212">按鈕5</span><span class="sxs-lookup"><span data-stu-id="b28c4-212">Button 5</span></span> </td><td> <span data-ttu-id="b28c4-213">握住觸發程式</span><span class="sxs-lookup"><span data-stu-id="b28c4-213">Grip trigger</span></span></td>
</tr><tr>
<td> <span data-ttu-id="b28c4-214">TriggerButton</span><span class="sxs-lookup"><span data-stu-id="b28c4-214">TriggerButton</span></span> </td><td> <span data-ttu-id="b28c4-215">按鈕14</span><span class="sxs-lookup"><span data-stu-id="b28c4-215">Button 14</span></span> </td><td> <span data-ttu-id="b28c4-216">按鈕15</span><span class="sxs-lookup"><span data-stu-id="b28c4-216">Button 15</span></span> </td><td> <span data-ttu-id="b28c4-217">索引觸發程式</span><span class="sxs-lookup"><span data-stu-id="b28c4-217">Index trigger</span></span></td>
</tr><tr>
</tr>
</table>


## <a name="grip-pose-vs-pointing-pose"></a><span data-ttu-id="b28c4-218">底姿勢與指標姿勢</span><span class="sxs-lookup"><span data-stu-id="b28c4-218">Grip pose vs. pointing pose</span></span>

<span data-ttu-id="b28c4-219">Windows Mixed Reality 支援各種外型規格中的運動控制器，每個控制器的設計各有不同之處，就是使用者的位置與應用程式在轉譯控制器時應使用的自然「向前」方向之間的關聯性。</span><span class="sxs-lookup"><span data-stu-id="b28c4-219">Windows Mixed Reality supports motion controllers in a variety of form factors, with each controller's design differing in its relationship between the user's hand position and the natural "forward" direction that apps should use for pointing when rendering the controller.</span></span>

<span data-ttu-id="b28c4-220">為了更妥善地表示這些控制器，您可以針對每個互動來源（底框 **姿勢** 和 **指標姿勢** ）調查兩種類型的姿勢。</span><span class="sxs-lookup"><span data-stu-id="b28c4-220">To better represent these controllers, there are two kinds of poses you can investigate for each interaction source, the **grip pose** and the **pointer pose** .</span></span> <span data-ttu-id="b28c4-221">框姿勢和指標姿勢座標都是由全域 Unity 全局座標中的所有 Unity Api 表示。</span><span class="sxs-lookup"><span data-stu-id="b28c4-221">Both the grip pose and pointer pose coordinates are expressed by all Unity APIs in global Unity world coordinates.</span></span>

### <a name="grip-pose"></a><span data-ttu-id="b28c4-222">握住姿勢</span><span class="sxs-lookup"><span data-stu-id="b28c4-222">Grip pose</span></span>

<span data-ttu-id="b28c4-223">底框 **姿勢** 代表 HoloLens 所偵測到的掌上的位置，或是持有移動控制器的掌上。</span><span class="sxs-lookup"><span data-stu-id="b28c4-223">The **grip pose** represents the location of either the palm of a hand detected by a HoloLens, or the palm holding a motion controller.</span></span>

<span data-ttu-id="b28c4-224">在沉浸式耳機上，把手姿勢最適合用來 **呈現使用者手或\*\*\*\*使用者手中所持有的物件** ，例如寶劍或機槍。</span><span class="sxs-lookup"><span data-stu-id="b28c4-224">On immersive headsets, the grip pose is best used to render **the user's hand** or **an object held in the user's hand** , such as a sword or gun.</span></span> <span data-ttu-id="b28c4-225">視覺化運動控制器時也會使用底框姿勢，因為移動控制器的 Windows 所提供的 **呈現模型** 會使用底框姿勢作為其原點和旋轉中心。</span><span class="sxs-lookup"><span data-stu-id="b28c4-225">The grip pose is also used when visualizing a motion controller, as the **renderable model** provided by Windows for a motion controller uses the grip pose as its origin and center of rotation.</span></span>

<span data-ttu-id="b28c4-226">此底框姿勢的定義方式明確如下：</span><span class="sxs-lookup"><span data-stu-id="b28c4-226">The grip pose is defined specifically as follows:</span></span>
* <span data-ttu-id="b28c4-227">把手 **位置** ：自然地按住控制器時的棕櫚距心，向左或向右調整以將位置置中置中。</span><span class="sxs-lookup"><span data-stu-id="b28c4-227">The **grip position** : The palm centroid when holding the controller naturally, adjusted left or right to center the position within the grip.</span></span> <span data-ttu-id="b28c4-228">在 Windows Mixed Reality 運動控制器上，此位置通常會與 [抓住] 按鈕對齊。</span><span class="sxs-lookup"><span data-stu-id="b28c4-228">On the Windows Mixed Reality motion controller, this position generally aligns with the Grasp button.</span></span>
* <span data-ttu-id="b28c4-229">底 **圖方向的右軸** ：當您完全開啟手來形成平面的5形姿勢時，您的掌上光 (的光線會從左至右向前復原，從右邊的棕櫚) </span><span class="sxs-lookup"><span data-stu-id="b28c4-229">The **grip orientation's Right axis** : When you completely open your hand to form a flat 5-finger pose, the ray that is normal to your palm (forward from left palm, backward from right palm)</span></span>
* <span data-ttu-id="b28c4-230">底圖 **方向的向前軸** ：當您關閉手部分 (時，如同按住控制器) 一樣，也就是由非拇指手指所形成的電子管「轉寄」的光線。</span><span class="sxs-lookup"><span data-stu-id="b28c4-230">The **grip orientation's Forward axis** : When you close your hand partially (as if holding the controller), the ray that points "forward" through the tube formed by your non-thumb fingers.</span></span>
* <span data-ttu-id="b28c4-231">底圖 **方向的向上軸** ：右邊和向前定義所隱含的向上軸。</span><span class="sxs-lookup"><span data-stu-id="b28c4-231">The **grip orientation's Up axis** : The Up axis implied by the Right and Forward definitions.</span></span>

<span data-ttu-id="b28c4-232">您可以透過 Unity 的跨廠商輸入 API (XR 來存取抓住姿勢 *[。InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)。GetLocalPosition/輪替* ) 或透過 WINDOWS MR 專屬 API ( *SourceState. SourcePose. TryGetPosition/輪替* ，要求 **) 的** 的資料。</span><span class="sxs-lookup"><span data-stu-id="b28c4-232">You can access the grip pose through either Unity's cross-vendor input API ( *[XR.InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html).GetLocalPosition/Rotation* ) or through the Windows MR-specific API ( *sourceState.sourcePose.TryGetPosition/Rotation* , requesting pose data for the **Grip** node).</span></span>

### <a name="pointer-pose"></a><span data-ttu-id="b28c4-233">指標姿勢</span><span class="sxs-lookup"><span data-stu-id="b28c4-233">Pointer pose</span></span>

<span data-ttu-id="b28c4-234">**指標姿勢** 代表指向轉寄的控制器秘訣。</span><span class="sxs-lookup"><span data-stu-id="b28c4-234">The **pointer pose** represents the tip of the controller pointing forward.</span></span>

<span data-ttu-id="b28c4-235">系統提供的指標姿勢最適合用來在您 **呈現控制器模型本身** 時 raycast。</span><span class="sxs-lookup"><span data-stu-id="b28c4-235">The system-provided pointer pose is best used to raycast when you are **rendering the controller model itself** .</span></span> <span data-ttu-id="b28c4-236">如果您要轉譯某個其他的虛擬物件來取代控制器，例如虛擬的機槍，您應該指向該虛擬物件最自然的光線，例如沿著應用程式定義的機槍模型的圓柱移動光線。</span><span class="sxs-lookup"><span data-stu-id="b28c4-236">If you are rendering some other virtual object in place of the controller, such as a virtual gun, you should point with a ray that is most natural for that virtual object, such as a ray that travels along the barrel of the app-defined gun model.</span></span> <span data-ttu-id="b28c4-237">因為使用者可以看到虛擬物件，而不是實體控制器，所以指向虛擬物件可能會比使用您的應用程式更自然。</span><span class="sxs-lookup"><span data-stu-id="b28c4-237">Because users can see the virtual object and not the physical controller, pointing with the virtual object will likely be more natural for those using your app.</span></span>

<span data-ttu-id="b28c4-238">目前，只有透過 Windows MR 專屬 API （ *sourceState. sourcePose. TryGetPosition/旋轉* ）在 Unity 中提供指標姿勢，並傳入 *InteractionSourceNode* 作為引數。</span><span class="sxs-lookup"><span data-stu-id="b28c4-238">Currently, the pointer pose is available in Unity only through the Windows MR-specific API, *sourceState.sourcePose.TryGetPosition/Rotation* , passing in *InteractionSourceNode.Pointer* as the argument.</span></span>

## <a name="controller-tracking-state"></a><span data-ttu-id="b28c4-239">控制器追蹤狀態</span><span class="sxs-lookup"><span data-stu-id="b28c4-239">Controller tracking state</span></span>

<span data-ttu-id="b28c4-240">如同耳機，Windows Mixed Reality 運動控制器不需要設定外部追蹤感應器。</span><span class="sxs-lookup"><span data-stu-id="b28c4-240">Like the headsets, the Windows Mixed Reality motion controller requires no setup of external tracking sensors.</span></span> <span data-ttu-id="b28c4-241">相反地，控制器是由耳機本身的感應器追蹤。</span><span class="sxs-lookup"><span data-stu-id="b28c4-241">Instead, the controllers are tracked by sensors in the headset itself.</span></span>

<span data-ttu-id="b28c4-242">如果使用者將控制器移出耳機的觀賞欄位，在大部分情況下，Windows 會繼續推斷控制器位置，並將其提供給應用程式。</span><span class="sxs-lookup"><span data-stu-id="b28c4-242">If the user moves the controllers out of the headset's field of view, in most cases Windows will continue to infer controller positions and provide them to the app.</span></span> <span data-ttu-id="b28c4-243">如果控制器的長時間遺失視覺追蹤，控制器的位置將會降到大約精確度的位置。</span><span class="sxs-lookup"><span data-stu-id="b28c4-243">When the controller has lost visual tracking for long enough, the controller's positions will drop to approximate-accuracy positions.</span></span>

<span data-ttu-id="b28c4-244">此時，系統會將控制器主體鎖定給使用者，在移動時追蹤使用者的位置，同時仍會使用其內部方向感應器來公開控制器的真實方向。</span><span class="sxs-lookup"><span data-stu-id="b28c4-244">At this point, the system will body-lock the controller to the user, tracking the user's position as they move around, while still exposing the controller's true orientation using its internal orientation sensors.</span></span> <span data-ttu-id="b28c4-245">許多使用控制器來指向和啟動 UI 元素的應用程式，可以正常運作，而不會察覺到使用者注意。</span><span class="sxs-lookup"><span data-stu-id="b28c4-245">Many apps that use controllers to point at and activate UI elements can operate normally while in approximate accuracy without the user noticing.</span></span>

<span data-ttu-id="b28c4-246">若要瞭解這一點，最好的方法就是親自試試看。</span><span class="sxs-lookup"><span data-stu-id="b28c4-246">The best way to get a feel for this is to try it yourself.</span></span> <span data-ttu-id="b28c4-247">請觀看這段影片，其中包含可搭配各種追蹤狀態的運動控制器使用的沉浸式內容範例：</span><span class="sxs-lookup"><span data-stu-id="b28c4-247">Check out this video with examples of immersive content that works with motion controllers across various tracking states:</span></span>

<br>

 >[!VIDEO https://www.youtube.com/embed/QK_fOFDHj0g]

### <a name="reasoning-about-tracking-state-explicitly"></a><span data-ttu-id="b28c4-248">明確追蹤狀態的原因</span><span class="sxs-lookup"><span data-stu-id="b28c4-248">Reasoning about tracking state explicitly</span></span>

<span data-ttu-id="b28c4-249">希望根據追蹤狀態以不同方式來處理位置的應用程式，可能會進一步檢查控制器狀態的屬性，例如 *SourceLossRisk* 和 *PositionAccuracy* ：</span><span class="sxs-lookup"><span data-stu-id="b28c4-249">Apps that wish to treat positions differently based on tracking state may go further and inspect properties on the controller's state, such as *SourceLossRisk* and *PositionAccuracy* :</span></span>

<table>
<tr>
<th> <span data-ttu-id="b28c4-250">追蹤狀態</span><span class="sxs-lookup"><span data-stu-id="b28c4-250">Tracking state</span></span> </th><th> <span data-ttu-id="b28c4-251">SourceLossRisk</span><span class="sxs-lookup"><span data-stu-id="b28c4-251">SourceLossRisk</span></span> </th><th> <span data-ttu-id="b28c4-252">PositionAccuracy</span><span class="sxs-lookup"><span data-stu-id="b28c4-252">PositionAccuracy</span></span> </th><th> <span data-ttu-id="b28c4-253">TryGetPosition</span><span class="sxs-lookup"><span data-stu-id="b28c4-253">TryGetPosition</span></span></th>
</tr><tr>
<td> <span data-ttu-id="b28c4-254"><b>高精確度</b> </span><span class="sxs-lookup"><span data-stu-id="b28c4-254"><b>High accuracy</b> </span></span></td><td style="background-color: green; color: white"> <span data-ttu-id="b28c4-255">&lt; 1.0</span><span class="sxs-lookup"><span data-stu-id="b28c4-255">&lt; 1.0</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="b28c4-256">高</span><span class="sxs-lookup"><span data-stu-id="b28c4-256">High</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="b28c4-257">true</span><span class="sxs-lookup"><span data-stu-id="b28c4-257">true</span></span></td>
</tr><tr>
<td> <span data-ttu-id="b28c4-258"><b>高精確度 (有遺失) 的風險 </b> </span><span class="sxs-lookup"><span data-stu-id="b28c4-258"><b>High accuracy (at risk of losing)</b> </span></span></td><td style="background-color: orange"> <span data-ttu-id="b28c4-259">= = 1。0</span><span class="sxs-lookup"><span data-stu-id="b28c4-259">== 1.0</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="b28c4-260">高</span><span class="sxs-lookup"><span data-stu-id="b28c4-260">High</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="b28c4-261">true</span><span class="sxs-lookup"><span data-stu-id="b28c4-261">true</span></span></td>
</tr><tr>
<td> <span data-ttu-id="b28c4-262"><b>近似精確度</b> </span><span class="sxs-lookup"><span data-stu-id="b28c4-262"><b>Approximate accuracy</b> </span></span></td><td style="background-color: orange"> <span data-ttu-id="b28c4-263">= = 1。0</span><span class="sxs-lookup"><span data-stu-id="b28c4-263">== 1.0</span></span> </td><td style="background-color: orange"> <span data-ttu-id="b28c4-264">大約</span><span class="sxs-lookup"><span data-stu-id="b28c4-264">Approximate</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="b28c4-265">true</span><span class="sxs-lookup"><span data-stu-id="b28c4-265">true</span></span></td>
</tr><tr>
<td> <span data-ttu-id="b28c4-266"><b>沒有位置</b> </span><span class="sxs-lookup"><span data-stu-id="b28c4-266"><b>No position</b> </span></span></td><td style="background-color: orange"> <span data-ttu-id="b28c4-267">= = 1。0</span><span class="sxs-lookup"><span data-stu-id="b28c4-267">== 1.0</span></span> </td><td style="background-color: orange"> <span data-ttu-id="b28c4-268">大約</span><span class="sxs-lookup"><span data-stu-id="b28c4-268">Approximate</span></span> </td><td style="background-color: orange"> <span data-ttu-id="b28c4-269">false</span><span class="sxs-lookup"><span data-stu-id="b28c4-269">false</span></span></td>
</tr>
</table>

<span data-ttu-id="b28c4-270">這些移動控制器追蹤狀態的定義如下：</span><span class="sxs-lookup"><span data-stu-id="b28c4-270">These motion controller tracking states are defined as follows:</span></span>
* <span data-ttu-id="b28c4-271">**高精確度：** 當移動控制器位於耳機的視圖範圍內時，它通常會根據視覺效果追蹤，提供高精確度的位置。</span><span class="sxs-lookup"><span data-stu-id="b28c4-271">**High accuracy:** While the motion controller is within the headset's field of view, it will generally provide high-accuracy positions, based on visual tracking.</span></span> <span data-ttu-id="b28c4-272">請注意，移動控制器會暫時離開視圖的欄位，或是短暫地遮蔽到耳機感應器 (例如，根據使用者的角度，) 會根據控制器本身的慣性追蹤，繼續傳回高精確度的姿勢。</span><span class="sxs-lookup"><span data-stu-id="b28c4-272">Note that a moving controller that momentarily leaves the field of view or is momentarily obscured from the headset sensors (e.g. by the user's other hand) will continue to return high-accuracy poses for a short time, based on inertial tracking of the controller itself.</span></span>
* <span data-ttu-id="b28c4-273">**高精確度 (有遺失) 的風險：** 當使用者將移動控制站移出耳機視圖的邊緣之後，耳機很快就無法以視覺化方式追蹤控制器的位置。</span><span class="sxs-lookup"><span data-stu-id="b28c4-273">**High accuracy (at risk of losing):** When the user moves the motion controller past the edge of the headset's field of view, the headset will soon be unable to visually track the controller's position.</span></span> <span data-ttu-id="b28c4-274">應用程式知道當控制器達到此 FOV 界限時，會看到 **SourceLossRisk** 達到1.0。</span><span class="sxs-lookup"><span data-stu-id="b28c4-274">The app knows when the controller has reached this FOV boundary by seeing the **SourceLossRisk** reach 1.0.</span></span> <span data-ttu-id="b28c4-275">屆時，應用程式可能會選擇暫停需要穩定資料流程的控制器手勢，以提供高品質的物。</span><span class="sxs-lookup"><span data-stu-id="b28c4-275">At that point, the app may choose to pause controller gestures that require a steady stream of very high-quality poses.</span></span>
* <span data-ttu-id="b28c4-276">**近似精確度：** 如果控制器的長時間遺失視覺追蹤，控制器的位置將會降到大約精確度的位置。</span><span class="sxs-lookup"><span data-stu-id="b28c4-276">**Approximate accuracy:** When the controller has lost visual tracking for long enough, the controller's positions will drop to approximate-accuracy positions.</span></span> <span data-ttu-id="b28c4-277">此時，系統會將控制器主體鎖定給使用者，在移動時追蹤使用者的位置，同時仍會使用其內部方向感應器來公開控制器的真實方向。</span><span class="sxs-lookup"><span data-stu-id="b28c4-277">At this point, the system will body-lock the controller to the user, tracking the user's position as they move around, while still exposing the controller's true orientation using its internal orientation sensors.</span></span> <span data-ttu-id="b28c4-278">許多使用控制器來指向和啟動 UI 元素的應用程式，都可以正常運作，而不會察覺到使用者的精確度。</span><span class="sxs-lookup"><span data-stu-id="b28c4-278">Many apps that use controllers to point at and activate UI elements can operate as normal while in approximate accuracy without the user noticing.</span></span> <span data-ttu-id="b28c4-279">具有較長輸入需求的應用程式可能會藉由檢查 **PositionAccuracy** 屬性，選擇將此下降從 **高** 精確度到 **近似** 精確度，例如，讓使用者在這段時間內更有更多的螢幕目標 hitbox。</span><span class="sxs-lookup"><span data-stu-id="b28c4-279">Apps with heavier input requirements may choose to sense this drop from **High** accuracy to **Approximate** accuracy by inspecting the **PositionAccuracy** property, for example to give the user a more generous hitbox on off-screen targets during this time.</span></span>
* <span data-ttu-id="b28c4-280">**沒有位置：** 雖然控制器可在很長的時間內正常運作，但有時系統會知道即使主體鎖定的位置在當時都沒有意義。</span><span class="sxs-lookup"><span data-stu-id="b28c4-280">**No position:** While the controller can operate at approximate accuracy for a long time, sometimes the system knows that even a body-locked position is not meaningful at the moment.</span></span> <span data-ttu-id="b28c4-281">例如，剛開啟的控制器可能未曾以視覺化的方式觀察到，或者使用者可能會放置由其他人挑選的控制器。</span><span class="sxs-lookup"><span data-stu-id="b28c4-281">For example, a controller that was just turned on may have never been observed visually, or a user may put down a controller that's then picked up by someone else.</span></span> <span data-ttu-id="b28c4-282">在這些時間，系統不會提供應用程式的任何位置，且 *TryGetPosition* 會傳回 false。</span><span class="sxs-lookup"><span data-stu-id="b28c4-282">At those times, the system will not provide any position to the app, and *TryGetPosition* will return false.</span></span>

## <a name="common-unity-apis-inputgetbuttongetaxis"></a><span data-ttu-id="b28c4-283">通用 Unity Api (輸入 GetButton/GetAxis) </span><span class="sxs-lookup"><span data-stu-id="b28c4-283">Common Unity APIs (Input.GetButton/GetAxis)</span></span>

<span data-ttu-id="b28c4-284">**Namespace：** *UnityEngine* ， *UnityEngine. XR*</span><span class="sxs-lookup"><span data-stu-id="b28c4-284">**Namespace:** *UnityEngine* , *UnityEngine.XR*</span></span><br>
<span data-ttu-id="b28c4-285">**類型** ： *輸入* 、 *XR。InputTracking*</span><span class="sxs-lookup"><span data-stu-id="b28c4-285">**Types** : *Input* , *XR.InputTracking*</span></span>

<span data-ttu-id="b28c4-286">Unity 目前使用其一般 *輸入. GetButton/GetAxis* api 來公開 [Oculus SDK](https://docs.unity3d.com/Manual/OculusControllers.html)、 [OpenVR SDK](https://docs.unity3d.com/Manual/OpenVRControllers.html) 和 Windows Mixed Reality 的輸入，包括實習和移動控制器。</span><span class="sxs-lookup"><span data-stu-id="b28c4-286">Unity currently uses its general *Input.GetButton/Input.GetAxis* APIs to expose input for [the Oculus SDK](https://docs.unity3d.com/Manual/OculusControllers.html), [the OpenVR SDK](https://docs.unity3d.com/Manual/OpenVRControllers.html) and Windows Mixed Reality, including hands and motion controllers.</span></span> <span data-ttu-id="b28c4-287">如果您的應用程式使用這些 Api 進行輸入，則可以輕鬆地支援跨多個 XR Sdk 的移動控制器，包括 Windows Mixed Reality。</span><span class="sxs-lookup"><span data-stu-id="b28c4-287">If your app uses these APIs for input, it can easily support motion controllers across multiple XR SDKs, including Windows Mixed Reality.</span></span>

### <a name="getting-a-logical-buttons-pressed-state"></a><span data-ttu-id="b28c4-288">取得邏輯按鈕的按下狀態</span><span class="sxs-lookup"><span data-stu-id="b28c4-288">Getting a logical button's pressed state</span></span>

<span data-ttu-id="b28c4-289">若要使用一般 Unity 輸入 Api，您通常會先將按鈕和軸連結到 [Unity 輸入管理員](https://docs.unity3d.com/Manual/ConventionalGameInput.html)中的邏輯名稱，然後將按鈕或軸識別碼系結至每個名稱。</span><span class="sxs-lookup"><span data-stu-id="b28c4-289">To use the general Unity input APIs, you'll typically start by wiring up buttons and axes to logical names in the [Unity Input Manager](https://docs.unity3d.com/Manual/ConventionalGameInput.html), binding a button or axis IDs to each name.</span></span> <span data-ttu-id="b28c4-290">然後，您可以撰寫參考該邏輯按鈕/軸名稱的程式碼。</span><span class="sxs-lookup"><span data-stu-id="b28c4-290">You can then write code that refers to that logical button/axis name.</span></span>

<span data-ttu-id="b28c4-291">例如，若要將左移動控制器的 [觸發程式] 按鈕對應至 [提交] 動作，請移至 Unity 內的 [ **編輯 > 專案設定] > 輸入** ，並展開 [軸] 下的 [提交] 區段的屬性。</span><span class="sxs-lookup"><span data-stu-id="b28c4-291">For example, to map the left motion controller's trigger button to the Submit action, go to **Edit > Project Settings > Input** within Unity, and expand the properties of the Submit section under Axes.</span></span> <span data-ttu-id="b28c4-292">將 **正面按鈕** 或 **Alt 正按鈕** 屬性變更為讀取 **搖桿按鈕 14** ，如下所示：</span><span class="sxs-lookup"><span data-stu-id="b28c4-292">Change the **Positive Button** or **Alt Positive Button** property to read **joystick button 14** , like this:</span></span>

<span data-ttu-id="b28c4-293">![Unity 的 InputManager](images/unity-input-manager.png)</span><span class="sxs-lookup"><span data-stu-id="b28c4-293">![Unity's InputManager](images/unity-input-manager.png)</span></span><br>
<span data-ttu-id="b28c4-294">*Unity InputManager*</span><span class="sxs-lookup"><span data-stu-id="b28c4-294">*Unity InputManager*</span></span>

<span data-ttu-id="b28c4-295">然後，您的腳本可以使用 *GetButton* 來檢查提交動作：</span><span class="sxs-lookup"><span data-stu-id="b28c4-295">Your script can then check for the Submit action using *Input.GetButton* :</span></span>

```cs
if (Input.GetButton("Submit"))
{
  // ...
}
```
<span data-ttu-id="b28c4-296">您可以變更 [ **軸** ] 下的 [ **大小** ] 屬性，以新增更多邏輯按鈕。</span><span class="sxs-lookup"><span data-stu-id="b28c4-296">You can add more logical buttons by changing the **Size** property under **Axes** .</span></span>

### <a name="getting-a-physical-buttons-pressed-state-directly"></a><span data-ttu-id="b28c4-297">直接取得實體按鈕的按下狀態</span><span class="sxs-lookup"><span data-stu-id="b28c4-297">Getting a physical button's pressed state directly</span></span>

<span data-ttu-id="b28c4-298">您也可以使用 *GetKey* 的完整名稱，以手動方式存取按鈕：</span><span class="sxs-lookup"><span data-stu-id="b28c4-298">You can also access buttons manually by their fully-qualified name, using *Input.GetKey* :</span></span>

```cs
if (Input.GetKey("joystick button 8"))
{
  // ...
}
```

### <a name="getting-a-hand-or-motion-controllers-pose"></a><span data-ttu-id="b28c4-299">取得手或移動控制器的姿勢</span><span class="sxs-lookup"><span data-stu-id="b28c4-299">Getting a hand or motion controller's pose</span></span>

<span data-ttu-id="b28c4-300">您可以使用 XR 存取控制器的位置和旋轉 *。InputTracking* ：</span><span class="sxs-lookup"><span data-stu-id="b28c4-300">You can access the position and rotation of the controller, using *XR.InputTracking* :</span></span>

```cs
Vector3 leftPosition = InputTracking.GetLocalPosition(XRNode.LeftHand);
Quaternion leftRotation = InputTracking.GetLocalRotation(XRNode.LeftHand);
```

<span data-ttu-id="b28c4-301">請注意，這代表控制器的底狀姿勢 (其中的使用者持有控制器) ，這對於在使用者手中轉譯寶劍或機槍，或控制器本身的模型很有用。</span><span class="sxs-lookup"><span data-stu-id="b28c4-301">Note that this represents the controller's grip pose (where the user holds the controller), which is useful for rendering a sword or gun in the user's hand, or a model of the controller itself.</span></span>

<span data-ttu-id="b28c4-302">請注意，此底框之間的關聯性會造成，且指標會造成 (，控制器的提示會指向控制器的) 可能不同。</span><span class="sxs-lookup"><span data-stu-id="b28c4-302">Note that the relationship between this grip pose and the pointer pose (where the tip of the controller is pointing) may differ across controllers.</span></span> <span data-ttu-id="b28c4-303">目前，只能透過 MR 專屬的輸入 API 來存取控制器的指標姿勢，如下一節所述。</span><span class="sxs-lookup"><span data-stu-id="b28c4-303">At this moment, accessing the controller's pointer pose is only possible through the MR-specific input API, described in the sections below.</span></span>

## <a name="windows-specific-apis-xrwsainput"></a><span data-ttu-id="b28c4-304">Windows 特定 Api (XR。Wsa。輸入) </span><span class="sxs-lookup"><span data-stu-id="b28c4-304">Windows-specific APIs (XR.WSA.Input)</span></span>

<span data-ttu-id="b28c4-305">**命名空間：** *UnityEngine. XR。輸入*</span><span class="sxs-lookup"><span data-stu-id="b28c4-305">**Namespace:** *UnityEngine.XR.WSA.Input*</span></span><br>
<span data-ttu-id="b28c4-306">**類型** ： *InteractionManager* 、 *InteractionSourceState* 、 *InteractionSource* 、 *InteractionSourceProperties* 、 *InteractionSourceKind* 、 *InteractionSourceLocation*</span><span class="sxs-lookup"><span data-stu-id="b28c4-306">**Types** : *InteractionManager* , *InteractionSourceState* , *InteractionSource* , *InteractionSourceProperties* , *InteractionSourceKind* , *InteractionSourceLocation*</span></span>

<span data-ttu-id="b28c4-307">若要取得 HoloLens) 和移動控制器的 Windows Mixed Reality 手輸入 (的詳細資訊，您可以選擇使用 *UnityEngine. XR* 底下的 Windows 特定空間輸入 api。</span><span class="sxs-lookup"><span data-stu-id="b28c4-307">To get at more detailed information about Windows Mixed Reality hand input (for HoloLens) and motion controllers, you can choose to use the Windows-specific spatial input APIs under the *UnityEngine.XR.WSA.Input* namespace.</span></span> <span data-ttu-id="b28c4-308">這可讓您存取額外的資訊，例如位置精確度或來源種類，讓您可以分辨手和控制器。</span><span class="sxs-lookup"><span data-stu-id="b28c4-308">This lets you access additional information, such as position accuracy or the source kind, letting you tell hands and controllers apart.</span></span>

### <a name="polling-for-the-state-of-hands-and-motion-controllers"></a><span data-ttu-id="b28c4-309">輪詢實習和移動控制器的狀態</span><span class="sxs-lookup"><span data-stu-id="b28c4-309">Polling for the state of hands and motion controllers</span></span>

<span data-ttu-id="b28c4-310">您可以使用 *GetCurrentReading* 方法，輪詢每個互動來源 (手或移動控制器) 的此畫面格狀態。</span><span class="sxs-lookup"><span data-stu-id="b28c4-310">You can poll for this frame's state for each interaction source (hand or motion controller) using the *GetCurrentReading* method.</span></span>

```cs
var interactionSourceStates = InteractionManager.GetCurrentReading();
foreach (var interactionSourceState in interactionSourceStates) {
    // ...
}
```

<span data-ttu-id="b28c4-311">您取回的每個 *InteractionSourceState* 都代表目前時間的互動來源。</span><span class="sxs-lookup"><span data-stu-id="b28c4-311">Each *InteractionSourceState* you get back represents an interaction source at the current moment in time.</span></span> <span data-ttu-id="b28c4-312">*InteractionSourceState* 會公開如下的資訊：</span><span class="sxs-lookup"><span data-stu-id="b28c4-312">The *InteractionSourceState* exposes info such as:</span></span>
* <span data-ttu-id="b28c4-313"> (選取/功能表/抓住/觸控板/操縱杆) 會發生何[種類型的按鍵](../../design/motion-controllers.md)</span><span class="sxs-lookup"><span data-stu-id="b28c4-313">Which [kinds of presses](../../design/motion-controllers.md) are occurring (Select/Menu/Grasp/Touchpad/Thumbstick)</span></span>

   ```cs
   if (interactionSourceState.selectPressed) {
       // ...
   }
   ```
* <span data-ttu-id="b28c4-314">動作控制器特定的其他資料，例如觸控板和/或操縱杆的 XY 座標和觸及的狀態</span><span class="sxs-lookup"><span data-stu-id="b28c4-314">Other data specific to motion controllers, such the touchpad and/or thumbstick's XY coordinates and touched state</span></span>

   ```cs
   if (interactionSourceState.touchpadTouched && interactionSourceState.touchpadPosition.x > 0.5) {
       // ...
   }
   ```

* <span data-ttu-id="b28c4-315">InteractionSourceKind，以瞭解來源是手或移動控制器</span><span class="sxs-lookup"><span data-stu-id="b28c4-315">The InteractionSourceKind to know if the source is a hand or a motion controller</span></span>

   ```cs
   if (interactionSourceState.source.kind == InteractionSourceKind.Hand) {
       // ...
   }
   ```

### <a name="polling-for-forward-predicted-rendering-poses"></a><span data-ttu-id="b28c4-316">輪詢向前預測呈現的姿勢</span><span class="sxs-lookup"><span data-stu-id="b28c4-316">Polling for forward-predicted rendering poses</span></span>

* <span data-ttu-id="b28c4-317">當您輪詢來自手和控制器的互動來源資料時，您所得到的是向前預測的原因，是在此框架的光子到達使用者眼時的時間點。</span><span class="sxs-lookup"><span data-stu-id="b28c4-317">When polling for interaction source data from hands and controllers, the poses you get are forward-predicted poses for the moment in time when this frame's photons will reach the user's eyes.</span></span>  <span data-ttu-id="b28c4-318">這些向前預測的姿勢最適合 **用來轉譯** 控制器或每個畫面格的保留物件。</span><span class="sxs-lookup"><span data-stu-id="b28c4-318">These forward-predicted poses are best used for **rendering** the controller or a held object each frame.</span></span>  <span data-ttu-id="b28c4-319">如果您的目標是使用控制器指定的按下或放開，如果您使用如下所述的歷程記錄事件 Api，這將會是最精確的。</span><span class="sxs-lookup"><span data-stu-id="b28c4-319">If you are targeting a given press or release with the controller, that will be most accurate if you use the historical event APIs described below.</span></span>

   ```cs
   var sourcePose = interactionSourceState.sourcePose;
   Vector3 sourceGripPosition;
   Quaternion sourceGripRotation;
   if ((sourcePose.TryGetPosition(out sourceGripPosition, InteractionSourceNode.Grip)) &&
       (sourcePose.TryGetRotation(out sourceGripRotation, InteractionSourceNode.Grip))) {
       // ...
   }
   ```

* <span data-ttu-id="b28c4-320">您也可以取得這個目前畫面格的向前預測標頭姿勢。</span><span class="sxs-lookup"><span data-stu-id="b28c4-320">You can also get the forward-predicted head pose for this current frame.</span></span>  <span data-ttu-id="b28c4-321">如同來源的原因，如果您使用如下所 **述的歷程** 記錄事件 api，則在轉譯資料指標時，這會很有用。</span><span class="sxs-lookup"><span data-stu-id="b28c4-321">As with the source pose, this is useful for **rendering** a cursor, although targeting a given press or release will be most accurate if you use the historical event APIs described below.</span></span>

   ```cs
   var headPose = interactionSourceState.headPose;
   var headRay = new Ray(headPose.position, headPose.forward);
   RaycastHit raycastHit;
   if (Physics.Raycast(headPose.position, headPose.forward, out raycastHit, 10)) {
       var cursorPos = raycastHit.point;
       // ...
   }
   ```

### <a name="handling-interaction-source-events"></a><span data-ttu-id="b28c4-322">處理互動來源事件</span><span class="sxs-lookup"><span data-stu-id="b28c4-322">Handling interaction source events</span></span>

<span data-ttu-id="b28c4-323">若要在輸入事件發生時處理其正確的歷程記錄資料，您可以處理互動來源事件，而不是輪詢。</span><span class="sxs-lookup"><span data-stu-id="b28c4-323">To handle input events as they happen with their accurate historical pose data, you can handle interaction source events instead of polling.</span></span>

<span data-ttu-id="b28c4-324">若要處理互動來源事件：</span><span class="sxs-lookup"><span data-stu-id="b28c4-324">To handle interaction source events:</span></span>
* <span data-ttu-id="b28c4-325">註冊 *InteractionManager* 輸入事件。</span><span class="sxs-lookup"><span data-stu-id="b28c4-325">Register for a *InteractionManager* input event.</span></span> <span data-ttu-id="b28c4-326">針對每個您感興趣的互動事件種類，您必須訂閱該事件。</span><span class="sxs-lookup"><span data-stu-id="b28c4-326">For each type of interaction event that you are interested in, you need to subscribe to it.</span></span>

   ```cs
   InteractionManager.InteractionSourcePressed += InteractionManager_InteractionSourcePressed;
   ```

* <span data-ttu-id="b28c4-327">處理事件。</span><span class="sxs-lookup"><span data-stu-id="b28c4-327">Handle the event.</span></span> <span data-ttu-id="b28c4-328">當您訂閱了互動事件之後，就會在適當的情況下取得回呼。</span><span class="sxs-lookup"><span data-stu-id="b28c4-328">Once you have subscribed to an interaction event, you will get the callback when appropriate.</span></span> <span data-ttu-id="b28c4-329">在 *SourcePressed* 範例中，這會在偵測到來源之後，且在釋放或遺失之前。</span><span class="sxs-lookup"><span data-stu-id="b28c4-329">In the *SourcePressed* example, this will be after the source was detected and before it is released or lost.</span></span>

   ```cs
   void InteractionManager_InteractionSourceDetected(InteractionSourceDetectedEventArgs args)
       var interactionSourceState = args.state;

       // args.state has information about:
          // targeting head ray at the time when the event was triggered
          // whether the source is pressed or not
          // properties like position, velocity, source loss risk
          // source id (which hand id for example) and source kind like hand, voice, controller or other
   }
   ```

### <a name="how-to-stop-handling-an-event"></a><span data-ttu-id="b28c4-330">如何停止處理事件</span><span class="sxs-lookup"><span data-stu-id="b28c4-330">How to stop handling an event</span></span>

<span data-ttu-id="b28c4-331">當您不再想要處理事件，或終結已訂閱事件的物件時，您需要停止處理事件。</span><span class="sxs-lookup"><span data-stu-id="b28c4-331">You need to stop handling an event when you are no longer interested in the event or you are destroying the object that has subscribed to the event.</span></span> <span data-ttu-id="b28c4-332">若要停止處理事件，您可以取消訂閱事件。</span><span class="sxs-lookup"><span data-stu-id="b28c4-332">To stop handling the event, you unsubscribe from the event.</span></span>

```cs
InteractionManager.InteractionSourcePressed -= InteractionManager_InteractionSourcePressed;
```

### <a name="list-of-interaction-source-events"></a><span data-ttu-id="b28c4-333">互動來源事件的清單</span><span class="sxs-lookup"><span data-stu-id="b28c4-333">List of interaction source events</span></span>

<span data-ttu-id="b28c4-334">可用的互動來源事件如下：</span><span class="sxs-lookup"><span data-stu-id="b28c4-334">The available interaction source events are:</span></span>
* <span data-ttu-id="b28c4-335">*InteractionSourceDetected* (來源會變成作用中) </span><span class="sxs-lookup"><span data-stu-id="b28c4-335">*InteractionSourceDetected* (source becomes active)</span></span>
* <span data-ttu-id="b28c4-336">*InteractionSourceLost* (變成非使用中) </span><span class="sxs-lookup"><span data-stu-id="b28c4-336">*InteractionSourceLost* (becomes inactive)</span></span>
* <span data-ttu-id="b28c4-337">*InteractionSourcePressed* (點擊、按下按鈕或「選取」從未提到) </span><span class="sxs-lookup"><span data-stu-id="b28c4-337">*InteractionSourcePressed* (tap, button press, or "Select" uttered)</span></span>
* <span data-ttu-id="b28c4-338">*InteractionSourceReleased* (結束、放開按鈕或 "Select" 從未提到結尾) </span><span class="sxs-lookup"><span data-stu-id="b28c4-338">*InteractionSourceReleased* (end of a tap, button released, or end of "Select" uttered)</span></span>
* <span data-ttu-id="b28c4-339">*InteractionSourceUpdated* (會移動或以其他方式變更某些狀態) </span><span class="sxs-lookup"><span data-stu-id="b28c4-339">*InteractionSourceUpdated* (moves or otherwise changes some state)</span></span>

### <a name="events-for-historical-targeting-poses-that-most-accurately-match-a-press-or-release"></a><span data-ttu-id="b28c4-340">歷程記錄目標的事件，最精確地符合電子報或發行</span><span class="sxs-lookup"><span data-stu-id="b28c4-340">Events for historical targeting poses that most accurately match a press or release</span></span>

<span data-ttu-id="b28c4-341">稍早所述的輪詢 Api 會讓您的應用程式向前預測的姿勢。</span><span class="sxs-lookup"><span data-stu-id="b28c4-341">The polling APIs described earlier give your app forward-predicted poses.</span></span>  <span data-ttu-id="b28c4-342">雖然這些預測的姿勢最適合用來呈現控制器或虛擬掌上型物件，但未來的原因並不適合作為目標，原因有兩個：</span><span class="sxs-lookup"><span data-stu-id="b28c4-342">While those predicted poses are best for rendering the controller or a virtual handheld object, future poses are not optimal for targeting, for two key reasons:</span></span>
* <span data-ttu-id="b28c4-343">當使用者按下控制器上的按鈕時，可能會有關于在系統收到按下之前，透過藍牙20毫秒無線延遲的情況。</span><span class="sxs-lookup"><span data-stu-id="b28c4-343">When the user presses a button on a controller, there can be about 20ms of wireless latency over Bluetooth before the system receives the press.</span></span>
* <span data-ttu-id="b28c4-344">然後，如果您使用向前預測的姿勢，則會有另一個 10 20 毫秒的向前預測套用到目標，也就是目前框架的光子到達使用者眼睛的時間。</span><span class="sxs-lookup"><span data-stu-id="b28c4-344">Then, if you are using a forward-predicted pose, there would be another 10-20ms of forward prediction applied to target the time when the current frame's photons will reach the user's eyes.</span></span>

<span data-ttu-id="b28c4-345">這表示輪詢會提供您一個來源姿勢或 head 的原因，也就是從使用者的標頭開始，並在發生按下或放開時實際返回的40毫秒。</span><span class="sxs-lookup"><span data-stu-id="b28c4-345">This means that polling gives you a source pose or head pose that is 30-40ms forward from where the user's head and hands actually were back when the press or release happened.</span></span>  <span data-ttu-id="b28c4-346">針對 HoloLens 手輸入，雖然沒有無線傳輸延遲，但偵測到按下的處理延遲也很類似。</span><span class="sxs-lookup"><span data-stu-id="b28c4-346">For HoloLens hand input, while there's no wireless transmission delay, there is a similar processing delay to detect the press.</span></span>

<span data-ttu-id="b28c4-347">若要根據使用者的原始意圖來精確地鎖定目標，請按下該 *InteractionSourcePressed* 或 *InteractionSourceReleased* 輸入事件的歷程記錄來源姿勢或 head 姿勢。</span><span class="sxs-lookup"><span data-stu-id="b28c4-347">To accurately target based on the user's original intent for a hand or controller press, you should use the historical source pose or head pose from that *InteractionSourcePressed* or *InteractionSourceReleased* input event.</span></span>

<span data-ttu-id="b28c4-348">您可以使用來自使用者前端或其控制器的歷程記錄資料，來進行按下或釋放的目標：</span><span class="sxs-lookup"><span data-stu-id="b28c4-348">You can target a press or release with historical pose data from the user's head or their controller:</span></span>
* <span data-ttu-id="b28c4-349">當軌跡或控制器按下的時間點時，可能會用來做為 **目標** ，以判斷使用者的 [撥雲見日](../../design/gaze-and-commit.md) ：</span><span class="sxs-lookup"><span data-stu-id="b28c4-349">The head pose at the moment in time when a gesture or controller press occurred, which can be used for **targeting** to determine what the user was [gazing](../../design/gaze-and-commit.md) at:</span></span>

   ```cs
   void InteractionManager_InteractionSourcePressed(InteractionSourcePressedEventArgs args) {
       var interactionSourceState = args.state;
       var headPose = interactionSourceState.headPose;
       RaycastHit raycastHit;
       if (Physics.Raycast(headPose.position, headPose.forward, out raycastHit, 10)) {
           var targetObject = raycastHit.collider.gameObject;
           // ...
       }
   }
   ```

* <span data-ttu-id="b28c4-350">來源會在移動控制器按下的時間點發生，這可用於 **目標** ，以判斷使用者在何處指向控制器。</span><span class="sxs-lookup"><span data-stu-id="b28c4-350">The source pose at the moment in time when a motion controller press occurred, which can be used for **targeting** to determine what the user was pointing the controller at.</span></span>  <span data-ttu-id="b28c4-351">這會是遇到按下之控制器的狀態。</span><span class="sxs-lookup"><span data-stu-id="b28c4-351">This will be the state of the controller that experienced the press.</span></span>  <span data-ttu-id="b28c4-352">如果您要轉譯控制器本身，您可以要求指標姿勢，而不是把手姿勢，以將目標光線從使用者考慮到該轉譯控制器的自然秘訣：</span><span class="sxs-lookup"><span data-stu-id="b28c4-352">If you are rendering the controller itself, you can request the pointer pose rather than the grip pose, to shoot the targeting ray from what the user will consider the natural tip of that rendered controller:</span></span>

   ```cs
   void InteractionManager_InteractionSourcePressed(InteractionSourcePressedEventArgs args)
   {
       var interactionSourceState = args.state;
       var sourcePose = interactionSourceState.sourcePose;
       Vector3 sourceGripPosition;
       Quaternion sourceGripRotation;
       if ((sourcePose.TryGetPosition(out sourceGripPosition, InteractionSourceNode.Pointer)) &&
           (sourcePose.TryGetRotation(out sourceGripRotation, InteractionSourceNode.Pointer))) {
           RaycastHit raycastHit;
           if (Physics.Raycast(sourceGripPosition, sourceGripRotation * Vector3.forward, out raycastHit, 10)) {
               var targetObject = raycastHit.collider.gameObject;
               // ...
           }
       }
   }
   ```

### <a name="event-handlers-example"></a><span data-ttu-id="b28c4-353">事件處理常式範例</span><span class="sxs-lookup"><span data-stu-id="b28c4-353">Event handlers example</span></span>

```cs
using UnityEngine.XR.WSA.Input;

void Start()
{
    InteractionManager.InteractionSourceDetected += InteractionManager_InteractionSourceDetected;
    InteractionManager.InteractionSourceLost += InteractionManager_InteractionSourceLost;
    InteractionManager.InteractionSourcePressed += InteractionManager_InteractionSourcePressed;
    InteractionManager.InteractionSourceReleased += InteractionManager_InteractionSourceReleased;
    InteractionManager.InteractionSourceUpdated += InteractionManager_InteractionSourceUpdated;
}

void OnDestroy()
{
    InteractionManager.InteractionSourceDetected -= InteractionManager_InteractionSourceDetected;
    InteractionManager.InteractionSourceLost -= InteractionManager_InteractionSourceLost;
    InteractionManager.InteractionSourcePressed -= InteractionManager_InteractionSourcePressed;
    InteractionManager.InteractionSourceReleased -= InteractionManager_InteractionSourceReleased;
    InteractionManager.InteractionSourceUpdated -= InteractionManager_InteractionSourceUpdated;
}

void InteractionManager_InteractionSourceDetected(InteractionSourceDetectedEventArgs args)
{
    // Source was detected
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourceLost(InteractionSourceLostEventArgs state)
{
    // Source was lost. This will be after a SourceDetected event and no other events for this
    // source id will occur until it is Detected again
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourcePressed(InteractionSourcePressedEventArgs state)
{
    // Source was pressed. This will be after the source was detected and before it is
    // released or lost
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourceReleased(InteractionSourceReleasedEventArgs state)
{
    // Source was released. The source would have been detected and pressed before this point.
    // This event will not fire if the source is lost
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourceUpdated(InteractionSourceUpdatedEventArgs state)
{
    // Source was updated. The source would have been detected before this point
    // args.state has the current state of the source including id, position, kind, etc.
}
```

## <a name="high-level-composite-gesture-apis-gesturerecognizer"></a><span data-ttu-id="b28c4-354">高層級複合手勢 Api (GestureRecognizer) </span><span class="sxs-lookup"><span data-stu-id="b28c4-354">High-level composite gesture APIs (GestureRecognizer)</span></span>

<span data-ttu-id="b28c4-355">**命名空間：** *UnityEngine. XR。輸入*</span><span class="sxs-lookup"><span data-stu-id="b28c4-355">**Namespace:** *UnityEngine.XR.WSA.Input*</span></span><br>
<span data-ttu-id="b28c4-356">**類型** ： *GestureRecognizer* 、 *GestureSettings* 、 *InteractionSourceKind*</span><span class="sxs-lookup"><span data-stu-id="b28c4-356">**Types** : *GestureRecognizer* , *GestureSettings* , *InteractionSourceKind*</span></span>

<span data-ttu-id="b28c4-357">您的應用程式也可以辨識空間輸入來源、點擊、按住、操作和導覽手勢的較高層級複合手勢。</span><span class="sxs-lookup"><span data-stu-id="b28c4-357">Your app can also recognize higher-level composite gestures for spatial input sources, Tap, Hold, Manipulation and Navigation gestures.</span></span> <span data-ttu-id="b28c4-358">您可以使用 GestureRecognizer，跨 [手](../../design/gaze-and-commit.md#composite-gestures) 和 [移動控制器](../../design/motion-controllers.md) 辨識這些複合手勢。</span><span class="sxs-lookup"><span data-stu-id="b28c4-358">You can recognize these composite gestures across both [hands](../../design/gaze-and-commit.md#composite-gestures) and [motion controllers](../../design/motion-controllers.md) using the GestureRecognizer.</span></span>

<span data-ttu-id="b28c4-359">GestureRecognizer 上的每個手勢事件都會提供輸入的 SourceKind，以及事件時的目標 head 光線。</span><span class="sxs-lookup"><span data-stu-id="b28c4-359">Each Gesture event on the GestureRecognizer provides the SourceKind for the input as well as the targeting head ray at the time of the event.</span></span> <span data-ttu-id="b28c4-360">某些事件提供其他內容特定資訊。</span><span class="sxs-lookup"><span data-stu-id="b28c4-360">Some events provide additional context specific information.</span></span>

<span data-ttu-id="b28c4-361">使用手勢辨識器來捕捉手勢時，只需要執行幾個步驟：</span><span class="sxs-lookup"><span data-stu-id="b28c4-361">There are only a few steps required to capture gestures using a Gesture Recognizer:</span></span>
1. <span data-ttu-id="b28c4-362">建立新的手勢辨識器</span><span class="sxs-lookup"><span data-stu-id="b28c4-362">Create a new Gesture Recognizer</span></span>
2. <span data-ttu-id="b28c4-363">指定要監看的手勢</span><span class="sxs-lookup"><span data-stu-id="b28c4-363">Specify which gestures to watch for</span></span>
3. <span data-ttu-id="b28c4-364">訂閱這些手勢的事件</span><span class="sxs-lookup"><span data-stu-id="b28c4-364">Subscribe to events for those gestures</span></span>
4. <span data-ttu-id="b28c4-365">開始捕獲手勢</span><span class="sxs-lookup"><span data-stu-id="b28c4-365">Start capturing gestures</span></span>

### <a name="create-a-new-gesture-recognizer"></a><span data-ttu-id="b28c4-366">建立新的手勢辨識器</span><span class="sxs-lookup"><span data-stu-id="b28c4-366">Create a new Gesture Recognizer</span></span>

<span data-ttu-id="b28c4-367">若要使用 *GestureRecognizer* ，您必須建立 *GestureRecognizer* ：</span><span class="sxs-lookup"><span data-stu-id="b28c4-367">To use the *GestureRecognizer* , you must have created a *GestureRecognizer* :</span></span>

```cs
GestureRecognizer recognizer = new GestureRecognizer();
```

### <a name="specify-which-gestures-to-watch-for"></a><span data-ttu-id="b28c4-368">指定要監看的手勢</span><span class="sxs-lookup"><span data-stu-id="b28c4-368">Specify which gestures to watch for</span></span>

<span data-ttu-id="b28c4-369">透過 SetRecognizableGestures 指定您感興趣的手勢 *( # B1* ：</span><span class="sxs-lookup"><span data-stu-id="b28c4-369">Specify which gestures you are interested in via *SetRecognizableGestures()* :</span></span>

```cs
recognizer.SetRecognizableGestures(GestureSettings.Tap | GestureSettings.Hold);
```

### <a name="subscribe-to-events-for-those-gestures"></a><span data-ttu-id="b28c4-370">訂閱這些手勢的事件</span><span class="sxs-lookup"><span data-stu-id="b28c4-370">Subscribe to events for those gestures</span></span>

<span data-ttu-id="b28c4-371">針對您感興趣的手勢訂閱事件。</span><span class="sxs-lookup"><span data-stu-id="b28c4-371">Subscribe to events for the gestures you are interested in.</span></span>

```cs
void Start()
{
    recognizer.Tapped += GestureRecognizer_Tapped;
    recognizer.HoldStarted += GestureRecognizer_HoldStarted;
    recognizer.HoldCompleted += GestureRecognizer_HoldCompleted;
    recognizer.HoldCanceled += GestureRecognizer_HoldCanceled;
}
```

>[!NOTE]
><span data-ttu-id="b28c4-372">導覽和操作手勢在 *GestureRecognizer* 的實例上是互斥的。</span><span class="sxs-lookup"><span data-stu-id="b28c4-372">Navigation and Manipulation gestures are mutually exclusive on an instance of a *GestureRecognizer* .</span></span>

### <a name="start-capturing-gestures"></a><span data-ttu-id="b28c4-373">開始捕獲手勢</span><span class="sxs-lookup"><span data-stu-id="b28c4-373">Start capturing gestures</span></span>

<span data-ttu-id="b28c4-374">根據預設， *GestureRecognizer* 會在呼叫 *StartCapturingGestures ( # B1* 之前，不會監視輸入。</span><span class="sxs-lookup"><span data-stu-id="b28c4-374">By default, a *GestureRecognizer* does not monitor input until *StartCapturingGestures()* is called.</span></span> <span data-ttu-id="b28c4-375">如果在處理 *StopCapturingGestures ( # B3* 的框架之前執行輸入，可能會在 StopCapturingGestures 之後產生手勢事件， *( # B1* 呼叫。</span><span class="sxs-lookup"><span data-stu-id="b28c4-375">It is possible that a gesture event may be generated after *StopCapturingGestures()* is called if input was performed before the frame where *StopCapturingGestures()* was processed.</span></span> <span data-ttu-id="b28c4-376">*GestureRecognizer* 會記得在先前的畫面格進行實際發生的情況下，它是開啟或關閉，因此可以根據此框架的監看式目標啟動和停止手勢監視。</span><span class="sxs-lookup"><span data-stu-id="b28c4-376">The *GestureRecognizer* will remember whether it was on or off during the previous frame in which the gesture actually occurred, and so it is reliable to start and stop gesture monitoring based on this frame's gaze targeting.</span></span>

```cs
recognizer.StartCapturingGestures();
```

### <a name="stop-capturing-gestures"></a><span data-ttu-id="b28c4-377">停止捕捉手勢</span><span class="sxs-lookup"><span data-stu-id="b28c4-377">Stop capturing gestures</span></span>

<span data-ttu-id="b28c4-378">若要停止手勢辨識：</span><span class="sxs-lookup"><span data-stu-id="b28c4-378">To stop gesture recognition:</span></span>

```cs
recognizer.StopCapturingGestures();
```

### <a name="removing-a-gesture-recognizer"></a><span data-ttu-id="b28c4-379">移除手勢辨識器</span><span class="sxs-lookup"><span data-stu-id="b28c4-379">Removing a gesture recognizer</span></span>

<span data-ttu-id="b28c4-380">請記得在終結 *GestureRecognizer* 物件之前取消訂閱的事件。</span><span class="sxs-lookup"><span data-stu-id="b28c4-380">Remember to unsubscribe from subscribed events before destroying a *GestureRecognizer* object.</span></span>

```cs
void OnDestroy()
{
    recognizer.Tapped -= GestureRecognizer_Tapped;
    recognizer.HoldStarted -= GestureRecognizer_HoldStarted;
    recognizer.HoldCompleted -= GestureRecognizer_HoldCompleted;
    recognizer.HoldCanceled -= GestureRecognizer_HoldCanceled;
}
```

## <a name="rendering-the-motion-controller-model-in-unity"></a><span data-ttu-id="b28c4-381">在 Unity 中轉譯移動控制器模型</span><span class="sxs-lookup"><span data-stu-id="b28c4-381">Rendering the motion controller model in Unity</span></span>

<span data-ttu-id="b28c4-382">![移動控制器模型和遙傳](images/motioncontrollertest-teleport-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="b28c4-382">![Motion Controller model and teleportation](images/motioncontrollertest-teleport-1000px.png)</span></span><br>
<span data-ttu-id="b28c4-383">*移動控制器模型和遙傳*</span><span class="sxs-lookup"><span data-stu-id="b28c4-383">*Motion controller model and teleportation*</span></span>

<span data-ttu-id="b28c4-384">若要在您的應用程式中轉譯與您的使用者所持有的實體控制器相符的移動控制站，並在按下各種按鈕時表達清楚，您可以在 [混合現實工具](https://github.com/Microsoft/MixedRealityToolkit-Unity/)組中使用 **MotionController 預製專案** 。</span><span class="sxs-lookup"><span data-stu-id="b28c4-384">To render motion controllers in your app that match the physical controllers your users are holding and articulate as various buttons are pressed, you can use the **MotionController prefab** in the [Mixed Reality Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/).</span></span>  <span data-ttu-id="b28c4-385">這個預製專案會從系統已安裝的移動控制器驅動程式，在執行時間動態載入正確的 glTF 模型。</span><span class="sxs-lookup"><span data-stu-id="b28c4-385">This prefab dynamically loads the correct glTF model at runtime from the system's installed motion controller driver.</span></span>  <span data-ttu-id="b28c4-386">請務必以動態方式載入這些模型，而不是在編輯器中手動匯入這些模型，如此您的應用程式就會針對使用者可能擁有的任何目前和未來控制器顯示實際精確的3D 模型。</span><span class="sxs-lookup"><span data-stu-id="b28c4-386">It's important to load these models dynamically rather than importing them manually in the editor, so that your app will show physically accurate 3D models for any current and future controllers your users may have.</span></span>

1. <span data-ttu-id="b28c4-387">遵循 [消費者入門](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/GettingStarted.md) 指示下載 Mixed Reality 工具組，並將它新增至 Unity 專案。</span><span class="sxs-lookup"><span data-stu-id="b28c4-387">Follow the [Getting Started](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/GettingStarted.md) instructions to download the Mixed Reality Toolkit and add it to your Unity project.</span></span>
2. <span data-ttu-id="b28c4-388">如果您在消費者入門步驟中將相機替換成 *MixedRealityCameraParent* 預製專案，您就可以開始使用！</span><span class="sxs-lookup"><span data-stu-id="b28c4-388">If you replaced your camera with the *MixedRealityCameraParent* prefab as part of the Getting Started steps, you're good to go!</span></span>  <span data-ttu-id="b28c4-389">該預製專案包括移動控制器轉譯。</span><span class="sxs-lookup"><span data-stu-id="b28c4-389">That prefab includes motion controller rendering.</span></span>  <span data-ttu-id="b28c4-390">否則，請從 [專案] 窗格將 *資產/HoloToolkit/Input/Prefabs/MotionControllers* 加入場景中。</span><span class="sxs-lookup"><span data-stu-id="b28c4-390">Otherwise, add *Assets/HoloToolkit/Input/Prefabs/MotionControllers.prefab* into your scene from the Project pane.</span></span>  <span data-ttu-id="b28c4-391">當使用者在場景中 teleports 時，您會想要將該預製專案新增為您用來移動攝影機之任何父物件的子系，以便讓控制器與使用者一起使用。</span><span class="sxs-lookup"><span data-stu-id="b28c4-391">You'll want to add that prefab as a child of whatever parent object you use to move the camera around when the user teleports within your scene, so that the controllers come along with the user.</span></span>  <span data-ttu-id="b28c4-392">如果您的應用程式不需要 teleporting，只要在場景的根目錄新增預製專案即可。</span><span class="sxs-lookup"><span data-stu-id="b28c4-392">If your app does not involve teleporting, just add the prefab at the root of your scene.</span></span>

## <a name="throwing-objects"></a><span data-ttu-id="b28c4-393">擲回物件</span><span class="sxs-lookup"><span data-stu-id="b28c4-393">Throwing objects</span></span>

<span data-ttu-id="b28c4-394">在虛擬實境中擲回物件是較困難的問題，因此可能會先出現。</span><span class="sxs-lookup"><span data-stu-id="b28c4-394">Throwing objects in virtual reality is a harder problem then it may at first seem.</span></span> <span data-ttu-id="b28c4-395">如同大部分的實際互動，在遊戲中擲回時，它會以非預期的方式運作，並中斷深度。</span><span class="sxs-lookup"><span data-stu-id="b28c4-395">As with most physically based interactions, when throwing in game acts in an unexpected way, it is immediately obvious and breaks immersion.</span></span> <span data-ttu-id="b28c4-396">我們花了一些時間來思考如何表示實體正確的擲回行為，並提供一些指導方針，讓我們想要與您分享，並透過我們的平臺更新來啟用。</span><span class="sxs-lookup"><span data-stu-id="b28c4-396">We have spent some time thinking deeply about how to represent a physically correct throwing behavior, and have come up with a few guidelines, enabled through updates to our platform, that we would like to share with you.</span></span>

<span data-ttu-id="b28c4-397">您可以在 [這裡](https://github.com/keluecke/MixedRealityToolkit-Unity/blob/master/External/Unitypackages/ThrowingStarter.unitypackage)找到建議如何執行擲回的範例。</span><span class="sxs-lookup"><span data-stu-id="b28c4-397">You can find an example of how we recommend to implement throwing [here](https://github.com/keluecke/MixedRealityToolkit-Unity/blob/master/External/Unitypackages/ThrowingStarter.unitypackage).</span></span> <span data-ttu-id="b28c4-398">此範例會遵循下列四個指導方針：</span><span class="sxs-lookup"><span data-stu-id="b28c4-398">This sample follows these four guidelines:</span></span>
* <span data-ttu-id="b28c4-399">**使用控制器的 *速度* ，而不是位置** 。</span><span class="sxs-lookup"><span data-stu-id="b28c4-399">**Use the controller’s *velocity* instead of position** .</span></span> <span data-ttu-id="b28c4-400">在 Windows 的11月更新中，我們引進了「 [近似」位置追蹤狀態](../../design/motion-controllers.md#controller-tracking-state)時的行為變更。</span><span class="sxs-lookup"><span data-stu-id="b28c4-400">In the November update to Windows, we introduced a change in behavior when in the [''Approximate'' positional tracking state](../../design/motion-controllers.md#controller-tracking-state).</span></span> <span data-ttu-id="b28c4-401">處於此狀態時，系統會繼續回報控制器的相關速度資訊，只要我們認為它的精確度很高，通常會比位置維持高準確度更長。</span><span class="sxs-lookup"><span data-stu-id="b28c4-401">When in this state, velocity information about the controller will continue to be reported for as long as we believe it is high accuracy, which is often longer than position remains high accuracy.</span></span>
* <span data-ttu-id="b28c4-402">**納入控制器的 *角度速度*** 。</span><span class="sxs-lookup"><span data-stu-id="b28c4-402">**Incorporate the *angular velocity* of the controller** .</span></span> <span data-ttu-id="b28c4-403">此邏輯全部包含在靜態方法的檔案中，該檔案 `throwing.cs` 位於 `GetThrownObjectVelAngVel` 上述連結的封裝內：</span><span class="sxs-lookup"><span data-stu-id="b28c4-403">This logic is all contained in the `throwing.cs` file in the `GetThrownObjectVelAngVel` static method, within the package linked above:</span></span>
   1. <span data-ttu-id="b28c4-404">由於 conserved 的角度速度，擲回的物件必須維持與擲回時相同的角度速度： `objectAngularVelocity = throwingControllerAngularVelocity;`</span><span class="sxs-lookup"><span data-stu-id="b28c4-404">As angular velocity is conserved, the thrown object must maintain the same angular velocity as it had at the moment of the throw: `objectAngularVelocity = throwingControllerAngularVelocity;`</span></span>
   2. <span data-ttu-id="b28c4-405">因為擲回之物件的中心可能不是在底框姿勢的原點，所以它可能會有不同的速度，而在使用者的參考框架中，控制器則可能會有不同的速度。</span><span class="sxs-lookup"><span data-stu-id="b28c4-405">As the center of mass of the thrown object is likely not at the origin of the grip pose, it likely has a different velocity then that of the controller in the frame of reference of the user.</span></span> <span data-ttu-id="b28c4-406">以這種方式產生的物件速度的部分，就是在控制器原點周圍擲回物件的最大中心的瞬間相切速度。</span><span class="sxs-lookup"><span data-stu-id="b28c4-406">The portion of the object’s velocity contributed in this way is the instantaneous tangential velocity of the center of mass of the thrown object around the controller origin.</span></span> <span data-ttu-id="b28c4-407">這種相切速度是控制器角度速度的交叉乘積，向量表示控制器原點與擲回物件的中央之間的距離。</span><span class="sxs-lookup"><span data-stu-id="b28c4-407">This tangential velocity is the cross product of the angular velocity of the controller with the vector representing the distance between the controller origin and the center of mass of the thrown object.</span></span>

      ```cs
      Vector3 radialVec = thrownObjectCenterOfMass - throwingControllerPos;
      Vector3 tangentialVelocity = Vector3.Cross(throwingControllerAngularVelocity, radialVec);
      ```

   3. <span data-ttu-id="b28c4-408">擲回物件的速度總計是控制器速度和這個相切速度的總和： `objectVelocity = throwingControllerVelocity + tangentialVelocity;`</span><span class="sxs-lookup"><span data-stu-id="b28c4-408">The total velocity of the thrown object is thus the sum of velocity of the controller and this tangential velocity: `objectVelocity = throwingControllerVelocity + tangentialVelocity;`</span></span>

* <span data-ttu-id="b28c4-409">請密切 **注意我們應用速度的 *時間*** 。</span><span class="sxs-lookup"><span data-stu-id="b28c4-409">**Pay close attention to the *time* at which we apply the velocity** .</span></span> <span data-ttu-id="b28c4-410">按下按鈕時，最多可能需要20毫秒該事件，才能透過藍牙向上到作業系統。</span><span class="sxs-lookup"><span data-stu-id="b28c4-410">When a button is pressed, it can take up to 20ms for that event to bubble up through Bluetooth to the operating system.</span></span> <span data-ttu-id="b28c4-411">這表示，如果您將控制器狀態變更從按下的狀態變更為未按下（反之亦然），則控制器會引發您所取得的資訊，而這項資訊會在狀態變更之前出現。</span><span class="sxs-lookup"><span data-stu-id="b28c4-411">This means that if you poll for a controller state change from pressed to not pressed or vice versa, the controller pose information you get with it will actually be ahead of this change in state.</span></span> <span data-ttu-id="b28c4-412">此外，我們的輪詢 API 所呈現的控制器會向前預測，以反映畫面上顯示的可能原因，未來可能會更20毫秒。</span><span class="sxs-lookup"><span data-stu-id="b28c4-412">Further, the controller pose presented by our polling API is forward predicted to reflect a likely pose at the time the frame will be displayed which could be more then 20ms in the future.</span></span> <span data-ttu-id="b28c4-413">這適合用來 *呈現* 保留的物件，但是會在使用者釋放擲回的時間點時，將我們的時間問題轉譯為 *目標* 物件。</span><span class="sxs-lookup"><span data-stu-id="b28c4-413">This is good for *rendering* held objects, but compounds our time problem for *targeting* the object as we calculate the trajectory for the moment the user released their throw.</span></span> <span data-ttu-id="b28c4-414">幸運的是，在11月更新中，當傳送 *InteractionSourcePressed* 或 *InteractionSourceReleased* 這類 Unity 事件時，該狀態會包含實際按下或放開按鈕時的歷程記錄資料。</span><span class="sxs-lookup"><span data-stu-id="b28c4-414">Fortunately, with the November update, when a Unity event like *InteractionSourcePressed* or *InteractionSourceReleased* is sent, the state includes the historical pose data from back when the button was actually pressed or released.</span></span>  <span data-ttu-id="b28c4-415">若要在擲回期間取得最精確的控制器轉譯和控制器目標，您必須適當地正確地使用輪詢和事件：</span><span class="sxs-lookup"><span data-stu-id="b28c4-415">To get the most accurate controller rendering and controller targeting during throws, you must correctly use polling and eventing, as appropriate:</span></span>
   * <span data-ttu-id="b28c4-416">針對每個畫面格的 **控制器呈現** ，您的應用程式應該將控制器的 *GameObject* 放在向前預測的控制器上，以表示目前畫面格的 photon 時間。</span><span class="sxs-lookup"><span data-stu-id="b28c4-416">For **controller rendering** each frame, your app should position the controller's *GameObject* at the forward-predicted controller pose for the current frame’s photon time.</span></span>  <span data-ttu-id="b28c4-417">您可以從 Unity 輪詢 Api （例如 XR）取得此資料 *[。InputTracking. GetLocalPosition](https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html)* 或 *[XR。Wsa。輸入. InteractionManager. GetCurrentReading](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.GetCurrentReading.html)* 。</span><span class="sxs-lookup"><span data-stu-id="b28c4-417">You get this data from Unity polling APIs like *[XR.InputTracking.GetLocalPosition](https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html)* or *[XR.WSA.Input.InteractionManager.GetCurrentReading](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.GetCurrentReading.html)* .</span></span>
   * <span data-ttu-id="b28c4-418">針對以按下或放開的 **控制器為目標的控制器** ，您的應用程式應該根據該按下或釋放事件的歷程控制器姿勢來 raycast 和計算軌跡。</span><span class="sxs-lookup"><span data-stu-id="b28c4-418">For **controller targeting** upon a press or release, your app should raycast and calculate trajectories based on the historical controller pose for that press or release event.</span></span>  <span data-ttu-id="b28c4-419">您可以從 Unity 事件 Api 取得這類資料，例如 *[InteractionManager. InteractionSourcePressed](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.InteractionSourcePressed.html)* 。</span><span class="sxs-lookup"><span data-stu-id="b28c4-419">You get this data from Unity eventing APIs, like *[InteractionManager.InteractionSourcePressed](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.InteractionSourcePressed.html)* .</span></span>
* <span data-ttu-id="b28c4-420">**使用** 底框姿勢。</span><span class="sxs-lookup"><span data-stu-id="b28c4-420">**Use the grip pose** .</span></span> <span data-ttu-id="b28c4-421">相對於底框姿勢（而不是指標姿勢）回報角度速度和速度。</span><span class="sxs-lookup"><span data-stu-id="b28c4-421">Angular velocity and velocity are reported relative to the grip pose, not pointer pose.</span></span>

<span data-ttu-id="b28c4-422">未來的 Windows 更新將持續改善擲回，而您可以預期在此找到更多資訊。</span><span class="sxs-lookup"><span data-stu-id="b28c4-422">Throwing will continue to improve with future Windows updates, and you can expect to find more information on it here.</span></span>

## <a name="gesture-and-motion-controllers-in-mrtk-v2"></a><span data-ttu-id="b28c4-423">MRTK v2 中的手勢和移動控制器</span><span class="sxs-lookup"><span data-stu-id="b28c4-423">Gesture and Motion Controllers in MRTK v2</span></span>

<span data-ttu-id="b28c4-424">您可以從輸入管理員存取手勢和移動控制器。</span><span class="sxs-lookup"><span data-stu-id="b28c4-424">You can access gesture and motion controller from the input Manager.</span></span>
* [<span data-ttu-id="b28c4-425">MRTK v2 中的手勢</span><span class="sxs-lookup"><span data-stu-id="b28c4-425">Gesture in MRTK v2</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Gestures.html)
* [<span data-ttu-id="b28c4-426">MRTK v2 中的動作控制器</span><span class="sxs-lookup"><span data-stu-id="b28c4-426">Motion Controller in MRTK v2</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Controllers.html)


## <a name="follow-along-with-tutorials"></a><span data-ttu-id="b28c4-427">遵循教學課程</span><span class="sxs-lookup"><span data-stu-id="b28c4-427">Follow along with tutorials</span></span>

<span data-ttu-id="b28c4-428">混合現實學術中提供逐步教學課程，包含更詳細的自訂範例：</span><span class="sxs-lookup"><span data-stu-id="b28c4-428">Step-by-step tutorials, with more detailed customization examples, are available in the Mixed Reality Academy:</span></span>

- [<span data-ttu-id="b28c4-429">MR Input 211：筆勢</span><span class="sxs-lookup"><span data-stu-id="b28c4-429">MR Input 211: Gesture</span></span>](tutorials/holograms-211.md)
- [<span data-ttu-id="b28c4-430">MR Input 213：運動控制器</span><span class="sxs-lookup"><span data-stu-id="b28c4-430">MR Input 213: Motion controllers</span></span>](../../deprecated/mixed-reality-213.md)

<span data-ttu-id="b28c4-431">[![MR 輸入 213-移動控制器](images/mr213-main-600px.jpg)](https://docs.microsoft.com/windows/mixed-reality/mixed-reality-213)</span><span class="sxs-lookup"><span data-stu-id="b28c4-431">[![MR Input 213 - Motion controller](images/mr213-main-600px.jpg)](https://docs.microsoft.com/windows/mixed-reality/mixed-reality-213)</span></span><br>
<span data-ttu-id="b28c4-432">*MR 輸入 213-移動控制器*</span><span class="sxs-lookup"><span data-stu-id="b28c4-432">*MR Input 213 - Motion controller*</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="b28c4-433">下一個開發檢查點</span><span class="sxs-lookup"><span data-stu-id="b28c4-433">Next Development Checkpoint</span></span>

<span data-ttu-id="b28c4-434">依循我們配置的 Unity 開發檢查點旅程，此時您會探索 MRTK核心建置組塊。</span><span class="sxs-lookup"><span data-stu-id="b28c4-434">If you're following the Unity development checkpoint journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="b28c4-435">接下來，您可以繼續進行下一個建置組塊：</span><span class="sxs-lookup"><span data-stu-id="b28c4-435">From here, you can proceed to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="b28c4-436">手部和眼睛追蹤</span><span class="sxs-lookup"><span data-stu-id="b28c4-436">Hand and eye tracking</span></span>](hand-eye-in-unit.md)

<span data-ttu-id="b28c4-437">或者，直接跳到混合實境平台功能和 API 的主題：</span><span class="sxs-lookup"><span data-stu-id="b28c4-437">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="b28c4-438">共用體驗</span><span class="sxs-lookup"><span data-stu-id="b28c4-438">Shared experiences</span></span>](shared-experiences-in-unity.md)

<span data-ttu-id="b28c4-439">您可以隨時回到 [Unity 開發檢查點](unity-development-overview.md#2-core-building-blocks)。</span><span class="sxs-lookup"><span data-stu-id="b28c4-439">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="b28c4-440">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b28c4-440">See also</span></span>

* [<span data-ttu-id="b28c4-441">頭部目光和行動</span><span class="sxs-lookup"><span data-stu-id="b28c4-441">Head-gaze and commit</span></span>](../../design/gaze-and-commit.md)
* [<span data-ttu-id="b28c4-442">運動控制器</span><span class="sxs-lookup"><span data-stu-id="b28c4-442">Motion controllers</span></span>](../../design/motion-controllers.md)
