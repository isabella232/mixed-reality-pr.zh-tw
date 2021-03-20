---
title: 入門教學課程 - 3。 設定 MRTK 設定檔
description: 本課程說明如何設定混合實境工具組 (MRTK) 設定檔。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens, MRTK, 混合實境工具組, UWP, 空間感知
ms.localizationpriority: high
ms.openlocfilehash: 0a8beb647516ebcb5bc07cb58d0193e8fe71e9fc
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "101760014"
---
# <a name="3-configuring-the-mrtk-profiles"></a><span data-ttu-id="9e0ea-105">3.設定 MRTK 設定檔</span><span class="sxs-lookup"><span data-stu-id="9e0ea-105">3. Configuring the MRTK profiles</span></span>

## <a name="overview"></a><span data-ttu-id="9e0ea-106">概觀</span><span class="sxs-lookup"><span data-stu-id="9e0ea-106">Overview</span></span>

<span data-ttu-id="9e0ea-107">在本教學課程中，您將了解如何自訂和設定 MRTK 設定檔。</span><span class="sxs-lookup"><span data-stu-id="9e0ea-107">In this tutorial, you will learn how to customize and configure the MRTK profiles.</span></span>

<span data-ttu-id="9e0ea-108"><a href="https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/profiles/profiles.md" target="_blank">MRTK 設定檔</a>是巢狀設定檔的樹狀結構，其構成了 MRTK 系統和功能應如何初始化的組態設定資訊。</span><span class="sxs-lookup"><span data-stu-id="9e0ea-108">The <a href="https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/profiles/profiles.md" target="_blank">MRTK profiles</a> is a tree of nested profiles that make up the configuration information for how the MRTK systems and features should be initialized.</span></span> <span data-ttu-id="9e0ea-109">最上層設定檔 (組態設定檔) 包含每個主要核心系統的巢狀設定檔。</span><span class="sxs-lookup"><span data-stu-id="9e0ea-109">The top-level profile, the Configuration Profile, contains nested profiles for each of the primary core systems.</span></span> <span data-ttu-id="9e0ea-110">每個巢狀設定檔都是設計來設定其對應系統的行為。</span><span class="sxs-lookup"><span data-stu-id="9e0ea-110">Each nested profile is designed to configure the behavior of their corresponding system.</span></span>

<span data-ttu-id="9e0ea-111">此特定範例將示範如何藉由變更空間網格觀察器的設定，來隱藏空間感知網格。</span><span class="sxs-lookup"><span data-stu-id="9e0ea-111">This particular example will show you how to hide the spatial awareness mesh by changing the settings of the Spatial Mesh Observer.</span></span> <span data-ttu-id="9e0ea-112">不過，您也可以遵循這些相同原則，自訂 MRTK 設定檔中的任何設定或值。</span><span class="sxs-lookup"><span data-stu-id="9e0ea-112">However, you may follow these same principles to customize any setting or value in the MRTK profiles.</span></span>

