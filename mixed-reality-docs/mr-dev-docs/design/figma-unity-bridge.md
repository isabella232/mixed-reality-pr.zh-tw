---
title: 適用于 Unity 的 MRTK Figma Bridge
description: MRTK Figma Bridge for Unity 可讓您將 Figma 工具組的版面配置帶入 Unity
author: dongpark
ms.author: dongpark
ms.date: 03/29/2021
ms.topic: article
keywords: Figma、素描、Adobe XD、設計、設計工具、設計檔、UX 設計、HoloLens、MRTK、混合現實工具組
ms.openlocfilehash: d21caa796907ebc7ea1fb46ce940cf210e9fc49d
ms.sourcegitcommit: 9431e9d6d7e959954ab3e18ecc0e420a3583d1a0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/21/2021
ms.locfileid: "128053779"
---
# <a name="mrtk-figma-bridge-for-unity-beta"></a>適用于 Unity (Beta) 的 MRTK Figma Bridge

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWKiO4]

MRTK Figma Bridge for Unity 可讓您將 Figma 工具組的版面配置帶入 Unity 中。 橋接器可以匯入以 MRTK Figma 工具組建立的 UI 版面配置，然後具適當的位置和大小，將對應的 MRTK prefabs 具現化。 Figma Bridge 將有助於設計設計師和開發人員之間的整合程式和協同作業。


請參閱[MRTK Figma 工具](figma-toolkit.md)組頁面，以瞭解 Figma 工具組，這是使用 HoloLens 2 樣式 UI 程式庫的設計檔。

## <a name="prerequisites"></a>必要條件
- 請參閱安裝適用于混合現實開發所需軟體的[工具](/windows/mixed-reality/develop/install-the-tools)
- Unity 2019 或更高版本
- [MRTK-Unity 2.7.0 或更高版本](/windows/mixed-reality/mrtk-unity/)

> [!IMPORTANT]
> **需要 MRTK-Unity 2.7.0 或更高版本**
> 
> 由於 Figma 工具組和 Figma 橋接器是以 MRTK 2.7.0 prefabs 為基礎，因此需要 MRTK 2.7.0 或更新版本。 搭配較低版本的 MRTK 使用時，某些元件不會正確轉譯。

## <a name="how-to-use-mrtk-figma-bridge"></a>如何使用 MRTK Figma Bridge

### <a name="1-installation"></a>1. 安裝

Figma Unity Bridge 可透過 [混合現實功能工具](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool)安裝。 下載並執行混合現實功能工具。

在 [ **探索功能** ] 頁面的 [ **混合現實工具** 組] 區段下，選取 [ **MRTK Figma Unity Bridge**]。 遵循下列步驟來完成 MR 功能工具，並返回您的 Unity 專案。 Unity 將會匯入 MRTK Figma Bridge 的套件。

### <a name="2-open-figma-bridge-window"></a>2. 開啟 Figma 橋接器視窗

匯入程式完成之後，您將能夠在 [ **> 工具組 > Figma 橋接器**] 下，找到 [Figma Bridge]。

<img src="images/FigmaToolkit/FigmaBridge_Menu.png" width="500px" alt="Figma Bridge - Menu"><br>

### <a name="3-generate-and-enter-your-figma-token"></a>3. 產生並輸入您的 Figma 權杖

在 Figma 網站上，按一下左上角的 [Figma] 功能表，開啟 [說明及帳戶 > 帳戶設定]。 在 [個人存取權杖] 區段中，產生新的個人存取權杖。

<img src="images/FigmaToolkit/FigmaToolkit_Token.png" width="500px" alt="Figma Bridge - Get Token"><br>

<img src="images/FigmaToolkit/FigmaBridge_Token.png" width="500px" alt="Figma Bridge - Enter Token"><br>


### <a name="4-enter-id-for-a-figma-document"></a>4. 輸入 Figma 檔的識別碼
每個 Figma 檔在 URL 中都有唯一的識別碼。 將此識別碼複製並貼到 Figma Bridge 中。

<img src="images/FigmaToolkit/FigmaToolkit_DocID.png" alt="Figma Bridge - Doc ID"><br>

按一下 [ **取得** 檔案] 以下載 Figma 檔。 您可以藉由輸入新的識別碼來下載其他 Figma 檔案。

按一下 [ **載入** 檔案] 以開啟 Figma 檔案。

<img src="images/FigmaToolkit/FigmaBridge_Files.png" width="500px" alt="Figma Bridge - Files"><br>

### <a name="5-build-a-page"></a>5. 建立頁面

Figma Bridge 將會顯示 Figma 檔案中的頁面清單。 檢查您想要在 Unity 中建立的頁面。 按一下 [ **建立頁面** ] 按鈕。

<img src="images/FigmaToolkit/FigmaBridge_Pages.png" width="500px" alt="Figma Bridge - Pages"><br>

<img src="images/FigmaToolkit/FigmaBridge_Result.png" alt="Figma Bridge - Result"><br>

### <a name="6-refresh-a-document-for-changes"></a>6. 重新整理檔以進行變更

您可以修改 web (上的 Figma 檔案，或使用桌面編輯器) 然後按一下 [重新整理 **]，以** 取得任何變更。 按一下 [ **組建頁面** ] 以使用更新建立。 如此一來，您就可以輕鬆地在 Figma 中反復查看您的設計，並在 Unity 中查看。



## <a name="see-also"></a>另請參閱
* [Figma 工具組](figma-toolkit.md)
* [游標](cursors.md)
* [手部光線](point-and-commit.md)
* [Button](button.md)
* [可互動的物件](interactable-object.md)
* [週框方塊和應用程式列](app-bar-and-bounding-box.md)
* [操作](direct-manipulation.md)
* [手部功能表](hand-menu.md)
* [近端功能表](near-menu.md)
* [物件集合](object-collection.md)
* [語音命令](voice-input.md)
* [鍵盤](keyboard.md)
* [工具提示](tooltip.md)
* [平板](slate.md)
* [滑桿](slider.md)
* [著色器](shader.md)
* [佈告板和常駐標籤](billboarding-and-tag-along.md)
* [顯示進度](progress.md)
* [表面磁性](surface-magnetism.md)
