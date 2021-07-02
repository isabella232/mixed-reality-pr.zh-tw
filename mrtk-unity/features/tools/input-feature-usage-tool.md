---
title: 輸入功能使用方式工具
description: MRTK 中的檔 InputFeatureUsage 工具
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: 413d2a3105294411f9c08f4a2add9365389ea783
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176125"
---
# <a name="input-feature-usage-tool"></a><span data-ttu-id="13175-104">輸入功能使用方式工具</span><span class="sxs-lookup"><span data-stu-id="13175-104">Input feature usage tool</span></span>

<span data-ttu-id="13175-105">InputFeatureUsage 工具是裝置上的執行時間 (或編輯器) 工具，可讓開發人員快速判斷所偵測到之輸入來源的可用 Unity InputFeatureUsages， (例如：移動控制器或明確的) 。</span><span class="sxs-lookup"><span data-stu-id="13175-105">The InputFeatureUsage tool is a runtime (on device or in the editor) tool that enables developers to quickly determine the available Unity InputFeatureUsages for a detected input source (ex: motion controller or articulated hand).</span></span>

> [!NOTE]
> <span data-ttu-id="13175-106">此場景僅適用于 Unity 2019.3 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="13175-106">This scene only works on Unity 2019.3 or later.</span></span>

<span data-ttu-id="13175-107">當您針對新的硬體控制器開發支援時，此工具非常有用。</span><span class="sxs-lookup"><span data-stu-id="13175-107">This tool is very useful when developing support for a new hardware controller.</span></span> <span data-ttu-id="13175-108">它也可以協助確認現有控制器的支援類別中可疑的控制項對應問題。</span><span class="sxs-lookup"><span data-stu-id="13175-108">It can also help to confirm a suspected control mapping issue in the support class for an existing controller.</span></span>

![InputFeatureUsage 工具](../images/controller-mapping-tool/InputFeatureUsages.png)

## <a name="using-the-inputfeatureusage-tool"></a><span data-ttu-id="13175-110">使用 InputFeatureUsage 工具</span><span class="sxs-lookup"><span data-stu-id="13175-110">Using the InputFeatureUsage tool</span></span>

<span data-ttu-id="13175-111">若要開始使用 InputFeatureUsage 工具，請流覽至 [ **MRTK]/[工具]/[RuntimeTools]/[工具]/[InputFeatureUsageTool** ]，然後開啟 **InputFeatureUsageTool** 場景。</span><span class="sxs-lookup"><span data-stu-id="13175-111">To get started with the InputFeatureUsage tool, navigate to **MRTK/Tools/RuntimeTools/Tools/InputFeatureUsageTool** and open the **InputFeatureUsageTool** scene.</span></span> <span data-ttu-id="13175-112">載入場景之後，您可以在編輯器中使用播放模式來執行專案，或在裝置上建立並執行專案。</span><span class="sxs-lookup"><span data-stu-id="13175-112">Once the scene has been loaded, the project can either be run in the editor, using play mode, or built and run on a device.</span></span>

<span data-ttu-id="13175-113">檢查控制器的 Unity 對應：</span><span class="sxs-lookup"><span data-stu-id="13175-113">To examine Unity's mappings for a controller:</span></span>

- <span data-ttu-id="13175-114">連線控制器</span><span class="sxs-lookup"><span data-stu-id="13175-114">Connect the controller</span></span>
- <span data-ttu-id="13175-115">按下每個按鈕並移動每個軸</span><span class="sxs-lookup"><span data-stu-id="13175-115">Press each button and move each axis</span></span>
- <span data-ttu-id="13175-116">請注意顯示中的功能使用方式</span><span class="sxs-lookup"><span data-stu-id="13175-116">Note the feature usages in the display</span></span>
- <span data-ttu-id="13175-117">更新控制器的輸入系統資料提供者中的控制項對應</span><span class="sxs-lookup"><span data-stu-id="13175-117">Update the control mappings in the input system data provider for the controller</span></span>

> [!NOTE]
> <span data-ttu-id="13175-118">InputFeatureUsage 工具不會利用 Microsoft Mixed Reality 工具組元件。</span><span class="sxs-lookup"><span data-stu-id="13175-118">The InputFeatureUsage tool does not make use of Microsoft Mixed Reality Toolkit components.</span></span> <span data-ttu-id="13175-119">它會直接與 Unity 通訊，以決定並顯示功能的使用方式。</span><span class="sxs-lookup"><span data-stu-id="13175-119">It directly communicates with Unity to determine and display the feature usages.</span></span>

### <a name="panels"></a><span data-ttu-id="13175-120">窗格</span><span class="sxs-lookup"><span data-stu-id="13175-120">Panels</span></span>

<span data-ttu-id="13175-121">面板會顯示所有已偵測到之 Unity 輸入來源上所有回報 InputFeatureUsages 的目前狀態。</span><span class="sxs-lookup"><span data-stu-id="13175-121">The panels display the current state of all reported InputFeatureUsages on all detected Unity input sources.</span></span>

<span data-ttu-id="13175-122">頂端較小的面板會列出所有偵測到的來源名稱。</span><span class="sxs-lookup"><span data-stu-id="13175-122">The smaller panel along the top lists the names of all detected sources.</span></span>

## <a name="see-also"></a><span data-ttu-id="13175-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="13175-123">See also</span></span>

- [<span data-ttu-id="13175-124">建立輸入系統資料提供者</span><span class="sxs-lookup"><span data-stu-id="13175-124">Creating an input system data provider</span></span>](../input/create-data-provider.md)
- [<span data-ttu-id="13175-125">控制器對應工具</span><span class="sxs-lookup"><span data-stu-id="13175-125">Controller mapping tool</span></span>](controller-mapping-tool.md)
