---
title: Ford GT40 體驗
description: 當我們探索 Ford GT40 mixed reality 應用程式與 MRTK HoloLens 2 for Unreal 中的時，請跟著做。
author: hferrone
ms.author: v-hferrone
ms.date: 3/23/2021
ms.topic: article
keywords: Unreal、Unreal Engine 4、UE4、HoloLens、HoloLens 2、mixed reality、部署至裝置、電腦、檔、混合現實耳機、windows mixed reality 耳機、虛擬實境耳機
appliesto:
- HoloLens 2
ms.openlocfilehash: ca577bdc5bc30aebf80c9888345eb0e2d5c3ce6d
ms.sourcegitcommit: cc9d90b046a9fce792058fea25ae13a9186e43e7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2021
ms.locfileid: "105008923"
---
# <a name="the-making-of-the-ford-gt40-experience"></a>製作 Ford GT40 體驗

*「預先 MRTK，使用 Unreal 開發 HoloLens 2 的作業有點繁瑣，因為所有的空間互動都必須以 c + + 手動編碼。MRTK for Unreal 讓許多這些相同的工作變得很簡單。我估計它會將初始原型所需的時間剪下一半。」* -聖約瑟 Rodriguez，軟體發展人員

*「Ford GT40 體驗證明，在短短幾個月內可以完成高精確度的 HoloLens 2 應用程式，並具有適度的預算，但仍可提供高度具影響力的結果。」*  -Daniel Cheetham，首席創新官員，快樂完成

使用混合現實工具組 (MRTK) Unreal 的創意，創意的生產公司很高興完成提供 HoloLens 2 的體驗，提供 Ford GT40 的全新觀點，也就是在 Le 傳說的24小時內 Ferrari 的黑心遊記競爭汽車！

使用者可以使用一系列的自然且直覺的空間互動，探索 GT40's 的有利、效能和工程，這些都是以利用 Unreal 引擎所提供的高視覺精確度的方式來提供。 整個專案的軟體發展是由單一開發人員在三個月內完成，並可透過 MRTK Unreal 的 visual 腳本和設計環境來達成。

