---
title: 使用語音命令
description: 本課程說明如何在混合實境應用程式中透過混合實境工具組 (MRTK) 來設定、建立及使用語音命令。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens, MRTK, 混合實境工具組, UWP, 語音命令, 語音輸入
ms.localizationpriority: high
ms.openlocfilehash: 3aea23d5a259e555f47ca9ea41d77f345c977aeb
ms.sourcegitcommit: 4fb961beeebd158e2f65b7c714c5e471454400a3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/30/2021
ms.locfileid: "105982927"
---
# <a name="9-using-speech-commands"></a><span data-ttu-id="a2946-104">9.使用語音命令</span><span class="sxs-lookup"><span data-stu-id="a2946-104">9. Using speech commands</span></span>

<span data-ttu-id="a2946-105">在本教學課程中，您將了解如何建立語音命令，以及如何全域性地控制這些命令。</span><span class="sxs-lookup"><span data-stu-id="a2946-105">In this tutorial, you will learn how to create speech commands and how to control them globally.</span></span> <span data-ttu-id="a2946-106">您也將了解如何控制局部語音命令，該命令會要求使用者看著控制語音命令的物件。</span><span class="sxs-lookup"><span data-stu-id="a2946-106">You will also learn how to control local speech commands that require the user to look at the object that controls the speech command.</span></span>

## <a name="objectives"></a><span data-ttu-id="a2946-107">目標</span><span class="sxs-lookup"><span data-stu-id="a2946-107">Objectives</span></span>

* <span data-ttu-id="a2946-108">了解如何建立語音命令</span><span class="sxs-lookup"><span data-stu-id="a2946-108">Learn how to create speech commands</span></span>
* <span data-ttu-id="a2946-109">了解如何全域性和局部性地控制語音命令</span><span class="sxs-lookup"><span data-stu-id="a2946-109">Learn how to control speech commands globally and locally</span></span>

[!INCLUDE[](includes/ensuring-microphone-capabality.md)]

## <a name="creating-speech-commands"></a><span data-ttu-id="a2946-110">建立語音命令</span><span class="sxs-lookup"><span data-stu-id="a2946-110">Creating speech commands</span></span>

<span data-ttu-id="a2946-111">在 [階層] 視窗中，選取 **MixedRealityToolkit** 物件，然後在 [偵測器] 視窗中，選取 [MixedRealityToolkit] > [輸入] 索引標籤，並採取下列步驟：</span><span class="sxs-lookup"><span data-stu-id="a2946-111">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, select the MixedRealityToolkit > **Input** tab and take the following steps:</span></span>

* <span data-ttu-id="a2946-112">展開 [語音] 區段</span><span class="sxs-lookup"><span data-stu-id="a2946-112">Expand the **Speech** section</span></span>
* <span data-ttu-id="a2946-113">複製 **DefaultMixedRealitySpeechCommandsProfile** 並為其指定適當的名稱，例如 _GettingStarted_MixedRealitySpeechCommandsProfile_</span><span class="sxs-lookup"><span data-stu-id="a2946-113">Clone the **DefaultMixedRealitySpeechCommandsProfile** and give it a suitable name, for example, _GettingStarted_MixedRealitySpeechCommandsProfile_</span></span>
* <span data-ttu-id="a2946-114">確認 [啟動行為] 已設定為 [自動啟動]</span><span class="sxs-lookup"><span data-stu-id="a2946-114">Verify that **Start Behaviour** is set to **Auto Start**</span></span>

![建立語音命令](images/mr-learning-base/base-09-section2-step1-1.png)

> [!TIP]
> <span data-ttu-id="a2946-116">如需有關如何複製 MRTK 設定檔的提示，您可以參閱[設定 MRTK 設定檔](mr-learning-base-03.md)的指示。</span><span class="sxs-lookup"><span data-stu-id="a2946-116">For a reminder on how to clone MRTK profiles, you can refer to the [Configuring the MRTK profiles](mr-learning-base-03.md) instructions.</span></span>

<span data-ttu-id="a2946-117">在 [語音] > [語音命令] 區段中，按四次 [+ 新增語音命令] 按鈕，將四個新的語音命令新增至現有語音命令的清單中，然後在 [關鍵字] 欄位中輸入下列片語：</span><span class="sxs-lookup"><span data-stu-id="a2946-117">In the Speech > **Speech Commands** section, click the **+ Add a New Speech Command** button four times to add four new speech commands to the list of the existing speech commands, then in the **Keyword** fields enter the following phrases:</span></span>

