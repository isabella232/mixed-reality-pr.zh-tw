---
title: 偵測平臺功能
description: MRTK 支援的不同功能詳細資料
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、功能、
ms.openlocfilehash: 70d320e178f4635d74b5be6a1874eb4254801719
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175521"
---
# <a name="detecting-platform-capabilities"></a><span data-ttu-id="97ef3-104">偵測平臺功能</span><span class="sxs-lookup"><span data-stu-id="97ef3-104">Detecting platform capabilities</span></span>

<span data-ttu-id="97ef3-105">MRTK 常見的問題是，您必須知道哪些特定裝置 (例如： Microsoft HoloLens 2) 用來執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="97ef3-105">A common question asked of the MRTK involves knowing which specific device (ex: Microsoft HoloLens 2) is being used to run an application.</span></span> <span data-ttu-id="97ef3-106">識別確切的硬體在不同的平臺上可能會有挑戰性。</span><span class="sxs-lookup"><span data-stu-id="97ef3-106">Identifying the exact hardware can be challenging on different platforms.</span></span> <span data-ttu-id="97ef3-107">相反地，MRTK 會提供一種方法來識別執行時間的特定功能， (例如，如果目前的裝置端點支援明確的手) 。</span><span class="sxs-lookup"><span data-stu-id="97ef3-107">Instead, the MRTK provides a way to identify specific capabilities at runtime, (e.g. if the current device endpoint supports articulated hands).</span></span>

## <a name="capabilities"></a><span data-ttu-id="97ef3-108">功能</span><span class="sxs-lookup"><span data-stu-id="97ef3-108">Capabilities</span></span>

<span data-ttu-id="97ef3-109">Mixed Reality 工具 [`MixedRealityCapability`](xref:Microsoft.MixedReality.Toolkit.MixedRealityCapability) 組提供列舉，其定義應用程式可以在執行時間查詢的一組功能。</span><span class="sxs-lookup"><span data-stu-id="97ef3-109">The Mixed Reality Toolkit provides the [`MixedRealityCapability`](xref:Microsoft.MixedReality.Toolkit.MixedRealityCapability) enumeration, which defines a set of capabilities for which an application can query at runtime.</span></span>

### <a name="input-system-capabilities"></a><span data-ttu-id="97ef3-110">輸入系統功能</span><span class="sxs-lookup"><span data-stu-id="97ef3-110">Input system capabilities</span></span>

<span data-ttu-id="97ef3-111">預設的 MRTK 輸入系統支援查詢下列功能：</span><span class="sxs-lookup"><span data-stu-id="97ef3-111">The default MRTK Input System supports querying the following capabilities:</span></span>

| <span data-ttu-id="97ef3-112">功能</span><span class="sxs-lookup"><span data-stu-id="97ef3-112">Capability</span></span> | <span data-ttu-id="97ef3-113">描述</span><span class="sxs-lookup"><span data-stu-id="97ef3-113">Description</span></span> |
|---|---|
| <span data-ttu-id="97ef3-114">ArticulatedHand</span><span class="sxs-lookup"><span data-stu-id="97ef3-114">ArticulatedHand</span></span> | <span data-ttu-id="97ef3-115">明確的手輸入</span><span class="sxs-lookup"><span data-stu-id="97ef3-115">Articulated hand input</span></span> |
| <span data-ttu-id="97ef3-116">EyeTracking</span><span class="sxs-lookup"><span data-stu-id="97ef3-116">EyeTracking</span></span> | <span data-ttu-id="97ef3-117">眼睛的目標</span><span class="sxs-lookup"><span data-stu-id="97ef3-117">Eye gaze targeting</span></span> |
| <span data-ttu-id="97ef3-118">GGVHand</span><span class="sxs-lookup"><span data-stu-id="97ef3-118">GGVHand</span></span> | <span data-ttu-id="97ef3-119">注視手勢-語音手輸入</span><span class="sxs-lookup"><span data-stu-id="97ef3-119">Gaze-Gesture-Voice hand input</span></span> |
| <span data-ttu-id="97ef3-120">MotionController</span><span class="sxs-lookup"><span data-stu-id="97ef3-120">MotionController</span></span> | <span data-ttu-id="97ef3-121">移動控制器輸入</span><span class="sxs-lookup"><span data-stu-id="97ef3-121">Motion controller input</span></span> |
| <span data-ttu-id="97ef3-122">VoiceCommand</span><span class="sxs-lookup"><span data-stu-id="97ef3-122">VoiceCommand</span></span> | <span data-ttu-id="97ef3-123">使用應用程式定義關鍵字的語音命令</span><span class="sxs-lookup"><span data-stu-id="97ef3-123">Voice commands using app defined keywords</span></span> |
| <span data-ttu-id="97ef3-124">VoiceDictation</span><span class="sxs-lookup"><span data-stu-id="97ef3-124">VoiceDictation</span></span> | <span data-ttu-id="97ef3-125">語音文字聽寫</span><span class="sxs-lookup"><span data-stu-id="97ef3-125">Voice to text dictation</span></span> |

