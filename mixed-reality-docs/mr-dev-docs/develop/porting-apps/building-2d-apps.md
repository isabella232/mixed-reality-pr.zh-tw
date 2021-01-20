---
title: 更新 Windows Mixed Reality 的 2D UWP 應用程式
description: 本文概述如何更新您現有的2D 通用 Windows 平臺應用程式，以在 HoloLens 和 Windows Mixed Reality 沉浸式耳機上執行。
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: 2D 應用程式、UWP、平面應用程式、HoloLens、沉浸式耳機、應用程式模型、上一頁按鈕、應用程式行、DPI、解析度、縮放、移植、HoloLens 1 代、HoloLens 2、混合現實耳機、windows mixed reality 耳機、遷移、Windows 10
ms.openlocfilehash: 2d6b03a8cca70ac2db810209263139ebdf3c22a7
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583536"
---
# <a name="updating-2d-uwp-apps-for-windows-mixed-reality"></a>更新 Windows Mixed Reality 的 2D UWP 應用程式

Windows Mixed Reality 可讓您的使用者看到全像是在實體和數位世界中的圖片。 在其核心中，您將沉浸式耳機配件附加至的 HoloLens 和桌上型電腦都是 Windows 10 裝置。 您可以在存放區中執行幾乎所有通用 Windows 平臺 (UWP) 應用程式作為2D 應用程式。

## <a name="creating-a-2d-uwp-app-for-mixed-reality"></a>為混合的現實建立 2D UWP 應用程式

將2D 應用程式帶入混合現實耳機的第一個步驟，是讓您的應用程式在桌面監視器上以標準2D 應用程式的形式執行。

### <a name="building-a-new-2d-uwp-app"></a>建立新的 2D UWP 應用程式

若要建立混合現實的新2D 應用程式，您可以建立標準2D 通用 Windows 平臺 (UWP) 應用程式。 應用程式不需要進行任何其他應用程式變更，就可以在混合現實中以平板的形式執行。

若要開始建立 2D UWP 應用程式，請參閱 [建立您的第一個應用程式](/windows/uwp/get-started/your-first-app) 文章。

### <a name="bringing-an-existing-2d-store-app-to-uwp"></a>將現有的2D 存放區應用程式帶入 UWP

如果您在存放區中已經有 2D Windows 應用程式，請確定它的目標是 Windows 10 通用 Windows 平臺 (UWP) 。 以下是您目前的 Store 應用程式可能會有的所有可能起點：
<br>

|  起點  |  AppX 資訊清單平臺目標  |  如何將此通用？ | 
|----------|----------|----------|
|  Windows Phone (Silverlight)  |  Silverlight 應用程式資訊清單 |  [遷移至 WinRT](/previous-versions/windows/apps/dn642486(v=vs.105)) | 
|  Windows Phone 8.1 通用  |  不包含平臺目標的 8.1 AppX 資訊清單  |  [將您的應用程式遷移至通用 Windows 平臺](/previous-versions/visualstudio/visual-studio-2015/misc/migrate-apps-to-the-universal-windows-platform-uwp) | 
|  Windows Store 8  |  8個不包含平臺目標的 AppX 資訊清單  |  [將您的應用程式遷移至通用 Windows 平臺](/previous-versions/visualstudio/visual-studio-2015/misc/migrate-apps-to-the-universal-windows-platform-uwp) | 
|  Windows Store 8.1 通用  |  不包含平臺目標的 8.1 AppX 資訊清單  |  [將您的應用程式遷移至通用 Windows 平臺](/previous-versions/visualstudio/visual-studio-2015/misc/migrate-apps-to-the-universal-windows-platform-uwp) | 

如果您目前有 2D Unity 應用程式在電腦上以 Win32 應用程式的形式建立 **，Mac & Linux 獨立** 組建目標上，請切換至 **通用 Windows 平臺** 的組建目標，以瞭解混合的實際情況。

