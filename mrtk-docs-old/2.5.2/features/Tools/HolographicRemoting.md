---
title: HolographicRemoting
description: 檔全像全像遠端 MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: f7f3ab014405ba3f2e658e04d1ee2b4f62400907
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/03/2021
ms.locfileid: "101780378"
---
# <a name="holographic-remoting"></a>全像攝影遠端處理

全像是使用 Wi-Fi 或 USB 纜線連線，將電腦上的全像攝影內容從電腦即時串流處理至 Microsoft HoloLens。 當開發混合現實應用程式時，這項功能可以大幅提升開發人員的生產力。

XR SDK （如下所述）是 unity [2019.3 及更高的 unity 新 XR 管線](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/)。 如需搭配使用 XR SDK 與 MRTK 的詳細資訊，請參閱 [這裡](../../configuration/GettingStartedWithMRTKAndXRSDK.md) 。 舊版 XR 是指 unity 2018 中包含的現有 XR 管線，在 Unity 2019.3 中已被取代，並已在 Unity 2020 中移除。

## <a name="initial-setup"></a>初始設定

若要啟用 HoloLens 的遠端功能，請務必確定專案使用的是最新的遠端處理元件。

1. 開啟 **視窗 > 套件管理員**
    - 如果使用舊版 XR：確認已安裝最新版的 **Windows Mixed Reality** 套件。
    - 如果使用 XR SDK：請確認已安裝最新版的 **WINDOWS XR 外掛程式** 套件。
1. 確定已在 HoloLens 上透過 Microsoft Store 安裝最新的全像全像遠端應用程式。

