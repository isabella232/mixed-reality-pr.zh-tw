---
title: 設定界限視覺效果
description: 在 MRTK 中設定界限系統的詳細資料
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、界限系統、
ms.openlocfilehash: 77bdaedb60700bac27643ae718c795c02e5ee7e7
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177096"
---
# <a name="configuring-boundary-visualization"></a><span data-ttu-id="51fbb-104">設定界限視覺效果</span><span class="sxs-lookup"><span data-stu-id="51fbb-104">Configuring boundary visualization</span></span>

<span data-ttu-id="51fbb-105">*界限視覺效果設定檔* 提供的選項可用來設定界限系統的視覺效果美學和其他相關參數。</span><span class="sxs-lookup"><span data-stu-id="51fbb-105">The *Boundary Visualization Profile* provides options for configuring the visual aesthetics and other related parameters for the Boundary system.</span></span> <span data-ttu-id="51fbb-106">界限視覺效果會附加至場景中的 Mixed Reality Playspace 物件，並隨使用者傳送。</span><span class="sxs-lookup"><span data-stu-id="51fbb-106">Boundary visualizations are attached to the Mixed Reality Playspace object in the scene and teleport with the user.</span></span>

## <a name="general-settings"></a><span data-ttu-id="51fbb-107">一般設定</span><span class="sxs-lookup"><span data-stu-id="51fbb-107">General settings</span></span>

![界限視覺效果的一般設定](../images/boundary/BoundaryVisualizationGeneralSettings.png)

### <a name="boundary-height"></a><span data-ttu-id="51fbb-109">界限高度</span><span class="sxs-lookup"><span data-stu-id="51fbb-109">Boundary height</span></span>

<span data-ttu-id="51fbb-110">界限高度表示應該呈現邊界上限之樓層平面的距離。</span><span class="sxs-lookup"><span data-stu-id="51fbb-110">The boundary height indicates the distance above the floor plane at which the boundary ceiling should be rendered.</span></span> <span data-ttu-id="51fbb-111">預設值為3個計量。</span><span class="sxs-lookup"><span data-stu-id="51fbb-111">The default value is 3 meters.</span></span>

## <a name="floor-settings"></a><span data-ttu-id="51fbb-112">樓層設定</span><span class="sxs-lookup"><span data-stu-id="51fbb-112">Floor settings</span></span>

![界限視覺效果樓層設定](../images/boundary/BoundaryVisualizationFloorSettings.png)

<span data-ttu-id="51fbb-114">**顯示**</span><span class="sxs-lookup"><span data-stu-id="51fbb-114">**Show**</span></span>

<span data-ttu-id="51fbb-115">指出是否要建立 floor 平面，並將其加入場景中。</span><span class="sxs-lookup"><span data-stu-id="51fbb-115">Indicates whether or not a floor plane is to be created and added to the scene.</span></span> <span data-ttu-id="51fbb-116">預設值為 true。</span><span class="sxs-lookup"><span data-stu-id="51fbb-116">The default value is true.</span></span>

<span data-ttu-id="51fbb-117">**Material**</span><span class="sxs-lookup"><span data-stu-id="51fbb-117">**Material**</span></span>

<span data-ttu-id="51fbb-118">指出建立 floor 平面時應該使用的材質。</span><span class="sxs-lookup"><span data-stu-id="51fbb-118">Indicates the material that should be used when creating the floor plane.</span></span>

<span data-ttu-id="51fbb-119">**調整**</span><span class="sxs-lookup"><span data-stu-id="51fbb-119">**Scale**</span></span>

<span data-ttu-id="51fbb-120">表示要建立之樓層平面的大小（以量值為單位）。</span><span class="sxs-lookup"><span data-stu-id="51fbb-120">Indicates the size, in meters, of the floor plane to be created.</span></span> <span data-ttu-id="51fbb-121">預設小數位數為3計量 x 3 計量方塊。</span><span class="sxs-lookup"><span data-stu-id="51fbb-121">The default scale is a 3 meter x 3 meter square.</span></span>

<span data-ttu-id="51fbb-122">**實體層**</span><span class="sxs-lookup"><span data-stu-id="51fbb-122">**Physics Layer**</span></span>

<span data-ttu-id="51fbb-123">應設定 floor 平面的圖層。</span><span class="sxs-lookup"><span data-stu-id="51fbb-123">The layer on which the floor plane should be set.</span></span> <span data-ttu-id="51fbb-124">預設值為 *預設* 的圖層。</span><span class="sxs-lookup"><span data-stu-id="51fbb-124">The default value is the *Default* layer.</span></span>

