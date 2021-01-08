---
title: Unity 的建議設定
description: 瞭解 Unity 的效能以及混合現實應用程式特定的發佈行為，這些行為可透過專案設定來切換。
author: hferrone
ms.author: v-hferrone
ms.date: 07/29/2020
ms.topic: article
keywords: unity、設定、混合現實、HoloLens、混合現實耳機、windows mixed reality 耳機、虛擬實境耳機、效能、品質設定、照明設定、深度緩衝區、xr、追蹤損失
ms.openlocfilehash: be85b592a6857c9dd40e2b3bb3f09dec0a6273be
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009328"
---
# <a name="recommended-settings-for-unity"></a>Unity 的建議設定

Unity 提供一組預設選項，通常是所有平臺的平均案例。 不過，Unity 提供某些混合現實特定的行為，可透過專案設定來切換。

## <a name="performant-environment-set-up"></a>高效能環境設定

### <a name="low-quality-settings"></a>低品質設定

請務必將 **Unity 品質設定** 修改為 **非常低** ，如此您的應用程式就會在適當的速率下執行，並以適當的速率執行，特別是針對 HoloLens 開發。 在沉浸式耳機上進行開發時，根據桌上型電腦的規格來提供 VR 體驗，您仍然可以在沒有最低品質參數的情況下達到畫面播放速率。

在 Unity 2019 LTS + 中，您可以藉由前往 [**編輯** 專案設定品質] 來設定專案的品質等級  >    >   ，然後按一下向下箭號，以設定 **預設值*** * 非常低品質的等級。

### <a name="lighting-settings"></a>光源設定

類似于品質場景設定，請務必為您的混合現實應用程式設定最佳光源設定。 在 Unity 中，通常會對您的場景具有最大效能影響的光源設定，是 **即時的全球照明**。 您可以前往 **視窗** 轉譯  >    >  **光源設定**  >  **即時全球照明**，關閉全域照明。

另外還有另一個光源設定 **內建全球照明**。 這種設定可以在沉浸式耳機上提供高效能且以視覺方式呈現的結果，但不適用於 HoloLens 開發。 **內建全域照明** 只會針對靜態 gameobject 計算，因為由於未知且變更的環境本質，無法在 HoloLens 場景中找到。

如需詳細資訊，請參閱 [Unity 的全球照明](https://docs.unity3d.com/Manual/GIIntro.html) 。 

>[!NOTE]
> **即時全域照明** 是 **針對每個場景** 設定的，因此開發人員必須為專案中的每個 Unity 場景儲存此屬性。

### <a name="single-pass-instancing-rendering-path"></a>單一傳遞實例轉譯路徑

在混合現實應用程式中，場景會轉譯兩次，每一次對使用者來說。 相較于傳統的3D 開發，這會有效地將需要計算的工作量加倍。 請務必在 Unity 中選取最有效率的轉譯路徑，以節省 CPU 和 GPU 時間。 單一傳遞實例轉譯可針對混合現實應用程式優化 Unity 轉譯管線，建議針對每個專案預設啟用這項設定。

若要在 Unity 專案中啟用這項功能

1)  開啟 [Player XR 設定] (移至 [編輯] > [專案設定] > [播放器] > [XR 設定])
2) 從 [立體聲轉譯方法] 下拉式功能表中，選取 [單通道執行個體化] (必須核取 [支援的虛擬實境] 核取方塊)

如需此轉譯方法的詳細資訊，請參閱 Unity 中的下列文章。

