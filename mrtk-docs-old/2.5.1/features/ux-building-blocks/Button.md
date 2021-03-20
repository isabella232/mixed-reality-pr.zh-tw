---
title: Butons
description: MRTK 中的按鈕總覽
author: cre8ivepark
ms.author: dongpark
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、MRTK 按鈕
ms.openlocfilehash: a3e639c02258fbdd4eab1f72d71256a4bf220091
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104691475"
---
# <a name="button"></a><span data-ttu-id="d1eff-104">按鈕</span><span class="sxs-lookup"><span data-stu-id="d1eff-104">Button</span></span>

![按鈕主要](../images/button/MRTK_Button_Main.png)

<span data-ttu-id="d1eff-106">按鈕讓使用者得以觸發立即動作。</span><span class="sxs-lookup"><span data-stu-id="d1eff-106">A button gives the user a way to trigger an immediate action.</span></span> <span data-ttu-id="d1eff-107">它是混合現實中最基本的元件之一。</span><span class="sxs-lookup"><span data-stu-id="d1eff-107">It is one of the most foundational components in mixed reality.</span></span> <span data-ttu-id="d1eff-108">MRTK 提供各種類型的按鈕 prefabs。</span><span class="sxs-lookup"><span data-stu-id="d1eff-108">MRTK provides various types of button prefabs.</span></span>

## <a name="button-prefabs-in-mrtk"></a><span data-ttu-id="d1eff-109">MRTK 中的按鈕 prefabs</span><span class="sxs-lookup"><span data-stu-id="d1eff-109">Button prefabs in MRTK</span></span>

<span data-ttu-id="d1eff-110">[資料夾] 下的按鈕 prefabs 範例 ``MRTK/SDK/Features/UX/Interactable/Prefabs``</span><span class="sxs-lookup"><span data-stu-id="d1eff-110">Examples of the button prefabs under ``MRTK/SDK/Features/UX/Interactable/Prefabs`` folder</span></span>

### <a name="unity-ui-imagegraphic-based-buttons"></a><span data-ttu-id="d1eff-111">Unity UI 影像/以圖形為基礎的按鈕</span><span class="sxs-lookup"><span data-stu-id="d1eff-111">Unity UI Image/Graphic based buttons</span></span>

* `UnityUIInteractableButton.prefab`
* `PressableButtonUnityUI.prefab`
* `PressableButtonUnityUICircular.prefab`
* `PressableButtonHoloLens2UnityUI.prefab`

### <a name="collider-based-buttons"></a><span data-ttu-id="d1eff-112">以碰撞式為基礎的按鈕</span><span class="sxs-lookup"><span data-stu-id="d1eff-112">Collider based buttons</span></span>

