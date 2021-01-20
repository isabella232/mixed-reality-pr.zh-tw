---
title: Unreal 中的手勢追蹤
description: 瞭解如何在 Unreal 混合現實應用程式中使用手追蹤輸入、姿勢、手形網格和即時連結動畫。
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
keywords: Windows Mixed Reality、手形追蹤、Unreal、Unreal 引擎4、UE4、HoloLens、HoloLens 2、混合現實、開發、功能、檔、指南、全像投影、遊戲開發、混合現實耳機、windows Mixed Reality 耳機、虛擬實境耳機
ms.openlocfilehash: 1888258321af978ca52623008193e6dae94833a8
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/20/2021
ms.locfileid: "98581114"
---
# <a name="hand-tracking-in-unreal"></a>Unreal 中的手勢追蹤

手追蹤系統會使用某人的手掌和手指做為輸入。 每個手指的位置和旋轉、完整的掌上和手手勢的資料都可以使用。 從 Unreal 4.26 開始，手動追蹤是以 Unreal HeadMountedDisplay 外掛程式為基礎，並在所有 XR 平臺和裝置上使用通用 API。 Windows Mixed Reality 和 OpenXR 系統的功能都相同。

## <a name="hand-pose"></a>手姿勢

手姿勢可讓您追蹤並使用使用者的手和手指作為輸入，可在藍圖和 c + + 中存取。 Unreal API 會將資料傳送為座標系統，並與 Unreal 引擎同步處理刻度。

![手形基本架構](../native/images/hand-skeleton.png)

[!INCLUDE[](includes/tabs-tracking-hand-pose.md)]

## <a name="hand-live-link-animation"></a>手實況連結動畫

