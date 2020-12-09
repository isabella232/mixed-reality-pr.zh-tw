---
title: Unity 的輸入移植指南
description: 瞭解如何在 Unity 中處理 Windows Mixed Reality 的輸入。
author: thetuvix
ms.author: alexturn
ms.date: 12/9/2020
ms.topic: article
keywords: 輸入、unity、移植
ms.openlocfilehash: 053918ec62f83c74655b0d4bb09a2b45b62bfc53
ms.sourcegitcommit: f2782d0925b2075fdaa0a4ecdef3dd4f0b4e1e99
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/09/2020
ms.locfileid: "96925874"
---
# <a name="input-porting-guide-for-unity"></a><span data-ttu-id="13f1a-104">Unity 的輸入移植指南</span><span class="sxs-lookup"><span data-stu-id="13f1a-104">Input porting guide for Unity</span></span>

<span data-ttu-id="13f1a-105">您可以使用下列兩種方法之一來將輸入邏輯移植到 Windows Mixed Reality： Unity 的一般輸入。跨多個平臺的 GetButton/GetAxis Api，或 Windows 特定的 XR。Wsa。輸入 Api，專為運動控制器和 HoloLens 手提供更豐富的資料。</span><span class="sxs-lookup"><span data-stu-id="13f1a-105">You can port your input logic to Windows Mixed Reality using one of two approaches, Unity's general Input.GetButton/GetAxis APIs that span across multiple platforms, or the Windows-specific XR.WSA.Input APIs that offer richer data specifically for motion controllers and HoloLens hands.</span></span>

## <a name="general-inputgetbuttongetaxis-apis"></a><span data-ttu-id="13f1a-106">一般輸入. GetButton/GetAxis Api</span><span class="sxs-lookup"><span data-stu-id="13f1a-106">General Input.GetButton/GetAxis APIs</span></span>

