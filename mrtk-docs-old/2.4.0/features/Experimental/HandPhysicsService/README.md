---
title: README_HandPhysicsExtensionService
description: 描述手型物理延伸模組服務。
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
ms.localizationpriority: medium
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: 365c2625190a0d249fd81107545473e27efedea1
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104690965"
---
# <a name="hand-physics-extension-service"></a><span data-ttu-id="d2a52-104">手上物理延伸模組服務</span><span class="sxs-lookup"><span data-stu-id="d2a52-104">Hand physics extension service</span></span>

![手上物理延伸模組服務](../../Images/HandPhysics/MRTK_UX_HandPhysics_Main.jpg)

<span data-ttu-id="d2a52-106">實際的物理服務可讓您使用明確的內文衝突事件，並與明確的手進行互動。</span><span class="sxs-lookup"><span data-stu-id="d2a52-106">The hand physics service enables rigid body collision events and interactions with articulated hands.</span></span>

## <a name="getting-started-with-hand-physics-extension-service"></a><span data-ttu-id="d2a52-107">開始使用手型物理延伸模組服務</span><span class="sxs-lookup"><span data-stu-id="d2a52-107">Getting started with hand physics extension service</span></span>

<span data-ttu-id="d2a52-108">將「手型物理服務」新增至擴充服務清單，並使用預設設定檔。</span><span class="sxs-lookup"><span data-stu-id="d2a52-108">Add the hand physics service to the list of extension services and use the default profile.</span></span>

<span data-ttu-id="d2a52-109">啟用之後，請使用任何碰撞器的 IsTrigger 屬性來接收來自所有10位數的衝突事件 (以及手掌是否已啟用) 。</span><span class="sxs-lookup"><span data-stu-id="d2a52-109">Once enabled, use any collider's IsTrigger property to receive collision events from all 10 digits (and palms if they're enabled).</span></span>

### <a name="prerequisites"></a><span data-ttu-id="d2a52-110">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="d2a52-110">Prerequisites</span></span>

- <span data-ttu-id="d2a52-111">已啟用延伸模組服務</span><span class="sxs-lookup"><span data-stu-id="d2a52-111">Enabled the extension service</span></span>
- <span data-ttu-id="d2a52-112">將適當的預製專案指派給手指/掌接合。</span><span class="sxs-lookup"><span data-stu-id="d2a52-112">Assign an appropriate prefab to the finger/palm joint.</span></span>

## <a name="recommendations"></a><span data-ttu-id="d2a52-113">建議</span><span class="sxs-lookup"><span data-stu-id="d2a52-113">Recommendations</span></span>

<span data-ttu-id="d2a52-114">雖然服務預設為「預設」層，但建議針對 HandPhysics 物件使用不同的層級。</span><span class="sxs-lookup"><span data-stu-id="d2a52-114">While the service defaults to the "default" layer, it is recommended to use a separate layer for HandPhysics objects.</span></span> <span data-ttu-id="d2a52-115">否則可能會發生不必要的衝突和（或）不正確的 raycasts。</span><span class="sxs-lookup"><span data-stu-id="d2a52-115">Otherwise there may be unwanted collisions and/or inaccurate raycasts.</span></span>
