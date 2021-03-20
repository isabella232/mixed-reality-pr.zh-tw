---
title: 與 3D 物件互動
description: 本課程說明如何使用混合實境工具組 (MRTK) 來與混合實境應用程式中的 3D 物件互動及進行操作。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: 混合現實、unity、教學課程、hololens、MRTK、混合現實工具組、UWP、物件互動、界限會控制
ms.localizationpriority: high
ms.openlocfilehash: 1ab7b3a334639be564717d77d3bbc478a25e8326
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "102237239"
---
# <a name="7-interacting-with-3d-objects"></a><span data-ttu-id="8c6ad-104">7.與 3D 物件互動</span><span class="sxs-lookup"><span data-stu-id="8c6ad-104">7. Interacting with 3D objects</span></span>

<span data-ttu-id="8c6ad-105">在本教學課程中，您將了解如何對 3D 物件進行遠近操作，並限制允許的操作類型。</span><span class="sxs-lookup"><span data-stu-id="8c6ad-105">In this tutorial, you will learn how to enable near and far manipulation of 3D objects and limit the allowed types of manipulation.</span></span> <span data-ttu-id="8c6ad-106">您也將瞭解如何在3D 物件周圍新增界限控制項，讓您更輕鬆地控制物件操作。</span><span class="sxs-lookup"><span data-stu-id="8c6ad-106">You will also learn how to add bounds control around 3D objects to make it easier to control the object manipulation.</span></span>

## <a name="objectives"></a><span data-ttu-id="8c6ad-107">目標</span><span class="sxs-lookup"><span data-stu-id="8c6ad-107">Objectives</span></span>

* <span data-ttu-id="8c6ad-108">了解如何設定3D 物件，使其能夠進行互動</span><span class="sxs-lookup"><span data-stu-id="8c6ad-108">Learn how to configure 3D objects so they can be interacted with</span></span>
* <span data-ttu-id="8c6ad-109">瞭解如何將界限控制項新增至3D 物件</span><span class="sxs-lookup"><span data-stu-id="8c6ad-109">Learn how to add bounds control to 3D objects</span></span>

## <a name="manipulating-3d-objects"></a><span data-ttu-id="8c6ad-110">操作 3D 物件</span><span class="sxs-lookup"><span data-stu-id="8c6ad-110">Manipulating 3D objects</span></span>

<span data-ttu-id="8c6ad-111">在本節中，您將加入可操作所有 Rover 零件的能力，也就是您在[將物件置放在場景中](mr-learning-base-04.md)的教學課程中，於桌面上組織的所有 Rover 零件。</span><span class="sxs-lookup"><span data-stu-id="8c6ad-111">In this section, you will add the ability to manipulate all the Rover parts you organized on the table during the [Positioning objects in the scene](mr-learning-base-04.md) tutorial.</span></span>

<span data-ttu-id="8c6ad-112">達成此動作所需採取的主要步驟如下：</span><span class="sxs-lookup"><span data-stu-id="8c6ad-112">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="8c6ad-113">將 Object Manipulator (指令碼) 元件新增至所有零件物件</span><span class="sxs-lookup"><span data-stu-id="8c6ad-113">Add the Object Manipulator (Script) component to all the part objects</span></span>
2. <span data-ttu-id="8c6ad-114">將 NearInteractionGrabbable 元件新增至所有零件物件</span><span class="sxs-lookup"><span data-stu-id="8c6ad-114">Add the NearInteractionGrabbable component to all the part objects</span></span>
3. <span data-ttu-id="8c6ad-115">設定 Object Manipulator (指令碼) 元件</span><span class="sxs-lookup"><span data-stu-id="8c6ad-115">Configure the Object Manipulator (Script) component</span></span>

