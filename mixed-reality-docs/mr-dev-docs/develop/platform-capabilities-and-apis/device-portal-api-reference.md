---
title: 裝置入口網站 API 參照
description: 隨時掌握適用于 HoloLens 開發的 Windows 裝置入口網站 API。
author: hamalawi
ms.author: moelhama
ms.date: 08/03/2020
ms.topic: article
keywords: HoloLens、Windows 裝置入口網站、API、混合現實耳機、Windows mixed reality 耳機、虛擬實境耳機
ms.openlocfilehash: cdbe9635fc51a0d19c978b72fdc8d5db6b8e8e01
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/20/2021
ms.locfileid: "98581256"
---
# <a name="device-portal-api-reference"></a><span data-ttu-id="ef857-104">裝置入口網站 API 參照</span><span class="sxs-lookup"><span data-stu-id="ef857-104">Device portal API reference</span></span>

<span data-ttu-id="ef857-105">[Windows 裝置入口網站](using-the-windows-device-portal.md)中的所有專案都建置於 REST API 的之上，您可以用來以程式設計方式存取資料和控制您的裝置。</span><span class="sxs-lookup"><span data-stu-id="ef857-105">Everything in the [Windows Device Portal](using-the-windows-device-portal.md) is built on top of REST API's that you can use to access the data and control your device programmatically.</span></span>

## <a name="app-deloyment"></a><span data-ttu-id="ef857-106">應用程式部署常見問題</span><span class="sxs-lookup"><span data-stu-id="ef857-106">App deloyment</span></span>

<span data-ttu-id="ef857-107">**/api/app/packagemanager/package (刪除)**</span><span class="sxs-lookup"><span data-stu-id="ef857-107">**/api/app/packagemanager/package (DELETE)**</span></span>

<span data-ttu-id="ef857-108">卸載應用程式</span><span class="sxs-lookup"><span data-stu-id="ef857-108">Uninstalls an app</span></span>

<span data-ttu-id="ef857-109">參數</span><span class="sxs-lookup"><span data-stu-id="ef857-109">Parameters</span></span>
* <span data-ttu-id="ef857-110">封裝：要卸載之封裝的檔案名。</span><span class="sxs-lookup"><span data-stu-id="ef857-110">package : File name of the package to be uninstalled.</span></span>

<span data-ttu-id="ef857-111">**/api/app/packagemanager/package (POST)**</span><span class="sxs-lookup"><span data-stu-id="ef857-111">**/api/app/packagemanager/package (POST)**</span></span>

<span data-ttu-id="ef857-112">安裝應用程式</span><span class="sxs-lookup"><span data-stu-id="ef857-112">Installs an App</span></span>

<span data-ttu-id="ef857-113">參數</span><span class="sxs-lookup"><span data-stu-id="ef857-113">Parameters</span></span>
* <span data-ttu-id="ef857-114">封裝：要安裝之套件的檔案名。</span><span class="sxs-lookup"><span data-stu-id="ef857-114">package : File name of the package to be installed.</span></span>

<span data-ttu-id="ef857-115">Payload</span><span class="sxs-lookup"><span data-stu-id="ef857-115">Payload</span></span>
* <span data-ttu-id="ef857-116">多部分的符合 HTTP 主體</span><span class="sxs-lookup"><span data-stu-id="ef857-116">multi-part conforming http body</span></span>

<span data-ttu-id="ef857-117">**/api/app/packagemanager/packages (取得)**</span><span class="sxs-lookup"><span data-stu-id="ef857-117">**/api/app/packagemanager/packages (GET)**</span></span>

<span data-ttu-id="ef857-118">抓取系統上已安裝應用程式的清單，並提供詳細資料</span><span class="sxs-lookup"><span data-stu-id="ef857-118">Retrieves the list of installed apps on the system, with details</span></span>

<span data-ttu-id="ef857-119">傳回資料</span><span class="sxs-lookup"><span data-stu-id="ef857-119">Return data</span></span>
* <span data-ttu-id="ef857-120">包含詳細資料的已安裝套件清單</span><span class="sxs-lookup"><span data-stu-id="ef857-120">List of installed packages with details</span></span>

<span data-ttu-id="ef857-121">**/api/app/packagemanager/state (取得)**</span><span class="sxs-lookup"><span data-stu-id="ef857-121">**/api/app/packagemanager/state (GET)**</span></span>

<span data-ttu-id="ef857-122">取得進行中的應用程式安裝狀態</span><span class="sxs-lookup"><span data-stu-id="ef857-122">Gets the status of in progress app installation</span></span>

## <a name="dump-collection"></a><span data-ttu-id="ef857-123">傾印集合</span><span class="sxs-lookup"><span data-stu-id="ef857-123">Dump collection</span></span>

<span data-ttu-id="ef857-124">**/api/debug/dump/usermode/crashcontrol (刪除)**</span><span class="sxs-lookup"><span data-stu-id="ef857-124">**/api/debug/dump/usermode/crashcontrol (DELETE)**</span></span>

<span data-ttu-id="ef857-125">停用側載應用程式的損毀傾印收集</span><span class="sxs-lookup"><span data-stu-id="ef857-125">Disables crash dump collection for a sideloaded app</span></span>

<span data-ttu-id="ef857-126">參數</span><span class="sxs-lookup"><span data-stu-id="ef857-126">Parameters</span></span>
* <span data-ttu-id="ef857-127">packageFullname：套件名稱</span><span class="sxs-lookup"><span data-stu-id="ef857-127">packageFullname : package name</span></span>

<span data-ttu-id="ef857-128">**/api/debug/dump/usermode/crashcontrol (取得)**</span><span class="sxs-lookup"><span data-stu-id="ef857-128">**/api/debug/dump/usermode/crashcontrol (GET)**</span></span>

<span data-ttu-id="ef857-129">取得側載 apps 損毀傾印集合的設定</span><span class="sxs-lookup"><span data-stu-id="ef857-129">Gets settings for sideloaded apps crash dump collection</span></span>

<span data-ttu-id="ef857-130">參數</span><span class="sxs-lookup"><span data-stu-id="ef857-130">Parameters</span></span>
* <span data-ttu-id="ef857-131">packageFullname：套件名稱</span><span class="sxs-lookup"><span data-stu-id="ef857-131">packageFullname : package name</span></span>

<span data-ttu-id="ef857-132">**/api/debug/dump/usermode/crashcontrol (POST)**</span><span class="sxs-lookup"><span data-stu-id="ef857-132">**/api/debug/dump/usermode/crashcontrol (POST)**</span></span>

<span data-ttu-id="ef857-133">啟用並設定側載應用程式的傾印控制項設定</span><span class="sxs-lookup"><span data-stu-id="ef857-133">Enables and sets dump control settings for a sideloaded app</span></span>

<span data-ttu-id="ef857-134">參數</span><span class="sxs-lookup"><span data-stu-id="ef857-134">Parameters</span></span>
* <span data-ttu-id="ef857-135">packageFullname：套件名稱</span><span class="sxs-lookup"><span data-stu-id="ef857-135">packageFullname : package name</span></span>

<span data-ttu-id="ef857-136">**/api/debug/dump/usermode/crashdump (刪除)**</span><span class="sxs-lookup"><span data-stu-id="ef857-136">**/api/debug/dump/usermode/crashdump (DELETE)**</span></span>

<span data-ttu-id="ef857-137">刪除側載應用程式的損毀傾印</span><span class="sxs-lookup"><span data-stu-id="ef857-137">Deletes a crash dump for a sideloaded app</span></span>

<span data-ttu-id="ef857-138">參數</span><span class="sxs-lookup"><span data-stu-id="ef857-138">Parameters</span></span>
* <span data-ttu-id="ef857-139">packageFullname：套件名稱</span><span class="sxs-lookup"><span data-stu-id="ef857-139">packageFullname : package name</span></span>
* <span data-ttu-id="ef857-140">檔案名：傾印檔案名</span><span class="sxs-lookup"><span data-stu-id="ef857-140">fileName : dump file name</span></span>

<span data-ttu-id="ef857-141">**/api/debug/dump/usermode/crashdump (取得)**</span><span class="sxs-lookup"><span data-stu-id="ef857-141">**/api/debug/dump/usermode/crashdump (GET)**</span></span>

<span data-ttu-id="ef857-142">捕獲側載應用程式的損毀傾印</span><span class="sxs-lookup"><span data-stu-id="ef857-142">Retrieves a crash dump for a sideloaded app</span></span>

<span data-ttu-id="ef857-143">參數</span><span class="sxs-lookup"><span data-stu-id="ef857-143">Parameters</span></span>
* <span data-ttu-id="ef857-144">packageFullname：套件名稱</span><span class="sxs-lookup"><span data-stu-id="ef857-144">packageFullname : package name</span></span>
* <span data-ttu-id="ef857-145">檔案名：傾印檔案名</span><span class="sxs-lookup"><span data-stu-id="ef857-145">fileName : dump file name</span></span>

<span data-ttu-id="ef857-146">傳回資料</span><span class="sxs-lookup"><span data-stu-id="ef857-146">Return data</span></span>
* <span data-ttu-id="ef857-147">傾印檔案。</span><span class="sxs-lookup"><span data-stu-id="ef857-147">Dump file.</span></span> <span data-ttu-id="ef857-148">使用 WinDbg 或 Visual Studio 檢查</span><span class="sxs-lookup"><span data-stu-id="ef857-148">Inspect with WinDbg or Visual Studio</span></span>

<span data-ttu-id="ef857-149">**/api/debug/dump/usermode/dumps (取得)**</span><span class="sxs-lookup"><span data-stu-id="ef857-149">**/api/debug/dump/usermode/dumps (GET)**</span></span>

<span data-ttu-id="ef857-150">傳回側載 apps 的所有損毀傾印清單</span><span class="sxs-lookup"><span data-stu-id="ef857-150">Returns list of all crash dumps for sideloaded apps</span></span>

