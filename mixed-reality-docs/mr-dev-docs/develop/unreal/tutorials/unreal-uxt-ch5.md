---
title: 5. 新增按鈕並重設棋子位置
description: 教學課程系列的第 5 部分 (共有 6 部分)，使用 Unreal Engine 4 和混合實境工具組 UX 工具外掛程式來建置國際象棋應用程式
author: hferrone
ms.author: v-hferrone
ms.date: 11/18/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 混合實境, 教學課程, 開始使用, mrtk, uxt, UX 工具, 文件, 混合實境頭戴式裝置, windows 混合實境頭戴式裝置, 虛擬實境頭戴式裝置
ms.openlocfilehash: 8e16865e89c06c37f2932f1828bf8ca5551e6fce
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "96609689"
---
# <a name="5-adding-a-button--resetting-piece-locations"></a><span data-ttu-id="e22f3-104">5.新增按鈕並重設棋子位置</span><span class="sxs-lookup"><span data-stu-id="e22f3-104">5. Adding a button & resetting piece locations</span></span>

<span data-ttu-id="e22f3-105">在上一個教學課程中，您已將手動互動動作項目新增至 Pawn，並將操作工具元件新增至國際象棋盤，使其都能夠互動。</span><span class="sxs-lookup"><span data-stu-id="e22f3-105">In the previous tutorial, you added Hand Interaction Actors to the Pawn and Manipulator components to the chess board to make them both interactive.</span></span> <span data-ttu-id="e22f3-106">在本節中，您將繼續使用混合實境工具組 UX 工具外掛程式，透過藍圖中的新函式和動作項目參考來建置您的國際象棋應用程式。</span><span class="sxs-lookup"><span data-stu-id="e22f3-106">In this section, you'll continue to use the Mixed Reality Toolkit UX Tools plugin to build out your chess app with new functions and Actor references in Blueprints.</span></span> <span data-ttu-id="e22f3-107">本節結束時，您將可以在裝置或模擬器上封裝和部署混合實境應用程式。</span><span class="sxs-lookup"><span data-stu-id="e22f3-107">By the end of this section, you'll be ready to package and deploy the mixed reality app on a device or emulator.</span></span>

## <a name="objectives"></a><span data-ttu-id="e22f3-108">目標</span><span class="sxs-lookup"><span data-stu-id="e22f3-108">Objectives</span></span>

* <span data-ttu-id="e22f3-109">新增互動式按鈕</span><span class="sxs-lookup"><span data-stu-id="e22f3-109">Adding an interactive button</span></span>
* <span data-ttu-id="e22f3-110">建立函式來重設棋子的位置</span><span class="sxs-lookup"><span data-stu-id="e22f3-110">Creating a function to reset a pieces' location</span></span>
* <span data-ttu-id="e22f3-111">連結按鈕以在按下按鈕時觸發函式</span><span class="sxs-lookup"><span data-stu-id="e22f3-111">Hooking the button up to trigger the function when pressed</span></span>

## <a name="creating-a-reset-function"></a><span data-ttu-id="e22f3-112">建立重設函式</span><span class="sxs-lookup"><span data-stu-id="e22f3-112">Creating a reset function</span></span>

<span data-ttu-id="e22f3-113">您的第一項工作是建立函式藍圖，將棋子重設為其在場景中的原始位置。</span><span class="sxs-lookup"><span data-stu-id="e22f3-113">Your first task is to create a function blueprint that resets a chess piece to its original position in the scene.</span></span>

1.  <span data-ttu-id="e22f3-114">開啟 **WhiteKing**、選取 [ My 藍圖] 中 [函式] 區段旁的 **+** 圖示，並將其命名為 [Reset Location]。</span><span class="sxs-lookup"><span data-stu-id="e22f3-114">Open **WhiteKing**, select the **+** icon next to the **Functions** section in the **My Blueprint** and name it **Reset Location**.</span></span>