<span data-ttu-id="13f1a-107">Unity 目前使用其一般輸入. GetButton/GetAxis Api 來公開 [OCULUS SDK](https://docs.unity3d.com/Manual/OculusControllers.html) 和 [OpenVR SDK](https://docs.unity3d.com/Manual/OpenVRControllers.html)的輸入。</span><span class="sxs-lookup"><span data-stu-id="13f1a-107">Unity currently uses its general Input.GetButton/Input.GetAxis APIs to expose input for [the Oculus SDK](https://docs.unity3d.com/Manual/OculusControllers.html) and [the OpenVR SDK](https://docs.unity3d.com/Manual/OpenVRControllers.html).</span></span> <span data-ttu-id="13f1a-108">如果您的應用程式已經使用這些 Api 進行輸入，這是在 Windows Mixed Reality 中支援移動控制器最簡單的路徑：您應該只需要重新對應輸入管理員中的按鈕和軸。</span><span class="sxs-lookup"><span data-stu-id="13f1a-108">If your apps are already using these APIs for input, this is the easiest path for supporting motion controllers in Windows Mixed Reality: you should just need to remap buttons and axes in the Input Manager.</span></span>

<span data-ttu-id="13f1a-109">如需詳細資訊，請參閱 [unity 按鈕/軸對應表](../unity/gestures-and-motion-controllers-in-unity.md#unity-buttonaxis-mapping-table) 和 [通用 Unity api 的總覽](../unity/gestures-and-motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis)。</span><span class="sxs-lookup"><span data-stu-id="13f1a-109">For more information, see the [Unity button/axis mapping table](../unity/gestures-and-motion-controllers-in-unity.md#unity-buttonaxis-mapping-table) and the [overview of the common Unity APIs](../unity/gestures-and-motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis).</span></span>

## <a name="windows-specific-xrwsainput-apis"></a><span data-ttu-id="13f1a-110">Windows 特定 XR。Wsa。輸入 Api</span><span class="sxs-lookup"><span data-stu-id="13f1a-110">Windows-specific XR.WSA.Input APIs</span></span>

<span data-ttu-id="13f1a-111">如果您的應用程式已經為每個平臺建立自訂輸入邏輯，您可以選擇使用 **UnityEngine. XR** 命名空間底下的 Windows 特定空間輸入 api。</span><span class="sxs-lookup"><span data-stu-id="13f1a-111">If your app already builds custom input logic for each platform, you can choose to use the Windows-specific spatial input APIs under the **UnityEngine.XR.WSA.Input** namespace.</span></span> <span data-ttu-id="13f1a-112">這可讓您存取額外的資訊，例如位置精確度或來源種類，讓您可以在 HoloLens 上分辨手和控制器。</span><span class="sxs-lookup"><span data-stu-id="13f1a-112">This lets you access additional information, such as position accuracy or the source kind, letting you tell hands and controllers apart on HoloLens.</span></span>

<span data-ttu-id="13f1a-113">如需詳細資訊，請參閱 [UnityEngine. XR. 輸入 api 的總覽](../unity/gestures-and-motion-controllers-in-unity.md#windows-specific-apis-xrwsainput)。</span><span class="sxs-lookup"><span data-stu-id="13f1a-113">For more information, see the [overview of the UnityEngine.XR.WSA.Input APIs](../unity/gestures-and-motion-controllers-in-unity.md#windows-specific-apis-xrwsainput).</span></span>

## <a name="grip-pose-vs-pointing-pose"></a><span data-ttu-id="13f1a-114">底姿勢與指標姿勢</span><span class="sxs-lookup"><span data-stu-id="13f1a-114">Grip pose vs. pointing pose</span></span>

<span data-ttu-id="13f1a-115">Windows Mixed Reality 支援各種外型規格中的運動控制器，每個控制器的設計各有不同之處，就是使用者的位置與應用程式在轉譯控制器時應使用的自然「向前」方向之間的關聯性。</span><span class="sxs-lookup"><span data-stu-id="13f1a-115">Windows Mixed Reality supports motion controllers in a variety of form factors, with each controller's design differing in its relationship between the user's hand position and the natural "forward" direction that apps should use for pointing when rendering the controller.</span></span>

<span data-ttu-id="13f1a-116">為了更妥善地表示這些控制器，您可以針對每個互動來源進行兩種調查：</span><span class="sxs-lookup"><span data-stu-id="13f1a-116">To better represent these controllers, there are two kinds of poses you can investigate for each interaction source:</span></span>

* <span data-ttu-id="13f1a-117">底框 **姿勢**，代表 HoloLens 所偵測到之掌上的位置，或是持有運動控制器的掌上。</span><span class="sxs-lookup"><span data-stu-id="13f1a-117">The **grip pose**, representing the location of either the palm of a hand detected by a HoloLens, or the palm holding a motion controller.</span></span>
    * <span data-ttu-id="13f1a-118">在沉浸式耳機上，這個姿勢最適合用 **來呈現使用者手** 或 **使用者手中所持有的物件**，例如寶劍或機槍。</span><span class="sxs-lookup"><span data-stu-id="13f1a-118">On immersive headsets, this pose is best used to render **the user's hand** or **an object held in the user's hand**, such as a sword or gun.</span></span>
    * <span data-ttu-id="13f1a-119">把手 **位置**：自然地按住控制器時的棕櫚距心，向左或向右調整以將位置置中置中。</span><span class="sxs-lookup"><span data-stu-id="13f1a-119">The **grip position**: The palm centroid when holding the controller naturally, adjusted left or right to center the position within the grip.</span></span>
    * <span data-ttu-id="13f1a-120">底 **圖方向的右軸**：當您完全開啟手來形成平面的5形姿勢時，您的掌上光 (的光線會從左至右向前復原，從右邊的棕櫚) </span><span class="sxs-lookup"><span data-stu-id="13f1a-120">The **grip orientation's Right axis**: When you completely open your hand to form a flat 5-finger pose, the ray that is normal to your palm (forward from left palm, backward from right palm)</span></span>
    * <span data-ttu-id="13f1a-121">底圖 **方向的向前軸**：當您關閉手部分 (時，如同按住控制器) 一樣，也就是由非拇指手指所形成的電子管「轉寄」的光線。</span><span class="sxs-lookup"><span data-stu-id="13f1a-121">The **grip orientation's Forward axis**: When you close your hand partially (as if holding the controller), the ray that points "forward" through the tube formed by your non-thumb fingers.</span></span>
    * <span data-ttu-id="13f1a-122">底圖 **方向的向上軸**：右邊和向前定義所隱含的向上軸。</span><span class="sxs-lookup"><span data-stu-id="13f1a-122">The **grip orientation's Up axis**: The Up axis implied by the Right and Forward definitions.</span></span>
    * <span data-ttu-id="13f1a-123">您可以透過 Unity 的跨廠商輸入 API (XR 來存取抓住姿勢 **[。InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)。GetLocalPosition/輪替**) 或透過 Windows 特定 API (**SourceState. SourcePose. TryGetPosition/旋轉**，要求底框姿勢) 。</span><span class="sxs-lookup"><span data-stu-id="13f1a-123">You can access the grip pose through either Unity's cross-vendor input API (**[XR.InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html).GetLocalPosition/Rotation**) or through the Windows-specific API (**sourceState.sourcePose.TryGetPosition/Rotation**, requesting the Grip pose).</span></span>
* <span data-ttu-id="13f1a-124">**指標姿勢**，代表指向轉寄之控制器的秘訣。</span><span class="sxs-lookup"><span data-stu-id="13f1a-124">The **pointer pose**, representing the tip of the controller pointing forward.</span></span>
    * <span data-ttu-id="13f1a-125">當您在呈現控制器模型本身時 **指向 UI** 時，最好使用這個姿勢來 raycast。</span><span class="sxs-lookup"><span data-stu-id="13f1a-125">This pose is best used to raycast when **pointing at UI** when you are rendering the controller model itself.</span></span>
    * <span data-ttu-id="13f1a-126">目前，指標姿勢只能透過 Windows 特定 API 來使用 (**sourceState. sourcePose. TryGetPosition/旋轉**，要求指標姿勢) 。</span><span class="sxs-lookup"><span data-stu-id="13f1a-126">Currently, the pointer pose is available only through the Windows-specific API (**sourceState.sourcePose.TryGetPosition/Rotation**, requesting the Pointer pose).</span></span>

<span data-ttu-id="13f1a-127">這些姿勢座標全都以 Unity 全局座標表示。</span><span class="sxs-lookup"><span data-stu-id="13f1a-127">These pose coordinates are all expressed in Unity world coordinates.</span></span>

## <a name="see-also"></a><span data-ttu-id="13f1a-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="13f1a-128">See also</span></span>
* <span data-ttu-id="13f1a-129">[移動控制器]().。。/../design/motion-controllers.md) </span><span class="sxs-lookup"><span data-stu-id="13f1a-129">[Motion controllers]()../../design/motion-controllers.md)</span></span>
* [<span data-ttu-id="13f1a-130">Unity 中的筆勢和運動控制器</span><span class="sxs-lookup"><span data-stu-id="13f1a-130">Gestures and motion controllers in Unity</span></span>](../unity/gestures-and-motion-controllers-in-unity.md)
* [<span data-ttu-id="13f1a-131">UnityEngine. XR。輸入</span><span class="sxs-lookup"><span data-stu-id="13f1a-131">UnityEngine.XR.WSA.Input</span></span>](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.html)
* [<span data-ttu-id="13f1a-132">UnityEngine. XR. InputTracking</span><span class="sxs-lookup"><span data-stu-id="13f1a-132">UnityEngine.XR.InputTracking</span></span>](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)
* [<span data-ttu-id="13f1a-133">移植指南</span><span class="sxs-lookup"><span data-stu-id="13f1a-133">Porting guides</span></span>](porting-guides.md)
