---
title: Unity 中的動作控制器
description: 瞭解如何使用 XR 和一般按鈕和軸 Api，在 Unity 中使用移動控制器輸入來採取行動。
author: hferrone
ms.author: alexturn
ms.date: 12/1/2020
ms.topic: article
keywords: 運動控制器、unity、輸入、混合現實耳機、windows mixed reality 耳機、虛擬實境耳機、MRTK、混合現實工具組
ms.openlocfilehash: bf9aad0ee67a406280cefedec8b55fb1de130b8b
ms.sourcegitcommit: a1bb77f729ee2e0b3dbd1c2c837bb7614ba7b9bd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/14/2021
ms.locfileid: "98192952"
---
# <a name="motion-controllers-in-unity"></a><span data-ttu-id="143b2-104">Unity 中的動作控制器</span><span class="sxs-lookup"><span data-stu-id="143b2-104">Motion controllers in Unity</span></span>

<span data-ttu-id="143b2-105">您可以透過兩種主要方式，在您 [的 [Unity](gaze-in-unity.md)]、[ [手手勢](../../design/gaze-and-commit.md#composite-gestures) ] 和 [ [運動] 控制器](../../design/motion-controllers.md) 中針對 HoloLens 和沉浸式 HMD 採取行動。</span><span class="sxs-lookup"><span data-stu-id="143b2-105">There are two key ways to take action on your [gaze in Unity](gaze-in-unity.md), [hand gestures](../../design/gaze-and-commit.md#composite-gestures) and [motion controllers](../../design/motion-controllers.md) in HoloLens and Immersive HMD.</span></span> <span data-ttu-id="143b2-106">您可以透過 Unity 中的相同 Api，存取兩個空間輸入來源的資料。</span><span class="sxs-lookup"><span data-stu-id="143b2-106">You access the data for both sources of spatial input through the same APIs in Unity.</span></span>

<span data-ttu-id="143b2-107">Unity 提供兩種主要方式來存取 Windows Mixed Reality 的空間輸入資料。</span><span class="sxs-lookup"><span data-stu-id="143b2-107">Unity provides two primary ways to access spatial input data for Windows Mixed Reality.</span></span> <span data-ttu-id="143b2-108">常見的 *GetButton/GetAxis* api 可跨多個 Unity XR sdk 運作，而 Windows Mixed Reality 特定的 *InteractionManager/GestureRecognizer* api 會公開一組完整的空間輸入資料。</span><span class="sxs-lookup"><span data-stu-id="143b2-108">The common *Input.GetButton/Input.GetAxis* APIs work across multiple Unity XR SDKs, while the *InteractionManager/GestureRecognizer* API specific to Windows Mixed Reality exposes the full set of spatial input data.</span></span>

## <a name="unity-xr-input-apis"></a><span data-ttu-id="143b2-109">Unity XR 輸入 Api</span><span class="sxs-lookup"><span data-stu-id="143b2-109">Unity XR input APIs</span></span>

<span data-ttu-id="143b2-110">針對新的專案，我們建議您從頭開始使用新的 XR 輸入 Api。</span><span class="sxs-lookup"><span data-stu-id="143b2-110">For new projects, we recommend using the new XR input APIs from the beginning.</span></span> 

<span data-ttu-id="143b2-111">您可以在這裡找到有關 [XR api](https://docs.unity3d.com/Manual/xr_input.html)的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="143b2-111">You can find more information about the [XR APIs here](https://docs.unity3d.com/Manual/xr_input.html).</span></span>

## <a name="unity-buttonaxis-mapping-table"></a><span data-ttu-id="143b2-112">Unity 按鈕/軸對應表</span><span class="sxs-lookup"><span data-stu-id="143b2-112">Unity button/axis mapping table</span></span>

<span data-ttu-id="143b2-113">Unity 的 Windows Mixed Reality 移動控制器的輸入管理員可透過 *GetButton/GetAxis* api 支援下列按鈕和軸識別碼。</span><span class="sxs-lookup"><span data-stu-id="143b2-113">Unity's Input Manager for Windows Mixed Reality motion controllers supports the button and axis IDs listed below through the *Input.GetButton/GetAxis* APIs.</span></span> <span data-ttu-id="143b2-114">「Windows MR 特定」資料行指的是 *InteractionSourceState* 類型可用的屬性。</span><span class="sxs-lookup"><span data-stu-id="143b2-114">The "Windows MR-specific" column refers to properties available off of the *InteractionSourceState* type.</span></span> <span data-ttu-id="143b2-115">下列各節將詳細說明每個 Api。</span><span class="sxs-lookup"><span data-stu-id="143b2-115">Each of these APIs is described in detail in the sections below.</span></span>

<span data-ttu-id="143b2-116">Windows Mixed Reality 的按鈕/軸識別碼對應通常會符合 Oculus 按鈕/軸識別碼。</span><span class="sxs-lookup"><span data-stu-id="143b2-116">The button/axis ID mappings for Windows Mixed Reality generally match the Oculus button/axis IDs.</span></span>

<span data-ttu-id="143b2-117">Windows Mixed Reality 的按鈕/軸識別碼對應有兩種不同于 OpenVR 的對應：</span><span class="sxs-lookup"><span data-stu-id="143b2-117">The button/axis ID mappings for Windows Mixed Reality differ from OpenVR's mappings in two ways:</span></span>
1. <span data-ttu-id="143b2-118">對應會使用與操縱杆不同的觸控板識別碼，以支援具有 thumbsticks 和 touchpads 的控制器。</span><span class="sxs-lookup"><span data-stu-id="143b2-118">The mapping uses touchpad IDs that are distinct from thumbstick, to support controllers with both thumbsticks and touchpads.</span></span>
2. <span data-ttu-id="143b2-119">對應可避免多載功能表按鈕的 A 和 X 按鈕識別碼，讓它們可用於實體 ABXY 按鈕。</span><span class="sxs-lookup"><span data-stu-id="143b2-119">The mapping avoids overloading the A and X button IDs for the Menu buttons to leave them available for the physical ABXY buttons.</span></span>

<table>
<tr>
<th rowspan="2"><span data-ttu-id="143b2-120">輸入</span><span class="sxs-lookup"><span data-stu-id="143b2-120">Input</span></span> </th><th colspan="2"><span data-ttu-id="143b2-121"><a href="motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis">通用 Unity API</a></span><span class="sxs-lookup"><span data-stu-id="143b2-121"><a href="motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis">Common Unity APIs</a></span></span><br /><span data-ttu-id="143b2-122"> (輸入. GetButton/GetAxis) </span><span class="sxs-lookup"><span data-stu-id="143b2-122">(Input.GetButton/GetAxis)</span></span> </th><th rowspan="2"><span data-ttu-id="143b2-123"><a href="motion-controllers-in-unity.md#windows-specific-apis-xrwsainput">Windows MR 專用輸入 API</a></span><span class="sxs-lookup"><span data-stu-id="143b2-123"><a href="motion-controllers-in-unity.md#windows-specific-apis-xrwsainput">Windows MR-specific Input API</a></span></span><br /><span data-ttu-id="143b2-124"> (XR。Wsa。輸入) </span><span class="sxs-lookup"><span data-stu-id="143b2-124">(XR.WSA.Input)</span></span></th>
</tr><tr>
<th> <span data-ttu-id="143b2-125">左手</span><span class="sxs-lookup"><span data-stu-id="143b2-125">Left hand</span></span> </th><th> <span data-ttu-id="143b2-126">右手</span><span class="sxs-lookup"><span data-stu-id="143b2-126">Right hand</span></span></th>
</tr><tr>
<td> <span data-ttu-id="143b2-127">已按下 Select 觸發程式</span><span class="sxs-lookup"><span data-stu-id="143b2-127">Select trigger pressed</span></span> </td><td> <span data-ttu-id="143b2-128">軸 9 = 1。0</span><span class="sxs-lookup"><span data-stu-id="143b2-128">Axis 9 = 1.0</span></span> </td><td> <span data-ttu-id="143b2-129">軸 10 = 1。0</span><span class="sxs-lookup"><span data-stu-id="143b2-129">Axis 10 = 1.0</span></span> </td><td> <span data-ttu-id="143b2-130">selectPressed</span><span class="sxs-lookup"><span data-stu-id="143b2-130">selectPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="143b2-131">選取觸發程式類比值</span><span class="sxs-lookup"><span data-stu-id="143b2-131">Select trigger analog value</span></span> </td><td> <span data-ttu-id="143b2-132">軸9</span><span class="sxs-lookup"><span data-stu-id="143b2-132">Axis 9</span></span> </td><td> <span data-ttu-id="143b2-133">軸10</span><span class="sxs-lookup"><span data-stu-id="143b2-133">Axis 10</span></span> </td><td> <span data-ttu-id="143b2-134">selectPressedAmount</span><span class="sxs-lookup"><span data-stu-id="143b2-134">selectPressedAmount</span></span></td>
</tr><tr>
<td> <span data-ttu-id="143b2-135">選取觸發程式部分按下</span><span class="sxs-lookup"><span data-stu-id="143b2-135">Select trigger partially pressed</span></span> </td><td> <span data-ttu-id="143b2-136">按鈕 14 <i> (遊戲台相容性) </i> </span><span class="sxs-lookup"><span data-stu-id="143b2-136">Button 14 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="143b2-137">按鈕 15 <i> (遊戲台相容性) </i> </span><span class="sxs-lookup"><span data-stu-id="143b2-137">Button 15 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="143b2-138">selectPressedAmount &gt; 0。0</span><span class="sxs-lookup"><span data-stu-id="143b2-138">selectPressedAmount &gt; 0.0</span></span></td>
</tr><tr>
<td> <span data-ttu-id="143b2-139">已按下功能表按鈕</span><span class="sxs-lookup"><span data-stu-id="143b2-139">Menu button pressed</span></span> </td><td> <span data-ttu-id="143b2-140">按鈕 6 \*</span><span class="sxs-lookup"><span data-stu-id="143b2-140">Button 6\*</span></span> </td><td> <span data-ttu-id="143b2-141">按鈕 7 \*</span><span class="sxs-lookup"><span data-stu-id="143b2-141">Button 7\*</span></span> </td><td> <span data-ttu-id="143b2-142">menuPressed</span><span class="sxs-lookup"><span data-stu-id="143b2-142">menuPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="143b2-143">已按下手柄按鈕</span><span class="sxs-lookup"><span data-stu-id="143b2-143">Grip button pressed</span></span> </td><td> <span data-ttu-id="143b2-144">軸 11 = 1.0 (沒有類比值) </span><span class="sxs-lookup"><span data-stu-id="143b2-144">Axis 11 = 1.0 (no analog values)</span></span><br /><span data-ttu-id="143b2-145">按鈕 4 <i> (遊戲台相容性) </i> </span><span class="sxs-lookup"><span data-stu-id="143b2-145">Button 4 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="143b2-146">軸 12 = 1.0 (沒有類比值) </span><span class="sxs-lookup"><span data-stu-id="143b2-146">Axis 12 = 1.0 (no analog values)</span></span><br /><span data-ttu-id="143b2-147">按鈕 5 <i> (遊戲台相容性) </i> </span><span class="sxs-lookup"><span data-stu-id="143b2-147">Button 5 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="143b2-148">抓住</span><span class="sxs-lookup"><span data-stu-id="143b2-148">grasped</span></span></td>
</tr><tr>
<td> <span data-ttu-id="143b2-149">操縱杆 X <i> (左：-1.0，右： 1.0) </i> </span><span class="sxs-lookup"><span data-stu-id="143b2-149">Thumbstick X <i>(left: -1.0, right: 1.0)</i> </span></span></td><td> <span data-ttu-id="143b2-150">軸1</span><span class="sxs-lookup"><span data-stu-id="143b2-150">Axis 1</span></span> </td><td> <span data-ttu-id="143b2-151">軸4</span><span class="sxs-lookup"><span data-stu-id="143b2-151">Axis 4</span></span> </td><td> <span data-ttu-id="143b2-152">thumbstickPosition. x</span><span class="sxs-lookup"><span data-stu-id="143b2-152">thumbstickPosition.x</span></span></td>
</tr><tr>
<td> <span data-ttu-id="143b2-153">操縱杆 Y <i> (top：-1.0，底端： 1.0) </i> </span><span class="sxs-lookup"><span data-stu-id="143b2-153">Thumbstick Y <i>(top: -1.0, bottom: 1.0)</i> </span></span></td><td> <span data-ttu-id="143b2-154">軸2</span><span class="sxs-lookup"><span data-stu-id="143b2-154">Axis 2</span></span> </td><td> <span data-ttu-id="143b2-155">軸5</span><span class="sxs-lookup"><span data-stu-id="143b2-155">Axis 5</span></span> </td><td> <span data-ttu-id="143b2-156">thumbstickPosition. y</span><span class="sxs-lookup"><span data-stu-id="143b2-156">thumbstickPosition.y</span></span></td>
</tr><tr>
<td> <span data-ttu-id="143b2-157">已按下操縱杆</span><span class="sxs-lookup"><span data-stu-id="143b2-157">Thumbstick pressed</span></span> </td><td> <span data-ttu-id="143b2-158">按鈕8</span><span class="sxs-lookup"><span data-stu-id="143b2-158">Button 8</span></span> </td><td> <span data-ttu-id="143b2-159">按鈕9</span><span class="sxs-lookup"><span data-stu-id="143b2-159">Button 9</span></span> </td><td> <span data-ttu-id="143b2-160">thumbstickPressed</span><span class="sxs-lookup"><span data-stu-id="143b2-160">thumbstickPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="143b2-161">觸控板 X <i> (左：-1.0、右邊： 1.0) </i> </span><span class="sxs-lookup"><span data-stu-id="143b2-161">Touchpad X <i>(left: -1.0, right: 1.0)</i> </span></span></td><td> <span data-ttu-id="143b2-162">軸 17 \*</span><span class="sxs-lookup"><span data-stu-id="143b2-162">Axis 17\*</span></span> </td><td> <span data-ttu-id="143b2-163">軸 19 \*</span><span class="sxs-lookup"><span data-stu-id="143b2-163">Axis 19\*</span></span> </td><td> <span data-ttu-id="143b2-164">touchpadPosition. x</span><span class="sxs-lookup"><span data-stu-id="143b2-164">touchpadPosition.x</span></span></td>
</tr><tr>
<td> <span data-ttu-id="143b2-165">觸控板 Y <i> (頂端：-1.0、底部： 1.0) </i> </span><span class="sxs-lookup"><span data-stu-id="143b2-165">Touchpad Y <i>(top: -1.0, bottom: 1.0)</i> </span></span></td><td> <span data-ttu-id="143b2-166">軸 18 \*</span><span class="sxs-lookup"><span data-stu-id="143b2-166">Axis 18\*</span></span> </td><td> <span data-ttu-id="143b2-167">軸 20 \*</span><span class="sxs-lookup"><span data-stu-id="143b2-167">Axis 20\*</span></span> </td><td> <span data-ttu-id="143b2-168">touchpadPosition. y</span><span class="sxs-lookup"><span data-stu-id="143b2-168">touchpadPosition.y</span></span></td>
</tr><tr>
<td> <span data-ttu-id="143b2-169">觸及觸控板</span><span class="sxs-lookup"><span data-stu-id="143b2-169">Touchpad touched</span></span> </td><td> <span data-ttu-id="143b2-170">按鈕 18 \*</span><span class="sxs-lookup"><span data-stu-id="143b2-170">Button 18\*</span></span> </td><td> <span data-ttu-id="143b2-171">按鈕 19 \*</span><span class="sxs-lookup"><span data-stu-id="143b2-171">Button 19\*</span></span> </td><td> <span data-ttu-id="143b2-172">touchpadTouched</span><span class="sxs-lookup"><span data-stu-id="143b2-172">touchpadTouched</span></span></td>
</tr><tr>
<td> <span data-ttu-id="143b2-173">已按下觸控板</span><span class="sxs-lookup"><span data-stu-id="143b2-173">Touchpad pressed</span></span> </td><td> <span data-ttu-id="143b2-174">按鈕 16 \*</span><span class="sxs-lookup"><span data-stu-id="143b2-174">Button 16\*</span></span> </td><td> <span data-ttu-id="143b2-175">按鈕 17 \*</span><span class="sxs-lookup"><span data-stu-id="143b2-175">Button 17\*</span></span> </td><td> <span data-ttu-id="143b2-176">touchpadPressed</span><span class="sxs-lookup"><span data-stu-id="143b2-176">touchpadPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="143b2-177">6DoF 抓住姿勢或指標姿勢</span><span class="sxs-lookup"><span data-stu-id="143b2-177">6DoF grip pose or pointer pose</span></span> </td><td colspan="2"> <span data-ttu-id="143b2-178">僅限<i>握</i>姿勢： <a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html">XR。InputTracking. GetLocalPosition</a></span><span class="sxs-lookup"><span data-stu-id="143b2-178"><i>Grip</i> pose only: <a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html">XR.InputTracking.GetLocalPosition</a></span></span><br /><span data-ttu-id="143b2-179"><a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalRotation.html">XR.InputTracking.GetLocalRotation</a></span><span class="sxs-lookup"><span data-stu-id="143b2-179"><a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalRotation.html">XR.InputTracking.GetLocalRotation</a></span></span></td><td> <span data-ttu-id="143b2-180">以引數 <i>形式傳遞底</i> 框或 <i>指標</i> ： SourceState. sourcePose. TryGetPosition</span><span class="sxs-lookup"><span data-stu-id="143b2-180">Pass <i>Grip</i> or <i>Pointer</i> as an argument: sourceState.sourcePose.TryGetPosition</span></span><br /><span data-ttu-id="143b2-181">sourceState.sourcePose.TryGetRotation</span><span class="sxs-lookup"><span data-stu-id="143b2-181">sourceState.sourcePose.TryGetRotation</span></span><br /></td>
</tr><tr>
<td> <span data-ttu-id="143b2-182">追蹤狀態</span><span class="sxs-lookup"><span data-stu-id="143b2-182">Tracking state</span></span> </td><td colspan="2"> <span data-ttu-id="143b2-183"><i>職位精確度和來源遺失風險僅可透過 MR 專屬 API 取得</i> </span><span class="sxs-lookup"><span data-stu-id="143b2-183"><i>Position accuracy and source loss risk only available through MR-specific API</i> </span></span></td><td> <span data-ttu-id="143b2-184"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourcePose-positionAccuracy.html">sourceState.sourcePose.positionAccuracy</a></span><span class="sxs-lookup"><span data-stu-id="143b2-184"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourcePose-positionAccuracy.html">sourceState.sourcePose.positionAccuracy</a></span></span><br /><span data-ttu-id="143b2-185"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourceProperties-sourceLossRisk.html">sourceState。 sourceLossRisk</a></span><span class="sxs-lookup"><span data-stu-id="143b2-185"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourceProperties-sourceLossRisk.html">sourceState.properties.sourceLossRisk</a></span></span></td>
</tr>
</table>

>[!NOTE]
><span data-ttu-id="143b2-186">這些按鈕/軸識別碼與 Unity 針對 OpenVR 所使用的識別碼不同，因為 gamepads、Oculus Touch 和 OpenVR 所使用的對應中發生衝突。</span><span class="sxs-lookup"><span data-stu-id="143b2-186">These button/axis IDs differ from the IDs that Unity uses for OpenVR due to collisions in the mappings used by gamepads, Oculus Touch and OpenVR.</span></span>

<!-- ### Using HP Reverb G2 controllers

If you're using the HP Reverb G2 controllers, refer to the table below for button and axis IDs.

<table>
<tr>
<th rowspan="2"><a href="https://docs.unity3d.com/ScriptReference/XR.CommonUsages.html">Input </th><th colspan="2">Common Unity APIs</a><br />(Input.GetButton/GetAxis) </th><th rowspan="2">HP Reverb G2 Input API</a></th>
</tr><tr>
<th> Left hand </th><th> Right hand</th>
</tr><tr>
<td> Primary2DAxis </td><td> Axis 1 (X) / Axis 2 (Y) </td><td> Axis 4 (X) / Axis 5(Y) </td><td> Thumbstick</td>
</tr><tr>
<td> Trigger pressed </td><td> Axis 9 </td><td> Axis 10 </td><td> Index trigger</td>
</tr><tr>
<td> Grip </td><td> Axis 11d </td><td> Axis 12 </td><td> Grip trigger</td>
</tr><tr>
<td> PrimaryButton pressed </td><td> Button 2 </td><td> Button 0 </td><td> Menu button pressed</td>
</tr><tr>
<td> SecondaryButton pressed </td><td> Button 3 </td><td> Button 1 </td><td> A/X button</td>
</tr><tr>
<td> GripButton </td><td> Button 4 </td><td> Button 5 </td><td> Grip trigger</td>
</tr><tr>
<td> TriggerButton </td><td> Button 14 </td><td> Button 15 </td><td> Index trigger</td>
</tr><tr>
</tr>
</table> -->


## <a name="grip-pose-vs-pointing-pose"></a><span data-ttu-id="143b2-187">底姿勢與指標姿勢</span><span class="sxs-lookup"><span data-stu-id="143b2-187">Grip pose vs. pointing pose</span></span>

<span data-ttu-id="143b2-188">Windows Mixed Reality 支援各種外型規格中的動作控制器。</span><span class="sxs-lookup"><span data-stu-id="143b2-188">Windows Mixed Reality supports motion controllers in a variety of form factors.</span></span> <span data-ttu-id="143b2-189">每個控制器的設計都不同于使用者的手邊位置與自然「轉寄」方向之間的關聯性，而應用程式在轉譯控制器時會用到指標。</span><span class="sxs-lookup"><span data-stu-id="143b2-189">Each controller's design differs in its relationship between the user's hand position and the natural "forward" direction that apps should use for pointing when rendering the controller.</span></span>

<span data-ttu-id="143b2-190">為了更妥善地表示這些控制器，您可以針對每個互動來源（底框 **姿勢** 和 **指標姿勢**）調查兩種類型的姿勢。</span><span class="sxs-lookup"><span data-stu-id="143b2-190">To better represent these controllers, there are two kinds of poses you can investigate for each interaction source, the **grip pose** and the **pointer pose**.</span></span> <span data-ttu-id="143b2-191">框姿勢和指標姿勢座標都是由全域 Unity 全局座標中的所有 Unity Api 表示。</span><span class="sxs-lookup"><span data-stu-id="143b2-191">Both the grip pose and pointer pose coordinates are expressed by all Unity APIs in global Unity world coordinates.</span></span>

### <a name="grip-pose"></a><span data-ttu-id="143b2-192">握住姿勢</span><span class="sxs-lookup"><span data-stu-id="143b2-192">Grip pose</span></span>

<span data-ttu-id="143b2-193">底框 **姿勢** 代表使用者棕櫚的位置（由 HoloLens 偵測或保留移動控制器）。</span><span class="sxs-lookup"><span data-stu-id="143b2-193">The **grip pose** represents the location of the users palm, either detected by a HoloLens or holding a motion controller.</span></span>

<span data-ttu-id="143b2-194">在沉浸式耳機上，把手姿勢最適合用來 **呈現使用者手或\*\*\*\*使用者手中所持有的物件**。</span><span class="sxs-lookup"><span data-stu-id="143b2-194">On immersive headsets, the grip pose is best used to render **the user's hand** or **an object held in the user's hand**.</span></span> <span data-ttu-id="143b2-195">視覺化運動控制器時，也會使用底框姿勢。</span><span class="sxs-lookup"><span data-stu-id="143b2-195">The grip pose is also used when visualizing a motion controller.</span></span> <span data-ttu-id="143b2-196">Windows 為移動控制器提供的 **呈現模型** ，會使用底框姿勢作為其原點和旋轉中心。</span><span class="sxs-lookup"><span data-stu-id="143b2-196">The **renderable model** provided by Windows for a motion controller uses the grip pose as its origin and center of rotation.</span></span>

<span data-ttu-id="143b2-197">此底框姿勢的定義方式明確如下：</span><span class="sxs-lookup"><span data-stu-id="143b2-197">The grip pose is defined specifically as follows:</span></span>
* <span data-ttu-id="143b2-198">把手 **位置**：自然地按住控制器時的棕櫚距心，向左或向右調整以將位置置中置中。</span><span class="sxs-lookup"><span data-stu-id="143b2-198">The **grip position**: The palm centroid when holding the controller naturally, adjusted left or right to center the position within the grip.</span></span> <span data-ttu-id="143b2-199">在 Windows Mixed Reality 運動控制器上，此位置通常會與 [抓住] 按鈕對齊。</span><span class="sxs-lookup"><span data-stu-id="143b2-199">On the Windows Mixed Reality motion controller, this position generally aligns with the Grasp button.</span></span>
* <span data-ttu-id="143b2-200">底 **圖方向的右軸**：當您完全開啟手來形成平面的5形姿勢時，您的掌上光 (的光線會從左至右向前復原，從右邊的棕櫚) </span><span class="sxs-lookup"><span data-stu-id="143b2-200">The **grip orientation's Right axis**: When you completely open your hand to form a flat 5-finger pose, the ray that is normal to your palm (forward from left palm, backward from right palm)</span></span>
* <span data-ttu-id="143b2-201">底圖 **方向的向前軸**：當您關閉手部分 (時，如同按住控制器) 一樣，也就是由非拇指手指所形成的電子管「轉寄」的光線。</span><span class="sxs-lookup"><span data-stu-id="143b2-201">The **grip orientation's Forward axis**: When you close your hand partially (as if holding the controller), the ray that points "forward" through the tube formed by your non-thumb fingers.</span></span>
* <span data-ttu-id="143b2-202">底圖 **方向的向上軸**：右邊和向前定義所隱含的向上軸。</span><span class="sxs-lookup"><span data-stu-id="143b2-202">The **grip orientation's Up axis**: The Up axis implied by the Right and Forward definitions.</span></span>

<span data-ttu-id="143b2-203">您可以透過 Unity 的跨廠商輸入 API (XR 來存取抓住姿勢 *[。InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)。GetLocalPosition/輪替*) 或透過 WINDOWS MR 專屬 API (*SourceState. SourcePose. TryGetPosition/輪替*，要求 **) 的** 的資料。</span><span class="sxs-lookup"><span data-stu-id="143b2-203">You can access the grip pose through either Unity's cross-vendor input API (*[XR.InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html).GetLocalPosition/Rotation*) or through the Windows MR-specific API (*sourceState.sourcePose.TryGetPosition/Rotation*, requesting pose data for the **Grip** node).</span></span>

### <a name="pointer-pose"></a><span data-ttu-id="143b2-204">指標姿勢</span><span class="sxs-lookup"><span data-stu-id="143b2-204">Pointer pose</span></span>

<span data-ttu-id="143b2-205">**指標姿勢** 代表指向轉寄的控制器秘訣。</span><span class="sxs-lookup"><span data-stu-id="143b2-205">The **pointer pose** represents the tip of the controller pointing forward.</span></span>

<span data-ttu-id="143b2-206">系統提供的指標姿勢最適合用來在您 **呈現控制器模型本身** 時 raycast。</span><span class="sxs-lookup"><span data-stu-id="143b2-206">The system-provided pointer pose is best used to raycast when you're **rendering the controller model itself**.</span></span> <span data-ttu-id="143b2-207">如果您要轉譯某個其他的虛擬物件來取代控制器，例如虛擬的機槍，您應該指向該虛擬物件最自然的光線，例如沿著應用程式定義的機槍模型的圓柱移動光線。</span><span class="sxs-lookup"><span data-stu-id="143b2-207">If you're rendering some other virtual object in place of the controller, such as a virtual gun, you should point with a ray that's most natural for that virtual object, such as a ray that travels along the barrel of the app-defined gun model.</span></span> <span data-ttu-id="143b2-208">因為使用者可以看到虛擬物件，而不是實體控制器，所以指向虛擬物件可能會比使用您的應用程式更自然。</span><span class="sxs-lookup"><span data-stu-id="143b2-208">Because users can see the virtual object and not the physical controller, pointing with the virtual object will likely be more natural for those using your app.</span></span>

<span data-ttu-id="143b2-209">目前，只有透過 Windows MR 專屬 API （ *sourceState. sourcePose. TryGetPosition/旋轉*）在 Unity 中提供指標姿勢，並傳入 *InteractionSourceNode* 作為引數。</span><span class="sxs-lookup"><span data-stu-id="143b2-209">Currently, the pointer pose is available in Unity only through the Windows MR-specific API, *sourceState.sourcePose.TryGetPosition/Rotation*, passing in *InteractionSourceNode.Pointer* as the argument.</span></span>

## <a name="controller-tracking-state"></a><span data-ttu-id="143b2-210">控制器追蹤狀態</span><span class="sxs-lookup"><span data-stu-id="143b2-210">Controller tracking state</span></span>

<span data-ttu-id="143b2-211">如同耳機，Windows Mixed Reality 運動控制器不需要設定外部追蹤感應器。</span><span class="sxs-lookup"><span data-stu-id="143b2-211">Like the headsets, the Windows Mixed Reality motion controller requires no setup of external tracking sensors.</span></span> <span data-ttu-id="143b2-212">相反地，控制器是由耳機本身的感應器追蹤。</span><span class="sxs-lookup"><span data-stu-id="143b2-212">Instead, the controllers are tracked by sensors in the headset itself.</span></span>

<span data-ttu-id="143b2-213">如果使用者將控制器移出耳機的觀賞欄位，Windows 會在大部分情況下繼續推斷控制器的位置。</span><span class="sxs-lookup"><span data-stu-id="143b2-213">If the user moves the controllers out of the headset's field of view, Windows continues to infer controller positions in most cases.</span></span> <span data-ttu-id="143b2-214">如果控制器的長時間遺失視覺追蹤，控制器的位置將會降到大約精確度的位置。</span><span class="sxs-lookup"><span data-stu-id="143b2-214">When the controller has lost visual tracking for long enough, the controller's positions will drop to approximate-accuracy positions.</span></span>

<span data-ttu-id="143b2-215">此時，系統會將控制器主體鎖定給使用者，在移動時追蹤使用者的位置，同時仍會使用其內部方向感應器來公開控制器的真實方向。</span><span class="sxs-lookup"><span data-stu-id="143b2-215">At this point, the system will body-lock the controller to the user, tracking the user's position as they move around, while still exposing the controller's true orientation using its internal orientation sensors.</span></span> <span data-ttu-id="143b2-216">許多使用控制器來指向和啟動 UI 元素的應用程式，可以正常運作，而不會察覺到使用者注意。</span><span class="sxs-lookup"><span data-stu-id="143b2-216">Many apps that use controllers to point at and activate UI elements can operate normally while in approximate accuracy without the user noticing.</span></span>

<span data-ttu-id="143b2-217">若要瞭解這一點，最好的方法就是親自試試看。</span><span class="sxs-lookup"><span data-stu-id="143b2-217">The best way to get a feel for this is to try it yourself.</span></span> <span data-ttu-id="143b2-218">請觀看這段影片，其中包含可搭配各種追蹤狀態的運動控制器使用的沉浸式內容範例：</span><span class="sxs-lookup"><span data-stu-id="143b2-218">Check out this video with examples of immersive content that works with motion controllers across various tracking states:</span></span>

<br>

 >[!VIDEO https://www.youtube.com/embed/QK_fOFDHj0g]

### <a name="reasoning-about-tracking-state-explicitly"></a><span data-ttu-id="143b2-219">明確追蹤狀態的原因</span><span class="sxs-lookup"><span data-stu-id="143b2-219">Reasoning about tracking state explicitly</span></span>

<span data-ttu-id="143b2-220">希望根據追蹤狀態以不同方式來處理位置的應用程式，可能會進一步檢查控制器狀態的屬性，例如 *SourceLossRisk* 和 *PositionAccuracy*：</span><span class="sxs-lookup"><span data-stu-id="143b2-220">Apps that wish to treat positions differently based on tracking state may go further and inspect properties on the controller's state, such as *SourceLossRisk* and *PositionAccuracy*:</span></span>

<table>
<tr>
<th> <span data-ttu-id="143b2-221">追蹤狀態</span><span class="sxs-lookup"><span data-stu-id="143b2-221">Tracking state</span></span> </th><th> <span data-ttu-id="143b2-222">SourceLossRisk</span><span class="sxs-lookup"><span data-stu-id="143b2-222">SourceLossRisk</span></span> </th><th> <span data-ttu-id="143b2-223">PositionAccuracy</span><span class="sxs-lookup"><span data-stu-id="143b2-223">PositionAccuracy</span></span> </th><th> <span data-ttu-id="143b2-224">TryGetPosition</span><span class="sxs-lookup"><span data-stu-id="143b2-224">TryGetPosition</span></span></th>
</tr><tr>
<td> <span data-ttu-id="143b2-225"><b>高精確度</b> </span><span class="sxs-lookup"><span data-stu-id="143b2-225"><b>High accuracy</b> </span></span></td><td style="background-color: green; color: white"> <span data-ttu-id="143b2-226">&lt; 1.0</span><span class="sxs-lookup"><span data-stu-id="143b2-226">&lt; 1.0</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="143b2-227">高</span><span class="sxs-lookup"><span data-stu-id="143b2-227">High</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="143b2-228">true</span><span class="sxs-lookup"><span data-stu-id="143b2-228">true</span></span></td>
</tr><tr>
<td> <span data-ttu-id="143b2-229"><b>高精確度 (有遺失) 的風險 </b> </span><span class="sxs-lookup"><span data-stu-id="143b2-229"><b>High accuracy (at risk of losing)</b> </span></span></td><td style="background-color: orange"> <span data-ttu-id="143b2-230">= = 1。0</span><span class="sxs-lookup"><span data-stu-id="143b2-230">== 1.0</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="143b2-231">高</span><span class="sxs-lookup"><span data-stu-id="143b2-231">High</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="143b2-232">true</span><span class="sxs-lookup"><span data-stu-id="143b2-232">true</span></span></td>
</tr><tr>
<td> <span data-ttu-id="143b2-233"><b>近似精確度</b> </span><span class="sxs-lookup"><span data-stu-id="143b2-233"><b>Approximate accuracy</b> </span></span></td><td style="background-color: orange"> <span data-ttu-id="143b2-234">= = 1。0</span><span class="sxs-lookup"><span data-stu-id="143b2-234">== 1.0</span></span> </td><td style="background-color: orange"> <span data-ttu-id="143b2-235">大約</span><span class="sxs-lookup"><span data-stu-id="143b2-235">Approximate</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="143b2-236">true</span><span class="sxs-lookup"><span data-stu-id="143b2-236">true</span></span></td>
</tr><tr>
<td> <span data-ttu-id="143b2-237"><b>沒有位置</b> </span><span class="sxs-lookup"><span data-stu-id="143b2-237"><b>No position</b> </span></span></td><td style="background-color: orange"> <span data-ttu-id="143b2-238">= = 1。0</span><span class="sxs-lookup"><span data-stu-id="143b2-238">== 1.0</span></span> </td><td style="background-color: orange"> <span data-ttu-id="143b2-239">大約</span><span class="sxs-lookup"><span data-stu-id="143b2-239">Approximate</span></span> </td><td style="background-color: orange"> <span data-ttu-id="143b2-240">false</span><span class="sxs-lookup"><span data-stu-id="143b2-240">false</span></span></td>
</tr>
</table>

<span data-ttu-id="143b2-241">這些移動控制器追蹤狀態的定義如下：</span><span class="sxs-lookup"><span data-stu-id="143b2-241">These motion controller tracking states are defined as follows:</span></span>
* <span data-ttu-id="143b2-242">**高精確度：** 當移動控制器位於耳機的視圖範圍內時，它通常會根據視覺效果追蹤，提供高精確度的位置。</span><span class="sxs-lookup"><span data-stu-id="143b2-242">**High accuracy:** While the motion controller is within the headset's field of view, it will generally provide high-accuracy positions, based on visual tracking.</span></span> <span data-ttu-id="143b2-243">移動控制器會短暫離開視圖的欄位，或是短暫地遮蔽到耳機感應器 (例如，根據使用者的角度，) 會根據控制器本身的慣性追蹤，繼續傳回高精確度的姿勢。</span><span class="sxs-lookup"><span data-stu-id="143b2-243">A moving controller that momentarily leaves the field of view or is momentarily obscured from the headset sensors (e.g. by the user's other hand) will continue to return high-accuracy poses for a short time, based on inertial tracking of the controller itself.</span></span>
* <span data-ttu-id="143b2-244">**高精確度 (有遺失) 的風險：** 當使用者將移動控制站移出耳機視圖的邊緣之後，耳機很快就無法以視覺化方式追蹤控制器的位置。</span><span class="sxs-lookup"><span data-stu-id="143b2-244">**High accuracy (at risk of losing):** When the user moves the motion controller past the edge of the headset's field of view, the headset will soon be unable to visually track the controller's position.</span></span> <span data-ttu-id="143b2-245">應用程式知道當控制器達到此 FOV 界限時，會看到 **SourceLossRisk** 達到1.0。</span><span class="sxs-lookup"><span data-stu-id="143b2-245">The app knows when the controller has reached this FOV boundary by seeing the **SourceLossRisk** reach 1.0.</span></span> <span data-ttu-id="143b2-246">屆時，應用程式可能會選擇暫停控制器手勢，而這些手勢需要穩定的高品質串流。</span><span class="sxs-lookup"><span data-stu-id="143b2-246">At that point, the app may choose to pause controller gestures that require a steady stream of high quality poses.</span></span>
* <span data-ttu-id="143b2-247">**近似精確度：** 如果控制器的長時間遺失視覺追蹤，控制器的位置將會降到大約精確度的位置。</span><span class="sxs-lookup"><span data-stu-id="143b2-247">**Approximate accuracy:** When the controller has lost visual tracking for long enough, the controller's positions will drop to approximate-accuracy positions.</span></span> <span data-ttu-id="143b2-248">此時，系統會將控制器主體鎖定給使用者，在移動時追蹤使用者的位置，同時仍會使用其內部方向感應器來公開控制器的真實方向。</span><span class="sxs-lookup"><span data-stu-id="143b2-248">At this point, the system will body-lock the controller to the user, tracking the user's position as they move around, while still exposing the controller's true orientation using its internal orientation sensors.</span></span> <span data-ttu-id="143b2-249">許多使用控制器來指向和啟動 UI 元素的應用程式，都可以正常運作，而不會察覺到使用者的精確度。</span><span class="sxs-lookup"><span data-stu-id="143b2-249">Many apps that use controllers to point at and activate UI elements can operate as normal while in approximate accuracy without the user noticing.</span></span> <span data-ttu-id="143b2-250">具有較長輸入需求的應用程式可能會藉由檢查 **PositionAccuracy** 屬性，選擇將此下降從 **高** 精確度到 **近似** 精確度，例如，讓使用者在這段時間內更有更多的螢幕目標 hitbox。</span><span class="sxs-lookup"><span data-stu-id="143b2-250">Apps with heavier input requirements may choose to sense this drop from **High** accuracy to **Approximate** accuracy by inspecting the **PositionAccuracy** property, for example to give the user a more generous hitbox on off-screen targets during this time.</span></span>
* <span data-ttu-id="143b2-251">**沒有位置：** 雖然控制器可在很長的時間內正常運作，但有時系統會知道即使主體鎖定的位置目前沒有意義。</span><span class="sxs-lookup"><span data-stu-id="143b2-251">**No position:** While the controller can operate at approximate accuracy for a long time, sometimes the system knows that even a body-locked position isn't meaningful at the moment.</span></span> <span data-ttu-id="143b2-252">例如，已開啟的控制器可能從未以視覺化的方式觀察到，或使用者可能會放置由其他人挑選的控制器。</span><span class="sxs-lookup"><span data-stu-id="143b2-252">For example, a controller that was turned on may have never been observed visually, or a user may put down a controller that's then picked up by someone else.</span></span> <span data-ttu-id="143b2-253">在這些情況下，系統不會提供任何位置給應用程式，而 *TryGetPosition* 會傳回 false。</span><span class="sxs-lookup"><span data-stu-id="143b2-253">At those times, the system won't provide any position to the app, and *TryGetPosition* will return false.</span></span>

## <a name="common-unity-apis-inputgetbuttongetaxis"></a><span data-ttu-id="143b2-254">通用 Unity Api (輸入 GetButton/GetAxis) </span><span class="sxs-lookup"><span data-stu-id="143b2-254">Common Unity APIs (Input.GetButton/GetAxis)</span></span>

<span data-ttu-id="143b2-255">**Namespace：** *UnityEngine*， *UnityEngine. XR*</span><span class="sxs-lookup"><span data-stu-id="143b2-255">**Namespace:** *UnityEngine*, *UnityEngine.XR*</span></span><br>
<span data-ttu-id="143b2-256">**類型**： *輸入*、 *XR。InputTracking*</span><span class="sxs-lookup"><span data-stu-id="143b2-256">**Types**: *Input*, *XR.InputTracking*</span></span>

<span data-ttu-id="143b2-257">Unity 目前使用其一般 *輸入. GetButton/GetAxis* api 來公開 [Oculus SDK](https://docs.unity3d.com/Manual/OculusControllers.html)、 [OpenVR SDK](https://docs.unity3d.com/Manual/OpenVRControllers.html) 和 Windows Mixed Reality 的輸入，包括實習和移動控制器。</span><span class="sxs-lookup"><span data-stu-id="143b2-257">Unity currently uses its general *Input.GetButton/Input.GetAxis* APIs to expose input for [the Oculus SDK](https://docs.unity3d.com/Manual/OculusControllers.html), [the OpenVR SDK](https://docs.unity3d.com/Manual/OpenVRControllers.html) and Windows Mixed Reality, including hands and motion controllers.</span></span> <span data-ttu-id="143b2-258">如果您的應用程式使用這些 Api 進行輸入，則可以輕鬆地支援跨多個 XR Sdk 的移動控制器，包括 Windows Mixed Reality。</span><span class="sxs-lookup"><span data-stu-id="143b2-258">If your app uses these APIs for input, it can easily support motion controllers across multiple XR SDKs, including Windows Mixed Reality.</span></span>

### <a name="getting-a-logical-buttons-pressed-state"></a><span data-ttu-id="143b2-259">取得邏輯按鈕的按下狀態</span><span class="sxs-lookup"><span data-stu-id="143b2-259">Getting a logical button's pressed state</span></span>

<span data-ttu-id="143b2-260">若要使用一般 Unity 輸入 Api，您通常會先將按鈕和軸連結到 [Unity 輸入管理員](https://docs.unity3d.com/Manual/ConventionalGameInput.html)中的邏輯名稱，然後將按鈕或軸識別碼系結至每個名稱。</span><span class="sxs-lookup"><span data-stu-id="143b2-260">To use the general Unity input APIs, you'll typically start by wiring up buttons and axes to logical names in the [Unity Input Manager](https://docs.unity3d.com/Manual/ConventionalGameInput.html), binding a button or axis IDs to each name.</span></span> <span data-ttu-id="143b2-261">然後，您可以撰寫參考該邏輯按鈕/軸名稱的程式碼。</span><span class="sxs-lookup"><span data-stu-id="143b2-261">You can then write code that refers to that logical button/axis name.</span></span>

<span data-ttu-id="143b2-262">例如，若要將左移動控制器的 [觸發程式] 按鈕對應至 [提交] 動作，請移至 Unity 內的 [ **編輯 > 專案設定] > 輸入** ，並展開 [軸] 下的 [提交] 區段的屬性。</span><span class="sxs-lookup"><span data-stu-id="143b2-262">For example, to map the left motion controller's trigger button to the Submit action, go to **Edit > Project Settings > Input** within Unity, and expand the properties of the Submit section under Axes.</span></span> <span data-ttu-id="143b2-263">將 **正面按鈕** 或 **Alt 正按鈕** 屬性變更為讀取 **搖桿按鈕 14**，如下所示：</span><span class="sxs-lookup"><span data-stu-id="143b2-263">Change the **Positive Button** or **Alt Positive Button** property to read **joystick button 14**, like this:</span></span>

<span data-ttu-id="143b2-264">![Unity 的 InputManager](images/unity-input-manager.png)</span><span class="sxs-lookup"><span data-stu-id="143b2-264">![Unity's InputManager](images/unity-input-manager.png)</span></span><br>
<span data-ttu-id="143b2-265">*Unity InputManager*</span><span class="sxs-lookup"><span data-stu-id="143b2-265">*Unity InputManager*</span></span>

<span data-ttu-id="143b2-266">然後，您的腳本可以使用 *GetButton* 來檢查提交動作：</span><span class="sxs-lookup"><span data-stu-id="143b2-266">Your script can then check for the Submit action using *Input.GetButton*:</span></span>

```cs
if (Input.GetButton("Submit"))
{
  // ...
}
```
<span data-ttu-id="143b2-267">您可以變更 [**軸**] 下的 [**大小**] 屬性，以新增更多邏輯按鈕。</span><span class="sxs-lookup"><span data-stu-id="143b2-267">You can add more logical buttons by changing the **Size** property under **Axes**.</span></span>

### <a name="getting-a-physical-buttons-pressed-state-directly"></a><span data-ttu-id="143b2-268">直接取得實體按鈕的按下狀態</span><span class="sxs-lookup"><span data-stu-id="143b2-268">Getting a physical button's pressed state directly</span></span>

<span data-ttu-id="143b2-269">您也可以使用 *GetKey* 的完整名稱，以手動方式存取按鈕：</span><span class="sxs-lookup"><span data-stu-id="143b2-269">You can also access buttons manually by their fully qualified name, using *Input.GetKey*:</span></span>

```cs
if (Input.GetKey("joystick button 8"))
{
  // ...
}
```

### <a name="getting-a-hand-or-motion-controllers-pose"></a><span data-ttu-id="143b2-270">取得手或移動控制器的姿勢</span><span class="sxs-lookup"><span data-stu-id="143b2-270">Getting a hand or motion controller's pose</span></span>

<span data-ttu-id="143b2-271">您可以使用 XR 存取控制器的位置和旋轉 *。InputTracking*：</span><span class="sxs-lookup"><span data-stu-id="143b2-271">You can access the position and rotation of the controller, using *XR.InputTracking*:</span></span>

```cs
Vector3 leftPosition = InputTracking.GetLocalPosition(XRNode.LeftHand);
Quaternion leftRotation = InputTracking.GetLocalRotation(XRNode.LeftHand);
```

> [!NOTE] 
> <span data-ttu-id="143b2-272">上述程式碼代表控制器的底狀姿勢 (其中的使用者持有控制器) ，此控制器適用于轉譯使用者手中的寶劍或機槍，或控制器本身的模型。</span><span class="sxs-lookup"><span data-stu-id="143b2-272">The above code represents the controller's grip pose (where the user holds the controller), which is useful for rendering a sword or gun in the user's hand, or a model of the controller itself.</span></span>
> 
> <span data-ttu-id="143b2-273">此底框的關聯性和指標姿勢 (，控制器的提示會指向控制器之間的) 可能不同。</span><span class="sxs-lookup"><span data-stu-id="143b2-273">The relationship between this grip pose and the pointer pose (where the tip of the controller is pointing) may differ across controllers.</span></span> <span data-ttu-id="143b2-274">目前，只能透過 MR 專屬的輸入 API 來存取控制器的指標姿勢，如下一節所述。</span><span class="sxs-lookup"><span data-stu-id="143b2-274">At this moment, accessing the controller's pointer pose is only possible through the MR-specific input API, described in the sections below.</span></span>

## <a name="windows-specific-apis-xrwsainput"></a><span data-ttu-id="143b2-275">Windows 特定 Api (XR。Wsa。輸入) </span><span class="sxs-lookup"><span data-stu-id="143b2-275">Windows-specific APIs (XR.WSA.Input)</span></span>

> [!CAUTION]
> <span data-ttu-id="143b2-276">如果您的專案使用任何 XR。WSA Api 在未來的 Unity 版本中，將會以 XR SDK 的方式來淘汰這些 Api。</span><span class="sxs-lookup"><span data-stu-id="143b2-276">If your project is using any of the XR.WSA APIs, these are being phased out in favor of the XR SDK in future Unity releases.</span></span> <span data-ttu-id="143b2-277">針對新的專案，我們建議您從一開始就使用 XR SDK。</span><span class="sxs-lookup"><span data-stu-id="143b2-277">For new projects, we recommend using the XR SDK from the beginning.</span></span> <span data-ttu-id="143b2-278">您可以在 [這裡找到 XR 輸入系統和 api](https://docs.unity3d.com/Manual/xr_input.html)的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="143b2-278">You can find more information about the [XR Input system and APIs here](https://docs.unity3d.com/Manual/xr_input.html).</span></span>

<span data-ttu-id="143b2-279">**命名空間：** *UnityEngine. XR。輸入*</span><span class="sxs-lookup"><span data-stu-id="143b2-279">**Namespace:** *UnityEngine.XR.WSA.Input*</span></span><br>
<span data-ttu-id="143b2-280">**類型**： *InteractionManager*、 *InteractionSourceState*、 *InteractionSource*、 *InteractionSourceProperties*、 *InteractionSourceKind*、 *InteractionSourceLocation*</span><span class="sxs-lookup"><span data-stu-id="143b2-280">**Types**: *InteractionManager*, *InteractionSourceState*, *InteractionSource*, *InteractionSourceProperties*, *InteractionSourceKind*, *InteractionSourceLocation*</span></span>

<span data-ttu-id="143b2-281">若要取得 HoloLens) 和移動控制器的 Windows Mixed Reality 手輸入 (的詳細資訊，您可以選擇使用 *UnityEngine. XR* 底下的 Windows 特定空間輸入 api。</span><span class="sxs-lookup"><span data-stu-id="143b2-281">To get at more detailed information about Windows Mixed Reality hand input (for HoloLens) and motion controllers, you can choose to use the Windows-specific spatial input APIs under the *UnityEngine.XR.WSA.Input* namespace.</span></span> <span data-ttu-id="143b2-282">這可讓您存取額外的資訊，例如位置精確度或來源種類，讓您可以分辨手和控制器。</span><span class="sxs-lookup"><span data-stu-id="143b2-282">This lets you access additional information, such as position accuracy or the source kind, letting you tell hands and controllers apart.</span></span>

### <a name="polling-for-the-state-of-hands-and-motion-controllers"></a><span data-ttu-id="143b2-283">輪詢實習和移動控制器的狀態</span><span class="sxs-lookup"><span data-stu-id="143b2-283">Polling for the state of hands and motion controllers</span></span>

<span data-ttu-id="143b2-284">您可以使用 *GetCurrentReading* 方法，輪詢每個互動來源 (手或移動控制器) 的此畫面格狀態。</span><span class="sxs-lookup"><span data-stu-id="143b2-284">You can poll for this frame's state for each interaction source (hand or motion controller) using the *GetCurrentReading* method.</span></span>

```cs
var interactionSourceStates = InteractionManager.GetCurrentReading();
foreach (var interactionSourceState in interactionSourceStates) {
    // ...
}
```

<span data-ttu-id="143b2-285">您取回的每個 *InteractionSourceState* 都代表目前時間的互動來源。</span><span class="sxs-lookup"><span data-stu-id="143b2-285">Each *InteractionSourceState* you get back represents an interaction source at the current moment in time.</span></span> <span data-ttu-id="143b2-286">*InteractionSourceState* 會公開如下的資訊：</span><span class="sxs-lookup"><span data-stu-id="143b2-286">The *InteractionSourceState* exposes info such as:</span></span>
* <span data-ttu-id="143b2-287"> (選取/功能表/抓住/觸控板/操縱杆) 會發生何[種類型的按鍵](../../design/motion-controllers.md)</span><span class="sxs-lookup"><span data-stu-id="143b2-287">Which [kinds of presses](../../design/motion-controllers.md) are occurring (Select/Menu/Grasp/Touchpad/Thumbstick)</span></span>

   ```cs
   if (interactionSourceState.selectPressed) {
       // ...
   }
   ```
* <span data-ttu-id="143b2-288">動作控制器特定的其他資料，例如觸控板和/或操縱杆的 XY 座標和觸及的狀態</span><span class="sxs-lookup"><span data-stu-id="143b2-288">Other data specific to motion controllers, such the touchpad and/or thumbstick's XY coordinates and touched state</span></span>

   ```cs
   if (interactionSourceState.touchpadTouched && interactionSourceState.touchpadPosition.x > 0.5) {
       // ...
   }
   ```

* <span data-ttu-id="143b2-289">InteractionSourceKind，以瞭解來源是手或移動控制器</span><span class="sxs-lookup"><span data-stu-id="143b2-289">The InteractionSourceKind to know if the source is a hand or a motion controller</span></span>

   ```cs
   if (interactionSourceState.source.kind == InteractionSourceKind.Hand) {
       // ...
   }
   ```

### <a name="polling-for-forward-predicted-rendering-poses"></a><span data-ttu-id="143b2-290">輪詢向前預測呈現的姿勢</span><span class="sxs-lookup"><span data-stu-id="143b2-290">Polling for forward-predicted rendering poses</span></span>

* <span data-ttu-id="143b2-291">當您輪詢來自手和控制器的互動來源資料時，您所得到的是向前預測的原因，是在此框架的光子到達使用者眼時的時間點。</span><span class="sxs-lookup"><span data-stu-id="143b2-291">When polling for interaction source data from hands and controllers, the poses you get are forward-predicted poses for the moment in time when this frame's photons will reach the user's eyes.</span></span>  <span data-ttu-id="143b2-292">向前預測的姿勢最適合 **用來轉譯** 控制器或每個畫面格的保留物件。</span><span class="sxs-lookup"><span data-stu-id="143b2-292">Forward-predicted poses are best used for **rendering** the controller or a held object each frame.</span></span>  <span data-ttu-id="143b2-293">如果您的目標是使用控制器指定的按下或放開，如果您使用如下所述的歷程記錄事件 Api，這將會是最精確的。</span><span class="sxs-lookup"><span data-stu-id="143b2-293">If you're targeting a given press or release with the controller, that will be most accurate if you use the historical event APIs described below.</span></span>

   ```cs
   var sourcePose = interactionSourceState.sourcePose;
   Vector3 sourceGripPosition;
   Quaternion sourceGripRotation;
   if ((sourcePose.TryGetPosition(out sourceGripPosition, InteractionSourceNode.Grip)) &&
       (sourcePose.TryGetRotation(out sourceGripRotation, InteractionSourceNode.Grip))) {
       // ...
   }
   ```

* <span data-ttu-id="143b2-294">您也可以取得這個目前畫面格的向前預測標頭姿勢。</span><span class="sxs-lookup"><span data-stu-id="143b2-294">You can also get the forward-predicted head pose for this current frame.</span></span>  <span data-ttu-id="143b2-295">如同來源的原因，如果您使用如下所 **述的歷程** 記錄事件 api，則在轉譯資料指標時，這會很有用。</span><span class="sxs-lookup"><span data-stu-id="143b2-295">As with the source pose, this is useful for **rendering** a cursor, although targeting a given press or release will be most accurate if you use the historical event APIs described below.</span></span>

   ```cs
   var headPose = interactionSourceState.headPose;
   var headRay = new Ray(headPose.position, headPose.forward);
   RaycastHit raycastHit;
   if (Physics.Raycast(headPose.position, headPose.forward, out raycastHit, 10)) {
       var cursorPos = raycastHit.point;
       // ...
   }
   ```

### <a name="handling-interaction-source-events"></a><span data-ttu-id="143b2-296">處理互動來源事件</span><span class="sxs-lookup"><span data-stu-id="143b2-296">Handling interaction source events</span></span>

<span data-ttu-id="143b2-297">若要在輸入事件發生時處理其正確的歷程記錄資料，您可以處理互動來源事件，而不是輪詢。</span><span class="sxs-lookup"><span data-stu-id="143b2-297">To handle input events as they happen with their accurate historical pose data, you can handle interaction source events instead of polling.</span></span>

<span data-ttu-id="143b2-298">若要處理互動來源事件：</span><span class="sxs-lookup"><span data-stu-id="143b2-298">To handle interaction source events:</span></span>
* <span data-ttu-id="143b2-299">註冊 *InteractionManager* 輸入事件。</span><span class="sxs-lookup"><span data-stu-id="143b2-299">Register for a *InteractionManager* input event.</span></span> <span data-ttu-id="143b2-300">針對每個您感興趣的互動事件種類，您必須訂閱該事件。</span><span class="sxs-lookup"><span data-stu-id="143b2-300">For each type of interaction event that you are interested in, you need to subscribe to it.</span></span>

   ```cs
   InteractionManager.InteractionSourcePressed += InteractionManager_InteractionSourcePressed;
   ```

* <span data-ttu-id="143b2-301">處理事件。</span><span class="sxs-lookup"><span data-stu-id="143b2-301">Handle the event.</span></span> <span data-ttu-id="143b2-302">當您訂閱了互動事件之後，就會在適當的情況下取得回呼。</span><span class="sxs-lookup"><span data-stu-id="143b2-302">Once you have subscribed to an interaction event, you will get the callback when appropriate.</span></span> <span data-ttu-id="143b2-303">在 *SourcePressed* 範例中，這會在偵測到來源之後，且在釋放或遺失之前。</span><span class="sxs-lookup"><span data-stu-id="143b2-303">In the *SourcePressed* example, this will be after the source was detected and before it is released or lost.</span></span>

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

### <a name="how-to-stop-handling-an-event"></a><span data-ttu-id="143b2-304">如何停止處理事件</span><span class="sxs-lookup"><span data-stu-id="143b2-304">How to stop handling an event</span></span>

<span data-ttu-id="143b2-305">當您對事件不再感興趣，或您正在終結已訂閱事件的物件時，您必須停止處理事件。</span><span class="sxs-lookup"><span data-stu-id="143b2-305">You need to stop handling an event when you're no longer interested in the event or you're destroying the object that has subscribed to the event.</span></span> <span data-ttu-id="143b2-306">若要停止處理事件，您可以取消訂閱事件。</span><span class="sxs-lookup"><span data-stu-id="143b2-306">To stop handling the event, you unsubscribe from the event.</span></span>

```cs
InteractionManager.InteractionSourcePressed -= InteractionManager_InteractionSourcePressed;
```

### <a name="list-of-interaction-source-events"></a><span data-ttu-id="143b2-307">互動來源事件的清單</span><span class="sxs-lookup"><span data-stu-id="143b2-307">List of interaction source events</span></span>

<span data-ttu-id="143b2-308">可用的互動來源事件如下：</span><span class="sxs-lookup"><span data-stu-id="143b2-308">The available interaction source events are:</span></span>
* <span data-ttu-id="143b2-309">*InteractionSourceDetected* (來源會變成作用中) </span><span class="sxs-lookup"><span data-stu-id="143b2-309">*InteractionSourceDetected* (source becomes active)</span></span>
* <span data-ttu-id="143b2-310">*InteractionSourceLost* (變成非使用中) </span><span class="sxs-lookup"><span data-stu-id="143b2-310">*InteractionSourceLost* (becomes inactive)</span></span>
* <span data-ttu-id="143b2-311">*InteractionSourcePressed* (點擊、按下按鈕或「選取」從未提到) </span><span class="sxs-lookup"><span data-stu-id="143b2-311">*InteractionSourcePressed* (tap, button press, or "Select" uttered)</span></span>
* <span data-ttu-id="143b2-312">*InteractionSourceReleased* (結束、放開按鈕或 "Select" 從未提到結尾) </span><span class="sxs-lookup"><span data-stu-id="143b2-312">*InteractionSourceReleased* (end of a tap, button released, or end of "Select" uttered)</span></span>
* <span data-ttu-id="143b2-313">*InteractionSourceUpdated* (會移動或以其他方式變更某些狀態) </span><span class="sxs-lookup"><span data-stu-id="143b2-313">*InteractionSourceUpdated* (moves or otherwise changes some state)</span></span>

### <a name="events-for-historical-targeting-poses-that-most-accurately-match-a-press-or-release"></a><span data-ttu-id="143b2-314">歷程記錄目標的事件，最精確地符合電子報或發行</span><span class="sxs-lookup"><span data-stu-id="143b2-314">Events for historical targeting poses that most accurately match a press or release</span></span>

<span data-ttu-id="143b2-315">稍早所述的輪詢 Api 會讓您的應用程式向前預測的姿勢。</span><span class="sxs-lookup"><span data-stu-id="143b2-315">The polling APIs described earlier give your app forward-predicted poses.</span></span>  <span data-ttu-id="143b2-316">雖然這些預測的姿勢最適合用來呈現控制器或虛擬掌上型物件，但未來的原因不是最佳的目標，原因有兩個：</span><span class="sxs-lookup"><span data-stu-id="143b2-316">While those predicted poses are best for rendering the controller or a virtual handheld object, future poses aren't optimal for targeting, for two key reasons:</span></span>
* <span data-ttu-id="143b2-317">當使用者按下控制器上的按鈕時，可能會有大約20毫秒的無線延遲超過藍牙，系統才會收到按下的動作。</span><span class="sxs-lookup"><span data-stu-id="143b2-317">When the user presses a button on a controller, there can be about 20 ms of wireless latency over Bluetooth before the system receives the press.</span></span>
* <span data-ttu-id="143b2-318">然後，如果您使用向前預測的姿勢，則會有另一個10-20 毫秒的向前預測套用到目標，也就是目前框架的光子到達使用者眼睛的時間。</span><span class="sxs-lookup"><span data-stu-id="143b2-318">Then, if you're using a forward-predicted pose, there would be another 10-20 ms of forward prediction applied to target the time when the current frame's photons will reach the user's eyes.</span></span>

<span data-ttu-id="143b2-319">這表示輪詢會提供來源姿勢或 head 的原因，從使用者的標頭開始，到按下或放開時，都30-40 是從使用者的標頭開始。</span><span class="sxs-lookup"><span data-stu-id="143b2-319">This means that polling gives you a source pose or head pose that is 30-40 ms forward from where the user's head and hands actually were back when the press or release happened.</span></span>  <span data-ttu-id="143b2-320">針對 HoloLens 手輸入，雖然沒有無線傳輸延遲，但偵測到按下的處理延遲也很類似。</span><span class="sxs-lookup"><span data-stu-id="143b2-320">For HoloLens hand input, while there's no wireless transmission delay, there's a similar processing delay to detect the press.</span></span>

<span data-ttu-id="143b2-321">若要根據使用者的原始意圖來精確地鎖定目標，請按下該 *InteractionSourcePressed* 或 *InteractionSourceReleased* 輸入事件的歷程記錄來源姿勢或 head 姿勢。</span><span class="sxs-lookup"><span data-stu-id="143b2-321">To accurately target based on the user's original intent for a hand or controller press, you should use the historical source pose or head pose from that *InteractionSourcePressed* or *InteractionSourceReleased* input event.</span></span>

<span data-ttu-id="143b2-322">您可以使用來自使用者前端或其控制器的歷程記錄資料，來進行按下或釋放的目標：</span><span class="sxs-lookup"><span data-stu-id="143b2-322">You can target a press or release with historical pose data from the user's head or their controller:</span></span>
* <span data-ttu-id="143b2-323">當軌跡或控制器按下的時間點時，可能會用來做為 **目標** ，以判斷使用者的 [撥雲見日](../../design/gaze-and-commit.md) ：</span><span class="sxs-lookup"><span data-stu-id="143b2-323">The head pose at the moment in time when a gesture or controller press occurred, which can be used for **targeting** to determine what the user was [gazing](../../design/gaze-and-commit.md) at:</span></span>

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

* <span data-ttu-id="143b2-324">來源會在移動控制器按下的時間點發生，這可用於 **目標** ，以判斷使用者在何處指向控制器。</span><span class="sxs-lookup"><span data-stu-id="143b2-324">The source pose at the moment in time when a motion controller press occurred, which can be used for **targeting** to determine what the user was pointing the controller at.</span></span>  <span data-ttu-id="143b2-325">這會是遇到按下之控制器的狀態。</span><span class="sxs-lookup"><span data-stu-id="143b2-325">This will be the state of the controller that experienced the press.</span></span>  <span data-ttu-id="143b2-326">如果您要轉譯控制器本身，您可以要求指標姿勢，而不是把手姿勢，以將目標光線從使用者考慮到該轉譯控制器的自然秘訣：</span><span class="sxs-lookup"><span data-stu-id="143b2-326">If you're rendering the controller itself, you can request the pointer pose rather than the grip pose, to shoot the targeting ray from what the user will consider the natural tip of that rendered controller:</span></span>

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

### <a name="event-handlers-example"></a><span data-ttu-id="143b2-327">事件處理常式範例</span><span class="sxs-lookup"><span data-stu-id="143b2-327">Event handlers example</span></span>

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

## <a name="motion-controllers-in-mrtk-v2"></a><span data-ttu-id="143b2-328">MRTK v2 中的動作控制器</span><span class="sxs-lookup"><span data-stu-id="143b2-328">Motion Controllers in MRTK v2</span></span>

<span data-ttu-id="143b2-329">您可以從輸入管理員存取 [手勢和移動控制器](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Controllers.html) 。</span><span class="sxs-lookup"><span data-stu-id="143b2-329">You can access [gesture and motion controller](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Controllers.html) from the input Manager.</span></span>

## <a name="follow-along-with-tutorials"></a><span data-ttu-id="143b2-330">遵循教學課程</span><span class="sxs-lookup"><span data-stu-id="143b2-330">Follow along with tutorials</span></span>

<span data-ttu-id="143b2-331">混合現實學術中提供逐步教學課程，包含更詳細的自訂範例：</span><span class="sxs-lookup"><span data-stu-id="143b2-331">Step-by-step tutorials, with more detailed customization examples, are available in the Mixed Reality Academy:</span></span>

- [<span data-ttu-id="143b2-332">MR Input 211：筆勢</span><span class="sxs-lookup"><span data-stu-id="143b2-332">MR Input 211: Gesture</span></span>](tutorials/holograms-211.md)
- [<span data-ttu-id="143b2-333">MR Input 213：運動控制器</span><span class="sxs-lookup"><span data-stu-id="143b2-333">MR Input 213: Motion controllers</span></span>](../../deprecated/mixed-reality-213.md)

<span data-ttu-id="143b2-334">[![MR 輸入 213-移動控制器](images/mr213-main-600px.jpg)](https://docs.microsoft.com/windows/mixed-reality/mixed-reality-213)</span><span class="sxs-lookup"><span data-stu-id="143b2-334">[![MR Input 213 - Motion controller](images/mr213-main-600px.jpg)](https://docs.microsoft.com/windows/mixed-reality/mixed-reality-213)</span></span><br>
<span data-ttu-id="143b2-335">*MR 輸入 213-移動控制器*</span><span class="sxs-lookup"><span data-stu-id="143b2-335">*MR Input 213 - Motion controller*</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="143b2-336">下一個開發檢查點</span><span class="sxs-lookup"><span data-stu-id="143b2-336">Next Development Checkpoint</span></span>

<span data-ttu-id="143b2-337">如果您是遵循我們所配置的 Unity 開發旅程，您將會在探索 MRTK 核心構成要素的過程中進行。</span><span class="sxs-lookup"><span data-stu-id="143b2-337">If you're following the Unity development journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="143b2-338">接下來，您可以繼續進行下一個建置組塊：</span><span class="sxs-lookup"><span data-stu-id="143b2-338">From here, you can continue to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="143b2-339">手部和眼睛追蹤</span><span class="sxs-lookup"><span data-stu-id="143b2-339">Hand and eye tracking</span></span>](hand-eye-in-unit.md)

<span data-ttu-id="143b2-340">或者，直接跳到混合實境平台功能和 API 的主題：</span><span class="sxs-lookup"><span data-stu-id="143b2-340">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="143b2-341">共用體驗</span><span class="sxs-lookup"><span data-stu-id="143b2-341">Shared experiences</span></span>](shared-experiences-in-unity.md)

<span data-ttu-id="143b2-342">您可以隨時回到 [Unity 開發檢查點](unity-development-overview.md#2-core-building-blocks)。</span><span class="sxs-lookup"><span data-stu-id="143b2-342">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="143b2-343">另請參閱</span><span class="sxs-lookup"><span data-stu-id="143b2-343">See also</span></span>

* [<span data-ttu-id="143b2-344">頭部目光和行動</span><span class="sxs-lookup"><span data-stu-id="143b2-344">Head-gaze and commit</span></span>](../../design/gaze-and-commit.md)
* [<span data-ttu-id="143b2-345">運動控制器</span><span class="sxs-lookup"><span data-stu-id="143b2-345">Motion controllers</span></span>](../../design/motion-controllers.md)
