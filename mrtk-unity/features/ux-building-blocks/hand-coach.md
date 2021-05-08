---
title: README_HandCoach
description: 手動指導的說明和範例。
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: 8b4069f25692c4058c912ccd06ae678d67882fcd
ms.sourcegitcommit: e89431d12b5fe480c9bc40e176023798fc35001b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2021
ms.locfileid: "109489268"
---
# <a name="hand-coach"></a><span data-ttu-id="c1e13-104">手勢指導</span><span class="sxs-lookup"><span data-stu-id="c1e13-104">Hand coach</span></span>

![手動指導功能表](../images/hand-coach/MRTK_UX_HandCoach_Main.jpg)

<span data-ttu-id="c1e13-106">手上的教練是3D 模型化的手，當系統未偵測到使用者的手時，就會觸發此手。</span><span class="sxs-lookup"><span data-stu-id="c1e13-106">Hand coach is 3D modeled hand which is triggered when the system does not detect the user’s hands.</span></span> <span data-ttu-id="c1e13-107">這會實作為「教學」元件，可在未教授手勢時協助引導使用者。</span><span class="sxs-lookup"><span data-stu-id="c1e13-107">This is implemented as a “teaching” component that helps guide the user when the gesture has not been taught.</span></span> <span data-ttu-id="c1e13-108">如果使用者尚未針對某段時間完成指定的手勢，則手將會有延遲的迴圈。</span><span class="sxs-lookup"><span data-stu-id="c1e13-108">If users have not done the specified gesture for a period, the hands will loop with a delay.</span></span> <span data-ttu-id="c1e13-109">手指導可用來代表按下按鈕或挑選全像影像。</span><span class="sxs-lookup"><span data-stu-id="c1e13-109">Hand coach could be used to represent pressing a button or picking up a hologram.</span></span>

<span data-ttu-id="c1e13-110">目前的互動模型代表各式各樣的手勢控制項，例如滾動、遠選和近端點擊。</span><span class="sxs-lookup"><span data-stu-id="c1e13-110">The current interaction model represents a wide variety of gesture controls such as scrolling, far select, and near tap.</span></span> <span data-ttu-id="c1e13-111">以下是現有的手動指導範例的完整清單：</span><span class="sxs-lookup"><span data-stu-id="c1e13-111">Below is a full list of existing Hand coach examples:</span></span>

- <span data-ttu-id="c1e13-112">近端點擊-用於按鈕或關閉互動物件</span><span class="sxs-lookup"><span data-stu-id="c1e13-112">Near tap – Used for buttons or close interactable objects</span></span>
- <span data-ttu-id="c1e13-113">全選–用於遠離物件</span><span class="sxs-lookup"><span data-stu-id="c1e13-113">Far select – Used for objects that are far away</span></span>
- <span data-ttu-id="c1e13-114">移動–用來在空間中移動全息圖</span><span class="sxs-lookup"><span data-stu-id="c1e13-114">Move – Used to move a hologram in space</span></span>
- <span data-ttu-id="c1e13-115">旋轉–用來顯示如何旋轉全像影像或物件</span><span class="sxs-lookup"><span data-stu-id="c1e13-115">Rotate – Used to show how to rotate holograms or objects</span></span>
- <span data-ttu-id="c1e13-116">調整-用來顯示如何操作大容量比較或更小的影像</span><span class="sxs-lookup"><span data-stu-id="c1e13-116">Scale – Used to show how to manipulate holograms to be bigger or smaller</span></span>
- <span data-ttu-id="c1e13-117">手形-用來啟動 UI 開始面板或手形功能表</span><span class="sxs-lookup"><span data-stu-id="c1e13-117">Hand flip – Used for bringing up a UI start panel or Hand Menus</span></span>
- <span data-ttu-id="c1e13-118">手掌–用於現成體驗中的 hummingbird 時間。</span><span class="sxs-lookup"><span data-stu-id="c1e13-118">Palm up – Used for hummingbird moment in out of the box experience.</span></span> <span data-ttu-id="c1e13-119">另一個建議是顯示 UI 啟動面板</span><span class="sxs-lookup"><span data-stu-id="c1e13-119">Another suggestion could be to bring up a UI start panel</span></span>
- <span data-ttu-id="c1e13-120">捲軸-用於滾動清單或長檔</span><span class="sxs-lookup"><span data-stu-id="c1e13-120">Scroll – Used for scrolling a list or a long document</span></span>

