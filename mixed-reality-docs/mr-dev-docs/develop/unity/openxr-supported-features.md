---
title: Unity 中的 OpenXR 外掛程式支援功能
description: 探索 OpenXR 針對 Unity 中的混合現實開發所支援的功能。
author: hferrone
ms.author: alexturn
ms.date: 01/11/2021
ms.topic: article
keywords: openxr、unity、hololens、hololens 2、mixed reality、MRTK、Mixed Reality 工具組、增強的現實、虛擬實境、混合現實耳機、學習、教學課程、快速入門
ms.openlocfilehash: d65bab65bcb06f7ccba522461e04062458e7400c
ms.sourcegitcommit: aa29b68603721e909f08f352feed24c65d2e505e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/12/2021
ms.locfileid: "98108841"
---
# <a name="mixed-reality-openxr-supported-features-in-unity"></a><span data-ttu-id="e13b8-104">混合現實 OpenXR Unity 中支援的功能</span><span class="sxs-lookup"><span data-stu-id="e13b8-104">Mixed Reality OpenXR supported features in Unity</span></span>

<span data-ttu-id="e13b8-105">**Mixed Reality OpenXR 外掛程式** 套件是 Unity **OpenXR 外掛程式** 的延伸模組，並支援 HoloLens 2 和 Windows Mixed Reality 耳機的功能套件。</span><span class="sxs-lookup"><span data-stu-id="e13b8-105">The **Mixed Reality OpenXR Plugin** package is an extension of Unity's **OpenXR Plugin** and supports a suite of features for HoloLens 2 and Windows Mixed Reality headsets.</span></span> <span data-ttu-id="e13b8-106">繼續之前，請確定您已安裝 **unity 2020.2** 或更新版本、 **OpenXR 外掛程式版本 0.1.2** 或更新版本，且您的 Unity 專案已 [設定 OpenXR](openxr-getting-started.md)。</span><span class="sxs-lookup"><span data-stu-id="e13b8-106">Before continuing, make sure that you've installed **Unity 2020.2** or later, **OpenXR Plugin version 0.1.2** or later, and your Unity project is [configured for OpenXR](openxr-getting-started.md).</span></span>

## <a name="whats-supported"></a><span data-ttu-id="e13b8-107">支援的項目</span><span class="sxs-lookup"><span data-stu-id="e13b8-107">What's supported</span></span>

<span data-ttu-id="e13b8-108">目前支援下列功能：</span><span class="sxs-lookup"><span data-stu-id="e13b8-108">The following features are currently supported:</span></span>