> [!NOTE]
> <span data-ttu-id="8c6ad-116">若要能夠 **操作物件**，該物件必須具有下列元件：</span><span class="sxs-lookup"><span data-stu-id="8c6ad-116">To be able to **manipulate an object**, the object must have the following components:</span></span>
>
> * <span data-ttu-id="8c6ad-117">**Collider** 元件，例如 Box Collider</span><span class="sxs-lookup"><span data-stu-id="8c6ad-117">**Collider** component, for example, a Box Collider</span></span>
> * <span data-ttu-id="8c6ad-118">**Object Manipulator (指令碼)** 元件</span><span class="sxs-lookup"><span data-stu-id="8c6ad-118">**Object Manipulator (Script)** component</span></span>
>
> <span data-ttu-id="8c6ad-119">若要能夠以追蹤的手部 **操作** 及 **抓取物件**，該物件必須具有下列元件：</span><span class="sxs-lookup"><span data-stu-id="8c6ad-119">To be able to **manipulate** and **grab an object with tracked hands**, the object must have the following components:</span></span>
>
> * <span data-ttu-id="8c6ad-120">**Collider** 元件，例如 Box Collider</span><span class="sxs-lookup"><span data-stu-id="8c6ad-120">**Collider** component, for example, a Box Collider</span></span>
> * <span data-ttu-id="8c6ad-121">**Object Manipulator (指令碼)** 元件</span><span class="sxs-lookup"><span data-stu-id="8c6ad-121">**Object Manipulator (Script)** component</span></span>
> * <span data-ttu-id="8c6ad-122">**NearInteractionGrabbable** 元件</span><span class="sxs-lookup"><span data-stu-id="8c6ad-122">**NearInteractionGrabbable** component</span></span>

<span data-ttu-id="8c6ad-123">此外，您將設定 Rover Explorer，讓您可以將 Rover 零件放在 Rover 上，使其成為完整的 Rover 組件。</span><span class="sxs-lookup"><span data-stu-id="8c6ad-123">Additionally, you will configure the Rover Explorer so that you can place the rover parts on to the Rover to make it a complete rover assembly.</span></span>

<span data-ttu-id="8c6ad-124">在 [階層] 視窗中，展開 RoverExplorer > **RoverParts** 物件，並選取其所有子 Rover 零件物件和 **RoverAssembly** 物件，然後在 [偵測器] 視窗中，使用 [新增元件] 按鈕將下列元件新增至所有選取的物件：</span><span class="sxs-lookup"><span data-stu-id="8c6ad-124">In the Hierarchy window, expand the RoverExplorer > **RoverParts** object and select all its child rover part objects and the **RoverAssembly** object, then in the Inspector window, use the **Add Component** button to add the following components to all the selected objects:</span></span>

* <span data-ttu-id="8c6ad-125">**Object Manipulator (指令碼)** 元件</span><span class="sxs-lookup"><span data-stu-id="8c6ad-125">**Object Manipulator (Script)** component</span></span>
* <span data-ttu-id="8c6ad-126">**NearInteractionGrabbable** 元件</span><span class="sxs-lookup"><span data-stu-id="8c6ad-126">**NearInteractionGrabbable** component</span></span>
* <span data-ttu-id="8c6ad-127">**Part Assembly Controller (指令碼)** 元件</span><span class="sxs-lookup"><span data-stu-id="8c6ad-127">**Part Assembly Controller (Script)** component</span></span>

![已選取 RoverAssembly 和所有 Rover 組件物件並已新增元件的 Unity](images/mr-learning-base/base-07-section1-step1-1.png)

> [!TIP]
> <span data-ttu-id="8c6ad-129">若要選取非連續的多個物件，請按住 CTRL 鍵並使用滑鼠選取任何物件。</span><span class="sxs-lookup"><span data-stu-id="8c6ad-129">To select multiple objects that are not next to each other, press-and-hold the CTRL key while using the mouse to select any object.</span></span>

> [!NOTE]
> <span data-ttu-id="8c6ad-130">當您加入物件操作工具 (腳本時) ，在此情況下，會自動加入條件約束管理員 (腳本) ，因為物件操作工具 (腳本) 相依于它。</span><span class="sxs-lookup"><span data-stu-id="8c6ad-130">When you add a Object Manipulator (Script), in this case, the Constraint Manager (Script) is automatically added because Object Manipulator (Script) depends on it.</span></span>

> [!NOTE]
> <span data-ttu-id="8c6ad-131">基於本教學課程的目的，碰撞器 (Collider) 已新增至 Rover 零件。</span><span class="sxs-lookup"><span data-stu-id="8c6ad-131">For the purpose of this tutorial, colliders have already been added to the rover parts.</span></span> <span data-ttu-id="8c6ad-132">若要深入了解碰撞器，您可以造訪 Unity 的<a href="https://docs.unity3d.com/Manual/CollidersOverview.html" target="_blank">碰撞器 (Collider)</a> 文件。</span><span class="sxs-lookup"><span data-stu-id="8c6ad-132">To learn more about colliders, you can visit Unity's <a href="https://docs.unity3d.com/Manual/CollidersOverview.html" target="_blank">Collider</a> documentation.</span></span>

