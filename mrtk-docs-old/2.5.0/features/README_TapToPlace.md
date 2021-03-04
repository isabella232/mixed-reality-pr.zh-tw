---
title: README_TapToPlace
description: TapToPlace MRTK 的檔
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、點下
ms.openlocfilehash: 6a8ac4a5f65f25ffaea690733847e9e720fef294
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/03/2021
ms.locfileid: "101781054"
---
# <a name="tap-to-place"></a>點一下以放置

![TapToPlace](Images/Solver/TapToPlace/TapToPlaceIntroGif.gif)

點一下，就是用來將遊戲物件放在表面上的最互動元件。 此元件適用于將物件放在空間網格上。 點一下以使用兩個按鍵的組合，並使用前端移動來放置物件。 按一下以開始放置、前端移動以控制物件的位置，然後按一下以將物件放在場景中。

## <a name="using-tap-to-place"></a>使用攻點放置

1. 設定場景
    - 建立新的 unity 場景
    - 流覽至 **混合現實工具** 組  >  **新增至場景並設定**，以將 MRTK 新增至場景
    > [!NOTE]
    > 點擊以放置 MRTK 輸入系統所驅動的使用方式，但您也可以在不按下的情況下控制它，請參閱下面的點一下來放置程式碼可配置的部分。
    - 將 cube 新增至場景，並將比例變更為0.2，並將位置變更為 (0、0、0.7) 。
1. 使用碰撞器將 [點選連結至](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.TapToPlace) 遊戲物件

    ![TapToPlaceInspector](Images/Solver/TapToPlace/TapToPlaceInspector2.png)

    - 當加入 [點選] 元件時，也會附加一個「規劃求解」處理常式。 從需要規劃求解處理常式的 [求解](README_Solver.md) 器類別中，按一下以放置衍生的。 點一下放置物件的位置是相對於 `TrackedTargetType` 求解器處理常式內的計算。 依預設，標頭會是，也就是 `TrackedTargetType` 當標頭移動時，如果已選取該物件，就會遵循該物件。  `TrackedTargetType`也可以設定為控制器光線，並將物件跟隨在控制器上。 用來放置偵測器的第一個屬性群組是常見的 [求解器屬性](README_Solver.md#common-solver-properties)。  
    > [!IMPORTANT]
    > 點一下放置是獨立的規劃，不能與其他解析器連結。 它無法連結，因為 SolverHandler. UpdateSolvers 是用來在放置物件的位置時更新物件的位置。
    - 點擊以放置屬性：
        - `Auto Start`：若為 true，則點一下放置規劃求解將開始控制要放置遊戲物件的位置。 物件將會立即開始遵循 TrackedTargetType (Head 或 Controller 光線) 。 在叫用開始 () 之前必須先修改此值，才能產生任何作用。
        - `Default Placement Distance`：) 物件的預設距離 (，會相對於 SolverHandler 中的 TrackedTargetType 向前放置。 如果 raycast 未叫用介面，則遊戲物件將會放在預設的放置距離。
        - `Max Raycast Distance`： Raycast 的最大距離 (計量) 以 ' TrackedTargetType ' 的原點為基礎。 此 raycast 會尋找用來放置所選物件的介面。
        - `UseDefaultSurfaceNormalOffset`：此屬性預設為 true，可確保放置的物件會在介面上對齊。 如果這個屬性為 true，則會套用預設介面的一般位移，而不是針對屬性指定的任何值 `SurfaceNormalOffset` 。 如果為 false，則會套用的值 `SurfaceNormalOffset` 。 預設介面正常位移是沿著 Z 軸的碰撞器範圍。
        - `Surface Normal Offset`：當 raycast 碰到介面時，要放置的遊戲物件中心與表面法線的表面之間的距離。 如果為 false，則這個屬性只會套用至物件 `UseDefaultSurfaceNormalOffset` 。
        - `Keep Orientation Vertical`：若為 true，要放置的遊戲物件將保持垂直，且與 Vector3 對齊。
        - `Rotate According to Surface`：若為 false，要放置的遊戲物件不會根據介面點擊變更其旋轉。  當 IsBeingPlaced 為 true 時，物件將會繼續面對相機。
        - `Magnetic Surfaces`：要從最高到最低優先順序執行的 LayerMasks 陣列。 提供 raycast 點擊的第一層遮罩將用於位置計算。
        - `Debug Enabled`：如果為 true 且在 Unity 編輯器中，則會以黃色繪製 raycast 點擊的標準。 當為 true 時，[啟用偵錯工具] 會很有用， `RotateAccordingToSurface` 因為它會繪製介面點擊的一般視覺效果，以視覺方式說明物件是以其目前方向設定的原因。
        - `On Placing Started`：當選取要放置的遊戲物件時，就會觸發此事件一次。
        - `On Placing Stopped`：當要放置的遊戲物件未選取時，就會觸發此事件一次。

1. 測試點擊以在編輯器中放置行為
    - 按下 [播放] 並按住空格鍵以顯示輸入模擬手。
    - 將手移至立方體焦點為止，然後按一下滑鼠左鍵，模擬具有輸入模擬手的點擊。
        - 如果場景中沒有 colliders，則物件會 `TrackedTargetType` 在已定義的上遵循 `Default Placement Distance` 。
    - 物件將會遵循 `TrackedTargetType` 選取範圍之後的移動。 若要在編輯器中模擬 head 移動，請按 WASD 鍵。 按一下並按住滑鼠右鍵，以變更頭部旋轉。
    - 若要停止放置物件，請再按一次。  不需要將焦點放在「停用」點點按一下的物件。 只有開始放置程式的初始按一下才需要焦點。

    `TrackedTargetType`： Head (預設)  |  `TrackedTargetType`：控制器光線
    :-------------------------:|:-------------------------:
    ![TapToPlaceInputSimulationHead](Images/Solver/TapToPlace/TapToPlaceInputSimulationHead.gif)  |  ![TapToPlaceInputSimulationControllerRay](Images/Solver/TapToPlace/TapToPlaceInputSimulationControllerRay.gif)

## <a name="tap-to-place-code-configurability"></a>點擊以放置程式碼可配置

點擊以放置物件選取時間，也可以透過來控制 `StartPlacement()` ， `StopPlacement()` 而不需要按下事件。 這項功能適用于撰寫測試，並提供替代方法，在不使用 MRTK 輸入系統的情況下，將物件放在編輯器中。

1. 建立空的遊戲物件
1. 建立下列範例腳本，並將其附加至空白的遊戲物件

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

1. 在 [播放] 模式中，按 *U 鍵* 開始放置 cube
1. 按 *I 鍵* 以停止放置

## <a name="tap-to-place-example-scene"></a>點擊以放置範例場景

點擊放置範例場景包含4個可放置的物件，每個都有不同的設定。 範例場景包含牆壁，以顯示階層中依預設停用的表面放置行為。 您可以在 [ [發行] 頁面](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases)上找到範例場景範例中的 MixedReality。 場景位置是： *MRTK。範例/示範/解析器/場景/TapToPlaceExample unity*

![TapToPlaceExampleScene](Images/Solver/TapToPlace/TapToPlaceExampleScene.gif)

## <a name="see-also"></a>另請參閱

- [解算器](README_Solver.md)
- [空間感知](SpatialAwareness/SpatialAwarenessGettingStarted.md)
- [輸入模擬](InputSimulation/InputSimulationService.md)
- [手動追蹤](Input/HandTracking.md)
- [目光](Input/Gaze.md)
