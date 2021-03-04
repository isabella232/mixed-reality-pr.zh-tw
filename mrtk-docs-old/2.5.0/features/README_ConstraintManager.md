---
title: README_ConstraintManager
description: MRTK 中的條件約束管理員總覽
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: 593313e1b2af7520550e6e9bbd9cb17e4337312d
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/03/2021
ms.locfileid: "101779614"
---
# <a name="constraint-manager"></a><span data-ttu-id="7bb57-104">條件約束管理員</span><span class="sxs-lookup"><span data-stu-id="7bb57-104">Constraint manager</span></span>

<span data-ttu-id="7bb57-105">條件約束管理員可讓您將一組條件約束元件套用至轉換。</span><span class="sxs-lookup"><span data-stu-id="7bb57-105">The constraint manager allows to apply a set of constraint components to a transform.</span></span> <span data-ttu-id="7bb57-106">[`TransformConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.TransformConstraint)附加至遊戲物件的類型元件可以納入考慮。</span><span class="sxs-lookup"><span data-stu-id="7bb57-106">Components of type [`TransformConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.TransformConstraint) that are attached to the game object can be taken into consideration.</span></span>
<span data-ttu-id="7bb57-107">根據預設，條件約束管理員會自動收集所有附加至遊戲物件的 [條件約束元件](#transform-constraints) ，並將其套用至處理的轉換。</span><span class="sxs-lookup"><span data-stu-id="7bb57-107">Per default, constraint manager will automatically collect all [constraint components](#transform-constraints) attached to the game object and apply them to processed transforms.</span></span>
<span data-ttu-id="7bb57-108">不過，使用者可以選擇手動設定套用的條件約束清單，而只允許套用附加條件約束的子集。</span><span class="sxs-lookup"><span data-stu-id="7bb57-108">However users can opt for configuring the list of applied constraints manually and allowing only a subset of attached constraints to be applied.</span></span>

<span data-ttu-id="7bb57-109">目前，下列 MRTK UX 元素支援條件約束管理員：</span><span class="sxs-lookup"><span data-stu-id="7bb57-109">Currently the following MRTK UX elements are supporting constraint manager:</span></span>

- [<span data-ttu-id="7bb57-110">界限控制項</span><span class="sxs-lookup"><span data-stu-id="7bb57-110">Bounds control</span></span>](README_BoundsControl.md)
- [<span data-ttu-id="7bb57-111">物件操作工具</span><span class="sxs-lookup"><span data-stu-id="7bb57-111">Object manipulator</span></span>](README_ObjectManipulator.md)

## <a name="inspector-properties-and-fields"></a><span data-ttu-id="7bb57-112">偵測器屬性和欄位</span><span class="sxs-lookup"><span data-stu-id="7bb57-112">Inspector properties and fields</span></span>

<span data-ttu-id="7bb57-113">條件約束管理員可在兩種模式中運作：</span><span class="sxs-lookup"><span data-stu-id="7bb57-113">Constraint manager can be operated in two modes:</span></span>

- <span data-ttu-id="7bb57-114">自動條件約束選取</span><span class="sxs-lookup"><span data-stu-id="7bb57-114">Auto constraint selection</span></span>
- <span data-ttu-id="7bb57-115">手動條件約束選取</span><span class="sxs-lookup"><span data-stu-id="7bb57-115">Manual constraint selection</span></span>

### <a name="auto-constraint-selection"></a><span data-ttu-id="7bb57-116">自動條件約束選取</span><span class="sxs-lookup"><span data-stu-id="7bb57-116">Auto constraint selection</span></span>

<img src="Images/ConstraintManager/AutoSelection.png" width="600" alt="Auto Selection">

<span data-ttu-id="7bb57-117">[條件約束管理員] 的預設模式是 [自動條件約束選取]，將會提供所有附加條件約束元件的清單，以及 [ [移至按鈕](#go-to-component) ] 和 [ [新增條件約束] 按鈕](#add-constraint-to-game-object)。</span><span class="sxs-lookup"><span data-stu-id="7bb57-117">The default mode of constraint manager, auto constraint selection, will provide a list of all attached constraint components as well as [go to buttons](#go-to-component) and an [add constraint button](#add-constraint-to-game-object).</span></span>

#### <a name="add-constraint-to-game-object"></a><span data-ttu-id="7bb57-118">將條件約束新增至遊戲物件</span><span class="sxs-lookup"><span data-stu-id="7bb57-118">Add constraint to game object</span></span>

<span data-ttu-id="7bb57-119">此按鈕可讓條件約束元件直接從條件約束管理員偵測器加入。</span><span class="sxs-lookup"><span data-stu-id="7bb57-119">This button allows a constraint component to be added directly from the constraint manager inspector.</span></span> <span data-ttu-id="7bb57-120">專案中應該會顯示專案中的所有條件約束類型。</span><span class="sxs-lookup"><span data-stu-id="7bb57-120">All constraint types in a project should be visible here.</span></span> <span data-ttu-id="7bb57-121">如需詳細資訊，請參閱 [轉換條件約束](#transform-constraints) 。</span><span class="sxs-lookup"><span data-stu-id="7bb57-121">See [transform constraints](#transform-constraints) for more info.</span></span>

#### <a name="go-to-component"></a><span data-ttu-id="7bb57-122">移至元件</span><span class="sxs-lookup"><span data-stu-id="7bb57-122">Go to component</span></span>

<span data-ttu-id="7bb57-123">在此物件上找到的所有條件約束，都會在這裡列出，並顯示 [ *移至元件* ] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="7bb57-123">All constraints found on the object wil be listed here with a *Go to component* button.</span></span> <span data-ttu-id="7bb57-124">此按鈕會讓偵測器滾動至選取的條件約束元件，以便進行設定。</span><span class="sxs-lookup"><span data-stu-id="7bb57-124">This button will cause the inspector to scroll to the selected constraint component so that it can be configured.</span></span>

### <a name="manual-constraint-selection"></a><span data-ttu-id="7bb57-125">手動條件約束選取</span><span class="sxs-lookup"><span data-stu-id="7bb57-125">Manual constraint selection</span></span>

<img src="Images/ConstraintManager/ManualSelection.png" width="600" alt="Manual Selection">

<span data-ttu-id="7bb57-126">如果條件約束管理員設定為手動模式，則只會處理條件約束清單中連結的條件約束，並將其套用至轉換。</span><span class="sxs-lookup"><span data-stu-id="7bb57-126">If constraint manager is set to manual mode, only constraints that are linked in the constraint list are processed and applied to the transform.</span></span> <span data-ttu-id="7bb57-127">顯示的清單只會顯示使用者選取的條件約束，以及移 [至按鈕](#go-to-component) 或選項以移除或新增專案。</span><span class="sxs-lookup"><span data-stu-id="7bb57-127">The list displayed will only show the user selected constraints as well as [go to buttons](#go-to-component) or options to remove or add entries.</span></span>
<span data-ttu-id="7bb57-128">當第一次啟用手動模式時，條件約束管理員會將所有可用的元件填入清單，做為選取附加條件約束元件的起點。</span><span class="sxs-lookup"><span data-stu-id="7bb57-128">When enabling manual mode for the first time, constraint manager will populate the list will all available components as a starting point for selecting attached constraint components.</span></span>

### <a name="remove-entry"></a><span data-ttu-id="7bb57-129">移除專案</span><span class="sxs-lookup"><span data-stu-id="7bb57-129">Remove entry</span></span>

<span data-ttu-id="7bb57-130">這會從手動選取的清單中移除專案。</span><span class="sxs-lookup"><span data-stu-id="7bb57-130">This removes the entry from the manually selected list.</span></span> <span data-ttu-id="7bb57-131">請注意，這個選項不會從遊戲物件中移除條件約束元件。</span><span class="sxs-lookup"><span data-stu-id="7bb57-131">Note that this option will not remove the constraint component from the game object.</span></span> <span data-ttu-id="7bb57-132">條件約束元件一律需要手動移除，以確保不會意外中斷任何參考此元件的其他元件。</span><span class="sxs-lookup"><span data-stu-id="7bb57-132">Constraint components always need to be removed manually to ensure not accidentally breaking any other component referring to this component.</span></span>

### <a name="add-entry"></a><span data-ttu-id="7bb57-133">新增專案</span><span class="sxs-lookup"><span data-stu-id="7bb57-133">Add entry</span></span>

<span data-ttu-id="7bb57-134">[新增專案] 會開啟下拉式清單，顯示尚未在手動清單中的所有可用條件約束元件。</span><span class="sxs-lookup"><span data-stu-id="7bb57-134">Add entry will open a dropdown showing all available constraint components that are not in the manual list yet.</span></span> <span data-ttu-id="7bb57-135">按一下該元件將會新增至手動條件約束選取專案的任何專案。</span><span class="sxs-lookup"><span data-stu-id="7bb57-135">By clicking on any of the entries that component will be added to the manual constraint selection.</span></span>

### <a name="add-new-constraint"></a><span data-ttu-id="7bb57-136">新增條件約束</span><span class="sxs-lookup"><span data-stu-id="7bb57-136">Add new constraint</span></span>

<span data-ttu-id="7bb57-137">此選項會將所選類型的元件新增至遊戲物件，並將新建立的條件約束元件加入至手動條件約束清單。</span><span class="sxs-lookup"><span data-stu-id="7bb57-137">This option will add a component of the selected type to the game object and add the newly created constraint component to the manual constraint list.</span></span>

## <a name="transform-constraints"></a><span data-ttu-id="7bb57-138">轉換條件約束</span><span class="sxs-lookup"><span data-stu-id="7bb57-138">Transform constraints</span></span>

<span data-ttu-id="7bb57-139">條件約束可以用來限制操作的方式。</span><span class="sxs-lookup"><span data-stu-id="7bb57-139">Constraints can be used to limit manipulation in some way.</span></span> <span data-ttu-id="7bb57-140">例如，有些應用程式可能需要輪替，但物件也需要保持垂直。</span><span class="sxs-lookup"><span data-stu-id="7bb57-140">For example, some applications may require rotation, but also require that the object remain upright.</span></span> <span data-ttu-id="7bb57-141">在此情況下，您 `RotationAxisConstraint` 可以將加入至物件，並用來將旋轉限制為 y 軸旋轉。</span><span class="sxs-lookup"><span data-stu-id="7bb57-141">In this case, a `RotationAxisConstraint` can be added to the object and used to limit rotation to y-axis rotation.</span></span> <span data-ttu-id="7bb57-142">MRTK 提供許多條件約束，如下所述。</span><span class="sxs-lookup"><span data-stu-id="7bb57-142">MRTK provides a number of constraints, all of which are described below.</span></span>

<span data-ttu-id="7bb57-143">您也可以定義新的條件約束，並使用它們來建立某些應用程式可能需要的獨特操作行為。</span><span class="sxs-lookup"><span data-stu-id="7bb57-143">It is also possible to define new constraints and use them to create unique manipulation behaviour that may be needed for some applications.</span></span> <span data-ttu-id="7bb57-144">若要這樣做，請建立一個繼承自 [`TransformConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.TransformConstraint) 的腳本，並執行抽象 `ConstraintType` 屬性和抽象 `ApplyConstraint` 方法。</span><span class="sxs-lookup"><span data-stu-id="7bb57-144">To do this, create a script that inherits from [`TransformConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.TransformConstraint) and implement the abstract `ConstraintType` property and the abstract `ApplyConstraint` method.</span></span> <span data-ttu-id="7bb57-145">將新的條件約束加入至物件時，它應該會以定義的方式來限制操作。</span><span class="sxs-lookup"><span data-stu-id="7bb57-145">Upon adding a new constraint to the object, it should constrain manipulation in the way that was defined.</span></span> <span data-ttu-id="7bb57-146">這個新的條件約束也應該顯示在 [條件約束管理員 [自動選取](#auto-constraint-selection) ] 或 [以手動模式 [加入專案](#add-entry) ] 下拉式清單中。</span><span class="sxs-lookup"><span data-stu-id="7bb57-146">This new constraint should also show in the constraint manager [auto selection](#auto-constraint-selection) or [add entry](#add-entry) dropdown in manual mode.</span></span>

<span data-ttu-id="7bb57-147">MRTK 提供的所有條件約束都會共用下列屬性：</span><span class="sxs-lookup"><span data-stu-id="7bb57-147">All of the constraints provided by MRTK share the following properties:</span></span>

#### <a name="hand-type"></a><span data-ttu-id="7bb57-148">手型別</span><span class="sxs-lookup"><span data-stu-id="7bb57-148">Hand Type</span></span>

<span data-ttu-id="7bb57-149">指定是否要將條件約束用於一或兩種類型的操作。</span><span class="sxs-lookup"><span data-stu-id="7bb57-149">Specifies whether the constraint is used for one handed, two handed or both kinds of manipulation.</span></span> <span data-ttu-id="7bb57-150">因為這個屬性是一個旗標，所以可以選取兩個選項。</span><span class="sxs-lookup"><span data-stu-id="7bb57-150">Because this property is a flag, both options can be selected.</span></span>

- <span data-ttu-id="7bb57-151">*一個右手*：條件約束會在一次執行時使用，如果選取的話。</span><span class="sxs-lookup"><span data-stu-id="7bb57-151">*One handed*: Constraint will be used during one handed manipulation if selected.</span></span>
- <span data-ttu-id="7bb57-152">*兩個右手*：條件約束將在兩個強制操作期間使用（如果選取）。</span><span class="sxs-lookup"><span data-stu-id="7bb57-152">*Two handed*: Constraint will be used during two handed manipulation if selected.</span></span>

#### <a name="proximity-type"></a><span data-ttu-id="7bb57-153">鄰近型別</span><span class="sxs-lookup"><span data-stu-id="7bb57-153">Proximity Type</span></span>

<span data-ttu-id="7bb57-154">指定是否要將條件約束用於接近、遠或兩種類型的操作。</span><span class="sxs-lookup"><span data-stu-id="7bb57-154">Specifies whether the constraint is used for near, far or both kinds of manipulation.</span></span> <span data-ttu-id="7bb57-155">因為這個屬性是一個旗標，所以可以選取兩個選項。</span><span class="sxs-lookup"><span data-stu-id="7bb57-155">Because this property is a flag, both options can be selected.</span></span>

- <span data-ttu-id="7bb57-156">*Near*：若選取此選項，則會在接近操作期間使用條件約束。</span><span class="sxs-lookup"><span data-stu-id="7bb57-156">*Near*: Constraint will be used during near manipulation if selected.</span></span>
- <span data-ttu-id="7bb57-157">*目前為止*：如果選取，就會在目前的操作期間使用條件約束。</span><span class="sxs-lookup"><span data-stu-id="7bb57-157">*Far*: Constraint will be used during far manipulation if selected.</span></span>

### <a name="faceuserconstraint"></a><span data-ttu-id="7bb57-158">FaceUserConstraint</span><span class="sxs-lookup"><span data-stu-id="7bb57-158">FaceUserConstraint</span></span>

<img src="Images/ObjectManipulator/MRTK_Constraint_FaceUser.gif" width="400" alt="Constraint FaceUser">

<span data-ttu-id="7bb57-159">當這個條件約束附加到物件時，旋轉將會受到限制，因此物件一律會面對使用者。</span><span class="sxs-lookup"><span data-stu-id="7bb57-159">When this constraint is attached to an object, rotation will be limited so that object will always face the user.</span></span> <span data-ttu-id="7bb57-160">這對平板或面板很有用。</span><span class="sxs-lookup"><span data-stu-id="7bb57-160">This is useful for slates or panels.</span></span> <span data-ttu-id="7bb57-161">的屬性如下所示 `FaceUserConstraint` ：</span><span class="sxs-lookup"><span data-stu-id="7bb57-161">The properties for `FaceUserConstraint` are as follows:</span></span>

#### <a name="face-away"></a><span data-ttu-id="7bb57-162">臉部離開</span><span class="sxs-lookup"><span data-stu-id="7bb57-162">Face away</span></span>

<span data-ttu-id="7bb57-163">若為 true，則物件會離開使用者。</span><span class="sxs-lookup"><span data-stu-id="7bb57-163">Object faces away from the user if true.</span></span>

### <a name="fixeddistanceconstraint"></a><span data-ttu-id="7bb57-164">FixedDistanceConstraint</span><span class="sxs-lookup"><span data-stu-id="7bb57-164">FixedDistanceConstraint</span></span>

<img src="Images/ObjectManipulator/MRTK_Constraint_FixedDistance.gif" width="400" alt="Constraint Fixed Distance">

<span data-ttu-id="7bb57-165">這個條件約束會修正操作物件與操作啟動時的另一個物件轉換之間的距離。</span><span class="sxs-lookup"><span data-stu-id="7bb57-165">This constraint fixes the distance between the manipulated object and another object transform on manipulation start.</span></span> <span data-ttu-id="7bb57-166">這適用于將操作物件的距離修正至 head 轉換的行為。</span><span class="sxs-lookup"><span data-stu-id="7bb57-166">This is useful for behaviour such as fixing the distance from the manipulated object to the head transform.</span></span> <span data-ttu-id="7bb57-167">的屬性如下所示 `FixedDistanceConstraint` ：</span><span class="sxs-lookup"><span data-stu-id="7bb57-167">The properties for `FixedDistanceConstraint` are as follows:</span></span>

#### <a name="constraint-transform"></a><span data-ttu-id="7bb57-168">條件約束轉換</span><span class="sxs-lookup"><span data-stu-id="7bb57-168">Constraint transform</span></span>

<span data-ttu-id="7bb57-169">這是操作物件將會有固定距離的另一個轉換。</span><span class="sxs-lookup"><span data-stu-id="7bb57-169">This is the other transform that the manipulated object will have a fixed distance to.</span></span> <span data-ttu-id="7bb57-170">預設為相機轉換。</span><span class="sxs-lookup"><span data-stu-id="7bb57-170">Defaults to the camera transform.</span></span>

### <a name="fixedrotationtouserconstraint"></a><span data-ttu-id="7bb57-171">FixedRotationToUserConstraint</span><span class="sxs-lookup"><span data-stu-id="7bb57-171">FixedRotationToUserConstraint</span></span>

<img src="Images/ObjectManipulator/MRTK_Constraint_FixedRotationToUser.gif" width="400" alt="Fixed Rotation to user">

<span data-ttu-id="7bb57-172">此條件約束會修正使用者與操作中物件之間的相對旋轉。</span><span class="sxs-lookup"><span data-stu-id="7bb57-172">This constraint fixes the relative rotation between the user and the manipulated object while it is being manipulated.</span></span> <span data-ttu-id="7bb57-173">這對平板或面板很有用，因為它可確保操作物件一律會顯示相同的臉部給使用者，如同操作開始時一樣。</span><span class="sxs-lookup"><span data-stu-id="7bb57-173">This is useful for slates or panels as it ensures that the manipulated object always shows the same face to the user as it did at the start of manipulation.</span></span> <span data-ttu-id="7bb57-174">沒有 `FixedRotationToUserConstraint` 任何唯一的屬性。</span><span class="sxs-lookup"><span data-stu-id="7bb57-174">The `FixedRotationToUserConstraint` does not have any unique properties.</span></span>

### <a name="fixedrotationtoworldconstraint"></a><span data-ttu-id="7bb57-175">FixedRotationToWorldConstraint</span><span class="sxs-lookup"><span data-stu-id="7bb57-175">FixedRotationToWorldConstraint</span></span>

<img src="Images/ObjectManipulator/MRTK_Constraint_FixedRotationToWorld.gif" width="400" alt="Fixed Rotation to world">

<span data-ttu-id="7bb57-176">此條件約束可修正操作物件在操作時的全域旋轉。</span><span class="sxs-lookup"><span data-stu-id="7bb57-176">This constraint fixes the global rotation of the manipulated object while it is being manipulated.</span></span> <span data-ttu-id="7bb57-177">如果不應該透過操作來給予任何旋轉，這項功能就很有用。</span><span class="sxs-lookup"><span data-stu-id="7bb57-177">This can be useful in cases where no rotation should be imparted by manipulation.</span></span> <span data-ttu-id="7bb57-178">沒有 `FixedRotationToWorldConstraint` 任何唯一的屬性：</span><span class="sxs-lookup"><span data-stu-id="7bb57-178">The `FixedRotationToWorldConstraint` does not have any unique properties:</span></span>

### <a name="maintainapparentsizeconstraint"></a><span data-ttu-id="7bb57-179">MaintainApparentSizeConstraint</span><span class="sxs-lookup"><span data-stu-id="7bb57-179">MaintainApparentSizeConstraint</span></span>

<img src="Images/ObjectManipulator/MRTK_Constraint_MaintainApparentSize.gif" width="400" alt="Maintain Apparent size">

<span data-ttu-id="7bb57-180">當這個條件約束附加到物件時，無論物件與使用者之間的距離為何，它都會維持與使用者相同的明顯大小 (也就是，它所占的使用者欄位的比例) 。</span><span class="sxs-lookup"><span data-stu-id="7bb57-180">When this constraint is attached to an object, no matter how far the object is from the user, it will maintain the same apparent size to the user (i.e. it will take up the same proportion of the user's field of view).</span></span> <span data-ttu-id="7bb57-181">這可以用來確保在操作時，平板或文字面板仍可讀取。</span><span class="sxs-lookup"><span data-stu-id="7bb57-181">This can be used to ensure that a slate or text panel remains readable while manipulating.</span></span> <span data-ttu-id="7bb57-182">沒有 `MaintainApparentSizeConstraint` 任何唯一的屬性：</span><span class="sxs-lookup"><span data-stu-id="7bb57-182">The `MaintainApparentSizeConstraint` does not have any unique properties:</span></span>

### <a name="moveaxisconstraint"></a><span data-ttu-id="7bb57-183">MoveAxisConstraint</span><span class="sxs-lookup"><span data-stu-id="7bb57-183">MoveAxisConstraint</span></span>

<img src="Images/ObjectManipulator/MRTK_Constraint_MoveAxis.gif" width="400" alt="Constraint Move Axis">

<span data-ttu-id="7bb57-184">這個條件約束可以用來修正可以移動操作物件的座標軸。</span><span class="sxs-lookup"><span data-stu-id="7bb57-184">This constraint can be used to fix along which axes a manipulated object can be moved.</span></span> <span data-ttu-id="7bb57-185">當您在平面表面或線條上操作物件時，這會很有用。</span><span class="sxs-lookup"><span data-stu-id="7bb57-185">This can be useful for manipulating objects over the surface of a plane, or along a line.</span></span> <span data-ttu-id="7bb57-186">的屬性如下所示 `MoveAxisConstraint` ：</span><span class="sxs-lookup"><span data-stu-id="7bb57-186">The properties for `MoveAxisConstraint` are as follows:</span></span>

#### <a name="constraint-on-movement"></a><span data-ttu-id="7bb57-187">移動時的條件約束</span><span class="sxs-lookup"><span data-stu-id="7bb57-187">Constraint on movement</span></span>

<span data-ttu-id="7bb57-188">指定要防止移動的座標軸。</span><span class="sxs-lookup"><span data-stu-id="7bb57-188">Specifies which axes to prevent movement on.</span></span> <span data-ttu-id="7bb57-189">根據預設，這些軸會是全域的，而不是本機，但可在下方變更。</span><span class="sxs-lookup"><span data-stu-id="7bb57-189">By default, these axes will be global rather than local, but this can be changed below.</span></span> <span data-ttu-id="7bb57-190">因為此屬性是旗標，所以可以選取任何數目的選項。</span><span class="sxs-lookup"><span data-stu-id="7bb57-190">Because this property is a flag, any number of options can be selected.</span></span>

- <span data-ttu-id="7bb57-191">*X 軸*：如果選取，沿著 X 軸移動會受到限制。</span><span class="sxs-lookup"><span data-stu-id="7bb57-191">*X Axis*: Movement along the x-axis is constrained if selected.</span></span>
- <span data-ttu-id="7bb57-192">*Y 軸*：如果選取，沿著 y 軸的移動會受到限制。</span><span class="sxs-lookup"><span data-stu-id="7bb57-192">*Y Axis*: Movement along the y-axis is constrained if selected.</span></span>
- <span data-ttu-id="7bb57-193">*Z 軸*：如果選取，沿著 Z 軸的移動會受到限制。</span><span class="sxs-lookup"><span data-stu-id="7bb57-193">*Z Axis*: Movement along the z-axis is constrained if selected.</span></span>

#### <a name="use-local-space-for-constraint"></a><span data-ttu-id="7bb57-194">使用本機空間進行條件約束</span><span class="sxs-lookup"><span data-stu-id="7bb57-194">Use local space for constraint</span></span>

<span data-ttu-id="7bb57-195">會限制操作物件的本機轉換軸（如果為 true）。</span><span class="sxs-lookup"><span data-stu-id="7bb57-195">Will constrain relative the manipulated object's local transform axes if true.</span></span> <span data-ttu-id="7bb57-196">預設為 False。</span><span class="sxs-lookup"><span data-stu-id="7bb57-196">False by default.</span></span>

### <a name="rotationaxisconstraint"></a><span data-ttu-id="7bb57-197">RotationAxisConstraint</span><span class="sxs-lookup"><span data-stu-id="7bb57-197">RotationAxisConstraint</span></span>

<img src="Images/ObjectManipulator/MRTK_Constraint_RotationAxis.gif" width="400" alt="Rotation Axis">

<span data-ttu-id="7bb57-198">這個條件約束可以用來修正哪些軸可以旋轉可操作的物件。</span><span class="sxs-lookup"><span data-stu-id="7bb57-198">This constraint can be used to fix about which axes a manipulated object can be rotated.</span></span> <span data-ttu-id="7bb57-199">這有助於讓操作物件保持垂直，但仍允許 y 軸旋轉（例如）。</span><span class="sxs-lookup"><span data-stu-id="7bb57-199">This can be useful for keeping a manipulated object upright, but still allowing y-axis rotations, for example.</span></span> <span data-ttu-id="7bb57-200">的屬性如下所示 `RotationAxisConstraint` ：</span><span class="sxs-lookup"><span data-stu-id="7bb57-200">The properties for `RotationAxisConstraint` are as follows:</span></span>

#### <a name="constraint-on-rotation"></a><span data-ttu-id="7bb57-201">旋轉的條件約束</span><span class="sxs-lookup"><span data-stu-id="7bb57-201">Constraint on rotation</span></span>

<span data-ttu-id="7bb57-202">指定要防止旋轉的座標軸。</span><span class="sxs-lookup"><span data-stu-id="7bb57-202">Specifies which axes to prevent rotation about.</span></span> <span data-ttu-id="7bb57-203">根據預設，這些軸會是全域的，而不是本機，但可在下方變更。</span><span class="sxs-lookup"><span data-stu-id="7bb57-203">By default, these axes will be global rather than local, but this can be changed below.</span></span> <span data-ttu-id="7bb57-204">因為此屬性是旗標，所以可以選取任何數目的選項。</span><span class="sxs-lookup"><span data-stu-id="7bb57-204">Because this property is a flag, any number of options can be selected.</span></span>

- <span data-ttu-id="7bb57-205">*Y 軸*：如有選取，y 軸的旋轉會受到限制。</span><span class="sxs-lookup"><span data-stu-id="7bb57-205">*Y Axis*: Rotation about the y-axis is constrained if selected.</span></span>
- <span data-ttu-id="7bb57-206">*Z 軸*：若已選取，則會限制 Z 軸的旋轉。</span><span class="sxs-lookup"><span data-stu-id="7bb57-206">*Z Axis*: Rotation about the z-axis is constrained if selected.</span></span>
- <span data-ttu-id="7bb57-207">*X 軸*：若已選取，則會限制 X 軸的旋轉。</span><span class="sxs-lookup"><span data-stu-id="7bb57-207">*X Axis*: Rotation about the x-axis is constrained if selected.</span></span>

#### <a name="use-local-space-for-constraint"></a><span data-ttu-id="7bb57-208">使用本機空間進行條件約束</span><span class="sxs-lookup"><span data-stu-id="7bb57-208">Use local space for constraint</span></span>

<span data-ttu-id="7bb57-209">會限制操作物件的本機轉換軸（如果為 true）。</span><span class="sxs-lookup"><span data-stu-id="7bb57-209">Will constrain relative the manipulated object's local transform axes if true.</span></span> <span data-ttu-id="7bb57-210">預設為 False。</span><span class="sxs-lookup"><span data-stu-id="7bb57-210">False by default.</span></span>

### <a name="minmaxscaleconstraint"></a><span data-ttu-id="7bb57-211">MinMaxScaleConstraint</span><span class="sxs-lookup"><span data-stu-id="7bb57-211">MinMaxScaleConstraint</span></span>

<img src="Images/ObjectManipulator/MRTK_Constraint_MinMaxScale.gif" width="400" alt="Min Max Scale Constraint">

<span data-ttu-id="7bb57-212">這個條件約束允許為操作物件的小數位數設定最小值和最大值。</span><span class="sxs-lookup"><span data-stu-id="7bb57-212">This constraint allows minimum and maximum values to be set for the scale of the manipulated object.</span></span> <span data-ttu-id="7bb57-213">這有助於防止使用者調整太小或太大的物件。</span><span class="sxs-lookup"><span data-stu-id="7bb57-213">This is useful for preventing users from scaling an object too small or too large.</span></span> <span data-ttu-id="7bb57-214">的屬性如下所示 `MinMaxScaleConstraint` ：</span><span class="sxs-lookup"><span data-stu-id="7bb57-214">The properties for `MinMaxScaleConstraint` are as follows:</span></span>

#### <a name="scale-minimum"></a><span data-ttu-id="7bb57-215">最小規模</span><span class="sxs-lookup"><span data-stu-id="7bb57-215">Scale minimum</span></span>

<span data-ttu-id="7bb57-216">操作期間的最小縮放值。</span><span class="sxs-lookup"><span data-stu-id="7bb57-216">The minimum scale value during manipulation.</span></span>

#### <a name="scale-maximum"></a><span data-ttu-id="7bb57-217">調整最大值</span><span class="sxs-lookup"><span data-stu-id="7bb57-217">Scale maximum</span></span>

<span data-ttu-id="7bb57-218">操作期間的最大縮放值。</span><span class="sxs-lookup"><span data-stu-id="7bb57-218">The maximum scale value during manipulation.</span></span>

#### <a name="relative-to-initial-state"></a><span data-ttu-id="7bb57-219">相對於初始狀態</span><span class="sxs-lookup"><span data-stu-id="7bb57-219">Relative to initial state</span></span>

<span data-ttu-id="7bb57-220">若為 true，則會將上述值轉譯為相對於物件初始縮放比例的值。</span><span class="sxs-lookup"><span data-stu-id="7bb57-220">If true, the values above will be interpreted as relative to the objects initial scale.</span></span> <span data-ttu-id="7bb57-221">否則，它們會被視為絕對規模值。</span><span class="sxs-lookup"><span data-stu-id="7bb57-221">Otherwise they will be interpreted as absolute scale values.</span></span>
