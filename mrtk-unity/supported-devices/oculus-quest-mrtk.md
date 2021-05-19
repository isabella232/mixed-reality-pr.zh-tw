---
title: Oculus 的追求 MRTK
description: 在 MRTK 中設定 Oculus 的相關檔
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、Oculus 的追求、
ms.openlocfilehash: c0eccd0b366d39529eafc51d23031fc30144b1ae
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143964"
---
# <a name="how-to-configure-oculus-quest-in-mrtk-using-the-xr-sdk-pipeline"></a>如何使用 XR SDK 管線在 MRTK 中設定 Oculus 操作

需要進行 [Oculus](https://www.oculus.com/quest/) 。

MRTK 對 Oculus 的支援有兩個不同的來源： Unity 的 XR 管線和 Oculus Integration Unity 套件。 **OCULUS XRSDK Data Provider** 可讓您同時使用這兩個來源，而且必須用來在 Oculus 上使用 MRTK。

[Unity 的 XR 管線](https://docs.unity3d.com/Manual/XR.html)可讓您使用 Oculus 觸控控制器並搭配 Oculus 的進行追蹤。
此管線是在 Unity 2019.3 和更多功能中開發 XR 應用程式的標準。 若要使用此管線，請確定您使用的是 **Unity 2019.3 或更新版本**。

[Oculus Integration Unity 封裝](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022)可讓您搭配 Oculus 的執行來使用 **手動追蹤**。
此資料提供者 **不會使用 unity** 的 **XR 管線** 或 **舊版 XR 管線**，但因為控制器和 Headtracking 是由 Unity 的 XR 管線處理，所以必須遵循為 **Oculus 執行設定專案** 的步驟，以確保您使用的是 **XR 管線** ，而不是即將淘汰的 **舊版 XR 管線**。

## <a name="setting-up-project-for-the-oculus-quest"></a>設定專案以進行 Oculus 的尋找

1. 請遵循下列 [步驟](https://developer.oculus.com/documentation/unity/book-unity-gsg/) ，以確保您的專案已準備好在 Oculus 時進行部署。

1. 確定已在您的裝置上啟用 [開發人員模式](https://developer.oculus.com/documentation/native/android/mobile-device-setup/) 。 安裝 Oculus ADB 驅動程式是選擇性的。

## <a name="setting-up-the-xr-pipeline-for-oculus-quest"></a>設定 XR 管線以進行 Oculus 的尋找

1. 確定 **OCULUS XR 外掛程式** 已安裝在視窗下 **--> 封裝管理員**

    ![Oculus XR 外掛程式套件](../images/cross-platform/oculus-quest/OculusXRPluginPackage.png)

1. 前往 [**編輯--> 專案設定--> XR 外掛程式管理--> 外掛程式提供** 者]，以確定專案中包含 Oculus 外掛程式提供者

    ![Oculus 外掛程式提供者](../images/cross-platform/oculus-quest/OculusPluginProvider.png)

## <a name="setting-up-the-oculus-integration-unity-package-to-enable-handtracking"></a>設定 Oculus Integration Unity 套件以啟用 handtracking

1. 從 Unity 資產存放區下載並匯入 [Oculus 整合](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022) 。 測試的最新版本是20.0.0。 您[可以從此封存](https://developer.oculus.com/downloads/package/unity-integration-archive/)中找到較舊的版本

1. 流覽至混合現實工具組 > 公用程式 > Oculus > 整合 Oculus Integration Unity 模組。 這麼做會使用相關 Oculus 執行程式碼運作所需的定義和參考，來更新 asmdefs。 它也會更新 csc 檔案，以篩選出 Oculus 整合資產所產生的過時警告。 MRTK 存放庫包含將警告轉換成錯誤的 csc 檔案，這種轉換會中止 MRTK-Quest 設定程式。

    ![Oculus 整合 Asmdef](../images/cross-platform/oculus-quest/OculusIntegrationAsmdef.png)

1. 在匯入的 Oculus 資料夾中 (應該在資產/Oculus) 找到，其中有一個可編寫腳本的物件，稱為 OculusProjectConfig。 在該設定檔中，您必須將 HandTrackingSupport 設定為「控制器和手」。

    ![Oculus 整合控制器與手](../images/cross-platform/oculus-quest/OculusIntegrationControllerAndHands.png)

## <a name="setting-up-the-scene"></a>設定場景

1. 建立新的 Unity 場景，或開啟預先存在的場景，例如 HandInteractionExamples
1. 流覽至 **混合現實工具** 組  >  **新增至場景並設定**，以將 MRTK 新增至場景

## <a name="using-the-oculus-xr-sdk-data-provider"></a>使用 Oculus XR SDK Data Provider

1. 將您的設定檔設定為使用 **OCULUS XR SDK Data Provider**
    - 如果不打算修改設定設定檔
        - 將您的設定檔變更為 DefaultXRSDKConfigurationProfile，然後移至 [ [組建]，並將專案部署至 Oculus 的追求](oculus-quest-mrtk.md#build-and-deploy-your-project-to-oculus-quest)

    - 否則，請遵循下列步驟：
        - 選取階層中的 MixedRealityToolkit 遊戲物件，然後選取 [ **複製和自訂** ] 以複製預設的混合現實設定檔。

        ![複製設定檔](../images/cross-platform/CloneProfile.png)

        - 選取 **輸入** 設定設定檔

        ![輸入設定設定檔](../images/cross-platform/InputConfigurationProfile.png)

        - 在輸入系統設定檔中選取 [ **複製** ]，以啟用修改。

        ![複製輸入系統設定檔](../images/cross-platform/CloneInputSystemProfile.png)

        - 開啟 [ **輸入資料提供者** ] 區段，選取頂端的 [ **新增 Data Provider** ，然後在清單結尾加入新的資料提供者。  開啟新的資料提供者，並將類型設為 MixedReality，並將 **類型** 設定為 **XRSDK. Oculus > OculusXRSDKDeviceManager**

        ![Oculus 新增 XRSDK Data Provider](../images/cross-platform/oculus-quest/OculusAddDataXRSDKProvider.png)

1. Oculus XR SDK Data Provider 包含 OVR 相機 Rig 預製專案，此會使用 OVR 攝影機 Rig 自動設定專案，並 OVR 手以正確地路由輸入。 手動將 OVR 攝影機裝備新增至場景需要手動設定設定和輸入。

## <a name="build-and-deploy-your-project-to-oculus-quest"></a>建立您的專案，並將其部署至 Oculus 的追求

1. 透過 USB 3.0-> USB C 纜線插入 Oculus 的尋找
1. 流覽至檔案 **> 組建設定**
1. 將部署變更為 **Android**
1. 確定已選取 [Oculus]，作為適用的執行裝置

    ![Oculus 執行裝置](../images/cross-platform/oculus-quest/OculusRunDevice.png)

1. 選取組建並執行
    - 當您第一次選取 *組建並執行* 時，可能會遇到下列一組組建錯誤。 當您選取 [ *組建] 並重新執行* 時，應該可以成功部署。

    ![Oculus 預期的組建錯誤](../images/cross-platform/oculus-quest/OculusExpectedBuildErrors.png)

1. 接受來自要求內的 _允許 USB 調試_
1. 查看 Oculus 中的場景

## <a name="removing-oculus-integration-from-the-project"></a>從專案移除 Oculus 整合

1. 流覽至混合現實工具組 > Oculus > 個別的 Oculus Integration Unity 模組  ![ Oculus 分隔 Asmdef](../images/cross-platform/oculus-quest/OculusSeparationAsmdef.png)
1. 讓 Unity 重新整理為 MixedReality 中的參考，在此步驟中會修改 Oculus asmdef 和其他檔案
1. 關閉 Unity
1. 關閉 Visual Studio （如果已開啟）
1. 開啟檔案總管並流覽至 MRTK Unity 專案的根目錄
1. 刪除 UnityProjectName/Library 目錄
1. 刪除 UnityProjectName/資產/Oculus 目錄
1. 刪除 UnityProjectName/資產/Oculus 中繼檔案
1. 重新開啟 Unity

## <a name="common-errors"></a>常見錯誤

### <a name="quest-not-recognized-by-unity"></a>Unity 無法辨識的找出

請確定您的 Android 路徑已正確設定。 如果您持續遇到問題，請遵循本 [指南](https://developer.oculus.com/documentation/unity/book-unity-gsg/#install-android-tools)

**編輯 > 喜好設定 > 外部工具 > Android**

![Android 工具設定](../images/cross-platform/oculus-quest/AndroidToolsConfig.png)
