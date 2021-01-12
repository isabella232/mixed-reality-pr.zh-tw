---
title: 初始化您的專案並部署您的第一個應用程式
description: 本課程說明如何為混合實境工具組 (MRTK) 設定 Unity 專案，以及如何將其部署到 HoloLens 2。
author: jessemcculloch
ms.author: v-vtieto
ms.date: 12/30/2020
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens, MRTK, 混合實境工具組, UWP, TextMeshPro,
ms.localizationpriority: high
ms.openlocfilehash: 2ce119e1dd18eacf02088d00e99fb70d06bf956e
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2021
ms.locfileid: "98008218"
---
# <a name="2-initializing-your-project-and-deploying-your-first-application"></a>2.初始化您的專案並部署您的第一個應用程式

在本教學課程中，您將了解如何建立新的 Unity 專案、將其設定為<a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank">混合實境工具組 (MRTK)</a>開發之用，以及匯入 MRTK。 您也將逐步了解如何設定和建置基本 Unity 場景，並將其從 Visual Studio 部署到 HoloLens 2。 將其部署到 HoloLens 2 之後，您應該會看到一個空間對應網格，其中涵蓋 HoloLens 所感知到的介面。 此外，您應該會看到雙手和手指上有用於手部追蹤的指標，還有用於留意應用程式效能的畫面播放速率計數器。

## <a name="objectives"></a>目標

* 了解如何設定 Unity 以用於 HoloLens 開發。
* 了解如何建置應用程式並部署至 HoloLens。
* 體驗 HoloLens 2 裝置上的空間對應網格、手部網格和畫面播放速率計數器。

## <a name="creating-the-unity-project"></a>建立 Unity 專案

1. 啟動 **Unity Hub**，選取 [專案] 索引標籤，然後按一下 [新增] 按鈕旁的 **向下箭號**：

![已反白顯示 [新增] 按鈕向下箭號的 Unity Hub](images/mr-learning-base/base-02-section1-step1-1.png)

