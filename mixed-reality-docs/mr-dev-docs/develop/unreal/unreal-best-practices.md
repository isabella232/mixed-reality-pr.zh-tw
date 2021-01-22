---
title: 一般最佳作法
description: 隨時掌握在 Unreal 引擎中開發混合現實應用程式的最新建議最佳作法。
author: hferrone
ms.author: safarooq
ms.date: 01/08/2021
ms.topic: article
ms.localizationpriority: high
keywords: Unreal、Unreal Engine 4、editor extensions、Unreal editor、UE4、HoloLens、HoloLens 2、mixed reality、開發、檔、指南、功能、混合現實耳機、windows mixed reality 耳機、虛擬實境耳機、移植、升級
ms.openlocfilehash: 478ae3137fc73d1ef516087618ab0247f2164c02
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/20/2021
ms.locfileid: "98584791"
---
# <a name="general-best-practices"></a><span data-ttu-id="f702d-104">一般最佳作法</span><span class="sxs-lookup"><span data-stu-id="f702d-104">General best practices</span></span>

<span data-ttu-id="f702d-105">以下是我們建議所有開發人員在建立混合現實的 Unreal 引擎專案時所遵循的一般最佳作法。</span><span class="sxs-lookup"><span data-stu-id="f702d-105">The following are some general best practices we recommend all developers follow when creating an Unreal Engine project for Mixed Reality.</span></span>

## <a name="constructors"></a><span data-ttu-id="f702d-106">建構函式</span><span class="sxs-lookup"><span data-stu-id="f702d-106">Constructors</span></span>

