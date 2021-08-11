---
title: 全像攝影框架
description: 瞭解使用者如何透過全像攝影框架查看混合現實世界，以及如何以最佳的方式設計體驗。
author: cre8ivepark
ms.author: dongpark
ms.date: 06/25/2020
ms.topic: article
keywords: HoloLens、Windows Mixed Reality、全像攝影框架、FOV、混合現實耳機、Windows Mixed reality 耳機、虛擬實境耳機、HoloLens、MRTK、混合現實工具組、互動、流覽、功能表
ms.openlocfilehash: be24f2b583541e6ed0adff25b3d8edd6c3fe5285aea93d0a4d6df8ee61e5c070
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2021
ms.locfileid: "115226374"
---
# <a name="holographic-frame"></a>全像攝影框架

使用者透過其頭戴式裝置所提供的矩形視口，來看到混合實境的世界。 在 HoloLens 上，這個矩形區域稱為全像攝影框架，可讓使用者看到其周圍真實世界中的數位內容。 針對全像攝影畫面格設計經驗的設計體驗，可創造機會、降低挑戰，以及加強混合現實應用程式的使用者體驗。

## <a name="designing-for-content"></a>為內容設計

通常，設計人員會覺得需要將其經驗範圍限制為使用者可以立即看到的內容，並犧牲真實世界的規模，以確保使用者能看到整個物件。 同樣地，具有複雜應用程式的設計人員通常會使用內容來多載全像全像的框架、很難互動的使用者，以及雜亂的 建立混合現實內容的設計人員不需要將體驗直接放在使用者的前方，也不需要限制在其立即觀看中。 如果對應使用者的實體世界，則應該將所有這些表面視為數位內容和互動的可能畫布。 在體驗中適當地設計互動和內容，應該鼓勵使用者四處移動空間、將注意力導向重要內容，並協助查看混合現實的潛能。

在應用程式中鼓勵移動和探索最重要的技巧，或許是 **讓使用者調整體驗**。 使用裝置提供短時間的「免工作」時間給使用者。 這可以像將物件放在空間中一樣簡單，讓使用者四處移動或 narrating 體驗簡介。 這次應該是任何重要的工作，或像是按下的特定手勢。 目的是讓使用者在要求互動或透過應用程式進行之前，透過裝置來查看內容。 這對於第一次的使用者來說特別重要，因為他們可以透過全像全像全像全像全像全像全像地看到內容。

### <a name="large-objects"></a>大型物件

