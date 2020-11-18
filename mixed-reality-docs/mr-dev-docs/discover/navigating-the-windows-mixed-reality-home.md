---
title: 瀏覽 Windows Mixed Reality 住家
description: HoloLens 和 Windows Mixed Reality 的耳機共用了一個範例，可在您的環境中啟動、放置及操作應用程式和3D 模型， (是否為實體或數位) 。 瞭解如何在這兩種裝置類型上流覽 Windows Mixed Reality 首頁。
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: shell、os、platform、cliff 房子、房屋、home、環境、開始、開始功能表、首頁功能表、釘選、應用程式、啟動應用程式、放置應用程式、傳送、移動、流覽、混合現實耳機、虛擬實境耳機、何謂虛擬實境
ms.openlocfilehash: 590e52de7caacc515e703da19e9efdc0a2b9c535
ms.sourcegitcommit: 4f3ef057a285be2e260615e5d6c41f00d15d08f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2020
ms.locfileid: "94703444"
---
# <a name="navigating-the-windows-mixed-reality-home"></a>瀏覽 Windows Mixed Reality 住家

就像 Windows 電腦體驗從桌面開始一樣，Windows Mixed Reality 從首頁開始。 Windows Mixed Reality home 利用我們固有的能力來瞭解和流覽3D 地點。 使用 HoloLens，您的家庭是您的實體空間。 有了沉浸式耳機，您的家庭就是虛擬場所。

您的家裡也可以使用 [開始] 功能表來開啟和放置應用程式與內容。 您可以同時使用多個應用程式，以混合現實內容和多階段填滿您的家裡。 即使您重新開機裝置，您放在家裡的專案仍會留在那裡。

## <a name="start-menu"></a>開始功能表

![Microsoft HoloLens 上的 [開始] 功能表](images/start-500px.png)

[開始] 功能表包含：
* 系統資訊 (網路狀態、電池百分比、目前時間和磁片區) 
* Cortana (在沉浸式耳機上，一個開始磚;在 HoloLens 上，于 [開始) ] 頂端
* 釘選的應用程式
* 所有應用程式按鈕 (加號) 
* [混合現實 capture](../mixed-reality-capture.md)的相片和影片按鈕

藉由選取加號或減號按鈕，在釘選的應用程式和所有應用程式的視圖之間切換。 若要在 HoloLens 上開啟 [開始] 功能表，請使用 bloom 手勢。 在沉浸式耳機上，按下控制器上的 Windows 按鈕。

## <a name="launching-apps"></a>啟動應用程式

若要啟動應用程式，請在啟動時加以選取。 [開始] 功能表將會消失，而應用程式將會以放置模式開啟，例如2D 視窗或 [3d 模型](../distribute/implementing-3d-app-launchers.md)。

