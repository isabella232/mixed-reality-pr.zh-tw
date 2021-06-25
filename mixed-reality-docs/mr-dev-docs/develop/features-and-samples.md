---
title: 範例和功能應用程式
description: 隨時掌握所有可用的 Microsoft 範例以及 HoloLens 的混合實境功能應用程式。
author: hferrone
ms.author: jemccull
ms.date: 6/7/2021
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens, 學習, 範例, MRTK, 研究模式, HoloLens 2, qr 代碼, WebRTC, 混合實境擷取, 全像攝影遠端處理, UX 工具
ms.localizationpriority: high
ms.openlocfilehash: 78a9e343fde4a6cbc23268f0be353577498d67b6
ms.sourcegitcommit: 72970dbe6674e28c250f741e50a44a238bb162d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2021
ms.locfileid: "112906894"
---
# <a name="samples-and-feature-apps"></a><span data-ttu-id="64844-104">範例和功能應用程式</span><span class="sxs-lookup"><span data-stu-id="64844-104">Samples and feature apps</span></span>

![使用者配戴並手動操作 HoloLens 的圖片](unreal/images/unreal-developer.jpg)

<span data-ttu-id="64844-106">每個開發旅程一開始都會回顧其他開發人員已成功建置的內容 - 混合實境也是如此。</span><span class="sxs-lookup"><span data-stu-id="64844-106">Every development journey starts with a look back at what other developers have successfully built - mixed reality is no different.</span></span> <span data-ttu-id="64844-107">目前，我們所有的教學課程和範例應用程式都是在 Unity 或 Unreal 中建置。</span><span class="sxs-lookup"><span data-stu-id="64844-107">Currently, all of our tutorials and sample apps are built in Unity or Unreal.</span></span> <span data-ttu-id="64844-108">隨著我們開發其他引擎和平台的內容，您會在目錄中的相關標題底下找到它們。</span><span class="sxs-lookup"><span data-stu-id="64844-108">As we develop content for other engines and platforms, you'll find them under the relevant heading in the Table of Contents.</span></span>

## <a name="sample-apps"></a><span data-ttu-id="64844-109">範例應用程式</span><span class="sxs-lookup"><span data-stu-id="64844-109">Sample apps</span></span>

[!INCLUDE[](includes/tabs-samples.md)]

## <a name="feature-samples"></a><span data-ttu-id="64844-110">功能範例</span><span class="sxs-lookup"><span data-stu-id="64844-110">Feature samples</span></span>

<span data-ttu-id="64844-111">下列功能範例對應於我們的文件中說明的特定實作，並涵蓋各種開發平臺和硬體裝置。</span><span class="sxs-lookup"><span data-stu-id="64844-111">The feature samples listed below correspond to specific implementations that are covered in our documentation and covers a range of development platforms and hardware devices.</span></span>

### <a name="openxr"></a><span data-ttu-id="64844-112">OpenXR</span><span class="sxs-lookup"><span data-stu-id="64844-112">OpenXR</span></span>

<span data-ttu-id="64844-113">針對以 Unity 2020 為目標的開發人員建立 HoloLens 2 或混合的現實應用程式，OpenXR 外掛程式可以用來取代 WindowsXR 外掛程式，以獲得更好的跨平臺相容性。</span><span class="sxs-lookup"><span data-stu-id="64844-113">For developers targeting Unity 2020 to build HoloLens 2 or Mixed Reality applications, OpenXR plugin can be used instead of WindowsXR plugin for better cross platform compatibilities.</span></span> <span data-ttu-id="64844-114">Mixed Reality OpenXR 外掛程式也適用于最新的混合現實工具組2.7。</span><span class="sxs-lookup"><span data-stu-id="64844-114">The Mixed Reality OpenXR Plugin also works well with latest Mixed Reality Toolkit 2.7.</span></span>

<br>

