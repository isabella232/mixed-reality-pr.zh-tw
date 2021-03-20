---
title: TapToPlace
description: TapToPlace MRTK 的檔
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、點下
ms.openlocfilehash: d41c5f77be31a7479e6706c0a5c5994708ac4f7c
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104689568"
---
# <a name="tap-to-place"></a><span data-ttu-id="1f60b-104">點一下以放置</span><span class="sxs-lookup"><span data-stu-id="1f60b-104">Tap to Place</span></span>

![TapToPlace 簡介](../../images/solver/tap-to-place/TapToPlaceIntroGif.gif)

<span data-ttu-id="1f60b-106">點一下，就是用來將遊戲物件放在表面上的最互動元件。</span><span class="sxs-lookup"><span data-stu-id="1f60b-106">Tap to Place is a far interaction component that is used to place a game object on surface.</span></span> <span data-ttu-id="1f60b-107">此元件適用于將物件放在空間網格上。</span><span class="sxs-lookup"><span data-stu-id="1f60b-107">This component is useful for placing objects on a spatial mesh.</span></span> <span data-ttu-id="1f60b-108">點一下以使用兩個按鍵的組合，並使用前端移動來放置物件。</span><span class="sxs-lookup"><span data-stu-id="1f60b-108">Tap to Place uses a combination of two clicks and head movement to place an object.</span></span> <span data-ttu-id="1f60b-109">按一下以開始放置、前端移動以控制物件的位置，然後按一下以將物件放在場景中。</span><span class="sxs-lookup"><span data-stu-id="1f60b-109">A click to start the placement, head movement to control the position of the object and a click to place the object in the scene.</span></span>

## <a name="using-tap-to-place"></a><span data-ttu-id="1f60b-110">使用攻點放置</span><span class="sxs-lookup"><span data-stu-id="1f60b-110">Using Tap to Place</span></span>

1. <span data-ttu-id="1f60b-111">設定場景</span><span class="sxs-lookup"><span data-stu-id="1f60b-111">Set up the scene</span></span>
    - <span data-ttu-id="1f60b-112">建立新的 unity 場景</span><span class="sxs-lookup"><span data-stu-id="1f60b-112">Create a new unity scene</span></span>
    - <span data-ttu-id="1f60b-113">流覽至 **混合現實工具** 組  >  **新增至場景並設定**，以將 MRTK 新增至場景</span><span class="sxs-lookup"><span data-stu-id="1f60b-113">Add MRTK to the scene by navigating to the **Mixed Reality Toolkit** > **Add to Scene and Configure**</span></span>
    > [!NOTE]
    > <span data-ttu-id="1f60b-114">點擊以放置 MRTK 輸入系統所驅動的使用方式，但您也可以在不按下的情況下控制它，請參閱下面的點一下來放置程式碼可配置的部分。</span><span class="sxs-lookup"><span data-stu-id="1f60b-114">Tap to Place uses clicks driven by the MRTK Input System but it can also be controlled without clicks, see the Tap To Place Code Configurability section below.</span></span>
    - <span data-ttu-id="1f60b-115">將 cube 新增至場景，並將比例變更為0.2，並將位置變更為 (0、0、0.7) 。</span><span class="sxs-lookup"><span data-stu-id="1f60b-115">Add a cube to the scene and change the scale to 0.2 and change the position to (0, 0, 0.7).</span></span>
