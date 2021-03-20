---
title: UsingARFoundation
description: 在 unity 中使用 ARFoundation 的檔
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、AR Core、AR 套件
ms.openlocfilehash: 4a0e57fa3f8b00ac9867689b9c8fe49a560dbe11
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104683051"
---
# <a name="how-to-configure-mrtk-for-ios-and-android-experimental"></a>如何設定 iOS 和 Android 的 MRTK [實驗]

## <a name="install-required-packages"></a>安裝必要的套件

1. 從 [GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/tag/v2.3.0)或 [Unity 封裝管理員](../../configuration/usingupm.md)下載並匯入 **MixedReality 的套件。**

1. 在 Unity 封裝管理員 (UPM) 中，安裝下列套件：

    **Unity 2018.4.x**

    | **Android** | **iOS** | 註解 |
    | --- | --- | --- |
    | AR 基礎  <br/> 版本： 1.5.0-preview 6 | AR 基礎  <br/> 版本： 1.5.0-preview 6 | 針對 Unity 2018.4，此套件包含為預覽版本。 若要查看套件： `Window` > `Package Manager` > `Advanced` > `Show Preview Packages` |
    | ARCore XR 外掛程式 <br/> 版本：2.1。2 | ARKit XR 外掛程式 <br/> 版本：2.1。2 | |

    **Unity 2019.4. x**

    | **Android** | **iOS** |
    | --- | --- |
    | AR 基礎  <br/> 版本：2.1。8 |  AR 基礎  <br/> 版本：2.1。8 |
    | ARCore XR 外掛程式 <br/> 版本：2.1.11 | ARKit XR 外掛程式 <br/> 版本：2.1。9 |

    **Unity 2020.1 (目前尚未正式支援，僅包含供資訊用途之用)**

    | **Android** | **iOS** |
    | --- | --- |
    | AR 基礎  <br/> 版本：3.1。3 |  AR 基礎  <br/> 版本：3.1。3 |
    | ARCore XR 外掛程式 <br/> 版本：3.1。4 | ARKit XR 外掛程式 <br/> 版本：3.1。3 |

1. 藉由叫用功能表項目來更新 MRTK UnityAR 腳本定義： **混合現實工具組 > 公用程式 > UnityAR > 更新腳本定義**

## <a name="enabling-the-unity-ar-camera-settings-provider"></a>啟用 Unity AR 攝影機設定提供者

下列步驟假設使用 MixedRealityToolkit 物件。 其他服務註冊機構所需的步驟可能會不同。

1. 選取場景階層中的 MixedRealityToolkit 物件。

    ![MRTK 設定的場景階層](../images/MRTK_ConfiguredHierarchy.png)

1. 選取 [ **複製並自訂** ] 以複製 MRTK 設定檔，以啟用自訂設定。

    ![複製 MRTK 設定檔](../images/camera-system/CloneProfileARFoundation.png)

1. 選取相機設定檔旁邊的 [ **複製** ]。

    ![複製 MRTK 攝影機設定檔](../images/camera-system/CloneCameraProfileARFoundation.png)

1. 將 [偵測器] 面板移至 [相機系統] 區段，然後展開 [ **相機設定提供者** ] 區段。

    ![展開設定提供者](../images/camera-system/ExpandProviders.png)

1. 按一下 [新增 **相機設定提供者** ]，並展開新加入的 **新相機設定** 專案。

    ![展開新的設定提供者](../images/camera-system/ExpandNewProvider.png)

1. 選取 Unity AR 攝影機設定提供者

    ![選取 Unity AR 設定提供者](../images/camera-system/SelectUnityArSettings.png)

    如需有關設定 Unity AR 攝影機設定提供者的詳細資訊： [UNITY ar 攝影機設定提供者](../camera-system/unity-ar-camera-settings.md)。

> [!NOTE]
> 此安裝會在應用程式啟動時檢查 () 如果 AR 基礎元件在場景中。 如果沒有，則會自動新增它們，使其可搭配 ARCore 和 ARKit 使用。
> 如果您需要設定特定行為，您應該自行新增您需要的元件。
> 如需 AR 基礎元件和安裝的詳細資訊，請參閱此 [檔](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@2.2/manual/index.html#samples)。

## <a name="building-a-scene-for-android-and-ios-devices"></a>建立適用于 Android 和 iOS 裝置的場景

1. 確定您已將 UnityAR 攝影機設定提供者新增至您的場景。

1. 將平臺切換至 Unity 組建設定中的 Android 或 iOS

    當您切換平臺時，您應該會看到 [MRTK 專案設定] 視窗，其中包含您所選平臺的設定。  按一下 [套用] 以啟用平臺特定設定。

    iOS 專案設定器設定

    ![iOS 專案配置器](../images/camera-system/MRTKProjectConfigurator.png)

1. 切換 Android 的平臺後，不需要額外的步驟。

1. 如果平臺是 iOS，請編輯 > 專案設定 > 播放程式 > 其他設定，請在優化標頭下， **取消** 核取 [去除引擎程式碼]

    ![iOS 設定](../images/camera-system/UncheckStripEngineCodeiOS.png)

    > [!NOTE]
    > 取消核取區域引擎程式碼是 Xcode [#6646](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/6646)的錯誤的短期解決方案。  我們正致力於長期解決方案。

1. 建立並執行場景

## <a name="see-also"></a>另請參閱

- [Unity AR 相機設定](../camera-system/unity-ar-camera-settings.md)
