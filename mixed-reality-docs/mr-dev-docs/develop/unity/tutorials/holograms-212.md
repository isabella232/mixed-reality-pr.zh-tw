---
title: MR 輸入 212-語音
description: 遵循此程式碼逐步解說，使用 Unity、Visual Studio 和 HoloLens 來瞭解語音概念的詳細資料。
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit、mixedrealitytoolkit、mixedrealitytoolkit-unity、學院、教學課程、語音
ms.openlocfilehash: ed37ef6e0c26c3d2a0cd2d51e18d01a258b2fc78
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2020
ms.locfileid: "91680629"
---
# <a name="mr-input-212-voice"></a>MR Input 212：語音

>[!NOTE]
>混合實境學院教學課程的設計是以 HoloLens (第 1 代) 和混合實境沉浸式頭戴裝置為準。  因此，對於仍在尋找這些裝置開發指引的開發人員而言，我們覺得這些教學課程很重要。  這些教學課程 **_不會_** 使用用於 HoloLens 2 的最新工具組或互動進行更新。  系統會保留這些資訊，以繼續在支援的裝置上運作。 已針對 HoloLens 2 公佈[一系列新的教學課程](../../../mr-learning-base-01.md)。

[語音輸入](../../../design/voice-input.md) 可讓我們以另一種方式與我們的全像影像互動。 語音命令的運作方式非常自然且簡單。 設計您的語音命令，使其為：

* Natural
* 容易記住
* 適當的內容
* 與相同內容中的其他選項有充分的差異