> [!NOTE]
> <span data-ttu-id="8c6ad-133">Part Assembly Controller (指令碼) 不是 MRTK 的一部分，但已包含在教學課程資產中。</span><span class="sxs-lookup"><span data-stu-id="8c6ad-133">The Part Assembly Controller (Script) is not part of the MRTK but was included with the tutorial assets.</span></span>

<span data-ttu-id="8c6ad-134">在仍選取所有 Rover 零件物件和 RoverAssembly 物件的情況下，在 [偵測器] 視窗中，設定 **Object Manipulator (指令碼)** 元件，如下所示：</span><span class="sxs-lookup"><span data-stu-id="8c6ad-134">With all the rover part objects and the RoverAssembly object still selected, in the Inspector window, configure the **Object Manipulator (Script)** component as follows:</span></span>

* <span data-ttu-id="8c6ad-135">從 [兩手操作類型] 下拉式清單中，取消核取 [縮放]，只啟用 [移動] 和 [選轉]</span><span class="sxs-lookup"><span data-stu-id="8c6ad-135">From the **Two Handed Manipulation Type** dropdown, uncheck the Scale, so only **Move** and **Rotate** is enabled</span></span>

![已設定 [雙手操作類型] 的 Unity](images/mr-learning-base/base-07-section1-step1-2.png)

> [!NOTE]
> <span data-ttu-id="8c6ad-137">此時，您已針對所有 Rover 零件物件和 RoverAssembly 物件啟用物件操作。</span><span class="sxs-lookup"><span data-stu-id="8c6ad-137">At this point, you have enabled object manipulation for all the rover part objects and the RoverAssembly object.</span></span>

<span data-ttu-id="8c6ad-138">在 [專案] 視窗中，流覽至 [**封裝**  >  **混合現實工具組標準資產**]  >  **音訊** 資料夾以找出音訊剪輯：</span><span class="sxs-lookup"><span data-stu-id="8c6ad-138">In the Project window, navigate to **Packages** > **Mixed Reality Toolkit Standard Assets** > **Audio** folder to locate the audio clips:</span></span>

![已選取 [音訊] 資料夾的 Unity [專案] 視窗](images/mr-learning-base/base-07-section1-step1-3.png)

<span data-ttu-id="8c6ad-140">在 [階層] 視窗中，重新選取所有 **Rover 零件物件**，然後在 [偵測器] 視窗中，使用 [新增元件] 按鈕來新增 **音訊來源** 元件，並進行以下設定：</span><span class="sxs-lookup"><span data-stu-id="8c6ad-140">In the Hierarchy window, reselect all the **rover part objects**, then in the Inspector window, use the **Add Component** button to add the **Audio Sources** component and configure it as follows:</span></span>

* <span data-ttu-id="8c6ad-141">將 **MRTK_Scale_Start** 音訊剪輯指派給 **AudioClip** 欄位</span><span class="sxs-lookup"><span data-stu-id="8c6ad-141">Assign the **MRTK_Scale_Start** audio clip to the **AudioClip** field</span></span>
* <span data-ttu-id="8c6ad-142">取消核取 [喚醒時播放] 核取方塊</span><span class="sxs-lookup"><span data-stu-id="8c6ad-142">Uncheck the **Play On Awake** checkbox</span></span>
* <span data-ttu-id="8c6ad-143">將 [空間混合] 變更為 1</span><span class="sxs-lookup"><span data-stu-id="8c6ad-143">Change **Spatial Blend** to 1</span></span>

![已選取所有 Rover 組件並已新增和設定音訊來源元件的 Unity](images/mr-learning-base/base-07-section1-step1-4.png)

<span data-ttu-id="8c6ad-145">在 [階層] 視窗中，展開 RoverAssembly > RoverModel_PlacementHints_XRay > **Parts_PlacementHints** 物件，以顯示所有位置提示物件，選取第一個 Rover 零件 RoverParts > **Camera_Part**，然後設定 **Part Assembly Controller (指令碼)** 元件，如下所示：</span><span class="sxs-lookup"><span data-stu-id="8c6ad-145">In the Hierarchy window, expand the RoverAssembly > RoverModel_PlacementHints_XRay > **Parts_PlacementHints** object to reveal all of the placement hint objects, then select the first rover part, RoverParts > **Camera_Part**, and configure the **Part Assembly Controller (Script)** component as follows:</span></span>

