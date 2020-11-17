---
title: 取得 HolographicSpace
description: 說明 HolographicSpace API，這是一種適用于全息轉譯和空間輸入的核心概念。
author: mikeriches
ms.author: mriches
ms.date: 08/04/2020
ms.topic: article
keywords: Windows Mixed Reality、HolographicSpace、CoreWindow、空間輸入、轉譯、交換鏈、全像攝影框架、更新迴圈、遊戲迴圈、參考框架、locatability、範例程式碼、逐步解說、混合現實耳機、windows Mixed Reality 耳機、虛擬實境耳機
ms.openlocfilehash: fa2c64901a7c4a09710a472509441d54a9e3a383
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2020
ms.locfileid: "94679637"
---
# <a name="getting-a-holographicspace"></a>取得 HolographicSpace

> [!NOTE]
> 本文與舊版 WinRT 原生 Api 相關。  針對新的原生應用程式專案，建議使用 **[OPENXR API](openxr-getting-started.md)**。

<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>類別是您的入口網站，進入全像全球。 它會控制沉浸式轉譯、提供相機資料，並提供空間推理 Api 的存取權。 您將針對 UWP 應用程式的 <a href="https://docs.microsoft.com/api/windows.ui.core.corewindow" target="_blank">CoreWindow</a> 或您的 Win32 應用程式 HWND 建立一個。

## <a name="set-up-the-holographic-space"></a>設定全像空間

建立全像空間物件是建立 Windows Mixed Reality 應用程式的第一個步驟。 傳統的 Windows 應用程式會轉譯成針對其應用程式視圖的核心視窗所建立的 Direct3D 交換鏈。 此交換鏈會顯示于全像平板使用者的平板中。 若要讓您的應用程式視圖成為全像2D 的平板電腦，請建立其核心視窗的全像空間，而不是交換鏈。 展示此全像空間所建立的全螢幕畫面格，可將您的應用程式放入全螢幕轉譯模式。

針對從全像 [ *DirectX 11 應用程式開始 (通用 Windows) 範本*](creating-a-holographic-directx-project.md)的 **UWP 應用程式**，請在 AppView 中的 **SetWindow** 方法中尋找此程式碼：

```cpp
m_holographicSpace = HolographicSpace::CreateForCoreWindow(window);
```

