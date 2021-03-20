---
title: 顯示 Azure Spatial Anchors 意見反應
description: 完成此課程，以了解如何在混合實境應用程式中顯示來自 Azure Spatial Anchors 的意見反應。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens, MRTK, 混合實境工具組, UWP, Azure 空間錨點, 工作階段, 回饋元素
ms.localizationpriority: high
ms.openlocfilehash: f5f92d8b19da6a449b8630d7f87e0719e438b4ab
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "99590670"
---
# <a name="4-displaying-feedback-from-azure-spatial-anchors"></a><span data-ttu-id="3609a-104">4.顯示 Azure Spatial Anchors 的意見反應</span><span class="sxs-lookup"><span data-stu-id="3609a-104">4. Displaying feedback from Azure Spatial Anchors</span></span>

<span data-ttu-id="3609a-105">在本教學課程中，您將了解如何為使用者提供使用 Azure Spatial Anchors (ASA) 的相關錨點探索、事件和狀態的相關回饋。</span><span class="sxs-lookup"><span data-stu-id="3609a-105">In this tutorial, you will learn how to provide users with feedback about anchor discovery, events, and status using Azure Spatial Anchors (ASA).</span></span>

## <a name="objectives"></a><span data-ttu-id="3609a-106">目標</span><span class="sxs-lookup"><span data-stu-id="3609a-106">Objectives</span></span>

* <span data-ttu-id="3609a-107">了解如何設定 UI 面板，以顯示目前 ASA 工作階段的相關重要資訊</span><span class="sxs-lookup"><span data-stu-id="3609a-107">Learn how to set up a UI panel that displays essential information about the current ASA session</span></span>
* <span data-ttu-id="3609a-108">了解並探索 ASA SDK 可供使用者使用的回饋元素</span><span class="sxs-lookup"><span data-stu-id="3609a-108">learn about and explore feedback elements that the ASA SDK makes available to users</span></span>

## <a name="setting-up-asa-feedback-panel"></a><span data-ttu-id="3609a-109">設定 ASA 意見反應面板</span><span class="sxs-lookup"><span data-stu-id="3609a-109">Setting up ASA feedback panel</span></span>

<span data-ttu-id="3609a-110">在階層視窗中，以滑鼠右鍵按一下 [指示] >  [TextContent] 物件。</span><span class="sxs-lookup"><span data-stu-id="3609a-110">In the Hierarchy window, right-click on the **Instructions** > **TextContent** object.</span></span> <span data-ttu-id="3609a-111">選取 [3D 物件] >  [文字 - TextMeshPro]，將 TextMeshPro 文字物件建立為指示 > TextContent 物件的子系：</span><span class="sxs-lookup"><span data-stu-id="3609a-111">Select **3D Object** > **Text - TextMeshPro** to create a TextMeshPro text object as a child of the Instructions > TextContent object:</span></span>

![已選取新建立 TextMeshPro 物件的 Unity](images/mr-learning-asa/asa-04-section1-step1-1.png)

> [!TIP]
> <span data-ttu-id="3609a-113">若要更簡便地使用場景，請按一下物件左邊的眼睛圖示，將 ParentAnchor 物件的<a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">場景可見度</a>設為關閉。</span><span class="sxs-lookup"><span data-stu-id="3609a-113">To make it easier to work with your scene, set the  <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">Scene Visibility</a> for the ParentAnchor object to off by clicking the eye icon to the left of the object.</span></span> <span data-ttu-id="3609a-114">這會在場景視窗中隱藏物件，而不會變更其遊戲內的可見度。</span><span class="sxs-lookup"><span data-stu-id="3609a-114">This hides the object in the Scene window without changing their in-game visibility.</span></span>

<span data-ttu-id="3609a-115">將新建立的文字 (TMP) 物件 **意見反應** 重新命名，接著在 [偵測器] 視窗中變更其位置和大小，使其整齊地放在指示文字底下，例如：</span><span class="sxs-lookup"><span data-stu-id="3609a-115">Rename the newly created Text (TMP) object **Feedback**, then, in the Inspector window, change its position and size, so it is placed neatly underneath the instruction text, for example:</span></span>

