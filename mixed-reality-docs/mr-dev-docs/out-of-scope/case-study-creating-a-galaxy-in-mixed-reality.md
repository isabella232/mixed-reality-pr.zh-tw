---
title: 案例研究-在混合式事實下建立 galaxy
description: 瞭解「Galaxy Explorer」應用程式，以及它如何針對 Microsft HoloLens 和在24小時的 Twitter 輪詢之後，由社區開發人員進行。
author: karimluccin
ms.author: kaluccin
ms.date: 03/21/2018
ms.topic: article
keywords: Galaxy Explorer、HoloLens、Windows Mixed Reality、分享您的想法、個案研究
ms.openlocfilehash: ef97920d22df65a9d4fa5e630840759e58c80b53
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583539"
---
# <a name="case-study---creating-a-galaxy-in-mixed-reality"></a>案例研究-在混合式事實下建立 galaxy

在 Microsoft HoloLens 出貨之前，我們會要求開發人員小組想要看到新裝置有經驗的內部小組組建。 有超過5000的想法已共用，在24小時的 Twitter 輪詢之後，優勝者是稱為 [Galaxy Explorer](../develop/unity/galaxy-explorer.md)的概念。

Zibits 是專案的尖端領導人，而 Karim Luccin 是團隊的圖形工程師，討論藝術與工程之間的共同作業，這是在 Galaxy Explorer 中建立銀河方式的精確、互動式標記法。

## <a name="the-tech"></a>技術

