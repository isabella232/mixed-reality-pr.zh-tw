---
title: SceneUnderstanding
description: 描述 MRTK 中的場景理解
author: MaxWang-MS
ms.author: wangmax
ms.date: 03/02/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、場景理解
ms.openlocfilehash: 991c8152baa138d241b0454d08de267eeaefcb05
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104696155"
---
# <a name="scene-understanding"></a>場景理解

[場景理解](https://docs.microsoft.com/windows/mixed-reality/scene-understanding) 會傳回場景實體的語義標記法，以及其在 __HoloLens 2__ 的幾何形式 (HoloLens 第1代不支援) 。

這項技術的一些預期使用案例如下：
* 將物件放在特定種類的最接近表面 (例如牆壁和樓層) 
* 為平臺樣式遊戲建立導覽網格
* 提供物理引擎易記幾何作為四邊形
* 避免需要撰寫類似的演算法來加速開發

從 MRTK 2.6 開始，場景理解會以 __實驗__ 性功能的形式提供。 它會整合到 MRTK 中，作為名為的 [空間觀察](spatial-awareness-getting-started.md#register-observers) 者 [`WindowsSceneUnderstandingObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsSceneUnderstanding.Experimental.WindowsSceneUnderstandingObserver) 。 場景理解適用于舊版 XR 管線和 XR SDK 管線。 在這兩種情況下， `WindowsSceneUnderstandingObserver` 都會使用。

## <a name="observer-overview"></a>觀察者總覽

當系統詢問時， [`WindowsSceneUnderstandingObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsSceneUnderstanding.Experimental.WindowsSceneUnderstandingObserver) 會傳回 [SpatialAwarenessSceneObject](xref:Microsoft.MixedReality.Toolkit.Experimental.SpatialAwareness.SpatialAwarenessSceneObject) ，其中包含可讓應用程式瞭解其周圍的屬性。 觀察頻率、傳回的物件類型 (例如牆壁、floor) 和其他觀察器行為，都取決於透過設定檔的觀察者設定。 例如，如果需要遮蔽遮罩，則必須設定觀察者來產生四邊形。 觀察到的場景可以儲存為序列化檔案，稍後可以載入以在編輯器播放模式中重新建立場景。

## <a name="setup"></a>設定

> [!IMPORTANT]
> 只有 HoloLens 2 和 Unity 2019.4 和更新版本才支援場景理解。

1. 確定平臺已在組建設定中設定為 UWP。
1. 透過 [混合現實功能工具](https://aka.ms/MRFeatureTool)取得場景理解套件。

## <a name="using-scene-understanding"></a>使用場景理解

開始進行場景理解最快的方式是查看範例場景。

### <a name="scene-understanding-sample-scene"></a>場景理解範例場景

在 Unity 中，使用 Project Explorer 開啟場景檔案 `Examples/Experimental/SceneUnderstanding/Scenes/SceneUnderstandingExample.unity` ，然後按下 [播放]！

> [!IMPORTANT]
> 使用 Mixed Reality 功能工具或透過 UPM 匯入時，請先匯入示範-SpatialAwareness 範例，再匯入實驗性 SceneUnderstanding 範例，因為相依性問題。 如需詳細資訊，請參閱 [此 GitHub 問題](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9431) 。

場景會示範下列各項：

* 在應用程式 UI 中使用觀察到的場景物件來設定觀察者的視覺效果
* 示範 `DemoSceneUnderstandingController` 如何變更觀察者設定以及接聽相關事件的範例腳本
* 將場景資料儲存至裝置以進行離線開發
* 將先前儲存的場景資料載入 ( 的位元組檔案) 以支援編輯器開發工作流程

> [!NOTE] 
> 範例場景是以舊版 XR 管線為基礎。 如果您使用 XR SDK 管線，則應該據以修改設定檔。 提供的場景瞭解空間感知系統設定檔 (`DemoSceneUnderstandingSystemProfile`) 和場景瞭解觀察者設定檔 (`DefaultSceneUnderstandingObserverProfile` 和 `DemoSceneUnderstandingObserverProfile`) 適用于這兩個管線。

#### <a name="configuring-the-observer-service"></a>設定觀察者服務

選取 [MixedRealityToolkit] 遊戲物件並檢查偵測器。

![場景瞭解階層中的位置](../images/spatial-awareness/MRTKHierarchy.png)

![偵測器中的 MRTK 位置](../images/spatial-awareness/MRTKLocation.png)

這些選項可讓其中一個設定 `WindowsSceneUnderstandingObserver` 。

### <a name="example-script"></a>範例指令碼

範例腳本 _DemoSceneUnderstandingController_ 會示範使用場景理解服務的主要概念。

* 訂閱場景理解事件
* 處理場景理解事件
* `WindowsSceneUnderstandingObserver`在執行時間設定

場景中面板上的切換會藉由呼叫此範例腳本的公用函式，來變更場景理解觀察者的行為。

開啟具現 *化 Prefabs*，將會示範如何建立大小適當的物件，使其符合所有 [SpatialAwarenessSceneObject](xref:Microsoft.MixedReality.Toolkit.Experimental.SpatialAwareness.SpatialAwarenessSceneObject)的大小，並整齊地在父物件底下收集。

![示範控制器選項](../images/spatial-awareness/Controller.png)

### <a name="built-app-notes"></a>建立的應用程式附注

以標準方式建立並部署至 HoloLens。 執行之後，您應該會有一些按鈕可以與功能一起播放。

請注意，有一些 pit 正在對觀察者進行查詢。 提取要求的設定不正確會導致您的事件裝載中未包含預期的資料。 例如，如果其中一個不要求四邊形，則不會出現任何遮蔽 mask 紋理。 如同明智的，如果觀察者未設定為要求網格，則不會出現任何世界網格。 `DemoSceneUnderstandingController`腳本會處理其中一些相依性，但並非全部。

您可以透過 [裝置入口網站](https://docs.microsoft.com/windows/mixed-reality/using-the-windows-device-portal) 存取已儲存的場景檔案 `User Folders/LocalAppData/[APP_NAME]/LocalState/PREFIX_yyyyMMdd_hhmmss.bytes` 。 這些場景檔案可以在編輯器中使用，方法是在偵測器中找到的觀察者設定檔中指定它們。

![位元組檔案裝置入口網站位置](../images/spatial-awareness/BytesInDevicePortal.png)

![觀察者中的序列化場景位元組](../images/spatial-awareness/BytesLocationInObserver.png)

## <a name="see-also"></a>另請參閱

* https://docs.microsoft.com/windows/mixed-reality/scene-understanding
* https://docs.microsoft.com/windows/mixed-reality/scene-understanding-sdk
