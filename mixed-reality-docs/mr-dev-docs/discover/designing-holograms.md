---
title: 設計全像投影
description: 透過 Microsoft 全新的設計全像影像應用程式，瞭解混合的現實。
author: hferrone
ms.author: daescu
ms.date: 11/24/2020
ms.topic: article
keywords: MRTK，混合的現實工具組，全像投影，設計全像投影、學習、範例應用程式、混合現實耳機、虛擬實境耳機、何謂虛擬實境
ms.openlocfilehash: 2480b5e0b4dca502c746dad6f070226ffa8cd1f9
ms.sourcegitcommit: 8d3b84d2aa01f078ecf92cec001a252e3ea7b24d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2020
ms.locfileid: "97757756"
---
# <a name="the-making-of-designing-holograms"></a><span data-ttu-id="0bcb1-104">設計全息製作</span><span class="sxs-lookup"><span data-stu-id="0bcb1-104">The making of Designing Holograms</span></span>

> [!NOTE]
> <span data-ttu-id="0bcb1-105">請在此頁面上，允許小型載入視窗，以將所有酷炫的 Gif 和 embedded 影片全部考慮。</span><span class="sxs-lookup"><span data-stu-id="0bcb1-105">Please allow for a small loading window to account for all the cool GIFs and embedded videos on this page.</span></span>