- [如何使用進階的立體聲轉譯將 AR 和 VR 效能最大化](https://blogs.unity3d.com/2017/11/21/how-to-maximize-ar-and-vr-performance-with-advanced-stereo-rendering/)
- [單通道執行個體](https://docs.unity3d.com/Manual/SinglePassInstancing.html)

>[!NOTE]
> 如果開發人員已經有非針對執行個體撰寫的現有自訂著色器，就會發生單通道執行個體化轉譯的一個常見問題。 啟用這項功能之後，開發人員可能會注意到，有些 GameObject 只會在單一眼球中轉譯。 這是因為相關聯的自訂著色器沒有適當的執行個體屬性。
>
> 如需解決此問題的方法，請參閱 Unity 中的[適用於 HoloLens 的單通道立體聲轉譯](https://docs.unity3d.com/Manual/SinglePassStereoRenderingHoloLens.html)

### <a name="enable-depth-buffer-sharing"></a>啟用深度緩衝區共用

若要從使用者的觀點來達到更好的全像影像穩定性，建議您在 Unity 中啟用 **深度緩衝區共用** 屬性。 藉由開啟此項，Unity 將會與 Windows Mixed Reality 平臺共用您的應用程式所產生的深度對應。 然後，此平臺可以針對您的應用程式所呈現的任何特定框架，更妥善地優化全像場景的全像是您的場景。

若要在 Unity 專案中啟用這項功能

1) 開啟 [Player XR 設定] (移至 [編輯] > [專案設定] > [播放器] > [XR 設定])
2) 選取 [在 **虛擬實境 sdk** Windows Mixed Reality 擴充] 下 **啟用深度緩衝區共用** 的核取方塊，  >   (必須核取 [**虛擬實境支援**] 核取方塊) 

此外，建議您在此面板中選取 [**深度格式**] 設定下的 **16 位深度**，特別是針對 HoloLens 開發。 相較于24位，選取16位會大幅減少頻寬需求，因為需要移動/處理的資料較少。

為了讓 Windows Mixed Reality 平臺優化全像影像的穩定性，它依賴深度緩衝區來精確且符合螢幕上任何轉譯的全像影像。 因此，在上有深度緩衝區共用時，轉譯色彩時很重要，也就是呈現深度。 在 Unity 中，大部分的不透明或 TransparentCutout 材質預設會呈現深度，但透明和文字物件將不會呈現深度，雖然這是與著色器相依的情況等等。

如果使用 [混合現實工具組標準著色器](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_MRTKStandardShader.md)來呈現透明物件的深度：

1) 選取使用 MRTK 標準著色器的透明材質，然後開啟偵測器編輯器視窗
2) 選取深度緩衝區共用警告內的 [ **立即修正** ] 按鈕。 您也可以將轉譯 **模式** 設定為 **Custom**，以手動方式執行這項作業。然後將 **模式** 設定為 [**透明**]，最後將 [**深度寫入**] 設定為 [**開啟**]

> [!IMPORTANT]
> 當您變更這些值以及相機的近/上平面設定時，開發人員應該注意 Z 的干擾。 當兩個 gameobject 嘗試轉譯成相同的圖元，而因為深度緩衝區的精確度有所限制時，就會發生 Z 對抗 (例如 z 深度) ，Unity 無法分辨哪一個物件位於另一個物件之前。 開發人員會注意到兩個遊戲物件之間的閃爍，因為它們會 *對抗* 相同的 z 深度值。 切換至24位深度格式可解決這種情況，因為每個物件的值範圍會比從相機的 z 深度算出的值更大。
>
> 不過，建議您特別針對 HoloLens 開發，將相機近和遠的平面修改為較小的範圍，並保留16位深度格式。 Z 深度會以非線性方式對應至接近或距離相機平面的值範圍。 您可以藉由選取場景中的 *主要相機* 和在 [偵測 **器**] 下進行修改，變更 **接近的 & 遠裁剪平面** 值，以縮減其範圍 (亦即 從變更為1000m 到100m 或其他 x 值等等 ) 

