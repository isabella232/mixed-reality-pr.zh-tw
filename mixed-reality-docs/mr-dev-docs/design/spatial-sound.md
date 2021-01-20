---
title: 混合現實的音效
description: 混合現實中的音訊可以提高 UI 互動的使用者信心，並 immerse 使用者體驗。
author: kegodin
ms.author: v-hferrone
ms.date: 11/07/2019
ms.topic: article
keywords: 空間音效、環繞音效、3d 音訊、3d 音效、空間音訊、混合現實耳機、windows mixed reality 耳機、虛擬實境耳機、HoloLens、MRTK、混合現實工具組、個案研究、聲場
ms.openlocfilehash: 335ff8acf036591bbbf9868f591ca2c3cef1386c
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583256"
---
# <a name="audio-in-mixed-reality"></a><span data-ttu-id="ea704-104">混合現實的音效</span><span class="sxs-lookup"><span data-stu-id="ea704-104">Audio in mixed reality</span></span>

<span data-ttu-id="ea704-105">音訊是設計和生產力在混合現實中不可或缺的一部分。</span><span class="sxs-lookup"><span data-stu-id="ea704-105">Audio is an essential part of design and productivity in mixed reality.</span></span> <span data-ttu-id="ea704-106">音效可以：</span><span class="sxs-lookup"><span data-stu-id="ea704-106">Sound can:</span></span>
* <span data-ttu-id="ea704-107">提高筆勢和語音互動的使用者信賴度。</span><span class="sxs-lookup"><span data-stu-id="ea704-107">Increase user confidence in gesture and voice interactions.</span></span>
* <span data-ttu-id="ea704-108">引導使用者進行後續步驟。</span><span class="sxs-lookup"><span data-stu-id="ea704-108">Guide users to next steps.</span></span>
* <span data-ttu-id="ea704-109">有效地結合虛擬物件與真實世界。</span><span class="sxs-lookup"><span data-stu-id="ea704-109">Effectively combine virtual objects with the real world.</span></span>

<span data-ttu-id="ea704-110">混合現實耳機的低延遲 head 追蹤（包括 HoloLens）支援高品質的 HRTF 型 spatialization。</span><span class="sxs-lookup"><span data-stu-id="ea704-110">The low-latency head tracking of mixed reality headsets, including HoloLens, supports high-quality HRTF-based spatialization.</span></span> <span data-ttu-id="ea704-111">您可以在應用程式中 spatialize 音訊，以：</span><span class="sxs-lookup"><span data-stu-id="ea704-111">You can spatialize audio in your application to:</span></span>
* <span data-ttu-id="ea704-112">注意視覺元素。</span><span class="sxs-lookup"><span data-stu-id="ea704-112">Call attention to visual elements.</span></span>
* <span data-ttu-id="ea704-113">協助使用者維護其真實世界周圍的認知。</span><span class="sxs-lookup"><span data-stu-id="ea704-113">Help users maintain awareness of their real-world surroundings.</span></span>

<span data-ttu-id="ea704-114">聲場更深入地連接全像混合現實世界的影像。</span><span class="sxs-lookup"><span data-stu-id="ea704-114">Acoustics more deeply connect holograms to the mixed-reality world.</span></span> <span data-ttu-id="ea704-115">它會提供有關環境和物件狀態的提示。</span><span class="sxs-lookup"><span data-stu-id="ea704-115">It provides cues about the environment and object state.</span></span>

<span data-ttu-id="ea704-116">請參閱 [使用音訊之設計](spatial-sound-design.md)的詳細範例。</span><span class="sxs-lookup"><span data-stu-id="ea704-116">See detailed [examples of design that uses audio](spatial-sound-design.md).</span></span>

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/PTPvx7mDon4" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## <a name="device-support"></a><span data-ttu-id="ea704-117">裝置支援</span><span class="sxs-lookup"><span data-stu-id="ea704-117">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="ea704-118"><strong>功能</strong></span><span class="sxs-lookup"><span data-stu-id="ea704-118"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="ea704-119"><a href="/hololens/hololens1-hardware"><strong>HoloLens (第一代) </strong></a></span><span class="sxs-lookup"><span data-stu-id="ea704-119"><a href="/hololens/hololens1-hardware"><strong>HoloLens (first gen)</strong></a></span></span></td>
        <td><span data-ttu-id="ea704-120"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="ea704-120"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="ea704-121"><a href="../discover/immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></span><span class="sxs-lookup"><span data-stu-id="ea704-121"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="ea704-122">空間化</span><span class="sxs-lookup"><span data-stu-id="ea704-122">Spatialization</span></span></td>
        <td><span data-ttu-id="ea704-123">✔️</span><span class="sxs-lookup"><span data-stu-id="ea704-123">✔️</span></span></td>
        <td><span data-ttu-id="ea704-124">✔️</span><span class="sxs-lookup"><span data-stu-id="ea704-124">✔️</span></span></td>
        <td><span data-ttu-id="ea704-125">✔️</span><span class="sxs-lookup"><span data-stu-id="ea704-125">✔️</span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="ea704-126">Spatialization 硬體加速</span><span class="sxs-lookup"><span data-stu-id="ea704-126">Spatialization hardware acceleration</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="ea704-127">✔️</span><span class="sxs-lookup"><span data-stu-id="ea704-127">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>