2.  <span data-ttu-id="e22f3-115">從藍圖格線上的 [Reset Location] 拖曳並放開執行，以建立 **SetActorRelativeTransform** 節點。</span><span class="sxs-lookup"><span data-stu-id="e22f3-115">Drag and release the execution from **Reset Location** on the Blueprint grid to create a **SetActorRelativeTransform** node.</span></span>
    * <span data-ttu-id="e22f3-116">此函式會為動作項目設定與其父系相對的變形 (位置、旋轉和縮放)。</span><span class="sxs-lookup"><span data-stu-id="e22f3-116">This function sets the transform (location, rotation, and scale) of an actor relative to its parent.</span></span> <span data-ttu-id="e22f3-117">您會使用此函式來重設棋盤上的國王位置，即使棋盤已從其原始位置移動也一樣。</span><span class="sxs-lookup"><span data-stu-id="e22f3-117">You’ll use this function to reset the king’s position on the board, even if the board has been moved from its original position.</span></span>

3. <span data-ttu-id="e22f3-118">在事件圖形內部按一下滑鼠右鍵，選取 [進行轉換]，並將其 [位置] 變更為 **X =-26**、**Y = 4**、**Z = 0**。</span><span class="sxs-lookup"><span data-stu-id="e22f3-118">Right-click inside the Event Graph, select **Make Transform**, and change its **Location** to **X = -26**, **Y = 4**, **Z = 0**.</span></span>
    * <span data-ttu-id="e22f3-119">將其 [傳回值] 連線到 **SetActorRelativeTransform** 中的 [新增相對轉換] 釘選。</span><span class="sxs-lookup"><span data-stu-id="e22f3-119">Connect its **Return Value** to the **New Relative Transform** pin in **SetActorRelativeTransform**.</span></span>

![重設位置函式](images/unreal-uxt/5-function.PNG)

<span data-ttu-id="e22f3-121">**編譯** 並 **儲存** 專案，然後回到主視窗。</span><span class="sxs-lookup"><span data-stu-id="e22f3-121">**Compile** and **Save** the project before returning to the Main window.</span></span>


## <a name="adding-a-button"></a><span data-ttu-id="e22f3-122">新增按鈕</span><span class="sxs-lookup"><span data-stu-id="e22f3-122">Adding a button</span></span>

<span data-ttu-id="e22f3-123">既然已正確設定函式，您的下一項工作就是建立按鈕，讓該函式在被觸碰時啟動。</span><span class="sxs-lookup"><span data-stu-id="e22f3-123">Now that the function is set up correctly, your next task is to create a button that fires it off when touched.</span></span>

1.  <span data-ttu-id="e22f3-124">按一下 [新增] > [藍圖類別]、展開 [所有類別] 區段，然後搜尋 **UxtPressableButtonActor**。</span><span class="sxs-lookup"><span data-stu-id="e22f3-124">Click **Add New > Blueprint Class**, expand the **All Classes** section, and search for **UxtPressableButtonActor**.</span></span>
    * <span data-ttu-id="e22f3-125">將其命名為 **ResetButton**，然後按兩下以開啟藍圖</span><span class="sxs-lookup"><span data-stu-id="e22f3-125">Name it **ResetButton** and double click to open the Blueprint</span></span>

![從 HoloLens 2 樣式按鈕建立新藍圖的子類別](images/unreal-uxt/5-subclass.PNG)

2. <span data-ttu-id="e22f3-127">確定已在 [元件] 面板中選取 **ResetButton(self)** 。</span><span class="sxs-lookup"><span data-stu-id="e22f3-127">Ensure **ResetButton(self)** is selected in the **Components** panel.</span></span> <span data-ttu-id="e22f3-128">在 [詳細資料] 面板中，瀏覽至 [按鈕] 區段。</span><span class="sxs-lookup"><span data-stu-id="e22f3-128">In the **Details** panel, navigate to the **Button** section.</span></span> <span data-ttu-id="e22f3-129">將預設的 [按鈕標籤] 變更為 [重設]，展開 [按鈕圖示筆刷] 區段，然後按 [開啟圖示筆刷編輯器] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="e22f3-129">Change the default **Button Label** to "Reset", expand the **Button Icon Brush** section, and press the **Open Icon Brush Editor** button.</span></span>

![設定按鈕上的標籤和圖示](images/unreal-uxt/5-buttonconfig.PNG)

<span data-ttu-id="e22f3-131">圖示筆刷編輯器隨即開啟，可讓您用來為按鈕選取新的圖示。</span><span class="sxs-lookup"><span data-stu-id="e22f3-131">The Icon Brush Editor will open, which you can use to select a new icon for your button.</span></span>

![選取按鈕的圖示](images/unreal-uxt/5-iconbrusheditor.PNG)

