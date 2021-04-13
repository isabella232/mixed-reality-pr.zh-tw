---
title: 入門教學課程 - 3。 設定 MRTK 設定檔
description: 本課程說明如何設定混合實境工具組 (MRTK) 設定檔。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens, MRTK, 混合實境工具組, UWP, 空間感知
ms.localizationpriority: high
ms.openlocfilehash: f6c17dc361846808ec10f1d94932e3089072e642
ms.sourcegitcommit: 1c9035487270af76c6eaba11b11f6fc56c008135
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/13/2021
ms.locfileid: "107300453"
---
# <a name="3-configuring-the-mrtk-profiles"></a>3.設定 MRTK 設定檔

## <a name="overview"></a>概觀

在本教學課程中，您將了解如何自訂和設定 MRTK 設定檔。

<a href="/windows/mixed-reality/mrtk-unity/features/profiles/profiles" target="_blank">MRTK 設定檔</a>是巢狀設定檔的樹狀結構，其構成了 MRTK 系統和功能應如何初始化的組態設定資訊。 最上層設定檔 (組態設定檔) 包含每個主要核心系統的巢狀設定檔。 每個巢狀設定檔都是設計來設定其對應系統的行為。

此特定範例將示範如何藉由變更空間網格觀察器的設定，來隱藏空間感知網格。 不過，您也可以遵循這些相同原則，自訂 MRTK 設定檔中的任何設定或值。

正如您在進行[上一個教學課程](mr-learning-base-02.md#congratulations)的期間將專案部署至 HoloLens 2 時所經歷的體驗，<a href="/windows/mixed-reality/mrtk-unity/features/spatial-awareness/spatial-awareness-getting-started" target="_blank">空間感知</a>網格是代表環境幾何的網格所形成的集合。 一開始，這樣的視覺效果很有用，但我們一般會將此功能關閉，以免遇到開啟此功能時所會遭遇的視覺干擾和額外的效能減損。

## <a name="objectives"></a>目標

* 了解如何自訂和設定 MRTK 設定檔
* 隱藏空間感知網格

## <a name="changing-the-spatial-awareness-display-option"></a>變更空間感知顯示選項

隱藏空間感知網格所需採取的主要步驟如下：

1. 複製預設的組態設定檔
2. 啟用空間感知系統
3. 複製預設的空間感知系統設定檔
4. 複製預設的空間感知網格觀察器設定檔
5. 變更空間感知網格的顯示

> [!NOTE]
> 根據預設，您無法編輯 MRTK 設定檔。 這些是預設的設定檔範本，您必須先加以複製，才能進行編輯。 其中有數個巢狀的設定檔層。 因此，在設定一個或多個設定時，通常會複製及編輯數個設定檔。

[!INCLUDE[](includes/configuring-profile.md)]

## <a name="congratulations"></a>恭喜！

在本教學課程中，您已了解如何複製、自訂和設定 MRTK 設定檔和設定。

> [!div class="nextstepaction"]
> [下一個教學課程：4.將物件置放在場景中](mr-learning-base-04.md)