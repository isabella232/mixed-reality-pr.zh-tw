---
title: 適用于 Unreal 的 MRTK 簡介
description: 開始使用適用于 Unreal 的混合現實工具組，必須提供新的混合現實開發人員。
author: hferrone
ms.author: v-hferrone
ms.date: 01/08/2021
ms.topic: article
ms.localizationpriority: high
keywords: Windows Mixed Reality, 測試, 混合實境工具組, MRTK 第 2 版, MRTK, 工具, SDK, HoloLens, HoloLens 2, 混合實境頭戴式裝置, windows 混合實境頭戴式裝置, 虛擬實境頭戴式裝置, 跨平台
ms.openlocfilehash: 06eacac245c80f16ab48dbda4b5aca740ffdfd66a0266beafac5e46b39a9d109
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2021
ms.locfileid: "115221828"
---
# <a name="introducing-mrtk-for-unreal"></a>適用于 Unreal 的 MRTK 簡介

![MRTK 橫幅影像](../../design/images/MRTK_UX_Hero.png)

## <a name="what-is-mixed-reality-toolkit-mrtk"></a>混合實境工具組 (MRTK) 是什麼？

MRTK 是一項令人驚奇的開放原始碼工具組，自 HoloLens 首次發行之後就已經存在。 沒有開發人員社群的努力，就不會達到今天的境界。 

適用于 Unreal (MRTK-Unreal) 的混合現實工具組是一組元件（以外掛程式、範例和檔的形式），其設計目的是要協助使用 Unreal 引擎開發混合現實應用程式。 目前，此工具組包含：
* [適用于 Unreal 的 UX 工具](https://github.com/microsoft/MixedReality-UXTools-Unreal)，可提供程式碼、藍圖和範例，以針對 Hololens 2 應用程式執行 UX 功能。
* [適用于 Unreal 的圖形工具](https://github.com/microsoft/MixedReality-GraphicsTools-Unreal)，可協助改善混合現實應用程式的視覺精確度，同時維持在效能預算內。

請參閱[MRTK 的檔，瞭解 GitHub 的相關檔](https://microsoft.github.io/MixedReality-UXTools-Unreal/README.html)，以及如何開始使用[UX 工具](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/Installation.html)或[圖形工具](https://github.com/microsoft/MixedReality-GraphicsTools-Unreal/blob/main/Docs/Installation.md)安裝指南。

### <a name="modular"></a>模組化

我們以模組化的方式建立了 MRTK Unreal，因此您不需要將工具組的每個專案都帶到您的專案中。 您可以選擇並選擇所需的外掛程式，並在每次看到合適的時候新增或移除它們。 這種方法可讓您的專案大小保持較小，而且更容易管理。  

### <a name="performant"></a>效能

使用行動平臺時，我們已將效能考慮到 MRTK Unreal。 這是非常重要的，我們想要確保工具不會與您合作。

## <a name="project-setup"></a>專案設定

> [!div class="nextstepaction"]
> [下載 Unreal Engine 和 MRTK](unreal-project-setup.md)

## <a name="see-also"></a>另請參閱

* [安裝工具](../install-the-tools.md)
* [使用 MRTK for Unreal 進行開發](unreal-development-overview.md)
* [UX 工具- (GitHub) 的安裝指南](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/Installation.html)
* [UX 工具-檔首頁 (GitHub) ](https://microsoft.github.io/MixedReality-UXTools-Unreal/README.html)
* [圖形工具- (GitHub) 的安裝指南](https://github.com/microsoft/MixedReality-GraphicsTools-Unreal/blob/main/Docs/Installation.md)
* [圖形工具-檔首頁 (GitHub) ](https://github.com/microsoft/MixedReality-GraphicsTools-Unreal/)