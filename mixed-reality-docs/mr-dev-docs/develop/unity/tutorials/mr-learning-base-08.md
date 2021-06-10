---
title: 使用眼球追蹤
description: 本課程說明如何在混合實境應用程式中透過混合實境工具組 (MRTK) 來使用眼球追蹤。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens, MRTK, 混合實境工具組, UWP, 眼球追蹤
ms.localizationpriority: high
ms.openlocfilehash: a5b93b9e66ffb1e4e9f60251cdc146f48005ae8b
ms.sourcegitcommit: 4a6c26615d52776bdc4faab70391592092a471fc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2021
ms.locfileid: "110713744"
---
# <a name="8-using-eye-tracking"></a><span data-ttu-id="1e5bc-104">8.使用眼球追蹤</span><span class="sxs-lookup"><span data-stu-id="1e5bc-104">8. Using eye-tracking</span></span>

<span data-ttu-id="1e5bc-105">在本教學課程中，您將了解如何啟用 HoloLens 2 的眼球追蹤，並將眼球追蹤新增至物件，以在使用者查看物件時觸發動作。</span><span class="sxs-lookup"><span data-stu-id="1e5bc-105">In this tutorial, you will learn how to enable eye-tracking for HoloLens 2 and add eye-tracking to objects to trigger actions when the user looks at the objects.</span></span>

> [!NOTE]
> <span data-ttu-id="1e5bc-106">如果您也要將此專案部署到 HoloLens (第 1 代)，請注意，只有 HoloLens 2 支援眼球追蹤。</span><span class="sxs-lookup"><span data-stu-id="1e5bc-106">If you are also deploying this project to HoloLens (1st generation), note that eye-tracking is only supported on HoloLens 2.</span></span>

## <a name="objectives"></a><span data-ttu-id="1e5bc-107">目標</span><span class="sxs-lookup"><span data-stu-id="1e5bc-107">Objectives</span></span>

* <span data-ttu-id="1e5bc-108">了解如何啟用 HoleLens 2 的眼球追蹤</span><span class="sxs-lookup"><span data-stu-id="1e5bc-108">Learn how to enable eye-tracking for HoleLens 2</span></span>
* <span data-ttu-id="1e5bc-109">了解如何使用眼球追蹤來觸發動作</span><span class="sxs-lookup"><span data-stu-id="1e5bc-109">Learn how to use eye-tracking to trigger action</span></span>

## <a name="ensuring-the-eye-gaze-input-capability-is-enabled"></a><span data-ttu-id="1e5bc-110">確保已啟用「眼球注視輸入」功能</span><span class="sxs-lookup"><span data-stu-id="1e5bc-110">Ensuring the Eye Gaze Input capability is enabled</span></span>

<span data-ttu-id="1e5bc-111">在 Unity 功能表中，選取 [混合式事實 > 工具組] > 公用程式 > **設定 Project FOR MRTK** 以開啟 [ **MRTK 專案** 設定程式] 視窗，然後在 [ **UWP 功能** ] 區段中，確認 **啟用眼睛的輸入功能** 呈現灰色：</span><span class="sxs-lookup"><span data-stu-id="1e5bc-111">In the Unity menu, select Mixed Reality > Toolkit > Utilities > **Configure Project for MRTK** to open the **MRTK Project Configurator** window, then in the **UWP Capabilities** section, verify that **Enable Eye Gaze Input Capability** is greyed out:</span></span>

![Unity [MRTK 專案設定程式] 視窗](images/mr-learning-base/base-08-section1-step1-1.png)

> [!NOTE]
> <span data-ttu-id="1e5bc-113">當您在本教學課程系列開頭設定 Unity 時，「注視輸入」功能應該在[套用 MRTK 專案設定程式設定](mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk)指示期間啟用。</span><span class="sxs-lookup"><span data-stu-id="1e5bc-113">The Gaze Input capability should have been enabled during the [Apply the MRTK Project Configurator settings](mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk) instructions when you configured the Unity project at the beginning of this tutorial series.</span></span> <span data-ttu-id="1e5bc-114">不過如果未啟用，請確定您立即啟用。</span><span class="sxs-lookup"><span data-stu-id="1e5bc-114">However, if it is not enabled, make sure you enable it now.</span></span>

