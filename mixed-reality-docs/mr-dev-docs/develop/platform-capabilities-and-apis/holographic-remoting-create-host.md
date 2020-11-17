---
title: 撰寫全像攝影遠端應用程式
description: 藉由建立可在遠端電腦上轉譯的全像遠端遠端應用程式遠端內容，可以串流處理至 HoloLens 2。 本文說明如何達成此目的。
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 03/11/2020
ms.topic: article
keywords: HoloLens、遠端、全像全像遠端、混合現實耳機、windows mixed reality 耳機、虛擬實境耳機、NuGet
ms.openlocfilehash: 8494387b99352866632b46a98a449d173395b85d
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2020
ms.locfileid: "94677937"
---
# <a name="writing-a-holographic-remoting-remote-app"></a><span data-ttu-id="e8337-105">撰寫全像攝影遠端應用程式</span><span class="sxs-lookup"><span data-stu-id="e8337-105">Writing a Holographic Remoting remote app</span></span>

>[!IMPORTANT]
><span data-ttu-id="e8337-106">本檔說明如何建立 HoloLens 2 的遠端應用程式。</span><span class="sxs-lookup"><span data-stu-id="e8337-106">This document describes the creation of a remote application for HoloLens 2.</span></span> <span data-ttu-id="e8337-107">**HoloLens (第1代)** 的遠端應用程式必須使用 NuGet **1.x.x** 套件1.x 版。</span><span class="sxs-lookup"><span data-stu-id="e8337-107">Remote applications for **HoloLens (1st gen)** must use NuGet package version **1.x.x**.</span></span> <span data-ttu-id="e8337-108">這表示針對 HoloLens 2 撰寫的遠端應用程式不相容于 HoloLens 1，反之亦然。</span><span class="sxs-lookup"><span data-stu-id="e8337-108">This implies that remote applications written for HoloLens 2 are not compatible with HoloLens 1 and vice versa.</span></span> <span data-ttu-id="e8337-109">您可以在 [這裡](add-holographic-remoting.md)找到 HoloLens 1 的檔。</span><span class="sxs-lookup"><span data-stu-id="e8337-109">The documentation for HoloLens 1 can be found [here](add-holographic-remoting.md).</span></span>

<span data-ttu-id="e8337-110">藉由建立全像遠端遠端應用程式，可以將遠端電腦上轉譯的遠端內容串流處理至 HoloLens 2。</span><span class="sxs-lookup"><span data-stu-id="e8337-110">By creating a Holographic Remoting remote app, remote content that is rendered on a remote machine can be streamed to HoloLens 2.</span></span> <span data-ttu-id="e8337-111">本文說明如何達成此目的。</span><span class="sxs-lookup"><span data-stu-id="e8337-111">This article describes how this can be achieved.</span></span> <span data-ttu-id="e8337-112">此頁面上的所有程式碼和工作專案都可在「全像 [遠端範例」 github 存放庫](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples)中找到。</span><span class="sxs-lookup"><span data-stu-id="e8337-112">All code on this page and working projects can be found in the [Holographic Remoting samples github repository](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).</span></span>

<span data-ttu-id="e8337-113">全像「全像」的遠端功能可讓應用程式以在桌上型電腦上轉譯的全像是 HoloLens 2，或在 UWP 裝置上轉譯（例如 Xbox One），以允許存取更多系統資源，並讓您能夠將遠端 [沉浸式視圖](../../design/app-views.md) 整合至現有的桌上型電腦軟體。</span><span class="sxs-lookup"><span data-stu-id="e8337-113">Holographic remoting allows an app to target HoloLens 2 with holographic content rendered on a desktop PC or on a UWP device such as the Xbox One, allowing access to more system resources and making it possible to integrate remote [immersive views](../../design/app-views.md) into existing desktop PC software.</span></span> <span data-ttu-id="e8337-114">遠端應用程式會從 HoloLens 2 接收輸入資料流程、在虛擬沉浸式視圖中轉譯內容，並將內容框架串流回 HoloLens 2。</span><span class="sxs-lookup"><span data-stu-id="e8337-114">A remote app receives an input data stream from HoloLens 2, renders content in a virtual immersive view, and streams content frames back to HoloLens 2.</span></span> <span data-ttu-id="e8337-115">連接是使用標準 Wi-fi 進行的。</span><span class="sxs-lookup"><span data-stu-id="e8337-115">The connection is made using standard Wi-Fi.</span></span> <span data-ttu-id="e8337-116">在桌面或 UWP 應用程式中，會透過 NuGet 封包新增全像的遠端處理。</span><span class="sxs-lookup"><span data-stu-id="e8337-116">Holographic Remoting is added to a desktop or UWP app via a NuGet packet.</span></span> <span data-ttu-id="e8337-117">需要額外的程式碼，以處理連接並以沉浸式視圖呈現。</span><span class="sxs-lookup"><span data-stu-id="e8337-117">Additional code is required which handles the connection and renders in an immersive view.</span></span>

