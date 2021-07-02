---
ms.openlocfilehash: 2420e68a0753739111fc2c5eecfbd1da563f52c2
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175966"
---
# <a name="unity-2020--openxr"></a>[Unity 2020 + OpenXR](#tab/openxr)

**MixedRealityFeatureTool** 開啟後，按一下 [**開始**] 以開始使用 Mixed Reality 功能工具。

<img src="../images/mr-learning-base/base-02-section4-step1-2.png" width="650px" alt="MixedRealityFeatureTool main screen">

第一個步驟是使用 **省略號** 按鈕將「混合現實」功能工具指向您的 **Project 路徑**，按一下 Project 路徑旁的三個點省略號按鈕，然後流覽至您在瀏覽器中的專案資料夾，例如 _D:\MixedRealityLearning\MRTK 教學_ 課程。

<img src="../images/mr-learning-base/base-02-section4-step1-3.png" width="650px" alt="Adding Unity Path for MixedRealityFeatureTool">

當您找到專案的資料夾時，請按一下 [開啟] 按鈕以返回 [混合現實] 功能工具。 然後按一下 [ **探索功能**]。

> [!NOTE]
> 流覽 Unity 專案資料夾時顯示的對話方塊會包含 ' _ ' 作為檔案名。 檔案名必須有一個值，才能選取該資料夾。

> [!Important]
> 「混合現實」功能工具會執行驗證，以確保它已導向至 Unity 專案資料夾。 資料夾必須包含資產、封裝和 Project 設定資料夾。

功能會依類別目錄分組，讓您更容易尋找，請按一下 [ **Mixed Reality 工具** 組] 下拉式清單來尋找與混合現實工具組相關的套件，然後按一下 [ **平臺支援** ] 下拉式清單，以尋找與各種支援平臺相關的套件。

<img src="../images/mr-learning-base/base-02-section4-step1-4-openxr.png" width="650px" alt="MixedRealityFeatureTool Discover Features">

檢查 **Mixed Reality 工具組 Foundation** ，然後按一下其旁邊的下拉式清單，選取 [ **MRTK 2.7.2**]，同時檢查 **mixed reality OpenXR 外掛程式 1.0.0** ，然後按一下其旁邊的下拉式清單，以選取最新可用的版本，然後按一下 [ **取得功能** ] 按鈕以下載選取的套件。

<img src="../images/mr-learning-base/base-02-section4-step1-5-openxr.png" width="650px" alt="MixedRealityFeatureTool Open MixedReality">

接下來按一下 [ **驗證** ] 按鈕以驗證選取的封裝，您會看到 [偵測 **不到驗證問題** 的快顯視窗 **] 按一下 [確定]** 關閉快顯視窗，然後按一下 [匯 **入** ] 按鈕。

<img src="../images/mr-learning-base/base-02-section4-step1-6-openxr.png" width="650px" alt="MixedRealityFeatureTool Select required package">


按一下 [ **核准** ] 按鈕，將 **Mixed Reality 工具** 組新增至專案。

<img src="../images/mr-learning-base/base-02-section4-step1-7-openxr.png" width="650px" alt="MixedRealityFeatureTool Validate package">

## <a name="configuring-the-unity-project"></a>設定 Unity 專案

Unity 完成從上一節匯入封裝之後，會出現一則警告訊息，以重新開機 Unity 編輯器，以便後端新外掛程式系統，請按一下 **[是]** 。

<img src="../images/mr-learning-base/base-02-section5-step1-1-openxr.png" width="650px" alt="Unity Restart Option">

Unity 重新開機後，MRTK Project 的 [配置器] 視窗隨即出現。 如果沒有，您可以藉由前往 **混合現實**  >  **工具** 組  >  **公用程式** 來  >  **設定 MRTK 的 Project**，以手動方式開啟它：

![開啟 MRTK 專案配置器視窗](../images/mr-learning-base/base-02-section5-step1-2-openxr.png)

按一下 **Unity OpenXR 外掛程式** ，以啟用 XR 外掛程式管理，並將其所需的套件新增至您的專案。

![新增 Unity OpenXR 外掛程式 ](../images/mr-learning-base/base-02-section5-step1-3-openxr.png)

這會匯入 XR 外掛程式管理所需的 unity 套件，一旦完成，請按一下 [MRTK 專案] 設定檔中的 [**顯示 XR Plug-In 管理] 設定**。

![顯示 XR Plug-In 管理設定 ](../images/mr-learning-base/base-02-section5-step1-4-openxr.png)

