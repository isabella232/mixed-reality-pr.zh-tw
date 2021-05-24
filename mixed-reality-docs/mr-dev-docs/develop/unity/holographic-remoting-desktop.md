---
title: 傳統型應用程式中的全像全像遠端
description: 探索如何在傳統型應用程式中使用 OpenXR 的全像是全像的遠端處理。
author: hferrone
ms.author: alexturn
ms.date: 03/16/2021
ms.topic: article
keywords: openxr、unity、hololens、hololens 2、mixed reality、MRTK、Mixed Reality 工具組、增強的現實、虛擬實境、混合現實耳機、學習、教學課程、快速入門、全像桌面
ms.openlocfilehash: 18557af1f08ea05715b92b5072460871bb05a329
ms.sourcegitcommit: b195b82f7e83e2ac4f5d8937d169e9dcb865d46d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/24/2021
ms.locfileid: "110333412"
---
# <a name="holographic-remoting-in-desktop-app"></a><span data-ttu-id="44e0a-104">傳統型應用程式中的全像全像遠端</span><span class="sxs-lookup"><span data-stu-id="44e0a-104">Holographic Remoting in desktop app</span></span>

> [!NOTE]
> <span data-ttu-id="44e0a-105">0.1.3 套件版本已新增 Windows 獨立應用程式遠端支援。</span><span class="sxs-lookup"><span data-stu-id="44e0a-105">Windows Standalone app remoting support was added in the 0.1.3 package release.</span></span>
> <span data-ttu-id="44e0a-106">從版本0.1.3，此功能不支援 UWP 組建。</span><span class="sxs-lookup"><span data-stu-id="44e0a-106">As of version 0.1.3, this feature doesn’t support UWP builds.</span></span>