|  ![PressableButtonHoloLens2](../images/button/MRTK_Button_Prefabs_HoloLens2.png) <span data-ttu-id="d1eff-114">PressableButtonHoloLens2</span><span class="sxs-lookup"><span data-stu-id="d1eff-114">PressableButtonHoloLens2</span></span> | ![PressableButtonHoloLens2Unplated](../images/button/MRTK_Button_Prefabs_HoloLens2Unplated.png) <span data-ttu-id="d1eff-116">PressableButtonHoloLens2Unplated</span><span class="sxs-lookup"><span data-stu-id="d1eff-116">PressableButtonHoloLens2Unplated</span></span> | ![PressableButtonHoloLens2Circular](../images/button/MRTK_Button_Prefabs_HoloLens2Circular.png) <span data-ttu-id="d1eff-118">PressableButtonHoloLens2Circular</span><span class="sxs-lookup"><span data-stu-id="d1eff-118">PressableButtonHoloLens2Circular</span></span> |
|:--- | :--- | :--- |
| <span data-ttu-id="d1eff-119">HoloLens 2 的 shell 樣式按鈕，其 backplate 支援各種視覺效果的意見反應，例如框線燈、相近光源和壓縮的 front 盤子</span><span class="sxs-lookup"><span data-stu-id="d1eff-119">HoloLens 2's shell-style button with backplate which supports various visual feedback such as border light, proximity light, and compressed front plate</span></span> | <span data-ttu-id="d1eff-120">不含 backplate 的 HoloLens 2 shell 樣式按鈕</span><span class="sxs-lookup"><span data-stu-id="d1eff-120">HoloLens 2's shell-style button without backplate</span></span>  | <span data-ttu-id="d1eff-121">具有圓形圖形 HoloLens 2 的 shell 樣式按鈕</span><span class="sxs-lookup"><span data-stu-id="d1eff-121">HoloLens 2's shell-style button with circular shape</span></span>  |
|  <span data-ttu-id="d1eff-122">![PressableButtonHoloLens2_32x96 ](../images/button/MRTK_Button_Prefabs_HoloLens2_32x96.png) **PressableButtonHoloLens2_32x96**</span><span class="sxs-lookup"><span data-stu-id="d1eff-122">![PressableButtonHoloLens2_32x96](../images/button/MRTK_Button_Prefabs_HoloLens2_32x96.png) **PressableButtonHoloLens2_32x96**</span></span> | <span data-ttu-id="d1eff-123">![PressableButtonHoloLens2Bar3H ](../images/button/MRTK_Button_Prefabs_HoloLens2BarH.png) **PressableButtonHoloLens2Bar3H**</span><span class="sxs-lookup"><span data-stu-id="d1eff-123">![PressableButtonHoloLens2Bar3H](../images/button/MRTK_Button_Prefabs_HoloLens2BarH.png) **PressableButtonHoloLens2Bar3H**</span></span> | <span data-ttu-id="d1eff-124">![PressableButtonHoloLens2Bar3V ](../images/button/MRTK_Button_Prefabs_HoloLens2BarV.png) **PressableButtonHoloLens2Bar3V**</span><span class="sxs-lookup"><span data-stu-id="d1eff-124">![PressableButtonHoloLens2Bar3V](../images/button/MRTK_Button_Prefabs_HoloLens2BarV.png) **PressableButtonHoloLens2Bar3V**</span></span> |
| <span data-ttu-id="d1eff-125">寬 HoloLens 2 的 shell 樣式按鈕32x96mm</span><span class="sxs-lookup"><span data-stu-id="d1eff-125">Wide HoloLens 2's shell-style button 32x96mm</span></span> | <span data-ttu-id="d1eff-126">具有共用 backplate 的水準 HoloLens 2 按鈕列</span><span class="sxs-lookup"><span data-stu-id="d1eff-126">Horizontal HoloLens 2 button bar with shared backplate</span></span> | <span data-ttu-id="d1eff-127">具有共用 backplate 的垂直 HoloLens 2 按鈕列</span><span class="sxs-lookup"><span data-stu-id="d1eff-127">Vertical HoloLens 2 button bar with shared backplate</span></span> |
|  <span data-ttu-id="d1eff-128">![PressableButtonHoloLens2ToggleCheckBox_32x32 ](../images/button/MRTK_Button_Prefabs_HoloLens2_Checkbox.png) **PressableButtonHoloLens2ToggleCheckBox_32x32**</span><span class="sxs-lookup"><span data-stu-id="d1eff-128">![PressableButtonHoloLens2ToggleCheckBox_32x32](../images/button/MRTK_Button_Prefabs_HoloLens2_Checkbox.png) **PressableButtonHoloLens2ToggleCheckBox_32x32**</span></span> | <span data-ttu-id="d1eff-129">![PressableButtonHoloLens2ToggleSwitch_32x32 ](../images/button/MRTK_Button_Prefabs_HoloLens2_Switch.png) **PressableButtonHoloLens2ToggleSwitch_32x32**</span><span class="sxs-lookup"><span data-stu-id="d1eff-129">![PressableButtonHoloLens2ToggleSwitch_32x32](../images/button/MRTK_Button_Prefabs_HoloLens2_Switch.png) **PressableButtonHoloLens2ToggleSwitch_32x32**</span></span> | <span data-ttu-id="d1eff-130">![PressableButtonHoloLens2ToggleRadio_32x32 ](../images/button/MRTK_Button_Prefabs_HoloLens2_Radio.png) **PressableButtonHoloLens2ToggleRadio_32x32**</span><span class="sxs-lookup"><span data-stu-id="d1eff-130">![PressableButtonHoloLens2ToggleRadio_32x32](../images/button/MRTK_Button_Prefabs_HoloLens2_Radio.png) **PressableButtonHoloLens2ToggleRadio_32x32**</span></span> |
| <span data-ttu-id="d1eff-131">HoloLens 2 的 shell 樣式核取方塊32x32mm</span><span class="sxs-lookup"><span data-stu-id="d1eff-131">HoloLens 2's shell-style checkbox 32x32mm</span></span> | <span data-ttu-id="d1eff-132">HoloLens 2 的 shell 樣式參數32x32mm</span><span class="sxs-lookup"><span data-stu-id="d1eff-132">HoloLens 2's shell-style switch 32x32mm</span></span> | <span data-ttu-id="d1eff-133">HoloLens 2 的 shell 樣式選項按鈕32x32mm</span><span class="sxs-lookup"><span data-stu-id="d1eff-133">HoloLens 2's shell-style radio 32x32mm</span></span> |
|  <span data-ttu-id="d1eff-134">![PressableButtonHoloLens2ToggleCheckBox_32x96 ](../images/button/MRTK_Button_Prefabs_HoloLens2_Checkbox_32x96.png) **PressableButtonHoloLens2ToggleCheckBox_32x96**</span><span class="sxs-lookup"><span data-stu-id="d1eff-134">![PressableButtonHoloLens2ToggleCheckBox_32x96](../images/button/MRTK_Button_Prefabs_HoloLens2_Checkbox_32x96.png) **PressableButtonHoloLens2ToggleCheckBox_32x96**</span></span> | <span data-ttu-id="d1eff-135">![PressableButtonHoloLens2ToggleSwitch_32x96 ](../images/button/MRTK_Button_Prefabs_HoloLens2_Switch_32x96.png) **PressableButtonHoloLens2ToggleSwitch_32x96**</span><span class="sxs-lookup"><span data-stu-id="d1eff-135">![PressableButtonHoloLens2ToggleSwitch_32x96](../images/button/MRTK_Button_Prefabs_HoloLens2_Switch_32x96.png) **PressableButtonHoloLens2ToggleSwitch_32x96**</span></span> | <span data-ttu-id="d1eff-136">![PressableButtonHoloLens2ToggleRadio_32x96 ](../images/button/MRTK_Button_Prefabs_HoloLens2_Radio_32x96.png) **PressableButtonHoloLens2ToggleRadio_32x96**</span><span class="sxs-lookup"><span data-stu-id="d1eff-136">![PressableButtonHoloLens2ToggleRadio_32x96](../images/button/MRTK_Button_Prefabs_HoloLens2_Radio_32x96.png) **PressableButtonHoloLens2ToggleRadio_32x96**</span></span> |
| <span data-ttu-id="d1eff-137">HoloLens 2 的 shell 樣式核取方塊32x96mm</span><span class="sxs-lookup"><span data-stu-id="d1eff-137">HoloLens 2's shell-style checkbox 32x96mm</span></span> | <span data-ttu-id="d1eff-138">HoloLens 2 的 shell 樣式參數32x96mm</span><span class="sxs-lookup"><span data-stu-id="d1eff-138">HoloLens 2's shell-style switch 32x96mm</span></span> | <span data-ttu-id="d1eff-139">HoloLens 2 的 shell 樣式選項按鈕32x96mm</span><span class="sxs-lookup"><span data-stu-id="d1eff-139">HoloLens 2's shell-style radio 32x96mm</span></span> |
|  <span data-ttu-id="d1eff-140">![星形 ](../images/button/MRTK_Button_Radial.png) **放射狀**</span><span class="sxs-lookup"><span data-stu-id="d1eff-140">![Radial](../images/button/MRTK_Button_Radial.png) **Radial**</span></span> | <span data-ttu-id="d1eff-141">![核取方塊](../images/button/MRTK_Button_Checkbox.png) **核取方塊**</span><span class="sxs-lookup"><span data-stu-id="d1eff-141">![Checkbox](../images/button/MRTK_Button_Checkbox.png) **Checkbox**</span></span> | <span data-ttu-id="d1eff-142">![ToggleSwitch ](../images/button/MRTK_Button_ToggleSwitch.png) **ToggleSwitch**</span><span class="sxs-lookup"><span data-stu-id="d1eff-142">![ToggleSwitch](../images/button/MRTK_Button_ToggleSwitch.png) **ToggleSwitch**</span></span> |
| <span data-ttu-id="d1eff-143">放射狀按鈕</span><span class="sxs-lookup"><span data-stu-id="d1eff-143">Radial button</span></span> | <span data-ttu-id="d1eff-144">核取方塊</span><span class="sxs-lookup"><span data-stu-id="d1eff-144">Checkbox</span></span>  | <span data-ttu-id="d1eff-145">切換開關</span><span class="sxs-lookup"><span data-stu-id="d1eff-145">Toggle switch</span></span> |
|  <span data-ttu-id="d1eff-146">![ButtonHoloLens1 ](../images/button/MRTK_Button_HoloLens1.png) **ButtonHoloLens1**</span><span class="sxs-lookup"><span data-stu-id="d1eff-146">![ButtonHoloLens1](../images/button/MRTK_Button_HoloLens1.png) **ButtonHoloLens1**</span></span> | <span data-ttu-id="d1eff-147">![PressableRoundButton ](../images/button/MRTK_Button_Round.png) **PressableRoundButton**</span><span class="sxs-lookup"><span data-stu-id="d1eff-147">![PressableRoundButton](../images/button/MRTK_Button_Round.png) **PressableRoundButton**</span></span> | <span data-ttu-id="d1eff-148">![按鈕基底 ](../images/button/MRTK_Button_Base.png) **按鈕**</span><span class="sxs-lookup"><span data-stu-id="d1eff-148">![Button base](../images/button/MRTK_Button_Base.png) **Button**</span></span> |
| <span data-ttu-id="d1eff-149">HoloLens 1 gen 的 shell 樣式按鈕</span><span class="sxs-lookup"><span data-stu-id="d1eff-149">HoloLens 1st gen's shell style button</span></span> | <span data-ttu-id="d1eff-150">圓形形狀推播按鈕</span><span class="sxs-lookup"><span data-stu-id="d1eff-150">Round shape push button</span></span> | <span data-ttu-id="d1eff-151">基本按鈕</span><span class="sxs-lookup"><span data-stu-id="d1eff-151">Basic button</span></span> |

<span data-ttu-id="d1eff-152">`Button` (的資產/MRTK/SDK/Features/UX/互動/Prefabs/預製專案) 是以[互動](Interactable.md)概念為基礎，可為按鈕或其他類型的互動表面提供簡單的 UI 控制項。</span><span class="sxs-lookup"><span data-stu-id="d1eff-152">The `Button` (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/Button.prefab) is based on the [Interactable](Interactable.md) concept to provide easy UI controls for buttons or other types of interactive surfaces.</span></span> <span data-ttu-id="d1eff-153">[基準] 按鈕支援所有可用的輸入方法，包括用於近距離互動的已表達手輸入，以及最遠互動的注視 + 無線電波。</span><span class="sxs-lookup"><span data-stu-id="d1eff-153">The baseline button supports all available input methods, including articulated hand input for the near interactions as well as gaze + air-tap for the far interactions.</span></span> <span data-ttu-id="d1eff-154">您也可以使用語音命令來觸發按鈕。</span><span class="sxs-lookup"><span data-stu-id="d1eff-154">You can also use voice command to trigger the button.</span></span>

<span data-ttu-id="d1eff-155">`PressableButtonHoloLens2` (資產/MRTK/SDK/Features/UX/互動/Prefabs/PressableButtonHoloLens2. 預製專案) 是 HoloLens 2 的 shell 樣式按鈕，可支援直接手動追蹤輸入的按鈕精確移動。</span><span class="sxs-lookup"><span data-stu-id="d1eff-155">`PressableButtonHoloLens2` (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/PressableButtonHoloLens2.prefab) is HoloLens 2's shell style button that supports the precise movement of the button for the direct hand tracking input.</span></span> <span data-ttu-id="d1eff-156">它結合 `Interactable` 腳本與 `PressableButton` 腳本。</span><span class="sxs-lookup"><span data-stu-id="d1eff-156">It combines `Interactable` script with `PressableButton` script.</span></span>

