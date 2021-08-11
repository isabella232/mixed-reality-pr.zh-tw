---
title: 初始化您的專案並部署您的第一個應用程式
description: 本課程說明如何為混合實境工具組 (MRTK) 設定 Unity 專案，以及如何將其部署到 HoloLens 2。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens, MRTK, 混合實境工具組, UWP, TextMeshPro,
ms.localizationpriority: high
ms.openlocfilehash: cab10789bc7ab86a4090a0db46e5445b728c7c8ad2dd904cba530e81f1bab18e
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2021
ms.locfileid: "115201179"
---
# <a name="2-initializing-your-project-and-deploying-your-first-application"></a>2.初始化您的專案並部署您的第一個應用程式

在本教學課程中，您將了解如何建立新的 Unity 專案、將其設定為混合實境工具組 (MRTK)開發之用，以及匯入 MRTK。 您也將逐步了解如何設定和建置基本 Unity 場景，並將其從 Visual Studio 部署到 HoloLens 2。 將其部署到 HoloLens 2 之後，您應該會看到一個空間對應網格，其中涵蓋 HoloLens 所感知到的介面。 此外，您應該會看到雙手和手指上有用於手部追蹤的指標，還有用於留意應用程式效能的畫面播放速率計數器。

## <a name="objectives"></a>目標

* 了解如何設定 Unity 以用於 HoloLens 開發
* 了解如何建置應用程式並部署至 HoloLens
* 體驗 HoloLens 2 裝置上的空間對應網格、手部網格和畫面播放速率計數器

### <a name="steps-overview"></a>步驟總覽
:::row:::
    :::column:::
       ![概述步驟 1 ](images/mr-learning-base/base-02-overview-step1.png) **1。建立新的 Unity 專案**
    :::column-end:::
    :::column:::
       ![[總覽] 步驟 2 ](images/mr-learning-base/base-02-overview-step2.png) **。將 MRTK 匯入專案**
    :::column-end:::
    :::column:::
       ![概述步驟 3 ](images/mr-learning-base/base-02-overview-step3.png) **：使用 MRTK 設定新場景**
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::
       ![概述步驟 4 ](images/mr-learning-base/base-02-overview-step4.png) **。建立 Unity Project**
    :::column-end:::
    :::column:::
       ![概述步驟 5 ](images/mr-learning-base/base-02-overview-step5.png) **：建立 UWP Project**
    :::column-end:::
    :::column:::
       ![總覽步驟 6 ](images/mr-learning-base/base-02-overview-step6.png) **：在裝置上執行 Project**
    :::column-end:::
:::row-end:::

## <a name="creating-the-unity-project"></a>建立 Unity 專案

啟動 **Unity Hub**，選取 [專案] 索引標籤，然後按一下 [新增] 按鈕旁的 **向下箭號**：

<img src="images/mr-learning-base/base-02-section1-step1-1.png" width="650px" alt="Unity Hub with New button highlighted">

