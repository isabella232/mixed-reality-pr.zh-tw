---
title: 輸入動畫檔案格式
description: MRTK 中輸入動畫二進位檔案格式規格的相關檔
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: ba232818c0a49d803ca6fae0b5adbc64e6deefa8
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145126"
---
# <a name="input-animation-binary-file-format-specification"></a><span data-ttu-id="05490-104">輸入動畫二進位檔案格式規格</span><span class="sxs-lookup"><span data-stu-id="05490-104">Input animation binary file format specification</span></span>

## <a name="overall-structure"></a><span data-ttu-id="05490-105">整體結構</span><span class="sxs-lookup"><span data-stu-id="05490-105">Overall structure</span></span>

<span data-ttu-id="05490-106">輸入動畫二進位檔案的開頭為64位整數魔術數位。</span><span class="sxs-lookup"><span data-stu-id="05490-106">The input animation binary file begins with a 64 bit integer magic number.</span></span> <span data-ttu-id="05490-107">這個數位的十六進位標記法值是 `0x6a8faf6e0f9e42c6` ，而且可以用來識別有效的輸入動畫檔案。</span><span class="sxs-lookup"><span data-stu-id="05490-107">The value of this number in hexadecimal notation is `0x6a8faf6e0f9e42c6` and can be used to identify valid input animation files.</span></span>

<span data-ttu-id="05490-108">接下來八個位元組是兩個 Int32 值，用來宣告檔案的主要和次要版本號碼。</span><span class="sxs-lookup"><span data-stu-id="05490-108">The next eight bytes are two Int32 values declaring the major and minor version number of the file.</span></span>

<span data-ttu-id="05490-109">檔案的其餘部分是由動畫資料所佔用，可能會在版本號碼之間變更。</span><span class="sxs-lookup"><span data-stu-id="05490-109">The rest of the file is taken up by animation data, which may change between version numbers.</span></span>

| <span data-ttu-id="05490-110">區段</span><span class="sxs-lookup"><span data-stu-id="05490-110">Section</span></span> | <span data-ttu-id="05490-111">類型</span><span class="sxs-lookup"><span data-stu-id="05490-111">Type</span></span> |
|---------|------|
| <span data-ttu-id="05490-112">魔術數位</span><span class="sxs-lookup"><span data-stu-id="05490-112">Magic Number</span></span> | <span data-ttu-id="05490-113">Int64</span><span class="sxs-lookup"><span data-stu-id="05490-113">Int64</span></span> |
| <span data-ttu-id="05490-114">主要版本號碼</span><span class="sxs-lookup"><span data-stu-id="05490-114">Major Version Number</span></span> | <span data-ttu-id="05490-115">Int32</span><span class="sxs-lookup"><span data-stu-id="05490-115">Int32</span></span> |
| <span data-ttu-id="05490-116">次要版本號碼</span><span class="sxs-lookup"><span data-stu-id="05490-116">Minor Version Number</span></span> | <span data-ttu-id="05490-117">Int32</span><span class="sxs-lookup"><span data-stu-id="05490-117">Int32</span></span> |
| <span data-ttu-id="05490-118">動畫資料</span><span class="sxs-lookup"><span data-stu-id="05490-118">Animation Data</span></span> | <span data-ttu-id="05490-119">_請參閱版本區段_</span><span class="sxs-lookup"><span data-stu-id="05490-119">_see version section_</span></span> |

## <a name="version-11"></a><span data-ttu-id="05490-120">1.1 版</span><span class="sxs-lookup"><span data-stu-id="05490-120">Version 1.1</span></span>

<span data-ttu-id="05490-121">輸入動畫資料包含三個布林值，指出動畫是否包含相機、手和眼睛等資料，後面接著一連串的動畫曲線。</span><span class="sxs-lookup"><span data-stu-id="05490-121">The input animation data consists of three boolean values that indicate whether the animation contains Camera, Hand, and Eye Gaze data, followed by a sequence of animation curves.</span></span> <span data-ttu-id="05490-122">出現的曲線取決於這些布林值的值。</span><span class="sxs-lookup"><span data-stu-id="05490-122">The curves present depends on the values of these booleans.</span></span> <span data-ttu-id="05490-123">每個曲線都可以有不同的主要畫面格數目。</span><span class="sxs-lookup"><span data-stu-id="05490-123">Each curve can have a different number of keyframes.</span></span>

