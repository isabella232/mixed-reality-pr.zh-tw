---
title: 裝置入口網站 API 參照
description: HoloLens Windows 裝置入口網站的 API 參考
author: hamalawi
ms.author: moelhama
ms.date: 08/03/2020
ms.topic: article
keywords: HoloLens、Windows 裝置入口網站、API、混合現實耳機、Windows mixed reality 耳機、虛擬實境耳機
ms.openlocfilehash: 1085f6c948ab7fe0ff8cb3801ebb0b883570acbc
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2020
ms.locfileid: "94677967"
---
# <a name="device-portal-api-reference"></a>裝置入口網站 API 參照

[Windows 裝置入口網站](using-the-windows-device-portal.md)中的所有專案都建置於 REST API 的之上，您可以用來以程式設計方式存取資料和控制您的裝置。

## <a name="app-deloyment"></a>應用程式部署常見問題

**/api/app/packagemanager/package (刪除)**

卸載應用程式

參數
* 封裝：要卸載之封裝的檔案名。

**/api/app/packagemanager/package (POST)**

安裝應用程式

參數
* 封裝：要安裝之套件的檔案名。

Payload
* 多部分的符合 HTTP 主體

**/api/app/packagemanager/packages (取得)**

抓取系統上已安裝應用程式的清單，並提供詳細資料

傳回資料
* 包含詳細資料的已安裝套件清單

**/api/app/packagemanager/state (取得)**

取得進行中的應用程式安裝狀態

## <a name="dump-collection"></a>傾印集合

**/api/debug/dump/usermode/crashcontrol (刪除)**

停用側載應用程式的損毀傾印收集

參數
* packageFullname：套件名稱

**/api/debug/dump/usermode/crashcontrol (取得)**

取得側載 apps 損毀傾印集合的設定

參數
* packageFullname：套件名稱

**/api/debug/dump/usermode/crashcontrol (POST)**

啟用並設定側載應用程式的傾印控制項設定

參數
* packageFullname：套件名稱

**/api/debug/dump/usermode/crashdump (刪除)**

刪除側載應用程式的損毀傾印

參數
* packageFullname：套件名稱
* 檔案名：傾印檔案名

**/api/debug/dump/usermode/crashdump (取得)**

捕獲側載應用程式的損毀傾印

參數
* packageFullname：套件名稱
* 檔案名：傾印檔案名

傳回資料
* 傾印檔案。 使用 WinDbg 或 Visual Studio 檢查

**/api/debug/dump/usermode/dumps (取得)**

傳回側載 apps 的所有損毀傾印清單

傳回資料
* 每一端載入的應用程式損毀傾印清單

## <a name="etw"></a>ETW

**/api/etw/providers (取得)**

列舉已註冊的提供者

傳回資料
* 提供者清單、易記名稱和 GUID

**/api/etw/session/realtime (GET/WebSocket)**

建立即時 ETW 會話;在 websocket 上進行管理。

傳回資料
* 來自已啟用提供者的 ETW 事件

## <a name="holographic-os"></a>全像攝影版 OS

**/api/holographic/os/etw/customproviders (取得)**

傳回未向系統註冊的 HoloLens 特定 ETW 提供者清單

**/api/holographic/os/services (取得)**

傳回所有執行中之服務的狀態。

**/api/holographic/os/settings/ipd (取得)**

取得儲存的 IPD (Interpupillary 距離) 以毫米為單位

**/api/holographic/os/settings/ipd (POST)**

設定 IPD

參數
* ipd：要設定的新 IPD 值（以毫米為單位）

**/api/holographic/os/webmanagement/settings/HTTPs (取得)**

取得裝置入口網站的 HTTPS 需求

**/api/holographic/os/webmanagement/settings/HTTPs (POST)**

設定裝置入口網站的 HTTPS 需求

參數
* 必要：是、否或預設值

## <a name="holographic-perception"></a>全像

