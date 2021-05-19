---
title: 手形物理服務總覽
description: 在 MRTK 中使用手物理延伸模組服務的檔
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: 751aec148d3a40da4728d2fdd60a60402b59a4de
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145084"
---
# <a name="hand-physics-extension-service"></a><span data-ttu-id="6379d-104">手上物理延伸模組服務</span><span class="sxs-lookup"><span data-stu-id="6379d-104">Hand physics extension service</span></span>

![手上物理延伸模組服務](../images/hand-physics/MRTK_UX_HandPhysics_Main.jpg)

<span data-ttu-id="6379d-106">實際的物理服務可讓您使用明確的內文衝突事件，並與明確的手進行互動。</span><span class="sxs-lookup"><span data-stu-id="6379d-106">The hand physics service enables rigid body collision events and interactions with articulated hands.</span></span>

## <a name="enabling-the-extension"></a><span data-ttu-id="6379d-107">啟用擴充功能</span><span class="sxs-lookup"><span data-stu-id="6379d-107">Enabling the extension</span></span>

<span data-ttu-id="6379d-108">若要啟用擴充功能，請開啟您的 RegisteredServiceProvider 設定檔。</span><span class="sxs-lookup"><span data-stu-id="6379d-108">To enable the extension, open your RegisteredServiceProvider profile.</span></span> <span data-ttu-id="6379d-109">按一下 `Register a new Service Provider` 以新增設定。</span><span class="sxs-lookup"><span data-stu-id="6379d-109">Click `Register a new Service Provider` to add a new configuration.</span></span> <span data-ttu-id="6379d-110">在 [元件類型] 欄位中，選取 [HandPhysicsService]。</span><span class="sxs-lookup"><span data-stu-id="6379d-110">In the component type field, select HandPhysicsService.</span></span> <span data-ttu-id="6379d-111">在 [設定設定檔] 欄位中，選取延伸模組隨附的預設的 [物理設定檔]。</span><span class="sxs-lookup"><span data-stu-id="6379d-111">In the configuration Profile field, select the default hand physics profile included with the extension.</span></span>

## <a name="profile-options"></a><span data-ttu-id="6379d-112">設定檔選項</span><span class="sxs-lookup"><span data-stu-id="6379d-112">Profile options</span></span>

### <a name="hand-physics-layer"></a><span data-ttu-id="6379d-113">手中實體層</span><span class="sxs-lookup"><span data-stu-id="6379d-113">Hand physics layer</span></span>

<span data-ttu-id="6379d-114">控制具現化的手接點將移至的圖層。</span><span class="sxs-lookup"><span data-stu-id="6379d-114">Controls the layer the instantiated hand joints will go to.</span></span>

<span data-ttu-id="6379d-115">雖然服務預設為「預設」層 (0) ，但建議針對手物理物件使用不同的層級。</span><span class="sxs-lookup"><span data-stu-id="6379d-115">While the service defaults to the "default" layer (0), it is recommended to use a separate layer for hand physics objects.</span></span> <span data-ttu-id="6379d-116">否則可能會發生不必要的衝突和（或）不正確的 raycasts。</span><span class="sxs-lookup"><span data-stu-id="6379d-116">Otherwise there may be unwanted collisions and/or inaccurate raycasts.</span></span>

### <a name="finger-tip-kinematic-body-prefab"></a><span data-ttu-id="6379d-117">手指運動主體預製專案</span><span class="sxs-lookup"><span data-stu-id="6379d-117">Finger tip kinematic body prefab</span></span>

<span data-ttu-id="6379d-118">控制可隨時具現化的預製專案。</span><span class="sxs-lookup"><span data-stu-id="6379d-118">Controls which prefab is instantiated on fingertips.</span></span> <span data-ttu-id="6379d-119">為了讓服務能夠如預期般運作，預製專案需要：</span><span class="sxs-lookup"><span data-stu-id="6379d-119">In order for the service to work as expected, the prefab requires:</span></span>

- <span data-ttu-id="6379d-120">啟用 isKinematic 的 rigidbody 元件</span><span class="sxs-lookup"><span data-stu-id="6379d-120">A rigidbody component, with isKinematic enabled</span></span>
- <span data-ttu-id="6379d-121">碰撞</span><span class="sxs-lookup"><span data-stu-id="6379d-121">A collider</span></span>
- <span data-ttu-id="6379d-122">`JointKinematicBody` 元件</span><span class="sxs-lookup"><span data-stu-id="6379d-122">`JointKinematicBody` component</span></span>

### <a name="use-palm-kinematic-body"></a><span data-ttu-id="6379d-123">使用 palm 運動學主體</span><span class="sxs-lookup"><span data-stu-id="6379d-123">Use palm kinematic body</span></span>

<span data-ttu-id="6379d-124">控制服務是否會嘗試將預製專案具現化于 palm 聯合。</span><span class="sxs-lookup"><span data-stu-id="6379d-124">Controls whether the service will attempt to instantiate a prefab on the palm joint.</span></span>

### <a name="palm-kinematic-body-prefab"></a><span data-ttu-id="6379d-125">掌運動學內文主體預製專案</span><span class="sxs-lookup"><span data-stu-id="6379d-125">Palm kinematic body prefab</span></span>

<span data-ttu-id="6379d-126">當 `UsePalmKinematicBody` 啟用時，這會是要具現化的預製專案。</span><span class="sxs-lookup"><span data-stu-id="6379d-126">When `UsePalmKinematicBody` is enabled, this is the prefab it will instantiate.</span></span> <span data-ttu-id="6379d-127">就像 `FingerTipKinematicBodyPrefab` 這樣的預製專案需要：</span><span class="sxs-lookup"><span data-stu-id="6379d-127">Just like `FingerTipKinematicBodyPrefab`, this prefab requires:</span></span>

- <span data-ttu-id="6379d-128">啟用 isKinematic 的 rigidbody 元件</span><span class="sxs-lookup"><span data-stu-id="6379d-128">A rigidbody component, with isKinematic enabled</span></span>
- <span data-ttu-id="6379d-129">碰撞</span><span class="sxs-lookup"><span data-stu-id="6379d-129">A collider</span></span>
- <span data-ttu-id="6379d-130">`JointKinematicBody` 元件</span><span class="sxs-lookup"><span data-stu-id="6379d-130">`JointKinematicBody` component</span></span>

## <a name="how-to-use-the-service"></a><span data-ttu-id="6379d-131">如何使用服務</span><span class="sxs-lookup"><span data-stu-id="6379d-131">How to use the service</span></span>

<span data-ttu-id="6379d-132">啟用之後，請使用任何碰撞器的 `IsTrigger` 屬性來接收所有10位數的衝突事件 (和手掌（如果已啟用) ）。</span><span class="sxs-lookup"><span data-stu-id="6379d-132">Once enabled, use any collider's `IsTrigger` property to receive collision events from all 10 digits (and palms if they're enabled).</span></span>
