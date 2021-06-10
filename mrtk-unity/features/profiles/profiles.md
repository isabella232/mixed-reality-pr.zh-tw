---
title: Profiles
description: MRTK 中的檔設定檔
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、設定檔、
ms.openlocfilehash: 785d402e924a534627dfd1d742d2019d9ce9dd5a
ms.sourcegitcommit: 2f69fb62eb81f91e655d7b55306b0550a1162496
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/10/2021
ms.locfileid: "111908242"
---
# <a name="profiles"></a><span data-ttu-id="91ddc-104">Profiles</span><span class="sxs-lookup"><span data-stu-id="91ddc-104">Profiles</span></span>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Introduction-to-MRTK-Profiles/player]

<span data-ttu-id="91ddc-105">設定 MRTK 的主要方式之一是透過基礎套件中提供的設定檔。</span><span class="sxs-lookup"><span data-stu-id="91ddc-105">One of the main ways that the MRTK is configured is through the profiles available in the foundation package.</span></span> <span data-ttu-id="91ddc-106">[`MixedRealityToolkit`](xref:Microsoft.MixedReality.Toolkit.MixedRealityToolkit)場景中的主要物件會有使用中的設定檔，也就是 ScriptableObject。</span><span class="sxs-lookup"><span data-stu-id="91ddc-106">The main [`MixedRealityToolkit`](xref:Microsoft.MixedReality.Toolkit.MixedRealityToolkit) object in a scene will have the active profile, which is a ScriptableObject.</span></span> <span data-ttu-id="91ddc-107">最上層 MRTK 設定檔包含主要核心系統每個核心的子設定檔資料，每一個核心系統都是設計來設定其對應子系統的行為。</span><span class="sxs-lookup"><span data-stu-id="91ddc-107">The top level MRTK Configuration Profile contains sub-profile data for each core of the primary core systems, each of which are designed to configure the behavior of their corresponding subsystems.</span></span> <span data-ttu-id="91ddc-108">此外，這些子設定檔也會 ScriptableObjects，因此可包含其下一個層級之其他設定檔物件的參考。</span><span class="sxs-lookup"><span data-stu-id="91ddc-108">Furthermore, these sub-profiles are also ScriptableObjects and thus can contain references to other profile objects one level below them.</span></span> <span data-ttu-id="91ddc-109">基本上，有一個連線設定檔的整個樹狀結構，這些設定檔會組成設定資訊，以說明如何初始化 MRTK 子系統和功能。</span><span class="sxs-lookup"><span data-stu-id="91ddc-109">There is essentially an entire tree of connected profiles that make up the configuration information for how to initialize the MRTK subsystems and features.</span></span>

<span data-ttu-id="91ddc-110">例如，輸入系統的行為是由輸入系統設定檔所控制，例如 `DefaultMixedRealityInputSystemProfile` (資產/MRTK/SDK/設定檔) 。</span><span class="sxs-lookup"><span data-stu-id="91ddc-110">For example, the input system's behavior is governed by an input system profile, like the `DefaultMixedRealityInputSystemProfile` (Assets/MRTK/SDK/Profiles).</span></span>

<img src="../images/profiles/input_profile.png" width="650px" alt="Input profile" style="display:block;">
<span data-ttu-id="91ddc-111"><sup>設定檔偵測器</sup></span><span class="sxs-lookup"><span data-stu-id="91ddc-111"><sup>Profile Inspector</sup></span></span>

## <a name="background"></a><span data-ttu-id="91ddc-112">背景</span><span class="sxs-lookup"><span data-stu-id="91ddc-112">Background</span></span>

<span data-ttu-id="91ddc-113">設定檔主要是用來支援跨多個裝置的特定案例，這些裝置會透過資料提供者來處理。</span><span class="sxs-lookup"><span data-stu-id="91ddc-113">Profiles are mainly intended to support specific scenarios across multiple devices, which are handled via the data providers.</span></span> <span data-ttu-id="91ddc-114">如此一來，應用程式就可以盡可能地設計為裝置 agnosticly，並讓 MRTK 和設定檔的資料提供者處理跨平臺支援。</span><span class="sxs-lookup"><span data-stu-id="91ddc-114">This way, an app can be designed as device-agnosticly as possible and let the MRTK and the profile's data providers handle cross-platform support.</span></span>

<span data-ttu-id="91ddc-115">另外還有一些設定檔是根據特定裝置的輸入功能來建立的，例如預設為 GGV 樣式互動的 HoloLens 1 設定檔。</span><span class="sxs-lookup"><span data-stu-id="91ddc-115">There are also profiles built around the input features of specific devices, such as the HoloLens 1 profile which defaults to GGV-style interactions.</span></span>

## <a name="xr-sdk"></a><span data-ttu-id="91ddc-116">XR SDK</span><span class="sxs-lookup"><span data-stu-id="91ddc-116">XR SDK</span></span>

