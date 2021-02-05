---
title: 空間音訊教學課程-4。 在執行時間啟用和停用空間音訊
description: 使用按鈕來啟用和停用在執行時間 spatialization 的音訊。
author: kegodin
ms.author: v-hferrone
ms.date: 02/05/2021
ms.topic: article
keywords: 混合的現實、unity、教學課程、hololens2、空間音訊、MRTK、混合現實工具組、UWP、Windows 10、HRTF、前端相關的傳送功能、回音、Microsoft 空間定位器
ms.openlocfilehash: 26143975707b2cd6141803a6335cec89db5bbd26
ms.sourcegitcommit: 68140e9ce84e69a99c2b3d970c7b8f2927a7fc93
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/05/2021
ms.locfileid: "99590730"
---
# <a name="4-enabling-and-disabling-spatialization-at-run-time"></a><span data-ttu-id="b7265-105">4. 在執行時間啟用和停用 spatialization</span><span class="sxs-lookup"><span data-stu-id="b7265-105">4. Enabling and disabling spatialization at run time</span></span>

## <a name="overview"></a><span data-ttu-id="b7265-106">概觀</span><span class="sxs-lookup"><span data-stu-id="b7265-106">Overview</span></span>

<span data-ttu-id="b7265-107">在本教學課程中，您將瞭解如何在執行時間啟用和停用 spatialization，並在 unity 編輯器和 HoloLens 2 中進行測試。</span><span class="sxs-lookup"><span data-stu-id="b7265-107">In this tutorial, you will learn how to Enable and disable spatialization at run time and test this in the unity editor and HoloLens 2.</span></span>

## <a name="objectives"></a><span data-ttu-id="b7265-108">目標</span><span class="sxs-lookup"><span data-stu-id="b7265-108">Objectives</span></span>

* <span data-ttu-id="b7265-109">新增腳本來控制遊戲物件上的 spatialization</span><span class="sxs-lookup"><span data-stu-id="b7265-109">Add a new script to control spatialization on a game object</span></span>
* <span data-ttu-id="b7265-110">從按鈕動作驅動 spatialization 控制腳本</span><span class="sxs-lookup"><span data-stu-id="b7265-110">Drive the spatialization control script from button actions</span></span>

