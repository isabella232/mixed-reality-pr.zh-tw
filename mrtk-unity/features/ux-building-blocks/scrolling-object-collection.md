---
title: 滾動物件集合
description: 總覽功能表類型 MRTK
author: vaoliva
ms.author: vaolivaa
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、滾動物件
ms.openlocfilehash: a724b9fb4a0f72910e16353a6c76b9e31005a76e
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176603"
---
# <a name="scrolling-object-collection"></a><span data-ttu-id="c9679-104">滾動物件集合</span><span class="sxs-lookup"><span data-stu-id="c9679-104">Scrolling object collection</span></span>

![滾動物件集合](../images/scrolling-collection/ScrollingCollection_Main.jpg)

<span data-ttu-id="c9679-106">MRTK 滾動物件集合是 UX 元件，可透過包含的可見區域來滾動3D 內容。</span><span class="sxs-lookup"><span data-stu-id="c9679-106">The MRTK scrolling object collection is an UX component that enables scrolling of 3D content through a contained viewable area.</span></span> <span data-ttu-id="c9679-107">滾動移動可透過接近或遠的輸入互動和離散分頁來觸發。</span><span class="sxs-lookup"><span data-stu-id="c9679-107">The scrolling movement can be triggered by near or far input interaction and by discrete pagination.</span></span> <span data-ttu-id="c9679-108">它同時支援互動式和非互動式物件。</span><span class="sxs-lookup"><span data-stu-id="c9679-108">It supports both interactive and non-interactive objects.</span></span>

## <a name="getting-started-with-the-scrolling-object-collection"></a><span data-ttu-id="c9679-109">開始使用滾動物件集合</span><span class="sxs-lookup"><span data-stu-id="c9679-109">Getting started with the scrolling object collection</span></span>

### <a name="setting-up-the-scene"></a><span data-ttu-id="c9679-110">設定場景</span><span class="sxs-lookup"><span data-stu-id="c9679-110">Setting up the scene</span></span>

1. <span data-ttu-id="c9679-111">建立新的 unity 場景。</span><span class="sxs-lookup"><span data-stu-id="c9679-111">Create a new unity scene.</span></span>
1. <span data-ttu-id="c9679-112">藉由流覽至 **混合現實工具** 組  >  **加入場景並設定**，將 MRTK 加入場景。</span><span class="sxs-lookup"><span data-stu-id="c9679-112">Add MRTK to the scene by navigating to the **Mixed Reality Toolkit** > **Add to Scene and Configure**.</span></span>

### <a name="setting-up-the-scrolling-object"></a><span data-ttu-id="c9679-113">設定滾動物件</span><span class="sxs-lookup"><span data-stu-id="c9679-113">Setting up the scrolling object</span></span>

