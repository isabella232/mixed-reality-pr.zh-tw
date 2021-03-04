---
title: 在不 MRTK 的情況下設定您的專案
description: 瞭解如何在沒有混合現實工具組的情況下，為 Windows Mixed Reality 設定新的 Unity 專案。
author: hferrone
ms.author: alexturn
ms.date: 07/29/2020
ms.topic: article
keywords: Unity，混合現實，開發，使用者入門，新專案，Windows Mixed Reality，UWP，XR，效能
ms.openlocfilehash: bd25c56947007f90c0310ea9802bba91a81b0914
ms.sourcegitcommit: fd19bf57607c7ed94a849d4cf606bba2bb93e668
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2021
ms.locfileid: "102117622"
---
# <a name="configuring-your-project-without-mrtk"></a>在沒有 MRTK 的情況下設定專案

Windows Mixed Reality (WMR) 是 Windows 10 作業系統中引進的 Microsoft 平臺。 WMR 平臺可讓您建立應用程式，以在全像全像 VR 的顯示裝置上呈現數位內容。

雖然 Microsoft 和社區建立了開放原始碼工具，例如 [混合現實工具組 (MRTK) ](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html) ，而這些工具會自動設定 WMR 的環境，但許多開發人員想要從頭開始建立他們的體驗。  當您使用 MRTK 時，下列檔將示範如何針對混合現實開發正確設定專案。  您需要變更的設定分為兩類：每個專案設定和個別場景設定。

> [!NOTE]
> 您稍後可以隨時匯入 MRTK，如此一來，就不會再進行手動路由。

如果您選擇 WMR 手動設定，您需要變更的設定會分成兩種類別：個別專案和每一場景。

## <a name="per-project-settings"></a>每個專案的設定

如果您的目標是 Desktop VR，建議您在新的 Unity 專案上使用預設選取的電腦獨立平臺：