<span data-ttu-id="0bcb1-106">學習如何設計混合的現實可能很困難，因為媒體不一定會轉譯成2D 設計流程。</span><span class="sxs-lookup"><span data-stu-id="0bcb1-106">Learning how to design for mixed reality can be hard because the medium doesn't always translate well to 2D design processes.</span></span> <span data-ttu-id="0bcb1-107">在 Microsoft，我們為 HoloLens 2 建立了免費的應用程式，協助您瞭解混合現實 UX 設計第一手的基本概念。</span><span class="sxs-lookup"><span data-stu-id="0bcb1-107">Here at Microsoft, we've created a free app for the HoloLens 2 to help you learn the fundamentals of mixed reality UX Design firsthand.</span></span> <span data-ttu-id="0bcb1-108">設計全像影像應用程式的獨特方法是探討混合現實行為、秘訣和建議，以協助您建立自己的吸引人和出色的 HoloLens 應用程式。</span><span class="sxs-lookup"><span data-stu-id="0bcb1-108">The unique approach of the Designing Holograms app dives into mixed reality behaviors, tips, and recommendations to help you create engaging and amazing HoloLens apps of your own.</span></span> <span data-ttu-id="0bcb1-109">從 Microsoft Store 免費下載應用程式，並從 Microsoft 的混合現實設計小組學習！</span><span class="sxs-lookup"><span data-stu-id="0bcb1-109">Download the app for free from the Microsoft Store and learn from Microsoft’s Mixed Reality Design Team!</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="0bcb1-110">下載設計全像影像應用程式</span><span class="sxs-lookup"><span data-stu-id="0bcb1-110">Download the Designing Holograms app</span></span>](https://www.microsoft.com/p/designing-holograms/9nxwnjklrzwd)

<br>

![設計全息圖的示範房間中的標頭追蹤場景動畫 GIF](images/designing-holograms/demo-room.gif)

<span data-ttu-id="0bcb1-112">*設計全息圖的示範房間 (也稱為娃娃房子)*</span><span class="sxs-lookup"><span data-stu-id="0bcb1-112">*Designing Hologram’s demo room (also known as the doll house)*</span></span>

## <a name="designing-for-mixed-reality"></a><span data-ttu-id="0bcb1-113">混合現實的設計</span><span class="sxs-lookup"><span data-stu-id="0bcb1-113">Designing for mixed reality</span></span>

<span data-ttu-id="0bcb1-114">我和許多人一樣，都是用來設計行動應用程式。</span><span class="sxs-lookup"><span data-stu-id="0bcb1-114">Like many of you, I used to design mobile apps.</span></span> <span data-ttu-id="0bcb1-115">從2D 設計世界開始，一直到目前為止都在世界各地的空間運算，一直都是很大的轉變。</span><span class="sxs-lookup"><span data-stu-id="0bcb1-115">Coming from a 2D design world, jumping into full on spatial computing, where everything is now in the world, was a significant shift.</span></span> <span data-ttu-id="0bcb1-116">在混合的現實情況下，應用程式不會再局限于2D 螢幕;事實上，它們幾乎是免費的，放在真實世界中，並與實際物件互動。</span><span class="sxs-lookup"><span data-stu-id="0bcb1-116">In mixed reality, apps aren't confined to a 2D screen anymore; in fact, they're almost free, placed in the real world and interacting with real objects.</span></span>

<span data-ttu-id="0bcb1-117">對我來說，將3D 體驗連接到傳統2D 設計程式是混合現實開發最具挑戰性的層面。</span><span class="sxs-lookup"><span data-stu-id="0bcb1-117">To me, connecting 3D experiences to conventional 2D design processes is the most challenging aspect of mixed reality development.</span></span> <span data-ttu-id="0bcb1-118">在與客戶對話的情況下，我會聽到像是「我知道要包含哪些功能，以及如何讓它們正常運作。</span><span class="sxs-lookup"><span data-stu-id="0bcb1-118">In conversations with customers, I would hear things like “I know what features to include and how to get them up and running.</span></span> <span data-ttu-id="0bcb1-119">它是程式碼，我可以遵循檔和教學課程，但是使用者體驗？</span><span class="sxs-lookup"><span data-stu-id="0bcb1-119">It’s code, I can follow the docs and tutorials, but the user experience?</span></span> <span data-ttu-id="0bcb1-120">許多功能、不同的輸入選項、不同的案例和實體環境都很龐大」。</span><span class="sxs-lookup"><span data-stu-id="0bcb1-120">So many features, different input options, different scenarios, and physical environments, it’s overwhelming".</span></span>

<span data-ttu-id="0bcb1-121">![來自三藩市的 HoloLens 2 設計研討會中的影像 ](images/designing-holograms/workshop.jpeg)
 *，從三藩市的 HoloLens 2 設計研討會*</span><span class="sxs-lookup"><span data-stu-id="0bcb1-121">![Image from the HoloLens 2 Design Workshop in San Francisco](images/designing-holograms/workshop.jpeg)
*Image from the HoloLens 2 Design Workshop in San Francisco*</span></span>

## <a name="an-opportunity-to-teach"></a><span data-ttu-id="0bcb1-122">教授的機會</span><span class="sxs-lookup"><span data-stu-id="0bcb1-122">An opportunity to teach</span></span>

<span data-ttu-id="0bcb1-123">它一開始並不明顯，但有一個絕佳的機會，可以使用 mixed reality 作為媒體來教授。</span><span class="sxs-lookup"><span data-stu-id="0bcb1-123">It wasn’t obvious at first, but an excellent opportunity was presented to use mixed reality as a Medium to teach it.</span></span>

<span data-ttu-id="0bcb1-124">設計全像影像是一種視覺體驗，可解釋混合的現實設計概念和建議。</span><span class="sxs-lookup"><span data-stu-id="0bcb1-124">Designing Holograms is a visual experience that explains mixed reality design concepts and recommendations.</span></span> <span data-ttu-id="0bcb1-125">這只是您和一個示範混合現實設計概念的虛擬老師。</span><span class="sxs-lookup"><span data-stu-id="0bcb1-125">It’s just you and a virtual teacher demonstrating mixed reality design concepts.</span></span> <span data-ttu-id="0bcb1-126">所有專案都是從第三個人的觀點來看，在您自己的空間中有很穩固的體驗。</span><span class="sxs-lookup"><span data-stu-id="0bcb1-126">Everything is from a third person perspective with the experience firmly in your own space.</span></span>

<br>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Designing-Holograms-app-trailer/player]

<span data-ttu-id="0bcb1-127">*設計全像投影片影片*</span><span class="sxs-lookup"><span data-stu-id="0bcb1-127">*Designing Holograms trailer video*</span></span>

## <a name="exploring-the-doll-house"></a><span data-ttu-id="0bcb1-128">探索娃娃房子</span><span class="sxs-lookup"><span data-stu-id="0bcb1-128">Exploring the doll house</span></span>

