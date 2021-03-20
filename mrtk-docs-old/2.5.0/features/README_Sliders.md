---
title: README_Slider
description: 滑杆 MRTK 簡介
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、滑杆、
ms.openlocfilehash: af94da6e72a6dc87adef27d6f4a055b522f68155
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104694895"
---
# <a name="sliders"></a><span data-ttu-id="e04d4-104">滑桿</span><span class="sxs-lookup"><span data-stu-id="e04d4-104">Sliders</span></span>

![滑杆範例](Images/Slider/MRTK_UX_Slider_Main.jpg)

<span data-ttu-id="e04d4-106">滑杆是 UI 元件，可讓您藉由移動軌跡上的滑杆來持續變更值。目前，您可以直接或距離，直接抓取滑杆來移動縮小滑杆。</span><span class="sxs-lookup"><span data-stu-id="e04d4-106">Sliders are UI components that allow you to continuously change a value by moving a slider on a track. Currently the Pinch Slider can be moved by directly grabbing the slider, either directly or at a distance.</span></span> <span data-ttu-id="e04d4-107">滑杆適用于 AR 和 VR，使用動作控制器、手或手勢 + 語音。</span><span class="sxs-lookup"><span data-stu-id="e04d4-107">Sliders work on AR and VR, using motion controllers, hands, or Gesture + Voice.</span></span>

## <a name="example-scene"></a><span data-ttu-id="e04d4-108">範例場景</span><span class="sxs-lookup"><span data-stu-id="e04d4-108">Example scene</span></span>

<span data-ttu-id="e04d4-109">您可以在的 **SliderExample** 場景中找到範例 `MRTK/Examples/Demos/UX/Slider/Scenes/` 。</span><span class="sxs-lookup"><span data-stu-id="e04d4-109">You can find examples in the **SliderExample** scene under `MRTK/Examples/Demos/UX/Slider/Scenes/`.</span></span>

## <a name="how-to-use-sliders"></a><span data-ttu-id="e04d4-110">如何使用滑杆</span><span class="sxs-lookup"><span data-stu-id="e04d4-110">How to use sliders</span></span>

<span data-ttu-id="e04d4-111">將 **PinchSlider** 預製專案拖放到場景階層中。</span><span class="sxs-lookup"><span data-stu-id="e04d4-111">Drag and drop the **PinchSlider** prefab into the scene hierarchy.</span></span> <span data-ttu-id="e04d4-112">如果您想要修改或建立自己的滑杆，請務必執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="e04d4-112">If you want to modify or create your own slider, remember to do the following:</span></span>

- <span data-ttu-id="e04d4-113">請確定您的 thumb 物件有其碰撞器。</span><span class="sxs-lookup"><span data-stu-id="e04d4-113">Make sure your that your thumb object has a collider on it.</span></span> <span data-ttu-id="e04d4-114">在 PinchSlider 預製專案中，碰撞器已開啟 `SliderThumb/Button_AnimationContainer/Slider_Button`</span><span class="sxs-lookup"><span data-stu-id="e04d4-114">In the PinchSlider prefab, the collider is on `SliderThumb/Button_AnimationContainer/Slider_Button`</span></span>
- <span data-ttu-id="e04d4-115">如果您想要能夠抓取靠近的滑杆，請確定包含碰撞器的物件也有近乎互動的 Grabbable 元件。</span><span class="sxs-lookup"><span data-stu-id="e04d4-115">Make sure that the object containing the collider also has a Near Interaction Grabbable component on it, if you want to be able to grab the slider near.</span></span>

<span data-ttu-id="e04d4-116">我們也建議使用下列階層</span><span class="sxs-lookup"><span data-stu-id="e04d4-116">We also recommend using the following hierarchy</span></span>

