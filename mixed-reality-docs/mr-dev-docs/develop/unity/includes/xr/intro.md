---
ms.openlocfilehash: eaa2651a22fd5b2b601493845d507aeda6745f1a
ms.sourcegitcommit: e380d56f5504be4e4f069394a58cf0147eb33b66
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2021
ms.locfileid: "113603705"
---
# <a name="openxr"></a>[OpenXR](#tab/openxr)

Mixed Reality OpenXR 外掛程式是 Microsoft 對 **Unity 2020 LTS** 或更新版本的 **建議**。 在未來開發新功能時，它們只會包含在混合現實 OpenXR 外掛程式中。

Mixed Reality OpenXR 外掛程式完全支援 AR Foundation 4.0，提供 ARPlaneManager 和 ARRaycastManager 執行。 這可讓您撰寫 raycasting 程式碼一次，然後跨越 HoloLens 2 和 ARCore/ARKit 手機和平板電腦。

### <a name="prerequisites"></a>必要條件 

* [適用于 HoloLens 2 開發的](../../../install-the-tools.md?tabs=unity#installation-checklist)最新工具
* 最新的 Unity 2020.3 LTS：版本 2020.3.8 f1 或更新版本

### <a name="recommended-package-versions"></a>建議的套件版本

此頁面中的指示將會為您設定部署 HoloLens 2 或 Windows Mixed Reality 應用程式所需的核心 Unity OpenXR 套件：

* Unity OpenXR 外掛程式：1.2 版或更新版本
* Mixed Reality OpenXR 外掛程式：1.0.0 版或更新版本

如果您在專案中使用下列封裝，您將必須確定至少使用下列最小版本：

* MRTK： version 2.7.2 或更新版本
* AR Foundation： version 4.1.1 或更新版本
* 通用轉譯管線 (URP) ： version 10.5.1 或更新版本
* Azure 空間錨點：2.10 版或更新版本
* Azure 遠端轉譯： version 1.0.15 或更新版本

> [!NOTE]
> 如果您要在 Windows 電腦上建立 VR 應用程式，則不一定需要 Mixed Reality OpenXR 外掛程式。 但是，如果您要設定適用于 HP 重送 G2 控制器的輸入系結，或建立可在 HoloLens 2 和 VR 耳機上運作的應用程式，則您會想要安裝外掛程式。

# <a name="windows-xr"></a>[WindowsXR](#tab/windowsxr)

Microsoft 不建議針對 Unity 2020 中的任何新專案使用 Windows XR 外掛程式。  相反地，您應該使用 Mixed Reality OpenXR 外掛程式。

不過，如果您使用 Unity 2019，而且需要 AR Foundation 2.0 才能與 ARCore/ARKit 裝置相容，此外掛程式會啟用該支援。

> [!IMPORTANT]
> 在 Unity 2019 中使用此外掛程式與 Azure 空間錨點不相容。

# <a name="legacy-xr"></a>[傳統 XR](#tab/legacy)

如果您仍在 **Unity 2019** 或更早版本，Microsoft 建議使用 **舊版內建 XR 支援**。

雖然 Windows XR 外掛程式可在 unity 2019 上運作，但不建議使用，因為此外掛程式與 unity 2019 上的 Azure 空間錨點不相容。

如果您要開始新的專案，建議您 [改為安裝 Unity 2020](../../choosing-unity-version.md) ，並使用 Mixed Reality OpenXR 外掛程式。