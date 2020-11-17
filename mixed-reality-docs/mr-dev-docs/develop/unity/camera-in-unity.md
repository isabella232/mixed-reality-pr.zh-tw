---
title: Unity 中的相機
description: 如何使用 Unity 的主要攝影機進行 Windows Mixed Reality 開發以進行全像轉譯。
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit，mixedrealitytoolkit，mixedrealitytoolkit-unity，全像轉譯，全像全像，全像投影、全像投影、聚焦點、深度緩衝區、僅限方向、位置、不透明、透明、剪輯、混合現實耳機、windows mixed reality 耳機、虛擬實境耳機
ms.openlocfilehash: c3c470634e2c5c9445ae8c0a29621971de22a92b
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2020
ms.locfileid: "94677617"
---
# <a name="camera-in-unity"></a>Unity 中的相機

當您磨損混合現實耳機時，它就會變成您的全像世界的中心。 當您的專案在 [Windows Store Player 設定]) 的 [其他設定] 區段中，Windows Mixed Reality 選取 [虛擬實境支援] 時，Unity [攝影機](https://docs.unity3d.com/Manual/class-Camera.html) 元件會自動處理 stereoscopic 轉譯，並遵循您 (的頭部移動和旋轉。 這可能會在舊版 Unity 中列為「Windows 全像」。

不過，若要充分優化視覺品質和全像全像的 [穩定性](../platform-capabilities-and-apis/hologram-stability.md)，您應該設定如下所述的相機設定。

>[!NOTE]
>這些設定必須套用至應用程式每個場景中的相機。
>
>依預設，當您在 Unity 中建立新場景時，它會包含階層中的主要攝影機 GameObject，其中包括相機元件，但未正確套用下列設定。

## <a name="holographic-vs-immersive-headsets"></a>全像沉浸式耳機

Unity 攝影機元件上的預設設定適用于需要類似 skybox 背景的傳統3D 應用程式，因為它們沒有真實世界。

* 在 **[沉浸式耳機](../../discover/immersive-headset-hardware-details.md)** 上執行時，您會轉譯使用者看到的所有專案，因此您可能會想要保留 skybox。
* 不過，在 [HoloLens](../../hololens-hardware-details.md)這類的全像攝影 **耳機** 上執行時，真實世界應該會出現在相機轉譯的所有內容後方。 若要這樣做，請將攝影機背景設定為在 HoloLens 中 (透明，黑色呈現為透明) ，而不是 Skybox 材質：
    1. 選取階層面板中的主要攝影機
    2. 在 [檢查] 面板中，尋找相機元件，並將 [清除旗標] 下拉式清單從 [Skybox] 變更為 [純色]
    3. 選取背景色彩選擇器，並將 RGBA 值變更為 (0、0、0、0) 

您可以藉由檢查 [HolographicSettings IsDisplayOpaque](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.IsDisplayOpaque.html)，使用腳本來判斷耳機是否為沉浸式或全像攝影。

## <a name="positioning-the-camera"></a>定位相機

如果您想像使用者的開始位置是 (X：0，Y：0，Z： 0) ，將會比較容易配置您的應用程式。 因為主要攝影機正在追蹤使用者的標頭移動，所以可以設定主要攝影機的開始位置來設定使用者的開始位置。

1. 選取 [階層] 面板中的 [主要攝影機]
2. 在 [偵測器] 面板中，尋找 [轉換] 元件，並將位置從 (X：0，Y：1，Z：-10) 變更為 (X：0，Y：0，Z： 0) 

   ![Unity 中的 [偵測器] 窗格中的相機](images/maincamera-350px.png)  
   *Unity 中的 [偵測器] 窗格中的相機*

## <a name="clip-planes"></a>剪輯平面

轉譯內容太接近使用者可能會對混合現實感到不舒服。 您可以調整攝影機元件上的 [近距離和目前的剪切平面](../platform-capabilities-and-apis/hologram-stability.md#hologram-render-distances) 。

1. 選取階層面板中的主要攝影機
2. 在 [偵測器] 面板中，尋找相機元件裁剪平面，然後將近端 textbox 從0.3 變更為85。 更深入轉譯的內容可能會導致使用者不適感，而且應該根據轉譯 [距離指導方針](../platform-capabilities-and-apis/hologram-stability.md#hologram-render-distances)來避免。

## <a name="multiple-cameras"></a>多個相機

當場景中有多個相機元件時，Unity 會藉由檢查有 MainCamera 標記的 GameObject，知道要使用哪一種相機來 stereoscopic 轉譯和標頭追蹤。

## <a name="recentering-a-seated-experience"></a>Recentering 上一體驗

如果您要建立 [大規模的體驗](../../design/coordinate-systems.md)，您可以藉由呼叫 XR，在使用者目前的標頭位置 recenter Unity 的世界原點 **[。InputTracking. Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)** 方法。

## <a name="reprojection-modes"></a>Reprojection 模式

HoloLens 和沉浸式耳機都會 reproject 您的應用程式所轉譯的每個畫面格，以在發出光子時，針對使用者的實際標上任何 misprediction 進行調整。

依照預設：

* 如果應用程式為指定的框架提供深度緩衝區，那麼 **沉浸式耳機** 將會執行位置 reprojection，並調整您的全像位置和方向的 misprediction。  如果未提供深度緩衝區，則系統只會正確地校正 mispredictions。
* HoloLens 這類的全像 **耳機** 會執行位置 reprojection，無論應用程式是否提供深度緩衝區。  在 HoloLens 上可能沒有深度緩衝區的位置 reprojection，因為轉譯通常會因為真實世界提供的穩定背景而稀疏。

如果您知道您要使用最嚴格的主體鎖定內容來建立 [僅限方向的體驗](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience) (例如360度的影片內容) ，您可以將 reprojection 模式明確設定為僅限方向，只要將 [HolographicSettings ReprojectionMode](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.ReprojectionMode.html) 設定為 [HolographicReprojectionMode. OrientationOnly](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.HolographicReprojectionMode.html)。

## <a name="sharing-your-depth-buffers-with-windows"></a>使用 Windows 共用深度緩衝區

將您的應用程式深度緩衝區共用到 Windows 每個畫面格，將會根據您要轉譯的耳機類型，為您的應用程式提供兩個最多的全像全像全像全像：

* 當提供深度緩衝區時，**沉浸式耳機** 可以執行位置 reprojection，調整您的全像位置和方向的 misprediction。
* 全像 **耳機** 有幾種不同的方法。 當提供深度緩衝區時，HoloLens 1 會自動選取 [焦點點](focus-point-in-unity.md) ，並在與大部分內容交集的平面上優化全像影像穩定性。 HoloLens 2 將會使用深度 LSR 來穩定內容 [ (請參閱備註) ](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint)。

設定您的 Unity 應用程式是否會提供 Windows 的深度緩衝區：

1. 移至 [**編輯**  >  **專案設定**  >  **播放機**  >  **] 通用 Windows 平臺** 索引標籤  >  **XR 設定**]。
2. 展開 **WINDOWS MIXED REALITY SDK** 專案。
3. 核取或取消核取 [ **啟用深度緩衝區共用** ] 核取方塊。  這項功能預設會在建立的新專案中檢查，因為這項功能已新增至 Unity，而且預設會針對已升級的舊專案取消核取。

將深度緩衝區提供給 Windows 可以改善視覺品質，只要 Windows 可以精確地將深度緩衝區中的正規化的每個圖元深度值對應到量值，就可以使用您在主要攝影機上的 Unity 中所設定的近乎和 far 平面。  如果您的轉譯階段以一般方式處理深度值，您通常應該會在這裡進行，不過在顯示到現有的色彩圖元時，透明轉譯會寫入深度緩衝區的行程可能會使 reprojection 混淆。  如果您知道您的轉譯行程將會離開許多具有不正確深度值的最終深度圖元，您可能會被取消核取 [啟用深度緩衝區共用]，以取得更佳的視覺品質。 # # 下一個開發檢查點

## <a name="automatic-scene-and-camera-setup-with-mixed-reality-toolkit-v2"></a>混合現實工具組 v2 的自動場景和攝影機設定

遵循 [逐步](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html) 指南，將混合現實工具組 v2 新增至 Unity 專案，它將會自動設定您的專案。 您也可以使用下一節中的指南，手動設定沒有 MRTK 的專案。

## <a name="next-development-checkpoint"></a>下一個開發檢查點

依循我們配置的 Unity 開發檢查點旅程，此時您會探索 MRTK核心建置組塊。 接下來，您可以繼續進行下一個建置組塊：

> [!div class="nextstepaction"]
> [目光](gaze-in-unity.md)

或者，直接跳到混合實境平台功能和 API 的主題：

> [!div class="nextstepaction"]
> [共用體驗](shared-experiences-in-unity.md)

您可以隨時回到 [Unity 開發檢查點](unity-development-overview.md#2-core-building-blocks)。

## <a name="see-also"></a>另請參閱

* [全像投影穩定性](../platform-capabilities-and-apis/hologram-stability.md)
* [MixedRealityToolkit 主要攝影機. 預製專案](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Input/Prefabs)
