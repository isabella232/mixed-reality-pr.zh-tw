---
title: 注視並認可
description: 深入瞭解「注視」和「認可」輸入模型，包括兩種類型的注視 (前端和眼睛) ，以及各種類型的認可。
author: sostel
ms.author: sostel
ms.date: 10/31/2019
ms.topic: article
keywords: 混合的現實、注視、注視目標、互動、設計、眼睛追蹤、head 追蹤
ms.openlocfilehash: 887d1a30a974bdd643889959a1fee55e96d7b16a
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2020
ms.locfileid: "91680940"
---
# <a name="gaze-and-commit"></a>注視並認可

「 _注視」和「認可_ 」是一種基本的輸入模型，與使用滑鼠： _點 & 按一下_ 來與電腦互動的方式密切相關。
在這個頁面中，我們會介紹兩種類型的注視輸入 (前端和眼睛) 以及不同類型的認可動作。 
您可以使用間接操作將 _注視和 commit_ 視為最遠的輸入模型。
這表示它最適合用來與不觸及的全像內容互動。

混合現實耳機可以使用使用者的標頭位置和方向來決定其前端方向向量。 您可以將此視為直接從使用者的雙眼之間向前直指的雷射。 這是相當粗略的使用者觀看位置概算。 您的應用程式可以將此光線與虛擬或真實世界物件相交，並在該位置繪製游標，讓使用者知道他們目前的目標。

除了頭部眼，某些混合的現實耳機（例如 HoloLens 2）包含產生眼睛向量的眼睛追蹤系統。 這會對使用者觀看的位置提供精細的測量。 在這兩種情況下，注視都代表使用者意圖的重要信號。 系統可以更妥善地解讀和預測使用者的預期動作、提高使用者滿意度，以及提升效能。

以下幾個範例可讓您以混合現實開發人員的身分來受益于 head 或眼睛：
* 您的應用程式可以與場景中的全像眼睛相同，以判斷使用者的注意力 (更精確的眼睛) 。
* 您的應用程式可以根據使用者的注視來進行頻道手勢和控制器按動作，讓使用者可以順暢地選取、啟用、抓取、滾動或以其他方式與其全息的互動。
* 您的應用程式可以讓使用者將表面光線與空間對應網格相交，以將影像放在真實世界的表面上。
* 您的應用程式可以知道使用者何時 *不* 會查看重要物件的方向，這可能會導致您的應用程式提供視覺效果和音訊提示，以轉向該物件。

<br>


## <a name="device-support"></a>裝置支援

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>輸入模型</strong></td>
        <td><a href="../hololens-hardware-details.md"><strong>HoloLens (第 1 代)</strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="../discover/immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></td>
    </tr>
     <tr>
        <td>頭部注視並認可</td>
        <td>✔️ 建議使用</td>
        <td>✔️ 建議使用 (第三個選擇 - <a href="interaction-fundamentals.md">查看其他選項</a>)</td>
        <td>➕ 替代選項</td>
    </tr>
         <tr>
        <td>眼部注視並認可</td>
        <td>❌ 無法使用</td>
        <td>✔️ 建議使用 (第三個選擇 - <a href="interaction-fundamentals.md">查看其他選項</a>)</td>
        <td>❌ 無法使用</td>
    </tr>
</table>


## <a name="gaze"></a>注視

### <a name="eye--or-head-gaze"></a>眼睛或頭部？
當遇到問題時，您應該考慮幾個考慮：您是否應該使用「眼睛和認可」或「前端和認可」輸入模型。 如果您正在針對沉浸式耳機或 HoloLens (第一代) 進行開發，則選擇很簡單：標上和認可。 如果您正在針對 HoloLens 2 進行開發，則選擇會變得更困難，這也是瞭解每一種方法的優點和挑戰，是很重要的。
在下表中，我們編譯了一些很廣泛的專業人員和 con，以對比眼睛的目標。 這並不是完整的，我們建議您在此處深入瞭解混合現實中的眼睛目標：
* [HoloLens 2 上的眼睛追蹤](eye-tracking.md)：在 HoloLens 2 上推出新的眼睛追蹤功能，包括一些開發人員指引。 
* [眼睛的互動](eye-gaze-interaction.md)：規劃使用眼睛追蹤作為輸入時的設計考慮和建議。

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
   <tr>
        <td><strong>眼睛的目標</strong></td>
        <td><strong>頭部注視定向</strong></td>
    </tr>
    <tr>
        <td>快速！</td>
        <td>慢</td>
    </tr>
    <tr>
        <td>低工作量 (幾乎不需要任何主體移動) </td>
        <td>可以是 fatiguing 可能的不適感 (例如，頸部壓力) </td>
    </tr>
    <tr>
        <td>不需要資料指標，但建議使用微妙的意見反應</td>
        <td>需要顯示資料指標</td>
    </tr>
    <tr>
        <td>無平滑的移動–例如，不適合繪圖</td>
        <td>更受控制且明確</td>
    </tr>
    <tr>
        <td>很難進行非常小的目標 (例如，小按鈕或網頁連結) </td>
        <td>可靠！ 絕佳的回復！</td>
    </tr>
    <tr>
        <td>...</td>
        <td>...</td>
    </tr>
