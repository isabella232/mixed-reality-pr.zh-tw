---
title: InputAnimationFileFormat
description: MRTK 中輸入動畫二進位檔案格式規格的相關檔
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: 25af173b911897bc10e632d0be418c89f01fda6f
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104702414"
---
# <a name="input-animation-binary-file-format-specification"></a><span data-ttu-id="fbb49-104">輸入動畫二進位檔案格式規格</span><span class="sxs-lookup"><span data-stu-id="fbb49-104">Input animation binary file format specification</span></span>

## <a name="overall-structure"></a><span data-ttu-id="fbb49-105">整體結構</span><span class="sxs-lookup"><span data-stu-id="fbb49-105">Overall structure</span></span>

<span data-ttu-id="fbb49-106">輸入動畫二進位檔案的開頭為64位整數魔術數位。</span><span class="sxs-lookup"><span data-stu-id="fbb49-106">The input animation binary file begins with a 64 bit integer magic number.</span></span> <span data-ttu-id="fbb49-107">這個數位的十六進位標記法值是 `0x6a8faf6e0f9e42c6` ，而且可以用來識別有效的輸入動畫檔案。</span><span class="sxs-lookup"><span data-stu-id="fbb49-107">The value of this number in hexadecimal notation is `0x6a8faf6e0f9e42c6` and can be used to identify valid input animation files.</span></span>

<span data-ttu-id="fbb49-108">接下來八個位元組是兩個 Int32 值，用來宣告檔案的主要和次要版本號碼。</span><span class="sxs-lookup"><span data-stu-id="fbb49-108">The next eight bytes are two Int32 values declaring the major and minor version number of the file.</span></span>

<span data-ttu-id="fbb49-109">檔案的其餘部分是由動畫資料所佔用，可能會在版本號碼之間變更。</span><span class="sxs-lookup"><span data-stu-id="fbb49-109">The rest of the file is taken up by animation data, which may change between version numbers.</span></span>

| <span data-ttu-id="fbb49-110">區段</span><span class="sxs-lookup"><span data-stu-id="fbb49-110">Section</span></span> | <span data-ttu-id="fbb49-111">類型</span><span class="sxs-lookup"><span data-stu-id="fbb49-111">Type</span></span> |
|---------|------|
| <span data-ttu-id="fbb49-112">魔術數位</span><span class="sxs-lookup"><span data-stu-id="fbb49-112">Magic Number</span></span> | <span data-ttu-id="fbb49-113">Int64</span><span class="sxs-lookup"><span data-stu-id="fbb49-113">Int64</span></span> |
| <span data-ttu-id="fbb49-114">主要版本號碼</span><span class="sxs-lookup"><span data-stu-id="fbb49-114">Major Version Number</span></span> | <span data-ttu-id="fbb49-115">Int32</span><span class="sxs-lookup"><span data-stu-id="fbb49-115">Int32</span></span> |
| <span data-ttu-id="fbb49-116">次要版本號碼</span><span class="sxs-lookup"><span data-stu-id="fbb49-116">Minor Version Number</span></span> | <span data-ttu-id="fbb49-117">Int32</span><span class="sxs-lookup"><span data-stu-id="fbb49-117">Int32</span></span> |
| <span data-ttu-id="fbb49-118">動畫資料</span><span class="sxs-lookup"><span data-stu-id="fbb49-118">Animation Data</span></span> | <span data-ttu-id="fbb49-119">_請參閱版本區段_</span><span class="sxs-lookup"><span data-stu-id="fbb49-119">_see version section_</span></span> |

## <a name="version-11"></a><span data-ttu-id="fbb49-120">1.1 版</span><span class="sxs-lookup"><span data-stu-id="fbb49-120">Version 1.1</span></span>

<span data-ttu-id="fbb49-121">輸入動畫資料包含三個布林值，指出動畫是否包含相機、手和眼睛等資料，後面接著一連串的動畫曲線。</span><span class="sxs-lookup"><span data-stu-id="fbb49-121">The input animation data consists of three boolean values that indicate whether the animation contains Camera, Hand, and Eye Gaze data, followed by a sequence of animation curves.</span></span> <span data-ttu-id="fbb49-122">出現的曲線取決於這些布林值的值。</span><span class="sxs-lookup"><span data-stu-id="fbb49-122">The curves present depends on the values of these booleans.</span></span> <span data-ttu-id="fbb49-123">每個曲線都可以有不同的主要畫面格數目。</span><span class="sxs-lookup"><span data-stu-id="fbb49-123">Each curve can have a different number of keyframes.</span></span>

