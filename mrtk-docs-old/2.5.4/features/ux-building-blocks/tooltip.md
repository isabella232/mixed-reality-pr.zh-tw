---
title: 工具提示
description: MRTK 中的工具提示總覽
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、工具提示、
ms.openlocfilehash: 68b5b434180c05f1176b141c85009bd35a364dd8
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104686061"
---
# <a name="tooltip"></a><span data-ttu-id="2f49b-104">工具提示</span><span class="sxs-lookup"><span data-stu-id="2f49b-104">Tooltip</span></span>

![工具提示主要](../images/tooltip/MRTK_Tooltip_Main.png)

<span data-ttu-id="2f49b-106">工具提示通常用來在進一步檢查物件時傳達提示或額外資訊。</span><span class="sxs-lookup"><span data-stu-id="2f49b-106">Tooltips are usually used to convey a hint or extra information upon closer inspection of an object.</span></span> <span data-ttu-id="2f49b-107">工具提示可以用來標注實體環境中的物件。</span><span class="sxs-lookup"><span data-stu-id="2f49b-107">Tooltips can be used to annotate objects in the physical environment.</span></span>

## <a name="how-to-use-a-tooltip"></a><span data-ttu-id="2f49b-108">如何使用工具提示</span><span class="sxs-lookup"><span data-stu-id="2f49b-108">How to use a tooltip</span></span>

<span data-ttu-id="2f49b-109">工具提示可以直接新增至階層，並以物件為目標。</span><span class="sxs-lookup"><span data-stu-id="2f49b-109">A tooltip can be added directly to the hierarchy and targeted to an object.</span></span>

<span data-ttu-id="2f49b-110">若要使用這個方法，只需將遊戲物件和其中一個工具提示 prefabs (資產/MRTK/SDK/Features/UX/Prefabs/工具提示) 至場景階層。</span><span class="sxs-lookup"><span data-stu-id="2f49b-110">To use this method simply add a game object and one of the tooltip prefabs (Assets/MRTK/SDK/Features/UX/Prefabs/Tooltips) to the scene hierarchy.</span></span> <span data-ttu-id="2f49b-111">在預製專案的 [偵測器] 面板中，展開 [`ToolTip`](xref:Microsoft.MixedReality.Toolkit.UI.ToolTip) 腳本。</span><span class="sxs-lookup"><span data-stu-id="2f49b-111">In the prefab's inspector panel, expand the [`ToolTip`](xref:Microsoft.MixedReality.Toolkit.UI.ToolTip) script.</span></span> <span data-ttu-id="2f49b-112">選取提示狀態，並設定工具提示。</span><span class="sxs-lookup"><span data-stu-id="2f49b-112">Select a tip state and configure the tooltip.</span></span>  <span data-ttu-id="2f49b-113">在 [文字] 欄位中，輸入工具提示的個別文字。</span><span class="sxs-lookup"><span data-stu-id="2f49b-113">Enter the respective text for the tool tip in the text field.</span></span> <span data-ttu-id="2f49b-114">展開 [`ToolTipConnector`](xref:Microsoft.MixedReality.Toolkit.UI.ToolTipConnector) 腳本，並將具有工具提示的物件從階層拖曳至標示為 [ *目標*] 的欄位。</span><span class="sxs-lookup"><span data-stu-id="2f49b-114">Expand the [`ToolTipConnector`](xref:Microsoft.MixedReality.Toolkit.UI.ToolTipConnector) script and drag the object that is to have the tooltip from the hierarchy into the field labelled *Target*.</span></span> <span data-ttu-id="2f49b-115">這會將工具提示附加至物件。</span><span class="sxs-lookup"><span data-stu-id="2f49b-115">This attaches the tooltip to the object.</span></span>
<span data-ttu-id="2f49b-116">![工具提示連接器](../images/tooltip/MRTK_Tooltip_Connector.png)</span><span class="sxs-lookup"><span data-stu-id="2f49b-116">![Tooltip Connector](../images/tooltip/MRTK_Tooltip_Connector.png)</span></span>

<span data-ttu-id="2f49b-117">這種使用方式假設工具提示一律會顯示，或是藉由變更 tooltip 元件的工具提示狀態屬性，透過腳本顯示/隱藏。</span><span class="sxs-lookup"><span data-stu-id="2f49b-117">This use assumes a tooltip that is always showing or that is shown / hidden via script by changing the tooltip state property of the tooltip component.</span></span>

## <a name="dynamically-spawning-tooltips"></a><span data-ttu-id="2f49b-118">動態產生工具提示</span><span class="sxs-lookup"><span data-stu-id="2f49b-118">Dynamically spawning tooltips</span></span>

<span data-ttu-id="2f49b-119">工具提示可以在執行時間以動態方式加入至物件，也可以預先設定為在點按或焦點上顯示和隱藏。</span><span class="sxs-lookup"><span data-stu-id="2f49b-119">A tooltip can be dynamically added to an object at runtime as well as pre-set to show and hide on a tap or focus.</span></span> <span data-ttu-id="2f49b-120">只要將 [`ToolTipSpawner`](xref:Microsoft.MixedReality.Toolkit.UI.ToolTipSpawner) 腳本新增到任何遊戲物件。</span><span class="sxs-lookup"><span data-stu-id="2f49b-120">Simply add the [`ToolTipSpawner`](xref:Microsoft.MixedReality.Toolkit.UI.ToolTipSpawner) script to any game object.</span></span> <span data-ttu-id="2f49b-121">出現和消失的延遲可在腳本偵測器和存留期內設定，讓工具提示在設定的持續時間之後消失。</span><span class="sxs-lookup"><span data-stu-id="2f49b-121">Delays for appearing and disappearing can be set in the scripts inspector as well as a lifetime so that the tooltip will disappear after a set duration.</span></span> <span data-ttu-id="2f49b-122">工具提示也是功能樣式屬性，例如 spawner 腳本中的背景視覺效果。</span><span class="sxs-lookup"><span data-stu-id="2f49b-122">Tooltips also feature style properties such as background visuals in the spawner script.</span></span> <span data-ttu-id="2f49b-123">根據預設，工具提示會使用 spawner 腳本錨定至物件。</span><span class="sxs-lookup"><span data-stu-id="2f49b-123">By default the tooltip will be anchored to the object with the spawner script.</span></span> <span data-ttu-id="2f49b-124">這可以藉由將 GameObject 指派給錨點欄位來加以變更。</span><span class="sxs-lookup"><span data-stu-id="2f49b-124">This can be changed by assigning a GameObject to the anchor field.</span></span>

## <a name="example-scene"></a><span data-ttu-id="2f49b-125">範例場景</span><span class="sxs-lookup"><span data-stu-id="2f49b-125">Example scene</span></span>

<span data-ttu-id="2f49b-126">在範例場景中 (資產/MRTK/範例/示範/UX/工具提示/場景) ，您將可以找到工具提示的各種範例。</span><span class="sxs-lookup"><span data-stu-id="2f49b-126">In the example scenes (Assets/MRTK/Examples/Demos/UX/Tooltips/Scenes), you will be able to find various examples of tooltips.</span></span>

![工具提示範例](../images/tooltip/MRTK_Tooltip_Examples.png)
