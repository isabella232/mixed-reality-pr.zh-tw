---
title: 3D 應用程式啟動程式設計指引
description: 3D 應用程式啟動器是使用者的混合現實房子中的「實體」物件，可選擇啟動應用程式。
author: thmignon
ms.author: thmignon
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality、設計、3D 應用程式啟動器、沉浸式耳機、即時立方體、混合現實耳機、windows Mixed Reality 耳機、虛擬實境耳機、UWP、Win32、光源、色彩
ms.openlocfilehash: a501b4bdc86df17f6d005c2f7ccf4fe6a94a4b43
ms.sourcegitcommit: 4f3ef057a285be2e260615e5d6c41f00d15d08f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2020
ms.locfileid: "94703474"
---
# <a name="3d-app-launcher-design-guidance"></a>3D 應用程式啟動程式設計指引

當您放入 Windows Mixed Reality 沉浸式 (VR) 耳機時，您會進入 Windows Mixed Reality 首頁，並以山脈和水 (的 cliff 來視覺化，不過您可以 [選擇其他環境，甚至建立自己的](../design/add-custom-home-environments.md)) 。 在這個首頁的空間內，使用者可以自由排列和組織他們關心任何方式的3D 物件和應用程式。 **3d 應用程式啟動器** 是使用者的混合現實房子中的「實體」物件，可選擇啟動應用程式。

![範例： Floaty 鳥3D 應用程式啟動器](images/20171016-151526-mixedreality1-1200px-1000px.jpg)<br>
*(虛構應用程式) 的 Floaty 鳥3D 應用程式啟動器範例*

## <a name="3d-app-launcher-creation-process"></a>3D 應用程式啟動器建立流程

建立3D 應用程式啟動器有3個步驟：

