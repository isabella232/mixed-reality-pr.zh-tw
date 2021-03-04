---
title: SceneUnderstanding
description: 描述 MRTK 中的場景理解
author: MaxWang-MS
ms.author: wangmax
ms.date: 03/02/2021
ms.localizationpriority: high
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、場景理解
ms.openlocfilehash: c8f82de2418b199220261fbae034acb3e5640362
ms.sourcegitcommit: 7a8fa3257a13635ddad77d963e49440f62c19774
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2021
ms.locfileid: "101884049"
---
# <a name="scene-understanding"></a><span data-ttu-id="40528-104">場景理解</span><span class="sxs-lookup"><span data-stu-id="40528-104">Scene Understanding</span></span>

<span data-ttu-id="40528-105">[場景理解](https://docs.microsoft.com/windows/mixed-reality/scene-understanding) 會傳回場景實體的語義標記法，以及其在 __hololens 2__ 上的幾何形式 (hololens 第1代不支援) 。</span><span class="sxs-lookup"><span data-stu-id="40528-105">[Scene Understanding](https://docs.microsoft.com/windows/mixed-reality/scene-understanding) returns a semantic representation of scene entities as well as their geometric forms on __HoloLens 2__ (HoloLens 1st Gen is not supported).</span></span>

<span data-ttu-id="40528-106">這項技術的一些預期使用案例如下：</span><span class="sxs-lookup"><span data-stu-id="40528-106">Some expected use cases of this technology are:</span></span>
* <span data-ttu-id="40528-107">將物件放在特定種類的最接近表面 (例如牆壁和樓層) </span><span class="sxs-lookup"><span data-stu-id="40528-107">Place objects on nearest surface of a certain kind (e.g. wall and floor)</span></span>
* <span data-ttu-id="40528-108">為平臺樣式遊戲建立導覽網格</span><span class="sxs-lookup"><span data-stu-id="40528-108">Construct nav-mesh for platform style games</span></span>
* <span data-ttu-id="40528-109">提供物理引擎易記幾何作為四邊形</span><span class="sxs-lookup"><span data-stu-id="40528-109">Provide physics engine friendly geometry as quads</span></span>
* <span data-ttu-id="40528-110">避免需要撰寫類似的演算法來加速開發</span><span class="sxs-lookup"><span data-stu-id="40528-110">Accelerate development by avoiding the need to write similar algorithms</span></span>

<span data-ttu-id="40528-111">從 MRTK 2.6 開始，場景理解會以 __實驗__ 性功能的形式提供。</span><span class="sxs-lookup"><span data-stu-id="40528-111">Scene Understanding is available as an __experimental__ feature starting from MRTK 2.6.</span></span> <span data-ttu-id="40528-112">它會整合到 MRTK 中，作為名為的 [空間觀察](spatial-awareness-getting-started.md#register-observers) 者 [`WindowsSceneUnderstandingObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsSceneUnderstanding.Experimental.WindowsSceneUnderstandingObserver) 。</span><span class="sxs-lookup"><span data-stu-id="40528-112">It is integrated into MRTK as a [spatial observer](spatial-awareness-getting-started.md#register-observers) called [`WindowsSceneUnderstandingObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsSceneUnderstanding.Experimental.WindowsSceneUnderstandingObserver).</span></span> <span data-ttu-id="40528-113">場景理解適用于舊版 XR 管線和 XR SDK 管線。</span><span class="sxs-lookup"><span data-stu-id="40528-113">Scene Understanding works both with the Legacy XR pipeline and the XR SDK pipeline.</span></span> <span data-ttu-id="40528-114">在這兩種情況下， `WindowsSceneUnderstandingObserver` 都會使用。</span><span class="sxs-lookup"><span data-stu-id="40528-114">In both cases the `WindowsSceneUnderstandingObserver` is used.</span></span>

## <a name="observer-overview"></a><span data-ttu-id="40528-115">觀察者總覽</span><span class="sxs-lookup"><span data-stu-id="40528-115">Observer overview</span></span>

<span data-ttu-id="40528-116">當系統詢問時， [`WindowsSceneUnderstandingObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsSceneUnderstanding.Experimental.WindowsSceneUnderstandingObserver) 會傳回 [SpatialAwarenessSceneObject](xref:Microsoft.MixedReality.Toolkit.Experimental.SpatialAwareness.SpatialAwarenessSceneObject) ，其中包含可讓應用程式瞭解其周圍的屬性。</span><span class="sxs-lookup"><span data-stu-id="40528-116">When asked, the [`WindowsSceneUnderstandingObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsSceneUnderstanding.Experimental.WindowsSceneUnderstandingObserver) will return [SpatialAwarenessSceneObject](xref:Microsoft.MixedReality.Toolkit.Experimental.SpatialAwareness.SpatialAwarenessSceneObject) with attributes useful for the application to understand its surroundings.</span></span> <span data-ttu-id="40528-117">觀察頻率、傳回的物件類型 (例如牆壁、floor) 和其他觀察器行為，都取決於透過設定檔的觀察者設定。</span><span class="sxs-lookup"><span data-stu-id="40528-117">The observation frequency, returned object type (e.g. wall, floor) and other observer behaviors are dependent on the configuration of the observer via profile.</span></span> <span data-ttu-id="40528-118">例如，如果需要遮蔽遮罩，則必須設定觀察者來產生四邊形。</span><span class="sxs-lookup"><span data-stu-id="40528-118">For instance, if the occlusion mask is desired the observer must be configured to generate quads.</span></span> <span data-ttu-id="40528-119">觀察到的場景可以儲存為序列化檔案，稍後可以載入以在編輯器播放模式中重新建立場景。</span><span class="sxs-lookup"><span data-stu-id="40528-119">The observed scene can be saved as serialized file that can be later loaded to recreate the scene in editor play mode.</span></span>

## <a name="setup"></a><span data-ttu-id="40528-120">安裝程式</span><span class="sxs-lookup"><span data-stu-id="40528-120">Setup</span></span>

1. <span data-ttu-id="40528-121">確定平臺已在組建設定中設定為 UWP。</span><span class="sxs-lookup"><span data-stu-id="40528-121">Ensure the platform is set to UWP in build settings.</span></span>
1. <span data-ttu-id="40528-122">透過 [混合現實功能工具](https://aka.ms/MRFeatureTool)取得場景理解套件。</span><span class="sxs-lookup"><span data-stu-id="40528-122">Acquire the Scene Understanding package via [Mixed Reality Feature Tool](https://aka.ms/MRFeatureTool).</span></span>

## <a name="using-scene-understanding"></a><span data-ttu-id="40528-123">使用場景理解</span><span class="sxs-lookup"><span data-stu-id="40528-123">Using Scene Understanding</span></span>

<span data-ttu-id="40528-124">開始進行場景理解最快的方式是查看範例場景。</span><span class="sxs-lookup"><span data-stu-id="40528-124">The quickest way to get started with Scene Understanding is to check out the sample scene.</span></span>

### <a name="scene-understanding-sample-scene"></a><span data-ttu-id="40528-125">場景理解範例場景</span><span class="sxs-lookup"><span data-stu-id="40528-125">Scene Understanding sample scene</span></span>

<span data-ttu-id="40528-126">在 Unity 中，使用 Project Explorer 開啟場景檔案 `Examples/Experimental/SceneUnderstanding/Scenes/SceneUnderstandingExample.unity` ，然後按下 [播放]！</span><span class="sxs-lookup"><span data-stu-id="40528-126">In Unity, use the Project Explorer to open the scene file in `Examples/Experimental/SceneUnderstanding/Scenes/SceneUnderstandingExample.unity` and press play!</span></span>

<span data-ttu-id="40528-127">場景會示範下列各項：</span><span class="sxs-lookup"><span data-stu-id="40528-127">The scene demonstrates the following:</span></span>

* <span data-ttu-id="40528-128">在應用程式 UI 中使用觀察到的場景物件來設定觀察者的視覺效果</span><span class="sxs-lookup"><span data-stu-id="40528-128">Visualization of observed Scene Objects with in application UI for configuring the observer</span></span>
* <span data-ttu-id="40528-129">示範 `DemoSceneUnderstandingController` 如何變更觀察者設定以及接聽相關事件的範例腳本</span><span class="sxs-lookup"><span data-stu-id="40528-129">Example `DemoSceneUnderstandingController` script that shows how to change observer settings and listen to relevant events</span></span>
* <span data-ttu-id="40528-130">將場景資料儲存至裝置以進行離線開發</span><span class="sxs-lookup"><span data-stu-id="40528-130">Saving scene data to device for offline development</span></span>
* <span data-ttu-id="40528-131">將先前儲存的場景資料載入 ( 的位元組檔案) 以支援編輯器開發工作流程</span><span class="sxs-lookup"><span data-stu-id="40528-131">Loading previously saved scene data (.bytes files) to support in-editor development workflow</span></span>

> [!NOTE] 
> <span data-ttu-id="40528-132">範例場景是以舊版 XR 管線為基礎。</span><span class="sxs-lookup"><span data-stu-id="40528-132">The sample scene is based on the Legacy XR pipeline.</span></span> <span data-ttu-id="40528-133">如果您使用 XR SDK 管線，則應該據以修改設定檔。</span><span class="sxs-lookup"><span data-stu-id="40528-133">If you are using the XR SDK pipeline you should modify the profiles accordingly.</span></span> <span data-ttu-id="40528-134">提供的場景瞭解空間感知系統設定檔 (`DemoSceneUnderstandingSystemProfile`) 和場景瞭解觀察者設定檔 (`DefaultSceneUnderstandingObserverProfile` 和 `DemoSceneUnderstandingObserverProfile`) 適用于這兩個管線。</span><span class="sxs-lookup"><span data-stu-id="40528-134">The provided Scene Understanding Spatial Awareness System profile (`DemoSceneUnderstandingSystemProfile`) and the Scene Understanding Observer profiles (`DefaultSceneUnderstandingObserverProfile` and `DemoSceneUnderstandingObserverProfile`) works for both pipelines.</span></span>

#### <a name="configuring-the-observer-service"></a><span data-ttu-id="40528-135">設定觀察者服務</span><span class="sxs-lookup"><span data-stu-id="40528-135">Configuring the observer service</span></span>

<span data-ttu-id="40528-136">選取 [MixedRealityToolkit] 遊戲物件並檢查偵測器。</span><span class="sxs-lookup"><span data-stu-id="40528-136">Select the 'MixedRealityToolkit' game object and check the inspector.</span></span>

![場景瞭解階層中的位置](../images/spatial-awareness/MRTKHierarchy.png)

![偵測器中的 mrkt 位置](../images/spatial-awareness/MRTKLocation.png)

<span data-ttu-id="40528-139">這些選項可讓其中一個設定 `WindowsSceneUnderstandingObserver` 。</span><span class="sxs-lookup"><span data-stu-id="40528-139">These options will allow one to configure the `WindowsSceneUnderstandingObserver`.</span></span>

### <a name="example-script"></a><span data-ttu-id="40528-140">範例指令碼</span><span class="sxs-lookup"><span data-stu-id="40528-140">Example script</span></span>

<span data-ttu-id="40528-141">範例腳本 _DemoSceneUnderstandingController.cs_ 示範使用場景理解服務的主要概念。</span><span class="sxs-lookup"><span data-stu-id="40528-141">The example script _DemoSceneUnderstandingController.cs_ demonstrates the major concepts in working with the Scene Understanding service.</span></span>

* <span data-ttu-id="40528-142">訂閱場景理解事件</span><span class="sxs-lookup"><span data-stu-id="40528-142">Subscribing to Scene Understanding events</span></span>
* <span data-ttu-id="40528-143">處理場景理解事件</span><span class="sxs-lookup"><span data-stu-id="40528-143">Handling Scene Understanding events</span></span>
* <span data-ttu-id="40528-144">`WindowsSceneUnderstandingObserver`在執行時間設定</span><span class="sxs-lookup"><span data-stu-id="40528-144">Configuring the `WindowsSceneUnderstandingObserver` at runtime</span></span>

<span data-ttu-id="40528-145">場景中面板上的切換會藉由呼叫此範例腳本的公用函式，來變更場景理解觀察者的行為。</span><span class="sxs-lookup"><span data-stu-id="40528-145">The toggles on the panel in the scene change the behavior of scene understanding observer by calling public functions of this sample script.</span></span>

<span data-ttu-id="40528-146">開啟具現 *化 Prefabs*，將會示範如何建立大小適當的物件，使其符合所有 [SpatialAwarenessSceneObject](xref:Microsoft.MixedReality.Toolkit.Experimental.SpatialAwareness.SpatialAwarenessSceneObject)的大小，並整齊地在父物件底下收集。</span><span class="sxs-lookup"><span data-stu-id="40528-146">Turning on *Instantiate Prefabs*, will demonstrate creating objects that size to fit themselves to all [SpatialAwarenessSceneObject](xref:Microsoft.MixedReality.Toolkit.Experimental.SpatialAwareness.SpatialAwarenessSceneObject), gathered neatly under a parent object.</span></span>

![示範控制器選項](../images/spatial-awareness/Controller.png)

### <a name="built-app-notes"></a><span data-ttu-id="40528-148">建立的應用程式附注</span><span class="sxs-lookup"><span data-stu-id="40528-148">Built app notes</span></span>

<span data-ttu-id="40528-149">以標準方式建立並部署至 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="40528-149">Build and deploy to HoloLens in the standard way.</span></span> <span data-ttu-id="40528-150">執行之後，您應該會有一些按鈕可以與功能一起播放。</span><span class="sxs-lookup"><span data-stu-id="40528-150">Once running, a number of buttons should appear to play with the features.</span></span>

<span data-ttu-id="40528-151">請注意，有一些 pit 正在對觀察者進行查詢。</span><span class="sxs-lookup"><span data-stu-id="40528-151">Note, their are some pit falls in making queries to the observer.</span></span> <span data-ttu-id="40528-152">提取要求的設定不正確會導致您的事件裝載中未包含預期的資料。</span><span class="sxs-lookup"><span data-stu-id="40528-152">Misconfiguration of a fetch request result in your event payload not containing the expected data.</span></span> <span data-ttu-id="40528-153">例如，如果一個 dosen't 要求四邊形，則不會出現任何遮蔽 mask 紋理。</span><span class="sxs-lookup"><span data-stu-id="40528-153">For example, if one dosen't request quads, then no occlusion mask textures will be present.</span></span> <span data-ttu-id="40528-154">如同明智的，如果觀察者未設定為要求網格，則不會出現任何世界網格。</span><span class="sxs-lookup"><span data-stu-id="40528-154">Like wise, no world mesh will appear if the observer is not configured to request meshes.</span></span> <span data-ttu-id="40528-155">`DemoSceneUnderstandingController`腳本會處理其中一些相依性，但並非全部。</span><span class="sxs-lookup"><span data-stu-id="40528-155">The `DemoSceneUnderstandingController` script takes care of some of these dependencies, but not all.</span></span>

<span data-ttu-id="40528-156">您可以透過 [裝置入口網站](https://docs.microsoft.com/windows/mixed-reality/using-the-windows-device-portal) 存取已儲存的場景檔案 `User Folders/LocalAppData/[APP_NAME]/LocalState/PREFIX_yyyyMMdd_hhmmss.bytes` 。</span><span class="sxs-lookup"><span data-stu-id="40528-156">Saved scene files can be accessed through the [device portal](https://docs.microsoft.com/windows/mixed-reality/using-the-windows-device-portal) at `User Folders/LocalAppData/[APP_NAME]/LocalState/PREFIX_yyyyMMdd_hhmmss.bytes`.</span></span> <span data-ttu-id="40528-157">這些場景檔案可以在編輯器中使用，方法是在偵測器中找到的觀察者設定檔中指定它們。</span><span class="sxs-lookup"><span data-stu-id="40528-157">These scene files can be used in editor by specifying them in the observer profile found in the inspector.</span></span>

![裝置入口網站位置位元組檔案](../images/spatial-awareness/BytesInDevicePortal.png)

![觀察者中的序列化場景位元組](../images/spatial-awareness/BytesLocationInObserver.png)

## <a name="see-also"></a><span data-ttu-id="40528-160">另請參閱</span><span class="sxs-lookup"><span data-stu-id="40528-160">See Also</span></span>

* https://docs.microsoft.com/windows/mixed-reality/scene-understanding
* https://docs.microsoft.com/windows/mixed-reality/scene-understanding-sdk
