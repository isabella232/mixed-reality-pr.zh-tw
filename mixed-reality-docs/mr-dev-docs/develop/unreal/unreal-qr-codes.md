---
title: Unreal 中的 QR 代碼
description: 在 Unreal 中使用 QR 代碼的指南
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 混合實境, 開發, 功能, 文件, 指南, holograms, qr 代碼
ms.openlocfilehash: 0f0507e2f726830cef27c190083363b3607379ee
ms.sourcegitcommit: 8e91ff47ef70e80a41137f80aa1093e711d27bf7
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2020
ms.locfileid: "91957818"
---
# <a name="qr-codes-in-unreal"></a><span data-ttu-id="5cdf8-104">Unreal 中的 QR 代碼</span><span class="sxs-lookup"><span data-stu-id="5cdf8-104">QR codes in Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="5cdf8-105">概觀</span><span class="sxs-lookup"><span data-stu-id="5cdf8-105">Overview</span></span>

<span data-ttu-id="5cdf8-106">HoloLens 2 可以使用網路攝影機查看世界空間中的 QR 代碼，這會在每個代碼的真實世界位置中使用座標系統將其呈現為全息投影。</span><span class="sxs-lookup"><span data-stu-id="5cdf8-106">The HoloLens 2 can see QR codes in world space using the webcam, which renders them as holograms using a coordinate system at each code's real-world position.</span></span>  <span data-ttu-id="5cdf8-107">除了單一 QR 代碼外，HoloLens 2 還可以在相同位置的多個裝置上呈現全像投影，以建立共用體驗。</span><span class="sxs-lookup"><span data-stu-id="5cdf8-107">In addition to single QR codes, HoloLens 2 can also render holograms in the same location on multiple devices to create a shared experience.</span></span> <span data-ttu-id="5cdf8-108">確定您遵循將 QR 代碼新增至應用程式的最佳作法：</span><span class="sxs-lookup"><span data-stu-id="5cdf8-108">Make sure you're following the best practices for adding QR codes to your applications:</span></span>

- <span data-ttu-id="5cdf8-109">寧靜區域</span><span class="sxs-lookup"><span data-stu-id="5cdf8-109">Quiet zones</span></span>
- <span data-ttu-id="5cdf8-110">光源和底圖</span><span class="sxs-lookup"><span data-stu-id="5cdf8-110">Lighting and backdrop</span></span>
- <span data-ttu-id="5cdf8-111">大小、距離和角度位置</span><span class="sxs-lookup"><span data-stu-id="5cdf8-111">Size, distance, and angular position</span></span>

<span data-ttu-id="5cdf8-112">將 QR 代碼放在您的應用程式時，請特別注意[環境考量](../../environment-considerations-for-hololens.md)。</span><span class="sxs-lookup"><span data-stu-id="5cdf8-112">Pay special attention to the [environment considerations](../../environment-considerations-for-hololens.md) when QR codes are being placed in your app.</span></span> <span data-ttu-id="5cdf8-113">您可以在其中每一個主題上找到詳細資訊，以及在主要 [QR 代碼追蹤](../platform-capabilities-and-apis/qr-code-tracking.md)文件中找到如何下載所需 NuGet 套件的指示。</span><span class="sxs-lookup"><span data-stu-id="5cdf8-113">You can find more information on each of these topics and instructions on how to download the required NuGet package in the main [QR code tracking](../platform-capabilities-and-apis/qr-code-tracking.md) document.</span></span>

## <a name="enabling-qr-detection"></a><span data-ttu-id="5cdf8-114">啟用 QR 偵測</span><span class="sxs-lookup"><span data-stu-id="5cdf8-114">Enabling QR detection</span></span>
<span data-ttu-id="5cdf8-115">因為 HoloLens 2 需要使用網路攝影機來查看 QR 代碼，所以您必須在專案設定中將其啟用：</span><span class="sxs-lookup"><span data-stu-id="5cdf8-115">Since the HoloLens 2 needs to use the webcam to see QR codes, you'll need to enable it in the project settings:</span></span>
- <span data-ttu-id="5cdf8-116">開啟 [編輯] > [專案設定]捲動至 [平台] 區段，然後按一下 [HoloLens]。</span><span class="sxs-lookup"><span data-stu-id="5cdf8-116">Open **Edit > Project Settings**, scroll to the **Platforms** section and click **HoloLens**.</span></span>
    + <span data-ttu-id="5cdf8-117">展開 [功能] 區段，並勾選 [網路攝影機]。</span><span class="sxs-lookup"><span data-stu-id="5cdf8-117">Expand the **Capabilities** section and check **Webcam**.</span></span>  

