---
title: 使用 Windows 裝置入口網站
description: 了解如何使用 Windows 裝置入口網站從遠端透過 Wi-Fi 或 USB 來設定及管理您的裝置。
author: hamalawi
ms.author: moelhama
ms.date: 08/03/2020
ms.topic: article
keywords: Windows 裝置入口網站, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: d772175683208ac0e3ed4b3163ca561da416c1cf
ms.sourcegitcommit: 593e8f80297ac0b5eccb2488d3f333885eab9adf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2021
ms.locfileid: "112919809"
---
# <a name="using-the-windows-device-portal"></a>使用 Windows 裝置入口網站

<table>
<tr>
<th>功能</th><th style="width:150px"><a href="/hololens/hololens1-hardware">HoloLens (第 1 代)</a></th><th style="width:150px">HoloLens 2</th><th style="width:150px">
</tr><tr>
<td> Windows 裝置入口網站</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"></td>
</tr>
</table>

HoloLens 的 Windows 裝置入口網站能讓您從遠端透 Wi-Fi 或 USB 來設定及管理您的裝置。 Device Portal 是您 HoloLens 上的網頁伺服器，您可以從電腦上的網頁瀏覽器與它連線。 裝置入口網站包含許多工具，可協助您管理 HoloLens，並對應用程式進行偵錯及最佳化。

本文件特別說明適用於 HoloLens 的 Windows 裝置入口網站。 若要使用適用於傳統型 Windows 裝置入口網站 (包括 Windows Mixed Reality)，請參閱 [Windows 裝置入口網站概觀](/windows/uwp/debug-test-perf/device-portal)

## <a name="setting-up-hololens-to-use-windows-device-portal"></a>設定 HoloLens 以使用 Windows 裝置入口網站

