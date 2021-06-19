---
title: QR 代碼追蹤
description: 瞭解如何在 HoloLens 2 上偵測 QR 代碼、新增網路攝影機功能，以及管理混合現實應用程式中的座標系統。
author: dorreneb
ms.author: dobrown
ms.date: 01/21/2021
ms.topic: article
keywords: vr、lbe、以位置為基礎的娛樂、vr arcade、arcade、沉浸式、qr、qr 代碼、hololens2
ms.openlocfilehash: 9d3a5d9696fbf875b2e6a890ed837efc055a9e6e
ms.sourcegitcommit: 6ade7e8ebab7003fc24f9e0b5fa81d091369622c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2021
ms.locfileid: "112394332"
---
# <a name="qr-code-tracking"></a><span data-ttu-id="09b25-104">QR 代碼追蹤</span><span class="sxs-lookup"><span data-stu-id="09b25-104">QR code tracking</span></span>

<span data-ttu-id="09b25-105">HoloLens 2 可以偵測頭戴式裝置周圍環境中的 QR 代碼，而在每個代碼的真實世界位置建立座標系統。</span><span class="sxs-lookup"><span data-stu-id="09b25-105">HoloLens 2 can detect QR codes in the environment around the headset, establishing a coordinate system at each code's real-world location.</span></span> <span data-ttu-id="09b25-106">啟用裝置的網路攝影機之後，您就能夠辨識 Unreal 或 Unity 專案最新版本中的 QR 代碼。</span><span class="sxs-lookup"><span data-stu-id="09b25-106">Once you enable your device's webcam, you'll be able to recognize QR codes in the latest versions of your Unreal or Unity projects.</span></span> <span data-ttu-id="09b25-107">在進入生產環境之前，建議您遵循我們在本文結尾的 [最佳作法](#best-practices-for-qr-code-detection) 。</span><span class="sxs-lookup"><span data-stu-id="09b25-107">Before going to production, we recommend following the [best practices](#best-practices-for-qr-code-detection) we've laid at the end of the article.</span></span>

## <a name="device-support"></a><span data-ttu-id="09b25-108">裝置支援</span><span class="sxs-lookup"><span data-stu-id="09b25-108">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="09b25-109">功能</span><span class="sxs-lookup"><span data-stu-id="09b25-109">Feature</span></span></th><th style="width:150px"> <span data-ttu-id="09b25-110"><a href="/hololens/hololens1-hardware">HoloLens (第一代) </a></span><span class="sxs-lookup"><span data-stu-id="09b25-110"><a href="/hololens/hololens1-hardware">HoloLens (first gen)</a></span></span></th><th style="width:150px"><span data-ttu-id="09b25-111">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="09b25-111">HoloLens 2</span></span></th><th style="width:150px"> <span data-ttu-id="09b25-112"><a href="../../discover/immersive-headset-hardware-details.md">沉浸式頭戴裝置</a></span><span class="sxs-lookup"><span data-stu-id="09b25-112"><a href="../../discover/immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="09b25-113">QR 代碼偵測</span><span class="sxs-lookup"><span data-stu-id="09b25-113">QR code detection</span></span></td><td style="text-align: center;"><span data-ttu-id="09b25-114">️</span><span class="sxs-lookup"><span data-stu-id="09b25-114">️</span></span></td><td style="text-align: center;"> <span data-ttu-id="09b25-115">✔️</span><span class="sxs-lookup"><span data-stu-id="09b25-115">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="09b25-116">✔️</span><span class="sxs-lookup"><span data-stu-id="09b25-116">✔️</span></span></td>
</tr>
</table>

>[!NOTE]
><span data-ttu-id="09b25-117">Windows 10 2004 版和更高版本支援在桌上型電腦上使用沉浸式 Windows Mixed Reality 耳機進行 QR 代碼追蹤。</span><span class="sxs-lookup"><span data-stu-id="09b25-117">QR code tracking with immersive Windows Mixed Reality headsets on desktop PCs is supported on Windows 10 Version 2004 and higher.</span></span> <span data-ttu-id="09b25-118">使用 MixedReality. QRCodeWatcher. IsSupported () API 來判斷目前的裝置是否支援此功能。</span><span class="sxs-lookup"><span data-stu-id="09b25-118">Use the Microsoft.MixedReality.QRCodeWatcher.IsSupported() API to determine whether the feature is supported on the current device.</span></span>

