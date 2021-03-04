---
title: EyeTracking_Main
description: MRTK 中的眼睛追蹤登陸頁面
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、EyeTracking、
ms.openlocfilehash: 81d6ce7af74e1562da76c5c9467a3bf8519e28ab
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/03/2021
ms.locfileid: "101780558"
---
# <a name="eye-tracking-in-the-mixed-reality-toolkit"></a><span data-ttu-id="ae5f2-104">混合現實工具組中的眼睛追蹤</span><span class="sxs-lookup"><span data-stu-id="ae5f2-104">Eye tracking in the Mixed Reality Toolkit</span></span>

![MRTK 中的眼睛追蹤](../../images/eye-tracking/mrtk_et_compilation.png)

<span data-ttu-id="ae5f2-106">_HoloLens 2_ 提供令人興奮且強大的新輸入：眼睛追蹤！</span><span class="sxs-lookup"><span data-stu-id="ae5f2-106">_HoloLens 2_ offers an exciting and powerful new input: Eye tracking!</span></span>
<span data-ttu-id="ae5f2-107">目視追蹤可讓使用者快速且輕鬆地與全像間的全像觀賞，並藉由更妥善地識別使用者的意圖，讓您的系統更聰明。</span><span class="sxs-lookup"><span data-stu-id="ae5f2-107">Eye tracking enables users to quickly and effortlessly engage with holograms across their view and can make your system smarter by better identifying a user's intention.</span></span> <span data-ttu-id="ae5f2-108">如需詳細資訊，請參閱 Microsoft 的混合現實 [檔](https://docs.microsoft.com/windows/mixed-reality/eye-tracking) （如需詳細資訊），例如針對混合現實中的眼睛追蹤說明強大的應用程式和設計指導方針。</span><span class="sxs-lookup"><span data-stu-id="ae5f2-108">Check out Microsoft's Mixed Reality [documentation on eye tracking on HoloLens 2](https://docs.microsoft.com/windows/mixed-reality/eye-tracking) for more details, such as explaining powerful applications and design guidelines for eye tracking in mixed reality.</span></span>

<span data-ttu-id="ae5f2-109">剛開始進行眼追蹤？</span><span class="sxs-lookup"><span data-stu-id="ae5f2-109">New to eye tracking?</span></span> <span data-ttu-id="ae5f2-110">沒問題！</span><span class="sxs-lookup"><span data-stu-id="ae5f2-110">No problem!</span></span> <span data-ttu-id="ae5f2-111">有幾個影片、教學課程和範例可協助您開始使用 [混合現實工具](https://github.com/Microsoft/MixedRealityToolkit-Unity)組！</span><span class="sxs-lookup"><span data-stu-id="ae5f2-111">There are a number of videos, tutorials and samples to get you started in the [Mixed Reality Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity)!</span></span>
<span data-ttu-id="ae5f2-112">建議您一開始先探索一些現有的眼睛追蹤範例，這些範例會示範以眼睛為基礎之互動的最佳做法。</span><span class="sxs-lookup"><span data-stu-id="ae5f2-112">It is recommended to start by exploring some of the existing eye tracking samples that demonstrate best practices for eye-based interactions.</span></span> <span data-ttu-id="ae5f2-113">然後，您可以使用這些範例，將看起來與您相關的部分提取至您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="ae5f2-113">You can then use these samples to pull the parts that seem relevant to you into your app.</span></span> <span data-ttu-id="ae5f2-114">最後，我們也會說明如何設定具有核心元件的全新場景，以在您的應用程式中運作。</span><span class="sxs-lookup"><span data-stu-id="ae5f2-114">Finally, we also describe how to set up a fresh scene with the core components to get eye tracking working in your app.</span></span>

1. [<span data-ttu-id="ae5f2-115">MRTK 眼睛追蹤範例</span><span class="sxs-lookup"><span data-stu-id="ae5f2-115">MRTK eye tracking samples</span></span>](../../example-scenes/eye-tracking-examples-overview.md)

2. [<span data-ttu-id="ae5f2-116">MRTK 眼睛追蹤設定</span><span class="sxs-lookup"><span data-stu-id="ae5f2-116">MRTK eye tracking setup</span></span>](eye-tracking-basic-setup.md)

3. [<span data-ttu-id="ae5f2-117">透過程式碼存取眼睛追蹤資料</span><span class="sxs-lookup"><span data-stu-id="ae5f2-117">Accessing eye tracking data via Code</span></span>](eye-tracking-eye-gaze-provider.md)

4. [<span data-ttu-id="ae5f2-118">驗證裝置上的眼睛追蹤校正</span><span class="sxs-lookup"><span data-stu-id="ae5f2-118">Validate eye tracking calibration on device</span></span>](eye-tracking-is-user-calibrated.md)

## <a name="see-also"></a><span data-ttu-id="ae5f2-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ae5f2-119">See also</span></span>

- [<span data-ttu-id="ae5f2-120">MRTK 眼睛追蹤設定</span><span class="sxs-lookup"><span data-stu-id="ae5f2-120">MRTK Eye Tracking setup</span></span>](eye-tracking-basic-setup.md)
- [<span data-ttu-id="ae5f2-121">透過程式碼 MRTK 眼睛追蹤</span><span class="sxs-lookup"><span data-stu-id="ae5f2-121">MRTK Eye Tracking via Code</span></span>](eye-tracking-eye-gaze-provider.md)
- [<span data-ttu-id="ae5f2-122">MRTK 眼睛追蹤校正</span><span class="sxs-lookup"><span data-stu-id="ae5f2-122">MRTK Eye Tracking Calibration</span></span>](eye-tracking-is-user-calibrated.md)
- [<span data-ttu-id="ae5f2-123">HoloLens 2 目視追蹤檔</span><span class="sxs-lookup"><span data-stu-id="ae5f2-123">HoloLens 2 Eye Tracking Documentation</span></span>](https://docs.microsoft.com/windows/mixed-reality/eye-tracking)