* <span data-ttu-id="a2946-118">啟用指標</span><span class="sxs-lookup"><span data-stu-id="a2946-118">Enable Indicator</span></span>
* <span data-ttu-id="a2946-119">啟用點選放置</span><span class="sxs-lookup"><span data-stu-id="a2946-119">Enable Tap to Place</span></span>
* <span data-ttu-id="a2946-120">啟用界限控制項</span><span class="sxs-lookup"><span data-stu-id="a2946-120">Enable Bounds Control</span></span>
* <span data-ttu-id="a2946-121">停用界限控制項</span><span class="sxs-lookup"><span data-stu-id="a2946-121">Disable Bounds Control</span></span>

![新增語音命令](images/mr-learning-base/base-09-section2-step1-2.png)

> [!TIP]
> <span data-ttu-id="a2946-123">如果您的電腦沒有麥克風，您可以將 KeyCode 指派給語音命令，讓您在按下對應的按鍵時觸發語音命令。</span><span class="sxs-lookup"><span data-stu-id="a2946-123">If your computer does not have a microphone you can assign a KeyCode to the speech commands, which will let you trigger them when the corresponding key is pressed.</span></span>

## <a name="controlling-speech-commands"></a><span data-ttu-id="a2946-124">控制語音命令</span><span class="sxs-lookup"><span data-stu-id="a2946-124">Controlling speech commands</span></span>

<span data-ttu-id="a2946-125">在 [專案] 視窗中，流覽至 [**封裝**  >  **混合現實工具組 Foundation**  >  **SDK**  >  **功能**  >  **UX**  >  **Prefabs**  >  **工具提示**] 資料夾，以找出工具提示 Prefabs：</span><span class="sxs-lookup"><span data-stu-id="a2946-125">In the Project window, navigate to the **Package** > **Mixed Reality Toolkit Foundation** > **SDK** > **Features** > **UX** > **Prefabs** > **ToolTip** folder to locate the tooltip prefabs:</span></span>

![開啟工具提示資料夾](images/mr-learning-base/base-09-section3-step1-1.png)

<span data-ttu-id="a2946-127">在 [階層] 視窗中，以滑鼠右鍵按一下空的位置，然後選取 [建立空物件]，將空的物件新增至您的場景。</span><span class="sxs-lookup"><span data-stu-id="a2946-127">In the Hierarchy window, right-click on an empty spot and select **Create Empty** to add an empty object to your scene.</span></span>

<span data-ttu-id="a2946-128">將物件命名為 **SpeechInputHandler_Global**，然後在 [偵測器] 視窗中，使用 [新增元件] 按鈕來新增 **SpeechInputHandler** 元件並進行下列設定：</span><span class="sxs-lookup"><span data-stu-id="a2946-128">Name the object **SpeechInputHandler_Global**, then in the Inspector window, use the **Add Component** button to add the **SpeechInputHandler** component and configure it as follows:</span></span>

* <span data-ttu-id="a2946-129">**取消核取** [需要對焦] 核取方塊，如此使用者就不需要看著具有 SpeechInputHandler 元件的物件來觸發語音命令</span><span class="sxs-lookup"><span data-stu-id="a2946-129">**Uncheck** the **Is Focus Required** checkbox, so the user is not required to look at the object with the SpeechInputHandler component to trigger the speech command</span></span>
* <span data-ttu-id="a2946-130">從 [專案] 視窗中，將 **SpeechConfirmation Tooltip** Prefab 指派給 [語音確認工具提示 Prefab] 欄位，以在辨識到語音命令時顯示此 Prefab</span><span class="sxs-lookup"><span data-stu-id="a2946-130">From the Project window, assign the **SpeechConfirmation Tooltip** prefab to the **Speech Confirmation Tooltip Prefab** field, to have this prefab appear when a speech command is recognized</span></span>

![設定語音輸入處理常式元件](images/mr-learning-base/base-09-section3-step1-2.png)

<span data-ttu-id="a2946-132">在 SpeechInputHandler 元件上，按三次小型 **+** 圖示，以新增三個關鍵字元素：</span><span class="sxs-lookup"><span data-stu-id="a2946-132">On the SpeechInputHandler component, click the small **+** icon three times to add three keyword elements:</span></span>

![將關鍵字元素新增至語音輸入處理常式](images/mr-learning-base/base-09-section3-step1-3.png)

<span data-ttu-id="a2946-134">展開 **元素 0** 並進行下列設定：</span><span class="sxs-lookup"><span data-stu-id="a2946-134">Expand **Element 0** and configure it as follows:</span></span>

