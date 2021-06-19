---
title: Mixed Reality OpenXR 外掛程式版本資訊
description: 隨時掌握最新的版本資訊，並升級至 Mixed Reality OpenXR 外掛程式。
author: hferrone
ms.author: v-hferrone
ms.date: 06/18/2021
ms.topic: article
ms.localizationpriority: high
keywords: 最新狀態, 開始使用, 基本概念, unity, visual studio, 工具組, 混合實境頭戴式裝置, windows 混合實境頭戴式裝置, 虛擬實境頭戴式裝置, 安裝, Windows, HoloLens, 模擬器, unreal, openxr
ms.openlocfilehash: c926fbb758d7cfaa2e73b5357cacdab7a5d15e27
ms.sourcegitcommit: 6ade7e8ebab7003fc24f9e0b5fa81d091369622c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2021
ms.locfileid: "112394646"
---
# <a name="mixed-reality-openxr-plugin-release-notes"></a>Mixed Reality OpenXR 外掛程式版本資訊

## <a name="100---current-release"></a>1.0.0-目前版本

* 修正了 XRAnchorSubsystem 一律在應用程式啟動時啟動的錯誤（bug），不論 ARAnchorManager 是否存在。
* 修正 reprojection 模式無法正常運作的 bug。

## <a name="100-preview2---2021-06-14"></a>1.0.0-preview。 2-2021-06-14

* 相依于 Unity 的 1.2.2 OpenXR 外掛程式。
* 已將中的全像遠端功能變更為個別的功能群組。
* 修正 [套用 HoloLens 2 專案設定] 變更專案色彩空間的錯誤。 Unity OpenXR 1.2.0 外掛程式之後不再需要此功能。
* 修正了在應用程式暫停和繼續之後，輸入裝置連線而沒有中斷連線的 bug。
* 已新增透過 ARSession 偵測外掛程式和目前追蹤狀態的支援。
* 修正了 [AR Default 平面] ARFoundation 預製專案不會顯示的錯誤。

## <a name="100-preview1---2021-06-02"></a>1.0.0-preview。 1-2021-06-02

* 支援 OpenXR 場景理解 MSFT 擴充功能，而不是預覽延伸模組。
* HoloLens 2 的平面偵測不再需要預覽版本的混合現實 OpenXR 執行時間。

## <a name="095---2021-05-21"></a>0.9.5-2021-05-21

* 相依于 Unity 的 1.2.0 OpenXR 外掛程式
* 適用于 OpenXR 外掛程式 1.2.0) 中的新功能 UI (，以進行設定。
* 已修正找不到已定位相機提供者未正確取消註冊的 bug。
* 清除 [Preserve] 的一些額外用法。
* 更新輸入系統 UI 中的「HP 回音 G2 控制器 (OpenXR) 」名稱。

## <a name="094---2021-05-20"></a>0.9.4-2021-05-20

* 相依于 Unity 的 1.2.0 OpenXR 外掛程式。
* 已新增新的 c # API 來取得運動控制器 glTF 模型。
* 已新增新的 c # API，以取得啟用的視圖設定和設定 reprojection 設定。
* 已新增新的 c # API，以使用 XRMeshSubsystem 來設定計算網格的其他設定。
* 已新增新的 c # API 來設定和訂閱手勢辨識事件。
* 已新增 Windows->XR->編輯器遠端設定] 對話方塊。
* 已新增適用于 HoloLens UWP 應用程式的 ARM 支援。

## <a name="093---2021-04-29"></a>0.9.3-2021-04-29

* 修正了全息型遠端連線不可靠的 bug
* 修正了在升級至 Unity 的 1.1.1 OpenXR 外掛程式之後，VR 轉譯效能是次最佳的錯誤。

## <a name="092---2021-04-21"></a>0.9.2-2021-04-21

* 外掛程式版本0.9.1 中 HoloLens 2 的平面偵測將可搭配105版的 Mixed Reality OpenXR preview 執行時間使用。
* 外掛程式版本0.9.2 中 HoloLens 2 的平面偵測將可搭配106版的 Mixed Reality OpenXR preview 執行時間使用。
* 已從 InputProvider 中移除一些未使用的回呼，以防止像 XRInputSubsystem. * GetTrackingOriginMode (不是由我們的輸入系統管理，) 無法傳回具有誤導值的成功。
* 將已淘汰的 XRAnchorStore 版本分割成自己的檔案，以防止 Unity 主控台出現警告。

## <a name="091---2021-04-20"></a>0.9.1-2021-04-20

* 相依于 Unity 的 1.1.1 OpenXR 外掛程式。
* 新增 UWP 平臺的全像遠端應用程式支援。
* 修正 XRAnchorStore 嘗試在主要執行緒外部取得設定實例的 UnityException。

## <a name="090---2021-03-29"></a>0.9.0-2021-03-29

* 已新增透過 XRMeshSubsystem 和 ARMeshManager 的空間對應支援。
* 已新增新的 c # API 來取得 OpenXR 控制碼，以支援其他 Unity 套件使用 OpenXR 擴充功能。
* 已新增新的 c # API 與 Windows 的互通性。認知 Api 可支援使用認知 WinRT Api 的其他 Unity 套件。
* 從 Windows Mixed Reality 功能集中的必要功能移除互動設定檔，讓開發人員可以選擇所測試的動作控制器。
* 已新增全像「編輯遠端功能」驗證程式，可協助使用者正確設定編輯器的遠端功能。
* 修正當連線失敗後，Unity 編輯器在離開全像 editor 遠端處理模式時損毀的 bug。
* 修正了 unpremultipled Alpha 紋理在 HoloLens 2 上導致次效能的 bug。
* 修正了當場景原點位於地面層級時，無法正確找出手追蹤的錯誤。
* 修正了在離開和載入新場景後，會消失的手上網格追蹤的錯誤。
* 修正了可定位的相機提供者未正確清除的 bug。
* 已將 XRAnchorStore API 的命名空間修改為 MixedReality. OpenXR。