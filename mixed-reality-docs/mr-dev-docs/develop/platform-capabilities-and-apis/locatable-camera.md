---
title: 定位相機
description: HoloLens 正面相機、運作方式，以及可供開發人員使用的設定檔和解決方案的一般資訊。
author: cdedmonds
ms.author: wguyman
ms.date: 06/12/2019
ms.topic: article
keywords: 攝影機、hololens、彩色攝影機、正面、hololens 2、cv、電腦視覺、基準、標記、qr 代碼、qr、相片、影片
ms.openlocfilehash: 9261465f362e6aa0e97d9f6b1f61af305c178079
ms.sourcegitcommit: c41372e0c6ca265f599bff309390982642d628b8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/15/2020
ms.locfileid: "97530380"
---
# <a name="locatable-camera"></a><span data-ttu-id="e7978-104">定位相機</span><span class="sxs-lookup"><span data-stu-id="e7978-104">Locatable camera</span></span>

<span data-ttu-id="e7978-105">HoloLens 包含掛接在裝置前方的全球面向相機，可讓應用程式查看使用者看到的內容。</span><span class="sxs-lookup"><span data-stu-id="e7978-105">HoloLens includes a world-facing camera mounted on the front of the device, which enables apps to see what the user sees.</span></span> <span data-ttu-id="e7978-106">開發人員可以存取和控制攝影機，就像在 smartphone、筆記本電腦或桌上型電腦上的彩色攝影機一樣。</span><span class="sxs-lookup"><span data-stu-id="e7978-106">Developers have access to and control of the camera, just as they would for color cameras on smartphones, portables, or desktops.</span></span> <span data-ttu-id="e7978-107">適用于行動裝置和桌上型電腦的相同通用 windows [media capture](https://msdn.microsoft.com/library/windows/apps/windows.media.capture.mediacapture.aspx) 和 windows Media foundation api 可在 HoloLens 上運作。</span><span class="sxs-lookup"><span data-stu-id="e7978-107">The same universal windows [media capture](https://msdn.microsoft.com/library/windows/apps/windows.media.capture.mediacapture.aspx) and windows media foundation APIs that work on mobile and desktop work on HoloLens.</span></span> <span data-ttu-id="e7978-108">Unity [已將這些 Windows api 包裝](../unity/locatable-camera-in-unity.md) 成可在 HoloLens 上抽象化相機使用功能。</span><span class="sxs-lookup"><span data-stu-id="e7978-108">Unity [has wrapped these windows APIs](../unity/locatable-camera-in-unity.md) to abstract camera usage features on HoloLens.</span></span> <span data-ttu-id="e7978-109">功能工作包括將一般相片和影片 (與或不含全像投影) ，以及在場景中找出相機的位置和觀點。</span><span class="sxs-lookup"><span data-stu-id="e7978-109">Feature tasks include taking regular photos and videos (with or without holograms) and locating the camera's position in and perspective on the scene.</span></span>

## <a name="device-camera-information"></a><span data-ttu-id="e7978-110">裝置相機資訊</span><span class="sxs-lookup"><span data-stu-id="e7978-110">Device camera information</span></span>

### <a name="hololens-first-generation"></a><span data-ttu-id="e7978-111">HoloLens (第一代) </span><span class="sxs-lookup"><span data-stu-id="e7978-111">HoloLens (first-generation)</span></span>

* <span data-ttu-id="e7978-112">已修正焦點相片/影片 (PV) 攝影機與自動白平衡、自動曝光和完整的影像處理管線。</span><span class="sxs-lookup"><span data-stu-id="e7978-112">Fixed focus photo/video (PV) camera with auto white balance, auto exposure, and full image-processing pipeline.</span></span>
* <span data-ttu-id="e7978-113">當相機處於作用中狀態時，世界上的白色隱私權 LED 將會發亮</span><span class="sxs-lookup"><span data-stu-id="e7978-113">White Privacy LED facing the world will illuminate whenever the camera is active</span></span>
* <span data-ttu-id="e7978-114">攝影機支援下列模式 (所有模式都是16:9 的外觀比例) 30、24、20、15和 5 fps：</span><span class="sxs-lookup"><span data-stu-id="e7978-114">The camera supports the following modes (all modes are 16:9 aspect ratio) at 30, 24, 20, 15, and 5 fps:</span></span>

  |  <span data-ttu-id="e7978-115">影片</span><span class="sxs-lookup"><span data-stu-id="e7978-115">Video</span></span>  |  <span data-ttu-id="e7978-116">預覽</span><span class="sxs-lookup"><span data-stu-id="e7978-116">Preview</span></span>  |  <span data-ttu-id="e7978-117">還</span><span class="sxs-lookup"><span data-stu-id="e7978-117">Still</span></span>  |  <span data-ttu-id="e7978-118">水準視圖 (H-FOV) </span><span class="sxs-lookup"><span data-stu-id="e7978-118">Horizontal Field of View (H-FOV)</span></span> |  <span data-ttu-id="e7978-119">建議用法</span><span class="sxs-lookup"><span data-stu-id="e7978-119">Suggested usage</span></span> | 
  |----------|----------|----------|----------|----------|
  |  <span data-ttu-id="e7978-120">1280x720</span><span class="sxs-lookup"><span data-stu-id="e7978-120">1280x720</span></span> |  <span data-ttu-id="e7978-121">1280x720</span><span class="sxs-lookup"><span data-stu-id="e7978-121">1280x720</span></span> |  <span data-ttu-id="e7978-122">1280x720</span><span class="sxs-lookup"><span data-stu-id="e7978-122">1280x720</span></span> |  <span data-ttu-id="e7978-123">45度</span><span class="sxs-lookup"><span data-stu-id="e7978-123">45 deg</span></span>  |  <span data-ttu-id="e7978-124">使用影片穩定)  (預設模式</span><span class="sxs-lookup"><span data-stu-id="e7978-124">(default mode with video stabilization)</span></span> | 
  |  <span data-ttu-id="e7978-125">不適用</span><span class="sxs-lookup"><span data-stu-id="e7978-125">N/A</span></span> |  <span data-ttu-id="e7978-126">不適用</span><span class="sxs-lookup"><span data-stu-id="e7978-126">N/A</span></span> |  <span data-ttu-id="e7978-127">2048x1152</span><span class="sxs-lookup"><span data-stu-id="e7978-127">2048x1152</span></span> |  <span data-ttu-id="e7978-128">67度</span><span class="sxs-lookup"><span data-stu-id="e7978-128">67 deg</span></span> |  <span data-ttu-id="e7978-129">最高解析度仍為影像</span><span class="sxs-lookup"><span data-stu-id="e7978-129">Highest resolution still image</span></span> | 
  |  <span data-ttu-id="e7978-130">1408x792</span><span class="sxs-lookup"><span data-stu-id="e7978-130">1408x792</span></span> |  <span data-ttu-id="e7978-131">1408x792</span><span class="sxs-lookup"><span data-stu-id="e7978-131">1408x792</span></span> |  <span data-ttu-id="e7978-132">1408x792</span><span class="sxs-lookup"><span data-stu-id="e7978-132">1408x792</span></span> |  <span data-ttu-id="e7978-133">48度</span><span class="sxs-lookup"><span data-stu-id="e7978-133">48 deg</span></span> |  <span data-ttu-id="e7978-134">Overscan (填補影片穩定之前的) 解析度</span><span class="sxs-lookup"><span data-stu-id="e7978-134">Overscan (padding) resolution before video stabilization</span></span> | 
  |  <span data-ttu-id="e7978-135">1344x756</span><span class="sxs-lookup"><span data-stu-id="e7978-135">1344x756</span></span> |  <span data-ttu-id="e7978-136">1344x756</span><span class="sxs-lookup"><span data-stu-id="e7978-136">1344x756</span></span> |  <span data-ttu-id="e7978-137">1344x756</span><span class="sxs-lookup"><span data-stu-id="e7978-137">1344x756</span></span> |  <span data-ttu-id="e7978-138">67度</span><span class="sxs-lookup"><span data-stu-id="e7978-138">67 deg</span></span> |  <span data-ttu-id="e7978-139">使用 overscan 的大型 FOV 影片模式</span><span class="sxs-lookup"><span data-stu-id="e7978-139">Large FOV video mode with overscan</span></span> | 
  |  <span data-ttu-id="e7978-140">896x504</span><span class="sxs-lookup"><span data-stu-id="e7978-140">896x504</span></span> |  <span data-ttu-id="e7978-141">896x504</span><span class="sxs-lookup"><span data-stu-id="e7978-141">896x504</span></span> |  <span data-ttu-id="e7978-142">896x504</span><span class="sxs-lookup"><span data-stu-id="e7978-142">896x504</span></span> |  <span data-ttu-id="e7978-143">48度</span><span class="sxs-lookup"><span data-stu-id="e7978-143">48 deg</span></span> |  <span data-ttu-id="e7978-144">影像處理工作的低電源/低解析度模式</span><span class="sxs-lookup"><span data-stu-id="e7978-144">Low power / Low-resolution mode for image-processing tasks</span></span> | 

### <a name="hololens-2"></a><span data-ttu-id="e7978-145">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="e7978-145">HoloLens 2</span></span>

* <span data-ttu-id="e7978-146">自動聚焦相片/影片 (PV) 攝影機（具有自動白平衡、自動曝光和完整的影像處理管線）。</span><span class="sxs-lookup"><span data-stu-id="e7978-146">Auto-focus photo/video (PV) camera with auto white balance, auto exposure, and full image-processing pipeline.</span></span>
* <span data-ttu-id="e7978-147">當相機處於作用中狀態時，就會導致世界各地的白色隱私權燈亮著。</span><span class="sxs-lookup"><span data-stu-id="e7978-147">White Privacy LED facing the world will illuminate whenever the camera is active.</span></span>
* <span data-ttu-id="e7978-148">HoloLens 2 支援不同的相機設定檔。</span><span class="sxs-lookup"><span data-stu-id="e7978-148">HoloLens 2 supports different camera profiles.</span></span> <span data-ttu-id="e7978-149">瞭解如何 [探索並選取攝影機功能](https://docs.microsoft.com//windows/uwp/audio-video-camera/camera-profiles)。</span><span class="sxs-lookup"><span data-stu-id="e7978-149">Learn how to [discover and select camera capabilities](https://docs.microsoft.com//windows/uwp/audio-video-camera/camera-profiles).</span></span>
* <span data-ttu-id="e7978-150">攝影機支援下列設定檔和解析度 (所有的影片模式都是16:9 的外觀比例) ：</span><span class="sxs-lookup"><span data-stu-id="e7978-150">The camera supports the following profiles and resolutions (all video modes are 16:9 aspect ratio):</span></span>
  
  | <span data-ttu-id="e7978-151">設定檔</span><span class="sxs-lookup"><span data-stu-id="e7978-151">Profile</span></span>                                         | <span data-ttu-id="e7978-152">影片</span><span class="sxs-lookup"><span data-stu-id="e7978-152">Video</span></span>     | <span data-ttu-id="e7978-153">預覽</span><span class="sxs-lookup"><span data-stu-id="e7978-153">Preview</span></span>   | <span data-ttu-id="e7978-154">還</span><span class="sxs-lookup"><span data-stu-id="e7978-154">Still</span></span>     | <span data-ttu-id="e7978-155">畫面播放速率</span><span class="sxs-lookup"><span data-stu-id="e7978-155">Frame rates</span></span> | <span data-ttu-id="e7978-156">水準視圖 (H-FOV) </span><span class="sxs-lookup"><span data-stu-id="e7978-156">Horizontal Field of View (H-FOV)</span></span> | <span data-ttu-id="e7978-157">建議用法</span><span class="sxs-lookup"><span data-stu-id="e7978-157">Suggested usage</span></span>                             |
  |-------------------------------------------------|-----------|-----------|-----------|-------------|----------------------------------|---------------------------------------------|
  | <span data-ttu-id="e7978-158">舊版、0 BalancedVideoAndPhoto、100</span><span class="sxs-lookup"><span data-stu-id="e7978-158">Legacy,0  BalancedVideoAndPhoto,100</span></span>             | <span data-ttu-id="e7978-159">2272x1278</span><span class="sxs-lookup"><span data-stu-id="e7978-159">2272x1278</span></span> | <span data-ttu-id="e7978-160">2272x1278</span><span class="sxs-lookup"><span data-stu-id="e7978-160">2272x1278</span></span> |           | <span data-ttu-id="e7978-161">15.30</span><span class="sxs-lookup"><span data-stu-id="e7978-161">15.30</span></span>       | <span data-ttu-id="e7978-162">64.69</span><span class="sxs-lookup"><span data-stu-id="e7978-162">64.69</span></span>                            | <span data-ttu-id="e7978-163">高品質的影片錄製</span><span class="sxs-lookup"><span data-stu-id="e7978-163">High-quality video recording</span></span>                |
  | <span data-ttu-id="e7978-164">舊版、0 BalancedVideoAndPhoto、100</span><span class="sxs-lookup"><span data-stu-id="e7978-164">Legacy,0  BalancedVideoAndPhoto,100</span></span>             | <span data-ttu-id="e7978-165">896x504</span><span class="sxs-lookup"><span data-stu-id="e7978-165">896x504</span></span>   | <span data-ttu-id="e7978-166">896x504</span><span class="sxs-lookup"><span data-stu-id="e7978-166">896x504</span></span>   |           | <span data-ttu-id="e7978-167">15.30</span><span class="sxs-lookup"><span data-stu-id="e7978-167">15.30</span></span>       | <span data-ttu-id="e7978-168">64.69</span><span class="sxs-lookup"><span data-stu-id="e7978-168">64.69</span></span>                            | <span data-ttu-id="e7978-169">適用于高品質相片捕捉的預覽串流</span><span class="sxs-lookup"><span data-stu-id="e7978-169">Preview stream for high-quality photo capture</span></span> |
  | <span data-ttu-id="e7978-170">舊版、0 BalancedVideoAndPhoto、100</span><span class="sxs-lookup"><span data-stu-id="e7978-170">Legacy,0  BalancedVideoAndPhoto,100</span></span>             |           |           | <span data-ttu-id="e7978-171">3904x2196</span><span class="sxs-lookup"><span data-stu-id="e7978-171">3904x2196</span></span> |             | <span data-ttu-id="e7978-172">64.69</span><span class="sxs-lookup"><span data-stu-id="e7978-172">64.69</span></span>                            | <span data-ttu-id="e7978-173">高品質的相片捕捉</span><span class="sxs-lookup"><span data-stu-id="e7978-173">High-quality photo capture</span></span>                  |
  | <span data-ttu-id="e7978-174">BalancedVideoAndPhoto，120</span><span class="sxs-lookup"><span data-stu-id="e7978-174">BalancedVideoAndPhoto, 120</span></span>                       | <span data-ttu-id="e7978-175">1952x1100</span><span class="sxs-lookup"><span data-stu-id="e7978-175">1952x1100</span></span> | <span data-ttu-id="e7978-176">1952x1100</span><span class="sxs-lookup"><span data-stu-id="e7978-176">1952x1100</span></span> | <span data-ttu-id="e7978-177">1952x1100</span><span class="sxs-lookup"><span data-stu-id="e7978-177">1952x1100</span></span> | <span data-ttu-id="e7978-178">15.30</span><span class="sxs-lookup"><span data-stu-id="e7978-178">15.30</span></span>       | <span data-ttu-id="e7978-179">64.69</span><span class="sxs-lookup"><span data-stu-id="e7978-179">64.69</span></span>                            | <span data-ttu-id="e7978-180">長時間案例</span><span class="sxs-lookup"><span data-stu-id="e7978-180">Long duration scenarios</span></span>                     |
  | <span data-ttu-id="e7978-181">BalancedVideoAndPhoto，120</span><span class="sxs-lookup"><span data-stu-id="e7978-181">BalancedVideoAndPhoto, 120</span></span>                       | <span data-ttu-id="e7978-182">1504x846</span><span class="sxs-lookup"><span data-stu-id="e7978-182">1504x846</span></span>  | <span data-ttu-id="e7978-183">1504x846</span><span class="sxs-lookup"><span data-stu-id="e7978-183">1504x846</span></span>  |           | <span data-ttu-id="e7978-184">15.30</span><span class="sxs-lookup"><span data-stu-id="e7978-184">15.30</span></span>       | <span data-ttu-id="e7978-185">64.69</span><span class="sxs-lookup"><span data-stu-id="e7978-185">64.69</span></span>                            | <span data-ttu-id="e7978-186">長時間案例</span><span class="sxs-lookup"><span data-stu-id="e7978-186">Long duration scenarios</span></span>                     |
  | <span data-ttu-id="e7978-187">視訊會議，100</span><span class="sxs-lookup"><span data-stu-id="e7978-187">VideoConferencing,100</span></span>                           | <span data-ttu-id="e7978-188">1952x1100</span><span class="sxs-lookup"><span data-stu-id="e7978-188">1952x1100</span></span> | <span data-ttu-id="e7978-189">1952x1100</span><span class="sxs-lookup"><span data-stu-id="e7978-189">1952x1100</span></span> | <span data-ttu-id="e7978-190">1952x1100</span><span class="sxs-lookup"><span data-stu-id="e7978-190">1952x1100</span></span> | <span data-ttu-id="e7978-191">15、30、60</span><span class="sxs-lookup"><span data-stu-id="e7978-191">15,30,60</span></span>    | <span data-ttu-id="e7978-192">64.69</span><span class="sxs-lookup"><span data-stu-id="e7978-192">64.69</span></span>                            | <span data-ttu-id="e7978-193">視訊會議，長時間案例</span><span class="sxs-lookup"><span data-stu-id="e7978-193">Video conferencing, long duration scenarios</span></span> |
  | <span data-ttu-id="e7978-194">視訊會議，100</span><span class="sxs-lookup"><span data-stu-id="e7978-194">Videoconferencing,100</span></span>                           | <span data-ttu-id="e7978-195">1504x846</span><span class="sxs-lookup"><span data-stu-id="e7978-195">1504x846</span></span>  | <span data-ttu-id="e7978-196">1504x846</span><span class="sxs-lookup"><span data-stu-id="e7978-196">1504x846</span></span>  |           | <span data-ttu-id="e7978-197">5、15、30、60</span><span class="sxs-lookup"><span data-stu-id="e7978-197">5,15,30,60</span></span>  | <span data-ttu-id="e7978-198">64.69</span><span class="sxs-lookup"><span data-stu-id="e7978-198">64.69</span></span>                            | <span data-ttu-id="e7978-199">視訊會議，長時間案例</span><span class="sxs-lookup"><span data-stu-id="e7978-199">Video conferencing, long duration scenarios</span></span> |
  | <span data-ttu-id="e7978-200">視訊會議，100 BalancedVideoAndPhoto，120</span><span class="sxs-lookup"><span data-stu-id="e7978-200">Videoconferencing,100 BalancedVideoAndPhoto,120</span></span> | <span data-ttu-id="e7978-201">1920x1080</span><span class="sxs-lookup"><span data-stu-id="e7978-201">1920x1080</span></span> | <span data-ttu-id="e7978-202">1920x1080</span><span class="sxs-lookup"><span data-stu-id="e7978-202">1920x1080</span></span> | <span data-ttu-id="e7978-203">1920x1080</span><span class="sxs-lookup"><span data-stu-id="e7978-203">1920x1080</span></span> | <span data-ttu-id="e7978-204">15、30</span><span class="sxs-lookup"><span data-stu-id="e7978-204">15,30</span></span>       | <span data-ttu-id="e7978-205">64.69</span><span class="sxs-lookup"><span data-stu-id="e7978-205">64.69</span></span>                            | <span data-ttu-id="e7978-206">視訊會議，長時間案例</span><span class="sxs-lookup"><span data-stu-id="e7978-206">Video conferencing, long duration scenarios</span></span> |
  | <span data-ttu-id="e7978-207">視訊會議，100 BalancedVideoAndPhoto，120</span><span class="sxs-lookup"><span data-stu-id="e7978-207">Videoconferencing,100 BalancedVideoAndPhoto,120</span></span> | <span data-ttu-id="e7978-208">1280x720</span><span class="sxs-lookup"><span data-stu-id="e7978-208">1280x720</span></span>  | <span data-ttu-id="e7978-209">1280x720</span><span class="sxs-lookup"><span data-stu-id="e7978-209">1280x720</span></span>  | <span data-ttu-id="e7978-210">1280x720</span><span class="sxs-lookup"><span data-stu-id="e7978-210">1280x720</span></span>  | <span data-ttu-id="e7978-211">15、30</span><span class="sxs-lookup"><span data-stu-id="e7978-211">15,30</span></span>       | <span data-ttu-id="e7978-212">64.69</span><span class="sxs-lookup"><span data-stu-id="e7978-212">64.69</span></span>                            | <span data-ttu-id="e7978-213">視訊會議，長時間案例</span><span class="sxs-lookup"><span data-stu-id="e7978-213">Video conferencing, long duration scenarios</span></span> |
  | <span data-ttu-id="e7978-214">視訊會議，100 BalancedVideoAndPhoto，120</span><span class="sxs-lookup"><span data-stu-id="e7978-214">Videoconferencing,100 BalancedVideoAndPhoto,120</span></span> | <span data-ttu-id="e7978-215">1128x636</span><span class="sxs-lookup"><span data-stu-id="e7978-215">1128x636</span></span>  |           |           | <span data-ttu-id="e7978-216">15、30</span><span class="sxs-lookup"><span data-stu-id="e7978-216">15,30</span></span>       | <span data-ttu-id="e7978-217">64.69</span><span class="sxs-lookup"><span data-stu-id="e7978-217">64.69</span></span>                            | <span data-ttu-id="e7978-218">視訊會議，長時間案例</span><span class="sxs-lookup"><span data-stu-id="e7978-218">Video conferencing, long duration scenarios</span></span> |
  | <span data-ttu-id="e7978-219">視訊會議，100 BalancedVideoAndPhoto，120</span><span class="sxs-lookup"><span data-stu-id="e7978-219">Videoconferencing,100 BalancedVideoAndPhoto,120</span></span> | <span data-ttu-id="e7978-220">960x540</span><span class="sxs-lookup"><span data-stu-id="e7978-220">960x540</span></span>   |           |           | <span data-ttu-id="e7978-221">15、30</span><span class="sxs-lookup"><span data-stu-id="e7978-221">15,30</span></span>       | <span data-ttu-id="e7978-222">64.69</span><span class="sxs-lookup"><span data-stu-id="e7978-222">64.69</span></span>                            | <span data-ttu-id="e7978-223">視訊會議，長時間案例</span><span class="sxs-lookup"><span data-stu-id="e7978-223">Video conferencing, long duration scenarios</span></span> |
  | <span data-ttu-id="e7978-224">視訊會議，100 BalancedVideoAndPhoto，120</span><span class="sxs-lookup"><span data-stu-id="e7978-224">Videoconferencing,100 BalancedVideoAndPhoto,120</span></span> | <span data-ttu-id="e7978-225">760x428</span><span class="sxs-lookup"><span data-stu-id="e7978-225">760x428</span></span>   |           |           | <span data-ttu-id="e7978-226">15、30</span><span class="sxs-lookup"><span data-stu-id="e7978-226">15,30</span></span>       | <span data-ttu-id="e7978-227">64.69</span><span class="sxs-lookup"><span data-stu-id="e7978-227">64.69</span></span>                            | <span data-ttu-id="e7978-228">視訊會議，長時間案例</span><span class="sxs-lookup"><span data-stu-id="e7978-228">Video conferencing, long duration scenarios</span></span> |
  | <span data-ttu-id="e7978-229">視訊會議，100 BalancedVideoAndPhoto，120</span><span class="sxs-lookup"><span data-stu-id="e7978-229">Videoconferencing,100 BalancedVideoAndPhoto,120</span></span> | <span data-ttu-id="e7978-230">640x360</span><span class="sxs-lookup"><span data-stu-id="e7978-230">640x360</span></span>   |           |           | <span data-ttu-id="e7978-231">15、30</span><span class="sxs-lookup"><span data-stu-id="e7978-231">15,30</span></span>       | <span data-ttu-id="e7978-232">64.69</span><span class="sxs-lookup"><span data-stu-id="e7978-232">64.69</span></span>                            | <span data-ttu-id="e7978-233">視訊會議，長時間案例</span><span class="sxs-lookup"><span data-stu-id="e7978-233">Video conferencing, long duration scenarios</span></span> |
  | <span data-ttu-id="e7978-234">視訊會議，100 BalancedVideoAndPhoto，120</span><span class="sxs-lookup"><span data-stu-id="e7978-234">Videoconferencing,100 BalancedVideoAndPhoto,120</span></span> | <span data-ttu-id="e7978-235">500x282</span><span class="sxs-lookup"><span data-stu-id="e7978-235">500x282</span></span>   |           |           | <span data-ttu-id="e7978-236">15、30</span><span class="sxs-lookup"><span data-stu-id="e7978-236">15,30</span></span>       | <span data-ttu-id="e7978-237">64.69</span><span class="sxs-lookup"><span data-stu-id="e7978-237">64.69</span></span>                            | <span data-ttu-id="e7978-238">視訊會議，長時間案例</span><span class="sxs-lookup"><span data-stu-id="e7978-238">Video conferencing, long duration scenarios</span></span> |
  | <span data-ttu-id="e7978-239">視訊會議，100 BalancedVideoAndPhoto，120</span><span class="sxs-lookup"><span data-stu-id="e7978-239">Videoconferencing,100 BalancedVideoAndPhoto,120</span></span> | <span data-ttu-id="e7978-240">424x240</span><span class="sxs-lookup"><span data-stu-id="e7978-240">424x240</span></span>   |           |           | <span data-ttu-id="e7978-241">15、30</span><span class="sxs-lookup"><span data-stu-id="e7978-241">15,30</span></span>       | <span data-ttu-id="e7978-242">64.69</span><span class="sxs-lookup"><span data-stu-id="e7978-242">64.69</span></span>                            | <span data-ttu-id="e7978-243">視訊會議，長時間案例</span><span class="sxs-lookup"><span data-stu-id="e7978-243">Video conferencing, long duration scenarios</span></span> |

> [!NOTE]
> <span data-ttu-id="e7978-244">客戶可以利用 [混合的現實 capture](../../mixed-reality-capture.md) 來拍攝您應用程式的影片或相片，包括全像全像觀賞和影片穩定。</span><span class="sxs-lookup"><span data-stu-id="e7978-244">Customers can leverage [mixed reality capture](../../mixed-reality-capture.md) to take videos or photos of your app, which include holograms and video stabilization.</span></span>
>
><span data-ttu-id="e7978-245">開發人員在建立應用程式時，如果您想要在客戶捕獲內容時盡可能地查看，則有一些考慮需要考慮。</span><span class="sxs-lookup"><span data-stu-id="e7978-245">As a developer, there are considerations you should take into account when creating your app if you want it to look as good as possible when a customer captures content.</span></span> <span data-ttu-id="e7978-246">您也可以直接在應用程式內啟用 (和自訂) mixed reality capture。</span><span class="sxs-lookup"><span data-stu-id="e7978-246">You can also enable (and customize) mixed reality capture from directly within your app.</span></span> <span data-ttu-id="e7978-247">深入瞭解 [適用于開發人員的混合現實開發](mixed-reality-capture-for-developers.md)。</span><span class="sxs-lookup"><span data-stu-id="e7978-247">Learn more at [mixed reality capture for developers](mixed-reality-capture-for-developers.md).</span></span>

## <a name="locating-the-device-camera-in-the-world"></a><span data-ttu-id="e7978-248">找出世界中的裝置攝影機</span><span class="sxs-lookup"><span data-stu-id="e7978-248">Locating the Device Camera in the World</span></span>

<span data-ttu-id="e7978-249">當 HoloLens 拍攝相片和影片時，所捕捉的框架會包含相機在世界的位置，以及相機的鏡頭模型。</span><span class="sxs-lookup"><span data-stu-id="e7978-249">When HoloLens takes photos and videos, the captured frames include the location of the camera in the world and the lens model of the camera.</span></span> <span data-ttu-id="e7978-250">這可讓應用程式在真實世界中的相機位置，以增強影像案例。</span><span class="sxs-lookup"><span data-stu-id="e7978-250">This allows applications to reason about the position of the camera in the real world for augmented imaging scenarios.</span></span> <span data-ttu-id="e7978-251">開發人員可以使用其最愛的影像處理或自訂電腦視覺程式庫，以創造性的來變換自己的案例。</span><span class="sxs-lookup"><span data-stu-id="e7978-251">Developers can creatively roll their own scenarios using their favorite image processing or custom computer vision libraries.</span></span>

<span data-ttu-id="e7978-252">HoloLens 檔中其他位置的「相機」可能參考「虛擬遊戲攝影機」 (應用程式轉譯為) 的錐。</span><span class="sxs-lookup"><span data-stu-id="e7978-252">"Camera" elsewhere in HoloLens documentation may refer to the "virtual game camera" (the frustum the app renders to).</span></span> <span data-ttu-id="e7978-253">除非另有指示，否則這個頁面上的「相機」是指真實的 RGB 色攝影機。</span><span class="sxs-lookup"><span data-stu-id="e7978-253">Unless denoted otherwise, "camera" on this page refers to the real-world RGB color camera.</span></span>

### <a name="using-unity"></a><span data-ttu-id="e7978-254">使用 Unity</span><span class="sxs-lookup"><span data-stu-id="e7978-254">Using Unity</span></span>

<span data-ttu-id="e7978-255">若要從「CameraIntrinsics」和「CameraCoordinateSystem」移至您的應用程式/全局座標系統，請依照 [Unity 文章中](../unity/locatable-camera-in-unity.md) 的可定位相機中的指示進行。</span><span class="sxs-lookup"><span data-stu-id="e7978-255">To go from the 'CameraIntrinsics' and 'CameraCoordinateSystem' to your application/world coordinate system, follow the instructions in the [Locatable camera in Unity](../unity/locatable-camera-in-unity.md) article.</span></span>  <span data-ttu-id="e7978-256">CameraToWorldMatrix 是由 PhotoCaptureFrame 類別自動提供，因此您不需要擔心下面討論的 CameraCoordinateSystem 轉換。</span><span class="sxs-lookup"><span data-stu-id="e7978-256">CameraToWorldMatrix is automatically provided by PhotoCaptureFrame class, and so you don't need to worry about the CameraCoordinateSystem transforms discussed below.</span></span>

### <a name="using-mediaframereference"></a><span data-ttu-id="e7978-257">使用 MediaFrameReference</span><span class="sxs-lookup"><span data-stu-id="e7978-257">Using MediaFrameReference</span></span>

<span data-ttu-id="e7978-258">如果 you'r 使用 [MediaFrameReference](https://docs.microsoft.com//uwp/api/windows.media.capture.frames.mediaframereference) 類別從相機讀取影像畫面格，則適用這些指示。</span><span class="sxs-lookup"><span data-stu-id="e7978-258">These instructions apply if you'r using the [MediaFrameReference](https://docs.microsoft.com//uwp/api/windows.media.capture.frames.mediaframereference) class to read image frames from the camera.</span></span>

<span data-ttu-id="e7978-259">每個影像框架都會 (相片或影片) 是否包含在拍攝時根目錄于相機的[SpatialCoordinateSystem](https://docs.microsoft.com//uwp/api/windows.perception.spatial.spatialcoordinatesystem) ，可使用[MediaFrameReference](https://docs.microsoft.com//uwp/api/Windows.Media.Capture.Frames.MediaFrameReference)的[CoordinateSystem](https://docs.microsoft.com//uwp/api/windows.media.capture.frames.mediaframereference.coordinatesystem#Windows_Media_Capture_Frames_MediaFrameReference_CoordinateSystem)屬性來存取。</span><span class="sxs-lookup"><span data-stu-id="e7978-259">Each image frame (whether photo or video) includes a [SpatialCoordinateSystem](https://docs.microsoft.com//uwp/api/windows.perception.spatial.spatialcoordinatesystem) rooted at the camera at the time of capture, which can be accessed using the [CoordinateSystem](https://docs.microsoft.com//uwp/api/windows.media.capture.frames.mediaframereference.coordinatesystem#Windows_Media_Capture_Frames_MediaFrameReference_CoordinateSystem) property of your [MediaFrameReference](https://docs.microsoft.com//uwp/api/Windows.Media.Capture.Frames.MediaFrameReference).</span></span> <span data-ttu-id="e7978-260">每個畫面格都包含相機鏡頭模型的描述，可在 [CameraIntrinsics](https://docs.microsoft.com//uwp/api/windows.media.capture.frames.videomediaframe.cameraintrinsics#Windows_Media_Capture_Frames_VideoMediaFrame_CameraIntrinsics) 屬性中找到。</span><span class="sxs-lookup"><span data-stu-id="e7978-260">Each frame contains a description of the camera lens model, which can be found in the [CameraIntrinsics](https://docs.microsoft.com//uwp/api/windows.media.capture.frames.videomediaframe.cameraintrinsics#Windows_Media_Capture_Frames_VideoMediaFrame_CameraIntrinsics) property.</span></span> <span data-ttu-id="e7978-261">這些轉換會一起定義3D 空間中每個圖元的光線，代表產生圖元的光子所採用的路徑。</span><span class="sxs-lookup"><span data-stu-id="e7978-261">Together, these transforms define for each pixel a ray in 3D space representing the path taken by the photons that produced the pixel.</span></span> <span data-ttu-id="e7978-262">這些光線可以與應用程式中的其他內容相關，方法是從框架的座標系統取得轉換到其他的座標系統 (例如從 [固定的參考框架](../../design/coordinate-systems.md#stationary-frame-of-reference)) 。</span><span class="sxs-lookup"><span data-stu-id="e7978-262">These rays can be related to other content in the app by obtaining the transform from the frame's coordinate system to some other coordinate system (e.g. from a [stationary frame of reference](../../design/coordinate-systems.md#stationary-frame-of-reference)).</span></span> 

<span data-ttu-id="e7978-263">每個影像框架都會提供下列各項：</span><span class="sxs-lookup"><span data-stu-id="e7978-263">Each image frame provides the following:</span></span>
* <span data-ttu-id="e7978-264">以 RGB/NV12/JPEG/etc 格式) 的圖元資料 (</span><span class="sxs-lookup"><span data-stu-id="e7978-264">Pixel Data (in RGB/NV12/JPEG/etc. format)</span></span>
* <span data-ttu-id="e7978-265">從 capture 的位置[SpatialCoordinateSystem](https://docs.microsoft.com//uwp/api/windows.perception.spatial.spatialcoordinatesystem)</span><span class="sxs-lookup"><span data-stu-id="e7978-265">A [SpatialCoordinateSystem](https://docs.microsoft.com//uwp/api/windows.perception.spatial.spatialcoordinatesystem) from the location of capture</span></span>
* <span data-ttu-id="e7978-266">包含相機鏡頭模式的 [CameraIntrinsics](https://docs.microsoft.com//uwp/api/windows.media.capture.frames.videomediaframe.cameraintrinsics#Windows_Media_Capture_Frames_VideoMediaFrame_CameraIntrinsics) 類別</span><span class="sxs-lookup"><span data-stu-id="e7978-266">A [CameraIntrinsics](https://docs.microsoft.com//uwp/api/windows.media.capture.frames.videomediaframe.cameraintrinsics#Windows_Media_Capture_Frames_VideoMediaFrame_CameraIntrinsics) class containing the lens mode of the camera</span></span>

<span data-ttu-id="e7978-267">[HolographicFaceTracking 範例會示範](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicFaceTracking)在相機座標系統和您自己的應用程式座標系統之間，查詢轉換的方式相當直接。</span><span class="sxs-lookup"><span data-stu-id="e7978-267">The [HolographicFaceTracking sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicFaceTracking) shows the fairly straightforward way to query for the transform between the camera's coordinate system and your own application coordinate systems.</span></span>

### <a name="using-media-foundation"></a><span data-ttu-id="e7978-268">使用媒體基礎</span><span class="sxs-lookup"><span data-stu-id="e7978-268">Using Media Foundation</span></span>

<span data-ttu-id="e7978-269">如果您直接使用媒體基礎從相機讀取影像畫面格，您可以使用每個畫面格的 [MFSampleExtension_CameraExtrinsics 屬性](https://docs.microsoft.com/windows/win32/medfound/mfsampleextension-cameraextrinsics) 和 [MFSampleExtension_PinholeCameraIntrinsics 屬性](https://docs.microsoft.com/windows/win32/medfound/mfsampleextension-pinholecameraintrinsics) 來找出相對於應用程式其他座標系統的相機畫面格，如下列範例程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="e7978-269">If you are using Media Foundation directly to read image frames from the camera, you can use each frame's [MFSampleExtension_CameraExtrinsics attribute](https://docs.microsoft.com/windows/win32/medfound/mfsampleextension-cameraextrinsics) and [MFSampleExtension_PinholeCameraIntrinsics attribute](https://docs.microsoft.com/windows/win32/medfound/mfsampleextension-pinholecameraintrinsics) to locate camera frames relative to your application's other coordinate systems, as shown in this sample code:</span></span>

```cpp
#include <winrt/windows.perception.spatial.preview.h>
#include <mfapi.h>
#include <mfidl.h>
 
using namespace winrt::Windows::Foundation;
using namespace winrt::Windows::Foundation::Numerics;
using namespace winrt::Windows::Perception;
using namespace winrt::Windows::Perception::Spatial;
using namespace winrt::Windows::Perception::Spatial::Preview;
 
class CameraFrameLocator
{
public:
    struct CameraFrameLocation
    {
        SpatialCoordinateSystem CoordinateSystem;
        float4x4 CameraViewToCoordinateSytemTransform;
        MFPinholeCameraIntrinsics Intrinsics;
    };
 
    std::optional<CameraFrameLocation> TryLocateCameraFrame(IMFSample* pSample)
    {
        MFCameraExtrinsics cameraExtrinsics;
        MFPinholeCameraIntrinsics cameraIntrinsics;
        UINT32 sizeCameraExtrinsics = 0;
        UINT32 sizeCameraIntrinsics = 0;
        UINT64 sampleTimeHns = 0;
 
        // query sample for calibration and validate
        if (FAILED(pSample->GetUINT64(MFSampleExtension_DeviceTimestamp, &sampleTimeHns)) ||
            FAILED(pSample->GetBlob(MFSampleExtension_CameraExtrinsics, (UINT8*)& cameraExtrinsics, sizeof(cameraExtrinsics), &sizeCameraExtrinsics)) ||
            FAILED(pSample->GetBlob(MFSampleExtension_PinholeCameraIntrinsics, (UINT8*)& cameraIntrinsics, sizeof(cameraIntrinsics), &sizeCameraIntrinsics)) ||
            (sizeCameraExtrinsics != sizeof(cameraExtrinsics)) ||
            (sizeCameraIntrinsics != sizeof(cameraIntrinsics)) ||
            (cameraExtrinsics.TransformCount == 0))
        {
            return std::nullopt;
        }
 
        // compute extrinsic transform
        const auto& calibratedTransform = cameraExtrinsics.CalibratedTransforms[0];
        const GUID& dynamicNodeId = calibratedTransform.CalibrationId;
        const float4x4 cameraToDynamicNode =
            make_float4x4_from_quaternion(quaternion{ calibratedTransform.Orientation.x, calibratedTransform.Orientation.y, calibratedTransform.Orientation.z, calibratedTransform.Orientation.w }) *
            make_float4x4_translation(calibratedTransform.Position.x, calibratedTransform.Position.y, calibratedTransform.Position.z);
 
        // update locator cache for dynamic node
        if (dynamicNodeId != m_currentDynamicNodeId || !m_locator)
        {
            m_locator = SpatialGraphInteropPreview::CreateLocatorForNode(dynamicNodeId);
            if (!m_locator)
            {
                return std::nullopt;
            }
 
            m_frameOfReference = m_locator.CreateAttachedFrameOfReferenceAtCurrentHeading();
            m_currentDynamicNodeId = dynamicNodeId;
        }
 
        // locate dynamic node
        auto timestamp = PerceptionTimestampHelper::FromSystemRelativeTargetTime(TimeSpan{ sampleTimeHns });
        auto coordinateSystem = m_frameOfReference.GetStationaryCoordinateSystemAtTimestamp(timestamp);
        auto location = m_locator.TryLocateAtTimestamp(timestamp, coordinateSystem);
        if (!location)
        {
            return std::nullopt;
        }
 
        const float4x4 dynamicNodeToCoordinateSystem = make_float4x4_from_quaternion(location.Orientation()) * make_float4x4_translation(location.Position());
 
        return CameraFrameLocation{ coordinateSystem, cameraToDynamicNode * dynamicNodeToCoordinateSystem, cameraIntrinsics };
    }

private:
    GUID m_currentDynamicNodeId{ GUID_NULL };
    SpatialLocator m_locator{ nullptr };
    SpatialLocatorAttachedFrameOfReference m_frameOfReference{ nullptr };
};
```

### <a name="distortion-error"></a><span data-ttu-id="e7978-270">扭曲錯誤</span><span class="sxs-lookup"><span data-stu-id="e7978-270">Distortion Error</span></span>

<span data-ttu-id="e7978-271">在 HoloLens 上，影片和靜止影像串流會在系統的影像處理管線中 undistorted，然後才會將框架提供給應用程式 (預覽資料流程包含) 的原始失真畫面。</span><span class="sxs-lookup"><span data-stu-id="e7978-271">On HoloLens, the video and still image streams are undistorted in the system's image-processing pipeline before the frames are made available to the application (the preview stream contains the original distorted frames).</span></span> <span data-ttu-id="e7978-272">由於只有 CameraIntrinsics 可供使用，因此應用程式必須假設圖像框架代表完美的 pinhole 攝影機。</span><span class="sxs-lookup"><span data-stu-id="e7978-272">Because only the CameraIntrinsics are made available, applications must assume image frames represent a perfect pinhole camera.</span></span>

<span data-ttu-id="e7978-273">在 HoloLens (第一代) ，在框架中繼資料中使用 CameraIntrinsics 時，映射處理器中的 undistortion 函式可能仍會保留最多10圖元的錯誤。</span><span class="sxs-lookup"><span data-stu-id="e7978-273">On HoloLens (first-generation), the undistortion function in the image processor may still leave an error of up to 10 pixels when using the CameraIntrinsics in the frame metadata.</span></span> <span data-ttu-id="e7978-274">在許多使用案例中，此錯誤並不重要，但如果您要將影像對齊真實的海報/標記，而您注意到 <的10圖元位移 (大約是 11 mm 的空間，代表2計量離開) ，則可能造成失真錯誤。</span><span class="sxs-lookup"><span data-stu-id="e7978-274">In many use cases, this error won't matter, but if you're aligning holograms to real world posters/markers, for example, and you notice a <10-px offset (roughly 11 mm for holograms positioned 2 meters away), this distortion error could be the cause.</span></span> 

## <a name="locatable-camera-usage-scenarios"></a><span data-ttu-id="e7978-275">的相機使用案例</span><span class="sxs-lookup"><span data-stu-id="e7978-275">Locatable Camera Usage Scenarios</span></span>

### <a name="show-a-photo-or-video-in-the-world-where-it-was-captured"></a><span data-ttu-id="e7978-276">顯示在世界中的拍攝相片或影片</span><span class="sxs-lookup"><span data-stu-id="e7978-276">Show a photo or video in the world where it was captured</span></span>

<span data-ttu-id="e7978-277">裝置相機框架隨附「相機到世界」轉換，可用來顯示裝置在拍攝影像時的確切位置。</span><span class="sxs-lookup"><span data-stu-id="e7978-277">The Device Camera frames come with a "Camera To World" transform, that can be used to show exactly where the device was when the image was taken.</span></span> <span data-ttu-id="e7978-278">例如，您可以將小型全像攝影圖示放置在此位置， (CameraToWorld MultiplyPoint (Vector3。零) # A3，甚至在相機面對的方向繪製一個小箭號 (CameraToWorld. MultiplyVector (Vector3. 轉寄) # A7。</span><span class="sxs-lookup"><span data-stu-id="e7978-278">For example, you could position a small holographic icon at this location (CameraToWorld.MultiplyPoint(Vector3.zero)) and even draw a little arrow in the direction that the camera was facing (CameraToWorld.MultiplyVector(Vector3.forward)).</span></span>

### <a name="tag--pattern--poster--object-tracking"></a><span data-ttu-id="e7978-279">標記/模式/海報/物件追蹤</span><span class="sxs-lookup"><span data-stu-id="e7978-279">Tag / Pattern / Poster / Object Tracking</span></span>

<span data-ttu-id="e7978-280">許多混合現實應用程式都使用可辨識的影像或視覺模式來建立空間中的可追蹤點。</span><span class="sxs-lookup"><span data-stu-id="e7978-280">Many mixed reality applications use a recognizable image or visual pattern to create a trackable point in space.</span></span> <span data-ttu-id="e7978-281">然後，這會用來呈現相對於該點的物件，或建立已知位置。</span><span class="sxs-lookup"><span data-stu-id="e7978-281">This is then used to render objects relative to that point or create a known location.</span></span> <span data-ttu-id="e7978-282">HoloLens 的一些用途包括尋找以 fiducials 標記的真實世界物件 (例如，具有 QR 代碼) 的電視監視器、將 fiducials 放在，以及以視覺化方式與非 HoloLens 裝置（例如已設定為透過 Wi-fi 與 HoloLens 通訊的平板電腦）配對。</span><span class="sxs-lookup"><span data-stu-id="e7978-282">Some uses for HoloLens include finding a real world object tagged with fiducials (e.g. a TV monitor with a QR code), placing holograms over fiducials, and visually pairing with non-HoloLens devices like tablets that have been set up to communicate with HoloLens via Wi-Fi.</span></span>

<span data-ttu-id="e7978-283">您需要一些東西來辨識視覺效果模式，並將物件放在應用程式世界空間中：</span><span class="sxs-lookup"><span data-stu-id="e7978-283">You'll need a few things to recognize a visual pattern and place an object in the applications world space:</span></span>
1. <span data-ttu-id="e7978-284">影像模式辨識工具組，例如 QR 代碼、AR 標記、臉部搜尋工具、圓形追蹤器、OCR 等等。</span><span class="sxs-lookup"><span data-stu-id="e7978-284">An image pattern recognition toolkit, such as QR code, AR tags, face finder, circle trackers, OCR etc.</span></span>
2. <span data-ttu-id="e7978-285">在執行時間收集影像畫面格，並將其傳遞至辨識層</span><span class="sxs-lookup"><span data-stu-id="e7978-285">Collect image frames at runtime, and pass them to the recognition layer</span></span>
3. <span data-ttu-id="e7978-286">將其影像位置 Unproject 回世界位置，或可能是世界光線。</span><span class="sxs-lookup"><span data-stu-id="e7978-286">Unproject their image locations back into world positions, or likely world rays.</span></span> 
4. <span data-ttu-id="e7978-287">將您的虛擬模型放在這些世界位置</span><span class="sxs-lookup"><span data-stu-id="e7978-287">Position your virtual models over these world locations</span></span>

<span data-ttu-id="e7978-288">一些重要的影像處理連結：</span><span class="sxs-lookup"><span data-stu-id="e7978-288">Some important image-processing links:</span></span>
* [<span data-ttu-id="e7978-289">OpenCV</span><span class="sxs-lookup"><span data-stu-id="e7978-289">OpenCV</span></span>](https://opencv.org/)
* [<span data-ttu-id="e7978-290">QR 標記</span><span class="sxs-lookup"><span data-stu-id="e7978-290">QR Tags</span></span>](https://en.wikipedia.org/wiki/QR_code)
* [<span data-ttu-id="e7978-291">FaceSDK</span><span class="sxs-lookup"><span data-stu-id="e7978-291">FaceSDK</span></span>](https://research.microsoft.com/projects/facesdk/)
* [<span data-ttu-id="e7978-292">Microsoft Translator</span><span class="sxs-lookup"><span data-stu-id="e7978-292">Microsoft Translator</span></span>](https://www.microsoft.com/translator/business)

<span data-ttu-id="e7978-293">保持互動式應用程式框架速率很重要，特別是在處理長時間執行的影像辨識演算法時。</span><span class="sxs-lookup"><span data-stu-id="e7978-293">Keeping an interactive application frame-rate is critical, especially when dealing with long-running image recognition algorithms.</span></span> <span data-ttu-id="e7978-294">基於這個理由，我們通常會使用下列模式：</span><span class="sxs-lookup"><span data-stu-id="e7978-294">For this reason, we commonly use the following pattern:</span></span>
1. <span data-ttu-id="e7978-295">主要執行緒：管理相機物件</span><span class="sxs-lookup"><span data-stu-id="e7978-295">Main Thread: manages the camera object</span></span>
2. <span data-ttu-id="e7978-296">主要執行緒：要求新的框架 (async) </span><span class="sxs-lookup"><span data-stu-id="e7978-296">Main Thread: requests new frames (async)</span></span>
3. <span data-ttu-id="e7978-297">主執行緒：傳遞新的框架至追蹤執行緒</span><span class="sxs-lookup"><span data-stu-id="e7978-297">Main Thread: pass new frames to tracking thread</span></span>
4. <span data-ttu-id="e7978-298">追蹤執行緒：進程映射以收集關鍵點</span><span class="sxs-lookup"><span data-stu-id="e7978-298">Tracking Thread: processes image to collect key points</span></span>
5. <span data-ttu-id="e7978-299">主要執行緒：移動虛擬模型以符合找到的重點</span><span class="sxs-lookup"><span data-stu-id="e7978-299">Main Thread: moves virtual model to match found key points</span></span>
6. <span data-ttu-id="e7978-300">主執行緒：重複步驟2</span><span class="sxs-lookup"><span data-stu-id="e7978-300">Main Thread: repeat from step 2</span></span>

<span data-ttu-id="e7978-301">某些影像標記系統只會提供單一圖元位置 (其他人會提供完整的轉換，在此情況下不需要此區段) ，這相當於可能的位置。</span><span class="sxs-lookup"><span data-stu-id="e7978-301">Some image marker systems only provide a single pixel location (others provide the full transform in which case this section won't be needed), which equates to a ray of possible locations.</span></span> <span data-ttu-id="e7978-302">若要取得單一3d 位置，我們可以利用多個光線，並依其近似交集找出最終結果。</span><span class="sxs-lookup"><span data-stu-id="e7978-302">To get to a single 3d location, we can then leverage multiple rays and find the final result by their approximate intersection.</span></span> <span data-ttu-id="e7978-303">若要這樣做，您需要執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="e7978-303">To do this, you'll need to:</span></span>
1. <span data-ttu-id="e7978-304">取得迴圈來收集多個相機影像</span><span class="sxs-lookup"><span data-stu-id="e7978-304">Get a loop going collecting multiple camera images</span></span>
2. <span data-ttu-id="e7978-305">尋找相關聯的功能點及其世界光線</span><span class="sxs-lookup"><span data-stu-id="e7978-305">Find the associated feature points, and their world rays</span></span>
3. <span data-ttu-id="e7978-306">當您有功能的字典，而且每個都有多個世界光線時，您可以使用下列程式碼來解決這些光線的交集：</span><span class="sxs-lookup"><span data-stu-id="e7978-306">When you have a dictionary of features, each with multiple world rays, you can use the following code to solve for the intersection of those rays:</span></span>

```
public static Vector3 ClosestPointBetweenRays(
   Vector3 point1, Vector3 normalizedDirection1,
   Vector3 point2, Vector3 normalizedDirection2) {
   float directionProjection = Vector3.Dot(normalizedDirection1, normalizedDirection2);
   if (directionProjection == 1) {
     return point1; // parallel lines
   }
   float projection1 = Vector3.Dot(point2 - point1, normalizedDirection1);
   float projection2 = Vector3.Dot(point2 - point1, normalizedDirection2);
   float distanceAlongLine1 = (projection1 - directionProjection * projection2) / (1 - directionProjection * directionProjection);
   float distanceAlongLine2 = (projection2 - directionProjection * projection1) / (directionProjection * directionProjection - 1);
   Vector3 pointOnLine1 = point1 + distanceAlongLine1 * normalizedDirection1;
   Vector3 pointOnLine2 = point2 + distanceAlongLine2 * normalizedDirection2;
   return Vector3.Lerp(pointOnLine2, pointOnLine1, 0.5f);
 }
```

<span data-ttu-id="e7978-307">如果有兩個或多個追蹤的標記位置，您可以將模型化的場景定位至符合使用者目前的案例。</span><span class="sxs-lookup"><span data-stu-id="e7978-307">Given two or more tracked tag locations, you can position a modeled scene to fit the user's current scenario.</span></span> <span data-ttu-id="e7978-308">如果您無法採用重力，則需要三個標記位置。</span><span class="sxs-lookup"><span data-stu-id="e7978-308">If you can't assume gravity, then you'll need three tag locations.</span></span> <span data-ttu-id="e7978-309">在許多情況下，我們會使用色彩配置，其中白色球體代表即時追蹤標記位置，而藍色球體表示模型化標記位置。</span><span class="sxs-lookup"><span data-stu-id="e7978-309">In many cases, we use a color scheme where white spheres represent real-time tracked tag locations, and blue spheres represent modeled tag locations.</span></span> <span data-ttu-id="e7978-310">這可讓使用者以視覺化方式測量對齊品質。</span><span class="sxs-lookup"><span data-stu-id="e7978-310">This allows the user to visually gauge the alignment quality.</span></span> <span data-ttu-id="e7978-311">我們假設所有的應用程式都有下列設定：</span><span class="sxs-lookup"><span data-stu-id="e7978-311">We assume the following setup in all our applications:</span></span>
* <span data-ttu-id="e7978-312">兩個或多個模型化標記位置</span><span class="sxs-lookup"><span data-stu-id="e7978-312">Two or more modeled tag locations</span></span>
* <span data-ttu-id="e7978-313">一個「校正空間」，在場景中是標記的父系</span><span class="sxs-lookup"><span data-stu-id="e7978-313">One 'calibration space', which in the scene is the parent of the tags</span></span>
* <span data-ttu-id="e7978-314">相機功能識別碼</span><span class="sxs-lookup"><span data-stu-id="e7978-314">Camera feature identifier</span></span>
* <span data-ttu-id="e7978-315">行為，這會移動校正空間來對齊模型標記與即時標籤 (我們很小心地移動上層空間，而不是模型標記本身，因為其他連接是相對於其) 的位置。</span><span class="sxs-lookup"><span data-stu-id="e7978-315">Behavior, which moves the calibration space to align the modeled tags with the real-time tags (we're careful to move the parent space, not the modeled markers themselves, because other connect is positions relative to them).</span></span>

```
// In the two tags case:
 Vector3 idealDelta = (realTags[1].EstimatedWorldPos - realTags[0].EstimatedWorldPos);
 Vector3 curDelta = (modelledTags[1].transform.position - modelledTags[0].transform.position);
 if (IsAssumeGravity) {
   idealDelta.y = 0;
   curDelta.y = 0;
 }
 Quaternion deltaRot = Quaternion.FromToRotation(curDelta, idealDelta);
 trans.rotation = Quaternion.LookRotation(deltaRot * trans.forward, trans.up);
 trans.position += realTags[0].EstimatedWorldPos - modelledTags[0].transform.position;
```

### <a name="track-or-identify-tagged-stationary-or-moving-real-world-objectsfaces-using-leds-or-other-recognizer-libraries"></a><span data-ttu-id="e7978-316">使用 Led 或其他辨識器程式庫追蹤或識別已標記的固定或移動真實世界的物件/臉部</span><span class="sxs-lookup"><span data-stu-id="e7978-316">Track or Identify Tagged Stationary or Moving real-world objects/faces using LEDs or other recognizer libraries</span></span>

<span data-ttu-id="e7978-317">範例：</span><span class="sxs-lookup"><span data-stu-id="e7978-317">Examples:</span></span>
* <span data-ttu-id="e7978-318">具有 Led (的產業機器人，或較慢移動物件的 QR 代碼) </span><span class="sxs-lookup"><span data-stu-id="e7978-318">Industrial robots with LEDs (or QR codes for slower moving objects)</span></span>
* <span data-ttu-id="e7978-319">識別和辨識房間中的物件</span><span class="sxs-lookup"><span data-stu-id="e7978-319">Identify and recognize objects in the room</span></span>
* <span data-ttu-id="e7978-320">識別和辨識房間中的人員，例如，將全像攝影的連絡人卡片放在臉部上</span><span class="sxs-lookup"><span data-stu-id="e7978-320">Identify and recognize people in the room, for example placing holographic contact cards over faces</span></span>

## <a name="see-also"></a><span data-ttu-id="e7978-321">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e7978-321">See also</span></span>
* [<span data-ttu-id="e7978-322">已定位相機範例</span><span class="sxs-lookup"><span data-stu-id="e7978-322">Locatable camera sample</span></span>](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicFaceTracking)
* [<span data-ttu-id="e7978-323">Unity 中的定位相機</span><span class="sxs-lookup"><span data-stu-id="e7978-323">Locatable camera in Unity</span></span>](../unity/locatable-camera-in-unity.md)
* [<span data-ttu-id="e7978-324">混合實境擷取</span><span class="sxs-lookup"><span data-stu-id="e7978-324">Mixed reality capture</span></span>](../../mixed-reality-capture.md)
* [<span data-ttu-id="e7978-325">適用於開發人員的混合實境擷取</span><span class="sxs-lookup"><span data-stu-id="e7978-325">Mixed reality capture for developers</span></span>](mixed-reality-capture-for-developers.md)
* [<span data-ttu-id="e7978-326">Media capture 簡介</span><span class="sxs-lookup"><span data-stu-id="e7978-326">Media capture introduction</span></span>](https://msdn.microsoft.com/library/windows/apps/mt243896.aspx)
* [<span data-ttu-id="e7978-327">全像臉部追蹤範例</span><span class="sxs-lookup"><span data-stu-id="e7978-327">Holographic face tracking sample</span></span>](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicFaceTracking)
