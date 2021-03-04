---
title: HowToAddNearInteractivity
description: MRTK 近乎互動的相關檔
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、近乎互動、
ms.openlocfilehash: fed8846e4157240e38abf862f804f2311eb26dd5
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/03/2021
ms.locfileid: "101780959"
---
# <a name="how-to-add-near-interaction-in-mrtk"></a><span data-ttu-id="8f3db-104">如何在 MRTK 中新增近乎互動</span><span class="sxs-lookup"><span data-stu-id="8f3db-104">How to add near interaction in MRTK</span></span>

<span data-ttu-id="8f3db-105">近距離互動的形式為觸控和抓取。</span><span class="sxs-lookup"><span data-stu-id="8f3db-105">Near interactions come in the form of touches and grabs.</span></span> <span data-ttu-id="8f3db-106">觸控和抓取事件會分別由 [PokePointer](Pointers.md#pokepointer) 和 [SpherePointer](Pointers.md#spherepointer)以指標事件的形式引發。</span><span class="sxs-lookup"><span data-stu-id="8f3db-106">Touch and grab events are raised as pointer events by the [PokePointer](Pointers.md#pokepointer) and [SpherePointer](Pointers.md#spherepointer), respectively.</span></span>

<span data-ttu-id="8f3db-107">在特定 GameObject 上接聽觸控和/或抓取輸入事件需要三個主要步驟。</span><span class="sxs-lookup"><span data-stu-id="8f3db-107">Three key steps are required to listen for touch and/or grab input events on a particular GameObject.</span></span>

1. <span data-ttu-id="8f3db-108">確定已在主要 [MRTK 設定檔](../../configuration/MixedRealityConfigurationGuide.md)中註冊相關的指標。</span><span class="sxs-lookup"><span data-stu-id="8f3db-108">Ensure the relevant pointer is registered in the main [MRTK Configuration Profile](../../configuration/MixedRealityConfigurationGuide.md).</span></span>
1. <span data-ttu-id="8f3db-109">確定所需的 GameObject 具有適當的 [抓取](#add-grab-interactions) 或 [觸控](#add-touch-interactions) 腳本元件和 [`Unity Collider`](https://docs.unity3d.com/ScriptReference/Collider.html) 。</span><span class="sxs-lookup"><span data-stu-id="8f3db-109">Ensure the desired GameObject has the appropriate [grab](#add-grab-interactions) or [touch](#add-touch-interactions) script component and [`Unity Collider`](https://docs.unity3d.com/ScriptReference/Collider.html).</span></span>
1. <span data-ttu-id="8f3db-110">在附加的腳本上，將輸入處理常式介面實作為所需的 GameObject，以接聽 [抓取](#grab-code-example) 或 [觸控](#touch-code-example) 事件。</span><span class="sxs-lookup"><span data-stu-id="8f3db-110">Implement an input handler interface on an attached script to the desired GameObject to listen for the [grab](#grab-code-example) or [touch](#touch-code-example) events.</span></span>

## <a name="add-grab-interactions"></a><span data-ttu-id="8f3db-111">新增抓取互動</span><span class="sxs-lookup"><span data-stu-id="8f3db-111">Add grab interactions</span></span>

1. <span data-ttu-id="8f3db-112">確定已在 *MRTK 指標設定檔* 中註冊 [SpherePointer](Pointers.md#spherepointer) 。</span><span class="sxs-lookup"><span data-stu-id="8f3db-112">Ensure a [SpherePointer](Pointers.md#spherepointer) is registered in the *MRTK Pointer profile*.</span></span>

    <span data-ttu-id="8f3db-113">預設 MRTK 設定檔和預設的 HoloLens 2 設定檔已包含 *SpherePointer*。</span><span class="sxs-lookup"><span data-stu-id="8f3db-113">The default MRTK profile and the default HoloLens 2 profile already contain a *SpherePointer*.</span></span> <span data-ttu-id="8f3db-114">您可以藉由選取 MRTK 設定檔並流覽至 **輸入**  >  **指標**  >  **指標選項**，來確認將會建立 SpherePointer。</span><span class="sxs-lookup"><span data-stu-id="8f3db-114">One can confirm a SpherePointer will be created by selecting the MRTK Configuration Profile and navigating to **Input** > **Pointers** > **Pointer Options**.</span></span> <span data-ttu-id="8f3db-115">預設的 `GrabPointer` 預製專案 (資產/MRTK/SDK/功能/UX/Prefabs/指標) 應以有向的 *控制器類型* 來列出。</span><span class="sxs-lookup"><span data-stu-id="8f3db-115">The default `GrabPointer` prefab (Assets/MRTK/SDK/Features/UX/Prefabs/Pointers) should be listed with a *Controller Type* of *Articulated Hand*.</span></span> <span data-ttu-id="8f3db-116">只要自訂預製專案實作為類別，就可以使用它 [`SpherePointer`](xref:Microsoft.MixedReality.Toolkit.Input.SpherePointer) 。</span><span class="sxs-lookup"><span data-stu-id="8f3db-116">A custom prefab can be utilized as long as it implements the [`SpherePointer`](xref:Microsoft.MixedReality.Toolkit.Input.SpherePointer) class.</span></span>

    ![抓取指標設定檔範例](../images/input/pointers/GrabPointer_MRTKProfile.png)

    <span data-ttu-id="8f3db-118">預設抓取指標會查詢位於抓取點周圍的附近物件，以符合預設的 Hololens 2 介面。</span><span class="sxs-lookup"><span data-stu-id="8f3db-118">The default grab pointer queries for nearby objects in a cone around the grab point to match the default Hololens 2 interface.</span></span>

    ![圓錐抓取指標](https://user-images.githubusercontent.com/39840334/82500569-72d58300-9aa8-11ea-8102-ec9a62832d4e.png)

1. <span data-ttu-id="8f3db-120">在應該 grabbable 的 GameObject 上，加入，以及 [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) 碰撞。</span><span class="sxs-lookup"><span data-stu-id="8f3db-120">On the GameObject that should be grabbable, add a [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable), as well as a collider.</span></span>

    <span data-ttu-id="8f3db-121">請確定 GameObject 的圖層位於 grabbable 層。</span><span class="sxs-lookup"><span data-stu-id="8f3db-121">Make sure the layer of the GameObject is on a grabbable layer.</span></span> <span data-ttu-id="8f3db-122">依預設，所有圖層（ *空間感知* 和 *忽略 Raycasts* ）都會 grabbable。</span><span class="sxs-lookup"><span data-stu-id="8f3db-122">By default, all layers except *Spatial Awareness* and *Ignore Raycasts* are grabbable.</span></span> <span data-ttu-id="8f3db-123">檢查您 *GrabPointer* 預製專案中的 *抓取圖層遮罩*，以查看 grabbable 的圖層。</span><span class="sxs-lookup"><span data-stu-id="8f3db-123">See which layers are grabbable by inspecting the *Grab Layer Masks* in your *GrabPointer* prefab.</span></span>

1. <span data-ttu-id="8f3db-124">在 GameObject 或其中一個祖系上，加入可執行介面的腳本元件 [`IMixedRealityPointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointerHandler) 。</span><span class="sxs-lookup"><span data-stu-id="8f3db-124">On the GameObject or one of its ancestors, add a script component that implements the [`IMixedRealityPointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointerHandler) interface.</span></span> <span data-ttu-id="8f3db-125">具有的物件的任何上階 [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) 也都可以接收指標事件。</span><span class="sxs-lookup"><span data-stu-id="8f3db-125">Any ancestor of the object with the [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) will be able to receive pointer events, as well.</span></span>

### <a name="grab-code-example"></a><span data-ttu-id="8f3db-126">抓取程式碼範例</span><span class="sxs-lookup"><span data-stu-id="8f3db-126">Grab code example</span></span>

<span data-ttu-id="8f3db-127">以下是當事件為觸控或抓取時，將會列印的腳本。</span><span class="sxs-lookup"><span data-stu-id="8f3db-127">Below is a script that will print if an event is a touch or grab.</span></span> <span data-ttu-id="8f3db-128">在相關的 *IMixedRealityPointerHandler* 介面函式中，您可以查看透過觸發該事件的指標類型 [`MixedRealityPointerEventData`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityPointerEventData) 。</span><span class="sxs-lookup"><span data-stu-id="8f3db-128">In the relevant *IMixedRealityPointerHandler* interface function, one can look at the type of pointer that triggers that event via the [`MixedRealityPointerEventData`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityPointerEventData).</span></span> <span data-ttu-id="8f3db-129">如果指標是 *SpherePointer*，則互動是一種抓取。</span><span class="sxs-lookup"><span data-stu-id="8f3db-129">If the pointer is a *SpherePointer*, the interaction is a grab.</span></span>

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

## <a name="add-touch-interactions"></a><span data-ttu-id="8f3db-130">新增觸控互動</span><span class="sxs-lookup"><span data-stu-id="8f3db-130">Add touch interactions</span></span>

<span data-ttu-id="8f3db-131">在 UnityUI 元素上新增觸控互動的程式，與香草 3D Gameobject 的程式不同。</span><span class="sxs-lookup"><span data-stu-id="8f3db-131">The process for adding touch interactions on UnityUI elements is different than for vanilla 3D GameObjects.</span></span> <span data-ttu-id="8f3db-132">您可以跳到下一節（ *UNITY ui*）來啟用 unity ui 元件。</span><span class="sxs-lookup"><span data-stu-id="8f3db-132">You can skip to the following section, *Unity UI*, for enabling Unity UI components.</span></span>

<span data-ttu-id="8f3db-133">不過，對於 **這兩種** 類型的 UX 元素，請確定已在 *MRTK 指標設定檔* 中註冊 [PokePointer](Pointers.md#pokepointer) 。</span><span class="sxs-lookup"><span data-stu-id="8f3db-133">For **both** types of UX elements though, ensure a [PokePointer](Pointers.md#pokepointer) is registered in the *MRTK Pointer profile*.</span></span>

<span data-ttu-id="8f3db-134">預設 MRTK 設定檔和預設的 HoloLens 2 設定檔已包含 *PokePointer*。</span><span class="sxs-lookup"><span data-stu-id="8f3db-134">The default MRTK profile and the default HoloLens 2 profile already contain a *PokePointer*.</span></span> <span data-ttu-id="8f3db-135">您可以藉由選取 MRTK 設定檔並流覽至 **輸入**  >  **指標**  >  **指標選項**，來確認將會建立 PokePointer。</span><span class="sxs-lookup"><span data-stu-id="8f3db-135">One can confirm a PokePointer will be created by selecting the MRTK Configuration Profile and navigate to **Input** > **Pointers** > **Pointer Options**.</span></span> <span data-ttu-id="8f3db-136">預設的 `PokePointer` (資產/MRTK/SDK/Features/UX/Prefabs/指標) 預製專案應該會列出，且 *控制器類型* 為有向的 *手*。</span><span class="sxs-lookup"><span data-stu-id="8f3db-136">The default `PokePointer` (Assets/MRTK/SDK/Features/UX/Prefabs/Pointers) prefab should be listed with a *Controller Type* of *Articulated Hand*.</span></span> <span data-ttu-id="8f3db-137">只要自訂預製專案實作為類別，就可以使用它 [`PokePointer`](xref:Microsoft.MixedReality.Toolkit.Input.PokePointer) 。</span><span class="sxs-lookup"><span data-stu-id="8f3db-137">A custom prefab can be utilized as long as it implements the [`PokePointer`](xref:Microsoft.MixedReality.Toolkit.Input.PokePointer) class.</span></span>

![移動指標設定檔範例](../images/input/pointers/PokePointer_MRTKProfile.png)

### <a name="3d-gameobjects"></a><span data-ttu-id="8f3db-139">3D Gameobject</span><span class="sxs-lookup"><span data-stu-id="8f3db-139">3D GameObjects</span></span>

<span data-ttu-id="8f3db-140">有兩種不同的方式可將觸控互動新增至 3D Gameobject，取決於您的3d 物件是否應該只有單一可觸式平面，或是否應該根據其整個碰撞項加以可觸式。</span><span class="sxs-lookup"><span data-stu-id="8f3db-140">There are two different ways of adding touch interactions to 3D GameObjects, depending on if your 3d object should only have a single touchable plane, or of if it should be touchable based on its entire collider.</span></span>
<span data-ttu-id="8f3db-141">第一種方式通常是在具有 BoxColliders 的物件上，而只想要讓碰撞器回應觸控事件的單一臉部。</span><span class="sxs-lookup"><span data-stu-id="8f3db-141">The first way is typically on objects with BoxColliders, where it is desired to only have a single face of the collider react to touch events.</span></span> <span data-ttu-id="8f3db-142">另一個則適用于需要根據其碰撞器從任何方向可觸式的物件。</span><span class="sxs-lookup"><span data-stu-id="8f3db-142">The other is for objects that need to be touchable from any direction based on their collider.</span></span>

### <a name="single-face-touch"></a><span data-ttu-id="8f3db-143">單一臉部觸控</span><span class="sxs-lookup"><span data-stu-id="8f3db-143">Single face touch</span></span>

<span data-ttu-id="8f3db-144">這對於啟用只需要可觸式單一臉部的情況很有用。</span><span class="sxs-lookup"><span data-stu-id="8f3db-144">This is useful to enable situations where only a single face needs to be touchable.</span></span> <span data-ttu-id="8f3db-145">此選項假設遊戲物件有 BoxCollider。</span><span class="sxs-lookup"><span data-stu-id="8f3db-145">This option assumes that the game object has a BoxCollider.</span></span> <span data-ttu-id="8f3db-146">您可以使用此功能搭配非 BoxCollider 物件，在此情況下，會以手動方式將 ' 界限 ' 和 ' Local Center ' 屬性設定為設定可觸式平面 (也就是，界限應該設定為非零零值) 。</span><span class="sxs-lookup"><span data-stu-id="8f3db-146">it's possible to use this with non-BoxCollider objects, in which case the 'Bounds' and 'Local Center' properties much be manually set to configure the touchable plane (i.e. Bounds should be set to a non-zero-zero value).</span></span>

1. <span data-ttu-id="8f3db-147">在應該可觸式的 GameObject 上，新增 BoxCollider 和 [ `NearInteractionTouchable` ] (x：： MixedReality) 元件。</span><span class="sxs-lookup"><span data-stu-id="8f3db-147">On the GameObject that should be touchable, add a BoxCollider and a [`NearInteractionTouchable`] (xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) component.</span></span>

    1. <span data-ttu-id="8f3db-148">如果您在下方的元件腳本中使用 [] (x： IMixedRealityTouchHandler) 介面，請設定 \**要接收\*\*\*觸控* 的事件 `IMixedRealityTouchHandler` 。</span><span class="sxs-lookup"><span data-stu-id="8f3db-148">Set **Events to Receive** to *Touch* if using the [`IMixedRealityTouchHandler`] (xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) interface in your component script below.</span></span>

    1. <span data-ttu-id="8f3db-149">按一下 [**修正界限** 和 **修正中心**]</span><span class="sxs-lookup"><span data-stu-id="8f3db-149">Click **Fix bounds** and **Fix center**</span></span>

    ![NearInteractionTouchable Gizmos 範例1](../images/input/pointers/NearInteractionTouchableSetup.gif)

1. <span data-ttu-id="8f3db-151">在該物件或其中一個祖系上，新增一個腳本元件來執行 [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler)</span><span class="sxs-lookup"><span data-stu-id="8f3db-151">On that object or one of its ancestors, add a script component that implements the [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler)</span></span>
   <span data-ttu-id="8f3db-152">介面。</span><span class="sxs-lookup"><span data-stu-id="8f3db-152">interface.</span></span> <span data-ttu-id="8f3db-153">具有 [ `NearInteractionTouchable` ] (x： NearInteractionTouchable) 之物件的任何上階，也都可以接收指標事件。</span><span class="sxs-lookup"><span data-stu-id="8f3db-153">Any ancestor of the object with the [`NearInteractionTouchable`] (xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) will be able to receive pointer events, as well.</span></span>

> [!NOTE]
> <span data-ttu-id="8f3db-154">在已選取 *NearInteractionTouchable* GameObject 的編輯器場景視圖中，請注意白色外框方形和箭號。</span><span class="sxs-lookup"><span data-stu-id="8f3db-154">In the editor scene view with the *NearInteractionTouchable* GameObject selected, notice a white outline square and arrow.</span></span> <span data-ttu-id="8f3db-155">箭號指向可觸式的「前方」。</span><span class="sxs-lookup"><span data-stu-id="8f3db-155">The arrow points to the "front" of the touchable.</span></span> <span data-ttu-id="8f3db-156">Collidable 只會從該方向可觸式。</span><span class="sxs-lookup"><span data-stu-id="8f3db-156">The collidable will only be touchable from that direction.</span></span> <span data-ttu-id="8f3db-157">若要讓碰撞從所有方向可觸式，請參閱 [任意碰撞點觸控](#arbitrary-collider-touch)的一節。</span><span class="sxs-lookup"><span data-stu-id="8f3db-157">To make a collider touchable from all directions, see the section on [arbitrary collider touch](#arbitrary-collider-touch).</span></span>
> <span data-ttu-id="8f3db-158">![NearInteractionTouchable Gizmos 範例2](../images/input/pointers/NearInteractionTouchableGizmos.png)</span><span class="sxs-lookup"><span data-stu-id="8f3db-158">![NearInteractionTouchable Gizmos Example 2](../images/input/pointers/NearInteractionTouchableGizmos.png)</span></span>

### <a name="arbitrary-collider-touch"></a><span data-ttu-id="8f3db-159">任意碰撞點觸控</span><span class="sxs-lookup"><span data-stu-id="8f3db-159">Arbitrary collider touch</span></span>

<span data-ttu-id="8f3db-160">這對於啟用遊戲物件必須沿著整個碰撞器臉部可觸式的情況很有用。</span><span class="sxs-lookup"><span data-stu-id="8f3db-160">This is useful to enable situations where the game object needs to be touchable along its entire collider face.</span></span> <span data-ttu-id="8f3db-161">例如，這可以用來啟用具有 SphereCollider 之物件的觸控互動，而必須可觸式整個碰撞。</span><span class="sxs-lookup"><span data-stu-id="8f3db-161">For example, this can be used to enable touch interactions for an object with a SphereCollider, where the entire collider needs to be touchable.</span></span>

1. <span data-ttu-id="8f3db-162">在應該可觸式的 GameObject 上，新增碰撞程式和 [ `NearInteractionTouchableVolume` ] (x： MixedReality。 NearInteractionTouchableVolume) 元件。</span><span class="sxs-lookup"><span data-stu-id="8f3db-162">On the GameObject that should be touchable, add a collider and a [`NearInteractionTouchableVolume`] (xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableVolume) component.</span></span>

    1. <span data-ttu-id="8f3db-163">如果您在下方的元件腳本中使用 [] (x： IMixedRealityTouchHandler) 介面，請設定 \**要接收\*\*\*觸控* 的事件 `IMixedRealityTouchHandler` 。</span><span class="sxs-lookup"><span data-stu-id="8f3db-163">Set **Events to Receive** to *Touch* if using the [`IMixedRealityTouchHandler`] (xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) interface in your component script below.</span></span>

1. <span data-ttu-id="8f3db-164">在該物件或其中一個祖系上，新增一個腳本元件來執行 [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler)</span><span class="sxs-lookup"><span data-stu-id="8f3db-164">On that object or one of its ancestors, add a script component that implements the [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler)</span></span>
   <span data-ttu-id="8f3db-165">介面。</span><span class="sxs-lookup"><span data-stu-id="8f3db-165">interface.</span></span> <span data-ttu-id="8f3db-166">具有 [ `NearInteractionTouchable` ] (x： NearInteractionTouchable) 之物件的任何上階，也都可以接收指標事件。</span><span class="sxs-lookup"><span data-stu-id="8f3db-166">Any ancestor of the object with the [`NearInteractionTouchable`] (xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) will be able to receive pointer events, as well.</span></span>

### <a name="unity-ui"></a><span data-ttu-id="8f3db-167">Unity UI</span><span class="sxs-lookup"><span data-stu-id="8f3db-167">Unity UI</span></span>

1. <span data-ttu-id="8f3db-168">新增/確定場景中有 [UnityUI 畫布](https://docs.unity3d.com/Manual/UICanvas.html) 。</span><span class="sxs-lookup"><span data-stu-id="8f3db-168">Add/ensure there is a [UnityUI canvas](https://docs.unity3d.com/Manual/UICanvas.html) in the scene.</span></span>

1. <span data-ttu-id="8f3db-169">在應該可觸式的 GameObject 上，新增 [`NearInteractionTouchableUnityUI`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableUnityUI) 元件。</span><span class="sxs-lookup"><span data-stu-id="8f3db-169">On the GameObject that should be touchable, add a [`NearInteractionTouchableUnityUI`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableUnityUI) component.</span></span>  

    1. <span data-ttu-id="8f3db-170">如果您在下方的元件腳本中使用介面，請設定 \**要接收\*\*\*觸控* 的事件 [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) 。</span><span class="sxs-lookup"><span data-stu-id="8f3db-170">Set **Events to Receive** to *Touch* if using the [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) interface in your component script below.</span></span>

1. <span data-ttu-id="8f3db-171">在該物件或其中一個祖系上，加入可執行介面的腳本元件 [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) 。</span><span class="sxs-lookup"><span data-stu-id="8f3db-171">On that object or one of its ancestors, add a script component that implements the [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) interface.</span></span> <span data-ttu-id="8f3db-172">具有的物件的任何上階 [`NearInteractionTouchableUnityUI`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableUnityUI) 也都可以接收指標事件。</span><span class="sxs-lookup"><span data-stu-id="8f3db-172">Any ancestor of the object with the [`NearInteractionTouchableUnityUI`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableUnityUI) will be able to receive pointer events as well.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8f3db-173">在 `NearInteractionTouchable` 腳本元件中， *要接收* 的屬性事件有兩個選項： *指標* 和 *觸控*。</span><span class="sxs-lookup"><span data-stu-id="8f3db-173">On the `NearInteractionTouchable` script component, for the property *Events to Receive* there are two options: *Pointer* and *Touch*.</span></span> <span data-ttu-id="8f3db-174">如果  [`IMixedRealityPointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointerHandler) 您在元件腳本中使用介面來回應/處理輸入事件，請設定要接收到指標的事件，並將其設定為 *觸控* [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) 。</span><span class="sxs-lookup"><span data-stu-id="8f3db-174">Set *Events to Receive* to *Pointer* if using the [`IMixedRealityPointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointerHandler) interface and set to *Touch* if using the [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) interface in your component script that responds/handles the input events.</span></span>

#### <a name="touch-code-example"></a><span data-ttu-id="8f3db-175">觸控程式碼範例</span><span class="sxs-lookup"><span data-stu-id="8f3db-175">Touch code example</span></span>

<span data-ttu-id="8f3db-176">下列程式碼示範可以附加至具有 variant 元件之 GameObject 的 MonoBehaviour， [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) 並回應觸控輸入事件。</span><span class="sxs-lookup"><span data-stu-id="8f3db-176">The code below demonstrates a MonoBehaviour that can be attached to a GameObject with a [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) variant component and respond to touch input events.</span></span>

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

## <a name="near-interaction-script-examples"></a><span data-ttu-id="8f3db-177">近距離互動腳本範例</span><span class="sxs-lookup"><span data-stu-id="8f3db-177">Near interaction script examples</span></span>

### <a name="touch-events"></a><span data-ttu-id="8f3db-178">觸控事件</span><span class="sxs-lookup"><span data-stu-id="8f3db-178">Touch events</span></span>

<span data-ttu-id="8f3db-179">這個範例會建立一個 cube、讓它可觸式，以及變更觸控的色彩。</span><span class="sxs-lookup"><span data-stu-id="8f3db-179">This example creates a cube, makes it touchable, and changes color on touch.</span></span>

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

### <a name="grab-events"></a><span data-ttu-id="8f3db-180">抓取事件</span><span class="sxs-lookup"><span data-stu-id="8f3db-180">Grab events</span></span>

<span data-ttu-id="8f3db-181">下列範例顯示如何讓 GameObject 可拖曳。</span><span class="sxs-lookup"><span data-stu-id="8f3db-181">The below example shows how to make a GameObject draggable.</span></span> <span data-ttu-id="8f3db-182">假設遊戲物件上有碰撞器。</span><span class="sxs-lookup"><span data-stu-id="8f3db-182">Assumes that the game object has a collider on it.</span></span>

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

## <a name="useful-apis"></a><span data-ttu-id="8f3db-183">實用的 API</span><span class="sxs-lookup"><span data-stu-id="8f3db-183">Useful APIs</span></span>

* [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable)
* [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable)
* [`NearInteractionTouchableUnityUI`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableUnityUI)
* [`NearInteractionTouchableVolume`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableVolume)
* [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler)
* [`IMixedRealityPointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointerHandler)

## <a name="see-also"></a><span data-ttu-id="8f3db-184">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8f3db-184">See also</span></span>

* [<span data-ttu-id="8f3db-185">輸入概觀</span><span class="sxs-lookup"><span data-stu-id="8f3db-185">Input Overview</span></span>](Overview.md)
* [<span data-ttu-id="8f3db-186">指標</span><span class="sxs-lookup"><span data-stu-id="8f3db-186">Pointers</span></span>](Pointers.md)
* [<span data-ttu-id="8f3db-187">輸入事件</span><span class="sxs-lookup"><span data-stu-id="8f3db-187">Input Events</span></span>](InputEvents.md)
