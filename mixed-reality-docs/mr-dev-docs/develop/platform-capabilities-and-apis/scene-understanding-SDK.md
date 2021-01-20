---
title: 場景理解 SDK
description: 瞭解如何安裝和使用場景理解 SDK，包括混合現實應用程式中的元件、網格和物件。
author: szymons
ms.author: szymons
ms.date: 12/14/2020
ms.topic: article
keywords: 場景理解、空間對應、Windows Mixed Reality、Unity
ms.openlocfilehash: 10cb96ffe0496a20c7244ba4c40dec097ebd4bd8
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583754"
---
# <a name="scene-understanding-sdk-overview"></a>場景理解 SDK 總覽

場景理解會轉換混合式現實裝置所捕捉的非結構化環境感應器資料，並將其轉換成強大的抽象標記法。 SDK 會作為應用程式與場景理解執行時間之間的通訊層。 其目的是要模擬現有的標準結構，例如3d 呈現的3D 場景圖形，以及2D 應用程式的2D 矩形和麵板。 雖然結構場景理解模擬會對應到具體的架構，但一般而言，SceneUnderstanding 是架構中立的，可讓與它互動的各種架構之間進行互通性。 隨著場景的理解，發展 SDK 的角色是為了確保新的表示和功能能持續在統一架構中公開。 在本檔中，我們會先介紹高階的概念，以協助您熟悉開發環境/使用方式，然後針對特定類別和結構提供更詳細的檔。

## <a name="where-do-i-get-the-sdk"></a>哪裡可以取得 SDK？

您可以透過 NuGet 下載 SceneUnderstanding SDK。

