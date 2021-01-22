---
title: 建立 HoloLens 專案
description: 瞭解如何使用場景物件正確設定 Unreal 專案，並針對 HoloLens 混合現實開發進行輸入互動。
author: hferrone
ms.author: safarooq
ms.date: 01/19/2021
ms.topic: article
ms.localizationpriority: high
keywords: Unreal、Unreal Engine 4、Unreal editor、UE4、HoloLens、HoloLens 2、mixed reality、開發、檔、指南、功能、混合現實耳機、windows mixed reality 耳機、虛擬實境耳機、移植、升級
ms.openlocfilehash: 3b2b88ac897a8791fec1ca2942d0db34efcee598
ms.sourcegitcommit: be33fcda10d1cb98df90b428a923289933d42c77
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/22/2021
ms.locfileid: "98672735"
---
# <a name="creating-a-hololens-project"></a>建立 HoloLens 專案

您需要的第一個項目是供您使用的專案。 如果您是首次接觸的 Unreal 開發人員，則需要從 Epic Launcher [下載支援檔案](tutorials/unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal)。

1. 啟動 Unreal Engine
2. 在 **新的專案類別** 中，選取 [ **遊戲** ]，然後按一下 **[下一步]**：

![已反白顯示遊戲的 [最近使用的專案] 視窗開啟](images/unreal-quickstart-img-01.png)

3. 選取 **空白** 範本，然後按 **[下一步]**：

![醒目提示空白範本的 Unreal 專案瀏覽器視窗](images/unreal-quickstart-img-02.png)

4. 在 **專案設定** 中，設定 **c + +、可擴充的3d 或2d、行動/平板** 電腦和 **無入門內容**，然後選擇 [儲存位置]，再按一下 [**建立專案**]。

> [!NOTE] 您使用的是 c + +，而不是藍圖專案，以便稍後準備使用 OpenXR 外掛程式。 本快速入門會使用 Unreal 引擎隨附的預設 OpenXR 外掛程式。 不過，建議您下載並使用官方 Microsoft OpenXR 外掛程式。 這需要專案是 c + + 專案。

![醒目提示專案、效能、目標平臺和入門內容選項的 [專案設定] 視窗](images/unreal-quickstart-img-03.png)

您的新專案應該會自動在 [Unreal 編輯器] 中開啟，這表示您已經準備好進行下一節。

## <a name="enabling-required-plugins"></a>啟用必要的外掛程式

在您開始將物件新增至場景之前，必須啟用兩個外掛程式。

1. 開啟 [編輯] > [外掛程式]，然後從內建選項清單中選取 [擴增實境]。
* 向下滾動至 **HoloLens** 並勾選 [**啟用**]

![開啟並醒目提示 [增強的事實] 區段的 [外掛程式] 視窗](images/unreal-quickstart-img-04.png)

2. 在右上方的搜尋方塊中輸入 **OpenXR** ，並啟用 **OpenXR** 和 **OpenXRMsftHandInteraction** 外掛程式：

![已啟用 OpenXR 的外掛程式視窗](images/unreal-quickstart-img-05.jpg)

![啟用 Open XR Msft 手型互動的外掛程式視窗](images/unreal-quickstart-img-06.jpg)

3. 重新開機編輯器

