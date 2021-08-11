---
title: TeleportSystemOverview
description: 在 MRTK 中啟用和停用傳送系統的總覽
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、傳送系統、
ms.openlocfilehash: ee56f62d6e0206249db62d8e7e93cf97cdf8bcc40c35ec0284ebae319870f8ee
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2021
ms.locfileid: "115197638"
---
# <a name="teleport-system"></a>傳送系統

當應用程式使用不透明的顯示時，傳送系統是處理 teleporting 使用者的 MRTK 子系統。 針對 AR 體驗 (例如 HoloLens) ，遙傳系統不在使用中。 針對沉浸式 HMD 體驗 (OpenVR、WMR) 可啟用「傳送」系統。

## <a name="enabling-and-disabling"></a>啟用和停用

您可以切換設定檔中的核取方塊來啟用或停用「傳送」系統。
這可以藉由選取場景中的 MixedRealityToolkit 物件、按一下 [傳送]，然後切換 [啟用傳送系統] 核取方塊來完成。

這也可以在執行時間進行：

```c#
void DisableTeleportSystem()
{
    CoreServices.TeleportSystem.Disable();
}

void EnableTeleportSystem()
{
    CoreServices.TeleportSystem.Enable();
}
```

## <a name="events"></a>事件

傳送系統會透過介面公開事件 [`IMixedRealityTeleportHandler`](xref:Microsoft.MixedReality.Toolkit.Teleport.IMixedRealityTeleportHandler) ，以提供傳送動作開始、結束或取消時的信號。
請參閱連結的 API 檔，以取得有關事件和其相關聯承載之機制的詳細資料。

## <a name="usage"></a>使用方式

### <a name="how-to-register-for-teleportation-events"></a>如何註冊遙傳事件

下列程式碼顯示如何建立將接聽遙傳事件的 MonoBehaviour。 此程式碼假設已啟用傳送系統。

```c#
using Microsoft.MixedReality.Toolkit;
using Microsoft.MixedReality.Toolkit.Teleport;
using UnityEngine;

public class TeleportHandlerExample : MonoBehaviour, IMixedRealityTeleportHandler
{
    public void OnTeleportCanceled(TeleportEventData eventData)
    {
        Debug.Log("Teleport Cancelled");
    }

    public void OnTeleportCompleted(TeleportEventData eventData)
    {
        Debug.Log("Teleport Completed");
    }

    public void OnTeleportRequest(TeleportEventData eventData)
    {
        Debug.Log("Teleport Request");
    }

    public void OnTeleportStarted(TeleportEventData eventData)
    {
        Debug.Log("Teleport Started");
    }

    void OnEnable()
    {
        // This is the critical call that registers this class for events. Without this
        // class's IMixedRealityTeleportHandler interface will not be called.
        CoreServices.TeleportSystem.RegisterHandler<IMixedRealityTeleportHandler>(this);
    }

    void OnDisable()
    {
        // Unregistering when disabled is important, otherwise this class will continue
        // to receive teleportation events.
        CoreServices.TeleportSystem.UnregisterHandler<IMixedRealityTeleportHandler>(this);
    }
}
```
