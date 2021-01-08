---
title: 原生開發概觀
description: 瞭解如何直接使用 Windows Mixed Reality Api 來建立以 DirectX 為基礎的混合現實引擎。
author: thetuvix
ms.author: alexturn
ms.date: 08/04/2020
ms.topic: article
keywords: DirectX，全像攝影轉譯、原生、原生應用程式、WinRT、WinRT 應用程式、平臺 Api、自訂引擎、中介軟體、混合現實耳機、windows mixed reality 耳機、虛擬實境耳機
ms.openlocfilehash: 764cbe0a37501cc176e9bb05a9a7771b03666f0c
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2021
ms.locfileid: "98006848"
---
# <a name="native-development-overview"></a>原生開發概觀

![原生橫幅標誌](../images/native_logo_banner.png)

[Unity](../unity/unity-development-overview.md)或[Unreal](../unreal/unreal-development-overview.md)這類3d 引擎不是唯一開放給您的混合現實開發途徑。 您也可以使用 Windows Mixed Reality Api 搭配 DirectX 11 或 DirectX 12 來建立混合的現實應用程式。 藉由進入平臺來源，您基本上就是建立自己的中介軟體或架構。 

> [!IMPORTANT]
> 如果您有想要維護的現有 WinRT 專案，請前往我們的主要 [winrt 檔](creating-a-holographic-directx-project.md)。 

## <a name="development-checkpoints"></a>開發檢查點

使用下列檢查點，將您的 Unity 遊戲和應用程式融入混合實境的世界中。

### <a name="1-getting-started"></a>1.開始使用

Windows Mixed Reality 支援 [兩種類型的應用程式](../../design/app-views.md)：
* UWP 或 Win32 **混合現實應用程式，這些應用程式** 會使用 [HolographicSpace API](getting-a-holographicspace.md)或 [OpenXR api](openxr.md)來呈現可填滿耳機顯示器的 [沉浸式視圖](../../design/app-views.md)
* **2d 應用程式** (UWP) ，其使用 DIRECTX、XAML 或其他架構在 Windows Mixed Reality 首頁的平板上轉譯 [2d 視圖](../../design/app-views.md#2d-views)

[2d 視圖和沉浸式視圖](../../design/app-views.md)的 DirectX 開發之間的差異，主要是要考慮全像攝影轉譯和空間輸入。 您的 UWP 應用程式 [IFrameworkView](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.core.iframeworkview.aspx) 或您的 Win32 應用程式的 HWND 是必要的，而且維持在相同的狀態。 適用于您應用程式的 WinRT Api 也是如此。 但是，您必須使用這些 Api 的不同子集來利用全像全像的功能。 例如，「全像」應用程式的系統會管理 swapchain 和框架，以啟用姿勢預測的框架迴圈。

[!INCLUDE[](../includes/native-getting-started.md)]

### <a name="2-core-building-blocks"></a>2.核心基本要素

Windows Mixed Reality 的應用程式會使用下列 Api 來建立 HoloLens 和其他沉浸式耳機的 [混合現實](../../discover/mixed-reality.md) 體驗：

|  功能  |  功能  |
| --- | --- |
| [目光](../../design/gaze-and-commit.md) | 讓使用者藉由注視全像投影而將其定為目標 |
| [手勢](../../design/gaze-and-commit.md#composite-gestures) | 將空間動作新增至您的應用程式 |
| [全像攝影的呈現](../platform-capabilities-and-apis/rendering.md) | 在您的使用者附近的確切位置繪製全像影像 |
| [移動控制器](../../design/motion-controllers.md) | 讓您的使用者在您的混合現實環境中採取行動 |
| [空間對應](../../design/spatial-mapping.md) | 透過虛擬網格重疊對應您的實體空間，以標示環境的界限 |
| [語音](../../design/voice-input.md) | 擷取使用者說出的關鍵字、片語和指令 |
 
> [!NOTE]
> 您可以在 OpenXR [藍圖](openxr.md#roadmap) 檔中找到即將推出和開發中的核心功能。

### <a name="3-deploying-and-testing"></a>3. 部署和測試

您可以在 HoloLens 2 上使用 OpenXR 或 Windows Mixed Reality 沉浸式耳機開發桌上型電腦。  如果您沒有耳機的存取權，您可以改用 [HoloLens 2 模擬器](../platform-capabilities-and-apis/using-the-hololens-emulator.md) 或 [Windows Mixed Reality](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md) 模擬器。

## <a name="whats-next"></a>接下來要做什麼？

開發人員的工作無止境，在學習新工具或 SDK 方面尤其如此。 下列各節會將您帶到您已完成的初學者層級內容以外的區域。 這些主題和資源不會以任何順序排列，因此您可以隨時跳到探索！

### <a name="additional-resources"></a>其他資源

如果您想要 OpenXR 遊戲的等級，請參閱下列連結：

* [OpenXR 最佳做法](openxr-best-practices.md)
* [OpenXR 效能](openxr-performance.md)
* [對 OpenXR 進行疑難排解](openxr-troubleshooting.md)

## <a name="see-also"></a>請參閱
* [應用程式模型](../../design/app-model.md)
* [應用程式檢視](../../design/app-views.md)
