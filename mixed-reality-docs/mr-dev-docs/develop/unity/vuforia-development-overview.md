---
title: 使用 Unity 的 Vuforia
description: 使用 Vuforia 在 Unity 中建立 Windows Mixed Reality 應用程式。
author: thetuvix
ms.author: alexturn
ms.date: 12/20/2019
ms.topic: article
keywords: Vuforia、標記、座標、參考的框架、追蹤、混合現實耳機、windows mixed reality 耳機、虛擬實境耳機、unity、HoloLens、裝置追蹤、效能模式、Vuforia 開發人員入口網站
ms.openlocfilehash: 1a21f4bb441a1ab0706b5916feaac0d691486626
ms.sourcegitcommit: 7160843723ccd6567490e2f4222219603f184d76
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2021
ms.locfileid: "114232168"
---
# <a name="using-vuforia-engine-with-unity"></a>搭配使用 Vuforia 引擎與 Unity

Vuforia 引擎帶來了 HoloLens 的重要功能–將 AR 體驗連接到環境中的特定映射和物件的能力。 您可以使用這項功能，在產業企業的機械上重迭引導式逐步指示，或將數位功能和體驗新增至實體產品或遊戲。

Vuforia 引擎提供廣泛的功能和目標，讓您的 AR 開發程式更有彈性。 其中一項最新的功能 Vuforia 模型目標，是商業和產業使用的主要功能。 模型目標可讓應用程式辨識實體物件（例如機器、汽車或玩具），並根據 CAD 或數位3D 模型來進行追蹤。 針對產業用途，這項功能可以提供元件工作者和服務技術人員使用 AR 工作指示，以及在工廠或在現場推出的程式指引。

您可以輕鬆地在 Unity 中設定適用于手機和平板電腦的現有 Vuforia 引擎應用程式，以在 HoloLens 上執行。 您甚至可以使用 Vuforia 引擎，讓新的 HoloLens 應用程式 Windows 10 平板電腦，例如 Surface Pro 和 Surface Book。


## <a name="get-the-tools"></a>取得工具

[安裝建議](../install-the-tools.md)的 Visual Studio 和 unity 版本，然後設定 Unity 以使用 Visual Studio 和慣用的 IDE 和編譯器。 

安裝 Unity 時，請務必安裝「Windows 存放區 IL2CPP 腳本後端」。