<span data-ttu-id="d1eff-157">針對 HoloLens 2，建議使用具有不透明 backplate 的按鈕。</span><span class="sxs-lookup"><span data-stu-id="d1eff-157">For HoloLens 2, it is recommended to use buttons with an opaque backplate.</span></span> <span data-ttu-id="d1eff-158">由於這些可用性和穩定性問題，因此不建議使用透明按鈕：</span><span class="sxs-lookup"><span data-stu-id="d1eff-158">Transparent buttons are not recommended because of these usability and stability issues:</span></span>

* <span data-ttu-id="d1eff-159">在實體環境中難以閱讀圖示和文字</span><span class="sxs-lookup"><span data-stu-id="d1eff-159">Icon and text are difficult to read with the physical environment</span></span>
* <span data-ttu-id="d1eff-160">當事件觸發時，很難瞭解</span><span class="sxs-lookup"><span data-stu-id="d1eff-160">It is hard to understand when the event triggers</span></span>
* <span data-ttu-id="d1eff-161">透過透明平面顯示的全像 LSR，可能不穩定，HoloLens 2 的深度穩定</span><span class="sxs-lookup"><span data-stu-id="d1eff-161">Holograms that are displayed through a transparent plane can be unstable with HoloLens 2's Depth LSR stabilization</span></span>

![按鈕](../images/button/MRTK_Button_UsePlated.png)

## <a name="how-to-use-pressable-buttons"></a><span data-ttu-id="d1eff-163">如何使用 pressable 按鈕</span><span class="sxs-lookup"><span data-stu-id="d1eff-163">How to use pressable buttons</span></span>

### <a name="unity-ui-based-buttons"></a><span data-ttu-id="d1eff-164">Unity UI 型按鈕</span><span class="sxs-lookup"><span data-stu-id="d1eff-164">Unity UI based buttons</span></span>

<span data-ttu-id="d1eff-165">在場景中建立畫布 (GameObject > UI-> Canvas) 。</span><span class="sxs-lookup"><span data-stu-id="d1eff-165">Create a Canvas in your scene (GameObject -> UI -> Canvas).</span></span> <span data-ttu-id="d1eff-166">在畫布的 [偵測器] 面板中：</span><span class="sxs-lookup"><span data-stu-id="d1eff-166">In the Inspector panel for your Canvas:</span></span>

* <span data-ttu-id="d1eff-167">按一下 [轉換成 MRTK Canvas]</span><span class="sxs-lookup"><span data-stu-id="d1eff-167">Click "Convert to MRTK Canvas"</span></span>
* <span data-ttu-id="d1eff-168">按一下 [新增 NearInteractionTouchableUnityUI]</span><span class="sxs-lookup"><span data-stu-id="d1eff-168">Click "Add NearInteractionTouchableUnityUI"</span></span>
* <span data-ttu-id="d1eff-169">將矩形轉換元件的 X、Y 和 Z 刻度設定為0.001</span><span class="sxs-lookup"><span data-stu-id="d1eff-169">Set the Rect Transform component's X, Y, and Z scale to 0.001</span></span>

<span data-ttu-id="d1eff-170">然後，將 `PressableButtonUnityUI` (資產/MRTK/sdk/features/ux/互動/Prefabs/PressableButtonUnityUI. 預製專案) 、 `PressableButtonUnityUICircular` (資產/MRTK/Sdk/FEATURES/Ux/互動/Prefabs/PressableButtonUnityUICircular. 預製專案) ，或 `PressableButtonHoloLens2UnityUI` (資產/MRTK/sdk/features/ux/互動/Prefabs/PressableButtonHoloLens2UnityUI. 預製專案) 至畫布上。</span><span class="sxs-lookup"><span data-stu-id="d1eff-170">Then, drag `PressableButtonUnityUI` (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/PressableButtonUnityUI.prefab), `PressableButtonUnityUICircular` (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/PressableButtonUnityUICircular.prefab), or `PressableButtonHoloLens2UnityUI` (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/PressableButtonHoloLens2UnityUI.prefab) onto the Canvas.</span></span>

### <a name="collider-based-buttons"></a><span data-ttu-id="d1eff-171">以碰撞式為基礎的按鈕</span><span class="sxs-lookup"><span data-stu-id="d1eff-171">Collider based buttons</span></span>

<span data-ttu-id="d1eff-172">只要拖曳 `PressableButtonHoloLens2` (資產/MRTK/SDK/Features/UX/互動/Prefabs/PressableButtonHoloLens2. 預製專案) 或 `PressableButtonHoloLens2Unplated` (資產/MRTK/SDK/FEATURES/UX/互動/Prefabs/PressableButtonHoloLens2Unplated. 預製專案) 進入場景。</span><span class="sxs-lookup"><span data-stu-id="d1eff-172">Simply drag `PressableButtonHoloLens2` (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/PressableButtonHoloLens2.prefab) or `PressableButtonHoloLens2Unplated` (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/PressableButtonHoloLens2Unplated.prefab) into the scene.</span></span> <span data-ttu-id="d1eff-173">這些按鈕 prefabs 已設定為對各種類型的輸入具有音訊視覺效果的意見反應，包括清楚的輸入和注視。</span><span class="sxs-lookup"><span data-stu-id="d1eff-173">These button prefabs are already configured to have audio-visual feedback for the various types of inputs, including articulated hand input and gaze.</span></span>

<span data-ttu-id="d1eff-174">預製專案本身以及 [互動](Interactable.md) 元件中公開的事件可以用來觸發其他動作。</span><span class="sxs-lookup"><span data-stu-id="d1eff-174">The events exposed in the prefab itself as well as the [Interactable](Interactable.md) component can be used to trigger additional actions.</span></span> <span data-ttu-id="d1eff-175">[HandInteractionExample 場景](../example-scenes/HandInteractionExamples.md)中的 [pressable] 按鈕會使用互動的 *OnClick* 事件來觸發 cube 色彩的變更。</span><span class="sxs-lookup"><span data-stu-id="d1eff-175">The pressable buttons in the [HandInteractionExample scene](../example-scenes/HandInteractionExamples.md) use Interactable's *OnClick* event to trigger a change in the color of a cube.</span></span> <span data-ttu-id="d1eff-176">此事件會針對不同類型的輸入方法（例如注視、碰點、手光，以及透過 pressable 按鈕腳本的實體按鈕按下）觸發。</span><span class="sxs-lookup"><span data-stu-id="d1eff-176">This event gets triggered for different types of input methods such as gaze, air-tap, hand-ray, as well as physical button presses through the pressable button script.</span></span>

<img src="../images/button/MRTK_Button_HowToUse_Interactable.png" width="450" alt="How to Use Interactable">

<span data-ttu-id="d1eff-177">您可以設定 [pressable] 按鈕透過按鈕上的來引發 *OnClick* 事件的時機 `PhysicalPressEventRouter` 。</span><span class="sxs-lookup"><span data-stu-id="d1eff-177">You can configure when the pressable button fires the *OnClick* event via the `PhysicalPressEventRouter` on the button.</span></span> <span data-ttu-id="d1eff-178">例如，您可以將 *OnClick* 設定為第一次按下按鈕時引發，而不是按下和放開，方法是在 *按下* 時，按 [按一下] 事件來設定 *互動*。</span><span class="sxs-lookup"><span data-stu-id="d1eff-178">For example, you can set *OnClick* to fire when the button is first pressed, as opposed to being pressed and released, by setting *Interactable On Click* to *Event On Press*.</span></span>

<img src="../images/button/MRTK_Button_HowTo_Events.png" width="450" alt="How to add Events">

