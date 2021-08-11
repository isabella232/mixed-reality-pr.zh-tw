---
title: 追蹤常見問題
description: 追蹤超出標準取用者支援檔的 Windows Mixed Reality 疑難排解。
ms.topic: article
keywords: Windows Mixed Reality，混合的現實，虛擬實境，VR，MR，疑難排解，錯誤，協助，支援，追蹤
ms.openlocfilehash: fe5462a53de7b196db37edbbf0e56199a17c4c99b54ea1e7d9edf72e0845c9e5
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2021
ms.locfileid: "115199474"
---
# <a name="tracking-faqs"></a>追蹤常見問題

## <a name="my-headset-has-stopped-tracking"></a>我的耳機已停止追蹤

請確定燈開啟，而且沒有任何阻礙在耳機前方的內部追蹤攝影機。 如果遺失追蹤，可能需要幾秒鐘的時間才能繼續。 重新開機 Windows Mixed Reality 入口網站不會重新開機追蹤。

## <a name="i-can-look-around-but-i-cant-translate-im-stuck-in-3dof"></a>我可以查看，但無法轉譯 (我卡在 3DOF) 

這表示追蹤系統無法產生姿勢，或應用程式已停止使用新的姿勢資料來呈現。 若要修正此問題：

* 請確定房間有足夠的光線。
* 請確定房間有足夠的詳細資料可供追蹤。
* 拔下裝置，關閉 Windows Mixed Reality，然後重新插入裝置。
* 如果訊息持續存在，請洽詢 [客戶支援](https://support.microsoft.com/)

## <a name="the-view-in-the-hmd-is-frozen"></a>HMD 中的 view 已凍結

這通常表示應用程式或系統層級元件已失敗。 嘗試：

1. 按 [首頁] 按鈕以離開應用程式。
2. 拔掉裝置、關閉 MRP，然後重新插入裝置。
3. 將電腦重新開機。

## <a name="the-world-briefly-froze-and-tilted-or-flipped-upside-down-before-returning-to-normal"></a>在回到正常之前，世界短暫地旁邊、傾斜或翻轉

這可能是因為應用程式或系統層級元件發生嚴重錯誤或暫時性缺乏記憶體或 CPU 資源所造成。 若要檢查：

1. 開啟工作管理員並確定至少有20% 的 CPU 可用、400 MB 的記憶體可供使用，而磁片 IO 應低於80%。
2. 移至 **事件檢視器 > Windows 記錄 > 應用程式**，以查看凍結期間的任何錯誤。 尋找任何參考 HoloLens 感應器、混合現實或您在該時間執行之應用程式的相關事項。 這些記錄檔可能會說明造成失敗的原因。
3. 如果問題持續發生，請重新開機電腦。

## <a name="the-world-flipped-upside-down-momentarily-and-returned-to-normal"></a>世界會短暫反轉並回到正常狀態

這通常是因為從耳機取得感應器資料以通知追蹤演算法的錯誤所造成。 如果經常發生這種情況：

1. 將耳機插入不同的 USB 3.0 埠。
2. 將耳機直接插入電腦，而不是進入 USB 3.0 中樞。
3. 如果問題持續發生，請洽詢 [客戶支援](https://support.microsoft.com/)。

## <a name="the-world-is-tilted-but-i-can-navigate-and-walk-around-in-windows-mixed-reality"></a>世界是傾斜的，但我可以在 Windows Mixed Reality 中流覽和四處流覽

如果感應器資料錯誤記錄在您電腦上的環境資料中，可能會導致 Windows Mixed Reality 顯示為傾斜，有時會永久出現。 修正方法：

1. 拔掉耳機，關閉 Windows Mixed Reality 並插上耳機。
2. 將電腦重新開機。
3. 清除您的環境資料。