**/api/holographic/perception/client (GET/WebSocket)**

接受 websocket 升級並執行感知用戶端，以 30 fps 的形式傳送更新。

參數
* clientmode：「作用中」會在無法被動建立時強制視覺化追蹤模式

## <a name="holographic-thermal"></a>全像熱

**/api/holographic/thermal/stage (取得)**

取得裝置的熱階段 (0 正常、1暖、2關鍵) 

## <a name="map-manager"></a>地圖管理員

**/api/holographic/mapmanager/mapFiles (取得)**

取得可用對應檔 ( mapx) 的清單。

**/api/holographic/mapmanager/anchorFiles (取得)**

取得可用錨定檔案 ( ancx) 的清單。

**/api/holographic/mapmanager/srdbFiles (取得)**

取得可用空間重建資料庫檔案 ( srdb) 的清單。

**/api/holographic/mapmanager/getanchors (取得)**

取得目前使用者的已保存錨點清單。 

### <a name="downloaduploaddelete-files"></a>下載/上傳/刪除檔案
**/api/holographic/mapmanager/download (取得)**

下載地圖、錨點或空間重建資料庫檔案。 檔案必須先前已上傳或匯出。

參數
* 檔案名：要下載的檔案名。

範例： 
```
$.post("/api/holographic/mapmanager/download?FileName=" + spaceID)
```

**/api/holographic/mapmanager/upload (POST)**

上傳地圖、錨點或空間重建資料庫檔案。 檔案上傳之後，稍後可以匯入以供系統使用。

參數
* file：要上傳之檔案的名稱。

範例：
```
var form_data = new FormData();
form_data.append("file", file_data);

$.ajax({
    url: "/api/holographic/mapmanager/upload",
    dataType: 'json',
    cache: false,
    contentType: false,
    processData: false,
    data: form_data,
    type: 'post'
})
```

**/api/holographic/mapmanager/delete (POST)**

刪除地圖、錨點或空間重建資料庫檔案。 檔案必須先前已上傳或匯出。

參數
* FileName：要刪除的檔案名。

範例： 
```
$.post("/api/holographic/mapmanager/delete?FileName=" + spaceID)
```

### <a name="export"></a>匯出

**/api/holographic/mapmanager/export (POST)**

匯出系統目前正在使用的對應。 一旦匯出之後，即可加以下載。 

範例： 
```
$.post("/api/holographic/mapmanager/export")
```

**/api/holographic/mapmanager/exportanchors (POST)**

匯出系統目前正在使用的對應。 一旦匯出之後，即可加以下載。 範例： 
```
$.post("/api/holographic/mapmanager/exportanchors")
```

**/api/holographic/mapmanager/exportmapandanchors (POST)**

匯出系統目前正在使用的對應和錨點。 一旦匯出之後，即可加以下載。 範例： 
```
$.post("/api/holographic/mapmanager/exportmapandanchors")
```

**/api/holographic/mapmanager/exportmapandspatialmappingdb (POST)**

匯出系統目前正在使用的地圖和空間重建資料庫。 一旦匯出之後，即可加以下載。 

範例： 
```
$.post("/api/holographic/mapmanager/exportmapandspatialmappingdb")
```

### <a name="import"></a>匯入

**/api/holographic/mapmanager/import (POST)**

向系統表示目前使用的對應。 可以在已匯出或已上傳的檔案上呼叫。

參數
* FileName：要使用的對應名稱。 

範例： 
```
$.post("/api/holographic/mapmanager/import?FileName=" + spaceID, function() { alert("Import was successful!"); })
```

**/api/holographic/mapmanager/importanchors (POST)**

向系統表示目前使用的錨點。 可以在已匯出或已上傳的檔案上呼叫。

參數
* FileName：要使用的錨點名稱。 

範例： 
```
$.post("/api/holographic/mapmanager/import?FileName=" + spaceID, function() { alert("Import was successful!"); })
```

