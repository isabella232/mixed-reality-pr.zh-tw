---
title: Unity 中的攝影機設定
description: 瞭解如何設定及使用 Unity 的主要攝影機進行 Windows Mixed Reality 開發以進行全像轉譯。
author: keveleigh
ms.author: kurtie
ms.date: 03/25/2021
ms.topic: article
keywords: holotoolkit，mixedrealitytoolkit，mixedrealitytoolkit-unity，全像轉譯，全像全像，全像投影、全像投影、聚焦點、深度緩衝區、僅限方向、位置、不透明、透明、剪輯、混合現實耳機、windows mixed reality 耳機、虛擬實境耳機
ms.openlocfilehash: 1ac8c16e7bdd6b85b05c837e1a27fbd1e4cf4489ccb03d10ea5e952b2656cbe8
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2021
ms.locfileid: "115212229"
---
# <a name="camera-setup-in-unity"></a>Unity 中的攝影機設定

當您磨損混合現實耳機時，它就會變成您的全像世界的中心。 Unity [攝影機](https://docs.unity3d.com/Manual/class-Camera.html) 元件會自動處理 stereoscopic 轉譯，並遵循您的頭部移動和旋轉。 不過，若要充分優化視覺品質和全像全像的 [穩定性](../platform-capabilities-and-apis/hologram-stability.md)，您應該設定如下所述的相機設定。

## <a name="hololens-vs-vr-immersive-headsets"></a>HoloLens vs VR 沉浸式耳機

Unity 攝影機元件上的預設設定適用于傳統3D 應用程式，因為它們沒有真實世界，所以需要像 skybox 的背景。

* 在 **[沉浸式耳機](../../discover/immersive-headset-hardware-details.md)** 上執行時，您正在轉譯使用者看到的所有內容，因此您可能會想要保留 skybox。
* 不過，在 [HoloLens](/hololens/hololens2-hardware)的全像攝影 **耳機** 上執行時，真實世界應該會出現在相機所呈現的所有內容後方。 將相機背景設定為 HoloLens 的透明 (，黑色會轉譯為透明) 而不是 Skybox 材質：
    1. 選取階層面板中的主要攝影機
    2. 在 [檢查] 面板中，尋找相機元件，並將 [清除旗標] 下拉式清單從 [Skybox] 變更為 [純色]
    3. 選取背景色彩選擇器，並將 RGBA 值變更為 (0、0、0、0) 
        1. 如果從程式碼設定此值，您可以使用 Unity 的 [`Color.clear`](https://docs.unity3d.com/ScriptReference/Color-clear.html)

[!INCLUDE[](includes/camera/opaque-camera-include.md)]

## <a name="camera-setup"></a>相機設定

無論您正在開發何種體驗，主要攝影機一律是連接到您裝置之前端掛接顯示器的主要身歷聲轉譯元件。 如果您想像使用者的開始位置是 (X：0，Y：0，Z： 0) ，將會比較容易配置您的應用程式。 因為主要攝影機正在追蹤使用者的標頭移動，所以可以設定主要攝影機的開始位置來設定使用者的開始位置。

您需要做的主要選擇是您是針對 HoloLens 或 VR 沉浸式耳機進行開發。 當您取得該內容之後，請跳至適用的任何安裝程式區段。

### <a name="hololens-camera-setup"></a>HoloLens 攝影機設定

針對 HoloLens 的應用程式，您必須針對想要鎖定場景環境的任何物件使用錨點。 我們建議使用未系結的空間來最大化穩定性，並在多個房間內建立錨點。

[!INCLUDE[](includes/camera/hololens-setup-include.md)]

### <a name="vr-camera-setup"></a>VR 攝影機設定

Windows Mixed Reality 透過房間規模的應用程式，支援橫跨各種[體驗規模](../../design/coordinate-systems.md#mixed-reality-experience-scales)的應用程式，從僅限方向和已安置規模的應用程式。 在 HoloLens 上，您可以進一步建立全球規模的應用程式，讓使用者超越5個計量，探索整個大樓的整個樓層。

在 Unity 中打造混合現實體驗的第一步，是要判斷您的應用程式將設為目標的 [體驗調整](../../design/coordinate-systems.md) ：

* [方向或固定規模](../../design/coordinate-systems.md#building-an-orientation-only-or-seated-scale-experience)
* [站上或房間規模](../../design/coordinate-systems.md#building-a-standing-scale-or-room-scale-experience)
* [全球規模](../../design/coordinate-systems.md#building-a-world-scale-experience)

#### <a name="room-scale-or-standing-experiences"></a>會議室規模或長期體驗

> [!NOTE]
> 如果您正在建立 HL2，我們建議您建立眼睛層級的體驗，或考慮使用 [場景理解](../platform-capabilities-and-apis/scene-understanding-sdk.md) ，以瞭解場景的樓層原因。

[!INCLUDE[](includes/camera/vr-setup-standing-include.md)]

#### <a name="seated-experiences"></a>上一位體驗

[!INCLUDE[](includes/camera/vr-setup-seated-include.md)]

### <a name="setting-up-the-camera-background"></a>設定相機背景

如果您使用的是 MRTK，則會自動設定並管理相機的背景。 針對 XR SDK 或舊版的 WSA 專案，建議您在 HoloLens 上將攝影機的背景設定為純黑色，並保留 skybox 的 VR。

## <a name="using-multiple-cameras"></a>使用多個相機

當場景中有多個相機元件時，Unity 會根據哪一個 GameObject 具有 MainCamera 標記來得知要使用的相機來進行 stereoscopic 轉譯。 在舊版 XR 中，它也會使用此標記來同步處理標頭追蹤。 在 XR SDK 中，head 追蹤是由附加至相機的 TrackedPoseDriver 腳本驅動。

## <a name="sharing-depth-buffers"></a>共用深度緩衝區

共用您的應用程式深度緩衝區來 Windows 每個畫面格，將會根據您要轉譯的耳機類型，為您的應用程式提供兩種影像內的增強功能：

* 當提供深度緩衝區時， **VR 沉浸式耳機** 可以處理位置 reprojection，調整您的全像位置和方向的 misprediction。
* **HoloLens 耳機** 有幾個不同的方法。 當提供深度緩衝區時，HoloLens 1 會自動選取[焦點點](focus-point-in-unity.md)，並在與大部分內容交集的平面上優化全像全像的穩定性。 HoloLens 2 將會使用深度 LSR 來穩定內容[ (請參閱備註) ](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint)。

[!INCLUDE[](includes/camera/depth-buffer-include.md)]

## <a name="using-clipping-planes"></a>使用裁剪平面

轉譯內容太接近使用者可能會對混合現實感到不舒服。 您可以調整攝影機元件上的 [近距離和目前的剪切平面](../platform-capabilities-and-apis/hologram-stability.md#hologram-render-distances) 。

1. 選取 **階層面板中的****主要攝影機**
2. 在 [偵測 **器** ] 面板中，尋找 **相機** 元件 **裁剪平面** ，然後將 **近端** textbox 從 **0.3** 變更為 **0.85**。 更深入轉譯的內容可能會導致使用者不適感，而且應該根據轉譯 [距離指導方針](../platform-capabilities-and-apis/hologram-stability.md#hologram-render-distances)來避免。

## <a name="recentering-the-camera"></a>Recentering 攝影機

如果您要建立 [大規模的體驗](../../design/coordinate-systems.md)，您可以藉由呼叫 XR，在使用者目前的標頭位置 recenter Unity 的世界原點 **[。InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)** 在舊版 XR 中的 Recenter 方法或 TRYRECENTER SDK 中的 **[XRInputSubsystem. XR](https://docs.unity3d.com/ScriptReference/XR.XRInputSubsystem.TryRecenter.html)** 方法。

## <a name="teleportation"></a>遙傳

這項功能通常會保留給 VR 體驗：

[!INCLUDE[](includes/camera/teleport-include.md)]

## <a name="reprojection-modes"></a>Reprojection 模式

HoloLens 和沉浸式耳機都會 reproject 您的應用程式所轉譯的每個畫面格，以在發出光子時，針對使用者的實際標上任何 misprediction 進行調整。

依照預設：

* 如果應用程式為指定的框架提供深度緩衝區，則 **VR 沉浸式耳機** 會負責定位 reprojection。 沉浸式耳機也會調整您的全像位置和方向的 misprediction。 如果未提供深度緩衝區，則系統只會正確地校正 mispredictions。
* HoloLens 2 的全像 **耳機** 一樣，會負責處理應用程式是否提供深度緩衝區的位置 reprojection。 HoloLens 的位置 reprojection 可能沒有深度緩衝區，因為轉譯通常會因為真實世界提供的穩定背景而稀疏。

[!INCLUDE[](includes/camera/reprojection-include.md)]

## <a name="next-development-checkpoint"></a>下一個開發檢查點

如果您是遵循我們所配置的 Unity 開發旅程，您將會在探索 MRTK 核心構成要素的過程中進行。 接下來，您可以繼續進行下一個建置組塊：

> [!div class="nextstepaction"]
> [目光](gaze-in-unity.md)

或者，直接跳到混合實境平台功能和 API 的主題：

> [!div class="nextstepaction"]
> [共用體驗](shared-experiences-in-unity.md)

您可以隨時回到 [Unity 開發檢查點](unity-development-overview.md#2-core-building-blocks)。

## <a name="see-also"></a>另請參閱

* [全像投影穩定性](../platform-capabilities-and-apis/hologram-stability.md)
* [體驗規模調整](../../design/coordinate-systems.md#mixed-reality-experience-scales)
* [空間階段](../../design/coordinate-systems.md#stage-frame-of-reference)
* [Unity 中的追蹤遺失](tracking-loss-in-unity.md)
* [空間錨點](../../design/spatial-anchors.md)
* [Unity 中的持續性](persistence-in-unity.md)
* [Unity 中的共用體驗](shared-experiences-in-unity.md)
* [Azure Spatial Anchors](/azure/spatial-anchors)
* [適用于 Unity 的 Azure 空間錨點 SDK](/dotnet/api/Microsoft.Azure.SpatialAnchors)