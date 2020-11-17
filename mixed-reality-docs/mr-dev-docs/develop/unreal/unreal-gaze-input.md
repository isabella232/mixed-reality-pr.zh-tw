---
title: Unreal 中的注視輸入
description: 針對 HoloLens 和 Unreal 引擎設定注視輸入的教學課程
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
keywords: Windows Mixed Reality、全像 HoloLens 2、眼睛追蹤、注視輸入、前端掛接顯示器、Unreal 引擎、混合現實耳機、windows Mixed reality 耳機、虛擬實境耳機
ms.openlocfilehash: 2ea55e3c53275f6150ca7f2def10d71634119e2e
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2020
ms.locfileid: "94679047"
---
# <a name="gaze-input"></a>注視輸入

## <a name="overview"></a>概觀

[Windows Mixed Reality 外掛程式](https://docs.unrealengine.com/Platforms/VR/WMR/index.html)不會為眼睛輸入提供任何內建函數，但 HoloLens 2 支援眼睛追蹤。 實際的追蹤功能是由 Unreal 的前端 **裝載顯示器** 和 **眼睛追蹤** api 所提供，包括：

- 裝置資訊
- 追蹤感應器
- 方向和位置
- 裁剪窗格
- 注視資料和追蹤資訊

您可以在 Unreal 的前端 [裝載顯示](https://docs.unrealengine.com/BlueprintAPI/Input/HeadMountedDisplay/index.html) 和 [眼睛追蹤](https://docs.unrealengine.com/BlueprintAPI/EyeTracking/index.html) 檔中找到完整的功能清單。

除了 Unreal Api 之外，請查看 HoloLens 2 [眼睛](../../design/eye-gaze-interaction.md) 的相關檔，並深入瞭解 [HoloLens 2 的眼睛追蹤](https://docs.microsoft.com/windows/mixed-reality/eye-tracking) 的運作方式。

> [!IMPORTANT]
> 只有 HoloLens 2 才支援眼睛追蹤。

## <a name="enabling-eye-tracking"></a>啟用眼睛追蹤
您必須先在 HoloLens 專案設定中啟用注視輸入，才能使用任何 Unreal 的 Api。 當應用程式啟動時，您會看到如下列螢幕擷取畫面所示的同意提示。

- 選取 **[是]** 可設定許可權，並取得輸入的存取權。 如果您在任何時間都需要變更此設定，可以在 [ **設定** ] 應用程式中找到。

![目視輸入許可權](images/unreal/eye-input-permissions.png)

> [!NOTE] 
> Unreal 中的 HoloLens 眼睛追蹤只會有一個眼睛光線，而不是 stereoscopic 追蹤所需的兩個光線，而這是不受支援的。

這就是您在 Unreal 中開始將注視輸入新增至 HoloLens 2 應用程式時所需的所有設定。 您可以在下列連結中找到有關注視輸入的詳細資訊，以及它如何影響混合現實中的使用者。 當您建立互動式體驗時，請務必考慮這些資訊。

## <a name="next-development-checkpoint"></a>下一個開發檢查點

依循我們配置的 Unreal 開發檢查點旅程，此時您會探索 MRTK核心建置組塊。 接下來，您可以繼續進行下一個建置組塊： 

> [!div class="nextstepaction"]
> [手勢追蹤](unreal-hand-tracking.md)

或者，直接跳到混合實境平台功能和 API 的主題：

> [!div class="nextstepaction"]
> [HoloLens 相機](unreal-hololens-camera.md)

您可以隨時回到 [Unreal 開發檢查點](unreal-development-overview.md#2-core-building-blocks)。

## <a name="see-also"></a>另請參閱
* [校正](../../calibration.md)
* [舒適度](../../design/comfort.md)
* [目光和行動](../../design/gaze-and-commit.md)
* [語音輸入](../../out-of-scope/voice-design.md)
