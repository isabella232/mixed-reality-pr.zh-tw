---
title: 空間物件網格觀察者
description: MRTK 中的空間網格觀察器檔
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: 51963fca4fa76340089b84e400f2882763977f72
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144452"
---
# <a name="configuring-mesh-observers-for-the-editor"></a><span data-ttu-id="06ca9-104">設定編輯器的網格觀察器</span><span class="sxs-lookup"><span data-stu-id="06ca9-104">Configuring mesh observers for the editor</span></span>

<span data-ttu-id="06ca9-105">在 Unity 編輯器中提供環境網格資料的便利方式是使用 [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) 類別。</span><span class="sxs-lookup"><span data-stu-id="06ca9-105">A convenient way to provide environment mesh data in the Unity editor is to use the [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) class.</span></span> <span data-ttu-id="06ca9-106">*空間物件網格觀察* 者是一種僅限編輯器的資料提供者，適用于 [空間感知系統](spatial-awareness-getting-started.md)，可讓您匯入3d 模型資料來代表空間網格。</span><span class="sxs-lookup"><span data-stu-id="06ca9-106">The *Spatial Object Mesh Observer* is an editor-only data provider for the [Spatial Awareness system](spatial-awareness-getting-started.md) that enables importing 3D model data to represent a spatial mesh.</span></span> <span data-ttu-id="06ca9-107">*空間物件網格觀察* 者的其中一種常見用法是匯入透過 Microsoft HoloLens 掃描的資料，以測試如何從 Unity 內調整不同環境的體驗。</span><span class="sxs-lookup"><span data-stu-id="06ca9-107">One common use of the *Spatial Object Mesh Observer* is to import data scanned via a Microsoft HoloLens to test how an experience adapts to different environments from within Unity.</span></span>

## <a name="getting-started"></a><span data-ttu-id="06ca9-108">開始使用</span><span class="sxs-lookup"><span data-stu-id="06ca9-108">Getting started</span></span>

<span data-ttu-id="06ca9-109">本指南將逐步解說如何設定 *空間物件網格觀察* 者。</span><span class="sxs-lookup"><span data-stu-id="06ca9-109">This guide will walk through setting up a *Spatial Object Mesh Observer*.</span></span> <span data-ttu-id="06ca9-110">啟用這項功能有三個主要步驟。</span><span class="sxs-lookup"><span data-stu-id="06ca9-110">There are three key steps to enable this feature.</span></span>

1. <span data-ttu-id="06ca9-111">將 *空間物件網格觀察* 器新增至空間感知系統設定檔</span><span class="sxs-lookup"><span data-stu-id="06ca9-111">Add a *Spatial Object Mesh Observer* to the Spatial Awareness system profile</span></span>
1. <span data-ttu-id="06ca9-112">設定環境網格資料物件</span><span class="sxs-lookup"><span data-stu-id="06ca9-112">Set the Environment Mesh Data object</span></span>
1. [<span data-ttu-id="06ca9-113">設定其他網格觀察者配置檔案屬性</span><span class="sxs-lookup"><span data-stu-id="06ca9-113">Configure rest of the Mesh Observer profile properties</span></span>](configuring-spatial-awareness-mesh-observer.md)

### <a name="set-up-a-spatial-object-mesh-observer-profile"></a><span data-ttu-id="06ca9-114">設定 *空間物件網格觀察* 者設定檔</span><span class="sxs-lookup"><span data-stu-id="06ca9-114">Set up a *spatial object mesh observer* profile</span></span>

1. <span data-ttu-id="06ca9-115">選取所需的 *混合現實工具* 組設定設定檔，或選取場景中的 *混合現實工具* 組物件</span><span class="sxs-lookup"><span data-stu-id="06ca9-115">Select the desired *Mixed Reality Toolkit* configuration profile or select the *Mixed Reality Toolkit* object in scene</span></span>
1. <span data-ttu-id="06ca9-116">開啟或展開 [ *空間感知系統* ] 索引標籤</span><span class="sxs-lookup"><span data-stu-id="06ca9-116">Open or expand the *Spatial Awareness System* tab</span></span>
1. <span data-ttu-id="06ca9-117">按一下 *[新增空間觀察者]* 按鈕</span><span class="sxs-lookup"><span data-stu-id="06ca9-117">Click on *"Add Spatial Observer"* button</span></span>

    ![新增空間觀察者](../images/spatial-awareness/AddObserver.png)

1. <span data-ttu-id="06ca9-119">選取 *SpatialObjectMeshObserver* 類型</span><span class="sxs-lookup"><span data-stu-id="06ca9-119">Select the *SpatialObjectMeshObserver* type</span></span>

    ![選取空間物件網格觀察者](../images/spatial-awareness/SelectObjectObserver.png)

