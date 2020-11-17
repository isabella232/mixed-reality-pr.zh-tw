---
title: Unreal 中的材質建議
description: Unreal 引擎中的材質總覽。
author: hferrone
ms.author: v-hferrone
ms.date: 09/18/2020
ms.topic: article
keywords: Unreal、Unreal Engine 4、UE4、HoloLens、HoloLens 2、開發、教材、檔、指南、功能、全息表、遊戲開發、混合現實耳機、windows mixed reality 耳機、虛擬實境耳機
ms.openlocfilehash: d57689e9427ab5877e3afb49b0d19f35df6c47d2
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2020
ms.locfileid: "94678937"
---
# <a name="material-recommendations-in-unreal"></a>Unreal 中的材質建議

材質可以在 Unreal 引擎中建立或打破效能。 此頁面可作為基本設定的快速入門，您應該使用這些設定才能獲得最佳效能。

## <a name="using-customizeduvs"></a>使用 CustomizedUVs

如果您需要為您的材質提供 UVs 圖，您應該使用 CustomizedUVs 而不是直接修改材質節點的 UV。 CustomizedUVs 允許在頂點著色器中發生 UV 操作，而不是圖元著色器。 

![Unreal 中的材質設定](images/unreal-materials-img-01c.png)

您可以在下列螢幕擷取畫面中找到 [Unreal 引擎檔](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html) 和最佳作法範例中的材質詳細資料：

[ ![ 建議的材質設定 Unreal ](images/unreal-materials-img-01.png) 建議的](images/unreal-materials-img-01.png#lightbox) 
 *材質設定*

Unreal 不建議的材質設定[ ![ 中不建議的材質設定 ](images/unreal-materials-img-01b.png) ](images/unreal-materials-img-01b.png#lightbox) 
 *Non-recommended material setup*

## <a name="changing-blend-mode"></a>變更 Blend 模式

除非有強原因，否則您應該將 blend 模式設定為不透明。 遮罩和半透明材質很慢。 您可以在 [Unreal 引擎檔](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html)中找到更多有關材質的詳細資料。

![變更 blend 模式](images/unreal-materials-img-02.jpg)

## <a name="updating-lighting-for-mobile"></a>更新行動裝置的燈光

應關閉完整精確度。 您可以藉由關閉方向資訊，來向下撥號 Lightmap 光源。 停用時，lightmaps 中的光源將會是平坦的，但較便宜。

![Unreal 中的行動電話材質設定](images/unreal-materials-img-03.jpg)

## <a name="adjusting-forward-shading"></a>調整正向網底

這些選項會以效能的成本改善視覺精確度。 它們應該會關閉以獲得最大效能。

![Unreal 中的向前陰影材質設定](images/unreal-materials-img-04.jpg)

## <a name="setting-material-translucency"></a>設定材質半透明度

指出透明的材質不應受到 bloom 或 DOF 的影響。 由於這兩種效果在 MR 中都很罕見，因此預設應該開啟此設定。

![Unreal 中的 Mobile 個別半透明度設定](images/unreal-materials-img-05.jpg)

## <a name="optional-settings"></a>選擇性設定

下列設定可能會改善效能，但請注意，這些設定會停用某些功能。 只有在您確定不需要有問題的功能時，才使用這些設定。

![Unreal 中的選擇性材質設定](images/unreal-materials-img-06.jpg)

如果您的材質不需要反射或眼，則設定此選項可提供大幅的效能提升。 在內部測試中，它會與「unlit」一樣快速，同時提供光源資訊。

## <a name="best-practices"></a>最佳作法

以下不是「設定」，因為它們是與材質相關的最佳做法。

建立參數時，最好盡可能使用「靜態參數」。 靜態參數可用來移除沒有執行時間成本之材質的整個分支。 實例可以有不同的值，因此可以有樣板化著色器設定，而不會遺失效能。 但缺點在於，這會建立許多會導致重新編譯許多著色器的排列。 請儘量減少材質中的靜態參數數目，以及這些靜態參數實際上使用的排列數目。 您可以在 [Unreal 引擎檔](https://docs.unrealengine.com/Engine/Rendering/Materials/ExpressionReference/Parameters/index.html#staticswitchparameter)中找到轉譯材質參數的詳細資料。

![材質設定的最佳作法](images/unreal-materials-img-07.jpg)

建立材質實例時，應該將喜好設定提供給材質實例動態的 **材質實例常數** 。 **材質實例常數** 是在執行時間之前只計算一次的實例材質。

透過內容瀏覽器建立的材質實例 (以 **滑鼠右鍵按一下 > 建立材質實例**) 是材質實例常數。 動態資料實例是透過程式碼建立。 您可以在 [Unreal 引擎檔](https://docs.unrealengine.com/Engine/Rendering/Materials/MaterialInstances/index.html)中找到有關材質實例的詳細資料。

![在 Unreal 中建立材質實例](images/unreal-materials-img-08.png)

請留意您的材質/著色器複雜度。 您可以按一下 [平臺統計資料] 圖示，以查看各種平臺上的材質成本。 您也可以在 [Unreal 引擎檔](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html)中找到更多有關材質的詳細資料。

![在 Unreal 中建立材質實例動態設定](images/unreal-materials-img-09.png)

您可以透過著色器複雜性 [視圖模式](https://docs.unrealengine.com/Engine/UI/LevelEditor/Viewports/ViewModes/index.html)，快速瞭解著色器的相對複雜度。

* 視圖模式熱鍵： Alt + 8
* 主控台命令： viewmode shadercomplexity

![Unreal 中的材質複雜性](images/unreal-materials-img-10.png)

## <a name="see-also"></a>另請參閱
* [行動教材](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html)
* [視圖模式](https://docs.unrealengine.com/Engine/UI/LevelEditor/Viewports/ViewModes/index.html)
* [材質實例](https://docs.unrealengine.com/Engine/Rendering/Materials/MaterialInstances/index.html)
