---
ms.openlocfilehash: eaa2651a22fd5b2b601493845d507aeda6745f1a
ms.sourcegitcommit: e380d56f5504be4e4f069394a58cf0147eb33b66
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2021
ms.locfileid: "113603705"
---
# <a name="openxr"></a>[<span data-ttu-id="d89fe-101">OpenXR</span><span class="sxs-lookup"><span data-stu-id="d89fe-101">OpenXR</span></span>](#tab/openxr)

<span data-ttu-id="d89fe-102">Mixed Reality OpenXR 外掛程式是 Microsoft 對 **Unity 2020 LTS** 或更新版本的 **建議**。</span><span class="sxs-lookup"><span data-stu-id="d89fe-102">The Mixed Reality OpenXR plugin is **Microsoft's recommendation** for **Unity 2020 LTS** or later.</span></span> <span data-ttu-id="d89fe-103">在未來開發新功能時，它們只會包含在混合現實 OpenXR 外掛程式中。</span><span class="sxs-lookup"><span data-stu-id="d89fe-103">As new features are developed in the future, they will only be included in the Mixed Reality OpenXR plugin going forward.</span></span>

<span data-ttu-id="d89fe-104">Mixed Reality OpenXR 外掛程式完全支援 AR Foundation 4.0，提供 ARPlaneManager 和 ARRaycastManager 執行。</span><span class="sxs-lookup"><span data-stu-id="d89fe-104">The Mixed Reality OpenXR plugin fully supports AR Foundation 4.0, providing ARPlaneManager and ARRaycastManager implementations.</span></span> <span data-ttu-id="d89fe-105">這可讓您撰寫 raycasting 程式碼一次，然後跨越 HoloLens 2 和 ARCore/ARKit 手機和平板電腦。</span><span class="sxs-lookup"><span data-stu-id="d89fe-105">This enables you to write raycasting code once that then spans HoloLens 2 and ARCore/ARKit phones and tablets.</span></span>

### <a name="prerequisites"></a><span data-ttu-id="d89fe-106">必要條件</span><span class="sxs-lookup"><span data-stu-id="d89fe-106">Prerequisites</span></span> 

