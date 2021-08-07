---
title: ControllersPointersAndFocus
description: 與控制器、指標和焦點互動。
author: cDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、指標、控制器
ms.openlocfilehash: cc759c827f864c7c53d4b12b284ad4b89d2db9fdebe9e08a25dd3d62b16b6e4a
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2021
ms.locfileid: "115187628"
---
# <a name="controllers-pointers-and-focus"></a>控制器、指標和焦點

控制器、指標和焦點是以核心輸入系統所建立的基礎為基礎所建立的較高層級概念。 兩者結合在一起，可提供一大部分機制來與場景中的物件互動。

## <a name="controllers"></a>控制器

控制器是實體控制器的代表 (6 度的自由、明確的手) 等等。 它們是由裝置管理員所建立，負責與對應的基礎系統進行通訊，並將該資料轉譯成 MRTK 狀的資料和事件。

例如，在 Windows Mixed Reality 平臺上， [`WindowsMixedRealityArticulatedHand`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityArticulatedHand) 是負責與基礎 Windows[手追蹤 api](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate)互動的控制器，以取得關於接點、姿勢和其他屬性的資訊。 它負責將這項資料轉換成相關的 MRTK 事件 (例如，藉由呼叫 RaisePoseInputChanged 或 RaiseHandJointsUpdated) ，以及藉由更新其本身的內部狀態，讓的查詢傳回 [`TryGetJointPose`](xref:Microsoft.MixedReality.Toolkit.Input.HandJointUtils.TryGetJointPose(TrackedHandJoint,Handedness,MixedRealityPose@)) 正確的資料。

一般而言，控制器的生命週期會涉及：

1. 在偵測到新的來源時，裝置管理員會建立一個控制器 (例如，裝置管理員會偵測並開始追蹤) 。

2. 在控制器的更新 () 迴圈中，它會呼叫其基礎 API 系統。

3. 在相同的更新迴圈中，它會藉由直接呼叫核心輸入系統本身來引發輸入事件變更 (例如，引發 HandMeshUpdated 或 HandJointsUpdated) 。

## <a name="pointers-and-focus"></a>指標和焦點