1. <span data-ttu-id="06ca9-121">選取所需的 *空間網格物件*。</span><span class="sxs-lookup"><span data-stu-id="06ca9-121">Select the desired *Spatial Mesh Object*.</span></span> <span data-ttu-id="06ca9-122">根據預設，系統會使用範例模型來設定觀察者。</span><span class="sxs-lookup"><span data-stu-id="06ca9-122">By default, the observer is configured with an example model.</span></span> <span data-ttu-id="06ca9-123">此模型是使用 Microsoft HoloLens 建立的，但您可以 [建立新的掃描網格物件](#acquiring-environment-scans)。</span><span class="sxs-lookup"><span data-stu-id="06ca9-123">This model was created using a Microsoft HoloLens but it is possible to [create a new scan mesh object](#acquiring-environment-scans).</span></span>
1. [<span data-ttu-id="06ca9-124">設定其他網格觀察者配置檔案屬性</span><span class="sxs-lookup"><span data-stu-id="06ca9-124">Configure rest of the Mesh Observer profile properties</span></span>](configuring-spatial-awareness-mesh-observer.md)

    ![選取網格物件](../images/spatial-awareness/ObjectObserverProfile.png)

### <a name="spatial-object-mesh-observer-profile-notes"></a><span data-ttu-id="06ca9-126">空間物件網格觀察器設定檔注意事項</span><span class="sxs-lookup"><span data-stu-id="06ca9-126">Spatial object mesh observer profile notes</span></span>

<span data-ttu-id="06ca9-127">由於 *空間物件網格觀察* 器會從3d 模型載入資料，因此它不會接受以下所述的一些標準網格觀察者設定。</span><span class="sxs-lookup"><span data-stu-id="06ca9-127">Since the *Spatial Object Mesh Observer* loads data from a 3D model, it does not honor some of the standard mesh observer settings which are outlined below.</span></span>

<span data-ttu-id="06ca9-128">**更新間隔**</span><span class="sxs-lookup"><span data-stu-id="06ca9-128">**Update Interval**</span></span>

<span data-ttu-id="06ca9-129">當載入模型時，  *空間物件網格觀察* 者會將所有網格傳送至應用程式。</span><span class="sxs-lookup"><span data-stu-id="06ca9-129">The  *Spatial Object Mesh Observer* sends all meshes to an application when the model is loaded.</span></span> <span data-ttu-id="06ca9-130">它不會模擬更新之間的時間差異。</span><span class="sxs-lookup"><span data-stu-id="06ca9-130">It does not simulate time deltas between updates.</span></span> <span data-ttu-id="06ca9-131">應用程式可以藉由呼叫和來重新接收網格 [`myObserver.ClearObservation()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver.ClearObservations) 事件 [`myObserver.Resume()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver.Resume) 。</span><span class="sxs-lookup"><span data-stu-id="06ca9-131">An application can re-receive the mesh events by calling [`myObserver.ClearObservation()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver.ClearObservations) and [`myObserver.Resume()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver.Resume).</span></span>

<span data-ttu-id="06ca9-132">**為固定觀察者**</span><span class="sxs-lookup"><span data-stu-id="06ca9-132">**Is Stationary Observer**</span></span>

<span data-ttu-id="06ca9-133">*空間物件網格觀察* 者會將所有3d 網格物件視為固定和忽略來源。</span><span class="sxs-lookup"><span data-stu-id="06ca9-133">The *Spatial Object Mesh Observer* considers all 3D mesh objects to be stationary and disregards origin.</span></span>

<span data-ttu-id="06ca9-134">**觀察者圖形和範圍**</span><span class="sxs-lookup"><span data-stu-id="06ca9-134">**Observer Shape and Extents**</span></span>

<span data-ttu-id="06ca9-135">*空間物件網格觀察* 者會將整個3d 網格傳送至應用程式。</span><span class="sxs-lookup"><span data-stu-id="06ca9-135">The  *Spatial Object Mesh Observer* sends the entire 3D mesh to the application.</span></span> <span data-ttu-id="06ca9-136">不考慮觀察者圖形與範圍。</span><span class="sxs-lookup"><span data-stu-id="06ca9-136">Observer shape and extents are not considered.</span></span>

<span data-ttu-id="06ca9-137">**詳細資料層級與三角形/三立方計量表**</span><span class="sxs-lookup"><span data-stu-id="06ca9-137">**Level of Detail and Triangles / Cubic Meter**</span></span>

<span data-ttu-id="06ca9-138">將網格傳送至應用程式時，觀察者不會嘗試尋找3D 模型 LODs。</span><span class="sxs-lookup"><span data-stu-id="06ca9-138">The Observer does not attempt to find 3D model LODs when sending the meshes to the application.</span></span>

## <a name="acquiring-environment-scans"></a><span data-ttu-id="06ca9-139">取得環境掃描</span><span class="sxs-lookup"><span data-stu-id="06ca9-139">Acquiring environment scans</span></span>

<span data-ttu-id="06ca9-140">本節將概述用來建立和收集 *空間網格物件* 檔案，以與 *空間物件網格觀察* 者搭配使用的其他資訊。</span><span class="sxs-lookup"><span data-stu-id="06ca9-140">This section outlines additional information to create and gather *Spatial Mesh Object* files for use with the *Spatial Object Mesh Observer*.</span></span>

### <a name="windows-device-portal"></a><span data-ttu-id="06ca9-141">Windows 裝置入口網站</span><span class="sxs-lookup"><span data-stu-id="06ca9-141">Windows Device Portal</span></span>

<span data-ttu-id="06ca9-142">[Windows 裝置入口網站](/windows/mixed-reality/using-the-windows-device-portal)可以用來從 Microsoft HoloLens 裝置將空間網格下載為 .obj 檔。</span><span class="sxs-lookup"><span data-stu-id="06ca9-142">The [Windows Device Portal](/windows/mixed-reality/using-the-windows-device-portal) can be used to download the spatial mesh, as a .obj file, from a Microsoft HoloLens device.</span></span>

1. <span data-ttu-id="06ca9-143">藉由使用 HoloLens 來掃描及觀看所需的環境，進行掃描</span><span class="sxs-lookup"><span data-stu-id="06ca9-143">Scan by simply walking and viewing the desired environment with a HoloLens</span></span>
1. <span data-ttu-id="06ca9-144">使用 Windows 裝置入口網站連接到 HoloLens</span><span class="sxs-lookup"><span data-stu-id="06ca9-144">Connect to the HoloLens using the Windows Device Portal</span></span>
1. <span data-ttu-id="06ca9-145">流覽至 *3D 視圖* 頁面</span><span class="sxs-lookup"><span data-stu-id="06ca9-145">Navigate to the *3D View* page</span></span>
1. <span data-ttu-id="06ca9-146">按一下 [*空間對應*] 區段底下的 [*更新*] 按鈕</span><span class="sxs-lookup"><span data-stu-id="06ca9-146">Click the *Update* button under *Spatial Mapping* section</span></span>
1. <span data-ttu-id="06ca9-147">按一下 [*空間對應*] 區段下的 [*儲存*] 按鈕，將 OBJ 檔案儲存至 PC</span><span class="sxs-lookup"><span data-stu-id="06ca9-147">Click the *Save* button under *Spatial Mapping* section to save the obj file to PC</span></span>

> [!NOTE]
> <span data-ttu-id="06ca9-148">**HoloToolkit 聊天室檔案**</span><span class="sxs-lookup"><span data-stu-id="06ca9-148">**HoloToolkit .room files**</span></span>
>
> <span data-ttu-id="06ca9-149">許多開發人員先前都會使用 HoloToolkit 來掃描環境，並建立聊天室檔案。</span><span class="sxs-lookup"><span data-stu-id="06ca9-149">Many developers will have previously used HoloToolkit to scan environments and create .room files.</span></span> <span data-ttu-id="06ca9-150">混合現實工具組現在支援將這些檔案匯入為 Unity 中的 Gameobject，並在觀察者中使用它們做為 *空間網格物件* 。</span><span class="sxs-lookup"><span data-stu-id="06ca9-150">The Mixed Reality Toolkit now supports importing these files as GameObjects in Unity and use them as *Spatial Mesh Objects* in the observer.</span></span>

## <a name="see-also"></a><span data-ttu-id="06ca9-151">另請參閱</span><span class="sxs-lookup"><span data-stu-id="06ca9-151">See also</span></span>

- [<span data-ttu-id="06ca9-152">設定檔</span><span class="sxs-lookup"><span data-stu-id="06ca9-152">Profiles</span></span>](../profiles/profiles.md)
- [<span data-ttu-id="06ca9-153">混合現實工具組設定檔設定指南</span><span class="sxs-lookup"><span data-stu-id="06ca9-153">Mixed Reality Toolkit Profile configuration guide</span></span>](../../configuration/mixed-reality-configuration-guide.md)
- [<span data-ttu-id="06ca9-154">空間感知入門</span><span class="sxs-lookup"><span data-stu-id="06ca9-154">Spatial Awareness Getting started</span></span>](spatial-awareness-getting-started.md)
- [<span data-ttu-id="06ca9-155">設定裝置上的網狀觀察器</span><span class="sxs-lookup"><span data-stu-id="06ca9-155">Configuring Mesh Observers on Device</span></span>](configuring-spatial-awareness-mesh-observer.md)
- [<span data-ttu-id="06ca9-156">透過程式碼設定網格觀察者</span><span class="sxs-lookup"><span data-stu-id="06ca9-156">Configuring Mesh Observers via code</span></span>](usage-guide.md)
- [<span data-ttu-id="06ca9-157">使用 Windows 裝置入口網站</span><span class="sxs-lookup"><span data-stu-id="06ca9-157">Using the Windows Device Portal</span></span>](/windows/mixed-reality/using-the-windows-device-portal)