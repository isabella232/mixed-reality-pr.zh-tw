---
title: Azure 語音服務教學課程 - 1。 整合並使用語音辨識和文字記錄
description: 完成此課程以了解如何在混合實境應用程式中實作 Azure 語音 SDK。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens, MRTK, 混合實境工具組, UWP, Azure 空間錨點, 語音辨識, Windows 10
ms.localizationpriority: high
ms.openlocfilehash: a12163dda0a6bf961c6c34ebc35b6e00f491d6ca59c08dfba7c5126e797d089a
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2021
ms.locfileid: "115214607"
---
# <a name="1-integrating-and-using-speech-recognition-and-transcription"></a>1.整合並使用語音辨識和文字記錄

## <a name="overview"></a>概觀

在此教學課程系列中，您將建立一個混合實境應用程式，以探索 Azure 語音服務與 HoloLens 2 的使用方式。 當您完成本教學課程系列時，您將能夠使用裝置的麥克風即時將語音轉譯成文字、將語音翻譯成其他語言，以及利用意圖辨識功能來使用人工智慧了解語音命令。

## <a name="objectives"></a>目標

* 了解如何將 Azure 語音服務與 HoloLens 2 應用程式整合
* 了解如何使用語音辨識來轉譯文字

## <a name="prerequisites"></a>必要條件

>[!TIP]
>如果您尚未完成[入門教學課程](mr-learning-base-01.md)系列，建議您先完成這些教學課程。

* 已[安裝正確工具](../../install-the-tools.md)的 Windows 10 電腦
* Windows 10 SDK 10.0.18362.0 或更新版本
* 基本的 C# 程式設計能力
* 已[針對開發而設定](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)的 HoloLens 2 裝置
* 已安裝 unity 2020/2019 LTS 的<a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">unity 中樞</a>，並已新增通用 Windows 平臺組建支援模組

> [!Important]
> 此教學課程系列支援 Unity 2020 LTS (目前的 2020.3) 如果您使用 Open XR 或 Windows XR 外掛程式，以及 unity 2019 LTS (目前 2019.4. x) 如果您使用舊版的 WSA 或 Windows XR 外掛程式。 這個版本能取代上述連結必要條件中所述的任何 Unity 版本需求。

## <a name="creating-and-preparing-the-unity-project"></a>建立和準備 Unity 專案

在本節中，您將建立新的 Unity 專案，並使該專案準備好進行 MRTK 開發。