## <a name="use-of-sounds-in-mixed-reality"></a><span data-ttu-id="ea704-128">在混合現實中使用音效</span><span class="sxs-lookup"><span data-stu-id="ea704-128">Use of sounds in mixed reality</span></span>

<span data-ttu-id="ea704-129">[在混合現實中使用](spatial-sound-design.md) 音效需要的方法與觸控和鍵盤和滑鼠應用程式不同。</span><span class="sxs-lookup"><span data-stu-id="ea704-129">[Use of sounds in mixed reality](spatial-sound-design.md) requires a different approach than in touch and keyboard-and-mouse applications.</span></span> <span data-ttu-id="ea704-130">主要的音效設計決策包括要 spatialize 的音效，以及要 sonify 的互動。</span><span class="sxs-lookup"><span data-stu-id="ea704-130">Key sound design decisions include which sounds to spatialize and which interactions to sonify.</span></span> <span data-ttu-id="ea704-131">這些決策會大幅影響使用者信賴度、生產力和學習曲線。</span><span class="sxs-lookup"><span data-stu-id="ea704-131">These decisions strongly effect user confidence, productivity, and learning curve.</span></span>

### <a name="case-studies"></a><span data-ttu-id="ea704-132">案例研究</span><span class="sxs-lookup"><span data-stu-id="ea704-132">Case studies</span></span>

<span data-ttu-id="ea704-133">HoloTour 幾乎會讓使用者在世界各地旅遊和歷程記錄網站。</span><span class="sxs-lookup"><span data-stu-id="ea704-133">HoloTour virtually takes users to tourist and historical sites around the world.</span></span> <span data-ttu-id="ea704-134">請參閱 HoloTour 案例研究的 [音效設計](case-study-spatial-sound-design-for-holotour.md) 。</span><span class="sxs-lookup"><span data-stu-id="ea704-134">See the [Sound design for HoloTour](case-study-spatial-sound-design-for-holotour.md) case study.</span></span> <span data-ttu-id="ea704-135">用來捕捉主體空間的特殊麥克風和轉譯設定。</span><span class="sxs-lookup"><span data-stu-id="ea704-135">A special microphone and rendering setup were used to capture the subject spaces.</span></span>

<span data-ttu-id="ea704-136">RoboRaid 是適用于 HoloLens 的高能源射擊。</span><span class="sxs-lookup"><span data-stu-id="ea704-136">RoboRaid is a high-energy shooter for HoloLens.</span></span> <span data-ttu-id="ea704-137">RoboRaid 案例研究的 [音效設計](case-study-using-spatial-sound-in-roboraid.md) 說明了可確保使用空間音訊來發揮最大效果的設計選擇。</span><span class="sxs-lookup"><span data-stu-id="ea704-137">The [Sound design for RoboRaid](case-study-using-spatial-sound-in-roboraid.md) case study describes the design choices that were made to ensure spatial audio was used to the fullest dramatic effect.</span></span>

## <a name="spatialization"></a><span data-ttu-id="ea704-138">空間化</span><span class="sxs-lookup"><span data-stu-id="ea704-138">Spatialization</span></span>

