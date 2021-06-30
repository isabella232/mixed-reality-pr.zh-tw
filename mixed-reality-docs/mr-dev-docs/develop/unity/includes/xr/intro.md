---
ms.openlocfilehash: 550ad2b9fa92894cdf4dad86def4cd3a9b450fb1
ms.sourcegitcommit: e9a1510984d00dc40ffd39239349e500f5737a0d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/30/2021
ms.locfileid: "113103892"
---
# <a name="openxr"></a>[<span data-ttu-id="40ac0-101">OpenXR</span><span class="sxs-lookup"><span data-stu-id="40ac0-101">OpenXR</span></span>](#tab/openxr)

<span data-ttu-id="40ac0-102">Mixed Reality OpenXR 外掛程式是 Microsoft 對 Unity 2020 LTS 或更新版本的 **建議** 。</span><span class="sxs-lookup"><span data-stu-id="40ac0-102">The Mixed Reality OpenXR plugin is **Microsoft's recommendation** for Unity 2020 LTS or later.</span></span> <span data-ttu-id="40ac0-103">在未來開發新功能時，它們只會包含在混合現實 OpenXR 外掛程式中。</span><span class="sxs-lookup"><span data-stu-id="40ac0-103">As new features are developed in the future, they will only be included in the Mixed Reality OpenXR plugin going forward.</span></span>

<span data-ttu-id="40ac0-104">Mixed Reality OpenXR 外掛程式完全支援 AR Foundation 4.0，提供 ARPlaneManager 和 ARRaycastManager 執行。</span><span class="sxs-lookup"><span data-stu-id="40ac0-104">The Mixed Reality OpenXR plugin fully supports AR Foundation 4.0, providing ARPlaneManager and ARRaycastManager implementations.</span></span> <span data-ttu-id="40ac0-105">這可讓您撰寫 raycasting 程式碼一次，然後跨越 HoloLens 2 和 ARCore/ARKit 手機和平板電腦。</span><span class="sxs-lookup"><span data-stu-id="40ac0-105">This enables you to write raycasting code once that then spans HoloLens 2 and ARCore/ARKit phones and tablets.</span></span>

### <a name="prerequisites"></a><span data-ttu-id="40ac0-106">必要條件</span><span class="sxs-lookup"><span data-stu-id="40ac0-106">Prerequisites</span></span> 

