---
title: MRTK 2.5 版本資訊
description: 目前 MRTK 版本的發行 nots
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: e2d93993ad6100adc0c9bb70067e6cb09d61c68b
ms.sourcegitcommit: 7a8fa3257a13635ddad77d963e49440f62c19774
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2021
ms.locfileid: "101883266"
---
# <a name="microsoft-mixed-reality-toolkit-254-release-notes"></a><span data-ttu-id="dcc7d-104">Microsoft Mixed Reality 工具組2.5.4 版本資訊</span><span class="sxs-lookup"><span data-stu-id="dcc7d-104">Microsoft Mixed Reality Toolkit 2.5.4 release notes</span></span>

- [<span data-ttu-id="dcc7d-105">新功能</span><span class="sxs-lookup"><span data-stu-id="dcc7d-105">What's new</span></span>](#whats-new)
- [<span data-ttu-id="dcc7d-106">更新指導方針</span><span class="sxs-lookup"><span data-stu-id="dcc7d-106">Updating guidance</span></span>](../updates-deployment/updating.md#upgrading-to-a-new-version-of-mrtk)
- [<span data-ttu-id="dcc7d-107">已知問題</span><span class="sxs-lookup"><span data-stu-id="dcc7d-107">Known issues</span></span>](#known-issues)

> [!IMPORTANT]
> <span data-ttu-id="dcc7d-108">有一個已知的編譯器問題，會影響使用 ARM64 針對 Microsoft HoloLens 2 所建立的應用程式。</span><span class="sxs-lookup"><span data-stu-id="dcc7d-108">There is a known compiler issue that impacts applications built for Microsoft HoloLens 2 using ARM64.</span></span> <span data-ttu-id="dcc7d-109">將 Visual Studio 2019 更新至16.8 版或更新版本，即可修正此問題。</span><span class="sxs-lookup"><span data-stu-id="dcc7d-109">This issue is fixed by updating Visual Studio 2019 to version 16.8 or later.</span></span> <span data-ttu-id="dcc7d-110">如果您無法更新 Visual Studio，請匯入套件以套用因應措施 `com.microsoft.mixedreality.toolkit.tools` 。</span><span class="sxs-lookup"><span data-stu-id="dcc7d-110">If you are unable to update Visual Studio, please import the `com.microsoft.mixedreality.toolkit.tools` package to apply a workaround.</span></span>

## <a name="whats-new"></a><span data-ttu-id="dcc7d-111">最新消息</span><span class="sxs-lookup"><span data-stu-id="dcc7d-111">What's new</span></span>

### <a name="fixes-a-bug-with-oculus-integration-when-using-upm"></a><span data-ttu-id="dcc7d-112">使用 UPM 來修正 Oculus 整合的 bug</span><span class="sxs-lookup"><span data-stu-id="dcc7d-112">Fixes a bug with Oculus Integration when using UPM</span></span>

<span data-ttu-id="dcc7d-113">使用 UPM 時，OculusXRSDKDeviceManagerProfile 在啟動時一律會將其 [prefabs 設定為 None](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9160)。</span><span class="sxs-lookup"><span data-stu-id="dcc7d-113">When using UPM, the OculusXRSDKDeviceManagerProfile would always have its [prefabs set to None on startup](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9160).</span></span> <span data-ttu-id="dcc7d-114">此版本會將裝置管理員設定為在啟動時指向一組工作 prefabs。</span><span class="sxs-lookup"><span data-stu-id="dcc7d-114">This release configures the Device Manager to point to a working set of prefabs on startup.</span></span>

### <a name="fixes-an-issue-with-openxr-via-upm"></a><span data-ttu-id="dcc7d-115">修正 OpenXR via UPM 的問題</span><span class="sxs-lookup"><span data-stu-id="dcc7d-115">Fixes an issue with OpenXR via UPM</span></span>

<span data-ttu-id="dcc7d-116">修正在使用 OpenXR 和 MRTK 透過 Unity 的套件管理員時，OpenXR 提供者預設不會新增至 link.xml 的問題，會導致新的專案無法在裝置上執行。</span><span class="sxs-lookup"><span data-stu-id="dcc7d-116">Fixes an issue where the OpenXR providers weren't added to the link.xml by default, causing new projects to fail to run on-device when using OpenXR and MRTK via Unity's Package Manager.</span></span> <span data-ttu-id="dcc7d-117">已升級的現有專案仍需要手動加入。</span><span class="sxs-lookup"><span data-stu-id="dcc7d-117">Existing projects that are upgraded will still need this added manually.</span></span>

## <a name="what-was-new-in-253"></a><span data-ttu-id="dcc7d-118">2.5.3 的新功能</span><span class="sxs-lookup"><span data-stu-id="dcc7d-118">What was new in 2.5.3</span></span>

### <a name="fixes-a-regression-with-oculus-introduced-in-252"></a><span data-ttu-id="dcc7d-119">修正在2.5.2 中引進的 Oculus 回歸</span><span class="sxs-lookup"><span data-stu-id="dcc7d-119">Fixes a regression with Oculus introduced in 2.5.2</span></span>

<span data-ttu-id="dcc7d-120">2.5.2 在 [整合 OCULUS SDK 時引進了組建問題](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9083)。</span><span class="sxs-lookup"><span data-stu-id="dcc7d-120">2.5.2 introduced [a build issue when integrating the Oculus SDK](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9083).</span></span> <span data-ttu-id="dcc7d-121">此版本會還原該問題。</span><span class="sxs-lookup"><span data-stu-id="dcc7d-121">This release reverts that issue.</span></span>

### <a name="add-support-for-openxr"></a><span data-ttu-id="dcc7d-122">新增對 OpenXR 的支援</span><span class="sxs-lookup"><span data-stu-id="dcc7d-122">Add support for OpenXR</span></span>

<span data-ttu-id="dcc7d-123">已新增 Unity OpenXR preview 套件和 Microsoft Mixed Reality OpenXR 封裝的初始支援。</span><span class="sxs-lookup"><span data-stu-id="dcc7d-123">Initial support for Unity's OpenXR preview package and Microsoft's Mixed Reality OpenXR package has been added.</span></span> <span data-ttu-id="dcc7d-124">如需詳細資訊，請參閱 [MRTK/XRSDK 開始使用頁面](../configuration/getting-started-with-mrtk-and-xrsdk.md)、 [Unity 的論壇文章](https://forum.unity.com/threads/unity-support-for-openxr-in-preview.1023613/)或 [Microsoft 的檔](https://aka.ms/openxr-unity-install) 。</span><span class="sxs-lookup"><span data-stu-id="dcc7d-124">See [the MRTK/XRSDK getting started page](../configuration/getting-started-with-mrtk-and-xrsdk.md), [Unity's forum post](https://forum.unity.com/threads/unity-support-for-openxr-in-preview.1023613/), or [Microsoft's documentation](https://aka.ms/openxr-unity-install) for more information.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="dcc7d-125">Unity 中的 OpenXR 僅支援 Unity 2020.2 和更新版本。</span><span class="sxs-lookup"><span data-stu-id="dcc7d-125">OpenXR in Unity is only supported on Unity 2020.2 and higher.</span></span>
>
> <span data-ttu-id="dcc7d-126">目前它也只支援 x64 和 ARM64 組建。</span><span class="sxs-lookup"><span data-stu-id="dcc7d-126">Currently, it also only supports x64 and ARM64 builds.</span></span>

### <a name="boundary-visualization-errors-fixed"></a><span data-ttu-id="dcc7d-127">已修正界限視覺效果錯誤</span><span class="sxs-lookup"><span data-stu-id="dcc7d-127">Boundary visualization errors fixed</span></span>

<span data-ttu-id="dcc7d-128">界限視覺效果（例如 floor 或牆壁）現在將會正確設定，並在執行時間根據界限設定檔顯示。</span><span class="sxs-lookup"><span data-stu-id="dcc7d-128">Boundary visualizations, like the floor or walls, will now be properly configured and visible at runtime according to the boundary profile.</span></span>

### <a name="msbuild-for-unity-support"></a><span data-ttu-id="dcc7d-129">適用于 Unity 的 MSBuild 支援</span><span class="sxs-lookup"><span data-stu-id="dcc7d-129">MSBuild for Unity support</span></span>

<span data-ttu-id="dcc7d-130">從2.5.2 版本開始，已移除對 MSBuild for Unity 的支援，以配合 [Unity 的新套件指引](https://forum.unity.com/threads/updates-to-our-terms-of-service-and-new-package-guidelines.999940/)。</span><span class="sxs-lookup"><span data-stu-id="dcc7d-130">Support for MSBuild for Unity has been removed as of the 2.5.2 release, to align with [Unity's new package guidance](https://forum.unity.com/threads/updates-to-our-terms-of-service-and-new-package-guidelines.999940/).</span></span>

## <a name="known-issues"></a><span data-ttu-id="dcc7d-131">已知問題</span><span class="sxs-lookup"><span data-stu-id="dcc7d-131">Known issues</span></span>

### <a name="openxr"></a><span data-ttu-id="dcc7d-132">OpenXR</span><span class="sxs-lookup"><span data-stu-id="dcc7d-132">OpenXR</span></span>

<span data-ttu-id="dcc7d-133">目前有一個已知的全像是「全像」遠端和 OpenXR 的問題，也就是沒有一直可用的手接點。</span><span class="sxs-lookup"><span data-stu-id="dcc7d-133">There's currently a known issue with Holographic Remoting and OpenXR, where hand joints aren't consistently available.</span></span>
<span data-ttu-id="dcc7d-134">此外，眼睛追蹤範例場景目前不相容，不過眼睛追蹤 *的確* 可以運作。</span><span class="sxs-lookup"><span data-stu-id="dcc7d-134">Additionally, the eye tracking sample scenes aren't currently compatible, though eye tracking *does* work.</span></span>

### <a name="some-mixed-reality-toolkit-standard-shader-features-require-the-foundation-package"></a><span data-ttu-id="dcc7d-135">部分混合現實工具組標準著色器功能需要基礎封裝</span><span class="sxs-lookup"><span data-stu-id="dcc7d-135">Some Mixed Reality Toolkit Standard Shader features require the Foundation package</span></span>

<span data-ttu-id="dcc7d-136">透過 Unity 套件管理員匯入時，MRTK 標準著色器公用程式腳本 (例如： HoverLight.cs) 不會與標準資產套件中的著色器共置。</span><span class="sxs-lookup"><span data-stu-id="dcc7d-136">When imported via the Unity Package Manager, the MRTK Standard Shader utilities scripts (ex: HoverLight.cs) are not co-located with the shader in the Standard Assets package.</span></span> <span data-ttu-id="dcc7d-137">若要存取此功能，應用程式將需要匯入基礎套件。</span><span class="sxs-lookup"><span data-stu-id="dcc7d-137">To access this functionality, applications will require the Foundation package to be imported.</span></span>

### <a name="cameracache-may-create-a-new-camera-on-shutdown"></a><span data-ttu-id="dcc7d-138">CameraCache 可能會在關機時建立新的攝影機</span><span class="sxs-lookup"><span data-stu-id="dcc7d-138">CameraCache may create a new camera on shutdown</span></span>

<span data-ttu-id="dcc7d-139">在某些情況下 (例如在 Unity 編輯器) 中使用 LeapMotion 提供者時，CameraCache 可能會在關閉時重新建立 MainCamera。</span><span class="sxs-lookup"><span data-stu-id="dcc7d-139">In some situations (e.g. when using the LeapMotion provider in the Unity Editor), it is possible for the CameraCache to re-create the MainCamera on shutdown.</span></span> <span data-ttu-id="dcc7d-140">如需詳細資訊，請參閱 [此問題](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8459) 。</span><span class="sxs-lookup"><span data-stu-id="dcc7d-140">Please see [this issue](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8459) for more information.</span></span>

### <a name="filenotfoundexception-when-examples-are-imported-via-unity-package-manager"></a><span data-ttu-id="dcc7d-141">透過 Unity 套件管理員匯入範例時的 FileNotFoundException</span><span class="sxs-lookup"><span data-stu-id="dcc7d-141">FileNotFoundException when examples are imported via Unity Package Manager</span></span>

<span data-ttu-id="dcc7d-142">根據專案路徑的長度，透過 Unity 套件管理員匯入範例可能會在 Unity 主控台中產生 FileNotFoundException 訊息。</span><span class="sxs-lookup"><span data-stu-id="dcc7d-142">Depending on the length of the project path, importing examples via Unity Package Manager may generate FileNotFoundException messages in the Unity Console.</span></span> <span data-ttu-id="dcc7d-143">造成這種情況的原因是「遺失」檔案的路徑超過 MAX_PATH (256 個字元) 。</span><span class="sxs-lookup"><span data-stu-id="dcc7d-143">The cause of this is the path to the "missing" file being longer than MAX_PATH (256 characters).</span></span> <span data-ttu-id="dcc7d-144">若要解決此問題，請縮短專案路徑的長度。</span><span class="sxs-lookup"><span data-stu-id="dcc7d-144">To resolve, please shorten the length of the project path.</span></span>

### <a name="no-spatializer-was-specified-the-application-will-not-support-spatial-sound"></a><span data-ttu-id="dcc7d-145">未指定空間定位器。</span><span class="sxs-lookup"><span data-stu-id="dcc7d-145">No spatializer was specified.</span></span> <span data-ttu-id="dcc7d-146">應用程式將不支援空間音效</span><span class="sxs-lookup"><span data-stu-id="dcc7d-146">The application will not support Spatial Sound</span></span>

<span data-ttu-id="dcc7d-147">如果未設定音訊空間定位器，則會出現「未指定任何空間定位器」警告。</span><span class="sxs-lookup"><span data-stu-id="dcc7d-147">A "No spatializer was specified" warning will appear if an audio spatializer is not configured.</span></span> <span data-ttu-id="dcc7d-148">如果未安裝 XR 套件，則會發生這種情況，因為 Unity 包含這些套件中的 spatializers。</span><span class="sxs-lookup"><span data-stu-id="dcc7d-148">This can occur if no XR package is installed, as Unity includes spatializers in these packages.</span></span>

<span data-ttu-id="dcc7d-149">若要解決此問題，請確定：</span><span class="sxs-lookup"><span data-stu-id="dcc7d-149">To resolve, please ensure that:</span></span>

- <span data-ttu-id="dcc7d-150">**視窗**  > **套件管理員** 已安裝一或多個 XR 套件</span><span class="sxs-lookup"><span data-stu-id="dcc7d-150">**Window** > **Package Manager** has one or more XR packages installed</span></span>
- <span data-ttu-id="dcc7d-151">**混合現實工具**  >  組 **公用程式**  > **設定 Unity 專案** 並為 **音訊空間定位器** 進行選取</span><span class="sxs-lookup"><span data-stu-id="dcc7d-151">**Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** and make a selection for **Audio Spatializer**</span></span>

  ![選取音訊 Apatializer](images/SpatializerSelection.png)

### <a name="nullreferenceexception-object-reference-not-set-to-an-instance-of-an-object-scenetransitionserviceinitialize"></a><span data-ttu-id="dcc7d-153">NullReferenceException：物件參考未設定為物件的實例 (SceneTransitionService.Initialize) </span><span class="sxs-lookup"><span data-stu-id="dcc7d-153">NullReferenceException: Object reference not set to an instance of an object (SceneTransitionService.Initialize)</span></span>

<span data-ttu-id="dcc7d-154">在某些情況下，開啟 `EyeTrackingDemo-00-RootScene` 可能會在 SceneTransitionService 類別的 Initialize 方法中造成 NullReferenceException。</span><span class="sxs-lookup"><span data-stu-id="dcc7d-154">In some situations, opening `EyeTrackingDemo-00-RootScene` may cause a NullReferenceException in the Initialize method of the SceneTransitionService class.</span></span>
<span data-ttu-id="dcc7d-155">此錯誤是因為未設定場景轉換服務的設定檔。</span><span class="sxs-lookup"><span data-stu-id="dcc7d-155">This error is due to the Scene Transition Service's configuration profile being unset.</span></span> <span data-ttu-id="dcc7d-156">若要解決此問題，請使用下列步驟：</span><span class="sxs-lookup"><span data-stu-id="dcc7d-156">To resolve, please use the following steps:</span></span>

- <span data-ttu-id="dcc7d-157">流覽至階層 `MixedRealityToolkit` 中的物件</span><span class="sxs-lookup"><span data-stu-id="dcc7d-157">Navigate to the `MixedRealityToolkit` object in the Hierarchy</span></span>
- <span data-ttu-id="dcc7d-158">在 [偵測器] 視窗中，選取 `Extensions`</span><span class="sxs-lookup"><span data-stu-id="dcc7d-158">In the Inspector window, select `Extensions`</span></span>
- <span data-ttu-id="dcc7d-159">如果未展開，請展開 `Scene Transition Service`</span><span class="sxs-lookup"><span data-stu-id="dcc7d-159">If not expanded, expand `Scene Transition Service`</span></span>
- <span data-ttu-id="dcc7d-160">將的值設定 `Configuration Profile` 為 **MRTKExamplesHubSceneTransitionServiceProfile**</span><span class="sxs-lookup"><span data-stu-id="dcc7d-160">Set the value of `Configuration Profile` to **MRTKExamplesHubSceneTransitionServiceProfile**</span></span>

![修正場景轉換](images/FixSceneTransitionProfile.png)

### <a name="oculus-quest"></a><span data-ttu-id="dcc7d-162">Oculus 的追求</span><span class="sxs-lookup"><span data-stu-id="dcc7d-162">Oculus Quest</span></span>

<span data-ttu-id="dcc7d-163">目前在 [以獨立平臺為目標時，使用 OCULUS XR 外掛程式](https://forum.unity.com/threads/unable-to-start-oculus-xr-plugin.913883/)的已知問題。</span><span class="sxs-lookup"><span data-stu-id="dcc7d-163">There is currently a known issue for using the [Oculus XR plugin with when targeting Standalone platforms](https://forum.unity.com/threads/unable-to-start-oculus-xr-plugin.913883/).</span></span>  <span data-ttu-id="dcc7d-164">查看 Oculus bug 追蹤程式/論壇/版本資訊以取得更新。</span><span class="sxs-lookup"><span data-stu-id="dcc7d-164">Check the Oculus bug tracker/forums/release notes for updates.</span></span>

<span data-ttu-id="dcc7d-165">Bug 會以這一組3個錯誤表示：</span><span class="sxs-lookup"><span data-stu-id="dcc7d-165">The bug is signified with this set of 3 errors:</span></span>

![Oculus XR 外掛程式錯誤](https://forum.unity.com/attachments/erori-unity-png.644204/)

### <a name="unityui-and-textmeshpro"></a><span data-ttu-id="dcc7d-167">UnityUI 和 TextMeshPro</span><span class="sxs-lookup"><span data-stu-id="dcc7d-167">UnityUI and TextMeshPro</span></span>

<span data-ttu-id="dcc7d-168">較新版本的 TextMeshPro 有一個已知問題 (1.5.0 + 或 2.1.1 +) ，其中下拉式清單和粗體字字元間距的預設字型大小已改變。</span><span class="sxs-lookup"><span data-stu-id="dcc7d-168">There's a known issue for newer versions of TextMeshPro (1.5.0+ or 2.1.1+), where the default font size for dropdowns and bold font character spacing has been altered.</span></span>

![TMP 映射](https://user-images.githubusercontent.com/68253937/93158069-4d582f00-f6c0-11ea-87ad-94d0ba3ba6e5.png)

<span data-ttu-id="dcc7d-170">這可以透過降級至舊版的 TextMeshPro 來解決。</span><span class="sxs-lookup"><span data-stu-id="dcc7d-170">This can be worked around by downgrading to an earlier version of TextMeshPro.</span></span> <span data-ttu-id="dcc7d-171">See [issue #8556](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8556) for more details.</span><span class="sxs-lookup"><span data-stu-id="dcc7d-171">See [issue #8556](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8556) for more details.</span></span>