<span data-ttu-id="0bcb1-129">娃娃房子是我們在整個應用程式中使用的虛擬環境。</span><span class="sxs-lookup"><span data-stu-id="0bcb1-129">The doll house is the virtual environment we use throughout the app.</span></span> <span data-ttu-id="0bcb1-130">環境是 80 x 60 x 40-cm 的空間，其中包含大部分房間共通的基本元素，例如牆壁、燈、傢俱、表格和電視。</span><span class="sxs-lookup"><span data-stu-id="0bcb1-130">The environment is an 80 x 60 x 40-cm miniature room that contains the basic elements that most rooms have in common, like walls, lamps, furniture, a table, and a TV.</span></span> <span data-ttu-id="0bcb1-131">娃娃房子是應用程式體驗的主要 protagonist，因此我們需要確定它在任何環境中都能正常運作。</span><span class="sxs-lookup"><span data-stu-id="0bcb1-131">The doll house is the main protagonist of the app experience, so we needed to make sure it would work great in any environment.</span></span> <span data-ttu-id="0bcb1-132">把它想像成一個小型的示範空間，用來視覺化各種混合現實概念。</span><span class="sxs-lookup"><span data-stu-id="0bcb1-132">Think of it as a small demo room for visualizing all sorts of mixed reality concepts.</span></span>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Dollhouse-adjustment-behavior-in-the-Designing-Holograms-app/player]
<span data-ttu-id="0bcb1-133">*Dollhouse 調整行為的影片*</span><span class="sxs-lookup"><span data-stu-id="0bcb1-133">*Video of the Dollhouse adjustment behavior*</span></span>

### <a name="11-vs-110-prototypes"></a><span data-ttu-id="0bcb1-134">1:1 與1:10 原型</span><span class="sxs-lookup"><span data-stu-id="0bcb1-134">1:1 vs 1:10 prototypes</span></span>

<span data-ttu-id="0bcb1-135">我們最初的假設是，1:1 示範會很令人驚奇，看起來像是真實的老師。</span><span class="sxs-lookup"><span data-stu-id="0bcb1-135">Our initial assumption was that 1:1 demonstrations would be amazing, almost like looking at a real life teacher.</span></span> <span data-ttu-id="0bcb1-136">使用者會看到老師在真實規模中看到的所有內容。</span><span class="sxs-lookup"><span data-stu-id="0bcb1-136">The user would see everything that the teacher sees at a real life scale.</span></span> <span data-ttu-id="0bcb1-137">不過，我們會立即發現有幾個問題：</span><span class="sxs-lookup"><span data-stu-id="0bcb1-137">However, we immediately realized that there would be a few problems:</span></span>

- <span data-ttu-id="0bcb1-138">大部分的開發人員會在辦公室或房間以外的房間內執行其應用程式，因此無法容納。</span><span class="sxs-lookup"><span data-stu-id="0bcb1-138">Most developers will run their apps in offices, or rooms smaller than the demo room, so it wouldn’t fit.</span></span>
- <span data-ttu-id="0bcb1-139">顯示是加總的，這表示整個虛擬環境會在使用者的房間上重迭。</span><span class="sxs-lookup"><span data-stu-id="0bcb1-139">Displays are additive, meaning the entire virtual environment will be overlaid over a user’s room.</span></span> <span data-ttu-id="0bcb1-140">這可能會造成兩個數據表混淆（可能是雙 couches）和沒有對齊的牆。</span><span class="sxs-lookup"><span data-stu-id="0bcb1-140">That can get confusing with two tables, maybe double couches, and walls that don’t align.</span></span>
- <span data-ttu-id="0bcb1-141">而最糟的是，所有虛擬環境都受到視野的高度限制。</span><span class="sxs-lookup"><span data-stu-id="0bcb1-141">And worst of all a virtual environment heavily constrained by a field of view.</span></span>

<span data-ttu-id="0bcb1-142">當我們嘗試迷你1:10 規模時，結果就是一個很棒的鳥，也就是實際的房間。</span><span class="sxs-lookup"><span data-stu-id="0bcb1-142">When we tried out a mini 1:10 scale, the result was a fantastic birds-eye view of a realistic room.</span></span> <span data-ttu-id="0bcb1-143">您可以同時看到所有從任何角度進入的內容。</span><span class="sxs-lookup"><span data-stu-id="0bcb1-143">You could see everything that was going on from any angle all at the same time.</span></span> <span data-ttu-id="0bcb1-144">最令人驚訝的是，大部分的測試人員發現它更能看到較小的版本，而不是切換回1:1 規模。</span><span class="sxs-lookup"><span data-stu-id="0bcb1-144">What was most surprising is that most testers found it so much more immersive to see a small version, then they never toggled back to the 1:1 scale.</span></span> <span data-ttu-id="0bcb1-145">因此，我們決定實際報廢1:1 版，並避免需要額外的工作來調整 UI 和應用程式的其他層面。</span><span class="sxs-lookup"><span data-stu-id="0bcb1-145">So we decided to actually scrap the 1:1 version and avoid the extra work required to adapt UI and other aspects of the app.</span></span>

