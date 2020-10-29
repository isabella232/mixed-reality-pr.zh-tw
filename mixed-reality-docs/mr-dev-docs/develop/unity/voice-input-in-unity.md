---
title: Unity 中的語音輸入
description: Unity 會公開三種方式，將語音輸入新增至您的 Windows Mixed Reality 應用程式。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: 語音輸入、KeywordRecognizer、GrammarRecognizer、麥克風、聽寫、語音
ms.openlocfilehash: b6930b35046e32beb1a4ca9f9ca29996487fcf4d
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2020
ms.locfileid: "91681045"
---
# <a name="voice-input-in-unity"></a>Unity 中的語音輸入

>[!NOTE]
>除了下列資訊之外，請考慮使用適用于認知語音服務 SDK 的 Unity 外掛程式，其具有更好的語音精確度結果，並可讓您輕鬆存取語音轉換文字解碼和先進的語音功能，例如對話方塊、意圖型互動、轉譯、文字轉語音的合成和自然語言的語音辨識。 在這裡尋找範例和檔： https://docs.microsoft.com//azure/cognitive-services/speech-service/quickstart-csharp-unity   

Unity 公開三種將 [語音輸入](../../design/voice-input.md) 新增至 Unity 應用程式的方式。

KeywordRecognizer (兩種 PhraseRecognizers 類型的其中一種) ，您的應用程式可以指定要接聽的字串命令陣列。 GrammarRecognizer (PhraseRecognizer) 的另一種類型時，您的應用程式可以取得定義特定文法的 SRGS 檔案來接聽。 使用 DictationRecognizer 時，您的應用程式可以接聽任何單字，並提供使用者語音的備註或其他顯示。

>[!NOTE]
>一次只能處理聽寫或片語辨識。 這表示，如果 GrammarRecognizer 或 KeywordRecognizer 處於作用中狀態，DictationRecognizer 就無法作用，反之亦然。

## <a name="enabling-the-capability-for-voice"></a>啟用語音的功能

您必須為應用程式宣告 **麥克風** 功能，以利用語音輸入。
1. 在 Unity 編輯器中，流覽至 [> Player 編輯 > 專案設定]，移至播放機設定
2. 按一下 [Windows 市存放區] 索引標籤
3. 在 [發佈設定 > 功能] 區段中，檢查 **麥克風** 功能

## <a name="phrase-recognition"></a>片語辨識

若要讓您的應用程式接聽使用者所說的特定片語，請採取一些動作，您必須：
1. 使用 KeywordRecognizer 或 GrammarRecognizer 指定要接聽的片語
2. 處理 OnPhraseRecognized 事件，並採取對應至已辨識片語的動作

### <a name="keywordrecognizer"></a>KeywordRecognizer

**命名空間：** *UnityEngine*<br>
**類型：** *KeywordRecognizer* 、 *PhraseRecognizedEventArgs* 、 *SpeechError* 、 *SpeechSystemStatus*

我們需要一些 using 語句來節省一些按鍵：

```
using UnityEngine.Windows.Speech;
using System.Collections.Generic;
using System.Linq;
```

然後讓我們將幾個欄位新增至您的類別，以儲存辨識器和關鍵字 >動作字典：

```
KeywordRecognizer keywordRecognizer;
Dictionary<string, System.Action> keywords = new Dictionary<string, System.Action>();
```

