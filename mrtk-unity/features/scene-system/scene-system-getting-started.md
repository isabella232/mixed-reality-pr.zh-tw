---
title: SceneSystemGettingStarted
description: 具有 MRTK 之場景系統的登陸頁面
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: 92b0fa8df5e48d4a03ea168f18a77a49add255df
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/03/2021
ms.locfileid: "101781157"
---
# <a name="scene-system-overview"></a><span data-ttu-id="57543-104">場景系統總覽</span><span class="sxs-lookup"><span data-stu-id="57543-104">Scene system overview</span></span>

## <a name="when-to-use-the-scene-system"></a><span data-ttu-id="57543-105">使用場景系統的時機</span><span class="sxs-lookup"><span data-stu-id="57543-105">When to use the scene system</span></span>

<span data-ttu-id="57543-106">如果您的專案包含單一場景，則可能不需要場景系統。</span><span class="sxs-lookup"><span data-stu-id="57543-106">If your project consists of a single scene, the Scene System probably isn't necessary.</span></span> <span data-ttu-id="57543-107">當下列一或多項條件成立時，最有用：</span><span class="sxs-lookup"><span data-stu-id="57543-107">It is most useful when one or more of the following are true:</span></span>

- <span data-ttu-id="57543-108">您的專案有多個場景。</span><span class="sxs-lookup"><span data-stu-id="57543-108">Your project has multiple scenes.</span></span>
- <span data-ttu-id="57543-109">您可以使用單一場景載入，但您不喜歡它終結 MixedRealityToolkit 實例的方式。</span><span class="sxs-lookup"><span data-stu-id="57543-109">You're used to single scene loading, but you don't like the way it destroys the MixedRealityToolkit instance.</span></span>
- <span data-ttu-id="57543-110">您需要簡單的方法來額外載入多個場景，以建立您的體驗。</span><span class="sxs-lookup"><span data-stu-id="57543-110">You want a simple way to additively load multiple scenes to construct your experience.</span></span>
- <span data-ttu-id="57543-111">您需要簡單的方法來追蹤進行中的載入作業，或使用簡單的方式來控制一次載入多個場景的場景啟用。</span><span class="sxs-lookup"><span data-stu-id="57543-111">You want a simple way to keep track of load operations in progress or a simple way to control scene activation for multiple scenes being loaded at once.</span></span>
- <span data-ttu-id="57543-112">您想要讓燈光保持一致，並可在所有場景中預測。</span><span class="sxs-lookup"><span data-stu-id="57543-112">You want to keep lighting consistent and predictable across all your scenes.</span></span>

## <a name="scene-system-resources"></a><span data-ttu-id="57543-113">場景系統資源</span><span class="sxs-lookup"><span data-stu-id="57543-113">Scene System Resources</span></span>

<span data-ttu-id="57543-114">根據預設，場景系統會利用一對場景物件 (DefaultManagerScene 和 DefaultLighting 場景) 。</span><span class="sxs-lookup"><span data-stu-id="57543-114">By default, the Scene System utilizes a pair of scene objects (DefaultManagerScene and DefaultLighting scene).</span></span> <span data-ttu-id="57543-115">如果找不到任何一種場景，則會在場景系統設定檔偵測器中出現一則訊息。</span><span class="sxs-lookup"><span data-stu-id="57543-115">If either of these scenes cannot be located, a message will appear in the Scene System profile inspector.</span></span>

![預設資源訊息](../images/scene-system/DefaultResourcesMessage.png)

><span data-ttu-id="57543-117">!記如果專案使用自訂的管理員和燈光場景，則可以放心地忽略此訊息。</span><span class="sxs-lookup"><span data-stu-id="57543-117">![Note] If the project is using custom manager and lighting scenes, this message can be safely ignored.</span></span>

<span data-ttu-id="57543-118">下列各節將說明如何根據用來匯入混合現實工具組的方法，來解決此訊息。</span><span class="sxs-lookup"><span data-stu-id="57543-118">The following sections describe now to resolve this message, based on which method was used to import the Mixed Reality Toolkit.</span></span>

