---
title: Unity 中的 OpenXR 外掛程式支援功能
description: 探索 OpenXR 針對 Unity 中的混合現實開發所支援的功能。
author: hferrone
ms.author: alexturn
ms.date: 01/11/2021
ms.topic: article
keywords: openxr、unity、hololens、hololens 2、mixed reality、MRTK、Mixed Reality 工具組、增強的現實、虛擬實境、混合現實耳機、學習、教學課程、快速入門
ms.openlocfilehash: 0501abe5a417c17283347455ccea8ec6f49a6a45
ms.sourcegitcommit: 4647712788a91a2b26d4b01e62285c2942bb0bd2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102230739"
---
# <a name="mixed-reality-openxr-supported-features-in-unity"></a>混合現實 OpenXR Unity 中支援的功能

**Mixed Reality OpenXR 外掛程式** 套件是 Unity **OpenXR 外掛程式** 的延伸模組，並支援 HoloLens 2 和 Windows Mixed Reality 耳機的功能套件。 繼續之前，請確定您已安裝 **unity 2020.2** 或更新版本、 **OpenXR 外掛程式版本 0.1.3** 或更新版本，且您的 Unity 專案已 [設定 OpenXR](openxr-getting-started.md)。

## <a name="whats-supported"></a>支援的項目

目前支援下列功能：

