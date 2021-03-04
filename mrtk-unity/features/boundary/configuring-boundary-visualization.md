---
title: ConfiguringBoundaryVisualization
description: 在 MRTK 中設定界限系統的詳細資料
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、界限系統、
ms.openlocfilehash: e118359bf5faf4f198d1ed2a59329e585c547fad
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/03/2021
ms.locfileid: "101780058"
---
# <a name="configuring-the-boundary-visualization"></a><span data-ttu-id="9ecd8-104">設定界限視覺效果</span><span class="sxs-lookup"><span data-stu-id="9ecd8-104">Configuring the boundary visualization</span></span>

<span data-ttu-id="9ecd8-105">*界限視覺效果設定檔* 提供的選項可用來設定界限系統的視覺效果美學和其他相關參數。</span><span class="sxs-lookup"><span data-stu-id="9ecd8-105">The *Boundary Visualization Profile* provides options for configuring the visual aesthetics and other related parameters for the Boundary system.</span></span> <span data-ttu-id="9ecd8-106">界限視覺效果會附加至場景中的 Mixed Reality Playspace 物件，並隨使用者傳送。</span><span class="sxs-lookup"><span data-stu-id="9ecd8-106">Boundary visualizations are attached to the Mixed Reality Playspace object in the scene and teleport with the user.</span></span>

## <a name="general-settings"></a><span data-ttu-id="9ecd8-107">一般設定</span><span class="sxs-lookup"><span data-stu-id="9ecd8-107">General settings</span></span>

![界限視覺效果一般設定](../images/boundary/BoundaryVisualizationGeneralSettings.png)

### <a name="boundary-height"></a><span data-ttu-id="9ecd8-109">界限高度</span><span class="sxs-lookup"><span data-stu-id="9ecd8-109">Boundary height</span></span>

<span data-ttu-id="9ecd8-110">界限高度表示應該呈現邊界上限之樓層平面的距離。</span><span class="sxs-lookup"><span data-stu-id="9ecd8-110">The boundary height indicates the distance above the floor plane at which the boundary ceiling should be rendered.</span></span> <span data-ttu-id="9ecd8-111">預設值為3個計量。</span><span class="sxs-lookup"><span data-stu-id="9ecd8-111">The default value is 3 meters.</span></span>

## <a name="floor-settings"></a><span data-ttu-id="9ecd8-112">樓層設定</span><span class="sxs-lookup"><span data-stu-id="9ecd8-112">Floor settings</span></span>

![界限視覺效果樓層設定](../images/boundary/BoundaryVisualizationFloorSettings.png)

<span data-ttu-id="9ecd8-114">**顯示**</span><span class="sxs-lookup"><span data-stu-id="9ecd8-114">**Show**</span></span>

<span data-ttu-id="9ecd8-115">指出是否要建立 floor 平面，並將其加入場景中。</span><span class="sxs-lookup"><span data-stu-id="9ecd8-115">Indicates whether or not a floor plane is to be created and added to the scene.</span></span> <span data-ttu-id="9ecd8-116">預設值為 true。</span><span class="sxs-lookup"><span data-stu-id="9ecd8-116">The default value is true.</span></span>

<span data-ttu-id="9ecd8-117">**Material**</span><span class="sxs-lookup"><span data-stu-id="9ecd8-117">**Material**</span></span>

<span data-ttu-id="9ecd8-118">指出建立 floor 平面時應該使用的材質。</span><span class="sxs-lookup"><span data-stu-id="9ecd8-118">Indicates the material that should be used when creating the floor plane.</span></span>

<span data-ttu-id="9ecd8-119">**縮放**</span><span class="sxs-lookup"><span data-stu-id="9ecd8-119">**Scale**</span></span>

<span data-ttu-id="9ecd8-120">表示要建立之樓層平面的大小（以量值為單位）。</span><span class="sxs-lookup"><span data-stu-id="9ecd8-120">Indicates the size, in meters, of the floor plane to be created.</span></span> <span data-ttu-id="9ecd8-121">預設小數位數為3計量 x 3 計量方塊。</span><span class="sxs-lookup"><span data-stu-id="9ecd8-121">The default scale is a 3 meter x 3 meter square.</span></span>

<span data-ttu-id="9ecd8-122">**實體層**</span><span class="sxs-lookup"><span data-stu-id="9ecd8-122">**Physics Layer**</span></span>

<span data-ttu-id="9ecd8-123">應設定 floor 平面的圖層。</span><span class="sxs-lookup"><span data-stu-id="9ecd8-123">The layer on which the floor plane should be set.</span></span> <span data-ttu-id="9ecd8-124">預設值為 *預設* 的圖層。</span><span class="sxs-lookup"><span data-stu-id="9ecd8-124">The default value is the *Default* layer.</span></span>