>[!VIDEO https://www.youtube.com/embed/BYpYsVFYjdw]

在 [MR 基本的 101](../../../develop/unity/tutorials/holograms-101.md)中，我們使用了 KeywordRecognizer 來建立兩個簡單的語音命令。 在 MR 輸入212中，我們將深入探討並學習如何：

* 設計針對 HoloLens 語音引擎優化的語音命令。
* 讓使用者知道有哪些語音命令可供使用。
* 確認我們已聽過使用者的語音命令。
* 使用聽寫辨識器瞭解使用者的意思。
* 使用文法辨識器，根據 SRGS 或語音辨識文法規格（file）來接聽命令。

在此課程中，我們將重新流覽 [模型瀏覽器]，這是我們在 [Mr 輸入 210](holograms-210.md) 和 [MR 輸入 211](holograms-211.md)中建立的。

>[!IMPORTANT]
>下列各章節中內嵌的影片是使用較舊版本的 Unity 和混合現實工具組所記錄。 雖然逐步指示是正確且最新的，但您可能會在相對應的影片中看到已過期的腳本和視覺效果。 影片仍隨附于 posterity，因為所涵蓋的概念仍然適用。


## <a name="device-support"></a>裝置支援

<table>
<tr>
<th>課程</th><th style="width:150px"> <a href="../../../hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">沉浸式頭戴裝置</a></th>
</tr><tr>
<td>MR Input 212：語音</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="before-you-start"></a>開始之前

### <a name="prerequisites"></a>Prerequisites

* [已安裝正確工具](../../../develop/install-the-tools.md)的 Windows 10 電腦。
* 一些基本的 c # 程式設計功能。
* 您應已完成 [MR 基本的 101](../../../develop/unity/tutorials/holograms-101.md)。
* 您應已完成 [MR 輸入 210](holograms-210.md)。
* 您應已完成 [MR 輸入 211](holograms-211.md)。
* [針對開發設定](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)的 HoloLens 裝置。

### <a name="project-files"></a>專案檔

* 下載專案 [所需的](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-212-Voice.zip) 檔案。 需要 Unity 2017.2 或更新版本。
* 取消將檔案封存到您的桌面或其他易於觸及的位置。

>[!NOTE]
>如果您想要在下載之前查看原始程式碼， [可在 GitHub 上](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-212-Voice)取得。

### <a name="errata-and-notes"></a>勘誤表和記事

* 您必須在 [工具]-[>選項] 下的 Visual Studio 中停用 [啟用 Just My Code] ( *未* 核取) ，才能在程式碼中叫用中斷點。

## <a name="unity-setup"></a>Unity 設定

### <a name="instructions"></a>Instructions

1. 啟動 Unity。
2. 選取 [開啟]。
3. 流覽至您先前取消封存的 HolographicAcademy-全像 **-212-Voice** 資料夾。
4. 尋找並選取 [ **啟動** / **模型瀏覽器** ] 資料夾。
5. 按一下 [ **選取資料夾** ] 按鈕。
6. 在 [ **專案** ] 面板中，展開 [ **場景** ] 資料夾。
7. 按兩下 [ **ModelExplorer** 場景]，以在 Unity 中載入。

### <a name="building"></a>建置

1. 在 Unity 中，選取 [ **File > Build Settings** ]。
2. 如果 **場景/ModelExplorer** 未列在 **組建的場景** 中，請按一下 [ **新增開啟場景** ] 以加入場景。
3. 如果您是特別針對 HoloLens 進行開發，請將 **目標裝置** 設定為 **hololens** 。 否則，請將它保留在 **任何裝置** 上。
4. 請確定 **組建類型** 設定為 [ **D3D** ]，並將 [ **Sdk** ] 設定為 [ **最新安裝** 的 (，其應為 SDK 16299 或更新版本的) 。
5. 按一下 [建置]  。
6. 建立名為 "App" 的 **新資料夾** 。
7. 按一下 **應用程式** 資料夾。
8. 按下 [ **選取資料夾** ]，Unity 就會開始建立 Visual Studio 的專案。

當 Unity 完成時，將會出現檔案總管視窗。

1. 開啟 **應用程式** 資料夾。
2. 開啟 **ModelExplorer Visual Studio 方案** 。

如果要部署到 HoloLens：

1. 使用 Visual Studio 中的頂端工具列，將目標從 Debug 變更為 **Release** ，以及從 ARM 變更為 **x86** 。
2. 按一下 [本機電腦] 按鈕旁的下拉箭號，然後選取 [ **遠端電腦** ]。
3. 輸入 **您的 HoloLens 裝置 IP 位址** ，並將驗證模式設定為 **通用 (未加密的通訊協定)** 。 按一下 [選取]。  如果您不知道您的裝置 IP 位址，請查看 [ **設定] > Network & Internet > Advanced 選項** 。
4. 在頂端功能表列中，按一下 [ **Debug-> 啟動但不進行調試** ]，或按 **Ctrl + F5** 。 如果這是您第一次部署至您的裝置，您必須將 [它與 Visual Studio 配對](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#pairing-your-device)。
5. 部署應用程式之後，請使用 **選取手勢** 來關閉 **Fitbox** 。

如果部署到沉浸式耳機：

1. 使用 Visual Studio 中的頂端工具列，將目標從 Debug 變更為 **Release** ，以及從 ARM 變更為 **x64** 。
2. 請確定部署目標設定為 [ **本機電腦** ]。
3. 在頂端功能表列中，按一下 [ **Debug-> 啟動但不進行調試** ]，或按 **Ctrl + F5** 。
4. 部署應用程式之後，請在動作控制器上提取觸發程式來關閉 **Fitbox** 。

>[!NOTE]
>您可能會注意到 Visual Studio 錯誤面板中有一些紅色錯誤。 您可以放心地忽略它們。 切換至 [輸出] 面板以查看實際的組建進度。 輸出面板中的錯誤會要求您進行修正 (最常見的原因是腳本) 中發生錯誤。

## <a name="chapter-1---awareness"></a>第1章-認知

>[!VIDEO https://www.youtube.com/embed/fDwijJWuEc0]

### <a name="objectives"></a>目標

* 瞭解語音命令設計的 **Dos 和不注意事項** 。
* 使用 **KeywordRecognizer** 來新增以注視為基礎的語音命令。
* 使用游標 **回饋** 讓使用者知道語音命令。

### <a name="voice-command-design"></a>語音命令設計

在本章中，您將瞭解如何設計語音命令。 建立語音命令時：

#### <a name="do"></a>DO

* 建立簡潔的命令。 您不想要使用「 *播放目前選取的影片* 」，因為該命令並非簡潔，而且使用者很容易就會忘記。 相反地，您應該使用：「 *播放影片* 」，因為它很簡潔，而且有多個音節。
* 使用簡單的詞彙。 請一律嘗試使用簡單的單字和片語，方便使用者探索和記住。 例如，如果您的應用程式具有可顯示或隱藏的附注物件，您就不會使用 " *Show 牌子"* 命令，因為 "牌子" 是很少使用的詞彙。 相反地，您會 *使用下列命令來顯示應用* 程式中的附注。
* 保持一致。 語音命令在您的應用程式中應該保持一致。 假設您的應用程式中有兩個場景，而且這兩個場景都包含用來關閉應用程式的按鈕。 如果第一個場景使用 " *Exit"* 命令來觸發按鈕，但第二個場景使用「 *關閉應用程式* 」命令，則使用者會感到混淆。 如果相同的功能跨多個場景保存，則應該使用相同的語音命令來觸發它。

#### <a name="dont"></a>不要

* 使用單一的音節命令。 例如，如果您要建立語音命令來播放影片，您應該避免使用簡單的命令「 *播放* 」，因為這只是一個音節，而且可能很容易被系統錯過。 相反地，您應該使用：「 *播放影片* 」，因為它很簡潔，而且有多個音節。
* 使用系統命令。 系統會保留 *"Select"* 命令，以觸發目前焦點物件的點擊事件。 請勿重複使用關鍵字或片語中的 *"Select"* 命令，因為它可能無法如您預期般運作。 例如，如果在您的應用程式中選取 cube 的聲音命令為「 *選取 cube* 」，但使用者在從未提到命令時正在查看球體，則會改為選取球體。 同樣地，已啟用語音的應用程式行命令。 請勿在 CoreWindow View 中使用下列語音命令：
    1. 向後
    2. 捲軸工具
    3. Zoom 工具
    4. 拖曳工具
    5. Adjust
    6. 移除
* 使用類似的聲音。 請嘗試避免使用 rhyme 的語音命令。 如果您的購物應用程式支援 [ *顯示存放區]* 和 [ *顯示更多]* 作為語音命令，則您會想要在另一個使用中的命令停用其中一個命令。 例如，您可以使用 [ *顯示存放區]* 按鈕來開啟存放區，然後在商店顯示時停用該命令，如此就可以使用 [ *顯示更多]* 命令來進行流覽。

### <a name="instructions"></a>Instructions

* 在 **Unity 的階層** 面板中，使用搜尋工具來尋找 **holoComm_screen_mesh** 物件。
* 按兩下 **holoComm_screen_mesh** 物件以在 **場景** 中加以查看。 這是太空人的監看，它會回應我們的語音命令。
* 在 [偵測 **器** ] 面板中，找出 **語音輸入來源 (腳本)** 元件。
* 展開 [ **關鍵字** ] 區段以查看支援的語音命令： **開啟 Communicator** 。
* 按一下右邊的齒輪，然後選取 [ **編輯腳本** ]。
* 探索 **SpeechInputSource.cs** ，瞭解它如何使用 **KeywordRecognizer** 來新增語音命令。

### <a name="build-and-deploy"></a>建置和部署

* 在 Unity 中，使用檔案 **> 組建設定** 來重建應用程式。
* 開啟 **應用程式** 資料夾。
* 開啟 **ModelExplorer Visual Studio 方案** 。

 (如果您已在安裝期間于 Visual Studio 中建立或部署此專案，則您可以開啟 VS 的實例，然後在出現) 提示時按一下 [全部重載]。

* 在 Visual Studio 中，按一下 [ **Debug-> 啟動但不進行調試** ]，或按 **Ctrl + F5** 。
* 將應用程式部署到 HoloLens 之後，請使用 [點 [一下手勢] 關閉 [符合](../../../design/gaze-and-commit.md#composite-gestures) ] 方塊。
* 觀賞太空人的觀賞。
* 當 watch 具有焦點時，請確認游標變更為麥克風。 這會提供應用程式接聽語音命令的意見反應。
* 確認 watch 上出現工具提示。 這可協助使用者探索 *"Open Communicator"* 命令。
* 撥雲見日監看時，請說「 *開啟 communicator* 」來開啟 communicator 面板。

## <a name="chapter-2---acknowledgement"></a>第2章-確認

>[!VIDEO https://www.youtube.com/embed/87ViteoPpyU]

### <a name="objectives"></a>目標

* 使用麥克風輸入記錄訊息。
* 將意見反應提供給使用者，指出應用程式正在接聽其語音。

>[!NOTE]
>必須針對要從麥克風錄製的應用程式宣告 **麥克風** 功能。 您已在 MR 輸入212中為您完成這項操作，但請記住您自己的專案。
>
>1. 在 Unity 編輯器中，流覽至 [> Player 編輯 > 專案設定]，移至播放機設定
>2. 按一下 [通用 Windows 平臺] 索引標籤
>3. 在 [發佈設定 > 功能] 區段中，檢查 **麥克風** 功能

### <a name="instructions"></a>Instructions

* 在 Unity 的 **階層面板中** ，確認已選取 **holoComm_screen_mesh** 物件。
* 在 [偵測 **器** ] 面板中，尋找 **太空人 Watch (腳本)** 元件。
* 按一下設定為 [ **Communicator 預製專案** ] 屬性值的小、藍色 cube。
* 在 [ **專案** ] 面板中， **Communicator** 預製專案現在應該會有焦點。
* 按一下 [ **專案** ] 面板中的 **Communicator** 預製專案，以在偵測 **器** 中查看其元件。
* 查看 **麥克風管理員 (腳本)** 元件，這可讓我們記錄使用者的聲音。
* 請注意， **Communicator** 物件具有 **語音輸入處理常式 (腳本)** 元件，可回應 **傳送訊息** 命令。
* 查看 **Communicator (腳本)** 元件，然後按兩下腳本，在 Visual Studio 中開啟它。

Communicator.cs 負責在 communicator 裝置上設定適當的按鈕狀態。 這可讓我們的使用者記錄訊息、播放訊息，然後將訊息傳送至太空人。 它也會啟動和停止動畫 wave 表單，以向使用者確認他們的聲音聽到。

* 在 **Communicator.cs** 中，從 **Start** 方法 (81 和 82) 刪除下列幾行。 這會啟用 communicator 上的 [記錄] 按鈕。

```cs
// TODO: 2.a Delete the following two lines:
RecordButton.SetActive(false);
MessageUIRenderer.gameObject.SetActive(false);
```

### <a name="build-and-deploy"></a>建置和部署

* 在 Visual Studio 中，重建您的應用程式並部署至裝置。
* 觀賞太空人的監看，然後說「 *開啟 communicator* 」來顯示 Communicator。
* 按下 [ **錄製** ] 按鈕 (麥克風) ，開始記錄太空人的口頭訊息。
* 開始說話，並確認 wave 動畫是在 communicator 上播放的，它會將意見反應提供給使用者，指出他們的聲音聽起來。
* 按下 [ **停止** ] 按鈕 (左方塊) ，並確認 wave 動畫停止執行。
* 按下 [ **播放** ] 按鈕 (右三角形) 播放錄製的訊息，並在裝置上聆聽。
* 按下 [ **停止** ] 按鈕 (右方塊) 停止播放錄製的訊息。
* 說「 *傳送訊息* 」以關閉 communicator，並接收來自太空人的「訊息已接收」回應。

## <a name="chapter-3---understanding-and-the-dictation-recognizer"></a>第3章-瞭解與聽寫辨識器

>[!VIDEO https://www.youtube.com/embed/TIMddr-HqEU]

### <a name="objectives"></a>目標

* 使用聽寫辨識器將使用者的語音轉換成文字。
* 在 communicator 中顯示聽寫辨識器的假設和最終結果。

在本章中，我們將使用聽寫辨識器來建立太空人的訊息。 使用聽寫辨識器時，請記住：

* 您必須連線到 WiFi，聽寫辨識器才能運作。
* 在設定的一段時間後發生超時。 有兩個需要注意的超時：
  * 如果辨識器啟動，但在前五秒內未收到任何音訊，則會超時。
  * 如果辨識器已指定結果，但接著會聽到20秒的無回應，則會超時。
* 一次只能執行一種辨識器 (關鍵字或聽寫) 。

>[!NOTE]
>必須針對要從麥克風錄製的應用程式宣告 **麥克風** 功能。 您已在 MR 輸入212中為您完成這項操作，但請記住您自己的專案。
>
>1. 在 Unity 編輯器中，流覽至 [> Player 編輯 > 專案設定]，移至播放機設定
>2. 按一下 [通用 Windows 平臺] 索引標籤
>3. 在 [發佈設定 > 功能] 區段中，檢查 **麥克風** 功能

### <a name="instructions"></a>Instructions

我們將編輯 **MicrophoneManager.cs** 以使用聽寫辨識器。 這就是我們要新增的內容：

1. 當您按下 [ **錄製] 按鈕** 時，我們會 **啟動 DictationRecognizer** 。
2. 顯示 DictationRecognizer 瞭解的 **假設** 。
3. 鎖定 DictationRecognizer 瞭解的 **結果** 。
4. 檢查 DictationRecognizer 是否有超時。
5. 當按下 [ **停止] 按鈕** 或 mic 會話超時時，請 **停止 DictationRecognizer** 。
6. 重新開機 **KeywordRecognizer** ，它會接聽 **傳送訊息** 命令。

讓我們開始這次的教學。 完成 3. a **MicrophoneManager.cs** 中的所有程式碼撰寫練習，或複製並貼上完成的程式碼，如下所示：

```cs
// Copyright (c) Microsoft Corporation. All rights reserved.
// Licensed under the MIT License. See LICENSE in the project root for license information.

using System.Collections;
using System.Text;
using UnityEngine;
using UnityEngine.UI;
using UnityEngine.Windows.Speech;

namespace Academy
{
    public class MicrophoneManager : MonoBehaviour
    {
        [Tooltip("A text area for the recognizer to display the recognized strings.")]
        [SerializeField]
        private Text dictationDisplay;

        private DictationRecognizer dictationRecognizer;

        // Use this string to cache the text currently displayed in the text box.
        private StringBuilder textSoFar;

        // Using an empty string specifies the default microphone.
        private static string deviceName = string.Empty;
        private int samplingRate;
        private const int messageLength = 10;

        // Use this to reset the UI once the Microphone is done recording after it was started.
        private bool hasRecordingStarted;

        void Awake()
        {
            /* TODO: DEVELOPER CODING EXERCISE 3.a */

            // 3.a: Create a new DictationRecognizer and assign it to dictationRecognizer variable.
            dictationRecognizer = new DictationRecognizer();

            // 3.a: Register for dictationRecognizer.DictationHypothesis and implement DictationHypothesis below
            // This event is fired while the user is talking. As the recognizer listens, it provides text of what it's heard so far.
            dictationRecognizer.DictationHypothesis += DictationRecognizer_DictationHypothesis;

            // 3.a: Register for dictationRecognizer.DictationResult and implement DictationResult below
            // This event is fired after the user pauses, typically at the end of a sentence. The full recognized string is returned here.
            dictationRecognizer.DictationResult += DictationRecognizer_DictationResult;

            // 3.a: Register for dictationRecognizer.DictationComplete and implement DictationComplete below
            // This event is fired when the recognizer stops, whether from Stop() being called, a timeout occurring, or some other error.
            dictationRecognizer.DictationComplete += DictationRecognizer_DictationComplete;

            // 3.a: Register for dictationRecognizer.DictationError and implement DictationError below
            // This event is fired when an error occurs.
            dictationRecognizer.DictationError += DictationRecognizer_DictationError;

            // Query the maximum frequency of the default microphone. Use 'unused' to ignore the minimum frequency.
            int unused;
            Microphone.GetDeviceCaps(deviceName, out unused, out samplingRate);

            // Use this string to cache the text currently displayed in the text box.
            textSoFar = new StringBuilder();

            // Use this to reset the UI once the Microphone is done recording after it was started.
            hasRecordingStarted = false;
        }

        void Update()
        {
            // 3.a: Add condition to check if dictationRecognizer.Status is Running
            if (hasRecordingStarted && !Microphone.IsRecording(deviceName) && dictationRecognizer.Status == SpeechSystemStatus.Running)
            {
                // Reset the flag now that we're cleaning up the UI.
                hasRecordingStarted = false;

                // This acts like pressing the Stop button and sends the message to the Communicator.
                // If the microphone stops as a result of timing out, make sure to manually stop the dictation recognizer.
                // Look at the StopRecording function.
                SendMessage("RecordStop");
            }
        }

        /// <summary>
        /// Turns on the dictation recognizer and begins recording audio from the default microphone.
        /// </summary>
        /// <returns>The audio clip recorded from the microphone.</returns>
        public AudioClip StartRecording()
        {
            // 3.a Shutdown the PhraseRecognitionSystem. This controls the KeywordRecognizers
            PhraseRecognitionSystem.Shutdown();

            // 3.a: Start dictationRecognizer
            dictationRecognizer.Start();

            // 3.a Uncomment this line
            dictationDisplay.text = "Dictation is starting. It may take time to display your text the first time, but begin speaking now...";

            // Set the flag that we've started recording.
            hasRecordingStarted = true;

            // Start recording from the microphone for 10 seconds.
            return Microphone.Start(deviceName, false, messageLength, samplingRate);
        }

        /// <summary>
        /// Ends the recording session.
        /// </summary>
        public void StopRecording()
        {
            // 3.a: Check if dictationRecognizer.Status is Running and stop it if so
            if (dictationRecognizer.Status == SpeechSystemStatus.Running)
            {
                dictationRecognizer.Stop();
            }

            Microphone.End(deviceName);
        }

        /// <summary>
        /// This event is fired while the user is talking. As the recognizer listens, it provides text of what it's heard so far.
        /// </summary>
        /// <param name="text">The currently hypothesized recognition.</param>
        private void DictationRecognizer_DictationHypothesis(string text)
        {
            // 3.a: Set DictationDisplay text to be textSoFar and new hypothesized text
            // We don't want to append to textSoFar yet, because the hypothesis may have changed on the next event
            dictationDisplay.text = textSoFar.ToString() + " " + text + "...";
        }

        /// <summary>
        /// This event is fired after the user pauses, typically at the end of a sentence. The full recognized string is returned here.
        /// </summary>
        /// <param name="text">The text that was heard by the recognizer.</param>
        /// <param name="confidence">A representation of how confident (rejected, low, medium, high) the recognizer is of this recognition.</param>
        private void DictationRecognizer_DictationResult(string text, ConfidenceLevel confidence)
        {
            // 3.a: Append textSoFar with latest text
            textSoFar.Append(text + ". ");

            // 3.a: Set DictationDisplay text to be textSoFar
            dictationDisplay.text = textSoFar.ToString();
        }

        /// <summary>
        /// This event is fired when the recognizer stops, whether from Stop() being called, a timeout occurring, or some other error.
        /// Typically, this will simply return "Complete". In this case, we check to see if the recognizer timed out.
        /// </summary>
        /// <param name="cause">An enumerated reason for the session completing.</param>
        private void DictationRecognizer_DictationComplete(DictationCompletionCause cause)
        {
            // If Timeout occurs, the user has been silent for too long.
            // With dictation, the default timeout after a recognition is 20 seconds.
            // The default timeout with initial silence is 5 seconds.
            if (cause == DictationCompletionCause.TimeoutExceeded)
            {
                Microphone.End(deviceName);

                dictationDisplay.text = "Dictation has timed out. Please press the record button again.";
                SendMessage("ResetAfterTimeout");
            }
        }

        /// <summary>
        /// This event is fired when an error occurs.
        /// </summary>
        /// <param name="error">The string representation of the error reason.</param>
        /// <param name="hresult">The int representation of the hresult.</param>
        private void DictationRecognizer_DictationError(string error, int hresult)
        {
            // 3.a: Set DictationDisplay text to be the error string
            dictationDisplay.text = error + "\nHRESULT: " + hresult;
        }

        /// <summary>
        /// The dictation recognizer may not turn off immediately, so this call blocks on
        /// the recognizer reporting that it has actually stopped.
        /// </summary>
        public IEnumerator WaitForDictationToStop()
        {
            while (dictationRecognizer != null && dictationRecognizer.Status == SpeechSystemStatus.Running)
            {
                yield return null;
            }
        }
    }
}
```

### <a name="build-and-deploy"></a>建置和部署

* 在 Visual Studio 中重建並部署至您的裝置。
* 使用輕量手勢關閉 [符合] 方塊。
* 觀賞太空人的監看，然後說「 *開啟 Communicator* 」。
* 選取 [ **錄製** ] 按鈕 (麥克風) 以記錄您的訊息。
* 開始說話。 **聽寫辨識器** 會解讀您的語音，並顯示 communicator 中的假設文字。
* 當您記錄訊息時，請嘗試說出「 *傳送訊息* 」。 請注意， **關鍵字辨識器** 沒有回應，因為 **聽寫辨識器** 仍在作用中。
* 停止說話幾秒鐘。 觀賞聽寫辨識器完成其假設並顯示最終結果。
* 開始說話，然後暫停20秒。 這會導致 **聽寫辨識器** 超時。
* 請注意，在上述 timeout 之後， **關鍵字辨識器** 會重新啟用。 Communicator 現在會回應語音命令。
* 說「 *傳送訊息* 」，將訊息傳送至太空人。

## <a name="chapter-4---grammar-recognizer"></a>第4章-文法辨識器

>[!VIDEO https://www.youtube.com/embed/J2dYJNSvv18]

### <a name="objectives"></a>目標

* 使用文法辨識器，根據 SRGS 或語音辨識文法規格（file）辨識使用者的語音。

>[!NOTE]
>必須針對要從麥克風錄製的應用程式宣告 **麥克風** 功能。 您已在 MR 輸入212中為您完成這項操作，但請記住您自己的專案。
>
>1. 在 Unity 編輯器中，流覽至 [> Player 編輯 > 專案設定]，移至播放機設定
>2. 按一下 [通用 Windows 平臺] 索引標籤
>3. 在 [發佈設定 > 功能] 區段中，檢查 **麥克風** 功能

### <a name="instructions"></a>Instructions

1. **在 [階層** ] 面板中搜尋 **Jetpack_Center** ，然後選取它。
2. 在 [偵測 **器** ] 面板中尋找 **Tagalong 動作** 腳本。
3. 按一下 [物件] 右邊的小圓圈， **沿著欄位標記** 。
4. 在彈出的視窗中，搜尋 **SRGSToolbox** ，然後從清單中選取它。
5. 請查看 **StreamingAssets** 資料夾中的 **SRGSColor.xml** 檔案。
    1. 您可以在 [W3C 網站上](https://www.w3.org/TR/speech-grammar/)找到 SRGS 設計規格。

在我們的 SRGS 檔案中，有三種類型的規則：

* 此規則可讓您從十二個色彩的清單中說出一種色彩。
* 有三個規則會接聽色彩規則和三個圖形之一的組合。
* ColorChooser 的根規則，它會接聽三個「色彩 + 圖形」規則的任何組合。 您可以依任何順序或從1到全部三個的任意數量，來說出圖形。 這是唯一接聽的規則，因為它在初始文法標記中是指定為檔案頂端的根規則 &lt; &gt; 。

### <a name="build-and-deploy"></a>建置和部署

* 在 Unity 中重建應用程式，然後從 Visual Studio 建立和部署，以在 HoloLens 上體驗應用程式。
* 使用輕量手勢關閉 [符合] 方塊。
* 看看太空人的 jetpack，然後執行一下點一下手勢。
* 開始說話。 **文法辨識器** 會解讀您的語音，並根據辨識來變更圖形的色彩。 範例命令為「藍色圓圈、黃色方形」。
* 執行另一個輕量手勢來關閉工具箱。

## <a name="the-end"></a>結束

恭喜！ 您現在已完成 **MR 輸入212： Voice** 。

* 您知道語音命令的 Dos 和注意事項。
* 您已瞭解如何運用工具提示，讓使用者知道語音命令。
* 您看到了數種類型的意見反應，用來確認使用者的聲音聽起來。
* 您知道如何在關鍵字辨識器與聽寫辨識器之間切換，以及這兩項功能如何理解及解讀您的聲音。
* 您已瞭解如何在您的應用程式中使用 SRGS 檔案和文法辨識器進行語音辨識。