1. <span data-ttu-id="c9679-114">在場景中建立空白的遊戲物件，並將其位置變更為 (0、0、1) 。</span><span class="sxs-lookup"><span data-stu-id="c9679-114">Create an empty game object in the scene and change its position to (0, 0, 1).</span></span>
1. <span data-ttu-id="c9679-115">將 [滾動物件集合](xref:Microsoft.MixedReality.Toolkit.UI.ScrollingObjectCollection) 元件新增至遊戲物件。</span><span class="sxs-lookup"><span data-stu-id="c9679-115">Add a [scrolling object collection](xref:Microsoft.MixedReality.Toolkit.UI.ScrollingObjectCollection) component to the game object.</span></span>

    <span data-ttu-id="c9679-116">加入滾動物件集合時，會自動將方塊碰撞器和 [近端互動可觸式](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) 元件附加至根遊戲物件。</span><span class="sxs-lookup"><span data-stu-id="c9679-116">When the scrolling object collection is added, a box collider and a [near interaction touchable](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) component will be automatically attached to the root game object.</span></span> <span data-ttu-id="c9679-117">這些元件可讓 scroll 物件接聽近距離互動輸入事件，例如指標觸控或按一下。</span><span class="sxs-lookup"><span data-stu-id="c9679-117">These components allow the scroll object to listen to near and far interaction input events, like a pointer touch or click.</span></span>  

    <span data-ttu-id="c9679-118">MRTK 滾動物件集合有兩個重要元素，這些元素會在根滾動物件階層下建立為子遊戲物件：</span><span class="sxs-lookup"><span data-stu-id="c9679-118">The MRTK scrolling object collection has two important elements that are created as child game objects under the root scrolling object hierarchy:</span></span>
    * <span data-ttu-id="c9679-119">`Container` -所有滾動的內容物件都必須是容器遊戲物件的子系。</span><span class="sxs-lookup"><span data-stu-id="c9679-119">`Container` - All scrolling content objects must be children of the container game object.</span></span>
    * <span data-ttu-id="c9679-120">`Clipping bounds` -如果已啟用滾動內容遮罩，則裁剪界限元素可確保只會顯示其界限內的可滾動內容。</span><span class="sxs-lookup"><span data-stu-id="c9679-120">`Clipping bounds` - If scrolling content masking is enabled, the clipping bounds element ensures that only the scrollable content inside its boundaries is visible.</span></span> <span data-ttu-id="c9679-121">裁剪界限遊戲物件有兩個元件：停用的方塊碰撞器和 [裁剪](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox)方塊。</span><span class="sxs-lookup"><span data-stu-id="c9679-121">The clipping bounds game object has two components: a disabled box collider and a [clipping box](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox).</span></span>

![滾動物件集合元素](../images/scrolling-collection/ScrollingObjectCollection.png)

### <a name="adding-content-to-the-scrolling-object"></a><span data-ttu-id="c9679-123">將內容加入至滾動物件</span><span class="sxs-lookup"><span data-stu-id="c9679-123">Adding content to the scrolling object</span></span>

<span data-ttu-id="c9679-124">滾動物件集合可以與 [格線物件集合](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection) 結合，以便在具有統一大小和間距的對齊元素方格中配置內容。</span><span class="sxs-lookup"><span data-stu-id="c9679-124">The scrolling object collection can be combined with a [grid object collection](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection) to layout content in a grid of aligned elements that have uniform size and spacing.</span></span>

1. <span data-ttu-id="c9679-125">建立空的遊戲物件做為捲軸容器的子系。</span><span class="sxs-lookup"><span data-stu-id="c9679-125">Create an empty game object as a child of the scroll container.</span></span>
1. <span data-ttu-id="c9679-126">將方格物件集合元件新增至遊戲物件。</span><span class="sxs-lookup"><span data-stu-id="c9679-126">Add a grid object collection component to the game object.</span></span>
1. <span data-ttu-id="c9679-127">若是垂直的單一資料行捲軸，請在 [偵測器] 索引標籤中，設定網格物件集合，如下所示：</span><span class="sxs-lookup"><span data-stu-id="c9679-127">For a vertical single column scroll, in the inspector tab, configure the grid object collection as follow:</span></span>
    * <span data-ttu-id="c9679-128">**Num 資料行**：1</span><span class="sxs-lookup"><span data-stu-id="c9679-128">**Num columns**: 1</span></span>
    * <span data-ttu-id="c9679-129">**版面** 配置：資料行 then 資料列</span><span class="sxs-lookup"><span data-stu-id="c9679-129">**Layout**: column then row</span></span>
    * <span data-ttu-id="c9679-130">**錨點**：左上方</span><span class="sxs-lookup"><span data-stu-id="c9679-130">**Anchor**: upper left</span></span>
1. <span data-ttu-id="c9679-131">根據內容物件的尺寸來變更 **儲存格的寬度** 和 **高度** 。</span><span class="sxs-lookup"><span data-stu-id="c9679-131">Change the **cell width** and **height** according to the dimensions of the content objects.</span></span>
1. <span data-ttu-id="c9679-132">將 content 物件新增為 grid 物件的子系。</span><span class="sxs-lookup"><span data-stu-id="c9679-132">Add the content objects as children of the grid object.</span></span>
1. <span data-ttu-id="c9679-133">按下 [ **更新集合**]。</span><span class="sxs-lookup"><span data-stu-id="c9679-133">Press **update collection**.</span></span>

