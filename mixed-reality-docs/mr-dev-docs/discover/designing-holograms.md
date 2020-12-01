---
title: 設計全像影像
description: 透過 Microsoft 全新的設計全像影像應用程式，瞭解混合的現實。
author: hferrone
ms.author: daescu
ms.date: 11/24/2020
ms.topic: article
keywords: MRTK，混合的現實工具組，全像投影，設計全像投影、學習、範例應用程式、混合現實耳機、虛擬實境耳機、何謂虛擬實境
ms.openlocfilehash: 243b6f28da7b074b3ff6d48794d525ac08281fa7
ms.sourcegitcommit: 09522ab15a9008ca4d022f9e37fcc98f6eaf6093
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/30/2020
ms.locfileid: "96355338"
---
# <a name="the-making-of-designing-holograms"></a><span data-ttu-id="2428f-104">設計全息製作</span><span class="sxs-lookup"><span data-stu-id="2428f-104">The making of Designing Holograms</span></span>

> [!NOTE]
> <span data-ttu-id="2428f-105">請在此頁面上，允許小型載入視窗，以將所有酷炫的 Gif 和 embedded 影片全部考慮。</span><span class="sxs-lookup"><span data-stu-id="2428f-105">Please allow for a small loading window to account for all the cool GIFs and embedded videos on this page.</span></span>

