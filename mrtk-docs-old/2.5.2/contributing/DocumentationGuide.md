---
title: DocumentationGuide
description: MRTK 的檔指導方針和標準。
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: cc940aa1458db3e67c1ab30ea243adfc51eca7af
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/03/2021
ms.locfileid: "101783407"
---
# <a name="documentation-guidelines"></a>檔指導方針

![MRTK 標誌](../features/images/MRTK_Logo_Rev.png)

本檔概述混合現實工具組 (MRTK) 的檔指導方針和標準。 這提供撰寫和產生檔的技術層面簡介、強調常見的陷阱，以及描述建議的書寫樣式。

頁面本身應該作為範例，因此它會使用預期的樣式以及檔的最常見標記功能。

- [來源](#source-documentation)
- [How to](#how-to-documentation)
- [設計](#design-documentation)
- [效能注意事項](#performance-notes)
- [重大變更](#breaking-changes)

---

## <a name="functionality-and-markup"></a>功能和標記

本節將描述經常需要的功能。 若要查看其運作方式，請查看頁面的原始程式碼。

1. 編號清單
   1. 具有至少3個前置空格的嵌套編號清單
   1. 程式碼中的實際數位不相關;剖析將會負責設定正確的專案編號。

- 專案符號點清單
  - 嵌套的專案符號點清單
- 以 **粗體顯示** 的文字（含 \* \* 雙星號）\*\*
-  具有 \_ 底線 \_ 或 \* 單一星號的斜體文字\*
- `highlighted as code`使用 backquotes 的句子中的文字 \`\`
- 檔頁面連結 [MRTK 檔指導方針](DocumentationGuide.md)
- [頁面內錨點](#style)的連結;錨點的形成方式是以連字號取代空格，然後轉換成小寫

在程式碼範例中，我們會使用具有三個倒引號的區塊 \` \` \` ，並將 *csharp* 指定為語法醒目提示的語言：

```c#
int SampleFunction(int i)
{
   return i + 42;
}
```

在句子內提及程式碼時 `use a single backtick` 。

### <a name="todos"></a>待辦事項

避免在檔中使用待辦事項，因為在經過一段時間後，這些待辦事項 (（例如程式碼) 待辦事項）通常會累積，以及應如何更新它們以及遺失原因的相關資訊。

如果絕對需要新增 TODO，請遵循下列步驟：

1. 在 Github 上提出新的問題，描述 TODO 背後的內容，並提供足夠的背景，讓其他參與者能夠瞭解並解決 TODO 問題。
2. 參考檔中 todo 的問題 URL。

\<\!-- TODO: [https://github.com/microsoft/MixedRealityToolkit-Unity/issues/ISSUE_NUMBER_HERE](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/ISSUE_NUMBER_HERE)  A brief blurb on the issue --\>

### <a name="highlighted-sections"></a>反白顯示的區段

若要反白顯示讀取器的特定點，請使用 *> [!NOTE]* 、 *> [!WARNING]* 和 *> [!IMPORTANT]* 來產生下列樣式。 建議您僅針對特殊的相關案例，使用一般點的附注和警告/重要點。

> [!NOTE]
> 附注範例

> [!WARNING]
> 警告範例

> [!IMPORTANT]
> 重要批註的範例

## <a name="page-layout"></a>頁面配置

### <a name="introduction"></a>簡介

主要章節標題後面的部分應該會是本章所述的簡短簡介。 請勿將此值設得太長，而是新增子頭條新聞。 這些可讓您連結至區段，並可儲存為書簽。

### <a name="main-body"></a>主體

使用雙層級和三層級的頭條來結構其餘部分。

**迷你區段**

使用粗體的文字來表示應該要注意的區塊。我們可能會在某個時間點以四個層級的頭條新聞來取代此項。

### <a name="see-also-section"></a>「另請參閱」一節

大部分的頁面最後應該會有一個稱為 [ *另請參閱*] 的章節。 這一章只是一個專案符號，指向與此主題相關的頁面連結清單。 這些連結可能也會出現在適當的頁面文字內，但不是必要的。 同樣地，頁面文字可能包含與主要主題沒有關聯之頁面的連結，這些連結也不應該包含在 [ *請參閱* ] 清單中。 請參閱 [此頁面的「另請參閱」一章](#see-also) ，以選擇連結的範例。

## <a name="table-of-contents-toc"></a>目錄 (TOC) 

在 MRTK github.io 檔中，會使用 Toc 檔案來產生巡覽列。
每當新增檔檔案時，請確定檔資料夾的其中一個 yml 檔案中有該檔案的專案。 只有目錄檔案中列出的文章會顯示在開發人員檔的導覽中。[檔] 資料夾中的每個子資料夾都可以有一個 toc 檔案，您可以將它連結到任何現有的 toc 檔案，將它做為子區段加入至導覽的對應部分。

## <a name="style"></a>樣式

### <a name="writing-style"></a>撰寫樣式

一般經驗法則：嘗試 **音效 professional**。 這通常表示要避免「對話式語氣」。 也請嘗試避免 hyperbole 和 sensationalism。

1. 請勿嘗試 (過於有趣的) 。
2. 絕不寫入 ' I '
3. 避免「我們」。 這通常可以使用 ' MRTK ' 來輕鬆改換措辭。 範例：「我們支援這項功能」-> 「MRTK 支援這項功能」或「支援下列功能 ...」。
4. 同樣地，請試著避免「您」。 範例：「有了這個簡單的變更，您的著色器就變成可設定的！」 -> 「可以輕鬆設定著色器」。
5. 請勿使用 ' 草率片語 '。
6. 避免發音太興奮，我們不需要銷售任何事物。
7. 同樣地，請避免過度大幅。 驚嘆號很少需要用到。

### <a name="capitalization"></a>大寫

- 將 **句子案例用於頭條新聞**。 亦即 將第一個字母和名稱大寫，但不需要其他任何專案。
- 針對其他所有專案使用一般英文。 這表示 **不會將任意字組大寫**，即使它們在該內容中有特殊意義也一樣。 偏好 *斜體文字* 以醒目提示特定文字， [請參閱下文](#emphasis-and-highlighting)。
- 當連結內嵌于句子 (（) 慣用的方法）時，標準章節名稱一律會使用大寫字母，因此會中斷文字內部沒有任意大小寫的規則。 因此，請使用自訂連結名稱來修正大小寫。 例如，以下是 [界限控制項](../features/ux-building-blocks/BoundsControl.md) 檔的連結。
- 請將名稱大寫，例如 *Unity*。
- 撰寫 *Unity 編輯器* 時，請勿將「編輯器」變成大寫。

### <a name="emphasis-and-highlighting"></a>強調和反白顯示

有兩種方式可以強調或反白顯示字組，使其變成粗體或使其成為斜體。 粗體文字的效果是 **粗體文字** ，因此可以在 skimming 一段文字，或甚至只是在頁面上顯示時，輕易注意到。 粗體很適合用來醒目提示人們應記住的片語。 不過， **很少使用粗體文字**，因為通常會造成干擾。

通常會有一個「群組」是以邏輯方式存在的內容，或反白顯示特定詞彙，因為它具有特殊意義。 這類專案不需要與整體文字相關。 使用斜體文字作為 *輕量方法* ，以反白顯示某個東西。

同樣地，在文字中提及檔案名、路徑或功能表項目時，最好將它設為斜體以進行邏輯分組，而不會造成干擾。

一般情況下，請嘗試 **避免不必要的文字** 反白顯示。 特殊字詞可以反白顯示，讓讀者知道，當它不再有目的，而且只是 distracts 時，請不要在整個文字中重複這類的反白顯示。

### <a name="mentioning-menu-entries"></a>提及功能表項目

提及使用者應該按一下的功能表項目時，目前的慣例是： *Project > Files > 建立 > 分葉*

### <a name="links"></a>連結

盡可能將許多有用的連結插入至其他頁面，但每個連結只會出現一次。 假設讀者按一下頁面中的每個連結，並思考它的麻煩程度，如果同一個頁面開啟了20次。

偏好內嵌于句子中的連結：

- 錯誤：指導方針很有用。 如需詳細資訊，請參閱 [這一章](DocumentationGuide.md) 。
- 好： [指導方針](DocumentationGuide.md) 很有用。

避免外部連結，它們可能會變成過期或包含受著作權的內容。

新增連結時，請考慮它是否也應該列在 [ [另請參閱](#see-also) ] 區段中。 同樣地，檢查是否應將新頁面的連結加入至連結的頁面。

### <a name="images--screenshots"></a>影像/螢幕擷取畫面

**請謹慎使用螢幕擷取畫面。** 在檔中維護映射是很多工作，小型 UI 的變更可能會導致許多螢幕擷取畫面過期。 下列規則將減少維護工作：

1. 請勿針對可在文字中描述的專案使用螢幕擷取畫面。 尤其是， **絕對不會顯示內容方格的螢幕擷取畫面** ，以顯示內容名稱和值的唯一用途。
2. 請勿在與顯示內容無關的螢幕擷取畫面中包含專案。 例如，顯示轉譯效果時，請建立該區的螢幕擷取畫面，但在其周圍排除任何 UI。 在顯示某些 UI 的情況下，請試著四處移動視窗，如此一來，只有該重要部分才會在影像中。
3. 包含螢幕擷取畫面 UI 時，只會顯示重要的部分。 例如，在討論工具列中的按鈕時，請建立一個小影像來顯示重要的工具列按鈕，但是排除它周圍的所有專案。
4. 只使用容易重現的映射。 這表示不會在螢幕擷取畫面中繪製標記或反白顯示。 首先，這些都不會有一致的規則。 其次，重新產生這類螢幕擷取畫面是額外的工作。 相反地，請描述文字中的重要部分。 這項規則有一些例外狀況，但很罕見。
5. 很明顯地，重新建立動畫 GIF 的工作更多。 如果不想花時間，就必須負責重新建立，直到時間結束為止，或希望人們擲出它。
6. 讓文章中的影像數目減少。 通常，最好的方法是為某些工具提供一個整體的螢幕擷取畫面，以顯示所有專案，然後在文字中描述其餘部分。 這可讓您視需要輕鬆地取代螢幕擷取畫面。

其他方面：

- 螢幕擷取畫面的編輯器 UI 應該使用淺灰色主題編輯器，因為並非所有使用者都有深色主題的存取權，而且我們想要盡可能保持一致的專案。
- 預設影像寬度為500圖元，因為這會在大部分監視器上顯示得很好。 不要再從它偏離太多。 800圖元的寬度應為最大值。
- 使用 Png 來取得 UI 的螢幕擷取畫面。
- 將 Png 或 Jpg 用於3D 視窗圖的螢幕擷取畫面。 偏好超過壓縮比例的品質。

### <a name="list-of-component-properties"></a>元件屬性清單

記錄屬性清單時，請使用粗體文字來反白顯示內容名稱、分行符號號和一般文字來描述它們。 請勿使用子章節或專案符號點清單。

此外，別忘了以句號完成所有句子。

## <a name="page-completion-checklist"></a>頁面完成檢查清單

1. 確定已遵循本檔的指導方針。
1. 流覽檔結構，並查看是否可在其他頁面的 [另 [請參閱](#see-also) ] 區段下提及新檔。
1. 如果有的話，請讓有人瞭解如何證明頁面的技術正確性。
1. 讓他人證明頁面的樣式和格式。 這可能是主題中不熟悉的使用者，這也是取得檔瞭解如何理解的建議。

## <a name="source-documentation"></a>來原始檔案

API 檔將會自動從 MRTK 原始檔產生。 為了方便進行，來源檔案必須包含下列各項：

- [類別、結構、列舉摘要區塊](#class-struct-enum-summary-blocks)
- [屬性、方法、事件摘要區塊](#property-method-event-summary-blocks)
- [功能簡介版本和相依性](#feature-introduction-version-and-dependencies)
- [序列化欄位](#serialized-fields)
- [列舉值](#enumeration-values)

除了上述的程式碼，程式碼應該有適當的批註，以便進行維護、bug 修正和自訂的簡化。

### <a name="class-struct-enum-summary-blocks"></a>類別、結構、列舉摘要區塊

如果將類別、結構或列舉新增至 MRTK，就必須描述其用途。 這是採用類別之上的摘要區塊形式。

```c#
/// <summary>
/// AudioOccluder implements IAudioInfluencer to provide an occlusion effect.
/// </summary>
```

如果有任何類別層級相依性，這些相依性應該記錄在備註區塊中，緊接在摘要下方。

```c#
/// <remarks>
/// Ensure that all sound emitting objects have an attached AudioInfluencerController.
/// Failing to do so will result in the desired effect not being applied to the sound.
/// </remarks>
```

如果沒有類別、結構或列舉的摘要，提交的提取要求將不會獲得核准。

### <a name="property-method-event-summary-blocks"></a>屬性、方法、事件摘要區塊

屬性、方法和事件 (PMEs) 以及欄位都要記錄在摘要區塊中，不論程式碼可見度 (公用、私用、受保護和內部) 。 檔產生工具會負責篩選出和只發行公用和受保護的功能。

注意： Unity 方法 **不** 需要摘要區塊 (例如：喚醒、啟動、更新) 。

**需要** 有 PME 檔才能核准提取要求。

作為 PME 摘要區塊的一部分，需要參數和傳回資料的意義和用途。

```c#
/// <summary>
/// Sets the cached native cutoff frequency of the attached low pass filter.
/// </summary>
/// <param name="frequency">The new low pass filter cutoff frequency.</param>
/// <returns>The new cutoff frequency value.</returns>
```

### <a name="feature-introduction-version-and-dependencies"></a>功能簡介版本和相依性

作為 API 摘要檔的一部分，這是引入功能的 MRTK 版本相關資訊，而任何相依性都應記載于備註區塊中。

相依性應該包含擴充功能和/或平臺相依性。

```c#
/// <remarks>
/// Introduced in MRTK version: 2018.06.0
/// Minimum Unity version: 2018.0.0f1
/// Minimum Operating System: Windows 10.0.11111.0
/// Requires installation of: ImaginarySDK v2.1
/// </remarks>
```

### <a name="serialized-fields"></a>序列化欄位

使用 Unity 的 tooltip 屬性來提供偵測器中腳本欄位的執行時間檔是很好的作法。

為了讓設定選項包含在 API 檔中，腳本必須 *至少* 包含摘要區塊中的工具提示內容。

```c#
/// <summary>
/// The quality level of the simulated audio source (ex: AM radio).
/// </summary>
[Tooltip("The quality level of the simulated audio source.")]
```

### <a name="enumeration-values"></a>列舉值

在定義和列舉時，程式碼也必須使用摘要區塊來記錄列舉值的意義。 您可以選擇性地使用備註區塊來提供其他詳細資料，以增強理解。

```c#
/// <summary>
/// Full range of human hearing.
/// </summary>
/// <remarks>
/// The frequency range used is a bit wider than that of human
/// hearing. It closely resembles the range used for audio CDs.
/// </remarks>
```

## <a name="how-to-documentation"></a>How to 檔

混合現實工具組的許多使用者可能不需要使用 API 檔。 這些使用者將利用我們預先製作的可重複使用 prefabs 和腳本，來建立他們的體驗。

每個功能區域將包含一或多個 markdown ( md) 檔案，這些檔案會以相當高的層級來描述。 視指定功能區域的大小和/或複雜度而定，可能需要額外的檔案，每個功能提供最多一個檔案。

當 (新增功能或變更使用方式時) ，就必須提供總覽檔。

在本檔中，您應該提供「如何」區段（包括圖例），以協助新的客戶開始使用功能或概念。

## <a name="design-documentation"></a>設計檔

Mixed Reality 讓您有機會建立全新的領域。 這可能牽涉到建立自訂資產以與 MRTK 搭配使用。 為了讓客戶能更輕鬆地釋出這種情況，元件應該提供描述任何格式或其他藝術資產需求的設計檔。

設計檔可能會有説明的一些範例：

- 資料指標模型
- 空間對應視覺效果
- 音效效果檔案

**強烈** 建議您採用這種類型的檔，而且 **可能** 會在提取要求審核過程中要求。

這不一定與[MS 開發人員網站](https://docs.microsoft.com/windows/mixed-reality/design)上的設計建議不同

## <a name="performance-notes"></a>效能注意事項

有一些重要功能會產生效能成本。 這段程式碼通常會根據其設定方式而定。

例如：

```md
When using the spatial mapping component, the performance impact will increase with the level of detail requested.  
It is recommended to use the least detail possible for the desired experience.
```

建議針對 CPU 和/或 GPU 繁重的元件使用效能注意事項，而且 **可能** 會在提取要求審核過程中要求。 任何適用的效能注意事項都會包含在 API **和** 總覽檔中。

## <a name="breaking-changes"></a>重大變更

重大變更 [檔](BreakingChanges.md) 是由最上層的檔案所組成，其會連結至每個功能區域的個別 [BreakingChanges.md](BreakingChanges.md)。

功能區 [BreakingChanges.md](BreakingChanges.md) 檔包含特定版本的所有已知中斷變更清單 **，以及過去** 版本的重大變更歷程記錄。

例如：

```md
Spatial sound breaking changes

2018.07.2
* Spatialization of the imaginary effect is now required.
* Management of randomized AudioClip files requires an entropy value in the manager node.

2018.07.1
No known breaking changes

2018.07.0
...
```

包含在功能層級 [BreakingChanges.md](BreakingChanges.md) 檔案中的資訊，將會匯總為每個新 MRTK 版本的版本資訊。

任何屬於變更一部分的重大變更都 **必須** 記載為提取要求的一部分。

## <a name="tools-for-editing-markdown"></a>用來編輯 MarkDown 的工具

[Visual Studio Code](https://code.visualstudio.com/) 是很棒的工具，可讓您編輯屬於 MRTK 檔的 markdown 檔案。

撰寫檔時，也強烈建議您安裝下列兩個延伸模組：

- Visual Studio Code 的檔 Markdown 擴充功能-使用 Alt + M 來顯示檔撰寫選項的功能表。

- 程式碼拼寫檢查-拼錯的單字會加上底線;以滑鼠右鍵按一下拼錯的字組來變更它，或將它儲存至字典。

這兩個套件都封裝在 Microsoft 發行的檔撰寫套件中。

## <a name="see-also"></a>另請參閱

- [檔入口網站產生指南](DevDocGuide.md)
