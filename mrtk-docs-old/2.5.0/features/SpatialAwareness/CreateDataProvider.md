---
title: CreateSpatialAwarenessDataProvider
description: 描述如何在 MRTK 中建立自訂資料提供者
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: e5af47e710a61c2ea08c01cdfff8dae6970b352e
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/03/2021
ms.locfileid: "101779715"
---
# <a name="creating-a-spatial-awareness-system-data-provider"></a><span data-ttu-id="20c30-104">建立空間感知系統資料提供者</span><span class="sxs-lookup"><span data-stu-id="20c30-104">Creating a spatial awareness system data provider</span></span>

<span data-ttu-id="20c30-105">空間感知系統是可延伸的系統，可為應用程式提供真實世界環境的相關資料。</span><span class="sxs-lookup"><span data-stu-id="20c30-105">The Spatial Awareness system is an extensible system for providing applications with data about real world environments.</span></span> <span data-ttu-id="20c30-106">若要加入新硬體平臺或新形式空間感知資料的支援，可能需要自訂資料提供者。</span><span class="sxs-lookup"><span data-stu-id="20c30-106">To add support for a new hardware platform or a new form of Spatial Awareness data, a custom data provider may be required.</span></span>

<span data-ttu-id="20c30-107">本文說明如何建立空間感知系統的 [自訂資料提供者](../../architecture/SystemsExtensionsProviders.md)（也稱為空間觀察者）。</span><span class="sxs-lookup"><span data-stu-id="20c30-107">This article describes how to create [custom data providers](../../architecture/SystemsExtensionsProviders.md), also called Spatial Observers, for the Spatial Awareness system.</span></span> <span data-ttu-id="20c30-108">此處所示的範例程式碼是來自 [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) 類別執行，這 [對在編輯器中載入3d 網格資料很有用](SpatialObjectMeshObserver.md)。</span><span class="sxs-lookup"><span data-stu-id="20c30-108">The example code shown here is from the [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) class implementation which is [useful for loading 3D mesh data in-editor](SpatialObjectMeshObserver.md).</span></span>

> [!NOTE]
> <span data-ttu-id="20c30-109">此範例中使用的完整原始程式碼可以在資料夾中找到 `Assets/MRTK/Providers/ObjectMeshObserver` 。</span><span class="sxs-lookup"><span data-stu-id="20c30-109">The complete source code used in this example can be found in the `Assets/MRTK/Providers/ObjectMeshObserver` folder.</span></span>

## <a name="namespace-and-folder-structure"></a><span data-ttu-id="20c30-110">命名空間和資料夾結構</span><span class="sxs-lookup"><span data-stu-id="20c30-110">Namespace and folder structure</span></span>

<span data-ttu-id="20c30-111">資料提供者可透過下列其中一種方式散發：</span><span class="sxs-lookup"><span data-stu-id="20c30-111">Data providers can be distributed in one of two ways:</span></span>

1. <span data-ttu-id="20c30-112">協力廠商附加元件</span><span class="sxs-lookup"><span data-stu-id="20c30-112">Third party add-ons</span></span>
1. <span data-ttu-id="20c30-113">Microsoft Mixed Reality 工具組的一部分</span><span class="sxs-lookup"><span data-stu-id="20c30-113">Part of the Microsoft Mixed Reality Toolkit</span></span>