<span data-ttu-id="97ef3-126">下列範例程式碼會檢查輸入系統是否已載入資料提供者，並支援具明確的手。</span><span class="sxs-lookup"><span data-stu-id="97ef3-126">The example code below checks to see if the input system has loaded a data provider with support for articulated hands.</span></span>

```c#
bool supportsArticulatedHands = false;

IMixedRealityCapabilityCheck capabilityCheck = CoreServices.InputSystem as IMixedRealityCapabilityCheck;
if (capabilityCheck != null)
{
    supportsArticulatedHands = capabilityCheck.CheckCapability(MixedRealityCapability.ArticulatedHand);
}
```

### <a name="spatial-awareness-capabilities"></a><span data-ttu-id="97ef3-127">空間感知功能</span><span class="sxs-lookup"><span data-stu-id="97ef3-127">Spatial awareness capabilities</span></span>

<span data-ttu-id="97ef3-128">預設的 MRTK 空間感知系統支援查詢下列功能：</span><span class="sxs-lookup"><span data-stu-id="97ef3-128">The default MRTK Spatial Awareness system supports querying the following capabilities:</span></span>

| <span data-ttu-id="97ef3-129">功能</span><span class="sxs-lookup"><span data-stu-id="97ef3-129">Capability</span></span> | <span data-ttu-id="97ef3-130">描述</span><span class="sxs-lookup"><span data-stu-id="97ef3-130">Description</span></span> |
|---|---|
| <span data-ttu-id="97ef3-131">SpatialAwarenessMesh</span><span class="sxs-lookup"><span data-stu-id="97ef3-131">SpatialAwarenessMesh</span></span> | <span data-ttu-id="97ef3-132">空間網格</span><span class="sxs-lookup"><span data-stu-id="97ef3-132">Spatial meshes</span></span> |
| <span data-ttu-id="97ef3-133">SpatialAwarenessPlane</span><span class="sxs-lookup"><span data-stu-id="97ef3-133">SpatialAwarenessPlane</span></span> | <span data-ttu-id="97ef3-134">空間平面</span><span class="sxs-lookup"><span data-stu-id="97ef3-134">Spatial planes</span></span> |
| <span data-ttu-id="97ef3-135">SpatialAwarenessPoint</span><span class="sxs-lookup"><span data-stu-id="97ef3-135">SpatialAwarenessPoint</span></span> | <span data-ttu-id="97ef3-136">空間點</span><span class="sxs-lookup"><span data-stu-id="97ef3-136">Spatial points</span></span> |

<span data-ttu-id="97ef3-137">此範例會檢查空間感知系統是否已載入具有空間網格支援的資料提供者。</span><span class="sxs-lookup"><span data-stu-id="97ef3-137">This example checks to see if the spatial awareness system has loaded a data provider with support for spatial meshes.</span></span>

```c#
bool supportsSpatialMesh = false;

IMixedRealityCapabilityCheck capabilityCheck = CoreServices.SpatialAwarenessSystem as IMixedRealityCapabilityCheck;
if (capabilityCheck != null)
{
    supportsSpatialMesh = capabilityCheck.CheckCapability(MixedRealityCapability.SpatialAwarenessMesh);
}
```

## <a name="see-also"></a><span data-ttu-id="97ef3-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="97ef3-138">See also</span></span>

- [<span data-ttu-id="97ef3-139">IMixedRealityCapabilityCheck API 檔</span><span class="sxs-lookup"><span data-stu-id="97ef3-139">IMixedRealityCapabilityCheck API documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.IMixedRealityCapabilityCheck)
- [<span data-ttu-id="97ef3-140">MixedRealityCapability 列舉檔</span><span class="sxs-lookup"><span data-stu-id="97ef3-140">MixedRealityCapability enum documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.MixedRealityCapability)
