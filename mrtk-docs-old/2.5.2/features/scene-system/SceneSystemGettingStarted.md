---
title: SceneSystemGettingStarted
description: 具有 MRTK 之場景系統的登陸頁面
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: 428fb95bad48082fad8affa8761c6e362c14bac2
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104690528"
---
# <a name="scene-system-overview"></a>場景系統總覽

## <a name="when-to-use-the-scene-system"></a>使用場景系統的時機

如果您的專案包含單一場景，則可能不需要場景系統。 當下列一或多項條件成立時，最有用：

- 您的專案有多個場景。
- 您可以使用單一場景載入，但您不喜歡它終結 MixedRealityToolkit 實例的方式。
- 您需要簡單的方法來額外載入多個場景，以建立您的體驗。
- 您需要簡單的方法來追蹤進行中的載入作業，或使用簡單的方式來控制一次載入多個場景的場景啟用。
- 您想要讓燈光保持一致，並可在所有場景中預測。

## <a name="scene-system-resources"></a>場景系統資源

根據預設，場景系統會利用一對場景物件 (DefaultManagerScene 和 DefaultLighting 場景) 。 如果找不到任何一種場景，則會在場景系統設定檔偵測器中出現一則訊息。

![預設資源訊息](../images/scene-system/DefaultResourcesMessage.png)

>!記如果專案使用自訂的管理員和燈光場景，則可以放心地忽略此訊息。

下列各節將說明如何根據用來匯入混合現實工具組的方法，來解決此訊息。

### <a name="unity-package-manager-upm"></a>Unity 封裝管理員 (UPM) 

在混合現實工具組 UPM 套件中，場景系統資源會封裝成範例。 由於 UPM 套件是不可變的，因此 Unity 無法開啟必要的場景檔案，除非它們明確地匯入至專案中。

若要匯入，請使用下列步驟：

- 選取 **視窗**  >  **封裝管理員**
- 選取 **混合現實工具組基礎**
- 在 [**範例**] 區段中找出 **場景系統資源**

  ![匯入場景系統資源](../images/scene-system/UpmImportSceneSystemResources.png)

- 選取匯 **入**

### <a name="asset-unitypackage-files"></a>資產 ( unitypackage) 檔案

如果 SceneSystemResources 資料夾已被刪除，或在匯入時取消選取，則可以使用下列步驟來復原：

- 選取 **資產** 匯  >  **入套件**  >  **自訂套件**
- 開啟 **MixedReality 套件。**
- 確定已選取 [ **服務/SceneSystem/SceneSystemResources** ] 和 [所有子選項]

  ![重新匯入場景系統資源](../images/scene-system/ReimportSceneSystemResources.png)

- 選取匯 **入**

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

![場景系統編輯器設定](../images/scene-system/MRTK_SceneSystemProfileEditorSettings.PNG)
