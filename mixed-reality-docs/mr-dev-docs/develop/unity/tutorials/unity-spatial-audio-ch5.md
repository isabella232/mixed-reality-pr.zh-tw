---
title: 空間音訊教學課程-5。 使用殘響增加空間音訊的距離
description: 新增回音效果，以增強距離變化與空間音訊的意義。
author: kegodin
ms.author: v-hferrone
ms.date: 12/01/2019
ms.topic: article
keywords: 混合的現實、unity、教學課程、hololens2、空間音訊、MRTK、混合現實工具組、UWP、Windows 10、HRTF、前端相關的傳送功能、回音、Microsoft 空間定位器、音訊混音器、SFX 回音
ms.openlocfilehash: 3d19bb0b22c507eb692a752aa318ecb82a1cf2f7
ms.sourcegitcommit: a56a551ebc59529a3683fe6db90d59f982ab0b45
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2021
ms.locfileid: "98578369"
---
# <a name="5-using-reverb-to-add-distance-to-spatial-audio"></a><span data-ttu-id="47841-105">5.使用殘響增加空間音訊的距離</span><span class="sxs-lookup"><span data-stu-id="47841-105">5. Using reverb to add distance to spatial audio</span></span>

## <a name="overview"></a><span data-ttu-id="47841-106">概觀</span><span class="sxs-lookup"><span data-stu-id="47841-106">Overview</span></span>

<span data-ttu-id="47841-107">在上一個教學課程中，您已新增音效的 spatialization，讓他們在本教學課程中有意義的方向，您將會新增一個回音效果，讓音效具有距離。</span><span class="sxs-lookup"><span data-stu-id="47841-107">In previous tutorial, you have added spatialization for the sounds to give them a sense of direction in this tutorial you'll add a reverb effect to give sounds a sense of distance.</span></span>

## <a name="objectives"></a><span data-ttu-id="47841-108">目標</span><span class="sxs-lookup"><span data-stu-id="47841-108">Objectives</span></span>

* <span data-ttu-id="47841-109">藉由新增回音來改善音效來源的認知距離。</span><span class="sxs-lookup"><span data-stu-id="47841-109">Improve perceived distance of sound sources by adding reverb.</span></span>
* <span data-ttu-id="47841-110">使用接聽程式與全像投影之間的距離，控制音效的感覺。</span><span class="sxs-lookup"><span data-stu-id="47841-110">Control perceived distance of the sound using the listener's distance to the hologram.</span></span>

## <a name="add-a-mixer-group-and-a-reverb-effect"></a><span data-ttu-id="47841-111">新增混音器群組和回音效果</span><span class="sxs-lookup"><span data-stu-id="47841-111">Add a mixer group and a reverb effect</span></span>

<span data-ttu-id="47841-112">在 [Spatializing 按鈕互動音效教學](unity-spatial-audio-ch2.md)課程中，我們新增了混音器。</span><span class="sxs-lookup"><span data-stu-id="47841-112">In [Spatializing button interaction sounds Tutorial](unity-spatial-audio-ch2.md), we added a mixer.</span></span> <span data-ttu-id="47841-113">混音器依預設會包含一個名為 **Master** 的 **群組**。</span><span class="sxs-lookup"><span data-stu-id="47841-113">The mixer includes one **Group** by default called **Master**.</span></span> <span data-ttu-id="47841-114">因為我們只想要將回音效果套用至某些音效，所以讓我們為這些音效新增第二個群組。</span><span class="sxs-lookup"><span data-stu-id="47841-114">Because we'll only want to apply a reverb effect to some sounds, let's add a second Group for those sounds.</span></span> <span data-ttu-id="47841-115">若要加入群組，請以滑鼠右鍵按一下 **音訊混音** 器中的主要群組，選擇 [ **新增子群組** ]，然後提供適當的名稱來取得範例 _房間效果_：</span><span class="sxs-lookup"><span data-stu-id="47841-115">To add a Group, right click on the Master group in the **Audio Mixer** choose **Add child group** and give suitable name for example _Room Effect_:</span></span>