* <span data-ttu-id="8c6ad-146">將 **Camera_PlacementHint** 物件指派給 [要放置的位置] 欄位</span><span class="sxs-lookup"><span data-stu-id="8c6ad-146">Assign the **Camera_PlacementHint** object to the **Location To Place** field</span></span>

![已設定 Camera_Part PartAssemblyController 元件的 Unity](images/mr-learning-base/base-07-section1-step1-5.png)

<span data-ttu-id="8c6ad-148">針對其餘每個 Rover 零件物件和 RoverAssembly 物件 **重複** 此步驟，以設定 **Part Assembly Controller (指令碼)** 元件，如下所示：</span><span class="sxs-lookup"><span data-stu-id="8c6ad-148">**Repeat** this step for each of the remaining rover part objects and the RoverAssembly object to configure the **Part Assembly Controller (Script)** component as follows:</span></span>

* <span data-ttu-id="8c6ad-149">針對 **Generator_Part**，將 **Generator_PlacementHint** 物件指派給 [要放置的位置] 欄位</span><span class="sxs-lookup"><span data-stu-id="8c6ad-149">For the **Generator_Part**, assign the **Generator_PlacementHint** object to the **Location To Place** field</span></span>
* <span data-ttu-id="8c6ad-150">針對 **Lights_Part**，將 **Lights_PlacementHint** 物件指派給 [要放置的位置] 欄位</span><span class="sxs-lookup"><span data-stu-id="8c6ad-150">For the **Lights_Part**, assign the **Lights_PlacementHint** object to the **Location To Place** field</span></span>
* <span data-ttu-id="8c6ad-151">針對 **UHFAntenna_Part**，將 **UHFAntenna_PlacementHint** 物件指派給 [要放置的位置] 欄位</span><span class="sxs-lookup"><span data-stu-id="8c6ad-151">For the **UHFAntenna_Part**, assign the **UHFAntenna_PlacementHint** object to the **Location To Place** field</span></span>
* <span data-ttu-id="8c6ad-152">針對 **Spectrometer_Part**，將 **Spectrometer_PlacementHint** 物件指派給 [要放置的位置] 欄位</span><span class="sxs-lookup"><span data-stu-id="8c6ad-152">For the **Spectrometer_Part**, assign the **Spectrometer_PlacementHint** object to the **Location To Place** field</span></span>
* <span data-ttu-id="8c6ad-153">針對 **RoverAssembly**，將物件本身 (也就是相同的 **RoverAssembly** 物件) 指派給 [要放置的位置] 欄位</span><span class="sxs-lookup"><span data-stu-id="8c6ad-153">For the **RoverAssembly**, assign the object itself, i.e. the same **RoverAssembly** object, to the **Location To Place** field</span></span>

<span data-ttu-id="8c6ad-154">在 [階層] 視窗中，選取 [RoverExplorer] > [按鈕] > [重設] 按鈕物件，然後在 [偵測器] 視窗中，設定可互動的 **OnClick ()** 事件，如下所示：</span><span class="sxs-lookup"><span data-stu-id="8c6ad-154">In the Hierarchy window, select the RoverExplorer > Buttons > **Reset** button object, then in the Inspector window, configure the Interactable **OnClick ()** event as follows:</span></span>

* <span data-ttu-id="8c6ad-155">將 **RoverAssembly** 物件指派給 [無 (物件)] 欄位</span><span class="sxs-lookup"><span data-stu-id="8c6ad-155">Assign the **RoverAssembly** object to the **None (Object)** field</span></span>
* <span data-ttu-id="8c6ad-156">從 [沒有函式] 下拉式清單中，選取 [PartAssemblyController] > [ResetPlacement ()]，以將此函式設定為觸發事件時所要執行的動作</span><span class="sxs-lookup"><span data-stu-id="8c6ad-156">From the **No Function** dropdown, select **PartAssemblyController** > **ResetPlacement ()** to set this function as the action to be executed when the event is triggered</span></span>