## <a name="play-area-settings"></a><span data-ttu-id="9ecd8-125">播放區域設定</span><span class="sxs-lookup"><span data-stu-id="9ecd8-125">Play area settings</span></span>

![界限視覺效果播放區域設定](../images/boundary/BoundaryVisualizationPlayAreaSettings.png)

<span data-ttu-id="9ecd8-127">**顯示**</span><span class="sxs-lookup"><span data-stu-id="9ecd8-127">**Show**</span></span>

<span data-ttu-id="9ecd8-128">指出是否要建立播放區域矩形並將其加入場景中。</span><span class="sxs-lookup"><span data-stu-id="9ecd8-128">Indicates whether or not a play area rectangle is be created and added to the scene.</span></span> <span data-ttu-id="9ecd8-129">預設值為 true。</span><span class="sxs-lookup"><span data-stu-id="9ecd8-129">The default value is true.</span></span>

<span data-ttu-id="9ecd8-130">**Material**</span><span class="sxs-lookup"><span data-stu-id="9ecd8-130">**Material**</span></span>

<span data-ttu-id="9ecd8-131">指出建立播放區域物件時應使用的材質。</span><span class="sxs-lookup"><span data-stu-id="9ecd8-131">Indicates the material that should be used when creating the play area object.</span></span>

<span data-ttu-id="9ecd8-132">**實體層**</span><span class="sxs-lookup"><span data-stu-id="9ecd8-132">**Physics Layer**</span></span>

<span data-ttu-id="9ecd8-133">應設定播放區域的圖層。</span><span class="sxs-lookup"><span data-stu-id="9ecd8-133">The layer on which the play area should be set.</span></span> <span data-ttu-id="9ecd8-134">預設值為 [ *忽略 Raycast* 圖層]。</span><span class="sxs-lookup"><span data-stu-id="9ecd8-134">The default value is the *Ignore Raycast* layer.</span></span>

## <a name="tracked-area-settings"></a><span data-ttu-id="9ecd8-135">追蹤區域設定</span><span class="sxs-lookup"><span data-stu-id="9ecd8-135">Tracked area settings</span></span>

![界限視覺效果追蹤區域設定](../images/boundary/BoundaryVisualizationTrackedAreaSettings.png)

<span data-ttu-id="9ecd8-137">**顯示**</span><span class="sxs-lookup"><span data-stu-id="9ecd8-137">**Show**</span></span>

<span data-ttu-id="9ecd8-138">指出是否要建立追蹤區域的外框，並將其加入場景中。</span><span class="sxs-lookup"><span data-stu-id="9ecd8-138">Indicates whether or not the outline of the tracked area is be created and added to the scene.</span></span> <span data-ttu-id="9ecd8-139">預設值為 true。</span><span class="sxs-lookup"><span data-stu-id="9ecd8-139">The default value is true.</span></span>

<span data-ttu-id="9ecd8-140">**Material**</span><span class="sxs-lookup"><span data-stu-id="9ecd8-140">**Material**</span></span>

<span data-ttu-id="9ecd8-141">表示建立追蹤區域外框時應該使用的材質。</span><span class="sxs-lookup"><span data-stu-id="9ecd8-141">Indicates the material that should be used when creating the tracked area outline.</span></span>

<span data-ttu-id="9ecd8-142">**實體層**</span><span class="sxs-lookup"><span data-stu-id="9ecd8-142">**Physics Layer**</span></span>

<span data-ttu-id="9ecd8-143">應設定追蹤區域的圖層。</span><span class="sxs-lookup"><span data-stu-id="9ecd8-143">The layer on which the tracked area should be sets.</span></span> <span data-ttu-id="9ecd8-144">預設值為 [ *忽略 Raycast* 圖層]。</span><span class="sxs-lookup"><span data-stu-id="9ecd8-144">The default value is the *Ignore Raycast* layer.</span></span>

## <a name="boundary-wall-settings"></a><span data-ttu-id="9ecd8-145">界限牆設定</span><span class="sxs-lookup"><span data-stu-id="9ecd8-145">Boundary wall settings</span></span>

![界限視覺效果邊界牆設定](../images/boundary/BoundaryVisualizationWallSettings.png)

<span data-ttu-id="9ecd8-147">**顯示**</span><span class="sxs-lookup"><span data-stu-id="9ecd8-147">**Show**</span></span>

