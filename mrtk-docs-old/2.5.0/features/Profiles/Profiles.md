---
title: Profiles
description: MRTK 中的檔設定檔
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、設定檔、
ms.openlocfilehash: fb9f6b2e0e02741ad77bae3b1d9ba37334cf630c
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104695285"
---
# <a name="profiles"></a><span data-ttu-id="c40b6-104">Profiles</span><span class="sxs-lookup"><span data-stu-id="c40b6-104">Profiles</span></span>

<span data-ttu-id="c40b6-105">MRTK 設定的主要方式之一是透過基礎套件中的許多可用設定檔。</span><span class="sxs-lookup"><span data-stu-id="c40b6-105">One of the main ways that the MRTK is configured is through the many profiles available in the foundation package.</span></span> <span data-ttu-id="c40b6-106">[`MixedRealityToolkit`](xref:Microsoft.MixedReality.Toolkit.MixedRealityToolkit)場景中的主要物件會有使用中的設定檔，基本上是 ScriptableObject。</span><span class="sxs-lookup"><span data-stu-id="c40b6-106">The main [`MixedRealityToolkit`](xref:Microsoft.MixedReality.Toolkit.MixedRealityToolkit) object in a scene will have the active profile, which is essentially a ScriptableObject.</span></span> <span data-ttu-id="c40b6-107">最上層的 MRTK 設定檔包含主要核心系統每個核心的子設定檔資料，每一個核心系統都是設計來設定其對應子系統的行為。</span><span class="sxs-lookup"><span data-stu-id="c40b6-107">The top level MRTK Configuration Profile contains sub-profile data for each core of the primary core systems, each of which are designed to configure the behavior of their corresponding sub-systems.</span></span> <span data-ttu-id="c40b6-108">此外，這些子設定檔也是可編寫腳本的物件，因此可包含其下一個層級之其他設定檔物件的參考。</span><span class="sxs-lookup"><span data-stu-id="c40b6-108">Furthermore, these sub-profiles are also Scriptable Objects and thus can contain references to other profile objects one level below them.</span></span> <span data-ttu-id="c40b6-109">基本上，有一個連線設定檔的整個樹狀結構，這些設定檔會組成設定資訊，以說明如何初始化 MRTK 子系統和功能。</span><span class="sxs-lookup"><span data-stu-id="c40b6-109">There is essentially an entire tree of connected profiles that make up the configuration information for how to initialize the MRTK sub-systems and features.</span></span>

<span data-ttu-id="c40b6-110">例如，輸入系統的行為是由輸入系統設定檔所控制，例如 `DefaultMixedRealityInputSystemProfile` (資產/MRTK/SDK/設定檔) 。</span><span class="sxs-lookup"><span data-stu-id="c40b6-110">For example, the Input system's behavior is governed by an input system profile, for example the `DefaultMixedRealityInputSystemProfile` (Assets/MRTK/SDK/Profiles).</span></span> <span data-ttu-id="c40b6-111">強烈建議您一律透過編輯器中的偵測器來修改設定檔 ScriptableObject 資產。</span><span class="sxs-lookup"><span data-stu-id="c40b6-111">It's highly recommended to always modify the profile ScriptableObject assets via the in-editor inspector.</span></span>

<img src="../Images/Profiles/input_profile.png" width="650px" alt="Input Profile" style="display:block;">
<span data-ttu-id="c40b6-112"><sup>設定檔偵測器</sup></span><span class="sxs-lookup"><span data-stu-id="c40b6-112"><sup>Profile Inspector</sup></span></span>

> [!NOTE]
> <span data-ttu-id="c40b6-113">雖然這是為了讓設定檔可在執行時間交換，但 [目前無法運作](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/4289)</span><span class="sxs-lookup"><span data-stu-id="c40b6-113">While it is intended that profiles can be swapped out at runtime, this [currently does not work](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/4289)</span></span>

## <a name="default-profile"></a><span data-ttu-id="c40b6-114">預設設定檔</span><span class="sxs-lookup"><span data-stu-id="c40b6-114">Default profile</span></span>

<span data-ttu-id="c40b6-115">MRTK 會提供一組預設設定檔，其中涵蓋 MRTK 支援的大部分平臺和案例。</span><span class="sxs-lookup"><span data-stu-id="c40b6-115">The MRTK provides a set of default profiles which cover most platforms and scenarios that the MRTK supports.</span></span> <span data-ttu-id="c40b6-116">例如，當您選取 `DefaultMixedRealityToolkitConfigurationProfile` (資產/MRTK/SDK/設定檔時) 您將能夠在 VR 上試用案例 (OpenVR、WMR) 和 HoloLens (1 和 2) 。</span><span class="sxs-lookup"><span data-stu-id="c40b6-116">For example, when you select the `DefaultMixedRealityToolkitConfigurationProfile` (Assets/MRTK/SDK/Profiles) you will be able to try out scenarios on VR (OpenVR, WMR) and HoloLens (1 and 2).</span></span>

