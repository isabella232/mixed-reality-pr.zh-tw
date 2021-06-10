---
title: 遷移視窗
description: 如何在 MRTK 中遷移至更新的相關檔
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: a6e268dd28be2a3d485f937ec5b5ce6b1f29851f
ms.sourcegitcommit: a5afc24a4887880e394ef57216b8fd9de9760004
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/28/2021
ms.locfileid: "110647117"
---
# <a name="migration-window"></a><span data-ttu-id="501fd-104">遷移視窗</span><span class="sxs-lookup"><span data-stu-id="501fd-104">Migration window</span></span>

<span data-ttu-id="501fd-105">當 MRTK 進行變更時，某些元件可能會被取代，並引進取代。</span><span class="sxs-lookup"><span data-stu-id="501fd-105">As the MRTK undergoes changes, some components might get deprecated and replacements will get introduced.</span></span>
<span data-ttu-id="501fd-106">[遷移] 視窗是一種工具，可協助使用者將這些被取代元件的子集自動遷移至新的取代。</span><span class="sxs-lookup"><span data-stu-id="501fd-106">The migration window is a tool that helps users to automatically migrate a subset of those deprecated components to the new replacements.</span></span>

![遷移視窗](../images/migration-window/MRTK_Migration_Window.png)

## <a name="usage"></a><span data-ttu-id="501fd-108">使用方式</span><span class="sxs-lookup"><span data-stu-id="501fd-108">Usage</span></span>

<span data-ttu-id="501fd-109">若要開啟視窗，請選取 [**混合的實際**  >  **工具組**  >  **公用程式**  >  **遷移] 視窗**。</span><span class="sxs-lookup"><span data-stu-id="501fd-109">To open the window, select **Mixed Reality** > **Toolkit** > **Utilities** > **Migration Window**.</span></span> <span data-ttu-id="501fd-110">一旦開啟 [遷移] 視窗，您可以選擇遷移處理常式的元件特定執行方式來啟用 [選取模式] 流覽索引標籤。</span><span class="sxs-lookup"><span data-stu-id="501fd-110">Once the migration window is open, the selection mode navigation tabs can be enabled by choosing the component specific implementation of the migration handler.</span></span>  

![遷移選取模式](../images/migration-window/MRTK_Migration_Modes.png)

### <a name="object-mode"></a><span data-ttu-id="501fd-112">物件模式</span><span class="sxs-lookup"><span data-stu-id="501fd-112">Object mode</span></span>

<span data-ttu-id="501fd-113">選取 [物件] 索引標籤可讓物件欄位從目前開啟的場景或從要遷移的專案資料夾中的 prefabs，拖放任何遊戲物件。</span><span class="sxs-lookup"><span data-stu-id="501fd-113">Selecting the objects tab enables the object Field to where the user can drag and drop any Game objects from the currently open scene or prefabs from the project folder to be migrated.</span></span>
<span data-ttu-id="501fd-114">按下所列物件右邊顯示的 [移除] *(-)* 按鈕，就會從選取清單中移除該物件。</span><span class="sxs-lookup"><span data-stu-id="501fd-114">Pressing the remove *(-)* button displayed at the right side of the listed object removes the object from the selection list.</span></span>

<span data-ttu-id="501fd-115">當所有所需的物件都在清單中之後，按 [ *遷移* ] 按鈕會將所選遷移處理常式執行所需的變更，套用至選取範圍中符合執行的所有元件。</span><span class="sxs-lookup"><span data-stu-id="501fd-115">Once all the desired objects are in the list, pressing the *Migrate* button will apply the changes required by the chosen migration handler implementation to all components in the selection that match the implementation.</span></span>

![選取專案遷移](../images/migration-window/MRTK_Object_Migration.png)

### <a name="scene-mode"></a><span data-ttu-id="501fd-117">場景模式</span><span class="sxs-lookup"><span data-stu-id="501fd-117">Scene mode</span></span>

<span data-ttu-id="501fd-118">允許使用者拖放包含要遷移之物件的場景資產。</span><span class="sxs-lookup"><span data-stu-id="501fd-118">Allows user to drag and drop scene assets containing objects to be migrated.</span></span>

![選取用於遷移的場景](../images/migration-window/MRTK_Scene_Selection.png)

### <a name="project-mode"></a><span data-ttu-id="501fd-120">專案模式</span><span class="sxs-lookup"><span data-stu-id="501fd-120">Project mode</span></span>

<span data-ttu-id="501fd-121">按下 [ *遷移* ] 按鈕將會針對專案中的所有 prefabs 和場景，更新遷移處理常式執行的目標群組件。</span><span class="sxs-lookup"><span data-stu-id="501fd-121">Pressing the *Migrate* button will update the component targeted by the migration handler implementation for all prefabs and scenes in the project.</span></span>

![遷移完整專案](../images/migration-window/MRTK_Project_Migration.png)

## <a name="see-also"></a><span data-ttu-id="501fd-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="501fd-123">See also</span></span>

- [<span data-ttu-id="501fd-124">從較早的版本更新</span><span class="sxs-lookup"><span data-stu-id="501fd-124">Updating from earlier versions</span></span>](../../updates-deployment/updating.md)
- [<span data-ttu-id="501fd-125">Microsoft Mixed Reality 工具組版本</span><span class="sxs-lookup"><span data-stu-id="501fd-125">Microsoft Mixed Reality Toolkit releases</span></span>](../../release-notes/mrtk-26-release-notes.md)
- [<span data-ttu-id="501fd-126">MRTK 藍圖</span><span class="sxs-lookup"><span data-stu-id="501fd-126">MRTK roadmap</span></span>](../../roadmap.md)