在下拉式清單中，選取 [必要條件](mr-learning-base-01.md#prerequisites)中所指定的 Unity **版本**：

<img src="images/mr-learning-base/base-02-section1-step1-2.png" width="650px" alt="Unity Hub with NEW version selector dropdown">


> [!TIP]
> 如果 Unity Hub 中無法使用特定的 Unity 版本，您可以從 Unity 的 <a href="https://unity3d.com/get-unity/download/archive" target="_blank">下載封存</a>起始安裝。

在 [建立新專案] 視窗中：

* 確定 [範本] 設定為 [3D]
* 輸入適當的 [專案名稱]，例如 MRTK Tutorials
* 選擇適當的 [位置] 來儲存您的專案，例如 D:\MixedRealityLearning
* 按一下 [建立] 按鈕，以建立並啟動新的 Unity 專案

<img src="images/mr-learning-base/base-02-section1-step1-3.png" width="650px" alt="Unity Hub with Create a new project window filled out">

> [!CAUTION]
> 在 Windows 上建立時，有 255 個字元的 MAX_PATH 限制。 因此，您應該將 Unity 專案儲存在磁碟機的根目錄附近。

等候 Unity 建立專案：

<img src="images/mr-learning-base/base-02-section1-step1-4.png" width="650px" alt="Unity create new project in progress">

## <a name="switching-the-build-platform"></a>切換建置平台

在 Unity 功能表中，選取 [檔案] >  [組建設定...] 來開啟 [組建設定] 視窗：

![Unity [建置設定] 功能表路徑](images/mr-learning-base/base-02-section2-step1-1.png)

在 [組建設定] 視窗中，選取 **通用 Windows 平臺** 和：

1. 將 **目標裝置** 設定為 **HoloLens**
2. 將 **架構** 設定為 **ARM 64** 
3. 將 [組建類型] 設定為 [D3D 專案]
4. 將 **目標 SDK 版本** 設為 **最新安裝**
5. 將 **最低平臺版本** 設定為 **10.0.1024.0**
6. 將 **Visual Studio 版本** 設為 **最新安裝**
7. 設定 **組建並在** **USB 裝置** 上執行
8. 將 **組建** 設定設為 **發行** ，因為 Debug 有已知的效能問題
9. 按一下 [切換平臺] 按鈕

![已設定通用 Windows 平臺設定的 Unity 組建設定](images/mr-learning-base/base-02-section2-step1-2-openxr.png)

等候 Unity 完成平台的切換：

![Unity 正在切換平台](images/mr-learning-base/base-02-section2-step1-3-openxr.png)

當 Unity 完成切換平臺時，請按一下 **x** 圖示以關閉組建設定視窗。

## <a name="importing-the-mixed-reality-toolkit-and-configuring-the-unity-project"></a>匯入混合現實工具組和設定 Unity 專案

若要將 mixed reality 工具組匯入 unity Project 您必須使用[mixed reality 功能工具](../welcome-to-mr-feature-tool.md)，讓開發人員能夠探索、更新和新增混合現實功能套件至 unity 專案。 您可以依名稱或類別搜尋套件、查看其相依性，甚至在匯入之前查看專案資訊清單檔的建議變更。

請從 [Microsoft 下載中心](https://aka.ms/MRFeatureTool)下載最新版本的混合現實功能工具，下載完成後，請將檔案解壓縮，並將其儲存到您的桌面。

> [!NOTE]
> 在您可以執行混合現實功能工具之前，請先安裝[.net 5.0 運行](https://dotnet.microsoft.com/download/dotnet/thank-you/runtime-desktop-5.0.7-windows-x64-installer)時間

從下載的資料夾開啟可執行檔 **MixedRealityFeatureTool** ，以啟動「混合現實」功能工具。  


<img src="images/mr-learning-base/base-02-section4-step1-1.png" width="750px" alt="Opening MixedRealityFeatureTool">

[!INCLUDE[](includes/importing-mrtk.md)]

## <a name="creating-the-scene-and-configuring-mrtk"></a>建立場景並設定 MRTK

在 Unity 功能表中，選取 [ **File**  >  **New 場景**：

![Unity [新增場景] 功能表路徑](images/mr-learning-base/base-02-section6-step1-1.png)

在 [ **新場景** ] 視窗中，選取 [ **基本 (內建)** ，然後按一下 [ **建立** ] 以建立新場景：

![Unity 新場景視窗](images/mr-learning-base/base-02-section6-step1-1-newscene.png)

> [!NOTE]
> 上述螢幕擷取畫面是來自 Unity 2020 版，如果您在按一下 [ **建立** ] 時使用 unity 2019，則會建立新的空場景。

在 Unity 功能表中，選取 [**混合現實**  >  **工具** 組  >  **新增至場景]，並設定 ...** 將 MRTK 新增至您目前的場景：

![Unity [新增至場景並設定...] 功能表路徑](images/mr-learning-base/base-02-section6-step1-2.png)

在 [階層] 視窗中選取 **MixedRealityToolkit** 物件後，在 [偵測器] 視窗中，驗證 **MixedRealityToolkit** 設定中的設定檔是否變更為 **DefaultMixedRealityToolkitConfigurationProfile**：

![已選取 DefaultMixedRealityTookitConfigurationProfile 的 Unity MixedRealityToolkit 元件](images/mr-learning-base/base-02-section6-step1-3.png)

在 Unity 功能表中，選取 [檔案] >  [另存新檔 ...] 以開啟 [儲存場景] 視窗：

![Unity [另存新檔...] 功能表路徑](images/mr-learning-base/base-02-section6-step1-4.png)

將您專案中的場景儲存在 **資產**  >  **幕後**。

![Unity [儲存場景] 的 [儲存] 提示視窗](images/mr-learning-base/base-02-section6-step1-5.png)

## <a name="adding-hand-interaction-to-an-object"></a>將手互動新增至物件

在 Unity 功能表中，選取 [ **GameObject**  >  **3d 物件**  >  **Cube** ]，將 Cube 物件加入場景中。

![將 cube 加入場景](images/mr-learning-base/base-02-section8-step1-1.png)

按一下 [階層] 視窗中的 **Cube** 物件，然後在 [偵測器] 視窗中設定其 **轉換** 元件，如下所示

* **Position**： X = 0，Y =-0.1，Z = 0。5
* **旋轉**：X = 0、Y = 0、Z = 0
* **Scale**： X = 0.1、Y = 0.1、Z = 0。1

1個 Unity 單位是1個計量。 我們已將 cube 的大小更新為 10x10x10 cm，從耳機位置的50cm 放置 (0，0，0) 。 10cm，以熟悉互動。 

如果您使用預設小數位數 (1，1，1) ，cube 將會太大。 如果您使用預設位置 (0、0、0) ，cube 將放置在與耳機相同的位置，而且您將無法看到它，直到您向前移動為止。

![調整轉換資訊](images/mr-learning-base/base-02-section8-step1-1b.png)

若要將焦點放在場景中的物件上，您可以按兩下 **Cube** 物件，然後再稍微放大。 或者，您可以使用 F 鍵來縮放物件，並將焦點放在物件上。

若要與追蹤的手互動及抓取物件，物件必須有：
 * 碰撞器元件（例如方塊 **碰撞** 器） (Unity 的 cube 預設已經有方塊碰撞器) 
 * **Object Manipulator (指令碼)** 元件
 * **NearInteractionGrabbable (腳本)** 元件

MRTK 的 **ObjectManipulator** 腳本會使用一或兩個手來讓物件可移動、可擴充和 rotatable。 此指令碼支援直接操作輸入模型，因為指令碼可讓使用者用手直接碰觸全像投影。

當 **Cube** 仍在 [階層] 視窗中選取時，在 [偵測器] 視窗中，按一下 [ **加入元件** ] 按鈕，然後搜尋並選取 [ **物件** 操作工具腳本]，將物件操作工具腳本加入 Cube 物件中。

![將物件 manupulator 加入至 cube](images/mr-learning-base/base-02-section8-step1-2.PNG)

重複相同的步驟，將 **接近互動的 Grabbable 腳本** 新增至 cube

![將近乎互動的 Grabable 新增至 cube](images/mr-learning-base/base-02-section8-step1-3.PNG)

> [!NOTE]
> 當您加入物件操作工具 (腳本時) ，在此情況下，會自動加入條件約束管理員 (腳本) ，因為物件操作工具 (腳本) 相依于它。

## <a name="testing-your-application-in-unity-editor-with-mrtk-input-simulation"></a>使用 MRTK 輸入模擬在 Unity 編輯器中測試您的應用程式

使用 MRTK 的輸入模擬，您可以在 Unity 編輯器中測試各種類型的互動，而不需要建立及部署到裝置。 這可讓您快速地在設計和開發程式中反復查看您的想法。 使用鍵盤和滑鼠組合來控制模擬的輸入。

按一下 [播放] 按鈕，然後輸入播放模式。 按住 **左 Shift** 鍵或 **空格鍵** ，讓控制器 (模擬的手) ，滑鼠移動會移動控制器，也可以使用滑鼠滾輪移至或靠近相機。 指標位於 Cube 上時，按住 **滑鼠** 左鍵以抓取 cube 物件。

* 按 **W、A、S、D、Q、E** 鍵以移動相機。
* 按住滑鼠 **右鍵** ，並將滑鼠移至 [四處尋找]。
* 若要啟動模擬的手，請按 **空格鍵 (右手)** 或 **左 Shift 鍵 (左邊)**
* 若要讓模擬手保持在視野中，請按 **T** 或 **Y** 鍵
* 若要旋轉模擬的手，請按住 **Ctrl** 鍵並移動滑鼠

![遊戲模式](images/mr-learning-base/base-02-section8-step1-4.gif)


## <a name="building-your-application-to-your-hololens-2"></a>在您的 HoloLens 2 上建置應用程式

### <a name="1-build-the-unity-project"></a>1.組建 Unity 專案

在 Unity 功能表中，選取 [檔案] >  [組建設定...] 來開啟 [組建設定] 視窗。

在 [組建設定] 視窗中，按一下 [新增開啟的場景] 按鈕，將您目前的場景新增至 [組建中的場景] 清單，然後按一下 [組建] 按鈕以開啟 [組建通用 Windows 平台] 視窗：

![已選取 UWP 的 Unity [建置設定] 視窗](images/mr-learning-base/base-02-section9-step1-1.png)

在 [組建通用 Windows 平台] 視窗中，選擇適當的位置來儲存您的組建，例如 D:\MixedRealityLearning\Builds，建立新的資料夾並指定適當的名稱，例如 GettingStarted，然後按一下 [選取資料夾] 按鈕開始組建程序：

![具有 [選取資料夾] 提示視窗的 Unity [建置設定] 視窗](images/mr-learning-base/base-02-section9-step1-2.png)

等候 Unity 完成組建程序：

![Unity 正在進行建置程序](images/mr-learning-base/base-02-section9-step1-3.png)

### <a name="2-build-and-deploy-the-application"></a>2.組建和部署應用程式

當建置程序完成時，Unity 會提示 Windows 檔案總管開啟您儲存組建的位置。 瀏覽該資料夾，按兩下解決方案的檔案即可在 Visual Studio 中開啟該檔案：

![Windows 檔案總管，其中已選取新建立的 Visual Studio 解決方案](images/mr-learning-base/base-02-section10-step1-1.png)

> [!NOTE]
> 如果 Visual Studio 要求您安裝新元件，請花一些時間確認是否已安裝所有必要元件，如同 **[安裝工具](../../install-the-tools.md)** 文件中所述。

設定 Visual Studio 以便用於 HoloLens，請選取 [Master] 或 [Release] 設定、[ARM64] 架構，選取 [裝置] 作為目標：

![已針對要部署至 HoloLens 2 來設定 Visual Studio](images/mr-learning-base/base-02-section10-step1-2.png)

> [!TIP]
> 如果您要部署至 HoloLens (第1代)，請選取 **x86** 架構。

> [!NOTE]
> 若是 HoloLens，您通常會建立 ARM 架構。 不過，在 Visual Studio 中選取 ARM 作為建置架構時，Unity 2019.3 中的<a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank"><strong>已知問題</strong></a>會造成錯誤。 建議的解決方法是以 ARM64 建置。 如果無法這麼做，請移至 **編輯 > 專案設定 > 播放程式 > 其他設定** 並停用 **圖形作業**。

> [!NOTE]
> 如果您看不到 [裝置為目標] 選項，可能需要將 Visual Studio 解決方案的啟始專案從 IL2CPP 專案變更為 UWP 專案。 要這麼做，在方案總管中，以滑鼠右鍵按一下 YourProjectName (Universal Windows) 並選取 [設定為啟動專案]。

將 HoloLens 與電腦連線，然後選取 [偵錯] > [啟動但不進行偵錯]，以建置並部署至您的裝置：

![Visual Studio [啟動但不進行偵錯] 功能表路徑](images/mr-learning-base/base-02-section10-step1-3.png)

> [!IMPORTANT]
> 在組建您的裝置之前，裝置必須處於「開發人員模式」，並與開發電腦配對。 請遵循[這些指示](../../platform-capabilities-and-apis/using-visual-studio.md)來完成這兩個步驟。

> [!TIP]
> 您也可以部署到 [HoloLens 模擬器](../../platform-capabilities-and-apis/using-the-hololens-emulator.md) 或為側載建立[應用程式套件](/windows/uwp/packaging/packaging-uwp-apps)。

使用 [啟動但不進行偵測] 會自動啟動您裝置上的應用程式，而不會附加 Visual Studio 偵錯工具。

若要在不自動啟動應用程式的情況下部署裝置，選取 [組建] > [部署解決方案]。

> [!NOTE]
>您可能會注意到應用程式中的診斷 profiler，您可以使用語音命令「 **切換診斷**」來開啟或關閉。 建議您在開發期間儘量讓分析工具保持可見，以了解應用程式的變更何時會對效能產生影響。 例如，HoloLens 應用程式應該[持續以 60 FPS 執行](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md)。

## <a name="congratulations"></a>恭喜！

您現在已部署了第一個 HoloLens 應用程式。 開啟應用程式之後，您應該會看到 Cube 物件放在您面前，而且應該可以移動它來與 cube 互動，您應該會看到空間對應網格，其中涵蓋了 HoloLens 所察覺的介面。 此外，您應該會看到雙手和手指上有用於手部追蹤的指標，還有用於留意應用程式效能的畫面播放速率計數器。 這些功能只是 MRTK 所包含的幾個基本部分。 在接下來的教學課程中，您將會在場景中新增內容，以探索 HoloLens 和 MRTK 的功能。

> [!div class="nextstepaction"]
> [下一個教學課程：3.設定 MRTK 設定檔](mr-learning-base-03.md)
