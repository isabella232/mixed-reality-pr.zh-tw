---
title: 關於本設計指南
description: 本指南是以 Microsoft 設計工具、開發人員、程式經理和研究人員所撰寫，其工作橫跨全像攝影裝置) 例如 HoloLens) 和沈浸式裝置 (例如 Acer 和 HP Windows Mixed Reality 頭戴式裝置)。
author: mrwied
ms.author: jonwie
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality、設計、簡介、指引、混合現實耳機、Windows Mixed reality 耳機、虛擬實境耳機、ux、資源
ms.openlocfilehash: 0bd70e08d55f8d556ff3a612dbbc979dc895cebbfc9950f18d8d474ff347407b
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2021
ms.locfileid: "115198636"
---
# <a name="about-this-design-guidance"></a>關於本設計指南

## <a name="introduction"></a>簡介

**您好，歡迎使用混合現實的設計指引。**

本指南是由 Microsoft 設計人員、開發人員、程式經理和研究人員所撰寫。 從我們的作者進行的工作橫跨全像裝置，包括 HoloLens、沉浸式裝置、andAcer 和 HP Windows Mixed Reality 耳機。 建議您將這篇文章視為一組用於 Windows 前端裝載設計的主題。

我們會與您一起進入一個極具影響力的新時代。 突破在前端掛接的顯示器、空間音效、感應器、環境感知、輸入和3D 圖形潛在客戶，以及挑戰我們定義新的體驗類型。 新的新領域更具個人化、直覺化、沉浸式及內容。

在可能的情況下，我們將會提供可操作的設計指引，以及 GitHub 的相關程式碼。 話雖如此，因為我們正與您一起學習，所以我們無法在此提供特定、可採取動作的指引。 我們分享的部分將會是「我們學到的課程」的精神，而「避免」該路徑。

而且我們知道許多創新將由較大型的設計團體產生。 因此，我們期待收到您的意見、向您學習，並與您密切合作。 我們會盡力分享我們的見解，即使它們是先行探索和早期的。 我們的目標是協助開發人員和設計人員使用自己的設計思考、最佳作法，以及相關的開放原始碼控制項、模式，以及您可以直接在自己的工作中使用的範例應用程式。

## <a name="overview"></a>概觀

以下是如何組織此設計指導的快速總覽：