| <span data-ttu-id="05490-124">區段</span><span class="sxs-lookup"><span data-stu-id="05490-124">Section</span></span> | <span data-ttu-id="05490-125">類型</span><span class="sxs-lookup"><span data-stu-id="05490-125">Type</span></span> | <span data-ttu-id="05490-126">注意</span><span class="sxs-lookup"><span data-stu-id="05490-126">Notes</span></span> |
|---------|------|------|
| <span data-ttu-id="05490-127">有相機姿勢</span><span class="sxs-lookup"><span data-stu-id="05490-127">Has Camera Pose</span></span> | <span data-ttu-id="05490-128">布林值</span><span class="sxs-lookup"><span data-stu-id="05490-128">Boolean</span></span> | |
| <span data-ttu-id="05490-129">有手資料</span><span class="sxs-lookup"><span data-stu-id="05490-129">Has Hand Data</span></span> | <span data-ttu-id="05490-130">布林值</span><span class="sxs-lookup"><span data-stu-id="05490-130">Boolean</span></span> | |
| <span data-ttu-id="05490-131">具有眼睛</span><span class="sxs-lookup"><span data-stu-id="05490-131">Has Eye Gaze</span></span>| <span data-ttu-id="05490-132">布林值</span><span class="sxs-lookup"><span data-stu-id="05490-132">Boolean</span></span> | |
| <span data-ttu-id="05490-133">相機</span><span class="sxs-lookup"><span data-stu-id="05490-133">Camera</span></span> | [<span data-ttu-id="05490-134">姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="05490-134">Pose Curves</span></span>](#pose-curves) | <span data-ttu-id="05490-135">只有當攝影機姿勢為 true 時</span><span class="sxs-lookup"><span data-stu-id="05490-135">Only if Has Camera Pose is true</span></span> |
| <span data-ttu-id="05490-136">靠右追蹤</span><span class="sxs-lookup"><span data-stu-id="05490-136">Hand Tracked Left</span></span> | [<span data-ttu-id="05490-137">布林曲線</span><span class="sxs-lookup"><span data-stu-id="05490-137">Boolean Curve</span></span>](#boolean-curve) | <span data-ttu-id="05490-138">只有在有手資料為 true 時</span><span class="sxs-lookup"><span data-stu-id="05490-138">Only if Has Hand Data is true</span></span> |
| <span data-ttu-id="05490-139">右側追蹤</span><span class="sxs-lookup"><span data-stu-id="05490-139">Hand Tracked Right</span></span> | [<span data-ttu-id="05490-140">布林曲線</span><span class="sxs-lookup"><span data-stu-id="05490-140">Boolean Curve</span></span>](#boolean-curve) | <span data-ttu-id="05490-141">只有在有手資料為 true 時</span><span class="sxs-lookup"><span data-stu-id="05490-141">Only if Has Hand Data is true</span></span> |
| <span data-ttu-id="05490-142">向左捏合手</span><span class="sxs-lookup"><span data-stu-id="05490-142">Hand Pinching Left</span></span> | [<span data-ttu-id="05490-143">布林曲線</span><span class="sxs-lookup"><span data-stu-id="05490-143">Boolean Curve</span></span>](#boolean-curve) | <span data-ttu-id="05490-144">只有在有手資料為 true 時</span><span class="sxs-lookup"><span data-stu-id="05490-144">Only if Has Hand Data is true</span></span> |
| <span data-ttu-id="05490-145">右手捏合 Right</span><span class="sxs-lookup"><span data-stu-id="05490-145">Hand Pinching Right</span></span> | [<span data-ttu-id="05490-146">布林曲線</span><span class="sxs-lookup"><span data-stu-id="05490-146">Boolean Curve</span></span>](#boolean-curve) | <span data-ttu-id="05490-147">只有在有手資料為 true 時</span><span class="sxs-lookup"><span data-stu-id="05490-147">Only if Has Hand Data is true</span></span> |
| <span data-ttu-id="05490-148">左邊的接點</span><span class="sxs-lookup"><span data-stu-id="05490-148">Hand Joints Left</span></span> | [<span data-ttu-id="05490-149">聯合姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="05490-149">Joint Pose Curves</span></span>](#joint-pose-curves) | <span data-ttu-id="05490-150">只有在有手資料為 true 時</span><span class="sxs-lookup"><span data-stu-id="05490-150">Only if Has Hand Data is true</span></span> |
| <span data-ttu-id="05490-151">右邊</span><span class="sxs-lookup"><span data-stu-id="05490-151">Hand Joints Right</span></span> | [<span data-ttu-id="05490-152">聯合姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="05490-152">Joint Pose Curves</span></span>](#joint-pose-curves) | <span data-ttu-id="05490-153">只有在有手資料為 true 時</span><span class="sxs-lookup"><span data-stu-id="05490-153">Only if Has Hand Data is true</span></span> |
| <span data-ttu-id="05490-154">眼睛</span><span class="sxs-lookup"><span data-stu-id="05490-154">Eye Gaze</span></span> | <span data-ttu-id="05490-155">[光線曲線](#ray-curves)]</span><span class="sxs-lookup"><span data-stu-id="05490-155">[Ray Curves](#ray-curves)]</span></span> | <span data-ttu-id="05490-156">只有當眼睛為 true 時</span><span class="sxs-lookup"><span data-stu-id="05490-156">Only if Has Eye Gaze is true</span></span> |

## <a name="version-10"></a><span data-ttu-id="05490-157">版本 1.0</span><span class="sxs-lookup"><span data-stu-id="05490-157">Version 1.0</span></span>

<span data-ttu-id="05490-158">輸入動畫資料包含一連串的動畫曲線。</span><span class="sxs-lookup"><span data-stu-id="05490-158">The input animation data consists of a sequence of animation curves.</span></span> <span data-ttu-id="05490-159">動畫曲線的數目和意義是固定的，但每個曲線都可以有不同的主要畫面格數目。</span><span class="sxs-lookup"><span data-stu-id="05490-159">The number and meaning of animation curves is fixed, but each curve can have a different number of keyframes.</span></span>

| <span data-ttu-id="05490-160">區段</span><span class="sxs-lookup"><span data-stu-id="05490-160">Section</span></span> | <span data-ttu-id="05490-161">類型</span><span class="sxs-lookup"><span data-stu-id="05490-161">Type</span></span> |
|---------|------|
| <span data-ttu-id="05490-162">相機</span><span class="sxs-lookup"><span data-stu-id="05490-162">Camera</span></span> | [<span data-ttu-id="05490-163">姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="05490-163">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="05490-164">靠右追蹤</span><span class="sxs-lookup"><span data-stu-id="05490-164">Hand Tracked Left</span></span> | [<span data-ttu-id="05490-165">布林曲線</span><span class="sxs-lookup"><span data-stu-id="05490-165">Boolean Curve</span></span>](#boolean-curve) |
| <span data-ttu-id="05490-166">右側追蹤</span><span class="sxs-lookup"><span data-stu-id="05490-166">Hand Tracked Right</span></span> | [<span data-ttu-id="05490-167">布林曲線</span><span class="sxs-lookup"><span data-stu-id="05490-167">Boolean Curve</span></span>](#boolean-curve) |
| <span data-ttu-id="05490-168">向左捏合手</span><span class="sxs-lookup"><span data-stu-id="05490-168">Hand Pinching Left</span></span> | [<span data-ttu-id="05490-169">布林曲線</span><span class="sxs-lookup"><span data-stu-id="05490-169">Boolean Curve</span></span>](#boolean-curve) |
| <span data-ttu-id="05490-170">右手捏合 Right</span><span class="sxs-lookup"><span data-stu-id="05490-170">Hand Pinching Right</span></span> | [<span data-ttu-id="05490-171">布林曲線</span><span class="sxs-lookup"><span data-stu-id="05490-171">Boolean Curve</span></span>](#boolean-curve) |
| <span data-ttu-id="05490-172">左邊的接點</span><span class="sxs-lookup"><span data-stu-id="05490-172">Hand Joints Left</span></span> | [<span data-ttu-id="05490-173">聯合姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="05490-173">Joint Pose Curves</span></span>](#joint-pose-curves) |
| <span data-ttu-id="05490-174">右邊</span><span class="sxs-lookup"><span data-stu-id="05490-174">Hand Joints Right</span></span> | [<span data-ttu-id="05490-175">聯合姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="05490-175">Joint Pose Curves</span></span>](#joint-pose-curves) |

### <a name="joint-pose-curves"></a><span data-ttu-id="05490-176">聯合姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="05490-176">Joint pose curves</span></span>

<span data-ttu-id="05490-177">每次都會儲存一連串的聯合動畫曲線。</span><span class="sxs-lookup"><span data-stu-id="05490-177">For each hand a sequence of joint animation curves is stored.</span></span> <span data-ttu-id="05490-178">接點的數目是固定的，而且會針對每個聯合儲存一組姿勢曲線。</span><span class="sxs-lookup"><span data-stu-id="05490-178">The number of joints is fixed, and a set of pose curves is stored for each joint.</span></span>

| <span data-ttu-id="05490-179">區段</span><span class="sxs-lookup"><span data-stu-id="05490-179">Section</span></span> | <span data-ttu-id="05490-180">類型</span><span class="sxs-lookup"><span data-stu-id="05490-180">Type</span></span> |
|---------|------|
| <span data-ttu-id="05490-181">無</span><span class="sxs-lookup"><span data-stu-id="05490-181">None</span></span> | [<span data-ttu-id="05490-182">姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="05490-182">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="05490-183">手腕</span><span class="sxs-lookup"><span data-stu-id="05490-183">Wrist</span></span> | [<span data-ttu-id="05490-184">姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="05490-184">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="05490-185">Palm</span><span class="sxs-lookup"><span data-stu-id="05490-185">Palm</span></span> | [<span data-ttu-id="05490-186">姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="05490-186">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="05490-187">ThumbMetacarpalJoint</span><span class="sxs-lookup"><span data-stu-id="05490-187">ThumbMetacarpalJoint</span></span> | [<span data-ttu-id="05490-188">姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="05490-188">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="05490-189">ThumbProximalJoint</span><span class="sxs-lookup"><span data-stu-id="05490-189">ThumbProximalJoint</span></span> | [<span data-ttu-id="05490-190">姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="05490-190">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="05490-191">ThumbDistalJoint</span><span class="sxs-lookup"><span data-stu-id="05490-191">ThumbDistalJoint</span></span> | [<span data-ttu-id="05490-192">姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="05490-192">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="05490-193">ThumbTip</span><span class="sxs-lookup"><span data-stu-id="05490-193">ThumbTip</span></span> | [<span data-ttu-id="05490-194">姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="05490-194">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="05490-195">IndexMetacarpal</span><span class="sxs-lookup"><span data-stu-id="05490-195">IndexMetacarpal</span></span> | [<span data-ttu-id="05490-196">姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="05490-196">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="05490-197">IndexKnuckle</span><span class="sxs-lookup"><span data-stu-id="05490-197">IndexKnuckle</span></span> | [<span data-ttu-id="05490-198">姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="05490-198">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="05490-199">IndexMiddleJoint</span><span class="sxs-lookup"><span data-stu-id="05490-199">IndexMiddleJoint</span></span> | [<span data-ttu-id="05490-200">姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="05490-200">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="05490-201">IndexDistalJoint</span><span class="sxs-lookup"><span data-stu-id="05490-201">IndexDistalJoint</span></span> | [<span data-ttu-id="05490-202">姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="05490-202">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="05490-203">IndexTip</span><span class="sxs-lookup"><span data-stu-id="05490-203">IndexTip</span></span> | [<span data-ttu-id="05490-204">姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="05490-204">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="05490-205">MiddleMetacarpal</span><span class="sxs-lookup"><span data-stu-id="05490-205">MiddleMetacarpal</span></span> | [<span data-ttu-id="05490-206">姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="05490-206">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="05490-207">MiddleKnuckle</span><span class="sxs-lookup"><span data-stu-id="05490-207">MiddleKnuckle</span></span> | [<span data-ttu-id="05490-208">姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="05490-208">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="05490-209">MiddleMiddleJoint</span><span class="sxs-lookup"><span data-stu-id="05490-209">MiddleMiddleJoint</span></span> | [<span data-ttu-id="05490-210">姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="05490-210">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="05490-211">MiddleDistalJoint</span><span class="sxs-lookup"><span data-stu-id="05490-211">MiddleDistalJoint</span></span> | [<span data-ttu-id="05490-212">姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="05490-212">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="05490-213">MiddleTip</span><span class="sxs-lookup"><span data-stu-id="05490-213">MiddleTip</span></span> | [<span data-ttu-id="05490-214">姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="05490-214">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="05490-215">RingMetacarpal</span><span class="sxs-lookup"><span data-stu-id="05490-215">RingMetacarpal</span></span> | [<span data-ttu-id="05490-216">姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="05490-216">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="05490-217">RingKnuckle</span><span class="sxs-lookup"><span data-stu-id="05490-217">RingKnuckle</span></span> | [<span data-ttu-id="05490-218">姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="05490-218">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="05490-219">RingMiddleJoint</span><span class="sxs-lookup"><span data-stu-id="05490-219">RingMiddleJoint</span></span> | [<span data-ttu-id="05490-220">姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="05490-220">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="05490-221">RingDistalJoint</span><span class="sxs-lookup"><span data-stu-id="05490-221">RingDistalJoint</span></span> | [<span data-ttu-id="05490-222">姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="05490-222">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="05490-223">RingTip</span><span class="sxs-lookup"><span data-stu-id="05490-223">RingTip</span></span> | [<span data-ttu-id="05490-224">姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="05490-224">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="05490-225">PinkyMetacarpal</span><span class="sxs-lookup"><span data-stu-id="05490-225">PinkyMetacarpal</span></span> | [<span data-ttu-id="05490-226">姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="05490-226">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="05490-227">PinkyKnuckle</span><span class="sxs-lookup"><span data-stu-id="05490-227">PinkyKnuckle</span></span> | [<span data-ttu-id="05490-228">姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="05490-228">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="05490-229">PinkyMiddleJoint</span><span class="sxs-lookup"><span data-stu-id="05490-229">PinkyMiddleJoint</span></span> | [<span data-ttu-id="05490-230">姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="05490-230">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="05490-231">PinkyDistalJoint</span><span class="sxs-lookup"><span data-stu-id="05490-231">PinkyDistalJoint</span></span> | [<span data-ttu-id="05490-232">姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="05490-232">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="05490-233">PinkyTip</span><span class="sxs-lookup"><span data-stu-id="05490-233">PinkyTip</span></span> | [<span data-ttu-id="05490-234">姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="05490-234">Pose Curves</span></span>](#pose-curves) |

### <a name="pose-curves"></a><span data-ttu-id="05490-235">姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="05490-235">Pose curves</span></span>

<span data-ttu-id="05490-236">姿勢曲線是位置向量的三個動畫曲線序列，後面接著4個旋轉四元數的動畫曲線。</span><span class="sxs-lookup"><span data-stu-id="05490-236">Pose curves are a sequence of 3 animation curves for the position vector, followed by 4 animation curves for the rotation quaternion.</span></span>

| <span data-ttu-id="05490-237">區段</span><span class="sxs-lookup"><span data-stu-id="05490-237">Section</span></span> | <span data-ttu-id="05490-238">類型</span><span class="sxs-lookup"><span data-stu-id="05490-238">Type</span></span> |
|---------|------|
| <span data-ttu-id="05490-239">位置 X</span><span class="sxs-lookup"><span data-stu-id="05490-239">Position X</span></span> | [<span data-ttu-id="05490-240">浮點數曲線</span><span class="sxs-lookup"><span data-stu-id="05490-240">Float Curve</span></span>](#float-curve) |
| <span data-ttu-id="05490-241">位置 Y</span><span class="sxs-lookup"><span data-stu-id="05490-241">Position Y</span></span> | [<span data-ttu-id="05490-242">浮點數曲線</span><span class="sxs-lookup"><span data-stu-id="05490-242">Float Curve</span></span>](#float-curve) |
| <span data-ttu-id="05490-243">位置 Z</span><span class="sxs-lookup"><span data-stu-id="05490-243">Position Z</span></span> | [<span data-ttu-id="05490-244">浮點數曲線</span><span class="sxs-lookup"><span data-stu-id="05490-244">Float Curve</span></span>](#float-curve) |
| <span data-ttu-id="05490-245">旋轉 X</span><span class="sxs-lookup"><span data-stu-id="05490-245">Rotation X</span></span> | [<span data-ttu-id="05490-246">浮點數曲線</span><span class="sxs-lookup"><span data-stu-id="05490-246">Float Curve</span></span>](#float-curve) |
| <span data-ttu-id="05490-247">旋轉 Y</span><span class="sxs-lookup"><span data-stu-id="05490-247">Rotation Y</span></span> | [<span data-ttu-id="05490-248">浮點數曲線</span><span class="sxs-lookup"><span data-stu-id="05490-248">Float Curve</span></span>](#float-curve) |
| <span data-ttu-id="05490-249">旋轉 Z</span><span class="sxs-lookup"><span data-stu-id="05490-249">Rotation Z</span></span> | [<span data-ttu-id="05490-250">浮點數曲線</span><span class="sxs-lookup"><span data-stu-id="05490-250">Float Curve</span></span>](#float-curve) |
| <span data-ttu-id="05490-251">旋轉 W</span><span class="sxs-lookup"><span data-stu-id="05490-251">Rotation W</span></span> | [<span data-ttu-id="05490-252">浮點數曲線</span><span class="sxs-lookup"><span data-stu-id="05490-252">Float Curve</span></span>](#float-curve) |

### <a name="ray-curves"></a><span data-ttu-id="05490-253">光線曲線</span><span class="sxs-lookup"><span data-stu-id="05490-253">Ray curves</span></span>

<span data-ttu-id="05490-254">光線曲線是原點向量的三個動畫曲線序列，後面接著三個方向向量的動畫曲線。</span><span class="sxs-lookup"><span data-stu-id="05490-254">Ray curves are a sequence of 3 animation curves for the origin vector, followed by 3 animation curves for the direction vector.</span></span>

| <span data-ttu-id="05490-255">區段</span><span class="sxs-lookup"><span data-stu-id="05490-255">Section</span></span> | <span data-ttu-id="05490-256">類型</span><span class="sxs-lookup"><span data-stu-id="05490-256">Type</span></span> |
|---------|------|
| <span data-ttu-id="05490-257">原始 X</span><span class="sxs-lookup"><span data-stu-id="05490-257">Origin X</span></span> | [<span data-ttu-id="05490-258">浮點數曲線</span><span class="sxs-lookup"><span data-stu-id="05490-258">Float Curve</span></span>](#float-curve) |
| <span data-ttu-id="05490-259">原點 Y</span><span class="sxs-lookup"><span data-stu-id="05490-259">Origin Y</span></span> | [<span data-ttu-id="05490-260">浮點數曲線</span><span class="sxs-lookup"><span data-stu-id="05490-260">Float Curve</span></span>](#float-curve) |
| <span data-ttu-id="05490-261">原點 Z</span><span class="sxs-lookup"><span data-stu-id="05490-261">Origin Z</span></span> | [<span data-ttu-id="05490-262">浮點數曲線</span><span class="sxs-lookup"><span data-stu-id="05490-262">Float Curve</span></span>](#float-curve) |
| <span data-ttu-id="05490-263">方向 X</span><span class="sxs-lookup"><span data-stu-id="05490-263">Direction X</span></span> | [<span data-ttu-id="05490-264">浮點數曲線</span><span class="sxs-lookup"><span data-stu-id="05490-264">Float Curve</span></span>](#float-curve) |
| <span data-ttu-id="05490-265">方向 Y</span><span class="sxs-lookup"><span data-stu-id="05490-265">Direction Y</span></span> | [<span data-ttu-id="05490-266">浮點數曲線</span><span class="sxs-lookup"><span data-stu-id="05490-266">Float Curve</span></span>](#float-curve) |
| <span data-ttu-id="05490-267">方向 Z</span><span class="sxs-lookup"><span data-stu-id="05490-267">Direction Z</span></span> | [<span data-ttu-id="05490-268">浮點數曲線</span><span class="sxs-lookup"><span data-stu-id="05490-268">Float Curve</span></span>](#float-curve) |

### <a name="float-curve"></a><span data-ttu-id="05490-269">浮點數曲線</span><span class="sxs-lookup"><span data-stu-id="05490-269">Float curve</span></span>

<span data-ttu-id="05490-270">浮點數曲線是具有不定數目之主要畫面格的完備貝茲曲線。</span><span class="sxs-lookup"><span data-stu-id="05490-270">Floating point curves are fully fledged Bézier curves with a variable number of keyframes.</span></span> <span data-ttu-id="05490-271">每個主要畫面格都會儲存時間和曲線值，以及每個主要畫面格左右側邊的正切和加權。</span><span class="sxs-lookup"><span data-stu-id="05490-271">Each keyframe stores a time and a curve value, as well as tangents and weights on the left and right side of each keyframe.</span></span>

| <span data-ttu-id="05490-272">區段</span><span class="sxs-lookup"><span data-stu-id="05490-272">Section</span></span> | <span data-ttu-id="05490-273">類型</span><span class="sxs-lookup"><span data-stu-id="05490-273">Type</span></span> |
|---------|------|
| <span data-ttu-id="05490-274">預先換行模式</span><span class="sxs-lookup"><span data-stu-id="05490-274">Pre-Wrap Mode</span></span> | <span data-ttu-id="05490-275">Int32、 [Wrap 模式](#wrap-mode)</span><span class="sxs-lookup"><span data-stu-id="05490-275">Int32, [Wrap Mode](#wrap-mode)</span></span> |
| <span data-ttu-id="05490-276">後置換行模式</span><span class="sxs-lookup"><span data-stu-id="05490-276">Post-Wrap Mode</span></span> | <span data-ttu-id="05490-277">Int32、 [Wrap 模式](#wrap-mode)</span><span class="sxs-lookup"><span data-stu-id="05490-277">Int32, [Wrap Mode](#wrap-mode)</span></span> |
| <span data-ttu-id="05490-278">關鍵畫面數</span><span class="sxs-lookup"><span data-stu-id="05490-278">Number of keyframes</span></span> | <span data-ttu-id="05490-279">Int32</span><span class="sxs-lookup"><span data-stu-id="05490-279">Int32</span></span> |
| <span data-ttu-id="05490-280">關鍵 幀</span><span class="sxs-lookup"><span data-stu-id="05490-280">Keyframes</span></span> | [<span data-ttu-id="05490-281">Float 主要畫面格</span><span class="sxs-lookup"><span data-stu-id="05490-281">Float Keyframe</span></span>](#float-keyframe) |

### <a name="float-keyframe"></a><span data-ttu-id="05490-282">Float 主要畫面格</span><span class="sxs-lookup"><span data-stu-id="05490-282">Float keyframe</span></span>

<span data-ttu-id="05490-283">Float 主要畫面格會在基本時間和值的旁邊儲存正切值和加權值。</span><span class="sxs-lookup"><span data-stu-id="05490-283">A float keyframe stores tangent and weight values alongside the basic time and value.</span></span>

| <span data-ttu-id="05490-284">區段</span><span class="sxs-lookup"><span data-stu-id="05490-284">Section</span></span> | <span data-ttu-id="05490-285">類型</span><span class="sxs-lookup"><span data-stu-id="05490-285">Type</span></span> |
|---------|------|
| <span data-ttu-id="05490-286">時間</span><span class="sxs-lookup"><span data-stu-id="05490-286">Time</span></span> | <span data-ttu-id="05490-287">Float32</span><span class="sxs-lookup"><span data-stu-id="05490-287">Float32</span></span> |
| <span data-ttu-id="05490-288">值</span><span class="sxs-lookup"><span data-stu-id="05490-288">Value</span></span> | <span data-ttu-id="05490-289">Float32</span><span class="sxs-lookup"><span data-stu-id="05490-289">Float32</span></span> |
| <span data-ttu-id="05490-290">InTangent</span><span class="sxs-lookup"><span data-stu-id="05490-290">InTangent</span></span> | <span data-ttu-id="05490-291">Float32</span><span class="sxs-lookup"><span data-stu-id="05490-291">Float32</span></span> |
| <span data-ttu-id="05490-292">OutTangent</span><span class="sxs-lookup"><span data-stu-id="05490-292">OutTangent</span></span> | <span data-ttu-id="05490-293">Float32</span><span class="sxs-lookup"><span data-stu-id="05490-293">Float32</span></span> |
| <span data-ttu-id="05490-294">InWeight</span><span class="sxs-lookup"><span data-stu-id="05490-294">InWeight</span></span> | <span data-ttu-id="05490-295">Float32</span><span class="sxs-lookup"><span data-stu-id="05490-295">Float32</span></span> |
| <span data-ttu-id="05490-296">OutWeight</span><span class="sxs-lookup"><span data-stu-id="05490-296">OutWeight</span></span> | <span data-ttu-id="05490-297">Float32</span><span class="sxs-lookup"><span data-stu-id="05490-297">Float32</span></span> |
| <span data-ttu-id="05490-298">WeightedMode</span><span class="sxs-lookup"><span data-stu-id="05490-298">WeightedMode</span></span> | <span data-ttu-id="05490-299">Int32、 [加權模式](#weighted-mode)</span><span class="sxs-lookup"><span data-stu-id="05490-299">Int32, [Weighted Mode](#weighted-mode)</span></span> |

### <a name="boolean-curve"></a><span data-ttu-id="05490-300">布林曲線</span><span class="sxs-lookup"><span data-stu-id="05490-300">Boolean curve</span></span>

<span data-ttu-id="05490-301">布林曲線是開啟/關閉值的簡單序列。</span><span class="sxs-lookup"><span data-stu-id="05490-301">Boolean curves are simple sequences of on/off values.</span></span> <span data-ttu-id="05490-302">在每個主要畫面上，曲線的值會立即翻轉。</span><span class="sxs-lookup"><span data-stu-id="05490-302">On every keyframe the value of the curve flips immediately.</span></span>

| <span data-ttu-id="05490-303">區段</span><span class="sxs-lookup"><span data-stu-id="05490-303">Section</span></span> | <span data-ttu-id="05490-304">類型</span><span class="sxs-lookup"><span data-stu-id="05490-304">Type</span></span> |
|---------|------|
| <span data-ttu-id="05490-305">預先換行模式</span><span class="sxs-lookup"><span data-stu-id="05490-305">Pre-Wrap Mode</span></span> | <span data-ttu-id="05490-306">Int32、 [Wrap 模式](#wrap-mode)</span><span class="sxs-lookup"><span data-stu-id="05490-306">Int32, [Wrap Mode](#wrap-mode)</span></span> |
| <span data-ttu-id="05490-307">後置換行模式</span><span class="sxs-lookup"><span data-stu-id="05490-307">Post-Wrap Mode</span></span> | <span data-ttu-id="05490-308">Int32、 [Wrap 模式](#wrap-mode)</span><span class="sxs-lookup"><span data-stu-id="05490-308">Int32, [Wrap Mode](#wrap-mode)</span></span> |
| <span data-ttu-id="05490-309">關鍵畫面數</span><span class="sxs-lookup"><span data-stu-id="05490-309">Number of keyframes</span></span> | <span data-ttu-id="05490-310">Int32</span><span class="sxs-lookup"><span data-stu-id="05490-310">Int32</span></span> |
| <span data-ttu-id="05490-311">關鍵 幀</span><span class="sxs-lookup"><span data-stu-id="05490-311">Keyframes</span></span> | [<span data-ttu-id="05490-312">布林主要畫面格</span><span class="sxs-lookup"><span data-stu-id="05490-312">Boolean Keyframe</span></span>](#boolean-keyframe) |

### <a name="boolean-keyframe"></a><span data-ttu-id="05490-313">布林主要畫面格</span><span class="sxs-lookup"><span data-stu-id="05490-313">Boolean keyframe</span></span>

<span data-ttu-id="05490-314">布林值主要畫面格只會儲存時間和值。</span><span class="sxs-lookup"><span data-stu-id="05490-314">A boolean keyframe only stores a time and value.</span></span>

| <span data-ttu-id="05490-315">區段</span><span class="sxs-lookup"><span data-stu-id="05490-315">Section</span></span> | <span data-ttu-id="05490-316">類型</span><span class="sxs-lookup"><span data-stu-id="05490-316">Type</span></span> |
|---------|------|
| <span data-ttu-id="05490-317">時間</span><span class="sxs-lookup"><span data-stu-id="05490-317">Time</span></span> | <span data-ttu-id="05490-318">Float32</span><span class="sxs-lookup"><span data-stu-id="05490-318">Float32</span></span> |
| <span data-ttu-id="05490-319">值</span><span class="sxs-lookup"><span data-stu-id="05490-319">Value</span></span> | <span data-ttu-id="05490-320">Float32</span><span class="sxs-lookup"><span data-stu-id="05490-320">Float32</span></span> |

### <a name="wrap-mode"></a><span data-ttu-id="05490-321">Wrap 模式</span><span class="sxs-lookup"><span data-stu-id="05490-321">Wrap mode</span></span>

<span data-ttu-id="05490-322">前置和後置換行模式的語法遵循 [Unity WrapMode](https://docs.unity3d.com/ScriptReference/WrapMode.html) 定義。</span><span class="sxs-lookup"><span data-stu-id="05490-322">The semantics of Pre- and Post-Wrap modes follow the [Unity WrapMode](https://docs.unity3d.com/ScriptReference/WrapMode.html) definition.</span></span> <span data-ttu-id="05490-323">它們是下列位的組合：</span><span class="sxs-lookup"><span data-stu-id="05490-323">They are a combination of the following bits:</span></span>

| <span data-ttu-id="05490-324">值</span><span class="sxs-lookup"><span data-stu-id="05490-324">Value</span></span> | <span data-ttu-id="05490-325">意義</span><span class="sxs-lookup"><span data-stu-id="05490-325">Meaning</span></span> |
|-------|---------|
| <span data-ttu-id="05490-326">0</span><span class="sxs-lookup"><span data-stu-id="05490-326">0</span></span> | <span data-ttu-id="05490-327">預設值：讀取設定為較高的預設重複模式。</span><span class="sxs-lookup"><span data-stu-id="05490-327">Default: Reads the default repeat mode set higher up.</span></span> |
| <span data-ttu-id="05490-328">1</span><span class="sxs-lookup"><span data-stu-id="05490-328">1</span></span> | <span data-ttu-id="05490-329">一次：當時間到達動畫剪輯的結尾時，剪輯將會自動停止播放，而時間將會重設為剪輯的開頭。</span><span class="sxs-lookup"><span data-stu-id="05490-329">Once: When time reaches the end of the animation clip, the clip will automatically stop playing and time will be reset to beginning of the clip.</span></span> |
| <span data-ttu-id="05490-330">2</span><span class="sxs-lookup"><span data-stu-id="05490-330">2</span></span> | <span data-ttu-id="05490-331">Loop：當時間達到動畫剪輯的結尾時，時間會在一開始就繼續進行。</span><span class="sxs-lookup"><span data-stu-id="05490-331">Loop: When time reaches the end of the animation clip, time will continue at the beginning.</span></span> |
| <span data-ttu-id="05490-332">4</span><span class="sxs-lookup"><span data-stu-id="05490-332">4</span></span> | <span data-ttu-id="05490-333">PingPong：當時間達到動畫剪輯的結尾時，時間會在開始與結束時 ping 一次。</span><span class="sxs-lookup"><span data-stu-id="05490-333">PingPong: When time reaches the end of the animation clip, time will ping pong back between beginning and end.</span></span> |
| <span data-ttu-id="05490-334">8</span><span class="sxs-lookup"><span data-stu-id="05490-334">8</span></span> | <span data-ttu-id="05490-335">ClampForever：播放動畫。</span><span class="sxs-lookup"><span data-stu-id="05490-335">ClampForever: Plays back the animation.</span></span> <span data-ttu-id="05490-336">到達結束時，它會繼續播放最後一個畫面格，而且永遠不會停止播放。</span><span class="sxs-lookup"><span data-stu-id="05490-336">When it reaches the end, it will keep playing the last frame and never stop playing.</span></span> |

### <a name="weighted-mode"></a><span data-ttu-id="05490-337">加權模式</span><span class="sxs-lookup"><span data-stu-id="05490-337">Weighted mode</span></span>

<span data-ttu-id="05490-338">加權模式的語義遵循 [Unity WeightedMode](https://docs.unity3d.com/ScriptReference/WeightedMode.html) 定義。</span><span class="sxs-lookup"><span data-stu-id="05490-338">The semantics of the Weighted mode follow the [Unity WeightedMode](https://docs.unity3d.com/ScriptReference/WeightedMode.html) definition.</span></span>

| <span data-ttu-id="05490-339">值</span><span class="sxs-lookup"><span data-stu-id="05490-339">Value</span></span> | <span data-ttu-id="05490-340">意義</span><span class="sxs-lookup"><span data-stu-id="05490-340">Meaning</span></span> |
|-------|---------|
| <span data-ttu-id="05490-341">0</span><span class="sxs-lookup"><span data-stu-id="05490-341">0</span></span> | <span data-ttu-id="05490-342">None：在計算曲線區段時排除 inWeight 或 outWeight。</span><span class="sxs-lookup"><span data-stu-id="05490-342">None: Exclude both inWeight or outWeight when calculating curve segments.</span></span> |
| <span data-ttu-id="05490-343">1</span><span class="sxs-lookup"><span data-stu-id="05490-343">1</span></span> | <span data-ttu-id="05490-344">在中：在計算上一個曲線區段時包含 inWeight。</span><span class="sxs-lookup"><span data-stu-id="05490-344">In: Include inWeight when calculating the previous curve segment.</span></span> |
| <span data-ttu-id="05490-345">2</span><span class="sxs-lookup"><span data-stu-id="05490-345">2</span></span> | <span data-ttu-id="05490-346">Out：在計算下一個曲線區段時包含 outWeight。</span><span class="sxs-lookup"><span data-stu-id="05490-346">Out: Include outWeight when calculating the next curve segment.</span></span> |
| <span data-ttu-id="05490-347">3</span><span class="sxs-lookup"><span data-stu-id="05490-347">3</span></span> | <span data-ttu-id="05490-348">兩者：在計算曲線區段時包含 inWeight 和 outWeight。</span><span class="sxs-lookup"><span data-stu-id="05490-348">Both: Include inWeight and outWeight when calculating curve segments.</span></span> |