* <span data-ttu-id="3609a-116">將矩形變形元件的 **Y 位置** 變更為 -0.24。</span><span class="sxs-lookup"><span data-stu-id="3609a-116">Change the Rect Transform component's **Pos Y** to -0.24.</span></span>
* <span data-ttu-id="3609a-117">將矩形變形元件的 **寬度** 變更為 0.555。</span><span class="sxs-lookup"><span data-stu-id="3609a-117">Change the Rect Transform component's **Width** to 0.555.</span></span>
* <span data-ttu-id="3609a-118">將矩形變形元件的 **高度** 變更為 0.1。</span><span class="sxs-lookup"><span data-stu-id="3609a-118">Change the Rect Transform component's **Height** to 0.1.</span></span>

<span data-ttu-id="3609a-119">然後選擇字型屬性，讓文字適當地放在文字區域中，例如：</span><span class="sxs-lookup"><span data-stu-id="3609a-119">Then choose font properties, so the text fits nicely within the text area, for example:</span></span>

* <span data-ttu-id="3609a-120">將 TextMeshPro - 文字元件的 **字型樣式** 變更為粗體。</span><span class="sxs-lookup"><span data-stu-id="3609a-120">Change the TextMeshPro - Text component's **Font Style** to Bold.</span></span>
* <span data-ttu-id="3609a-121">將 TextMeshPro - 文字元件的 **字型大小** 變更為 0.17。</span><span class="sxs-lookup"><span data-stu-id="3609a-121">Change the TextMeshPro - Text component's **Font Size** to 0.17.</span></span>
* <span data-ttu-id="3609a-122">將 TextMeshPro 文字元件的 **對齊** 變更為置中和中間。</span><span class="sxs-lookup"><span data-stu-id="3609a-122">Change the TextMeshPro - Text component's **Alignment** to Center and Middle.</span></span>

![已設定意見反應物件的 Unity](images/mr-learning-asa/asa-04-section1-step1-2.png)

<span data-ttu-id="3609a-124">在階層視窗中再次選取 [意見反應] 物件，然後在偵測器視窗中使用 [新增元件] 按鈕來新增 **錨點意見反應指令碼 (指令碼)** 元件，並進行以下設定：</span><span class="sxs-lookup"><span data-stu-id="3609a-124">In the Hierarchy window, select the **Feedback** object still, then in the Inspector window, use the **Add Component** button to add the **Anchor Feedback Script (Script)** component and configure it as follows:</span></span>

* <span data-ttu-id="3609a-125">將 **Feedback** 物件本身指派給 **Anchor Feedback Script (指令碼)** 元件的 [回饋文字] 欄位。</span><span class="sxs-lookup"><span data-stu-id="3609a-125">Assign the **Feedback** object itself to the **Anchor Feedback Script (Script)** component's **Feedback Text** field.</span></span>

![已設定 Anchor Feedback Script 元件的 Unity](images/mr-learning-asa/asa-04-section1-step1-3.png)

## <a name="congratulations"></a><span data-ttu-id="3609a-127">恭喜！</span><span class="sxs-lookup"><span data-stu-id="3609a-127">Congratulations</span></span>

<span data-ttu-id="3609a-128">在本教學課程中，您已了解如何建立 UI 面板。</span><span class="sxs-lookup"><span data-stu-id="3609a-128">In this tutorial, you learned how to create a UI panel.</span></span> <span data-ttu-id="3609a-129">該面板會顯示 Azure Spatial Anchors 體驗的目前狀態，以提供即時的使用者意見反應。</span><span class="sxs-lookup"><span data-stu-id="3609a-129">It displays the current status of the Azure Spatial Anchors experience for providing users with real-time feedback.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="3609a-130">下一個教學課程：5.適用於 Android 和 iOS 的 Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="3609a-130">Next Tutorial: 5. Azure Spatial Anchors for Android and iOS</span></span>](mr-learning-asa-05.md)