由兩個設計人員組成的[小組](../develop/unity/galaxy-explorer.md#meet-the-team)（三名開發人員、四個演出者、生產者和一個測試人員）有六周的時間來建立功能完整的應用程式，可讓人們瞭解及探索銀河的 Vastness 和方式的優點。

我們想要充分利用 HoloLens 在您的生活空間中直接轉譯3D 物件的能力，因此我們決定要建立實際的查看 galaxy，讓人們可以放大並查看個別的星星，每一個都是各自的軌跡。

在第一周的開發過程中，我們提供了銀河方法的一些目標，也就是 Galaxy：需要有深度、移動和感覺體積型—全星形，可協助建立 Galaxy 的形式。

建立具有數十億顆星的動畫 galaxy 的問題，就是需要更新的大量單一元素會是每個畫面格太大的問題，以使用 CPU 建立動畫。 我們的解決方案牽涉到複雜的藝術與科學組合。

## <a name="behind-the-scenes"></a>在幕後

為了讓人們能夠探索個別的星星，我們的第一個步驟是瞭解我們可以一次轉譯的粒子數目。

### <a name="rendering-particles"></a>轉譯粒子

目前的 Cpu 很適合用來處理序列工作，且一次最多可以進行一些平行工作 (視它們) 的核心數目而定，但 Gpu 在以平行方式處理上千個作業時更有效率。 不過，因為它們通常不會與 CPU 共用相同的記憶體，所以在 CPU<>GPU 之間交換資料可能很快就會變成瓶頸。 我們的解決方案是在 GPU 上建立 galaxy，而且必須完全存留在 GPU 上。

我們開始使用各種模式的數千點粒子來進行壓力測試。 如此一來，我們就可以在 HoloLens 上取得 galaxy，看看有什麼作用和不是什麼。

### <a name="creating-the-position-of-the-stars"></a>建立星星的位置

我們的其中一個小組成員已經撰寫了 c # 程式碼，該程式碼會在其初始位置產生星星。 星星位於橢圓形上，而其位置可以透過 (**curveOffset**、 **ellipseSize**、提高 **許可權**) 來描述，其中 **curveOffset** 是沿著橢圓形的星形角度， **ellipseSize** 是沿著 X 和 Z 的橢圓形的維度，而且會提高 galaxy 內星號的適當提高許可權。 因此，我們可以建立 ([Unity 的 ComputeBuffer](https://docs.unity3d.com/ScriptReference/ComputeBuffer.html)) 的緩衝區，它會使用每個星狀屬性來初始化，並將其傳送至 GPU，以供其餘體驗使用。 為了繪製這個緩衝區，我們會使用 [Unity 的 DrawProcedural](https://docs.unity3d.com/ScriptReference/Graphics.DrawProcedural.html) ，以允許在任意一組點上的 GPU) 上執行著色器 (程式碼，而不會有代表 galaxy 的實際網格：

**Cpu：**




```
GraphicsDrawProcedural(MeshTopology.Points, starCount, 1);
```

**Gpu：**




```
v2g vert (uint index : SV_VertexID)
{

 // _Stars is the buffer we created that contains the initial state of the system
 StarDescriptor star = _Stars[index];
 …

}
```

我們開始使用具有上千個粒子的原始迴圈模式。 這讓我們能夠以較佳的速度來管理許多粒子，並以高效能的速度來執行，但我們不滿意 galaxy 的整體塑造。 為了改善圖形，我們嘗試使用旋轉的各種模式和物件系統。 這一開始是因為粒子的數目和效能維持一致，但圖形接近中央，而星星發出的外表並不切合實際。 我們需要一段時間，讓我們可以操作時間，並讓粒子實際移動，更接近 galaxy 的中心。

![我們嘗試了各種不同的模式和粒子系統，如下所示。](images/galaxy-patterns-500px.png)

我們嘗試了各種不同的模式和粒子系統，如下所示。

我們的團隊對 galaxies 函式進行了一些研究，而我們為 galaxy 建立了自訂的物件系統，讓我們可以根據「[密度 wave 理論](https://en.wikipedia.org/wiki/Density_wave_theory)」來移動有關省略號的粒子，如此一來，galaxy 的 arm 就是較高密度的區域，但在固定的 flux 中，例如交通堵塞。 它的外觀穩定且穩固，但星形在移動其各自的省略號時，會實際移入和移出 arm。 在我們的系統中，粒子絕不會存在於 CPU 上-我們會產生卡片並在 GPU 上將它們導向，讓整個系統只是初始狀態 + 時間。 它的進展如下：

![具有 GPU 轉譯之粒子系統的進展](images/spiral-galaxy-arms-500px.jpg)

具有 GPU 轉譯之粒子系統的進展


一旦加入足夠的省略號並設定為旋轉，galaxies 就會開始形成「臂」，也就是星星的移動。 每個橢圓形路徑的星星間距都有一些隨機性，而且每顆星都有一些隨機新增的位置。 這建立了更自然的星狀移動和 arm 圖形分佈。 最後，我們新增了根據距離中心距離驅動色彩的能力。

### <a name="creating-the-motion-of-the-stars"></a>建立星星的運動

若要建立一般星形運動的動畫，我們需要為每個框架新增常數角度，並以常數星形速度在其省略號之間移動星星。 這是使用 **curveOffset** 的主要原因。 這在技術上並不正確，因為星形會沿著省略號的最長邊移動，但一般動作覺得良好。

![星星在長弧線的移動速度更快，邊緣的速度較慢。](images/ellipse-movement.jpg)

星星在長弧線的移動速度更快，邊緣的速度較慢。


如此一來，就會 (**curveOffset**、 **ellipseSize**、提高 **許可權**、 **年齡**) 的完整描述每顆星，其中 **age** 是在載入場景之後所經過的總時間。




```
float3 ComputeStarPosition(StarDescriptor star)
{

  float curveOffset = star.curveOffset + Age;
  
  // this will be coded as a “sincos” on the hardware which will compute both sides
  float x = cos(curveOffset) * star.xRadii;
  float z = sin(curveOffset) * star.zRadii;
   
  return float3(x, star.elevation, z);
  
}
```

如此一來，我們就可以在應用程式一開始就產生數萬顆星，然後在建立的曲線上以一組挑的星形為動畫。 由於所有專案都是在 GPU 上，因此系統可以平行地以平行方式建立所有星星的動畫，而不需支付 CPU 的成本。

![以下是繪製白色四邊形時的樣子。](images/drawing-white-quads-300px.jpg)

以下是繪製白色四邊形時的樣子。



為了讓每個四顆人都臉部，我們使用幾何著色器，將每個星形位置轉換成螢幕上包含星狀材質的2D 矩形。

![鑽石（而非四邊形）。](images/drawing-white-quads-300px.jpg)

鑽石（而非四邊形）。


因為我們想要限制過度繪製 (次圖元) 處理的次數，所以我們會旋轉四邊形，使其重迭。

### <a name="adding-clouds"></a>新增雲端

有許多方式可以讓體積型感覺，從磁片區內的光線按照，到盡可能繪製最多的粒子來模擬雲端。 即時光線按照需要太多資源而且難以撰寫，因此我們先嘗試使用一種呈現遊戲中樹系的方法來建立冒名頂替的系統，並以許多2D 影像呈現相機的樹狀結構。 當我們在遊戲中進行這項操作時，就可以有從相機旋轉的樹狀結構、儲存所有影像，以及在執行時間為每個佈告欄卡片選取符合視圖方向的影像。 當映射是全息影像時，這也不適用。 左邊眼和右邊的差異讓它成為需要更高解析度的解析度，否則就只是平面、別名或重複。

在第二次嘗試時，我們嘗試盡可能地有最多的粒子。 當我們在將物件加入場景之前，額外繪製了它們並模糊它們之前，可以達到最佳的視覺效果。 這種方法的典型問題，是與我們一次可以繪製的粒子數目，以及它們所涵蓋的畫面區域數目仍維持60fps 的程度有關。 模糊產生的影像，以取得此雲端感覺通常是非常昂貴的作業。

![如果沒有紋理，這就是雲端看起來會像2% 不透明度的樣子。](images/clouds-without-texture-300px.jpg)

如果沒有紋理，這就是雲端看起來會像2% 不透明度的樣子。



如果是加總且有很多，表示我們會將多個四邊形放在彼此的上方，並重複地將相同的圖元加上陰影。 在 galaxy 的中央，相同的圖元在彼此上具有數百個四邊形，而且在全螢幕完成時，會有相當大的成本。

進行全螢幕雲端，並嘗試將它們模糊會是個不錯的想法，因此我們決定讓硬體為我們執行工作。

### <a name="a-bit-of-context-first"></a>先有一點內容

使用遊戲中的材質時，紋理大小很少會符合我們想要在其中使用的區域，但我們可以使用不同類型的材質篩選來取得圖形卡片，以從紋理的圖元 ([材質篩選](/previous-versions/visualstudio/visual-studio-2015/debugger/point-bilinear-trilinear-and-anisotropic-texture-filtering-variants)) 中插入所要的色彩。 感興趣的篩選是 [雙線性篩選](/windows/win32/direct3d9/bilinear-texture-filtering) ，會使用4個最接近的鄰近專案來計算任何圖元的值。

![在篩選之前的原始](images/texture-1.png)

![篩選後的結果](images/texture-2.png)

使用這個屬性，我們會看到每次嘗試將材質繪製到兩倍的區域時，都會使結果變得模糊。

我們不會轉譯成全螢幕，而且會遺失這些珍貴的毫秒數，因此我們會轉譯成螢幕的小版本。 然後，藉由複製此材質並以2倍的因數將它延展，我們會回到全螢幕，同時將進程中的內容模糊。

![x3 精密回到完整解析度。](images/galaxy-resolutions-300px.png)

x3 精密回到完整解析度。



如此一來，我們就能取得雲端部分，只剩下一小部分的原始成本。 我們不會在完整解析度上新增雲端，而是只繪製 1/第64次圖元，然後將材質延展回完整解析度。

![從 1/8 精密至完整解析;沒錯，有3個精密使用2的乘冪。](images/stars-upscaled-300px.jpg)

從 1/8 精密至完整解析;沒錯，有3個精密使用2的乘冪。


請注意，嘗試從大小的 1/第64次到全尺寸的結果看起來完全不同，因為在我們的安裝程式中，圖形卡仍會使用4個圖元來陰影放大較大的區域，並開始顯示成品。

然後，如果我們以較小的卡片新增完整的解析度星星，我們會取得完整的 galaxy：

![使用完整解析度星星的 galaxy 轉譯接近最終結果](images/full-galaxy-500px.png)

當我們在圖形上進行適當的追蹤之後，我們新增了一層雲端，將暫存點與我們在 Photoshop 中繪製的點交換，並新增一些其他色彩。 結果是一個銀河的方式，就是 Galaxy 我們的藝術和工程團隊都覺得很不錯，而且它符合我們的深度、數量和運動目標，全都不會讓 CPU 負擔。

![這是在3D 中的最終銀河方式。](images/final-galaxy-500px.jpg)

這是在3D 中的最終銀河方式。


### <a name="more-to-explore"></a>深入瞭解

我們已開放建立 Galaxy Explorer 應用程式的程式碼，並使其可在 [GitHub](https://github.com/Microsoft/GalaxyExplorer) 上提供，以供開發人員使用。

有興趣找出有關 Galaxy Explorer 開發流程的詳細資訊嗎？ 查看 [Microsoft HoloLens YouTube 頻道](https://www.youtube.com/playlist?list=PLZCHH_4VqpRj0Nl46J0LNRkMyBNU4knbL)上所有過去的專案更新。

## <a name="about-the-authors"></a>關於作者

<table style="border:0">
<tr>
<td style="border:0" width="60px"> <img alt="Picture of Karim Luccin at his desk" width="60" height="60" src="images/karim-thumb.jpg" /></td>
<td style="border:0"><b>Karim Luccin</b> 是軟體工程師和別致的視覺愛好者愛好者。 他是「Galaxy Explorer 的圖形工程師」。</td>
</tr>
<tr>
<td style="border:0" width="60px"> <img alt="Photo of art lead Andy Zibits" width="60" height="60" src="images/andy-avatar.png" /></td>
<td style="border:0"><b>Zibits</b> 是一種尖端的領導和空間愛好者，負責管理適用于 Galaxy Explorer 和曾的3d 模型化小組，以取得更多的粒子。</td>
</tr>
</table>


## <a name="see-also"></a>另請參閱
* [GitHub 上的 Galaxy Explorer](https://github.com/Microsoft/GalaxyExplorer)
* [YouTube 上的 Galaxy Explorer 專案更新](https://www.youtube.com/playlist?list=PLZCHH_4VqpRj0Nl46J0LNRkMyBNU4knbL)