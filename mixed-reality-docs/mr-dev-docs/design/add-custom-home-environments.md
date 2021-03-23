---
title: 設計自己的沉浸式環境
description: 瞭解如何建立您自己的 Windows Mixed Reality home 環境。
author: thmignon
ms.author: thmignon
ms.date: 04/30/2018
ms.topic: article
keywords: Windows Mixed Reality、混合的現實、虛擬實境、VR、MR、Home、自訂環境、地點、cliff 房子、skyloft、使用者、建立、混合現實耳機、windows Mixed Reality 耳機、虛擬實境耳機、HoloLens、MRTK、混合現實工具組
ms.openlocfilehash: 2a626b91b79eadb49c9da95c9d61f92a375015a0
ms.sourcegitcommit: f74d33d50c1fbfebe8571695d631ce78dd599f74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/23/2021
ms.locfileid: "104881215"
---
# <a name="design-your-own-immersive-environments"></a>設計自己的沉浸式環境

>[!NOTE]
>這是實驗性的功能。 請試試看，它很有趣，但如果一切沒有如預期般運作，則不會感到驚訝。 我們正在評估這項功能的可行性並對其使用感興趣，因此請告訴我們您的體驗 (以及您在 [開發人員論壇](https://forums.hololens.com/categories/custom-home-environments)) 找到的任何 bug。

從 [2018 年4月更新 Windows 10](/windows/mixed-reality/enthusiast-guide/release-notes-april-2018)開始，我們已啟用實驗性功能，可讓您將自訂環境新增至 [開始] 功能表) 上的 [位置選擇器] (，以做為 [Windows Mixed Reality 首頁](../discover/navigating-the-windows-mixed-reality-home.md)使用。 Windows Mixed Reality 有兩個預設環境：懸崖之屋和 Skyloft，您可以選擇做為您的首頁。 建立自訂環境可讓您使用自己的建立來展開清單。 這項功能是以早期的狀態提供，以評估建立者和開發人員的興趣。 查看您所建立的各種領域，並瞭解如何使用不同的 authoring tools。

使用自訂環境時，您會注意到 teleporting、與應用程式互動，以及放置全像投影一樣的運作方式，與在懸崖之屋和 Skyloft 中一樣。 您可以在幻想環境中流覽 web，或使用全像幻想式道具城市來填滿，這可能是無限的。

## <a name="device-support"></a>裝置支援

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><strong>功能</strong></td>
        <td><a href="/hololens/hololens2-hardware"><strong>HoloLens</strong></a></td>
        <td><a href="../discover/immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></td>
    </tr>
     <tr>
        <td>自訂家用環境</td>
        <td>❌</td>
        <td>✔️</td>
    </tr>
</table>

## <a name="trying-a-sample-environment"></a>嘗試範例環境

我們建立了一個範例環境，顯示自訂家用環境的一些創意潛力。 請遵循下列步驟來試用：
1. [下載我們的範例幻想島環境](https://download.microsoft.com/download/B/2/5/B25C1AEF-40CD-4B03-A596-4BCA3D33035A/Fantasy_Island.exe) (連結點，以) 自動解壓縮的可執行檔。

    ![幻想島範例環境](images/FantasyLand.jpg)<br>
    *幻想島範例環境*<br>

2. 執行您所下載的 **Fantasy_Island.exe** 檔案。

    > [!NOTE]
    > 當您嘗試執行從 web (下載的 .exe 檔案，就像這樣的) ，您可能會遇到「Windows 已保護您的電腦」快顯視窗。 若要從此快顯視窗執行 Fantasy_Island.exe，請選取 [ **更多資訊** ]，然後 **繼續執行**。 此安全性設定的目的是要防止您下載不想要信任的檔案，因此當您信任檔案的來源時，請選擇此選項。

3. 開啟 **檔案總管** 並在網址列中貼上下列檔案位置，以流覽至 [環境] 資料夾： `%LOCALAPPDATA%\Packages\EnvironmentsApp_cw5n1h2txyewy\LocalState` 。
4. 將您下載的範例環境複製到此資料夾。
5. 重新開機 **混合實境入口** ，以重新整理位置選擇器中的環境清單。
6. 放在您的耳機上。 一旦您在家中，請使用 [Windows] 按鈕來開啟 **[開始] 功能表** 。
7. 選取釘選應用程式清單上方的 [ **地點** ] 圖示，以選擇主環境。
8. 您會在您的地點清單中找到您下載的幻想島環境。 選取 [ **幻想島** ] 以進入新的自訂家用環境！

## <a name="creating-your-own-custom-environment"></a>建立您自己的自訂環境

除了使用我們的範例環境，您還可以使用您最愛的3D 編輯軟體來匯出自己的自訂環境。 

### <a name="modeling-guidelines"></a>模型指導方針

為您的環境建立模型時，請記住下列建議，讓使用者在 believably 規模的世界中產生正確的方向：

1. 使用者將會產生0、0、0，以將您的產生位置置中到原點的中心。
2. 工作單位應該設定為計量，以便能夠以全球規模撰寫資產。
3. 向上軸應設定為 "Y"。
4. 資產應「轉寄」朝正 Z 軸。
5. 您不需要將所有的網格合併，但如果您是以資源限制的裝置為目標，則建議使用此選項。

### <a name="exporting-your-environment"></a>匯出您的環境

Windows Mixed Reality 依賴二進位 glTF (. glb) 做為環境的資產傳遞格式。 glTF 是 Khronos 群組所維護之3D 資產傳遞的專利免費開放標準。 Microsoft 對 Windows 應用程式和體驗的格式支援將隨著 glTF 發展成為互通3D 內容的產業標準。

匯出用來作為自訂家用環境之資產的第一個步驟是產生 glTF 2.0 模型。 GlTF 工作群組會維護一份 [支援的匯出工具和轉換器清單，](https://github.com/KhronosGroup/glTF/blob/master/README.md#converters-and-exporters) 以建立 glTF 2.0 模型。 若要開始使用，請使用此頁面上所列的其中一個程式來建立和匯出 glTF 2.0 模型，或使用其中一個支援的轉換器來轉換現有的模型。

<!-- Additionally, check out [this helpful article, which provides an overview of an art workflow for exporting glTF models from Blender and 3DS Max directly.  -->

### <a name="environment-limits"></a>環境限制

所有環境都必須是 < 256 mb。 大於 256 mb 的環境將無法載入，而且只會使用使用者周圍的預設 skybox 來切換回空白世界。 建立模型時，請記住此檔案大小限制。 此外，如果您打算使用 WindowsMRAssetConverter （如下所述）將您的環境優化，請 cognizant 材質大小會隨著優化工具建立檔案大小較大但載入速度更快的材質而增加。 

### <a name="optimizing-your-environment"></a>優化您的環境

Windows Mixed Reality 支援許多可大幅降低環境載入時間的選擇性優化。 請特別注意具有許多材質的環境，因為它們有時候會在載入時出現。 一般來說，我們建議所有資產都使用此步驟，不過，只有少數或低解析度紋理的較小環境並不一定需要它。 

為了簡化此程式，我們建立了 Windows Mixed Reality 的 [資產轉換器 (可在 GitHub) 上 ](https://github.com/Microsoft/glTF-Toolkit/releases) 取得，以進行優化。 這項工具會使用 Microsoft glTF 工具組中提供的一組公用程式，藉由執行額外的材質封裝、壓縮和解析度向下調整，來優化任何標準 2.0 glTF 或 glb。 

轉換器目前支援數個旗標，以調整優化的確切行為。 建議您以下列旗標執行，以獲得最佳結果：

旗標|建議值 (s) |描述
---|---|---
-最大材質-大小|1024或2048| 調整值以改善紋理的品質，預設值為512x512。 較大的值會大幅影響環境的檔案大小，因此請記住 256-mb 的限制
-最小-版本|1803|只有在 windows >= 1803 的版本上才支援自訂環境。 此旗標會移除較舊版本的材質，並減少最終資產的檔案大小

例如：

```cmd
WindowsMRAssetConverter FileToConvert.gltf -max-texture-size 1024 -min-version 1803
```

### <a name="testing-your-environment"></a>測試您的環境

當您擁有最終的 glb 環境之後，即可在耳機中進行測試。 從「 [試用範例環境](#trying-a-sample-environment) 」一節的步驟2開始，使用您的自訂環境做為混合實境首頁。 

## <a name="sending-feedback"></a>傳送意見反應

在評估這項實驗性功能時，我們想要瞭解您使用自訂環境的方式、您可能發現的任何錯誤，以及您喜歡此功能的方式。 分享在 [開發人員論壇](https://forums.hololens.com/categories/custom-home-environments)中建立及使用自訂家用環境的任何意見反應。

## <a name="troubleshooting-and-tips"></a>疑難排解與秘訣

### <a name="how-do-i-change-the-name-of-the-environment"></a>如何? 變更環境的名稱？

[環境] 資料夾中的檔案名將用於位置選擇器中。 若要變更您的環境名稱，請重新命名環境檔案名，然後重新開機混合實境入口。

### <a name="how-do-i-remove-custom-environments-from-my-places-picker"></a>如何? 從我的地點選擇器移除自訂環境？

若要移除自訂環境，請在您的電腦上開啟環境資料夾 (`%LOCALAPPDATA%\Packages\EnvironmentsApp_cw5n1h2txyewy\LocalState`) 並刪除環境。 一旦您重新開機混合實境入口，此環境將不會再出現在位置選擇器中。 

### <a name="how-do-i-default-to-my-favorite-custom-environment"></a>如何? 預設為我最愛的自訂環境？

您目前無法變更預設環境。 每次您重新開機混合實境入口時，您都會回到懸崖之屋環境。 

### <a name="i-spawn-into-a-blank-space"></a>我產生了一個空格

Windows Mixed Reality [不支援超過 256 mb 的環境](#environment-limits)。 當環境超過此限制時，您會進入空白的天空方塊，而不需要模型。

### <a name="it-takes-a-long-time-to-load-my-environment"></a>載入我的環境需要很長的時間

您可以為您的環境新增選擇性的優化，以加快載入的速度。 如需詳細資訊，請參閱「 [將您的環境優化](#optimizing-your-environment) 」。

### <a name="the-scale-of-my-environment-is-incorrect"></a>我的環境規模不正確

Windows Mixed Reality 會在載入環境時將 glTF 單位轉譯為1計量。 如果您的環境載入未預期的規模，請再次檢查您的匯出工具，以確定您是以1計量規模的模型化。 

### <a name="the-spawn-location-in-my-environment-is-incorrect"></a>我的環境中產生的位置不正確

預設產生位置位於環境中0、0、0。 目前無法自訂此位置，因此您必須將您的環境與您想要的產生點上的來源一起匯出，以修改產生點。

### <a name="the-audio-doesnt-sound-correct-in-the-environment"></a>音訊在環境中無法正確播放

當您建立自訂環境時，它會使用聲場呈現模擬，而不符合您所建立的實體空間。 音效可能來自錯誤的方向，而且可能音效 muffled。 

## <a name="see-also"></a>另請參閱
* [GitHub 上的 Windows Mixed Reality 資產轉換器 () ](https://github.com/Microsoft/glTF-Toolkit/releases)