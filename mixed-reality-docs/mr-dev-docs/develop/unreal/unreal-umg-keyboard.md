---
title: Unreal 中的 UMG 和鍵盤
description: 瞭解如何使用 Unrealm 動畫圖形來建立小工具的 UI 系統。
author: hferrone
ms.author: suwu
ms.date: 11/25/2020
ms.topic: article
keywords: Windows Mixed Reality、全像移動、HoloLens 2、眼睛追蹤、眼睛輸入、前端掛載顯示器、Unreal 引擎、混合現實耳機、windows Mixed Reality 耳機、虛擬實境耳機、widget、UI、UMG、Unreal 運動圖形、Unreal 引擎、UE、UE4
ms.openlocfilehash: 59ad108a0e27298256f4f0d1661381a4f1748777
ms.sourcegitcommit: 32cb81eee976e73cd661c2b347691c37865a60bc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/04/2020
ms.locfileid: "96609759"
---
# <a name="umg-and-keyboard-in-unreal"></a><span data-ttu-id="bc1b2-104">Unreal 中的 UMG 和鍵盤</span><span class="sxs-lookup"><span data-stu-id="bc1b2-104">UMG and keyboard in Unreal</span></span>

<span data-ttu-id="bc1b2-105">Unreal 動畫圖形 (UMG) 是 Unreal 引擎的內建 UI 系統，用來建立功能表和文字方塊等介面。</span><span class="sxs-lookup"><span data-stu-id="bc1b2-105">Unreal Motion Graphics (UMG) is Unreal Engine’s built-in UI system, used to create interfaces such as menus and text boxes.</span></span> <span data-ttu-id="bc1b2-106">使用 UMG 所建立的使用者介面是由小工具所組成。</span><span class="sxs-lookup"><span data-stu-id="bc1b2-106">User interfaces built with UMG consist of widgets.</span></span> <span data-ttu-id="bc1b2-107">我們將引導您建立新的 widget、將其新增至世界空間，以及使用系統鍵盤作為範例來啟用互動。</span><span class="sxs-lookup"><span data-stu-id="bc1b2-107">We'll guide you through creating a new widget, adding it to world space, and enabling interaction using the system keyboard as an example.</span></span> <span data-ttu-id="bc1b2-108">您可以在官方的 Unreal 引擎 [檔](https://docs.unrealengine.com/en-US/Engine/UMG/index.html)中深入瞭解 UMG。</span><span class="sxs-lookup"><span data-stu-id="bc1b2-108">You can learn more about UMG in the official Unreal Engine [documentation](https://docs.unrealengine.com/en-US/Engine/UMG/index.html).</span></span> 

## <a name="create-a-new-widget"></a><span data-ttu-id="bc1b2-109">建立新的小工具</span><span class="sxs-lookup"><span data-stu-id="bc1b2-109">Create a new widget</span></span>

- <span data-ttu-id="bc1b2-110">建立 Widget 藍圖來配置遊戲的 UI：</span><span class="sxs-lookup"><span data-stu-id="bc1b2-110">Create a Widget Blueprint to lay out the game’s UI:</span></span>

![從 [Unreal] 功能表新增 widget 藍圖的螢幕擷取畫面](images/unreal-umg-img-01.png)

- <span data-ttu-id="bc1b2-112">開啟新的藍圖，然後將元件從 [元件] 新增至畫布。</span><span class="sxs-lookup"><span data-stu-id="bc1b2-112">Open the new blueprint and add components from the Palette to the canvas.</span></span>  <span data-ttu-id="bc1b2-113">在此情況下，我們已從 [輸入] 區段新增兩個文字方塊元件：</span><span class="sxs-lookup"><span data-stu-id="bc1b2-113">In this case, we've added two Text Box components from the “Input” section:</span></span>

![醒目提示和展開文字 widget 元件之階層視窗的螢幕擷取畫面](images/unreal-umg-img-02.png)

- <span data-ttu-id="bc1b2-115">在 [階層] 或 [設計工具] 視窗中選取 widget，並修改 [詳細資料] 面板中的參數。</span><span class="sxs-lookup"><span data-stu-id="bc1b2-115">Select a widget in the Hierarchy or Designer window and modify parameters in the details panel.</span></span>  <span data-ttu-id="bc1b2-116">在此情況下，我們新增了一些預設的「提示文字」，以及當您將滑鼠停留在文字方塊上時所顯示的淡色色彩。</span><span class="sxs-lookup"><span data-stu-id="bc1b2-116">In this case, we’ve added some default “Hint Text” and a tint color that appears when you hover over the text box.</span></span>  <span data-ttu-id="bc1b2-117">當您進行互動時，文字方塊將會顯示 HoloLens 上的虛擬鍵盤：</span><span class="sxs-lookup"><span data-stu-id="bc1b2-117">A text box will pop up a virtual keyboard on HoloLens when it's interacted with:</span></span>

