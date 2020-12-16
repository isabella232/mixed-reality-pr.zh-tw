---
title: QR 代碼追蹤
description: 瞭解如何在 HoloLens 2 上偵測 QR 代碼。
author: dorreneb
ms.author: dobrown
ms.date: 05/15/2019
ms.topic: article
keywords: vr、lbe、以位置為基礎的娛樂、vr arcade、arcade、沉浸式、qr、qr 代碼、hololens2
ms.openlocfilehash: 023da7a98d1559d9dd0387a7efbaf26ad577df50
ms.sourcegitcommit: c41372e0c6ca265f599bff309390982642d628b8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/15/2020
ms.locfileid: "97530008"
---
# <a name="qr-code-tracking"></a><span data-ttu-id="4f3ae-104">QR 代碼追蹤</span><span class="sxs-lookup"><span data-stu-id="4f3ae-104">QR code tracking</span></span>

<span data-ttu-id="4f3ae-105">HoloLens 2 可以偵測頭戴式裝置周圍環境中的 QR 代碼，而在每個代碼的真實世界位置建立座標系統。</span><span class="sxs-lookup"><span data-stu-id="4f3ae-105">HoloLens 2 can detect QR codes in the environment around the headset, establishing a coordinate system at each code's real-world location.</span></span>

## <a name="device-support"></a><span data-ttu-id="4f3ae-106">裝置支援</span><span class="sxs-lookup"><span data-stu-id="4f3ae-106">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="4f3ae-107">功能</span><span class="sxs-lookup"><span data-stu-id="4f3ae-107">Feature</span></span></th><th style="width:150px"> <span data-ttu-id="4f3ae-108"><a href="../../hololens-hardware-details.md">HoloLens (第一代) </a></span><span class="sxs-lookup"><span data-stu-id="4f3ae-108"><a href="../../hololens-hardware-details.md">HoloLens (first gen)</a></span></span></th><th style="width:150px"><span data-ttu-id="4f3ae-109">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="4f3ae-109">HoloLens 2</span></span></th><th style="width:150px"> <span data-ttu-id="4f3ae-110"><a href="../../discover/immersive-headset-hardware-details.md">沉浸式頭戴裝置</a></span><span class="sxs-lookup"><span data-stu-id="4f3ae-110"><a href="../../discover/immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="4f3ae-111">QR 代碼偵測</span><span class="sxs-lookup"><span data-stu-id="4f3ae-111">QR code detection</span></span></td><td style="text-align: center;"><span data-ttu-id="4f3ae-112">️</span><span class="sxs-lookup"><span data-stu-id="4f3ae-112">️</span></span></td><td style="text-align: center;"> <span data-ttu-id="4f3ae-113">✔️</span><span class="sxs-lookup"><span data-stu-id="4f3ae-113">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="4f3ae-114">✔️</span><span class="sxs-lookup"><span data-stu-id="4f3ae-114">✔️</span></span></td>
</tr>
</table>

