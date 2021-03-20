---
title: ExampleHub
description: MRTK 中的範例場景總覽
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: 4f55718e0fe9bebca2ff9e2850057e83a3f4b6bb
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104684682"
---
# <a name="mrtk-examples-hub"></a>MRTK 範例中樞

![MRTK 範例中樞](../images/examples-hub/MRTK_ExamplesHub.png)

MRTK 範例中樞是 Unity 場景，可讓您輕鬆體驗多個場景。 它會使用 MRTK 的場景系統來載入 & 卸載幕後。

**MRTKExamplesHub** 是具有共用元件（包括和）的容器場景 ``MixedRealityToolkit`` 。 ``MixedRealityPlayspace`` **MRTKExamplesHubMainMenu： unity** 場景具有 cube 按鈕。

## <a name="prerequisite"></a>必要條件

MRTK 範例中樞使用 [場景轉換服務](../extensions/scene-transition-service.md) 和相關的腳本。 如果您是透過 Unity 套件使用 MRTK，請匯入 MixedReality 的 [發行套件](https://github.com/microsoft/MixedRealityToolkit-Unity/releases)中所包含的 node.js.. x. **unitypackage** 。 如果您是透過儲存機制複製來使用 MRTK，您的專案中應該已經有 **MRTK/Extensions** 資料夾。

## <a name="mrtkexampleshub-scene-and-the-scene-system"></a>MRTKExamplesHub 場景和場景系統

開啟 **MRTKExamplesHub** ，其位於 `MRTK/Examples/Experimental/Demos/ExamplesHub/Scenes/` MixedRealityToolkit、MixedRealityPlayspace 和 LoadHubOnStartup 的空白場景中。 此場景已設定為使用 MRTK 的場景系統。 按一下 [MixedRealityToolkit] 底下的 [] `MixedRealitySceneSystem` 。 它會在 [偵測器] 面板中顯示場景系統的資訊。

<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_Hierarchy.png" width="300" alt="Example Hub Hierarchy">
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_Inspector1.png" width="450" alt="Inspector 1">

在偵測器底部，會顯示場景系統設定檔中定義的場景清單。 您可以按一下場景名稱以載入/卸載它們。

<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_Inspector2.png" width="550" alt="Inspector 2">
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem3.png" alt="Scene system 3">按一下清單中的場景名稱載入 _MRTKExamplesHub_ 場景的範例。
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem4.png" alt="Scene system 4">載入 _HandInteractionExamples_ 場景的範例。
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem5.png" alt="Scene system 5">
載入多個場景的範例。

## <a name="running-the-scene"></a>執行場景

此場景適用于 Unity 的遊戲模式和裝置。 在 Unity 編輯器中執行 **MRTKExamplesHub** 場景，並使用 MRTK 的輸入模擬來與場景內容互動。 若要建立和部署，只要使用場景系統清單中所包含的其他場景來建立 **MRTKExamplesHub** 場景即可。 偵測器也可讓您輕鬆地將場景新增至組建設定。 在 [建築設定] 中，確定 **MRTKExamplesHub** 場景位於清單的最上方（索引0）。

<img src="../images/examples-hub/MRTK_ExamplesHub_BuildSettings.png" width="450" alt="Build settings">

## <a name="how-mrtkexampleshub-loads-a-scene"></a>MRTKExamplesHub 如何載入場景

在 **MRTKExamplesHub** 場景中，您可以找到 ``ExamplesHubButton`` 預製專案。
預製專案中有一個 **FrontPlate** 物件，其中包含 ``Interactable`` 。
使用互動的 ``OnClick()`` 和 ``OnTouch()`` 事件，它會觸發 **LoadContentScene** 腳本的 **LoadContent ()** 函式。
在 **LoadContentScene** 腳本的偵測器中，您可以定義要載入的場景名稱。

<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem6.png" alt="Scene system 6">
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem8.png" width="450" alt="Scene System 8">
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem7.png" width="450" alt="Scene System 7">

腳本會使用場景系統的 LoadContent () 函式來載入場景。
如需詳細資訊，請參閱 [場景系統](../scene-system/scene-system-getting-started.md) 頁面。

```c#
MixedRealityToolkit.SceneSystem.LoadContent(contentName, loadSceneMode);
```

## <a name="returning-to-the-main-menu-scene"></a>返回主功能表場景

若要返回主功能表場景 (MRTKExamplesHubMainMenu 場景) ，您可以使用相同的場景系統 `LoadContent()` 方法。 **ToggleFeaturesPanelExamplesHub. 預製專案** 會提供包含 **LoadContentScene** 腳本的 [Home （首頁）] 按鈕。 您可以使用此預製專案，或在每個場景中提供自訂的 [首頁] 按鈕，以允許使用者返回主要場景。 您可以將 **ToggleFeaturesPanelExamplesHub 預製專案** 在 **MRTKExamplesHub** 場景中，讓它永遠可見，因為 **MRTKExamplesHub** 是共用的容器場景。 請務必在每個範例場景中隱藏/停用 **ToggleFeaturesPanel。預製專案。**

<img src="../images/examples-hub/MRTK_ExamplesHubToggleFeaturesPanel.png" alt="Toggle feature Panel">

<img src="../images/examples-hub/MRTK_ExamplesHubHomeButton.png" width="450" alt="Example Hub home button">

## <a name="adding-additional-buttons"></a>新增其他按鈕

在 **CubeCollection** 物件中，重複 (或新增) _ExampleHubButton_ prefabs，然後按一下中的 [ **更新集合** ] `GridObjectCollection` 。
這會根據新的按鈕總數來更新圓柱版面配置。
如需詳細資料，請參閱 [ [物件集合](../ux-building-blocks/object-collection.md) ] 頁面。

<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem9.png" alt="Scene System 9">
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem10.png" alt="Scene System 10">

新增按鈕之後，請更新 **LoadContentScene** 腳本中的場景名稱， (上述) 所述。
將其他場景新增至場景系統的設定檔。