**/api/holographic/mapmanager/importspatialmappingdb (POST)**

向系統表示目前應使用的空間重建資料庫。 可以在已匯出或已上傳的檔案上呼叫。

參數
* FileName：要使用之空間對應資料庫的名稱。 

範例： 
```
$.post("/api/holographic/mapmanager/import?FileName=" + spaceID, function() { alert("Import was successful!"); })
```

### <a name="other"></a>其他

**/api/holographic/mapmanager/resetmapandanchorsandsrdb (POST)**

重設對應、錨定和空間重建資料庫的系統。

範例： 
```
$.post("/api/holographic/mapmanager/resetmapandanchorsandsrdb")
```

**/api/holographic/mapmanager/status (取得)**

取得系統的狀態，包括上次匯入的對應、錨點和空間重建資料庫檔案。 


## <a name="mixed-reality-capture"></a>混合實境擷取

**/api/holographic/mrc/file (取得)**

從裝置下載混合的實際檔案。 使用 op = 串流查詢參數進行串流。

參數
* 檔案名：要取得之影片檔案的名稱、hex64 編碼
* op：資料流程

**/api/holographic/mrc/file (刪除)**

從裝置刪除混合現實記錄。

參數
* 檔案名：要刪除之檔案的名稱、hex64 編碼

**/api/holographic/mrc/files (取得)**

傳回儲存在裝置上的混合現實檔案清單

**/api/holographic/mrc/photo (POST)**

採用混合的現實照片，並在裝置上建立檔案

參數
* hololens：抓取全像： true 或 false (預設為 false) 
* pv： capture PV 攝影機： true 或 false (預設為 false) 
* RenderFromCamera： (只 HoloLens 2) 從相片/攝影機的觀點轉譯： true 或 false (預設為 true) 

**/api/holographic/mrc/settings (取得)**

取得預設的混合現實捕獲設定

**/api/holographic/mrc/settings (POST)**

設定預設的混合現實捕獲設定。  其中某些設定會套用到系統的 MRC 照片和影片捕捉。

**/api/holographic/mrc/status (取得)**

取得 Windows 裝置入口網站內混合現實捕捉的狀態。

**_回應_* _

回應包含 JSON 屬性，指出 Windows 裝置入口網站是否錄製影片。

``` javascript
{"IsRecording" : boolean}
```

_ */api/holographic/mrc/thumbnail (取得)**

取得指定檔案的縮圖影像。

參數
* 檔案名：已要求縮圖的檔案名、hex64 編碼的檔案

**/api/holographic/mrc/video/control/start (POST)**

開始混合現實記錄

參數
* hololens：抓取全像： true 或 false (預設為 false) 
* pv： capture PV 攝影機： true 或 false (預設為 false) 
* mic： capture 麥克風： true 或 false (預設為 false) 
* 回送： capture app audio： true 或 false (預設為 false) 
* RenderFromCamera： (只 HoloLens 2) 從相片/攝影機的觀點轉譯： true 或 false (預設為 true) 
* vstab： (只 HoloLens 2) 啟用影片穩定： true 或 false (預設為 true) 
* vstabbuffer： (只 HoloLens 2) video 穩定緩衝區延遲：0到30個畫面格 (預設為15個畫面格) 

**/api/holographic/mrc/video/control/stop (POST)**

停止目前的混合現實記錄

## <a name="mixed-reality-streaming"></a>混合的現實串流

HoloLens 透過區塊下載分散的數量，支援混合現實的即時預覽。

混合的現實資料流程共用一組相同的參數來控制所要捕獲的內容：
* hololens：抓取全像： true 或 false
* pv： capture PV 攝影機： true 或 false
* mic： capture 麥克風： true 或 false
* 回送：捕捉應用程式音訊： true 或 false