<span data-ttu-id="2428f-106">學習如何設計混合的現實可能很困難，特別是在視覺效果的情況下，這不一定會正確轉譯成2D 設計流程。</span><span class="sxs-lookup"><span data-stu-id="2428f-106">Learning how to design for mixed reality can be hard, especially with how visual the medium is, which doesn't always translate well to 2D design processes.</span></span> <span data-ttu-id="2428f-107">在 Microsoft，我們已建立可供您下載 HoloLens 2 的免費應用程式，可協助您透過第一手來瞭解混合現實 UX 設計的基本概念。</span><span class="sxs-lookup"><span data-stu-id="2428f-107">Here at Microsoft, we've created a free app you can download for the HoloLens 2, which helps you learn the fundamentals of mixed reality UX Design by experiencing it firsthand.</span></span> <span data-ttu-id="2428f-108">設計全像影像應用程式的獨特方法是探討混合現實行為、秘訣和建議，以協助您建立自己的吸引人和出色的 HoloLens 應用程式。</span><span class="sxs-lookup"><span data-stu-id="2428f-108">The unique approach of the Designing Holograms app dives into mixed reality behaviors, tips, and recommendations to help you create engaging and amazing HoloLens apps of your own.</span></span> <span data-ttu-id="2428f-109">從 Microsoft Store 免費下載應用程式，並從 Microsoft 的混合現實設計小組學習！</span><span class="sxs-lookup"><span data-stu-id="2428f-109">Download the app for free from the Microsoft Store and learn from Microsoft’s Mixed Reality Design Team!</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="2428f-110">下載設計全像影像應用程式</span><span class="sxs-lookup"><span data-stu-id="2428f-110">Download the Designing Holograms app</span></span>](https://www.microsoft.com/p/designing-holograms/9nxwnjklrzwd)

<br>

![設計全息圖的示範房間中的標頭追蹤場景動畫 GIF](images/designing-holograms/demo-room.gif)

<span data-ttu-id="2428f-112">*設計全息圖的示範房間 (也稱為娃娃房子)*</span><span class="sxs-lookup"><span data-stu-id="2428f-112">*Designing Hologram’s demo room (also known as the doll house)*</span></span>

## <a name="designing-for-mixed-reality"></a><span data-ttu-id="2428f-113">混合現實的設計</span><span class="sxs-lookup"><span data-stu-id="2428f-113">Designing for mixed reality</span></span>

<span data-ttu-id="2428f-114">我和許多人一樣，都是用來設計行動應用程式。</span><span class="sxs-lookup"><span data-stu-id="2428f-114">Like many of you, I used to design mobile apps.</span></span> <span data-ttu-id="2428f-115">從2D 設計世界開始，一直到目前為止都在世界各地的空間運算，一直都是很大的轉變。</span><span class="sxs-lookup"><span data-stu-id="2428f-115">Coming from a 2D design world, jumping into full on spatial computing, where everything is now in the world, was a significant shift.</span></span> <span data-ttu-id="2428f-116">在混合的現實情況下，應用程式不會再局限于2D 螢幕;事實上，它們幾乎是免費的，放在真實世界中，並與實際物件互動。</span><span class="sxs-lookup"><span data-stu-id="2428f-116">In mixed reality, apps aren't confined to a 2D screen anymore; in fact, they're almost free, placed in the real world and interacting with real objects.</span></span>

<span data-ttu-id="2428f-117">對我來說，將3D 體驗連接到傳統2D 設計程式是混合現實開發最具挑戰性的層面。</span><span class="sxs-lookup"><span data-stu-id="2428f-117">To me, connecting 3D experiences to conventional 2D design processes is the most challenging aspect of mixed reality development.</span></span> <span data-ttu-id="2428f-118">在與客戶對話的情況下，我會聽到像是「我知道要包含哪些功能，以及如何讓它們正常運作。</span><span class="sxs-lookup"><span data-stu-id="2428f-118">In conversations with customers, I would hear things like “I know what features to include and how to get them up and running.</span></span> <span data-ttu-id="2428f-119">它是程式碼，我可以遵循檔和教學課程，但是使用者體驗？</span><span class="sxs-lookup"><span data-stu-id="2428f-119">It’s code, I can follow the docs and tutorials, but the user experience?</span></span> <span data-ttu-id="2428f-120">許多功能、不同的輸入選項、不同的案例和實體環境都很龐大」。</span><span class="sxs-lookup"><span data-stu-id="2428f-120">So many features, different input options, different scenarios and physical environments, it’s overwhelming".</span></span>

<span data-ttu-id="2428f-121">![來自三藩市的 HoloLens 2 設計研討會中的影像 ](images/designing-holograms/workshop.jpeg)
 *，從三藩市的 HoloLens 2 設計研討會*</span><span class="sxs-lookup"><span data-stu-id="2428f-121">![Image from the HoloLens 2 Design Workshop in San Francisco](images/designing-holograms/workshop.jpeg)
*Image from the HoloLens 2 Design Workshop in San Francisco*</span></span>

## <a name="an-opportunity-to-teach"></a><span data-ttu-id="2428f-122">教授的機會</span><span class="sxs-lookup"><span data-stu-id="2428f-122">An opportunity to teach</span></span>

<span data-ttu-id="2428f-123">它一開始並不明顯，但有一個絕佳的機會，可以使用 mixed reality 作為媒體來教授。</span><span class="sxs-lookup"><span data-stu-id="2428f-123">It wasn’t obvious at first, but an excellent opportunity was presented to use mixed reality as a Medium to teach it.</span></span>

<span data-ttu-id="2428f-124">設計全像影像是一種視覺體驗，可解釋混合的現實設計概念和建議。</span><span class="sxs-lookup"><span data-stu-id="2428f-124">Designing Holograms is a visual experience that explains mixed reality design concepts and recommendations.</span></span> <span data-ttu-id="2428f-125">這只是您和一個示範混合現實設計概念的虛擬老師。</span><span class="sxs-lookup"><span data-stu-id="2428f-125">It’s just you and a virtual teacher demonstrating mixed reality design concepts.</span></span> <span data-ttu-id="2428f-126">所有專案都是從第三個人的觀點來看，在您自己的空間中有很穩固的體驗。</span><span class="sxs-lookup"><span data-stu-id="2428f-126">Everything is from a third person perspective with the experience firmly in your own space.</span></span>

<br>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Designing-Holograms-app-trailer/player]

