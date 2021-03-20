---
title: EyeTracking_BasicSetup
description: 如何在 MRTK 中設定眼睛追蹤
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、眼睛追蹤、
ms.openlocfilehash: 0a603ca293d66fea51b8fc22615f99324edeaca6
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104693135"
---
# <a name="getting-started-with-eye-tracking-in-mrtk"></a>開始在 MRTK 中使用眼睛追蹤

本頁面涵蓋如何設定您的 Unity MRTK 場景，以在應用程式中使用眼睛追蹤。
以下假設您是以全新的新場景開始。
或者，您可以查看我們已設定的 [MRTK 眼睛追蹤範例](../../example-scenes/eye-tracking-examples-overview.md) ，其中包含可供您直接建立的大量絕佳範例。

## <a name="eye-tracking-requirements-checklist"></a>目視追蹤需求檢查清單

若要讓眼睛追蹤正常運作，必須符合下列需求。
如果您不熟悉 HoloLens 2 上的眼睛追蹤，以及如何在 MRTK 中設定眼睛追蹤，請別擔心！
我們將詳細說明如何解決這些問題。

1. 您必須將「 _眼睛眼 Data Provider_ 」新增至輸入系統。 這會從平臺提供眼睛追蹤資料。
2. 應用程式資訊清單中必須啟用 _' GazeInput '_ 功能。
   **這項功能可以在 Unity 2019 中設定，但在 Unity 2018 和更早版本中，這項功能僅適用于 Visual Studio 以及透過 MRTK build tool**
3. HoloLens **必須** 針對目前的使用者進行眼睛校正。 請查看我們 [的範例，以偵測使用者是否已校正](eye-tracking-is-user-calibrated.md)。

### <a name="a-note-on-the-gazeinput-capability"></a>GazeInput 功能的注意事項

MRTK 提供的組建工具 (，也就是混合現實工具組-> 公用程式-> 組建視窗) 可以自動為您啟用 GazeInput 功能。 若要這樣做，您必須確定已核取 [Appx 組建選項] 索引標籤上的 [注視輸入功能]：

![MRTK Build Tools](../../images/eye-tracking/mrtk_et_buildsetup.png)

此工具會在 Unity 組建完成後找到 AppX 資訊清單，並以手動方式新增 GazeInput 功能。
**在 unity 2019 之前，使用 unity 的內建組建視窗時，此工具不會處於使用中狀態， (也就是** > 的組建設定) 。

在 Unity 2019 之前，使用 Unity 的 [組建] 視窗時，必須在 Unity 組建之後以手動方式新增功能，如下所示：

