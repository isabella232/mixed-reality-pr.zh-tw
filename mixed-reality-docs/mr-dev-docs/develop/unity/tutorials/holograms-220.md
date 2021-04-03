---
title: HoloLens (第1代) 空間 220-空間音效
description: 遵循此程式碼逐步解說，使用 Unity、Visual Studio 和 HoloLens 來學習空間音效概念的詳細資料。
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit、mixedrealitytoolkit、mixedrealitytoolkit-unity、學術、教學課程、空間音效、HoloLens、混合現實學院、unity、混合現實耳機、windows Mixed Reality 耳機、虛擬實境耳機、Windows 10
ms.openlocfilehash: 789f4da924c00554042ad991cc5610d3e816f12d
ms.sourcegitcommit: 3236abcba27335fe3d52e38423d2b265ca883355
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2021
ms.locfileid: "106269994"
---
# <a name="hololens-1st-gen-spatial-220-spatial-sound"></a>HoloLens (第1代) 空間220：空間音效

>[!IMPORTANT]
>混合的現實學術教學課程是以 HoloLens (第一代) 、Unity 2017 和混合現實的沉浸式耳機來設計的。  因此，對於仍在尋找這些裝置開發指引的開發人員而言，我們覺得這些教學課程很重要。 這些教學課程 **_不_** 會使用最新的工具組或互動進行 HoloLens 2，而且可能與較新版本的 Unity 不相容。  系統會保留這些資訊，以繼續在支援的裝置上運作。 已針對 HoloLens 2 公佈[一系列新的教學課程](mrlearning-base.md)。

[空間音效](../../../design/spatial-sound.md) breathes 生活進入全像全球，並讓他們在世界各地都存在。 全像投影是由光線和音效所組成，如果您似乎無法看見您的全像影像，空間音效可以協助您找到它們。 空間音效與您在無線電上聽到的一般音效不一樣，它是位於3D 空間的音效。 有了空間音效，您就可以讓像是在您後方、您或甚至是在您的頭上的全像投影一樣： 在此課程中，您將會：

* 設定您的開發環境以使用 Microsoft 空間音效。
* 使用空間音效來增強互動。
* 使用空間音效搭配 [空間對應](../../../design/spatial-mapping.md)。
* 瞭解音效設計和混合最佳做法。
* 使用音效強化特殊效果，並讓使用者進入混合現實世界。

## <a name="device-support"></a>裝置支援

<table>
<tr>
<th>課程</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">沉浸式頭戴裝置</a></th>
</tr><tr>
<td>MR Spatial 220：空間音效</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="before-you-start"></a>在您開始使用 Intune 之前

### <a name="prerequisites"></a>必要條件

* [已安裝正確工具](../../../develop/install-the-tools.md)的 Windows 10 電腦。
* 一些基本的 c # 程式設計功能。
* 您應已完成 [MR 基本的 101](../../../develop/unity/tutorials/holograms-101.md)。
* [針對開發設定](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)的 HoloLens 裝置。

### <a name="project-files"></a>專案檔

* 下載專案 [所需的](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-220-SpatialSound.zip) 檔案。 需要 Unity 2017.2 或更新版本。
  * 如果您仍然需要 Unity 5.6 支援，請使用 [此版本](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-220.zip)。 此版本可能不再是最新版本。
  * 如果您仍然需要 Unity 5.5 支援，請使用 [此版本](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-220.zip)。 此版本可能不再是最新版本。
  * 如果您仍然需要 Unity 5.4 支援，請使用 [此版本](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-220.zip)。 此版本可能不再是最新版本。
* 取消將檔案封存到您的桌面或其他易於觸及的位置。

>[!NOTE]
>如果您想要在下載之前查看原始程式碼， [可在 GitHub 上](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-220-SpatialSound)取得。

### <a name="errata-and-notes"></a>勘誤表和記事

* 您必須在 [工具]-[>選項] 下的 Visual Studio 中停用 [啟用 Just My Code] (*未* 核取) ，才能在程式碼中叫用中斷點。

## <a name="chapter-1---unity-setup"></a>第1章-Unity 設定

### <a name="objectives"></a>目標

* 變更 Unity 的音效設定以使用 Microsoft 空間音效。
* 將3D 音效新增至 Unity 中的物件。

### <a name="instructions"></a>指示

