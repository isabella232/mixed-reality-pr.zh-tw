---
title: 場景理解
description: 瞭解如何使用 HoloLens 的場景理解進行開發，包括 SDK、功能和常見的使用案例。
author: szymons
ms.author: szymons
ms.date: 07/08/2019
ms.topic: article
keywords: 場景理解、空間對應、Windows Mixed Reality、Unity、混合現實耳機、Windows Mixed reality 耳機、虛擬實境耳機、HoloLens、遮蔽、SDK
ms.openlocfilehash: 6d950fca4211aef659b1f957ca5e7135ac9764ac
ms.sourcegitcommit: 6b8ccb881fbbdaa5119841eac528e29d7b49bd04
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2021
ms.locfileid: "123557315"
---
# <a name="scene-understanding"></a>場景理解

場景理解為混合的現實開發人員提供結構化、高階的環境標記法，其設計目的是為了讓環保感知應用程式的開發變得直覺。 場景理解藉由結合現有混合現實執行時間的強大功能，例如高度精確但較不具結構化的 [空間對應](spatial-mapping.md) 和全新的 AI 驅動執行時間。 藉由結合這些技術，場景理解會產生3D 環境的標記法，類似于您在 Unity 或 ARKit/ARCore 架構中所使用的環境。 場景理解進入點的開頭是場景觀察器，由您的應用程式呼叫以計算新場景。 現在，此技術可以產生3個相異但相關的物件類別：

* 簡化的防水環境網格，可推斷平面房間結構而不會雜亂
* 用於放置的平面區域，我們稱之為四邊形
* 與我們所呈現的四邊形/防水資料對齊的 [空間對應](spatial-mapping.md) 網格快照集

![空間對應網格、標示為平面介面、防水網格](images/SUScenarios.png)

本檔的目的是要提供案例總覽，以及說明場景理解和空間對應共用的關聯性。 如果您想要查看實際的場景理解，請參閱下面 **的設計全像投影空間感知** 影片示範：

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Spatial-Awareness-Chapter/player]