<span data-ttu-id="c40b6-117">請注意，因為這是一般用途的設定檔，所以不會針對任何特定使用案例進行優化。</span><span class="sxs-lookup"><span data-stu-id="c40b6-117">Note that because this is a general use profile, it's not optimized for any particular use case.</span></span> <span data-ttu-id="c40b6-118">如果您想要在其他平臺上擁有更佳的效能/特定設定，請參閱下列其他設定檔，這些設定檔會在其各自的平臺上稍微調整得更好。</span><span class="sxs-lookup"><span data-stu-id="c40b6-118">If you want to have more performant/specific settings that are better on other platforms, see the other profiles below, which are slightly tweaked to be better on their respective platforms.</span></span>

## <a name="hololens-2-profile"></a><span data-ttu-id="c40b6-119">HoloLens 2 設定檔</span><span class="sxs-lookup"><span data-stu-id="c40b6-119">HoloLens 2 profile</span></span>

<span data-ttu-id="c40b6-120">MRTK 也提供已針對 HoloLens 2： `DefaultHoloLens2ConfigurationProfile` (資產/MRTK/SDK/設定檔/HoloLens2) 進行部署和測試的預設設定檔。</span><span class="sxs-lookup"><span data-stu-id="c40b6-120">The MRTK also provides a default profile that is optimized for deployment and testing on the HoloLens 2: `DefaultHoloLens2ConfigurationProfile` (Assets/MRTK/SDK/Profiles/HoloLens2).</span></span>

<span data-ttu-id="c40b6-121">當系統提示您選擇 MixedRealityToolkit 物件的設定檔時，請使用此設定檔，而不是預設選取的設定檔。</span><span class="sxs-lookup"><span data-stu-id="c40b6-121">When prompted to choose a profile for the MixedRealityToolkit object, use this profile instead of the default selected profile.</span></span>

<span data-ttu-id="c40b6-122">HoloLens2 設定檔和預設設定檔之間的主要差異如下：</span><span class="sxs-lookup"><span data-stu-id="c40b6-122">The key differences between the HoloLens2 profile and the Default Profile are:</span></span>

<span data-ttu-id="c40b6-123">**已停用** 特徵：</span><span class="sxs-lookup"><span data-stu-id="c40b6-123">**Disabled** Features:</span></span>

- [<span data-ttu-id="c40b6-124">界限系統</span><span class="sxs-lookup"><span data-stu-id="c40b6-124">Boundary System</span></span>](../Boundary/BoundarySystemGettingStarted.md)
- [<span data-ttu-id="c40b6-125">傳送系統</span><span class="sxs-lookup"><span data-stu-id="c40b6-125">Teleport System</span></span>](../TeleportSystem/Overview.md)
- [<span data-ttu-id="c40b6-126">空間感知系統</span><span class="sxs-lookup"><span data-stu-id="c40b6-126">Spatial Awareness System</span></span>](../SpatialAwareness/SpatialAwarenessGettingStarted.md)
- <span data-ttu-id="c40b6-127">因效能額外負荷而 ([手上網格視覺效果](../Input/HandTracking.md)) </span><span class="sxs-lookup"><span data-stu-id="c40b6-127">[Hand mesh visualization](../Input/HandTracking.md) (due to performance overhead)</span></span>

<span data-ttu-id="c40b6-128">**已啟用** 系統：</span><span class="sxs-lookup"><span data-stu-id="c40b6-128">**Enabled** Systems:</span></span>

- <span data-ttu-id="c40b6-129">[眼睛追蹤提供者](../EyeTracking/EyeTracking_Main.md)</span><span class="sxs-lookup"><span data-stu-id="c40b6-129">The [Eye Tracking provider](../EyeTracking/EyeTracking_Main.md)</span></span>
- <span data-ttu-id="c40b6-130">目視輸入模擬</span><span class="sxs-lookup"><span data-stu-id="c40b6-130">Eye input simulation</span></span>

<span data-ttu-id="c40b6-131">攝影機設定檔設定會設定為相符，因此編輯器品質和播放程式品質都相同。</span><span class="sxs-lookup"><span data-stu-id="c40b6-131">Camera profile settings are set to match so that the editor quality and player quality are the same.</span></span> <span data-ttu-id="c40b6-132">這與預設攝影機設定檔不同，因為不透明顯示會設定為較高的品質。</span><span class="sxs-lookup"><span data-stu-id="c40b6-132">This is different from the default camera profile where Opaque displays are set to a higher quality.</span></span> <span data-ttu-id="c40b6-133">這項變更表示在編輯器品質較低的情況下，將會更接近裝置上呈現的內容。</span><span class="sxs-lookup"><span data-stu-id="c40b6-133">This change means that in-editor quality will be lower, which will more closely match what will be rendered on the device.</span></span>

> [!NOTE]
> <span data-ttu-id="c40b6-134">根據用戶端的意見反應，預設會關閉空間感知系統，這是一種有趣的視覺效果，但通常會將其關閉，以避免視覺干擾以及將它開啟的額外效能衝擊。</span><span class="sxs-lookup"><span data-stu-id="c40b6-134">The Spatial Awareness system is turned off by default based on client feedback - it is an interesting visualization to see initially but is typically turned off to avoid the visual distraction and the additional performance hit of having it on.</span></span> <span data-ttu-id="c40b6-135">您可以遵循 [此處的指示](../SpatialAwareness/SpatialAwarenessGettingStarted.md)來重新啟用系統。</span><span class="sxs-lookup"><span data-stu-id="c40b6-135">The system can be re-enabled by following the [instructions here](../SpatialAwareness/SpatialAwarenessGettingStarted.md).</span></span>
