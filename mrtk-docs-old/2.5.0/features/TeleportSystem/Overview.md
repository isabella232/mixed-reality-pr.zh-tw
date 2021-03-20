---
title: TeleportSystemOverview
description: 在 MRTK 中啟用和停用傳送系統的總覽
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、傳送系統、
ms.openlocfilehash: 2dfccc009510183f6c6b60d46ef4df312d2dc046
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104689688"
---
# <a name="teleport-system"></a><span data-ttu-id="69cd9-104">傳送系統</span><span class="sxs-lookup"><span data-stu-id="69cd9-104">Teleport system</span></span>

<span data-ttu-id="69cd9-105">當應用程式使用不透明的顯示時，傳送系統是處理 teleporting 使用者的 MRTK 子系統。</span><span class="sxs-lookup"><span data-stu-id="69cd9-105">The teleport system is a sub-system of the MRTK that handles teleporting the user when the application is using an opaque display.</span></span> <span data-ttu-id="69cd9-106">針對 (如 HoloLens) 的 AR 體驗，遙傳系統不在使用中。</span><span class="sxs-lookup"><span data-stu-id="69cd9-106">For AR experiences (like HoloLens), the teleportation system is not active.</span></span> <span data-ttu-id="69cd9-107">針對沉浸式 HMD 體驗 (OpenVR、WMR) 可啟用「傳送」系統。</span><span class="sxs-lookup"><span data-stu-id="69cd9-107">For immersive HMD experiences (OpenVR, WMR) the teleport system can be enabled.</span></span>

## <a name="enabling-and-disabling"></a><span data-ttu-id="69cd9-108">啟用和停用</span><span class="sxs-lookup"><span data-stu-id="69cd9-108">Enabling and disabling</span></span>

<span data-ttu-id="69cd9-109">您可以切換設定檔中的核取方塊來啟用或停用「傳送」系統。</span><span class="sxs-lookup"><span data-stu-id="69cd9-109">The teleport system can be enabled or disabled by toggling the checkbox in its profile.</span></span>
<span data-ttu-id="69cd9-110">這可以藉由選取場景中的 MixedRealityToolkit 物件、按一下 [傳送]，然後切換 [啟用傳送系統] 核取方塊來完成。</span><span class="sxs-lookup"><span data-stu-id="69cd9-110">This can be done by selecting the MixedRealityToolkit object in the scene, clicking "Teleport" and then toggling the "Enable Teleport System" checkbox.</span></span>

<span data-ttu-id="69cd9-111">這也可以在執行時間進行：</span><span class="sxs-lookup"><span data-stu-id="69cd9-111">This can also be done at runtime:</span></span>

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

## <a name="events"></a><span data-ttu-id="69cd9-112">事件</span><span class="sxs-lookup"><span data-stu-id="69cd9-112">Events</span></span>

<span data-ttu-id="69cd9-113">傳送系統會透過介面公開事件 [`IMixedRealityTeleportHandler`](xref:Microsoft.MixedReality.Toolkit.Teleport.IMixedRealityTeleportHandler) ，以提供傳送動作開始、結束或取消時的信號。</span><span class="sxs-lookup"><span data-stu-id="69cd9-113">The teleport system exposes events through the [`IMixedRealityTeleportHandler`](xref:Microsoft.MixedReality.Toolkit.Teleport.IMixedRealityTeleportHandler) interface to provide signals on when teleport actions begin, end, or get cancelled.</span></span>
<span data-ttu-id="69cd9-114">請參閱連結的 API 檔，以取得有關事件和其相關聯承載之機制的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="69cd9-114">See the linked API documentation for more details on the mechanics of the events and their associated payload.</span></span>

## <a name="usage"></a><span data-ttu-id="69cd9-115">使用方式</span><span class="sxs-lookup"><span data-stu-id="69cd9-115">Usage</span></span>

### <a name="how-to-register-for-teleportation-events"></a><span data-ttu-id="69cd9-116">如何註冊遙傳事件</span><span class="sxs-lookup"><span data-stu-id="69cd9-116">How to register for teleportation events</span></span>

<span data-ttu-id="69cd9-117">下列程式碼顯示如何建立將接聽遙傳事件的 MonoBehaviour。</span><span class="sxs-lookup"><span data-stu-id="69cd9-117">The code below shows how to create a MonoBehaviour that will listen for teleportation events.</span></span> <span data-ttu-id="69cd9-118">此程式碼假設已啟用傳送系統。</span><span class="sxs-lookup"><span data-stu-id="69cd9-118">This code assumes that the teleport system is enabled.</span></span>

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