</table>

無論您是針對您的注視和認可輸入模型使用前端或眼睛，都有不同組的設計條件約束，這些條件約束將會在 [眼睛和認可](gaze-and-commit-eyes.md) 以及 [前端和認可](gaze-and-commit-head.md) 文章中各自討論。

<br>

---

### <a name="cursor"></a>資料指標

:::row:::
    :::column:::
        針對 head，大部分的應用程式應該使用 [游標](cursors.md) (或其他聽覺/視覺指示) ，讓使用者在他們即將與其互動的方面具有信賴度。 您通常會將這個資料指標放在世界中，其中的前端光線最先與物件（可能是全息圖或真實世界表面）相交。<br>
        <br>
        針對眼睛，我們通常不建議您 *不要* 顯示資料指標，因為這可能會對使用者造成干擾和討厭。 相反地強調顯示視覺效果目標，或使用非常模糊的眼睛游標，以提供使用者即將與其互動的相關資訊。 如需詳細資訊，請參閱 HoloLens 2 上 [的眼睛輸入的設計指引](eye-tracking.md) 。
    :::column-end:::
        :::column:::
       ![顯示注視的視覺效果游標範例](images/cursor.jpg)<br>
       *影像：顯示注視的視覺效果游標範例*
    :::column-end:::
:::row-end:::

<br>

---

## <a name="commit"></a>Commit
談到不同的 _方式來看_ 看某個目標之後，讓我們再談談一下看看 _和認可_ 的 _認可_ 部分。
以物件或 UI 元素為目標之後，使用者可以使用次要輸入進行互動或按一下。 這就是所謂的輸入模型認可步驟。 

