---
title: MR 基本 100-開始使用 Unity
description: 瞭解如何建立您的第一個基本 mixed reality "hello world" 應用程式。
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: mixed reality、Windows Mixed Reality、HoloLens、沉浸、vr、mr、入門、全息圖、學院、教學課程
ms.openlocfilehash: b2992f59970aaba44505d64de06e4ea57f400e1b
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2020
ms.locfileid: "91680676"
---
# <a name="mr-basics-100-getting-started-with-unity"></a>MR Basics 100：開始使用 Unity

>[!IMPORTANT]
>混合實境學院教學課程的設計是以 HoloLens (第 1 代) 和混合實境沉浸式頭戴裝置為準。  因此，對於仍在尋找這些裝置開發指引的開發人員而言，我們覺得這些教學課程很重要。  這些教學課程 **_不會_** 使用用於 HoloLens 2 的最新工具組或互動進行更新。  系統會保留這些資訊，以繼續在支援的裝置上運作。 已針對 HoloLens 2 公佈[一系列新的教學課程](mrlearning-base.md)。

本教學課程將逐步引導您建立以 Unity 建立的基本混合現實應用程式。

## <a name="device-support"></a>裝置支援

<table>
<tr>
<th>課程</th><th style="width:150px"> <a href="../../../hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">沉浸式頭戴裝置</a></th>
</tr><tr>
<td>MR Basics 100：開始使用 Unity</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="prerequisites"></a>Prerequisites

* [已安裝正確工具](../../install-the-tools.md)的 Windows 10 電腦。

## <a name="chapter-1---create-a-new-project"></a>第1章-建立新專案

