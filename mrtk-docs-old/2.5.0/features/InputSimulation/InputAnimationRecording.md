---
title: InputAnimationRecording
description: MRTK 中輸入動畫記錄系統的相關檔
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: 0054a891cf500ba7a3577cf6f781fff663a76e70
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104695325"
---
# <a name="input-animation-recording"></a><span data-ttu-id="b831f-104">輸入動畫錄製</span><span class="sxs-lookup"><span data-stu-id="b831f-104">Input animation recording</span></span>

<span data-ttu-id="b831f-105">MRTK 具有記錄系統，可將前端移動和手追蹤資料儲存在動畫檔案中。</span><span class="sxs-lookup"><span data-stu-id="b831f-105">MRTK features an recording system by which head movement and hand tracking data can be stored in animation files.</span></span> <span data-ttu-id="b831f-106">然後，您可以使用 [輸入模擬系統](InputSimulationService.md)來播放記錄的資料。</span><span class="sxs-lookup"><span data-stu-id="b831f-106">The recorded data can then be played back using the [input simulation system](InputSimulationService.md).</span></span>

<span data-ttu-id="b831f-107">記錄輸入在各種情況下都是有用的工具：</span><span class="sxs-lookup"><span data-stu-id="b831f-107">Recording input is a useful tool in a variety of situations:</span></span>

* <span data-ttu-id="b831f-108">建立互動、操作、解析器等的自動化測試。為這些測試建立控制器和手的移動可能相當耗時。</span><span class="sxs-lookup"><span data-stu-id="b831f-108">Creating automated tests for interaction, manipulations, solvers, etc. Creating the movement of controllers and hands for these tests can be time consuming.</span></span> <span data-ttu-id="b831f-109">直接錄製輸入可以加速處理常式，並提供真實世界的資料。</span><span class="sxs-lookup"><span data-stu-id="b831f-109">Recording input directly can speed up the process and provide real-world data.</span></span>
* <span data-ttu-id="b831f-110">透過動畫教學 UX 元素的使用。</span><span class="sxs-lookup"><span data-stu-id="b831f-110">Teaching the use of UX elements through animations.</span></span>
  <span data-ttu-id="b831f-111">顯示使用者如何與按鈕和其他物件互動，可使學習曲線更平滑。</span><span class="sxs-lookup"><span data-stu-id="b831f-111">Showing users how to interact with buttons and other objects can smooth the learning curve.</span></span>