### <a name="unity-package-manager-upm"></a><span data-ttu-id="57543-119">Unity 套件管理員 (UPM) </span><span class="sxs-lookup"><span data-stu-id="57543-119">Unity Package Manager (UPM)</span></span>

<span data-ttu-id="57543-120">在混合現實工具組 UPM 套件中，場景系統資源會封裝成範例。</span><span class="sxs-lookup"><span data-stu-id="57543-120">In the Mixed Reality Toolkit UPM packages, the scene system resources are packaged as a sample.</span></span> <span data-ttu-id="57543-121">由於 UPM 套件是不可變的，因此 Unity 無法開啟必要的場景檔案，除非它們明確地匯入至專案中。</span><span class="sxs-lookup"><span data-stu-id="57543-121">Due to UPM packages being immutable, Unity is unable to open the necessary scene file unless they are explicitly imported into the project.</span></span>

<span data-ttu-id="57543-122">若要匯入，請使用下列步驟：</span><span class="sxs-lookup"><span data-stu-id="57543-122">To import use the following steps:</span></span>

- <span data-ttu-id="57543-123">選取 **視窗**  >  **套件管理員**</span><span class="sxs-lookup"><span data-stu-id="57543-123">Select **Window** > **Package Manager**</span></span>
- <span data-ttu-id="57543-124">選取 **混合現實工具組基礎**</span><span class="sxs-lookup"><span data-stu-id="57543-124">Select **Mixed Reality Toolkit Foundation**</span></span>
- <span data-ttu-id="57543-125">在 [**範例**] 區段中找出 **場景系統資源**</span><span class="sxs-lookup"><span data-stu-id="57543-125">Locate **Scene System Resources** in the **Samples** section</span></span>

  ![匯入場景系統資源](../images/scene-system/UpmImportSceneSystemResources.png)

- <span data-ttu-id="57543-127">選取匯 **入**</span><span class="sxs-lookup"><span data-stu-id="57543-127">Select **Import**</span></span>

### <a name="asset-unitypackage-files"></a><span data-ttu-id="57543-128">資產 ( unitypackage) 檔案</span><span class="sxs-lookup"><span data-stu-id="57543-128">Asset (.unitypackage) files</span></span>

<span data-ttu-id="57543-129">如果 SceneSystemResources 資料夾已被刪除，或在匯入時取消選取，則可以使用下列步驟來復原：</span><span class="sxs-lookup"><span data-stu-id="57543-129">If the SceneSystemResources folder has been deleted, or was deselected during import, it can be recovered using the following steps:</span></span>

- <span data-ttu-id="57543-130">選取 **資產** 匯  >  **入套件**  >  **自訂套件**</span><span class="sxs-lookup"><span data-stu-id="57543-130">Select **Assets** > **Import Package** > **Custom Package**</span></span>
- <span data-ttu-id="57543-131">開啟 **MixedReality 套件。**</span><span class="sxs-lookup"><span data-stu-id="57543-131">Open the **Microsoft.MixedReality.Toolkit.Foundation** package</span></span>
- <span data-ttu-id="57543-132">確定已選取 [ **服務/SceneSystem/SceneSystemResources** ] 和 [所有子選項]</span><span class="sxs-lookup"><span data-stu-id="57543-132">Ensure that **Services/SceneSystem/SceneSystemResources** and all child options are selected</span></span>

  ![重新匯入場景系統資源](../images/scene-system/ReimportSceneSystemResources.png)

- <span data-ttu-id="57543-134">選取匯 **入**</span><span class="sxs-lookup"><span data-stu-id="57543-134">Select **Import**</span></span>

## <a name="how-to-use-the-scene-system"></a><span data-ttu-id="57543-135">如何使用場景系統</span><span class="sxs-lookup"><span data-stu-id="57543-135">How to use the scene system</span></span>

