---
title: 空間錨點
description: 瞭解在混合現實應用程式中使用空間錨點轉譯穩定的全像影像的最佳作法。
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: 座標系統、空間座標系統、世界規模、世界、縮放、位置、方向、錨點、空間錨點、世界鎖定、全球鎖定、持續性、共用、混合現實耳機、windows mixed reality 耳機、虛擬實境耳機、HoloLens
ms.openlocfilehash: dc9b57d51f4202499d82abb8d210261d2ee36dc60bb90ed039a7554f82af79a0
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2021
ms.locfileid: "115193512"
---
# <a name="spatial-anchors"></a>空間錨點

空間錨點代表一段時間內系統追蹤的一個重點。 每個錨點都有一個可調整的 [座標系統](coordinate-systems.md)（根據其他錨點或參考的框架），以確保錨定的全像位置保持精確。  在錨點座標系統中轉譯全息圖，可讓您在任何指定時間最精確地放置該全像投影。 這是因為系統會根據真實世界，不斷地將其移回原位的位置，而將一段時間的小型調整成本納入考慮。

您也可以跨應用程式會話和跨裝置來保存和共用空間錨點：
* 藉由將本機空間錨點儲存到磁片，並于稍後再將其載入，您的應用程式可以在單一 HoloLens 上的多個應用程式會話之間計算相同的位置。
* 藉由使用<a href="/azure/spatial-anchors/overview" target="_blank">Azure 空間錨點</a>來建立雲端錨點，您的應用程式可以跨多個 HoloLens、iOS 和 Android 裝置共用空間錨點。 藉由讓每個裝置使用相同的空間錨點轉譯全像影像，使用者會看到在真實世界中的相同位置出現全像投影。 這可提供即時共用體驗。
* 您也可以在 HoloLens、iOS 和 Android 裝置上，使用<a href="/azure/spatial-anchors/overview" target="_blank">Azure 空間錨點</a>來取得非同步全像持續性。 藉由共用長期雲端空間錨點，即使這些裝置不會同時存在，多個裝置也可以觀察經過一段時間的相同保存全息圖。