## <a name="example-scene"></a><span data-ttu-id="c1e13-121">範例場景</span><span class="sxs-lookup"><span data-stu-id="c1e13-121">Example scene</span></span>

<span data-ttu-id="c1e13-122">您可以在以下的 **HandCoachExample** 場景中找到範例： [MixedRealityToolkit. 範例/實驗/HandCoach/場景](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/Examples/Demos/HandCoach/Scenes)</span><span class="sxs-lookup"><span data-stu-id="c1e13-122">You can find examples in the **HandCoachExample** scene under: [MixedRealityToolkit.Examples/Experimental/HandCoach/Scenes](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/Examples/Demos/HandCoach/Scenes)</span></span>

## <a name="hand-3d-assets"></a><span data-ttu-id="c1e13-123">手上立體資產</span><span class="sxs-lookup"><span data-stu-id="c1e13-123">Hand 3D Assets</span></span>

<span data-ttu-id="c1e13-124">您可以在下列檔中找到資產： [MixedRealityToolkit. SDK/實驗/HandCoach](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/Examples/Demos/HandCoach)</span><span class="sxs-lookup"><span data-stu-id="c1e13-124">You can find the assets under: [MixedRealityToolkit.SDK/Experimental/HandCoach](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/Examples/Demos/HandCoach)</span></span>

## <a name="quality"></a><span data-ttu-id="c1e13-125">品質</span><span class="sxs-lookup"><span data-stu-id="c1e13-125">Quality</span></span>

<span data-ttu-id="c1e13-126">如果您注意到 skinned 網格上的扭曲，您需要確定您的專案使用適當的接點數量。</span><span class="sxs-lookup"><span data-stu-id="c1e13-126">If you notice distortions on the skinned mesh, you need to make sure your project is using the proper amount of joints.</span></span>
<span data-ttu-id="c1e13-127">移至 Unity 的 [編輯] > 專案設定 > 品質 > 其他 > Blend 加權。</span><span class="sxs-lookup"><span data-stu-id="c1e13-127">Go to Unity's Edit > Project Settings > Quality > Other > Blend Weights.</span></span> <span data-ttu-id="c1e13-128">確定已選取「4個骨骼」以查看平滑接點。</span><span class="sxs-lookup"><span data-stu-id="c1e13-128">Make sure "4 bones" are selected to see Smooth Joints.</span></span>
<span data-ttu-id="c1e13-129">![專案設定](../images/hand-coach/MRTK_ProjectSettings.png)</span><span class="sxs-lookup"><span data-stu-id="c1e13-129">![Project Setting](../images/hand-coach/MRTK_ProjectSettings.png)</span></span>

## <a name="scripts"></a><span data-ttu-id="c1e13-130">指令碼</span><span class="sxs-lookup"><span data-stu-id="c1e13-130">Scripts</span></span>

### <a name="interaction-hint"></a><span data-ttu-id="c1e13-131">互動提示</span><span class="sxs-lookup"><span data-stu-id="c1e13-131">Interaction hint</span></span>

<span data-ttu-id="c1e13-132">`InteractionHint.cs`腳本提供用於觸發動畫的包裝函式功能，並讓您的工作機組淡化。</span><span class="sxs-lookup"><span data-stu-id="c1e13-132">The `InteractionHint.cs` script provides wrapper functionality for triggering animations and fades for the hand rig.</span></span>

#### <a name="how-to-set-up-an-interaction-hint"></a><span data-ttu-id="c1e13-133">如何設定互動提示</span><span class="sxs-lookup"><span data-stu-id="c1e13-133">How to set up an interaction hint</span></span>

