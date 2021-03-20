---
title: ControllerMappingTool
description: MRTK 中的控制器對應工具檔
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
ms.localizationpriority: medium
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: 9008925869b7f7f4f219f056cee512651fe451b1
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104688008"
---
# <a name="controller-mapping-tool"></a><span data-ttu-id="574da-104">控制器對應工具</span><span class="sxs-lookup"><span data-stu-id="574da-104">Controller mapping tool</span></span>

<span data-ttu-id="574da-105">控制器對應工具是裝置上的執行時間 (或編輯器) 工具，可讓開發人員快速判斷硬體控制器的 Unity 輸入軸和按鈕對應 (例如：移動控制器) 。</span><span class="sxs-lookup"><span data-stu-id="574da-105">The controller mapping tool is a runtime (on device or in the editor) tool that enables developers to quickly determine the Unity input axis and button mappings for a hardware controller (ex: motion controller).</span></span>

<span data-ttu-id="574da-106">當您針對新的硬體控制器開發支援時，此工具非常有用。</span><span class="sxs-lookup"><span data-stu-id="574da-106">This tool is very useful when developing support for a new hardware controller.</span></span> <span data-ttu-id="574da-107">它也可以協助確認現有控制器的支援類別中可疑的控制項對應問題。</span><span class="sxs-lookup"><span data-stu-id="574da-107">It can also help to confirm a suspected control mapping issue in the support class for an existing controller.</span></span>

![控制器對應工具](../Images/ControllerMappingTool/ControllerMappingTool.png)

## <a name="using-the-controller-mapping-tool"></a><span data-ttu-id="574da-109">使用控制器對應工具</span><span class="sxs-lookup"><span data-stu-id="574da-109">Using the controller mapping tool</span></span>

<span data-ttu-id="574da-110">若要開始使用控制器對應工具，請流覽至 **MRTK/tools/RuntimeTools/tools/ControllerMappingTool** ，然後開啟 **ControllerMappingTool** 場景。</span><span class="sxs-lookup"><span data-stu-id="574da-110">To get started with the controller mapping tool, navigate to **MRTK/Tools/RuntimeTools/Tools/ControllerMappingTool** and open the **ControllerMappingTool** scene.</span></span> <span data-ttu-id="574da-111">載入場景之後，您可以在編輯器中使用播放模式來執行專案，或在裝置上建立並執行專案。</span><span class="sxs-lookup"><span data-stu-id="574da-111">Once the scene has been loaded, the project can either be run in the editor, using play mode, or built and run on a device.</span></span>

<span data-ttu-id="574da-112">檢查控制器的 Unity 對應：</span><span class="sxs-lookup"><span data-stu-id="574da-112">To examine Unity's mappings for a controller:</span></span>

- <span data-ttu-id="574da-113">連接控制器</span><span class="sxs-lookup"><span data-stu-id="574da-113">Connect the controller</span></span>
- <span data-ttu-id="574da-114">按下每個按鈕並移動每個軸</span><span class="sxs-lookup"><span data-stu-id="574da-114">Press each button and move each axis</span></span>
- <span data-ttu-id="574da-115">請注意顯示中的對應</span><span class="sxs-lookup"><span data-stu-id="574da-115">Note the mappings in the display</span></span>
- <span data-ttu-id="574da-116">更新控制器的輸入系統資料提供者中的控制項對應</span><span class="sxs-lookup"><span data-stu-id="574da-116">Update the control mappings in the input system data provider for the controller</span></span>

> [!NOTE]
> <span data-ttu-id="574da-117">控制器對應工具不會利用 Microsoft Mixed Reality 工具組元件。</span><span class="sxs-lookup"><span data-stu-id="574da-117">The controller mapping tool does not make use of Microsoft Mixed Reality Toolkit components.</span></span> <span data-ttu-id="574da-118">它會直接與 Unity 通訊，以決定並顯示控制項對應。</span><span class="sxs-lookup"><span data-stu-id="574da-118">It directly communicates with Unity to determine and display the control mappings.</span></span>

### <a name="all-controls-display"></a><span data-ttu-id="574da-119">所有控制項顯示</span><span class="sxs-lookup"><span data-stu-id="574da-119">All controls display</span></span>

<span data-ttu-id="574da-120">大型顯示面板會報告所有已定義 Unity 輸入軸和按鈕的狀態， (例如：軸10、按鈕 3) 。</span><span class="sxs-lookup"><span data-stu-id="574da-120">The large display panel reports the state of all defined Unity input axes and buttons (ex: Axis 10, Button 3).</span></span> <span data-ttu-id="574da-121">此面板會提供控制器狀態的完整觀點。</span><span class="sxs-lookup"><span data-stu-id="574da-121">This panel provides a complete view of the state of the controller.</span></span>

![所有控制項顯示](../Images/ControllerMappingTool/AllControls.png)

### <a name="active-controls-display"></a><span data-ttu-id="574da-123">現用控制項顯示</span><span class="sxs-lookup"><span data-stu-id="574da-123">Active controls display</span></span>

<span data-ttu-id="574da-124">較小、窄的顯示面板會顯示 Unity 輸入 axed 以及處於作用中狀態的按鈕 (例如：按下按鈕) 。</span><span class="sxs-lookup"><span data-stu-id="574da-124">The smaller, narrow display panel shows the Unity input axed and buttons which are in an active state (ex: a button is pressed).</span></span> <span data-ttu-id="574da-125">作用中的控制項顯示提供控制器狀態的簡單讀取摘要視圖。</span><span class="sxs-lookup"><span data-stu-id="574da-125">The active controls display provides an easy to read summary view of the state of the controller.</span></span>

![現用控制項顯示](../Images/ControllerMappingTool/ActiveControls.png)

## <a name="see-also"></a><span data-ttu-id="574da-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="574da-127">See also</span></span>

- [<span data-ttu-id="574da-128">建立輸入系統資料提供者</span><span class="sxs-lookup"><span data-stu-id="574da-128">Creating an input system data provider</span></span>](../Input/CreateDataProvider.md)
