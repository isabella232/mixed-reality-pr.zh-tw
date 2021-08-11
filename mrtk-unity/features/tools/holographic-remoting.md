---
title: 全像攝影遠端處理
description: 檔全像全像遠端 MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: a0d8e695e23ed2b58a62511e8b061bede2c68d92fb0089c8dada1d336c2a09e5
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2021
ms.locfileid: "115224806"
---
# <a name="holographic-remoting"></a>全像攝影遠端處理

全像是，使用 Wi-Fi 或 USB 纜線連線，全像是即時的遠端處理將電腦上的全息內容串流處理到您的 Microsoft HoloLens。 當開發混合現實應用程式時，這項功能可以大幅提升開發人員的生產力。

XR SDK （如下所述）是 unity [2019.3 及更高的 unity 新 XR 管線](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/)。 如需搭配使用 XR SDK 與 MRTK 的詳細資訊，請參閱 [這裡](../../configuration/getting-started-with-mrtk-and-xrsdk.md) 。 舊版 XR 是指 unity 2018 中包含的現有 XR 管線，在 Unity 2019.3 中已被取代，並已在 Unity 2020 中移除。

## <a name="initial-setup"></a>初始設定

若要啟用 HoloLens 的遠端功能，請務必確定專案使用的是最新的遠端處理元件。

1. 開啟 **視窗 > 封裝管理員**
    - 如果使用舊版 XR：確認已安裝最新版的 **Windows Mixed Reality** 套件。
    - 如果使用 XR SDK：請確認已安裝最新版的 **Windows XR 外掛程式** 套件。
1. 透過 Microsoft Store，確定已在 HoloLens 上安裝最新的全像全像遠端處理應用程式。