> [!div class="nextstepaction"]
> [下載 Ford GT40 應用程式](https://www.microsoft.com/p/ford-gt40/9p4vllktfvfp)

![Ford GT40 主圖影像](images/ford-gt40-hero.jpg)

## <a name="the-ask"></a>Ask

快樂的完成是全球領先的創新生產公司之一，其用戶端基礎包含、Ford、Microsoft、代表性、Netflix、Vodafone 和其他家庭名稱。 這家公司先將其從一家高階相片潤色機構開始，再將其致力於將其致力於在具有3D 空間設計與互動的沉浸式故事行銷中，將其致力於高品質。

在2020的中，Microsoft 已完成的示範應用程式，可協助展示新的混合現實工具組所啟用的可能性 (MRTK) for Unreal，這是以 Unreal 引擎的 HoloLens 2 支援為基礎。 到目前為止，公司已經有兩個成功的 Unreal HoloLens 2 專案。 這兩者都是針對全域辨識的取用者品牌，在內部 R&D/B2B 銷售工具的 HoloLens 2 上選擇 Unreal，以最適合用來展示用戶端專屬高階產品的需求。

雖然解決方案本身會保持在最新狀態，但必須符合一些重要的指導方針。 首先，它必須專注于企業案例，以說明 Unreal 在遊戲產業以外 HoloLens 2 的公用程式。 其次，它必須是僅限裝置的，也就是它可以作為獨立的示範，而不需要網路連接和外部處理能力來取得目標畫面播放速率和視覺品質。 第三，它應該將 MRTK 所支援的直覺互動範圍融合成流暢且自然的體驗。 最後，建議的解決方案應該展示 Unreal 引擎本身的固有視覺精確度和其他優點，例如著色器的效率。 

有了這些指導方針，您就可以開始將可能性集體討論，而這是一項混合現實體驗的概念，也就是使用空間互動來傳達品牌名稱、高價值產品的價值。 在考慮到包含監看、攝影機、汽車和私用常飛的物件範圍之後，在 Ford GT40 上，最後決定的是的汽車1966圖例（當 Ford 在 Le Ferrari 的24小時內黑心遊記的時間迎接強大），如 2019 Ford 膠捲 Ferrari 與所示。 

從 Ford 取得購買（現有的快樂用戶端）之後，公司就可以提供傳統汽車圖示的全新觀點。

## <a name="the-solution"></a>解決方案

此工作會在2020年5月7日開始。 取得 GT40 模型檔案之後，3D 演出者花了三周的時間來優化多邊形模型、UV 地圖、重新繪製材質地圖，以及將這些地圖壓縮成越少的材質。 技術演出者會平行處理3D 演出者的輸出、判斷指定的目標畫面播放速率的最佳紋理大小，並找出在 Unreal 中套用自訂著色器的最佳方式。 所有的預先生產工作都已完成，以將裝置上的體驗優化。

創意總監 Alex Lambert 在生產前工作完成後進入圖片。 他開始先觀賞 Ford 與 Ferrari，思考如何在案例和互動方面，將敘述緊密地放在一起。 他也收集了 UI 演出者的視覺參考，例如 GT40 儀表板的影像和 Le 黑心遊記 racetrack 的視覺效果，並針對音效設計工具收集 GT40 的音訊錄影。

在手邊定義敘述和優化的生產前資產之後，會將 Rodriguez 的兼職軟體發展人員 Rodriguez 已成為先前兩個已完成的兩個 Unreal HoloLens 2 專案的開發人員，在 Unreal 的 MRTK 發行之前，都已完成。

MRTK for Unreal 提供的值會提早出現，協助 Rodriguez 在一周內傳遞初始原型。 他實施了三個獨特的案例，其中一個是 Lambert 所識別之 GT40 的每個主要部分：它的美式、效能以及其工程。 在每個案例中，Rodriguez 會使用 MRTK，將優化的3D 資產從預先生產階段整合至範圍的空間互動。 

透過 MRTK for Unreal，Rodriguez 使用 visual Unreal 運動圖形來建立每個案例 (UMG) UI 設計工具，而不需要在 c + + 中執行任何動作。 [適用于 Unreal 的 Ux 工具](https://www.unrealengine.com/marketplace/product/mixed-reality-ux-tools)、包含 UX 大樓組塊的外掛程式，以及 MRTK 內的元件，賦予他 Unreal 的輸入模擬 [藍圖](https://docs.unrealengine.com/ProgrammingAndScripting/Blueprints/index.html) 、以視覺化方式編寫腳本的互動、pressable 按鈕、3d 影像操作、表面磁性等等—全都在無程式碼的拖放設計環境中。

「預先 MRTK，使用 Unreal 開發 HoloLens 2 的作業有點繁瑣，因為所有的空間互動都必須以手動方式撰寫程式碼，在 c + + 中則是「說 Rodriguez」。 「MRTK for Unreal 讓許多這些相同的工作變得很簡單。 我估計它會將初始原型所需的時間剪下一半。」

有了原型之後，小組就開始每週的反復專案，來精簡體驗。 「這是混合實境擷取功能和 Windows 裝置入口網站真的有説明」的時候，請重新叫用 Lambert。 「我使用它們來捕捉設計審核、將我的意見反應廣播給其他人，以及共同處理變更。 像這樣的隔離工作，在沒有這類工具的情況下無法執行。」

![Unreal editor Ford GT40 應用程式執行時，以順序排列的車輪元件](images/ford-gt40-img-04.JPG)

當 Lambert 要求變更時（例如重新置放 UI 元素或變更按鈕的行為），Rodriguez 會加以執行。 雖然某些變更需要較小的程式碼調整，但大部分的變更都是在 Unreal 視覺化設計工具中處理。 「我對我可以反覆運算的速度感到驚訝，」說 Rodriguez。 「沒有時間浪費;我要在設計工具中進行變更，然後按 [播放] 立即在裝置上觀看。 MRTK 真的簡化了我的工作。」

Rodriguez 也會透過生產環境就緒的所有開發工具，來重新叫用印象深刻的印象。 「我們從初始原型到最終的生產階段都能順利進行，而不需要在程式碼中重新執行或優化，」他說。  

## <a name="the-final-build"></a>最終組建

在2020年7月28日，Ford 的 GT40 Experience 完成生產 HoloLens 2 經驗已完成，並在傳說的競爭汽車上提供全新的觀點。 體驗是從歡迎畫面開始，然後藉由抓取 Ford 標誌，並將它放在類似表格或桌面的平面表面，來引導使用者設定錨點。 

### <a name="beauty"></a>美

**美** 隔區會將使用者帶到 GT40 的配置器，這會在旋轉的內部網路上顯示 GT40，類似于汽車節目中的實體車輛顯示方式。 使用者可以套用不同的滾輪選項、從不同的色彩配置中選擇，以及開啟和關閉大門和主幹 (或開機，因為它們在 UK) 中呼叫。 在所有的美後體驗中，使用者都可以挑選汽車並自由操作，以取得更深入的外觀。

![在裝置上執行之 GT40 配置器的動畫 GIF](images/ford-gt40-img-05.gif)

### <a name="performance"></a>效能

**效能** 區段會展示 GT40's 速度和耐用性。 Voiceover 一開始會說明汽車的開發方式，並將其步調在 Ford 的京中（亞利桑那州證明），並以3D 視覺效果顯示測試軌上的 GT40 in 運動。當效能區段的簡介結束時，voiceover 會提示使用者「按下 Le 黑心遊記按鈕以點擊 racetrack」。

![在裝置上執行的 GT40 速度與耐久性應用程式動畫 GIF](images/ford-gt40-img-06.gif)

效能區段的第二個部分會展示 GT40 在 Le 黑心遊記的24小時內可能遇到的條件驅動程式範圍內，這會在每年以電路 de la Sarthe 接近 Le 黑心遊記，法國舉辦。 3D 視圖會顯示 Le 黑心遊記軌上的車輛運動，並提供可讓汽車更快或更慢的按鈕。 GT40's 類比 speedometer 和流速計浮點數在 racetrack 視圖上方的影像，並在背景顯示更多競爭遙測。 使用者可以在 day 和夜間觀看之間進行切換，並在試與濕駕駛的情況之間切換，提供在實際競爭中，Ken 英里和其他 GT40 驅動程式所遭遇的真實且逼真的觀點。

### <a name="engineering"></a>Engineering

Ford GT40 Experience 的 **工程** 部門展示了其中一個協助 Ford 贏得競賽的工程創新，也就是在不到一分鐘內改變煞車 rotors 和 pad 的能力，相較于所有其他團隊所需的20-30 分鐘。 使用者可以使用直覺手勢操作 GT40 輪子和煞車元件的詳細3D 模型。 若要展開元件，使用者會挑選隨身攜帶扳手、將它與滾輪的中心鎖定對齊、將其重設成逆時針，然後將它拉離滾輪。 其他筆勢可用來移除磨損的煞車 rotors 和板、將它們取代為新的手勢、折迭元件，以及 resecure 中心鎖定。 在背景中，計時器會顯示已耗用的時間，讓使用者看看是否可以像是在 Le 黑心遊記的 pit 小組一樣快速完成進程。

![在裝置上執行之 GT40 工程體驗的動畫 GIF](images/ford-gt40-img-07.gif)

您可以 [從 Microsoft 網上商店下載](https://www.microsoft.com/p/ford-gt40/9p4vllktfvfp?activetab=pivot:overviewtab)Ford GT40 體驗，讓任何人都能利用 HoloLens 2 探索如何完成，讓傳說的賽車更有新的觀點。

### <a name="getting-impressive-visual-fidelity"></a>取得令人印象深刻的視覺精確度

雖然 Ford GT40 體驗所支援的空間互動範圍對自己有印象深刻，但體驗所提供的創意與視覺精確度，是真正讓它變得最棒的部分。 透過其3D 模型的優化，以及 Unreal 自訂著色器的使用方式，快樂完成的每秒60畫面格的目標，即使應用程式的效能區段接近315000個多邊形的大小。 

「我很高興能夠將一組流暢、直覺的互動組合成一致且吸引人的敘述」，這就是 Lambert。 「顯然，HoloLens 2 的 Unreal 引擎強大功能，讓您有新的機會，以獲得更令人驚訝和令人興奮的混合現實體驗。 無失真的視覺精確度不一定是企業應用程式在 HoloLens 2 上的最終目標，但在這種情況下，對 HoloLens 2 Unreal 的支援會變得很寶貴。」

### <a name="rapid-solution-delivery"></a>快速傳遞解決方案

就像終端使用者 Ford GT40 體驗一樣，只要在12周內完成，就能讓整個專案（從生產階段到最終交付）完成。 總而言之，專案耗用了1088小時的時間，細分如下：創意總監 (80 小時) 、UX 設計工具 (56 小時) 、UI 設計工具 (40 時) 、音效設計工具 (40 時) 、3D/技術演出者 (328 時) 、軟體發展人員 (408 時數) 、技術總監 (40 時) 、生產者 (56 時數) 和品質保證 (40 時數) 。

「整體來說，我們很接近原始專案估計值」，這是 Daniel Cheetham，這是一場快樂的首席創新專員，負責公司的互動部門。 「Ford GT40 體驗證明，在短短幾個月內可以完成高精確度的 HoloLens 2 應用程式，並具有適度的預算，但仍可提供高度具影響力的結果。」 

從開發的觀點來看，根據先前在 HoloLens 2 的 Unreal 經驗，Rodriguez 預估 Unreal 的 MRTK 會在一半的部分中，剪下所需的總時間和精力。 他還會注意到，MRTK 可以如何協助從未使用 HoloLens 2 的開發人員開始使用。 「當其他開發人員說他們對混合現實有興趣時，我鼓勵他們直接進入、安裝 HoloLens 2 開發堆疊和 MRTK，然後著手。 MRTK 可讓您快速且輕鬆地建立應用程式，而 Unreal 視覺化編輯器的運作方式，就是您甚至不需要 HoloLens 2 裝置就能開始使用。 這並不複雜，所有東西都能正常運作。」

### <a name="potential-azure-service-enhancements"></a>潛在的 Azure 服務增強功能

Lambert 看到數種方式，可讓 Azure mixed reality 服務用來增強 Ford GT40 體驗，例如使用 Azure 空間錨點來提供錨定于真實世界的多使用者體驗。 「從創意的觀點來看，Azure 空間錨點透過其提供的功能，在我們的實體世界內對應、保存及還原3D 內容或景點，以開放全新的可能性範圍」。

Lambert 也構思如何使用 Azure 中的應用程式 Azure 遠端轉譯或串流處理更詳細且複雜的3D 模型，以達成所需的畫面播放速率。 「我們必須在 Unreal 中執行一些高度優化的自訂著色器，以達到每秒60個畫面格的裝置目標」。 「有了 Azure 遠端轉譯，我們可以執行更多工作，更輕鬆地執行，而不需要花費太多工作來優化多邊形模型、重新繪製材質地圖等等。」

### <a name="endless-new-possibilities"></a>無限的新可能性

那麼快樂的下一步是什麼？ Ford 對 Ford GT40 體驗的意見反應已回應非常正面正面，在未來的 HoloLens 2 專案中，會進一步討論快樂的完成和 Ford。 在與 Ford 的關聯性之外，快樂完成已開始 HoloLens 2 上的新專案，其中 MRTK for Unreal 將成為大部分使用者體驗的基本構成要素。 

「我們一直都為每個新專案維護一種技術無關的方法，並建議任何最適合用來協助用戶端達成所需結果的工具組，」說 Cheetham。 「也就是說，HoloLens 2 已成為混合現實的實際黃金標準，尤其是在企業中，肩膀在裝置功能和支援生態系統普及率方面的所有其他選項。」

根據 Cheetham，全球流感已在潛在客戶之間，對沉浸式混合現實帶來了巨大的新興趣。 「我們比以往更忙碌，有大約50% 的潛在客戶端可討論混合的現實選項」。 「關鍵是讓人們試用它。 您可以隨時告訴他們混合的現實情況，但當您 HoloLens 2 自行體驗時，它們會立即獲得遊戲的改變。 HoloLens 2 中的 Unreal 引擎支援只會增加我們所能提供的價值，讓我們能提供視覺效果絕佳的體驗，讓您能夠獲得更高需求的用戶端。」

## <a name="try-it-out"></a>試試看！

> [!div class="nextstepaction"]
> [下載 Ford GT40 應用程式](https://www.microsoft.com/p/ford-gt40/9p4vllktfvfp)

請參閱 GitHub 上的 HoloLens 2 或[MRTK For Unreal 的](https://github.com/microsoft/MixedRealityToolkit-Unreal)[混合現實開發簡介](../development.md)。

<!-- ## About the team

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Jack Caron" width="60" height="60" src="images/kippys-escape/jack-caron.jpg"></td>
<td style="border-style: none"><b>Jack Caron</b><br><i>Lead Game Designer</i><br>Jack currently works on Mixed Reality experiences for Microsoft, including HoloLens 2 projects and AltspaceVR, and was previously a designer on the HoloLens platform team.</td>
</tr>
</table>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Summer Wu" width="60" height="60" src="images/kippys-escape/summer-wu.jpg"></td>
<td style="border-style: none"><b>Summer Wu</b><br><i>Producer</i><br>Summer works on the mixed reality developer platform and heads the team’s Unreal Engine related efforts.</td>
</tr>
</table> -->