這會開啟 **Project 設定] 視窗**。 在 [ **XR 外掛程式管理**] 下的 [Project 設定] 視窗中，確定您處於通用 Windows 平臺設定 (Windows 標誌] 索引標籤) 。 此外，請確定已核取 [**啟動時初始化 XR** ]，然後按一下 [ **OpenXR** ] 核取方塊並 **Microsoft HoloLens [功能集**] 核取方塊加以啟用。

![啟用 Open XR](../images/mr-learning-base/base-02-section5-step1-5-openxr.png)

核取 [OpenXR] 核取方塊之後，MRTK Project 的 [配置器] 視窗會顯示 [套用 **設定**] 按鈕的更新訊息。 按一下 [套用]**設定** 按鈕。 

![Project 設定視窗1](../images/mr-learning-base/base-02-section5-step1-6-openxr.png)

當您按一下 [套用] 設定時，您可能會在主控台中看到此錯誤訊息。 如果這是唯一的錯誤或沒有錯誤，您可以繼續進行。

![OpenXR 遠端處理錯誤訊息](../images/mr-learning-base/base-02-section5-step1-6-openxr-Error.png)

若要驗證 OpenXR 設定，請按一下 **[XR 外掛程式管理]** 下的 [ **OpenXR** ]，並檢查下列專案：
* 深度提交模式： **深度16位**
* 互動設定檔： **Microsoft 手互動設定檔**

![Project 設定視窗2](../images/mr-learning-base/base-02-section5-step1-7-openxr.png)

> [!TIP]
> 您可以選擇是否將 [深度格式] 減少為 16 位元，但這麼做可協助改善專案中的圖形效能。 若要深入了解本主題，您可以參閱 MRTK 效能文件中的<a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering" target="_blank">深度緩衝區共用 (HoloLens)</a> 一節。


在 [ **MRTK Project** 設定器] 視窗中，按一下 [**下一步**]，然後按一下 [套用]**按鈕以** 套用設定。  (如果您將其關閉，您可以藉由前往 **混合現實**  >  **工具** 組  >  **公用程式**  >  **設定 Project 進行 MRTK** ，以手動方式開啟它) 

![Project 設定視窗3](../images/mr-learning-base/base-02-section5-step1-8-openxr.png)

![Project 設定視窗4](../images/mr-learning-base/base-02-section5-step1-9-openxr.png)

當您按一下 [套用] 之後，Unity 將會嘗試重新開機，輸入系統才會生效，請按一下 [套用 **] 以重新** 啟動 Unity 編輯器

### <a name="configure-additional-project-settings"></a>設定其他專案設定

在 Unity 功能表中，選取 [**編輯**  >  **Project 設定 ...** ] 以開啟 Project 設定視窗。

在 [專案設定] 視窗中，選取 [播放程式] > [發佈設定]，然後在 **套件名稱** 欄位中輸入適當的名稱，例如 _MRTKTutorials-GettingStarted_：

![Unity 發佈設定。 已設定套件名稱](../images/mr-learning-base/base-02-section5-step2-2.png)

> [!NOTE]
> 「套件名稱」是應用程式的唯一識別碼。 您應該在部署應用程式之前變更此識別碼，以避免覆寫先前安裝的應用程式。

> [!TIP]
> 「產品名稱」是 HoloLens 開始功能表中顯示的名稱。 若要在開發期間更容易找到應用程式，請在名稱前面加上底線，將其排序到頂端。

# <a name="unity-20192020--windows-xr-plugin"></a>[Unity 2019/2020 + Windows XR 外掛程式](#tab/winxr)

**MixedRealityFeatureTool** 開啟後，按一下 [**開始**] 以開始使用 Mixed Reality 功能工具。

<img src="../images/mr-learning-base/base-02-section4-step1-2.png" width="650px" alt="MixedRealityFeatureTool main screen">

第一個步驟是使用 **省略號** 按鈕將「混合現實」功能工具指向您的 **Project 路徑**，按一下 Project 路徑旁的三個點省略號按鈕，然後流覽至您在瀏覽器中的專案資料夾，例如 _D:\MixedRealityLearning\MRTK 教學_ 課程。

<img src="../images/mr-learning-base/base-02-section4-step1-3.png" width="650px" alt="Adding Unity Path for MixedRealityFeatureTool">


當您找到專案的資料夾時，請按一下 [開啟] 按鈕以返回 [混合現實] 功能工具。 然後按一下 [ **探索功能**]。

