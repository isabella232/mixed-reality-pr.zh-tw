---
title: ReleaseNotes
description: 目前 MRTK 版本的發行 nots
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: 0d12f2cc88506af5034bfc224e45a2b59601044a
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/03/2021
ms.locfileid: "101779586"
---
# <a name="microsoft-mixed-reality-toolkit-251-release-notes"></a>Microsoft Mixed Reality 工具組2.5.1 版本資訊

- [新功能](#whats-new)
- [重大變更](#breaking-changes)
- [更新指導方針](../updates-deployment/Updating.md#upgrading-to-a-new-version-of-mrtk)
- [已知問題](#known-issues)

> [!IMPORTANT]
> 有一個已知的編譯器問題，會影響使用 ARM64 針對 Microsoft HoloLens 2 所建立的應用程式。 Visual Studio 2019 即將推出的16.8 更新會解決此問題。 在更新可用之前，請匯入套件以套用因應措施 `com.microsoft.mixedreality.toolkit.tools` 。

## <a name="whats-new"></a>最新消息

### <a name="package-dependency-errors-fixed"></a>已修正套件相依性錯誤

此版本修正不正確的套件間檔案相依性 (例如：標準資產中的檔案不再于基礎) 中正確參考檔案。 2.5.1 版也會在文字網格 Pro 上新增明確的相依性。

### <a name="standard-assets-package-shaders-copied-to-assetsmrtkshaders"></a>複製到資產/MRTK/著色器的標準資產套件著色器

當標準資產套件透過 UPM 安裝時，著色器將會複製到 [資產/MRTK/著色器] 資料夾，使其不再是不可變的。 這可解決在下一次載入專案時， (URP) 還原舊版行為的通用轉譯管線所更新的著色器問題。

### <a name="fixed-teleport-cursor-sticking-to-hands"></a>固定的傳送游標停留在手中

此版本修正了 [傳送目的地] 游標可以用來手上視覺效果的 [問題](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8755) 。

## <a name="breaking-changes"></a>重大變更

自版本2.5.0 之後，沒有任何中斷性變更。

## <a name="known-issues"></a>已知問題

### <a name="some-mixed-reality-toolkit-standard-shader-features-require-the-foundation-package"></a>部分混合現實工具組標準著色器功能需要基礎封裝

透過 Unity 套件管理員匯入時，MRTK 標準著色器公用程式腳本 (例如： HoverLight.cs) 不會與標準資產套件中的著色器共置。 若要存取此功能，應用程式將需要匯入基礎套件。

### <a name="cameracache-may-create-a-new-camera-on-shutdown"></a>CameraCache 可能會在關機時建立新的攝影機

在某些情況下 (例如在 Unity 編輯器) 中使用 LeapMotion 提供者時，CameraCache 可能會在關閉時重新建立 MainCamera。 如需詳細資訊，請參閱 [此問題](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8459) 。

### <a name="filenotfoundexception-when-examples-are-imported-via-unity-package-manager"></a>透過 Unity 套件管理員匯入範例時的 FileNotFoundException

根據專案路徑的長度，透過 Unity 套件管理員匯入範例可能會在 Unity 主控台中產生 FileNotFoundException 訊息。 造成這種情況的原因是「遺失」檔案的路徑超過 MAX_PATH (256 個字元) 。 若要解決此問題，請縮短專案路徑的長度。

### <a name="no-spatializer-was-specified-the-application-will-not-support-spatial-sound"></a>未指定空間定位器。 應用程式將不支援空間音效

如果未設定音訊空間定位器，則會出現「未指定任何空間定位器」警告。 如果未安裝 XR 套件，則會發生這種情況，因為 Unity 包含這些套件中的 spatializers。

若要解決此問題，請確定：

- **視窗**  > **套件管理員** 已安裝一或多個 XR 套件
- **混合現實工具**  >  組 **公用程式**  > **設定 Unity 專案** 並為 **音訊空間定位器** 進行選取

  ![選取音訊 Apatializer](../features/images/release-notes/SpatializerSelection.png)

### <a name="nullreferenceexception-object-reference-not-set-to-an-instance-of-an-object-scenetransitionserviceinitialize"></a>NullReferenceException：物件參考未設定為物件的實例 (SceneTransitionService.Initialize) 

在某些情況下，開啟 `EyeTrackingDemo-00-RootScene` 可能會在 SceneTransitionService 類別的 Initialize 方法中造成 NullReferenceException。
此錯誤是因為未設定場景轉換服務的設定檔。 若要解決此問題，請使用下列步驟：

- 流覽至階層 `MixedRealityToolkit` 中的物件
- 在 [偵測器] 視窗中，選取 `Extensions`
- 如果未展開，請展開 `Scene Transition Service`
- 將的值設定 `Configuration Profile` 為 **MRTKExamplesHubSceneTransitionServiceProfile**

<img src="../features/images/release-notes/FixSceneTransitionProfile.png" width="500px" alt="Fix Scene Transition Profile">

### <a name="oculus-quest"></a>Oculus 的追求

目前在 [以獨立平臺為目標時，使用 OCULUS XR 外掛程式](https://forum.unity.com/threads/unable-to-start-oculus-xr-plugin.913883/)的已知問題。  查看 Oculus bug 追蹤程式/論壇/版本資訊以取得更新。

Bug 會以這一組3個錯誤表示：

![Oculus XR 外掛程式錯誤](https://forum.unity.com/attachments/erori-unity-png.644204/)

### <a name="unityui-and-textmeshpro"></a>UnityUI 和 TextMeshPro

較新版本的 TextMeshPro 有一個已知問題 (1.5.0 + 或 2.1.1 +) ，其中下拉式清單和粗體字字元間距的預設字型大小已改變。

![TMP 映射](https://user-images.githubusercontent.com/68253937/93158069-4d582f00-f6c0-11ea-87ad-94d0ba3ba6e5.png)

這可以透過降級至舊版的 TextMeshPro 來解決。 See [issue #8556](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8556) for more details.