<span data-ttu-id="2428f-127">*設計全像投影片影片*</span><span class="sxs-lookup"><span data-stu-id="2428f-127">*Designing Holograms trailer video*</span></span>

## <a name="exploring-the-doll-house"></a><span data-ttu-id="2428f-128">探索娃娃房子</span><span class="sxs-lookup"><span data-stu-id="2428f-128">Exploring the doll house</span></span>

<span data-ttu-id="2428f-129">娃娃房子是我們在整個應用程式中使用的虛擬環境，這是一個 80 x 60 x 40-cm 微型空間，其中包含大部分房間共通的基本元素，例如牆、燈、傢俱、表格和電視。</span><span class="sxs-lookup"><span data-stu-id="2428f-129">The doll house is the virtual environment we use throughout the app, an 80 x 60 x 40-cm miniature room that contains the basic elements that most rooms have in common, like walls, lamps, furniture, a table, and a TV.</span></span> <span data-ttu-id="2428f-130">娃娃房子是應用程式體驗的主要 protagonist，因此我們需要確定它在任何環境中都能正常運作。</span><span class="sxs-lookup"><span data-stu-id="2428f-130">The doll house is the main protagonist of the app experience, so we needed to make sure that it would work great in any environment.</span></span> <span data-ttu-id="2428f-131">把它想像成一個小型的示範空間，用來視覺化各種混合現實概念。</span><span class="sxs-lookup"><span data-stu-id="2428f-131">Think of it as a small demo room for visualizing all sorts of mixed reality concepts.</span></span>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Dollhouse-adjustment-behavior-in-the-Designing-Holograms-app/player]
<span data-ttu-id="2428f-132">*Dollhouse 調整行為的影片*</span><span class="sxs-lookup"><span data-stu-id="2428f-132">*Video of the Dollhouse adjustment behavior*</span></span>

### <a name="11-vs-110-prototypes"></a><span data-ttu-id="2428f-133">1:1 與1:10 原型</span><span class="sxs-lookup"><span data-stu-id="2428f-133">1:1 vs 1:10 prototypes</span></span>

<span data-ttu-id="2428f-134">我們最初的假設是，1:1 示範會很令人驚奇，看起來像是真實的老師。</span><span class="sxs-lookup"><span data-stu-id="2428f-134">Our initial assumption was that 1:1 demonstrations would be amazing, almost like looking at a real life teacher.</span></span> <span data-ttu-id="2428f-135">使用者會看到老師在真實規模中看到的所有內容。</span><span class="sxs-lookup"><span data-stu-id="2428f-135">The user would see everything that the teacher sees at a real life scale.</span></span> <span data-ttu-id="2428f-136">不過，我們會立即發現有幾個問題：</span><span class="sxs-lookup"><span data-stu-id="2428f-136">However, we immediately realized that there would be a few problems:</span></span>

- <span data-ttu-id="2428f-137">大部分的開發人員會在辦公室或房間以外的房間內執行其應用程式，因此無法容納。</span><span class="sxs-lookup"><span data-stu-id="2428f-137">Most developers will run their apps in offices, or rooms smaller than the demo room, so it wouldn’t fit.</span></span>
- <span data-ttu-id="2428f-138">顯示是加總的，這表示整個虛擬環境會在使用者的房間上重迭。</span><span class="sxs-lookup"><span data-stu-id="2428f-138">Displays are additive, meaning the entire virtual environment will be overlaid over a user’s room.</span></span> <span data-ttu-id="2428f-139">這可能會造成兩個數據表混淆，或許是雙 couches 和沒有對齊的牆。</span><span class="sxs-lookup"><span data-stu-id="2428f-139">That can get confusing with two tables, maybe double couches and walls that don’t align.</span></span>
- <span data-ttu-id="2428f-140">而最糟的是，所有虛擬環境都受到視野的高度限制。</span><span class="sxs-lookup"><span data-stu-id="2428f-140">And worst of all a virtual environment heavily constrained by a field of view.</span></span>

