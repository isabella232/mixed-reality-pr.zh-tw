---
ms.openlocfilehash: 8a7253f4d151911fa0de3e60ccec1712df0956df
ms.sourcegitcommit: 4fb961beeebd158e2f65b7c714c5e471454400a3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/30/2021
ms.locfileid: "105983369"
---
# <a name="unity-20192020--windows-xr-plugin"></a>[<span data-ttu-id="51577-101">Unity 2019/2020 + Windows XR 外掛程式</span><span class="sxs-lookup"><span data-stu-id="51577-101">Unity 2019/2020 + Windows XR Plugin</span></span>](#tab/winxr)

### <a name="1-clone-the-default-configuration-profile"></a><span data-ttu-id="51577-102">1.複製預設的組態設定檔</span><span class="sxs-lookup"><span data-stu-id="51577-102">1. Clone the default Configuration Profile</span></span>

> [!NOTE]
> <span data-ttu-id="51577-103">組態設定檔是最上層的設定檔。</span><span class="sxs-lookup"><span data-stu-id="51577-103">The Configuration Profile is the top-level profile.</span></span> <span data-ttu-id="51577-104">因此，若要編輯任何其他設定檔，您必須先複製組態設定檔。</span><span class="sxs-lookup"><span data-stu-id="51577-104">Consequently, to be able to edit any other profiles, you first have to clone the Configuration Profile.</span></span>

<span data-ttu-id="51577-105">在 [階層] 視窗中，選取 [ **MixedRealityToolkit** ] 物件，然後在 [偵測器] 視窗中，確認 **MixedRealityToolkit** 設定設定檔已設定為 **DefaultXRSDKConfigurationProfile**：</span><span class="sxs-lookup"><span data-stu-id="51577-105">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, verify that the **MixedRealityToolkit** Configuration Profile is set to the **DefaultXRSDKConfigurationProfile**:</span></span>

![已選取 DefaultHoloLens2ConfigurationProfile 的 Unity MixedRealityToolkit 元件](../images/mr-learning-base/base-03-section1-step1-1xrsdk.png)

<span data-ttu-id="51577-107">在仍選取 **MixedRealityToolkit** 物件的情況下，在 [偵測器] 視窗中按一下 [複製與自訂] 按鈕來開啟 [複製設定檔] 視窗：</span><span class="sxs-lookup"><span data-stu-id="51577-107">With the **MixedRealityToolkit** object still selected, in the Inspector window, click the **Copy & Customize** button to open the Clone Profile window:</span></span>

![Unity MixedRealityToolkit 元件的 [複製與自訂] 按鈕](../images/mr-learning-base/base-03-section1-step1-2xrsdk.png)

<span data-ttu-id="51577-109">在 [複製設定檔] 視窗中，輸入適當的 **設定檔名稱**，例如 _GettingStarted_XRSDKConfigurationProfile_，然後按一下 [ **複製** ] 按鈕，以建立 **DefaultXRSDKConfigurationProfile** 的可編輯複本：</span><span class="sxs-lookup"><span data-stu-id="51577-109">In the Clone Profile window, enter a suitable **Profile Name**, for example, _GettingStarted_XRSDKConfigurationProfile_, then click the **Clone** button to create an editable copy of the **DefaultXRSDKConfigurationProfile**:</span></span>

![Unity MixedRealityToolkit 複製的 [組態設定檔] 快顯視窗](../images/mr-learning-base/base-03-section1-step1-3xrsdk.png)

<span data-ttu-id="51577-111">新建立的組態設定檔現在已指派為您場景的組態設定檔：</span><span class="sxs-lookup"><span data-stu-id="51577-111">The newly created Configuration Profile is now assigned as the Configuration Profile for your scene:</span></span>

![已套用新建立自訂 HoloLens2ConfigurationProfile 的 Unity MixedRealityToolkit 元件](../images/mr-learning-base/base-03-section1-step1-4xrsdk.png)

<span data-ttu-id="51577-113">在 Unity 功能表中，選取 [檔案] > [儲存]，即可儲存場景。</span><span class="sxs-lookup"><span data-stu-id="51577-113">In the Unity menu, select **File** > **Save** to save your scene.</span></span>

