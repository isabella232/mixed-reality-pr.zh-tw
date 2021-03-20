---
title: 聽寫
description: Docummentation 如何錄製音訊剪輯並在 MRTK 中取得轉譯
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: 15ee2b5f636e9f1e0a235b1e7fdef15cda28ed36
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104680611"
---
# <a name="dictation"></a>聽寫

聽寫可讓使用者錄製音訊剪輯並取得轉譯。 若要使用它，請確定已在 *輸入系統設定檔* 中註冊聽寫系統。 **Windows 聽寫輸入提供者** 是現成提供的聽寫系統，但是可以建立執行替代的聽寫系統 [`IMixedRealityDictationSystem`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityDictationSystem) 。

## <a name="requirements"></a>規格需求

聽寫系統會使用 Unity 的 [DictationRecognizer](https://docs.unity3d.com/ScriptReference/Windows.Speech.DictationRecognizer.html) ，其本身會使用基礎 Windows 語音 api 來處理聽寫。 請注意，這表示這項功能只存在於 Windows 架構的平臺上。

使用聽寫系統需要 [PlayerSettings 功能一節](https://docs.unity3d.com/Manual/class-PlayerSettingsWSA.html#Capabilities)中的「網際網路用戶端」和「麥克風」應用程式功能。
如需 Unity 中語音輸入的詳細資訊，請參閱 [Windows Mixed Reality 檔](https://docs.microsoft.com/windows/mixed-reality/voice-input-in-unity#dictation) 。

## <a name="configuration"></a>組態

<img src="../images/input/DictationDataProvider.png" width="80%" class="center" alt="Dictation Data Provider">

設定好聽寫服務之後，您可以使用 [`DictationHandler`](xref:Microsoft.MixedReality.Toolkit.Input.DictationHandler) 腳本來啟動和停止錄製會話，並透過 UnityEvents 取得轉譯結果。

<img src="../images/input/DictationHandler.png" width="80%" class="center" alt="Dictation Handler">

- 當使用者在到目前為止所捕獲音訊的早期轉譯時，會引發 **聽寫假設**。
- **聽寫結果** 會在每個句子的結尾引發 (也就是當使用者) 暫停時，會產生截至目前為止所捕獲音訊的最後轉譯。
- 錄製會話的結尾會產生 **聽寫完成**，並包含音訊的完整、最後轉譯。
- 引發 **聽寫錯誤**，以通知聽寫服務中的錯誤。 此案例中的轉譯包含錯誤的描述。

## <a name="example-scene"></a>範例場景

中的 **聽寫** 場景會 `MRTK/Examples/Demos/Input/Scenes/Dictation` 顯示 `DictationHandler` 使用中的腳本。 如果您需要更多控制，您可以擴充此腳本或建立自己的執行 [`IMixedRealityDictationHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityDictationHandler) ，以直接接收聽寫事件。

<img src="../images/input/DictationDemo.png" width="80%" class="center" alt="Dictation Demo">
