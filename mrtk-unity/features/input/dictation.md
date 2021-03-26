---
title: 聽寫
description: Docummentation 如何錄製音訊剪輯並在 MRTK 中取得轉譯
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: c273059310c380333700d0b588ee74d9e2ecabe2
ms.sourcegitcommit: ac315c1d35f2b9c431e79bc3f1212215301bb867
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105550538"
---
# <a name="dictation"></a><span data-ttu-id="57814-104">聽寫</span><span class="sxs-lookup"><span data-stu-id="57814-104">Dictation</span></span>

<span data-ttu-id="57814-105">聽寫可讓使用者錄製音訊剪輯並取得轉譯。</span><span class="sxs-lookup"><span data-stu-id="57814-105">Dictation allows users to record audio clips and obtain a transcription.</span></span> <span data-ttu-id="57814-106">若要使用它，請確定已在 *輸入系統設定檔* 中註冊聽寫系統。</span><span class="sxs-lookup"><span data-stu-id="57814-106">To use it make sure that a dictation system is registered in the *Input System Profile*.</span></span> <span data-ttu-id="57814-107">**Windows 聽寫輸入提供者** 是現成提供的聽寫系統，但是可以建立執行替代的聽寫系統 [`IMixedRealityDictationSystem`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityDictationSystem) 。</span><span class="sxs-lookup"><span data-stu-id="57814-107">**Windows Dictation Input Provider** is the dictation system provided out of the box but alternative dictation systems can be created implementing [`IMixedRealityDictationSystem`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityDictationSystem).</span></span>

## <a name="requirements"></a><span data-ttu-id="57814-108">規格需求</span><span class="sxs-lookup"><span data-stu-id="57814-108">Requirements</span></span>

<span data-ttu-id="57814-109">聽寫系統會使用 Unity 的 [DictationRecognizer](https://docs.unity3d.com/ScriptReference/Windows.Speech.DictationRecognizer.html) ，其本身會使用基礎 Windows 語音 api 來處理聽寫。</span><span class="sxs-lookup"><span data-stu-id="57814-109">The dictation system uses Unity's [DictationRecognizer](https://docs.unity3d.com/ScriptReference/Windows.Speech.DictationRecognizer.html) which itself uses the underlying Windows speech APIs for handling dictation.</span></span> <span data-ttu-id="57814-110">請注意，這表示這項功能只存在於 Windows 架構的平臺上。</span><span class="sxs-lookup"><span data-stu-id="57814-110">Note that this implies that this feature is only present on Windows-based platforms.</span></span>

<span data-ttu-id="57814-111">使用聽寫系統需要 [PlayerSettings 功能一節](https://docs.unity3d.com/Manual/class-PlayerSettingsWSA.html#Capabilities)中的「網際網路用戶端」和「麥克風」應用程式功能。</span><span class="sxs-lookup"><span data-stu-id="57814-111">Usage of the Dictation system requires both the "Internet Client" and "Microphone" application capabilities in the [PlayerSettings - Capabilities section](https://docs.unity3d.com/Manual/class-PlayerSettingsWSA.html#Capabilities).</span></span>
<span data-ttu-id="57814-112">如需 Unity 中語音輸入的詳細資訊，請參閱 [Windows Mixed Reality 檔](/windows/mixed-reality/voice-input-in-unity#dictation) 。</span><span class="sxs-lookup"><span data-stu-id="57814-112">See [Windows Mixed Reality Documentation](/windows/mixed-reality/voice-input-in-unity#dictation) for more details on voice input in Unity.</span></span>

## <a name="configuration"></a><span data-ttu-id="57814-113">組態</span><span class="sxs-lookup"><span data-stu-id="57814-113">Configuration</span></span>

<img src="../images/input/DictationDataProvider.png" width="80%" class="center" alt="Data provider">

<span data-ttu-id="57814-114">設定好聽寫服務之後，您可以使用 [`DictationHandler`](xref:Microsoft.MixedReality.Toolkit.Input.DictationHandler) 腳本來啟動和停止錄製會話，並透過 UnityEvents 取得轉譯結果。</span><span class="sxs-lookup"><span data-stu-id="57814-114">Once you have a dictation service set up, you can use the [`DictationHandler`](xref:Microsoft.MixedReality.Toolkit.Input.DictationHandler) script to start and stop recording sessions and obtain the transcription results via UnityEvents.</span></span>

<img src="../images/input/DictationHandler.png" width="80%" alt="Dictation Handler" class="center">

- <span data-ttu-id="57814-115">當使用者在到目前為止所捕獲音訊的早期轉譯時，會引發 **聽寫假設**。</span><span class="sxs-lookup"><span data-stu-id="57814-115">**Dictation Hypothesis** is raised as the user speaks with early, rough transcriptions of the audio captured so far.</span></span>
- <span data-ttu-id="57814-116">**聽寫結果** 會在每個句子的結尾引發 (也就是當使用者) 暫停時，會產生截至目前為止所捕獲音訊的最後轉譯。</span><span class="sxs-lookup"><span data-stu-id="57814-116">**Dictation Result** is raised at the end of each sentence (i.e. when the user pauses) with the final transcription of the audio captured so far.</span></span>
- <span data-ttu-id="57814-117">錄製會話的結尾會產生 **聽寫完成**，並包含音訊的完整、最後轉譯。</span><span class="sxs-lookup"><span data-stu-id="57814-117">**Dictation Complete** is raised at the end of the recording session with the full, final transcription of the audio.</span></span>
- <span data-ttu-id="57814-118">引發 **聽寫錯誤**，以通知聽寫服務中的錯誤。</span><span class="sxs-lookup"><span data-stu-id="57814-118">**Dictation Error** is raised to inform of errors in the dictation service.</span></span> <span data-ttu-id="57814-119">此案例中的轉譯包含錯誤的描述。</span><span class="sxs-lookup"><span data-stu-id="57814-119">The transcription in this case contains a description of the error.</span></span>

## <a name="example-scene"></a><span data-ttu-id="57814-120">範例場景</span><span class="sxs-lookup"><span data-stu-id="57814-120">Example scene</span></span>

<span data-ttu-id="57814-121">中的 **聽寫** 場景會 `MRTK/Examples/Demos/Input/Scenes/Dictation` 顯示 `DictationHandler` 使用中的腳本。</span><span class="sxs-lookup"><span data-stu-id="57814-121">**Dictation** scene in `MRTK/Examples/Demos/Input/Scenes/Dictation` shows the `DictationHandler` script in use.</span></span> <span data-ttu-id="57814-122">如果您需要更多控制，您可以擴充此腳本或建立自己的執行 [`IMixedRealityDictationHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityDictationHandler) ，以直接接收聽寫事件。</span><span class="sxs-lookup"><span data-stu-id="57814-122">If you need more control, you can either extend this script or create your own implementing [`IMixedRealityDictationHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityDictationHandler) to receive dictation events directly.</span></span>

<img src="../images/input/DictationDemo.png" width="80%" alt="Dictation Demo" class="center">