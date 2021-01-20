---
title: 應用程式模型
description: Windows Mixed Reality 使用通用 Windows 平臺所提供的應用程式模型，也就是新式 Windows 應用程式的模型和環境。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: UWP、應用程式模型、生命週期、暫停、繼續、磚、視圖、合約、混合現實耳機、windows mixed reality 耳機、虛擬實境耳機、HoloLens、MRTK、混合現實工具組
ms.openlocfilehash: 941c0f3f81596e8465157121462b4150cefd8ac2
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583215"
---
# <a name="app-model"></a>應用程式模型

Windows Mixed Reality 使用 [通用 Windows 平臺](/windows/uwp/get-started/) (UWP) 所提供的應用程式模型，也就是新式 Windows 應用程式的模型和環境。 UWP 應用程式模型定義了如何安全地安裝、更新、設定版本，以及完全移除應用程式。 它也會控制應用程式的生命週期，也就是應用程式執行、睡眠和停止的方式，以及它們如何保留狀態。 最後，應用程式模型涵蓋與作業系統、檔案和其他應用程式的整合和互動。

![在早餐區域 Windows Mixed Reality 首頁中排列的2D 應用程式](images/20160112-055908-hololens-500px.jpg)<br>
*在 Windows Mixed Reality 首頁中排列2D 視圖的應用程式*

## <a name="app-lifecycle"></a>應用程式週期

混合現實應用程式的生命週期牽涉到標準應用程式概念，例如放置、啟動、終止和移除。

### <a name="placement-is-launch"></a>放置開始

每個應用程式都是以混合現實的方式啟動，方法是將應用程式磚放 ([Windows Mixed Reality 首頁](../discover/navigating-the-windows-mixed-reality-home.md)中) 的[Windows 次要磚](/uwp/api/Windows.UI.StartScreen.SecondaryTile)。 這些應用程式圖格會在放置時開始執行應用程式。 這些應用程式磚會保存並保持在其放置位置，如同您想要傳回給應用程式的啟動器。

![放置會將次要磚放在世界中](images/slide1-600px.png)<br>
*放置會將次要磚放在世界中*

