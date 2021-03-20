---
title: InputAnimationRecording
description: MRTK 中輸入動畫記錄系統的相關檔
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: 21d765dcf7f7866edd33fc994de5a7e32f8c3e10
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104702404"
---
# <a name="input-animation-recording"></a>輸入動畫錄製

MRTK 具有記錄系統，可將前端移動和手追蹤資料儲存在動畫檔案中。 然後，您可以使用 [輸入模擬系統](input-simulation-service.md)來播放記錄的資料。

記錄輸入在各種情況下都是有用的工具：

* 建立互動、操作、解析器等的自動化測試。為這些測試建立控制器和手的移動可能相當耗時。 直接錄製輸入可以加速處理常式，並提供真實世界的資料。
* 透過動畫教學 UX 元素的使用。
  顯示使用者如何與按鈕和其他物件互動，可使學習曲線更平滑。
* 在正常使用期間偵測可能發生的未預期行為。
  錄製系統支援「滾動緩衝區」概念，可讓您在背景中錄製最近的輸入。
  請參閱 [輸入記錄服務](#input-recording-service)。

## <a name="recording-and-playback-services"></a>錄製和播放服務

系統會提供兩個輸入系統服務，分別記錄及播放輸入。

### <a name="input-recording-service"></a>輸入記錄服務

[`InputRecordingService`](xref:Microsoft.MixedReality.Toolkit.Input.InputRecordingService) 從主要相機轉換和主動式控制器取得資料，並將其儲存在內部緩衝區中。 要求時，此資料會序列化為二進位檔案，以供儲存和稍後重新執行。

<a target="_blank" href="../images/input-simulation/MRTK_InputAnimation_RecordingDiagram.png">
  <img src="../images/input-simulation/MRTK_InputAnimation_RecordingDiagram.png" title="錄製輸入動畫" width="80%" alt="Recording diagram" class="center" />
</a>

若要開始錄製輸入，請呼叫 [`StartRecording`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputRecordingService.StartRecording) 函數。 [`StopRecording`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputRecordingService.StopRecording) 會暫停錄製 (但無法捨棄目前為止所記錄的資料， [`DiscardRecordedInput`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputRecordingService.DiscardRecordedInput) 如有必要，請使用來執行此動作) 。

根據預設，記錄緩衝區的大小限制為30秒。 這可讓錄製服務在背景中保持錄製，而不會累積太多資料，然後在需要時儲存最後30秒。 您可以使用屬性來變更時間間隔 [`RecordingBufferTimeLimit`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputRecordingService.RecordingBufferTimeLimit) ，也可以使用選項來限制錄製 [`UseBufferTimeLimit`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputRecordingService.UseBufferTimeLimit) 。

您可以使用 [SaveInputAnimation](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputRecordingService.SaveInputAnimation*) 函式，將記錄緩衝區中的資料儲存在二進位檔案中。

如需二進位檔案格式的詳細資訊，請參閱 [輸入動畫檔案格式規格](input-animation-file-format.md)。

### <a name="input-playback-service"></a>輸入播放服務

[`InputPlaybackService`](xref:Microsoft.MixedReality.Toolkit.Input.InputPlaybackService) 讀取具有輸入動畫資料的二進位檔案，然後透過 [InputSimulationService](xref:Microsoft.MixedReality.Toolkit.Input.InputSimulationService) 套用此資料，以重新建立錄製的移動。

<a target="_blank" href="../images/input-simulation/MRTK_InputAnimation_PlaybackDiagram.png">
  <img src="../images/input-simulation/MRTK_InputAnimation_PlaybackDiagram.png" title="播放輸入動畫" width="80%" alt="Play Back diagram" class="center" />
</a>

若要開始播放輸入動畫，應該使用 [LoadInputAnimation](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputPlaybackService.LoadInputAnimation*) 函式從檔案載入。

呼叫 [播放](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputPlaybackService.Play)、 [暫停](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputPlaybackService.Play)或 [停止](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputPlaybackService.Stop) 以控制動畫播放。

目前的動畫時間也可以直接使用 [LocalTime](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputPlaybackService.LocalTime) 屬性來控制。

> [!WARNING]
> 藉由清除時間軸來迴圈或重設輸入動畫或直接設定， [`LocalTime`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputPlaybackService.LocalTime) 可能會在操作場景時產生非預期的結果！ 只會記錄輸入移動，任何其他變更（例如移動物件或翻轉參數）都不會重設。 如果已進行無法復原的變更，請務必重載場景。

### <a name="editor-tools-for-recording-and-playing-input-animation"></a>錄製和播放輸入動畫的編輯器工具

Unity 編輯器中有一些工具可用來錄製和檢查輸入動畫。 您可以在 [ [輸入模擬工具] 視窗](input-simulation-service.md#input-simulation-tools-window)中存取這些工具，這些工具可以從混合現實工具組開啟， _> 公用程式 > 輸入模擬_ 功能表。

> [!NOTE]
> 輸入錄製和播放只能在播放模式下運作。

輸入錄製視窗有兩種模式：

* _錄製_ 在播放模式期間錄製輸入，並將其儲存至動畫檔案。

  在錄製按鈕上切換時， [`InputRecordingService`](xref:Microsoft.MixedReality.Toolkit.Input.InputRecordingService) 已啟用記錄輸入。
  關閉錄製按鈕時，會顯示檔案儲存選取範圍，且錄製的輸入動畫會儲存至選取的目的地。

  您也可以在此模式中變更緩衝區時間限制。

* _播放_ 以載入動畫檔案，然後透過輸入模擬系統重建輸入。

  必須先在此模式中載入動畫。 在錄製模式中錄製輸入之後，會自動載入產生的動畫。 或者，按一下 [載入] 按鈕以選取現有的動畫檔。

  從左至右的時間控制按鈕如下：

  * 將播放時間 _重設_ 為動畫的開頭。
  * 在一段時間內持續 _播放_ 動畫。
  * _向前復原一次步驟。_

  滑杆也可以用來清除動畫時間軸。

> [!WARNING]
> 在操作場景時，迴圈或重設輸入動畫或清除時間軸可能會產生非預期的結果！ 只會記錄輸入移動，任何其他變更（例如移動物件或翻轉參數）都不會重設。 如果已進行無法復原的變更，請務必重載場景。