![已設定 [重設] 按鈕物件 OnClick 事件的 Unity](images/mr-learning-base/base-07-section1-step1-6.png)

<span data-ttu-id="8c6ad-158">如果您現在進入遊戲模式，您可以使用近或遠的互動來將 Rover 零件放在 Rover 上。</span><span class="sxs-lookup"><span data-stu-id="8c6ad-158">If you now enter Game mode, you can use near or far interaction to place the rover parts on to the Rover.</span></span> <span data-ttu-id="8c6ad-159">零件會在接近對應的放置提示時，貼齊位置並成為 Rover 的一部分。</span><span class="sxs-lookup"><span data-stu-id="8c6ad-159">Once the part is close to the corresponding placement hint, it will snap into place and become part of the Rover.</span></span> <span data-ttu-id="8c6ad-160">若要重設放置位置，您可以按下 [重設] 按鈕：</span><span class="sxs-lookup"><span data-stu-id="8c6ad-160">To reset the placements, you can press the Reset button:</span></span>

![按下 [重設] 按鈕的 Unity 播放模式分割檢視](images/mr-learning-base/base-07-section1-step1-7.png)

<span data-ttu-id="8c6ad-162">若要深入了解 Object Manipulator (物件操作工具) 元件及其相關聯的屬性，您可以瀏覽 [MRTK 文件入口網站](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/)中的 [Object Manipulator (物件操作工具)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectManipulator.html) 指南。</span><span class="sxs-lookup"><span data-stu-id="8c6ad-162">To learn more about the Object Manipulator component and its associated properties, you can visit the [Object Manipulator](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectManipulator.html) guide in the [MRTK Documentation Portal](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/).</span></span>

## <a name="adding-bounds-control"></a><span data-ttu-id="8c6ad-163">加入界限控制項</span><span class="sxs-lookup"><span data-stu-id="8c6ad-163">Adding Bounds Control</span></span>

<span data-ttu-id="8c6ad-164">界限控制項可提供可用於縮放和旋轉的控制碼，讓您更輕鬆且更直覺地操作物件。</span><span class="sxs-lookup"><span data-stu-id="8c6ad-164">Bounds Control makes it easier and more intuitive to manipulate objects with one hand for both near and far interaction by providing handles that can be used for scaling and rotating.</span></span>

<span data-ttu-id="8c6ad-165">在此範例中，您會將 BoundsControl 新增至 RoverExplorer 物件，如此即可輕鬆地移動、旋轉和縮放整個體驗。</span><span class="sxs-lookup"><span data-stu-id="8c6ad-165">In this example, you will add a BoundsControl to the RoverExplorer object so the whole experience can easily be moved, rotated, and scaled.</span></span> <span data-ttu-id="8c6ad-166">此外，您將設定功能表，讓您可以開啟和關閉界限控制項。</span><span class="sxs-lookup"><span data-stu-id="8c6ad-166">Additionally, you will configure the Menu so you can turn the Bounds Control on and off.</span></span>

<span data-ttu-id="8c6ad-167">在 [階層] 視窗中，選取 **RoverExplorer** 物件，然後在 [偵測器] 視窗中，使用 [新增元件] 按鈕來新增下列元件：</span><span class="sxs-lookup"><span data-stu-id="8c6ad-167">In the Hierarchy window, select the **RoverExplorer** object, then in the Inspector window, use the **Add Component** button to add the following components:</span></span>

* <span data-ttu-id="8c6ad-168">**BoundsControl** 元件</span><span class="sxs-lookup"><span data-stu-id="8c6ad-168">**BoundsControl** component</span></span>
* <span data-ttu-id="8c6ad-169">**Object Manipulator (指令碼)** 元件</span><span class="sxs-lookup"><span data-stu-id="8c6ad-169">**Object Manipulator (Script)** component</span></span>

<span data-ttu-id="8c6ad-170">然後 **取消** 核取所有元件旁的核取方塊，使其預設為 **停用** ：</span><span class="sxs-lookup"><span data-stu-id="8c6ad-170">Then **uncheck** the checkbox next to all the components to make them **disabled** by default:</span></span>

![已選取 RoverExplorer 物件並已新增和停用元件的 Unity](images/mr-learning-base/base-07-section2-step1-1.png)

