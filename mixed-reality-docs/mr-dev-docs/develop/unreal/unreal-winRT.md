---
title: Unreal 中的 WinRT
description: 瞭解如何在 HoloLens 裝置的 Unreal 混合現實應用程式中撰寫和管理自訂 WinRT 功能。
author: hferrone
ms.author: jacksonf
ms.date: 12/9/2020
ms.topic: article
keywords: Unreal、Unreal Engine 4、UE4、HoloLens、HoloLens 2、串流、遠端處理、混合現實、開發、入門、功能、新專案、模擬器、檔、指南、功能、全像投影、遊戲開發、混合現實耳機、windows mixed reality 耳機、虛擬實境耳機、WinRT、DLL
ms.openlocfilehash: b00886908f51804650220b6dbb7b3bfe4184cf33b505e3bd278327d1669c5067
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2021
ms.locfileid: "115198378"
---
# <a name="winrt-in-unreal"></a>Unreal 中的 WinRT

在您的 HoloLens 開發過程中，您可能需要使用 WinRT 來撰寫功能。 例如，在 HoloLens 應用程式中開啟檔案對話方塊需要 winrt/Windows 中的 FileSavePicker。儲存體。選擇器 .h 標頭檔。 從4.26 版開始，Unreal 的組建系統支援 WinRT。

[!INCLUDE[](includes/tabs-winRT.md)]

## <a name="next-development-checkpoint"></a>下一個開發檢查點

依循我們配置的 Unreal 開發旅程，此時您會探索混合實境平台功能和 API。 您可以從這裡繼續前往任何 [主題](unreal-development-overview.md#3-advanced-features) ，或直接跳到在裝置或模擬器上部署您的應用程式。

> [!div class="nextstepaction"]
> [部署至裝置](unreal-deploying.md)

## <a name="see-also"></a>另請參閱

* [C + +/WinRT Api](/windows/uwp/cpp-and-winrt-apis/)
* [FileSavePicker 類別](/uwp/api/Windows.Storage.Pickers.FileSavePicker) 
* [Unreal 協力廠商程式庫](https://docs.unrealengine.com/Programming/BuildTools/UnrealBuildTool/ThirdPartyLibraries/index.html)