![在 unity 編輯器中開啟 [組建設定] 視窗的螢幕擷取畫面，其中已醒目提示 [電腦]、[Mac & 獨立平臺](images/wmr-config-img-3.png)

如果您是以 HoloLens 2 為目標，則必須切換至通用 Windows 平臺：

1.  選取 [檔案 **> 組建設定 ...** ]
2.  在 [平臺] 清單中選取 [**通用 Windows 平臺**]，然後選取 [**切換平臺**]
3.  將 **架構** 設定為 **ARM 64**
4.  將 **目標裝置** 設定為 **HoloLens**
5.  將 **組建類型** 設定為 **D3D**
6.  將 **UWP SDK** 設定為 **最新安裝**
7.  將 **組建** 設定設為 **發行** ，因為 Debug 有已知的效能問題

![醒目提示通用 Windows 平臺的 unity 編輯器中開啟 [組建設定] 視窗的螢幕擷取畫面](images/wmr-config-img-4.png)

設定您的平臺之後，您需要讓 Unity 知道在匯出時建立一個 [沉浸式視圖](../../design/app-views.md) ，而不是2d 視圖。

### <a name="for-xrsdk"></a>針對 XRSDK 

1. 在 Unity 編輯器中，流覽至 [**編輯 > 專案設定**]，然後選取 [ **XR 外掛程式管理**]

2. 選取 [**安裝 XR 外掛程式管理**]

![醒目提示 XR 外掛程式管理的 unity 編輯器中開啟之 [專案設定] 視窗的螢幕擷取畫面](images/wmr-config-img-5.png)

3. 選取 [**在啟動時初始化 XR** ] 和 [ **Windows Mixed Reality** ]

![醒目提示 XR 外掛程式管理的 unity 編輯器中開啟之 [專案設定] 視窗的螢幕擷取畫面](images/wmr-config-img-7.png)

4. 展開 [ **XR 外掛程式管理** ] 區段，然後選取 [ **通用 Windows 平臺設定** ] 索引標籤
5. 如果您使用 Unity 2020 或更新版本，您會看到檢查 **OpenXR (preview)** 或 **Windows Mixed Reality** 的選項
6. 您可以選擇任一執行時間。  如果您要特別針對 HoloLens 2 或 HP 回流的 G2 進行開發，並決定嘗試 **OpenXR (preview)**，請選取 [OpenXR (預覽]) 方塊，然後參閱我們的指南，以 [使用 Unity 的 Mixed Reality OpenXR 外掛程式](openxr-getting-started.md) 為這些裝置正確設定，然後再返回本教學課程
7. 如果您決定選擇 **Windows Mixed Reality** 外掛程式，請檢查所有方塊，並將 **深度提交模式** 設定為 **深度16位**

![醒目提示 Windows Mixed Reality 區段的 unity 編輯器中開啟專案設定視窗的螢幕擷取畫面](images/wmr-config-img-8.png)

### <a name="for-legacy-xr"></a>針對舊版 XR 

> [!CAUTION]
> Unity 2019 中的舊版 XR 已被取代，並已在 Unity 2020 中移除。

1. 從組建設定開啟 **播放機設定** ... **視窗** 並展開 [ **XR 設定** ] 群組
2. 在 [ **XR 設定** ] 區段中，選取 [ **支援的虛擬實境** 新增虛擬實境裝置] 清單
3. 將 **深度格式** 設定為 **16 位深度** ，並啟用 **深度緩衝區共用**
4. 將 **身歷聲轉譯模式** 設定為 **單一傳遞實例**
5. 如果您想要使用全像攝影的遠端處理，請選取 [不 **支援的 WSA** 全像 

![醒目提示 [播放程式設定] 區段的 [在 unity 編輯器中開啟專案設定] 視窗的螢幕擷取畫面](images/wmr-config-img-9.png)

### <a name="updating-the-manifest"></a>更新資訊清單

您的應用程式現在可以處理全像呈現和空間輸入。 不過，您的應用程式需要在其資訊清單中宣告適當的功能，以利用特定功能。 您可以前往 [ **Media Player 設定] > 設定通用 Windows 平臺 > 發佈設定 > 功能**，找到您的專案功能。 

建議您讓 Unity 中的資訊清單宣告將它們包含在您匯出的所有未來專案中。 針對混合現實啟用常用 Unity Api 的適用功能如下：

|  功能  |  需要功能的 Api | 
|----------|----------|
|  SpatialPerception  |  SurfaceObserver (在 HoloLens 上存取 [空間對應](../../design/spatial-mapping.md)網格) &mdash; *不需要一般空間追蹤耳機的功能* | 
|  攝像頭  |  PhotoCapture 和 VideoCapture | 
|  PicturesLibrary/VideosLibrary  |  PhotoCapture 或 VideoCapture，分別 (儲存已捕捉的內容時)  | 
|  麥克風  |  VideoCapture 捕獲音訊) 、DictationRecognizer、GrammarRecognizer 和 KeywordRecognizer 時的 ( | 
|  InternetClient  |  DictationRecognizer (並使用 Unity Profiler)  | 

### <a name="quality-settings"></a>品質設定

HoloLens 有行動類別 GPU。 如果您的應用程式是以 HoloLens 為目標，您會想要從已調整為最快效能的應用程式中品質設定開始，以確保其維持完整的畫面播放速率。  當您在開發過程中進一步開發之後，您可以考慮 upping 品質設定，以找出品質和效能的正確平衡： 

1. 選取 [ **編輯] > 專案設定 > 品質** 
2. 選取 [ **Windows Store**] 標誌底下的 **下拉式清單**   ，然後選取 [ **非常低**]。 您會知道當 Windows Store 資料行中的方塊和非常低的資料列中的方塊為綠色時，會正確套用設定 
3. 在 [ **遮蔽**]   區段中，選取 [停用 **陰影**] 

![醒目提示 [品質設定] 區段的 unity 編輯器中開啟的 [專案設定] 視窗螢幕擷取畫面](images/wmr-config-img-10.png)<br>
*Unity 品質設定*

## <a name="per-scene-settings"></a>每場景設定

### <a name="unity-camera-settings"></a>Unity 攝影機設定

若已核取 [ **虛擬事實** ]，則 [Unity 攝影機](camera-in-unity.md) 元件會處理 [標頭追蹤和 stereoscopic](../platform-capabilities-and-apis/rendering.md)轉譯。 這表示您不需要使用自訂相機來取代主要攝影機物件。

如果您的應用程式是以 HoloLens 為目標，則您必須變更一些設定，以針對裝置的透明顯示進行優化。 這些設定可讓您的全像全球內容顯示到實體世界：

1. **在階層中，選取****主要攝影機**
2. 在 [偵測 **器** ] 面板中，將轉換 **位置** 設定為 **0、0、0** ，讓使用者的標頭位置開始于 Unity world 來源。
3. 將 **清除旗標** 變更為 **純色**。
4. 將 **背景** 色彩變更為 **RGBA 0、0、0、0**。 在 HoloLens 中，黑色呈現為透明。
5. 變更 **裁剪平面-接近** [HoloLens 建議](camera-in-unity.md#clip-planes) 的 0.85 (計量) 。

![在 Unity 編輯器中開啟之偵測器索引標籤的螢幕擷取畫面](images/wmr-config-img-11.png)<br>
*Unity 攝影機設定*

> [!IMPORTANT]
> 如果您刪除並建立新的相機，請確定您的新相機已標記為 **MainCamera**。

## <a name="next-steps"></a>下一步

現在您的專案已經準備就緒，您可以開始開發混合現實體驗：

* 新增 [核心組建區塊](unity-development-overview.md#2-core-building-blocks)
* 查看可用 [的平臺功能和 api](unity-development-overview.md#3-advanced-features)
* 瞭解如何 [部署您的應用程式](../platform-capabilities-and-apis/using-visual-studio.md#)
* 使用[混合現實](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)模擬器

## <a name="see-also"></a>另請參閱
* [安裝工具](../install-the-tools.md)