> [!TIP]
> <span data-ttu-id="51577-114">請記得在整個教學課程中儲存工作。</span><span class="sxs-lookup"><span data-stu-id="51577-114">Remember to save your work throughout the tutorials.</span></span>

### <a name="2-enable-the-spatial-awareness-system"></a><span data-ttu-id="51577-115">2.啟用空間感知系統</span><span class="sxs-lookup"><span data-stu-id="51577-115">2. Enable the Spatial Awareness System</span></span>

<span data-ttu-id="51577-116">在 [階層] 視窗中選取 **MixedRealityToolkit** 物件，在 [偵測器] 視窗中選取 [空間感知] 索引標籤，然後勾選 [啟用空間感知系統] 核取方塊：</span><span class="sxs-lookup"><span data-stu-id="51577-116">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, select the **Spatial Awareness** tab, and then check the **Enable Spatial Awareness System** checkbox:</span></span>

![已啟用 [空間感知系統] 的 Unity MixedRealityToolkit 元件](../images/mr-learning-base/base-03-section1-step2-1xrsdk.png)

> [!NOTE]
> <span data-ttu-id="51577-118">針對未來的專案，如果您的應用程式不需要回應環境或與其互動，建議您讓空間感知保持關閉狀態，以降低效能成本。</span><span class="sxs-lookup"><span data-stu-id="51577-118">For future projects, if your app doesn't need to respond to or interact with the environment, it's recommended to keep the spatial awareness turned off to reduce performance cost.</span></span>

### <a name="3-clone-the-default-spatial-awareness-system-profile"></a><span data-ttu-id="51577-119">3.複製預設的空間感知系統設定檔</span><span class="sxs-lookup"><span data-stu-id="51577-119">3. Clone the default Spatial Awareness System Profile</span></span>

<span data-ttu-id="51577-120">在 [空間感知] 索引標籤中，按一下 [複製] 按鈕以開啟 [複製設定檔] 視窗：</span><span class="sxs-lookup"><span data-stu-id="51577-120">In the **Spatial Awareness** tab, click the **Clone** button to open the Clone Profile window:</span></span>

![已選取 [空間感知] 索引標籤的 Unity MixedRealityToolkit 元件](../images/mr-learning-base/base-03-section1-step3-1xrsdk.png)

<span data-ttu-id="51577-122">在 [複製設定檔] 視窗中，輸入適當的 **設定檔名稱**，例如 _GettingStarted_XRSDKSpatialAwarenessSystemProfile_，然後按一下 [ **複製** ] 按鈕，以建立 **DefaultXRSDKSpatialAwarenessSystemProfile** 的可編輯複本：</span><span class="sxs-lookup"><span data-stu-id="51577-122">In the Clone Profile window, enter a suitable **Profile Name**, for example, _GettingStarted_XRSDKSpatialAwarenessSystemProfile_, then click the **Clone** button to create an editable copy of the **DefaultXRSDKSpatialAwarenessSystemProfile**:</span></span>

![Unity MixedRealityToolkit 複製的 [空間感知系統設定檔] 快顯視窗](../images/mr-learning-base/base-03-section1-step3-2xrsdk.png)

<span data-ttu-id="51577-124">新建立的空間感知系統設定檔現在會自動指派給您的組態設定檔：</span><span class="sxs-lookup"><span data-stu-id="51577-124">The newly created Spatial Awareness System Profile is now automatically assigned to your Configuration Profile:</span></span>

![已套用新建立自訂 MixedRealitySpatialAwarenessSystemProfile 的 Unity MixedRealityToolkit 元件](../images/mr-learning-base/base-03-section1-step3-3xrsdk.png)

### <a name="4-clone-the-default-spatial-awareness-mesh-observer-profile"></a><span data-ttu-id="51577-126">4.複製預設的空間感知網格觀察器設定檔</span><span class="sxs-lookup"><span data-stu-id="51577-126">4. Clone the default Spatial Awareness Mesh Observer Profile</span></span>

<span data-ttu-id="51577-127">在仍選取 [ **空間感知** ] 索引標籤的情況下，展開 [ **XR SDK Windows Mixed Reality 空間網格觀察** 者] 區段，然後按一下 [ **複製** ] 按鈕以開啟 [複製設定檔] 視窗：</span><span class="sxs-lookup"><span data-stu-id="51577-127">With the **Spatial Awareness** tab still selected, expand the **XR SDK Windows Mixed Reality Spatial Mesh Observer** section, then click the **Clone** button to open the Clone Profile window:</span></span>

