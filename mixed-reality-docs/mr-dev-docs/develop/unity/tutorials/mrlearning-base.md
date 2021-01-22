---
title: 教學課程概觀和目標
description: 完成此課程以了解如何在混合實境應用程式中實作 Azure 臉部辨識。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.localizationpriority: high
ms.openlocfilehash: b7e04a03f01beb1438f6f723c3938d05a60c9131
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/20/2021
ms.locfileid: "98581162"
---
# <a name="1-overview-and-objectives"></a><span data-ttu-id="2d5c2-104">1.概觀和目標</span><span class="sxs-lookup"><span data-stu-id="2d5c2-104">1. Overview and objectives</span></span>

## <a name="device-support"></a><span data-ttu-id="2d5c2-105">裝置支援</span><span class="sxs-lookup"><span data-stu-id="2d5c2-105">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="2d5c2-106"><strong>課程</strong></span><span class="sxs-lookup"><span data-stu-id="2d5c2-106"><strong>Course</strong></span></span></td>
        <td><span data-ttu-id="2d5c2-107"><a href="/hololens/hololens1-hardware"><strong>HoloLens (第 1 代)</strong></a></span><span class="sxs-lookup"><span data-stu-id="2d5c2-107"><a href="/hololens/hololens1-hardware"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="2d5c2-108"><a href="https://www.microsoft.com//hololens/hardware"><strong>HoloLens 2</strong></a></span><span class="sxs-lookup"><span data-stu-id="2d5c2-108"><a href="https://www.microsoft.com//hololens/hardware"><strong>HoloLens 2</strong></a></span></span></td>
        <td><span data-ttu-id="2d5c2-109"><a href="../../../discover/immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></span><span class="sxs-lookup"><span data-stu-id="2d5c2-109"><a href="../../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td></td>
        <td>❌</td>
        <td><span data-ttu-id="2d5c2-110">✔️</span><span class="sxs-lookup"><span data-stu-id="2d5c2-110">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="2d5c2-111">在您開始使用 Intune 之前</span><span class="sxs-lookup"><span data-stu-id="2d5c2-111">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="2d5c2-112">必要條件</span><span class="sxs-lookup"><span data-stu-id="2d5c2-112">Prerequisites</span></span>

* <span data-ttu-id="2d5c2-113">已[安裝正確工具](../../install-the-tools.md)的 Windows 10 電腦</span><span class="sxs-lookup"><span data-stu-id="2d5c2-113">A Windows 10 PC configured with the correct [tools installed](../../install-the-tools.md)</span></span>
* <span data-ttu-id="2d5c2-114">Windows 10 SDK 10.0.18362.0 或更新版本</span><span class="sxs-lookup"><span data-stu-id="2d5c2-114">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="2d5c2-115">基本的 C# 程式設計能力</span><span class="sxs-lookup"><span data-stu-id="2d5c2-115">Some basic C# programming ability</span></span>
* <span data-ttu-id="2d5c2-116">已[針對開發而設定](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)的 HoloLens 2 裝置</span><span class="sxs-lookup"><span data-stu-id="2d5c2-116">A HoloLens 2 device [configured for development](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="2d5c2-117"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a>，已安裝 Unity 2019.2，且已新增通用 Windows 平台組建支援模組</span><span class="sxs-lookup"><span data-stu-id="2d5c2-117"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.2.X installed and the Universal Windows Platform Build Support module added</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2d5c2-118">本教學課程系列的建議 Unity 版本是 Unity 2019.2. X。</span><span class="sxs-lookup"><span data-stu-id="2d5c2-118">The recommended Unity version for this tutorial series is Unity 2019.2.X.</span></span> <span data-ttu-id="2d5c2-119">這個版本能取代上述連結之必要條件中所述的任何 Unity 版本需求或建議。</span><span class="sxs-lookup"><span data-stu-id="2d5c2-119">This supersedes any Unity version requirements or recommendations stated in the prerequisites linked above.</span></span>

[<span data-ttu-id="2d5c2-120">下一課：2.初始化您的專案和第一個應用程式</span><span class="sxs-lookup"><span data-stu-id="2d5c2-120">Next lesson: 2. Initializing your project and first application</span></span>](./mr-learning-base-02.md)