---
title: QR 代碼追蹤
description: 瞭解如何在 HoloLens 2 上偵測 QR 代碼。
author: dorreneb
ms.author: dobrown
ms.date: 05/15/2019
ms.topic: article
keywords: vr、lbe、以位置為基礎的娛樂、vr arcade、arcade、沉浸式、qr、qr 代碼、hololens2
ms.openlocfilehash: e7b1f04b51cb1011cd0d66c27fe6a8bff3aafb79
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2020
ms.locfileid: "91679909"
---
# <a name="qr-code-tracking"></a><span data-ttu-id="ec2f6-104">QR 代碼追蹤</span><span class="sxs-lookup"><span data-stu-id="ec2f6-104">QR code tracking</span></span>

<span data-ttu-id="ec2f6-105">HoloLens 2 可以偵測到耳機周圍的 QR 代碼，並在每個程式碼的真實世界位置建立座標系統。</span><span class="sxs-lookup"><span data-stu-id="ec2f6-105">HoloLens 2 can detect QR codes in the environment around the headset, establishing a coordinate system at each code's real-world location.</span></span>

## <a name="device-support"></a><span data-ttu-id="ec2f6-106">裝置支援</span><span class="sxs-lookup"><span data-stu-id="ec2f6-106">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="ec2f6-107">功能</span><span class="sxs-lookup"><span data-stu-id="ec2f6-107">Feature</span></span></th><th style="width:150px"> <span data-ttu-id="ec2f6-108"><a href="../../hololens-hardware-details.md">HoloLens (第 1 代)</a></span><span class="sxs-lookup"><span data-stu-id="ec2f6-108"><a href="../../hololens-hardware-details.md">HoloLens (1st gen)</a></span></span></th><th style="width:150px"><span data-ttu-id="ec2f6-109">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="ec2f6-109">HoloLens 2</span></span></th><th style="width:150px"> <span data-ttu-id="ec2f6-110"><a href="../../discover/immersive-headset-hardware-details.md">沉浸式頭戴裝置</a></span><span class="sxs-lookup"><span data-stu-id="ec2f6-110"><a href="../../discover/immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="ec2f6-111">QR 代碼偵測</span><span class="sxs-lookup"><span data-stu-id="ec2f6-111">QR code detection</span></span></td><td style="text-align: center;"><span data-ttu-id="ec2f6-112">️</span><span class="sxs-lookup"><span data-stu-id="ec2f6-112">️</span></span></td><td style="text-align: center;"> <span data-ttu-id="ec2f6-113">✔️</span><span class="sxs-lookup"><span data-stu-id="ec2f6-113">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="ec2f6-114">✔️</span><span class="sxs-lookup"><span data-stu-id="ec2f6-114">✔️</span></span></td>
</tr>
</table>

