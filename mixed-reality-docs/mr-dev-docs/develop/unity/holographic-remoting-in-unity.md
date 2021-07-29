---
title: Unity 中的全像攝影遠端
description: 探索如何在傳統型應用程式和 Unity Play 模式中使用 OpenXR 來使用全像的遠端處理。
author: hferrone
ms.author: v-vtieto
ms.date: 07/26/2021
ms.topic: article
keywords: openxr、unity、hololens、hololens 2、mixed reality、MRTK、Mixed Reality 工具組、增強的現實、虛擬實境、混合現實耳機、學習、教學課程、快速入門、全像桌面
ms.openlocfilehash: 51244a94fb7e54f2eee41d9d1b7f65b0ba373138
ms.sourcegitcommit: 9831b89a1641ba1b5df14419ee2a4f29d3fa2d64
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/29/2021
ms.locfileid: "114757401"
---
# <a name="holographic-remoting-in-unity"></a>Unity 中的全像攝影遠端

> [!NOTE]
> Windows0.1.3 套件版本中新增了獨立的應用程式遠端支援。
> 從版本0.1.3，此功能不支援 UWP 組建。

[瞭解全像攝影的基本概念。](../platform-capabilities-and-apis/holographic-remoting-overview.md)

您可以使用內建的遠端功能，即時將全息內容串流至您的 HoloLens 2。 這是快速偵測應用程式，而不需要建立及部署完整專案的絕佳方式。 

開始之前，請務必瞭解 Unity 中的兩個主要選項：
* **Unity play 模式** 的全像遠端功能：在電腦上的 unity 編輯器中以播放模式執行您的應用程式，以提供快速的方式在 HoloLens 2 上預覽內容。 [播放] 模式也可以與連接至開發電腦的 Windows Mixed Reality 耳機一起使用。
* **從 unity 組建** 檔案進行全像遠端作業：從 unity 全像遠端遠端應用程式執行您的應用程式，該應用程式已從您匯出至桌面上的電腦到您的 HoloLens 2。 如果您的應用程式具有高解析度的資產或模型，這會很有説明。您的桌面 GPU 會在到達 HoloLens 2 之前處理轉譯。

## <a name="holographic-remoting-setup"></a>全像遠端設定

無論您使用的是「全像全像」的路由，您都必須從 HoloLens 2 上的 Microsoft Store 安裝「全像[遠端播放機」應用程式](https://www.microsoft.com/store/productId/9NBLGGH4SV40)。

下載之後，請在您的 HoloLens 2 上執行全像遠端播放程式應用程式，您會看到要連接的版本號碼和 IP 位址。 **您將需要2.4 版或更新版本，才能使用 OpenXR 外掛程式**。

![HoloLens 中執行的全像遠端播放播放程式螢幕擷取畫面](images/openxr-features-img-01.png)

## <a name="unity-play-mode-with-holographic-remoting"></a>使用全像攝影遠端的 Unity 播放模式

[!INCLUDE[](includes/unity-play-mode.md)]

全像遠端處理需要快速的電腦和 Wi-Fi 連接。 您可以在全像是「全像 [遠端播放機](../platform-capabilities-and-apis/holographic-remoting-player.md) 」檔中找到更多詳細資料。

為了獲得最佳結果，請確定您的應用程式已正確設定 [焦點點](focus-point-in-unity.md)。 這可協助全像攝影的遠端處理，將您的場景調整為無線連線的延遲。

## <a name="holographic-remoting-from-a-remote-application"></a>從遠端應用程式進行全像的遠端處理

1. 在功能表列上，選取 [**編輯] > Project 設定**。
1. 在左側資料行中，選取 **[XR 外掛程式管理]**。
1. 在 [ **XR 外掛程式管理]** 區段中，選取 [ **Microsoft HoloLens 功能群組** 和全像遠端 **遠端應用程式功能群組**]。
1. **在啟動時取消選取 INITIALIZE XR**：

    ![未核取 [啟動時，在 Unity 編輯器中開啟初始化 XR] 的 [專案設定] 面板螢幕擷取畫面](images/001-openxr-features.png)

1. 撰寫一些程式碼來設定遠端設定，並觸發 XR 初始化。 使用 [Mixed Reality OpenXR 外掛程式](./xr-project-setup.md#unity-sample-projects-for-openxr-and-hololens-2) 散發的範例應用程式包含 AppRemoting，其中顯示在執行時間連接到特定 IP 位址的範例案例。 此時將範例應用程式部署到本機電腦，將會顯示具有 [連接] 按鈕的 IP 位址輸入欄位。 輸入 IP 位址，然後按一下 [連線將會初始化 XR 並嘗試連線到目標裝置：

    ![顯示範例應用程式遠端 UI 範例應用程式的螢幕擷取畫面](images/openxr-sample-app-remoting.png)

1. 若要撰寫自訂的連接程式碼，請使用已填寫的進行呼叫 `Microsoft.MixedReality.OpenXR.Remoting.AppRemoting.Connect` `RemotingConfiguration` 。 範例應用程式會在偵測器中顯示這項功能，並示範如何從文字欄位填入 IP 位址。 呼叫 `Connect` 會設定並自動初始化 XR，這也是為什麼必須以協同程式的方式來呼叫它：

    ``` cs
    StartCoroutine(Remoting.AppRemoting.Connect(remotingConfiguration));
    ```

1. 執行時，您可以使用 API 取得目前的線上狀態 `AppRemoting.TryGetConnectionState` ，並選擇性地使用中斷連接和解除初始化 XR `AppRemoting.Disconnect()` 。 這可用來中斷連線，然後重新連線到相同應用程式會話內的不同裝置。 範例應用程式會提供 tappable cube，以在點擊時中斷遠端會話的連接。

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

## <a name="see-also"></a>另請參閱

* [全像攝影遠端播放程式](../platform-capabilities-and-apis/holographic-remoting-player.md)
* [教學課程：開始使用 PC 全像遠端](../unity/tutorials/mr-learning-pc-holographic-remoting-01.md)
* [教學課程：建立全像遠端電腦應用程式](../unity/tutorials/mr-learning-pc-holographic-remoting-02.md)