![格線版面配置](../images/scrolling-collection/ScrollingObjectCollection_GridLayout.png)

> [!IMPORTANT]
> <span data-ttu-id="c9679-135">任何滾動的內容物件材質都必須使用 [MRTK 標準著色器](../rendering/MRTK-standard-shader.md) ，才能讓可見區域的剪切效果正常運作。</span><span class="sxs-lookup"><span data-stu-id="c9679-135">Any scrolling content object material must use the [MRTK standard shader](../rendering/MRTK-standard-shader.md) in order for the clipping effect on the viewable area to work properly.</span></span>

> [!NOTE]
> <span data-ttu-id="c9679-136">如果已啟用滾動內容遮罩，則滾動物件集合會將 [材質實例](../rendering/material-instance.md) 元件加入至已附加轉譯器的任何內容物件。</span><span class="sxs-lookup"><span data-stu-id="c9679-136">If scrolling content masking is enabled, the scrolling object collection will add a [material instance](../rendering/material-instance.md) component to any content objects that have a renderer attached.</span></span> <span data-ttu-id="c9679-137">此元件可用來管理實例材質存留期，並改善記憶體效能。</span><span class="sxs-lookup"><span data-stu-id="c9679-137">This component is used to manage instanced materials lifetime and improve memory performance.</span></span>

### <a name="configuring-the-scrolling-viewable-area"></a><span data-ttu-id="c9679-138">設定捲軸可見區域</span><span class="sxs-lookup"><span data-stu-id="c9679-138">Configuring the scrolling viewable area</span></span>

1. <span data-ttu-id="c9679-139">若要透過物件的單一資料行垂直捲動，請在 [偵測器] 索引標籤中，設定滾動物件集合，如下所示：</span><span class="sxs-lookup"><span data-stu-id="c9679-139">For vertical scrolling through a single column of objects, in the inspector tab, configure the scrolling object collection as follow:</span></span>
    * <span data-ttu-id="c9679-140">**每一層** 的資料格：1</span><span class="sxs-lookup"><span data-stu-id="c9679-140">**Cells per tier**: 1</span></span>
    * <span data-ttu-id="c9679-141">根據所需的可見資料列數目，選擇 **每頁的層級** 數目</span><span class="sxs-lookup"><span data-stu-id="c9679-141">Choose the number of **tiers per page** according to the desired number of visible rows</span></span>
1. <span data-ttu-id="c9679-142">根據內容物件的尺寸，變更 **頁面儲存格寬度**、 **高度** 和 **深度** 。</span><span class="sxs-lookup"><span data-stu-id="c9679-142">Change the **page cell width**, **height** and **depth** according to the dimensions of the content objects.</span></span>

<span data-ttu-id="c9679-143">請注意，在捲軸可見區域外的內容物件現在是停用的，而與捲軸線框相交的物件可能會由裁剪基本部分遮罩。</span><span class="sxs-lookup"><span data-stu-id="c9679-143">Notice how the content objects lying outside the scrolling viewable area are now disabled, while objects intersecting the scroll wireframe might be partially masked by the clipping primitive.</span></span>

![可見區域](../images/scrolling-collection/ScrollingObjectCollection_ViewableArea.png)

### <a name="testing-the-scrolling-object-collection-in-the-editor"></a><span data-ttu-id="c9679-145">在編輯器中測試滾動物件集合</span><span class="sxs-lookup"><span data-stu-id="c9679-145">Testing the scrolling object collection in the editor</span></span>

