---
title: Unity 中的空間對應
description: 瞭解如何在 Unity 混合現實應用程式中，使用及管理與您有關的真實世界幾何呈現和衝突。
author: davidkline-ms
ms.author: davidkl
ms.date: 03/21/2018
ms.topic: article
keywords: Unity、空間對應、轉譯器、碰撞器、網格、掃描、元件、混合現實耳機、windows mixed reality 耳機、虛擬實境耳機、MRTK、混合現實工具組
ms.openlocfilehash: 62e4c4fad725dbe58773035b0bb47f1911098217
ms.sourcegitcommit: 191c3d89c034714377d09fa91c07cbaa81301bae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/13/2021
ms.locfileid: "121905700"
---
# <a name="spatial-mapping-in-unity"></a>Unity 中的空間對應

[空間對應](../../design/spatial-mapping.md)可讓您取得代表 HoloLens 裝置周圍世界表面的三角形網格。 您可以使用 surface 資料進行放置、遮蔽和房間分析，讓您的 Unity 專案有額外的深度劑量。

Unity 包含空間對應的完整支援，可透過下列方式公開給開發人員：

1. MixedRealityToolkit 中提供的空間對應元件，可為開始使用空間對應提供便利快速的路徑
2. 較低層級的空間對應 Api，可提供完整控制權，並啟用更精密的應用程式特定自訂

若要在您的應用程式中使用空間對應，必須在 Package.appxmanifest 中設定 >spatialperception 功能。

## <a name="device-support"></a>裝置支援

| 功能 | [HoloLens (第一代) ](/hololens/hololens1-hardware) | [HoloLens 2](/hololens/hololens2-hardware) | [沉浸式頭戴裝置](../../discover/immersive-headset-hardware-details.md) |
| ---- | ---- | ---- | ---- |
| 空間對應 | ✔️ | ✔️ | ❌ |

## <a name="setting-the-spatialperception-capability"></a>設定 >spatialperception 功能

為了讓應用程式使用空間對應資料，必須啟用 >spatialperception 功能。

如何啟用 >spatialperception 功能：

1. 在 Unity 編輯器中，開啟 [**播放設定**] 窗格 (編輯 > Project 設定 > 播放機) 
2. 在 [ **Windows 存放區**] 索引標籤上選取
3. 展開 [**發行設定]** ，並檢查 [**功能]** 清單中的 [ **>spatialperception]** 功能