指標是用來與遊戲物件互動。 本節說明如何建立指標、如何更新它們，以及它們如何判斷焦點) 的物件 (。 此外，它也會涵蓋存在的不同指標類型，以及它們處於作用中狀態的案例。

### <a name="pointer-categories"></a>指標分類

指標通常屬於下列其中一個類別：

- **遠指標**

  這些類型的指標會用來與使用者遠離使用者 (的物件互動，而不是定義為「不接近」 ) 。 這些類型的指標通常會將可移至世界各地的線條轉型，並可讓使用者與不緊接在其旁邊的物件互動和操作。

- **近端指標**

  這些類型的指標是用來與接近使用者的物件互動，以抓取、觸控和操作。 一般而言，這些類型的指標會藉由尋找鄰近區域中的物件來與物件互動 (方法是在較小的距離執行 raycasting、執行球形轉型以尋找鄰近區域中的物件，或列舉視為 grabbable/可觸式) 的物件清單。

- **傳送指標**

  這些類型的指標會插入遙傳系統，以處理將使用者移至指標的目標位置。

## <a name="pointer-mediation"></a>指標中繼

由於單一控制器可能會有多個指標 (例如，有向的手勢可以) 接近且遠的互動指標，因此有一個元件負責調節應使用中的指標。

例如，當使用者的手中使用 pressable 按鈕時， [`ShellHandRayPointer`](xref:Microsoft.MixedReality.Toolkit.Input.ShellHandRayPointer) 應該會停止顯示，且 [`PokePointer`](xref:Microsoft.MixedReality.Toolkit.Input.PokePointer) 應該參與。

這是由所處理 [`DefaultPointerMediator`](xref:Microsoft.MixedReality.Toolkit.Input.DefaultPointerMediator) ，它負責根據所有指標的狀態判斷哪些指標是作用中。 這項作業的其中一個重要功能是，當接近的指標接近物件時，會停用遠指標 (請參閱 [`DefaultPointerMediator`](xref:Microsoft.MixedReality.Toolkit.Input.DefaultPointerMediator)) 。

您可以藉由變更 [`PointerMediator`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityPointerProfile.PointerMediator) 指標設定檔上的屬性，提供指標中繼程式的替代實。

### <a name="how-to-disable-pointers"></a>如何停用指標

因為指標中繼程式會執行每個畫面格，所以最後會控制所有指標的作用中/非作用中狀態。 因此，如果您在程式碼中設定指標的 IsInteractionEnabled 屬性，則會在每個畫面格的指標中繼程式中覆寫它。 相反地，您可以指定 [`PointerBehavior`](xref:Microsoft.MixedReality.Toolkit.Input.PointerBehavior) 來控制指標應該自行開啟或關閉。 請注意，只有在您使用預設值和 MRTK 時，才能使用此功能 [`FocusProvider`](xref:Microsoft.MixedReality.Toolkit.Input.FocusProvider) [`DefaultPointerMediator`](xref:Microsoft.MixedReality.Toolkit.Input.DefaultPointerMediator) 。

#### <a name="example-disable-hand-rays-in-mrtk"></a>範例：停用 MRTK 中的手光線

下列程式碼會關閉 MRTK 中的手光：

```c#
// Turn off all hand rays
PointerUtils.SetHandRayPointerBehavior(PointerBehavior.AlwaysOff);

// Turn off hand rays for the right hand only
PointerUtils.SetHandRayPointerBehavior(PointerBehavior.AlwaysOff, Handedness.Right);
```

下列程式碼將會在 MRTK 中將手片的預設行為傳回：

```c#
PointerUtils.SetHandRayPointerBehavior(PointerBehavior.Default);
```

不論是否接近 grabbable，下列程式碼都會強制讓手的光線開啟：

```c#
// Turn off all hand rays
PointerUtils.SetHandRayPointerBehavior(PointerBehavior.AlwaysOn);
```

[`PointerUtils`](xref:Microsoft.MixedReality.Toolkit.Input.PointerUtils)如需 [`TurnPointersOnOff`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.DisablePointersExample) 更多範例，請參閱和。

### <a name="focusprovider"></a>FocusProvider

[`FocusProvider`](xref:Microsoft.MixedReality.Toolkit.Input.FocusProvider)是主力，負責逐一查看所有指標的清單，並找出每個指標的焦點物件。

在每次 `Update()` 呼叫中，這將會：

1. 藉由 raycasting 和執行指標本身所設定的點擊偵測來更新所有指標 (例如，球體指標可指定 SphereOverlap raycastMode，因此 FocusProvider 會執行以球體為基礎的衝突) 

2. 以個別指標為基礎更新焦點物件 (也就是，如果物件取得焦點，它也會觸發這些物件的事件，如果物件遺失焦點，則會觸發焦點遺失等) 。

### <a name="pointer-configuration-and-lifecycle"></a>指標設定和生命週期

[指標可以](../features/input/pointers.md) 在輸入系統設定檔的 [ *指標* ] 區段中設定。

指標的存留期通常如下所示：

1. 裝置管理員會偵測到控制器是否存在。 此裝置管理員接著會透過的呼叫，建立與控制器相關聯的指標集 [`RequestPointers`](xref:Microsoft.MixedReality.Toolkit.Input.BaseInputDeviceManager) 。

2. FocusProvider 會在其 Update () 迴圈中逐一查看所有有效的指標，並執行相關聯的 raycast 或點擊偵測邏輯。 這是用來判斷每個特定指標所專注的物件。

    - 因為可以同時使用多個輸入來源 (例如，有兩個實際操作) ，所以也可以有多個具有焦點的物件。

3. 裝置管理員在發現控制器來源遺失時，將會中斷與遺失控制器相關聯的指標。
