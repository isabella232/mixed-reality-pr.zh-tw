---
title: 語音
description: 在 MRTK 中設定語音輸入
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、語音、
ms.openlocfilehash: d86b81a707c7ca47d9c98991a56e63531add4847
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104695335"
---
# <a name="speech"></a>語音

![近端功能表](../Images/Input/MRTK_Input_Speech.png)

語音輸入提供者（例如 *Windows 語音輸入*）不會建立任何控制器，而是可讓您定義可在辨識時引發語音輸入事件的關鍵字。 *輸入系統設定檔* 中的 **語音命令設定檔** 可讓您設定要辨識的關鍵字。 您也可以針對每個命令：

- 選取要對應的 **輸入動作** 。 如此一來，您就可以藉由將這兩個動作對應到相同的動作，使用關鍵字 *Select* 來與滑鼠左鍵相同的效果。
- 指定在按下時會產生相同語音事件的 **按鍵碼** 。
- 新增將在 UWP 應用程式中用來從應用程式資源取得當地語系化關鍵字的 **當地語系化金鑰** 。

<img src="../Images/Input/SpeechCommandsProfile.png" width="450px" alt="Speech command profile">

## <a name="handling-speech-input"></a>處理語音輸入

您 [**`Speech Input Handler`**](xref:Microsoft.MixedReality.Toolkit.Input.SpeechInputHandler) 可以使用 [**UnityEvents**](https://docs.unity3d.com/Manual/UnityEvents.html)將腳本新增至 GameObject 來處理語音命令。 它會自動顯示來自 **語音命令設定檔** 的已定義關鍵字清單。

<img src="../Images/Input/SpeechCommands_SpeechInputHandler1.png" width="450px" alt="speech input handler 1">

指派選擇性的 **SpeechConfirmationTooltip 預製專案** ，以顯示辨識的動畫確認工具提示標籤。

<img src="../Images/Input/SpeechCommands_SpeechInputHandler2.png" alt="Speech input handler 2">

或者，開發人員可以 [`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) 在自訂腳本元件中執行介面，以 [處理語音輸入事件](InputEvents.md#input-event-interface-example)。

## <a name="example-scene"></a>範例場景

中的 **SpeechInputExample** 場景 `MRTK/Examples/Demos/Input/Scenes/Speech` 顯示如何使用語音。 您也可以藉由執行 [`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) (參閱 [事件處理常式](InputEvents.md)) 的表格，直接在您自己的腳本中接聽語音命令事件。

<img src="../Images/Input/SpeechExampleScene.png" width="750px" alt="Speech Example scene">
