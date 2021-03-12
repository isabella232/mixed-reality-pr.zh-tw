---
title: InputAnimationFileFormat
description: MRTK 中輸入動畫二進位檔案格式規格的相關檔
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: adc6bee83faacf20a1b8013bafb1cf50e1e3d419
ms.sourcegitcommit: 210312f6be83745761eeb4f55827e1fc677d79ca
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/11/2021
ms.locfileid: "103147413"
---
# <a name="input-animation-binary-file-format-specification"></a><span data-ttu-id="fc9ef-104">輸入動畫二進位檔案格式規格</span><span class="sxs-lookup"><span data-stu-id="fc9ef-104">Input animation binary file format specification</span></span>

## <a name="overall-structure"></a><span data-ttu-id="fc9ef-105">整體結構</span><span class="sxs-lookup"><span data-stu-id="fc9ef-105">Overall structure</span></span>

<span data-ttu-id="fc9ef-106">輸入動畫二進位檔案的開頭為64位整數魔術數位。</span><span class="sxs-lookup"><span data-stu-id="fc9ef-106">The input animation binary file begins with a 64 bit integer magic number.</span></span> <span data-ttu-id="fc9ef-107">這個數位的十六進位標記法值是 `0x6a8faf6e0f9e42c6` ，而且可以用來識別有效的輸入動畫檔案。</span><span class="sxs-lookup"><span data-stu-id="fc9ef-107">The value of this number in hexadecimal notation is `0x6a8faf6e0f9e42c6` and can be used to identify valid input animation files.</span></span>

<span data-ttu-id="fc9ef-108">接下來八個位元組是兩個 Int32 值，用來宣告檔案的主要和次要版本號碼。</span><span class="sxs-lookup"><span data-stu-id="fc9ef-108">The next eight bytes are two Int32 values declaring the major and minor version number of the file.</span></span>

<span data-ttu-id="fc9ef-109">檔案的其餘部分是由動畫資料所佔用，可能會在版本號碼之間變更。</span><span class="sxs-lookup"><span data-stu-id="fc9ef-109">The rest of the file is taken up by animation data, which may change between version numbers.</span></span>

| <span data-ttu-id="fc9ef-110">區段</span><span class="sxs-lookup"><span data-stu-id="fc9ef-110">Section</span></span> | <span data-ttu-id="fc9ef-111">類型</span><span class="sxs-lookup"><span data-stu-id="fc9ef-111">Type</span></span> |
|---------|------|
| <span data-ttu-id="fc9ef-112">魔術數位</span><span class="sxs-lookup"><span data-stu-id="fc9ef-112">Magic Number</span></span> | <span data-ttu-id="fc9ef-113">Int64</span><span class="sxs-lookup"><span data-stu-id="fc9ef-113">Int64</span></span> |
| <span data-ttu-id="fc9ef-114">主要版本號碼</span><span class="sxs-lookup"><span data-stu-id="fc9ef-114">Major Version Number</span></span> | <span data-ttu-id="fc9ef-115">Int32</span><span class="sxs-lookup"><span data-stu-id="fc9ef-115">Int32</span></span> |
| <span data-ttu-id="fc9ef-116">次要版本號碼</span><span class="sxs-lookup"><span data-stu-id="fc9ef-116">Minor Version Number</span></span> | <span data-ttu-id="fc9ef-117">Int32</span><span class="sxs-lookup"><span data-stu-id="fc9ef-117">Int32</span></span> |
| <span data-ttu-id="fc9ef-118">動畫資料</span><span class="sxs-lookup"><span data-stu-id="fc9ef-118">Animation Data</span></span> | <span data-ttu-id="fc9ef-119">_請參閱版本區段_</span><span class="sxs-lookup"><span data-stu-id="fc9ef-119">_see version section_</span></span> |

## <a name="version-11"></a><span data-ttu-id="fc9ef-120">1.1 版</span><span class="sxs-lookup"><span data-stu-id="fc9ef-120">Version 1.1</span></span>

<span data-ttu-id="fc9ef-121">輸入動畫資料包含三個布林值，指出動畫是否包含相機、手和眼睛等資料，後面接著一連串的動畫曲線。</span><span class="sxs-lookup"><span data-stu-id="fc9ef-121">The input animation data consists of three boolean values that indicate whether the animation contains Camera, Hand, and Eye Gaze data, followed by a sequence of animation curves.</span></span> <span data-ttu-id="fc9ef-122">出現的曲線取決於這些布林值的值。</span><span class="sxs-lookup"><span data-stu-id="fc9ef-122">The curves present depends on the values of these booleans.</span></span> <span data-ttu-id="fc9ef-123">每個曲線都可以有不同的主要畫面格數目。</span><span class="sxs-lookup"><span data-stu-id="fc9ef-123">Each curve can have a different number of keyframes.</span></span>

