---
title: Unity 中的空間音效
description: 瞭解如何使用範例，從 Unity 場景內的特定3D 點播放和 attenuate 空間音效。
author: kegodin
ms.author: v-hferrone
ms.date: 11/07/2019
ms.topic: article
keywords: Unity、空間音效、HRTF、房間大小、混合現實耳機、windows mixed reality 耳機、虛擬實境耳機、MRTK、混合現實工具組、空間定位器、回音
ms.openlocfilehash: ec2703aa89925cb68860670f574a1e43f672e247
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009268"
---
# <a name="spatial-sound-in-unity"></a><span data-ttu-id="f4363-104">Unity 中的空間音效</span><span class="sxs-lookup"><span data-stu-id="f4363-104">Spatial sound in Unity</span></span>

<span data-ttu-id="f4363-105">此頁面會連結至 Unity 中空間音效的資源。</span><span class="sxs-lookup"><span data-stu-id="f4363-105">This page links to resources for spatial sound in Unity.</span></span>

## <a name="spatializer-options"></a><span data-ttu-id="f4363-106">空間定位器選項</span><span class="sxs-lookup"><span data-stu-id="f4363-106">Spatializer options</span></span>

<span data-ttu-id="f4363-107">混合現實應用程式的空間定位器選項包括：</span><span class="sxs-lookup"><span data-stu-id="f4363-107">Spatializer options for mixed reality applications include:</span></span>
* <span data-ttu-id="f4363-108">Unity 提供 *MS HRTF 空間定位器* 做為 *Windows Mixed Reality* 選用套件的一部分。</span><span class="sxs-lookup"><span data-stu-id="f4363-108">Unity provides the *MS HRTF Spatializer* as part of the *Windows Mixed Reality* optional package.</span></span>
  * <span data-ttu-id="f4363-109">以較高成本的「單一來源」架構在 CPU 上執行。</span><span class="sxs-lookup"><span data-stu-id="f4363-109">Runs on CPU in a higher-cost 'single-source' architecture.</span></span>
  * <span data-ttu-id="f4363-110">提供與原始 HoloLens 應用程式的回溯相容性。</span><span class="sxs-lookup"><span data-stu-id="f4363-110">Provided for backwards compatibility with original HoloLens applications.</span></span>