>[!IMPORTANT]
> Unity 在使用16位深度格式時，[不會建立樣板緩衝區](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html)。 因此，某些 Unity UI 效果和其他樣板所需的效果將無法運作，除非選取了24位深度格式，而這會建立 [8 位](https://docs.unity3d.com/Manual/SL-Stencil.html)的樣板緩衝區。

### <a name="building-for-il2cpp"></a>建立 IL2CPP

Unity 已淘汰 .NET 腳本後端的支援，因此建議開發人員使用 **IL2CPP** 來處理其 UWP visual studio 組建。 雖然這帶來了各種優點，但從 Unity 建立您的 visual studio 解決方案， **IL2CPP** 可能會比舊的 .net 方法慢。 因此，強烈建議您遵循最佳做法來建立 **IL2CPP** ，以節省開發反復專案時間。

1) 每次在相同的目錄中建立您的專案，並在該處重複使用預先建立的檔案，以利用累加式大樓
2) 針對您的專案停用反惡意程式碼軟體掃描 & 組建資料夾
   - 在您的 Windows 10 設定應用程式下開啟 **病毒 & 威脅防護**
   - 選取 [**病毒 & 威脅防護設定**] 下的 [**管理設定**]
   - 選取 [**排除**] 區段底下的 [**新增或移除排除** 專案]
   - 選取 [ **新增排除** ]，然後選取包含 Unity 專案程式碼和組建輸出的資料夾
3) 使用 SSD 來建立

如需詳細資訊，請參閱 [IL2CPP 的優化組建時間](https://docs.unity3d.com/Manual/IL2CPP-OptimizingBuildTimes.html) 。

> [!NOTE]
> 此外，設定[快取伺服器](https://docs.unity3d.com/Manual/CacheServer.html)可能會有幫助，對於有大量資產 (排除指令檔) 或不斷變更場景/資產的 Unity 專案來說，更是如此。 開啟專案時，Unity 會將符合資格的資產以內部快取格式儲存在開發機器上。 項目必須重新匯入，因此修改時必須加以重新處理。 此程序可以執行一次後就儲存在快取伺服器中，之後再與其他開發人員共用以節省時間，而不是每位開發人員都在本機處理新變更的重新匯入工作。

## <a name="publishing-properties"></a>發佈屬性

### <a name="holographic-splash-screen"></a>全像啟動顯示畫面

HoloLens 有行動類別的 CPU 和 GPU，這表示應用程式可能需要較長的時間才能載入。 當應用程式正在載入時，使用者只會看到黑色，因此可能會想知道發生什麼事。 若要在載入期間讓它們，您可以新增全像全像顯示畫面。

若要切換全像的啟動顯示畫面：

1) 移至 [**編輯**  >  **專案設定**  >  **播放機**] 頁面
2) 選取 [ **Windows 存放區** ] 索引標籤，然後開啟 [ **啟動顯示映射** ] 區段
3) 將您的映射套用到 **> Windows** 全像攝影版的「全像」、「全像」
    - 切換 [ **顯示 Unity 啟動顯示** 畫面] 選項將會啟用或停用 Unity 品牌的啟動顯示畫面。 如果您沒有 Unity Pro 授權，則一律會顯示 Unity 品牌的啟動顯示畫面。
    - 如果已套用全像顯示的 **啟動顯示影像** ，則會一律顯示是否已啟用或停用 [顯示 Unity 啟動顯示畫面] 核取方塊。 只有具備 Unity Pro 授權的開發人員才能指定自訂的全像全息版映射。

|  顯示 Unity 啟動顯示畫面  |  全像閃屏映射  |  行為 |
|----------|----------|----------|
|  開啟  |  無  |  顯示預設的 Unity 啟動顯示畫面5秒，或直到應用程式載入為止，以較長的時間為准。 |
|  開啟  |  自訂  |  顯示自訂啟動顯示畫面5秒，或直到應用程式載入為止（以較長者為准）。 |
|  關閉  |  無  |  在載入應用程式之前，顯示透明的黑色 (沒有任何) 。 |
|  關閉  |  自訂  |  顯示自訂啟動顯示畫面5秒，或直到應用程式載入為止（以較長者為准）。 |