<span data-ttu-id="2428f-141">當我們嘗試迷你的1:10 規模時，結果就是一個很棒的鳥，也就是實際的房間，您可以從任何角度查看所有的東西</span><span class="sxs-lookup"><span data-stu-id="2428f-141">When we tried out a mini 1:10 scale, the result was a fantastic birds-eye view of a realistic room where you could see everything that was going on from any angle and all at the same time.</span></span> <span data-ttu-id="2428f-142">最令人驚訝的是，大部分的測試人員發現它更能看到較小的版本，而不是切換回1:1 規模。</span><span class="sxs-lookup"><span data-stu-id="2428f-142">What was most surprising is that most testers found it so much more immersive to see a small version, then they never toggled back to the 1:1 scale.</span></span> <span data-ttu-id="2428f-143">因此，我們決定實際報廢1:1 版，並避免需要額外的工作來調整 UI 和應用程式的其他層面。</span><span class="sxs-lookup"><span data-stu-id="2428f-143">So we decided to actually scrap the 1:1 version and avoid the extra work required to adapt UI and other aspects of the app.</span></span>

<span data-ttu-id="2428f-144">![使用1:1 調整規模 ](images/designing-holograms/1-1-scale.png)
 *欄位與 1:1* 級別的視圖模式</span><span class="sxs-lookup"><span data-stu-id="2428f-144">![Field of view with 1:1 scale](images/designing-holograms/1-1-scale.png)
*Field of view with 1:1 scale*</span></span>

<span data-ttu-id="2428f-145">![使用1:10 調整規模 ](images/designing-holograms/1-10-scale.png)
 *欄位與 1:10* 級別的視圖模式</span><span class="sxs-lookup"><span data-stu-id="2428f-145">![Field of view with 1:10 scale](images/designing-holograms/1-10-scale.png)
*Field of view with 1:10 scale*</span></span>

## <a name="using-mixed-reality-capture"></a><span data-ttu-id="2428f-146">使用混合實境擷取</span><span class="sxs-lookup"><span data-stu-id="2428f-146">Using Mixed Reality Capture</span></span>

<span data-ttu-id="2428f-147">此應用程式的其中一項最特性功能是使用混合實境擷取來教授和展示混合的現實設計概念。</span><span class="sxs-lookup"><span data-stu-id="2428f-147">One of the most characteristic features of this app is the use of Mixed Reality Capture to teach and demonstrate mixed reality design concepts.</span></span>

<span data-ttu-id="2428f-148">Microsoft 在三藩市有混合實境擷取 studio。</span><span class="sxs-lookup"><span data-stu-id="2428f-148">Microsoft has a Mixed Reality Capture studio in San Francisco.</span></span> <span data-ttu-id="2428f-149">Microsoft 也會將這項技術授權給其他工作室，包括華盛頓特區的圖片、Metastage 在洛杉磯、倫敦的 Dimension 工作室、首爾的 SK 電信，以及柏林的 Volucap。</span><span class="sxs-lookup"><span data-stu-id="2428f-149">Microsoft also licenses this technology to other studios, which include Avatar Dimension in Washington D.C., Metastage in Los Angeles, Dimension Studios in London, SK Telecom in Seoul, and Volucap in Berlin.</span></span> <span data-ttu-id="2428f-150">您可以在 [這裡找到混合實境擷取工作室](https://www.microsoft.com/mixed-reality/capture-studios)的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="2428f-150">You can find more information on our [Mixed Reality Capture Studios here](https://www.microsoft.com/mixed-reality/capture-studios).</span></span>

<br>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Raw-capture-footage-for-the-Designing-Holograms-app/player]
<span data-ttu-id="2428f-151">*Daniel Escudero 的原始素材，從三藩市的混合實境擷取 Studio 中的106攝影機之一。*</span><span class="sxs-lookup"><span data-stu-id="2428f-151">*Raw footage of Daniel Escudero from one of the 106 cameras in the Mixed Reality Capture Studio in San Francisco.*</span></span>