<span data-ttu-id="e8337-118">一般的遠端連線的延遲將會降到50毫秒。</span><span class="sxs-lookup"><span data-stu-id="e8337-118">A typical remoting connection will have as low as 50 ms of latency.</span></span> <span data-ttu-id="e8337-119">播放程式應用程式可以即時報告延遲時間。</span><span class="sxs-lookup"><span data-stu-id="e8337-119">The player app can report the latency in real-time.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e8337-120">先決條件</span><span class="sxs-lookup"><span data-stu-id="e8337-120">Prerequisites</span></span>

<span data-ttu-id="e8337-121">良好的起點是以 Windows Mixed Reality API 為目標的可運作 DirectX 型桌面或 UWP 應用程式。</span><span class="sxs-lookup"><span data-stu-id="e8337-121">A good starting point is a working DirectX based Desktop or UWP app which targets the Windows Mixed Reality API.</span></span> <span data-ttu-id="e8337-122">如需詳細資訊，請參閱 [DirectX 開發總覽](../native/directx-development-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="e8337-122">For details see [DirectX development overview](../native/directx-development-overview.md).</span></span> <span data-ttu-id="e8337-123">[C + + 全息版專案範本](../native/creating-a-holographic-directx-project.md)是不錯的起點。</span><span class="sxs-lookup"><span data-stu-id="e8337-123">The [C++ holographic project template](../native/creating-a-holographic-directx-project.md) is a good starting point.</span></span>

>[!IMPORTANT]
><span data-ttu-id="e8337-124">使用「全像」遠端處理的任何應用程式都應該撰寫為使用 [多執行緒的單元](https://docs.microsoft.com//windows/win32/com/multithreaded-apartments)。</span><span class="sxs-lookup"><span data-stu-id="e8337-124">Any app using Holographic Remoting should be authored to use a [multi-threaded apartment](https://docs.microsoft.com//windows/win32/com/multithreaded-apartments).</span></span> <span data-ttu-id="e8337-125">支援使用 [單一執行緒的單元](https://docs.microsoft.com//windows/win32/com/single-threaded-apartments) ，但會導致效能不佳，而且可能會在播放期間間斷情形。</span><span class="sxs-lookup"><span data-stu-id="e8337-125">The use of a [single-threaded apartment](https://docs.microsoft.com//windows/win32/com/single-threaded-apartments) is supported but will lead to sub-optimal performance and possibly stuttering during playback.</span></span> <span data-ttu-id="e8337-126">使用 c + +/WinRT [WinRT：： init_apartment](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/get-started) 多執行緒的單元是預設值。</span><span class="sxs-lookup"><span data-stu-id="e8337-126">When using C++/WinRT [winrt::init_apartment](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/get-started) a multi-threaded apartment is the default.</span></span>



## <a name="get-the-holographic-remoting-nuget-package"></a><span data-ttu-id="e8337-127">取得全像 Remoting NuGet 套件</span><span class="sxs-lookup"><span data-stu-id="e8337-127">Get the Holographic Remoting NuGet package</span></span>

<span data-ttu-id="e8337-128">若要將 NuGet 套件新增至 Visual Studio 中的專案，必須執行下列步驟。</span><span class="sxs-lookup"><span data-stu-id="e8337-128">The following steps are required to add the NuGet package to a project in Visual Studio.</span></span>
1. <span data-ttu-id="e8337-129">在 Visual Studio 中開啟專案。</span><span class="sxs-lookup"><span data-stu-id="e8337-129">Open the project in Visual Studio.</span></span>
2. <span data-ttu-id="e8337-130">以滑鼠右鍵按一下專案節點，然後選取 [**管理 NuGet 套件 ...** ]</span><span class="sxs-lookup"><span data-stu-id="e8337-130">Right-click the project node and select **Manage NuGet Packages...**</span></span>
3. <span data-ttu-id="e8337-131">在出現的面板中，按一下 **[流覽]** ，然後搜尋「全像的遠端處理」。</span><span class="sxs-lookup"><span data-stu-id="e8337-131">In the panel that appears, click **Browse** and then search for "Holographic Remoting".</span></span>
4. <span data-ttu-id="e8337-132">選取 [ **Microsoft**]，並確定 **挑選最新** 的2.x 版，然後按一下 [ **安裝**]。</span><span class="sxs-lookup"><span data-stu-id="e8337-132">Select **Microsoft.Holographic.Remoting**, ensure to pick the latest **2.x.x** version and click **Install**.</span></span>
5. <span data-ttu-id="e8337-133">如果出現 [ **預覽** ] 對話方塊，請按一下 **[確定**]。</span><span class="sxs-lookup"><span data-stu-id="e8337-133">If the **Preview** dialog appears, click **OK**.</span></span>
6. <span data-ttu-id="e8337-134">出現的下一個對話方塊是授權合約。</span><span class="sxs-lookup"><span data-stu-id="e8337-134">The next dialog that appears is the license agreement.</span></span> <span data-ttu-id="e8337-135">按一下 [ **我接受** ] 以接受授權合約。</span><span class="sxs-lookup"><span data-stu-id="e8337-135">Click on **I Accept** to accept the license agreement.</span></span>

>[!NOTE]
><span data-ttu-id="e8337-136">2.x **版的** NuGet 套件仍可供想要以 HoloLens 1 為目標的開發人員使用。</span><span class="sxs-lookup"><span data-stu-id="e8337-136">Version **1.x.x** of the NuGet package is still available for developers who want to target HoloLens 1.</span></span> <span data-ttu-id="e8337-137">如需詳細資訊，請參閱新增全像 [遠端 (HoloLens (第1代) # B3 ](add-holographic-remoting.md)。</span><span class="sxs-lookup"><span data-stu-id="e8337-137">For details see [Add Holographic Remoting (HoloLens (1st gen))](add-holographic-remoting.md).</span></span>

## <a name="create-the-remote-context"></a><span data-ttu-id="e8337-138">建立遠端內容</span><span class="sxs-lookup"><span data-stu-id="e8337-138">Create the remote context</span></span>

<span data-ttu-id="e8337-139">在第一個步驟中，應用程式應該建立遠端內容。</span><span class="sxs-lookup"><span data-stu-id="e8337-139">As a first step the application should create a remote context.</span></span>

```cpp
// class declaration
#include <winrt/Microsoft.Holographic.AppRemoting.h>

...

private:
    // RemoteContext used to connect with a Holographic Remoting player and display rendered frames
    winrt::Microsoft::Holographic::AppRemoting::RemoteContext m_remoteContext = nullptr;
```


```cpp
// class implementation
#include <HolographicAppRemoting\Streamer.h>

...

CreateRemoteContext(m_remoteContext, 20000, false, PreferredVideoCodec::Default);

```

>[!WARNING]
><span data-ttu-id="e8337-140">全像是以遠端處理特定執行時間取代 Windows 一部分的 Windows Mixed Reality 執行時間，來進行全像的遠端處理工作。</span><span class="sxs-lookup"><span data-stu-id="e8337-140">Holographic Remoting works by replacing the Windows Mixed Reality runtime which is part of Windows with a remoting specific runtime.</span></span> <span data-ttu-id="e8337-141">這是在建立遠端內容期間完成的。</span><span class="sxs-lookup"><span data-stu-id="e8337-141">This is done during the creation of the remote context.</span></span> <span data-ttu-id="e8337-142">基於這個理由，在建立遠端內容之前，對任何 Windows Mixed Reality API 進行的任何呼叫都會導致非預期的行為。</span><span class="sxs-lookup"><span data-stu-id="e8337-142">For that reason any call on any Windows Mixed Reality API before creating the remote context can result in unexpected behavior.</span></span> <span data-ttu-id="e8337-143">建議的方法是在與任何混合現實 API 互動之前儘早建立遠端內容。</span><span class="sxs-lookup"><span data-stu-id="e8337-143">The recommended approach is to create the remote context as early as possible before interaction with any Mixed Reality API.</span></span> <span data-ttu-id="e8337-144">使用之後建立或抓取的物件來呼叫 CreateRemoteCoNtext 之前，絕對不要混合透過任何 Windows Mixed Reality API 建立或取出的物件。</span><span class="sxs-lookup"><span data-stu-id="e8337-144">Never mix objects created or retrieved through any Windows Mixed Reality API before the call to CreateRemoteContext with objects created or retrieved afterwards.</span></span>

<span data-ttu-id="e8337-145">接下來必須建立全像空間。</span><span class="sxs-lookup"><span data-stu-id="e8337-145">Next the holographic space needs to be created.</span></span> <span data-ttu-id="e8337-146">不需要指定 CoreWindow。</span><span class="sxs-lookup"><span data-stu-id="e8337-146">Specifying a CoreWindow is not required.</span></span> <span data-ttu-id="e8337-147">沒有 CoreWindow 的桌面應用程式可以直接傳遞 ```nullptr``` 。</span><span class="sxs-lookup"><span data-stu-id="e8337-147">Desktop apps that do not have a CoreWindow can just pass a ```nullptr```.</span></span>

```cpp
m_holographicSpace = winrt::Windows::Graphics::Holographic::HolographicSpace::CreateForCoreWindow(nullptr);
```

## <a name="connect-to-the-device"></a><span data-ttu-id="e8337-148">連接到裝置</span><span class="sxs-lookup"><span data-stu-id="e8337-148">Connect to the device</span></span>

<span data-ttu-id="e8337-149">遠端應用程式準備好轉譯內容之後，就可以建立裝置的連線。</span><span class="sxs-lookup"><span data-stu-id="e8337-149">Once the remote app is ready for rendering content a connection to the device can be established.</span></span>

<span data-ttu-id="e8337-150">您可以透過下列兩種方式之一來完成連接。</span><span class="sxs-lookup"><span data-stu-id="e8337-150">Connection can be done in one of two ways.</span></span>
1) <span data-ttu-id="e8337-151">遠端應用程式會連接到在裝置上執行的播放程式。</span><span class="sxs-lookup"><span data-stu-id="e8337-151">The remote app connects to the player running on the device.</span></span>
2) <span data-ttu-id="e8337-152">在裝置上執行的播放程式會連接到遠端應用程式。</span><span class="sxs-lookup"><span data-stu-id="e8337-152">The player running on the device connects to the remote app.</span></span>

<span data-ttu-id="e8337-153">若要建立從遠端應用程式到 HoloLens 2 的連接，請 ```Connect``` 在指定主機名稱和埠的遠端內容上呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="e8337-153">To establish a connection from the remote app to HoloLens 2 call the ```Connect``` method on the remote context specifying the hostname and port.</span></span> <span data-ttu-id="e8337-154">全像遠端播放機使用的埠是 **8265**。</span><span class="sxs-lookup"><span data-stu-id="e8337-154">The port used by the Holographic Remoting Player is **8265**.</span></span>

```cpp
try
{
    m_remoteContext.Connect(m_hostname, m_port);
}
catch(winrt::hresult_error& e)
{
    DebugLog(L"Connect failed with hr = 0x%08X", e.code());
}
```

>[!IMPORTANT]
><span data-ttu-id="e8337-155">如同任何 c + +/WinRT API， ```Connect``` 可能會擲回需要處理的 WinRT：： hresult_error。</span><span class="sxs-lookup"><span data-stu-id="e8337-155">As with any C++/WinRT API ```Connect``` might throw an winrt::hresult_error which needs to be handled.</span></span>

>[!TIP]
><span data-ttu-id="e8337-156">若要避免使用 [c + +/WinRT](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/) 語言投射， ```build\native\include\<windows sdk version>\abi\Microsoft.Holographic.AppRemoting.h``` 可以包含位於全像「遠端處理 NuGet」套件內的檔案。</span><span class="sxs-lookup"><span data-stu-id="e8337-156">To avoid using [C++/WinRT](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/) language projection the file ```build\native\include\<windows sdk version>\abi\Microsoft.Holographic.AppRemoting.h``` located inside the Holographic Remoting NuGet package can be included.</span></span> <span data-ttu-id="e8337-157">它包含基礎 COM 介面的宣告。</span><span class="sxs-lookup"><span data-stu-id="e8337-157">It contains declarations of the underlying COM interfaces.</span></span> <span data-ttu-id="e8337-158">不過，我們建議使用 c + +/WinRT。</span><span class="sxs-lookup"><span data-stu-id="e8337-158">The use of C++/WinRT is recommended though.</span></span>

<span data-ttu-id="e8337-159">您可以藉由呼叫方法來接聽遠端應用程式上的連入連線 ```Listen``` 。</span><span class="sxs-lookup"><span data-stu-id="e8337-159">Listening for incoming connections on the remote app can be done by calling the ```Listen``` method.</span></span> <span data-ttu-id="e8337-160">交握埠和傳輸埠都可以在此呼叫期間指定。</span><span class="sxs-lookup"><span data-stu-id="e8337-160">Both the handshake port and transport port can be specified during this call.</span></span> <span data-ttu-id="e8337-161">交握埠用於初始交握。</span><span class="sxs-lookup"><span data-stu-id="e8337-161">The handshake port is used for the initial handshake.</span></span> <span data-ttu-id="e8337-162">然後，資料會透過傳輸埠傳送。</span><span class="sxs-lookup"><span data-stu-id="e8337-162">The data is then send over the transport port.</span></span> <span data-ttu-id="e8337-163">預設會使用 **8265** 和 **8266** 。</span><span class="sxs-lookup"><span data-stu-id="e8337-163">By default **8265** and **8266** are used.</span></span>

```cpp
try
{
    m_remoteContext.Listen(L"0.0.0.0", m_port, m_port + 1);
}
catch(winrt::hresult_error& e)
{
    DebugLog(L"Listen failed with hr = 0x%08X", e.code());
}
```

>[!IMPORTANT]
><span data-ttu-id="e8337-164">NuGet 套件內的包含適用于全像全像攝影的 ```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl``` API 的詳細檔。</span><span class="sxs-lookup"><span data-stu-id="e8337-164">The ```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl``` inside the NuGet package contains detailed documentation for the API exposed by Holographic Remoting.</span></span>

## <a name="handling-remoting-specific-events"></a><span data-ttu-id="e8337-165">處理遠端處理特定事件</span><span class="sxs-lookup"><span data-stu-id="e8337-165">Handling Remoting specific events</span></span>

<span data-ttu-id="e8337-166">遠端內容會公開三個很重要的事件，以監視連接的狀態。</span><span class="sxs-lookup"><span data-stu-id="e8337-166">The remote context exposes three events which are important to monitor the state of a connection.</span></span>
1) <span data-ttu-id="e8337-167">OnConnected：已成功建立裝置的連線時觸發。</span><span class="sxs-lookup"><span data-stu-id="e8337-167">OnConnected: Triggered when a connection to the device has been successfully established.</span></span>
```cpp
winrt::weak_ref<winrt::Microsoft::Holographic::AppRemoting::IRemoteContext> remoteContextWeakRef = m_remoteContext;

m_onConnectedEventRevoker = m_remoteContext.OnConnected(winrt::auto_revoke, [this, remoteContextWeakRef]() {
    if (auto remoteContext = remoteContextWeakRef.get())
    {
        // Update UI state
    }
});
```
2) <span data-ttu-id="e8337-168">OnDisconnected：如果建立的連接已關閉或無法建立連接，則會觸發。</span><span class="sxs-lookup"><span data-stu-id="e8337-168">OnDisconnected: Triggered if an established connection is closed or a connection could not be established.</span></span>
```cpp
m_onDisconnectedEventRevoker =
    m_remoteContext.OnDisconnected(winrt::auto_revoke, [this, remoteContextWeakRef](ConnectionFailureReason failureReason) {
        if (auto remoteContext = remoteContextWeakRef.get())
        {
            DebugLog(L"Disconnected with reason %d", failureReason);
            // Update UI

            // Reconnect if this is a transient failure.
            if (failureReason == ConnectionFailureReason::HandshakeUnreachable ||
                failureReason == ConnectionFailureReason::TransportUnreachable ||
                failureReason == ConnectionFailureReason::ConnectionLost)
            {
                DebugLog(L"Reconnecting...");

                ConnectOrListen();
            }
            // Failure reason None indicates a normal disconnect.
            else if (failureReason != ConnectionFailureReason::None)
            {
                DebugLog(L"Disconnected with unrecoverable error, not attempting to reconnect.");
            }
        }
    });
```
3) <span data-ttu-id="e8337-169">OnListening：接聽連入連線開始時。</span><span class="sxs-lookup"><span data-stu-id="e8337-169">OnListening: When listening for incoming connections starts.</span></span>
```cpp
m_onListeningEventRevoker = m_remoteContext.OnListening(winrt::auto_revoke, [this, remoteContextWeakRef]() {
    if (auto remoteContext = remoteContextWeakRef.get())
    {
        // Update UI state
    }
});
```

