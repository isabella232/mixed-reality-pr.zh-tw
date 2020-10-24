---
title: 在 Windows Mixed Reality 中使用 Microsoft Edge
description: 準備好開始進行新的 Microsoft Edge Windows Mixed Reality。 包含預期的變更、要尋找的更新，以及已知問題。
author: mattzmsft
ms.author: mazeller
ms.date: 08/04/2020
ms.topic: article
keywords: Windows Mixed Reality、混合的現實、虛擬實境、VR、MR、Home、流覽、規避、應用程式、遊戲、Microsoft Edge、chromium、邊緣
ms.openlocfilehash: 40f5f57883c5d8ad1a03076411a077deb9979c71
ms.sourcegitcommit: 1aae69e26ae872b724be1bd1ae0b3158c49dc7e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2020
ms.locfileid: "92499563"
---
# <a name="windows-mixed-reality-and-the-new-microsoft-edge"></a>Windows Mixed Reality 和新的 Microsoft Edge

[新的 Microsoft Edge](https://www.microsoft.com/edge)可供下載，並已開始透過 Windows Update 自動推出給客戶。 

新的 Microsoft Edge [採用桌面上的 Chromium 開放原始碼專案](https://blogs.windows.com/windowsexperience/2018/12/06/microsoft-edge-making-the-web-better-through-more-open-source-collaboration/) ，為客戶建立更好的 web 相容性，並讓所有 網頁程式開發人員都能更少的網路片段。 它也支援在啟動時 WebXR，這是建立 VR 耳機之沉浸式 web 體驗的新標準，取代 WebVR。

>[!IMPORTANT]
>當您在最新的 Windows 10 裝置上安裝 Microsoft Edge 時，將會取代您電腦上先前 (舊版) 版本。

## <a name="installing-the-new-microsoft-edge"></a>安裝新的 Microsoft Edge 

在安裝新的 Microsoft Edge 之前，請 **升級為 Windows 10 1903 版或更新版本，以提供 Win32 應用程式的原生支援 (例如) 中的新 Microsoft Edge Windows Mixed Reality ** 。 請檢查 Windows Update 或 [手動安裝最新版本的 Windows 10](https://www.microsoft.com/software-download/windows10)。

Windows 10 1903 版或更新版本之後，您就可以開始使用新的 Microsoft Edge！ 新 Microsoft Edge 是透過 Windows Update 推出，但如果您想要更快，可以從 [Microsoft Edge 網站](https://www.microsoft.com/edge) 手動安裝新的 Microsoft Edge。

>[!IMPORTANT]
>新的 Microsoft Edge 推出 WebXR 的支援，這是為 VR 耳機建立沉浸式 web 體驗的新標準。 當您安裝新的 Microsoft Edge 時，將無法再于 Microsoft Edge 播放 WebVR 體驗。 

## <a name="known-issues"></a>已知問題

### <a name="known-issues-resolved-by-the-2020-01-cumulative-update-for-windows-10-version-1903-or-later"></a>2020-01 累積更新針對 Windows 10 1903 版 (或更新版本所解決的已知問題) 

- 啟動任何 Win32 應用程式（包括新的 Microsoft Edge）都會使耳機顯示短暫地凍結。
- Microsoft Edge 圖格會從 Windows Mixed Reality [開始] 功能表中消失， (您可以在 [傳統應用程式] 資料夾) 中找到它。
- 先前 Microsoft Edge 的 Windows 仍會放置在混合實境首頁，但無法使用。 嘗試啟用這些 windows 會在桌面應用程式中啟動 Edge。
- 選取混合實境首頁中的超連結，會在桌上型電腦上啟動網頁瀏覽器，而不是在混合實境首頁上啟動。
- WebVR 展示應用程式存在於混合實境首頁中，儘管不再支援 WebVR。
- 鍵盤啟動和視覺效果的一般改進。

### <a name="monitor-and-input-handling-issues"></a>監視和輸入處理問題

取得 Windows 10 1903 版 (或更新版本) 的2020-01 累積更新之後，虛擬監視器會顯示為 [設定] 中的一般實體監視器， **> 系統 >** 在 Windows Mixed Reality 會話期間顯示。 某些客戶（特別是具有多個實體監視器的客戶）可能會發現桌面配置和輸入處理的問題。

**發生這種情況的原因**

[Windows 10 2019 年5月更新](https://docs.microsoft.com/windows/mixed-reality/release-notes-may-2019)引進 Windows Mixed Reality 中的傳統 Win32 應用程式支援。 若要啟用這種支援，必須建立虛擬監視器來裝載 Win32 應用程式。 每次啟動新的 Win32 應用程式時，都必須建立另一個虛擬監視器。 可惜的是，建立虛擬監視器是一項密集的工作，可能會使耳機顯示短暫地凍結。 客戶提供意見反應，指出這是不舒服且干擾性的體驗。 由於該意見反應和 Win32 應用程式的使用方式不斷增加，因此我們決定在 Windows Mixed Reality 啟動時預先配置三個虛擬監視器，以避免此中斷，並讓客戶可以啟動最多三個並行的 Win32 應用程式，而不會遇到耳機顯示凍結。

**因應措施**

我們已收到一些客戶的意見反應，特別是具有多個實體監視器的客戶，會想要停用此虛擬監視器預先配置。 為了提供客戶控制和選擇，我們啟用了包含變更登錄機碼值的因應措施，可透過下列 Windows 更新取得：
- 2020-07 Windows 10 2004 版的累計更新預覽 (KB4568831) 
- 2020-10 Windows 10 1909 版的累計更新預覽 (KB4580386) 
- 2020-10 Windows 10 1903 版的累計更新預覽 (KB4580386) 

>[!NOTE]
>修改登錄機碼值的目的是要讓 advanced 使用者。

>[!WARNING]
>停用虛擬監視器預先配置，可能會在您啟動 Win32 應用程式 (例如串流、新 Microsoft Edge 或 Windows Mixed Reality 中的 Google Chrome) 時，導致您的耳機顯示短暫凍結。

若要停用虛擬監視器預先配置：
1. 檢查上面所列的其中一個 Windows 10 累積更新預覽版本的 **Windows Update** ，並在可用時安裝更新 (您可能會在 [Windows Update 設定] 頁面上的 [ **選擇性更新** ] 或 [ **Advanced options** ] 下找到更新) 
2. 啟動 **登錄編輯程式**
3. 流覽至 [HKEY_CURRENT_USER\SOFTWARE\Microsoft\Windows\CurrentVersion\Holographic\"
4. 如果 "PreallocateVirtualMonitors" REG_DWORD 不存在，請選取 [ **編輯 > New > DWORD (32 位) 值** ，然後輸入 PreallocateVirtualMonitors 做為名稱，以建立它
5. 如果 "PreallocateVirtualMonitors" REG_DWORD 存在 (或您剛才) 建立，請按兩下該專案，然後將 [值資料] 從 1 (預設值) 為 0 (零) 
    * TRUE-1
    * FALSE-0

虛擬監視器現在會在您嘗試在 Windows Mixed Reality （而不是預先配置）中啟動 Win32 應用程式時進行配置。 若要重設此值並重新啟用虛擬監視器預先配置，請將 DWORD 「值資料」傳回1。

### <a name="additional-known-issues"></a>其他已知問題

-   在 Windows Mixed Reality 中開啟的網站將會在混合實境入口關閉時遺失，不過 Microsoft Edge 視窗仍會保留在混合實境首頁中的位置。
- 具有混合式 GPU 設定的電腦上可能無法正確啟動 WebXR 體驗，包括360檢視器擴充功能。 您可以藉由在圖形配接器軟體中選取您專用的 GPU 作為預設 GPU，來解決此問題。
-   未 hrtf 來自 Microsoft Edge windows 的音訊。
-   **修正于360檢視器延伸模組版本 2.3.8**：在 Windows Mixed Reality 中從 YouTube 開啟360影片可能會導致視頻耳機中的影片失真。 重新開機 Edge 應該會以不可見的更新360檢視器延伸模組來解決此問題。 您可以 `edge://system/` 在網址列中輸入，然後選取 [擴充功能] 旁的 **展開** 按鈕，以確認您擁有的延伸模組版本。