> [!NOTE]
> 流覽 Unity 專案資料夾時顯示的對話方塊會包含 ' _ ' 作為檔案名。 檔案名必須有一個值，才能選取該資料夾。

> [!Important]
> 「混合現實」功能工具會執行驗證，以確保它已導向至 Unity 專案資料夾。 資料夾必須包含資產、封裝和 Project 設定資料夾。

功能會依類別目錄分組，讓您更容易找到這些專案，請按一下 [ **Mixed Reality 工具** 組] 下拉式清單，以尋找與混合現實工具組相關的套件。

<img src="../images/mr-learning-base/base-02-section4-step1-4.PNG" width="650px" alt="MixedRealityFeatureTool Discover Features">

核取 [ **混合現實工具組 Foundation**] 的方塊，然後按一下其旁邊的下拉式清單，選取 [ **MRTK 2.7.0**]，然後按一下 [ **取得功能** ] 按鈕以下載選取的套件。

<img src="../images/mr-learning-base/base-02-section4-step1-5.PNG" width="650px" alt="MixedRealityFeatureTool Open Mixed Reality">

接下來按一下 [ **驗證** ] 按鈕以驗證選取的封裝，您會看到 [偵測 **不到驗證問題** 的快顯視窗 **] 按一下 [確定]** 關閉快顯視窗，然後按一下 [匯 **入** ] 按鈕。

<img src="../images/mr-learning-base/base-02-section4-step1-6.PNG" width="650px" alt="MixedRealityFeatureTool Select required package">


按一下 [ **核准** ] 按鈕，將 **Mixed Reality 工具** 組新增至專案。

<img src="../images/mr-learning-base/base-02-section4-step1-7.PNG" width="650px" alt="MixedRealityFeatureTool Validate package">


## <a name="configuring-the-unity-project"></a>設定 Unity 專案

Unity 完成上一節中提到的匯入封裝後，應該會出現 [MRTK 專案配置器] 視窗。 如果沒有，您可以藉由前往 **混合現實**  >  **工具** 組  >  **公用程式** 來  >  **設定 MRTK 的 Project**，以手動方式開啟它：

![開啟 MRTK 的配置器工具](../images/mr-learning-base/base-02-section5-step1-1xrsdk.PNG)

按一下 **內建 Unity 外掛程式 (非 OpenXR)** ，以啟用 XR 外掛程式管理，並將其所需的套件新增至您的專案。

![ MRTK 配置器工具](../images/mr-learning-base/base-02-section5-step1-2xrsdk.PNG)

> [!NOTE]
> 上述螢幕擷取畫面是來自 Unity 2020，如果您使用 Unity 2019，請選取 **XR SDK/XR 管理**

這會匯入 XR 外掛程式管理所需的 unity 套件，一旦完成，請按一下 [MRTK 專案] 設定檔中的 [**顯示設定**。

![播放機設定視窗](../images/mr-learning-base/base-02-section5-step1-3xrsdk.PNG)

這會開啟 **Project 設定] 視窗** 中，在 [ **XR 外掛程式管理**] 下的 [Project 設定] 視窗中，確定您是在 [**啟動時初始化 XR** ] 核取方塊，然後核取 [**通用 Windows 平臺**] 核取方塊。

![[播放機設定] 視窗啟用混合現實-xrsdk](../images/mr-learning-base/base-02-section5-step1-4xrsdk.PNG)

Unity 完成匯入 Windows Mixed Reality SDK 後，應該會再次出現 [MRTK 專案配置器] 視窗。 如果沒有出現，請使用 Unity 功能表開啟。

在 [MRTK Project 設定] 視窗中，按一下 **[下一步**]，然後使用 [音訊空間定位器] 下拉式清單選取 **MS HRTF 空間定位器**，然後按一下 [套用 **] 按鈕以** 套用設定：

![MRTK 專案配置器-xrsdk](../images/mr-learning-base/base-02-section5-step1-5xrsdk.PNG)

> [!TIP]
> 您可以選擇是否套用 MRTK 預設設定，但強烈建議您這麼做，因為這可協助您設定一些建議的 Unity 設定：

> * 設定單一階段執行個體化轉譯路徑：藉由在相同的繪製呼叫中為雙眼執行轉譯管線，來改善圖形效能。 若要深入了解本主題，您可以參閱 MRTK [效能](/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering)文件中的[單一階段執行個體化轉譯](/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering)一節。
> * 設定預設空間感知層：建立名為「空間感知」的 Unity 圖層，並將 MRTK 設定為將此圖層用於空間感知網格。 若要深入了解 Unity 圖層，您可以參閱 Unity 的<a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">自訂您的工作區</a>文件。

