---
ms.openlocfilehash: d39f6032eaf9a59ca52a6e7ae9b8e4d227175738
ms.sourcegitcommit: 72970dbe6674e28c250f741e50a44a238bb162d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2021
ms.locfileid: "112906937"
---
# <a name="openxr"></a>[OpenXR](#tab/openxr)

Mixed Reality OpenXR 外掛程式是 Microsoft 對 Unity 2020 LTS 或更新版本的 **建議** 。 在未來開發新功能時，它們只會包含在混合現實 OpenXR 外掛程式中。

Mixed Reality OpenXR 外掛程式完全支援 AR Foundation 4.0，提供 ARPlaneManager 和 ARRaycastManager 執行。 這可讓您撰寫 raycasting 程式碼一次，然後跨越 HoloLens 2 和 ARCore/ARKit 手機和平板電腦。

### <a name="prerequisites"></a>必要條件 

* [適用于 HoloLens 2 開發的](../../../install-the-tools.md?tabs=unity#installation-checklist)最新工具
* 最新的 Unity 2020.3 LTS， (我們建議 2020.3.8 f1 或更新版本) 

### <a name="minimum-versions"></a>最小版本

此頁面中的指示將會為您設定下列最新且最棒的 Unity 和 OpenXR 需求：

* 最新的 Unity OpenXR 外掛程式， (建議1.2 或更新版本) 
* 最新的混合現實 OpenXR 外掛程式， (建議1.0.0 版或更新版本) 
* **(選擇性)** 最新的 MRTK， (建議2.7 版或更新版本) 
* **(選擇性)** 最新的通用轉譯管線套件， (我們建議10.5.1 版或更新版本) 

<!-- ![Screenshot of the open xr unity basic sample running on a HoloLens](../../images/openxr-example.png) -->

> [!NOTE]
> 如果您是在 Windows 電腦上建立 VR 應用程式，則不一定需要混合現實 OpenXR 外掛程式。 但是，如果您要自訂適用于 HP 重設系的控制器對應，或建立可在 HoloLens 2 和 VR 耳機上運作的應用程式，則您會想要安裝外掛程式。

# <a name="windows-xr"></a>[Windows XR](#tab/windowsxr)

Microsoft 不建議針對 Unity 2020 中的任何新專案使用 Windows XR 外掛程式。

不過，如果您使用 Unity 2019，而且需要 AR Foundation 2.0 才能與 ARCore/ARKit 裝置相容，此外掛程式會啟用該支援。

> [!IMPORTANT]
> 在 Unity 2019 中使用此外掛程式不支援 Azure 空間錨點。 

# <a name="legacy-xr"></a>[傳統 XR](#tab/legacy)

如果您仍在 Unity 2019 或更早版本，Microsoft 建議使用舊版內建 XR 支援。 雖然 Windows XR 外掛程式可在 Unity 2019 上運作，但不建議使用，因為不支援 Azure 空間錨點。