---
title: 攝影機系統總覽
description: MRTK 中相機系統的登陸頁面
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、攝影機、
ms.openlocfilehash: e3b7caacaa9baa67fd81f6d32f3fd8c9f123e66d
ms.sourcegitcommit: 8b4c2b1aac83bc8adf46acfd92b564f899ef7735
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/30/2021
ms.locfileid: "113121286"
---
# <a name="camera-system"></a>攝影機系統

攝影機系統可讓 Microsoft Mixed Reality 工具組設定和優化應用程式的攝影機，以用於混合現實應用程式。 您可以使用相機系統來撰寫應用程式，以支援不透明的 (例如：虛擬實境) 和透明的 (例如： Microsoft HoloLens) 裝置，而不需要撰寫程式碼來區分和容納各種類型的顯示。

## <a name="enabling-the-camera-system"></a>啟用相機系統

攝影機系統是由 MixedRealityToolkit 物件 (或另一個服務註冊機構元件) 管理。

下列步驟假設使用 MixedRealityToolkit 物件。 其他服務註冊機構所需的步驟可能會不同。

1. 選取場景階層中的 MixedRealityToolkit 物件。

    ![MRTK 設定的場景階層](../images/MRTK_ConfiguredHierarchy.png)

2. 將 [偵測器] 面板移至 [相機系統] 區段，並確定已核取 [ **啟用相機系統** ]。

    ![啟用相機系統](../images/camera-system/EnableCameraSystem.png)

3. 選取相機系統的執行。 MRTK 提供的預設類別實作為 `MixedRealityCameraSystem` 。

    ![選取相機系統執行](../images/camera-system/SelectCameraSystemType.png)

4. 選取所需的設定設定檔

    ![選取相機系統設定檔](../images/camera-system/SelectCameraProfile.png)

## <a name="configuring-the-camera-system"></a>設定相機系統

### <a name="settings-providers"></a>設定提供者

![攝影機設定提供者](../images/camera-system/CameraSettingsProviders.png)

攝影機設定提供者會啟用相機的平臺特定設定。 這些設定可能包含自訂設定步驟和/或元件。

您可以按一下 [ **新增相機設定提供者** ] 按鈕來加入提供者。 您可以按一下 **-** 提供者名稱右邊的按鈕來移除它們。

> [!Note]
> 並非所有平臺都需要相機設定提供者。 如果沒有任何提供者與應用程式執行所在的平臺相容，Microsoft Mixed Reality 工具組將會套用基本的預設值。

### <a name="display-settings"></a>顯示器設定

![攝影機顯示設定](../images/camera-system/CameraDisplaySettings.png)

顯示設定是針對不透明的 (（例如：虛擬實境) 和透明的 (例如： Microsoft HoloLens) 顯示兩者指定的。 相機是在執行時間使用這些設定來設定。

**近距離剪輯**

近接的裁剪平面是虛擬物件可以指向相機但仍呈現的最接近量（以量為單位）。 為了讓使用者更容易緩和，建議將此值設為大於零。 先前的映射包含已發現的值，可在各種裝置上感到滿意。

**最遠的剪輯**

最遠的剪輯平面是在計量中，虛擬物件可以是相機的最遠，而且仍會呈現。 針對透明裝置，建議此值相對較接近真實世界空間，並中斷應用程式的沉浸式品質。

**清除旗標**

「清除旗標」值表示在繪製時如何清除顯示。 針對虛擬實境經驗，此值最常設為 Skybox。 針對透明顯示，建議將此設定為 [色彩]。

**背景色彩**

如果清除旗標未設定為 Skybox，則會顯示背景色彩屬性。

**品質設定**

[品質設定] 值表示 Unity 在呈現場景時應該使用的圖形品質。 品質層級是專案層級設定，不是任何一張相機特有的。 如需詳細資訊，請參閱 Unity 檔中的 [品質](https://docs.unity3d.com/Manual/class-QualitySettings.html) 文章。

## <a name="see-also"></a>另請參閱

- [攝影機系統 API 檔](xref:Microsoft.MixedReality.Toolkit.CameraSystem)
- [建立相機設定提供者](create-settings-provider.md)