新增 Vuforia 引擎封裝[，如下所述。](https://library.vuforia.com/content/vuforia-library/en/articles/Solution/vuforia-engine-package-hosting-for-unity.html)

## <a name="getting-started-with-vuforia-engine"></a>開始使用 Vuforia 引擎

學習 Vuforia 引擎和 HoloLens 的最佳起點是 Unity 資產存放區) 提供的[Vuforia 引擎 HoloLens 範例](https://assetstore.unity.com/packages/templates/packs/vuforia-hololens-sample-101553) (。 此範例會提供完整的 HoloLens 專案，包括可部署至 HoloLens 的預先設定幕後。

幕後顯示如何使用 Vuforia 映射目標辨識影像，並在 HoloLens 體驗中以數位內容加以增強。 Vuforia 引擎 HoloLens 範例也包含顯示模型目標和 VuMarks 在 HoloLens 上使用方式的場景。 您可以輕鬆地在幕後替換成您自己的內容，以實驗如何建立使用 Vuforia 引擎的 HoloLens 應用程式。



## <a name="configuring-a-vuforia-app-for-hololens"></a>針對 HoloLens 設定 Vuforia 應用程式

開發 HoloLens 的 Vuforia 引擎應用程式基本上與開發其他裝置的 Vuforia 引擎應用程式相同。 接著，您可以套用組建設定和設定，如下一節所述。 這就是讓 Vuforia 引擎使用 HoloLens 空間對應和位置追蹤系統所需的一切。

## <a name="build-and-run-the-vuforia-engine-sample-for-hololens"></a>建立並執行 HoloLens 的 Vuforia 引擎範例
1.  從 Unity 資產存放區下載[HoloLens 的 Vuforia 引擎範例](https://assetstore.unity.com/packages/templates/packs/vuforia-hololens-sample-101553)
2.  套用適用于 [電源和效能的建議 Unity 引擎選項](performance-recommendations-for-unity.md)
3.  將範例場景新增至組建中的 **場景** **。**
4.  在 [**組建設定**] 中，按一下 [**新增開啟場景**] 按鈕，將組建平臺切換至 **UWP** 。
![image](https://user-images.githubusercontent.com/45470042/89573103-173daa80-d7f8-11ea-9284-931a7b6c913d.png)
5.  選取 [**播放設定**] 按鈕。  
   * 選取 **UWP** 圖示，然後展開 [ **XR 設定** 區段。
   * 確定已啟用 **支援的虛擬事實** 。    
   * 在 **虛擬實境 sdk** 下，確定：
     * **視窗混合的現實** 會包含在清單中，並啟用 **深度緩衝區** 共用。 
     * **深度格式** 會設定為 **16 位的深度。** 
   * 確定身歷聲轉譯 **模式** 設定為 [ **單一傳遞實例]。**
6.  展開 [**發行設定**] 區段。
   * 在 [**功能**] 底下，**確定已選取**[**網際網路用戶端**]、[網路攝影機]、[麥克風] 和 [
   * **注意：** 只有在您想要使用 SURFACE Observer API 時，才應該選取 >spatialperception。
   * 在 [ **支援的裝置系列**] 底下， **確定已選取** [全像]。 
7.  展開 [ **解析和展示** ] 區段。
   * 停 **用在背景執行** 時，Vuforia 引擎會在應用程式進入背景時暫停，並可在應用程式繼續時再次存取相機。 
   * 在 [ **預設方向** ] 下拉式清單中，確定已選取 [ **橫向左方** ]。
8.  返回 **組建設定** 視窗，然後選取 [**組建**] 以產生 Visual Studio 專案。
9.  從 Visual Studio 建立可執行檔，並將它安裝在您的 HoloLens 上。

## <a name="the-vuforia-developer-portal"></a>Vuforia 開發人員入口網站

如果開發人員想要使用 Vuforia 引擎和 HoloLens 來建立自己的 AR 體驗，應該在[developer.vuforia.com](https://developer.vuforia.com/)的 Vuforia 開發人員入口網站上註冊。 在入口網站中，開發人員可以存取 [Vuforia Engine 論壇](https://developer.vuforia.com/forum) ，讓他們可以加入社區討論、包含有關所有 Vuforia 引擎功能的深入檔的文檔 [庫](https://library.vuforia.com/) ，以及可供使用者建立自己自訂目標的 [Vuforia 目標管理員](https://developer.vuforia.com/target-manager) 。 開發人員也可以使用 [Vuforia 授權管理員](https://developer.vuforia.com/license-manager)來註冊免費的開發人員授權。

## <a name="device-tracking-with-vuforia"></a>使用 Vuforia 進行裝置追蹤

[裝置追蹤](https://library.vuforia.com/features/environments/device-tracker-overview.html) 會維持追蹤的時間，即使目標已不在查看中也一樣。 啟用位置裝置追蹤器時，它會自動啟用所有目標。 針對 HoloLens 的應用程式，會在 Unity 中自動啟動位置裝置追蹤器。

Vuforia 引擎會自動從相機追蹤和 HoloLens 的空間追蹤 e-fuses 姿勢，以提供穩定的目標，而不受相機是否看到目標的影響。

因為此程式會自動處理，所以開發人員不需要任何程式設計。


**以下是此程式的高階描述：**
1. Vuforia 的目標追蹤器可識別目標
2. 接著會初始化目標追蹤
3. 系統會分析目標的位置和旋轉，以針對 HoloLens 提供健全的姿勢估計
4. Vuforia 引擎會將目標的姿勢轉換成 HoloLens 空間對應座標空間
5. 如果目標已不在查看中，HoloLens 會過度追蹤。 當您再次查看目標時，Vuforia 會繼續正確地追蹤影像和物件。

偵測到但不再顯示的目標會回報為 EXTENDED_TRACKED。 在這些情況下，在所有目標上使用的 DefaultTrackableEventHandler 腳本會繼續呈現增強的內容。 開發人員可以藉由執行自訂可追蹤事件處理常式腳本來控制這項行為。

## <a name="performance-mode-with-vuforia-engine"></a>具有 Vuforia 引擎的效能模式 

您可以透過 Vuforia 引擎來管理 HoloLens 的效能，以達到範圍 AR 的效能，並減少 CPU 上的工作負載。 Vuforia 引擎提供可選取的三種模式：預設值、優化速度，以及優化品質。 

*   MODE_OPTIMIZE_SPEED 可讓您將 HoloLens 裝置上的工作負載降到最低，並非常適合用來擴充 AR 體驗。 建議在應用程式正在追蹤靜態物件/目標的情況下使用。
*   MODE_DEFAULT 是標準模式，可在大部分的情況下使用。
*   MODE_OPTIMIZE_QUALITY 更適合用來追蹤您希望挑選的可移動目標或模型目標。

**設定模式**

若要變更 Unity 中的效能模式，請流覽至 Vuforia Configuration (Ctrl + Shift + V/Cmd + Shift + V) ，其位於 ARCamera GameObject 的元件中。 
*   選取 [相機裝置模式] 的下拉式功能表，然後選取三個選項的其中一個。


## <a name="see-also"></a>另請參閱
* [安裝工具](../install-the-tools.md)
* [座標系統](../../design/coordinate-systems.md)
* [空間對應](../../design/spatial-mapping.md)
* [Unity 中的相機](camera-in-unity.md)
* [匯出和建置 Unity Visual Studio 解決方案](exporting-and-building-a-unity-visual-studio-solution.md)
* [Vuforia 檔：使用 Vuforia 引擎進行 Windows 10 開發的開始使用](https://library.vuforia.com/articles/Training/Getting-Started-with-Vuforia-for-Windows-10-Development.html)
* [Vuforia 檔：在 Unity 中使用 Vuforia 引擎開始使用](https://library.vuforia.com/articles/Training/getting-started-with-vuforia-in-unity.html)
* [Vuforia 檔：使用 Unity 中的 HoloLens 範例](https://library.vuforia.com/articles/Solution/Working-with-the-HoloLens-sample-in-Unity.html)
* [Vuforia 檔： Vuforia 中的裝置追蹤](https://library.vuforia.com/features/environments/device-tracker-overview.html)
* [Vuforia 檔：畫面播放速率和效能優化](https://library.vuforia.com/content/vuforia-library/en/articles/Solution/Framerate-Optimization-for-Mixed-Reality-Apps.html)
