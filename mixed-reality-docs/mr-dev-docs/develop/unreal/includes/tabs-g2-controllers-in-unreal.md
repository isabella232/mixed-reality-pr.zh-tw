---
ms.openlocfilehash: ce1f02bd2846cadc4e970fef738fb4b46bc3a09f10742b820a0998491c590c80
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2021
ms.locfileid: "115204206"
---
# <a name="all-platforms"></a>[所有平台](#tab/all)

### <a name="enabling-hp-motion-controller-plugin"></a>啟用 HP 移動控制器外掛程式 

互動設定檔和控制器對應位於 HP 移動控制器外掛程式中，必須啟用此外掛程式才能將控制器對應公開給 Unreal 的輸入系統。

![啟用 OpenXRHPController 外掛程式](../images/reverb-g2-img-01.png)

# <a name="steamvr"></a>[SteamVR](#tab/steamvr)

### <a name="configuring-startup-and-hmdpluginpriority"></a>設定啟動和 HMDPluginPriority

使用 SteamVR 的 Unreal 輸入有一些差異。  設定專案時，請先確認它是藉由新增 vr 來使用 SteamVR 的新輸入系統 **。SteamVR. EnableVRInput = 1** 至 **Engine/Config/ConsoleVariables.ini** 中的 **啟動** 區段。  此 ini 可在引擎安裝目錄中找到，而不是在專案目錄中。

![更新啟動設定](../images/reverb-g2-img-07.png)

HP 移動控制器外掛程式將會啟用 OpenXR。  如果您不是使用 OpenXR，您將需要在 ConsoleVariables.ini 的相同目錄中編輯 BaseEngine.ini SteamVR 的 HMDPluginPriority。  將 SteamVR 值變更為大於 OpenXRHMD 值。

![更新 HMDPluginPriority 設定](../images/reverb-g2-img-08.png)


