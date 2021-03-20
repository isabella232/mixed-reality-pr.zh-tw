---
title: 在 Unreal 中升級專案
description: 隨時掌握 Unreal 專案的版本升級步驟、API 變更和淘汰項目。
author: hferrone
ms.author: jacksonf
ms.date: 11/23/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 混合實境, 開發, 文件, 指南, 功能, 混合實境頭戴式裝置, windows 混合實境頭戴式裝置, 虛擬實境頭戴式裝置, 移植, 升級
ms.openlocfilehash: 27fb726bc0ca9c51b4e7b68ad28b76f89312262e
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "98010048"
---
# <a name="upgrading-projects-in-unreal"></a>在 Unreal 中升級專案

更新至新版本的 Unreal 時，已淘汰的函式會在編譯藍圖或封裝專案時顯示為警告。  新增了應改用的新函式時，舊函式就會淘汰。 

## <a name="426-upgrades"></a>4.26 升級
 
在 4.26 中，所有 AR 和 VR 平台都已重構，以新增通用介面，並讓應用程式的程式碼平台不受限制，因此您可能會看到比平常更多的警告。  建議您更新為新的 API，以讓專案更容易移植到其他平台。

警告訊息會顯示哪個函式已淘汰，並指出要改用哪個函式。  所有已淘汰的函式在此版本中仍可繼續運作，但在未來的版本中可能就無法運作。  在藍圖中搜尋函式時，也不會再列出已淘汰的函式。

![建立具名 ARPin 函式的藍圖](images/unreal-porting-img-01.png)

### <a name="425-deprecations"></a>4.25 淘汰

| 已淘汰的函式 | 新增函式 |
| --- | --- |
| CreateNamedARPin | ![「釘選元件」函式的藍圖](images/unreal-porting-img-02.png) |
| LoadWMRAnchorStoreARPins | ![「從本機存放區載入 ARPins」函式的藍圖](images/unreal-porting-img-03.png) |
| LoadWMRAnchorSaveARPinToWMRAnchorStoreStoreARPins | ![「將 ARPin 儲存至本機存放區」函式的藍圖](images/unreal-porting-img-04.png) |
| RemoveARPinFromWMRAnchorStore | ![「從本機存放區移除 ARPin」函式的藍圖](images/unreal-porting-img-05.png) |
| SetEnabledMixedRealityCamera | ![「設定已啟用的 XRCamera」函式的藍圖](images/unreal-porting-img-06.png) |
| ResizeMixedRealityCamera | ![「調整 XRCamera 大小」函式的藍圖](images/unreal-porting-img-07.png) |
| StartCameraCapture | ![用於啟動相機擷取的「切換 ARCapture」函式藍圖](images/unreal-porting-img-08.png) |
| StopCameraCapture | ![用於停止相機擷取的「切換 ARCapture」函式藍圖](images/unreal-porting-img-09.png) |
| StartQRCodeCapture | ![用於啟動 QR 代碼擷取的「切換 ARCapture」函式藍圖](images/unreal-porting-img-10.png) |
| StopQRCodeCapture | ![用於停止 QR 代碼擷取的「切換 ARCapture」函式藍圖](images/unreal-porting-img-11.png) |
| 以前在 4.25 中，空間對應會自動啟動，但現在在 4.26 中，則必須進行切換。 | ![用於啟用空間對應的「切換 ARCapture」函式藍圖](images/unreal-porting-img-12.png) |
| ShowKeyboard | 已在 4.26 中移除，因為當焦點放在文字小工具時，會自動顯示鍵盤。 |
| HideKeyboard | 已在 4.26 中移除，因為當焦點不在文字小工具時，會自動隱藏鍵盤。 |
| SupportsHandTracking | ![「支援手部追蹤」屬性的藍圖](images/unreal-porting-img-13.png) |
| IsDisplayOpaque | ![IsDisplayOpaque 屬性的藍圖](images/unreal-porting-img-14.png) |
| GetHandJointTransform、GetPointerPoseInfo、GetControllerTrackingStatus | ![「取得運動控制器資料」函式的藍圖](images/unreal-porting-img-15.png) |
| GetVersionString | ![「取得版本字串」函式的藍圖](images/unreal-porting-img-16.png) |
| IsTrackingAvailable | ![IsTrackingAvailable 屬性的藍圖](images/unreal-porting-img-17.png) |
| IsButtonClicked、IsButtonDown、IsGrasped、IsSelectPressed | 使用 Unreal 的輸入動作系統。 |
| SetFocusPointForFrame | 已在 4.26 中移除。  過去用於遠端處理時的重新投影，現在則支援深度重新投影。 |

## <a name="426-changes"></a>4.26 變更

重大變更為必須設定 [編輯] > [專案設定] > [專案] > [描述] > [設定] 中的 [在 VR 中啟動]，才能啟動 Windows Mixed Reality 外掛程式。 若沒有該參數，您就不會在裝置上看到全像投影。
