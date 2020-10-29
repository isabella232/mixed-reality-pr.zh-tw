---
title: 應用程式內建購買功能
description: 混合現實應用程式支援應用程式內購買，但有一些工作可以進行設定。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: 應用程式內購買（hololens）
ms.openlocfilehash: 7174fe555322216b7e547055aaaf7879c01d8f23
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2020
ms.locfileid: "91679844"
---
# <a name="in-app-purchases"></a>應用程式內建購買功能

HoloLens 中支援應用程式內購買，但有一些工作可以進行設定。

為了充分利用應用程式購買功能，您必須：
* 建立 XAML [2d 視圖](../design/app-views.md) 以顯示為平板
* 切換至該位置以啟用放置，使其離開沉浸式視圖
* 呼叫 API： await [CurrentApp. RequestProductPurchaseAsync ( "DurableItemIAPName" ) ;](https://docs.microsoft.com/uwp/api/windows.applicationmodel.store.currentapp#Windows_ApplicationModel_Store_CurrentApp_RequestProductPurchaseAsync_System_String_)

此 API 會顯示顯示應用程式內購買名稱、描述和價格的 stock Windows OS 快顯視窗。 然後，使用者可以選擇購買選項。 完成此動作之後，應用程式將需要顯示 UI，讓使用者能夠切換回其 [沉浸式](../design/app-views.md)觀賞。

針對以桌面為基礎 Windows Mixed Reality 沉浸式耳機的應用程式，在呼叫 RequestProductPurchaseAsync API 之前，不需要手動切換至 XAML 視圖。
