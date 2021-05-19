---
title: 建立設定提供者
description: MRTK 中相機設定的資料提供者
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: 6ec3fc1c88c1a32334cb2869ad1994863e55bf9a
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144889"
---
# <a name="creating-a-camera-settings-provider"></a>建立相機設定提供者

攝影機系統是可延伸的系統，可提供平臺特定相機設定的支援。 若要新增新攝影機設定的支援，可能需要自訂設定提供者。

> [!NOTE]
> 此範例中使用的完整原始程式碼可以在 **MRTK/Providers/UnityAR** 資料夾中找到。

## <a name="namespace-and-folder-structure"></a>命名空間和資料夾結構

資料提供者可透過下列其中一種方式散發：

1. 協力廠商附加元件
1. Microsoft Mixed Reality 工具組的一部分

將新資料提供者提交給 MRTK 的核准程式將依案例而有所不同，並會在初始提案時傳達。 您可以藉由建立新的 [*功能要求* 類型問題](https://github.com/microsoft/MixedRealityToolkit-Unity/issues)來提交提案。

### <a name="third-party-add-ons"></a>協力廠商附加元件

**Namespace**

資料提供者必須具有命名空間，才能減少潛在的名稱衝突。 建議命名空間包含下列元件。

- 產生附加元件的公司名稱
- 功能區域

例如，Contoso 公司所建立和出貨的攝影機設定提供者可能是 *"MixedReality"*。

**資料夾結構**

建議在資料夾階層中應資料提供者的原始程式碼，如下圖所示。

![範例資料夾結構](../images/camera-system/ExampleProviderFolderStructure.png)

其中 *ContosoCamera* 資料夾包含資料提供者的執行、 *編輯器* 資料夾包含偵測器 (以及任何其他 Unity 編輯器的特定程式碼) ，而 *設定檔* 資料夾包含一或多個預先製作的設定檔可編寫腳本的物件。

### <a name="mrtk-submission"></a>MRTK 提交

**Namespace**

如果將相機設定提供者提交至 [混合現實工具](https://github.com/Microsoft/MixedRealityToolkit-Unity)組存放庫，則命名空間 **必須** 以 (MixedReality 的開頭，例如： *MixedReality. CameraSystem*) 。

**資料夾結構**

所有程式碼都必須位於 MRTK/Provider 下的資料夾中， (例如： MRTK/Providers/UnityAR) 。

## <a name="define-the-camera-settings-object"></a>定義相機設定物件

建立攝影機設定提供者的第一個步驟，是決定資料類型 (例如：網格或平面，) 它會提供給應用程式。

所有空間資料物件都必須執行 [`IMixedRealityCameraSettingsProvider`](xref:Microsoft.MixedReality.Toolkit.CameraSystem.IMixedRealityCameraSettingsProvider) 介面。

## <a name="implement-the-settings-provider"></a>執行設定提供者

### <a name="specify-interface-andor-base-class-inheritance"></a>指定介面和/或基類繼承

所有相機設定提供者都必須執行 [`IMixedRealityCameraSettingsProvider`](xref:Microsoft.MixedReality.Toolkit.CameraSystem.IMixedRealityCameraSettingsProvider) 介面，以指定相機系統所需的最小功能。 MRTK foundation 包含 [`BaseCameraSettingsProvider`](xref:Microsoft.MixedReality.Toolkit.CameraSystem.BaseCameraSettingsProvider) 可提供所需功能預設執行的類別。

```c#
namespace namespace Microsoft.MixedReality.Toolkit.Experimental.UnityAR
{
    public class UnityARCameraSettings : BaseCameraSettingsProvider
    { }
}
```

#### <a name="apply-the-mixedrealitydataprovider-attribute"></a>套用 MixedRealityDataProvider 屬性

建立攝影機設定提供者的關鍵步驟是將 [`MixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.MixedRealityDataProviderAttribute) 屬性套用至類別。 此步驟可讓您為數據提供者設定預設設定檔和平臺 (s) （在相機系統設定檔中選取），以及名稱、資料夾路徑等。

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

### <a name="implement-the-imixedrealitydataprovider-methods"></a>執行 IMixedRealityDataProvider 方法

一旦定義了類別之後，下一個步驟就是提供介面的實作為 [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) 。

> [!NOTE]
> [`BaseDataProvider`](xref:Microsoft.MixedReality.Toolkit.BaseDataProvider`1)類別 [`BaseService`](xref:Microsoft.MixedReality.Toolkit.BaseService) 可透過類別提供空白的方法實作為 [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) 。 這些方法的詳細資料通常是資料提供者特有的。

由資料提供者所執行的方法如下：

- `Destroy()`
- `Disable()`
- `Enable()`
- `Initialize()`
- `Reset()`
- `Update()`

> [!NOTE]
> 並非所有的設定提供者都需要所有這些方法的執行。 強烈建議您 `Destroy()` `Initialize()` 至少執行這項工作。

### <a name="implement-the-data-provider-logic"></a>執行資料提供者邏輯

下一步是藉由執行來新增設定提供者的邏輯 [`IMixedRealityCameraSettingsProvider`](xref:Microsoft.MixedReality.Toolkit.CameraSystem.IMixedRealityCameraSettingsProvider) 。 這部分的資料提供者通常會是相機設定專屬的。

## <a name="create-the-profile-and-inspector"></a>建立設定檔和偵測器

在混合現實工具組中，資料提供者會使用 [設定檔](../profiles/profiles.md)進行設定。

### <a name="define-the-profile"></a>定義設定檔

設定檔內容應該鏡像開發人員可選取的設定選項。 在每個介面中定義的任何使用者可設定屬性也應該包含在設定檔中。

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

`CreateAssetMenu`屬性可以套用至設定檔類別，讓客戶能夠使用 [**建立**  >  **資產**  >  **混合現實工具** 組  >  **設定檔**] 功能表建立設定檔實例。

### <a name="implement-the-inspector"></a>執行偵測器

設定檔偵測器是用來設定和查看設定檔內容的使用者介面。 每個設定檔偵測器都應擴充 [`BaseMixedRealityToolkitConfigurationProfileInspector`](xref:Microsoft.MixedReality.Toolkit.Editor.BaseMixedRealityToolkitConfigurationProfileInspector) 類別。

`CustomEditor`屬性會通知 Unity 套用偵測器的資產類型。

```c#
namespace namespace Microsoft.MixedReality.Toolkit.Experimental.UnityAR
{
    [CustomEditor(typeof(UnityARCameraSettingsProfile))]
    public class UnityARCameraSettingsProfileInspector : BaseMixedRealityToolkitConfigurationProfileInspector
    { }
}
```

## <a name="create-assembly-definitions"></a>建立元件定義 (s) 

混合現實工具組會使用元件定義 ([. asmdef](https://docs.unity3d.com/Manual/ScriptCompilationAssemblyDefinitionFiles.html)) 檔案來指定元件之間的相依性，以及協助 Unity 減少編譯時間。

建議您為所有資料提供者及其編輯器元件建立元件定義檔。

使用先前範例中的 [資料夾結構](#namespace-and-folder-structure) 時，ContosoCamera 資料提供者會有兩個 asmdef 檔案。

第一個元件定義適用于資料提供者。 在此範例中，它會被稱為 ContosoCamera，而且會位於範例的 *ContosoCamera* 資料夾中。 此元件定義必須指定 MixedReality 的相依性，以及它所相依的任何其他元件。

ContosoCameraEditor 元件定義會指定設定檔偵測器和任何編輯器特定的程式碼。 這個檔案必須位於編輯器程式碼的根資料夾中。 在此範例中，檔案會位於 *ContosoCamera\Editor* 資料夾中。 此元件定義會包含 ContosoCamera 元件的參考，以及：

- MixedReality 工具組
- MixedReality。檢查工具
- MixedReality （工具組）

## <a name="register-the-data-provider"></a>註冊資料提供者

一旦建立之後，就可以向相機系統註冊資料提供者，以便在應用程式中使用。

![選取相機設定提供者](../images/camera-system/SelectUnityArSettings.png)

## <a name="packaging-and-distribution"></a>封裝和散發

散發為協力廠商元件的資料提供者，會將封裝和散發的特定詳細資料提供給開發人員的喜好設定。 最常見的解決方案可能是透過 Unity 資產存放區產生 unitypackage 和散發。

如果資料提供者已提交並接受成為 Microsoft Mixed Reality 工具組套件的一部分，Microsoft MRTK 團隊將會將其封裝並散發為 MRTK 供應專案的一部分。

## <a name="see-also"></a>另請參閱

- [攝影機系統總覽](camera-system-overview.md)
- [`BaseCameraSettingsProvider` 類別](xref:Microsoft.MixedReality.Toolkit.CameraSystem.BaseCameraSettingsProvider)
- [`IMixedRealityCameraSettingsProvider` 介面](xref:Microsoft.MixedReality.Toolkit.CameraSystem.IMixedRealityCameraSettingsProvider)
- [`IMixedRealityDataProvider` 介面](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider)
