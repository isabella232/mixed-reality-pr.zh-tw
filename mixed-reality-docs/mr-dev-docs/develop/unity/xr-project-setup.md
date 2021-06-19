---
title: 設定您的 XR 設定
description: 隨時掌握最新的 Unity XR 設定建議，以進行 HoloLens 應用程式開發。
author: hferrone
ms.author: v-hferrone
ms.date: 04/22/2021
ms.topic: article
keywords: mixedrealitytoolkit、mixedrealitytoolkit-unity、mixed reality 耳機、windows mixed reality 耳機、虛擬實境耳機、unity
ms.openlocfilehash: df7c5039c6cdcfa1e39dc96f0829611dd5209772
ms.sourcegitcommit: 6ade7e8ebab7003fc24f9e0b5fa81d091369622c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2021
ms.locfileid: "112394562"
---
# <a name="setting-up-your-xr-configuration"></a>設定您的 XR 設定

當您啟動新的 Unity 專案時，您有三個不同的選項可處理您的 XR 需求： 
* OpenXR 外掛程式
* Windows XR 外掛程式
* 舊版 XR 外掛程式

[!INCLUDE[](includes/xr/intro.md)]

## <a name="setting-up-your-project-with-mrtk"></a>使用 MRTK 設定您的專案

適用于 Unity 的 MRTK 會提供跨平臺輸入系統、基礎元件，以及空間互動的常見組建區塊。 MRTK 第 2 版主要用於加速開發適用於 Microsoft HoloLens、Windows Mixed Reality 沈浸式 (VR) 頭戴裝置和 OpenVR 平台的應用程式。 此專案的目標是減少進入障礙、建立混合實境應用程式，以及回饋伴著我們成長的社群。

> [!div class="nextstepaction"]
> [試用我們的 MRTK 教學課程](/windows/mixed-reality/develop/unity/tutorials/mr-learning-base-02?tabs=winxr)

如需詳細的功能詳細資料，請參閱 [MRTK 的檔](/windows/mixed-reality/mrtk-unity) 。

### <a name="using-mrtk-with-openxr-support"></a>搭配使用 MRTK 與 OpenXR 支援

MRTK-Unity 2.7 版可針對 Mixed Reality OpenXR 外掛程式提供更佳的支援。

如果您還沒有這麼做，請再次開啟 [Mixed Reality 功能工具](welcome-to-mr-feature-tool.md) 以安裝混合現實工具組。 **基礎** 套件中的 OpenXR 支援。

如需有關 [遷移至 OpenXR 的深入資訊](/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk#configuring-mrtk-for-the-xr-sdk-pipeline)，請參閱 MRTK 檔。

> [!NOTE]
> 從早于 **2.5.3** 的舊版 MRTK 進行升級時，請確定 [資產/MixedRealityToolkit] 中的下列程式程式碼位於 [ **資產/] 中。產生/link.xml** 檔案：
>
> ```xml
> <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>
> ```
>
> 如果您開始使用 MRTK 2.5.4 或更新版本，則預設會新增這一行。

## <a name="manual-setup-without-mrtk"></a>手動設定而不 MRTK

雖然 Microsoft 和社區建立了開放原始碼工具，例如 [混合現實工具組 (MRTK) ](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html) ，而這些工具會自動設定 WMR 的環境，但許多開發人員想要從頭開始建立他們的體驗。

[!INCLUDE[](includes/xr/manual-setup.md)]