> [!NOTE]
> <span data-ttu-id="8c6ad-172">界限控制項視覺效果是在執行時間建立的，因此，在您進入遊戲模式之前看不到。</span><span class="sxs-lookup"><span data-stu-id="8c6ad-172">The Bounds Control visualization is created at runtime and, therefore, not visible before you enter Game mode.</span></span>

> [!NOTE]
><span data-ttu-id="8c6ad-173">物件操作工具 (腳本) 會自動加入條件約束管理員 (腳本) </span><span class="sxs-lookup"><span data-stu-id="8c6ad-173">The Object Manipulator (Script) automatically adds Constraint Manager (Script)</span></span>

<span data-ttu-id="8c6ad-174">在 [階層] 視窗中，展開功能表 > **ButtonCollection** 物件，以顯示四個按鈕，並將第三個按鈕重新命名為 **BoundsControl_Enable**，然後在 [偵測器] 視窗中，設定按鈕設定協助程式 **(腳本)** 元件，如下所示：</span><span class="sxs-lookup"><span data-stu-id="8c6ad-174">In the Hierarchy window, expand the Menu > **ButtonCollection** object to reveal the four buttons and rename the third button to **BoundsControl_Enable**, then in the Inspector window, configure the **Button Config Helper (Script)** component as follows:</span></span>

* <span data-ttu-id="8c6ad-175">將 [主要標籤文字] 變更為 [啟用]</span><span class="sxs-lookup"><span data-stu-id="8c6ad-175">Change the **Main Label Text** to **Enable**</span></span>
* <span data-ttu-id="8c6ad-176">將 **RoverExplorer** 物件指派給 [無 (物件)] 欄位</span><span class="sxs-lookup"><span data-stu-id="8c6ad-176">Assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="8c6ad-177">從 [**沒有** 函式] 下拉式清單中，選取 [ **BoundsControl**  >  **bool Enabled** ]，以在觸發事件時更新此屬性值</span><span class="sxs-lookup"><span data-stu-id="8c6ad-177">From the **No Function** dropdown, select **BoundsControl** > **bool Enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="8c6ad-178">確認 **已核取** 引數核取方塊</span><span class="sxs-lookup"><span data-stu-id="8c6ad-178">Verify that the argument checkbox is **checked**</span></span>
* <span data-ttu-id="8c6ad-179">按一下小型 **+** 圖示，以新增另一個事件</span><span class="sxs-lookup"><span data-stu-id="8c6ad-179">Click the small **+** icon to add another event</span></span>
* <span data-ttu-id="8c6ad-180">將 **RoverExplorer** 物件指派給 [無 (物件)] 欄位</span><span class="sxs-lookup"><span data-stu-id="8c6ad-180">Assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="8c6ad-181">從 [沒有函式] 下拉式清單中，選取 [ObjectManipulator] > [bool Enabled] 以在觸發事件時更新此屬性值</span><span class="sxs-lookup"><span data-stu-id="8c6ad-181">From the **No Function** dropdown, select **ObjectManipulator** > **bool Enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="8c6ad-182">確認 **已核取** 引數核取方塊</span><span class="sxs-lookup"><span data-stu-id="8c6ad-182">Verify that the argument checkbox is **checked**</span></span>
* <span data-ttu-id="8c6ad-183">將 **圖示** 保留為「具有界限控制項的 cube」圖示</span><span class="sxs-lookup"><span data-stu-id="8c6ad-183">Leave the **Icon** as the 'cube with bounds control' icon</span></span>

![已選取 BoundsControl_Enable 按鈕物件和設定按鈕設定協助程式元件的 Unity](images/mr-learning-base/base-07-section2-step1-2.png)

<span data-ttu-id="8c6ad-185">將 [向下] 和 [最後] 按鈕重新命名為 **BoundsControl_Disable**，然後在 [偵測器] 視窗中，設定 **按鈕設定 Helper (腳本)** 元件，如下所示：</span><span class="sxs-lookup"><span data-stu-id="8c6ad-185">Rename the forth and last button to **BoundsControl_Disable**, then in the Inspector window, configure the **Button Config Helper (Script)** component as follows:</span></span>

