---
title: Unity 中的 OpenXR 外掛程式支援功能
description: 探索 OpenXR 針對 Unity 中的混合現實開發所支援的功能。
author: hferrone
ms.author: alexturn
ms.date: 01/11/2021
ms.topic: article
keywords: openxr、unity、hololens、hololens 2、mixed reality、MRTK、Mixed Reality 工具組、增強的現實、虛擬實境、混合現實耳機、學習、教學課程、快速入門
ms.openlocfilehash: bad18c5f30465120bce370aa91c13ff3f229bef6
ms.sourcegitcommit: 029f247a6c33068360d3a06f2a473a12586017e1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2021
ms.locfileid: "100496132"
---
# <a name="mixed-reality-openxr-supported-features-in-unity"></a><span data-ttu-id="b54e9-104">混合現實 OpenXR Unity 中支援的功能</span><span class="sxs-lookup"><span data-stu-id="b54e9-104">Mixed Reality OpenXR supported features in Unity</span></span>

<span data-ttu-id="b54e9-105">**Mixed Reality OpenXR 外掛程式** 套件是 Unity **OpenXR 外掛程式** 的延伸模組，並支援 HoloLens 2 和 Windows Mixed Reality 耳機的功能套件。</span><span class="sxs-lookup"><span data-stu-id="b54e9-105">The **Mixed Reality OpenXR Plugin** package is an extension of Unity's **OpenXR Plugin** and supports a suite of features for HoloLens 2 and Windows Mixed Reality headsets.</span></span> <span data-ttu-id="b54e9-106">繼續之前，請確定您已安裝 **unity 2020.2** 或更新版本、 **OpenXR 外掛程式版本 0.1.3** 或更新版本，且您的 Unity 專案已 [設定 OpenXR](openxr-getting-started.md)。</span><span class="sxs-lookup"><span data-stu-id="b54e9-106">Before continuing, make sure that you've installed **Unity 2020.2** or later, **OpenXR Plugin version 0.1.3** or later, and your Unity project is [configured for OpenXR](openxr-getting-started.md).</span></span>

## <a name="whats-supported"></a><span data-ttu-id="b54e9-107">支援的項目</span><span class="sxs-lookup"><span data-stu-id="b54e9-107">What's supported</span></span>

<span data-ttu-id="b54e9-108">目前支援下列功能：</span><span class="sxs-lookup"><span data-stu-id="b54e9-108">The following features are currently supported:</span></span>