* 啟動 Unity。
* 選取 [開啟]  。
* 流覽至您的桌面，並尋找您先前取消封存的資料夾。
* 按一下 [ **Starting\Decibel** ] 資料夾，然後按下 [ **選取資料夾** ] 按鈕。
* 等候專案在 Unity 中載入。
* 在 [ **專案** ] 面板中，開啟 [ **Scenes\Decibel.unity**]。
* **在 [階層**] 面板中，展開 [ **HologramCollection** ]，然後選取 [ **P0LY**]。
* 在 [偵測器] 中，展開 [ **spatialize** ]，並注意 [沒有 **Spatialize** ] 核取方塊。

根據預設，Unity 不會載入空間定位器外掛程式。 下列步驟將會在專案中啟用空間音效。

* 在 Unity 的頂端功能表中，移至 [ **編輯 > 專案設定 > 音訊**]。
* 尋找 [ **空間定位器外掛程式** ] 下拉式清單，然後選取 [ **MS HRTF 空間定位器**]。
* **在 [階層**] 面板中，選取 [ **HologramCollection > P0LY**]。
* 在 [偵測 **器** ] 面板中，尋找 **音訊來源** 元件。
* 核取 [ **Spatialize** ] 核取方塊。
* 將 **空間 Blend** 滑杆拖曳至 **3d**，或在編輯方塊中輸入 **1** 。

我們現在會在 Unity 中建立專案，並在 Visual Studio 中設定解決方案。

