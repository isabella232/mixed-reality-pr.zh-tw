---
ms.openlocfilehash: 18921520cc9cd7cea3fb6957d3fad823103e3e3d
ms.sourcegitcommit: 4fb961beeebd158e2f65b7c714c5e471454400a3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/30/2021
ms.locfileid: "105983271"
---
# <a name="unity-20192020--windows-xr-plugin"></a>[Unity 2019/2020 + Windows XR 外掛程式](#tab/winxr)

在 Unity 功能表中，選取 [編輯] >  [專案設定...] 來開啟 [專案設定] 視窗：

![Unity [專案設定...] 功能表路徑](../images/mr-learning-base/base-02-section5-step2-1.png)

在 [專案設定] 視窗中，選取 [ **XR 外掛程式管理**  >  **安裝 XR 外掛程式管理**]，以安裝 XR 外掛程式管理：

![已選取新增 [Windows Mixed Reality] SDK 的 Unity XR 設定](../images/mr-learning-base/base-02-section5-step2-2.png)

Unity 完成安裝 XR 外掛程式管理之後。 確定您處於通用 Windows 平臺設定，並 **在啟動時檢查 INITIALIZE XR** 並 **Windows Mixed Reality** 核取方塊。

![已選取新增 [Windows Mixed Reality] SDK 的 Unity XR 設定](../images/mr-learning-base/base-02-section5-step2-2-1.png)

Unity 完成匯入 Windows Mixed Reality SDK 後，應該會再次出現 [MRTK 專案配置器] 視窗。 如果沒有出現，請使用 Unity 功能表開啟。

在 [MRTK 專案設定] 視窗中，使用 **Audio 空間定位器** 下拉式清單選取 [MS HRTF 空間定位器]，然後按一下 [套用] 按鈕來套用設定：

![已選取新增 [Windows Mixed Reality] SDK 的 Unity XR 設定](../images/mr-learning-base/base-02-section5-step2-2-2.png)

> [!TIP]
>您可以選擇是否設定 [音訊空間定位器] 屬性，但這麼做可以改善專案中的音訊體驗。 如果您將此屬性設定為 [MS HRTF 空間定位器]，當 Unity 的 AudioSource.spatialize 屬性啟用時，便會使用此空間定位器外掛程式。 若要深入瞭解本主題，您可以參考  <a href="https://docs.microsoft.com/en-us/windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank"> 空間音訊教學</a>課程。

在 [專案設定] 視窗中，選取 **[XR 外掛程式管理**  >  **Windows Mixed Reality**  >  **執行時間設定**]，然後使用 [**深度緩衝區格式**] 下拉式清單選取 **16 位深度：**

![已設定 [套件名稱] 的 Unity [發佈設定]](../images/mr-learning-base/base-02-section5-step2-5-1.png)

> [!TIP]
> 您可以選擇是否將 [深度格式] 減少為 16 位元，但這麼做可協助改善專案中的圖形效能。 若要深入瞭解本主題，您可以參考 MRTK 的<a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html" target="_blank">效能</a>檔中的<a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html#depth-buffer-sharing-hololens" target="_blank">深度緩衝區共用 (HoloLens) </a>一節。

在 [專案設定] 視窗中，選取 [播放程式] > [發佈設定]，然後在 **套件名稱** 欄位中輸入適當的名稱，例如 _MRTKTutorials-GettingStarted_：

![已設定 [套件名稱] 的 Unity [發佈設定]](../images/mr-learning-base/base-02-section5-step2-7.png)

> [!NOTE]
> 「套件名稱」是應用程式的唯一識別碼。 您應該在部署應用程式之前變更此識別碼，以避免覆寫先前安裝的應用程式。

> [!TIP]
> 「產品名稱」是 HoloLens 開始功能表中顯示的名稱。 若要在開發期間更容易找到應用程式，請在名稱前面加上底線，將其排序到頂端。

# <a name="legacy-wsa"></a>[舊版 WSA](#tab/wsa)

在 Unity 功能表中，選取 [編輯] >  [專案設定...] 來開啟 [專案設定] 視窗：

在 [專案設定] 視窗中，選取 [ **Player**  >  **XR 設定**] 並選取 [**支援虛擬**] 核取方塊，然後按一下 **+** 圖示，然後選取 [Windows Mixed Reality] 以新增 Windows Mixed Reality SDK：

![已選取新增 [Windows Mixed Reality] SDK 的 Unity XR 設定](../images/mr-learning-base/base-02-section5-step2-4.png)

Unity 完成匯入 Windows Mixed Reality SDK 後，應該會再次出現 [MRTK 專案配置器] 視窗。 如果沒有，您可以從 Unity 功能表手動開啟它，方法是前往 **混合現實工具** 組  >  **公用程式**  >  **設定 Unity 專案**

在 [MRTK 專案設定] 視窗中，使用 **Audio 空間定位器** 下拉式清單選取 [MS HRTF 空間定位器]，然後按一下 [套用] 按鈕來套用設定：

![已選取新增 [Windows Mixed Reality] SDK 的 Unity XR 設定](../images/mr-learning-base/base-02-section5-step2-5.png)

> [!TIP]
>您可以選擇是否設定 [音訊空間定位器] 屬性，但這麼做可以改善專案中的音訊體驗。 如果您將此屬性設定為 [MS HRTF 空間定位器]，當 Unity 的 AudioSource.spatialize 屬性啟用時，便會使用此空間定位器外掛程式。 若要深入瞭解本主題，您可以參考  <a href="//windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank"> 空間音訊教學</a>課程。

在 [專案設定] 視窗中，選取 [播放程式] > [XR 設定]，然後使用 **深度格式** 下拉式清單選取 **16 位元深度**：

![Unity 啟用16深度](../images/mr-learning-base/base-02-section5-step2-6.png)

> [!TIP]
> 您可以選擇是否將 [深度格式] 減少為 16 位元，但這麼做可協助改善專案中的圖形效能。 若要深入瞭解本主題，您可以參考 MRTK 的<a href="/windows/mixed-reality/mrtk-docs/performance/perf-getting-started.md#single-pass-instanced-rendering" target="_blank">效能</a>檔中的<a href="/windows/mixed-reality/mrtk-docs/performance/perf-getting-started.md#single-pass-instanced-rendering" target="_blank">深度緩衝區共用 (HoloLens) </a>一節。

在 [專案設定] 視窗中，選取 [播放程式] > [發佈設定]，然後在 **套件名稱** 欄位中輸入適當的名稱，例如 _MRTKTutorials-GettingStarted_：

![已設定 [套件名稱] 的 Unity [發佈設定]](../images/mr-learning-base/base-02-section5-step2-7.png)

> [!NOTE]
> 「套件名稱」是應用程式的唯一識別碼。 您應該在部署應用程式之前變更此識別碼，以避免覆寫先前安裝的應用程式。

> [!TIP]
> 「產品名稱」是 HoloLens 開始功能表中顯示的名稱。 若要在開發期間更容易找到應用程式，請在名稱前面加上底線，將其排序到頂端。
