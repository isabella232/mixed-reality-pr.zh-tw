---
title: 裝置入口網站 API 參照
description: HoloLens Windows 裝置入口網站的 API 參考
author: hamalawi
ms.author: moelhama
ms.date: 08/03/2020
ms.topic: article
keywords: HoloLens、Windows 裝置入口網站、API
ms.openlocfilehash: 6b8f99fbc6f1965639ceef218f5c516d2e6ba467
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2020
ms.locfileid: "91679305"
---
# <a name="device-portal-api-reference"></a><span data-ttu-id="68fcf-104">裝置入口網站 API 參照</span><span class="sxs-lookup"><span data-stu-id="68fcf-104">Device portal API reference</span></span>

<span data-ttu-id="68fcf-105">[Windows 裝置入口網站](using-the-windows-device-portal.md)中的所有專案都建置於 REST API 的之上，您可以用來以程式設計方式存取資料和控制您的裝置。</span><span class="sxs-lookup"><span data-stu-id="68fcf-105">Everything in the [Windows Device Portal](using-the-windows-device-portal.md) is built on top of REST API's that you can use to access the data and control your device programmatically.</span></span>

## <a name="app-deloyment"></a><span data-ttu-id="68fcf-106">應用程式部署常見問題</span><span class="sxs-lookup"><span data-stu-id="68fcf-106">App deloyment</span></span>

<span data-ttu-id="68fcf-107">**/api/app/packagemanager/package (刪除)**</span><span class="sxs-lookup"><span data-stu-id="68fcf-107">**/api/app/packagemanager/package (DELETE)**</span></span>

<span data-ttu-id="68fcf-108">卸載應用程式</span><span class="sxs-lookup"><span data-stu-id="68fcf-108">Uninstalls an app</span></span>

<span data-ttu-id="68fcf-109">參數</span><span class="sxs-lookup"><span data-stu-id="68fcf-109">Parameters</span></span>
* <span data-ttu-id="68fcf-110">封裝：要卸載之封裝的檔案名。</span><span class="sxs-lookup"><span data-stu-id="68fcf-110">package : File name of the package to be uninstalled.</span></span>

<span data-ttu-id="68fcf-111">**/api/app/packagemanager/package (POST)**</span><span class="sxs-lookup"><span data-stu-id="68fcf-111">**/api/app/packagemanager/package (POST)**</span></span>

<span data-ttu-id="68fcf-112">安裝應用程式</span><span class="sxs-lookup"><span data-stu-id="68fcf-112">Installs an App</span></span>

<span data-ttu-id="68fcf-113">參數</span><span class="sxs-lookup"><span data-stu-id="68fcf-113">Parameters</span></span>
* <span data-ttu-id="68fcf-114">封裝：要安裝之套件的檔案名。</span><span class="sxs-lookup"><span data-stu-id="68fcf-114">package : File name of the package to be installed.</span></span>

<span data-ttu-id="68fcf-115">Payload</span><span class="sxs-lookup"><span data-stu-id="68fcf-115">Payload</span></span>
* <span data-ttu-id="68fcf-116">多部分的符合 HTTP 主體</span><span class="sxs-lookup"><span data-stu-id="68fcf-116">multi-part conforming http body</span></span>

<span data-ttu-id="68fcf-117">**/api/app/packagemanager/packages (取得)**</span><span class="sxs-lookup"><span data-stu-id="68fcf-117">**/api/app/packagemanager/packages (GET)**</span></span>

<span data-ttu-id="68fcf-118">抓取系統上已安裝應用程式的清單，並提供詳細資料</span><span class="sxs-lookup"><span data-stu-id="68fcf-118">Retrieves the list of installed apps on the system, with details</span></span>

<span data-ttu-id="68fcf-119">傳回資料</span><span class="sxs-lookup"><span data-stu-id="68fcf-119">Return data</span></span>
* <span data-ttu-id="68fcf-120">包含詳細資料的已安裝套件清單</span><span class="sxs-lookup"><span data-stu-id="68fcf-120">List of installed packages with details</span></span>

<span data-ttu-id="68fcf-121">**/api/app/packagemanager/state (取得)**</span><span class="sxs-lookup"><span data-stu-id="68fcf-121">**/api/app/packagemanager/state (GET)**</span></span>

<span data-ttu-id="68fcf-122">取得進行中的應用程式安裝狀態</span><span class="sxs-lookup"><span data-stu-id="68fcf-122">Gets the status of in progress app installation</span></span>

## <a name="dump-collection"></a><span data-ttu-id="68fcf-123">傾印集合</span><span class="sxs-lookup"><span data-stu-id="68fcf-123">Dump collection</span></span>

<span data-ttu-id="68fcf-124">**/api/debug/dump/usermode/crashcontrol (刪除)**</span><span class="sxs-lookup"><span data-stu-id="68fcf-124">**/api/debug/dump/usermode/crashcontrol (DELETE)**</span></span>

<span data-ttu-id="68fcf-125">停用側載應用程式的損毀傾印收集</span><span class="sxs-lookup"><span data-stu-id="68fcf-125">Disables crash dump collection for a sideloaded app</span></span>

<span data-ttu-id="68fcf-126">參數</span><span class="sxs-lookup"><span data-stu-id="68fcf-126">Parameters</span></span>
* <span data-ttu-id="68fcf-127">packageFullname：套件名稱</span><span class="sxs-lookup"><span data-stu-id="68fcf-127">packageFullname : package name</span></span>

<span data-ttu-id="68fcf-128">**/api/debug/dump/usermode/crashcontrol (取得)**</span><span class="sxs-lookup"><span data-stu-id="68fcf-128">**/api/debug/dump/usermode/crashcontrol (GET)**</span></span>

<span data-ttu-id="68fcf-129">取得側載 apps 損毀傾印集合的設定</span><span class="sxs-lookup"><span data-stu-id="68fcf-129">Gets settings for sideloaded apps crash dump collection</span></span>

<span data-ttu-id="68fcf-130">參數</span><span class="sxs-lookup"><span data-stu-id="68fcf-130">Parameters</span></span>
* <span data-ttu-id="68fcf-131">packageFullname：套件名稱</span><span class="sxs-lookup"><span data-stu-id="68fcf-131">packageFullname : package name</span></span>

<span data-ttu-id="68fcf-132">**/api/debug/dump/usermode/crashcontrol (POST)**</span><span class="sxs-lookup"><span data-stu-id="68fcf-132">**/api/debug/dump/usermode/crashcontrol (POST)**</span></span>

<span data-ttu-id="68fcf-133">啟用並設定側載應用程式的傾印控制項設定</span><span class="sxs-lookup"><span data-stu-id="68fcf-133">Enables and sets dump control settings for a sideloaded app</span></span>

<span data-ttu-id="68fcf-134">參數</span><span class="sxs-lookup"><span data-stu-id="68fcf-134">Parameters</span></span>
* <span data-ttu-id="68fcf-135">packageFullname：套件名稱</span><span class="sxs-lookup"><span data-stu-id="68fcf-135">packageFullname : package name</span></span>

<span data-ttu-id="68fcf-136">**/api/debug/dump/usermode/crashdump (刪除)**</span><span class="sxs-lookup"><span data-stu-id="68fcf-136">**/api/debug/dump/usermode/crashdump (DELETE)**</span></span>

<span data-ttu-id="68fcf-137">刪除側載應用程式的損毀傾印</span><span class="sxs-lookup"><span data-stu-id="68fcf-137">Deletes a crash dump for a sideloaded app</span></span>

<span data-ttu-id="68fcf-138">參數</span><span class="sxs-lookup"><span data-stu-id="68fcf-138">Parameters</span></span>
* <span data-ttu-id="68fcf-139">packageFullname：套件名稱</span><span class="sxs-lookup"><span data-stu-id="68fcf-139">packageFullname : package name</span></span>
* <span data-ttu-id="68fcf-140">檔案名：傾印檔案名</span><span class="sxs-lookup"><span data-stu-id="68fcf-140">fileName : dump file name</span></span>

<span data-ttu-id="68fcf-141">**/api/debug/dump/usermode/crashdump (取得)**</span><span class="sxs-lookup"><span data-stu-id="68fcf-141">**/api/debug/dump/usermode/crashdump (GET)**</span></span>

<span data-ttu-id="68fcf-142">捕獲側載應用程式的損毀傾印</span><span class="sxs-lookup"><span data-stu-id="68fcf-142">Retrieves a crash dump for a sideloaded app</span></span>

<span data-ttu-id="68fcf-143">參數</span><span class="sxs-lookup"><span data-stu-id="68fcf-143">Parameters</span></span>
* <span data-ttu-id="68fcf-144">packageFullname：套件名稱</span><span class="sxs-lookup"><span data-stu-id="68fcf-144">packageFullname : package name</span></span>
* <span data-ttu-id="68fcf-145">檔案名：傾印檔案名</span><span class="sxs-lookup"><span data-stu-id="68fcf-145">fileName : dump file name</span></span>

<span data-ttu-id="68fcf-146">傳回資料</span><span class="sxs-lookup"><span data-stu-id="68fcf-146">Return data</span></span>
* <span data-ttu-id="68fcf-147">傾印檔案。</span><span class="sxs-lookup"><span data-stu-id="68fcf-147">Dump file.</span></span> <span data-ttu-id="68fcf-148">使用 WinDbg 或 Visual Studio 檢查</span><span class="sxs-lookup"><span data-stu-id="68fcf-148">Inspect with WinDbg or Visual Studio</span></span>

<span data-ttu-id="68fcf-149">**/api/debug/dump/usermode/dumps (取得)**</span><span class="sxs-lookup"><span data-stu-id="68fcf-149">**/api/debug/dump/usermode/dumps (GET)**</span></span>

<span data-ttu-id="68fcf-150">傳回側載 apps 的所有損毀傾印清單</span><span class="sxs-lookup"><span data-stu-id="68fcf-150">Returns list of all crash dumps for sideloaded apps</span></span>

