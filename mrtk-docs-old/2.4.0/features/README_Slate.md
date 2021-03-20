---
title: README_Slate
description: MRTK 中的平板相關檔
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
ms.localizationpriority: medium
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、平板、
ms.openlocfilehash: ac0c10a50ed3114150ede0988bf39c2c7696ea20
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104682641"
---
# <a name="slate"></a><span data-ttu-id="5f01c-104">平板</span><span class="sxs-lookup"><span data-stu-id="5f01c-104">Slate</span></span>

![平板](Images/Slate/MRTK_Slate_Main.png)

<span data-ttu-id="5f01c-106">[石板] 預製專案提供精簡的視窗樣式控制項，以顯示2D 內容，例如純文字或包含媒體的文章。</span><span class="sxs-lookup"><span data-stu-id="5f01c-106">The Slate prefab offers a thin window style control for displaying 2D content, for example plain text or articles including media.</span></span> <span data-ttu-id="5f01c-107">它提供了 grabbable 的標題列，以及 *追蹤* 和 *關閉* 功能。</span><span class="sxs-lookup"><span data-stu-id="5f01c-107">It offers a grabbable title bar as well as *Follow Me* and *Close* functionality.</span></span> <span data-ttu-id="5f01c-108">您可以透過明確的手寫輸入來滾動內容視窗。</span><span class="sxs-lookup"><span data-stu-id="5f01c-108">The content window can be scrolled via articulated hand input.</span></span>

## <a name="how-to-use-a-slate-control"></a><span data-ttu-id="5f01c-109">如何使用平板控制項</span><span class="sxs-lookup"><span data-stu-id="5f01c-109">How to use a slate control</span></span>

<span data-ttu-id="5f01c-110">[石板] 控制項是由下列元素所組成：</span><span class="sxs-lookup"><span data-stu-id="5f01c-110">A slate control is composed of the following elements:</span></span>

* <span data-ttu-id="5f01c-111">**標題** 欄：平板最上層的整個標題列。</span><span class="sxs-lookup"><span data-stu-id="5f01c-111">**TitleBar**: The entire title bar on top of the slate.</span></span>
* <span data-ttu-id="5f01c-112">**標題**：標題列左邊的標題區域。</span><span class="sxs-lookup"><span data-stu-id="5f01c-112">**Title**: The title area on the left side of the title bar.</span></span>
* <span data-ttu-id="5f01c-113">**按鈕**：標題列右側的按鈕區。</span><span class="sxs-lookup"><span data-stu-id="5f01c-113">**Buttons**: The button area on the right side of the title bar.</span></span>
* <span data-ttu-id="5f01c-114">**BackPlate**：蓋板的後端。</span><span class="sxs-lookup"><span data-stu-id="5f01c-114">**BackPlate**: The back side of the slate.</span></span>
* <span data-ttu-id="5f01c-115">**ContentQuad**：內容已指派為材質。</span><span class="sxs-lookup"><span data-stu-id="5f01c-115">**ContentQuad**: Content is assigned as material.</span></span> <span data-ttu-id="5f01c-116">此範例使用範例材質 ' PanContent '。</span><span class="sxs-lookup"><span data-stu-id="5f01c-116">The example uses a sample material 'PanContent'.</span></span>

<img src="Images/Slate/MRTK_SlateStructure.jpg" width="650" alt="Slate Structures">

## <a name="bounding-box"></a><span data-ttu-id="5f01c-117">週框方塊</span><span class="sxs-lookup"><span data-stu-id="5f01c-117">Bounding box</span></span>

<span data-ttu-id="5f01c-118">一個石板控制項包含用來縮放和旋轉的周框方塊腳本。</span><span class="sxs-lookup"><span data-stu-id="5f01c-118">A slate control contains a bounding box script for scaling and rotating.</span></span> <span data-ttu-id="5f01c-119">如需周框方塊的詳細資訊，請參閱周 [框](README_BoundingBox.md) 方塊頁面。</span><span class="sxs-lookup"><span data-stu-id="5f01c-119">For more information on bounding box, please see the [Bounding box](README_BoundingBox.md) page.</span></span>

<img src="Images/Slate/MRTK_Slate_BB.jpg" width="650" alt="Slate BB">

## <a name="buttons"></a><span data-ttu-id="5f01c-120">按鈕</span><span class="sxs-lookup"><span data-stu-id="5f01c-120">Buttons</span></span>

<span data-ttu-id="5f01c-121">標準的平板版提供兩個按鈕，作為標題列右上角的預設值：</span><span class="sxs-lookup"><span data-stu-id="5f01c-121">A standard slate offers two buttons as default on the top right of the title bar:</span></span>

* <span data-ttu-id="5f01c-122">**跟隨我**：切換 orbital 的求解元件，讓 [石板] 物件跟隨在使用者後面。</span><span class="sxs-lookup"><span data-stu-id="5f01c-122">**Follow Me**: Toggles an orbital solver components to make the slate object follow the user.</span></span>
* <span data-ttu-id="5f01c-123">**關閉**：停用 [石板] 物件。</span><span class="sxs-lookup"><span data-stu-id="5f01c-123">**Close**: Disables the slate object.</span></span>

<img src="Images/Slate/MRTK_Slate_Buttons.jpg" width="650" alt="Slate Buttons">

## <a name="scripts"></a><span data-ttu-id="5f01c-124">指令碼</span><span class="sxs-lookup"><span data-stu-id="5f01c-124">Scripts</span></span>

<span data-ttu-id="5f01c-125">一般而言， `NearInteractionTouchable.cs` 腳本必須附加至任何要接收觸控事件的物件 `IMixedRealityTouchHandler` 。</span><span class="sxs-lookup"><span data-stu-id="5f01c-125">In general, the `NearInteractionTouchable.cs` script must be attached to any object that is intended to receive touch events from the `IMixedRealityTouchHandler`.</span></span>

<img src="Images/Slate/MRTK_Slate_Scripts.png" alt="Scripts">

* <span data-ttu-id="5f01c-126">`HandInteractionPan.cs` 此腳本會處理已表達的手輸入，以便在平板 *ContentQuad* 上接觸和移動內容。</span><span class="sxs-lookup"><span data-stu-id="5f01c-126">`HandInteractionPan.cs` This script handles articulated hand input for touching and moving the content on the slate's *ContentQuad*.</span></span>

* <span data-ttu-id="5f01c-127">`HandInteractionPanZoom.cs`：除了移動流覽互動之外，此腳本也支援雙向縮放。</span><span class="sxs-lookup"><span data-stu-id="5f01c-127">`HandInteractionPanZoom.cs`: In addition to the panning interaction, this script supports two-handed zooming.</span></span>

<img src="Images/Slate/MRTK_Slate_PanZoom.png" width="500" alt="Slate Pan Zoom">