<span data-ttu-id="9ecd8-148">指出是否要建立界限牆平面，並將其加入場景中。</span><span class="sxs-lookup"><span data-stu-id="9ecd8-148">Indicates whether or not boundary wall planes are to be created and added to the scene.</span></span> <span data-ttu-id="9ecd8-149">預設值為 false。</span><span class="sxs-lookup"><span data-stu-id="9ecd8-149">The default value is false.</span></span>

<span data-ttu-id="9ecd8-150">**Material**</span><span class="sxs-lookup"><span data-stu-id="9ecd8-150">**Material**</span></span>

<span data-ttu-id="9ecd8-151">指出建立邊界牆平面時應該使用的材質。</span><span class="sxs-lookup"><span data-stu-id="9ecd8-151">Indicates the material that should be used when creating the boundary wall planes.</span></span>

<span data-ttu-id="9ecd8-152">**實體層**</span><span class="sxs-lookup"><span data-stu-id="9ecd8-152">**Physics Layer**</span></span>

<span data-ttu-id="9ecd8-153">應設定界限牆的圖層。</span><span class="sxs-lookup"><span data-stu-id="9ecd8-153">The layer on which the boundary walls should be set.</span></span> <span data-ttu-id="9ecd8-154">預設值為 [ *忽略 Raycast* 圖層]。</span><span class="sxs-lookup"><span data-stu-id="9ecd8-154">The default value is the *Ignore Raycast* layer.</span></span>

> [!NOTE]
> <span data-ttu-id="9ecd8-155">將界限牆元件設定為 [ *略過 Raycast* ] 以外的實體層，可能會讓使用者無法與場景內的物件互動。</span><span class="sxs-lookup"><span data-stu-id="9ecd8-155">Setting the boundary wall component to a physics layer other than *Ignore Raycast* may prevent users from interacting with objects within the scene.</span></span>

## <a name="boundary-ceiling-settings"></a><span data-ttu-id="9ecd8-156">界限上限設定</span><span class="sxs-lookup"><span data-stu-id="9ecd8-156">Boundary ceiling settings</span></span>

![界限視覺效果界限上限設定](../images/boundary/BoundaryVisualizationCeilingSettings.png)

<span data-ttu-id="9ecd8-158">**顯示**</span><span class="sxs-lookup"><span data-stu-id="9ecd8-158">**Show**</span></span>

<span data-ttu-id="9ecd8-159">指出是否要建立界限上限平面，並將其加入場景中。</span><span class="sxs-lookup"><span data-stu-id="9ecd8-159">Indicates whether or not a boundary ceiling plane is to be created and added to the scene.</span></span> <span data-ttu-id="9ecd8-160">預設值為 false。</span><span class="sxs-lookup"><span data-stu-id="9ecd8-160">The default value is false.</span></span>

<span data-ttu-id="9ecd8-161">**Material**</span><span class="sxs-lookup"><span data-stu-id="9ecd8-161">**Material**</span></span>

<span data-ttu-id="9ecd8-162">指出建立界限上限平面時應使用的材質。</span><span class="sxs-lookup"><span data-stu-id="9ecd8-162">Indicates the material that should be used when creating the boundary ceiling plane.</span></span>

<span data-ttu-id="9ecd8-163">**實體層**</span><span class="sxs-lookup"><span data-stu-id="9ecd8-163">**Physics Layer**</span></span>

<span data-ttu-id="9ecd8-164">應設定界限牆的圖層。</span><span class="sxs-lookup"><span data-stu-id="9ecd8-164">The layer on which the boundary walls should be set.</span></span> <span data-ttu-id="9ecd8-165">預設值為 [ *忽略 Raycast* 圖層]。</span><span class="sxs-lookup"><span data-stu-id="9ecd8-165">The default value is the *Ignore Raycast* layer.</span></span>

> [!NOTE]
> <span data-ttu-id="9ecd8-166">將界限上限元件設定為 [ *略過 Raycast* ] 以外的實體層，可能會讓使用者無法與場景內的物件互動。</span><span class="sxs-lookup"><span data-stu-id="9ecd8-166">Setting the boundary ceiling component to a physics layer other than *Ignore Raycast* may prevent users from interacting with objects within the scene.</span></span>

## <a name="see-also"></a><span data-ttu-id="9ecd8-167">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9ecd8-167">See also</span></span>

- [<span data-ttu-id="9ecd8-168">界限 API 檔</span><span class="sxs-lookup"><span data-stu-id="9ecd8-168">Boundary API documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.Boundary)
- [<span data-ttu-id="9ecd8-169">界限系統</span><span class="sxs-lookup"><span data-stu-id="9ecd8-169">Boundary System</span></span>](boundary-system-getting-started.md)
