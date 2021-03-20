---
title: SceneSystemSceneTypes
description: MRTK 中不同場景類型的檔
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: 627510d1961b48a64d3b5914f06543cf9037af32
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104693475"
---
# <a name="scene-types"></a>場景類型

場景已分成三種類型，而且每種類型都有不同的函式。

![階層中的場景系統](../images/scene-system/MRTK_SceneSystemEditorSceneHierarchy.PNG)

## <a name="content-scenes"></a>內容場景

這些是您用來處理的場景。 任何種類的內容都可以儲存在其中，而且可以任何組合載入或卸載。

預設會啟用內容幕後。 您設定檔陣列中包含的任何場景 `Content Scenes` 都可以由服務載入/卸載。

___

## <a name="manager-scenes"></a>管理員場景

具有必要 MixedRealityToolkit 實例的單一場景。 這個場景會在啟動時先載入，並且會在應用程式存留期內維持載入狀態。 管理員場景也可以裝載不應終結的其他物件。 這是 DontDestroyOnLoad 的慣用替代方法。

若要啟用這項功能，請簽 `Use Manager Scene` 入您的設定檔，並將場景物件拖曳到 `Manager Scene` 欄位中。

___

## <a name="lighting-scenes"></a>燈光場景

一組用來儲存光源資訊和光源物件的場景。 一次只能載入一個，而其設定可以在載入時混合，以進行平滑的光源轉換。

Unity 的光源設定-環境光源、skyboxes 等，在使用加法式載入時，可能難以管理，因為它們會系結至個別的場景，而覆寫行為則不直接。 在實務上，如果在執行時間未取得的照明條件中撰寫資產，則會造成混淆。

![場景系統光源設定](../images/scene-system/MRTK_SceneSystemLightingSettings.PNG)

場景系統會使用光源來確保無論在編輯模式中和在播放模式中，這些設定都維持一致。

若要啟用這項功能，請簽 `Use Lighting Scene` 入您的設定檔並填入 `Lighting Scenes` 陣列。

### <a name="cached-lighting-settings"></a>快取光源設定

您的設定檔會儲存光源設定的快取複本，並保留在燈光場景中。 如果這些設定在您的燈光場景中變更，您將需要更新快取，以確保光源在播放模式中如預期般顯示。 當您的設定檔懷疑快取設定已過期時，就會顯示警告。 按一下 `Update Cached Lighting Settings` 會載入每個光源場景、將其設定解壓縮，然後將它們儲存在您的設定檔中。

![場景系統光源設定](../images/scene-system/MRTK_SceneSystemCachedLightingSettings.PNG)

### <a name="editor-behavior"></a>編輯器行為

使用燈光場景的其中一個優點是，在編輯時，您的內容會正確地發亮。 為了達到這個目的，場景服務會隨時載入燈光場景，並將該場景的光源設定複製到目前使用中的場景。\*

您可以藉由開啟場景系統的[服務偵測器](../../configuration/mixed-reality-configuration-guide.md#editor-utilities)來變更所載入的燈光場景。 在編輯模式中，您可以立即在燈光場景之間轉換。 在 [播放] 模式中，您可以預覽轉換。

![場景系統偵測器](../images/scene-system/MRTK_SceneSystemServiceInspector.PNG)

\**注意：使用中場景通常會判斷編輯器中的光源設定。不過，我們選擇不使用這項功能來強制執行光源設定，因為使用中的場景也是新建立的物件預設放置位置，而光源場景則只允許包含光源元件。相反地，目前光源場景的設定會自動複製到使用中場景的設定。請記住，這會導致內容場景的光源設定過度寫入。*