| <span data-ttu-id="fbb49-124">區段</span><span class="sxs-lookup"><span data-stu-id="fbb49-124">Section</span></span> | <span data-ttu-id="fbb49-125">類型</span><span class="sxs-lookup"><span data-stu-id="fbb49-125">Type</span></span> | <span data-ttu-id="fbb49-126">注意</span><span class="sxs-lookup"><span data-stu-id="fbb49-126">Notes</span></span> |
|---------|------|------|
| <span data-ttu-id="fbb49-127">有相機姿勢</span><span class="sxs-lookup"><span data-stu-id="fbb49-127">Has Camera Pose</span></span> | <span data-ttu-id="fbb49-128">Boolean</span><span class="sxs-lookup"><span data-stu-id="fbb49-128">Boolean</span></span> | |
| <span data-ttu-id="fbb49-129">有手資料</span><span class="sxs-lookup"><span data-stu-id="fbb49-129">Has Hand Data</span></span> | <span data-ttu-id="fbb49-130">Boolean</span><span class="sxs-lookup"><span data-stu-id="fbb49-130">Boolean</span></span> | |
| <span data-ttu-id="fbb49-131">具有眼睛</span><span class="sxs-lookup"><span data-stu-id="fbb49-131">Has Eye Gaze</span></span>| <span data-ttu-id="fbb49-132">Boolean</span><span class="sxs-lookup"><span data-stu-id="fbb49-132">Boolean</span></span> | |
| <span data-ttu-id="fbb49-133">相機</span><span class="sxs-lookup"><span data-stu-id="fbb49-133">Camera</span></span> | [<span data-ttu-id="fbb49-134">姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="fbb49-134">Pose Curves</span></span>](#pose-curves) | <span data-ttu-id="fbb49-135">只有當攝影機姿勢為 true 時</span><span class="sxs-lookup"><span data-stu-id="fbb49-135">Only if Has Camera Pose is true</span></span> |
| <span data-ttu-id="fbb49-136">靠右追蹤</span><span class="sxs-lookup"><span data-stu-id="fbb49-136">Hand Tracked Left</span></span> | [<span data-ttu-id="fbb49-137">布林曲線</span><span class="sxs-lookup"><span data-stu-id="fbb49-137">Boolean Curve</span></span>](#boolean-curve) | <span data-ttu-id="fbb49-138">只有在有手資料為 true 時</span><span class="sxs-lookup"><span data-stu-id="fbb49-138">Only if Has Hand Data is true</span></span> |
| <span data-ttu-id="fbb49-139">右側追蹤</span><span class="sxs-lookup"><span data-stu-id="fbb49-139">Hand Tracked Right</span></span> | [<span data-ttu-id="fbb49-140">布林曲線</span><span class="sxs-lookup"><span data-stu-id="fbb49-140">Boolean Curve</span></span>](#boolean-curve) | <span data-ttu-id="fbb49-141">只有在有手資料為 true 時</span><span class="sxs-lookup"><span data-stu-id="fbb49-141">Only if Has Hand Data is true</span></span> |
| <span data-ttu-id="fbb49-142">向左捏合手</span><span class="sxs-lookup"><span data-stu-id="fbb49-142">Hand Pinching Left</span></span> | [<span data-ttu-id="fbb49-143">布林曲線</span><span class="sxs-lookup"><span data-stu-id="fbb49-143">Boolean Curve</span></span>](#boolean-curve) | <span data-ttu-id="fbb49-144">只有在有手資料為 true 時</span><span class="sxs-lookup"><span data-stu-id="fbb49-144">Only if Has Hand Data is true</span></span> |
| <span data-ttu-id="fbb49-145">右手捏合 Right</span><span class="sxs-lookup"><span data-stu-id="fbb49-145">Hand Pinching Right</span></span> | [<span data-ttu-id="fbb49-146">布林曲線</span><span class="sxs-lookup"><span data-stu-id="fbb49-146">Boolean Curve</span></span>](#boolean-curve) | <span data-ttu-id="fbb49-147">只有在有手資料為 true 時</span><span class="sxs-lookup"><span data-stu-id="fbb49-147">Only if Has Hand Data is true</span></span> |
| <span data-ttu-id="fbb49-148">左邊的接點</span><span class="sxs-lookup"><span data-stu-id="fbb49-148">Hand Joints Left</span></span> | [<span data-ttu-id="fbb49-149">聯合姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="fbb49-149">Joint Pose Curves</span></span>](#joint-pose-curves) | <span data-ttu-id="fbb49-150">只有在有手資料為 true 時</span><span class="sxs-lookup"><span data-stu-id="fbb49-150">Only if Has Hand Data is true</span></span> |
| <span data-ttu-id="fbb49-151">右邊</span><span class="sxs-lookup"><span data-stu-id="fbb49-151">Hand Joints Right</span></span> | [<span data-ttu-id="fbb49-152">聯合姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="fbb49-152">Joint Pose Curves</span></span>](#joint-pose-curves) | <span data-ttu-id="fbb49-153">只有在有手資料為 true 時</span><span class="sxs-lookup"><span data-stu-id="fbb49-153">Only if Has Hand Data is true</span></span> |
| <span data-ttu-id="fbb49-154">眼睛</span><span class="sxs-lookup"><span data-stu-id="fbb49-154">Eye Gaze</span></span> | <span data-ttu-id="fbb49-155">[光線曲線](#ray-curves)]</span><span class="sxs-lookup"><span data-stu-id="fbb49-155">[Ray Curves](#ray-curves)]</span></span> | <span data-ttu-id="fbb49-156">只有當眼睛為 true 時</span><span class="sxs-lookup"><span data-stu-id="fbb49-156">Only if Has Eye Gaze is true</span></span> |

## <a name="version-10"></a><span data-ttu-id="fbb49-157">版本 1.0</span><span class="sxs-lookup"><span data-stu-id="fbb49-157">Version 1.0</span></span>

<span data-ttu-id="fbb49-158">輸入動畫資料包含一連串的動畫曲線。</span><span class="sxs-lookup"><span data-stu-id="fbb49-158">The input animation data consists of a sequence of animation curves.</span></span> <span data-ttu-id="fbb49-159">動畫曲線的數目和意義是固定的，但每個曲線都可以有不同的主要畫面格數目。</span><span class="sxs-lookup"><span data-stu-id="fbb49-159">The number and meaning of animation curves is fixed, but each curve can have a different number of keyframes.</span></span>

| <span data-ttu-id="fbb49-160">區段</span><span class="sxs-lookup"><span data-stu-id="fbb49-160">Section</span></span> | <span data-ttu-id="fbb49-161">類型</span><span class="sxs-lookup"><span data-stu-id="fbb49-161">Type</span></span> |
|---------|------|
| <span data-ttu-id="fbb49-162">相機</span><span class="sxs-lookup"><span data-stu-id="fbb49-162">Camera</span></span> | [<span data-ttu-id="fbb49-163">姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="fbb49-163">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="fbb49-164">靠右追蹤</span><span class="sxs-lookup"><span data-stu-id="fbb49-164">Hand Tracked Left</span></span> | [<span data-ttu-id="fbb49-165">布林曲線</span><span class="sxs-lookup"><span data-stu-id="fbb49-165">Boolean Curve</span></span>](#boolean-curve) |
| <span data-ttu-id="fbb49-166">右側追蹤</span><span class="sxs-lookup"><span data-stu-id="fbb49-166">Hand Tracked Right</span></span> | [<span data-ttu-id="fbb49-167">布林曲線</span><span class="sxs-lookup"><span data-stu-id="fbb49-167">Boolean Curve</span></span>](#boolean-curve) |
| <span data-ttu-id="fbb49-168">向左捏合手</span><span class="sxs-lookup"><span data-stu-id="fbb49-168">Hand Pinching Left</span></span> | [<span data-ttu-id="fbb49-169">布林曲線</span><span class="sxs-lookup"><span data-stu-id="fbb49-169">Boolean Curve</span></span>](#boolean-curve) |
| <span data-ttu-id="fbb49-170">右手捏合 Right</span><span class="sxs-lookup"><span data-stu-id="fbb49-170">Hand Pinching Right</span></span> | [<span data-ttu-id="fbb49-171">布林曲線</span><span class="sxs-lookup"><span data-stu-id="fbb49-171">Boolean Curve</span></span>](#boolean-curve) |
| <span data-ttu-id="fbb49-172">左邊的接點</span><span class="sxs-lookup"><span data-stu-id="fbb49-172">Hand Joints Left</span></span> | [<span data-ttu-id="fbb49-173">聯合姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="fbb49-173">Joint Pose Curves</span></span>](#joint-pose-curves) |
| <span data-ttu-id="fbb49-174">右邊</span><span class="sxs-lookup"><span data-stu-id="fbb49-174">Hand Joints Right</span></span> | [<span data-ttu-id="fbb49-175">聯合姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="fbb49-175">Joint Pose Curves</span></span>](#joint-pose-curves) |

### <a name="joint-pose-curves"></a><span data-ttu-id="fbb49-176">聯合姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="fbb49-176">Joint pose curves</span></span>

<span data-ttu-id="fbb49-177">每次都會儲存一連串的聯合動畫曲線。</span><span class="sxs-lookup"><span data-stu-id="fbb49-177">For each hand a sequence of joint animation curves is stored.</span></span> <span data-ttu-id="fbb49-178">接點的數目是固定的，而且會針對每個聯合儲存一組姿勢曲線。</span><span class="sxs-lookup"><span data-stu-id="fbb49-178">The number of joints is fixed, and a set of pose curves is stored for each joint.</span></span>

| <span data-ttu-id="fbb49-179">區段</span><span class="sxs-lookup"><span data-stu-id="fbb49-179">Section</span></span> | <span data-ttu-id="fbb49-180">類型</span><span class="sxs-lookup"><span data-stu-id="fbb49-180">Type</span></span> |
|---------|------|
| <span data-ttu-id="fbb49-181">無</span><span class="sxs-lookup"><span data-stu-id="fbb49-181">None</span></span> | [<span data-ttu-id="fbb49-182">姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="fbb49-182">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="fbb49-183">手腕</span><span class="sxs-lookup"><span data-stu-id="fbb49-183">Wrist</span></span> | [<span data-ttu-id="fbb49-184">姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="fbb49-184">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="fbb49-185">Palm</span><span class="sxs-lookup"><span data-stu-id="fbb49-185">Palm</span></span> | [<span data-ttu-id="fbb49-186">姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="fbb49-186">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="fbb49-187">ThumbMetacarpalJoint</span><span class="sxs-lookup"><span data-stu-id="fbb49-187">ThumbMetacarpalJoint</span></span> | [<span data-ttu-id="fbb49-188">姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="fbb49-188">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="fbb49-189">ThumbProximalJoint</span><span class="sxs-lookup"><span data-stu-id="fbb49-189">ThumbProximalJoint</span></span> | [<span data-ttu-id="fbb49-190">姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="fbb49-190">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="fbb49-191">ThumbDistalJoint</span><span class="sxs-lookup"><span data-stu-id="fbb49-191">ThumbDistalJoint</span></span> | [<span data-ttu-id="fbb49-192">姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="fbb49-192">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="fbb49-193">ThumbTip</span><span class="sxs-lookup"><span data-stu-id="fbb49-193">ThumbTip</span></span> | [<span data-ttu-id="fbb49-194">姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="fbb49-194">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="fbb49-195">IndexMetacarpal</span><span class="sxs-lookup"><span data-stu-id="fbb49-195">IndexMetacarpal</span></span> | [<span data-ttu-id="fbb49-196">姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="fbb49-196">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="fbb49-197">IndexKnuckle</span><span class="sxs-lookup"><span data-stu-id="fbb49-197">IndexKnuckle</span></span> | [<span data-ttu-id="fbb49-198">姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="fbb49-198">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="fbb49-199">IndexMiddleJoint</span><span class="sxs-lookup"><span data-stu-id="fbb49-199">IndexMiddleJoint</span></span> | [<span data-ttu-id="fbb49-200">姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="fbb49-200">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="fbb49-201">IndexDistalJoint</span><span class="sxs-lookup"><span data-stu-id="fbb49-201">IndexDistalJoint</span></span> | [<span data-ttu-id="fbb49-202">姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="fbb49-202">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="fbb49-203">IndexTip</span><span class="sxs-lookup"><span data-stu-id="fbb49-203">IndexTip</span></span> | [<span data-ttu-id="fbb49-204">姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="fbb49-204">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="fbb49-205">MiddleMetacarpal</span><span class="sxs-lookup"><span data-stu-id="fbb49-205">MiddleMetacarpal</span></span> | [<span data-ttu-id="fbb49-206">姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="fbb49-206">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="fbb49-207">MiddleKnuckle</span><span class="sxs-lookup"><span data-stu-id="fbb49-207">MiddleKnuckle</span></span> | [<span data-ttu-id="fbb49-208">姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="fbb49-208">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="fbb49-209">MiddleMiddleJoint</span><span class="sxs-lookup"><span data-stu-id="fbb49-209">MiddleMiddleJoint</span></span> | [<span data-ttu-id="fbb49-210">姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="fbb49-210">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="fbb49-211">MiddleDistalJoint</span><span class="sxs-lookup"><span data-stu-id="fbb49-211">MiddleDistalJoint</span></span> | [<span data-ttu-id="fbb49-212">姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="fbb49-212">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="fbb49-213">MiddleTip</span><span class="sxs-lookup"><span data-stu-id="fbb49-213">MiddleTip</span></span> | [<span data-ttu-id="fbb49-214">姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="fbb49-214">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="fbb49-215">RingMetacarpal</span><span class="sxs-lookup"><span data-stu-id="fbb49-215">RingMetacarpal</span></span> | [<span data-ttu-id="fbb49-216">姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="fbb49-216">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="fbb49-217">RingKnuckle</span><span class="sxs-lookup"><span data-stu-id="fbb49-217">RingKnuckle</span></span> | [<span data-ttu-id="fbb49-218">姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="fbb49-218">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="fbb49-219">RingMiddleJoint</span><span class="sxs-lookup"><span data-stu-id="fbb49-219">RingMiddleJoint</span></span> | [<span data-ttu-id="fbb49-220">姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="fbb49-220">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="fbb49-221">RingDistalJoint</span><span class="sxs-lookup"><span data-stu-id="fbb49-221">RingDistalJoint</span></span> | [<span data-ttu-id="fbb49-222">姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="fbb49-222">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="fbb49-223">RingTip</span><span class="sxs-lookup"><span data-stu-id="fbb49-223">RingTip</span></span> | [<span data-ttu-id="fbb49-224">姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="fbb49-224">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="fbb49-225">PinkyMetacarpal</span><span class="sxs-lookup"><span data-stu-id="fbb49-225">PinkyMetacarpal</span></span> | [<span data-ttu-id="fbb49-226">姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="fbb49-226">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="fbb49-227">PinkyKnuckle</span><span class="sxs-lookup"><span data-stu-id="fbb49-227">PinkyKnuckle</span></span> | [<span data-ttu-id="fbb49-228">姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="fbb49-228">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="fbb49-229">PinkyMiddleJoint</span><span class="sxs-lookup"><span data-stu-id="fbb49-229">PinkyMiddleJoint</span></span> | [<span data-ttu-id="fbb49-230">姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="fbb49-230">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="fbb49-231">PinkyDistalJoint</span><span class="sxs-lookup"><span data-stu-id="fbb49-231">PinkyDistalJoint</span></span> | [<span data-ttu-id="fbb49-232">姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="fbb49-232">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="fbb49-233">PinkyTip</span><span class="sxs-lookup"><span data-stu-id="fbb49-233">PinkyTip</span></span> | [<span data-ttu-id="fbb49-234">姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="fbb49-234">Pose Curves</span></span>](#pose-curves) |

### <a name="pose-curves"></a><span data-ttu-id="fbb49-235">姿勢曲線</span><span class="sxs-lookup"><span data-stu-id="fbb49-235">Pose curves</span></span>

<span data-ttu-id="fbb49-236">姿勢曲線是位置向量的三個動畫曲線序列，後面接著4個旋轉四元數的動畫曲線。</span><span class="sxs-lookup"><span data-stu-id="fbb49-236">Pose curves are a sequence of 3 animation curves for the position vector, followed by 4 animation curves for the rotation quaternion.</span></span>

| <span data-ttu-id="fbb49-237">區段</span><span class="sxs-lookup"><span data-stu-id="fbb49-237">Section</span></span> | <span data-ttu-id="fbb49-238">類型</span><span class="sxs-lookup"><span data-stu-id="fbb49-238">Type</span></span> |
|---------|------|
| <span data-ttu-id="fbb49-239">位置 X</span><span class="sxs-lookup"><span data-stu-id="fbb49-239">Position X</span></span> | [<span data-ttu-id="fbb49-240">浮點數曲線</span><span class="sxs-lookup"><span data-stu-id="fbb49-240">Float Curve</span></span>](#float-curve) |
| <span data-ttu-id="fbb49-241">位置 Y</span><span class="sxs-lookup"><span data-stu-id="fbb49-241">Position Y</span></span> | [<span data-ttu-id="fbb49-242">浮點數曲線</span><span class="sxs-lookup"><span data-stu-id="fbb49-242">Float Curve</span></span>](#float-curve) |
| <span data-ttu-id="fbb49-243">位置 Z</span><span class="sxs-lookup"><span data-stu-id="fbb49-243">Position Z</span></span> | [<span data-ttu-id="fbb49-244">浮點數曲線</span><span class="sxs-lookup"><span data-stu-id="fbb49-244">Float Curve</span></span>](#float-curve) |
| <span data-ttu-id="fbb49-245">旋轉 X</span><span class="sxs-lookup"><span data-stu-id="fbb49-245">Rotation X</span></span> | [<span data-ttu-id="fbb49-246">浮點數曲線</span><span class="sxs-lookup"><span data-stu-id="fbb49-246">Float Curve</span></span>](#float-curve) |
| <span data-ttu-id="fbb49-247">旋轉 Y</span><span class="sxs-lookup"><span data-stu-id="fbb49-247">Rotation Y</span></span> | [<span data-ttu-id="fbb49-248">浮點數曲線</span><span class="sxs-lookup"><span data-stu-id="fbb49-248">Float Curve</span></span>](#float-curve) |
| <span data-ttu-id="fbb49-249">旋轉 Z</span><span class="sxs-lookup"><span data-stu-id="fbb49-249">Rotation Z</span></span> | [<span data-ttu-id="fbb49-250">浮點數曲線</span><span class="sxs-lookup"><span data-stu-id="fbb49-250">Float Curve</span></span>](#float-curve) |
| <span data-ttu-id="fbb49-251">旋轉 W</span><span class="sxs-lookup"><span data-stu-id="fbb49-251">Rotation W</span></span> | [<span data-ttu-id="fbb49-252">浮點數曲線</span><span class="sxs-lookup"><span data-stu-id="fbb49-252">Float Curve</span></span>](#float-curve) |

### <a name="ray-curves"></a><span data-ttu-id="fbb49-253">光線曲線</span><span class="sxs-lookup"><span data-stu-id="fbb49-253">Ray curves</span></span>

<span data-ttu-id="fbb49-254">光線曲線是原點向量的三個動畫曲線序列，後面接著三個方向向量的動畫曲線。</span><span class="sxs-lookup"><span data-stu-id="fbb49-254">Ray curves are a sequence of 3 animation curves for the origin vector, followed by 3 animation curves for the direction vector.</span></span>

| <span data-ttu-id="fbb49-255">區段</span><span class="sxs-lookup"><span data-stu-id="fbb49-255">Section</span></span> | <span data-ttu-id="fbb49-256">類型</span><span class="sxs-lookup"><span data-stu-id="fbb49-256">Type</span></span> |
|---------|------|
| <span data-ttu-id="fbb49-257">原始 X</span><span class="sxs-lookup"><span data-stu-id="fbb49-257">Origin X</span></span> | [<span data-ttu-id="fbb49-258">浮點數曲線</span><span class="sxs-lookup"><span data-stu-id="fbb49-258">Float Curve</span></span>](#float-curve) |
| <span data-ttu-id="fbb49-259">原點 Y</span><span class="sxs-lookup"><span data-stu-id="fbb49-259">Origin Y</span></span> | [<span data-ttu-id="fbb49-260">浮點數曲線</span><span class="sxs-lookup"><span data-stu-id="fbb49-260">Float Curve</span></span>](#float-curve) |
| <span data-ttu-id="fbb49-261">原點 Z</span><span class="sxs-lookup"><span data-stu-id="fbb49-261">Origin Z</span></span> | [<span data-ttu-id="fbb49-262">浮點數曲線</span><span class="sxs-lookup"><span data-stu-id="fbb49-262">Float Curve</span></span>](#float-curve) |
| <span data-ttu-id="fbb49-263">方向 X</span><span class="sxs-lookup"><span data-stu-id="fbb49-263">Direction X</span></span> | [<span data-ttu-id="fbb49-264">浮點數曲線</span><span class="sxs-lookup"><span data-stu-id="fbb49-264">Float Curve</span></span>](#float-curve) |
| <span data-ttu-id="fbb49-265">方向 Y</span><span class="sxs-lookup"><span data-stu-id="fbb49-265">Direction Y</span></span> | [<span data-ttu-id="fbb49-266">浮點數曲線</span><span class="sxs-lookup"><span data-stu-id="fbb49-266">Float Curve</span></span>](#float-curve) |
| <span data-ttu-id="fbb49-267">方向 Z</span><span class="sxs-lookup"><span data-stu-id="fbb49-267">Direction Z</span></span> | [<span data-ttu-id="fbb49-268">浮點數曲線</span><span class="sxs-lookup"><span data-stu-id="fbb49-268">Float Curve</span></span>](#float-curve) |

### <a name="float-curve"></a><span data-ttu-id="fbb49-269">浮點數曲線</span><span class="sxs-lookup"><span data-stu-id="fbb49-269">Float curve</span></span>

<span data-ttu-id="fbb49-270">浮點數曲線是具有不定數目之主要畫面格的完備貝茲曲線。</span><span class="sxs-lookup"><span data-stu-id="fbb49-270">Floating point curves are fully fledged Bézier curves with a variable number of keyframes.</span></span> <span data-ttu-id="fbb49-271">每個主要畫面格都會儲存時間和曲線值，以及每個主要畫面格左右側邊的正切和加權。</span><span class="sxs-lookup"><span data-stu-id="fbb49-271">Each keyframe stores a time and a curve value, as well as tangents and weights on the left and right side of each keyframe.</span></span>

| <span data-ttu-id="fbb49-272">區段</span><span class="sxs-lookup"><span data-stu-id="fbb49-272">Section</span></span> | <span data-ttu-id="fbb49-273">類型</span><span class="sxs-lookup"><span data-stu-id="fbb49-273">Type</span></span> |
|---------|------|
| <span data-ttu-id="fbb49-274">預先換行模式</span><span class="sxs-lookup"><span data-stu-id="fbb49-274">Pre-Wrap Mode</span></span> | <span data-ttu-id="fbb49-275">Int32、 [Wrap 模式](#wrap-mode)</span><span class="sxs-lookup"><span data-stu-id="fbb49-275">Int32, [Wrap Mode](#wrap-mode)</span></span> |
| <span data-ttu-id="fbb49-276">後置換行模式</span><span class="sxs-lookup"><span data-stu-id="fbb49-276">Post-Wrap Mode</span></span> | <span data-ttu-id="fbb49-277">Int32、 [Wrap 模式](#wrap-mode)</span><span class="sxs-lookup"><span data-stu-id="fbb49-277">Int32, [Wrap Mode](#wrap-mode)</span></span> |
| <span data-ttu-id="fbb49-278">關鍵畫面數</span><span class="sxs-lookup"><span data-stu-id="fbb49-278">Number of keyframes</span></span> | <span data-ttu-id="fbb49-279">Int32</span><span class="sxs-lookup"><span data-stu-id="fbb49-279">Int32</span></span> |
| <span data-ttu-id="fbb49-280">關鍵 幀</span><span class="sxs-lookup"><span data-stu-id="fbb49-280">Keyframes</span></span> | [<span data-ttu-id="fbb49-281">Float 主要畫面格</span><span class="sxs-lookup"><span data-stu-id="fbb49-281">Float Keyframe</span></span>](#float-keyframe) |

### <a name="float-keyframe"></a><span data-ttu-id="fbb49-282">Float 主要畫面格</span><span class="sxs-lookup"><span data-stu-id="fbb49-282">Float keyframe</span></span>

<span data-ttu-id="fbb49-283">Float 主要畫面格會在基本時間和值的旁邊儲存正切值和加權值。</span><span class="sxs-lookup"><span data-stu-id="fbb49-283">A float keyframe stores tangent and weight values alongside the basic time and value.</span></span>

| <span data-ttu-id="fbb49-284">區段</span><span class="sxs-lookup"><span data-stu-id="fbb49-284">Section</span></span> | <span data-ttu-id="fbb49-285">類型</span><span class="sxs-lookup"><span data-stu-id="fbb49-285">Type</span></span> |
|---------|------|
| <span data-ttu-id="fbb49-286">Time</span><span class="sxs-lookup"><span data-stu-id="fbb49-286">Time</span></span> | <span data-ttu-id="fbb49-287">Float32</span><span class="sxs-lookup"><span data-stu-id="fbb49-287">Float32</span></span> |
| <span data-ttu-id="fbb49-288">值</span><span class="sxs-lookup"><span data-stu-id="fbb49-288">Value</span></span> | <span data-ttu-id="fbb49-289">Float32</span><span class="sxs-lookup"><span data-stu-id="fbb49-289">Float32</span></span> |
| <span data-ttu-id="fbb49-290">InTangent</span><span class="sxs-lookup"><span data-stu-id="fbb49-290">InTangent</span></span> | <span data-ttu-id="fbb49-291">Float32</span><span class="sxs-lookup"><span data-stu-id="fbb49-291">Float32</span></span> |
| <span data-ttu-id="fbb49-292">OutTangent</span><span class="sxs-lookup"><span data-stu-id="fbb49-292">OutTangent</span></span> | <span data-ttu-id="fbb49-293">Float32</span><span class="sxs-lookup"><span data-stu-id="fbb49-293">Float32</span></span> |
| <span data-ttu-id="fbb49-294">InWeight</span><span class="sxs-lookup"><span data-stu-id="fbb49-294">InWeight</span></span> | <span data-ttu-id="fbb49-295">Float32</span><span class="sxs-lookup"><span data-stu-id="fbb49-295">Float32</span></span> |
| <span data-ttu-id="fbb49-296">OutWeight</span><span class="sxs-lookup"><span data-stu-id="fbb49-296">OutWeight</span></span> | <span data-ttu-id="fbb49-297">Float32</span><span class="sxs-lookup"><span data-stu-id="fbb49-297">Float32</span></span> |
| <span data-ttu-id="fbb49-298">WeightedMode</span><span class="sxs-lookup"><span data-stu-id="fbb49-298">WeightedMode</span></span> | <span data-ttu-id="fbb49-299">Int32、 [加權模式](#weighted-mode)</span><span class="sxs-lookup"><span data-stu-id="fbb49-299">Int32, [Weighted Mode](#weighted-mode)</span></span> |

### <a name="boolean-curve"></a><span data-ttu-id="fbb49-300">布林曲線</span><span class="sxs-lookup"><span data-stu-id="fbb49-300">Boolean curve</span></span>

<span data-ttu-id="fbb49-301">布林曲線是開啟/關閉值的簡單序列。</span><span class="sxs-lookup"><span data-stu-id="fbb49-301">Boolean curves are simple sequences of on/off values.</span></span> <span data-ttu-id="fbb49-302">在每個主要畫面上，曲線的值會立即翻轉。</span><span class="sxs-lookup"><span data-stu-id="fbb49-302">On every keyframe the value of the curve flips immediately.</span></span>

| <span data-ttu-id="fbb49-303">區段</span><span class="sxs-lookup"><span data-stu-id="fbb49-303">Section</span></span> | <span data-ttu-id="fbb49-304">類型</span><span class="sxs-lookup"><span data-stu-id="fbb49-304">Type</span></span> |
|---------|------|
| <span data-ttu-id="fbb49-305">預先換行模式</span><span class="sxs-lookup"><span data-stu-id="fbb49-305">Pre-Wrap Mode</span></span> | <span data-ttu-id="fbb49-306">Int32、 [Wrap 模式](#wrap-mode)</span><span class="sxs-lookup"><span data-stu-id="fbb49-306">Int32, [Wrap Mode](#wrap-mode)</span></span> |
| <span data-ttu-id="fbb49-307">後置換行模式</span><span class="sxs-lookup"><span data-stu-id="fbb49-307">Post-Wrap Mode</span></span> | <span data-ttu-id="fbb49-308">Int32、 [Wrap 模式](#wrap-mode)</span><span class="sxs-lookup"><span data-stu-id="fbb49-308">Int32, [Wrap Mode](#wrap-mode)</span></span> |
| <span data-ttu-id="fbb49-309">關鍵畫面數</span><span class="sxs-lookup"><span data-stu-id="fbb49-309">Number of keyframes</span></span> | <span data-ttu-id="fbb49-310">Int32</span><span class="sxs-lookup"><span data-stu-id="fbb49-310">Int32</span></span> |
| <span data-ttu-id="fbb49-311">關鍵 幀</span><span class="sxs-lookup"><span data-stu-id="fbb49-311">Keyframes</span></span> | [<span data-ttu-id="fbb49-312">布林主要畫面格</span><span class="sxs-lookup"><span data-stu-id="fbb49-312">Boolean Keyframe</span></span>](#boolean-keyframe) |

### <a name="boolean-keyframe"></a><span data-ttu-id="fbb49-313">布林主要畫面格</span><span class="sxs-lookup"><span data-stu-id="fbb49-313">Boolean keyframe</span></span>

<span data-ttu-id="fbb49-314">布林值主要畫面格只會儲存時間和值。</span><span class="sxs-lookup"><span data-stu-id="fbb49-314">A boolean keyframe only stores a time and value.</span></span>

| <span data-ttu-id="fbb49-315">區段</span><span class="sxs-lookup"><span data-stu-id="fbb49-315">Section</span></span> | <span data-ttu-id="fbb49-316">類型</span><span class="sxs-lookup"><span data-stu-id="fbb49-316">Type</span></span> |
|---------|------|
| <span data-ttu-id="fbb49-317">Time</span><span class="sxs-lookup"><span data-stu-id="fbb49-317">Time</span></span> | <span data-ttu-id="fbb49-318">Float32</span><span class="sxs-lookup"><span data-stu-id="fbb49-318">Float32</span></span> |
| <span data-ttu-id="fbb49-319">值</span><span class="sxs-lookup"><span data-stu-id="fbb49-319">Value</span></span> | <span data-ttu-id="fbb49-320">Float32</span><span class="sxs-lookup"><span data-stu-id="fbb49-320">Float32</span></span> |

### <a name="wrap-mode"></a><span data-ttu-id="fbb49-321">Wrap 模式</span><span class="sxs-lookup"><span data-stu-id="fbb49-321">Wrap mode</span></span>

<span data-ttu-id="fbb49-322">前置和後置換行模式的語法遵循 [Unity WrapMode](https://docs.unity3d.com/ScriptReference/WrapMode.html) 定義。</span><span class="sxs-lookup"><span data-stu-id="fbb49-322">The semantics of Pre- and Post-Wrap modes follow the [Unity WrapMode](https://docs.unity3d.com/ScriptReference/WrapMode.html) definition.</span></span> <span data-ttu-id="fbb49-323">它們是下列位的組合：</span><span class="sxs-lookup"><span data-stu-id="fbb49-323">They are a combination of the following bits:</span></span>

| <span data-ttu-id="fbb49-324">值</span><span class="sxs-lookup"><span data-stu-id="fbb49-324">Value</span></span> | <span data-ttu-id="fbb49-325">意義</span><span class="sxs-lookup"><span data-stu-id="fbb49-325">Meaning</span></span> |
|-------|---------|
| <span data-ttu-id="fbb49-326">0</span><span class="sxs-lookup"><span data-stu-id="fbb49-326">0</span></span> | <span data-ttu-id="fbb49-327">預設值：讀取設定為較高的預設重複模式。</span><span class="sxs-lookup"><span data-stu-id="fbb49-327">Default: Reads the default repeat mode set higher up.</span></span> |
| <span data-ttu-id="fbb49-328">1</span><span class="sxs-lookup"><span data-stu-id="fbb49-328">1</span></span> | <span data-ttu-id="fbb49-329">一次：當時間到達動畫剪輯的結尾時，剪輯將會自動停止播放，而時間將會重設為剪輯的開頭。</span><span class="sxs-lookup"><span data-stu-id="fbb49-329">Once: When time reaches the end of the animation clip, the clip will automatically stop playing and time will be reset to beginning of the clip.</span></span> |
| <span data-ttu-id="fbb49-330">2</span><span class="sxs-lookup"><span data-stu-id="fbb49-330">2</span></span> | <span data-ttu-id="fbb49-331">Loop：當時間達到動畫剪輯的結尾時，時間會在一開始就繼續進行。</span><span class="sxs-lookup"><span data-stu-id="fbb49-331">Loop: When time reaches the end of the animation clip, time will continue at the beginning.</span></span> |
| <span data-ttu-id="fbb49-332">4</span><span class="sxs-lookup"><span data-stu-id="fbb49-332">4</span></span> | <span data-ttu-id="fbb49-333">PingPong：當時間達到動畫剪輯的結尾時，時間會在開始與結束時 ping 一次。</span><span class="sxs-lookup"><span data-stu-id="fbb49-333">PingPong: When time reaches the end of the animation clip, time will ping pong back between beginning and end.</span></span> |
| <span data-ttu-id="fbb49-334">8</span><span class="sxs-lookup"><span data-stu-id="fbb49-334">8</span></span> | <span data-ttu-id="fbb49-335">ClampForever：播放動畫。</span><span class="sxs-lookup"><span data-stu-id="fbb49-335">ClampForever: Plays back the animation.</span></span> <span data-ttu-id="fbb49-336">到達結束時，它會繼續播放最後一個畫面格，而且永遠不會停止播放。</span><span class="sxs-lookup"><span data-stu-id="fbb49-336">When it reaches the end, it will keep playing the last frame and never stop playing.</span></span> |

### <a name="weighted-mode"></a><span data-ttu-id="fbb49-337">加權模式</span><span class="sxs-lookup"><span data-stu-id="fbb49-337">Weighted mode</span></span>

<span data-ttu-id="fbb49-338">加權模式的語義遵循 [Unity WeightedMode](https://docs.unity3d.com/ScriptReference/WeightedMode.html) 定義。</span><span class="sxs-lookup"><span data-stu-id="fbb49-338">The semantics of the Weighted mode follow the [Unity WeightedMode](https://docs.unity3d.com/ScriptReference/WeightedMode.html) definition.</span></span>

| <span data-ttu-id="fbb49-339">值</span><span class="sxs-lookup"><span data-stu-id="fbb49-339">Value</span></span> | <span data-ttu-id="fbb49-340">意義</span><span class="sxs-lookup"><span data-stu-id="fbb49-340">Meaning</span></span> |
|-------|---------|
| <span data-ttu-id="fbb49-341">0</span><span class="sxs-lookup"><span data-stu-id="fbb49-341">0</span></span> | <span data-ttu-id="fbb49-342">None：在計算曲線區段時排除 inWeight 或 outWeight。</span><span class="sxs-lookup"><span data-stu-id="fbb49-342">None: Exclude both inWeight or outWeight when calculating curve segments.</span></span> |
| <span data-ttu-id="fbb49-343">1</span><span class="sxs-lookup"><span data-stu-id="fbb49-343">1</span></span> | <span data-ttu-id="fbb49-344">在中：在計算上一個曲線區段時包含 inWeight。</span><span class="sxs-lookup"><span data-stu-id="fbb49-344">In: Include inWeight when calculating the previous curve segment.</span></span> |
| <span data-ttu-id="fbb49-345">2</span><span class="sxs-lookup"><span data-stu-id="fbb49-345">2</span></span> | <span data-ttu-id="fbb49-346">Out：在計算下一個曲線區段時包含 outWeight。</span><span class="sxs-lookup"><span data-stu-id="fbb49-346">Out: Include outWeight when calculating the next curve segment.</span></span> |
| <span data-ttu-id="fbb49-347">3</span><span class="sxs-lookup"><span data-stu-id="fbb49-347">3</span></span> | <span data-ttu-id="fbb49-348">兩者：在計算曲線區段時包含 inWeight 和 outWeight。</span><span class="sxs-lookup"><span data-stu-id="fbb49-348">Both: Include inWeight and outWeight when calculating curve segments.</span></span> |
