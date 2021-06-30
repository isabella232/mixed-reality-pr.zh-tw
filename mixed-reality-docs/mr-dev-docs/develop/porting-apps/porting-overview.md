---
title: 移植概觀
description: 介紹各種移植選項，以將現有應用程式用於 HoloLens 和 VR 的混合現實。
author: hferrone
ms.author: v-hferrone
ms.date: 12/9/2020
ms.topic: article
keywords: 移植、unity、中介軟體、引擎、UWP、Win32
ms.openlocfilehash: 167559d69cc4e65f971a8970b56e41e6e3ca8b22
ms.sourcegitcommit: 12ea3fb2df4664c5efd07dcbb9040c2ff173afb6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/29/2021
ms.locfileid: "113042269"
---
# <a name="porting-overview"></a><span data-ttu-id="2ebae-104">移植概觀</span><span class="sxs-lookup"><span data-stu-id="2ebae-104">Porting overview</span></span>

<span data-ttu-id="2ebae-105">當您想要移植或升級現有的專案時，您的移植旅程取決於您的應用程式是使用 Unity 或 Unreal 引擎所建立，並以 HoloLens (第1代) 或 HoloLens 2 或 SteamVR 為目標。</span><span class="sxs-lookup"><span data-stu-id="2ebae-105">When it comes to porting or upgrading your existing projects for Mixed Reality, your porting journey depends on whether your app is built with Unity or Unreal Engine, and targets HoloLens (1st Gen) or HoloLens 2, or SteamVR.</span></span> <span data-ttu-id="2ebae-106">此總覽頁面包含我們針對每個平臺和裝置目前的建議-請務必回頭查看這些流程一律會變更。</span><span class="sxs-lookup"><span data-stu-id="2ebae-106">This overview page contains our current recommendations for each platform and device - be sure to check back as these processes are always changing.</span></span>

