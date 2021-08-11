---
title: 規劃求解總覽
description: MRTK 中的解析器總覽
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、解析器、
ms.openlocfilehash: 28e961aa20fb15b533f369ed436e2d8178d682801f6f6ce6a703e53a0c26ac01
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2021
ms.locfileid: "115206872"
---
# <a name="solver-overview"></a>規劃求解總覽

![規劃主](../../images/solver/MRTK_Solver_Main.png)

解析器是一種元件，可根據預先定義的演算法，協助計算物件的位置 & 方向。 例如，可能會將物件放在使用者的注視 raycast 目前點擊的表面上。

此外，「規劃求解」系統會以決定性的方式定義這些轉換計算的作業順序，因為沒有可靠的方式可以指定元件的更新順序給 Unity。

解析器提供一系列行為，以將物件附加至其他物件或系統。 另一個範例是標記物件，該物件會停留在使用者 (根據相機) 。 規劃求解也可以附加至控制器和物件，以沿著控制器來建立物件標記。 所有的解析器都可以安全地堆疊，例如標籤-沿著行為 + surface 磁性 + 動力。

## <a name="how-to-use-a-solver"></a>如何使用規劃求解

規劃求解系統包含三種腳本類別：

* [`Solver`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.Solver)：所有解析器衍生自的基底抽象類別。 它提供狀態追蹤、平滑參數和實行、自動規劃求解系統整合，以及更新順序。
* [`SolverHandler`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.SolverHandler)：設定要追蹤的參考物件 (例如：主要相機轉換、手光線等 ) 、處理收集求解元件的程式，並以正確的循序執行更新。

第三個類別是規劃求解本身。 下列解析器提供基本行為的建立區塊：