<span data-ttu-id="e8337-170">此外，您也可以使用遠端內容上的屬性來查詢連接狀態 ```ConnectionState``` 。</span><span class="sxs-lookup"><span data-stu-id="e8337-170">Additionally the connection state can be queried using the ```ConnectionState``` property on the remote context.</span></span>
```cpp
auto connectionState = m_remoteContext.ConnectionState();
```

## <a name="handling-speech-events"></a><span data-ttu-id="e8337-171">處理語音事件</span><span class="sxs-lookup"><span data-stu-id="e8337-171">Handling speech events</span></span>

<span data-ttu-id="e8337-172">您可以使用遠端語音介面，向 HoloLens 2 註冊語音觸發程式，並讓它們遠端處理遠端應用程式。</span><span class="sxs-lookup"><span data-stu-id="e8337-172">Using the remote speech interface it is possible to register speech triggers with HoloLens 2 and have them remoted to the remote application.</span></span>

<span data-ttu-id="e8337-173">需要此額外成員才能追蹤遠端語音的狀態。</span><span class="sxs-lookup"><span data-stu-id="e8337-173">This additional member is required to track the state of the remote speech.</span></span>

```cpp
winrt::Microsoft::Holographic::AppRemoting::IRemoteSpeech::OnRecognizedSpeech_revoker m_onRecognizedSpeechRevoker;

```