## <a name="play-area-settings"></a><span data-ttu-id="51fbb-125">播放區域設定</span><span class="sxs-lookup"><span data-stu-id="51fbb-125">Play area settings</span></span>

![界限視覺效果播放區域設定](../images/boundary/BoundaryVisualizationPlayAreaSettings.png)

<span data-ttu-id="51fbb-127">**顯示**</span><span class="sxs-lookup"><span data-stu-id="51fbb-127">**Show**</span></span>

<span data-ttu-id="51fbb-128">指出是否要建立播放區域矩形並將其加入場景中。</span><span class="sxs-lookup"><span data-stu-id="51fbb-128">Indicates whether or not a play area rectangle is be created and added to the scene.</span></span> <span data-ttu-id="51fbb-129">預設值為 true。</span><span class="sxs-lookup"><span data-stu-id="51fbb-129">The default value is true.</span></span>

<span data-ttu-id="51fbb-130">**Material**</span><span class="sxs-lookup"><span data-stu-id="51fbb-130">**Material**</span></span>

<span data-ttu-id="51fbb-131">指出建立播放區域物件時應使用的材質。</span><span class="sxs-lookup"><span data-stu-id="51fbb-131">Indicates the material that should be used when creating the play area object.</span></span>

<span data-ttu-id="51fbb-132">**實體層**</span><span class="sxs-lookup"><span data-stu-id="51fbb-132">**Physics Layer**</span></span>

<span data-ttu-id="51fbb-133">應設定播放區域的圖層。</span><span class="sxs-lookup"><span data-stu-id="51fbb-133">The layer on which the play area should be set.</span></span> <span data-ttu-id="51fbb-134">預設值為 [ *忽略 Raycast* 圖層]。</span><span class="sxs-lookup"><span data-stu-id="51fbb-134">The default value is the *Ignore Raycast* layer.</span></span>

## <a name="tracked-area-settings"></a><span data-ttu-id="51fbb-135">追蹤區域設定</span><span class="sxs-lookup"><span data-stu-id="51fbb-135">Tracked area settings</span></span>

![界限視覺效果追蹤區域設定](../images/boundary/BoundaryVisualizationTrackedAreaSettings.png)

<span data-ttu-id="51fbb-137">**顯示**</span><span class="sxs-lookup"><span data-stu-id="51fbb-137">**Show**</span></span>

<span data-ttu-id="51fbb-138">指出是否要建立追蹤區域的外框，並將其加入場景中。</span><span class="sxs-lookup"><span data-stu-id="51fbb-138">Indicates whether or not the outline of the tracked area is be created and added to the scene.</span></span> <span data-ttu-id="51fbb-139">預設值為 true。</span><span class="sxs-lookup"><span data-stu-id="51fbb-139">The default value is true.</span></span>

<span data-ttu-id="51fbb-140">**Material**</span><span class="sxs-lookup"><span data-stu-id="51fbb-140">**Material**</span></span>

<span data-ttu-id="51fbb-141">表示建立追蹤區域外框時應該使用的材質。</span><span class="sxs-lookup"><span data-stu-id="51fbb-141">Indicates the material that should be used when creating the tracked area outline.</span></span>

<span data-ttu-id="51fbb-142">**實體層**</span><span class="sxs-lookup"><span data-stu-id="51fbb-142">**Physics Layer**</span></span>

<span data-ttu-id="51fbb-143">應設定追蹤區域的圖層。</span><span class="sxs-lookup"><span data-stu-id="51fbb-143">The layer on which the tracked area should be sets.</span></span> <span data-ttu-id="51fbb-144">預設值為 [ *忽略 Raycast* 圖層]。</span><span class="sxs-lookup"><span data-stu-id="51fbb-144">The default value is the *Ignore Raycast* layer.</span></span>

## <a name="boundary-wall-settings"></a><span data-ttu-id="51fbb-145">界限牆設定</span><span class="sxs-lookup"><span data-stu-id="51fbb-145">Boundary wall settings</span></span>

![界限視覺效果邊界牆設定](../images/boundary/BoundaryVisualizationWallSettings.png)

<span data-ttu-id="51fbb-147">**顯示**</span><span class="sxs-lookup"><span data-stu-id="51fbb-147">**Show**</span></span>