您通常可以使用 [參考的階段框架](coordinate-systems.md#stage-frame-of-reference) （而不是空間錨點），針對行動網卡桌上型耳機提供固定規模或房間規模的體驗，這會提供您單一座標系統來轉譯所有內容。 但是，如果您的應用程式可讓使用者在 HoloLens 中穿梭超過5個量，可能會在整個大樓的整個樓層進行作業，您將需要空間錨點來保持內容的穩定。

雖然空間錨點對於在真實世界中應保持固定的全像投影非常有用，但是一旦將錨點放至定位，就無法移動它。 錨點有一些替代方式，更適合用來與使用者一起標記的動態全像投影。 最好使用固定的參考框架來定位動態全像， (Unity 的全局座標) 或附加的參考框架。

## <a name="best-practices"></a>最佳做法

這些空間錨點指南將協助您轉譯穩定、且能準確追蹤現實世界的全像投影。

### <a name="create-spatial-anchors-where-users-place-them"></a>建立使用者放置的空間錨點

一般而言，使用者是明確放置空間錨點的使用者。

例如，在 HoloLens 上，應用程式可以將使用者的[注視](gaze-and-commit.md)光線與[空間對應](spatial-mapping.md)網格相交，讓使用者決定要放置全像影像的位置。 當使用者按下該影像時，請在交集點建立空間錨點，然後將全像位置放在錨點座標系統的原點。

本機空間錨點很容易就能建立。 如果有多個錨點可以共用其基礎感應器資料，系統就會合並內部資料。 建議您為使用者明確放置的每個全息圖建立新的本機空間錨點，但以下所述的案例除外，例如固定的全像投影群組。

### <a name="always-render-anchored-holograms-within-3-meters-of-their-anchor"></a>一律轉譯位於錨點 3 公尺範圍內的錨定全像投影

空間錨點可穩固錨點原始位置附近的座標系統。 如果您從原點轉譯超過3個量表的全像投影，則可能會因為拉杆 arm 的影響，而從該原點的距離來看，可能會遇到明顯的位置錯誤。 這適用于使用者接近錨點，因為全像全像使用者一樣。 換句話說，最遠的全像影像的角度錯誤將會很小。 不過，如果使用者往上移到最遠的全像全像影像，則會在其觀賞中很大，因此，遠處錨點來源的拉杆 arm 效果也很明顯。

### <a name="group-holograms-that-should-form-a-rigid-cluster"></a>應形成固定叢集的群組全像投影

如果應用程式預期這些全像間的全像之間保持固定的關聯性，則多個全像影像可以共用同一個空間錨點。

例如，如果您要在房間內以動畫顯示全像攝影系統，最好將所有的日光系統物件系結至中央的單一錨點。 如此一來，它們就會以彼此順暢地移動。 在此情況下，它是錨定的整個日光系統，即使它的元件部分在錨點動態移動也是一樣。

維持全像影像穩定性的關鍵是遵循上述的3計量規則。

### <a name="render-highly-dynamic-holograms-using-the-stationary-frame-of-reference-instead-of-a-local-spatial-anchor"></a>使用靜止的參考架構而不是本機空間錨點來轉譯高動態全像投影

如果您有高度動態的全像點，例如沿著使用者附近的房間或浮動 UI 的字元，則最好略過本機空間錨點，並直接在 [參考的靜止框架](coordinate-systems.md#stationary-frame-of-reference)所提供的座標系統中轉譯這些全像投影。 在 Unity 中，您可以直接在全局座標中放入全像無 WorldAnchor，以達到這個目的。 在固定的參考框架中全像投影可能會在使用者離全像全像全像投影時遇到漂移。 但這對動態的全像是較不明顯的現象：可能是因為全像全像全像移動的全像移動一樣，也可能是因為動態的移動會讓它接近最小化漂移的使用者。

動態全像投影的一個有趣的例子是一個物件從某個錨定座標系統移動至另一個座標系統的動畫。 例如，您可能會有兩個 castles 的10個計量，每個都在自己的空間錨點，而一個 castle 引發另一個 castle 的 cannonball。 當 cannonball 引發時，您可以將它呈現在固定的參考框架中的適當位置，以與第一個 castle 的錨定座標系統中的 cannon 一致。 然後它可以在靜止的參考架構中追蹤砲彈在空中飛行 10 公尺的軌跡。 當 cannonball 到達其他 castle 時，您可以將它移到第二個 castle 的錨定座標系統，以允許使用該 castle 固定主體的物理計算。

如果您要跨裝置共用高度動態的全像影像，請挑選一些雲端空間錨點做為其父系，因為無法在裝置間共用固定的參考框架。  不過，您應該確保動態全像影像或裝置的觀看位置都維持在錨點的3計量半徑內，如此一來，全像全像所有裝置上的全像是穩定的。

### <a name="avoid-creating-a-grid-of-spatial-anchors"></a>避免建立空間錨點的網格

您可能會想要讓應用程式在使用者四處移動時，卸載空間錨點的一般方格，將動態物件從錨點轉換至錨點。 不過，這牽涉到更多的應用程式管理，而不會有系統本身在內部維護的深度感應器資料的好處。 在這些情況下，您可以藉由將您的全像上一節所述，將您的全像放在參考的靜止框架中來達到更好的
當您在靜態空間周圍預先放置一組雲端空間錨點時，請考慮將空間錨點放在使用者的金鑰磁碟空間的位置，而不是建立任意的錨點方格。 這可確保您能夠讓那些關鍵的全像投影獲得最高的穩定性。

### <a name="release-local-spatial-anchors-you-no-longer-need"></a>釋出您不再需要的本機空間錨點

當本機空間錨點為作用中時，系統會優先保留位於該錨點附近的感應器資料。 如果您不再使用空間錨點，請停止存取其座標系統。 這可讓其基礎感應器資料視需要移除。

對於您已保存到空間錨點存放區的本機錨點而言，這一點特別重要。 這些錨點後方的感應器資料將會永久保留，讓您的應用程式在未來的會話中找出該錨點，進而減少可用來追蹤其他錨點的空間。 只保存您需要在未來的會話中再次尋找的本機錨點。 當使用者不再有意義時，建議您將它們從存放區中移除。

對於雲端空間錨點，您的儲存體可以依照案例需要調整規模。 您可以儲存所需數量的雲端錨點，並在您知道使用者不再需要錨點時釋放它們。

## <a name="see-also"></a>另請參閱

* [座標系統](coordinate-systems.md)
* [混合實境中的共用體驗](../develop/platform-capabilities-and-apis/shared-experiences-in-mixed-reality.md)
* <a href="/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>
* [Unity 中的持續性](../develop/unity/persistence-in-unity.md)
* [DirectX 中的空間錨點](../develop/native/coordinate-systems-in-directx.md#place-holograms-in-the-world-using-spatial-anchors)
* [案例研究 - 在實境中的的透視技術](../out-of-scope/case-study-looking-through-holes-in-your-reality.md)