通常，體驗所呼叫的內容（尤其是真實世界的內容）會比全像全像全像全像全像攝影框架一樣。 通常無法容納在全像攝影框架內的物件，應該在第一次以較小的規模或距離)  (時，進行壓縮以符合其大小。 關鍵是讓使用者在尺規 overwhelms 框架之前 **查看物件的完整大小** 。 例如，您應該會顯示全像大象，以在框架內完全符合。 這可讓使用者在將動物的整體圖形調整為接近使用者的 [真實世界規模](scale.md) 之前，對動物的整體圖形形成空間瞭解。

記住物件的完整大小之後，使用者就會期望在哪裡四處移動和尋找該物件的特定部分。 在具有沉浸式內容的體驗中，它可協助您回頭參考該內容的完整大小。 比方說，如果體驗牽涉到虛擬房屋的模型，則可以使用較小的娃娃內部大小版本來指出其在房屋內部的位置。

如需針對大型物件設計的範例，請參閱 [Volvo Cars](holographic-frame.md#volvo-cars)。

### <a name="many-objects"></a>許多物件

有許多物件或元件的體驗，應該考慮使用使用者的完整空間，以避免直接在使用者面前將全像攝影框架雜亂。 建議您將內容的引入速度減緩至體驗，特別是計畫為使用者提供許多物件的體驗。 關鍵在於 **讓使用者瞭解體驗中的內容版面** 配置，以協助他們充分瞭解內容更新的內容。

達成此目的的方法之一，是在將內容錨定至真實世界的體驗中提供持續點 (也稱為地標) 。 例如，地標可能是真實世界中的實體物件，例如數位內容出現所在的表格，或是數位物件，例如經常出現內容的一組數位畫面。 您也可以將物件放在全像攝影框架的其邊界中，以鼓勵使用者尋找重要的內容。 探索超出其邊界的內容可透過 [注意總監](holographic-frame.md#attention-directors)來輔助。

將物件放在其邊界中可鼓勵使用者查看端，而這可由注意總監輔助，如下所述。 如需有關全像攝影框架考慮的詳細資訊，請參閱 [緩和](comfort.md#holographic-frame-considerations) 檔。

<br>

---

## <a name="interaction-considerations"></a>互動考慮

如同內容，混合現實體驗的互動不需要限制為使用者可以立即看到的內容。 互動可以在使用者周圍的真實世界空間中的任何位置進行。 這些互動有助於鼓勵使用者四處移動和探索體驗。

### <a name="attention-directors"></a>注意總監

指出感興趣的點或主要互動，對於透過體驗進行使用者來說非常重要。 以微妙或繁重的方式導向全像攝影框架的使用者注意和移動。 請記得以混合現實的免費探索期間來平衡注意總監 (特別是在體驗) 的一開始，以避免使用者感到不知所措。 一般情況下，有兩種類型的注意總監：
* **視覺導演：** 讓使用者知道他們應該以特定方向移動的最簡單方式，就是提供視覺指示。 您可以透過視覺效果來完成這項工作 (例如，使用者可透過視覺方式追蹤到下一個體驗的路徑) 或甚至是簡單的方向箭號。 任何視覺指標都應該在使用者的環境內進行，而不是「附加」至全像全像框架或游標。
* **音訊總監：** [空間音效](spatial-sound-design.md) 可以提供強大的方式來建立場景中的物件。 您可以將使用者的觀點移至重要物件，以警示使用者進入經驗，或將使用者的觀點移到特定的空間點。 使用音訊主管來引導使用者注意，可能會比視覺導演更微妙且更不具侵入性。 在某些情況下，最好是從音訊主管著手，然後在使用者無法辨識提示時移至視覺導演。 音訊總監也可以與視覺導演配對，以提高強調效果。

### <a name="commanding-navigation-and-menus"></a>命令、導覽和功能表

混合現實體驗中的介面，在理想的情況下會與所控制的數位內容緊密配對。 因此，自由浮點數的2D 功能表通常不適合互動，而且在全像全像全像全像的框架內，使用者可能會很難處理。 針對需要介面專案（例如功能表或文字欄位）的體驗，請考慮在短暫延遲之後，使用以標記為依據的 [方法](billboarding-and-tag-along.md) 來依照全像攝影畫面。 避免鎖定畫面上的內容，例如列印頭顯示，因為這可以針對使用者 disorienting，以及打破場景中其他數位物件的深度意義。

您也可以將介面專案直接放在其所控制的特定內容，讓互動在使用者的實體空間周圍自然發生。 例如，將複雜的功能表分成不同的部分，並將每個按鈕或控制項群組附加至互動影響的特定物件。 若要進一步瞭解這個概念，請考慮使用 [互動物件](interactable-object.md)。

### <a name="gaze-and-gaze-targeting"></a>注視和注視目標

全像攝影框架提供一種工具，可讓開發人員觸發互動並評估使用者的注意力 dwells。 「[注視](gaze-and-commit.md)」是[HoloLens 的主要互動](interaction-fundamentals.md)，其中的注視可以與[手勢](gaze-and-commit.md#composite-gestures)配對 (例如，透過按下) 或[語音](voice-input.md) (允許較短、更自然的語音互動) 。 如此一來，就能讓全像攝影的框架成為觀察數位內容並與其互動的空間。 如果體驗在使用者的空間周圍與多個物件進行互動 (例如，在使用者的空間周圍，以注視 + 手勢) 來進行多個物件的選擇，請考慮將這些物件帶入使用者的觀點，或限制需要的前端移動量，以提升 [使用者](comfort.md)的能力。

您也可以使用「注視」來追蹤使用者的體驗，並查看使用者最注意的部分物件或場景部分。 這特別適合用來偵測體驗，並可讓熱度圖等分析工具查看使用者花費最多時間或遺失某些物件或互動的位置。 注視追蹤也可以提供強大的 facilitators 體驗工具 (請參閱 [Lowe 的廚房](holographic-frame.md#lowes-kitchen) 範例) 。

如果您想要查看前端和眼睛追蹤設計的概念，請參閱下面 **的設計全像投影標頭追蹤和眼睛追蹤** 影片示範：

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Head-Tracking-and-Eye-Tracking-Chapter/player]

*這段影片取自「設計全像投影」 HoloLens 2 應用程式。下載並享有完整 [的體驗。](https://aka.ms/dhapp)*

<br>

---

## <a name="performance"></a>效能

適當地使用全像攝影框架，是 [效能品質](../develop/platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md) 體驗的基礎。 常見的技術 (和可用性) 挑戰是以數位內容來多載使用者的畫面格，進而降低轉譯效能。 請考慮改為使用上面所述的技術來排列數位內容，以減少轉譯的負擔並確保最佳的顯示品質。

HoloLens 的全像範圍內的數位內容也可以與[穩定平面](../develop/platform-capabilities-and-apis/case-study-using-the-stabilization-plane-to-reduce-holographic-turbulence.md)配對，以獲得最佳效能和全像全像的[穩定性](../develop/platform-capabilities-and-apis/hologram-stability.md)。

<br>

---

## <a name="examples"></a>範例

### <a name="volvo-cars"></a>Volvo 車

<iframe width="940" height="530" src="https://www.youtube.com/embed/DilzwF90vec" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

在 Volvo 汽車的 showroom 體驗中，客戶會受邀在 Volvo 相關聯的 HoloLens 體驗中瞭解新車的功能。 全像全尺寸的 Volvo 面對挑戰：全尺寸的汽車太大，無法在使用者旁邊放置。 解決方法是開始使用實體地標（showroom 中的中央資料表）的體驗，並以較小的車輛數位模型放在資料表的最上方。 這可確保使用者在引進時看到完整的汽車，讓您能夠在車輛成長到其實際經驗之後的真實世界規模之後，瞭解空間的理解。

Volvo 的經驗也利用了視覺導演，從資料表上的小型汽車模型，到顯示空間中的牆上建立長的視覺效果。 這會導致「魔術視窗」效果，並以距離顯示汽車的完整觀點，以真實世界的規模來說明車輛的進一步功能。 前端移動是水準的，不會與使用者直接互動， (改為以視覺化方式收集提示，並從 Volvo 的體驗) 旁白。

<br>

---

### <a name="lowes-kitchen"></a>Lowe 的廚房

Lowe 的商店體驗邀請客戶進入廚房的全大規模原型，以展示透過 HoloLens 所見到的各種裝修商機。 存放區中的廚房提供了數位物件的實體背景、設備的空白畫布、countertops，以及用來展開混合現實體驗的封包。

實體表面可作為靜態地標，讓使用者在體驗中脫穎而出，因為 Lowe 的關聯會引導使用者完成不同的產品選項並完成。 如此一來，關聯可 verbally 將使用者的注意力導向至展示數位內容的「冰箱」或「中心」。

![Lowe 的關聯會使用平板電腦來引導客戶 HoloLens 體驗。](images/loweskitchen-750px.jpg)<br>
*Lowe 的關聯會使用平板電腦來引導客戶 HoloLens 體驗。*

使用者的體驗是由 Lowe 的關聯性所控制的平板電腦體驗來管理。 在此情況下，關聯性角色的一部分也會限制過度的移動量，並在廚房的景點中順暢地強調。 平板電腦體驗也提供 Lowe 的關聯性，並以廚房的熱度圖視圖形式呈現觀賞的資料，協助您瞭解使用者俗套的位置 (例如，在 cabinetry) 的特定區域，以更精確地提供裝修指引。

若要深入瞭解 Lowe 的廚房體驗，請參閱 [Microsoft 在 Ignite 2016](https://www.youtube.com/watch?v=gC_4JxF0e_k)的專題演講。

<br>

---

### <a name="fragments"></a>片段

在 HoloLens 遊戲片段中，您的房間會轉換成虛擬犯罪場景，以顯示線索和辨識項，以及一個虛擬會議室，讓您與您的椅子上的字元和您的牆壁保持聯繫。

![片段的設計目的是要在使用者的首頁中進行，並將字元與真實世界的物件和表面互動。](images/fragments-750px.jpg)<br>
*片段的設計目的是要在使用者的首頁中進行，並將字元與真實世界的物件和表面互動。*

當使用者一開始就開始使用時，會有短暫的調整時間，幾乎不會有任何互動。 相反地，我們鼓勵他們自行尋找和導向，並確保該遊戲的互動式內容可以正確地對應房間。

在整個過程中，字元會成為焦點，並做為視覺導演 (在字元之間進行前端移動，並將搜尋或手勢指向感興趣的區域) 。 當使用者花太多時間找出物件或事件，以及大量使用空間音效時，此遊戲也會依賴更顯著的視覺提示 (特別是在進入場景) 時使用字元語音。

<br>

---

### <a name="destination-mars"></a>目的地： Mars

在 [NASA 的甘迺迪空間中心](https://blogs.windows.com/devices/2016/09/19/hololens-experience-destination-mars-now-open-at-kennedy-space-center-visitor-complex/)的目的地： mars 體驗中，訪客已受邀進入 mars 的範圍，並以虛擬標記法傳說太空人的發燒 Aldrin 來引導。

![虛擬消息 Aldrin 會成為目的地： Mars 中使用者的焦點。](images/destinationmars-750px.png)<br>
*虛擬消息 Aldrin 會成為目的地： Mars 中使用者的焦點。*

以沉浸式的方式，我們鼓勵這些使用者四處四處移動，以查看虛擬 Martian 的範圍。 雖然為了確保使用者的熟悉度，但 Aldrin 的旁白和虛擬目前狀態都提供了整個體驗的焦點。 這份由 [Microsoft 的混合實境擷取工作室](https://www.microsoft.com/mixed-reality/capture-studios)) 勇敢面對考驗所建立的發燒 (，可讓使用者以近乎完整的觀點來查看他的工作。 有興趣的學生的旁白會將焦點放在環境中的不同點 (例如，一組 Martian rocks 在地面上，或是在特定場景變更或他所引進的物件) 的不同。

![虛擬 narrators 將會轉換為遵循使用者的移動，在整個體驗中建立功能強大的焦點。](images/gazereset-750px.png)<br>
*虛擬 narrators 將會轉換為遵循使用者的移動，在整個體驗中建立功能強大的焦點。*

實際的口頭表達方式提供了功能強大的焦點，並利用微妙的技巧來將您的消息轉變成使用者，像是我說的一樣。 當使用者移動經驗時，如果使用者移到他的其邊界以外的範圍，則會在返回中性狀態之前，先將您導向至閾值。 如果使用者從內容中看起來完全 (比方說，若要查看場景中其他地方) 再回頭看看，朗讀程式的方向位置將會再次以使用者為主。 這類技術可提供強大的深度功能，並在全像全像的框架內建立焦點，減少過多的前端移動並提升 [使用者的舒適](comfort.md)。

## <a name="see-also"></a>另請參閱
* [本能互動](interaction-fundamentals.md)
* [舒適度](comfort.md)
* [調整](scale.md)
* [頭部目光和停駐](gaze-and-dwell.md)
* [全像投影穩定性](../develop/platform-capabilities-and-apis/hologram-stability.md)
