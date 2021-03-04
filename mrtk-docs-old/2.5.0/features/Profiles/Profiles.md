---
title: Profiles
description: MRTK 中的檔設定檔
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、設定檔、
ms.openlocfilehash: badb1e1b5d20633922a8ff04b08ac98953cea559
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/03/2021
ms.locfileid: "101781296"
---
# <a name="profiles"></a>Profiles

MRTK 設定的主要方式之一是透過基礎套件中的許多可用設定檔。 [`MixedRealityToolkit`](xref:Microsoft.MixedReality.Toolkit.MixedRealityToolkit)場景中的主要物件會有使用中的設定檔，基本上是 ScriptableObject。 最上層的 MRTK 設定檔包含主要核心系統每個核心的子設定檔資料，每一個核心系統都是設計來設定其對應子系統的行為。 此外，這些子設定檔也是可編寫腳本的物件，因此可包含其下一個層級之其他設定檔物件的參考。 基本上，有一個連線設定檔的整個樹狀結構，這些設定檔會組成設定資訊，以說明如何初始化 MRTK 子系統和功能。

例如，輸入系統的行為是由輸入系統設定檔所控制，例如 `DefaultMixedRealityInputSystemProfile` (資產/MRTK/SDK/設定檔) 。 強烈建議您一律透過編輯器中的偵測器來修改設定檔 ScriptableObject 資產。

<img src="../Images/Profiles/input_profile.png" width="650px" alt="Input Profile" style="display:block;">
<sup>設定檔偵測器</sup>

> [!NOTE]
> 雖然這是為了讓設定檔可在執行時間交換，但 [目前無法運作](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/4289)

## <a name="default-profile"></a>預設設定檔

MRTK 會提供一組預設設定檔，其中涵蓋 MRTK 支援的大部分平臺和案例。 例如，當您選取 `DefaultMixedRealityToolkitConfigurationProfile` (資產/MRTK/SDK/設定檔時) 您將能夠在 VR 上試用案例 (OpenVR、WMR) 和 HoloLens (1 和 2) 。

請注意，因為這是一般用途的設定檔，所以不會針對任何特定使用案例進行優化。 如果您想要在其他平臺上擁有更佳的效能/特定設定，請參閱下列其他設定檔，這些設定檔會在其各自的平臺上稍微調整得更好。

## <a name="hololens-2-profile"></a>HoloLens 2 設定檔

MRTK 也提供已針對 HoloLens 2： `DefaultHoloLens2ConfigurationProfile` (資產/MRTK/SDK/設定檔/HoloLens2) 優化部署和測試的預設設定檔。

當系統提示您選擇 MixedRealityToolkit 物件的設定檔時，請使用此設定檔，而不是預設選取的設定檔。

HoloLens2 設定檔和預設設定檔之間的主要差異如下：

**已停用** 特徵：

- [界限系統](../Boundary/BoundarySystemGettingStarted.md)
- [傳送系統](../TeleportSystem/Overview.md)
- [空間感知系統](../SpatialAwareness/SpatialAwarenessGettingStarted.md)
- 因效能額外負荷而 ([手上網格視覺效果](../Input/HandTracking.md)) 

**已啟用** 系統：

- [眼睛追蹤提供者](../EyeTracking/EyeTracking_Main.md)
- 目視輸入模擬

攝影機設定檔設定會設定為相符，因此編輯器品質和播放程式品質都相同。 這與預設攝影機設定檔不同，因為不透明顯示會設定為較高的品質。 這項變更表示在編輯器品質較低的情況下，將會更接近裝置上呈現的內容。

> [!NOTE]
> 根據用戶端的意見反應，預設會關閉空間感知系統，這是一種有趣的視覺效果，但通常會將其關閉，以避免視覺干擾以及將它開啟的額外效能衝擊。 您可以遵循 [此處的指示](../SpatialAwareness/SpatialAwarenessGettingStarted.md)來重新啟用系統。