## <a name="add-spatialization-control-script"></a><span data-ttu-id="b7265-111">新增 spatialization 控制項腳本</span><span class="sxs-lookup"><span data-stu-id="b7265-111">Add spatialization control script</span></span>

 <span data-ttu-id="b7265-112">以滑鼠右鍵按一下 [專案] 視窗，然後選擇 [**建立**  >  **c # 腳本**] 來建立新的 c # 腳本，輸入適合腳本的名稱，例如 _SpatializeOnOff_：</span><span class="sxs-lookup"><span data-stu-id="b7265-112">Right-click in the Project window and choose **Create** > **C# Script** to create a new C# script, enter a suitable name for the script, for example, _SpatializeOnOff_:</span></span>

![建立腳本](images/spatial-audio/spatial-audio-04-section1-step1-1.png)

<span data-ttu-id="b7265-114">按兩下 [專案] 視窗中的腳本，在 Visual Studio 中開啟它。</span><span class="sxs-lookup"><span data-stu-id="b7265-114">Double-click the script in the Project window to open it in Visual Studio.</span></span> <span data-ttu-id="b7265-115">以下列內容取代預設腳本內容：</span><span class="sxs-lookup"><span data-stu-id="b7265-115">Replace the default script contents with the following:</span></span>

> [!NOTE]
> <span data-ttu-id="b7265-116">腳本的幾行批註化。下一章將取消批註這些行 [：使用回音來增加空間音訊的距離](unity-spatial-audio-ch5.md)。</span><span class="sxs-lookup"><span data-stu-id="b7265-116">Several lines of the script are commented out. These lines will be uncommented in [Next Chapter: Using reverb to add distance to spatial audio](unity-spatial-audio-ch5.md).</span></span>

```c#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.Audio;

[RequireComponent(typeof(AudioSource))]
public class SpatializeOnOff : MonoBehaviour
{
    public GameObject ButtonTextObject;
    //public AudioMixerGroup RoomEffectGroup;
    //public AudioMixerGroup MasterGroup;

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
        //m_SourceObject.outputAudioMixerGroup = RoomEffectGroup;
    }

    private void SetStereo()
    {
        m_IsSpatialized = false;
        m_SourceObject.spatialBlend = 0;
        m_TextMeshPro.SetText("Set Spatialized");
        //m_SourceObject.outputAudioMixerGroup = MasterGroup;
    }

}
```

> [!NOTE]
> <span data-ttu-id="b7265-117">若要啟用或停用 spatialization，腳本只會調整 **spatialBlend** 屬性，並啟用 **spatialization** 屬性。</span><span class="sxs-lookup"><span data-stu-id="b7265-117">To enable or disable the spatialization, the script only adjusts the **spatialBlend** property, leaving the **spatialization** property enabled.</span></span> <span data-ttu-id="b7265-118">在此模式中，Unity 仍會套用 **音量** 曲線。</span><span class="sxs-lookup"><span data-stu-id="b7265-118">In this mode, Unity still applies the **Volume** curve.</span></span> <span data-ttu-id="b7265-119">否則，如果使用者從來源到目前為止都要停用 spatialization，他們會聽到大量增加。</span><span class="sxs-lookup"><span data-stu-id="b7265-119">Otherwise, if the user were to disable spatialization when far from the source, they would hear the volume increase abruptly.</span></span>
> <span data-ttu-id="b7265-120">如果您想要完全停用 spatialization，請修改腳本，以同時調整 **SourceObject** 變數的 **spatialization** 布林值屬性。</span><span class="sxs-lookup"><span data-stu-id="b7265-120">If you prefer to fully disable spatialization, modify the script to also adjust the **spatialization** boolean property of the **SourceObject** variable.</span></span>

## <a name="attach-your-script-and-drive-it-from-the-button"></a><span data-ttu-id="b7265-121">附加您的腳本，並從按鈕進行驅動</span><span class="sxs-lookup"><span data-stu-id="b7265-121">Attach your script and drive it from the button</span></span>

<span data-ttu-id="b7265-122">選取階層中的 [ **四** ]，然後在 [偵測器] 視窗中，使用 [新增元件] 按鈕來新增 **SpatializeOnOff (腳本)**</span><span class="sxs-lookup"><span data-stu-id="b7265-122">Select **Quad** in the Hierarchy and in the Inspector window, use the Add Component button to add **SpatializeOnOff(Script)**</span></span>

![將腳本新增至四個](images/spatial-audio/spatial-audio-04-section2-step1-1.png)

<span data-ttu-id="b7265-124">在階層中，找到 **PressableButtonHoloLens2**  >  **IconAndText**  >  **TextMeshPro**。</span><span class="sxs-lookup"><span data-stu-id="b7265-124">In the Hierarchy locate **PressableButtonHoloLens2** > **IconAndText** > **TextMeshPro**.</span></span>

<span data-ttu-id="b7265-125">在階層中仍選取了 **四** 個物件時，請在 [偵測器] 視窗中，找 **出 (腳本)** 元件的 Spatialize，然後拖放 PressableButtonHoloLens2 的 **TextMeshPro** 元件。</span><span class="sxs-lookup"><span data-stu-id="b7265-125">With the **Quad** object still selected in the Hierarchy, in the Inspector window, locate the **Spatialize On Off (Script)** component and Drag and drop **TextMeshPro** Component of the PressableButtonHoloLens2.</span></span>

![尋找階層中的 PressableButtonHoloLens2 物件](images/spatial-audio/spatial-audio-04-section2-step1-2.png)

<span data-ttu-id="b7265-127">若要在放開按鈕時設定按鈕以呼叫 **SpatializeOnOff** 腳本，您必須設定互動腳本。</span><span class="sxs-lookup"><span data-stu-id="b7265-127">To set the button to call the **SpatializeOnOff** script when the button is released You need to configure interactable script.</span></span>

<span data-ttu-id="b7265-128">在 [階層] 視窗中，選取 **PressableButtonHoloLens2**。</span><span class="sxs-lookup"><span data-stu-id="b7265-128">In the Hierarchy window, select the **PressableButtonHoloLens2**.</span></span> <span data-ttu-id="b7265-129">在 [偵測器] 視窗中，找出 [ **互動 (腳本)** 元件]，然後按一下 [OnClick ( # A3 事件] 底下的 + 圖示。</span><span class="sxs-lookup"><span data-stu-id="b7265-129">In the Inspector window, locate the **Interactable (Script)** component and click on + icon under OnClick () event.</span></span>

* <span data-ttu-id="b7265-130">在 [階層] 視窗中仍選取 [ **PressableButtonHoloLens2** ] 物件，然後從 [階層] 視窗中，將 [ **四** 個物件] 拖曳至您剛剛加入之事件的 [ **無 (物件])** 欄位，讓 ButtonParent 物件從此按鈕接聽按鈕 click 事件：</span><span class="sxs-lookup"><span data-stu-id="b7265-130">With the **PressableButtonHoloLens2** object still selected in the Hierarchy window, click-and-drag the **Quad** object from the Hierarchy window into the empty **None (Object)** field of the event you just added to make the ButtonParent object listen for button click event from this button:</span></span>

* <span data-ttu-id="b7265-131">按一下相同事件的 [沒有函式] 下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="b7265-131">Click the **No Function** dropdown of the same event.</span></span> <span data-ttu-id="b7265-132">然後選取 **SpatializeOnOff**  >  **SwapSpatialization ( # B1** 來開啟和關閉空間音訊</span><span class="sxs-lookup"><span data-stu-id="b7265-132">Then select **SpatializeOnOff** > **SwapSpatialization ()** to turn on and off the Spatial audio</span></span>

![按鈕動作設定](images/spatial-audio/spatial-audio-04-section2-step1-3.png)

## <a name="congratulations"></a><span data-ttu-id="b7265-134">恭喜！</span><span class="sxs-lookup"><span data-stu-id="b7265-134">Congratulations</span></span>

<span data-ttu-id="b7265-135">在本教學課程中，您已瞭解如何在執行時間啟用和停用 spatialization、在 HoloLens 2 上或在 Unity 編輯器中測試應用程式。</span><span class="sxs-lookup"><span data-stu-id="b7265-135">In this tutorial, you have learned how to enable and disable spatialization at run time, test out the app on a HoloLens 2 or in the Unity editor.</span></span> <span data-ttu-id="b7265-136">您現在可以在應用程式中按一下按鈕，以啟用和停用音訊的 spatialization。</span><span class="sxs-lookup"><span data-stu-id="b7265-136">In the app, you can now click the button to activate and deactivate spatialization of the audio.</span></span>

<span data-ttu-id="b7265-137">在下一個教學課程中，您將會新增一個回音效果，讓音效成為距離的意義。</span><span class="sxs-lookup"><span data-stu-id="b7265-137">In the next tutorial you'll add a reverb effect to give sounds a sense of distance.</span></span>

> [!TIP]
> <span data-ttu-id="b7265-138">如需有關如何建立 Unity 專案並將其部署至 HoloLens 2 的提醒，您可以參閱[對您的 HoloLens 2 建置應用程式](mr-learning-base-02.md#building-your-application-to-your-hololens-2)的指示。</span><span class="sxs-lookup"><span data-stu-id="b7265-138">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Building your app to your HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="b7265-139">下一個教學課程： 5. 使用回音將距離新增至空間音訊</span><span class="sxs-lookup"><span data-stu-id="b7265-139">Next Tutorial: 5. Using reverb to add distance to spatial audio</span></span>](unity-spatial-audio-ch5.md)