<span data-ttu-id="ea704-139">Spatialization 是空間音訊的方向元件。</span><span class="sxs-lookup"><span data-stu-id="ea704-139">Spatialization is the directional component of spatial audio.</span></span> <span data-ttu-id="ea704-140">若為7.1 家用劇院設定，spatialization 就像在 loudspeakers 之間移動一樣簡單。</span><span class="sxs-lookup"><span data-stu-id="ea704-140">For a 7.1 home theater setup, spatialization is as simple as panning between loudspeakers.</span></span> <span data-ttu-id="ea704-141">但對於混合式的耳機，使用 HRTF 型技術很重要且舒適。</span><span class="sxs-lookup"><span data-stu-id="ea704-141">But for headphones in mixed reality, it's essential to use an HRTF-based technology for accuracy and comfort.</span></span> <span data-ttu-id="ea704-142">Windows 提供以 HRTF 為基礎的 spatialization，這項支援在 HoloLens 2 的硬體加速。</span><span class="sxs-lookup"><span data-stu-id="ea704-142">Windows offers HRTF-based spatialization, and this support is hardware-accelerated on HoloLens 2.</span></span>

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/aB3TDjYklmo" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### <a name="should-i-spatialize"></a><span data-ttu-id="ea704-143">我應該 spatialize 嗎？</span><span class="sxs-lookup"><span data-stu-id="ea704-143">Should I spatialize?</span></span>

<span data-ttu-id="ea704-144">Spatialization 可以改善混合現實應用程式中的許多音效。</span><span class="sxs-lookup"><span data-stu-id="ea704-144">Spatialization can improve many sounds in mixed-reality applications.</span></span> <span data-ttu-id="ea704-145">Spatialization 會從接聽程式的頭部取出聲音，將它放在世界各地。</span><span class="sxs-lookup"><span data-stu-id="ea704-145">Spatialization takes a sound out of the listener's head and places it in the world.</span></span> <span data-ttu-id="ea704-146">如需在應用程式中有效使用 spatialization 的建議，請參閱 [空間音效設計](spatial-sound-design.md)。</span><span class="sxs-lookup"><span data-stu-id="ea704-146">For suggestions on effective use of spatialization in your application, see [Spatial sound design](spatial-sound-design.md).</span></span>

### <a name="spatializer-personalization"></a><span data-ttu-id="ea704-147">空間定位器個人化</span><span class="sxs-lookup"><span data-stu-id="ea704-147">Spatializer personalization</span></span>

<span data-ttu-id="ea704-148">Hrtf 會操控各頻間的耳之間的層級和階段差異。</span><span class="sxs-lookup"><span data-stu-id="ea704-148">HRTFs manipulate the level and phase differences between ears across the frequency spectrum.</span></span> <span data-ttu-id="ea704-149">它們是以人類 head、torso 和 ear (pinnae) 的實體模型和測量為基礎。</span><span class="sxs-lookup"><span data-stu-id="ea704-149">They're based on physical models and measurements of human head, torso, and ear shapes (pinnae).</span></span> <span data-ttu-id="ea704-150">我們的大腦會回應這些差異，以提供音效的觀察方向。</span><span class="sxs-lookup"><span data-stu-id="ea704-150">Our brains respond to these differences to provide perceived direction in sound.</span></span>

<span data-ttu-id="ea704-151">每個人都有獨特的 ear 形狀、前端大小和 ear 定位。</span><span class="sxs-lookup"><span data-stu-id="ea704-151">Every individual has a unique ear shape, head size, and ear position.</span></span> <span data-ttu-id="ea704-152">因此最適合您的 Hrtf。</span><span class="sxs-lookup"><span data-stu-id="ea704-152">So the best HRTFs conform to you.</span></span> <span data-ttu-id="ea704-153">為了提高 spatialization 準確度，HoloLens 會使用您的 pupilary 距離，從耳機顯示器 (IPD) ，以調整您的前端大小 Hrtf。</span><span class="sxs-lookup"><span data-stu-id="ea704-153">To increase spatialization accuracy, HoloLens uses your inter-pupilary distance (IPD) from the headset displays to adjust the HRTFs for your head size.</span></span>

### <a name="spatializer-platform-support"></a><span data-ttu-id="ea704-154">空間定位器平臺支援</span><span class="sxs-lookup"><span data-stu-id="ea704-154">Spatializer platform support</span></span>

<span data-ttu-id="ea704-155">Windows 透過 [ISPATIALAUDIOCLIENT API](/windows/win32/coreaudio/spatial-sound)提供 spatialization，包括 hrtf。</span><span class="sxs-lookup"><span data-stu-id="ea704-155">Windows offers spatialization, including HRTFs, via the [ISpatialAudioClient API](/windows/win32/coreaudio/spatial-sound).</span></span> <span data-ttu-id="ea704-156">此 API 會向應用程式公開 HoloLens 2 HRTF 硬體加速。</span><span class="sxs-lookup"><span data-stu-id="ea704-156">This API exposes the HoloLens 2 HRTF hardware acceleration to applications.</span></span>