- [<span data-ttu-id="57543-136">場景類型</span><span class="sxs-lookup"><span data-stu-id="57543-136">Scene Types</span></span>](scene-system-scene-types.md)
- [<span data-ttu-id="57543-137">內容場景載入</span><span class="sxs-lookup"><span data-stu-id="57543-137">Content Scene Loading</span></span>](scene-system-content-loading.md)
- [<span data-ttu-id="57543-138">監視內容載入</span><span class="sxs-lookup"><span data-stu-id="57543-138">Monitoring Content Loading</span></span>](scene-system-load-progress.md)
- [<span data-ttu-id="57543-139">照明場景載入</span><span class="sxs-lookup"><span data-stu-id="57543-139">Lighting Scene Loading</span></span>](scene-system-lighting-scenes.md)

## <a name="editor-settings"></a><span data-ttu-id="57543-140">編輯器設定</span><span class="sxs-lookup"><span data-stu-id="57543-140">Editor settings</span></span>

<span data-ttu-id="57543-141">根據預設，場景系統會在 Unity 編輯器中強制執行數個行為。</span><span class="sxs-lookup"><span data-stu-id="57543-141">By default, the Scene System enforces several behaviors in the Unity editor.</span></span> <span data-ttu-id="57543-142">如果您發現任何這些行為很繁重，可以在場景系統設定檔的 **編輯器設定** 區段中加以停用。</span><span class="sxs-lookup"><span data-stu-id="57543-142">If you find any of these behaviors heavy-handed, they can be disabled in the **Editor Settings** section of your Scene System profile.</span></span>

- <span data-ttu-id="57543-143">`Editor Manage Build Settings:` 若為 true，服務會自動更新您的組建設定，以確保所有管理員、光源和內容場景都會加入。</span><span class="sxs-lookup"><span data-stu-id="57543-143">`Editor Manage Build Settings:` If true, the service will update your build settings automatically, ensuring that all manager, lighting and content scenes are added.</span></span> <span data-ttu-id="57543-144">如果您想要完全掌控組建設定，請停用此值。</span><span class="sxs-lookup"><span data-stu-id="57543-144">Disable this if you want total control over build settings.</span></span>

- <span data-ttu-id="57543-145">`Editor Enforce Scene Order:` 若為 true，服務將確保管理員場景先顯示在場景階層中，後面接著光源和內容。</span><span class="sxs-lookup"><span data-stu-id="57543-145">`Editor Enforce Scene Order:` If true, the service will ensure that the manager scene is displayed first in scene hierarchy, followed by lighting and then content.</span></span> <span data-ttu-id="57543-146">如果您想要完全掌控場景階層，請停用此。</span><span class="sxs-lookup"><span data-stu-id="57543-146">Disable this if you want total control over scene hierarchy.</span></span>

- <span data-ttu-id="57543-147">`Editor Manage Loaded Scenes:` 若為 true，服務將確保一律會載入管理員、內容和光源場景。</span><span class="sxs-lookup"><span data-stu-id="57543-147">`Editor Manage Loaded Scenes:` If true, the service will ensure that the manager, content and lighting scenes are always loaded.</span></span> <span data-ttu-id="57543-148">如果您想要完全掌控編輯器中載入的場景，請停用。</span><span class="sxs-lookup"><span data-stu-id="57543-148">Disable if you want total control over which scenes are loaded in editor.</span></span>

- <span data-ttu-id="57543-149">`Editor Enforce Lighting Scene Types:` 若為 true，服務將確保光源只允許在中定義光源相關的元件 `PermittedLightingSceneComponentTypes` 。</span><span class="sxs-lookup"><span data-stu-id="57543-149">`Editor Enforce Lighting Scene Types:` If true, the service will ensure that only the lighting-related components defined in `PermittedLightingSceneComponentTypes` are allowed in lighting scenes.</span></span> <span data-ttu-id="57543-150">如果您想要完全掌控燈光場景的內容，請停用。</span><span class="sxs-lookup"><span data-stu-id="57543-150">Disable if you want total control over the content of lighting scenes.</span></span>

![場景系統編輯器設定](../images/scene-system/MRTK_SceneSystemProfileEditorSettings.PNG)
