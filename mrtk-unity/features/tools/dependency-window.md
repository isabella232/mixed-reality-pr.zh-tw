---
title: DependencyWindow
description: 在 MRTK 中使用相依性視窗的相關檔
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: c53989151123f61988160b74fa876b907264bdd4
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104696015"
---
# <a name="dependency-window"></a><span data-ttu-id="fdab2-104">相依性視窗</span><span class="sxs-lookup"><span data-stu-id="fdab2-104">Dependency window</span></span>

<span data-ttu-id="fdab2-105">在 Unity 中，通常很難 gleam 正在使用的資產，以及參考它們的內容。</span><span class="sxs-lookup"><span data-stu-id="fdab2-105">In Unity, it is often difficult to gleam which assets are being used, and what is referencing them.</span></span> <span data-ttu-id="fdab2-106">當您只在意目前的場景時，[尋找場景中的參考] 選項的效果很好，但是整個 Unity 專案呢？</span><span class="sxs-lookup"><span data-stu-id="fdab2-106">The "Find References in Scene" option works great when you are only concerned with the current scene, but what about your entire Unity project?</span></span> <span data-ttu-id="fdab2-107">這是相依性 **視窗** (資產/MRTK/工具/DependencyWindow) 可能很有用的地方。</span><span class="sxs-lookup"><span data-stu-id="fdab2-107">This is where the **Dependency Window** (Assets/MRTK/Tools/DependencyWindow) can be useful.</span></span>

<span data-ttu-id="fdab2-108">[相依性] 視窗會顯示資產的參考方式，以及彼此之間的關係。</span><span class="sxs-lookup"><span data-stu-id="fdab2-108">The Dependency Window displays how assets reference and depend on each other.</span></span> <span data-ttu-id="fdab2-109">相依性的計算方式是剖析專案 YAML 檔中的 guid (注意：腳本相依性的腳本不會被視為) 。</span><span class="sxs-lookup"><span data-stu-id="fdab2-109">Dependencies are calculated by parsing guids within project YAML files (note, script to script dependencies are not considered).</span></span>

## <a name="usage"></a><span data-ttu-id="fdab2-110">使用方式</span><span class="sxs-lookup"><span data-stu-id="fdab2-110">Usage</span></span>

<span data-ttu-id="fdab2-111">若要開啟此視窗，請選取 [ *混合現實工具組->公用程式->相依性] 視窗* ，此視窗會開啟視窗並自動開始建立專案的相依性圖形。</span><span class="sxs-lookup"><span data-stu-id="fdab2-111">To open the window, select *Mixed Reality Toolkit->Utilities->Dependency Window* which will open the window and automatically begin building your project's dependency graph.</span></span> <span data-ttu-id="fdab2-112">建立相依性圖形之後，您可以在 [專案] 索引標籤中選取資產來檢查其相依性。</span><span class="sxs-lookup"><span data-stu-id="fdab2-112">Once the dependency graph is built, you can select assets in the project tab to inspect their dependencies.</span></span>

![相依性視窗](../images/dependency-window/MRTK_Dependency_Window.png)

<span data-ttu-id="fdab2-114">此視窗會顯示目前所選資產相依的資產清單，以及相依于該資產的資產階層式清單。</span><span class="sxs-lookup"><span data-stu-id="fdab2-114">The window displays a list of assets that the currently selected asset depends on, and a hierarchical list of assets that depend on it.</span></span> <span data-ttu-id="fdab2-115">如果沒有任何專案取決於目前選取的資產，您可以考慮將它從您的專案中刪除 (請注意，某些資產是透過著色器之類的 Api 以程式設計方式載入。尋找 () ，相依性追蹤程式) 可能不會攔截到這些資產。</span><span class="sxs-lookup"><span data-stu-id="fdab2-115">If nothing depends on the currently selected asset, you can consider deleting it from your project (note that some assets are loaded programmatically via APIs like Shader.Find() and may not be caught by the dependency tracker).</span></span>

<span data-ttu-id="fdab2-116">此視窗也可以只顯示任何其他資產未參考的所有資產清單，並可將其視為刪除：</span><span class="sxs-lookup"><span data-stu-id="fdab2-116">The window can also display just a list of all assets which are not referenced by any other assets and could be considered for deletion:</span></span>

![顯示未參考資產的相依性視窗](../images/dependency-window/MRTK_Dependency_Window_Unreferenced.png)

> [!NOTE]
> <span data-ttu-id="fdab2-118">當相依性視窗正在使用中時，如果已修改、新增或移除資產，建議您重新整理相依性圖形以取得最新的結果。</span><span class="sxs-lookup"><span data-stu-id="fdab2-118">If assets are modified, added, or removed while the dependency window is in use, it is advised to refresh the dependency graph for the most "up to date" results.</span></span>
