---
title: MRTK 2.7 版本資訊
description: MRTK 2.7 版的版本資訊
author: RogPodge
ms.author: roliu
ms.date: 06/16/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、XRSDK、舊版 XR、閏運動、Ultraleap、OpenXR
ms.localizationpriority: high
monikerRange: '>= mrtkunity-2021-05'
ms.openlocfilehash: d8fe446f99a4969e684bb4d2041c4ad4364c2eba
ms.sourcegitcommit: 72ddda03b13abc02bcea951a371ab4e4ccee3147
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/23/2021
ms.locfileid: "112536771"
---
# <a name="microsoft-mixed-reality-toolkit-27-release-notes"></a><span data-ttu-id="a43f9-104">Microsoft Mixed Reality 工具組2.7 版本資訊</span><span class="sxs-lookup"><span data-stu-id="a43f9-104">Microsoft Mixed Reality Toolkit 2.7 Release Notes</span></span>

## <a name="whats-new-in-271"></a><span data-ttu-id="a43f9-105">2.7.1 的新功能</span><span class="sxs-lookup"><span data-stu-id="a43f9-105">What's new in 2.7.1</span></span>

### <a name="show-version"></a><span data-ttu-id="a43f9-106">顯示版本</span><span class="sxs-lookup"><span data-stu-id="a43f9-106">Show version</span></span>

<span data-ttu-id="a43f9-107">`Mixed Reality`  >  `Toolkit` 功能表現在包含一個 `Show version...` 專案，該專案會檢查混合現實工具組 Foundation 套件，以判斷專案所使用的 MRTK 版本。</span><span class="sxs-lookup"><span data-stu-id="a43f9-107">The `Mixed Reality` > `Toolkit` menu now contains a `Show version...` entry that examines the Mixed Reality Toolkit Foundation package to determine the version of MRTK that is being used by the project.</span></span>

![顯示版本功能表](images/ShowVersionMenu.png)

![MRTK 版本對話方塊](images/VersionDialog.png)