### <a name="spatializer-middleware-support"></a><span data-ttu-id="ea704-157">空間定位器中介軟體支援</span><span class="sxs-lookup"><span data-stu-id="ea704-157">Spatializer middleware support</span></span>

<span data-ttu-id="ea704-158">下列協力廠商音訊引擎可使用 Windows 的 Hrtf 支援。</span><span class="sxs-lookup"><span data-stu-id="ea704-158">Support for Windows' HRTFs is available for the following third-party audio engines.</span></span>
* <span data-ttu-id="ea704-159">[Unity 音訊引擎外掛程式](../develop/unity/spatial-sound-in-unity.md)</span><span class="sxs-lookup"><span data-stu-id="ea704-159">A [Unity audio engine plugin](../develop/unity/spatial-sound-in-unity.md)</span></span>
* <span data-ttu-id="ea704-160">[Wwise 音訊引擎外掛程式](https://www.audiokinetic.com/products/plug-ins/msspatial/)</span><span class="sxs-lookup"><span data-stu-id="ea704-160">A [Wwise audio engine plugin](https://www.audiokinetic.com/products/plug-ins/msspatial/)</span></span>

## <a name="acoustics"></a><span data-ttu-id="ea704-161">聲學</span><span class="sxs-lookup"><span data-stu-id="ea704-161">Acoustics</span></span>

<span data-ttu-id="ea704-162">空間音訊大約是方向。</span><span class="sxs-lookup"><span data-stu-id="ea704-162">Spatial audio is about more than direction.</span></span> <span data-ttu-id="ea704-163">其他維度包括遮蔽、障礙物、回音、傳送和來源模型。</span><span class="sxs-lookup"><span data-stu-id="ea704-163">Other dimensions include occlusion, obstruction, reverb, portaling, and source modeling.</span></span> <span data-ttu-id="ea704-164">這些維度 *統稱為聲場。*</span><span class="sxs-lookup"><span data-stu-id="ea704-164">Collectively these dimensions are referred to as *acoustics*.</span></span> <span data-ttu-id="ea704-165">在沒有聲場的情況下，hrtf 音效缺乏認知距離。</span><span class="sxs-lookup"><span data-stu-id="ea704-165">Without acoustics, spatialized sounds lack perceived distance.</span></span>

<span data-ttu-id="ea704-166">聲場的治療範圍從簡單到複雜。</span><span class="sxs-lookup"><span data-stu-id="ea704-166">Acoustics treatments range from simple to complex.</span></span> <span data-ttu-id="ea704-167">您可以使用任何音訊引擎所支援的回音，將 hrtf 音效推送至接聽程式的環境。</span><span class="sxs-lookup"><span data-stu-id="ea704-167">You can use a reverb that's supported by any audio engine to push spatialized sounds into the environment of the listener.</span></span> <span data-ttu-id="ea704-168">聲場系統（例如 [聲場專案](/gaming/acoustics/what-is-acoustics)  ）提供更豐富且更吸引人的聲場處理。</span><span class="sxs-lookup"><span data-stu-id="ea704-168">Acoustics systems such as [Project Acoustics](/gaming/acoustics/what-is-acoustics)  provide richer and more compelling acoustics treatment.</span></span> <span data-ttu-id="ea704-169">聲場專案可以建立音效上牆、大門和其他場景幾何的效果模型。</span><span class="sxs-lookup"><span data-stu-id="ea704-169">Project Acoustics can model the effect of walls, doors, and other scene geometry on a sound.</span></span> <span data-ttu-id="ea704-170">在開發階段已知相關場景幾何的情況下，這是有效的選項。</span><span class="sxs-lookup"><span data-stu-id="ea704-170">It's an effective option for cases where the relevant scene geometry is known at development time.</span></span>

## <a name="next-steps"></a><span data-ttu-id="ea704-171">後續步驟</span><span class="sxs-lookup"><span data-stu-id="ea704-171">Next steps</span></span>

- [<span data-ttu-id="ea704-172">Unity 中的空間音效</span><span class="sxs-lookup"><span data-stu-id="ea704-172">Spatial sound in Unity</span></span>](../develop/unity/spatial-sound-in-unity.md)
- [<span data-ttu-id="ea704-173">如何在混合現實應用程式中使用音效</span><span class="sxs-lookup"><span data-stu-id="ea704-173">How to use sound in mixed-reality applications</span></span>](spatial-sound-design.md)