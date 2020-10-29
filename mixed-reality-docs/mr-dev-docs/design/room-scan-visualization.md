---
title: 空間位置掃描視覺效果
description: 需要空間對應資料的應用程式依賴裝置在一段時間內自動收集此資料，並在使用者探索其環境中使用中的裝置時，跨會話自動收集此資料。
author: mattzmsft
ms.author: alexpf
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality，應用程式模式、設計、HoloLens、會議室掃描、空間對應、網格
ms.openlocfilehash: 25de181bbb2dedaba9e4917f51cc80bac77cc5f1
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2020
ms.locfileid: "91679436"
---
# <a name="room-scan-visualization"></a>空間位置掃描視覺效果

需要空間對應資料的應用程式依賴裝置在一段時間內自動收集此資料，並在使用者探索其環境中使用中的裝置時，跨會話自動收集此資料。 這項資料的完整性和品質取決於許多因素，包括使用者已完成的探索量、從探索以來經過的時間，以及裝置掃描區域之後是否已移動傢俱和大門等物件。

為了確保有用的空間對應資料，應用程式開發人員有數個選項：
* 依賴可能已收集的內容。 這種資料一開始可能不完整。
* 要求使用者使用 bloom 手勢前往 Windows Mixed Reality 首頁，然後探索他們想要用於體驗的領域。 他們可以使用 [點一下] 來確認裝置已知所有必要的區域。
* 在自己的應用程式中建立自訂的探索體驗。

請注意，在所有這些情況下，在探索期間收集的實際資料會由系統儲存，而應用程式則不需要這麼做。

## <a name="device-support"></a>裝置支援

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><strong>功能</strong></td>
        <td><a href="../hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="../discover/immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></td>
    </tr>
     <tr>
        <td>空間位置掃描視覺效果</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>



## <a name="building-a-custom-scanning-experience"></a>建立自訂掃描體驗

應用程式可能會決定在體驗開始時分析空間對應資料，以判斷是否希望使用者執行額外的步驟來改善其完整性和品質。 如果分析指出品質應獲得改善，開發人員應該提供視覺效果以在世界上重迭，以表示：
* 使用者鄰近區中的總數量必須是經驗的一部分
* 使用者應該前往哪裡改善資料

使用者不知道什麼會進行「良好」掃描。 如果系統要求您評估掃描– flatness、與實際牆的距離等，則需要顯示或告知要尋找的內容。開發人員應執行意見反應迴圈，其中包含在掃描或探索階段期間重新整理空間對應資料。

在許多情況下，最好讓使用者知道他們需要做什麼事 (例如查看最上方的 [傢俱]) ，以便取得所需的掃描品質。

## <a name="cached-versus-continuous-spatial-mapping"></a>快取與連續空間對應

空間對應資料是最繁重的資料來源應用程式可取用的資料來源。 若要避免效能問題（例如捨棄的畫面格或間斷情形），應謹慎地使用此資料。

在體驗期間進行主動式掃描可能會有很大的説明，而開發人員必須根據經驗決定要使用的方法。

### <a name="cached-spatial-mapping"></a>快取的空間對應

在快取空間對應的情況下，應用程式通常會取得空間對應資料的快照集，並在體驗期間使用此快照集。

**優點**
* 降低系統的額外負荷，同時體驗能大幅提高電源、冷卻和 cpu 效能。
* 更簡單的主要體驗，因為空間資料的變更不會中斷。
* 針對物理、圖形和其他用途之空間資料的任何後置處理，都是單一時間成本。

**缺點**
* 實際物件或人員的移動不會由快取的資料反映。 例如 應用程式可能會在實際關閉時，將門視為開啟。
* 可能會有更多的應用程式記憶體，以維護資料的快取版本。

這種方法的良好案例是受控制的環境或資料表最上層的遊戲。

### <a name="continuous-spatial-mapping"></a>連續空間對應

某些應用程式可能會依賴繼續掃描以重新整理空間對應資料。

**優點**
* 您不需要在應用程式中事先建立個別的掃描或探索體驗。
* 雖然有一些延遲，但遊戲可能會反映實際物件的移動。

**缺點**
* 在主要體驗的執行上有更高的複雜度。
* 由於變更需要以累加方式內嵌這些系統，因此可能會額外增加圖形或物理處理的額外負荷。
* 更高的電源、冷卻和 CPU 的影響。

這種方法的理想情況是，全像投影應該與移動物件互動的情況，例如，地面磁片磁碟機可能會想要根據其是開啟或關閉的方式，正確地移入門。

## <a name="see-also"></a>另請參閱
* [空間對應](spatial-mapping.md)
* [座標系統](coordinate-systems.md)
* [空間音效設計](spatial-sound-design.md)