* <span data-ttu-id="a2946-135">在 [關鍵字] 欄位中輸入 **啟用指標**，以參考您在上一節中建立的啟用指標語音命令。</span><span class="sxs-lookup"><span data-stu-id="a2946-135">In the **Keyword** field, enter **Enable Indicator**, to reference the Enable Indicator speech command you created in the previous section</span></span>
* <span data-ttu-id="a2946-136">按一下小型 **+** 圖示，以新增事件</span><span class="sxs-lookup"><span data-stu-id="a2946-136">Click the small **+** icon to add an event</span></span>
* <span data-ttu-id="a2946-137">從 [階層] 視窗中，將 [指標] 物件指派給 [無 (物件)] 欄位</span><span class="sxs-lookup"><span data-stu-id="a2946-137">From the Hierarchy window, assign the **Indicator** object to the **None (Object)** field</span></span>
* <span data-ttu-id="a2946-138">從 [沒有函式] 下拉式清單中，選取 [GameObject] > [SetActive (bool)]，以將此函式設定為觸發事件時所要執行的動作</span><span class="sxs-lookup"><span data-stu-id="a2946-138">From the **No Function** dropdown, select **GameObject** > **SetActive (bool)** to set this function as the action to be executed when the event is triggered</span></span>
* <span data-ttu-id="a2946-139">核取引數核取方塊，讓其呈現 **已核取** 狀態</span><span class="sxs-lookup"><span data-stu-id="a2946-139">Check the argument checkbox, so it is **checked**</span></span>

![設定關鍵字元素 0](images/mr-learning-base/base-09-section3-step1-4.png)

<span data-ttu-id="a2946-141">展開 **元素 1** 並進行下列設定：</span><span class="sxs-lookup"><span data-stu-id="a2946-141">Expand **Element 1** and configure it as follows:</span></span>

* <span data-ttu-id="a2946-142">在 [ **關鍵字** ] 欄位中，輸入 [ **啟用界限控制**]，以參考您在上一節中建立的 [啟用界限控制] 命令。</span><span class="sxs-lookup"><span data-stu-id="a2946-142">In the **Keyword** field, enter **Enable Bounds Control**, to reference the Enable Bounds Control command you created in the previous section</span></span>
* <span data-ttu-id="a2946-143">按一下小型 **+** 圖示，以新增事件</span><span class="sxs-lookup"><span data-stu-id="a2946-143">Click the small **+** icon to add an event</span></span>
* <span data-ttu-id="a2946-144">從 [階層] 視窗中，將 [RoverExplorer] 物件指派給 [無 (物件)] 欄位</span><span class="sxs-lookup"><span data-stu-id="a2946-144">From the Hierarchy window, assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="a2946-145">從 [**沒有** 函式] 下拉式清單中，選取 [ **BoundsControl**  >  **bool enabled** ]，以在觸發事件時更新此屬性值</span><span class="sxs-lookup"><span data-stu-id="a2946-145">From the **No Function** dropdown, select **BoundsControl** > **bool enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="a2946-146">核取引數核取方塊，讓其呈現 **已核取** 狀態</span><span class="sxs-lookup"><span data-stu-id="a2946-146">Check the argument checkbox, so it is **checked**</span></span>
* <span data-ttu-id="a2946-147">按一下小型 **+** 圖示，以新增另一個事件</span><span class="sxs-lookup"><span data-stu-id="a2946-147">Click the small **+** icon to add another event</span></span>
* <span data-ttu-id="a2946-148">從 [階層] 視窗中，將 [RoverExplorer] 物件指派給 [無 (物件)] 欄位</span><span class="sxs-lookup"><span data-stu-id="a2946-148">From the Hierarchy window, assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="a2946-149">從 [沒有函式] 下拉式清單中，選取 [ObjectManipulator] > [bool enabled] 以在觸發事件時更新此屬性值</span><span class="sxs-lookup"><span data-stu-id="a2946-149">From the **No Function** dropdown, select **ObjectManipulator** > **bool enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="a2946-150">核取引數核取方塊，讓其呈現 **已核取** 狀態</span><span class="sxs-lookup"><span data-stu-id="a2946-150">Check the argument checkbox, so it is **checked**</span></span>

![設定關鍵字元素 1](images/mr-learning-base/base-09-section3-step1-5.png)

<span data-ttu-id="a2946-152">展開 **元素 2** 並進行下列設定：</span><span class="sxs-lookup"><span data-stu-id="a2946-152">Expand **Element 2** and configure it as follows:</span></span>

