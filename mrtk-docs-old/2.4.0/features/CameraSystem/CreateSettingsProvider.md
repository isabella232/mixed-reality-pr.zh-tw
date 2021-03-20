---
title: CreateSettingProvider
description: MRTK 中相機設定的資料提供者
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
ms.localizationpriority: medium
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: f28c411c80955e9a2c7e2cd4074ee534b302cfee
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104688228"
---
# <a name="creating-a-camera-settings-provider"></a><span data-ttu-id="9c3b1-104">建立相機設定提供者</span><span class="sxs-lookup"><span data-stu-id="9c3b1-104">Creating a camera settings provider</span></span>

<span data-ttu-id="9c3b1-105">攝影機系統是可延伸的系統，可提供平臺特定相機設定的支援。</span><span class="sxs-lookup"><span data-stu-id="9c3b1-105">The Camera system is an extensible system for providing support for platform specific camera configurations.</span></span> <span data-ttu-id="9c3b1-106">若要新增新攝影機設定的支援，可能需要自訂設定提供者。</span><span class="sxs-lookup"><span data-stu-id="9c3b1-106">To add support for a new camera configuration, a custom settings provider may be required.</span></span>

> [!NOTE]
> <span data-ttu-id="9c3b1-107">此範例中使用的完整原始程式碼可以在 **MRTK/Providers/UnityAR** 資料夾中找到。</span><span class="sxs-lookup"><span data-stu-id="9c3b1-107">The complete source code used in this example can be found in the **MRTK/Providers/UnityAR** folder.</span></span>

## <a name="namespace-and-folder-structure"></a><span data-ttu-id="9c3b1-108">命名空間和資料夾結構</span><span class="sxs-lookup"><span data-stu-id="9c3b1-108">Namespace and folder structure</span></span>

<span data-ttu-id="9c3b1-109">資料提供者可透過下列其中一種方式散發：</span><span class="sxs-lookup"><span data-stu-id="9c3b1-109">Data providers can be distributed in one of two ways:</span></span>

1. <span data-ttu-id="9c3b1-110">協力廠商附加元件</span><span class="sxs-lookup"><span data-stu-id="9c3b1-110">Third party add-ons</span></span>
1. <span data-ttu-id="9c3b1-111">Microsoft Mixed Reality 工具組的一部分</span><span class="sxs-lookup"><span data-stu-id="9c3b1-111">Part of the Microsoft Mixed Reality Toolkit</span></span>