- <span data-ttu-id="e04d4-117">PinchSlider-包含 sliderComponent</span><span class="sxs-lookup"><span data-stu-id="e04d4-117">PinchSlider - Contains the sliderComponent</span></span>
  - <span data-ttu-id="e04d4-118">SliderThumb-包含可移動的拇指</span><span class="sxs-lookup"><span data-stu-id="e04d4-118">SliderThumb - Contains the movable thumb</span></span>
  - <span data-ttu-id="e04d4-119">TrackVisuals-包含曲目和任何其他視覺效果</span><span class="sxs-lookup"><span data-stu-id="e04d4-119">TrackVisuals - Containing the track and any other visuals</span></span>
  - <span data-ttu-id="e04d4-120">OtherVisuals-包含任何其他視覺效果</span><span class="sxs-lookup"><span data-stu-id="e04d4-120">OtherVisuals - Containing any other visuals</span></span>

## <a name="slider-events"></a><span data-ttu-id="e04d4-121">滑杆事件</span><span class="sxs-lookup"><span data-stu-id="e04d4-121">Slider events</span></span>

<span data-ttu-id="e04d4-122">滑杆會公開下列事件：</span><span class="sxs-lookup"><span data-stu-id="e04d4-122">Sliders expose the following events:</span></span>

- <span data-ttu-id="e04d4-123">OnValueUpdated-每當滑杆值變更時呼叫</span><span class="sxs-lookup"><span data-stu-id="e04d4-123">OnValueUpdated - Called whenever the slider value changes</span></span>
- <span data-ttu-id="e04d4-124">OnInteractionStarted-當使用者抓取滑杆時呼叫</span><span class="sxs-lookup"><span data-stu-id="e04d4-124">OnInteractionStarted - Called when the user grabs the slider</span></span>
- <span data-ttu-id="e04d4-125">OnInteractionEnded-當使用者放開滑杆時呼叫</span><span class="sxs-lookup"><span data-stu-id="e04d4-125">OnInteractionEnded - Called when the user releases the slider</span></span>
- <span data-ttu-id="e04d4-126">OnHoverEntered-當使用者的手形/控制器停留在滑杆上時，使用接近或遠的互動來呼叫。</span><span class="sxs-lookup"><span data-stu-id="e04d4-126">OnHoverEntered - Called when the user's hand / controller hovers over the slider, using either near or far interaction.</span></span>
- <span data-ttu-id="e04d4-127">OnHoverExited-當使用者的手形/控制器不再靠近滑杆時呼叫。</span><span class="sxs-lookup"><span data-stu-id="e04d4-127">OnHoverExited - Called when the user's hand / controller is no longer near the slider.</span></span>

## <a name="configuring-slider-bound-and-axis"></a><span data-ttu-id="e04d4-128">設定滑杆系結和軸</span><span class="sxs-lookup"><span data-stu-id="e04d4-128">Configuring slider bound and axis</span></span>

<span data-ttu-id="e04d4-129">您可以藉由移動場景中的控點，直接移動滑杆的起點和終點：</span><span class="sxs-lookup"><span data-stu-id="e04d4-129">You can directly move the starting and end points of the slider by moving the handles in the Scene:</span></span>

![滑杆設定](Images/Sliders/MRTK_Sliders_Setup.png)