* <span data-ttu-id="a2946-153">在 [ **關鍵字** ] 欄位中，輸入 **停用界限控制項**，以參考您在上一節中建立的停用界限控制命令</span><span class="sxs-lookup"><span data-stu-id="a2946-153">In the **Keyword** field, enter **Disable Bounds Control**, to reference the Disable Bounds Control command you created in the previous section</span></span>
* <span data-ttu-id="a2946-154">按一下小型 **+** 圖示，以新增事件</span><span class="sxs-lookup"><span data-stu-id="a2946-154">Click the small **+** icon to add an event</span></span>
* <span data-ttu-id="a2946-155">從 [階層] 視窗中，將 [RoverExplorer] 物件指派給 [無 (物件)] 欄位</span><span class="sxs-lookup"><span data-stu-id="a2946-155">From the Hierarchy window, assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="a2946-156">從 [**沒有** 函式] 下拉式清單中，選取 [ **BoundsControl**  >  **bool enabled** ]，以在觸發事件時更新此屬性值</span><span class="sxs-lookup"><span data-stu-id="a2946-156">From the **No Function** dropdown, select **BoundsControl** > **bool enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="a2946-157">確認 **未核取** 引數核取方塊</span><span class="sxs-lookup"><span data-stu-id="a2946-157">Verify that the argument checkbox is **unchecked**</span></span>
* <span data-ttu-id="a2946-158">按一下小型 **+** 圖示，以新增另一個事件</span><span class="sxs-lookup"><span data-stu-id="a2946-158">Click the small **+** icon to add another event</span></span>
* <span data-ttu-id="a2946-159">從 [階層] 視窗中，將 [RoverExplorer] 物件指派給 [無 (物件)] 欄位</span><span class="sxs-lookup"><span data-stu-id="a2946-159">From the Hierarchy window, assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="a2946-160">從 [沒有函式] 下拉式清單中，選取 [ObjectManipulator] > [bool enabled] 以在觸發事件時更新此屬性值</span><span class="sxs-lookup"><span data-stu-id="a2946-160">From the **No Function** dropdown, select **ObjectManipulator** > **bool enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="a2946-161">確認 **未核取** 引數核取方塊</span><span class="sxs-lookup"><span data-stu-id="a2946-161">Verify that the argument checkbox is **unchecked**</span></span>

![設定關鍵字元素 2](images/mr-learning-base/base-09-section3-step1-6.png)

<span data-ttu-id="a2946-163">在 [階層] 視窗中選取 [RoverExplorer] > **RoverAssembly** 物件，然後在 [偵測器] 視窗中使用 [新增元件] 按鈕來新增 **SpeechInputHandler** 元件，並進行以下設定：</span><span class="sxs-lookup"><span data-stu-id="a2946-163">In the Hierarchy window, select the RoverExplorer > **RoverAssembly** object, then in the Inspector window, use the **Add Component** button to add the **SpeechInputHandler** component and configure it as follows:</span></span>

* <span data-ttu-id="a2946-164">確認 **已核取** [需要對焦] 核取方塊，如此使用者就必須看著具有 SpeechInputHandler 元件的物件 (也就是 RoverAssembly) 來觸發語音命令</span><span class="sxs-lookup"><span data-stu-id="a2946-164">Verify that the **Is Focus Required** checkbox is **check**, so the user is required to look at the object with the SpeechInputHandler component, i.e., the RoverAssembly, to trigger the speech command</span></span>
* <span data-ttu-id="a2946-165">從 [專案] 視窗中，將 **SpeechConfirmation Tooltip** Prefab 指派給 [語音確認工具提示 Prefab] 欄位，以在辨識到語音命令時顯示此 Prefab</span><span class="sxs-lookup"><span data-stu-id="a2946-165">From the Project window, assign the **SpeechConfirmation Tooltip** prefab to the **Speech Confirmation Tooltip Prefab** field, to have this prefab appear when a speech command is recognized</span></span>

![將語音輸入處理常式新增至 Rover 組件](images/mr-learning-base/base-09-section3-step1-7.png)

<span data-ttu-id="a2946-167">在 SpeechInputHandler 元件上，按一下小型 **+** 圖示以新增關鍵字元素，然後展開新建立的元素，並進行下列設定：</span><span class="sxs-lookup"><span data-stu-id="a2946-167">On the SpeechInputHandler component, click the small **+** icon to add a keyword element, expand the newly created element, then configure it as follows:</span></span>