如需詳細資訊，請參閱 [Unity 的啟動顯示畫面檔](https://docs.unity3d.com/Manual/class-PlayerSettingsSplashScreen.html) 。

### <a name="tracking-loss"></a>追蹤遺失

混合的現實耳機取決於查看環境周圍的環境，以建立 [全球鎖定的座標系統](coordinate-systems-in-unity.md)，讓全像位置保持可換行。 當耳機無法在世界中找出自己時，即表示耳機已 *遺失追蹤*。 在這些情況下，相依于全球鎖定座標系統的功能（例如空間階段、空間錨點和空間對應）將無法運作。

如果發生追蹤遺失，Unity 的預設行為就是停止轉譯全像投影，暫停 [遊戲迴圈](https://docs.unity3d.com/Manual/ExecutionOrder.html)，並顯示追蹤遺失通知，讓使用者看起來更輕鬆。 您也可以使用追蹤遺失影像的形式來提供自訂通知。 針對相依于追蹤整個體驗的應用程式，可以讓 Unity 完全進行處理，直到重新取得追蹤為止。 開發人員可以提供要在追蹤遺失期間顯示的自訂影像。

若要自訂追蹤遺失的映射：

1) 移至 [**編輯**  >  **專案設定**  >  **播放機**] 頁面
2) 選取 [ **Windows 存放區** ] 索引標籤，然後開啟 [ **啟動顯示映射** ] 區段
3) 將您的映射套用到 Windows 全像 **> 追蹤遺失影像** ] 屬性下。

#### <a name="opt-out-of-automatic-pause"></a>退出自動暫停

某些應用程式可能不需要追蹤 (例如 [僅限方向的應用程式](coordinate-systems-in-unity.md) ，例如360度的影片檢視器) 或可能需要在追蹤遺失時繼續處理不中斷的情況。 您可以選擇不使用追蹤行為的預設遺失，但您必須負責隱藏/停用任何物件，而不會在追蹤遺失案例中正確呈現。 在大部分情況下，建議在該情況下轉譯的內容是以主體鎖定的內容，以主要攝影機為中心。

退出宣告自動暫停行為：

1) 移至 [**編輯**  >  **專案設定**  >  **播放機**] 頁面
2) 選取 [ **Windows 存放區** ] 索引標籤，然後開啟 [ **啟動顯示映射** ] 區段
3) 修改 [ **追蹤遺失時暫停和顯示影像** ] 核取方塊的 Windows 全像攝影 >。

#### <a name="tracking-loss-events"></a>追蹤遺失事件

若要定義追蹤遺失時的自訂行為，請處理全域 [追蹤遺失事件](tracking-loss-in-unity.md)。

### <a name="capabilities"></a>功能

若要讓應用程式充分利用特定功能，則必須在其資訊清單中宣告適當的功能。 您可以在 Unity 中建立資訊清單宣告，使其包含在每個未來的專案匯出中。

您可以透過下列方式，為混合現實應用程式啟用功能：

1) 移至 [**編輯**  >  **專案設定**  >  **播放機**] 頁面
2) 選取 [ **Windows 存放區** ] 索引標籤，開啟 [ **發行設定** ] 區段，然後尋找 **功能** 清單

針對全像攝影應用程式啟用常用 Api 的適用功能如下：
<br>

|  功能  |  需要功能的 Api |
|----------|----------|
|  SpatialPerception  |  SurfaceObserver |
|  攝像頭  |  PhotoCapture 和 VideoCapture |
|  PicturesLibrary/VideosLibrary  |  PhotoCapture 或 VideoCapture，分別 (儲存已捕捉的內容時)  |
|  麥克風  |  VideoCapture 捕獲音訊) 、DictationRecognizer、GrammarRecognizer 和 KeywordRecognizer 時的 ( |
|  InternetClient  |  DictationRecognizer (並使用 Unity Profiler)  |

## <a name="see-also"></a>請參閱

* [Unity 開發概觀](unity-development-overview.md)
* [了解混合實境的效能](../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md)
* [對 Unity 的效能建議](performance-recommendations-for-unity.md)