現在將關鍵字加入至字典 (例如，在 Start ( # A2 方法) 內。 在此範例中，我們要新增 "activate" 關鍵字：

```
//Create keywords for keyword recognizer
keywords.Add("activate", () =>
{
    // action to be performed when this keyword is spoken
});
```

建立關鍵字辨識器並告訴它要辨識的內容：

```
keywordRecognizer = new KeywordRecognizer(keywords.Keys.ToArray());
```

現在報名 OnPhraseRecognized 事件

```
keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
```

範例處理常式如下：

```
private void KeywordRecognizer_OnPhraseRecognized(PhraseRecognizedEventArgs args)
{
    System.Action keywordAction;
    // if the keyword recognized is in our dictionary, call that Action.
    if (keywords.TryGetValue(args.text, out keywordAction))
    {
        keywordAction.Invoke();
    }
}
```

最後，開始辨識！

```
keywordRecognizer.Start();
```

### <a name="grammarrecognizer"></a>GrammarRecognizer

**命名空間：** *UnityEngine*<br>
**類型** ： *GrammarRecognizer* 、 *PhraseRecognizedEventArgs* 、 *SpeechError* 、 *SpeechSystemStatus*

如果您要使用 SRGS 指定辨識文法，則會使用 GrammarRecognizer。 如果您的應用程式有多個關鍵字，如果您想要辨識更複雜的片語，或是想要輕鬆開啟和關閉命令集，這會很有用。 請參閱： [使用 SRGS XML 建立](https://msdn.microsoft.com/library/hh378349(v=office.14).aspx) 檔案格式資訊的文法。

一旦您有 SRGS 文法，而且它位於 [StreamingAssets 資料夾](https://docs.unity3d.com/Manual/StreamingAssets.html)的專案中：

```
<PROJECT_ROOT>/Assets/StreamingAssets/SRGS/myGrammar.xml
```

建立 GrammarRecognizer，並將路徑傳遞至您的 SRGS 檔案：

```
private GrammarRecognizer grammarRecognizer;
grammarRecognizer = new GrammarRecognizer(Application.streamingDataPath + "/SRGS/myGrammar.xml");
```

現在報名 OnPhraseRecognized 事件

```
grammarRecognizer.OnPhraseRecognized += grammarRecognizer_OnPhraseRecognized;
```

您將會取得一個回呼，其中包含您可以適當處理的 SRGS 文法中指定的資訊。 大部分的重要資訊都會在 semanticMeanings 陣列中提供。

```
private void Grammar_OnPhraseRecognized(PhraseRecognizedEventArgs args)
{
    SemanticMeaning[] meanings = args.semanticMeanings;
    // do something
}
```

最後，開始辨識！

```
grammarRecognizer.Start();
```

## <a name="dictation"></a>聽寫

**命名空間：** *UnityEngine*<br>
**類型** ： *DictationRecognizer* 、 *SpeechError* 、 *SpeechSystemStatus*

使用 DictationRecognizer 將使用者的語音轉換成文字。 DictationRecognizer 會公開 [聽寫](../../design/voice-input.md#dictation) 功能，並支援註冊和接聽假設和片語完成的事件，讓您可以在使用者說話和之後，將意見反應提供給您的使用者。 開始 ( # A1 並停止 ( # A3 方法，分別啟用和停用聽寫辨識。 完成辨識器之後，應該使用 Dispose ( # A1 方法來處置它所使用的資源。 如果未在這之前釋出這些資源，它會在垃圾收集期間自動釋出這些資源。

開始使用聽寫只需要幾個步驟：
1. 建立新的 DictationRecognizer
2. 處理聽寫事件
3. 啟動 DictationRecognizer

### <a name="enabling-the-capability-for-dictation"></a>啟用聽寫功能

除了上述的「麥克風」功能之外，您必須為應用程式宣告「網際網路用戶端」功能，以利用聽寫。
1. 在 Unity 編輯器中，流覽至 [> Player 編輯 > 專案設定] 頁面，移至播放機設定
2. 按一下 [Windows 市存放區] 索引標籤
3. 在 [發佈設定 > 功能] 區段中，檢查 **InternetClient** 功能

### <a name="dictationrecognizer"></a>DictationRecognizer

建立 DictationRecognizer，如下所示：

```
dictationRecognizer = new DictationRecognizer();
```

有四個聽寫事件可供訂閱和處理，以實行聽寫行為。
1. DictationResult
2. DictationComplete
3. DictationHypothesis
4. DictationError

**DictationResult**

此事件會在使用者暫停（通常是在句子結尾）時引發。 在這裡會傳回完整的可辨識字串。

首先，訂閱 DictationResult 事件：

```
dictationRecognizer.DictationResult += DictationRecognizer_DictationResult;
```

然後處理 DictationResult 回呼：

```
private void DictationRecognizer_DictationResult(string text, ConfidenceLevel confidence)
{
    // do something
}
```

**DictationHypothesis**

此事件會在使用者進行交談時持續引發。 當辨識器接聽時，它會提供到目前為止所聽過的文字。

首先，訂閱 DictationHypothesis 事件：

```
dictationRecognizer.DictationHypothesis += DictationRecognizer_DictationHypothesis;
```

然後處理 DictationHypothesis 回呼：

```
private void DictationRecognizer_DictationHypothesis(string text)
{
    // do something
}
```

**DictationComplete**

此事件會在辨識器停止時引發，不論是從停止 ( # A1 呼叫、發生超時或其他錯誤。

首先，訂閱 DictationComplete 事件：

```
dictationRecognizer.DictationComplete += DictationRecognizer_DictationComplete;
```

然後處理 DictationComplete 回呼：

```
private void DictationRecognizer_DictationComplete(DictationCompletionCause cause)
{
   // do something
}
```

**DictationError**

發生錯誤時，就會引發此事件。

首先，訂閱 DictationError 事件：

```
dictationRecognizer.DictationError += DictationRecognizer_DictationError;
```

然後處理 DictationError 回呼：

```
private void DictationRecognizer_DictationError(string error, int hresult)
{
    // do something
}
```

一旦您已訂閱並處理您感興趣的聽寫事件之後，請啟動聽寫辨識器以開始接收事件。

```
dictationRecognizer.Start();
```

如果您不想再保留 DictationRecognizer，則需要取消訂閱事件並處置 DictationRecognizer。

```
dictationRecognizer.DictationResult -= DictationRecognizer_DictationResult;
dictationRecognizer.DictationComplete -= DictationRecognizer_DictationComplete ;
dictationRecognizer.DictationHypothesis -= DictationRecognizer_DictationHypothesis ;
dictationRecognizer.DictationError -= DictationRecognizer_DictationError ;
dictationRecognizer.Dispose();
```

**提示**
* 開始 ( # A1 並停止 ( # A3 方法，分別啟用和停用聽寫辨識。
* 完成辨識器之後，必須使用 Dispose ( # A1 方法處置，以釋放其使用的資源。 如果未在這之前釋出這些資源，它會在垃圾收集期間自動釋出這些資源。
* 在設定的一段時間後發生超時。 您可以檢查 DictationComplete 事件中的這些超時。 有兩個需要注意的超時：
   1. 如果辨識器啟動，但在前五秒內未收到任何音訊，則會超時。
   2. 如果辨識器已指定結果，但接著會聽到20秒的無回應，則會超時。

## <a name="using-both-phrase-recognition-and-dictation"></a>使用片語辨識和聽寫

如果您想要在您的應用程式中同時使用片語辨識和聽寫，您必須完全關閉，才能啟動另一個。 如果您有多個 KeywordRecognizers 正在執行，您可以將它們一次全部關閉：

```
PhraseRecognitionSystem.Shutdown();
```

為了將所有辨識器還原至先前的狀態，在 DictationRecognizer 停止之後，您可以呼叫：

```
PhraseRecognitionSystem.Restart();
```

您也可以直接啟動 KeywordRecognizer，這也會重新開機 PhraseRecognitionSystem。

## <a name="using-the-microphone-helper"></a>使用麥克風協助程式

GitHub 上的混合現實工具組包含麥克風協助程式類別，可在系統上有可用的麥克風時提示開發人員。 其中一個用途是要檢查系統上是否有麥克風，然後才在應用程式中顯示任何語音互動提示。

您可以在 [ [輸入/腳本/公用程式] 資料夾](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Utilities/MicrophoneHelper.cs)中找到麥克風協助程式腳本。 GitHub 存放庫也包含示範如何使用 helper 的 [小型範例](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Input/Scripts/MicrophoneHelperSample.cs) 。

## <a name="voice-input-in-mixed-reality-toolkit"></a>混合現實工具組中的語音輸入
您可以在此場景中找到語音輸入的範例。

- [HoloToolkit-Examples/Input/場景/SpeechInputSource unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Input/Scenes/SpeechInputSource.unity)

## <a name="next-development-checkpoint"></a>下一個開發檢查點

如果您要遵循我們所配置的 Unity 開發檢查點旅程，您接下來要探索混合現實平臺功能和 Api：

> [!div class="nextstepaction"]
> [共用體驗](shared-experiences-in-unity.md)

您隨時都可以回到 [Unity 開發檢查點](unity-development-overview.md#2-core-building-blocks) 。
