---
title: 語音輸入
description: 在 HoloLens 2 和 Unreal 引擎中設定及使用語音輸入的教學課程
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
keywords: Windows Mixed Reality、Unreal、Unreal Engine 4、UE4、HoloLens 2、語音、語音輸入、語音辨識、混合現實、開發、功能、檔、指南、全息全像遊戲開發
ms.openlocfilehash: 88ab39de5f219691a6c3fe5b4ad3008d9614668e
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2020
ms.locfileid: "91682241"
---
# <a name="voice-input-in-unreal"></a>Unreal 中的語音輸入

## <a name="overview"></a>概觀
Unreal 中的語音輸入可讓您與全息圖互動，而不需要使用手勢，且僅 HoloLens 2 支援。 雖然 HoloLens 2 上的語音輸入是由在所有其他通用 Windows 應用程式中支援語音的相同引擎所提供，但 Unreal 會使用它自己的較有限引擎來處理語音輸入。 這會將 Unreal 中的語音輸入功能限制為預先定義的語音對應，如下節所述。 

## <a name="enabling-speech-recognition"></a>啟用語音辨識

若要在 HoloLens 上啟用語音辨識：
1. 選取 [ **專案設定] > 平臺 > HoloLens > 功能** ，並啟用 **麥克風** 。 
2. 在 [設定] **> 隱私權 > 語音** ] 中啟用語音辨識，然後選取 [ **英文** ]。

> [!NOTE]
> 語音辨識一律會以 [ **設定** ] 應用程式中所設定的 Windows 顯示語言運作。 建議您也啟用 **線上語音辨識** ，以獲得最佳的服務品質。

![Windows 語音辨識設定](images/unreal/speech-recognition-settings.png)

3. 當應用程式第一次開始詢問您是否要啟用麥克風時，就會顯示對話方塊。 選取 [ **是]** 會在應用程式中啟動語音輸入。

語音輸入不需要任何特殊的 Windows Mixed Reality Api;它建置於現有的 Unreal Engine 4 [輸入](https://docs.unrealengine.com/Gameplay/Input/index.html) 對應 API 上。 

## <a name="adding-speech-mappings"></a>新增語音對應
使用語音輸入時，連接語音轉換動作是很重要的步驟。 這些對應會監視使用者可能說出的語音關鍵字應用程式，然後引發連結的動作。 您可以透過下列方式尋找語音對應：
1. 選取 [ **編輯] > 專案設定** 、滾動至 [ **引擎** ] 區段，然後按一下 [ **輸入** ]。

若要為跳躍命令新增語音對應：
1. 按一下 [ **+** **陣列元素** ] 旁的圖示，並填寫下列值：
    * **動作名稱** 的 **jumpWord**
    * **跳躍****語音關鍵字**

> [!NOTE]
> 任何英文字 (s) 或簡短句子 (s) 都可以當做關鍵字使用。 

![UE4 引擎輸入設定](images/unreal/engine-input.png)

語音對應可作為活動圖中的輸入元件，例如動作或軸對應，或作為藍圖節點。 例如，您可以連結跳躍命令，根據說出單字的時間，列印出兩個不同的記錄檔：

1. 按兩下藍圖，以在 **事件圖形** 中開啟。
2. 以 **滑鼠右鍵按一下** 並搜尋語音對應的 **動作名稱** (在此案例中為 **JumpWord** ) ，然後按 **Enter 鍵** 。 這會將 **輸入動作** 節點新增至圖形。
3. 拖放已 **按下** 的釘選以 **列印字串** 節點，如下圖所示。 您可以讓釋 **出的** pin 空白，而不會對語音對應執行任何作業。
 
![語音的簡單動作](images/unreal/voice-input-img-03.png)

4. 播放應用程式，比方說，在主控台 **中，將** 記錄檔列印出記錄！

這就是開始在 Unreal 中新增語音輸入到 HoloLens 應用程式所需的所有設定。 您可以在下列連結找到有關語音和互動的詳細資訊，並務必考慮您為使用者建立的體驗。

## <a name="next-development-checkpoint"></a>下一個開發檢查點

如果您正在遵循我們所配置的 Unreal 開發檢查點旅程，您接下來要探索混合現實平臺功能和 Api： 

> [!div class="nextstepaction"]
> [HoloLens 相機](unreal-hololens-camera.md)

您隨時都可以回到 [Unreal 開發檢查點](unreal-development-overview.md#2-core-building-blocks) 。

## <a name="see-also"></a>另請參閱
* [語音輸入](../../design/voice-input.md)
* [目光和行動](../../design/gaze-and-commit.md)
* [本能互動](../../design/interaction-fundamentals.md)