![已擴充 Windows Mixed Reality [空間網格觀察者] 區段的 Unity MixedRealityToolkit 元件](../images/mr-learning-base/base-03-section1-step4-1xrsdk.png)

<span data-ttu-id="51577-129">在 [複製設定檔] 視窗中，輸入適當的 **設定檔名稱**，例如 _GettingStarted_MixedRealitySpatialAwarenessMeshObserverProfile_，然後按一下 [複製] 按鈕，以建立 **DefaultMixedRealitySpatialAwarenessMeshObserverProfile** 的可編輯複本：</span><span class="sxs-lookup"><span data-stu-id="51577-129">In the Clone Profile window, enter a suitable **Profile Name**, for example, _GettingStarted_MixedRealitySpatialAwarenessMeshObserverProfile_, then click the **Clone** button to create an editable copy of the **DefaultMixedRealitySpatialAwarenessMeshObserverProfile**:</span></span>

![Unity MixedRealityToolkit 複製的 [空間網格觀察者設定檔] 快顯視窗](../images/mr-learning-base/base-03-section1-step4-2xrsdk.png)

<span data-ttu-id="51577-131">新建立的空間感知網格觀察器設定檔現在會自動指派給您的空間感知系統設定檔：</span><span class="sxs-lookup"><span data-stu-id="51577-131">The newly created Spatial Awareness Mesh Observer Profile is now automatically assigned to your Spatial Awareness System Profile:</span></span>

![已套用新建立自訂 MixedRealitySpatialAwarenessMeshObserverProfile 的 Unity MixedRealityToolkit 元件](../images/mr-learning-base/base-03-section1-step4-3xrsdk.png)

### <a name="5-change-the-visibility-of-the-spatial-awareness-mesh"></a><span data-ttu-id="51577-133">5.變更空間感知網格的顯示</span><span class="sxs-lookup"><span data-stu-id="51577-133">5. Change the visibility of the spatial awareness mesh</span></span>

<span data-ttu-id="51577-134">在 [空間網格觀察器設定] 中，將 [顯示選項] 變更為 [遮蔽]，以隱藏仍在運作的空間對應網格：</span><span class="sxs-lookup"><span data-stu-id="51577-134">In the **Spatial Mesh Observer Settings**, change the **Display Option** to **Occlusion** to make the spatial mapping mesh invisible while still functional:</span></span>

![[空間網格觀察者顯示選項] 設定為 [遮蔽] 的 Unity MixedRealityToolkit 元件](../images/mr-learning-base/base-03-section1-step5-1xrsdk.png)

> [!NOTE]
> <span data-ttu-id="51577-136">雖然空間對應網格看不到，但仍存在且正常運作。</span><span class="sxs-lookup"><span data-stu-id="51577-136">Although the spatial mapping mesh is not visible, it is still present and functional.</span></span> <span data-ttu-id="51577-137">例如，空間對應網格後方的任何全像投影 (實體牆後方的全像投影等) 將不會顯示。</span><span class="sxs-lookup"><span data-stu-id="51577-137">For example, any holograms behind the spatial mapping mesh, such as a hologram behind a physical wall, will not be visible.</span></span>

<span data-ttu-id="51577-138">您方才已了解如何修改 MRTK 設定檔中的設定。</span><span class="sxs-lookup"><span data-stu-id="51577-138">You just learned how to modify a setting in the MRTK profile.</span></span> <span data-ttu-id="51577-139">如您所見，為了自訂 MRTK 設定，您必須先建立預設設定檔的複本。</span><span class="sxs-lookup"><span data-stu-id="51577-139">As you can see, to customize the MRTK settings, you first need to create copies of the default profiles.</span></span> <span data-ttu-id="51577-140">由於預設設定檔無法編輯，因此當您想要還原為預設設定時，一律可以參考這些設定。</span><span class="sxs-lookup"><span data-stu-id="51577-140">Because the default profiles are not editable, you will always have them as references if you want to revert to the default settings.</span></span> <span data-ttu-id="51577-141">若要深入了解 MRTK 設定檔及其架構，您可以參閱 [MRTK 文件入口網站](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)中的 [MRTK 設定檔設定指南](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html)。</span><span class="sxs-lookup"><span data-stu-id="51577-141">To learn more about MRTK profiles and their architecture, you can refer to the [MRTK profile configuration guide](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html) in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>