<span data-ttu-id="0bcb1-146">![使用1:1 調整規模 ](images/designing-holograms/1-1-scale.png)
 *欄位與 1:1* 級別的視圖模式</span><span class="sxs-lookup"><span data-stu-id="0bcb1-146">![Field of view with 1:1 scale](images/designing-holograms/1-1-scale.png)
*Field of view with 1:1 scale*</span></span>

<span data-ttu-id="0bcb1-147">![使用1:10 調整規模 ](images/designing-holograms/1-10-scale.png)
 *欄位與 1:10* 級別的視圖模式</span><span class="sxs-lookup"><span data-stu-id="0bcb1-147">![Field of view with 1:10 scale](images/designing-holograms/1-10-scale.png)
*Field of view with 1:10 scale*</span></span>

## <a name="using-mixed-reality-capture"></a><span data-ttu-id="0bcb1-148">使用混合實境擷取</span><span class="sxs-lookup"><span data-stu-id="0bcb1-148">Using Mixed Reality Capture</span></span>

<span data-ttu-id="0bcb1-149">此應用程式的其中一項最特性功能是使用混合實境擷取來教授和展示混合的現實設計概念。</span><span class="sxs-lookup"><span data-stu-id="0bcb1-149">One of the most characteristic features of this app is the use of Mixed Reality Capture to teach and demonstrate mixed reality design concepts.</span></span>

<span data-ttu-id="0bcb1-150">Microsoft 在三藩市有混合實境擷取 studio。</span><span class="sxs-lookup"><span data-stu-id="0bcb1-150">Microsoft has a Mixed Reality Capture studio in San Francisco.</span></span> <span data-ttu-id="0bcb1-151">Microsoft 也會將這項技術授權給其他工作室，包括華盛頓特區的圖片、Metastage 在洛杉磯、倫敦的 Dimension 工作室、首爾的 SK 電信，以及柏林的 Volucap。</span><span class="sxs-lookup"><span data-stu-id="0bcb1-151">Microsoft also licenses this technology to other studios, which include Avatar Dimension in Washington D.C., Metastage in Los Angeles, Dimension Studios in London, SK Telecom in Seoul, and Volucap in Berlin.</span></span> <span data-ttu-id="0bcb1-152">您可以在 [這裡找到混合實境擷取工作室](https://www.microsoft.com/mixed-reality/capture-studios)的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="0bcb1-152">You can find more information on our [Mixed Reality Capture Studios here](https://www.microsoft.com/mixed-reality/capture-studios).</span></span>

<br>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Raw-capture-footage-for-the-Designing-Holograms-app/player]
<span data-ttu-id="0bcb1-153">*Daniel Escudero 的原始素材，從三藩市的混合實境擷取 Studio 中的106攝影機之一。*</span><span class="sxs-lookup"><span data-stu-id="0bcb1-153">*Raw footage of Daniel Escudero from one of the 106 cameras in the Mixed Reality Capture Studio in San Francisco.*</span></span>

<span data-ttu-id="0bcb1-154">此捕捉程式會產生 keyframed 網格、法線和材質，以供進一步的進入生產階段，或是準備好播放作為 h.264 壓縮的檔案。</span><span class="sxs-lookup"><span data-stu-id="0bcb1-154">The capture process generates a keyframed mesh, normals, and texture, which can be delivered as OBJ/PNG files for further post-production, or ready for playback as an H.264 compressed MP4 file.</span></span> <span data-ttu-id="0bcb1-155">這些檔案可以匯入 Unity、Unreal、Native 和 WebXR 專案中。</span><span class="sxs-lookup"><span data-stu-id="0bcb1-155">These files can be imported into Unity, Unreal, Native, and WebXR projects.</span></span> <span data-ttu-id="0bcb1-156">檔案可以在 Windows、iOS、Mac、Android、魔術 Leap 和 Playstation VR 上執行。</span><span class="sxs-lookup"><span data-stu-id="0bcb1-156">Files can run on Windows, iOS, Mac, Android, Magic Leap, and Playstation VR.</span></span>

