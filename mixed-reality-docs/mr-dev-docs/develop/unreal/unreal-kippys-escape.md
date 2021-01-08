---
title: 製作 Kippy 的 Escape
description: 當我們探索在 Unreal 引擎中進行 HoloLens 2 的 Kippy Escape mixed reality 應用程式時，請遵循我們的指示。
author: sw5813
ms.author: suwu
ms.date: 9/4/2020
ms.topic: article
keywords: Unreal、Unreal Engine 4、UE4、HoloLens、HoloLens 2、mixed reality、部署至裝置、電腦、檔、混合現實耳機、windows mixed reality 耳機、虛擬實境耳機
appliesto:
- HoloLens 2
ms.openlocfilehash: df199b6a3215158e15fb1252dd75c58aea5bc2ab
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2021
ms.locfileid: "98010038"
---
# <a name="the-making-of-kippys-escape"></a><span data-ttu-id="3834b-104">製作 Kippy 的 Escape</span><span class="sxs-lookup"><span data-stu-id="3834b-104">The Making of Kippy's Escape</span></span>

<span data-ttu-id="3834b-105">Kippy 機器人喚醒以找出自己在島上的孤立狀態。</span><span class="sxs-lookup"><span data-stu-id="3834b-105">Kippy the robot wakes up to find itself stranded on an island.</span></span> <span data-ttu-id="3834b-106">您可以自行專注于問題解決 hat，以協助 it 尋找 rocket 出貨的途徑！</span><span class="sxs-lookup"><span data-stu-id="3834b-106">It’s up to you to put on your problem-solving hat to help it find a path back to its rocket ship!</span></span> <span data-ttu-id="3834b-107">在您的 HoloLens 2 上，從 Microsoft Store [下載應用程式](https://www.microsoft.com/p/kippys-escape/9nbd7gl86vkd) ，或從 GitHub 複製存放 [庫](https://github.com/microsoft/MixedReality-Unreal-KippysEscape) ，並取得 Kippy 家用安全！</span><span class="sxs-lookup"><span data-stu-id="3834b-107">Strap on your HoloLens 2 and [download the app](https://www.microsoft.com/p/kippys-escape/9nbd7gl86vkd) from the Microsoft Store or clone the [repository](https://github.com/microsoft/MixedReality-Unreal-KippysEscape) from GitHub and get Kippy home safe!</span></span>  

> [!IMPORTANT]
> <span data-ttu-id="3834b-108">如果您是從 GitHub 存放庫建立 Kippy 的 Escape，請確定您使用的是 **Unreal Engine 4.25 或更新版本** 。</span><span class="sxs-lookup"><span data-stu-id="3834b-108">Make sure you're using **Unreal Engine 4.25 or later** if you're building Kippy's Escape from the GitHub repository.</span></span>

<span data-ttu-id="3834b-109">Kippy 的 Escape 是一個開放原始碼 [HoloLens 2](https://docs.microsoft.com/hololens/hololens2-hardware) 範例應用程式，使用 Unreal Engine 4 和 [混合現實 UX 工具進行 Unreal](https://github.com/microsoft/MixedReality-UXTools-Unreal)。</span><span class="sxs-lookup"><span data-stu-id="3834b-109">Kippy’s Escape is an open-source [HoloLens 2](https://docs.microsoft.com/hololens/hololens2-hardware) sample app built with Unreal Engine 4 and [Mixed Reality UX Tools for Unreal](https://github.com/microsoft/MixedReality-UXTools-Unreal).</span></span> <span data-ttu-id="3834b-110">在這篇文章中，我們將逐步引導您完成我們的程式，從第一個原則和視覺化設計，到實施和優化體驗。</span><span class="sxs-lookup"><span data-stu-id="3834b-110">In this post, we’ll walk you through our process from first principles and visual design to implementing and optimizing the experience.</span></span> <span data-ttu-id="3834b-111">您可以在 [Unreal 開發總覽](unreal-development-overview.md)中找到使用 MRTK UX 工具開發混合現實應用程式的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="3834b-111">You can find more information on developing Mixed Reality applications with MRTK UX Tools in the [Unreal development overview](unreal-development-overview.md).</span></span>

## <a name="first-principles"></a><span data-ttu-id="3834b-112">第一個原則</span><span class="sxs-lookup"><span data-stu-id="3834b-112">First principles</span></span> 

<span data-ttu-id="3834b-113">在設定以建立 Kippy 的轉型時，我們的目標是要建立一項體驗來強調 [Unreal 引擎的 HoloLens 2 支援](https://docs.unrealengine.com/Platforms/AR/HoloLens2/index.html)、HoloLens 2 的功能，以及混合現實工具組。</span><span class="sxs-lookup"><span data-stu-id="3834b-113">In setting out to create Kippy’s Escape, our goal was to create an experience that would highlight [Unreal Engine’s HoloLens 2 support](https://docs.unrealengine.com/Platforms/AR/HoloLens2/index.html), the HoloLens 2’s capabilities, and the Mixed Reality Toolkit.</span></span> <span data-ttu-id="3834b-114">我們想要讓開發人員能夠想像他們可以使用 Unreal 和 HoloLens 2 來建立的功能。</span><span class="sxs-lookup"><span data-stu-id="3834b-114">We wanted to inspire developers to imagine what they could create with Unreal and HoloLens 2.</span></span>  

<span data-ttu-id="3834b-115">我們針對此體驗有三個指導準則：它需要有趣、互動，而且進入的障礙很低。</span><span class="sxs-lookup"><span data-stu-id="3834b-115">We came up with three guiding principles for the experience: that it needed to be fun, interactive, and have a low barrier to entry.</span></span> <span data-ttu-id="3834b-116">我們希望體驗的視覺效果足夠，即使是首次的混合現實使用者也不需要教學課程。</span><span class="sxs-lookup"><span data-stu-id="3834b-116">We wanted the experience to be intuitive enough that even a first-time mixed reality user won’t need a tutorial to go through it.</span></span>  

## <a name="designing-the-game"></a><span data-ttu-id="3834b-117">設計遊戲</span><span class="sxs-lookup"><span data-stu-id="3834b-117">Designing the game</span></span> 

<span data-ttu-id="3834b-118">HoloLens 2 可以存取設計功能，目前在遊戲中有其他地方。</span><span class="sxs-lookup"><span data-stu-id="3834b-118">The HoloLens 2 has access to design features found nowhere else in gaming today.</span></span> <span data-ttu-id="3834b-119">您可以使用您的手或以眼睛追蹤作為目標，直接推送或操作物件。</span><span class="sxs-lookup"><span data-stu-id="3834b-119">Objects can be directly pushed or manipulated using your hands or targeted with eye tracking.</span></span> <span data-ttu-id="3834b-120">這些主要功能的背後，是我們在 Kippy 的轉換程式中所建立的一些有趣的部分。</span><span class="sxs-lookup"><span data-stu-id="3834b-120">These key features are behind some of the fun moments we built out in Kippy’s Escape.</span></span>  

<span data-ttu-id="3834b-121">使用獨特的 HoloLens 2 功能做為遊戲設計的指導方針，我們已將一些小型環境案例的範圍限定在其中。</span><span class="sxs-lookup"><span data-stu-id="3834b-121">Using the unique HoloLens 2 features as guidance for our game design, we scoped out a few small environment scenarios.</span></span> <span data-ttu-id="3834b-122">孤島有意義，因為可以針對不同的播放程式高度進行調整，並提供一些有趣的橋樑想法。</span><span class="sxs-lookup"><span data-stu-id="3834b-122">Islands made sense because they can be adjusted for different player heights, and provided some entertaining bridge ideas.</span></span> <span data-ttu-id="3834b-123">我們進入了古文明的主題，以符合科幻-fi 技術的概念，也就是有人在毀損上建立的機械，利用了每個島所提供的奇怪能源。</span><span class="sxs-lookup"><span data-stu-id="3834b-123">We landed on the theme of ancient civilization meets sci-fi tech, with the idea that someone had built machinery over ruins harnessing a strange energy provided by each island.</span></span> <span data-ttu-id="3834b-124">每個孤島都有各自的外觀和操作，這是協助您建立視覺興趣的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="3834b-124">The islands were each given their own look and feel, a detail that helped create visual interest.</span></span> <span data-ttu-id="3834b-125">模型化和紋理之間的良好平衡會讓繪製呼叫的效能降低，以呈現效能，因此設計風格的外觀是以這種方式設計。</span><span class="sxs-lookup"><span data-stu-id="3834b-125">A good balance between modeling and texturing would keep draw calls low for rendering performance, so a stylized look was designed with that in mind.</span></span> 

<span data-ttu-id="3834b-126">![早期遊戲設計 ](images/kippys-escape/kippys-escape-img-01.png)
 *會針對體驗的外觀進行一些早期的草圖*</span><span class="sxs-lookup"><span data-stu-id="3834b-126">![Early game design sketches](images/kippys-escape/kippys-escape-img-01.png)
*Some early sketches for what the experience might look like*</span></span>

<span data-ttu-id="3834b-127">![](images/kippys-escape/kippys-escape-img-02.png)
*第二島* 的第二個島轉譯轉譯</span><span class="sxs-lookup"><span data-stu-id="3834b-127">![Renderings of the second island](images/kippys-escape/kippys-escape-img-02.png)
*Renderings of the second island*</span></span>

<span data-ttu-id="3834b-128">為了維持在短期的生產環境中，我們同意浮動字元可能會在沒有嚴格動畫迴圈的情況下捕捉意圖和表情。</span><span class="sxs-lookup"><span data-stu-id="3834b-128">To keep within our short production schedule, we agreed that a floating character could capture intent and emotion without rigorous animation cycles.</span></span> <span data-ttu-id="3834b-129">所以 Kippy 是出生的！</span><span class="sxs-lookup"><span data-stu-id="3834b-129">And so Kippy was born!</span></span> <span data-ttu-id="3834b-130">它會透過其眼睛 emotes 幾個不同的運算式，並透過 minimalistic 關切這個領域音效，協助引導玩家體驗整個體驗。</span><span class="sxs-lookup"><span data-stu-id="3834b-130">It emotes a few different expressions through its eyes and through minimalistic vocal sound effects to help guide the player throughout the experience.</span></span> 

![Kippy 透過其眼睛顯示不同的運算式](images/kippys-escape/kippys-escape-img-03.gif)

<span data-ttu-id="3834b-132">*Kippy 透過其眼睛顯示不同的運算式*</span><span class="sxs-lookup"><span data-stu-id="3834b-132">*Kippy showing different expressions via its eyes*</span></span>

![如果使用者花太多時間來解決謎題，Kippy 會為使用者提供提示](images/kippys-escape/kippys-escape-img-04.gif)

<span data-ttu-id="3834b-134">*如果使用者花太多時間來解決謎題，Kippy 會為使用者提供提示*</span><span class="sxs-lookup"><span data-stu-id="3834b-134">*If the user takes too long to solve a puzzle, Kippy will give the user a hint*</span></span>

<span data-ttu-id="3834b-135">除了字元和環境設計之外，我們也一致了讓遊戲感到有趣的工作。</span><span class="sxs-lookup"><span data-stu-id="3834b-135">Beyond the character and environment design, we made a concerted effort to make the game feel fun.</span></span> <span data-ttu-id="3834b-136">眼睛追蹤可讓我們引發材質和音效屬性，這些屬性強調遊戲的重要部分。</span><span class="sxs-lookup"><span data-stu-id="3834b-136">Eye tracking allowed us to fire off material and sound attributes, which highlighted key pieces of the game.</span></span> <span data-ttu-id="3834b-137">空間音訊可協助您在玩家的環境中，讓這些層級在家裡的外觀。</span><span class="sxs-lookup"><span data-stu-id="3834b-137">Spatial audio helped make the levels feel at home in the player’s surroundings.</span></span> <span data-ttu-id="3834b-138">能夠抓取物件、推播按鈕和操作滑杆，推動創新的玩家參與。</span><span class="sxs-lookup"><span data-stu-id="3834b-138">Being able to grab objects, push buttons, and manipulate sliders drives innovative player engagements.</span></span> <span data-ttu-id="3834b-139">請務必確定這些連接點都有自然的感覺。</span><span class="sxs-lookup"><span data-stu-id="3834b-139">It was important to make sure these connection points felt natural.</span></span> 

![橋接器纜線的尾端會在使用者的手上進行時發光](images/kippys-escape/kippys-escape-img-05.gif)

<span data-ttu-id="3834b-141">*橋接器纜線的尾端會在使用者的手上進行時發光*</span><span class="sxs-lookup"><span data-stu-id="3834b-141">*The end of the bridge cable glows when the user’s hand approaches it*</span></span>

## <a name="building-the-game-mechanics"></a><span data-ttu-id="3834b-142">打造遊戲機制</span><span class="sxs-lookup"><span data-stu-id="3834b-142">Building the game mechanics</span></span> 

<span data-ttu-id="3834b-143">Kippy 的 Escape 高度依賴混合現實 UX 工具元件，讓遊戲成為互動的互動動作專案、界限控制項、操作工具、滑杆和按鈕。</span><span class="sxs-lookup"><span data-stu-id="3834b-143">Kippy’s Escape relies heavily on Mixed Reality UX Tools components to make the game interactive - namely hand interaction actors, bounds controls, manipulators, sliders, and buttons.</span></span>   

<span data-ttu-id="3834b-144">「 [手上互動](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.9.x/Docs/HandInteraction.html) 」動作專案可讓您直接操作或同時管理全像。</span><span class="sxs-lookup"><span data-stu-id="3834b-144">The [hand interaction actor](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.9.x/Docs/HandInteraction.html) enables both direct and far manipulation of holograms.</span></span> <span data-ttu-id="3834b-145">在 Kippy 的 Escape 開始時，使用者有機會設定遊戲的位置。</span><span class="sxs-lookup"><span data-stu-id="3834b-145">At the start of Kippy’s Escape, the user is given the opportunity to set the location of the game.</span></span> <span data-ttu-id="3834b-146">從使用者的掌上字形狀延伸，可讓您輕鬆地操作距離較遠的大型全息圖，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="3834b-146">Hand beams extending from the user’s palm make it easy to manipulate large holograms that are far away, as seen in the gif below.</span></span>  

![手邊互動執行者 gif](images/kippys-escape/kippys-escape-img-06.gif)

<span data-ttu-id="3834b-148">您可以使用 UX 工具的 [界限控制項](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.9.x/Docs/BoundsControl.html) 元件來拖曳和旋轉預留位置場景本身。</span><span class="sxs-lookup"><span data-stu-id="3834b-148">The placeholder scene itself can be dragged and rotated using UX Tools’ [bounds control](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.9.x/Docs/BoundsControl.html) component.</span></span>  

<span data-ttu-id="3834b-149">在第二個島上，使用者必須挑選 gem，並將它們放在其相符的位置。</span><span class="sxs-lookup"><span data-stu-id="3834b-149">On the second island, the user must pick up gems and place them in their matching slots.</span></span> <span data-ttu-id="3834b-150">Gem 已附加操作工具， [可讓使用者](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.9.x/Docs/Manipulator.html) 挑選它們並將其放在下方。</span><span class="sxs-lookup"><span data-stu-id="3834b-150">The gems have [manipulators](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.9.x/Docs/Manipulator.html) attached to them that allow the user to pick them up and place them down.</span></span> 

![操作工具範例 gif](images/kippys-escape/kippys-escape-img-07.gif)

<span data-ttu-id="3834b-152">[Pressable 按鈕](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.9.x/Docs/PressableButton.html)是讓炸彈在第三島上使用的關鍵。</span><span class="sxs-lookup"><span data-stu-id="3834b-152">A [pressable button](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.9.x/Docs/PressableButton.html) is the key to bringing up bombs for use on the third island.</span></span>  

![Pressable 按鈕範例 gif](images/kippys-escape/kippys-escape-img-08.gif)

<span data-ttu-id="3834b-154">[滑杆](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.9.x/Docs/PinchSlider.html)元件會出現在第四個島上，觸發最後一個要引發的橋接器。</span><span class="sxs-lookup"><span data-stu-id="3834b-154">A [slider](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.9.x/Docs/PinchSlider.html) component appears on the fourth island, triggering the final bridge to be raised.</span></span>  

![滑杆元件範例 gif](images/kippys-escape/kippys-escape-img-09.gif) 

## <a name="optimizing-for-hololens-2"></a><span data-ttu-id="3834b-156">HoloLens 2 的優化</span><span class="sxs-lookup"><span data-stu-id="3834b-156">Optimizing for HoloLens 2</span></span> 

<span data-ttu-id="3834b-157">在行動裝置上建立的任何體驗中，請注意效能很重要。</span><span class="sxs-lookup"><span data-stu-id="3834b-157">With any experience built to run on a mobile device, keeping an eye on performance is critical.</span></span> <span data-ttu-id="3834b-158">Unreal 4.25 包含支援行動多重視圖的重大更新，可大幅減少轉譯的負荷並提高畫面播放速率。</span><span class="sxs-lookup"><span data-stu-id="3834b-158">Unreal 4.25 includes a major update to support for mobile multi-view, which significantly reduces rendering overhead and boosts frame-rate.</span></span> <span data-ttu-id="3834b-159">建議您在優化時，查看其他 [建議的效能設定](performance-recommendations-for-unreal.md) ，以使用 Unreal 進行 HoloLens 2 開發。</span><span class="sxs-lookup"><span data-stu-id="3834b-159">We recommend checking out our other [recommended performance settings](performance-recommendations-for-unreal.md) for HoloLens 2 development with Unreal when you're optimizing.</span></span>  

<span data-ttu-id="3834b-160">物理物件的效能仍維持昂貴，因此使用了一些聰明的因應措施。</span><span class="sxs-lookup"><span data-stu-id="3834b-160">Physics objects still remain costly for performance, so a couple clever workarounds were used.</span></span> <span data-ttu-id="3834b-161">比方說，第三個「橋接器」需要吹出一些阻礙 stairway 的碎屑。</span><span class="sxs-lookup"><span data-stu-id="3834b-161">For instance, the third “bridge” requires blowing up some debris blocking the stairway.</span></span> <span data-ttu-id="3834b-162">因為炸彈引爆會觸發交換、切換靜態石子以進行爆炸式物件效果，而不會強制將石子視為物理物件。</span><span class="sxs-lookup"><span data-stu-id="3834b-162">Instead of having a force impact the stones as physics objects, the bomb detonation triggers a swap, switching the static stones for an exploding particle effect.</span></span> 

![HoloLens 2 gif 的優化範例](images/kippys-escape/kippys-escape-img-10.gif) 

<span data-ttu-id="3834b-164">我們也會將我們的繪製呼叫從400減少到 ~ 260，方法如下：</span><span class="sxs-lookup"><span data-stu-id="3834b-164">We also cut down our draw calls from over 400 to  ~260 by:</span></span> 
* <span data-ttu-id="3834b-165">降低網格複雜度</span><span class="sxs-lookup"><span data-stu-id="3834b-165">Reducing mesh complexity</span></span>
* <span data-ttu-id="3834b-166">組合網格</span><span class="sxs-lookup"><span data-stu-id="3834b-166">Combining meshes</span></span>
* <span data-ttu-id="3834b-167">移除一些初始動態光源元素</span><span class="sxs-lookup"><span data-stu-id="3834b-167">Removing some of our initial dynamic lighting elements</span></span>

<span data-ttu-id="3834b-168">雖然我們可能會有更多工作，但我們認為這在效能與視覺品質之間是一個良好的平衡。</span><span class="sxs-lookup"><span data-stu-id="3834b-168">While there’s likely more we could have done, we felt that was a good balance between performance and visual quality.</span></span>  

## <a name="try-it-out"></a><span data-ttu-id="3834b-169">試試看！</span><span class="sxs-lookup"><span data-stu-id="3834b-169">Try it out!</span></span> 

<span data-ttu-id="3834b-170">啟動您的 HoloLens 2 並從 Microsoft Store [下載](https://www.microsoft.com/p/kippys-escape/9nbd7gl86vkd) 應用程式，或從 GitHub 複製存放 [庫](https://github.com/microsoft/MixedReality-Unreal-KippysEscape) ，自行建立應用程式！</span><span class="sxs-lookup"><span data-stu-id="3834b-170">Boot up your HoloLens 2 and [download](https://www.microsoft.com/p/kippys-escape/9nbd7gl86vkd) the app from the Microsoft Store, or clone the [repository](https://github.com/microsoft/MixedReality-Unreal-KippysEscape) from GitHub and build the app yourself!</span></span>  

## <a name="about-the-team"></a><span data-ttu-id="3834b-171">關於小組</span><span class="sxs-lookup"><span data-stu-id="3834b-171">About the team</span></span>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Jack Caron" width="60" height="60" src="images/kippys-escape/jack-caron.jpg"></td>
<td style="border-style: none"><span data-ttu-id="3834b-172"><b>插座</b></span><span class="sxs-lookup"><span data-stu-id="3834b-172"><b>Jack Caron</b></span></span><br><span data-ttu-id="3834b-173"><i>領導遊戲設計工具</i></span><span class="sxs-lookup"><span data-stu-id="3834b-173"><i>Lead Game Designer</i></span></span><br><span data-ttu-id="3834b-174">目前的「插座」適用于 Microsoft 的混合現實體驗，包括 HoloLens 2 專案和 AltspaceVR，而且之前是 HoloLens 平臺小組的設計工具。</span><span class="sxs-lookup"><span data-stu-id="3834b-174">Jack currently works on Mixed Reality experiences for Microsoft, including HoloLens 2 projects and AltspaceVR, and was previously a designer on the HoloLens platform team.</span></span></td>
</tr>
</table>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Summer Wu" width="60" height="60" src="images/kippys-escape/summer-wu.jpg"></td>
<td style="border-style: none"><span data-ttu-id="3834b-175"><b>夏天 Wu</b></span><span class="sxs-lookup"><span data-stu-id="3834b-175"><b>Summer Wu</b></span></span><br><span data-ttu-id="3834b-176"><i>產生器 (producer)</i></span><span class="sxs-lookup"><span data-stu-id="3834b-176"><i>Producer</i></span></span><br><span data-ttu-id="3834b-177">夏天在混合現實開發人員平臺上運作，並且與小組 Unreal 引擎的相關工作進行領導。</span><span class="sxs-lookup"><span data-stu-id="3834b-177">Summer works on the mixed reality developer platform and heads the team’s Unreal Engine related efforts.</span></span></td>
</tr>
</table>

<span data-ttu-id="3834b-178">特別感謝我們的朋友 [Framestore](https://www.framestore.com/) ，協助我們將 Kippy 的轉換至生命。</span><span class="sxs-lookup"><span data-stu-id="3834b-178">Special thanks to our friends at [Framestore](https://www.framestore.com/) for helping us bring Kippy’s Escape to life.</span></span> <span data-ttu-id="3834b-179">從字元開發到資產設計，到遊戲程式設計，在此專案上進行共同作業的 pivotal。</span><span class="sxs-lookup"><span data-stu-id="3834b-179">From character development, to asset design, to game programming, their collaboration on this project was pivotal.</span></span>  