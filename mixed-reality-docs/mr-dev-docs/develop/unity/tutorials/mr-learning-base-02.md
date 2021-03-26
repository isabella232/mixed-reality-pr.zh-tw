---
title: 初始化您的專案並部署您的第一個應用程式
description: 本課程說明如何為混合實境工具組 (MRTK) 設定 Unity 專案，以及如何將其部署到 HoloLens 2。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens, MRTK, 混合實境工具組, UWP, TextMeshPro,
ms.localizationpriority: high
ms.openlocfilehash: c80074ffec3e1f90d5dfe2ea2e64a379b59c5af6
ms.sourcegitcommit: ac315c1d35f2b9c431e79bc3f1212215301bb867
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105550458"
---
# <a name="2-initializing-your-project-and-deploying-your-first-application"></a>2.初始化您的專案並部署您的第一個應用程式

在本教學課程中，您將了解如何建立新的 Unity 專案、將其設定為<a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank">混合實境工具組 (MRTK)</a>開發之用，以及匯入 MRTK。 您也將逐步了解如何設定和建置基本 Unity 場景，並將其從 Visual Studio 部署到 HoloLens 2。 將其部署到 HoloLens 2 之後，您應該會看到一個空間對應網格，其中涵蓋 HoloLens 所感知到的介面。 此外，您應該會看到雙手和手指上有用於手部追蹤的指標，還有用於留意應用程式效能的畫面播放速率計數器。

![MRTK](../../../develop/images/Unity_MRTK_MRFT_Flow.png)


## <a name="objectives"></a>目標

* 了解如何設定 Unity 以用於 HoloLens 開發
* 了解如何建置應用程式並部署至 HoloLens
* 體驗 HoloLens 2 裝置上的空間對應網格、手部網格和畫面播放速率計數器

## <a name="creating-the-unity-project"></a>建立 Unity 專案

啟動 **Unity Hub**，選取 [專案] 索引標籤，然後按一下 [新增] 按鈕旁的 **向下箭號**：

![已醒目提示 [新增] 按鈕的 Unity Hub](images/mr-learning-base/base-02-section1-step1-1.png)