<span data-ttu-id="c1e13-134">若要設定互動提示，建議使用提供的 prefabs "StaticHandCoachRoot_L. 預製專案" 和 "StaticHandCoachRoot_R. 預製專案"。</span><span class="sxs-lookup"><span data-stu-id="c1e13-134">To set up an interaction hint, it is recommended to use the provided prefabs “StaticHandCoachRoot_L.prefab” and “StaticHandCoachRoot_R.prefab”.</span></span> <span data-ttu-id="c1e13-135">此預製專案包含 InteractionHint 腳本和手邊的設備，以及適當的階層，以確保提供的提示動畫能如預期運作。</span><span class="sxs-lookup"><span data-stu-id="c1e13-135">This prefab contains the InteractionHint script and hand rig as well as the proper hierarchy to ensure that the provided hint animations work as intended.</span></span>
<span data-ttu-id="c1e13-136">否則，您必須使用 animator，將腳本放在 gameObject 一個上層的父層級上。</span><span class="sxs-lookup"><span data-stu-id="c1e13-136">Otherwise, you'll need to place the script on a gameObject one parent level up from your hand rig with animator.</span></span>

#### <a name="inspector-properties"></a><span data-ttu-id="c1e13-137">偵測器屬性</span><span class="sxs-lookup"><span data-stu-id="c1e13-137">Inspector properties</span></span>

- <span data-ttu-id="c1e13-138">**HideIfHandTracked** 此布林值指定在追蹤使用者的手時，是否應使用「手動追蹤」狀態來隱藏視覺效果。</span><span class="sxs-lookup"><span data-stu-id="c1e13-138">**HideIfHandTracked** This boolean specifies whether hand tracking state should be used to hide visuals when a user’s hands are being tracked.</span></span> <span data-ttu-id="c1e13-139">如果設定為 false，則只會使用腳本屬性 "customShouldHideVisuals" 來判斷是否要隱藏提示。</span><span class="sxs-lookup"><span data-stu-id="c1e13-139">If this is set to false, only the scripting property “customShouldHideVisuals” will be used to determine whether to hide the hint.</span></span>

- <span data-ttu-id="c1e13-140">**MinDelay** 這個屬性會指定顯示視覺效果的最小延遲。</span><span class="sxs-lookup"><span data-stu-id="c1e13-140">**MinDelay** This property specifies the minimum delay for showing the visuals.</span></span> <span data-ttu-id="c1e13-141">根據預設，如果未追蹤使用者的手中，則會在這幾秒後出現該手的視覺效果。</span><span class="sxs-lookup"><span data-stu-id="c1e13-141">By default, the visuals for the hand will appear after this many seconds if the user’s hands are not being tracked.</span></span>

- <span data-ttu-id="c1e13-142">**MaxDelay** 這個屬性會指定顯示視覺效果的最大延遲。</span><span class="sxs-lookup"><span data-stu-id="c1e13-142">**MaxDelay** This property specifies the maximum delay for showing the visuals.</span></span> <span data-ttu-id="c1e13-143">根據預設，即使正在追蹤使用者的手中，該手的視覺效果也會出現在這幾秒之後。</span><span class="sxs-lookup"><span data-stu-id="c1e13-143">By default, the visuals for the hand will appear after this many seconds even if the user’s hands are being tracked.</span></span>

- <span data-ttu-id="c1e13-144">**UseMaxTimer** 如果這個布林值設定為 false，它會停用最大計時器，並只允許在使用者的手離開時顯示手形提示，或自訂條件傳回 false。</span><span class="sxs-lookup"><span data-stu-id="c1e13-144">**UseMaxTimer** If this boolean is set to false, it disables the max timer and only allows the hand hint to be shown when the user’s hands are out of view, or the custom condition returns false.</span></span>

