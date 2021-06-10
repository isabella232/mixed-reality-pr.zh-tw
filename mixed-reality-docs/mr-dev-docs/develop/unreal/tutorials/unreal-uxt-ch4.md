---
title: 4. 使場景成為互動式場景
description: 教學課程系列的第 4 部分 (共有 6 部分)，使用 Unreal Engine 4 和混合實境工具組 UX 工具外掛程式來建置國際象棋應用程式
author: hferrone
ms.author: v-hferrone
ms.date: 11/18/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 混合實境, 教學課程, 開始使用, mrtk, uxt, UX 工具, 文件, 混合實境頭戴式裝置, windows 混合實境頭戴式裝置, 虛擬實境頭戴式裝置
ms.openlocfilehash: 771dd4028adfacb27544e632aa0f355d3bc91c66
ms.sourcegitcommit: 4a6c26615d52776bdc4faab70391592092a471fc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2021
ms.locfileid: "110712595"
---
# <a name="4-making-your-scene-interactive"></a><span data-ttu-id="687b7-104">4.使場景成為互動式場景</span><span class="sxs-lookup"><span data-stu-id="687b7-104">4. Making your scene interactive</span></span>

<span data-ttu-id="687b7-105">在上一個教學課程中，您已新增 ARSession、Pawn 和遊戲模式，來完成適用於國際象棋應用程式的混合實境設定。</span><span class="sxs-lookup"><span data-stu-id="687b7-105">In the previous tutorial, you added an ARSession, Pawn, and Game Mode to complete the mixed reality setup for the chess app.</span></span> <span data-ttu-id="687b7-106">本節著重於使用開放原始碼[混合實境工具組 UX 工具](https://github.com/microsoft/MixedReality-UXTools-Unreal)外掛程式，其提供讓場景成為互動式場景的工具。</span><span class="sxs-lookup"><span data-stu-id="687b7-106">This section focuses on using the open source [Mixed Reality Toolkit UX Tools](https://github.com/microsoft/MixedReality-UXTools-Unreal) plugin, which provides tools to make the scene interactive.</span></span> <span data-ttu-id="687b7-107">在本節結束時，您的棋子將透過使用者輸入而移動。</span><span class="sxs-lookup"><span data-stu-id="687b7-107">By the end of this section, your chess pieces will be moving by user input.</span></span>

## <a name="objectives"></a><span data-ttu-id="687b7-108">目標</span><span class="sxs-lookup"><span data-stu-id="687b7-108">Objectives</span></span>

* <span data-ttu-id="687b7-109">安裝 Mixed Reality UX 工具外掛程式</span><span class="sxs-lookup"><span data-stu-id="687b7-109">Installing the Mixed Reality UX Tools plugin</span></span>
* <span data-ttu-id="687b7-110">將手部互動動作項目新增至您的指尖</span><span class="sxs-lookup"><span data-stu-id="687b7-110">Adding Hand Interaction Actors to your fingertips</span></span>
* <span data-ttu-id="687b7-111">建立操作工具並將其新增到場景中的物件</span><span class="sxs-lookup"><span data-stu-id="687b7-111">Creating and adding Manipulators to objects in the scene</span></span>
* <span data-ttu-id="687b7-112">使用輸入模擬來驗證專案</span><span class="sxs-lookup"><span data-stu-id="687b7-112">Using input simulation to validate the project</span></span>

## <a name="downloading-the-mixed-reality-ux-tools-plugin"></a><span data-ttu-id="687b7-113">下載混合實境 UX 工具外掛程式</span><span class="sxs-lookup"><span data-stu-id="687b7-113">Downloading the Mixed Reality UX Tools plugin</span></span>
<span data-ttu-id="687b7-114">開始使用使用者輸入之前，您必須先將 Mixed Reality UX 工具外掛程式新增至專案。</span><span class="sxs-lookup"><span data-stu-id="687b7-114">Before you start working with user input, you'll need to add the Mixed Reality UX Tools plugin to the project.</span></span> <span data-ttu-id="687b7-115">若要深入瞭解 UX 工具，您可以在 [GitHub](https://aka.ms/uxt-unreal)上查看專案。</span><span class="sxs-lookup"><span data-stu-id="687b7-115">To learn more about UX Tools, you can check out the project on [GitHub](https://aka.ms/uxt-unreal).</span></span>

1. <span data-ttu-id="687b7-116">開啟 [長篇比賽] 啟動器。</span><span class="sxs-lookup"><span data-stu-id="687b7-116">Open the Epic Games Launcher.</span></span> <span data-ttu-id="687b7-117">流覽至 Unreal Engine Marketplace 並搜尋「[混合現實 UX 工具](https://www.unrealengine.com/marketplace/en-US/product/mixed-reality-ux-tools)」。</span><span class="sxs-lookup"><span data-stu-id="687b7-117">Navigate to Unreal Engine Marketplace and search for "[Mixed Reality UX Tools](https://www.unrealengine.com/marketplace/en-US/product/mixed-reality-ux-tools)".</span></span> <span data-ttu-id="687b7-118">將外掛程式安裝到您的引擎。</span><span class="sxs-lookup"><span data-stu-id="687b7-118">Install the plugin to your engine.</span></span>

![Unreal Marketplace](images/unreal-uxt/2-uxt-plugin.PNG)

2. <span data-ttu-id="687b7-120">回到 [Unreal 編輯器]，移至 [**專案設定**]  >  **外掛程式**，並搜尋「混合式現實 UX 工具」。</span><span class="sxs-lookup"><span data-stu-id="687b7-120">Back in the Unreal editor, go to **Project Settings** > **Plugins** and search for "Mixed Reality UX Tools".</span></span> <span data-ttu-id="687b7-121">確定已啟用外掛程式，並在出現提示時重新開機編輯器。</span><span class="sxs-lookup"><span data-stu-id="687b7-121">Ensure the plugin is enabled and restart the editor if prompted.</span></span>

![啟用混合式現實 UX 工具外掛程式](images/unreal-uxt/2-enable-uxt.PNG)

3.  <span data-ttu-id="687b7-123">UXTools 外掛程式的 Content 資料夾具有元件的子資料夾，包括 **按鈕**、 **XR 模擬** 和 **指標**，以及具有額外程式碼的 c + + 類別資料夾。</span><span class="sxs-lookup"><span data-stu-id="687b7-123">The UXTools plugin has a Content folder with subfolders for components, including **Buttons**, **XR Simulation**, and **Pointers**, and a C++ Classes folder with additional code.</span></span>  

> [!NOTE]
> <span data-ttu-id="687b7-124">如果您在 **內容瀏覽器** 中看不到 [ **UXTools 內容**] 區段，請按一下 [**視圖選項] > 顯示引擎內容**]。</span><span class="sxs-lookup"><span data-stu-id="687b7-124">If you don’t see the **UXTools Content** section in the **Content Browser**, click **View Options > Show Engine Content**.</span></span>

![顯示引擎內容](images/unreal-uxt/4-showenginecontent.PNG)

<span data-ttu-id="687b7-126">如需其他外掛程式文件，可以從混合實境 UX 工具 GitHub [存放庫](https://aka.ms/uxt-unreal)取得。</span><span class="sxs-lookup"><span data-stu-id="687b7-126">Additional plugin documentation can be found on the Mixed Reality UX Tools GitHub [repository](https://aka.ms/uxt-unreal).</span></span>

<span data-ttu-id="687b7-127">安裝外掛程式後，您就可以開始使用程式所提供的工具，從手部互動動作項目開始。</span><span class="sxs-lookup"><span data-stu-id="687b7-127">With the plugin installed, you're ready to start using the tools it has to offer, starting with hand interaction actors.</span></span>

## <a name="spawning-hand-interaction-actors"></a><span data-ttu-id="687b7-128">繁衍手部互動動作項目</span><span class="sxs-lookup"><span data-stu-id="687b7-128">Spawning Hand Interaction Actors</span></span>

<span data-ttu-id="687b7-129">與 UX 元素的手動互動是搭配手動互動動作項目來執行，此動作項目會建立及驅動指標和視覺效果，以進行遠近距離互動。</span><span class="sxs-lookup"><span data-stu-id="687b7-129">Hand interaction with UX elements is done with Hand Interaction Actors, which create and drive the pointers and visuals for near and far interactions.</span></span>
- <span data-ttu-id="687b7-130">*近距離互動* - 在食指與拇指之間捏合元素或用指尖點戳。</span><span class="sxs-lookup"><span data-stu-id="687b7-130">*Near interactions* - pinching elements between index finger and thumb or by poking them with a fingertip.</span></span>
- <span data-ttu-id="687b7-131">*遠距離互動* - 將虛擬手發出的光線指向某個元素，並同時按下食指和拇指。</span><span class="sxs-lookup"><span data-stu-id="687b7-131">*Far interactions* - pointing a ray from the virtual hand at an element and pressing index and thumb together.</span></span>

<span data-ttu-id="687b7-132">在我們的案例中，將手部互動動作項目新增至 **MRPawn** 將會：</span><span class="sxs-lookup"><span data-stu-id="687b7-132">In our case, adding a Hand Interaction Actor to **MRPawn** will:</span></span>
- <span data-ttu-id="687b7-133">新增游標至 Pawn 食指的指尖。</span><span class="sxs-lookup"><span data-stu-id="687b7-133">Add a cursor to the tips of the Pawn’s index fingers.</span></span>
- <span data-ttu-id="687b7-134">提供以關節連接的手部輸入事件，可透過 Pawn 操作。</span><span class="sxs-lookup"><span data-stu-id="687b7-134">Provide articulated hand input events that can be manipulated through the Pawn.</span></span>
- <span data-ttu-id="687b7-135">允許透過從虛擬手掌延伸的手部光線，進行遠距離互動輸入事件。</span><span class="sxs-lookup"><span data-stu-id="687b7-135">Allow far interaction input events through hand rays extending from the palms of the virtual hands.</span></span>

<span data-ttu-id="687b7-136">建議您先閱讀手部互動的[文件](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/HandInteraction.html)，再繼續進行。</span><span class="sxs-lookup"><span data-stu-id="687b7-136">We recommend reading through the [documentation](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/HandInteraction.html) on hand interactions before continuing.</span></span>

<span data-ttu-id="687b7-137">一旦準備好，就開啟 **MRPawn** 藍圖，然後移至 [事件圖形]。</span><span class="sxs-lookup"><span data-stu-id="687b7-137">Once you're ready, open the **MRPawn** Blueprint and go to the **Event Graph**.</span></span>

1. <span data-ttu-id="687b7-138">從 **Event BeginPlay** 拖曳並放開執行釘選，以放置新的節點。</span><span class="sxs-lookup"><span data-stu-id="687b7-138">Drag and release the execution pin from **Event BeginPlay** to place a new node.</span></span>
    * <span data-ttu-id="687b7-139">選取 [從類別繁衍動作項目]、按一下 [類別] 釘選旁的下拉式清單，然後搜尋 [Uxt 手部互動動作項目]。</span><span class="sxs-lookup"><span data-stu-id="687b7-139">Select **Spawn Actor from Class**, click the dropdown next to the **Class** pin and search for **Uxt Hand Interaction Actor**.</span></span>  

2. <span data-ttu-id="687b7-140">繁衍第二個 [Uxt 手部互動動作項目]，這次會將 [手部] 設定為 [右手]。</span><span class="sxs-lookup"><span data-stu-id="687b7-140">Spawn a second **Uxt Hand Interaction Actor**, this time setting the **Hand** to **Right**.</span></span> <span data-ttu-id="687b7-141">當事件開始時，會在每個手部上繁衍 Uxt 手部互動動作項目。</span><span class="sxs-lookup"><span data-stu-id="687b7-141">When the event begins, a Uxt Hand Interaction Actor will be spawned on each hand.</span></span>

<span data-ttu-id="687b7-142">您的 [事件圖形] 應該符合下列螢幕擷取畫面：</span><span class="sxs-lookup"><span data-stu-id="687b7-142">Your **Event Graph** should match the following screenshot:</span></span>

![繁衍 UXT 手部互動動作項目](images/unreal-uxt/4-spawnactor.PNG)

<span data-ttu-id="687b7-144">這兩個 Uxt 手部互動動作項目都需要擁有者和初始轉換位置。</span><span class="sxs-lookup"><span data-stu-id="687b7-144">Both Uxt Hand Interaction Actors need owners and initial transform locations.</span></span> <span data-ttu-id="687b7-145">在此情況下，初始轉換並不重要，因為 UX 工具會讓「手互動」動作專案在看到時立即跳到虛擬手。</span><span class="sxs-lookup"><span data-stu-id="687b7-145">The initial transform doesn’t matter in this case because UX Tools will have the Hand Interaction Actors jump to the virtual hands as soon as they're visible.</span></span> <span data-ttu-id="687b7-146">不過，`SpawnActor` 函式需要轉換輸入來避免編譯器錯誤，因此您將使用預設值。</span><span class="sxs-lookup"><span data-stu-id="687b7-146">However, the `SpawnActor` function requires a Transform input to avoid a compiler error, so you'll use the default values.</span></span>

1. <span data-ttu-id="687b7-147">從其中一個 [繁衍轉換] 釘選拖曳並放開釘選，以放置新的節點。</span><span class="sxs-lookup"><span data-stu-id="687b7-147">Drag and release the pin off one of the **Spawn Transform** pins to place a new node.</span></span>
    * <span data-ttu-id="687b7-148">搜尋 [進行轉換] 節點，然後將 [傳回值] 拖曳至另一手的 [繁衍轉換]，讓兩個 **SpawnActor** 節點連線。</span><span class="sxs-lookup"><span data-stu-id="687b7-148">Search for the **Make Transform** node, then drag the **Return Value** to the other hand’s **Spawn Transform** so that both **SpawnActor** nodes are connected.</span></span>

2.  <span data-ttu-id="687b7-149">選取兩個 **SpawnActor** 節點底端的 **向下箭頭**，以顯示 [擁有者] 釘選。</span><span class="sxs-lookup"><span data-stu-id="687b7-149">Select the **down arrow** at the bottom of both **SpawnActor** nodes to reveal the **Owner** pin.</span></span>    
    * <span data-ttu-id="687b7-150">從其中一個 **擁有者** 釘選拖曳釘選，然後放開以放置新的節點。</span><span class="sxs-lookup"><span data-stu-id="687b7-150">Drag the pin off one of the **Owner** pins and release to place a new node.</span></span>
    * <span data-ttu-id="687b7-151">搜尋 **本身**，然後選取 **取得本身的參考** 變數。</span><span class="sxs-lookup"><span data-stu-id="687b7-151">Search for **self** and select the **Get a reference to self** variable.</span></span>
    * <span data-ttu-id="687b7-152">在 **本身** 物件參考節點與另一個手部互動動作項目的 **擁有者** 釘選之間建立連結。</span><span class="sxs-lookup"><span data-stu-id="687b7-152">Create a link between the **Self** object reference node and the other Hand Interaction Actor’s **Owner** pin.</span></span>
3. <span data-ttu-id="687b7-153">最後，應對兩個手部互動動作項目都核取 [在抓取目標上顯示近處的游標] 方塊。</span><span class="sxs-lookup"><span data-stu-id="687b7-153">Lastly, check the **Show Near Cursor on Grab Targets** box for both Hand Interaction Actors.</span></span> <span data-ttu-id="687b7-154">當您的食指靠近時，抓取目標上應該會出現游標，讓您能夠看出手指與目標的相對位置。</span><span class="sxs-lookup"><span data-stu-id="687b7-154">A cursor should appear on the grab target as your index finger gets close, so you can see where your finger is relative to the target.</span></span>
    * <span data-ttu-id="687b7-155">**編譯**、**儲存**，然後返回主視窗。</span><span class="sxs-lookup"><span data-stu-id="687b7-155">**Compile**, **save**, and return to the Main window.</span></span>

<span data-ttu-id="687b7-156">確定連線符合下列螢幕擷取畫面，但是您可以隨意拖曳節點，讓您的藍圖更容易閱讀。</span><span class="sxs-lookup"><span data-stu-id="687b7-156">Make sure the connections match the following screenshot, but feel free to drag around nodes to make your Blueprint more readable.</span></span>

![完成 UXT 手部互動動作項目設定](images/unreal-uxt/4-fingerptrs.PNG)

<span data-ttu-id="687b7-158">您可以在 [UX 工具文件](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/HandInteraction.html)中找到關於手動互動動作項目的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="687b7-158">You can find more information about Hand Interaction Actors in the [UX Tools documentation](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/HandInteraction.html).</span></span>

<span data-ttu-id="687b7-159">現在，專案中的虛擬手部有一種方式可以選取物件，但仍然無法進行操作。</span><span class="sxs-lookup"><span data-stu-id="687b7-159">Now the virtual hands in the project have a way of selecting objects, but they still can't manipulate them.</span></span> <span data-ttu-id="687b7-160">測試應用程式前的最後一項工作是將操作工具元件新增至場景中的動作項目。</span><span class="sxs-lookup"><span data-stu-id="687b7-160">Your last task before testing the app is to add Manipulator components to the actors in the scene.</span></span>

## <a name="attaching-manipulators"></a><span data-ttu-id="687b7-161">附加操作工具</span><span class="sxs-lookup"><span data-stu-id="687b7-161">Attaching Manipulators</span></span>

<span data-ttu-id="687b7-162">操作工具是一種元件，可回應以關節連接的手部輸入，而且可以抓取、旋轉和轉譯。</span><span class="sxs-lookup"><span data-stu-id="687b7-162">A Manipulator is a component that responds to articulated hand input and can be grabbed, rotated, and translated.</span></span> <span data-ttu-id="687b7-163">將操作工具的轉換套用至動作項目轉換可允許直接動作項目操作。</span><span class="sxs-lookup"><span data-stu-id="687b7-163">Applying the Manipulator’s transform to an Actors transform allows direct Actor manipulation.</span></span>

1. <span data-ttu-id="687b7-164">開啟 [棋盤] 藍圖、按一下 [新增元件]，然後在 [元件] 面板中搜尋 [Uxt 一般操作工具]。</span><span class="sxs-lookup"><span data-stu-id="687b7-164">Open the **Board** blueprint, click **Add Component** and search for **Uxt Generic Manipulator** in the **Components** panel.</span></span>

![新增一般操作工具](images/unreal-uxt/4-addmanip.PNG)

2. <span data-ttu-id="687b7-166">展開 [詳細資料] 面板中的 [一般操作工具] 區段。</span><span class="sxs-lookup"><span data-stu-id="687b7-166">Expand the **Generic Manipulator** section in the **Details** panel.</span></span> <span data-ttu-id="687b7-167">您可以從這裡設定單手或雙手操作、旋轉模式和其他等等。</span><span class="sxs-lookup"><span data-stu-id="687b7-167">You can set one-handed or two-handed manipulation, rotation mode, and smoothing from here.</span></span> <span data-ttu-id="687b7-168">請隨意選取您想要的任何模式，然後 [編譯] 及 [儲存] 棋盤。</span><span class="sxs-lookup"><span data-stu-id="687b7-168">Feel free to select whichever modes you wish, then **Compile** and **Save** Board.</span></span>

![設定模式](images/unreal-uxt/4-setrotmode.PNG)

3. <span data-ttu-id="687b7-170">針對 **WhiteKing** 動作項目重複上述步驟。</span><span class="sxs-lookup"><span data-stu-id="687b7-170">Repeat the steps above for the **WhiteKing** Actor.</span></span>

<span data-ttu-id="687b7-171">若要深入了解混合實境 UX 工具外掛程式中提供的操作工具元件，請參閱[文件](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/Manipulator.html)。</span><span class="sxs-lookup"><span data-stu-id="687b7-171">You can find more information about the Manipulator Components provided in the Mixed Reality UX Tools plugin in the [documentation](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/Manipulator.html).</span></span>

## <a name="testing-the-scene"></a><span data-ttu-id="687b7-172">測試場景</span><span class="sxs-lookup"><span data-stu-id="687b7-172">Testing the scene</span></span>

<span data-ttu-id="687b7-173">好消息！</span><span class="sxs-lookup"><span data-stu-id="687b7-173">Good news everyone!</span></span> <span data-ttu-id="687b7-174">您已經準備好使用新的虛擬手部和使用者輸入來測試應用程式。</span><span class="sxs-lookup"><span data-stu-id="687b7-174">You're ready to test out the app with its new virtual hands and user input.</span></span> <span data-ttu-id="687b7-175">按下主視窗中的 [播放]，您會看到兩個網狀手部，以及從每一個手掌延伸的光線。</span><span class="sxs-lookup"><span data-stu-id="687b7-175">Press **Play** in the Main Window and you'll see two mesh hands with rays extending from each hand’s palm.</span></span> <span data-ttu-id="687b7-176">您可以控制手部及其互動，如下所示：</span><span class="sxs-lookup"><span data-stu-id="687b7-176">You can control the hands and their interactions as follows:</span></span>
- <span data-ttu-id="687b7-177">按住 **左 Alt** 鍵，以控制 **左手**，按住 **左 Shift** 鍵，以控制 **右手**。</span><span class="sxs-lookup"><span data-stu-id="687b7-177">Hold down the **left Alt** key to control the **left hand** and the **left Shift** key to control the **right hand**.</span></span>
- <span data-ttu-id="687b7-178">移動您的滑鼠來移動手部，並使用您的 **滑鼠滾輪** 來捲動，將手部 **向前** 或 **向後** 移動。</span><span class="sxs-lookup"><span data-stu-id="687b7-178">Move your mouse to move the hand and scroll with your **mouse wheel** to move the hand **forwards** or **backwards**.</span></span>
- <span data-ttu-id="687b7-179">使用滑鼠左鍵 **捏合**，使用滑鼠中間按鈕 **撥開**。</span><span class="sxs-lookup"><span data-stu-id="687b7-179">Use the left mouse button to **pinch** and the middle mouse button to **poke**.</span></span>

> [!NOTE]
> <span data-ttu-id="687b7-180">如果您將多個頭戴式裝置插入電腦，輸入模擬可能無法正常運作。</span><span class="sxs-lookup"><span data-stu-id="687b7-180">Input simulation may not work if you have multiple headsets plugged into your PC.</span></span> <span data-ttu-id="687b7-181">如有問題，請嘗試拔掉其他頭戴式裝置。</span><span class="sxs-lookup"><span data-stu-id="687b7-181">If you're having issues, try unplugging your other headsets.</span></span>

![檢視區中的模擬手部](images/unreal-uxt/4-handsim.PNG)

<span data-ttu-id="687b7-183">試著使用模擬的手部來拾起、移動和放置白棋國王，並操作棋盤！</span><span class="sxs-lookup"><span data-stu-id="687b7-183">Try using the simulated hands to pick up, move, and set down the white chess king and manipulate the board!</span></span> <span data-ttu-id="687b7-184">實驗遠近距離互動 - 請注意，當您的手夠靠近可以直接抓取棋盤和國王時，食指指尖上的手指游標會取代手部光線。</span><span class="sxs-lookup"><span data-stu-id="687b7-184">Experiment with both near and far interaction - notice that when your hands get close enough to grab the board and king directly, a finger cursor at the tip of the index finger replaces the hand ray.</span></span>

<span data-ttu-id="687b7-185">若要深入了解 MRTK UX 工具外掛程式中所提供的模擬手部功能，請參閱[文件](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/InputSimulation.html)。</span><span class="sxs-lookup"><span data-stu-id="687b7-185">You can find more information about the simulated hands feature provided by the MRTK UX Tools plugin in the [documentation](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/InputSimulation.html).</span></span>

<span data-ttu-id="687b7-186">既然您的虛擬手部可以與物件互動，您就可以繼續進行下一個教學課程，並新增使用者介面和事件。</span><span class="sxs-lookup"><span data-stu-id="687b7-186">Now that your virtual hands can interact with objects, you're ready to move on to the next tutorial and add user interfaces and events.</span></span>

[<span data-ttu-id="687b7-187">下一節：5.新增按鈕並重設棋子位置</span><span class="sxs-lookup"><span data-stu-id="687b7-187">Next Section: 5. Adding a button & resetting piece locations</span></span>](unreal-uxt-ch5.md)
