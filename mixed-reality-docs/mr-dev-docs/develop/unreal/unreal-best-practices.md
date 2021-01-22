---
title: 一般最佳作法
description: 隨時掌握在 Unreal 引擎中開發混合現實應用程式的最新建議最佳作法。
author: hferrone
ms.author: safarooq
ms.date: 01/08/2021
ms.topic: article
ms.localizationpriority: high
keywords: Unreal、Unreal Engine 4、editor extensions、Unreal editor、UE4、HoloLens、HoloLens 2、mixed reality、開發、檔、指南、功能、混合現實耳機、windows mixed reality 耳機、虛擬實境耳機、移植、升級
ms.openlocfilehash: 478ae3137fc73d1ef516087618ab0247f2164c02
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/20/2021
ms.locfileid: "98584791"
---
# <a name="general-best-practices"></a>一般最佳作法

以下是我們建議所有開發人員在建立混合現實的 Unreal 引擎專案時所遵循的一般最佳作法。

## <a name="constructors"></a>建構函式

如果您需要藍圖中的「函式」對等專案，請使用 Unreals 的 [結構腳本](https://docs.unrealengine.com/ProgrammingAndScripting/Blueprints/UserGuide/UserConstructionScript/index.html)。 使用 "BeginPlay" 事件的主要優點是，函式腳本也會在「編輯器」中執行。 大部分的時間都可以在一開始或甚至編譯時期快取。

> [!NOTE]
> 您可以在 [編輯器延伸模組總覽](unreal-editor-extensions.md#construction-scripts)中找到更多的結構腳本支援資訊。

## <a name="3d-buttons-and-textures"></a>3D 按鈕和紋理

在混合現實應用程式中建立或規劃使用3D 按鈕時，最好考慮效能。 不過，並非所有東西都必須從網格中被視為3D。 您可以選擇使用 Paper2D 和精心製作的紋理來取得3D 外觀。 這非常適合「看似」3D 的按鈕，但只是在四個 photoshopped 影像。 這類的奇特版本稱為 [sprite](https://docs.unrealengine.com/AnimatingObjects/Paper2D/Sprites/index.html)。

## <a name="variants"></a>變異

如果您要在執行時間建立具有多個物件設定的場景，請使用 [Unreal](https://docs.unrealengine.com/Basics/Levels/Variants/index.html) 變異。 變化可以包含變更的材質或網格。 

## <a name="animation"></a>動畫

如果您要建立許多「互動動畫」，請利用 [曲線元件](https://docs.unrealengine.com/API/Runtime/Engine/Components/USplineComponent/index.html) (不是曲線「網格」元件) 和 [時間軸節點](https://docs.unrealengine.com/ProgrammingAndScripting/Blueprints/UserGuide/Timelines/index.html) 。 

<!-- You can find a comprehensive [video tutorial here](https://www.youtube.com/watch?v=bWXI91FdMtk&ab_channel=DoubleCrossGames). -->

## <a name="communications"></a>通訊

如果您在多個動作專案和藍圖之間動態尋找物件或使用太多頻寬來進行通訊，請使用 [層級藍圖](https://docs.unrealengine.com/ProgrammingAndScripting/Blueprints/UserGuide/Types/LevelBlueprint/index.html) 。 請記住，Unreal Engine 4 不像 Unity，並非所有專案都必須在元件中。 層級藍圖是完全有效且建議的方式，可簡化多個執行者之間的通訊。 在層級藍圖的 OnBeginPlay 中啟動時，物件參考甚至可以「快取」。

## <a name="global-state"></a>全域狀態

您通常需要儲存層級特定的狀態，例如分數、層級資料、播放機特定資訊，或任何其他不屬於特定物件的內容。 不要忽略 [GameMode](https://docs.unrealengine.com/en-US/InteractiveExperiences/Framework/GameMode/index.html)。 大部分的人都忘記它存在，但是 GameMode 可以針對每個層級建立，並且包含每個層級的特定資料。

## <a name="optimizing-blueprints"></a>優化藍圖

如果您發現藍圖的速度太慢，請先 Unreal 「nativize」您的藍圖，再利用 c + + 重寫程式碼。 在建立您自己的自訂解決方案之前，請先嘗試使用自動 [nativization](https://docs.unrealengine.com/ProgrammingAndScripting/Blueprints/TechnicalGuide/NativizingBlueprints/index.html) 。

![藍圖設定，具有醒目提示內含的藍圖 nativization 方法](images/unreal-general-practices-img-01.jpg)