<span data-ttu-id="2428f-152">此捕捉程式會產生 keyframed 網格、法線和材質，以供進一步的進入生產階段，或是準備好播放作為 h.264 壓縮的檔案。</span><span class="sxs-lookup"><span data-stu-id="2428f-152">The capture process generates a keyframed mesh, normals, and texture, which can be delivered as OBJ/PNG files for further post-production, or ready for playback as an H.264 compressed MP4 file.</span></span> <span data-ttu-id="2428f-153">這些檔案可以匯入 Unity、Unreal、native 和 WebXR，並在 Windows、iOS、Mac、Android、魔術 Leap 和 Playstation VR 上執行。</span><span class="sxs-lookup"><span data-stu-id="2428f-153">These files can be imported into Unity, Unreal, native, and WebXR and run on Windows, iOS, Mac, Android, Magic Leap, and Playstation VR.</span></span>

<br>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Mixed-Reality-Capture-footage-for-the-Designing-Holograms-app/player]
<span data-ttu-id="2428f-154">*提供用來分析包含音訊和內嵌網格影片之 mp4 的捕獲播放機。*</span><span class="sxs-lookup"><span data-stu-id="2428f-154">*The Capture Player provided to analyze mp4s that contain video with audio and embedded meshes.*</span></span>

## <a name="manipulating-captures-and-virtual-objects"></a><span data-ttu-id="2428f-155">操作捕獲和虛擬物件</span><span class="sxs-lookup"><span data-stu-id="2428f-155">Manipulating captures and virtual objects</span></span>

<span data-ttu-id="2428f-156">混合的事實捕獲會產生使用者或動物的虛擬標記法，但有時您可能需要這些字元與其他虛擬物件互動。</span><span class="sxs-lookup"><span data-stu-id="2428f-156">Mixed Reality Captures produce virtual representations of people or animals, but at times you may need those characters to interact with other virtual objects.</span></span> <span data-ttu-id="2428f-157">下列兩個範例示範我們操作幕後以達成此效果的不同方式。</span><span class="sxs-lookup"><span data-stu-id="2428f-157">The following two examples show different ways we manipulated the scenes to achieve this effect.</span></span>

### <a name="head-gaze-adjustment"></a><span data-ttu-id="2428f-158">前端注視調整</span><span class="sxs-lookup"><span data-stu-id="2428f-158">Head Gaze Adjustment</span></span>

<span data-ttu-id="2428f-159">Headgaze 調整可讓您在執行時間移動已捕捉的人員頭部，這表示您可能會有使用者的捕獲臉部。</span><span class="sxs-lookup"><span data-stu-id="2428f-159">Headgaze adjustment lets you to move a captured person’s head at runtime, meaning you could have a capture face towards a user.</span></span> <span data-ttu-id="2428f-160">在我們的案例中，我們使用它來顯示您感興趣的視圖欄位和欄位。</span><span class="sxs-lookup"><span data-stu-id="2428f-160">In our case, we used it to show the field of view and field of interest.</span></span> <span data-ttu-id="2428f-161">您在下面所見的是移動 gameobject，作為要查看的標題。</span><span class="sxs-lookup"><span data-stu-id="2428f-161">What you see below is a moving gameobject acting as a target for the head gaze to look at.</span></span> <span data-ttu-id="2428f-162">當我們將目標從側邊移至一邊時，捕捉的開頭會如下所示。</span><span class="sxs-lookup"><span data-stu-id="2428f-162">As we move the target from side to side, the head of the capture follows.</span></span>

<span data-ttu-id="2428f-163">我們使用這個技巧來確定閒置的捕獲一律會面對放在娃娃房子不同部分的全像投影。</span><span class="sxs-lookup"><span data-stu-id="2428f-163">We used this trick to make sure that the idle capture would always face towards holograms placed in different parts of the doll house.</span></span> 