<br>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Mixed-Reality-Capture-footage-for-the-Designing-Holograms-app/player]
<span data-ttu-id="0bcb1-157">*提供用來分析包含音訊和內嵌網格影片之 mp4 的捕獲播放機。*</span><span class="sxs-lookup"><span data-stu-id="0bcb1-157">*The Capture Player provided to analyze mp4s that contain video with audio and embedded meshes.*</span></span>

## <a name="manipulating-captures-and-virtual-objects"></a><span data-ttu-id="0bcb1-158">操作捕獲和虛擬物件</span><span class="sxs-lookup"><span data-stu-id="0bcb1-158">Manipulating captures and virtual objects</span></span>

<span data-ttu-id="0bcb1-159">混合的事實捕獲會產生使用者或動物的虛擬標記法，但有時您可能需要這些字元與其他虛擬物件互動。</span><span class="sxs-lookup"><span data-stu-id="0bcb1-159">Mixed Reality Captures produce virtual representations of people or animals, but at times you may need those characters to interact with other virtual objects.</span></span> <span data-ttu-id="0bcb1-160">下列兩個範例示範我們操作幕後以達成此效果的不同方式。</span><span class="sxs-lookup"><span data-stu-id="0bcb1-160">The following two examples show different ways we manipulated the scenes to achieve this effect.</span></span>

### <a name="head-gaze-adjustment"></a><span data-ttu-id="0bcb1-161">前端注視調整</span><span class="sxs-lookup"><span data-stu-id="0bcb1-161">Head Gaze Adjustment</span></span>

<span data-ttu-id="0bcb1-162">Headgaze 調整可讓您在執行時間移動已捕捉的人員頭部，這表示您可能會有使用者的捕獲臉部。</span><span class="sxs-lookup"><span data-stu-id="0bcb1-162">Headgaze adjustment lets you move a captured person’s head at runtime, meaning you could have a capture face towards a user.</span></span> <span data-ttu-id="0bcb1-163">在我們的案例中，我們使用它來顯示您感興趣的視圖欄位和欄位。</span><span class="sxs-lookup"><span data-stu-id="0bcb1-163">In our case, we used it to show the field of view and field of interest.</span></span> <span data-ttu-id="0bcb1-164">您在下面所見的是移動 gameobject，作為要查看的標題。</span><span class="sxs-lookup"><span data-stu-id="0bcb1-164">What you see below is a moving gameobject acting as a target for the head gaze to look at.</span></span> <span data-ttu-id="0bcb1-165">當我們將目標從側邊移至一邊時，捕捉的開頭會如下所示。</span><span class="sxs-lookup"><span data-stu-id="0bcb1-165">As we move the target from side to side, the head of the capture follows.</span></span>

<span data-ttu-id="0bcb1-166">我們使用這個技巧來確定閒置的捕獲一律會面對放在娃娃房子不同部分的全像投影。</span><span class="sxs-lookup"><span data-stu-id="0bcb1-166">We used this trick to make sure that the idle capture would always face towards holograms placed in different parts of the doll house.</span></span> 

![在 Unity 中的目標 gameobject 之後，于執行時間移動了 Capture 的標頭](images/designing-holograms/head-adjustment.gif)

<span data-ttu-id="0bcb1-168">*在 Unity 中的目標 gameobject 之後，會在執行時間移動 Capture 的開端。*</span><span class="sxs-lookup"><span data-stu-id="0bcb1-168">*The Capture’s head being moved at runtime following a target gameobject in Unity.*</span></span>

### <a name="syncing-animated-objects"></a><span data-ttu-id="0bcb1-169">同步處理動畫物件</span><span class="sxs-lookup"><span data-stu-id="0bcb1-169">Syncing Animated Objects</span></span>

