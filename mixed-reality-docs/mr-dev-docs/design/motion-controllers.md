---
title: 運動控制器
description: 瞭解如何在您的應用程式中使用混合現實移動控制器來設定、配對和管理員輸入互動。
author: wguyman
ms.author: wguyman
ms.date: 03/21/2018
ms.topic: article
keywords: 6dof 控制器、移動控制器、配對、混合現實耳機、windows mixed reality 耳機、虛擬實境耳機、HoloLens、滾動、抓住、州
ms.openlocfilehash: bced0115eee5e753ef01d129ae10910acdca2b7b91020117f53b2ebf8833a130
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2021
ms.locfileid: "115224878"
---
# <a name="motion-controllers"></a>運動控制器

:::row:::
    :::column:::
        移動控制器是可讓使用者在混合現實中採取行動的 [硬體配件](../discover/hardware-accessories.md) 。 動作控制器優於 [手勢](gaze-and-commit.md#composite-gestures) 的優點是，控制器在空間中具有精確的位置，讓您可以更精細地與數位物件互動。 針對 Windows Mixed Reality 沉浸式耳機，移動控制器是使用者將在其世界中採取行動的主要方式。<br>
        <br>
        *影像： Windows Mixed Reality 移動控制器*
    :::column-end:::
        :::column:::
       ![Windows Mixed Reality 動作控制器](images/winmr-ck-1080x1080-350px.jpg)<br> 
    :::column-end:::
:::row-end:::

<br>

---

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
     <td><a href="/hololens/hololens1-hardware"><strong>HoloLens (第 1 代)</strong></a></td>
     <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
     <td><a href="../discover/immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></td>
</tr>
<tr>
     <td>運動控制器</td>
     <td>❌</td>
     <td>❌</td>
     <td>✔️</td>
</tr>
</table>

## <a name="hardware-details"></a>硬體詳細資料

<iframe width="940" height="530" src="https://www.youtube.com/embed/1nlcdDNOdm8" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

Windows Mixed Reality 的動作控制器會使用沉浸式耳機中的感應器，在您的視圖中提供精確且回應性的移動追蹤。 您不需要在空間的牆上安裝硬體。 這些移動控制器會提供與 Windows Mixed Reality 沉浸式耳機一樣容易的設定和可攜性。 我們的裝置合作夥伴計畫在此假日的零售貨架上市場及銷售這些控制器。

![瞭解您的控制器](images/controllerimage-750px.png)<br>
*瞭解您的控制器*

**特徵：**
* 光學追蹤
* 觸發程序
* 抓取按鈕
* 操縱杆
* Touchpad

## <a name="setup"></a>設定

### <a name="before-you-begin"></a>開始之前

**您將需要：**
* 兩個移動控制器的組合。
* 四個 AA 電池。
* 具有藍牙4.0 支援的電腦。

**檢查 Windows、Unity 和驅動程式更新**
* 請造訪安裝適用于混合現實開發之 Windows、Unity 等慣用版本的[工具](../develop/install-the-tools.md)。
* 請確定您有最新的 [耳機和移動控制器驅動程式](/windows/mixed-reality/enthusiast-guide/mixed-reality-software)。

### <a name="pairing-controllers"></a>配對控制器

您可以使用 Windows 設定，像是任何其他藍牙裝置，將移動控制器與主機電腦進行設定。

1. 將兩個 AA 電池插入控制器的背面。 請暫時讓電池蓋住。
2. 如果您使用的是外部 USB 藍牙介面卡，而不是內建的藍牙無線電，請先參閱[藍牙的最佳作法](/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#bluetooth-best-practices)，再繼續進行。 針對具有內建無線電的桌面設定，請確定天線已連線。
3. 開啟 **Windows 設定**  ->  **裝置**  ->  **新增藍牙或其他裝置**  ->  **藍牙**，然後移除任何先前的「運動控制器–右方」和「移動控制器–左方」實例。 另請檢查清單底部的其他裝置類別。
4. 選取 [**新增藍牙或其他裝置**，並查看其開始探索藍牙裝置。
5. 按住控制器的 Windows 按鈕，開啟控制器 buzzes 之後的版本。
6. 按住電池區間中的配對按鈕 (索引標籤) 直到 Led 開始閃爍。

:::row:::
    :::column:::
7. 等候「移動控制器-左方」或「移動控制器-右側」顯示在清單底部。 選取以配對。 控制器會在連線時震動一次。<br>
        <br>
        *影像：選取「移動控制器」以配對;如果有多個實例，請從清單底部選取一個*
    :::column-end:::
        :::column:::
       ![如果有多個實例從清單底部選取一個，請選取要配對的移動控制器](images/450px-bluetooth-add-a-device-300px.png)<br> 
    :::column-end:::
:::row-end:::
   
8. 您會看到控制器出現在 [**滑鼠]、[鍵盤]、[& 畫筆] 類別** 下的 [**已連線**] 藍牙設定中。 至此，您可能會收到一次固件更新–請參閱 [下一節](motion-controllers.md#updating-controller-firmware)。
9. 重新連接電池蓋。
10. 針對第二個控制器重複步驟1-9。

<br>

:::row:::
    :::column:::
        成功配對這兩個控制器之後，您的設定看起來應該如下所示，在 **[滑鼠、鍵盤、& 畫筆] 類別** 下 <br>
        <br>
        *影像：已連線的動作控制器*
    :::column-end:::
        :::column:::
       ![已連線的移動控制器](images/450px-motion-controller-connected-300px.png)<br>
    :::column-end:::
:::row-end:::

如果控制器在配對之後關閉，其狀態會顯示為配對。 對於永久在 [其他裝置] 類別下的控制器，配對可能只有部分完成。 在此情況下，請再次執行配對步驟以取得控制器功能。

### <a name="updating-controller-firmware"></a>正在更新控制器固件

* 如果有一個沉浸式耳機連接到您的電腦，且有新的控制器固件可供使用，則會在您下一次開啟時自動將其推送到您的動作控制器。 控制器固件更新會以一種顯示迴圈中的 LED 象限模式來表示，並花費1-2 分鐘。


:::row:::
    :::column:::
* 在固件更新完成後，控制器將會重新開機並重新連線。 這兩個控制器都應該立即連接。 <br>
        <br>
        *映射：在藍牙設定中連接的控制器*
    :::column-end:::
        :::column:::
       ![連接的控制器](images/cyk-connected-300px.jpg)<br>
    :::column-end:::
:::row-end:::


* 確認您的控制器正常運作：
    1. 啟動 **混合實境入口** ，然後輸入您的混合現實首頁。
    2. 移動控制器並確認追蹤、測試按鈕，並確認 [遙傳](../discover/navigating-the-windows-mixed-reality-home.md#getting-around-your-home) 可運作。 如果沒有，則請查看 [移動控制器的疑難排解](/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#motion-controllers)。

## <a name="gazing-and-pointing"></a>撥雲見日和指標

Windows Mixed Reality 支援兩個重要的互動模型：**注視和認可** 以及認可和 **認可**：
* 使用「 **注視」和「認可**」時，使用者會以其 [注視](gaze-and-commit.md)的物件為目標，然後選取具有手中的物件（遊戲台、clicker 或語音）。
* 使用 **point 和 commit** 時，使用者可以在目標物件上以具有指標能力的移動控制器為目標，然後選取具有控制器觸發程式的物件。

支援指向移動控制器的應用程式也應該盡可能啟用注視導向互動，讓使用者可以選擇他們所使用的輸入裝置。

### <a name="managing-recoil-when-pointing"></a>在指標時管理 recoil

使用移動控制器來指向和認可時，您的使用者將會藉由提取其觸發程式來將其鎖定並進行互動。 提取觸發程式嚴密的使用者最終可能會在其觸發程式提取結束時，讓控制器比預期更高。

若要管理使用者提取觸發程式時可能發生的任何這類 recoil，當觸發程式的類比軸值高於0.0 時，您的應用程式可以貼齊其目標光線。 然後，只要在短時間內發生最後一個按鍵，就可以在觸發程式值到達1.0 之後，使用該目標光線來執行動作。 使用較高層級的[複合點手勢](gaze-and-commit.md#composite-gestures)時，Windows 將會為您管理此目標光線捕獲和超時時間。

## <a name="grip-pose-vs-pointing-pose"></a>底姿勢與指標姿勢

Windows Mixed Reality 支援不同外型規格中的運動控制器，每個控制器的設計都不同于使用者的手邊位置與自然「轉寄」方向之間的關聯性，而應用程式會在轉譯控制器時用於指標。

為了更妥善地表示這些控制器，您可以針對每個互動來源進行兩種調查：底框 **姿勢** 和 **指標姿勢**。

### <a name="grip-pose"></a>握住姿勢

底框 **姿勢** 代表 HoloLens 所偵測到的掌上邊的位置，或是持有移動控制器的棕櫚。

在沉浸式耳機上，把手姿勢最適合用來 **呈現使用者手或****使用者手中所持有的物件**，例如寶劍或機槍。 視覺化動畫控制器時也會使用底框姿勢，因為移動控制器 Windows 所提供的 **呈現模型** 會使用底框姿勢作為其原點和旋轉中心。

此底框姿勢的定義方式明確如下：
* 把手 **位置**：自然地按住控制器時的棕櫚距心，向左或向右調整以將位置置中置中。 在 Windows Mixed Reality 動作控制器上，此位置通常會與 [抓住] 按鈕對齊。
* 底 **圖方向的右軸**：當您完全開啟手來形成平面的五指姿勢時，您的掌上光 (的光線會從左至右向前復原，從右邊的棕櫚) 
* 底圖 **方向的向前軸**：當您關閉手部分 (時，如同按住控制器) 一樣，也就是由非拇指手指所形成的電子管「轉寄」的光線。
* 底圖 **方向的向上軸**：右邊和向前定義所隱含的向上軸。

### <a name="pointer-pose"></a>指標姿勢

**指標姿勢** 代表指向轉寄的控制器秘訣。

系統提供的指標姿勢最適合用來在您 **呈現控制器模型本身** 時 raycast。 如果您要轉譯某個其他的虛擬物件來取代控制器，例如虛擬的機槍，您應該指向該虛擬物件最自然的光線，例如沿著應用程式定義的機槍模型的圓柱移動光線。 因為使用者可以看到虛擬物件，而不是實體控制器，所以指向虛擬物件可能會比使用您的應用程式更自然。

## <a name="controller-tracking-state"></a>控制器追蹤狀態

如同耳機，Windows Mixed Reality 移動控制器不需要設定外部追蹤感應器。 相反地，控制器是由耳機本身的感應器追蹤。

如果使用者將控制器移出耳機的視圖，在大部分情況下，Windows 將會繼續推斷控制器位置，並將其提供給應用程式。 如果控制器的長時間遺失視覺追蹤，控制器的位置將會降到大約精確度的位置。

此時，系統會將控制器主體鎖定給使用者，在移動時追蹤使用者的位置，同時仍會使用其內部方向感應器來公開控制器的真實方向。 許多使用控制器來指向和啟動 UI 元素的應用程式，可以正常運作，而不會察覺到使用者注意。

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/rkDpRllbLII" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


### <a name="reasoning-about-tracking-state-explicitly"></a>明確追蹤狀態的原因

希望根據追蹤狀態以不同方式來處理位置的應用程式，可能會進一步檢查控制器狀態的屬性，例如 SourceLossRisk 和 PositionAccuracy：

<table>
<tr>
<th> 追蹤狀態 </th><th> SourceLossRisk </th><th> PositionAccuracy </th><th> TryGetPosition</th>
</tr><tr>
<td> <b>高精確度</b> </td><td style="background-color: green; color: white"> &lt; 1.0 </td><td style="background-color: green; color: white"> 高 </td><td style="background-color: green; color: white"> true</td>
</tr><tr>
<td> <b>高精確度 (有遺失) 的風險 </b> </td><td style="background-color: orange"> = = 1。0 </td><td style="background-color: green; color: white"> 高 </td><td style="background-color: green; color: white"> true</td>
</tr><tr>
<td> <b>近似精確度</b> </td><td style="background-color: orange"> = = 1。0 </td><td style="background-color: orange"> 大約 </td><td style="background-color: green; color: white"> true</td>
</tr><tr>
<td> <b>沒有位置</b> </td><td style="background-color: orange"> = = 1。0 </td><td style="background-color: orange"> 大約 </td><td style="background-color: orange"> false</td>
</tr>
</table>

這些移動控制器追蹤狀態的定義如下：
* **高精確度：** 當移動控制器位於耳機的視圖範圍內時，它通常會根據視覺效果追蹤，提供高精確度的位置。 移動控制器會短暫離開視圖的欄位，或是短暫地遮蔽到耳機感應器 (例如，根據使用者的情況，) 會根據控制器本身的慣性追蹤，繼續傳回高精確度的姿勢。
* **高精確度 (有遺失) 的風險：** 當使用者將移動控制站移出耳機視圖的邊緣之後，耳機很快就無法以視覺化方式追蹤控制器的位置。 應用程式知道當控制器達到此 FOV 界限時，會看到 **SourceLossRisk** 達到1.0。 屆時，應用程式可能會選擇暫停控制器手勢，而這些手勢需要穩定的高品質串流。
* **近似精確度：** 如果控制器的長時間遺失視覺追蹤，控制器的位置將會降到大約精確度的位置。 此時，系統會將控制器主體鎖定給使用者，在移動時追蹤使用者的位置，同時仍會使用其內部方向感應器來公開控制器的真實方向。 許多使用控制器來指向和啟動 UI 元素的應用程式，都可以正常運作，而不會察覺到使用者的精確度。 具有較長輸入需求的應用程式可能會藉由檢查 **PositionAccuracy** 屬性，選擇將此下降從 **高** 精確度到 **近似** 精確度，例如，讓使用者在這段時間內更有更多的螢幕目標 hitbox。
* **沒有位置：** 雖然控制器可在很長的時間內正常運作，但有時系統會知道即使主體鎖定的位置目前沒有意義。 例如，已開啟的控制器可能從未以視覺化的方式觀察到，或使用者可能會放置由其他人挑選的控制器。 在這些情況下，系統不會提供任何位置給應用程式，而 **TryGetPosition** 會傳回 false。

## <a name="interactions-low-level-spatial-input"></a>互動：低層級空間輸入

跨手和移動控制器的核心互動是 **選取**、 **功能表**、 **抓住**、 **觸控板**、 **操縱杆** 和 **首頁**。
* **Select** 是啟動全像下一次發行的全像是的主要互動。 針對移動控制器，您可以使用控制器的觸發程式來執行選取的按鍵。 其他執行選取的方法是說 [語音命令](voice-input.md) 「選取」。 您可以在任何應用程式中使用相同的選取互動。 將 Select 視為等同于滑鼠點擊的專案;您只需要學習一次，然後再套用到所有應用程式的通用動作。
* **功能表** 是在物件上作用的次要互動，用來提取內容功能表或採取其他次要動作。 使用移動控制器，您可以使用控制器的 *功能表* 按鈕來執行功能表動作。  (也就是，其上有漢堡「功能表」圖示的按鈕) 
* 深入瞭解使用者如何直接在物件上採取動作來操作它們。 使用移動控制器，您可以藉由緊密地擠壓第一個來執行理解動作。 移動控制器可能會偵測到有抓取按鈕、棕櫚觸發程式或其他感應器的理解。
* **觸控板** 可讓使用者在移動控制器的觸控板介面上調整兩個維度中的動作，並按一下觸控板上的 [關閉] 來認可動作。 Touchpads 會提供已按下的狀態、觸及狀態和正規化的 XY 座標。 X 和 Y 的範圍介於-1 到1之間，橫跨圓形觸控板的範圍，中間是 (0，0) 。 若為 X，-1 位於左邊，1位在右邊。 若為 Y，-1 是在底部，1位在頂端。
* **操縱杆** 可讓使用者在其迴圈範圍內移動移動控制器的操縱杆來調整兩個維度中的動作，然後按一下操縱杆上的 [向下] 來認可動作。 Thumbsticks 也會提供已按下的狀態和正規化的 XY 座標。 X 和 Y 的範圍介於-1 到1之間，橫跨圓形觸控板的範圍，中間是 (0，0) 。 若為 X，-1 位於左邊，1位在右邊。 若為 Y，-1 是在底部，1位在頂端。
* **Home** 是一個特殊的系統動作，可用來返回 [開始] 功能表。 它類似于按下鍵盤上的 Windows 鍵或 xbox 控制器上的 xbox 按鈕。 您可以按下移動控制器上的 [Windows] 按鈕。 請注意，您隨時都可以說「嗨 Cortana，回家」。 應用程式無法特別回應家用動作，因為這些動作是由系統處理。

## <a name="composite-gestures-high-level-spatial-input"></a>複合手勢：高層級空間輸入

您可以在一段時間內追蹤 [手手勢](gaze-and-commit.md#composite-gestures) 和移動控制器，以偵測一組常見的高階 **[複合手勢](gaze-and-commit.md#composite-gestures)**。 這可讓您的應用程式偵測到高階的 **點擊**、 **保存**、 **操作** 和 **導覽** 手勢，無論使用者是否最終使用手或控制器。

## <a name="rendering-the-motion-controller-model"></a>轉譯移動控制器模型

**3d 控制器模型** Windows 可讓應用程式使用在系統中目前作用中的每個移動控制器的呈現模型。 藉由讓您的應用程式在執行時間動態載入和表達這些系統提供的控制器模型，您可以確保應用程式向前相容于未來的任何控制器設計。

我們建議您在控制器的把手 **姿勢** 上轉譯所有呈現模型，因為模型的來源會與實體世界中的這個點對齊。 如果您正在轉譯控制器模型，您可能會想要從 **指標姿勢** raycast 至場景，代表使用者自然預期會指向的光線，並假設該控制器的實體設計。

如需如何在 Unity 中以動態方式載入控制器模型的詳細資訊，請參閱在 [unity 中轉譯移動控制器模型](../develop/unity/gestures-in-unity.md#rendering-the-motion-controller-model-in-unity) 一節。

**2d 控制器線條藝術** 雖然我們建議您將應用程式內控制器的秘訣和命令附加至 app 內控制器模型本身，但某些開發人員可能會想要在一般的「教學課程」或「操作說明」 UI 中使用動態控制器的2D 線條藝術標記法。 針對這些開發人員，我們已在下面的黑色和白色中提供 .png 的移動控制器線條藝術檔案， (以滑鼠右鍵按一下以儲存) 。

![行動電話控制器線狀圖的預覽](images/motioncontrollers-black-preview-300px.png)

[' ' ' 白色 ' ' 中的全解析度動作控制器線狀圖](images/motioncontrollers-white.png)
 
[' ' ' 黑色 ' ' 中的全解析度動作控制器線狀圖](images/motioncontrollers-black.png)

## <a name="faq"></a>常見問題集

### <a name="can-i-pair-motion-controllers-to-multiple-pcs"></a>我可以將移動控制器配對到多部電腦嗎？

移動控制器支援與單一電腦配對。 依照 [移動控制器設定](motion-controllers.md#setup) 的指示，將您的控制器配對。

### <a name="how-do-i-update-motion-controller-firmware"></a>如何? 更新移動控制器的固件？

移動控制器固件是耳機驅動程式的一部分，並會在必要時自動更新。 根據藍牙的無線電和連結品質，通常需要1-2 分鐘的時間來進行固件更新。 在罕見的情況下，控制器固件更新最多可能需要10分鐘的時間，這可能表示藍牙連接或無線電干擾不佳。 請參閱[《愛好者指南》中的藍牙最佳作法](/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#bluetooth-best-practices)，以針對連線能力問題進行疑難排解。 在固件更新之後，控制器將會重新開機，並重新連線至主機電腦 (您可能會注意到，Led 會很亮以追蹤) 。 如果固件更新中斷 (例如，控制器會遺失電源) ，它會在下一次控制器開機時再次嘗試。

### <a name="how-i-can-check-battery-level"></a>我可以如何檢查電池計量？

在[Windows Mixed Reality 首頁](../discover/navigating-the-windows-mixed-reality-home.md)中，您可以將控制器開啟，以在虛擬模型的反面查看其電池計量。 沒有實體電池等級指標。

### <a name="can-you-use-these-controllers-without-a-headset-just-for-the-joysticktriggeretc-input"></a>您可以在沒有耳機的情況下使用這些控制器嗎？ 僅適用于搖桿/觸發程式/etc 輸入？

不適用於通用 Windows 應用程式。

## <a name="troubleshooting"></a>疑難排解

請參閱愛好者指南中的 [動作控制器疑難排解](/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#motion-controllers) 。

## <a name="filing-motion-controller-feedbackbugs"></a>歸檔移動控制器意見反應/錯誤

使用「混合現實-> 輸入」類別，在意見反應中樞中[提供意見反應給我們](/hololens/hololens-feedback)。

## <a name="see-also"></a>另請參閱

* [Unity 中的動作控制器](../develop/unity/motion-controllers-in-unity.md)
* [DirectX 中的手部和運動控制器](../develop/native/hands-and-motion-controllers-in-directx.md)
* [手勢](gaze-and-commit.md#composite-gestures)
* [愛好者指南：您的 Windows Mixed Reality 首頁](/windows/mixed-reality/enthusiast-guide/your-mixed-reality-home)
* [愛好者指南：在 Windows Mixed Reality 中使用遊戲 & 應用程式](/windows/mixed-reality/enthusiast-guide/using-games-and-apps-in-windows-mixed-reality)
* [內外追蹤的運作方式](/windows/mixed-reality/enthusiast-guide/tracking-system)