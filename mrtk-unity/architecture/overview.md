---
title: 架構概觀
description: MRTK 的架構總覽。
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK 架構、
ms.openlocfilehash: 7113ee68a3d8bae016236996725a879c95e31f410cb273184ddcc255ae7a0685
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2021
ms.locfileid: "115186596"
---
# <a name="architecture-overview"></a>架構概觀

如需 MRTK 內容的整體簡介，本檔中包含的架構資訊將協助您瞭解下列各項：

- 大量 MRTK 以及它們如何連接
- MRTK 引進的概念可能不存在於香草 Unity 中
- 某些較大型的系統 (例如輸入) 的運作方式

本節的目的不是要告訴您如何進行工作，而是如何將這類工作結構化及原因。

## <a name="many-audiences-one-toolkit"></a>許多物件，一個工具組

MRTK 沒有單一、統一的物件。 它是為了支援使用案例（範圍從第一次駭客松），到為企業建立複雜且共用體驗的人員所撰寫。 某些程式碼和 Api 可能已撰寫為比其他更多的 (，也就是 MRTK 的某些部分會比較適合「單鍵設定」 ) ，但請務必注意，某些程式碼和應用程式開發介面的原因較多。 隨著 MRTK 發展，所建的功能應該設計成可支援使用案例的範圍。

MRTK 也具有在 VR 和 AR 體驗之間妥善調整的需求。 將應用程式部署在 HoloLens 2 或 HoloLens 1 上時，應該可以輕鬆地建立可正常回復行為的應用程式，而且必須簡單地建立以 OpenVR 和 (WMR 為目標的應用程式，以及) 的其他平臺。 雖然團隊有時可能會將特定的反復專案放在特定的系統或平臺上，但長期目標是要在使用者建立混合現實體驗的任何地方建立廣泛的支援。

## <a name="high-level-breakdown"></a>高層級明細

MRTK 是一組工具的集合，可讓您輕鬆地 (MR) 的經驗，同時也提供應用程式架構，其中包含自己的執行時間、其擴充方式，以及其設定方式。

概括而言，MRTK 可透過下列方式細分：

![架構總覽圖表](../features/images/architecture/MRTK_Architecture.png)

MRTK 還包含另一組抓取包公用程式，這些公用程式幾乎不需要相依于其餘的 MRTK (來列出一些：組建工具、解析器、音訊影響因素、平滑處理公用程式和線條轉譯器) 

架構檔的其餘部分將從架構和執行時間開始，並在更有趣且複雜的系統（例如輸入）上發展。 請參閱目錄以繼續進行架構總覽。
