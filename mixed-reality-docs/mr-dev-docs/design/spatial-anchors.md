---
title: 空間錨點
description: 使用空間錨點轉譯穩定全像投影的最佳做法。
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: 座標系統、空間座標系統、世界規模、世界、縮放、位置、方向、錨點、空間錨點、世界鎖定、全球鎖定、持續性、共用、混合現實耳機、windows mixed reality 耳機、虛擬實境耳機、HoloLens
ms.openlocfilehash: 92694023a3c7c7266b0f5d927180df20692b9d45
ms.sourcegitcommit: 4f3ef057a285be2e260615e5d6c41f00d15d08f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2020
ms.locfileid: "94703304"
---
# <a name="spatial-anchors"></a>空間錨點

空間錨點代表在世界中，系統會持續追蹤一段時間的重要點。 每個錨點都有一個會視需要調整 (相對於其他錨點或參考架構) 的[座標系統](coordinate-systems.md) ，以確保錨定的全像投影能維持準確定位。  在錨點的座標系統中轉譯全像投影，可以在任何指定的時間為您提供最準確的全像投影定位。 這是因為系統不斷地將其移回相對於真實世界的位置，而不是一段時間的小型調整成本。

您也可以跨應用程式會話和跨裝置來保存和共用空間錨點：
* 藉由將本機空間錨點儲存到磁片，並于稍後再將其載入，您的應用程式可以在單一 HoloLens 上的多個應用程式會話之間計算相同的位置。
* 藉由使用 <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure 空間錨點</a> 來建立雲端錨點，您的應用程式可以跨多個 HoloLens、IOS 和 Android 裝置共用空間錨點。 藉由讓每個裝置使用相同的空間錨點轉譯全像影像，使用者會看到在真實世界中的相同位置出現全像投影。 這可提供即時共用體驗。
* 您也可以使用<a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> 跨 HoloLens、iOS 和 Android 裝置取得非同步全像投影持久性。 藉由共用持久的雲端空間錨點，多個裝置就能觀察相同的已保存全像投影一段時間，即使那些裝置並未同時存在。

