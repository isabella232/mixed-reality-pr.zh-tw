---
title: MRTK_Configuration_Dialog
description: 在 Unity 專案中設定 MRTK
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、Unity
ms.openlocfilehash: 7d2fd9d0b457c9357eb70295144e21ef1441c222
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/03/2021
ms.locfileid: "101783469"
---
# <a name="mrtk-project-configuration-dialog"></a>MRTK 專案設定對話方塊

當 Unity 載入專案時，會顯示 [MRTK 設定] 對話方塊，並判斷一或多個設定選項需要開發人員的注意力。

![稍後套用忽略](../features/images/configuration-dialog/ConfigurationDialogHeader.png)

若要套用變更，請按一下 **[套用** ] 按鈕。 **稍後** 的按鈕會延後變更，直到未來重新載入專案為止。

> [!NOTE]
> 如果有一或多個建議的設定保持未核取狀態，則 [設定] 對話方塊會再次出現。 若要避免發生這種情況，請套用所需的選項，然後透過 **混合現實工具** 組公用程式來重新開機對話方塊，  >    >  **設定 Unity 專案**，然後按一下 [**忽略**]。 這可防止設定對話方塊自動再次出現。

## <a name="common-settings"></a>一般設定

所有組建目標都會共用一組常見的選項。

![一般設定](../features/images/configuration-dialog/ConfigurationDialogCommonSettings.png)

### <a name="force-text-asset-serialization-and-enable-visible-meta-files"></a>強制文字資產序列化和啟用可見的中繼檔案

這些設定有助於簡化使用 Unity 專案和原始檔控制系統 (例如： Git) 。

### <a name="enable-vr-supported"></a>啟用 VR 支援

**Unity 2018**

在 **Player 設定**  >  **XR 設定中設定** 虛擬實境支援的虛擬實境 SDK 選項。

### <a name="set-single-pass-instanced-rendering-path"></a>設定單一傳遞實例轉譯路徑

將 **播放機設定**  >  **XR 設定**  >  **身歷聲轉譯模式** 設定為 **單一階段實例**。

### <a name="set-default-spatial-awareness-layer"></a>設定預設空間感知層

將空間感知註冊為第31層，以啟用簡單且一致的 raycast 和物理選項設定。

### <a name="audio-spatializer"></a>音訊空間定位器

音訊 spatializers 是可發揮空間音效和位置音訊功能的元件，讓混合的現實體驗真正沉浸。

> [!NOTE]
> 將音訊空間定位器設定為 [無] 將會停用位置音訊功能。

#### <a name="common-spatializers"></a>一般 spatializers

- Microsoft 空間定位器

Microsoft 提供的空間定位器支援在 HoloLens 2 上使用硬體加速。

此空間定位器可透過 [NuGet](https://www.nuget.org/packages/Microsoft.SpatialAudio.Spatializer.Unity/) 和 [GitHub](https://github.com/microsoft/spatialaudio-unity)取得。

如需 Microsoft 空間定位器的詳細資訊，請參閱 [空間音效檔](https://docs.microsoft.com/windows/mixed-reality/spatial-sound-in-unity)。

- MS HRTF 空間定位器

Unity 提供的 Microsoft Windows 空間定位器，是 Windows Mixed Reality 和 Windows XR Platform 套件的一部分。

- 共振音訊

由 Unity 提供的 Google 跨平臺空間定位器。

您可以在 [共振音訊檔](https://resonance-audio.github.io/resonance-audio/develop/unity/getting-started) 網站上找到詳細資訊。

## <a name="universal-windows-platform-settings"></a>通用 Windows 平臺設定

![UWP 設定](../features/images/configuration-dialog/ConfigurationDialogUWPSettings.png)

### <a name="uwp-capabilities"></a>UWP 功能

啟用通用 Windows 平臺應用程式的特定應用程式功能。 這些功能可讓平臺通知和要求啟用特定功能的許可權。

- 麥克風

  透過麥克風啟用捕捉音效。

- 網際網路用戶端

  啟用存取網際網路上資源的支援。

- 空間感知

  可支援使用真實世界的環境。

- 眼睛

  **Unity 2019.3 和更新版本**

  啟用追蹤使用者眼睛的支援。

### <a name="avoid-unity-playersettingsgraphicsjob-crash"></a>避免 Unity ' PlayerSettings. graphicsJob ' 損毀

**Unity 2019.3 和更新版本**

在最新版的 Unity 2019 中，當啟用 [圖形工作] 時，應用程式會在部署到 HoloLens 2 時損毀。
在 Unity 中，預設會啟用這項設定，但此錯誤存在 (查看 [Unity bug](https://issuetracker.unity3d.com/issues/enabling-graphics-jobs-in-2019-dot-3-x-results-in-a-crash-or-nothing-rendering-on-hololens-2)) ，設定程式會預設為將圖形作業設定為 [false] (因此允許部署到 HoloLens 2 的應用程式不會在) 時損毀。

## <a name="android-settings"></a>Android 設定

支援在 Android 供電裝置上進行 AR 應用程式的設定。

![Android 設定](../features/images/configuration-dialog/ConfigurationDialogAndroidSettings.png)

### <a name="disable-multi-threaded-rendering"></a>停用多執行緒轉譯

停  >    >  用由 Android 的 AR 支援所需的其他設定 **多執行緒** 轉譯的播放程式設定。

### <a name="set-minimum-api-level"></a>設定最小 API 層級

將 [   >  **其他設定** 的  >  **最小 API 層級**] 設定的值設定為強制執行 AR 應用程式的作業系統需求。

## <a name="ios-settings"></a>iOS 設定

支援在 iOS 裝置上的 AR 應用程式進行的設定。

![iOS 設定](../features/images/configuration-dialog/ConfigurationDialogiOSSettings.png)

### <a name="set-required-os-version"></a>設定必要的 OS 版本

設定 [播放程式 **設定**] 的值 [  >  **其他設定**  >  **目標最小 iOS 版本**]，以強制執行 AR 應用程式的作業系統需求。

### <a name="set-required-architecture"></a>設定必要的架構

設定 [ **Player 設定**  >  **其他設定**]  >  **架構** 的值，以強制執行 AR 應用程式的平臺需求。

### <a name="set-camera-usage-descriptions"></a>設定相機使用方式描述

設定 [播放程式 **設定**] 的值  >  **其他設定**  >  **相機** 使用方式描述，以要求使用裝置相機的許可權。