* <span data-ttu-id="d89fe-107">[適用于 HoloLens 2 開發的](../../../install-the-tools.md?tabs=unity#installation-checklist)最新工具</span><span class="sxs-lookup"><span data-stu-id="d89fe-107">Latest [tools for HoloLens 2 development](../../../install-the-tools.md?tabs=unity#installation-checklist)</span></span>
* <span data-ttu-id="d89fe-108">最新的 Unity 2020.3 LTS：版本 2020.3.8 f1 或更新版本</span><span class="sxs-lookup"><span data-stu-id="d89fe-108">Latest Unity 2020.3 LTS: version 2020.3.8f1 or later</span></span>

### <a name="recommended-package-versions"></a><span data-ttu-id="d89fe-109">建議的套件版本</span><span class="sxs-lookup"><span data-stu-id="d89fe-109">Recommended package versions</span></span>

<span data-ttu-id="d89fe-110">此頁面中的指示將會為您設定部署 HoloLens 2 或 Windows Mixed Reality 應用程式所需的核心 Unity OpenXR 套件：</span><span class="sxs-lookup"><span data-stu-id="d89fe-110">The instructions in this page will set you up with the core Unity OpenXR packages required to deploy HoloLens 2 or Windows Mixed Reality apps:</span></span>

* <span data-ttu-id="d89fe-111">Unity OpenXR 外掛程式：1.2 版或更新版本</span><span class="sxs-lookup"><span data-stu-id="d89fe-111">Unity OpenXR plugin: version 1.2 or later</span></span>
* <span data-ttu-id="d89fe-112">Mixed Reality OpenXR 外掛程式：1.0.0 版或更新版本</span><span class="sxs-lookup"><span data-stu-id="d89fe-112">Mixed Reality OpenXR plugin: version 1.0.0 or later</span></span>

<span data-ttu-id="d89fe-113">如果您在專案中使用下列封裝，您將必須確定至少使用下列最小版本：</span><span class="sxs-lookup"><span data-stu-id="d89fe-113">If you use the following packages in your project, you will need to ensure that you use at least the minimum versions listed below:</span></span>

* <span data-ttu-id="d89fe-114">MRTK： version 2.7.2 或更新版本</span><span class="sxs-lookup"><span data-stu-id="d89fe-114">MRTK: version 2.7.2 or later</span></span>
* <span data-ttu-id="d89fe-115">AR Foundation： version 4.1.1 或更新版本</span><span class="sxs-lookup"><span data-stu-id="d89fe-115">AR Foundation: version 4.1.1 or later</span></span>
* <span data-ttu-id="d89fe-116">通用轉譯管線 (URP) ： version 10.5.1 或更新版本</span><span class="sxs-lookup"><span data-stu-id="d89fe-116">Universal Render Pipeline (URP): version 10.5.1 or later</span></span>
* <span data-ttu-id="d89fe-117">Azure 空間錨點：2.10 版或更新版本</span><span class="sxs-lookup"><span data-stu-id="d89fe-117">Azure Spatial Anchors: version 2.10 or later</span></span>
* <span data-ttu-id="d89fe-118">Azure 遠端轉譯： version 1.0.15 或更新版本</span><span class="sxs-lookup"><span data-stu-id="d89fe-118">Azure Remote Rendering: version 1.0.15 or later</span></span>

> [!NOTE]
> <span data-ttu-id="d89fe-119">如果您要在 Windows 電腦上建立 VR 應用程式，則不一定需要 Mixed Reality OpenXR 外掛程式。</span><span class="sxs-lookup"><span data-stu-id="d89fe-119">If you're building VR applications on Windows PC, the Mixed Reality OpenXR plugin is not strictly required.</span></span> <span data-ttu-id="d89fe-120">但是，如果您要設定適用于 HP 重送 G2 控制器的輸入系結，或建立可在 HoloLens 2 和 VR 耳機上運作的應用程式，則您會想要安裝外掛程式。</span><span class="sxs-lookup"><span data-stu-id="d89fe-120">However, you'll want to install the plugin if you're setting up input bindings for HP Reverb G2 controllers or building apps that work on both HoloLens 2 and VR headsets.</span></span>

# <a name="windows-xr"></a>[<span data-ttu-id="d89fe-121">WindowsXR</span><span class="sxs-lookup"><span data-stu-id="d89fe-121">Windows XR</span></span>](#tab/windowsxr)

<span data-ttu-id="d89fe-122">Microsoft 不建議針對 Unity 2020 中的任何新專案使用 Windows XR 外掛程式。</span><span class="sxs-lookup"><span data-stu-id="d89fe-122">Microsoft doesn't recommend using the Windows XR plugin for any new projects in Unity 2020.</span></span>  <span data-ttu-id="d89fe-123">相反地，您應該使用 Mixed Reality OpenXR 外掛程式。</span><span class="sxs-lookup"><span data-stu-id="d89fe-123">Instead, you should use the Mixed Reality OpenXR plugin.</span></span>

<span data-ttu-id="d89fe-124">不過，如果您使用 Unity 2019，而且需要 AR Foundation 2.0 才能與 ARCore/ARKit 裝置相容，此外掛程式會啟用該支援。</span><span class="sxs-lookup"><span data-stu-id="d89fe-124">However, if you're using Unity 2019 and you need AR Foundation 2.0 for compatibility with ARCore/ARKit devices, this plugin enables that support.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d89fe-125">在 Unity 2019 中使用此外掛程式與 Azure 空間錨點不相容。</span><span class="sxs-lookup"><span data-stu-id="d89fe-125">Using this plugin in Unity 2019 is not compatible with Azure Spatial Anchors.</span></span>

# <a name="legacy-xr"></a>[<span data-ttu-id="d89fe-126">傳統 XR</span><span class="sxs-lookup"><span data-stu-id="d89fe-126">Legacy XR</span></span>](#tab/legacy)

<span data-ttu-id="d89fe-127">如果您仍在 **Unity 2019** 或更早版本，Microsoft 建議使用 **舊版內建 XR 支援**。</span><span class="sxs-lookup"><span data-stu-id="d89fe-127">If you're still on **Unity 2019** or earlier, Microsoft recommends using the **Legacy Built-in XR support**.</span></span>

<span data-ttu-id="d89fe-128">雖然 Windows XR 外掛程式可在 unity 2019 上運作，但不建議使用，因為此外掛程式與 unity 2019 上的 Azure 空間錨點不相容。</span><span class="sxs-lookup"><span data-stu-id="d89fe-128">While the Windows XR plugin is functional on Unity 2019, it's not recommended because this plugin is not compatible with Azure Spatial Anchors on Unity 2019.</span></span>

<span data-ttu-id="d89fe-129">如果您要開始新的專案，建議您 [改為安裝 Unity 2020](../../choosing-unity-version.md) ，並使用 Mixed Reality OpenXR 外掛程式。</span><span class="sxs-lookup"><span data-stu-id="d89fe-129">If you're starting a new project, we recommend [installing Unity 2020 instead](../../choosing-unity-version.md) and using the Mixed Reality OpenXR plugin.</span></span>