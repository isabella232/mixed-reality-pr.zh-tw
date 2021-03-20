---
title: InputAnimationFileFormat
description: MRTK 中輸入動畫二進位檔案格式規格的相關檔
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: 81c83fe88b4943f4857898a6d0beebb3f5c05ba9
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104695315"
---
# <a name="input-animation-binary-file-format-specification"></a><span data-ttu-id="7263a-104">輸入動畫二進位檔案格式規格</span><span class="sxs-lookup"><span data-stu-id="7263a-104">Input animation binary file format specification</span></span>

## <a name="overall-structure"></a><span data-ttu-id="7263a-105">整體結構</span><span class="sxs-lookup"><span data-stu-id="7263a-105">Overall structure</span></span>

<span data-ttu-id="7263a-106">輸入動畫二進位檔案的開頭為64位整數魔術數位。</span><span class="sxs-lookup"><span data-stu-id="7263a-106">The input animation binary file begins with a 64 bit integer magic number.</span></span> <span data-ttu-id="7263a-107">這個數位的十六進位標記法值是 `0x6a8faf6e0f9e42c6` ，而且可以用來識別有效的輸入動畫檔案。</span><span class="sxs-lookup"><span data-stu-id="7263a-107">The value of this number in hexadecimal notation is `0x6a8faf6e0f9e42c6` and can be used to identify valid input animation files.</span></span>

<span data-ttu-id="7263a-108">接下來八個位元組是兩個 Int32 值，用來宣告檔案的主要和次要版本號碼。</span><span class="sxs-lookup"><span data-stu-id="7263a-108">The next eight bytes are two Int32 values declaring the major and minor version number of the file.</span></span>

<span data-ttu-id="7263a-109">檔案的其餘部分是由動畫資料所佔用，可能會在版本號碼之間變更。</span><span class="sxs-lookup"><span data-stu-id="7263a-109">The rest of the file is taken up by animation data, which may change between version numbers.</span></span>

| <span data-ttu-id="7263a-110">區段</span><span class="sxs-lookup"><span data-stu-id="7263a-110">Section</span></span> | <span data-ttu-id="7263a-111">類型</span><span class="sxs-lookup"><span data-stu-id="7263a-111">Type</span></span> |
|---------|------|
| <span data-ttu-id="7263a-112">魔術數位</span><span class="sxs-lookup"><span data-stu-id="7263a-112">Magic Number</span></span> | <span data-ttu-id="7263a-113">Int64</span><span class="sxs-lookup"><span data-stu-id="7263a-113">Int64</span></span> |
| <span data-ttu-id="7263a-114">主要版本號碼</span><span class="sxs-lookup"><span data-stu-id="7263a-114">Major Version Number</span></span> | <span data-ttu-id="7263a-115">Int32</span><span class="sxs-lookup"><span data-stu-id="7263a-115">Int32</span></span> |
| <span data-ttu-id="7263a-116">次要版本號碼</span><span class="sxs-lookup"><span data-stu-id="7263a-116">Minor Version Number</span></span> | <span data-ttu-id="7263a-117">Int32</span><span class="sxs-lookup"><span data-stu-id="7263a-117">Int32</span></span> |
| <span data-ttu-id="7263a-118">動畫資料</span><span class="sxs-lookup"><span data-stu-id="7263a-118">Animation Data</span></span> | <span data-ttu-id="7263a-119">_請參閱版本區段_</span><span class="sxs-lookup"><span data-stu-id="7263a-119">_see version section_</span></span> |

## <a name="version-10"></a><span data-ttu-id="7263a-120">版本 1.0</span><span class="sxs-lookup"><span data-stu-id="7263a-120">Version 1.0</span></span>

<span data-ttu-id="7263a-121">輸入動畫資料包含一連串的動畫曲線。</span><span class="sxs-lookup"><span data-stu-id="7263a-121">The input animation data consists of a sequence of animation curves.</span></span> <span data-ttu-id="7263a-122">動畫曲線的數目和意義是固定的，但每個曲線都可以有不同的主要畫面格數目。</span><span class="sxs-lookup"><span data-stu-id="7263a-122">The number and meaning of animation curves is fixed, but each curve can have a different number of keyframes.</span></span>