1. 在 Unity 中，選取 [ **File > Build Settings**]。
2. 按一下 [ **新增開啟場景** ] 以加入場景。
3. 在 [**平臺**] 清單中選取 **通用 Windows 平臺**，然後按一下 [**切換平臺**]。
4. 如果您是特別針對 HoloLens 進行開發，請將 **目標裝置** 設定為 **hololens**。 否則，請將它保留在 **任何裝置** 上。
5. 請確定 **組建類型** 設定為 [ **D3D** ]，並將 [ **Sdk** ] 設定為 [ **最新安裝** 的 (，其應為 SDK 16299 或更新版本的) 。
6. 按一下 [建置]。
7. 建立名為 "App" 的 **新資料夾** 。
8. 按一下 **應用程式** 資料夾。
9. 按下 [ **選取資料夾**]。

當 Unity 完成時，將會出現檔案總管視窗。

1. 開啟 **應用程式** 資料夾。
2. 開啟 [ **分貝 Visual Studio] 解決方案**。

如果要部署到 HoloLens：

1. 使用 Visual Studio 中的頂端工具列，將目標從 Debug 變更為 **Release** ，以及從 ARM 變更為 **x86**。
2. 按一下 [本機電腦] 按鈕旁的下拉箭號，然後選取 [ **遠端電腦**]。
3. 輸入 **您的 HoloLens 裝置 IP 位址** ，並將驗證模式設定為 **通用 (未加密的通訊協定)**。 按一下 [選取]。 如果您不知道您的裝置 IP 位址，請查看 [ **設定] > Network & Internet > Advanced 選項**。
4. 在頂端功能表列中，按一下 [ **Debug-> 啟動但不進行調試** ]，或按 **Ctrl + F5**。 如果這是您第一次部署至您的裝置，您必須將 [它與 Visual Studio 配對](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#pairing-your-device)。

如果部署到沉浸式耳機：

1. 使用 Visual Studio 中的頂端工具列，將目標從 Debug 變更為 **Release** ，以及從 ARM 變更為 **x64**。
2. 請確定部署目標設定為 [ **本機電腦**]。
3. 在頂端功能表列中，按一下 [ **Debug-> 啟動但不進行調試** ]，或按 **Ctrl + F5**。

## <a name="chapter-2---spatial-sound-and-interaction"></a>第2章-空間音效和互動

### <a name="objectives"></a>目標

* 使用音效增強全像配音。
* 使用音效指示使用者的注視。
* 使用音效提供手勢意見反應。

### <a name="part-1---enhancing-realism"></a>第1部分-增強真實感

#### <a name="key-concepts"></a>重要概念

* Spatialize 全像音效。
* 音效來源應放置於全息圖的適當位置。

音效的適當位置將會取決於全像影像。 比方說，如果全息圖是人類的，則音效來源應該位於嘴附近，而不是距離。

#### <a name="instructions"></a>指示

下列指示會將 hrtf 音效附加至全像影像。

* **在 [階層**] 面板中，展開 [ **HologramCollection** ]，然後選取 [ **P0LY**]。
* 在 [偵測 **器** ] 面板的 [ **spatialize**] 中，按一下 [ **AudioClip** ] 旁的圓形，然後從快顯視窗中選取 [ **PolyHover** ]。
* 按一下 [ **輸出** ] 旁的圓形，然後從快顯視窗中選取 [ **SoundEffects** ]。

專案分貝會使用 Unity **AudioMixer** 元件來調整音效群組的音效等級。 藉由以這種方式將聲音分組，可以調整整體磁片區，同時維持每個音效的相對音量。

* 在 **spatialize** 中，展開 [ **3d 音效設定**]。
* 將 **Doppler 層級** 設定為 **0**。

將 Doppler 層級設定為 [零] 會停用 (由全像影像或使用者) 的移動所造成的音調變化。 Doppler 的典型範例是快速移動的汽車。 當汽車採用固定的接聽程式時，引擎的音調也會上升。 當它通過接聽程式時，會降低距離。

### <a name="part-2---directing-the-users-gaze"></a>第2部分-引導使用者的注視

#### <a name="key-concepts"></a>重要概念

* 使用音效呼叫重要的全像投影。
* 此耳可協助引導眼睛的外觀。
* 大腦有一些學習的期望。

瞭解預期的其中一個範例是，鳥通常會高於人類的標題。 如果使用者聽到鳥音效，他們的初始反應就是查閱。 將鳥放在使用者的下方，可能會讓他們面對正確的音效方向，但根據預期需要查閱，找不到影像。

#### <a name="instructions"></a>指示

下列指示可讓 P0LY 在您後方隱藏，讓您可以使用音效找出全像影像。

* **在 [階層**] 面板中，選取 [**管理員**]。
* 在 [偵測 **器** ] 面板中，尋找 [ **語音輸入處理常式**]。
* 在 [ **語音輸入處理常式**] 中，展開 [ **移至隱藏**]。
* 將 **函數** 變更為 **PolyActions. GoHide**。

![關鍵字：移至隱藏](images/gohide.png)

### <a name="part-3---gesture-feedback"></a>第3部分-手勢意見反應

#### <a name="key-concepts"></a>重要概念

* 使用音效為使用者提供正面的手勢確認
* 不要讓使用者過高的聲音變得太過
* 微妙的音效效果最佳-請勿失色經驗

#### <a name="instructions"></a>指示

* **在 [階層**] 面板中，展開 [ **HologramCollection**]。
* 展開 [ **EnergyHub** ]，然後選取 [ **基底**]。
* 在 [偵測 **器** ] 面板中，按一下 [ **新增元件** ] 並加入 **手勢音效處理常式**。
* 在 [ **手勢音效處理常式**] 中，按一下 [ **導覽開始的剪輯** ] 和 [ **導覽更新的剪輯** ] 旁的圓形，然後從快顯視窗中選取 [ **RotateClick** ]。
* 按兩下 [GestureSoundHandler] 以 Visual Studio 載入。

手勢音效處理常式會執行下列工作：

* 建立並設定 **spatialize**。
* 將 **spatialize** 放在適當 **GameObject** 的位置。
* 播放與手勢相關聯的 **AudioClip** 。

#### <a name="build-and-deploy"></a>建置和部署

1. 在 Unity 中，選取 [ **File > Build Settings**]。
2. 按一下 [建置]。
3. 按一下 **應用程式** 資料夾。
4. 按下 [ **選取資料夾**]。

確認工具列中顯示的是「發行」、「x86」、「x64」和「遠端裝置」。 如果沒有，這就是 Visual Studio 的編碼實例。 您可能需要從應用程式資料夾重新開啟方案。

* 出現提示時，請重載專案檔。
* 同樣地，從 Visual Studio 部署。

部署應用程式之後：

* 觀察當您在 P0LY 上移動時的音效變化。
* 說「 *Go 隱藏* 」讓 P0LY 移至您後方的位置。 依音效找出它。
* 注視能源中樞的基底。 您可以用滑鼠左鍵或向右拖曳來旋轉全像投影，然後留意一下按一下音效如何確認手勢。

注意：有一個文字面板會與您一起標記。 這將包含可在整個課程中使用的語音命令。

## <a name="chapter-3---spatial-sound-and-spatial-mapping"></a>第3章-空間音效和空間對應

### <a name="objectives"></a>目標

* 使用音效確認全像全息和真實世界之間的互動。
* 使用實體世界遮蔽音效。

### <a name="part-1---physical-world-interaction"></a>第1部分-實體世界互動

#### <a name="key-concepts"></a>重要概念

* 實體物件通常會在遇到表面或另一個物件時產生音效。
* 音效應該在體驗中是適當的內容。

例如，在資料表上設定杯的音效應該會比將科羅拉多放在金屬片上的音效更安靜。

#### <a name="instructions"></a>指示

* **在 [階層**] 面板中，展開 [ **HologramCollection**]。
* 展開 [ **EnergyHub**]，選取 [ **基底**]。
* 在 [偵測 **器** ] 面板中，按一下 [ **新增元件** ]，然後 **以音效和動作** 新增點一下。
* 利用 **音效和動作來放置**：
  * 選取 **[在點處放置父系**]。
  * 設定放置 **音效** 以 **放置**。
  * 將 **取貨音效** 設定為 **收取**。
  * 在 [ **取貨動作** ] 和 [ **放置] 動作** 下，按右下方的 +。 將 EnergyHub 從場景拖曳至 [ **無] (物件)** 欄位。
    * 在 [**裝貨] 動作** 底下，按一下 [**沒有函數**  ->  **EnergyHubBase**  ->  **ResetAnimation**]。
    * 在 [**放置動作**] 下方，按一下 [**沒有函數**  ->  **EnergyHubBase**  ->  **>onselect**]。

![利用音效和動作來放置](images/holograms220-taptoplace.png)

### <a name="part-2---sound-occlusion"></a>第2部分-音效遮蔽

#### <a name="key-concepts"></a>重要概念

* 像光一樣的音效可以是 pixels occluded。

典型的範例是音樂會廳。 當接聽程式位於大廳之外且門已關閉時，音樂音效會 muffled。 通常磁片區也會減少。 當大門開啟時，就會在實際的音量聽到音效的整個範圍。 高頻率音效通常會吸收較低的頻率。

#### <a name="instructions"></a>指示

* **在 [階層**] 面板中，展開 [ **HologramCollection** ]，然後選取 [ **P0LY**]。
* 在 [偵測 **器** ] 面板中，按一下 [ **新增元件** ]，然後新增 **音訊發射器**。

音訊發射器類別提供下列功能：

* 還原 **spatialize** 磁片區的任何變更。
* 從使用者的位置，以 **AudioEmitter** 附加的 **GameObject** 方向來執行 **RaycastNonAlloc** 。

RaycastNonAlloc 方法會用來做為效能優化，以限制配置以及傳回的結果數目。

* 針對每個遇到的 **IAudioInfluencer** ，會呼叫 **ApplyEffect** 方法。
* 針對不再遇到的每個先前 **IAudioInfluencer** ，請呼叫 **RemoveEffect** 方法。

請注意，AudioEmitter 會更新人為時間刻度，而不是每個畫面上的。 這樣做的原因是因為人們通常不會移動到足夠的速度，因此效果必須比每一季或半秒更頻繁地更新。 從某個位置快速傳送到另一個位置的全像影像，可能會破壞假像。

* **在 [階層**] 面板中，展開 [ **HologramCollection**]。
* 展開 [ **EnergyHub** ]，然後選取 [ **BlobOutside**]。
* 在 [偵測 **器** ] 面板中，按一下 [ **新增元件** ]，然後新增 **音訊 Occluder**。
* 在 [ **音訊 Occluder**] 中，將 **截止頻率** 設定為 **1500**。

此設定會將 Spatialize 頻率限制為 1500 Hz 和以下。

* 將 **磁片區傳遞** 至 **0.9**。

這項設定會將 Spatialize 的磁片區縮減為其目前層級的90%。

音訊 Occluder 會將 IAudioInfluencer 實作為：

* 使用附加至 **spatialize** 受控購買 **AudioEmitter** 的 **AudioLowPassFilter** 來套用遮蔽效果。
* 將磁片區衰減套用至 Spatialize。
* 藉由設定中性截止頻率和停用篩選來停用效果。

使用中性的頻率是 22 kHz (22000 Hz) 。 選擇此頻率的原因，是因為它高於可由人類 ear 聽到的最大頻率，所以不會對音效造成明顯影響。

* **在 [階層**] 面板中，選取 [ **SpatialMapping**]。
* 在 [偵測 **器** ] 面板中，按一下 [ **新增元件** ]，然後新增 **音訊 Occluder**。
* 在 [ **音訊 Occluder**] 中，將 **截止頻率** 設定為 **750**。

當使用者與 **AudioEmitter** 之間的路徑中有多個阻隔器時，會將最低頻率套用至篩選準則。

* 將 **磁片區傳遞** 至 **0.75**。

當使用者與 **AudioEmitter** 之間的路徑中有多個阻隔器時，會套用額外的大量傳遞。

* **在 [階層**] 面板中，選取 [**管理員**]。
* 在 [偵測 **器** ] 面板中，展開 [ **語音輸入處理常式**]。
* 在 [ **語音輸入處理常式**] 中，展開 [ **繼續收費**]。
* 將 **函數** 變更為 **PolyActions. GoCharge**。

![關鍵字： Go 收費](images/gocharge.png)

* 展開 **這裡**。
* 將 **函數** 變更為 **PolyActions. 撰寫復活**。

![關鍵字：這裡](images/comehere.png)

#### <a name="build-and-deploy"></a>建置和部署

* 同樣地，在 Unity 中建立專案，並在 Visual Studio 中部署。

部署應用程式之後：

* 說「 *繼續收費* 」以 P0LY 輸入能源中樞。

請注意音效中的變更。 它應該聽起來 muffled，而且有點安靜。 如果您可以將自己放在您和能源中樞之間的牆或其他物件，您應該會注意到因為真實世界遮蔽而 muffling 的音效。

* 說「 *來到這裡* 」讓 P0LY 離開能源中樞，並將它放在您的前方。

請注意，P0LY 結束能源中樞後，就會移除音效遮蔽。 如果您仍在聽到遮蔽，P0LY 可能會受到真實世界的 pixels occluded。 請嘗試移動以確保您有清楚的 P0LY。

### <a name="part-3---room-models"></a>第3部分-房間模型

#### <a name="key-concepts"></a>重要概念

* 空間大小提供可提供音效當地語系化的 subliminal 佇列。
* 每個 **spatialize** 都會設定房間模型。
* [MixedRealityToolkit For Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)提供用來設定房間模型的程式碼。
* 針對混合現實體驗，請選取最適合真實世界空間的房間模型。

如果您要建立虛擬實境案例，請選取最適合虛擬環境的房間模型。

## <a name="chapter-4---sound-design"></a>第4章-音效設計

### <a name="objectives"></a>目標

* 瞭解有效音效設計的考慮。
* 學習混合技術與指導方針。

### <a name="part-1---sound-and-experience-design"></a>第1部分-音效和體驗設計

本節將討論主要音效，以及體驗設計考慮與指導方針。

#### <a name="normalize-all-sounds"></a>標準化所有音效

如此一來，就不需要特殊案例的程式碼來調整每個音效的音量層級，這可能相當耗時，而且會限制輕鬆更新音效檔的能力。

#### <a name="design-for-an-untethered-experience"></a>非網路共用體驗的設計

HoloLens 是完全獨立的非網路共用全像電腦。 在移動時，您的使用者可以和將會使用您的體驗。 請務必四處流覽，以測試您的音訊組合。

#### <a name="emit-sound-from-logical-locations-on-your-holograms"></a>從您的全像位置的邏輯位置發出音效

在真實世界中，狗不會從其尾端吠，而人類的語音也不會來自于其腳。 避免讓您的音效從非預期的全息部分發出。

針對小型全像影像，從幾何中央開始發出音效是合理的。

#### <a name="familiar-sounds-are-most-localizable"></a>熟悉的音效最能當地語系化

人類心聲和音樂很容易當地語系化。 如果有人呼叫您的名字，您可以非常精確地判斷聲音的出現方向和距離。 簡短的是，不熟悉的音效也難以當地語系化。

#### <a name="be-cognizant-of-user-expectations"></a>Cognizant 使用者期望

生命體驗讓我們能夠找出音效的位置。 這是人們的聲音特別容易當地語系化的原因之一。 在放置音效時，請務必留意使用者的預期期望。

例如，當有人聽到鳥的歌曲時，通常會進行查閱，因為鳥通常會在 (飛出或在樹狀結構) 上。 使用者開啟正確的音效方向並不常見，但請查看錯誤的垂直方向，並在找不到全像時感到混淆或感到挫折。

#### <a name="avoid-hidden-emitters"></a>避免隱藏的發射器

在真實世界中，如果聽到音效，我們通常可以找出發出音效的物件。 這也應該在您的體驗中成立。 這可能很令人不安，讓使用者聽聽音效，從音效的來源，到無法查看物件。

此指導方針有一些例外。 例如，欄位中的 crickets 等環境音效不需要可見。 生命體驗讓我們熟悉這些音效的來源，而不需要加以查看。

### <a name="part-2---sound-mixing"></a>第2部分-音效混合

#### <a name="target-your-mix-for-70-volume-on-the-hololens"></a>將您在 HoloLens 上的70% 磁片區混合設為目標

混合現實體驗可讓您在真實世界中看到全像影像。 它們也應該讓真實的聲音聽起來。 70% 的磁片區目標可讓使用者在世界各地聆聽您的體驗。

#### <a name="hololens-at-100-volume-should-drown-out-external-sounds"></a>100% 磁片區的 HoloLens 應下拉式清單外部聲音

磁片區層級100% 類似于虛擬實境體驗。 使用者會以視覺化方式傳送到不同的世界。 相同的語音也是如此。

#### <a name="use-the-unity-audiomixer-to-adjust-categories-of-sounds"></a>使用 Unity AudioMixer 來調整聲音的類別

設計混合時，建立音效類別以及能夠將其磁片區增加或減少為一個單位通常會很有説明。 這會保留每個音效的相對層級，同時讓整體混合的快速且輕鬆地進行變更。 常見類別包括：音效、環境、語音轉移和背景音樂。

#### <a name="mix-sounds-based-on-the-users-gaze"></a>根據使用者的注視來混合音效

根據使用者在 (或不) 的情況下，變更您體驗的音效通常會很有用。 這項技術的其中一種常見用途是減少全像全像攝影框架外的全息體音量層級，讓使用者更容易專注于他們之前的資訊。 另一種用途是增加音效的音量，將使用者的注意力吸引到重要的活動。

#### <a name="building-your-mix"></a>打造您的混合

建立混合時，建議您從經驗的背景音訊著手，並根據重要性新增圖層。 這通常會導致每個圖層比上一個層更大。

將您的混合想像為反向漏斗圖，其中最重要的 (，且通常會在底部) quietest 音效，建議您以類似下圖的方式來結構您的混合。

![音效混合結構](images/soundlevels.png)

語音轉移是一種有趣的案例。 根據您所建立的體驗，您可能會想要有身歷聲 (未當地語系化) 音效或 spatialize 語音轉移。 兩個 Microsoft 發佈的經驗說明每個案例的絕佳範例。

[HoloTour](https://www.microsoft.com/store/p/holotour/9nblggh5pj87) 使用身歷聲語音。 當朗讀程式描述所要查看的位置時，音效是一致的，而且不會根據使用者的位置而有所不同。 這可讓朗讀程式描述場景，而不需要離開環境的 hrtf 音效。

[片段](https://www.microsoft.com/store/p/fragments/9nblggh5ggm8) 會利用 hrtf 的語音，以偵探的形式來使用。 您可以使用偵探的聲音來協助使用者關注重要的線索，就像實際的人在房間裡一樣。 這可讓您更清楚地深度解決謎的體驗。

### <a name="part-3--performance"></a>第3部分-效能

#### <a name="cpu-usage"></a>CPU 使用量

使用空間音效時，10-12 發射器將耗用大約12% 的 CPU。

#### <a name="stream-long-audio-files"></a>串流長音訊檔案

音訊資料可能很大，尤其是常見的取樣率 (44.1 和 48 kHz) 。 一般規則是，應串流處理超過 5-10 秒的音訊檔案，以減少應用程式記憶體使用量。

在 Unity 中，您可以在檔案的匯入設定中標示要串流處理的音訊檔案。

![音訊匯入設定](images/audioimportsettings.png)

## <a name="chapter-5---special-effects"></a>第5章-特殊效果

### <a name="objectives"></a>目標

* 將深度新增至「魔術視窗」。
* 將使用者帶入虛擬世界。

### <a name="magic-windows"></a>魔術視窗

#### <a name="key-concepts"></a>重要概念

* 以視覺效果吸引人，將視圖建立到隱藏的世界中。
* 藉由在隱藏體或使用者接近隱藏的世界時新增音訊效果，以增強真實感。

#### <a name="instructions"></a>指示

* **在 [階層**] 面板中，展開 [ **HologramCollection** ]，然後選取 [ **Underworld**]。
* 展開 [ **Underworld** ]，然後選取 [ **VoiceSource**]。
* 在 [偵測 **器** ] 面板中，按一下 [ **新增元件** ] 和 [新增 **使用者語音效果**]。

**Spatialize** 元件將會新增至 **VoiceSource**。

* 在 **spatialize** 中，將 [ **輸出** ] 設定為 **UserVoice (混音器)**。
* 核取 [ **Spatialize** ] 核取方塊。
* 將 **空間 Blend** 滑杆拖曳至 **3d**，或在編輯方塊中輸入 **1** 。
* 展開 [ **3D 音效設定**]。
* 將 **Doppler 層級** 設定為 **0**。
* 在 [ **使用者心聲效果**] 中，將 **父物件** 從場景設定為 **Underworld** 。
* 將 **最大距離** 設定為 **1**。

設定 [ **最大距離** ] 會告知 **使用者語音效果** 在啟用效果之前，使用者必須在父物件中的距離。

* 在 [ **使用者語音效果**] 中，展開 [ **一首哀歌參數**]。
* 將 **深度** 設定為 **0.1**。
* 設定一下 **1 個磁片** 區，再按2個 **音量** ，然後將3個 **磁片區分** 到 **0.8**。
* 將 **原始音效磁片** 區設定為 **0.5**。

先前的設定會設定 Unity **AudioChorusFilter** 的參數，這些參數是用來為使用者的語音新增豐富的聲音。

* 在 [ **使用者語音效果**] 中，展開 [ **Echo 參數**]。
* 將 **延遲** 設定為 **300**
* 將 **衰減比例** 設定為 **0.2**。
* 將 **原始音效音量** 設定為 **0**。

先前的設定會設定用來讓使用者的語音回應的 Unity **AudioEchoFilter** 參數。

使用者心聲效果腳本負責：

* 測量使用者與附加腳本的 **GameObject** 之間的距離。
* 判斷使用者是否遇到 **GameObject**。

無論距離為何，使用者都必須面對 GameObject，才能啟用效果。

* 將 **AudioChorusFilter** 和 **AudioEchoFilter** 套用至 **spatialize**。
* 停用篩選以停用效果。

使用者心聲效果會使用來自 [MixedRealityToolkit For Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)的 Mic 串流選取器元件，來選取高品質的語音串流，並將其路由傳送至 Unity 的音訊系統。

* **在 [階層**] 面板中，選取 [**管理員**]。
* 在 [偵測 **器** ] 面板中，展開 [ **語音輸入處理常式**]。
* 在 [ **語音輸入處理常式**] 中，展開 [ **顯示 Underworld**]。
* 將 **函數** 變更為 **UnderworldBase. OnEnable**。

![關鍵字：顯示 Underworld](images/showunderworld.png)

* 展開 [ **隱藏 Underworld**]。
* 將 **函數** 變更為 **UnderworldBase. OnDisable**。

![關鍵字：隱藏 Underworld](images/hideunderworld.png)

#### <a name="build-and-deploy"></a>建置和部署

* 同樣地，在 Unity 中建立專案，並在 Visual Studio 中部署。

部署應用程式之後：

* 臉部 (牆壁、樓層、表格) ，然後說出 *"Show Underworld"*。

將會顯示 underworld，並隱藏所有其他的全像投影。 如果看不到 underworld，請確定您面對的是真實世界表面。

* Underworld 全像1計量中的方法，並開始討論。

現在音訊效果已套用至您的語音！

* 關閉 underworld，並注意效果不再適用的方式。
* 說「 *隱藏 Underworld* 」以隱藏 Underworld。

Underworld 將會隱藏，而先前隱藏的全像全像投影會再度出現。

## <a name="the-end"></a>結束

恭喜！ 您現在已完成 **MR 空間220：空間音效**。

聽聽全世界的音效，利用音效讓您的生活體驗！