* <span data-ttu-id="8c6ad-186">將 [主要標籤文字] 變更為 [停用]</span><span class="sxs-lookup"><span data-stu-id="8c6ad-186">Change the **Main Label Text** to **Disable**</span></span>
* <span data-ttu-id="8c6ad-187">將 **RoverExplorer** 物件指派給 [無 (物件)] 欄位</span><span class="sxs-lookup"><span data-stu-id="8c6ad-187">Assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="8c6ad-188">從 [**沒有** 函式] 下拉式清單中，選取 [ **BoundsControl**  >  **bool Enabled** ]，以在觸發事件時更新此屬性值</span><span class="sxs-lookup"><span data-stu-id="8c6ad-188">From the **No Function** dropdown, select **BoundsControl** > **bool Enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="8c6ad-189">確認 **未核取** 引數核取方塊</span><span class="sxs-lookup"><span data-stu-id="8c6ad-189">Verify that the argument checkbox is **unchecked**</span></span>
* <span data-ttu-id="8c6ad-190">按一下小型 **+** 圖示，以新增另一個事件</span><span class="sxs-lookup"><span data-stu-id="8c6ad-190">Click the small **+** icon to add another event</span></span>
* <span data-ttu-id="8c6ad-191">將 **RoverExplorer** 物件指派給 [無 (物件)] 欄位</span><span class="sxs-lookup"><span data-stu-id="8c6ad-191">Assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="8c6ad-192">從 [沒有函式] 下拉式清單中，選取 [ObjectManipulator] > [bool Enabled] 以在觸發事件時更新此屬性值</span><span class="sxs-lookup"><span data-stu-id="8c6ad-192">From the **No Function** dropdown, select **ObjectManipulator** > **bool Enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="8c6ad-193">確認 **未核取** 引數核取方塊</span><span class="sxs-lookup"><span data-stu-id="8c6ad-193">Verify that the argument checkbox is **unchecked**</span></span>
* <span data-ttu-id="8c6ad-194">將 **圖示** 變更為「具有界限控制項的 cube」圖示</span><span class="sxs-lookup"><span data-stu-id="8c6ad-194">Change the **Icon** to the 'cube with bounds control" icon</span></span>

![已選取 BoundsControl_Disable 按鈕物件和設定按鈕設定協助程式元件的 Unity](images/mr-learning-base/base-07-section2-step1-3.png)

<span data-ttu-id="8c6ad-196">如果您現在進入遊戲模式，並按一下 [啟用] 按鈕來啟用界限控制項，則可以使用接近或遠的互動來移動、旋轉和縮放界限控制項，然後使用 [停用] 按鈕再次停用界限控制項：</span><span class="sxs-lookup"><span data-stu-id="8c6ad-196">If you now enter Game mode and enable the Bounds Control by clicking the Enable button, you can use near or far interaction to move, rotate, and scale the Bounds Control, and use the Disable button to disable the Bounds Control again:</span></span>

![要操作界限控制項的 Unity 播放模式分割視圖](images/mr-learning-base/base-07-section2-step1-4.png)

<span data-ttu-id="8c6ad-198">若要深入瞭解界限控制元件與其相關聯的屬性，您可以造訪[MRTK 檔入口網站](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/)中的[界限控制](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundsControl.html)指南。</span><span class="sxs-lookup"><span data-stu-id="8c6ad-198">To learn more about the Bounds Control component and its associated properties, you can visit the [Bounds Control](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundsControl.html) guide in the [MRTK Documentation Portal](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/).</span></span>

## <a name="congratulations"></a><span data-ttu-id="8c6ad-199">恭喜！</span><span class="sxs-lookup"><span data-stu-id="8c6ad-199">Congratulations</span></span>

<span data-ttu-id="8c6ad-200">在本教學課程中，您已了解如何啟用 3D 物件的遠近操作，以及如何限制允許的操作類型。</span><span class="sxs-lookup"><span data-stu-id="8c6ad-200">In this tutorial, you learned how to enable near and far manipulation for 3D objects and how to limit the allowed types of manipulation.</span></span> <span data-ttu-id="8c6ad-201">您也已瞭解如何在3D 物件周圍新增界限控制項，讓您更輕鬆地控制物件操作。</span><span class="sxs-lookup"><span data-stu-id="8c6ad-201">You also learned how to add Bounds Control around 3D objects to make it easier to control the object manipulation.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="8c6ad-202">下一個教學課程：8.使用眼球追蹤</span><span class="sxs-lookup"><span data-stu-id="8c6ad-202">Next Tutorial: 8. Using eye-tracking</span></span>](mr-learning-base-08.md)