# <a name="legacy-wsa"></a>[<span data-ttu-id="51577-142">舊版 WSA</span><span class="sxs-lookup"><span data-stu-id="51577-142">Legacy WSA</span></span>](#tab/wsa)

### <a name="1-clone-the-default-configuration-profile"></a><span data-ttu-id="51577-143">1.複製預設的組態設定檔</span><span class="sxs-lookup"><span data-stu-id="51577-143">1. Clone the default Configuration Profile</span></span>

> [!NOTE]
> <span data-ttu-id="51577-144">組態設定檔是最上層的設定檔。</span><span class="sxs-lookup"><span data-stu-id="51577-144">The Configuration Profile is the top-level profile.</span></span> <span data-ttu-id="51577-145">因此，若要編輯任何其他設定檔，您必須先複製組態設定檔。</span><span class="sxs-lookup"><span data-stu-id="51577-145">Consequently, to be able to edit any other profiles, you first have to clone the Configuration Profile.</span></span>

<span data-ttu-id="51577-146">在 [階層] 視窗中選取 **MixedRealityToolkit** 物件，然後在 [偵測器] 視窗中，將 **MixedRealityToolkit** 組態設定檔變更為 **DefaultHoloLens2ConfigurationProfile**：</span><span class="sxs-lookup"><span data-stu-id="51577-146">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, change the **MixedRealityToolkit** Configuration Profile to the **DefaultHoloLens2ConfigurationProfile**:</span></span>

![已選取 DefaultHoloLens2ConfigurationProfile 的 Unity MixedRealityToolkit 元件](../images/mr-learning-base/base-03-section1-step1-1.png)

<span data-ttu-id="51577-148">在仍選取 **MixedRealityToolkit** 物件的情況下，在 [偵測器] 視窗中按一下 [複製與自訂] 按鈕來開啟 [複製設定檔] 視窗：</span><span class="sxs-lookup"><span data-stu-id="51577-148">With the **MixedRealityToolkit** object still selected, in the Inspector window, click the **Copy & Customize** button to open the Clone Profile window:</span></span>

![Unity MixedRealityToolkit 元件的 [複製與自訂] 按鈕](../images/mr-learning-base/base-03-section1-step1-2.png)

<span data-ttu-id="51577-150">在 [複製設定檔] 視窗中，輸入適當的 **設定檔名稱**，例如 _GettingStarted_HoloLens2ConfigurationProfile_，然後按一下 [複製] 按鈕，以建立 **DefaultHololens2ConfigurationProfile** 的可編輯複本：</span><span class="sxs-lookup"><span data-stu-id="51577-150">In the Clone Profile window, enter a suitable **Profile Name**, for example, _GettingStarted_HoloLens2ConfigurationProfile_, then click the **Clone** button to create an editable copy of the **DefaultHololens2ConfigurationProfile**:</span></span>

![Unity MixedRealityToolkit 複製的 [組態設定檔] 快顯視窗](../images/mr-learning-base/base-03-section1-step1-3.png)

<span data-ttu-id="51577-152">新建立的組態設定檔現在已指派為您場景的組態設定檔：</span><span class="sxs-lookup"><span data-stu-id="51577-152">The newly created Configuration Profile is now assigned as the Configuration Profile for your scene:</span></span>

![已套用新建立自訂 HoloLens2ConfigurationProfile 的 Unity MixedRealityToolkit 元件](../images/mr-learning-base/base-03-section1-step1-4.png)

<span data-ttu-id="51577-154">在 Unity 功能表中，選取 [檔案] > [儲存]，即可儲存場景。</span><span class="sxs-lookup"><span data-stu-id="51577-154">In the Unity menu, select **File** > **Save** to save your scene.</span></span>

> [!TIP]
> <span data-ttu-id="51577-155">請記得在整個教學課程中儲存工作。</span><span class="sxs-lookup"><span data-stu-id="51577-155">Remember to save your work throughout the tutorials.</span></span>