<span data-ttu-id="e8337-174">首先，必須抓取遠端語音介面。</span><span class="sxs-lookup"><span data-stu-id="e8337-174">First the remote speech interface needs to be retrieved.</span></span>

```cpp
if (auto remoteSpeech = m_remoteContext.GetRemoteSpeech())
{
    InitializeSpeechAsync(remoteSpeech, m_onRecognizedSpeechRevoker, weak_from_this());
}
```

<span data-ttu-id="e8337-175">您可以使用非同步協助程式方法來初始化遠端語音。</span><span class="sxs-lookup"><span data-stu-id="e8337-175">Using an asynchronous helper method you can then initialize the remote speech.</span></span> <span data-ttu-id="e8337-176">這應該會以非同步方式完成，因為初始化可能需要相當長的時間。</span><span class="sxs-lookup"><span data-stu-id="e8337-176">This should be done asynchronously as initializing might take a considerable amount of time.</span></span> <span data-ttu-id="e8337-177">[使用 c + +/WinRT 的並行和非同步作業](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/concurrency) 說明如何使用 c + +/winrt 撰寫非同步函式</span><span class="sxs-lookup"><span data-stu-id="e8337-177">[Concurrency and asynchronous operations with C++/WinRT](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/concurrency) explains how to author asynchronous functions with C++/WinRT.</span></span>