1. 設計和 concepting (本文) 
2. [模型化和匯出](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
3. 將它整合到您的應用程式中：
    * [UWP 應用程式](implementing-3d-app-launchers.md)
    * [Win32 應用程式](implementing-3d-app-launchers-win32.md)

## <a name="design-concepts"></a>設計概念

### <a name="fantastic-yet-familiar"></a>太棒了

您的應用程式啟動器所居住的 Windows Mixed Reality 環境，是 fantastical/科幻的一部分。 最佳的啟動器會遵循此世界的規則。 您可以想要如何從您的應用程式中取得熟悉的代表性物件，但是將一些實際現實的規則折到最多。 魔術將會產生。

### <a name="intuitive"></a>直觀

當您查看您的應用程式啟動程式時，其目的是要啟動您的應用程式，應該很明顯且不會造成任何混淆。 例如，請確定您的啟動器是您應用程式的明確代表，不會與懸崖之屋中的某一段 décor 混淆。 您的應用程式啟動程式應邀請人員觸控/選取它。

![範例：全新附注3D 應用程式啟動器](images/20171016-152145-mixedreality1-1200px-1000px.jpg)<br>
*全新附注3D 應用程式啟動器範例 (虛構應用程式)*

### <a name="home-scale"></a>首頁規模

3D 應用程式啟動器會存留在懸崖之屋中，而且其預設大小應該與空間中的其他「實體」物件有意義。 如果您將啟動器放置在房屋工廠或某些傢俱旁邊，則應該在家裡、大小調整。 一個不錯的起點是查看它看起來如何查看30個三分，但是請記住，使用者可以視需要擴大或縮小。

### <a name="own-able"></a>擁有能力

應用程式啟動程式應該會像是某個人很高興在其空間中擁有的物件。 它們幾乎都是以這些專案為其本身，因此啟動器應該會像是使用者認為需要足夠的東西，以找出並保持在附近。

![範例： Astro 變形3D 應用程式啟動器](images/20171016-132936-mixedreality-1200px-1000px.jpg)<br>
*Astro (虛構應用程式) 的變形3D 應用程式啟動器範例*

### <a name="recognizable"></a>識別

您的3D 應用程式啟動器應該會立即將「您的應用程式品牌」表達給看到該應用程式的人員。 如果您的應用程式中有星號字元或特別可識別的物件，我們建議您在設計中使用該字元。 在混合現實世界中，物件會比單獨的標誌更吸引使用者。 可辨識的物件會快速且清楚地傳達品牌。

### <a name="volumetric"></a>體積

您的應用程式不只是將您的標誌放在平面平面上，還需要一天的時間來呼叫它。 您的啟動器應該會像是使用者空間中令人興奮的立體實體物件。 最好的方法是想像您的應用程式在 Macy 的感恩節日行列中將會有一個球形球。 問您自己，為什麼會讓人們看到街道？ 所有的觀賞角度看起來很棒嗎？

:::row:::
    :::column:::
        ![僅限標誌 ](images/20171016-140436-mixedreality-640px.jpg) *標誌*
    :::column-end:::
    :::column:::
        ![使用 ](images/20171016-140557-mixedreality-640px.jpg) *字元更容易辨識* 的字元更容易辨識
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        ![一般方法（非驚訝）感覺一般一般 ](images/20171016-155101-mixedreality-640px.jpg) *方法，而非驚訝地感覺* 一般
    :::column-end:::
    :::column:::
        ![體積型方法更能展現您的應用程式 ](images/20171016-161407-mixedreality-640px.jpg) *體積型方法，讓您的應用程式更清楚展示*
    :::column-end:::
:::row-end:::

## <a name="tips-for-good-3d-models"></a>良好3D 模型的秘訣

* 規劃應用程式啟動程式的維度時，大約會針對 30cm cube 進行。 因此，1:1:1 大小的比率。
* 模型必須在10000多邊形下。 [深入瞭解 (LODs 的三角形計數和詳細資料層級) ](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#triangle-counts-and-levels-of-detail-lods)
* 在沉浸式耳機上測試。
* 盡可能在您的模型幾何中建立詳細資料–不依賴材質取得詳細資料。
* 建立「水緊密」封閉幾何。 沒有任何未模型化的漏洞。
* 在您的物件中使用自然材質。 想像一下在現實世界中製作它。
* 確定您的模型在不同的距離和大小都能妥善閱讀。
* 當您的模型已準備好開始時，請閱讀 [匯出資產的指導方針](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#asset-requirements-overview)。

![材質中具有微妙詳細資料的模型](images/20171013-143334-mixedreality-640px.jpg)<br>
*材質中具有微妙詳細資料的模型*

### <a name="what-to-avoid"></a>避免事項

* 請勿使用高對比的詳細資料或小型、忙碌模式和紋理。
* 請勿使用精簡型幾何–它不會在某個距離正常運作，而且別名會不正確。
* 不要讓模型的某些部分延伸超過1:1:1 大小比例。 它會建立調整問題。

![避免高對比、小型忙碌模式](images/20171013-143603-mixedreality-640px.jpg)<br>
*避免高對比、小型、忙碌模式*

## <a name="how-to-handle-type"></a>如何處理類型

* 我們建議您的類型包含應用程式啟動器的 1/3 (或更) 。 型別是讓人們知道您的啟動器實際上是啟動程式的主要事物，所以如果它很大，就很好用。
* 避免將類型設為寬度-請嘗試將其保留在應用程式啟動器核心維度的範圍內 (更多或更少) 。
* 一般類型可以運作，但請注意，在某些環境中，可能很難查看。 您可以考慮將它放在其背後的穩固物件或背後，以協助進行此工作。
* 將維度加入至您的型別在3D 中感覺很不錯。 將類型的側邊著色為不同、較深色的色彩有助於可讀性。

:::row:::
    :::column:::
        ![沒有背景的平面類型可能難以從特定角度進行查看，而在某些環境中， ](images/flattype-640px.png) *沒有任何背景的平面類型可能難以從特定角度和某些環境中查看*
    :::column-end:::
    :::column:::
        ![具有內建圖的型別可以正常運作 ](images/flattypeandbkg-640px.png) *，而且內建的背景可以正常運作*
    :::column-end:::
    :::column:::
        ![如果您將側邊的拉伸類型加上陰影，則 ](images/20171016-160221-mixedreality-640px.jpg) *如果您將側邊加上陰影*，則拉伸類型可以正常運作
    :::column-end:::
:::row-end:::

**輸入可運作的色彩**

* 白色
* 黑色
* 亮色半形色彩

![輸入可運作的色彩。](images/20171016-112111-mixedreality-640px.jpg)<br>
*輸入可運作的色彩*

### <a name="colors-to-avoid"></a>要避免的色彩

造成問題的類型色彩包括：

* 中音調
* 灰色
* 過度飽和色彩或 desaturated 色彩

![造成問題的類型色彩。](images/20171016-112246-mixedreality-640px.jpg)<br>
*造成問題的類型色彩*

## <a name="lighting"></a>光源

應用程式啟動程式的光源來自懸崖之屋環境。 請務必在整個單元中的數個位置測試您的啟動程式，讓它在燈光和遮蔽中都能美觀。 好消息是，如果您已遵循本檔中的其他設計指導方針，則您的啟動程式應該會相當適合懸崖之屋中的大部分光源。

測試啟動程式如何在環境中的各種燈光中尋找的好地方，就是 Studio、媒體室、外部和後 Patio 的任何地方， (具有草坪) 的具體區域。 另一個不錯的測試是把它放在半淺色和半影子，看看它的樣子。

![確定您的啟動器在燈光和遮蔽中都看起來不錯。](images/20171013-145523-mixedreality-1200px-1000px.jpg)<br>
*確定您的啟動器在燈光和遮蔽中都很美觀*

## <a name="texturing"></a>紋理

### <a name="authoring-your-textures"></a>撰寫您的材質

您3D 應用程式啟動器的結束格式將會是 glb 檔案，這是使用 .PBR (實際轉譯) 管線所建立。 這可能是一項複雜的程式，如果您還沒有這麼做，現在是使用技術演出者的好時機。 如果您是美麗 DIY-er，請花時間 [研究並學習 .pbr 的術語](https://wiki.polycount.com/wiki/PBR) ，以及開始之前的幕後工作，將可協助您避免常見的錯誤。 

![範例：全新的備註應用程式](images/pbr-freshnote1-640px-500px.png)<br>
*全新附注3D 應用程式啟動器範例 (虛構應用程式)*

### <a name="recommended-authoring-tool"></a>建議的 authoring tool

我們建議 Allegorithmic 使用「 [物質刷](https://www.allegorithmic.com/products/substance-painter) 」來撰寫您的最終檔案。 如果您不熟悉如何在物質刷中撰寫 .PBR 著色器，請參閱以下 [教學](https://docs.allegorithmic.com/documentation/display/SPDOC/Tutorials)課程。

如果您更熟悉上述其中一項，則 ([Coat](https://3dcoat.com/home/)、 [Quixel Suite 2](https://quixel.se/suite2/)或 [Marmoset Toolbag](https://www.marmoset.co/toolbag/) 也可以使用。 ) 

### <a name="best-practices"></a>最佳作法

* 如果您的應用程式啟動器物件是針對 .PBR 而撰寫的，則將它轉換為懸崖之屋環境應該相當簡單。
* 我們的著色器預期會有金屬/粗糙度的工作流程– Unreal 的 .PBR 著色器是關閉的傳真。
* 匯出紋理時，請記住 [建議的材質大小](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#material-guidelines) 。
* 請務必為您的物件建立即時光源，這表示：
  * 避免內建陰影-或繪製陰影
  * 避免紋理中的內建光源
  * 使用其中一個 .PBR 材質撰寫套件來取得為著色器產生的正確對應

## <a name="see-also"></a>另請參閱

* [建立要在混合實境首頁中使用的3D 模型](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [實作 3D 應用程式啟動器 (UWP 應用程式)](implementing-3d-app-launchers.md)
* [實作 3D 應用程式啟動器 (Win32 應用程式)](implementing-3d-app-launchers-win32.md)