>[!NOTE]
><span data-ttu-id="4f3ae-115">Windows 10 2004 版和更高版本支援在桌上型電腦上使用沉浸式 Windows Mixed Reality 耳機進行 QR 代碼追蹤。</span><span class="sxs-lookup"><span data-stu-id="4f3ae-115">QR code tracking with immersive Windows Mixed Reality headsets on desktop PCs is supported on Windows 10 Version 2004 and higher.</span></span> <span data-ttu-id="4f3ae-116">使用 MixedReality. QRCodeWatcher. IsSupported ( # A1 API 來判斷目前的裝置是否支援此功能。</span><span class="sxs-lookup"><span data-stu-id="4f3ae-116">Use the Microsoft.MixedReality.QRCodeWatcher.IsSupported() API to determine whether the feature is supported on the current device.</span></span>

## <a name="getting-the-qr-package"></a><span data-ttu-id="4f3ae-117">取得 QR 套件</span><span class="sxs-lookup"><span data-stu-id="4f3ae-117">Getting the QR package</span></span>

<span data-ttu-id="4f3ae-118">您可以在 [這裡](https://nuget.org/Packages/Microsoft.MixedReality.QR)下載適用于 QR 代碼偵測的 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="4f3ae-118">You can download the NuGet package for QR code detection [here](https://nuget.org/Packages/Microsoft.MixedReality.QR).</span></span>

## <a name="detecting-qr-codes"></a><span data-ttu-id="4f3ae-119">偵測 QR 代碼</span><span class="sxs-lookup"><span data-stu-id="4f3ae-119">Detecting QR codes</span></span>

### <a name="adding-the-webcam-capability"></a><span data-ttu-id="4f3ae-120">新增網路攝影機功能</span><span class="sxs-lookup"><span data-stu-id="4f3ae-120">Adding the webcam capability</span></span>

<span data-ttu-id="4f3ae-121">您必須將功能新增 `webcam` 至您的資訊清單，以偵測 QR 代碼。</span><span class="sxs-lookup"><span data-stu-id="4f3ae-121">You'll need to add the capability `webcam` to your manifest to detect QR codes.</span></span> <span data-ttu-id="4f3ae-122">這項功能是必要的，因為使用者環境中偵測到的程式碼內的資料可能包含機密資訊。</span><span class="sxs-lookup"><span data-stu-id="4f3ae-122">This capability is required as the data within detected codes in the user's environment may contain sensitive information.</span></span>

<span data-ttu-id="4f3ae-123">您可以呼叫下列方法來要求許可權 `QRCodeWatcher.RequestAccessAsync()` ：</span><span class="sxs-lookup"><span data-stu-id="4f3ae-123">Permission can be requested by calling `QRCodeWatcher.RequestAccessAsync()`:</span></span>

<span data-ttu-id="4f3ae-124">_C#：_</span><span class="sxs-lookup"><span data-stu-id="4f3ae-124">_C#:_</span></span>
```cs
await QRCodeWatcher.RequestAccessAsync();
```

<span data-ttu-id="4f3ae-125">_C++：_</span><span class="sxs-lookup"><span data-stu-id="4f3ae-125">_C++:_</span></span>
```cpp
co_await QRCodeWatcher.RequestAccessAsync();
```

<span data-ttu-id="4f3ae-126">在您建立 QRCodeWatcher 物件之前，必須先要求許可權。</span><span class="sxs-lookup"><span data-stu-id="4f3ae-126">Permission must be requested before you construct a QRCodeWatcher object.</span></span>

<span data-ttu-id="4f3ae-127">當 QR 代碼偵測需要這項 `webcam` 功能時，會使用裝置的追蹤攝影機進行偵測。</span><span class="sxs-lookup"><span data-stu-id="4f3ae-127">While QR code detection requires the `webcam` capability, the detection occurs using the device's tracking cameras.</span></span> <span data-ttu-id="4f3ae-128">相較于使用裝置的相片/影片 (PV) 攝影機的偵測，這可提供更廣泛的偵測 FOV 和較佳的電池壽命。</span><span class="sxs-lookup"><span data-stu-id="4f3ae-128">This provides a wider detection FOV and better battery life compared to detection with the device's photo/video (PV) camera.</span></span>

### <a name="detecting-qr-codes-in-unity"></a><span data-ttu-id="4f3ae-129">在 Unity 中偵測 QR 代碼</span><span class="sxs-lookup"><span data-stu-id="4f3ae-129">Detecting QR codes in Unity</span></span>

<span data-ttu-id="4f3ae-130">您可以在 Unity 中使用 QR 代碼偵測 API，而不需要匯入 MRTK，方法是使用 [nuget For Unity](https://github.com/GlitchEnzo/NuGetForUnity)安裝 nuget 套件。</span><span class="sxs-lookup"><span data-stu-id="4f3ae-130">You can use the QR code detection API in Unity without importing MRTK by installing the NuGet package using [NuGet for Unity](https://github.com/GlitchEnzo/NuGetForUnity).</span></span> <span data-ttu-id="4f3ae-131">如果您想要瞭解其運作方式，請下載 [範例 Unity 應用程式](https://github.com/chgatla-microsoft/QRTracking/tree/master/SampleQRCodes)。</span><span class="sxs-lookup"><span data-stu-id="4f3ae-131">If you want to get a feel for how it works, download the [sample Unity app](https://github.com/chgatla-microsoft/QRTracking/tree/master/SampleQRCodes).</span></span> <span data-ttu-id="4f3ae-132">範例應用程式中的範例會顯示 QR 代碼的全像正方形，以及相關聯的資料，例如 GUID、實體大小、時間戳記和已解碼的資料。</span><span class="sxs-lookup"><span data-stu-id="4f3ae-132">The sample app has examples for displaying a holographic square over QR codes and associated data such as GUID, physical size, timestamp, and decoded data.</span></span>

### <a name="detecting-qr-codes-in-c"></a><span data-ttu-id="4f3ae-133">在 c + + 中偵測 QR 代碼</span><span class="sxs-lookup"><span data-stu-id="4f3ae-133">Detecting QR codes in C++</span></span>

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

## <a name="getting-the-coordinate-system-for-a-qr-code"></a><span data-ttu-id="4f3ae-134">取得 QR 代碼的座標系統</span><span class="sxs-lookup"><span data-stu-id="4f3ae-134">Getting the coordinate system for a QR code</span></span>

<span data-ttu-id="4f3ae-135">每個偵測到的 QR 代碼都會公開 [空間座標系統](../../design/coordinate-systems.md) ，此系統會對齊左上角的 QR 代碼，位於左上角的快速偵測方塊左上角：</span><span class="sxs-lookup"><span data-stu-id="4f3ae-135">Each detected QR code exposes a [spatial coordinate system](../../design/coordinate-systems.md) aligned with the QR code at the top-left corner of the fast detection square in the top left:</span></span>  

![QR 代碼座標系統](images/Qr-coordinatesystem.png) 

<span data-ttu-id="4f3ae-137">當直接使用 QR SDK 時，Z 軸會指向紙張 (不會顯示) -轉換成 Unity 座標時，Z 軸會指向紙張，並會被左手。</span><span class="sxs-lookup"><span data-stu-id="4f3ae-137">When directly using the QR SDK, the Z-axis is pointing into the paper (not shown) - when converted into Unity coordinates, the Z-axis points out of the paper and is left-handed.</span></span>

<span data-ttu-id="4f3ae-138">QR 代碼的 SpatialCoordinateSystem 會對齊，如下所示。</span><span class="sxs-lookup"><span data-stu-id="4f3ae-138">A QR code's SpatialCoordinateSystem aligns as shown.</span></span> <span data-ttu-id="4f3ae-139">您可以藉由呼叫 <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.createcoordinatesystemfornode" target="_blank">SpatialGraphInteropPreview：： CreateCoordinateSystemForNode</a> 並傳入程式碼的 SpatialGraphNodeId，從平臺取得座標系統。</span><span class="sxs-lookup"><span data-stu-id="4f3ae-139">You can get the coordinate system from the platform by calling <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.createcoordinatesystemfornode" target="_blank">SpatialGraphInteropPreview::CreateCoordinateSystemForNode</a> and passing in the code's SpatialGraphNodeId.</span></span>

<span data-ttu-id="4f3ae-140">下列 c + + 程式碼顯示如何建立矩形，並使用 QR 代碼的座標系統來放置它：</span><span class="sxs-lookup"><span data-stu-id="4f3ae-140">The C++ code below shows how to create a rectangle and place it using the QR code's coordinate system:</span></span>

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

<span data-ttu-id="4f3ae-141">您可以使用實體大小來建立 QR 矩形：</span><span class="sxs-lookup"><span data-stu-id="4f3ae-141">You can use the physical size to create the QR rectangle:</span></span>

```cpp
std::vector<float3> qrVertices = CreateRectangle(code.PhysicalSideLength(), code.PhysicalSideLength()); 
```

<span data-ttu-id="4f3ae-142">座標系統可以用來繪製 QR 代碼，或將全像位置連接到位置：</span><span class="sxs-lookup"><span data-stu-id="4f3ae-142">The coordinate system can be used to draw the QR code or attach holograms to the location:</span></span>

```cpp
using namespace winrt::Windows::Perception::Spatial;
using namespace winrt::Windows::Perception::Spatial::Preview;
SpatialCoordinateSystem qrCoordinateSystem = SpatialGraphInteropPreview::CreateCoordinateSystemForNode(code.SpatialGraphNodeId());
```

<span data-ttu-id="4f3ae-143">您的 *QRCodeAddedHandler* 會完全看起來像這樣：</span><span class="sxs-lookup"><span data-stu-id="4f3ae-143">Altogether, your *QRCodeAddedHandler* may look something like this:</span></span>

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

## <a name="best-practices-for-qr-code-detection"></a><span data-ttu-id="4f3ae-144">QR 代碼偵測的最佳作法</span><span class="sxs-lookup"><span data-stu-id="4f3ae-144">Best practices for QR code detection</span></span>

### <a name="quiet-zones-around-qr-codes"></a><span data-ttu-id="4f3ae-145">QR 代碼周圍的安靜區域</span><span class="sxs-lookup"><span data-stu-id="4f3ae-145">Quiet zones around QR Codes</span></span>

<span data-ttu-id="4f3ae-146">若要正確讀取，QR 代碼需要在程式碼的所有側邊周圍邊界。</span><span class="sxs-lookup"><span data-stu-id="4f3ae-146">To be read correctly, QR codes require a margin around all sides of the code.</span></span> <span data-ttu-id="4f3ae-147">此邊界不得包含任何列印的內容，而且應該是四個模組 (程式碼) 寬的單一黑色方塊。</span><span class="sxs-lookup"><span data-stu-id="4f3ae-147">This margin must not contain any printed content and should be four modules (a single black square in the code) wide.</span></span> 

<span data-ttu-id="4f3ae-148">[QR 規格](https://www.qrcode.com/en/howto/code.html)包含有關安靜區域的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="4f3ae-148">The [QR spec](https://www.qrcode.com/en/howto/code.html) contains more information about quiet zones.</span></span>

### <a name="lighting-and-backdrop"></a><span data-ttu-id="4f3ae-149">光源和底圖</span><span class="sxs-lookup"><span data-stu-id="4f3ae-149">Lighting and backdrop</span></span>
<span data-ttu-id="4f3ae-150">QR 代碼偵測品質很容易受到不同的照明和背景影響。</span><span class="sxs-lookup"><span data-stu-id="4f3ae-150">QR code detection quality is susceptible to varying illumination and backdrop.</span></span> 

<span data-ttu-id="4f3ae-151">在具有亮光源的場景中，列印灰色背景上的黑色程式碼。</span><span class="sxs-lookup"><span data-stu-id="4f3ae-151">In a scene with bright lighting, print a code that is black on a gray background.</span></span> <span data-ttu-id="4f3ae-152">否則，請在白色背景列印黑色 QR 代碼。</span><span class="sxs-lookup"><span data-stu-id="4f3ae-152">Otherwise, print a black QR code on a white background.</span></span>

<span data-ttu-id="4f3ae-153">如果程式碼的背景為深色，如果您的偵測速率很低，請嘗試黑色的灰色程式碼。</span><span class="sxs-lookup"><span data-stu-id="4f3ae-153">If the backdrop to the code is dark, try a black on gray code if your detection rate is low.</span></span> <span data-ttu-id="4f3ae-154">如果背景相對較輕，則一般程式碼應該會正常運作。</span><span class="sxs-lookup"><span data-stu-id="4f3ae-154">If the backdrop is relatively light, a regular code should work fine.</span></span>

### <a name="size-of-qr-codes"></a><span data-ttu-id="4f3ae-155">QR 代碼的大小</span><span class="sxs-lookup"><span data-stu-id="4f3ae-155">Size of QR codes</span></span>
<span data-ttu-id="4f3ae-156">Windows Mixed Reality 裝置無法處理每個邊小於 5 cm 的 QR 代碼。</span><span class="sxs-lookup"><span data-stu-id="4f3ae-156">Windows Mixed Reality devices don't work with QR codes with sides smaller than 5 cm each.</span></span>

<span data-ttu-id="4f3ae-157">若為 5 cm 到 10-cm 長度之間的 QR 代碼，您必須非常接近偵測程式碼。</span><span class="sxs-lookup"><span data-stu-id="4f3ae-157">For QR codes between 5 cm and 10-cm length sides, you must be fairly close to detect the code.</span></span> <span data-ttu-id="4f3ae-158">也需要較長的時間來偵測這種大小的代碼。</span><span class="sxs-lookup"><span data-stu-id="4f3ae-158">It will also take longer to detect codes at this size.</span></span> 

<span data-ttu-id="4f3ae-159">偵測程式碼的確切時間，不只取決於 QR 代碼的大小，也不只是您離開程式碼的程度。</span><span class="sxs-lookup"><span data-stu-id="4f3ae-159">The exact time to detect codes depends not only on the size of the QR codes, but how far you're away from the code.</span></span> <span data-ttu-id="4f3ae-160">移動較接近程式碼將有助於彌補大小問題。</span><span class="sxs-lookup"><span data-stu-id="4f3ae-160">Moving closer to the code will help offset issues with size.</span></span>

### <a name="distance-and-angular-position-from-the-qr-code"></a><span data-ttu-id="4f3ae-161">QR 代碼的距離和角度位置</span><span class="sxs-lookup"><span data-stu-id="4f3ae-161">Distance and angular position from the QR code</span></span>
<span data-ttu-id="4f3ae-162">追蹤攝影機只能偵測特定層級的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="4f3ae-162">The tracking cameras can only detect a certain level of detail.</span></span> <span data-ttu-id="4f3ae-163">針對較小的程式碼-< 10 cm 的側邊，您必須非常接近。</span><span class="sxs-lookup"><span data-stu-id="4f3ae-163">For small codes - < 10 cm along the sides - you must be fairly close.</span></span> <span data-ttu-id="4f3ae-164">針對第1版的 QR 代碼，從 10 cm 到 25 cm 寬的不同，最小偵測距離的範圍是從0.15 計量到0.5 計量。</span><span class="sxs-lookup"><span data-stu-id="4f3ae-164">For a version 1 QR code varying from 10 cm to 25 cm wide, the minimum detection distance ranges from 0.15 meters to 0.5 meters.</span></span> 

<span data-ttu-id="4f3ae-165">大小的偵測距離會以線性方式增加。</span><span class="sxs-lookup"><span data-stu-id="4f3ae-165">The detection distance for size increases linearly.</span></span> 

<span data-ttu-id="4f3ae-166">QR 偵測適用于一系列的角度 + = 45 度，以確保我們具有適當的解析度來偵測程式碼。</span><span class="sxs-lookup"><span data-stu-id="4f3ae-166">QR detection works with a range of angles += 45 deg to ensure we have proper resolution to detect the code.</span></span>

### <a name="qr-codes-with-logos"></a><span data-ttu-id="4f3ae-167">具有標誌的 QR 代碼</span><span class="sxs-lookup"><span data-stu-id="4f3ae-167">QR codes with logos</span></span>
<span data-ttu-id="4f3ae-168">具有標誌的 QR 代碼尚未經過測試，且目前不受支援。</span><span class="sxs-lookup"><span data-stu-id="4f3ae-168">QR codes with logos haven't been tested and are currently unsupported.</span></span>

### <a name="managing-qr-code-data"></a><span data-ttu-id="4f3ae-169">管理 QR 代碼資料</span><span class="sxs-lookup"><span data-stu-id="4f3ae-169">Managing QR code data</span></span>
<span data-ttu-id="4f3ae-170">Windows Mixed Reality 裝置會在驅動程式中偵測系統層級的 QR 代碼。</span><span class="sxs-lookup"><span data-stu-id="4f3ae-170">Windows Mixed Reality devices detect QR codes at the system level in the driver.</span></span> <span data-ttu-id="4f3ae-171">當裝置重新開機時，偵測到的 QR 代碼將會消失，並且會在下一次重新檢測為新物件。</span><span class="sxs-lookup"><span data-stu-id="4f3ae-171">When the device is rebooted, the detected QR codes are gone and will be redetected as new objects next time.</span></span>

<span data-ttu-id="4f3ae-172">建議您將應用程式設定為略過超過特定時間戳記的 QR 代碼。</span><span class="sxs-lookup"><span data-stu-id="4f3ae-172">We recommend configuring your app to ignore QR codes older than a specific timestamp.</span></span> <span data-ttu-id="4f3ae-173">目前，API 不支援清除 QR 代碼歷程記錄。</span><span class="sxs-lookup"><span data-stu-id="4f3ae-173">Currently, the API doesn't support clearing QR code history.</span></span>

### <a name="qr-code-placement-in-a-space"></a><span data-ttu-id="4f3ae-174">將 QR 代碼放置在空間中</span><span class="sxs-lookup"><span data-stu-id="4f3ae-174">QR code placement in a space</span></span>
<span data-ttu-id="4f3ae-175">如需在何處及如何放置 QR 代碼的建議，請參閱 [HoloLens 的環境考慮](../../environment-considerations-for-hololens.md)。</span><span class="sxs-lookup"><span data-stu-id="4f3ae-175">For recommendations on where and how to place QR codes, refer to [Environment considerations for HoloLens](../../environment-considerations-for-hololens.md).</span></span>

## <a name="qr-api-reference"></a><span data-ttu-id="4f3ae-176">QR API 參考</span><span class="sxs-lookup"><span data-stu-id="4f3ae-176">QR API reference</span></span>

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

## <a name="see-also"></a><span data-ttu-id="4f3ae-177">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4f3ae-177">See also</span></span>
* [<span data-ttu-id="4f3ae-178">座標系統</span><span class="sxs-lookup"><span data-stu-id="4f3ae-178">Coordinate systems</span></span>](../../design/coordinate-systems.md)
* <span data-ttu-id="4f3ae-179"><a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a></span><span class="sxs-lookup"><span data-stu-id="4f3ae-179"><a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a></span></span>
