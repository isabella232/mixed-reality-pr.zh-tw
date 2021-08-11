---
title: 版本資訊-2018 年4月
description: 隨時掌握 HoloLens 的最新版本，並 Windows Mixed Reality Windows 10 四月 2018/RS4 Update 的版本資訊。
author: mattzmsft
ms.author: mazeller
ms.date: 05/21/2018
ms.topic: article
keywords: 版本資訊、版本、windows 10、組建、rs4、os
ms.openlocfilehash: 27f80d659c63362191a80eeae973111ca342090901c243772868d1a7c11e24d3
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2021
ms.locfileid: "115202430"
---
# <a name="release-notes---april-2018"></a>版本資訊-2018 年4月

**[Windows 10 2018 年4月的更新](https://blogs.windows.com/windowsexperience/2018/04/30/whats-new-in-the-windows-10-april-2018-update)** (也稱為 RS4) 包括與電腦連線 HoloLens 和 Windows Mixed Reality 沉浸式耳機的新功能。 

若要更新為任一裝置類型的最新版本，請開啟 **設定** 應用程式，移至 [**更新 & 安全性**]，然後選取 [**檢查更新**] 按鈕。 在 Windows 10 的電腦上，您也可以使用[Windows 媒體建立工具](https://www.microsoft.com/software-download/windows10)，手動安裝 Windows 10 2018 年4月更新。

**適用于桌面的最新版本：** Windows 10 2018 年4月更新 (**10.0.17134.1**) <br>
**HoloLens 的最新版本：** Windows 10 2018 年4月更新 (**10.0.17134.80**) <br>
<br>

>[!VIDEO https://www.youtube.com/embed/O-84oWjSbr0]

*Alex 2018 年4月更新 Windows 10 中的新混合現實功能 Kipman 和總覽的訊息*

## <a name="new-features-for-windows-mixed-reality-immersive-headsets"></a>Windows Mixed Reality 沉浸式耳機的新功能

Windows 10 2018 年4月更新包含許多對桌上型電腦使用 Windows Mixed Reality 沉浸式 (VR) 耳機的增強功能，例如： 

* **混合實境首頁的新環境**-選取 [[開始] 功能表上的 **位置**，在懸崖之屋和新的 Skyloft 環境之間選擇。 我們也新增 [了實驗性功能](/windows/mixed-reality/design/add-custom-home-environments) ，可讓您使用您所建立的自訂環境。
* **快速存取混合的現實 capture** -使用跨環境和應用程式的動作控制器來取得混合的現實相片，但不會捕捉受 DRM 保護的內容。 按住 Windows 按鈕，然後點擊觸發程式。 .
* **啟動和調整大小內容的新選項**：當您從 [開始] 功能表啟動應用程式時，現在會自動將應用程式放在您的前方。 您現在也可以拖曳視窗的邊緣和角落來調整2D 應用程式的大小。
* **使用「傳送」聲音命令輕鬆跳到內容**-透過撥雲見日內容並說「傳送」來快速地在 Windows Mixed Reality 首頁中的內容上傳送。
* **混合實境首頁的 [動畫3d 應用程式啟動器](/windows/mixed-reality/distribute/creating-3d-models-for-use-in-the-windows-mixed-reality-home#animation-guidelines)和 [裝飾性3d 物件](/windows/mixed-reality/distribute/enable-placement-of-3d-models-in-the-home)**。 您現在可以將動畫新增至3d 應用程式啟動器，並允許使用者將裝飾性3d 模型從網頁或2d 應用程式放入 Windows Mixed Reality 首頁。
* 適用于 SteamVR 的 **[Windows Mixed Reality 的改善](/windows/mixed-reality/develop/porting-apps/updating-your-steamvr-application-for-windows-mixed-reality)**，在新的升級時不會有「早期存取」，包括：使用動作控制器時 haptic Windows Mixed Reality 的意見反應、改善的效能和可靠性，以及 SteamVR 中的動作控制器外觀改善。
* **其他改進** -更新的自動效能設定可提供更優化的體驗 (您可以 [手動覆寫](#visual-quality) 此設定) 。 安裝程式現在提供 USB 3.0 控制器和圖形配接器常見相容性問題的詳細資訊。

## <a name="new-features-for-hololens"></a>HoloLens 的新功能

Windows 10 2018 年4月更新已抵達所有 HoloLens 客戶！ 此更新已封裝在[2016 年8月](release-notes-august-2016.md)HoloLens 軟體的最後一個主要版本之後引進的改進。

### <a name="for-everyone"></a>適用于每個人

<table>
  <tr>
    <th>功能</th><th>詳細資料</th><th>指示</th>
  </tr>
  <tr>
    <td>啟動時自動放置2D 和3D 內容</td><td>當您啟動2D 應用程式啟動器或 2D UWP 應用程式時，會以最佳的大小和距離在世界各地自動放置，而不需要使用者進行放置。 如果 <a href="/windows/mixed-reality/design/app-views">沉浸式應用程式</a> 使用2d 應用程式啟動程式，而不是使用 <a href="/windows/mixed-reality/distribute/3d-app-launcher-design-guidance">3d 應用程式啟動</a>程式，則沉浸式應用程式會從2d 應用程式啟動程式自動啟動，與 RS1 中的相同。<br><br>[開始] 功能表中的3d 應用程式啟動程式也會自動放在世界各地。 使用者可以按一下啟動器以啟動沉浸式應用程式，而不是自動啟動應用程式。 從全像投影應用程式和邊緣開啟的3d 內容也會自動放在世界各地。</td><td>從 [開始] 功能表開啟應用程式時，系統不會要求您將它放在世界中。<br><br>如果2D 應用程式/<a href="/windows/mixed-reality/distribute/3d-app-launcher-design-guidance">3d 應用程式啟動器</a> 放置位置不是最佳的，您可以使用以下所述的新的流暢應用程式操作輕鬆地移動它們。 您也可以藉由說出「移動這個」，然後使用「注視」來重新放置內容，來重新調整2D 應用程式啟動器/3D 內容的位置。</td>
  </tr>
  <tr>
    <td>流體應用程式操作</td><td>移動、調整大小和旋轉2D 和3D 內容，而不需要輸入「調整」模式。</td><td>若要移動 2D UWP 應用程式或2D 應用程式啟動器，只要看看它的應用程式行，然後使用點按 + 按住 + 拖曳手勢。 您可以撥雲見日物件上的任何位置來移動3D 內容，然後使用點按 + 按住 + 拖曳。<br><br>若要調整2D 內容的大小，請在其角落。 注視游標會變成調整大小游標，然後您可以按下 + 按住 + 拖曳以調整大小。 您也可以藉由查看邊緣和拖曳的方式，讓2D 內容變成高度或更寬。<br><br>若要調整3D 內容的大小，請將您的手抬起到手勢框架中，並在就緒的位置中向上手指。 您會看到資料指標變成有2個小手的狀態。 無論您的手，都能用兩個手勢來按住手勢。 將您的手移到更接近或更遠的變更物件的大小。 將您的手向前和向後移動彼此之間的關聯，將會旋轉物件。 您也可以透過這種方式來調整或旋轉2D 內容。</td>
  </tr>
  <tr>
    <td>使用重排進行2D 應用程式水準調整大小</td><td>讓 2D UWP 應用程式更寬的外觀比例，以查看更多應用程式內容。 例如，讓郵件應用程式夠寬，以顯示預覽窗格。</td><td>只要注視 2D UWP 應用程式的左邊緣或右邊緣，即可看到調整大小游標，然後使用點按 + 按住 + 拖曳手勢來調整大小。</td>
  </tr>
  <tr>
    <td>展開的語音命令支援</td><td>只要使用您的聲音就可以了。</td><td>請嘗試下列語音命令：<ul><li>「移至開始」-帶出 [開始] 功能表，或離開<a href="/windows/mixed-reality/design/app-views">沉浸式應用程式</a>。</li><li>"Move this"-可讓您移動物件。</li></ul></td>
  </tr>
  <tr>
    <td>更新全像投影和相片應用程式</td><td>使用新的全像是更新全像投影應用程式。 更新的相片應用程式。</td><td>您將會注意到全像投影和相片應用程式已更新的外觀。 全像投影應用程式包含數個新的全像投影和標籤製作程式，可讓您更輕鬆地建立文字。</td>
  </tr>
  <tr>
    <td>改良的混合現實捕獲</td><td>硬體快捷方式開始和結束 MRC 影片。</td><td>將音量向上 + 向下，3秒即可開始錄製 MRC 影片。 再次點擊，或使用 bloom 手勢結束。</td>
  </tr>
  <tr>
    <td>合併的空格</td><td>簡化將磁碟空間管理到單一空間的空間管理。</td><td>HoloLens 會自動尋找您的空間，而且不再需要您管理或選取空格。 如果您有關于您的全像投影問題，您可以移至<b>設定 > 系統 > 全像投影 > 移除鄰近</b>的全像投影。 如有需要，您也可以選取 [ <b>移除所有的全</b>像]。</td>
  </tr>
  <tr>
    <td>改良的音訊深度</td><td>您現在可以在雜訊環境中聽到 HoloLens 更好的音效，並從應用程式體驗更逼真的音效，因為裝置偵測到的真實牆會遮蔽音效。</td><td>您不必做任何事來享受改良的空間音效。</td>
  </tr>
  <tr>
    <td>檔案總管</td><td>從 HoloLens 內移動和刪除檔案。</td><td>您可以使用<b>檔案總管</b>應用程式來移動和刪除 HoloLens 內的檔案。<br><br><b>秘訣：</b> 如果您沒有看到任何檔案，則 [最近] 篩選可能會在左窗格中反白顯示 (時鐘圖示) 。 若要修正，請選取 </b> 左窗格中的 [此裝置檔] 圖示 (時鐘圖示) 下方，或開啟功能表並選取 <b>此裝置</b>。
</td>
  </tr>
  <tr>
    <td>MTP (媒體傳輸通訊協定) 支援</td><td>可讓您的桌上型電腦存取您的媒體櫃 (相片、影片、檔) HoloLens 以方便傳輸。</td><td>類似于其他行動裝置，請將您的 HoloLens 連接到您的電腦，以顯示<b>檔案總管</b>來存取 HoloLens 程式庫 (相片、影片、檔) 方便傳送。<br><br><b>祕訣：</b><ul><li>如果您沒有看到任何檔案，請確定您已登入 HoloLens，以啟用資料的存取權。</li><li>從電腦上的<b>檔案總管</b>，您可以選取<b>裝置屬性</b>，以查看 Windows 的全像作業系統版本號碼 (的) 和裝置序號。</li></ul><b>已知問題：</b>未啟用在電腦上透過<b>檔案總管</b>重新命名 HoloLens。</td>
  </tr>
  <tr>
    <td>安裝期間的驗證入口網站網路支援</td><td>您現在可以在旅館、會議中心、零售商店或使用網頁驗證入口網站的公司的來賓網路上設定 HoloLens。</td><td>在安裝期間，選取 [網路]，然後選取 [自動連線]，然後在出現提示時輸入網路資訊。</td>
  </tr>
  <tr>
    <td>透過 OneDrive 應用程式的相片和影片同步</td><td>HoloLens 的相片和影片現在會從 Microsoft Store （而不是相片應用程式）透過 OneDrive 應用程式進行同步處理。</td><td>若要進行此設定，請從存放區下載並啟動 OneDrive 應用程式。 第一次執行時，系統會提示您自動上傳您的相片以 OneDrive。 如果未出現此提示，您可以在應用程式設定中找到選項。</td>
  </tr>
</table>

### <a name="for-developers"></a>開發人員

<table>
  <tr>
    <th>功能</th><th>詳細資料</th><th>指示</th>
  </tr>
  <tr>
    <td>空間對應改進</td><td>品質、簡化和效能改進。</td><td>空間對應網格會顯示為簡潔，需要較少的三角形來代表相同層級的詳細資料。 您可能會注意到場景中的三角形密度有所變更。</td>
  </tr>
  <tr>
    <td>根據深度緩衝區自動選取焦點點</td><td>提交深度緩衝區至 Windows 可讓 HoloLens 自動選取焦點點，以優化全像全像</td><td>在 Unity 中，移至 [<b>編輯] > Project 設定 > 播放機] > 通用 Windows 平臺索引標籤 > XR 設定</b>，展開 [ <b>Windows Mixed Reality SDK</b> ] 專案，然後選取 [<b>啟用深度緩衝區共用</b>]。 系統會自動檢查是否有新專案。<br><br>針對 DirectX 應用程式，請務必在<b>HolographicRenderingParameters</b>每個畫面上呼叫<a href="/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer">CommitDirect3D11DepthBuffer</a>方法，以提供 Windows 的深度緩衝區。
</td>
  </tr>
  <tr>
    <td>全像 reprojection 模式</td><td>您現在可以停用 HoloLens 上的位置 reprojection，以改善最嚴格的主體鎖定內容（例如360度的影片）的全像影像穩定性。</td><td>在 Unity 中，當 view 中的所有內容都是嚴格的主體鎖定時，將 <a href="https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.ReprojectionMode.html">HolographicSettings. ReprojectionMode</a> 設定為 <a href="https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.HolographicReprojectionMode.html">HolographicReprojectionMode. OrientationOnly</a> 。<br><br>針對 DirectX 應用程式，當 view 中的所有內容都是嚴格的主體鎖定時，將 <a href="/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.reprojectionmode"> HolographicCameraRenderingParameters ReprojectionMode</a> 設定為 <a href="/uwp/api/windows.graphics.holographic.holographicreprojectionmode">HolographicReprojectionMode. OrientationOnly</a> 。</td>
  </tr>
  <tr>
    <td>應用程式量身打造 Api</td><td>Windowsapi 可深入瞭解您的應用程式執行所在的位置，例如裝置的顯示器是否為透明的 (HoloLens) 或不透明 (沉浸式耳機) ，以及 UWP 應用程式的2d 視圖是否顯示在全像攝影介面中。</td><td>Unity 先前以手動方式公開了 <a href="https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.IsDisplayOpaque.html">HolographicSettings</a> ，甚至是在此組建之前都能運作的方式。<br><br>針對 DirectX 應用程式，您現在可以存取現有的 Api，例如<a href="/uwp/api/windows.graphics.holographic.holographicdisplay.isopaque">HolographicDisplay. GetDefault () 。</a>HoloLens 上的 IsOpaque 和<a href="/uwp/api/windows.applicationmodel.preview.holographic.holographicapplicationpreview.iscurrentviewpresentedonholographicdisplay">HolographicApplicationPreview。</a>
</td>
  </tr>
  <tr>
      <td>研究模式</td><td>可讓開發人員在建立學術和產業應用程式時，存取金鑰 HoloLens 感應器，以測試電腦視覺和機器人領域中的新想法，包括：<ul><li>四個環境追蹤攝影機</li><li>深度對應相機資料的兩個版本</li><li>IR 反射率串流的兩個版本</li></ul></td><td><a href="/windows/mixed-reality/develop/platform-capabilities-and-apis/research-mode">研究模式檔</a><br><a href="https://github.com/Microsoft/HoloLensForCV">研究模式範例應用程式</a></td>
  </tr>
</table>

### <a name="for-commercial-customers"></a>適用于商業客戶

<table>
  <tr>
    <th>功能</th><th>詳細資料</th><th>指示</th>
  </tr>
  <tr>
    <td>在單一裝置上使用多個 Azure Active Directory 使用者帳戶</td><td>與多個 Azure AD 使用者共用 HoloLens，每個使用者都有自己的使用者設定和裝置上的使用者資料。</td><td><a href="/hololens/hololens-multiple-users">IT Pro 中心：與多人共用 HoloLens</a></td>
  </tr>
  <tr>
    <td>變更登入時 Wi-Fi 網路</td><td>先變更 Wi-Fi 網路再登入，讓另一位使用者第一次登入自己的 Azure AD 使用者帳戶，讓使用者能夠在不同的位置和工作地點共用裝置。</td><td>在登入畫面上，您可以使用 [密碼] 欄位底下的 [網路] 圖示來連線至網路。 當您第一次登入裝置時，這會很有説明。</td>
  </tr>
  <tr>
    <td>整合註冊</td><td>您現在可以輕鬆地使用個人 Microsoft 帳戶來設定裝置的 HoloLens 使用者，以新增工作帳戶 (Azure AD) 並將裝置加入其 MDM 伺服器。</td><td>使用 Azure AD 帳戶登入，註冊會自動進行。</td>
  </tr>
  <tr>
    <td>沒有 MDM 註冊的郵件同步</td><td>支援 Exchange Active Sync (EAS) mail 同步，而不需要 MDM 註冊。</td><td>您現在可以同步電子郵件，而不需要在 MDM 中註冊。 您可以使用 Microsoft 帳戶設定裝置、下載及安裝郵件應用程式，以及直接新增工作電子郵件帳戶。</td>
  </tr>
</table>

### <a name="for-it-pros"></a>適用於 IT 專業人員

<table>
  <tr>
    <th>功能</th><th>詳細資料</th><th>指示</th>
  </tr>
  <tr>
    <td>新的 "Windows Holographic for Business" OS 名稱</td><td>清除版本命名，以在 HoloLens 上啟用商用套件功能時，減少版本升級授權應用程式的混淆。</td><td>您可以在<b>設定 > 系統 ></b>，查看裝置上的 Windows 全像的版本。 如果已套用版本更新以啟用商業套件功能，則會出現「Windows Holographic for Business」。 瞭解如何<a href="/hololens/hololens-upgrade-enterprise">解除鎖定 Windows Holographic for Business 功能</a>。</td>
  </tr>
  <tr>
  <td>WindowsConfiguration Designer (WCD) </td><td>建立和編輯布建套件，以透過更新的 WCD 應用程式設定 HoloLens。 適用于版本更新、可設定的 OOBE、區域/時區、大量 Azure AD 權杖、網路和開發人員 CSP 的簡單 HoloLens wizard。 Advanced editor 已篩選成 HoloLens 支援的選項，包括指派的存取和帳戶管理 csp。</td><td><a href="/hololens/hololens-provisioning">IT Pro 中心：使用布建套件設定 HoloLens</a></td>
  </tr>
  <tr>
    <td>可設定的設定 (OOBE) </td><td>在安裝期間隱藏校正、手勢/注視訓練和 Wi-Fi 設定畫面。</td><td><a href="/hololens/hololens-provisioning#create-a-provisioning-package-for-hololens-using-the-hololens-wizard">IT Pro 中心：使用布建套件設定 HoloLens</a></td>
  </tr>
  <tr>
    <td>大量 Azure AD 權杖支援</td><td>預先註冊裝置至 Azure AD directory 租使用者，以加快使用者設定流程的速度。</td><td><a href="/hololens/hololens-provisioning">IT Pro 中心：使用布建套件設定 HoloLens</a></td>
  </tr>
  <tr>
  <td>DeveloperSetup CSP</td><td>部署設定檔，以在開發人員模式中設定 HoloLens。 適用于開發和示範裝置。</td><td><a href="/hololens/hololens-provisioning">IT Pro 中心：使用布建套件設定 HoloLens</a></td>
  </tr>
  <tr>
  <td>AccountManagement CSP</td><td>共用 HoloLens 裝置，並在登出或無活動/儲存閾值之後，移除暫時使用的使用者資料。 支援 Azure AD 帳戶。</td><td><a href="/hololens/hololens-provisioning">IT Pro 中心：使用布建套件設定 HoloLens</a></td>
  </tr>
  <tr>
  <td>受指派的存取權</td><td>針對第一行工作者或示範 Windows 指派的存取權。 單一或多個應用程式鎖定。 不需要開發人員解除鎖定。</td><td><a href="/hololens/hololens-kiosk">IT Pro Center：在 kiosk 模式中設定 HoloLens</a></td>
  </tr>
  <tr>
  <td>Kiosk 裝置的來賓存取權</td><td>使用無密碼的來賓帳戶 Windows 指派的存取權，以供示範之用。 單一或多個應用程式鎖定。 不需要開發人員解除鎖定。</td><td><a href="/hololens/hololens-kiosk#guest">IT Pro Center：在 kiosk 模式中設定 HoloLens</a></td>
  </tr>
  <tr>
    <td>設定 (OOBE) 診斷</td><td>從 HoloLens 取得診斷記錄，以便在登入失敗) 的使用者可以使用意見反應中樞之前，對 Azure AD 登入失敗進行疑難排解 (。</td><td>當安裝或登入失敗時，請選擇 [新增 <b>收集資訊</b> ] 選項來取得診斷記錄以進行疑難排解。</td>
  </tr>
  <tr>
    <td>本機帳戶不定密碼到期</td><td>移除本機帳戶密碼過期時，裝置重設中斷的情形。</td><td>布建本機帳戶時，您不再需要在<b>設定</b>中每42天變更密碼，因為帳戶密碼不再過期。</td>
  </tr>
  <tr>
    <td>MDM 同步狀態和詳細資料</td><td>標準 Windows 功能，可瞭解 HoloLens 內的 MDM 同步狀態和詳細資料。</td><td>您可以在設定 > 帳戶中檢查裝置的 MDM 同步狀態<b>> 存取公司或學校 > 資訊</b>。 在 [ <b> 裝置同步狀態] <b> 區段中，您可以開始同步處理、查看由 MDM 管理的區域，以及建立和匯出高階診斷報告。</td>
  </tr>
</table>

## <a name="known-issues"></a>已知問題

我們努力提供絕佳的 Windows Mixed Reality 經驗，但仍在追蹤一些已知問題。 如果您發現其他人，請 [提供意見反應給我們](/windows/mixed-reality/give-us-feedback)。

### <a name="hololens"></a>HoloLens

#### <a name="after-update"></a>更新之後

從 RS1 更新至 RS4 之後，您可能會注意到您的 HoloLens 上的下列問題：
* **pin 重設**-釘選到您 [開始] 功能表的3x3 應用程式將會在更新之後重設為預設值。 
* **應用程式和已放置** 的全像調整大小調整應用程式會在更新之後移除，而且必須在整個空間中重新放置。 
* **意見反應中樞可能不會立即啟動** -在更新之後，需要幾分鐘的時間，您才能啟動一些像是意見反應中樞的收件匣應用程式，而這些應用程式會自行更新。 
* **公司 Wi-Fi 憑證需要重新同步** 處理-我們正在調查需要將 HoloLens 連線到不同網路的問題，才能讓公司憑證重新同步至裝置，然後才能使用憑證重新連接到公司網路。 
* **H. HEVC 影片播放無法運作** -嘗試播放 h. 的應用程式將會收到錯誤訊息。 因應措施是 [存取 Windows 裝置入口網站](/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-windows-device-portal)，選取左側導覽列上的 [**應用** 程式]，然後 **移除** HEVC 應用程式。 然後，從 Microsoft Store 安裝最新的[HEVC 視訊延伸模組](https://www.microsoft.com/p/hevc-video-extensions/9nmzlz57r3t7)。 我們正在調查此問題。 

#### <a name="for-developers-updating-hololens-apps-for-devices-running-windows-10-april-2018-update"></a>適用于開發人員：更新執行 Windows 10 2018 年4月更新之裝置的 HoloLens 應用程式

除了一份絕佳的[新功能](#new-features-for-hololens)清單之外，Windows 10 2018 年4月更新 (RS4) 的 HoloLens 會強制執行先前版本沒有的一些程式程式碼為：
* 在 HoloLens 上 **使用敏感性資源 (相機、麥克風等等) RS4 的許可權要求**，將會對要存取敏感資源的應用程式（例如相機或麥克風）強制執行許可權要求。 RS1 on HoloLens 不會強制執行這些提示，因此，如果您的應用程式會立即存取這些資源，即使使用者將許可權授與要求的資源) ，也可能會在 RS4 (中損毀。 如需詳細資訊，請參閱相關的 [UWP 應用程式功能聲明文章](/windows/uwp/packaging/app-capability-declarations) 。
* 對 HoloLens 的 **外部應用程式進行呼叫**，將會強制適當地使用 [ *Windows.System。 Launcher* 類別](/uwp/api/Windows.System.Launcher)可自行啟動另一個應用程式。 例如，我們發現呼叫Windows.System 的應用程式有問題。 *Launcher。* 從非 ASTA (UI) 執行緒中 LaunchUriForResultsAsync。 在 HoloLens 上的 RS1 會成功，但是 RS4 需要在 UI 執行緒上執行呼叫。

### <a name="windows-mixed-reality-on-desktop"></a>桌面上的 Windows Mixed Reality

#### <a name="visual-quality"></a>視覺品質

* 如果您在2018年4月更新 Windows 10 後發現圖形比之前更清楚，或視野的欄位在您的耳機上變得較小，則可能已變更自動效能設定，以在較不強大的圖形 (配接器上維持足夠的畫面播放速率，例如 Nvidia 1050) 。 您可以手動覆寫此 (，如果您選擇) ，請流覽至 **設定 > 混合現實 > 耳機顯示**> [體驗] 選項 > 變更並將 [自動] 變更為 [90 Hz]。 您也可以嘗試將相同設定頁面上的 **視覺品質** (變更) 為「高」。

#### <a name="windows-mixed-reality-setup"></a>Windows Mixed Reality 設定

* 設定連接耳機的 Windows 時，您的電腦監視器可能會空白。 拔掉耳機以啟用電腦監視器的輸出，以完成 Windows 設定。
* 如果您沒有連接耳機，您可能會在第一次造訪 Windows Mixed Reality 首頁時錯過提示。
* 其他藍牙裝置可能會造成與移動控制器的干擾。 如果移動控制器有連線/配對/追蹤問題，請確定藍牙的無線電 (如果外部的轉換器) 插入到未阻擋的位置，而不是緊接在另一個藍牙的轉換器旁。 也請嘗試在 Windows Mixed Reality 會話期間關閉其他藍牙週邊設備，以查看其是否有説明。

#### <a name="games-and-apps-from-the-microsoft-store"></a>Microsoft Store 的遊戲和應用程式

* 有些以圖形化的方式，像是 Forza Motorsport 7 一樣，在 Windows Mixed Reality 內播放時，可能會造成效能問題在支援較低的電腦上。

#### <a name="audio"></a>音訊

* 如果您在使用 Windows Mixed Reality 耳機之前，在主機電腦上啟用 Cortana，您可能會遺失將空間音效模擬套用至您在 Windows Mixed Reality home 周圍所放置的應用程式。 
   * 解決辦法是在所有連接到您電腦的音訊裝置上啟用「耳機用 Windows Sonic」，即使是連接耳機的音訊裝置也是一樣：
      1. 以滑鼠左鍵按一下桌面工作列上的喇叭圖示，然後從音訊裝置清單中選取。
      2. 以滑鼠右鍵按一下桌面工作列上的喇叭圖示，然後在 [喇叭設定] 功能表中選取 [耳機用 Windows Sonic]。
      3. 針對 (端點) 的所有音訊裝置重複這些步驟。
   * 另一個選項是在啟動 Windows Mixed Reality 之前，關閉桌面 **設定** Cortana 中的「讓 Cortana 回應嗨 Cortana」  >   。
* 當另一個多媒體 usb 裝置 (（例如網路凸輪）) 與 Windows Mixed Reality 耳機共用相同的 usb 集線器)  (，在罕見的情況下，耳機的音訊插孔/耳機可能會有噪音音效或完全沒有音訊。 您可以將耳機修正為沒有與其他裝置共用相同中樞的 USB 埠，或中斷連接/停用其他 USB 多媒體裝置。
* 在罕見的情況下，主機電腦的 USB 集線器無法提供足夠的電源給 Windows Mixed Reality 耳機，您可能會注意到連接到耳機的耳機有突然的雜訊。

#### <a name="holograms"></a>全像投影

* 如果您在 Windows Mixed Reality 首頁中放入大量的全像投影，有些可能會在您的情況下消失並重新顯示。 若要避免這種情況，請移除 Windows Mixed Reality home 的該區域中的一些全息。

#### <a name="motion-controllers"></a>運動控制器

* 如果未將輸入路由傳送到耳機，移動控制器將會在房間界限的旁邊保留時短暫消失。 按 Win + Y 以確保桌面監視器上有藍色橫幅可解決此問題。 
* 有時候，當您在 Microsoft Edge 中按一下網頁時，內容將會縮放，而不是按下。

#### <a name="desktop-app-in-the-windows-mixed-reality-home"></a>Windows Mixed Reality 首頁中的桌面應用程式

* 剪取工具不適用於桌面應用程式。
* 桌面應用程式在重新開機時不會保存設定。
* 如果您在桌上型電腦上使用混合實境入口預覽版，在 Windows Mixed Reality 首頁中開啟桌面應用程式時，您可能會注意到無限的鏡像效果。 
* 執行傳統型應用程式可能會導致非 Ultra Windows Mixed Reality 電腦上的效能問題;不建議您這樣做。  
* 傳統型應用程式可能會自動啟動，因為桌面上的隱藏視窗具有焦點。 
* 桌面使用者帳戶控制提示會使耳機顯示為黑色，直到提示完成為止。

#### <a name="windows-mixed-reality-for-steamvr"></a>適用于 SteamVR 的 Windows Mixed Reality

* 您可能需要在更新之後啟動混合實境入口，以確保2018年4月更新的必要軟體 Windows 10 更新已完成，再啟動 SteamVR。 
* 您必須使用最新版本的 Windows Mixed Reality，SteamVR 才能 Windows 10 與2018年4月更新保持相容。 確定已針對 SteamVR Windows Mixed Reality 開啟自動更新，其位於串流的程式庫的「軟體」區段中。  

#### <a name="other-issues"></a>其他問題

>[!IMPORTANT]
>Windows 10 2018 年4月更新的早期版本推送至測試人員 (17134.5 版) 缺少執行 Windows Mixed Reality 所需的軟體。 如果使用 Windows Mixed Reality，建議您避免使用此版本。 

當您在此更新的初始發行版本上使用 Surface Book 2 時，已識別出效能回歸 (10.0.17134.1) 我們正致力於在即將推出的更新修補程式中進行修正。 建議您等到修正此問題，然後再手動更新或等待更新正常推出。

## <a name="provide-feedback-and-report-issues"></a>提供意見反應和報告問題

使用[HoloLens 或 Windows 10 電腦上意見反應中樞應用程式](/windows/mixed-reality/give-us-feedback)來提供意見反應和回報問題。 使用意見反應中樞可確保包含所有必要的診斷資訊，以協助我們的工程師快速地偵測和解決問題。

>[!NOTE]
>請務必接受提示，詢問您是否要意見反應中樞存取您的 [檔] 資料夾， (在出現提示時選取 **[是]**) 。

## <a name="prior-release-notes"></a>先前的版本資訊

* [版本資訊 - 2017 年 10 月](release-notes-october-2017.md)
* [版本資訊 - 2016 年 8 月](release-notes-august-2016.md)
* [版本資訊 - 2016 年 5 月](release-notes-may-2016.md)
* [版本資訊 - 2016 年 3 月](release-notes-march-2016.md)

## <a name="see-also"></a>另請參閱
* [ (外部連結的沉浸式耳機支援) ](./troubleshooting-windows-mixed-reality.md)
* [HoloLens 支援 (外部連結) ](https://support.microsoft.com/products/hololens)
* [安裝工具](/windows/mixed-reality/develop/install-the-tools)
* [提供意見反應](/windows/mixed-reality/give-us-feedback)