<span data-ttu-id="d1eff-179">若要利用特定的已表達手勢輸入狀態資訊，您可以使用 pressable 按鈕事件- *觸控開始*、 *觸控端*、 *按下按鈕*、 *按鈕已釋放*。</span><span class="sxs-lookup"><span data-stu-id="d1eff-179">To leverage specific articulated hand input state information, you can use pressable buttons events - *Touch Begin*, *Touch End*, *Button Pressed*, *Button Released*.</span></span> <span data-ttu-id="d1eff-180">不過，這些事件將不會引發，以回應碰點、手動光線或眼睛輸入。</span><span class="sxs-lookup"><span data-stu-id="d1eff-180">These events will not fire in response to air-tap, hand-ray, or eye inputs, however.</span></span> <span data-ttu-id="d1eff-181">**若要同時支援近乎和遠的互動，建議使用互動的 *OnClick* 事件。**</span><span class="sxs-lookup"><span data-stu-id="d1eff-181">**To support both near and far interactions, it is recommended to use Interactable's *OnClick* event.**</span></span>

<img src="../images/button/MRTK_Button_HowTo_PressableButton.png" width="450" alt="How to Pressable buttons">

## <a name="interaction-states"></a><span data-ttu-id="d1eff-182">互動狀態</span><span class="sxs-lookup"><span data-stu-id="d1eff-182">Interaction states</span></span>

<span data-ttu-id="d1eff-183">處於閒置狀態時，不會顯示按鈕的 front 板。</span><span class="sxs-lookup"><span data-stu-id="d1eff-183">In the idle state, the button's front plate is not visible.</span></span> <span data-ttu-id="d1eff-184">以手指方法或注視輸入的游標作為介面，會顯示 front 盤子的發光框線。</span><span class="sxs-lookup"><span data-stu-id="d1eff-184">As a finger approaches or a cursor from gaze input targets the surface, the front plate's glowing border becomes visible.</span></span> <span data-ttu-id="d1eff-185">前端板介面上的 fingertip 位置有額外的反白顯示。</span><span class="sxs-lookup"><span data-stu-id="d1eff-185">There is additional highlighting of the fingertip position on the front plate surface.</span></span> <span data-ttu-id="d1eff-186">以手指推送時，front 板會隨著 fingertip 移動。</span><span class="sxs-lookup"><span data-stu-id="d1eff-186">When pushed with a finger, the front plate moves with the fingertip.</span></span> <span data-ttu-id="d1eff-187">當 fingertip 觸及 front 板的介面時，它會顯示一個微妙的脈衝效果，以提供觸控點的視覺化意見反應。</span><span class="sxs-lookup"><span data-stu-id="d1eff-187">When the fingertip touches the surface of the front plate, it shows a subtle pulse effect to give visual feedback of the touch point.</span></span>

<span data-ttu-id="d1eff-188">在 HoloLens 2 shell 樣式按鈕中，有許多視覺提示和 affordances 可提高使用者對互動的信賴度。</span><span class="sxs-lookup"><span data-stu-id="d1eff-188">In HoloLens 2 shell-style button, there are many visual cues and affordances to increase the user's confidence on interaction.</span></span>

|  ![近亮光](../images/button/ux_button_affordance_proximitylight.jpg) | ![焦點醒目提示](../images/button/ux_button_affordance_focushighlight.jpg)  | ![壓縮框架](../images/button/ux_button_affordance_compression.jpg) | ![觸發程式上的脈衝](../images/button/ux_button_affordance_pulse.jpg) |
|:--- | :--- | :--- | :--- |
| <span data-ttu-id="d1eff-193">近亮光</span><span class="sxs-lookup"><span data-stu-id="d1eff-193">Proximity light</span></span> | <span data-ttu-id="d1eff-194">焦點醒目提示</span><span class="sxs-lookup"><span data-stu-id="d1eff-194">Focus highlight</span></span> | <span data-ttu-id="d1eff-195">壓縮框架</span><span class="sxs-lookup"><span data-stu-id="d1eff-195">Compressing cage</span></span> | <span data-ttu-id="d1eff-196">觸發程式上的脈衝</span><span class="sxs-lookup"><span data-stu-id="d1eff-196">Pulse on trigger</span></span> |