2. 在下拉式功能表中，選取[必要條件](mr-learning-base-01.md#prerequisites)中所指定的 Unity 版本：

![選取 Unity 版本](images/mr-learning-base/base-02-section1-step1-2.png)

> [!TIP]
> 如果 Unity Hub 中無法使用特定的 Unity 版本，您可以從 Unity 的 <a href="https://unity3d.com/get-unity/download/archive" target="_blank">下載封存</a>起始安裝。

3. 在 [建立新專案] 視窗中，執行下列動作：

    * 確定 [範本] 設定為 [3D]。
    * 在 [專案名稱] 方塊中，為您的專案輸入適當的名稱 (例如「MRTK 教學課程」)。
    * 按一下 [位置] 旁的三個點按鈕，然後瀏覽至您要儲存專案的資料夾。

> [!CAUTION]
> 在 Windows 上建立時，有 255 個字元的 MAX_PATH 限制。 因此，您應該將 Unity 專案儲存在磁碟機的根目錄附近。

    * 按一下 [ **建立** ] 按鈕。 這會建立並啟動新的 Unity 專案。

![已填入 [建立新專案] 視窗的 Unity Hub](images/mr-learning-base/base-02-section1-step1-3.png)

狀態列會持續更新您的進度。

![Unity 進度列會持續更新您的「建立專案」狀態](images/mr-learning-base/base-02-section1-step1-4.png)

## <a name="switching-the-build-platform"></a>切換建置平台

1. 在功能表列上，選取 [檔案] > [建置設定...]。

![Unity [建置設定] 功能表路徑](images/mr-learning-base/base-02-section2-step1-1.png)

2. 在 [建置設定] 視窗中，選取 [通用 Windows 平台]，然後按一下 [切換平台] 按鈕：

![已選取 UWP 以從 [獨立式] 平台進行切換的 Unity [建置設定] 視窗](images/mr-learning-base/base-02-section2-step1-2.png)

3. 等候 Unity 完成平台切換，然後關閉 [建置設定] 視窗。

## <a name="importing-the-textmeshpro-essential-resources"></a>匯入 TextMeshPro 基本資源

MRTK 的 UI 元素需要 TextMeshPro 基本資源。 如果您不打算在專案中使用 MRTK 的 UI 元素，可以略過此步驟。

1. 在功能表列上，選取 [視窗] >  [TextMeshPro]  >  [匯入 TMP 基本資源]。

![Unity [匯入 TMP 基本資源] 功能表路徑](images/mr-learning-base/base-02-section3-step1-1.png)

2. 在 [匯入 Unity 套件] 視窗中，按一下 [全部] 按鈕以確保選取所有資產，然後按一下 [匯入] 按鈕來匯入資產：

![Unity [TMP 基本資源] 匯入視窗](images/mr-learning-base/base-02-section3-step1-2.png)

## <a name="importing-the-mixed-reality-toolkit"></a>匯入混合實境工具組

1. 下載 Unity 自訂套件：

    [Microsoft.MixedReality.Toolkit.Unity.Foundation.2.4.0.unitypackage](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.4.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.4.0.unitypackage)

2. 在功能表列上，選取 [資產] > [匯入套件] > [自訂套件...]。
3. 在 [匯入套件...] 對話方塊中，瀏覽至您剛下載套件的位置，加以選取，然後按一下 [開啟] 按鈕。
4. 在 [匯入 Unity 套件] 視窗中，按一下 [全部] 按鈕以確保選取所有資產，然後按一下 [匯入] 按鈕來匯入資產。

## <a name="selecting-mrtk-and-project-settings"></a>選取 MRTK 和專案設定

Unity 完成上一節中提到的匯入封裝後，應該會出現 [MRTK 專案配置器] 視窗。 如果沒有出現，請至 [混合實境工具組] > [公用程式] > [設定 Unity 專案] 手動開啟視窗。

![Unity [設定 Unity 專案] 功能表路徑](images/mr-learning-base/base-02-section5-step1-1.png)

1. 在 [MRTK 專案設定程式] 視窗中，展開 [修改設定] 區段，(如有需要) 然後確定已選取所有選項。

![顯示 [修改設定] 的 Unity MRTK 專案配置器視窗](images/mr-learning-base/base-02-section5-step1-2.png)

2. 若要套用設定，請按一下 [套用] 按鈕。

![MRTK 中的 [套用] 按鈕](images/mr-learning-base/apply.png)

> [!NOTE]
> 您之所以使用 Unity 的內建舊版 XR，而不是新的 XR 外掛程式系統，是因為新系統與本教學課程系列的[建議的 Unity 和 MRTK 版本](mr-learning-base-01.md#prerequisites)未能完全相容。 如果您看到任何關於內建 XR 即將淘汰的警告，您可予以忽略。

> [!TIP]
> 您可以選擇是否套用 MRTK 預設設定，但強烈建議您這麼做，因為這可協助您設定一些建議的 Unity 設定：
>
> * 啟用舊版 XR：為專案啟用 VR。
> * 設定單一階段執行個體化轉譯路徑：藉由在相同的繪製呼叫中為雙眼執行轉譯管線，來改善圖形效能。 若要深入了解本主題，您可以參閱 MRTK [效能](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html)文件中的[單一階段執行個體化轉譯](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html#single-pass-instanced-rendering)一節。
> * 設定預設空間感知層：建立名為「空間感知」的 Unity 圖層，並將 MRTK 設定為將此圖層用於空間感知網格。 若要深入了解 Unity 圖層，您可以參閱 Unity 的<a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">自訂您的工作區</a>文件。

3. 在功能表列上，選取 [編輯] > [專案設定...]。

4. 在 [專案設定] 視窗中，選取 [播放程式]，然後按一下 [XR 設定] 下拉式清單，然後選取 [支援虛擬實境] 旁的方塊：

![顯示支援虛擬實境的 Unity XR 設定](images/mr-learning-base/base-02-section5-step2-2.png)

這會匯入 Windows Mixed Reality SDK：

![顯示虛擬實境 SDK 的 Unity XR 設定](images/mr-learning-base/mixed-reality-sdk.png)

Unity 完成匯入 Windows Mixed Reality SDK 後，應該會再次出現 [MRTK 專案配置器] 視窗。 如果沒有出現，請選取 [混合實境工具組] > [公用程式] > [設定 Unity 專案] 加以開啟。

5. 在 [MRTK 專案配置器] 視窗中，按一下 [音訊空間定位器] 下拉式清單，然後選取 [MS HRTF 空間定位器]。

![顯示音訊空間定位器選項的專案設定](images/mr-learning-base/base-02-section5-step2-3.png)

6. 按一下 [套用]  按鈕。 這會關閉 [MRTK 專案設定程式] 視窗。

    > [!TIP]
    > 您可以選擇是否設定 [音訊空間定位器] 屬性，但這麼做可以改善專案中的音訊體驗。 如果您將此屬性設定為 [MS HRTF 空間定位器]，當 Unity 的 AudioSource.spatialize 屬性啟用時，便會使用此空間定位器外掛程式。 若要深入了解本主題，您可以參閱空間音訊教學課程。

7. 在 [專案設定] 視窗中，按一下 [深度格式] 下拉式清單，然後選取 [16 位元深度]：

    :::image type="content" source="images/mr-learning-base/base-02-section5-step2-4.png" alt-text="已選取 [16 位元深度] 的 Unity XR 設定。":::

    > [!TIP]
    > 您可以選擇是否將 [深度格式] 減少為 16 位元，但這麼做可協助改善專案中的圖形效能。 若要深入了解本主題，您可以參閱 MRTK [效能](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html)文件中的[深度緩衝區共用 (HoloLens)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html#depth-buffer-sharing-hololens) 一節。

8. 按一下 [發佈設定] 下拉式單，然後在 [套件名稱] 方塊中，輸入適當的名稱 (例如 "MRTK-Tutorials-Getting-Started")。

    :::image type="content" source="images/mr-learning-base/base-02-section5-step2-5.png" alt-text="已設定 [套件名稱] 的 Unity [發佈設定]。":::

    **套件名稱和產品名稱**

    - 「套件名稱」是應用程式的唯一識別碼。 您應該在部署應用程式之前建立此識別碼，以避免覆寫先前安裝的應用程式。
    - 「產品名稱」是 HoloLens 開始功能表中顯示的名稱。 若要在開發期間更容易找到應用程式，您可以在名稱前面加上底線，將其排序到頂端。

    :::image type="content" source="images/mr-learning-base/product-name.png" alt-text="已設定產品名稱的 Unity 專案設定。":::

9. 關閉 [專案設定] 視窗。

## <a name="creating-and-configuring-the-scene"></a>建立和設定場景

1. 在功能表列上，選取 [檔案] > [新場景]。
2. 若要將 MRTK 新增至場景，請在功能表上，選取 [混合實境工具組] > [新增至場景並設定...]。

    :::image type="content" source="images/mr-learning-base/base-02-section6-step1-2.png" alt-text="Unity [新增至場景並設定...] 功能表路徑。":::

3. 在 [階層] 視窗中，確定已選取 [MixedRealityToolkit]。

    :::image type="content" source="images/mr-learning-base/select-mixed-reality-toolkit.png" alt-text="確定已選取 MixedRealityTookit。":::

4. 在 [偵測器] 視窗的 [MixedRealityToolkit] 區段中，確認組態設定檔已設為 [DefaultMixedRealityToolkitConfigurationProfile]：

    :::image type="content" source="images/mr-learning-base/base-02-section6-step1-3.png" alt-text="已選取 DefaultMixedRealityTookitConfigurationProfile 的 Unity MixedRealityToolkit 元件。":::

    > [!IMPORTANT]
    > 通常，在開發 HoloLens 時會使用 DefaultHoloLens2ConfigurationProfile。 不過，在本教學課程中，您將使用 DefaultMixedRealityToolkitConfigurationProfile。 在下一個教學課程[設定 MRTK 設定檔](mr-learning-base-03.md)中，您將變更為 DefaultHoloLens2ConfigurationProfile。

5. 在功能表列上，選取 [檔案] > [另存新檔...]。
6. 在 [儲存場景] 對話方塊中，瀏覽至專案的 [場景] 資料夾。 在 [檔案檔案] 方塊中，為您的場景提供適當的名稱 (例如 "\_GettingStarted\_")，然後按一下 [儲存] 按鈕。

    :::image type="content" source="images/mr-learning-base/base-02-section6-step1-5.png" alt-text="Unity [儲存場景] 的 [儲存] 提示視窗。":::

## <a name="building-and-deploying-to-your-hololens-2"></a>建立及部署至您的 HoloLens 2

> 在建立到您的裝置之前，請確認下列事項：
- 您的裝置處於開發人員模式。
- 您的裝置與您的開發電腦配對。 如果沒有，您會在建置過程中，於 Visual Studio 中看到下列對話方塊：

![輸入配對裝置的 PIN](images/mr-learning-base/pin-request.png)

 若要深入了解這兩個步驟，請參閱[使用 Visual Studio 進行部署和偵錯](../../platform-capabilities-and-apis/using-visual-studio.md)。

1. 在功能表列上，選取 [檔案] > [建置設定...]。
2. 在 [建置設定] 視窗中，按一下 [新增開啟的場景] 按鈕，將您目前的場景新增至 [建置中的場景] 清單。

![將您目前的場景新增至「建置中的場景」清單](images/mr-learning-base/base-02-section7-step1-1.png)

3. 按一下 [組建] 按鈕。

    :::image type="content" source="images/mr-learning-base/build-button.png" alt-text="按一下 [組建] 按鈕。":::

4. 在 [建置通用 Windows 平台] 對話方塊中，選擇適當的位置來儲存您的組建 (例如，您可能想要在「MRTK 教學課程」資料夾中建立「組建」資料夾)。 建立新的資料夾並為其指定適當的名稱 (例如 "GettingStarted")，然後選取該資料夾，按一下 [選取資料夾] 按鈕來啟動建置程序。

    :::image type="content" source="images/mr-learning-base/base-02-section7-step1-2.png" alt-text="顯示您的組建資料夾的 [Unity 組建] 視窗。":::

    狀態列隨即出現，並持續更新您的建置進度。

    :::image type="content" source="images/mr-learning-base/base-02-section7-step1-3.png" alt-text="Unity 正在進行建置程序。":::

    > [!TIP]
    > 您也可以部署到 [HoloLens 模擬器](../../platform-capabilities-and-apis/using-the-hololens-emulator.md) 或為側載建立[應用程式套件](https://docs.microsoft.com/windows/uwp/packaging/packaging-uwp-apps)。

5. 當建置程序完成時，在 [檔案總管] 中，瀏覽至您儲存組建的位置，然後按兩下解決方案檔案以在 Visual Studio 中開啟：

    :::image type="content" source="images/mr-learning-base/base-02-section8-step1-1.png" alt-text="Windows 檔案總管，其中已選取新建立的 Visual Studio 解決方案檔案。":::

    > [!NOTE]
    > 如果 Visual Studio 要求您安裝新元件，請花一些時間確認是否已安裝所有必要元件，如同 **[安裝工具](../../install-the-tools.md)** 文件中所述。

6. 設定 Visual Studio 以便用於 HoloLens，請選取 [Master] 或 [Release] 設定、[ARM64] 架構，選取 [裝置] 作為目標。

    > [!TIP]
    > 如果您要部署至 HoloLens (第1代)，請選取 **x86** 架構。

    :::image type="content" source="images/mr-learning-base/base-02-section8-step1-2.png" alt-text="已針對要部署至 HoloLens 2 來設定 Visual Studio。":::

    > [!NOTE]
    > 若是 HoloLens，您通常會建立 ARM 架構。 不過，在 Visual Studio 中選取 ARM 作為建置架構時，Unity 2019.3 中的<a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank"><strong>已知問題</strong></a>會造成錯誤。 建議的解決方法是以 ARM64 建置。 如果無法這麼做，請移至 **編輯 > 專案設定 > 播放程式 > 其他設定** 並停用 **圖形作業**。

    > [!NOTE]
    > 如果您看不到 [裝置為目標] 選項，可能需要將 Visual Studio 解決方案的啟始專案從 IL2CPP 專案變更為 UWP 專案。 要這麼做，在方案總管中，以滑鼠右鍵按一下 YourProjectName (Universal Windows)，然後選取 [設定為啟動專案]。

7. 將 HoloLens 連接到您的電腦，然後執行下列其中一項動作：
- 若要建置應用程式、將其部署至您的 HoloLens，然後在不連結 Visual Studio 偵錯工具的情況下自動啟動，請在功能表列上選取 [偵錯] > [啟動但不偵錯]。

    :::image type="content" source="images/mr-learning-base/base-02-section8-step1-3.png" alt-text="Visual Studio [啟動但不偵錯] 功能表路徑。":::

- 若要建置應用程式並將其部署至 HoloLens，但不要自動啟動，請在功能表列上，選取 [建置] > [部署解決方案]。

    > [!NOTE]
    >您可能會注意到應用程式中的診斷分析工具，您可以使用 **Toggle Diagnostics** 語音命令開啟或關閉此工具。 建議您在開發期間儘量讓分析工具保持可見，以了解應用程式的變更何時會對效能產生影響。 例如，HoloLens 應用程式應該[持續以 60 FPS 執行](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md)。

## <a name="congratulations"></a>恭喜！

您現在已部署了第一個 HoloLens 應用程式。 當您隨處走動時，應該會看到空間對應網格涵蓋了所有 HoloLens 所感知到的表面。 此外，您應該會看到雙手和手指上有用於手部追蹤的指標，還有用於留意應用程式效能的畫面播放速率計數器。 這些功能只是 MRTK 所包含的幾個基本部分。 在接下來的教學課程中，您將會在場景中新增內容，以探索 HoloLens 和 MRTK 的功能。

> [!div class="nextstepaction"]
> [下一個教學課程：3.設定 MRTK 設定檔](mr-learning-base-03.md)