<span data-ttu-id="20c30-114">將新資料提供者提交給 MRTK 的核准程式將依案例而有所不同，並會在初始提案時傳達。</span><span class="sxs-lookup"><span data-stu-id="20c30-114">The approval process for submissions of new data providers to the MRTK will vary on a case-by-case basis and will be communicated at the time of the initial proposal.</span></span> <span data-ttu-id="20c30-115">您可以藉由建立新的 [*功能要求* 類型問題](https://github.com/microsoft/MixedRealityToolkit-Unity/issues)來提交提案。</span><span class="sxs-lookup"><span data-stu-id="20c30-115">Proposals can be submitted by creating a new [*Feature Request* type issue](https://github.com/microsoft/MixedRealityToolkit-Unity/issues).</span></span>

### <a name="third-party-add-on"></a><span data-ttu-id="20c30-116">協力廠商附加元件</span><span class="sxs-lookup"><span data-stu-id="20c30-116">Third party add-on</span></span>

<span data-ttu-id="20c30-117">**Namespace**</span><span class="sxs-lookup"><span data-stu-id="20c30-117">**Namespace**</span></span>

<span data-ttu-id="20c30-118">資料提供者必須具有命名空間，才能減少潛在的名稱衝突。</span><span class="sxs-lookup"><span data-stu-id="20c30-118">Data providers are required to have a namespace to mitigate potential name collisions.</span></span> <span data-ttu-id="20c30-119">建議命名空間包含下列元件。</span><span class="sxs-lookup"><span data-stu-id="20c30-119">It is recommended that the namespace includes the following components.</span></span>

- <span data-ttu-id="20c30-120">產生附加元件的公司名稱</span><span class="sxs-lookup"><span data-stu-id="20c30-120">Company name producing the add-on</span></span>
- <span data-ttu-id="20c30-121">功能區域</span><span class="sxs-lookup"><span data-stu-id="20c30-121">Feature area</span></span>

<span data-ttu-id="20c30-122">例如，Contoso 公司所建立和出貨的空間感知資料提供者可能是 *"MixedReality. SpatialAwareness"*。</span><span class="sxs-lookup"><span data-stu-id="20c30-122">For example, a Spatial Awareness data provider created and shipped by the Contoso company may be *"Contoso.MixedReality.Toolkit.SpatialAwareness"*.</span></span>

<span data-ttu-id="20c30-123">**資料夾結構**</span><span class="sxs-lookup"><span data-stu-id="20c30-123">**Folder structure**</span></span>

<span data-ttu-id="20c30-124">建議在資料夾階層中應資料提供者的原始程式碼，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="20c30-124">It is recommended that the source code for data providers be layed out in a folder hierarchy as shown in the following image.</span></span>

![範例資料夾結構](../Images/SpatialAwareness/ExampleProviderFolderStructure.png)

<span data-ttu-id="20c30-126">其中 *ContosoSpatialAwareness* 資料夾包含資料提供者的執行、 *編輯器* 資料夾包含偵測器 (以及任何其他 Unity 編輯器的特定程式碼) ，而 *設定檔* 資料夾包含一或多個預先製作的設定檔可編寫腳本的物件。</span><span class="sxs-lookup"><span data-stu-id="20c30-126">Where the *ContosoSpatialAwareness* folder contains the implementation of the data provider, the *Editor* folder contains the inspector (and any other Unity editor specific code), and the *Profiles* folder contains one or more pre-made profile scriptable objects.</span></span>

### <a name="mrtk-submission"></a><span data-ttu-id="20c30-127">MRTK 提交</span><span class="sxs-lookup"><span data-stu-id="20c30-127">MRTK submission</span></span>

<span data-ttu-id="20c30-128">**Namespace**</span><span class="sxs-lookup"><span data-stu-id="20c30-128">**Namespace**</span></span>

<span data-ttu-id="20c30-129">如果空間感知系統資料提供者提交至 [混合現實工具](https://github.com/Microsoft/MixedRealityToolkit-Unity)組存放庫，則命名空間 **必須** 以 (MixedReality 的開頭，例如： *MixedReality. SpatialObjectMeshObserver*) </span><span class="sxs-lookup"><span data-stu-id="20c30-129">If a spatial awareness system data provider is being submitted to the [Mixed Reality Toolkit repository](https://github.com/Microsoft/MixedRealityToolkit-Unity), the namespace **must** begin with Microsoft.MixedReality.Toolkit (ex: *Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver*)</span></span>

 <span data-ttu-id="20c30-130">程式碼應該位於 MRTK/Providers 底下的資料夾中， (例如： *MRTK/providers/ObjectMeshObserver*) 。</span><span class="sxs-lookup"><span data-stu-id="20c30-130">and the code should be located in a folder beneath MRTK/Providers (ex: *MRTK/Providers/ObjectMeshObserver*).</span></span>

<span data-ttu-id="20c30-131">**資料夾結構**</span><span class="sxs-lookup"><span data-stu-id="20c30-131">**Folder structure**</span></span>

<span data-ttu-id="20c30-132">所有程式碼都應該位於 MRTK/Provider 下的資料夾中， (例如： MRTK/Providers/ObjectMeshObserver) 。</span><span class="sxs-lookup"><span data-stu-id="20c30-132">All code should be located in a folder beneath MRTK/Providers (ex: MRTK/Providers/ObjectMeshObserver).</span></span>

## <a name="define-the-spatial-data-object"></a><span data-ttu-id="20c30-133">定義空間資料物件</span><span class="sxs-lookup"><span data-stu-id="20c30-133">Define the spatial data object</span></span>

<span data-ttu-id="20c30-134">建立空間感知資料提供者的第一個步驟，是決定資料的類型 (例如：網格或平面，) 它會提供給應用程式。</span><span class="sxs-lookup"><span data-stu-id="20c30-134">The first step in creating a Spatial Awareness data provider is determining the type of data (ex: meshes or planes) it will provide to applications.</span></span>

<span data-ttu-id="20c30-135">所有空間資料物件都必須執行 [`IMixedRealitySpatialAwarenessObject`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObject) 介面。</span><span class="sxs-lookup"><span data-stu-id="20c30-135">All spatial data objects must implement the [`IMixedRealitySpatialAwarenessObject`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObject) interface.</span></span>

<span data-ttu-id="20c30-136">Mixed Reality 工具組 foundation 提供下列空間物件，可在新的資料提供者中使用或擴充。</span><span class="sxs-lookup"><span data-stu-id="20c30-136">The Mixed Reality Toolkit foundation provides the following spatial objects that can be used or extended in new data providers.</span></span>

- [`BaseSpatialAwarenessObject`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialAwarenessObject)
- [`SpatialAwarenessMeshObject`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.SpatialAwarenessMeshObject)
- [`SpatialAwarenessPlanarObject`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.SpatialAwarenessPlanarObject)

## <a name="implement-the-data-provider"></a><span data-ttu-id="20c30-137">執行資料提供者</span><span class="sxs-lookup"><span data-stu-id="20c30-137">Implement the data provider</span></span>

### <a name="specify-interface-andor-base-class-inheritance"></a><span data-ttu-id="20c30-138">指定介面和/或基類繼承</span><span class="sxs-lookup"><span data-stu-id="20c30-138">Specify interface and/or base class inheritance</span></span>

<span data-ttu-id="20c30-139">所有空間感知資料提供者都必須執行 [`IMixedRealitySpatialAwarenessObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver) 介面，以指定空間感知系統所需的最小功能。</span><span class="sxs-lookup"><span data-stu-id="20c30-139">All Spatial Awareness data providers must implement the [`IMixedRealitySpatialAwarenessObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver) interface, which specifies the minimum functionality required by the Spatial Awareness system.</span></span> <span data-ttu-id="20c30-140">MRTK foundation 包含 [`BaseSpatialObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialObserver) 可提供此必要功能之預設執行的類別。</span><span class="sxs-lookup"><span data-stu-id="20c30-140">The MRTK foundation includes the [`BaseSpatialObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialObserver) class which provides a default implementation of this required functionality.</span></span>

```c#
public class SpatialObjectMeshObserver :
    BaseSpatialObserver,
    IMixedRealitySpatialAwarenessMeshObserver,
    IMixedRealityCapabilityCheck
{ }
```

> [!NOTE]
> <span data-ttu-id="20c30-141">[`IMixedRealityCapabilityCheck`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityCapabilityCheck)類別會使用介面 [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) 來表示它提供 SpatialAwarenessMesh 功能的支援。</span><span class="sxs-lookup"><span data-stu-id="20c30-141">The [`IMixedRealityCapabilityCheck`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityCapabilityCheck) interface is used by the [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) class to indicate that it provides support for the SpatialAwarenessMesh capability.</span></span>

#### <a name="apply-the-mixedrealitydataprovider-attribute"></a><span data-ttu-id="20c30-142">套用 MixedRealityDataProvider 屬性</span><span class="sxs-lookup"><span data-stu-id="20c30-142">Apply the MixedRealityDataProvider attribute</span></span>

<span data-ttu-id="20c30-143">建立空間感知資料提供者的關鍵步驟是將 [`MixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.MixedRealityDataProviderAttribute) 屬性套用至類別。</span><span class="sxs-lookup"><span data-stu-id="20c30-143">A key step in creating a Spatial Awareness data provider is to apply the [`MixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.MixedRealityDataProviderAttribute) attribute to the class.</span></span> <span data-ttu-id="20c30-144">此步驟可讓您為數據提供者設定預設設定檔和平臺 (s) ，並在空間感知設定檔中選取，以及名稱、資料夾路徑等。</span><span class="sxs-lookup"><span data-stu-id="20c30-144">This step enables setting the default profile and platform(s) for the data provider, when selected in the Spatial Awareness profile as well as Name, folder path, and more.</span></span>

```c#
[MixedRealityDataProvider(
    typeof(IMixedRealitySpatialAwarenessSystem),
    SupportedPlatforms.WindowsEditor | SupportedPlatforms.MacEditor | SupportedPlatforms.LinuxEditor,
    "Spatial Object Mesh Observer",
    "ObjectMeshObserver/Profiles/DefaultObjectMeshObserverProfile.asset",
    "MixedRealityToolkit.Providers")]
public class SpatialObjectMeshObserver :
    BaseSpatialObserver,
    IMixedRealitySpatialAwarenessMeshObserver,
    IMixedRealityCapabilityCheck
{ }
```

### <a name="implement-the-imixedrealitydataprovider-methods"></a><span data-ttu-id="20c30-145">執行 IMixedRealityDataProvider 方法</span><span class="sxs-lookup"><span data-stu-id="20c30-145">Implement the IMixedRealityDataProvider methods</span></span>

<span data-ttu-id="20c30-146">一旦定義了類別之後，下一個步驟就是提供介面的實作為 [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) 。</span><span class="sxs-lookup"><span data-stu-id="20c30-146">Once the class has been defined, the next step is to provide the implementation of the [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) interface.</span></span>

> [!NOTE]
> <span data-ttu-id="20c30-147">透過 [`BaseSpatialObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialObserver) 類別的類別 [`BaseService`](xref:Microsoft.MixedReality.Toolkit.BaseService) ，只會為方法提供空白的實作為 [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) 。</span><span class="sxs-lookup"><span data-stu-id="20c30-147">The [`BaseSpatialObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialObserver) class, via the [`BaseService`](xref:Microsoft.MixedReality.Toolkit.BaseService) class, provides only an empty implementations for [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) methods.</span></span> <span data-ttu-id="20c30-148">這些方法的詳細資料通常是資料提供者特有的。</span><span class="sxs-lookup"><span data-stu-id="20c30-148">The details of these methods are generally data provider specific.</span></span>

<span data-ttu-id="20c30-149">由資料提供者所執行的方法如下：</span><span class="sxs-lookup"><span data-stu-id="20c30-149">The methods that should be implemented by the data provider are:</span></span>

- `Destroy()`
- `Disable()`
- `Enable()`
- `Initialize()`
- `Reset()`
- `Update()`

### <a name="implement-the-data-provider-logic"></a><span data-ttu-id="20c30-150">執行資料提供者邏輯</span><span class="sxs-lookup"><span data-stu-id="20c30-150">Implement the data provider logic</span></span>

<span data-ttu-id="20c30-151">下一步是藉由執行特定的資料提供者介面，來新增資料提供者的邏輯 [`IMixedRealitySpatialAwarenessMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessMeshObserver) 。</span><span class="sxs-lookup"><span data-stu-id="20c30-151">The next step is to add the logic of the data provider by implementing the specific data provider interface, for example [`IMixedRealitySpatialAwarenessMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessMeshObserver).</span></span> <span data-ttu-id="20c30-152">這部分的資料提供者通常會是平臺特定。</span><span class="sxs-lookup"><span data-stu-id="20c30-152">This portion of the data provider will typically be platform specific.</span></span>

### <a name="observation-change-notifications"></a><span data-ttu-id="20c30-153">觀察變更通知</span><span class="sxs-lookup"><span data-stu-id="20c30-153">Observation change notifications</span></span>

<span data-ttu-id="20c30-154">為了讓應用程式能夠回應裝置對環境的瞭解變更，此資料提供者會依照介面中的定義來引發通知事件 [`IMixedRealitySpatialAwarenessObservationtHandler<T>`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObservationHandler`1) 。</span><span class="sxs-lookup"><span data-stu-id="20c30-154">To allow applications to respond to changes in the device's understanding of the environment, the data provider raises notification events as defined in the [`IMixedRealitySpatialAwarenessObservationtHandler<T>`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObservationHandler`1) interface.</span></span>

- `OnObservationAdded()`
- `OnObservationRemoved()`
- `OnObservationUpdated()`

 <span data-ttu-id="20c30-155">範例中的下列程式碼 [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) 會示範在新增網格資料時引發和事件。</span><span class="sxs-lookup"><span data-stu-id="20c30-155">The following code from the [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) examples demonstrates raising and event when mesh data is added.</span></span>

```c#
// The data to be sent when mesh observation events occur.
// This member variable is initialized as part of the Initialize() method.
private MixedRealitySpatialAwarenessEventData<SpatialAwarenessMeshObject> meshEventData = null;

/// <summary>
/// Sends the observations using the mesh data contained within the configured 3D model.
/// </summary>
private void SendMeshObjects()
{
    if (!sendObservations) { return; }

    if (spatialMeshObject != null)
    {
        MeshFilter[] meshFilters = spatialMeshObject.GetComponentsInChildren<MeshFilter>();
        for (int i = 0; i < meshFilters.Length; i++)
        {
            SpatialAwarenessMeshObject meshObject = SpatialAwarenessMeshObject.Create(
                meshFilters[i].sharedMesh,
                MeshPhysicsLayer,
                $"Spatial Object Mesh {currentMeshId}",
                currentMeshId,
                ObservedObjectParent);

            meshObject.GameObject.transform.localPosition = meshFilters[i].transform.position;
            meshObject.GameObject.transform.localRotation = meshFilters[i].transform.rotation;

            ApplyMeshMaterial(meshObject);

            meshes.Add(currentMeshId, meshObject);

            // Initialize the meshEventData variable with data for the added event.
            meshEventData.Initialize(this, currentMeshId, meshObject);
            // Raise the event via the spatial awareness system.
            SpatialAwarenessSystem?.HandleEvent(meshEventData, OnMeshAdded);

            currentMeshId++;
        }
    }

    sendObservations = false;
}
```

> [!NOTE]
> <span data-ttu-id="20c30-156">[`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) `OnObservationUpdated` 因為3d 模型只會載入一次，所以類別不會引發事件。</span><span class="sxs-lookup"><span data-stu-id="20c30-156">The [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) class does not raise `OnObservationUpdated` events since the 3D model is only loaded once.</span></span> <span data-ttu-id="20c30-157">類別中的實作為 [`WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver) `OnObservationUpdated` 針對觀察到的網格引發事件的範例。</span><span class="sxs-lookup"><span data-stu-id="20c30-157">The implementation in the [`WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver) class provides an example of raising an `OnObservationUpdated` event for an observed mesh.</span></span>

### <a name="add-unity-profiler-instrumentation"></a><span data-ttu-id="20c30-158">新增 Unity Profiler 檢測</span><span class="sxs-lookup"><span data-stu-id="20c30-158">Add Unity Profiler instrumentation</span></span>

<span data-ttu-id="20c30-159">效能在混合現實應用程式中是很重要的。</span><span class="sxs-lookup"><span data-stu-id="20c30-159">Performance is critical in mixed reality applications.</span></span> <span data-ttu-id="20c30-160">每個元件都會增加應用程式必須考慮的額外負荷。</span><span class="sxs-lookup"><span data-stu-id="20c30-160">Every component adds some amount of overhead for which applications must account.</span></span> <span data-ttu-id="20c30-161">至此，所有空間感知資料提供者都必須在內部迴圈中包含 Unity Profiler 檢測，以及經常使用的程式碼路徑。</span><span class="sxs-lookup"><span data-stu-id="20c30-161">To this end, it is important that all spatial awareness data providers contain Unity Profiler instrumentation in inner loop and frequently utilized code paths.</span></span>

<span data-ttu-id="20c30-162">建議您在檢測自訂提供者時，執行 MRTK 所使用的模式。</span><span class="sxs-lookup"><span data-stu-id="20c30-162">It is recommended to implement the pattern utilized by the MRTK when instrumenting custom providers.</span></span>

```c#
        private static readonly ProfilerMarker UpdateObserverPerfMarker = new ProfilerMarker("[MRTK] WindowsMixedRealitySpatialMeshObserver.UpdateObserver");

        /// <summary>
        /// Requests updates from the surface observer.
        /// </summary>
        private void UpdateObserver()
        {
            using (UpdateObserverPerfMarker.Auto())
            {
                // Code to be measured.
            }
        }
```

> [!Note]
> <span data-ttu-id="20c30-163">用來識別 profiler 標記的名稱是任意的。</span><span class="sxs-lookup"><span data-stu-id="20c30-163">The name used to identify the profiler marker is arbitrary.</span></span> <span data-ttu-id="20c30-164">MRTK 會使用下列模式。</span><span class="sxs-lookup"><span data-stu-id="20c30-164">The MRTK uses the following pattern.</span></span>
>
> <span data-ttu-id="20c30-165">"[product] className. 方法名稱-選擇性附注"</span><span class="sxs-lookup"><span data-stu-id="20c30-165">"[product] className.methodName - optional note"</span></span>
>
> <span data-ttu-id="20c30-166">建議自訂資料提供者遵循類似的模式，以協助簡化分析追蹤時特定元件和方法的識別。</span><span class="sxs-lookup"><span data-stu-id="20c30-166">It is recommended that custom data providers follow a similar pattern to help simplify identification of specific components and methods when analyzing traces.</span></span>

## <a name="create-the-profile-and-inspector"></a><span data-ttu-id="20c30-167">建立設定檔和偵測器</span><span class="sxs-lookup"><span data-stu-id="20c30-167">Create the profile and inspector</span></span>

<span data-ttu-id="20c30-168">在混合現實工具組中，資料提供者會使用 [設定檔](../Profiles/Profiles.md)進行設定。</span><span class="sxs-lookup"><span data-stu-id="20c30-168">In the Mixed Reality Toolkit, data providers are configured using [profiles](../Profiles/Profiles.md).</span></span>

### <a name="define-the-profile"></a><span data-ttu-id="20c30-169">定義設定檔</span><span class="sxs-lookup"><span data-stu-id="20c30-169">Define the profile</span></span>

<span data-ttu-id="20c30-170">設定檔內容應該鏡像資料提供者的可存取屬性 (例如：更新間隔) 。</span><span class="sxs-lookup"><span data-stu-id="20c30-170">Profile contents should mirror the accessible properties of the data provider (ex: update interval).</span></span> <span data-ttu-id="20c30-171">在每個介面中定義的所有使用者可設定屬性都應該包含在設定檔中。</span><span class="sxs-lookup"><span data-stu-id="20c30-171">All of the user configurable properties defined in each interface should be contained with the profile.</span></span>

<span data-ttu-id="20c30-172">如果新的資料提供者延伸了現有的提供者，則建議使用基類。</span><span class="sxs-lookup"><span data-stu-id="20c30-172">Base classes are encouraged if a new data provider extends an existing provider.</span></span> <span data-ttu-id="20c30-173">例如，會 [`SpatialObjectMeshObserverProfile`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserverProfile) 擴充， [`MixedRealitySpatialAwarenessMeshObserverProfile`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.MixedRealitySpatialAwarenessMeshObserverProfile) 讓客戶能夠提供要當做環境資料使用的3d 模型。</span><span class="sxs-lookup"><span data-stu-id="20c30-173">For example, the [`SpatialObjectMeshObserverProfile`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserverProfile) extends the [`MixedRealitySpatialAwarenessMeshObserverProfile`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.MixedRealitySpatialAwarenessMeshObserverProfile) to enable customers to provide a 3D model to be used as the environment data.</span></span>

```c#
[CreateAssetMenu(
    menuName = "Mixed Reality Toolkit/Profiles/Spatial Object Mesh Observer Profile",
    fileName = "SpatialObjectMeshObserverProfile",
    order = 100)]
public class SpatialObjectMeshObserverProfile : MixedRealitySpatialAwarenessMeshObserverProfile
{
    [SerializeField]
    [Tooltip("The model containing the desired mesh data.")]
    private GameObject spatialMeshObject = null;

    /// <summary>
    /// The model containing the desired mesh data.
    /// </summary>
    public GameObject SpatialMeshObject => spatialMeshObject;
}
```

<span data-ttu-id="20c30-174">`CreateAssetMenu`屬性可以套用至設定檔類別，讓客戶能夠使用 [**建立**  >  **資產**  >  **混合現實工具** 組  >  **設定檔**] 功能表建立設定檔實例。</span><span class="sxs-lookup"><span data-stu-id="20c30-174">The `CreateAssetMenu` attribute can be applied to the profile class to enable customers to create a profile instance using the **Create** > **Assets** > **Mixed Reality Toolkit** > **Profiles** menu.</span></span>

### <a name="implement-the-inspector"></a><span data-ttu-id="20c30-175">執行偵測器</span><span class="sxs-lookup"><span data-stu-id="20c30-175">Implement the inspector</span></span>

<span data-ttu-id="20c30-176">設定檔偵測器是用來設定和查看設定檔內容的使用者介面。</span><span class="sxs-lookup"><span data-stu-id="20c30-176">Profile inspectors are the user interface for configuring and viewing profile contents.</span></span> <span data-ttu-id="20c30-177">每個設定檔偵測器都應擴充 [`BaseMixedRealityToolkitConfigurationProfileInspector`](xref:Microsoft.MixedReality.Toolkit.Editor.BaseMixedRealityToolkitConfigurationProfileInspector) 類別。</span><span class="sxs-lookup"><span data-stu-id="20c30-177">Each profile inspector should extend the [`BaseMixedRealityToolkitConfigurationProfileInspector`](xref:Microsoft.MixedReality.Toolkit.Editor.BaseMixedRealityToolkitConfigurationProfileInspector) class.</span></span>

<span data-ttu-id="20c30-178">`CustomEditor`屬性會通知 Unity 套用偵測器的資產類型。</span><span class="sxs-lookup"><span data-stu-id="20c30-178">The `CustomEditor` attribute informs Unity the type of asset to which the inspector applies.</span></span>

```c#
[CustomEditor(typeof(SpatialObjectMeshObserverProfile))]
public class SpatialObjectMeshObserverProfileInspector : BaseMixedRealityToolkitConfigurationProfileInspector
{ }
```

## <a name="create-assembly-definitions"></a><span data-ttu-id="20c30-179">建立元件定義 (s) </span><span class="sxs-lookup"><span data-stu-id="20c30-179">Create assembly definition(s)</span></span>

<span data-ttu-id="20c30-180">混合現實工具組會使用元件定義 ([. asmdef](https://docs.unity3d.com/Manual/ScriptCompilationAssemblyDefinitionFiles.html)) 檔案來指定元件之間的相依性，以及協助 Unity 減少編譯時間。</span><span class="sxs-lookup"><span data-stu-id="20c30-180">The Mixed Reality Toolkit uses assembly definition ([.asmdef](https://docs.unity3d.com/Manual/ScriptCompilationAssemblyDefinitionFiles.html)) files to specify dependencies between components as well as to assist Unity in reducing compilation time.</span></span>

<span data-ttu-id="20c30-181">建議您為所有資料提供者及其編輯器元件建立元件定義檔。</span><span class="sxs-lookup"><span data-stu-id="20c30-181">It is recommended that assembly definition files are created for all data providers and their editor components.</span></span>

<span data-ttu-id="20c30-182">使用先前範例中的 [資料夾結構](#namespace-and-folder-structure) 時，ContosoSpatialAwareness 資料提供者會有兩個 asmdef 檔案。</span><span class="sxs-lookup"><span data-stu-id="20c30-182">Using the [folder structure](#namespace-and-folder-structure) in the earlier example, there would be two .asmdef files for the ContosoSpatialAwareness data provider.</span></span>

<span data-ttu-id="20c30-183">第一個元件定義適用于資料提供者。</span><span class="sxs-lookup"><span data-stu-id="20c30-183">The first assembly definition is for the data provider.</span></span> <span data-ttu-id="20c30-184">在此範例中，它會被稱為 ContosoSpatialAwareness，而且會位於範例的 *ContosoSpatialAwareness* 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="20c30-184">For this example, it will be called ContosoSpatialAwareness and will be located in the example's *ContosoSpatialAwareness* folder.</span></span> <span data-ttu-id="20c30-185">此元件定義必須指定 MixedReality 的相依性，以及它所相依的任何其他元件。</span><span class="sxs-lookup"><span data-stu-id="20c30-185">This assembly definition must specify a dependency on Microsoft.MixedReality.Toolkit and any other assemblies upon which it depends.</span></span>

<span data-ttu-id="20c30-186">ContosoInputEditor 元件定義會指定設定檔偵測器和任何編輯器特定的程式碼。</span><span class="sxs-lookup"><span data-stu-id="20c30-186">The ContosoInputEditor assembly definition will specify the profile inspector and any editor specific code.</span></span> <span data-ttu-id="20c30-187">這個檔案必須位於編輯器程式碼的根資料夾中。</span><span class="sxs-lookup"><span data-stu-id="20c30-187">This file must be located in the root folder of the editor code.</span></span> <span data-ttu-id="20c30-188">在此範例中，檔案會位於 *ContosoSpatialAwareness\Editor* 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="20c30-188">In this example, the file will be located in the *ContosoSpatialAwareness\Editor* folder.</span></span> <span data-ttu-id="20c30-189">此元件定義會包含 ContosoSpatialAwareness 元件的參考，以及：</span><span class="sxs-lookup"><span data-stu-id="20c30-189">This assembly definition will contain a reference to the ContosoSpatialAwareness assembly as well as:</span></span>

- <span data-ttu-id="20c30-190">MixedReality 工具組</span><span class="sxs-lookup"><span data-stu-id="20c30-190">Microsoft.MixedReality.Toolkit</span></span>
- <span data-ttu-id="20c30-191">MixedReality。檢查工具</span><span class="sxs-lookup"><span data-stu-id="20c30-191">Microsoft.MixedReality.Toolkit.Editor.Inspectors</span></span>
- <span data-ttu-id="20c30-192">MixedReality （工具組）</span><span class="sxs-lookup"><span data-stu-id="20c30-192">Microsoft.MixedReality.Toolkit.Editor.Utilities</span></span>

## <a name="register-the-data-provider"></a><span data-ttu-id="20c30-193">註冊資料提供者</span><span class="sxs-lookup"><span data-stu-id="20c30-193">Register the data provider</span></span>

<span data-ttu-id="20c30-194">一旦建立之後，就可以向空間感知系統註冊資料提供者，以便在應用程式中使用。</span><span class="sxs-lookup"><span data-stu-id="20c30-194">Once created, the data provider can be registered with the Spatial Awareness system to be used in the application.</span></span>

![選取空間物件網格觀察者](../Images/SpatialAwareness/SelectObjectObserver.png)

## <a name="packaging-and-distribution"></a><span data-ttu-id="20c30-196">封裝和散發</span><span class="sxs-lookup"><span data-stu-id="20c30-196">Packaging and distribution</span></span>

<span data-ttu-id="20c30-197">散發為協力廠商元件的資料提供者，會將封裝和散發的特定詳細資料提供給開發人員的喜好設定。</span><span class="sxs-lookup"><span data-stu-id="20c30-197">Data providers that are distributed as third party components have the specific details of packaging and distribution left to the preference of the developer.</span></span> <span data-ttu-id="20c30-198">最常見的解決方案可能是透過 Unity 資產存放區產生 unitypackage 和散發。</span><span class="sxs-lookup"><span data-stu-id="20c30-198">Likely, the most common solution will be to generate a .unitypackage and distribute via the Unity Asset Store.</span></span>

<span data-ttu-id="20c30-199">如果資料提供者已提交並接受成為 Microsoft Mixed Reality 工具組套件的一部分，Microsoft MRTK 團隊將會將其封裝並散發為 MRTK 供應專案的一部分。</span><span class="sxs-lookup"><span data-stu-id="20c30-199">If a data provider is submitted and accepted as a part of the Microsoft Mixed Reality Toolkit package, the Microsoft MRTK team will package and distribute it as part of the MRTK offerings.</span></span>

## <a name="see-also"></a><span data-ttu-id="20c30-200">另請參閱</span><span class="sxs-lookup"><span data-stu-id="20c30-200">See also</span></span>

- [<span data-ttu-id="20c30-201">空間感知系統</span><span class="sxs-lookup"><span data-stu-id="20c30-201">Spatial awareness system</span></span>](SpatialAwarenessGettingStarted.md)
- [<span data-ttu-id="20c30-202">`IMixedRealitySpatialAwarenessObject` 介面</span><span class="sxs-lookup"><span data-stu-id="20c30-202">`IMixedRealitySpatialAwarenessObject` interface</span></span>](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObject)
- [<span data-ttu-id="20c30-203">`BaseSpatialAwarenessObject` 類</span><span class="sxs-lookup"><span data-stu-id="20c30-203">`BaseSpatialAwarenessObject` class</span></span>](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialAwarenessObject)
- [<span data-ttu-id="20c30-204">`SpatialAwarenessMeshObject` 類</span><span class="sxs-lookup"><span data-stu-id="20c30-204">`SpatialAwarenessMeshObject` class</span></span>](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.SpatialAwarenessMeshObject)
- [<span data-ttu-id="20c30-205">`SpatialAwarenessPlanarObject` 類</span><span class="sxs-lookup"><span data-stu-id="20c30-205">`SpatialAwarenessPlanarObject` class</span></span>](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.SpatialAwarenessPlanarObject)
- [<span data-ttu-id="20c30-206">`IMixedRealitySpatialAwarenessObserver` 介面</span><span class="sxs-lookup"><span data-stu-id="20c30-206">`IMixedRealitySpatialAwarenessObserver` interface</span></span>](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver)
- [<span data-ttu-id="20c30-207">`BaseSpatialObserver` 類</span><span class="sxs-lookup"><span data-stu-id="20c30-207">`BaseSpatialObserver` class</span></span>](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialObserver)
- [<span data-ttu-id="20c30-208">`IMixedRealitySpatialAwarenessMeshObserver` 介面</span><span class="sxs-lookup"><span data-stu-id="20c30-208">`IMixedRealitySpatialAwarenessMeshObserver` interface</span></span>](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessMeshObserver)
- [<span data-ttu-id="20c30-209">`IMixedRealityDataProvider` 介面</span><span class="sxs-lookup"><span data-stu-id="20c30-209">`IMixedRealityDataProvider` interface</span></span>](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider)
- [<span data-ttu-id="20c30-210">`IMixedRealityCapabilityCheck` 介面</span><span class="sxs-lookup"><span data-stu-id="20c30-210">`IMixedRealityCapabilityCheck` interface</span></span>](xref:Microsoft.MixedReality.Toolkit.IMixedRealityCapabilityCheck)