```cpp
winrt::Windows::Foundation::IAsyncOperation<winrt::Windows::Storage::StorageFile> LoadGrammarFileAsync()
{
    const wchar_t* speechGrammarFile = L"SpeechGrammar.xml";
    auto rootFolder = winrt::Windows::ApplicationModel::Package::Current().InstalledLocation();
    return rootFolder.GetFileAsync(speechGrammarFile);
}

winrt::fire_and_forget InitializeSpeechAsync(
    winrt::Microsoft::Holographic::AppRemoting::IRemoteSpeech remoteSpeech,
    winrt::Microsoft::Holographic::AppRemoting::IRemoteSpeech::OnRecognizedSpeech_revoker& onRecognizedSpeechRevoker,
    std::weak_ptr<SampleRemoteMain> sampleRemoteMainWeak)
{
    onRecognizedSpeechRevoker = remoteSpeech.OnRecognizedSpeech(
        winrt::auto_revoke, [sampleRemoteMainWeak](const winrt::Microsoft::Holographic::AppRemoting::RecognizedSpeech& recognizedSpeech) {
            if (auto sampleRemoteMain = sampleRemoteMainWeak.lock())
            {
                sampleRemoteMain->OnRecognizedSpeech(recognizedSpeech.RecognizedText);
            }
        });

    auto grammarFile = co_await LoadGrammarFileAsync();

    std::vector<winrt::hstring> dictionary;
    dictionary.push_back(L"Red");
    dictionary.push_back(L"Blue");
    dictionary.push_back(L"Green");
    dictionary.push_back(L"Default");
    dictionary.push_back(L"Aquamarine");

    remoteSpeech.ApplyParameters(L"", grammarFile, dictionary);
}
```

