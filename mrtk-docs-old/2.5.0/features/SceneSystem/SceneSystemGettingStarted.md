---
title: SceneSystemGettingStarted
description: 具有 MRTK 之場景系統的登陸頁面
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: 4cfc8d21a069dd8dbdad900d555c2539c89dff7b
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104689888"
---
# <a name="scene-system-overview"></a><span data-ttu-id="7f09b-104">場景系統總覽</span><span class="sxs-lookup"><span data-stu-id="7f09b-104">Scene system overview</span></span>

## <a name="when-to-use-the-scene-system"></a><span data-ttu-id="7f09b-105">使用場景系統的時機</span><span class="sxs-lookup"><span data-stu-id="7f09b-105">When to use the scene system</span></span>

<span data-ttu-id="7f09b-106">如果您的專案包含單一場景，則可能不需要場景系統。</span><span class="sxs-lookup"><span data-stu-id="7f09b-106">If your project consists of a single scene, the Scene System probably isn't necessary.</span></span> <span data-ttu-id="7f09b-107">當下列一或多項條件成立時，最有用：</span><span class="sxs-lookup"><span data-stu-id="7f09b-107">It is most useful when one or more of the following are true:</span></span>

- <span data-ttu-id="7f09b-108">您的專案有多個場景。</span><span class="sxs-lookup"><span data-stu-id="7f09b-108">Your project has multiple scenes.</span></span>
- <span data-ttu-id="7f09b-109">您可以使用單一場景載入，但您不喜歡它終結 MixedRealityToolkit 實例的方式。</span><span class="sxs-lookup"><span data-stu-id="7f09b-109">You're used to single scene loading, but you don't like the way it destroys the MixedRealityToolkit instance.</span></span>
- <span data-ttu-id="7f09b-110">您需要簡單的方法來額外載入多個場景，以建立您的體驗。</span><span class="sxs-lookup"><span data-stu-id="7f09b-110">You want a simple way to additively load multiple scenes to construct your experience.</span></span>
- <span data-ttu-id="7f09b-111">您需要簡單的方法來追蹤進行中的載入作業，或使用簡單的方式來控制一次載入多個場景的場景啟用。</span><span class="sxs-lookup"><span data-stu-id="7f09b-111">You want a simple way to keep track of load operations in progress or a simple way to control scene activation for multiple scenes being loaded at once.</span></span>
- <span data-ttu-id="7f09b-112">您想要讓燈光保持一致，並可在所有場景中預測。</span><span class="sxs-lookup"><span data-stu-id="7f09b-112">You want to keep lighting consistent and predictable across all your scenes.</span></span>

## <a name="how-to-use-the-scene-system"></a><span data-ttu-id="7f09b-113">如何使用場景系統</span><span class="sxs-lookup"><span data-stu-id="7f09b-113">How to use the scene system</span></span>

- [<span data-ttu-id="7f09b-114">場景類型</span><span class="sxs-lookup"><span data-stu-id="7f09b-114">Scene Types</span></span>](SceneSystemSceneTypes.md)
- [<span data-ttu-id="7f09b-115">內容場景載入</span><span class="sxs-lookup"><span data-stu-id="7f09b-115">Content Scene Loading</span></span>](SceneSystemContentLoading.md)
- [<span data-ttu-id="7f09b-116">監視內容載入</span><span class="sxs-lookup"><span data-stu-id="7f09b-116">Monitoring Content Loading</span></span>](SceneSystemLoadProgress.md)
- [<span data-ttu-id="7f09b-117">照明場景載入</span><span class="sxs-lookup"><span data-stu-id="7f09b-117">Lighting Scene Loading</span></span>](SceneSystemLightingScenes.md)

## <a name="editor-settings"></a><span data-ttu-id="7f09b-118">編輯器設定</span><span class="sxs-lookup"><span data-stu-id="7f09b-118">Editor settings</span></span>

<span data-ttu-id="7f09b-119">根據預設，場景系統會在 Unity 編輯器中強制執行數個行為。</span><span class="sxs-lookup"><span data-stu-id="7f09b-119">By default, the Scene System enforces several behaviors in the Unity editor.</span></span> <span data-ttu-id="7f09b-120">如果您發現任何這些行為很繁重，可以在場景系統設定檔的 **編輯器設定** 區段中加以停用。</span><span class="sxs-lookup"><span data-stu-id="7f09b-120">If you find any of these behaviors heavy-handed, they can be disabled in the **Editor Settings** section of your Scene System profile.</span></span>

- <span data-ttu-id="7f09b-121">`Editor Manage Build Settings:` 若為 true，服務會自動更新您的組建設定，以確保所有管理員、光源和內容場景都會加入。</span><span class="sxs-lookup"><span data-stu-id="7f09b-121">`Editor Manage Build Settings:` If true, the service will update your build settings automatically, ensuring that all manager, lighting and content scenes are added.</span></span> <span data-ttu-id="7f09b-122">如果您想要完全掌控組建設定，請停用此值。</span><span class="sxs-lookup"><span data-stu-id="7f09b-122">Disable this if you want total control over build settings.</span></span>

- <span data-ttu-id="7f09b-123">`Editor Enforce Scene Order:` 若為 true，服務將確保管理員場景先顯示在場景階層中，後面接著光源和內容。</span><span class="sxs-lookup"><span data-stu-id="7f09b-123">`Editor Enforce Scene Order:` If true, the service will ensure that the manager scene is displayed first in scene hierarchy, followed by lighting and then content.</span></span> <span data-ttu-id="7f09b-124">如果您想要完全掌控場景階層，請停用此。</span><span class="sxs-lookup"><span data-stu-id="7f09b-124">Disable this if you want total control over scene hierarchy.</span></span>

- <span data-ttu-id="7f09b-125">`Editor Manage Loaded Scenes:` 若為 true，服務將確保一律會載入管理員、內容和光源場景。</span><span class="sxs-lookup"><span data-stu-id="7f09b-125">`Editor Manage Loaded Scenes:` If true, the service will ensure that the manager, content and lighting scenes are always loaded.</span></span> <span data-ttu-id="7f09b-126">如果您想要完全掌控編輯器中載入的場景，請停用。</span><span class="sxs-lookup"><span data-stu-id="7f09b-126">Disable if you want total control over which scenes are loaded in editor.</span></span>

- <span data-ttu-id="7f09b-127">`Editor Enforce Lighting Scene Types:` 若為 true，服務將確保光源只允許在中定義光源相關的元件 `PermittedLightingSceneComponentTypes` 。</span><span class="sxs-lookup"><span data-stu-id="7f09b-127">`Editor Enforce Lighting Scene Types:` If true, the service will ensure that only the lighting-related components defined in `PermittedLightingSceneComponentTypes` are allowed in lighting scenes.</span></span> <span data-ttu-id="7f09b-128">如果您想要完全掌控燈光場景的內容，請停用。</span><span class="sxs-lookup"><span data-stu-id="7f09b-128">Disable if you want total control over the content of lighting scenes.</span></span>

![場景系統編輯器設定](../Images/SceneSystem/MRTK_SceneSystemProfileEditorSettings.PNG)