- <span data-ttu-id="c1e13-145">**重複** 這個屬性會控制當最小或最大計時器超過時，提示動畫的播放次數。</span><span class="sxs-lookup"><span data-stu-id="c1e13-145">**Repeats** This property controls how many times the hint animation plays when the min or max timer has passed.</span></span> <span data-ttu-id="c1e13-146">提示接著會隱藏並等候延遲。</span><span class="sxs-lookup"><span data-stu-id="c1e13-146">The hint then hides and waits for the delay again.</span></span>

- <span data-ttu-id="c1e13-147">**AutoActivate** 當這個布林值設定為 true 時，當腳本的 GameObject 在使用中，且腳本已啟用時，提示會自動執行計時器邏輯。</span><span class="sxs-lookup"><span data-stu-id="c1e13-147">**AutoActivate** When this boolean is set to true, the hint will automatically run through the timer logic when the GameObject of the script is active in the hierarchy and the script is enabled.</span></span> <span data-ttu-id="c1e13-148">如果您想要透過程式碼手動控制提示外觀和消失，則應該將此設定為 false。</span><span class="sxs-lookup"><span data-stu-id="c1e13-148">This should only be set to false if you intend to manually control the hint appearance and disappearance via code.</span></span>

- <span data-ttu-id="c1e13-149">**AnimationState** 當提示為作用中時，應播放之動畫狀態的名稱。</span><span class="sxs-lookup"><span data-stu-id="c1e13-149">**AnimationState** The name of the animation state that should play when the hint is active.</span></span> <span data-ttu-id="c1e13-150">這必須在 OnEnable 期間呼叫 StartHintLoop () 函式之前設定 (如果) 檢查 AutoActivate。</span><span class="sxs-lookup"><span data-stu-id="c1e13-150">This must be set before the StartHintLoop() function is called (during OnEnable if AutoActivate is checked).</span></span>

#### <a name="controlling-interactionhint-via-script"></a><span data-ttu-id="c1e13-151">透過腳本控制 InteractionHint</span><span class="sxs-lookup"><span data-stu-id="c1e13-151">Controlling InteractionHint via script</span></span>

- <span data-ttu-id="c1e13-152">**StartHintLoop** 如果 AutoActivate 旗標設定為 true，則此函式會啟動顯示/隱藏迴圈，否則會啟動 OnEnable。</span><span class="sxs-lookup"><span data-stu-id="c1e13-152">**StartHintLoop** This function starts the show/hide loop that otherwise starts OnEnable if the AutoActivate flag is set to true.</span></span>
- <span data-ttu-id="c1e13-153">**StopHintLoop** 如果目前沒有播放，此函式會呼叫淡出動畫狀態，然後停用顯示/隱藏迴圈，並將階層中非使用中的工作區設定為非作用中。</span><span class="sxs-lookup"><span data-stu-id="c1e13-153">**StopHintLoop** This function calls the fade out animation state if it is not currently playing, then will deactivate the show/hide loop and set the hand rig inactive in the hierarchy.</span></span>
- <span data-ttu-id="c1e13-154">**AnimationState** 這個字串會決定迴圈期間要播放的動畫狀態。</span><span class="sxs-lookup"><span data-stu-id="c1e13-154">**AnimationState** This string determines which animation state is played during the loop.</span></span> <span data-ttu-id="c1e13-155">您可以變更此字串來變更要播放的狀態，但是在呼叫 StopHintLoop 之後必須這樣做，而且您必須在變更狀態之後再次呼叫 StartHintLoop。</span><span class="sxs-lookup"><span data-stu-id="c1e13-155">You may change this string to change which state plays, but you must do so after calling StopHintLoop, and you must call StartHintLoop again after you have changed the state.</span></span>
- <span data-ttu-id="c1e13-156">**CustomShouldHideVisuals** 您可以使用自己的函式來設定此設定，當您想要隱藏手的視覺效果時，應該會傳回 true (請特別注意 MinMaxTimer，尤其是 max 參數) </span><span class="sxs-lookup"><span data-stu-id="c1e13-156">**CustomShouldHideVisuals** You can set this with your own function, which should return true when you want to hide the hand visuals (keep in mind the MinMaxTimer, specifically the max parameter)</span></span>

