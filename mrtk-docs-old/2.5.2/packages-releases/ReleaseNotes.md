---
title: ReleaseNotes
description: 目前 MRTK 版本的發行 nots
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: 0ca835113ce9650b2eea1e6af340cce22ee02ca8
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/03/2021
ms.locfileid: "101783495"
---
# <a name="microsoft-mixed-reality-toolkit-251-release-notes"></a><span data-ttu-id="1c875-104">Microsoft Mixed Reality 工具組2.5.1 版本資訊</span><span class="sxs-lookup"><span data-stu-id="1c875-104">Microsoft Mixed Reality Toolkit 2.5.1 release notes</span></span>

- [<span data-ttu-id="1c875-105">新功能</span><span class="sxs-lookup"><span data-stu-id="1c875-105">What's new</span></span>](#whats-new)
- [<span data-ttu-id="1c875-106">重大變更</span><span class="sxs-lookup"><span data-stu-id="1c875-106">Breaking changes</span></span>](#breaking-changes)
- [<span data-ttu-id="1c875-107">更新指導方針</span><span class="sxs-lookup"><span data-stu-id="1c875-107">Updating guidance</span></span>](../updates-deployment/Updating.md#upgrading-to-a-new-version-of-mrtk)
- [<span data-ttu-id="1c875-108">已知問題</span><span class="sxs-lookup"><span data-stu-id="1c875-108">Known issues</span></span>](#known-issues)

> [!IMPORTANT]
> <span data-ttu-id="1c875-109">有一個已知的編譯器問題，會影響使用 ARM64 針對 Microsoft HoloLens 2 所建立的應用程式。</span><span class="sxs-lookup"><span data-stu-id="1c875-109">There is a known compiler issue that impacts applications built for Microsoft HoloLens 2 using ARM64.</span></span> <span data-ttu-id="1c875-110">將 Visual Studio 2019 更新至16.8 版或更新版本，即可修正此問題。</span><span class="sxs-lookup"><span data-stu-id="1c875-110">This issue is fixed by updating Visual Studio 2019 to version 16.8 or later.</span></span> <span data-ttu-id="1c875-111">如果您無法更新 Visual Studio，請匯入套件以套用因應措施 `com.microsoft.mixedreality.toolkit.tools` 。</span><span class="sxs-lookup"><span data-stu-id="1c875-111">If you are unable to update Visual Studio, please import the `com.microsoft.mixedreality.toolkit.tools` package to apply a workaround.</span></span>

## <a name="whats-new"></a><span data-ttu-id="1c875-112">最新消息</span><span class="sxs-lookup"><span data-stu-id="1c875-112">What's new</span></span>

### <a name="package-dependency-errors-fixed"></a><span data-ttu-id="1c875-113">已修正套件相依性錯誤</span><span class="sxs-lookup"><span data-stu-id="1c875-113">Package dependency errors fixed</span></span>

<span data-ttu-id="1c875-114">此版本修正不正確的套件間檔案相依性 (例如：標準資產中的檔案不再于基礎) 中正確參考檔案。</span><span class="sxs-lookup"><span data-stu-id="1c875-114">This release fixes incorrect inter-package file dependencies (ex: files in Standard Assets no longer incorrectly reference files in Foundation).</span></span> <span data-ttu-id="1c875-115">2.5.1 版也會在文字網格 Pro 上新增明確的相依性。</span><span class="sxs-lookup"><span data-stu-id="1c875-115">Version 2.5.1 also adds an explicit dependency on Text Mesh Pro.</span></span>

### <a name="standard-assets-package-shaders-copied-to-assetsmrtkshaders"></a><span data-ttu-id="1c875-116">複製到資產/MRTK/著色器的標準資產套件著色器</span><span class="sxs-lookup"><span data-stu-id="1c875-116">Standard Assets package shaders copied to Assets/MRTK/Shaders</span></span>

<span data-ttu-id="1c875-117">當標準資產套件透過 UPM 安裝時，著色器將會複製到 [資產/MRTK/著色器] 資料夾，使其不再是不可變的。</span><span class="sxs-lookup"><span data-stu-id="1c875-117">When the Standard Assets package is installed via UPM, the shaders will be copied to the Assets/MRTK/Shaders folder so that they will no longer be immutable.</span></span> <span data-ttu-id="1c875-118">這可解決在下一次載入專案時， (URP) 還原舊版行為的通用轉譯管線所更新的著色器問題。</span><span class="sxs-lookup"><span data-stu-id="1c875-118">This resolves the issue of shaders updated for the Universal Render Pipeline (URP) reverting the legacy behavior the next time the project is loaded.</span></span>

### <a name="fixed-teleport-cursor-sticking-to-hands"></a><span data-ttu-id="1c875-119">固定的傳送游標停留在手中</span><span class="sxs-lookup"><span data-stu-id="1c875-119">Fixed teleport cursor sticking to hands</span></span>

<span data-ttu-id="1c875-120">此版本修正了 [傳送目的地] 游標可以用來手上視覺效果的 [問題](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8755) 。</span><span class="sxs-lookup"><span data-stu-id="1c875-120">This release fixes an [issue](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8755) where the teleport destination cursor can stick to hand visuals.</span></span>

## <a name="breaking-changes"></a><span data-ttu-id="1c875-121">重大變更</span><span class="sxs-lookup"><span data-stu-id="1c875-121">Breaking changes</span></span>

<span data-ttu-id="1c875-122">自版本2.5.0 之後，沒有任何中斷性變更。</span><span class="sxs-lookup"><span data-stu-id="1c875-122">There are no breaking changes since version 2.5.0.</span></span>

## <a name="known-issues"></a><span data-ttu-id="1c875-123">已知問題</span><span class="sxs-lookup"><span data-stu-id="1c875-123">Known issues</span></span>

### <a name="some-mixed-reality-toolkit-standard-shader-features-require-the-foundation-package"></a><span data-ttu-id="1c875-124">部分混合現實工具組標準著色器功能需要基礎封裝</span><span class="sxs-lookup"><span data-stu-id="1c875-124">Some Mixed Reality Toolkit Standard Shader features require the Foundation package</span></span>

<span data-ttu-id="1c875-125">透過 Unity 套件管理員匯入時，MRTK 標準著色器公用程式腳本 (例如： HoverLight.cs) 不會與標準資產套件中的著色器共置。</span><span class="sxs-lookup"><span data-stu-id="1c875-125">When imported via the Unity Package Manager, the MRTK Standard Shader utilities scripts (ex: HoverLight.cs) are not co-located with the shader in the Standard Assets package.</span></span> <span data-ttu-id="1c875-126">若要存取此功能，應用程式將需要匯入基礎套件。</span><span class="sxs-lookup"><span data-stu-id="1c875-126">To access this functionality, applications will require the Foundation package to be imported.</span></span>

### <a name="cameracache-may-create-a-new-camera-on-shutdown"></a><span data-ttu-id="1c875-127">CameraCache 可能會在關機時建立新的攝影機</span><span class="sxs-lookup"><span data-stu-id="1c875-127">CameraCache may create a new camera on shutdown</span></span>

<span data-ttu-id="1c875-128">在某些情況下 (例如在 Unity 編輯器) 中使用 LeapMotion 提供者時，CameraCache 可能會在關閉時重新建立 MainCamera。</span><span class="sxs-lookup"><span data-stu-id="1c875-128">In some situations (e.g. when using the LeapMotion provider in the Unity Editor), it is possible for the CameraCache to re-create the MainCamera on shutdown.</span></span> <span data-ttu-id="1c875-129">如需詳細資訊，請參閱 [此問題](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8459) 。</span><span class="sxs-lookup"><span data-stu-id="1c875-129">Please see [this issue](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8459) for more information.</span></span>

### <a name="filenotfoundexception-when-examples-are-imported-via-unity-package-manager"></a><span data-ttu-id="1c875-130">透過 Unity 套件管理員匯入範例時的 FileNotFoundException</span><span class="sxs-lookup"><span data-stu-id="1c875-130">FileNotFoundException when examples are imported via Unity Package Manager</span></span>

<span data-ttu-id="1c875-131">根據專案路徑的長度，透過 Unity 套件管理員匯入範例可能會在 Unity 主控台中產生 FileNotFoundException 訊息。</span><span class="sxs-lookup"><span data-stu-id="1c875-131">Depending on the length of the project path, importing examples via Unity Package Manager may generate FileNotFoundException messages in the Unity Console.</span></span> <span data-ttu-id="1c875-132">造成這種情況的原因是「遺失」檔案的路徑超過 MAX_PATH (256 個字元) 。</span><span class="sxs-lookup"><span data-stu-id="1c875-132">The cause of this is the path to the "missing" file being longer than MAX_PATH (256 characters).</span></span> <span data-ttu-id="1c875-133">若要解決此問題，請縮短專案路徑的長度。</span><span class="sxs-lookup"><span data-stu-id="1c875-133">To resolve, please shorten the length of the project path.</span></span>

### <a name="no-spatializer-was-specified-the-application-will-not-support-spatial-sound"></a><span data-ttu-id="1c875-134">未指定空間定位器。</span><span class="sxs-lookup"><span data-stu-id="1c875-134">No spatializer was specified.</span></span> <span data-ttu-id="1c875-135">應用程式將不支援空間音效</span><span class="sxs-lookup"><span data-stu-id="1c875-135">The application will not support Spatial Sound</span></span>

<span data-ttu-id="1c875-136">如果未設定音訊空間定位器，則會出現「未指定任何空間定位器」警告。</span><span class="sxs-lookup"><span data-stu-id="1c875-136">A "No spatializer was specified" warning will appear if an audio spatializer is not configured.</span></span> <span data-ttu-id="1c875-137">如果未安裝 XR 套件，則會發生這種情況，因為 Unity 包含這些套件中的 spatializers。</span><span class="sxs-lookup"><span data-stu-id="1c875-137">This can occur if no XR package is installed, as Unity includes spatializers in these pacakges.</span></span>

<span data-ttu-id="1c875-138">若要解決此問題，請確定：</span><span class="sxs-lookup"><span data-stu-id="1c875-138">To resolve, please ensure that:</span></span>

- <span data-ttu-id="1c875-139">**視窗**  > **套件管理員** 已安裝一或多個 XR 套件</span><span class="sxs-lookup"><span data-stu-id="1c875-139">**Window** > **Package Manager** has one or more XR packages installed</span></span>
- <span data-ttu-id="1c875-140">**混合現實工具**  >  組 **公用程式**  > **設定 Unity 專案** 並為 **音訊空間定位器** 進行選取</span><span class="sxs-lookup"><span data-stu-id="1c875-140">**Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** and make a selection for **Audio Spatializer**</span></span>

  ![選取音訊 Apatializer](../features/images/release-notes/SpatializerSelection.png)

### <a name="nullreferenceexception-object-reference-not-set-to-an-instance-of-an-object-scenetransitionserviceinitialize"></a><span data-ttu-id="1c875-142">NullReferenceException：物件參考未設定為物件的實例 (SceneTransitionService.Initialize) </span><span class="sxs-lookup"><span data-stu-id="1c875-142">NullReferenceException: Object reference not set to an instance of an object (SceneTransitionService.Initialize)</span></span>

<span data-ttu-id="1c875-143">在某些情況下，開啟 `EyeTrackingDemo-00-RootScene` 可能會在 SceneTransitionService 類別的 Initialize 方法中造成 NullReferenceException。</span><span class="sxs-lookup"><span data-stu-id="1c875-143">In some situations, opening `EyeTrackingDemo-00-RootScene` may cause a NullReferenceException in the Initialize method of the SceneTransitionService class.</span></span>
<span data-ttu-id="1c875-144">此錯誤是因為未設定場景轉換服務的設定檔。</span><span class="sxs-lookup"><span data-stu-id="1c875-144">This error is due to the Scene Transition Service's configuration profile being unset.</span></span> <span data-ttu-id="1c875-145">若要解決此問題，請使用下列步驟：</span><span class="sxs-lookup"><span data-stu-id="1c875-145">To resolve, please use the following steps:</span></span>

- <span data-ttu-id="1c875-146">流覽至階層 `MixedRealityToolkit` 中的物件</span><span class="sxs-lookup"><span data-stu-id="1c875-146">Navigate to the `MixedRealityToolkit` object in the Hierarchy</span></span>
- <span data-ttu-id="1c875-147">在 [偵測器] 視窗中，選取 `Extensions`</span><span class="sxs-lookup"><span data-stu-id="1c875-147">In the Inspector window, select `Extensions`</span></span>
- <span data-ttu-id="1c875-148">如果未展開，請展開 `Scene Transition Service`</span><span class="sxs-lookup"><span data-stu-id="1c875-148">If not expanded, expand `Scene Transition Service`</span></span>
- <span data-ttu-id="1c875-149">將的值設定 `Configuration Profile` 為 **MRTKExamplesHubSceneTransitionServiceProfile**</span><span class="sxs-lookup"><span data-stu-id="1c875-149">Set the value of `Configuration Profile` to **MRTKExamplesHubSceneTransitionServiceProfile**</span></span>

<img src="../features/images/release-notes/FixSceneTransitionProfile.png" width="500px" alt="Fix Scene Transition">

### <a name="oculus-quest"></a><span data-ttu-id="1c875-150">Oculus 的追求</span><span class="sxs-lookup"><span data-stu-id="1c875-150">Oculus Quest</span></span>

<span data-ttu-id="1c875-151">目前在 [以獨立平臺為目標時，使用 OCULUS XR 外掛程式](https://forum.unity.com/threads/unable-to-start-oculus-xr-plugin.913883/)的已知問題。</span><span class="sxs-lookup"><span data-stu-id="1c875-151">There is currently a known issue for using the [Oculus XR plugin with when targeting Standalone platforms](https://forum.unity.com/threads/unable-to-start-oculus-xr-plugin.913883/).</span></span>  <span data-ttu-id="1c875-152">查看 Oculus bug 追蹤程式/論壇/版本資訊以取得更新。</span><span class="sxs-lookup"><span data-stu-id="1c875-152">Check the Oculus bug tracker/forums/release notes for updates.</span></span>

<span data-ttu-id="1c875-153">Bug 會以這一組3個錯誤表示：</span><span class="sxs-lookup"><span data-stu-id="1c875-153">The bug is signified with this set of 3 errors:</span></span>

![Oculus XR 外掛程式錯誤](https://forum.unity.com/attachments/erori-unity-png.644204/)

### <a name="unityui-and-textmeshpro"></a><span data-ttu-id="1c875-155">UnityUI 和 TextMeshPro</span><span class="sxs-lookup"><span data-stu-id="1c875-155">UnityUI and TextMeshPro</span></span>

<span data-ttu-id="1c875-156">較新版本的 TextMeshPro 有一個已知問題 (1.5.0 + 或 2.1.1 +) ，其中下拉式清單和粗體字字元間距的預設字型大小已改變。</span><span class="sxs-lookup"><span data-stu-id="1c875-156">There's a known issue for newer versions of TextMeshPro (1.5.0+ or 2.1.1+), where the default font size for dropdowns and bold font character spacing has been altered.</span></span>

![TMP 映射](https://user-images.githubusercontent.com/68253937/93158069-4d582f00-f6c0-11ea-87ad-94d0ba3ba6e5.png)

<span data-ttu-id="1c875-158">這可以透過降級至舊版的 TextMeshPro 來解決。</span><span class="sxs-lookup"><span data-stu-id="1c875-158">This can be worked around by downgrading to an earlier version of TextMeshPro.</span></span> <span data-ttu-id="1c875-159">See [issue #8556](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8556) for more details.</span><span class="sxs-lookup"><span data-stu-id="1c875-159">See [issue #8556](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8556) for more details.</span></span>
