---
title: MRTK_and_managed_code_stripping
description: MRTK 和 Unity 中的程式碼去除
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: 7e80f25f6e5af7fe851bf9106ebbd07dece5dbad
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104681571"
---
# <a name="mrtk-and-unity-managed-code-stripping"></a><span data-ttu-id="3c884-104">MRTK 和 Unity managed code 抽出</span><span class="sxs-lookup"><span data-stu-id="3c884-104">MRTK and Unity managed code stripping</span></span>

<span data-ttu-id="3c884-105">使用 Unity 的 IL2CPP 腳本後端時 (在 Unity 2018.4 中為選擇性，在2019和更新版本的) 中，需要進行 [managed 程式碼的去除](https://docs.unity3d.com/Manual/ManagedCodeStripping.html) 。</span><span class="sxs-lookup"><span data-stu-id="3c884-105">When using Unity's IL2CPP scripting backend (optional in Unity 2018.4, required in 2019 and newer), [managed code stripping](https://docs.unity3d.com/Manual/ManagedCodeStripping.html) occurs.</span></span>
<span data-ttu-id="3c884-106">Unity 的連結器會執行此程式，以減少二進位大小以及減少組建時間。</span><span class="sxs-lookup"><span data-stu-id="3c884-106">Unity's linker performs this process to reduce binary size as well as to decrease build times.</span></span>

<span data-ttu-id="3c884-107">混合現實工具組會使用檔案， `link.xml` 以影響 Unity 的連結器處理 MRTK 元件的方式。</span><span class="sxs-lookup"><span data-stu-id="3c884-107">The Mixed Reality Toolkit uses a file, `link.xml`, to influence how Unity's linker processes MRTK assemblies.</span></span> <span data-ttu-id="3c884-108">本檔案（完整于 [Unity 的](https://docs.unity3d.com/Manual/ManagedCodeStripping.html#LinkXML)檔中所述）提供連結器指示，說明如何在無法推斷程式碼時保留程式碼 (例如：透過反映) 來使用。</span><span class="sxs-lookup"><span data-stu-id="3c884-108">This file, described in full in [Unity's documentation](https://docs.unity3d.com/Manual/ManagedCodeStripping.html#LinkXML), provides the linker with instructions on how to preserve code when its usage cannot be inferred (ex: used via reflection).</span></span>

<span data-ttu-id="3c884-109">MRTK 是有彈性且可自訂的平臺，它會在匯入時建立檔案 `link.xml` `Assets/MixedRealityToolkit.Generated` （如果找不到的話）。</span><span class="sxs-lookup"><span data-stu-id="3c884-109">As a flexible and customizable platform, MRTK creates the `link.xml` file in `Assets/MixedRealityToolkit.Generated` on import, if it is found to not exist.</span></span> <span data-ttu-id="3c884-110">預先存在的 link.xml 檔案不會遭到覆寫。</span><span class="sxs-lookup"><span data-stu-id="3c884-110">Pre-existing link.xml files are not overwritten.</span></span> <span data-ttu-id="3c884-111">建議您將其 `link.xml` `link.xml.meta` 加入至版本控制。</span><span class="sxs-lookup"><span data-stu-id="3c884-111">It is recommended that `link.xml` and `link.xml.meta` be added to version control.</span></span> <span data-ttu-id="3c884-112">開發人員應該可以隨意自訂 `Assets/MixedRealityToolkit.Generated/link.xml` 以符合專案的需求。</span><span class="sxs-lookup"><span data-stu-id="3c884-112">Developers should feel free to customize `Assets/MixedRealityToolkit.Generated/link.xml` to meet the needs of the project.</span></span>

<span data-ttu-id="3c884-113">依預設，MRTK 所建立的 link.xml 檔會保留下列資料中所顯示的完整元件。</span><span class="sxs-lookup"><span data-stu-id="3c884-113">By default, the link.xml file created by MRTK preserves the entirety of the assemblies shown in the following data.</span></span>

``` xml
<linker> 
  <!-- 
    This link.xml file is provided to prevent MRTK code from being optimized away 
    during IL2CPP builds.More details on when this is needed and why this is needed 
    can be found here: https://github.com/microsoft/MixedRealityToolkit-Unity/issues/5273 
    If your application doesn't use some specific services (for example, if teleportation system is 
    disabled in the profile), it is possible to remove their corresponding lines down 
    below(in the previous example, we would remove the TeleportSystem below). 
    It's recommended to start with this list and narrow down if you want to ensure 
    specific bits of code get optimized away. 
  --> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.SDK" preserve="all"/> 
  <!-- Core systems --> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Services.BoundarySystem" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Services.CameraSystem" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Services.DiagnosticsSystem" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Services.InputSystem" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Services.SceneSystem" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Services.SpatialAwarenessSystem" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Services.TeleportSystem" preserve="all"/> 
  <!-- Data providers --> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.LeapMotion" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenVR" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.UnityAR" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.WindowsMixedReality.Shared" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.WindowsMixedReality" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.XRSDK.WindowsMixedReality" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.WindowsVoiceInput" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.XRSDK" preserve="all"/> 
  <!-- Extension services --> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Extensions.HandPhysics" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Extensions.Tracking" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Extensions.SceneTransitionService" preserve="all"/> 
</linker>
```

<span data-ttu-id="3c884-114">如需有關 link.xml 檔案格式的詳細資訊，請參閱 Unity 檔。</span><span class="sxs-lookup"><span data-stu-id="3c884-114">For more information on the link.xml file format, please refer to the Unity documentation.</span></span>

## <a name="see-also"></a><span data-ttu-id="3c884-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3c884-115">See also</span></span>

- [<span data-ttu-id="3c884-116">Unity： Managed Code 抽出</span><span class="sxs-lookup"><span data-stu-id="3c884-116">Unity: Managed Code Stripping</span></span>](https://docs.unity3d.com/Manual/ManagedCodeStripping.html)
- [<span data-ttu-id="3c884-117">Unity： Link XML 檔案</span><span class="sxs-lookup"><span data-stu-id="3c884-117">Unity: Link XML file</span></span>](https://docs.unity3d.com/Manual/ManagedCodeStripping.html#LinkXML)