#### <a name="custom-animation-considerations"></a><span data-ttu-id="c1e13-157">自訂動畫的考慮</span><span class="sxs-lookup"><span data-stu-id="c1e13-157">Custom animation considerations</span></span>

<span data-ttu-id="c1e13-158">淡化的預設值為0.5 秒，因此為了與 rig 一起使用而建立的任何自訂動畫，都應為任何要傳達的有意義資訊的1.5 秒</span><span class="sxs-lookup"><span data-stu-id="c1e13-158">Fades are defaulted to 0.5 seconds, so any custom animations created for use with the rig should be 1.5 seconds minimum for any meaningful information to be conveyed</span></span>

<span data-ttu-id="c1e13-159">您可以藉由變更第二個主要畫面格的時間戳記來設定淡化長度，來調整所提供的預設淡入和淡出狀態、Fade_In 和 Fade_Out。</span><span class="sxs-lookup"><span data-stu-id="c1e13-159">The provided default fade in and fade out states, Fade_In and Fade_Out may be adjusted by changing the timestamp of the second keyframe to set the fade length.</span></span>

<span data-ttu-id="c1e13-160">Animator 和腳本的設定方式應該盡可能簡化安裝程式。</span><span class="sxs-lookup"><span data-stu-id="c1e13-160">The animator and script were set up in a way that should make setup as simple as possible.</span></span> <span data-ttu-id="c1e13-161">若要加入新的動畫狀態，只需匯入您的 fbx，確定動畫名稱是以相異名稱設定，然後將該動畫拖曳至 animator 中。</span><span class="sxs-lookup"><span data-stu-id="c1e13-161">To add new animation states, simply import your fbx, ensure the animation name is set with a distinct name, and drag that animation into the animator.</span></span>

### <a name="movetotarget"></a><span data-ttu-id="c1e13-162">MoveToTarget</span><span class="sxs-lookup"><span data-stu-id="c1e13-162">MoveToTarget</span></span>

<span data-ttu-id="c1e13-163">MoveToTarget .cs 腳本提供了一段時間，將手提示從追蹤位置移至目標位置的功能。</span><span class="sxs-lookup"><span data-stu-id="c1e13-163">The MoveToTarget.cs script provides functionality to move the hand hint from a tracking position to a target position over time.</span></span>

#### <a name="how-to-set-up-movetotarget"></a><span data-ttu-id="c1e13-164">如何設定 MoveToTarget</span><span class="sxs-lookup"><span data-stu-id="c1e13-164">How to set up MoveToTarget</span></span>

<span data-ttu-id="c1e13-165">提供的 prefabs "MovingHandCoachRoot_L. 預製專案" 和 "MovingHandCoachRoot_R. 預製專案" 包含其階層中的 MoveToTarget。</span><span class="sxs-lookup"><span data-stu-id="c1e13-165">The provided prefabs “MovingHandCoachRoot_L.prefab” and “MovingHandCoachRoot_R.prefab” contain a MoveToTarget in their hierarchies.</span></span> <span data-ttu-id="c1e13-166">如果您想要在自己的安裝程式上使用此腳本，您必須將它放在包含您的 rig Animator 的根 gameobject。</span><span class="sxs-lookup"><span data-stu-id="c1e13-166">If you want to use this script on your own setup, you need to place it on the root gameobject containing the Animator for your rig.</span></span>

#### <a name="inspector-properties"></a><span data-ttu-id="c1e13-167">偵測器屬性</span><span class="sxs-lookup"><span data-stu-id="c1e13-167">Inspector properties</span></span>