>[!VIDEO https://www.youtube.com/embed/2L5IFO0hnYA]

若要使用 Unity 建立應用程式，您必須先建立專案。 此專案會組織成幾個資料夾，最重要的就是您的資產資料夾。 此資料夾會保存您從數位內容建立工具（例如 Maya、最大電影4D 或 Photoshop）匯入的所有資產、使用 Visual Studio 或您最愛的程式碼編輯器建立的所有程式碼，以及當您在編輯器中撰寫場景、動畫和其他 Unity 資產類型時，Unity 所建立的任何內容檔案數目。

若要建立及部署 UWP 應用程式，Unity 可以將專案匯出為 Visual Studio 方案，其中包含所有必要的資產和程式碼檔案。

1. 啟動 Unity
2. 選取 [ **新增** ]
3. 輸入 (的專案名稱，例如 "MixedRealityIntroduction" ) 
4. 輸入儲存專案的位置
5. 確定已選取 **3d** 切換
6. 選取 [ **建立專案** ]

恭喜，您現在已設定好開始使用您的混合現實自訂。

## <a name="chapter-2---setup-the-camera"></a>第2章-設定相機

>[!VIDEO https://www.youtube.com/embed/eP1ZwB4wSNA]

Unity 主要攝影機會處理前端追蹤和 stereoscopic 轉譯。 主要攝影機有一些變更，可將其用於混合現實。

1. 選取檔案 > 新場景

首先，如果您想像使用者的開始位置是 ( **X** ：0， **Y** ：0， **Z** ： 0) ，將會比較容易配置您的應用程式。 因為主要攝影機正在追蹤使用者的標頭移動，所以可以設定主要攝影機的開始位置來設定使用者的開始位置。

1. 選取 **[階層** ] 面板中的 [ **主要攝影機** ]
2. 在 [偵測 **器** ] 面板中，尋找 [ **轉換** ] 元件，並將 **位置** 從 ( **X** ：0， **Y** ：1， **Z** ：-10) 變更為 ( **X** ：0， **y** ：0， **Z** ： 0) 

其次，預設攝影機背景需要一些思考。

**針對 HoloLens 應用程式** ，真實世界應該會出現在相機呈現的所有專案，而不是 Skybox 材質的後方。

1. 當 **主要攝影機** 仍在 [階層] **面板中** 選取時，請在 [ **檢查** ] 面板中尋找 **相機** 元件，並將 [ **清除旗標** ] 下拉式清單從 [ **Skybox** ] 變更為 [ **純色** ]。
2. 選取 **背景** 色彩選擇器，並將 **RGBA** 值變更為 (0、0、0、0) 

**針對以沉浸式耳機為目標的混合現實應用程式** ，我們可以使用 Unity 提供的預設 Skybox 材質。

1. 當 **主要攝影機** 仍在 [階層] **面板中** 選取時，請在 [偵測 **器** ] 面板中尋找 **相機** 元件，並保留 [ **清除旗標** ] 下拉式清單以進行 **Skybox** 。

第三，讓我們考慮 Unity 中的近接裁剪平面，並防止在使用者接近使用者的情況下，將物件呈現太接近使用者眼睛。

**針對 hololens 應用程式** ，接近的裁剪平面可以設定為 [hololens 建議](../camera-in-unity.md#clip-planes) 的0.85 計量。

1. 當 **主要攝影機** 仍在 [階層] **面板中** 選取時，請在 [偵測 **器** ] 面板中尋找 **相機** 元件，並將 **接近的剪輯平面** 欄位從預設的 **0.3** 變更為 HoloLens 建議的 **0.85** 。

**針對以沉浸式耳機為目標的混合現實應用程式** ，我們可以使用 Unity 提供的預設設定。

1. 當 **主要攝影機** 仍在 [階層] **面板中** 選取時，請在 [偵測 **器** ] 面板中尋找 **相機** 元件，並將 **接近的裁剪平面** 欄位保留為預設值 **0.3** 。

最後，讓我們來節省目前的進度。 若要儲存場景變更，請選取 [檔案] **> [另存場景** ]、將場景命名為 **主要** ，然後選取 [ **儲存** ]。

## <a name="chapter-3---setup-the-project-settings"></a>第3章-設定專案設定

>[!VIDEO https://www.youtube.com/embed/ItRoiXccC0g]

在本章中，我們將設定一些 Unity 專案設定，以協助我們以 Windows 全像開發版 SDK 為目標。 我們也會為應用程式設定一些品質設定。 最後，我們會確保組建目標設定為通用 Windows 平臺。

### <a name="unity-performance-and-quality-settings"></a>Unity 效能和品質設定

**適用于 HoloLens 的 Unity 品質設定**

![適用于 HoloLens 的 Unity 品質設定](images/qualitysettings.png)

由於在 HoloLens 上維持高幀率很重要，我們想要調整品質設定以獲得最快的效能。 如需更詳細的效能資訊，請瞭解 [Unity 的效能建議](../performance-recommendations-for-unity.md)。

1. 選取 [ **編輯] > 專案設定 > 品質**
2. 選取 **通用 Windows 平臺** 標誌底下的 **下拉式清單** ，然後選取 [ **非常低** ]。 當通用 Windows 平臺資料行中的方塊和 **非常低** 的資料列都是綠色時，您將會知道此設定已正確套用。

**對於以 pixels occluded 顯示為目標的混合現實應用程式** ，您可以將品質設定保留為其預設值。

### <a name="target-windows-10-sdk"></a>目標 Windows 10 SDK

**以 Windows 全像攝影 SDK 為目標**

![以 Windows 全像攝影 SDK 為目標](../images/xrsettings.png)

我們需要讓 Unity 知道我們想要匯出的應用程式應該建立一個 [沉浸式視圖](../../../design/app-views.md) ，而不是2d 視圖。 若要這麼做，請在以 Windows 10 SDK 為目標的 Unity 上啟用虛擬實境支援。

1. 移至 **> Player 的 [編輯 > 專案設定** ]。
2. 在 [播放程式設定] 的 [偵測 **器] 面板** 中，選取 **通用 Windows 平臺** 圖示。
3. 展開 [XR 設定] 群組。
4. 在 [轉譯] 區段中核取 [支援虛擬實境] 核取方塊，以新增 [虛擬實境 SDK] 清單。
5. 確認 **Windows Mixed Reality** 出現在清單中。 如果沒有，請選取清單底部的 **+** 按鈕，然後選擇 [Windows Mixed Reality]。

>[!NOTE]
>如果您看不到 **通用 Windows 平臺** 圖示，請再次檢查以確定您已在安裝期間選取通用 Windows 平臺組建支援。 如果沒有，您可能需要以正確的 Windows 安裝重新安裝 Unity。

取得所有專案設定的絕佳工作。 接下來，我們要新增一張全像

## <a name="chapter-4---create-a-cube"></a>第4章-建立 cube

>[!VIDEO https://www.youtube.com/embed/qKcK1Yuj-HQ]

在 Unity 專案中建立 cube 就像是在 Unity 中建立任何其他物件一樣。 將 cube 放在使用者的前方很容易，因為 Unity 的座標系統對應到真實世界，其中一個在 Unity 中的計量大約是真實世界中的一個計量。

1. **在 [階層] 面板左上** 角，選取 [ **建立** ] 下拉式清單，然後選擇 [ **3d 物件 > Cube** ]。
2. **在 [階層] 面板中** 選取新建立的 **Cube**
3. 在偵測 **器** 中找出 **轉換** 元件，並將 **位置** 變更為 ( **X** ：0， **Y** ：0， **Z** ： 2) 。 *這會將 cube 2 計量置於使用者開始位置的前方。*
4. 在 **轉換** 元件中，將 **旋轉** 變更為 ( **X** ：45、 **Y** ：45、 **Z** ： 45) ，然後將 **比例** 變更為 ( **X** ：0.25， **y** ：0.25， **Z** ： 0.25) 。 *這會將 cube 調整為0.25 計量。*
5. 若要儲存場景變更，請選取 [檔案] **> 儲存場景** ]。

## <a name="chapter-5---verify-on-device-from-unity-editor"></a>第5章-從 Unity 編輯器確認裝置

>[!VIDEO https://www.youtube.com/embed/vmCfiIdRb6Q]

既然我們已建立了 cube，現在就可以快速檢查裝置。 您可以直接從 Unity 編輯器內進行此作業。

### <a name="initial-setup"></a>初始設定

1. 在您的開發電腦上，于 Unity 的 [ **組建設定** ] 視窗中開啟 [檔案] >。
2. 將 **平臺** 變更為 **通用 Windows 平臺** ，然後按一下 [ **切換平臺** ]

### <a name="for-hololens-use-unity-remoting"></a>針對 HoloLens，請使用 Unity Remoting

1. 在 HoloLens 上，安裝並執行可從 Windows 市集中取得的全像 [遠端播放機](../../platform-capabilities-and-apis/holographic-remoting-player.md)。 在裝置上啟動應用程式，它會進入等候狀態，並顯示裝置的 IP 位址。 記下 IP。
2. 開啟 **Window > XR >** 全像全像模擬。
3. 將 **模擬模式** 從 [ **無** ] 變更為 [ **遠端] 至 [裝置** ]。
4. 在 [ **遠端電腦** ] 中，輸入您先前記下的 HoloLens IP 位址。
5. 按一下 [ **連接** ]。
6. 確定連線 **狀態** 變更為綠色 **已連線** 。
7. 現在您可以在 Unity 編輯器中按一下 [ **播放** ]。

您現在可以在 [裝置] 和編輯器中看到 cube。 您可以像在編輯器中執行應用程式一樣暫停、檢查物件和進行偵錯工具，因為這基本上是發生的情況，但在主機電腦與裝置之間的網路上來回傳輸了影片、音訊和裝置輸入。

### <a name="for-other-mixed-reality-supported-headsets"></a>適用于其他 mixed reality 支援的耳機

1. 使用 USB 纜線和 HDMI 或顯示器埠纜線，將耳機連接到您的開發電腦。
2. 啟動 **混合實境入口** ，並確定您已完成第一次執行體驗。
3. 您現在可以從 Unity 按下 [播放] 按鈕。

您現在可以在混合現實耳機和編輯器中看到 cube 轉譯。

## <a name="chapter-6---build-and-deploy-to-device-from-visual-studio"></a>第6章-從 Visual Studio 建立並部署至裝置

>[!VIDEO https://www.youtube.com/embed/USSu8yHUdbk]

我們現在已準備好要編譯專案，以 Visual Studio 並部署至目標裝置。

### <a name="export-to-the-visual-studio-solution"></a>匯出至 Visual Studio 解決方案

1. 開啟 [檔案 **> 組建設定** ] 視窗。
1. 按一下 [ **新增開啟場景** ] 以加入場景。
1. 將 **平臺** 變更為 **通用 Windows 平臺** ，然後按一下 [ **切換平臺** ]。
1. 在 **通用 Windows 平臺** 設定] 中，確定 [ **SDK** ] 是 [ **通用] 10** 。
1. 針對目標裝置，請離開 **任何裝置** 以進行 pixels occluded 顯示或切換至 **HoloLens** 。
1. **UWP 組建類型** 應該是 **D3D** 。
1. **UWP SDK** 可以保留 **最新的安裝** 。
1. 按一下 [建置]  。
1. 在 [檔案瀏覽器] 中，按一下 [ **新增資料夾** ]，然後將資料夾命名為 **"App"** 。
1. 選取 **應用程式** 資料夾，然後按一下 [ **選取資料夾** ] 按鈕。
1. 當 Unity 完成建立時，將會出現 Windows 檔案總管視窗。
1. 在 [檔案瀏覽器] 中開啟 **應用程式** 資料夾。
1. 在此範例中， (MixedRealityIntroduction 開啟產生的 Visual Studio 方案) 

### <a name="compile-the-visual-studio-solution"></a>編譯 Visual Studio 解決方案

最後，我們將編譯匯出的 Visual Studio 解決方案、加以部署，然後在裝置上試用。

1. 使用 Visual Studio 中的頂端工具列，將目標從 **Debug** 變更為 **Release** ，以及從 **ARM** 變更為 **X86** 。

部署至裝置與模擬器的指示不同。 遵循符合您設定的指示進行。

### <a name="deploy-to-mixed-reality-device-over-wi-fi"></a>透過 Wi-fi 部署至混合現實裝置

1. 按一下 [ **本機電腦** ] 按鈕旁的箭號，然後將部署目標變更為 [ **遠端電腦** ]。
2. 輸入您的混合現實裝置的 IP 位址，並將 **驗證模式** 變更為適用于 HoloLens 和 **Windows** 的通用 (未加密通訊協定) 的其他裝置。
3. 按一下 [ **Debug] > 啟動但不進行調試** 。

**針對 HoloLens** ，如果這是您第一次部署至您的裝置，您必須 [使用 Visual Studio](../../platform-capabilities-and-apis/using-visual-studio.md)配對。

### <a name="deploy-to-mixed-reality-device-over-usb"></a>透過 USB 部署至混合現實裝置

確定您已透過 USB 纜線插入裝置。

1. 若 **為 HoloLens** ，請按一下 [ **本機電腦** ] 按鈕旁的箭號，然後將部署目標變更為 [ **裝置** ]。
2. **針對連接到您電腦的 pixels occluded 裝置** ，將設定保留在 [本機電腦]。 確定您的 **混合實境入口** 正在執行。
3. 按一下 [ **Debug] > 啟動但不進行調試** 。

### <a name="deploy-to-emulator"></a>部署至模擬器

1. 按一下 [ **裝置** ] 按鈕旁邊的箭號，然後從下拉式清單中選取 [ **HoloLens 模擬器** ]。
2. 按一下 [ **Debug] > 啟動但不進行調試** 。

### <a name="try-out-your-app"></a>試用您的應用程式

現在已部署您的應用程式，請嘗試在整個 cube 周圍移動，然後觀察它是否存在於世界的前方。

## <a name="see-also"></a>另請參閱

* [Unity 開發概觀](../unity-development-overview.md)
* [使用 Unity 和 Visual Studio 的最佳作法](../best-practices-for-working-with-unity-and-visual-studio.md)
* [MR Basics 101](holograms-101.md)
* [MR Basics 101E](holograms-101e.md)
