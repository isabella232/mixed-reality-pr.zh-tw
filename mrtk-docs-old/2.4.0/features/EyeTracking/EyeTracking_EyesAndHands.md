---
title: EyeTracking_EyesAndHands
description: 如何搭配 MRTK 中的手運動使用眼睛目標作為主要指標
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
ms.localizationpriority: medium
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、EyeTracking、
ms.openlocfilehash: e3436bb361f0407c8a3b7a57cdf5f52f2a9a910a
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104690865"
---
# <a name="eyes--hand-interaction"></a><span data-ttu-id="69e0a-104">眼睛 + 手互動</span><span class="sxs-lookup"><span data-stu-id="69e0a-104">Eyes + hand interaction</span></span>

## <a name="how-to-support-_look--hand-motions_-eye-gaze--hand-gestures"></a><span data-ttu-id="69e0a-105">如何支援 _外觀 + 手運動_ (眼睛 & 手勢) </span><span class="sxs-lookup"><span data-stu-id="69e0a-105">How to support _look + hand motions_ (eye gaze & hand gestures)</span></span>

<span data-ttu-id="69e0a-106">此頁面說明如何使用眼睛目標作為與手運動組合的主要指標。</span><span class="sxs-lookup"><span data-stu-id="69e0a-106">This page explains how to use eye targeting as a primary pointer in combination with hand motions.</span></span>
<span data-ttu-id="69e0a-107">在我們的 [MRTK 眼追蹤示範](EyeTracking_ExamplesOverview.md)中，我們會說明使用眼睛 + 手的數個範例，例如：</span><span class="sxs-lookup"><span data-stu-id="69e0a-107">In our [MRTK eye tracking demos](EyeTracking_ExamplesOverview.md), we describe several examples for using eyes + hands, for example:</span></span>

- <span data-ttu-id="69e0a-108">[選擇](EyeTracking_TargetSelection.md)：查看遙遠的全像全像，然後執行縮小的手勢來快速選取它。</span><span class="sxs-lookup"><span data-stu-id="69e0a-108">[Selection](EyeTracking_TargetSelection.md): Looking at distant holographic button and simply performing a pinch gesture to quickly select it.</span></span>
- <span data-ttu-id="69e0a-109">[定位](EyeTracking_Positioning.md)：流暢在您的場景中移動全像投影、捏合您的食指和 thumb 以抓取，然後使用您的手四處移動。</span><span class="sxs-lookup"><span data-stu-id="69e0a-109">[Positioning](EyeTracking_Positioning.md): Fluently move a hologram across your scene by simply looking at it, pinching your index finger and thumb together to grab it and then move it around using your hand.</span></span>
- <span data-ttu-id="69e0a-110">[導覽](EyeTracking_Navigation.md)：只需查看您想要放大的位置，並將您的索引手指與 thumb 一起放大 _，並朝_ 您手上一步。</span><span class="sxs-lookup"><span data-stu-id="69e0a-110">[Navigation](EyeTracking_Navigation.md): Simply look at a location you want to zoom in, pinch your index finger and thumb together and _pull_ your hand toward you to zoom in.</span></span>

<span data-ttu-id="69e0a-111">請注意，MRTK 目前的設計方式，是以距離光線作為優先的焦點指標。</span><span class="sxs-lookup"><span data-stu-id="69e0a-111">Please note that MRTK is currently designed in a way that at a distance hand rays act as the prioritized focus pointers.</span></span>
<span data-ttu-id="69e0a-112">這表示在偵測到手上時，就會自動隱藏 head 和眼睛的指標。</span><span class="sxs-lookup"><span data-stu-id="69e0a-112">This means that the head and eye gaze pointers will automatically be suppressed once a hand is detected.</span></span>
<span data-ttu-id="69e0a-113">不過，這可能不是您想要在某處互動的方式，而是比您的觀點來看單純的「 _注視和認可_ 」互動。</span><span class="sxs-lookup"><span data-stu-id="69e0a-113">However, this may not be the way you would like to interact at a distance and rather favor a simple _'gaze and commit'_ interaction independent of the presence of hands in your view.</span></span>

### <a name="how-to-disable-the-hand-ray"></a><span data-ttu-id="69e0a-114">如何停用手光線</span><span class="sxs-lookup"><span data-stu-id="69e0a-114">How to disable the hand ray</span></span>

<span data-ttu-id="69e0a-115">若要停用手光線指標，只要移除 _輸入 > 指標_ MRTK 設定中的 _' DefaultControllerPointer '_ 。</span><span class="sxs-lookup"><span data-stu-id="69e0a-115">To disable the hand ray pointer, simply remove the _'DefaultControllerPointer'_ in your _Input -> Pointer_ MRTK configuration setting.</span></span>
<span data-ttu-id="69e0a-116">若要在您的應用程式中使用眼睛和手（如上所述），也請確定您符合 [使用眼睛追蹤](EyeTracking_BasicSetup.md)的所有需求。</span><span class="sxs-lookup"><span data-stu-id="69e0a-116">To use eyes and hands as described above in your app, please also make sure that you meet all of the [requirements for using eye tracking](EyeTracking_BasicSetup.md).</span></span>

![如何卸下手光線](../Images/EyeTracking/mrtk_setup_removehandray.jpg)

<span data-ttu-id="69e0a-118">您也可以查看，從眼睛追蹤範例套件 _EyeTrackingDemoPointerProfile_ 的輸入設定檔如何設定為參考。</span><span class="sxs-lookup"><span data-stu-id="69e0a-118">You can also check out, how the input profile _EyeTrackingDemoPointerProfile_ from the eye tracking sample package is set up as a reference.</span></span>

---
[<span data-ttu-id="69e0a-119">回到「MixedRealityToolkit 中的眼睛追蹤」</span><span class="sxs-lookup"><span data-stu-id="69e0a-119">Back to "Eye tracking in the MixedRealityToolkit"</span></span>](EyeTracking_Main.md)