## <a name="enabling-eye-based-gaze-in-the-gaze-provider"></a><span data-ttu-id="1e5bc-115">在注視提供者中啟用眼球型追蹤</span><span class="sxs-lookup"><span data-stu-id="1e5bc-115">Enabling eye based gaze in the gaze provider</span></span>

<span data-ttu-id="1e5bc-116">在 [階層] 視窗中，選取 **MixedRealityToolkit** 物件，然後在 [偵測器] 視窗中，選取 [MixedRealityToolkit] > [輸入] 索引標籤，並採取下列步驟：</span><span class="sxs-lookup"><span data-stu-id="1e5bc-116">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, select the MixedRealityToolkit > **Input** tab and take the following steps:</span></span>

* <span data-ttu-id="1e5bc-117">複製 **DefaultHoloLens2InputSystemProfile** 並為其指定適當的名稱，例如 _GettingStarted_HoloLens2InputSystemProfile_</span><span class="sxs-lookup"><span data-stu-id="1e5bc-117">Clone the **DefaultHoloLens2InputSystemProfile** and give it a suitable name, for example, _GettingStarted_HoloLens2InputSystemProfile_</span></span>
* <span data-ttu-id="1e5bc-118">展開 [指標] 區段</span><span class="sxs-lookup"><span data-stu-id="1e5bc-118">Expand the **Pointers** section</span></span>
* <span data-ttu-id="1e5bc-119">複製 **DefaultMixedRealityPointerProfile** 並為其指定適當的名稱，例如 _GettingStarted_MixedRealityPointerProfile_</span><span class="sxs-lookup"><span data-stu-id="1e5bc-119">Clone the **DefaultMixedRealityPointerProfile** and give it a suitable name, for example, _GettingStarted_MixedRealityPointerProfile_</span></span>
* <span data-ttu-id="1e5bc-120">找出 [注視設定] 區段，然後勾選 [已啟用眼球追蹤] 核取方塊</span><span class="sxs-lookup"><span data-stu-id="1e5bc-120">Locate the **Gaze Settings** section and check the **Is Eye Tracking Enabled** checkbox</span></span>

![已套用新建立設定檔並已啟用眼球追蹤的 Unity MixedRealityToolkit 元件](images/mr-learning-base/base-08-section2-step1-1.png)

> [!TIP]
> <span data-ttu-id="1e5bc-122">如需有關如何複製 MRTK 設定檔的提示，您可以參閱[設定 MRTK 設定檔](mr-learning-base-03.md)的指示。</span><span class="sxs-lookup"><span data-stu-id="1e5bc-122">For a reminder on how to clone MRTK profiles, you can refer to the [Configuring the MRTK profiles](mr-learning-base-03.md) instructions.</span></span>

## <a name="enabling-simulated-eye-tracking-for-the-unity-editor"></a><span data-ttu-id="1e5bc-123">啟用 Unity 編輯器的模擬眼球追蹤</span><span class="sxs-lookup"><span data-stu-id="1e5bc-123">Enabling simulated eye-tracking for the Unity editor</span></span>

<span data-ttu-id="1e5bc-124">在 [階層] 視窗中，選取 **MixedRealityToolkit** 物件，在 [偵測器] 視窗中，瀏覽至 [輸入] 索引標籤，然後：</span><span class="sxs-lookup"><span data-stu-id="1e5bc-124">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, navigate to the **Input** tab, then:</span></span>