如果未指定這些任何一項：將會捕捉全像照片、相片/攝影機和應用程式音訊<br>
如果有指定任何參數：未指定的參數會預設為 false

 (只 HoloLens 2) 的選擇性參數
* RenderFromCamera：從相片/攝影機的觀點來呈現： true 或 false (預設為 true) 
* vstab：啟用影片穩定： true 或 false (預設為 false) 
* vstabbuffer：影片穩定緩衝區延遲：0到30個畫面格 (預設為15個畫面格) 

**/api/holographic/stream/live.mp4 (取得)**

1280x720p 30fps 5Mbit 串流。

**/api/holographic/stream/live_high.mp4 (取得)**

1280x720p 30fps 5Mbit 串流。

**/api/holographic/stream/live_med.mp4 (取得)**

854x480p 30fps 2.5 Mbit 串流。

**/api/holographic/stream/live_low.mp4 (取得)**

428x240p 15fps 0.6 Mbit 串流。

## <a name="networking"></a>網路功能

**/api/networking/ipconfig (取得)**

取得目前的 ip 設定

## <a name="os-information"></a>作業系統資訊

**/api/os/info (取得)**

取得作業系統資訊

**/api/os/machinename (取得)**

取得電腦名稱稱

**/api/os/machinename (POST)**

設定電腦名稱稱

參數
* 名稱：新電腦名稱稱、hex64 編碼、設定為

## <a name="perception-simulation-control"></a>認知模擬控制項

**/api/holographic/simulation/control/mode (取得)**

取得模擬模式

**/api/holographic/simulation/control/mode (POST)**

設定模擬模式

參數
* 模式：模擬模式：預設、模擬、遠端、舊版

**/api/holographic/simulation/control/stream (刪除)**

刪除控制資料流程。

**/api/holographic/simulation/control/stream (GET/WebSocket)**

開啟控制項資料流程的 web 通訊端連接。

**/api/holographic/simulation/control/stream (POST)**

建立控制項資料流程 (需要優先權) 或將資料張貼至建立的資料流程 (streamId 必要) 。 張貼的資料應為 ' application/八進位-stream ' 類型。

**/api/holographic/simulation/display/stream (GET/WebSocket)**

要求模擬影片串流，其中包含在「模擬」模式中呈現給系統顯示的內容。  一開始會傳送簡單的格式描述元標頭，後面接著 h.264 編碼的材質，每個標頭前面都有一個標頭，表示眼睛索引和材質大小。

## <a name="perception-simulation-playback"></a>感知模擬播放

**/api/holographic/simulation/playback/file (刪除)**

刪除錄製。

參數
* 錄製：要刪除的記錄名稱。

**/api/holographic/simulation/playback/file (POST)**

上傳錄製。

**/api/holographic/simulation/playback/files (取得)**

取得所有錄製。

**/api/holographic/simulation/playback/session (取得)**

取得錄製的目前播放狀態。

參數
* 錄製：錄製的名稱。

**/api/holographic/simulation/playback/session/file (刪除)**

卸載錄製。

參數
* 記錄：要卸載的記錄名稱。

**/api/holographic/simulation/playback/session/file (POST)**

載入錄製。

參數
* 記錄：要載入的記錄名稱。

**/api/holographic/simulation/playback/session/files (取得)**

取得所有載入的記錄。

**/api/holographic/simulation/playback/session/pause (POST)**

暫停錄製。

參數
* 錄製：錄製的名稱。

**/api/holographic/simulation/playback/session/play (POST)**

播放錄製。

參數
* 錄製：錄製的名稱。

**/api/holographic/simulation/playback/session/stop (POST)**

停止錄製。

參數
* 錄製：錄製的名稱。

**/api/holographic/simulation/playback/session/types (取得)**

取得載入錄製中的資料類型。

參數
* 錄製：錄製的名稱。

## <a name="perception-simulation-recording"></a>感知模擬錄製

**/api/holographic/simulation/recording/start (POST)**

