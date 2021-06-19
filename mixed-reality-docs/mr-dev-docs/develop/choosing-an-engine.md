---
title: 選擇您的引擎
description: 介紹適用于 HoloLens 和 VR 混合現實開發的引擎選項。
author: hferrone
ms.author: v-hferrone
ms.date: 04/22/2021
ms.topic: article
keywords: mixedrealitytoolkit、mixedrealitytoolkit-unity、mixed reality 耳機、windows mixed reality 耳機、虛擬實境耳機、unity
ms.openlocfilehash: c91a4df9db8ef71778421750bca48d81d4b4a02e
ms.sourcegitcommit: 6ade7e8ebab7003fc24f9e0b5fa81d091369622c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2021
ms.locfileid: "112394522"
---
# <a name="choosing-your-engine"></a>選擇您的引擎

您可以透過我們的文件採用數個開發路徑。 第一個步驟是尋找最適合您的技術。 如果您已有屬意的技術，請直接跳到下方與其對應的索引標籤。 如果您抱持觀望態度或才剛開始，請逐一查看每項技術並了解其所提供的內容、可用的平台和工具，然後開始建立！

> [!IMPORTANT]
> 如果您有現有專案要帶到 HoloLens 2 或沉浸式 VR頭戴式裝置 (例如 Reverb G2)，請參閱我們的 **[移植指南概觀](porting-apps/porting-overview.md)** 。 對於使用 HTK、MRTK v1、SteamVR 的專案，或針對沉浸式頭戴裝置 (例如 Oculus Rift 或 HTC Vive) 開發的專案，我們都提供了相關指南。

## <a name="engine-overview"></a>引擎概觀

* **Unity** 是市場上領先的即時開發平臺之一，其基礎執行時間程式碼是以 c + + 撰寫，而所有開發腳本都是在 c # 中完成。 無論您想要打造遊戲、電影和動畫電影藝術，甚至要在虛擬世界中轉譯架構或工程概念，Unity 都有可支援您的基礎結構。

* **Unreal Engine 4** 是功能強大的開放原始碼建立引擎，在 c + + 和藍圖中都有混合現實的完整支援。 從 Unreal Engine 4.25 開始，HoloLens 支援已具備完整功能且可供生產環境使用。 藉由使用靈活的 Blueprints Visual Scripting 系統功能，設計人員幾乎可以使用通常僅適用於程式設計人員的完整概念和工具。 各行各業的建立者可以利用自由和控制來提供最先進的內容、互動式體驗和沉浸式虛擬世界。

* 具有撰寫專屬3D 轉譯器經驗的 **原生** 開發人員可以使用 OpenXR 來建立自訂引擎。 OpenXR 是 Khronos 中開放且免權利金的 API 標準，可讓引擎以原生方式對多個跨混合實境頻譜的廠商存取其中各種裝置。 您可以在 HoloLens 2 上使用 OpenXR 或在電腦上使用 Windows Mixed Reality 沉浸式頭戴裝置進行開發。

* 建立吸引人的跨瀏覽器 AR/VR web 體驗的 **web** 開發人員可以使用 **WebXR**。

    > [!NOTE]
    > HoloLens 開發的 **Babylon.js** 正在進行中。 查看 [最新消息，並參與此社區](https://doc.babylonjs.com/divingDeeper/webXR/introToWebXR)！

<!-- Babylon is a Javascript-based, open source, 3D graphics engine capable of powering 3D scenes in a web browser. Babylon.js 4.2+ includes support for WebXR. With Babylon React Native, you can even build cross-platform native     applications for PC, mobile, and mixed reality devices. -->

## <a name="features-and-devices"></a>功能和裝置

<br>

| 後勤 | Unity | Unreal | JavaScript | 自訂引擎 <br>使用 OpenXR)  ( |
|---|---|---|---|---|
| 語言 | C# | C++ | JavaScript | C/C++ |
| 定價 | [Unity 定價](https://store.unity.com/#plans-individual) | [Unreal 定價](https://www.unrealengine.com/download) | 免費 | 免費 |

<br>

| 裝置功能 | Unity | Unreal | JavaScript | 自訂引擎 <br>使用 OpenXR)  ( |
|---|---|---|---|---|
| 裝置/顯示追蹤 | ✔️ | ✔️ | ✔️ | ✔️ |
| 手輸入 | ✔️ | ✔️ | ✔️ | ✔️ |
| 眼睛輸入 | ✔️ | ✔️ | ❌ | ✔️ |
| 語音輸入 | ✔️ | ✔️ | ✔️ | ✔️ |
| 運動控制器 | ✔️ | ✔️ | ✔️ | ✔️ |
| 平面/網格點擊測試 | ✔️ | ✔️ | ✔️ | ✔️ |
| 場景理解 | ✔️ | ✔️ | ❌ | ✔️ |
| 空間音效 | ✔️ | ✔️ | ✔️ | ✔️ |
| QR 代碼偵測 | ✔️ | ✔️ | ❌ | ✔️ |

<br>

| 硬體 | Unity | Unreal | JavaScript | 自訂引擎 <br>使用 OpenXR)  ( |
|---|---|---|---|---|
| HoloLens 2 | ✔️ | ✔️ | ✔️ | ✔️ |
| HoloLens (第 1 代) | ✔️ | ✔️ | ❌ | WinRT (舊版)  |
| [Windows Mixed Reality 頭戴式裝置](../discover/immersive-headset-hardware-details.md) | ✔️ | ✔️ | ✔️ | ✔️ |
| SteamVR 耳機 | ✔️ | ✔️ | ✔️ | ✔️ |
| Oculus 的追求/Rift | ✔️ | ✔️ | ✔️ | ✔️ |
| Mobile (ARCore/ARKit)  | ✔️ | ✔️ | ✔️ | ❌ |

<br>

| 工具 | Unity | Unreal | JavaScript | 自訂引擎 <br>使用 OpenXR)  ( |
|---|---|---|---|---|
| 混合實境工具組 | ✔️ | ✔️ | ❌  | ❌ |
| 全球鎖定工具 | ✔️ | ❌ | ❌  | ❌ |
<!-- | 網狀 | ❌ | ❌ | ❌ | ❌ | -->

<br>

| 雲端服務 | Unity | Unreal | JavaScript | 自訂引擎 <br>使用 OpenXR)  ( |
|---|---|---|---|---|
| Azure Spatial Anchors | ✔️ | ✔️ | ❌ | ✔️ |
| Azure 物件錨點 | ✔️ | ❌ | ❌ | ✔️ |
| Azure 遠端轉譯 | ✔️ * | ❌ | ❌ | ✔️ * |

> [!NOTE]
> * 在 Unity) 中使用舊版 WinRT Api (Windows XR 外掛程式的應用程式目前支援 Azure 遠端轉譯。 OpenXR apps 的 ARR 支援即將推出。

## <a name="next-steps"></a>後續步驟

[!INCLUDE[](includes/tools-next-steps.md)]