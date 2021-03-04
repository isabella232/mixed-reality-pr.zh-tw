---
title: DetectingPlatformCapabilities
description: MRTK 支援的不同功能詳細資料
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、功能、
ms.openlocfilehash: 00d6cd822b261413d4b4270041966675bec4280a
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/03/2021
ms.locfileid: "101780023"
---
# <a name="detecting-platform-capabilities"></a>偵測平臺功能

MRTK 常見的問題是，您必須知道哪些特定的裝置 (例如： Microsoft HoloLens 2) 用來執行應用程式。 識別確切的硬體在不同的平臺上可能會有挑戰性。 相反地，MRTK 會提供一種方法來識別執行時間的特定功能， (例如，如果目前的裝置端點支援明確的手) 。

## <a name="capabilities"></a>功能

Mixed Reality 工具 [`MixedRealityCapability`](xref:Microsoft.MixedReality.Toolkit.MixedRealityCapability) 組提供列舉，其定義應用程式可以在執行時間查詢的一組功能。

### <a name="input-system-capabilities"></a>輸入系統功能

預設的 MRTK 輸入系統支援查詢下列功能：

| 功能 | 描述 |
|---|---|
| ArticulatedHand | 明確的手輸入 |
| EyeTracking | 眼睛的目標 |
| GGVHand | 注視手勢-語音手輸入 |
| MotionController | 移動控制器輸入 |
| VoiceCommand | 使用應用程式定義關鍵字的語音命令 |
| VoiceDictation | 語音文字聽寫 |

下列範例程式碼會檢查輸入系統是否已載入資料提供者，並支援具明確的手。

```c#
bool supportsArticulatedHands = false;

IMixedRealityCapabilityCheck capabilityCheck = CoreServices.InputSystem as IMixedRealityCapabilityCheck;
if (capabilityCheck != null)
{
    supportsArticulatedHands = capabilityCheck.CheckCapability(MixedRealityCapability.ArticulatedHand);
}
```

### <a name="spatial-awareness-capabilities"></a>空間感知功能

預設的 MRTK 空間感知系統支援查詢下列功能：

| 功能 | 描述 |
|---|---|
| SpatialAwarenessMesh | 空間網格 |
| SpatialAwarenessPlane | 空間平面 |
| SpatialAwarenessPoint | 空間點 |

此範例會檢查空間感知系統是否已載入具有空間網格支援的資料提供者。

```c#
bool supportsSpatialMesh = false;

IMixedRealityCapabilityCheck capabilityCheck = CoreServices.SpatialAwarenessSystem as IMixedRealityCapabilityCheck;
if (capabilityCheck != null)
{
    supportsSpatialMesh = capabilityCheck.CheckCapability(MixedRealityCapability.SpatialAwarenessMesh);
}
```

## <a name="see-also"></a>另請參閱

- [IMixedRealityCapabilityCheck API 檔](xref:Microsoft.MixedReality.Toolkit.IMixedRealityCapabilityCheck)
- [MixedRealityCapability 列舉檔](xref:Microsoft.MixedReality.Toolkit.MixedRealityCapability)
