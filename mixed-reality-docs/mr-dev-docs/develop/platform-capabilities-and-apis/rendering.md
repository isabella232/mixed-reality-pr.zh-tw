---
title: 轉譯
description: 瞭解全像攝影轉譯如何讓您的應用程式在全球各地的使用者，于全球的確切位置繪製一個全像投影。
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: 轉譯，全像影像
ms.openlocfilehash: eea302aa31829bb91ccf1cc8ad55faed5a380d17
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583127"
---
# <a name="rendering"></a>轉譯

全像影像呈現可讓您的應用程式在世界各地的精確位置繪製一個全像，無論是精確地放在實體世界或您所建立的虛擬領域中。 全[像是音效和光線所組成](../../discover/hologram.md)的物件。 呈現可讓您的應用程式新增燈光。

## <a name="device-support"></a>裝置支援

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>功能</strong></td>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens (第一代) </strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="../../discover/immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></td>
    </tr>
     <tr>
        <td>轉譯</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
</table>

## <a name="holographic-rendering"></a>全像攝影的呈現

全像攝影轉譯的關鍵在於瞭解正在使用的裝置類型。 具有 **觀看顯示** 的裝置（例如 [HoloLens](/hololens/hololens1-hardware)）會將燈光新增至世界。 黑色圖元是完全透明的，而較亮的圖元則逐漸不透明。 由於顯示器的光線是從真實世界的光線加入，因此白色圖元是半透明的。

雖然 stereoscopic 轉譯針對您的全像投影提供一個深度的提示，但新增 [接地效果](../../design/interaction-fundamentals.md) 可協助使用者更輕鬆地看到全息圖的表面。 其中一個接地技巧是在附近表面上的全像投影周圍加上發光，然後針對這項發光呈現陰影。 如此一來，您的陰影就可以從環境中減去燈光。 [空間音效](../../design/spatial-sound.md) 是另一個重要的深度提示，可讓使用者知道全像影像距離和相對位置的原因。

具有不 **透明顯示** 的裝置（例如 [Windows Mixed Reality 沉浸式耳機](../../discover/immersive-headset-hardware-details.md)）會封鎖世界。 黑色圖元是實心的黑色，而任何其他色彩會顯示為使用者的色彩。 您的應用程式會負責呈現使用者所看到的所有內容。 這可讓您更重要的是維護持續的重新整理頻率，讓使用者擁有舒適的體驗。

## <a name="predicted-rendering-parameters"></a>預測的呈現參數

 (HoloLens 和沉浸式耳機的混合現實耳機) 會持續追蹤使用者的標題相對於其周圍的位置和方向。 當您的應用程式開始準備它的下一個畫面時，系統會預測使用者在該畫面上顯示的確切時間。 根據這種預測，系統會計算要用於該框架的視圖和投射轉換。 您的應用程式 **必須使用這些轉換來產生正確的結果**。 如果未使用系統提供的轉換，則產生的影像不會與真實世界一致，進而導致使用者不適感。

> [!NOTE]
> 為了精確地預測新框架何時會到達顯示器，系統會不斷地測量應用程式轉譯管線的有效端對端延遲。 雖然系統會調整為轉譯管線的長度，但您可以將該管線保持在最短的時間，藉以改善全像影像的穩定性。

使用先進技術來加強系統預測的應用程式，可以覆寫系統檢視和投影轉換。 這些應用程式仍然必須使用系統提供的轉換，作為其自訂轉換的基礎，以產生有意義的結果。

## <a name="other-rendering-parameters"></a>其他呈現參數

當轉譯框架時，系統會指定應用程式應繪製的後置緩衝區區。 此區通常小於框架緩衝區的完整大小。 無論是什麼區大小，一旦應用程式呈現框架之後，系統就會 upscales 影像以填滿整個顯示器。