<span data-ttu-id="e8337-178">有兩種方式可以指定要辨識的片語。</span><span class="sxs-lookup"><span data-stu-id="e8337-178">There are two ways of specifying phrases to be recognized.</span></span>
1) <span data-ttu-id="e8337-179">語音文法 xml 檔案內的規格。</span><span class="sxs-lookup"><span data-stu-id="e8337-179">Specification inside a speech grammar xml file.</span></span> <span data-ttu-id="e8337-180">如需詳細資料，請參閱 [如何建立基本的 XML 文法](https://docs.microsoft.com//previous-versions/office/developer/speech-technologies/hh361658(v=office.14)) 。</span><span class="sxs-lookup"><span data-stu-id="e8337-180">See [How to create a basic XML Grammar](https://docs.microsoft.com//previous-versions/office/developer/speech-technologies/hh361658(v=office.14)) for details.</span></span>
2) <span data-ttu-id="e8337-181">藉由將字典向量內的傳遞給來指定 ```ApplyParameters``` 。</span><span class="sxs-lookup"><span data-stu-id="e8337-181">Specify by passing them inside the dictionary vector to ```ApplyParameters```.</span></span>

<span data-ttu-id="e8337-182">在 OnRecognizedSpeech 回呼中，可以處理語音事件：</span><span class="sxs-lookup"><span data-stu-id="e8337-182">Inside the OnRecognizedSpeech callback the speech events can then be processed:</span></span>

```cpp
void SampleRemoteMain::OnRecognizedSpeech(const winrt::hstring& recognizedText)
{
    bool changedColor = false;
    DirectX::XMFLOAT4 color = {1, 1, 1, 1};

    if (recognizedText == L"Red")
    {
        color = {1, 0, 0, 1};
        changedColor = true;
    }
    else if (recognizedText == L"Blue")
    {
        color = {0, 0, 1, 1};
        changedColor = true;
    }
    else if (recognizedText == L"Green")
    {
        ...
    }

    ...
}
```

## <a name="preview-streamed-content-locally"></a><span data-ttu-id="e8337-183">在本機預覽資料流程內容</span><span class="sxs-lookup"><span data-stu-id="e8337-183">Preview streamed content locally</span></span>

<span data-ttu-id="e8337-184">若要在傳送至裝置的遠端應用程式中顯示相同的內容， ```OnSendFrame``` 可以使用遠端內容的事件。</span><span class="sxs-lookup"><span data-stu-id="e8337-184">To display the same content in the remote app that is send to the device the ```OnSendFrame``` event of the remote context can be used.</span></span> <span data-ttu-id="e8337-185">每次全像全像遠端連結 ```OnSendFrame``` 庫將目前的框架傳送到遠端裝置時，就會觸發此事件。</span><span class="sxs-lookup"><span data-stu-id="e8337-185">The ```OnSendFrame``` event is triggered every time the Holographic Remoting library sends the current frame to the remote device.</span></span> <span data-ttu-id="e8337-186">這是取得內容，並將它 array.blit 到桌面或 UWP 視窗的理想時間。</span><span class="sxs-lookup"><span data-stu-id="e8337-186">This is the ideal time to take the content and also blit it into the desktop or UWP window.</span></span>

