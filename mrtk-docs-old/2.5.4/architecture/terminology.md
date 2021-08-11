---
title: 詞彙
description: MRTK 中的不同輸入系統。
author: cDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、輸入、
ms.openlocfilehash: e13dd23b33690039839ad66d8b0e3235a7238fc6118927dbce51065e01aae3ee
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2021
ms.locfileid: "115201820"
---
# <a name="input-system"></a>輸入系統

輸入系統是 MRTK 所提供的所有功能的其中一個最大系統。
工具組內的許多專案都是以 it 為基礎 (指標、焦點、prefabs) 。 輸入系統內的程式碼可讓您進行自然互動，例如跨平臺抓取和旋轉。

輸入系統有一些值得定義的術語：

- **資料提供者**

    輸入設定檔中的輸入設定會參考稱為資料提供者的實體，另一個描述這些專案的單字是裝置管理員。 這些元件的工作是藉由與特定基礎系統互動來擴充 MRTK 輸入系統。 提供者的範例是 Windows Mixed Reality 的提供者，它的工作是要與基礎 Windows Mixed Reality api 溝通，然後將這些 api 的資料轉譯為下面的 MRTK 特定輸入概念。 另一個範例是 OpenVR 提供者 (其作業是與 Unity 抽象版本的 OpenVR Api 溝通，然後將該資料轉譯成 MRTK 輸入概念) 。

- **控制器**

    實體控制器的標記法 (是否為6度自由度的控制器、具有手勢支援的 HoloLens 1 樣式的手、完全有向的手勢、閏運動控制器等 ) 。 控制器是由裝置管理員所產生 (亦即，WMR 裝置管理員會產生一個控制器，並在看到有明確的手) 時管理其存留期。

- **指標**

    控制器會使用指標來與遊戲物件互動。 例如，近距離互動指標負責偵測 (是控制器) 接近的物件，這些物件會將本身公告為支援「接近互動」。 指標的其他範例是遙傳或遠指標 (也就是使用最多 raycasts 的 shell 手光線指標) ，與使用者的距離長度相比，可使用的內容遠超過手臂長度。

    指標是由裝置管理員所建立，然後附加至輸入來源。 若要取得控制器的所有指標，請執行： `controller.InputSource.Pointers`

    請注意，控制器可以同時與許多不同的指標相關聯。 為了確保這不會 devolve 混亂，有一個指標中繼程式可控制哪些指標可供使用 (例如，當偵測到接近互動時，中繼程式將會停用目前的互動指標) 。

- **焦點**

    指標事件會傳送至 **焦點** 的物件。 焦點選取專案將依指標類型而有所不同;手光線指標會使用 raycasts，而指標會使用 spherecasts。 物件必須執行 IMixedRealityFocusHandler 以取得焦點。 您可以全域註冊物件以接收未篩選的指標事件，但不建議使用此方法。

    用來更新物件焦點的元件是 [FocusProvider](xref:Microsoft.MixedReality.Toolkit.Input.FocusProvider)

- **資料指標**

    與指標相關聯的實體，可針對指標互動提供額外的視覺提示。 例如，FingerCursor 會在您的手指周圍呈現環形，而當手指接近「近端互動」物件時，可能會旋轉該環形。 指標可以一次與單一資料指標產生關聯。

- **互動和操作**

    物件可以使用互動或操作腳本來標記。 這可能是 [`Interactable`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) 透過或類似的方式 [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) / [`ManipulationHandler`](xref:Microsoft.MixedReality.Toolkit.UI.ManipulationHandler) 。

    例如，NearInteractionGrabbable 和 NearInteractionTouchable 允許某些指標 (特別是近距離的互動指標) 知道哪些物件可專注于。

    互動和 ManipulationHandler 是接聽指標事件以修改 UI 視覺效果或移動/調整/旋轉遊戲物件的元件範例。

下圖從 MRTK 輸入堆疊的下) 中，將概要組建 (：

![輸入系統圖表](../features/images/input/MRTK_InputSystem.png)