### <a name="2-enable-the-spatial-awareness-system"></a><span data-ttu-id="51577-156">2.啟用空間感知系統</span><span class="sxs-lookup"><span data-stu-id="51577-156">2. Enable the Spatial Awareness System</span></span>

<span data-ttu-id="51577-157">在 [階層] 視窗中選取 **MixedRealityToolkit** 物件，在 [偵測器] 視窗中選取 [空間感知] 索引標籤，然後勾選 [啟用空間感知系統] 核取方塊：</span><span class="sxs-lookup"><span data-stu-id="51577-157">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, select the **Spatial Awareness** tab, and then check the **Enable Spatial Awareness System** checkbox:</span></span>

![已啟用 [空間感知系統] 的 Unity MixedRealityToolkit 元件](../images/mr-learning-base/base-03-section1-step2-1.png)

> [!NOTE]
> <span data-ttu-id="51577-159">針對未來的專案，如果您的應用程式不需要回應環境或與其互動，建議您讓空間感知保持關閉狀態，以降低效能成本。</span><span class="sxs-lookup"><span data-stu-id="51577-159">For future projects, if your app doesn't need to respond to or interact with the environment, it's recommended to keep the spatial awareness turned off to reduce performance cost.</span></span>

### <a name="3-clone-the-default-spatial-awareness-system-profile"></a><span data-ttu-id="51577-160">3.複製預設的空間感知系統設定檔</span><span class="sxs-lookup"><span data-stu-id="51577-160">3. Clone the default Spatial Awareness System Profile</span></span>

<span data-ttu-id="51577-161">在 [空間感知] 索引標籤中，按一下 [複製] 按鈕以開啟 [複製設定檔] 視窗：</span><span class="sxs-lookup"><span data-stu-id="51577-161">In the **Spatial Awareness** tab, click the **Clone** button to open the Clone Profile window:</span></span>

![已選取 [空間感知] 索引標籤的 Unity MixedRealityToolkit 元件](../images/mr-learning-base/base-03-section1-step3-1.png)

<span data-ttu-id="51577-163">在 [複製設定檔] 視窗中，輸入適當的 **設定檔名稱**，例如 _GettingStarted_MixedRealitySpatialAwarenessSystemProfile_，然後按一下 [複製] 按鈕，以建立 **DefaultMixedRealitySpatialAwarenessSystemProfile** 的可編輯複本：</span><span class="sxs-lookup"><span data-stu-id="51577-163">In the Clone Profile window, enter a suitable **Profile Name**, for example, _GettingStarted_MixedRealitySpatialAwarenessSystemProfile_, then click the **Clone** button to create an editable copy of the **DefaultMixedRealitySpatialAwarenessSystemProfile**:</span></span>

![Unity MixedRealityToolkit 複製的 [空間感知系統設定檔] 快顯視窗](../images/mr-learning-base/base-03-section1-step3-2.png)

<span data-ttu-id="51577-165">新建立的空間感知系統設定檔現在會自動指派給您的組態設定檔：</span><span class="sxs-lookup"><span data-stu-id="51577-165">The newly created Spatial Awareness System Profile is now automatically assigned to your Configuration Profile:</span></span>

![已套用新建立自訂 MixedRealitySpatialAwarenessSystemProfile 的 Unity MixedRealityToolkit 元件](../images/mr-learning-base/base-03-section1-step3-3.png)

### <a name="4-clone-the-default-spatial-awareness-mesh-observer-profile"></a><span data-ttu-id="51577-167">4.複製預設的空間感知網格觀察器設定檔</span><span class="sxs-lookup"><span data-stu-id="51577-167">4. Clone the default Spatial Awareness Mesh Observer Profile</span></span>

<span data-ttu-id="51577-168">在仍選取 [空間感知] 索引標籤的情況下，展開 [Windows Mixed Reality 空間網格觀察器] 區段，然後按一下 [複製] 按鈕來開啟 [複製設定檔] 視窗：</span><span class="sxs-lookup"><span data-stu-id="51577-168">With the **Spatial Awareness** tab still selected, expand the **Windows Mixed Reality Spatial Mesh Observer** section, then click the **Clone** button to open the Clone Profile window:</span></span>

![已擴充 Windows Mixed Reality [空間網格觀察者] 區段的 Unity MixedRealityToolkit 元件](../images/mr-learning-base/base-03-section1-step4-1.png)