- <span data-ttu-id="c1e13-168">**TrackingObject** 使用您想要讓 rig 在開始其動作之前所要遵循的物件來設定此設定。</span><span class="sxs-lookup"><span data-stu-id="c1e13-168">**TrackingObject** Set this with the object you want the rig to follow before it starts its motion.</span></span> <span data-ttu-id="c1e13-169">建議您建立空白的 GameObject，並將它移至特定位置，以協助您找出追蹤。</span><span class="sxs-lookup"><span data-stu-id="c1e13-169">It is recommended to create an empty GameObject and move it to a specific position to help you pinpoint the tracking.</span></span>
- <span data-ttu-id="c1e13-170">**TargetObject** 使用您想要讓 rig 移至其移動期間的物件來設定此設定。</span><span class="sxs-lookup"><span data-stu-id="c1e13-170">**TargetObject** Set this with the object you want the rig to move to during its motion.</span></span> <span data-ttu-id="c1e13-171">建議您建立空白的 GameObject，並將它移至特定位置，以協助您找出追蹤。</span><span class="sxs-lookup"><span data-stu-id="c1e13-171">It is recommended to create an empty GameObject and move it to a specific position to help you pinpoint the tracking.</span></span>
- <span data-ttu-id="c1e13-172">**RootObject** 將此設定為追蹤與目標物件之間的共用父系，以便能夠正確計算相對位置。</span><span class="sxs-lookup"><span data-stu-id="c1e13-172">**RootObject** Set this to a shared parent between tracking and target object so that the relative positions can be calculated correctly.</span></span> <span data-ttu-id="c1e13-173">包含的預製專案在其階層中有追蹤和目標物件，但您可以將目標物件設定為預製專案以外的 gameObject，並將根物件變更為共用父系。</span><span class="sxs-lookup"><span data-stu-id="c1e13-173">The included prefab has both tracking and target objects in its hierarchy, but you can set the target object as a gameObject outside of the prefab and change the root object to a shared parent.</span></span>
- <span data-ttu-id="c1e13-174">**持續時間** 從 TrackingObject 到 TargetObject （以秒為單位）進行移動所需的 (時間長度（以) 秒為單位）。</span><span class="sxs-lookup"><span data-stu-id="c1e13-174">**Duration** The amount of time it should take (in seconds) to move from TrackingObject to TargetObject in seconds.</span></span>
- <span data-ttu-id="c1e13-175">**TargetOffset** 可調式位移，可讓 GameObject 到達正確的目標位置。</span><span class="sxs-lookup"><span data-stu-id="c1e13-175">**TargetOffset** A tunable offset to get the GameObject to arrive at the right target position.</span></span> <span data-ttu-id="c1e13-176">如果您的動畫在動畫期間包含位置位移，這就很有用。</span><span class="sxs-lookup"><span data-stu-id="c1e13-176">This is useful if your animation includes a position offset during the animation.</span></span>
- <span data-ttu-id="c1e13-177">**AnimationCurve** 這會預設為線性曲線，但您可以在啟動和停止移動路徑時，改變曲線以提供緩時/放大。</span><span class="sxs-lookup"><span data-stu-id="c1e13-177">**AnimationCurve** This is defaulted to a linear curve, but you can alter the curve to provide easing in/out when starting and stopping the motion path.</span></span>

#### <a name="controlling-movetotarget-via-script"></a><span data-ttu-id="c1e13-178">透過腳本控制 MoveToTarget</span><span class="sxs-lookup"><span data-stu-id="c1e13-178">Controlling MoveToTarget via script</span></span>

<span data-ttu-id="c1e13-179">在您的自訂腳本中，進行下列 () ，並在您想要讓設備在 TrackingObject 之後進行呼叫，然後在您想要讓設備的 MoveToTargetPosition 開始移動到 TargetObject 時，呼叫 () 。</span><span class="sxs-lookup"><span data-stu-id="c1e13-179">In your custom script, make a call to Follow() while you want the hand rig to be following the TrackingObject, then make a call to MoveToTargetPosition() when you want the hand rig to begin its motion to the TargetObject.</span></span>

#### <a name="controlling-movetotarget-via-animations"></a><span data-ttu-id="c1e13-180">透過動畫控制 MoveToTarget</span><span class="sxs-lookup"><span data-stu-id="c1e13-180">Controlling MoveToTarget via animations</span></span>

