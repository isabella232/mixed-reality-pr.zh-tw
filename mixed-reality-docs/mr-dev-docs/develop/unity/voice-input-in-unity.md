---
title: Unity 中的語音輸入
description: 瞭解 Unity 如何公開三種方式，將語音輸入、語音辨識和聽寫新增至您的 Windows Mixed Reality 應用程式。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: 語音輸入、KeywordRecognizer、GrammarRecognizer、麥克風、聽寫、語音、混合現實耳機、windows mixed reality 耳機、虛擬實境耳機、MRTK、混合現實工具組
ms.openlocfilehash: 7268a4df9c7fce03029937c72540ed274574067d
ms.sourcegitcommit: 8c3af63fb49494f75c8ab46236fc3dd8533c1e9d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/05/2021
ms.locfileid: "99606113"
---
# <a name="voice-input-in-unity"></a><span data-ttu-id="9afeb-104">Unity 中的語音輸入</span><span class="sxs-lookup"><span data-stu-id="9afeb-104">Voice input in Unity</span></span>

> [!CAUTION]
> <span data-ttu-id="9afeb-105">開始之前，請考慮使用適用于認知語音服務 SDK 的 Unity 外掛程式。</span><span class="sxs-lookup"><span data-stu-id="9afeb-105">Before starting, consider using the Unity plug-in for the Cognitive Speech Services SDK.</span></span> <span data-ttu-id="9afeb-106">此外掛程式具有更佳的語音精確度結果，並可輕鬆存取語音轉換文字解碼，以及快速的語音轉換功能，例如對話方塊、意圖型互動、轉譯、文字轉換語音，以及自然語言的語音辨識。</span><span class="sxs-lookup"><span data-stu-id="9afeb-106">The plugin has better Speech Accuracy results and easy access to speech-to-text decode, as well as advanced speech features like dialog, intent based interaction, translation, text-to-speech synthesis, and natural language speech recognition.</span></span> <span data-ttu-id="9afeb-107">若要開始使用，請參閱 [範例和檔](https://docs.microsoft.com/azure/cognitive-services/speech-service/quickstart-csharp-unity)集。</span><span class="sxs-lookup"><span data-stu-id="9afeb-107">To get started, check out the [sample and documentation](https://docs.microsoft.com/azure/cognitive-services/speech-service/quickstart-csharp-unity).</span></span>

<span data-ttu-id="9afeb-108">Unity 公開三種將 [語音輸入](../../design/voice-input.md) 新增至 Unity 應用程式的方式，其中前兩個是 PhraseRecognizer 類型：</span><span class="sxs-lookup"><span data-stu-id="9afeb-108">Unity exposes three ways to add [Voice input](../../design/voice-input.md) to your Unity application, the first two of which are types of PhraseRecognizer:</span></span>
* <span data-ttu-id="9afeb-109">會為 `KeywordRecognizer` 您的應用程式提供要接聽的字串命令陣列</span><span class="sxs-lookup"><span data-stu-id="9afeb-109">The `KeywordRecognizer` supplies your app with an array of string commands to listen for</span></span>
* <span data-ttu-id="9afeb-110">為 `GrammarRecognizer` 您的應用程式提供一個可定義特定文法以接聽的 SRGS 檔案</span><span class="sxs-lookup"><span data-stu-id="9afeb-110">The `GrammarRecognizer` gives your app an SRGS file defining a specific grammar to listen for</span></span>
* <span data-ttu-id="9afeb-111">`DictationRecognizer`可讓您的應用程式接聽任何單字，並提供使用者語音的備註或其他顯示</span><span class="sxs-lookup"><span data-stu-id="9afeb-111">The `DictationRecognizer` lets your app listen for any word and provide the user with a note or other display of their speech</span></span>

> [!NOTE]
> <span data-ttu-id="9afeb-112">聽寫和片語辨識無法同時處理。</span><span class="sxs-lookup"><span data-stu-id="9afeb-112">Dictation and phrase recognition can't be handled at the same time.</span></span> <span data-ttu-id="9afeb-113">如果 GrammarRecognizer 或 KeywordRecognizer 處於作用中狀態，則 DictationRecognizer 無法使用，反之亦然。</span><span class="sxs-lookup"><span data-stu-id="9afeb-113">If a GrammarRecognizer or KeywordRecognizer is active, a DictationRecognizer can't be active and vice versa.</span></span>

## <a name="enabling-the-capability-for-voice"></a><span data-ttu-id="9afeb-114">啟用語音的功能</span><span class="sxs-lookup"><span data-stu-id="9afeb-114">Enabling the capability for Voice</span></span>

<span data-ttu-id="9afeb-115">必須為應用程式宣告 **麥克風** 功能，才能使用語音輸入。</span><span class="sxs-lookup"><span data-stu-id="9afeb-115">The **Microphone** capability must be declared for an app to use Voice input.</span></span>
1. <span data-ttu-id="9afeb-116">在 Unity 編輯器中，流覽至 **> Player 編輯 > 專案設定**</span><span class="sxs-lookup"><span data-stu-id="9afeb-116">In the Unity Editor, navigate to **Edit > Project Settings > Player**</span></span>
2. <span data-ttu-id="9afeb-117">選取 [ **Windows 存放區** ] 索引標籤</span><span class="sxs-lookup"><span data-stu-id="9afeb-117">Select the **Windows Store** tab</span></span>
3. <span data-ttu-id="9afeb-118">在 [ **發佈設定 > 功能** ] 區段中，檢查 **麥克風** 功能</span><span class="sxs-lookup"><span data-stu-id="9afeb-118">In the **Publishing Settings > Capabilities** section, check the **Microphone** capability</span></span>
4. <span data-ttu-id="9afeb-119">在 HoloLens 裝置上將許可權授與應用程式以進行麥克風存取</span><span class="sxs-lookup"><span data-stu-id="9afeb-119">Grant permissions to the app for microphone access on your HoloLens device</span></span>
    * <span data-ttu-id="9afeb-120">系統會要求您在裝置啟動時這麼做，但如果您不小心按一下 [否]，您可以變更裝置設定中的許可權</span><span class="sxs-lookup"><span data-stu-id="9afeb-120">You'll be asked to do this on device startup, but if you accidentally clicked "no" you can change the permissions in the device settings</span></span>

## <a name="phrase-recognition"></a><span data-ttu-id="9afeb-121">片語辨識</span><span class="sxs-lookup"><span data-stu-id="9afeb-121">Phrase Recognition</span></span>

<span data-ttu-id="9afeb-122">若要讓您的應用程式接聽使用者所說的特定片語，請採取一些動作，您必須：</span><span class="sxs-lookup"><span data-stu-id="9afeb-122">To enable your app to listen for specific phrases spoken by the user then take some action, you need to:</span></span>
1. <span data-ttu-id="9afeb-123">使用或指定要接聽的片語 `KeywordRecognizer``GrammarRecognizer`</span><span class="sxs-lookup"><span data-stu-id="9afeb-123">Specify which phrases to listen for using a `KeywordRecognizer` or `GrammarRecognizer`</span></span>
2. <span data-ttu-id="9afeb-124">處理 `OnPhraseRecognized` 事件，並採取對應至已辨識片語的動作</span><span class="sxs-lookup"><span data-stu-id="9afeb-124">Handle the `OnPhraseRecognized` event and take action corresponding to the phrase recognized</span></span>

### <a name="keywordrecognizer"></a><span data-ttu-id="9afeb-125">KeywordRecognizer</span><span class="sxs-lookup"><span data-stu-id="9afeb-125">KeywordRecognizer</span></span>

<span data-ttu-id="9afeb-126">**命名空間：** *UnityEngine*</span><span class="sxs-lookup"><span data-stu-id="9afeb-126">**Namespace:** *UnityEngine.Windows.Speech*</span></span><br>
<span data-ttu-id="9afeb-127">**類型：** *KeywordRecognizer*、 *PhraseRecognizedEventArgs*、 *SpeechError*、 *SpeechSystemStatus*</span><span class="sxs-lookup"><span data-stu-id="9afeb-127">**Types:** *KeywordRecognizer*, *PhraseRecognizedEventArgs*, *SpeechError*, *SpeechSystemStatus*</span></span>

<span data-ttu-id="9afeb-128">我們需要一些 using 語句來節省一些按鍵：</span><span class="sxs-lookup"><span data-stu-id="9afeb-128">We'll need a few using statements to save some keystrokes:</span></span>

```
using UnityEngine.Windows.Speech;
using System.Collections.Generic;
using System.Linq;
```

<span data-ttu-id="9afeb-129">然後讓我們將幾個欄位新增至您的類別，以儲存辨識器和關鍵字 >動作字典：</span><span class="sxs-lookup"><span data-stu-id="9afeb-129">Then let's add a few fields to your class to store the recognizer and keyword->action dictionary:</span></span>

```
KeywordRecognizer keywordRecognizer;
Dictionary<string, System.Action> keywords = new Dictionary<string, System.Action>();
```

<span data-ttu-id="9afeb-130">現在將關鍵字加入至字典，例如，在 `Start()` 方法中。</span><span class="sxs-lookup"><span data-stu-id="9afeb-130">Now add a keyword to the dictionary, for example in of a `Start()` method.</span></span> <span data-ttu-id="9afeb-131">在此範例中，我們要新增 "activate" 關鍵字：</span><span class="sxs-lookup"><span data-stu-id="9afeb-131">We're adding the "activate" keyword in this example:</span></span>

```
//Create keywords for keyword recognizer
keywords.Add("activate", () =>
{
    // action to be performed when this keyword is spoken
});
```

<span data-ttu-id="9afeb-132">建立關鍵字辨識器並告訴它要辨識的內容：</span><span class="sxs-lookup"><span data-stu-id="9afeb-132">Create the keyword recognizer and tell it what we want to recognize:</span></span>

```
keywordRecognizer = new KeywordRecognizer(keywords.Keys.ToArray());
```

<span data-ttu-id="9afeb-133">現在報名 `OnPhraseRecognized` 活動</span><span class="sxs-lookup"><span data-stu-id="9afeb-133">Now register for the `OnPhraseRecognized` event</span></span>

```
keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
```

<span data-ttu-id="9afeb-134">範例處理常式如下：</span><span class="sxs-lookup"><span data-stu-id="9afeb-134">An example handler is:</span></span>

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

<span data-ttu-id="9afeb-135">最後，開始辨識！</span><span class="sxs-lookup"><span data-stu-id="9afeb-135">Finally, start recognizing!</span></span>

```
keywordRecognizer.Start();
```

### <a name="grammarrecognizer"></a><span data-ttu-id="9afeb-136">GrammarRecognizer</span><span class="sxs-lookup"><span data-stu-id="9afeb-136">GrammarRecognizer</span></span>

<span data-ttu-id="9afeb-137">**命名空間：** *UnityEngine*</span><span class="sxs-lookup"><span data-stu-id="9afeb-137">**Namespace:** *UnityEngine.Windows.Speech*</span></span><br>
<span data-ttu-id="9afeb-138">**類型**： *GrammarRecognizer*、 *PhraseRecognizedEventArgs*、 *SpeechError*、 *SpeechSystemStatus*</span><span class="sxs-lookup"><span data-stu-id="9afeb-138">**Types**: *GrammarRecognizer*, *PhraseRecognizedEventArgs*, *SpeechError*, *SpeechSystemStatus*</span></span>

<span data-ttu-id="9afeb-139">如果您要使用 SRGS 指定辨識文法，則會使用 GrammarRecognizer。</span><span class="sxs-lookup"><span data-stu-id="9afeb-139">The GrammarRecognizer is used if you're specifying your recognition grammar using SRGS.</span></span> <span data-ttu-id="9afeb-140">如果您的應用程式有多個關鍵字，如果您想要辨識更複雜的片語，或是想要輕鬆開啟和關閉命令集，這會很有用。</span><span class="sxs-lookup"><span data-stu-id="9afeb-140">This can be useful if your app has more than just a few keywords, if you want to recognize more complex phrases, or if you want to easily turn on and off sets of commands.</span></span> <span data-ttu-id="9afeb-141">請參閱： [使用 SRGS XML 建立](/previous-versions/office/developer/speech-technologies/hh378349(v=office.14)) 檔案格式資訊的文法。</span><span class="sxs-lookup"><span data-stu-id="9afeb-141">See: [Create Grammars Using SRGS XML](/previous-versions/office/developer/speech-technologies/hh378349(v=office.14)) for file format information.</span></span>

<span data-ttu-id="9afeb-142">一旦您有 SRGS 文法，而且它位於 [StreamingAssets 資料夾](https://docs.unity3d.com/Manual/StreamingAssets.html)的專案中：</span><span class="sxs-lookup"><span data-stu-id="9afeb-142">Once you have your SRGS grammar, and it is in your project in a [StreamingAssets folder](https://docs.unity3d.com/Manual/StreamingAssets.html):</span></span>

```
<PROJECT_ROOT>/Assets/StreamingAssets/SRGS/myGrammar.xml
```

<span data-ttu-id="9afeb-143">建立 `GrammarRecognizer` ，並將路徑傳遞至您的 SRGS 檔案：</span><span class="sxs-lookup"><span data-stu-id="9afeb-143">Create a `GrammarRecognizer` and pass it the path to your SRGS file:</span></span>

```
private GrammarRecognizer grammarRecognizer;
grammarRecognizer = new GrammarRecognizer(Application.streamingDataPath + "/SRGS/myGrammar.xml");
```

<span data-ttu-id="9afeb-144">現在報名 `OnPhraseRecognized` 活動</span><span class="sxs-lookup"><span data-stu-id="9afeb-144">Now register for the `OnPhraseRecognized` event</span></span>

```
grammarRecognizer.OnPhraseRecognized += grammarRecognizer_OnPhraseRecognized;
```

<span data-ttu-id="9afeb-145">您將會取得一個回呼，其中包含您可以適當處理的 SRGS 文法中指定的資訊。</span><span class="sxs-lookup"><span data-stu-id="9afeb-145">You'll get a callback containing information specified in your SRGS grammar, which you can handle appropriately.</span></span> <span data-ttu-id="9afeb-146">最重要的資訊將會在陣列中提供 `semanticMeanings` 。</span><span class="sxs-lookup"><span data-stu-id="9afeb-146">Most of the important information will be provided in the `semanticMeanings` array.</span></span>

```
private void Grammar_OnPhraseRecognized(PhraseRecognizedEventArgs args)
{
    SemanticMeaning[] meanings = args.semanticMeanings;
    // do something
}
```

<span data-ttu-id="9afeb-147">最後，開始辨識！</span><span class="sxs-lookup"><span data-stu-id="9afeb-147">Finally, start recognizing!</span></span>

```
grammarRecognizer.Start();
```

## <a name="dictation"></a><span data-ttu-id="9afeb-148">聽寫</span><span class="sxs-lookup"><span data-stu-id="9afeb-148">Dictation</span></span>

<span data-ttu-id="9afeb-149">**命名空間：** *UnityEngine*</span><span class="sxs-lookup"><span data-stu-id="9afeb-149">**Namespace:** *UnityEngine.Windows.Speech*</span></span><br>
<span data-ttu-id="9afeb-150">**類型**： *DictationRecognizer*、 *SpeechError*、 *SpeechSystemStatus*</span><span class="sxs-lookup"><span data-stu-id="9afeb-150">**Types**: *DictationRecognizer*, *SpeechError*, *SpeechSystemStatus*</span></span>

<span data-ttu-id="9afeb-151">使用將 `DictationRecognizer` 使用者的語音轉換成文字。</span><span class="sxs-lookup"><span data-stu-id="9afeb-151">Use the `DictationRecognizer` to convert the user's speech to text.</span></span> <span data-ttu-id="9afeb-152">DictationRecognizer 會公開 [聽寫](../../design/voice-input.md#dictation) 功能，並支援註冊和接聽假設和片語完成的事件，讓您可以在使用者說話和之後，將意見反應提供給您的使用者。</span><span class="sxs-lookup"><span data-stu-id="9afeb-152">The DictationRecognizer exposes [dictation](../../design/voice-input.md#dictation) functionality and supports registering and listening for hypothesis and phrase completed events, so you can give feedback to your user both while they speak and afterwards.</span></span> <span data-ttu-id="9afeb-153">`Start()` 和 `Stop()` 方法分別啟用和停用聽寫識別。</span><span class="sxs-lookup"><span data-stu-id="9afeb-153">`Start()` and `Stop()` methods respectively enable and disable dictation recognition.</span></span> <span data-ttu-id="9afeb-154">完成辨識器之後，應該使用來處置它 `Dispose()` 所使用的資源。</span><span class="sxs-lookup"><span data-stu-id="9afeb-154">Once done with the recognizer, it should be disposed using `Dispose()` to release the resources it uses.</span></span> <span data-ttu-id="9afeb-155">如果未在這之前釋出這些資源，它會在垃圾收集期間自動釋出這些資源。</span><span class="sxs-lookup"><span data-stu-id="9afeb-155">It will release these resources automatically during garbage collection at an extra performance cost if they aren't released before that.</span></span>

<span data-ttu-id="9afeb-156">開始使用聽寫只需要幾個步驟：</span><span class="sxs-lookup"><span data-stu-id="9afeb-156">There are only a few steps needed to get started with dictation:</span></span>
1. <span data-ttu-id="9afeb-157">建立新的 `DictationRecognizer`</span><span class="sxs-lookup"><span data-stu-id="9afeb-157">Create a new `DictationRecognizer`</span></span>
2. <span data-ttu-id="9afeb-158">處理聽寫事件</span><span class="sxs-lookup"><span data-stu-id="9afeb-158">Handle Dictation events</span></span>
3. <span data-ttu-id="9afeb-159">啟動 DictationRecognizer</span><span class="sxs-lookup"><span data-stu-id="9afeb-159">Start the DictationRecognizer</span></span>

### <a name="enabling-the-capability-for-dictation"></a><span data-ttu-id="9afeb-160">啟用聽寫功能</span><span class="sxs-lookup"><span data-stu-id="9afeb-160">Enabling the capability for dictation</span></span>

<span data-ttu-id="9afeb-161">您必須為應用程式宣告 **網際網路用戶端** 和 **麥克風** 功能，才能使用聽寫：</span><span class="sxs-lookup"><span data-stu-id="9afeb-161">The **Internet Client** and **Microphone** capabilities must be declared for an app to use dictation:</span></span>
1. <span data-ttu-id="9afeb-162">在 Unity 編輯器中，移至 **> Player 編輯 > 專案設定**</span><span class="sxs-lookup"><span data-stu-id="9afeb-162">In the Unity Editor, go to **Edit > Project Settings > Player**</span></span>
2. <span data-ttu-id="9afeb-163">在 Windows [ **存放區** ] 索引標籤上選取</span><span class="sxs-lookup"><span data-stu-id="9afeb-163">Select on the **Windows Store** tab</span></span>
3. <span data-ttu-id="9afeb-164">在 [ **發佈設定 > 功能** ] 區段中，檢查 **InternetClient** 功能</span><span class="sxs-lookup"><span data-stu-id="9afeb-164">In the **Publishing Settings > Capabilities** section, check the **InternetClient** capability</span></span>
    * <span data-ttu-id="9afeb-165">（選擇性）如果您還未啟用麥克風，請檢查 **麥克風** 功能</span><span class="sxs-lookup"><span data-stu-id="9afeb-165">Optionally, if you didn't already enable the microphone, check the **Microphone** capability</span></span>
4. <span data-ttu-id="9afeb-166">在 HoloLens 裝置上將許可權授與應用程式以進行麥克風存取（如果您尚未這樣做）</span><span class="sxs-lookup"><span data-stu-id="9afeb-166">Grant permissions to the app for microphone access on your HoloLens device if you haven't already</span></span>
    * <span data-ttu-id="9afeb-167">系統會要求您在裝置啟動時這麼做，但如果您不小心按一下 [否]，您可以變更裝置設定中的許可權</span><span class="sxs-lookup"><span data-stu-id="9afeb-167">You'll be asked to do this on device startup, but if you accidentally clicked "no" you can change the permissions in the device settings</span></span>

### <a name="dictationrecognizer"></a><span data-ttu-id="9afeb-168">DictationRecognizer</span><span class="sxs-lookup"><span data-stu-id="9afeb-168">DictationRecognizer</span></span>

<span data-ttu-id="9afeb-169">建立 DictationRecognizer，如下所示：</span><span class="sxs-lookup"><span data-stu-id="9afeb-169">Create a DictationRecognizer like so:</span></span>

```
dictationRecognizer = new DictationRecognizer();
```

<span data-ttu-id="9afeb-170">有四個聽寫事件可供訂閱和處理，以實行聽寫行為。</span><span class="sxs-lookup"><span data-stu-id="9afeb-170">There are four dictation events that can be subscribed to and handled to implement dictation behavior.</span></span>
1. `DictationResult`
2. `DictationComplete`
3. `DictationHypothesis`
4. `DictationError`

<span data-ttu-id="9afeb-171">**DictationResult**</span><span class="sxs-lookup"><span data-stu-id="9afeb-171">**DictationResult**</span></span>

<span data-ttu-id="9afeb-172">此事件會在使用者暫停（通常是在句子結尾）時引發。</span><span class="sxs-lookup"><span data-stu-id="9afeb-172">This event is fired after the user pauses, typically at the end of a sentence.</span></span> <span data-ttu-id="9afeb-173">在這裡會傳回完整的可辨識字串。</span><span class="sxs-lookup"><span data-stu-id="9afeb-173">The full recognized string is returned here.</span></span>

<span data-ttu-id="9afeb-174">首先，訂閱 `DictationResult` 事件：</span><span class="sxs-lookup"><span data-stu-id="9afeb-174">First, subscribe to the `DictationResult` event:</span></span>

```
dictationRecognizer.DictationResult += DictationRecognizer_DictationResult;
```

<span data-ttu-id="9afeb-175">然後處理 DictationResult 回呼：</span><span class="sxs-lookup"><span data-stu-id="9afeb-175">Then handle the DictationResult callback:</span></span>

```
private void DictationRecognizer_DictationResult(string text, ConfidenceLevel confidence)
{
    // do something
}
```

<span data-ttu-id="9afeb-176">**DictationHypothesis**</span><span class="sxs-lookup"><span data-stu-id="9afeb-176">**DictationHypothesis**</span></span>

<span data-ttu-id="9afeb-177">此事件會在使用者進行交談時持續引發。</span><span class="sxs-lookup"><span data-stu-id="9afeb-177">This event is fired continuously while the user is talking.</span></span> <span data-ttu-id="9afeb-178">當辨識器接聽時，它會提供到目前為止所聽過的文字。</span><span class="sxs-lookup"><span data-stu-id="9afeb-178">As the recognizer listens, it provides text of what it's heard so far.</span></span>

<span data-ttu-id="9afeb-179">首先，訂閱 `DictationHypothesis` 事件：</span><span class="sxs-lookup"><span data-stu-id="9afeb-179">First, subscribe to the `DictationHypothesis` event:</span></span>

```
dictationRecognizer.DictationHypothesis += DictationRecognizer_DictationHypothesis;
```

<span data-ttu-id="9afeb-180">然後處理 DictationHypothesis 回呼：</span><span class="sxs-lookup"><span data-stu-id="9afeb-180">Then handle the DictationHypothesis callback:</span></span>

```
private void DictationRecognizer_DictationHypothesis(string text)
{
    // do something
}
```

<span data-ttu-id="9afeb-181">**DictationComplete**</span><span class="sxs-lookup"><span data-stu-id="9afeb-181">**DictationComplete**</span></span>

<span data-ttu-id="9afeb-182">此事件會在辨識器停止時引發，不論是從停止 ( # A1 呼叫、發生超時或其他錯誤。</span><span class="sxs-lookup"><span data-stu-id="9afeb-182">This event is fired when the recognizer stops, whether from Stop() being called, a timeout occurring, or some other error.</span></span>

<span data-ttu-id="9afeb-183">首先，訂閱 `DictationComplete` 事件：</span><span class="sxs-lookup"><span data-stu-id="9afeb-183">First, subscribe to the `DictationComplete` event:</span></span>

```
dictationRecognizer.DictationComplete += DictationRecognizer_DictationComplete;
```

<span data-ttu-id="9afeb-184">然後處理 DictationComplete 回呼：</span><span class="sxs-lookup"><span data-stu-id="9afeb-184">Then handle the DictationComplete callback:</span></span>

```
private void DictationRecognizer_DictationComplete(DictationCompletionCause cause)
{
   // do something
}
```

<span data-ttu-id="9afeb-185">**DictationError**</span><span class="sxs-lookup"><span data-stu-id="9afeb-185">**DictationError**</span></span>

<span data-ttu-id="9afeb-186">發生錯誤時，就會引發此事件。</span><span class="sxs-lookup"><span data-stu-id="9afeb-186">This event is fired when an error occurs.</span></span>

<span data-ttu-id="9afeb-187">首先，訂閱 `DictationError` 事件：</span><span class="sxs-lookup"><span data-stu-id="9afeb-187">First, subscribe to the `DictationError` event:</span></span>

```
dictationRecognizer.DictationError += DictationRecognizer_DictationError;
```

<span data-ttu-id="9afeb-188">然後處理 DictationError 回呼：</span><span class="sxs-lookup"><span data-stu-id="9afeb-188">Then handle the DictationError callback:</span></span>

```
private void DictationRecognizer_DictationError(string error, int hresult)
{
    // do something
}
```

<span data-ttu-id="9afeb-189">當您訂閱並處理您所關心的聽寫事件之後，請啟動聽寫辨識器以開始接收事件。</span><span class="sxs-lookup"><span data-stu-id="9afeb-189">Once you've subscribed and handled the dictation events that you care about, start the dictation recognizer to begin receiving events.</span></span>

```
dictationRecognizer.Start();
```

<span data-ttu-id="9afeb-190">如果您不想再保留 DictationRecognizer，則需要取消訂閱事件並處置 DictationRecognizer。</span><span class="sxs-lookup"><span data-stu-id="9afeb-190">If you no longer want to keep the DictationRecognizer around, you need to unsubscribe from the events and Dispose the DictationRecognizer.</span></span>

```
dictationRecognizer.DictationResult -= DictationRecognizer_DictationResult;
dictationRecognizer.DictationComplete -= DictationRecognizer_DictationComplete ;
dictationRecognizer.DictationHypothesis -= DictationRecognizer_DictationHypothesis ;
dictationRecognizer.DictationError -= DictationRecognizer_DictationError ;
dictationRecognizer.Dispose();
```

<span data-ttu-id="9afeb-191">**提示**</span><span class="sxs-lookup"><span data-stu-id="9afeb-191">**Tips**</span></span>
* <span data-ttu-id="9afeb-192">`Start()` 和 `Stop()` 方法分別啟用和停用聽寫識別。</span><span class="sxs-lookup"><span data-stu-id="9afeb-192">`Start()` and `Stop()` methods respectively enable and disable dictation recognition.</span></span>
* <span data-ttu-id="9afeb-193">完成辨識器之後，必須使用來處置它 `Dispose()` 所使用的資源。</span><span class="sxs-lookup"><span data-stu-id="9afeb-193">Once done with the recognizer, it must be disposed using `Dispose()` to release the resources it uses.</span></span> <span data-ttu-id="9afeb-194">如果未在這之前釋出這些資源，它會在垃圾收集期間自動釋出這些資源。</span><span class="sxs-lookup"><span data-stu-id="9afeb-194">It will release these resources automatically during garbage collection at an extra performance cost if they aren't released before that.</span></span>
* <span data-ttu-id="9afeb-195">在設定的一段時間後發生超時。</span><span class="sxs-lookup"><span data-stu-id="9afeb-195">Timeouts occur after a set period of time.</span></span> <span data-ttu-id="9afeb-196">您可以檢查事件中的這些超時 `DictationComplete` 。</span><span class="sxs-lookup"><span data-stu-id="9afeb-196">You can check for these timeouts in the `DictationComplete` event.</span></span> <span data-ttu-id="9afeb-197">有兩個需要注意的超時：</span><span class="sxs-lookup"><span data-stu-id="9afeb-197">There are two timeouts to be aware of:</span></span>
   1. <span data-ttu-id="9afeb-198">如果辨識器啟動，但在前五秒沒有聽到任何音訊，則會超時。</span><span class="sxs-lookup"><span data-stu-id="9afeb-198">If the recognizer starts and doesn't hear any audio for the first five seconds, it will time out.</span></span>
   2. <span data-ttu-id="9afeb-199">如果辨識器已指定結果，但接著會聽到20秒的無回應，則會超時。</span><span class="sxs-lookup"><span data-stu-id="9afeb-199">If the recognizer has given a result, but then hears silence for 20 seconds, it will time out.</span></span>

## <a name="using-both-phrase-recognition-and-dictation"></a><span data-ttu-id="9afeb-200">使用片語辨識和聽寫</span><span class="sxs-lookup"><span data-stu-id="9afeb-200">Using both Phrase Recognition and Dictation</span></span>

<span data-ttu-id="9afeb-201">如果您想要在您的應用程式中同時使用片語辨識和聽寫，您必須完全關閉，才能啟動另一個。</span><span class="sxs-lookup"><span data-stu-id="9afeb-201">If you want to use both phrase recognition and dictation in your app, you'll need to fully shut one down before you can start the other.</span></span> <span data-ttu-id="9afeb-202">如果您有多個 KeywordRecognizers 正在執行，您可以將它們一次全部關閉：</span><span class="sxs-lookup"><span data-stu-id="9afeb-202">If you have multiple KeywordRecognizers running, you can shut them all down at once with:</span></span>

```
PhraseRecognitionSystem.Shutdown();
```

<span data-ttu-id="9afeb-203">在 DictationRecognizer 停止後，您可以呼叫 `Restart()` 將所有辨識器還原為先前的狀態：</span><span class="sxs-lookup"><span data-stu-id="9afeb-203">You can call `Restart()` to restore all recognizers to their previous state after the DictationRecognizer has stopped:</span></span>

```
PhraseRecognitionSystem.Restart();
```

<span data-ttu-id="9afeb-204">您也可以直接啟動 KeywordRecognizer，這也會重新開機 PhraseRecognitionSystem。</span><span class="sxs-lookup"><span data-stu-id="9afeb-204">You could also just start a KeywordRecognizer, which will restart the PhraseRecognitionSystem as well.</span></span>

## <a name="voice-input-in-mixed-reality-toolkit"></a><span data-ttu-id="9afeb-205">混合現實工具組中的語音輸入</span><span class="sxs-lookup"><span data-stu-id="9afeb-205">Voice input in Mixed Reality Toolkit</span></span>

<span data-ttu-id="9afeb-206">您可以在下列示範場景中找到語音輸入的 MRTK 範例：</span><span class="sxs-lookup"><span data-stu-id="9afeb-206">You can find MRTK examples for voice input in the following demo scenes:</span></span>
* [<span data-ttu-id="9afeb-207">聽寫</span><span class="sxs-lookup"><span data-stu-id="9afeb-207">Dictation</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MRTK/Examples/Demos/Input/Scenes/Dictation)
* [<span data-ttu-id="9afeb-208">語音</span><span class="sxs-lookup"><span data-stu-id="9afeb-208">Speech</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MRTK/Examples/Demos/Input/Scenes/Speech)

## <a name="next-development-checkpoint"></a><span data-ttu-id="9afeb-209">下一個開發檢查點</span><span class="sxs-lookup"><span data-stu-id="9afeb-209">Next Development Checkpoint</span></span>

<span data-ttu-id="9afeb-210">如果您要遵循我們所配置的 Unity 開發檢查點旅程，您接下來要探索混合現實平臺功能和 Api：</span><span class="sxs-lookup"><span data-stu-id="9afeb-210">If you're following the Unity development checkpoint journey we've laid out, you're next task is exploring the Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="9afeb-211">共用體驗</span><span class="sxs-lookup"><span data-stu-id="9afeb-211">Shared experiences</span></span>](shared-experiences-in-unity.md)

<span data-ttu-id="9afeb-212">您可以隨時回到 [Unity 開發檢查點](unity-development-overview.md#2-core-building-blocks)。</span><span class="sxs-lookup"><span data-stu-id="9afeb-212">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>