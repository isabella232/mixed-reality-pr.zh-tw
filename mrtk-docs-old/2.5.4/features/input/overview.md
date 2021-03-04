---
title: 輸入概觀
description: MRTK 中的輸入系統總覽
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: ec8ebced1f7faea04e88068612cd642e15fb165f
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/03/2021
ms.locfileid: "101779561"
---
# <a name="input-overview"></a>輸入總覽

MRTK 中的輸入系統可讓您：

- 透過輸入事件，使用各種輸入來源的輸入，例如6個 DOF 控制器、明確表述的手或語音。
- 定義抽象動作，例如 *選取* 或 *功能表*，並將它們關聯至不同的輸入。
- 透過焦點和指標事件連接至控制器的設定指標，以驅動 UI 元件。

<img src="../images/input/MRTK_InputSystem.png" alt="Input System" style="display:block;margin-left:auto;margin-right:auto;">
<sup>MRTK 輸入系統的總覽</sup>

[**輸入資料提供者會 (裝置管理員)**](input-providers.md)產生輸入。 每個提供者都對應至特定的輸入來源： Open VR、Windows Mixed Reality (WMR) 、Unity 搖桿、Windows 語音等等。提供者會透過 *混合現實工具* 組元件中 **已註冊的服務提供者設定檔** 新增至專案，並會在提供對應的輸入來源時自動產生 [**輸入事件**](input-events.md) (例如，偵測到 WMR 控制器或遊戲台連線) 時。

[**輸入動作**](input-actions.md) 是原始輸入的抽象概念，目的是要協助隔離應用程式邏輯與產生輸入的特定輸入來源。 例如，它可能很有用，例如，定義 *選取* 動作並將它對應至滑鼠左鍵、遊戲台中的按鈕，以及6個 DOF 控制器中的觸發程式。 然後，您可以讓應用程式邏輯接聽 *選取* 的輸入動作事件，而不需要知道可以產生的所有不同輸入。 輸入動作會定義在 **輸入動作設定檔** 中，可在 *混合現實工具* 組元件的 *輸入系統設定檔* 中找到。

當偵測到輸入裝置時，以及當輸入裝置遺失或中斷連線時，這些 [**控制器**](controllers.md)會由 *輸入提供者* 建立。 例如，WMR 輸入提供者將會為 6 DOF 裝置建立 *WMR 控制器* ，並針對有向的 *手勢建立 WMR* 的明確控制器。 您可以透過 **控制器對應設定檔**，在 *輸入系統設定檔* 中，將控制器輸入對應至輸入動作。 控制器所引發的輸入事件會包含相關聯的輸入動作（如果有的話）。

控制器可以將 [**指標**](pointers.md) 附加至它們，以查詢場景來判斷具有焦點的遊戲物件，並在其上引發 [**指標事件**](pointers.md#pointer-event-interfaces) 。 例如，我們的 *線指標* 會使用控制器姿勢來計算光線的原點和方向，對場景執行 raycast。 在 **指標設定檔** 的 *輸入系統設定檔* 下，會設定為每個控制器建立的指標。

<img src="../images/input/MRTK_Input_EventFlow.png" width="200px" alt="Event Flow" style="display:block;margin-left:auto;margin-right:auto;">
<sup>事件流程。</sup>

雖然您可以 [直接在 UI 元件中處理輸入事件](input-events.md)，但建議使用 [指標事件](pointers.md#pointer-event-interfaces) 來讓執行裝置保持獨立。

MRTK 也提供數種便利的方法，可讓您直接以與裝置無關的方式查詢輸入狀態。 See [Accessing input state in MRTK](input-state.md) for more details.