![在 Unity 中的目標 gameobject 之後，于執行時間移動了 Capture 的標頭](images/designing-holograms/head-adjustment.gif)

<span data-ttu-id="2428f-165">*在 Unity 中的目標 gameobject 之後，會在執行時間移動 Capture 的開端。*</span><span class="sxs-lookup"><span data-stu-id="2428f-165">*The Capture’s head being moved at runtime following a target gameobject in Unity.*</span></span>

### <a name="syncing-animated-objects"></a><span data-ttu-id="2428f-166">同步處理動畫物件</span><span class="sxs-lookup"><span data-stu-id="2428f-166">Syncing Animated Objects</span></span>

<span data-ttu-id="2428f-167">第二個是建立物件的動畫，以與捕捉的移動進行同步處理。</span><span class="sxs-lookup"><span data-stu-id="2428f-167">The second one, was animating objects to sync with a capture’s movement.</span></span> <span data-ttu-id="2428f-168">在應用程式的不同部分中，我們會每隔五個畫面匯入特定捕獲的連續 Obj。</span><span class="sxs-lookup"><span data-stu-id="2428f-168">In different parts of the app, we imported sequential OBJs of a specific capture every five frames.</span></span> <span data-ttu-id="2428f-169">然後，Obj 會在場景中以動畫顯示，以確保它們符合捕捉的相對應框架。</span><span class="sxs-lookup"><span data-stu-id="2428f-169">The OBJs were then animated in the scene to make sure they would match the corresponding frame of the capture.</span></span> <span data-ttu-id="2428f-170">它是動畫和 keyframing 的繁瑣程式，但結果很棒，您現在可以看到與非捕捉物件的混合實境擷取互動。</span><span class="sxs-lookup"><span data-stu-id="2428f-170">It’s a tedious process of animating and keyframing, but the result is great, you can now see a Mixed Reality Capture interacting with non-captured objects.</span></span>

![混合實境擷取和 UI 面板之間的同步動畫](images/designing-holograms/synced-objects.gif)

<span data-ttu-id="2428f-172">*混合實境擷取和 UI 面板之間的同步動畫*</span><span class="sxs-lookup"><span data-stu-id="2428f-172">*Synced animation between a Mixed Reality Capture and UI panel*</span></span>

### <a name="ui-creative-process"></a><span data-ttu-id="2428f-173">UI 創意流程</span><span class="sxs-lookup"><span data-stu-id="2428f-173">UI creative process</span></span>

<span data-ttu-id="2428f-174">當我們開始 ideating UI 設計時，除了傳輸資訊外，我們也想要展示一些魔術以及全息圖案提供的可能性。</span><span class="sxs-lookup"><span data-stu-id="2428f-174">When we started ideating the UI design, besides from transporting information we also wanted to show some of the magic and the possibilities that holograms have to offer.</span></span> <span data-ttu-id="2428f-175">只要顯示靜態2D 視窗和文字方塊並不會直接在3D 世界中，也不會顯示許多可能性，因此從一開始，我們決定要從該視窗中移除，並充分利用全像立體空間。</span><span class="sxs-lookup"><span data-stu-id="2428f-175">Simply showing static 2D windows and text boxes doesn’t feel right in the 3D world and doesn’t show many of the possibilities at hand, so right from the beginning we decided to move away from that and make full use of holographic 3D space.</span></span>

