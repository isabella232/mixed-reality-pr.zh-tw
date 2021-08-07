---
title: 案例研究-擴充 HoloLens 的空間對應功能
description: 當您建立第一個 Microsoft HoloLens 的應用程式時，我們會積極地查看我們可以在裝置上推送空間對應界限的程度。
author: jevertt
ms.author: jemccull
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality、HoloLens、空間對應
ms.openlocfilehash: f0438990c39570f9188e2e150a8cbe7907d72f7e2be260c72e41646565b8d89e
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2021
ms.locfileid: "115210438"
---
# <a name="case-study---expanding-the-spatial-mapping-capabilities-of-hololens"></a>案例研究-擴充 HoloLens 的空間對應功能

當您建立第一個 Microsoft HoloLens 的應用程式時，我們會積極地查看我們可以在裝置上推送空間對應界限的程度。 Microsoft 工作室的軟體工程師 Jeff Evertt，將說明如何開發新技術，而不需要更充分掌控在使用者的真實世界環境中如何放置全息影像。

> [!NOTE]
> HoloLens 2 可實現新的[場景理解運行](../design/scene-understanding.md)時間，為混合的現實開發人員提供結構化、高階環境的標記法，其設計目的是為了讓環保感知應用程式的開發變得直覺。 

## <a name="watch-the-video"></a>觀賞影片

