---
title: HowToAddNearInteractivity
description: MRTK 近乎互動的相關檔
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、近乎互動、
ms.openlocfilehash: 0a936dae3500d94aaecbaf2f460f30169e4cb264
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/03/2021
ms.locfileid: "101779902"
---
# <a name="how-to-add-near-interaction-in-mrtk"></a>如何在 MRTK 中新增近乎互動

近距離互動的形式為觸控和抓取。 觸控和抓取事件會分別由 [PokePointer](pointers.md#pokepointer) 和 [SpherePointer](pointers.md#spherepointer)以指標事件的形式引發。

在特定 GameObject 上接聽觸控和/或抓取輸入事件需要三個主要步驟。

1. 確定已在主要 [MRTK 設定檔](../../configuration/mixed-reality-configuration-guide.md)中註冊相關的指標。
1. 確定所需的 GameObject 具有適當的 [抓取](#add-grab-interactions) 或 [觸控](#add-touch-interactions) 腳本元件和 [`Unity Collider`](https://docs.unity3d.com/ScriptReference/Collider.html) 。
1. 在附加的腳本上，將輸入處理常式介面實作為所需的 GameObject，以接聽 [抓取](#grab-code-example) 或 [觸控](#touch-code-example) 事件。

## <a name="add-grab-interactions"></a>新增抓取互動

1. 確定已在 *MRTK 指標設定檔* 中註冊 [SpherePointer](pointers.md#spherepointer) 。

    預設 MRTK 設定檔和預設的 HoloLens 2 設定檔已包含 *SpherePointer*。 您可以藉由選取 MRTK 設定檔並流覽至 **輸入**  >  **指標**  >  **指標選項**，來確認將會建立 SpherePointer。 預設的 `GrabPointer` 預製專案 (資產/MRTK/SDK/功能/UX/Prefabs/指標) 應以有向的 *控制器類型* 來列出。 只要自訂預製專案實作為類別，就可以使用它 [`SpherePointer`](xref:Microsoft.MixedReality.Toolkit.Input.SpherePointer) 。

    ![抓取指標設定檔範例](../images/input/Pointers/GrabPointer_MRTKProfile.png)

    預設抓取指標會查詢位於抓取點周圍的附近物件，以符合預設的 Hololens 2 介面。

    ![圓錐抓取指標](https://user-images.githubusercontent.com/39840334/82500569-72d58300-9aa8-11ea-8102-ec9a62832d4e.png)

1. 在應該 grabbable 的 GameObject 上，加入，以及 [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) 碰撞。

    請確定 GameObject 的圖層位於 grabbable 層。 依預設，所有圖層（ *空間感知* 和 *忽略 Raycasts* ）都會 grabbable。 檢查您 *GrabPointer* 預製專案中的 *抓取圖層遮罩*，以查看 grabbable 的圖層。

1. 在 GameObject 或其中一個祖系上，加入可執行介面的腳本元件 [`IMixedRealityPointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointerHandler) 。 具有的物件的任何上階 [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) 也都可以接收指標事件。

### <a name="grab-code-example"></a>抓取程式碼範例

以下是當事件為觸控或抓取時，將會列印的腳本。 在相關的 *IMixedRealityPointerHandler* 介面函式中，您可以查看透過觸發該事件的指標類型 [`MixedRealityPointerEventData`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityPointerEventData) 。 如果指標是 *SpherePointer*，則互動是一種抓取。

```c#
public class PrintPointerEvents : MonoBehaviour, IMixedRealityPointerHandler
{
    public void OnPointerDown(MixedRealityPointerEventData eventData)
    {
        if (eventData.Pointer is SpherePointer)
        {
            Debug.Log($"Grab start from {eventData.Pointer.PointerName}");
        }
        if (eventData.Pointer is PokePointer)
        {
            Debug.Log($"Touch start from {eventData.Pointer.PointerName}");
        }
    }

    public void OnPointerClicked(MixedRealityPointerEventData eventData) {}
    public void OnPointerDragged(MixedRealityPointerEventData eventData) {}
    public void OnPointerUp(MixedRealityPointerEventData eventData) {}
}
```

## <a name="add-touch-interactions"></a>新增觸控互動

在 UnityUI 元素上新增觸控互動的程式，與香草 3D Gameobject 的程式不同。 您可以跳到下一節（ *UNITY ui*）來啟用 unity ui 元件。

不過，對於 **這兩種** 類型的 UX 元素，請確定已在 *MRTK 指標設定檔* 中註冊 [PokePointer](pointers.md#pokepointer) 。

預設 MRTK 設定檔和預設的 HoloLens 2 設定檔已包含 *PokePointer*。 您可以藉由選取 MRTK 設定檔並流覽至 **輸入**  >  **指標**  >  **指標選項**，來確認將會建立 PokePointer。 預設的 `PokePointer` (資產/MRTK/SDK/Features/UX/Prefabs/指標) 預製專案應該會列出，且 *控制器類型* 為有向的 *手*。 只要自訂預製專案實作為類別，就可以使用它 [`PokePointer`](xref:Microsoft.MixedReality.Toolkit.Input.PokePointer) 。

![移動指標設定檔範例](../images/input/Pointers/PokePointer_MRTKProfile.png)

### <a name="3d-gameobjects"></a>3D Gameobject

有兩種不同的方式可將觸控互動新增至 3D Gameobject，取決於您的3d 物件是否應該只有單一可觸式平面，或是否應該根據其整個碰撞項加以可觸式。
第一種方式通常是在具有 BoxColliders 的物件上，而只想要讓碰撞器回應觸控事件的單一臉部。 另一個則適用于需要根據其碰撞器從任何方向可觸式的物件。

### <a name="single-face-touch"></a>單一臉部觸控

這對於啟用只需要可觸式單一臉部的情況很有用。 此選項假設遊戲物件有 BoxCollider。 您可以使用此功能搭配非 BoxCollider 物件，在此情況下，會以手動方式將 ' 界限 ' 和 ' Local Center ' 屬性設定為設定可觸式平面 (也就是，界限應該設定為非零零值) 。

1. 在應該可觸式的 GameObject 上，新增 BoxCollider 和 [ `NearInteractionTouchable` ] (x：： MixedReality) 元件。

    1. 如果您在下方的元件腳本中使用 [] (x： IMixedRealityTouchHandler) 介面，請設定 **要接收***觸控* 的事件 `IMixedRealityTouchHandler` 。

    1. 按一下 [**修正界限** 和 **修正中心**]

    ![NearInteractionTouchable 設定](../images/input/Pointers/NearInteractionTouchableSetup.gif)

1. 在該物件或其中一個祖系上，新增一個腳本元件來執行 [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler)
   介面。 具有 [ `NearInteractionTouchable` ] (x： NearInteractionTouchable) 之物件的任何上階，也都可以接收指標事件。

> [!NOTE]
> 在已選取 *NearInteractionTouchable* GameObject 的編輯器場景視圖中，請注意白色外框方形和箭號。 箭號指向可觸式的「前方」。 Collidable 只會從該方向可觸式。 若要讓碰撞從所有方向可觸式，請參閱 [任意碰撞點觸控](#arbitrary-collider-touch)的一節。
> ![NearInteractionTouchable Gizmos ](../images/input/Pointers/NearInteractionTouchableGizmos.png)

### <a name="arbitrary-collider-touch"></a>任意碰撞點觸控

這對於啟用遊戲物件必須沿著整個碰撞器臉部可觸式的情況很有用。 例如，這可以用來啟用具有 SphereCollider 之物件的觸控互動，而必須可觸式整個碰撞。

1. 在應該可觸式的 GameObject 上，新增碰撞程式和 [ `NearInteractionTouchableVolume` ] (x： MixedReality。 NearInteractionTouchableVolume) 元件。

    1. 如果您在下方的元件腳本中使用 [] (x： IMixedRealityTouchHandler) 介面，請設定 **要接收***觸控* 的事件 `IMixedRealityTouchHandler` 。

1. 在該物件或其中一個祖系上，新增一個腳本元件來執行 [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler)
   介面。 具有 [ `NearInteractionTouchable` ] (x： NearInteractionTouchable) 之物件的任何上階，也都可以接收指標事件。

### <a name="unity-ui"></a>Unity UI

1. 新增/確定場景中有 [UnityUI 畫布](https://docs.unity3d.com/Manual/UICanvas.html) 。

1. 在應該可觸式的 GameObject 上，新增 [`NearInteractionTouchableUnityUI`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableUnityUI) 元件。  

    1. 如果您在下方的元件腳本中使用介面，請設定 **要接收***觸控* 的事件 [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) 。

1. 在該物件或其中一個祖系上，加入可執行介面的腳本元件 [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) 。 具有的物件的任何上階 [`NearInteractionTouchableUnityUI`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableUnityUI) 也都可以接收指標事件。

> [!IMPORTANT]
> 在 `NearInteractionTouchable` 腳本元件中， *要接收* 的屬性事件有兩個選項： *指標* 和 *觸控*。 如果  [`IMixedRealityPointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointerHandler) 您在元件腳本中使用介面來回應/處理輸入事件，請設定要接收到指標的事件，並將其設定為 *觸控* [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) 。

#### <a name="touch-code-example"></a>觸控程式碼範例

下列程式碼示範可以附加至具有 variant 元件之 GameObject 的 MonoBehaviour， [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) 並回應觸控輸入事件。

```c#
public class TouchEventsExample : MonoBehaviour, IMixedRealityTouchHandler
{
    public void OnTouchStarted(HandTrackingInputEventData eventData)
    {
        string ptrName = eventData.Pointer.PointerName;
        Debug.Log($"Touch started from {ptrName}");
    }
    public void OnTouchCompleted(HandTrackingInputEventData eventData) {}
    public void OnTouchUpdated(HandTrackingInputEventData eventData) { }
}
```

## <a name="near-interaction-script-examples"></a>近距離互動腳本範例

### <a name="touch-events"></a>觸控事件

這個範例會建立一個 cube、讓它可觸式，以及變更觸控的色彩。

```c#
public static void MakeChangeColorOnTouch(GameObject target)
{
    // Add and configure the touchable
    var touchable = target.AddComponent<NearInteractionTouchableVolume>();
    touchable.EventsToReceive = TouchableEventType.Pointer;

    var material = target.GetComponent<Renderer>().material;
    // Change color on pointer down and up
    var pointerHandler = target.AddComponent<PointerHandler>();
    pointerHandler.OnPointerDown.AddListener((e) => material.color = Color.green);
    pointerHandler.OnPointerUp.AddListener((e) => material.color = Color.magenta);
}
```

### <a name="grab-events"></a>抓取事件

下列範例顯示如何讓 GameObject 可拖曳。 假設遊戲物件上有碰撞器。

```c#
public static void MakeNearDraggable(GameObject target)
{
    // Instantiate and add grabbable
    target.AddComponent<NearInteractionGrabbable>();

    // Add ability to drag by re-parenting to pointer object on pointer down
    var pointerHandler = target.AddComponent<PointerHandler>();
    pointerHandler.OnPointerDown.AddListener((e) =>
    {
        if (e.Pointer is SpherePointer)
        {
            target.transform.parent = ((SpherePointer)(e.Pointer)).transform;
        }
    });
    pointerHandler.OnPointerUp.AddListener((e) =>
    {
        if (e.Pointer is SpherePointer)
        {
            target.transform.parent = null;
        }
    });
}
```

## <a name="useful-apis"></a>實用的 API

* [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable)
* [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable)
* [`NearInteractionTouchableUnityUI`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableUnityUI)
* [`NearInteractionTouchableVolume`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableVolume)
* [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler)
* [`IMixedRealityPointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointerHandler)

## <a name="see-also"></a>另請參閱

* [輸入概觀](overview.md)
* [指標](pointers.md)
* [輸入事件](input-events.md)