[SceneUnderstanding SDK](https://www.nuget.org/packages/Microsoft.MixedReality.SceneUnderstanding/)

**注意：** 最新版本取決於預覽套件，您將需要啟用發行前版本的套件才能看到它。

針對 0.5.2022 rc 和更新版本，場景理解支援 c # 和 c + + 的語言投影，讓應用程式開發 Win32 或 UWP 平臺的應用程式。 從這個版本開始，SceneUnderstanding 支援支援 unity 的編輯器支援，而禁止使用 SceneObserver，這僅用於與 HoloLens2 通訊。 

SceneUnderstanding 需要 Windows SDK 18362 版或更高版本。 

如果您是在 Unity 專案中使用 SDK，請使用 [適用于 unity 的 NuGet](https://github.com/GlitchEnzo/NuGetForUnity) 將套件安裝到您的專案中。

## <a name="conceptual-overview"></a>概觀說明

### <a name="the-scene"></a>場景

您的混合現實裝置會不斷地整合在您的環境中所看到內容的相關資訊。 場景理解會漏斗圖所有的資料來源，並產生單一的緊密抽象概念。 場景理解會產生場景，也就是代表單一事物之實例的 [SceneObjects](scene-understanding-SDK.md#sceneobjects) 組合， (例如牆壁/上限/樓層。 ) 場景物件本身是 [SceneComponents 的組合，代表組成此 SceneObject 的更細微部分。 元件的範例包括四邊形和網格，但未來可能代表周框方塊、衝突網格、中繼資料等。

將未經處理的感應器資料轉換為場景的程式，可能會花費幾秒鐘的中等空間 (~ 10x10m) 到數分鐘的空間 (~ 50x50m) ，因此不會由沒有應用程式要求的裝置所計算的內容。 相反地，您的應用程式會視需要觸發場景產生。 SceneObserver 類別具有可計算或還原序列化場景的靜態方法，您可以接著列舉/與其互動。 「計算」動作會依需求執行，並在 CPU 上執行，但在混合現實驅動程式)  (的個別進程中執行。 不過，當我們在另一個進程中進行計算時，產生的場景資料會儲存在您的應用程式中，並保留在場景物件中。 

以下圖表說明此程式流程，並顯示兩個應用程式與場景理解執行時間互動的範例。 

![處理圖表](images/SU-ProcessFlow.png)

左側是混合現實執行時間的圖表，它會在自己的進程中保持開啟並執行。 此執行時間負責執行裝置追蹤、空間對應，以及場景理解用來瞭解與世界周圍相關原因的其他作業。 在圖表的右側，我們會顯示兩個理論上的應用程式，利用場景理解。 第一個應用程式是使用 MRTK 的介面，它會在內部使用場景理解 SDK，第二個應用程式會計算並使用兩個不同的場景實例。 此圖表中的三個場景都會產生不同的場景實例，驅動程式不會追蹤在不同場景中的應用程式與場景物件之間共用的全域狀態。 場景理解確實提供了一段時間的追蹤機制，但這是使用 SDK 來完成的。 在應用程式的程式中，追蹤程式碼已經在 SDK 中執行。

因為每個場景會將它的資料儲存在您應用程式的記憶體空間中，所以您可以假設場景物件的所有功能或其內部資料一律會在應用程式的進程中執行。

### <a name="layout"></a>Layout

若要使用場景理解，瞭解並瞭解執行時間如何以邏輯和實際方式代表元件，可能會有價值。 場景代表具有特定版面配置的資料，並在維持 pliable 的基礎結構，而不需要進行重大修訂時，才會維持符合未來需求的基礎結構。 場景會藉由儲存所有元件， (一般清單中) 的所有場景物件的所有元件，並透過參考（特定元件參考其他元件）定義階層和組合。

以下範例顯示其平面和邏輯形式的結構範例。

<table>
<tr><th>邏輯版面配置</th><th>實體配置</th></tr>
<tr>
<td>
<ul>
  場景
  <ul>
  <li>SceneObject_1
    <ul>
      <li>SceneMesh_1</li>
      <li>SceneQuad_1</li>
      <li>SceneQuad_2</li>
    </ul>
  </li>
  <li>SceneObject_2
    <ul>
      <li>SceneQuad_1</li>
      <li>SceneQuad_3</li>
      </li></ul>
  </li>
  <li>SceneObject_3
    <ul>
      <li>SceneMesh_3</li>
    </ul>
  </ul>
</ul>
</td>
<td>
<ul>
  <li>SceneObject_1</li>
  <li>SceneObject_2</li>
  <li>SceneObject_3</li>
  <li>SceneQuad_1</li>
  <li>SceneQuad_2</li>
  <li>SceneQuad_3</li>
  <li>SceneMesh_1</li>
  <li>SceneMesh_2</li>
</ul>
</td>
</tr>
</table>

下圖強調場景的實體和邏輯配置之間的差異。 在左側，我們會看到您的應用程式在列舉場景時所看到的資料的階層式版面配置。 在右側，我們看到場景是由12個不同的元件所組成，視需要個別存取。 在處理新的場景時，我們預期應用程式會以邏輯方式來引導此階層，不過在場景更新之間進行追蹤時，有些應用程式可能只會對以兩種場景間共用的特定元件為目標感興趣。

## <a name="api-overview"></a>API 概觀

下一節提供場景理解中的結構高階總覽。 閱讀此區段可讓您瞭解幕後的呈現方式，以及各種元件的用途/用途。 下一節將提供具體的程式碼範例，以及在此總覽中說明 mda 的其他詳細資料。

以下所述的所有類型都位於 `Microsoft.MixedReality.SceneUnderstanding` 命名空間中。

### <a name="scenecomponents"></a>SceneComponents

現在您已瞭解幕後的邏輯配置，我們現在可以展示 SceneComponents 的概念，以及如何使用它們來撰寫階層。 SceneComponents 是 SceneUnderstanding 中最細微的分解，代表單一核心事物，例如網格或四或周框方塊。 SceneComponents 是可獨立更新，並且可由其他 SceneComponents 參考的專案，因此它們具有唯一識別碼的單一全域屬性，可允許這種類型的追蹤/參考機制。 識別碼會用於場景階層的邏輯組合以及物件持續性， (與另一個場景相關的更新動作。 )  

如果您要將每個新計算的場景視為相異，只要列舉其中的所有資料，則識別碼對您而言都很透明。 但是，如果您打算追蹤數個更新的元件，您將會使用這些識別碼來編制索引，並尋找場景物件之間的 SceneComponents。

### <a name="sceneobjects"></a>SceneObjects

SceneObject 是一種 SceneComponent，代表「事物」的實例，例如牆、樓層、頂棚等等。以其 Kind 屬性工作表示。 SceneObjects 是幾何，因此具有代表其在空間中位置的函式和屬性，但不包含任何幾何或邏輯結構。 相反地，SceneObjects 會參考其他 SceneComponents，特別是 SceneQuads 和 SceneMeshes，以提供系統所支援的各種不同標記法。 當計算新場景時，您的應用程式很可能會列舉場景的 SceneObjects 來處理其感興趣的內容。

SceneObjects 可以有下列任何一項：

<table>
<tr>
<th>SceneObjectKind</th> <th>描述</th>
</tr>
<tr><td>背景</td><td>已知 SceneObject <b>不</b> 是其他可辨識的場景物件類型之一。 此類別不應與未知的情況混淆，因為背景已知不是牆壁/樓層/上限等 .。。雖然不明尚未分類。</b></td></tr>
<tr><td>牆</td><td>實體牆。 牆會假設為 immovable 環境結構。</td></tr>
<tr><td>樓層</td><td>樓層是任何可進行引導的表面。 注意：階梯並非樓層。 另請注意，該樓層採用任何 walkable 介面，因此不會明確地假設單數地板。 多層結構、斜坡等 .。。全都分類為 floor。</td></tr>
<tr><td>Ceiling</td><td>房間的上方面。</td></tr>
<tr><td>平台</td><td>您可以用來放置全息圖的大型平面。 這些通常會代表資料表、countertops 和其他大型水準表面。</td></tr>
<tr><td>World</td><td>標記無關的幾何資料保留標籤。 藉由設定 EnableWorldMesh 更新旗標所產生的網格會分類為 world。</td></tr>
<tr><td>Unknown</td><td>這個場景物件尚未分類並指派給類型。 這應該不會與背景混淆，因為此物件可能是任何事情，因此系統還不會為它提供強大的分類。</td></tr>
</tr>
</table>

### <a name="scenemesh"></a>SceneMesh

SceneMesh 是一個 SceneComponent，使用三角形清單來近似任意幾何物件的幾何。 SceneMeshes 會在數個不同的內容中使用，它們可以代表防水資料格結構的元件或 WorldMesh，代表與場景相關聯的未系結空間對應網格。 每個網格所提供的索引和頂點資料，會使用與用來呈現所有新式轉譯 Api 中三角形網格的 [頂點和索引緩衝區](/windows/win32/direct3d9/rendering-from-vertex-and-index-buffers) 相同的熟悉版面配置。 在場景理解中，網格會使用32位的索引，而且可能需要針對某些轉譯引擎分割成區塊。

#### <a name="winding-order-and-coordinate-systems"></a>纏繞順序和座標系統

場景理解所產生的所有網格都應該使用順向的纏繞順序，在 Right-Handed 座標系統中傳回網格。 

注意：在191105之前的 OS 組建可能會有已知的錯誤，其中「世界」網格以 Counter-Clockwise 的纏繞順序傳回，這會在之後修正。

### <a name="scenequad"></a>SceneQuad

SceneQuad 是代表佔用3d 世界之2d 表面的 SceneComponent。 SceneQuads 的使用方式類似于 ARKit ARPlaneAnchor 或 ARCore 平面，但它們提供了更高階的功能，像是一般應用程式使用的2d 畫布或增強的 UX。 提供2D 特定 Api 供四邊形使用，讓放置和版面配置便於使用，並開發 (但使用四邊形轉譯) 的例外狀況，應該會比較類似于使用2d 畫布來處理3d 網格。

#### <a name="scenequad-shape"></a>SceneQuad 圖形

SceneQuads 在2d 中定義界限矩形介面。 不過，SceneQuads 代表具有任意且可能複雜圖形 (例如環圈圖的圖形 ) 。若要代表四顆環的複雜圖形，您可以使用 GetSurfaceMask API 將介面的形狀轉譯至您提供的影像緩衝區。 如果具有四個的 SceneObject 也有網格，則網格三角形應該相當於這個呈現的影像，它們都代表介面的真實幾何，不論是2d 或3d 座標。

## <a name="scene-understanding-sdk-details-and-reference"></a>場景理解 SDK 詳細資料和參考

下一節將協助您熟悉 SceneUnderstanding 的基本概念。 本節應提供您基本概念，此時您應該有足夠的內容可流覽範例應用程式，以瞭解如何使用 SceneUnderstanding 全面性地型。

### <a name="initialization"></a>初始化

使用 SceneUnderstanding 的第一個步驟是讓您的應用程式取得場景物件的參考。 這可以透過兩種方式之一來完成，而場景可以由驅動程式計算，也可以取消序列化先前計算的現有場景。 後者適用于在開發期間使用 SceneUnderstanding，其中應用程式和體驗可在沒有混合現實裝置的情況下快速建立原型。

場景是使用 SceneObserver 來計算。 建立場景之前，您的應用程式應該查詢您的裝置，以確保它支援 SceneUnderstanding，以及要求使用者存取 SceneUnderstanding 需要的資訊。

```cs
if (!SceneObserver.IsSupported())
{
    // Handle the error
}

// This call should grant the access we need.
await SceneObserver.RequestAccessAsync();
```

如果未呼叫 RequestAccessAsync ( # A1，則計算新場景將會失敗。 接下來，我們將計算以混合現實耳機為基礎的新場景，並擁有10計量的半徑。

```cs
// Create Query settings for the scene update
SceneQuerySettings querySettings;

querySettings.EnableSceneObjectQuads = true;                                       // Requests that the scene updates quads.
querySettings.EnableSceneObjectMeshes = true;                                      // Requests that the scene updates watertight mesh data.
querySettings.EnableOnlyObservedSceneObjects = false;                              // Do not explicitly turn off quad inference.
querySettings.EnableWorldMesh = true;                                              // Requests a static version of the spatial mapping mesh.
querySettings.RequestedMeshLevelOfDetail = SceneMeshLevelOfDetail.Fine;            // Requests the finest LOD of the static spatial mapping mesh.

// Initialize a new Scene
Scene myScene = SceneObserver.ComputeAsync(querySettings, 10.0f).GetAwaiter().GetResult();
```

### <a name="initialization-from-data-also-known-as-the-pc-path"></a>從資料初始化 (也稱為。 電腦路徑) 

雖然可以計算場景以進行直接取用，但也可以使用序列化形式來計算，以供稍後使用。 這已證明適用于開發，因為它可讓開發人員在不需要裝置的情況下工作並測試場景理解。 將場景序列化的動作與計算場景幾乎完全相同，而是將資料傳回到您的應用程式，而不是由 SDK 在本機還原序列化。 您可以自行將其還原序列化，或將其儲存供日後使用。

```cs
// Create Query settings for the scene update
SceneQuerySettings querySettings;

// Compute a scene but serialized as a byte array
SceneBuffer newSceneBuffer = SceneObserver.ComputeSerializedAsync(querySettings, 10.0f).GetAwaiter().GetResult();

// If we want to use it immediately we can de-serialize the scene ourselves
byte[] newSceneData = new byte[newSceneBuffer.Size];
newSceneBuffer.GetData(newSceneData);
Scene mySceneDeSerialized = Scene.Deserialize(newSceneData);

// Save newSceneData for later
```

### <a name="sceneobject-enumeration"></a>SceneObject 列舉

既然您的應用程式有場景，您的應用程式將會查看 SceneObjects 並與之互動。 這是透過存取 **SceneObjects** 屬性來完成的：

```cs
SceneObject firstFloor = null;

// Find the first floor object
foreach (var sceneObject in myScene.SceneObjects)
{
    if (sceneObject.Kind == SceneObjectKind.Floor)
    {
        firstFloor = sceneObject;
        break;
    }
}
```

### <a name="component-update-and-refinding-components"></a>元件更新和 refinding 元件

另外還有另一個函式可在場景中抓取元件，稱為 **_sys.application.findcomponent_* _。 當更新追蹤物件，並在稍後的場景中尋找時，此函式很有用。 下列程式碼會計算相對於前一個場景的新場景，然後在新場景中找出樓層。

```cs
// Compute a new scene, and tell the system that we want to compute relative to the previous scene
Scene myNextScene = SceneObserver.ComputeAsync(querySettings, 10.0f, myScene).GetAwaiter().GetResult();

// Use the Id for the floor we found last time, and find it again
firstFloor = (SceneObject)myNextScene.FindComponent(firstFloor.Id);

if (firstFloor != null)
{
    // We found it again, we can now update the transforms of all objects we attached to this floor transform
}
```

## <a name="accessing-meshes-and-quads-from-scene-objects"></a>從場景物件存取網格和四邊形

一旦找到 SceneObjects，您的應用程式很可能會想要存取其所組成之四邊形/網格中所包含的資料。 這項資料是使用 _*_四邊形_*_ 和 _*_網格_*_ 屬性來存取。 下列程式碼將列舉 floor 物件的所有四邊形和網格。

```cs

// Get the transform for the SceneObject
System.Numerics.Matrix4x4 objectToSceneOrigin = firstFloor.GetLocationAsMatrix();

// Enumerate quads
foreach (var quad in firstFloor.Quads)
{
    // Process quads
}

// Enumerate meshes
foreach (var mesh in firstFloor.Meshes)
{
    // Process meshes
}
```

請注意，它是具有相對於場景原點之轉換的 SceneObject。 這是因為 SceneObject 代表「東西」的實例，並可在空間中加以定位、四邊形和網格表示相對於其父系的轉換幾何。 不同的 SceneObjects 可以參考相同的 SceneMesh/SceneQuad SceneComponents，也有可能是 SceneObject 有一個以上的 SceneMesh/SceneQuad。

### <a name="dealing-with-transforms"></a>處理轉換

在處理轉換時，場景理解已刻意嘗試配合傳統的3D 場景標記法。 因此，每個場景會限制為單一座標系統，就像是最常見的3D 環境表示一樣。 SceneObjects 每個都提供其相對於座標系統的位置。 如果您的應用程式處理的場景會延展單一來源提供的限制，讓它可以將 SceneObjects 錨定到 SpatialAnchors，或是產生數個場景並將它們合併在一起，但為了簡單起見，我們假設防水場景存在於自己的原點，並由場景所定義的一個來當地語系化。

例如，下列 Unity 程式碼示範如何使用 Windows 感知和 Unity Api 來調整座標系統的組合。 如需有關取得與 Unity 世界原點對應之 SpatialCoordinateSystem 的詳細資訊，請參閱 [SpatialCoordinateSystem](//uwp/api/windows.perception.spatial.spatialcoordinatesystem) 和 [SpatialGraphInteropPreview](//uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview) ，以取得有關 Windows 認知 api 的詳細資料，以及 [Unity 中的混合現實原生物件](//windows/mixed-reality/unity-xrdevice-advanced) 。

```cs
private System.Numerics.Matrix4x4? GetSceneToUnityTransformAsMatrix4x4(SceneUnderstanding.Scene scene)
{

      System.Numerics.Matrix4x4? sceneToUnityTransform = System.Numerics.Matrix4x4.Identity;

      Windows.Perception.Spatial.SpatialCoordinateSystem sceneCoordinateSystem = Microsoft.Windows.Perception.Spatial.Preview.SpatialGraphInteropPreview.CreateCoordinateSystemForNode(scene.OriginSpatialGraphNodeId);
      HolograhicFrameData holoFrameData =  Marshal.PtrToStructure<HolograhicFrameData>(UnityEngine.XR.XRDevice.GetNativePtr());
      Windows.Perception.Spatial.SpatialCoordinateSystem unityCoordinateSystem = Microsoft.Windows.Perception.Spatial.SpatialCoordinateSystem.FromNativePtr(holoFrameData.ISpatialCoordinateSystemPtr);

      sceneToUnityTransform = sceneCoordinateSystem.TryGetTransformTo(unityCoordinateSystem);

      if(sceneToUnityTransform != null)
      {
          sceneToUnityTransform = ConvertRightHandedMatrix4x4ToLeftHanded(sceneToUnityTransform.Value);
      }
      else
      {
          return null;
      }

    return sceneToUnityTransform;
}
```

每個都 `SceneObject` 有轉換，然後套用至該物件。 在 Unity 中，我們轉換為右手座標，並將本機轉換指派為：

```cs
private System.Numerics.Matrix4x4 ConvertRightHandedMatrix4x4ToLeftHanded(System.Numerics.Matrix4x4 matrix)
{
    matrix.M13 = -matrix.M13;
    matrix.M23 = -matrix.M23;
    matrix.M43 = -matrix.M43;

    matrix.M31 = -matrix.M31;
    matrix.M32 = -matrix.M32;
    matrix.M34 = -matrix.M34;

    return matrix;
}

 private void SetUnityTransformFromMatrix4x4(Transform targetTransform, System.Numerics.Matrix4x4 matrix, bool updateLocalTransformOnly = false)
 {
    if(targetTransform == null)
    {
        return;
    }

    Vector3 unityTranslation;
    Quaternion unityQuat;
    Vector3 unityScale;

    System.Numerics.Vector3 vector3;
    System.Numerics.Quaternion quaternion;
    System.Numerics.Vector3 scale;

    System.Numerics.Matrix4x4.Decompose(matrix, out scale, out quaternion, out vector3);

    unityTranslation = new Vector3(vector3.X, vector3.Y, vector3.Z);
    unityQuat        = new Quaternion(quaternion.X, quaternion.Y, quaternion.Z, quaternion.W);
    unityScale       = new Vector3(scale.X, scale.Y, scale.Z);

    if(updateLocalTransformOnly)
    {
        targetTransform.localPosition = unityTranslation;
        targetTransform.localRotation = unityQuat;
    }
    else
    {
        targetTransform.SetPositionAndRotation(unityTranslation, unityQuat);
    }
}

// Assume we have an SU object called suObject and a unity equivalent unityObject

System.Numerics.Matrix4x4 converted4x4LocationMatrix = ConvertRightHandedMatrix4x4ToLeftHanded(suObject.GetLocationAsMatrix());
SetUnityTransformFromMatrix4x4(unityObject.transform, converted4x4LocationMatrix, true);
        
```

### <a name="quad"></a>四

四邊形的設計目的是要協助2D 放置案例，而且應該將其視為2D 畫布 UX 元素的延伸。 雖然四邊形是 SceneObjects 的元件，而且可以在3D 中轉譯，但四個 Api 本身會假設四邊形是2D 結構。 它們提供的資訊包括範圍、圖形，以及提供用於放置的 Api。

四邊形具有矩形範圍，但代表任意成形的2D 表面。 若要啟用與3D 環境互動之2D 表面上的放置，四邊形提供公用程式以實現這種互動。 目前的場景理解提供兩種這類功能： _ *FindCentermostPlacement** 和 **GetSurfaceMask**。 FindCentermostPlacement 是高階 API，可找出四個位置上可放置物件的位置，並且會嘗試找出您的物件的最佳位置，以確保您提供的周框方塊會留在基礎介面上。

> [!NOTE]
> 輸出的座標相對於「四個空間」中的四個十字，左上角的 (x = 0，y = 0) ，就如同其他 windows Rect 類型一樣。 使用您自己的物件的來源時，請務必將此納入考慮。 

下列範例示範如何尋找 centermost 可放置位置，並將全像點放置在四個位置。

```cs
// This code assumes you already have a "Root" object that attaches the Scene's Origin.

// Find the first quad
foreach (var sceneObject in myScene.SceneObjects)
{
    // Find a wall
    if (sceneObject.Kind == SceneObjectKind.Wall)
    {
        // Get the quad
        var quads = sceneObject.Quads;
        if (quads.Count > 0)
        {
            // Find a good location for a 1mx1m object  
            System.Numerics.Vector2 location;
            if (quads[0].FindCentermostPlacement(new System.Numerics.Vector2(1.0f, 1.0f), out location))
            {
                // We found one, anchor something to the transform
                // Step 1: Create a new game object for the quad itself as a child of the scene root
                // Step 2: Set the local transform from quads[0].Position and quads[0].Orientation
                // Step 3: Create your hologram and set it as a child of the quad's game object
                // Step 4: Set the hologram's local transform to a translation (location.x, location.y, 0)
            }
        }
    }
}
```

步驟1-4 高度取決於您的特定架構/執行，但主題應該類似。 有一點要注意的是，四個只代表在空間中當地語系化的界限2D 平面。 藉由讓您的引擎/架構知道四個部分，並將您的物件與四個實體相對應，您的全像是會正確地找出與真實世界相關的您的全像。 

<!-- 
// TODO: Add sample link when released
For more detailed information please see our samples on quads which show specific implementations.
-->

### <a name="mesh"></a>網狀

網格代表物件或環境的幾何標記法。 與 [空間對應](../../design/spatial-mapping.md)、網格索引和每個空間介面網格所提供的頂點資料非常類似，其使用的是與用來呈現所有新式轉譯 api 中三角形網格的頂點和索引緩衝區相同的熟悉版面配置。 頂點位置是在的座標系統中提供 `Scene` 。 用來參考此資料的特定 Api 如下：

```cs
void GetTriangleIndices(int[] indices);
void GetVertices(System.Numerics.Vector3[] vertices);
```

下列程式碼提供從網格結構產生三角形清單的範例：

```cs
uint[] indices = new uint[mesh.TriangleIndexCount];
System.Numerics.Vector3[] positions = new System.Numerics.Vector3[mesh.VertexCount];

mesh.GetTriangleIndices(indices);
mesh.GetVertexPositions(positions);
```

索引/頂點緩衝區必須 >= 索引/頂點計數，但也可以任意調整大小，以便有效率地重複使用記憶體。

### <a name="collidermesh"></a>ColliderMesh

場景物件可透過 [網格] 和 [ColliderMeshes] 屬性，提供網格和碰撞的網格資料存取。 這些網格一律會相符，這表示網格屬性的 i'th 索引代表與 ColliderMeshes 屬性的 i'th 索引相同的幾何。 如果執行時間/物件支援碰撞器網格，則在您的應用程式使用 colliders 的任何地方，都可保證您取得最小的多邊形、最高的順序近似值，以及使用 ColliderMeshes 的最佳作法。 如果系統不支援 colliders，則在 ColliderMeshes 中傳回的網格物件將會是與網格減少記憶體限制相同的物件。

## <a name="developing-with-scene-understanding"></a>使用場景理解進行開發

至此，您應該瞭解場景瞭解執行時間和 SDK 的核心構成要素。 大部分的電源和複雜性都是存取模式、與3D 架構的互動，以及可以撰寫在這些 Api 之上的工具，以進行空間規劃、房間分析、流覽、物理等等等更先進的工作。 我們希望在範例中抓住這些範例，建議您以適當的方向引導您的案例。 如果有未解決的範例或案例，請讓我們知道，我們會嘗試記錄/原型您所需的內容。

### <a name="where-can-i-get-sample-code"></a>我可以在哪裡取得範例程式碼？

適用于 Unity 的場景理解範例程式碼可以在我們的 [Unity 範例頁面](https://github.com/sceneunderstanding-microsoft/unitysample) 頁面上找到。 此應用程式可讓您與您的裝置通訊並轉譯各種場景物件，或者，它可讓您在電腦上載入已序列化的場景，並讓您在沒有裝置的情況下體驗到場景的理解。

### <a name="where-can-i-get-sample-scenes"></a>我可以在哪裡取得範例場景？

如果您有 HoloLens2，可以將 ComputeSerializedAsync 的輸出儲存至檔案，並在您自己的方便的情況下還原序列化，以儲存您所捕獲的任何場景。 

如果您沒有 HoloLens2 裝置，但想要在場景理解的情況下播放，您必須下載預先捕捉的場景。 場景理解範例目前隨附的序列化場景，可供您自行下載及使用。 您可以在這裡找到：

[場景理解範例場景](https://github.com/microsoft/MixedReality-SceneUnderstanding-Samples/tree/master/Assets/Resources/SerializedScenesForPCPath)

## <a name="see-also"></a>另請參閱

* [空間對應](../../design/spatial-mapping.md)
* [場景理解](../../design/scene-understanding.md)
* [Unity 範例](https://github.com/microsoft/MixedReality-SceneUnderstanding-Samples)