1. <span data-ttu-id="c9679-146">按下 [播放] 並按住空格鍵以顯示輸入模擬手。</span><span class="sxs-lookup"><span data-stu-id="c9679-146">Press play and hold the space bar to show an input simulation hand.</span></span>
1. <span data-ttu-id="c9679-147">移動手，直到滾動碰撞器或任何滾動的互動式內容都處於焦點狀態，然後按一下滑鼠左鍵並向下拖曳，以觸發滾動移動。</span><span class="sxs-lookup"><span data-stu-id="c9679-147">Move the hand until the scrolling collider or any scrolling interactive content is in focus and trigger the scrolling movement by clicking and dragging up and down with the left mouse.</span></span>

## <a name="controlling-the-scrolling-object-from-code"></a><span data-ttu-id="c9679-148">從程式碼控制滾動物件</span><span class="sxs-lookup"><span data-stu-id="c9679-148">Controlling the scrolling object from code</span></span>

<span data-ttu-id="c9679-149">MRTK 滾動物件集合會公開一些公用方法，以允許移動滾動容器，方法是根據屬性設定來貼上其位置 `pagination` 。</span><span class="sxs-lookup"><span data-stu-id="c9679-149">The MRTK scrolling object collection exposes a few public methods that allow moving the scrolling container by snapping its position according to the `pagination` properties configuration.</span></span>

<span data-ttu-id="c9679-150">如何存取滾動物件集合分頁介面的範例可用於 ``MRTK/Examples/Demos/ScrollingObjectCollection/Scripts`` 資料夾之下。</span><span class="sxs-lookup"><span data-stu-id="c9679-150">An example of how to access the scrolling object collection pagination interface is available to use under the ``MRTK/Examples/Demos/ScrollingObjectCollection/Scripts`` folder.</span></span> <span data-ttu-id="c9679-151">可 [滾動分頁](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.ScrollablePagination) 範例腳本可以連結至場景中任何現有的滾動物件集合。</span><span class="sxs-lookup"><span data-stu-id="c9679-151">The [scrollable pagination](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.ScrollablePagination) example script can be linked to any existing scrolling object collection in the scene.</span></span> <span data-ttu-id="c9679-152">然後，可透過公開 Unity 事件的場景元件參考腳本 (例如， [MRTK 按鈕](button.md)) 。</span><span class="sxs-lookup"><span data-stu-id="c9679-152">The script can then be referenced by scene components exposing Unity events (e.g, [MRTK button](button.md)).</span></span>

```c#
public class ScrollablePagination : MonoBehaviour
{
    [SerializeField]
    private ScrollingObjectCollection scrollView;

    public void ScrollByTier(int amount)
    {
        scrollView.MoveByTiers(amount);
    }
}
```

## <a name="scrolling-object-collection-properties"></a><span data-ttu-id="c9679-153">滾動物件集合屬性</span><span class="sxs-lookup"><span data-stu-id="c9679-153">Scrolling object collection properties</span></span>

| <span data-ttu-id="c9679-154">一般</span><span class="sxs-lookup"><span data-stu-id="c9679-154">General</span></span>          | <span data-ttu-id="c9679-155">描述</span><span class="sxs-lookup"><span data-stu-id="c9679-155">Description</span></span>                                   |
| :--------------- | :-------------------------------------------- |
| <span data-ttu-id="c9679-156">捲動方向</span><span class="sxs-lookup"><span data-stu-id="c9679-156">Scroll direction</span></span> | <span data-ttu-id="c9679-157">內容應滾動的方向。</span><span class="sxs-lookup"><span data-stu-id="c9679-157">The direction in which content should scroll.</span></span> |