1. 開啟您已編譯的 Visual Studio 專案，然後在您的方案中開啟 _' package.appxmanifest '_ 。
2. 請務必勾選 [_功能_] 下的 [ _GazeInput_ ] 核取方塊。 如果您沒有看到「 _GazeInput_ 」功能，請確認您的系統符合 [使用 MRTK](https://docs.microsoft.com/windows/mixed-reality/develop/install-the-tools) (的必要條件，特別是 Windows SDK 版本) 。

_請注意：_ 如果您建立的是新的組建資料夾，就只需要這麼做。
這表示，如果您已經建立 Unity 專案，並在之前設定 package.appxmanifest，而且現在將目標設為相同的資料夾，您就不需要重新套用變更。

## <a name="setting-up-eye-tracking-step-by-step"></a>逐步設定眼睛追蹤

### <a name="setting-up-the-scene"></a>設定場景

只要按一下 [ _Mixed Reality 工具組-> 設定 ..._ ]，即可設定 _MixedRealityToolkit_ 在功能表列中。

![MRTK 設定](../../images/eye-tracking/mrtk_setup_configure.jpg)

### <a name="setting-up-the-mrtk-profiles-required-for-eye-tracking"></a>設定眼睛追蹤所需的 MRTK 設定檔

設定 MRTK 場景之後，系統會要求您選擇 MRTK 的設定檔。
您可以直接選取 [ _DefaultMixedRealityToolkitConfigurationProfile_ ]，然後選取 [ _複製 & 自訂_ ] 選項。

![MRTK 設定檔](../../images/eye-tracking/mrtk_setup_configprofile.jpg)

### <a name="create-an-eye-gaze-data-provider"></a>建立「眼睛注視資料提供者」

- 按一下 MRTK 設定檔中的 [ _輸入_ ] 索引標籤。
- 若要編輯預設值 ( [ _DefaultMixedRealityInputSystemProfile_ ] ) ，請按一下其旁邊的 [ _複製_ ] 按鈕。 [ _複製設定檔_ ] 功能表隨即出現。 只要按一下該功能表底部的 [ _複製_ ] 即可。
- 按兩下新的輸入設定檔，展開 [ _輸入資料提供者_]，然後選取 [ _+ 新增 Data Provider_]。
- 建立新的資料提供者：
  - 在 [**類型**] 下，選取 [ _MixedReality] WindowsMixedReality。輸入 '_  ->  _' WindowsMixedRealityEyeGazeDataProvider '_
  - 針對 **平臺 (s)** 選取 [ _Windows 通用_]。

![MRTK 資料提供者](../../images/eye-tracking/mrtk_setup_eyes_dataprovider.jpg)

### <a name="simulating-eye-tracking-in-the-unity-editor"></a>在 Unity 編輯器中模擬目視追蹤

您可以在 Unity 編輯器中模擬眼睛追蹤輸入，以確保在將應用程式部署到您的 HoloLens 2 之前，已正確觸發事件。
您只需使用相機的位置做為眼睛眼睛，並將攝影機的正向向量視為眼睛的方向，即可模擬眼睛信號。
雖然這很適合用於初始測試，但請注意，它不是快速眼移動的理想仿造。
為了達到此效果，最好是確保經常測試 HoloLens 2 上的眼睛型互動。

1. **啟用模擬的眼睛追蹤**：
    - 按一下 MRTK 設定檔中的 [ _輸入_ ] 索引標籤。
    - 從該處流覽至「_輸入資料提供者_」  ->  _的「輸入模擬服務_」。
    - 複製 _' DefaultMixedRealityInputSimpulationProfile '_ 以進行變更。
    - 選取 [ _模擬眼睛位置_ ] 核取方塊。

    ![MRTK 眼睛模擬](../../images/eye-tracking/mrtk_setup_eyes_simulate.jpg)

2. **停用預設** 的前端資料指標：一般而言，建議您避免顯示眼睛指標，或是絕對需要使其變 _得非常_ 微妙。
建議您根據預設，隱藏附加至 MRTK 注視指標設定檔的預設標頭注視游標。
    - 流覽至您的 MRTK 設定設定檔-> _' Input '_  ->  _' 指標 '_
    - 複製 _' DefaultMixedRealityInputPointerProfile '_ 以進行變更。
    - 在 [ _指標設定_] 的頂端，您應該將不可見的資料指標預製專案指派給 _' GazeCursor '_。 若要這麼做，您可以從 MRTK Foundation 中選取 [ _EyeGazeCursor_ ] 預製專案。

### <a name="enabling-eye-based-gaze-in-the-gaze-provider"></a>在注視提供者中啟用以眼睛為基礎的注視

在 HoloLens v1 中，用來做為主要指標技術的標頭。
雖然仍可透過連接到 [相機](https://docs.unity3d.com/ScriptReference/Camera.html)的 MRTK 中的 _GazeProvider_ 來使用前端，但您可以改為勾選輸入指標設定檔的眼睛設定中的 [ _IsEyeTrackingEnabled_ ] 核取方塊。

>[!NOTE]
>藉由變更 _' GazeProvider '_ 的 _' IsEyeTrackingEnabled '_ 屬性，開發人員可以在程式碼中切換眼睛和前端。  

>[!IMPORTANT]
>如果不符合任何眼睛追蹤需求，應用程式將會自動切換回以前端為基礎的注視。

### <a name="accessing-eye-gaze-data"></a>存取眼睛資料

現在您的場景已設定為使用眼睛追蹤，讓我們看看如何在您的腳本中進行存取：透過 EyeGazeProvider 和[支援的目標選取專案](eye-tracking-target-selection.md)來存取[眼睛追蹤資料](eye-tracking-eye-gaze-provider.md)。

### <a name="testing-your-unity-app-on-a-hololens-2"></a>在 HoloLens 2 上測試 Unity 應用程式

使用眼睛追蹤建立您的應用程式應該類似于編譯其他 HoloLens 2 MRTK 應用程式的方式。 請確定您已依照上述 [*GazeInput 功能*](#a-note-on-the-gazeinput-capability)一節中所述的方式啟用「*注視輸入*」功能。

#### <a name="eye-calibration"></a>眼睛校正

最後，請別忘了在 HoloLens 2 上執行眼睛校正。
如果未校正使用者，則眼睛追蹤系統將不會傳回任何輸入。
取得校正最簡單的方式，就是向上復原面板和向下切換。
系統通知應該會出現，歡迎您成為新的使用者，並要求您完成眼睛校正。
或者，您可以在 [系統設定：設定 > 系統 > 校正] 中找到視覺校正 > 執行眼睛校正。

#### <a name="eye-tracking-permission"></a>目視追蹤許可權

當您第一次在 HoloLens 2 上啟動應用程式時，會出現提示，要求使用者提供使用眼睛追蹤的許可權。
如果未顯示，則這通常表示未設定「 _GazeInput_ 」功能。

許可權提示出現一次之後，就不會再自動顯示。
如果您「已 _拒絕眼追蹤」許可權_，您可以在 [設定-> 隱私權-> 應用程式] 中重設此項。

---

這應該可讓您開始在 MRTK Unity 應用程式中使用眼睛追蹤。
別忘了看看 [我們的 MRTK 眼睛追蹤教學課程和範例，](../../example-scenes/eye-tracking-examples-overview.md) 示範如何使用眼睛追蹤輸入，並以便利的方式提供可在專案中重複使用的腳本。

---
[回到「MixedRealityToolkit 中的眼睛追蹤」](eye-tracking-main.md)