若為 [從 *BasicHologram* win32 範例開始](creating-a-holographic-directx-project.md#creating-a-win32-project)的 **win32 應用程式**，請查看 **app：： CreateWindowAndHolographicSpace** ，以取得如何建立 HWND，然後藉由建立相關聯的 <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>，將它轉換成沉浸式 HWND 的範例：
```cpp
void App::CreateWindowAndHolographicSpace(HINSTANCE hInstance, int nCmdShow)
{
    // Store the instance handle in our class variable.
    m_hInst = hInstance;

    // Create the window for the HolographicSpace.
    hWnd = CreateWindowW(
        m_szWindowClass, 
        m_szTitle,
        WS_VISIBLE,
        CW_USEDEFAULT, 
        0, 
        CW_USEDEFAULT, 
        0, 
        nullptr, 
        nullptr, 
        hInstance, 
        nullptr);

    if (!hWnd)
    {
        winrt::check_hresult(E_FAIL);
    }

    {
        // Use WinRT factory to create the holographic space.
        using namespace winrt::Windows::Graphics::Holographic;
        winrt::com_ptr<IHolographicSpaceInterop> holographicSpaceInterop =
            winrt::get_activation_factory<HolographicSpace, IHolographicSpaceInterop>();
        winrt::com_ptr<ABI::Windows::Graphics::Holographic::IHolographicSpace> spHolographicSpace;
        winrt::check_hresult(holographicSpaceInterop->CreateForWindow(
            hWnd, __uuidof(ABI::Windows::Graphics::Holographic::IHolographicSpace),
            winrt::put_abi(spHolographicSpace)));

        if (!spHolographicSpace)
        {
            winrt::check_hresult(E_FAIL);
        }

        // Store the holographic space.
        m_holographicSpace = spHolographicSpace.as<HolographicSpace>();
    }

    // The DeviceResources class uses the preferred DXGI adapter ID from the holographic
    // space (when available) to create a Direct3D device. The HolographicSpace
    // uses this ID3D11Device to create and manage device-based resources such as
    // swap chains.
    m_deviceResources->SetHolographicSpace(m_holographicSpace);

    // The main class uses the holographic space for updates and rendering.
    m_main->SetHolographicSpace(hWnd, m_holographicSpace);

    // Show the window. This will activate the holographic view and switch focus
    // to the app in Windows Mixed Reality.
    ShowWindow(hWnd, nCmdShow);
    UpdateWindow(hWnd);
}
```

既然您已取得 UWP CoreWindow 或 Win32 HWND 的 HolographicSpace，您將會使用該 HolographicSpace 來處理全像相機、建立座標系統，以及進行全像轉譯。 目前的全像空間可用於 DirectX 範本中的多個位置：
* **DeviceResources** 類別需要從 HolographicSpace 物件取得一些資訊，才能建立 Direct3D 裝置。 這是與全像全像顯示器相關聯的 DXGI 介面卡識別碼。 <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>類別會使用您應用程式的 Direct3D 11 裝置來建立及管理裝置資源，例如每個全像攝影相機的背景緩衝區。 如果您有興趣查看此函式的本質，您可以在 DeviceResources 中找到它。
* 函式 **DeviceResources：： InitializeUsingHolographicSpace** 示範如何藉由查閱 LUID 來取得介面卡，以及如何在未指定慣用介面卡時選擇預設的介面卡。
* 應用程式的主要類別會使用 **AppView：： SetWindow** 或 **App：： CreateWindowAndHolographicSpace** 的全像空間來進行更新和轉譯。

>[!NOTE]
>雖然下列各節提及範本中的函式名稱（例如 **AppView：： SetWindow** ），這會假設您已從全像 uwp 應用程式範本開始，但您看到的程式碼片段同樣適用于 UWP 和 Win32 應用程式。

接下來，我們將深入探討 **SetHolographicSpace** 在 AppMain 類別中負責的設定流程。

## <a name="subscribe-to-camera-events-create-and-remove-camera-resources"></a>訂閱攝影機事件、建立和移除相機資源

您應用程式的全像攝影空間，是由一或多個代表場景上不同觀點的全像攝影攝影機所觀看。 現在您已有全像攝影空間，您可以接收全像攝影攝影機的資料。

您的應用程式必須藉由建立該攝影機專屬的任何資源（例如背景緩衝區轉譯目標視圖），來回應 **CameraAdded** 事件。 您可以在應用程式建立任何內建的框架之前，在 **DeviceResources：： SetHolographicSpace** 函式中看到此程式碼（由 **AppView：： SetWindow** 呼叫）：

```cpp
m_cameraAddedToken = m_holographicSpace.CameraAdded(
    std::bind(&AppMain::OnCameraAdded, this, _1, _2));
```

您的應用程式也需要釋出為該攝影機建立的資源，以回應 **CameraRemoved** 事件。

從 **DeviceResources：： SetHolographicSpace**：

```cpp
m_cameraRemovedToken = m_holographicSpace.CameraRemoved(
    std::bind(&AppMain::OnCameraRemoved, this, _1, _2));
```

事件處理常式必須完成一些工作，才能讓全像攝影轉譯流暢地流動，讓您的應用程式能夠完全呈現。 閱讀詳細資料的程式碼和批註：您可以在主要類別中尋找 **OnCameraAdded** 和 **OnCameraRemoved** ，以瞭解 **DeviceResources** 如何處理 **m_cameraResources** 對應。

現在，我們將焦點放在 AppMain 和設定，讓您的應用程式知道全像攝影攝影機。 記住這一點，請務必記下下列兩個需求：

1. 針對 **CameraAdded** 事件處理常式，應用程式可以非同步運作，以完成建立資源，以及為新的全像攝影中心載入資產。 使用多個畫面格來完成這項工作的應用程式應該要求延遲，並在非同步載入後完成延遲; [PPL](https://docs.microsoft.com/cpp/parallel/concrt/parallel-patterns-library-ppl) 工作可以用來執行非同步工作。 您的應用程式必須在結束事件處理常式或完成延遲時，確保它可以立即呈現給該攝影機。 結束事件處理常式或完成延遲，會告訴系統您的應用程式現在已準備好接收包含該攝影機的全像攝影畫面。

2. 當應用程式收到 **CameraRemoved** 事件時，它必須釋放對背景緩衝區的所有參考，並立即結束函式。 這包括轉譯目標視圖，以及可能保存 [IDXGIResource](https://docs.microsoft.com/windows/desktop/api/dxgi/nn-dxgi-idxgiresource)參考的任何其他資源。 應用程式也必須確保背景緩衝區未以轉譯目標的形式附加，如 **CameraResources：： ReleaseResourcesForBackBuffer** 所示。 為了協助您加快速度，您的應用程式可以釋出背景緩衝區，然後啟動工作來以非同步方式完成卸載該攝影機所需的任何其他工作。 全像「全像」應用程式範本包含可用於此用途的 PPL 工作。

>[!NOTE]
>如果您想要判斷畫面上顯示的是新增或移除的相機，請使用 **HolographicFrame** [AddedCameras](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.addedcameras) 和 [RemovedCameras](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.removedcameras) 屬性。

## <a name="create-a-frame-of-reference-for-your-holographic-content"></a>為您的全像內容建立參考框架

您應用程式的內容必須放置在要在 HolographicSpace 中轉譯的 [空間座標系統](coordinate-systems-in-directx.md) 中。 系統提供兩個主要的參考框架，您可以用來建立全像影像的座標系統。

Windows 內建的參考框架有兩種：連結至裝置的參考框架，以及裝置在使用者的環境中移動時仍保持靜止的參考框架。 全像「全像」應用程式範本預設會使用固定的參考框架;這是呈現全球鎖定的全像是最簡單的方式之一。

固定的參考框架是針對裝置目前位置附近的穩定位置所設計。 這表示，當裝置深入瞭解其周圍的空間時，可讓您更進一步地從裝置協調，以稍微偏離使用者的環境。 有兩種方式可以建立固定的參考框架：從 [空間階段](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-a-spatial-stage)取得座標系統，或使用預設 <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a>。 如果您要建立沉浸式耳機的 Windows Mixed Reality 應用程式，建議的起點是 [空間階段](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-a-spatial-stage)，它也會提供玩家所磨損之沉浸式耳機功能的相關資訊。 在這裡，我們會示範如何使用預設 <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a>。

空間定位器代表 Windows Mixed Reality 裝置，並會追蹤裝置的動作，並提供可理解的座標系統（相對於其位置）。

從 **AppMain：： OnHolographicDisplayIsAvailableChanged**：

```cpp
spatialLocator = SpatialLocator::GetDefault();
```

當應用程式啟動時，請建立固定的參考框架。 這類似于定義全局座標系統，並在應用程式啟動時，將原點放置於裝置的位置。 此參考框架不會與裝置一起移動。

從 **AppMain：： SetHolographicSpace**：

```cpp
m_stationaryReferenceFrame =
    m_spatialLocator.CreateStationaryFrameOfReferenceAtCurrentLocation();
```

所有的參考框架都是引力對齊的，也就是說，y 軸會依據使用者的環境指向「向上」。 由於 Windows 使用「右手」座標系統，因此– Z 軸的方向會與裝置在參考框架建立時所面向的「轉寄」方向一致。

>[!NOTE]
>當您的應用程式需要精確放置個別的全像投影時，請使用 <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor" target="_blank">SpatialAnchor</a> 將個別的全像點放置到真實世界的某個位置。 例如，當使用者指出要特別注意的點時，請使用空間錨點。 錨點位置不會漂移，但可以調整。 根據預設，當錨點調整之後，它會在發生更正之後，讓其在接下來的幾個框架上達到適當的位置。 視您的應用程式而定，當發生這種情況時，您可能會想要以不同的方式處理調整 (例如，將其延後到全像全像) 為止。 <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor.rawcoordinatesystem" target="_blank">RawCoordinateSystem</a>屬性和<a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor.rawcoordinatesystemadjusted" target="_blank">RawCoordinateSystemAdjusted</a>事件可啟用這些自訂。

## <a name="respond-to-locatability-changed-events"></a>回應 locatability 已變更的事件

呈現世界鎖定的全像是，裝置必須能夠在世界各地找到自己。 這可能不一定會因為環境條件而不一定可行，若是如此，使用者可能會預期追蹤中斷的視覺指示。 此視覺指示必須使用附加至裝置的參考框架來呈現，而不是使用非固定的環境。

您的應用程式可以要求在追蹤因為任何原因而中斷時收到通知。 註冊 LocatabilityChanged 事件，以偵測裝置在世界中尋找本身的能力變更。 從 **AppMain：： SetHolographicSpace：**

```cpp
m_locatabilityChangedToken = m_spatialLocator.LocatabilityChanged(
    std::bind(&HolographicApp6Main::OnLocatabilityChanged, this, _1, _2));
```

然後，請使用此事件來判斷何時無法將靜止的全像全球呈現。

## <a name="see-also"></a>另請參閱
* [DirectX 中的呈現](rendering-in-directx.md)
* [DirectX 中的座標系統](coordinate-systems-in-directx.md)