* <span data-ttu-id="e13b8-109">支援 HoloLens 2 的 UWP 應用程式，並針對 HoloLens 2 應用程式模型進行優化。</span><span class="sxs-lookup"><span data-stu-id="e13b8-109">Supports UWP applications for HoloLens 2, and optimize for HoloLens 2 application model.</span></span>
* <span data-ttu-id="e13b8-110">支援適用于 Windows Mixed Reality 耳機的 Win32 VR 應用程式，具有最新的控制器設定檔和全像應用程式遠端。</span><span class="sxs-lookup"><span data-stu-id="e13b8-110">Supports Win32 VR applications for Windows Mixed Reality headset with latest controller profiles and holographic app remoting.</span></span>
* <span data-ttu-id="e13b8-111">使用錨點和未系結空間的世界規模追蹤。</span><span class="sxs-lookup"><span data-stu-id="e13b8-111">World scale tracking using Anchors and Unbounded space.</span></span>
* <span data-ttu-id="e13b8-112">[錨點儲存體 API，以將錨點保存](#anchors-and-anchor-persistence) 到 HoloLens 2 的本機儲存體。</span><span class="sxs-lookup"><span data-stu-id="e13b8-112">[Anchor storage API to persist anchors](#anchors-and-anchor-persistence) to HoloLens 2 local storage.</span></span>
* <span data-ttu-id="e13b8-113">[移動控制器和手互動](#motion-controller-and-hand-interactions)，包括新的 HP 回音卡控制器。</span><span class="sxs-lookup"><span data-stu-id="e13b8-113">[Motion controller and hand interactions](#motion-controller-and-hand-interactions), including the new HP Reverb G2 controller.</span></span>
* <span data-ttu-id="e13b8-114">使用26個接點和聯合半徑輸入，以明確表述的手勢進行追蹤。</span><span class="sxs-lookup"><span data-stu-id="e13b8-114">Articulated hand tracking using 26 joints and joint radius inputs.</span></span>
* <span data-ttu-id="e13b8-115">HoloLens 2 上的眼睛注視互動。</span><span class="sxs-lookup"><span data-stu-id="e13b8-115">Eye gaze interaction on HoloLens 2.</span></span>
* <span data-ttu-id="e13b8-116">HoloLens 2 上尋找 (PV) 攝影機的相片/影片。</span><span class="sxs-lookup"><span data-stu-id="e13b8-116">Locating photo/video (PV) camera on HoloLens 2.</span></span>
* <span data-ttu-id="e13b8-117">混合實境擷取使用透過 PV 攝影機的第三種眼睛呈現。</span><span class="sxs-lookup"><span data-stu-id="e13b8-117">Mixed Reality Capture using 3rd eye rendering through PV camera.</span></span>
* <span data-ttu-id="e13b8-118">支援「播放」以使用全像「 [遠端處理」應用程式 HoloLens 2](#holographic-remoting-in-unity-editor-play-mode)，讓開發人員不需要建立及部署到裝置，即可將腳本進行偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="e13b8-118">Supports ["Play" to HoloLens 2 with the Holographic Remoting app](#holographic-remoting-in-unity-editor-play-mode), allowing developers to debug scripts without building and deploying to the device.</span></span>
* <span data-ttu-id="e13b8-119">透過 [MRTK OpenXR 提供者支援](openxr-getting-started.md#using-mrtk-with-openxr-support)，與 MRTK Unity 2.5.3 和更新版本相容。</span><span class="sxs-lookup"><span data-stu-id="e13b8-119">Compatible with MRTK Unity 2.5.3 and newer through [MRTK OpenXR provider support](openxr-getting-started.md#using-mrtk-with-openxr-support).</span></span>
* <span data-ttu-id="e13b8-120">與 Unity [ARFoundation 4.0](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html) 或更新版本相容</span><span class="sxs-lookup"><span data-stu-id="e13b8-120">Compatible with Unity [ARFoundation 4.0](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html) or later</span></span>

## <a name="holographic-remoting-in-unity-editor-play-mode"></a><span data-ttu-id="e13b8-121">Unity 編輯器 play 模式的全像遠端功能</span><span class="sxs-lookup"><span data-stu-id="e13b8-121">Holographic Remoting in Unity Editor play mode</span></span>

<span data-ttu-id="e13b8-122">在 Visual Studio 專案中建立 UWP Unity 專案，然後將它封裝並部署到 HoloLens 2 裝置，可能需要一些時間。</span><span class="sxs-lookup"><span data-stu-id="e13b8-122">Building a UWP Unity project in Visual Studio project and then packaging and deploying it to a HoloLens 2 device can take some time.</span></span> <span data-ttu-id="e13b8-123">其中一個解決方法是啟用全像「全像」編輯器遠端處理，讓您透過網路直接使用「播放」模式來將 c # 腳本進行 HoloLens 2 裝置的偵測。</span><span class="sxs-lookup"><span data-stu-id="e13b8-123">One solution is to enable the Holographic Editor Remoting, which lets you debug your C# script using “Play” mode directly to a HoloLens 2 device over your network.</span></span> <span data-ttu-id="e13b8-124">此案例可避免建立 UWP 套件並將其部署至遠端裝置的額外負荷。</span><span class="sxs-lookup"><span data-stu-id="e13b8-124">This scenario avoids the overhead of building and deploying a UWP package to remote device.</span></span>

1. <span data-ttu-id="e13b8-125">首先，您必須從存放區的 HoloLens 2 安裝全像 [遠端播放機應用程式](https://www.microsoft.com/store/productId/9NBLGGH4SV40) 。</span><span class="sxs-lookup"><span data-stu-id="e13b8-125">First, you need to [install the Holographic Remoting Player app](https://www.microsoft.com/store/productId/9NBLGGH4SV40) from Store on your HoloLens 2</span></span>
2. <span data-ttu-id="e13b8-126">在 HoloLens 2 上執行全像遠端播放播放程式應用程式，您會看到要連接的版本號碼和 IP 位址</span><span class="sxs-lookup"><span data-stu-id="e13b8-126">Run the Holographic Remoting Player app on HoloLens 2 and you'll see the version number and IP address to connect to</span></span>
    * <span data-ttu-id="e13b8-127">您將需要2.4 或更新版本才能使用 OpenXR 外掛程式</span><span class="sxs-lookup"><span data-stu-id="e13b8-127">You'll need v2.4 or later to work with the OpenXR plugin</span></span>

    ![HoloLens 中執行的全像 Remoting 播放程式的螢幕擷取畫面](images/openxr-features-img-01.png)

3. <span data-ttu-id="e13b8-129">開啟 [ **編輯-> 專案設定**]，流覽至 **XR 外掛程式管理**，然後選取 [ **Windows Mixed Reality 功能集** ] 方塊：</span><span class="sxs-lookup"><span data-stu-id="e13b8-129">Open **Edit -> Project Settings**, navigate to **XR plug-in Management**, and check the **Windows Mixed Reality feature set** box:</span></span>

    ![醒目提示 XR 外掛程式管理的 Unity 編輯器中開啟之 [專案設定] 面板的螢幕擷取畫面](images/openxr-features-img-02.png)

4. <span data-ttu-id="e13b8-131">展開 [ **OpenXR** ] 底下的 [**功能**] 區段，然後選取 [**全部顯示**]</span><span class="sxs-lookup"><span data-stu-id="e13b8-131">Expand the **Features** section under **OpenXR** and select **Show All**</span></span>
5. <span data-ttu-id="e13b8-132">核取 [全像攝影 **編輯器遠端處理** ] 核取方塊，然後輸入您從「全像」遠端應用程式取得的 IP 位址</span><span class="sxs-lookup"><span data-stu-id="e13b8-132">Check the **Holographic Editor Remoting** checkbox and input the IP address you get from the Holographic Remoting app:</span></span>

    ![在 Unity 編輯器中開啟專案設定面板的螢幕擷取畫面，其中已醒目提示功能](images/openxr-features-img-03.png)

<span data-ttu-id="e13b8-134">現在您可以按一下 [播放] 按鈕，以在 HoloLens 上的全像遠端應用程式中播放 Unity 應用程式。</span><span class="sxs-lookup"><span data-stu-id="e13b8-134">Now you can click the “Play” button to play your Unity app into the Holographic Remoting app on your HoloLens.</span></span> <span data-ttu-id="e13b8-135">您也可以 [將 Visual Studio 附加至 Unity](https://docs.microsoft.com/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows) ，以在播放模式中進行 c # 腳本的調試。</span><span class="sxs-lookup"><span data-stu-id="e13b8-135">You can also [attach Visual Studio to Unity](https://docs.microsoft.com/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows) to debug C# scripts in the play mode.</span></span>

> [!NOTE]
> <span data-ttu-id="e13b8-136">從0.1.0 版起，全像「全像」遠端執行時間不支援錨點，而 ARAnchorManager 功能將無法透過遠端處理。</span><span class="sxs-lookup"><span data-stu-id="e13b8-136">As of version 0.1.0, the Holographic Remoting runtime doesn’t support Anchors, and ARAnchorManager functionalities will not work through remoting.</span></span>  <span data-ttu-id="e13b8-137">這項功能會在未來的版本中推出。</span><span class="sxs-lookup"><span data-stu-id="e13b8-137">This feature is coming in future releases.</span></span>

## <a name="anchors-and-anchor-persistence"></a><span data-ttu-id="e13b8-138">錨點和錨點持續性</span><span class="sxs-lookup"><span data-stu-id="e13b8-138">Anchors and Anchor Persistence</span></span>

<span data-ttu-id="e13b8-139">Mixed Reality OpenXR 外掛程式透過 Unity 的 ARFoundation **ARAnchorManager** 的執行，提供基本錨定功能。</span><span class="sxs-lookup"><span data-stu-id="e13b8-139">The Mixed Reality OpenXR Plugin supplies basic anchor functionality through an implementation of Unity’s ARFoundation **ARAnchorManager**.</span></span> <span data-ttu-id="e13b8-140">若要瞭解 ARFoundation 中 **ARAnchor** 的基本概念，請造訪 [AR 錨點管理員的 ARFoundation 手冊](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/anchor-manager.html)。</span><span class="sxs-lookup"><span data-stu-id="e13b8-140">To learn the basics on **ARAnchor** s in ARFoundation, visit the [ARFoundation Manual for AR Anchor Manager](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/anchor-manager.html).</span></span> <span data-ttu-id="e13b8-141">從版本0.1.0，此外掛程式除了建立附加至平面的錨點（即將在未來版本中）之外，也支援所有 ARAnchorManager 功能。</span><span class="sxs-lookup"><span data-stu-id="e13b8-141">As of version 0.1.0, this plugin supports all ARAnchorManager functionality except creating anchors attached to a plane, which is coming in a future release.</span></span>

### <a name="anchor-persistence-and-the-xranchorstore"></a><span data-ttu-id="e13b8-142">錨點持續性和 XRAnchorStore</span><span class="sxs-lookup"><span data-stu-id="e13b8-142">Anchor Persistence and the XRAnchorStore</span></span>

<span data-ttu-id="e13b8-143">另一個稱為 **XRAnchorStore** 的 API 可讓錨點在會話之間保存。</span><span class="sxs-lookup"><span data-stu-id="e13b8-143">An additional API called the **XRAnchorStore** enables anchors to be persisted between sessions.</span></span> <span data-ttu-id="e13b8-144">XRAnchorStore 是您裝置上已儲存錨點的標記法。</span><span class="sxs-lookup"><span data-stu-id="e13b8-144">The XRAnchorStore is a representation of the saved anchors on your device.</span></span> <span data-ttu-id="e13b8-145">錨點可以從 Unity 場景中的 **ARAnchors** 保存、從儲存體載入至新的 **ARAnchors**，或從儲存體中刪除。</span><span class="sxs-lookup"><span data-stu-id="e13b8-145">Anchors can be persisted from **ARAnchors** in the Unity scene, loaded from storage into new **ARAnchors**, or deleted from storage.</span></span>

> [!NOTE]
> <span data-ttu-id="e13b8-146">這些錨點會儲存並載入至相同的裝置。</span><span class="sxs-lookup"><span data-stu-id="e13b8-146">These anchors are to be saved and loaded on the same device.</span></span> <span data-ttu-id="e13b8-147">未來版本中的 Azure 空間錨點將會支援跨裝置錨定儲存體。</span><span class="sxs-lookup"><span data-stu-id="e13b8-147">Cross-device anchor storage will be supported through Azure Spatial Anchors in a future release.</span></span>

``` cs
public class Microsoft.MixedReality.ARSubsystems.XRAnchorStore
{
    // A list of all persisted anchors, which can be loaded.
    public IReadOnlyList<string> PersistedAnchorNames { get; }

    // Clear all persisted anchors
    public void Clear();

    // Load a single persisted anchor by name. The ARAnchorManager will create this new anchor and report it in
    // the ARAnchorManager.anchorsChanged event. The TrackableId returned here is the same TrackableId the
    // ARAnchor will have when it is instantiated.
    public TrackableId LoadAnchor(string name);

    // Attempts to persist an existing ARAnchor with the given TrackableId to the local store. Returns true if
    // the storage is successful, false otherwise.
    public bool TryPersistAnchor(string name, TrackableId trackableId);

    // Removes a single persisted anchor from the anchor store. This will not affect any ARAnchors in the Unity
    // scene, only the anchors in storage.
    public void UnpersistAnchor(string name);
}
```

<span data-ttu-id="e13b8-148">為了載入 XRAnchorStore，外掛程式會在 XRAnchorSubsystem （ARAnchorManager 的子系統）上提供擴充方法：</span><span class="sxs-lookup"><span data-stu-id="e13b8-148">To load the XRAnchorStore, the plugin provides an extension method on the XRAnchorSubsystem, the subsystem of an ARAnchorManager:</span></span>

``` cs
public static Task<XRAnchorStore> LoadAnchorStoreAsync(this XRAnchorSubsystem anchorSubsystem)
```

<span data-ttu-id="e13b8-149">若要使用此擴充方法，請從 ARAnchorManager 的子系統進行存取，如下所示：</span><span class="sxs-lookup"><span data-stu-id="e13b8-149">To use this extension method, access it from an ARAnchorManager's subsystem as follows:</span></span>

``` cs
ARAnchorManager arAnchorManager = GetComponent<ARAnchorManager>();
XRAnchorStore anchorStore = await arAnchorManager.subsystem.LoadAnchorStoreAsync();
```

<span data-ttu-id="e13b8-150">若要查看保存/unpersisting 錨點的完整範例，請查看 [混合現實 OpenXR 外掛程式範例場景](openxr-getting-started.md#hololens-2-samples)中的錨點 > 錨點範例 GameObject 和 AnchorsSample.cs 腳本：</span><span class="sxs-lookup"><span data-stu-id="e13b8-150">To see a full example of persisting / unpersisting anchors, check out the Anchors -> Anchors Sample GameObject and AnchorsSample.cs script in the [Mixed Reality OpenXR Plugin Sample Scene](openxr-getting-started.md#hololens-2-samples):</span></span>

![在 Unity 編輯器中開啟之 [階層] 面板的螢幕擷取畫面，其中已醒目提示錨點範例](images/openxr-features-img-04.png)

![在 Unity 編輯器中開啟的 [偵測器] 面板的螢幕擷取畫面，其中已醒目提示錨點範例腳本](images/openxr-features-img-05.png)

## <a name="motion-controller-and-hand-interactions"></a><span data-ttu-id="e13b8-153">移動控制器和手互動</span><span class="sxs-lookup"><span data-stu-id="e13b8-153">Motion controller and hand interactions</span></span>

<span data-ttu-id="e13b8-154">若要瞭解 Unity 中混合現實互動的基本概念，請流覽 unity [Manual For UNITY XR 輸入](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html)。</span><span class="sxs-lookup"><span data-stu-id="e13b8-154">To learn the basics about mixed reality interactions in Unity, visit the [Unity Manual for Unity XR Input](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html).</span></span> <span data-ttu-id="e13b8-155">這項 Unity 檔涵蓋從控制器專屬輸入到更一般化 **InputFeatureUsage** 的對應、如何識別和分類可用的 XR 輸入、如何從這些輸入讀取資料等等。</span><span class="sxs-lookup"><span data-stu-id="e13b8-155">This Unity documentation covers the mappings from controller-specific inputs to more generalizable **InputFeatureUsage** s, how available XR inputs can be identified and categorized, how to read data from these inputs, and more.</span></span>

<span data-ttu-id="e13b8-156">Mixed Reality OpenXR 外掛程式提供額外的輸入互動設定檔，對應至標準 **InputFeatureUsage** s，如下所述：</span><span class="sxs-lookup"><span data-stu-id="e13b8-156">The Mixed Reality OpenXR Plugin provides additional input interaction profiles, mapped to standard **InputFeatureUsage** s as detailed below:</span></span>

| <span data-ttu-id="e13b8-157">InputFeatureUsage</span><span class="sxs-lookup"><span data-stu-id="e13b8-157">InputFeatureUsage</span></span> | <span data-ttu-id="e13b8-158">HP 回音 (OpenXR) </span><span class="sxs-lookup"><span data-stu-id="e13b8-158">HP Reverb G2 Controller (OpenXR)</span></span> | <span data-ttu-id="e13b8-159">HoloLens (OpenXR) </span><span class="sxs-lookup"><span data-stu-id="e13b8-159">HoloLens Hand (OpenXR)</span></span> |
| ---- | ---- | ---- |
| <span data-ttu-id="e13b8-160">primary2DAxis</span><span class="sxs-lookup"><span data-stu-id="e13b8-160">primary2DAxis</span></span> | <span data-ttu-id="e13b8-161">操縱 杆</span><span class="sxs-lookup"><span data-stu-id="e13b8-161">Joystick</span></span> | |
| <span data-ttu-id="e13b8-162">primary2DAxisClick</span><span class="sxs-lookup"><span data-stu-id="e13b8-162">primary2DAxisClick</span></span> | <span data-ttu-id="e13b8-163">搖桿-按一下</span><span class="sxs-lookup"><span data-stu-id="e13b8-163">Joystick - Click</span></span> | |
| <span data-ttu-id="e13b8-164">觸發程序 (trigger)</span><span class="sxs-lookup"><span data-stu-id="e13b8-164">trigger</span></span> | <span data-ttu-id="e13b8-165">觸發程序</span><span class="sxs-lookup"><span data-stu-id="e13b8-165">Trigger</span></span>  | |
| <span data-ttu-id="e13b8-166">握</span><span class="sxs-lookup"><span data-stu-id="e13b8-166">grip</span></span> | <span data-ttu-id="e13b8-167">握</span><span class="sxs-lookup"><span data-stu-id="e13b8-167">Grip</span></span> | <span data-ttu-id="e13b8-168">點擊或擠壓</span><span class="sxs-lookup"><span data-stu-id="e13b8-168">Air tap or squeeze</span></span> |
| <span data-ttu-id="e13b8-169">primaryButton</span><span class="sxs-lookup"><span data-stu-id="e13b8-169">primaryButton</span></span> | <span data-ttu-id="e13b8-170">[X/A]-按下</span><span class="sxs-lookup"><span data-stu-id="e13b8-170">[X/A] - Press</span></span> | <span data-ttu-id="e13b8-171">空中點選</span><span class="sxs-lookup"><span data-stu-id="e13b8-171">Air tap</span></span> |
| <span data-ttu-id="e13b8-172">secondaryButton</span><span class="sxs-lookup"><span data-stu-id="e13b8-172">secondaryButton</span></span> | <span data-ttu-id="e13b8-173">[Y/B]-按下</span><span class="sxs-lookup"><span data-stu-id="e13b8-173">[Y/B] - Press</span></span> | |
| <span data-ttu-id="e13b8-174">gripButton</span><span class="sxs-lookup"><span data-stu-id="e13b8-174">gripButton</span></span> | <span data-ttu-id="e13b8-175">握住-按</span><span class="sxs-lookup"><span data-stu-id="e13b8-175">Grip - Press</span></span> | |
| <span data-ttu-id="e13b8-176">triggerButton</span><span class="sxs-lookup"><span data-stu-id="e13b8-176">triggerButton</span></span> | <span data-ttu-id="e13b8-177">觸發程式-按下</span><span class="sxs-lookup"><span data-stu-id="e13b8-177">Trigger - Press</span></span> | |
| <span data-ttu-id="e13b8-178">menuButton</span><span class="sxs-lookup"><span data-stu-id="e13b8-178">menuButton</span></span> | <span data-ttu-id="e13b8-179">功能表</span><span class="sxs-lookup"><span data-stu-id="e13b8-179">Menu</span></span> | |

### <a name="aim-and-grip-poses"></a><span data-ttu-id="e13b8-180">目標和底姿勢</span><span class="sxs-lookup"><span data-stu-id="e13b8-180">Aim and Grip Poses</span></span>

<span data-ttu-id="e13b8-181">您可以透過 OpenXR 輸入互動存取兩組姿勢：</span><span class="sxs-lookup"><span data-stu-id="e13b8-181">You have access to two sets of poses through OpenXR input interactions:</span></span>

* <span data-ttu-id="e13b8-182">抓手中呈現物件的底框</span><span class="sxs-lookup"><span data-stu-id="e13b8-182">The grip poses for rendering objects in the hand</span></span>
* <span data-ttu-id="e13b8-183">目標是指向世界。</span><span class="sxs-lookup"><span data-stu-id="e13b8-183">The aim poses for pointing into the world.</span></span>

<span data-ttu-id="e13b8-184">有關此設計的詳細資訊，以及這兩個姿勢之間的差異，請參閱 [OpenXR 規格-輸入子路徑](https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#semantic-path-input)。</span><span class="sxs-lookup"><span data-stu-id="e13b8-184">More information on this design and the differences between the two poses can be found in the [OpenXR Specification - Input Subpaths](https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#semantic-path-input).</span></span>

<span data-ttu-id="e13b8-185">InputFeatureUsages **DevicePosition**、 **DeviceRotation**、 **DeviceVelocity** 和 **DeviceAngularVelocity** 提供 **的姿勢全都代表 OpenXR 的** 把手姿勢。</span><span class="sxs-lookup"><span data-stu-id="e13b8-185">Poses supplied by the InputFeatureUsages **DevicePosition**, **DeviceRotation**, **DeviceVelocity**, and **DeviceAngularVelocity** all represent the OpenXR **grip** pose.</span></span> <span data-ttu-id="e13b8-186">與框姿勢相關的 InputFeatureUsages 是在 Unity 的 [CommonUsages](https://docs.unity3d.com/2020.2/Documentation/ScriptReference/XR.CommonUsages.html)中定義。</span><span class="sxs-lookup"><span data-stu-id="e13b8-186">InputFeatureUsages related to grip poses are defined in Unity’s [CommonUsages](https://docs.unity3d.com/2020.2/Documentation/ScriptReference/XR.CommonUsages.html).</span></span>

<span data-ttu-id="e13b8-187">InputFeatureUsages **PointerPosition**、 **PointerRotation**、 **PointerVelocity** 和 **PointerAngularVelocity** 提供的姿勢全都代表 OpenXR 的 **目標** 。</span><span class="sxs-lookup"><span data-stu-id="e13b8-187">Poses supplied by the InputFeatureUsages **PointerPosition**, **PointerRotation**, **PointerVelocity**, and **PointerAngularVelocity** all represent the OpenXR **aim** pose.</span></span> <span data-ttu-id="e13b8-188">這些 InputFeatureUsages 不會定義在任何包含的 c # 檔案中，因此您必須定義您自己的 InputFeatureUsages，如下所示：</span><span class="sxs-lookup"><span data-stu-id="e13b8-188">These InputFeatureUsages aren't defined in any included C# files, so you'll need to define your own InputFeatureUsages as follows:</span></span>

``` cs
public static readonly InputFeatureUsage<Vector3> PointerPosition = new InputFeatureUsage<Vector3>("PointerPosition");
```

### <a name="haptics"></a><span data-ttu-id="e13b8-189">Haptics</span><span class="sxs-lookup"><span data-stu-id="e13b8-189">Haptics</span></span>

<span data-ttu-id="e13b8-190">如需在 Unity 的 XR 輸入系統中使用 haptics 的相關資訊，請參閱 unity [Manual For UNITY XR 輸入-haptics](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html#Haptics)中的檔。</span><span class="sxs-lookup"><span data-stu-id="e13b8-190">For information on using haptics in Unity’s XR Input system, documentation can be found at the [Unity Manual for Unity XR Input - Haptics](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html#Haptics).</span></span>

## <a name="whats-coming-soon"></a><span data-ttu-id="e13b8-191">即將推出的內容</span><span class="sxs-lookup"><span data-stu-id="e13b8-191">What's coming soon</span></span>

<span data-ttu-id="e13b8-192">下列問題和遺漏的功能都是已知的混合現實 OpenXR 外掛程式 **版本 0.1.0**。</span><span class="sxs-lookup"><span data-stu-id="e13b8-192">The following issues and missing features are known with Mixed Reality OpenXR plugin **version 0.1.0**.</span></span> <span data-ttu-id="e13b8-193">我們正在處理這些問題，並將在即將推出的版本中發行修正程式和新功能。</span><span class="sxs-lookup"><span data-stu-id="e13b8-193">We're working on these and will release fixes and new features in upcoming releases.</span></span>

* <span data-ttu-id="e13b8-194">尚不支援 **ARPlaneSubsystem** 。</span><span class="sxs-lookup"><span data-stu-id="e13b8-194">**ARPlaneSubsystem** is not supported yet.</span></span> <span data-ttu-id="e13b8-195">HoloLens 2 也不支援 **ARPlaneManager**、 **ARRaycastManager** 和相關的 API，例如 **ARAnchorManager. AttachAnchor** 。</span><span class="sxs-lookup"><span data-stu-id="e13b8-195">**ARPlaneManager**, **ARRaycastManager**, and related API like **ARAnchorManager.AttachAnchor** are also not supported on HoloLens 2.</span></span>
* <span data-ttu-id="e13b8-196">目前尚未支援錨點，但不久的未來將會推出 **錨點**。</span><span class="sxs-lookup"><span data-stu-id="e13b8-196">**Anchor** isn't supported by Holographic Remoting yet, but it's coming in the near future.</span></span>
* <span data-ttu-id="e13b8-197">目前尚不支援手上的 **網格** 追蹤、 **QR 代碼** 和 **XRMeshSubsystem** 。</span><span class="sxs-lookup"><span data-stu-id="e13b8-197">**Hand Mesh** tracking, **QR Codes**, and **XRMeshSubsystem** aren't supported yet.</span></span>
* <span data-ttu-id="e13b8-198">**Azure 空間錨點** 支援即將在未來版本中推出。</span><span class="sxs-lookup"><span data-stu-id="e13b8-198">**Azure Spatial Anchors** support is coming in a future release.</span></span>
* <span data-ttu-id="e13b8-199">**ARM64** 是 HoloLens 2 應用程式唯一支援的平臺。</span><span class="sxs-lookup"><span data-stu-id="e13b8-199">**ARM64** is the only supported platform for HoloLens 2 apps.</span></span> <span data-ttu-id="e13b8-200">**ARM** 平臺即將在未來版本中推出。</span><span class="sxs-lookup"><span data-stu-id="e13b8-200">The **ARM** platform is coming in a future release.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="e13b8-201">疑難排解</span><span class="sxs-lookup"><span data-stu-id="e13b8-201">Troubleshooting</span></span>

<span data-ttu-id="e13b8-202">當您在 HoloLens 2 上暫停和繼續 Unity 應用程式時，應用程式無法正確地繼續，這會導致 HoloLens 視圖中有4個旋轉點。</span><span class="sxs-lookup"><span data-stu-id="e13b8-202">When you suspend and resume a Unity app on HoloLens 2, the app can't correctly resume, which leads to 4 spinning dots in the HoloLens view.</span></span>
* <span data-ttu-id="e13b8-203">將 OpenXR 專案設定中的 **深度提交模式** 設定為 [ **無** ] 作為因應措施</span><span class="sxs-lookup"><span data-stu-id="e13b8-203">Set **Depth submission Mode** to **None** in the OpenXR project settings as a workaround</span></span>