1. <span data-ttu-id="1f60b-116">使用碰撞器將 [點選連結至](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.TapToPlace) 遊戲物件</span><span class="sxs-lookup"><span data-stu-id="1f60b-116">Attach [Tap to Place](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.TapToPlace) to a game object with a collider</span></span>

    ![TapToPlaceInspector](../../images/solver/tap-to-place/TapToPlaceInspector2.png)

    - <span data-ttu-id="1f60b-118">當加入 [點選] 元件時，也會附加一個「規劃求解」處理常式。</span><span class="sxs-lookup"><span data-stu-id="1f60b-118">When the Tap to Place component is added, a Solver Handler will also be attached.</span></span> <span data-ttu-id="1f60b-119">從需要規劃求解處理常式的 [求解](Solver.md) 器類別中，按一下以放置衍生的。</span><span class="sxs-lookup"><span data-stu-id="1f60b-119">Tap to Place derives from the [Solver](Solver.md) class which requires a Solver Handler.</span></span> <span data-ttu-id="1f60b-120">點一下放置物件的位置是相對於 `TrackedTargetType` 求解器處理常式內的計算。</span><span class="sxs-lookup"><span data-stu-id="1f60b-120">The position of a Tap to Place object is calculated relative to the `TrackedTargetType` within the Solver Handler.</span></span> <span data-ttu-id="1f60b-121">依預設，標頭會是，也就是 `TrackedTargetType` 當標頭移動時，如果已選取該物件，就會遵循該物件。</span><span class="sxs-lookup"><span data-stu-id="1f60b-121">By default the Head is the `TrackedTargetType`, i.e. when the head moves, the object follows if it is selected.</span></span>  <span data-ttu-id="1f60b-122">`TrackedTargetType`也可以設定為控制器光線，並將物件跟隨在控制器上。</span><span class="sxs-lookup"><span data-stu-id="1f60b-122">The `TrackedTargetType` can also be set to Controller Ray which has the object follow the controller.</span></span> <span data-ttu-id="1f60b-123">用來放置偵測器的第一個屬性群組是常見的 [求解器屬性](Solver.md#common-solver-properties)。</span><span class="sxs-lookup"><span data-stu-id="1f60b-123">The first group of properties in the Tap to Place inspector are the [Common Solver Properties](Solver.md#common-solver-properties).</span></span>  
    > [!IMPORTANT]
    > <span data-ttu-id="1f60b-124">點一下放置是獨立的規劃，不能與其他解析器連結。</span><span class="sxs-lookup"><span data-stu-id="1f60b-124">Tap to Place is a stand alone Solver and cannot be chained with other Solvers.</span></span> <span data-ttu-id="1f60b-125">它無法連結，因為 SolverHandler. UpdateSolvers 是用來在放置物件的位置時更新物件的位置。</span><span class="sxs-lookup"><span data-stu-id="1f60b-125">It cannot be chained because SolverHandler.UpdateSolvers is used to update the object's position while it is being placed.</span></span>
    - <span data-ttu-id="1f60b-126">點擊以放置屬性：</span><span class="sxs-lookup"><span data-stu-id="1f60b-126">Tap to Place Properties:</span></span>
        - <span data-ttu-id="1f60b-127">`Auto Start`：若為 true，則點一下放置規劃求解將開始控制要放置遊戲物件的位置。</span><span class="sxs-lookup"><span data-stu-id="1f60b-127">`Auto Start`: If true, the Tap to Place solver will start out controlling the position of the game object to be placed.</span></span> <span data-ttu-id="1f60b-128">物件將會立即開始遵循 TrackedTargetType (Head 或 Controller 光線) 。</span><span class="sxs-lookup"><span data-stu-id="1f60b-128">The object will immediately start following the TrackedTargetType (Head or Controller Ray).</span></span> <span data-ttu-id="1f60b-129">在叫用開始 () 之前必須先修改此值，才能產生任何作用。</span><span class="sxs-lookup"><span data-stu-id="1f60b-129">This value must be modified before Start() is invoked in order to have any effect.</span></span>
        - <span data-ttu-id="1f60b-130">`Default Placement Distance`：) 物件的預設距離 (，會相對於 SolverHandler 中的 TrackedTargetType 向前放置。</span><span class="sxs-lookup"><span data-stu-id="1f60b-130">`Default Placement Distance`: The default distance (in meters) an object will be placed relative to the TrackedTargetType forward in the SolverHandler.</span></span> <span data-ttu-id="1f60b-131">如果 raycast 未叫用介面，則遊戲物件將會放在預設的放置距離。</span><span class="sxs-lookup"><span data-stu-id="1f60b-131">The game object will be placed at the default placement distance if a surface is not hit by the raycast.</span></span>
        - <span data-ttu-id="1f60b-132">`Max Raycast Distance`： Raycast 的最大距離 (計量) 以 ' TrackedTargetType ' 的原點為基礎。</span><span class="sxs-lookup"><span data-stu-id="1f60b-132">`Max Raycast Distance`: The max distance (meters) for the raycast based on the 'TrackedTargetType' origin.</span></span> <span data-ttu-id="1f60b-133">此 raycast 會尋找用來放置所選物件的介面。</span><span class="sxs-lookup"><span data-stu-id="1f60b-133">This raycast looks for a surface to place a selected object.</span></span>
        - <span data-ttu-id="1f60b-134">`UseDefaultSurfaceNormalOffset`：此屬性預設為 true，可確保放置的物件會在介面上對齊。</span><span class="sxs-lookup"><span data-stu-id="1f60b-134">`UseDefaultSurfaceNormalOffset`: This property is true by default, it ensures the object being placed is aligned on a surface.</span></span> <span data-ttu-id="1f60b-135">如果這個屬性為 true，則會套用預設介面的一般位移，而不是針對屬性指定的任何值 `SurfaceNormalOffset` 。</span><span class="sxs-lookup"><span data-stu-id="1f60b-135">If this property is true, the default surface normal offset will be applied instead of any value specified for the `SurfaceNormalOffset` property.</span></span> <span data-ttu-id="1f60b-136">如果為 false，則會套用的值 `SurfaceNormalOffset` 。</span><span class="sxs-lookup"><span data-stu-id="1f60b-136">If false, the value for `SurfaceNormalOffset` will be applied.</span></span> <span data-ttu-id="1f60b-137">預設介面正常位移是沿著 Z 軸的碰撞器範圍。</span><span class="sxs-lookup"><span data-stu-id="1f60b-137">The default surface normal offset is the collider's extents along the z axis.</span></span>
        - <span data-ttu-id="1f60b-138">`Surface Normal Offset`：當 raycast 碰到介面時，要放置的遊戲物件中心與表面法線的表面之間的距離。</span><span class="sxs-lookup"><span data-stu-id="1f60b-138">`Surface Normal Offset`: The distance between the center of the game object to place and a surface along the surface normal, if the raycast hits a surface.</span></span> <span data-ttu-id="1f60b-139">如果為 false，則這個屬性只會套用至物件 `UseDefaultSurfaceNormalOffset` 。</span><span class="sxs-lookup"><span data-stu-id="1f60b-139">This property is only applied to an object if `UseDefaultSurfaceNormalOffset` is false.</span></span>
        - <span data-ttu-id="1f60b-140">`Keep Orientation Vertical`：若為 true，要放置的遊戲物件將保持垂直，且與 Vector3 對齊。</span><span class="sxs-lookup"><span data-stu-id="1f60b-140">`Keep Orientation Vertical`: If true, the game object to place will remain upright and in line with Vector3.up.</span></span>
        - <span data-ttu-id="1f60b-141">`Rotate According to Surface`：若為 false，要放置的遊戲物件不會根據介面點擊變更其旋轉。</span><span class="sxs-lookup"><span data-stu-id="1f60b-141">`Rotate According to Surface`: If false, the game object to place will not change its rotation according to the surface hit.</span></span>  <span data-ttu-id="1f60b-142">當 IsBeingPlaced 為 true 時，物件將會繼續面對相機。</span><span class="sxs-lookup"><span data-stu-id="1f60b-142">The object will remain facing the camera while IsBeingPlaced is true.</span></span>
        - <span data-ttu-id="1f60b-143">`Magnetic Surfaces`：要從最高到最低優先順序執行的 LayerMasks 陣列。</span><span class="sxs-lookup"><span data-stu-id="1f60b-143">`Magnetic Surfaces`: An array of LayerMasks to execute from highest to lowest priority.</span></span> <span data-ttu-id="1f60b-144">提供 raycast 點擊的第一層遮罩將用於位置計算。</span><span class="sxs-lookup"><span data-stu-id="1f60b-144">First layer mask to provide a raycast hit will be used for position calculations.</span></span>
        - <span data-ttu-id="1f60b-145">`Debug Enabled`：如果為 true 且在 Unity 編輯器中，則會以黃色繪製 raycast 點擊的標準。</span><span class="sxs-lookup"><span data-stu-id="1f60b-145">`Debug Enabled`: If true and in the Unity Editor, the normal of the raycast hit will be drawn in yellow.</span></span> <span data-ttu-id="1f60b-146">當為 true 時，[啟用偵錯工具] 會很有用， `RotateAccordingToSurface` 因為它會繪製介面點擊的一般視覺效果，以視覺方式說明物件是以其目前方向設定的原因。</span><span class="sxs-lookup"><span data-stu-id="1f60b-146">Debug enabled is useful when `RotateAccordingToSurface` is true because it draws the normal of the surface hit which visually explains why the object is set at its current orientation.</span></span>
        - <span data-ttu-id="1f60b-147">`On Placing Started`：當選取要放置的遊戲物件時，就會觸發此事件一次。</span><span class="sxs-lookup"><span data-stu-id="1f60b-147">`On Placing Started`: This event is triggered once when the game object to place is selected.</span></span>
        - <span data-ttu-id="1f60b-148">`On Placing Stopped`：當要放置的遊戲物件未選取時，就會觸發此事件一次。</span><span class="sxs-lookup"><span data-stu-id="1f60b-148">`On Placing Stopped`: This event is triggered once when the game object to place is unselected, placed.</span></span>

1. <span data-ttu-id="1f60b-149">測試點擊以在編輯器中放置行為</span><span class="sxs-lookup"><span data-stu-id="1f60b-149">Testing Tap to Place behavior in editor</span></span>
    - <span data-ttu-id="1f60b-150">按下 [播放] 並按住空格鍵以顯示輸入模擬手。</span><span class="sxs-lookup"><span data-stu-id="1f60b-150">Press play and hold the space bar to show an input simulation hand.</span></span>
    - <span data-ttu-id="1f60b-151">將手移至立方體焦點為止，然後按一下滑鼠左鍵，模擬具有輸入模擬手的點擊。</span><span class="sxs-lookup"><span data-stu-id="1f60b-151">Move the hand until the cube is in focus and simulate a click with the input simulation hand by clicking with the left mouse.</span></span>
        - <span data-ttu-id="1f60b-152">如果場景中沒有 colliders，則物件會 `TrackedTargetType` 在已定義的上遵循 `Default Placement Distance` 。</span><span class="sxs-lookup"><span data-stu-id="1f60b-152">If colliders are not present in the scene, the object will follow the `TrackedTargetType` at the defined `Default Placement Distance`.</span></span>
    - <span data-ttu-id="1f60b-153">物件將會遵循 `TrackedTargetType` 選取範圍之後的移動。</span><span class="sxs-lookup"><span data-stu-id="1f60b-153">The object will follow the movement of the `TrackedTargetType` after selection.</span></span> <span data-ttu-id="1f60b-154">若要在編輯器中模擬 head 移動，請按 WASD 鍵。</span><span class="sxs-lookup"><span data-stu-id="1f60b-154">To simulate head movement in editor, press the WASD keys.</span></span> <span data-ttu-id="1f60b-155">按一下並按住滑鼠右鍵，以變更頭部旋轉。</span><span class="sxs-lookup"><span data-stu-id="1f60b-155">Change head rotation by clicking and holding the right mouse.</span></span>
    - <span data-ttu-id="1f60b-156">若要停止放置物件，請再按一次。</span><span class="sxs-lookup"><span data-stu-id="1f60b-156">To stop placing the object, click again.</span></span>  <span data-ttu-id="1f60b-157">不需要將焦點放在「停用」點點按一下的物件。</span><span class="sxs-lookup"><span data-stu-id="1f60b-157">The object does not need to be in focus for the stop placement click.</span></span> <span data-ttu-id="1f60b-158">只有開始放置程式的初始按一下才需要焦點。</span><span class="sxs-lookup"><span data-stu-id="1f60b-158">Focus is only required for the initial click that starts the placement process.</span></span>

    <span data-ttu-id="1f60b-159">`TrackedTargetType`： Head (預設) </span><span class="sxs-lookup"><span data-stu-id="1f60b-159">`TrackedTargetType`: Head (Default)</span></span> |  <span data-ttu-id="1f60b-160">`TrackedTargetType`：控制器光線</span><span class="sxs-lookup"><span data-stu-id="1f60b-160">`TrackedTargetType`: Controller Ray</span></span>
    :-------------------------:|:-------------------------:
    ![TapToPlace 輸入模擬 Head 1](../../images/solver/tap-to-place/TapToPlaceInputSimulationHead.gif)  |  ![TapToPlace InputSimulation 控制器光線](../../images/solver/tap-to-place/TapToPlaceInputSimulationControllerRay.gif)

## <a name="tap-to-place-code-configurability"></a><span data-ttu-id="1f60b-163">點擊以放置程式碼可配置</span><span class="sxs-lookup"><span data-stu-id="1f60b-163">Tap to Place Code Configurability</span></span>

<span data-ttu-id="1f60b-164">點擊以放置物件選取時間，也可以透過來控制 `StartPlacement()` ， `StopPlacement()` 而不需要按下事件。</span><span class="sxs-lookup"><span data-stu-id="1f60b-164">Tap to Place object selection timing can also be controlled via `StartPlacement()` and `StopPlacement()` instead of requiring a click event.</span></span> <span data-ttu-id="1f60b-165">這項功能適用于撰寫測試，並提供替代方法，在不使用 MRTK 輸入系統的情況下，將物件放在編輯器中。</span><span class="sxs-lookup"><span data-stu-id="1f60b-165">This capability is useful for writing tests and provides an alternative method to place an object in editor without using the MRTK Input System.</span></span>

1. <span data-ttu-id="1f60b-166">建立空的遊戲物件</span><span class="sxs-lookup"><span data-stu-id="1f60b-166">Create an empty game object</span></span>
1. <span data-ttu-id="1f60b-167">建立下列範例腳本，並將其附加至空白的遊戲物件</span><span class="sxs-lookup"><span data-stu-id="1f60b-167">Create and attach the following example script to the empty game object</span></span>

    ```c#
    using UnityEngine;
    using Microsoft.MixedReality.Toolkit.Utilities.Solvers;

    public class TapToPlaceInputExample : MonoBehaviour
    {
        private GameObject cube;
        private TapToPlace tapToPlace;

        void Start()
        {
            cube = GameObject.CreatePrimitive(PrimitiveType.Cube);
            cube.transform.localScale = Vector3.one * 0.2f;
            cube.transform.position = Vector3.forward * 0.7f;

            tapToPlace = cube.AddComponent<TapToPlace>();
        }

        void Update()
        {
            if (Input.GetKeyDown(KeyCode.U))
            {
                tapToPlace.StartPlacement();
            }
            if (Input.GetKeyDown(KeyCode.I))
            {
                tapToPlace.StopPlacement();
            }
        }
    }
    ```

1. <span data-ttu-id="1f60b-168">在 [播放] 模式中，按 *U 鍵* 開始放置 cube</span><span class="sxs-lookup"><span data-stu-id="1f60b-168">In play mode, press the *U key* to start placing the cube</span></span>
1. <span data-ttu-id="1f60b-169">按 *I 鍵* 以停止放置</span><span class="sxs-lookup"><span data-stu-id="1f60b-169">Press the *I key* to stop the placement</span></span>

## <a name="tap-to-place-example-scene"></a><span data-ttu-id="1f60b-170">點擊以放置範例場景</span><span class="sxs-lookup"><span data-stu-id="1f60b-170">Tap to Place Example Scene</span></span>

<span data-ttu-id="1f60b-171">點擊放置範例場景包含4個可放置的物件，每個都有不同的設定。</span><span class="sxs-lookup"><span data-stu-id="1f60b-171">The Tap to Place example scene consists of 4 placeable objects, each with a different configuration.</span></span> <span data-ttu-id="1f60b-172">範例場景包含牆壁，以顯示階層中依預設停用的表面放置行為。</span><span class="sxs-lookup"><span data-stu-id="1f60b-172">The example scene contains walls to show the surface placement behavior that are disabled by default in the hierarchy.</span></span> <span data-ttu-id="1f60b-173">您可以在 [ [發行] 頁面](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases)上找到範例場景範例中的 MixedReality。</span><span class="sxs-lookup"><span data-stu-id="1f60b-173">The example scene can be found in the Microsoft.MixedReality.Toolkit.Unity.Examples unity package found on the [Release Page](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases).</span></span> <span data-ttu-id="1f60b-174">場景位置是： *MRTK。範例/示範/解析器/場景/TapToPlaceExample unity*</span><span class="sxs-lookup"><span data-stu-id="1f60b-174">The scene location is: *MRTK.Examples/Demos/Solvers/Scenes/TapToPlaceExample.unity*</span></span>

![TapToPlace 範例場景1](../../images/solver/tap-to-place/TapToPlaceExampleScene.gif)

## <a name="see-also"></a><span data-ttu-id="1f60b-176">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1f60b-176">See also</span></span>

- [<span data-ttu-id="1f60b-177">解算器</span><span class="sxs-lookup"><span data-stu-id="1f60b-177">Solvers</span></span>](Solver.md)
- [<span data-ttu-id="1f60b-178">空間感知</span><span class="sxs-lookup"><span data-stu-id="1f60b-178">Spatial Awareness</span></span>](../../spatial-awareness/SpatialAwarenessGettingStarted.md)
- [<span data-ttu-id="1f60b-179">輸入模擬</span><span class="sxs-lookup"><span data-stu-id="1f60b-179">Input Simulation</span></span>](../../input-simulation/InputSimulationService.md)
- [<span data-ttu-id="1f60b-180">手動追蹤</span><span class="sxs-lookup"><span data-stu-id="1f60b-180">Hand Tracking</span></span>](../../input/HandTracking.md)
- [<span data-ttu-id="1f60b-181">目光</span><span class="sxs-lookup"><span data-stu-id="1f60b-181">Gaze</span></span>](../../input/Gaze.md)