支援的認可方法如下：
- 點擊手勢 (也就是，將您手上的手抬起，並將您的食指與 thumb 合在一起) 
- 說「 _select_ 」或其中一個目標語音命令
- 在[HoloLens Clicker](https://docs.microsoft.com/hololens/hololens1-clicker)上按單一按鈕
- 按下 Xbox 遊戲台上的 [A] 按鈕
- 按下 Xbox 適應性控制器上的 [A] 按鈕

### <a name="gaze-and-air-tap-gesture"></a>注視和點擊手勢
空中點選是手部直立的點選手勢。 若要執行點一下，請將您的索引指向就緒的位置，然後使用您的 thumb 來縮小，然後將您的索引手指重回來以釋放。 在 HoloLens (第1代) 上，按一下是最常見的次要輸入。


:::row:::
    :::column:::
       ![觸達就緒位置](images/readyandpress-ready.jpg)<br>
       **觸達就緒位置**<br>
    :::column-end:::
    :::column:::
       ![按下手指以點擊或按一下](images/readyandpress-press.jpg)<br>
        **按下手指以點擊或按一下**<br>
    :::column-end:::
:::row-end:::


HoloLens 2 也可以使用 [點一下]。 它已從原始版本中放寬。 幾乎所有類型的 pinches 現在都可支援，只要手邊的手是直立的，且仍維持。 這可讓使用者更容易了解和執行手勢。 這個新的空中會透過相同的 API 來取代舊的，讓現有的應用程式在重新編譯以進行 HoloLens 2 之後，會自動有新的行為。

<br>

---

### <a name="gaze-and-select-voice-command"></a>注視和「選取」聲音命令
語音命令是混合現實中的其中一個主要互動方法。 它提供了一套功能強大的無人參與機制來控制系統。 語音互動模型有不同的類型：

- 執行 click actuation 或 commit 作為次要輸入的泛型 "Select" 命令。
- 物件命令 (例如，「關閉」或「變得更大」 ) 執行並認可至動作做為次要輸入。
- 全域命令 (例如「移至開始」 ) 不需要目標。
- 對話使用者介面或 Cortana 之類的實體都具有 AI 自然語言功能。
- 自訂語音命令

若要瞭解更多詳細資料，以及可用語音命令的完整清單，以及如何使用這些命令，請參閱我們的 [語音](../out-of-scope/voice-design.md) 命令指引。

<br>

---


### <a name="gaze-and-hololens-clicker"></a>注視和 HoloLens Clicker

:::row:::
    :::column:::
        HoloLens Clicker 是特別為 HoloLens 建立的第一個週邊設備。 它隨附于 HoloLens (第一代) 開發版。 HoloLens Clicker 可讓使用者按下最少量的動作，並認可為次要輸入。 HoloLens Clicker 會連接到 HoloLens (第1代) 或使用藍牙低能源 (BTLE) HoloLens 2。<br>
        <br>
        [有關將裝置配對的詳細資訊和指示](../discover/hardware-accessories.md#pairing-bluetooth-accessories)<br>
        <br>
        *映射： HoloLens Clicker*
    :::column-end:::
        :::column:::
       ![HoloLens Clicker](images/hololens-clicker-500px.jpg)<br>
    :::column-end:::
:::row-end:::

<br>

---


### <a name="gaze-and-xbox-wireless-controller"></a>注視和 Xbox 無線控制器

:::row:::
    :::column:::
        Xbox 無線控制器會使用 [A] 按鈕，以次要輸入的形式執行 click actuation。 裝置會對應至一組預設的動作，以協助流覽和控制系統。 如果您想要自訂控制器，請使用 Xbox 配件應用程式來設定 Xbox 無線控制器。<br>
        <br>
        [如何將 Xbox 控制器與您的電腦配對](../discover/hardware-accessories.md#pairing-bluetooth-accessories)<br>
        <br>
        *影像： Xbox 無線控制器*
    :::column-end:::
        :::column:::
       ![Xbox 無線控制器](images/xboxcontroller.jpg)<br>
    :::column-end:::
:::row-end:::



<br>

---


### <a name="gaze-and-xbox-adaptive-controller"></a>注視和 Xbox 調適型控制器
Xbox 調適型控制器是專為滿足行動裝置的需求而設計，可協助讓混合現實更容易存取的裝置具有統一的中樞。

Xbox 適應性控制器會使用 [A] 按鈕，以次要輸入的形式執行 click actuation。 裝置會對應至一組預設的動作，以協助流覽和控制系統。 如果您想要自訂控制器，請使用 Xbox 配件應用程式來設定 Xbox 調適型控制器。

![Xbox Adaptive Controller](images/xbox-adaptive-controller-devices.jpg)<br>
*Xbox Adaptive Controller*

連接外部裝置（例如交換器、按鈕、掛接和操作杆）來建立獨特的自訂控制器體驗。 按鈕、操縱杆和觸發程式輸入都是由透過 3.5 mm 插孔和 USB 埠連接的輔助裝置所控制。

![Xbox Adaptive Controller 連接埠](images/xbox-adaptive-controller-ports.jpg)<br>
*Xbox Adaptive Controller 連接埠*

[裝置配對指示](../discover/hardware-accessories.md#pairing-bluetooth-accessories)

<a href=https://www.xbox.com/xbox-one/accessories/controllers/xbox-adaptive-controller>在 Xbox 網站上可取得更多資訊</a>

<br>

---

## <a name="composite-gestures"></a>複合手勢

### <a name="air-tap"></a>空中點選
點擊手勢 (以及下面的其他手勢) 只會回應特定的點。 若要偵測其他點擊（例如功能表或理解），您的應用程式必須直接使用上述兩個主要元件手勢區段中所述的較低層級互動。

### <a name="tap-and-hold"></a>點選並按住
按住只是維持空中點選的手指朝下位置。 使用「點擊和拖曳」的組合，可讓您在結合 arm 移動（例如挑選物件）時，使用各種更複雜的「點擊和拖曳」互動，而不是啟用它，或在顯示操作功能表之類的次要互動。
不過，針對這個手勢進行設計時應格外小心，因為使用者很容易在任何延伸手勢的過程中放鬆其手勢。

### <a name="manipulation"></a>操作
當您想1:1 要讓全像全像移動、調整大小或旋轉全像移動、調整大小或旋轉影像時，可以使用操作手勢來移動、調整大小或旋轉。 這類 1:1 移動的用途之一是要讓使用者可以實際繪圖。
操作手勢的初始定向應經由注視或指向來完成。 當點一下和按住開始之後，就會以手動方式處理物件的任何操作，讓使用者在操作時進行查詢。

### <a name="navigation"></a>巡覽
瀏覽手勢的運作方式如同虛擬搖桿，可用來瀏覽 UI 小工具，例如放射狀功能表。 您可點選並按住來啟動手勢，然後在標準化 3D Cube (在初次按壓時置中) 中移動您的手。 您可以將您的手沿著 X、 Y 或 Z 軸從值 -1 移到 1 (而 0 表示起點)。
瀏覽可用來建置以速度為基礎的連續捲動或縮放手勢，類似於藉由按一下滑鼠中間按鈕，然後上下移動滑鼠來捲動 2D UI。

使用 rails 的導覽指的是在特定軸中辨識移動的能力，直到到達該軸上的特定臨界值為止。 當開發人員在應用程式中啟用多個軸的移動時（例如，如果應用程式設定為辨識跨 X、Y 軸的導覽手勢，但同時指定 X 軸與 rails），這項功能就很有用。 在此情況下，系統會在 X 軸上辨識手間的移動，只要它們留在 X 軸的虛數滑軌 (指南) ，如果在 Y 軸上也會發生手移動。

在 2D 應用程式內，使用者可以使用垂直瀏覽手勢在應用程式內捲動、縮放或拖曳。 這會在應用程式中插入虛擬手指觸控，以模擬同類型的觸控手勢。 使用者可以在應用程式上方的工具列上切換，藉由選取按鈕或說「<滾動/拖曳/縮放> 工具」，來選取要進行的動作。

[複合手勢的詳細資訊](gaze-and-commit.md#composite-gestures)

## <a name="gesture-recognizers"></a>手勢辨識器

使用手勢辨識的其中一個優點是，您只能針對目前目標的全像全像影像所能接受的手勢設定手勢辨識器。 平臺只會視需要去除混淆，以區別這些特定支援的手勢。 如此一來，只支援「敲擊」的全像是在按下和放開之間有任何時間長度，而同時支援點一下和按住的全像投影可以在按住時間閾值之後升階。

## <a name="hand-recognition"></a>手部辨識
HoloLens 可藉由追蹤裝置可見的任一手或雙手位置來辨識手勢。 當手部處於就緒狀態 (手背朝向您且食指朝上) 或按下狀態 (手背朝向您且食指朝下) 時，HoloLens 就會看見手部。 當手中有其他人時，HoloLens 會忽略它們。
針對 HoloLens 偵測到的每個手，您可以存取其位置，而不需要方向和按下的狀態。 當手部接近手勢框架邊緣時，您也會取得方向向量，而您可對使用者顯示該向量，讓他們知道如何移動其手部以回到 HoloLens 可看見手部的位置。

## <a name="gesture-frame"></a>手勢框架
針對 HoloLens 上的手勢，手必須位於手勢框架內、手勢檢測攝影機可適當地查看的範圍、從鼻子到 waist，以及肩膀之間。 使用者必須在此辨識區域上進行訓練，以獲得動作的成功，並讓他們自己的舒適。 許多使用者一開始會假設手勢畫面格必須在其觀看的情況下，並保有 uncomfortably，以便進行互動。 使用 HoloLens Clicker 時，不一定要將手放在手勢框架內。

尤其是連續手勢的情況下，使用者在移動全息型物件時，將其手移至手勢框架之外時，會有一些風險，例如，以及遺失其預期結果。

您應該考量下列三個事項：

- 手勢框架存在和大約界限的使用者教育。 這是在 HoloLens 安裝期間教授。

- 當使用者的手勢接近或中斷應用程式內的手勢框架界限時，通知使用者，表示遺失的手勢會導致不想要的結果。 研究已展示這類通知系統的主要品質。 HoloLens shell 會在中央游標上提供此類型通知（視覺效果）的良好範例，指出界限跨越的方向。

- 您應該將突破手勢框架界限的後果最小化。 一般來說，這表示手勢的結果應該在界限停止，而不是反轉。 比方說，如果使用者要在房間內移動一些全像的物件，則當軌跡框架被入侵時，移動應該會停止，而且不會傳回至起始點。 使用者可能會遇到一些挫折，但可能更快速地瞭解界限，而不必每次重新開機其完整的預期動作。



## <a name="see-also"></a>另請參閱
* [眼動式互動](eye-gaze-interaction.md)
* [HoloLens 2 的眼球追蹤](eye-tracking.md)
* [目光和停駐](gaze-and-dwell.md)
* [手 - 直接操作](direct-manipulation.md)
* [手 - 手勢](gaze-and-commit.md#composite-gestures)
* [手 - 指向和行動](point-and-commit.md)
* [本能互動](interaction-fundamentals.md)
* [語音輸入](voice-input.md)