1. 開啟您的 HoloLens 並將裝置戴上。
2. 使用 HoloLens2 的[開始手勢](/hololens/hololens2-basic-usage#start-gesture)或 HoloLens (第 1 代) 的[綻開](/hololens/hololens1-basic-usage#open-the-start-menu-with-bloom)，以啟動主功能表。 
3. 注視 [設定] 圖格，並在 HoloLens (第一代) 上進行[空中點選](/hololens/hololens1-basic-usage#select-holograms-with-gaze-and-air-tap)手勢。 [加以觸控或使用手部射線](/hololens/hololens2-basic-usage)，也可以在 HoloLens 2 上進行選取。 
4. 選取 [更新] 功能表項目。
5. 選取 [適用於開發人員]  功能表項目。
6. 啟用 [開發人員模式]。

> [!IMPORTANT]
> 如果目前處於多重使用者模式，且您不是系統管理員，進入開發人員模式的功能可能會呈現為灰色。請確定您是 **[裝置的系統管理員](/hololens/security-adminless-os)** 。

7. [向下捲動](../../design/gaze-and-commit.md#composite-gestures)並啟用 **裝置入口網站**。
8. 如果您要設定 Windows 裝置入口網站，以便透過 USB 或 Wi-Fi 將應用程式部署到此 HoloLens，請選取 [配對] 以[產生配對 PIN](using-visual-studio.md)。 將 [設定] 應用程式保留在 [PIN] 快顯視窗中，直到您在第一次部署期間，將 PIN 輸入 Visual Studio 為止。

![在 Windows 全像攝影版的 [設定] 應用程式中啟用開發人員模式](images/using-windows-portal-img-01.jpg)

## <a name="connecting-over-wi-fi"></a>透過 Wi-Fi 連線

1. [將您的 HoloLens 連線到 Wi-Fi](/hololens/hololens-network)。
2. 尋找裝置的 IP 位址，可行方式如下：
  * 移至 [設定] > [網路和網際網路] > [Wi-Fi] > [進階選項]。
  * 移至 [設定] > [網路和網際網路]，然後選取 [硬體屬性]。
  * 使用「我的 IP 位址是什麼？」 語音命令。

![HoloLens 2 設定](images/using-windows-portal-img-02.jpg)

3. 從您電腦上的網頁瀏覽器，移至 https://<YOUR_HOLOLENS_IP_ADDRESS>
   * 瀏覽器將會顯示下列訊息：「此網站的安全性憑證有問題」，因為發給裝置入口網站的憑證是測試憑證。 您可以暫時略過這個憑證錯誤並繼續。

## <a name="connecting-over-usb"></a>透過 USB 連線

> [!IMPORTANT]
> 基於新的瀏覽器標準，不再建議使用 IpOverUsb，因為它需要使用埠10080。 如果您仍然想要使用 IpOverUsb，請在 Visual Studio 安裝期間檢查 [USB 裝置連線能力] 方塊（預設不會核取）。 相反地，我們建議使用 UsbNcm 連接，HoloLens 2 上預設支援此功能。 如果您使用 HoloLens 1，建議您使用 WiFi 連接到您的電腦。

1. 如果您的 HoloLens 2 正在執行 Windows 全像21H1 版或更高版本，請移至 [設定] 應用程式中的 [適用于開發人員]，並確定已開啟 [裝置探索]。 
2. 使用 USB 纜線將您的 HoloLens 2 連接到您的電腦。
3. 尋找您的 UsbNcm IP。 有幾種方式可以執行此作業：
  * 在裝置上的 [設定] 應用程式中 (此方法僅適用于執行 Windows 全像21H1 或更高版本的 HoloLenses，並開啟 [裝置探索]。 ) 
    1. 移至裝置上的 [設定] 應用程式。
    2. 移至開發人員的「更新 & 安全性」 >」。 這是您裝置入口網站啟用的相同位置。
    3. 在頁面底部複製您的 **乙太** 網路 IP 位址。 這是您的 UsbNcm IP。 
    ![HoloLens 2 設定-UsbNcm IP](images/deviceportal_usbncm_ipaddress.jpg)

  * 在裝置入口網站 
    1. 在您的裝置上，使用 HoloLens 的 WiFi 位址開啟裝置入口網站。 如果您不知道 HoloLens 的 WiFi 位址，可以使用語音命令「我的 IP 位址為何？」
    2. 移至系統 > 網路
    3. 在 [IP 設定] 面板中頁面的最右側，找出開頭為 "Description： UsbNcm Function" 的區段。
    4. 您的 UsbNcm IP 是 [IPv4 位址] 行。 您可以複製位址或直接按一下位址-它是超連結，會使用 UsbNcm IP 重新開啟裝置入口網站。
  
  * 在命令提示字元中
    1. 在任何命令提示字元中，流覽至 \<SDK version> 安裝 WINDOWS 10 SDK 的 bin \x86 資料夾，例如 C:\Program Files (x86) \Windows Kits\10\bin\10.0.19041.0\x86。
    2. 輸入 "winappdeploycmd.exe devices"，然後按 Enter 鍵。
    3. 在輸出中，尋找模型/名稱資料行是 HoloLens 裝置名稱的專案，例如 HOLOLENS-xxxxxx。 UsbNcm IP 位於這一行的開頭，且將會是 169.254.. x.x. 格式的自動私人 IP 位址。 複製此位址。 
 
4. 如果您複製了 UsbNcm IP，請從您電腦上的網頁瀏覽器移至 HTTPs://，然後再移至您的 UsbNcm IP。

### <a name="moving-files-over-usb"></a>透過 USB 移動檔案

您可以直接將檔案從電腦移至 HoloLens，而無須進行任何額外的設定。
1. 使用 USB 線將您的電腦連接到 HoloLens
2. 將檔案拖曳到桌面上的 **PC\\[Your_HoloLens_Device_Name]\Internal Storage** 中
3. 開啟 [開始] 功能表，然後在 HoloLens上選取 [所有應用程式] > [檔案總管]

> [!NOTE]
> 您可能需要選取面板左側的 [此裝置]，從 [最近使用] 瀏覽至他處以找出您的檔案。 

## <a name="connecting-to-an-emulator"></a>連線到模擬器

您也可以透過模擬器使用 Device Portal。 若要連線到裝置入口網站，請使用[工具列](using-the-hololens-emulator.md)。 選取此圖示：![開啟裝置入口網站圖示](images/emulator-deviceportal.png) **開啟裝置入口網站**：在模擬器中開啟 HoloLens OS 的 Windows 裝置入口網站。

## <a name="creating-a-username-and-password"></a>建立使用者名稱和密碼

![設定 Windows 裝置入口網站的存取權](images/windows-device-portal-credentials-reset-page-1000px.png)<br>
設定 Windows 裝置入口網站的存取權

首次在 HoloLens 上連線到 Device Portal 時，您必須建立使用者名稱和密碼。
1. 在您電腦上的網頁瀏覽器中，輸入 HoloLens 的 IP 位址。 [設定存取] 頁面隨即開啟。
2. 選取或點選 [要求 PIN]，並查看 HoloLens 顯示畫面以取得產生的 PIN。
3. 輸入 [您裝置上顯示的 PIN] 文字方塊中的 PIN。
4. 輸入您會用來連線到 Device Portal 的使用者名稱。 它並不需要是 Microsoft 帳戶 (MSA) 或網域名稱。
5. 輸入密碼並確認它。 密碼長度必須至少為七個字元。 它並不需要是 MSA 或網域密碼。
6. 按一下 [配對]，在 HoloLens 上連線到 Windows 裝置入口網站。

如果您想在任何時候變更此使用者名稱或密碼，可以造訪裝置安全性頁面來重複此程序，方法是瀏覽到： https://<YOUR_HOLOLENS_IP_ADDRESS>/devicepair.htm。

## <a name="security-certificate"></a>安全性憑證

如果您在瀏覽器中看見「憑證錯誤」，可透過與裝置建立信任關係來加以修正。

每個 HoloLens 都會為其 SSL 連線產生自我簽署憑證。 根據預設，此憑證並不會受到您電腦的網頁瀏覽器信任，因此您可能會收到「憑證錯誤」。 透過 USB 或您信任的 Wi-Fi 網路，從您的 HoloLens 下載此憑證，並在電腦上信任該憑證，您便可安全地連線到您的裝置。
1. **請確保您是在安全的網路上 (USB 或您信任的 Wi-Fi 網路)。**
2. 從裝置入口網站上的 [安全性] 頁面下載此裝置的憑證。
   * 瀏覽到： https://<YOUR_HOLOLENS_IP_ADDRESS>/devicepair.htm
   * 開啟 [系統] > [喜好設定] 的節點。 
   * 向下捲動至 [裝置安全性]，選取 [下載此裝置的憑證] 按鈕。
3. 安裝您電腦上「信任的根憑證授權」存放區中的憑證。
   * 從 [Windows] 功能表中，輸入：管理電腦憑證並啟動 applet。
   * 展開 [信任的根憑證授權] 資料夾。
   * 選取 [憑證] 資料夾。
   * 從 [動作] 功能表中，選取：[所有工作] > [匯入]...
   * 使用您從 Device Portal 下載的憑證檔案完成憑證匯入精靈。
4. 重新啟動瀏覽器。

>[!NOTE]
> 僅在裝置刷新時，才會信任此裝置的憑證，且使用者才必須再次執行此程序。

## <a name="sideloading-applications"></a>側載應用程式

### <a name="installing-a-certificate"></a>安裝憑證

1. 在 Windows 裝置入口網站中，瀏覽至 [應用程式管理員] 頁面
2. 在 [部署應用程式] 區段中，選取 [安裝憑證]
3. 在 [選取用於簽署應用程式套件的憑證檔案 (.cer)] 下，選取 [選擇檔案]，並瀏覽至與您要側載的應用程式套件相關聯的憑證
4. 選取 [安裝] 可開始進行安裝

![螢幕擷取畫面：在 Windows 裝置入口網站中開啟的 [應用程式管理員] 頁面](images/sideloading-1.png)

### <a name="installing-an-app"></a>安裝應用程式

> [!NOTE]
> 為了讓應用程式能夠透過裝置入口網站成功完成安裝，其必須經過憑證的簽署，您必須先將此憑證安裝到裝置上，然後才能嘗試安裝應用程式。 如需相關指示，請參閱[上一節](#installing-a-certificate)。

1. 當您[從 Visual Studio 建立了應用程式套件](using-visual-studio.md)後，就可以將套件從產生的檔案遠端安裝到您的裝置上：

![螢幕擷取畫面：應用程式套件的檔案內容](images/sideloading-2.png)

2. 在 Windows 裝置入口網站中，瀏覽至 [應用程式管理員] 頁面
3. 在 [部署應用程式] 區段中，選取 [本機存放區]
4. 在 [選取應用程式套件] 下，選取 [選擇檔案]，並瀏覽至您要側載的應用程式套件
5. 如果您在安裝應用程式時，要一起安裝選用項目或架構套件，請勾選對應的方塊，然後選取 [下一步]：

![螢幕擷取畫面：在 Windows 裝置入口網站中開啟的 [應用程式管理員] 頁面，其中已醒目提示 [本機儲存體] 索引標籤](images/sideloading-3.png)

6. 選取 [安裝] 可開始進行安裝
 
![螢幕擷取畫面：在 Windows 裝置入口網站中開啟的 [應用程式管理員] 頁面，且安裝已成功完成](images/sideloading-4.png) 

安裝完成後，回到 HoloLens 上的 [所有應用程式] 頁面，然後啟動新安裝的應用程式！

## <a name="device-portal-pages"></a>Device Portal 頁面

### <a name="home"></a>首頁

![Microsoft HoloLens 上的 Windows 裝置入口網站首頁](images/using-windows-portal-img-04.png)<br>
*Microsoft HoloLens 上的 Windows 裝置入口網站首頁*

您的 Device Portal 工作階段從首頁開始。 從首頁左側的瀏覽列中存取其他頁面。

頁面頂端的工具列能讓您存取常用狀態與功能。
* **線上**：指出裝置是否已連線到 Wi-Fi。
* **關機**：關閉裝置。
* **重新啟動**：關閉裝置電源並重新開啟。
* **安全性**：開啟 [裝置安全性] 頁面。
* **冷卻**：指出裝置的溫度。
* **A/C**：指出裝置是否已插上電源並且正在充電。
* **說明**：開啟 REST 介面文件頁面。

首頁將顯示下列資訊：
* **裝置狀態：** 監視裝置的健康狀況並報告嚴重錯誤。
* **Windows 資訊：** 顯示 HoloLens 的名稱，以及目前安裝的 Windows 版本。
* [喜好設定] 區段包含下列設定：
   * **IPD**：設定瞳孔間距 (IPD) - 這是使用者雙眼注視前方時，兩個瞳孔中心點之間的距離 (以公釐為單位)。 此設定會立即生效。 預設值會在您設定裝置時自動計算。
   * **裝置名稱**：為 HoloLens 指派名稱。 在變更此值之後，重新啟動裝置才能生效。 按一下 [儲存] 之後，將會有對話方塊詢問您是否要立即重新啟動裝置，或稍後再重新啟動。
   * **睡眠設定**：設定裝置在接上電源及使用電池的情況下，在進入睡眠之前所需等待的時間長度。

### <a name="3d-view"></a>3D 檢視

![Microsoft HoloLens 上 Windows 裝置入口網站的 3D 檢視頁面](images/using-windows-portal-img-05.png)<br>
*Microsoft HoloLens 上 Windows 裝置入口網站的 3D 檢視頁面*

使用 [3D 檢視] 頁面來查看 HoloLens 解譯您周遭環境的方式。 使用滑鼠來瀏覽檢視：
* 旋轉：按下滑鼠左鍵 + 移動滑鼠；
* 平移：按下滑鼠右鍵 + 移動滑鼠；
* 縮放：滑鼠滾輪。
* **追蹤選項**
   * 選取 [強制視覺追蹤] 來開啟持續性視覺追蹤。 
   * **暫停** 將會停止視覺追蹤。
* **檢視選項**：設定 3D 視圖上的選項：
  * **追蹤**：指出視覺追蹤是否為作用中。
  * **顯示樓面**：顯示棋盤式的樓面規劃。
  * **顯示範圍**：顯示檢視範圍。
  * **顯示穩定平面**：顯示 HoloLens 用來穩定動作的平面。
  * **顯示網格**：顯示代表您周遭環境的空間對應網格。
  * **顯示空間錨點**：顯示作用中應用程式的空間錨點。 選取 [更新] 按鈕，才能取得並重新整理錨點。
  * **顯示詳細資料**：隨著下列數據變更，即時顯示雙手位置、頭部旋轉四元數，以及裝置原點向量。
  * **全螢幕按鈕**：以全螢幕模式顯示 3D 檢視。 按下 ESC 以離開全螢幕檢視。
* **表面重建**：選取或點選 [更新] 以顯示裝置中最新的空間對應網格。 可能需要花費一些時間 (最多幾秒鐘) 才能完成完整作業。 網格並不會在 3D 檢視中自動更新，您必須手動選取 [更新] 以取得來自裝置的最新網格。 選取 [儲存] 以將目前的空間對應網格在您的電腦上儲存為 obj 檔案。
* **空間錨點**：選取 [更新] 以顯示或更新作用中應用程式的空間錨點。

### <a name="map-manager"></a>地圖管理員

地圖管理員可讓您跨裝置共用地圖，藉以設定實景娛樂客戶的共用體驗。 此工具可讓您匯入及匯出系統地圖和錨點。  

若要存取地圖管理員，請登入裝置入口網站，然後選取 [混合實境] -> [地圖管理員]： 

![Windows 裝置入口網站中的地圖管理員頁面](images/using-windows-portal-img-06.png)
*Microsoft HoloLens 上的 Windows 裝置入口網站中的地圖管理員頁面*

#### <a name="exporting-and-importing-maps"></a>匯出和匯入地圖

若要匯出地圖，請選取 [匯出系統地圖和錨點]。 這可能需要一些時間，請等候 30-60 秒，讓地圖完成匯出。 完成後，檔案就會下載到您的瀏覽器中。  

若要匯入地圖和錨點，請分別選取 [上傳地圖檔案] 和 [上傳錨點檔案]，然後選取您已匯出的地圖或錨點檔案。 上傳的地圖或錨點檔案可來自任何其他的 HoloLens 裝置。 

> [!NOTE]
> 在 HoloLens 上，您也可以匯入和匯出空間對應資料基底。 不過，這並不適用於非 HoloLens 裝置。  


### <a name="mixed-reality-capture"></a>混合實境擷取

![Microsoft HoloLens 上 Windows 裝置入口網站的混合實境擷取頁面](images/using-windows-portal-img-07.png)<br>
*Microsoft HoloLens 上 Windows 裝置入口網站的混合實境擷取頁面*

使用 [混合實境擷取] 頁面來儲存來自 HoloLens 的媒體串流。
* **擷取設定**：藉由檢查下列設定來控制所擷取的媒體串流：
  * **全像投影**：在影片串流中擷取全像投影內容。 全像投影是以單聲道進行轉譯，而非立體聲。
  * **PV 相機**：擷取來自相片/攝影機的影片串流。
  * **麥克風音訊**：擷取來自麥克風陣列的音訊。
  * **App 音訊**：擷取來自目前執行中 App 的音訊。
  * **從相機呈現**：如果 [受執行中應用程式支援](mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in) (僅限 HoloLens 2)，則將要從相片/攝影機角度進行的擷取對齊。
  * **即時預覽品質**：選取即時預覽的螢幕解析度、畫面播放速率，以及串流速率。
* **音訊設定** (僅限 HoloLens 2)：
  * **音訊媒體類別**：選取要在處理麥克風時使用的類別。 [預設值] 會包含部分環境，而 [通訊] 會套用背景噪音消除。
  * **App 音訊增益**：套用至 App 音訊音量的增益。
  * **麥克風音訊增益**：套用至麥克風音訊音量的增益。
* **相片和影片設定** (HoloLens 2，2004 版或更新版本)：
  * **擷取設定檔**：選取拍攝相片和影片時所使用的設定檔。 此設定檔會決定可用的解析度和畫面播放速率。
  * **相片解析度**：相片將採用的解析度。
  * **影片解析度和畫面播放速率**：影片將採用的解析度和畫面播放速率。
  * **影片防震緩衝區**：拍攝影片時使用的緩衝區大小。 值愈高，快速移動時的補償效果愈好。
* 選取或點選 [即時預覽] 按鈕以顯示擷取串流。 **停止即時預覽** 將會停止擷取串流。
* 選取或點選 [錄製] 來開始使用指定的設定錄製混合實境串流。 **停止錄製** 將會中止並儲存錄製內容。
* 選取或點選 [拍攝相片] 來從擷取串流中拍攝靜止影像。
* 選取或點選 [還原預設設定] 以還原音訊、相片和影片設定的預設設定。
* **影片與相片**：顯示在裝置上所拍攝影片和相片擷取的清單。

此頁面上的所有設定都適用於使用 Windows 裝置入口網站取得的擷取。 有些則額外適用於系統 MRC，包括 [開始] 功能表、硬體按鈕、全域語音命令、Miracast 和自訂 MRC 錄製器。

|  設定  |  適用於系統 MRC  |  適用於自訂 MRC 錄製器 |
|----------|----------|----------|
|  全像投影  |  否  |  否 |
|  PV 相機  |  否  |  否 |
|  麥克風音訊  |  否  |  否 |
|  App 音訊  |  否  |  否 |
|  從相機呈現  |  是    |  是 (可以覆寫) |
|  即時預覽品質  |  否  |  否 |
|  音訊媒體類別  |  是  |  否 |
|  App 音訊增益  |  是  |  是 (可以覆寫) |
|  麥克風音訊增益  |  是  |  是 (可以覆寫) |
|  擷取設定檔  |  是  |  否 |
|  相片解析度  |  是  |  否 |
|  影片解析度和畫面播放速率  |  是  |  否 |
|  影片防震緩衝區  |  是  |  是 (可以覆寫) |

> [!NOTE]
> [同步 MRC 有以下限制](mixed-reality-capture-for-developers.md#simultaneous-mrc-limitations)：
> * 如果應用程式在 Windows 裝置入口網站錄製影片時嘗試存取相片/攝影機，將會停止影片錄製。
>   * 如果應用程式透過 SharedReadOnly 模式存取相片/攝影機，則 HoloLens 2 不會停止錄製影片。
> * 如果應用程式主動使用相片/攝影機，Windows 裝置入口網站就能夠拍攝相片或錄製影片。
> * 即時串流：
>   * HoloLens (第 1 代) 可避免應用程式在從 Windows 裝置入口網站即時串流時存取相片/攝影機。
>   * 如果應用程式主動使用相片/攝影機，HoloLens (第 1 代) 將無法即時串流。
>   * 當應用程式嘗試以 ExclusiveControl 模式存取相片/攝影機時，HoloLens 2 會自動停止即時串流。
>   * 當應用程式主動使用 PV 相機時，HoloLens 2 可以啟動即時串流。

### <a name="performance-tracing"></a>效能追蹤

![Microsoft HoloLens 上 Windows 裝置入口網站的效能追蹤頁面](images/using-windows-portal-img-08.png)<br>
*Microsoft HoloLens 上 Windows 裝置入口網站的效能追蹤頁面*

從您的 HoloLens 擷取 [Windows Performance Recorder](/previous-versions/windows/it-pro/windows-8.1-and-8/hh448205(v=win.10)) (WPR) 追蹤。
* **可用的設定檔**：從下拉式清單選取 WPR 設定檔，然後選取或點選 [開始] 以開始追蹤。
* **自訂設定檔**：選取或點選 [瀏覽]，以從您的電腦選擇 WPR 設定檔。 選取或點選 [上傳並開始] 以開始追蹤。

若要停止追蹤，請選取 [停止] 連結。 留在此頁面上，直到追蹤檔案下載完成。

擷取的 ETL 檔案可以在 [Windows Performance Analyzer](/previous-versions/windows/it-pro/windows-8.1-and-8/hh448170(v=win.10)) 中開啟以進行分析。

### <a name="processes"></a>處理程序

![Microsoft HoloLens 上 Windows 裝置入口網站中的程序頁面](images/using-windows-portal-img-09.png)<br>
*Microsoft HoloLens 上 Windows 裝置入口網站中的程序頁面*

顯示有關目前正在執行之處理程序的詳細資訊。 這包括 App 與系統處理程序。

### <a name="system-performance"></a>系統效能

![Microsoft HoloLens 上 Windows 裝置入口網站中的系統效能頁面](images/using-windows-portal-img-10.png)<br>
*Microsoft HoloLens 上 Windows 裝置入口網站中的系統效能頁面*

顯示系統診斷資訊的即時圖表，例如電源使用量、畫面播放速率與 CPU 負載。

下列為可用的衡量標準：
* **SoC 電源**：系統單晶片電源瞬間使用量 (一分鐘內的平均值)
* **系統電源**：系統電源瞬間使用量 (一分鐘內的平均值)
* **畫面播放速率**：每秒畫面格數、每秒遺失的 VBlanks 數，以及連續遺失的 VBlanks 數
* **GPU**：GPU 引擎使用量、可用總計的百分比
* **CPU**︰可用總計的百分比
* **I/O**：讀取與寫入
* **網路**：已接收與已傳送
* **記憶體**：總計、使用中、已認可的、分頁與非分頁

### <a name="apps"></a>[App]

![Microsoft HoloLens 上 Windows 裝置入口網站的應用程式頁面](images/using-windows-portal-img-11.png)<br>
*Microsoft HoloLens 上 Windows 裝置入口網站的應用程式頁面*

管理安裝在 HoloLens 上的應用程式。
* **已安裝的應用程式**：移除並啟動應用程式。
* **執行中應用程式**：列出目前執行中的應用程式。
* **安裝應用程式**：從電腦/網路上的資料夾，選取安裝的應用程式套件。
* **相依性**：新增所要安裝應用程式的相依性。
* **部署**：將選取的應用程式 + 相依性部署至 HoloLens。

### <a name="app-crash-dumps"></a>應用程式損毀傾印頁面

![Microsoft HoloLens 上 Windows 裝置入口網站的應用程式損毀傾印頁面](images/using-windows-portal-img-12.png)<br>
*Microsoft HoloLens 上 Windows 裝置入口網站的應用程式損毀傾印頁面*

此頁面可讓您收集側載 App 的損毀傾印。 請針對您想要收集損毀傾印的應用程式，選取其 [啟用的損毀傾印] 核取方塊。 返回此頁面以收集損毀傾印。 傾印檔案可以在 [Visual Studio 中開啟以進行偵錯](/previous-versions/visualstudio/visual-studio-2015/debugger/using-dump-files)。

### <a name="file-explorer"></a>檔案總管

![Microsoft HoloLens 上 Windows 裝置入口網站的檔案總管頁面](images/using-windows-portal-img-13.png)<br>
*Microsoft HoloLens 上 Windows 裝置入口網站的檔案總管頁面*

使用檔案總管來瀏覽、上傳和下載檔案。 您可以針對從 Visual Studio 或裝置入口網站部署的應用程式，使用 [文件] 資料夾、[圖片] 資料夾和 [本機儲存體] 資料夾中的檔案。

### <a name="kiosk-mode"></a>Kiosk 模式

>[!NOTE]
>Kiosk 模式僅適用於 [Microsoft HoloLens Commercial Suite](/hololens/hololens-commercial-features)。

![Microsoft HoloLens 上的 Windows 裝置入口網站中的 Kiosk 模式頁面](images/using-windows-portal-img-14.png)

如需透過 Windows 裝置入口網站啟用 Kiosk 模式的最新指示，請參閱 Windows IT Pro 中心的[以 Kiosk 模式設定 HoloLens](/hololens/hololens-kiosk#set-up-kiosk-mode-using-the-windows-device-portal-windows-10-version-1607-and-version-1803) 文章。

### <a name="logging"></a>記錄

![Microsoft HoloLens 上 Windows 裝置入口網站的記錄頁面](images/using-windows-portal-img-15.png)<br>
*Microsoft HoloLens 上 Windows 裝置入口網站的記錄頁面*

管理 HoloLens 上的即時 Windows 事件追蹤 (ETW)。

選取 [隱藏提供者]，以只顯示 [事件] 清單。
* **已註冊的提供者**：選取 ETW 提供者與追蹤層級。 追蹤等級是下列其中一個值 ︰
   1. 異常結束或終止
   2. 嚴重錯誤
   3. 警告
   4. 非錯誤警告

選取或點選 [啟用] 以開始追蹤。 提供者已新增到 [啟用的提供者] 下拉式清單中。
* **自訂提供者**：選取自訂 ETW 提供者與追蹤層級。 依 GUID 識別提供者。 不要在 GUID 中包含括號。
* **啟用的提供者**：列出已啟用的提供者。 從下拉式清單選取提供者，然後按一下或點選 [停用] 以停止追蹤。 按一下或點選 [全部停止] 以暫停所有追蹤。
* **提供者歷程記錄**：顯示目前工作階段期間已啟用的 ETW 提供者。 按一下或點選 [啟用] 以啟用已停用的提供者。 按一下或點選 [清除] 以清除歷程記錄。
* **事件**：以表格格式列出所選提供者的 ETW 事件。 此表格會即時更新。 在表格下方，按一下 [清除] 按鈕，以刪除表格中的所有 ETW 事件。 這不會停用任何提供者。 您可以按一下 [儲存到檔案]，在本機將目前收集的 ETW 事件匯出到 CSV 檔案。
* **篩選**：可讓您篩選由識別碼、關鍵字、層級、提供者名稱、工作名稱或文字所收集的 ETW 事件。 您可以將數個準則結合在一起：
   1. 針對套用至相同屬性的準則，會顯示可滿足任一準則的事件。
   2. 針對套用至不同屬性的準則，事件必須滿足所有準則

例如，您可以指定準則 *(工作名稱包含 'Foo' 或 'Bar') AND (文字包含 'error' 或 'warning')*

### <a name="simulation"></a>模擬

![Microsoft HoloLens 上 Windows 裝置入口網站的模擬頁面](images/using-windows-portal-img-16.png)<br>
*Microsoft HoloLens 上 Windows 裝置入口網站的模擬頁面*

允許您記錄並播放輸入資料以進行測試。
* **擷取房間**：用來下載模擬的房間檔案，其中包含針對使用者周遭環境的空間對應網格。 為房間命名，然後按一下 [擷取] 來將資料在您的電腦上儲存為 .xef 檔案。 此房間檔案可以載入 HoloLens 模擬器。
* **錄製**：檢查要錄製的串流、為錄製命名，然後按一下或點選 [錄製] 開始錄製。 使用您的 HoloLens 執行動作，然後按一下 [停止] 來將資料在您的電腦上儲存為 .xef 檔案。 此檔案可以載入 HoloLens 模擬器或裝置。
  >[!NOTE]
  >錄製功能目前僅適用于 HoloLens 第1代。 HoloLens 2 尚不支援錄製，但支援播放現有錄製。
* **播放**：按一下或點選 [上傳錄製]，從電腦中選取 xef 檔案，並將資料傳送到 HoloLens。
* **控制模式**：從下拉式清單中選取 [預設] 或 [模擬]，然後按一下或點選 [設定] 按鈕來選取 HoloLens 上的模式。 選擇 [模擬] 將會停用 HoloLens 上實際的感應器，並改為使用已上傳的模擬資料。 如果您切換到 [模擬]，您的 HoloLens 不會對真實使用者做出回應，直到您切換回 [預設] 為止。

### <a name="networking"></a>網路功能

![Microsoft HoloLens 上 Windows 裝置入口網站的網路功能頁面](images/using-windows-portal-img-17.png)<br>
*Microsoft HoloLens 上 Windows 裝置入口網站的網路功能頁面*

管理 HoloLens 上的 Wi-Fi 連線。
* **WiFi 介面卡**：使用下拉式清單控制項選取 Wi-Fi 介面卡和設定檔。 按一下或點擊 [連線] 以使用選取的介面卡。
* **可用網路**：列出 HoloLens 可以連線的 Wi-Fi 網路。 按一下或點選 [重新整理] 以更新清單。
* **IP 設定**：顯示網路連線的 IP 位址和其他詳細資料。

### <a name="virtual-input"></a>虛擬輸入

![Microsoft HoloLens 上 Windows 裝置入口網站的虛擬輸入頁面](images/using-windows-portal-img-18.png)<br>
*Microsoft HoloLens 上 Windows 裝置入口網站的虛擬輸入頁面*

從遠端電腦傳送鍵盤輸入到 HoloLens。

按一下或點選 [虛擬鍵盤] 下方的區域，來啟用傳送按鍵輸入到 HoloLens。 在 [輸入文字] 文字方塊中輸入，然後按一下或點選 [傳送]，將按鍵輸入傳送到使用中的應用程式。

## <a name="device-portal-rest-apis"></a>裝置入口網站 REST API

裝置入口網站中所有的項目都是以 [REST API](device-portal-api-reference.md) (可選擇性地讓您用來存取資料，並以程式設計方式控制裝置) 為基礎所建置。

## <a name="troubleshooting"></a>疑難排解

### <a name="how-to-fix-the-its-lonely-here-message"></a>如何修正「此處暫無任何項目」訊息

> [!NOTE]
> 如果在 Hololens 2 上使用之前在 HoloLens (第一代) 上使用，則從 HoloLens 2 移轉到 HoloLens (第一代) 可能會導致頁面變得空無一物。

![裝置入口網站頁面中的「此處暫無任何項目」訊息](images/using-windows-portal-img-19.png)

1. 從左上角的功能表中，選取 [重設版面配置]：

![從裝置入口網站功能表中，選取 [重設版面配置]](images/using-windows-portal-img-20.png)

2. 按一下 [重設工作區] 標題下的 [重設版面配置]。 入口網站頁面會自動重新整理並顯示您的內容。

![從 [重設工作區] 頁面選取 [重設版面配置]](images/using-windows-portal-img-21.png)