![新增子群組](images/spatial-audio/spatial-audio-05-section1-step1-1.png)

<span data-ttu-id="47841-117">每個 **群組** 都有自己的一組效果。</span><span class="sxs-lookup"><span data-stu-id="47841-117">Each **Group** has its own set of effects.</span></span> <span data-ttu-id="47841-118">按一下新群組上的 [新增 **...** ]，然後選擇 [ **SFX 回音**：</span><span class="sxs-lookup"><span data-stu-id="47841-118">Add a reverb effect to the new group by clicking **Add...** on the new group, and choosing **SFX Reverb**:</span></span>

![新增 SFX 回音](images/spatial-audio/spatial-audio-05-section1-step1-2.png)

<span data-ttu-id="47841-120">在音訊術語中，原始的 unreverberated 音訊稱為「 _乾路徑_」，而以「回音」篩選篩選之後的音訊則稱為「 _潮濕」路徑_。</span><span class="sxs-lookup"><span data-stu-id="47841-120">In audio terminology, the original, unreverberated audio is called the _dry path_, and the audio after filtering with the reverb filter is called the _wet path_.</span></span> <span data-ttu-id="47841-121">這兩個路徑都會傳送至音訊輸出，而其在這種混合中的相對強度稱為 _濕/幹組合_。</span><span class="sxs-lookup"><span data-stu-id="47841-121">Both paths are sent to the audio output, and their relative strengths in this mixture is called the _wet/dry mix_.</span></span> <span data-ttu-id="47841-122">濕/幹混合對距離的意義有強烈的影響。</span><span class="sxs-lookup"><span data-stu-id="47841-122">The wet/dry mix strongly affects the sense of distance.</span></span>

<span data-ttu-id="47841-123">**SFX 的回音** 包含可調整效果中濕/幹混合的控制項。</span><span class="sxs-lookup"><span data-stu-id="47841-123">The **SFX Reverb** includes controls to adjust the wet/dry mix within the effect.</span></span> <span data-ttu-id="47841-124">因為 **Microsoft 空間定位器** 外掛程式會處理試路徑，所以我們只會針對潮濕的路徑使用 **SFX 的回音** 。</span><span class="sxs-lookup"><span data-stu-id="47841-124">Because the **Microsoft Spatializer** plugin handles the dry path, we'll be using the **SFX Reverb** only for the wet path.</span></span> <span data-ttu-id="47841-125">在您的 **SFX 回音** 的偵測器窗格上：</span><span class="sxs-lookup"><span data-stu-id="47841-125">On the Inspector pane of your **SFX Reverb**:</span></span>

* <span data-ttu-id="47841-126">將 [ **乾等級** ] 屬性設定為最低的設定 (-10000 mB) </span><span class="sxs-lookup"><span data-stu-id="47841-126">Set the **Dry Level** property to the lowest setting (-10000 mB)</span></span>
* <span data-ttu-id="47841-127">將 [ **空間] 屬性** 設定為最高的設定 (0 mB) </span><span class="sxs-lookup"><span data-stu-id="47841-127">Set the **Room property** to the highest setting (0 mB)</span></span>

![SFX 回音屬性](images/spatial-audio/spatial-audio-05-section1-step1-3.png)

<span data-ttu-id="47841-129">其他設定則控制模擬房間的感覺。</span><span class="sxs-lookup"><span data-stu-id="47841-129">The other settings control the feel of the simulated room.</span></span> <span data-ttu-id="47841-130">尤其是， **衰減時間** 與認知的房間大小有關。</span><span class="sxs-lookup"><span data-stu-id="47841-130">In particular, **Decay Time** is related to perceived room size.</span></span>

## <a name="enable-reverb-on-the-video-playback"></a><span data-ttu-id="47841-131">啟用影片播放時的回音</span><span class="sxs-lookup"><span data-stu-id="47841-131">Enable reverb on the video playback</span></span>

<span data-ttu-id="47841-132">有兩個步驟可在音訊來源上啟用回音：</span><span class="sxs-lookup"><span data-stu-id="47841-132">There are two steps to enable reverb on an audio source:</span></span>

* <span data-ttu-id="47841-133">將 **音訊來源** 路由傳送至適當的 **群組**</span><span class="sxs-lookup"><span data-stu-id="47841-133">Route the **Audio Source** to the appropriate **Group**</span></span>
* <span data-ttu-id="47841-134">設定 **Microsoft 空間定位器** 外掛程式，以將音訊傳遞到 **群組** 進行處理</span><span class="sxs-lookup"><span data-stu-id="47841-134">Set the **Microsoft Spatializer** plugin to pass audio into the **Group** for processing</span></span>

<span data-ttu-id="47841-135">在下列步驟中，您將調整腳本來控制音訊路由，並附加 **Microsoft 空間定位器** 外掛程式所提供的控制項腳本，將資料送入回送。</span><span class="sxs-lookup"><span data-stu-id="47841-135">In the following steps, you will adjust the script to control the audio routing, and attach a control script provided with the **Microsoft Spatializer** plugin to feed data into the reverb.</span></span>

<span data-ttu-id="47841-136">在階層中選取的 **四** 個步驟中，按一下 [偵測器] 視窗上的 [ **新增元件** ]，然後將 **房間效果的傳送層級 (腳本)**：</span><span class="sxs-lookup"><span data-stu-id="47841-136">With the **Quad** selected in the Hierarchy click **Add Component** On the Inspector window and add the **Room Effect Send Level(Script)**:</span></span>

![新增傳送層級腳本](images/spatial-audio/spatial-audio-05-section2-step1-1.png)

> [!NOTE]
> <span data-ttu-id="47841-138">除非您啟用 **Microsoft 空間定位器** 外掛程式的 **房間效果傳送層級** 功能，否則它不會將任何音訊傳回至 Unity 音訊引擎以進行效果處理。</span><span class="sxs-lookup"><span data-stu-id="47841-138">Unless you enable **Room Effect Send Level** feature of the **Microsoft Spatializer** plugin, it doesn't send any audio back to the Unity audio engine for effect processing.</span></span>

<span data-ttu-id="47841-139">**房間效果傳送層級** 元件包含圖形控制項，可將傳送至 Unity 音訊引擎的音訊層級設定為進行回音處理。</span><span class="sxs-lookup"><span data-stu-id="47841-139">The **Room Effect Send Level** component includes a graph control that sets the level of the audio sent to the Unity audio engine for reverb processing.</span></span> <span data-ttu-id="47841-140">若要開啟圖形控制項，請按一下 **房間效果傳送層級**。</span><span class="sxs-lookup"><span data-stu-id="47841-140">To open the graph control, click on the **Room Effect Send Level**.</span></span>  <span data-ttu-id="47841-141">按一下並向下拖曳綠色曲線，將層級設定為 [30dB]：</span><span class="sxs-lookup"><span data-stu-id="47841-141">Click and drag the green curve downwards to set the level to about -30dB:</span></span>

![調整回音曲線](images/spatial-audio/spatial-audio-05-section2-step1-2.png)

<span data-ttu-id="47841-143">接下來，將 **SpatializeOnOff** 腳本中的4個批註行取消批註。</span><span class="sxs-lookup"><span data-stu-id="47841-143">Next, uncomment the 4 commented lines in the **SpatializeOnOff** script.</span></span> <span data-ttu-id="47841-144">腳本現在看起來會像這樣：</span><span class="sxs-lookup"><span data-stu-id="47841-144">The script will now look like this:</span></span>

```c#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.Audio;

[RequireComponent(typeof(AudioSource))]
public class SpatializeOnOff : MonoBehaviour
{
    public GameObject ButtonTextObject;
    public AudioMixerGroup RoomEffectGroup;
    public AudioMixerGroup MasterGroup;

    private AudioSource m_SourceObject;
    private bool m_IsSpatialized;
    private TMPro.TextMeshPro m_TextMeshPro;

    public void Start()
    {
        m_SourceObject = gameObject.GetComponent<AudioSource>();
        m_TextMeshPro = ButtonTextObject.GetComponent<TMPro.TextMeshPro>();
        SetSpatialized();
    }

    public void SwapSpatialization()
    {
        if (m_IsSpatialized)
        {
            SetStereo();
        }
        else
        {
            SetSpatialized();
        }
    }

    private void SetSpatialized()
    {
        m_IsSpatialized = true;
        m_SourceObject.spatialBlend = 1;
        m_TextMeshPro.SetText("Set Stereo");
        m_SourceObject.outputAudioMixerGroup = RoomEffectGroup;
    }

    private void SetStereo()
    {
        m_IsSpatialized = false;
        m_SourceObject.spatialBlend = 0;
        m_TextMeshPro.SetText("Set Spatialized");
        m_SourceObject.outputAudioMixerGroup = MasterGroup;
    }

}
```

<span data-ttu-id="47841-145">這些行會取消批註之後，它會將兩個屬性新增至 **SpatializeOnOff 腳本** 的偵測器。</span><span class="sxs-lookup"><span data-stu-id="47841-145">Once these lines are Uncommented  it adds two properties to the Inspector of the **SpatializeOnOff script**.</span></span> <span data-ttu-id="47841-146">在 **四** 個 **SpatializeOnOff** 元件的 [偵測器] 視窗上指派這些資訊。</span><span class="sxs-lookup"><span data-stu-id="47841-146">assign these on the Inspector window of **SpatializeOnOff** component of the **Quad**.</span></span>

<span data-ttu-id="47841-147">在階層中仍選取了四個物件時，在 [偵測器] 視窗中找到 **SpatializeOnOff 腳本** 元件和：</span><span class="sxs-lookup"><span data-stu-id="47841-147">With the Quad object still selected in the Hierarchy , in the Inspector window locate the **SpatializeOnOff Script** component and :</span></span>

* <span data-ttu-id="47841-148">將 [ **會議室效果群組** ] 屬性設定為新的房間效果混音器群組</span><span class="sxs-lookup"><span data-stu-id="47841-148">Set the **Room Effect Group** property to your new Room Effect mixer group</span></span>
* <span data-ttu-id="47841-149">將 [ **主要群組** ] 屬性設定為主要混音器群組</span><span class="sxs-lookup"><span data-stu-id="47841-149">Set the **Master Group** property to the Master mixer group</span></span>

![Spatialize 關閉擴充](images/spatial-audio/spatial-audio-05-section2-step1-3.png)

## <a name="congratulations"></a><span data-ttu-id="47841-151">恭喜！</span><span class="sxs-lookup"><span data-stu-id="47841-151">Congratulations</span></span>

<span data-ttu-id="47841-152">您已完成適用于 Unity 的 HoloLens 2 空間音訊教學課程。</span><span class="sxs-lookup"><span data-stu-id="47841-152">You've completed the HoloLens 2 spatial audio tutorials for Unity.</span></span> <span data-ttu-id="47841-153">試用 HoloLens 2 或 Unity 上的應用程式。</span><span class="sxs-lookup"><span data-stu-id="47841-153">Try out the app on a HoloLens 2 or Unity.</span></span> <span data-ttu-id="47841-154">當您按一下應用程式中的按鈕來啟動 spatialization 時，腳本會將影片的音訊路由傳送至房間效果群組，以新增回音。</span><span class="sxs-lookup"><span data-stu-id="47841-154">When you click the button in the app to activate spatialization, the script will route the video's audio to the Room Effect Group to add reverb.</span></span> <span data-ttu-id="47841-155">切換至身歷聲時，會將音訊路由傳送至主要群組，並避免新增回音。</span><span class="sxs-lookup"><span data-stu-id="47841-155">When switching to stereo, it will route the audio to the Master group, and avoid adding reverb.</span></span>

> [!TIP]
> <span data-ttu-id="47841-156">如需有關如何建立 Unity 專案並將其部署至 HoloLens 2 的提醒，您可以參閱[對您的 HoloLens 2 建置應用程式](mr-learning-base-02.md#building-your-application-to-your-hololens-2)的指示。</span><span class="sxs-lookup"><span data-stu-id="47841-156">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Building your app to your HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions.</span></span>