![階層視窗中已修改之參數的螢幕擷取畫面](images/unreal-umg-img-03.png)

- <span data-ttu-id="bc1b2-119">您也可以在 [詳細資料] 面板中訂閱事件：</span><span class="sxs-lookup"><span data-stu-id="bc1b2-119">Events can also be subscribed to in the details panel:</span></span>

![詳細資料面板中事件的螢幕擷取畫面](images/unreal-umg-img-04.png)

## <a name="add-a-widget-to-world-space"></a><span data-ttu-id="bc1b2-121">將 Widget 新增至世界空間</span><span class="sxs-lookup"><span data-stu-id="bc1b2-121">Add a Widget to World Space</span></span>

- <span data-ttu-id="bc1b2-122">建立新的動作專案、新增 Widget 元件，並將動作專案加入場景中：</span><span class="sxs-lookup"><span data-stu-id="bc1b2-122">Create a new Actor, add a Widget component, and add the actor to the scene:</span></span>

![已附加 widget 之執行者的螢幕擷取畫面](images/unreal-umg-img-05.png)

- <span data-ttu-id="bc1b2-124">在 Widget 的詳細資料面板中，將 **Widget 類別** 設定為稍早建立的 widget 藍圖：</span><span class="sxs-lookup"><span data-stu-id="bc1b2-124">In the details panel for the Widget, set the **Widget Class** to the Widget Blueprint created earlier:</span></span>

![具有 widget 類別集之 [藍圖詳細資料] 面板的螢幕擷取畫面](images/unreal-umg-img-06.png)

- <span data-ttu-id="bc1b2-126">若為文字小工具，請確定未核取 [ **接收硬體輸入** ]，因此我們只會從虛擬鍵盤更新其文字：</span><span class="sxs-lookup"><span data-stu-id="bc1b2-126">For a text Widget, ensure **Receive Hardware Input** is unchecked so we only update its text from the virtual keyboard:</span></span>

![未核取 [接收硬體輸入] 的 [互動] 區段螢幕擷取畫面](images/unreal-umg-img-07.png)

## <a name="widget-interaction"></a><span data-ttu-id="bc1b2-128">Widget 互動</span><span class="sxs-lookup"><span data-stu-id="bc1b2-128">Widget Interaction</span></span>

<span data-ttu-id="bc1b2-129">UMG 小工具通常會從滑鼠接收輸入。</span><span class="sxs-lookup"><span data-stu-id="bc1b2-129">UMG Widgets typically receive input from a mouse.</span></span>  <span data-ttu-id="bc1b2-130">在 HoloLens 或 VR 上，我們需要模擬具有 Widget 互動元件的滑鼠，才能取得相同的事件。</span><span class="sxs-lookup"><span data-stu-id="bc1b2-130">On HoloLens or VR, we need to simulate a mouse with a Widget Interaction component to get the same events.</span></span>

- <span data-ttu-id="bc1b2-131">建立新的動作專案、新增 **Widget 互動** 元件，並將動作專案加入場景中：</span><span class="sxs-lookup"><span data-stu-id="bc1b2-131">Create a new Actor, add a **Widget Interaction** component, and add the actor to your scene:</span></span>

![反白顯示 widget 互動元件的新動作專案螢幕擷取畫面](images/unreal-umg-img-08.png)

- <span data-ttu-id="bc1b2-133">在 Widget 互動元件的詳細資料面板中：</span><span class="sxs-lookup"><span data-stu-id="bc1b2-133">In the details panel for the Widget Interaction component:</span></span>
    - <span data-ttu-id="bc1b2-134">將互動距離設定為您想要的距離值</span><span class="sxs-lookup"><span data-stu-id="bc1b2-134">Set the interaction distance to the distance value you want</span></span>
    - <span data-ttu-id="bc1b2-135">將 **互動來源** 設定為 **自訂**</span><span class="sxs-lookup"><span data-stu-id="bc1b2-135">Set the **Interaction Source** to **custom**</span></span>
    - <span data-ttu-id="bc1b2-136">若為開發，請將 **Show Debug** 設為 **true**：</span><span class="sxs-lookup"><span data-stu-id="bc1b2-136">For development, set **Show Debug** to **true**:</span></span>

