---
title: 設計全像攝影顯示器的內容
description: 瞭解全像顯示器的設計方針和最佳作法。
author: yoonpark
ms.author: dongpark
ms.date: 06/18/2020
ms.topic: article
keywords: UI 設計、全像展示、內容設計、深色主題、淺色主題、混合現實耳機、windows mixed reality 耳機、虛擬實境耳機、HoloLens、MRTK、混合現實工具組、設計、圖元
ms.openlocfilehash: 4a95f5df50a600035d9127c73f86a5d8be5e7131
ms.sourcegitcommit: d340303cda71c31e6c3320231473d623c0930d33
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/01/2021
ms.locfileid: "97847996"
---
# <a name="designing-content-for-holographic-display"></a>設計全像攝影顯示器的內容

![Ulnar 側邊位置](images/UX_Hero_DarkTheme.jpg)

在設計全像顯示器的內容時，您必須考慮幾個元素，才能達到最佳體驗。 我們已在下方列出一些建議，而您可以在 [ [色彩]、[淺色] 和 [材質](color-light-and-materials.md) ] 頁面上深入瞭解全像攝影顯示器的特性。

<br>

## <a name="challenges-with-bright-color-on-a-large-surface"></a>在大型表面上具有亮色的挑戰 
根據我們的 HoloLens 經驗研究和測試，我們發現在顯示的大型區域中使用亮色可能會導致幾個問題： 

**眼睛疲勞** 

因為全像全像的顯示器是加總的，所以色彩很亮的全像影像。 在顯示的大型區域中，很亮的純色可能會讓使用者很容易就能疲勞。 

**手遮蔽** 

明亮的色彩讓使用者在直接與物件互動時，難以看到他們的手。 由於使用者看不到他們的手，因此很難觀察手指/指標與目標表面之間的深度/距離。 手指指標有助於彌補這個問題，但在亮白表面上仍然很有挑戰性。 

![色彩和手遮蔽 ](images/color_handocclusion.jpg)
 *很難看到明亮的彩色內容 backplate*

**色彩一致性**

由於全息型顯示器的特性，顯示器上的大型區域可能會變成 blotchy。 藉由使用深色配置，您可以將此問題降至最低。 

## <a name="design-guidelines-for-color-choices"></a>色彩選擇的設計方針

**針對 UI 背景使用深色色彩**

藉由使用深色色彩配置，您可以將眼睛疲勞降到最低，並改善直接互動的信賴度。 

![深色色彩範例，用於內容背景的 ](images/color_dark_examples.jpg)
 *深色色彩範例*

**使用 semibold 或粗體字型粗細**

HoloLens 可讓您的體驗顯示美觀的高解析度文字。 不過，建議您避免使用淺色或半淺色等細字型粗細，因為垂直筆觸可能會以小型字型大小來抖動。 

![粗體或粗體字型粗細 (上方面板) 改善可讀性 ](images/color_font_examples.jpg)
 *粗體或粗體字型粗細 (上方面板) 改善可讀性*

**使用 MRTK 的 HolographicBackplate 材質**

HolographicBackplate 材質會套用至 HoloLens shell 中的數個 UI 面板。 其中一個功能是使用者在根據面板移動其位置時，可看見的 iridescence 效果。 Backplate 色彩會在預先定義的頻譜之間稍微移動、建立吸引人且動態的視覺效果，而不會干擾內容的可讀性。 這種微妙的色彩變換也可彌補任何次要色彩的不規則。 


## <a name="challenges-with-transparent-or-translucent-ui-backplate"></a>透明或半透明 UI backplate 的挑戰 

![透明 ui 的透明 ui 範例 ](images/color_transparent_examples.jpg)
 *backplate*

**視覺效果複雜性和協助工具**

因為全像是融合的物件與實體環境混合，所以透明或半透明視窗的內容或 UI 可讀性可能會降低。 此外，當透明的全像全像全像的物件彼此重迭時，它可能會讓使用者難以進行互動，因為這會造成混淆的深度。

**效能**

若要正確轉譯透明或半透明的物件，則必須使用存在於背景中的任何物件來排序和混合。 透明物件的排序具有適度的 CPU 成本，因此混合具有相當大的 GPU 成本，因為它不允許 GPU 透過 z 剔除來隱藏表面移除 (例如 深度測試) 。 不允許隱藏的介面移除會增加最後轉譯圖元所需的作業數目。 這會增加壓力的填滿率條件約束。

**深度 LSR 技術的全像穩定性問題**

若要改善全像攝影 reprojection 或全像全像全像全像，應用程式可以為每個轉譯的畫面格提交深度緩衝區至系統。 使用 reprojection 的深度緩衝區時，您需要為每個色彩轉譯圖元的對應深度寫入深度緩衝區。 具有深度值的任何圖元也都應該具有色彩值。 如果未遵循上述指導方針，則會以產生成品的方式 reprojected 已轉譯影像的區域，而這些專案會產生成品，通常會顯示為類似 wave 的扭曲。


## <a name="design-guidelines-for-transparent-elements"></a>透明元素的設計方針

**使用不透明的 UI 背景**

根據預設，透明或透明物件不會寫入深度來允許適當的混合。 解決這個問題的方法包括：使用不透明的物件，確保透明物件靠近不透明的物件 (例如在不透明 backplate) 前面的半透明按鈕、強制透明物件寫入深度 (不適用於所有案例) 或轉譯 proxy 物件，這些物件只會在框架結尾提供深度值。

MRTK 中的解決方案-Unity： https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/hologram-stabilization.html#depth-buffer-sharing-in-unity  

藉由使用穩固且不透明的 backplate，我們可以保障可讀性和互動的信賴度。

**將受影響的圖元數目降至最低**

如果您的專案必須使用透明物件，請儘量減少受影響的圖元數目。 例如，如果只有在特定條件下才會顯示物件 (例如加亮光暈效果) ，則在完全不顯示時，請停用該物件 (而不是將加法色彩設定為黑色) 。 針對使用具有 Alpha 遮罩之四色的簡單2D 圖形，請考慮改為使用不透明著色器來建立圖形的網格標記法。 

<br/>

---

<br/>

## <a name="dark-ui-examples-in-mrtk-mixed-reality-toolkit-for-unity"></a>適用于 Unity 的 MRTK (混合現實工具組) 的深色 UI 範例

**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** 會根據深色色彩配置提供許多 UI 建立區塊範例。

* [近端功能表](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_NearMenu.html)
* [對話方塊](https://microsoft.github.io/MixedRealityToolkit-Unity/Assets/MRTK/SDK/Experimental/Dialog/README_Dialog.html)
* [手形功能表](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_HandMenu.html)

<br>

---

## <a name="see-also"></a>請參閱

* [色彩、光線和材質](color-light-and-materials.md)
* [游標](cursors.md)
* [手部光線](point-and-commit.md)
* [Button](button.md)
* [可互動的物件](interactable-object.md)
* [週框方塊和應用程式列](app-bar-and-bounding-box.md)
* [操作](direct-manipulation.md)
* [手部功能表](hand-menu.md)
* [近端功能表](near-menu.md)
* [物件集合](object-collection.md)
* [語音命令](voice-input.md)
* [鍵盤](keyboard.md)
* [工具提示](tooltip.md)
* [平板](slate.md)
* [滑桿](slider.md)
* [著色器](shader.md)
* [佈告板和常駐標籤](billboarding-and-tag-along.md)
* [顯示進度](progress.md)
* [表面磁性](surface-magnetism.md)
