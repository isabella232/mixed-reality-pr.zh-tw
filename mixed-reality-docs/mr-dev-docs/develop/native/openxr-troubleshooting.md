---
title: 針對 OpenXR 進行疑難排解
description: 針對 OpenXR 應用程式中的問題進行疑難排解。
author: thetuvix
ms.author: alexturn
ms.date: 2/28/2020
ms.topic: article
keywords: OpenXR、Khronos、BasicXRApp、DirectX、原生、原生應用程式、自訂引擎、中介軟體、疑難排解
ms.openlocfilehash: 174c115b86e62d5c52051a7363a59e383e503a95
ms.sourcegitcommit: c199872c11adae7de24929ed043ea90dea087b3e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/28/2020
ms.locfileid: "92903094"
---
# <a name="openxr-troubleshooting"></a><span data-ttu-id="0f16f-104">針對 OpenXR 進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="0f16f-104">OpenXR troubleshooting</span></span>

<span data-ttu-id="0f16f-105">以下是使用 Windows Mixed Reality OpenXR 執行時間開發 OpenXR 應用程式時的一些疑難排解秘訣。</span><span class="sxs-lookup"><span data-stu-id="0f16f-105">Here are some troubleshooting tips when developing an OpenXR app using the Windows Mixed Reality OpenXR Runtime.</span></span>  <span data-ttu-id="0f16f-106">如果您有任何其他有關 <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">OpenXR 1.0 規格</a>的問題，請造訪 <a href="https://community.khronos.org/c/openxr" target="_blank">Khronos OpenXR 論壇</a> 或 <a href="https://khr.io/slack" target="_blank">#openxr 頻道的時差</a>。</span><span class="sxs-lookup"><span data-stu-id="0f16f-106">If you have any other questions about the <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">OpenXR 1.0 specification</a>, please visit the <a href="https://community.khronos.org/c/openxr" target="_blank">Khronos OpenXR Forums</a> or <a href="https://khr.io/slack" target="_blank">Slack #openxr channel</a>.</span></span>

>[!NOTE]
><span data-ttu-id="0f16f-107">目前 Windows Mixed Reality OpenXR 執行時間與 x86 應用程式有已知的問題。</span><span class="sxs-lookup"><span data-stu-id="0f16f-107">There are known issues in the current Windows Mixed Reality OpenXR runtime with x86 apps.</span></span>  <span data-ttu-id="0f16f-108">您現在應該建立 x64 的桌面 OpenXR 應用程式。</span><span class="sxs-lookup"><span data-stu-id="0f16f-108">You should build desktop OpenXR apps for x64 at the moment.</span></span>

### <a name="openxr-app-not-starting-windows-mixed-reality"></a><span data-ttu-id="0f16f-109">OpenXR 應用程式未啟動 Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="0f16f-109">OpenXR app not starting Windows Mixed Reality</span></span>

<span data-ttu-id="0f16f-110">如果您的 OpenXR 應用程式未在執行時啟動 Windows Mixed Reality，Windows Mixed Reality OpenXR 執行時間可能不會設定為使用中執行時間。</span><span class="sxs-lookup"><span data-stu-id="0f16f-110">If your OpenXR app is not starting Windows Mixed Reality when you run it, the Windows Mixed Reality OpenXR Runtime may not be set as the active runtime.</span></span>  <span data-ttu-id="0f16f-111">請務必遵循 [Windows Mixed Reality 耳機開始使用 OpenXR](openxr-getting-started.md#getting-started-with-openxr-for-windows-mixed-reality-headsets) 的指示，使執行時間成為使用中狀態。</span><span class="sxs-lookup"><span data-stu-id="0f16f-111">Be sure to follow the instructions for [getting started with OpenXR for Windows Mixed Reality headsets](openxr-getting-started.md#getting-started-with-openxr-for-windows-mixed-reality-headsets) to make the runtime active.</span></span>

<span data-ttu-id="0f16f-112">您也可以執行 [適用于 Windows Mixed Reality 的 OpenXR 開發人員工具](openxr-getting-started.md#getting-the-openxr-developer-tools-for-windows-mixed-reality) ，以取得有關系統上 Windows Mixed Reality OpenXR 執行時間狀態的額外疑難排解協助。</span><span class="sxs-lookup"><span data-stu-id="0f16f-112">You can also run the [OpenXR Developer Tools for Windows Mixed Reality](openxr-getting-started.md#getting-the-openxr-developer-tools-for-windows-mixed-reality) for additional troubleshooting help around the state of the Windows Mixed Reality OpenXR Runtime on your system.</span></span>