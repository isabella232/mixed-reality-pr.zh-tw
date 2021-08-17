---
title: 使用電腦資源透過全像遠端功能來增強您的應用程式
description: 使用電腦資源，而不是依賴 HoloLens 的內部處理能力，以透過全像的遠端處理來為您的應用程式提供強大的功能
author: vtieto
ms.author: v-vtieto
ms.date: 08/12/2021
ms.topic: article
keywords: openxr、unity、hololens、hololens 2、mixed reality、MRTK、Mixed Reality 工具組、增強的現實、虛擬實境、混合現實耳機、學習、教學課程、快速入門、攝影遠端、桌面、預覽、debug
ms.openlocfilehash: 634e1a5e92ade79d1d9f0e7bfdd994cfdfb5866b
ms.sourcegitcommit: 820f2dfe98065298f6978a651f838de12620dd45
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/14/2021
ms.locfileid: "122203839"
---
# <a name="use-pc-resources-to-power-your-app-with-holographic-remoting"></a>使用電腦資源透過全像遠端功能來增強您的應用程式

本文說明適用于全像攝影的下列使用案例：

-  **您希望電腦的資源能夠為您的應用程式提供強大的功能，而不是依賴 HoloLens 的內部資源**：您可以建立並建立具有全像的遠端功能的應用程式。 使用者會在 HoloLens 上體驗應用程式，但應用程式實際上是在電腦上執行，這可讓應用程式利用電腦功能更強大的資源。 如果您的應用程式具有高解析度的資產或模型，而且您不希望畫面播放速率受到影響，這會特別有用。 我們稱之為全像遠端 _遠端應用程式_。 來自 HoloLens 的輸入（注視、手勢、語音和空間對應）會傳送至電腦，其中內容會以虛擬沉浸式視圖呈現。 然後，轉譯的框架會傳送至 HoloLens。

這種類型的全像是 Windows Mixed Reality (WMR) 沉浸式耳機。 比方說，如果您的 WMR 耳機連接到背包」 PC，而您想要將應用程式從功能更強大的電腦串流到背包」 PC，這可能會很有用。

若要深入瞭解全像攝影的[遠端處理功能，請參閱全](../platform-capabilities-and-apis/holographic-remoting-overview.md)像

請注意，如果 [您想要在開發過程中預覽和偵測應用程式](preview-and-debug-your-app.md)，也可以使用全像的遠端處理。

## <a name="set-up-holographic-remoting"></a>設定全像遠端

若要使用全像的遠端功能，您必須從 HoloLens 2 上的 Microsoft Store 安裝全像[遠端播放機](../platform-capabilities-and-apis/holographic-remoting-player.md)應用程式。 如下所述，下載並執行應用程式之後，您會看到要連接的版本號碼和 IP 位址。 **您將需要2.4 版或更新版本，才能使用 OpenXR 外掛程式**。

全像遠端處理需要快速的電腦和 Wi-Fi 連接。 您可以在上面所連結的全像「全像遠端播放播放」文章中找到詳細資料。

![HoloLens 中執行的全像遠端播放播放程式螢幕擷取畫面](images/openxr-features-img-01.png)

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

## <a name="migrate-from-previous-holographic-remoting-apis"></a>從舊版的全像 Remoting Api 遷移

若要深入瞭解全像攝影的[遠端處理功能，請參閱全](../platform-capabilities-and-apis/holographic-remoting-overview.md)像

#### <a name="unityenginexrwsaholographicremoting"></a>UnityEngine. XR HolographicRemoting

從 [Unity](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/XR.WSA.HolographicRemoting.html)檔的範例程式碼：

| XR.WSA。HolographicRemoting | OpenXR. AppRemoting |
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
* [使用全像全像「遠端處理」和「播放」模式來預覽及偵測應用](preview-and-debug-your-app.md)
* [教學課程：開始使用 PC 全像遠端](../unity/tutorials/mr-learning-pc-holographic-remoting-01.md)
* [教學課程：建立全像遠端電腦應用程式](../unity/tutorials/mr-learning-pc-holographic-remoting-02.md)
