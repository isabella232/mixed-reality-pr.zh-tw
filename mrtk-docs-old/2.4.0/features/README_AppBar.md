---
title: README_AppBar
description: MRTK 中的應用程式行總覽
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
ms.localizationpriority: medium
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、應用程式行、
ms.openlocfilehash: e730c5a51aa32e72147ec7482b9ebbcdb9fafedc
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104688808"
---
# <a name="app-bar"></a><span data-ttu-id="4b01c-104">應用程式列</span><span class="sxs-lookup"><span data-stu-id="4b01c-104">App bar</span></span>

![應用程式列](Images/AppBar/MRTK_AppBar_Main.png)

<span data-ttu-id="4b01c-106">應用程式行是與周 [框](README_BoundingBox.md) 方塊腳本一起使用的 UI 元件。</span><span class="sxs-lookup"><span data-stu-id="4b01c-106">App bar is a UI component that is used together with the [bounding box](README_BoundingBox.md) script.</span></span> <span data-ttu-id="4b01c-107">它會將按鈕控制項新增至物件，並具有要操作的目的。</span><span class="sxs-lookup"><span data-stu-id="4b01c-107">It adds button controls to an object with the intent to manipulate it.</span></span> <span data-ttu-id="4b01c-108">您可以使用 [調整] 按鈕，將物件的周框方塊介面解除/啟用。</span><span class="sxs-lookup"><span data-stu-id="4b01c-108">Using the 'Adjust' button, the bounding box interface for an object can be de- / activated.</span></span> <span data-ttu-id="4b01c-109">[移除] 按鈕應該從場景中移除該物件。</span><span class="sxs-lookup"><span data-stu-id="4b01c-109">The "Remove" button should remove the object from the scene.</span></span>

## <a name="how-to-use-app-bar"></a><span data-ttu-id="4b01c-110">如何使用應用程式行</span><span class="sxs-lookup"><span data-stu-id="4b01c-110">How to use app bar</span></span>

<span data-ttu-id="4b01c-111">拖放 `AppBar` (資產/MRTK/SDK/Features/UX/Prefabs/AppBar/AppBar. 預製專案) 入場景階層中。</span><span class="sxs-lookup"><span data-stu-id="4b01c-111">Drag and drop `AppBar` (Assets/MRTK/SDK/Features/UX/Prefabs/AppBar/AppBar.prefab) into the scene hierarchy.</span></span> <span data-ttu-id="4b01c-112">在元件的 [偵測器] 面板中，指派具有周框方塊的任何物件做為 *目標周框* 方塊，以將應用程式行加入其中。</span><span class="sxs-lookup"><span data-stu-id="4b01c-112">In the inspector panel of the component, assign any object with a bounding box as the *Target Bounding Box* to add the app bar to it.</span></span>

<span data-ttu-id="4b01c-113">**重要事項：** 目標物件的周框方塊啟用選項應該是「手動啟用」。</span><span class="sxs-lookup"><span data-stu-id="4b01c-113">**Important:** The bounding box activation option for the target object should be 'Activate Manually'.</span></span>

<img src="Images/AppBar/MRTK_AppBar_Setup1.png" width="450" alt="App Bar Setup 1">

<img src="Images/AppBar/MRTK_AppBar_Setup2.png" width="450" alt="App Bar Setup 2">