>[!NOTE]
><span data-ttu-id="ec2f6-115">Windows 10 2004 版和更高版本支援在桌上型電腦上使用沉浸式 Windows Mixed Reality 耳機進行 QR 代碼追蹤。</span><span class="sxs-lookup"><span data-stu-id="ec2f6-115">QR code tracking with immersive Windows Mixed Reality headsets on desktop PCs is supported on Windows 10 Version 2004 and higher.</span></span> <span data-ttu-id="ec2f6-116">使用 MixedReality. QRCodeWatcher. IsSupported ( # A1 API 來判斷目前的裝置是否支援此功能。</span><span class="sxs-lookup"><span data-stu-id="ec2f6-116">Use the Microsoft.MixedReality.QRCodeWatcher.IsSupported() API to determine whether the feature is supported on the current device.</span></span>

## <a name="getting-the-qr-package"></a><span data-ttu-id="ec2f6-117">取得 QR 套件</span><span class="sxs-lookup"><span data-stu-id="ec2f6-117">Getting the QR package</span></span>
<span data-ttu-id="ec2f6-118">您可以在 [這裡](https://nuget.org/Packages/Microsoft.MixedReality.QR)下載適用于 QR 代碼偵測的 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="ec2f6-118">You can download the NuGet package for QR code detection [here](https://nuget.org/Packages/Microsoft.MixedReality.QR).</span></span>

## <a name="detecting-qr-codes"></a><span data-ttu-id="ec2f6-119">偵測 QR 代碼</span><span class="sxs-lookup"><span data-stu-id="ec2f6-119">Detecting QR codes</span></span>

### <a name="adding-the-webcam-capability"></a><span data-ttu-id="ec2f6-120">新增網路攝影機功能</span><span class="sxs-lookup"><span data-stu-id="ec2f6-120">Adding the webcam capability</span></span>
<span data-ttu-id="ec2f6-121">您必須將功能新增 `webcam` 至您的資訊清單，以偵測 QR 代碼。</span><span class="sxs-lookup"><span data-stu-id="ec2f6-121">You will need to add the capability `webcam` to your manifest to detect QR codes.</span></span> <span data-ttu-id="ec2f6-122">這項功能是必要的，因為使用者環境中偵測到的程式碼內的資料可能包含機密資訊。</span><span class="sxs-lookup"><span data-stu-id="ec2f6-122">This capability is required as the data within detected codes in the user's environment may contain sensitive information.</span></span>

<span data-ttu-id="ec2f6-123">您可以呼叫下列方法來要求許可權 `QRCodeWatcher.RequestAccessAsync()` ：</span><span class="sxs-lookup"><span data-stu-id="ec2f6-123">Permission can be requested by calling `QRCodeWatcher.RequestAccessAsync()`:</span></span>

<span data-ttu-id="ec2f6-124">_C#：_</span><span class="sxs-lookup"><span data-stu-id="ec2f6-124">_C#:_</span></span>
```cs
await QRCodeWatcher.RequestAccessAsync();
```

<span data-ttu-id="ec2f6-125">_C++：_</span><span class="sxs-lookup"><span data-stu-id="ec2f6-125">_C++:_</span></span>
```cpp
co_await QRCodeWatcher.RequestAccessAsync();
```

<span data-ttu-id="ec2f6-126">在您建立 QRCodeWatcher 物件之前，必須先要求許可權。</span><span class="sxs-lookup"><span data-stu-id="ec2f6-126">Permission must be requested before you construct a QRCodeWatcher object.</span></span>

<span data-ttu-id="ec2f6-127">當 QR 代碼偵測需要這項 `webcam` 功能時，會使用裝置的追蹤攝影機進行偵測。</span><span class="sxs-lookup"><span data-stu-id="ec2f6-127">While QR code detection requires the `webcam` capability, the detection occurs using the device's tracking cameras.</span></span> <span data-ttu-id="ec2f6-128">相較于使用裝置的相片/影片 (PV) 攝影機的偵測，這可提供更廣泛的偵測 FOV 和較佳的電池壽命。</span><span class="sxs-lookup"><span data-stu-id="ec2f6-128">This provides a wider detection FOV and better battery life compared to detection with the device's photo/video (PV) camera.</span></span>

### <a name="detecting-qr-codes-in-unity"></a><span data-ttu-id="ec2f6-129">在 Unity 中偵測 QR 代碼</span><span class="sxs-lookup"><span data-stu-id="ec2f6-129">Detecting QR codes in Unity</span></span>

<span data-ttu-id="ec2f6-130">您可以在 Unity 中使用 QR 代碼偵測 API，而不需依賴 MRTK。</span><span class="sxs-lookup"><span data-stu-id="ec2f6-130">You can use the QR code detection API in Unity without taking a dependency on MRTK.</span></span> <span data-ttu-id="ec2f6-131">若要這樣做，您必須使用 [適用于 Unity 的 nuget](https://github.com/GlitchEnzo/NuGetForUnity)來安裝 nuget 套件。</span><span class="sxs-lookup"><span data-stu-id="ec2f6-131">To do so, you must install the NuGet package using [NuGet for Unity](https://github.com/GlitchEnzo/NuGetForUnity).</span></span>

<span data-ttu-id="ec2f6-132">其中有一個範例 Unity 應用程式，可顯示 QR 代碼的全像方塊，以及相關聯的資料，例如 GUID、實體大小、時間戳記和已解碼的資料。</span><span class="sxs-lookup"><span data-stu-id="ec2f6-132">There is a sample Unity app that displays a holographic square over QR codes, along with the associated data such as GUID, physical size, timestamp, and decoded data.</span></span> <span data-ttu-id="ec2f6-133">此應用程式可以位於 https://github.com/chgatla-microsoft/QRTracking/tree/master/SampleQRCodes 。</span><span class="sxs-lookup"><span data-stu-id="ec2f6-133">This app can be located at https://github.com/chgatla-microsoft/QRTracking/tree/master/SampleQRCodes.</span></span>

### <a name="detecting-qr-codes-in-c"></a><span data-ttu-id="ec2f6-134">在 c + + 中偵測 QR 代碼</span><span class="sxs-lookup"><span data-stu-id="ec2f6-134">Detecting QR codes in C++</span></span>

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

## <a name="getting-the-coordinate-system-for-a-qr-code"></a><span data-ttu-id="ec2f6-135">取得 QR 代碼的座標系統</span><span class="sxs-lookup"><span data-stu-id="ec2f6-135">Getting the coordinate system for a QR code</span></span>

<span data-ttu-id="ec2f6-136">每個偵測到的 QR 代碼都會公開 [空間座標系統](../../design/coordinate-systems.md) ，並與左上角的 [快速偵測] 方塊左上角的 QR 代碼保持一致，如下所示。</span><span class="sxs-lookup"><span data-stu-id="ec2f6-136">Each detected QR code exposes a [spatial coordinate system](../../design/coordinate-systems.md) aligned with the QR code at the top left corner of the fast detection square in the top left as seen below.</span></span>  <span data-ttu-id="ec2f6-137">當直接使用 QR SDK 時，Z 軸會指向紙張 (不會顯示) -轉換成 Unity 座標時，Z 軸會指向紙張，並會被左手。</span><span class="sxs-lookup"><span data-stu-id="ec2f6-137">When directly using the QR SDK, the Z-axis is pointing into the paper (not shown) - when converted into Unity coordinates, the Z-axis points out of the paper and is left-handed.</span></span>

<span data-ttu-id="ec2f6-138">QR 代碼的 SpatialCoordinateSystem 會對齊，如下所示。</span><span class="sxs-lookup"><span data-stu-id="ec2f6-138">A QR code's SpatialCoordinateSystem aligns as shown.</span></span> <span data-ttu-id="ec2f6-139">您可以呼叫 <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.createcoordinatesystemfornode" target="_blank">SpatialGraphInteropPreview：： CreateCoordinateSystemForNode</a> ，並傳入程式碼的 SpatialGraphNodeId，以從平臺取得此座標系統。</span><span class="sxs-lookup"><span data-stu-id="ec2f6-139">This coordinate system can be obtained from the platform by calling <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.createcoordinatesystemfornode" target="_blank">SpatialGraphInteropPreview::CreateCoordinateSystemForNode</a> and passing in the code's SpatialGraphNodeId.</span></span>

![QR 代碼座標系統](images/Qr-coordinatesystem.png) 

<span data-ttu-id="ec2f6-141">針對 QRCode 物件，下列 c + + 程式碼會示範如何建立矩形，並使用 QR 代碼的座標系統來放置它：</span><span class="sxs-lookup"><span data-stu-id="ec2f6-141">For a QRCode object, the following C++ code shows how to create a rectangle and place it using the QR code's coordinate system:</span></span>

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

<span data-ttu-id="ec2f6-142">您可以使用實體大小來建立 QR 矩形：</span><span class="sxs-lookup"><span data-stu-id="ec2f6-142">You can use the physical size to create the QR rectangle:</span></span>

```cpp
std::vector<float3> qrVertices = CreateRectangle(code.PhysicalSideLength(), code.PhysicalSideLength()); 
```

<span data-ttu-id="ec2f6-143">座標系統可以用來繪製 QR 代碼，或將全像位置連接到位置：</span><span class="sxs-lookup"><span data-stu-id="ec2f6-143">The coordinate system can be used to draw the QR code or attach holograms to the location:</span></span>

```cpp
using namespace winrt::Windows::Perception::Spatial;
using namespace winrt::Windows::Perception::Spatial::Preview;
SpatialCoordinateSystem qrCoordinateSystem = SpatialGraphInteropPreview::CreateCoordinateSystemForNode(code.SpatialGraphNodeId());
```

<span data-ttu-id="ec2f6-144">您的 *QRCodeAddedHandler* 會完全看起來像這樣：</span><span class="sxs-lookup"><span data-stu-id="ec2f6-144">Altogether, your *QRCodeAddedHandler* may look something like this:</span></span>

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

## <a name="best-practices-for-qr-code-detection"></a><span data-ttu-id="ec2f6-145">QR 代碼偵測的最佳作法</span><span class="sxs-lookup"><span data-stu-id="ec2f6-145">Best practices for QR code detection</span></span>

### <a name="quiet-zones-around-qr-codes"></a><span data-ttu-id="ec2f6-146">QR 代碼周圍的安靜區域</span><span class="sxs-lookup"><span data-stu-id="ec2f6-146">Quiet zones around QR Codes</span></span>

<span data-ttu-id="ec2f6-147">若要正確讀取，QR 代碼需要在程式碼的所有側邊周圍邊界。</span><span class="sxs-lookup"><span data-stu-id="ec2f6-147">To be read correctly, QR codes require a margin around all sides of the code.</span></span> <span data-ttu-id="ec2f6-148">此邊界不得包含任何列印的內容，而且應該是四個模組 (程式碼) 寬的單一黑色方塊。</span><span class="sxs-lookup"><span data-stu-id="ec2f6-148">This margin must not contain any printed content and should be four modules (a single black square in the code) wide.</span></span> 

<span data-ttu-id="ec2f6-149">[QR 規格](https://www.qrcode.com/en/howto/code.html)包含有關安靜區域的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="ec2f6-149">The [QR spec](https://www.qrcode.com/en/howto/code.html) contains more information about quiet zones.</span></span>

### <a name="lighting-and-backdrop"></a><span data-ttu-id="ec2f6-150">光源和底圖</span><span class="sxs-lookup"><span data-stu-id="ec2f6-150">Lighting and backdrop</span></span>
<span data-ttu-id="ec2f6-151">QR 代碼偵測品質很容易受到不同的照明和背景影響。</span><span class="sxs-lookup"><span data-stu-id="ec2f6-151">QR code detection quality is susceptible to varying illumination and backdrop.</span></span> 

<span data-ttu-id="ec2f6-152">在具有特別明亮光源的場景中，列印灰色背景上的黑色程式碼。</span><span class="sxs-lookup"><span data-stu-id="ec2f6-152">In a scene with particularly bright lighting, print a code that is black on a gray background.</span></span> <span data-ttu-id="ec2f6-153">否則，請在白色背景列印黑色 QR 代碼。</span><span class="sxs-lookup"><span data-stu-id="ec2f6-153">Otherwise, print a black QR code on a white background.</span></span>

<span data-ttu-id="ec2f6-154">如果程式碼的背景特別深，如果您的偵測速率很低，請嘗試黑色的灰色程式碼。</span><span class="sxs-lookup"><span data-stu-id="ec2f6-154">If the backdrop to the code is particularly dark, try a black on gray code if your detection rate is low.</span></span> <span data-ttu-id="ec2f6-155">如果背景相對較輕，則一般程式碼應該會正常運作。</span><span class="sxs-lookup"><span data-stu-id="ec2f6-155">If the backdrop is relatively light, a regular code should work fine.</span></span>

### <a name="size-of-qr-codes"></a><span data-ttu-id="ec2f6-156">QR 代碼的大小</span><span class="sxs-lookup"><span data-stu-id="ec2f6-156">Size of QR codes</span></span>
<span data-ttu-id="ec2f6-157">Windows Mixed Reality 裝置無法使用每個邊小於 5 cm 的 QR 代碼。</span><span class="sxs-lookup"><span data-stu-id="ec2f6-157">Windows Mixed Reality devices do not work with QR codes with sides smaller than 5 cm each.</span></span>

<span data-ttu-id="ec2f6-158">針對介於5到 10 cm 長度的 QR 代碼，您必須非常接近偵測程式碼。</span><span class="sxs-lookup"><span data-stu-id="ec2f6-158">For QR codes between 5 and 10 cm length sides, you must be fairly close to detect the code.</span></span> <span data-ttu-id="ec2f6-159">也需要較長的時間來偵測這種大小的代碼。</span><span class="sxs-lookup"><span data-stu-id="ec2f6-159">It will also take longer to detect codes at this size.</span></span> 

<span data-ttu-id="ec2f6-160">偵測程式碼的確切時間，不僅取決於 QR 代碼的大小，還會與您離開程式碼的程度不同。</span><span class="sxs-lookup"><span data-stu-id="ec2f6-160">The exact time to detect codes depends not only on the size of the QR codes, but how far you are away from the code.</span></span> <span data-ttu-id="ec2f6-161">移動較接近程式碼將有助於彌補大小問題。</span><span class="sxs-lookup"><span data-stu-id="ec2f6-161">Moving closer to the code will help offset issues with size.</span></span>

### <a name="distance-and-angular-position-from-the-qr-code"></a><span data-ttu-id="ec2f6-162">QR 代碼的距離和角度位置</span><span class="sxs-lookup"><span data-stu-id="ec2f6-162">Distance and angular position from the QR code</span></span>
<span data-ttu-id="ec2f6-163">追蹤攝影機只能偵測特定層級的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="ec2f6-163">The tracking cameras can only detect a certain level of detail.</span></span> <span data-ttu-id="ec2f6-164">針對真的很小的程式碼-< 10cm，您必須非常接近。</span><span class="sxs-lookup"><span data-stu-id="ec2f6-164">For really small codes - < 10cm along the sides - you must be fairly close.</span></span> <span data-ttu-id="ec2f6-165">針對第1版的 QR 代碼，從10到 25 cm 寬，最小偵測距離的範圍是從0.15 計量到0.5 計量。</span><span class="sxs-lookup"><span data-stu-id="ec2f6-165">For a version 1 QR code varying from 10 to 25 cm wide, the minimum detection distance ranges from 0.15 meters to 0.5 meters.</span></span> 

<span data-ttu-id="ec2f6-166">大小的偵測距離會以線性方式增加。</span><span class="sxs-lookup"><span data-stu-id="ec2f6-166">The detection distance for size increases linearly.</span></span> 

<span data-ttu-id="ec2f6-167">QR 偵測適用于一系列的角度 + = 45deg。</span><span class="sxs-lookup"><span data-stu-id="ec2f6-167">QR detection works with a range of angles += 45deg.</span></span> <span data-ttu-id="ec2f6-168">這是為了確保我們具有適當的解析度來偵測程式碼。</span><span class="sxs-lookup"><span data-stu-id="ec2f6-168">This is to ensure we have proper resolution to detect the code.</span></span>

### <a name="qr-codes-with-logos"></a><span data-ttu-id="ec2f6-169">具有標誌的 QR 代碼</span><span class="sxs-lookup"><span data-stu-id="ec2f6-169">QR codes with logos</span></span>
<span data-ttu-id="ec2f6-170">具有標誌的 QR 代碼尚未經過測試，且目前不受支援。</span><span class="sxs-lookup"><span data-stu-id="ec2f6-170">QR codes with logos have not been tested and are currently unsupported.</span></span>

### <a name="managing-qr-code-data"></a><span data-ttu-id="ec2f6-171">管理 QR 代碼資料</span><span class="sxs-lookup"><span data-stu-id="ec2f6-171">Managing QR code data</span></span>
<span data-ttu-id="ec2f6-172">Windows Mixed Reality 裝置會在驅動程式中偵測系統層級的 QR 代碼。</span><span class="sxs-lookup"><span data-stu-id="ec2f6-172">Windows Mixed Reality devices detect QR codes at the system level in the driver.</span></span> <span data-ttu-id="ec2f6-173">當裝置重新開機時，偵測到的 QR 代碼將會消失，並且會在下次重新偵測為新物件時重新偵測到。</span><span class="sxs-lookup"><span data-stu-id="ec2f6-173">When the device is rebooted, the detected QR codes are gone and will be re-detected as new objects next time.</span></span>

<span data-ttu-id="ec2f6-174">建議您將應用程式設定為略過超過特定時間戳記的 QR 代碼。</span><span class="sxs-lookup"><span data-stu-id="ec2f6-174">It is recommended to configure your app to ignore QR codes older than a specific timestamp.</span></span> <span data-ttu-id="ec2f6-175">目前，API 不支援清除 QR 代碼歷程記錄。</span><span class="sxs-lookup"><span data-stu-id="ec2f6-175">Currently, the API does not support clearing QR code history.</span></span>

### <a name="qr-code-placement-in-a-space"></a><span data-ttu-id="ec2f6-176">將 QR 代碼放置在空間中</span><span class="sxs-lookup"><span data-stu-id="ec2f6-176">QR code placement in a space</span></span>
<span data-ttu-id="ec2f6-177">如需在何處及如何放置 QR 代碼的建議，請參閱 [HoloLens 的環境考慮](../../environment-considerations-for-hololens.md)。</span><span class="sxs-lookup"><span data-stu-id="ec2f6-177">For recommendations on where and how to place QR codes, please refer to [Environment considerations for HoloLens](../../environment-considerations-for-hololens.md).</span></span>

## <a name="qr-api-reference"></a><span data-ttu-id="ec2f6-178">QR API 參考</span><span class="sxs-lookup"><span data-stu-id="ec2f6-178">QR API reference</span></span>

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

## <a name="see-also"></a><span data-ttu-id="ec2f6-179">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ec2f6-179">See also</span></span>
* [<span data-ttu-id="ec2f6-180">座標系統</span><span class="sxs-lookup"><span data-stu-id="ec2f6-180">Coordinate systems</span></span>](../../design/coordinate-systems.md)
* <span data-ttu-id="ec2f6-181"><a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a></span><span class="sxs-lookup"><span data-stu-id="ec2f6-181"><a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a></span></span>