<span data-ttu-id="0bcb1-170">第二個是建立物件的動畫，以與捕捉的移動進行同步處理。</span><span class="sxs-lookup"><span data-stu-id="0bcb1-170">The second one, was animating objects to sync with a capture’s movement.</span></span> <span data-ttu-id="0bcb1-171">在應用程式的不同部分中，我們會每隔五個畫面匯入特定捕獲的連續 Obj。</span><span class="sxs-lookup"><span data-stu-id="0bcb1-171">In different parts of the app, we imported sequential OBJs of a specific capture every five frames.</span></span> <span data-ttu-id="0bcb1-172">然後，Obj 會在場景中以動畫顯示，以確保它們符合捕捉的相對應框架。</span><span class="sxs-lookup"><span data-stu-id="0bcb1-172">The OBJs were then animated in the scene to make sure they would match the corresponding frame of the capture.</span></span> <span data-ttu-id="0bcb1-173">它是動畫處理和 keyframing 的繁瑣程式，但結果很棒。</span><span class="sxs-lookup"><span data-stu-id="0bcb1-173">It’s a tedious process of animating and keyframing, but the result is great.</span></span> <span data-ttu-id="0bcb1-174">您現在可以看到與非捕捉物件互動的混合實境擷取。</span><span class="sxs-lookup"><span data-stu-id="0bcb1-174">You can now see a Mixed Reality Capture interacting with non-captured objects.</span></span>

![混合實境擷取和 UI 面板之間的同步動畫](images/designing-holograms/synced-objects.gif)

<span data-ttu-id="0bcb1-176">*混合實境擷取和 UI 面板之間的同步動畫*</span><span class="sxs-lookup"><span data-stu-id="0bcb1-176">*Synced animation between a Mixed Reality Capture and UI panel*</span></span>

### <a name="ui-creative-process"></a><span data-ttu-id="0bcb1-177">UI 創意流程</span><span class="sxs-lookup"><span data-stu-id="0bcb1-177">UI creative process</span></span>

<span data-ttu-id="0bcb1-178">當我們開始進行 UI 設計時，我們想要示範一些像是「全息」所提供的魔術和可能性。</span><span class="sxs-lookup"><span data-stu-id="0bcb1-178">When we started the UI design, we wanted to show some of the magic and possibility that holograms have to offer.</span></span> <span data-ttu-id="0bcb1-179">單純地顯示靜態2D 視窗和文字方塊，並不會直接在3D 世界中。</span><span class="sxs-lookup"><span data-stu-id="0bcb1-179">Simply showing static 2D windows and text boxes doesn’t feel right in the 3D world.</span></span> <span data-ttu-id="0bcb1-180">手中的許多可能性都不會顯示，因此從一開始，我們決定要從該位置移出，並充分利用全像立體空間。</span><span class="sxs-lookup"><span data-stu-id="0bcb1-180">Many of the possibilities at hand just don't show up, so right from the beginning we decided to move away from that and make full use of holographic 3D space.</span></span>

<span data-ttu-id="0bcb1-181">一開始，我們開始將一些粗細新增至面板、圖示和文字資訊。</span><span class="sxs-lookup"><span data-stu-id="0bcb1-181">At first, we started with adding some thickness to the panels, icons, and text information.</span></span> <span data-ttu-id="0bcb1-182">但是，以使用者的身份來看，我看到的是一個文字方塊。</span><span class="sxs-lookup"><span data-stu-id="0bcb1-182">Still, as a user, what I see is a text box.</span></span> <span data-ttu-id="0bcb1-183">具有影像的文字方塊，但不存在。</span><span class="sxs-lookup"><span data-stu-id="0bcb1-183">Text boxes with images, but we aren't there.</span></span> <span data-ttu-id="0bcb1-184">我們進一步利用混合現實工具組 (MRTK) 著色器。</span><span class="sxs-lookup"><span data-stu-id="0bcb1-184">We went further by making use of the Mixed Reality Toolkit (MRTK) shaders.</span></span> <span data-ttu-id="0bcb1-185">MRTK 著色器變成一項強大的工具，並使用其樣板功能將負面深度新增至面板。</span><span class="sxs-lookup"><span data-stu-id="0bcb1-185">The MRTK shaders became a powerful tool, and we made use of its stencil features to add negative depth to the panels.</span></span> <span data-ttu-id="0bcb1-186">這表示，圖示現在會出現在透明面板後方，而不是在文字方塊前面加上專案。</span><span class="sxs-lookup"><span data-stu-id="0bcb1-186">That means instead of adding elements in front of a text box, the icons now appear behind a transparent panel.</span></span> <span data-ttu-id="0bcb1-187">我現在看到的就是使用者，這就是我在現實世界中無法再複寫的內容，而且這就是您開始進行全像攝影的地方。</span><span class="sxs-lookup"><span data-stu-id="0bcb1-187">What I see now as a user is something that I just can’t replicate anymore in the real world, and this is where holographic magic started to happen.</span></span> <span data-ttu-id="0bcb1-188">此外，我還不太喜歡閱讀的使用者，而是在實體世界中做過許多事。</span><span class="sxs-lookup"><span data-stu-id="0bcb1-188">Also as a user I don’t really like to read, I do a lot already in the physical world.</span></span>