<span data-ttu-id="5cdf8-118">您也必須[新增 ARSessionConfig 資產](https://docs.microsoft.com/windows/mixed-reality/unreal-uxt-ch3#adding-the-session-asset)，來加入 QR 代碼追蹤。</span><span class="sxs-lookup"><span data-stu-id="5cdf8-118">You'll also need to opt into QR code tracking by [adding an ARSessionConfig asset](https://docs.microsoft.com/windows/mixed-reality/unreal-uxt-ch3#adding-the-session-asset).</span></span>

<span data-ttu-id="5cdf8-119">在使用之前，您應藉由呼叫 `UHoloLensARFunctionLibrary::StartCameraCapture()`來手動啟用追蹤。</span><span class="sxs-lookup"><span data-stu-id="5cdf8-119">Right before the usage, you should manually enable the tracking by calling `UHoloLensARFunctionLibrary::StartCameraCapture()`.</span></span> <span data-ttu-id="5cdf8-120">在結束 QR 代碼追蹤之後，您應經由 `UHoloLensARFunctionLibrary::StopCameraCapture()` 將其停用，以儲存裝置資源。</span><span class="sxs-lookup"><span data-stu-id="5cdf8-120">After ending the QR code tracking, you should disable it by `UHoloLensARFunctionLibrary::StopCameraCapture()` to save the device resources.</span></span>

## <a name="setting-up-a-tracked-image"></a><span data-ttu-id="5cdf8-121">設定追蹤的影像</span><span class="sxs-lookup"><span data-stu-id="5cdf8-121">Setting up a tracked image</span></span>

<span data-ttu-id="5cdf8-122">QR 代碼會透過 Unreal 的 AR 追蹤幾何系統呈現為追蹤的影像。</span><span class="sxs-lookup"><span data-stu-id="5cdf8-122">QR codes are surfaced through Unreal’s AR tracked geometry system as a tracked image.</span></span> <span data-ttu-id="5cdf8-123">若要讓此作業運作，您必須：</span><span class="sxs-lookup"><span data-stu-id="5cdf8-123">To get this working, you'll need to:</span></span>
1. <span data-ttu-id="5cdf8-124">建立藍圖並新增 **ARTrackableNotify** 元件。</span><span class="sxs-lookup"><span data-stu-id="5cdf8-124">Create a Blueprint and add an **ARTrackableNotify** component.</span></span>

![QR AR 可追蹤通知](images/unreal-spatialmapping-artrackablenotify.PNG)

2. <span data-ttu-id="5cdf8-126">選取 [ARTrackableNotify]，然後展開 [詳細資料] 面板中的 [事件] 區段。</span><span class="sxs-lookup"><span data-stu-id="5cdf8-126">Select **ARTrackableNotify** and expand the **Events** section in the **Details** panel.</span></span>

![QR 事件](images/unreal-spatialmapping-events.PNG)

3. <span data-ttu-id="5cdf8-128">按一下 [On Add Tracked Geometry] 旁邊的 **+** ，將節點新增至事件圖形。</span><span class="sxs-lookup"><span data-stu-id="5cdf8-128">Click **+** next to **On Add Tracked Geometry** to add the node to the Event Graph.</span></span>
    - <span data-ttu-id="5cdf8-129">您可以在 [UARTrackableNotify](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackableNotifyComponent/index.html) 元件 API 中找到完整的事件清單。</span><span class="sxs-lookup"><span data-stu-id="5cdf8-129">You can find the full list of events in the [UARTrackableNotify](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackableNotifyComponent/index.html) component API.</span></span>

![將節點新增至 On Add Tracked Geometry](images/unreal-qr-codes-tracked-geometry.png)

## <a name="using-a-tracked-image"></a><span data-ttu-id="5cdf8-131">使用追蹤的影像</span><span class="sxs-lookup"><span data-stu-id="5cdf8-131">Using a tracked image</span></span>
<span data-ttu-id="5cdf8-132">下圖中的事件圖形會顯示用來在 QR 代碼中心呈現點的 **OnUpdateTrackedImage** 事件，並印出其資料。</span><span class="sxs-lookup"><span data-stu-id="5cdf8-132">The Event Graph in the following image shows the **OnUpdateTrackedImage** event being used to render a point in the center of a QR code and print out its data.</span></span>

![QR 轉譯範例](images/unreal-qr-render.PNG)

<span data-ttu-id="5cdf8-134">以下是後續動作：</span><span class="sxs-lookup"><span data-stu-id="5cdf8-134">Here's what's going on:</span></span>
1. <span data-ttu-id="5cdf8-135">首先，追蹤的影像會強制轉型為 **ARTrackedQRCode**，以檢查目前更新的影像是否為 QR 代碼。</span><span class="sxs-lookup"><span data-stu-id="5cdf8-135">First, the tracked image is cast to an **ARTrackedQRCode** to check that the current updated image is a QR code.</span></span>  
2. <span data-ttu-id="5cdf8-136">編碼的資料是從 **QRCode** 變數中擷取的。</span><span class="sxs-lookup"><span data-stu-id="5cdf8-136">The encoded data is retrieved from the **QRCode** variable.</span></span> <span data-ttu-id="5cdf8-137">您可以從 **GetLocalToWorldTransform** 的位置，以及具有 **GetEstimateSize** 的維度，到達 QR 代碼的左上角。</span><span class="sxs-lookup"><span data-stu-id="5cdf8-137">You can get the top-left of the QR code from the location of **GetLocalToWorldTransform** and the dimensions with **GetEstimateSize**.</span></span>

<span data-ttu-id="5cdf8-138">您也可以在程式碼中[取得 QR 代碼的座標系統](https://docs.microsoft.com/windows/mixed-reality/qr-code-tracking#getting-the-coordinate-system-for-a-qr-code)。</span><span class="sxs-lookup"><span data-stu-id="5cdf8-138">You can also [get the coordinate system for a QR code](https://docs.microsoft.com/windows/mixed-reality/qr-code-tracking#getting-the-coordinate-system-for-a-qr-code) in code.</span></span>

## <a name="finding-the-unique-id"></a><span data-ttu-id="5cdf8-139">尋找唯一識別碼</span><span class="sxs-lookup"><span data-stu-id="5cdf8-139">Finding the unique ID</span></span>
<span data-ttu-id="5cdf8-140">每個 QR 代碼都有唯一的 guid 識別碼，您可以透過下列方式找到該識別碼：</span><span class="sxs-lookup"><span data-stu-id="5cdf8-140">Every QR code has a unique guid ID, which you can find by:</span></span>
- <span data-ttu-id="5cdf8-141">拖放 **As ARTracked QRCode** 釘選並搜尋 [取得唯一識別碼]。</span><span class="sxs-lookup"><span data-stu-id="5cdf8-141">Dragging and dropping the **As ARTracked QRCode**  pin and searching for **Get Unique ID**.</span></span>

![QR GUID](images/unreal-qr-guid.PNG)

<span data-ttu-id="5cdf8-143">QR 代碼在幕後還有很多工作要做，因此這不是盡頭。</span><span class="sxs-lookup"><span data-stu-id="5cdf8-143">There's a lot going on behind the scenes with QR codes, so this isn't the end of the road.</span></span> <span data-ttu-id="5cdf8-144">請務必查看下列連結，以取得有關幕後內容的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="5cdf8-144">Be sure to check out the following links for more details on what's under the hood.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="5cdf8-145">下一個開發檢查點</span><span class="sxs-lookup"><span data-stu-id="5cdf8-145">Next Development Checkpoint</span></span>

<span data-ttu-id="5cdf8-146">依循我們配置的 Unreal 開發檢查點旅程，此時您會探索混合實境平台功能和 API。</span><span class="sxs-lookup"><span data-stu-id="5cdf8-146">If you're following the Unreal development checkpoint journey we've laid out, you're in the midst of exploring the Mixed Reality platform capabilities and APIs.</span></span> <span data-ttu-id="5cdf8-147">接下來，您可以繼續進行下一個主題：</span><span class="sxs-lookup"><span data-stu-id="5cdf8-147">From here, you can proceed to the next topic:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="5cdf8-148">WinRT</span><span class="sxs-lookup"><span data-stu-id="5cdf8-148">WinRT</span></span>](unreal-winRT.md)

<span data-ttu-id="5cdf8-149">或者，直接跳到在裝置或模擬器上部署應用程式的主題：</span><span class="sxs-lookup"><span data-stu-id="5cdf8-149">Or jump directly to deploying your app on a device or emulator:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="5cdf8-150">部署至裝置</span><span class="sxs-lookup"><span data-stu-id="5cdf8-150">Deploying to device</span></span>](unreal-deploying.md)

<span data-ttu-id="5cdf8-151">您可以隨時回到 [Unreal 開發檢查點](unreal-development-overview.md#3-platform-capabilities-and-apis)。</span><span class="sxs-lookup"><span data-stu-id="5cdf8-151">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#3-platform-capabilities-and-apis) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="5cdf8-152">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5cdf8-152">See also</span></span>
* [<span data-ttu-id="5cdf8-153">空間對應</span><span class="sxs-lookup"><span data-stu-id="5cdf8-153">Spatial mapping</span></span>](../../design/spatial-mapping.md)
* [<span data-ttu-id="5cdf8-154">全像投影</span><span class="sxs-lookup"><span data-stu-id="5cdf8-154">Holograms</span></span>](../../discover/hologram.md)
* [<span data-ttu-id="5cdf8-155">座標系統</span><span class="sxs-lookup"><span data-stu-id="5cdf8-155">Coordinate systems</span></span>](../../design/coordinate-systems.md)
