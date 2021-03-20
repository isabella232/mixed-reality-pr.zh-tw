---
title: InputEvents
description: MRTK 中的 InputEvents 檔
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、事件、
ms.openlocfilehash: 4b75d80d4c212fde13335761339452965be83058
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104687228"
---
# <a name="input-events"></a>輸入事件

下列清單概述自訂 MonoBehaviour 元件所要執行的所有可用輸入事件介面。 MRTK 輸入系統會呼叫這些介面，以根據使用者輸入互動來處理自訂應用程式邏輯。 [指標輸入事件](pointers.md#pointer-event-interfaces) 的處理方式稍有不同，如下所示：標準輸入事件種類。

> [!IMPORTANT]
> 根據預設，腳本只會在焦點為 GameObject 的指標或父系時，才會收到輸入事件。

| 處理常式 | 事件 | 描述 |
| --- | :---: | --- |
| [`IMixedRealitySourceStateHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySourceStateHandler) | 偵測到來源/遺失 | 當偵測到輸入來源時引發/遺失，例如，偵測到有向的手勢或遺失追蹤時。 |
| [`IMixedRealitySourcePoseHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySourcePoseHandler) | 來源姿勢變更 | 在來源姿勢變更時引發。 來源姿勢代表輸入來源的一般姿勢。 您可以透過取得特定的姿勢，例如在六個 DOF 控制器中的把手或指標姿勢 `IMixedRealityInputHandler<MixedRealityPose>` 。 |
| [`IMixedRealityInputHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler) | 輸入向下/向上鍵 | 在對二進位輸入（例如按鈕）的變更時引發。 |
| [`IMixedRealityInputHandler<T>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1) | 輸入已變更 | 在對指定類型的輸入變更時引發。 **T** 可以採用下列值： <br/> - *float* (例如傳回類比觸發程式) <br/> - *Vector2* (例如會傳回游戲杆杆方向)  <br/> - *Vector3* (例如追蹤裝置的傳回位置)  <br/> - *四元數* (例如會傳回追蹤裝置的方向) <br/> - [MixedRealityPose](xref:Microsoft.MixedReality.Toolkit.Utilities.MixedRealityPose) (例如會傳回完整追蹤的裝置)  |
| [`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) | 語音關鍵字已辨認 | 在識別 *語音命令設定檔* 中所設定的其中一個關鍵字時引發。 |
| [`IMixedRealityDictationHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityDictationHandler) | 聽寫<br/> 假設 <br/> 結果 <br/> 完成 <br/> 錯誤 | 由聽寫系統引發，以報告聽寫會話的結果。 |
| [`IMixedRealityGestureHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler) | 手勢事件： <br/> 已開始 <br/> 已更新 <br/> 已完成 <br/> 已取消 | 在筆勢偵測時引發。 |
| [`IMixedRealityGestureHandler<T>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler`1) | 已更新/完成手勢 | 在偵測包含指定類型之其他資料的手勢時引發。 如需 **T** 可能值的詳細資訊，請參閱 [**手勢事件**](Gestures.md#gesture-events)。 |
| [`IMixedRealityHandJointHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHandJointHandler) | 手動接點已更新 | 當手動接點更新時，透過明確的手控制器來引發。 |
| [`IMixedRealityHandMeshHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHandMeshHandler) | 已更新手形網格 | 在更新手勢時，透過明確的手勢控制器來引發。 |
| [`IMixedRealityInputActionHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputActionHandler) | 動作已開始/結束 | 引發以表示對應至動作之輸入的動作開始和結束。 |

## <a name="input-events-in-action"></a>作用中的輸入事件

在腳本層級，您可以藉由執行上表中所示的其中一個事件處理常式介面來取用輸入事件。 透過使用者互動引發輸入事件時，會發生下列情況：

1. MRTK 輸入系統會辨識出輸入事件已發生。
1. MRTK 輸入系統會將輸入事件的相關介面函式引發至所有 [已註冊的全域輸入處理常式](#register-for-global-input-events)
1. 針對在輸入系統中註冊的每個作用中指標：
    1. 輸入系統會決定要將焦點放在目前指標的 GameObject。
    1. 輸入系統會利用 [Unity 的事件系統](https://docs.unity3d.com/Manual/EventSystem.html) 來引發焦點 GameObject 上所有相符元件的相關介面函式。
    1. 如果您在任何時間點輸入事件已 [標示為已使用](#how-to-stop-input-events)，進程將會結束，且不會有進一步的 gameobject 接收回呼。
        - 範例：辨識出語音命令時，將會搜尋執行介面的元件 [`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) 。
        - 注意：如果在目前的 GameObject 上找不到符合所需介面的元件，Unity 事件系統將會反升搜尋父 GameObject。
1. 如果未註冊任何全域輸入處理常式，且找不到具有相符元件/介面的 GameObject，則輸入系統會呼叫每個已註冊的回溯輸入處理常式

> [!NOTE]
> [指標輸入事件](pointers.md#pointer-event-interfaces) 的處理方式與上面所列的輸入事件介面稍有不同。 尤其是，指標輸入事件只會由引發輸入事件的指標，以及任何全域輸入處理常式所專注的 GameObject 來處理。 一般輸入事件是由所有使用中指標的焦點 Gameobject 來處理。

### <a name="input-event-interface-example"></a>輸入事件介面範例

下列程式碼示範如何使用 [`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) 介面。 當使用者在將焦點放在具有這個類別的 GameObject 時，說出「較小」或「更大」的單字時 `ShowHideSpeechHandler` ，GameObject 將會以一半或兩倍的方式來調整其大小。

```c#
public class ShowHideSpeechHandler : MonoBehaviour, IMixedRealitySpeechHandler
{
    ...

    void IMixedRealitySpeechHandler.OnSpeechKeywordRecognized(SpeechEventData eventData)
    {
        if (eventData.Command.Keyword == "smaller")
        {
            transform.localScale *= 0.5f;
        }
        else if (eventData.Command.Keyword == "bigger")
        {
            transform.localScale *= 2.0f;
        }
    }
}
```

> [!NOTE]
> [`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) 輸入事件需要在 [MRTK Speech 命令設定檔](Speech.md)中預先註冊所需的關鍵字。

## <a name="register-for-global-input-events"></a>註冊全域輸入事件

若要建立可接聽全域輸入事件的元件，並忽略 GameObject 可能的焦點，元件必須向輸入系統註冊本身。 註冊之後，此 MonoBehaviour 的任何實例都會收到輸入事件，以及任何 GameObject () 目前為焦點和其他全域註冊的接聽程式。

如果輸入事件已 [標示為已使用](#how-to-stop-input-events)，則全域註冊的處理常式仍會接收回呼。 不過，沒有任何焦點的 Gameobject 會收到此事件。

### <a name="global-input-registration-example"></a>全域輸入註冊範例

```c#
public class GlobalHandListenerExample : MonoBehaviour,
    IMixedRealitySourceStateHandler, // Handle source detected and lost
    IMixedRealityHandJointHandler // handle joint position updates for hands
{
    private void OnEnable()
    {
        // Instruct Input System that we would like to receive all input events of type
        // IMixedRealitySourceStateHandler and IMixedRealityHandJointHandler
        CoreServices.InputSystem?.RegisterHandler<IMixedRealitySourceStateHandler>(this);
        CoreServices.InputSystem?.RegisterHandler<IMixedRealityHandJointHandler>(this);
    }

    private void OnDisable()
    {
        // This component is being destroyed
        // Instruct the Input System to disregard us for input event handling
        CoreServices.InputSystem?.UnregisterHandler<IMixedRealitySourceStateHandler>(this);
        CoreServices.InputSystem?.UnregisterHandler<IMixedRealityHandJointHandler>(this);
    }

    // IMixedRealitySourceStateHandler interface
    public void OnSourceDetected(SourceStateEventData eventData)
    {
        var hand = eventData.Controller as IMixedRealityHand;

        // Only react to articulated hand input sources
        if (hand != null)
        {
            Debug.Log("Source detected: " + hand.ControllerHandedness);
        }
    }

    public void OnSourceLost(SourceStateEventData eventData)
    {
        var hand = eventData.Controller as IMixedRealityHand;

        // Only react to articulated hand input sources
        if (hand != null)
        {
            Debug.Log("Source lost: " + hand.ControllerHandedness);
        }
    }

    public void OnHandJointsUpdated(
                InputEventData<IDictionary<TrackedHandJoint, MixedRealityPose>> eventData)
    {
        MixedRealityPose palmPose;
        if (eventData.InputData.TryGetValue(TrackedHandJoint.Palm, out palmPose))
        {
            Debug.Log("Hand Joint Palm Updated: " + palmPose.Position);
        }
    }
}
```

## <a name="register-for-fallback-input-events"></a>註冊 fallback 輸入事件

回溯輸入處理常式類似于已註冊的全域輸入處理常式，但會被視為輸入事件處理的最後手段。 只有在找不到任何全域輸入處理常式，且焦點沒有任何 Gameobject 時，才會利用回溯輸入處理常式。

### <a name="fallback-input-handler-example"></a>Fallback 輸入處理常式範例

```c#
public class GlobalHandListenerExample : MonoBehaviour,
    IMixedRealitySourceStateHandler // Handle source detected and lost
{
    private void OnEnable()
    {
        CoreServices.InputSystem?.PushFallbackInputHandler(this);
    }

    private void OnDisable()
    {
        CoreServices.InputSystem?.PopFallbackInputHandler();
    }

    // IMixedRealitySourceStateHandler interface
    public void OnSourceDetected(SourceStateEventData eventData)
    {
        ...
    }

    public void OnSourceLost(SourceStateEventData eventData)
    {
        ...
    }
}
```

## <a name="how-to-stop-input-events"></a>如何停止輸入事件

每個輸入事件介面都會提供一個 [`BaseInputEventData`](xref:Microsoft.MixedReality.Toolkit.Input.BaseInputEventData) 資料物件做為介面上每個函數的參數。 此事件資料物件會從 Unity 本身擴充 [`AbstractEventData`](https://docs.unity3d.com/2019.1/Documentation/ScriptReference/EventSystems.AbstractEventData.html) 。

若要停止輸入事件，使其無法 [依照所述](#input-events-in-action)的執行傳播，元件可以呼叫， [`AbstractEventData.Use()`](https://docs.unity3d.com/2019.1/Documentation/ScriptReference/EventSystems.AbstractEventData.Use.html) 以將事件標示為已使用。 這會停止任何其他 Gameobject 接收目前的輸入事件，但全域輸入處理常式除外。

> [!NOTE]
> 呼叫方法的元件 `Use()` 會阻止其他 gameobject 接收它。 不過，目前 GameObject 上的其他元件仍會收到輸入事件，並引發任何相關的介面函數。

## <a name="see-also"></a>另請參閱

- [指標](Pointers.md)
- [語音](Speech.md)
- [輸入狀態](InputState.md)