<span data-ttu-id="0bcb1-189">顯然圖示的運作方式比簡單的文字更好，為了提供更強大的指引，我接著開始建立一組動畫物件和虛擬人偶，每個物件都告訴您有關在個別案例中所做的事情，以及其使用方式的一小部分。</span><span class="sxs-lookup"><span data-stu-id="0bcb1-189">Obviously icons work a lot better than simple text does, to provide an even more powerful guidance, I then started creating a set of animated objects and avatars, each of them telling a tiny story about what is being done in the respective scenario and how it’s being used.</span></span>

![互動式全息式功能表系統的動畫 GIF](images/designing-holograms/creative-process.gif)

## <a name="core-concepts"></a><span data-ttu-id="0bcb1-191">核心概念</span><span class="sxs-lookup"><span data-stu-id="0bcb1-191">Core concepts</span></span>

<span data-ttu-id="0bcb1-192">**全像攝影框架**</span><span class="sxs-lookup"><span data-stu-id="0bcb1-192">**Holographic frame**</span></span>

![使用者的動畫 GIF，以醒目提示的全像全像 dollhouse 來搜尋](images/designing-holograms/FOVandFOI.gif)

<span data-ttu-id="0bcb1-194">**座標系統**</span><span class="sxs-lookup"><span data-stu-id="0bcb1-194">**Coordinate systems**</span></span>

![以反白顯示座標系統的方式 dollhouse 使用者的動畫 GIF](images/designing-holograms/CoordinateSystems.gif)

<span data-ttu-id="0bcb1-196">**眼球追蹤**</span><span class="sxs-lookup"><span data-stu-id="0bcb1-196">**Eye tracking**</span></span>

![使用者的動畫 GIF，查看已醒目提示眼睛光線的靜止全息影像](images/designing-holograms/EyeTracking.gif)

<span data-ttu-id="0bcb1-198">**房間掃描視覺效果和空間對應**</span><span class="sxs-lookup"><span data-stu-id="0bcb1-198">**Room scan visualization and spatial mapping**</span></span>

![正在對應之 dollhouse 內所有表面的動畫 GIF](images/designing-holograms/SpatialMapping.gif)

<span data-ttu-id="0bcb1-200">**場景理解**</span><span class="sxs-lookup"><span data-stu-id="0bcb1-200">**Scene understanding**</span></span>

![所辨識 dollhouse 中物件的動畫 GIF](images/designing-holograms/SceneUnderstanding.gif)

<span data-ttu-id="0bcb1-202">**使用手光線的點和認可**</span><span class="sxs-lookup"><span data-stu-id="0bcb1-202">**Point and commit with hand rays**</span></span>

![醒目提示手動光線之使用者的動畫 GIF](images/designing-holograms/HandRays.gif)

## <a name="try-it-out-moments"></a><span data-ttu-id="0bcb1-204">「立即試用」分鐘</span><span class="sxs-lookup"><span data-stu-id="0bcb1-204">"Try it out" moments</span></span>

<span data-ttu-id="0bcb1-205">設計全像混合的現實概念，但也可讓您在您的房間內試用。</span><span class="sxs-lookup"><span data-stu-id="0bcb1-205">Designing Holograms teaches mixed reality concepts, but it also allows you to try them in your room.</span></span> <span data-ttu-id="0bcb1-206">在這些說明中，我們會暫停並讓您離開娃娃房子並進入互動式時刻。</span><span class="sxs-lookup"><span data-stu-id="0bcb1-206">After some of those explanations, we pause and take you out of the doll house and into an interactive moment.</span></span> <span data-ttu-id="0bcb1-207">以下是這些互動式時刻的一些範例：</span><span class="sxs-lookup"><span data-stu-id="0bcb1-207">Here are some examples of those interactive moments:</span></span>

![手形追蹤框架的動畫 GIF，顯示當偵測到手時以及何時進入 view 欄位時](images/designing-holograms/try-out-1.gif)

