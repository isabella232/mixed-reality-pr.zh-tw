---
title: 測試 HoloLens 上的應用程式
description: 測試 HoloLens 應用程式的指引和建議
author: jonmlyons
ms.author: jlyons
ms.date: 02/24/2019
ms.topic: article
keywords: HoloLens，測試
ms.openlocfilehash: f498fd9f724cc0786e7b8bfe656f1948de1ab0cb
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2020
ms.locfileid: "91679873"
---
# <a name="testing-your-app-on-hololens"></a>測試 HoloLens 上的應用程式

測試 HoloLens 應用程式與測試 Windows 應用程式非常類似。 所有一般區域都應考慮 (功能、互通性、效能、安全性、可靠性等 ) 。 不過，某些需要特殊處理或注意的區域，通常不會在電腦或電話應用程式中觀察到。 全像攝影應用程式需要在各式各樣的環境中順利執行。 他們也需要隨時維護效能和使用者的緩和。 本主題將詳細說明測試這些區域的指引。

## <a name="performance"></a>效能

全像攝影應用程式需要在各式各樣的環境中順利執行。 他們也需要隨時維護效能和使用者的緩和。 使用全像全像全公司的應用程式時，效能對使用者的體驗很重要。 請確認您已閱讀並遵循 [混合現實的瞭解效能](understanding-performance-for-mixed-reality.md)