* [`Orbital`](#orbital)：鎖定至指定的位置，以及從參考的物件位移。
* [`ConstantViewSize`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.ConstantViewSize)：調整以維持相對於參考物件之視圖的固定大小。
* [`RadialView`](#radialview)：將物件保留在被參考物件轉換的視圖錐形內。
* [`Follow`](#follow)：將物件保留在所參考物件的一組使用者定義界限內。
* [`InBetween`](#inbetween)：將物件保留在兩個追蹤的物件之間。
* [`SurfaceMagnetism`](#surfacemagnetism)：將光線轉換成世界中的表面，並將物件對齊該介面。
* [`DirectionalIndicator`](#directionalindicator)：決定物件的位置和方向作為方向指標。 從 SolverHandler 追蹤目標的參考點來看，此指標會指向提供的 DirectionalTarget。
* [`Momentum`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.Momentum)：套用加速度/速度/摩擦，以模擬其他解析器/元件正在移動之物件的動力和 springiness。
* [`HandConstraint`](#hand-menu-with-handconstraint-and-handconstraintpalmup)：限制物件，使其在不與 GameObject 的區域中的實際操作。 適用于手動限制的互動式內容，例如功能表等。這項規劃的目標是要與 [IMixedRealityHand](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHand) 搭配使用，但也可以搭配 [IMixedRealityController](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityController)使用。
* [`HandConstraintPalmUp`](#hand-menu-with-handconstraint-and-handconstraintpalmup)：衍生自 HandConstraint，但會包含邏輯，以測試 palm 是否會在啟用前對使用者進行測試。 此規劃求解只適用于 [IMixedRealityHand](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHand) 控制器，而其他控制器類型則此規劃求解的行為就像其基類一樣。

若要使用「規劃求解」系統，只要將上面所列的其中一個元件加入至 GameObject。 由於所有解析器都需要 [`SolverHandler`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.SolverHandler) ，因此 Unity 會自動建立一個。

> [!NOTE]
> 您可以在 **SolverExamples** 檔中找到如何使用解析器系統的範例。

## <a name="how-to-change-tracking-reference"></a>如何變更追蹤參考

元件的 [ *追蹤的目標型別* ] 屬性 [`SolverHandler`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.SolverHandler) 會定義解析器將用來計算其演算法的參考點。 例如，具有簡單元件的實值型別， [`Head`](xref:Microsoft.MixedReality.Toolkit.Utilities.TrackedObjectType.Head) [`SurfaceMagnetism`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.SurfaceMagnetism) 會導致來自 head 的 raycast 和使用者的注視方向，以解決遇到的介面。 屬性的可能值為 `TrackedTargetType` ：

* *Head* ：參考點是主要攝影機的轉換
* *ControllerRay*：參考點是 [`LinePointer`](xref:Microsoft.MixedReality.Toolkit.Input.LinePointer) 控制器上的轉換 (亦即 移動控制器或手形控制器上的指標原點) 指向線路光線的方向
  * 您 `TrackedHandedness` 可以使用屬性來選取 handedness 喜好設定 (例如 Left、Right、Both) 
* *HandJoint*：參考點是特定手聯合的轉換
  * 您 `TrackedHandedness` 可以使用屬性來選取 handedness 喜好設定 (例如 Left、Right、Both) 
  * 使用  `TrackedHandJoint` 屬性來判斷要使用的聯合轉換
* *CustomOverride*：來自所指派之的參考點 `TransformOverride`

> [!NOTE]
> 針對 *ControllerRay* 和 *HandJoint* 類型，規劃求解處理常式會先嘗試提供左方控制器/手的轉換，如果前者無法使用，則為右邊，除非 `TrackedHandedness` 屬性另有指定。

![](../../images/solver/TrackedObjectType-Example.gif) 
*與每個 TrackedTargetType 相關聯之各種屬性的* 規劃求解追蹤物件範例

> [!IMPORTANT]
> 大部分的解析器會使用所提供之追蹤轉換目標的正向向量 `SolverHandler` 。 使用 *手聯合* 追蹤的目標型別時，掌上接點的正向向量可能會指向手指，而不是透過棕櫚。 這取決於提供手聯合資料的平臺。 針對輸入模擬和 Windows Mixed Reality，它是指向多個 palm (的 *向上向量*，亦即： 綠色向量為向上、藍色向量向前) 。
>
> ![上往上向量](../../images/solver/HandJoint_ForwardUpVectors.png)
>
> 若要解決此情況，請將上的 [ *其他旋轉* ] 屬性更新 `SolverHandler` 為 **<90，0，0>**。 這可確保提供給解析器的正向向量會朝手向外指向掌上和離手。
>
> ![額外的旋轉](../../images/solver/SolverHandler_AdditionalRotation.png)
>
> 或者，您也可以使用 *控制器光線* 追蹤的目標型別，來取得與手形相關的類似行為。

## <a name="how-to-chain-solvers"></a>如何連鎖解析器

您可以將多個 `Solver` 元件新增至相同 GameObject，進而連結其演算法。 `SolverHandler`元件會處理相同 GameObject 上的所有解析器更新。 依預設， `SolverHandler` `GetComponents<Solver>()` 開始時的呼叫會以它們出現在偵測器中的順序傳回解析器。

此外，將 [ *已更新的連結轉換* ] 屬性設定為 [true]，會指示將 `Solver` 其計算的位置、方向 & 調整為所有解析器可存取的中繼變數 (亦即 `GoalPosition`). 若為 false，則 `Solver` 會直接更新 GameObject 的轉換。 藉由將轉換屬性儲存到中繼位置，其他解析器就能從中繼變數開始執行其計算。 這是因為 Unity 不允許更新 gameObject，而是在相同的框架內轉換成堆疊。

> [!NOTE]
> 開發人員可以藉由直接設定屬性來修改解析器的執行順序 `SolverHandler.Solvers` 。

## <a name="how-to-create-a-new-solver"></a>如何建立新的規劃求解

所有解析器都必須繼承自抽象基類 [`Solver`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.Solver) 。 規劃求解擴充功能的主要需求牽涉到覆寫 `SolverUpdate` 方法。 在這個方法中，開發人員應該將繼承的 `GoalPosition` `GoalRotation` 和 `GoalScale` 屬性更新為所需的值。 此外， `SolverHandler.TransformTarget` 作為取用者所需的參考框架，通常是相當重要的。

下面提供的程式碼提供了一個新的規劃求解元件的範例，此元件 `InFront` 會將附加的物件2m 放在前面 `SolverHandler.TransformTarget` 。 如果取用 `SolverHandler.TrackedTargetType` 者將設定為，則 [`Head`](xref:Microsoft.MixedReality.Toolkit.Utilities.TrackedObjectType.Head) `SolverHandler.TransformTarget` 會是相機轉換，因此這個規劃求解會將附加的 GameObject 2m 放在使用者的每個畫面格之前。

```c#
/// <summary>
/// InFront solver positions an object 2m in front of the tracked transform target
/// </summary>
public class InFront : Solver
{
    ...

    public override void SolverUpdate()
    {
        if (SolverHandler != null && SolverHandler.TransformTarget != null)
        {
            var target = SolverHandler.TransformTarget;
            GoalPosition = target.position + target.forward * 2.0f;
        }
    }
}
```

## <a name="solver-implementation-guides"></a>規劃求解的執行指南

### <a name="common-solver-properties"></a>常見的規劃求解屬性

每個求解元件都有一組完全相同的屬性，可控制核心的規劃式行為。

如果啟用 *平滑* 效果，則規劃求解會逐漸將 GameObject 一段時間的轉換逐漸更新為計算的值。 這項變更的速度取決於每個轉換元件的 *LerpTime* 屬性。 例如，較高的 *MoveLerpTime* 值會導致畫面格之間的移動速度變慢。

如果已啟用 *MaintainScale* ，則規劃求解會利用 GameObject 的預設本機規模。

![核心規劃求解屬性](../../images/solver/GeneralSolverProperties.png)  
*所有的規劃求解元件所繼承的通用屬性*

### <a name="orbital"></a>軌道

[`Orbital`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.Orbital)類別是一種以標記為依據的元件，其行為類似于日光系統中的行星。 此規劃將可確保附加的 GameObject 會圍繞追蹤的轉換。 因此，如果的 *追蹤目標型* 別 [`SolverHandler`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.SolverHandler) 設定為 [`Head`](xref:Microsoft.MixedReality.Toolkit.Utilities.TrackedObjectType.Head) ，GameObject 就會在使用者的標頭周圍套用固定位移。

開發人員可以修改此固定位移，讓功能表或其他場景元件在眼睛層級或 waist 層級等。 這是藉由修改 *區域位移* 和 *全球位移* 屬性來完成。 [ *方向類型* ] 屬性會決定套用至物件的旋轉（如果它應該維持其原始的旋轉），或一律面對相機或臉部（無論轉換的位置等）。

![Orbital 範例](../../images/solver/OrbitalExample.png)  
*Orbital 範例*

### <a name="radialview"></a>RadialView

[`RadialView`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.RadialView)是另一個標記式元件，它會將 GameObject 的特定部分保留在使用者的視圖的中。

最 *小 & 最大視圖度數* 屬性會決定 GameObject 部分的大小必須一律在視野中。

[ *最小 & 距離* ] 屬性可決定要從使用者保留 GameObject 的距離。 例如，在 GameObject 的 *最小距離* 為1m 的情況下，會將 GameObject 推離，以確保該使用者絕對不會接近1m。

一般而言， [`RadialView`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.RadialView) 會搭配使用的 *追蹤目標型別* 設定為， [`Head`](xref:Microsoft.MixedReality.Toolkit.Utilities.TrackedObjectType.Head) 讓元件遵循使用者的注視。 不過，這個元件可讓您在任何 *追蹤的目標型別* 的「 *view* 」中保持運作。

![RadialView 範例](../../images/solver/RadialViewExample.png)  
*RadialView 範例*

### <a name="follow"></a>追隨

類別會將專案放 [`Follow`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.Follow) 在相對於其本機向前軸之追蹤目標的前方。 元素可能會受到鬆散限制 (也稱為 加上標籤-沿著) ，使其不會在追蹤的目標超過使用者定義界限時進行追蹤。

它的運作方式類似于 RadialView 的規劃求解，還有額外的控制項可管理 *最大水準 & 垂直視圖度數*，以及改變物件 *方向* 的機制。

![遵循屬性](../../images/solver/FollowExample.png)  
*遵循屬性*

![遵循範例場景](../../images/solver/FollowExampleScene.gif)  
*遵循範例場景 (資產/MRTK/範例/示範/解析器/場景/FollowSolverExample unity)*

### <a name="inbetween"></a>Receivebegindoc

[`InBetween`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.InBetween)類別會在兩個轉換之間保留附加的 GameObject。 這兩個轉換端點是由 GameObject 本身的 [`SolverHandler`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.SolverHandler) *追蹤目標型別* 和 [`InBetween`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.InBetween) 元件 *第二個追蹤的目標型別* 屬性所定義。 一般而言，這兩種類型都會設定為， [`CustomOverride`](xref:Microsoft.MixedReality.Toolkit.Utilities.TrackedObjectType.CustomOverride) 而產生 `SolverHandler.TransformOverride` 和 `InBetween.SecondTransformOverride` 值會設定為兩個追蹤的端點。

在執行時間， [`InBetween`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.InBetween) 元件會 [`SolverHandler`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.SolverHandler) 根據 *第二個追蹤的目標型別* 和 *第二個轉換覆寫* 屬性，建立另一個元件。

會 `PartwayOffset` 定義兩個轉換之間的位置，在第一次轉換時，物件應放置於0.5 的中間、1.0，以及第二個轉換的0.0。

![Receivebegindoc 範例](../../images/solver/InBetweenExample.png)  
*使用 Receivebegindoc 規劃求解將物件保留在兩個轉換之間的範例*

### <a name="surfacemagnetism"></a>SurfaceMagnetism

其運作方式是對介面的 [`SurfaceMagnetism`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.SurfaceMagnetism) 集合 LayerMask 執行 raycast，並將 GameObject 放在該點點。

*介面正常位移* 會將 GameObject 的距離，從表面上的垂直方向，將距離從表面上算起的距離。

相反地， *表面光線位移* 會將 GameObject 設定為距離表面的距離，但在 raycast 執行的方向相反。 因此，如果 raycast 是使用者的注視，則 GameObject 會從表面上的點擊點向相機移動較接近的線。

*方向模式* 會決定要套用的旋轉類型，以與表面上的法線相對應。

* *無* -未套用旋轉
* *TrackedTarget* -物件會面對追蹤的轉換來推動 raycast
* *SurfaceNormal* -物件將依據介面上的一般位置進行對齊
* *混合* 式物件將依據介面上的法線，以及根據追蹤的轉換來對齊。

若要強制相關聯的 GameObject 在非 [ *無*] 的任何模式下保持垂直，請啟用 [ *保持垂直方向*]。

> [!NOTE]
> 使用 [ *方向 Blend* ] 屬性可控制當 *方向模式* 設定為 [ *混合*] 時，旋轉因數之間的平衡。 值為0.0 時，會以 *TrackedTarget* 模式完全驅動方向，而1.0 的值將會由 *SurfaceNormal* 完全驅動方向。

![SurfaceMagnetism 範例](../../images/solver/SurfaceMagExample.png)

#### <a name="determining-what-surfaces-can-be-hit"></a>判斷可點擊的表面

將元件新增 [`SurfaceMagnetism`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.SurfaceMagnetism) 至 GameObject 時，請務必考慮 GameObject 的層級及其子系（如果有的話）。 元件的運作方式是執行各種類型的 raycasts，以判斷「磁鐵」本身的表面。 如果 [規劃求解] GameObject 在的屬性中所列的其中一個圖層上有碰撞器 `MagneticSurfaces` `SurfaceMagnetism` ，則 raycast 可能會在 GameObject 附加至它自己的碰撞點時遇到。 您可以藉由將主要 GameObject 和所有子系設定為 [ *忽略 Raycast* 層]，或 `MagneticSurfaces` 適當地修改 LayerMask 陣列，來避免這種奇怪的行為。

相反地， [`SurfaceMagnetism`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.SurfaceMagnetism) GameObject 不會與未列在屬性中的圖層上的表面衝突 `MagneticSurfaces` 。 一般來說，建議您將所有所需的表面放在專用圖層上 (例如 *) 介面* ，並將 `MagneticSurfaces` 屬性設定為只有這個圖層。  使用 [ *預設* ] 或 [ *所有專案* ] 可能會導致 UI 元件或資料指標參與規劃求解。

最後，raycasts 會忽略比屬性設定更遠的表面 `MaxRaycastDistance` `SurfaceMagnetism` 。

### <a name="directionalindicator"></a>DirectionalIndicator

[`DirectionalIndicator`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.DirectionalIndicator)類別是沿著標記的元件，它會將自己導向至空間中所需的時間點方向。

當的 *追蹤目標型* 別設定為時，最常使用 [`SolverHandler`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.SolverHandler) [`Head`](xref:Microsoft.MixedReality.Toolkit.Utilities.TrackedObjectType.Head) 。 以這種方式，包含規劃求解的 UX 元件 [`DirectionalIndicator`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.DirectionalIndicator)  會引導使用者查看空間中所需的時間點。

需要的空間點是透過 *方向性目標* 屬性來決定。

如果使用者可以看到方向性目標，或在中設定任何參考的畫面格 [`SolverHandler`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.SolverHandler) ，則此規劃求解將會停用 [`Renderer`](https://docs.unity3d.com/ScriptReference/Renderer.html) 其下的所有元件。 如果無法查看，則所有專案都會在指標上啟用。

指標的大小會縮小使用者在其 FOV 中取得 *方向目標* 的更近距離。

* *最小指標尺規* -指標物件的最小縮放比例
* *最大指標刻度* -指標物件的最大刻度

* *可見度比例因數* -乘數，以增加或減少決定 *方向性目標* 點是否可見的 FOV
* *View Offset* -從參考框架的觀點來看 (例如 攝影機可能) ，此屬性會定義在指標方向中，物件是從區中央開始的距離。

![方向指標屬性](../../images/solver/DirectionalIndicatorExample.png)  
*方向指標屬性*

![方向指標範例場景](../../images/solver/DirectionalIndicatorExampleScene.gif)  
*方向指標範例場景 (資產/MRTK/範例/示範/解析器/場景/DirectionalIndicatorSolverExample unity)*

### <a name="hand-menu-with-handconstraint-and-handconstraintpalmup"></a>具有 HandConstraint 和 HandConstraintPalmUp 的手功能表

![手形功能表 UX 範例](../../images/solver/MRTK_UX_HandMenu.png)

此 [`HandConstraint`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.HandConstraint) 行為提供的規劃求解會將追蹤的物件限制為可安全的 (，例如，手動 UI、功能表等) 。 保管庫區域會被視為不會與手相交的區域。 [`HandConstraint`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.HandConstraint)另外也包含了呼叫的衍生類別 [`HandConstraintPalmUp`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.HandConstraintPalmUp) ，以示範當掌上有使用者時啟動規劃求解追蹤物件的常見行為。

如需使用手形條件約束規劃求解來建立快顯功能表的範例，[請參閱手形功能表頁](../hand-menu.md)。

## <a name="see-also"></a>另請參閱

* [手動追蹤](../../input/hand-tracking.md)
* [目光](../../input/gaze.md)