若要執行應用程式，您必須將它放在您的家裡：
1. 使用您的 [注視](../design/gaze-and-commit.md) 或控制器將應用程式放在您想要的位置。 它會自動調整大小和位置) 的 (，以符合您放置它的空間。
2. 使用 (HoloLens) 或 [選取] 按鈕 (沉浸式耳機) 來放置應用程式。 若要取消並取回 [開始] 功能表，請使用 bloom 手勢或 Windows 按鈕。

您可以使用[HOLOGRAPHICSPACE API](https://msdn.microsoft.com/library/windows/apps/windows.graphics.holographic.holographicspace.aspx)修改為桌面、行動裝置或 Xbox 建立的[2d 應用程式](../develop/porting-apps/building-2d-apps.md)，以混合現實的沉浸式應用程式執行。 沉浸式應用程式可讓使用者離開家裡，並獲得沉浸式體驗。 使用者可以使用 bloom 手勢 (HoloLens) 或按下其控制器上的 Windows 按鈕 (沉浸式耳機) ）來退回首頁。

您也可以透過應用程式對應用程式 API 或 Cortana 來啟動應用程式。

![Windows Mixed Reality 首頁中的應用程式](images/mixed-reality-home-500px.png)

## <a name="moving-and-adjusting-apps"></a>移動及調整應用程式

選取應用程式行上的 [ **調整** ]，以顯示移動、調整和旋轉混合現實內容的控制項。 當您完成時，請選取 [ **完成**]。

![在調整模式中的商店平板 (blue frame) 。 請注意， (top) 的應用程式行已變更為包含 [完成] 和 [移除] 按鈕。](images/adjust-500px.png)

不同的應用程式可能會有應用程式行上的其他選項。 例如，Microsoft Edge 具有 *滾動* 條、 *拖曳* 和 *縮放* 選項。 

![在 HoloLens 上執行之2D 應用程式的應用程式行](images/holobar-500px.png)

[ **上一頁** ] 按鈕會流覽回到先前在應用程式中看到的畫面。 當您到達應用程式中已顯示的體驗開始時，它會停止，而且不會流覽至其他應用程式。

## <a name="getting-around-your-home"></a>開始

使用 **HoloLens**，您可以在實際空間間移動，以在家裡四處移動。

有了 **沉浸式耳機**，您也可以在 playspace 中，于虛擬世界的類似區域內進行移動和四處移動。 若要在較長的距離間移動，您可以使用控制器上的操縱杆來幾乎「進行」，也可以使用 *遙傳* 來立即跳過較長的距離。

![Windows Mixed Reality 首頁中的遙傳](images/teleportation-500px.png)

**傳送：**
1. 帶出遙傳 reticle。
   * 使用 [動作控制器](../design/motion-controllers.md)：向前按下操縱杆，然後將它放在該位置。
   * 使用 Xbox 控制器：將左側的操縱杆向前按，然後將它放在該位置。
   * 使用滑鼠：按住滑鼠右鍵 (，然後在傳送) 時使用滾輪來旋轉您要面對的方向。
2. 將 reticle 放在您想要傳送的位置。
   * 使用 [動作控制器](../design/motion-controllers.md)：將您按住操縱杆的控制器 (傾斜) 來移動 reticle。
   * 使用 Xbox controller：使用您的 [注視](../design/gaze-and-commit.md) 來移動 reticle。
   * 使用滑鼠：移動滑鼠以移動 reticle。
3. 放開按鈕以傳送 reticle 的放置位置。

**到幾乎「逐步解說：」**
* 使用 [動作控制器](../design/motion-controllers.md)：按一下操縱杆並按住，然後以您想要的方向移動操縱杆。
* 使用 Xbox 控制器：按一下左側操縱杆並按住，然後以您想要的方向移動操縱杆。

## <a name="immersive-headset-input-support"></a>沉浸式耳機輸入支援

[Windows Mixed Reality 沉浸式耳機](immersive-headset-hardware-details.md) 支援多種輸入類型來導覽 Windows Mixed Reality 首頁。 HoloLens 不支援適用于導覽的配件輸入，因為您實際上會四處流覽並查看您的環境。 不過，HoloLens 支援與應用程式互動的 [輸入](hardware-accessories.md) 。

### <a name="motion-controllers"></a>運動控制器

最佳的 Windows Mixed Reality 體驗將會是 Windows Mixed Reality 的 [動作控制器](../design/motion-controllers.md) ，其支援使用耳機中的感應器來支援6種自由度的追蹤，而不需要外部攝影機或標記！

即將推出流覽命令。

### <a name="gamepad"></a>遊戲台
* **左方操縱杆：**
  * 按住左邊的操縱杆，以帶出 [遙傳](navigating-the-windows-mixed-reality-home.md#getting-around-your-home) reticle。
  * 以較小的增量，向左、向右或向左移動操縱杆。
  * 在左側的操縱杆上按一下並按住，然後以您想要的方向，將操縱杆移至「 [走」。](navigating-the-windows-mixed-reality-home.md#getting-around-your-home)
* 將 **右邊的操縱杆** 向左或向右移動，以旋轉45度的方向。
* 按下 **按鈕可** 執行選取動作，就像使用 [[點](../design/gaze-and-commit.md#composite-gestures) 一下] 手勢一樣。
* 按下 [ **節目表** ] 按鈕會顯示 [[開始] 功能表](navigating-the-windows-mixed-reality-home.md#start-menu) ，並如同 [bloom](../design/system-gesture.md#bloom) 手勢一樣。
* 按 **左和右觸發** 程式可讓您放大和縮小您要在家裡互動的2d 桌面應用程式。

### <a name="keyboard-and-mouse"></a>鍵盤和滑鼠

**注意：** 使用 **Windows 鍵 + Y** ，在控制電腦桌面與 Windows Mixed Reality 首頁之間切換滑鼠。

在 Windows Mixed Reality 首頁內：
* 按下滑鼠左鍵時，會執行選取動作，就像使用 [攻](../design/gaze-and-commit.md#composite-gestures)**點** 手勢一樣。
* 按住滑鼠 **右鍵** 按鈕會帶出 [遙傳](navigating-the-windows-mixed-reality-home.md#getting-around-your-home) reticle。
* 按下鍵盤上的 **Windows** 鍵會顯示 [ [開始] 功能表](navigating-the-windows-mixed-reality-home.md#start-menu) ，並如同 [bloom](../design/system-gesture.md#bloom) 手勢一樣。
* 在2D 桌面應用程式中 [撥雲見日](../design/gaze-and-commit.md) 時，您可以 **按一下** 滑鼠右鍵以選取， **按一下滑鼠右鍵** 以顯示操作功能表，然後使用 **滾輪** 滾動 (，就像在電腦的桌面) 一樣。

## <a name="cortana"></a>Cortana

[Cortana](../design/voice-input.md#hey-cortana) 是 Windows Mixed Reality 的個人助理，就像在 PC 和手機上一樣。 HoloLens 有內建的麥克風，但沉浸式耳機可能需要額外的硬體。 使用 Cortana 來開啟應用程式，重新開機您的裝置，並在線上尋找專案等等。 開發人員也可以選擇將 [Cortana 整合](https://dev.windows.com/cortana) 到他們的體驗。

您也可以使用語音命令來解決您的首頁。 例如，根據裝置) ，指向按鈕 ([gaze](../design/gaze-and-commit.md) ，視裝置而定，然後說「選取」。 其他聲音命令包括「Go 首頁」、「更大」、「更小」、「關閉」和「臉部我」。

## <a name="store-settings-and-system-apps"></a>儲存、設定和系統應用程式

Windows Mixed Reality 有一些內建的應用程式，例如：
* 取得應用程式和遊戲的 **Microsoft Store**
* **意見反應中樞** 提交有關系統和系統應用程式的意見反應
* **設定** 系統設定的設定 ([包括網路](../connecting-to-wi-fi-on-hololens.md) 和系統更新) 
* **Microsoft Edge** 流覽網站
* 觀看及分享相片和影片的 **相片**
* **校正** (hololens 僅) 用來調整目前使用者的 hololens 體驗
* **瞭解** (HoloLens) 或 **學習混合實境** (沉浸式耳機) 的手勢，以瞭解如何使用您的裝置
* **3D 檢視器** 使用混合的現實內容裝飾您的世界
* **混合實境入口** (desktop) 設定和管理您的沉浸式耳機，以及串流您在耳機中觀看的即時預覽，讓其他人看到。
* **影片和電視** 可用於觀看360影片和最新的電影和電視節目
* 適用于您所有虛擬助理需求的 **Cortana**
* **桌面** (沉浸式耳機) ，可在沉浸式耳機中觀看桌上型電腦監視器
* **檔案總管** 存取位於您裝置上的檔案和資料夾

## <a name="see-also"></a>另請參閱
* [應用程式檢視](../design/app-views.md)
* [運動控制器](../design/motion-controllers.md)
* [硬體配件](hardware-accessories.md)
* [HoloLens 的環境考量](../environment-considerations-for-hololens.md)
* [實作 3D 應用程式啟動器](../distribute/implementing-3d-app-launchers.md)
* [建立要在 Windows Mixed Reality 首頁中使用的3D 模型](../distribute/creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