## <a name="testing-3d-in-3d"></a>在3D 中測試3D
1. **盡可能在最多不同的空間中測試您的應用程式。** 在大房間、小型房間、bathrooms、廚房、臥室、辦公室等中試用。另外也請考慮非標準功能的房間，例如非垂直牆、彎曲牆、非水準上限。 在房間間、地面之間轉換走廊或階梯時，是否能順利運作？
2. **在不同的光源條件中測試您的應用程式。** 它會正確地回應不同的環境條件，例如光源、黑色表面、透明/反射表面（例如鏡像、玻璃牆等）。
3. **在不同的動作條件中測試您的應用程式。** 放在裝置上，並在各種不同的動作狀態下嘗試您的案例。 它會正確地回應不同的移動還是穩定狀態？
4. **測試您的應用程式從不同角度的運作方式。** 如果您有全球鎖定的全像影像，如果您的使用者在幕後，會發生什麼事？ 如果使用者與全像全像全像），會發生什麼事？ 如果使用者查看上述或下方的全像影像，該怎麼辦？
5. **使用空間和音訊提示。** 請確定您的應用程式使用這些應用程式，以防止使用者遺失。
6. **在不同層級的環境雜訊中測試您的應用程式。** 如果您已執行語音命令，請嘗試以不同的環境雜訊層級叫用它們。
7. **測試您的應用程式** 是否已站上。 請務必從座位和站上的位置進行測試。
8. **從不同的距離測試您的應用程式** 。 UI 元素是否可以從遠距離讀取和互動？ 您的應用程式是否會對使用者太靠近您的全像投影而反應？
9. **針對常見的應用程式行互動測試您的應用程式** 。 所有的應用程式磚和2D 通用應用程式都有一個 [應用程式行](../../discover/navigating-the-windows-mixed-reality-home.md#moving-and-adjusting-apps) ，可讓您控制應用程式在混合式環境中的定位方式。 請確定按一下 [移除] 會正常地終止您的應用程式進程，而且在2D 通用應用程式的內容中支援 [上一頁] 按鈕。 當您的應用程式處於作用中狀態時，請嘗試在 [調整模式](../../discover/navigating-the-windows-mixed-reality-home.md#moving-and-adjusting-apps) 中調整並移動應用程式，而這是暫止的應用程式磚。

### <a name="environmental-test-matrix"></a>環境測試矩陣

![適用于 HoloLens 應用程式開發的環境測試矩陣](images/environment-matrix-600px.png)

## <a name="comfort"></a>舒適度
1. **剪輯平面。** 用心到轉譯 [全息影像](hologram-stability.md#hologram-render-distances)的位置。
2. **避免與實際的 head 移動不一致的虛擬移動。** 避免以不代表使用者實際動作的方式移動攝影機。 如果您的應用程式需要透過場景移動使用者，請讓動作可預測、將加速降至最低，並讓使用者控制移動。
3. **遵循「全像」品質指導方針。** 實行全像 [影像品質指導](hologram-stability.md) 方針的高效能應用程式比較不可能導致使用者不適感。
4. **以水準方式（而不是垂直）散發全像投影。** 強制使用者花很長的時間來向上查閱或向下，可能會導致疲勞。


## <a name="input"></a>輸入

### <a name="interaction-models"></a>互動模型

請確定全像影像互動可與您選擇的 [互動模型](../../design/interaction-fundamentals.md)一起運作。
如果需要這些配件來支援協助工具，也最好使用不同的配件來進行驗證，例如滑鼠和鍵盤。

**驗證您的應用程式在使用滑鼠和觸控時有不同的行為。** 這會找出不一致的問題，並協助設計決策，讓使用者更自然體驗。 例如，根據停留來觸發動作。


### <a name="custom-voice-commands"></a>自訂語音命令

[語音輸入](../../design/voice-input.md) 是一種自然的互動形式。 根據您選擇的命令以及公開這些命令的方式，使用者體驗可能會神奇或令人困惑。 作為規則，您不應該使用系統語音命令，例如 "Select" 或 "嗨 Cortana" 作為自訂命令。 以下是一些要考慮的重點：
1. **避免使用發音類似的命令。** 這可能會觸發不正確的命令。
2. **盡可能選擇發音豐富的單字。** 這會最小化及/或避免啟用錯誤。

### <a name="peripherals"></a>周邊設備

使用者可以透過 [週邊設備](../../discover/hardware-accessories.md)與您的應用程式互動。 應用程式不需要執行任何特殊動作就能利用這項功能，但有幾個值得檢查的專案。
1. **驗證自訂互動。** 像是您應用程式的自訂鍵盤快速鍵。
2. **驗證切換輸入類型。** 在相同的情況下，嘗試使用多個輸入方法來完成工作，例如語音、手勢、滑鼠和鍵盤。

## <a name="system-integration"></a>系統整合

### <a name="battery"></a>電池

在沒有電源線連接的情況下測試您的應用程式，以瞭解其耗盡電池的速度。 您可以藉由查看電源 LED 讀數，輕鬆地瞭解電池狀態。 

![指出電池電力的 LED 狀態](images/batterypowerledindication-500px.png)<br>

*指出電池電力的 LED 狀態*

### <a name="power-state-transitions"></a>電源狀態轉換

在電源狀態之間轉換時，驗證主要案例會如預期般運作。 例如，應用程式是否維持在其原始位置？ 是否正確保存其狀態？ 它是否會繼續如預期般運作？
1. **待命/繼續。** 若要進入待命，可以立即按下並放開電源按鈕。 裝置也會在閒置3分鐘後自動進入待命狀態。 若要從待命恢復，可以立即按下並放開電源按鈕。 如果您從電源線連接或中斷連線，則裝置也會繼續。
2. **關機/重新開機。** 若要關閉，請持續按住電源按鈕6秒。 若要重新開機，請按下電源按鈕。

### <a name="multi-app-scenarios"></a>多應用程式案例

在應用程式之間切換時驗證核心應用程式功能，特別是當您已執行背景工作時。 在適用的情況下，複製/貼上和 Cortana 整合也值得檢查。

## <a name="telemetry"></a>遙測

使用遙測和分析來引導您。 將分析整合到您的應用程式，可協助您深入瞭解您的應用程式，並瞭解您的 Beta 測試人員和使用者。 這種資料可以用來在提交至存放區之前，以及在未來的更新中，協助您將應用程式優化。 其中有許多分析選項。 如果您不確定要從何處著手，請參閱 [App Insights](https://www.visualstudio.com/products/application-insights-vs.aspx)。

要考慮的問題：
1. 使用者使用空間的方式為何？
2. 應用程式如何將物件放在世界中-您可以偵測出問題嗎？
3. 他們在應用程式的不同階段花了多少時間？
4. 他們在應用程式中花了多少時間？
5. 使用者嘗試的最常見使用路徑為何？
6. 使用者是否碰到非預期的狀態及/或錯誤？

## <a name="emulator-and-simulated-input"></a>模擬器和模擬輸入

[HoloLens 模擬器](using-the-hololens-emulator.md)是使用各種模擬的使用者特性和空間有效率地測試您的全像攝影應用程式的絕佳方式。 以下是有效使用模擬器來測試應用程式的一些建議：
1. **使用模擬器的虛擬房間來擴展您的測試。** 模擬器隨附一組虛擬房間，您可用來在更多的環境中測試您的應用程式。
2. **使用模擬器來查看所有角度的應用程式。** PageUp/PageDn 金鑰會讓您的模擬使用者變得更高或更短。
3. **使用實際 HoloLens 測試您的應用程式。** HoloLens 模擬器是一個絕佳的工具，可協助您快速地逐一查看應用程式並攔截新的錯誤，但請確定您也先在實體 HoloLens 上進行測試，然後再提交至 Windows Store。 這一點很重要，可確保效能和經驗在真正的硬體上很有説明。

## <a name="automated-testing-with-perception-simulation"></a>使用認知模擬進行自動化測試

有些應用程式開發人員可能會想要將應用程式的測試自動化。 除了簡單的單元測試之外，您還可以使用 HoloLens 中的 [認知模擬](perception-simulation.md) 堆疊，將人類和世界的輸入自動化至您的應用程式。 認知模擬 API 可以將模擬的輸入傳送到 HoloLens 模擬器或實體 HoloLens。

## <a name="windows-app-certification-kit"></a>Windows 應用程式認證套件

若要為您的應用程式提供最有機會在 Windows 市集中 [發佈](../../distribute/submitting-an-app-to-the-microsoft-store.md)，請先在本機進行驗證並測試，再提交憑證以進行認證。 如果您的應用程式是以 Windows 全像裝置系列為目標， [Windows 應用程式認證套件](https://msdn.microsoft.com/library/windows/apps/xaml/mt186449.aspx) 只會在您的電腦上執行本機靜態分析測試。 您的 HoloLens 不會執行任何測試。

## <a name="see-also"></a>另請參閱
* [將應用程式提交到 Windows Store](../../distribute/submitting-an-app-to-the-microsoft-store.md)
