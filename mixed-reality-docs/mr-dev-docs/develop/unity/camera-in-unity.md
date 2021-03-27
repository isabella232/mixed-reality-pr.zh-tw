---
title: Unity 中的攝影機設定
description: 瞭解如何設定及使用 Unity 的主要攝影機進行 Windows Mixed Reality 開發以進行全像轉譯。
author: keveleigh
ms.author: kurtie
ms.date: 03/25/2021
ms.topic: article
keywords: holotoolkit，mixedrealitytoolkit，mixedrealitytoolkit-unity，全像轉譯，全像全像，全像投影、全像投影、聚焦點、深度緩衝區、僅限方向、位置、不透明、透明、剪輯、混合現實耳機、windows mixed reality 耳機、虛擬實境耳機
ms.openlocfilehash: d3f69c6cf1889587b23b68259f22b34b89b925a4
ms.sourcegitcommit: 0db5777954697f1d738469363bbf385481204d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/27/2021
ms.locfileid: "105636268"
---
# <a name="camera-setup-in-unity"></a><span data-ttu-id="f9724-104">Unity 中的攝影機設定</span><span class="sxs-lookup"><span data-stu-id="f9724-104">Camera setup in Unity</span></span>

<span data-ttu-id="f9724-105">當您磨損混合現實耳機時，它就會變成您的全像世界的中心。</span><span class="sxs-lookup"><span data-stu-id="f9724-105">When you wear a mixed reality headset, it becomes the center of your holographic world.</span></span> <span data-ttu-id="f9724-106">Unity [攝影機](https://docs.unity3d.com/Manual/class-Camera.html) 元件會自動處理 stereoscopic 轉譯，並遵循您的頭部移動和旋轉。</span><span class="sxs-lookup"><span data-stu-id="f9724-106">The Unity [Camera](https://docs.unity3d.com/Manual/class-Camera.html) component will automatically handle stereoscopic rendering and follow your head movement and rotation.</span></span> <span data-ttu-id="f9724-107">不過，若要充分優化視覺品質和全像全像的 [穩定性](../platform-capabilities-and-apis/hologram-stability.md)，您應該設定如下所述的相機設定。</span><span class="sxs-lookup"><span data-stu-id="f9724-107">However, to fully optimize visual quality and [hologram stability](../platform-capabilities-and-apis/hologram-stability.md), you should set the camera settings described below.</span></span>

## <a name="hololens-vs-vr-immersive-headsets"></a><span data-ttu-id="f9724-108">HoloLens 與 VR 沉浸式耳機</span><span class="sxs-lookup"><span data-stu-id="f9724-108">HoloLens vs VR immersive headsets</span></span>

<span data-ttu-id="f9724-109">Unity 攝影機元件上的預設設定適用于傳統3D 應用程式，因為它們沒有真實世界，所以需要像 skybox 的背景。</span><span class="sxs-lookup"><span data-stu-id="f9724-109">The default settings on the Unity Camera component are for traditional 3D applications, which need a skybox-like background as they don't have a real world.</span></span>

* <span data-ttu-id="f9724-110">在 **[沉浸式耳機](../../discover/immersive-headset-hardware-details.md)** 上執行時，您正在轉譯使用者看到的所有內容，因此您可能會想要保留 skybox。</span><span class="sxs-lookup"><span data-stu-id="f9724-110">When running on an **[immersive headset](../../discover/immersive-headset-hardware-details.md)**, you're rendering everything the user sees, and so you'll likely want to keep the skybox.</span></span>
* <span data-ttu-id="f9724-111">不過，在 [HoloLens](/hololens/hololens2-hardware)這類的全像攝影 **耳機** 上執行時，真實世界應該會出現在相機轉譯的所有內容後方。</span><span class="sxs-lookup"><span data-stu-id="f9724-111">However, when running on a **holographic headset** like [HoloLens](/hololens/hololens2-hardware), the real world should appear behind everything the camera renders.</span></span> <span data-ttu-id="f9724-112">將攝影機背景設定為 HoloLens (在 HoloLens 中，黑色呈現為透明) ，而不是 Skybox 材質：</span><span class="sxs-lookup"><span data-stu-id="f9724-112">Set the camera background to be transparent (in HoloLens, black renders as transparent) instead of a Skybox texture:</span></span>
    1. <span data-ttu-id="f9724-113">選取階層面板中的主要攝影機</span><span class="sxs-lookup"><span data-stu-id="f9724-113">Select the Main Camera in the Hierarchy panel</span></span>
    2. <span data-ttu-id="f9724-114">在 [檢查] 面板中，尋找相機元件，並將 [清除旗標] 下拉式清單從 [Skybox] 變更為 [純色]</span><span class="sxs-lookup"><span data-stu-id="f9724-114">In the Inspector panel, find the Camera component and change the Clear Flags dropdown from Skybox to Solid Color</span></span>
    3. <span data-ttu-id="f9724-115">選取背景色彩選擇器，並將 RGBA 值變更為 (0、0、0、0) </span><span class="sxs-lookup"><span data-stu-id="f9724-115">Select the Background color picker and change the RGBA values to (0, 0, 0, 0)</span></span>
        1. <span data-ttu-id="f9724-116">如果從程式碼設定此值，您可以使用 Unity 的 [`Color.clear`](https://docs.unity3d.com/ScriptReference/Color-clear.html)</span><span class="sxs-lookup"><span data-stu-id="f9724-116">If setting this from code, you can use Unity's [`Color.clear`](https://docs.unity3d.com/ScriptReference/Color-clear.html)</span></span>

[!INCLUDE[](includes/camera/opaque-camera-include.md)]

## <a name="camera-setup"></a><span data-ttu-id="f9724-117">相機設定</span><span class="sxs-lookup"><span data-stu-id="f9724-117">Camera setup</span></span>

<span data-ttu-id="f9724-118">無論您正在開發何種體驗，主要攝影機一律是連接到您裝置之前端掛接顯示器的主要身歷聲轉譯元件。</span><span class="sxs-lookup"><span data-stu-id="f9724-118">Whatever kind of experience you're developing, the Main Camera is always the primary stereo rendering component attached to your device's head-mounted display.</span></span> <span data-ttu-id="f9724-119">如果您想像使用者的開始位置是 (X：0，Y：0，Z： 0) ，將會比較容易配置您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="f9724-119">It'll be easier to lay out your app if you imagine the starting position of the user as (X: 0, Y: 0, Z: 0).</span></span> <span data-ttu-id="f9724-120">因為主要攝影機正在追蹤使用者的標頭移動，所以可以設定主要攝影機的開始位置來設定使用者的開始位置。</span><span class="sxs-lookup"><span data-stu-id="f9724-120">Since the Main Camera is tracking movement of the user's head, the starting position of the user can be set by setting the starting position of the Main Camera.</span></span>

<span data-ttu-id="f9724-121">您需要做的主要選擇是您是要針對 HoloLens 或 VR 沉浸式耳機進行開發。</span><span class="sxs-lookup"><span data-stu-id="f9724-121">The central choice you need to make is whether you're developing for HoloLens or VR immersive headsets.</span></span> <span data-ttu-id="f9724-122">當您取得該內容之後，請跳至適用的任何安裝程式區段。</span><span class="sxs-lookup"><span data-stu-id="f9724-122">Once you've got that, skip to whichever setup section applies.</span></span>

### <a name="hololens-camera-setup"></a><span data-ttu-id="f9724-123">HoloLens 攝影機設定</span><span class="sxs-lookup"><span data-stu-id="f9724-123">HoloLens camera setup</span></span>

<span data-ttu-id="f9724-124">針對 HoloLens 應用程式，您必須針對想要鎖定場景環境的任何物件使用錨點。</span><span class="sxs-lookup"><span data-stu-id="f9724-124">For HoloLens apps, you need to use anchors for any objects you want to lock to the scene environment.</span></span> <span data-ttu-id="f9724-125">我們建議使用未系結的空間來最大化穩定性，並在多個房間內建立錨點。</span><span class="sxs-lookup"><span data-stu-id="f9724-125">We recommend using unbounded space to maximize stability and create anchors in multiple rooms.</span></span>

[!INCLUDE[](includes/camera/hololens-setup-include.md)]

### <a name="vr-camera-setup"></a><span data-ttu-id="f9724-126">VR 攝影機設定</span><span class="sxs-lookup"><span data-stu-id="f9724-126">VR camera setup</span></span>

<span data-ttu-id="f9724-127">Windows Mixed Reality 透過房間規模的應用程式，支援橫跨各種 [體驗規模](../../design/coordinate-systems.md#mixed-reality-experience-scales)的應用程式，從僅限方向和已安置規模的應用程式。</span><span class="sxs-lookup"><span data-stu-id="f9724-127">Windows Mixed Reality supports apps across a wide range of [experience scales](../../design/coordinate-systems.md#mixed-reality-experience-scales), from orientation-only and seated-scale apps up through room-scale apps.</span></span> <span data-ttu-id="f9724-128">在 HoloLens 上，您可以進一步建立全球規模的應用程式，讓使用者超越5個計量，探索整個大樓的整個樓層。</span><span class="sxs-lookup"><span data-stu-id="f9724-128">On HoloLens, you can go further and build world-scale apps that let users walk beyond 5 meters, exploring an entire floor of a building and beyond.</span></span>

<span data-ttu-id="f9724-129">在 Unity 中打造混合現實體驗的第一步，是要判斷您的應用程式將設為目標的 [體驗調整](../../design/coordinate-systems.md) ：</span><span class="sxs-lookup"><span data-stu-id="f9724-129">Your first step in building a mixed reality experience in Unity is to determine which [experience scale](../../design/coordinate-systems.md) your app will target:</span></span>

* [<span data-ttu-id="f9724-130">方向或固定規模</span><span class="sxs-lookup"><span data-stu-id="f9724-130">Orientation or seated-scale</span></span>](../../design/coordinate-systems.md#building-an-orientation-only-or-seated-scale-experience)
* [<span data-ttu-id="f9724-131">站上或房間規模</span><span class="sxs-lookup"><span data-stu-id="f9724-131">Standing or room-scale</span></span>](../../design/coordinate-systems.md#building-a-standing-scale-or-room-scale-experience)
* [<span data-ttu-id="f9724-132">全球規模</span><span class="sxs-lookup"><span data-stu-id="f9724-132">World-scale</span></span>](../../design/coordinate-systems.md#building-a-world-scale-experience)

#### <a name="room-scale-or-standing-experiences"></a><span data-ttu-id="f9724-133">會議室規模或長期體驗</span><span class="sxs-lookup"><span data-stu-id="f9724-133">Room-scale or standing experiences</span></span>

> [!NOTE]
> <span data-ttu-id="f9724-134">如果您正在建立 HL2，我們建議您建立眼睛層級的體驗，或考慮使用 [場景理解](../platform-capabilities-and-apis/scene-understanding-sdk.md) ，以瞭解場景的樓層原因。</span><span class="sxs-lookup"><span data-stu-id="f9724-134">If you're building for HL2, we recommend creating an eye-level experience, or consider using [Scene Understanding](../platform-capabilities-and-apis/scene-understanding-sdk.md) to reason about the floor of your scene.</span></span>

[!INCLUDE[](includes/camera/vr-setup-standing-include.md)]

#### <a name="seated-experiences"></a><span data-ttu-id="f9724-135">上一位體驗</span><span class="sxs-lookup"><span data-stu-id="f9724-135">Seated experiences</span></span>

[!INCLUDE[](includes/camera/vr-setup-seated-include.md)]

### <a name="setting-up-the-camera-background"></a><span data-ttu-id="f9724-136">設定相機背景</span><span class="sxs-lookup"><span data-stu-id="f9724-136">Setting up the camera background</span></span>

<span data-ttu-id="f9724-137">如果您使用的是 MRTK，則會自動設定並管理相機的背景。</span><span class="sxs-lookup"><span data-stu-id="f9724-137">If you're using MRTK, the camera's background is automatically configured and managed.</span></span> <span data-ttu-id="f9724-138">針對 XR SDK 或舊版的 WSA 專案，建議您在 HoloLens 上將攝影機的背景設定為純黑色，並保留 skybox 的 VR。</span><span class="sxs-lookup"><span data-stu-id="f9724-138">For XR SDK or Legacy WSA projects, we recommend setting the camera's background to solid black on HoloLens and keeping the skybox for VR.</span></span>

## <a name="using-multiple-cameras"></a><span data-ttu-id="f9724-139">使用多個相機</span><span class="sxs-lookup"><span data-stu-id="f9724-139">Using multiple cameras</span></span>

<span data-ttu-id="f9724-140">當場景中有多個相機元件時，Unity 會根據哪一個 GameObject 具有 MainCamera 標記來得知要使用的相機來進行 stereoscopic 轉譯。</span><span class="sxs-lookup"><span data-stu-id="f9724-140">When there are multiple Camera components in the scene, Unity knows which camera to use for stereoscopic rendering based on which GameObject has the MainCamera tag.</span></span> <span data-ttu-id="f9724-141">在舊版 XR 中，它也會使用此標記來同步處理標頭追蹤。</span><span class="sxs-lookup"><span data-stu-id="f9724-141">In legacy XR, it also uses this tag to sync head tracking.</span></span> <span data-ttu-id="f9724-142">在 XR SDK 中，head 追蹤是由附加至相機的 TrackedPoseDriver 腳本驅動。</span><span class="sxs-lookup"><span data-stu-id="f9724-142">In XR SDK, head tracking is driven by a TrackedPoseDriver script attached to the camera.</span></span>

## <a name="sharing-depth-buffers"></a><span data-ttu-id="f9724-143">共用深度緩衝區</span><span class="sxs-lookup"><span data-stu-id="f9724-143">Sharing depth buffers</span></span>

<span data-ttu-id="f9724-144">將您的應用程式深度緩衝區共用到 Windows 每個畫面格，將會根據您要轉譯的耳機類型，為您的應用程式提供兩個最多的全像全像全像全像：</span><span class="sxs-lookup"><span data-stu-id="f9724-144">Sharing your app's depth buffer to Windows each frame will give your app one of two boosts in hologram stability, based on the type of headset you're rendering for:</span></span>

* <span data-ttu-id="f9724-145">當提供深度緩衝區時， **VR 沉浸式耳機** 可以處理位置 reprojection，調整您的全像位置和方向的 misprediction。</span><span class="sxs-lookup"><span data-stu-id="f9724-145">**VR immersive headsets** can take care of positional reprojection when a depth buffer is provided, adjusting your holograms for misprediction in both position and orientation.</span></span>
* <span data-ttu-id="f9724-146">**HoloLens 耳機** 有幾種不同的方法。</span><span class="sxs-lookup"><span data-stu-id="f9724-146">**HoloLens headsets** have a few different methods.</span></span> <span data-ttu-id="f9724-147">當提供深度緩衝區時，HoloLens 1 會自動選取 [焦點點](focus-point-in-unity.md) ，並在與大部分內容交集的平面上優化全像影像穩定性。</span><span class="sxs-lookup"><span data-stu-id="f9724-147">HoloLens 1 will automatically select a [focus point](focus-point-in-unity.md) when a depth buffer is provided, optimizing hologram stability along the plane that intersects the most content.</span></span> <span data-ttu-id="f9724-148">HoloLens 2 將會使用深度 LSR 來穩定內容 [ (請參閱備註) ](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint)。</span><span class="sxs-lookup"><span data-stu-id="f9724-148">HoloLens 2 will stabilize content using [Depth LSR (see Remarks)](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint).</span></span>

[!INCLUDE[](includes/camera/depth-buffer-include.md)]

## <a name="using-clipping-planes"></a><span data-ttu-id="f9724-149">使用裁剪平面</span><span class="sxs-lookup"><span data-stu-id="f9724-149">Using clipping planes</span></span>

<span data-ttu-id="f9724-150">轉譯內容太接近使用者可能會對混合現實感到不舒服。</span><span class="sxs-lookup"><span data-stu-id="f9724-150">Rendering content too close to the user can be uncomfortable in mixed reality.</span></span> <span data-ttu-id="f9724-151">您可以調整攝影機元件上的 [近距離和目前的剪切平面](../platform-capabilities-and-apis/hologram-stability.md#hologram-render-distances) 。</span><span class="sxs-lookup"><span data-stu-id="f9724-151">You can adjust the [near and far clip planes](../platform-capabilities-and-apis/hologram-stability.md#hologram-render-distances) on the Camera component.</span></span>

1. <span data-ttu-id="f9724-152">選取 **階層面板中的\*\*\*\*主要攝影機**</span><span class="sxs-lookup"><span data-stu-id="f9724-152">Select the **Main Camera** in the **Hierarchy** panel</span></span>
2. <span data-ttu-id="f9724-153">在 [偵測 **器** ] 面板中，尋找 **相機** 元件 **裁剪平面** ，然後將 **近端** textbox 從 **0.3** 變更為 **0.85**。</span><span class="sxs-lookup"><span data-stu-id="f9724-153">In the **Inspector** panel, find the **Camera** component **Clipping Planes** and change the **Near** textbox from **0.3** to **0.85**.</span></span> <span data-ttu-id="f9724-154">更深入轉譯的內容可能會導致使用者不適感，而且應該根據轉譯 [距離指導方針](../platform-capabilities-and-apis/hologram-stability.md#hologram-render-distances)來避免。</span><span class="sxs-lookup"><span data-stu-id="f9724-154">Content rendered even closer can lead to user discomfort and should be avoided per the [render distance guidelines](../platform-capabilities-and-apis/hologram-stability.md#hologram-render-distances).</span></span>

## <a name="recentering-the-camera"></a><span data-ttu-id="f9724-155">Recentering 攝影機</span><span class="sxs-lookup"><span data-stu-id="f9724-155">Recentering the camera</span></span>

<span data-ttu-id="f9724-156">如果您要建立 [大規模的體驗](../../design/coordinate-systems.md)，您可以藉由呼叫 XR，在使用者目前的標頭位置 recenter Unity 的世界原點 **[。InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)** 在舊版 XR 中的 Recenter 方法或 TRYRECENTER SDK 中的 **[XRInputSubsystem. XR](https://docs.unity3d.com/ScriptReference/XR.XRInputSubsystem.TryRecenter.html)** 方法。</span><span class="sxs-lookup"><span data-stu-id="f9724-156">If you're building a [seated-scale experience](../../design/coordinate-systems.md), you can recenter Unity's world origin at the user's current head position by calling the **[XR.InputTracking.Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)** method in legacy XR or the **[XRInputSubsystem.TryRecenter](https://docs.unity3d.com/ScriptReference/XR.XRInputSubsystem.TryRecenter.html)** method in XR SDK.</span></span>

## <a name="teleportation"></a><span data-ttu-id="f9724-157">遙傳</span><span class="sxs-lookup"><span data-stu-id="f9724-157">Teleportation</span></span>

<span data-ttu-id="f9724-158">這項功能通常會保留給 VR 體驗：</span><span class="sxs-lookup"><span data-stu-id="f9724-158">This feature is typically reserved for VR experiences:</span></span>

[!INCLUDE[](includes/camera/teleport-include.md)]

## <a name="reprojection-modes"></a><span data-ttu-id="f9724-159">Reprojection 模式</span><span class="sxs-lookup"><span data-stu-id="f9724-159">Reprojection modes</span></span>

<span data-ttu-id="f9724-160">HoloLens 和沉浸式耳機都會 reproject 您的應用程式所轉譯的每個畫面格，以在發出光子時，針對使用者的實際標上任何 misprediction 進行調整。</span><span class="sxs-lookup"><span data-stu-id="f9724-160">Both HoloLens and immersive headsets will reproject each frame your app renders to adjust for any misprediction of the user's actual head position when photons are emitted.</span></span>

<span data-ttu-id="f9724-161">依照預設：</span><span class="sxs-lookup"><span data-stu-id="f9724-161">By default:</span></span>

* <span data-ttu-id="f9724-162">如果應用程式為指定的框架提供深度緩衝區，則 **VR 沉浸式耳機** 會負責定位 reprojection。</span><span class="sxs-lookup"><span data-stu-id="f9724-162">**VR immersive headsets** will take care of positional reprojection if the app provides a depth buffer for a given frame.</span></span> <span data-ttu-id="f9724-163">沉浸式耳機也會調整您的全像位置和方向的 misprediction。</span><span class="sxs-lookup"><span data-stu-id="f9724-163">Immersive headsets will also adjust your holograms for misprediction in both position and orientation.</span></span> <span data-ttu-id="f9724-164">如果未提供深度緩衝區，則系統只會正確地校正 mispredictions。</span><span class="sxs-lookup"><span data-stu-id="f9724-164">If a depth buffer isn't provided, the system will only correct mispredictions in orientation.</span></span>
* <span data-ttu-id="f9724-165">HoloLens 2 的全像 **耳機** 一樣，會負責處理應用程式是否提供深度緩衝區的位置 reprojection。</span><span class="sxs-lookup"><span data-stu-id="f9724-165">**Holographic headsets** like HoloLens 2 will take care of positional reprojection whether the app provides its depth buffer or not.</span></span> <span data-ttu-id="f9724-166">在 HoloLens 上可能沒有深度緩衝區的位置 reprojection，因為轉譯通常會因為真實世界提供的穩定背景而稀疏。</span><span class="sxs-lookup"><span data-stu-id="f9724-166">Positional reprojection is possible without depth buffers on HoloLens as rendering is often sparse with a stable background provided by the real world.</span></span>

[!INCLUDE[](includes/camera/reprojection-include.md)]

## <a name="next-development-checkpoint"></a><span data-ttu-id="f9724-167">下一個開發檢查點</span><span class="sxs-lookup"><span data-stu-id="f9724-167">Next Development Checkpoint</span></span>

<span data-ttu-id="f9724-168">如果您是遵循我們所配置的 Unity 開發旅程，您將會在探索 MRTK 核心構成要素的過程中進行。</span><span class="sxs-lookup"><span data-stu-id="f9724-168">If you're following the Unity development journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="f9724-169">接下來，您可以繼續進行下一個建置組塊：</span><span class="sxs-lookup"><span data-stu-id="f9724-169">From here, you can continue to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="f9724-170">目光</span><span class="sxs-lookup"><span data-stu-id="f9724-170">Gaze</span></span>](gaze-in-unity.md)

<span data-ttu-id="f9724-171">或者，直接跳到混合實境平台功能和 API 的主題：</span><span class="sxs-lookup"><span data-stu-id="f9724-171">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="f9724-172">共用體驗</span><span class="sxs-lookup"><span data-stu-id="f9724-172">Shared experiences</span></span>](shared-experiences-in-unity.md)

<span data-ttu-id="f9724-173">您可以隨時回到 [Unity 開發檢查點](unity-development-overview.md#2-core-building-blocks)。</span><span class="sxs-lookup"><span data-stu-id="f9724-173">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="f9724-174">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f9724-174">See also</span></span>

* [<span data-ttu-id="f9724-175">全像投影穩定性</span><span class="sxs-lookup"><span data-stu-id="f9724-175">Hologram stability</span></span>](../platform-capabilities-and-apis/hologram-stability.md)
* [<span data-ttu-id="f9724-176">體驗規模調整</span><span class="sxs-lookup"><span data-stu-id="f9724-176">Experience scales</span></span>](../../design/coordinate-systems.md#mixed-reality-experience-scales)
* [<span data-ttu-id="f9724-177">空間階段</span><span class="sxs-lookup"><span data-stu-id="f9724-177">Spatial stage</span></span>](../../design/coordinate-systems.md#stage-frame-of-reference)
* [<span data-ttu-id="f9724-178">Unity 中的追蹤遺失</span><span class="sxs-lookup"><span data-stu-id="f9724-178">Tracking loss in Unity</span></span>](tracking-loss-in-unity.md)
* [<span data-ttu-id="f9724-179">空間錨點</span><span class="sxs-lookup"><span data-stu-id="f9724-179">Spatial anchors</span></span>](../../design/spatial-anchors.md)
* [<span data-ttu-id="f9724-180">Unity 中的持續性</span><span class="sxs-lookup"><span data-stu-id="f9724-180">Persistence in Unity</span></span>](persistence-in-unity.md)
* [<span data-ttu-id="f9724-181">Unity 中的共用體驗</span><span class="sxs-lookup"><span data-stu-id="f9724-181">Shared experiences in Unity</span></span>](shared-experiences-in-unity.md)
* [<span data-ttu-id="f9724-182">Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="f9724-182">Azure Spatial Anchors</span></span>](/azure/spatial-anchors)
* [<span data-ttu-id="f9724-183">適用于 Unity 的 Azure 空間錨點 SDK</span><span class="sxs-lookup"><span data-stu-id="f9724-183">Azure Spatial Anchors SDK for Unity</span></span>](/dotnet/api/Microsoft.Azure.SpatialAnchors)