<span data-ttu-id="c1e13-181">在需要移動的動畫中，設定兩個事件：一個是呼叫後面的 () ，另一個則是呼叫 MoveToTargetPosition () 。</span><span class="sxs-lookup"><span data-stu-id="c1e13-181">In the animation that needs to move, set two events: one with a call to Follow() and one with a call to MoveToTargetPosition().</span></span> <span data-ttu-id="c1e13-182">您應該在第一個主要畫面格上設定下列各個，因為它會讓設備裝備符合您的 TrackingObject。</span><span class="sxs-lookup"><span data-stu-id="c1e13-182">Follow should be set on the first keyframe, since it causes the hand rig to follow your TrackingObject.</span></span> <span data-ttu-id="c1e13-183">MoveToTargetPosition 應該設定在您要讓 rig 開始移至目標的主要畫面上。</span><span class="sxs-lookup"><span data-stu-id="c1e13-183">MoveToTargetPosition should be set on the keyframe where you want the rig to begin moving to the target.</span></span> <span data-ttu-id="c1e13-184">這是在提供的 prefabs 中使用腳本功能的方式。</span><span class="sxs-lookup"><span data-stu-id="c1e13-184">This is how the script functionality is used in the provided prefabs.</span></span>

### <a name="rotatearoundpoint"></a><span data-ttu-id="c1e13-185">RotateAroundPoint</span><span class="sxs-lookup"><span data-stu-id="c1e13-185">RotateAroundPoint</span></span>

<span data-ttu-id="c1e13-186">RotateAroundPoint 可提供在一段時間內旋轉旋轉點提示的功能。</span><span class="sxs-lookup"><span data-stu-id="c1e13-186">The RotateAroundPoint.cs script provides functionality to rotate the hand hint around a pivot point over time.</span></span>

#### <a name="how-to-set-up-rotatearoundpoint"></a><span data-ttu-id="c1e13-187">如何設定 RotateAroundPoint</span><span class="sxs-lookup"><span data-stu-id="c1e13-187">How to set up RotateAroundPoint</span></span>

<span data-ttu-id="c1e13-188">提供的 prefabs "RotatingHandCoachRoot_L. 預製專案" 和 "RotatingHandCoachRoot_R. 預製專案" 包含其階層中的 RotateAroundPoint。</span><span class="sxs-lookup"><span data-stu-id="c1e13-188">The provided prefabs “RotatingHandCoachRoot_L.prefab” and “RotatingHandCoachRoot_R.prefab” contain a RotateAroundPoint in their hierarchies.</span></span> <span data-ttu-id="c1e13-189">如果您想要在自己的安裝程式上使用此腳本，您必須將它放在包含您的 rig Animator 的根 gameobject。</span><span class="sxs-lookup"><span data-stu-id="c1e13-189">If you want to use this script on your own setup, you need to place it on the root gameobject containing the Animator for your rig.</span></span>

#### <a name="inspector-properties"></a><span data-ttu-id="c1e13-190">偵測器屬性</span><span class="sxs-lookup"><span data-stu-id="c1e13-190">Inspector properties</span></span>

