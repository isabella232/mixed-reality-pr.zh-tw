---
title: 全像影像-穩定
description: 不同環境和畫面播放速率條件下的全像影像效能。
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、環境追蹤、TMP、
ms.openlocfilehash: f7a24d281bedd583d010baaf3840bcbe3fc7f877
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/03/2021
ms.locfileid: "101780883"
---
# <a name="hologram-stabilization"></a>全像穩定

## <a name="performance"></a>效能

為了讓基礎混合現實平臺和裝置產生最佳結果，請務必達到執行畫面播放速率。 目標畫面播放速率 (例如： 60 FPS 或 90 FPS) 會因不同的平臺和裝置而有所不同。 不過，混合現實應用程式的符合幀率將會有穩定的全像投影，以及有效率的標頭追蹤、手動追蹤等等。  

## <a name="environment-tracking"></a>環境追蹤

穩定的全像攝影轉譯非常依賴平臺 & 裝置的 head 姿勢追蹤。 Unity 將會從相機中的每個畫面格呈現每個畫面格，並由基礎平臺進行預估和提供。 如果此追蹤未正確遵循實際的 head 移動，則會以視覺化方式呈現全像影像。 這對 AR 裝置（例如 HoloLens）來說特別明顯，也很重要，因為使用者可以將虛擬全像是真實世界的關聯性。 效能對於可靠的標頭追蹤很重要，但也有 [其他重要功能](https://docs.microsoft.com/windows/mixed-reality/environment-considerations-for-hololens)。 影響使用者體驗的環境元素類型將取決於目標平臺細節。

## <a name="windows-mixed-reality"></a>Windows Mixed Reality

Windows Mixed Reality 平臺提供一些在平臺上穩定全息的 [參考](https://docs.microsoft.com/windows/mixed-reality/hologram-stability) 資料。 不過，開發人員可以利用一些重要的工具來改善使用者的全像影像視覺體驗。

### <a name="depth-buffer-sharing"></a>深度緩衝區共用

Unity 開發人員可以選擇將應用程式的深度緩衝區與平臺共用。 這會提供目前畫面格所在的全像投影的資訊，平臺可透過硬體輔助的程式（稱為 Late-Stage Reprojection）來利用穩定的全像影像。

#### <a name="late-stage-reprojection"></a>延遲階段 reprojection

在轉譯畫面格結束時，Windows Mixed Reality 平臺會採用應用程式所產生的色彩 & 深度轉譯目標，並轉換最後的畫面輸出，以考慮自從最後一個 head 姿勢預測之後的任何輕微移動。 應用程式的遊戲迴圈需要一些時間才能執行。 例如，在 60 FPS，這表示應用程式會採用 ~ 16.667 ms 來呈現畫面格。 雖然這看起來可能像是相比簡直小巫見大巫的時間，但使用者的位置和方向也會改變，而導致投影的新投射矩陣。 延遲階段 reprojection 會轉換最終影像中的圖元，以考慮這個新的觀點。

#### <a name="per-pixel-vs-stabilization-plane-lsr"></a>每個圖元與穩定平面 LSR

根據在 Windows Mixed Reality 裝置上執行的裝置端點和作業系統版本，Late-Stage 的 Reprojection 演算法會以圖元為單位執行，或經由 [穩定平面](https://docs.microsoft.com/windows/mixed-reality/hologram-stability#stabilization-plane)執行。

##### <a name="per-pixel-depth-based"></a>依圖元深度為基礎

每圖元深度型 reprojection 牽涉到利用深度緩衝區來修改每個圖元的影像輸出，進而在不同的距離進行穩定的全像投影。 例如，球體的1m 可能會在1千萬個離開的要件前面。 代表球體的圖元會有不同的轉換，而不是代表要件的圖元，如果使用者稍微略過它們的標頭。 每個圖元的 reprojection 會將每個圖元的距離差異納入考慮，以取得更精確的 reprojection。

##### <a name="stabilization-plane"></a>穩定平面

如果無法建立要與平臺共用的精確深度緩衝區，則另一種形式的 LSR 會利用穩定平面。 場景中的所有全像全像都能獲得一些穩定的情況，但在所需的平面中的全像投影，將會獲得最大硬體穩定 您可以透過 [Unity 提供](https://docs.microsoft.com/windows/mixed-reality/focus-point-in-unity)的 *HolographicSettings SetFocusPointForFrame* API，將平面的點和法線提供給平臺。

#### <a name="depth-buffer-format"></a>深度緩衝區格式

如果以 HoloLens 為目標以進行開發，強烈建議使用16位深度緩衝區格式（相較于24位）。 這可節省效能，但深度值的精確度較低。 若要補償較低的精確度，並避免進行 [z 對](https://en.wikipedia.org/wiki/Z-fighting)，建議您從 Unity 所設定的變更為1000m 預設值減少最 [遠的剪輯平面](https://docs.unity3d.com/Manual/class-Camera.html) 。

> [!NOTE]
> 如果使用 *16 位深度格式*，則樣板緩衝區所需的效果將無法運作，因為 Unity 不會在此設定中 [建立樣板緩衝區](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html) 。 相反地，選取 *24 位深度格式* 通常會建立 [8 位的樣板緩衝區](https://docs.unity3d.com/Manual/SL-Stencil.html)（如果適用于端點圖形平台）。

#### <a name="depth-buffer-sharing-in-unity"></a>Unity 中的深度緩衝區共用

為了利用深度型 LSR，開發人員必須採取兩個重要的步驟。

1. 在 [**編輯**  >  **專案設定**  >  **播放機**  >  **XR 設定**  >  **虛擬實境 sdk** ] 下，> 啟用 **深度緩衝區共用**
    1. 如果以 HoloLens 為目標，建議您也選取 **16 位深度格式** 。
1. 在螢幕上轉譯色彩時，也會呈現深度

Unity 中的不[透明 gameobject](https://docs.unity3d.com/Manual/StandardShaderMaterialParameterRenderingMode.html)通常會自動寫入深度。 不過，透明的 & 文字物件通常不會根據預設寫入深度。 如果使用 MRTK 標準著色器或文字網格 Pro，可以輕鬆地補救。

> [!NOTE]
> 若要快速判斷場景中的哪些物件不會以視覺化方式寫入深度緩衝區，可以使用 MRTK 設定檔中 *編輯器設定* 下的轉譯 [*深度緩衝區* 公用程式](MixedRealityConfigurationGuide.md#editor-utilities)。

##### <a name="transparent-mrtk-standard-shader"></a>透明 MRTK 標準著色器

針對使用 [MRTK 標準著色器](../features/README_MRTKStandardShader.md)的透明材質，請在 [偵測 *器* ] 視窗中選取要查看的材質。 然後按一下 [ *立即修正* ] 按鈕，將材質轉換成深度 (例如 ) 上的 Z-寫入。

之前

![修正 MRTK 標準著色器之前的深度緩衝區](../features/Images/Performance/DepthBufferFixNow_Before.PNG)

After

![深度緩衝區固定 MRTK 標準著色器](../features/Images/Performance/DepthBufferFixNow_After.PNG)

##### <a name="text-mesh-pro"></a>文字網格 Pro

若為文字網格 Pro 物件，請選取 TMP GameObject 以在偵測器中加以查看。 在 [材質] 元件下，將指派之材質的著色器切換為使用 MRTK TextMeshPro 著色器。

![文字網格 Pro 深度緩衝區修正](../features/Images/Performance/TextMeshPro-DepthBuffer-Fix.PNG)

##### <a name="custom-shader"></a>自訂著色器

如果撰寫自訂著色器，請將 [ZWrite 旗](https://docs.unity3d.com/Manual/SL-CullAndDepth.html) 標加入至 *傳遞* 區塊定義的頂端，以設定要寫入深度緩衝區的著色器。

```
Shader "Custom/MyShader"
{
    SubShader
    {
        Pass
        {
            ...
            ZWrite On
            ...
        }
    }
}
```

##### <a name="opaque-backings"></a>不透明 backings

如果上述方法不適用於指定的案例 (即 您可以使用 Unity UI) ，將另一個物件寫入深度緩衝區。 常見的範例是在場景中的浮動面板上使用 Unity UI 文字。 藉由讓面板不透明或至少寫入深度，此面板 & 的文字將會由平臺穩定，因為它們的 z 值彼此接近。

### <a name="worldanchors-hololens"></a>WorldAnchors (HoloLens) 

除了確保符合正確的設定，以確保視覺穩定性，請務必確保全像地理位置在正確的實體位置維持穩定。 若要在實體空間中通知平臺的重要位置，開發人員可以在需要保持在同一處的 Gameobject 上利用 [WorldAnchors](https://docs.unity3d.com/ScriptReference/XR.WSA.WorldAnchor.html) 。 [WorldAnchor](https://docs.unity3d.com/ScriptReference/XR.WSA.WorldAnchor.html)是新增至 GameObject 的元件，可對該物件的轉換取得絕對控制權。

HoloLens 這類裝置會不斷地掃描和學習環境。 因此，當 HoloLens 追蹤移動 & 空間中的位置時，將會更新其估價，並 [調整 Unity 座標系統](https://docs.microsoft.com/windows/mixed-reality/coordinate-systems-in-unity)。 例如，如果在一開始就將 GameObject 從相機放置1百萬個，則在 HoloLens 追蹤環境時，可能會發現 GameObject 所在的實體點實際上是 1.1 m。 這會導致全息全像離開。 將 WorldAnchor 套用至 GameObject，可讓錨點控制物件的轉換，讓物件保持在正確的實體位置 (也就是 在執行時間) 更新為 1.1 m 而不是1m。 若要跨應用程式會話保存 [WorldAnchors](https://docs.unity3d.com/ScriptReference/XR.WSA.WorldAnchor.html) ，開發人員可以使用 [WorldAnchorStore](https://docs.unity3d.com/ScriptReference/XR.WSA.Persistence.WorldAnchorStore.html) 來 [儲存和載入 WorldAnchors](https://docs.microsoft.com/windows/mixed-reality/persistence-in-unity)。

> [!NOTE]
> 將 WorldAnchor 元件新增至 GameObject 之後，就無法修改該 GameObject 的轉換 (例如 transform。 position = x) 。 開發人員必須移除 WorldAnchor 來編輯轉換。

```c#
WorldAnchor m_anchor;

public void AddAnchor()
{
    this.m_anchor = this.gameObject.AddComponent<WorldAnchor>();
}

public void RemoveAnchor()
{
    DestroyImmediate(m_anchor);
}
```

## <a name="see-also"></a>另請參閱

- [效能](../Performance/PerfGettingStarted.md)
- [HoloLens 的環境考慮](https://docs.microsoft.com/windows/mixed-reality/environment-considerations-for-hololens)
- [全像 Windows 混合式的穩定性](https://docs.microsoft.com/windows/mixed-reality/hologram-stability)
- [Unity 中的焦點](https://docs.microsoft.com/windows/mixed-reality/focus-point-in-unity)
- [Unity 中的座標系統](https://docs.microsoft.com/windows/mixed-reality/coordinate-systems-in-unity)
- [Unity 中的持續性](https://docs.microsoft.com/windows/mixed-reality/persistence-in-unity)
- [瞭解混合現實的效能](https://docs.microsoft.com/windows/mixed-reality/understanding-performance-for-mixed-reality)
- [對 Unity 的效能建議](https://docs.microsoft.com/windows/mixed-reality/performance-recommendations-for-unity)
