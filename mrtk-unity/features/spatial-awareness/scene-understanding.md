---
title: 場景理解
description: 描述 MRTK 中的場景理解
author: MaxWang-MS
ms.author: wangmax
ms.date: 05/27/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、場景理解
ms.openlocfilehash: 67a8b99a281b6deecd621edb5600578806812d8a
ms.sourcegitcommit: 86fafb3a7ac6a5f60340ae5041619e488223f4f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/22/2021
ms.locfileid: "112449747"
---
# <a name="scene-understanding"></a><span data-ttu-id="53a9a-104">場景理解</span><span class="sxs-lookup"><span data-stu-id="53a9a-104">Scene Understanding</span></span>

<span data-ttu-id="53a9a-105">[場景理解](/windows/mixed-reality/scene-understanding) 會傳回場景實體的語義標記法，以及其在 __HoloLens 2__ 的幾何形式 (HoloLens 第1代不支援) 。</span><span class="sxs-lookup"><span data-stu-id="53a9a-105">[Scene Understanding](/windows/mixed-reality/scene-understanding) returns a semantic representation of scene entities as well as their geometric forms on __HoloLens 2__ (HoloLens 1st Gen is not supported).</span></span>

<span data-ttu-id="53a9a-106">這項技術的一些預期使用案例如下：</span><span class="sxs-lookup"><span data-stu-id="53a9a-106">Some expected use cases of this technology are:</span></span>
* <span data-ttu-id="53a9a-107">將物件放在特定種類的最接近表面 (例如牆壁和樓層) </span><span class="sxs-lookup"><span data-stu-id="53a9a-107">Place objects on nearest surface of a certain kind (e.g. wall and floor)</span></span>
* <span data-ttu-id="53a9a-108">為平臺樣式遊戲建立導覽網格</span><span class="sxs-lookup"><span data-stu-id="53a9a-108">Construct nav-mesh for platform style games</span></span>
* <span data-ttu-id="53a9a-109">提供物理引擎易記幾何作為四邊形</span><span class="sxs-lookup"><span data-stu-id="53a9a-109">Provide physics engine friendly geometry as quads</span></span>
* <span data-ttu-id="53a9a-110">避免需要撰寫類似的演算法來加速開發</span><span class="sxs-lookup"><span data-stu-id="53a9a-110">Accelerate development by avoiding the need to write similar algorithms</span></span>