* <span data-ttu-id="b54e9-109">支援 HoloLens 2 的 UWP 應用程式，並針對 HoloLens 2 應用程式模型進行優化。</span><span class="sxs-lookup"><span data-stu-id="b54e9-109">Supports UWP applications for HoloLens 2, and optimize for HoloLens 2 application model.</span></span>
* <span data-ttu-id="b54e9-110">支援適用于 Windows Mixed Reality 耳機的 Win32 VR 應用程式，具有最新的控制器設定檔和全像應用程式遠端。</span><span class="sxs-lookup"><span data-stu-id="b54e9-110">Supports Win32 VR applications for Windows Mixed Reality headset with latest controller profiles and holographic app remoting.</span></span>
* <span data-ttu-id="b54e9-111">使用錨點和未系結空間的世界規模追蹤。</span><span class="sxs-lookup"><span data-stu-id="b54e9-111">World scale tracking using Anchors and Unbounded space.</span></span>
* <span data-ttu-id="b54e9-112">[錨點儲存體 API，以將錨點保存](#anchors-and-anchor-persistence) 到 HoloLens 2 的本機儲存體。</span><span class="sxs-lookup"><span data-stu-id="b54e9-112">[Anchor storage API to persist anchors](#anchors-and-anchor-persistence) to HoloLens 2 local storage.</span></span>
* <span data-ttu-id="b54e9-113">[移動控制器和手互動](#motion-controller-and-hand-interactions)，包括新的 HP 回音卡控制器。</span><span class="sxs-lookup"><span data-stu-id="b54e9-113">[Motion controller and hand interactions](#motion-controller-and-hand-interactions), including the new HP Reverb G2 controller.</span></span>
* <span data-ttu-id="b54e9-114">使用26個接點和聯合半徑輸入，以明確表述的手勢進行追蹤。</span><span class="sxs-lookup"><span data-stu-id="b54e9-114">Articulated hand tracking using 26 joints and joint radius inputs.</span></span>
* <span data-ttu-id="b54e9-115">HoloLens 2 上的眼睛注視互動。</span><span class="sxs-lookup"><span data-stu-id="b54e9-115">Eye gaze interaction on HoloLens 2.</span></span>
* <span data-ttu-id="b54e9-116">HoloLens 2 上尋找 (PV) 攝影機的相片/影片。</span><span class="sxs-lookup"><span data-stu-id="b54e9-116">Locating photo/video (PV) camera on HoloLens 2.</span></span>
* <span data-ttu-id="b54e9-117">混合實境擷取使用透過 PV 攝影機的第三種眼睛呈現。</span><span class="sxs-lookup"><span data-stu-id="b54e9-117">Mixed Reality Capture using 3rd eye rendering through PV camera.</span></span>
* <span data-ttu-id="b54e9-118">支援「播放」以使用全像「 [遠端處理」應用程式 HoloLens 2](#holographic-remoting-in-unity-editor-play-mode)，讓開發人員不需要建立及部署到裝置，即可將腳本進行偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="b54e9-118">Supports ["Play" to HoloLens 2 with the Holographic Remoting app](#holographic-remoting-in-unity-editor-play-mode), allowing developers to debug scripts without building and deploying to the device.</span></span>
* <span data-ttu-id="b54e9-119">透過 [MRTK OpenXR 提供者支援](openxr-getting-started.md#using-mrtk-with-openxr-support)，與 MRTK Unity 2.5.3 和更新版本相容。</span><span class="sxs-lookup"><span data-stu-id="b54e9-119">Compatible with MRTK Unity 2.5.3 and newer through [MRTK OpenXR provider support](openxr-getting-started.md#using-mrtk-with-openxr-support).</span></span>
* <span data-ttu-id="b54e9-120">與 Unity [ARFoundation 4.0](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html) 或更新版本相容。</span><span class="sxs-lookup"><span data-stu-id="b54e9-120">Compatible with Unity [ARFoundation 4.0](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html) or later.</span></span>
* <span data-ttu-id="b54e9-121"> (在 0.1.3) 中新增的功能，可支援從組建和部署的 Windows 獨立應用程式進行傳統型 [應用程式](#holographic-remoting-in-desktop-app) 全像開發。</span><span class="sxs-lookup"><span data-stu-id="b54e9-121">(Added in 0.1.3) Supports [desktop app Holographic Remoting](#holographic-remoting-in-desktop-app) from a built and deployed Windows Standalone app.</span></span>

## <a name="holographic-remoting-setup"></a><span data-ttu-id="b54e9-122">全像遠端設定</span><span class="sxs-lookup"><span data-stu-id="b54e9-122">Holographic Remoting setup</span></span>

1. <span data-ttu-id="b54e9-123">首先，您必須從 HoloLens 2 上的 Microsoft Store 安裝全像[遠端播放機應用程式](https://www.microsoft.com/store/productId/9NBLGGH4SV40)</span><span class="sxs-lookup"><span data-stu-id="b54e9-123">First, you need to [install the Holographic Remoting Player app](https://www.microsoft.com/store/productId/9NBLGGH4SV40) from the Microsoft Store on your HoloLens 2</span></span>
2. <span data-ttu-id="b54e9-124">在 HoloLens 2 上執行全像遠端播放播放程式應用程式，您會看到要連接的版本號碼和 IP 位址</span><span class="sxs-lookup"><span data-stu-id="b54e9-124">Run the Holographic Remoting Player app on HoloLens 2 and you'll see the version number and IP address to connect to</span></span>
    * <span data-ttu-id="b54e9-125">您將需要2.4 或更新版本才能使用 OpenXR 外掛程式</span><span class="sxs-lookup"><span data-stu-id="b54e9-125">You'll need v2.4 or later to work with the OpenXR plugin</span></span>

    ![HoloLens 中執行的全像 Remoting 播放程式的螢幕擷取畫面](images/openxr-features-img-01.png)

## <a name="holographic-remoting-in-unity-editor-play-mode"></a><span data-ttu-id="b54e9-127">Unity 編輯器 play 模式的全像遠端功能</span><span class="sxs-lookup"><span data-stu-id="b54e9-127">Holographic Remoting in Unity Editor play mode</span></span>

<span data-ttu-id="b54e9-128">在 Visual Studio 專案中建立 UWP Unity 專案，然後將它封裝並部署到 HoloLens 2 裝置，可能需要一些時間。</span><span class="sxs-lookup"><span data-stu-id="b54e9-128">Building a UWP Unity project in Visual Studio project and then packaging and deploying it to a HoloLens 2 device can take some time.</span></span> <span data-ttu-id="b54e9-129">其中一個解決方法是啟用全像「全像」編輯器遠端功能，讓您透過網路直接使用「播放」模式來將 c # 腳本進行 HoloLens 2 裝置的偵測。</span><span class="sxs-lookup"><span data-stu-id="b54e9-129">One solution is to enable the Holographic Editor Remoting feature, which lets you debug your C# script using “Play” mode directly to a HoloLens 2 device over your network.</span></span> <span data-ttu-id="b54e9-130">此案例可避免建立 UWP 套件並將其部署至遠端裝置的額外負荷。</span><span class="sxs-lookup"><span data-stu-id="b54e9-130">This scenario avoids the overhead of building and deploying a UWP package to remote device.</span></span>

1. <span data-ttu-id="b54e9-131">遵循全像全像[遠端設定](#holographic-remoting-setup)的步驟</span><span class="sxs-lookup"><span data-stu-id="b54e9-131">Follow the steps in [Holographic Remoting setup](#holographic-remoting-setup)</span></span>
2. <span data-ttu-id="b54e9-132">開啟 [ **編輯-> 專案設定**]，流覽至 **XR 外掛程式管理**，然後選取 [ **Windows Mixed Reality 功能集** ] 方塊：</span><span class="sxs-lookup"><span data-stu-id="b54e9-132">Open **Edit -> Project Settings**, navigate to **XR plug-in Management**, and check the **Windows Mixed Reality feature set** box:</span></span>

    ![醒目提示 XR 外掛程式管理的 Unity 編輯器中開啟之 [專案設定] 面板的螢幕擷取畫面](images/openxr-features-img-02.png)

3. <span data-ttu-id="b54e9-134">展開 [ **OpenXR** ] 底下的 [**功能**] 區段，然後選取 [**全部顯示**]</span><span class="sxs-lookup"><span data-stu-id="b54e9-134">Expand the **Features** section under **OpenXR** and select **Show All**</span></span>
4. <span data-ttu-id="b54e9-135">核取 [全像攝影 **編輯器遠端處理** ] 核取方塊，然後輸入您從「全像」遠端應用程式取得的 IP 位址</span><span class="sxs-lookup"><span data-stu-id="b54e9-135">Check the **Holographic Editor Remoting** checkbox and input the IP address you get from the Holographic Remoting app:</span></span>

    ![在 Unity 編輯器中開啟專案設定面板的螢幕擷取畫面，其中已醒目提示功能](images/openxr-features-img-03.png)

<span data-ttu-id="b54e9-137">現在您可以按一下 [播放] 按鈕，以在 HoloLens 上的全像遠端應用程式中播放 Unity 應用程式。</span><span class="sxs-lookup"><span data-stu-id="b54e9-137">Now you can click the “Play” button to play your Unity app into the Holographic Remoting app on your HoloLens.</span></span> <span data-ttu-id="b54e9-138">您也可以 [將 Visual Studio 附加至 Unity](/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows) ，以在播放模式中進行 c # 腳本的調試。</span><span class="sxs-lookup"><span data-stu-id="b54e9-138">You can also [attach Visual Studio to Unity](/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows) to debug C# scripts in the play mode.</span></span>

> [!NOTE]
> <span data-ttu-id="b54e9-139">從0.1.0 版起，全像「全像」遠端執行時間不支援錨點，而 ARAnchorManager 功能將無法透過遠端處理。</span><span class="sxs-lookup"><span data-stu-id="b54e9-139">As of version 0.1.0, the Holographic Remoting runtime doesn’t support Anchors, and ARAnchorManager functionalities will not work through remoting.</span></span>  <span data-ttu-id="b54e9-140">這項功能會在未來的版本中推出。</span><span class="sxs-lookup"><span data-stu-id="b54e9-140">This feature is coming in future releases.</span></span>

## <a name="holographic-remoting-in-desktop-app"></a><span data-ttu-id="b54e9-141">傳統型應用程式中的全像全像遠端</span><span class="sxs-lookup"><span data-stu-id="b54e9-141">Holographic Remoting in desktop app</span></span>

> [!NOTE]
> <span data-ttu-id="b54e9-142">0.1.3 套件版本已新增 Windows 獨立應用程式遠端支援。</span><span class="sxs-lookup"><span data-stu-id="b54e9-142">Windows Standalone app remoting support was added in the 0.1.3 package release.</span></span>
> <span data-ttu-id="b54e9-143">從版本0.1.3，此功能不支援 UWP 組建。</span><span class="sxs-lookup"><span data-stu-id="b54e9-143">As of version 0.1.3, this feature doesn’t support UWP builds.</span></span>

1. <span data-ttu-id="b54e9-144">遵循全像全像[遠端設定](#holographic-remoting-setup)的步驟</span><span class="sxs-lookup"><span data-stu-id="b54e9-144">Follow the steps in [Holographic Remoting setup](#holographic-remoting-setup)</span></span>
2. <span data-ttu-id="b54e9-145">開啟 [ **編輯-> 專案設定**]，流覽至 **XR 外掛程式管理**，然後選取 [ **Windows Mixed Reality 功能集** ] 方塊。</span><span class="sxs-lookup"><span data-stu-id="b54e9-145">Open **Edit -> Project Settings**, navigate to **XR plug-in Management**, and check the **Windows Mixed Reality feature set** box.</span></span> <span data-ttu-id="b54e9-146">此外，取消核取 [ **啟動時初始化 XR**]：</span><span class="sxs-lookup"><span data-stu-id="b54e9-146">Also, uncheck **Initialize XR on Startup**:</span></span>

    ![未核取 [啟動時，在 Unity 編輯器中開啟初始化 XR] 的 [專案設定] 面板螢幕擷取畫面](images/openxr-features-img-02-app.png)

3. <span data-ttu-id="b54e9-148">展開 [ **OpenXR** ] 底下的 [**功能**] 區段，然後選取 [**全部顯示**]</span><span class="sxs-lookup"><span data-stu-id="b54e9-148">Expand the **Features** section under **OpenXR** and select **Show All**</span></span>
4. <span data-ttu-id="b54e9-149">核取全像 **應用程式遠端處理** 的核取方塊：</span><span class="sxs-lookup"><span data-stu-id="b54e9-149">Check the **Holographic App Remoting** checkbox:</span></span>

    ![在 Unity 編輯器中開啟的 [專案設定] 面板的螢幕擷取畫面，其中已啟用應用程式遠端功能](images/openxr-features-img-03-app.png)

5. <span data-ttu-id="b54e9-151">接下來，撰寫一些程式碼來設定遠端設定，並觸發 XR 初始化。</span><span class="sxs-lookup"><span data-stu-id="b54e9-151">Next, write some code to set the remoting configuration and trigger XR initialization.</span></span> <span data-ttu-id="b54e9-152">使用 [Mixed Reality OpenXR 外掛程式](openxr-getting-started.md#hololens-2-samples) 散發的範例應用程式包含 AppRemoting.cs，其中顯示在執行時間連接到特定 IP 位址的範例案例。</span><span class="sxs-lookup"><span data-stu-id="b54e9-152">The sample app distributed with the [Mixed Reality OpenXR Plugin](openxr-getting-started.md#hololens-2-samples) contains AppRemoting.cs, which shows an example scenario for connecting to a specific IP address at runtime.</span></span> <span data-ttu-id="b54e9-153">此時將範例應用程式部署到本機電腦，將會顯示具有 [連接] 按鈕的 IP 位址輸入欄位。</span><span class="sxs-lookup"><span data-stu-id="b54e9-153">Deploying the sample app to a local machine at this point will display an IP address input field with a connect button.</span></span> <span data-ttu-id="b54e9-154">輸入 IP 位址，然後按一下 [連線]，將會初始化 XR 並嘗試連線到目標裝置：</span><span class="sxs-lookup"><span data-stu-id="b54e9-154">Typing an IP address and clicking Connect will initialize XR and attempt to connect to the target device:</span></span>

    ![顯示範例應用程式遠端 UI 範例應用程式的螢幕擷取畫面](images/openxr-sample-app-remoting.png)

6. <span data-ttu-id="b54e9-156">若要撰寫自訂的連接程式碼，請使用已填寫的進行呼叫 `Microsoft.MixedReality.OpenXR.Remoting.AppRemoting.Connect` `RemotingConfiguration` 。</span><span class="sxs-lookup"><span data-stu-id="b54e9-156">To write custom connection code, call `Microsoft.MixedReality.OpenXR.Remoting.AppRemoting.Connect` with a filled-in `RemotingConfiguration`.</span></span> <span data-ttu-id="b54e9-157">範例應用程式會在偵測器中顯示這項功能，並示範如何從文字欄位填入 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="b54e9-157">The sample app exposes this in the inspector and shows how to fill in the IP address from a text field.</span></span> <span data-ttu-id="b54e9-158">呼叫 `Connect` 會設定並自動初始化 XR，這也是為什麼必須以協同程式的方式來呼叫它：</span><span class="sxs-lookup"><span data-stu-id="b54e9-158">Calling `Connect` will set the configuration and automatically initialize XR, which is why it must be called as a coroutine:</span></span>

    ``` cs
    StartCoroutine(Remoting.AppRemoting.Connect(remotingConfiguration));
    ```

7. <span data-ttu-id="b54e9-159">執行時，您可以使用 API 取得目前的線上狀態 `AppRemoting.TryGetConnectionState` ，並選擇性地使用中斷連接和解除初始化 XR `AppRemoting.Disconnect()` 。</span><span class="sxs-lookup"><span data-stu-id="b54e9-159">While running, you can obtain the current connection state with the `AppRemoting.TryGetConnectionState` API, and optionally disconnect and de-initialize XR using `AppRemoting.Disconnect()`.</span></span> <span data-ttu-id="b54e9-160">這可用來中斷連線，然後重新連線到相同應用程式會話內的不同裝置。</span><span class="sxs-lookup"><span data-stu-id="b54e9-160">This could be used to disconnect and reconnect to a different device within the same app session.</span></span> <span data-ttu-id="b54e9-161">範例應用程式會提供 tappable cube，以在點擊時中斷遠端會話的連接。</span><span class="sxs-lookup"><span data-stu-id="b54e9-161">The sample app provides a tappable cube which will disconnect the remoting session if tapped.</span></span>

### <a name="migration-from-previous-apis"></a><span data-ttu-id="b54e9-162">從先前的 Api 遷移</span><span class="sxs-lookup"><span data-stu-id="b54e9-162">Migration from previous APIs</span></span>

#### <a name="unityenginexrwsaholographicremoting"></a><span data-ttu-id="b54e9-163">UnityEngine. XR HolographicRemoting</span><span class="sxs-lookup"><span data-stu-id="b54e9-163">UnityEngine.XR.WSA.HolographicRemoting</span></span>

<span data-ttu-id="b54e9-164">從 [Unity](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/XR.WSA.HolographicRemoting.html)檔的範例程式碼：</span><span class="sxs-lookup"><span data-stu-id="b54e9-164">From the sample code on [Unity's docs](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/XR.WSA.HolographicRemoting.html):</span></span>

| <span data-ttu-id="b54e9-165">XR.Wsa。HolographicRemoting</span><span class="sxs-lookup"><span data-stu-id="b54e9-165">XR.WSA.HolographicRemoting</span></span> | <span data-ttu-id="b54e9-166">OpenXR. AppRemoting</span><span class="sxs-lookup"><span data-stu-id="b54e9-166">OpenXR.Remoting.AppRemoting</span></span> |
| ---- | ---- |
| `HolographicRemoting.Connect(String)` | `AppRemoting.Connect(RemotingConfiguration)` |
| `HolographicRemoting.ConnectionState` | `AppRemoting.TryGetConnectionState(out ConnectionState, out DisconnectReason)`|
| `StartCoroutine(LoadDevice("WindowsMR"))`| <span data-ttu-id="b54e9-167">[N/A：呼叫時自動發生 `AppRemoting.Connect`</span><span class="sxs-lookup"><span data-stu-id="b54e9-167">[N/A: Automatically happens when calling `AppRemoting.Connect`]</span></span>  |

#### <a name="unityenginexrwindowsmrwindowsmrremoting"></a><span data-ttu-id="b54e9-168">UnityEngine. XR. WindowsMR. WindowsMRRemoting</span><span class="sxs-lookup"><span data-stu-id="b54e9-168">UnityEngine.XR.WindowsMR.WindowsMRRemoting</span></span>

| <span data-ttu-id="b54e9-169">XR.WindowsMR.WindowsMRRemoting</span><span class="sxs-lookup"><span data-stu-id="b54e9-169">XR.WindowsMR.WindowsMRRemoting</span></span> | <span data-ttu-id="b54e9-170">OpenXR. AppRemoting</span><span class="sxs-lookup"><span data-stu-id="b54e9-170">OpenXR.Remoting.AppRemoting</span></span> |
| ---- | ---- |
| `WindowsMRRemoting.Connect()` | `AppRemoting.Connect(RemotingConfiguration)` |
| `WindowsMRRemoting.Disconnect()` | `AppRemoting.Disconnect()` |
| <span data-ttu-id="b54e9-171">`WindowsMRRemoting.TryGetConnectionState(out ConnectionState)` 和 `WindowsMRRemoting.TryGetConnectionFailureReason(out ConnectionFailureReason)`</span><span class="sxs-lookup"><span data-stu-id="b54e9-171">`WindowsMRRemoting.TryGetConnectionState(out ConnectionState)` and `WindowsMRRemoting.TryGetConnectionFailureReason(out ConnectionFailureReason)`</span></span>| `AppRemoting.TryGetConnectionState(out ConnectionState, out DisconnectReason)`|
| <span data-ttu-id="b54e9-172">`WindowsMRRemoting.isAudioEnabled`, `WindowsMRRemoting.maxBitRateKbps`, `WindowsMRRemoting.remoteMachineName`</span><span class="sxs-lookup"><span data-stu-id="b54e9-172">`WindowsMRRemoting.isAudioEnabled`, `WindowsMRRemoting.maxBitRateKbps`, `WindowsMRRemoting.remoteMachineName`</span></span> | <span data-ttu-id="b54e9-173">`AppRemoting.Connect`經由結構傳遞至 `RemotingConfiguration`</span><span class="sxs-lookup"><span data-stu-id="b54e9-173">Passed into `AppRemoting.Connect` via the `RemotingConfiguration` struct</span></span> |
| `WindowsMRRemoting.isConnected` | `AppRemoting.TryGetConnectionState(out ConnectionState state, out _) && state == ConnectionState.Connected`

## <a name="anchors-and-anchor-persistence"></a><span data-ttu-id="b54e9-174">錨點和錨點持續性</span><span class="sxs-lookup"><span data-stu-id="b54e9-174">Anchors and Anchor Persistence</span></span>

<span data-ttu-id="b54e9-175">Mixed Reality OpenXR 外掛程式透過 Unity 的 ARFoundation **ARAnchorManager** 的執行，提供基本錨定功能。</span><span class="sxs-lookup"><span data-stu-id="b54e9-175">The Mixed Reality OpenXR Plugin supplies basic anchor functionality through an implementation of Unity’s ARFoundation **ARAnchorManager**.</span></span> <span data-ttu-id="b54e9-176">若要瞭解 ARFoundation 中 **ARAnchor** 的基本概念，請造訪 [AR 錨點管理員的 ARFoundation 手冊](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/anchor-manager.html)。</span><span class="sxs-lookup"><span data-stu-id="b54e9-176">To learn the basics on **ARAnchor** s in ARFoundation, visit the [ARFoundation Manual for AR Anchor Manager](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/anchor-manager.html).</span></span> <span data-ttu-id="b54e9-177">從版本0.1.0，此外掛程式除了建立附加至平面的錨點（即將在未來版本中）之外，也支援所有 ARAnchorManager 功能。</span><span class="sxs-lookup"><span data-stu-id="b54e9-177">As of version 0.1.0, this plugin supports all ARAnchorManager functionality except creating anchors attached to a plane, which is coming in a future release.</span></span>

### <a name="anchor-persistence-and-the-xranchorstore"></a><span data-ttu-id="b54e9-178">錨點持續性和 XRAnchorStore</span><span class="sxs-lookup"><span data-stu-id="b54e9-178">Anchor Persistence and the XRAnchorStore</span></span>

<span data-ttu-id="b54e9-179">另一個稱為 **XRAnchorStore** 的 API 可讓錨點在會話之間保存。</span><span class="sxs-lookup"><span data-stu-id="b54e9-179">An additional API called the **XRAnchorStore** enables anchors to be persisted between sessions.</span></span> <span data-ttu-id="b54e9-180">XRAnchorStore 是您裝置上已儲存錨點的標記法。</span><span class="sxs-lookup"><span data-stu-id="b54e9-180">The XRAnchorStore is a representation of the saved anchors on your device.</span></span> <span data-ttu-id="b54e9-181">錨點可以從 Unity 場景中的 **ARAnchors** 保存、從儲存體載入至新的 **ARAnchors**，或從儲存體中刪除。</span><span class="sxs-lookup"><span data-stu-id="b54e9-181">Anchors can be persisted from **ARAnchors** in the Unity scene, loaded from storage into new **ARAnchors**, or deleted from storage.</span></span>

> [!NOTE]
> <span data-ttu-id="b54e9-182">這些錨點會儲存並載入至相同的裝置。</span><span class="sxs-lookup"><span data-stu-id="b54e9-182">These anchors are to be saved and loaded on the same device.</span></span> <span data-ttu-id="b54e9-183">未來版本中的 Azure 空間錨點將會支援跨裝置錨定儲存體。</span><span class="sxs-lookup"><span data-stu-id="b54e9-183">Cross-device anchor storage will be supported through Azure Spatial Anchors in a future release.</span></span>

``` cs
public class Microsoft.MixedReality.ARSubsystems.XRAnchorStore
{
    // A list of all persisted anchors, which can be loaded.
    public IReadOnlyList<string> PersistedAnchorNames { get; }

    // Clear all persisted anchors
    public void Clear();

    // Load a single persisted anchor by name. The ARAnchorManager will create this new anchor and report it in
    // the ARAnchorManager.anchorsChanged event. The TrackableId returned here is the same TrackableId the
    // ARAnchor will have when it is instantiated.
    public TrackableId LoadAnchor(string name);

    // Attempts to persist an existing ARAnchor with the given TrackableId to the local store. Returns true if
    // the storage is successful, false otherwise.
    public bool TryPersistAnchor(string name, TrackableId trackableId);

    // Removes a single persisted anchor from the anchor store. This will not affect any ARAnchors in the Unity
    // scene, only the anchors in storage.
    public void UnpersistAnchor(string name);
}
```

<span data-ttu-id="b54e9-184">為了載入 XRAnchorStore，外掛程式會在 XRAnchorSubsystem （ARAnchorManager 的子系統）上提供擴充方法：</span><span class="sxs-lookup"><span data-stu-id="b54e9-184">To load the XRAnchorStore, the plugin provides an extension method on the XRAnchorSubsystem, the subsystem of an ARAnchorManager:</span></span>

``` cs
public static Task<XRAnchorStore> LoadAnchorStoreAsync(this XRAnchorSubsystem anchorSubsystem)
```

<span data-ttu-id="b54e9-185">若要使用此擴充方法，請從 ARAnchorManager 的子系統進行存取，如下所示：</span><span class="sxs-lookup"><span data-stu-id="b54e9-185">To use this extension method, access it from an ARAnchorManager's subsystem as follows:</span></span>

``` cs
ARAnchorManager arAnchorManager = GetComponent<ARAnchorManager>();
XRAnchorStore anchorStore = await arAnchorManager.subsystem.LoadAnchorStoreAsync();
```

<span data-ttu-id="b54e9-186">若要查看保存/unpersisting 錨點的完整範例，請查看 [混合現實 OpenXR 外掛程式範例場景](openxr-getting-started.md#hololens-2-samples)中的錨點 > 錨點範例 GameObject 和 AnchorsSample.cs 腳本：</span><span class="sxs-lookup"><span data-stu-id="b54e9-186">To see a full example of persisting / unpersisting anchors, check out the Anchors -> Anchors Sample GameObject and AnchorsSample.cs script in the [Mixed Reality OpenXR Plugin Sample Scene](openxr-getting-started.md#hololens-2-samples):</span></span>

![在 Unity 編輯器中開啟之 [階層] 面板的螢幕擷取畫面，其中已醒目提示錨點範例](images/openxr-features-img-04.png)

![在 Unity 編輯器中開啟的 [偵測器] 面板的螢幕擷取畫面，其中已醒目提示錨點範例腳本](images/openxr-features-img-05.png)

## <a name="motion-controller-and-hand-interactions"></a><span data-ttu-id="b54e9-189">移動控制器和手互動</span><span class="sxs-lookup"><span data-stu-id="b54e9-189">Motion controller and hand interactions</span></span>

<span data-ttu-id="b54e9-190">若要瞭解 Unity 中混合現實互動的基本概念，請流覽 unity [Manual For UNITY XR 輸入](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html)。</span><span class="sxs-lookup"><span data-stu-id="b54e9-190">To learn the basics about mixed reality interactions in Unity, visit the [Unity Manual for Unity XR Input](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html).</span></span> <span data-ttu-id="b54e9-191">這項 Unity 檔涵蓋從控制器專屬輸入到更一般化 **InputFeatureUsage** 的對應、如何識別和分類可用的 XR 輸入、如何從這些輸入讀取資料等等。</span><span class="sxs-lookup"><span data-stu-id="b54e9-191">This Unity documentation covers the mappings from controller-specific inputs to more generalizable **InputFeatureUsage** s, how available XR inputs can be identified and categorized, how to read data from these inputs, and more.</span></span>

<span data-ttu-id="b54e9-192">Mixed Reality OpenXR 外掛程式提供額外的輸入互動設定檔，對應至標準 **InputFeatureUsage** s，如下所述：</span><span class="sxs-lookup"><span data-stu-id="b54e9-192">The Mixed Reality OpenXR Plugin provides additional input interaction profiles, mapped to standard **InputFeatureUsage** s as detailed below:</span></span>

| <span data-ttu-id="b54e9-193">InputFeatureUsage</span><span class="sxs-lookup"><span data-stu-id="b54e9-193">InputFeatureUsage</span></span> | <span data-ttu-id="b54e9-194">HP 回音 (OpenXR) </span><span class="sxs-lookup"><span data-stu-id="b54e9-194">HP Reverb G2 Controller (OpenXR)</span></span> | <span data-ttu-id="b54e9-195">HoloLens (OpenXR) </span><span class="sxs-lookup"><span data-stu-id="b54e9-195">HoloLens Hand (OpenXR)</span></span> |
| ---- | ---- | ---- |
| <span data-ttu-id="b54e9-196">primary2DAxis</span><span class="sxs-lookup"><span data-stu-id="b54e9-196">primary2DAxis</span></span> | <span data-ttu-id="b54e9-197">操縱 杆</span><span class="sxs-lookup"><span data-stu-id="b54e9-197">Joystick</span></span> | |
| <span data-ttu-id="b54e9-198">primary2DAxisClick</span><span class="sxs-lookup"><span data-stu-id="b54e9-198">primary2DAxisClick</span></span> | <span data-ttu-id="b54e9-199">搖桿-按一下</span><span class="sxs-lookup"><span data-stu-id="b54e9-199">Joystick - Click</span></span> | |
| <span data-ttu-id="b54e9-200">觸發程序 (trigger)</span><span class="sxs-lookup"><span data-stu-id="b54e9-200">trigger</span></span> | <span data-ttu-id="b54e9-201">觸發程序</span><span class="sxs-lookup"><span data-stu-id="b54e9-201">Trigger</span></span>  | |
| <span data-ttu-id="b54e9-202">握</span><span class="sxs-lookup"><span data-stu-id="b54e9-202">grip</span></span> | <span data-ttu-id="b54e9-203">握</span><span class="sxs-lookup"><span data-stu-id="b54e9-203">Grip</span></span> | <span data-ttu-id="b54e9-204">點擊或擠壓</span><span class="sxs-lookup"><span data-stu-id="b54e9-204">Air tap or squeeze</span></span> |
| <span data-ttu-id="b54e9-205">primaryButton</span><span class="sxs-lookup"><span data-stu-id="b54e9-205">primaryButton</span></span> | <span data-ttu-id="b54e9-206">[X/A]-按下</span><span class="sxs-lookup"><span data-stu-id="b54e9-206">[X/A] - Press</span></span> | <span data-ttu-id="b54e9-207">空中點選</span><span class="sxs-lookup"><span data-stu-id="b54e9-207">Air tap</span></span> |
| <span data-ttu-id="b54e9-208">secondaryButton</span><span class="sxs-lookup"><span data-stu-id="b54e9-208">secondaryButton</span></span> | <span data-ttu-id="b54e9-209">[Y/B]-按下</span><span class="sxs-lookup"><span data-stu-id="b54e9-209">[Y/B] - Press</span></span> | |
| <span data-ttu-id="b54e9-210">gripButton</span><span class="sxs-lookup"><span data-stu-id="b54e9-210">gripButton</span></span> | <span data-ttu-id="b54e9-211">握住-按</span><span class="sxs-lookup"><span data-stu-id="b54e9-211">Grip - Press</span></span> | |
| <span data-ttu-id="b54e9-212">triggerButton</span><span class="sxs-lookup"><span data-stu-id="b54e9-212">triggerButton</span></span> | <span data-ttu-id="b54e9-213">觸發程式-按下</span><span class="sxs-lookup"><span data-stu-id="b54e9-213">Trigger - Press</span></span> | |
| <span data-ttu-id="b54e9-214">menuButton</span><span class="sxs-lookup"><span data-stu-id="b54e9-214">menuButton</span></span> | <span data-ttu-id="b54e9-215">功能表</span><span class="sxs-lookup"><span data-stu-id="b54e9-215">Menu</span></span> | |

### <a name="aim-and-grip-poses"></a><span data-ttu-id="b54e9-216">目標和底姿勢</span><span class="sxs-lookup"><span data-stu-id="b54e9-216">Aim and Grip Poses</span></span>

<span data-ttu-id="b54e9-217">您可以透過 OpenXR 輸入互動存取兩組姿勢：</span><span class="sxs-lookup"><span data-stu-id="b54e9-217">You have access to two sets of poses through OpenXR input interactions:</span></span>

* <span data-ttu-id="b54e9-218">抓手中呈現物件的底框</span><span class="sxs-lookup"><span data-stu-id="b54e9-218">The grip poses for rendering objects in the hand</span></span>
* <span data-ttu-id="b54e9-219">目標是指向世界。</span><span class="sxs-lookup"><span data-stu-id="b54e9-219">The aim poses for pointing into the world.</span></span>

<span data-ttu-id="b54e9-220">有關此設計的詳細資訊，以及這兩個姿勢之間的差異，請參閱 [OpenXR 規格-輸入子路徑](https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#semantic-path-input)。</span><span class="sxs-lookup"><span data-stu-id="b54e9-220">More information on this design and the differences between the two poses can be found in the [OpenXR Specification - Input Subpaths](https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#semantic-path-input).</span></span>

<span data-ttu-id="b54e9-221">InputFeatureUsages **DevicePosition**、 **DeviceRotation**、 **DeviceVelocity** 和 **DeviceAngularVelocity** 提供 **的姿勢全都代表 OpenXR 的** 把手姿勢。</span><span class="sxs-lookup"><span data-stu-id="b54e9-221">Poses supplied by the InputFeatureUsages **DevicePosition**, **DeviceRotation**, **DeviceVelocity**, and **DeviceAngularVelocity** all represent the OpenXR **grip** pose.</span></span> <span data-ttu-id="b54e9-222">與框姿勢相關的 InputFeatureUsages 是在 Unity 的 [CommonUsages](https://docs.unity3d.com/2020.2/Documentation/ScriptReference/XR.CommonUsages.html)中定義。</span><span class="sxs-lookup"><span data-stu-id="b54e9-222">InputFeatureUsages related to grip poses are defined in Unity’s [CommonUsages](https://docs.unity3d.com/2020.2/Documentation/ScriptReference/XR.CommonUsages.html).</span></span>

<span data-ttu-id="b54e9-223">InputFeatureUsages **PointerPosition**、 **PointerRotation**、 **PointerVelocity** 和 **PointerAngularVelocity** 提供的姿勢全都代表 OpenXR 的 **目標** 。</span><span class="sxs-lookup"><span data-stu-id="b54e9-223">Poses supplied by the InputFeatureUsages **PointerPosition**, **PointerRotation**, **PointerVelocity**, and **PointerAngularVelocity** all represent the OpenXR **aim** pose.</span></span> <span data-ttu-id="b54e9-224">這些 InputFeatureUsages 不會定義在任何包含的 c # 檔案中，因此您必須定義您自己的 InputFeatureUsages，如下所示：</span><span class="sxs-lookup"><span data-stu-id="b54e9-224">These InputFeatureUsages aren't defined in any included C# files, so you'll need to define your own InputFeatureUsages as follows:</span></span>

``` cs
public static readonly InputFeatureUsage<Vector3> PointerPosition = new InputFeatureUsage<Vector3>("PointerPosition");
```

### <a name="haptics"></a><span data-ttu-id="b54e9-225">Haptics</span><span class="sxs-lookup"><span data-stu-id="b54e9-225">Haptics</span></span>

<span data-ttu-id="b54e9-226">如需在 Unity 的 XR 輸入系統中使用 haptics 的相關資訊，請參閱 unity [Manual For UNITY XR 輸入-haptics](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html#Haptics)中的檔。</span><span class="sxs-lookup"><span data-stu-id="b54e9-226">For information on using haptics in Unity’s XR Input system, documentation can be found at the [Unity Manual for Unity XR Input - Haptics](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html#Haptics).</span></span>

## <a name="whats-coming-soon"></a><span data-ttu-id="b54e9-227">即將推出的內容</span><span class="sxs-lookup"><span data-stu-id="b54e9-227">What's coming soon</span></span>

<span data-ttu-id="b54e9-228">下列問題和遺漏的功能都是已知的混合現實 OpenXR 外掛程式 **版本 0.1.0**。</span><span class="sxs-lookup"><span data-stu-id="b54e9-228">The following issues and missing features are known with Mixed Reality OpenXR plugin **version 0.1.0**.</span></span> <span data-ttu-id="b54e9-229">我們正在處理這些問題，並將在即將推出的版本中發行修正程式和新功能。</span><span class="sxs-lookup"><span data-stu-id="b54e9-229">We're working on these and will release fixes and new features in upcoming releases.</span></span>

* <span data-ttu-id="b54e9-230">尚不支援 **ARPlaneSubsystem** 。</span><span class="sxs-lookup"><span data-stu-id="b54e9-230">**ARPlaneSubsystem** is not supported yet.</span></span> <span data-ttu-id="b54e9-231">HoloLens 2 也不支援 **ARPlaneManager**、 **ARRaycastManager** 和相關的 API，例如 **ARAnchorManager. AttachAnchor** 。</span><span class="sxs-lookup"><span data-stu-id="b54e9-231">**ARPlaneManager**, **ARRaycastManager**, and related API like **ARAnchorManager.AttachAnchor** are also not supported on HoloLens 2.</span></span>
* <span data-ttu-id="b54e9-232">目前尚未支援錨點，但不久的未來將會推出 **錨點**。</span><span class="sxs-lookup"><span data-stu-id="b54e9-232">**Anchor** isn't supported by Holographic Remoting yet, but it's coming in the near future.</span></span>
* <span data-ttu-id="b54e9-233">目前尚不支援手上的 **網格** 追蹤、 **QR 代碼** 和 **XRMeshSubsystem** 。</span><span class="sxs-lookup"><span data-stu-id="b54e9-233">**Hand Mesh** tracking, **QR Codes**, and **XRMeshSubsystem** aren't supported yet.</span></span>
* <span data-ttu-id="b54e9-234">**Azure 空間錨點** 支援即將在未來版本中推出。</span><span class="sxs-lookup"><span data-stu-id="b54e9-234">**Azure Spatial Anchors** support is coming in a future release.</span></span>
* <span data-ttu-id="b54e9-235">**ARM64** 是 HoloLens 2 應用程式唯一支援的平臺。</span><span class="sxs-lookup"><span data-stu-id="b54e9-235">**ARM64** is the only supported platform for HoloLens 2 apps.</span></span> <span data-ttu-id="b54e9-236">**ARM** 平臺即將在未來版本中推出。</span><span class="sxs-lookup"><span data-stu-id="b54e9-236">The **ARM** platform is coming in a future release.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="b54e9-237">疑難排解</span><span class="sxs-lookup"><span data-stu-id="b54e9-237">Troubleshooting</span></span>

<span data-ttu-id="b54e9-238">當您在 HoloLens 2 上暫停和繼續 Unity 應用程式時，應用程式無法正確地繼續，這會導致 HoloLens 視圖中有4個旋轉點。</span><span class="sxs-lookup"><span data-stu-id="b54e9-238">When you suspend and resume a Unity app on HoloLens 2, the app can't correctly resume, which leads to 4 spinning dots in the HoloLens view.</span></span>

* <span data-ttu-id="b54e9-239">將 OpenXR 專案設定中的 **深度提交模式** 設定為 [ **無** ] 作為因應措施</span><span class="sxs-lookup"><span data-stu-id="b54e9-239">Set **Depth submission Mode** to **None** in the OpenXR project settings as a workaround</span></span>
