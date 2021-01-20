---
title: Unity 中的相機
description: 瞭解如何設定及使用 Unity 的主要攝影機進行 Windows Mixed Reality 開發以進行全像轉譯。
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit，mixedrealitytoolkit，mixedrealitytoolkit-unity，全像轉譯，全像全像，全像投影、全像投影、聚焦點、深度緩衝區、僅限方向、位置、不透明、透明、剪輯、混合現實耳機、windows mixed reality 耳機、虛擬實境耳機
ms.openlocfilehash: ba42e8a384f62dddcf7b8e685859ddeff7b666bb
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/20/2021
ms.locfileid: "98581125"
---
# <a name="camera-in-unity"></a><span data-ttu-id="73355-104">Unity 中的相機</span><span class="sxs-lookup"><span data-stu-id="73355-104">Camera in Unity</span></span>

<span data-ttu-id="73355-105">當您磨損混合現實耳機時，它就會變成您的全像世界的中心。</span><span class="sxs-lookup"><span data-stu-id="73355-105">When you wear a mixed reality headset, it becomes the center of your holographic world.</span></span> <span data-ttu-id="73355-106">Unity [攝影機](https://docs.unity3d.com/Manual/class-Camera.html) 元件會自動處理 stereoscopic 轉譯，並遵循您的頭部移動和旋轉。</span><span class="sxs-lookup"><span data-stu-id="73355-106">The Unity [Camera](https://docs.unity3d.com/Manual/class-Camera.html) component will automatically handle stereoscopic rendering and follow your head movement and rotation.</span></span> <span data-ttu-id="73355-107">不過，若要充分優化視覺品質和全像全像的 [穩定性](../platform-capabilities-and-apis/hologram-stability.md)，您應該設定如下所述的相機設定。</span><span class="sxs-lookup"><span data-stu-id="73355-107">However, to fully optimize visual quality and [hologram stability](../platform-capabilities-and-apis/hologram-stability.md), you should set the camera settings described below.</span></span>

## <a name="setup"></a><span data-ttu-id="73355-108">安裝程式</span><span class="sxs-lookup"><span data-stu-id="73355-108">Setup</span></span>

1. <span data-ttu-id="73355-109">移至 **Windows Store Player 設定** 的 [**其他設定**] 區段</span><span class="sxs-lookup"><span data-stu-id="73355-109">Go to **Other Settings** section of the **Windows Store Player Settings**</span></span>
2. <span data-ttu-id="73355-110">選擇 [ **Windows Mixed Reality** ] 作為裝置，可能會列為舊版 Unity 的 **Windows** 全像攝影版</span><span class="sxs-lookup"><span data-stu-id="73355-110">Choose **Windows Mixed Reality** as the device, which may be listed as **Windows Holographic** in older versions of Unity</span></span>
3. <span data-ttu-id="73355-111">選取 **支援的虛擬實境**</span><span class="sxs-lookup"><span data-stu-id="73355-111">Select **Virtual Reality Supported**</span></span>

>[!NOTE]
><span data-ttu-id="73355-112">這些設定必須套用至應用程式每個場景中的相機。</span><span class="sxs-lookup"><span data-stu-id="73355-112">These settings need to be applied to the Camera in each scene of your app.</span></span>
>
><span data-ttu-id="73355-113">依預設，當您在 Unity 中建立新場景時，它會包含階層中的主要攝影機 GameObject，其中包括相機元件，但未正確套用下列設定。</span><span class="sxs-lookup"><span data-stu-id="73355-113">By default, when you create a new scene in Unity, it will contain a Main Camera GameObject in the Hierarchy which includes the Camera component, but does not have the settings below properly applied.</span></span>

## <a name="holographic-vs-immersive-headsets"></a><span data-ttu-id="73355-114">全像沉浸式耳機</span><span class="sxs-lookup"><span data-stu-id="73355-114">Holographic vs. immersive headsets</span></span>

<span data-ttu-id="73355-115">Unity 攝影機元件上的預設設定適用于傳統3D 應用程式，因為它們沒有真實世界，所以需要像 skybox 的背景。</span><span class="sxs-lookup"><span data-stu-id="73355-115">The default settings on the Unity Camera component are for traditional 3D applications, which need a skybox-like background as they don't have a real world.</span></span>

* <span data-ttu-id="73355-116">在 **[沉浸式耳機](../../discover/immersive-headset-hardware-details.md)** 上執行時，您正在轉譯使用者看到的所有內容，因此您可能會想要保留 skybox。</span><span class="sxs-lookup"><span data-stu-id="73355-116">When running on an **[immersive headset](../../discover/immersive-headset-hardware-details.md)**, you're rendering everything the user sees, and so you'll likely want to keep the skybox.</span></span>
* <span data-ttu-id="73355-117">不過，在 [HoloLens](/hololens/hololens1-hardware)這類的全像攝影 **耳機** 上執行時，真實世界應該會出現在相機轉譯的所有內容後方。</span><span class="sxs-lookup"><span data-stu-id="73355-117">However, when running on a **holographic headset** like [HoloLens](/hololens/hololens1-hardware), the real world should appear behind everything the camera renders.</span></span> <span data-ttu-id="73355-118">將攝影機背景設定為 HoloLens (在 HoloLens 中，黑色呈現為透明) ，而不是 Skybox 材質：</span><span class="sxs-lookup"><span data-stu-id="73355-118">Set the camera background to be transparent (in HoloLens, black renders as transparent) instead of a Skybox texture:</span></span>
    1. <span data-ttu-id="73355-119">選取階層面板中的主要攝影機</span><span class="sxs-lookup"><span data-stu-id="73355-119">Select the Main Camera in the Hierarchy panel</span></span>
    2. <span data-ttu-id="73355-120">在 [檢查] 面板中，尋找相機元件，並將 [清除旗標] 下拉式清單從 [Skybox] 變更為 [純色]</span><span class="sxs-lookup"><span data-stu-id="73355-120">In the Inspector panel, find the Camera component and change the Clear Flags dropdown from Skybox to Solid Color</span></span>
    3. <span data-ttu-id="73355-121">選取背景色彩選擇器，並將 RGBA 值變更為 (0、0、0、0) </span><span class="sxs-lookup"><span data-stu-id="73355-121">Select the Background color picker and change the RGBA values to (0, 0, 0, 0)</span></span>

<span data-ttu-id="73355-122">您可以藉由檢查 [HolographicSettings IsDisplayOpaque](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.IsDisplayOpaque.html)，使用腳本來判斷耳機是否為沉浸式或全像攝影。</span><span class="sxs-lookup"><span data-stu-id="73355-122">You can use script code to determine at runtime whether the headset is immersive or holographic by checking [HolographicSettings.IsDisplayOpaque](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.IsDisplayOpaque.html).</span></span>

## <a name="positioning-the-camera"></a><span data-ttu-id="73355-123">定位相機</span><span class="sxs-lookup"><span data-stu-id="73355-123">Positioning the Camera</span></span>

<span data-ttu-id="73355-124">如果您想像使用者的開始位置是 (X：0，Y：0，Z： 0) ，將會比較容易配置您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="73355-124">It will be easier to lay out your app if you imagine the starting position of the user as (X: 0, Y: 0, Z: 0).</span></span> <span data-ttu-id="73355-125">因為主要攝影機正在追蹤使用者的標頭移動，所以可以設定主要攝影機的開始位置來設定使用者的開始位置。</span><span class="sxs-lookup"><span data-stu-id="73355-125">Since the Main Camera is tracking movement of the user's head, the starting position of the user can be set by setting the starting position of the Main Camera.</span></span>

1. <span data-ttu-id="73355-126">選取 [階層] 面板中的 [主要攝影機]</span><span class="sxs-lookup"><span data-stu-id="73355-126">Select Main Camera in the Hierarchy panel</span></span>
2. <span data-ttu-id="73355-127">在 [偵測器] 面板中，尋找 [轉換] 元件，並將位置從 (X：0，Y：1，Z：-10) 變更為 (X：0，Y：0，Z： 0) </span><span class="sxs-lookup"><span data-stu-id="73355-127">In the Inspector panel, find the Transform component and change the Position from (X: 0, Y: 1, Z: -10) to (X: 0, Y: 0, Z: 0)</span></span>

   <span data-ttu-id="73355-128">![Unity 中的 [偵測器] 窗格中的相機](images/maincamera-350px.png)</span><span class="sxs-lookup"><span data-stu-id="73355-128">![Camera in the Inspector pane in Unity](images/maincamera-350px.png)</span></span>  
   <span data-ttu-id="73355-129">*Unity 中的 [偵測器] 窗格中的相機*</span><span class="sxs-lookup"><span data-stu-id="73355-129">*Camera in the Inspector pane in Unity*</span></span>

## <a name="clip-planes"></a><span data-ttu-id="73355-130">剪輯平面</span><span class="sxs-lookup"><span data-stu-id="73355-130">Clip planes</span></span>

<span data-ttu-id="73355-131">轉譯內容太接近使用者可能會對混合現實感到不舒服。</span><span class="sxs-lookup"><span data-stu-id="73355-131">Rendering content too close to the user can be uncomfortable in mixed reality.</span></span> <span data-ttu-id="73355-132">您可以調整攝影機元件上的 [近距離和目前的剪切平面](../platform-capabilities-and-apis/hologram-stability.md#hologram-render-distances) 。</span><span class="sxs-lookup"><span data-stu-id="73355-132">You can adjust the [near and far clip planes](../platform-capabilities-and-apis/hologram-stability.md#hologram-render-distances) on the Camera component.</span></span>

1. <span data-ttu-id="73355-133">選取階層面板中的主要攝影機</span><span class="sxs-lookup"><span data-stu-id="73355-133">Select the Main Camera in the Hierarchy panel</span></span>
2. <span data-ttu-id="73355-134">在 [偵測器] 面板中，尋找相機元件裁剪平面，然後將近端 textbox 從0.3 變更為0.85。</span><span class="sxs-lookup"><span data-stu-id="73355-134">In the Inspector panel, find the Camera component Clipping Planes and change the Near textbox from 0.3 to 0.85.</span></span> <span data-ttu-id="73355-135">更深入轉譯的內容可能會導致使用者不適感，而且應該根據轉譯 [距離指導方針](../platform-capabilities-and-apis/hologram-stability.md#hologram-render-distances)來避免。</span><span class="sxs-lookup"><span data-stu-id="73355-135">Content rendered even closer can lead to user discomfort and should be avoided per the [render distance guidelines](../platform-capabilities-and-apis/hologram-stability.md#hologram-render-distances).</span></span>

## <a name="multiple-cameras"></a><span data-ttu-id="73355-136">多個相機</span><span class="sxs-lookup"><span data-stu-id="73355-136">Multiple Cameras</span></span>

<span data-ttu-id="73355-137">當場景中有多個相機元件時，Unity 會根據哪些 GameObject 具有 MainCamera 標籤，知道要使用哪一種相機來進行 stereoscopic 轉譯和前端追蹤。</span><span class="sxs-lookup"><span data-stu-id="73355-137">When there are multiple Camera components in the scene, Unity knows which camera to use for stereoscopic rendering and head tracking based on which GameObject has the MainCamera tag.</span></span>

## <a name="recentering-a-seated-experience"></a><span data-ttu-id="73355-138">Recentering 上一體驗</span><span class="sxs-lookup"><span data-stu-id="73355-138">Recentering a seated experience</span></span>

<span data-ttu-id="73355-139">如果您要建立 [大規模的體驗](../../design/coordinate-systems.md)，您可以藉由呼叫 XR，在使用者目前的標頭位置 recenter Unity 的世界原點 **[。InputTracking. Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)** 方法。</span><span class="sxs-lookup"><span data-stu-id="73355-139">If you're building a [seated-scale experience](../../design/coordinate-systems.md), you can recenter Unity's world origin at the user's current head position by calling the **[XR.InputTracking.Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)** method.</span></span>

## <a name="reprojection-modes"></a><span data-ttu-id="73355-140">Reprojection 模式</span><span class="sxs-lookup"><span data-stu-id="73355-140">Reprojection modes</span></span>

<span data-ttu-id="73355-141">HoloLens 和沉浸式耳機都會 reproject 您的應用程式所轉譯的每個畫面格，以在發出光子時，針對使用者的實際標上任何 misprediction 進行調整。</span><span class="sxs-lookup"><span data-stu-id="73355-141">Both HoloLens and immersive headsets will reproject each frame your app renders to adjust for any misprediction of the user's actual head position when photons are emitted.</span></span>

<span data-ttu-id="73355-142">依照預設：</span><span class="sxs-lookup"><span data-stu-id="73355-142">By default:</span></span>

* <span data-ttu-id="73355-143">如果應用程式為指定的框架提供深度緩衝區，則 **沉浸式耳機** 會負責定位 reprojection。</span><span class="sxs-lookup"><span data-stu-id="73355-143">**Immersive headsets** will take care of positional reprojection if the app provides a depth buffer for a given frame.</span></span> <span data-ttu-id="73355-144">沉浸式耳機也會調整您的全像位置和方向的 misprediction。</span><span class="sxs-lookup"><span data-stu-id="73355-144">Immersive headsets will also adjust your holograms for misprediction in both position and orientation.</span></span> <span data-ttu-id="73355-145">如果未提供深度緩衝區，則系統只會正確地校正 mispredictions。</span><span class="sxs-lookup"><span data-stu-id="73355-145">If a depth buffer isn't provided, the system will only correct mispredictions in orientation.</span></span>
* <span data-ttu-id="73355-146">HoloLens **這類的** 全像像一樣，無論應用程式是否提供深度緩衝區，都將負責定位 reprojection。</span><span class="sxs-lookup"><span data-stu-id="73355-146">**Holographic headsets** like HoloLens will take care of positional reprojection whether the app provides its depth buffer or not.</span></span>  <span data-ttu-id="73355-147">在 HoloLens 上可能沒有深度緩衝區的位置 reprojection，因為轉譯通常會因為真實世界提供的穩定背景而稀疏。</span><span class="sxs-lookup"><span data-stu-id="73355-147">Positional reprojection is possible without depth buffers on HoloLens as rendering is often sparse with a stable background provided by the real world.</span></span>

<span data-ttu-id="73355-148">如果您知道您要使用嚴格的主體鎖定內容來建立 [僅限方向的體驗](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience) (例如，360度的影片內容) ，您可以將 reprojection 模式明確地設定為方向，只要將 [HolographicSettings](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.ReprojectionMode.html) 設定為 [HolographicReprojectionMode. OrientationOnly](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.HolographicReprojectionMode.html)。</span><span class="sxs-lookup"><span data-stu-id="73355-148">If you know that you're building an [orientation-only experience](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience) with rigidly body-locked content (for example, 360-degree video content), you can explicitly set the reprojection mode to orientation only by setting [HolographicSettings.ReprojectionMode](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.ReprojectionMode.html) to [HolographicReprojectionMode.OrientationOnly](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.HolographicReprojectionMode.html).</span></span>

## <a name="sharing-your-depth-buffers-with-windows"></a><span data-ttu-id="73355-149">使用 Windows 共用深度緩衝區</span><span class="sxs-lookup"><span data-stu-id="73355-149">Sharing your depth buffers with Windows</span></span>

<span data-ttu-id="73355-150">將您的應用程式深度緩衝區共用到 Windows 每個畫面格，將會根據您要轉譯的耳機類型，為您的應用程式提供兩個最多的全像全像全像全像：</span><span class="sxs-lookup"><span data-stu-id="73355-150">Sharing your app's depth buffer to Windows each frame will give your app one of two boosts in hologram stability, based on the type of headset you're rendering for:</span></span>

* <span data-ttu-id="73355-151">當提供深度緩衝區時，**沉浸式耳機** 可以處理位置 reprojection，調整您的全像位置和方向的 misprediction。</span><span class="sxs-lookup"><span data-stu-id="73355-151">**Immersive headsets** can take care of positional reprojection when a depth buffer is provided, adjusting your holograms for misprediction in both position and orientation.</span></span>
* <span data-ttu-id="73355-152">全像 **耳機** 有幾種不同的方法。</span><span class="sxs-lookup"><span data-stu-id="73355-152">**Holographic headsets** have a few different methods.</span></span> <span data-ttu-id="73355-153">當提供深度緩衝區時，HoloLens 1 會自動選取 [焦點點](focus-point-in-unity.md) ，並在與大部分內容交集的平面上優化全像影像穩定性。</span><span class="sxs-lookup"><span data-stu-id="73355-153">HoloLens 1 will automatically select a [focus point](focus-point-in-unity.md) when a depth buffer is provided, optimizing hologram stability along the plane that intersects the most content.</span></span> <span data-ttu-id="73355-154">HoloLens 2 將會使用深度 LSR 來穩定內容 [ (請參閱備註) ](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint)。</span><span class="sxs-lookup"><span data-stu-id="73355-154">HoloLens 2 will stabilize content using [Depth LSR (see Remarks)](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint).</span></span>

<span data-ttu-id="73355-155">設定您的 Unity 應用程式是否會提供 Windows 的深度緩衝區：</span><span class="sxs-lookup"><span data-stu-id="73355-155">To set whether your Unity app will provide a depth buffer to Windows:</span></span>

1. <span data-ttu-id="73355-156">移至 [**編輯**  >  **專案設定**  >  **播放機**  >  **] 通用 Windows 平臺** 索引標籤  >  **XR 設定**]。</span><span class="sxs-lookup"><span data-stu-id="73355-156">Go to **Edit** > **Project Settings** > **Player** > **Universal Windows Platform tab** > **XR Settings**.</span></span>
2. <span data-ttu-id="73355-157">展開 **WINDOWS MIXED REALITY SDK** 專案。</span><span class="sxs-lookup"><span data-stu-id="73355-157">Expand the **Windows Mixed Reality SDK** item.</span></span>
3. <span data-ttu-id="73355-158">核取或取消核取 [ **啟用深度緩衝區共用** ] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="73355-158">Check or uncheck the **Enable Depth Buffer Sharing** check box.</span></span>  <span data-ttu-id="73355-159">預設會在新的專案中核取 [啟用深度緩衝區共用]，因為這項功能已新增至 Unity，而且預設會針對已升級的舊專案取消核取。</span><span class="sxs-lookup"><span data-stu-id="73355-159">Enable Depth Buffer Sharing is checked by default in new projects, since this feature was added to Unity and will be unchecked by default for older projects that were upgraded.</span></span>

<span data-ttu-id="73355-160">深度緩衝區可以改善視覺品質，只要 Windows 可以精確地將深度緩衝區中的正規化的每個圖元深度值對應到量值，就可以使用您在主要攝影機上的 Unity 中所設定的近距離和最遠的平面。</span><span class="sxs-lookup"><span data-stu-id="73355-160">A depth buffer can improve visual quality so long as Windows can accurately map the normalized per-pixel depth values in your depth buffer back to distances in meters, using the near and far planes you've set in Unity on the main camera.</span></span>  <span data-ttu-id="73355-161">如果您的轉譯階段以一般方式處理深度值，您通常應該會在這裡進行，不過在顯示到現有的色彩圖元時，透明轉譯會寫入深度緩衝區的行程可能會使 reprojection 混淆。</span><span class="sxs-lookup"><span data-stu-id="73355-161">If your render passes handle depth values in typical ways, you should generally be fine here, though translucent render passes that write to the depth buffer while showing through to existing color pixels can confuse the reprojection.</span></span>  <span data-ttu-id="73355-162">如果您知道您的轉譯行程將會離開許多具有不正確深度值的最終深度圖元，您可能會藉由取消核取 [啟用深度緩衝區共用]，以取得更佳的視覺品質。</span><span class="sxs-lookup"><span data-stu-id="73355-162">If you know that your render passes will leave many of your final depth pixels with inaccurate depth values, you are likely to get better visual quality by unchecking "Enable Depth Buffer Sharing".</span></span>

## <a name="automatic-scene-and-camera-setup-with-mixed-reality-toolkit"></a><span data-ttu-id="73355-163">使用混合現實工具組的自動場景和攝影機設定</span><span class="sxs-lookup"><span data-stu-id="73355-163">Automatic Scene and Camera Setup with Mixed Reality Toolkit</span></span> 

<span data-ttu-id="73355-164">遵循 [逐步](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html) 指南，將混合現實工具組新增至 Unity 專案，它將會自動設定您的專案。</span><span class="sxs-lookup"><span data-stu-id="73355-164">Follow the [step-by-step](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html) guide to add Mixed Reality Toolkit to your Unity project and it will configure your project automatically.</span></span> <span data-ttu-id="73355-165">您也可以使用下一節中的指南，手動設定沒有 MRTK 的專案。</span><span class="sxs-lookup"><span data-stu-id="73355-165">You can also manually configure the project without MRTK with the guide in the section below.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="73355-166">下一個開發檢查點</span><span class="sxs-lookup"><span data-stu-id="73355-166">Next Development Checkpoint</span></span>

<span data-ttu-id="73355-167">如果您是遵循我們所配置的 Unity 開發旅程，您將會在探索 MRTK 核心構成要素的過程中進行。</span><span class="sxs-lookup"><span data-stu-id="73355-167">If you're following the Unity development journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="73355-168">接下來，您可以繼續進行下一個建置組塊：</span><span class="sxs-lookup"><span data-stu-id="73355-168">From here, you can continue to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="73355-169">目光</span><span class="sxs-lookup"><span data-stu-id="73355-169">Gaze</span></span>](gaze-in-unity.md)

<span data-ttu-id="73355-170">或者，直接跳到混合實境平台功能和 API 的主題：</span><span class="sxs-lookup"><span data-stu-id="73355-170">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="73355-171">共用體驗</span><span class="sxs-lookup"><span data-stu-id="73355-171">Shared experiences</span></span>](shared-experiences-in-unity.md)

<span data-ttu-id="73355-172">您可以隨時回到 [Unity 開發檢查點](unity-development-overview.md#2-core-building-blocks)。</span><span class="sxs-lookup"><span data-stu-id="73355-172">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="73355-173">另請參閱</span><span class="sxs-lookup"><span data-stu-id="73355-173">See also</span></span>

* [<span data-ttu-id="73355-174">全像投影穩定性</span><span class="sxs-lookup"><span data-stu-id="73355-174">Hologram stability</span></span>](../platform-capabilities-and-apis/hologram-stability.md)
* [<span data-ttu-id="73355-175">MixedRealityToolkit 主要攝影機. 預製專案</span><span class="sxs-lookup"><span data-stu-id="73355-175">MixedRealityToolkit Main Camera.prefab</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Input/Prefabs)