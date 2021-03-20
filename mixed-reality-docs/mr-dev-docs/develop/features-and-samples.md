---
title: 範例和功能應用程式
description: 隨時掌握所有可用的 Microsoft 範例以及 HoloLens 的混合實境功能應用程式。
author: hferrone
ms.author: jemccull
ms.date: 12/3/2020
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens, 學習, 範例, MRTK, 研究模式, HoloLens 2, qr 代碼, WebRTC, 混合實境擷取, 全像攝影遠端處理, UX 工具
ms.localizationpriority: high
ms.openlocfilehash: 78cfc726bdffdb461a83bd1e9805d8f0e64b0f01
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "98583191"
---
# <a name="samples-and-feature-apps"></a><span data-ttu-id="84a86-104">範例和功能應用程式</span><span class="sxs-lookup"><span data-stu-id="84a86-104">Samples and feature apps</span></span>

![使用者配戴並手動操作 HoloLens 的圖片](unreal/images/unreal-developer.jpg)

<span data-ttu-id="84a86-106">每個開發旅程一開始都會回顧其他開發人員已成功建置的內容 - 混合實境也是如此。</span><span class="sxs-lookup"><span data-stu-id="84a86-106">Every development journey starts with a look back at what other developers have successfully built - mixed reality is no different.</span></span> <span data-ttu-id="84a86-107">目前，我們所有的教學課程和範例應用程式都是在 Unity 或 Unreal 中建置。</span><span class="sxs-lookup"><span data-stu-id="84a86-107">Currently, all of our tutorials and sample apps are built in Unity or Unreal.</span></span> <span data-ttu-id="84a86-108">隨著我們開發其他引擎和平台的內容，您會在目錄中的相關標題底下找到它們。</span><span class="sxs-lookup"><span data-stu-id="84a86-108">As we develop content for other engines and platforms, you'll find them under the relevant heading in the Table of Contents.</span></span>

## <a name="sample-apps"></a><span data-ttu-id="84a86-109">範例應用程式</span><span class="sxs-lookup"><span data-stu-id="84a86-109">Sample apps</span></span>

[!INCLUDE[](includes/tabs-samples.md)]

## <a name="feature-samples"></a><span data-ttu-id="84a86-110">功能範例</span><span class="sxs-lookup"><span data-stu-id="84a86-110">Feature samples</span></span>

<span data-ttu-id="84a86-111">下列功能範例對應於我們的文件中說明的特定實作，並涵蓋各種開發平臺和硬體裝置。</span><span class="sxs-lookup"><span data-stu-id="84a86-111">The feature samples listed below correspond to specific implementations that are covered in our documentation and covers a range of development platforms and hardware devices.</span></span>

### <a name="research-mode"></a><span data-ttu-id="84a86-112">研究模式</span><span class="sxs-lookup"><span data-stu-id="84a86-112">Research Mode</span></span>