| <span data-ttu-id="c9679-158">分頁</span><span class="sxs-lookup"><span data-stu-id="c9679-158">Pagination</span></span>     | <span data-ttu-id="c9679-159">描述</span><span class="sxs-lookup"><span data-stu-id="c9679-159">Description</span></span>                                                                                               |
| :------------- | :-------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="c9679-160">每一層的資料格</span><span class="sxs-lookup"><span data-stu-id="c9679-160">Cells per tier</span></span> | <span data-ttu-id="c9679-161">在上下捲軸上，資料列中的資料格數目，或是由左至右捲軸之資料行中的資料格數目。</span><span class="sxs-lookup"><span data-stu-id="c9679-161">Number of cells in a row on up-down scroll view or number of cells in a column on left-right scroll view.</span></span> |
| <span data-ttu-id="c9679-162">每頁層級</span><span class="sxs-lookup"><span data-stu-id="c9679-162">Tiers per page</span></span> | <span data-ttu-id="c9679-163">捲動區域中可見層的數目。</span><span class="sxs-lookup"><span data-stu-id="c9679-163">Number of visible tiers in the scrolling area.</span></span>                                                            |
| <span data-ttu-id="c9679-164">頁面儲存格</span><span class="sxs-lookup"><span data-stu-id="c9679-164">Page cell</span></span>      | <span data-ttu-id="c9679-165">分頁資料格的維度。</span><span class="sxs-lookup"><span data-stu-id="c9679-165">Dimensions of the pagination cell.</span></span>                                                                        |