<span data-ttu-id="d1eff-197">微妙的脈衝效果是由 [pressable] 按鈕所觸發，它會尋找即時在目前互動指標上 *) 的 ProximityLight (s* 。</span><span class="sxs-lookup"><span data-stu-id="d1eff-197">The subtle pulse effect is triggered by the pressable button, which looks for *ProximityLight(s)* that live on the currently interacting pointer.</span></span> <span data-ttu-id="d1eff-198">如果找到任何接近的燈，則會 `ProximityLight.Pulse` 呼叫方法，這會自動以動畫顯示著色器參數來顯示脈衝。</span><span class="sxs-lookup"><span data-stu-id="d1eff-198">If any proximity lights are found, the `ProximityLight.Pulse` method is called, which automatically animates shader parameters to display a pulse.</span></span>

## <a name="inspector-properties"></a><span data-ttu-id="d1eff-199">偵測器屬性</span><span class="sxs-lookup"><span data-stu-id="d1eff-199">Inspector properties</span></span>

![按鈕結構](../images/button/MRTK_Button_Structure.png)

<span data-ttu-id="d1eff-201">方塊 **碰撞** 
 `Box Collider`按鈕的 front 板。</span><span class="sxs-lookup"><span data-stu-id="d1eff-201">**Box Collider**
`Box Collider` for the button's front plate.</span></span>

<span data-ttu-id="d1eff-202">**Pressable 按鈕** 按鍵互動的按鈕移動邏輯。</span><span class="sxs-lookup"><span data-stu-id="d1eff-202">**Pressable Button** The logic for the button movement with hand press interaction.</span></span>

<span data-ttu-id="d1eff-203">**實體按事件路由器** 此腳本會將事件從手形的互動傳送至 [互動](Interactable.md)。</span><span class="sxs-lookup"><span data-stu-id="d1eff-203">**Physical Press Event Router** This script sends events from hand press interaction to [Interactable](Interactable.md).</span></span>

<span data-ttu-id="d1eff-204">**互動** 
[互動](Interactable.md)可處理各種類型的互動狀態和事件。</span><span class="sxs-lookup"><span data-stu-id="d1eff-204">**Interactable**
[Interactable](Interactable.md) handles various types of interaction states and events.</span></span> <span data-ttu-id="d1eff-205">HoloLens 的注視、手勢和語音輸入，以及沉浸式耳機移動控制器輸入都會由這個腳本直接處理。</span><span class="sxs-lookup"><span data-stu-id="d1eff-205">HoloLens gaze, gesture, and voice input and immersive headset motion controller input are directly handled by this script.</span></span>

<span data-ttu-id="d1eff-206">**音訊來源** 音訊意見反應剪輯的 Unity 音訊來源。</span><span class="sxs-lookup"><span data-stu-id="d1eff-206">**Audio Source** Unity audio source for the audio feedback clips.</span></span>

<span data-ttu-id="d1eff-207">*NearInteractionTouchable* 需要使用明確的手輸入進行任何物件可觸式。</span><span class="sxs-lookup"><span data-stu-id="d1eff-207">*NearInteractionTouchable.cs* Required to make any object touchable with articulated hand input.</span></span>

## <a name="prefab-layout"></a><span data-ttu-id="d1eff-208">預製專案版面配置</span><span class="sxs-lookup"><span data-stu-id="d1eff-208">Prefab layout</span></span>

<span data-ttu-id="d1eff-209">*ButtonContent* 物件包含 front 板、文字標籤和圖示。</span><span class="sxs-lookup"><span data-stu-id="d1eff-209">The *ButtonContent* object contains front plate, text label and icon.</span></span> <span data-ttu-id="d1eff-210">*FrontPlate* 會使用 *Button_Box* 著色器，回應索引 fingertip 的鄰近程度。</span><span class="sxs-lookup"><span data-stu-id="d1eff-210">The *FrontPlate* responds to the proximity of the index fingertip using the *Button_Box* shader.</span></span> <span data-ttu-id="d1eff-211">它會顯示對觸控的燈光框線、相近光源和脈衝效果。</span><span class="sxs-lookup"><span data-stu-id="d1eff-211">It shows glowing borders, proximity light, and a pulse effect on touch.</span></span> <span data-ttu-id="d1eff-212">文字標籤會使用 TextMesh Pro 進行。</span><span class="sxs-lookup"><span data-stu-id="d1eff-212">The text label is made with TextMesh Pro.</span></span> <span data-ttu-id="d1eff-213">*SeeItSayItLabel* 的可見度由 [互動](Interactable.md)的主題控制。</span><span class="sxs-lookup"><span data-stu-id="d1eff-213">*SeeItSayItLabel*'s visibility is controlled by [Interactable](Interactable.md)'s theme.</span></span>

![按鈕版面配置](../images/button/MRTK_Button_Layout.png)

## <a name="how-to-change-the-icon-and-text"></a><span data-ttu-id="d1eff-215">如何變更圖示和文字</span><span class="sxs-lookup"><span data-stu-id="d1eff-215">How to change the icon and text</span></span>

<span data-ttu-id="d1eff-216">MRTK 按鈕會使用 `ButtonConfigHelper` 元件來協助您變更按鈕的圖示、文字和標籤。</span><span class="sxs-lookup"><span data-stu-id="d1eff-216">MRTK buttons use a `ButtonConfigHelper` component to assist you in changing the button's icon, text and label.</span></span> <span data-ttu-id="d1eff-217"> (請注意，如果選取的按鈕上沒有元素，某些欄位可能不存在。 ) </span><span class="sxs-lookup"><span data-stu-id="d1eff-217">(Note that some fields may be absent if elements are not present on the selected button.)</span></span>

![按鈕設定協助程式](../images/button/MRTK_Button_Config_Helper.png)

### <a name="creating-and-modifying-icon-sets"></a><span data-ttu-id="d1eff-219">建立和修改圖示集</span><span class="sxs-lookup"><span data-stu-id="d1eff-219">Creating and Modifying Icon Sets</span></span>

<span data-ttu-id="d1eff-220">**圖示集** 是元件所使用的一組共用圖示資產 `ButtonConfigHelper` 。</span><span class="sxs-lookup"><span data-stu-id="d1eff-220">An **Icon Set** is a shared set of icon assets used by the `ButtonConfigHelper` component.</span></span> <span data-ttu-id="d1eff-221">支援三種圖示 *樣式* 。</span><span class="sxs-lookup"><span data-stu-id="d1eff-221">Three icon *styles* are supported.</span></span>

* <span data-ttu-id="d1eff-222">**四** 個圖示會在使用的四個上呈現 `MeshRenderer` 。</span><span class="sxs-lookup"><span data-stu-id="d1eff-222">**Quad** icons are rendered on a quad using a `MeshRenderer`.</span></span> <span data-ttu-id="d1eff-223">這是預設的圖示樣式。</span><span class="sxs-lookup"><span data-stu-id="d1eff-223">This is the default icon style.</span></span>
* <span data-ttu-id="d1eff-224">**Sprite** 圖示是使用來呈現 `SpriteRenderer` 。</span><span class="sxs-lookup"><span data-stu-id="d1eff-224">**Sprite** icons are rendered using a `SpriteRenderer`.</span></span> <span data-ttu-id="d1eff-225">如果您想要將圖示匯入為 sprite 工作表，或想要將圖示資產與 Unity UI 元件共用，這會很有用。</span><span class="sxs-lookup"><span data-stu-id="d1eff-225">This is useful if you prefer to import your icons as a sprite sheet, or if you want your icon assets to be shared with Unity UI components.</span></span> <span data-ttu-id="d1eff-226">若要使用此樣式，您必須將 Sprite 編輯器套件安裝 **(Windows-> 封裝管理員 > 2D Sprite)**</span><span class="sxs-lookup"><span data-stu-id="d1eff-226">To use this style you will need to install the Sprite Editor package **(Windows -> Package Manager -> 2D Sprite)**</span></span>
* <span data-ttu-id="d1eff-227">**字元** 圖示會使用元件來呈現 `TextMeshPro` 。</span><span class="sxs-lookup"><span data-stu-id="d1eff-227">**Char** icons are rendered using a `TextMeshPro` component.</span></span> <span data-ttu-id="d1eff-228">如果您想要使用圖示字型，這會很有用。</span><span class="sxs-lookup"><span data-stu-id="d1eff-228">This is useful if you prefer to use an icon font.</span></span> <span data-ttu-id="d1eff-229">若要使用 HoloLens 圖示字型，您將需要建立 `TextMeshPro` 字型資產。</span><span class="sxs-lookup"><span data-stu-id="d1eff-229">To use the HoloLens icon font you will need to create a `TextMeshPro` font asset.</span></span>

<span data-ttu-id="d1eff-230">若要變更按鈕使用的樣式，請展開 ButtonConfigHelper 中的 [ *圖示* ] 下拉式清單，然後從 [ *圖示樣式* ] 下拉式清單中選取。</span><span class="sxs-lookup"><span data-stu-id="d1eff-230">To change which style your button uses, expand the *Icons* dropdown in the ButtonConfigHelper and select from the *Icon Style* dropdown.</span></span>

<span data-ttu-id="d1eff-231">您可以使用 [資產] 功能表建立新的按鈕圖示集： **建立 > 混合現實工具組 > 圖示集。**</span><span class="sxs-lookup"><span data-stu-id="d1eff-231">You can create a new button icon set with the asset menu: **Create > Mixed Reality Toolkit > Icon Set.**</span></span> <span data-ttu-id="d1eff-232">若要加入四個和 sprite 圖示，只要將它們拖曳到各自的陣列中即可。</span><span class="sxs-lookup"><span data-stu-id="d1eff-232">To add quad and sprite icons, simply drag them into their respective arrays.</span></span> <span data-ttu-id="d1eff-233">若要新增字元圖示，您必須先建立並指派字型資產。</span><span class="sxs-lookup"><span data-stu-id="d1eff-233">To add Char icons, you must first create and assign a font asset.</span></span>

<span data-ttu-id="d1eff-234">在 MRTK 2.4 和更高的範圍中，我們建議將自訂圖示紋理移至 IconSet。</span><span class="sxs-lookup"><span data-stu-id="d1eff-234">In MRTK 2.4 and beyond, we recommend custom icon textures be moved into an IconSet.</span></span>
<span data-ttu-id="d1eff-235">若要將專案中所有按鈕的資產升級為新的建議格式，請使用 ButtonConfigHelperMigrationHandler。</span><span class="sxs-lookup"><span data-stu-id="d1eff-235">To upgrade the assets on all buttons in a project to the new recommended format, use the ButtonConfigHelperMigrationHandler.</span></span>
<span data-ttu-id="d1eff-236"> (混合現實工具組-> 公用程式-> 的遷移視窗-> 的遷移處理常式選取範圍-> MixedReality) </span><span class="sxs-lookup"><span data-stu-id="d1eff-236">(Mixed Reality Toolkit -> Utilities -> Migration Window -> Migration Handler Selection -> Microsoft.MixedReality.Toolkit.Utilities.ButtonConfigHelperMigrationHandler)</span></span>

<span data-ttu-id="d1eff-237">匯入升級按鈕所需的 MixedRealityToolkit 工具套件。</span><span class="sxs-lookup"><span data-stu-id="d1eff-237">Importing the Microsoft.MixedRealityToolkit.Unity.Tools package required to upgrade the buttons.</span></span>

![升級視窗對話方塊](https://user-images.githubusercontent.com/39840334/82096923-bd28bf80-96b6-11ea-93a9-ceafcb822242.png)

<span data-ttu-id="d1eff-239">如果在遷移期間于預設的圖示集中找不到圖示，則會在 MixedRealityToolkit 中建立自訂圖示集。產生/CustomIconSets。</span><span class="sxs-lookup"><span data-stu-id="d1eff-239">If an icon is not found in the default icon set during migration, a custom icon set will be created in MixedRealityToolkit.Generated/CustomIconSets.</span></span> <span data-ttu-id="d1eff-240">對話方塊會指出已發生此情況。</span><span class="sxs-lookup"><span data-stu-id="d1eff-240">A dialog will indicate that this has taken place.</span></span>

![自訂圖示通知](https://user-images.githubusercontent.com/9789716/82093856-c57dfc00-96b0-11ea-83ab-4df57446d661.PNG)

### <a name="creating-a-hololens-icon-font-asset"></a><span data-ttu-id="d1eff-242">建立 HoloLens 圖示字型資產</span><span class="sxs-lookup"><span data-stu-id="d1eff-242">Creating a HoloLens Icon Font Asset</span></span>

<span data-ttu-id="d1eff-243">首先，將圖示字型匯入 Unity。</span><span class="sxs-lookup"><span data-stu-id="d1eff-243">First, import the icon font into Unity.</span></span> <span data-ttu-id="d1eff-244">在 Windows 電腦上，您可以在 *windows/font-family/holomdl2. ttf* 中找到預設的 HoloLens 字型。</span><span class="sxs-lookup"><span data-stu-id="d1eff-244">On Windows machines you can find the default HoloLens font in *Windows/Fonts/holomdl2.ttf.*</span></span> <span data-ttu-id="d1eff-245">將此檔案複製並貼到您的 [資產] 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="d1eff-245">Copy and paste this file into your Assets folder.</span></span>

<span data-ttu-id="d1eff-246">接下來，透過 **Window > TextMeshPro > 字型建立者** 來開啟 [TextMeshPro 字型資產建立者]。</span><span class="sxs-lookup"><span data-stu-id="d1eff-246">Next, open the TextMeshPro Font Asset Creator via **Window > TextMeshPro > Font Asset Creator.**</span></span> <span data-ttu-id="d1eff-247">以下是用來產生 HoloLens 字型塔的建議設定。</span><span class="sxs-lookup"><span data-stu-id="d1eff-247">Here are the recommended settings for generating a HoloLens font atlas.</span></span> <span data-ttu-id="d1eff-248">若要包含所有圖示，請在 [ *字元順序* ] 欄位中貼上下列 Unicode 範圍：</span><span class="sxs-lookup"><span data-stu-id="d1eff-248">To include all icons, paste the following Unicode range into the *Character Sequence* field:</span></span>

```c#
E700-E702,E706,E70D-E70E,E710-E714,E718,E71A,E71D-E71E,E720,E722,E728,E72A-E72E,E736,E738,E73F,E74A-E74B,E74D,E74F-E752,E760-E761,E765,E767-E769,E76B-E76C,E770,E772,E774,E777,E779-E77B,E782-E783,E785-E786,E799,E7A9-E7AB,E7AF-E7B1,E7B4,E7C8,E7E8-E7E9,E7FC,E80F,E821,E83F,E850-E859,E872-E874,E894-E895,E8A7,E8B2,E8B7,E8B9,E8D5,E8EC,E8FB,E909,E91B,E92C,E942,E95B,E992-E995,E9E9-E9EA,EA37,EA40,EA4A,EA55,EA96,EB51-EB52,EB65,EB9D-EBB5,EBCB-EBCC,EBCF-EBD3,EC03,EC19,EC3F,EC7A,EC8E-EC98,ECA2,ECD8-ECDA,ECE0,ECE7-ECEB,ED17,EE93,EFA9,F114-F120,F132,F181,F183-F186
```

![按鈕資產建立1](../images/button/MRTK_Font_Asset_Creation_1.png)

<span data-ttu-id="d1eff-250">產生字型資產之後，請將其儲存至您的專案，並將其指派給您的圖示集的 *Char 圖示字型* 欄位。</span><span class="sxs-lookup"><span data-stu-id="d1eff-250">Once the font asset is generated, save it to your project and assign it to your Icon Set's *Char Icon Font* field.</span></span> <span data-ttu-id="d1eff-251">現在將會填入 [ *可用圖示* ] 下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="d1eff-251">The *Available Icons* dropdown will now be populated.</span></span> <span data-ttu-id="d1eff-252">若要讓圖示可供按鈕使用，請按一下它。</span><span class="sxs-lookup"><span data-stu-id="d1eff-252">To make an icon available for use by a button, click it.</span></span> <span data-ttu-id="d1eff-253">它會新增至 [ *選取的圖示* ] 下拉式清單中，現在會顯示在中， `ButtonConfigHelper.` 您可以選擇性地為圖示提供標記。</span><span class="sxs-lookup"><span data-stu-id="d1eff-253">It will be added to the *Selected Icons* dropdown and will now show up in the `ButtonConfigHelper.` You can optionally give the icon a tag.</span></span> <span data-ttu-id="d1eff-254">這可讓您在執行時間設定圖示。</span><span class="sxs-lookup"><span data-stu-id="d1eff-254">This enables setting the icon at runtime.</span></span>

![按鈕資產建立3](../images/button/MRTK_Font_Asset_Creation_3.png)

![按鈕資產建立2](../images/button/MRTK_Font_Asset_Creation_2.png)

```c#
public void SetButtonToAdjust()
{
    ButtonConfigHelper buttonConfigHelper = gameObject.GetComponent<ButtonConfigHelper>();
    buttonConfigHelper.SetCharIconByName("AppBarAdjust");
}
```

<span data-ttu-id="d1eff-257">若要使用您的圖示集，請選取按鈕，展開中的 [圖示] 下拉式清單， `ButtonConfigHelper` 然後將它指派給 [ *圖示集* ] 欄位。</span><span class="sxs-lookup"><span data-stu-id="d1eff-257">To use your Icon Set select a button, expand the Icons dropdown in the `ButtonConfigHelper` and assign it to the *Icon Set* field.</span></span>

![按鈕資產指派圖示集](../images/button/MRTK_Button_Icon_Set_Assign.png)

## <a name="how-to-change-the-size-of-a-button"></a><span data-ttu-id="d1eff-259">如何變更按鈕的大小</span><span class="sxs-lookup"><span data-stu-id="d1eff-259">How to change the size of a button</span></span>

<span data-ttu-id="d1eff-260">HoloLens 2 的 shell 樣式按鈕大小為32x32mm。</span><span class="sxs-lookup"><span data-stu-id="d1eff-260">HoloLens 2's shell-style button's size is 32x32mm.</span></span> <span data-ttu-id="d1eff-261">若要自訂維度，請在按鈕預製專案中變更這些物件的大小：</span><span class="sxs-lookup"><span data-stu-id="d1eff-261">To customize the dimension, change the size of these objects in the button prefab:</span></span>

1. <span data-ttu-id="d1eff-262">**FrontPlate**</span><span class="sxs-lookup"><span data-stu-id="d1eff-262">**FrontPlate**</span></span>
2. <span data-ttu-id="d1eff-263">BackPlate 下的 **四** 個</span><span class="sxs-lookup"><span data-stu-id="d1eff-263">**Quad** under BackPlate</span></span>
3. <span data-ttu-id="d1eff-264">根的方塊 **碰撞**</span><span class="sxs-lookup"><span data-stu-id="d1eff-264">**Box Collider** on the root</span></span>

<span data-ttu-id="d1eff-265">然後，在 NearInteractionTouchable 腳本（位於按鈕的根目錄）中，按一下 [ **修正界限** ] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="d1eff-265">Then, click **Fix Bounds** button in the NearInteractionTouchable script which is in the root of the button.</span></span>

<span data-ttu-id="d1eff-266">更新 FrontPlate ![ 按鈕大小自訂1的大小](../images/button/MRTK_Button_SizeCustomization1.png)</span><span class="sxs-lookup"><span data-stu-id="d1eff-266">Update the size of the FrontPlate ![Button Size customization 1](../images/button/MRTK_Button_SizeCustomization1.png)</span></span>

<span data-ttu-id="d1eff-267">更新四個 ![ 按鈕大小自訂2的大小](../images/button/MRTK_Button_SizeCustomization2.png)</span><span class="sxs-lookup"><span data-stu-id="d1eff-267">Update the size of the Quad ![Button Size customization 2](../images/button/MRTK_Button_SizeCustomization2.png)</span></span>

<span data-ttu-id="d1eff-268">更新 Box 碰撞 ![ 按鈕大小自訂3的大小](../images/button/MRTK_Button_SizeCustomization3.png)</span><span class="sxs-lookup"><span data-stu-id="d1eff-268">Update the size of the Box Collider ![Button Size customization 3](../images/button/MRTK_Button_SizeCustomization3.png)</span></span>

<span data-ttu-id="d1eff-269">按一下 [修正界限] ![ 按鈕大小自訂4](../images/button/MRTK_Button_SizeCustomization4.png)</span><span class="sxs-lookup"><span data-stu-id="d1eff-269">Click 'Fix Bounds' ![Button Size customization 4](../images/button/MRTK_Button_SizeCustomization4.png)</span></span>

## <a name="voice-command-see-it-say-it"></a><span data-ttu-id="d1eff-270">語音命令 ( 「請參閱-it」 ) </span><span class="sxs-lookup"><span data-stu-id="d1eff-270">Voice command ('see-it, say-it')</span></span>

<span data-ttu-id="d1eff-271">**語音輸入處理常式** [Pressable 中的 [互動](Interactable.md) 腳本] 按鈕已經在執行 `IMixedRealitySpeechHandler` 。</span><span class="sxs-lookup"><span data-stu-id="d1eff-271">**Speech Input Handler** The [Interactable](Interactable.md) script in Pressable Button already implements `IMixedRealitySpeechHandler`.</span></span> <span data-ttu-id="d1eff-272">您可以在這裡設定語音命令關鍵字。</span><span class="sxs-lookup"><span data-stu-id="d1eff-272">A voice command keyword can be set here.</span></span>

<img src="../images/button/MRTK_Button_Speech1.png" width="450" alt="Button Speech 1">

<span data-ttu-id="d1eff-273">**語音輸入設定檔** 此外，您必須在全域 *語音命令設定檔* 中註冊 voice 命令關鍵字。</span><span class="sxs-lookup"><span data-stu-id="d1eff-273">**Speech Input Profile** Additionally, you need to register the voice command keyword in the global *Speech Commands Profile*.</span></span>

<img src="../images/button/MRTK_Button_Speech2.png" width="450" alt="Button Speech 2">

<span data-ttu-id="d1eff-274">**請參閱-it，例如 it 標籤** Pressable 按鈕預製專案在 *SeeItSayItLabel* 物件下具有預留位置 TextMesh Pro 標籤。</span><span class="sxs-lookup"><span data-stu-id="d1eff-274">**See-it, Say-it label** The pressable button prefab has a placeholder TextMesh Pro label under the *SeeItSayItLabel* object.</span></span> <span data-ttu-id="d1eff-275">您可以使用此標籤，將按鈕的 voice 命令關鍵字傳達給使用者。</span><span class="sxs-lookup"><span data-stu-id="d1eff-275">You can use this label to communicate the voice command keyword for the button to the user.</span></span>

<img src="../images/button/MRTK_Button_Speech3.png" width="450" alt="Button Speech 3">

## <a name="how-to-make-a-button-from-scratch"></a><span data-ttu-id="d1eff-276">如何從頭建立按鈕</span><span class="sxs-lookup"><span data-stu-id="d1eff-276">How to make a button from scratch</span></span>

<span data-ttu-id="d1eff-277">您可以在 **PressableButtonExample** 場景中找到這些按鈕的範例。</span><span class="sxs-lookup"><span data-stu-id="d1eff-277">You can find the examples of these buttons in the **PressableButtonExample** scene.</span></span>

<img src="../images/button/MRTK_PressableButtonCube0.png" alt="Pressable Button Cube 0">

### <a name="1-creating-a-pressable-button-with-cube-near-interaction-only"></a><span data-ttu-id="d1eff-278">1. 建立具有 cube 的 pressable 按鈕 (近乎互動) </span><span class="sxs-lookup"><span data-stu-id="d1eff-278">1. Creating a pressable button with cube (near interaction only)</span></span>

1. <span data-ttu-id="d1eff-279"> (GameObject > 3D 物件 > Cube 建立 Unity Cube) </span><span class="sxs-lookup"><span data-stu-id="d1eff-279">Create a Unity Cube (GameObject > 3D Object > Cube)</span></span>
2. <span data-ttu-id="d1eff-280">新增 `PressableButton.cs` 腳本</span><span class="sxs-lookup"><span data-stu-id="d1eff-280">Add `PressableButton.cs` script</span></span>
3. <span data-ttu-id="d1eff-281">新增 `NearInteractionTouchable.cs` 腳本</span><span class="sxs-lookup"><span data-stu-id="d1eff-281">Add `NearInteractionTouchable.cs` script</span></span>

<span data-ttu-id="d1eff-282">在的 [ `PressableButton` 檢查] 面板中，將 cube 物件指派給 **移動按鈕視覺效果**。</span><span class="sxs-lookup"><span data-stu-id="d1eff-282">In the `PressableButton`'s Inspector panel, assign the cube object to the **Moving Button Visuals**.</span></span>

<img src="../images/button/MRTK_PressableButtonCube3.png" width="450" alt="Pressable Button Cube 3">

<span data-ttu-id="d1eff-283">當您選取 cube 時，您會在物件上看到多個彩色圖層。</span><span class="sxs-lookup"><span data-stu-id="d1eff-283">When you select the cube, you will see multiple colored layers on the object.</span></span> <span data-ttu-id="d1eff-284">這會將 **按下設定** 下的距離值視覺化。</span><span class="sxs-lookup"><span data-stu-id="d1eff-284">This visualizes the distance values under **Press Settings**.</span></span> <span data-ttu-id="d1eff-285">使用控制碼，您可以設定何時開始按 (將物件) 移動，以及何時觸發事件。</span><span class="sxs-lookup"><span data-stu-id="d1eff-285">Using the handles, you can configure when to start press (move the object) and when to trigger event.</span></span>

<img src="../images/button/MRTK_PressableButtonCube1.jpg" width="450" alt="Pressable Button Cube 1">

<img src="../images/button/MRTK_PressableButtonCube2.png" width="450"  alt="Pressable button cube 2">

<span data-ttu-id="d1eff-286">當您按下按鈕時，它會移動並產生腳本中公開的適當事件， `PressableButton.cs` 例如 TouchBegin () 、TouchEnd () 、ButtonPressed () 、ButtonReleased () 。</span><span class="sxs-lookup"><span data-stu-id="d1eff-286">When you press the button, it will move and generate proper events exposed in the `PressableButton.cs` script such as TouchBegin(), TouchEnd(), ButtonPressed(), ButtonReleased().</span></span>

<img src="../images/button/MRTK_PressableButtonCubeRun1.jpg" alt="Pressable Button Cube Run 1">

### <a name="2-adding-visual-feedback-to-the-basic-cube-button"></a><span data-ttu-id="d1eff-287">2. 將視覺效果意見反應新增至 [基本 cube] 按鈕</span><span class="sxs-lookup"><span data-stu-id="d1eff-287">2. Adding visual feedback to the basic cube button</span></span>

<span data-ttu-id="d1eff-288">MRTK 標準著色器提供各種功能，可讓您輕鬆地新增視覺效果的意見反應。</span><span class="sxs-lookup"><span data-stu-id="d1eff-288">MRTK Standard Shader provides various features that makes it easy to add visual feedback.</span></span> <span data-ttu-id="d1eff-289">建立材質並選取著色器 `Mixed Reality Toolkit/Standard` 。</span><span class="sxs-lookup"><span data-stu-id="d1eff-289">Create a material and select shader `Mixed Reality Toolkit/Standard`.</span></span> <span data-ttu-id="d1eff-290">或者，您可以使用或複製其中一個 `/SDK/StandardAssets/Materials/` 使用 MRTK 標準著色器的現有材質。</span><span class="sxs-lookup"><span data-stu-id="d1eff-290">Or you can use or duplicate one of the existing materials under `/SDK/StandardAssets/Materials/` that uses MRTK Standard Shader.</span></span>

<img src="../images/button/MRTK_PressableButtonCube4.png" width="450" alt="Pressable button cube 4">

<span data-ttu-id="d1eff-291">核取 [ `Hover Light` `Proximity Light` 流暢的 **選項**]。</span><span class="sxs-lookup"><span data-stu-id="d1eff-291">Check `Hover Light` and `Proximity Light` under **Fluent Options**.</span></span> <span data-ttu-id="d1eff-292">這可讓您近乎接近的視覺效果回饋 (鄰近性光線) 和目前的指標 (停留) 互動。</span><span class="sxs-lookup"><span data-stu-id="d1eff-292">This enables visual feedback for both near hand(Proximity Light) and far pointer(Hover Light) interactions.</span></span>

<img src="../images/button/MRTK_PressableButtonCube5.png" width="450" alt="Pressable Button cube 5">

<img src="../images/button/MRTK_PressableButtonCubeRun2.jpg" alt="Pressable button cube Run 2">

### <a name="3-adding-audio-feedback-to-the-basic-cube-button"></a><span data-ttu-id="d1eff-293">3. 將音訊意見反應新增至 [基本 cube] 按鈕</span><span class="sxs-lookup"><span data-stu-id="d1eff-293">3. Adding audio feedback to the basic cube button</span></span>

<span data-ttu-id="d1eff-294">由於 `PressableButton.cs` 腳本會公開 TouchBegin () 、TouchEnd () 、ButtonPressed () 、ButtonReleased () 等事件，因此我們可以輕鬆地指派音訊意見反應。</span><span class="sxs-lookup"><span data-stu-id="d1eff-294">Since `PressableButton.cs` script exposes events such as TouchBegin(), TouchEnd(), ButtonPressed(), ButtonReleased(), we can easily assign audio feedback.</span></span> <span data-ttu-id="d1eff-295">只要將 Unity 新增 `Audio Source` 至 cube 物件，然後選取 [spatialize. PlayOneShot () 來指派音訊剪輯。</span><span class="sxs-lookup"><span data-stu-id="d1eff-295">Simply add Unity's `Audio Source` to the cube object then assign audio clips by selecting AudioSource.PlayOneShot().</span></span> <span data-ttu-id="d1eff-296">您可以使用 MRTK_Select_Main，並 MRTK_Select_Secondary 資料夾下的音訊剪輯 `/SDK/StandardAssets/Audio/` 。</span><span class="sxs-lookup"><span data-stu-id="d1eff-296">You can use MRTK_Select_Main and MRTK_Select_Secondary audio clips under `/SDK/StandardAssets/Audio/` folder.</span></span>

<img src="../images/button/MRTK_PressableButtonCube7.png" width="450" alt="Pressable button cube 7">

<img src="../images/button/MRTK_PressableButtonCube6.png" width="450" alt="Pressable Button Cube 6">

### <a name="4-adding-visual-states-and-handle-far-interaction-events"></a><span data-ttu-id="d1eff-297">4. 新增視覺狀態並處理最遠的互動事件</span><span class="sxs-lookup"><span data-stu-id="d1eff-297">4. Adding visual states and handle far interaction events</span></span>

<span data-ttu-id="d1eff-298">[互動](Interactable.md) 是一種腳本，可讓您輕鬆地為各種類型的輸入互動建立視覺狀態。</span><span class="sxs-lookup"><span data-stu-id="d1eff-298">[Interactable](Interactable.md) is a script that makes it easy to create a visual state for the various types of input interactions.</span></span> <span data-ttu-id="d1eff-299">它也會處理大部分的互動事件。</span><span class="sxs-lookup"><span data-stu-id="d1eff-299">It also handles far interaction events.</span></span> <span data-ttu-id="d1eff-300">`Interactable.cs`在 [**設定檔**] 下的 [**目標**] 欄位中加入 cube 物件，並將其拖放。</span><span class="sxs-lookup"><span data-stu-id="d1eff-300">Add `Interactable.cs` and drag and drop the cube object onto the **Target** field under **Profiles**.</span></span> <span data-ttu-id="d1eff-301">然後，使用類型 **ScaleOffsetColorTheme** 來建立新的主題。</span><span class="sxs-lookup"><span data-stu-id="d1eff-301">Then, create a new Theme with a type **ScaleOffsetColorTheme**.</span></span> <span data-ttu-id="d1eff-302">在此主題下，您可以指定特定互動狀態（例如 **焦點** 和 **按下**）的物件色彩。</span><span class="sxs-lookup"><span data-stu-id="d1eff-302">Under this theme, you can specify the color of the object for the specific interaction states, such as **Focus** and **Pressed**.</span></span> <span data-ttu-id="d1eff-303">您也可以控制刻度和位移。</span><span class="sxs-lookup"><span data-stu-id="d1eff-303">You can also control Scale and Offset, as well.</span></span> <span data-ttu-id="d1eff-304">檢查 **簡化** 並設定持續時間，讓視覺效果轉換平滑。</span><span class="sxs-lookup"><span data-stu-id="d1eff-304">Check **Easing** and set duration to make the visual transition smooth.</span></span>

![選取設定檔主題](../images/button/mrtk_button_profiles.gif)

<span data-ttu-id="d1eff-306">您會看到物件對 (手光線或注視游標) 的回應，以及接近 (手) 互動。</span><span class="sxs-lookup"><span data-stu-id="d1eff-306">You will see the object respond to both far (hand ray or gaze cursor) and near(hand) interactions.</span></span>

<img src="../images/button/MRTK_PressableButtonCubeRun3.jpg" alt="Pressable button cube 3">
<img src="../images/button/MRTK_PressableButtonCubeRun4.jpg" alt="Pressable Button cube 4">

## <a name="custom-button-examples"></a><span data-ttu-id="d1eff-307">自訂按鈕範例</span><span class="sxs-lookup"><span data-stu-id="d1eff-307">Custom button examples</span></span>

<span data-ttu-id="d1eff-308">在 [HandInteractionExample 場景](../example-scenes/HandInteractionExamples.md)中，請參閱使用的鋼琴和圓形按鈕範例 `PressableButton` 。</span><span class="sxs-lookup"><span data-stu-id="d1eff-308">In the [HandInteractionExample scene](../example-scenes/HandInteractionExamples.md), see the piano and round button examples which are both using `PressableButton`.</span></span>

<img src="../images/button/MRTK_Button_Custom1.png" width="450" alt="Button custom 1">

<img src="../images/button/MRTK_Button_Custom2.png" width="450" alt="Button custom 2">

<span data-ttu-id="d1eff-309">每個鋼琴按鍵都有一個 `PressableButton` 和一個已 `NearInteractionTouchable` 指派的腳本。</span><span class="sxs-lookup"><span data-stu-id="d1eff-309">Each piano key has a `PressableButton` and a `NearInteractionTouchable` script assigned.</span></span> <span data-ttu-id="d1eff-310">請務必確認的 *本機向前* 方向 `NearInteractionTouchable` 正確無誤。</span><span class="sxs-lookup"><span data-stu-id="d1eff-310">It is important to verify that the *Local Forward* direction of `NearInteractionTouchable` is correct.</span></span> <span data-ttu-id="d1eff-311">它是以編輯器中的白色箭號表示。</span><span class="sxs-lookup"><span data-stu-id="d1eff-311">It is represented by a white arrow in the editor.</span></span> <span data-ttu-id="d1eff-312">請確定箭號指向按鈕的正面臉部：</span><span class="sxs-lookup"><span data-stu-id="d1eff-312">Make sure the arrow points away from the button's front face:</span></span>

<img src="../images/button/MRTK_Button_Custom3.png" width="450" alt="Button custom 3">

## <a name="see-also"></a><span data-ttu-id="d1eff-313">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d1eff-313">See also</span></span>

* [<span data-ttu-id="d1eff-314">互動</span><span class="sxs-lookup"><span data-stu-id="d1eff-314">Interactable</span></span>](Interactable.md)
* [<span data-ttu-id="d1eff-315">視覺主題</span><span class="sxs-lookup"><span data-stu-id="d1eff-315">Visual Themes</span></span>](../VisualThemes.md)
