---
title: Unreal 中的 WinRT
description: 瞭解如何在適用于 HoloLens 裝置的 Unreal 混合現實應用程式中撰寫和管理自訂 WinRT 功能。
author: hferrone
ms.author: jacksonf
ms.date: 12/9/2020
ms.topic: article
keywords: Unreal、Unreal Engine 4、UE4、HoloLens、HoloLens 2、串流、遠端處理、混合現實、開發、入門、功能、新專案、模擬器、檔、指南、功能、全像投影、遊戲開發、混合現實耳機、windows 混合現實耳機、虛擬實境耳機、WinRT、DLL
ms.openlocfilehash: f32b5b3ddbee2e24e61d08b0a1b887b7b06e6da4
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/20/2021
ms.locfileid: "98580417"
---
# <a name="winrt-in-unreal"></a><span data-ttu-id="c123b-104">Unreal 中的 WinRT</span><span class="sxs-lookup"><span data-stu-id="c123b-104">WinRT in Unreal</span></span>

<span data-ttu-id="c123b-105">在您的 HoloLens 開發過程中，您可能需要使用 WinRT 來撰寫功能。</span><span class="sxs-lookup"><span data-stu-id="c123b-105">Over the course of your HoloLens development you may need to write a feature using WinRT.</span></span> <span data-ttu-id="c123b-106">例如，在 HoloLens 應用程式中開啟檔案對話方塊，需要 FileSavePicker 在 winrt 標頭檔中。</span><span class="sxs-lookup"><span data-stu-id="c123b-106">For example, opening a file dialogue in a HoloLens application would need the FileSavePicker in winrt/Windows.Storage.Pickers.h header file.</span></span> <span data-ttu-id="c123b-107">從4.26 版開始，Unreal 的組建系統支援 WinRT。</span><span class="sxs-lookup"><span data-stu-id="c123b-107">WinRT is supported in Unreal's build system from version 4.26 onwards.</span></span>

[!INCLUDE[](includes/tabs-winRT.md)]

## <a name="next-development-checkpoint"></a><span data-ttu-id="c123b-108">下一個開發檢查點</span><span class="sxs-lookup"><span data-stu-id="c123b-108">Next Development Checkpoint</span></span>

<span data-ttu-id="c123b-109">依循我們配置的 Unreal 開發旅程，此時您會探索混合實境平台功能和 API。</span><span class="sxs-lookup"><span data-stu-id="c123b-109">If you're following the Unreal development journey we've laid out, you're in the midst of exploring the Mixed Reality platform capabilities and APIs.</span></span> <span data-ttu-id="c123b-110">您可以從這裡繼續前往任何 [主題](unreal-development-overview.md#3-advanced-features) ，或直接跳到在裝置或模擬器上部署您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="c123b-110">From here, you can continue to any [topic](unreal-development-overview.md#3-advanced-features) or jump directly to deploying your app on a device or emulator.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="c123b-111">部署至裝置</span><span class="sxs-lookup"><span data-stu-id="c123b-111">Deploying to device</span></span>](unreal-deploying.md)

## <a name="see-also"></a><span data-ttu-id="c123b-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c123b-112">See also</span></span>

* [<span data-ttu-id="c123b-113">C + +/WinRT Api</span><span class="sxs-lookup"><span data-stu-id="c123b-113">C++/WinRT APIs</span></span>](/windows/uwp/cpp-and-winrt-apis/)
* [<span data-ttu-id="c123b-114">FileSavePicker 類別</span><span class="sxs-lookup"><span data-stu-id="c123b-114">FileSavePicker class</span></span>](/uwp/api/Windows.Storage.Pickers.FileSavePicker) 
* [<span data-ttu-id="c123b-115">Unreal 協力廠商程式庫</span><span class="sxs-lookup"><span data-stu-id="c123b-115">Unreal Third-Party Libraries</span></span>](https://docs.unrealengine.com/Programming/BuildTools/UnrealBuildTool/ThirdPartyLibraries/index.html)