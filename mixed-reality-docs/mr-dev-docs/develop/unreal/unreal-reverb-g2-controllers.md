---
title: Unreal 中的 HP 回音 G2 控制器
description: 瞭解如何在 OpenXR 和 SteamVR 中使用新的 HP 迴響 G2 控制器來 Unreal 混合現實應用程式。
author: hferrone
ms.author: jacksonf
ms.date: 10/9/2020
ms.topic: article
keywords: Unreal、Unreal Engine 4、UE4、回音、回音、HP 回音、mixed reality、開發、運動控制器、使用者輸入、功能、新專案、模擬器、檔、指南、功能、全像遊戲開發、混合現實耳機、windows mixed reality 耳機、虛擬實境耳機
ms.openlocfilehash: b287a5c7de1ea086b76228d9109cc07a4e1569f5f926cb42dc3e37cc2a3bb916
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2021
ms.locfileid: "115204168"
---
# <a name="hp-reverb-g2-controllers-in-unreal"></a>Unreal 中的 HP 回音 G2 控制器 

## <a name="getting-started"></a>使用者入門

> [!IMPORTANT]
> 需要有 Unreal Engine 4.26 及 OpenXR 或 SteamVR，才能存取 hp 運動控制器外掛程式，您必須使用 HP 的「回音」 G2 控制器。

[!INCLUDE[](includes/tabs-g2-controllers-in-unreal.md)]

## <a name="porting-an-existing-openxr-app"></a>移植現有的 OpenXR 應用程式 

如果沒有任何控制器系結存在於 HP Mixed Reality 控制器的遊戲中，OpenXR 執行時間會嘗試將現有的系結重新對應到主動控制器。  在此情況下，遊戲已 Oculus 觸控系結，而且沒有任何 HP Mixed Reality 控制器系結。

![沒有控制器系結存在時重新對應現有的系結](images/reverb-g2-img-04.png)

這些事件仍然會引發，但是如果遊戲需要使用控制器專屬系結，例如右鍵的功能表按鈕，就必須使用 HP Mixed Reality 互動設定檔。  您可以針對每個動作指定多個控制器系結，以更妥善支援不同的裝置。
   
![使用多個控制器系結](images/reverb-g2-img-05.png)

## <a name="adding-input-action-mappings"></a>新增輸入動作對應 

定義新的動作，並對應至 [HP Mixed Reality 控制器] 區段中的其中一個按鍵。

![定義新的動作和對應](images/reverb-g2-img-02.png)

HP 的殘響 G2 控制器也有類比底框，可用於與「壓縮軸」系結的軸對應中。  有個別的捏住系結，當您完全按下 [握住] 按鈕時，應該將其用於動作對應。 

![使用壓縮軸系結](images/reverb-g2-img-03.png)

## <a name="adding-input-events"></a>加入輸入事件

在藍圖上按一下滑鼠右鍵，並從輸入系統中搜尋新的動作名稱，以新增這些動作的事件。  在此，藍圖會使用輸出字串來回應事件，並輸出目前的按鈕和軸狀態。

![藍圖會回應事件並輸出目前的按鈕和軸狀態](images/reverb-g2-img-06.png)

### <a name="using-input"></a>使用輸入 

[!INCLUDE[](includes/tabs-g2-controller-mapping-in-unreal.md)]

## <a name="see-also"></a>另請參閱
* [SteamVR 輸入](https://docs.unrealengine.com/Platforms/VR/SteamVR/HowTo/SteamVRInput/index.html)
* [使用 SteamVR 搭配 Windows Mixed Reality](/windows/mixed-reality/enthusiast-guide/using-steamvr-with-windows-mixed-reality)
* [Unreal Player 攝影機](https://docs.unrealengine.com/Programming/Tutorials/PlayerCamera/3/index.html)