| <span data-ttu-id="7263a-123">區段</span><span class="sxs-lookup"><span data-stu-id="7263a-123">Section</span></span> | <span data-ttu-id="7263a-124">類型</span><span class="sxs-lookup"><span data-stu-id="7263a-124">Type</span></span> |
|---------|------|
| <span data-ttu-id="7263a-125">相機</span><span class="sxs-lookup"><span data-stu-id="7263a-125">Camera</span></span> | [<span data-ttu-id="7263a-126">姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="7263a-126">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="7263a-127">靠右追蹤</span><span class="sxs-lookup"><span data-stu-id="7263a-127">Hand Tracked Left</span></span> | [<span data-ttu-id="7263a-128">布林曲線</span><span class="sxs-lookup"><span data-stu-id="7263a-128">Boolean Curve</span></span>](#boolean-curve) |
| <span data-ttu-id="7263a-129">右側追蹤</span><span class="sxs-lookup"><span data-stu-id="7263a-129">Hand Tracked Right</span></span> | [<span data-ttu-id="7263a-130">布林曲線</span><span class="sxs-lookup"><span data-stu-id="7263a-130">Boolean Curve</span></span>](#boolean-curve) |
| <span data-ttu-id="7263a-131">向左捏合手</span><span class="sxs-lookup"><span data-stu-id="7263a-131">Hand Pinching Left</span></span> | [<span data-ttu-id="7263a-132">布林曲線</span><span class="sxs-lookup"><span data-stu-id="7263a-132">Boolean Curve</span></span>](#boolean-curve) |
| <span data-ttu-id="7263a-133">右手捏合 Right</span><span class="sxs-lookup"><span data-stu-id="7263a-133">Hand Pinching Right</span></span> | [<span data-ttu-id="7263a-134">布林曲線</span><span class="sxs-lookup"><span data-stu-id="7263a-134">Boolean Curve</span></span>](#boolean-curve) |
| <span data-ttu-id="7263a-135">左邊的接點</span><span class="sxs-lookup"><span data-stu-id="7263a-135">Hand Joints Left</span></span> | [<span data-ttu-id="7263a-136">聯合姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="7263a-136">Joint Pose Curves</span></span>](#joint-pose-curves) |
| <span data-ttu-id="7263a-137">右邊</span><span class="sxs-lookup"><span data-stu-id="7263a-137">Hand Joints Right</span></span> | [<span data-ttu-id="7263a-138">聯合姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="7263a-138">Joint Pose Curves</span></span>](#joint-pose-curves) |

### <a name="joint-pose-curves"></a><span data-ttu-id="7263a-139">聯合姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="7263a-139">Joint pose curves</span></span>

<span data-ttu-id="7263a-140">每次都會儲存一連串的聯合動畫曲線。</span><span class="sxs-lookup"><span data-stu-id="7263a-140">For each hand a sequence of joint animation curves is stored.</span></span> <span data-ttu-id="7263a-141">接點的數目是固定的，而且會針對每個聯合儲存一組姿勢曲線。</span><span class="sxs-lookup"><span data-stu-id="7263a-141">The number of joints is fixed, and a set of pose curves is stored for each joint.</span></span>

| <span data-ttu-id="7263a-142">區段</span><span class="sxs-lookup"><span data-stu-id="7263a-142">Section</span></span> | <span data-ttu-id="7263a-143">類型</span><span class="sxs-lookup"><span data-stu-id="7263a-143">Type</span></span> |
|---------|------|
| <span data-ttu-id="7263a-144">無</span><span class="sxs-lookup"><span data-stu-id="7263a-144">None</span></span> | [<span data-ttu-id="7263a-145">姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="7263a-145">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="7263a-146">手腕</span><span class="sxs-lookup"><span data-stu-id="7263a-146">Wrist</span></span> | [<span data-ttu-id="7263a-147">姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="7263a-147">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="7263a-148">Palm</span><span class="sxs-lookup"><span data-stu-id="7263a-148">Palm</span></span> | [<span data-ttu-id="7263a-149">姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="7263a-149">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="7263a-150">ThumbMetacarpalJoint</span><span class="sxs-lookup"><span data-stu-id="7263a-150">ThumbMetacarpalJoint</span></span> | [<span data-ttu-id="7263a-151">姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="7263a-151">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="7263a-152">ThumbProximalJoint</span><span class="sxs-lookup"><span data-stu-id="7263a-152">ThumbProximalJoint</span></span> | [<span data-ttu-id="7263a-153">姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="7263a-153">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="7263a-154">ThumbDistalJoint</span><span class="sxs-lookup"><span data-stu-id="7263a-154">ThumbDistalJoint</span></span> | [<span data-ttu-id="7263a-155">姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="7263a-155">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="7263a-156">ThumbTip</span><span class="sxs-lookup"><span data-stu-id="7263a-156">ThumbTip</span></span> | [<span data-ttu-id="7263a-157">姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="7263a-157">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="7263a-158">IndexMetacarpal</span><span class="sxs-lookup"><span data-stu-id="7263a-158">IndexMetacarpal</span></span> | [<span data-ttu-id="7263a-159">姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="7263a-159">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="7263a-160">IndexKnuckle</span><span class="sxs-lookup"><span data-stu-id="7263a-160">IndexKnuckle</span></span> | [<span data-ttu-id="7263a-161">姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="7263a-161">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="7263a-162">IndexMiddleJoint</span><span class="sxs-lookup"><span data-stu-id="7263a-162">IndexMiddleJoint</span></span> | [<span data-ttu-id="7263a-163">姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="7263a-163">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="7263a-164">IndexDistalJoint</span><span class="sxs-lookup"><span data-stu-id="7263a-164">IndexDistalJoint</span></span> | [<span data-ttu-id="7263a-165">姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="7263a-165">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="7263a-166">IndexTip</span><span class="sxs-lookup"><span data-stu-id="7263a-166">IndexTip</span></span> | [<span data-ttu-id="7263a-167">姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="7263a-167">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="7263a-168">MiddleMetacarpal</span><span class="sxs-lookup"><span data-stu-id="7263a-168">MiddleMetacarpal</span></span> | [<span data-ttu-id="7263a-169">姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="7263a-169">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="7263a-170">MiddleKnuckle</span><span class="sxs-lookup"><span data-stu-id="7263a-170">MiddleKnuckle</span></span> | [<span data-ttu-id="7263a-171">姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="7263a-171">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="7263a-172">MiddleMiddleJoint</span><span class="sxs-lookup"><span data-stu-id="7263a-172">MiddleMiddleJoint</span></span> | [<span data-ttu-id="7263a-173">姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="7263a-173">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="7263a-174">MiddleDistalJoint</span><span class="sxs-lookup"><span data-stu-id="7263a-174">MiddleDistalJoint</span></span> | [<span data-ttu-id="7263a-175">姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="7263a-175">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="7263a-176">MiddleTip</span><span class="sxs-lookup"><span data-stu-id="7263a-176">MiddleTip</span></span> | [<span data-ttu-id="7263a-177">姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="7263a-177">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="7263a-178">RingMetacarpal</span><span class="sxs-lookup"><span data-stu-id="7263a-178">RingMetacarpal</span></span> | [<span data-ttu-id="7263a-179">姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="7263a-179">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="7263a-180">RingKnuckle</span><span class="sxs-lookup"><span data-stu-id="7263a-180">RingKnuckle</span></span> | [<span data-ttu-id="7263a-181">姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="7263a-181">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="7263a-182">RingMiddleJoint</span><span class="sxs-lookup"><span data-stu-id="7263a-182">RingMiddleJoint</span></span> | [<span data-ttu-id="7263a-183">姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="7263a-183">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="7263a-184">RingDistalJoint</span><span class="sxs-lookup"><span data-stu-id="7263a-184">RingDistalJoint</span></span> | [<span data-ttu-id="7263a-185">姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="7263a-185">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="7263a-186">RingTip</span><span class="sxs-lookup"><span data-stu-id="7263a-186">RingTip</span></span> | [<span data-ttu-id="7263a-187">姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="7263a-187">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="7263a-188">PinkyMetacarpal</span><span class="sxs-lookup"><span data-stu-id="7263a-188">PinkyMetacarpal</span></span> | [<span data-ttu-id="7263a-189">姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="7263a-189">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="7263a-190">PinkyKnuckle</span><span class="sxs-lookup"><span data-stu-id="7263a-190">PinkyKnuckle</span></span> | [<span data-ttu-id="7263a-191">姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="7263a-191">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="7263a-192">PinkyMiddleJoint</span><span class="sxs-lookup"><span data-stu-id="7263a-192">PinkyMiddleJoint</span></span> | [<span data-ttu-id="7263a-193">姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="7263a-193">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="7263a-194">PinkyDistalJoint</span><span class="sxs-lookup"><span data-stu-id="7263a-194">PinkyDistalJoint</span></span> | [<span data-ttu-id="7263a-195">姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="7263a-195">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="7263a-196">PinkyTip</span><span class="sxs-lookup"><span data-stu-id="7263a-196">PinkyTip</span></span> | [<span data-ttu-id="7263a-197">姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="7263a-197">Pose Curves</span></span>](#pose-curves) |

### <a name="pose-curves"></a><span data-ttu-id="7263a-198">姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="7263a-198">Pose curves</span></span>

<span data-ttu-id="7263a-199">姿勢曲線是位置向量的三個動畫曲線序列，後面接著4個旋轉四元數的動畫曲線。</span><span class="sxs-lookup"><span data-stu-id="7263a-199">Pose curves are a sequence of 3 animation curves for the position vector, followed by 4 animation curves for the rotation quaternion.</span></span>

| <span data-ttu-id="7263a-200">區段</span><span class="sxs-lookup"><span data-stu-id="7263a-200">Section</span></span> | <span data-ttu-id="7263a-201">類型</span><span class="sxs-lookup"><span data-stu-id="7263a-201">Type</span></span> |
|---------|------|
| <span data-ttu-id="7263a-202">位置 X</span><span class="sxs-lookup"><span data-stu-id="7263a-202">Position X</span></span> | [<span data-ttu-id="7263a-203">浮點數曲線</span><span class="sxs-lookup"><span data-stu-id="7263a-203">Float Curve</span></span>](#float-curve) |
| <span data-ttu-id="7263a-204">位置 Y</span><span class="sxs-lookup"><span data-stu-id="7263a-204">Position Y</span></span> | [<span data-ttu-id="7263a-205">浮點數曲線</span><span class="sxs-lookup"><span data-stu-id="7263a-205">Float Curve</span></span>](#float-curve) |
| <span data-ttu-id="7263a-206">位置 Z</span><span class="sxs-lookup"><span data-stu-id="7263a-206">Position Z</span></span> | [<span data-ttu-id="7263a-207">浮點數曲線</span><span class="sxs-lookup"><span data-stu-id="7263a-207">Float Curve</span></span>](#float-curve) |
| <span data-ttu-id="7263a-208">旋轉 X</span><span class="sxs-lookup"><span data-stu-id="7263a-208">Rotation X</span></span> | [<span data-ttu-id="7263a-209">浮點數曲線</span><span class="sxs-lookup"><span data-stu-id="7263a-209">Float Curve</span></span>](#float-curve) |
| <span data-ttu-id="7263a-210">旋轉 Y</span><span class="sxs-lookup"><span data-stu-id="7263a-210">Rotation Y</span></span> | [<span data-ttu-id="7263a-211">浮點數曲線</span><span class="sxs-lookup"><span data-stu-id="7263a-211">Float Curve</span></span>](#float-curve) |
| <span data-ttu-id="7263a-212">旋轉 Z</span><span class="sxs-lookup"><span data-stu-id="7263a-212">Rotation Z</span></span> | [<span data-ttu-id="7263a-213">浮點數曲線</span><span class="sxs-lookup"><span data-stu-id="7263a-213">Float Curve</span></span>](#float-curve) |
| <span data-ttu-id="7263a-214">旋轉 W</span><span class="sxs-lookup"><span data-stu-id="7263a-214">Rotation W</span></span> | [<span data-ttu-id="7263a-215">浮點數曲線</span><span class="sxs-lookup"><span data-stu-id="7263a-215">Float Curve</span></span>](#float-curve) |

### <a name="float-curve"></a><span data-ttu-id="7263a-216">浮點數曲線</span><span class="sxs-lookup"><span data-stu-id="7263a-216">Float curve</span></span>

<span data-ttu-id="7263a-217">浮點數曲線是具有不定數目之主要畫面格的完備貝茲曲線。</span><span class="sxs-lookup"><span data-stu-id="7263a-217">Floating point curves are fully fledged Bézier curves with a variable number of keyframes.</span></span> <span data-ttu-id="7263a-218">每個主要畫面格都會儲存時間和曲線值，以及每個主要畫面格左右側邊的正切和加權。</span><span class="sxs-lookup"><span data-stu-id="7263a-218">Each keyframe stores a time and a curve value, as well as tangents and weights on the left and right side of each keyframe.</span></span>

| <span data-ttu-id="7263a-219">區段</span><span class="sxs-lookup"><span data-stu-id="7263a-219">Section</span></span> | <span data-ttu-id="7263a-220">類型</span><span class="sxs-lookup"><span data-stu-id="7263a-220">Type</span></span> |
|---------|------|
| <span data-ttu-id="7263a-221">預先換行模式</span><span class="sxs-lookup"><span data-stu-id="7263a-221">Pre-Wrap Mode</span></span> | <span data-ttu-id="7263a-222">Int32、 [Wrap 模式](#wrap-mode)</span><span class="sxs-lookup"><span data-stu-id="7263a-222">Int32, [Wrap Mode](#wrap-mode)</span></span> |
| <span data-ttu-id="7263a-223">後置換行模式</span><span class="sxs-lookup"><span data-stu-id="7263a-223">Post-Wrap Mode</span></span> | <span data-ttu-id="7263a-224">Int32、 [Wrap 模式](#wrap-mode)</span><span class="sxs-lookup"><span data-stu-id="7263a-224">Int32, [Wrap Mode](#wrap-mode)</span></span> |
| <span data-ttu-id="7263a-225">關鍵畫面數</span><span class="sxs-lookup"><span data-stu-id="7263a-225">Number of keyframes</span></span> | <span data-ttu-id="7263a-226">Int32</span><span class="sxs-lookup"><span data-stu-id="7263a-226">Int32</span></span> |
| <span data-ttu-id="7263a-227">關鍵 幀</span><span class="sxs-lookup"><span data-stu-id="7263a-227">Keyframes</span></span> | [<span data-ttu-id="7263a-228">Float 主要畫面格</span><span class="sxs-lookup"><span data-stu-id="7263a-228">Float Keyframe</span></span>](#float-keyframe) |

### <a name="float-keyframe"></a><span data-ttu-id="7263a-229">Float 主要畫面格</span><span class="sxs-lookup"><span data-stu-id="7263a-229">Float keyframe</span></span>

<span data-ttu-id="7263a-230">Float 主要畫面格會在基本時間和值的旁邊儲存正切值和加權值。</span><span class="sxs-lookup"><span data-stu-id="7263a-230">A float keyframe stores tangent and weight values alongside the basic time and value.</span></span>

| <span data-ttu-id="7263a-231">區段</span><span class="sxs-lookup"><span data-stu-id="7263a-231">Section</span></span> | <span data-ttu-id="7263a-232">類型</span><span class="sxs-lookup"><span data-stu-id="7263a-232">Type</span></span> |
|---------|------|
| <span data-ttu-id="7263a-233">Time</span><span class="sxs-lookup"><span data-stu-id="7263a-233">Time</span></span> | <span data-ttu-id="7263a-234">Float32</span><span class="sxs-lookup"><span data-stu-id="7263a-234">Float32</span></span> |
| <span data-ttu-id="7263a-235">值</span><span class="sxs-lookup"><span data-stu-id="7263a-235">Value</span></span> | <span data-ttu-id="7263a-236">Float32</span><span class="sxs-lookup"><span data-stu-id="7263a-236">Float32</span></span> |
| <span data-ttu-id="7263a-237">InTangent</span><span class="sxs-lookup"><span data-stu-id="7263a-237">InTangent</span></span> | <span data-ttu-id="7263a-238">Float32</span><span class="sxs-lookup"><span data-stu-id="7263a-238">Float32</span></span> |
| <span data-ttu-id="7263a-239">OutTangent</span><span class="sxs-lookup"><span data-stu-id="7263a-239">OutTangent</span></span> | <span data-ttu-id="7263a-240">Float32</span><span class="sxs-lookup"><span data-stu-id="7263a-240">Float32</span></span> |
| <span data-ttu-id="7263a-241">InWeight</span><span class="sxs-lookup"><span data-stu-id="7263a-241">InWeight</span></span> | <span data-ttu-id="7263a-242">Float32</span><span class="sxs-lookup"><span data-stu-id="7263a-242">Float32</span></span> |
| <span data-ttu-id="7263a-243">OutWeight</span><span class="sxs-lookup"><span data-stu-id="7263a-243">OutWeight</span></span> | <span data-ttu-id="7263a-244">Float32</span><span class="sxs-lookup"><span data-stu-id="7263a-244">Float32</span></span> |
| <span data-ttu-id="7263a-245">WeightedMode</span><span class="sxs-lookup"><span data-stu-id="7263a-245">WeightedMode</span></span> | <span data-ttu-id="7263a-246">Int32、 [加權模式](#weighted-mode)</span><span class="sxs-lookup"><span data-stu-id="7263a-246">Int32, [Weighted Mode](#weighted-mode)</span></span> |

### <a name="boolean-curve"></a><span data-ttu-id="7263a-247">布林曲線</span><span class="sxs-lookup"><span data-stu-id="7263a-247">Boolean curve</span></span>

<span data-ttu-id="7263a-248">布林曲線是開啟/關閉值的簡單序列。</span><span class="sxs-lookup"><span data-stu-id="7263a-248">Boolean curves are simple sequences of on/off values.</span></span> <span data-ttu-id="7263a-249">在每個主要畫面上，曲線的值會立即翻轉。</span><span class="sxs-lookup"><span data-stu-id="7263a-249">On every keyframe the value of the curve flips immediately.</span></span>

| <span data-ttu-id="7263a-250">區段</span><span class="sxs-lookup"><span data-stu-id="7263a-250">Section</span></span> | <span data-ttu-id="7263a-251">類型</span><span class="sxs-lookup"><span data-stu-id="7263a-251">Type</span></span> |
|---------|------|
| <span data-ttu-id="7263a-252">預先換行模式</span><span class="sxs-lookup"><span data-stu-id="7263a-252">Pre-Wrap Mode</span></span> | <span data-ttu-id="7263a-253">Int32、 [Wrap 模式](#wrap-mode)</span><span class="sxs-lookup"><span data-stu-id="7263a-253">Int32, [Wrap Mode](#wrap-mode)</span></span> |
| <span data-ttu-id="7263a-254">後置換行模式</span><span class="sxs-lookup"><span data-stu-id="7263a-254">Post-Wrap Mode</span></span> | <span data-ttu-id="7263a-255">Int32、 [Wrap 模式](#wrap-mode)</span><span class="sxs-lookup"><span data-stu-id="7263a-255">Int32, [Wrap Mode](#wrap-mode)</span></span> |
| <span data-ttu-id="7263a-256">關鍵畫面數</span><span class="sxs-lookup"><span data-stu-id="7263a-256">Number of keyframes</span></span> | <span data-ttu-id="7263a-257">Int32</span><span class="sxs-lookup"><span data-stu-id="7263a-257">Int32</span></span> |
| <span data-ttu-id="7263a-258">關鍵 幀</span><span class="sxs-lookup"><span data-stu-id="7263a-258">Keyframes</span></span> | [<span data-ttu-id="7263a-259">布林主要畫面格</span><span class="sxs-lookup"><span data-stu-id="7263a-259">Boolean Keyframe</span></span>](#boolean-keyframe) |

### <a name="boolean-keyframe"></a><span data-ttu-id="7263a-260">布林主要畫面格</span><span class="sxs-lookup"><span data-stu-id="7263a-260">Boolean keyframe</span></span>

<span data-ttu-id="7263a-261">布林值主要畫面格只會儲存時間和值。</span><span class="sxs-lookup"><span data-stu-id="7263a-261">A boolean keyframe only stores a time and value.</span></span>

| <span data-ttu-id="7263a-262">區段</span><span class="sxs-lookup"><span data-stu-id="7263a-262">Section</span></span> | <span data-ttu-id="7263a-263">類型</span><span class="sxs-lookup"><span data-stu-id="7263a-263">Type</span></span> |
|---------|------|
| <span data-ttu-id="7263a-264">Time</span><span class="sxs-lookup"><span data-stu-id="7263a-264">Time</span></span> | <span data-ttu-id="7263a-265">Float32</span><span class="sxs-lookup"><span data-stu-id="7263a-265">Float32</span></span> |
| <span data-ttu-id="7263a-266">值</span><span class="sxs-lookup"><span data-stu-id="7263a-266">Value</span></span> | <span data-ttu-id="7263a-267">Float32</span><span class="sxs-lookup"><span data-stu-id="7263a-267">Float32</span></span> |

### <a name="wrap-mode"></a><span data-ttu-id="7263a-268">Wrap 模式</span><span class="sxs-lookup"><span data-stu-id="7263a-268">Wrap mode</span></span>

<span data-ttu-id="7263a-269">前置和後置換行模式的語法遵循 [Unity WrapMode](https://docs.unity3d.com/ScriptReference/WrapMode.html) 定義。</span><span class="sxs-lookup"><span data-stu-id="7263a-269">The semantics of Pre- and Post-Wrap modes follow the [Unity WrapMode](https://docs.unity3d.com/ScriptReference/WrapMode.html) definition.</span></span> <span data-ttu-id="7263a-270">它們是下列位的組合：</span><span class="sxs-lookup"><span data-stu-id="7263a-270">They are a combination of the following bits:</span></span>

| <span data-ttu-id="7263a-271">值</span><span class="sxs-lookup"><span data-stu-id="7263a-271">Value</span></span> | <span data-ttu-id="7263a-272">意義</span><span class="sxs-lookup"><span data-stu-id="7263a-272">Meaning</span></span> |
|-------|---------|
| <span data-ttu-id="7263a-273">0</span><span class="sxs-lookup"><span data-stu-id="7263a-273">0</span></span> | <span data-ttu-id="7263a-274">預設值：讀取設定為較高的預設重複模式。</span><span class="sxs-lookup"><span data-stu-id="7263a-274">Default: Reads the default repeat mode set higher up.</span></span> |
| <span data-ttu-id="7263a-275">1</span><span class="sxs-lookup"><span data-stu-id="7263a-275">1</span></span> | <span data-ttu-id="7263a-276">一次：當時間到達動畫剪輯的結尾時，剪輯將會自動停止播放，而時間將會重設為剪輯的開頭。</span><span class="sxs-lookup"><span data-stu-id="7263a-276">Once: When time reaches the end of the animation clip, the clip will automatically stop playing and time will be reset to beginning of the clip.</span></span> |
| <span data-ttu-id="7263a-277">2</span><span class="sxs-lookup"><span data-stu-id="7263a-277">2</span></span> | <span data-ttu-id="7263a-278">Loop：當時間達到動畫剪輯的結尾時，時間會在一開始就繼續進行。</span><span class="sxs-lookup"><span data-stu-id="7263a-278">Loop: When time reaches the end of the animation clip, time will continue at the beginning.</span></span> |
| <span data-ttu-id="7263a-279">4</span><span class="sxs-lookup"><span data-stu-id="7263a-279">4</span></span> | <span data-ttu-id="7263a-280">PingPong：當時間達到動畫剪輯的結尾時，時間會在開始與結束時 ping 一次。</span><span class="sxs-lookup"><span data-stu-id="7263a-280">PingPong: When time reaches the end of the animation clip, time will ping pong back between beginning and end.</span></span> |
| <span data-ttu-id="7263a-281">8</span><span class="sxs-lookup"><span data-stu-id="7263a-281">8</span></span> | <span data-ttu-id="7263a-282">ClampForever：播放動畫。</span><span class="sxs-lookup"><span data-stu-id="7263a-282">ClampForever: Plays back the animation.</span></span> <span data-ttu-id="7263a-283">到達結束時，它會繼續播放最後一個畫面格，而且永遠不會停止播放。</span><span class="sxs-lookup"><span data-stu-id="7263a-283">When it reaches the end, it will keep playing the last frame and never stop playing.</span></span> |

### <a name="weighted-mode"></a><span data-ttu-id="7263a-284">加權模式</span><span class="sxs-lookup"><span data-stu-id="7263a-284">Weighted mode</span></span>

<span data-ttu-id="7263a-285">加權模式的語義遵循 [Unity WeightedMode](https://docs.unity3d.com/ScriptReference/WeightedMode.html) 定義。</span><span class="sxs-lookup"><span data-stu-id="7263a-285">The semantics of the Weighted mode follow the [Unity WeightedMode](https://docs.unity3d.com/ScriptReference/WeightedMode.html) definition.</span></span>

| <span data-ttu-id="7263a-286">值</span><span class="sxs-lookup"><span data-stu-id="7263a-286">Value</span></span> | <span data-ttu-id="7263a-287">意義</span><span class="sxs-lookup"><span data-stu-id="7263a-287">Meaning</span></span> |
|-------|---------|
| <span data-ttu-id="7263a-288">0</span><span class="sxs-lookup"><span data-stu-id="7263a-288">0</span></span> | <span data-ttu-id="7263a-289">None：在計算曲線區段時排除 inWeight 或 outWeight。</span><span class="sxs-lookup"><span data-stu-id="7263a-289">None: Exclude both inWeight or outWeight when calculating curve segments.</span></span> |
| <span data-ttu-id="7263a-290">1</span><span class="sxs-lookup"><span data-stu-id="7263a-290">1</span></span> | <span data-ttu-id="7263a-291">在中：在計算上一個曲線區段時包含 inWeight。</span><span class="sxs-lookup"><span data-stu-id="7263a-291">In: Include inWeight when calculating the previous curve segment.</span></span> |
| <span data-ttu-id="7263a-292">2</span><span class="sxs-lookup"><span data-stu-id="7263a-292">2</span></span> | <span data-ttu-id="7263a-293">Out：在計算下一個曲線區段時包含 outWeight。</span><span class="sxs-lookup"><span data-stu-id="7263a-293">Out: Include outWeight when calculating the next curve segment.</span></span> |
| <span data-ttu-id="7263a-294">3</span><span class="sxs-lookup"><span data-stu-id="7263a-294">3</span></span> | <span data-ttu-id="7263a-295">兩者：在計算曲線區段時包含 inWeight 和 outWeight。</span><span class="sxs-lookup"><span data-stu-id="7263a-295">Both: Include inWeight and outWeight when calculating curve segments.</span></span> |
