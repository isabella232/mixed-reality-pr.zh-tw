---
title: 遷移視窗
description: 如何在 MRTK 中遷移至更新的相關檔
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: 9d960d01e738736edd452a124db5c306b5d752ce
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176135"
---
# <a name="migration-window"></a>遷移視窗

當 MRTK 進行變更時，某些元件可能會被取代，並引進取代。
[遷移] 視窗是一種工具，可協助使用者將這些被取代元件的子集自動遷移至新的取代。

![遷移視窗](../images/migration-window/MRTK_Migration_Window.png)

## <a name="usage"></a>使用方式

若要開啟視窗，請選取 [**混合的實際**  >  **工具組**  >  **公用程式**  >  **遷移] 視窗**。 一旦開啟 [遷移] 視窗，您可以選擇遷移處理常式的元件特定執行方式來啟用 [選取模式] 流覽索引標籤。  

![遷移選取模式](../images/migration-window/MRTK_Migration_Modes.png)

### <a name="object-mode"></a>物件模式

選取 [物件] 索引標籤可讓物件欄位從目前開啟的場景或從要遷移的專案資料夾中的 prefabs，拖放任何遊戲物件。
按下所列物件右邊顯示的 [移除] *(-)* 按鈕，就會從選取清單中移除該物件。

當所有所需的物件都在清單中之後，按 [ *遷移* ] 按鈕會將所選遷移處理常式執行所需的變更，套用至選取範圍中符合執行的所有元件。

![選取專案遷移](../images/migration-window/MRTK_Object_Migration.png)

### <a name="scene-mode"></a>場景模式

允許使用者拖放包含要遷移之物件的場景資產。

![選取用於遷移的場景](../images/migration-window/MRTK_Scene_Selection.png)

### <a name="project-mode"></a>Project 模式

按下 [ *遷移* ] 按鈕將會針對專案中的所有 prefabs 和場景，更新遷移處理常式執行的目標群組件。

![遷移完整專案](../images/migration-window/MRTK_Project_Migration.png)

## <a name="see-also"></a>另請參閱

- [從較早的版本更新](../../updates-deployment/updating.md)
- [Microsoft Mixed Reality 工具組版本](../../release-notes/mrtk-26-release-notes.md)
- [MRTK 藍圖](../../roadmap.md)