<span data-ttu-id="9c3b1-112">將新資料提供者提交給 MRTK 的核准程式將依案例而有所不同，並會在初始提案時傳達。</span><span class="sxs-lookup"><span data-stu-id="9c3b1-112">The approval process for submissions of new data providers to the MRTK will vary on a case-by-case basis and will be communicated at the time of the initial proposal.</span></span> <span data-ttu-id="9c3b1-113">您可以藉由建立新的 [*功能要求* 類型問題](https://github.com/microsoft/MixedRealityToolkit-Unity/issues)來提交提案。</span><span class="sxs-lookup"><span data-stu-id="9c3b1-113">Proposals can be submitted by creating a new [*Feature Request* type issue](https://github.com/microsoft/MixedRealityToolkit-Unity/issues).</span></span>

### <a name="third-party-add-ons"></a><span data-ttu-id="9c3b1-114">協力廠商附加元件</span><span class="sxs-lookup"><span data-stu-id="9c3b1-114">Third party add-ons</span></span>

<span data-ttu-id="9c3b1-115">**Namespace**</span><span class="sxs-lookup"><span data-stu-id="9c3b1-115">**Namespace**</span></span>

<span data-ttu-id="9c3b1-116">資料提供者必須具有命名空間，才能減少潛在的名稱衝突。</span><span class="sxs-lookup"><span data-stu-id="9c3b1-116">Data providers are required to have a namespace to mitigate potential name collisions.</span></span> <span data-ttu-id="9c3b1-117">建議命名空間包含下列元件。</span><span class="sxs-lookup"><span data-stu-id="9c3b1-117">It is recommended that the namespace includes the following components.</span></span>

- <span data-ttu-id="9c3b1-118">產生附加元件的公司名稱</span><span class="sxs-lookup"><span data-stu-id="9c3b1-118">Company name producing the add-on</span></span>
- <span data-ttu-id="9c3b1-119">功能區域</span><span class="sxs-lookup"><span data-stu-id="9c3b1-119">Feature area</span></span>

<span data-ttu-id="9c3b1-120">例如，Contoso 公司所建立和出貨的攝影機設定提供者可能是 *"MixedReality"*。</span><span class="sxs-lookup"><span data-stu-id="9c3b1-120">For example, a camera settings provider created and shipped by the Contoso company may be *"Contoso.MixedReality.Toolkit.Camera"*.</span></span>

<span data-ttu-id="9c3b1-121">**資料夾結構**</span><span class="sxs-lookup"><span data-stu-id="9c3b1-121">**Folder structure**</span></span>

<span data-ttu-id="9c3b1-122">建議在資料夾階層中應資料提供者的原始程式碼，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="9c3b1-122">It is recommended that the source code for data providers be layed out in a folder hierarchy as shown in the following image.</span></span>

![範例資料夾結構](../Images/CameraSystem/ExampleProviderFolderStructure.png)

<span data-ttu-id="9c3b1-124">其中 *ContosoCamera* 資料夾包含資料提供者的執行、 *編輯器* 資料夾包含偵測器 (以及任何其他 Unity 編輯器的特定程式碼) ，而 *設定檔* 資料夾包含一或多個預先製作的設定檔可編寫腳本的物件。</span><span class="sxs-lookup"><span data-stu-id="9c3b1-124">Where the *ContosoCamera* folder contains the implementation of the data provider, the *Editor* folder contains the inspector (and any other Unity editor specific code), and the *Profiles* folder contains one or more pre-made profile scriptable objects.</span></span>

### <a name="mrtk-submission"></a><span data-ttu-id="9c3b1-125">MRTK 提交</span><span class="sxs-lookup"><span data-stu-id="9c3b1-125">MRTK submission</span></span>

<span data-ttu-id="9c3b1-126">**Namespace**</span><span class="sxs-lookup"><span data-stu-id="9c3b1-126">**Namespace**</span></span>

<span data-ttu-id="9c3b1-127">如果將相機設定提供者提交至 [混合現實工具](https://github.com/Microsoft/MixedRealityToolkit-Unity)組存放庫，則命名空間 **必須** 以 (MixedReality 的開頭，例如： *MixedReality. CameraSystem*) 。</span><span class="sxs-lookup"><span data-stu-id="9c3b1-127">If a camera settings provider is being submitted to the [Mixed Reality Toolkit repository](https://github.com/Microsoft/MixedRealityToolkit-Unity), the namespace **must** begin with Microsoft.MixedReality.Toolkit (ex: *Microsoft.MixedReality.Toolkit.CameraSystem*).</span></span>

<span data-ttu-id="9c3b1-128">**資料夾結構**</span><span class="sxs-lookup"><span data-stu-id="9c3b1-128">**Folder structure**</span></span>

<span data-ttu-id="9c3b1-129">所有程式碼都必須位於 MRTK/Provider 下的資料夾中， (例如： MRTK/Providers/UnityAR) 。</span><span class="sxs-lookup"><span data-stu-id="9c3b1-129">All code must be located in a folder beneath MRTK/Providers (ex: MRTK/Providers/UnityAR).</span></span>

## <a name="define-the-camera-settings-object"></a><span data-ttu-id="9c3b1-130">定義相機設定物件</span><span class="sxs-lookup"><span data-stu-id="9c3b1-130">Define the camera settings object</span></span>

<span data-ttu-id="9c3b1-131">建立攝影機設定提供者的第一個步驟，是決定資料類型 (例如：網格或平面，) 它會提供給應用程式。</span><span class="sxs-lookup"><span data-stu-id="9c3b1-131">The first step in creating a camera settings provider is determining the type of data (ex: meshes or planes) it will provide to applications.</span></span>

<span data-ttu-id="9c3b1-132">所有空間資料物件都必須執行 [`IMixedRealityCameraSettingsProvider`](xref:Microsoft.MixedReality.Toolkit.CameraSystem.IMixedRealityCameraSettingsProvider) 介面。</span><span class="sxs-lookup"><span data-stu-id="9c3b1-132">All spatial data objects must implement the [`IMixedRealityCameraSettingsProvider`](xref:Microsoft.MixedReality.Toolkit.CameraSystem.IMixedRealityCameraSettingsProvider) interface.</span></span>

## <a name="implement-the-settings-provider"></a><span data-ttu-id="9c3b1-133">執行設定提供者</span><span class="sxs-lookup"><span data-stu-id="9c3b1-133">Implement the settings provider</span></span>

### <a name="specify-interface-andor-base-class-inheritance"></a><span data-ttu-id="9c3b1-134">指定介面和/或基類繼承</span><span class="sxs-lookup"><span data-stu-id="9c3b1-134">Specify interface and/or base class inheritance</span></span>

<span data-ttu-id="9c3b1-135">所有相機設定提供者都必須執行 [`IMixedRealityCameraSettingsProvider`](xref:Microsoft.MixedReality.Toolkit.CameraSystem.IMixedRealityCameraSettingsProvider) 介面，以指定相機系統所需的最小功能。</span><span class="sxs-lookup"><span data-stu-id="9c3b1-135">All camera settings providers must implement the [`IMixedRealityCameraSettingsProvider`](xref:Microsoft.MixedReality.Toolkit.CameraSystem.IMixedRealityCameraSettingsProvider) interface, which specifies the minimum functionality required by the camera system.</span></span> <span data-ttu-id="9c3b1-136">MRTK foundation 包含 [`BaseCameraSettingsProvider`](xref:Microsoft.MixedReality.Toolkit.CameraSystem.BaseCameraSettingsProvider) 可提供所需功能預設執行的類別。</span><span class="sxs-lookup"><span data-stu-id="9c3b1-136">The MRTK foundation includes the [`BaseCameraSettingsProvider`](xref:Microsoft.MixedReality.Toolkit.CameraSystem.BaseCameraSettingsProvider) class which provides a default implementation of the required functionality.</span></span>

```c#
namespace namespace Microsoft.MixedReality.Toolkit.Experimental.UnityAR
{
    public class UnityARCameraSettings : BaseCameraSettingsProvider
    { }
}
```

#### <a name="apply-the-mixedrealitydataprovider-attribute"></a><span data-ttu-id="9c3b1-137">套用 MixedRealityDataProvider 屬性</span><span class="sxs-lookup"><span data-stu-id="9c3b1-137">Apply the MixedRealityDataProvider attribute</span></span>

<span data-ttu-id="9c3b1-138">建立攝影機設定提供者的關鍵步驟是將 [`MixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.MixedRealityDataProviderAttribute) 屬性套用至類別。</span><span class="sxs-lookup"><span data-stu-id="9c3b1-138">A key step in creating a camera settings provider is to apply the [`MixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.MixedRealityDataProviderAttribute) attribute to the class.</span></span> <span data-ttu-id="9c3b1-139">此步驟可讓您為數據提供者設定預設設定檔和平臺 (s) （在相機系統設定檔中選取），以及名稱、資料夾路徑等。</span><span class="sxs-lookup"><span data-stu-id="9c3b1-139">This step enables setting the default profile and platform(s) for the data provider, when selected in the Camera System profile as well as name, folder path, and more.</span></span>

```c#
    [MixedRealityDataProvider(
        typeof(IMixedRealityCameraSystem),
        SupportedPlatforms.Android | SupportedPlatforms.IOS,
        "Unity AR Foundation Camera Settings",
        "UnityAR/Profiles/DefaultUnityARCameraSettingsProfile.asset",
        "MixedRealityToolkit.Providers")]
    public class UnityARCameraSettings : BaseCameraSettingsProvider
    { }
```

### <a name="implement-the-imixedrealitydataprovider-methods"></a><span data-ttu-id="9c3b1-140">執行 IMixedRealityDataProvider 方法</span><span class="sxs-lookup"><span data-stu-id="9c3b1-140">Implement the IMixedRealityDataProvider methods</span></span>

<span data-ttu-id="9c3b1-141">一旦定義了類別之後，下一個步驟就是提供介面的實作為 [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) 。</span><span class="sxs-lookup"><span data-stu-id="9c3b1-141">Once the class has been defined, the next step is to provide the implementation of the [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) interface.</span></span>

> [!NOTE]
> <span data-ttu-id="9c3b1-142">[`BaseDataProvider`](xref:Microsoft.MixedReality.Toolkit.BaseDataProvider`1)類別 [`BaseService`](xref:Microsoft.MixedReality.Toolkit.BaseService) 可透過類別提供空白的方法實作為 [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) 。</span><span class="sxs-lookup"><span data-stu-id="9c3b1-142">The [`BaseDataProvider`](xref:Microsoft.MixedReality.Toolkit.BaseDataProvider`1) class, via the [`BaseService`](xref:Microsoft.MixedReality.Toolkit.BaseService) class, provides empty implementations for [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) methods.</span></span> <span data-ttu-id="9c3b1-143">這些方法的詳細資料通常是資料提供者特有的。</span><span class="sxs-lookup"><span data-stu-id="9c3b1-143">The details of these methods are generally data provider specific.</span></span>

<span data-ttu-id="9c3b1-144">由資料提供者所執行的方法如下：</span><span class="sxs-lookup"><span data-stu-id="9c3b1-144">The methods that should be implemented by the data provider are:</span></span>

- `Destroy()`
- `Disable()`
- `Enable()`
- `Initialize()`
- `Reset()`
- `Update()`

> [!NOTE]
> <span data-ttu-id="9c3b1-145">並非所有的設定提供者都需要所有這些方法的執行。</span><span class="sxs-lookup"><span data-stu-id="9c3b1-145">Not all settings providers will require implementations for all of these methods.</span></span> <span data-ttu-id="9c3b1-146">強烈建議您 `Destroy()` `Initialize()` 至少執行這項工作。</span><span class="sxs-lookup"><span data-stu-id="9c3b1-146">It is highly recommended that `Destroy()` and `Initialize()` be implemented at a minimum.</span></span>

### <a name="implement-the-data-provider-logic"></a><span data-ttu-id="9c3b1-147">執行資料提供者邏輯</span><span class="sxs-lookup"><span data-stu-id="9c3b1-147">Implement the data provider logic</span></span>

<span data-ttu-id="9c3b1-148">下一步是藉由執行來新增設定提供者的邏輯 [`IMixedRealityCameraSettingsProvider`](xref:Microsoft.MixedReality.Toolkit.CameraSystem.IMixedRealityCameraSettingsProvider) 。</span><span class="sxs-lookup"><span data-stu-id="9c3b1-148">The next step is to add the logic of the settings provider by implementing [`IMixedRealityCameraSettingsProvider`](xref:Microsoft.MixedReality.Toolkit.CameraSystem.IMixedRealityCameraSettingsProvider).</span></span> <span data-ttu-id="9c3b1-149">這部分的資料提供者通常會是相機設定專屬的。</span><span class="sxs-lookup"><span data-stu-id="9c3b1-149">This portion of the data provider will typically be camera configuration specific.</span></span>

## <a name="create-the-profile-and-inspector"></a><span data-ttu-id="9c3b1-150">建立設定檔和偵測器</span><span class="sxs-lookup"><span data-stu-id="9c3b1-150">Create the profile and inspector</span></span>

<span data-ttu-id="9c3b1-151">在混合現實工具組中，資料提供者會使用 [設定檔](../Profiles/Profiles.md)進行設定。</span><span class="sxs-lookup"><span data-stu-id="9c3b1-151">In the Mixed Reality Toolkit, data providers are configured using [profiles](../Profiles/Profiles.md).</span></span>

### <a name="define-the-profile"></a><span data-ttu-id="9c3b1-152">定義設定檔</span><span class="sxs-lookup"><span data-stu-id="9c3b1-152">Define the profile</span></span>

<span data-ttu-id="9c3b1-153">設定檔內容應該鏡像開發人員可選取的設定選項。</span><span class="sxs-lookup"><span data-stu-id="9c3b1-153">Profile contents should mirror the developer selectable configuration options.</span></span> <span data-ttu-id="9c3b1-154">在每個介面中定義的任何使用者可設定屬性也應該包含在設定檔中。</span><span class="sxs-lookup"><span data-stu-id="9c3b1-154">Any user configurable properties defined in each interface should also be contained with the profile.</span></span>

```c#
using UnityEngine.SpatialTracking;

namespace namespace Microsoft.MixedReality.Toolkit.Experimental.UnityAR
{
    [CreateAssetMenu(
        menuName = "Mixed Reality Toolkit/Profiles/Unity AR Camera Settings Profile",
        fileName = "UnityARCameraSettingsProfile",
        order = 100)]
    public class UnityARCameraSettingsProfile : BaseCameraSettingsProfile
    {
        [SerializeField]
        [Tooltip("The portion of the device (ex: color camera) from which to read the pose.")]
        private ArTrackedPose poseSource = TrackedPoseDriver.TrackedPose.ColorCamera;

        /// <summary>
        /// The portion of the device (ex: color camera) from which to read the pose.
        /// </summary>
        public ArTrackedPose PoseSource => poseSource;

        [SerializeField]
        [Tooltip("The type of tracking (position and/or rotation) to apply.")]
        private ArTrackingType trackingType = TrackedPoseDriver.TrackingType.RotationAndPosition;

        /// <summary>
        /// The type of tracking (position and/or rotation) to apply.
        /// </summary>
        public ArTrackingType TrackingType => trackingType;

        [SerializeField]
        [Tooltip("Specifies when (during Update and/or just before rendering) to update the tracking of the pose.")]
        private ArUpdateType updateType = TrackedPoseDriver.UpdateType.UpdateAndBeforeRender;

        /// <summary>
        /// Specifies when (during Update and/or just before rendering) to update the tracking of the pose.
        /// </summary>
        public ArUpdateType UpdateType => updateType;
    }
}
```

<span data-ttu-id="9c3b1-155">`CreateAssetMenu`屬性可以套用至設定檔類別，讓客戶能夠使用 [**建立**  >  **資產**  >  **混合現實工具** 組  >  **設定檔**] 功能表建立設定檔實例。</span><span class="sxs-lookup"><span data-stu-id="9c3b1-155">The `CreateAssetMenu` attribute can be applied to the profile class to enable customers to create a profile instance using the **Create** > **Assets** > **Mixed Reality Toolkit** > **Profiles** menu.</span></span>

### <a name="implement-the-inspector"></a><span data-ttu-id="9c3b1-156">執行偵測器</span><span class="sxs-lookup"><span data-stu-id="9c3b1-156">Implement the inspector</span></span>

<span data-ttu-id="9c3b1-157">設定檔偵測器是用來設定和查看設定檔內容的使用者介面。</span><span class="sxs-lookup"><span data-stu-id="9c3b1-157">Profile inspectors are the user interface for configuring and viewing profile contents.</span></span> <span data-ttu-id="9c3b1-158">每個設定檔偵測器都應擴充 [`BaseMixedRealityToolkitConfigurationProfileInspector`](xref:Microsoft.MixedReality.Toolkit.Editor.BaseMixedRealityToolkitConfigurationProfileInspector) 類別。</span><span class="sxs-lookup"><span data-stu-id="9c3b1-158">Each profile inspector should extend the [`BaseMixedRealityToolkitConfigurationProfileInspector`](xref:Microsoft.MixedReality.Toolkit.Editor.BaseMixedRealityToolkitConfigurationProfileInspector) class.</span></span>

<span data-ttu-id="9c3b1-159">`CustomEditor`屬性會通知 Unity 套用偵測器的資產類型。</span><span class="sxs-lookup"><span data-stu-id="9c3b1-159">The `CustomEditor` attribute informs Unity the type of asset to which the inspector applies.</span></span>

```c#
namespace namespace Microsoft.MixedReality.Toolkit.Experimental.UnityAR
{
    [CustomEditor(typeof(UnityARCameraSettingsProfile))]
    public class UnityARCameraSettingsProfileInspector : BaseMixedRealityToolkitConfigurationProfileInspector
    { }
}
```

## <a name="create-assembly-definitions"></a><span data-ttu-id="9c3b1-160">建立元件定義 (s) </span><span class="sxs-lookup"><span data-stu-id="9c3b1-160">Create assembly definition(s)</span></span>

<span data-ttu-id="9c3b1-161">混合現實工具組會使用元件定義 ([. asmdef](https://docs.unity3d.com/Manual/ScriptCompilationAssemblyDefinitionFiles.html)) 檔案來指定元件之間的相依性，以及協助 Unity 減少編譯時間。</span><span class="sxs-lookup"><span data-stu-id="9c3b1-161">The Mixed Reality Toolkit uses assembly definition ([.asmdef](https://docs.unity3d.com/Manual/ScriptCompilationAssemblyDefinitionFiles.html)) files to specify dependencies between components as well as to assist Unity in reducing compilation time.</span></span>

<span data-ttu-id="9c3b1-162">建議您為所有資料提供者及其編輯器元件建立元件定義檔。</span><span class="sxs-lookup"><span data-stu-id="9c3b1-162">It is recommended that assembly definition files are created for all data providers and their editor components.</span></span>

<span data-ttu-id="9c3b1-163">使用先前範例中的 [資料夾結構](#namespace-and-folder-structure) 時，ContosoCamera 資料提供者會有兩個 asmdef 檔案。</span><span class="sxs-lookup"><span data-stu-id="9c3b1-163">Using the [folder structure](#namespace-and-folder-structure) in the earlier example, there would be two .asmdef files for the ContosoCamera data provider.</span></span>

<span data-ttu-id="9c3b1-164">第一個元件定義適用于資料提供者。</span><span class="sxs-lookup"><span data-stu-id="9c3b1-164">The first assembly definition is for the data provider.</span></span> <span data-ttu-id="9c3b1-165">在此範例中，它會被稱為 ContosoCamera，而且會位於範例的 *ContosoCamera* 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="9c3b1-165">For this example, it will be called ContosoCamera and will be located in the example's *ContosoCamera* folder.</span></span> <span data-ttu-id="9c3b1-166">此元件定義必須指定 MixedReality 的相依性，以及它所相依的任何其他元件。</span><span class="sxs-lookup"><span data-stu-id="9c3b1-166">This assembly definition must specify a dependency on Microsoft.MixedReality.Toolkit and any other assemblies upon which it depends.</span></span>

<span data-ttu-id="9c3b1-167">ContosoCameraEditor 元件定義會指定設定檔偵測器和任何編輯器特定的程式碼。</span><span class="sxs-lookup"><span data-stu-id="9c3b1-167">The ContosoCameraEditor assembly definition will specify the profile inspector and any editor specific code.</span></span> <span data-ttu-id="9c3b1-168">這個檔案必須位於編輯器程式碼的根資料夾中。</span><span class="sxs-lookup"><span data-stu-id="9c3b1-168">This file must be located in the root folder of the editor code.</span></span> <span data-ttu-id="9c3b1-169">在此範例中，檔案會位於 *ContosoCamera\Editor* 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="9c3b1-169">In this example, the file will be located in the *ContosoCamera\Editor* folder.</span></span> <span data-ttu-id="9c3b1-170">此元件定義會包含 ContosoCamera 元件的參考，以及：</span><span class="sxs-lookup"><span data-stu-id="9c3b1-170">This assembly definition will contain a reference to the ContosoCamera assembly as well as:</span></span>

- <span data-ttu-id="9c3b1-171">MixedReality 工具組</span><span class="sxs-lookup"><span data-stu-id="9c3b1-171">Microsoft.MixedReality.Toolkit</span></span>
- <span data-ttu-id="9c3b1-172">MixedReality。檢查工具</span><span class="sxs-lookup"><span data-stu-id="9c3b1-172">Microsoft.MixedReality.Toolkit.Editor.Inspectors</span></span>
- <span data-ttu-id="9c3b1-173">MixedReality （工具組）</span><span class="sxs-lookup"><span data-stu-id="9c3b1-173">Microsoft.MixedReality.Toolkit.Editor.Utilities</span></span>

## <a name="register-the-data-provider"></a><span data-ttu-id="9c3b1-174">註冊資料提供者</span><span class="sxs-lookup"><span data-stu-id="9c3b1-174">Register the data provider</span></span>

<span data-ttu-id="9c3b1-175">一旦建立之後，就可以向相機系統註冊資料提供者，以便在應用程式中使用。</span><span class="sxs-lookup"><span data-stu-id="9c3b1-175">Once created, the data provider can be registered with the Camera system to be used in the application.</span></span>

![選取相機設定提供者](../Images/CameraSystem/SelectUnityArSettings.png)

## <a name="packaging-and-distribution"></a><span data-ttu-id="9c3b1-177">封裝和散發</span><span class="sxs-lookup"><span data-stu-id="9c3b1-177">Packaging and distribution</span></span>

<span data-ttu-id="9c3b1-178">散發為協力廠商元件的資料提供者，會將封裝和散發的特定詳細資料提供給開發人員的喜好設定。</span><span class="sxs-lookup"><span data-stu-id="9c3b1-178">Data providers that are distributed as third party components have the specific details of packaging and distribution left to the preference of the developer.</span></span> <span data-ttu-id="9c3b1-179">最常見的解決方案可能是透過 Unity 資產存放區產生 unitypackage 和散發。</span><span class="sxs-lookup"><span data-stu-id="9c3b1-179">Likely, the most common solution will be to generate a .unitypackage and distribute via the Unity Asset Store.</span></span>

<span data-ttu-id="9c3b1-180">如果資料提供者已提交並接受成為 Microsoft Mixed Reality 工具組套件的一部分，Microsoft MRTK 團隊將會將其封裝並散發為 MRTK 供應專案的一部分。</span><span class="sxs-lookup"><span data-stu-id="9c3b1-180">If a data provider is submitted and accepted as a part of the Microsoft Mixed Reality Toolkit package, the Microsoft MRTK team will package and distribute it as part of the MRTK offerings.</span></span>

## <a name="see-also"></a><span data-ttu-id="9c3b1-181">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9c3b1-181">See also</span></span>

- [<span data-ttu-id="9c3b1-182">攝影機系統總覽</span><span class="sxs-lookup"><span data-stu-id="9c3b1-182">Camera System Overview</span></span>](CameraSystemOverview.md)
- [<span data-ttu-id="9c3b1-183">`BaseCameraSettingsProvider` 類</span><span class="sxs-lookup"><span data-stu-id="9c3b1-183">`BaseCameraSettingsProvider` class</span></span>](xref:Microsoft.MixedReality.Toolkit.CameraSystem.BaseCameraSettingsProvider)
- [<span data-ttu-id="9c3b1-184">`IMixedRealityCameraSettingsProvider` 介面</span><span class="sxs-lookup"><span data-stu-id="9c3b1-184">`IMixedRealityCameraSettingsProvider` interface</span></span>](xref:Microsoft.MixedReality.Toolkit.CameraSystem.IMixedRealityCameraSettingsProvider)
- [<span data-ttu-id="9c3b1-185">`IMixedRealityDataProvider` 介面</span><span class="sxs-lookup"><span data-stu-id="9c3b1-185">`IMixedRealityDataProvider` interface</span></span>](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider)
