---
title: 手上物理延伸模組服務
description: 描述手型物理延伸模組服務。
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: 401a9d31ed3fbbe0c3e02cb95ffebb024f882fd9
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143433"
---
# <a name="hand-physics-extension-services"></a><span data-ttu-id="d0341-104">手上物理延伸模組服務</span><span class="sxs-lookup"><span data-stu-id="d0341-104">Hand physics extension services</span></span>

<span data-ttu-id="d0341-105">實際的物理服務可讓您使用明確的內文衝突事件，並與明確的手進行互動。</span><span class="sxs-lookup"><span data-stu-id="d0341-105">The hand physics service enables rigid body collision events and interactions with articulated hands.</span></span>

## <a name="getting-started-with-hand-physics-extension-service"></a><span data-ttu-id="d0341-106">開始使用手型物理延伸模組服務</span><span class="sxs-lookup"><span data-stu-id="d0341-106">Getting started with hand physics extension service</span></span>

<span data-ttu-id="d0341-107">將「手型物理服務」新增至擴充服務清單，並使用預設設定檔。</span><span class="sxs-lookup"><span data-stu-id="d0341-107">Add the hand physics service to the list of extension services and use the default profile.</span></span>

<span data-ttu-id="d0341-108">啟用之後，請使用任何碰撞器的 IsTrigger 屬性來接收來自所有10位數的衝突事件 (以及手掌是否已啟用) 。</span><span class="sxs-lookup"><span data-stu-id="d0341-108">Once enabled, use any collider's IsTrigger property to receive collision events from all 10 digits (and palms if they're enabled).</span></span>

### <a name="prerequisites"></a><span data-ttu-id="d0341-109">必要條件</span><span class="sxs-lookup"><span data-stu-id="d0341-109">Prerequisites</span></span>

- <span data-ttu-id="d0341-110">已啟用延伸模組服務</span><span class="sxs-lookup"><span data-stu-id="d0341-110">Enabled the extension service</span></span>
- <span data-ttu-id="d0341-111">將適當的預製專案指派給手指/掌接合。</span><span class="sxs-lookup"><span data-stu-id="d0341-111">Assign an appropriate prefab to the finger/palm joint.</span></span>

## <a name="recommendations"></a><span data-ttu-id="d0341-112">建議</span><span class="sxs-lookup"><span data-stu-id="d0341-112">Recommendations</span></span>

<span data-ttu-id="d0341-113">雖然服務預設為「預設」層，但建議針對 HandPhysics 物件使用不同的層級。</span><span class="sxs-lookup"><span data-stu-id="d0341-113">While the service defaults to the "default" layer, it is recommended to use a separate layer for HandPhysics objects.</span></span> <span data-ttu-id="d0341-114">否則可能會發生不必要的衝突和（或）不正確的 raycasts。</span><span class="sxs-lookup"><span data-stu-id="d0341-114">Otherwise there may be unwanted collisions and/or inaccurate raycasts.</span></span>