開始錄製。 一次只能有一個作用中的記錄。 必須設定 head、雙手、spatialMapping 或環境之一。

參數
* head：設定為1以記錄 head 資料。
* 雙手：設定為1以記錄手資料。
* spatialMapping：設定為1以記錄空間對應。
* 環境：設定為1以記錄環境資料。
* 名稱：錄製的名稱。
* singleSpatialMappingFrame：設定為1只記錄單一空間對應框架。

**/api/holographic/simulation/recording/status (取得)**

取得錄製狀態。

**/api/holographic/simulation/recording/stop (取得)**

停止目前的錄製。 記錄會以檔案的形式傳回。

## <a name="performance-data"></a>效能資料

**/api/resourcemanager/processes (取得)**

傳回執行中進程的清單，並提供詳細資料

傳回資料
* JSON 與進程清單以及每個進程的詳細資料

**/api/resourcemanager/systemperf (取得)**

傳回系統效能統計資料 (i/o 讀取/寫入、記憶體統計資料等。

傳回資料
* 具有系統資訊的 JSON： CPU、GPU、記憶體、網路、IO

## <a name="power"></a>電源

**/api/power/battery (取得)**

取得目前的電池狀態

**/api/power/state (取得)**

檢查系統是否處於低電源狀態

## <a name="remote-control"></a>遠端控制

**/api/control/restart (POST)**

重新開機目標裝置

**/api/control/shutdown (POST)**

關閉目標裝置

## <a name="task-manager"></a>工作管理員

**/api/taskmanager/app (刪除)**

停止新式應用程式

參數
* 封裝：應用程式套件的完整名稱，hex64 編碼
* forcestop：強制所有進程停止 (= 是) 

**/api/taskmanager/app (POST)**

啟動新式應用程式

參數
* appid：要啟動的應用程式 PRAID，hex64 編碼
* 封裝：應用程式套件的完整名稱，hex64 編碼

## <a name="wifi-management"></a>WiFi 管理

**/api/wifi/interfaces (取得)**

列舉無線網路介面

傳回資料
* 具有詳細資料 (GUID、描述等 ) 的無線介面清單

**/api/wifi/network (刪除)**

刪除與指定介面上的網路相關聯的設定檔

參數
* 介面：網路介面 guid
* 設定檔：設定檔名稱

**/api/wifi/networks (取得)**

列舉指定網路介面上的無線網路

參數
* 介面：網路介面 guid

傳回資料
* 網路介面上找到的無線網路清單與詳細資料

**/api/wifi/network (POST)**

連接或中斷指定介面上的網路連線

參數
* 介面：網路介面 guid
* ssid： ssid、hex64 編碼、要連接的
* op：連線或中斷連接
* createprofile：是或否
* 機碼：共用金鑰，hex64 編碼

## <a name="windows-performance-recorder"></a>Windows Performance Recorder

**/api/wpr/customtrace (POST)**

上傳 WPR 設定檔，並使用上傳的設定檔開始追蹤。

Payload
* 多部分的符合 HTTP 主體

傳回資料
* 傳回 WPR 會話狀態。

**/api/wpr/status (取得)**

捕獲 WPR 會話的狀態

傳回資料
* WPR 會話狀態。

**/api/wpr/trace (取得)**

停止 WPR (效能) 追蹤會話

傳回資料
* 傳回追蹤 ETL 檔案

**/api/wpr/trace (POST)**

啟動 WPR (效能) 追蹤會話

參數
* 設定檔：設定檔名稱。 可用的設定檔會儲存在 perfprofiles/profiles.js

傳回資料
* 在開始時，會傳回 WPR 會話狀態。

## <a name="see-also"></a>另請參閱
* [使用 Windows 裝置入口網站](using-the-windows-device-portal.md)
* [裝置入口網站 (UWP) 的核心 API 參考 ](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-api-core)
