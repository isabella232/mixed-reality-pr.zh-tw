---
title: Unreal 中的空間對應
description: 在 Unreal 中使用空間對應的指南
author: hferrone
ms.author: jacksonf
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 混合實境, 開發, 功能, 文件, 指南, 全像投影, 空間對應, 混合實境頭戴式裝置, windows 混合實境頭戴式裝置, 虛擬實境頭戴式裝置
ms.openlocfilehash: bde5a1b53f6ad90bc84f54bd3e4f1237b78f2abe
ms.sourcegitcommit: 32cb81eee976e73cd661c2b347691c37865a60bc
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/04/2020
ms.locfileid: "96609419"
---
# <a name="spatial-mapping-in-unreal"></a>Unreal 中的空間對應

空間對應可讓您將物件放在真實世界的實體表面上。 對應了 HoloLens 周圍的環境後，對使用者而言，全像投影看起來會更真實。 空間對應也會利用深度提示將物件錨定在使用者所處的環境中，這樣更能說服使用者這些全像投影真的在其空間中。 浮動於空間中或隨著使用者移動的全像投影會缺乏真實感，因此您應盡可能放置物品，以營造舒適感。

若要深入了解空間對應品質、放置、遮蔽、轉譯等等，請參閱[空間對應](../../design/spatial-mapping.md)文件。

## <a name="enabling-spatial-mapping"></a>啟用空間對應

若要在 HoloLens 上啟用空間對應：
- 開啟 [編輯] > [專案設定]，然後向下捲動至 [平台] 區段。    
    + 選取 **HoloLens** 並勾選 [空間感知]。

![螢幕擷取畫面：已醒目提示空間感知的 HoloLens 專案設定功能](images/unreal-spatial-mapping-img-01.png)

若要在 HoloLens 遊戲中加入空間對應，並偵錯 **MRMesh**：
1. 開啟 **ARSessionConfig**，並展開 [ARSettings] > [世界對應] 區段。 

2. 勾選 [從追蹤的幾何圖形產生網格資料]，這會指示 HoloLens 外掛程式啟動，以非同步方式取得空間對應資料，並透過 **MRMesh** 將其呈現給 Unreal。 
3. 勾選 [以線框呈現網格資料]，以在 **MRMesh** 中顯示每個三角形的白色線框。 

![空間錨點存放區就緒](images/unreal-spatialmapping-arsettings.PNG)


## <a name="spatial-mapping-at-runtime"></a>執行階段的空間對應
您可以修改下列參數，以更新空間對應執行階段行為：

- 開啟 [編輯] > [專案設定]、向下捲動至 [平台] 區段，然後選取 [HoloLens] > [空間對應]： 

![空間錨點專案設定](images/unreal-spatialmapping-projectsettings.PNG)

- **每立方米的三角形數量上限計量** 會更新空間對應網格中三角形的密度。  
- **空間網格體積大小** 是玩家周圍用來呈現和更新空間對應資料的立方體大小。  
    + 如果預期的應用程式執行階段環境預期會很大，此值可能需要很大，才能符合真實世界的空間。 如果應用程式只需要在使用者附近的表面上放置全像投影，則此值可能會比較小。 當使用者在世界中行走時，空間對應體積會隨著他們移動。 

## <a name="working-with-mrmesh"></a>使用 MongoDB

首先，您必須啟動空間對應：

![已醒目提示空間對應擷取類型的 ToggleARCapture 函式藍圖](images/unreal-spatial-mapping-img-02.png)

在為空間擷取了空間對應後，建議您關閉空間對應。  空間對應可能會在一段時間後完成，也可能會在每個方向的光線投射針對 MRMesh 傳回碰撞時完成。

若要可在執行階段存取 **MRMesh**：
1. 將 **ARTrackableNotify** 元件新增至藍圖動作項目。 

![空間錨點的 AR Trackable Notify](images/unreal-spatialmapping-artrackablenotify.PNG)

2. 選取 **ARTrackableNotify** 元件，然後展開 [詳細資料] 面板中的 [事件] 區段。 
    - 對您要監視的事件選取 **+** 按鈕。 

![空間錨點事件](images/unreal-spatialmapping-events.PNG)

在此情況下，會監視 **On Add Tracked Geometry** 事件，這會尋找與空間對應資料相符的有效世界網格。 您可以在 [UARTrackableNotify](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackableNotifyComponent/index.html) 元件 API 中找到完整的事件清單。 

您可以在藍圖事件圖形或 C++ 中變更網格的材質。 下方螢幕擷取畫面會顯示藍圖路由： 

![空間錨點範例](images/unreal-spatialmapping-example.PNG)

## <a name="spatial-mapping-in-c"></a>C++ 中的空間對應

在遊戲的 build.cs 檔案中，將 **AugmentedReality** 和 **MRMesh** 新增至 PublicDependencyModuleNames 清單：

```cpp
PublicDependencyModuleNames.AddRange(
    new string[] {
        "Core",
        "CoreUObject",
        "Engine",
        "InputCore",    
        "EyeTracker",
        "AugmentedReality",
        "MRMesh"
});
```

若要存取 MRMesh，請訂閱 **OnTrackableAdded** 委派：

```cpp
#include "ARBlueprintLibrary.h"
#include "MRMeshComponent.h"

void AARTrackableMonitor::BeginPlay()
{
    Super::BeginPlay();

    // Subscribe to Tracked Geometry delegates
    UARBlueprintLibrary::AddOnTrackableAddedDelegate_Handle(
        FOnTrackableAddedDelegate::CreateUObject(this, &AARTrackableMonitor::OnTrackableAdded)
    );
}

void AARTrackableMonitor::OnTrackableAdded(UARTrackedGeometry* Added)
{
    // When tracked geometry is received, check that it's from spatial mapping
    if(Added->GetObjectClassification() == EARObjectClassification::World)
    {
        UMRMeshComponent* MRMesh = Added->GetUnderlyingMesh();
    }
}
```

> [!NOTE]
> 已更新和已移除的事件有類似的委派，分別是 **AddOnTrackableUpdatedDelegate_Handle** 和 **AddOnTrackableRemovedDelegate_Handle**。
>
> 您可以在 [UARTrackedGeometry](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackedGeometry/index.html) API 中找到完整的事件清單。

## <a name="see-also"></a>另請參閱
* [空間對應](../../design/spatial-mapping.md)