::: moniker range=">= mrtkunity-2021-05"
<span data-ttu-id="91ddc-117">使用任何預設的 MRTK 設定檔，這些設定檔全都在 Unity 的 XR 管線中設定。</span><span class="sxs-lookup"><span data-stu-id="91ddc-117">Use any of the default MRTK profiles, which are all configured across Unity's XR pipelines.</span></span> <span data-ttu-id="91ddc-118">先前的 "DefaultOpenXRConfigurationProfile" 和 "DefaultXRSDKConfigurationProfile" 現在標示為過時。</span><span class="sxs-lookup"><span data-stu-id="91ddc-118">The previous "DefaultOpenXRConfigurationProfile" and "DefaultXRSDKConfigurationProfile" are now labeled obsolete.</span></span>
::: moniker-end
::: moniker range="< mrtkunity-2021-05"
<span data-ttu-id="91ddc-119">目前有兩個設定檔提供給 XR SDK `DefaultXRSDKConfigurationProfile` 和 `DefaultHoloLens2XRSDKConfigurationProfile` 。</span><span class="sxs-lookup"><span data-stu-id="91ddc-119">Currently, there are two profiles provided for XR SDK, `DefaultXRSDKConfigurationProfile` and `DefaultHoloLens2XRSDKConfigurationProfile`.</span></span> <span data-ttu-id="91ddc-120">如此一來，就不會因為場景和案例特定的設定而完全支援所有的範例場景。</span><span class="sxs-lookup"><span data-stu-id="91ddc-120">As a result, not all samples scenes are fully supported due to scene- and scenario-specific configurations.</span></span> <span data-ttu-id="91ddc-121">任何使用和的範例都 `DefaultMixedRealityToolkitConfigurationProfile` `DefaultHoloLens2ConfigurationProfile` _可以_ 交換至其對應的 XR SDK 設定檔。</span><span class="sxs-lookup"><span data-stu-id="91ddc-121">Any samples that use `DefaultMixedRealityToolkitConfigurationProfile` and `DefaultHoloLens2ConfigurationProfile` _can_ be swapped over to their corresponding XR SDK profiles.</span></span> <span data-ttu-id="91ddc-122">如果您是使用 OpenXR 搭配 XR SDK，請改用 `DefaultOpenXRConfigurationProfile` 。</span><span class="sxs-lookup"><span data-stu-id="91ddc-122">If you're using OpenXR with XR SDK, use the `DefaultOpenXRConfigurationProfile` instead.</span></span>

