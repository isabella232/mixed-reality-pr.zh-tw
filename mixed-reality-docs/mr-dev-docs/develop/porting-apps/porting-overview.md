---
title: 移植總覽
description: 概述將現有應用程式帶入混合現實的各種移植選項。
author: hferrone
ms.author: v-hferrone
ms.date: 10/02/2020
ms.topic: article
keywords: 移植、unity、中介軟體、引擎、UWP、Win32
ms.openlocfilehash: 074e0792a5ed43bb56b8f337613234efbd166eb7
ms.sourcegitcommit: 9664bcc10ed7e60f7593f3a7ae58c66060802ab1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96443543"
---
# <a name="porting-overview"></a><span data-ttu-id="81adf-104">移植總覽</span><span class="sxs-lookup"><span data-stu-id="81adf-104">Porting overview</span></span>

<span data-ttu-id="81adf-105">當您將現有專案移植或升級為混合的實際專案時，可能會根據您的應用程式是使用 Unity 或 Unreal 引擎、HoloLens (第一代) 或 HoloLens 2，或 SteamVR 來進行。</span><span class="sxs-lookup"><span data-stu-id="81adf-105">When it comes to porting or upgrading your existing projects for Mixed Reality, several scenarios may apply depending on whether your app was built with Unity or Unreal Engine, HoloLens (1st Gen) or HoloLens 2, or SteamVR.</span></span> <span data-ttu-id="81adf-106">此總覽頁面包含我們針對每個平臺和裝置目前的建議-請務必回頭查看這些流程一律會變更。</span><span class="sxs-lookup"><span data-stu-id="81adf-106">This overview page contains our current recommendations for each platform and device - be sure to check back as these processes are always changing.</span></span>

