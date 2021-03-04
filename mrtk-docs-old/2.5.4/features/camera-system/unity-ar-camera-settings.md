---
title: UnityArCameraSettings
description: 在 MRTK 中使用 AR 攝影機的檔
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、AR 攝影機、
ms.openlocfilehash: 40770bb4d5eb466ee3698dfffb7a89b964a9938d
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/03/2021
ms.locfileid: "101779692"
---
# <a name="unity-ar-camera-settings-provider"></a>Unity AR 相機設定提供者

Unity AR 攝影機設定提供者是實驗性的 MRTK 元件，可讓 mixed reality 應用程式在 Android 和 iOS 裝置上執行。

## <a name="unity-ar-camera-settings-provider-options"></a>Unity AR 相機設定提供者選項

![Unity AR 相機設定設定](../images/camera-system/UnityArSettingsConfiguration.png)

如需如何將提供者新增至場景的指南： [如何設定 iOS 和 Android 的 MRTK](../cross-platform/using-ar-foundation.md)

### <a name="tracking-settings"></a>追蹤設定

Unity AR 攝影機設定提供者可以設定如何執行追蹤的設定選項。 這些設定僅適用于 Unity AR 攝影機設定提供者的執行。

**姿勢來源**

姿勢來源定義了可用的擴充現實追蹤的可用類型。 一般而言，這些值會對應至執行應用程式之裝置的元件。

下表說明可用的選項。

| 選項 | 描述 |
| --- | --- |
| Center | 前端掛接裝置的中心眼睛。 |
| 彩色相機 | 行動裝置的色彩相機。 |
| Head | 前端掛接裝置的前端，通常會稍微高於中心眼睛。 |
| 左方眼睛 | 前端掛載裝置的最左邊。 |
| 左方姿勢 | 左邊控制器會造成。 |
| 適當留意 | 前端掛接裝置的正確眼睛。 |
| 靠右姿勢 | 右手邊控制器會造成。 |

姿勢來源的預設值是 [ **彩色攝影機**]，可在行動裝置上啟用透明顯示，例如手機或平板電腦。

**追蹤類型**

追蹤類型會定義將用於追蹤的姿勢 () 部分。

下表說明可用的選項。

| 選項 | 描述 |
| --- | --- |
| 位置 | 裝置的位置。 |
| 旋轉 | 裝置的旋轉。 |
| 旋轉和位置 | 裝置的位置和旋轉。 |

追蹤類型的預設值為 [ **旋轉] 和 [位置**]，以啟用最豐富的追蹤體驗。

**更新類型**

更新類型會定義在框架處理期間，將會取樣資料的位置。

下表說明可用的選項。

| 選項 | 描述 |
| --- | --- |
| 轉譯前 | 緊接在轉譯之前。 |
| 更新 | 在框架的更新階段。 |
| 更新和在轉譯之前 | 在更新階段和轉譯之前。 |

追蹤類型的預設值是 **Update 和轉譯之前** 的值，可啟用最低的追蹤延遲。

## <a name="see-also"></a>另請參閱

- [攝影機系統總覽](camera-system-overview.md)
- [建立相機設定提供者](create-settings-provider.md)