放置完成之後 ([除非應用程式](app-model.md#protocols) 啟動應用程式啟動) ，否則應用程式會開始啟動。 Windows Mixed Reality 可以一次執行有限數量的應用程式。 一旦您放置並啟動應用程式，其他作用中的應用程式可能會暫停。 已暫停的應用程式會在您放置應用程式的任何位置，讓應用程式的上次狀態螢幕擷取畫面。 如需處理繼續和其他生命週期事件的詳細資訊，請參閱 [WINDOWS 10 UWP 應用程式生命週期](/windows/uwp/launch-resume/app-lifecycle)。

![放置磚之後，應用程式會開始 ](images/slide2-500px.png) ![ 執行執行、暫停或未執行之應用程式的狀態圖表](images/ic576232-500px.png)<br>
*左方：放置磚之後，應用程式就會開始執行。Right：應用程式執行中、已暫止或未執行的狀態圖表。*

### <a name="remove-is-closeterminate-process"></a>移除是關閉/終止進程

當您從世界中移除放置的應用程式磚時，基礎進程會關閉。 這有助於確保您的應用程式停止或重新開機有問題的應用程式。

### <a name="app-suspensiontermination"></a>應用程式暫停/終止

在 [Windows Mixed Reality 首頁](../discover/navigating-the-windows-mixed-reality-home.md)中，使用者可以從 [開始] 功能表啟動應用程式，並將應用程式磚放在世界中，以建立應用程式的多個進入點。 每個應用程式磚的行為都是不同的進入點，並且在系統中具有個別的磚實例。 [SecondaryTile](/uwp/api/Windows.UI.StartScreen.SecondaryTile#Windows_UI_StartScreen_SecondaryTile_FindAllAsync)的查詢會針對每個應用程式實例產生 **SecondaryTile** 。

當 UWP 應用程式暫停時，會取得目前狀態的螢幕擷取畫面。

![針對已暫止的應用程式顯示幕幕快照](images/slide9-800px.png)<br>
*針對已暫止的應用程式顯示幕幕快照*

另一個 Windows 10 shell 的主要差異在於應用程式如何透過 CoreApplication 來通知應用程式實例啟用[。](/uwp/api/Windows.ApplicationModel.Core.CoreApplication#Windows_ApplicationModel_Core_CoreApplication_Resuming) [](/uwp/api/windows.ui.core.corewindow#Windows_UI_Core_CoreWindow_Activated)

|  狀況 |  繼續中  |  已啟動 | 
|----------|----------|----------|
|  從 [開始] 功能表啟動應用程式的新實例  |   |  以新的 [TileId](/uwp/api/windows.ui.startscreen.secondarytile#Windows_UI_StartScreen_SecondaryTile_TileId) **啟用** | 
|  從 [開始] 功能表啟動應用程式的第二個實例  |   |  以新的 **TileId** **啟用** | 
|  選取目前未使用的應用程式實例  |   |  使用與實例相關聯的 **TileId** 來 **啟用** | 
|  選取不同的應用程式，然後選取先前作用中的實例  |  **繼續** 引發  |  | 
|  選取不同的應用程式，然後選取先前處於非使用中狀態的實例  |  **繼續** 引發  |  然後使用與實例相關聯的 **TileId** 來 **啟用** | 

### <a name="extended-execution"></a>擴充執行

有時候您的應用程式需要繼續在背景中執行工作或播放音訊。 [背景](/windows/uwp/launch-resume/declare-background-tasks-in-the-application-manifest) 工作可在 HoloLens 上取得。

![應用程式可以在背景中執行](images/slide10-800px.png)<br>
*應用程式可以在背景中執行*

## <a name="app-views"></a>應用程式檢視

當您的應用程式啟動時，您可以選擇您想要顯示的檢視類型。 針對應用程式的 **CoreApplication**，一律會有主要的 [應用程式視圖](/uwp/api/Windows.UI.ViewManagement.ApplicationView) ，以及您想要建立的任意數目的應用程式視圖。 在桌上型電腦上，您可以將應用程式視圖視為視窗。 我們的混合現實應用程式範本會建立 Unity 專案，其中主要應用程式視圖為 [沉浸式](app-views.md)。 

您的應用程式可以使用 XAML 之類的技術來建立額外的2D 應用程式視圖，以使用應用程式內購買的 Windows 10 功能。 如果您的應用程式啟動為其他 Windows 10 裝置的 UWP 應用程式，您的主要視圖是2D。 不過，您可以藉由新增另一個可輕鬆顯示體驗 volumetrically 的應用程式視圖，在混合現實中「亮亮」。 想像一下以 XAML 建立相片檢視器應用程式，其中的投影片按鈕會切換至沉浸式應用程式視圖，從世界各地的應用程式 flew 相片。

![執行中的應用程式可以有2D 視圖或沉浸式視圖](images/slide3-800px.png)<br>
*執行中的應用程式可以有2D 視圖或沉浸式視圖*

### <a name="creating-an-immersive-view"></a>建立沉浸式視圖

混合現實應用程式會建立具有 [HolographicSpace](/uwp/api/windows.graphics.holographic.holographicspace) 類型的沉浸式觀看。

純粹是沉浸式的應用程式應該一律在啟動時建立沉浸式視圖，即使是從桌面啟動也一樣。 沉浸式視圖一律會顯示在耳機中，不論其建立位置為何。 啟用沉浸式視圖會顯示混合實境入口，並引導使用者進入其耳機。

在桌上型電腦監視器上以2D 視圖開頭的應用程式，可能會建立次要的沉浸式視圖，以顯示耳機中的內容。 其中一個範例是監視器上的 2D Edge 視窗，會在耳機中顯示360度的影片。

![在沉浸式視圖中執行的應用程式只有一個可見的](images/slide4-800px.png)<br>
*在沉浸式視圖中執行的應用程式是唯一可見的*

### <a name="2d-view-in-the-windows-mixed-reality-home"></a>Windows Mixed Reality 首頁中的2D 視圖

沉浸式觀賞以外的任何功能都會轉譯為您世界上的2D 觀點。

在桌上型電腦監視器和耳機中，應用程式可能會有2D 的視圖。 新的2D 視圖將放置在與建立它的視圖相同的 shell 中，不論是在監視器上或在耳機中。 應用程式或使用者目前無法在混合現實首頁與監視器之間移動2D 視圖。

![在 2D view 中執行的應用程式與其他應用程式共用混合世界的空間](images/slide5-800px.png)<br>
*在2D 視圖中執行的應用程式與其他應用程式共用空間*

### <a name="placement-of-additional-app-tiles"></a>其他應用程式磚的位置

您可以視需要使用 [次要磚 api](/windows/uwp/design/shell/tiles-and-notifications/secondary-tiles)，將多個應用程式放在世界各地的 2d view。 這些「釘選」的磚會顯示為使用者必須放置的啟動顯示畫面，之後可用來啟動您的應用程式。 Windows Mixed Reality 目前不支援將任何2D 磚內容轉譯為動態磚。

![使用次要磚的應用程式可以有多個放置](images/slide6-800px.png)<br>
*使用次要磚的應用程式可以有多個放置*

### <a name="switching-views"></a>切換視圖

#### <a name="switching-from-the-2d-xaml-view-to-the-immersive-view"></a>從 2D XAML 視圖切換至沉浸式視圖

如果應用程式使用 XAML，則 XAML [IFrameworkViewSource](/uwp/api/windows.applicationmodel.core.iframeworkviewsource) 會控制應用程式的第一個視圖。 應用程式必須在啟用 **CoreWindow** 之前切換至沉浸式觀賞，以確保應用程式直接啟動至沉浸式體驗。

使用 [CoreApplication. CreateNewView](/uwp/api/Windows.ApplicationModel.Core.CoreApplication#Windows_ApplicationModel_Core_CoreApplication_CreateNewView_Windows_ApplicationModel_Core_IFrameworkViewSource_) 和 [ApplicationViewSwitcher](/uwp/api/Windows.UI.ViewManagement.ApplicationViewSwitcher#Windows_UI_ViewManagement_ApplicationViewSwitcher_SwitchAsync_System_Int32_) ，讓它成為使用中的視圖。

> [!NOTE]
>* 從 XAML 視圖切換至沉浸式視圖時，請勿指定 **SwitchAsync** 的 [ApplicationViewSwitchingOptions ConsolidateViews](/uwp/api/windows.ui.viewmanagement.applicationviewswitchingoptions)旗標，或啟動應用程式的平板將從世界中移除。
>* **SwitchAsync** 應該使用與您要切換的視圖關聯的 [發送器](/uwp/api/windows.ui.core.corewindow#Windows_UI_Core_CoreWindow_Dispatcher) 來呼叫。
>* 如果您需要啟動虛擬鍵盤或想要啟用另一個應用程式，則必須 **SwitchAsync** 回 XAML 視圖。

![](images/slide7-600px.png) ![ 當應用程式進入沉浸式觀賞、混合的世界和其他應用程式消失時，應用程式可以在2d 視圖和沉浸式視圖之間切換](images/slide8-600px.png)<br>
*左方：應用程式可以在2D 視圖和沉浸式視圖之間切換。沒錯：當應用程式進入沉浸式觀看時，Windows Mixed Reality 首頁和其他應用程式會消失。*

#### <a name="switching-from-the-immersive-view-back-to-a-keyboard-xaml-view"></a>從沉浸式視圖切換回鍵盤 XAML 視圖

在 views 之間來回切換的一個常見原因，是在混合現實應用程式中顯示鍵盤。 只有當應用程式顯示2D 視圖時，shell 才能顯示系統鍵盤。 如果應用程式需要取得文字輸入，它可能會提供具有文字輸入欄位的自訂 XAML 視圖、切換至該視窗，然後在輸入完成之後切換回來。

如同上一節中所示，您可以使用 **ApplicationViewSwitcher SwitchAsync** 從您的沉浸式視圖轉換回 XAML 視圖。

## <a name="app-size"></a>應用程式大小

2D 應用程式視圖一律會出現在固定的虛擬平板中。 這會讓所有2D 視圖顯示完全相同的內容數量。 以下是應用程式2D 視圖大小的進一步詳細資料：
* 調整應用程式時，會保留應用程式的外觀比例。
* 應用程式 [解析度和縮放比例](../develop/porting-apps/building-2d-apps.md#2d-app-view-resolution-and-scale-factor) 不會因調整大小而變更。
* 應用程式無法在世界中查詢其實際大小。

![2D 應用程式會以固定的視窗大小顯示](images/12493521-10104043956964683-6118765685995662420-o-500px.jpg)<br>
*具有2D 視圖的應用程式會以固定的視窗大小顯示*

## <a name="app-tiles"></a>應用程式磚

此 [開始] 功能表會針對釘 **選和所有應用程式** 清單，使用標準的小型磚和中等磚。 

![Windows Mixed Reality 的 [開始] 功能表](images/start-500px.png)<br>
*Windows Mixed Reality 的 [開始] 功能表*

## <a name="app-to-app-interactions"></a>應用程式與應用程式的互動

當您建立應用程式時，您可以存取 Windows 10 上可用的應用程式通訊機制的豐富應用程式。 許多新的通訊協定 Api 和檔案註冊在 HoloLens 上都能順利運作，以啟用應用程式啟動和通訊。 

針對桌上型耳機，與指定副檔名或通訊協定相關聯的應用程式可能是 Win32 應用程式，只能出現在桌面監視器或桌上型電腦平板中。

### <a name="protocols"></a>通訊協定

HoloLens 透過Windows.System 支援應用程式啟動應用程式 [ 。啟動器 Api](/uwp/api/Windows.System.Launcher)。

啟動另一個應用程式時，需要考慮一些事項：

* 執行非強制回應啟動（例如 [LaunchUriAsync](/uwp/api/Windows.System.Launcher#Windows_System_Launcher_LaunchUriAsync_Windows_Foundation_Uri_)）時，使用者必須先放置應用程式，才能與其互動。

* 執行強制回應啟動時（例如透過 [LaunchUriForResultsAsync](/uwp/api/Windows.System.Launcher#Windows_System_Launcher_LaunchUriForResultsAsync_Windows_Foundation_Uri_Windows_System_LauncherOptions_Windows_Foundation_Collections_ValueSet_)），會將強制回應應用程式放在視窗頂端。

* Windows Mixed Reality 無法在專屬的視圖上重迭應用程式。 為了顯示已啟動的應用程式，Windows 會將使用者帶回世界以顯示應用程式。

### <a name="file-pickers"></a>檔案選擇器

HoloLens 同時支援 [FileOpenPicker](/uwp/api/Windows.Storage.Pickers.FileOpenPicker) 和 [FileSavePicker](/uwp/api/Windows.Storage.Pickers.FileSavePicker) 合約。 不過，尚未預先安裝任何應用程式來滿足檔案選擇器合約。 例如，您可以從 Microsoft Store 安裝這些應用程式-OneDrive。

如果您已安裝多個檔案選擇器應用程式，您將不會看到任何可供選擇要啟動之應用程式的混淆 UI。 相反地，系統會選擇第一個安裝的檔案選擇器。 儲存檔案時，會產生包含時間戳記的檔案名。 這無法由使用者變更。

根據預設，下列是在本機支援的延伸模組：

|  應用程式  |  延伸模組 | 
|----------|----------|
|  照片  |  bmp、gif、jpg、png、avi、mov、的 wmv、wmv | 
|  Microsoft Edge  |  htm、html、pdf、svg、xml | 

### <a name="app-contracts-and-windows-mixed-reality-extensions"></a>應用程式合約和 Windows Mixed Reality 擴充功能

應用程式合約和擴充點可讓您註冊應用程式，以利用更深入的作業系統功能，例如處理副檔名或使用背景工作。 這是支援和不支援的合約清單，以及 HoloLens 上的擴充點。

|  合約或延伸模組  |  是否支援？ | 
|----------|----------|
| [帳戶圖片提供者 (延伸模組) ](/previous-versions/windows/apps/hh464906(v=win.10)#account_picture_provider) | 不支援 | 
| [警示](/previous-versions/windows/apps/hh464906(v=win.10)#alarm) | 不支援 | 
| [App Service](/previous-versions/windows/apps/hh464906(v=win.10)#app_service) | 支援但無法完全運作 | 
| [約會提供者](/previous-versions/windows/apps/hh464906(v=win.10)#appointmnets_provider) | 不支援 | 
| [自動播放 (延伸模組) ](/previous-versions/windows/apps/hh464906(v=win.10)#autoplay) | 不支援 | 
| [ (擴充功能的背景工作) ](/previous-versions/windows/apps/hh464906(v=win.10)#background_tasts) | 部分支援的 (並非所有觸發程式都可運作)  | 
| [更新工作 (延伸模組) ](/previous-versions/windows/apps/hh464906(v=win.10)#update_task) | 支援 | 
| [快取檔案更新程式合約](/previous-versions/windows/apps/hh464906(v=win.10)#cached_file_updater) | 支援 | 
| [ (擴充功能的相機設定) ](/previous-versions/windows/apps/hh464906(v=win.10)#camera_settings) | 不支援 | 
| [撥號通訊協定](/previous-versions/windows/apps/hh464906(v=win.10)#dial_protocol) | 不支援 | 
| [檔案啟用 (延伸模組) ](/previous-versions/windows/apps/hh464906(v=win.10)#file_activation) | 支援 | 
| [檔案開啟選擇器協定](/previous-versions/windows/apps/hh464906(v=win.10)#file_open_picker_contract) | 支援 | 
| [檔案儲存選擇器協定](/previous-versions/windows/apps/hh464906(v=win.10)#file_save_picker_contract) | 支援 | 
| [鎖定螢幕呼叫](/previous-versions/windows/apps/hh464906(v=win.10)#lock_screen_call) | 不支援 | 
| [媒體播放](/previous-versions/windows/apps/hh464906(v=win.10)#media_playback) | 不支援 | 
| [播放至合約](/previous-versions/windows/apps/hh464906(v=win.10)#playto_contract) | 不支援 | 
| [預先安裝的設定工作](/previous-versions/windows/apps/hh464906(v=win.10)#preinstalled_config_task) | 不支援 | 
| [Print 3D 工作流程](/previous-versions/windows/apps/hh464906(v=win.10)#print_3d_workflow) | 支援 | 
| [ (擴充功能) 列印工作設定 ](/previous-versions/windows/apps/hh464906(v=win.10)#print_task_settings) | 不支援 | 
| [URI 啟用 (延伸模組) ](/previous-versions/windows/apps/hh464906(v=win.10)#protocol_activation) | 支援 | 
| [受限啟動](/previous-versions/windows/apps/hh464906(v=win.10)#restricted_launch) | 不支援 | 
| [搜尋合約](/previous-versions/windows/apps/hh464906(v=win.10)#search_contract) | 不支援 | 
| [設定合約](/previous-versions/windows/apps/hh464906(v=win.10)#settings_contract) | 不支援 | 
| [共用合約](/previous-versions/windows/apps/hh464906(v=win.10)#share_contract) | 不支援 | 
| [SSL/憑證 (延伸模組) ](/previous-versions/windows/apps/hh464906(v=win.10)#ssl_certificates) | 支援 | 
| [Web 帳戶提供者](/previous-versions/windows/apps/hh464906(v=win.10)#web_account_provider) | 支援 | 

## <a name="app-file-storage"></a>應用程式檔儲存體

所有儲存體都是透過 [Windows. storage 命名空間](/uwp/api/Windows.Storage)。 HoloLens 不支援應用程式儲存體同步處理/漫遊。 如需詳細資訊，請參閱下列檔：

* [檔案、資料夾和媒體櫃](/windows/uwp/files/index)
* [儲存及擷取設定和其他應用程式資料](/windows/uwp/design/app-settings/store-and-retrieve-app-data)

### <a name="known-folders"></a>已知的資料夾

如需 UWP 應用程式的完整詳細資料，請參閱 [KnownFolders](/uwp/api/Windows.Storage.KnownFolders) 。

<table>
<tr>
<th> 屬性</th><th> 在 HoloLens 上支援</th><th> 在沉浸式耳機上支援</th><th> 描述</th>
</tr><tr>
<td><a href="/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_AppCaptures">AppCaptures</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>取得應用程式的 [捕獲] 資料夾。</td>
</tr><tr>
<td><a href="/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_CameraRoll">CameraRoll</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>取得相機翻轉資料夾。</td>
</tr><tr>
<td><a href="/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_DocumentsLibrary">DocumentsLibrary</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>取得文件庫。 文件庫並非一般用途。</td>
</tr><tr>
<td><a href="/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_MusicLibrary">MusicLibrary</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>取得音樂媒體櫃。</td>
</tr><tr>
<td><a href="/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_Objects3D">Objects3D</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>取得物件3D 資料夾。</td>
</tr><tr>
<td><a href="/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_PicturesLibrary">PicturesLibrary</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>取得圖片媒體櫃。</td>
</tr><tr>
<td><a href="/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_Playlists">播放清單</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>取得播放清單資料夾。</td>
</tr><tr>
<td><a href="/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_SavedPictures">SavedPictures</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>取得已儲存的圖片資料夾。</td>
</tr><tr>
<td><a href="/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_VideosLibrary">VideosLibrary</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>取得影片庫。</td>
</tr><tr>
<td><a href="/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_HomeGroup">HomeGroup</a></td><td></td><td style="text-align: center;">✔️</td><td>取得家庭家庭資料夾。</td>
</tr><tr>
<td><a href="/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_MediaServerDevices">MediaServerDevices</a></td><td></td><td style="text-align: center;">✔️</td><td>取得媒體伺服器的資料夾 (數位生活網路聯盟 (DLNA) # A3 裝置。</td>
</tr><tr>
<td><a href="/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_RecordedCalls">RecordedCalls</a></td><td></td><td style="text-align: center;">✔️</td><td>取得錄製的呼叫資料夾。</td>
</tr><tr>
<td><a href="/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_RemovableDevices">RemovableDevices</a></td><td></td><td style="text-align: center;">✔️</td><td>取得「卸載式裝置」資料夾。</td>
</tr>
</table>

## <a name="app-package"></a>應用程式套件

使用 Windows 10 時，您不再以作業系統為目標，而是將 [應用程式的目標設為一或多個裝置系列](/windows/uwp/get-started/universal-application-platform-guide#device-families)。 裝置系列會識別 API、系統特性以及您對於裝置系列中的裝置可以預期的行為。 它也會決定您的應用程式可從 [Microsoft Store](../distribute/submitting-an-app-to-the-microsoft-store.md#specifying-target-device-families)安裝的裝置集合。

* 若要以桌上型耳機和 HoloLens 為目標，請將應用程式的目標設為 **Windows。通用** 裝置系列。
* 若要以桌面耳機為目標，請將您的應用程式目標設為 **Windows desktop** 裝置系列。
* 若要以 HoloLens 為目標，請將您的應用程式設定為 **Windows** 全像裝置系列。

## <a name="see-also"></a>另請參閱

* [應用程式檢視](app-views.md)
* [更新混合實境的 2D UWP 應用程式](../develop/porting-apps/building-2d-apps.md)
* [3D 應用程式啟動程式設計指引](../distribute/3d-app-launcher-design-guidance.md)
* [實作 3D 應用程式啟動器](../distribute/implementing-3d-app-launchers.md)