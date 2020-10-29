---
title: Unreal 中的注視輸入
description: 針對 HoloLens 和 Unreal 引擎設定注視輸入的教學課程
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
keywords: Windows Mixed Reality，全像影像、HoloLens 2、眼睛追蹤、注視輸入、前端掛接顯示器、Unreal 引擎
ms.openlocfilehash: 477fbdc9c7ddb3b4e890e62150651d9227d4c19e
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2020
ms.locfileid: "91679849"
---
# <a name="gaze-input"></a><span data-ttu-id="66fb4-104">注視輸入</span><span class="sxs-lookup"><span data-stu-id="66fb4-104">Gaze Input</span></span>

## <a name="overview"></a><span data-ttu-id="66fb4-105">概觀</span><span class="sxs-lookup"><span data-stu-id="66fb4-105">Overview</span></span>

<span data-ttu-id="66fb4-106">[Windows Mixed Reality 外掛程式](https://docs.unrealengine.com/Platforms/VR/WMR/index.html)不會為眼睛輸入提供任何內建函數，但 HoloLens 2 支援眼睛追蹤。</span><span class="sxs-lookup"><span data-stu-id="66fb4-106">The [Windows Mixed Reality plugin](https://docs.unrealengine.com/Platforms/VR/WMR/index.html) doesn’t provide any built-in functions for gaze input, but HoloLens 2 does support eye tracking.</span></span> <span data-ttu-id="66fb4-107">實際的追蹤功能是由 Unreal 的前端 **裝載顯示器** 和 **眼睛追蹤** api 所提供，包括：</span><span class="sxs-lookup"><span data-stu-id="66fb4-107">The actual tracking features are provided by Unreal's **Head Mounted Display** and **Eye Tracking** APIs and include:</span></span>

- <span data-ttu-id="66fb4-108">裝置資訊</span><span class="sxs-lookup"><span data-stu-id="66fb4-108">Device information</span></span>
- <span data-ttu-id="66fb4-109">追蹤感應器</span><span class="sxs-lookup"><span data-stu-id="66fb4-109">Tracking sensors</span></span>
- <span data-ttu-id="66fb4-110">方向和位置</span><span class="sxs-lookup"><span data-stu-id="66fb4-110">Orientation and position</span></span>
- <span data-ttu-id="66fb4-111">裁剪窗格</span><span class="sxs-lookup"><span data-stu-id="66fb4-111">Clipping panes</span></span>
- <span data-ttu-id="66fb4-112">注視資料和追蹤資訊</span><span class="sxs-lookup"><span data-stu-id="66fb4-112">Gaze data and tracking information</span></span>

<span data-ttu-id="66fb4-113">您可以在 Unreal 的前端 [裝載顯示](https://docs.unrealengine.com/BlueprintAPI/Input/HeadMountedDisplay/index.html) 和 [眼睛追蹤](https://docs.unrealengine.com/BlueprintAPI/EyeTracking/index.html) 檔中找到完整的功能清單。</span><span class="sxs-lookup"><span data-stu-id="66fb4-113">You can find the full list of features in Unreal's [Head Mounted Display](https://docs.unrealengine.com/BlueprintAPI/Input/HeadMountedDisplay/index.html) and [Eye Tracking](https://docs.unrealengine.com/BlueprintAPI/EyeTracking/index.html) documentation.</span></span>

<span data-ttu-id="66fb4-114">除了 Unreal Api 之外，請查看 HoloLens 2 [眼睛](../../design/eye-gaze-interaction.md) 的相關檔，並深入瞭解 [HoloLens 2 的眼睛追蹤](https://docs.microsoft.com/windows/mixed-reality/eye-tracking) 的運作方式。</span><span class="sxs-lookup"><span data-stu-id="66fb4-114">In addition to the Unreal APIs, check out the documentation on [eye-gaze-based interaction](../../design/eye-gaze-interaction.md) for HoloLens 2 and read up on how [eye tracking on HoloLens 2](https://docs.microsoft.com/windows/mixed-reality/eye-tracking) works.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="66fb4-115">只有 HoloLens 2 才支援眼睛追蹤。</span><span class="sxs-lookup"><span data-stu-id="66fb4-115">Eye tracking is only supported on HoloLens 2.</span></span>

## <a name="enabling-eye-tracking"></a><span data-ttu-id="66fb4-116">啟用眼睛追蹤</span><span class="sxs-lookup"><span data-stu-id="66fb4-116">Enabling eye tracking</span></span>
<span data-ttu-id="66fb4-117">您必須先在 HoloLens 專案設定中啟用注視輸入，才能使用任何 Unreal 的 Api。</span><span class="sxs-lookup"><span data-stu-id="66fb4-117">Gaze input needs to be enabled in the HoloLens project settings before you can use any of Unreal's APIs.</span></span> <span data-ttu-id="66fb4-118">當應用程式啟動時，您會看到如下列螢幕擷取畫面所示的同意提示。</span><span class="sxs-lookup"><span data-stu-id="66fb4-118">When the application starts you'll see a consent prompt shown in the screenshot below.</span></span>

- <span data-ttu-id="66fb4-119">選取 **[是]** 可設定許可權，並取得輸入的存取權。</span><span class="sxs-lookup"><span data-stu-id="66fb4-119">Select **Yes** to set the permission and get access to gaze input.</span></span> <span data-ttu-id="66fb4-120">如果您在任何時間都需要變更此設定，可以在 [ **設定** ] 應用程式中找到。</span><span class="sxs-lookup"><span data-stu-id="66fb4-120">If you need to change this setting at any time, it can be found in the **Settings** app.</span></span>

![目視輸入許可權](images/unreal/eye-input-permissions.png)

> [!NOTE] 
> <span data-ttu-id="66fb4-122">Unreal 中的 HoloLens 眼睛追蹤只會有一個眼睛光線，而不是 stereoscopic 追蹤所需的兩個光線，而這是不受支援的。</span><span class="sxs-lookup"><span data-stu-id="66fb4-122">HoloLens eye tracking in Unreal only has a single gaze ray for both eyes instead of the two rays needed for stereoscopic tracking, which is not supported.</span></span>

<span data-ttu-id="66fb4-123">這就是您在 Unreal 中開始將注視輸入新增至 HoloLens 2 應用程式時所需的所有設定。</span><span class="sxs-lookup"><span data-stu-id="66fb4-123">That's all the setup you'll need to start adding gaze input to your HoloLens 2 apps in Unreal.</span></span> <span data-ttu-id="66fb4-124">您可以在下列連結中找到有關注視輸入的詳細資訊，以及它如何影響混合現實中的使用者。</span><span class="sxs-lookup"><span data-stu-id="66fb4-124">More information on gaze input and how it affects users in mixed reality can be found at the links below.</span></span> <span data-ttu-id="66fb4-125">當您建立互動式體驗時，請務必考慮這些資訊。</span><span class="sxs-lookup"><span data-stu-id="66fb4-125">Be sure to think about these when building your interactive experiences.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="66fb4-126">下一個開發檢查點</span><span class="sxs-lookup"><span data-stu-id="66fb4-126">Next Development Checkpoint</span></span>

<span data-ttu-id="66fb4-127">如果您正在遵循我們所配置的 Unreal 開發檢查點旅程，您將在探索 MRTK 核心構成要素。</span><span class="sxs-lookup"><span data-stu-id="66fb4-127">If you're following the Unreal development checkpoint journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="66fb4-128">您可以從這裡繼續進行下一個組建區塊：</span><span class="sxs-lookup"><span data-stu-id="66fb4-128">From here, you can proceed to the next building block:</span></span> 

> [!div class="nextstepaction"]
> [<span data-ttu-id="66fb4-129">手勢追蹤</span><span class="sxs-lookup"><span data-stu-id="66fb4-129">Hand tracking</span></span>](unreal-hand-tracking.md)

<span data-ttu-id="66fb4-130">或跳至混合的現實平臺功能和 Api：</span><span class="sxs-lookup"><span data-stu-id="66fb4-130">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="66fb4-131">HoloLens 相機</span><span class="sxs-lookup"><span data-stu-id="66fb4-131">HoloLens camera</span></span>](unreal-hololens-camera.md)

<span data-ttu-id="66fb4-132">您隨時都可以回到 [Unreal 開發檢查點](unreal-development-overview.md#2-core-building-blocks) 。</span><span class="sxs-lookup"><span data-stu-id="66fb4-132">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="66fb4-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="66fb4-133">See also</span></span>
* [<span data-ttu-id="66fb4-134">校正</span><span class="sxs-lookup"><span data-stu-id="66fb4-134">Calibration</span></span>](../../calibration.md)
* [<span data-ttu-id="66fb4-135">舒適度</span><span class="sxs-lookup"><span data-stu-id="66fb4-135">Comfort</span></span>](../../design/comfort.md)
* [<span data-ttu-id="66fb4-136">目光和行動</span><span class="sxs-lookup"><span data-stu-id="66fb4-136">Gaze and commit</span></span>](../../design/gaze-and-commit.md)
* [<span data-ttu-id="66fb4-137">語音輸入</span><span class="sxs-lookup"><span data-stu-id="66fb4-137">Voice input</span></span>](../../out-of-scope/voice-design.md)
