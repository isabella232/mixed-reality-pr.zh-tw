---
title: 適用於 VR 的 Unity 開發
description: 開始在 Unity 中建立適用於 VR 和 Windows Mixed Reality 沉浸式頭戴裝置的混合實境應用程式。
author: hferrone
ms.author: kurtie
ms.date: 12/11/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unity, 混合實境, 開發, 開始使用, 新專案, 移植, 功能, 相機, 模擬, 模擬, 文件, 混合實境頭戴式裝置, windows 混合實境頭戴式裝置, 虛擬實境頭戴式裝置, 什麼是虛擬實境, 什麼是擴增實境, MRTK, 混合實境工具組, 語音輸入, 定位相機, 模擬器, Azure, 教學課程
ms.openlocfilehash: bef2e3288730fdc4fa79494d441941a0bcfede2a
ms.sourcegitcommit: 6ade7e8ebab7003fc24f9e0b5fa81d091369622c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2021
ms.locfileid: "112394452"
---
# <a name="unity-development-for-vr-and-windows-mixed-reality"></a>適用於 VR 和 Windows Mixed Reality 的 Unity 開發

![Unity 橫幅標誌](../images/unity_logo_banner.png)

如果您是首次接觸 Unity，建議您先探索 Unity 學習平台上的入門級[教學課程](https://unity3d.com/learn/tutorials)，再繼續操作。 您也可以造訪 [Unity Mixed Reality 論壇](https://forum.unity3d.com/forums/hololens.102/)，與建置混合實境應用程式的線上社群交流。 您絕對想不到在這裡會發現哪些絕佳的資產或解決方案。 當您準備好開始使用 MRTK 時，請前往以下開發檢查點！

> [!IMPORTANT]
> 如果您想要將現有的 Unity 專案導入 Windows Mixed Reality 沉浸式頭戴裝置中，請參閱我們的 **[移植指南](../porting-apps/porting-overview.md)** 。 

## <a name="development-checkpoints"></a>開發檢查點

使用下列檢查點，將您的 Unity 遊戲和應用程式融入混合實境的世界中。

### <a name="1-getting-started"></a>1.開始使用

您需要針對 Windows Mixed Reality 和 VR 開發進行手動變更的一小部分 Unity 設定。 這些設定分成兩個類別：每個專案和每個場景。 在本節結束時，您將具有工具和專案設定，可以開始建立自己的應用程式！

|  Checkpoint  |  結果  |
| --- | --- |
| [安裝最新工具](../install-the-tools.md) | 下載並安裝最新的 Unity 套件，並設定您的混合實境專案 |
| [針對 VR 和 Windows Mixed Reality 耳機設定您的專案](/windows/mixed-reality/develop/unity/xr-project-setup?tabs=openxr) | 了解如何建置可在全像攝影和 VR 顯示裝置上呈現數位內容的應用程式 |

> [!IMPORTANT]
> 如需設定專案的詳細資訊，請參閱我們的 Unity 專案設定 [指南](choosing-unity-version.md) 。

### <a name="2-core-building-blocks"></a>2.核心基本要素

開始新的沉浸式專案之後，您需要一些基本的建構元素來開發沉浸式應用程式。 混合實境應用程式的所有核心建置組塊都會以與其他 Unity API 一致的方式公開。 您目前可能不需用到所有功能，但建議您及早探索。 深入探討下列核心建構元素後，您將了解如何將包含多樣化功能的工具箱整合到 VR 專案中。

|  功能  |  功能  |
| --- | --- |
| [相機](../unity/camera-in-unity.md) | 完整最佳化混合實境應用程式中的視覺品質和全像攝影穩定性 |
| [世界鎖定和空間錨點](spatial-anchors-in-unity.md) | 解決穩定問題、攝影機調整，以及整合穩定的座標系統解決方案 || [運動控制器](../unity/motion-controllers-in-unity.md) | 將空間動作新增至混合實境應用程式 |
| [手勢](../unity/gestures-in-unity.md) | 在混合實境體驗中使用手勢作為輸入 |
| [空間音效](../unity/spatial-sound-in-unity.md) | 利用沉浸式 3D 音訊增強您的應用程式 |
| [Text](../unity/text-in-unity.md) | 取得可管理大小且具有效轉譯的清晰、高品質文字 |
| [語音輸入](../unity/voice-input-in-unity.md) | 擷取使用者說出的關鍵字、片語和指令|

### <a name="3-advanced-features"></a>3.進階功能

在沉浸式應用程式中各有作用的其他重要功能可透過 Unity API 來使用，不需要任何額外的封裝或設定。 深入了解 Unity 提供的進階功能後，您將能夠建置更有深度的複雜 VR 應用程式。

|  功能  |  功能  |
| --- | --- |
| [追蹤遺失](tracking-loss-in-unity.md) | 處理您的裝置無法在應用程式環境的空間中找到本身所在位置的狀況 |
| [鍵盤輸入](keyboard-input-in-unity.md) | 在您的應用程式中取得實際環境和混合實境鍵盤的輸入 |

### <a name="4-deploying-to-a-device-or-emulator"></a>4.部署至裝置或模擬器

當您的全像攝影 Unity 專案準備好進行測試之後，下一步就是匯出和建置 Unity Visual Studio 解決方案。 有了該 VS 解決方案，您就可以在真正或模擬的裝置上執行您的應用程式。 在本節結束時，您將能夠在裝置或模擬器上部署您的應用程式，以符合您的開發需求。

* [Windows Mixed Reality 沉浸式頭戴裝置](../platform-capabilities-and-apis/using-visual-studio.md)
* [Windows 混合實境沉浸式頭戴裝置模擬器](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)

## <a name="whats-next"></a>接下來要做什麼？

開發人員的工作無止境，在學習新工具或 SDK 方面尤其如此。 完成入門級教學後，以下各節將帶領您前往更深入的領域，並提供有用的資源協助您脫離瓶頸。 請注意，這些主題和資源無須依序使用，您可以隨意來回參考並探索！

### <a name="porting"></a>移植

如果您有想要移植的現有應用程式，您接下來即應參考下列文章：

* [將 VR 應用程式移植到 Windows Mixed Reality](../porting-apps/porting-guides.md?tabs=project)
* [更新 Windows Mixed Reality 的 SteamVR 應用程式](../porting-apps/updating-your-steamvr-application-for-windows-mixed-reality.md)

### <a name="additional-resources"></a>其他資源

在您自行進入混合實境的世界之前，建議您先參閱下列額外文件。 

* [VR 愛好者指南](/windows/mixed-reality/enthusiast-guide/vr-journey)
* [Unity Asset Store](https://assetstore.unity.com)

## <a name="see-also"></a>另請參閱 

* [Unity 的建議設定](recommended-settings-for-unity.md)
* [對 Unity 的效能建議](performance-recommendations-for-unity.md)
* [匯出和建置 Unity Visual Studio 解決方案](exporting-and-building-a-unity-visual-studio-solution.md)
* [使用 Unity 和 Visual Studio 的最佳作法](best-practices-for-working-with-unity-and-visual-studio.md)