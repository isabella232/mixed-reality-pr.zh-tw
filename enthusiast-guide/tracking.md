---
title: 追蹤常見問題
description: 追蹤超出標準取用者支援檔的 Windows Mixed Reality 疑難排解。
ms.topic: article
keywords: Windows Mixed Reality，混合的現實，虛擬實境，VR，MR，疑難排解，錯誤，協助，支援，追蹤
ms.openlocfilehash: 2634b95cf876a5b540710f80d3dd7f9d48b3bad9
ms.sourcegitcommit: 1b90f27af091dffd4fba63d69a89873aa0f75079
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2020
ms.locfileid: "97725829"
---
# <a name="tracking-faqs"></a><span data-ttu-id="07bc4-104">追蹤常見問題</span><span class="sxs-lookup"><span data-stu-id="07bc4-104">Tracking FAQs</span></span>

## <a name="my-headset-has-stopped-tracking"></a><span data-ttu-id="07bc4-105">我的耳機已停止追蹤</span><span class="sxs-lookup"><span data-stu-id="07bc4-105">My headset has stopped tracking</span></span>

<span data-ttu-id="07bc4-106">請確定燈開啟，而且沒有任何阻礙在耳機前方的內部追蹤攝影機。</span><span class="sxs-lookup"><span data-stu-id="07bc4-106">Make sure the lights are on, and that there isn't anything obstructing the inside-out tracking cameras on the front of your headset.</span></span> <span data-ttu-id="07bc4-107">如果遺失追蹤，可能需要幾秒鐘的時間才能繼續。</span><span class="sxs-lookup"><span data-stu-id="07bc4-107">If tracking is lost, it can take a few seconds to resume.</span></span> <span data-ttu-id="07bc4-108">重新開機 Windows Mixed Reality 入口網站不會重新開機追蹤。</span><span class="sxs-lookup"><span data-stu-id="07bc4-108">Restart the Windows Mixed Reality Portal is tracking doesn't restart.</span></span>

## <a name="i-can-look-around-but-i-cant-translate-im-stuck-in-3dof"></a><span data-ttu-id="07bc4-109">我可以查看，但無法轉譯 (我卡在 3DOF) </span><span class="sxs-lookup"><span data-stu-id="07bc4-109">I can look around but I can't translate (I'm stuck in 3DOF)</span></span>

<span data-ttu-id="07bc4-110">這表示追蹤系統無法產生姿勢，或應用程式已停止使用新的姿勢資料來呈現。</span><span class="sxs-lookup"><span data-stu-id="07bc4-110">This means that the tracking system can't generate pose, or the application has stopped using new pose data to render.</span></span> <span data-ttu-id="07bc4-111">若要修正此問題：</span><span class="sxs-lookup"><span data-stu-id="07bc4-111">To fix the issue:</span></span>