<span data-ttu-id="f702d-107">如果您需要藍圖中的「函式」對等專案，請使用 Unreals 的 [結構腳本](https://docs.unrealengine.com/ProgrammingAndScripting/Blueprints/UserGuide/UserConstructionScript/index.html)。</span><span class="sxs-lookup"><span data-stu-id="f702d-107">If you need the equivalent of a "constructor" in blueprints, use Unreals' [construction script](https://docs.unrealengine.com/ProgrammingAndScripting/Blueprints/UserGuide/UserConstructionScript/index.html).</span></span> <span data-ttu-id="f702d-108">使用 "BeginPlay" 事件的主要優點是，函式腳本也會在「編輯器」中執行。</span><span class="sxs-lookup"><span data-stu-id="f702d-108">The primary advantage over using "BeginPlay" events is the constructor script runs in the "editor" as well.</span></span> <span data-ttu-id="f702d-109">大部分的時間都可以在一開始或甚至編譯時期快取。</span><span class="sxs-lookup"><span data-stu-id="f702d-109">Most of the time the values can be cached right at the start or even at compile time.</span></span>

> [!NOTE]
> <span data-ttu-id="f702d-110">您可以在 [編輯器延伸模組總覽](unreal-editor-extensions.md#construction-scripts)中找到更多的結構腳本支援資訊。</span><span class="sxs-lookup"><span data-stu-id="f702d-110">You can find more supporting information for Construction scripts in our [editor extensions overview](unreal-editor-extensions.md#construction-scripts).</span></span>

## <a name="3d-buttons-and-textures"></a><span data-ttu-id="f702d-111">3D 按鈕和紋理</span><span class="sxs-lookup"><span data-stu-id="f702d-111">3D buttons and textures</span></span>

<span data-ttu-id="f702d-112">在混合現實應用程式中建立或規劃使用3D 按鈕時，最好考慮效能。</span><span class="sxs-lookup"><span data-stu-id="f702d-112">It's natural to think about performance when creating or planning to use 3D buttons in mixed reality applications.</span></span> <span data-ttu-id="f702d-113">不過，並非所有東西都必須從網格中被視為3D。</span><span class="sxs-lookup"><span data-stu-id="f702d-113">However, not everything has to be made from meshes to be perceived as 3D.</span></span> <span data-ttu-id="f702d-114">您可以選擇使用 Paper2D 和精心製作的紋理來取得3D 外觀。</span><span class="sxs-lookup"><span data-stu-id="f702d-114">You have the option of using Paper2D with carefully crafted textures to get that 3D look.</span></span> <span data-ttu-id="f702d-115">這非常適合「看似」3D 的按鈕，但只是在四個 photoshopped 影像。</span><span class="sxs-lookup"><span data-stu-id="f702d-115">This works really well for buttons that "seem" 3D, but are just photoshopped images on a quad.</span></span> <span data-ttu-id="f702d-116">這類的奇特版本稱為 [sprite](https://docs.unrealengine.com/AnimatingObjects/Paper2D/Sprites/index.html)。</span><span class="sxs-lookup"><span data-stu-id="f702d-116">A fancy version of these is called a [sprite](https://docs.unrealengine.com/AnimatingObjects/Paper2D/Sprites/index.html).</span></span>

## <a name="variants"></a><span data-ttu-id="f702d-117">變異</span><span class="sxs-lookup"><span data-stu-id="f702d-117">Variants</span></span>

<span data-ttu-id="f702d-118">如果您要在執行時間建立具有多個物件設定的場景，請使用 [Unreal](https://docs.unrealengine.com/Basics/Levels/Variants/index.html) 變異。</span><span class="sxs-lookup"><span data-stu-id="f702d-118">Use [Unreal Variants](https://docs.unrealengine.com/Basics/Levels/Variants/index.html) in scenarios where you're creating a scene with multiple object configurations at runtime.</span></span> <span data-ttu-id="f702d-119">變化可以包含變更的材質或網格。</span><span class="sxs-lookup"><span data-stu-id="f702d-119">Variations can include changing materials or meshes.</span></span> 

## <a name="animation"></a><span data-ttu-id="f702d-120">動畫</span><span class="sxs-lookup"><span data-stu-id="f702d-120">Animation</span></span>

<span data-ttu-id="f702d-121">如果您要建立許多「互動動畫」，請利用 [曲線元件](https://docs.unrealengine.com/API/Runtime/Engine/Components/USplineComponent/index.html) (不是曲線「網格」元件) 和 [時間軸節點](https://docs.unrealengine.com/ProgrammingAndScripting/Blueprints/UserGuide/Timelines/index.html) 。</span><span class="sxs-lookup"><span data-stu-id="f702d-121">Take advantage of the [Spline component](https://docs.unrealengine.com/API/Runtime/Engine/Components/USplineComponent/index.html) (not the Spline "Mesh" Component) and [Timeline nodes](https://docs.unrealengine.com/ProgrammingAndScripting/Blueprints/UserGuide/Timelines/index.html) if you're creating lots of "interactable animations".</span></span> 

<!-- You can find a comprehensive [video tutorial here](https://www.youtube.com/watch?v=bWXI91FdMtk&ab_channel=DoubleCrossGames). -->

## <a name="communications"></a><span data-ttu-id="f702d-122">通訊</span><span class="sxs-lookup"><span data-stu-id="f702d-122">Communications</span></span>

<span data-ttu-id="f702d-123">如果您在多個動作專案和藍圖之間動態尋找物件或使用太多頻寬來進行通訊，請使用 [層級藍圖](https://docs.unrealengine.com/ProgrammingAndScripting/Blueprints/UserGuide/Types/LevelBlueprint/index.html) 。</span><span class="sxs-lookup"><span data-stu-id="f702d-123">Use a [Level Blueprint](https://docs.unrealengine.com/ProgrammingAndScripting/Blueprints/UserGuide/Types/LevelBlueprint/index.html) if you're having trouble dynamically finding objects or using too much bandwidth to communicate between multiple actors and blueprints.</span></span> <span data-ttu-id="f702d-124">請記住，Unreal Engine 4 不像 Unity，並非所有專案都必須在元件中。</span><span class="sxs-lookup"><span data-stu-id="f702d-124">Remember, Unreal Engine 4 isn't like Unity, not everything has to be inside a component.</span></span> <span data-ttu-id="f702d-125">層級藍圖是完全有效且建議的方式，可簡化多個執行者之間的通訊。</span><span class="sxs-lookup"><span data-stu-id="f702d-125">Level Blueprints are a perfectly valid and recommended way of simplifying the communication between multiple actors.</span></span> <span data-ttu-id="f702d-126">在層級藍圖的 OnBeginPlay 中啟動時，物件參考甚至可以「快取」。</span><span class="sxs-lookup"><span data-stu-id="f702d-126">Object references can even be "cached" at startup in the Level Blueprint's OnBeginPlay.</span></span>

## <a name="global-state"></a><span data-ttu-id="f702d-127">全域狀態</span><span class="sxs-lookup"><span data-stu-id="f702d-127">Global state</span></span>

<span data-ttu-id="f702d-128">您通常需要儲存層級特定的狀態，例如分數、層級資料、播放機特定資訊，或任何其他不屬於特定物件的內容。</span><span class="sxs-lookup"><span data-stu-id="f702d-128">You'll often need to store level-specific state like score, level data, player-specific information, or anything else that doesn't quite belong to a particular object.</span></span> <span data-ttu-id="f702d-129">不要忽略 [GameMode](https://docs.unrealengine.com/en-US/InteractiveExperiences/Framework/GameMode/index.html)。</span><span class="sxs-lookup"><span data-stu-id="f702d-129">Don't overlook the [GameMode](https://docs.unrealengine.com/en-US/InteractiveExperiences/Framework/GameMode/index.html).</span></span> <span data-ttu-id="f702d-130">大部分的人都忘記它存在，但是 GameMode 可以針對每個層級建立，並且包含每個層級的特定資料。</span><span class="sxs-lookup"><span data-stu-id="f702d-130">Most people forget that it exists, but the GameMode can be created per level, and contain data specific to each level.</span></span>

## <a name="optimizing-blueprints"></a><span data-ttu-id="f702d-131">優化藍圖</span><span class="sxs-lookup"><span data-stu-id="f702d-131">Optimizing Blueprints</span></span>

<span data-ttu-id="f702d-132">如果您發現藍圖的速度太慢，請先 Unreal 「nativize」您的藍圖，再利用 c + + 重寫程式碼。</span><span class="sxs-lookup"><span data-stu-id="f702d-132">If you're finding your blueprints to be too slow, let Unreal "nativize" your blueprints before resorting to rewriting the code in c++.</span></span> <span data-ttu-id="f702d-133">在建立您自己的自訂解決方案之前，請先嘗試使用自動 [nativization](https://docs.unrealengine.com/ProgrammingAndScripting/Blueprints/TechnicalGuide/NativizingBlueprints/index.html) 。</span><span class="sxs-lookup"><span data-stu-id="f702d-133">Try using the automatic [nativization](https://docs.unrealengine.com/ProgrammingAndScripting/Blueprints/TechnicalGuide/NativizingBlueprints/index.html) before creating your own custom solution.</span></span>

![藍圖設定，具有醒目提示內含的藍圖 nativization 方法](images/unreal-general-practices-img-01.jpg)