請根據專案中使用的管線，繼續閱讀 [舊版 XR 安裝指示](#legacy-xr-setup-instructions) 或 [XR SDK 設定指示](#xr-sdk-setup-instructions) 。

## <a name="legacy-xr-setup-instructions"></a>舊版 XR 安裝指示

下列指示僅適用于使用 HoloLens 2 的遠端處理。 如果您只使用 HoloLens (第1代) 執行遠端處理，請跳至[使用 wi-fi 連接到 HoloLens](#connecting-to-the-hololens-with-wi-fi)。

使用 HoloLens 2 時，已將對遠端的已表達和眼睛追蹤資料的支援新增至 MRTK。 若要啟用這些功能，請遵循將 DotNetWinRT 匯 [入到專案](#import-dotnetwinrt-into-the-project)中所述的步驟。

匯入之後，下一步是選取 **混合現實**  >  **工具** 組  >  **公用程式**  >  **Windows Mixed Reality**  >  **檢查** 設定。 此步驟會新增可啟用 DotNetWinRT 相依性的腳本定義。

> [!NOTE]
> 使用 Unity 2019.4 和更新版本時，不需要執行檢查設定公用程式。

若要追蹤手接程式和眼睛追蹤，請依照 **HoloLens 2 透過 Unity 套件匯入** 和相關章節進行的偵錯工具中的步驟進行。

### <a name="debugging-hololens-2-remoting-via-unity-package-import"></a>透過 Unity 套件匯入進行 HoloLens 2 遠端處理的調試

如果 HoloLens 2 的手接點和眼睛追蹤未在遠端處理，則有幾個常見的潛在問題點。 它們會依應檢查的順序列于下方。

這些問題在 **Unity 2019.3** 或更新版本上執行時特別相關。

#### <a name="import-dotnetwinrt-into-the-project"></a>將 DotNetWinRT 匯入專案

1. 下載 [Mixed Reality 功能工具](https://aka.ms/MRFeatureTool)

1. 在 [**探索功能**] 視圖中，選取 [*混合的事實 WinRT 投影*]

    ![選取 DotNetWinRT 套件](../images/tools/remoting/SelectDotNetWinRT.png)

1. 按一下 [ **取得功能** ]，然後繼續匯 [入封裝](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool#3-importing-feature-packages)。

#### <a name="dotnetwinrt_present-define-written-into-player-settings"></a>DOTNETWINRT_PRESENT 定義寫入播放機設定

> [!NOTE]
> 使用 Unity 2019.4 和更新版本時，DOTNETWINRT_PRESENT 定義會包含在適當的 asmdef 檔案中，而不是 Unity Player 設定。 不需要檢查設定步驟。

從 MRTK 版本2.5.0 開始，基於效能的考慮，不再自動設定此 #define。 若要啟用此旗標，請使用 **Mixed Reality** 工具組  >  **公用程式**  >  **Windows Mixed Reality**  >  **檢查** 設定功能表項目。

> [!Note]
> 檢查設定專案不會顯示確認。 若要確認已設定定義，請流覽至 Unity Player 設定。 從該處的 [UWP] 索引標籤下，檢查腳本定義符號的 [其他設定] 下的。 請確定已在該清單中正確寫入 DOTNETWINRT_PRESENT。 如果有的話，這個步驟就成功了。

![DotNetWinRT 存在](../images/tools/remoting/DotNetWinRTPresent.png)

### <a name="removing-hololens-2-specific-remoting-support"></a>移除 HoloLens 2 特定的遠端支援

如果您因為 DotNetWinRT 介面卡的存在而遇到衝突或其他問題，請前往 [我們的其中一個說明資源](../../index.md#getting-help)。

## <a name="xr-sdk-setup-instructions"></a>XR SDK 安裝指示

遵循[[開始使用 MRTK 和 XR SDK] 頁面上的 Windows Mixed Reality 設定指示](../../configuration/getting-started-with-mrtk-and-xrsdk.md#windows-mixed-reality)，並務必執行編輯器 HoloLens 遠端處理所需的步驟。

## <a name="connecting-to-the-hololens-with-wi-fi"></a>使用 Wi-Fi 連接到 HoloLens

設定好專案之後，就可以建立 HoloLens 的連接。

1. 在 [檔案 **> 組建設定** 中，確定專案組建類型設定為 [**通用 Windows 平臺**
1. 在 HoloLens 上，啟動全像的 **遠端處理** 應用程式。
1. 在 Unity 中，如果使用 XR SDK Windows，請選取 [ **Window > XR] > [全像 XR] () / (XR 外掛程式遠端)**。

    ![開始全像模擬](../images/tools/remoting/StartHolographicEmulation.png)

1. 將 **模擬模式** 設定為 [ **遠端裝置**]。

    ![設定模擬模式](../images/tools/remoting/SelectEmulationMode.png)

1.  (**_僅適用于舊版 XR_**) 選取 **裝置版本**。

    ![選取裝置版本](../images/tools/remoting/SelectDeviceVersion.png)

1. 使用「全像遠端播放播放程式」應用程式所顯示的 IP 位址，設定 [ **遠端電腦** ] 欄位。

    ![輸入 IP 位址](../images/tools/remoting/EnterIPAddress.png)

1. 按一下 [連線]。

> [!NOTE]
> 如果您無法連線，請確定您的 HoloLens 2 未插入電腦並重新啟動 Unity。

## <a name="connecting-to-the-hololens-with-usb-cable"></a>使用 USB 纜線連接到 HoloLens

USB 纜線連接可提供更佳的轉譯品質和穩定性。 若要使用 USB 纜線連線，請在 HoloLens 的設定中中斷與 Wi-Fi HoloLens 的連線，並啟動全像遠端播放機應用程式。 它會顯示開頭為169的 IP 位址。 在 Unity 的全像模擬設定中使用此 IP 位址來連接。 一旦識別出 USB 纜線的 IP 位址之後，就可以安全地將 HoloLens 連接到 Wi-Fi。

## <a name="starting-a-remoting-session"></a>啟動遠端會話

當 Unity 連接到 HoloLens，請在編輯器中輸入播放模式。

當會話完成時，結束播放模式。

> [!NOTE]
> 有一些 Unity 版本的已知問題，在遠端會話期間，編輯器可能會在進入播放模式時停止回應。 如果在載入專案時，全像全像是開啟的全像是，就會發生此問題。 若要確保不會發生此問題，請一律在離開 Unity 之前關閉全像的對話方塊。

## <a name="see-also"></a>另請參閱

- [全像遠端的疑難排解和限制](/windows/mixed-reality/holographic-remoting-troubleshooting)
- [Microsoft 全像遠端軟體授權條款](/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