<span data-ttu-id="81adf-107">首先，根據我們的 [Unity](#unity) 和 [Unreal](#unreal) 建議來設定您的專案目標，然後遵循一或多個移植案例：</span><span class="sxs-lookup"><span data-stu-id="81adf-107">First, setup your project target based on either our [Unity](#unity) and [Unreal](#unreal) recommendations, then follow one or more of our porting scenarios:</span></span>

- [<span data-ttu-id="81adf-108">HoloLens (第1代) 至 HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="81adf-108">HoloLens (1st Gen) to HoloLens 2</span></span>](#hololens-1st-gen-unity-apps-to-hololens-2)
- [<span data-ttu-id="81adf-109">Windows Mixed Reality 頭戴式裝置</span><span class="sxs-lookup"><span data-stu-id="81adf-109">Windows Mixed Reality headsets</span></span>](#windows-mixed-reality-headsets)
- [<span data-ttu-id="81adf-110">SteamVR 應用程式</span><span class="sxs-lookup"><span data-stu-id="81adf-110">SteamVR apps</span></span>](#steamvr-applications)
- [<span data-ttu-id="81adf-111">2D UWP 應用程式</span><span class="sxs-lookup"><span data-stu-id="81adf-111">2D UWP apps</span></span>](#2d-universal-windows-applications)

## <a name="recommended-project-targets"></a><span data-ttu-id="81adf-112">建議的專案目標</span><span class="sxs-lookup"><span data-stu-id="81adf-112">Recommended project targets</span></span>

<span data-ttu-id="81adf-113">無論您是否將應用程式移植到另一個目標裝置，都必須保持您的專案最新狀態。</span><span class="sxs-lookup"><span data-stu-id="81adf-113">It's important to keep your projects up-to-date, whether or not your porting an app to another target device.</span></span> <span data-ttu-id="81adf-114">如需我們目前的建議，請參閱下列以引擎為基礎的資源。</span><span class="sxs-lookup"><span data-stu-id="81adf-114">Refer to the engine-based resources listed below for our current recommendations.</span></span>

### <a name="unity"></a><span data-ttu-id="81adf-115">Unity</span><span class="sxs-lookup"><span data-stu-id="81adf-115">Unity</span></span>

<span data-ttu-id="81adf-116">我們目前有混合現實的 Unity 開發建議，是 **使用舊版 XR 封裝的 unity 2019 LTS**。</span><span class="sxs-lookup"><span data-stu-id="81adf-116">Our current recommendation for Unity development with Mixed Reality is **Unity 2019 LTS using the Legacy XR package**.</span></span> <span data-ttu-id="81adf-117">如果您的專案使用 Mixed Reality 工具組，請再次檢查您是否使用最新版本，也就是目前的 **MRTK-Unity 2.5**。</span><span class="sxs-lookup"><span data-stu-id="81adf-117">If your project uses the Mixed Reality Toolkit, double-check that you're on the latest version, which is currently **MRTK-Unity 2.5**.</span></span>

> [!CAUTION]
> <span data-ttu-id="81adf-118">雖然此版本的 Unity 可使用 XR SDK，但 Azure 空間錨點目前不與此設定相容。</span><span class="sxs-lookup"><span data-stu-id="81adf-118">While the XR SDK is available with this version of Unity, Azure Spatial Anchors is not currently compatible with this setup.</span></span> <span data-ttu-id="81adf-119">這項建議將會更新為適用于 Unity 的 Azure 空間錨點套件未來版本。</span><span class="sxs-lookup"><span data-stu-id="81adf-119">This recommendation will be updated with a future release of the Azure Spatial Anchors package for Unity.</span></span> 
> 
> * <span data-ttu-id="81adf-120">如果您不需要 Azure 空間錨點，您可以 [設定您的 Unity 專案以進行 XR](https://docs.unity3d.com/Manual/configuring-project-for-xr.html) ，並 [開始使用 MRTK 和 XR SDK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithMRTKAndXRSDK.html)。</span><span class="sxs-lookup"><span data-stu-id="81adf-120">If you don't need Azure Spatial Anchors, you can [configure your Unity project for XR](https://docs.unity3d.com/Manual/configuring-project-for-xr.html) and [get started with MRTK and XR SDK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithMRTKAndXRSDK.html).</span></span>
> 
> * <span data-ttu-id="81adf-121">如果您目前在專案中使用 XR SDK，而且想要使用 Azure 空間錨點，請將 XR SDK 卸載，然後重新安裝舊版 XR 套件來還原您的專案設定。</span><span class="sxs-lookup"><span data-stu-id="81adf-121">If you're currently using the XR SDK in your project and want to use Azure Spatial Anchors, uninstall XR SDK and reinstall the Legacy XR package to revert your project settings.</span></span>


### <a name="unreal"></a><span data-ttu-id="81adf-122">Unreal</span><span class="sxs-lookup"><span data-stu-id="81adf-122">Unreal</span></span> 

<span data-ttu-id="81adf-123">我們目前對混合現實的 Unreal 開發建議是 **Unreal Engine 4.26**。</span><span class="sxs-lookup"><span data-stu-id="81adf-123">Our current recommendation for Unreal development with Mixed Reality is **Unreal Engine 4.26**.</span></span> <span data-ttu-id="81adf-124">如果您的專案使用「混合現實工具組 UX 工具」，請確定您使用的是最新版本，其目前為 **UXT 0.10**。</span><span class="sxs-lookup"><span data-stu-id="81adf-124">If your project uses the Mixed Reality Toolkit UX Tools, make sure you're using the latest version, which is currently **UXT 0.10**.</span></span>

## <a name="porting-scenarios"></a><span data-ttu-id="81adf-125">移植案例</span><span class="sxs-lookup"><span data-stu-id="81adf-125">Porting scenarios</span></span>

### <a name="hololens-1st-gen-unity-apps-to-hololens-2"></a><span data-ttu-id="81adf-126">HoloLens (第1代) Unity 應用程式到 HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="81adf-126">HoloLens (1st Gen) Unity apps to HoloLens 2</span></span>

<span data-ttu-id="81adf-127">如果您有現有的 HoloLens (第1代) Unity 應用程式，而您想要將其移植到 HoloLens 2，請依照 [HoloLens 移植文章](../unity/mrtk-porting-guide.md)中的指示進行。</span><span class="sxs-lookup"><span data-stu-id="81adf-127">If you have an existing HoloLens (1st Gen) Unity application that you'd like to port over to a HoloLens 2, follow the instructions in our [HoloLens porting article](../unity/mrtk-porting-guide.md).</span></span>

### <a name="windows-mixed-reality-headsets"></a><span data-ttu-id="81adf-128">Windows Mixed Reality 頭戴式裝置</span><span class="sxs-lookup"><span data-stu-id="81adf-128">Windows Mixed Reality headsets</span></span>

<span data-ttu-id="81adf-129">如果您已為其他裝置（例如 Oculus Rift 或 HP 回送 G2）建立內容，您將必須重新鎖定廠商專屬的 VR Sdk 和可能的輸入對應 Api。</span><span class="sxs-lookup"><span data-stu-id="81adf-129">If you've built content for other devices, such as the Oculus Rift or HP Reverb G2, you'll need to re-target vendor-specific VR SDKs and potentially input mapping APIs.</span></span> <span data-ttu-id="81adf-130">您可以在「 [沉浸式應用程式移植指南](porting-guides.md)」中找到 Unity 和 Unreal 移植案例的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="81adf-130">You can find information for both Unity and Unreal porting scenarios in our [immersive apps porting guide](porting-guides.md).</span></span>

### <a name="steamvr-applications"></a><span data-ttu-id="81adf-131">SteamVR 應用程式</span><span class="sxs-lookup"><span data-stu-id="81adf-131">SteamVR applications</span></span>

<span data-ttu-id="81adf-132">如需任何您想要更新 Windows Mixed Reality 耳機的 SteamVR 體驗，請參閱我們的 [SteamVR 更新指南](updating-your-steamvr-application-for-windows-mixed-reality.md)。</span><span class="sxs-lookup"><span data-stu-id="81adf-132">For any SteamVR experiences that you want to update for Windows Mixed Reality headsets, refer to our [SteamVR updating guide](updating-your-steamvr-application-for-windows-mixed-reality.md).</span></span>

### <a name="2d-universal-windows-applications"></a><span data-ttu-id="81adf-133">2D 通用 Windows 應用程式</span><span class="sxs-lookup"><span data-stu-id="81adf-133">2D Universal Windows applications</span></span>

<span data-ttu-id="81adf-134">如果您有想要移植到 Windows Mixed Reality 沉浸式耳機或 HoloLens 的現有 2D UWP 應用程式，請遵循我們 [移植 2D uwp 應用程式](building-2d-apps.md) 中的指示，以取得 Windows Mixed Reality 文章。</span><span class="sxs-lookup"><span data-stu-id="81adf-134">If you have an existing 2D UWP app that you'd like to port to either a Windows Mixed Reality immersive headset or HoloLens, follow the instructions in our [porting 2D UWP apps for Windows Mixed Reality](building-2d-apps.md) article.</span></span>

