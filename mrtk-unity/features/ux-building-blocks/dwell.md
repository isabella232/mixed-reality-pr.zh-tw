---
title: 住
description: 停留互動
author: cre8ivepark
ms.author: dongpark
ms.date: 05/20/2021
keywords: 停留、Unity、HoloLens、HoloLens 2、混合現實、開發、MRTK
monikerRange: '>= mrtkunity-2021-05'
ms.openlocfilehash: 8ac63ee723cdd524ee7abbad7fd2658b446156adbd5ddee06ae1795edb3b68d1
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2021
ms.locfileid: "115226898"
---
# <a name="dwell"></a>住

![停留主圖](../images/dwell/MRTK_UX_Dwell.png)

當人的手中有其他工作忙碌的情況下，前端和停留很好用。 當語音不是100% 可靠或因為環境或社交條件約束而無法使用時，此功能也很有用。
MRTK 的停留範例會示範不同類型的 UI 元件，並提供可設定的回應時間和視覺效果的意見反應。

請參閱 [前端和停留指導](/windows/mixed-reality/design/gaze-and-dwell-head) 方針頁面，以取得設計建議。

## <a name="dwell-scripts"></a>停留腳本

- **DwellHandler**：將停留樣式新增至 UI 目標。
- **DwellStateType**：停留處理常式的狀態。
- **DwellUnityEvent**：停留事件的 Unity 事件。 包含指標參考。
- **BaseDwellPressableButton** ：在 PressableButtonHoloLens2 prefabs 中觸發 OnClick () 事件的腳本。 `Interactable`
- **ToggleDwellPressableButton** ：此腳本 `_BorderWidth` `dwellVisualImage` 會修改使用 MRTK 標準著色器之的屬性。

## <a name="dwell-profiles"></a>停留設定檔
停留 **處理常式** 會使用停留設定檔來設定各種閾值。
- **ButtonDwellProfile 資產**
- **InstandDwellProfile 資產**
- **DwellProfileWithDecay 資產**

## <a name="prefabs"></a>Prefabs

這些 prefabs 是 HoloLens 2 style pressable 按鈕 prefabs 的變體，具有可支援停留互動的額外元件。

- **PressableButtonHoloLens2_Dwell. 預製專案**
- **PressableButtonHoloLens2_32x96_Dwell. 預製專案**
- **PressableButtonHoloLens2ToggleDwell. 預製專案**
- **PressableButtonHoloLens2Toggle_32x96_Dwell. 預製專案**

這些 prefabs 有額外的 backplate 元件 **QuadDwellVisual** 可將停留輸入狀態視覺化。 它已指派 **HolographicBackPlateDwellVisual** 的材質。 **ToggleDwellPressableButton** 會更新 MRTK 標準著色器的 **_BorderWidth** 屬性，以視覺化停留輸入。

<img src="../images/dwell/MRTK_UX_Dwell_Prefabs_Structure.png" alt="Dwell prefabs structure" width="550px">
<img src="../images/dwell/MRTK_UX_Dwell_Prefabs.png" alt="Dwell prefabs" width="350px">

## <a name="example-scene"></a>範例場景

您可以在場景中找到範例 `DwellExample` 。 範例場景會顯示體積型 UI 範例和 Unity UI 範例。

<img src="../images/dwell/MRTK_UX_Dwell_Examples.png" alt="Near Menu Example">

## <a name="see-also"></a>另請參閱

- [**按鈕**](button.md)
- [**互動**](interactable.md)
