---
title: Dock
description: 停駐控制項的描述。
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: deb5cbd207befd9e941c6556d615523b0af11ca3
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104685641"
---
# <a name="dock"></a><span data-ttu-id="dde29-104">Dock</span><span class="sxs-lookup"><span data-stu-id="dde29-104">Dock</span></span>

![Dock](../images/dock/MRTK_UX_Dock_Main.png)

<span data-ttu-id="dde29-106">此控制項可讓您將物件移入和移出預定的位置，以建立調色板、貨架和導覽列。</span><span class="sxs-lookup"><span data-stu-id="dde29-106">This control enables moving objects in and out of predetermined positions, to create palettes, shelves and navigation bars.</span></span>

## <a name="features"></a><span data-ttu-id="dde29-107">功能</span><span class="sxs-lookup"><span data-stu-id="dde29-107">Features</span></span>

- <span data-ttu-id="dde29-108">支援任意數目的 dock 位置和版面配置 (可搭配 [`GridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection)) </span><span class="sxs-lookup"><span data-stu-id="dde29-108">Supports any number of dock positions and layouts (works great with [`GridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection))</span></span>
- <span data-ttu-id="dde29-109">停駐的物件會自動移至新物件的空間</span><span class="sxs-lookup"><span data-stu-id="dde29-109">Docked objects automatically move away to make space for new objects</span></span>
- <span data-ttu-id="dde29-110">物件會縮放以符合停駐的空間，然後在拖曳時調整為其原始位置。</span><span class="sxs-lookup"><span data-stu-id="dde29-110">Objects scale to fit the docked space, then resize to their original position when dragged out.</span></span>

## <a name="getting-started-with-dock"></a><span data-ttu-id="dde29-111">開始使用 Dock</span><span class="sxs-lookup"><span data-stu-id="dde29-111">Getting started with Dock</span></span>

- <span data-ttu-id="dde29-112">使用 Dock 元件建立 GameObject，並在其中新增 Gameobject 的子系。</span><span class="sxs-lookup"><span data-stu-id="dde29-112">Create a GameObject with the Dock component and add some children GameObjects to it.</span></span>
- <span data-ttu-id="dde29-113">將 DockPosition 元件新增至每個子系。</span><span class="sxs-lookup"><span data-stu-id="dde29-113">Add the DockPosition component to each of the children.</span></span>
- <span data-ttu-id="dde29-114">在場景中將可停駐元件新增至任意數目的物件，以允許它們固定。</span><span class="sxs-lookup"><span data-stu-id="dde29-114">Add the Dockable component to any number of objects in the scene to allow them to be docked.</span></span> <span data-ttu-id="dde29-115">它們也必須有 [`ObjectManipulator`](xref:Microsoft.MixedReality.Toolkit.UI.ObjectManipulator) 元件和碰撞。</span><span class="sxs-lookup"><span data-stu-id="dde29-115">They must have the [`ObjectManipulator`](xref:Microsoft.MixedReality.Toolkit.UI.ObjectManipulator) component and a Collider as well.</span></span>
- <span data-ttu-id="dde29-116">*選擇性：* 使用 [`GridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection) Dock 來自動設定 DockPositions。</span><span class="sxs-lookup"><span data-stu-id="dde29-116">*Optional:* use a [`GridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection) to the Dock to automatically lay out the DockPositions.</span></span>

### <a name="prerequisites"></a><span data-ttu-id="dde29-117">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="dde29-117">Prerequisites</span></span>

- <span data-ttu-id="dde29-118">每個可停駐的物件都必須具有或的碰撞 [`ObjectManipulator`](xref:Microsoft.MixedReality.Toolkit.UI.ObjectManipulator) [`ManipulationHandler`](xref:Microsoft.MixedReality.Toolkit.UI.ManipulationHandler) 。</span><span class="sxs-lookup"><span data-stu-id="dde29-118">Every dockable object must have a collider with an [`ObjectManipulator`](xref:Microsoft.MixedReality.Toolkit.UI.ObjectManipulator) or [`ManipulationHandler`](xref:Microsoft.MixedReality.Toolkit.UI.ManipulationHandler).</span></span>
- <span data-ttu-id="dde29-119">如果您想要物件在場景載入時啟動停駐，請將它指派給任何 DockPosition 的停駐物件屬性。</span><span class="sxs-lookup"><span data-stu-id="dde29-119">If you want an object to start Docked when the scene loads, assign it to any DockPosition's docked object property.</span></span>

## <a name="how-it-works"></a><span data-ttu-id="dde29-120">運作方式</span><span class="sxs-lookup"><span data-stu-id="dde29-120">How it works</span></span>

<span data-ttu-id="dde29-121">可停駐元件是以操作事件為基礎，可讓拖曳的物件在特定位置停駐和取消停駐。</span><span class="sxs-lookup"><span data-stu-id="dde29-121">The Dockable component builds upon manipulation events to allow dragged objects to be docked and undocked in specific positions.</span></span> <span data-ttu-id="dde29-122">放置是由最接近的重迭觸發 DockPosition 至拖曳的物件所決定，因此這兩個物件都必須有 Colliders，觸發程式才能啟動。</span><span class="sxs-lookup"><span data-stu-id="dde29-122">The placement is determined by the closest overlapping triggered DockPosition to the dragged object, so both objects need to have Colliders for the trigger to activate.</span></span>
