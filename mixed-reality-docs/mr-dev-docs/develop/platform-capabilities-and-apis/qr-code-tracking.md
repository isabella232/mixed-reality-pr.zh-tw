---
title: QR 代碼追蹤
description: 瞭解如何在 HoloLens 2 上偵測 QR 代碼、新增網路攝影機功能，以及管理混合現實應用程式中的座標系統。
author: dorreneb
ms.author: dobrown
ms.date: 01/21/2021
ms.topic: article
keywords: vr、lbe、以位置為基礎的娛樂、vr arcade、arcade、沉浸式、qr、qr 代碼、hololens2
ms.openlocfilehash: f6d2f224b9f477cf78ba4f0a5b6ce362f629d06988e966d71ed03bc48eda41d9
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2021
ms.locfileid: "115193706"
---
# <a name="qr-code-tracking"></a>QR 代碼追蹤

HoloLens 2 可以偵測頭戴式裝置周圍環境中的 QR 代碼，而在每個代碼的真實世界位置建立座標系統。 啟用裝置的網路攝影機之後，您就能夠辨識 Unreal 或 Unity 專案最新版本中的 QR 代碼。 在進入生產環境之前，建議您遵循我們在本文結尾的 [最佳作法](#best-practices-for-qr-code-detection) 。

## <a name="device-support"></a>裝置支援

<table>
<tr>
<th>功能</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens (第一代) </a></th><th style="width:150px">HoloLens 2</th><th style="width:150px"> <a href="../../discover/immersive-headset-hardware-details.md">沉浸式頭戴裝置</a></th>
</tr><tr>
<td> QR 代碼偵測</td><td style="text-align: center;">️</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;">✔️</td>
</tr>
</table>

>[!NOTE]
>Windows 10 2004 版和更高版本支援在桌上型電腦上使用沉浸式 Windows Mixed Reality 耳機進行 QR 代碼追蹤。 使用 MixedReality. QRCodeWatcher. IsSupported () API 來判斷目前的裝置是否支援此功能。

## <a name="getting-the-qr-package"></a>取得 QR 套件

您可以在[這裡](https://nuget.org/Packages/Microsoft.MixedReality.QR)下載適用于 QR 代碼偵測的 NuGet 套件。

## <a name="using-openxr"></a>使用 OpenXR

使用 OpenXR 外掛程式時，請[ `SpatialGraphNodeId` 從 QR API](../platform-capabilities-and-apis/qr-code-tracking.md#qr-api-reference)抓取，並使用 `Microsoft.MixedReality.OpenXR.SpatialGraphNode` API 來尋找 qr 代碼。

如需參考，我們有[GitHub 的 QR 追蹤範例專案](https://github.com/yl-msft/QRTracking)，並詳細說明[ `SpatialGraphNode` API](https://github.com/yl-msft/QRTracking/blob/main/SampleQRCodes/Assets/Scripts/SpatialGraphNodeTracker.cs)的使用方式說明。

## <a name="detecting-qr-codes"></a>偵測 QR 代碼

### <a name="adding-the-webcam-capability"></a>新增網路攝影機功能

您必須將功能新增 `webcam` 至您的資訊清單，以偵測 QR 代碼。 這項功能是必要的，因為使用者環境中偵測到的程式碼內的資料可能包含機密資訊。

您可以呼叫下列方法來要求許可權 `QRCodeWatcher.RequestAccessAsync()` ：

_C#：_
```cs
await QRCodeWatcher.RequestAccessAsync();
```

_C++：_
```cpp
co_await QRCodeWatcher.RequestAccessAsync();
```

在您建立 QRCodeWatcher 物件之前，必須先要求許可權。

當 QR 代碼偵測需要這項 `webcam` 功能時，會使用裝置的追蹤攝影機進行偵測。 相較于使用裝置的相片/影片 (PV) 攝影機的偵測，這可提供更廣泛的偵測 FOV 和較佳的電池壽命。

### <a name="detecting-qr-codes-in-unity"></a>在 Unity 中偵測 QR 代碼

您可以在 unity 中使用 QR 代碼偵測 API，而不需要匯入 MRTK，方法是使用[適用于 unity 的 NuGet](https://github.com/GlitchEnzo/NuGetForUnity)安裝 NuGet 套件。 如果您想要瞭解其運作方式，請下載 [範例 Unity 應用程式](https://github.com/chgatla-microsoft/QRTracking/tree/master/SampleQRCodes)。 範例應用程式中的範例會顯示 QR 代碼的全像正方形，以及相關聯的資料，例如 GUID、實體大小、時間戳記和已解碼的資料。

### <a name="detecting-qr-codes-in-c"></a>在 c + + 中偵測 QR 代碼

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

## <a name="getting-the-coordinate-system-for-a-qr-code"></a>取得 QR 代碼的座標系統

每個偵測到的 QR 代碼都會公開 [空間座標系統](../../design/coordinate-systems.md) ，此系統會對齊左上角的 QR 代碼，位於左上角的快速偵測方塊左上角：  

![QR 代碼座標系統](images/Qr-coordinatesystem.png) 

當直接使用 QR SDK 時，Z 軸會指向紙張 (不會顯示) -轉換成 Unity 座標時，Z 軸會指向紙張，並會被左手。

QR 代碼的 SpatialCoordinateSystem 會對齊，如下所示。 您可以藉由呼叫 <a href="/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.createcoordinatesystemfornode" target="_blank">SpatialGraphInteropPreview：： CreateCoordinateSystemForNode</a> 並傳入程式碼的 SpatialGraphNodeId，從平臺取得座標系統。

下列 c + + 程式碼顯示如何建立矩形，並使用 QR 代碼的座標系統來放置它：

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

您可以使用實體大小來建立 QR 矩形：

```cpp
std::vector<float3> qrVertices = CreateRectangle(code.PhysicalSideLength(), code.PhysicalSideLength()); 
```

座標系統可以用來繪製 QR 代碼，或將全像位置連接到位置：

```cpp
using namespace winrt::Windows::Perception::Spatial;
using namespace winrt::Windows::Perception::Spatial::Preview;
SpatialCoordinateSystem qrCoordinateSystem = SpatialGraphInteropPreview::CreateCoordinateSystemForNode(code.SpatialGraphNodeId());
```

您的 *QRCodeAddedHandler* 會完全看起來像這樣：

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

## <a name="best-practices-for-qr-code-detection"></a>QR 代碼偵測的最佳作法

### <a name="quiet-zones-around-qr-codes"></a>QR 代碼周圍的安靜區域

若要正確讀取，QR 代碼需要在程式碼的所有側邊周圍邊界。 此邊界不得包含任何列印的內容，而且應該是四個模組 (程式碼) 寬的單一黑色方塊。 

[QR 規格](https://www.qrcode.com/en/howto/code.html)包含有關安靜區域的詳細資訊。

### <a name="lighting-and-backdrop"></a>光源和底圖
QR 代碼偵測品質很容易受到不同的照明和背景影響。 

在具有亮光源的場景中，列印灰色背景上的黑色程式碼。 否則，請在白色背景列印黑色 QR 代碼。

如果程式碼的背景為深色，如果您的偵測速率很低，請嘗試黑色的灰色程式碼。 如果背景相對較輕，則一般程式碼應該會正常運作。

### <a name="size-of-qr-codes"></a>QR 代碼的大小
Windows Mixed Reality 裝置無法處理每個邊小於 5 cm 的 QR 代碼。

若為 5 cm 到 10-cm 長度之間的 QR 代碼，您必須非常接近偵測程式碼。 也需要較長的時間來偵測這種大小的代碼。 

偵測程式碼的確切時間，不只取決於 QR 代碼的大小，也不只是您離開程式碼的程度。 移動較接近程式碼將有助於彌補大小問題。

### <a name="distance-and-angular-position-from-the-qr-code"></a>QR 代碼的距離和角度位置
追蹤攝影機只能偵測特定層級的詳細資料。 針對較小的程式碼-< 10 cm 的側邊，您必須非常接近。 針對第1版的 QR 代碼，從 10 cm 到 25 cm 寬的不同，最小偵測距離的範圍是從0.15 計量到0.5 計量。 

大小的偵測距離會以線性方式增加，但也取決於 QR 版本或模組大小。 版本愈高，模組愈小，只可從較接近的位置偵測到。 如果您想要讓偵測的距離變長，您也可以嘗試微型 QR 代碼。 QR 偵測適用于一系列的角度 + = 45 度，以確保我們具有適當的解析度來偵測程式碼。

> [!IMPORTANT]
> 請務必確定您有足夠的對比和適當的框線。

### <a name="qr-codes-with-logos"></a>具有標誌的 QR 代碼
具有標誌的 QR 代碼尚未經過測試，且目前不受支援。

### <a name="managing-qr-code-data"></a>管理 QR 代碼資料
Windows Mixed Reality 裝置會在驅動程式中偵測系統層級的 QR 代碼。 當裝置重新開機時，偵測到的 QR 代碼將會消失，並且會在下一次重新檢測為新物件。

建議您將應用程式設定為略過超過特定時間戳記的 QR 代碼。 目前，API 不支援清除 QR 代碼歷程記錄。

### <a name="qr-code-placement-in-a-space"></a>將 QR 代碼放置在空間中
如需在何處及如何放置 QR 代碼的建議，請參閱[HoloLens 的環境考慮](/hololens/hololens-environment-considerations)。

## <a name="qr-api-reference"></a>QR API 參考

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

## <a name="see-also"></a>另請參閱
* [座標系統](../../design/coordinate-systems.md)
* <a href="/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a>