<span data-ttu-id="84a86-113">研究模式是在第 1 代 HoloLens 中導入的，可讓您存取裝置上的主要感應器，特別是並非供部署之用的研究應用程式。</span><span class="sxs-lookup"><span data-stu-id="84a86-113">Research Mode was introduced in the 1st Generation HoloLens to give access to key sensors on the device, specifically for research applications that are not intended for deployment.</span></span> <span data-ttu-id="84a86-114">以下範例應用程式是存取和記錄研究模式資料流以及使用[內部函式和外部函式](/windows/mixed-reality/locatable-camera#locating-the-device-camera-in-the-world)的範例。</span><span class="sxs-lookup"><span data-stu-id="84a86-114">The sample applications below are examples for accessing and recording Research Mode streams and using the [intrinsics and extrinsics](/windows/mixed-reality/locatable-camera#locating-the-device-camera-in-the-world).</span></span>

<br>

| <span data-ttu-id="84a86-115">參考文章</span><span class="sxs-lookup"><span data-stu-id="84a86-115">Reference article</span></span> | <span data-ttu-id="84a86-116">範例應用程式</span><span class="sxs-lookup"><span data-stu-id="84a86-116">Sample application</span></span> |
| --- | --- |
| [<span data-ttu-id="84a86-117">研究模式</span><span class="sxs-lookup"><span data-stu-id="84a86-117">Research Mode</span></span>](platform-capabilities-and-apis/research-mode.md) | [<span data-ttu-id="84a86-118">HoloLens (第 1 代)</span><span class="sxs-lookup"><span data-stu-id="84a86-118">HoloLens (1st gen)</span></span>](https://github.com/microsoft/HoloLensForCV/tree/master/Samples) |
| [<span data-ttu-id="84a86-119">研究模式</span><span class="sxs-lookup"><span data-stu-id="84a86-119">Research Mode</span></span>](platform-capabilities-and-apis/research-mode.md) | [<span data-ttu-id="84a86-120">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="84a86-120">HoloLens 2</span></span>](https://github.com/microsoft/HoloLens2ForCV/tree/main/Samples) |

### <a name="qr-codes"></a><span data-ttu-id="84a86-121">QR 代碼</span><span class="sxs-lookup"><span data-stu-id="84a86-121">QR codes</span></span>

<span data-ttu-id="84a86-122">HoloLens 2 可以偵測頭戴式裝置周圍環境中的 QR 代碼，而在每個代碼的真實世界位置建立座標系統。</span><span class="sxs-lookup"><span data-stu-id="84a86-122">HoloLens 2 can detect QR codes in the environment around the headset, establishing a coordinate system at each code's real-world location.</span></span>

<br>

| <span data-ttu-id="84a86-123">參考文章</span><span class="sxs-lookup"><span data-stu-id="84a86-123">Reference article</span></span> | <span data-ttu-id="84a86-124">範例</span><span class="sxs-lookup"><span data-stu-id="84a86-124">Sample</span></span> |
| --- | --- |
| [<span data-ttu-id="84a86-125">QR 代碼</span><span class="sxs-lookup"><span data-stu-id="84a86-125">QR codes</span></span>](platform-capabilities-and-apis/qr-code-tracking.md) | [<span data-ttu-id="84a86-126">Unity 中的 QR 代碼追蹤</span><span class="sxs-lookup"><span data-stu-id="84a86-126">QR code tracking in Unity</span></span>](https://github.com/chgatla-microsoft/QRTracking/tree/master/SampleQRCodes) |

### <a name="webrtc"></a><span data-ttu-id="84a86-127">WebRTC</span><span class="sxs-lookup"><span data-stu-id="84a86-127">WebRTC</span></span>

<span data-ttu-id="84a86-128">MixedReality-WebRTC 專案是多項元件的集合，可協助混合實境應用程式開發人員將點對點音訊、影片和資料即時通訊整合到其應用程式中。WebRTC 元件以即時通訊 (RTC) 的 WebRTC 通訊協定為基礎，大多數的新式網頁瀏覽器均加以支援。</span><span class="sxs-lookup"><span data-stu-id="84a86-128">The MixedReality-WebRTC project is a collection of components to help mixed reality app developers to integrate peer-to-peer audio, video, and data real-time communication into their applications WebRTC components are based on the WebRTC protocol for Real-Time Communication (RTC), which is supported by most modern web browsers.</span></span>

<br>

| <span data-ttu-id="84a86-129">參考文章</span><span class="sxs-lookup"><span data-stu-id="84a86-129">Reference article</span></span> | <span data-ttu-id="84a86-130">範例</span><span class="sxs-lookup"><span data-stu-id="84a86-130">Sample</span></span> |
| --- | --- |
| [<span data-ttu-id="84a86-131">WebRTC</span><span class="sxs-lookup"><span data-stu-id="84a86-131">WebRTC</span></span>](https://microsoft.github.io/MixedReality-WebRTC) | [<span data-ttu-id="84a86-132">WebRTC 範例應用程式</span><span class="sxs-lookup"><span data-stu-id="84a86-132">WebRTC sample apps</span></span>](https://github.com/microsoft/MixedReality-WebRTC/tree/master/examples) |

### <a name="holographic-mixed-reality-capture"></a><span data-ttu-id="84a86-133">全像攝影混合實境擷取</span><span class="sxs-lookup"><span data-stu-id="84a86-133">Holographic Mixed Reality Capture</span></span>

<span data-ttu-id="84a86-134">混合實境擷取 (MRC) 會以相片或影片的形式擷取將真實和數位世界融合的第一人稱體驗，並即時與其他人分享您所看到的內容。</span><span class="sxs-lookup"><span data-stu-id="84a86-134">Mixed reality capture (MRC) captures the first-person experience of mixing real and digital worlds as a photo or video, sharing what you see with others in real-time.</span></span>

<br>

| <span data-ttu-id="84a86-135">參考文章</span><span class="sxs-lookup"><span data-stu-id="84a86-135">Reference article</span></span> | <span data-ttu-id="84a86-136">範例</span><span class="sxs-lookup"><span data-stu-id="84a86-136">Sample</span></span> |
| --- | --- |
| [<span data-ttu-id="84a86-137">混合實境擷取</span><span class="sxs-lookup"><span data-stu-id="84a86-137">Mixed Reality Capture</span></span>](platform-capabilities-and-apis/mixed-reality-capture-for-developers.md) | [<span data-ttu-id="84a86-138">混合實境擷取範例</span><span class="sxs-lookup"><span data-stu-id="84a86-138">Mixed Reality Capture samples</span></span>](/samples/microsoft/windows-universal-samples/holographicmixedrealitycapture/) |

### <a name="holographic-remoting"></a><span data-ttu-id="84a86-139">全像攝影遠端處理</span><span class="sxs-lookup"><span data-stu-id="84a86-139">Holographic Remoting</span></span>

<span data-ttu-id="84a86-140">全像攝影遠端處理播放程式是一種隨附的應用程式，可連線至支援全像攝影遠端處理的電腦應用程式和遊戲。</span><span class="sxs-lookup"><span data-stu-id="84a86-140">The Holographic Remoting Player is a companion app that connects to PC apps and games that support Holographic Remoting.</span></span> <span data-ttu-id="84a86-141">全像攝影遠端處理會使用 Wi-Fi 連線即時將全像攝影內容從電腦串流至您的 Microsoft HoloLens，且在 HoloLens (第 1 代) 和 HoloLens 2 上均受支援。</span><span class="sxs-lookup"><span data-stu-id="84a86-141">Holographic Remoting streams holographic content from a PC to your Microsoft HoloLens in real-time, using a Wi-Fi connection, and is supported on HoloLens (1st gen) and HoloLens 2.</span></span>

<br>

| <span data-ttu-id="84a86-142">參考文章</span><span class="sxs-lookup"><span data-stu-id="84a86-142">Reference article</span></span> | <span data-ttu-id="84a86-143">範例</span><span class="sxs-lookup"><span data-stu-id="84a86-143">Sample</span></span> |
| --- | --- |
| [<span data-ttu-id="84a86-144">全像攝影遠端處理</span><span class="sxs-lookup"><span data-stu-id="84a86-144">Holographic Remoting</span></span>](platform-capabilities-and-apis/holographic-remoting-player.md) | [<span data-ttu-id="84a86-145">全像攝影遠端處理範例</span><span class="sxs-lookup"><span data-stu-id="84a86-145">Holographic Remoting samples</span></span>](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples) |