* <span data-ttu-id="a2946-168">在 [關鍵字] 欄位中輸入 **啟用點選放置**，以參考您在上一節中建立的點選放置命令</span><span class="sxs-lookup"><span data-stu-id="a2946-168">In the **Keyword** field, enter **Enable Tap to Place**, to reference the Enable Tap to Place command you created in the previous section</span></span>
* <span data-ttu-id="a2946-169">按一下小型 **+** 圖示，以新增事件</span><span class="sxs-lookup"><span data-stu-id="a2946-169">Click the small **+** icon to add an event</span></span>
* <span data-ttu-id="a2946-170">從 [階層] 視窗中，將物件本身 (也就是相同的 **RoverAssembly** 物件) 指派給 [無 (物件)] 欄位</span><span class="sxs-lookup"><span data-stu-id="a2946-170">From the Hierarchy window, assign the object itself, i.e., the same **RoverAssembly** object, to the **None (Object)** field</span></span>
* <span data-ttu-id="a2946-171">從 [沒有函式] 下拉式清單中，選取 [TapToPlace] > [bool enabled] 以在觸發事件時更新此屬性值</span><span class="sxs-lookup"><span data-stu-id="a2946-171">From the **No Function** dropdown, select **TapToPlace** > **bool enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="a2946-172">核取引數核取方塊，讓其呈現 **已核取** 狀態</span><span class="sxs-lookup"><span data-stu-id="a2946-172">Check the argument checkbox, so it is **checked**</span></span>

![在 Rover 組件上設定語音輸入處理常式](images/mr-learning-base/base-09-section3-step1-8.png)

## <a name="congratulations"></a><span data-ttu-id="a2946-174">恭喜！</span><span class="sxs-lookup"><span data-stu-id="a2946-174">Congratulations</span></span>

<span data-ttu-id="a2946-175">在本教學課程中，您已了解如何建立語音命令，以及如何全域性地控制這些命令。</span><span class="sxs-lookup"><span data-stu-id="a2946-175">In this tutorial, you learned how to create speech commands and how to control them globally.</span></span> <span data-ttu-id="a2946-176">您也已了解如何控制局部語音命令，該命令會要求使用者看著控制語音命令的物件。</span><span class="sxs-lookup"><span data-stu-id="a2946-176">You also learned how to control local speech commands that require the user to look at the object that controls the speech command.</span></span>

<span data-ttu-id="a2946-177">這同時也會結束[入門教學課程](mr-learning-base-01.md)系列。</span><span class="sxs-lookup"><span data-stu-id="a2946-177">This also concludes the [Getting started tutorials](mr-learning-base-01.md) series.</span></span> <span data-ttu-id="a2946-178">透過這些教學課程，您已成功地使用 MRTK 從頭開始建立完整的混合實境體驗。</span><span class="sxs-lookup"><span data-stu-id="a2946-178">Through these tutorials, you have successfully built a complete mixed reality experience from scratch using the MRTK.</span></span>

<span data-ttu-id="a2946-179">在接下來的兩個教學課程系列：[Azure Spatial Anchors 教學課程](mr-learning-asa-01.md)和[多使用者功能教學課程](mr-learning-sharing-01.md)中，您會先了解如何將 Azure Spatial Anchors 整合到您的專案中，以在現實世界中錨定您建立的 Rover Explorer 體驗。</span><span class="sxs-lookup"><span data-stu-id="a2946-179">In the next two tutorial series, [Azure Spatial Anchors tutorials](mr-learning-asa-01.md) and [Multi-user capabilities tutorials](mr-learning-sharing-01.md), you will first learn how to integrate Azure Spatial Anchors into your project to anchor the Rover Explorer experience you created in the real world.</span></span> <span data-ttu-id="a2946-180">然後，您將了解如何在專案中新增多使用者功能，以即時分享使用者和物件的動作。</span><span class="sxs-lookup"><span data-stu-id="a2946-180">Then, you will learn how to add multi-user capabilities to your project to share user and object movements in real-time.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="a2946-181">下一個開發檢查點</span><span class="sxs-lookup"><span data-stu-id="a2946-181">Next Development Checkpoint</span></span>

<span data-ttu-id="a2946-182">依循我們配置的 Unity 開發檢查點旅程，您的下一個工作將是熟悉混合實境應用程式的核心建置組塊。</span><span class="sxs-lookup"><span data-stu-id="a2946-182">If you're following the Unity development checkpoint journey we've laid out, your next task is to familiarize yourself with core building blocks of Mixed Reality apps.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="a2946-183">基本互動</span><span class="sxs-lookup"><span data-stu-id="a2946-183">Basic interactions</span></span>](../../../out-of-scope/mrtk-101.md)

<span data-ttu-id="a2946-184">您可以隨時回到 [Unity 開發檢查點](../unity-development-overview.md#1-getting-started)。</span><span class="sxs-lookup"><span data-stu-id="a2946-184">You can always go back to the [Unity development checkpoints](../unity-development-overview.md#1-getting-started) at any time.</span></span>