## <a name="getting-the-qr-package"></a><span data-ttu-id="09b25-119">取得 QR 套件</span><span class="sxs-lookup"><span data-stu-id="09b25-119">Getting the QR package</span></span>

<span data-ttu-id="09b25-120">您可以在 [這裡](https://nuget.org/Packages/Microsoft.MixedReality.QR)下載適用于 QR 代碼偵測的 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="09b25-120">You can download the NuGet package for QR code detection [here](https://nuget.org/Packages/Microsoft.MixedReality.QR).</span></span>

## <a name="using-openxr"></a><span data-ttu-id="09b25-121">使用 OpenXR</span><span class="sxs-lookup"><span data-stu-id="09b25-121">Using OpenXR</span></span>

<span data-ttu-id="09b25-122">使用 OpenXR 外掛程式時，請[ `SpatialGraphNodeId` 從 QR API](../platform-capabilities-and-apis/qr-code-tracking.md#qr-api-reference)抓取，並使用 `Microsoft.MixedReality.OpenXR.SpatialGraphNode` API 來尋找 qr 代碼。</span><span class="sxs-lookup"><span data-stu-id="09b25-122">When using the OpenXR plugin, grab the [`SpatialGraphNodeId` from the QR API](../platform-capabilities-and-apis/qr-code-tracking.md#qr-api-reference) and use the `Microsoft.MixedReality.OpenXR.SpatialGraphNode` API to locate the QR code.</span></span>

<span data-ttu-id="09b25-123">如需參考，我們[在 GitHub 上有 QR 追蹤範例專案](https://github.com/yl-msft/QRTracking)，並有更詳細的[ `SpatialGraphNode` API](https://github.com/yl-msft/QRTracking/blob/main/SampleQRCodes/Assets/Scripts/SpatialGraphNodeTracker.cs)使用說明。</span><span class="sxs-lookup"><span data-stu-id="09b25-123">For reference, we have a [QR tracking sample project on GitHub](https://github.com/yl-msft/QRTracking) with more a detailed usage explanation for the [`SpatialGraphNode` API](https://github.com/yl-msft/QRTracking/blob/main/SampleQRCodes/Assets/Scripts/SpatialGraphNodeTracker.cs).</span></span>

## <a name="detecting-qr-codes"></a><span data-ttu-id="09b25-124">偵測 QR 代碼</span><span class="sxs-lookup"><span data-stu-id="09b25-124">Detecting QR codes</span></span>

### <a name="adding-the-webcam-capability"></a><span data-ttu-id="09b25-125">新增網路攝影機功能</span><span class="sxs-lookup"><span data-stu-id="09b25-125">Adding the webcam capability</span></span>

<span data-ttu-id="09b25-126">您必須將功能新增 `webcam` 至您的資訊清單，以偵測 QR 代碼。</span><span class="sxs-lookup"><span data-stu-id="09b25-126">You'll need to add the capability `webcam` to your manifest to detect QR codes.</span></span> <span data-ttu-id="09b25-127">這項功能是必要的，因為使用者環境中偵測到的程式碼內的資料可能包含機密資訊。</span><span class="sxs-lookup"><span data-stu-id="09b25-127">This capability is required as the data within detected codes in the user's environment may contain sensitive information.</span></span>

<span data-ttu-id="09b25-128">您可以呼叫下列方法來要求許可權 `QRCodeWatcher.RequestAccessAsync()` ：</span><span class="sxs-lookup"><span data-stu-id="09b25-128">Permission can be requested by calling `QRCodeWatcher.RequestAccessAsync()`:</span></span>

<span data-ttu-id="09b25-129">_C#：_</span><span class="sxs-lookup"><span data-stu-id="09b25-129">_C#:_</span></span>
```cs
await QRCodeWatcher.RequestAccessAsync();
```

<span data-ttu-id="09b25-130">_C++：_</span><span class="sxs-lookup"><span data-stu-id="09b25-130">_C++:_</span></span>
```cpp
co_await QRCodeWatcher.RequestAccessAsync();
```

<span data-ttu-id="09b25-131">在您建立 QRCodeWatcher 物件之前，必須先要求許可權。</span><span class="sxs-lookup"><span data-stu-id="09b25-131">Permission must be requested before you construct a QRCodeWatcher object.</span></span>

<span data-ttu-id="09b25-132">當 QR 代碼偵測需要這項 `webcam` 功能時，會使用裝置的追蹤攝影機進行偵測。</span><span class="sxs-lookup"><span data-stu-id="09b25-132">While QR code detection requires the `webcam` capability, the detection occurs using the device's tracking cameras.</span></span> <span data-ttu-id="09b25-133">相較于使用裝置的相片/影片 (PV) 攝影機的偵測，這可提供更廣泛的偵測 FOV 和較佳的電池壽命。</span><span class="sxs-lookup"><span data-stu-id="09b25-133">This provides a wider detection FOV and better battery life compared to detection with the device's photo/video (PV) camera.</span></span>

### <a name="detecting-qr-codes-in-unity"></a><span data-ttu-id="09b25-134">在 Unity 中偵測 QR 代碼</span><span class="sxs-lookup"><span data-stu-id="09b25-134">Detecting QR codes in Unity</span></span>

<span data-ttu-id="09b25-135">您可以在 Unity 中使用 QR 代碼偵測 API，而不需要匯入 MRTK，方法是使用 [nuget For Unity](https://github.com/GlitchEnzo/NuGetForUnity)安裝 nuget 套件。</span><span class="sxs-lookup"><span data-stu-id="09b25-135">You can use the QR code detection API in Unity without importing MRTK by installing the NuGet package using [NuGet for Unity](https://github.com/GlitchEnzo/NuGetForUnity).</span></span> <span data-ttu-id="09b25-136">如果您想要瞭解其運作方式，請下載 [範例 Unity 應用程式](https://github.com/chgatla-microsoft/QRTracking/tree/master/SampleQRCodes)。</span><span class="sxs-lookup"><span data-stu-id="09b25-136">If you want to get a feel for how it works, download the [sample Unity app](https://github.com/chgatla-microsoft/QRTracking/tree/master/SampleQRCodes).</span></span> <span data-ttu-id="09b25-137">範例應用程式中的範例會顯示 QR 代碼的全像正方形，以及相關聯的資料，例如 GUID、實體大小、時間戳記和已解碼的資料。</span><span class="sxs-lookup"><span data-stu-id="09b25-137">The sample app has examples for displaying a holographic square over QR codes and associated data such as GUID, physical size, timestamp, and decoded data.</span></span>

### <a name="detecting-qr-codes-in-c"></a><span data-ttu-id="09b25-138">在 c + + 中偵測 QR 代碼</span><span class="sxs-lookup"><span data-stu-id="09b25-138">Detecting QR codes in C++</span></span>

```cpp
using namespace winrt::Windows::Foundation;
using namespace winrt::Microsoft::MixedReality::QR;

class QRListHelper
{
public:
    QRListHelper(MyApplication& app) :
        m_app(app)
    {}

    IAsyncAction SetUpQRCodes()
    {
        if (QRCodeWatcher::IsSupported())
        {
            QRCodeWatcherAccessStatus status = co_await QRCodeWatcher::RequestAccessAsync();
            InitializeQR(status);
        }
    }

private:
    void OnAddedQRCode(const IInspectable&, const QRCodeAddedEventArgs& args)
    {
        m_app.OnAddedQRCode(args);
    }

    void OnUpdatedQRCode(const IInspectable&, const QRCodeUpdatedEventArgs& args)
    {
        m_app.OnUpdatedQRCode(args);
    }

    void OnEnumerationComplete(const IInspectable&, const IInspectable&)
    {
        m_app.OnEnumerationComplete();
    }

    MyApplication& m_app;
    QRCodeWatcher m_qrWatcher{ nullptr };

    void InitializeQR(QRCodeWatcherAccessStatus status)
    {
        if (status == QRCodeWatcherAccessStatus::Allowed)
        {
            m_qrWatcher = QRCodeWatcher();
            m_qrWatcher.Added({ this, &QRListHelper::OnAddedQRCode });
            m_qrWatcher.Updated({ this, &QRListHelper::OnUpdatedQRCode });
            m_qrWatcher.EnumerationCompleted({ this, &QRListHelper::OnEnumerationComplete });
            m_qrWatcher.Start();
        }
        else
        {
            // Permission denied by system or user
            // Handle the failures
        }
    }
};
```

## <a name="getting-the-coordinate-system-for-a-qr-code"></a><span data-ttu-id="09b25-139">取得 QR 代碼的座標系統</span><span class="sxs-lookup"><span data-stu-id="09b25-139">Getting the coordinate system for a QR code</span></span>

<span data-ttu-id="09b25-140">每個偵測到的 QR 代碼都會公開 [空間座標系統](../../design/coordinate-systems.md) ，此系統會對齊左上角的 QR 代碼，位於左上角的快速偵測方塊左上角：</span><span class="sxs-lookup"><span data-stu-id="09b25-140">Each detected QR code exposes a [spatial coordinate system](../../design/coordinate-systems.md) aligned with the QR code at the top-left corner of the fast detection square in the top left:</span></span>  

![QR 代碼座標系統](images/Qr-coordinatesystem.png) 

<span data-ttu-id="09b25-142">當直接使用 QR SDK 時，Z 軸會指向紙張 (不會顯示) -轉換成 Unity 座標時，Z 軸會指向紙張，並會被左手。</span><span class="sxs-lookup"><span data-stu-id="09b25-142">When directly using the QR SDK, the Z-axis is pointing into the paper (not shown) - when converted into Unity coordinates, the Z-axis points out of the paper and is left-handed.</span></span>

<span data-ttu-id="09b25-143">QR 代碼的 SpatialCoordinateSystem 會對齊，如下所示。</span><span class="sxs-lookup"><span data-stu-id="09b25-143">A QR code's SpatialCoordinateSystem aligns as shown.</span></span> <span data-ttu-id="09b25-144">您可以藉由呼叫 <a href="/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.createcoordinatesystemfornode" target="_blank">SpatialGraphInteropPreview：： CreateCoordinateSystemForNode</a> 並傳入程式碼的 SpatialGraphNodeId，從平臺取得座標系統。</span><span class="sxs-lookup"><span data-stu-id="09b25-144">You can get the coordinate system from the platform by calling <a href="/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.createcoordinatesystemfornode" target="_blank">SpatialGraphInteropPreview::CreateCoordinateSystemForNode</a> and passing in the code's SpatialGraphNodeId.</span></span>

<span data-ttu-id="09b25-145">下列 c + + 程式碼顯示如何建立矩形，並使用 QR 代碼的座標系統來放置它：</span><span class="sxs-lookup"><span data-stu-id="09b25-145">The C++ code below shows how to create a rectangle and place it using the QR code's coordinate system:</span></span>

```cpp
// Creates a 2D rectangle in the x-y plane, with the specified properties.
std::vector<float3> MyApplication::CreateRectangle(float width, float height)
{
    std::vector<float3> vertices(4);

    vertices[0] = { 0, 0, 0 };
    vertices[1] = { width, 0, 0 };
    vertices[2] = { width, height, 0 };
    vertices[3] = { 0, height, 0 };

    return vertices;
}
```

<span data-ttu-id="09b25-146">您可以使用實體大小來建立 QR 矩形：</span><span class="sxs-lookup"><span data-stu-id="09b25-146">You can use the physical size to create the QR rectangle:</span></span>

```cpp
std::vector<float3> qrVertices = CreateRectangle(code.PhysicalSideLength(), code.PhysicalSideLength()); 
```

<span data-ttu-id="09b25-147">座標系統可以用來繪製 QR 代碼，或將全像位置連接到位置：</span><span class="sxs-lookup"><span data-stu-id="09b25-147">The coordinate system can be used to draw the QR code or attach holograms to the location:</span></span>

```cpp
using namespace winrt::Windows::Perception::Spatial;
using namespace winrt::Windows::Perception::Spatial::Preview;
SpatialCoordinateSystem qrCoordinateSystem = SpatialGraphInteropPreview::CreateCoordinateSystemForNode(code.SpatialGraphNodeId());
```

<span data-ttu-id="09b25-148">您的 *QRCodeAddedHandler* 會完全看起來像這樣：</span><span class="sxs-lookup"><span data-stu-id="09b25-148">Altogether, your *QRCodeAddedHandler* may look something like this:</span></span>

```cpp
void MyApplication::OnAddedQRCode(const QRCodeAddedEventArgs& args)
{
    QRCode code = args.Code();
    std::vector<float3> qrVertices = CreateRectangle(code.PhysicalSideLength(), code.PhysicalSideLength());
    std::vector<unsigned short> qrCodeIndices = TriangulatePoints(qrVertices);
    XMFLOAT3 qrAreaColor = XMFLOAT3(DirectX::Colors::Aqua);

    SpatialCoordinateSystem qrCoordinateSystem = SpatialGraphInteropPreview::CreateCoordinateSystemForNode(code.SpatialGraphNodeId());
    std::shared_ptr<SceneObject> m_qrShape =
        std::make_shared<SceneObject>(
            m_deviceResources,
            qrVertices,
            qrCodeIndices,
            qrAreaColor,
            qrCoordinateSystem);

    m_sceneController->AddSceneObject(m_qrShape);
}
```

## <a name="best-practices-for-qr-code-detection"></a><span data-ttu-id="09b25-149">QR 代碼偵測的最佳作法</span><span class="sxs-lookup"><span data-stu-id="09b25-149">Best practices for QR code detection</span></span>

### <a name="quiet-zones-around-qr-codes"></a><span data-ttu-id="09b25-150">QR 代碼周圍的安靜區域</span><span class="sxs-lookup"><span data-stu-id="09b25-150">Quiet zones around QR Codes</span></span>

<span data-ttu-id="09b25-151">若要正確讀取，QR 代碼需要在程式碼的所有側邊周圍邊界。</span><span class="sxs-lookup"><span data-stu-id="09b25-151">To be read correctly, QR codes require a margin around all sides of the code.</span></span> <span data-ttu-id="09b25-152">此邊界不得包含任何列印的內容，而且應該是四個模組 (程式碼) 寬的單一黑色方塊。</span><span class="sxs-lookup"><span data-stu-id="09b25-152">This margin must not contain any printed content and should be four modules (a single black square in the code) wide.</span></span> 

<span data-ttu-id="09b25-153">[QR 規格](https://www.qrcode.com/en/howto/code.html)包含有關安靜區域的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="09b25-153">The [QR spec](https://www.qrcode.com/en/howto/code.html) contains more information about quiet zones.</span></span>

### <a name="lighting-and-backdrop"></a><span data-ttu-id="09b25-154">光源和底圖</span><span class="sxs-lookup"><span data-stu-id="09b25-154">Lighting and backdrop</span></span>
<span data-ttu-id="09b25-155">QR 代碼偵測品質很容易受到不同的照明和背景影響。</span><span class="sxs-lookup"><span data-stu-id="09b25-155">QR code detection quality is susceptible to varying illumination and backdrop.</span></span> 

<span data-ttu-id="09b25-156">在具有亮光源的場景中，列印灰色背景上的黑色程式碼。</span><span class="sxs-lookup"><span data-stu-id="09b25-156">In a scene with bright lighting, print a code that is black on a gray background.</span></span> <span data-ttu-id="09b25-157">否則，請在白色背景列印黑色 QR 代碼。</span><span class="sxs-lookup"><span data-stu-id="09b25-157">Otherwise, print a black QR code on a white background.</span></span>

<span data-ttu-id="09b25-158">如果程式碼的背景為深色，如果您的偵測速率很低，請嘗試黑色的灰色程式碼。</span><span class="sxs-lookup"><span data-stu-id="09b25-158">If the backdrop to the code is dark, try a black on gray code if your detection rate is low.</span></span> <span data-ttu-id="09b25-159">如果背景相對較輕，則一般程式碼應該會正常運作。</span><span class="sxs-lookup"><span data-stu-id="09b25-159">If the backdrop is relatively light, a regular code should work fine.</span></span>

### <a name="size-of-qr-codes"></a><span data-ttu-id="09b25-160">QR 代碼的大小</span><span class="sxs-lookup"><span data-stu-id="09b25-160">Size of QR codes</span></span>
<span data-ttu-id="09b25-161">Windows Mixed Reality 裝置無法處理每個邊小於 5 cm 的 QR 代碼。</span><span class="sxs-lookup"><span data-stu-id="09b25-161">Windows Mixed Reality devices don't work with QR codes with sides smaller than 5 cm each.</span></span>

<span data-ttu-id="09b25-162">若為 5 cm 到 10-cm 長度之間的 QR 代碼，您必須非常接近偵測程式碼。</span><span class="sxs-lookup"><span data-stu-id="09b25-162">For QR codes between 5 cm and 10-cm length sides, you must be fairly close to detect the code.</span></span> <span data-ttu-id="09b25-163">也需要較長的時間來偵測這種大小的代碼。</span><span class="sxs-lookup"><span data-stu-id="09b25-163">It will also take longer to detect codes at this size.</span></span> 

<span data-ttu-id="09b25-164">偵測程式碼的確切時間，不只取決於 QR 代碼的大小，也不只是您離開程式碼的程度。</span><span class="sxs-lookup"><span data-stu-id="09b25-164">The exact time to detect codes depends not only on the size of the QR codes, but how far you're away from the code.</span></span> <span data-ttu-id="09b25-165">移動較接近程式碼將有助於彌補大小問題。</span><span class="sxs-lookup"><span data-stu-id="09b25-165">Moving closer to the code will help offset issues with size.</span></span>

### <a name="distance-and-angular-position-from-the-qr-code"></a><span data-ttu-id="09b25-166">QR 代碼的距離和角度位置</span><span class="sxs-lookup"><span data-stu-id="09b25-166">Distance and angular position from the QR code</span></span>
<span data-ttu-id="09b25-167">追蹤攝影機只能偵測特定層級的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="09b25-167">The tracking cameras can only detect a certain level of detail.</span></span> <span data-ttu-id="09b25-168">針對較小的程式碼-< 10 cm 的側邊，您必須非常接近。</span><span class="sxs-lookup"><span data-stu-id="09b25-168">For small codes - < 10 cm along the sides - you must be fairly close.</span></span> <span data-ttu-id="09b25-169">針對第1版的 QR 代碼，從 10 cm 到 25 cm 寬的不同，最小偵測距離的範圍是從0.15 計量到0.5 計量。</span><span class="sxs-lookup"><span data-stu-id="09b25-169">For a version 1 QR code varying from 10 cm to 25 cm wide, the minimum detection distance ranges from 0.15 meters to 0.5 meters.</span></span> 

<span data-ttu-id="09b25-170">大小的偵測距離會以線性方式增加，但也取決於 QR 版本或模組大小。</span><span class="sxs-lookup"><span data-stu-id="09b25-170">The detection distance for size increases linearly, but also depends on QR version or module size.</span></span> <span data-ttu-id="09b25-171">版本愈高，模組愈小，只可從較接近的位置偵測到。</span><span class="sxs-lookup"><span data-stu-id="09b25-171">The higher the version, the smaller the modules, which can only be detected from a closer position.</span></span> <span data-ttu-id="09b25-172">如果您想要讓偵測的距離變長，您也可以嘗試微型 QR 代碼。</span><span class="sxs-lookup"><span data-stu-id="09b25-172">You can also try micro QR codes if you want the distance of detection to be longer.</span></span> <span data-ttu-id="09b25-173">QR 偵測適用于一系列的角度 + = 45 度，以確保我們具有適當的解析度來偵測程式碼。</span><span class="sxs-lookup"><span data-stu-id="09b25-173">QR detection works with a range of angles += 45 deg to ensure we have proper resolution to detect the code.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="09b25-174">請務必確定您有足夠的對比和適當的框線。</span><span class="sxs-lookup"><span data-stu-id="09b25-174">Always make sure you have enough contrast and a proper border.</span></span>

### <a name="qr-codes-with-logos"></a><span data-ttu-id="09b25-175">具有標誌的 QR 代碼</span><span class="sxs-lookup"><span data-stu-id="09b25-175">QR codes with logos</span></span>
<span data-ttu-id="09b25-176">具有標誌的 QR 代碼尚未經過測試，且目前不受支援。</span><span class="sxs-lookup"><span data-stu-id="09b25-176">QR codes with logos haven't been tested and are currently unsupported.</span></span>

### <a name="managing-qr-code-data"></a><span data-ttu-id="09b25-177">管理 QR 代碼資料</span><span class="sxs-lookup"><span data-stu-id="09b25-177">Managing QR code data</span></span>
<span data-ttu-id="09b25-178">Windows Mixed Reality 裝置會在驅動程式中偵測系統層級的 QR 代碼。</span><span class="sxs-lookup"><span data-stu-id="09b25-178">Windows Mixed Reality devices detect QR codes at the system level in the driver.</span></span> <span data-ttu-id="09b25-179">當裝置重新開機時，偵測到的 QR 代碼將會消失，並且會在下一次重新檢測為新物件。</span><span class="sxs-lookup"><span data-stu-id="09b25-179">When the device is rebooted, the detected QR codes are gone and will be redetected as new objects next time.</span></span>

<span data-ttu-id="09b25-180">建議您將應用程式設定為略過超過特定時間戳記的 QR 代碼。</span><span class="sxs-lookup"><span data-stu-id="09b25-180">We recommend configuring your app to ignore QR codes older than a specific timestamp.</span></span> <span data-ttu-id="09b25-181">目前，API 不支援清除 QR 代碼歷程記錄。</span><span class="sxs-lookup"><span data-stu-id="09b25-181">Currently, the API doesn't support clearing QR code history.</span></span>

### <a name="qr-code-placement-in-a-space"></a><span data-ttu-id="09b25-182">將 QR 代碼放置在空間中</span><span class="sxs-lookup"><span data-stu-id="09b25-182">QR code placement in a space</span></span>
<span data-ttu-id="09b25-183">如需在何處及如何放置 QR 代碼的建議，請參閱 [HoloLens 的環境考慮](/hololens/hololens-environment-considerations)。</span><span class="sxs-lookup"><span data-stu-id="09b25-183">For recommendations on where and how to place QR codes, refer to [Environment considerations for HoloLens](/hololens/hololens-environment-considerations).</span></span>

## <a name="qr-api-reference"></a><span data-ttu-id="09b25-184">QR API 參考</span><span class="sxs-lookup"><span data-stu-id="09b25-184">QR API reference</span></span>

```cs
namespace Microsoft.MixedReality.QR
{
    /// <summary>
    /// Represents a detected QR code.
    /// </remarks>
    public class QRCode
    {
        /// <summary>
        /// Unique id that identifies this QR code for this session.
        /// </summary>
        public Guid Id { get; }

        /// <summary>
        /// Spatial graph node id for this QR code to create a coordinate system.
        /// </summary>
        public Guid SpatialGraphNodeId { get; }

        /// <summary>
        /// Version of this QR code. Version 1-40 are regular QR codes and M1 to M4 are Micro QR code formats 1-4.
        /// </summary>
        public QRVersion Version { get; }

        /// <summary>
        /// Physical width and height of this QR code in meters.
        /// </summary>
        public float PhysicalSideLength { get; }

        /// <summary>
        /// Decoded QR code data.
        /// </summary>
        public String Data { get; }

        /// <summary>
        /// Size of the RawData of this QR code.
        /// </summary>
        public UInt32 RawDataSize { get; }

        /// <summary>
        /// Gets the error-corrected raw data bytes.
        /// Used when the platform is unable to decode the code's format,
        /// allowing your app to decode as needed.
        /// </summary>
        public void GetRawData(byte[] buffer);

        /// <summary>
        /// The last detected time in 100ns QPC ticks.
        /// </summary>
        public System.TimeSpan SystemRelativeLastDetectedTime { get; }

        /// <summary>
        /// The last detected time.
        /// </summary>
        public System.DateTimeOffset LastDetectedTime { get; }
    }

    /// <summary>
    /// Event arguments for a QRCodeWatcher's Added event.
    /// </summary>
    public class QRCodeAddedEventArgs
    {
        /// <summary>
        /// Gets the QR Code that was added
        /// </summary>
        public QRCode Code { get; }
    }

    /// <summary>
    /// Event arguments for a QRCodeWatcher's Removed event.
    /// </summary>
    public class QRCodeRemovedEventArgs
    {
        /// <summary>
        /// Gets the QR Code that was removed.
        /// </summary>
        public QRCode Code { get; }
    }

    /// <summary>
    /// Event arguments for a QRCodeWatcher's Updated event.
    /// </summary>
    public class QRCodeUpdatedEventArgs
    {
        /// <summary>
        /// Gets the QR Code that was updated.
        /// </summary>
        public QRCode Code { get; }
    }

    /// <summary>
    /// Represents the status of an access request for QR code detection.
    /// </summary>
    public enum QRCodeWatcherAccessStatus
    {
        /// <summary>
        /// The system has denied permission for the app to detect QR codes.
        /// </summary>
        DeniedBySystem = 0,
        /// <summary>
        /// The app has not declared the webcam capability in its manifest.
        /// </summary>
        NotDeclaredByApp = 1,
        /// <summary>
        /// The user has denied permission for the app to detect QR codes.
        /// </summary>
        DeniedByUser = 2,
        /// <summary>
        /// A user prompt is required to get permission to detect QR codes.
        /// </summary>
        UserPromptRequired = 3,
        /// <summary>
        /// The user has given permission to detect QR codes.
        /// </summary>
        Allowed = 4,
    }

    /// <summary>
    /// Detects QR codes in the user's environment.
    /// </summary>
    public class QRCodeWatcher
    {
        /// <summary>
        /// Gets whether QR code detection is supported on the current device.
        /// </summary>
        public static bool IsSupported();

        /// <summary>
        /// Request user consent before using QR code detection.
        /// </summary>
        public static IAsyncOperation<QRCodeWatcherAccessStatus> RequestAccessAsync();

        /// <summary>
        /// Constructs a new QRCodeWatcher.
        /// </summary>
        public QRCodeWatcher();

        /// <summary>
        /// Starts detecting QR codes.
        /// </summary>
        /// <remarks>
        /// Start should only be called once RequestAccessAsync has succeeded.
        /// Start should not be called if QR code detection is not supported.
        /// Check that IsSupported returns true before calling Start.
        /// </remarks>
        public void Start();

        /// <summary>
        /// Stops detecting QR codes.
        /// </summary>
        public void Stop();

        /// <summary>
        /// Get the list of QR codes detected.
        /// </summary>
        /// <remarks>
        /// </remarks>
        public IList<QRCode> GetList();

        /// <summary>
        /// Event representing the addition of a QR Code.
        /// </summary>
        public event EventHandler<QRCodeAddedEventArgs> Added;

        /// <summary>
        /// Event representing the removal of a QR Code.
        /// </summary>
        public event EventHandler<QRCodeRemovedEventArgs> Removed;

        /// <summary>
        /// Event representing the update of a QR Code.
        /// </summary>
        public event EventHandler<QRCodeUpdatedEventArgs> Updated;

        /// <summary>
        /// Event representing the enumeration of QR Codes completing after a Start call.
        /// </summary>
        public event EventHandler<Object> EnumerationCompleted;
    }

    /// <summary>
    /// Version info for QR codes, including Micro QR codes.
    /// </summary>
    public enum QRVersion
    {
        QR1 = 1,
        QR2 = 2,
        QR3 = 3,
        QR4 = 4,
        QR5 = 5,
        QR6 = 6,
        QR7 = 7,
        QR8 = 8,
        QR9 = 9,
        QR10 = 10,
        QR11 = 11,
        QR12 = 12,
        QR13 = 13,
        QR14 = 14,
        QR15 = 15,
        QR16 = 16,
        QR17 = 17,
        QR18 = 18,
        QR19 = 19,
        QR20 = 20,
        QR21 = 21,
        QR22 = 22,
        QR23 = 23,
        QR24 = 24,
        QR25 = 25,
        QR26 = 26,
        QR27 = 27,
        QR28 = 28,
        QR29 = 29,
        QR30 = 30,
        QR31 = 31,
        QR32 = 32,
        QR33 = 33,
        QR34 = 34,
        QR35 = 35,
        QR36 = 36,
        QR37 = 37,
        QR38 = 38,
        QR39 = 39,
        QR40 = 40,
        MicroQRM1 = 41,
        MicroQRM2 = 42,
        MicroQRM3 = 43,
        MicroQRM4 = 44,
    }
}
```

## <a name="see-also"></a><span data-ttu-id="09b25-185">另請參閱</span><span class="sxs-lookup"><span data-stu-id="09b25-185">See also</span></span>
* [<span data-ttu-id="09b25-186">座標系統</span><span class="sxs-lookup"><span data-stu-id="09b25-186">Coordinate systems</span></span>](../../design/coordinate-systems.md)
* <span data-ttu-id="09b25-187"><a href="/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a></span><span class="sxs-lookup"><span data-stu-id="09b25-187"><a href="/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a></span></span>