<span data-ttu-id="2ebae-107">首先，根據我們的 [Unity](#unity) 和 [Unreal](#unreal) 建議來設定您的專案目標，然後遵循一或多個移植案例：</span><span class="sxs-lookup"><span data-stu-id="2ebae-107">First, set up your project target based on either our [Unity](#unity) and [Unreal](#unreal) recommendations, then follow one or more of our porting scenarios:</span></span>

- [<span data-ttu-id="2ebae-108">HoloLens (第1代) 至 HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="2ebae-108">HoloLens (1st Gen) to HoloLens 2</span></span>](#hololens-1st-gen-unity-apps-to-hololens-2)
- [<span data-ttu-id="2ebae-109">沉浸式 VR 頭戴裝置</span><span class="sxs-lookup"><span data-stu-id="2ebae-109">Immersive VR headsets</span></span>](#immersive-vr-headsets)
- [<span data-ttu-id="2ebae-110">2D UWP 應用程式</span><span class="sxs-lookup"><span data-stu-id="2ebae-110">2D UWP apps</span></span>](#2d-universal-windows-applications)

## <a name="recommended-project-targets"></a><span data-ttu-id="2ebae-111">建議的專案目標</span><span class="sxs-lookup"><span data-stu-id="2ebae-111">Recommended project targets</span></span>

<span data-ttu-id="2ebae-112">無論您是將應用程式移植到另一個目標裝置，都必須保持您的專案最新狀態。</span><span class="sxs-lookup"><span data-stu-id="2ebae-112">It's important to keep your projects up to date, whether your porting an app to another target device.</span></span> <span data-ttu-id="2ebae-113">如需我們目前的建議，請參閱下列以引擎為基礎的資源。</span><span class="sxs-lookup"><span data-stu-id="2ebae-113">Refer to the engine-based resources listed below for our current recommendations.</span></span>

### <a name="unity"></a><span data-ttu-id="2ebae-114">Unity</span><span class="sxs-lookup"><span data-stu-id="2ebae-114">Unity</span></span>

<span data-ttu-id="2ebae-115">如需建議的 Unity 和 MRTK 版本的最新指引，請參閱 [選擇 Unity 版本](../unity/choosing-unity-version.md) 頁面。</span><span class="sxs-lookup"><span data-stu-id="2ebae-115">See the [Choosing a Unity version](../unity/choosing-unity-version.md) page for up-to-date guidance on the recommended Unity and MRTK versions.</span></span>

### <a name="unreal"></a><span data-ttu-id="2ebae-116">Unreal</span><span class="sxs-lookup"><span data-stu-id="2ebae-116">Unreal</span></span>

<span data-ttu-id="2ebae-117">如需建議的 Unreal 和 MRTK 版本的最新指引，請參閱 [設定 Unreal 專案](../unreal/unreal-project-setup.md) 頁面。</span><span class="sxs-lookup"><span data-stu-id="2ebae-117">See the [Setting up your Unreal project](../unreal/unreal-project-setup.md) page for up-to-date guidance on the recommended Unreal and MRTK versions.</span></span>

## <a name="porting-scenarios"></a><span data-ttu-id="2ebae-118">移植案例</span><span class="sxs-lookup"><span data-stu-id="2ebae-118">Porting scenarios</span></span>

### <a name="hololens-1st-gen-unity-apps-to-hololens-2"></a><span data-ttu-id="2ebae-119">HoloLens (第1代) Unity 應用程式到 HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="2ebae-119">HoloLens (1st Gen) Unity apps to HoloLens 2</span></span>

<span data-ttu-id="2ebae-120">如果您有現有的 HoloLens (第1代) Unity 應用程式，而您想要將其移植到 HoloLens 2，請依照 [HoloLens 移植文章](./porting-hl1-hl2.md)中的指示進行。</span><span class="sxs-lookup"><span data-stu-id="2ebae-120">If you have an existing HoloLens (1st Gen) Unity application that you'd like to port over to a HoloLens 2, follow the instructions in our [HoloLens porting article](./porting-hl1-hl2.md).</span></span>

### <a name="immersive-vr-headsets"></a><span data-ttu-id="2ebae-121">沉浸式 VR 頭戴裝置</span><span class="sxs-lookup"><span data-stu-id="2ebae-121">Immersive VR headsets</span></span>

<span data-ttu-id="2ebae-122">如果您已建立其他 VR 裝置的內容，則必須將任何廠商專屬的 VR Sdk 和可能的輸入對應 Api 重定目標。</span><span class="sxs-lookup"><span data-stu-id="2ebae-122">If you've built content for other VR devices, you'll need to retarget any vendor-specific VR SDKs and potentially input-mapping APIs.</span></span> <span data-ttu-id="2ebae-123">您可以在「 [沉浸式應用程式移植指南](porting-guides.md)」中找到 Unity 和 Unreal 移植案例的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="2ebae-123">You can find information for both Unity and Unreal porting scenarios in our [immersive apps porting guide](porting-guides.md).</span></span>

<span data-ttu-id="2ebae-124">如需您想要更新 Windows Mixed Reality 耳機的 SteamVR 體驗，請參閱我們的 [SteamVR 更新指南](updating-your-steamvr-application-for-windows-mixed-reality.md)。</span><span class="sxs-lookup"><span data-stu-id="2ebae-124">For SteamVR experiences that you want to update for Windows Mixed Reality headsets, refer to our [SteamVR updating guide](updating-your-steamvr-application-for-windows-mixed-reality.md).</span></span>

### <a name="2d-universal-windows-applications"></a><span data-ttu-id="2ebae-125">2D 通用 Windows 應用程式</span><span class="sxs-lookup"><span data-stu-id="2ebae-125">2D Universal Windows applications</span></span>

<span data-ttu-id="2ebae-126">如果您有想要移植到 Windows Mixed Reality 沉浸式耳機或 HoloLens 的現有 2D UWP 應用程式，請遵循我們 [的移植 2D uwp 應用程式，以取得 Windows Mixed Reality 的](building-2d-apps.md) 指示。</span><span class="sxs-lookup"><span data-stu-id="2ebae-126">If you have an existing 2D UWP app that you'd like to port to either a Windows Mixed Reality immersive headset or HoloLens, follow our [porting 2D UWP apps for Windows Mixed Reality](building-2d-apps.md) instructions.</span></span>