* <span data-ttu-id="b831f-112">在正常使用期間偵測可能發生的未預期行為。</span><span class="sxs-lookup"><span data-stu-id="b831f-112">Debugging unexpected behavior that may be encountered during regular use.</span></span>
  <span data-ttu-id="b831f-113">錄製系統支援「滾動緩衝區」概念，可讓您在背景中錄製最近的輸入。</span><span class="sxs-lookup"><span data-stu-id="b831f-113">The recording system supports a "rolling buffer" concept that allows recording recent input in the background.</span></span>
  <span data-ttu-id="b831f-114">請參閱 [輸入記錄服務](#input-recording-service)。</span><span class="sxs-lookup"><span data-stu-id="b831f-114">See [Input Recording Service](#input-recording-service).</span></span>

## <a name="recording-and-playback-services"></a><span data-ttu-id="b831f-115">錄製和播放服務</span><span class="sxs-lookup"><span data-stu-id="b831f-115">Recording and playback services</span></span>

<span data-ttu-id="b831f-116">系統會提供兩個輸入系統服務，分別記錄及播放輸入。</span><span class="sxs-lookup"><span data-stu-id="b831f-116">Two input system services are provided to record and play back input respectively.</span></span>

### <a name="input-recording-service"></a><span data-ttu-id="b831f-117">輸入記錄服務</span><span class="sxs-lookup"><span data-stu-id="b831f-117">Input recording service</span></span>

<span data-ttu-id="b831f-118">[`InputRecordingService`](xref:Microsoft.MixedReality.Toolkit.Input.InputRecordingService) 從主要相機轉換和主動式控制器取得資料，並將其儲存在內部緩衝區中。</span><span class="sxs-lookup"><span data-stu-id="b831f-118">[`InputRecordingService`](xref:Microsoft.MixedReality.Toolkit.Input.InputRecordingService) takes data from the main camera transform and active hand controllers and stores it in an internal buffer.</span></span> <span data-ttu-id="b831f-119">要求時，此資料會序列化為二進位檔案，以供儲存和稍後重新執行。</span><span class="sxs-lookup"><span data-stu-id="b831f-119">When requested this data is then serialized into binary files for storage and later replay.</span></span>

<a target="_blank" href="../Images/InputSimulation/MRTK_InputAnimation_RecordingDiagram.png" alt="Recording Diagram">
  <img src="../Images/InputSimulation/MRTK_InputAnimation_RecordingDiagram.png" title="錄製輸入動畫" width="80%" class="center" />
</a>

<span data-ttu-id="b831f-121">若要開始錄製輸入，請呼叫 [`StartRecording`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputRecordingService.StartRecording) 函數。</span><span class="sxs-lookup"><span data-stu-id="b831f-121">To start recording input call the [`StartRecording`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputRecordingService.StartRecording) function.</span></span> <span data-ttu-id="b831f-122">[`StopRecording`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputRecordingService.StopRecording) 會暫停錄製 (但無法捨棄目前為止所記錄的資料， [`DiscardRecordedInput`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputRecordingService.DiscardRecordedInput) 如有必要，請使用來執行此動作) 。</span><span class="sxs-lookup"><span data-stu-id="b831f-122">[`StopRecording`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputRecordingService.StopRecording) will pause recording (but not discard the data recorded so far, use [`DiscardRecordedInput`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputRecordingService.DiscardRecordedInput) to do this if needed).</span></span>

<span data-ttu-id="b831f-123">根據預設，記錄緩衝區的大小限制為30秒。</span><span class="sxs-lookup"><span data-stu-id="b831f-123">By default the size of the recording buffer is limited to 30 seconds.</span></span> <span data-ttu-id="b831f-124">這可讓錄製服務在背景中保持錄製，而不會累積太多資料，然後在需要時儲存最後30秒。</span><span class="sxs-lookup"><span data-stu-id="b831f-124">This allows the recording service to keep recording in the background without accumulating too much data, and then save the last 30 seconds when required.</span></span> <span data-ttu-id="b831f-125">您可以使用屬性來變更時間間隔 [`RecordingBufferTimeLimit`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputRecordingService.RecordingBufferTimeLimit) ，也可以使用選項來限制錄製 [`UseBufferTimeLimit`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputRecordingService.UseBufferTimeLimit) 。</span><span class="sxs-lookup"><span data-stu-id="b831f-125">The time interval can be changed using the [`RecordingBufferTimeLimit`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputRecordingService.RecordingBufferTimeLimit) property, or recording can be unlimited using the [`UseBufferTimeLimit`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputRecordingService.UseBufferTimeLimit) option.</span></span>

<span data-ttu-id="b831f-126">您可以使用 [SaveInputAnimation](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputRecordingService.SaveInputAnimation*) 函式，將記錄緩衝區中的資料儲存在二進位檔案中。</span><span class="sxs-lookup"><span data-stu-id="b831f-126">The data in the recording buffer can be saved in a binary file using the [SaveInputAnimation](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputRecordingService.SaveInputAnimation*) function.</span></span>

<span data-ttu-id="b831f-127">如需二進位檔案格式的詳細資訊，請參閱 [輸入動畫檔案格式規格](InputAnimationFileFormat.md)。</span><span class="sxs-lookup"><span data-stu-id="b831f-127">For details on the binary file format see [Input Animation File Format Specification](InputAnimationFileFormat.md).</span></span>

### <a name="input-playback-service"></a><span data-ttu-id="b831f-128">輸入播放服務</span><span class="sxs-lookup"><span data-stu-id="b831f-128">Input playback service</span></span>

<span data-ttu-id="b831f-129">[`InputPlaybackService`](xref:Microsoft.MixedReality.Toolkit.Input.InputPlaybackService) 讀取具有輸入動畫資料的二進位檔案，然後透過 [InputSimulationService](xref:Microsoft.MixedReality.Toolkit.Input.InputSimulationService) 套用此資料，以重新建立錄製的移動。</span><span class="sxs-lookup"><span data-stu-id="b831f-129">[`InputPlaybackService`](xref:Microsoft.MixedReality.Toolkit.Input.InputPlaybackService) reads a binary file with input animation data and then applies this data through the [InputSimulationService](xref:Microsoft.MixedReality.Toolkit.Input.InputSimulationService) to recreate the recorded movements.</span></span>

<a target="_blank" href="../../Documentation/Images/InputSimulation/MRTK_InputAnimation_PlaybackDiagram.png">
  <img src="../Images/InputSimulation/MRTK_InputAnimation_PlaybackDiagram.png" title="播放輸入動畫" width="80%" class="center" />
</a>

<span data-ttu-id="b831f-131">若要開始播放輸入動畫，應該使用 [LoadInputAnimation](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputPlaybackService.LoadInputAnimation*) 函式從檔案載入。</span><span class="sxs-lookup"><span data-stu-id="b831f-131">To start playing back input animation it should be loaded from a file using the [LoadInputAnimation](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputPlaybackService.LoadInputAnimation*) function.</span></span>

<span data-ttu-id="b831f-132">呼叫 [播放](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputPlaybackService.Play)、 [暫停](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputPlaybackService.Play)或 [停止](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputPlaybackService.Stop) 以控制動畫播放。</span><span class="sxs-lookup"><span data-stu-id="b831f-132">Call [Play](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputPlaybackService.Play), [Pause](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputPlaybackService.Play), or [Stop](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputPlaybackService.Stop) to control the animation playback.</span></span>

<span data-ttu-id="b831f-133">目前的動畫時間也可以直接使用 [LocalTime](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputPlaybackService.LocalTime) 屬性來控制。</span><span class="sxs-lookup"><span data-stu-id="b831f-133">The current animation time can also be controlled directly with the [LocalTime](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputPlaybackService.LocalTime) property.</span></span>

> [!WARNING]
> <span data-ttu-id="b831f-134">藉由清除時間軸來迴圈或重設輸入動畫或直接設定， [`LocalTime`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputPlaybackService.LocalTime) 可能會在操作場景時產生非預期的結果！</span><span class="sxs-lookup"><span data-stu-id="b831f-134">Looping or resetting input animation or setting [`LocalTime`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputPlaybackService.LocalTime) directly by scrubbing the timeline may yield unexpected results when manipulating the scene!</span></span> <span data-ttu-id="b831f-135">只會記錄輸入移動，任何其他變更（例如移動物件或翻轉參數）都不會重設。</span><span class="sxs-lookup"><span data-stu-id="b831f-135">Only the input movements are recorded, any additional changes such as moving objects or flipping switches will not be reset.</span></span> <span data-ttu-id="b831f-136">如果已進行無法復原的變更，請務必重載場景。</span><span class="sxs-lookup"><span data-stu-id="b831f-136">Make sure to reload the scene if irreversible changes have been made.</span></span>

### <a name="editor-tools-for-recording-and-playing-input-animation"></a><span data-ttu-id="b831f-137">錄製和播放輸入動畫的編輯器工具</span><span class="sxs-lookup"><span data-stu-id="b831f-137">Editor tools for recording and playing input animation</span></span>

<span data-ttu-id="b831f-138">Unity 編輯器中有一些工具可用來錄製和檢查輸入動畫。</span><span class="sxs-lookup"><span data-stu-id="b831f-138">A number of tools exist in the Unity editor for recording and examining input animation.</span></span> <span data-ttu-id="b831f-139">您可以在 [ [輸入模擬工具] 視窗](InputSimulationService.md#input-simulation-tools-window)中存取這些工具，這些工具可以從混合現實工具組開啟， _> 公用程式 > 輸入模擬_ 功能表。</span><span class="sxs-lookup"><span data-stu-id="b831f-139">These tools can be accessed in the [input simulation tools window](InputSimulationService.md#input-simulation-tools-window), which can be opened from the _Mixed Reality Toolkit > Utilities > Input Simulation_ menu.</span></span>

> [!NOTE]
> <span data-ttu-id="b831f-140">輸入錄製和播放只能在播放模式下運作。</span><span class="sxs-lookup"><span data-stu-id="b831f-140">Input recording and playback only works during play mode.</span></span>

<span data-ttu-id="b831f-141">輸入錄製視窗有兩種模式：</span><span class="sxs-lookup"><span data-stu-id="b831f-141">The input recording window has two modes:</span></span>

* <span data-ttu-id="b831f-142">_錄製_ 在播放模式期間錄製輸入，並將其儲存至動畫檔案。</span><span class="sxs-lookup"><span data-stu-id="b831f-142">_Recording_ for recording input during play mode and saving it to animation files.</span></span>

  <span data-ttu-id="b831f-143">在錄製按鈕上切換時， [`InputRecordingService`](xref:Microsoft.MixedReality.Toolkit.Input.InputRecordingService) 已啟用記錄輸入。</span><span class="sxs-lookup"><span data-stu-id="b831f-143">When toggling on the recording button the [`InputRecordingService`](xref:Microsoft.MixedReality.Toolkit.Input.InputRecordingService) is enabled to record input.</span></span>
  <span data-ttu-id="b831f-144">關閉錄製按鈕時，會顯示檔案儲存選取範圍，且錄製的輸入動畫會儲存至選取的目的地。</span><span class="sxs-lookup"><span data-stu-id="b831f-144">When toggling off the recording button a file save selection is shown and the recorded input animation is saved to the selected destination.</span></span>

  <span data-ttu-id="b831f-145">您也可以在此模式中變更緩衝區時間限制。</span><span class="sxs-lookup"><span data-stu-id="b831f-145">The buffer time limit can also be changed in this mode.</span></span>

* <span data-ttu-id="b831f-146">_播放_ 以載入動畫檔案，然後透過輸入模擬系統重建輸入。</span><span class="sxs-lookup"><span data-stu-id="b831f-146">_Playback_ for loading animation files and then recreating input through the input simulation system.</span></span>

  <span data-ttu-id="b831f-147">必須先在此模式中載入動畫。</span><span class="sxs-lookup"><span data-stu-id="b831f-147">An animation must be loaded in this mode first.</span></span> <span data-ttu-id="b831f-148">在錄製模式中錄製輸入之後，會自動載入產生的動畫。</span><span class="sxs-lookup"><span data-stu-id="b831f-148">After recording input in recording mode the resulting animation is automatically loaded.</span></span> <span data-ttu-id="b831f-149">或者，按一下 [載入] 按鈕以選取現有的動畫檔。</span><span class="sxs-lookup"><span data-stu-id="b831f-149">Alternatively click the "Load" button to select an existing animation file.</span></span>

  <span data-ttu-id="b831f-150">從左至右的時間控制按鈕如下：</span><span class="sxs-lookup"><span data-stu-id="b831f-150">The time control buttons from left to right are:</span></span>

  * <span data-ttu-id="b831f-151">將播放時間 _重設_ 為動畫的開頭。</span><span class="sxs-lookup"><span data-stu-id="b831f-151">_Reset_ the playback time to the start of the animation.</span></span>
  * <span data-ttu-id="b831f-152">在一段時間內持續 _播放_ 動畫。</span><span class="sxs-lookup"><span data-stu-id="b831f-152">_Play_ animation continuously over time.</span></span>
  * <span data-ttu-id="b831f-153">_向前復原一次步驟。_</span><span class="sxs-lookup"><span data-stu-id="b831f-153">_Step_ forward one time step.</span></span>

  <span data-ttu-id="b831f-154">滑杆也可以用來清除動畫時間軸。</span><span class="sxs-lookup"><span data-stu-id="b831f-154">The slider can also be used to scrub through the animation timeline.</span></span>

> [!WARNING]
> <span data-ttu-id="b831f-155">在操作場景時，迴圈或重設輸入動畫或清除時間軸可能會產生非預期的結果！</span><span class="sxs-lookup"><span data-stu-id="b831f-155">Looping or resetting input animation or scrubbing the timeline may yield unexpected results when manipulating the scene!</span></span> <span data-ttu-id="b831f-156">只會記錄輸入移動，任何其他變更（例如移動物件或翻轉參數）都不會重設。</span><span class="sxs-lookup"><span data-stu-id="b831f-156">Only the input movements are recorded, any additional changes such as moving objects or flipping switches will not be reset.</span></span> <span data-ttu-id="b831f-157">如果已進行無法復原的變更，請務必重載場景。</span><span class="sxs-lookup"><span data-stu-id="b831f-157">Make sure to reload the scene if irreversible changes have been made.</span></span>