使用 [即時連結外掛程式](https://docs.unrealengine.com/Engine/Animation/LiveLinkPlugin/index.html)可對動畫公開手。

如果已啟用 Windows Mixed Reality 和即時連結外掛程式：
1. 選取 [ **Window > 即時連結** ] 以開啟 [即時連結編輯器] 視窗。
2. 選取 **來源** 並啟用 **Windows Mixed Reality 手追蹤來源**

![即時連結來源](images/unreal/live-link-source.png)

啟用來源並開啟動畫資產之後，展開 [**預覽場景**] 索引標籤中的 [**動畫**] 區段，也會看到其他選項。

![即時連結動畫](images/unreal/live-link-animation.png)

手形動畫階層與中的相同 `EWMRHandKeypoint` 。 動畫可以使用 **WindowsMixedRealityHandTrackingLiveLinkRemapAsset** 重定目標：

![即時連結動畫2](images/unreal/live-link-animation2.png)

它也可以在編輯器中進行子類別化：

![即時連結重新對應](images/unreal/live-link-remap.png)

## <a name="hand-mesh"></a>手上網格

### <a name="hand-mesh-as-a-tracked-geometry"></a>以手動方式作為追蹤幾何

> [!IMPORTANT]
> 在 OpenXR 中取得作為追蹤幾何的手勢需要您呼叫 Set 使用具有 **啟用追蹤幾何** 的 **手形網格**。

若要啟用該模式，您應該呼叫 Set 使用具有 **啟用追蹤幾何** 的 **手形網格**：

![事件開始播放的藍圖已連線到 set use 手勢函式已啟用追蹤幾何模式](images/unreal-hand-tracking-img-08.png)

> [!NOTE]
> 這兩種模式都不可能同時啟用。 如果您啟用了一個，另一個會自動停用。

### <a name="accessing-hand-mesh-data"></a>存取手形網格資料

![手上網格](images/unreal/hand-mesh.png)

在您可以存取手中的資料之前，您必須：
- 選取您的 **ARSessionConfig** 資產，展開 [ **AR 設定-> 世界對應** 設定]，然後核取 [ **從追蹤的幾何產生網格資料**]。

以下是預設的網格參數：

1.  使用網格資料進行遮蔽
2.  產生網格資料的衝突
3.  產生網格資料的 Nav 網格
4.  轉譯線框中的網格資料-debug 參數，可顯示產生的網格

這些參數值會當做空間對應網格和手邊網格預設值使用。 您可以隨時在任何網格的藍圖或程式碼中變更它們。

### <a name="c-api-reference"></a>C + + API 參考
用 `EEARObjectClassification` 來尋找所有可追蹤物件中的手網格值。
```cpp
enum class EARObjectClassification : uint8
{
    // Other types
    HandMesh,
};
```

當系統偵測到任何可追蹤物件（包括手形網格）時，會呼叫下列委派。

```cpp
class FARSupportInterface
{
    public:
    // Other params
    DECLARE_AR_SI_DELEGATE_FUNCS(OnTrackableAdded)
    DECLARE_AR_SI_DELEGATE_FUNCS(OnTrackableUpdated)
    DECLARE_AR_SI_DELEGATE_FUNCS(OnTrackableRemoved)
};
```

請確定您的委派處理常式遵循以下的函數簽章：

```cpp
void UARHandMeshComponent::OnTrackableAdded(UARTrackedGeometry* Added)
```

您可以透過下列步驟存取網格資料  `UARTrackedGeometry::GetUnderlyingMesh` ：

```cpp
UMRMeshComponent* UARTrackedGeometry::GetUnderlyingMesh()
```

### <a name="blueprint-api-reference"></a>藍圖 API 參考

若要在藍圖中使用手形網格：
1. 將 **ARTrackableNotify** 元件新增至藍圖執行者

![ARTrackable 通知](images/unreal/ar-trackable-notify.png)

2. 移至 [ **詳細資料** ] 面板，然後展開 [ **事件** ] 區段。

![ARTrackable 通知2](images/unreal/ar-trackable-notify2.png)

3. 在事件圖中使用下列節點覆寫新增/更新/移除追蹤幾何：

![ARTrackable 通知時](images/unreal/on-artrackable-notify.png)

### <a name="hand-mesh-visualization-in-openxr"></a>OpenXR 中的手中視覺效果

將手上網格視覺化的建議方式，是使用長篇的 XRVisualization 外掛程式搭配 [Microsoft OpenXR 外掛程式](https://github.com/microsoft/Microsoft-OpenXR-Unreal)。 

然後，在藍圖編輯器中，您應該使用來自 [Microsoft OpenXR 外掛程式](https://github.com/microsoft/Microsoft-OpenXR-Unreal)的 **Set use 手型** 函式，並搭配 **Enabled XRVisualization** 作為參數：

![事件開始播放的藍圖已連線到 set use 手型函式已啟用 xrvisualization 模式](images/unreal-hand-tracking-img-05.png)

若要管理轉譯程式，您應該使用 XRVisualization 的 **Render 移動控制器** ：

![連接到轉譯移動控制器函式的 get 運動控制器資料函式藍圖](images/unreal-hand-tracking-img-06.png)

結果：

![以真實人為重迭的數位手影像](images/unreal-hand-tracking-img-07.png) 

如果您需要更複雜的資訊，例如繪製具有自訂著色器的手形網格，您需要取得網格作為追蹤幾何。 

## <a name="hand-rays"></a>手部光線 (Hand Ray)

取得手姿勢適用于接近物件或按下按鈕的接近互動。 但是，有時候您需要處理離您的使用者更遠的全像影像。 這可以透過手光線來完成，這可以用來作為 c + + 和藍圖中的指標裝置。 您可以從手中畫出光線到目前為止，並透過 Unreal 光線追蹤的一些協助，來選取不觸及的全像影像。 

> [!IMPORTANT]
> 因為所有的函式結果都會變更每個畫面格，所以全都變成可呼叫。 如需有關純和 impure 或可呼叫函式的詳細資訊，請參閱「函 [式上的](https://docs.unrealengine.com/Engine/Blueprints/UserGuide/Functions/index.html#purevs.impure)藍圖使用者 guid」。

[!INCLUDE[](includes/tabs-tracking-hand-ray.md)]

## <a name="gestures"></a>軌跡

HoloLens 2 會追蹤空間手勢，這表示您可以將這些手勢捕捉為輸入。 軌跡追蹤是以訂用帳戶模型為基礎。 您應該使用「設定手勢」函式來告訴裝置您要追蹤的手勢。 您可以在 [HoloLens 2 基本使用](/hololens/hololens2-basic-usage) 方式檔中找到手勢的詳細資料。

[!INCLUDE[](includes/tabs-tracking-gestures.md)]

## <a name="next-development-checkpoint"></a>下一個開發檢查點

依循我們配置的 Unreal 開發旅程，此時您會探索 MRTK核心建置組塊。 接下來，您可以繼續進行下一個建置組塊：

> [!div class="nextstepaction"]
> [本機空間錨點](unreal-spatial-anchors.md)

或者，直接跳到混合實境平台功能和 API 的主題：

> [!div class="nextstepaction"]
> [HoloLens 相機](unreal-hololens-camera.md)

您可以隨時回到 [Unreal 開發檢查點](unreal-development-overview.md#2-core-building-blocks)。