<span data-ttu-id="e22f3-133">此外還有許多設定可供調整，用以設定您的按鈕。</span><span class="sxs-lookup"><span data-stu-id="e22f3-133">There are plenty of other settings you can adjust to configure your button.</span></span> <span data-ttu-id="e22f3-134">若要深入了解 UXT 可點按的按鈕元件，請參閱[文件](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/PressableButton.html)。</span><span class="sxs-lookup"><span data-stu-id="e22f3-134">To learn more about the UXT Pressable Button component, check out the [documentation](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/PressableButton.html).</span></span>

3. <span data-ttu-id="e22f3-135">在 [元件] 面板中按一下 [ButtonComponent (繼承)]，然後將 [詳細資料] 面板向下捲動至 [事件] 區段。</span><span class="sxs-lookup"><span data-stu-id="e22f3-135">Click **ButtonComponent (Inherited)** in the **Components** panel and scroll down the **Details** panel to the **Events** section.</span></span>
    * <span data-ttu-id="e22f3-136">按一下 [On Button Pressed] 旁邊的綠色 **+** 按鈕，將事件新增至事件圖形，如此在按下按鈕時便會呼叫該事件。</span><span class="sxs-lookup"><span data-stu-id="e22f3-136">Click the green **+** button next to **On Button Pressed** to add an event to the Event Graph, which will be called when the button is pressed.</span></span>

<span data-ttu-id="e22f3-137">從這裡開始，您會想要呼叫 **WhiteKing** 的 **Reset Location** 函式，該函式需要參考層級中的 **WhiteKing** 動作項目。</span><span class="sxs-lookup"><span data-stu-id="e22f3-137">From here, you’ll want to call **WhiteKing**’s **Reset Location** function, which needs a reference to the **WhiteKing** Actor in the Level.</span></span>

4.  <span data-ttu-id="e22f3-138">在 [我的藍圖] 面板中，瀏覽至 [變數] 區段、按一下 **+** 按鈕，並將變數命名為 **WhiteKing**。</span><span class="sxs-lookup"><span data-stu-id="e22f3-138">In the **My Blueprint** panel, navigate to the **Variables** section, click the **+** button, and name the variable **WhiteKing**.</span></span>
    * <span data-ttu-id="e22f3-139">在 [詳細資料] 面板中，選取 [變數類型] 旁的下拉式清單，搜尋 **WhiteKing**，然後選取 [物件參考]。</span><span class="sxs-lookup"><span data-stu-id="e22f3-139">In the **Details** panel, select the dropdown next to **Variable Type**, search for **WhiteKing**, and select the **Object Reference**.</span></span>
    * <span data-ttu-id="e22f3-140">核取 [可編輯執行個體] 旁的方塊，此方塊可讓您從主要層級設定變數。</span><span class="sxs-lookup"><span data-stu-id="e22f3-140">Check the box next to **Instance Editable**, which allows the variable to be set from the Main Level.</span></span>

![建立變數](images/unreal-uxt/5-var.PNG)

5.  <span data-ttu-id="e22f3-142">將 WhiteKing 變數從 [我的藍圖] > [變數] 拖曳到重設按鈕事件圖形，然後選擇 [取得 WhiteKing]。</span><span class="sxs-lookup"><span data-stu-id="e22f3-142">Drag the WhiteKing variable from **My Blueprint > Variables** onto the Reset Button Event Graph and choose **Get WhiteKing**.</span></span>

## <a name="firing-the-function"></a><span data-ttu-id="e22f3-143">啟動函式</span><span class="sxs-lookup"><span data-stu-id="e22f3-143">Firing the function</span></span>

<span data-ttu-id="e22f3-144">剩下的工作就是在按下按鈕時，正式啟動重設函式。</span><span class="sxs-lookup"><span data-stu-id="e22f3-144">All that's left is to officially fire off the reset function when the button is pressed.</span></span>

1.  <span data-ttu-id="e22f3-145">拖放 WhiteKing 輸出連接，以放置新的節點。</span><span class="sxs-lookup"><span data-stu-id="e22f3-145">Drag the WhiteKing output pin and release to place a new node.</span></span> <span data-ttu-id="e22f3-146">選取 **Reset Location** 函式。</span><span class="sxs-lookup"><span data-stu-id="e22f3-146">Select the **Reset Location** function.</span></span> <span data-ttu-id="e22f3-147">最後，將輸出執行連接點從 [On Button Pressed] 拖曳至 [Reset Location] 上的輸入執行連接點。</span><span class="sxs-lookup"><span data-stu-id="e22f3-147">Finally, drag the outgoing execution pin from **On Button Pressed** to the incoming execution pin on **Reset Location**.</span></span> <span data-ttu-id="e22f3-148">**編譯** 並 **儲存** ResetButton 藍圖，然後回到主視窗。</span><span class="sxs-lookup"><span data-stu-id="e22f3-148">**Compile** and **Save** the ResetButton Blueprint, then return to the Main window.</span></span>

