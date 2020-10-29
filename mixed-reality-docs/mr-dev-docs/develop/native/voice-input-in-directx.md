---
title: DirectX 中的語音輸入
description: 說明如何在適用于 Windows Mixed Reality 的 DirectX 應用程式中，執行語音命令和小片語和句子辨識。
author: mikeriches
ms.author: mriches
ms.date: 08/04/2020
ms.topic: article
keywords: 逐步解說、語音命令、片語、辨識、語音、directx、平臺、cortana、windows mixed reality
ms.openlocfilehash: bdd92f79b3dd9677ac5c2c64e532978477ac5bca
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2020
ms.locfileid: "91679325"
---
# <a name="voice-input-in-directx"></a><span data-ttu-id="a2900-104">DirectX 中的語音輸入</span><span class="sxs-lookup"><span data-stu-id="a2900-104">Voice input in DirectX</span></span>

> [!NOTE]
> <span data-ttu-id="a2900-105">本文與舊版 WinRT 原生 Api 相關。</span><span class="sxs-lookup"><span data-stu-id="a2900-105">This article relates to the legacy WinRT native APIs.</span></span>  <span data-ttu-id="a2900-106">針對新的原生應用程式專案，建議使用 **[OPENXR API](openxr-getting-started.md)** 。</span><span class="sxs-lookup"><span data-stu-id="a2900-106">For new native app projects, we recommend using the **[OpenXR API](openxr-getting-started.md)** .</span></span>

<span data-ttu-id="a2900-107">本文說明如何在 Windows Mixed Reality 的 DirectX 應用程式中，執行 [語音命令](../../design/voice-input.md) 加上小型片語和句子辨識。</span><span class="sxs-lookup"><span data-stu-id="a2900-107">This article explains how to implement [voice commands](../../design/voice-input.md) plus small-phrase and sentence recognition in a DirectX app for Windows Mixed Reality.</span></span>

>[!NOTE]
><span data-ttu-id="a2900-108">本文中的程式碼片段使用 c + +/CX，而不是 C + + 17 相容的 c + +/WinRT，它會用於 [c + + 全像專案範本](creating-a-holographic-directx-project.md)。</span><span class="sxs-lookup"><span data-stu-id="a2900-108">The code snippets in this article use C++/CX rather than C++17-compliant C++/WinRT, which is used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="a2900-109">這些概念對 c + +/WinRT 專案而言是相等的，但您需要轉譯程式碼。</span><span class="sxs-lookup"><span data-stu-id="a2900-109">The concepts are equivalent for a C++/WinRT project, but you need to translate the code.</span></span>

## <a name="use-speechrecognizer-for-continuous-speech-recognition"></a><span data-ttu-id="a2900-110">使用 SpeechRecognizer 進行連續語音辨識</span><span class="sxs-lookup"><span data-stu-id="a2900-110">Use SpeechRecognizer for continuous speech recognition</span></span>