> [!NOTE]
> <span data-ttu-id="a43f9-110">如果 MRTK 是從 GitHub 存放 [庫](https://aka.ms/mrtk)複製的，則不會設定版本資訊。</span><span class="sxs-lookup"><span data-stu-id="a43f9-110">If MRTK was cloned from the [GitHub repository](https://aka.ms/mrtk), the version information will not have been set.</span></span>
>
> ![無法判斷版本](images/CannotDetermineVersion.png)

### <a name="authors-list"></a><span data-ttu-id="a43f9-112">作者清單</span><span class="sxs-lookup"><span data-stu-id="a43f9-112">Authors list</span></span>

<span data-ttu-id="a43f9-113">從 MRTK 2.7.1 開始，作者清單檔案包含在 Mixed Reality 工具組 Foundation 套件中。</span><span class="sxs-lookup"><span data-stu-id="a43f9-113">Starting with MRTK 2.7.1, the authors list file is included in the Mixed Reality Toolkit Foundation package.</span></span>

### <a name="integrated-openxr-project-setup-into-the-configurator-setup-flow"></a><span data-ttu-id="a43f9-114">整合式 OpenXR 專案設定至設定流程</span><span class="sxs-lookup"><span data-stu-id="a43f9-114">Integrated OpenXR project setup into the Configurator setup flow</span></span>

<span data-ttu-id="a43f9-115">從 MRTK 2.7.1 開始，Mixed Reality OpenXR 外掛程式的使用者將會收到如何使用 MRTK 設定該外掛程式的指示。</span><span class="sxs-lookup"><span data-stu-id="a43f9-115">Starting with MRTK 2.7.1, users of the Mixed Reality OpenXR plugin will receive instructions on how to set up that plugin with MRTK.</span></span> <span data-ttu-id="a43f9-116">有一個選項可讓使用者以 HoloLens 2 為目標，以自動套用建議的設定。</span><span class="sxs-lookup"><span data-stu-id="a43f9-116">There is an option for users targeting HoloLens 2 to apply recommended settings automatically.</span></span>

![具有 OpenXR 安裝指示的設定程式視窗](images/configuratorMROpenXR.png)

### <a name="notable-bugfixes-and-changes"></a><span data-ttu-id="a43f9-118">值得注意的錯誤修正與變更</span><span class="sxs-lookup"><span data-stu-id="a43f9-118">Notable Bugfixes and Changes</span></span>

- <span data-ttu-id="a43f9-119">已標示 XR SDK 管線 [#9954](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9954)所支援的 Unity 操縱杆管理員， [#9994](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9994)</span><span class="sxs-lookup"><span data-stu-id="a43f9-119">Marked Unity Joystick Manager as supported on XR SDK pipeline [#9954](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9954), [#9994](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9994)</span></span>
- <span data-ttu-id="a43f9-120">已新增檢查以互動偵測器程式碼，以防止 null 錯誤 [#9943](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9943)</span><span class="sxs-lookup"><span data-stu-id="a43f9-120">Added checks to interactable inspector code to prevent null errors [#9943](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9943)</span></span>
- <span data-ttu-id="a43f9-121">將 OpenXR 網狀提供者新增至脈衝著色器範例場景 [#9902](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9902)</span><span class="sxs-lookup"><span data-stu-id="a43f9-121">Add OpenXR mesh provider to pulse shader example scene [#9902](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9902)</span></span>
- <span data-ttu-id="a43f9-122">將手型物理配置檔案還原至範例場景 [#9915](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9915)</span><span class="sxs-lookup"><span data-stu-id="a43f9-122">Restore hand physics profile to example scene [#9915](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9915)</span></span>
- <span data-ttu-id="a43f9-123">HandConstraint \* 腳本的一些清除 [#9935](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9935)</span><span class="sxs-lookup"><span data-stu-id="a43f9-123">Some cleanup to the HandConstraint\* scripts [#9935](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9935)</span></span>
- <span data-ttu-id="a43f9-124">修正會影響建立和複製設定檔的一些 bug [#9982](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9982)</span><span class="sxs-lookup"><span data-stu-id="a43f9-124">Fixed some bugs affecting creating and cloning profiles [#9982](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9982)</span></span>


## <a name="whats-new-in-270"></a><span data-ttu-id="a43f9-125">2.7.0 的新功能</span><span class="sxs-lookup"><span data-stu-id="a43f9-125">What's new in 2.7.0</span></span>

### <a name="openxr-is-now-officially-supported-in-mrtk"></a><span data-ttu-id="a43f9-126">OpenXR 現已正式支援 MRTK</span><span class="sxs-lookup"><span data-stu-id="a43f9-126">OpenXR is now officially supported in MRTK</span></span>

<span data-ttu-id="a43f9-127">由於新的 OpenXR 外掛程式變得越來越成熟，MRTK 現在正式支援 OpenXR。</span><span class="sxs-lookup"><span data-stu-id="a43f9-127">As the new OpenXR plugins are becoming more and more mature MRTK now officially supports OpenXR.</span></span> <span data-ttu-id="a43f9-128">相較于先前的版本，我們使用 OpenXR 將下列功能新增至專案：</span><span class="sxs-lookup"><span data-stu-id="a43f9-128">Compared to previous releases we added the following capabilities to projects using OpenXR:</span></span>

- [<span data-ttu-id="a43f9-129">支援系統提供的移動控制器模型</span><span class="sxs-lookup"><span data-stu-id="a43f9-129">Support for the system-provided motion controller model</span></span>](#support-for-the-system-provided-motion-controller-model-on-openxr)
- <span data-ttu-id="a43f9-130">支援 WinMR 手勢 (選取、保存、操作和流覽) [#9843](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9843)</span><span class="sxs-lookup"><span data-stu-id="a43f9-130">Support for WinMR gestures (select, hold, manipulation and navigation) [#9843](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9843)</span></span>
- [<span data-ttu-id="a43f9-131">控制器 haptics 的支援</span><span class="sxs-lookup"><span data-stu-id="a43f9-131">Support for controller haptics</span></span>](#support-for-controller-haptics-across-legacy-wmr-windows-xr-plugin-and-openxr)
- [<span data-ttu-id="a43f9-132">支援 HoloLens 2 上的已表達的手網格</span><span class="sxs-lookup"><span data-stu-id="a43f9-132">Support for articulated hand mesh on HoloLens 2</span></span>](#support-for-hololens-2-articulated-hand-mesh-on-openxr)
- <span data-ttu-id="a43f9-133">支援 HoloLens 2 [#9567](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9567)上的空間對應， [#9827](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9827)</span><span class="sxs-lookup"><span data-stu-id="a43f9-133">Support for Spatial Mapping on HoloLens 2 [#9567](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9567), [#9827](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9827)</span></span>
- <span data-ttu-id="a43f9-134">HoloLens 2 [#9744](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9744)上的場景理解支援</span><span class="sxs-lookup"><span data-stu-id="a43f9-134">Support for Scene Understanding on HoloLens 2 [#9744](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9744)</span></span>

<span data-ttu-id="a43f9-135">如果您的目標是透過 OpenXR HoloLens 2 或 Windows Mixed Reality 耳機，請務必透過 [混合現實功能工具](https://aka.ms/MRFeatureTool)安裝/更新至 **混合現實 OpenXR 外掛程式版本0.9.5 或** 更新版本，否則您可能會錯過上述一些改良功能。</span><span class="sxs-lookup"><span data-stu-id="a43f9-135">If you are targeting HoloLens 2 or Windows Mixed Reality headsets via OpenXR please make sure to install/update to **Mixed Reality OpenXR plugin version 0.9.5 or later** via [Mixed Reality Feature Tool](https://aka.ms/MRFeatureTool), otherwise you might miss some of the improvements above.</span></span>

### <a name="legacy-xr-and-xr-sdk-data-providers-can-now-be-used-within-the-same-profile"></a><span data-ttu-id="a43f9-136">舊版 XR 和 XR SDK 資料提供者現在可在相同的設定檔中使用</span><span class="sxs-lookup"><span data-stu-id="a43f9-136">Legacy XR and XR SDK Data Providers can now be used within the same profile</span></span>

<span data-ttu-id="a43f9-137">現在也會在選取適當的管線時載入資料提供者，讓舊版 XR 和 XR SDK 資料提供者在相同設定檔內並存存在。</span><span class="sxs-lookup"><span data-stu-id="a43f9-137">Data providers will now also only be loaded when the appropriate pipeline is selected, allowing both Legacy XR and XR SDK data providers to co-exist within the same profile.</span></span> <span data-ttu-id="a43f9-138">為了達到此目的，舊版 XR 和 XR SDK 資料提供者現在會組織在設定檔視圖內的不同索引標籤底下，協助使用者判斷他們是否擁有其目標 XR 管線的正確設定檔。</span><span class="sxs-lookup"><span data-stu-id="a43f9-138">To accommodate this, Legacy XR and XR SDK Data Providers are now organized under different tabs within the profile view, helping users determine whether they have the correct profile for their targeted XR pipeline.</span></span>

![舊版與 XR SDK 資料提供者現在可以在單一設定檔下整合](../features/images/xrsdk/LegacyAndXrsdkUnified.png)

<span data-ttu-id="a43f9-140">為了符合此值，現在不會再載入和顯示設定檔偵測器中的 null 資料提供者。</span><span class="sxs-lookup"><span data-stu-id="a43f9-140">To accommodate this, null data providers will now no longer be loaded and displayed in the profile inspector.</span></span> <span data-ttu-id="a43f9-141">使用者可以 `Show null data providers in the profile inspector` 在 **編輯 > 專案設定下切換-> Mixed Reality 工具** 組，以使用遺漏的資料提供者來偵測非預期的行為。</span><span class="sxs-lookup"><span data-stu-id="a43f9-141">Users can toggle `Show null data providers in the profile inspector` under **Edit -> Project Settings -> Mixed Reality Toolkit** to debug unexpected behaviors with missing data providers.</span></span>

<span data-ttu-id="a43f9-142">![Null 資料提供者現在會隱藏在 ](https://user-images.githubusercontent.com/39840334/115093658-ead24600-9ecf-11eb-91c2-486a37f69aba.png)
 ![ 設定檔偵測器中的預設值切換顯示 null 資料提供者](https://user-images.githubusercontent.com/39840334/115093670-f6257180-9ecf-11eb-96ec-ffe44a225a55.png)</span><span class="sxs-lookup"><span data-stu-id="a43f9-142">![Null data providers are now hidden by default](https://user-images.githubusercontent.com/39840334/115093658-ead24600-9ecf-11eb-91c2-486a37f69aba.png)
![Toggle show null data providers in the profile inspector](https://user-images.githubusercontent.com/39840334/115093670-f6257180-9ecf-11eb-96ec-ffe44a225a55.png)</span></span>

### <a name="added-experience-settings-and-an-associated-mixed-reality-scene-content-behavior"></a><span data-ttu-id="a43f9-143">新增經驗設定和相關聯的混合現實場景內容行為</span><span class="sxs-lookup"><span data-stu-id="a43f9-143">Added Experience Settings and an associated Mixed Reality Scene Content behavior</span></span>

<span data-ttu-id="a43f9-144">使用者現在可以設定 [體驗設定](../features/experience-settings/experience-settings.md)，這可讓 MRTK 根據目標體驗適當地顯示 [混合現實場景內容](../features/experience-settings/scene-content.md) 。</span><span class="sxs-lookup"><span data-stu-id="a43f9-144">Users can now configure [Experience Settings](../features/experience-settings/experience-settings.md), which will allow MRTK to display [Mixed Reality Scene Content](../features/experience-settings/scene-content.md) appropriately based on the targeted experience.</span></span>

<span data-ttu-id="a43f9-145">如果使用者先前的經驗調整設定不符合新的體驗設定設定檔，系統會提示他們在偵測器中加以修正</span><span class="sxs-lookup"><span data-stu-id="a43f9-145">If user's previous Experience Scale settings do not match the new Experience Settings Profile, they will be prompted to correct it in the inspector</span></span>

![體驗規模遷移](https://user-images.githubusercontent.com/39840334/114946863-d70bde80-9e00-11eb-9859-fa40d40d2b36.gif)

### <a name="the-redesigned-configurator-now-guides-the-user-through-the-setup-process"></a><span data-ttu-id="a43f9-147">重新設計的設定程式現在會引導使用者完成設定流程</span><span class="sxs-lookup"><span data-stu-id="a43f9-147">The Redesigned Configurator now guides the user through the setup process</span></span>

<span data-ttu-id="a43f9-148">新的 MRTK 設定程式會提供使用者逐步指引，以正確設定專案以進行 XR 開發，並與 MRTK 搭配使用。</span><span class="sxs-lookup"><span data-stu-id="a43f9-148">The new MRTK configurator provides users step-by-step guidance to properly configure the project for XR development and use with MRTK.</span></span> <span data-ttu-id="a43f9-149">它涵蓋了選取的 XR 管線、取得平臺專屬外掛程式、匯入 TextMeshPro、顯示使用 UPM) 的範例 (，以及其他先前包含專案的建議設定。</span><span class="sxs-lookup"><span data-stu-id="a43f9-149">It covers the selection of XR pipeline, getting the platform specific plugins, importing TextMeshPro, displaying the examples (when using UPM) and other previously included recommended settings for the project.</span></span>

![顯示管線清單的配置器](images/Configurator.png)

### <a name="graduated-teleport-hotspot"></a><span data-ttu-id="a43f9-151">分級的傳送熱點</span><span class="sxs-lookup"><span data-stu-id="a43f9-151">Graduated Teleport Hotspot</span></span>

<span data-ttu-id="a43f9-152">新的「 [傳送」熱點元件](../features/teleport-system/teleport-hotspot.md) 已經過分級。</span><span class="sxs-lookup"><span data-stu-id="a43f9-152">A new [teleport hotspot component](../features/teleport-system/teleport-hotspot.md) has been graduated.</span></span> <span data-ttu-id="a43f9-153">您可以將「傳送」熱點新增至 GameObject，以確保使用者在傳送至該位置時，在特定的位置和方向。</span><span class="sxs-lookup"><span data-stu-id="a43f9-153">You can add a teleport hotspot to your GameObject to ensure that the user is in a certain position and orientation when they teleport to that location.</span></span>

![傳送熱點範例](images/TeleportHotspot.gif)

### <a name="graduated-dwell"></a><span data-ttu-id="a43f9-155">過渡的停留</span><span class="sxs-lookup"><span data-stu-id="a43f9-155">Graduated Dwell</span></span>

<span data-ttu-id="a43f9-156">停留功能和範例現在已從實驗中開始。</span><span class="sxs-lookup"><span data-stu-id="a43f9-156">The dwell feature and example is now graduated from experimental.</span></span> <span data-ttu-id="a43f9-157">範例場景中包含體積型 HoloLens 2 樣式按鈕的新範例。</span><span class="sxs-lookup"><span data-stu-id="a43f9-157">New examples of volumetric HoloLens 2 style buttons are included in the sample scene.</span></span>

![停留主圖](../features/images/dwell/MRTK_UX_Dwell.png)

### <a name="added-support-for-leap-motion-unity-modules-version-460-470-471-and-480"></a><span data-ttu-id="a43f9-159">已新增對4.6.0、4.7.0、4.7.1 和4.8.0 之 Leap 動作 Unity 模組的支援</span><span class="sxs-lookup"><span data-stu-id="a43f9-159">Added support for Leap Motion Unity Modules version 4.6.0, 4.7.0, 4.7.1 and 4.8.0</span></span>

<span data-ttu-id="a43f9-160">最新版本的 [Leap 動作 Unity 模組](https://developer.leapmotion.com/unity) 支援現在與 MRTK 2.7.0 相容。</span><span class="sxs-lookup"><span data-stu-id="a43f9-160">Support for the latest versions of the [Leap Motion Unity Modules](https://developer.leapmotion.com/unity) is now compatible with MRTK 2.7.0.</span></span>  <span data-ttu-id="a43f9-161">如需詳細資訊，請參閱 [如何設定 MRTK 以進行 Leap 動作](../supported-devices/leap-motion-mrtk.md) 。</span><span class="sxs-lookup"><span data-stu-id="a43f9-161">See [How to Configure MRTK for Leap Motion](../supported-devices/leap-motion-mrtk.md) for more information.</span></span>

<span data-ttu-id="a43f9-162">感謝您 @jackyangzzh 參與新的 LeapMotionOrientationExample 場景！</span><span class="sxs-lookup"><span data-stu-id="a43f9-162">Big thanks to @jackyangzzh for contributing the new LeapMotionOrientationExample scene!</span></span>

### <a name="targeted-speech-events-raised-no-longer-restricted-to-gaze-pointers"></a><span data-ttu-id="a43f9-163">鎖定的目標語音事件不會再受限於注視指標</span><span class="sxs-lookup"><span data-stu-id="a43f9-163">Targeted speech events raised no longer restricted to gaze pointers</span></span>

<span data-ttu-id="a43f9-164">先前，目標語音事件只能在以注視指標為焦點的物件上引發。</span><span class="sxs-lookup"><span data-stu-id="a43f9-164">Previously, targeted speech events could only be raised on objects which were focused on with the gaze pointer.</span></span> <span data-ttu-id="a43f9-165">現在，如果物件是以任何指標為焦點，便可以接收語音事件。</span><span class="sxs-lookup"><span data-stu-id="a43f9-165">Now, objects can receive speech events if they are focused by any pointer.</span></span>

![具有太多指標的語音事件](https://user-images.githubusercontent.com/39840334/117516612-6fa00500-af4e-11eb-94ba-d5fb2ed4e7de.gif)

### <a name="ported-texttospeech-from-htk-to-mrtk"></a><span data-ttu-id="a43f9-167">從 HTK 移植 TextToSpeech 至 MRTK</span><span class="sxs-lookup"><span data-stu-id="a43f9-167">Ported TextToSpeech from HTK to MRTK</span></span>

<span data-ttu-id="a43f9-168">又陷入 TextToSpeech 腳本現在已在 MRTK 中正式推出，可協助您使用從 UWP 平臺上的文字產生語音 [`SpeechSynthesizer`](/uwp/api/windows.media.speechsynthesis.speechsynthesizer) 。</span><span class="sxs-lookup"><span data-stu-id="a43f9-168">The beloved TextToSpeech script is now finally available in MRTK to help you generate speech from text on the UWP platform using [`SpeechSynthesizer`](/uwp/api/windows.media.speechsynthesis.speechsynthesizer).</span></span> <span data-ttu-id="a43f9-169">也加入了範例場景來示範此功能。</span><span class="sxs-lookup"><span data-stu-id="a43f9-169">Also added a sample scene to demonstrate the feature.</span></span>

### <a name="support-for-the-system-provided-motion-controller-model-on-openxr"></a><span data-ttu-id="a43f9-170">在 OpenXR 上支援系統提供的移動控制器模型</span><span class="sxs-lookup"><span data-stu-id="a43f9-170">Support for the system-provided motion controller model on OpenXR</span></span>

<span data-ttu-id="a43f9-171">在 OpenXR 上針對系統提供的移動控制器模型，新增了在編輯器和執行時間中的支援。</span><span class="sxs-lookup"><span data-stu-id="a43f9-171">Added support, both in-editor and at runtime, for the system-provided motion controller model on OpenXR.</span></span>

![顯示兩個移動控制器模型的編輯器視窗](https://user-images.githubusercontent.com/3580640/116493405-89a55d80-a853-11eb-95ae-d430e6fdc8b4.png)

### <a name="support-for-hololens-2-articulated-hand-mesh-on-openxr"></a><span data-ttu-id="a43f9-173">支援在 OpenXR 上 HoloLens 2 表達的手網格</span><span class="sxs-lookup"><span data-stu-id="a43f9-173">Support for HoloLens 2 articulated hand mesh on OpenXR</span></span>

![MRTK 範例場景中在裝置上執行的手網格](https://user-images.githubusercontent.com/3580640/112909923-32bb3580-90a7-11eb-925d-464b135edc61.png)

### <a name="support-for-controller-haptics-across-legacy-wmr-windows-xr-plugin-and-openxr"></a><span data-ttu-id="a43f9-175">跨舊版 WMR、Windows XR 外掛程式和 OpenXR 的控制器 haptics 支援</span><span class="sxs-lookup"><span data-stu-id="a43f9-175">Support for controller haptics across legacy WMR, Windows XR Plugin, and OpenXR</span></span>

<span data-ttu-id="a43f9-176">已新增跨舊版 WMR、Windows XR 外掛程式和 OpenXR 的控制器 haptics 支援。</span><span class="sxs-lookup"><span data-stu-id="a43f9-176">Added support for controller haptics across legacy WMR, Windows XR Plugin, and OpenXR.</span></span> [<span data-ttu-id="a43f9-177">#9735</span><span class="sxs-lookup"><span data-stu-id="a43f9-177">#9735</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9735)

### <a name="support-for-eye-tracking-on-windows-xr-plugin"></a><span data-ttu-id="a43f9-178">Windows XR 外掛程式上的眼睛追蹤支援</span><span class="sxs-lookup"><span data-stu-id="a43f9-178">Support for eye tracking on Windows XR Plugin</span></span>

<span data-ttu-id="a43f9-179">在使用 Windows XR 外掛程式的最小2.7.0 版本時，新增了眼睛的支援 (Unity 2019) 、4.4.2 (Unity 2020) 和 5.2.2 (Unity 2021) 。</span><span class="sxs-lookup"><span data-stu-id="a43f9-179">Added support for eye gaze when using Windows XR Plugin minimum versions of 2.7.0 (Unity 2019), 4.4.2 (Unity 2020), and 5.2.2 (Unity 2021).</span></span> [<span data-ttu-id="a43f9-180">#9609</span><span class="sxs-lookup"><span data-stu-id="a43f9-180">#9609</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9609)

### <a name="notable-bugfixes-and-changes"></a><span data-ttu-id="a43f9-181">值得注意的錯誤修正與變更</span><span class="sxs-lookup"><span data-stu-id="a43f9-181">Notable Bugfixes and Changes</span></span>

- <span data-ttu-id="a43f9-182">縮小偵測變得更平滑。</span><span class="sxs-lookup"><span data-stu-id="a43f9-182">Pinch detection made smoother.</span></span> <span data-ttu-id="a43f9-183">現在難以意外地卸載縮小手勢。</span><span class="sxs-lookup"><span data-stu-id="a43f9-183">It is now harder to accidentally drop the pinch gesture.</span></span> [<span data-ttu-id="a43f9-184">#9576</span><span class="sxs-lookup"><span data-stu-id="a43f9-184">#9576</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9576)
- <span data-ttu-id="a43f9-185">具有物件操作工具元件的物件現在會在設定旗標時一致地維持版本的速度。</span><span class="sxs-lookup"><span data-stu-id="a43f9-185">Objects with the Object Manipulator component now consistently maintain velocity on release when the flag is set.</span></span> [<span data-ttu-id="a43f9-186">#9733</span><span class="sxs-lookup"><span data-stu-id="a43f9-186">#9733</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9733)
- <span data-ttu-id="a43f9-187">Strafing 現在會檢查樓層，以協助防止相機可裁剪至環境或使用者停留在空白空間的情況。[#9697](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9697)</span><span class="sxs-lookup"><span data-stu-id="a43f9-187">Back-strafing now checks for a floor, helping prevent situations where the camera can clip into the environment or where the user is left hovering over empty space.[#9697](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9697)</span></span>
- <span data-ttu-id="a43f9-188">IsNearObject 現在是虛擬屬性，可在擴充球體或取得指標時提供更大的彈性。</span><span class="sxs-lookup"><span data-stu-id="a43f9-188">IsNearObject is now a virtual property, allowing more flexibility when extending the sphere or poke pointer.</span></span> [<span data-ttu-id="a43f9-189">#9803</span><span class="sxs-lookup"><span data-stu-id="a43f9-189">#9803</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9803)
- <span data-ttu-id="a43f9-190">按鈕現在會在顯示可用的語音命令時顯示適當的關鍵字。</span><span class="sxs-lookup"><span data-stu-id="a43f9-190">Buttons now display the proper keyword when showing the available speech command.</span></span> [<span data-ttu-id="a43f9-191">#9824</span><span class="sxs-lookup"><span data-stu-id="a43f9-191">#9824</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9824)
- <span data-ttu-id="a43f9-192">Oculus 控制器現在會使用它自己的獨立視覺化程式，防止衝突的 MRTK 視覺效果與 Oculus 整合套件的視覺效果。</span><span class="sxs-lookup"><span data-stu-id="a43f9-192">Oculus Controllers now uses it's own standalone visualizer, preventing the MRTK visualization from clashing with the Oculus Integration Package's visualization.</span></span> [<span data-ttu-id="a43f9-193">#9589</span><span class="sxs-lookup"><span data-stu-id="a43f9-193">#9589</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9589)
- <span data-ttu-id="a43f9-194">鍵盤相關腳本已變更，以配合最新 Unity 版本的行為 (2019.4.25 + & 2020.3.2 +) 。</span><span class="sxs-lookup"><span data-stu-id="a43f9-194">Keyboard related scripts have been changed to align with the behavior in latest Unity versions (2019.4.25+ & 2020.3.2+).</span></span> <span data-ttu-id="a43f9-195">在發行時，仍有自動完成錯誤和 TMP 輸入欄位 bug (兩者都是 MRTK) 影響 HoloLens 的外部。</span><span class="sxs-lookup"><span data-stu-id="a43f9-195">As of the release there is still an auto-completion bug and a TMP Input Field bug (both are external to MRTK) impacting HoloLens.</span></span> <span data-ttu-id="a43f9-196">如需詳細資訊，請參閱 [#9056](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9056) 和 [#9724](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9724)。</span><span class="sxs-lookup"><span data-stu-id="a43f9-196">For more information please see [#9056](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9056) and [#9724](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9724).</span></span>
- <span data-ttu-id="a43f9-197">改進了滾動物件集合的效能。</span><span class="sxs-lookup"><span data-stu-id="a43f9-197">Improved the performance of Scrolling Object Collection.</span></span> <span data-ttu-id="a43f9-198">也修正了導致集合內的 GameObject 在重複時遺失材質的問題。</span><span class="sxs-lookup"><span data-stu-id="a43f9-198">Also fixed an issue causing GameObject within the collection to lose material when duplicated.</span></span> <span data-ttu-id="a43f9-199">[#9813](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9813)， [#9718](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9718)</span><span class="sxs-lookup"><span data-stu-id="a43f9-199">[#9813](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9813), [#9718](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9718)</span></span>
- <span data-ttu-id="a43f9-200">在場景理解示範腳本中，新增函式 `GetSceneObjectsOfType` 以取得特定種類的所有觀察場景物件。</span><span class="sxs-lookup"><span data-stu-id="a43f9-200">In the Scene Understanding demo script, added the `GetSceneObjectsOfType` function to retrieve all observed scene object of a certain kind.</span></span> <span data-ttu-id="a43f9-201">[#9524](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9524)， [#9744](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9744)</span><span class="sxs-lookup"><span data-stu-id="a43f9-201">[#9524](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9524), [#9744](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9744)</span></span>
- <span data-ttu-id="a43f9-202">在命令列建立工具中，只有 `sceneList` `sceneListFile` 當有任何旗標存在時，或旗標所指定的場景 () 將會包含在組建中。</span><span class="sxs-lookup"><span data-stu-id="a43f9-202">In command line build tool, only scenes specified by the `sceneList` or `sceneListFile` flags (when any flag is present) will be included in the build.</span></span> [<span data-ttu-id="a43f9-203">#9695</span><span class="sxs-lookup"><span data-stu-id="a43f9-203">#9695</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9695)
- <span data-ttu-id="a43f9-204">在 build tool 中，有一個新的選項可指定 `nuget.exe` 和使用該路徑來執行封裝還原，而不是使用 `msbuild` (預設選項) 。</span><span class="sxs-lookup"><span data-stu-id="a43f9-204">In build tool, there is a new option to specify a path to `nuget.exe` and use that to perform package restore instead of using `msbuild` (the default option).</span></span> [<span data-ttu-id="a43f9-205">#9556</span><span class="sxs-lookup"><span data-stu-id="a43f9-205">#9556</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9556)
- <span data-ttu-id="a43f9-206">已修正使用 Windows XR 外掛程式的問題可能會導致過時的接點和雙手勢網格。</span><span class="sxs-lookup"><span data-stu-id="a43f9-206">Fixed issue where using Windows XR Plugin could result in stale hand joints and doubled hand meshes.</span></span> [<span data-ttu-id="a43f9-207">#9890</span><span class="sxs-lookup"><span data-stu-id="a43f9-207">#9890</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9890)
- <span data-ttu-id="a43f9-208">已修正使用 Windows XR 外掛程式的自動遠端功能導致遺失輸入和互動的問題。</span><span class="sxs-lookup"><span data-stu-id="a43f9-208">Fixed issue where using Windows XR Plugin's automatic remoting feature led to missing input and interactions.</span></span> [<span data-ttu-id="a43f9-209">#9868</span><span class="sxs-lookup"><span data-stu-id="a43f9-209">#9868</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9868)
- <span data-ttu-id="a43f9-210">已修正 BuildDeployWindow 嘗試查詢不正確登錄機碼以取得 Windows SDK 路徑的問題。</span><span class="sxs-lookup"><span data-stu-id="a43f9-210">Fixed issue where the BuildDeployWindow would try to query an invalid reg key for the Windows SDK path.</span></span> [<span data-ttu-id="a43f9-211">#9664</span><span class="sxs-lookup"><span data-stu-id="a43f9-211">#9664</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9664)
- <span data-ttu-id="a43f9-212">MRTK 的 glTF 匯入工具現在是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="a43f9-212">MRTK's glTF importers are now optional.</span></span> <span data-ttu-id="a43f9-213">如果有多個 glTF 匯入工具，您可以藉由新增 `MRTK_GLTF_IMPORTER_OFF` 至自訂腳本定義符號來停用 MRTK。</span><span class="sxs-lookup"><span data-stu-id="a43f9-213">If multiple glTF importers are present, MRTK's can be disabled by adding `MRTK_GLTF_IMPORTER_OFF` to the custom scripting define symbols.</span></span> [<span data-ttu-id="a43f9-214">#9658</span><span class="sxs-lookup"><span data-stu-id="a43f9-214">#9658</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9658)
- <span data-ttu-id="a43f9-215">已修正未正確偵測到 OpenVR 上 Knuckles 控制器的問題。</span><span class="sxs-lookup"><span data-stu-id="a43f9-215">Fixed issue where the Knuckles controllers on OpenVR weren't being detected properly.</span></span> [<span data-ttu-id="a43f9-216">#9881</span><span class="sxs-lookup"><span data-stu-id="a43f9-216">#9881</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9881)
- <span data-ttu-id="a43f9-217">減少視覺化手中的每個畫面格配置數目 [#9756](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9756)</span><span class="sxs-lookup"><span data-stu-id="a43f9-217">Reduce the number of per-frame allocations when visualizing the hand mesh [#9756](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9756)</span></span>
- <span data-ttu-id="a43f9-218">新增功能表項目以啟動 Unity 中的 MRTK 範例套件 (封裝管理員) ，讓您更輕鬆地匯入範例 [#9798](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9798)</span><span class="sxs-lookup"><span data-stu-id="a43f9-218">Added a menu item to launch the MRTK Examples package (in Unity Package Manager) to make it easier to import samples [#9798](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9798)</span></span>
- <span data-ttu-id="a43f9-219">減少使用 Unity 2020.3 時的載入時間警告數目。</span><span class="sxs-lookup"><span data-stu-id="a43f9-219">Reduced the number of load-time warnings when using Unity 2020.3.</span></span>
- <span data-ttu-id="a43f9-220">已新增組建視窗功能檔： [造訪頁面](/windows/mixed-reality/mrtk-unity/features/tools/build-window)</span><span class="sxs-lookup"><span data-stu-id="a43f9-220">Added Build Window feature documentation: [Visit the page](/windows/mixed-reality/mrtk-unity/features/tools/build-window)</span></span>

## <a name="known-issues"></a><span data-ttu-id="a43f9-221">已知問題</span><span class="sxs-lookup"><span data-stu-id="a43f9-221">Known Issues</span></span>

### <a name="audio-demos-are-missing-an-asmdef-file-upm-package"></a><span data-ttu-id="a43f9-222">音訊示範缺少 asmdef 檔案 (UPM 套件) </span><span class="sxs-lookup"><span data-stu-id="a43f9-222">Audio demos are missing an asmdef file (UPM package)</span></span>

<span data-ttu-id="a43f9-223">透過混合現實功能工具匯入 MRTK 時，會使用 Unity 封裝管理員 UI 將範例和示範新增至專案。</span><span class="sxs-lookup"><span data-stu-id="a43f9-223">When importing MRTK via the Mixed Reality Feature Tool, samples and demos are added to the project using the Unity Package Manager UI.</span></span> <span data-ttu-id="a43f9-224">匯入音訊示範之後， `WindowsMicrophoneStreamDemo.unity` 場景將無法正常運作。</span><span class="sxs-lookup"><span data-stu-id="a43f9-224">After importing the Audio demos, the `WindowsMicrophoneStreamDemo.unity` scene will not behave properly.</span></span> <span data-ttu-id="a43f9-225">這是範例的 asmdef 檔案遺失的結果。</span><span class="sxs-lookup"><span data-stu-id="a43f9-225">This is a result of a missing .asmdef file for the sample.</span></span>

<span data-ttu-id="a43f9-226">若要解決此 [問題](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9908)，請執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="a43f9-226">To work around this [issue](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9908), please perform the following steps:</span></span>

- <span data-ttu-id="a43f9-227">Copy Library/PackageCache/com.microsoft.mixedreality.toolkit.examples@ [...]/MRTK.範例： asmdef 至您的「資產/範例/混合現實工具組範例」資料夾</span><span class="sxs-lookup"><span data-stu-id="a43f9-227">Copy Library/PackageCache/com.microsoft.mixedreality.toolkit.examples@[...]/MRTK.Examples.asmdef into your "Assets/Samples/Mixed Reality Toolkit Examples" folder</span></span>
- <span data-ttu-id="a43f9-228">將複製的檔案重新命名為範例</span><span class="sxs-lookup"><span data-stu-id="a43f9-228">Rename the copied file to Examples</span></span>
- <span data-ttu-id="a43f9-229">開啟範例檔案</span><span class="sxs-lookup"><span data-stu-id="a43f9-229">Open the Examples file</span></span>
- <span data-ttu-id="a43f9-230">在 [名稱] 方塊中，將內容取代為範例</span><span class="sxs-lookup"><span data-stu-id="a43f9-230">In the Name box, replace the contents with Examples</span></span>
- <span data-ttu-id="a43f9-231">按一下 [套用]</span><span class="sxs-lookup"><span data-stu-id="a43f9-231">Click Apply</span></span>
- <span data-ttu-id="a43f9-232">建置及部署</span><span class="sxs-lookup"><span data-stu-id="a43f9-232">Build and deploy</span></span>

<span data-ttu-id="a43f9-233">即將推出的 MRTK 版本將會修正此問題。</span><span class="sxs-lookup"><span data-stu-id="a43f9-233">This issue will be fixed in an upcoming MRTK release.</span></span>

### <a name="mrtk-build-window-triggers-indefinite-importing-assets-dialog-in-unity-20203"></a><span data-ttu-id="a43f9-234">Unity 2020.3 中的 MRTK 組建視窗觸發程式未限制的「匯入資產」對話方塊</span><span class="sxs-lookup"><span data-stu-id="a43f9-234">MRTK build window triggers indefinite "Importing assets" dialog in Unity 2020.3</span></span>

<span data-ttu-id="a43f9-235">Unity 2020.3 上的 MRTK build 視窗有一個已知 [問題](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9723) ，在成功執行 UWP 組建之後，[匯入資產] 對話方塊就不會完成。</span><span class="sxs-lookup"><span data-stu-id="a43f9-235">There is a known [issue](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9723) with the MRTK build window on Unity 2020.3 where after successfully performing a UWP build, the "Importing assets" dialog does not complete.</span></span> <span data-ttu-id="a43f9-236">正在與 Unity 合作調查此問題。</span><span class="sxs-lookup"><span data-stu-id="a43f9-236">This issue is being investigated in partnership with Unity.</span></span>

### <a name="text-mesh-pro-canvas-renderer-warnings-in-unity-2020"></a><span data-ttu-id="a43f9-237">Unity 2020 中的文字網格 Pro 畫布轉譯器警告</span><span class="sxs-lookup"><span data-stu-id="a43f9-237">Text Mesh Pro Canvas Renderer warnings in Unity 2020</span></span>

<span data-ttu-id="a43f9-238">使用 Unity 2020 時，最 MRTK 的範例場景中會記錄下列警告：</span><span class="sxs-lookup"><span data-stu-id="a43f9-238">The following warning is logged in most MRTK example scenes while using Unity 2020:</span></span>

```txt
Please remove the CanvasRenderer component from the [TextMeshPro] GameObject as this component is no longer necessary.
```

<span data-ttu-id="a43f9-239">[TextMeshPro 版本 3.0.3](https://docs.unity3d.com/Packages/com.unity.textmeshpro@3.0/changelog/CHANGELOG.html#changes-3)中新增了 Canvas 轉譯器警告。</span><span class="sxs-lookup"><span data-stu-id="a43f9-239">The Canvas Renderer warning was added in [TextMeshPro version 3.0.3](https://docs.unity3d.com/Packages/com.unity.textmeshpro@3.0/changelog/CHANGELOG.html#changes-3).</span></span>  <span data-ttu-id="a43f9-240">這些警告不會影響 MRTK 的範例場景，而且可以從主控台中清除。</span><span class="sxs-lookup"><span data-stu-id="a43f9-240">These warning do not have an impact on MRTK's example scenes and can be cleared from the console.</span></span> <span data-ttu-id="a43f9-241">如需詳細資訊，請參閱 [問題 9811](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9811) 。</span><span class="sxs-lookup"><span data-stu-id="a43f9-241">See [Issue 9811](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9811) for more details.</span></span>