| <span data-ttu-id="fc9ef-124">區段</span><span class="sxs-lookup"><span data-stu-id="fc9ef-124">Section</span></span> | <span data-ttu-id="fc9ef-125">類型</span><span class="sxs-lookup"><span data-stu-id="fc9ef-125">Type</span></span> | <span data-ttu-id="fc9ef-126">注意</span><span class="sxs-lookup"><span data-stu-id="fc9ef-126">Notes</span></span> |
|---------|------|------|
| <span data-ttu-id="fc9ef-127">有相機姿勢</span><span class="sxs-lookup"><span data-stu-id="fc9ef-127">Has Camera Pose</span></span> | <span data-ttu-id="fc9ef-128">Boolean</span><span class="sxs-lookup"><span data-stu-id="fc9ef-128">Boolean</span></span> | |
| <span data-ttu-id="fc9ef-129">有手資料</span><span class="sxs-lookup"><span data-stu-id="fc9ef-129">Has Hand Data</span></span> | <span data-ttu-id="fc9ef-130">Boolean</span><span class="sxs-lookup"><span data-stu-id="fc9ef-130">Boolean</span></span> | |
| <span data-ttu-id="fc9ef-131">具有眼睛</span><span class="sxs-lookup"><span data-stu-id="fc9ef-131">Has Eye Gaze</span></span>| <span data-ttu-id="fc9ef-132">Boolean</span><span class="sxs-lookup"><span data-stu-id="fc9ef-132">Boolean</span></span> | |
| <span data-ttu-id="fc9ef-133">相機</span><span class="sxs-lookup"><span data-stu-id="fc9ef-133">Camera</span></span> | [<span data-ttu-id="fc9ef-134">姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="fc9ef-134">Pose Curves</span></span>](#pose-curves) | <span data-ttu-id="fc9ef-135">只有當攝影機姿勢為 true 時</span><span class="sxs-lookup"><span data-stu-id="fc9ef-135">Only if Has Camera Pose is true</span></span> |
| <span data-ttu-id="fc9ef-136">靠右追蹤</span><span class="sxs-lookup"><span data-stu-id="fc9ef-136">Hand Tracked Left</span></span> | [<span data-ttu-id="fc9ef-137">布林曲線</span><span class="sxs-lookup"><span data-stu-id="fc9ef-137">Boolean Curve</span></span>](#boolean-curve) | <span data-ttu-id="fc9ef-138">只有在有手資料為 true 時</span><span class="sxs-lookup"><span data-stu-id="fc9ef-138">Only if Has Hand Data is true</span></span> |
| <span data-ttu-id="fc9ef-139">右側追蹤</span><span class="sxs-lookup"><span data-stu-id="fc9ef-139">Hand Tracked Right</span></span> | [<span data-ttu-id="fc9ef-140">布林曲線</span><span class="sxs-lookup"><span data-stu-id="fc9ef-140">Boolean Curve</span></span>](#boolean-curve) | <span data-ttu-id="fc9ef-141">只有在有手資料為 true 時</span><span class="sxs-lookup"><span data-stu-id="fc9ef-141">Only if Has Hand Data is true</span></span> |
| <span data-ttu-id="fc9ef-142">向左捏合手</span><span class="sxs-lookup"><span data-stu-id="fc9ef-142">Hand Pinching Left</span></span> | [<span data-ttu-id="fc9ef-143">布林曲線</span><span class="sxs-lookup"><span data-stu-id="fc9ef-143">Boolean Curve</span></span>](#boolean-curve) | <span data-ttu-id="fc9ef-144">只有在有手資料為 true 時</span><span class="sxs-lookup"><span data-stu-id="fc9ef-144">Only if Has Hand Data is true</span></span> |
| <span data-ttu-id="fc9ef-145">右手捏合 Right</span><span class="sxs-lookup"><span data-stu-id="fc9ef-145">Hand Pinching Right</span></span> | [<span data-ttu-id="fc9ef-146">布林曲線</span><span class="sxs-lookup"><span data-stu-id="fc9ef-146">Boolean Curve</span></span>](#boolean-curve) | <span data-ttu-id="fc9ef-147">只有在有手資料為 true 時</span><span class="sxs-lookup"><span data-stu-id="fc9ef-147">Only if Has Hand Data is true</span></span> |
| <span data-ttu-id="fc9ef-148">左邊的接點</span><span class="sxs-lookup"><span data-stu-id="fc9ef-148">Hand Joints Left</span></span> | [<span data-ttu-id="fc9ef-149">聯合姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="fc9ef-149">Joint Pose Curves</span></span>](#joint-pose-curves) | <span data-ttu-id="fc9ef-150">只有在有手資料為 true 時</span><span class="sxs-lookup"><span data-stu-id="fc9ef-150">Only if Has Hand Data is true</span></span> |
| <span data-ttu-id="fc9ef-151">右邊</span><span class="sxs-lookup"><span data-stu-id="fc9ef-151">Hand Joints Right</span></span> | [<span data-ttu-id="fc9ef-152">聯合姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="fc9ef-152">Joint Pose Curves</span></span>](#joint-pose-curves) | <span data-ttu-id="fc9ef-153">只有在有手資料為 true 時</span><span class="sxs-lookup"><span data-stu-id="fc9ef-153">Only if Has Hand Data is true</span></span> |
| <span data-ttu-id="fc9ef-154">眼睛</span><span class="sxs-lookup"><span data-stu-id="fc9ef-154">Eye Gaze</span></span> | <span data-ttu-id="fc9ef-155">[光線曲線](#ray-curves)]</span><span class="sxs-lookup"><span data-stu-id="fc9ef-155">[Ray Curves](#ray-curves)]</span></span> | <span data-ttu-id="fc9ef-156">只有當眼睛為 true 時</span><span class="sxs-lookup"><span data-stu-id="fc9ef-156">Only if Has Eye Gaze is true</span></span> |

## <a name="version-10"></a><span data-ttu-id="fc9ef-157">版本 1.0</span><span class="sxs-lookup"><span data-stu-id="fc9ef-157">Version 1.0</span></span>

<span data-ttu-id="fc9ef-158">輸入動畫資料包含一連串的動畫曲線。</span><span class="sxs-lookup"><span data-stu-id="fc9ef-158">The input animation data consists of a sequence of animation curves.</span></span> <span data-ttu-id="fc9ef-159">動畫曲線的數目和意義是固定的，但每個曲線都可以有不同的主要畫面格數目。</span><span class="sxs-lookup"><span data-stu-id="fc9ef-159">The number and meaning of animation curves is fixed, but each curve can have a different number of keyframes.</span></span>

| <span data-ttu-id="fc9ef-160">區段</span><span class="sxs-lookup"><span data-stu-id="fc9ef-160">Section</span></span> | <span data-ttu-id="fc9ef-161">類型</span><span class="sxs-lookup"><span data-stu-id="fc9ef-161">Type</span></span> |
|---------|------|
| <span data-ttu-id="fc9ef-162">相機</span><span class="sxs-lookup"><span data-stu-id="fc9ef-162">Camera</span></span> | [<span data-ttu-id="fc9ef-163">姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="fc9ef-163">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="fc9ef-164">靠右追蹤</span><span class="sxs-lookup"><span data-stu-id="fc9ef-164">Hand Tracked Left</span></span> | [<span data-ttu-id="fc9ef-165">布林曲線</span><span class="sxs-lookup"><span data-stu-id="fc9ef-165">Boolean Curve</span></span>](#boolean-curve) |
| <span data-ttu-id="fc9ef-166">右側追蹤</span><span class="sxs-lookup"><span data-stu-id="fc9ef-166">Hand Tracked Right</span></span> | [<span data-ttu-id="fc9ef-167">布林曲線</span><span class="sxs-lookup"><span data-stu-id="fc9ef-167">Boolean Curve</span></span>](#boolean-curve) |
| <span data-ttu-id="fc9ef-168">向左捏合手</span><span class="sxs-lookup"><span data-stu-id="fc9ef-168">Hand Pinching Left</span></span> | [<span data-ttu-id="fc9ef-169">布林曲線</span><span class="sxs-lookup"><span data-stu-id="fc9ef-169">Boolean Curve</span></span>](#boolean-curve) |
| <span data-ttu-id="fc9ef-170">右手捏合 Right</span><span class="sxs-lookup"><span data-stu-id="fc9ef-170">Hand Pinching Right</span></span> | [<span data-ttu-id="fc9ef-171">布林曲線</span><span class="sxs-lookup"><span data-stu-id="fc9ef-171">Boolean Curve</span></span>](#boolean-curve) |
| <span data-ttu-id="fc9ef-172">左邊的接點</span><span class="sxs-lookup"><span data-stu-id="fc9ef-172">Hand Joints Left</span></span> | [<span data-ttu-id="fc9ef-173">聯合姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="fc9ef-173">Joint Pose Curves</span></span>](#joint-pose-curves) |
| <span data-ttu-id="fc9ef-174">右邊</span><span class="sxs-lookup"><span data-stu-id="fc9ef-174">Hand Joints Right</span></span> | [<span data-ttu-id="fc9ef-175">聯合姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="fc9ef-175">Joint Pose Curves</span></span>](#joint-pose-curves) |

### <a name="joint-pose-curves"></a><span data-ttu-id="fc9ef-176">聯合姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="fc9ef-176">Joint pose curves</span></span>

<span data-ttu-id="fc9ef-177">每次都會儲存一連串的聯合動畫曲線。</span><span class="sxs-lookup"><span data-stu-id="fc9ef-177">For each hand a sequence of joint animation curves is stored.</span></span> <span data-ttu-id="fc9ef-178">接點的數目是固定的，而且會針對每個聯合儲存一組姿勢曲線。</span><span class="sxs-lookup"><span data-stu-id="fc9ef-178">The number of joints is fixed, and a set of pose curves is stored for each joint.</span></span>

| <span data-ttu-id="fc9ef-179">區段</span><span class="sxs-lookup"><span data-stu-id="fc9ef-179">Section</span></span> | <span data-ttu-id="fc9ef-180">類型</span><span class="sxs-lookup"><span data-stu-id="fc9ef-180">Type</span></span> |
|---------|------|
| <span data-ttu-id="fc9ef-181">無</span><span class="sxs-lookup"><span data-stu-id="fc9ef-181">None</span></span> | [<span data-ttu-id="fc9ef-182">姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="fc9ef-182">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="fc9ef-183">手腕</span><span class="sxs-lookup"><span data-stu-id="fc9ef-183">Wrist</span></span> | [<span data-ttu-id="fc9ef-184">姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="fc9ef-184">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="fc9ef-185">Palm</span><span class="sxs-lookup"><span data-stu-id="fc9ef-185">Palm</span></span> | [<span data-ttu-id="fc9ef-186">姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="fc9ef-186">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="fc9ef-187">ThumbMetacarpalJoint</span><span class="sxs-lookup"><span data-stu-id="fc9ef-187">ThumbMetacarpalJoint</span></span> | [<span data-ttu-id="fc9ef-188">姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="fc9ef-188">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="fc9ef-189">ThumbProximalJoint</span><span class="sxs-lookup"><span data-stu-id="fc9ef-189">ThumbProximalJoint</span></span> | [<span data-ttu-id="fc9ef-190">姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="fc9ef-190">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="fc9ef-191">ThumbDistalJoint</span><span class="sxs-lookup"><span data-stu-id="fc9ef-191">ThumbDistalJoint</span></span> | [<span data-ttu-id="fc9ef-192">姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="fc9ef-192">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="fc9ef-193">ThumbTip</span><span class="sxs-lookup"><span data-stu-id="fc9ef-193">ThumbTip</span></span> | [<span data-ttu-id="fc9ef-194">姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="fc9ef-194">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="fc9ef-195">IndexMetacarpal</span><span class="sxs-lookup"><span data-stu-id="fc9ef-195">IndexMetacarpal</span></span> | [<span data-ttu-id="fc9ef-196">姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="fc9ef-196">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="fc9ef-197">IndexKnuckle</span><span class="sxs-lookup"><span data-stu-id="fc9ef-197">IndexKnuckle</span></span> | [<span data-ttu-id="fc9ef-198">姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="fc9ef-198">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="fc9ef-199">IndexMiddleJoint</span><span class="sxs-lookup"><span data-stu-id="fc9ef-199">IndexMiddleJoint</span></span> | [<span data-ttu-id="fc9ef-200">姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="fc9ef-200">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="fc9ef-201">IndexDistalJoint</span><span class="sxs-lookup"><span data-stu-id="fc9ef-201">IndexDistalJoint</span></span> | [<span data-ttu-id="fc9ef-202">姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="fc9ef-202">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="fc9ef-203">IndexTip</span><span class="sxs-lookup"><span data-stu-id="fc9ef-203">IndexTip</span></span> | [<span data-ttu-id="fc9ef-204">姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="fc9ef-204">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="fc9ef-205">MiddleMetacarpal</span><span class="sxs-lookup"><span data-stu-id="fc9ef-205">MiddleMetacarpal</span></span> | [<span data-ttu-id="fc9ef-206">姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="fc9ef-206">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="fc9ef-207">MiddleKnuckle</span><span class="sxs-lookup"><span data-stu-id="fc9ef-207">MiddleKnuckle</span></span> | [<span data-ttu-id="fc9ef-208">姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="fc9ef-208">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="fc9ef-209">MiddleMiddleJoint</span><span class="sxs-lookup"><span data-stu-id="fc9ef-209">MiddleMiddleJoint</span></span> | [<span data-ttu-id="fc9ef-210">姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="fc9ef-210">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="fc9ef-211">MiddleDistalJoint</span><span class="sxs-lookup"><span data-stu-id="fc9ef-211">MiddleDistalJoint</span></span> | [<span data-ttu-id="fc9ef-212">姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="fc9ef-212">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="fc9ef-213">MiddleTip</span><span class="sxs-lookup"><span data-stu-id="fc9ef-213">MiddleTip</span></span> | [<span data-ttu-id="fc9ef-214">姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="fc9ef-214">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="fc9ef-215">RingMetacarpal</span><span class="sxs-lookup"><span data-stu-id="fc9ef-215">RingMetacarpal</span></span> | [<span data-ttu-id="fc9ef-216">姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="fc9ef-216">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="fc9ef-217">RingKnuckle</span><span class="sxs-lookup"><span data-stu-id="fc9ef-217">RingKnuckle</span></span> | [<span data-ttu-id="fc9ef-218">姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="fc9ef-218">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="fc9ef-219">RingMiddleJoint</span><span class="sxs-lookup"><span data-stu-id="fc9ef-219">RingMiddleJoint</span></span> | [<span data-ttu-id="fc9ef-220">姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="fc9ef-220">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="fc9ef-221">RingDistalJoint</span><span class="sxs-lookup"><span data-stu-id="fc9ef-221">RingDistalJoint</span></span> | [<span data-ttu-id="fc9ef-222">姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="fc9ef-222">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="fc9ef-223">RingTip</span><span class="sxs-lookup"><span data-stu-id="fc9ef-223">RingTip</span></span> | [<span data-ttu-id="fc9ef-224">姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="fc9ef-224">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="fc9ef-225">PinkyMetacarpal</span><span class="sxs-lookup"><span data-stu-id="fc9ef-225">PinkyMetacarpal</span></span> | [<span data-ttu-id="fc9ef-226">姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="fc9ef-226">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="fc9ef-227">PinkyKnuckle</span><span class="sxs-lookup"><span data-stu-id="fc9ef-227">PinkyKnuckle</span></span> | [<span data-ttu-id="fc9ef-228">姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="fc9ef-228">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="fc9ef-229">PinkyMiddleJoint</span><span class="sxs-lookup"><span data-stu-id="fc9ef-229">PinkyMiddleJoint</span></span> | [<span data-ttu-id="fc9ef-230">姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="fc9ef-230">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="fc9ef-231">PinkyDistalJoint</span><span class="sxs-lookup"><span data-stu-id="fc9ef-231">PinkyDistalJoint</span></span> | [<span data-ttu-id="fc9ef-232">姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="fc9ef-232">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="fc9ef-233">PinkyTip</span><span class="sxs-lookup"><span data-stu-id="fc9ef-233">PinkyTip</span></span> | [<span data-ttu-id="fc9ef-234">姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="fc9ef-234">Pose Curves</span></span>](#pose-curves) |

### <a name="pose-curves"></a><span data-ttu-id="fc9ef-235">姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="fc9ef-235">Pose curves</span></span>

<span data-ttu-id="fc9ef-236">姿勢曲線是位置向量的三個動畫曲線序列，後面接著4個旋轉四元數的動畫曲線。</span><span class="sxs-lookup"><span data-stu-id="fc9ef-236">Pose curves are a sequence of 3 animation curves for the position vector, followed by 4 animation curves for the rotation quaternion.</span></span>

| <span data-ttu-id="fc9ef-237">區段</span><span class="sxs-lookup"><span data-stu-id="fc9ef-237">Section</span></span> | <span data-ttu-id="fc9ef-238">類型</span><span class="sxs-lookup"><span data-stu-id="fc9ef-238">Type</span></span> |
|---------|------|
| <span data-ttu-id="fc9ef-239">位置 X</span><span class="sxs-lookup"><span data-stu-id="fc9ef-239">Position X</span></span> | [<span data-ttu-id="fc9ef-240">浮點數曲線</span><span class="sxs-lookup"><span data-stu-id="fc9ef-240">Float Curve</span></span>](#float-curve) |
| <span data-ttu-id="fc9ef-241">位置 Y</span><span class="sxs-lookup"><span data-stu-id="fc9ef-241">Position Y</span></span> | [<span data-ttu-id="fc9ef-242">浮點數曲線</span><span class="sxs-lookup"><span data-stu-id="fc9ef-242">Float Curve</span></span>](#float-curve) |
| <span data-ttu-id="fc9ef-243">位置 Z</span><span class="sxs-lookup"><span data-stu-id="fc9ef-243">Position Z</span></span> | [<span data-ttu-id="fc9ef-244">浮點數曲線</span><span class="sxs-lookup"><span data-stu-id="fc9ef-244">Float Curve</span></span>](#float-curve) |
| <span data-ttu-id="fc9ef-245">旋轉 X</span><span class="sxs-lookup"><span data-stu-id="fc9ef-245">Rotation X</span></span> | [<span data-ttu-id="fc9ef-246">浮點數曲線</span><span class="sxs-lookup"><span data-stu-id="fc9ef-246">Float Curve</span></span>](#float-curve) |
| <span data-ttu-id="fc9ef-247">旋轉 Y</span><span class="sxs-lookup"><span data-stu-id="fc9ef-247">Rotation Y</span></span> | [<span data-ttu-id="fc9ef-248">浮點數曲線</span><span class="sxs-lookup"><span data-stu-id="fc9ef-248">Float Curve</span></span>](#float-curve) |
| <span data-ttu-id="fc9ef-249">旋轉 Z</span><span class="sxs-lookup"><span data-stu-id="fc9ef-249">Rotation Z</span></span> | [<span data-ttu-id="fc9ef-250">浮點數曲線</span><span class="sxs-lookup"><span data-stu-id="fc9ef-250">Float Curve</span></span>](#float-curve) |
| <span data-ttu-id="fc9ef-251">旋轉 W</span><span class="sxs-lookup"><span data-stu-id="fc9ef-251">Rotation W</span></span> | [<span data-ttu-id="fc9ef-252">浮點數曲線</span><span class="sxs-lookup"><span data-stu-id="fc9ef-252">Float Curve</span></span>](#float-curve) |

### <a name="ray-curves"></a><span data-ttu-id="fc9ef-253">光線曲線</span><span class="sxs-lookup"><span data-stu-id="fc9ef-253">Ray curves</span></span>

<span data-ttu-id="fc9ef-254">光線曲線是原點向量的三個動畫曲線序列，後面接著三個方向向量的動畫曲線。</span><span class="sxs-lookup"><span data-stu-id="fc9ef-254">Ray curves are a sequence of 3 animation curves for the origin vector, followed by 3 animation curves for the direction vector.</span></span>

| <span data-ttu-id="fc9ef-255">區段</span><span class="sxs-lookup"><span data-stu-id="fc9ef-255">Section</span></span> | <span data-ttu-id="fc9ef-256">類型</span><span class="sxs-lookup"><span data-stu-id="fc9ef-256">Type</span></span> |
|---------|------|
| <span data-ttu-id="fc9ef-257">原始 X</span><span class="sxs-lookup"><span data-stu-id="fc9ef-257">Origin X</span></span> | [<span data-ttu-id="fc9ef-258">浮點數曲線</span><span class="sxs-lookup"><span data-stu-id="fc9ef-258">Float Curve</span></span>](#float-curve) |
| <span data-ttu-id="fc9ef-259">原點 Y</span><span class="sxs-lookup"><span data-stu-id="fc9ef-259">Origin Y</span></span> | [<span data-ttu-id="fc9ef-260">浮點數曲線</span><span class="sxs-lookup"><span data-stu-id="fc9ef-260">Float Curve</span></span>](#float-curve) |
| <span data-ttu-id="fc9ef-261">原點 Z</span><span class="sxs-lookup"><span data-stu-id="fc9ef-261">Origin Z</span></span> | [<span data-ttu-id="fc9ef-262">浮點數曲線</span><span class="sxs-lookup"><span data-stu-id="fc9ef-262">Float Curve</span></span>](#float-curve) |
| <span data-ttu-id="fc9ef-263">方向 X</span><span class="sxs-lookup"><span data-stu-id="fc9ef-263">Direction X</span></span> | [<span data-ttu-id="fc9ef-264">浮點數曲線</span><span class="sxs-lookup"><span data-stu-id="fc9ef-264">Float Curve</span></span>](#float-curve) |
| <span data-ttu-id="fc9ef-265">方向 Y</span><span class="sxs-lookup"><span data-stu-id="fc9ef-265">Direction Y</span></span> | [<span data-ttu-id="fc9ef-266">浮點數曲線</span><span class="sxs-lookup"><span data-stu-id="fc9ef-266">Float Curve</span></span>](#float-curve) |
| <span data-ttu-id="fc9ef-267">方向 Z</span><span class="sxs-lookup"><span data-stu-id="fc9ef-267">Direction Z</span></span> | [<span data-ttu-id="fc9ef-268">浮點數曲線</span><span class="sxs-lookup"><span data-stu-id="fc9ef-268">Float Curve</span></span>](#float-curve) |

### <a name="float-curve"></a><span data-ttu-id="fc9ef-269">浮點數曲線</span><span class="sxs-lookup"><span data-stu-id="fc9ef-269">Float curve</span></span>

<span data-ttu-id="fc9ef-270">浮點數曲線是具有不定數目之主要畫面格的完備貝茲曲線。</span><span class="sxs-lookup"><span data-stu-id="fc9ef-270">Floating point curves are fully fledged Bézier curves with a variable number of keyframes.</span></span> <span data-ttu-id="fc9ef-271">每個主要畫面格都會儲存時間和曲線值，以及每個主要畫面格左右側邊的正切和加權。</span><span class="sxs-lookup"><span data-stu-id="fc9ef-271">Each keyframe stores a time and a curve value, as well as tangents and weights on the left and right side of each keyframe.</span></span>

| <span data-ttu-id="fc9ef-272">區段</span><span class="sxs-lookup"><span data-stu-id="fc9ef-272">Section</span></span> | <span data-ttu-id="fc9ef-273">類型</span><span class="sxs-lookup"><span data-stu-id="fc9ef-273">Type</span></span> |
|---------|------|
| <span data-ttu-id="fc9ef-274">預先換行模式</span><span class="sxs-lookup"><span data-stu-id="fc9ef-274">Pre-Wrap Mode</span></span> | <span data-ttu-id="fc9ef-275">Int32、 [Wrap 模式](#wrap-mode)</span><span class="sxs-lookup"><span data-stu-id="fc9ef-275">Int32, [Wrap Mode](#wrap-mode)</span></span> |
| <span data-ttu-id="fc9ef-276">後置換行模式</span><span class="sxs-lookup"><span data-stu-id="fc9ef-276">Post-Wrap Mode</span></span> | <span data-ttu-id="fc9ef-277">Int32、 [Wrap 模式](#wrap-mode)</span><span class="sxs-lookup"><span data-stu-id="fc9ef-277">Int32, [Wrap Mode](#wrap-mode)</span></span> |
| <span data-ttu-id="fc9ef-278">關鍵畫面數</span><span class="sxs-lookup"><span data-stu-id="fc9ef-278">Number of keyframes</span></span> | <span data-ttu-id="fc9ef-279">Int32</span><span class="sxs-lookup"><span data-stu-id="fc9ef-279">Int32</span></span> |
| <span data-ttu-id="fc9ef-280">關鍵 幀</span><span class="sxs-lookup"><span data-stu-id="fc9ef-280">Keyframes</span></span> | [<span data-ttu-id="fc9ef-281">Float 主要畫面格</span><span class="sxs-lookup"><span data-stu-id="fc9ef-281">Float Keyframe</span></span>](#float-keyframe) |

### <a name="float-keyframe"></a><span data-ttu-id="fc9ef-282">Float 主要畫面格</span><span class="sxs-lookup"><span data-stu-id="fc9ef-282">Float keyframe</span></span>

<span data-ttu-id="fc9ef-283">Float 主要畫面格會在基本時間和值的旁邊儲存正切值和加權值。</span><span class="sxs-lookup"><span data-stu-id="fc9ef-283">A float keyframe stores tangent and weight values alongside the basic time and value.</span></span>

| <span data-ttu-id="fc9ef-284">區段</span><span class="sxs-lookup"><span data-stu-id="fc9ef-284">Section</span></span> | <span data-ttu-id="fc9ef-285">類型</span><span class="sxs-lookup"><span data-stu-id="fc9ef-285">Type</span></span> |
|---------|------|
| <span data-ttu-id="fc9ef-286">Time</span><span class="sxs-lookup"><span data-stu-id="fc9ef-286">Time</span></span> | <span data-ttu-id="fc9ef-287">Float32</span><span class="sxs-lookup"><span data-stu-id="fc9ef-287">Float32</span></span> |
| <span data-ttu-id="fc9ef-288">值</span><span class="sxs-lookup"><span data-stu-id="fc9ef-288">Value</span></span> | <span data-ttu-id="fc9ef-289">Float32</span><span class="sxs-lookup"><span data-stu-id="fc9ef-289">Float32</span></span> |
| <span data-ttu-id="fc9ef-290">InTangent</span><span class="sxs-lookup"><span data-stu-id="fc9ef-290">InTangent</span></span> | <span data-ttu-id="fc9ef-291">Float32</span><span class="sxs-lookup"><span data-stu-id="fc9ef-291">Float32</span></span> |
| <span data-ttu-id="fc9ef-292">OutTangent</span><span class="sxs-lookup"><span data-stu-id="fc9ef-292">OutTangent</span></span> | <span data-ttu-id="fc9ef-293">Float32</span><span class="sxs-lookup"><span data-stu-id="fc9ef-293">Float32</span></span> |
| <span data-ttu-id="fc9ef-294">InWeight</span><span class="sxs-lookup"><span data-stu-id="fc9ef-294">InWeight</span></span> | <span data-ttu-id="fc9ef-295">Float32</span><span class="sxs-lookup"><span data-stu-id="fc9ef-295">Float32</span></span> |
| <span data-ttu-id="fc9ef-296">OutWeight</span><span class="sxs-lookup"><span data-stu-id="fc9ef-296">OutWeight</span></span> | <span data-ttu-id="fc9ef-297">Float32</span><span class="sxs-lookup"><span data-stu-id="fc9ef-297">Float32</span></span> |
| <span data-ttu-id="fc9ef-298">WeightedMode</span><span class="sxs-lookup"><span data-stu-id="fc9ef-298">WeightedMode</span></span> | <span data-ttu-id="fc9ef-299">Int32、 [加權模式](#weighted-mode)</span><span class="sxs-lookup"><span data-stu-id="fc9ef-299">Int32, [Weighted Mode](#weighted-mode)</span></span> |

### <a name="boolean-curve"></a><span data-ttu-id="fc9ef-300">布林曲線</span><span class="sxs-lookup"><span data-stu-id="fc9ef-300">Boolean curve</span></span>

<span data-ttu-id="fc9ef-301">布林曲線是開啟/關閉值的簡單序列。</span><span class="sxs-lookup"><span data-stu-id="fc9ef-301">Boolean curves are simple sequences of on/off values.</span></span> <span data-ttu-id="fc9ef-302">在每個主要畫面上，曲線的值會立即翻轉。</span><span class="sxs-lookup"><span data-stu-id="fc9ef-302">On every keyframe the value of the curve flips immediately.</span></span>

| <span data-ttu-id="fc9ef-303">區段</span><span class="sxs-lookup"><span data-stu-id="fc9ef-303">Section</span></span> | <span data-ttu-id="fc9ef-304">類型</span><span class="sxs-lookup"><span data-stu-id="fc9ef-304">Type</span></span> |
|---------|------|
| <span data-ttu-id="fc9ef-305">預先換行模式</span><span class="sxs-lookup"><span data-stu-id="fc9ef-305">Pre-Wrap Mode</span></span> | <span data-ttu-id="fc9ef-306">Int32、 [Wrap 模式](#wrap-mode)</span><span class="sxs-lookup"><span data-stu-id="fc9ef-306">Int32, [Wrap Mode](#wrap-mode)</span></span> |
| <span data-ttu-id="fc9ef-307">後置換行模式</span><span class="sxs-lookup"><span data-stu-id="fc9ef-307">Post-Wrap Mode</span></span> | <span data-ttu-id="fc9ef-308">Int32、 [Wrap 模式](#wrap-mode)</span><span class="sxs-lookup"><span data-stu-id="fc9ef-308">Int32, [Wrap Mode](#wrap-mode)</span></span> |
| <span data-ttu-id="fc9ef-309">關鍵畫面數</span><span class="sxs-lookup"><span data-stu-id="fc9ef-309">Number of keyframes</span></span> | <span data-ttu-id="fc9ef-310">Int32</span><span class="sxs-lookup"><span data-stu-id="fc9ef-310">Int32</span></span> |
| <span data-ttu-id="fc9ef-311">關鍵 幀</span><span class="sxs-lookup"><span data-stu-id="fc9ef-311">Keyframes</span></span> | [<span data-ttu-id="fc9ef-312">布林主要畫面格</span><span class="sxs-lookup"><span data-stu-id="fc9ef-312">Boolean Keyframe</span></span>](#boolean-keyframe) |

### <a name="boolean-keyframe"></a><span data-ttu-id="fc9ef-313">布林主要畫面格</span><span class="sxs-lookup"><span data-stu-id="fc9ef-313">Boolean keyframe</span></span>

<span data-ttu-id="fc9ef-314">布林值主要畫面格只會儲存時間和值。</span><span class="sxs-lookup"><span data-stu-id="fc9ef-314">A boolean keyframe only stores a time and value.</span></span>

| <span data-ttu-id="fc9ef-315">區段</span><span class="sxs-lookup"><span data-stu-id="fc9ef-315">Section</span></span> | <span data-ttu-id="fc9ef-316">類型</span><span class="sxs-lookup"><span data-stu-id="fc9ef-316">Type</span></span> |
|---------|------|
| <span data-ttu-id="fc9ef-317">Time</span><span class="sxs-lookup"><span data-stu-id="fc9ef-317">Time</span></span> | <span data-ttu-id="fc9ef-318">Float32</span><span class="sxs-lookup"><span data-stu-id="fc9ef-318">Float32</span></span> |
| <span data-ttu-id="fc9ef-319">值</span><span class="sxs-lookup"><span data-stu-id="fc9ef-319">Value</span></span> | <span data-ttu-id="fc9ef-320">Float32</span><span class="sxs-lookup"><span data-stu-id="fc9ef-320">Float32</span></span> |

### <a name="wrap-mode"></a><span data-ttu-id="fc9ef-321">Wrap 模式</span><span class="sxs-lookup"><span data-stu-id="fc9ef-321">Wrap mode</span></span>

<span data-ttu-id="fc9ef-322">前置和後置換行模式的語法遵循 [Unity WrapMode](https://docs.unity3d.com/ScriptReference/WrapMode.html) 定義。</span><span class="sxs-lookup"><span data-stu-id="fc9ef-322">The semantics of Pre- and Post-Wrap modes follow the [Unity WrapMode](https://docs.unity3d.com/ScriptReference/WrapMode.html) definition.</span></span> <span data-ttu-id="fc9ef-323">它們是下列位的組合：</span><span class="sxs-lookup"><span data-stu-id="fc9ef-323">They are a combination of the following bits:</span></span>

| <span data-ttu-id="fc9ef-324">值</span><span class="sxs-lookup"><span data-stu-id="fc9ef-324">Value</span></span> | <span data-ttu-id="fc9ef-325">意義</span><span class="sxs-lookup"><span data-stu-id="fc9ef-325">Meaning</span></span> |
|-------|---------|
| <span data-ttu-id="fc9ef-326">0</span><span class="sxs-lookup"><span data-stu-id="fc9ef-326">0</span></span> | <span data-ttu-id="fc9ef-327">預設值：讀取設定為較高的預設重複模式。</span><span class="sxs-lookup"><span data-stu-id="fc9ef-327">Default: Reads the default repeat mode set higher up.</span></span> |
| <span data-ttu-id="fc9ef-328">1</span><span class="sxs-lookup"><span data-stu-id="fc9ef-328">1</span></span> | <span data-ttu-id="fc9ef-329">一次：當時間到達動畫剪輯的結尾時，剪輯將會自動停止播放，而時間將會重設為剪輯的開頭。</span><span class="sxs-lookup"><span data-stu-id="fc9ef-329">Once: When time reaches the end of the animation clip, the clip will automatically stop playing and time will be reset to beginning of the clip.</span></span> |
| <span data-ttu-id="fc9ef-330">2</span><span class="sxs-lookup"><span data-stu-id="fc9ef-330">2</span></span> | <span data-ttu-id="fc9ef-331">Loop：當時間達到動畫剪輯的結尾時，時間會在一開始就繼續進行。</span><span class="sxs-lookup"><span data-stu-id="fc9ef-331">Loop: When time reaches the end of the animation clip, time will continue at the beginning.</span></span> |
| <span data-ttu-id="fc9ef-332">4</span><span class="sxs-lookup"><span data-stu-id="fc9ef-332">4</span></span> | <span data-ttu-id="fc9ef-333">PingPong：當時間達到動畫剪輯的結尾時，時間會在開始與結束時 ping 一次。</span><span class="sxs-lookup"><span data-stu-id="fc9ef-333">PingPong: When time reaches the end of the animation clip, time will ping pong back between beginning and end.</span></span> |
| <span data-ttu-id="fc9ef-334">8</span><span class="sxs-lookup"><span data-stu-id="fc9ef-334">8</span></span> | <span data-ttu-id="fc9ef-335">ClampForever：播放動畫。</span><span class="sxs-lookup"><span data-stu-id="fc9ef-335">ClampForever: Plays back the animation.</span></span> <span data-ttu-id="fc9ef-336">到達結束時，它會繼續播放最後一個畫面格，而且永遠不會停止播放。</span><span class="sxs-lookup"><span data-stu-id="fc9ef-336">When it reaches the end, it will keep playing the last frame and never stop playing.</span></span> |

### <a name="weighted-mode"></a><span data-ttu-id="fc9ef-337">加權模式</span><span class="sxs-lookup"><span data-stu-id="fc9ef-337">Weighted mode</span></span>

<span data-ttu-id="fc9ef-338">加權模式的語義遵循 [Unity WeightedMode](https://docs.unity3d.com/ScriptReference/WeightedMode.html) 定義。</span><span class="sxs-lookup"><span data-stu-id="fc9ef-338">The semantics of the Weighted mode follow the [Unity WeightedMode](https://docs.unity3d.com/ScriptReference/WeightedMode.html) definition.</span></span>

| <span data-ttu-id="fc9ef-339">值</span><span class="sxs-lookup"><span data-stu-id="fc9ef-339">Value</span></span> | <span data-ttu-id="fc9ef-340">意義</span><span class="sxs-lookup"><span data-stu-id="fc9ef-340">Meaning</span></span> |
|-------|---------|
| <span data-ttu-id="fc9ef-341">0</span><span class="sxs-lookup"><span data-stu-id="fc9ef-341">0</span></span> | <span data-ttu-id="fc9ef-342">None：在計算曲線區段時排除 inWeight 或 outWeight。</span><span class="sxs-lookup"><span data-stu-id="fc9ef-342">None: Exclude both inWeight or outWeight when calculating curve segments.</span></span> |
| <span data-ttu-id="fc9ef-343">1</span><span class="sxs-lookup"><span data-stu-id="fc9ef-343">1</span></span> | <span data-ttu-id="fc9ef-344">在中：在計算上一個曲線區段時包含 inWeight。</span><span class="sxs-lookup"><span data-stu-id="fc9ef-344">In: Include inWeight when calculating the previous curve segment.</span></span> |
| <span data-ttu-id="fc9ef-345">2</span><span class="sxs-lookup"><span data-stu-id="fc9ef-345">2</span></span> | <span data-ttu-id="fc9ef-346">Out：在計算下一個曲線區段時包含 outWeight。</span><span class="sxs-lookup"><span data-stu-id="fc9ef-346">Out: Include outWeight when calculating the next curve segment.</span></span> |
| <span data-ttu-id="fc9ef-347">3</span><span class="sxs-lookup"><span data-stu-id="fc9ef-347">3</span></span> | <span data-ttu-id="fc9ef-348">兩者：在計算曲線區段時包含 inWeight 和 outWeight。</span><span class="sxs-lookup"><span data-stu-id="fc9ef-348">Both: Include inWeight and outWeight when calculating curve segments.</span></span> |
