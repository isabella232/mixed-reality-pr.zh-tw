---
title: SceneSystemGettingStarted
description: 具有 MRTK 之場景系統的登陸頁面
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: 930f37e844992b98a0e2ea965b695734bef495e3
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/03/2021
ms.locfileid: "101780273"
---
# <a name="scene-system-overview"></a>場景系統總覽

## <a name="when-to-use-the-scene-system"></a>使用場景系統的時機

如果您的專案包含單一場景，則可能不需要場景系統。 當下列一或多項條件成立時，最有用：

- 您的專案有多個場景。
- 您可以使用單一場景載入，但您不喜歡它終結 MixedRealityToolkit 實例的方式。
- 您需要簡單的方法來額外載入多個場景，以建立您的體驗。
- 您需要簡單的方法來追蹤進行中的載入作業，或使用簡單的方式來控制一次載入多個場景的場景啟用。
- 您想要讓燈光保持一致，並可在所有場景中預測。

## <a name="how-to-use-the-scene-system"></a>如何使用場景系統

- [場景類型](SceneSystemSceneTypes.md)
- [內容場景載入](SceneSystemContentLoading.md)
- [監視內容載入](SceneSystemLoadProgress.md)
- [照明場景載入](SceneSystemLightingScenes.md)

## <a name="editor-settings"></a>編輯器設定

根據預設，場景系統會在 Unity 編輯器中強制執行數個行為。 如果您發現任何這些行為很繁重，可以在場景系統設定檔的 **編輯器設定** 區段中加以停用。

- `Editor Manage Build Settings:` 若為 true，服務會自動更新您的組建設定，以確保所有管理員、光源和內容場景都會加入。 如果您想要完全掌控組建設定，請停用此值。

- `Editor Enforce Scene Order:` 若為 true，服務將確保管理員場景先顯示在場景階層中，後面接著光源和內容。 如果您想要完全掌控場景階層，請停用此。

- `Editor Manage Loaded Scenes:` 若為 true，服務將確保一律會載入管理員、內容和光源場景。 如果您想要完全掌控編輯器中載入的場景，請停用。

- `Editor Enforce Lighting Scene Types:` 若為 true，服務將確保光源只允許在中定義光源相關的元件 `PermittedLightingSceneComponentTypes` 。 如果您想要完全掌控燈光場景的內容，請停用。

![場景系統編輯器設定](../Images/SceneSystem/MRTK_SceneSystemProfileEditorSettings.PNG)