<span data-ttu-id="51fbb-148">指出是否要建立界限牆平面，並將其加入場景中。</span><span class="sxs-lookup"><span data-stu-id="51fbb-148">Indicates whether or not boundary wall planes are to be created and added to the scene.</span></span> <span data-ttu-id="51fbb-149">預設值為 false。</span><span class="sxs-lookup"><span data-stu-id="51fbb-149">The default value is false.</span></span>

<span data-ttu-id="51fbb-150">**Material**</span><span class="sxs-lookup"><span data-stu-id="51fbb-150">**Material**</span></span>

<span data-ttu-id="51fbb-151">指出建立邊界牆平面時應該使用的材質。</span><span class="sxs-lookup"><span data-stu-id="51fbb-151">Indicates the material that should be used when creating the boundary wall planes.</span></span>

<span data-ttu-id="51fbb-152">**實體層**</span><span class="sxs-lookup"><span data-stu-id="51fbb-152">**Physics Layer**</span></span>

<span data-ttu-id="51fbb-153">應設定界限牆的圖層。</span><span class="sxs-lookup"><span data-stu-id="51fbb-153">The layer on which the boundary walls should be set.</span></span> <span data-ttu-id="51fbb-154">預設值為 [ *忽略 Raycast* 圖層]。</span><span class="sxs-lookup"><span data-stu-id="51fbb-154">The default value is the *Ignore Raycast* layer.</span></span>

> [!NOTE]
> <span data-ttu-id="51fbb-155">將界限牆元件設定為 [ *略過 Raycast* ] 以外的實體層，可能會讓使用者無法與場景內的物件互動。</span><span class="sxs-lookup"><span data-stu-id="51fbb-155">Setting the boundary wall component to a physics layer other than *Ignore Raycast* may prevent users from interacting with objects within the scene.</span></span>

## <a name="boundary-ceiling-settings"></a><span data-ttu-id="51fbb-156">界限上限設定</span><span class="sxs-lookup"><span data-stu-id="51fbb-156">Boundary ceiling settings</span></span>

![界限視覺效果邊界上限設定](../images/boundary/BoundaryVisualizationCeilingSettings.png)

<span data-ttu-id="51fbb-158">**顯示**</span><span class="sxs-lookup"><span data-stu-id="51fbb-158">**Show**</span></span>

<span data-ttu-id="51fbb-159">指出是否要建立界限上限平面，並將其加入場景中。</span><span class="sxs-lookup"><span data-stu-id="51fbb-159">Indicates whether or not a boundary ceiling plane is to be created and added to the scene.</span></span> <span data-ttu-id="51fbb-160">預設值為 false。</span><span class="sxs-lookup"><span data-stu-id="51fbb-160">The default value is false.</span></span>

<span data-ttu-id="51fbb-161">**Material**</span><span class="sxs-lookup"><span data-stu-id="51fbb-161">**Material**</span></span>

<span data-ttu-id="51fbb-162">指出建立界限上限平面時應使用的材質。</span><span class="sxs-lookup"><span data-stu-id="51fbb-162">Indicates the material that should be used when creating the boundary ceiling plane.</span></span>

<span data-ttu-id="51fbb-163">**實體層**</span><span class="sxs-lookup"><span data-stu-id="51fbb-163">**Physics Layer**</span></span>

<span data-ttu-id="51fbb-164">應設定界限牆的圖層。</span><span class="sxs-lookup"><span data-stu-id="51fbb-164">The layer on which the boundary walls should be set.</span></span> <span data-ttu-id="51fbb-165">預設值為 [ *忽略 Raycast* 圖層]。</span><span class="sxs-lookup"><span data-stu-id="51fbb-165">The default value is the *Ignore Raycast* layer.</span></span>

> [!NOTE]
> <span data-ttu-id="51fbb-166">將界限上限元件設定為 [ *略過 Raycast* ] 以外的實體層，可能會讓使用者無法與場景內的物件互動。</span><span class="sxs-lookup"><span data-stu-id="51fbb-166">Setting the boundary ceiling component to a physics layer other than *Ignore Raycast* may prevent users from interacting with objects within the scene.</span></span>

## <a name="see-also"></a><span data-ttu-id="51fbb-167">另請參閱</span><span class="sxs-lookup"><span data-stu-id="51fbb-167">See also</span></span>

- [<span data-ttu-id="51fbb-168">界限 API 檔</span><span class="sxs-lookup"><span data-stu-id="51fbb-168">Boundary API documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.Boundary)
- [<span data-ttu-id="51fbb-169">界限系統</span><span class="sxs-lookup"><span data-stu-id="51fbb-169">Boundary System</span></span>](boundary-system-getting-started.md)