<span data-ttu-id="9e0ea-113">正如您在進行[上一個教學課程](mr-learning-base-02.md#congratulations)的期間將專案部署至 HoloLens 2 時所經歷的體驗，<a href="https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/spatial-awareness/spatial-awareness-getting-started.md" target="_blank">空間感知</a>網格是代表環境幾何的網格所形成的集合。</span><span class="sxs-lookup"><span data-stu-id="9e0ea-113">As you experienced when you deployed your project to your HoloLens 2 during the [previous tutorial](mr-learning-base-02.md#congratulations), the <a href="https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/spatial-awareness/spatial-awareness-getting-started.md" target="_blank">Spatial Awareness</a> mesh is a collection of meshes representing the geometry of the environment.</span></span> <span data-ttu-id="9e0ea-114">一開始，這樣的視覺效果很有用，但我們一般會將此功能關閉，以免遇到開啟此功能時所會遭遇的視覺干擾和額外的效能減損。</span><span class="sxs-lookup"><span data-stu-id="9e0ea-114">It's a helpful visualization to see initially but it's typically turned off to avoid the visual distraction and the additional performance hit of having it on.</span></span>

## <a name="objectives"></a><span data-ttu-id="9e0ea-115">目標</span><span class="sxs-lookup"><span data-stu-id="9e0ea-115">Objectives</span></span>

* <span data-ttu-id="9e0ea-116">了解如何自訂和設定 MRTK 設定檔</span><span class="sxs-lookup"><span data-stu-id="9e0ea-116">Learn how to customize and configure MRTK profiles</span></span>
* <span data-ttu-id="9e0ea-117">隱藏空間感知網格</span><span class="sxs-lookup"><span data-stu-id="9e0ea-117">Hide the spatial awareness mesh</span></span>

## <a name="changing-the-spatial-awareness-display-option"></a><span data-ttu-id="9e0ea-118">變更空間感知顯示選項</span><span class="sxs-lookup"><span data-stu-id="9e0ea-118">Changing the Spatial Awareness Display Option</span></span>

<span data-ttu-id="9e0ea-119">隱藏空間感知網格所需採取的主要步驟如下：</span><span class="sxs-lookup"><span data-stu-id="9e0ea-119">The main steps you will take to hide the spatial awareness mesh are:</span></span>

1. <span data-ttu-id="9e0ea-120">複製預設的組態設定檔</span><span class="sxs-lookup"><span data-stu-id="9e0ea-120">Clone the default Configuration Profile</span></span>
2. <span data-ttu-id="9e0ea-121">啟用空間感知系統</span><span class="sxs-lookup"><span data-stu-id="9e0ea-121">Enable the Spatial Awareness System</span></span>
3. <span data-ttu-id="9e0ea-122">複製預設的空間感知系統設定檔</span><span class="sxs-lookup"><span data-stu-id="9e0ea-122">Clone the default Spatial Awareness System Profile</span></span>
4. <span data-ttu-id="9e0ea-123">複製預設的空間感知網格觀察器設定檔</span><span class="sxs-lookup"><span data-stu-id="9e0ea-123">Clone the default Spatial Awareness Mesh Observer Profile</span></span>
5. <span data-ttu-id="9e0ea-124">變更空間感知網格的顯示</span><span class="sxs-lookup"><span data-stu-id="9e0ea-124">Change the visibility of the spatial awareness mesh</span></span>

> [!NOTE]
> <span data-ttu-id="9e0ea-125">根據預設，您無法編輯 MRTK 設定檔。</span><span class="sxs-lookup"><span data-stu-id="9e0ea-125">By default, the MRTK profiles are not editable.</span></span> <span data-ttu-id="9e0ea-126">這些是預設的設定檔範本，您必須先加以複製，才能進行編輯。</span><span class="sxs-lookup"><span data-stu-id="9e0ea-126">These are default profile templates that you have to clone before they can be edited.</span></span> <span data-ttu-id="9e0ea-127">其中有數個巢狀的設定檔層。</span><span class="sxs-lookup"><span data-stu-id="9e0ea-127">There are several nested layers of profiles.</span></span> <span data-ttu-id="9e0ea-128">因此，在設定一個或多個設定時，通常會複製及編輯數個設定檔。</span><span class="sxs-lookup"><span data-stu-id="9e0ea-128">Therefore, it is common to clone and edit several profiles when configuring one or more settings.</span></span>

### <a name="1-clone-the-default-configuration-profile"></a><span data-ttu-id="9e0ea-129">1.複製預設的組態設定檔</span><span class="sxs-lookup"><span data-stu-id="9e0ea-129">1. Clone the default Configuration Profile</span></span>

> [!NOTE]
> <span data-ttu-id="9e0ea-130">組態設定檔是最上層的設定檔。</span><span class="sxs-lookup"><span data-stu-id="9e0ea-130">The Configuration Profile is the top-level profile.</span></span> <span data-ttu-id="9e0ea-131">因此，若要編輯任何其他設定檔，您必須先複製組態設定檔。</span><span class="sxs-lookup"><span data-stu-id="9e0ea-131">Consequently, to be able to edit any other profiles, you first have to clone the Configuration Profile.</span></span>

<span data-ttu-id="9e0ea-132">在 [階層] 視窗中選取 **MixedRealityToolkit** 物件，然後在 [偵測器] 視窗中，將 **MixedRealityToolkit** 組態設定檔變更為 **DefaultHoloLens2ConfigurationProfile**：</span><span class="sxs-lookup"><span data-stu-id="9e0ea-132">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, change the **MixedRealityToolkit** Configuration Profile to the **DefaultHoloLens2ConfigurationProfile**:</span></span>

![已選取 DefaultHoloLens2ConfigurationProfile 的 Unity MixedRealityToolkit 元件](images/mr-learning-base/base-03-section1-step1-1.png)

<span data-ttu-id="9e0ea-134">在仍選取 **MixedRealityToolkit** 物件的情況下，在 [偵測器] 視窗中按一下 [複製與自訂] 按鈕來開啟 [複製設定檔] 視窗：</span><span class="sxs-lookup"><span data-stu-id="9e0ea-134">With the **MixedRealityToolkit** object still selected, in the Inspector window, click the **Copy & Customize** button to open the Clone Profile window:</span></span>

![Unity MixedRealityToolkit 元件的 [複製與自訂] 按鈕](images/mr-learning-base/base-03-section1-step1-2.png)

<span data-ttu-id="9e0ea-136">在 [複製設定檔] 視窗中，輸入適當的 **設定檔名稱**，例如 _GettingStarted_HoloLens2ConfigurationProfile_，然後按一下 [複製] 按鈕，以建立 **DefaultHololens2ConfigurationProfile** 的可編輯複本：</span><span class="sxs-lookup"><span data-stu-id="9e0ea-136">In the Clone Profile window, enter a suitable **Profile Name**, for example, _GettingStarted_HoloLens2ConfigurationProfile_, then click the **Clone** button to create an editable copy of the **DefaultHololens2ConfigurationProfile**:</span></span>

![Unity MixedRealityToolkit 複製的 [組態設定檔] 快顯視窗](images/mr-learning-base/base-03-section1-step1-3.png)

<span data-ttu-id="9e0ea-138">新建立的組態設定檔現在已指派為您場景的組態設定檔：</span><span class="sxs-lookup"><span data-stu-id="9e0ea-138">The newly created Configuration Profile is now assigned as the Configuration Profile for your scene:</span></span>

![已套用新建立自訂 HoloLens2ConfigurationProfile 的 Unity MixedRealityToolkit 元件](images/mr-learning-base/base-03-section1-step1-4.png)

<span data-ttu-id="9e0ea-140">在 Unity 功能表中，選取 [檔案] > [儲存]，即可儲存場景。</span><span class="sxs-lookup"><span data-stu-id="9e0ea-140">In the Unity menu, select **File** > **Save** to save your scene.</span></span>

> [!TIP]
> <span data-ttu-id="9e0ea-141">請記得在整個教學課程中儲存工作。</span><span class="sxs-lookup"><span data-stu-id="9e0ea-141">Remember to save your work throughout the tutorials.</span></span>

### <a name="2-enable-the-spatial-awareness-system"></a><span data-ttu-id="9e0ea-142">2.啟用空間感知系統</span><span class="sxs-lookup"><span data-stu-id="9e0ea-142">2. Enable the Spatial Awareness System</span></span>

<span data-ttu-id="9e0ea-143">在 [階層] 視窗中選取 **MixedRealityToolkit** 物件，在 [偵測器] 視窗中選取 [空間感知] 索引標籤，然後勾選 [啟用空間感知系統] 核取方塊：</span><span class="sxs-lookup"><span data-stu-id="9e0ea-143">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, select the **Spatial Awareness** tab, and then check the **Enable Spatial Awareness System** checkbox:</span></span>

![已啟用 [空間感知系統] 的 Unity MixedRealityToolkit 元件](images/mr-learning-base/base-03-section1-step2-1.png)

> [!NOTE]
> <span data-ttu-id="9e0ea-145">針對未來的專案，如果您的應用程式不需要回應環境或與其互動，建議您讓空間感知保持關閉狀態，以降低效能成本。</span><span class="sxs-lookup"><span data-stu-id="9e0ea-145">For future projects, if your app doesn't need to respond to or interact with the environment, it's recommended to keep the spatial awareness turned off to reduce performance cost.</span></span>

### <a name="3-clone-the-default-spatial-awareness-system-profile"></a><span data-ttu-id="9e0ea-146">3.複製預設的空間感知系統設定檔</span><span class="sxs-lookup"><span data-stu-id="9e0ea-146">3. Clone the default Spatial Awareness System Profile</span></span>

<span data-ttu-id="9e0ea-147">在 [空間感知] 索引標籤中，按一下 [複製] 按鈕以開啟 [複製設定檔] 視窗：</span><span class="sxs-lookup"><span data-stu-id="9e0ea-147">In the **Spatial Awareness** tab, click the **Clone** button to open the Clone Profile window:</span></span>

![已選取 [空間感知] 索引標籤的 Unity MixedRealityToolkit 元件](images/mr-learning-base/base-03-section1-step3-1.png)

<span data-ttu-id="9e0ea-149">在 [複製設定檔] 視窗中，輸入適當的 **設定檔名稱**，例如 _GettingStarted_MixedRealitySpatialAwarenessSystemProfile_，然後按一下 [複製] 按鈕，以建立 **DefaultMixedRealitySpatialAwarenessSystemProfile** 的可編輯複本：</span><span class="sxs-lookup"><span data-stu-id="9e0ea-149">In the Clone Profile window, enter a suitable **Profile Name**, for example, _GettingStarted_MixedRealitySpatialAwarenessSystemProfile_, then click the **Clone** button to create an editable copy of the **DefaultMixedRealitySpatialAwarenessSystemProfile**:</span></span>

![Unity MixedRealityToolkit 複製的 [空間感知系統設定檔] 快顯視窗](images/mr-learning-base/base-03-section1-step3-2.png)

<span data-ttu-id="9e0ea-151">新建立的空間感知系統設定檔現在會自動指派給您的組態設定檔：</span><span class="sxs-lookup"><span data-stu-id="9e0ea-151">The newly created Spatial Awareness System Profile is now automatically assigned to your Configuration Profile:</span></span>

![已套用新建立自訂 MixedRealitySpatialAwarenessSystemProfile 的 Unity MixedRealityToolkit 元件](images/mr-learning-base/base-03-section1-step3-3.png)

### <a name="4-clone-the-default-spatial-awareness-mesh-observer-profile"></a><span data-ttu-id="9e0ea-153">4.複製預設的空間感知網格觀察器設定檔</span><span class="sxs-lookup"><span data-stu-id="9e0ea-153">4. Clone the default Spatial Awareness Mesh Observer Profile</span></span>

<span data-ttu-id="9e0ea-154">在仍選取 [空間感知] 索引標籤的情況下，展開 [Windows Mixed Reality 空間網格觀察器] 區段，然後按一下 [複製] 按鈕來開啟 [複製設定檔] 視窗：</span><span class="sxs-lookup"><span data-stu-id="9e0ea-154">With the **Spatial Awareness** tab still selected, expand the **Windows Mixed Reality Spatial Mesh Observer** section, then click the **Clone** button to open the Clone Profile window:</span></span>

![已擴充 Windows Mixed Reality [空間網格觀察者] 區段的 Unity MixedRealityToolkit 元件](images/mr-learning-base/base-03-section1-step4-1.png)

<span data-ttu-id="9e0ea-156">在 [複製設定檔] 視窗中，輸入適當的 **設定檔名稱**，例如 _GettingStarted_MixedRealitySpatialAwarenessMeshObserverProfile_，然後按一下 [複製] 按鈕，以建立 **DefaultMixedRealitySpatialAwarenessMeshObserverProfile** 的可編輯複本：</span><span class="sxs-lookup"><span data-stu-id="9e0ea-156">In the Clone Profile window, enter a suitable **Profile Name**, for example, _GettingStarted_MixedRealitySpatialAwarenessMeshObserverProfile_, then click the **Clone** button to create an editable copy of the **DefaultMixedRealitySpatialAwarenessMeshObserverProfile**:</span></span>

![Unity MixedRealityToolkit 複製的 [空間網格觀察者設定檔] 快顯視窗](images/mr-learning-base/base-03-section1-step4-2.png)

<span data-ttu-id="9e0ea-158">新建立的空間感知網格觀察器設定檔現在會自動指派給您的空間感知系統設定檔：</span><span class="sxs-lookup"><span data-stu-id="9e0ea-158">The newly created Spatial Awareness Mesh Observer Profile is now automatically assigned to your Spatial Awareness System Profile:</span></span>

![已套用新建立自訂 MixedRealitySpatialAwarenessMeshObserverProfile 的 Unity MixedRealityToolkit 元件](images/mr-learning-base/base-03-section1-step4-3.png)

### <a name="5-change-the-visibility-of-the-spatial-awareness-mesh"></a><span data-ttu-id="9e0ea-160">5.變更空間感知網格的顯示</span><span class="sxs-lookup"><span data-stu-id="9e0ea-160">5. Change the visibility of the spatial awareness mesh</span></span>

<span data-ttu-id="9e0ea-161">在 [空間網格觀察器設定] 中，將 [顯示選項] 變更為 [遮蔽]，以隱藏仍在運作的空間對應網格：</span><span class="sxs-lookup"><span data-stu-id="9e0ea-161">In the **Spatial Mesh Observer Settings**, change the **Display Option** to **Occlusion** to make the spatial mapping mesh invisible while still functional:</span></span>

![[空間網格觀察者顯示選項] 設定為 [遮蔽] 的 Unity MixedRealityToolkit 元件](images/mr-learning-base/base-03-section1-step5-1.png)

> [!NOTE]
> <span data-ttu-id="9e0ea-163">雖然空間對應網格看不到，但仍存在且正常運作。</span><span class="sxs-lookup"><span data-stu-id="9e0ea-163">Although the spatial mapping mesh is not visible, it is still present and functional.</span></span> <span data-ttu-id="9e0ea-164">例如，空間對應網格後方的任何全像投影 (實體牆後方的全像投影等) 將不會顯示。</span><span class="sxs-lookup"><span data-stu-id="9e0ea-164">For example, any holograms behind the spatial mapping mesh, such as a hologram behind a physical wall, will not be visible.</span></span>

<span data-ttu-id="9e0ea-165">您方才已了解如何修改 MRTK 設定檔中的設定。</span><span class="sxs-lookup"><span data-stu-id="9e0ea-165">You just learned how to modify a setting in the MRTK profile.</span></span> <span data-ttu-id="9e0ea-166">如您所見，為了自訂 MRTK 設定，您必須先建立預設設定檔的複本。</span><span class="sxs-lookup"><span data-stu-id="9e0ea-166">As you can see, to customize the MRTK settings, you first need to create copies of the default profiles.</span></span> <span data-ttu-id="9e0ea-167">由於預設設定檔無法編輯，因此當您想要還原為預設設定時，一律可以參考這些設定。</span><span class="sxs-lookup"><span data-stu-id="9e0ea-167">Because the default profiles are not editable, you will always have them as references if you want to revert to the default settings.</span></span> <span data-ttu-id="9e0ea-168">若要深入了解 MRTK 設定檔及其架構，您可以參閱 [MRTK 文件入口網站](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs)中的 [MRTK 設定檔設定指南](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/configuration/mixed-reality-configuration-guide.md)。</span><span class="sxs-lookup"><span data-stu-id="9e0ea-168">To learn more about MRTK profiles and their architecture, you can refer to the [MRTK profile configuration guide](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/configuration/mixed-reality-configuration-guide.md) in the [MRTK Documentation Portal](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs).</span></span>

## <a name="congratulations"></a><span data-ttu-id="9e0ea-169">恭喜！</span><span class="sxs-lookup"><span data-stu-id="9e0ea-169">Congratulations</span></span>

<span data-ttu-id="9e0ea-170">在本教學課程中，您已了解如何複製、自訂和設定 MRTK 設定檔和設定。</span><span class="sxs-lookup"><span data-stu-id="9e0ea-170">In this tutorial, you learned how to clone, customize, and configure MRTK profiles and settings.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="9e0ea-171">下一個教學課程：4.將物件置放在場景中</span><span class="sxs-lookup"><span data-stu-id="9e0ea-171">Next Tutorial: 4. Positioning objects in the scene</span></span>](mr-learning-base-04.md)