> [!NOTE]
> 如果您已將 Unity 專案匯出至 Visual Studio 的解決方案，您必須匯出至新資料夾，或在[Visual Studio 的 package.appxmanifest 中手動設定這項功能](../native/spatial-mapping-in-directx.md#set-up-your-app-to-use-the-spatialperception-capability)。

空間對應也需要至少10.0.10586.0 的 MaxVersionTested：

1. 在 Visual Studio 中，以滑鼠右鍵按一下方案總管中的 **package.appxmanifest** ，然後選取 [ **View Code** ]
2. 找出指定 **y** 的行，並將 **MaxVersionTested = "10.0.10240.0"** 變更為 **MaxVersionTested = "10.0.10586.0"**
3. **儲存** package.appxmanifest。

## <a name="how-to-add-mapping-in-unity"></a>如何在 Unity 中新增對應

[!INCLUDE[](includes/unity-spatial-mapping.md)]

## <a name="higher-level-mesh-analysis-spatial-understanding"></a>更高層級的網狀分析：空間理解

> [!CAUTION]
> 空間理解已淘汰，以促進 [場景理解](../../design/scene-understanding.md)。

<a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a>是以 Unity 的全像內嵌式 api 為基礎進行全像開發的公用程式程式碼集合。

### <a name="spatial-understanding"></a>空間理解

在實體世界中放置全像影像時，通常會想要超越空間對應的網格和表面平面。 當放置完成 cti 時，需要較高層級的環境理解。 這通常需要做出有關樓層、上限和牆壁的決策。 您也可以針對一組放置條件約束進行優化，以決定全像攝影物件的最佳實體位置。

在開發年輕 Conker 和片段的期間，Asobo 工作室藉由開發會議室規劃求解來面對這個問題。 這些遊戲都有遊戲專屬的需求，但它們共用了核心空間的理解技術。 HoloToolkit. SpatialUnderstanding 程式庫會封裝這項技術，可讓您快速找出牆上的空格、將物件放在最上方、找出放置的字元，以及許多其他空間理解查詢。

所有原始程式碼都包含在內，可讓您依據需求進行自訂，並與您的小組分享您的改進。 C + + 規劃的程式碼已經包裝成 UWP dll，並使用 MixedRealityToolkit 中包含的預製專案來公開給 Unity。

### <a name="understanding-modules"></a>瞭解模組

模組會公開三個主要介面：適用于簡單介面和空間查詢的拓撲、物件偵測的圖形，以及物件放置規劃求解的物件集合之條件約束的位置。 以下說明上述各方式。 除了三個主要模組介面外，還可以使用光線轉型介面來取出標記的介面類別型，而且可以將自訂的防水 playspace 網格複製出來。

### <a name="ray-casting"></a>光線轉換

當房間掃描完成之後，就會在內部產生標籤，例如樓層、上限和牆。 此函式 `PlayspaceRaycast` 會使用光線，並在光線與已知表面衝突時傳回，如果是，則會傳回該介面的相關資訊（以形式表示） `RaycastResult` 。

```cpp
struct RaycastResult
{
    enum SurfaceTypes
    {
        Invalid,    // No intersection
        Other,
        Floor,
        FloorLike,  // Not part of the floor topology,
                    //  but close to the floor and looks like the floor
        Platform,   // Horizontal platform between the ground and
                    //  the ceiling
        Ceiling,
        WallExternal,
        WallLike,   // Not part of the external wall surface,
                    //  but vertical surface that looks like a
                    //  wall structure
    };
    SurfaceTypes SurfaceType;
    float SurfaceArea;  // Zero if unknown
                        //  (i.e. if not part of the topology analysis)
    DirectX::XMFLOAT3 IntersectPoint;
    DirectX::XMFLOAT3 IntersectNormal;
};
```

就內部而言，raycast 是針對 playspace 的計算出的 8-cm 立方體素標記法來計算。 每個體素都包含一組介面元素，其中包含已處理的拓撲資料 (也稱為 surfels) 。 會比較交集體素資料格內所含的 surfels，以及用來查閱拓撲資訊的最佳相符項。 此拓撲資料包含以 "SurfaceTypes" 列舉的形式傳回的標籤，以及交集資料表面的介面區。

在 Unity 範例中，資料指標會將光線轉換成每個畫面格。 首先，針對 Unity 的 colliders。 第二，針對瞭解模組的世界標記法。 最後一個是 UI 元素。 在此應用程式中，UI 會獲得優先權、接下來的理解結果，最後是 Unity 的 colliders。 SurfaceType 會回報為數據指標旁的文字。

![介面類別型在游標旁邊標示](images/su-raycastresults-300px.jpg)<br>
*介面類別型在游標旁邊標示*

### <a name="topology-queries"></a>拓撲查詢

在 DLL 內，拓撲管理員會處理環境的標籤。 如上所述，大部分的資料會儲存在 surfels 中，並包含在體素磁片區中。 此外，還會使用 "PlaySpaceInfos" 結構來儲存有關 playspace 的資訊，包括世界上的對齊 (更多有關以下) 、樓層和最高高度的詳細資料。 啟發學習法可用來決定樓層、上限和牆。 例如，具有大於 1-m2 介面區的最大和最低水準介面會被視為樓層。

> [!NOTE]
> 掃描過程中的攝影機路徑也會在此程式中使用。

拓撲管理員公開的查詢子集會透過 dll 公開。 公開的拓撲查詢如下所示。

```cpp
QueryTopology_FindPositionsOnWalls
QueryTopology_FindLargePositionsOnWalls
QueryTopology_FindLargestWall
QueryTopology_FindPositionsOnFloor
QueryTopology_FindLargestPositionsOnFloor
QueryTopology_FindPositionsSittable
```

每個查詢都有一組參數，特定于查詢類型。 在下列範例中，使用者會指定所需磁片區的最小高度 & 寬度、地面上方的最小放置高度，以及磁片區前方的最小間隙量。 所有度量都是計量。

```cpp
EXTERN_C __declspec(dllexport) int QueryTopology_FindPositionsOnWalls(
    _In_ float minHeightOfWallSpace,
    _In_ float minWidthOfWallSpace,
    _In_ float minHeightAboveFloor,
    _In_ float minFacingClearance,
    _In_ int locationCount,
    _Inout_ Dll_Interface::TopologyResult* locationData)
```

這些查詢都採用預先配置的 "TopologyResult" 結構陣列。 "LocationCount" 參數指定傳入陣列的長度。 傳回值會回報傳回位置的數目。 此數位絕不會大於傳入的 "locationCount" 參數。

"TopologyResult" 包含傳回之磁片區的中心位置、面向方向 (例如正常) ，以及所找到空間的維度。

```cpp
struct TopologyResult
{
    DirectX::XMFLOAT3 position;
    DirectX::XMFLOAT3 normal;
    float width;
    float length;
};
```

> [!NOTE]
> 在 Unity 範例中，每個查詢都會連結到虛擬 UI 面板中的按鈕。 此範例會將每個查詢的參數設為合理的值。 如需更多範例，請參閱範例程式碼中的 SpaceVisualizer。

### <a name="shape-queries"></a>圖形查詢

在 dll 中，圖形分析器 ( "ShapeAnalyzer_W" ) 使用拓朴分析器來比對使用者所定義的自訂圖形。 Unity 範例會定義一組圖形，並透過 [圖形] 索引標籤中的應用程式內查詢功能表來公開結果。其目的是讓使用者可以定義自己的物件圖形查詢，並視其應用程式的需要來使用這些查詢。

圖形分析僅適用于水準表面。 例如，一名沙發是由平面基座介面和沙發的一般頂端所定義。 圖形查詢會尋找特定大小、高度和外觀範圍的兩個表面，並將兩個表面對齊並連接。 使用 Api 術語時，沙發基座和上一頁是圖形元件，而對齊需求是圖形元件條件約束。

在 Unity 範例 () ShapeDefinition 中定義的範例查詢，"sittable" 物件如下所示。

```cs
shapeComponents = new List<ShapeComponent>()
{
    new ShapeComponent(
        new List<ShapeComponentConstraint>()
        {
            ShapeComponentConstraint.Create_SurfaceHeight_Between(0.2f, 0.6f),
            ShapeComponentConstraint.Create_SurfaceCount_Min(1),
            ShapeComponentConstraint.Create_SurfaceArea_Min(0.035f),
        }
    ),
};
AddShape("Sittable", shapeComponents);
```

每個圖形查詢都是由一組圖形元件所定義，每個都有一組元件條件約束，以及一組列出元件之間相依性的圖形條件約束。 此範例包含單一元件定義中的三個條件約束，而且元件之間沒有任何形狀條件約束 (因為只有一個元件) 。

相反地，「沙發」圖形有兩個圖形元件和四個「形狀」條件約束。 元件是以使用者元件清單中的索引來識別， (0 和1在此範例中) 。

```cs
shapeConstraints = new List<ShapeConstraint>()
{
    ShapeConstraint.Create_RectanglesSameLength(0, 1, 0.6f),
    ShapeConstraint.Create_RectanglesParallel(0, 1),
    ShapeConstraint.Create_RectanglesAligned(0, 1, 0.3f),
    ShapeConstraint.Create_AtBackOf(1, 0),
};
```

Unity 模組中提供包裝函式，可讓您輕鬆地建立自訂圖形定義。 您可以在 "ShapeComponentConstraint" 和 "ShapeConstraint" 結構內的 "SpatialUnderstandingDll" 中找到元件和圖形條件約束的完整清單。

![在此表面找到矩形圖形](images/su-shapequery-300px.jpg)<br>
*在此表面找到矩形圖形*

### <a name="object-placement-solver"></a>物件放置規劃求解

物件放置規劃求解可以用來識別實體房間中的理想位置，以放置您的物件。 根據物件規則和條件約束，規劃求解會找出最適合的位置。 此外，物件查詢會持續存在，直到以「Solver_RemoveObject」或「Solver_RemoveAllObjects」呼叫來移除物件為止，並允許受限的多重物件放置。 物件放置查詢包含三個部分：具有參數的放置類型、規則清單和條件約束清單。 若要執行查詢，請使用下列 API。

```cpp
public static int Solver_PlaceObject(
            [In] string objectName,
            [In] IntPtr placementDefinition,        // ObjectPlacementDefinition
            [In] int placementRuleCount,
            [In] IntPtr placementRules,             // ObjectPlacementRule
            [In] int constraintCount,
            [In] IntPtr placementConstraints,       // ObjectPlacementConstraint
            [Out] IntPtr placementResult)
```

此函式會接受物件名稱、位置定義，以及規則和條件約束的清單。 C # 包裝函式提供了結構協助程式函式，讓規則和條件約束結構更容易。 放置定義包含查詢類型–也就是下列其中一項。

```cpp
public enum PlacementType
{
    Place_OnFloor,
    Place_OnWall,
    Place_OnCeiling,
    Place_OnShape,
    Place_OnEdge,
    Place_OnFloorAndCeiling,
    Place_RandomInAir,
    Place_InMidAir,
    Place_UnderFurnitureEdge,
};
```

每個放置類型都有一組唯一類型的參數。 "ObjectPlacementDefinition" 結構包含一組靜態 helper 函式，可用於建立這些定義。 例如，若要尋找將物件放在樓層的位置，您可以使用下列函數。 公用靜態 ObjectPlacementDefinition Create_OnFloor (Vector3) halfDims 除了放置類型以外，您也可以提供一組規則和條件約束。 無法違反規則。 接著，滿足型別和規則的可能放置位置會針對一組條件約束進行優化，以便選取最佳放置位置。 每個規則和條件約束都可以透過提供的靜態建立函式來建立。 以下提供範例規則和條件約束結構函數。

```cs
public static ObjectPlacementRule Create_AwayFromPosition(
    Vector3 position, float minDistance)
public static ObjectPlacementConstraint Create_NearPoint(
    Vector3 position, float minDistance = 0.0f, float maxDistance = 0.0f)
```

下列物件放置查詢正在尋找在介面邊緣放置半計量立方體的位置，而不是從其他先前放置的物件和靠近房間的中央。

```cs
List<ObjectPlacementRule> rules =
    new List<ObjectPlacementRule>() {
        ObjectPlacementRule.Create_AwayFromOtherObjects(1.0f),
    };

List<ObjectPlacementConstraint> constraints =
    new List<ObjectPlacementConstraint> {
        ObjectPlacementConstraint.Create_NearCenter(),
    };

Solver_PlaceObject(
    “MyCustomObject”,
    new ObjectPlacementDefinition.Create_OnEdge(
        new Vector3(0.25f, 0.25f, 0.25f),
        new Vector3(0.25f, 0.25f, 0.25f)),
    rules.Count,
    UnderstandingDLL.PinObject(rules.ToArray()),
    constraints.Count,
    UnderstandingDLL.PinObject(constraints.ToArray()),
    UnderstandingDLL.GetStaticObjectPlacementResultPtr());
```

如果成功，則會傳回包含放置位置、維度和方向的 "ObjectPlacementResult" 結構。 此外，會將放置新增至 dll 的已放置物件的內部清單。 後續的放置查詢會將此物件列入考慮。 Unity 範例中的 "LevelSolver .cs" 檔案包含更多範例查詢。

![物件放置的結果](images/su-objectplacement-1000px.jpg)<br>
*圖3：藍色方塊如何從三個位置查詢的結果，而不是相機位置規則*

當您針對層級或應用程式案例所需的多個物件進行放置位置的解決時，請先解決不可或缺和大型物件，以充分發揮可找到空間的機率。 放置順序很重要。 如果找不到物件放置，請嘗試較不受限制的設定。 擁有一組恢復設定對於跨許多房間設定支援功能非常重要。

### <a name="room-scanning-process"></a>會議室掃描流程

雖然 HoloLens 所提供的空間對應解決方案設計成足以滿足整個問題空間的需求，但空間的理解模組是為了支援兩個特定遊戲的需要而設計的。 它的解決方案是以特定程式和假設集為依據，如下所摘要。

```txt
Fixed size playspace – The user specifies the maximum playspace size in the init call.

One-time scan process –
    The process requires a discrete scanning phase where the user walks around,
    defining the playspace.
    Query functions will not function until after the scan has been finalized.
```

使用者導向 playspace 「繪製」–在掃描階段期間，使用者會四處移動並查看播放步調，有效地繪製應該包含的區域。 產生的網格很重要，可在此階段提供使用者意見反應。 室內家用或 office 設定–查詢函式是以適當角度的平面和牆為中心設計的。 這是一項軟性限制。 不過，在掃描階段期間，主要軸分析已完成，可將網格鑲嵌沿著主要和次要軸優化。 內含的 SpatialUnderstanding .cs 檔案會管理掃描階段程式。 它會呼叫下列函數。

```txt
SpatialUnderstanding_Init – Called once at the start.

GeneratePlayspace_InitScan – Indicates that the scan phase should begin.

GeneratePlayspace_UpdateScan_DynamicScan –
    Called each frame to update the scanning process. The camera position and
    orientation is passed in and is used for the playspace painting process,
    described above.

GeneratePlayspace_RequestFinish –
    Called to finalize the playspace. This will use the areas “painted” during
    the scan phase to define and lock the playspace. The application can query
    statistics during the scanning phase as well as query the custom mesh for
    providing user feedback.

Import_UnderstandingMesh –
    During scanning, the “SpatialUnderstandingCustomMesh” behavior provided by
    the module and placed on the understanding prefab will periodically query the
    custom mesh generated by the process. In addition, this is done once more
    after scanning has been finalized.
```

掃描流程（由 "SpatialUnderstanding" 行為驅動）會呼叫 InitScan，然後 UpdateScan 每個畫面格。 當統計資料查詢報告合理的涵蓋範圍時，使用者就可以 airtap 呼叫 RequestFinish 來指出掃描階段結束。 UpdateScan 會繼續呼叫，直到其傳回值指出 dll 已完成處理。

### <a name="understanding-mesh"></a>瞭解網格

瞭解 dll 會在內部將 playspace 儲存為 8 cm 大小體素 cube 的方格。 在掃描的初始部分期間，主要元件分析完成以判斷房間的座標軸。 就內部而言，它會儲存其體素空間與這些軸對齊。 從體素磁片區解壓縮 isosurface，大約每秒會產生一個網狀。

![從體素磁片區產生的網狀](images/su-custommesh.jpg)<br>
*從體素磁片區產生的網狀*

## <a name="troubleshooting"></a>疑難排解

* 確定您已設定 [>spatialperception](#setting-the-spatialperception-capability) 功能
* 當追蹤遺失時，下一個 OnSurfaceChanged 事件將會移除所有的網格。

## <a name="spatial-mapping-in-mixed-reality-toolkit"></a>混合現實工具組中的空間對應

如需有關搭配使用空間對應與混合現實工具組的詳細資訊，請參閱 MRTK 檔的 [空間感知一節](/windows/mixed-reality/mrtk-unity/features/spatial-awareness/spatial-awareness-getting-started) 。

## <a name="next-development-checkpoint"></a>下一個開發檢查點

如果您是遵循我們所配置的 Unity 開發旅程，您將會在探索 MRTK 核心構成要素的過程中進行。 接下來，您可以繼續進行下一個建置組塊：

> [!div class="nextstepaction"]
> [Text](text-in-unity.md)

或者，直接跳到混合實境平台功能和 API 的主題：

> [!div class="nextstepaction"]
> [共用體驗](shared-experiences-in-unity.md)

您可以隨時回到 [Unity 開發檢查點](unity-development-overview.md#2-core-building-blocks)。

## <a name="see-also"></a>另請參閱

* [座標系統](../../design/coordinate-systems.md)
* [Unity 中的座標系統](coordinate-systems-in-unity.md)
* <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a>
* <a href="https://docs.unity3d.com/ScriptReference/MeshFilter.html" target="_blank">UnityEngine. MeshFilter</a>
* <a href="https://docs.unity3d.com/ScriptReference/MeshCollider.html" target="_blank">UnityEngine. MeshCollider</a>
* <a href="https://docs.unity3d.com/ScriptReference/Bounds.html" target="_blank">UnityEngine</a>