<span data-ttu-id="51577-170">在 [複製設定檔] 視窗中，輸入適當的 **設定檔名稱**，例如 _GettingStarted_MixedRealitySpatialAwarenessMeshObserverProfile_，然後按一下 [複製] 按鈕，以建立 **DefaultMixedRealitySpatialAwarenessMeshObserverProfile** 的可編輯複本：</span><span class="sxs-lookup"><span data-stu-id="51577-170">In the Clone Profile window, enter a suitable **Profile Name**, for example, _GettingStarted_MixedRealitySpatialAwarenessMeshObserverProfile_, then click the **Clone** button to create an editable copy of the **DefaultMixedRealitySpatialAwarenessMeshObserverProfile**:</span></span>

![Unity MixedRealityToolkit 複製的 [空間網格觀察者設定檔] 快顯視窗](../images/mr-learning-base/base-03-section1-step4-2.png)

<span data-ttu-id="51577-172">新建立的空間感知網格觀察器設定檔現在會自動指派給您的空間感知系統設定檔：</span><span class="sxs-lookup"><span data-stu-id="51577-172">The newly created Spatial Awareness Mesh Observer Profile is now automatically assigned to your Spatial Awareness System Profile:</span></span>

![已套用新建立自訂 MixedRealitySpatialAwarenessMeshObserverProfile 的 Unity MixedRealityToolkit 元件](../images/mr-learning-base/base-03-section1-step4-3.png)

### <a name="5-change-the-visibility-of-the-spatial-awareness-mesh"></a><span data-ttu-id="51577-174">5.變更空間感知網格的顯示</span><span class="sxs-lookup"><span data-stu-id="51577-174">5. Change the visibility of the spatial awareness mesh</span></span>

<span data-ttu-id="51577-175">在 [空間網格觀察器設定] 中，將 [顯示選項] 變更為 [遮蔽]，以隱藏仍在運作的空間對應網格：</span><span class="sxs-lookup"><span data-stu-id="51577-175">In the **Spatial Mesh Observer Settings**, change the **Display Option** to **Occlusion** to make the spatial mapping mesh invisible while still functional:</span></span>

![[空間網格觀察者顯示選項] 設定為 [遮蔽] 的 Unity MixedRealityToolkit 元件](../images/mr-learning-base/base-03-section1-step5-1.png)

> [!NOTE]
> <span data-ttu-id="51577-177">雖然空間對應網格看不到，但仍存在且正常運作。</span><span class="sxs-lookup"><span data-stu-id="51577-177">Although the spatial mapping mesh is not visible, it is still present and functional.</span></span> <span data-ttu-id="51577-178">例如，空間對應網格後方的任何全像投影 (實體牆後方的全像投影等) 將不會顯示。</span><span class="sxs-lookup"><span data-stu-id="51577-178">For example, any holograms behind the spatial mapping mesh, such as a hologram behind a physical wall, will not be visible.</span></span>

<span data-ttu-id="51577-179">您方才已了解如何修改 MRTK 設定檔中的設定。</span><span class="sxs-lookup"><span data-stu-id="51577-179">You just learned how to modify a setting in the MRTK profile.</span></span> <span data-ttu-id="51577-180">如您所見，為了自訂 MRTK 設定，您必須先建立預設設定檔的複本。</span><span class="sxs-lookup"><span data-stu-id="51577-180">As you can see, to customize the MRTK settings, you first need to create copies of the default profiles.</span></span> <span data-ttu-id="51577-181">由於預設設定檔無法編輯，因此當您想要還原為預設設定時，一律可以參考這些設定。</span><span class="sxs-lookup"><span data-stu-id="51577-181">Because the default profiles are not editable, you will always have them as references if you want to revert to the default settings.</span></span> <span data-ttu-id="51577-182">若要深入了解 MRTK 設定檔及其架構，您可以參閱 [MRTK 文件入口網站](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs)中的 [MRTK 設定檔設定指南](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/configuration/mixed-reality-configuration-guide.md)。</span><span class="sxs-lookup"><span data-stu-id="51577-182">To learn more about MRTK profiles and their architecture, you can refer to the [MRTK profile configuration guide](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/configuration/mixed-reality-configuration-guide.md) in the [MRTK Documentation Portal](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs).</span></span>