<span data-ttu-id="a2900-111">本節說明如何使用連續的語音辨識，在您的應用程式中啟用語音命令。</span><span class="sxs-lookup"><span data-stu-id="a2900-111">This section describes how to use continuous speech recognition to enable voice commands in your app.</span></span> <span data-ttu-id="a2900-112">本逐步解說會使用 [HolographicVoiceInput](https://go.microsoft.com/fwlink/p/?LinkId=844964) 範例中的程式碼。</span><span class="sxs-lookup"><span data-stu-id="a2900-112">This walk-through uses code from the [HolographicVoiceInput](https://go.microsoft.com/fwlink/p/?LinkId=844964) sample.</span></span> <span data-ttu-id="a2900-113">當範例正在執行時，請說出其中一個已註冊的色彩命令名稱，以變更旋轉 cube 的色彩。</span><span class="sxs-lookup"><span data-stu-id="a2900-113">When the sample is running, speak the name of one of the registered color commands to change the color of the spinning cube.</span></span>

<span data-ttu-id="a2900-114">首先，建立新的 *Windows：： Media：： SpeechRecognition：： SpeechRecognizer* 實例。</span><span class="sxs-lookup"><span data-stu-id="a2900-114">First, create a new *Windows::Media::SpeechRecognition::SpeechRecognizer* instance.</span></span>

<span data-ttu-id="a2900-115">從 *HolographicVoiceInputSampleMain：： CreateSpeechConstraintsForCurrentState* ：</span><span class="sxs-lookup"><span data-stu-id="a2900-115">From *HolographicVoiceInputSampleMain::CreateSpeechConstraintsForCurrentState* :</span></span>

```
m_speechRecognizer = ref new SpeechRecognizer();
```

<span data-ttu-id="a2900-116">建立可供辨識器接聽的語音命令清單。</span><span class="sxs-lookup"><span data-stu-id="a2900-116">Create a list of speech commands for the recognizer to listen for.</span></span> <span data-ttu-id="a2900-117">在這裡，我們會建立一組命令來變更全像影像的色彩。</span><span class="sxs-lookup"><span data-stu-id="a2900-117">Here, we construct a set of commands to change the color of a hologram.</span></span> <span data-ttu-id="a2900-118">為了方便起見，我們也會建立稍後將用於命令的資料。</span><span class="sxs-lookup"><span data-stu-id="a2900-118">For convenience, we also create the data that we'll use for the commands later.</span></span>

```
m_speechCommandList = ref new Platform::Collections::Vector<String^>();
   m_speechCommandData.clear();
   m_speechCommandList->Append(StringReference(L"white"));
   m_speechCommandData.push_back(float4(1.f, 1.f, 1.f, 1.f));
   m_speechCommandList->Append(StringReference(L"grey"));
   m_speechCommandData.push_back(float4(0.5f, 0.5f, 0.5f, 1.f));
   m_speechCommandList->Append(StringReference(L"green"));
   m_speechCommandData.push_back(float4(0.f, 1.f, 0.f, 1.f));
   m_speechCommandList->Append(StringReference(L"black"));
   m_speechCommandData.push_back(float4(0.1f, 0.1f, 0.1f, 1.f));
   m_speechCommandList->Append(StringReference(L"red"));
   m_speechCommandData.push_back(float4(1.f, 0.f, 0.f, 1.f));
   m_speechCommandList->Append(StringReference(L"yellow"));
   m_speechCommandData.push_back(float4(1.f, 1.f, 0.f, 1.f));
   m_speechCommandList->Append(StringReference(L"aquamarine"));
   m_speechCommandData.push_back(float4(0.f, 1.f, 1.f, 1.f));
   m_speechCommandList->Append(StringReference(L"blue"));
   m_speechCommandData.push_back(float4(0.f, 0.f, 1.f, 1.f));
   m_speechCommandList->Append(StringReference(L"purple"));
   m_speechCommandData.push_back(float4(1.f, 0.f, 1.f, 1.f));
```

<span data-ttu-id="a2900-119">您可以使用字典中可能不會有的語音字來指定命令。</span><span class="sxs-lookup"><span data-stu-id="a2900-119">You can use phonetic words that might not be in a dictionary to specify commands.</span></span>

```
m_speechCommandList->Append(StringReference(L"SpeechRecognizer"));
   m_speechCommandData.push_back(float4(0.5f, 0.1f, 1.f, 1.f));
```

<span data-ttu-id="a2900-120">若要在語音辨識器的條件約束清單中載入命令清單，請使用 [SpeechRecognitionListConstraint](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechrecognitionlistconstraint.aspx) 物件。</span><span class="sxs-lookup"><span data-stu-id="a2900-120">To load the commands list into the list of constraints for the speech recognizer use a [SpeechRecognitionListConstraint](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechrecognitionlistconstraint.aspx) object.</span></span>

```
SpeechRecognitionListConstraint^ spConstraint = ref new SpeechRecognitionListConstraint(m_speechCommandList);
   m_speechRecognizer->Constraints->Clear();
   m_speechRecognizer->Constraints->Append(spConstraint);
   create_task(m_speechRecognizer->CompileConstraintsAsync()).then([this](SpeechRecognitionCompilationResult^ compilationResult)
   {
       if (compilationResult->Status == SpeechRecognitionResultStatus::Success)
       {
           m_speechRecognizer->ContinuousRecognitionSession->StartAsync();
       }
       else
       {
           // Handle errors here.
       }
   });
```

<span data-ttu-id="a2900-121">在語音辨識器的[SpeechContinuousRecognitionSession](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionsession.aspx)上訂閱[ResultGenerated](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionsession.resultgenerated.aspx)事件。</span><span class="sxs-lookup"><span data-stu-id="a2900-121">Subscribe to the [ResultGenerated](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionsession.resultgenerated.aspx) event on the speech recognizer's [SpeechContinuousRecognitionSession](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionsession.aspx).</span></span> <span data-ttu-id="a2900-122">此事件會在已辨識您的其中一個命令時通知您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="a2900-122">This event notifies your app when one of your commands has been recognized.</span></span>

```
m_speechRecognizer->ContinuousRecognitionSession->ResultGenerated +=
       ref new TypedEventHandler<SpeechContinuousRecognitionSession^, SpeechContinuousRecognitionResultGeneratedEventArgs^>(
           std::bind(&HolographicVoiceInputSampleMain::OnResultGenerated, this, _1, _2)
           );
```

<span data-ttu-id="a2900-123">*OnResultGenerated* 事件處理常式會接收 [SpeechContinuousRecognitionResultGeneratedEventArgs](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionresultgeneratedeventargs.aspx)實例中的事件資料。</span><span class="sxs-lookup"><span data-stu-id="a2900-123">Your *OnResultGenerated* event handler receives event data in a [SpeechContinuousRecognitionResultGeneratedEventArgs](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionresultgeneratedeventargs.aspx) instance.</span></span> <span data-ttu-id="a2900-124">如果信賴度大於您所定義的閾值，您的應用程式應該會注意到事件發生。</span><span class="sxs-lookup"><span data-stu-id="a2900-124">If the confidence is greater than the threshold that you defined, your app should note that the event happened.</span></span> <span data-ttu-id="a2900-125">儲存事件資料，讓您可以在後續的更新迴圈中使用它。</span><span class="sxs-lookup"><span data-stu-id="a2900-125">Save the event data so that you can use it in a subsequent update loop.</span></span>

<span data-ttu-id="a2900-126">從 *HolographicVoiceInputSampleMain .cpp* ：</span><span class="sxs-lookup"><span data-stu-id="a2900-126">From *HolographicVoiceInputSampleMain.cpp* :</span></span>

```
// Change the cube color, if we get a valid result.
   void HolographicVoiceInputSampleMain::OnResultGenerated(SpeechContinuousRecognitionSession ^sender, SpeechContinuousRecognitionResultGeneratedEventArgs ^args)
   {
       if (args->Result->RawConfidence > 0.5f)
       {
           m_lastCommand = args->Result->Text;
       }
   }
```

<span data-ttu-id="a2900-127">在我們的範例程式碼中，我們會根據使用者的命令變更旋轉全息圖 cube 的色彩。</span><span class="sxs-lookup"><span data-stu-id="a2900-127">In our example code, we change the color of the spinning hologram cube according to the user's command.</span></span>

<span data-ttu-id="a2900-128">從 *HolographicVoiceInputSampleMain：： Update* ：</span><span class="sxs-lookup"><span data-stu-id="a2900-128">From *HolographicVoiceInputSampleMain::Update* :</span></span>

```
// Check for new speech input since the last frame.
   if (m_lastCommand != nullptr)
   {
       auto command = m_lastCommand;
       m_lastCommand = nullptr;

       int i = 0;
       for each (auto& iter in m_speechCommandList)
       {
           if (iter == command)
           {
               m_spinningCubeRenderer->SetColor(m_speechCommandData[i]);
               break;
           }

           ++i;
       }
   }
```

## <a name="use-one-shot-recognition"></a><span data-ttu-id="a2900-129">使用「一次」辨識</span><span class="sxs-lookup"><span data-stu-id="a2900-129">Use "one-shot" recognition</span></span>

<span data-ttu-id="a2900-130">您可以設定語音辨識器來接聽使用者說話的片語或句子。</span><span class="sxs-lookup"><span data-stu-id="a2900-130">You can configure a speech recognizer to listen for phrases or sentences that the user speaks.</span></span> <span data-ttu-id="a2900-131">在此情況下，我們會套用 *SpeechRecognitionTopicConstraint* ，告知語音辨識器預期的輸入類型。</span><span class="sxs-lookup"><span data-stu-id="a2900-131">In this case, we apply a *SpeechRecognitionTopicConstraint* that tells the speech recognizer what type of input to expect.</span></span> <span data-ttu-id="a2900-132">以下是此案例的應用程式工作流程：</span><span class="sxs-lookup"><span data-stu-id="a2900-132">Here's an app workflow for this scenario:</span></span>
1. <span data-ttu-id="a2900-133">您的應用程式會建立 SpeechRecognizer、提供 UI 提示，並開始接聽語音命令。</span><span class="sxs-lookup"><span data-stu-id="a2900-133">Your app creates the SpeechRecognizer, provides UI prompts, and starts listening for a spoken command.</span></span>
2. <span data-ttu-id="a2900-134">使用者會說出片語或句子。</span><span class="sxs-lookup"><span data-stu-id="a2900-134">The user speaks a phrase or sentence.</span></span>
3. <span data-ttu-id="a2900-135">使用者語音的辨識會發生，並將結果傳回給應用程式。</span><span class="sxs-lookup"><span data-stu-id="a2900-135">Recognition of the user's speech occurs, and a result is returned to the app.</span></span> <span data-ttu-id="a2900-136">此時，您的應用程式應該提供 UI 提示，指出已發生辨識。</span><span class="sxs-lookup"><span data-stu-id="a2900-136">At this point, your app should provide a UI prompt to indicate that recognition has occurred.</span></span>
4. <span data-ttu-id="a2900-137">根據您想要回應的信賴等級和語音辨識結果的信賴等級，您的應用程式可以處理結果並適當地回應。</span><span class="sxs-lookup"><span data-stu-id="a2900-137">Depending on the confidence level that you want to respond to and the confidence level of the speech recognition result, your app can process the result and respond as appropriate.</span></span>

<span data-ttu-id="a2900-138">本節說明如何建立 SpeechRecognizer、編譯條件約束，以及接聽語音輸入。</span><span class="sxs-lookup"><span data-stu-id="a2900-138">This section describes how to create a SpeechRecognizer, compile the constraint, and listen for speech input.</span></span>

<span data-ttu-id="a2900-139">下列程式碼會編譯主題條件約束，在此案例中是針對 web 搜尋進行優化。</span><span class="sxs-lookup"><span data-stu-id="a2900-139">The following code compiles the topic constraint, which in this case is optimized for web search.</span></span>

```
auto constraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::WebSearch, L"webSearch");
   m_speechRecognizer->Constraints->Clear();
   m_speechRecognizer->Constraints->Append(constraint);
   return create_task(m_speechRecognizer->CompileConstraintsAsync())
       .then([this](task<SpeechRecognitionCompilationResult^> previousTask)
   {
```

<span data-ttu-id="a2900-140">如果編譯成功，我們可以繼續進行語音辨識。</span><span class="sxs-lookup"><span data-stu-id="a2900-140">If compilation succeeds, we can proceed with speech recognition.</span></span>

```
try
       {
           SpeechRecognitionCompilationResult^ compilationResult = previousTask.get();

           // Check to make sure that the constraints were in a proper format and the recognizer was able to compile it.
           if (compilationResult->Status == SpeechRecognitionResultStatus::Success)
           {
               // If the compilation succeeded, we can start listening for the user's spoken phrase or sentence.
               create_task(m_speechRecognizer->RecognizeAsync()).then([this](task<SpeechRecognitionResult^>& previousTask)
               {
```

<span data-ttu-id="a2900-141">然後，結果會傳回給應用程式。</span><span class="sxs-lookup"><span data-stu-id="a2900-141">The result is then returned to the app.</span></span> <span data-ttu-id="a2900-142">如果有足夠的結果，我們可以處理這個命令。</span><span class="sxs-lookup"><span data-stu-id="a2900-142">If we're confident enough in the result, we can process the command.</span></span> <span data-ttu-id="a2900-143">這個程式碼範例會處理至少有中度信賴的結果。</span><span class="sxs-lookup"><span data-stu-id="a2900-143">This code example processes results with at least medium confidence.</span></span>

```
try
                   {
                       auto result = previousTask.get();

                       if (result->Status != SpeechRecognitionResultStatus::Success)
                       {
                           PrintWstringToDebugConsole(
                               std::wstring(L"Speech recognition was not successful: ") +
                               result->Status.ToString()->Data() +
                               L"\n"
                               );
                       }

                       // In this example, we look for at least medium confidence in the speech result.
                       if ((result->Confidence == SpeechRecognitionConfidence::High) ||
                           (result->Confidence == SpeechRecognitionConfidence::Medium))
                       {
                           // If the user said a color name anywhere in their phrase, it will be recognized in the
                           // Update loop; then, the cube will change color.
                           m_lastCommand = result->Text;

                           PrintWstringToDebugConsole(
                               std::wstring(L"Speech phrase was: ") +
                               m_lastCommand->Data() +
                               L"\n"
                               );
                       }
                       else
                       {
                           PrintWstringToDebugConsole(
                               std::wstring(L"Recognition confidence not high enough: ") +
                               result->Confidence.ToString()->Data() +
                               L"\n"
                               );
                       }
                   }
```

<span data-ttu-id="a2900-144">當您使用語音辨識時，請監看是否有可能指出使用者已關閉系統隱私權設定中麥克風的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="a2900-144">Whenever you use speech recognition, watch for exceptions that could indicate that the user has turned off the microphone in the system privacy settings.</span></span> <span data-ttu-id="a2900-145">這可能會在初始化或辨識期間發生。</span><span class="sxs-lookup"><span data-stu-id="a2900-145">This can happen during initialization or recognition.</span></span>

```
catch (Exception^ exception)
                   {
                       // Note that if you get an "Access is denied" exception, you might need to enable the microphone
                       // privacy setting on the device and/or add the microphone capability to your app manifest.

                       PrintWstringToDebugConsole(
                           std::wstring(L"Speech recognizer error: ") +
                           exception->ToString()->Data() +
                           L"\n"
                           );
                   }
               });

               return true;
           }
           else
           {
               OutputDebugStringW(L"Could not initialize predefined grammar speech engine!\n");

               // Handle errors here.
               return false;
           }
       }
       catch (Exception^ exception)
       {
           // Note that if you get an "Access is denied" exception, you might need to enable the microphone
           // privacy setting on the device and/or add the microphone capability to your app manifest.

           PrintWstringToDebugConsole(
               std::wstring(L"Exception while trying to initialize predefined grammar speech engine:") +
               exception->Message->Data() +
               L"\n"
               );

           // Handle exceptions here.
           return false;
       }
   });
```

> [!NOTE]
> <span data-ttu-id="a2900-146">您可以使用數個預先定義的 [SpeechRecognitionScenarios](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechrecognitionscenario.aspx) 來優化語音辨識。</span><span class="sxs-lookup"><span data-stu-id="a2900-146">There are several predefined [SpeechRecognitionScenarios](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechrecognitionscenario.aspx) that you can use to optimize speech recognition.</span></span>

* <span data-ttu-id="a2900-147">若要優化聽寫，請使用聽寫案例。</span><span class="sxs-lookup"><span data-stu-id="a2900-147">To optimize for dictation, use the dictation scenario.</span></span><br/>
   ```
   // Compile the dictation topic constraint, which optimizes for speech dictation.
   auto dictationConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::Dictation, "dictation");
   m_speechRecognizer->Constraints->Append(dictationConstraint);
   ```

* <span data-ttu-id="a2900-148">針對語音 web 搜尋，請使用下列 web 特定的案例條件約束。</span><span class="sxs-lookup"><span data-stu-id="a2900-148">For speech web searches, use the following web-specific scenario constraint.</span></span>

   ```
   // Add a web search topic constraint to the recognizer.
   auto webSearchConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::WebSearch, "webSearch");
   speechRecognizer->Constraints->Append(webSearchConstraint);
   ```

* <span data-ttu-id="a2900-149">使用表單條件約束來填滿表單。</span><span class="sxs-lookup"><span data-stu-id="a2900-149">Use the form constraint to fill out forms.</span></span> <span data-ttu-id="a2900-150">在此情況下，最好套用已針對填滿表單優化的文法。</span><span class="sxs-lookup"><span data-stu-id="a2900-150">In this case, it's best to apply your own grammar that's optimized for filling out the form.</span></span>

   ```
   // Add a form constraint to the recognizer.
   auto formConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::FormFilling, "formFilling");
   speechRecognizer->Constraints->Append(formConstraint );
   ```
* <span data-ttu-id="a2900-151">您可以用 SRGS 格式提供自己的文法。</span><span class="sxs-lookup"><span data-stu-id="a2900-151">You can provide your own grammar in the SRGS format.</span></span>

## <a name="use-continuous-recognition"></a><span data-ttu-id="a2900-152">使用連續辨識</span><span class="sxs-lookup"><span data-stu-id="a2900-152">Use continuous recognition</span></span>

<span data-ttu-id="a2900-153">如需持續聽寫的案例，請參閱 [WINDOWS 10 UWP 語音程式碼範例](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpeechRecognitionAndSynthesis/cpp/Scenario_ContinuousDictation.xaml.cpp)。</span><span class="sxs-lookup"><span data-stu-id="a2900-153">For the continuous-dictation scenario, see the [Windows 10 UWP speech code sample](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpeechRecognitionAndSynthesis/cpp/Scenario_ContinuousDictation.xaml.cpp).</span></span>

## <a name="handle-quality-degradation"></a><span data-ttu-id="a2900-154">處理品質降低</span><span class="sxs-lookup"><span data-stu-id="a2900-154">Handle quality degradation</span></span>

<span data-ttu-id="a2900-155">環境條件有時會干擾語音辨識。</span><span class="sxs-lookup"><span data-stu-id="a2900-155">Environmental conditions sometimes interfere with speech recognition.</span></span> <span data-ttu-id="a2900-156">例如，房間可能太過雜訊，或使用者可能會說太過大的聲音。</span><span class="sxs-lookup"><span data-stu-id="a2900-156">For example, the room might be too noisy, or the user might speak too loudly.</span></span> <span data-ttu-id="a2900-157">語音辨識 API 可能會盡可能提供導致品質降低的狀況相關資訊。</span><span class="sxs-lookup"><span data-stu-id="a2900-157">Whenever possible, the speech recognition API provides information about the conditions that caused the quality degradation.</span></span> <span data-ttu-id="a2900-158">這項資訊會透過 WinRT 事件推送到您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="a2900-158">This information is pushed to your app through a WinRT event.</span></span> <span data-ttu-id="a2900-159">下列範例顯示如何訂閱此事件。</span><span class="sxs-lookup"><span data-stu-id="a2900-159">The following example shows  how to subscribe to this event.</span></span>

```
m_speechRecognizer->RecognitionQualityDegrading +=
       ref new TypedEventHandler<SpeechRecognizer^, SpeechRecognitionQualityDegradingEventArgs^>(
           std::bind(&HolographicVoiceInputSampleMain::OnSpeechQualityDegraded, this, _1, _2)
           );
```

<span data-ttu-id="a2900-160">在我們的程式碼範例中，我們會將條件資訊寫入至 debug 主控台。</span><span class="sxs-lookup"><span data-stu-id="a2900-160">In our code sample, we write the conditions information to the debug console.</span></span> <span data-ttu-id="a2900-161">應用程式可能會想要透過 UI、語音合成和另一種方法，為使用者提供意見反應。</span><span class="sxs-lookup"><span data-stu-id="a2900-161">An app might want to provide feedback to the user through the UI, speech synthesis, and another method.</span></span> <span data-ttu-id="a2900-162">或者，當語音因品質暫時降低而中斷時，可能需要不同的行為。</span><span class="sxs-lookup"><span data-stu-id="a2900-162">Or it might need to behave differently when speech is interrupted by a temporary reduction in quality.</span></span>

```
void HolographicSpeechPromptSampleMain::OnSpeechQualityDegraded(SpeechRecognizer^ recognizer, SpeechRecognitionQualityDegradingEventArgs^ args)
   {
       switch (args->Problem)
       {
       case SpeechRecognitionAudioProblem::TooFast:
           OutputDebugStringW(L"The user spoke too quickly.\n");
           break;

       case SpeechRecognitionAudioProblem::TooSlow:
           OutputDebugStringW(L"The user spoke too slowly.\n");
           break;

       case SpeechRecognitionAudioProblem::TooQuiet:
           OutputDebugStringW(L"The user spoke too softly.\n");
           break;

       case SpeechRecognitionAudioProblem::TooLoud:
           OutputDebugStringW(L"The user spoke too loudly.\n");
           break;

       case SpeechRecognitionAudioProblem::TooNoisy:
           OutputDebugStringW(L"There is too much noise in the signal.\n");
           break;

       case SpeechRecognitionAudioProblem::NoSignal:
           OutputDebugStringW(L"There is no signal.\n");
           break;

       case SpeechRecognitionAudioProblem::None:
       default:
           OutputDebugStringW(L"An error was reported with no information.\n");
           break;
       }
   }
```

<span data-ttu-id="a2900-163">如果您不是使用 ref 類別來建立 DirectX 應用程式，則必須先取消訂閱事件，然後再發行或重新建立您的語音辨識器。</span><span class="sxs-lookup"><span data-stu-id="a2900-163">If you're not using ref classes to create your DirectX app, you must unsubscribe from the event before you release or recreate your speech recognizer.</span></span> <span data-ttu-id="a2900-164">HolographicSpeechPromptSample 具有可停止辨識和取消訂閱事件的常式。</span><span class="sxs-lookup"><span data-stu-id="a2900-164">The HolographicSpeechPromptSample has a routine to stop recognition and unsubscribe from events.</span></span>

```
Concurrency::task<void> HolographicSpeechPromptSampleMain::StopCurrentRecognizerIfExists()
   {
       return create_task([this]()
       {
           if (m_speechRecognizer != nullptr)
           {
               return create_task(m_speechRecognizer->StopRecognitionAsync()).then([this]()
               {
                   m_speechRecognizer->RecognitionQualityDegrading -= m_speechRecognitionQualityDegradedToken;

                   if (m_speechRecognizer->ContinuousRecognitionSession != nullptr)
                   {
                       m_speechRecognizer->ContinuousRecognitionSession->ResultGenerated -= m_speechRecognizerResultEventToken;
                   }
               });
           }
           else
           {
               return create_task([this]() { m_speechRecognizer = nullptr; });
           }
       });
   }
```

## <a name="use-speech-synthesis-to-provide-audible-prompts"></a><span data-ttu-id="a2900-165">使用語音合成提供可聽見的提示</span><span class="sxs-lookup"><span data-stu-id="a2900-165">Use speech synthesis to provide audible prompts</span></span>

<span data-ttu-id="a2900-166">「全像」語音範例會使用語音合成，為使用者提供有聲音的指示。</span><span class="sxs-lookup"><span data-stu-id="a2900-166">The holographic speech samples use speech synthesis to provide audible instructions to the user.</span></span> <span data-ttu-id="a2900-167">本節說明如何建立合成語音範例，然後透過 HRTF 音訊 Api 播放。</span><span class="sxs-lookup"><span data-stu-id="a2900-167">This section shows how to create a synthesized voice sample  and then play it back through the HRTF audio APIs.</span></span>

<span data-ttu-id="a2900-168">當您要求片語輸入時，您應該提供自己的語音提示。</span><span class="sxs-lookup"><span data-stu-id="a2900-168">You should provide your own speech prompts when you request phrase input.</span></span> <span data-ttu-id="a2900-169">提示也有助於指出語音命令可用於連續辨識案例的時機。</span><span class="sxs-lookup"><span data-stu-id="a2900-169">Prompts can also help indicate when speech commands can be spoken for a continuous-recognition scenario.</span></span> <span data-ttu-id="a2900-170">下列範例示範如何使用語音合成器來執行這項操作。</span><span class="sxs-lookup"><span data-stu-id="a2900-170">The following example demonstrates how to use a speech synthesizer to do this.</span></span> <span data-ttu-id="a2900-171">您也可以使用預先錄製的語音剪輯、視覺 UI 或其他指標，例如，在不是動態提示的情況下。</span><span class="sxs-lookup"><span data-stu-id="a2900-171">You could also use a pre-recorded voice clip, a visual UI, or another indicator of what to say, for example in scenarios where the prompt is not dynamic.</span></span>

<span data-ttu-id="a2900-172">首先，建立 SpeechSynthesizer 物件。</span><span class="sxs-lookup"><span data-stu-id="a2900-172">First, create the SpeechSynthesizer object.</span></span>

```
auto speechSynthesizer = ref new Windows::Media::SpeechSynthesis::SpeechSynthesizer();
```

<span data-ttu-id="a2900-173">您也需要包含要合成之文字的字串。</span><span class="sxs-lookup"><span data-stu-id="a2900-173">You also need a string that includes the text to  synthesize.</span></span>

```
// Phrase recognition works best when requesting a phrase or sentence.
   StringReference voicePrompt = L"At the prompt: Say a phrase, asking me to change the cube to a specific color.";
```

<span data-ttu-id="a2900-174">語音會透過 SynthesizeTextToStreamAsync 以非同步方式合成。</span><span class="sxs-lookup"><span data-stu-id="a2900-174">Speech is synthesized asynchronously through SynthesizeTextToStreamAsync.</span></span> <span data-ttu-id="a2900-175">在這裡，我們會啟動非同步工作以合成語音。</span><span class="sxs-lookup"><span data-stu-id="a2900-175">Here, we start an async task to synthesize the speech.</span></span>

```
create_task(speechSynthesizer->SynthesizeTextToStreamAsync(voicePrompt), task_continuation_context::use_current())
       .then([this, speechSynthesizer](task<Windows::Media::SpeechSynthesis::SpeechSynthesisStream^> synthesisStreamTask)
   {
       try
       {
```

<span data-ttu-id="a2900-176">語音合成會以位元組串流的形式傳送。</span><span class="sxs-lookup"><span data-stu-id="a2900-176">The speech synthesis is sent as a byte stream.</span></span> <span data-ttu-id="a2900-177">我們可以使用該位元組資料流程來初始化 XAudio2 聲音。</span><span class="sxs-lookup"><span data-stu-id="a2900-177">We can use that byte stream to initialize an XAudio2 voice.</span></span> <span data-ttu-id="a2900-178">針對我們的全像攝影程式碼範例，我們會以 HRTF 音訊效果的形式播放。</span><span class="sxs-lookup"><span data-stu-id="a2900-178">For our holographic code samples, we play it back as an HRTF audio effect.</span></span>

```
Windows::Media::SpeechSynthesis::SpeechSynthesisStream^ stream = synthesisStreamTask.get();

           auto hr = m_speechSynthesisSound.Initialize(stream, 0);
           if (SUCCEEDED(hr))
           {
               m_speechSynthesisSound.SetEnvironment(HrtfEnvironment::Small);
               m_speechSynthesisSound.Start();

               // Amount of time to pause after the audio prompt is complete, before listening
               // for speech input.
               static const float bufferTime = 0.15f;

               // Wait until the prompt is done before listening.
               m_secondsUntilSoundIsComplete = m_speechSynthesisSound.GetDuration() + bufferTime;
               m_waitingForSpeechPrompt = true;
           }
       }
```

<span data-ttu-id="a2900-179">如同語音辨識，如果發生問題，語音合成會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="a2900-179">As with speech recognition, speech synthesis throws an exception if something goes wrong.</span></span>

```
catch (Exception^ exception)
       {
           PrintWstringToDebugConsole(
               std::wstring(L"Exception while trying to synthesize speech: ") +
               exception->Message->Data() +
               L"\n"
               );

           // Handle exceptions here.
       }
   });
```

## <a name="see-also"></a><span data-ttu-id="a2900-180">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a2900-180">See also</span></span>
* [<span data-ttu-id="a2900-181">語音應用程式設計</span><span class="sxs-lookup"><span data-stu-id="a2900-181">Speech app design</span></span>](https://msdn.microsoft.com/library/dn596121.aspx)
* [<span data-ttu-id="a2900-182">SpeechRecognitionAndSynthesis 範例</span><span class="sxs-lookup"><span data-stu-id="a2900-182">SpeechRecognitionAndSynthesis sample</span></span>](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/SpeechRecognitionAndSynthesis)