| <span data-ttu-id="c9679-166">進階設定</span><span class="sxs-lookup"><span data-stu-id="c9679-166">Advanced settings</span></span>           | <span data-ttu-id="c9679-167">描述</span><span class="sxs-lookup"><span data-stu-id="c9679-167">Description</span></span>                                                                                                                                                                |
| :-------------------------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="c9679-168">遮罩編輯模式</span><span class="sxs-lookup"><span data-stu-id="c9679-168">Mask edit mode</span></span>              | <span data-ttu-id="c9679-169">用來定義裁剪方塊遮罩界限的編輯模式。</span><span class="sxs-lookup"><span data-stu-id="c9679-169">Edit modes for defining the clipping box masking boundaries.</span></span> <span data-ttu-id="c9679-170">' Auto ' 會自動使用分頁值。</span><span class="sxs-lookup"><span data-stu-id="c9679-170">'Auto' automatically uses pagination values.</span></span> <span data-ttu-id="c9679-171">「手動」可直接操作裁剪 box 物件。</span><span class="sxs-lookup"><span data-stu-id="c9679-171">'Manual' enables direct manipulation of the clipping box object.</span></span> |
| <span data-ttu-id="c9679-172">碰撞編輯模式</span><span class="sxs-lookup"><span data-stu-id="c9679-172">Collider edit mode</span></span>          | <span data-ttu-id="c9679-173">編輯模式，用於定義捲軸互動碰撞條界限。</span><span class="sxs-lookup"><span data-stu-id="c9679-173">Edit modes for defining the scroll interaction collider boundaries.</span></span> <span data-ttu-id="c9679-174">' Auto ' 會自動使用分頁值。</span><span class="sxs-lookup"><span data-stu-id="c9679-174">'Auto' automatically uses pagination values.</span></span> <span data-ttu-id="c9679-175">「手動」可直接操作碰撞。</span><span class="sxs-lookup"><span data-stu-id="c9679-175">'Manual' enables direct manipulation of the collider.</span></span>     |
| <span data-ttu-id="c9679-176">可滾動</span><span class="sxs-lookup"><span data-stu-id="c9679-176">Can scroll</span></span>                  | <span data-ttu-id="c9679-177">啟用/停用近乎/遠的互動的滾動。</span><span class="sxs-lookup"><span data-stu-id="c9679-177">Enables/disables scrolling with near/far interaction.</span></span>                                                                                                                      |
| <span data-ttu-id="c9679-178">在預先呈現時使用</span><span class="sxs-lookup"><span data-stu-id="c9679-178">Use on pre render</span></span>           | <span data-ttu-id="c9679-179">切換 scrollingObjectCollection 是否會使用相機 OnPreRender 事件來管理內容可見度。</span><span class="sxs-lookup"><span data-stu-id="c9679-179">Toggles whether the scrollingObjectCollection will use the Camera OnPreRender event to manage content visibility.</span></span>                                                          |
| <span data-ttu-id="c9679-180">分頁曲線</span><span class="sxs-lookup"><span data-stu-id="c9679-180">Pagination curve</span></span>            | <span data-ttu-id="c9679-181">分頁的動畫曲線。</span><span class="sxs-lookup"><span data-stu-id="c9679-181">Animation curve for pagination.</span></span>                                                                                                                                            |
| <span data-ttu-id="c9679-182">動畫長度</span><span class="sxs-lookup"><span data-stu-id="c9679-182">Animation length</span></span>            | <span data-ttu-id="c9679-183">PaginationCurve 進行評估所需的時間長度，以秒為) 單位 (。</span><span class="sxs-lookup"><span data-stu-id="c9679-183">The amount of time (in seconds) the PaginationCurve will take to evaluate.</span></span>                                                                                                 |
| <span data-ttu-id="c9679-184">手動差異滾動閾值</span><span class="sxs-lookup"><span data-stu-id="c9679-184">Hand delta scroll threshold</span></span> | <span data-ttu-id="c9679-185">目前指標的距離（以計量為單位）可以在觸發捲軸拖曳之前沿著捲軸方向移動。</span><span class="sxs-lookup"><span data-stu-id="c9679-185">The distance, in meters, the current pointer can travel along the scroll direction before triggering a scroll drag.</span></span>                                                        |
| <span data-ttu-id="c9679-186">前端觸控距離</span><span class="sxs-lookup"><span data-stu-id="c9679-186">Front touch distance</span></span>        | <span data-ttu-id="c9679-187">距離（以量為單位），用來確認在捲軸的前方是否已開始觸控互動的本機 xy 平面。</span><span class="sxs-lookup"><span data-stu-id="c9679-187">Distance, in meters, to position a local xy plane used to verify if a touch interaction started in the front of the scroll view.</span></span>                                           |
| <span data-ttu-id="c9679-188">釋放閾值</span><span class="sxs-lookup"><span data-stu-id="c9679-188">Release threshold</span></span>           | <span data-ttu-id="c9679-189">從所需的捲軸範圍，收回從觸控到已發行的轉換所需的提款量（單位為計量）。</span><span class="sxs-lookup"><span data-stu-id="c9679-189">Withdraw amount, in meters, from the scroll boundaries needed to transition from touch engaged to released.</span></span>                                                                |

| <span data-ttu-id="c9679-190">速度</span><span class="sxs-lookup"><span data-stu-id="c9679-190">Velocity</span></span>            | <span data-ttu-id="c9679-191">描述</span><span class="sxs-lookup"><span data-stu-id="c9679-191">Description</span></span>                                                                                                 |
| ------------------- | ----------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="c9679-192">速度的類型</span><span class="sxs-lookup"><span data-stu-id="c9679-192">Type of velocity</span></span>    | <span data-ttu-id="c9679-193">所需的捲軸速度衰減類型。</span><span class="sxs-lookup"><span data-stu-id="c9679-193">The desired type of velocity falloff for the scroller.</span></span>                                                      |
| <span data-ttu-id="c9679-194">速度乘數</span><span class="sxs-lookup"><span data-stu-id="c9679-194">Velocity multiplier</span></span> | <span data-ttu-id="c9679-195">要套用到捲軸的 (額外) 速度。</span><span class="sxs-lookup"><span data-stu-id="c9679-195">Amount of (extra) velocity to be applied to scroller.</span></span>                                                       |
| <span data-ttu-id="c9679-196">速度 dampen</span><span class="sxs-lookup"><span data-stu-id="c9679-196">Velocity dampen</span></span>     | <span data-ttu-id="c9679-197">套用至速度的衰減量。</span><span class="sxs-lookup"><span data-stu-id="c9679-197">Amount of falloff applied to the velocity.</span></span>                                                                  |
| <span data-ttu-id="c9679-198">彈跳乘數</span><span class="sxs-lookup"><span data-stu-id="c9679-198">Bounce multiplier</span></span>   | <span data-ttu-id="c9679-199">乘數，以在使用每個畫面的衰減或每個專案的衰減時，將更多彈跳新增至清單的 overscroll。</span><span class="sxs-lookup"><span data-stu-id="c9679-199">Multiplier to add more bounce to the overscroll of a list when using falloff per frame or falloff per item.</span></span> |

| <span data-ttu-id="c9679-200">Debug 選項</span><span class="sxs-lookup"><span data-stu-id="c9679-200">Debug options</span></span>         | <span data-ttu-id="c9679-201">描述</span><span class="sxs-lookup"><span data-stu-id="c9679-201">Description</span></span>                                                                                                 |
| --------------------- | ----------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="c9679-202">遮罩已啟用</span><span class="sxs-lookup"><span data-stu-id="c9679-202">Mask enabled</span></span>          | <span data-ttu-id="c9679-203">捲軸內容的可見度模式。</span><span class="sxs-lookup"><span data-stu-id="c9679-203">Visibility mode of scroll content.</span></span> <span data-ttu-id="c9679-204">預設值會遮罩捲軸可見區域以外的所有物件。</span><span class="sxs-lookup"><span data-stu-id="c9679-204">Default value will mask all objects outside of the scroll viewable area.</span></span> |
| <span data-ttu-id="c9679-205">顯示臨界值平面</span><span class="sxs-lookup"><span data-stu-id="c9679-205">Show threshold planes</span></span> | <span data-ttu-id="c9679-206">若為 true，則編輯器會在捲軸界限周圍轉譯觸控釋放閾值的平面。</span><span class="sxs-lookup"><span data-stu-id="c9679-206">If true, the editor will render the touch release threshold planes around the scroll boundaries.</span></span>            |
| <span data-ttu-id="c9679-207">調試分頁</span><span class="sxs-lookup"><span data-stu-id="c9679-207">Debug pagination</span></span>      | <span data-ttu-id="c9679-208">使用這個區段可在執行時間時，對捲軸分頁進行調試。</span><span class="sxs-lookup"><span data-stu-id="c9679-208">Use this section to debug the scroll pagination during runtime.</span></span>                                             |

| <span data-ttu-id="c9679-209">事件</span><span class="sxs-lookup"><span data-stu-id="c9679-209">Events</span></span>              | <span data-ttu-id="c9679-210">描述</span><span class="sxs-lookup"><span data-stu-id="c9679-210">Description</span></span>                                                                                                                   |
| ------------------- | ----------------------------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="c9679-211">按一下時</span><span class="sxs-lookup"><span data-stu-id="c9679-211">On click</span></span>            | <span data-ttu-id="c9679-212">當捲軸背景碰撞或其任何互動式內容收到點擊時，即會觸發。</span><span class="sxs-lookup"><span data-stu-id="c9679-212">Triggered when the scroll background collider or any of its interactive content receives a click.</span></span>                             |
| <span data-ttu-id="c9679-213">開始觸控時</span><span class="sxs-lookup"><span data-stu-id="c9679-213">On touch started</span></span>    | <span data-ttu-id="c9679-214">當滾動背景碰撞項或其任何互動式內容收到接近互動觸控時觸發。</span><span class="sxs-lookup"><span data-stu-id="c9679-214">Triggered when the scroll background collider or any of its interactive content receives a near interaction touch.</span></span>            |
| <span data-ttu-id="c9679-215">在觸控結束時</span><span class="sxs-lookup"><span data-stu-id="c9679-215">On touch ended</span></span>      | <span data-ttu-id="c9679-216">當接近互動指標跨越發行閾值平面時，會觸發作用中觸控互動。</span><span class="sxs-lookup"><span data-stu-id="c9679-216">Triggered when an active touch interaction is terminated when the near interaction pointer crosses a release threshold plane.</span></span> |
| <span data-ttu-id="c9679-217">開始使用時</span><span class="sxs-lookup"><span data-stu-id="c9679-217">On momentum started</span></span> | <span data-ttu-id="c9679-218">當滾動容器以互動、速度衰減或分頁開始移動時觸發。</span><span class="sxs-lookup"><span data-stu-id="c9679-218">Triggered when the scroll container starts moving by interaction, velocity falloff, or pagination.</span></span>                            |
| <span data-ttu-id="c9679-219">動力已結束</span><span class="sxs-lookup"><span data-stu-id="c9679-219">On momentum ended</span></span>   | <span data-ttu-id="c9679-220">當捲軸容器停止互動、速度衰減或分頁時，就會觸發。</span><span class="sxs-lookup"><span data-stu-id="c9679-220">Triggered when the scroll container stops moving by interaction, velocity falloff, or pagination.</span></span>                             |

## <a name="scrolling-example-scene"></a><span data-ttu-id="c9679-221">滾動範例場景</span><span class="sxs-lookup"><span data-stu-id="c9679-221">Scrolling example scene</span></span>

<span data-ttu-id="c9679-222">**ScrollingObjectCollection** 範例場景是由3個可滾動的範例所組成，每一個都有不同的速度衰減設定。</span><span class="sxs-lookup"><span data-stu-id="c9679-222">**ScrollingObjectCollection.unity** example scene consists of 3 scrollable examples, each one with a different velocity falloff configuration.</span></span> <span data-ttu-id="c9679-223">範例場景包含牆壁，以顯示階層中依預設停用的表面放置行為。</span><span class="sxs-lookup"><span data-stu-id="c9679-223">The example scene contains walls to show the surface placement behavior that are disabled by default in the hierarchy.</span></span> <span data-ttu-id="c9679-224">範例場景可以在資料夾下找到 ``MRTK/Examples/Demos/ScrollingObjectCollection/Scenes`` 。</span><span class="sxs-lookup"><span data-stu-id="c9679-224">The example scene can be found under the ``MRTK/Examples/Demos/ScrollingObjectCollection/Scenes`` folder.</span></span>

![滾動物件集合範例場景](../images/scrolling-collection/ScrollingObjectCollection_ExampleScene.png)

## <a name="scrolling-example-prefabs"></a><span data-ttu-id="c9679-226">滾動範例 prefabs</span><span class="sxs-lookup"><span data-stu-id="c9679-226">Scrolling example prefabs</span></span>

<span data-ttu-id="c9679-227">為了方便起見，您可以使用兩個滾動物件集合 prefabs。</span><span class="sxs-lookup"><span data-stu-id="c9679-227">For convenience, two scrolling object collection prefabs are available to use.</span></span> <span data-ttu-id="c9679-228">您可以在資料夾下找到範例 prefabs ``MRTK/Examples/Demos/ScrollingObjectCollection/Prefabs`` 。</span><span class="sxs-lookup"><span data-stu-id="c9679-228">The example prefabs can be found under the ``MRTK/Examples/Demos/ScrollingObjectCollection/Prefabs`` folder.</span></span>

![滾動物件集合 prefabs](../images/scrolling-collection/ScrollingObjectCollection_Prefabs.png)

## <a name="see-also"></a><span data-ttu-id="c9679-230">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c9679-230">See also</span></span>

* [<span data-ttu-id="c9679-231">裁剪基本</span><span class="sxs-lookup"><span data-stu-id="c9679-231">Clipping Primitive</span></span>](../rendering/clipping-primitive.md)
* [<span data-ttu-id="c9679-232">材質實例</span><span class="sxs-lookup"><span data-stu-id="c9679-232">Material Instance</span></span>](../rendering/material-instance.md)
* [<span data-ttu-id="c9679-233">標準著色器</span><span class="sxs-lookup"><span data-stu-id="c9679-233">Standard Shader</span></span>](../rendering/MRTK-standard-shader.md)
* [<span data-ttu-id="c9679-234">物件集合</span><span class="sxs-lookup"><span data-stu-id="c9679-234">Object collection</span></span>](object-collection.md)