![從 On Button Pressed 呼叫 Reset Location 函式](images/unreal-uxt/5-callresetloc.PNG)

2.  <span data-ttu-id="e22f3-150">將 **ResetButton** 拖曳到檢視區，並將其位置設定為 **X = 50**、**Y = -25** 和 **Z = 10**。</span><span class="sxs-lookup"><span data-stu-id="e22f3-150">Drag **ResetButton** into the viewport and set its location to **X = 50**, **Y = -25**, and **Z = 10**.</span></span> <span data-ttu-id="e22f3-151">將其旋轉設定為 **Z = 180**。</span><span class="sxs-lookup"><span data-stu-id="e22f3-151">Set its rotation to **Z = 180**.</span></span> <span data-ttu-id="e22f3-152">在 [預設值] 底下，將 **WhiteKing** 變數的值設定為 **WhiteKing**。</span><span class="sxs-lookup"><span data-stu-id="e22f3-152">Under **Default**, set the value of the **WhiteKing** variable to **WhiteKing**.</span></span>

![設定變數](images/unreal-uxt/5-buttonlevel.PNG)

<span data-ttu-id="e22f3-154">執行應用程式、將棋子移至新位置，然後按下 HoloLens 2 樣式按鈕，以查看作用中的重設邏輯！</span><span class="sxs-lookup"><span data-stu-id="e22f3-154">Run the app, move the chess piece to a new location, and press your HoloLens 2-style button to see the reset logic in action!</span></span>

<span data-ttu-id="e22f3-155">您現在有一個混合實境應用程式，其中包含可互動的棋子和棋盤，還有一個功能完整的按鈕，可重設棋子的位置。</span><span class="sxs-lookup"><span data-stu-id="e22f3-155">You now have a mixed reality app with an interactable chess piece and board, and a fully functioning button that resets the piece’s location.</span></span> <span data-ttu-id="e22f3-156">到目前為止，您可在 [GitHub](https://github.com/microsoft/MixedReality-Unreal-Samples/tree/master/ChessApp) 存放庫中找到完成的應用程式。</span><span class="sxs-lookup"><span data-stu-id="e22f3-156">You can find the completed app up to this point in its [GitHub](https://github.com/microsoft/MixedReality-Unreal-Samples/tree/master/ChessApp) repo.</span></span> <span data-ttu-id="e22f3-157">您可以隨意進行超越本教學課程範圍的內容並設定其餘的棋子，讓整個棋盤都可在您按下按鈕時重設。</span><span class="sxs-lookup"><span data-stu-id="e22f3-157">Feel free to go beyond this tutorial and set up the rest of the chess pieces so that the entire board is reset when you press the reset button.</span></span>

![檢視區中的最終場景](images/unreal-uxt/5-endscene.PNG)

<span data-ttu-id="e22f3-159">您已準備好繼續進行本教學課程的最後一節，在這裡您將了解如何封裝應用程式，並將其部署至裝置或模擬器。</span><span class="sxs-lookup"><span data-stu-id="e22f3-159">You're ready to move on to the final section of this tutorial where you'll learn how to package and deploy the app to a device or emulator.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e22f3-160">此時，您應先使用建議的 **[Unreal 效能設定](../performance-recommendations-for-unreal.md)** 更新您的專案，再將應用程式部署至裝置或模擬器。</span><span class="sxs-lookup"><span data-stu-id="e22f3-160">At this point, you should update your project with the recommended **[Unreal performance settings](../performance-recommendations-for-unreal.md)** before deploying your application to a device or emulator.</span></span>

[<span data-ttu-id="e22f3-161">下一節：6.封裝並部署至裝置或模擬器</span><span class="sxs-lookup"><span data-stu-id="e22f3-161">Next Section: 6. Packaging & deploying to device or emulator</span></span>](unreal-uxt-ch6.md)
