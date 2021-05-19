---
title: Unity AR 相機設定
description: 在 MRTK 中使用 AR 攝影機的檔
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、AR 攝影機、
ms.openlocfilehash: baa54f4a7c6238b136a108cf5adcbddd29c3ee1b
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143459"
---
# <a name="unity-ar-camera-settings-provider"></a><span data-ttu-id="247a6-104">Unity AR 相機設定提供者</span><span class="sxs-lookup"><span data-stu-id="247a6-104">Unity AR camera settings provider</span></span>

<span data-ttu-id="247a6-105">Unity AR 攝影機設定提供者是實驗性的 MRTK 元件，可讓 mixed reality 應用程式在 Android 和 iOS 裝置上執行。</span><span class="sxs-lookup"><span data-stu-id="247a6-105">The Unity AR camera settings provider is an experimental MRTK component that enables mixed reality applications to run on Android and iOS devices.</span></span>

## <a name="unity-ar-camera-settings-provider-options"></a><span data-ttu-id="247a6-106">Unity AR 相機設定提供者選項</span><span class="sxs-lookup"><span data-stu-id="247a6-106">Unity AR camera settings provider options</span></span>

![Unity AR 相機設定設定](../images/camera-system/UnityArSettingsConfiguration.png)

<span data-ttu-id="247a6-108">如需如何將提供者新增至場景的指南： [如何設定 iOS 和 Android 的 MRTK](../../supported-devices/using-ar-foundation.md)</span><span class="sxs-lookup"><span data-stu-id="247a6-108">For a guide on how to add the provider to your scene: [How to configure MRTK for iOS and Android](../../supported-devices/using-ar-foundation.md)</span></span>

### <a name="tracking-settings"></a><span data-ttu-id="247a6-109">追蹤設定</span><span class="sxs-lookup"><span data-stu-id="247a6-109">Tracking settings</span></span>

<span data-ttu-id="247a6-110">Unity AR 攝影機設定提供者可以設定如何執行追蹤的設定選項。</span><span class="sxs-lookup"><span data-stu-id="247a6-110">The Unity AR camera settings provider allows configuration options for how tracking is performed.</span></span> <span data-ttu-id="247a6-111">這些設定僅適用于 Unity AR 攝影機設定提供者的執行。</span><span class="sxs-lookup"><span data-stu-id="247a6-111">These settings are specific to the Unity AR camera settings provider implementation.</span></span>

<span data-ttu-id="247a6-112">**姿勢來源**</span><span class="sxs-lookup"><span data-stu-id="247a6-112">**Pose Source**</span></span>

<span data-ttu-id="247a6-113">姿勢來源定義了可用的擴充現實追蹤的可用類型。</span><span class="sxs-lookup"><span data-stu-id="247a6-113">The pose source defines the available types of augmented reality tracking poses.</span></span> <span data-ttu-id="247a6-114">一般而言，這些值會對應至執行應用程式之裝置的元件。</span><span class="sxs-lookup"><span data-stu-id="247a6-114">In general, these values map to a component of the device on which the application is running.</span></span>

<span data-ttu-id="247a6-115">下表說明可用的選項。</span><span class="sxs-lookup"><span data-stu-id="247a6-115">The available options are described in the following table.</span></span>

| <span data-ttu-id="247a6-116">選項</span><span class="sxs-lookup"><span data-stu-id="247a6-116">Option</span></span> | <span data-ttu-id="247a6-117">Description</span><span class="sxs-lookup"><span data-stu-id="247a6-117">Description</span></span> |
| --- | --- |
| <span data-ttu-id="247a6-118">Center</span><span class="sxs-lookup"><span data-stu-id="247a6-118">Center</span></span> | <span data-ttu-id="247a6-119">前端掛接裝置的中心眼睛。</span><span class="sxs-lookup"><span data-stu-id="247a6-119">The center eye of a head mounted device.</span></span> |
| <span data-ttu-id="247a6-120">彩色相機</span><span class="sxs-lookup"><span data-stu-id="247a6-120">Color Camera</span></span> | <span data-ttu-id="247a6-121">行動裝置的色彩相機。</span><span class="sxs-lookup"><span data-stu-id="247a6-121">The color camera of a mobile device.</span></span> |
| <span data-ttu-id="247a6-122">Head</span><span class="sxs-lookup"><span data-stu-id="247a6-122">Head</span></span> | <span data-ttu-id="247a6-123">前端掛接裝置的前端，通常會稍微高於中心眼睛。</span><span class="sxs-lookup"><span data-stu-id="247a6-123">The head eye of a head mounted device, often slightly above the center eye.</span></span> |
| <span data-ttu-id="247a6-124">左方眼睛</span><span class="sxs-lookup"><span data-stu-id="247a6-124">Left Eye</span></span> | <span data-ttu-id="247a6-125">前端掛載裝置的最左邊。</span><span class="sxs-lookup"><span data-stu-id="247a6-125">The left eye of a head mounted device.</span></span> |
| <span data-ttu-id="247a6-126">左方姿勢</span><span class="sxs-lookup"><span data-stu-id="247a6-126">Left Pose</span></span> | <span data-ttu-id="247a6-127">左邊控制器會造成。</span><span class="sxs-lookup"><span data-stu-id="247a6-127">The left hand controller pose.</span></span> |
| <span data-ttu-id="247a6-128">適當留意</span><span class="sxs-lookup"><span data-stu-id="247a6-128">Right Eye</span></span> | <span data-ttu-id="247a6-129">前端掛接裝置的正確眼睛。</span><span class="sxs-lookup"><span data-stu-id="247a6-129">The right eye of a head mounted device.</span></span> |
| <span data-ttu-id="247a6-130">靠右姿勢</span><span class="sxs-lookup"><span data-stu-id="247a6-130">Right Pose</span></span> | <span data-ttu-id="247a6-131">右手邊控制器會造成。</span><span class="sxs-lookup"><span data-stu-id="247a6-131">The right hand controller pose.</span></span> |