我們會討論您可以使用 [以下](#publish-and-maintain-your-universal-app)的 Windows 全像裝置系列，將您的應用程式明確限制為 HoloLens 的方式。

### <a name="run-your-2d-app-in-a-windows-mixed-reality-immersive-headset"></a>在 Windows Mixed Reality 沉浸式耳機中執行2D 應用程式

如果您已將2D 應用程式部署至桌上型電腦，並在您的監視器上試用它，您就可以在沉浸式桌面耳機上試用！

請移至混合現實耳機內的 [開始] 功能表，然後從該處啟動應用程式。 Desktop shell 和全像全像全像一樣，都共用一組 UWP 應用程式，因此當您從 Visual Studio 部署之後，應用程式應該就已經存在。

## <a name="targeting-both-immersive-headsets-and-hololens"></a>以沉浸式耳機和 HoloLens 為目標

恭喜！ 您的應用程式現在使用 Windows 10 通用 Windows 平臺 (UWP) 。

您的應用程式現在可以在現今的 Windows 裝置上執行，例如桌上型、Mobile、Xbox、Windows Mixed Reality 沉浸式耳機、HoloLens 和未來的 Windows 裝置。 不過，若要實際將所有裝置設為目標，您必須確定您的應用程式是以 Windows 為目標。 通用裝置系列。

### <a name="change-your-device-family-to-windowsuniversal"></a>將您的裝置系列變更為 Windows 通用

現在，讓我們跳到您的 AppX 資訊清單，以確保您的 Windows 10 UWP 應用程式可以在 HoloLens 上執行：
* 使用 **Visual Studio** 開啟您的應用程式解決方案檔，然後流覽至應用程式套件資訊清單
* 以滑鼠右鍵按一下方案中的 **package.appxmanifest** 檔案，然後移至 [ **View Code** ]<br>
  ![方案總管中的 package.appxmanifest](images/openappxmanifest-500px.png)<br>
* 確定您的目標平臺為 Windows。 [相依性] 區段中的 [通用]
  ```
  <Dependencies>
    <TargetDeviceFamily Name="Windows.Universal" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10586.0" />
  </Dependencies>
  ```
* 救！

如果您沒有針對開發環境使用 Visual Studio，就可以在您選擇的文字編輯器中開啟 **AppXManifest.xml** ，以確保您的目標是 **Windows 通用** *y*。

### <a name="run-in-the-hololens-emulator"></a>在 HoloLens 模擬器中執行

現在，您的 UWP 應用程式是以 "Windows 通用" 為目標，讓我們建立您的應用程式，並在 [HoloLens 模擬器](../platform-capabilities-and-apis/using-the-hololens-emulator.md)中執行它。
* 請確定您 [已安裝 HoloLens 模擬器](../install-the-tools.md)。
* 在 Visual Studio 中，選取應用程式的 **x86** 組建設定

  ![Visual Studio 中的 x86 組建設定](../platform-capabilities-and-apis/images/x86setting.png)<br>
* 在 [部署目標] 下拉式功能表中，選取 [HoloLens 模擬器] 

  ![部署目標清單中的 HoloLens 模擬器](images/deployemulator-500px.png)<br>
* 選取 [ **Debug] > 開始調試** 程式，以部署您的應用程式並啟動偵錯工具。
* 模擬器將會啟動並執行您的應用程式。
* 使用鍵盤、滑鼠和 Xbox 控制器，將您的應用程式放在世界中以啟動。

  ![使用 UWP 範例載入 HoloLens 模擬器](images/hololensemulatorwithuwpsample-800px.png)<br>

### <a name="next-steps"></a>後續步驟

此時，可能會發生下列其中一種情況：
1. 您的應用程式將會顯示其啟動顯示，並在放置於模擬器之後開始執行！ 好極了！
2. 或者，在您看到適用于2D 全息圖的載入動畫之後，載入將會停止，而且您會在其啟動顯示畫面上看到您的應用程式。 這表示發生了錯誤，且會進行更多調查，以瞭解如何讓您的應用程式在混合現實生活中保持存留。

您將需要進行偵錯工具，以取得可能會在 HoloLens 上停止 UWP 應用程式的可能問題根源。

### <a name="running-your-uwp-app-in-the-debugger"></a>在偵錯工具中執行 UWP 應用程式

這些步驟將逐步引導您使用 Visual Studio 偵錯工具來偵測 UWP 應用程式。
* 如果您尚未這麼做，請在 Visual Studio 中開啟您的解決方案。 將目標變更為 **HoloLens 模擬器** ，並將組建設定變更為 **x86**。
* 選取 [ **Debug] > 開始調試** 程式，以部署您的應用程式並啟動偵錯工具。
* 使用滑鼠、鍵盤或 Xbox 控制器將應用程式放在世界各地。
* Visual Studio 現在應該會在應用程式程式碼中的某處中斷。
  - 如果您的應用程式不會因為發生未處理的錯誤而立即損毀或中斷偵錯工具，則請進行應用程式核心功能的測試階段，以確定一切都在執行且正常運作。 您可能會看到如下圖所示的錯誤 () 處理的內部例外狀況。 為了確保您不會錯過影響應用程式體驗的內部錯誤，請執行您的自動化測試和單元測試，以確定一切都如預期般運作。

![使用 UWP 範例載入的 HoloLens 模擬器顯示系統例外狀況](images/hololensemulatorwithuwpsampleexception-800px.png)

## <a name="update-your-ui"></a>更新您的 UI

現在您的 UWP 應用程式是在沉浸式耳機和 HoloLens 上以2D 全息圖的形式執行，接下來我們要確定它看起來美觀。 以下是要考量的一些事項：
* Windows Mixed Reality 將會以固定的解析度和 DPI （相當於853x480 有效的圖元）執行所有2D 應用程式。 請考慮您的設計是否需要依此規模進行調整，並查看下列設計指引，以改善您的 HoloLens 和沉浸式耳機體驗。
* Windows Mixed Reality [不支援](../../design/app-model.md) 2d 動態磚。 如果您的核心功能顯示動態磚上的資訊，請考慮將該資訊移回您的應用程式，或探索 [3d 應用程式啟動器](../../distribute/3d-app-launcher-design-guidance.md)。

### <a name="2d-app-view-resolution-and-scale-factor"></a>2D 應用程式視圖解析度和縮放因數

![從回應式設計](images/scale-500px.png)

Windows 10 將所有視覺效果設計從真實螢幕圖元移至 **有效的圖元**。 這表示，開發人員會依照 Windows 10 的人類介面指導方針來設計其 UI 以取得有效的圖元，而 Windows 調整可確保這些有效的圖元在裝置、解析度、DPI 等方面都是正確的大小。 如需詳細資訊，請參閱 MSDN 和此[組建簡報](https://video.ch9.ms/sessions/build/2015/2-63_Build_2015_Windows_Scaling.pptx)的這篇[絕佳閱讀](/windows/uwp/design/layout/screen-sizes-and-breakpoints-for-responsive-design)。

即使有獨特的能力可將世界各地的應用程式放在不同的距離，建議使用類似電視的觀賞距離，以產生最佳的可讀性，並與注視/手勢互動。 因此，Mixed Reality 首頁中的虛擬平板會在下列位置顯示您的平面 UWP 視圖：

**1280x720，150% DPI** (853x480 有效圖元) 

此解決方法有幾個優點：
* 此有效的圖元配置將與 tablet 或 small desktop 具有相同的資訊密度。
* 它會針對在 Xbox One 上執行的 UWP 應用程式，符合固定 DPI 和有效的圖元，讓裝置之間能無縫體驗。
* 當您在世界各地的應用程式之間調整規模時，此大小會良好。

### <a name="2d-app-view-interface-design-best-practices"></a>2D 應用程式視圖介面設計最佳作法

**任務**
* 遵循 [Windows 10 的人體介面指導方針 (HIG) ](https://dev.windows.com/design) 樣式、字型大小和按鈕大小。 HoloLens 將會執行工作，以確保您的應用程式會有相容的應用程式模式、可讀取的文字大小，以及適當的點擊目標大小。
* 確定您的 UI 遵循最佳作法，以提供最適合 HoloLens 的獨特解析度和 DPI 的 [回應式設計](/windows/uwp/design/layout/screen-sizes-and-breakpoints-for-responsive-design) 。
* 使用來自 Windows 的「淺色」色彩主題建議。

**不要：**
* 在混合的現實情況下變更您的 UI，以確保使用者在耳機中有熟悉的體驗。

### <a name="understand-the-app-model"></a>瞭解應用程式模型

混合現實的 [應用程式模型](../../design/app-model.md) 是設計用來使用混合現實首頁，其中許多應用程式會一起運作。 您可以把它想成是桌上型電腦的混合現實，也就是一次執行許多2D 應用程式。 這會影響應用程式的生命週期、圖格和其他重要功能。

### <a name="app-bar-and-back-button"></a>應用程式行和上一頁按鈕

2D 視圖是以應用程式列在其內容之上裝飾。 應用程式行有兩個應用程式特定的個人化點：

**標題：** 顯示與應用程式實例相關聯之磚的 *displayname*

[**上一頁] 按鈕：** 按下時，會引發 *[BackRequested](/uwp/api/Windows.UI.Core.SystemNavigationManager)* 事件。 [上一頁] 按鈕可見度是由 *[SystemNavigationManager. AppViewBackButtonVisibility](/uwp/api/Windows.UI.Core.SystemNavigationManager)* 所控制。

![2D 應用程式視圖中的應用程式行 UI](images/12697297-10104100857470613-1470416918759008487-o-500px.jpg)<br>
*2D 應用程式視圖中的應用程式行 UI*

### <a name="test-your-2d-apps-design"></a>測試2D 應用程式的設計

請務必測試您的應用程式，以確定文字可以讀取、按鈕目標設為，且整體應用程式看起來正確。 您可以在桌上型耳機、HoloLens、模擬器，或解析度設定為1280x720% 的觸控裝置上進行 [測試](../platform-capabilities-and-apis/testing-your-app-on-hololens.md) @150 。

## <a name="new-input-possibilities"></a>新的輸入可能性

HoloLens 使用 advanced depth 感應器來查看世界並查看使用者。 這可啟用先進手勢，例如 [bloom](../../design/system-gesture.md#bloom) 和 [敲擊](../../design/gaze-and-commit.md#composite-gestures)。 強大的麥克風也可以提供 [語音體驗](../../design/voice-input.md)。

使用桌上型耳機時，使用者可以使用移動控制器來指向應用程式並採取動作。 他們也可以使用遊戲台，以物件作為其注視。

Windows 會為 UWP 應用程式處理這種複雜性，並將您的 [注視](../../design/gaze-and-commit.md)、手勢、語音和移動控制器輸入轉譯成可抽象化輸入機制的 [指標事件](/windows/uwp/design/input/handle-pointer-input#pointer_events) 。 比方說，使用者可能已在移動控制站上使用手或提取 Select 觸發程式，但是2D 應用程式不需要知道輸入的來源-它們只會看到2D 觸控按，如同在觸控式螢幕上一樣。

以下是將 UWP 應用程式帶入 HoloLens 時，應瞭解輸入的高階概念/案例：
* [](../../design/gaze-and-commit.md)您可以透過在應用程式周圍撥雲見日，以非預期地觸發功能表、flyouts 或其他使用者介面元素，來切換到暫止事件。
* 注視不像滑鼠輸入一樣精確。 針對 HoloLens 使用適當大小的點擊目標，類似于便於觸控的行動應用程式。 接近應用程式邊緣的小元素，特別難以與互動。
* 使用者必須切換輸入模式，才能從滾動至拖曳至兩個手指移動。 如果您的應用程式是針對觸控輸入而設計，請考慮確定不會在兩個手指移動之後鎖定任何主要功能。 若是如此，請考慮採用替代輸入機制，例如可啟動兩個手指移動的按鈕。 例如，地圖應用程式可以使用兩個手指移動來縮放，但是有加號、減號和旋轉按鈕，只要按一下就能模擬相同的縮放互動。

[語音輸入](../../design/voice-input.md) 是混合現實體驗的重要部分。 我們已啟用在使用耳機時，Windows 10 為 Cortana 提供的所有語音 Api。

## <a name="publish-and-maintain-your-universal-app"></a>發佈和維護您的通用應用程式

當您的應用程式啟動並執行之後，請封裝您的應用程式，以將 [它提交至 Microsoft Store](../../distribute/submitting-an-app-to-the-microsoft-store.md)。

## <a name="see-also"></a>另請參閱
* [應用程式模型](../../design/app-model.md)
* [頭部目光和行動](../../design/gaze-and-commit.md)
* [運動控制器](../../design/motion-controllers.md)
* [語音輸入](../../design/voice-input.md)
* [將應用程式提交到 Microsoft Store](../../distribute/submitting-an-app-to-the-microsoft-store.md)
* [使用 HoloLens 模擬器](../platform-capabilities-and-apis/using-the-hololens-emulator.md)