<span data-ttu-id="0bcb1-209">*當偵測到手時，以及當他們進入 view 欄位時，所顯示的手追蹤框架。*</span><span class="sxs-lookup"><span data-stu-id="0bcb1-209">*The hand tracking frame showing when hands are detected and when they enter the field of view.*</span></span>

![與衝突 crystals 進行互動的動畫 GIF](images/designing-holograms/try-out-2.gif)

<span data-ttu-id="0bcb1-211">*透過互動方式與衝突 crystals 互動*</span><span class="sxs-lookup"><span data-stu-id="0bcb1-211">*Interacting with colliding crystals through far interaction*</span></span>

![探索近乎互動 affordances 的動畫 GIF](images/designing-holograms/try-out-3.gif)

<span data-ttu-id="0bcb1-213">*探索近距離互動 affordances*</span><span class="sxs-lookup"><span data-stu-id="0bcb1-213">*Exploring near interaction affordances*</span></span>

## <a name="about-the-team"></a><span data-ttu-id="0bcb1-214">關於小組</span><span class="sxs-lookup"><span data-stu-id="0bcb1-214">About the team</span></span>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Daniel Escudero" width="60" height="60" src="images/designing-holograms/daniel-escudero.jpeg"></td>
<td style="border-style: none"><span data-ttu-id="0bcb1-215"><b>Daniel Escudero</b></span><span class="sxs-lookup"><span data-stu-id="0bcb1-215"><b>Daniel Escudero</b></span></span><br><span data-ttu-id="0bcb1-216"><i>首席技術設計人員</i></span><span class="sxs-lookup"><span data-stu-id="0bcb1-216"><i>Lead Technical Designer</i></span></span><br><span data-ttu-id="0bcb1-217">Dan 是設計全像市的創意總監，目前也是在三藩市的 Microsoft Mixed Reality 學術設計組長的設計，而且之前是 Microsoft 在倫敦的混合現實工作室之一。</span><span class="sxs-lookup"><span data-stu-id="0bcb1-217">Dan is the Creative Director on Designing Holograms and currently works as Design Lead for the Microsoft’s Mixed Reality Academy in San Francisco, and was previously a Designer in one of Microsoft’s Mixed Reality Studios in London.</span></span></td>
</tr>
</table>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Martin Wettig" width="60" height="60" src="images/designing-holograms/martin-wettig.jpeg"></td>
<td style="border-style: none"><span data-ttu-id="0bcb1-218"><b>聖馬丁 Wettig</b></span><span class="sxs-lookup"><span data-stu-id="0bcb1-218"><b>Martin Wettig</b></span></span><br><span data-ttu-id="0bcb1-219"><i>資深3D 演出者</i></span><span class="sxs-lookup"><span data-stu-id="0bcb1-219"><i>Senior 3D Artist</i></span></span><br><span data-ttu-id="0bcb1-220">聖馬丁在設計全像全像是 Microsoft 的混合現實工作室的其中一位資深3D 演出者的時候，會導致3D 藝術和 UI 設計。</span><span class="sxs-lookup"><span data-stu-id="0bcb1-220">Martin leads 3D Art and UI Design on Designing Holograms and was previously a Senior 3D Artist at one of Microsoft’s Mixed Reality Studios in Berlin.</span></span></td>
</tr>
</table>

<span data-ttu-id="0bcb1-221">這項寶貴的感謝，讓您瞭解混合的現實設計小組，以分享更多的知識，以及 [物件理論](https://objecttheory.com/) 上令人驚奇的人，在專案的每個步驟中都是重要的成員。</span><span class="sxs-lookup"><span data-stu-id="0bcb1-221">A huge thank you to the Mixed Reality Design Team for sharing so much knowledge, and to the amazing folks at [Object Theory](https://objecttheory.com/) for being essential teammates through every step of the project.</span></span> <span data-ttu-id="0bcb1-222">感謝您的熱情，讓您在設計上有出色的關注。</span><span class="sxs-lookup"><span data-stu-id="0bcb1-222">Thank you all for you amazing talent, for your passion and exceptional eye for design.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="0bcb1-223">下載設計全像影像應用程式</span><span class="sxs-lookup"><span data-stu-id="0bcb1-223">Download the Designing Holograms app</span></span>](https://www.microsoft.com/p/designing-holograms/9nxwnjklrzwd)