<span data-ttu-id="247a6-132">姿勢來源的預設值是 [ **彩色攝影機**]，可在行動裝置上啟用透明顯示，例如手機或平板電腦。</span><span class="sxs-lookup"><span data-stu-id="247a6-132">The default value for pose source is **Color Camera**, to enable a transparent display on mobile devices, such as a phone or tablet.</span></span>

<span data-ttu-id="247a6-133">**追蹤類型**</span><span class="sxs-lookup"><span data-stu-id="247a6-133">**Tracking Type**</span></span>

<span data-ttu-id="247a6-134">追蹤類型會定義將用於追蹤的姿勢 () 部分。</span><span class="sxs-lookup"><span data-stu-id="247a6-134">The tracking type defines the portion(s) of the pose that will be used for tracking.</span></span>

<span data-ttu-id="247a6-135">下表說明可用的選項。</span><span class="sxs-lookup"><span data-stu-id="247a6-135">The available options are described in the following table.</span></span>

| <span data-ttu-id="247a6-136">選項</span><span class="sxs-lookup"><span data-stu-id="247a6-136">Option</span></span> | <span data-ttu-id="247a6-137">Description</span><span class="sxs-lookup"><span data-stu-id="247a6-137">Description</span></span> |
| --- | --- |
| <span data-ttu-id="247a6-138">位置</span><span class="sxs-lookup"><span data-stu-id="247a6-138">Position</span></span> | <span data-ttu-id="247a6-139">裝置的位置。</span><span class="sxs-lookup"><span data-stu-id="247a6-139">The position of the device.</span></span> |
| <span data-ttu-id="247a6-140">旋轉</span><span class="sxs-lookup"><span data-stu-id="247a6-140">Rotation</span></span> | <span data-ttu-id="247a6-141">裝置的旋轉。</span><span class="sxs-lookup"><span data-stu-id="247a6-141">The rotation of the device.</span></span> |
| <span data-ttu-id="247a6-142">旋轉和位置</span><span class="sxs-lookup"><span data-stu-id="247a6-142">Rotation And Position</span></span> | <span data-ttu-id="247a6-143">裝置的位置和旋轉。</span><span class="sxs-lookup"><span data-stu-id="247a6-143">The position and rotation of the device.</span></span> |

<span data-ttu-id="247a6-144">追蹤類型的預設值為 [ **旋轉] 和 [位置**]，以啟用最豐富的追蹤體驗。</span><span class="sxs-lookup"><span data-stu-id="247a6-144">The default value for tracking type is **Rotation And Position**, to enable the richest tracking experience.</span></span>

<span data-ttu-id="247a6-145">**更新類型**</span><span class="sxs-lookup"><span data-stu-id="247a6-145">**Update Type**</span></span>

<span data-ttu-id="247a6-146">更新類型會定義在框架處理期間，將會取樣資料的位置。</span><span class="sxs-lookup"><span data-stu-id="247a6-146">The update type defines at what points, during frame processing, the pose data will be sampled.</span></span>

<span data-ttu-id="247a6-147">下表說明可用的選項。</span><span class="sxs-lookup"><span data-stu-id="247a6-147">The available options are described in the following table.</span></span>

| <span data-ttu-id="247a6-148">選項</span><span class="sxs-lookup"><span data-stu-id="247a6-148">Option</span></span> | <span data-ttu-id="247a6-149">Description</span><span class="sxs-lookup"><span data-stu-id="247a6-149">Description</span></span> |
| --- | --- |
| <span data-ttu-id="247a6-150">轉譯前</span><span class="sxs-lookup"><span data-stu-id="247a6-150">Before Render</span></span> | <span data-ttu-id="247a6-151">緊接在轉譯之前。</span><span class="sxs-lookup"><span data-stu-id="247a6-151">Just before rendering.</span></span> |
| <span data-ttu-id="247a6-152">更新</span><span class="sxs-lookup"><span data-stu-id="247a6-152">Update</span></span> | <span data-ttu-id="247a6-153">在框架的更新階段。</span><span class="sxs-lookup"><span data-stu-id="247a6-153">During the update phase of the frame.</span></span> |
| <span data-ttu-id="247a6-154">更新和在轉譯之前</span><span class="sxs-lookup"><span data-stu-id="247a6-154">Update And Before Render</span></span> | <span data-ttu-id="247a6-155">在更新階段和轉譯之前。</span><span class="sxs-lookup"><span data-stu-id="247a6-155">During the update phase and just before rendering.</span></span> |

<span data-ttu-id="247a6-156">追蹤類型的預設值是 **Update 和轉譯之前** 的值，可啟用最低的追蹤延遲。</span><span class="sxs-lookup"><span data-stu-id="247a6-156">The default value for tracking type is **Update And Before Render**, to enable the lowest tracking latency.</span></span>

## <a name="see-also"></a><span data-ttu-id="247a6-157">另請參閱</span><span class="sxs-lookup"><span data-stu-id="247a6-157">See also</span></span>

- [<span data-ttu-id="247a6-158">攝影機系統總覽</span><span class="sxs-lookup"><span data-stu-id="247a6-158">Camera System Overview</span></span>](camera-system-overview.md)
- [<span data-ttu-id="247a6-159">建立相機設定提供者</span><span class="sxs-lookup"><span data-stu-id="247a6-159">Creating a Camera Settings Provider</span></span>](create-settings-provider.md)
