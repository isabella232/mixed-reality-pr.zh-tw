---
title: README_AppBar
description: MRTK 中的應用程式行總覽
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、應用程式行、
ms.openlocfilehash: 03667ca49156781e61218d7201bdbed245540c81
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104695265"
---
# <a name="app-bar"></a><span data-ttu-id="68f35-104">應用程式列</span><span class="sxs-lookup"><span data-stu-id="68f35-104">App bar</span></span>

![應用程式列](Images/AppBar/MRTK_AppBar_Main.png)

<span data-ttu-id="68f35-106">應用程式行是與 [界限控制](README_BoundsControl.md) 腳本一起使用的 UI 元件。</span><span class="sxs-lookup"><span data-stu-id="68f35-106">App bar is a UI component that is used together with the [bounds control](README_BoundsControl.md) script.</span></span> <span data-ttu-id="68f35-107">它會將按鈕控制項新增至物件，並具有要操作的目的。</span><span class="sxs-lookup"><span data-stu-id="68f35-107">It adds button controls to an object with the intent to manipulate it.</span></span> <span data-ttu-id="68f35-108">您可以使用 [調整] 按鈕，將物件的界限控制介面解除/啟用。</span><span class="sxs-lookup"><span data-stu-id="68f35-108">Using the 'Adjust' button, the bounds control interface for an object can be de- / activated.</span></span> <span data-ttu-id="68f35-109">[移除] 按鈕應該從場景中移除該物件。</span><span class="sxs-lookup"><span data-stu-id="68f35-109">The "Remove" button should remove the object from the scene.</span></span>

## <a name="how-to-use-app-bar"></a><span data-ttu-id="68f35-110">如何使用應用程式行</span><span class="sxs-lookup"><span data-stu-id="68f35-110">How to use app bar</span></span>

<span data-ttu-id="68f35-111">拖放 `AppBar` (資產/MRTK/SDK/Features/UX/Prefabs/AppBar/AppBar. 預製專案) 入場景階層中。</span><span class="sxs-lookup"><span data-stu-id="68f35-111">Drag and drop `AppBar` (Assets/MRTK/SDK/Features/UX/Prefabs/AppBar/AppBar.prefab) into the scene hierarchy.</span></span> <span data-ttu-id="68f35-112">在元件的 [偵測器] 面板中，將具有界限控制項的任何物件指派為 *目標周框* 方塊，以將應用程式行加入其中。</span><span class="sxs-lookup"><span data-stu-id="68f35-112">In the inspector panel of the component, assign any object with a bounds control as the *Target Bounding Box* to add the app bar to it.</span></span>

<span data-ttu-id="68f35-113">**重要事項：** 目標物件的界限控制項啟用選項應該是「手動啟用」。</span><span class="sxs-lookup"><span data-stu-id="68f35-113">**Important:** The bounds control activation option for the target object should be 'Activate Manually'.</span></span>

<img src="Images/AppBar/MRTK_AppBar_Setup1.png" width="450" alt="App Bar setup 1">

<img src="Images/AppBar/MRTK_AppBar_Setup2.png" width="450" alt="App Bar setup 2">
