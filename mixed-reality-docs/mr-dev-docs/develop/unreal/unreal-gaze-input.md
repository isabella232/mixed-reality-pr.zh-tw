---
title: Unreal 中的注視輸入
description: 針對 HoloLens 和 Unreal 引擎設定注視輸入的教學課程
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
keywords: Windows Mixed Reality、全像 HoloLens 2、眼睛追蹤、注視輸入、前端掛接顯示器、Unreal 引擎、混合現實耳機、windows Mixed reality 耳機、虛擬實境耳機
ms.openlocfilehash: 2ea55e3c53275f6150ca7f2def10d71634119e2e
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2020
ms.locfileid: "94679047"
---
# <a name="gaze-input"></a><span data-ttu-id="460b7-104">注視輸入</span><span class="sxs-lookup"><span data-stu-id="460b7-104">Gaze Input</span></span>

## <a name="overview"></a><span data-ttu-id="460b7-105">概觀</span><span class="sxs-lookup"><span data-stu-id="460b7-105">Overview</span></span>

<span data-ttu-id="460b7-106">[Windows Mixed Reality 外掛程式](https://docs.unrealengine.com/Platforms/VR/WMR/index.html)不會為眼睛輸入提供任何內建函數，但 HoloLens 2 支援眼睛追蹤。</span><span class="sxs-lookup"><span data-stu-id="460b7-106">The [Windows Mixed Reality plugin](https://docs.unrealengine.com/Platforms/VR/WMR/index.html) doesn’t provide any built-in functions for gaze input, but HoloLens 2 does support eye tracking.</span></span> <span data-ttu-id="460b7-107">實際的追蹤功能是由 Unreal 的前端 **裝載顯示器** 和 **眼睛追蹤** api 所提供，包括：</span><span class="sxs-lookup"><span data-stu-id="460b7-107">The actual tracking features are provided by Unreal's **Head Mounted Display** and **Eye Tracking** APIs and include:</span></span>

- <span data-ttu-id="460b7-108">裝置資訊</span><span class="sxs-lookup"><span data-stu-id="460b7-108">Device information</span></span>
- <span data-ttu-id="460b7-109">追蹤感應器</span><span class="sxs-lookup"><span data-stu-id="460b7-109">Tracking sensors</span></span>
- <span data-ttu-id="460b7-110">方向和位置</span><span class="sxs-lookup"><span data-stu-id="460b7-110">Orientation and position</span></span>
- <span data-ttu-id="460b7-111">裁剪窗格</span><span class="sxs-lookup"><span data-stu-id="460b7-111">Clipping panes</span></span>
- <span data-ttu-id="460b7-112">注視資料和追蹤資訊</span><span class="sxs-lookup"><span data-stu-id="460b7-112">Gaze data and tracking information</span></span>

<span data-ttu-id="460b7-113">您可以在 Unreal 的前端 [裝載顯示](https://docs.unrealengine.com/BlueprintAPI/Input/HeadMountedDisplay/index.html) 和 [眼睛追蹤](https://docs.unrealengine.com/BlueprintAPI/EyeTracking/index.html) 檔中找到完整的功能清單。</span><span class="sxs-lookup"><span data-stu-id="460b7-113">You can find the full list of features in Unreal's [Head Mounted Display](https://docs.unrealengine.com/BlueprintAPI/Input/HeadMountedDisplay/index.html) and [Eye Tracking](https://docs.unrealengine.com/BlueprintAPI/EyeTracking/index.html) documentation.</span></span>

<span data-ttu-id="460b7-114">除了 Unreal Api 之外，請查看 HoloLens 2 [眼睛](../../design/eye-gaze-interaction.md) 的相關檔，並深入瞭解 [HoloLens 2 的眼睛追蹤](https://docs.microsoft.com/windows/mixed-reality/eye-tracking) 的運作方式。</span><span class="sxs-lookup"><span data-stu-id="460b7-114">In addition to the Unreal APIs, check out the documentation on [eye-gaze-based interaction](../../design/eye-gaze-interaction.md) for HoloLens 2 and read up on how [eye tracking on HoloLens 2](https://docs.microsoft.com/windows/mixed-reality/eye-tracking) works.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="460b7-115">只有 HoloLens 2 才支援眼睛追蹤。</span><span class="sxs-lookup"><span data-stu-id="460b7-115">Eye tracking is only supported on HoloLens 2.</span></span>

## <a name="enabling-eye-tracking"></a><span data-ttu-id="460b7-116">啟用眼睛追蹤</span><span class="sxs-lookup"><span data-stu-id="460b7-116">Enabling eye tracking</span></span>
<span data-ttu-id="460b7-117">您必須先在 HoloLens 專案設定中啟用注視輸入，才能使用任何 Unreal 的 Api。</span><span class="sxs-lookup"><span data-stu-id="460b7-117">Gaze input needs to be enabled in the HoloLens project settings before you can use any of Unreal's APIs.</span></span> <span data-ttu-id="460b7-118">當應用程式啟動時，您會看到如下列螢幕擷取畫面所示的同意提示。</span><span class="sxs-lookup"><span data-stu-id="460b7-118">When the application starts you'll see a consent prompt shown in the screenshot below.</span></span>

- <span data-ttu-id="460b7-119">選取 **[是]** 可設定許可權，並取得輸入的存取權。</span><span class="sxs-lookup"><span data-stu-id="460b7-119">Select **Yes** to set the permission and get access to gaze input.</span></span> <span data-ttu-id="460b7-120">如果您在任何時間都需要變更此設定，可以在 [ **設定** ] 應用程式中找到。</span><span class="sxs-lookup"><span data-stu-id="460b7-120">If you need to change this setting at any time, it can be found in the **Settings** app.</span></span>

![目視輸入許可權](images/unreal/eye-input-permissions.png)

> [!NOTE] 
> <span data-ttu-id="460b7-122">Unreal 中的 HoloLens 眼睛追蹤只會有一個眼睛光線，而不是 stereoscopic 追蹤所需的兩個光線，而這是不受支援的。</span><span class="sxs-lookup"><span data-stu-id="460b7-122">HoloLens eye tracking in Unreal only has a single gaze ray for both eyes instead of the two rays needed for stereoscopic tracking, which is not supported.</span></span>

<span data-ttu-id="460b7-123">這就是您在 Unreal 中開始將注視輸入新增至 HoloLens 2 應用程式時所需的所有設定。</span><span class="sxs-lookup"><span data-stu-id="460b7-123">That's all the setup you'll need to start adding gaze input to your HoloLens 2 apps in Unreal.</span></span> <span data-ttu-id="460b7-124">您可以在下列連結中找到有關注視輸入的詳細資訊，以及它如何影響混合現實中的使用者。</span><span class="sxs-lookup"><span data-stu-id="460b7-124">More information on gaze input and how it affects users in mixed reality can be found at the links below.</span></span> <span data-ttu-id="460b7-125">當您建立互動式體驗時，請務必考慮這些資訊。</span><span class="sxs-lookup"><span data-stu-id="460b7-125">Be sure to think about these when building your interactive experiences.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="460b7-126">下一個開發檢查點</span><span class="sxs-lookup"><span data-stu-id="460b7-126">Next Development Checkpoint</span></span>

<span data-ttu-id="460b7-127">依循我們配置的 Unreal 開發檢查點旅程，此時您會探索 MRTK核心建置組塊。</span><span class="sxs-lookup"><span data-stu-id="460b7-127">If you're following the Unreal development checkpoint journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="460b7-128">接下來，您可以繼續進行下一個建置組塊：</span><span class="sxs-lookup"><span data-stu-id="460b7-128">From here, you can proceed to the next building block:</span></span> 

> [!div class="nextstepaction"]
> [<span data-ttu-id="460b7-129">手勢追蹤</span><span class="sxs-lookup"><span data-stu-id="460b7-129">Hand tracking</span></span>](unreal-hand-tracking.md)

<span data-ttu-id="460b7-130">或者，直接跳到混合實境平台功能和 API 的主題：</span><span class="sxs-lookup"><span data-stu-id="460b7-130">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="460b7-131">HoloLens 相機</span><span class="sxs-lookup"><span data-stu-id="460b7-131">HoloLens camera</span></span>](unreal-hololens-camera.md)

<span data-ttu-id="460b7-132">您可以隨時回到 [Unreal 開發檢查點](unreal-development-overview.md#2-core-building-blocks)。</span><span class="sxs-lookup"><span data-stu-id="460b7-132">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="460b7-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="460b7-133">See also</span></span>
* [<span data-ttu-id="460b7-134">校正</span><span class="sxs-lookup"><span data-stu-id="460b7-134">Calibration</span></span>](../../calibration.md)
* [<span data-ttu-id="460b7-135">舒適度</span><span class="sxs-lookup"><span data-stu-id="460b7-135">Comfort</span></span>](../../design/comfort.md)
* [<span data-ttu-id="460b7-136">目光和行動</span><span class="sxs-lookup"><span data-stu-id="460b7-136">Gaze and commit</span></span>](../../design/gaze-and-commit.md)
* [<span data-ttu-id="460b7-137">語音輸入</span><span class="sxs-lookup"><span data-stu-id="460b7-137">Voice input</span></span>](../../out-of-scope/voice-design.md)
