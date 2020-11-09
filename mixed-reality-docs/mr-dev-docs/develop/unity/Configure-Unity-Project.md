---
title: 針對 Windows Mixed Reality 設定新的 Unity 專案
description: 針對 Windows Mixed Reality 設定 Unity 專案的指示
author: thetuvix
ms.author: alexturn
ms.date: 07/29/2020
ms.topic: article
keywords: Unity，混合現實，開發，使用者入門，新專案
ms.openlocfilehash: f1465dcb31718b9d3faeb64d24e33d9f9ffeb7cc
ms.sourcegitcommit: 83c9373fe5b2e07cdab921b6cab3fdd418307003
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/09/2020
ms.locfileid: "94386214"
---
# <a name="configure-a-new-unity-project-for-windows-mixed-reality"></a>針對 Windows Mixed Reality 設定新的 Unity 專案 

## <a name="overview"></a>概觀

Windows Mixed Reality (WMR) 是在 Windows 10 作業系統中引進的 Microsoft 平臺。 WMR 平臺可讓您建立應用程式，以在全像全像 VR 的顯示裝置上呈現數位內容。

設定 WMR 時，您可以採用兩個路徑。 第一個選項是安裝 [混合現實工具組 (MRTK) ](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html)，這會自動設定 WMR 環境。 第二個選項是手動變更一些 Unity 設定，以使用 WMR 進行滾動。 

> [!NOTE]
> 您稍後可以隨時匯入 MRTK，如此一來，就不會再進行手動路由。

如果您選擇 WMR 手動設定，您需要變更的設定會分成兩種類別：個別專案和每一場景。

## <a name="per-project-settings"></a>每個專案的設定

您需要變更 WMR 的第一個設定是專案平臺： 
1. 選取 [檔案 **> 組建設定 ...** ]
2. 在 [平臺] 清單中選取 **通用 Windows 平臺** ，然後按一下 [ **切換平臺** ]
3. 將 **SDK** 設定為 **通用 10**
4. 將 **目標裝置** 設定為 **任何裝置** 以支援沉浸式耳機或切換至 **HoloLens**
5. 將 **組建類型** 設定為 **D3D**
6. 將 **UWP SDK** 設定為 **最新安裝**

<img src="images/unity-uwp-settings.png" width="550px" alt="Unity XR Settings">
*Unity XR 設定*

當平臺設定正確之後，您需要讓 Unity 知道您的應用程式應該在匯出時建立一個 [沉浸式視圖](../../design/app-views.md) ，而不是2d 視圖：
1. 從 [ **組建設定 ...** ] 視窗中，開啟 [ **播放玩家設定** ]。
2. 選取 [ **通用 Windows 平臺** ] 索引標籤的設定，並展開 [ **XR 設定** ] 群組
3. 在 [ **XR 設定** ] 區段中，核取 [ **虛擬實境支援** ] 核取方塊，以新增 **虛擬實境裝置** 清單。
4. 在 [ **XR 設定** ] 群組中，確認 **[Windows Mixed Reality]** 列為受支援的裝置。  (此選項可能會顯示為舊版 Unity 中的 **Windows 全息** 版) 

![Unity UWP 設定](images/xrsettings.png)<br>
*Unity XR 設定*

### <a name="updating-the-manifest"></a>更新資訊清單

您的應用程式現在可以處理全像呈現和空間輸入。 不過，您的應用程式需要在其資訊清單中宣告適當的功能，以利用特定功能。 您可以前往 [ **播放程式設定] > 設定通用 Windows 平臺 > 發佈設定 > 功能** ，找出您的專案功能。 

建議您讓 Unity 中的資訊清單宣告將它們包含在您匯出的所有未來專案中。 針對混合現實啟用常用 Unity Api 的適用功能如下：

|  功能  |  需要功能的 Api | 
|----------|----------|
|  SpatialPerception  |  SurfaceObserver (在 HoloLens 上存取 [空間對應](../../design/spatial-mapping.md)網格) &mdash; *不需要一般空間追蹤耳機的功能* | 
|  攝像頭  |  PhotoCapture 和 VideoCapture | 
|  PicturesLibrary/VideosLibrary  |  PhotoCapture 或 VideoCapture，分別 (儲存已捕捉的內容時)  | 
|  麥克風  |  VideoCapture 捕獲音訊) 、DictationRecognizer、GrammarRecognizer 和 KeywordRecognizer 時的 ( | 
|  InternetClient  |  DictationRecognizer (並使用 Unity Profiler)  | 

### <a name="quality-settings"></a>品質設定

HoloLens 有行動類別 GPU。 如果您的應用程式是以 HoloLens 為目標，您會想要調整應用程式中的品質設定以獲得最快的效能，以確保它會維持完整的畫面播放速率：
1. 選取 [ **編輯] > 專案設定 > 品質**
2. 選取 [ **Windows Store** ] 標誌底下的 **下拉式清單** ，然後選取 [ **非常低** ]。 您會知道當 Windows Store 資料行中的方塊和 **非常低** 的資料列中的方塊為綠色時，會正確套用設定。

![Unity 品質設定](images/getting-started-unity-quality-settings.jpg)<br>
*Unity 品質設定*

## <a name="per-scene-settings"></a>每場景設定

### <a name="unity-camera-settings"></a>Unity 攝影機設定

若已核取 [ **虛擬事實** ]，則 [Unity 攝影機](camera-in-unity.md) 元件會處理 [標頭追蹤和 stereoscopic](../platform-capabilities-and-apis/rendering.md)轉譯。 這表示您不需要使用自訂相機來取代主要攝影機物件。

如果您的應用程式是以 HoloLens 為目標，則您必須變更一些設定，以針對裝置的透明顯示進行優化。 這些設定可讓您的全像全球內容顯示到實體世界：
1. **在階層中，選取****主要攝影機**
2. 在 [偵測 **器** ] 面板中，將轉換 **位置** 設定為 **0、0、0** ，讓使用者的標頭位置開始于 Unity world 來源。
3. 將 **清除旗標** 變更為 **純色** 。
4. 將 **背景** 色彩變更為 **RGBA 0、0、0、0** 。 在 HoloLens 中，黑色呈現為透明。
5. 變更 **裁剪平面-接近** [HoloLens 建議](camera-in-unity.md#clip-planes) 的 0.85 (計量) 。

![Unity 攝影機設定](images/Unitycamerasettings.png)<br>
*Unity 攝影機設定*

> [!IMPORTANT]
> 如果您刪除並建立新的相機，請確定您的新相機已標記為 **MainCamera** 。

## <a name="see-also"></a>另請參閱
* [MRTK-安裝指南 (GitHub) ](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html)
* [MRTK-檔首頁 (GitHub) ](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
* [安裝工具](../install-the-tools.md)
* [Unity 開發總覽](unity-development-overview.md)