* <span data-ttu-id="f4363-111">Microsoft *空間定位器* 可從 [microsoft 空間定位器 GitHub 存放庫](https://github.com/microsoft/spatialaudio-unity)取得。</span><span class="sxs-lookup"><span data-stu-id="f4363-111">The *Microsoft Spatializer* is available from the [Microsoft spatializer GitHub repository](https://github.com/microsoft/spatialaudio-unity).</span></span>
  * <span data-ttu-id="f4363-112">使用較低成本的「多來源」架構。</span><span class="sxs-lookup"><span data-stu-id="f4363-112">Uses a lower-cost 'multi-source' architecture.</span></span>
  * <span data-ttu-id="f4363-113">卸載 HoloLens 2 上的硬體加速器。</span><span class="sxs-lookup"><span data-stu-id="f4363-113">Offloaded to a hardware accelerator on the HoloLens 2.</span></span> 

<span data-ttu-id="f4363-114">針對新的應用程式，我們建議 *Microsoft 空間定位器*。</span><span class="sxs-lookup"><span data-stu-id="f4363-114">For new applications, we recommend the *Microsoft Spatializer*.</span></span>

## <a name="enable-spatialization"></a><span data-ttu-id="f4363-115">啟用 spatialization</span><span class="sxs-lookup"><span data-stu-id="f4363-115">Enable spatialization</span></span>

<span data-ttu-id="f4363-116">使用 [適用于 unity 的 NuGet](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest) 來安裝 _SpatialAudio 空間定位器_ ，並在專案的 [音訊] 設定中選擇 [ **microsoft 空間定位器** ]。</span><span class="sxs-lookup"><span data-stu-id="f4363-116">Use [NuGet for Unity](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest) to install _Microsoft.SpatialAudio.Spatializer.Unity_ and choose **Microsoft Spatializer** in your project's audio settings.</span></span> <span data-ttu-id="f4363-117">然後：</span><span class="sxs-lookup"><span data-stu-id="f4363-117">Then:</span></span>
* <span data-ttu-id="f4363-118">將 **音訊來源** 附加至階層中的物件</span><span class="sxs-lookup"><span data-stu-id="f4363-118">Attach an **Audio Source** to an object in the hierarchy</span></span>
* <span data-ttu-id="f4363-119">勾選 [ **啟用 spatialization** ] 核取方塊</span><span class="sxs-lookup"><span data-stu-id="f4363-119">Check the **Enable spatialization** checkbox</span></span>
* <span data-ttu-id="f4363-120">將 **空間 Blend** 滑杆移至 ' 1 '</span><span class="sxs-lookup"><span data-stu-id="f4363-120">Move the **Spatial Blend** slider to '1'</span></span>
* <span data-ttu-id="f4363-121">確定您的開發人員工作站上已啟用空間音訊。</span><span class="sxs-lookup"><span data-stu-id="f4363-121">Ensure spatial audio is enabled on your developer workstation.</span></span> 
    * <span data-ttu-id="f4363-122">以滑鼠右鍵按一下工作列中的音量圖示，並確定 [空間音效] 設定為 [關閉] 以外的地方。</span><span class="sxs-lookup"><span data-stu-id="f4363-122">Right-click on the volume icon in the task bar and making sure that Spatial Sound is set to something other than "off".</span></span> 
    * <span data-ttu-id="f4363-123">選擇 **耳機用 Windows Sonic** ，以取得您將在 HoloLens 2 上聽到的最大表現。</span><span class="sxs-lookup"><span data-stu-id="f4363-123">Choose **Windows Sonic for Headphones** to get the best representation of what you'll hear on HoloLens 2.</span></span>

>[!NOTE]
><span data-ttu-id="f4363-124">如果您在 Unity 中收到錯誤，指出無法載入外掛程式 SpatialAudio，因為其中一個相依性遺失，請確認您的電腦上已安裝最新版的 [Microsoft Visual C++](https://support.microsoft.com/en-us/help/2977003/the-latest-supported-visual-c-downloads) 可轉散發套件。</span><span class="sxs-lookup"><span data-stu-id="f4363-124">If you get an error in Unity about not being able to load plugin Microsoft.SpatialAudio.Spatializer.Unity because one of its dependencies is missing, check that you have the latest version of the [Microsoft Visual C++ Redistributable](https://support.microsoft.com/en-us/help/2977003/the-latest-supported-visual-c-downloads) installed on your PC.</span></span>

<span data-ttu-id="f4363-125">如需詳細資訊，請參閱</span><span class="sxs-lookup"><span data-stu-id="f4363-125">For more information, see:</span></span>
* [<span data-ttu-id="f4363-126">Microsoft 空間定位器 GitHub 存放庫</span><span class="sxs-lookup"><span data-stu-id="f4363-126">Microsoft spatializer GitHub repository</span></span>](https://github.com/microsoft/spatialaudio-unity)
* [<span data-ttu-id="f4363-127">Microsoft 的空間定位器教學課程</span><span class="sxs-lookup"><span data-stu-id="f4363-127">Microsoft's spatializer tutorial</span></span>](tutorials/unity-spatial-audio-ch1.md)
* [<span data-ttu-id="f4363-128">Unity 的音訊來原始檔案</span><span class="sxs-lookup"><span data-stu-id="f4363-128">Unity's audio source documentation</span></span>](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html)
* [<span data-ttu-id="f4363-129">Unity 的空間定位器檔</span><span class="sxs-lookup"><span data-stu-id="f4363-129">Unity's spatializer documentation</span></span>](https://docs.unity3d.com/Manual/VRAudioSpatializer.html)

## <a name="distance-based-attenuation"></a><span data-ttu-id="f4363-130">距離型衰減</span><span class="sxs-lookup"><span data-stu-id="f4363-130">Distance-based attenuation</span></span>

<span data-ttu-id="f4363-131">Unity 的預設距離為基礎的衰減最小距離為1個計量，最大距離為500計量，並具有對數 rolloff。</span><span class="sxs-lookup"><span data-stu-id="f4363-131">Unity's default distance-based decay has a minimum distance of 1 meter and a maximum distance of 500 meters, with a logarithmic rolloff.</span></span> <span data-ttu-id="f4363-132">這些設定可能適用于您的案例，或者您可能會發現來源 attenuate 太快或太慢。</span><span class="sxs-lookup"><span data-stu-id="f4363-132">These settings may work for your scenario, or you may find that sources attenuate too quickly or too slowly.</span></span> <span data-ttu-id="f4363-133">如需詳細資訊，請參閱</span><span class="sxs-lookup"><span data-stu-id="f4363-133">For more information, see:</span></span>
* <span data-ttu-id="f4363-134">適用于建議設定的[混合現實音效設計](../../design/spatial-sound-design.md)。</span><span class="sxs-lookup"><span data-stu-id="f4363-134">[Sound design in mixed reality](../../design/spatial-sound-design.md) for recommended settings.</span></span>
* <span data-ttu-id="f4363-135">[Unity 的音訊來原始檔案](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html) ，以取得設定這些曲線的指示。</span><span class="sxs-lookup"><span data-stu-id="f4363-135">[Unity's audio source documentation](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html) for instructions on setting these curves.</span></span>

## <a name="reverb"></a><span data-ttu-id="f4363-136">混響</span><span class="sxs-lookup"><span data-stu-id="f4363-136">Reverb</span></span>

<span data-ttu-id="f4363-137">根據預設， _Microsoft 空間定位器_ 會停用空間定位器後的效果。</span><span class="sxs-lookup"><span data-stu-id="f4363-137">The _Microsoft Spatializer_ disables post-spatializer effects by default.</span></span> <span data-ttu-id="f4363-138">若要啟用 hrtf 來源的回音和其他效果：</span><span class="sxs-lookup"><span data-stu-id="f4363-138">To enable reverb and other effects for spatialized sources:</span></span>
* <span data-ttu-id="f4363-139">將 **會議室效果的傳送層級** 元件附加至每個來源</span><span class="sxs-lookup"><span data-stu-id="f4363-139">Attach the **Room Effect Send Level** component to each source</span></span>
* <span data-ttu-id="f4363-140">調整每個來源的傳送層級曲線，以控制傳送回圖形以進行效果處理的音訊增益</span><span class="sxs-lookup"><span data-stu-id="f4363-140">Adjust the send level curve for each source, to control the gain on the audio sent back to the graph for effects processing</span></span>

<span data-ttu-id="f4363-141">如需詳細資訊，請參閱 [空間定位器教學課程的第5章](tutorials/unity-spatial-audio-ch5.md) 。</span><span class="sxs-lookup"><span data-stu-id="f4363-141">See [Chapter 5 of the spatializer tutorial](tutorials/unity-spatial-audio-ch5.md) for details.</span></span>

## <a name="unity-spatial-sound-examples"></a><span data-ttu-id="f4363-142">Unity 空間音效範例</span><span class="sxs-lookup"><span data-stu-id="f4363-142">Unity spatial sound examples</span></span>

<span data-ttu-id="f4363-143">如需 Unity 中空間音效的範例，請參閱：</span><span class="sxs-lookup"><span data-stu-id="f4363-143">For examples of spatial sound in Unity, see:</span></span>
* [<span data-ttu-id="f4363-144">MRTK 示範</span><span class="sxs-lookup"><span data-stu-id="f4363-144">MRTK demos</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.Examples/Demos/Audio)
* <span data-ttu-id="f4363-145">[Microsoft 空間定位器範例專案](https://github.com/microsoft/spatialaudio-unity/tree/master/Samples/MicrosoftSpatializerSample)</span><span class="sxs-lookup"><span data-stu-id="f4363-145">The [Microsoft Spatializer sample project](https://github.com/microsoft/spatialaudio-unity/tree/master/Samples/MicrosoftSpatializerSample)</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="f4363-146">下一個開發檢查點</span><span class="sxs-lookup"><span data-stu-id="f4363-146">Next Development Checkpoint</span></span>

<span data-ttu-id="f4363-147">如果您遵循我們所配置的 Unity 開發旅程圖，就會在探索 Mixed Reality 核心構成要素。</span><span class="sxs-lookup"><span data-stu-id="f4363-147">If you're following the Unity development journey we've laid out, you're in the midst of exploring the Mixed Reality core building blocks.</span></span> <span data-ttu-id="f4363-148">接下來，您可以繼續進行下一個建置組塊：</span><span class="sxs-lookup"><span data-stu-id="f4363-148">From here, you can continue to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="f4363-149">文字</span><span class="sxs-lookup"><span data-stu-id="f4363-149">Text</span></span>](text-in-unity.md)

<span data-ttu-id="f4363-150">或者，直接跳到混合實境平台功能和 API 的主題：</span><span class="sxs-lookup"><span data-stu-id="f4363-150">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="f4363-151">共用體驗</span><span class="sxs-lookup"><span data-stu-id="f4363-151">Shared experiences</span></span>](shared-experiences-in-unity.md)

<span data-ttu-id="f4363-152">您可以隨時回到 [Unity 開發檢查點](unity-development-overview.md#2-core-building-blocks)。</span><span class="sxs-lookup"><span data-stu-id="f4363-152">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="f4363-153">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f4363-153">See also</span></span>

* [<span data-ttu-id="f4363-154">混合現實的音效設計</span><span class="sxs-lookup"><span data-stu-id="f4363-154">Sound design in mixed reality</span></span>](../../design/spatial-sound-design.md)
* [<span data-ttu-id="f4363-155">Microsoft 的空間定位器教學課程</span><span class="sxs-lookup"><span data-stu-id="f4363-155">Microsoft's spatializer tutorial</span></span>](tutorials/unity-spatial-audio-ch1.md)