>[!VIDEO https://www.youtube.com/embed/iUmTi3_Ynus]

## <a name="beyond-spatial-mapping"></a>超越空間對應

雖然我們正在處理[片段](https://www.microsoft.com/p/fragments/9nblggh5ggm8)和[年輕 Conker](https://www.microsoft.com/p/young-conker/9nblggh5ggk1)，HoloLens 的第兩個遊戲中，我們發現當我們在實體世界中進行程式化的程式放置時，我們需要更高層級的瞭解使用者環境。 每個遊戲都有自己的特定放置需求：在片段中，我們想要能夠區分不同的表面（例如樓層或資料表），以在相關位置放置線索。 我們也想要能夠找出生活大小的全像是沙發或椅子的表面。 在年輕 Conker 中，我們希望 Conker 和他的對手能夠在玩家的房間內，以平臺的形式使用引發的表面。

[Asobo 工作室](https://www.asobostudio.com/index.html)是這些遊戲的開發合作夥伴，面對這個問題，並建立了擴充 HoloLens 空間對應功能的技術。 您可以使用這種方式來分析玩家的房間，並找出牆、表格、椅子和地面等表面。 它也讓我們能夠針對一組條件約束進行優化，以判斷全像攝影物件的最佳位置。

## <a name="the-spatial-understanding-code"></a>空間理解程式碼

我們採用 Asobo 的原始程式碼，並建立了封裝這項技術的程式庫。 Microsoft 與 Asobo 現已開放原始碼，並可在 [MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialMapping) 上使用，以供您在自己的專案中使用。 包含所有原始程式碼，可讓您依據需求進行自訂，並與您的小組分享您的改進。 C + + 規劃的程式碼已包裝成 UWP DLL，並使用 [MixedRealityToolkit 中包含的拖放預製專案](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/SpatialUnderstanding)向 Unity 公開。

Unity 範例中包含許多有用的查詢，可讓您在牆上尋找空白空間、將物件放在最上方，或放在地面的大型空間、找出要放置的字元位置，以及許多其他空間理解查詢。

雖然 HoloLens 所提供的空間對應解決方案設計成足以滿足整個問題空間的需求，但空間的理解模組是為了支援兩個特定遊戲的需要而設計的。 因此，其解決方案是以特定程式和假設集為結構：
* **固定大小 playspace**：使用者指定 init 呼叫中最大的 playspace 大小。
* 單次 **掃描程式**：此程式需要一段獨立的掃描階段，讓使用者四處進行，定義 playspace。 查詢函式在完成掃描之前將無法運作。
* **使用者導向 playspace 「繪製**」：在掃描階段期間，使用者會四處移動和尋找 playspace，以有效地繪製應該包含的區域。 產生的網格很重要，可在此階段提供使用者意見反應。
* **室內家用或 office 設定**：查詢函式是以適當角度的平面和牆為中心設計的。 這是一項軟性限制。 不過，在掃描階段期間，主要軸分析已完成，可將網格鑲嵌沿著主要和次要軸優化。

### <a name="room-scanning-process"></a>會議室掃描流程

當您載入空間理解模組時，您要做的第一件事就是掃描您的空間，以便找出並標示所有可用的表面（例如樓層、上限和牆）。 在掃描過程中，您可以查看您的房間，並「繪製」掃描中應包含的區域。

在這個階段中看到的網格是一項很重要的視覺意見反應，可讓使用者知道即將掃描的房間部分。 空間理解模組的 DLL 會在內部將 playspace 儲存為8cm 大小體素 cube 的方格。 在掃描的初始部分期間，主要元件分析完成以判斷房間的座標軸。 就內部而言，它會儲存其體素空間與這些軸對齊。 從體素磁片區解壓縮 isosurface，大約每秒會產生一個網狀。

![白色的空間對應網格，並瞭解綠色的 playspace 網格](images/spatial-mapping-500px.png)

白色的空間對應網格，並瞭解綠色的 playspace 網格



內含的 SpatialUnderstanding .cs 檔案會管理掃描階段程式。 它會呼叫下列函數：
* **SpatialUnderstanding_Init**：在一開始就呼叫一次。
* **GeneratePlayspace_InitScan**：表示掃描階段應開始。
* **GeneratePlayspace_UpdateScan_DynamicScan**：呼叫每個畫面格，以更新掃描程式。 相機位置和方向會傳入，並用於 playspace 繪製程式（如上所述）。
* **GeneratePlayspace_RequestFinish**：呼叫以結束 playspace。 這會使用掃描階段期間「繪製」的區域來定義和鎖定 playspace。 應用程式可以在掃描階段查詢統計資料，以及查詢自訂網格以提供使用者意見反應。
* **Import_UnderstandingMesh**：在掃描期間，模組所提供並放置於 [瞭解] 預製專案的 **SpatialUnderstandingCustomMesh** 行為，會定期查詢處理常式所產生的自訂網格。 此外，也會在完成掃描之後再完成一次。

**SpatialUnderstanding** 行為所驅動的掃描流程會呼叫 **InitScan**，然後 **UpdateScan** 每個畫面格。 當統計資料查詢報告合理的涵蓋範圍時，使用者可以 airtap 呼叫 **RequestFinish** 來指出掃描階段結束。 **UpdateScan** 會繼續呼叫，直到它的傳回值指出 DLL 已完成處理。

## <a name="the-queries"></a>查詢

掃描完成後，您將能夠在介面中存取三種不同類型的查詢：
* **拓撲查詢**：這些是以掃描的房間拓撲為基礎的快速查詢。
* **圖形查詢**：這些查詢會利用拓撲查詢的結果，來尋找與您所定義的自訂圖形很相符的水準表面。
* **物件放置查詢**：這些是更複雜的查詢，可根據一組規則和物件的條件約束，找出最適合的位置。

除了三個主要查詢以外，還有一個 raycasting 介面可用來取出標記的介面類別型，而且可以複製自訂的防水室網格。

### <a name="topology-queries"></a>拓撲查詢

在 DLL 內，拓撲管理員會處理環境的標籤。 如上所述，大部分的資料會儲存在 surfels 中，並包含在體素磁片區中。 此外， **PlaySpaceInfos** 結構是用來儲存有關 playspace 的資訊，包括世界上的對齊 (更多有關以下) 、樓層和上限高度的詳細資料。

啟發學習法可用來決定樓層、上限和牆。 例如，具有大於1個 m2 介面區的最大和最低水準介面會被視為樓層。 請注意，此程式也會使用掃描程式期間的相機路徑。

拓撲管理員公開的查詢子集會透過 DLL 公開。 公開的拓撲查詢如下所示：
* QueryTopology_FindPositionsOnWalls
* QueryTopology_FindLargePositionsOnWalls
* QueryTopology_FindLargestWall
* QueryTopology_FindPositionsOnFloor
* QueryTopology_FindLargestPositionsOnFloor
* QueryTopology_FindPositionsSittable

每個查詢都有一組參數，特定于查詢類型。 在下列範例中，使用者會指定所需磁片區的最小高度 & 寬度、地面上方的最小放置高度，以及磁片區前方的最小間隙量。 所有度量都是計量。




```
EXTERN_C __declspec(dllexport) int QueryTopology_FindPositionsOnWalls(
          _In_ float minHeightOfWallSpace,
          _In_ float minWidthOfWallSpace,
          _In_ float minHeightAboveFloor,
          _In_ float minFacingClearance,
          _In_ int locationCount,
          _Inout_ Dll_Interface::TopologyResult* locationData)
```

這些查詢都採用預先配置的 **TopologyResult** 結構陣列。 **LocationCount** 參數會指定傳入陣列的長度。 傳回值會回報傳回位置的數目。 此數位絕不會大於傳入的 **locationCount** 參數。

**TopologyResult** 包含傳回之磁片區的中心位置、面向方向 (例如正常) ，以及所找到空間的維度。




```
struct TopologyResult
     {
          DirectX::XMFLOAT3 position;
          DirectX::XMFLOAT3 normal;
          float width;
          float length;
     };
```

請注意，在 Unity 範例中，每個查詢都會連結到虛擬 UI 面板中的按鈕。 此範例會將每個查詢的參數設為合理的值。 如需更多範例，請參閱範例程式碼中的 *SpaceVisualizer。*

### <a name="shape-queries"></a>圖形查詢

在 DLL 內，圖形分析器 (**ShapeAnalyzer_W**) 會使用拓撲分析器來比對使用者所定義的自訂圖形。 Unity 範例中有一組預先定義的圖形，會顯示在 [查詢] 功能表的 [圖形] 索引標籤上。

請注意，圖形分析僅適用于水準表面。 例如，一名沙發是由平面基座介面和沙發的一般頂端所定義。 圖形查詢會尋找特定大小、高度和外觀範圍的兩個表面，並將兩個表面對齊並連接。 使用 Api 術語時，沙發基座和沙發背面是圖形元件，而對齊需求則是圖形元件條件約束。

在 Unity 範例 () **ShapeDefinition** 中定義的範例查詢，"sittable" 物件如下所示：




```
shapeComponents = new List<ShapeComponent>()
     {
          new ShapeComponent(
               new List<ShapeComponentConstraint>()
               {
                    ShapeComponentConstraint.Create_SurfaceHeight_Between(0.2f, 0.6f),
                    ShapeComponentConstraint.Create_SurfaceCount_Min(1),
                    ShapeComponentConstraint.Create_SurfaceArea_Min(0.035f),
               }),
     };
     AddShape("Sittable", shapeComponents);
```

每個圖形查詢都是由一組圖形元件所定義，每個都有一組元件條件約束，以及一組可列出元件之間相依性的圖形條件約束。 此範例包含單一元件定義中的三個條件約束，而且元件之間沒有任何形狀條件約束 (因為只有一個元件) 。

相反地，「沙發」圖形有兩個圖形元件和四個「形狀」條件約束。 請注意，在此範例中，元件會以其在使用者元件清單中的索引來識別 (0 和 1) 。




```
shapeConstraints = new List<ShapeConstraint>()
        {
              ShapeConstraint.Create_RectanglesSameLength(0, 1, 0.6f),
              ShapeConstraint.Create_RectanglesParallel(0, 1),
              ShapeConstraint.Create_RectanglesAligned(0, 1, 0.3f),
              ShapeConstraint.Create_AtBackOf(1, 0),
        };
```

Unity 模組中提供包裝函式，可讓您輕鬆地建立自訂圖形定義。 您可以在 **ShapeComponentConstraint** 和 **ShapeConstraint** 結構內的 **SpatialUnderstandingDll** 中找到元件和圖形條件約束的完整清單。

![藍色矩形會反白顯示「椅子圖形」查詢的結果。](images/chair-shape-query-500px.png)

藍色矩形會反白顯示「椅子圖形」查詢的結果。



### <a name="object-placement-solver"></a>物件放置規劃求解

物件放置查詢可以用來識別實體房間中的理想位置，以放置您的物件。 在指定物件規則和條件約束的情況下，規劃求解會尋找最適合的位置。 此外，物件查詢會持續存在，直到使用 **Solver_RemoveObject** 或 **Solver_RemoveAllObjects** 呼叫來移除物件為止，以允許受限制的多重物件放置。

物件放置查詢包含三個部分：具有參數的放置類型、規則清單和條件約束清單。 若要執行查詢，請使用下列 API：




```
public static int Solver_PlaceObject(
                [In] string objectName,
                [In] IntPtr placementDefinition,    // ObjectPlacementDefinition
                [In] int placementRuleCount,
                [In] IntPtr placementRules,         // ObjectPlacementRule
                [In] int constraintCount,
                [In] IntPtr placementConstraints,   // ObjectPlacementConstraint
                [Out] IntPtr placementResult)
```
此函式會接受物件名稱、位置定義，以及規則和條件約束的清單。 C # 包裝函式提供了結構協助程式函式，讓規則和條件約束結構更容易。 放置定義包含查詢類型，也就是下列其中一項：




```
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

每個放置類型都有一組唯一類型的參數。 **ObjectPlacementDefinition** 結構包含一組靜態 helper 函式，用來建立這些定義。 例如，若要尋找將物件放在樓層的位置，您可以使用下列函數： 


```
public static ObjectPlacementDefinition Create_OnFloor(Vector3 halfDims)
```

除了放置類型之外，您還可以提供一組規則和條件約束。 無法違反規則。 接著，滿足型別和規則的可能放置位置會針對一組條件約束進行優化，以選取最佳放置位置。 每個規則和條件約束都可以透過提供的靜態建立函式來建立。 以下提供範例規則和條件約束結構函數。




```
public static ObjectPlacementRule Create_AwayFromPosition(
                    Vector3 position, float minDistance)
               public static ObjectPlacementConstraint Create_NearPoint(
                    Vector3 position, float minDistance = 0.0f, float maxDistance = 0.0f)
```

以下的物件放置查詢正在尋找在介面邊緣放置半計量立方體的位置，而不是其他先前放置的物件和靠近房間的中心。




```
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

如果成功，則會傳回包含放置位置、維度和方向的 **ObjectPlacementResult** 結構。 此外，會將放置新增至 DLL 的已放置物件的內部清單。 後續的放置查詢會將此物件列入考慮。 Unity 範例中的 **LevelSolver .cs** 檔案包含更多範例查詢。

![藍色方塊會顯示三個位置查詢的結果，其中包含「離開相機位置」規則。](images/away-from-camera-position-500px.png)

藍色方塊會顯示三個位置查詢的結果，其中包含「離開相機位置」規則。


**祕訣：**
* 當您針對層級或應用程式案例所需的多個物件進行放置位置的解決時，請先解決不可或缺和大型物件，以最大化找出空間的可能性。
* 放置順序很重要。 如果找不到物件放置，請嘗試較不受限制的設定。 擁有一組恢復設定對於跨許多房間設定支援功能非常重要。

### <a name="ray-casting"></a>光線轉換

除了三個主要的查詢之外，還可以使用光線轉型介面來取出標記的表面型別，而且可以在掃描和結束空間之後，將自訂的防水 playspace 網格複製出，並在內部針對圖層、上限和牆壁等表面產生標籤。 **PlayspaceRaycast** 函式會使用光線，並在光線與已知表面衝突時傳回，如果是，則會以 **RaycastResult** 的形式呈現該介面的相關資訊。 


```
struct RaycastResult
     {
          enum SurfaceTypes
          {
               Invalid, // No intersection
               Other,
               Floor,
               FloorLike,         // Not part of the floor topology, 
                                  //     but close to the floor and looks like the floor
               Platform,          // Horizontal platform between the ground and 
                                  //     the ceiling
               Ceiling,
               WallExternal,
               WallLike,          // Not part of the external wall surface, 
                                  //     but vertical surface that looks like a 
                                  //    wall structure
               };
               SurfaceTypes SurfaceType;
               float SurfaceArea;   // Zero if unknown 
                                        //  (i.e. if not part of the topology analysis)
               DirectX::XMFLOAT3 IntersectPoint;
               DirectX::XMFLOAT3 IntersectNormal;
     };
```

就內部而言，raycast 是針對 playspace 的計算8cm 立方體素表示來計算。 每個體素都包含一組介面元素，其中包含已處理的拓撲資料 (也稱為 surfels) 。 會比較交集體素資料格內所含的 surfels，以及用來查閱拓撲資訊的最佳相符項。 此拓撲資料包含以 **SurfaceTypes** 列舉的形式傳回的標籤，以及交集資料表面的介面區。

在 Unity 範例中，資料指標會將光線轉換成每個畫面格。 首先，針對 Unity 的 colliders;第二，針對瞭解模組的世界標記法;最後，針對 UI 元素。 在此應用程式中，UI 會取得優先順序，然後是瞭解結果，最後是 Unity 的 colliders。 **SurfaceType** 會回報為數據指標旁的文字。

![Raycast 與 floor 的結果報告交集。](images/raycast-result-500px.jpg)

Raycast 與 floor 的結果報告交集。


## <a name="get-the-code"></a>取得程式碼

開放原始碼程式碼可在 [MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity)中取得。 如果您在專案中使用程式碼，請讓我們知道[HoloLens 開發人員論壇](https://forums.hololens.com/)。 我們無法等候看看您的做法！

## <a name="about-the-author"></a>關於作者

<table style="border:0;width:800px">
<tr>
<td style="border:0"> <img alt="Jeff Evertt, Software Engineering Lead at Microsoft" width="200" height="205" src="images/jeff-evertt-200px.jpg" /></td><td style="border:0"> <b>Jeff Evertt</b>是一項軟體工程組長，從 incubation 到經驗的早期，一直以來都在 HoloLens。 在 HoloLens 之前，他在各式各樣的平臺和遊戲中，在 Xbox Kinect 和遊戲產業中工作。 Jeff 熱衷於著機器人、圖形，以及亮色燈發出嗶聲的東西。 他喜歡學習新事物和處理軟體、硬體，特別是在兩者交集的空間中。</td>
</tr>
</table>



## <a name="see-also"></a>另請參閱
* [空間對應](../design/spatial-mapping.md)
* [場景理解](../design/scene-understanding.md)
* [空間位置掃描視覺效果](../design/room-scan-visualization.md)
* [MixedRealityToolkit-Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)
* [Asobo Studio： HoloLens 開發 frontline 的課程](https://www.gamesindustry.biz/articles/2016-05-12-asobo-lessons-from-the-frontline-of-ar-development)