如果應用程式無法以所需的重新整理頻率轉譯， [系統轉譯參數可以設定](/uwp/api/Windows.Graphics.Holographic.HolographicViewConfiguration#Windows_Graphics_Holographic_HolographicViewConfiguration) 為減少記憶體壓力和轉譯成本，代價是增加圖元別名。 您也可以變更背景緩衝區格式，讓某些應用程式可以協助改善記憶體頻寬和圖元輸送量。

要求您的應用程式轉譯時，轉譯的圖格、解析度和畫面播放速率可能也會從框架變更為框架，而且可能會在左右眼睛之間有差異。 例如，當 [mixed reality capture](/hololens/holographic-photos-and-videos) (MRC) 處於作用中狀態，且未加入宣告 [相片/攝影機視圖](/uwp/api/Windows.Graphics.Holographic.HolographicViewConfigurationKind#Windows_Graphics_Holographic_HolographicViewConfigurationKind) 設定時，可能會以較大的 FOV 或解析度來呈現一眼。

針對任何指定的框架，您的應用程式 *必須* 使用系統所提供的視圖轉換、投影轉換和視口解析來呈現。 此外，您的應用程式絕對不能假設任何轉譯或 view 參數都保持從框架到框架固定。 Unity 等引擎會在自己的攝影機物件中為您處理所有的轉換，如此一來，使用者的實際移動和系統的狀態一律會被遵守。 如果您的應用程式允許使用者透過全球進行虛擬移動 (例如，使用遊戲台上的操縱杆) ，您可以在相機上方新增上層的 rig 物件來四處移動。 這會導致相機反映使用者的虛擬和實際動作。 如果您的應用程式修改系統所提供的視圖轉換、投影轉換或視口維度，它必須呼叫適當的覆 [寫 API](/uwp/api/Windows.Graphics.Holographic.HolographicCameraPose#Windows_Graphics_Holographic_HolographicCameraPose)來通知系統。

為了增強您的全像轉譯的穩定性，您的應用程式應該提供 Windows 每個畫面格用於轉譯的深度緩衝區。 如果您的應用程式確實提供深度緩衝區，它應該會有一致的深度值，並以從相機的計量深度表示。 這可讓系統使用您的每個圖元深度資料，在使用者的前端與預測的位置稍微稍微位移時，使用您的每個圖元深度資料來提供更佳的穩定內容。 如果您無法提供深度緩衝區，您可以提供焦點點和正常，定義可剪下大部分內容的平面。 如果同時提供深度緩衝區和焦點平面，則系統可能會使用這兩者。 尤其是當您的應用程式顯示正在移動的全息影像時，提供深度緩衝區和焦點點（包含速度向量）會很有説明。

如需有關本主題的低層級詳細資料，請參閱 [DirectX 文章中](../native/rendering-in-directx.md) 的轉譯。

## <a name="holographic-cameras"></a>全像攝影機

Windows Mixed Reality 引進了 **全息攝影機** 的概念。 全像是在3D 圖形文字中找到的繁體攝影機，它們會定義外建的 (位置和方向) 和內建相機屬性。  (例如，[視圖] 會用來查看虛擬3D 場景。 ) 不同于傳統3D 相機，應用程式無法控制攝影機的位置、方向和內建屬性。 而是由使用者的移動隱含控制全像攝影相機的位置和方向。 使用者的移動會透過「視圖」轉換，依畫面格逐一轉送至應用程式。 同樣地，相機的內建屬性是由裝置的校正型器件所定義，並透過投影轉換依畫面轉送。

一般情況下，您的應用程式會針對單一身歷聲攝影機轉譯。 健全的轉譯迴圈將會支援多個相機，並同時支援 mono 和身歷聲攝影機。 例如，系統可能會要求您的應用程式在使用者啟動像是「 [混合現實](/hololens/holographic-photos-and-videos) 」 () 的功能時，根據耳機圖形，從替代的觀點來呈現。 可支援多個相機的應用程式會選擇其可支援的相機[類型](/uwp/api/Windows.Graphics.Holographic.HolographicViewConfigurationKind#Windows_Graphics_Holographic_HolographicViewConfigurationKind)[來取得](/uwp/api/Windows.Graphics.Holographic.HolographicViewConfiguration#Windows_Graphics_Holographic_HolographicViewConfiguration)它們。

## <a name="volume-rendering"></a>磁碟區呈現

在3D 中轉譯醫療/Mri 或工程磁片區時，通常會使用 [磁片](volume-rendering.md) 區轉譯技術。 這些技術在混合的現實中可能很有趣，因為使用者可以藉由移動其頭部，自然地從主要角度來查看這類音量。

## <a name="supported-resolutions-on-hololens-first-gen"></a>HoloLens (第一代) 支援的解決方案

* 最大的區數大小是 [HolographicDisplay](/uwp/api/windows.graphics.holographic.holographicdisplay)的屬性。 HoloLens 預設會設定為最大的最大區大小，也就是 720p (1268x720) 。
* 您可以藉由在 HolographicCamera 上設定 ViewportScaleFactor 來變更此區大小。 此比例因數的範圍介於0到1之間。
* HoloLens (第一代) 的最低支援的區大小是720p 的50%，也就是 360p (634x360) 。 這是0.5 的 ViewportScaleFactor。
* 由於視覺效果降低，因此不建議使用低於540p 的任何元素，但是可以用來識別圖元填滿率的瓶頸。

## <a name="supported-resolutions-on-hololens-2"></a>HoloLens 2 支援的解決方案

* 目前和最大支援的轉譯目標大小是 [view](/uwp/api/Windows.Graphics.Holographic.HolographicViewConfiguration#Windows_Graphics_Holographic_HolographicViewConfiguration)設定的屬性。 預設會將 HoloLens 2 設定為最大轉譯目標大小（預設為1440x936）。
* 應用程式可以藉由呼叫 RequestRenderTargetSize 方法來要求新的呈現目標大小，藉以變更轉譯目標緩衝區的大小。 將會選擇新的轉譯目標大小，以符合或超過要求的呈現目標大小。 此 API 會變更呈現目標緩衝區的大小，這需要在 GPU 上重新配置記憶體。 這包括：轉譯目標大小可相應減少以降低 GPU 上的記憶體壓力，而且不應以較高的頻率呼叫這個方法。
* 應用程式仍然可以用與 HoloLens 1 相同的方式變更其區大小。 GPU 上沒有額外的記憶體重新配置，因此可以在較高的頻率進行變更，但無法用來降低 GPU 上的記憶體壓力。
* HoloLens 2 上最低支援的區大小為634x412，當預設轉譯目標大小正在使用中時，ViewportScaleFactor 約為0.44。
* 如果提供的轉譯目標大小小於最低支援的區大小，則會忽略此區縮放比例。
* 由於視覺效果降低，因此不建議使用低於540p 的任何元素，但是可以用來識別圖元填滿率的瓶頸。



## <a name="see-also"></a>另請參閱
* [全像投影穩定性](hologram-stability.md)
* [DirectX 中的呈現](../native/rendering-in-directx.md)