* 支援 HoloLens 2 的 UWP 應用程式，並針對 HoloLens 2 應用程式模型進行優化。
* 支援 Win32 VR 應用程式，適用于具有最新控制器設定檔的 Windows Mixed Reality 耳機以及全像應用程式遠端處理。
* 使用錨點和未系結空間的世界規模追蹤。
* [錨點儲存體 API，以將錨點保存](#anchors-and-anchor-persistence) 到 HoloLens 2 本機儲存體。
* [移動控制器和手互動](#motion-controller-and-hand-interactions)，包括新的 HP 回音卡控制器。
* 使用26個接點和聯合半徑輸入，以明確表述的手勢進行追蹤。
* HoloLens 2 上的眼睛互動。
* 在 HoloLens 2 上尋找相片/影片 (PV) 攝影機。
* 混合現實捕捉使用透過 PV 攝影機的第三種視覺呈現。
* 支援「 [Play」至 HoloLens 2 （含全像遠端應用程式](#holographic-remoting-in-unity-editor-play-mode)），讓開發人員不需要建立及部署到裝置，即可將腳本進行偵錯工具。
* 透過 [MRTK OpenXR 提供者支援](openxr-getting-started.md#using-mrtk-with-openxr-support)，與 MRTK Unity 2.5.3 和更新版本相容。
* 與 Unity [ARFoundation 4.0](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html) 或更新版本相容。
*  (在 0.1.3) 中新增的功能，可支援從組建和部署的 Windows 獨立應用程式進行傳統型 [應用程式](#holographic-remoting-in-desktop-app) 全像開發。
*  (在0.1.4 中新增) 透過 SpatialGraphNode 支援 HoloLens2 上的[QR 代碼追蹤](#qr-codes)

## <a name="holographic-remoting-setup"></a>全像遠端設定

1. 首先，您必須從 HoloLens 2 上的 Microsoft Store 安裝全像[遠端播放機應用程式](https://www.microsoft.com/store/productId/9NBLGGH4SV40)
2. 在 HoloLens 2 上執行全像遠端播放播放程式應用程式，您會看到要連接的版本號碼和 IP 位址
    * 您將需要2.4 或更新版本才能使用 OpenXR 外掛程式

    ![HoloLens 中執行的全像 Remoting 播放程式的螢幕擷取畫面](images/openxr-features-img-01.png)

## <a name="holographic-remoting-in-unity-editor-play-mode"></a>Unity 編輯器 play 模式的全像遠端功能

在 Visual Studio 專案中建立 UWP Unity 專案，然後將它封裝並部署到 HoloLens 2 裝置，可能需要一些時間。 其中一個解決方法是啟用全像「全像」編輯器遠端功能，讓您可以使用「播放」模式，將 c # 腳本直接透過您的網路上的 HoloLens 2 裝置來進行。 此案例可避免建立 UWP 套件並將其部署至遠端裝置的額外負荷。

1. 遵循全像全像[遠端設定](#holographic-remoting-setup)的步驟
2. 開啟 [ **編輯-> 專案設定**]，流覽至 **XR 外掛程式管理**，然後選取 [ **Windows Mixed Reality 功能集** ] 方塊：

    ![醒目提示 XR 外掛程式管理的 Unity 編輯器中開啟之 [專案設定] 面板的螢幕擷取畫面](images/openxr-features-img-02.png)

3. 展開 [ **OpenXR** ] 底下的 [**功能**] 區段，然後選取 [**全部顯示**]
4. 核取 [全像攝影 **編輯器遠端處理** ] 核取方塊，然後輸入您從「全像」遠端應用程式取得的 IP 位址

    ![在 Unity 編輯器中開啟專案設定面板的螢幕擷取畫面，其中已醒目提示功能](images/openxr-features-img-03.png)

現在您可以按一下 [播放] 按鈕，以在 HoloLens 上的全像遠端應用程式中播放 Unity 應用程式。 您也可以 [將 Visual Studio 附加至 Unity](/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows) ，以在播放模式中進行 c # 腳本的調試。

> [!NOTE]
> 從0.1.0 版起，全像「全像」遠端執行時間不支援錨點，而 ARAnchorManager 功能將無法透過遠端處理。  這項功能會在未來的版本中推出。

## <a name="holographic-remoting-in-desktop-app"></a>傳統型應用程式中的全像全像遠端

> [!NOTE]
> 0.1.3 套件版本已新增 Windows 獨立應用程式遠端支援。
> 從版本0.1.3，此功能不支援 UWP 組建。

1. 遵循全像全像[遠端設定](#holographic-remoting-setup)的步驟
2. 開啟 [ **編輯-> 專案設定**]，流覽至 **XR 外掛程式管理**，然後選取 [ **Windows Mixed Reality 功能集** ] 方塊。 此外，取消核取 [ **啟動時初始化 XR**]：

    ![未核取 [啟動時，在 Unity 編輯器中開啟初始化 XR] 的 [專案設定] 面板螢幕擷取畫面](images/openxr-features-img-02-app.png)

3. 展開 [ **OpenXR** ] 底下的 [**功能**] 區段，然後選取 [**全部顯示**]
4. 核取全像 **應用程式遠端處理** 的核取方塊：

    ![在 Unity 編輯器中開啟的 [專案設定] 面板的螢幕擷取畫面，其中已啟用應用程式遠端功能](images/openxr-features-img-03-app.png)

5. 接下來，撰寫一些程式碼來設定遠端設定，並觸發 XR 初始化。 使用 [Mixed Reality OpenXR 外掛程式](openxr-getting-started.md#hololens-2-samples) 散發的範例應用程式包含 AppRemoting.cs，其中顯示在執行時間連接到特定 IP 位址的範例案例。 此時將範例應用程式部署到本機電腦，將會顯示具有 [連接] 按鈕的 IP 位址輸入欄位。 輸入 IP 位址，然後按一下 [連線]，將會初始化 XR 並嘗試連線到目標裝置：

    ![顯示範例應用程式遠端 UI 範例應用程式的螢幕擷取畫面](images/openxr-sample-app-remoting.png)

6. 若要撰寫自訂的連接程式碼，請使用已填寫的進行呼叫 `Microsoft.MixedReality.OpenXR.Remoting.AppRemoting.Connect` `RemotingConfiguration` 。 範例應用程式會在偵測器中顯示這項功能，並示範如何從文字欄位填入 IP 位址。 呼叫 `Connect` 會設定並自動初始化 XR，這也是為什麼必須以協同程式的方式來呼叫它：

    ``` cs
    StartCoroutine(Remoting.AppRemoting.Connect(remotingConfiguration));
    ```

7. 執行時，您可以使用 API 取得目前的線上狀態 `AppRemoting.TryGetConnectionState` ，並選擇性地使用中斷連接和解除初始化 XR `AppRemoting.Disconnect()` 。 這可用來中斷連線，然後重新連線到相同應用程式會話內的不同裝置。 範例應用程式會提供 tappable cube，以在點擊時中斷遠端會話的連接。

### <a name="migration-from-previous-apis"></a>從先前的 Api 遷移

#### <a name="unityenginexrwsaholographicremoting"></a>UnityEngine. XR HolographicRemoting

從 [Unity](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/XR.WSA.HolographicRemoting.html)檔的範例程式碼：

| XR.Wsa。HolographicRemoting | OpenXR. AppRemoting |
| ---- | ---- |
| `HolographicRemoting.Connect(String)` | `AppRemoting.Connect(RemotingConfiguration)` |
| `HolographicRemoting.ConnectionState` | `AppRemoting.TryGetConnectionState(out ConnectionState, out DisconnectReason)`|
| `StartCoroutine(LoadDevice("WindowsMR"))`| [N/A：呼叫時自動發生 `AppRemoting.Connect`  |

#### <a name="unityenginexrwindowsmrwindowsmrremoting"></a>UnityEngine. XR. WindowsMR. WindowsMRRemoting

| XR.WindowsMR.WindowsMRRemoting | OpenXR. AppRemoting |
| ---- | ---- |
| `WindowsMRRemoting.Connect()` | `AppRemoting.Connect(RemotingConfiguration)` |
| `WindowsMRRemoting.Disconnect()` | `AppRemoting.Disconnect()` |
| `WindowsMRRemoting.TryGetConnectionState(out ConnectionState)` 和 `WindowsMRRemoting.TryGetConnectionFailureReason(out ConnectionFailureReason)`| `AppRemoting.TryGetConnectionState(out ConnectionState, out DisconnectReason)`|
| `WindowsMRRemoting.isAudioEnabled`, `WindowsMRRemoting.maxBitRateKbps`, `WindowsMRRemoting.remoteMachineName` | `AppRemoting.Connect`經由結構傳遞至 `RemotingConfiguration` |
| `WindowsMRRemoting.isConnected` | `AppRemoting.TryGetConnectionState(out ConnectionState state, out _) && state == ConnectionState.Connected`

## <a name="anchors-and-anchor-persistence"></a>錨點和錨點持續性

Mixed Reality OpenXR 外掛程式透過 Unity 的 ARFoundation **ARAnchorManager** 的執行，提供基本錨定功能。 若要瞭解 ARFoundation 中 **ARAnchor** 的基本概念，請造訪 [AR 錨點管理員的 ARFoundation 手冊](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/anchor-manager.html)。 從版本0.1.0，此外掛程式除了建立附加至平面的錨點（即將在未來版本中）之外，也支援所有 ARAnchorManager 功能。

### <a name="anchor-persistence-and-the-xranchorstore"></a>錨點持續性和 XRAnchorStore

另一個稱為 **XRAnchorStore** 的 API 可讓錨點在會話之間保存。 XRAnchorStore 是您裝置上已儲存錨點的標記法。 錨點可以從 Unity 場景中的 **ARAnchors** 保存、從儲存體載入至新的 **ARAnchors**，或從儲存體中刪除。

> [!NOTE]
> 這些錨點會儲存並載入至相同的裝置。 未來版本中的 Azure 空間錨點將會支援跨裝置錨定儲存體。

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

為了載入 XRAnchorStore，外掛程式會在 XRAnchorSubsystem （ARAnchorManager 的子系統）上提供擴充方法：

``` cs
public static Task<XRAnchorStore> LoadAnchorStoreAsync(this XRAnchorSubsystem anchorSubsystem)
```

若要使用此擴充方法，請從 ARAnchorManager 的子系統進行存取，如下所示：

``` cs
ARAnchorManager arAnchorManager = GetComponent<ARAnchorManager>();
XRAnchorStore anchorStore = await arAnchorManager.subsystem.LoadAnchorStoreAsync();
```

若要查看保存/unpersisting 錨點的完整範例，請查看 [混合現實 OpenXR 外掛程式範例場景](openxr-getting-started.md#hololens-2-samples)中的錨點 > 錨點範例 GameObject 和 AnchorsSample.cs 腳本：

![在 Unity 編輯器中開啟之 [階層] 面板的螢幕擷取畫面，其中已醒目提示錨點範例](images/openxr-features-img-04.png)

![在 Unity 編輯器中開啟的 [偵測器] 面板的螢幕擷取畫面，其中已醒目提示錨點範例腳本](images/openxr-features-img-05.png)

## <a name="motion-controller-and-hand-interactions"></a>移動控制器和手互動

若要瞭解 Unity 中混合現實互動的基本概念，請流覽 unity [Manual For UNITY XR 輸入](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html)。 這項 Unity 檔涵蓋從控制器專屬輸入到更一般化 **InputFeatureUsage** 的對應、如何識別和分類可用的 XR 輸入、如何從這些輸入讀取資料等等。

Mixed Reality OpenXR 外掛程式提供額外的輸入互動設定檔，對應至標準 **InputFeatureUsage** s，如下所述：

| InputFeatureUsage | HP 回音 (OpenXR)  | HoloLens (OpenXR)  |
| ---- | ---- | ---- |
| primary2DAxis | 操縱 杆 | |
| primary2DAxisClick | 搖桿-按一下 | |
| 觸發程序 (trigger) | 觸發程序  | |
| 握 | 握 | 點擊或擠壓 |
| primaryButton | [X/A]-按下 | 空中點選 |
| secondaryButton | [Y/B]-按下 | |
| gripButton | 握住-按 | |
| triggerButton | 觸發程式-按下 | |
| menuButton | 功能表 | |

### <a name="aim-and-grip-poses"></a>目標和底姿勢

您可以透過 OpenXR 輸入互動存取兩組姿勢：

* 抓手中呈現物件的底框
* 目標是指向世界。

有關此設計的詳細資訊，以及這兩個姿勢之間的差異，請參閱 [OpenXR 規格-輸入子路徑](https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#semantic-path-input)。

InputFeatureUsages **DevicePosition**、 **DeviceRotation**、 **DeviceVelocity** 和 **DeviceAngularVelocity** 提供 **的姿勢全都代表 OpenXR 的** 把手姿勢。 與框姿勢相關的 InputFeatureUsages 是在 Unity 的 [CommonUsages](https://docs.unity3d.com/2020.2/Documentation/ScriptReference/XR.CommonUsages.html)中定義。

InputFeatureUsages **PointerPosition**、 **PointerRotation**、 **PointerVelocity** 和 **PointerAngularVelocity** 提供的姿勢全都代表 OpenXR 的 **目標** 。 這些 InputFeatureUsages 不會定義在任何包含的 c # 檔案中，因此您必須定義您自己的 InputFeatureUsages，如下所示：

``` cs
public static readonly InputFeatureUsage<Vector3> PointerPosition = new InputFeatureUsage<Vector3>("PointerPosition");
```

### <a name="haptics"></a>Haptics

如需在 Unity 的 XR 輸入系統中使用 haptics 的相關資訊，請參閱 unity [Manual For UNITY XR 輸入-haptics](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html#Haptics)中的檔。

## <a name="qr-codes"></a>QR 代碼

HoloLens 2 可以偵測頭戴式裝置周圍環境中的 QR 代碼，而在每個代碼的真實世界位置建立座標系統。 您可以在我們的 [QR 代碼追蹤](../platform-capabilities-and-apis/qr-code-tracking.md) 檔中找到更多詳細資料。  使用 OpenXR 外掛程式時，請[ `SpatialGraphNodeId` 從 QR API](../platform-capabilities-and-apis/qr-code-tracking.md#qr-api-reference)抓取，並使用 `Microsoft.MixedReality.OpenXR.SpatialGraphNode` API 來尋找 qr 代碼。

如需參考，我們[在 GitHub 上有 QR 追蹤範例專案](https://github.com/yl-msft/QRTracking)，並有更詳細的[ `SpatialGraphNode` API](https://github.com/yl-msft/QRTracking/blob/main/SampleQRCodes/Assets/Scripts/SpatialGraphNodeTracker.cs)使用說明。

## <a name="whats-coming-soon"></a>即將推出的內容

下列問題和遺漏的功能都是已知的混合現實 OpenXR 外掛程式 **版本 0.1.0**。 我們正在處理這些問題，並將在即將推出的版本中發行修正程式和新功能。

* 尚不支援 **ARPlaneSubsystem** 。 HoloLens 2 也不支援 **ARPlaneManager**、 **ARRaycastManager** 和相關的 API，例如 **ARAnchorManager. AttachAnchor** 。
* 目前的「全像」遠端功能不支援 **錨定持續** 性，但不久的未來將會推出。
* 目前尚不支援 **手形** 追蹤和 **XRMeshSubsystem** 。
* **Azure 空間錨點** 支援即將在未來版本中推出。
* **ARM64** 是 HoloLens 2 應用程式唯一支援的平臺。 **ARM** 平臺即將在未來版本中推出。

## <a name="troubleshooting"></a>疑難排解

當您在 HoloLens 2 上暫停和繼續 Unity 應用程式時，應用程式無法正確地繼續，這會導致 HoloLens 視圖中有4個旋轉點。

* 將 OpenXR 專案設定中的 **深度提交模式** 設定為 [ **無** ] 作為因應措施
