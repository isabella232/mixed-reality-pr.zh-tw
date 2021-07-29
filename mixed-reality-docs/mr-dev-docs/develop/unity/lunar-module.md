---
title: 月球模組
description: 瞭解如何使用雙向追蹤和 Xbox 控制器輸入來延伸 HoloLens 的基本手勢、建立回應物件，以及執行功能表系統。
author: radicalad
ms.author: adlinv
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality、範例應用程式、設計、MRTK、混合現實工具組、Unity、範例應用程式、範例應用程式、開放原始碼、Microsoft Store、HoloLens、混合現實耳機、Windows Mixed Reality 耳機、虛擬實境耳機
ms.openlocfilehash: 4a736990a94d7f5c97a1bfc2edf998e327071bcb
ms.sourcegitcommit: 9831b89a1641ba1b5df14419ee2a4f29d3fa2d64
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/29/2021
ms.locfileid: "114757220"
---
# <a name="lunar-module"></a>月球模組

>[!NOTE]
>本文討論我們在 [混合現實設計實驗室](https://github.com/Microsoft/MRDesignLabs_Unity)中建立的探索範例，這是我們分享學習的地方，並提供混合現實應用程式開發的建議。 我們的設計相關文章和程式碼將隨著我們進行新探索而演進。

[陰曆模組](https://github.com/Microsoft/MRDesignLabs_Unity_LunarModule) 是 Microsoft 混合現實設計實驗室的開放原始碼範例應用程式。 瞭解如何使用雙向追蹤和 Xbox 控制器輸入來擴充 HoloLens 的基本手勢、建立回應表面對應和平面尋找的物件，以及執行簡單的功能表系統。 所有專案的元件都可以在您自己的混合現實應用程式體驗中使用。

## <a name="demo-video"></a>示範影片 
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4IcIP]

使用混合實境擷取 HoloLens 2 記錄

## <a name="rethinking-classic-experiences-for-windows-mixed-reality"></a>重新思考 Windows Mixed Reality 的傳統體驗

最高的大氣中，Apollo 模組的小型出貨想起可在下方調查不規則地形。 我們的 fearless 試驗點是合適的登陸區。 下降的棘手但幸好，此旅程的時間已過多 .。。

![來自 Atari 1979 陰曆 Lander 的原始介面](images/640px-atari-lunar-lander.png)<br>
*來自 Atari 1979 陰曆 Lander 的原始介面*

[陰曆 Lander](https://en.wikipedia.org/wiki/Lunar_Lander_(1979_video_game)) 是一種 arcade 傳統的，玩家試圖將月亮 Lander 試驗到陰曆地形的一般位置。 在1970年代的任何人都很有可能花費 arcade 的時間，並將其眼睛從天空中出貨 plummeting。 當播放玩家將其出貨到登陸區域時，地形會進行調整以顯示更詳細的資料。 Success 表示在水準和垂直速度的安全閾值內登陸。 點數是以登陸和剩餘燃料所花費的時間為依據，並以登陸區域的大小為依據。

除了遊戲之外，遊戲的 arcade 時代也不斷創新控制項配置。 從最簡單的四向操縱杆和按鈕設定 (在 iconic [Pac](https://en.wikipedia.org/wiki/Pac-Man) 中看到的) ，一直到90年底的高度特定和複雜的配置，00s (像是高爾夫球模擬器和鐵路玩射擊) 。 在陰曆 Lander 機器中使用的輸入配置有兩個原因：的吸引和深度。

![Atari 的陰曆 Lander arcade 主控台](images/atariconsole.png)<br>
*Atari 的陰曆 Lander arcade 主控台*

為什麼 Atari 和這麼多其他遊戲公司決定重新思考輸入？

最新的 flashiest 電腦自然會感到十分好奇 arcade 的小孩。 但是陰曆 Lander 有一個新穎的輸入技師修理，勇敢面對考驗了。

陰曆 Lander 會使用兩個按鈕來旋轉左右出貨，以及使用 **天生拉杆** 來控制出貨產生的天生數量。 此拉杆可讓使用者有正常遊戲的特定層級 finesse 無法提供。 它也會是新式航空考核中心的萬用群組件。 Atari 希望陰曆 Lander immerse 使用者，覺得它們其實是試驗陰曆的課程模組。 這個概念稱為 **tactile 深度**。

Tactile 深度是感應式意見反應以進行重複動作的體驗。 在此情況下，調整節流拉杆和旋轉的重複動作（我們的眼睛會看到和我們的玩家聽到的），可協助您將玩家連接到衛星表面上出貨的動作。 這個概念可以系結至「流程」的心理概念。 當使用者完全吸收在具有適當混合的挑戰和獎勵，或更簡單的工作中時，他們就是「在區域中」。

當然，混合現實中最顯著的深度類型是空間深度。 混合的整個重點是要欺騙自己來相信這些數位物件存在於真實世界中。 我們正在合成在我們的環境中，全空間可以沉浸在整個環境和經驗中。 這並不表示我們在我們的經驗中仍無法採用其他類型的深度，如同 Atari 在陰曆 Lander 中使用 tactile 深度一樣。

## <a name="designing-with-immersion"></a>使用深度設計

我們會如何將 tactile 深度套用至 Atari 傳統的已更新體積型 sequel？ 在處理輸入配置之前，必須先定址三維空間的遊戲結構。

![視覺化 HoloLens 中的介面對應](images/surfacemapping.png)<br>
*視覺化 HoloLens 中的空間對應*

藉由運用使用者的環境，我們實際上有無限的地形選項可登陸我們的陰曆課程模組。 為了讓遊戲最喜歡原始標題，使用者可能會在環境中操作並放置不同問題的登陸板。

![飛行陰曆課程模組](images/640px-lm-hero.jpg)<br>
*飛行陰曆課程模組*

要求使用者瞭解輸入配置、控制出貨，以及要使用的小型目標是很多人。 成功的遊戲體驗具有適當的挑戰與獎勵組合。 使用者可以選擇一個難度層級，而最簡單的模式就是要求使用者成功地在 HoloLens 所掃描的介面上，進入使用者定義區域。 一旦使用者取得遊戲的停止回應後，他們就可以迅速地建立所見的困難。

### <a name="adding-input-for-hand-gestures"></a>新增手形手勢的輸入

HoloLens 基底輸入只有兩個手勢-[攻點和 Bloom](../../design/gaze-and-commit.md#composite-gestures)。 使用者不需要記住內容相關的細微差異或特定手勢的總清單，可讓平臺的介面變得更多功能且容易學習。 雖然系統可能只會公開這兩個手勢，但 HoloLens 的裝置可以一次追蹤兩次手。 我們的 node.js 至陰曆 Lander 是 [沉浸式應用程式，這表示我們可以擴充一組基本的手勢來利用兩個手勢，並新增我們自己的令人愉快 tactile 表示陰曆的模組導覽。

回頭看一下原始的控制項配置， **我們需要解決天生和旋轉的** 問題。 特別注意的是，新內容中的旋轉會將額外的座標軸新增 (技術的兩個軸，但是 Y 軸對於登陸) 來說比較不重要。 這兩個不同的出貨移動自然會使自己能夠對應到每個手：

![點擊並拖曳手勢，以在所有三個軸上旋轉 lander](images/module-handdrag.gif)<br>
*點擊並拖曳手勢，以在所有三個軸上旋轉 lander*

**推力**

原始 arcade 機器上的拉杆會對應到值的小數位數，移動杆的移動越多，就會有更多天生套用至出貨。 這裡有一項重要的細微之處，就是使用者可以從控制項中拿掉並維持所需的值。 我們可以有效地使用點擊和拖曳行為來達到相同的結果。 天生值從零開始。 使用者可點擊和拖曳以增加值。 他們可能會讓我們繼續維護。 任何點拖曳手勢值變更都會是原始值的差異。

**旋轉**

這會比較複雜一點。 讓全像「旋轉」按鈕，以提供更豐富的體驗。 沒有實際的控制項可供使用，因此其行為必須來自操作代表 lander 的物件，或使用 lander 本身。 我們會利用點一下和拖曳方法，讓使用者能夠以他們想要的方向，有效地「推送和提取」。 每當使用者點擊並保存時，開始手勢的空間就會變成旋轉的原點。 從原點拖曳可將手平移的差異轉換 (X、Y、Z) ，並將其套用至 lander 旋轉值的差異。 或者更簡單地說，將 *左拖曳 <-> 右邊、向上 <-> 向下、在空間中向前 <->，則會據以旋轉出貨*。

由於 HoloLens 可以追蹤兩次手，因此天生由左方控制，可以將旋轉指派給右手邊。 Finesse 是此遊戲中成功的驅動因素。 這些互動的 *風格* 是絕對最高的優先順序。 尤其是在 tactile 深度的內容中。 如果出貨的回應速度太快，就很難吸引人，而速度太慢時，使用者必須在出貨時「推送和提取」一段滑雪的時間。

### <a name="adding-input-for-game-controllers"></a>新增遊戲控制器的輸入

雖然 HoloLens 的手手勢可提供精細控制的新穎方法，但仍有某些缺乏「true」 tactile 的意見反應，您可以從類比控制項獲得。 連接 Xbox 遊戲控制器可讓我們回頭 physicality，同時利用控制杆來維持精細的控制。

有多種方式可將相對的直接控制項配置套用至 Xbox 控制器。 由於我們想要盡可能保持最接近原始 arcade 的設定， **天生** 對應最適合 [觸發程式] 按鈕。 這些按鈕是類比控制項，也就是它們有一個以上的「 *開」和「關閉* 」狀態，實際上會回應其壓力的程度。 如此一來，我們就可以像 **天生杆** 一樣地建立類似的結構。 與原始遊戲和手手勢不同的是，當使用者停止對觸發程式造成壓力時，此控制項將會剪下出貨的天生。 它仍然提供使用者與原始 arcade 遊戲一樣的 finesse 程度。

![左邊的操縱杆對應到偏擺和變換，右邊的操縱杆對應到音調和變換](images/thumbsticksidebyside.gif)<br>
*左邊的操縱杆對應至偏擺和變換;右邊的操縱杆對應到音調和變換*

雙重 thumbsticks 自然是控制出貨的旋轉。 可惜的是，出貨可以旋轉三個軸，而且兩個 thumbsticks 都支援兩個軸。 這種不相符的情形是，其中一個操縱杆控制一個軸;或 thumbsticks 的座標軸重迭。 先前的解決方案會覺得「中斷」，因為 thumbsticks 本質上是混合其區域 X 和 Y 值。 後者的解決方案需要進行一些測試，以找出哪些多餘的軸最自然的感覺。 最後一個範例會使用 *偏擺* 和 *變換 (的 Y 和 x* 軸) 適用于左邊的操縱杆，以及針對右邊的 *操縱杆，將 (Z* *軸和 x* 軸) 。 這認為最自然的情況 *是，* 與 *偏擺* 和 *推銷* 之間的表現完全獨立。 請注意，同時使用這兩個 thumbsticks 來進行 *變換也會* 發生兩倍的旋轉值;使用 lander do 迴圈相當有趣。

這個範例應用程式會示範空間辨識和 tactile 深度如何大幅改變體驗，因為這是 Windows Mixed Reality 的可延伸輸入形式。 雖然陰曆 Lander 的年齡可能接近40年，但以幾乎的八邊形來公開的概念將會無限期地存留。 想像未來，為什麼看不到過去？

## <a name="technical-details"></a>技術詳細資訊

您可以在[GitHub 的混合現實設計實驗室](https://github.com/Microsoft/MRDesignLabs_Unity_LunarModule)中找到陰曆模組範例應用程式的腳本和 prefabs。

## <a name="about-the-author"></a>關於作者

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Addison Linville" width="60" height="60" src="images/addisonlinville-tile-60px.jpg"></td>
<td style="border-style: none"><b>Addison Linville</b><br>UX 設計者 @Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>另請參閱

* [MRTK 範例中樞](/windows/mixed-reality/mrtk-unity/features/example-scenes/example-hub) - [ (從 HoloLens 2 中的 Microsoft Store 下載)](https://www.microsoft.com/en-us/p/mrtk-examples-hub/9mv8c39l2sj4)
* [表面](sampleapp-surfaces.md) - [ (從 HoloLens 2 中的 Microsoft Store 下載)](https://www.microsoft.com/en-us/p/surfaces/9nvkpv3sk3x0)
* [元素週期表 2.0](periodic-table-of-the-elements-2.md)
* [Galaxy Explorer 2.0](galaxy-explorer-update.md)