* <span data-ttu-id="07bc4-112">請確定房間有足夠的光線。</span><span class="sxs-lookup"><span data-stu-id="07bc4-112">Make sure the room has enough light.</span></span>
* <span data-ttu-id="07bc4-113">請確定房間有足夠的詳細資料可供追蹤。</span><span class="sxs-lookup"><span data-stu-id="07bc4-113">Make sure the room has enough details to track.</span></span>
* <span data-ttu-id="07bc4-114">拔下裝置，關閉 Windows Mixed Reality，然後重新插入裝置。</span><span class="sxs-lookup"><span data-stu-id="07bc4-114">Unplug the device, close Windows Mixed Reality, and plug in the device again.</span></span>
* <span data-ttu-id="07bc4-115">如果訊息持續存在，請洽詢 [客戶支援](https://support.microsoft.com/)</span><span class="sxs-lookup"><span data-stu-id="07bc4-115">If the message persists, contact [customer support](https://support.microsoft.com/)</span></span>

## <a name="the-view-in-the-hmd-is-frozen"></a><span data-ttu-id="07bc4-116">HMD 中的 view 已凍結</span><span class="sxs-lookup"><span data-stu-id="07bc4-116">The view in the HMD is frozen</span></span>

<span data-ttu-id="07bc4-117">這通常表示應用程式或系統層級元件已失敗。</span><span class="sxs-lookup"><span data-stu-id="07bc4-117">This usually means the application or a system level component has failed.</span></span> <span data-ttu-id="07bc4-118">嘗試：</span><span class="sxs-lookup"><span data-stu-id="07bc4-118">Try to:</span></span>

1. <span data-ttu-id="07bc4-119">按 [首頁] 按鈕以離開應用程式。</span><span class="sxs-lookup"><span data-stu-id="07bc4-119">Press the "home" button to leave the application.</span></span>
2. <span data-ttu-id="07bc4-120">拔掉裝置、關閉 MRP，然後重新插入裝置。</span><span class="sxs-lookup"><span data-stu-id="07bc4-120">Unplug the device, close MRP, and plug the device back in.</span></span>
3. <span data-ttu-id="07bc4-121">將電腦重新開機。</span><span class="sxs-lookup"><span data-stu-id="07bc4-121">Restart the PC.</span></span>

## <a name="the-world-briefly-froze-and-tilted-or-flipped-upside-down-before-returning-to-normal"></a><span data-ttu-id="07bc4-122">在回到正常之前，世界短暫地旁邊、傾斜或翻轉</span><span class="sxs-lookup"><span data-stu-id="07bc4-122">The world briefly froze and tilted or flipped upside down before returning to normal</span></span>

<span data-ttu-id="07bc4-123">這可能是因為應用程式或系統層級元件發生嚴重錯誤或暫時性缺乏記憶體或 CPU 資源所造成。</span><span class="sxs-lookup"><span data-stu-id="07bc4-123">This could be caused by an application or system level component hitting a fatal error or a temporary lack of memory or CPU resources.</span></span> <span data-ttu-id="07bc4-124">若要檢查：</span><span class="sxs-lookup"><span data-stu-id="07bc4-124">To check:</span></span>

1. <span data-ttu-id="07bc4-125">開啟工作管理員並確定至少有20% 的 CPU 可用、400 MB 的記憶體可供使用，而磁片 IO 應低於80%。</span><span class="sxs-lookup"><span data-stu-id="07bc4-125">Open Task Manager and ensure that at least 20% of the CPU is free, 400 MB of memory is available and disk IO should be below 80%.</span></span>
2. <span data-ttu-id="07bc4-126">移至 **事件檢視器 > Windows 記錄 > 應用程式** ，以尋找凍結時間前後的任何錯誤。</span><span class="sxs-lookup"><span data-stu-id="07bc4-126">Go to **Event Viewer > Windows Logs > Application** to look for any errors from around the time of the freeze.</span></span> <span data-ttu-id="07bc4-127">尋找任何參考 HoloLens 感應器、混合現實或您在該時間執行之應用程式的任何事物。</span><span class="sxs-lookup"><span data-stu-id="07bc4-127">Look for anything that refers to HoloLens sensors, Mixed Reality, or the application that you were running around that time.</span></span> <span data-ttu-id="07bc4-128">這些記錄檔可能會說明造成失敗的原因。</span><span class="sxs-lookup"><span data-stu-id="07bc4-128">Those logs might explain what caused the failure.</span></span>
3. <span data-ttu-id="07bc4-129">如果問題持續發生，請重新開機電腦。</span><span class="sxs-lookup"><span data-stu-id="07bc4-129">Restart the PC if the problem persists.</span></span>

## <a name="the-world-flipped-upside-down-momentarily-and-returned-to-normal"></a><span data-ttu-id="07bc4-130">世界會短暫反轉並回到正常狀態</span><span class="sxs-lookup"><span data-stu-id="07bc4-130">The world flipped upside down momentarily and returned to normal</span></span>

<span data-ttu-id="07bc4-131">這通常是因為從耳機取得感應器資料以通知追蹤演算法的錯誤所造成。</span><span class="sxs-lookup"><span data-stu-id="07bc4-131">This is typically caused by errors in obtaining sensor data from the headset to inform the tracking algorithms.</span></span> <span data-ttu-id="07bc4-132">如果經常發生這種情況：</span><span class="sxs-lookup"><span data-stu-id="07bc4-132">If this happens frequently:</span></span>

1. <span data-ttu-id="07bc4-133">將耳機插入不同的 USB 3.0 埠。</span><span class="sxs-lookup"><span data-stu-id="07bc4-133">Plug the headset into a different USB 3.0 port.</span></span>
2. <span data-ttu-id="07bc4-134">將耳機直接插入電腦，而不是進入 USB 3.0 中樞。</span><span class="sxs-lookup"><span data-stu-id="07bc4-134">Plug the headset directly into the PC rather than into a USB 3.0 hub.</span></span>
3. <span data-ttu-id="07bc4-135">如果問題持續發生，請洽詢 [客戶支援](https://support.microsoft.com/)。</span><span class="sxs-lookup"><span data-stu-id="07bc4-135">If the problem persists, contact [customer support](https://support.microsoft.com/).</span></span>

## <a name="the-world-is-tilted-but-i-can-navigate-and-walk-around-in-windows-mixed-reality"></a><span data-ttu-id="07bc4-136">世界是傾斜的，但我可以在 Windows Mixed Reality 中流覽和四處流覽</span><span class="sxs-lookup"><span data-stu-id="07bc4-136">The world is tilted but I can navigate and walk around in Windows Mixed Reality</span></span>

<span data-ttu-id="07bc4-137">如果感應器資料錯誤記錄在您電腦上的環境資料中，可能會導致 Windows Mixed Reality 顯示為傾斜，有時會永久出現。</span><span class="sxs-lookup"><span data-stu-id="07bc4-137">If sensor data errors are recorded into the environment data on your PC, it can cause Windows Mixed Reality to appear tilted, sometimes permanently.</span></span> <span data-ttu-id="07bc4-138">修正方法：</span><span class="sxs-lookup"><span data-stu-id="07bc4-138">To fix this:</span></span>

1. <span data-ttu-id="07bc4-139">拔掉耳機，關閉 Windows Mixed Reality 並插上耳機。</span><span class="sxs-lookup"><span data-stu-id="07bc4-139">Unplug the headset, close Windows Mixed Reality and plug the headset back in.</span></span>
2. <span data-ttu-id="07bc4-140">將電腦重新開機。</span><span class="sxs-lookup"><span data-stu-id="07bc4-140">Restart the PC.</span></span>
3. <span data-ttu-id="07bc4-141">清除您的環境資料。</span><span class="sxs-lookup"><span data-stu-id="07bc4-141">Clear your environment data.</span></span>