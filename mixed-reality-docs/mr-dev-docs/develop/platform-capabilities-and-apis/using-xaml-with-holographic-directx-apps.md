---
title: 使用全像攝影 DirectX 應用程式中的 XAML
description: 說明在您的 DirectX 應用程式中切換 2D XAML 視圖與沉浸式視圖之間的影響，以及如何有效率地使用 XAML 視圖和沉浸式視圖。
author: mikeriches
ms.author: mriches
ms.date: 08/04/2020
ms.topic: article
keywords: windows mixed reality、UWP、應用程式視圖管理、xaml、鍵盤、逐步解說、DirectX
ms.openlocfilehash: b062efadca9ccfe2e2caeb054f662becc0807b50
ms.sourcegitcommit: c41372e0c6ca265f599bff309390982642d628b8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/15/2020
ms.locfileid: "97530282"
---
# <a name="using-xaml-with-holographic-directx-apps"></a>使用全像攝影 DirectX 應用程式中的 XAML

> [!NOTE]
> 本文與舊版 WinRT 原生 Api 相關。  針對新的原生應用程式專案，建議使用 **[OPENXR API](../native/openxr-getting-started.md)**。

本主題說明在 DirectX 應用程式中切換 [2D XAML 視圖與沉浸式視圖](../../design/app-views.md) 之間的影響，以及如何有效率地使用 XAML 視圖和沉浸式視圖。

## <a name="xaml-view-switching-overview"></a>XAML 視圖切換總覽

在 HoloLens 上，可在稍後顯示 2D XAML 視圖的沉浸式應用程式，必須先初始化該 XAML 視圖，並立即從該處切換到沉浸式視圖。 XAML 會先載入，您的應用程式才能進行任何動作，這會增加您的啟動時間。 XAML 會在應用程式進程維持在背景時，繼續佔用記憶體空間。 啟動延遲和記憶體使用量的數量，取決於您的應用程式在切換至原生視圖之前的 XAML 用途。 如果您在 XAML 啟動程式碼中的第一次沒有執行任何動作，但開始您的沉浸式觀賞，則影回應該會很小。 此外，因為您的全像是直接在沉浸式的觀賞中進行，所以您會在該轉譯上避免任何與 XAML 相關的限制。

CPU 和 GPU 的記憶體使用量計數。 Direct3D 11 可以交換虛擬圖形記憶體，但它可能無法交換部分或所有的 XAML GPU 資源，而且可能會有明顯的效能衝擊。 無論何種方式，您都不需要載入任何 XAML 功能，也不需要載入更多應用程式的空間，並提供更好的體驗。

## <a name="xaml-view-switching-workflow"></a>XAML 視圖切換工作流程

從 XAML 直接進入沉浸式模式的應用程式工作流程，如下所示：
* 應用程式會在 2D XAML 視圖中啟動。
* 應用程式的 XAML 啟動順序會偵測目前的系統是否支援全像轉譯：
* 如果是，應用程式會建立沉浸式視圖，並立即將它帶到前景。 在 Windows Mixed Reality 裝置上不需要的任何動作都會略過 XAML 載入，包括 XAML 視圖中的任何轉譯類別和資產載入。 如果應用程式使用 XAML 進行鍵盤輸入，則仍應建立該輸入頁面。
* 如果沒有，則 XAML view 可以正常地繼續使用商務。

## <a name="tip-for-rendering-graphics-across-both-views"></a>跨兩個視圖呈現圖形的秘訣

如果您的應用程式需要針對 Windows Mixed Reality 中的 XAML 視圖在 DirectX 中執行某種程度的轉譯，最好的做法是建立一個可同時使用兩個視圖的轉譯器。 轉譯器應該是一個可從這兩個視圖存取的實例，而且應該在2D 和全像攝影轉譯之間切換。 如此一來，GPU 資產只會載入一次，可減少載入時間、記憶體影響，以及切換視圖時交換的資源數量。