> [!TIP]
> 您可以選擇是否設定 [音訊空間定位器] 屬性，但這麼做可以改善專案中的音訊體驗。 如果您將此屬性設定為 [MS HRTF 空間定位器]，當 Unity 的 AudioSource.spatialize 屬性啟用時，便會使用此空間定位器外掛程式。 若要深入瞭解本主題，您可以參考  <a href="//windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank"> 空間音訊教學</a>課程。

按一下 [**下一步**]，然後按一下 [MRTK Project 設定] 視窗中的 [**完成**]，完成 XRSDK 的 Unity 專案設定。

### <a name="configure-additional-project-settings"></a>設定其他專案設定

在 Unity 功能表中，選取 [編輯] >  [專案設定...] 來開啟 [專案設定] 視窗：

在 [Project 設定] 視窗中，選取 **[XR 外掛程式管理**  >  **Windows Mixed Reality**  >  **運行** 時間] 設定，然後使用 [**深度緩衝區格式**] 下拉式清單選取 **16 位深度**：

![Unity 啟用16深度](../images/mr-learning-base/base-02-section5-step2-1xrsdk.PNG)

> [!TIP]
> 您可以選擇是否將 [深度格式] 減少為 16 位元，但這麼做可協助改善專案中的圖形效能。 若要深入了解本主題，您可以參閱 MRTK 效能文件中的<a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering" target="_blank">深度緩衝區共用 (HoloLens)</a> 一節。

在 [專案設定] 視窗中，選取 [播放程式] > [發佈設定]，然後在 **套件名稱** 欄位中輸入適當的名稱，例如 _MRTKTutorials-GettingStarted_：

![Unity 發佈設定。 已設定套件名稱](../images/mr-learning-base/base-02-section5-step2-2.png)

> [!NOTE]
> 「套件名稱」是應用程式的唯一識別碼。 您應該在部署應用程式之前變更此識別碼，以避免覆寫先前安裝的應用程式。

> [!TIP]
> 「產品名稱」是 HoloLens 開始功能表中顯示的名稱。 若要在開發期間更容易找到應用程式，請在名稱前面加上底線，將其排序到頂端。

# <a name="legacy-wsa"></a>[舊版 WSA](#tab/wsa)

**MixedRealityFeatureTool** 開啟後，按一下 [**開始**] 以開始使用 Mixed Reality 功能工具。

<img src="../images/mr-learning-base/base-02-section4-step1-2.png" width="650px" alt="MixedRealityFeatureTool main screen">

第一個步驟是使用 **省略號** 按鈕將「混合現實」功能工具指向您的 **Project 路徑**，按一下 Project 路徑旁的三個點省略號按鈕，然後流覽至您在瀏覽器中的專案資料夾，例如 _D:\MixedRealityLearning\MRTK 教學_ 課程。

<img src="../images/mr-learning-base/base-02-section4-step1-3.png" width="650px" alt="Adding Unity Path for MixedRealityFeatureTool">

當您找到專案的資料夾時，請按一下 [開啟] 按鈕以返回 [混合現實] 功能工具。 然後按一下 [ **探索功能**]。

> [!NOTE]
> 流覽 Unity 專案資料夾時顯示的對話方塊會包含 ' _ ' 作為檔案名。 檔案名必須有一個值，才能選取該資料夾。

> [!Important]
> 「混合現實」功能工具會執行驗證，以確保它已導向至 Unity 專案資料夾。 資料夾必須包含資產、封裝和 Project 設定資料夾。

功能會依類別目錄分組，讓您更容易找到這些專案，請按一下 [ **Mixed Reality 工具** 組] 下拉式清單，以尋找與混合現實工具組相關的套件。

<img src="../images/mr-learning-base/base-02-section4-step1-4.PNG" width="650px" alt="MixedRealityFeatureTool Discover Features">

檢查 **Mixed Reality 工具組 Foundation**，然後按一下其旁邊的下拉式清單，選取 [ **MRTK 2.7.0**]，然後按一下 [ **取得功能** ] 按鈕以下載選取的套件。

<img src="../images/mr-learning-base/base-02-section4-step1-5.PNG" width="650px" alt="MixedRealityFeatureTool Open Mixed Reality">

接下來按一下 [ **驗證** ] 按鈕以驗證選取的封裝，您會看到 [偵測 **不到驗證問題** 的快顯視窗 **] 按一下 [確定]** 關閉快顯視窗，然後按一下 [匯 **入** ] 按鈕。

