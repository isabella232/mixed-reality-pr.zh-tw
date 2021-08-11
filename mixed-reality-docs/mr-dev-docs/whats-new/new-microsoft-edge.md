---
title: Windows Mixed Reality 和新的 Microsoft Edge
description: 瞭解混合現實的新 Microsoft Edge，包括預期、要尋找的更新，以及已知問題。
author: mattzmsft
ms.author: mazeller
ms.date: 08/04/2020
ms.topic: article
keywords: edge、new、沉浸式 web、microsoft edge、browser、vr、360、360 video、360 viewer、webxr、webvr
ms.openlocfilehash: 51efc5c4d3afb4d46ba7722867514f740a9f60a4280652fdbd665134f83af23d
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2021
ms.locfileid: "115218820"
---
# <a name="the-new-microsoft-edge-for-windows-mixed-reality"></a>Windows Mixed Reality 的新 Microsoft Edge

[新的 Microsoft Edge 現在已可供下載](https://blogs.windows.com/windowsexperience/?p=173496)，但客戶也可以[等候未來的更新](https://blogs.windows.com/msedgedev/2020/01/15/upgrading-new-microsoft-edge-79-chromium/)，在未來幾個月內依照測量出的推出方法，以 Windows 10 進行安裝。 

有了這項新聞，**我們想要讓 Windows Mixed Reality VR 耳機客戶知道新 Microsoft Edge 的預期，並顯示擱置的更新，以改善 Windows Mixed Reality 中的流覽體驗**。

## <a name="introducing-the-new-microsoft-edge"></a>新 Microsoft Edge 簡介

新的 Microsoft Edge 採用桌上型電腦上[Chromium 的開放原始碼專案](https://blogs.windows.com/windowsexperience/2018/12/06/microsoft-edge-making-the-web-better-through-more-open-source-collaboration/)，為客戶建立更好的相容性，並為 網頁程式開發人員提供較少的 web 片段。 它也支援在啟動時 WebXR，這是建立 VR 耳機之沉浸式 web 體驗的新標準，取代 WebVR。

>[!IMPORTANT]
>當您在最新的 Windows 10 裝置上安裝 Microsoft Edge 時，將會取代您電腦上先前 (舊版) 版本。

## <a name="getting-ready-for-the-new-microsoft-edge"></a>準備迎接新的 Microsoft Edge

Windows Mixed Reality如果您想要在混合實境首頁中使用新 Microsoft Edge 的 VR 耳機客戶應該 **升級至 Windows 10 1903 版或更新版本，以進行 Win32 應用 (程式的原生支援，如 Microsoft Edge 中新的) 混合實境首頁**。 請檢查 Windows Update 或[手動安裝最新版本的 Windows 10](https://www.microsoft.com/en-us/software-download/windows10)。

為了充分利用混合實境首頁中的最佳 Microsoft Edge 經驗，我們也建議您等候 **新 Microsoft Edge 的一些關鍵 Windows Mixed Reality 優化，以取得 Windows 10 1903 版或更新版本 (的2020-01 累積更新**，這應該會在1月底的) 中提供。

>[!IMPORTANT]
>如果您選擇在進行這些更新之前下載新的 Microsoft Edge，在 Windows Mixed Reality (中將會有一些已知問題，您可以在下面) 閱讀相關資訊。

## <a name="known-issues"></a>已知問題

### <a name="known-issues-resolved-by-the-2020-01-cumulative-update-for-windows-10-version-1903-or-later"></a>2020-01 累積更新針對 Windows 10 1903 版 (或更新版本所解決的已知問題) 

- 啟動任何 Win32 應用程式（包括新的 Microsoft Edge）都會使耳機顯示短暫地凍結。
- Microsoft Edge 圖格會從 Windows Mixed Reality [開始] 功能表中消失， (您可以在 [傳統應用程式] 資料夾) 中找到它。
- 先前 Microsoft Edge 的 Windows 仍會放置在混合實境首頁，但無法使用。 在桌面應用程式中嘗試啟用這些 windows 啟動邊緣。
- 選取混合實境首頁中的超連結，會在桌上型電腦上啟動網頁瀏覽器，而不是在混合實境首頁上啟動。
- WebVR 展示應用程式存在於混合實境首頁中，儘管不再支援 WebVR。
- 鍵盤啟動和視覺效果的一般改進。

### <a name="monitor-and-input-handling-issues"></a>監視和輸入處理問題

針對 Windows 10 1903 版 (或更新版本) 取得2020-01 累積更新之後，虛擬監視器將會在 > 會話期間顯示為 **設定 > 系統 Windows Mixed Reality 顯示** 的一般實體監視器。 某些客戶（尤其是有一個以上的實體監視器）可能會發現桌上出版面配置和輸入處理的問題。

**發生這種情況的原因**

[Windows 10 2019 年5月更新](/windows/mixed-reality/enthusiast-guide/release-notes-may-2019)引進 Windows Mixed Reality 中的傳統 Win32 應用程式支援。 若要啟用這種支援，必須建立虛擬監視器來裝載 Win32 應用程式。 每次啟動新的 Win32 應用程式時，都必須建立另一個虛擬監視器。 可惜的是，建立虛擬監視器是一項密集的工作，可能會使耳機顯示短暫地凍結。 客戶提供意見反應，指出這是不舒服且干擾性的體驗。 由於有意見反應和 Win32 應用程式的使用方式，因此我們決定在 Windows Mixed Reality 啟動期間預先配置三個虛擬監視器。 這可避免中斷，讓客戶可以啟動最多三個並行的 Win32 應用程式，而不會遇到耳機顯示凍結。

**因應措施**

我們已收到一些客戶的意見反應，特別是具有多個實體監視器的客戶，會想要停用此虛擬監視器預先配置。 為了提供客戶控制，我們啟用了包含變更登錄機碼值的因應措施，可透過下列 Windows 更新取得：

- 2020-07 Windows 10 2004 版的累計更新預覽 (KB4568831) 
- 2020-10 Windows 10 1909 版的累計更新預覽 (KB4580386) 
- 2020-10 Windows 10 1903 版的累計更新預覽 (KB4580386) 

>[!NOTE]
>修改登錄機碼值的目的是要讓 advanced 使用者。

>[!WARNING]
>停用虛擬監視器預先配置，可能會在您啟動 Win32 應用程式 (例如串流、新 Microsoft Edge 或 Windows Mixed Reality 中的 Google Chrome) 時，導致您的耳機顯示短暫凍結。

若要停用虛擬監視器預先配置：
1. 檢查上面所列的其中一個 Windows 10 累積更新預覽版本的 **Windows Update** ，並在可用時安裝更新。 您可以在 [Windows Update 設定] 頁面上的 [**選用更新**] 或 [ **Advanced options** ] 下找到更新
2. 啟動 **登錄編輯程式**
3. 流覽至 [HKEY_CURRENT_USER\SOFTWARE\Microsoft\Windows\CurrentVersion\Holographic\"
4. 如果 "PreallocateVirtualMonitors" REG_DWORD 不存在，請選取 [ **編輯 > New > DWORD (32 位) 值** ，然後輸入 PreallocateVirtualMonitors 做為名稱來建立它。
5. 如果 "PreallocateVirtualMonitors" REG_DWORD 存在 (或您剛才) 建立，請按兩下該專案，然後將 [值資料] 從 1 (預設值) 為 0 (零) 
    * TRUE-1
    * FALSE-0

虛擬監視器現在會在您嘗試在 Windows Mixed Reality （而不是預先配置）中啟動 Win32 應用程式時進行配置。 若要重設此值並重新啟用虛擬監視器預先配置，請將 DWORD 「值資料」傳回1。

### <a name="other-known-issues"></a>其他已知問題

-   當混合實境入口關閉時，在 Windows Mixed Reality 中開啟的網站將會遺失。 Microsoft Edge 視窗將停留在混合實境首頁的放置位置。
- 具有混合式 GPU 設定的電腦上可能無法正確啟動 WebXR 體驗，包括360檢視器擴充功能。 若要解決此問題，您可以在新的 Microsoft Edge 中啟用預覽功能。 流覽至 `edge://flags` ，並搜尋「多重 gpu」，並啟用稱為 **WEBXR 多重 gpu 支援** 的旗標。
-   Microsoft Edge windows 的音訊不會 hrtf。
-   **修正于360檢視器延伸模組版本 2.3.8**：在 Windows Mixed Reality 中從 YouTube 開啟360影片可能會導致視頻耳機中的影片失真。 重新開機 Edge 應該會以不可見的更新360檢視器延伸模組來解決此問題。 您可以 `edge://system/` 在網址列中輸入，然後選取 [擴充功能] 旁的 **展開** 按鈕，以確認您擁有的延伸模組版本。