```cpp
#include <windows.graphics.directx.direct3d11.interop.h>

...

m_onSendFrameEventRevoker = m_remoteContext.OnSendFrame(
    winrt::auto_revoke, [this](const winrt::Windows::Graphics::DirectX::Direct3D11::IDirect3DSurface& texture) {
        winrt::com_ptr<ID3D11Texture2D> texturePtr;
        {
            winrt::com_ptr<ID3D11Resource> resource;
            winrt::com_ptr<::IInspectable> inspectable = texture.as<::IInspectable>();
            winrt::com_ptr<Windows::Graphics::DirectX::Direct3D11::IDirect3DDxgiInterfaceAccess> dxgiInterfaceAccess;
            winrt::check_hresult(inspectable->QueryInterface(__uuidof(dxgiInterfaceAccess), dxgiInterfaceAccess.put_void()));
            winrt::check_hresult(dxgiInterfaceAccess->GetInterface(__uuidof(resource), resource.put_void()));
            resource.as(texturePtr);
        }

        // Copy / blit texturePtr into the back buffer here.
    });
```

## <a name="depth-reprojection"></a><span data-ttu-id="e8337-187">深度 Reprojection</span><span class="sxs-lookup"><span data-stu-id="e8337-187">Depth Reprojection</span></span>