*這段影片取自「設計全像投影」 HoloLens 2 應用程式。下載並享有完整 [的體驗。](https://aka.ms/dhapp)*

## <a name="developing-with-scene-understanding"></a>使用場景理解進行開發

本文僅適用于引入場景瞭解執行時間和概念。 如果您要尋找如何使用場景理解進行開發的相關檔，您可能會對下列文章感興趣：

[場景理解 SDK 總覽](../develop/unity/scene-understanding-SDK.md)

您可以從範例 GitHub 網站下載場景理解範例應用程式：

[場景理解範例](https://github.com/microsoft/MixedReality-SceneUnderstanding-Samples)

如果您沒有裝置，而且想要存取範例場景來嘗試進行場景瞭解，則範例資產資料夾中會有場景：

[場景理解範例場景](https://github.com/sceneunderstanding-microsoft/unitysample/tree/master/Assets/Resources/SerializedScenesForPCPath)

### <a name="sdk"></a>SDK

如果您要尋找以場景理解進行開發的特定詳細資料，請參閱 [場景理解 SDK 總覽](../develop/unity/scene-understanding-SDK.md) 檔。

### <a name="sample"></a>範例

## <a name="device-support"></a>裝置支援

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>功能</strong></td>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens (第 1 代)</strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="../discover/immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></td>
    </tr>
     <tr>
        <td>場景理解</td>
        <td>❌</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

## <a name="common-usage-scenarios"></a>常見使用案例

![一般空間對應使用案例的圖例：位置、遮蔽、物理和導覽](images/sm-concepts-1000px.png)<br>
*常見的空間對應使用案例：位置、遮蔽、物理和導覽。*

<br>

環境感知應用程式的許多核心案例都可以透過空間對應和場景理解來解決。 這些核心案例包括位置、遮蔽、物理等等。 場景理解和空間對應之間的核心差異，在於結構和簡化的最大精確度和延遲的取捨。 如果您的應用程式需要最低延遲的可能，以及只想要存取的網格三角形，請直接使用空間對應。 如果您要進行較高層級的處理，可以考慮改用場景理解模型，因為它應該會提供您功能的超集合。 您一律可以存取最完整且正確的空間對應資料，因為場景理解會在其標記法中提供空間對應網格的快照。

下列各節會回顧新場景理解 SDK 內容中的核心空間對應案例。

### <a name="placement"></a>放置

場景理解提供設計來簡化放置案例的新結構。 場景可以計算稱為 SceneQuads 的基本專案，其描述可放置全像影像的平面表面。 SceneQuads 的設計是圍繞放置，並描述2D 介面，並提供可放置於該介面上的 API。 先前，使用三角形網格來進行放置時，必須掃描四個部分的所有區域並進行填滿/後置處理，以找出適合物件放置的位置。 在四邊形時，這不一定是必要的，因為場景瞭解執行時間會推斷未掃描的四個部分，並使不是表面的區域失效。

:::row:::
    :::column:::
       ![已停用推斷的 SceneQuads，可捕獲掃描區域的放置區域。](images/SUQuads.png)<br>
       **映射 #1** -已停用推斷的 SceneQuads，可捕獲掃描區域的放置區域。
    :::column-end:::
        :::column:::
       ![已啟用推斷的四邊形，放置不再限於掃描的區域。](images/SUWatertight.png)<br>
        **影像 #2** -已啟用推斷的四邊形，放置不再限於掃描的區域。
    :::column-end:::
:::row-end:::

<br>


如果您的應用程式想要在您的環境的固定結構上放置2D 或3D 影像，則最好是從 [空間對應](spatial-mapping.md) 網格計算這項資訊，以方便放置 SceneQuads。 如需本主題的詳細資訊，請參閱 [場景理解 SDK 參考](../develop/unity/scene-understanding-SDK.md)

**注意** 若是相依于空間對應網格的舊版放置程式碼，則可以藉由設定 EnableWorldMesh 設定來計算空間對應網格和 SceneQuads。 如果場景理解 API 無法滿足您應用程式的延遲需求，我們建議您繼續使用 [空間對應 api](spatial-mapping.md#placement)。

### <a name="occlusion"></a>遮蔽

[空間對應遮蔽](spatial-mapping.md#occlusion) 維持環境的即時狀態時，是最不重要的方式。 雖然這可能有助於在高度動態的場景中提供遮蔽，但您可能會想要考慮針對遮蔽的場景瞭解有幾個原因。 如果您使用場景理解所產生的空間對應網格，則可以要求不會儲存在本機快取中且無法從認知 Api 使用的空間對應資料。 使用遮蔽和防水網格的空間對應可提供額外的價值，特別是完成未掃描的空間結構。

如果您的需求可容忍場景理解的延遲延遲，應用程式開發人員應該考慮使用場景理解防水網格，以及與平面表示一致的空間對應網格。 這會提供「最棒的」案例，其中簡化的防水遮蔽會使用更精細的 nonplanar 幾何，提供最實際的遮蔽地圖。

### <a name="physics"></a>物理特性

場景理解會產生防水網格，以使用語義分解空間，特別是為了解決空間對應網格所強加的物理限制。 防水結構可確保一律會達到物理光線轉換，而且語義分解可讓您更輕鬆地產生室內導覽的導覽網格。 如 [遮蔽](#occlusion)一節中所述，使用 EnableSceneObjectMeshes 和 EnableWorldMesh 建立場景將會產生最實際的完整網狀。 環境網格的防水屬性可防止點擊率測試失敗。 網格資料可確保物理與場景中的所有物件互動，而不只是空間結構。

### <a name="navigation"></a>導覽

以語義類別分解的平面網格是導覽和路徑規劃的理想結構，可簡化 [空間對應導覽](spatial-mapping.md#navigation) 總覽中所述的許多問題。 在場景中計算的 SceneMesh 物件是由表面型別取消組成，以確保導覽網格產生僅限於可進行的介面。 由於地板結構的簡單起見，3d 引擎（例如 Unity）中的動態 nav 網格產生會根據即時需求來實現。

產生精確的 nav 網格目前仍需要後置處理，也就是應用程式仍然必須將阻隔器投影至樓層，以確保流覽不會通過雜亂/資料表等等。 達成此目的最準確的方法是投射世界網格資料，如果場景是使用 EnableWorldMesh 旗標來計算的，就會提供此資料。

### <a name="visualization"></a>視覺效果

雖然 [空間對應視覺效果](spatial-mapping.md#visualization) 可用於環境的即時意見反應，但在許多情況下，平面和防水物件的簡易性可提供更多的效能或視覺品質。 如果投射在四邊形或平面防水網格所提供的平面表面上，使用空間對應所描述的陰影投影和接地技術可能更滿意。 這特別適用于完全預先掃描不適合的環境/案例，因為場景會推斷出，而完整的環境和平面假設會將構件降至最低。

此外，空間對應所傳回的表面總數會受限於內部空間快取，而場景理解的空間對應網格版本可以存取未快取的空間對應資料。 因此，場景理解更適合用來針對較大的空間來捕捉網格標記法 (例如，大於單一房間) 來進行視覺效果或進一步的網格處理。 以 EnableWorldMesh 傳回的世界網格會有一致的詳細資料層級，如果轉譯為框線，可能會產生更美觀的視覺效果。

### <a name="see-also"></a>另請參閱

* [場景理解 SDK](../develop/unity/scene-understanding-SDK.md)
* [空間對應](spatial-mapping.md)