<span data-ttu-id="68fcf-151">傳回資料</span><span class="sxs-lookup"><span data-stu-id="68fcf-151">Return data</span></span>
* <span data-ttu-id="68fcf-152">每一端載入的應用程式損毀傾印清單</span><span class="sxs-lookup"><span data-stu-id="68fcf-152">List of crash dumps per side loaded app</span></span>

## <a name="etw"></a><span data-ttu-id="68fcf-153">ETW</span><span class="sxs-lookup"><span data-stu-id="68fcf-153">ETW</span></span>

<span data-ttu-id="68fcf-154">**/api/etw/providers (取得)**</span><span class="sxs-lookup"><span data-stu-id="68fcf-154">**/api/etw/providers (GET)**</span></span>

<span data-ttu-id="68fcf-155">列舉已註冊的提供者</span><span class="sxs-lookup"><span data-stu-id="68fcf-155">Enumerates registered providers</span></span>

<span data-ttu-id="68fcf-156">傳回資料</span><span class="sxs-lookup"><span data-stu-id="68fcf-156">Return data</span></span>
* <span data-ttu-id="68fcf-157">提供者清單、易記名稱和 GUID</span><span class="sxs-lookup"><span data-stu-id="68fcf-157">List of providers, friendly name and GUID</span></span>