<span data-ttu-id="e04d4-131">您也可以透過 _滑杆軸_ 欄位，在滑杆的 [本機空間]) 中指定軸 (</span><span class="sxs-lookup"><span data-stu-id="e04d4-131">You can also specify the axis (in local space) of the slider via the _Slider Axis_ field</span></span>

<span data-ttu-id="e04d4-132">如果您無法使用控制碼，您可以改為透過 [ _滑杆開始距離_ ] 和 [ _滑杆結束距離_ ] 欄位來指定滑杆的起點和終點。</span><span class="sxs-lookup"><span data-stu-id="e04d4-132">If you cannot use the handles, you can instead specify the start and end points of the slider via the _Slider Start Distance_ and _Slider End Distance_ fields.</span></span> <span data-ttu-id="e04d4-133">這些會將滑杆的開始/結束位置指定為距離滑杆中心的距離（以區域座標表示）。</span><span class="sxs-lookup"><span data-stu-id="e04d4-133">These specify start / end position of slider as a distance from the slider's center, in local coordinates.</span></span> <span data-ttu-id="e04d4-134">這表示一旦您依需要設定滑杆的開始和結束距離，您可以將滑杆調整為較小或更大，而不需要更新開始和結束距離。</span><span class="sxs-lookup"><span data-stu-id="e04d4-134">This means that once you set the slider start and end distances as you want them, you can scale the slider to be smaller or larger without needing to update the start and end distances.</span></span>

## <a name="inspector-properties"></a><span data-ttu-id="e04d4-135">偵測器屬性</span><span class="sxs-lookup"><span data-stu-id="e04d4-135">Inspector properties</span></span>

<span data-ttu-id="e04d4-136">**Thumb 根目錄** 包含滑杆 thumb 的 gameobject。</span><span class="sxs-lookup"><span data-stu-id="e04d4-136">**Thumb Root** The gameobject that contains the slider thumb.</span></span>

<span data-ttu-id="e04d4-137">**滑杆值** 滑杆的值。</span><span class="sxs-lookup"><span data-stu-id="e04d4-137">**Slider Value** The value of the slider.</span></span>

<span data-ttu-id="e04d4-138">**追蹤視覺效果** Gameobject，其中包含沿著滑杆的所需追蹤視覺效果。</span><span class="sxs-lookup"><span data-stu-id="e04d4-138">**Track Visuals** The gameobject that contains the desired track visuals that goes along the slider.</span></span>

<span data-ttu-id="e04d4-139">**刻度標記** Gameobject，其中包含沿著滑杆的所需刻度標記。</span><span class="sxs-lookup"><span data-stu-id="e04d4-139">**Tick Marks** The gameobject that contains the desired tick marks that goes along the slider.</span></span>

<span data-ttu-id="e04d4-140">**Thumb 視覺效果** Gameobject，其中包含沿著滑杆的所需 thumb 視覺效果。</span><span class="sxs-lookup"><span data-stu-id="e04d4-140">**Thumb Visuals** The gameobject that contains the desired thumb visual that goes along the slider.</span></span>

<span data-ttu-id="e04d4-141">**滑杆軸** 滑杆沿著的軸移動。</span><span class="sxs-lookup"><span data-stu-id="e04d4-141">**Slider Axis** The axis the slider moves along.</span></span>

<span data-ttu-id="e04d4-142">**滑杆開始距離** 滑杆播放軌的起點，以當地空間單位為中心沿著滑杆軸的距離。</span><span class="sxs-lookup"><span data-stu-id="e04d4-142">**Slider Start Distance** Where the slider track starts, as distance from center along slider axis, in local space units.</span></span>

<span data-ttu-id="e04d4-143">**滑杆結束距離** 滑杆軌結束的位置，以當地空間單位為中心沿著滑杆軸的距離。</span><span class="sxs-lookup"><span data-stu-id="e04d4-143">**Slider End Distance** Where the slider track ends, as distance from center along slider axis, in local space units.</span></span>

<span data-ttu-id="e04d4-144">當使用者更新編輯器中的滑杆軸值時，如果指定了追蹤視覺效果或刻度視覺效果，則會更新其轉換。</span><span class="sxs-lookup"><span data-stu-id="e04d4-144">When user updates the slider axis value in editor then if Track Visuals or Tick Visuals are specified then their transform is updated.</span></span>
<span data-ttu-id="e04d4-145">具體而言，其本機位置會重設，而其本機旋轉會設定為符合滑杆軸的方向。</span><span class="sxs-lookup"><span data-stu-id="e04d4-145">Specifically, their local position is reset and their local rotation is set to match the Slider Axis orientation.</span></span>
<span data-ttu-id="e04d4-146">未修改其規模。</span><span class="sxs-lookup"><span data-stu-id="e04d4-146">Their scale isn't modified.</span></span>
<span data-ttu-id="e04d4-147">如果刻度具有方格物件集合元件，則版面配置和 CellWidth 或 CellHeight 會隨之更新，以符合滑杆軸。</span><span class="sxs-lookup"><span data-stu-id="e04d4-147">If Tick Marks have a Grid Object Collection component then the Layout and CellWidth or CellHeight is updated accordingly to match the Slider Axis.</span></span>