1. <span data-ttu-id="44e0a-107">遵循全像全像[遠端設定](unity-play-mode.md#holographic-remoting-setup)的步驟</span><span class="sxs-lookup"><span data-stu-id="44e0a-107">Follow the steps in [Holographic Remoting setup](unity-play-mode.md#holographic-remoting-setup)</span></span>
2. <span data-ttu-id="44e0a-108">開啟 [ **編輯-> 專案設定**]，流覽至 **XR 外掛程式管理**，然後選取 [ **Windows Mixed Reality 功能集** ] 方塊。</span><span class="sxs-lookup"><span data-stu-id="44e0a-108">Open **Edit -> Project Settings**, navigate to **XR plug-in Management**, and check the **Windows Mixed Reality feature set** box.</span></span> <span data-ttu-id="44e0a-109">此外，取消核取 [ **啟動時初始化 XR**]：</span><span class="sxs-lookup"><span data-stu-id="44e0a-109">Also, uncheck **Initialize XR on Startup**:</span></span>

    ![未核取 [啟動時，在 Unity 編輯器中開啟初始化 XR] 的 [專案設定] 面板螢幕擷取畫面](images/openxr-features-img-02-app.png)

3. <span data-ttu-id="44e0a-111">展開 [ **OpenXR** ] 底下的 [**功能**] 區段，然後選取 [**全部顯示**]</span><span class="sxs-lookup"><span data-stu-id="44e0a-111">Expand the **Features** section under **OpenXR** and select **Show All**</span></span>
4. <span data-ttu-id="44e0a-112">核取全像 **應用程式遠端處理** 的核取方塊：</span><span class="sxs-lookup"><span data-stu-id="44e0a-112">Check the **Holographic App Remoting** checkbox:</span></span>

    ![在 Unity 編輯器中開啟的 [專案設定] 面板的螢幕擷取畫面，其中已啟用應用程式遠端功能](images/openxr-features-img-03-app.png)

5. <span data-ttu-id="44e0a-114">接下來，撰寫一些程式碼來設定遠端設定，並觸發 XR 初始化。</span><span class="sxs-lookup"><span data-stu-id="44e0a-114">Next, write some code to set the remoting configuration and trigger XR initialization.</span></span> <span data-ttu-id="44e0a-115">使用 [Mixed Reality OpenXR 外掛程式](openxr-getting-started.md#unity-sample-projects-for-openxr-and-hololens-2) 散發的範例應用程式包含 AppRemoting，其中顯示在執行時間連接到特定 IP 位址的範例案例。</span><span class="sxs-lookup"><span data-stu-id="44e0a-115">The sample app distributed with the [Mixed Reality OpenXR Plugin](openxr-getting-started.md#unity-sample-projects-for-openxr-and-hololens-2) contains AppRemoting.cs, which shows an example scenario for connecting to a specific IP address at runtime.</span></span> <span data-ttu-id="44e0a-116">此時將範例應用程式部署到本機電腦，將會顯示具有 [連接] 按鈕的 IP 位址輸入欄位。</span><span class="sxs-lookup"><span data-stu-id="44e0a-116">Deploying the sample app to a local machine at this point will display an IP address input field with a connect button.</span></span> <span data-ttu-id="44e0a-117">輸入 IP 位址，然後按一下 [連線]，將會初始化 XR 並嘗試連線到目標裝置：</span><span class="sxs-lookup"><span data-stu-id="44e0a-117">Typing an IP address and clicking Connect will initialize XR and attempt to connect to the target device:</span></span>

    ![顯示範例應用程式遠端 UI 範例應用程式的螢幕擷取畫面](images/openxr-sample-app-remoting.png)

6. <span data-ttu-id="44e0a-119">若要撰寫自訂的連接程式碼，請使用已填寫的進行呼叫 `Microsoft.MixedReality.OpenXR.Remoting.AppRemoting.Connect` `RemotingConfiguration` 。</span><span class="sxs-lookup"><span data-stu-id="44e0a-119">To write custom connection code, call `Microsoft.MixedReality.OpenXR.Remoting.AppRemoting.Connect` with a filled-in `RemotingConfiguration`.</span></span> <span data-ttu-id="44e0a-120">範例應用程式會在偵測器中顯示這項功能，並示範如何從文字欄位填入 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="44e0a-120">The sample app exposes this in the inspector and shows how to fill in the IP address from a text field.</span></span> <span data-ttu-id="44e0a-121">呼叫 `Connect` 會設定並自動初始化 XR，這也是為什麼必須以協同程式的方式來呼叫它：</span><span class="sxs-lookup"><span data-stu-id="44e0a-121">Calling `Connect` will set the configuration and automatically initialize XR, which is why it must be called as a coroutine:</span></span>

    ``` cs
    StartCoroutine(Remoting.AppRemoting.Connect(remotingConfiguration));
    ```

7. <span data-ttu-id="44e0a-122">執行時，您可以使用 API 取得目前的線上狀態 `AppRemoting.TryGetConnectionState` ，並選擇性地使用中斷連接和解除初始化 XR `AppRemoting.Disconnect()` 。</span><span class="sxs-lookup"><span data-stu-id="44e0a-122">While running, you can obtain the current connection state with the `AppRemoting.TryGetConnectionState` API, and optionally disconnect and de-initialize XR using `AppRemoting.Disconnect()`.</span></span> <span data-ttu-id="44e0a-123">這可用來中斷連線，然後重新連線到相同應用程式會話內的不同裝置。</span><span class="sxs-lookup"><span data-stu-id="44e0a-123">This could be used to disconnect and reconnect to a different device within the same app session.</span></span> <span data-ttu-id="44e0a-124">範例應用程式會提供 tappable cube，以在點擊時中斷遠端會話的連接。</span><span class="sxs-lookup"><span data-stu-id="44e0a-124">The sample app provides a tappable cube which will disconnect the remoting session if tapped.</span></span>

### <a name="migration-from-previous-apis"></a><span data-ttu-id="44e0a-125">從先前的 Api 遷移</span><span class="sxs-lookup"><span data-stu-id="44e0a-125">Migration from previous APIs</span></span>

#### <a name="unityenginexrwsaholographicremoting"></a><span data-ttu-id="44e0a-126">UnityEngine. XR HolographicRemoting</span><span class="sxs-lookup"><span data-stu-id="44e0a-126">UnityEngine.XR.WSA.HolographicRemoting</span></span>

<span data-ttu-id="44e0a-127">從 [Unity](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/XR.WSA.HolographicRemoting.html)檔的範例程式碼：</span><span class="sxs-lookup"><span data-stu-id="44e0a-127">From the sample code on [Unity's docs](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/XR.WSA.HolographicRemoting.html):</span></span>

| <span data-ttu-id="44e0a-128">XR.Wsa。HolographicRemoting</span><span class="sxs-lookup"><span data-stu-id="44e0a-128">XR.WSA.HolographicRemoting</span></span> | <span data-ttu-id="44e0a-129">OpenXR. AppRemoting</span><span class="sxs-lookup"><span data-stu-id="44e0a-129">OpenXR.Remoting.AppRemoting</span></span> |
| ---- | ---- |
| `HolographicRemoting.Connect(String)` | `AppRemoting.Connect(RemotingConfiguration)` |
| `HolographicRemoting.ConnectionState` | `AppRemoting.TryGetConnectionState(out ConnectionState, out DisconnectReason)`|
| `StartCoroutine(LoadDevice("WindowsMR"))`| <span data-ttu-id="44e0a-130">[N/A：呼叫時自動發生 `AppRemoting.Connect`</span><span class="sxs-lookup"><span data-stu-id="44e0a-130">[N/A: Automatically happens when calling `AppRemoting.Connect`]</span></span>  |

#### <a name="unityenginexrwindowsmrwindowsmrremoting"></a><span data-ttu-id="44e0a-131">UnityEngine. XR. WindowsMR. WindowsMRRemoting</span><span class="sxs-lookup"><span data-stu-id="44e0a-131">UnityEngine.XR.WindowsMR.WindowsMRRemoting</span></span>

| <span data-ttu-id="44e0a-132">XR.WindowsMR.WindowsMRRemoting</span><span class="sxs-lookup"><span data-stu-id="44e0a-132">XR.WindowsMR.WindowsMRRemoting</span></span> | <span data-ttu-id="44e0a-133">OpenXR. AppRemoting</span><span class="sxs-lookup"><span data-stu-id="44e0a-133">OpenXR.Remoting.AppRemoting</span></span> |
| ---- | ---- |
| `WindowsMRRemoting.Connect()` | `AppRemoting.Connect(RemotingConfiguration)` |
| `WindowsMRRemoting.Disconnect()` | `AppRemoting.Disconnect()` |
| <span data-ttu-id="44e0a-134">`WindowsMRRemoting.TryGetConnectionState(out ConnectionState)` 和 `WindowsMRRemoting.TryGetConnectionFailureReason(out ConnectionFailureReason)`</span><span class="sxs-lookup"><span data-stu-id="44e0a-134">`WindowsMRRemoting.TryGetConnectionState(out ConnectionState)` and `WindowsMRRemoting.TryGetConnectionFailureReason(out ConnectionFailureReason)`</span></span>| `AppRemoting.TryGetConnectionState(out ConnectionState, out DisconnectReason)`|
| <span data-ttu-id="44e0a-135">`WindowsMRRemoting.isAudioEnabled`, `WindowsMRRemoting.maxBitRateKbps`, `WindowsMRRemoting.remoteMachineName`</span><span class="sxs-lookup"><span data-stu-id="44e0a-135">`WindowsMRRemoting.isAudioEnabled`, `WindowsMRRemoting.maxBitRateKbps`, `WindowsMRRemoting.remoteMachineName`</span></span> | <span data-ttu-id="44e0a-136">`AppRemoting.Connect`經由結構傳遞至 `RemotingConfiguration`</span><span class="sxs-lookup"><span data-stu-id="44e0a-136">Passed into `AppRemoting.Connect` via the `RemotingConfiguration` struct</span></span> |
| `WindowsMRRemoting.isConnected` | `AppRemoting.TryGetConnectionState(out ConnectionState state, out _) && state == ConnectionState.Connected`