| <span data-ttu-id="64844-115">參考文章</span><span class="sxs-lookup"><span data-stu-id="64844-115">Reference article</span></span> | <span data-ttu-id="64844-116">範例</span><span class="sxs-lookup"><span data-stu-id="64844-116">Sample</span></span> |
| --- | --- |
| [<span data-ttu-id="64844-117">使用 OpenXR 外掛程式</span><span class="sxs-lookup"><span data-stu-id="64844-117">Using the OpenXR plugin</span></span>](./unity/xr-project-setup.md) | [<span data-ttu-id="64844-118">混合現實 OpenXR 與 Unity 範例</span><span class="sxs-lookup"><span data-stu-id="64844-118">Mixed Reality OpenXR with Unity samples</span></span>](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples) |
| <span data-ttu-id="64844-119">N/A</span><span class="sxs-lookup"><span data-stu-id="64844-119">N/A</span></span> | [<span data-ttu-id="64844-120">OpenXR MRTK Base Unity 專案</span><span class="sxs-lookup"><span data-stu-id="64844-120">OpenXR MRTK Base Unity project</span></span>](https://github.com/microsoft/UnityOpenXRMRTKBase) |

### <a name="research-mode"></a><span data-ttu-id="64844-121">研究模式</span><span class="sxs-lookup"><span data-stu-id="64844-121">Research Mode</span></span>

<span data-ttu-id="64844-122">研究模式是在第 1 代 HoloLens 中導入的，可讓您存取裝置上的主要感應器，特別是並非供部署之用的研究應用程式。</span><span class="sxs-lookup"><span data-stu-id="64844-122">Research Mode was introduced in the 1st Generation HoloLens to give access to key sensors on the device, specifically for research applications that are not intended for deployment.</span></span> <span data-ttu-id="64844-123">以下範例應用程式是存取和記錄研究模式資料流以及使用[內部函式和外部函式](/windows/mixed-reality/locatable-camera#locating-the-device-camera-in-the-world)的範例。</span><span class="sxs-lookup"><span data-stu-id="64844-123">The sample applications below are examples for accessing and recording Research Mode streams and using the [intrinsics and extrinsics](/windows/mixed-reality/locatable-camera#locating-the-device-camera-in-the-world).</span></span>

<br>

| <span data-ttu-id="64844-124">參考文章</span><span class="sxs-lookup"><span data-stu-id="64844-124">Reference article</span></span> | <span data-ttu-id="64844-125">範例應用程式</span><span class="sxs-lookup"><span data-stu-id="64844-125">Sample application</span></span> |
| --- | --- |
| [<span data-ttu-id="64844-126">研究模式</span><span class="sxs-lookup"><span data-stu-id="64844-126">Research Mode</span></span>](platform-capabilities-and-apis/research-mode.md) | [<span data-ttu-id="64844-127">HoloLens (第 1 代)</span><span class="sxs-lookup"><span data-stu-id="64844-127">HoloLens (1st gen)</span></span>](https://github.com/microsoft/HoloLensForCV/tree/master/Samples) |
| [<span data-ttu-id="64844-128">研究模式</span><span class="sxs-lookup"><span data-stu-id="64844-128">Research Mode</span></span>](platform-capabilities-and-apis/research-mode.md) | [<span data-ttu-id="64844-129">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="64844-129">HoloLens 2</span></span>](https://github.com/microsoft/HoloLens2ForCV/tree/main/Samples) |

### <a name="qr-codes"></a><span data-ttu-id="64844-130">QR 代碼</span><span class="sxs-lookup"><span data-stu-id="64844-130">QR codes</span></span>

<span data-ttu-id="64844-131">HoloLens 2 可以偵測頭戴式裝置周圍環境中的 QR 代碼，而在每個代碼的真實世界位置建立座標系統。</span><span class="sxs-lookup"><span data-stu-id="64844-131">HoloLens 2 can detect QR codes in the environment around the headset, establishing a coordinate system at each code's real-world location.</span></span>

<br>

| <span data-ttu-id="64844-132">參考文章</span><span class="sxs-lookup"><span data-stu-id="64844-132">Reference article</span></span> | <span data-ttu-id="64844-133">範例</span><span class="sxs-lookup"><span data-stu-id="64844-133">Sample</span></span> |
| --- | --- |
| [<span data-ttu-id="64844-134">QR 代碼</span><span class="sxs-lookup"><span data-stu-id="64844-134">QR codes</span></span>](platform-capabilities-and-apis/qr-code-tracking.md) | [<span data-ttu-id="64844-135">Unity 中的 QR 代碼追蹤</span><span class="sxs-lookup"><span data-stu-id="64844-135">QR code tracking in Unity</span></span>](https://github.com/microsoft/MixedReality-QRCode-Sample) |

### <a name="scene-understanding"></a><span data-ttu-id="64844-136">場景理解</span><span class="sxs-lookup"><span data-stu-id="64844-136">Scene understanding</span></span>

<span data-ttu-id="64844-137">場景理解為混合的現實開發人員提供結構化、高階的環境標記法，其設計目的是為了讓環保感知應用程式的開發變得直覺。</span><span class="sxs-lookup"><span data-stu-id="64844-137">Scene understanding provides Mixed Reality developers with a structured, high-level environment representation designed to make developing for environmentally aware applications intuitive.</span></span> <span data-ttu-id="64844-138">場景理解藉由結合現有混合現實執行時間的強大功能，例如高度精確但較不具結構化的空間對應和全新的 AI 驅動執行時間。</span><span class="sxs-lookup"><span data-stu-id="64844-138">Scene understanding does this by combining the power of existing mixed reality runtimes, like the highly accurate but less structured spatial mapping and new AI driven runtimes.</span></span>

<br>

| <span data-ttu-id="64844-139">參考文章</span><span class="sxs-lookup"><span data-stu-id="64844-139">Reference article</span></span> | <span data-ttu-id="64844-140">範例</span><span class="sxs-lookup"><span data-stu-id="64844-140">Sample</span></span> |
| --- | --- |
| [<span data-ttu-id="64844-141">場景理解</span><span class="sxs-lookup"><span data-stu-id="64844-141">Scene understanding</span></span>](../design/scene-understanding.md) | [<span data-ttu-id="64844-142">混合現實場景理解範例</span><span class="sxs-lookup"><span data-stu-id="64844-142">Mixed Reality Scene Understanding samples</span></span>](https://github.com/microsoft/MixedReality-SceneUnderstanding-Samples) |

### <a name="webrtc"></a><span data-ttu-id="64844-143">WebRTC</span><span class="sxs-lookup"><span data-stu-id="64844-143">WebRTC</span></span>

<span data-ttu-id="64844-144">MixedReality-WebRTC 專案是多項元件的集合，可協助混合實境應用程式開發人員將點對點音訊、影片和資料即時通訊整合到其應用程式中。WebRTC 元件以即時通訊 (RTC) 的 WebRTC 通訊協定為基礎，大多數的新式網頁瀏覽器均加以支援。</span><span class="sxs-lookup"><span data-stu-id="64844-144">The MixedReality-WebRTC project is a collection of components to help mixed reality app developers to integrate peer-to-peer audio, video, and data real-time communication into their applications WebRTC components are based on the WebRTC protocol for Real-Time Communication (RTC), which is supported by most modern web browsers.</span></span>

<br>

| <span data-ttu-id="64844-145">參考文章</span><span class="sxs-lookup"><span data-stu-id="64844-145">Reference article</span></span> | <span data-ttu-id="64844-146">範例</span><span class="sxs-lookup"><span data-stu-id="64844-146">Sample</span></span> |
| --- | --- |
| [<span data-ttu-id="64844-147">WebRTC</span><span class="sxs-lookup"><span data-stu-id="64844-147">WebRTC</span></span>](https://microsoft.github.io/MixedReality-WebRTC) | [<span data-ttu-id="64844-148">WebRTC 範例應用程式</span><span class="sxs-lookup"><span data-stu-id="64844-148">WebRTC sample apps</span></span>](https://github.com/microsoft/MixedReality-WebRTC/tree/master/examples) |

### <a name="holographic-mixed-reality-capture"></a><span data-ttu-id="64844-149">全像攝影混合實境擷取</span><span class="sxs-lookup"><span data-stu-id="64844-149">Holographic Mixed Reality Capture</span></span>

<span data-ttu-id="64844-150">混合實境擷取 (MRC) 會以相片或影片的形式擷取將真實和數位世界融合的第一人稱體驗，並即時與其他人分享您所看到的內容。</span><span class="sxs-lookup"><span data-stu-id="64844-150">Mixed reality capture (MRC) captures the first-person experience of mixing real and digital worlds as a photo or video, sharing what you see with others in real-time.</span></span>

<br>

| <span data-ttu-id="64844-151">參考文章</span><span class="sxs-lookup"><span data-stu-id="64844-151">Reference article</span></span> | <span data-ttu-id="64844-152">範例</span><span class="sxs-lookup"><span data-stu-id="64844-152">Sample</span></span> |
| --- | --- |
| [<span data-ttu-id="64844-153">混合實境擷取</span><span class="sxs-lookup"><span data-stu-id="64844-153">Mixed Reality Capture</span></span>](platform-capabilities-and-apis/mixed-reality-capture-for-developers.md) | [<span data-ttu-id="64844-154">混合實境擷取範例</span><span class="sxs-lookup"><span data-stu-id="64844-154">Mixed Reality Capture samples</span></span>](/samples/microsoft/windows-universal-samples/holographicmixedrealitycapture/) |

### <a name="holographic-remoting"></a><span data-ttu-id="64844-155">全像攝影遠端處理</span><span class="sxs-lookup"><span data-stu-id="64844-155">Holographic Remoting</span></span>

<span data-ttu-id="64844-156">全像攝影遠端處理播放程式是一種隨附的應用程式，可連線至支援全像攝影遠端處理的電腦應用程式和遊戲。</span><span class="sxs-lookup"><span data-stu-id="64844-156">The Holographic Remoting Player is a companion app that connects to PC apps and games that support Holographic Remoting.</span></span> <span data-ttu-id="64844-157">全像攝影遠端處理會使用 Wi-Fi 連線即時將全像攝影內容從電腦串流至您的 Microsoft HoloLens，且在 HoloLens (第 1 代) 和 HoloLens 2 上均受支援。</span><span class="sxs-lookup"><span data-stu-id="64844-157">Holographic Remoting streams holographic content from a PC to your Microsoft HoloLens in real-time, using a Wi-Fi connection, and is supported on HoloLens (1st gen) and HoloLens 2.</span></span>

<br>

| <span data-ttu-id="64844-158">參考文章</span><span class="sxs-lookup"><span data-stu-id="64844-158">Reference article</span></span> | <span data-ttu-id="64844-159">範例</span><span class="sxs-lookup"><span data-stu-id="64844-159">Sample</span></span> |
| --- | --- |
| [<span data-ttu-id="64844-160">全像攝影遠端處理</span><span class="sxs-lookup"><span data-stu-id="64844-160">Holographic Remoting</span></span>](platform-capabilities-and-apis/holographic-remoting-player.md) | [<span data-ttu-id="64844-161">全像攝影遠端處理範例</span><span class="sxs-lookup"><span data-stu-id="64844-161">Holographic Remoting samples</span></span>](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples) |