---
title: CoreSystem
description: MRTK 中的輸入系統、裝置管理員和資料提供者
author: cDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、事件
ms.openlocfilehash: 174945c8d9edbe1ae8c612f75636a426f08dfb16
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/03/2021
ms.locfileid: "101780241"
---
# <a name="core-system"></a>核心系統

輸入系統的核心是 [InputSystem](../../features/Input/Overview.md)，也就是負責初始化和操作所有與 MRTK 相關聯之輸入相關功能的服務。

> [!NOTE]
> 假設讀者已經讀過，並對 [術語](Terminology.md) 區段有基本的瞭解。

此服務負責：

- 讀取 [輸入系統設定檔](../../out-of-scope/MixedRealityConfigurationGuide.md#input-system-settings)
- 例如，啟動已設定的 [資料提供者](../../features/Input/InputProviders.md) (， `Windows Mixed Reality Device Manager` 並 `OpenVR Device Manager`) 。
- [GazeProvider](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGazeProvider)的具現化，它是一種元件，負責提供 hololens (第一代) 樣式的列印頭資訊，以及 hololens 2 樣式的眼睛資訊。
- [FocusProvider](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityFocusProvider)的具現化，這是負責判斷具有焦點之物件的元件。 這在檔的 [ [指標和焦點](ControllersPointersAndFocus.md#pointers-and-focus) ] 區段中有更深入的說明。
- 將所有輸入事件的登錄點提供給 ([全域](#global-listeners) 接聽程式) 。
- 提供這些輸入事件的事件分派功能。

## <a name="input-events"></a>輸入事件

輸入事件通常會在兩個不同的通道上引發：

### <a name="objects-in-focus"></a>焦點物件

事件可以直接傳送至具有焦點的 GameObject。 例如，物件可能具有可執行檔腳本 [`IMixedRealityTouchHandler`](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Assets/MixedRealityToolkit/Interfaces/InputSystem/Handlers/IMixedRealityHandTrackHandler.cs) 。
這個物件會在焦點在其附近的手邊時取得觸控事件。 這些事件種類會「up」 GameObject 階層，直到找到能夠處理事件的 GameObject 為止。

這是透過從預設的輸入系統執行中使用 [ExecuteHierarchy](https://docs.unity3d.com/ScriptReference/EventSystems.ExecuteEvents.ExecuteHierarchy.html) 來完成。

### <a name="global-listeners"></a>全域接聽程式

事件可以傳送給全域接聽程式。 您可以使用輸入系統的介面來註冊所有輸入事件 [`IMixedRealityEventSystem`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityEventSystem) 。 建議使用 [RegisterHandler](xref:Microsoft.MixedReality.Toolkit.IMixedRealityEventSystem.RegisterHandler``1(IEventSystemHandler)) 方法來註冊全域事件-已被取代的函式會導致接聽程式收到 `Register` 所有輸入事件的通知，而不只是特定類型的輸入事件，而是由事件介面) 所定義的型別 (。

請注意 [，「](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityInputSystem.PushFallbackInputHandler(GameObject)) 回溯接聽程式」是另一種全域接聽程式，也不建議這樣做，因為它們會接收未在場景中的其他地方處理的每個單一輸入事件。

### <a name="order-of-event-dispatch"></a>事件分派的順序

一般情況下，事件會以下列方式傳送至接聽程式。 請注意，如果下列任何步驟將事件標示為已 [處理](https://docs.unity3d.com/ScriptReference/EventSystems.AbstractEventData-used.html)，事件分派進程就會停止。

1. 事件會傳送至全域接聽程式。
2. 事件會傳送至焦點物件的強制回應對話方塊。
3. 事件會傳送至焦點物件。
4. 事件會傳送至回溯接聽項。

## <a name="device-managers-and-data-providers"></a>裝置管理員和資料提供者

這些實體負責與較低層級的 (Api （例如 Windows Mixed Reality Api）進行互動，或 OpenVR Api) ，並將這些系統中的資料轉譯成符合 MRTK 較高層級輸入抽象的資料。 它們負責偵測、建立和管理 [控制器](ControllersPointersAndFocus.md#controllers)的存留期。

裝置管理員的基本流程包括：

1. 裝置管理員由輸入系統服務具現化。
2. 裝置管理員會向其基礎系統註冊 (例如，Windows Mixed Reality 裝置管理員會註冊 [輸入](../../features/Input/InputEvents.md) 和 [手勢](../../features/Input/Gestures.md#gesture-events) 事件。
3. 它會建立它從基礎系統中探索的控制器 (例如，提供者可以偵測出有明確的手) 
4. 在其更新 () 迴圈中，呼叫 UpdateController () 輪詢基礎系統的新狀態，並更新其控制器標記法。