<span data-ttu-id="e8337-188">從版本 [2.1.0](holographic-remoting-version-history.md#v2.1.0)開始，全像攝影遠端支援 [深度 Reprojection](hologram-stability.md#reprojection)。</span><span class="sxs-lookup"><span data-stu-id="e8337-188">Starting with version [2.1.0](holographic-remoting-version-history.md#v2.1.0), Holographic Remoting supports [Depth Reprojection](hologram-stability.md#reprojection).</span></span> <span data-ttu-id="e8337-189">除了色彩緩衝區之外，還需要從遠端應用程式將深度緩衝區串流至 HoloLens 2。</span><span class="sxs-lookup"><span data-stu-id="e8337-189">This requires, in addition to the color buffer, to also stream the depth buffer from the Remote application to the HoloLens 2.</span></span> <span data-ttu-id="e8337-190">預設會啟用深度緩衝區串流，並將其設定為使用色彩緩衝區的一半解析度。</span><span class="sxs-lookup"><span data-stu-id="e8337-190">By default depth buffer streaming is enabled and configured to use half the resolution of the color buffer.</span></span> <span data-ttu-id="e8337-191">這可以變更如下：</span><span class="sxs-lookup"><span data-stu-id="e8337-191">This can be changed as follows:</span></span>

```cpp
// class implementation
#include <HolographicAppRemoting\Streamer.h>

...

CreateRemoteContext(m_remoteContext, 20000, false, PreferredVideoCodec::Default);

// Configure for half-resolution depth.
m_remoteContext.ConfigureDepthVideoStream(DepthBufferStreamResolution::Half_Resolution);

```

<span data-ttu-id="e8337-192">請注意，如果不應該使用預設值，就 ```ConfigureDepthVideoStream``` 必須在建立 HoloLens 2 的連接之前呼叫。</span><span class="sxs-lookup"><span data-stu-id="e8337-192">Note, if default values should not be used ```ConfigureDepthVideoStream``` must be called before establishing a connection to the HoloLens 2.</span></span> <span data-ttu-id="e8337-193">最好的地方就是建立遠端內容。</span><span class="sxs-lookup"><span data-stu-id="e8337-193">The best place is right after you have created the remote context.</span></span> <span data-ttu-id="e8337-194">DepthBufferStreamResolution 的可能值為：</span><span class="sxs-lookup"><span data-stu-id="e8337-194">Possible values for DepthBufferStreamResolution are:</span></span>

* <span data-ttu-id="e8337-195">Full_Resolution</span><span class="sxs-lookup"><span data-stu-id="e8337-195">Full_Resolution</span></span>
* <span data-ttu-id="e8337-196">Half_Resolution</span><span class="sxs-lookup"><span data-stu-id="e8337-196">Half_Resolution</span></span>
* <span data-ttu-id="e8337-197">Quarter_Resolution</span><span class="sxs-lookup"><span data-stu-id="e8337-197">Quarter_Resolution</span></span>
* <span data-ttu-id="e8337-198">停用的 (在 [2.1.3](holographic-remoting-version-history.md#v2.1.3) 版本中新增，如果未使用，則會建立其他深度的影片串流) </span><span class="sxs-lookup"><span data-stu-id="e8337-198">Disabled (added with version [2.1.3](holographic-remoting-version-history.md#v2.1.3) and if used no additional depth video stream is created)</span></span>

<span data-ttu-id="e8337-199">請記住，使用完整的解析度深度緩衝區也會影響頻寬需求，而且需要在您提供的最大頻寬值中加以考慮 ```CreateRemoteContext``` 。</span><span class="sxs-lookup"><span data-stu-id="e8337-199">Keep in mind that using a full resolution depth buffer also affects bandwidth requirements and needs to be accounted for in the maximum bandwidth value you provide to ```CreateRemoteContext```.</span></span>

<span data-ttu-id="e8337-200">除了設定解決方案之外，您也必須透過 [HolographicCameraRenderingParameters. CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_)認可深度緩衝區。</span><span class="sxs-lookup"><span data-stu-id="e8337-200">Beside configuring the resolution you also have to commit a depth buffer via [HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_).</span></span>

```cpp

void SampleRemoteMain::Render(HolographicFrame holographicFrame)
{
    ...

    m_deviceResources->UseHolographicCameraResources([this, holographicFrame](auto& cameraResourceMap) {
        
        ...

        for (auto cameraPose : prediction.CameraPoses())
        {
            DXHelper::CameraResources* pCameraResources = cameraResourceMap[cameraPose.HolographicCamera().Id()].get();

            ...

            m_deviceResources->UseD3DDeviceContext([&](ID3D11DeviceContext3* context) {
                
                ...

                // Commit depth buffer if available and enabled.
                if (m_canCommitDirect3D11DepthBuffer && m_commitDirect3D11DepthBuffer)
                {
                    auto interopSurface = pCameraResources->GetDepthStencilTextureInteropObject();
                    HolographicCameraRenderingParameters renderingParameters = holographicFrame.GetRenderingParameters(cameraPose);
                    renderingParameters.CommitDirect3D11DepthBuffer(interopSurface);
                }
            });
        }
    });
}

```

<span data-ttu-id="e8337-201">若要確認 depth reprojection 是否正確運作 HoloLens 2 您可以透過裝置入口網站啟用深度視覺化。</span><span class="sxs-lookup"><span data-stu-id="e8337-201">To verify if depth reprojection is correctly working on HoloLens 2 you can enable a depth visualizer via the Device Portal.</span></span> <span data-ttu-id="e8337-202">如需詳細資料，請參閱 [驗證深度設定是否正確](hologram-stability.md#verifying-depth-is-set-correctly) 。</span><span class="sxs-lookup"><span data-stu-id="e8337-202">See [Verifying Depth is Set Correctly](hologram-stability.md#verifying-depth-is-set-correctly) for details.</span></span>

## <a name="optional-custom-data-channels"></a><span data-ttu-id="e8337-203">選用：自訂資料通道</span><span class="sxs-lookup"><span data-stu-id="e8337-203">Optional: Custom data channels</span></span>

<span data-ttu-id="e8337-204">自訂資料通道可以用來透過已建立的遠端連線來傳送使用者資料。</span><span class="sxs-lookup"><span data-stu-id="e8337-204">Custom data channels can be used to send user data over the already established remoting connection.</span></span> <span data-ttu-id="e8337-205">如需詳細資訊，請參閱 [自訂資料通道](holographic-remoting-custom-data-channels.md) 。</span><span class="sxs-lookup"><span data-stu-id="e8337-205">See [custom data channels](holographic-remoting-custom-data-channels.md) for more information.</span></span>

## <a name="see-also"></a><span data-ttu-id="e8337-206">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e8337-206">See Also</span></span>
* [<span data-ttu-id="e8337-207">撰寫自訂全像攝影遠端播放應用程式</span><span class="sxs-lookup"><span data-stu-id="e8337-207">Writing a custom Holographic Remoting player app</span></span>](holographic-remoting-create-player.md)
* [<span data-ttu-id="e8337-208">自訂全像攝影遠端資料通道</span><span class="sxs-lookup"><span data-stu-id="e8337-208">Custom Holographic Remoting data channels</span></span>](holographic-remoting-custom-data-channels.md)
* [<span data-ttu-id="e8337-209">建立全像攝影遠端處理的連線安全</span><span class="sxs-lookup"><span data-stu-id="e8337-209">Establishing a secure connection with Holographic Remoting</span></span>](holographic-remoting-secure-connection.md)
* [<span data-ttu-id="e8337-210">全像遠端的疑難排解和限制</span><span class="sxs-lookup"><span data-stu-id="e8337-210">Holographic Remoting troubleshooting and limitations</span></span>](holographic-remoting-troubleshooting.md)
* [<span data-ttu-id="e8337-211">全像攝影遠端軟體授權條款</span><span class="sxs-lookup"><span data-stu-id="e8337-211">Holographic Remoting software license terms</span></span>](https://docs.microsoft.com//legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [<span data-ttu-id="e8337-212">Microsoft 隱私權聲明</span><span class="sxs-lookup"><span data-stu-id="e8337-212">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)
