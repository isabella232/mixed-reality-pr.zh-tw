---
title: 針對 OpenXR 進行疑難排解
description: 尋找 Windows Mixed Reality OpenXR 應用程式中常見疑難排解問題的資源和解答。
author: thetuvix
ms.author: alexturn
ms.date: 2/28/2020
ms.topic: article
keywords: OpenXR、Khronos、BasicXRApp、DirectX、原生、原生應用程式、自訂引擎、中介軟體、疑難排解
ms.openlocfilehash: 6e1696bca4f31f70af10c32087400ed56efa3c11
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2021
ms.locfileid: "98006727"
---
# <a name="openxr-troubleshooting"></a><span data-ttu-id="b8752-104">針對 OpenXR 進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="b8752-104">OpenXR troubleshooting</span></span>

<span data-ttu-id="b8752-105">以下是使用 Windows Mixed Reality OpenXR 執行時間開發 OpenXR 應用程式時的一些疑難排解秘訣。</span><span class="sxs-lookup"><span data-stu-id="b8752-105">Here are some troubleshooting tips when developing an OpenXR app using the Windows Mixed Reality OpenXR Runtime.</span></span>  <span data-ttu-id="b8752-106">如果您有任何其他有關 <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">OpenXR 1.0 規格</a>的問題，請造訪 <a href="https://community.khronos.org/c/openxr" target="_blank">Khronos OpenXR 論壇</a> 或 <a href="https://khr.io/slack" target="_blank">#openxr 頻道的時差</a>。</span><span class="sxs-lookup"><span data-stu-id="b8752-106">If you have any other questions about the <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">OpenXR 1.0 specification</a>, visit the <a href="https://community.khronos.org/c/openxr" target="_blank">Khronos OpenXR Forums</a> or <a href="https://khr.io/slack" target="_blank">Slack #openxr channel</a>.</span></span>

>[!NOTE]
><span data-ttu-id="b8752-107">目前 Windows Mixed Reality OpenXR 執行時間與 x86 應用程式有已知的問題。</span><span class="sxs-lookup"><span data-stu-id="b8752-107">There are known issues in the current Windows Mixed Reality OpenXR runtime with x86 apps.</span></span>  <span data-ttu-id="b8752-108">您現在應該建立 x64 的桌面 OpenXR 應用程式。</span><span class="sxs-lookup"><span data-stu-id="b8752-108">You should build desktop OpenXR apps for x64 at the moment.</span></span>

### <a name="openxr-app-not-starting-windows-mixed-reality"></a><span data-ttu-id="b8752-109">OpenXR 應用程式未啟動 Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="b8752-109">OpenXR app not starting Windows Mixed Reality</span></span>

<span data-ttu-id="b8752-110">如果您的 OpenXR 應用程式未啟動 Windows Mixed Reality 當您執行它時，Windows Mixed Reality OpenXR 執行時間可能不會設定為使用中執行時間。</span><span class="sxs-lookup"><span data-stu-id="b8752-110">If your OpenXR app isn't starting Windows Mixed Reality when you run it, the Windows Mixed Reality OpenXR Runtime may not be set as the active runtime.</span></span> <span data-ttu-id="b8752-111">遵循 [Windows Mixed Reality 耳機的入門](openxr-getting-started.md#getting-started-with-openxr-for-windows-mixed-reality-headsets) 指示來修正問題。</span><span class="sxs-lookup"><span data-stu-id="b8752-111">Follow the instructions for [getting started with OpenXR for Windows Mixed Reality headsets](openxr-getting-started.md#getting-started-with-openxr-for-windows-mixed-reality-headsets) to fix the issue.</span></span>

<span data-ttu-id="b8752-112">您也可以執行 [適用于 Windows Mixed Reality 的 OpenXR 開發人員工具](openxr-getting-started.md#getting-the-openxr-developer-tools-for-windows-mixed-reality) ，以取得系統 Windows Mixed Reality OpenXR 執行時間狀態的疑難排解協助。</span><span class="sxs-lookup"><span data-stu-id="b8752-112">You can also run the [OpenXR Developer Tools for Windows Mixed Reality](openxr-getting-started.md#getting-the-openxr-developer-tools-for-windows-mixed-reality) to get troubleshooting help on the state of your systems Windows Mixed Reality OpenXR Runtime.</span></span>