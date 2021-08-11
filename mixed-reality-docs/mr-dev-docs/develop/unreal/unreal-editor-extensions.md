---
title: Unreal 中的編輯器延伸模組
description: 瞭解如何使用自訂腳本、腳本動作和公用程式 widget 來擴充 Unreal 引擎編輯器。
author: hferrone
ms.author: safarooq
ms.date: 01/08/2021
ms.topic: article
ms.localizationpriority: high
keywords: Unreal、Unreal Engine 4、editor extensions、Unreal editor、UE4、HoloLens、HoloLens 2、mixed reality、開發、檔、指南、功能、混合現實耳機、windows mixed reality 耳機、虛擬實境耳機、移植、升級
ms.openlocfilehash: 91d9a84e4e19cb7f0f2bf54060b45da1767b8d50cdfeb5655f5e58a29d45a702
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2021
ms.locfileid: "115226620"
---
# <a name="editor-extensions-in-unreal"></a>Unreal 中的編輯器延伸模組

Unreal 提供一組豐富的功能，可讓您自訂引擎以滿足您的需求。 這些功能的範圍從簡單但有限，到功能強大但複雜。 下列步驟會依複雜度的順序列出。 一般來說，在移至更複雜的選項之前，您應該先觸及問題的更簡單解決方案，並耗盡其選項。 舉例而言，我們發現基本的結構腳本可以用來代替大部分的外掛程式。 

<!-- Also, engine modification should be a last resort, as it is not only complex, but integrating changes back into the engine for simple work-around can take a disproportionately long time. -->

## <a name="construction-scripts"></a>結構腳本

您可以使用結構腳本來執行建立藍圖實例時所執行的初始化動作。

* [使用者結構腳本](https://docs.unrealengine.com/ProgrammingAndScripting/Blueprints/UserGuide/UserConstructionScript/index.html)
* [藍圖範例](https://docs.unrealengine.com/Resources/ContentExamples/Blueprints/1_4/index.html)
* [影片教學課程](https://www.youtube.com/watch?v=z1SD-d9yJmQ&ab_channel=UnrealEngine)

## <a name="scripted-actions"></a>腳本的動作

編寫腳本的動作為編輯器公用程式藍圖。 您可以在 [Unreal 編輯器] 中啟動它們，方法如下：
* 在內容瀏覽器中以滑鼠右鍵按一下 [ **資產** ]
* 或者，以滑鼠右鍵 **按一下層** 級區或世界 Outliner 中的動作專案

當您需要藍圖邏輯對資產或動作專案的集合具有內容感知時，腳本的動作是唯一適用的時機。 一般而言，已編寫腳本的動作會取得您在執行動作時選取的資產或動作專案清單，然後修改這些物件，或將它們視為其圖形。

* [腳本的動作](https://docs.unrealengine.com/ProductionPipelines/ScriptingAndAutomation/Blueprints/ScriptedActions/index.html)
* [在專案啟動時執行腳本的動作](https://docs.unrealengine.com/ProductionPipelines/ScriptingAndAutomation/Blueprints/StartupObjects/index.html)

## <a name="editor-utility-widgets"></a>編輯器公用程式小工具

每當您想要加入新的 UI 元素，以修改 Unreal 編輯器的消費者介面 (UI) 時，您都可以使用 [編輯器公用程式小工具](https://docs.unrealengine.com/InteractiveExperiences/UMG/UserGuide/EditorUtilityWidgets/index.html) 。 編輯器公用程式 widget 以 Unreal 動畫圖形為基礎， (UMG) ，因此您可以在藍圖中設定 widget，如同任何其他 UMG Widget 藍圖一樣。

這些小工具專為編輯器 UI 而設計，您可以使用它們來建立自訂編輯器索引標籤。 然後，您可以從 Windows] 功能表中選取這些自訂索引標籤，就像您選取現有的編輯器索引標籤一樣。

## <a name="plugins"></a>外掛程式

Unreal 可讓您開發及管理您自己的自訂 [外掛程式](https://docs.unrealengine.com/ProductionPipelines/Plugins/index.html) ，以搭配 UE4 工具和執行時間使用。 您可以隨時在 [Unreal 編輯器] 中啟用或停用外掛程式。 外掛程式可以新增執行時間遊戲功能、修改內建引擎功能、建立新的檔案類型，以及擴充編輯器的功能。

<!-- ## Engine modifications -->

