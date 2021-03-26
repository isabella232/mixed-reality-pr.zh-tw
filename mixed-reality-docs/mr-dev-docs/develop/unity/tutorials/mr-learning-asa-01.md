---
title: Azure Spatial Anchors 教學課程簡介
description: 完成此課程以了解如何在混合實境應用程式中實作 Azure Spatial Anchors。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens, MRTK, 混合實境工具組, UWP, Azure 空間錨點, ios, android, Windows 10, ARCore, macOS, Android 建置支援, ARKit
ms.localizationpriority: high
ms.openlocfilehash: 263575653df8fe22f2c59a00443d788c6598721b
ms.sourcegitcommit: ac315c1d35f2b9c431e79bc3f1212215301bb867
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105550338"
---
# <a name="1-introduction-to-the-azure-spatial-anchors-tutorials"></a>1.Azure Spatial Anchors 教學課程簡介

歡迎使用 Azure Spatial Anchors 教學課程！ 透過本教學課程系列，您將了解 <a href="https://azure.microsoft.com/services/spatial-anchors" target="_blank">Azure Spatial Anchors</a> (ASA) 的基本概念，以及如何在真實世界中錨定完整的混合實境體驗。 您也將了解如何將專案部署至 Android 和 iOS。

本系列的教學課程：

1. [簡介](mr-learning-asa-01.md) (您正在此教學課程中)
2. [開始使用 Azure Spatial Anchors](mr-learning-asa-02.md)
3. [儲存、擷取和共用 Azure Spatial Anchors](mr-learning-asa-03.md)
4. [顯示 Azure Spatial Anchor 意見反應](mr-learning-asa-04.md)
5. [適用於 Android 和 iOS 的 Azure Spatial Anchors](mr-learning-asa-05.md)

## <a name="objectives"></a>目標

* 了解如何建立空間錨點，並從 Azure 提取這些錨點
* 了解如何跨多個應用程式工作階段來對齊空間
* 了解如何在多個裝置之間對齊空間
* 了解如何準備和置專案，並部署至 Android 和 iOS

## <a name="prerequisites"></a>必要條件

* 已[安裝正確工具](../../install-the-tools.md)的 Windows 10 電腦
* Windows 10 SDK 10.0.18362.0 或更新版本
* 已[針對開發而設定](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)的 HoloLens 2 裝置
* 已安裝 Unity 2019 LTS 的 <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a>，且已新增通用 Windows 平台組建支援模組
* 完成[建立空間錨點資源](/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource)一節，其位於[教學課程：建立使用 Azure Spatial Anchors 的 Unity HoloLens 應用程式](/azure/spatial-anchors/quickstarts/get-started-unity-hololens)
* 完成[使用者入門教學課程](mr-learning-base-01.md)系列或一些基本的 Unity 和 MRTK 體驗
* 如果想要部署至 Android 及 HoloLens
  * 已啟用<a href="https://developer.android.com/studio/debug/dev-options" target="_blank">開發人員</a>和具有 <a href="https://developers.google.com/ar/discover/supported-devices" target="_blank">ARCore 功能</a>的 Android 裝置，可透過 USB 連接至您的 Windows 或 macOS 電腦
  * 已安裝 unity 2019 LTS 的<a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity 中樞</a>，並已新增 Android 組建支援模組
* 如果想要部署至 iOS 及 HoloLens
  * 已安裝最新版 <a href="https://geo.itunes.apple.com/us/app/xcode/id497799835?mt=12" target="_blank">Xcode</a> 和 <a href="https://cocoapods.org" target="_blank">CocoaPods</a> 的 macOS 電腦
  * <a href="https://developer.apple.com/documentation/arkit/verifying_device_support_and_user_permission" target="_blank">ARKit 相容</a>的 iOS 裝置可透過 USB 連接至您的 macOS 電腦
  * 已安裝 unity 2019 LTS 的<a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity 中樞</a>，並已新增 IOS 組建支援模組

> [!CAUTION]
> 本教學課程系列的建議混合現實工具組版本為 MRTK 2.6。

> [!CAUTION]
> 本教學課程系列的建議 Unity 版本是 Unity 2019 LTS 這會取代上述必要條件中所述的任何 Unity 版本需求。

> [!div class="nextstepaction"]
> [下一個教學課程：2.開始使用 Azure Spatial Anchors](mr-learning-asa-02.md)