* <span data-ttu-id="1e5bc-125">展開 [輸入資料提供者]  >  [輸入模擬服務] 區段</span><span class="sxs-lookup"><span data-stu-id="1e5bc-125">Expand the **Input Data Providers** > **Input Simulation Service** section</span></span>
* <span data-ttu-id="1e5bc-126">複製 **DefaultMixedRealityInputSimulationProfile** 並為其指定適當的名稱，例如 _GettingStarted_MixedRealityInputSimulationProfile_</span><span class="sxs-lookup"><span data-stu-id="1e5bc-126">Clone the **DefaultMixedRealityInputSimulationProfile** and give it a suitable name, for example, _GettingStarted_MixedRealityInputSimulationProfile_</span></span>
* <span data-ttu-id="1e5bc-127">找出 **眼睛的模擬** ，並將 **預設眼睛的眼睛模擬模式** 設定為 **相機轉寄軸**</span><span class="sxs-lookup"><span data-stu-id="1e5bc-127">Locate **Eye Gaze Simulation** and set the **Default Eye Gaze Simulation Mode** to **Camera Forward Axis**</span></span>

![已選取 TextMeshPro 物件的 Unity](images/mr-learning-base/base-08-section3-step1-1.png)

## <a name="adding-eye-tracking-to-objects"></a><span data-ttu-id="1e5bc-129">將眼球追蹤新增至物件</span><span class="sxs-lookup"><span data-stu-id="1e5bc-129">Adding eye-tracking to objects</span></span>

<span data-ttu-id="1e5bc-130">在 [階層] 視窗中，展開 [ **RoverExplorer**]  >  **按鈕**，然後選取三個子按鈕物件：</span><span class="sxs-lookup"><span data-stu-id="1e5bc-130">In the Hierarchy window, expand the **RoverExplorer** > **Buttons**, then select all three of the child button objects:</span></span>

![已選取按鈕物件的 Unity](images/mr-learning-base/base-08-section4-step1-1.png)

<span data-ttu-id="1e5bc-132">當所有三個按鈕物件仍為選取狀態時，在 [偵測器] 視窗中，使用 [ **新增元件** ] 按鈕將 **EyeTrackingTarget** 元件新增至所有選取的物件：</span><span class="sxs-lookup"><span data-stu-id="1e5bc-132">With all three Button objects still selected, in the Inspector window use the **Add Component** button to add the **EyeTrackingTarget** component to all the selected objects:</span></span>

![已選取 TextMeshPro 物件並已新增元件的 Unity](images/mr-learning-base/base-08-section4-step1-2.png)