為此，請先遵循[初始化您的專案和第一個應用程式](mr-learning-base-02.md) (但不包括[對您的裝置建置應用程式](mr-learning-base-02.md#building-your-application-to-your-hololens-2)的指示)，其中包括下列步驟：

1. [建立 Unity 專案](mr-learning-base-02.md#creating-the-unity-project)，並為其提供適當的名稱，例如「MRTK 教學課程」
2. [切換建置平台](mr-learning-base-02.md#configuring-the-unity-project)
3. [匯入 TextMeshPro 基本資源](mr-learning-base-04.md#importing-the-textmeshpro-essential-resources)
4. [匯入混合現實工具組和設定 Unity 專案](mr-learning-base-02.md#importing-the-mixed-reality-toolkit-and-configuring-the-unity-project)
5. [建立和設定場景](mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk)並為場景提供適當的名稱，例如 AzureCloudServices

然後，遵循 [變更空間感知顯示選項](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) 的指示，以確定您場景的 MRTK 設定檔是 **DefaultHoloLens2ConfigurationProfile**  ，並將空間感知網格的顯示選項變更為 **遮蔽**。

## <a name="configuring-the-speech-commands-start-behavior"></a>設定語音命令啟動行為

由於您將使用語音 SDK 進行語音辨識和轉譯，因此您需要設定 MRTK 語音命令，使其不會干擾語音 SDK 功能。 若要達到此目的，您可以將語音命令啟動行為從 [自動啟動] 變更為 [手動啟動]。

在 [階層] 視窗中選取 **MixedRealityToolkit** 物件之後，於 [偵測器] 視窗中選取 [輸入] 索引標籤，並複製 **DefaultHoloLens2InputSystemProfile** 和 **DefaultMixedRealitySpeechCommandsProfile**，然後將 **啟動行為** 的語音命令變更為 [手動啟動]：

![mrlearning-語音1](images/mrlearning-speech/tutorial1-section2-step1-1.png)

## <a name="configuring-the-capabilities"></a>設定功能

在 Unity 功能表中，選取 [編輯] > [專案設定...] 來開啟 [玩家設定] 視窗，然後找出 [玩家] >  [發佈設定] 區段：

![mrlearning-語音2](images/mrlearning-speech/tutorial1-section3-step1-1.png)

在 [**發行設定** 中，向下滾動至 [**功能**] 區段，並再次確認已啟用 [ **InternetClient**]、[**麥克風**] 和 [ **>spatialperception** ] 功能（當您在教學課程開頭建立專案時所啟用）。 然後，啟用 **InternetClientServer** 和 **PrivateNetworkClientServer** 功能：

![mrlearning-語音3](images/mrlearning-speech/tutorial1-section3-step1-2.png)

## <a name="importing-the-tutorial-assets"></a>匯入教學課程資產

下載並 **依列出順序** 來 **匯入** 下列 Unity 自訂套件：

* [Microsoft.CognitiveServices.Speech.N.N.N.unitypackage](https://aka.ms/csspeech/unitypackage) (最新版本)
* [MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.3.0.3/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage)
* [MRTK.HoloLens2. AzureSpeechServices. 2.5.2. unitypackage](https://github.com/onginnovations/MixedRealityLearning/releases/download/azure-speech-services-v2.5.2/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpeechServices.2.5.2.unitypackage)

> [!TIP]
> 如需有關如何匯入 Unity 自訂套件的提示，您可以參閱[匯入混合實境工具組](mr-learning-base-04.md#importing-the-tutorial-assets) 的指示。

匯入教學課程資產之後，您的專案視窗看起來應該會像這樣：

![mrlearning-語音4](images/mrlearning-speech/tutorial1-section4-step1-1.png)

您必須設定 Unity 專案以發佈適用于 ARM64 的 Azure 語音外掛程式，若要在 Project 視窗中進行這項作業，請流覽至 [**資產**]  >  **>speechsdk.quickstart**  >  **外掛程式** 的 [  >  **WSA**  >  **ARM64** ]，然後選取 [ **CognitiveServices]。**

![mrlearning-語音5](images/mrlearning-speech/tutorial1-section4-step1-2.PNG)

在仍選取 **CognitiveServices** 的情況下，在 [偵測器] 視窗中啟用 [ **WSA Player** ]，然後在 [ **平臺設定** ] 下，選取 [ **UWP** for SDK]、[針對 CPU **ARM64** ]，然後按一下 [套用] 將這些設定套用至外掛程式。

![mrlearning-語音6](images/mrlearning-speech/tutorial1-section4-step1-3.PNG)

針對其餘的每個外掛程式重複此步驟：

* **Microsoft.CognitiveServices.Speech.extension.audio.sys**
* **CognitiveServices 副檔名. kws**
* **Microsoft.CognitiveServices.Speech.extension.lu**
* **Microsoft.CognitiveServices.Speech.extension.silk_codec**

## <a name="preparing-the-scene"></a>準備場景

在本節中，您將藉由新增教學課程 Prefab 來準備場景，並設定 Lunarcom Controller (指令碼) 元件來控制您的場景。

在 [專案] 視窗中，瀏覽至 [資產] > [MRTK.Tutorials.AzureSpeechServices] > [Prefabs] 資料夾，並將 **Lunarcom** Prefab 拖曳至 [階層] 視窗來新增至您的場景：

![mrlearning-語音7](images/mrlearning-speech/tutorial1-section5-step1-1.png)

在 [階層] 視窗中仍選取 **Lunarcom** 物件的情況下，於 [偵測器] 視窗中使用 [新增元件] 按鈕來將 **Lunarcom Controller (指令碼)** 元件新增至 Lunarcom 物件：

![mrlearning-語音8](images/mrlearning-speech/tutorial1-section5-step1-2.png)

> [!NOTE]
> The Lunarcom Controller (指令碼) 元件不是 MRTK 的一部分。 這是本教學課程資產隨附的元件。

在仍選取 **Lunarcom** 物件的情況下，將其展開以顯示其子物件，然後將 **Terminal** 物件拖曳到 Lunarcom Controller (指令碼) 元件的 [終端機] 欄位中：

![mrlearning-語音9](images/mrlearning-speech/tutorial1-section5-step1-3.png)

在仍選取 **Lunarcom** 物件的情況下，展開 [終端機] 物件以顯示其子物件，然後將 **ConnectionLight** 物件拖曳至 Lunarcom Controller (指令碼) 元件的 [連接光源] 欄位，並將 **OutputText** 物件拖曳至 [輸出文字] 欄位中：

![mrlearning-語音10](images/mrlearning-speech/tutorial1-section5-step1-4.png)

在仍選取 **Lunarcom** 物件的情況下，展開 Buttons 物件以顯示其子物件，然後在 [偵測器] 視窗中展開 [按鈕] 清單，將其 [大小] 設定為 3，然後將 **MicButton**、**SatelliteButton** 和 **RocketButton** 物件分別拖曳至 **元素** 0、1 及 2 的欄位：

![mrlearning-語音11](images/mrlearning-speech/tutorial1-section5-step1-5.png)

## <a name="connecting-the-unity-project-to-the-azure-resource"></a>將 Unity 專案連接至 Azure 資源

若要使用 Azure 語音服務，您必須建立 Azure 資源，並取得語音服務的 API 金鑰。 請遵循[免費試用語音服務](/azure/cognitive-services/speech-service/get-started)的指示，並記下您的服務區域 (也就是「位置」) 和 API 金鑰 (也就是 Key1 或 Key2)。

在 [階層] 視窗中選取 **Lunarcom** 物件，然後在 [偵測器] 視窗中尋找 **Lunarcom Controller (指令碼)** 元件的 [語音 SDK 認證] 區段並進行設定，如下所示：

* 在 [語音服務 API 金鑰] 欄位中，輸入您的 API 金鑰 (Key1 或 Key2)
* 在 [語音服務區域] 欄位中，輸入您的服務區域 (位置)，請使用小寫字母並將空格移除

![mrlearning-語音12](images/mrlearning-speech/tutorial1-section6-step1-1.png)

## <a name="using-speech-recognition-to-transcribe-speech"></a>使用語音辨識來轉譯語音

在 [階層] 視窗中選取 **Lunarcom** 物件，然後在 [偵測器] 視窗中使用 [新增元件] 按鈕來將 **Lunarcom Speech Recognizer (指令碼)** 元件新增至 Lunarcom 物件：

![mrlearning-語音13](images/mrlearning-speech/tutorial1-section7-step1-1.png)

> [!NOTE]
> Lunarcom Speech Recognizer (指令碼) 元件不是 MRTK 的一部分。 這是本教學課程資產隨附的元件。

如果您現在進入遊戲模式，您可以先按下麥克風按鈕來測試語音辨識：

![mrlearning-語音14](images/mrlearning-speech/tutorial1-section7-step1-2.png)

接下來，假設您的電腦有麥克風，當您說到某個項目時，您的語音會在終端機面板上進行轉譯：

![mrlearning-語音15](images/mrlearning-speech/tutorial1-section7-step1-3.png)

> [!CAUTION]
> 應用程式必須連線到 Azure，因此請確定您的電腦/裝置已連線到網際網路。

## <a name="congratulations"></a>恭喜！

您已實行由 Azure 提供技術支援的語音辨識。 在您的裝置上執行應用程式，以確保功能可正常運作。

在下一個教學課程中，您將了解如何使用 Azure 語音辨識來執行命令。

> [!div class="nextstepaction"]
> [下一個教學課程： 2. 使用 Azure 語音辨識執行命令](mrlearning-speechSDK-ch2.md)