> [!NOTE]
> 本教學課程使用 OpenXR，但您先前安裝的兩個外掛程式目前未提供適用于 HoloLens 開發的完整功能集。 HandInteraction 外掛程式可滿足您稍後將會用到的「縮小」手勢，但如果您想要超越基本概念，您必須 [下載 OpenXR 外掛程式](https://github.com/microsoft/Microsoft-OpenXR-Unreal)。

啟用外掛程式之後，您可以將焦點放在以內容填入。

## <a name="creating-a-level"></a>建立層級

您的下一個工作是建立玩家設定，其中包含一個起點和一個用於參考和調整的立方體。

1. 選取 [檔案] > [新增層級]，然後選擇 [空白層級]。 區中的預設場景現在應該是空的
2. 從 [ **模式** ] 索引標籤中選取 [ **基本** ]，然後將 **PlayerStart** 拖曳到場景中
* 在 [ **詳細資料** ] 索引標籤中，將 [ **位置** ] 設定為 **X = 0、Y = 0** 和 **Z = 0** ，以在應用程式啟動時將使用者置於場景的中心

![已開始新增位置和播放機的 Unreal 編輯器場景](images/unreal-quickstart-img-07.png)

3. 從 [ **基本** ] 索引標籤中，將 **Cube** 拖曳至場景
* 將 cube 的 **位置** 設定為 **X = 50、Y = 0** 和 **Z = 0** ，以在啟動時將 cube 50 cm 移離播放程式
* 將 cube 的 **刻度** 變更為 **X = 0.2、Y = 0.2** 和 **Z = 0.2** 

您將無法看到立方體，除非您將光線新增至場景，這是測試場景前的最後一項工作。

4. 在 [ **模式** ] 面板中，切換至 [ **燈** ] 索引標籤，並將 **方向光線** 拖曳至場景
* 將燈光放在 **PlayerStart** 上方，讓您可以看到它

![已新增 cube 和方向光源的 Unreal 編輯器場景](images/unreal-quickstart-img-08.png)

5. 移至 [檔案] **> 另存新** 檔，將您的等級命名為 **主要**，然後選取 [ **儲存**

設定場景後，請按下工具列中的 [播放]，以查看行動中的立方體！ 當您完成工作的管理時，請按 Esc 以停止應用程式。

![螢幕中間的立方體在播放模式中的場景](images/unreal-quickstart-img-09.png)

現在已設定場景，讓它準備好用於 AR 的一些基本互動。 首先，您必須建立 AR 會話，並且可以新增藍圖來啟用手互動。

## <a name="adding-a-session-asset"></a>新增會話資產

Unreal 中的 AR 工作階段本身不會發生。 若要使用工作階段，您需要借助於 ARSessionConfig 資料資產，這就是您接下來的工作：

1. 在 **內容瀏覽器** 中，選取 [ **加入新的 > 其他 > 資料資產** ]，並確定您是位於根內容資料夾層級
2. 選取 [ **ARSessionConfig**]，按一下 [ **選取**]，然後將資產命名為 **ARSessionConfig**：

![已反白顯示 AR 會話設定資產的挑選資料資產類別視窗開啟](images/unreal-quickstart-img-10.png)

2. 按兩下 [ **ARSessionConfig** ] 將它開啟，並以所有預設設定 **儲存** 並返回主視窗：

![AR 會話設定資產詳細資料視窗](images/unreal-quickstart-img-11.png)

完成後，您的下一個步驟是確保 AR 工作階段會在層級載入時啟動，並在層級結束時停止。 值得慶幸的是，Unreal 具有名為 **層級藍圖** 的特殊藍圖，可作為整個層級的全域事件圖形。 在層級藍圖中連線 ARSessionConfig 資產，保證 AR 工作階段會在遊戲開始玩時立即啟動。

3. 從編輯器工具列中，選取 [ **藍圖] > 開啟層級藍圖**：

![已反白顯示開啟層級藍圖選項的藍圖功能表開啟](images/unreal-quickstart-img-12.png)

4. 將 [執行] 節點 (向左箭號圖示) 關閉 [ **事件 BeginPlay** ] 和 [發行]
* 搜尋 **開始 AR 會話節點** ，然後按 enter 鍵
* 按一下 [**會話** 設定] 下的 [**選取資產**] 下拉式清單，然後選擇 **ARSessionConfig** 資產

![具有連線到 start ar 會話函式之事件開始播放的藍圖圖形](images/unreal-quickstart-img-13.png)

5. 以滑鼠右鍵按一下 EventGraph 中的任一處，並建立新的 [事件 EndPlay] 節點。 
* 拖曳執行 pin 和版本，然後搜尋 **停止 AR 會話** 節點，然後按 enter 鍵 
* 點擊 **編譯**，然後 **儲存** 並返回主視窗

> [!IMPORTANT]
> 如果 AR 工作階段在層級結束時仍在執行，若您在串流至頭戴式裝置時重新啟動應用程式，某些功能可能會停止運作。

![連接到停止 ar 會話函式的事件結束播放節點](images/unreal-quickstart-img-14.png)

## <a name="setting-up-inputs"></a>設定輸入

1. 選取 [ **編輯] > 專案設定** ，並移至 **引擎 > 輸入**
2. 選取 [ **+** **動作** 對應] 旁的圖示，然後建立 **RightPinch** 和 **LeftPinch** 動作：

![醒目提示右邊和左方縮小動作對應的系結輸入設定](images/unreal-quickstart-img-15.jpg)

3. 將 **RightPinch** 和 **LeftPinch** 動作對應至個別的 **OpenXR Msft 手互動** 動作：

![醒目提示 Open XR Msft 手型互動選項的動作對應](images/unreal-quickstart-img-16.jpg)

4. 開啟 **層級藍圖** ，並新增 **InputAction RightPinch** 和 **InputAction LeftPinch**
* 將適當的縮小事件連接到 **AddActorLocalRotation** ，並 **將目標** 和 **差異旋轉** 設定為 **X = 0、Y = 0** 和 **Z = 20**。 Cube 現在會在您每次縮小時以20度旋轉
* 連接左方的縮小事件以結束 **遊戲**

![層級 bluprint 開啟，其中包含右和左縮小事件的輸入動作](images/unreal-quickstart-img-17.jpg)

5. 在 cube 的 **轉換** 設定中，將 **行動性** 設定為 **可移動** ，使其可以動態移動：

![已反白顯示行動性屬性的轉換設定](images/unreal-quickstart-img-18.jpg)

至此，您已準備好部署及測試應用程式！