<span data-ttu-id="68fcf-158">**/api/etw/session/realtime (GET/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="68fcf-158">**/api/etw/session/realtime (GET/WebSocket)**</span></span>

<span data-ttu-id="68fcf-159">建立即時 ETW 會話;在 websocket 上進行管理。</span><span class="sxs-lookup"><span data-stu-id="68fcf-159">Creates a realtime ETW session; managed over a websocket.</span></span>

<span data-ttu-id="68fcf-160">傳回資料</span><span class="sxs-lookup"><span data-stu-id="68fcf-160">Return data</span></span>
* <span data-ttu-id="68fcf-161">來自已啟用提供者的 ETW 事件</span><span class="sxs-lookup"><span data-stu-id="68fcf-161">ETW events from the enabled providers</span></span>

## <a name="holographic-os"></a><span data-ttu-id="68fcf-162">全像攝影版 OS</span><span class="sxs-lookup"><span data-stu-id="68fcf-162">Holographic OS</span></span>

<span data-ttu-id="68fcf-163">**/api/holographic/os/etw/customproviders (取得)**</span><span class="sxs-lookup"><span data-stu-id="68fcf-163">**/api/holographic/os/etw/customproviders (GET)**</span></span>

<span data-ttu-id="68fcf-164">傳回未向系統註冊的 HoloLens 特定 ETW 提供者清單</span><span class="sxs-lookup"><span data-stu-id="68fcf-164">Returns a list of HoloLens specific ETW providers that are not registered with the system</span></span>

<span data-ttu-id="68fcf-165">**/api/holographic/os/services (取得)**</span><span class="sxs-lookup"><span data-stu-id="68fcf-165">**/api/holographic/os/services (GET)**</span></span>

<span data-ttu-id="68fcf-166">傳回所有執行中之服務的狀態。</span><span class="sxs-lookup"><span data-stu-id="68fcf-166">Returns the states of all services running.</span></span>

<span data-ttu-id="68fcf-167">**/api/holographic/os/settings/ipd (取得)**</span><span class="sxs-lookup"><span data-stu-id="68fcf-167">**/api/holographic/os/settings/ipd (GET)**</span></span>

<span data-ttu-id="68fcf-168">取得儲存的 IPD (Interpupillary 距離) 以毫米為單位</span><span class="sxs-lookup"><span data-stu-id="68fcf-168">Gets the stored IPD (Interpupillary distance) in millimeters</span></span>

<span data-ttu-id="68fcf-169">**/api/holographic/os/settings/ipd (POST)**</span><span class="sxs-lookup"><span data-stu-id="68fcf-169">**/api/holographic/os/settings/ipd (POST)**</span></span>

<span data-ttu-id="68fcf-170">設定 IPD</span><span class="sxs-lookup"><span data-stu-id="68fcf-170">Sets the IPD</span></span>

<span data-ttu-id="68fcf-171">參數</span><span class="sxs-lookup"><span data-stu-id="68fcf-171">Parameters</span></span>
* <span data-ttu-id="68fcf-172">ipd：要設定的新 IPD 值（以毫米為單位）</span><span class="sxs-lookup"><span data-stu-id="68fcf-172">ipd : New IPD value to be set in millimeters</span></span>

<span data-ttu-id="68fcf-173">**/api/holographic/os/webmanagement/settings/HTTPs (取得)**</span><span class="sxs-lookup"><span data-stu-id="68fcf-173">**/api/holographic/os/webmanagement/settings/https (GET)**</span></span>

<span data-ttu-id="68fcf-174">取得裝置入口網站的 HTTPS 需求</span><span class="sxs-lookup"><span data-stu-id="68fcf-174">Get HTTPS requirements for the Device Portal</span></span>

<span data-ttu-id="68fcf-175">**/api/holographic/os/webmanagement/settings/HTTPs (POST)**</span><span class="sxs-lookup"><span data-stu-id="68fcf-175">**/api/holographic/os/webmanagement/settings/https (POST)**</span></span>

<span data-ttu-id="68fcf-176">設定裝置入口網站的 HTTPS 需求</span><span class="sxs-lookup"><span data-stu-id="68fcf-176">Sets HTTPS requirements for the Device Portal</span></span>

<span data-ttu-id="68fcf-177">參數</span><span class="sxs-lookup"><span data-stu-id="68fcf-177">Parameters</span></span>
* <span data-ttu-id="68fcf-178">必要：是、否或預設值</span><span class="sxs-lookup"><span data-stu-id="68fcf-178">required : yes, no or default</span></span>

## <a name="holographic-perception"></a><span data-ttu-id="68fcf-179">全像</span><span class="sxs-lookup"><span data-stu-id="68fcf-179">Holographic Perception</span></span>

<span data-ttu-id="68fcf-180">**/api/holographic/perception/client (GET/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="68fcf-180">**/api/holographic/perception/client (GET/WebSocket)**</span></span>

<span data-ttu-id="68fcf-181">接受 websocket 升級並執行感知用戶端，以 30 fps 的形式傳送更新。</span><span class="sxs-lookup"><span data-stu-id="68fcf-181">Accepts websocket upgrades and runs a perception client that sends updates at 30 fps.</span></span>

<span data-ttu-id="68fcf-182">參數</span><span class="sxs-lookup"><span data-stu-id="68fcf-182">Parameters</span></span>
* <span data-ttu-id="68fcf-183">clientmode：「作用中」會在無法被動建立時強制視覺化追蹤模式</span><span class="sxs-lookup"><span data-stu-id="68fcf-183">clientmode: "active" forces visual tracking mode when it can't be established passively</span></span>

## <a name="holographic-thermal"></a><span data-ttu-id="68fcf-184">全像熱</span><span class="sxs-lookup"><span data-stu-id="68fcf-184">Holographic Thermal</span></span>

<span data-ttu-id="68fcf-185">**/api/holographic/thermal/stage (取得)**</span><span class="sxs-lookup"><span data-stu-id="68fcf-185">**/api/holographic/thermal/stage (GET)**</span></span>

<span data-ttu-id="68fcf-186">取得裝置的熱階段 (0 正常、1暖、2關鍵) </span><span class="sxs-lookup"><span data-stu-id="68fcf-186">Get the thermal stage of the device (0 normal, 1 warm, 2 critical)</span></span>

## <a name="map-manager"></a><span data-ttu-id="68fcf-187">對應管理員</span><span class="sxs-lookup"><span data-stu-id="68fcf-187">Map Manager</span></span>

<span data-ttu-id="68fcf-188">**/api/holographic/mapmanager/mapFiles (取得)**</span><span class="sxs-lookup"><span data-stu-id="68fcf-188">**/api/holographic/mapmanager/mapFiles (GET)**</span></span>

<span data-ttu-id="68fcf-189">取得可用對應檔 ( mapx) 的清單。</span><span class="sxs-lookup"><span data-stu-id="68fcf-189">Gets the list of the available map files (.mapx).</span></span>

<span data-ttu-id="68fcf-190">**/api/holographic/mapmanager/anchorFiles (取得)**</span><span class="sxs-lookup"><span data-stu-id="68fcf-190">**/api/holographic/mapmanager/anchorFiles (GET)**</span></span>

<span data-ttu-id="68fcf-191">取得可用錨定檔案 ( ancx) 的清單。</span><span class="sxs-lookup"><span data-stu-id="68fcf-191">Gets the list of available anchor files (.ancx).</span></span>

<span data-ttu-id="68fcf-192">**/api/holographic/mapmanager/srdbFiles (取得)**</span><span class="sxs-lookup"><span data-stu-id="68fcf-192">**/api/holographic/mapmanager/srdbFiles (GET)**</span></span>

<span data-ttu-id="68fcf-193">取得可用空間重建資料庫檔案 ( srdb) 的清單。</span><span class="sxs-lookup"><span data-stu-id="68fcf-193">Gets the list of available spatial reconstruction database files (.srdb).</span></span>

<span data-ttu-id="68fcf-194">**/api/holographic/mapmanager/getanchors (取得)**</span><span class="sxs-lookup"><span data-stu-id="68fcf-194">**/api/holographic/mapmanager/getanchors (GET)**</span></span>

<span data-ttu-id="68fcf-195">取得目前使用者的已保存錨點清單。</span><span class="sxs-lookup"><span data-stu-id="68fcf-195">Gets the list of persisted anchors for the current user.</span></span> 

### <a name="downloaduploaddelete-files"></a><span data-ttu-id="68fcf-196">下載/上傳/刪除檔案</span><span class="sxs-lookup"><span data-stu-id="68fcf-196">Download/Upload/Delete Files</span></span>
<span data-ttu-id="68fcf-197">**/api/holographic/mapmanager/download (取得)**</span><span class="sxs-lookup"><span data-stu-id="68fcf-197">**/api/holographic/mapmanager/download (GET)**</span></span>

<span data-ttu-id="68fcf-198">下載地圖、錨點或空間重建資料庫檔案。</span><span class="sxs-lookup"><span data-stu-id="68fcf-198">Downloads a map, anchor, or spatial reconstruction database file.</span></span> <span data-ttu-id="68fcf-199">檔案必須先前已上傳或匯出。</span><span class="sxs-lookup"><span data-stu-id="68fcf-199">The file must have been previously uploaded or exported.</span></span>

<span data-ttu-id="68fcf-200">參數</span><span class="sxs-lookup"><span data-stu-id="68fcf-200">Parameters</span></span>
* <span data-ttu-id="68fcf-201">檔案名：要下載的檔案名。</span><span class="sxs-lookup"><span data-stu-id="68fcf-201">FileName: Name of file to download.</span></span>

<span data-ttu-id="68fcf-202">範例：</span><span class="sxs-lookup"><span data-stu-id="68fcf-202">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/download?FileName=" + spaceID)
```

<span data-ttu-id="68fcf-203">**/api/holographic/mapmanager/upload (POST)**</span><span class="sxs-lookup"><span data-stu-id="68fcf-203">**/api/holographic/mapmanager/upload (POST)**</span></span>

<span data-ttu-id="68fcf-204">上傳地圖、錨點或空間重建資料庫檔案。</span><span class="sxs-lookup"><span data-stu-id="68fcf-204">Uploads a map, anchor, or spatial reconstruction database file.</span></span> <span data-ttu-id="68fcf-205">檔案上傳之後，稍後可以匯入以供系統使用。</span><span class="sxs-lookup"><span data-stu-id="68fcf-205">Once a file is uploaded it can later be imported to be used by the system.</span></span>

<span data-ttu-id="68fcf-206">參數</span><span class="sxs-lookup"><span data-stu-id="68fcf-206">Parameters</span></span>
* <span data-ttu-id="68fcf-207">file：要上傳之檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="68fcf-207">file: Name of the file to upload.</span></span>

<span data-ttu-id="68fcf-208">範例：</span><span class="sxs-lookup"><span data-stu-id="68fcf-208">Example:</span></span>
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

<span data-ttu-id="68fcf-209">**/api/holographic/mapmanager/delete (POST)**</span><span class="sxs-lookup"><span data-stu-id="68fcf-209">**/api/holographic/mapmanager/delete (POST)**</span></span>

<span data-ttu-id="68fcf-210">刪除地圖、錨點或空間重建資料庫檔案。</span><span class="sxs-lookup"><span data-stu-id="68fcf-210">Deletes a map, anchor, or spatial reconstruction database file.</span></span> <span data-ttu-id="68fcf-211">檔案必須先前已上傳或匯出。</span><span class="sxs-lookup"><span data-stu-id="68fcf-211">The file must have been previously uploaded or exported.</span></span>

<span data-ttu-id="68fcf-212">參數</span><span class="sxs-lookup"><span data-stu-id="68fcf-212">Parameters</span></span>
* <span data-ttu-id="68fcf-213">FileName：要刪除的檔案名。</span><span class="sxs-lookup"><span data-stu-id="68fcf-213">FileName: Name of file to delete.</span></span>

<span data-ttu-id="68fcf-214">範例：</span><span class="sxs-lookup"><span data-stu-id="68fcf-214">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/delete?FileName=" + spaceID)
```

### <a name="export"></a><span data-ttu-id="68fcf-215">匯出</span><span class="sxs-lookup"><span data-stu-id="68fcf-215">Export</span></span>

<span data-ttu-id="68fcf-216">**/api/holographic/mapmanager/export (POST)**</span><span class="sxs-lookup"><span data-stu-id="68fcf-216">**/api/holographic/mapmanager/export (POST)**</span></span>

<span data-ttu-id="68fcf-217">匯出系統目前正在使用的對應。</span><span class="sxs-lookup"><span data-stu-id="68fcf-217">Exports the map currently in use by the system.</span></span> <span data-ttu-id="68fcf-218">一旦匯出之後，即可加以下載。</span><span class="sxs-lookup"><span data-stu-id="68fcf-218">Once exported, it can be downloaded.</span></span> 

<span data-ttu-id="68fcf-219">範例：</span><span class="sxs-lookup"><span data-stu-id="68fcf-219">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/export")
```

<span data-ttu-id="68fcf-220">**/api/holographic/mapmanager/exportanchors (POST)**</span><span class="sxs-lookup"><span data-stu-id="68fcf-220">**/api/holographic/mapmanager/exportanchors (POST)**</span></span>

<span data-ttu-id="68fcf-221">匯出系統目前正在使用的對應。</span><span class="sxs-lookup"><span data-stu-id="68fcf-221">Exports the map currently in use by the system.</span></span> <span data-ttu-id="68fcf-222">一旦匯出之後，即可加以下載。</span><span class="sxs-lookup"><span data-stu-id="68fcf-222">Once exported, it can be downloaded.</span></span> <span data-ttu-id="68fcf-223">範例：</span><span class="sxs-lookup"><span data-stu-id="68fcf-223">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/exportanchors")
```

<span data-ttu-id="68fcf-224">**/api/holographic/mapmanager/exportmapandanchors (POST)**</span><span class="sxs-lookup"><span data-stu-id="68fcf-224">**/api/holographic/mapmanager/exportmapandanchors (POST)**</span></span>

<span data-ttu-id="68fcf-225">匯出系統目前正在使用的對應和錨點。</span><span class="sxs-lookup"><span data-stu-id="68fcf-225">Exports the map and anchors currently in use by the system.</span></span> <span data-ttu-id="68fcf-226">一旦匯出之後，即可加以下載。</span><span class="sxs-lookup"><span data-stu-id="68fcf-226">Once are exported, they can be downloaded.</span></span> <span data-ttu-id="68fcf-227">範例：</span><span class="sxs-lookup"><span data-stu-id="68fcf-227">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/exportmapandanchors")
```

<span data-ttu-id="68fcf-228">**/api/holographic/mapmanager/exportmapandspatialmappingdb (POST)**</span><span class="sxs-lookup"><span data-stu-id="68fcf-228">**/api/holographic/mapmanager/exportmapandspatialmappingdb (POST)**</span></span>

<span data-ttu-id="68fcf-229">匯出系統目前正在使用的地圖和空間重建資料庫。</span><span class="sxs-lookup"><span data-stu-id="68fcf-229">Exports the map and spatial reconstruction database currently in use by the system.</span></span> <span data-ttu-id="68fcf-230">一旦匯出之後，即可加以下載。</span><span class="sxs-lookup"><span data-stu-id="68fcf-230">Once they are exported, they can be downloaded.</span></span> 

<span data-ttu-id="68fcf-231">範例：</span><span class="sxs-lookup"><span data-stu-id="68fcf-231">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/exportmapandspatialmappingdb")
```

### <a name="import"></a><span data-ttu-id="68fcf-232">匯入</span><span class="sxs-lookup"><span data-stu-id="68fcf-232">Import</span></span>

<span data-ttu-id="68fcf-233">**/api/holographic/mapmanager/import (POST)**</span><span class="sxs-lookup"><span data-stu-id="68fcf-233">**/api/holographic/mapmanager/import (POST)**</span></span>

<span data-ttu-id="68fcf-234">向系統表示目前使用的對應。</span><span class="sxs-lookup"><span data-stu-id="68fcf-234">Indicates to the system which map should be used be currently used.</span></span> <span data-ttu-id="68fcf-235">可以在已匯出或已上傳的檔案上呼叫。</span><span class="sxs-lookup"><span data-stu-id="68fcf-235">Can be called on files that have been exported or uploaded.</span></span>

<span data-ttu-id="68fcf-236">參數</span><span class="sxs-lookup"><span data-stu-id="68fcf-236">Parameters</span></span>
* <span data-ttu-id="68fcf-237">FileName：要使用的對應名稱。</span><span class="sxs-lookup"><span data-stu-id="68fcf-237">FileName: Name of the map to be used.</span></span> 

<span data-ttu-id="68fcf-238">範例：</span><span class="sxs-lookup"><span data-stu-id="68fcf-238">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/import?FileName=" + spaceID, function() { alert("Import was successful!"); })
```

<span data-ttu-id="68fcf-239">**/api/holographic/mapmanager/importanchors (POST)**</span><span class="sxs-lookup"><span data-stu-id="68fcf-239">**/api/holographic/mapmanager/importanchors (POST)**</span></span>

<span data-ttu-id="68fcf-240">向系統表示目前使用的錨點。</span><span class="sxs-lookup"><span data-stu-id="68fcf-240">Indicates to the system which anchors should be used be currently used.</span></span> <span data-ttu-id="68fcf-241">可以在已匯出或已上傳的檔案上呼叫。</span><span class="sxs-lookup"><span data-stu-id="68fcf-241">Can be called on files that have been exported or uploaded.</span></span>

<span data-ttu-id="68fcf-242">參數</span><span class="sxs-lookup"><span data-stu-id="68fcf-242">Parameters</span></span>
* <span data-ttu-id="68fcf-243">FileName：要使用的錨點名稱。</span><span class="sxs-lookup"><span data-stu-id="68fcf-243">FileName: Name of the anchors to be used.</span></span> 

<span data-ttu-id="68fcf-244">範例：</span><span class="sxs-lookup"><span data-stu-id="68fcf-244">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/import?FileName=" + spaceID, function() { alert("Import was successful!"); })
```

<span data-ttu-id="68fcf-245">**/api/holographic/mapmanager/importspatialmappingdb (POST)**</span><span class="sxs-lookup"><span data-stu-id="68fcf-245">**/api/holographic/mapmanager/importspatialmappingdb (POST)**</span></span>

<span data-ttu-id="68fcf-246">向系統表示目前應使用的空間重建資料庫。</span><span class="sxs-lookup"><span data-stu-id="68fcf-246">Indicates to the system which spatial reconstruction database should be used be currently used.</span></span> <span data-ttu-id="68fcf-247">可以在已匯出或已上傳的檔案上呼叫。</span><span class="sxs-lookup"><span data-stu-id="68fcf-247">Can be called on files that have been exported or uploaded.</span></span>

<span data-ttu-id="68fcf-248">參數</span><span class="sxs-lookup"><span data-stu-id="68fcf-248">Parameters</span></span>
* <span data-ttu-id="68fcf-249">FileName：要使用之空間對應資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="68fcf-249">FileName: Name of the spatial mapping db to be used.</span></span> 

<span data-ttu-id="68fcf-250">範例：</span><span class="sxs-lookup"><span data-stu-id="68fcf-250">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/import?FileName=" + spaceID, function() { alert("Import was successful!"); })
```

### <a name="other"></a><span data-ttu-id="68fcf-251">其他</span><span class="sxs-lookup"><span data-stu-id="68fcf-251">Other</span></span>

<span data-ttu-id="68fcf-252">**/api/holographic/mapmanager/resetmapandanchorsandsrdb (POST)**</span><span class="sxs-lookup"><span data-stu-id="68fcf-252">**/api/holographic/mapmanager/resetmapandanchorsandsrdb (POST)**</span></span>

<span data-ttu-id="68fcf-253">重設對應、錨定和空間重建資料庫的系統。</span><span class="sxs-lookup"><span data-stu-id="68fcf-253">Reset the system the map, anchors and spatial reconstruction database.</span></span>

<span data-ttu-id="68fcf-254">範例：</span><span class="sxs-lookup"><span data-stu-id="68fcf-254">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/resetmapandanchorsandsrdb")
```

<span data-ttu-id="68fcf-255">**/api/holographic/mapmanager/status (取得)**</span><span class="sxs-lookup"><span data-stu-id="68fcf-255">**/api/holographic/mapmanager/status (GET)**</span></span>

<span data-ttu-id="68fcf-256">取得系統的狀態，包括上次匯入的對應、錨點和空間重建資料庫檔案。</span><span class="sxs-lookup"><span data-stu-id="68fcf-256">Gets the status of the system, including which map, anchors, and spatial reconstruction database files that were last imported.</span></span> 


## <a name="mixed-reality-capture"></a><span data-ttu-id="68fcf-257">混合實境擷取</span><span class="sxs-lookup"><span data-stu-id="68fcf-257">Mixed Reality Capture</span></span>

<span data-ttu-id="68fcf-258">**/api/holographic/mrc/file (取得)**</span><span class="sxs-lookup"><span data-stu-id="68fcf-258">**/api/holographic/mrc/file (GET)**</span></span>

<span data-ttu-id="68fcf-259">從裝置下載混合的實際檔案。</span><span class="sxs-lookup"><span data-stu-id="68fcf-259">Downloads a mixed reality file from the device.</span></span> <span data-ttu-id="68fcf-260">使用 op = 串流查詢參數進行串流。</span><span class="sxs-lookup"><span data-stu-id="68fcf-260">Use op=stream query parameter for streaming.</span></span>

<span data-ttu-id="68fcf-261">參數</span><span class="sxs-lookup"><span data-stu-id="68fcf-261">Parameters</span></span>
* <span data-ttu-id="68fcf-262">檔案名：要取得之影片檔案的名稱、hex64 編碼</span><span class="sxs-lookup"><span data-stu-id="68fcf-262">filename : Name, hex64 encoded, of the video file to get</span></span>
* <span data-ttu-id="68fcf-263">op：資料流程</span><span class="sxs-lookup"><span data-stu-id="68fcf-263">op : stream</span></span>

<span data-ttu-id="68fcf-264">**/api/holographic/mrc/file (刪除)**</span><span class="sxs-lookup"><span data-stu-id="68fcf-264">**/api/holographic/mrc/file (DELETE)**</span></span>

<span data-ttu-id="68fcf-265">從裝置刪除混合現實記錄。</span><span class="sxs-lookup"><span data-stu-id="68fcf-265">Deletes a mixed reality recording from the device.</span></span>

<span data-ttu-id="68fcf-266">參數</span><span class="sxs-lookup"><span data-stu-id="68fcf-266">Parameters</span></span>
* <span data-ttu-id="68fcf-267">檔案名：要刪除之檔案的名稱、hex64 編碼</span><span class="sxs-lookup"><span data-stu-id="68fcf-267">filename : Name, hex64 encoded, of the file to delete</span></span>

<span data-ttu-id="68fcf-268">**/api/holographic/mrc/files (取得)**</span><span class="sxs-lookup"><span data-stu-id="68fcf-268">**/api/holographic/mrc/files (GET)**</span></span>

<span data-ttu-id="68fcf-269">傳回儲存在裝置上的混合現實檔案清單</span><span class="sxs-lookup"><span data-stu-id="68fcf-269">Returns the list of mixed reality files stored on the device</span></span>

<span data-ttu-id="68fcf-270">**/api/holographic/mrc/photo (POST)**</span><span class="sxs-lookup"><span data-stu-id="68fcf-270">**/api/holographic/mrc/photo (POST)**</span></span>

<span data-ttu-id="68fcf-271">採用混合的現實照片，並在裝置上建立檔案</span><span class="sxs-lookup"><span data-stu-id="68fcf-271">Takes a mixed reality photo and creates a file on the device</span></span>

<span data-ttu-id="68fcf-272">參數</span><span class="sxs-lookup"><span data-stu-id="68fcf-272">Parameters</span></span>
* <span data-ttu-id="68fcf-273">hololens：抓取全像： true 或 false (預設為 false) </span><span class="sxs-lookup"><span data-stu-id="68fcf-273">holo : capture holograms: true or false (defaults to false)</span></span>
* <span data-ttu-id="68fcf-274">pv： capture PV 攝影機： true 或 false (預設為 false) </span><span class="sxs-lookup"><span data-stu-id="68fcf-274">pv : capture PV camera: true or false (defaults to false)</span></span>
* <span data-ttu-id="68fcf-275">RenderFromCamera： (只 HoloLens 2) 從相片/攝影機的觀點轉譯： true 或 false (預設為 true) </span><span class="sxs-lookup"><span data-stu-id="68fcf-275">RenderFromCamera : (HoloLens 2 only) render from perspective of photo/video camera: true or false (defaults to true)</span></span>

<span data-ttu-id="68fcf-276">**/api/holographic/mrc/settings (取得)**</span><span class="sxs-lookup"><span data-stu-id="68fcf-276">**/api/holographic/mrc/settings (GET)**</span></span>

<span data-ttu-id="68fcf-277">取得預設的混合現實捕獲設定</span><span class="sxs-lookup"><span data-stu-id="68fcf-277">Gets the default mixed reality capture settings</span></span>

<span data-ttu-id="68fcf-278">**/api/holographic/mrc/settings (POST)**</span><span class="sxs-lookup"><span data-stu-id="68fcf-278">**/api/holographic/mrc/settings (POST)**</span></span>

<span data-ttu-id="68fcf-279">設定預設的混合現實捕獲設定。</span><span class="sxs-lookup"><span data-stu-id="68fcf-279">Sets the default mixed reality capture settings.</span></span>  <span data-ttu-id="68fcf-280">其中某些設定會套用到系統的 MRC 照片和影片捕捉。</span><span class="sxs-lookup"><span data-stu-id="68fcf-280">Some of these settings are applied to the system's MRC photo and video capture.</span></span>

<span data-ttu-id="68fcf-281">**/api/holographic/mrc/status (取得)**</span><span class="sxs-lookup"><span data-stu-id="68fcf-281">**/api/holographic/mrc/status (GET)**</span></span>

<span data-ttu-id="68fcf-282">取得 Windows 裝置入口網站內混合現實捕捉的狀態。</span><span class="sxs-lookup"><span data-stu-id="68fcf-282">Gets the state of mixed reality capture within the Windows Device Portal.</span></span>

<span data-ttu-id="68fcf-283">***回應***</span><span class="sxs-lookup"><span data-stu-id="68fcf-283">***Response***</span></span>

<span data-ttu-id="68fcf-284">回應包含 JSON 屬性，指出 Windows 裝置入口網站是否錄製影片。</span><span class="sxs-lookup"><span data-stu-id="68fcf-284">The response contains a JSON property indicating if Windows Device Portal is recording video or not.</span></span>

``` javascript
{"IsRecording" : boolean}
```

<span data-ttu-id="68fcf-285">**/api/holographic/mrc/thumbnail (取得)**</span><span class="sxs-lookup"><span data-stu-id="68fcf-285">**/api/holographic/mrc/thumbnail (GET)**</span></span>

<span data-ttu-id="68fcf-286">取得指定檔案的縮圖影像。</span><span class="sxs-lookup"><span data-stu-id="68fcf-286">Gets the thumbnail image for the specified file.</span></span>

<span data-ttu-id="68fcf-287">參數</span><span class="sxs-lookup"><span data-stu-id="68fcf-287">Parameters</span></span>
* <span data-ttu-id="68fcf-288">檔案名：已要求縮圖的檔案名、hex64 編碼的檔案</span><span class="sxs-lookup"><span data-stu-id="68fcf-288">filename: Name, hex64 encoded, of the file for which the thumbnail is being requested</span></span>

<span data-ttu-id="68fcf-289">**/api/holographic/mrc/video/control/start (POST)**</span><span class="sxs-lookup"><span data-stu-id="68fcf-289">**/api/holographic/mrc/video/control/start (POST)**</span></span>

<span data-ttu-id="68fcf-290">開始混合現實記錄</span><span class="sxs-lookup"><span data-stu-id="68fcf-290">Starts a mixed reality recording</span></span>

<span data-ttu-id="68fcf-291">參數</span><span class="sxs-lookup"><span data-stu-id="68fcf-291">Parameters</span></span>
* <span data-ttu-id="68fcf-292">hololens：抓取全像： true 或 false (預設為 false) </span><span class="sxs-lookup"><span data-stu-id="68fcf-292">holo : capture holograms: true or false (defaults to false)</span></span>
* <span data-ttu-id="68fcf-293">pv： capture PV 攝影機： true 或 false (預設為 false) </span><span class="sxs-lookup"><span data-stu-id="68fcf-293">pv : capture PV camera: true or false (defaults to false)</span></span>
* <span data-ttu-id="68fcf-294">mic： capture 麥克風： true 或 false (預設為 false) </span><span class="sxs-lookup"><span data-stu-id="68fcf-294">mic : capture microphone: true or false (defaults to false)</span></span>
* <span data-ttu-id="68fcf-295">回送： capture app audio： true 或 false (預設為 false) </span><span class="sxs-lookup"><span data-stu-id="68fcf-295">loopback : capture app audio: true or false (defaults to false)</span></span>
* <span data-ttu-id="68fcf-296">RenderFromCamera： (只 HoloLens 2) 從相片/攝影機的觀點轉譯： true 或 false (預設為 true) </span><span class="sxs-lookup"><span data-stu-id="68fcf-296">RenderFromCamera : (HoloLens 2 only) render from perspective of photo/video camera: true or false (defaults to true)</span></span>
* <span data-ttu-id="68fcf-297">vstab： (只 HoloLens 2) 啟用影片穩定： true 或 false (預設為 true) </span><span class="sxs-lookup"><span data-stu-id="68fcf-297">vstab : (HoloLens 2 only) enable video stabilization: true or false (defaults to true)</span></span>
* <span data-ttu-id="68fcf-298">vstabbuffer： (只 HoloLens 2) video 穩定緩衝區延遲：0到30個畫面格 (預設為15個畫面格) </span><span class="sxs-lookup"><span data-stu-id="68fcf-298">vstabbuffer: (HoloLens 2 only) video stabilization buffer latency: 0 to 30 frames (defaults to 15 frames)</span></span>

<span data-ttu-id="68fcf-299">**/api/holographic/mrc/video/control/stop (POST)**</span><span class="sxs-lookup"><span data-stu-id="68fcf-299">**/api/holographic/mrc/video/control/stop (POST)**</span></span>

<span data-ttu-id="68fcf-300">停止目前的混合現實記錄</span><span class="sxs-lookup"><span data-stu-id="68fcf-300">Stops the current mixed reality recording</span></span>

## <a name="mixed-reality-streaming"></a><span data-ttu-id="68fcf-301">混合的現實串流</span><span class="sxs-lookup"><span data-stu-id="68fcf-301">Mixed Reality Streaming</span></span>

<span data-ttu-id="68fcf-302">HoloLens 透過區塊下載分散的數量，支援混合現實的即時預覽。</span><span class="sxs-lookup"><span data-stu-id="68fcf-302">HoloLens supports live preview of mixed reality via chunked download of a fragmented mp4.</span></span>

<span data-ttu-id="68fcf-303">混合的現實資料流程共用一組相同的參數來控制所要捕獲的內容：</span><span class="sxs-lookup"><span data-stu-id="68fcf-303">Mixed reality streams share the same set of parameters to control what is captured:</span></span>
* <span data-ttu-id="68fcf-304">hololens：抓取全像： true 或 false</span><span class="sxs-lookup"><span data-stu-id="68fcf-304">holo : capture holograms: true or false</span></span>
* <span data-ttu-id="68fcf-305">pv： capture PV 攝影機： true 或 false</span><span class="sxs-lookup"><span data-stu-id="68fcf-305">pv : capture PV camera: true or false</span></span>
* <span data-ttu-id="68fcf-306">mic： capture 麥克風： true 或 false</span><span class="sxs-lookup"><span data-stu-id="68fcf-306">mic : capture microphone: true or false</span></span>
* <span data-ttu-id="68fcf-307">回送：捕捉應用程式音訊： true 或 false</span><span class="sxs-lookup"><span data-stu-id="68fcf-307">loopback : capture app audio: true or false</span></span>

<span data-ttu-id="68fcf-308">如果未指定這些任何一項：將會捕捉全像照片、相片/攝影機和應用程式音訊</span><span class="sxs-lookup"><span data-stu-id="68fcf-308">If none of these are specified: holograms, photo/video camera, and app audio will be captured</span></span><br>
<span data-ttu-id="68fcf-309">如果有指定任何參數：未指定的參數會預設為 false</span><span class="sxs-lookup"><span data-stu-id="68fcf-309">If any are specified: the unspecified parameters will default to false</span></span>

<span data-ttu-id="68fcf-310"> (只 HoloLens 2) 的選擇性參數</span><span class="sxs-lookup"><span data-stu-id="68fcf-310">Optional parameters (HoloLens 2 only)</span></span>
* <span data-ttu-id="68fcf-311">RenderFromCamera：從相片/攝影機的觀點來呈現： true 或 false (預設為 true) </span><span class="sxs-lookup"><span data-stu-id="68fcf-311">RenderFromCamera : render from perspective of photo/video camera: true or false (defaults to true)</span></span>
* <span data-ttu-id="68fcf-312">vstab：啟用影片穩定： true 或 false (預設為 false) </span><span class="sxs-lookup"><span data-stu-id="68fcf-312">vstab : enable video stabilization: true or false (defaults to false)</span></span>
* <span data-ttu-id="68fcf-313">vstabbuffer：影片穩定緩衝區延遲：0到30個畫面格 (預設為15個畫面格) </span><span class="sxs-lookup"><span data-stu-id="68fcf-313">vstabbuffer: video stabilization buffer latency: 0 to 30 frames (defaults to 15 frames)</span></span>

<span data-ttu-id="68fcf-314">**/api/holographic/stream/live.mp4 (取得)**</span><span class="sxs-lookup"><span data-stu-id="68fcf-314">**/api/holographic/stream/live.mp4 (GET)**</span></span>

<span data-ttu-id="68fcf-315">1280x720p 30fps 5Mbit 串流。</span><span class="sxs-lookup"><span data-stu-id="68fcf-315">A 1280x720p 30fps 5Mbit stream.</span></span>

<span data-ttu-id="68fcf-316">**/api/holographic/stream/live_high.mp4 (取得)**</span><span class="sxs-lookup"><span data-stu-id="68fcf-316">**/api/holographic/stream/live_high.mp4 (GET)**</span></span>

<span data-ttu-id="68fcf-317">1280x720p 30fps 5Mbit 串流。</span><span class="sxs-lookup"><span data-stu-id="68fcf-317">A 1280x720p 30fps 5Mbit stream.</span></span>

<span data-ttu-id="68fcf-318">**/api/holographic/stream/live_med.mp4 (取得)**</span><span class="sxs-lookup"><span data-stu-id="68fcf-318">**/api/holographic/stream/live_med.mp4 (GET)**</span></span>

<span data-ttu-id="68fcf-319">854x480p 30fps 2.5 Mbit 串流。</span><span class="sxs-lookup"><span data-stu-id="68fcf-319">A 854x480p 30fps 2.5Mbit stream.</span></span>

<span data-ttu-id="68fcf-320">**/api/holographic/stream/live_low.mp4 (取得)**</span><span class="sxs-lookup"><span data-stu-id="68fcf-320">**/api/holographic/stream/live_low.mp4 (GET)**</span></span>

<span data-ttu-id="68fcf-321">428x240p 15fps 0.6 Mbit 串流。</span><span class="sxs-lookup"><span data-stu-id="68fcf-321">A 428x240p 15fps 0.6Mbit stream.</span></span>

## <a name="networking"></a><span data-ttu-id="68fcf-322">網路功能</span><span class="sxs-lookup"><span data-stu-id="68fcf-322">Networking</span></span>

<span data-ttu-id="68fcf-323">**/api/networking/ipconfig (取得)**</span><span class="sxs-lookup"><span data-stu-id="68fcf-323">**/api/networking/ipconfig (GET)**</span></span>

<span data-ttu-id="68fcf-324">取得目前的 ip 設定</span><span class="sxs-lookup"><span data-stu-id="68fcf-324">Gets the current ip configuration</span></span>

## <a name="os-information"></a><span data-ttu-id="68fcf-325">作業系統資訊</span><span class="sxs-lookup"><span data-stu-id="68fcf-325">OS Information</span></span>

<span data-ttu-id="68fcf-326">**/api/os/info (取得)**</span><span class="sxs-lookup"><span data-stu-id="68fcf-326">**/api/os/info (GET)**</span></span>

<span data-ttu-id="68fcf-327">取得作業系統資訊</span><span class="sxs-lookup"><span data-stu-id="68fcf-327">Gets operating system information</span></span>

<span data-ttu-id="68fcf-328">**/api/os/machinename (取得)**</span><span class="sxs-lookup"><span data-stu-id="68fcf-328">**/api/os/machinename (GET)**</span></span>

<span data-ttu-id="68fcf-329">取得電腦名稱稱</span><span class="sxs-lookup"><span data-stu-id="68fcf-329">Gets the machine name</span></span>

<span data-ttu-id="68fcf-330">**/api/os/machinename (POST)**</span><span class="sxs-lookup"><span data-stu-id="68fcf-330">**/api/os/machinename (POST)**</span></span>

<span data-ttu-id="68fcf-331">設定電腦名稱稱</span><span class="sxs-lookup"><span data-stu-id="68fcf-331">Sets the machine name</span></span>

<span data-ttu-id="68fcf-332">參數</span><span class="sxs-lookup"><span data-stu-id="68fcf-332">Parameters</span></span>
* <span data-ttu-id="68fcf-333">名稱：新電腦名稱稱、hex64 編碼、設定為</span><span class="sxs-lookup"><span data-stu-id="68fcf-333">name : New machine name, hex64 encoded, to set to</span></span>

## <a name="perception-simulation-control"></a><span data-ttu-id="68fcf-334">認知模擬控制項</span><span class="sxs-lookup"><span data-stu-id="68fcf-334">Perception Simulation Control</span></span>

<span data-ttu-id="68fcf-335">**/api/holographic/simulation/control/mode (取得)**</span><span class="sxs-lookup"><span data-stu-id="68fcf-335">**/api/holographic/simulation/control/mode (GET)**</span></span>

<span data-ttu-id="68fcf-336">取得模擬模式</span><span class="sxs-lookup"><span data-stu-id="68fcf-336">Get the simulation mode</span></span>

<span data-ttu-id="68fcf-337">**/api/holographic/simulation/control/mode (POST)**</span><span class="sxs-lookup"><span data-stu-id="68fcf-337">**/api/holographic/simulation/control/mode (POST)**</span></span>

<span data-ttu-id="68fcf-338">設定模擬模式</span><span class="sxs-lookup"><span data-stu-id="68fcf-338">Set the simulation mode</span></span>

<span data-ttu-id="68fcf-339">參數</span><span class="sxs-lookup"><span data-stu-id="68fcf-339">Parameters</span></span>
* <span data-ttu-id="68fcf-340">模式：模擬模式：預設、模擬、遠端、舊版</span><span class="sxs-lookup"><span data-stu-id="68fcf-340">mode : simulation mode: default, simulation, remote, legacy</span></span>

<span data-ttu-id="68fcf-341">**/api/holographic/simulation/control/stream (刪除)**</span><span class="sxs-lookup"><span data-stu-id="68fcf-341">**/api/holographic/simulation/control/stream (DELETE)**</span></span>

<span data-ttu-id="68fcf-342">刪除控制資料流程。</span><span class="sxs-lookup"><span data-stu-id="68fcf-342">Delete a control stream.</span></span>

<span data-ttu-id="68fcf-343">**/api/holographic/simulation/control/stream (GET/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="68fcf-343">**/api/holographic/simulation/control/stream (GET/WebSocket)**</span></span>

<span data-ttu-id="68fcf-344">開啟控制項資料流程的 web 通訊端連接。</span><span class="sxs-lookup"><span data-stu-id="68fcf-344">Open a web socket connection for a control stream.</span></span>

<span data-ttu-id="68fcf-345">**/api/holographic/simulation/control/stream (POST)**</span><span class="sxs-lookup"><span data-stu-id="68fcf-345">**/api/holographic/simulation/control/stream (POST)**</span></span>

<span data-ttu-id="68fcf-346">建立控制項資料流程 (需要優先權) 或將資料張貼至建立的資料流程 (streamId 必要) 。</span><span class="sxs-lookup"><span data-stu-id="68fcf-346">Create a control stream (priority is required) or post data to a created stream (streamId required).</span></span> <span data-ttu-id="68fcf-347">張貼的資料應為 ' application/八進位-stream ' 類型。</span><span class="sxs-lookup"><span data-stu-id="68fcf-347">Posted data is expected to be of type 'application/octet-stream'.</span></span>

<span data-ttu-id="68fcf-348">**/api/holographic/simulation/display/stream (GET/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="68fcf-348">**/api/holographic/simulation/display/stream (GET/WebSocket)**</span></span>

<span data-ttu-id="68fcf-349">要求模擬影片串流，其中包含在「模擬」模式中呈現給系統顯示的內容。</span><span class="sxs-lookup"><span data-stu-id="68fcf-349">Request a simulation video stream containing the content rendered to the system display when in 'Simulation' mode.</span></span>  <span data-ttu-id="68fcf-350">一開始會傳送簡單的格式描述元標頭，後面接著 h.264 編碼的材質，每個標頭前面都有一個標頭，表示眼睛索引和材質大小。</span><span class="sxs-lookup"><span data-stu-id="68fcf-350">A simple format descriptor header will be sent initially, followed by H.264-encoded textures, each preceded by a header indicating the eye index and texture size.</span></span>

## <a name="perception-simulation-playback"></a><span data-ttu-id="68fcf-351">感知模擬播放</span><span class="sxs-lookup"><span data-stu-id="68fcf-351">Perception Simulation Playback</span></span>

<span data-ttu-id="68fcf-352">**/api/holographic/simulation/playback/file (刪除)**</span><span class="sxs-lookup"><span data-stu-id="68fcf-352">**/api/holographic/simulation/playback/file (DELETE)**</span></span>

<span data-ttu-id="68fcf-353">刪除錄製。</span><span class="sxs-lookup"><span data-stu-id="68fcf-353">Delete a recording.</span></span>

<span data-ttu-id="68fcf-354">參數</span><span class="sxs-lookup"><span data-stu-id="68fcf-354">Parameters</span></span>
* <span data-ttu-id="68fcf-355">錄製：要刪除的記錄名稱。</span><span class="sxs-lookup"><span data-stu-id="68fcf-355">recording : Name of recording to delete.</span></span>

<span data-ttu-id="68fcf-356">**/api/holographic/simulation/playback/file (POST)**</span><span class="sxs-lookup"><span data-stu-id="68fcf-356">**/api/holographic/simulation/playback/file (POST)**</span></span>

<span data-ttu-id="68fcf-357">上傳錄製。</span><span class="sxs-lookup"><span data-stu-id="68fcf-357">Upload a recording.</span></span>

<span data-ttu-id="68fcf-358">**/api/holographic/simulation/playback/files (取得)**</span><span class="sxs-lookup"><span data-stu-id="68fcf-358">**/api/holographic/simulation/playback/files (GET)**</span></span>

<span data-ttu-id="68fcf-359">取得所有錄製。</span><span class="sxs-lookup"><span data-stu-id="68fcf-359">Get all recordings.</span></span>

<span data-ttu-id="68fcf-360">**/api/holographic/simulation/playback/session (取得)**</span><span class="sxs-lookup"><span data-stu-id="68fcf-360">**/api/holographic/simulation/playback/session (GET)**</span></span>

<span data-ttu-id="68fcf-361">取得錄製的目前播放狀態。</span><span class="sxs-lookup"><span data-stu-id="68fcf-361">Get the current playback state of a recording.</span></span>

<span data-ttu-id="68fcf-362">參數</span><span class="sxs-lookup"><span data-stu-id="68fcf-362">Parameters</span></span>
* <span data-ttu-id="68fcf-363">錄製：錄製的名稱。</span><span class="sxs-lookup"><span data-stu-id="68fcf-363">recording : Name of recording.</span></span>

<span data-ttu-id="68fcf-364">**/api/holographic/simulation/playback/session/file (刪除)**</span><span class="sxs-lookup"><span data-stu-id="68fcf-364">**/api/holographic/simulation/playback/session/file (DELETE)**</span></span>

<span data-ttu-id="68fcf-365">卸載錄製。</span><span class="sxs-lookup"><span data-stu-id="68fcf-365">Unload a recording.</span></span>

<span data-ttu-id="68fcf-366">參數</span><span class="sxs-lookup"><span data-stu-id="68fcf-366">Parameters</span></span>
* <span data-ttu-id="68fcf-367">記錄：要卸載的記錄名稱。</span><span class="sxs-lookup"><span data-stu-id="68fcf-367">recording : Name of recording to unload.</span></span>

<span data-ttu-id="68fcf-368">**/api/holographic/simulation/playback/session/file (POST)**</span><span class="sxs-lookup"><span data-stu-id="68fcf-368">**/api/holographic/simulation/playback/session/file (POST)**</span></span>

<span data-ttu-id="68fcf-369">載入錄製。</span><span class="sxs-lookup"><span data-stu-id="68fcf-369">Load a recording.</span></span>

<span data-ttu-id="68fcf-370">參數</span><span class="sxs-lookup"><span data-stu-id="68fcf-370">Parameters</span></span>
* <span data-ttu-id="68fcf-371">記錄：要載入的記錄名稱。</span><span class="sxs-lookup"><span data-stu-id="68fcf-371">recording : Name of recording to load.</span></span>

<span data-ttu-id="68fcf-372">**/api/holographic/simulation/playback/session/files (取得)**</span><span class="sxs-lookup"><span data-stu-id="68fcf-372">**/api/holographic/simulation/playback/session/files (GET)**</span></span>

<span data-ttu-id="68fcf-373">取得所有載入的記錄。</span><span class="sxs-lookup"><span data-stu-id="68fcf-373">Get all loaded recordings.</span></span>

<span data-ttu-id="68fcf-374">**/api/holographic/simulation/playback/session/pause (POST)**</span><span class="sxs-lookup"><span data-stu-id="68fcf-374">**/api/holographic/simulation/playback/session/pause (POST)**</span></span>

<span data-ttu-id="68fcf-375">暫停錄製。</span><span class="sxs-lookup"><span data-stu-id="68fcf-375">Pause a recording.</span></span>

<span data-ttu-id="68fcf-376">參數</span><span class="sxs-lookup"><span data-stu-id="68fcf-376">Parameters</span></span>
* <span data-ttu-id="68fcf-377">錄製：錄製的名稱。</span><span class="sxs-lookup"><span data-stu-id="68fcf-377">recording : Name of recording.</span></span>

<span data-ttu-id="68fcf-378">**/api/holographic/simulation/playback/session/play (POST)**</span><span class="sxs-lookup"><span data-stu-id="68fcf-378">**/api/holographic/simulation/playback/session/play (POST)**</span></span>

<span data-ttu-id="68fcf-379">播放錄製。</span><span class="sxs-lookup"><span data-stu-id="68fcf-379">Play a recording.</span></span>

<span data-ttu-id="68fcf-380">參數</span><span class="sxs-lookup"><span data-stu-id="68fcf-380">Parameters</span></span>
* <span data-ttu-id="68fcf-381">錄製：錄製的名稱。</span><span class="sxs-lookup"><span data-stu-id="68fcf-381">recording : Name of recording.</span></span>

<span data-ttu-id="68fcf-382">**/api/holographic/simulation/playback/session/stop (POST)**</span><span class="sxs-lookup"><span data-stu-id="68fcf-382">**/api/holographic/simulation/playback/session/stop (POST)**</span></span>

<span data-ttu-id="68fcf-383">停止錄製。</span><span class="sxs-lookup"><span data-stu-id="68fcf-383">Stop a recording.</span></span>

<span data-ttu-id="68fcf-384">參數</span><span class="sxs-lookup"><span data-stu-id="68fcf-384">Parameters</span></span>
* <span data-ttu-id="68fcf-385">錄製：錄製的名稱。</span><span class="sxs-lookup"><span data-stu-id="68fcf-385">recording : Name of recording.</span></span>

<span data-ttu-id="68fcf-386">**/api/holographic/simulation/playback/session/types (取得)**</span><span class="sxs-lookup"><span data-stu-id="68fcf-386">**/api/holographic/simulation/playback/session/types (GET)**</span></span>

<span data-ttu-id="68fcf-387">取得載入錄製中的資料類型。</span><span class="sxs-lookup"><span data-stu-id="68fcf-387">Get the types of data in a loaded recording.</span></span>

<span data-ttu-id="68fcf-388">參數</span><span class="sxs-lookup"><span data-stu-id="68fcf-388">Parameters</span></span>
* <span data-ttu-id="68fcf-389">錄製：錄製的名稱。</span><span class="sxs-lookup"><span data-stu-id="68fcf-389">recording : Name of recording.</span></span>

## <a name="perception-simulation-recording"></a><span data-ttu-id="68fcf-390">感知模擬錄製</span><span class="sxs-lookup"><span data-stu-id="68fcf-390">Perception Simulation Recording</span></span>

<span data-ttu-id="68fcf-391">**/api/holographic/simulation/recording/start (POST)**</span><span class="sxs-lookup"><span data-stu-id="68fcf-391">**/api/holographic/simulation/recording/start (POST)**</span></span>

<span data-ttu-id="68fcf-392">開始錄製。</span><span class="sxs-lookup"><span data-stu-id="68fcf-392">Start a recording.</span></span> <span data-ttu-id="68fcf-393">一次只能有一個作用中的記錄。</span><span class="sxs-lookup"><span data-stu-id="68fcf-393">Only a single recording can be active at once.</span></span> <span data-ttu-id="68fcf-394">必須設定 head、雙手、spatialMapping 或環境之一。</span><span class="sxs-lookup"><span data-stu-id="68fcf-394">One of head, hands, spatialMapping or environment must be set.</span></span>

<span data-ttu-id="68fcf-395">參數</span><span class="sxs-lookup"><span data-stu-id="68fcf-395">Parameters</span></span>
* <span data-ttu-id="68fcf-396">head：設定為1以記錄 head 資料。</span><span class="sxs-lookup"><span data-stu-id="68fcf-396">head : Set to 1 to record head data.</span></span>
* <span data-ttu-id="68fcf-397">雙手：設定為1以記錄手資料。</span><span class="sxs-lookup"><span data-stu-id="68fcf-397">hands : Set to 1 to record hand data.</span></span>
* <span data-ttu-id="68fcf-398">spatialMapping：設定為1以記錄空間對應。</span><span class="sxs-lookup"><span data-stu-id="68fcf-398">spatialMapping : Set to 1 to record spatial mapping.</span></span>
* <span data-ttu-id="68fcf-399">環境：設定為1以記錄環境資料。</span><span class="sxs-lookup"><span data-stu-id="68fcf-399">environment : Set to 1 to record environment data.</span></span>
* <span data-ttu-id="68fcf-400">名稱：錄製的名稱。</span><span class="sxs-lookup"><span data-stu-id="68fcf-400">name : Name of the recording.</span></span>
* <span data-ttu-id="68fcf-401">singleSpatialMappingFrame：設定為1只記錄單一空間對應框架。</span><span class="sxs-lookup"><span data-stu-id="68fcf-401">singleSpatialMappingFrame : Set to 1 to record only a single spatial mapping frame.</span></span>

<span data-ttu-id="68fcf-402">**/api/holographic/simulation/recording/status (取得)**</span><span class="sxs-lookup"><span data-stu-id="68fcf-402">**/api/holographic/simulation/recording/status (GET)**</span></span>

<span data-ttu-id="68fcf-403">取得錄製狀態。</span><span class="sxs-lookup"><span data-stu-id="68fcf-403">Get recording state.</span></span>

<span data-ttu-id="68fcf-404">**/api/holographic/simulation/recording/stop (取得)**</span><span class="sxs-lookup"><span data-stu-id="68fcf-404">**/api/holographic/simulation/recording/stop (GET)**</span></span>

<span data-ttu-id="68fcf-405">停止目前的錄製。</span><span class="sxs-lookup"><span data-stu-id="68fcf-405">Stop the current recording.</span></span> <span data-ttu-id="68fcf-406">記錄會以檔案的形式傳回。</span><span class="sxs-lookup"><span data-stu-id="68fcf-406">Recording will be returned as a file.</span></span>

## <a name="performance-data"></a><span data-ttu-id="68fcf-407">效能資料</span><span class="sxs-lookup"><span data-stu-id="68fcf-407">Performance data</span></span>

<span data-ttu-id="68fcf-408">**/api/resourcemanager/processes (取得)**</span><span class="sxs-lookup"><span data-stu-id="68fcf-408">**/api/resourcemanager/processes (GET)**</span></span>

<span data-ttu-id="68fcf-409">傳回執行中進程的清單，並提供詳細資料</span><span class="sxs-lookup"><span data-stu-id="68fcf-409">Returns the list of running processes with details</span></span>

<span data-ttu-id="68fcf-410">傳回資料</span><span class="sxs-lookup"><span data-stu-id="68fcf-410">Return data</span></span>
* <span data-ttu-id="68fcf-411">JSON 與進程清單以及每個進程的詳細資料</span><span class="sxs-lookup"><span data-stu-id="68fcf-411">JSON with list of processes and details for each process</span></span>

<span data-ttu-id="68fcf-412">**/api/resourcemanager/systemperf (取得)**</span><span class="sxs-lookup"><span data-stu-id="68fcf-412">**/api/resourcemanager/systemperf (GET)**</span></span>

<span data-ttu-id="68fcf-413">傳回系統效能統計資料 (i/o 讀取/寫入、記憶體統計資料等。</span><span class="sxs-lookup"><span data-stu-id="68fcf-413">Returns system perf statistics (I/O read/write, memory stats etc.</span></span>

<span data-ttu-id="68fcf-414">傳回資料</span><span class="sxs-lookup"><span data-stu-id="68fcf-414">Return data</span></span>
* <span data-ttu-id="68fcf-415">具有系統資訊的 JSON： CPU、GPU、記憶體、網路、IO</span><span class="sxs-lookup"><span data-stu-id="68fcf-415">JSON with system information: CPU, GPU, Memory, Network, IO</span></span>

## <a name="power"></a><span data-ttu-id="68fcf-416">電源</span><span class="sxs-lookup"><span data-stu-id="68fcf-416">Power</span></span>

<span data-ttu-id="68fcf-417">**/api/power/battery (取得)**</span><span class="sxs-lookup"><span data-stu-id="68fcf-417">**/api/power/battery (GET)**</span></span>

<span data-ttu-id="68fcf-418">取得目前的電池狀態</span><span class="sxs-lookup"><span data-stu-id="68fcf-418">Gets the current battery state</span></span>

<span data-ttu-id="68fcf-419">**/api/power/state (取得)**</span><span class="sxs-lookup"><span data-stu-id="68fcf-419">**/api/power/state (GET)**</span></span>

<span data-ttu-id="68fcf-420">檢查系統是否處於低電源狀態</span><span class="sxs-lookup"><span data-stu-id="68fcf-420">Checks if the system is in a low power state</span></span>

## <a name="remote-control"></a><span data-ttu-id="68fcf-421">遠端控制</span><span class="sxs-lookup"><span data-stu-id="68fcf-421">Remote Control</span></span>

<span data-ttu-id="68fcf-422">**/api/control/restart (POST)**</span><span class="sxs-lookup"><span data-stu-id="68fcf-422">**/api/control/restart (POST)**</span></span>

<span data-ttu-id="68fcf-423">重新開機目標裝置</span><span class="sxs-lookup"><span data-stu-id="68fcf-423">Restarts the target device</span></span>

<span data-ttu-id="68fcf-424">**/api/control/shutdown (POST)**</span><span class="sxs-lookup"><span data-stu-id="68fcf-424">**/api/control/shutdown (POST)**</span></span>

<span data-ttu-id="68fcf-425">關閉目標裝置</span><span class="sxs-lookup"><span data-stu-id="68fcf-425">Shuts down the target device</span></span>

## <a name="task-manager"></a><span data-ttu-id="68fcf-426">工作管理員</span><span class="sxs-lookup"><span data-stu-id="68fcf-426">Task Manager</span></span>

<span data-ttu-id="68fcf-427">**/api/taskmanager/app (刪除)**</span><span class="sxs-lookup"><span data-stu-id="68fcf-427">**/api/taskmanager/app (DELETE)**</span></span>

<span data-ttu-id="68fcf-428">停止新式應用程式</span><span class="sxs-lookup"><span data-stu-id="68fcf-428">Stops a modern app</span></span>

<span data-ttu-id="68fcf-429">參數</span><span class="sxs-lookup"><span data-stu-id="68fcf-429">Parameters</span></span>
* <span data-ttu-id="68fcf-430">封裝：應用程式套件的完整名稱，hex64 編碼</span><span class="sxs-lookup"><span data-stu-id="68fcf-430">package : Full name of the app package, hex64 encoded</span></span>
* <span data-ttu-id="68fcf-431">forcestop：強制所有進程停止 (= 是) </span><span class="sxs-lookup"><span data-stu-id="68fcf-431">forcestop : Force all processes to stop (=yes)</span></span>

<span data-ttu-id="68fcf-432">**/api/taskmanager/app (POST)**</span><span class="sxs-lookup"><span data-stu-id="68fcf-432">**/api/taskmanager/app (POST)**</span></span>

<span data-ttu-id="68fcf-433">啟動新式應用程式</span><span class="sxs-lookup"><span data-stu-id="68fcf-433">Starts a modern app</span></span>

<span data-ttu-id="68fcf-434">參數</span><span class="sxs-lookup"><span data-stu-id="68fcf-434">Parameters</span></span>
* <span data-ttu-id="68fcf-435">appid：要啟動的應用程式 PRAID，hex64 編碼</span><span class="sxs-lookup"><span data-stu-id="68fcf-435">appid : PRAID of app to start, hex64 encoded</span></span>
* <span data-ttu-id="68fcf-436">封裝：應用程式套件的完整名稱，hex64 編碼</span><span class="sxs-lookup"><span data-stu-id="68fcf-436">package : Full name of the app package, hex64 encoded</span></span>

## <a name="wifi-management"></a><span data-ttu-id="68fcf-437">WiFi 管理</span><span class="sxs-lookup"><span data-stu-id="68fcf-437">WiFi Management</span></span>

<span data-ttu-id="68fcf-438">**/api/wifi/interfaces (取得)**</span><span class="sxs-lookup"><span data-stu-id="68fcf-438">**/api/wifi/interfaces (GET)**</span></span>

<span data-ttu-id="68fcf-439">列舉無線網路介面</span><span class="sxs-lookup"><span data-stu-id="68fcf-439">Enumerates wireless network interfaces</span></span>

<span data-ttu-id="68fcf-440">傳回資料</span><span class="sxs-lookup"><span data-stu-id="68fcf-440">Return data</span></span>
* <span data-ttu-id="68fcf-441">具有詳細資料 (GUID、描述等 ) 的無線介面清單</span><span class="sxs-lookup"><span data-stu-id="68fcf-441">List of wireless interfaces with details (GUID, description etc.)</span></span>

<span data-ttu-id="68fcf-442">**/api/wifi/network (刪除)**</span><span class="sxs-lookup"><span data-stu-id="68fcf-442">**/api/wifi/network (DELETE)**</span></span>

<span data-ttu-id="68fcf-443">刪除與指定介面上的網路相關聯的設定檔</span><span class="sxs-lookup"><span data-stu-id="68fcf-443">Deletes a profile associated with a network on a specified interface</span></span>

<span data-ttu-id="68fcf-444">參數</span><span class="sxs-lookup"><span data-stu-id="68fcf-444">Parameters</span></span>
* <span data-ttu-id="68fcf-445">介面：網路介面 guid</span><span class="sxs-lookup"><span data-stu-id="68fcf-445">interface : network interface guid</span></span>
* <span data-ttu-id="68fcf-446">設定檔：設定檔名稱</span><span class="sxs-lookup"><span data-stu-id="68fcf-446">profile : profile name</span></span>

<span data-ttu-id="68fcf-447">**/api/wifi/networks (取得)**</span><span class="sxs-lookup"><span data-stu-id="68fcf-447">**/api/wifi/networks (GET)**</span></span>

<span data-ttu-id="68fcf-448">列舉指定網路介面上的無線網路</span><span class="sxs-lookup"><span data-stu-id="68fcf-448">Enumerates wireless networks on the specified network interface</span></span>

<span data-ttu-id="68fcf-449">參數</span><span class="sxs-lookup"><span data-stu-id="68fcf-449">Parameters</span></span>
* <span data-ttu-id="68fcf-450">介面：網路介面 guid</span><span class="sxs-lookup"><span data-stu-id="68fcf-450">interface : network interface guid</span></span>

<span data-ttu-id="68fcf-451">傳回資料</span><span class="sxs-lookup"><span data-stu-id="68fcf-451">Return data</span></span>
* <span data-ttu-id="68fcf-452">網路介面上找到的無線網路清單與詳細資料</span><span class="sxs-lookup"><span data-stu-id="68fcf-452">List of wireless networks found on the network interface with details</span></span>

<span data-ttu-id="68fcf-453">**/api/wifi/network (POST)**</span><span class="sxs-lookup"><span data-stu-id="68fcf-453">**/api/wifi/network (POST)**</span></span>

<span data-ttu-id="68fcf-454">連接或中斷指定介面上的網路連線</span><span class="sxs-lookup"><span data-stu-id="68fcf-454">Connects or disconnects to a network on the specified interface</span></span>

<span data-ttu-id="68fcf-455">參數</span><span class="sxs-lookup"><span data-stu-id="68fcf-455">Parameters</span></span>
* <span data-ttu-id="68fcf-456">介面：網路介面 guid</span><span class="sxs-lookup"><span data-stu-id="68fcf-456">interface : network interface guid</span></span>
* <span data-ttu-id="68fcf-457">ssid： ssid、hex64 編碼、要連接的</span><span class="sxs-lookup"><span data-stu-id="68fcf-457">ssid : ssid, hex64 encoded, to connect to</span></span>
* <span data-ttu-id="68fcf-458">op：連線或中斷連接</span><span class="sxs-lookup"><span data-stu-id="68fcf-458">op : connect or disconnect</span></span>
* <span data-ttu-id="68fcf-459">createprofile：是或否</span><span class="sxs-lookup"><span data-stu-id="68fcf-459">createprofile : yes or no</span></span>
* <span data-ttu-id="68fcf-460">機碼：共用金鑰，hex64 編碼</span><span class="sxs-lookup"><span data-stu-id="68fcf-460">key : shared key, hex64 encoded</span></span>

## <a name="windows-performance-recorder"></a><span data-ttu-id="68fcf-461">Windows Performance Recorder</span><span class="sxs-lookup"><span data-stu-id="68fcf-461">Windows Performance Recorder</span></span>

<span data-ttu-id="68fcf-462">**/api/wpr/customtrace (POST)**</span><span class="sxs-lookup"><span data-stu-id="68fcf-462">**/api/wpr/customtrace (POST)**</span></span>

<span data-ttu-id="68fcf-463">上傳 WPR 設定檔，並使用上傳的設定檔開始追蹤。</span><span class="sxs-lookup"><span data-stu-id="68fcf-463">Uploads a WPR profile and starts tracing using the uploaded profile.</span></span>

<span data-ttu-id="68fcf-464">Payload</span><span class="sxs-lookup"><span data-stu-id="68fcf-464">Payload</span></span>
* <span data-ttu-id="68fcf-465">多部分的符合 HTTP 主體</span><span class="sxs-lookup"><span data-stu-id="68fcf-465">multi-part conforming http body</span></span>

<span data-ttu-id="68fcf-466">傳回資料</span><span class="sxs-lookup"><span data-stu-id="68fcf-466">Return data</span></span>
* <span data-ttu-id="68fcf-467">傳回 WPR 會話狀態。</span><span class="sxs-lookup"><span data-stu-id="68fcf-467">Returns the WPR session status.</span></span>

<span data-ttu-id="68fcf-468">**/api/wpr/status (取得)**</span><span class="sxs-lookup"><span data-stu-id="68fcf-468">**/api/wpr/status (GET)**</span></span>

<span data-ttu-id="68fcf-469">捕獲 WPR 會話的狀態</span><span class="sxs-lookup"><span data-stu-id="68fcf-469">Retrieves the status of the WPR session</span></span>

<span data-ttu-id="68fcf-470">傳回資料</span><span class="sxs-lookup"><span data-stu-id="68fcf-470">Return data</span></span>
* <span data-ttu-id="68fcf-471">WPR 會話狀態。</span><span class="sxs-lookup"><span data-stu-id="68fcf-471">WPR session status.</span></span>

<span data-ttu-id="68fcf-472">**/api/wpr/trace (取得)**</span><span class="sxs-lookup"><span data-stu-id="68fcf-472">**/api/wpr/trace (GET)**</span></span>

<span data-ttu-id="68fcf-473">停止 WPR (效能) 追蹤會話</span><span class="sxs-lookup"><span data-stu-id="68fcf-473">Stops a WPR (performance) tracing session</span></span>

<span data-ttu-id="68fcf-474">傳回資料</span><span class="sxs-lookup"><span data-stu-id="68fcf-474">Return data</span></span>
* <span data-ttu-id="68fcf-475">傳回追蹤 ETL 檔案</span><span class="sxs-lookup"><span data-stu-id="68fcf-475">Returns the trace ETL file</span></span>

<span data-ttu-id="68fcf-476">**/api/wpr/trace (POST)**</span><span class="sxs-lookup"><span data-stu-id="68fcf-476">**/api/wpr/trace (POST)**</span></span>

<span data-ttu-id="68fcf-477">啟動 WPR (效能) 追蹤會話</span><span class="sxs-lookup"><span data-stu-id="68fcf-477">Starts a WPR (performance) tracing sessions</span></span>

<span data-ttu-id="68fcf-478">參數</span><span class="sxs-lookup"><span data-stu-id="68fcf-478">Parameters</span></span>
* <span data-ttu-id="68fcf-479">設定檔：設定檔名稱。</span><span class="sxs-lookup"><span data-stu-id="68fcf-479">profile : Profile name.</span></span> <span data-ttu-id="68fcf-480">可用的設定檔會儲存在 perfprofiles/profiles.js</span><span class="sxs-lookup"><span data-stu-id="68fcf-480">Available profiles are stored in perfprofiles/profiles.json</span></span>

<span data-ttu-id="68fcf-481">傳回資料</span><span class="sxs-lookup"><span data-stu-id="68fcf-481">Return data</span></span>
* <span data-ttu-id="68fcf-482">在開始時，會傳回 WPR 會話狀態。</span><span class="sxs-lookup"><span data-stu-id="68fcf-482">On start, returns the WPR session status.</span></span>

## <a name="see-also"></a><span data-ttu-id="68fcf-483">另請參閱</span><span class="sxs-lookup"><span data-stu-id="68fcf-483">See also</span></span>
* [<span data-ttu-id="68fcf-484">使用 Windows 裝置入口網站</span><span class="sxs-lookup"><span data-stu-id="68fcf-484">Using the Windows Device Portal</span></span>](using-the-windows-device-portal.md)
* [<span data-ttu-id="68fcf-485">裝置入口網站 (UWP) 的核心 API 參考 </span><span class="sxs-lookup"><span data-stu-id="68fcf-485">Device Portal core API reference (UWP)</span></span>](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-api-core)