在下拉式清單中，選取 [必要條件](mr-learning-base-01.md#prerequisites)中所指定的 Unity **版本**：

![具有新版本選取器下拉式清單的 Unity Hub](images/mr-learning-base/base-02-section1-step1-2.png)

> [!TIP]
> 如果 Unity Hub 中無法使用特定的 Unity 版本，您可以從 Unity 的 <a href="https://unity3d.com/get-unity/download/archive" target="_blank">下載封存</a>起始安裝。

在 [建立新專案] 視窗中：

* 確定 [範本] 設定為 [3D]
* 輸入適當的 [專案名稱]，例如 MRTK Tutorials
* 選擇適當的 [位置] 來儲存您的專案，例如 D:\MixedRealityLearning
* 按一下 [建立] 按鈕，以建立並啟動新的 Unity 專案

![已填入 [建立新專案] 視窗的 Unity Hub](images/mr-learning-base/base-02-section1-step1-3.png)

> [!CAUTION]
> 在 Windows 上建立時，有 255 個字元的 MAX_PATH 限制。 因此，您應該將 Unity 專案儲存在磁碟機的根目錄附近。

等候 Unity 建立專案：

![Unity 正在建立新專案](images/mr-learning-base/base-02-section1-step1-4.png)

## <a name="switching-the-build-platform"></a>切換建置平台

在 Unity 功能表中，選取 [檔案] >  [組建設定...] 來開啟 [組建設定] 視窗：

![Unity [建置設定] 功能表路徑](images/mr-learning-base/base-02-section2-step1-1.png)

在 [組建設定] 視窗中，選取 [通用 Windows 平台]，然後按一下 [切換平台] 按鈕：

![已選取 UWP 以從 [獨立式] 平台進行切換的 Unity [建置設定] 視窗](images/mr-learning-base/base-02-section2-step1-2.png)

等候 Unity 完成平台的切換：

![Unity 正在切換平台](images/mr-learning-base/base-02-section2-step1-3.png)

當 Unity 完成平台切換之後，按一下紅色 **x** 圖示以關閉 [組建設定] 視窗：

![已醒目提示 [關閉] 圖示的 Unity 建置視窗](images/mr-learning-base/base-02-section2-step1-4.png)

## <a name="importing-the-textmeshpro-essential-resources"></a>匯入 TextMeshPro 基本資源

在 Unity 功能表中，選取 [視窗] >  [TextMeshPro]  >  [匯入 TMP 基本資源] 以開啟 [匯入 Unity 套件] 視窗：

![Unity [匯入 TMP 基本資源] 功能表路徑](images/mr-learning-base/base-02-section3-step1-1.png)

在 [匯入 Unity 套件] 視窗中，按一下 [全部] 按鈕以確保選取所有資產，然後按一下 [匯入] 按鈕來匯入資產：

![Unity [TMP 基本資源] 匯入視窗](images/mr-learning-base/base-02-section3-step1-2.png)

> [!TIP]
> MRTK 的 UI 元素需要 TextMeshPro 基本資源。 如果您不打算在專案中使用 MRTK 的 UI 元素，則可以略過此步驟。

## <a name="importing-the-mixed-reality-toolkit"></a>匯入混合實境工具組

若要將混合現實工具組匯入 Unity 專案中，您必須使用「 [混合現實」功能工具](//windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool) ，讓開發人員能夠探索、更新和新增混合現實功能套件至 unity 專案。 您可以依名稱或類別搜尋套件、查看其相依性，甚至在匯入之前查看專案資訊清單檔的建議變更。

請從 [Microsoft 下載中心](https://aka.ms/MRFeatureTool)下載最新版本的混合現實功能工具，下載完成後，請將檔案解壓縮，並將其儲存到您的桌面。

> [!NOTE]
> 在您可以執行混合現實功能工具之前，請先安裝[.net 5.0 運行](https://dotnet.microsoft.com/download/dotnet/5.0)時間

> [!NOTE]
> 混合現實功能工具目前只在 Windows 上執行，若為 MacOS，請依照此程式下載並匯入混合現實工具 [組至 unity](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html#1-get-the-latest-mrtk-unity-packages) 專案。

> [!NOTE]
> 您也可以從 [MRTK Github 的 [發行] 頁面](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases)手動下載 MRTK 套件。 使用 Unity 的資產匯入 MRTK 套件-> 匯入套件-> 自訂套件] 功能表。 


從下載的資料夾開啟可執行檔 **MixedRealityFeatureTool** ，以啟動「混合現實」功能工具。  

![開啟 MixedRealityFeatureTool](images/mr-learning-base/base-02-section4-step1-1.png)

開啟 **MixedRealityFeatureTool** 之後，請按一下 [開始] 以開始使用混合現實功能工具。

![MixedRealityFeatureTool](images/mr-learning-base/base-02-section4-step1-2.png)

您必須設定目標 unity 專案的位置以提供 **專案路徑**，按一下專案路徑旁的 **三個點** ，然後在 explorer 中流覽至您的專案資料夾，例如 _D:\MixedRealityLearning\MRTK 教學_ 課程。 按一下 [探索功能] 以進行下一個步驟。

![MixedRealityFeatureTool 專案路徑](images/mr-learning-base/base-02-section4-step1-2b.png)

功能會依類別目錄分組，讓您更容易找到這些專案，請按一下 [ **Mixed Reality 工具** 組] 下拉式清單，以尋找與混合現實工具組相關的套件。

![MixedRealityFeatureTool 視窗](images/mr-learning-base/base-02-section4-step1-3.png)

檢查 **Mixed Reality 工具組 Foundation**，然後按一下其旁邊的下拉式清單，以選取所需的 MRTK 版本，在此教學課程系列中，請選取 [ **2.5.3**]。 然後按一下 [ **取得功能** ] 按鈕，以下載選取的封裝。

![選取混合的現實基礎](images/mr-learning-base/base-02-section4-step1-4.png)

在 [匯 **入功能**] 視窗中會顯示選取的套件 **混合現實工具組 Foundation 2.5.3** ，以及其相依套件 **混合現實工具組標準資產 2.5.3** 。

> [!NOTE]
> 流覽 Unity 專案資料夾時顯示的對話方塊會包含 ' _ ' 作為檔案名。 檔案名必須有一個值，才能選取該資料夾。

接下來按一下 [ **驗證** ] 按鈕以驗證選取的封裝，您會看到 [偵測 **不到驗證問題** 的快顯視窗 **] 按一下 [確定]** 關閉快顯視窗，然後按一下 [匯 **入** ] 按鈕。

![驗證混合的現實基礎](images/mr-learning-base/base-02-section4-step1-5.png)

按一下 [ **核准** ] 按鈕，將 **Mixed Reality 工具** 組新增至專案。

![核准混合的現實基礎](images/mr-learning-base/base-02-section4-step1-6.png)

當您關閉 Mixed Reality 功能工具並返回 Unity 時，將會載入新的封裝。

## <a name="configuring-the-unity-project"></a>設定 Unity 專案

### <a name="1-apply-the-mrtk-project-configurator-settings"></a>1.套用 MRTK 專案配置器設定

Unity 完成上一節中提到的匯入封裝後，應該會出現 [MRTK 專案配置器] 視窗。 如果沒有出現，請至 [混合實境工具組] > [公用程式] > [設定 Unity 專案] 手動開啟視窗。

![Unity [設定 Unity 專案] 功能表路徑](images/mr-learning-base/base-02-section5-step1-1.png)

在 [MRTK 專案設定程式] 視窗中，展開 [修改設定] 區段，確定已勾選所有其他選項，然後按一下 [套用] 按鈕來套用設定：

![Unity [MRTK 專案設定程式] 視窗](images/mr-learning-base/base-02-section5-step1-2.png)

> [!TIP]
> 您可以選擇是否套用 MRTK 預設設定，但強烈建議您這麼做，因為這可協助您設定一些建議的 Unity 設定：

> * 設定單一階段執行個體化轉譯路徑：藉由在相同的繪製呼叫中為雙眼執行轉譯管線，來改善圖形效能。 若要深入了解本主題，您可以參閱 MRTK [效能](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/performance/perf-getting-started.md#single-pass-instanced-rendering)文件中的[單一階段執行個體化轉譯](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/performance/perf-getting-started.md#single-pass-instanced-rendering)一節。
> * 設定預設空間感知層：建立名為「空間感知」的 Unity 圖層，並將 MRTK 設定為將此圖層用於空間感知網格。 若要深入了解 Unity 圖層，您可以參閱 Unity 的<a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">自訂您的工作區</a>文件。

### <a name="2-configure-additional-project-settings"></a>2.設定其他專案設定

在 Unity 功能表中，選取 [編輯] >  [專案設定...] 來開啟 [專案設定] 視窗：

在 [專案設定] 視窗中，選取 [ **Player**  >  **XR 設定**]，然後勾選 [**支援虛擬實境**] 核取方塊。 這個程序需要一些時間。 核取 [ **支援虛擬事實** ] 之後，按一下 **+** 圖示，然後選取 [ **WINDOWS MIXED REALITY** 以新增 Windows Mixed Reality SDK：

![已選取新增 [Windows Mixed Reality] SDK 的 Unity XR 設定](images/mr-learning-base/base-02-section5-step2-4.png)

Unity 完成匯入 Windows Mixed Reality SDK 後，應該會再次出現 [MRTK 專案配置器] 視窗。 如果沒有，您可以從 Unity 功能表手動開啟它，方法是前往 **混合現實工具** 組  >  **公用程式**  >  **設定 Unity 專案**

在 [MRTK 專案設定] 視窗中，使用 **Audio 空間定位器** 下拉式清單選取 [MS HRTF 空間定位器]，然後按一下 [套用] 按鈕來套用設定：

![已選取 [新增 Windows Mixed Reality SDK] 選項的 Unity XR 設定](images/mr-learning-base/base-02-section5-step2-5.png)

> [!TIP]
>您可以選擇是否設定 [音訊空間定位器] 屬性，但這麼做可以改善專案中的音訊體驗。 如果您將此屬性設定為 [MS HRTF 空間定位器]，當 Unity 的 AudioSource.spatialize 屬性啟用時，便會使用此空間定位器外掛程式。 若要深入瞭解本主題，您可以參考  <a href="//windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank"> 空間音訊教學</a>課程。

在 [專案設定] 視窗中，選取 [播放程式] > [XR 設定]，然後使用 **深度格式** 下拉式清單選取 **16 位元深度**：

![Unity 啟用16深度](images/mr-learning-base/base-02-section5-step2-6.png)

> [!TIP]
> 您可以選擇是否將 [深度格式] 減少為 16 位元，但這麼做可協助改善專案中的圖形效能。 若要深入瞭解本主題，您可以參考 MRTK 的<a href="/windows/mixed-reality/mrtk-docs/performance/perf-getting-started.md#single-pass-instanced-rendering" target="_blank">效能</a>檔中的<a href="/windows/mixed-reality/mrtk-docs/performance/perf-getting-started.md#single-pass-instanced-rendering" target="_blank">深度緩衝區共用 (HoloLens) </a>一節。

在 [專案設定] 視窗中，選取 [播放程式] > [發佈設定]，然後在 **套件名稱** 欄位中輸入適當的名稱，例如 _MRTKTutorials-GettingStarted_：

![已設定 [套件名稱] 的 Unity [發佈設定]](images/mr-learning-base/base-02-section5-step2-7.png)

> [!NOTE]
> 「套件名稱」是應用程式的唯一識別碼。 您應該在部署應用程式之前變更此識別碼，以避免覆寫先前安裝的應用程式。

> [!TIP]
> 「產品名稱」是 HoloLens 開始功能表中顯示的名稱。 若要在開發期間更容易找到應用程式，請在名稱前面加上底線，將其排序到頂端。

## <a name="creating-and-configuring-the-scene"></a>建立和設定場景

在 Unity 功能表中，選取 [檔案] > [新增場景] 以建立新場景：

![Unity [新增場景] 功能表路徑](images/mr-learning-base/base-02-section6-step1-1.png)

在 Unity 功能表中，選取 [混合實境工具組] >  [新增至場景並設定...] 來將 MRTK 新增至目前的場景：

![Unity [新增至場景並設定...] 功能表路徑](images/mr-learning-base/base-02-section6-step1-2.png)

在 [階層] 視窗中選取 **MixedRealityToolkit** 物件後，在 [偵測器] 視窗中，驗證 **MixedRealityToolkit** 設定中的設定檔是否變更為 **DefaultMixedRealityToolkitConfigurationProfile**：

![已選取 DefaultMixedRealityTookitConfigurationProfile 的 Unity MixedRealityToolkit 元件](images/mr-learning-base/base-02-section6-step1-3.png)

在 Unity 功能表中，選取 [檔案] >  [另存新檔 ...] 以開啟 [儲存場景] 視窗：

![Unity [另存新檔...] 功能表路徑](images/mr-learning-base/base-02-section6-step1-4.png)

在 [儲存場景] 視窗中，瀏覽至專案的 **Scenes** 資料夾，為您的場景取一個適當的名稱，例如 _GettingStarted_，然後按一下 [儲存] 按鈕以儲存場景：

![Unity [儲存場景] 的 [儲存] 提示視窗](images/mr-learning-base/base-02-section6-step1-5.png)

## <a name="building-your-application-to-your-hololens-2"></a>在您的 HoloLens 2 上建置應用程式

### <a name="1-build-the-unity-project"></a>1.組建 Unity 專案

在 Unity 功能表中，選取 [檔案] >  [組建設定...] 來開啟 [組建設定] 視窗。

在 [組建設定] 視窗中，按一下 [新增開啟的場景] 按鈕，將您目前的場景新增至 [組建中的場景] 清單，然後按一下 [組建] 按鈕以開啟 [組建通用 Windows 平台] 視窗：

![已選取 UWP 的 Unity [建置設定] 視窗](images/mr-learning-base/base-02-section7-step1-1.png)

在 [組建通用 Windows 平台] 視窗中，選擇適當的位置來儲存您的組建，例如 D:\MixedRealityLearning\Builds，建立新的資料夾並指定適當的名稱，例如 GettingStarted，然後按一下 [選取資料夾] 按鈕開始組建程序：

![具有 [選取資料夾] 提示視窗的 Unity [建置設定] 視窗](images/mr-learning-base/base-02-section7-step1-2.png)

等候 Unity 完成組建程序：

![Unity 正在進行建置程序](images/mr-learning-base/base-02-section7-step1-3.png)

### <a name="2-build-and-deploy-the-application"></a>2.組建和部署應用程式

當建置程序完成時，Unity 會提示 Windows 檔案總管開啟您儲存組建的位置。 瀏覽該資料夾，按兩下解決方案的檔案即可在 Visual Studio 中開啟該檔案：

![Windows 檔案總管，其中已選取新建立的 Visual Studio 解決方案](images/mr-learning-base/base-02-section8-step1-1.png)

> [!NOTE]
> 如果 Visual Studio 要求您安裝新元件，請花一些時間確認是否已安裝所有必要元件，如同 **[安裝工具](../../install-the-tools.md)** 文件中所述。

設定 Visual Studio 以便用於 HoloLens，請選取 [Master] 或 [Release] 設定、[ARM64] 架構，選取 [裝置] 作為目標：

> [!NOTE]
> 根據您的部署方法選擇您的目標。

![已針對要部署至 HoloLens 2 來設定 Visual Studio](images/mr-learning-base/base-02-section8-step1-2.png)

> [!TIP]
> 如果您要部署至 HoloLens (第1代)，請選取 **x86** 架構。

> [!NOTE]
> 若是 HoloLens，您通常會建立 ARM 架構。 不過，在 Visual Studio 中選取 ARM 作為建置架構時，Unity 2019.3 中的<a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank"><strong>已知問題</strong></a>會造成錯誤。 建議的解決方法是以 ARM64 建置。 如果無法這麼做，請移至 **編輯 > 專案設定 > 播放程式 > 其他設定** 並停用 **圖形作業**。

> [!NOTE]
> 如果您看不到 [裝置為目標] 選項，可能需要將 Visual Studio 解決方案的啟始專案從 IL2CPP 專案變更為 UWP 專案。 要這麼做，在方案總管中，以滑鼠右鍵按一下 YourProjectName (Universal Windows) 並選取 [設定為啟動專案]。

使用 USB 纜線將 HoloLens 連接到您的電腦，**然後選取 [**  >  **啟動但不進行調試** 程式]，以建立並部署至您的裝置：

![Visual Studio [啟動但不進行偵錯] 功能表路徑](images/mr-learning-base/base-02-section8-step1-3.png)

> [!IMPORTANT]
> 在組建您的裝置之前，裝置必須處於「開發人員模式」，並與開發電腦配對。 請遵循[這些指示](../../platform-capabilities-and-apis/using-visual-studio.md)來完成這兩個步驟。

> [!TIP]
> 您也可以部署到 [HoloLens 模擬器](../../platform-capabilities-and-apis/using-the-hololens-emulator.md) 或為側載建立[應用程式套件](/windows/uwp/packaging/packaging-uwp-apps)。

使用 [啟動但不進行偵測] 會自動啟動您裝置上的應用程式，而不會附加 Visual Studio 偵錯工具。

若要在不自動啟動應用程式的情況下部署裝置，選取 [組建] > [部署解決方案]。

> [!NOTE]
>您可能會注意到應用程式中的診斷分析工具，您可以使用 **Toggle Diagnostics** 語音命令開啟或關閉此工具。 建議您在開發期間儘量讓分析工具保持可見，以了解應用程式的變更何時會對效能產生影響。 例如，HoloLens 應用程式應該[持續以 60 FPS 執行](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md)。

## <a name="congratulations"></a>恭喜！

您現在已部署了第一個 HoloLens 應用程式。 當您隨處走動時，應該會看到空間對應網格涵蓋了所有 HoloLens 所感知到的表面。 此外，您應該會看到雙手和手指上有用於手部追蹤的指標，還有用於留意應用程式效能的畫面播放速率計數器。 這些功能只是 MRTK 所包含的幾個基本部分。 在接下來的教學課程中，您將會在場景中新增內容，以探索 HoloLens 和 MRTK 的功能。

> [!div class="nextstepaction"]
> [下一個教學課程：3.設定 MRTK 設定檔](mr-learning-base-03.md)