<span data-ttu-id="91ddc-123">正在進行額外的工作，以簡化設定並支援所有範例場景，讓舊版 XR 和 XR SDK 可以並存設定。</span><span class="sxs-lookup"><span data-stu-id="91ddc-123">Additional work is being undertaken to ease configuration and support all sample scenes, allowing for both legacy XR and XR SDK to be configured side-by-side.</span></span> <span data-ttu-id="91ddc-124">請參閱追蹤的問題 [#9419](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9419) 。</span><span class="sxs-lookup"><span data-stu-id="91ddc-124">See issue [#9419](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9419) for tracking.</span></span>
::: moniker-end

<span data-ttu-id="91ddc-125">如需在舊版 XR 和 XR SDK 之間轉換設定檔的詳細資訊，請參閱設定 [XR SDK 管線的 MRTK](../../configuration/getting-started-with-mrtk-and-xrsdk.md#configuring-mrtk-for-the-xr-sdk-pipeline) 。</span><span class="sxs-lookup"><span data-stu-id="91ddc-125">See [Configuring MRTK for the XR SDK pipeline](../../configuration/getting-started-with-mrtk-and-xrsdk.md#configuring-mrtk-for-the-xr-sdk-pipeline) for more information on converting profiles between legacy XR and XR SDK.</span></span>

## <a name="default-profile"></a><span data-ttu-id="91ddc-126">預設設定檔</span><span class="sxs-lookup"><span data-stu-id="91ddc-126">Default profile</span></span>

<span data-ttu-id="91ddc-127">MRTK 會提供一組預設設定檔，其中涵蓋 MRTK 支援的大部分平臺和案例。</span><span class="sxs-lookup"><span data-stu-id="91ddc-127">The MRTK provides a set of default profiles which cover most platforms and scenarios that the MRTK supports.</span></span> <span data-ttu-id="91ddc-128">例如，當您選取 `DefaultMixedRealityToolkitConfigurationProfile` (資產/MRTK/SDK/設定檔時) 您將能夠在 VR 上試用案例 (OpenVR、WMR) 和 HoloLens (1 和 2) 。</span><span class="sxs-lookup"><span data-stu-id="91ddc-128">For example, when you select the `DefaultMixedRealityToolkitConfigurationProfile` (Assets/MRTK/SDK/Profiles) you will be able to try out scenarios on VR (OpenVR, WMR) and HoloLens (1 and 2).</span></span>

<span data-ttu-id="91ddc-129">請注意，因為這是一般用途的設定檔，所以不會針對任何特定使用案例進行優化。</span><span class="sxs-lookup"><span data-stu-id="91ddc-129">Note that because this is a general use profile, it's not optimized for any particular use case.</span></span> <span data-ttu-id="91ddc-130">如果您想要在其他平臺上擁有更佳的效能/特定設定，請參閱下列其他設定檔，這些設定檔會在其各自的平臺上稍微調整得更好。</span><span class="sxs-lookup"><span data-stu-id="91ddc-130">If you want to have more performant/specific settings that are better on other platforms, see the other profiles below, which are slightly tweaked to be better on their respective platforms.</span></span>

## <a name="hololens-2-profile"></a><span data-ttu-id="91ddc-131">HoloLens 2 設定檔</span><span class="sxs-lookup"><span data-stu-id="91ddc-131">HoloLens 2 profile</span></span>

<span data-ttu-id="91ddc-132">MRTK 也提供已針對 HoloLens 2： `DefaultHoloLens2ConfigurationProfile` (資產/MRTK/SDK/設定檔/HoloLens2) 進行部署和測試的預設設定檔。</span><span class="sxs-lookup"><span data-stu-id="91ddc-132">The MRTK also provides a default profile that is optimized for deployment and testing on the HoloLens 2: `DefaultHoloLens2ConfigurationProfile` (Assets/MRTK/SDK/Profiles/HoloLens2).</span></span>

<span data-ttu-id="91ddc-133">當系統提示您選擇 MixedRealityToolkit 物件的設定檔時，請使用此設定檔，而不是預設選取的設定檔。</span><span class="sxs-lookup"><span data-stu-id="91ddc-133">When prompted to choose a profile for the MixedRealityToolkit object, use this profile instead of the default selected profile.</span></span>

<span data-ttu-id="91ddc-134">HoloLens2 設定檔和預設設定檔之間的主要差異如下：</span><span class="sxs-lookup"><span data-stu-id="91ddc-134">The key differences between the HoloLens2 profile and the Default Profile are:</span></span>

<span data-ttu-id="91ddc-135">**停用** 的功能：</span><span class="sxs-lookup"><span data-stu-id="91ddc-135">**Disabled** features:</span></span>

- [<span data-ttu-id="91ddc-136">界限系統</span><span class="sxs-lookup"><span data-stu-id="91ddc-136">Boundary system</span></span>](../boundary/boundary-system-getting-started.md)
- [<span data-ttu-id="91ddc-137">傳送系統</span><span class="sxs-lookup"><span data-stu-id="91ddc-137">Teleport system</span></span>](../teleport-system/teleport-system.md)
- [<span data-ttu-id="91ddc-138">空間感知系統</span><span class="sxs-lookup"><span data-stu-id="91ddc-138">Spatial awareness system</span></span>](../spatial-awareness/spatial-awareness-getting-started.md)
- <span data-ttu-id="91ddc-139">因效能額外負荷而 ([手上網格視覺效果](../input/hand-tracking.md)) </span><span class="sxs-lookup"><span data-stu-id="91ddc-139">[Hand mesh visualization](../input/hand-tracking.md) (due to performance overhead)</span></span>

<span data-ttu-id="91ddc-140">**啟用** 的系統：</span><span class="sxs-lookup"><span data-stu-id="91ddc-140">**Enabled** systems:</span></span>

- <span data-ttu-id="91ddc-141">[眼睛追蹤提供者](../input/eye-tracking/eye-tracking-main.md)</span><span class="sxs-lookup"><span data-stu-id="91ddc-141">The [eye tracking provider](../input/eye-tracking/eye-tracking-main.md)</span></span>
- <span data-ttu-id="91ddc-142">目視輸入模擬</span><span class="sxs-lookup"><span data-stu-id="91ddc-142">Eye input simulation</span></span>

<span data-ttu-id="91ddc-143">攝影機設定檔設定會設定為相符，因此編輯器品質和播放程式品質都相同。</span><span class="sxs-lookup"><span data-stu-id="91ddc-143">Camera profile settings are set to match so that the editor quality and player quality are the same.</span></span> <span data-ttu-id="91ddc-144">這與預設攝影機設定檔不同，因為不透明顯示會設定為較高的品質。</span><span class="sxs-lookup"><span data-stu-id="91ddc-144">This is different from the default camera profile where opaque displays are set to a higher quality.</span></span> <span data-ttu-id="91ddc-145">這項變更表示在編輯器品質較低的情況下，將會更接近裝置上呈現的內容。</span><span class="sxs-lookup"><span data-stu-id="91ddc-145">This change means that in-editor quality will be lower, which will more closely match what will be rendered on the device.</span></span>

> [!NOTE]
> <span data-ttu-id="91ddc-146">根據用戶端的意見反應，預設會關閉空間感知系統，這是一種有趣的視覺效果，但通常會將其關閉，以避免視覺干擾以及將它開啟的額外效能衝擊。</span><span class="sxs-lookup"><span data-stu-id="91ddc-146">The Spatial Awareness system is turned off by default based on client feedback - it is an interesting visualization to see initially but is typically turned off to avoid the visual distraction and the additional performance hit of having it on.</span></span> <span data-ttu-id="91ddc-147">您可以遵循 [此處的指示](../spatial-awareness/spatial-awareness-getting-started.md)來重新啟用系統。</span><span class="sxs-lookup"><span data-stu-id="91ddc-147">The system can be re-enabled by following the [instructions here](../spatial-awareness/spatial-awareness-getting-started.md).</span></span>