* <span data-ttu-id="40ac0-107">[適用于 HoloLens 2 開發的](../../../install-the-tools.md?tabs=unity#installation-checklist)最新工具</span><span class="sxs-lookup"><span data-stu-id="40ac0-107">Latest [tools for HoloLens 2 development](../../../install-the-tools.md?tabs=unity#installation-checklist)</span></span>
* <span data-ttu-id="40ac0-108">最新的 Unity 2020.3 LTS， (我們建議 2020.3.8 f1 或更新版本) </span><span class="sxs-lookup"><span data-stu-id="40ac0-108">Latest Unity 2020.3 LTS, (we recommend 2020.3.8f1 or above)</span></span>

### <a name="minimum-versions"></a><span data-ttu-id="40ac0-109">最小版本</span><span class="sxs-lookup"><span data-stu-id="40ac0-109">Minimum versions</span></span>

<span data-ttu-id="40ac0-110">此頁面中的指示將會為您設定下列最新且最棒的 Unity 和 OpenXR 需求：</span><span class="sxs-lookup"><span data-stu-id="40ac0-110">The instructions in this page will set you up with the latest and greatest Unity and OpenXR requirements listed below:</span></span>

* <span data-ttu-id="40ac0-111">最新的 Unity OpenXR 外掛程式， (建議1.2 或更新版本) </span><span class="sxs-lookup"><span data-stu-id="40ac0-111">Latest Unity OpenXR plugin, (we recommend 1.2 or later)</span></span>
* <span data-ttu-id="40ac0-112">最新的混合現實 OpenXR 外掛程式， (建議1.0.0 版或更新版本) </span><span class="sxs-lookup"><span data-stu-id="40ac0-112">Latest Mixed Reality OpenXR Plugin, (we recommend version 1.0.0 or later)</span></span>
* <span data-ttu-id="40ac0-113">如果您的專案使用 MRTK，建議使用版本2.7.2 或更新版本</span><span class="sxs-lookup"><span data-stu-id="40ac0-113">If your project uses MRTK, we recommend version 2.7.2 or later</span></span>
* <span data-ttu-id="40ac0-114">如果您的專案使用通用轉譯管線 (URP) 封裝，我們建議使用10.5.1 或更新版本</span><span class="sxs-lookup"><span data-stu-id="40ac0-114">If your project uses Universal Render Pipeline (URP) package, we recommend version 10.5.1 or later</span></span>

<!-- ![Screenshot of the open xr unity basic sample running on a HoloLens](../../images/openxr-example.png) -->

> [!NOTE]
> <span data-ttu-id="40ac0-115">如果您是在 Windows 電腦上建立 VR 應用程式，則不一定需要混合現實 OpenXR 外掛程式。</span><span class="sxs-lookup"><span data-stu-id="40ac0-115">If you're building VR applications on Windows PC, the Mixed Reality OpenXR plugin is not necessarily required.</span></span> <span data-ttu-id="40ac0-116">但是，如果您要自訂適用于 HP 重設系的控制器對應，或建立可在 HoloLens 2 和 VR 耳機上運作的應用程式，則您會想要安裝外掛程式。</span><span class="sxs-lookup"><span data-stu-id="40ac0-116">However, you'll want to install the plugin if you're customizing controller mapping for HP Reverb G2 controllers or building apps that work on both HoloLens 2 and VR headsets.</span></span>

# <a name="windows-xr"></a>[<span data-ttu-id="40ac0-117">Windows XR</span><span class="sxs-lookup"><span data-stu-id="40ac0-117">Windows XR</span></span>](#tab/windowsxr)

<span data-ttu-id="40ac0-118">Microsoft 不建議針對 Unity 2020 中的任何新專案使用 Windows XR 外掛程式。</span><span class="sxs-lookup"><span data-stu-id="40ac0-118">Microsoft doesn't recommend using the Windows XR plugin for any new projects in Unity 2020.</span></span>

<span data-ttu-id="40ac0-119">不過，如果您使用 Unity 2019，而且需要 AR Foundation 2.0 才能與 ARCore/ARKit 裝置相容，此外掛程式會啟用該支援。</span><span class="sxs-lookup"><span data-stu-id="40ac0-119">However, if you're using Unity 2019 and you need AR Foundation 2.0 for compatibility with ARCore/ARKit devices, this plugin enables that support.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="40ac0-120">在 Unity 2019 中使用此外掛程式不支援 Azure 空間錨點。</span><span class="sxs-lookup"><span data-stu-id="40ac0-120">Using this plugin in Unity 2019 doesn't support Azure Spatial Anchors.</span></span> 

# <a name="legacy-xr"></a>[<span data-ttu-id="40ac0-121">傳統 XR</span><span class="sxs-lookup"><span data-stu-id="40ac0-121">Legacy XR</span></span>](#tab/legacy)

<span data-ttu-id="40ac0-122">如果您仍在 Unity 2019 或更早版本，Microsoft 建議使用舊版內建 XR 支援。</span><span class="sxs-lookup"><span data-stu-id="40ac0-122">If you're still on Unity 2019 or earlier, Microsoft recommends using the Legacy Built-in XR support.</span></span> <span data-ttu-id="40ac0-123">雖然 Windows XR 外掛程式可在 Unity 2019 上運作，但不建議使用，因為不支援 Azure 空間錨點。</span><span class="sxs-lookup"><span data-stu-id="40ac0-123">While the Windows XR plugin is functional on Unity 2019, it's not recommended because Azure Spatial Anchors isn't supported.</span></span>