<span data-ttu-id="2428f-176">一開始，我們會先將一些粗細新增至面板和圖示，以及文字資訊。</span><span class="sxs-lookup"><span data-stu-id="2428f-176">At first, we started with adding some thickness to the panels and icons in addition to text information.</span></span> <span data-ttu-id="2428f-177">但是，以使用者的身份來看，我看到的是一個文字方塊。</span><span class="sxs-lookup"><span data-stu-id="2428f-177">Still, as a user, what I see is a text box.</span></span> <span data-ttu-id="2428f-178">具有影像的文字方塊，但我們不在此。</span><span class="sxs-lookup"><span data-stu-id="2428f-178">Text boxes with images, but we are not there.</span></span> <span data-ttu-id="2428f-179">我們進一步利用混合現實工具組 (MRTK) 著色器。</span><span class="sxs-lookup"><span data-stu-id="2428f-179">We went further by making use of the Mixed Reality Toolkit (MRTK) shaders.</span></span> <span data-ttu-id="2428f-180">MRTK 著色器變成一項強大的工具，而且我們已使用其樣板功能，有些可能會將其視為入口網站效果，以將負面深度新增至面板。</span><span class="sxs-lookup"><span data-stu-id="2428f-180">The MRTK shaders became a powerful tool, and we made use of its stencil features, some may know it as the portal effect, to add negative depth to the panels.</span></span> <span data-ttu-id="2428f-181">這表示，圖示現在會出現在透明面板後方，而不是在文字方塊前面加上專案。</span><span class="sxs-lookup"><span data-stu-id="2428f-181">That means instead of adding elements in front of a text box, the icons now appear behind a transparent panel.</span></span> <span data-ttu-id="2428f-182">我現在看到的就是使用者，這就是我在現實世界中無法再複寫的內容，而且這就是您開始進行全像攝影的地方。</span><span class="sxs-lookup"><span data-stu-id="2428f-182">What I see now as a user is something that I just can’t replicate anymore in the real world, and this is where holographic magic started to happen.</span></span> <span data-ttu-id="2428f-183">此外，我也不想要閱讀的使用者，就是在實體世界中這麼多。</span><span class="sxs-lookup"><span data-stu-id="2428f-183">Also as a user I don’t really like to read, I do that a lot already in the physical world.</span></span>

<span data-ttu-id="2428f-184">顯然圖示的運作方式比簡單的文字更好，因此為了提供更強大的指引，我接著開始建立一組動畫物件和虛擬人偶，每個物件都告訴您有關在個別案例中所做的事情，以及其使用方式的一小部分。</span><span class="sxs-lookup"><span data-stu-id="2428f-184">Obviously icons work a lot better than simple text does, so in order to provide an even more powerful guidance, I then started creating a set of animated objects and avatars, each of them telling a tiny story about what is being done in the respective scenario and how it’s being used.</span></span>

![互動式全息式功能表系統的動畫 GIF](images/designing-holograms/creative-process.gif)

## <a name="try-it-out-moments"></a><span data-ttu-id="2428f-186">「立即試用」分鐘</span><span class="sxs-lookup"><span data-stu-id="2428f-186">"Try it out" moments</span></span>

<span data-ttu-id="2428f-187">設計全像混合的現實概念，但也可讓您在您的房間內試用。</span><span class="sxs-lookup"><span data-stu-id="2428f-187">Designing Holograms teaches mixed reality concepts, but it also allows you to try them in your room.</span></span> <span data-ttu-id="2428f-188">在這些說明中，我們會暫停並讓您離開娃娃房子並進入互動式時刻。</span><span class="sxs-lookup"><span data-stu-id="2428f-188">After some of those explanations, we pause and take you out of the doll house and into an interactive moment.</span></span> <span data-ttu-id="2428f-189">以下是這些互動式時刻的一些範例：</span><span class="sxs-lookup"><span data-stu-id="2428f-189">Here are some examples of those interactive moments:</span></span>

![手形追蹤框架的動畫 GIF，顯示當偵測到手時以及何時進入 view 欄位時](images/designing-holograms/try-out-1.gif)

<span data-ttu-id="2428f-191">*當偵測到手時，以及當他們進入 view 欄位時，所顯示的手追蹤框架。*</span><span class="sxs-lookup"><span data-stu-id="2428f-191">*The hand tracking frame showing when hands are detected and when they enter the field of view.*</span></span>

