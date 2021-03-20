---
title: 設定和設定檔
description: 修改 MRTK 中的設定檔。
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、MRTK 設定檔
ms.openlocfilehash: 98536341b854f834273107b76f67388189046196
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104680881"
---
# <a name="configuration-and-profiles"></a>設定和設定檔

並非每個 MRTK 的單一取用者都希望它以相同方式運作，因為在支援 AR 裝置時，有些會想要讓空間網格執行。 有些可能會想要在所有時間都有診斷視覺效果，而某些可能只會在使用者說出語音命令時，才需要它。

MRTK 必須可設定，才能支援各式各樣的需求，並使用稱為「設定檔」的概念來完成此動作。

## <a name="what-is-a-profile"></a>什麼是設定檔？

設定檔儲存服務的設定。 您可以使用它們來控制要執行哪些服務，以及這些服務在執行時的行為。 它們在您的專案中是儲存為 [ScriptableObject](https://docs.unity3d.com/Manual/class-ScriptableObject.html) 資產。 您可以在 [專案] 視窗中選取設定檔來加以查看和編輯。

例如，MRTK 有一個攝影機服務，這會根據顯示器是否為透明而定，將不同的屬性套用至主要相機 (例如 HoloLens) 或不透明 (例如 VR 耳機) 的情況。 攝影機服務會獲得 [相機設定檔](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Assets/MixedRealityToolkit/Definitions/MixedRealityCameraProfile.cs)，其中包含不同的透明與不透明的設定。

更複雜的設定檔範例是 [InputSystem](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Assets/MixedRealityToolkit/Definitions/InputSystem/MixedRealityInputSystemProfile.cs)。
該設定檔上的部分屬性 (例如 MixedRealityInputDataProviderConfiguration 實體) 控制將在執行時間具現化的物件，這是輸入系統知道如何建立 OpenVR、WMR 和 Unity 輸入子系統的方式。 此設定檔不只是一組屬性，可設定是否啟用或停用特定的輸入子功能，這也是 MRTK 在執行時間用來「新增」其他類別的插入機制 (例如，輸入系統設定檔包含具有序列化型別資訊的「輸入資料提供者」清單。這些物件是由輸入系統在執行時間具現化的) 

設定檔設定一開始會呈現灰色，因為它們是使用 MRTK 的預設設定檔來設定的。
它們只能在複製之後修改，以確保自訂的設定檔在 MRTK 版本更新之後不會遺失。

## <a name="modifying-profiles"></a>修改設定檔

雖然您可以藉由前往 ScriptableObject) 的序列化資產來個別修改設定檔 (，但是通常會透過根 MixedRealityToolkit 場景物件的 MRTK 偵測器來存取設定檔。

![設定檔](../features/images/profiles/input_profile.png)

上圖顯示大量的設定-請注意，左側的每個選項都會顯示其對應服務的設定。

### <a name="camera"></a>相機

包含每個顯示類型的設定。 用來根據應用程式執行所在的顯示類型，套用不同層級的品質、剪輯和轉譯設定 (也就是 AR 與 VR) 。

### <a name="input"></a>輸入

MRTK 最複雜子系統的最大設定檔。 輸入 [系統](Terminology.md) 檔本身將涵蓋輸入的各種子系統。

### <a name="teleport"></a>傳送

此設定檔會控制遙傳系統的運作方式，而這主要是 VR 的概念。

### <a name="spatial-mapping"></a>空間對應

此設定檔會控制空間網格系統的運作方式 (亦即，此系統負責啟動系統，以在 AR 裝置) 上轉譯空間網格。 主要是 AR 概念。

### <a name="diagnostics"></a>診斷

這會控制顯示畫面播放速率計數器的視覺化效能工具，以及基本的記憶體使用量。

### <a name="scene-system"></a>場景系統

這會控制目前未啟用預設的系統，其設計目的是要讓多場景案例更容易使用。

### <a name="extensions"></a>延伸模組

這個預設的預設設定檔是可供取用者寫入的擴充點，然後插入其本身的物件，MRTK 執行時間會將其具現化並執行。

### <a name="editor"></a>編輯器

包含 MRTK 的僅限編輯器行為的一般設定。