- <span data-ttu-id="c1e13-191">**CenteredParent** 使用您想要讓 rig 進行資料透視的父物件來設定此設定。</span><span class="sxs-lookup"><span data-stu-id="c1e13-191">**CenteredParent** Set this with the parent object you want the rig to pivot around.</span></span>
- <span data-ttu-id="c1e13-192">**InverseParent** 將此設定為父代，以將反向旋轉至 centeredParent，以保持方向相同。</span><span class="sxs-lookup"><span data-stu-id="c1e13-192">**InverseParent** Set this with the parent to rotate inverse to centeredParent in order to keep the hand orientation the same.</span></span> <span data-ttu-id="c1e13-193">一般來說，這會是具有 InteractionHint 腳本的父物件。</span><span class="sxs-lookup"><span data-stu-id="c1e13-193">In general, this will be the parent object with the InteractionHint script on it.</span></span>
- <span data-ttu-id="c1e13-194">**PivotPosition** 將此設定為您希望提示開始移動的時間點。</span><span class="sxs-lookup"><span data-stu-id="c1e13-194">**PivotPosition** Set this to a point where you want the hint to start movement at.</span></span>
- <span data-ttu-id="c1e13-195">**持續時間** 以秒為單位來旋轉 CenteredParent 所需的 (時間量) （以秒為單位）。</span><span class="sxs-lookup"><span data-stu-id="c1e13-195">**Duration** The amount of time it should take (in seconds) to rotate around the CenteredParent.</span></span>
- <span data-ttu-id="c1e13-196">**AnimationCurve** 這會預設為線性曲線，但您可以在啟動和停止移動路徑時，改變曲線以提供緩時/放大。</span><span class="sxs-lookup"><span data-stu-id="c1e13-196">**AnimationCurve** This is defaulted to a linear curve, but you can alter the curve to provide easing in/out when starting and stopping the motion path.</span></span>
- <span data-ttu-id="c1e13-197">**RotationVector** 沿著每個軸旋轉的度數。</span><span class="sxs-lookup"><span data-stu-id="c1e13-197">**RotationVector** How many degrees to rotate along each axis.</span></span>

#### <a name="controlling-rotatearoundpoint-via-script"></a><span data-ttu-id="c1e13-198">透過腳本控制 RotateAroundPoint</span><span class="sxs-lookup"><span data-stu-id="c1e13-198">Controlling RotateAroundPoint via script</span></span>

<span data-ttu-id="c1e13-199">在您的自訂腳本中，當您想要讓設備在 CenteredParent 周圍開始輪替時，請呼叫 RotateToTarget () 。</span><span class="sxs-lookup"><span data-stu-id="c1e13-199">In your custom script, make a call to RotateToTarget() when you want the hand rig to begin its rotation around the CenteredParent.</span></span> <span data-ttu-id="c1e13-200">當您想要重設為原始 PivotPosition 的位置時，請呼叫 ResetAndDeterminePivot () 。</span><span class="sxs-lookup"><span data-stu-id="c1e13-200">When you want the position to reset to the original PivotPosition, make a call to ResetAndDeterminePivot().</span></span>

#### <a name="controlling-rotatearoundpoint-via-animations"></a><span data-ttu-id="c1e13-201">透過動畫控制 RotateAroundPoint</span><span class="sxs-lookup"><span data-stu-id="c1e13-201">Controlling RotateAroundPoint via animations</span></span>

<span data-ttu-id="c1e13-202">在需要移動的動畫中，設定兩個事件：一個是呼叫 ResetAndDeterminePivot () ，另一個呼叫 RotateToTarget () 。</span><span class="sxs-lookup"><span data-stu-id="c1e13-202">In the animation that needs to move, set two events: one with a call to ResetAndDeterminePivot() and one with a call to RotateToTarget().</span></span> <span data-ttu-id="c1e13-203">ResetAndDeterminePivot 應該在第一個主要畫面格上設定，因為它會讓裝備的設備重設為 PivotPosition。</span><span class="sxs-lookup"><span data-stu-id="c1e13-203">ResetAndDeterminePivot should be set on the first keyframe, since it causes the hand rig to reset to the PivotPosition.</span></span> <span data-ttu-id="c1e13-204">RotateToTarget 應該設定在您要讓 rig 開始在 CenteredParent 周圍旋轉的主要畫面上。</span><span class="sxs-lookup"><span data-stu-id="c1e13-204">RotateToTarget should be set on the keyframe where you want the rig to begin rotating around the CenteredParent.</span></span> <span data-ttu-id="c1e13-205">這是在提供的 prefabs 中使用腳本功能的方式。</span><span class="sxs-lookup"><span data-stu-id="c1e13-205">This is how the script functionality is used in the provided prefabs.</span></span>