請根據專案中使用的管線，繼續閱讀 [舊版 XR 安裝指示](#legacy-xr-setup-instructions) 或 [XR SDK 設定指示](#xr-sdk-setup-instructions) 。

## <a name="legacy-xr-setup-instructions"></a>舊版 XR 安裝指示

下列指示僅適用于搭配 HoloLens 2 的遠端處理。 如果您只使用 HoloLens (第1代) 進行遠端處理，請跳至 [使用 wi-fi 連線到 hololens](#connecting-to-the-hololens-with-wi-fi)。

使用 HoloLens 2 時，已將對遠端處理明確和眼睛追蹤資料的支援新增至 MRTK。 若要啟用這些功能，請選取 **混合的現實工具** 組  >  **msbuild**  >  **將 msbuild 用於 Unity** 相依性解析。 這將會為全像全像進行安裝時安裝必要的相依性。

當 MSBuild 完成匯入程式之後，下一個步驟是選取 **混合現實工具** 組  >  **公用程式**  >  **Windows mixed Reality**  >  **檢查** 設定。 此步驟會新增腳本定義，以啟用 MSBuild for Unity 所安裝的 DotNetWinRT 相依性。

某些版本的 Unity 2019 在使用適用于 Unity 的 MSBuild 時遇到問題。 如果 [ **使用 MSBuild For Unity** 相依性解析] 選項失敗，請使用下列步驟來啟用全像的遠端處理。

1. 將檔案 **> 組建** 設定中的目標平臺設定為 **通用 Windows 平臺**
1. 如果未自動顯示，請 (**混合現實工具組 > 公用程式 > 設定 Unity 專案** 來執行 MRTK 設定程式公用程式) 
1. 按一下 [套用]  。
1. 開啟 **視窗 > 套件管理員**
    - 確定未安裝 **WINDOWS XR 外掛程式**
1. **> Player 開啟 [編輯 > 專案設定**

    ![Windows Mixed Reality SDK](../images/tools/remoting/WindowsMixedRealitySDK.png)

1. 確定已選取 [ **支援虛擬實境** ]，並將 **Windows Mixed Reality** 新增至 **虛擬實境 sdk**

若要啟用手動接點和眼睛追蹤的追蹤，請依照「透過 Unity 套件匯入和相關章節的 **偵錯工具 HoloLens 2 遠端處理** 」中的步驟進行。

### <a name="debugging-hololens-2-remoting-via-unity-package-import"></a>透過 Unity 套件匯入進行 HoloLens 2 遠端處理的調試

如果 HoloLens 2 的手接點和眼睛追蹤無法透過遠端處理，則有幾個常見的潛在問題點。 它們會依應檢查的順序列于下方。

這些問題在 **Unity 2019.3** 或更新版本上執行時特別相關。

#### <a name="msbuildforunity-package-import-via-writing-into-the-packagemanifest"></a>透過寫入封裝 MSBuildForUnity 套件匯入。資訊清單

若要啟用適用于 unity 的 msbuild，請執行 **混合現實工具** 組  >  **msbuild**  >  **使用 msbuild 進行 unity** 相依性解析。 執行此命令之後，MSBuild 應該開始匯入相依性。 匯入可能需要幾秒鐘的時間才會開始。

[ **使用 MSBuild For Unity** 相依性解析] 命令不會顯示確認。 若要確認它是否成功，請開啟 [**視窗**  >  **封裝管理員**]，並確定 [封裝] 清單中顯示 [適用于 Unity 的 MSBuild]。 如果有的話，請假設此步驟成功。

> [!Note]
> 有一個問題會導致 MSBuild for Unity 無法在某些 Unity 2019 版本上正常運作。 如果遇到問題，請參閱 [手動安裝指示](#manual-dotnetadapter-installation)。

![MSB4U 套件管理員](../images/tools/remoting/MSB4UPackageManager.png)

#### <a name="dotnetwinrt-nuget-package-resolution"></a>DotNetWinRT NuGet 套件解析

檢查的最佳方式是在 [資產] 資料夾中搜尋 DotNetWinRT.dll。 如果不存在，請流覽至 [專案] 視圖中的 [資產] 資料夾，然後選取 [] `[ProjectName].Dependencies.msb4u.csproj` 。 假設第1部分成功，應該會有一個具有組建、重建和清除按鈕的自訂偵測器。 請嘗試按一下 [建立] 或 [重建]，然後重新搜尋 DotNetWinRT.dll。 如果該 DLL 現在存在，這個步驟就會成功。

![DotNetAdapter 偵測器](../images/tools/remoting/DotNetAdapterInspector.png)

#### <a name="dotnetadaptercsproj-missing"></a>DotNetAdapter 缺少 .csproj

如果上一個步驟失敗，最好再次檢查您專案中是否有適當的 .csproj。 在 [ **MRTK**  /  **提供者**] 下，檢查  /  **WindowsMixedReality**  /  **Shared**  /  **DotNetAdapter** ，並確認 DotNetAdapter .csproj 存在。 如果您的 .gitignore 忽略 .csproj 檔案，而且您已將 MRTK 檔案認可到遠端存放庫，則其中一個常見的情況是此檔案可能不存在。 在此情況下，請確定您已強制新增 DotNetAdapter .csproj， `git add -f [path/to]/DotNetAdapter.csproj` 以確定它會針對所有其他共同作業者或電腦進行認可和複製。

#### <a name="dotnetwinrt_present-define-written-into-player-settings"></a>DOTNETWINRT_PRESENT 定義寫入播放機設定

從 MRTK 版本2.5.0 開始，基於效能的考慮，不再自動設定此 #define。 若要啟用此旗標，請使用 **混合現實工具** 組  >  **公用程式**  >  **Windows Mixed reality**  >  **檢查** 設定功能表項目。

> [!Note]
> 檢查設定專案不會顯示確認。 若要確認已設定定義，請流覽至 Unity Player 設定。 從該處的 [UWP] 索引標籤底下，檢查腳本定義符號的其他設定。 請確定已在該清單中正確寫入 DOTNETWINRT_PRESENT。 如果有的話，這個步驟就成功了。

![DotNetWinRT 存在](../images/tools/remoting/DotNetWinRTPresent.png)

#### <a name="failure-to-find-dotnetexe"></a>找不到 dotnet.exe 的問題

適用于 Unity 的 MSBuild 取決於系統路徑中現有的 dotnet.exe，dotnet.exe 必須安裝並存在於 PATH 環境變數中。 如果這兩項需求都不成立，Unity 主控台可能會出現此錯誤：

```cmd
Win32Exception: ApplicationName='dotnet', CommandLine='msbuild DotNetAdapter.csproj -restore  -v:minimal -p:NuGetInteractive=true  -t:Build -p:Configuration=Release -nologo', CurrentDirectory='C:\src\Assets\MRTK\Providers\WindowsMixedReality\Shared\DotNetAdapter', Native error= The system cannot find the file specified.
```

解決方法是確保 [已安裝 .Net CORE CLI 工具](https://docs.microsoft.com/dotnet/core/tools/?tabs=netcore2x) ，並重新啟動系統，以強制所有應用程式取得重新整理的系統路徑。

如果在執行上述步驟之後，透過遠端處理的操作仍無法運作，則在裝置上的一般操作設定檔中可能會有設定不正確的問題。 在此情況下，請與 [我們的其中一個說明資源聯繫](../../WelcomeToMRTK.md#getting-help)。

#### <a name="manual-dotnetadapter-installation"></a>手動 DotNetAdapter 安裝

如果無法透過 MSBuild for Unity 執行 DotNetAdapter 安裝，則可以執行下列步驟。

> [!Important]
> 不支援同時使用適用于 Unity 的 MSBuild 和相同專案中的另一個 NuGet 用戶端，因此可能會導致相依性解析問題。

1. 安裝 NuGet 用戶端

    > [!Note]
    > 下列指示假設使用 [適用于 Unity 的 NuGet](https://github.com/GlitchEnzo/NuGetForUnity/releases)

1. 流覽至 NuGet 用戶端 UI

    ![啟動 NuGet UI](../images/tools/remoting/LaunchNuGetForUnity.png)

1. 找出 `Microsoft.Windows.MixedReality.DotNetWinRT` 套件

    ![尋找套件](../images/tools/remoting/LocateDotNetWinRT.png)

1. 選取安裝

1. 啟用[必要的旗](#dotnetwinrt_present-define-written-into-player-settings)標

### <a name="removing-hololens-2-specific-remoting-support"></a>移除 HoloLens 2 特定的遠端支援

如果您因為 DotNetWinRT 介面卡的存在而遇到衝突或其他問題，請前往 [我們的其中一個說明資源](../../WelcomeToMRTK.md#getting-help)。

您也可以透過下列步驟，暫時移除介面卡以因應您的問題：

1. 在 Unity 中，移至 [視窗-> 套件管理員]，並卸載適用于 Unity 的 MSBuild。
1. 在 Unity 的 [資產] 清單中搜尋 DotNetWinRT.dll，並刪除 DLL 或刪除 (MRTK 2.2 或舊版) 的外掛程式，或刪除 (MRTK 2.3 或更新版本或更新版本) 資料夾，其中包含幾個層級。 這應該會移除這些衝突的命名空間，同時保持 MRTK。
1.  (選擇性) 在您的檔案瀏覽器中流覽至 MRTK/Providers/WindowsMixedReality/Shared/DotNetAdapter， (不是 Unity 的資產視圖) 並刪除 `.bin` 和 `.obj` 資料夾。 這會移除 DotNetWinRT 的 NuGet 還原套件的本機快取。
1. 如果您再次執行 MRTK 配置器，請確定您不會重新啟用適用于 Unity 的 MSBuild。

## <a name="xr-sdk-setup-instructions"></a>XR SDK 安裝指示

遵循「 [開始使用 MRTK 和 XR SDK」頁面上的 Windows Mixed Reality 設定指示](../../configuration/GettingStartedWithMRTKAndXRSDK.md#windows-mixed-reality) ，並確定執行編輯後 HoloLens 遠端處理所需的步驟。

## <a name="connecting-to-the-hololens-with-wi-fi"></a>使用 Wi-Fi 連接到 HoloLens

設定好專案之後，就可以建立 HoloLens 的連接。

1. 在 [檔案 **> 組建設定**] 中，確定 [專案組建類型] 已設定為 [**通用 Windows 平臺**]
1. 在 HoloLens 上啟動全像 **遠端處理** 應用程式。
1. 在 Unity 中，如果使用 **XR SDK (，請選取 Window > XR (> 全像 XR) /WINDOWS XR 外掛程式遠端處理)**。

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

USB 纜線連接可提供更佳的轉譯品質和穩定性。 若要使用 USB 纜線連線，請從 Wi-Fi HoloLens 與 HoloLens 的設定中斷連線，並啟動全像遠端播放機應用程式。 它會顯示開頭為169的 IP 位址。 在 Unity 的全像模擬設定中使用此 IP 位址來連接。 一旦識別出 USB 纜線的 IP 位址之後，就可以安全地將 HoloLens 連接到 Wi-Fi。

## <a name="starting-a-remoting-session"></a>啟動遠端會話

將 Unity 連接到 HoloLens 之後，請在編輯器中輸入播放模式。

當會話完成時，結束播放模式。

> [!NOTE]
> 有一些 Unity 版本的已知問題，在遠端會話期間，編輯器可能會在進入播放模式時停止回應。 如果在載入專案時，全像全像是開啟的全像是，就會發生此問題。 若要確保不會發生此問題，請一律在離開 Unity 之前關閉全像的對話方塊。

## <a name="see-also"></a>另請參閱

- [全像遠端的疑難排解和限制](https://docs.microsoft.com/windows/mixed-reality/holographic-remoting-troubleshooting)
- [Microsoft 全像遠端軟體授權條款](https://docs.microsoft.com/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
