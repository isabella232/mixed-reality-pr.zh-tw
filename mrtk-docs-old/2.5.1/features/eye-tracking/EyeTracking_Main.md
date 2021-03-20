---
title: EyeTracking_Main
description: MRTK 中的眼睛追蹤登陸頁面
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、EyeTracking、
ms.openlocfilehash: 71dcdb119ce6e2d340392afe840f9eaea3efeb48
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104687268"
---
# <a name="eye-tracking-in-the-mixed-reality-toolkit"></a><span data-ttu-id="3e054-104">混合現實工具組中的眼睛追蹤</span><span class="sxs-lookup"><span data-stu-id="3e054-104">Eye tracking in the Mixed Reality Toolkit</span></span>

![MRTK 中的眼睛追蹤](../images/eye-tracking/mrtk_et_compilation.png)

<span data-ttu-id="3e054-106">_HoloLens 2_ 提供令人興奮且強大的新輸入：眼睛追蹤！</span><span class="sxs-lookup"><span data-stu-id="3e054-106">_HoloLens 2_ offers an exciting and powerful new input: Eye tracking!</span></span>
<span data-ttu-id="3e054-107">目視追蹤可讓使用者快速且輕鬆地與全像間的全像觀賞，並藉由更妥善地識別使用者的意圖，讓您的系統更聰明。</span><span class="sxs-lookup"><span data-stu-id="3e054-107">Eye tracking enables users to quickly and effortlessly engage with holograms across their view and can make your system smarter by better identifying a user's intention.</span></span> <span data-ttu-id="3e054-108">如需詳細資訊，請參閱 Microsoft 的混合現實檔，以瞭解有關 [HoloLens 2 的紅眼](https://docs.microsoft.com/windows/mixed-reality/eye-tracking) 追蹤，例如說明強大的應用程式，以及在混合現實中追蹤眼睛的設計指導方針。</span><span class="sxs-lookup"><span data-stu-id="3e054-108">Check out Microsoft's Mixed Reality [documentation on eye tracking on HoloLens 2](https://docs.microsoft.com/windows/mixed-reality/eye-tracking) for more details, such as explaining powerful applications and design guidelines for eye tracking in mixed reality.</span></span>

<span data-ttu-id="3e054-109">剛開始進行眼追蹤？</span><span class="sxs-lookup"><span data-stu-id="3e054-109">New to eye tracking?</span></span> <span data-ttu-id="3e054-110">沒問題！</span><span class="sxs-lookup"><span data-stu-id="3e054-110">No problem!</span></span> <span data-ttu-id="3e054-111">有幾個影片、教學課程和範例可協助您開始使用 [混合現實工具](https://github.com/Microsoft/MixedRealityToolkit-Unity)組！</span><span class="sxs-lookup"><span data-stu-id="3e054-111">There are a number of videos, tutorials and samples to get you started in the [Mixed Reality Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity)!</span></span>
<span data-ttu-id="3e054-112">建議您一開始先探索一些現有的眼睛追蹤範例，這些範例會示範以眼睛為基礎之互動的最佳做法。</span><span class="sxs-lookup"><span data-stu-id="3e054-112">It is recommended to start by exploring some of the existing eye tracking samples that demonstrate best practices for eye-based interactions.</span></span> <span data-ttu-id="3e054-113">然後，您可以使用這些範例，將看起來與您相關的部分提取至您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="3e054-113">You can then use these samples to pull the parts that seem relevant to you into your app.</span></span> <span data-ttu-id="3e054-114">最後，我們也會說明如何設定具有核心元件的全新場景，以在您的應用程式中運作。</span><span class="sxs-lookup"><span data-stu-id="3e054-114">Finally, we also describe how to set up a fresh scene with the core components to get eye tracking working in your app.</span></span>

1. [<span data-ttu-id="3e054-115">MRTK 眼睛追蹤範例</span><span class="sxs-lookup"><span data-stu-id="3e054-115">MRTK eye tracking samples</span></span>](EyeTracking_ExamplesOverview.md)

2. [<span data-ttu-id="3e054-116">MRTK 眼睛追蹤設定</span><span class="sxs-lookup"><span data-stu-id="3e054-116">MRTK eye tracking setup</span></span>](EyeTracking_BasicSetup.md)

3. [<span data-ttu-id="3e054-117">透過程式碼存取眼睛追蹤資料</span><span class="sxs-lookup"><span data-stu-id="3e054-117">Accessing eye tracking data via Code</span></span>](EyeTracking_EyeGazeProvider.md)

4. [<span data-ttu-id="3e054-118">驗證裝置上的眼睛追蹤校正</span><span class="sxs-lookup"><span data-stu-id="3e054-118">Validate eye tracking calibration on device</span></span>](EyeTracking_IsUserCalibrated.md)

## <a name="see-also"></a><span data-ttu-id="3e054-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3e054-119">See also</span></span>

- [<span data-ttu-id="3e054-120">MRTK 眼睛追蹤設定</span><span class="sxs-lookup"><span data-stu-id="3e054-120">MRTK Eye Tracking setup</span></span>](EyeTracking_BasicSetup.md)
- [<span data-ttu-id="3e054-121">透過程式碼 MRTK 眼睛追蹤</span><span class="sxs-lookup"><span data-stu-id="3e054-121">MRTK Eye Tracking via Code</span></span>](EyeTracking_EyeGazeProvider.md)
- [<span data-ttu-id="3e054-122">MRTK 眼睛追蹤校正</span><span class="sxs-lookup"><span data-stu-id="3e054-122">MRTK Eye Tracking Calibration</span></span>](EyeTracking_IsUserCalibrated.md)
- [<span data-ttu-id="3e054-123">HoloLens 2 眼睛追蹤檔</span><span class="sxs-lookup"><span data-stu-id="3e054-123">HoloLens 2 Eye Tracking Documentation</span></span>](https://docs.microsoft.com/windows/mixed-reality/eye-tracking)