![與衝突 crystals 進行互動的動畫 GIF](images/designing-holograms/try-out-2.gif)

<span data-ttu-id="2428f-193">*透過互動方式與衝突 crystals 互動*</span><span class="sxs-lookup"><span data-stu-id="2428f-193">*Interacting with colliding crystals through far interaction*</span></span>

![探索近乎互動 affordances 的動畫 GIF](images/designing-holograms/try-out-3.gif)

<span data-ttu-id="2428f-195">*探索近距離互動 affordances*</span><span class="sxs-lookup"><span data-stu-id="2428f-195">*Exploring near interaction affordances*</span></span>

## <a name="about-the-team"></a><span data-ttu-id="2428f-196">關於小組</span><span class="sxs-lookup"><span data-stu-id="2428f-196">About the team</span></span>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Daniel Escudero" width="60" height="60" src="images/designing-holograms/daniel-escudero.jpeg"></td>
<td style="border-style: none"><span data-ttu-id="2428f-197"><b>Daniel Escudero</b></span><span class="sxs-lookup"><span data-stu-id="2428f-197"><b>Daniel Escudero</b></span></span><br><span data-ttu-id="2428f-198"><i>首席技術設計人員</i></span><span class="sxs-lookup"><span data-stu-id="2428f-198"><i>Lead Technical Designer</i></span></span><br><span data-ttu-id="2428f-199">Dan 是設計全像市的創意總監，目前也是在三藩市的 Microsoft Mixed Reality 學術設計組長的設計，而且之前是 Microsoft 在倫敦的混合現實工作室之一。</span><span class="sxs-lookup"><span data-stu-id="2428f-199">Dan is the Creative Director on Designing Holograms and currently works as Design Lead for the Microsoft’s Mixed Reality Academy in San Francisco, and was previously a Designer in one of Microsoft’s Mixed Reality Studios in London.</span></span></td>
</tr>
</table>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Martin Wettig" width="60" height="60" src="images/designing-holograms/martin-wettig.jpeg"></td>
<td style="border-style: none"><span data-ttu-id="2428f-200"><b>聖馬丁 Wettig</b></span><span class="sxs-lookup"><span data-stu-id="2428f-200"><b>Martin Wettig</b></span></span><br><span data-ttu-id="2428f-201"><i>資深3D 演出者</i></span><span class="sxs-lookup"><span data-stu-id="2428f-201"><i>Senior 3D Artist</i></span></span><br><span data-ttu-id="2428f-202">當您在設計全像全像是 Microsoft 的混合現實工作室中，有一位資深的3D 演出者在柏林上，會導致3D 藝術和 UI 設計。</span><span class="sxs-lookup"><span data-stu-id="2428f-202">Martin leads 3D Art and UI Design on Designing Holograms and was previously a Senior 3D Artist in one of Microsoft’s Mixed Reality Studios in Berlin.</span></span></td>
</tr>
</table>

<span data-ttu-id="2428f-203">很棒的是，「混合的現實設計小組」可讓您在此專案的每個步驟中，將許多人的知識與重要的團隊分享給令人驚喜的 [物件](https://objecttheory.com/) 。</span><span class="sxs-lookup"><span data-stu-id="2428f-203">A huge thank you to the Mixed Reality Design Team for sharing so much knowledge and of course to the amazing folks at [Object Theory](https://objecttheory.com/) that became essential teammates in every single step of this project.</span></span> <span data-ttu-id="2428f-204">感謝您的熱情，讓您在設計上有出色的關注。</span><span class="sxs-lookup"><span data-stu-id="2428f-204">Thank you all for you amazing talent, for your passion and exceptional eye for design.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="2428f-205">下載設計全像影像應用程式</span><span class="sxs-lookup"><span data-stu-id="2428f-205">Download the Designing Holograms app</span></span>](https://www.microsoft.com/p/designing-holograms/9nxwnjklrzwd)