![Widget 互動和偵測元件屬性的螢幕擷取畫面](images/unreal-umg-img-09.png)

<span data-ttu-id="bc1b2-138">互動來源的預設值是 "World"，這應該會根據 Widget 互動元件的世界位置傳送 raycasts。</span><span class="sxs-lookup"><span data-stu-id="bc1b2-138">The default for Interaction Source is “World”, which should send raycasts based on the world position of the Widget Interaction component.</span></span> <span data-ttu-id="bc1b2-139">在 AR 和 VR 中，就不是這樣。</span><span class="sxs-lookup"><span data-stu-id="bc1b2-139">In AR and VR, that's not the case.</span></span>  <span data-ttu-id="bc1b2-140">若要檢查 widget 互動元件是否符合您的預期，請務必啟用 [顯示偵錯工具] 並將暫留淡色新增至 widget。</span><span class="sxs-lookup"><span data-stu-id="bc1b2-140">Enabling “Show Debug” and adding a hover tint to widgets is important to check the widget interaction component is doing what you expect.</span></span>  <span data-ttu-id="bc1b2-141">因應措施是使用自訂來源，並從手光線的事件圖形中設定 raycast。</span><span class="sxs-lookup"><span data-stu-id="bc1b2-141">The workaround is to use a custom source and set the raycast in the event graph from the hand ray.</span></span>  

<span data-ttu-id="bc1b2-142">在這裡，我們會從事件滴答進行呼叫：</span><span class="sxs-lookup"><span data-stu-id="bc1b2-142">Here we're calling this from Event Tick:</span></span>

![事件滴答的藍圖](images/unreal-umg-img-10.png)

<span data-ttu-id="bc1b2-144">然後，將虛擬滑鼠指標事件新增至 widget 互動元件，以回應 HoloLens 輸入。</span><span class="sxs-lookup"><span data-stu-id="bc1b2-144">Then add virtual mouse pointer events to the widget interaction component reacting to HoloLens input.</span></span>  <span data-ttu-id="bc1b2-145">在此情況下，當手 grasped 時，傳送左滑鼠按下事件，以及在未 grasped 的情況下，將滑鼠左鍵釋出事件：</span><span class="sxs-lookup"><span data-stu-id="bc1b2-145">In this case, send a Left Mouse press event when the hand is grasped, and a Left Mouse release event when not grasped:</span></span>

![已新增虛擬滑鼠指標事件的藍圖](images/unreal-umg-img-13.png)

<span data-ttu-id="bc1b2-147">現在，當您將應用程式部署至 HoloLens 2 時，您會看到從右手邊延伸的手光線。</span><span class="sxs-lookup"><span data-stu-id="bc1b2-147">Now, when you deploy the app to the HoloLens 2, you’ll see a hand ray extending from your right hand.</span></span> <span data-ttu-id="bc1b2-148">如果您將它導向其中一個可編輯的文字方塊和點擊，系統鍵盤將會出現在您面前，並可讓您輸入文字。</span><span class="sxs-lookup"><span data-stu-id="bc1b2-148">If you direct it at one of the editable text boxes and air tap, the system keyboard will appear in front of you and allow you to enter text.</span></span> 
 
> [!NOTE]
> <span data-ttu-id="bc1b2-149">HoloLens 系統鍵盤需要 Unreal Engine 4.26 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="bc1b2-149">The HoloLens system keyboard requires Unreal Engine 4.26 or later.</span></span> <span data-ttu-id="bc1b2-150">此外，只有當應用程式在裝置上執行時，才會在您的應用程式從 Unreal 編輯器串流到耳機時，不會出現鍵盤。</span><span class="sxs-lookup"><span data-stu-id="bc1b2-150">Additionally, the keyboard will not appear when your app is being streamed from the Unreal editor to the headset, only when the app is running on device.</span></span>

## <a name="see-also"></a><span data-ttu-id="bc1b2-151">另請參閱：</span><span class="sxs-lookup"><span data-stu-id="bc1b2-151">See Also:</span></span>
* [<span data-ttu-id="bc1b2-152">Unreal 的 UMG 檔</span><span class="sxs-lookup"><span data-stu-id="bc1b2-152">Unreal's UMG documentation</span></span>](https://docs.unrealengine.com/Engine/UMG/index.html)
* [<span data-ttu-id="bc1b2-153">Unreal 的 UMG 教學課程</span><span class="sxs-lookup"><span data-stu-id="bc1b2-153">Unreal's UMG tutorials</span></span>](https://docs.unrealengine.com/Programming/Tutorials/UMG/index.html)
