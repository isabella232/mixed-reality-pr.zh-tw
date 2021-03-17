---
title: 傳統型應用程式中的全像全像遠端
description: 探索如何在傳統型應用程式中使用 OpenXR 的全像是全像的遠端處理。
author: hferrone
ms.author: alexturn
ms.date: 03/16/2021
ms.topic: article
keywords: openxr、unity、hololens、hololens 2、mixed reality、MRTK、Mixed Reality 工具組、增強的現實、虛擬實境、混合現實耳機、學習、教學課程、快速入門、全像桌面
ms.openlocfilehash: f3cf43d59b74b0f47e701acc1d7312544867b0df
ms.sourcegitcommit: d5e4eb94c87b86a7774a639f11cd9e35a7050107
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2021
ms.locfileid: "103624315"
---
# <a name="holographic-remoting-in-desktop-app"></a>傳統型應用程式中的全像全像遠端

> [!NOTE]
> 0.1.3 套件版本已新增 Windows 獨立應用程式遠端支援。
> 從版本0.1.3，此功能不支援 UWP 組建。

1. 遵循全像全像[遠端設定](openxr-supported-features.md#holographic-remoting-setup)的步驟
2. 開啟 [ **編輯-> 專案設定**]，流覽至 **XR 外掛程式管理**，然後選取 [ **Windows Mixed Reality 功能集** ] 方塊。 此外，取消核取 [ **啟動時初始化 XR**]：

    ![未核取 [啟動時，在 Unity 編輯器中開啟初始化 XR] 的 [專案設定] 面板螢幕擷取畫面](images/openxr-features-img-02-app.png)

3. 展開 [ **OpenXR** ] 底下的 [**功能**] 區段，然後選取 [**全部顯示**]
4. 核取全像 **應用程式遠端處理** 的核取方塊：

    ![在 Unity 編輯器中開啟的 [專案設定] 面板的螢幕擷取畫面，其中已啟用應用程式遠端功能](images/openxr-features-img-03-app.png)

5. 接下來，撰寫一些程式碼來設定遠端設定，並觸發 XR 初始化。 使用 [Mixed Reality OpenXR 外掛程式](openxr-getting-started.md#hololens-2-samples) 散發的範例應用程式包含 AppRemoting，其中顯示在執行時間連接到特定 IP 位址的範例案例。 此時將範例應用程式部署到本機電腦，將會顯示具有 [連接] 按鈕的 IP 位址輸入欄位。 輸入 IP 位址，然後按一下 [連線]，將會初始化 XR 並嘗試連線到目標裝置：

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