<span data-ttu-id="53a9a-111">場景理解會在 MRTK 2.6 中引進為 __實驗__ 性功能。</span><span class="sxs-lookup"><span data-stu-id="53a9a-111">Scene Understanding is introduced as an __experimental__ feature in MRTK 2.6.</span></span> <span data-ttu-id="53a9a-112">它會整合到 MRTK 中，作為名為的 [空間觀察](spatial-awareness-getting-started.md#register-observers) 者 [`WindowsSceneUnderstandingObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsSceneUnderstanding.Experimental.WindowsSceneUnderstandingObserver) 。</span><span class="sxs-lookup"><span data-stu-id="53a9a-112">It is integrated into MRTK as a [spatial observer](spatial-awareness-getting-started.md#register-observers) called [`WindowsSceneUnderstandingObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsSceneUnderstanding.Experimental.WindowsSceneUnderstandingObserver).</span></span> <span data-ttu-id="53a9a-113">場景理解適用于舊版 XR 管線和 XR SDK 管線 (從 MRTK 2.7) 和 Windows XR 外掛程式) 開始的 OpenXR (。</span><span class="sxs-lookup"><span data-stu-id="53a9a-113">Scene Understanding works both with the Legacy XR pipeline and the XR SDK pipeline (both OpenXR (starting from MRTK 2.7) and Windows XR Plugin).</span></span> <span data-ttu-id="53a9a-114">在這兩種情況下， `WindowsSceneUnderstandingObserver` 都會使用。</span><span class="sxs-lookup"><span data-stu-id="53a9a-114">In both cases the `WindowsSceneUnderstandingObserver` is used.</span></span>

> [!NOTE] 
> <span data-ttu-id="53a9a-115">不支援在遠端處理中使用場景理解。</span><span class="sxs-lookup"><span data-stu-id="53a9a-115">Using Scene Understanding in Remoting is not supported.</span></span>

## <a name="observer-overview"></a><span data-ttu-id="53a9a-116">觀察者總覽</span><span class="sxs-lookup"><span data-stu-id="53a9a-116">Observer overview</span></span>

<span data-ttu-id="53a9a-117">當系統詢問時， [`WindowsSceneUnderstandingObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsSceneUnderstanding.Experimental.WindowsSceneUnderstandingObserver) 會傳回 [SpatialAwarenessSceneObject](xref:Microsoft.MixedReality.Toolkit.Experimental.SpatialAwareness.SpatialAwarenessSceneObject) ，其中包含可讓應用程式瞭解其周圍的屬性。</span><span class="sxs-lookup"><span data-stu-id="53a9a-117">When asked, the [`WindowsSceneUnderstandingObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsSceneUnderstanding.Experimental.WindowsSceneUnderstandingObserver) will return [SpatialAwarenessSceneObject](xref:Microsoft.MixedReality.Toolkit.Experimental.SpatialAwareness.SpatialAwarenessSceneObject) with attributes useful for the application to understand its surroundings.</span></span> <span data-ttu-id="53a9a-118">觀察頻率、傳回的物件類型 (例如牆壁、floor) 和其他觀察器行為，都取決於透過設定檔的觀察者設定。</span><span class="sxs-lookup"><span data-stu-id="53a9a-118">The observation frequency, returned object type (e.g. wall, floor) and other observer behaviors are dependent on the configuration of the observer via profile.</span></span> <span data-ttu-id="53a9a-119">例如，如果需要遮蔽遮罩，則必須設定觀察者來產生四邊形。</span><span class="sxs-lookup"><span data-stu-id="53a9a-119">For instance, if the occlusion mask is desired the observer must be configured to generate quads.</span></span> <span data-ttu-id="53a9a-120">觀察到的場景可以儲存為序列化檔案，稍後可以載入以在編輯器播放模式中重新建立場景。</span><span class="sxs-lookup"><span data-stu-id="53a9a-120">The observed scene can be saved as serialized file that can be later loaded to recreate the scene in editor play mode.</span></span>

## <a name="setup"></a><span data-ttu-id="53a9a-121">設定</span><span class="sxs-lookup"><span data-stu-id="53a9a-121">Setup</span></span>

> [!IMPORTANT]
> <span data-ttu-id="53a9a-122">只有 HoloLens 2 和 Unity 2019.4 和更新版本才支援場景理解。</span><span class="sxs-lookup"><span data-stu-id="53a9a-122">Scene Understanding is only supported on HoloLens 2 and Unity 2019.4 and higher.</span></span>

1. <span data-ttu-id="53a9a-123">確定平臺已在組建設定中設定為 UWP。</span><span class="sxs-lookup"><span data-stu-id="53a9a-123">Ensure the platform is set to UWP in build settings.</span></span>
1. <span data-ttu-id="53a9a-124">透過 [混合現實功能工具](https://aka.ms/MRFeatureTool)取得場景理解套件。</span><span class="sxs-lookup"><span data-stu-id="53a9a-124">Acquire the Scene Understanding package via [Mixed Reality Feature Tool](https://aka.ms/MRFeatureTool).</span></span>

## <a name="using-scene-understanding"></a><span data-ttu-id="53a9a-125">使用場景理解</span><span class="sxs-lookup"><span data-stu-id="53a9a-125">Using Scene Understanding</span></span>

<span data-ttu-id="53a9a-126">開始進行場景理解最快的方式是查看範例場景。</span><span class="sxs-lookup"><span data-stu-id="53a9a-126">The quickest way to get started with Scene Understanding is to check out the sample scene.</span></span>

### <a name="scene-understanding-sample-scene"></a><span data-ttu-id="53a9a-127">場景理解範例場景</span><span class="sxs-lookup"><span data-stu-id="53a9a-127">Scene Understanding sample scene</span></span>

<span data-ttu-id="53a9a-128">在 Unity 中，使用 Project Explorer 開啟場景檔案 `Examples/Experimental/SceneUnderstanding/Scenes/SceneUnderstandingExample.unity` ，然後按下 [播放]！</span><span class="sxs-lookup"><span data-stu-id="53a9a-128">In Unity, use the Project Explorer to open the scene file in `Examples/Experimental/SceneUnderstanding/Scenes/SceneUnderstandingExample.unity` and press play!</span></span>

::: moniker range="< mrtkunity-2021-05"
> [!IMPORTANT]
> <span data-ttu-id="53a9a-129">僅適用于 MRTK 2.6.0-使用 Mixed Reality 功能工具或透過 UPM 匯入時，請先匯入示範-SpatialAwareness 範例，再匯入實驗性 SceneUnderstanding 範例，因為相依性問題。</span><span class="sxs-lookup"><span data-stu-id="53a9a-129">Only applies to MRTK 2.6.0 - When using the Mixed Reality Feature Tool or otherwise importing via UPM, please import the Demos - SpatialAwareness sample before importing the Experimental - SceneUnderstanding sample due to a dependency issue.</span></span> <span data-ttu-id="53a9a-130">如需詳細資訊，請參閱 [此 GitHub 問題](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9431) 。</span><span class="sxs-lookup"><span data-stu-id="53a9a-130">Please see [this GitHub issue](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9431) for more information.</span></span>

::: moniker-end
<span data-ttu-id="53a9a-131">場景會示範下列各項：</span><span class="sxs-lookup"><span data-stu-id="53a9a-131">The scene demonstrates the following:</span></span>

* <span data-ttu-id="53a9a-132">在應用程式 UI 中使用觀察到的場景物件來設定觀察者的視覺效果</span><span class="sxs-lookup"><span data-stu-id="53a9a-132">Visualization of observed Scene Objects with in application UI for configuring the observer</span></span>
* <span data-ttu-id="53a9a-133">示範 `DemoSceneUnderstandingController` 如何變更觀察者設定以及接聽相關事件的範例腳本</span><span class="sxs-lookup"><span data-stu-id="53a9a-133">Example `DemoSceneUnderstandingController` script that shows how to change observer settings and listen to relevant events</span></span>
* <span data-ttu-id="53a9a-134">將場景資料儲存至裝置以進行離線開發</span><span class="sxs-lookup"><span data-stu-id="53a9a-134">Saving scene data to device for offline development</span></span>
* <span data-ttu-id="53a9a-135">將先前儲存的場景資料載入 ( 的位元組檔案) 以支援編輯器開發工作流程</span><span class="sxs-lookup"><span data-stu-id="53a9a-135">Loading previously saved scene data (.bytes files) to support in-editor development workflow</span></span>

> [!IMPORTANT]
> <span data-ttu-id="53a9a-136">根據預設， `ShouldLoadFromFile` 觀察者的屬性會設定為 false。</span><span class="sxs-lookup"><span data-stu-id="53a9a-136">By default the `ShouldLoadFromFile` property of the observer is set to false.</span></span> <span data-ttu-id="53a9a-137">若要查看序列化範例房間的視覺效果，請參閱下面的「設定 [觀察者服務](#configuring-the-observer-service) 」一節，並在編輯器中將屬性設為 true。</span><span class="sxs-lookup"><span data-stu-id="53a9a-137">In order to see the visualization of a serialized sample room, please refer to the [configuring observer service](#configuring-the-observer-service) section below and set the property to true in the editor.</span></span>
::: moniker range="< mrtkunity-2021-05"

> [!NOTE] 
> <span data-ttu-id="53a9a-138">範例場景是以舊版 XR 管線為基礎。</span><span class="sxs-lookup"><span data-stu-id="53a9a-138">The sample scene is based on the Legacy XR pipeline.</span></span> <span data-ttu-id="53a9a-139">如果您使用 XR SDK 管線，則應該據以修改設定檔。</span><span class="sxs-lookup"><span data-stu-id="53a9a-139">If you are using the XR SDK pipeline you should modify the profiles accordingly.</span></span> <span data-ttu-id="53a9a-140">提供的場景瞭解空間感知系統設定檔 (`DemoSceneUnderstandingSystemProfile`) 和場景瞭解觀察者設定檔 (`DefaultSceneUnderstandingObserverProfile` 和 `DemoSceneUnderstandingObserverProfile`) 適用于這兩個管線。</span><span class="sxs-lookup"><span data-stu-id="53a9a-140">The provided Scene Understanding Spatial Awareness System profile (`DemoSceneUnderstandingSystemProfile`) and the Scene Understanding Observer profiles (`DefaultSceneUnderstandingObserverProfile` and `DemoSceneUnderstandingObserverProfile`) works for both pipelines.</span></span>
::: moniker-end
::: moniker range="= mrtkunity-2021-05"

> [!NOTE] 
> <span data-ttu-id="53a9a-141">範例場景會 `There is no active AsyncCoroutineRunner when an action is posted.` 在特定情況下，根據初始化/執行緒執行順序來記錄警告。</span><span class="sxs-lookup"><span data-stu-id="53a9a-141">The sample scene logs a `There is no active AsyncCoroutineRunner when an action is posted.` warning under certain circumstance due to the initialization/thread execution order.</span></span> <span data-ttu-id="53a9a-142">如果您可以確認 `AsyncCoroutineRunner` 元件已附加至「示範控制器」 GameObject，且元件/GameObject 在場景中保持啟用/作用中 (預設案例) ，則可以放心忽略該警告。</span><span class="sxs-lookup"><span data-stu-id="53a9a-142">If you can confirm the `AsyncCoroutineRunner` component is attached to the "Demo Controller" GameObject and the component/GameObject stay enabled/active in the scene (the default case), the warning can be safely ignored.</span></span> <span data-ttu-id="53a9a-143">**不過，在建立具有場景理解的新場景時，請務必在根目錄建立空白的 GameObject，並將 `AsyncCoroutineRunner` 腳本附加至該場景，否則場景理解可能無法正常運作。**</span><span class="sxs-lookup"><span data-stu-id="53a9a-143">**However, when creating a new scene with Scene Understanding please make sure to create an empty GameObject at root and attach the `AsyncCoroutineRunner` script to it, otherwise Scene Understanding may not function properly.**</span></span>
::: moniker-end

#### <a name="configuring-the-observer-service"></a><span data-ttu-id="53a9a-144">設定觀察者服務</span><span class="sxs-lookup"><span data-stu-id="53a9a-144">Configuring the observer service</span></span>

<span data-ttu-id="53a9a-145">選取 [MixedRealityToolkit] 遊戲物件並檢查偵測器。</span><span class="sxs-lookup"><span data-stu-id="53a9a-145">Select the 'MixedRealityToolkit' game object and check the inspector.</span></span>

![場景瞭解階層中的位置](../images/spatial-awareness/MRTKHierarchy.png)

![偵測器中的 MRTK 位置](../images/spatial-awareness/MRTKLocation.png)

<span data-ttu-id="53a9a-148">這些選項可讓其中一個設定 `WindowsSceneUnderstandingObserver` 。</span><span class="sxs-lookup"><span data-stu-id="53a9a-148">These options will allow one to configure the `WindowsSceneUnderstandingObserver`.</span></span>

### <a name="example-script"></a><span data-ttu-id="53a9a-149">範例指令碼</span><span class="sxs-lookup"><span data-stu-id="53a9a-149">Example script</span></span>

<span data-ttu-id="53a9a-150">範例腳本 _DemoSceneUnderstandingController_ 會示範使用場景理解服務的主要概念。</span><span class="sxs-lookup"><span data-stu-id="53a9a-150">The example script _DemoSceneUnderstandingController.cs_ demonstrates the major concepts in working with the Scene Understanding service.</span></span>

* <span data-ttu-id="53a9a-151">訂閱場景理解事件</span><span class="sxs-lookup"><span data-stu-id="53a9a-151">Subscribing to Scene Understanding events</span></span>
* <span data-ttu-id="53a9a-152">處理場景理解事件</span><span class="sxs-lookup"><span data-stu-id="53a9a-152">Handling Scene Understanding events</span></span>
* <span data-ttu-id="53a9a-153">`WindowsSceneUnderstandingObserver`在執行時間設定</span><span class="sxs-lookup"><span data-stu-id="53a9a-153">Configuring the `WindowsSceneUnderstandingObserver` at runtime</span></span>

<span data-ttu-id="53a9a-154">場景中面板上的切換會藉由呼叫此範例腳本的公用函式，來變更場景理解觀察者的行為。</span><span class="sxs-lookup"><span data-stu-id="53a9a-154">The toggles on the panel in the scene change the behavior of scene understanding observer by calling public functions of this sample script.</span></span>

<span data-ttu-id="53a9a-155">開啟具現 *化 Prefabs*，將會示範如何建立大小適當的物件，使其符合所有 [SpatialAwarenessSceneObject](xref:Microsoft.MixedReality.Toolkit.Experimental.SpatialAwareness.SpatialAwarenessSceneObject)的大小，並整齊地在父物件底下收集。</span><span class="sxs-lookup"><span data-stu-id="53a9a-155">Turning on *Instantiate Prefabs*, will demonstrate creating objects that size to fit themselves to all [SpatialAwarenessSceneObject](xref:Microsoft.MixedReality.Toolkit.Experimental.SpatialAwareness.SpatialAwarenessSceneObject), gathered neatly under a parent object.</span></span>

![示範控制器選項](../images/spatial-awareness/Controller.png)

### <a name="built-app-notes"></a><span data-ttu-id="53a9a-157">建立的應用程式附注</span><span class="sxs-lookup"><span data-stu-id="53a9a-157">Built app notes</span></span>

<span data-ttu-id="53a9a-158">以標準方式建立並部署至 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="53a9a-158">Build and deploy to HoloLens in the standard way.</span></span> <span data-ttu-id="53a9a-159">執行之後，您應該會有一些按鈕可以與功能一起播放。</span><span class="sxs-lookup"><span data-stu-id="53a9a-159">Once running, a number of buttons should appear to play with the features.</span></span>

<span data-ttu-id="53a9a-160">請注意，有一些 pit 正在對觀察者進行查詢。</span><span class="sxs-lookup"><span data-stu-id="53a9a-160">Note, their are some pit falls in making queries to the observer.</span></span> <span data-ttu-id="53a9a-161">提取要求的設定不正確會導致您的事件裝載中未包含預期的資料。</span><span class="sxs-lookup"><span data-stu-id="53a9a-161">Misconfiguration of a fetch request result in your event payload not containing the expected data.</span></span> <span data-ttu-id="53a9a-162">例如，如果其中一個不要求四邊形，則不會出現任何遮蔽 mask 紋理。</span><span class="sxs-lookup"><span data-stu-id="53a9a-162">For example, if one doesn't request quads, then no occlusion mask textures will be present.</span></span> <span data-ttu-id="53a9a-163">如同明智的，如果觀察者未設定為要求網格，則不會出現任何世界網格。</span><span class="sxs-lookup"><span data-stu-id="53a9a-163">Like wise, no world mesh will appear if the observer is not configured to request meshes.</span></span> <span data-ttu-id="53a9a-164">`DemoSceneUnderstandingController`腳本會處理其中一些相依性，但並非全部。</span><span class="sxs-lookup"><span data-stu-id="53a9a-164">The `DemoSceneUnderstandingController` script takes care of some of these dependencies, but not all.</span></span>

<span data-ttu-id="53a9a-165">您可以透過 [裝置入口網站](/windows/mixed-reality/using-the-windows-device-portal) 存取已儲存的場景檔案 `User Folders/LocalAppData/[APP_NAME]/LocalState/PREFIX_yyyyMMdd_hhmmss.bytes` 。</span><span class="sxs-lookup"><span data-stu-id="53a9a-165">Saved scene files can be accessed through the [device portal](/windows/mixed-reality/using-the-windows-device-portal) at `User Folders/LocalAppData/[APP_NAME]/LocalState/PREFIX_yyyyMMdd_hhmmss.bytes`.</span></span> <span data-ttu-id="53a9a-166">這些場景檔案可以在編輯器中使用，方法是在偵測器中找到的觀察者設定檔中指定它們。</span><span class="sxs-lookup"><span data-stu-id="53a9a-166">These scene files can be used in editor by specifying them in the observer profile found in the inspector.</span></span>

![位元組檔案裝置入口網站位置](../images/spatial-awareness/BytesInDevicePortal.png)

![觀察者中的序列化場景位元組](../images/spatial-awareness/BytesLocationInObserver.png)

## <a name="see-also"></a><span data-ttu-id="53a9a-169">另請參閱</span><span class="sxs-lookup"><span data-stu-id="53a9a-169">See Also</span></span>

* [<span data-ttu-id="53a9a-170">場景理解總覽</span><span class="sxs-lookup"><span data-stu-id="53a9a-170">Scene Understanding Overview</span></span>](/windows/mixed-reality/scene-understanding)
* [<span data-ttu-id="53a9a-171">場景理解 SDK 總覽</span><span class="sxs-lookup"><span data-stu-id="53a9a-171">Scene Understanding SDK Overview</span></span>](/windows/mixed-reality/scene-understanding-sdk)