<img src="../images/mr-learning-base/base-02-section4-step1-6.PNG" width="650px" alt="MixedRealityFeatureTool Select required package">

按一下 [ **核准** ] 按鈕，將 **Mixed Reality 工具** 組新增至專案。

<img src="../images/mr-learning-base/base-02-section4-step1-7.PNG" width="650px" alt="MixedRealityFeatureTool Validate package">


## <a name="configuring-the-unity-project"></a>設定 Unity 專案

Unity 完成上一節中提到的匯入封裝後，應該會出現 [MRTK 專案配置器] 視窗。 如果沒有，您可以藉由前往 **混合現實**  >  **工具** 組  >  **公用程式** 來  >  **設定 MRTK 的 Project**，以手動方式開啟它：

![Unity [設定 Unity 專案] 功能表路徑](../images/mr-learning-base/base-02-section5-step1-1.png)

按一下 **舊版 XR** 可啟用舊版 XR，並將其所需的套件新增至您的專案。

![s](../images/mr-learning-base/base-02-section5-step1-2.png)

按一下 [下一步] 按鈕，為舊版 XR 啟用 XR 管線設定。

![Unity MRTK 設定視窗](../images/mr-learning-base/base-02-section5-step1-3.PNG)

在 [MRTK Project 設定器] 視窗中，確定已核取所有選項，並且使用 [**音訊空間定位器**] 下拉式清單來選取 **MS HRTF 空間定位器**，然後 **按一下 [套用**] 按鈕以套用設定：

![MRTK 設定視窗](../images/mr-learning-base/base-02-section5-step1-4.PNG)

> [!TIP]
> 您可以選擇是否套用 MRTK 預設設定，但強烈建議您這麼做，因為這可協助您設定一些建議的 Unity 設定：

> * 設定單一階段執行個體化轉譯路徑：藉由在相同的繪製呼叫中為雙眼執行轉譯管線，來改善圖形效能。 若要深入了解本主題，您可以參閱 MRTK [效能](/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering)文件中的[單一階段執行個體化轉譯](/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering)一節。
> * 設定預設空間感知層：建立名為「空間感知」的 Unity 圖層，並將 MRTK 設定為將此圖層用於空間感知網格。 若要深入了解 Unity 圖層，您可以參閱 Unity 的<a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">自訂您的工作區</a>文件。

> [!TIP]
> 您可以選擇是否設定 [音訊空間定位器] 屬性，但這麼做可以改善專案中的音訊體驗。 如果您將此屬性設定為 [MS HRTF 空間定位器]，當 Unity 的 AudioSource.spatialize 屬性啟用時，便會使用此空間定位器外掛程式。 若要深入瞭解本主題，您可以參考  <a href="//windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank"> 空間音訊教學</a>課程。

按一下 **[下一步**]，然後按一下 [MRTK Project 設定] 視窗中的 [**完成**] 按鈕，以完成舊版 XR 的 Unity 專案設定。

### <a name="configure-additional-project-settings"></a>設定其他專案設定

在 Unity 功能表中，選取 [編輯] >  [專案設定...] 來開啟 [專案設定] 視窗：

在 [專案設定] 視窗中，選取 [播放程式] > [XR 設定]，然後使用 **深度格式** 下拉式清單選取 **16 位元深度**：

![Unity 啟用16深度](../images/mr-learning-base/base-02-section5-step2-1.png)

> [!TIP]
> 您可以選擇是否將 [深度格式] 減少為 16 位元，但這麼做可協助改善專案中的圖形效能。 若要深入了解本主題，您可以參閱 MRTK 效能文件中的<a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering" target="_blank">深度緩衝區共用 (HoloLens)</a> 一節。

在 [專案設定] 視窗中，選取 [播放程式] > [發佈設定]，然後在 **套件名稱** 欄位中輸入適當的名稱，例如 _MRTKTutorials-GettingStarted_：

![Unity 發佈設定。 已設定套件名稱](../images/mr-learning-base/base-02-section5-step2-2.png)

> [!NOTE]
> 「套件名稱」是應用程式的唯一識別碼。 您應該在部署應用程式之前變更此識別碼，以避免覆寫先前安裝的應用程式。

> [!TIP]
> 「產品名稱」是 HoloLens 開始功能表中顯示的名稱。 若要在開發期間更容易找到應用程式，請在名稱前面加上底線，將其排序到頂端。
