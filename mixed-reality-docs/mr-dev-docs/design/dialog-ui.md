---
title: 對話
description: 瞭解 MRTK 中的對話方塊覆迭，以及如何在混合現實應用程式中使用它們。
author: cre8ivepark
ms.author: dongpark
ms.date: 06/19/2020
ms.topic: article
keywords: 混合的現實、HoloLens、UI 控制項、互動、UI、ux、UX 設計、空間 UI、空間互動、3D UI、3D UX、混合現實耳機、windows mixed reality 耳機、虛擬實境耳機、HoloLens、MRTK、混合現實工具組
ms.openlocfilehash: c9e1bf3e263214f9691f6c788f6115f93e690489
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/03/2021
ms.locfileid: "101759253"
---
# <a name="dialog"></a><span data-ttu-id="5fffa-104">對話</span><span class="sxs-lookup"><span data-stu-id="5fffa-104">Dialog</span></span>

![以 [是] 且沒有任何按鈕顯示在 HoloLens 上的對話方塊重迭螢幕擷取畫面](images/MRTK_UX_Dialog.jpg)

<span data-ttu-id="5fffa-106">對話方塊控制項是 UI 重迭，可提供內容相關的應用程式資訊，通常會要求使用者動作。</span><span class="sxs-lookup"><span data-stu-id="5fffa-106">Dialog controls are UI overlays that provide contextual app information, often requesting a user action.</span></span> <span data-ttu-id="5fffa-107">您可以使用對話方塊來提供使用者重要資訊，以及要求確認或額外資訊，才能完成動作。</span><span class="sxs-lookup"><span data-stu-id="5fffa-107">Use dialogs to give users important information and request confirmation or extra information before an action can be completed.</span></span>

<br>

---

## <a name="dialog-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="5fffa-108">Unity 的 MRTK (混合現實工具組) 對話方塊</span><span class="sxs-lookup"><span data-stu-id="5fffa-108">Dialog in MRTK (Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="5fffa-109">MRTK 提供三種大小的對話方塊控制項，包含一或兩個按鈕選項。</span><span class="sxs-lookup"><span data-stu-id="5fffa-109">MRTK provides dialog control in three sizes with one or two button options.</span></span> <span data-ttu-id="5fffa-110">您也可以指定接近或遠距離互動範圍的放置距離。</span><span class="sxs-lookup"><span data-stu-id="5fffa-110">You can also specify the placement distance for near or far interaction range.</span></span> 

- <span data-ttu-id="5fffa-111">DialogSmall_192x96. 預製專案：192x96mm</span><span class="sxs-lookup"><span data-stu-id="5fffa-111">DialogSmall_192x96.prefab: 192x96mm</span></span>
- <span data-ttu-id="5fffa-112">DialogMedium_192x128. 預製專案：192x128mm</span><span class="sxs-lookup"><span data-stu-id="5fffa-112">DialogMedium_192x128.prefab: 192x128mm</span></span>
- <span data-ttu-id="5fffa-113">DialogLarge_192x192. 預製專案：192x192mm</span><span class="sxs-lookup"><span data-stu-id="5fffa-113">DialogLarge_192x192.prefab: 192x192mm</span></span>

![在 HoloLens 上執行的不同大小對話重迭螢幕擷取畫面](images/MRTK_UX_Dialog_Types.jpg)


* <span data-ttu-id="5fffa-115">如需詳細資訊，請參閱 [MRTK-對話方塊](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/experimental/dialog.md)。</span><span class="sxs-lookup"><span data-stu-id="5fffa-115">For more information, see [MRTK - Dialog](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/experimental/dialog.md).</span></span>

<br>

---

## <a name="see-also"></a><span data-ttu-id="5fffa-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5fffa-116">See also</span></span>

* [<span data-ttu-id="5fffa-117">游標</span><span class="sxs-lookup"><span data-stu-id="5fffa-117">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="5fffa-118">手部光線</span><span class="sxs-lookup"><span data-stu-id="5fffa-118">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="5fffa-119">Button</span><span class="sxs-lookup"><span data-stu-id="5fffa-119">Button</span></span>](button.md)
* [<span data-ttu-id="5fffa-120">可互動的物件</span><span class="sxs-lookup"><span data-stu-id="5fffa-120">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="5fffa-121">週框方塊和應用程式列</span><span class="sxs-lookup"><span data-stu-id="5fffa-121">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="5fffa-122">操作</span><span class="sxs-lookup"><span data-stu-id="5fffa-122">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="5fffa-123">手部功能表</span><span class="sxs-lookup"><span data-stu-id="5fffa-123">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="5fffa-124">近端功能表</span><span class="sxs-lookup"><span data-stu-id="5fffa-124">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="5fffa-125">物件集合</span><span class="sxs-lookup"><span data-stu-id="5fffa-125">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="5fffa-126">語音命令</span><span class="sxs-lookup"><span data-stu-id="5fffa-126">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="5fffa-127">鍵盤</span><span class="sxs-lookup"><span data-stu-id="5fffa-127">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="5fffa-128">工具提示</span><span class="sxs-lookup"><span data-stu-id="5fffa-128">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="5fffa-129">平板</span><span class="sxs-lookup"><span data-stu-id="5fffa-129">Slate</span></span>](slate.md)
* [<span data-ttu-id="5fffa-130">滑桿</span><span class="sxs-lookup"><span data-stu-id="5fffa-130">Slider</span></span>](slider.md)
* [<span data-ttu-id="5fffa-131">著色器</span><span class="sxs-lookup"><span data-stu-id="5fffa-131">Shader</span></span>](shader.md)
* [<span data-ttu-id="5fffa-132">佈告板和常駐標籤</span><span class="sxs-lookup"><span data-stu-id="5fffa-132">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="5fffa-133">顯示進度</span><span class="sxs-lookup"><span data-stu-id="5fffa-133">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="5fffa-134">表面磁性</span><span class="sxs-lookup"><span data-stu-id="5fffa-134">Surface magnetism</span></span>](surface-magnetism.md)
