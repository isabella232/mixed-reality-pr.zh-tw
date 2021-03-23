---
title: Profiles
description: MRTK 中的檔設定檔
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、設定檔、
ms.openlocfilehash: 384614f27c099af197ea8a9aedc72c711f0c099e
ms.sourcegitcommit: f74d33d50c1fbfebe8571695d631ce78dd599f74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/23/2021
ms.locfileid: "104881225"
---
# <a name="profiles"></a>Profiles

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Introduction-to-MRTK-Profiles/player]

設定 MRTK 的主要方式之一是透過基礎套件中提供的設定檔。 [`MixedRealityToolkit`](xref:Microsoft.MixedReality.Toolkit.MixedRealityToolkit)場景中的主要物件會有使用中的設定檔，也就是 ScriptableObject。 最上層 MRTK 設定檔包含主要核心系統每個核心的子設定檔資料，每一個核心系統都是設計來設定其對應子系統的行為。 此外，這些子設定檔也會 ScriptableObjects，因此可包含其下一個層級之其他設定檔物件的參考。 基本上，有一個連線設定檔的整個樹狀結構，這些設定檔會組成設定資訊，以說明如何初始化 MRTK 子系統和功能。

例如，輸入系統的行為是由輸入系統設定檔所控制，例如 `DefaultMixedRealityInputSystemProfile` (資產/MRTK/SDK/設定檔) 。

<img src="../images/profiles/input_profile.png" width="650px" alt="Input profile" style="display:block;">
<sup>設定檔偵測器</sup>

## <a name="background"></a>背景

設定檔主要是用來支援跨多個裝置的特定案例，這些裝置會透過資料提供者來處理。 如此一來，應用程式就可以盡可能地設計為裝置 agnosticly，並讓 MRTK 和設定檔的資料提供者處理跨平臺支援。

另外還有一些設定檔是根據特定裝置的輸入功能來建立的，例如預設為 GGV 樣式互動的 HoloLens 1 設定檔。

## <a name="xr-sdk"></a>XR SDK

目前有兩個設定檔提供給 XR SDK `DefaultXRSDKConfigurationProfile` 和 `DefaultHoloLens2XRSDKConfigurationProfile` 。 如此一來，就不會因為場景和案例特定的設定而完全支援所有的範例場景。 任何使用和的範例都 `DefaultMixedRealityToolkitConfigurationProfile` `DefaultHoloLens2ConfigurationProfile` _可以_ 交換至其對應的 XR SDK 設定檔。 如果您是使用 OpenXR 搭配 XR SDK，請改用 `DefaultOpenXRConfigurationProfile` 。

正在進行額外的工作，以簡化設定並支援所有範例場景，讓舊版 XR 和 XR SDK 可以並存設定。 請參閱追蹤的問題 [#9419](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9419) 。

如需在舊版 XR 和 XR SDK 之間轉換設定檔的詳細資訊，請參閱設定 [XR SDK 管線的 MRTK](../../configuration/getting-started-with-mrtk-and-xrsdk.md#configuring-mrtk-for-the-xr-sdk-pipeline) 。

## <a name="default-profile"></a>預設設定檔

MRTK 會提供一組預設設定檔，其中涵蓋 MRTK 支援的大部分平臺和案例。 例如，當您選取 `DefaultMixedRealityToolkitConfigurationProfile` (資產/MRTK/SDK/設定檔時) 您將能夠在 VR 上試用案例 (OpenVR、WMR) 和 HoloLens (1 和 2) 。

請注意，因為這是一般用途的設定檔，所以不會針對任何特定使用案例進行優化。 如果您想要在其他平臺上擁有更佳的效能/特定設定，請參閱下列其他設定檔，這些設定檔會在其各自的平臺上稍微調整得更好。

## <a name="hololens-2-profile"></a>HoloLens 2 設定檔

MRTK 也提供已針對 HoloLens 2： `DefaultHoloLens2ConfigurationProfile` (資產/MRTK/SDK/設定檔/HoloLens2) 進行部署和測試的預設設定檔。

當系統提示您選擇 MixedRealityToolkit 物件的設定檔時，請使用此設定檔，而不是預設選取的設定檔。

HoloLens2 設定檔和預設設定檔之間的主要差異如下：

**停用** 的功能：

- [界限系統](../boundary/boundary-system-getting-started.md)
- [傳送系統](../teleport-system/teleport-system.md)
- [空間感知系統](../spatial-awareness/spatial-awareness-getting-started.md)
- 因效能額外負荷而 ([手上網格視覺效果](../input/hand-tracking.md)) 

**啟用** 的系統：

- [眼睛追蹤提供者](../input/eye-tracking/eye-tracking-main.md)
- 目視輸入模擬

攝影機設定檔設定會設定為相符，因此編輯器品質和播放程式品質都相同。 這與預設攝影機設定檔不同，因為不透明顯示會設定為較高的品質。 這項變更表示在編輯器品質較低的情況下，將會更接近裝置上呈現的內容。

> [!NOTE]
> 根據用戶端的意見反應，預設會關閉空間感知系統，這是一種有趣的視覺效果，但通常會將其關閉，以避免視覺干擾以及將它開啟的額外效能衝擊。 您可以遵循 [此處的指示](../spatial-awareness/spatial-awareness-getting-started.md)來重新啟用系統。