您通常可以使用 [參考的階段框架](coordinate-systems.md#stage-frame-of-reference) （而不是空間錨點），針對行動網卡桌上型耳機提供固定規模或房間規模的體驗，這會提供您單一座標系統來轉譯所有內容。 但是，如果您的應用程式想要讓使用者在 HoloLens 中穿梭超過5個計量，或許是在整個大樓的整個樓層中運作，您將需要空間錨點來保持內容的穩定。

雖然空間錨點對於在真實世界中應保持固定的全像投影非常有用，但是一旦將錨點放至定位，就無法移動它。 錨點有一些替代方式，更適合用來與使用者一起標記的動態全像投影。 最好使用靜止的參考架構 (Unity 的世界座標基礎) 或附加的參考架構來定位動態全像投影。

## <a name="best-practices"></a>最佳作法

這些空間錨點指南將協助您轉譯穩定、且能準確追蹤現實世界的全像投影。

### <a name="create-spatial-anchors-where-users-place-them"></a>建立使用者放置的空間錨點

一般而言，使用者是明確放置空間錨點的使用者。

例如，在 HoloLens 上，應用程式可以將使用者的 [注視](gaze-and-commit.md) 光線與 [空間對應](spatial-mapping.md) 網格相交，讓使用者決定要放置全像影像的位置。 當使用者按下該影像時，請在交集點建立空間錨點，然後將全像位置放在錨點座標系統的原點。

本機空間錨點很容易就能建立。 如果有多個錨點可以共用其基礎感應器資料，系統會合並其內部資料。 一般來說，您應該針對使用者明確放置的每個全息圖建立新的本機空間錨點，但以下所述的案例除外，例如固定的全像投影群組。

### <a name="always-render-anchored-holograms-within-3-meters-of-their-anchor"></a>一律轉譯位於錨點 3 公尺範圍內的錨定全像投影

空間錨點可穩固錨點原始位置附近的座標系統。 如果您從該原點轉譯超過3個量表的全像投影，這些全息表可能會因為拉杆 arm 的影響，而從該原點的距離產生明顯的位置錯誤。 這適用于使用者接近錨點，因為全像全像使用者一樣。 換句話說，最遠的全像影像的角度錯誤將會很小。 不過，如果使用者往上移到最新的全像全像影像，它就會很大，因此，遠處錨點來源的拉杆 arm 效果相當明顯。

### <a name="group-holograms-that-should-form-a-rigid-cluster"></a>應形成固定叢集的群組全像投影

如果應用程式預期這些全像間的全像之間保持固定的關聯性，則多個全像影像可以共用同一個空間錨點。

例如，如果您要在房間內以動畫顯示全像攝影系統，最好將所有的日光系統物件系結至中央的單一錨點，讓它們彼此順暢地移動。 在這個情況下，即使各個元件部分會圍繞錨點動態移動，整個太陽系也會維持錨定狀態。

維持全像影像穩定性的關鍵是遵循上述的3計量規則。

### <a name="render-highly-dynamic-holograms-using-the-stationary-frame-of-reference-instead-of-a-local-spatial-anchor"></a>使用靜止的參考架構而不是本機空間錨點來轉譯高動態全像投影

如果您有高度動態的全像點，例如沿著使用者附近的房間或浮動 UI 來流覽的字元，最好略過本機空間錨點，並直接在 [參考的靜止框架](coordinate-systems.md#stationary-frame-of-reference)所提供的座標系統中轉譯這些全像投影。 在 Unity 中，您可以直接在全局座標中放入全像無 WorldAnchor，以達到這個目的。 當使用者離全像全像全像全像一樣，在固定的參考框架中的全息圖可能會發生漂移。 但這對動態的全像是較不明顯的現象：可能是因為全像全像全像移動的全像移動一樣，也可能是因為動態的移動會讓它接近最小化漂移的使用者。

動態全像投影的一個有趣的例子是一個物件從某個錨定座標系統移動至另一個座標系統的動畫。 例如，您可能會有兩個 castles 的10個計量，每個都在自己的空間錨點，而一個 castle 引發另一個 castle 的 cannonball。 Cannonball 引發時，您可以將它呈現在固定的參考框架中的適當位置，以與第一個 castle 的錨定座標系統中的 cannon 一致。 然後它可以在靜止的參考架構中追蹤砲彈在空中飛行 10 公尺的軌跡。 當 cannonball 到達其他 castle 時，您可以選擇將它移到第二個 castle 的錨定座標系統，以允許使用該 castle 固定主體的物理計算。

如果您跨裝置共用高度動態的全像影像，您將需要挑選一些雲端空間錨點來作為其父系，因為無法在裝置間共用固定的參考框架。  不過，在這種情況下，您應該確定動態全像影像或裝置可供觀看，以確保在所有裝置上都能穩定顯示全像影像。

### <a name="avoid-creating-a-grid-of-spatial-anchors"></a>避免建立空間錨點的網格

您可能會想要讓應用程式在使用者四處移動時，卸載空間錨點的一般方格，將動態物件從錨點轉換至錨點。 不過，這牽涉到許多應用程式的管理，而不會有系統本身在內部維護的深度感應器資料的好處。 在這些情況下，您通常會以較少的方式來達到更好的結果，其方式是將您的全像上一節所述，放在參考的靜止框架中。
在靜態空間前後放置一組雲端空間錨點時，請考慮將空間錨點放在使用者根據上述原則所遇到的金鑰磁碟空間的位置，而不是建立任意的錨點方格。 這可確保您能夠讓那些關鍵的全像投影獲得最高的穩定性。

### <a name="release-local-spatial-anchors-you-no-longer-need"></a>釋出您不再需要的本機空間錨點

當本機空間錨點為作用中時，系統會優先保留位於該錨點附近的感應器資料。 如果您無法再使用空間錨點，請停止存取其座標系統。 這可讓其基礎感應器資料視需要移除。

對於您已保存至空間錨點存放區的本機錨點來說，這一點特別重要。 這些錨點後方的感應器資料將會永久保留，讓您的應用程式在未來的會話中找出該錨點，進而減少可用來追蹤其他錨點的空間。 只保存您需要在未來的會話中再次尋找的本機錨點，並在不再對使用者有意義時，將它們從存放區中移除。

對於雲端空間錨點，您的儲存體可以依照案例需要調整規模。 您可以視需要儲存任意數量的雲端錨點，只有當您知道您的使用者不需要再次尋找該錨點上的全像時，才會釋放它們。

## <a name="see-also"></a>另請參閱
* [座標系統](coordinate-systems.md)
* [混合實境中的共用體驗](../develop/platform-capabilities-and-apis/shared-experiences-in-mixed-reality.md)
* <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>
* [Unity 中的持續性](../develop/unity/persistence-in-unity.md)
* [DirectX 中的空間錨點](../develop/native/coordinate-systems-in-directx.md#place-holograms-in-the-world-using-spatial-anchors)
* [案例研究 - 在實境中的的透視技術](../out-of-scope/case-study-looking-through-holes-in-your-reality.md)