<span data-ttu-id="ef857-151">傳回資料</span><span class="sxs-lookup"><span data-stu-id="ef857-151">Return data</span></span>
* <span data-ttu-id="ef857-152">每一端載入的應用程式損毀傾印清單</span><span class="sxs-lookup"><span data-stu-id="ef857-152">List of crash dumps per side loaded app</span></span>

## <a name="etw"></a><span data-ttu-id="ef857-153">ETW</span><span class="sxs-lookup"><span data-stu-id="ef857-153">ETW</span></span>

<span data-ttu-id="ef857-154">**/api/etw/providers (取得)**</span><span class="sxs-lookup"><span data-stu-id="ef857-154">**/api/etw/providers (GET)**</span></span>

<span data-ttu-id="ef857-155">列舉已註冊的提供者</span><span class="sxs-lookup"><span data-stu-id="ef857-155">Enumerates registered providers</span></span>

<span data-ttu-id="ef857-156">傳回資料</span><span class="sxs-lookup"><span data-stu-id="ef857-156">Return data</span></span>
* <span data-ttu-id="ef857-157">提供者清單、易記名稱和 GUID</span><span class="sxs-lookup"><span data-stu-id="ef857-157">List of providers, friendly name and GUID</span></span>

<span data-ttu-id="ef857-158">**/api/etw/session/realtime (GET/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="ef857-158">**/api/etw/session/realtime (GET/WebSocket)**</span></span>

<span data-ttu-id="ef857-159">建立即時 ETW 會話;在 websocket 上進行管理。</span><span class="sxs-lookup"><span data-stu-id="ef857-159">Creates a realtime ETW session; managed over a websocket.</span></span>

<span data-ttu-id="ef857-160">傳回資料</span><span class="sxs-lookup"><span data-stu-id="ef857-160">Return data</span></span>
* <span data-ttu-id="ef857-161">來自已啟用提供者的 ETW 事件</span><span class="sxs-lookup"><span data-stu-id="ef857-161">ETW events from the enabled providers</span></span>

## <a name="holographic-os"></a><span data-ttu-id="ef857-162">全像攝影版 OS</span><span class="sxs-lookup"><span data-stu-id="ef857-162">Holographic OS</span></span>

<span data-ttu-id="ef857-163">**/api/holographic/os/etw/customproviders (取得)**</span><span class="sxs-lookup"><span data-stu-id="ef857-163">**/api/holographic/os/etw/customproviders (GET)**</span></span>

<span data-ttu-id="ef857-164">傳回未向系統註冊的 HoloLens 特定 ETW 提供者清單</span><span class="sxs-lookup"><span data-stu-id="ef857-164">Returns a list of HoloLens specific ETW providers that are not registered with the system</span></span>

<span data-ttu-id="ef857-165">**/api/holographic/os/services (取得)**</span><span class="sxs-lookup"><span data-stu-id="ef857-165">**/api/holographic/os/services (GET)**</span></span>

<span data-ttu-id="ef857-166">傳回所有執行中之服務的狀態。</span><span class="sxs-lookup"><span data-stu-id="ef857-166">Returns the states of all services running.</span></span>

<span data-ttu-id="ef857-167">**/api/holographic/os/settings/ipd (取得)**</span><span class="sxs-lookup"><span data-stu-id="ef857-167">**/api/holographic/os/settings/ipd (GET)**</span></span>

<span data-ttu-id="ef857-168">取得儲存的 IPD (Interpupillary 距離) 以毫米為單位</span><span class="sxs-lookup"><span data-stu-id="ef857-168">Gets the stored IPD (Interpupillary distance) in millimeters</span></span>

<span data-ttu-id="ef857-169">**/api/holographic/os/settings/ipd (POST)**</span><span class="sxs-lookup"><span data-stu-id="ef857-169">**/api/holographic/os/settings/ipd (POST)**</span></span>

<span data-ttu-id="ef857-170">設定 IPD</span><span class="sxs-lookup"><span data-stu-id="ef857-170">Sets the IPD</span></span>

<span data-ttu-id="ef857-171">參數</span><span class="sxs-lookup"><span data-stu-id="ef857-171">Parameters</span></span>
* <span data-ttu-id="ef857-172">ipd：要設定的新 IPD 值（以毫米為單位）</span><span class="sxs-lookup"><span data-stu-id="ef857-172">ipd : New IPD value to be set in millimeters</span></span>

<span data-ttu-id="ef857-173">**/api/holographic/os/webmanagement/settings/HTTPs (取得)**</span><span class="sxs-lookup"><span data-stu-id="ef857-173">**/api/holographic/os/webmanagement/settings/https (GET)**</span></span>

<span data-ttu-id="ef857-174">取得裝置入口網站的 HTTPS 需求</span><span class="sxs-lookup"><span data-stu-id="ef857-174">Get HTTPS requirements for the Device Portal</span></span>

<span data-ttu-id="ef857-175">**/api/holographic/os/webmanagement/settings/HTTPs (POST)**</span><span class="sxs-lookup"><span data-stu-id="ef857-175">**/api/holographic/os/webmanagement/settings/https (POST)**</span></span>

<span data-ttu-id="ef857-176">設定裝置入口網站的 HTTPS 需求</span><span class="sxs-lookup"><span data-stu-id="ef857-176">Sets HTTPS requirements for the Device Portal</span></span>

<span data-ttu-id="ef857-177">參數</span><span class="sxs-lookup"><span data-stu-id="ef857-177">Parameters</span></span>
* <span data-ttu-id="ef857-178">必要：是、否或預設值</span><span class="sxs-lookup"><span data-stu-id="ef857-178">required : yes, no or default</span></span>

## <a name="holographic-perception"></a><span data-ttu-id="ef857-179">全像</span><span class="sxs-lookup"><span data-stu-id="ef857-179">Holographic Perception</span></span>

<span data-ttu-id="ef857-180">**/api/holographic/perception/client (GET/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="ef857-180">**/api/holographic/perception/client (GET/WebSocket)**</span></span>

<span data-ttu-id="ef857-181">接受 websocket 升級並執行感知用戶端，以 30 fps 的形式傳送更新。</span><span class="sxs-lookup"><span data-stu-id="ef857-181">Accepts websocket upgrades and runs a perception client that sends updates at 30 fps.</span></span>

<span data-ttu-id="ef857-182">參數</span><span class="sxs-lookup"><span data-stu-id="ef857-182">Parameters</span></span>
* <span data-ttu-id="ef857-183">clientmode：「作用中」會在無法被動建立時強制視覺化追蹤模式</span><span class="sxs-lookup"><span data-stu-id="ef857-183">clientmode: "active" forces visual tracking mode when it can't be established passively</span></span>

## <a name="holographic-thermal"></a><span data-ttu-id="ef857-184">全像熱</span><span class="sxs-lookup"><span data-stu-id="ef857-184">Holographic Thermal</span></span>

<span data-ttu-id="ef857-185">**/api/holographic/thermal/stage (取得)**</span><span class="sxs-lookup"><span data-stu-id="ef857-185">**/api/holographic/thermal/stage (GET)**</span></span>

<span data-ttu-id="ef857-186">取得裝置的熱階段 (0 正常、1暖、2關鍵) </span><span class="sxs-lookup"><span data-stu-id="ef857-186">Get the thermal stage of the device (0 normal, 1 warm, 2 critical)</span></span>

## <a name="map-manager"></a><span data-ttu-id="ef857-187">地圖管理員</span><span class="sxs-lookup"><span data-stu-id="ef857-187">Map Manager</span></span>

<span data-ttu-id="ef857-188">**/api/holographic/mapmanager/mapFiles (取得)**</span><span class="sxs-lookup"><span data-stu-id="ef857-188">**/api/holographic/mapmanager/mapFiles (GET)**</span></span>

<span data-ttu-id="ef857-189">取得可用對應檔 ( mapx) 的清單。</span><span class="sxs-lookup"><span data-stu-id="ef857-189">Gets the list of the available map files (.mapx).</span></span>

<span data-ttu-id="ef857-190">**/api/holographic/mapmanager/anchorFiles (取得)**</span><span class="sxs-lookup"><span data-stu-id="ef857-190">**/api/holographic/mapmanager/anchorFiles (GET)**</span></span>

<span data-ttu-id="ef857-191">取得可用錨定檔案 ( ancx) 的清單。</span><span class="sxs-lookup"><span data-stu-id="ef857-191">Gets the list of available anchor files (.ancx).</span></span>

<span data-ttu-id="ef857-192">**/api/holographic/mapmanager/srdbFiles (取得)**</span><span class="sxs-lookup"><span data-stu-id="ef857-192">**/api/holographic/mapmanager/srdbFiles (GET)**</span></span>

<span data-ttu-id="ef857-193">取得可用空間重建資料庫檔案 ( srdb) 的清單。</span><span class="sxs-lookup"><span data-stu-id="ef857-193">Gets the list of available spatial reconstruction database files (.srdb).</span></span>

<span data-ttu-id="ef857-194">**/api/holographic/mapmanager/getanchors (取得)**</span><span class="sxs-lookup"><span data-stu-id="ef857-194">**/api/holographic/mapmanager/getanchors (GET)**</span></span>

<span data-ttu-id="ef857-195">取得目前使用者的已保存錨點清單。</span><span class="sxs-lookup"><span data-stu-id="ef857-195">Gets the list of persisted anchors for the current user.</span></span> 

### <a name="downloaduploaddelete-files"></a><span data-ttu-id="ef857-196">下載/上傳/刪除檔案</span><span class="sxs-lookup"><span data-stu-id="ef857-196">Download/Upload/Delete Files</span></span>
<span data-ttu-id="ef857-197">**/api/holographic/mapmanager/download (取得)**</span><span class="sxs-lookup"><span data-stu-id="ef857-197">**/api/holographic/mapmanager/download (GET)**</span></span>

<span data-ttu-id="ef857-198">下載地圖、錨點或空間重建資料庫檔案。</span><span class="sxs-lookup"><span data-stu-id="ef857-198">Downloads a map, anchor, or spatial reconstruction database file.</span></span> <span data-ttu-id="ef857-199">檔案必須先前已上傳或匯出。</span><span class="sxs-lookup"><span data-stu-id="ef857-199">The file must have been previously uploaded or exported.</span></span>

<span data-ttu-id="ef857-200">參數</span><span class="sxs-lookup"><span data-stu-id="ef857-200">Parameters</span></span>
* <span data-ttu-id="ef857-201">檔案名：要下載的檔案名。</span><span class="sxs-lookup"><span data-stu-id="ef857-201">FileName: Name of file to download.</span></span>

<span data-ttu-id="ef857-202">範例：</span><span class="sxs-lookup"><span data-stu-id="ef857-202">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/download?FileName=" + spaceID)
```

<span data-ttu-id="ef857-203">**/api/holographic/mapmanager/upload (POST)**</span><span class="sxs-lookup"><span data-stu-id="ef857-203">**/api/holographic/mapmanager/upload (POST)**</span></span>

<span data-ttu-id="ef857-204">上傳地圖、錨點或空間重建資料庫檔案。</span><span class="sxs-lookup"><span data-stu-id="ef857-204">Uploads a map, anchor, or spatial reconstruction database file.</span></span> <span data-ttu-id="ef857-205">檔案上傳之後，稍後可以匯入以供系統使用。</span><span class="sxs-lookup"><span data-stu-id="ef857-205">Once a file is uploaded it can later be imported to be used by the system.</span></span>

<span data-ttu-id="ef857-206">參數</span><span class="sxs-lookup"><span data-stu-id="ef857-206">Parameters</span></span>
* <span data-ttu-id="ef857-207">file：要上傳之檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="ef857-207">file: Name of the file to upload.</span></span>

<span data-ttu-id="ef857-208">範例：</span><span class="sxs-lookup"><span data-stu-id="ef857-208">Example:</span></span>
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

<span data-ttu-id="ef857-209">**/api/holographic/mapmanager/delete (POST)**</span><span class="sxs-lookup"><span data-stu-id="ef857-209">**/api/holographic/mapmanager/delete (POST)**</span></span>

<span data-ttu-id="ef857-210">刪除地圖、錨點或空間重建資料庫檔案。</span><span class="sxs-lookup"><span data-stu-id="ef857-210">Deletes a map, anchor, or spatial reconstruction database file.</span></span> <span data-ttu-id="ef857-211">檔案必須先前已上傳或匯出。</span><span class="sxs-lookup"><span data-stu-id="ef857-211">The file must have been previously uploaded or exported.</span></span>

<span data-ttu-id="ef857-212">參數</span><span class="sxs-lookup"><span data-stu-id="ef857-212">Parameters</span></span>
* <span data-ttu-id="ef857-213">FileName：要刪除的檔案名。</span><span class="sxs-lookup"><span data-stu-id="ef857-213">FileName: Name of file to delete.</span></span>

<span data-ttu-id="ef857-214">範例：</span><span class="sxs-lookup"><span data-stu-id="ef857-214">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/delete?FileName=" + spaceID)
```

### <a name="export"></a><span data-ttu-id="ef857-215">匯出</span><span class="sxs-lookup"><span data-stu-id="ef857-215">Export</span></span>

<span data-ttu-id="ef857-216">**/api/holographic/mapmanager/export (POST)**</span><span class="sxs-lookup"><span data-stu-id="ef857-216">**/api/holographic/mapmanager/export (POST)**</span></span>

<span data-ttu-id="ef857-217">匯出系統目前正在使用的對應。</span><span class="sxs-lookup"><span data-stu-id="ef857-217">Exports the map currently in use by the system.</span></span> <span data-ttu-id="ef857-218">一旦匯出之後，即可加以下載。</span><span class="sxs-lookup"><span data-stu-id="ef857-218">Once exported, it can be downloaded.</span></span> 

<span data-ttu-id="ef857-219">範例：</span><span class="sxs-lookup"><span data-stu-id="ef857-219">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/export")
```

<span data-ttu-id="ef857-220">**/api/holographic/mapmanager/exportanchors (POST)**</span><span class="sxs-lookup"><span data-stu-id="ef857-220">**/api/holographic/mapmanager/exportanchors (POST)**</span></span>

<span data-ttu-id="ef857-221">匯出系統目前正在使用的對應。</span><span class="sxs-lookup"><span data-stu-id="ef857-221">Exports the map currently in use by the system.</span></span> <span data-ttu-id="ef857-222">一旦匯出之後，即可加以下載。</span><span class="sxs-lookup"><span data-stu-id="ef857-222">Once exported, it can be downloaded.</span></span> <span data-ttu-id="ef857-223">範例：</span><span class="sxs-lookup"><span data-stu-id="ef857-223">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/exportanchors")
```

<span data-ttu-id="ef857-224">**/api/holographic/mapmanager/exportmapandanchors (POST)**</span><span class="sxs-lookup"><span data-stu-id="ef857-224">**/api/holographic/mapmanager/exportmapandanchors (POST)**</span></span>

<span data-ttu-id="ef857-225">匯出系統目前正在使用的對應和錨點。</span><span class="sxs-lookup"><span data-stu-id="ef857-225">Exports the map and anchors currently in use by the system.</span></span> <span data-ttu-id="ef857-226">一旦匯出之後，即可加以下載。</span><span class="sxs-lookup"><span data-stu-id="ef857-226">Once are exported, they can be downloaded.</span></span> <span data-ttu-id="ef857-227">範例：</span><span class="sxs-lookup"><span data-stu-id="ef857-227">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/exportmapandanchors")
```

<span data-ttu-id="ef857-228">**/api/holographic/mapmanager/exportmapandspatialmappingdb (POST)**</span><span class="sxs-lookup"><span data-stu-id="ef857-228">**/api/holographic/mapmanager/exportmapandspatialmappingdb (POST)**</span></span>

<span data-ttu-id="ef857-229">匯出系統目前正在使用的地圖和空間重建資料庫。</span><span class="sxs-lookup"><span data-stu-id="ef857-229">Exports the map and spatial reconstruction database currently in use by the system.</span></span> <span data-ttu-id="ef857-230">一旦匯出之後，即可加以下載。</span><span class="sxs-lookup"><span data-stu-id="ef857-230">Once they are exported, they can be downloaded.</span></span> 

<span data-ttu-id="ef857-231">範例：</span><span class="sxs-lookup"><span data-stu-id="ef857-231">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/exportmapandspatialmappingdb")
```

### <a name="import"></a><span data-ttu-id="ef857-232">匯入</span><span class="sxs-lookup"><span data-stu-id="ef857-232">Import</span></span>

<span data-ttu-id="ef857-233">**/api/holographic/mapmanager/import (POST)**</span><span class="sxs-lookup"><span data-stu-id="ef857-233">**/api/holographic/mapmanager/import (POST)**</span></span>

<span data-ttu-id="ef857-234">向系統表示目前使用的對應。</span><span class="sxs-lookup"><span data-stu-id="ef857-234">Indicates to the system which map should be used be currently used.</span></span> <span data-ttu-id="ef857-235">可以在已匯出或已上傳的檔案上呼叫。</span><span class="sxs-lookup"><span data-stu-id="ef857-235">Can be called on files that have been exported or uploaded.</span></span>

<span data-ttu-id="ef857-236">參數</span><span class="sxs-lookup"><span data-stu-id="ef857-236">Parameters</span></span>
* <span data-ttu-id="ef857-237">FileName：要使用的對應名稱。</span><span class="sxs-lookup"><span data-stu-id="ef857-237">FileName: Name of the map to be used.</span></span> 

<span data-ttu-id="ef857-238">範例：</span><span class="sxs-lookup"><span data-stu-id="ef857-238">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/import?FileName=" + spaceID, function() { alert("Import was successful!"); })
```

<span data-ttu-id="ef857-239">**/api/holographic/mapmanager/importanchors (POST)**</span><span class="sxs-lookup"><span data-stu-id="ef857-239">**/api/holographic/mapmanager/importanchors (POST)**</span></span>

<span data-ttu-id="ef857-240">向系統表示目前使用的錨點。</span><span class="sxs-lookup"><span data-stu-id="ef857-240">Indicates to the system which anchors should be used be currently used.</span></span> <span data-ttu-id="ef857-241">可以在已匯出或已上傳的檔案上呼叫。</span><span class="sxs-lookup"><span data-stu-id="ef857-241">Can be called on files that have been exported or uploaded.</span></span>

<span data-ttu-id="ef857-242">參數</span><span class="sxs-lookup"><span data-stu-id="ef857-242">Parameters</span></span>
* <span data-ttu-id="ef857-243">FileName：要使用的錨點名稱。</span><span class="sxs-lookup"><span data-stu-id="ef857-243">FileName: Name of the anchors to be used.</span></span> 

<span data-ttu-id="ef857-244">範例：</span><span class="sxs-lookup"><span data-stu-id="ef857-244">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/import?FileName=" + spaceID, function() { alert("Import was successful!"); })
```

<span data-ttu-id="ef857-245">**/api/holographic/mapmanager/importspatialmappingdb (POST)**</span><span class="sxs-lookup"><span data-stu-id="ef857-245">**/api/holographic/mapmanager/importspatialmappingdb (POST)**</span></span>

<span data-ttu-id="ef857-246">向系統表示目前應使用的空間重建資料庫。</span><span class="sxs-lookup"><span data-stu-id="ef857-246">Indicates to the system which spatial reconstruction database should be used be currently used.</span></span> <span data-ttu-id="ef857-247">可以在已匯出或已上傳的檔案上呼叫。</span><span class="sxs-lookup"><span data-stu-id="ef857-247">Can be called on files that have been exported or uploaded.</span></span>

<span data-ttu-id="ef857-248">參數</span><span class="sxs-lookup"><span data-stu-id="ef857-248">Parameters</span></span>
* <span data-ttu-id="ef857-249">FileName：要使用之空間對應資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="ef857-249">FileName: Name of the spatial mapping db to be used.</span></span> 

<span data-ttu-id="ef857-250">範例：</span><span class="sxs-lookup"><span data-stu-id="ef857-250">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/import?FileName=" + spaceID, function() { alert("Import was successful!"); })
```

### <a name="other"></a><span data-ttu-id="ef857-251">其他</span><span class="sxs-lookup"><span data-stu-id="ef857-251">Other</span></span>

<span data-ttu-id="ef857-252">**/api/holographic/mapmanager/resetmapandanchorsandsrdb (POST)**</span><span class="sxs-lookup"><span data-stu-id="ef857-252">**/api/holographic/mapmanager/resetmapandanchorsandsrdb (POST)**</span></span>

<span data-ttu-id="ef857-253">重設對應、錨定和空間重建資料庫的系統。</span><span class="sxs-lookup"><span data-stu-id="ef857-253">Reset the system the map, anchors and spatial reconstruction database.</span></span>

<span data-ttu-id="ef857-254">範例：</span><span class="sxs-lookup"><span data-stu-id="ef857-254">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/resetmapandanchorsandsrdb")
```

<span data-ttu-id="ef857-255">**/api/holographic/mapmanager/status (取得)**</span><span class="sxs-lookup"><span data-stu-id="ef857-255">**/api/holographic/mapmanager/status (GET)**</span></span>

<span data-ttu-id="ef857-256">取得系統的狀態，包括上次匯入的對應、錨點和空間重建資料庫檔案。</span><span class="sxs-lookup"><span data-stu-id="ef857-256">Gets the status of the system, including which map, anchors, and spatial reconstruction database files that were last imported.</span></span> 


## <a name="mixed-reality-capture"></a><span data-ttu-id="ef857-257">混合實境擷取</span><span class="sxs-lookup"><span data-stu-id="ef857-257">Mixed Reality Capture</span></span>

<span data-ttu-id="ef857-258">**/api/holographic/mrc/file (取得)**</span><span class="sxs-lookup"><span data-stu-id="ef857-258">**/api/holographic/mrc/file (GET)**</span></span>

<span data-ttu-id="ef857-259">從裝置下載混合的實際檔案。</span><span class="sxs-lookup"><span data-stu-id="ef857-259">Downloads a mixed reality file from the device.</span></span> <span data-ttu-id="ef857-260">使用 op = 串流查詢參數進行串流。</span><span class="sxs-lookup"><span data-stu-id="ef857-260">Use op=stream query parameter for streaming.</span></span>

<span data-ttu-id="ef857-261">參數</span><span class="sxs-lookup"><span data-stu-id="ef857-261">Parameters</span></span>
* <span data-ttu-id="ef857-262">檔案名：要取得之影片檔案的名稱、hex64 編碼</span><span class="sxs-lookup"><span data-stu-id="ef857-262">filename : Name, hex64 encoded, of the video file to get</span></span>
* <span data-ttu-id="ef857-263">op：資料流程</span><span class="sxs-lookup"><span data-stu-id="ef857-263">op : stream</span></span>

<span data-ttu-id="ef857-264">**/api/holographic/mrc/file (刪除)**</span><span class="sxs-lookup"><span data-stu-id="ef857-264">**/api/holographic/mrc/file (DELETE)**</span></span>

<span data-ttu-id="ef857-265">從裝置刪除混合現實記錄。</span><span class="sxs-lookup"><span data-stu-id="ef857-265">Deletes a mixed reality recording from the device.</span></span>

<span data-ttu-id="ef857-266">參數</span><span class="sxs-lookup"><span data-stu-id="ef857-266">Parameters</span></span>
* <span data-ttu-id="ef857-267">檔案名：要刪除之檔案的名稱、hex64 編碼</span><span class="sxs-lookup"><span data-stu-id="ef857-267">filename : Name, hex64 encoded, of the file to delete</span></span>

<span data-ttu-id="ef857-268">**/api/holographic/mrc/files (取得)**</span><span class="sxs-lookup"><span data-stu-id="ef857-268">**/api/holographic/mrc/files (GET)**</span></span>

<span data-ttu-id="ef857-269">傳回儲存在裝置上的混合現實檔案清單</span><span class="sxs-lookup"><span data-stu-id="ef857-269">Returns the list of mixed reality files stored on the device</span></span>

<span data-ttu-id="ef857-270">**/api/holographic/mrc/photo (POST)**</span><span class="sxs-lookup"><span data-stu-id="ef857-270">**/api/holographic/mrc/photo (POST)**</span></span>

<span data-ttu-id="ef857-271">採用混合的現實照片，並在裝置上建立檔案</span><span class="sxs-lookup"><span data-stu-id="ef857-271">Takes a mixed reality photo and creates a file on the device</span></span>

<span data-ttu-id="ef857-272">參數</span><span class="sxs-lookup"><span data-stu-id="ef857-272">Parameters</span></span>
* <span data-ttu-id="ef857-273">hololens：抓取全像： true 或 false (預設為 false) </span><span class="sxs-lookup"><span data-stu-id="ef857-273">holo : capture holograms: true or false (defaults to false)</span></span>
* <span data-ttu-id="ef857-274">pv： capture PV 攝影機： true 或 false (預設為 false) </span><span class="sxs-lookup"><span data-stu-id="ef857-274">pv : capture PV camera: true or false (defaults to false)</span></span>
* <span data-ttu-id="ef857-275">RenderFromCamera： (只 HoloLens 2) 從相片/攝影機的觀點轉譯： true 或 false (預設為 true) </span><span class="sxs-lookup"><span data-stu-id="ef857-275">RenderFromCamera : (HoloLens 2 only) render from perspective of photo/video camera: true or false (defaults to true)</span></span>

<span data-ttu-id="ef857-276">**/api/holographic/mrc/settings (取得)**</span><span class="sxs-lookup"><span data-stu-id="ef857-276">**/api/holographic/mrc/settings (GET)**</span></span>

<span data-ttu-id="ef857-277">取得預設的混合現實捕獲設定</span><span class="sxs-lookup"><span data-stu-id="ef857-277">Gets the default mixed reality capture settings</span></span>

<span data-ttu-id="ef857-278">**/api/holographic/mrc/settings (POST)**</span><span class="sxs-lookup"><span data-stu-id="ef857-278">**/api/holographic/mrc/settings (POST)**</span></span>

<span data-ttu-id="ef857-279">設定預設的混合現實捕獲設定。</span><span class="sxs-lookup"><span data-stu-id="ef857-279">Sets the default mixed reality capture settings.</span></span>  <span data-ttu-id="ef857-280">其中某些設定會套用到系統的 MRC 照片和影片捕捉。</span><span class="sxs-lookup"><span data-stu-id="ef857-280">Some of these settings are applied to the system's MRC photo and video capture.</span></span>

<span data-ttu-id="ef857-281">**/api/holographic/mrc/status (取得)**</span><span class="sxs-lookup"><span data-stu-id="ef857-281">**/api/holographic/mrc/status (GET)**</span></span>

<span data-ttu-id="ef857-282">取得 Windows 裝置入口網站內混合現實捕捉的狀態。</span><span class="sxs-lookup"><span data-stu-id="ef857-282">Gets the state of mixed reality capture within the Windows Device Portal.</span></span>

<span data-ttu-id="ef857-283">\**_回應_* _</span><span class="sxs-lookup"><span data-stu-id="ef857-283">\**_Response_* _</span></span>

<span data-ttu-id="ef857-284">回應包含 JSON 屬性，指出 Windows 裝置入口網站是否錄製影片。</span><span class="sxs-lookup"><span data-stu-id="ef857-284">The response contains a JSON property indicating if Windows Device Portal is recording video or not.</span></span>

``` javascript
{"IsRecording" : boolean}
```

<span data-ttu-id="ef857-285">_ */api/holographic/mrc/thumbnail (取得)*\*</span><span class="sxs-lookup"><span data-stu-id="ef857-285">_ */api/holographic/mrc/thumbnail (GET)*\*</span></span>

<span data-ttu-id="ef857-286">取得指定檔案的縮圖影像。</span><span class="sxs-lookup"><span data-stu-id="ef857-286">Gets the thumbnail image for the specified file.</span></span>

<span data-ttu-id="ef857-287">參數</span><span class="sxs-lookup"><span data-stu-id="ef857-287">Parameters</span></span>
* <span data-ttu-id="ef857-288">檔案名：已要求縮圖的檔案名、hex64 編碼的檔案</span><span class="sxs-lookup"><span data-stu-id="ef857-288">filename: Name, hex64 encoded, of the file for which the thumbnail is being requested</span></span>

<span data-ttu-id="ef857-289">**/api/holographic/mrc/video/control/start (POST)**</span><span class="sxs-lookup"><span data-stu-id="ef857-289">**/api/holographic/mrc/video/control/start (POST)**</span></span>

<span data-ttu-id="ef857-290">開始混合現實記錄</span><span class="sxs-lookup"><span data-stu-id="ef857-290">Starts a mixed reality recording</span></span>

<span data-ttu-id="ef857-291">參數</span><span class="sxs-lookup"><span data-stu-id="ef857-291">Parameters</span></span>
* <span data-ttu-id="ef857-292">hololens：抓取全像： true 或 false (預設為 false) </span><span class="sxs-lookup"><span data-stu-id="ef857-292">holo : capture holograms: true or false (defaults to false)</span></span>
* <span data-ttu-id="ef857-293">pv： capture PV 攝影機： true 或 false (預設為 false) </span><span class="sxs-lookup"><span data-stu-id="ef857-293">pv : capture PV camera: true or false (defaults to false)</span></span>
* <span data-ttu-id="ef857-294">mic： capture 麥克風： true 或 false (預設為 false) </span><span class="sxs-lookup"><span data-stu-id="ef857-294">mic : capture microphone: true or false (defaults to false)</span></span>
* <span data-ttu-id="ef857-295">回送： capture app audio： true 或 false (預設為 false) </span><span class="sxs-lookup"><span data-stu-id="ef857-295">loopback : capture app audio: true or false (defaults to false)</span></span>
* <span data-ttu-id="ef857-296">RenderFromCamera： (只 HoloLens 2) 從相片/攝影機的觀點轉譯： true 或 false (預設為 true) </span><span class="sxs-lookup"><span data-stu-id="ef857-296">RenderFromCamera : (HoloLens 2 only) render from perspective of photo/video camera: true or false (defaults to true)</span></span>
* <span data-ttu-id="ef857-297">vstab： (只 HoloLens 2) 啟用影片穩定： true 或 false (預設為 true) </span><span class="sxs-lookup"><span data-stu-id="ef857-297">vstab : (HoloLens 2 only) enable video stabilization: true or false (defaults to true)</span></span>
* <span data-ttu-id="ef857-298">vstabbuffer： (只 HoloLens 2) video 穩定緩衝區延遲：0到30個畫面格 (預設為15個畫面格) </span><span class="sxs-lookup"><span data-stu-id="ef857-298">vstabbuffer: (HoloLens 2 only) video stabilization buffer latency: 0 to 30 frames (defaults to 15 frames)</span></span>

<span data-ttu-id="ef857-299">**/api/holographic/mrc/video/control/stop (POST)**</span><span class="sxs-lookup"><span data-stu-id="ef857-299">**/api/holographic/mrc/video/control/stop (POST)**</span></span>

<span data-ttu-id="ef857-300">停止目前的混合現實記錄</span><span class="sxs-lookup"><span data-stu-id="ef857-300">Stops the current mixed reality recording</span></span>

## <a name="mixed-reality-streaming"></a><span data-ttu-id="ef857-301">混合的現實串流</span><span class="sxs-lookup"><span data-stu-id="ef857-301">Mixed Reality Streaming</span></span>

> [!CAUTION]
> <span data-ttu-id="ef857-302">由於回送隔離的原因，您無法從裝置上的應用程式內連線到混合現實串流。</span><span class="sxs-lookup"><span data-stu-id="ef857-302">Because of loopback isolation, you can't connect to Mixed Reality Streaming from inside an app on a device.</span></span>

<span data-ttu-id="ef857-303">HoloLens 透過區塊下載分散的數量，支援混合現實的即時預覽。</span><span class="sxs-lookup"><span data-stu-id="ef857-303">HoloLens supports live preview of mixed reality via chunked download of a fragmented mp4.</span></span>

<span data-ttu-id="ef857-304">混合的現實資料流程共用一組相同的參數來控制所要捕獲的內容：</span><span class="sxs-lookup"><span data-stu-id="ef857-304">Mixed reality streams share the same set of parameters to control what is captured:</span></span>
* <span data-ttu-id="ef857-305">hololens：抓取全像： true 或 false</span><span class="sxs-lookup"><span data-stu-id="ef857-305">holo : capture holograms: true or false</span></span>
* <span data-ttu-id="ef857-306">pv： capture PV 攝影機： true 或 false</span><span class="sxs-lookup"><span data-stu-id="ef857-306">pv : capture PV camera: true or false</span></span>
* <span data-ttu-id="ef857-307">mic： capture 麥克風： true 或 false</span><span class="sxs-lookup"><span data-stu-id="ef857-307">mic : capture microphone: true or false</span></span>
* <span data-ttu-id="ef857-308">回送：捕捉應用程式音訊： true 或 false</span><span class="sxs-lookup"><span data-stu-id="ef857-308">loopback : capture app audio: true or false</span></span>

<span data-ttu-id="ef857-309">如果未指定這些任何一項：將會捕捉全像照片、相片/攝影機和應用程式音訊</span><span class="sxs-lookup"><span data-stu-id="ef857-309">If none of these are specified: holograms, photo/video camera, and app audio will be captured</span></span><br>
<span data-ttu-id="ef857-310">如果有指定任何參數：未指定的參數會預設為 false</span><span class="sxs-lookup"><span data-stu-id="ef857-310">If any are specified: the unspecified parameters will default to false</span></span>

<span data-ttu-id="ef857-311"> (只 HoloLens 2) 的選擇性參數</span><span class="sxs-lookup"><span data-stu-id="ef857-311">Optional parameters (HoloLens 2 only)</span></span>
* <span data-ttu-id="ef857-312">RenderFromCamera：從相片/攝影機的觀點來呈現： true 或 false (預設為 true) </span><span class="sxs-lookup"><span data-stu-id="ef857-312">RenderFromCamera : render from perspective of photo/video camera: true or false (defaults to true)</span></span>
* <span data-ttu-id="ef857-313">vstab：啟用影片穩定： true 或 false (預設為 false) </span><span class="sxs-lookup"><span data-stu-id="ef857-313">vstab : enable video stabilization: true or false (defaults to false)</span></span>
* <span data-ttu-id="ef857-314">vstabbuffer：影片穩定緩衝區延遲：0到30個畫面格 (預設為15個畫面格) </span><span class="sxs-lookup"><span data-stu-id="ef857-314">vstabbuffer: video stabilization buffer latency: 0 to 30 frames (defaults to 15 frames)</span></span>

<span data-ttu-id="ef857-315">**/api/holographic/stream/live.mp4 (取得)**</span><span class="sxs-lookup"><span data-stu-id="ef857-315">**/api/holographic/stream/live.mp4 (GET)**</span></span>

<span data-ttu-id="ef857-316">1280x720p 30fps 5Mbit 串流。</span><span class="sxs-lookup"><span data-stu-id="ef857-316">A 1280x720p 30fps 5Mbit stream.</span></span>

<span data-ttu-id="ef857-317">**/api/holographic/stream/live_high.mp4 (取得)**</span><span class="sxs-lookup"><span data-stu-id="ef857-317">**/api/holographic/stream/live_high.mp4 (GET)**</span></span>

<span data-ttu-id="ef857-318">1280x720p 30fps 5Mbit 串流。</span><span class="sxs-lookup"><span data-stu-id="ef857-318">A 1280x720p 30fps 5Mbit stream.</span></span>

<span data-ttu-id="ef857-319">**/api/holographic/stream/live_med.mp4 (取得)**</span><span class="sxs-lookup"><span data-stu-id="ef857-319">**/api/holographic/stream/live_med.mp4 (GET)**</span></span>

<span data-ttu-id="ef857-320">854x480p 30fps 2.5 Mbit 串流。</span><span class="sxs-lookup"><span data-stu-id="ef857-320">A 854x480p 30fps 2.5Mbit stream.</span></span>

<span data-ttu-id="ef857-321">**/api/holographic/stream/live_low.mp4 (取得)**</span><span class="sxs-lookup"><span data-stu-id="ef857-321">**/api/holographic/stream/live_low.mp4 (GET)**</span></span>

<span data-ttu-id="ef857-322">428x240p 15fps 0.6 Mbit 串流。</span><span class="sxs-lookup"><span data-stu-id="ef857-322">A 428x240p 15fps 0.6Mbit stream.</span></span>

## <a name="networking"></a><span data-ttu-id="ef857-323">網路</span><span class="sxs-lookup"><span data-stu-id="ef857-323">Networking</span></span>

<span data-ttu-id="ef857-324">**/api/networking/ipconfig (取得)**</span><span class="sxs-lookup"><span data-stu-id="ef857-324">**/api/networking/ipconfig (GET)**</span></span>

<span data-ttu-id="ef857-325">取得目前的 ip 設定</span><span class="sxs-lookup"><span data-stu-id="ef857-325">Gets the current ip configuration</span></span>

## <a name="os-information"></a><span data-ttu-id="ef857-326">作業系統資訊</span><span class="sxs-lookup"><span data-stu-id="ef857-326">OS Information</span></span>

<span data-ttu-id="ef857-327">**/api/os/info (取得)**</span><span class="sxs-lookup"><span data-stu-id="ef857-327">**/api/os/info (GET)**</span></span>

<span data-ttu-id="ef857-328">取得作業系統資訊</span><span class="sxs-lookup"><span data-stu-id="ef857-328">Gets operating system information</span></span>

<span data-ttu-id="ef857-329">**/api/os/machinename (取得)**</span><span class="sxs-lookup"><span data-stu-id="ef857-329">**/api/os/machinename (GET)**</span></span>

<span data-ttu-id="ef857-330">取得電腦名稱稱</span><span class="sxs-lookup"><span data-stu-id="ef857-330">Gets the machine name</span></span>

<span data-ttu-id="ef857-331">**/api/os/machinename (POST)**</span><span class="sxs-lookup"><span data-stu-id="ef857-331">**/api/os/machinename (POST)**</span></span>

<span data-ttu-id="ef857-332">設定電腦名稱稱</span><span class="sxs-lookup"><span data-stu-id="ef857-332">Sets the machine name</span></span>

<span data-ttu-id="ef857-333">參數</span><span class="sxs-lookup"><span data-stu-id="ef857-333">Parameters</span></span>
* <span data-ttu-id="ef857-334">名稱：新電腦名稱稱、hex64 編碼、設定為</span><span class="sxs-lookup"><span data-stu-id="ef857-334">name : New machine name, hex64 encoded, to set to</span></span>

## <a name="perception-simulation-control"></a><span data-ttu-id="ef857-335">認知模擬控制項</span><span class="sxs-lookup"><span data-stu-id="ef857-335">Perception Simulation Control</span></span>

<span data-ttu-id="ef857-336">**/api/holographic/simulation/control/mode (取得)**</span><span class="sxs-lookup"><span data-stu-id="ef857-336">**/api/holographic/simulation/control/mode (GET)**</span></span>

<span data-ttu-id="ef857-337">取得模擬模式</span><span class="sxs-lookup"><span data-stu-id="ef857-337">Get the simulation mode</span></span>

<span data-ttu-id="ef857-338">**/api/holographic/simulation/control/mode (POST)**</span><span class="sxs-lookup"><span data-stu-id="ef857-338">**/api/holographic/simulation/control/mode (POST)**</span></span>

<span data-ttu-id="ef857-339">設定模擬模式</span><span class="sxs-lookup"><span data-stu-id="ef857-339">Set the simulation mode</span></span>

<span data-ttu-id="ef857-340">參數</span><span class="sxs-lookup"><span data-stu-id="ef857-340">Parameters</span></span>
* <span data-ttu-id="ef857-341">模式：模擬模式：預設、模擬、遠端、舊版</span><span class="sxs-lookup"><span data-stu-id="ef857-341">mode : simulation mode: default, simulation, remote, legacy</span></span>

<span data-ttu-id="ef857-342">**/api/holographic/simulation/control/stream (刪除)**</span><span class="sxs-lookup"><span data-stu-id="ef857-342">**/api/holographic/simulation/control/stream (DELETE)**</span></span>

<span data-ttu-id="ef857-343">刪除控制資料流程。</span><span class="sxs-lookup"><span data-stu-id="ef857-343">Delete a control stream.</span></span>

<span data-ttu-id="ef857-344">**/api/holographic/simulation/control/stream (GET/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="ef857-344">**/api/holographic/simulation/control/stream (GET/WebSocket)**</span></span>

<span data-ttu-id="ef857-345">開啟控制項資料流程的 web 通訊端連接。</span><span class="sxs-lookup"><span data-stu-id="ef857-345">Open a web socket connection for a control stream.</span></span>

<span data-ttu-id="ef857-346">**/api/holographic/simulation/control/stream (POST)**</span><span class="sxs-lookup"><span data-stu-id="ef857-346">**/api/holographic/simulation/control/stream (POST)**</span></span>

<span data-ttu-id="ef857-347">建立控制項資料流程 (需要優先權) 或將資料張貼至建立的資料流程 (streamId 必要) 。</span><span class="sxs-lookup"><span data-stu-id="ef857-347">Create a control stream (priority is required) or post data to a created stream (streamId required).</span></span> <span data-ttu-id="ef857-348">張貼的資料應為 ' application/八進位-stream ' 類型。</span><span class="sxs-lookup"><span data-stu-id="ef857-348">Posted data is expected to be of type 'application/octet-stream'.</span></span>

<span data-ttu-id="ef857-349">**/api/holographic/simulation/display/stream (GET/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="ef857-349">**/api/holographic/simulation/display/stream (GET/WebSocket)**</span></span>

<span data-ttu-id="ef857-350">要求模擬影片串流，其中包含在「模擬」模式中呈現給系統顯示的內容。</span><span class="sxs-lookup"><span data-stu-id="ef857-350">Request a simulation video stream containing the content rendered to the system display when in 'Simulation' mode.</span></span>  <span data-ttu-id="ef857-351">一開始會傳送簡單的格式描述元標頭，後面接著 h.264 編碼的材質，每個標頭前面都有一個標頭，表示眼睛索引和材質大小。</span><span class="sxs-lookup"><span data-stu-id="ef857-351">A simple format descriptor header will be sent initially, followed by H.264-encoded textures, each preceded by a header indicating the eye index and texture size.</span></span>

## <a name="perception-simulation-playback"></a><span data-ttu-id="ef857-352">感知模擬播放</span><span class="sxs-lookup"><span data-stu-id="ef857-352">Perception Simulation Playback</span></span>

<span data-ttu-id="ef857-353">**/api/holographic/simulation/playback/file (刪除)**</span><span class="sxs-lookup"><span data-stu-id="ef857-353">**/api/holographic/simulation/playback/file (DELETE)**</span></span>

<span data-ttu-id="ef857-354">刪除錄製。</span><span class="sxs-lookup"><span data-stu-id="ef857-354">Delete a recording.</span></span>

<span data-ttu-id="ef857-355">參數</span><span class="sxs-lookup"><span data-stu-id="ef857-355">Parameters</span></span>
* <span data-ttu-id="ef857-356">錄製：要刪除的記錄名稱。</span><span class="sxs-lookup"><span data-stu-id="ef857-356">recording : Name of recording to delete.</span></span>

<span data-ttu-id="ef857-357">**/api/holographic/simulation/playback/file (POST)**</span><span class="sxs-lookup"><span data-stu-id="ef857-357">**/api/holographic/simulation/playback/file (POST)**</span></span>

<span data-ttu-id="ef857-358">上傳錄製。</span><span class="sxs-lookup"><span data-stu-id="ef857-358">Upload a recording.</span></span>

<span data-ttu-id="ef857-359">**/api/holographic/simulation/playback/files (取得)**</span><span class="sxs-lookup"><span data-stu-id="ef857-359">**/api/holographic/simulation/playback/files (GET)**</span></span>

<span data-ttu-id="ef857-360">取得所有錄製。</span><span class="sxs-lookup"><span data-stu-id="ef857-360">Get all recordings.</span></span>

<span data-ttu-id="ef857-361">**/api/holographic/simulation/playback/session (取得)**</span><span class="sxs-lookup"><span data-stu-id="ef857-361">**/api/holographic/simulation/playback/session (GET)**</span></span>

<span data-ttu-id="ef857-362">取得錄製的目前播放狀態。</span><span class="sxs-lookup"><span data-stu-id="ef857-362">Get the current playback state of a recording.</span></span>

<span data-ttu-id="ef857-363">參數</span><span class="sxs-lookup"><span data-stu-id="ef857-363">Parameters</span></span>
* <span data-ttu-id="ef857-364">錄製：錄製的名稱。</span><span class="sxs-lookup"><span data-stu-id="ef857-364">recording : Name of recording.</span></span>

<span data-ttu-id="ef857-365">**/api/holographic/simulation/playback/session/file (刪除)**</span><span class="sxs-lookup"><span data-stu-id="ef857-365">**/api/holographic/simulation/playback/session/file (DELETE)**</span></span>

<span data-ttu-id="ef857-366">卸載錄製。</span><span class="sxs-lookup"><span data-stu-id="ef857-366">Unload a recording.</span></span>

<span data-ttu-id="ef857-367">參數</span><span class="sxs-lookup"><span data-stu-id="ef857-367">Parameters</span></span>
* <span data-ttu-id="ef857-368">記錄：要卸載的記錄名稱。</span><span class="sxs-lookup"><span data-stu-id="ef857-368">recording : Name of recording to unload.</span></span>

<span data-ttu-id="ef857-369">**/api/holographic/simulation/playback/session/file (POST)**</span><span class="sxs-lookup"><span data-stu-id="ef857-369">**/api/holographic/simulation/playback/session/file (POST)**</span></span>

<span data-ttu-id="ef857-370">載入錄製。</span><span class="sxs-lookup"><span data-stu-id="ef857-370">Load a recording.</span></span>

<span data-ttu-id="ef857-371">參數</span><span class="sxs-lookup"><span data-stu-id="ef857-371">Parameters</span></span>
* <span data-ttu-id="ef857-372">記錄：要載入的記錄名稱。</span><span class="sxs-lookup"><span data-stu-id="ef857-372">recording : Name of recording to load.</span></span>

<span data-ttu-id="ef857-373">**/api/holographic/simulation/playback/session/files (取得)**</span><span class="sxs-lookup"><span data-stu-id="ef857-373">**/api/holographic/simulation/playback/session/files (GET)**</span></span>

<span data-ttu-id="ef857-374">取得所有載入的記錄。</span><span class="sxs-lookup"><span data-stu-id="ef857-374">Get all loaded recordings.</span></span>

<span data-ttu-id="ef857-375">**/api/holographic/simulation/playback/session/pause (POST)**</span><span class="sxs-lookup"><span data-stu-id="ef857-375">**/api/holographic/simulation/playback/session/pause (POST)**</span></span>

<span data-ttu-id="ef857-376">暫停錄製。</span><span class="sxs-lookup"><span data-stu-id="ef857-376">Pause a recording.</span></span>

<span data-ttu-id="ef857-377">參數</span><span class="sxs-lookup"><span data-stu-id="ef857-377">Parameters</span></span>
* <span data-ttu-id="ef857-378">錄製：錄製的名稱。</span><span class="sxs-lookup"><span data-stu-id="ef857-378">recording : Name of recording.</span></span>

<span data-ttu-id="ef857-379">**/api/holographic/simulation/playback/session/play (POST)**</span><span class="sxs-lookup"><span data-stu-id="ef857-379">**/api/holographic/simulation/playback/session/play (POST)**</span></span>

<span data-ttu-id="ef857-380">播放錄製。</span><span class="sxs-lookup"><span data-stu-id="ef857-380">Play a recording.</span></span>

<span data-ttu-id="ef857-381">參數</span><span class="sxs-lookup"><span data-stu-id="ef857-381">Parameters</span></span>
* <span data-ttu-id="ef857-382">錄製：錄製的名稱。</span><span class="sxs-lookup"><span data-stu-id="ef857-382">recording : Name of recording.</span></span>

<span data-ttu-id="ef857-383">**/api/holographic/simulation/playback/session/stop (POST)**</span><span class="sxs-lookup"><span data-stu-id="ef857-383">**/api/holographic/simulation/playback/session/stop (POST)**</span></span>

<span data-ttu-id="ef857-384">停止錄製。</span><span class="sxs-lookup"><span data-stu-id="ef857-384">Stop a recording.</span></span>

<span data-ttu-id="ef857-385">參數</span><span class="sxs-lookup"><span data-stu-id="ef857-385">Parameters</span></span>
* <span data-ttu-id="ef857-386">錄製：錄製的名稱。</span><span class="sxs-lookup"><span data-stu-id="ef857-386">recording : Name of recording.</span></span>

<span data-ttu-id="ef857-387">**/api/holographic/simulation/playback/session/types (取得)**</span><span class="sxs-lookup"><span data-stu-id="ef857-387">**/api/holographic/simulation/playback/session/types (GET)**</span></span>

<span data-ttu-id="ef857-388">取得載入錄製中的資料類型。</span><span class="sxs-lookup"><span data-stu-id="ef857-388">Get the types of data in a loaded recording.</span></span>

<span data-ttu-id="ef857-389">參數</span><span class="sxs-lookup"><span data-stu-id="ef857-389">Parameters</span></span>
* <span data-ttu-id="ef857-390">錄製：錄製的名稱。</span><span class="sxs-lookup"><span data-stu-id="ef857-390">recording : Name of recording.</span></span>

## <a name="perception-simulation-recording"></a><span data-ttu-id="ef857-391">感知模擬錄製</span><span class="sxs-lookup"><span data-stu-id="ef857-391">Perception Simulation Recording</span></span>

<span data-ttu-id="ef857-392">**/api/holographic/simulation/recording/start (POST)**</span><span class="sxs-lookup"><span data-stu-id="ef857-392">**/api/holographic/simulation/recording/start (POST)**</span></span>

<span data-ttu-id="ef857-393">開始錄製。</span><span class="sxs-lookup"><span data-stu-id="ef857-393">Start a recording.</span></span> <span data-ttu-id="ef857-394">一次只能有一個作用中的記錄。</span><span class="sxs-lookup"><span data-stu-id="ef857-394">Only a single recording can be active at once.</span></span> <span data-ttu-id="ef857-395">必須設定 head、雙手、spatialMapping 或環境之一。</span><span class="sxs-lookup"><span data-stu-id="ef857-395">One of head, hands, spatialMapping or environment must be set.</span></span>

<span data-ttu-id="ef857-396">參數</span><span class="sxs-lookup"><span data-stu-id="ef857-396">Parameters</span></span>
* <span data-ttu-id="ef857-397">head：設定為1以記錄 head 資料。</span><span class="sxs-lookup"><span data-stu-id="ef857-397">head : Set to 1 to record head data.</span></span>
* <span data-ttu-id="ef857-398">雙手：設定為1以記錄手資料。</span><span class="sxs-lookup"><span data-stu-id="ef857-398">hands : Set to 1 to record hand data.</span></span>
* <span data-ttu-id="ef857-399">spatialMapping：設定為1以記錄空間對應。</span><span class="sxs-lookup"><span data-stu-id="ef857-399">spatialMapping : Set to 1 to record spatial mapping.</span></span>
* <span data-ttu-id="ef857-400">環境：設定為1以記錄環境資料。</span><span class="sxs-lookup"><span data-stu-id="ef857-400">environment : Set to 1 to record environment data.</span></span>
* <span data-ttu-id="ef857-401">名稱：錄製的名稱。</span><span class="sxs-lookup"><span data-stu-id="ef857-401">name : Name of the recording.</span></span>
* <span data-ttu-id="ef857-402">singleSpatialMappingFrame：設定為1只記錄單一空間對應框架。</span><span class="sxs-lookup"><span data-stu-id="ef857-402">singleSpatialMappingFrame : Set to 1 to record only a single spatial mapping frame.</span></span>

<span data-ttu-id="ef857-403">**/api/holographic/simulation/recording/status (取得)**</span><span class="sxs-lookup"><span data-stu-id="ef857-403">**/api/holographic/simulation/recording/status (GET)**</span></span>

<span data-ttu-id="ef857-404">取得錄製狀態。</span><span class="sxs-lookup"><span data-stu-id="ef857-404">Get recording state.</span></span>

<span data-ttu-id="ef857-405">**/api/holographic/simulation/recording/stop (取得)**</span><span class="sxs-lookup"><span data-stu-id="ef857-405">**/api/holographic/simulation/recording/stop (GET)**</span></span>

<span data-ttu-id="ef857-406">停止目前的錄製。</span><span class="sxs-lookup"><span data-stu-id="ef857-406">Stop the current recording.</span></span> <span data-ttu-id="ef857-407">記錄會以檔案的形式傳回。</span><span class="sxs-lookup"><span data-stu-id="ef857-407">Recording will be returned as a file.</span></span>

## <a name="performance-data"></a><span data-ttu-id="ef857-408">效能資料</span><span class="sxs-lookup"><span data-stu-id="ef857-408">Performance data</span></span>

<span data-ttu-id="ef857-409">**/api/resourcemanager/processes (取得)**</span><span class="sxs-lookup"><span data-stu-id="ef857-409">**/api/resourcemanager/processes (GET)**</span></span>

<span data-ttu-id="ef857-410">傳回執行中進程的清單，並提供詳細資料</span><span class="sxs-lookup"><span data-stu-id="ef857-410">Returns the list of running processes with details</span></span>

<span data-ttu-id="ef857-411">傳回資料</span><span class="sxs-lookup"><span data-stu-id="ef857-411">Return data</span></span>
* <span data-ttu-id="ef857-412">JSON 與進程清單以及每個進程的詳細資料</span><span class="sxs-lookup"><span data-stu-id="ef857-412">JSON with list of processes and details for each process</span></span>

<span data-ttu-id="ef857-413">**/api/resourcemanager/systemperf (取得)**</span><span class="sxs-lookup"><span data-stu-id="ef857-413">**/api/resourcemanager/systemperf (GET)**</span></span>

<span data-ttu-id="ef857-414">傳回系統效能統計資料 (i/o 讀取/寫入、記憶體統計資料等。</span><span class="sxs-lookup"><span data-stu-id="ef857-414">Returns system perf statistics (I/O read/write, memory stats etc.</span></span>

<span data-ttu-id="ef857-415">傳回資料</span><span class="sxs-lookup"><span data-stu-id="ef857-415">Return data</span></span>
* <span data-ttu-id="ef857-416">具有系統資訊的 JSON： CPU、GPU、記憶體、網路、IO</span><span class="sxs-lookup"><span data-stu-id="ef857-416">JSON with system information: CPU, GPU, Memory, Network, IO</span></span>

## <a name="power"></a><span data-ttu-id="ef857-417">電源</span><span class="sxs-lookup"><span data-stu-id="ef857-417">Power</span></span>

<span data-ttu-id="ef857-418">**/api/power/battery (取得)**</span><span class="sxs-lookup"><span data-stu-id="ef857-418">**/api/power/battery (GET)**</span></span>

<span data-ttu-id="ef857-419">取得目前的電池狀態</span><span class="sxs-lookup"><span data-stu-id="ef857-419">Gets the current battery state</span></span>

<span data-ttu-id="ef857-420">**/api/power/state (取得)**</span><span class="sxs-lookup"><span data-stu-id="ef857-420">**/api/power/state (GET)**</span></span>

<span data-ttu-id="ef857-421">檢查系統是否處於低電源狀態</span><span class="sxs-lookup"><span data-stu-id="ef857-421">Checks if the system is in a low power state</span></span>

## <a name="remote-control"></a><span data-ttu-id="ef857-422">遠端控制</span><span class="sxs-lookup"><span data-stu-id="ef857-422">Remote Control</span></span>

<span data-ttu-id="ef857-423">**/api/control/restart (POST)**</span><span class="sxs-lookup"><span data-stu-id="ef857-423">**/api/control/restart (POST)**</span></span>

<span data-ttu-id="ef857-424">重新開機目標裝置</span><span class="sxs-lookup"><span data-stu-id="ef857-424">Restarts the target device</span></span>

<span data-ttu-id="ef857-425">**/api/control/shutdown (POST)**</span><span class="sxs-lookup"><span data-stu-id="ef857-425">**/api/control/shutdown (POST)**</span></span>

<span data-ttu-id="ef857-426">關閉目標裝置</span><span class="sxs-lookup"><span data-stu-id="ef857-426">Shuts down the target device</span></span>

## <a name="task-manager"></a><span data-ttu-id="ef857-427">工作管理員</span><span class="sxs-lookup"><span data-stu-id="ef857-427">Task Manager</span></span>

<span data-ttu-id="ef857-428">**/api/taskmanager/app (刪除)**</span><span class="sxs-lookup"><span data-stu-id="ef857-428">**/api/taskmanager/app (DELETE)**</span></span>

<span data-ttu-id="ef857-429">停止新式應用程式</span><span class="sxs-lookup"><span data-stu-id="ef857-429">Stops a modern app</span></span>

<span data-ttu-id="ef857-430">參數</span><span class="sxs-lookup"><span data-stu-id="ef857-430">Parameters</span></span>
* <span data-ttu-id="ef857-431">封裝：應用程式套件的完整名稱，hex64 編碼</span><span class="sxs-lookup"><span data-stu-id="ef857-431">package : Full name of the app package, hex64 encoded</span></span>
* <span data-ttu-id="ef857-432">forcestop：強制所有進程停止 (= 是) </span><span class="sxs-lookup"><span data-stu-id="ef857-432">forcestop : Force all processes to stop (=yes)</span></span>

<span data-ttu-id="ef857-433">**/api/taskmanager/app (POST)**</span><span class="sxs-lookup"><span data-stu-id="ef857-433">**/api/taskmanager/app (POST)**</span></span>

<span data-ttu-id="ef857-434">啟動新式應用程式</span><span class="sxs-lookup"><span data-stu-id="ef857-434">Starts a modern app</span></span>

<span data-ttu-id="ef857-435">參數</span><span class="sxs-lookup"><span data-stu-id="ef857-435">Parameters</span></span>
* <span data-ttu-id="ef857-436">appid：要啟動的應用程式 PRAID，hex64 編碼</span><span class="sxs-lookup"><span data-stu-id="ef857-436">appid : PRAID of app to start, hex64 encoded</span></span>
* <span data-ttu-id="ef857-437">封裝：應用程式套件的完整名稱，hex64 編碼</span><span class="sxs-lookup"><span data-stu-id="ef857-437">package : Full name of the app package, hex64 encoded</span></span>

## <a name="wifi-management"></a><span data-ttu-id="ef857-438">WiFi 管理</span><span class="sxs-lookup"><span data-stu-id="ef857-438">WiFi Management</span></span>

<span data-ttu-id="ef857-439">**/api/wifi/interfaces (取得)**</span><span class="sxs-lookup"><span data-stu-id="ef857-439">**/api/wifi/interfaces (GET)**</span></span>

<span data-ttu-id="ef857-440">列舉無線網路介面</span><span class="sxs-lookup"><span data-stu-id="ef857-440">Enumerates wireless network interfaces</span></span>

<span data-ttu-id="ef857-441">傳回資料</span><span class="sxs-lookup"><span data-stu-id="ef857-441">Return data</span></span>
* <span data-ttu-id="ef857-442">具有詳細資料 (GUID、描述等 ) 的無線介面清單</span><span class="sxs-lookup"><span data-stu-id="ef857-442">List of wireless interfaces with details (GUID, description etc.)</span></span>

<span data-ttu-id="ef857-443">**/api/wifi/network (刪除)**</span><span class="sxs-lookup"><span data-stu-id="ef857-443">**/api/wifi/network (DELETE)**</span></span>

<span data-ttu-id="ef857-444">刪除與指定介面上的網路相關聯的設定檔</span><span class="sxs-lookup"><span data-stu-id="ef857-444">Deletes a profile associated with a network on a specified interface</span></span>

<span data-ttu-id="ef857-445">參數</span><span class="sxs-lookup"><span data-stu-id="ef857-445">Parameters</span></span>
* <span data-ttu-id="ef857-446">介面：網路介面 guid</span><span class="sxs-lookup"><span data-stu-id="ef857-446">interface : network interface guid</span></span>
* <span data-ttu-id="ef857-447">設定檔：設定檔名稱</span><span class="sxs-lookup"><span data-stu-id="ef857-447">profile : profile name</span></span>

<span data-ttu-id="ef857-448">**/api/wifi/networks (取得)**</span><span class="sxs-lookup"><span data-stu-id="ef857-448">**/api/wifi/networks (GET)**</span></span>

<span data-ttu-id="ef857-449">列舉指定網路介面上的無線網路</span><span class="sxs-lookup"><span data-stu-id="ef857-449">Enumerates wireless networks on the specified network interface</span></span>

<span data-ttu-id="ef857-450">參數</span><span class="sxs-lookup"><span data-stu-id="ef857-450">Parameters</span></span>
* <span data-ttu-id="ef857-451">介面：網路介面 guid</span><span class="sxs-lookup"><span data-stu-id="ef857-451">interface : network interface guid</span></span>

<span data-ttu-id="ef857-452">傳回資料</span><span class="sxs-lookup"><span data-stu-id="ef857-452">Return data</span></span>
* <span data-ttu-id="ef857-453">網路介面上找到的無線網路清單與詳細資料</span><span class="sxs-lookup"><span data-stu-id="ef857-453">List of wireless networks found on the network interface with details</span></span>

<span data-ttu-id="ef857-454">**/api/wifi/network (POST)**</span><span class="sxs-lookup"><span data-stu-id="ef857-454">**/api/wifi/network (POST)**</span></span>

<span data-ttu-id="ef857-455">連接或中斷指定介面上的網路連線</span><span class="sxs-lookup"><span data-stu-id="ef857-455">Connects or disconnects to a network on the specified interface</span></span>

<span data-ttu-id="ef857-456">參數</span><span class="sxs-lookup"><span data-stu-id="ef857-456">Parameters</span></span>
* <span data-ttu-id="ef857-457">介面：網路介面 guid</span><span class="sxs-lookup"><span data-stu-id="ef857-457">interface : network interface guid</span></span>
* <span data-ttu-id="ef857-458">ssid： ssid、hex64 編碼、要連接的</span><span class="sxs-lookup"><span data-stu-id="ef857-458">ssid : ssid, hex64 encoded, to connect to</span></span>
* <span data-ttu-id="ef857-459">op：連線或中斷連接</span><span class="sxs-lookup"><span data-stu-id="ef857-459">op : connect or disconnect</span></span>
* <span data-ttu-id="ef857-460">createprofile：是或否</span><span class="sxs-lookup"><span data-stu-id="ef857-460">createprofile : yes or no</span></span>
* <span data-ttu-id="ef857-461">機碼：共用金鑰，hex64 編碼</span><span class="sxs-lookup"><span data-stu-id="ef857-461">key : shared key, hex64 encoded</span></span>

## <a name="windows-performance-recorder"></a><span data-ttu-id="ef857-462">Windows Performance Recorder</span><span class="sxs-lookup"><span data-stu-id="ef857-462">Windows Performance Recorder</span></span>

<span data-ttu-id="ef857-463">**/api/wpr/customtrace (POST)**</span><span class="sxs-lookup"><span data-stu-id="ef857-463">**/api/wpr/customtrace (POST)**</span></span>

<span data-ttu-id="ef857-464">上傳 WPR 設定檔，並使用上傳的設定檔開始追蹤。</span><span class="sxs-lookup"><span data-stu-id="ef857-464">Uploads a WPR profile and starts tracing using the uploaded profile.</span></span>

<span data-ttu-id="ef857-465">Payload</span><span class="sxs-lookup"><span data-stu-id="ef857-465">Payload</span></span>
* <span data-ttu-id="ef857-466">多部分的符合 HTTP 主體</span><span class="sxs-lookup"><span data-stu-id="ef857-466">multi-part conforming http body</span></span>

<span data-ttu-id="ef857-467">傳回資料</span><span class="sxs-lookup"><span data-stu-id="ef857-467">Return data</span></span>
* <span data-ttu-id="ef857-468">傳回 WPR 會話狀態。</span><span class="sxs-lookup"><span data-stu-id="ef857-468">Returns the WPR session status.</span></span>

<span data-ttu-id="ef857-469">**/api/wpr/status (取得)**</span><span class="sxs-lookup"><span data-stu-id="ef857-469">**/api/wpr/status (GET)**</span></span>

<span data-ttu-id="ef857-470">捕獲 WPR 會話的狀態</span><span class="sxs-lookup"><span data-stu-id="ef857-470">Retrieves the status of the WPR session</span></span>

<span data-ttu-id="ef857-471">傳回資料</span><span class="sxs-lookup"><span data-stu-id="ef857-471">Return data</span></span>
* <span data-ttu-id="ef857-472">WPR 會話狀態。</span><span class="sxs-lookup"><span data-stu-id="ef857-472">WPR session status.</span></span>

<span data-ttu-id="ef857-473">**/api/wpr/trace (取得)**</span><span class="sxs-lookup"><span data-stu-id="ef857-473">**/api/wpr/trace (GET)**</span></span>

<span data-ttu-id="ef857-474">停止 WPR (效能) 追蹤會話</span><span class="sxs-lookup"><span data-stu-id="ef857-474">Stops a WPR (performance) tracing session</span></span>

<span data-ttu-id="ef857-475">傳回資料</span><span class="sxs-lookup"><span data-stu-id="ef857-475">Return data</span></span>
* <span data-ttu-id="ef857-476">傳回追蹤 ETL 檔案</span><span class="sxs-lookup"><span data-stu-id="ef857-476">Returns the trace ETL file</span></span>

<span data-ttu-id="ef857-477">**/api/wpr/trace (POST)**</span><span class="sxs-lookup"><span data-stu-id="ef857-477">**/api/wpr/trace (POST)**</span></span>

<span data-ttu-id="ef857-478">啟動 WPR (效能) 追蹤會話</span><span class="sxs-lookup"><span data-stu-id="ef857-478">Starts a WPR (performance) tracing sessions</span></span>

<span data-ttu-id="ef857-479">參數</span><span class="sxs-lookup"><span data-stu-id="ef857-479">Parameters</span></span>
* <span data-ttu-id="ef857-480">設定檔：設定檔名稱。</span><span class="sxs-lookup"><span data-stu-id="ef857-480">profile : Profile name.</span></span> <span data-ttu-id="ef857-481">可用的設定檔會儲存在 perfprofiles/profiles.js</span><span class="sxs-lookup"><span data-stu-id="ef857-481">Available profiles are stored in perfprofiles/profiles.json</span></span>

<span data-ttu-id="ef857-482">傳回資料</span><span class="sxs-lookup"><span data-stu-id="ef857-482">Return data</span></span>
* <span data-ttu-id="ef857-483">在開始時，會傳回 WPR 會話狀態。</span><span class="sxs-lookup"><span data-stu-id="ef857-483">On start, returns the WPR session status.</span></span>

## <a name="see-also"></a><span data-ttu-id="ef857-484">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ef857-484">See also</span></span>
* [<span data-ttu-id="ef857-485">使用 Windows 裝置入口網站</span><span class="sxs-lookup"><span data-stu-id="ef857-485">Using the Windows Device Portal</span></span>](using-the-windows-device-portal.md)
* [<span data-ttu-id="ef857-486">裝置入口網站 (UWP) 的核心 API 參考 </span><span class="sxs-lookup"><span data-stu-id="ef857-486">Device Portal core API reference (UWP)</span></span>](/windows/uwp/debug-test-perf/device-portal-api-core)