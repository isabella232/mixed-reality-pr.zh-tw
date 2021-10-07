---
title: 品質基本概念
description: 瞭解設計混合現實應用程式的品質基本概念。
author: qianw211
ms.author: v-qianwen
ms.date: 07/15/2021
ms.topic: article
keywords: 品質基本概念、案例研究、專案、範例、MRTK、混合現實工具組、Unity、範例應用程式、範例應用程式、開放原始碼、Microsoft Store、HoloLens、混合現實耳機、windows Mixed Reality 耳機、虛擬實境耳機
ms.openlocfilehash: 69c6a55b95937c0c6af4920f6ffe0929eebe76ee
ms.sourcegitcommit: 82f7db75d8ecc7ac89c76b0db504126cbcb8f16d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2021
ms.locfileid: "129647526"
---
# <a name="quality-fundamentals"></a>品質基本概念

品質基礎是一個 HoloLens 2 的應用程式，示範建立絕佳混合現實體驗的基本概念。  我們不只是在混合現實中學習和閱讀品質問題，我們現在可以藉由選取應用程式中提供的選項，來體驗常見的環境、設計和效能問題和解決方案第一手。

若要下載並安裝應用程式，請移至應用程式下載頁面：

> [!div class="nextstepaction"]
> [品質基本概念](https://www.microsoft.com/p/quality-fundamentals/9mwz852q88fw?activetab=pivot:overviewtab)

![品質基本首頁](images\qf-homepage.jpg)

在此範例應用程式中，我們將瞭解：

>[!div class = "checklist"]
> * [裝置 i/o 和環境](#device-io-and-environment)：環境因素會如何影響 HoloLens 的效能。
> * [空間錨點](#anchor-fundamentals)：如何使用空間錨點將全像影像對齊實體空間。
> * 全像的[穩定性和精確度](#stability-and-fidelity)：探索可協助改善全像投影穩定性和精確度的技巧。
> * [3d 資產基本](#3d-asset-fundamentals)概念：如何優化3d 資產以維持高視覺效果的精確度。 

## <a name="device-io-and-environment"></a>裝置 i/o 和環境

在 HoloLens 上啟動品質基礎應用程式。 應用程式的首頁出現後，選取 [ **裝置 i/o 和環境**]。  我們將探索 HoloLens 感應器和周圍環境如何影響空間對應、追蹤和空間的放置。 

### <a name="surfaces"></a>表面

具有鏡像完成的鏡像或表面可能會使 HoloLens 感應器與物件的圖形有關。  在介面上反映的物件可能會被裝置轉譯為變更環境，這可能會導致裝置遺失追蹤。  如果鏡像表面造成 HoloLens 的挑戰，請考慮加入螢幕或 closable 遮蔽。

如需詳細資訊，請參閱[HoloLens 環境考慮](/hololens/hololens-environment-considerations)[中空間的表面](/hololens/hololens-environment-considerations#surfaces-in-a-space)。

### <a name="lighting"></a>光源

HoloLens 的效能可能會受到非常低或非常明亮的狀況所負面影響。  HoloLens 上的追蹤感應器需要大約 500-1000 lux 的燈光才能以最佳方式運作。 您可以使用 luxmeter 或行動裝置應用程式來測量空間中的光線量。

如需詳細資訊，請參閱[HoloLens 環境考慮](/hololens/hololens-environment-considerations)中的[光源](/hololens/hololens-environment-considerations?branch=pr-en-us-3071#lighting)。

## <a name="anchor-fundamentals"></a>錨點基礎

若要探索如何使用空間錨點來將全像地理空間與實體空間對齊，請在應用程式的首頁上選取 [ **錨點 Fundametals** ]。

在應用程式的這個部分中，我們將探索下列使用者案例：

>[!div class = "checklist"]
> * 當沒有任何錨點套用至物件時，會發生什麼事。
> * 當有多個空間錨點用於一組物件時。
> * 使用 QR 代碼，在多個共同作業者之間共用空間錨點。
> * 空間中非常大型物件的錨點放置。

如需詳細資訊，請參閱[混合現實](../../design/spatial-anchors.md)檔中的[空間錨點](../../design/spatial-anchors.md)。

## <a name="stability-and-fidelity"></a>穩定性和精確度

在應用程式的首頁上，選取 [ **穩定性和精確度** ] 以探索如何改善全像全像全像是。

我們將探索下列重要概念：

>[!div class = "checklist"]
> * [畫面播放速率](#frame-rate)。
> * [延遲階段 reprojection (LSR) ](#late-stage-reprojection-lsr)。
> * [Z-對抗](#z-fighting)。
> * [消除鋸齒](#anti-aliasing)。

### <a name="frame-rate"></a>畫面播放速率

為了盡可能提供最棒的全像全像的體驗，應用程式開發人員必須維持每秒60個框架 (FPS) 。  在應用程式的這個部分中，切換不同的三角形計數選項，以體驗不同畫面播放速率的差異。

![三角形計數優化](images\qf-triangle-count-optimization.png)

如需詳細資訊，請參閱全像全像全像全[像的](../platform-capabilities-and-apis/hologram-stability.md)[框架率](../platform-capabilities-and-apis/hologram-stability.md#frame-rate)。

### <a name="late-stage-reprojection-lsr"></a>延遲階段 reprojection (LSR) 

Reprojection 是用來在使用者四處移動空間時，穩定的全像影像。  請嘗試此部分應用程式所提供的不同 reprojection 選項，以查看全像影像品質的差異。

![請嘗試不同的 reprojection 選項，以體驗差異。](images\qf-lsr-modes.jpg)

For detailed information, see [reprojection](../platform-capabilities-and-apis/hologram-stability.md#reprojection) in the [hologram stability](../platform-capabilities-and-apis/hologram-stability.md) article.

### <a name="z-fighting"></a>Z-fighting

當混合式現實應用程式無法分辨哪一個物件位於另一個物件之前時，就會發生 Z-對抗。  您將會注意到，當您的全像是相同的 z 深度值時，您會看到全息的物件閃爍。  藉由變更全像在此案例中，自行車的位置，在應用程式中變更迭置物件的位置，以體驗 z 的影響。

![使用物件放置體驗 z 的操作。](images\qf-z-fighting.jpg)

如需有關 z 的詳細資訊，請參閱在[Unity 的建議設定](./recommended-settings-for-unity.md)文章中[啟用深度緩衝區共用](./recommended-settings-for-unity.md#enable-depth-buffer-sharing)。

### <a name="anti-aliasing"></a>消除鋸齒

消除鋸齒是一種技術，用來在全像投影的曲線和對角線上平滑不規則邊緣。  在應用程式的這個部分中，您會在顯示的文字和自行車輪輻上體驗別名的影響。  

## <a name="3d-asset-fundamentals"></a>3D 資產基礎

在應用程式的首頁上，選取 [ **3D 資產基礎** ] 以探索如何將3d 資產優化以符合畫面播放速率需求，同時維持高視覺效果的精確度。

我們將探索下列重要概念：

>[!div class = "checklist"]
> * [三角形計數](#triangle-count)。
> * [著色器傳遞](#shader-passes)。
> * [繪製呼叫](#draw-calls)。
> * [Finale](#finale)。

### <a name="triangle-count"></a>三角形計數

選取自行車模型的數目和複雜性，以根據 FPS 體驗視覺差異。

![選擇不同的三角形計數選項，以查看畫面播放速率的效果。](images\qf-3d-asset-visible-triangles.jpg)

如需詳細資訊，請參閱 [資產建立流程](../../design/asset-creation-process.md)。

### <a name="shader-passes"></a>著色器階段

選取自行車數目和不同的著色器選項，以根據 FPS 體驗視覺差異。

![選擇不同的著色器選項，以查看畫面播放速率的效果。](images\qf-3d-asset-shader-complexity.jpg)

如需詳細資訊，請參閱 [MRTK 標準著色器](/windows/mixed-reality/mrtk-unity/features/rendering/mrtk-standard-shader)。

### <a name="draw-calls"></a>繪製呼叫

繪製呼叫是對圖形配接器進行耗用大量資源的呼叫。  在應用程式的這個部分中，第一次體驗視覺效果差異，因為繪製呼叫的數目會影響 FPS。

![繪製呼叫應該經過優化，才能提升效能。](images\qf-3d-asset-draw-calls.jpg)

請參閱 [CPU 對 GPU 效能建議](./performance-recommendations-for-unity.md#cpu-to-gpu-performance-recommendations)。

### <a name="finale"></a>結局

在這裡，我們可以探索可顯示的完整優化自行車數量，以及可能提供優化技術的精確度層級。

![使用的優化技術。](images\qf-3d-asset-finale.jpg)

## <a name="next-steps"></a>下一步

探索其他混合現實範例案例：

   > [!div class="nextstepaction"]
   > [範例和功能應用程式](../features-and-samples.md)