<span data-ttu-id="1e5bc-134">在 [階層] 視窗中，展開 [ **RoverExplorer**  >  **按鈕**  >  **提示**  >  **SeeItSayItLabel**  >  **TextMeshPro**</span><span class="sxs-lookup"><span data-stu-id="1e5bc-134">In the Hierarchy window, expand **RoverExplorer** > **Buttons** > **Hints** > **SeeItSayItLabel** > **TextMeshPro**</span></span>

<span data-ttu-id="1e5bc-135">然後，在 [階層] 視窗中選取 [ **提示** ] 按鈕物件，並設定 **EyeTrackingTarget** 元件，如下所示：</span><span class="sxs-lookup"><span data-stu-id="1e5bc-135">Then in the Hierarchy window, select the **Hints** button object , and configure the **EyeTrackingTarget** component as follows:</span></span>

* <span data-ttu-id="1e5bc-136">在 **On Look At Start ()** 事件區段中</span><span class="sxs-lookup"><span data-stu-id="1e5bc-136">In the **On Look At Start ()** event section</span></span>
  * <span data-ttu-id="1e5bc-137">按一下小型 **+** 圖示，以新增另一個事件</span><span class="sxs-lookup"><span data-stu-id="1e5bc-137">Click the small **+** icon to add another event</span></span>
  * <span data-ttu-id="1e5bc-138">將  **TextMeshPro** 物件從 [ **提示** ] 按鈕指派給 [ **無 (物件)** ] 欄位</span><span class="sxs-lookup"><span data-stu-id="1e5bc-138">Assign the  **TextMeshPro** object from the **Hints** button to the **None (Object)** field</span></span>
  * <span data-ttu-id="1e5bc-139">從 [沒有函式] 下拉式清單中，選取 [TextMeshPro]  >  [float fontSize] 以在觸發事件時更新此屬性值</span><span class="sxs-lookup"><span data-stu-id="1e5bc-139">From the **No Function** dropdown, select **TextMeshPro** > **float fontSize** to update this property value when the event is triggered</span></span>
  * <span data-ttu-id="1e5bc-140">將引數設定為 **0.06**，以將目前的字型大小增加 50% 成為 0.04</span><span class="sxs-lookup"><span data-stu-id="1e5bc-140">Set the argument to **0.06** to increase the current font size of 0.04 by 50%</span></span>
* <span data-ttu-id="1e5bc-141">在 **On Look Away ()** 事件區段中</span><span class="sxs-lookup"><span data-stu-id="1e5bc-141">In the **On Look Away ()** event section</span></span>
  * <span data-ttu-id="1e5bc-142">按一下小型 **+** 圖示，以新增另一個事件</span><span class="sxs-lookup"><span data-stu-id="1e5bc-142">Click the small **+** icon to add another event</span></span>
  * <span data-ttu-id="1e5bc-143">將  **TextMeshPro** 物件從 [ **提示** ] 按鈕指派給 [ **無 (物件)** ] 欄位</span><span class="sxs-lookup"><span data-stu-id="1e5bc-143">Assign the  **TextMeshPro** object from the **Hints** button to the **None (Object)** field</span></span>
  * <span data-ttu-id="1e5bc-144">從 [沒有函式] 下拉式清單中，選取 [TextMeshPro]  >  [float fontSize] 以在觸發事件時更新此屬性值</span><span class="sxs-lookup"><span data-stu-id="1e5bc-144">From the **No Function** dropdown, select **TextMeshPro** > **float fontSize** to update this property value when the event is triggered</span></span>
  * <span data-ttu-id="1e5bc-145">將引數設定為 **0.04**，以將字型大小重設回 0.04</span><span class="sxs-lookup"><span data-stu-id="1e5bc-145">Set the argument to **0.04** to reset the font size back to 0.04</span></span>

![已選取提示 TextMeshPro 物件並已設定 EyeTrackingTarget 元件的 Unity](images/mr-learning-base/base-08-section4-step1-3.png)

<span data-ttu-id="1e5bc-147">針對 [**分解**] 和 [**重設**] 按鈕物件 **重複** 此步驟，以設定其他按鈕的眼睛追蹤。</span><span class="sxs-lookup"><span data-stu-id="1e5bc-147">**Repeat** this step for **Explode** and **Reset** button object to configure eye tracking for remaining buttons.</span></span>

<span data-ttu-id="1e5bc-148">如果您現在進入遊戲模式，然後在移動滑鼠時按住滑鼠右鍵，然後再移動滑鼠，直到看看看看看看它的其中一個按鈕時，您會看到文字字型大小增加50%，並在離開時重設回原始大小：</span><span class="sxs-lookup"><span data-stu-id="1e5bc-148">If you now enter Game mode and then press-and-hold the right mouse button while moving your mouse until the gaze hit's one of the buttons, you will see the text font size increase by 50% and reset back to its original size when looking away:</span></span>

![具有注視點擊眼球追蹤目標 [分解] 按鈕標籤的 Unity 播放模式分割檢視](images/mr-learning-base/base-08-section4-step1-4.png)

## <a name="congratulations"></a><span data-ttu-id="1e5bc-150">恭喜！</span><span class="sxs-lookup"><span data-stu-id="1e5bc-150">Congratulations</span></span>

<span data-ttu-id="1e5bc-151">在本教學課程中，您將了解如何啟用 HoloLens 2 的眼球追蹤，以及如何將眼球追蹤新增至物件，以在使用者查看物件時觸發動作。</span><span class="sxs-lookup"><span data-stu-id="1e5bc-151">In this tutorial, you learned how to enable eye-tracking for HoloLens 2 and how to add eye-tracking to objects to trigger actions when the user looks at the objects.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="1e5bc-152">下一個教學課程：9.使用語音命令</span><span class="sxs-lookup"><span data-stu-id="1e5bc-152">Next Tutorial: 9. Using speech commands</span></span>](mr-learning-base-09.md)
