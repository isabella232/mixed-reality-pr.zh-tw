---
title: 適用於 Unity 的 MRTK 簡介
description: 適用於想要使用 MRTK 的新開發人員
author: cre8ivepark
ms.author: dongpark
ms.date: 05/15/2019
ms.topic: article
ms.localizationpriority: high
keywords: Windows Mixed Reality, 測試, 混合實境工具組, MRTK 第 2 版, MRTK, 工具, SDK, HoloLens, HoloLens 2, 混合實境頭戴式裝置, windows 混合實境頭戴式裝置, 虛擬實境頭戴式裝置, 跨平台
ms.openlocfilehash: 6887d79d4a0737f3ed0f63af5686699fc7a1a2b6
ms.sourcegitcommit: 2bf79eef6a9b845494484f458443ef4f89d7efc0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/17/2020
ms.locfileid: "97613442"
---
# <a name="introducing-mrtk-for-unity"></a>適用於 Unity 的 MRTK 簡介

![MRTK](../../design/images/MRTK_UX_Hero.png)

## <a name="what-is-mixed-reality-toolkit-mrtk"></a>混合實境工具組 (MRTK) 是什麼？
MRTK 是一項令人驚奇的開放原始碼工具組，自 HoloLens 首次發行之後就已經存在。 沒有開發人員社群的努力，就不會達到今天的境界。 過去三年來，我們聽取了開發人員社群的意見反應，將最主要的考量納入，建置了 MRTK v2。  

適用於 Unity 的 MRTK 是混合實境應用程式的開放原始碼跨平台開發套件。 此工具組提供跨平台輸入系統、基礎元件，以及空間互動的常見基本要素。 MRTK 第 2 版主要用於加速開發適用於 Microsoft HoloLens、Windows Mixed Reality 沈浸式 (VR) 頭戴裝置和 OpenVR 平台的應用程式。 此專案的目標是減少進入障礙、建立混合實境應用程式，以及回饋伴著我們成長的社群。

<br>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4IkCG]

請參閱 [GitHub 上的 MRTK 文件](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)，並從[安裝指南](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html)來開始著手。


## <a name="new-with-mrtk-v2"></a>MRTK v2 的新功能
我們想要強調我們對這些平台工具的承諾。  事實上，我們使用 MRTK 第 2 版來開發收件匣體驗，例如全新安裝體驗 (OOBE) 和我們的混合實境提示應用程式。 您也可以預期新的 HoloLens 2 功能會先透過 MRTK 公開，因為我們認為這是在我們的平台上進行開發的最佳方式。 

### <a name="modular"></a>模組化
我們以模組化的方式建置，因此您不需要個別將工具組的部分納入您的專案中。  這其實有幾個優點。  它會讓您的專案大小變小，讓您更容易管理。  此外，由於它是以可編寫指令碼的物件建置，而且是介面驅動的，因此您也可以用自己的物件取代其中所包含的元件，以支援其他服務、系統和平台。

### <a name="cross-platform"></a>跨平台
說到其他平台，它有跨平台支援。  雖然這並不代表每個平台都會獲得支援，但是我們確定當您將建置目標切換至其他平台時，不會有任何工具組程式碼中斷。  模組化設計的健全性和擴充性，會讓應用程式有能力支援多個平台，例如 ARCore、ARKit 和 OpenVR。

### <a name="performant"></a>效能
使用行動平台時，我們會考慮到效能。  這是非常重要的，我們想要確保工具不會與您作對。

## <a name="see-also"></a>另請參閱
* [安裝工具](../install-the-tools.md)
* [MRTK - 安裝指南 (GitHub)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html)
* [MRTK - 文件首頁 (GitHub)](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
* [從 HoloToolkit/MRTK 移植到 MRTK 第 2 版 (GitHub)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/HTKToMRTKPortingGuide.html)