* **[總覽](design.md)** -瞭解設計流程、核心概念，以及要考慮的互動因素。
* **[核心概念](core-concepts-landingpage.md)** -瞭解緩和、全像全像攝影、空間對應，以及其他要考慮的核心概念。
* **[互動模型](interaction-fundamentals.md)** -本指南的結構是以三個主要互動模型為根據。
* **[UX 元素](app-patterns-landingpage.md)** -使用控制項和行為來建立您自己的應用程式體驗的建立區塊。
* **[資源](design.md#choose-a-prototyping-option)** -使用設計工具和原型處理選項快速啟動您的專案。

針對上述所有內容，我們的目標是要提供適當的文字、圖例和影片組合。 您將會看到我們使用不同的格式和技術進行實驗，並提供您所需的功能。 接下來的幾個月，我們將擴充此分類法，以包含更多的設計主題。 在可能的情況下，我們會為您提供接下來即將推出的內容，因此請持續回來查看。

## <a name="objectives"></a>目標

以下將快速查看一些指導此工作的高階目標，讓您可以瞭解我們的來源

### <a name="help-solve-customer-challenges"></a>協助解決客戶面臨的挑戰

![協助解決客戶面臨的挑戰](images/500px-fix-a-broken-switch-with-hololens.jpg) <br>

我們把了許多相同的問題，並瞭解您的工作有多困難。 很高興能探索並定義新的新領域 .。。 而且也可能會很困難。 舊的典範和實務正在 rethought，客戶需要新的體驗，而且有很多的創新潛力。 假設我們想要讓這份工作盡可能全面完成，請移至樣式指南之外。 我們的目標是要提供一組完整的設計指導方針，涵蓋混合現實互動、命令、流覽、輸入和樣式–全都在人類行為和案例中進行。 

### <a name="point-the-way-towards-a-new-more-human-way-of-computing"></a>將方式指向全新、更人類的計算方式

![將方式指向全新、更人類的計算方式](images/500px-man-and-women-with-holograph-on-table.png)<br>

雖然將焦點放在特定客戶的問題上，但我們也想要親自推送以提供更多的資訊。 我們認為絕佳的設計並不是「單純」問題解決，也是有意義地啟用人類演進的方式。 人力行為、人際關聯性、活動和環境的新方法，提供我們的創新。 我們希望我們的指導方針反映這些更理想的思考方式。 

### <a name="meet-creators-where-they-are"></a>認識他們的擁有者

![認識他們的擁有者](images/500px-creators.jpg) <br>

我們希望許多觀眾都能找到此指引，以提供説明。 您有不同的技能集 (開始、中繼、advanced) 、使用不同的工具 (Unity、DirectX、c + +、c #、其他) 、熟悉各種平臺 (Windows、iOS、Android) 、來自不同的背景 (行動裝置、企業版、遊戲) ，以及處理不同大小的小組 (單點、小型、中型、大型) 。 因此，您可以使用不同的觀點和需求來查看此指引。 可能的話，我們會嘗試將這項多樣性保持在考慮，並盡可能將我們的指導方針盡可能地與多人相關。 我們知道許多人已經在 GitHub。 因此，我們會直接連結到 GitHub 存放庫和論壇，以符合您的需求。 

### <a name="share-as-much-as-possible-from-experimental-to-explicit"></a>從實驗性到明確的共用越多

![從實驗性到明確的共用越多](images/500px-man-playinggame.jpg) <br>

在這個新的3D 媒體中提供設計指導的挑戰之一，就是我們不一定都有提供相關的指引。 就像您的一樣，我們正在學習、實驗、建立原型、解決問題，並隨著我們的碰到障礙而調整。 我們不需要等到測的未來時間，而是要與您分享我們的想法，即使沒有決定性也是一樣。 我們的最終目標是在我們可以的任何地方進行，提供與開放原始碼程式碼相關的清楚且彈性的設計指引，並可在 Microsoft 開發和設計工具中採取行動。 但是，進入該點會花許多反復專案和學習。 我們想要與您聯繫，並在過程中與您一起學習。 我們會盡可能地與我們分享，即使是實驗性的內容也一樣。 

### <a name="the-right-balance-of-global-and-local-design"></a>全域和本機設計的正確平衡

![全域和本機設計的正確平衡](images/500px-fluentdesign.jpg) <br>

我們將提供兩個層級的設計指引： global 和 local。 [Fluent Design 系統](https://fluent.microsoft.com)包含我們的「全域」設計指引。 Fluent 詳細說明我們在所有 Microsoft 設計（我們的裝置、產品、工具和服務）之間的基本概念，例如燈光、深度、移動、材質和規模。 話雖如此，此大型系統之間存在顯著的裝置特定差異。 因此，適用于 head 掛接顯示器的「本機」設計指導方針，說明了通常會有不同的輸入和輸出方法和不同使用者需求和案例的全像全像裝置和沉浸式裝置設計。 本機設計指引涵蓋 Hmd 特有的主題。 例如：3D 環境和物件;共用環境;使用感應器、眼睛追蹤和空間對應;以及空間音訊的機會。 在我們的整個指引中，您可能會看到我們指的是全域和本機方面。 希望這可協助您在更大的設計基礎中進行工作，同時利用特定裝置之間的設計差異。

### <a name="have-a-discussion"></a>討論

![討論](images/500px-share.jpg) <br>

最重要的是，我們想要與您（全像全像全像）設計人員和開發人員合作，來定義這項令人興奮的新時代。 如前所述，我們知道我們沒有所有答案。 這就是為什麼我們相信有許多令人興奮的解決方案和創新都能派上用場。 我們的目標是開啟並提供相關資訊，並在線上和活動中與您討論，並在我們可以的地方增加價值。 我們很高興成為這個絕佳設計社區的一部分，登機在一起。 

## <a name="dive-in"></a>深入瞭解

我們希望這篇簡介文章會在您探索我們的設計指引時，提供一些有意義的內容。 深入瞭解，並讓我們知道您在本文中所找到的 GitHub 論壇，或在[Twitter](https://twitter.com/MicrosoftDesign)和[Facebook](https://www.facebook.com/microsoftdesign/)上的 Microsoft 設計中所述的想法。 讓我們共同設計未來的合作！
