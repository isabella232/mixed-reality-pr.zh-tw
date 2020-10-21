---
title: 空間音訊教學課程-4。 在執行時間啟用和停用空間音訊
description: 使用按鈕來啟用和停用在執行時間 spatialization 的音訊。
author: kegodin
ms.author: kegodin
ms.date: 12/01/2019
ms.topic: article
keywords: 混合現實、unity、教學課程、hololens2、空間音訊
ms.openlocfilehash: cb9bfb03da864c78784c288f4d7c4190461cd838
ms.sourcegitcommit: d8f39c0b95d9e61d645d64f27baabc7a1c300dc1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/21/2020
ms.locfileid: "92293165"
---
# <a name="enabling-and-disabling-spatialization-at-run-time"></a><span data-ttu-id="90efc-105">在執行時間啟用和停用 spatialization</span><span class="sxs-lookup"><span data-stu-id="90efc-105">Enabling and disabling spatialization at run time</span></span>

## <a name="objectives"></a><span data-ttu-id="90efc-106">目標</span><span class="sxs-lookup"><span data-stu-id="90efc-106">Objectives</span></span>
<span data-ttu-id="90efc-107">在第4章中，您將會：</span><span class="sxs-lookup"><span data-stu-id="90efc-107">In this 4th chapter, you'll:</span></span>
* <span data-ttu-id="90efc-108">新增腳本來控制遊戲物件上的 spatialization</span><span class="sxs-lookup"><span data-stu-id="90efc-108">Add a new script to control spatialization on a game object</span></span>
* <span data-ttu-id="90efc-109">從按鈕動作驅動 spatialization 控制腳本</span><span class="sxs-lookup"><span data-stu-id="90efc-109">Drive the spatialization control script from button actions</span></span>

## <a name="add-spatialization-control-script"></a><span data-ttu-id="90efc-110">新增 spatialization 控制項腳本</span><span class="sxs-lookup"><span data-stu-id="90efc-110">Add spatialization control script</span></span>
<span data-ttu-id="90efc-111">在 [ **專案** ] 窗格中按一下滑鼠右鍵，然後選擇 [ **建立-> c # 腳本**] 來建立新的 c # 腳本。</span><span class="sxs-lookup"><span data-stu-id="90efc-111">Right-click in the **Project** pane and create a new C# script by choosing **Create -> C# Script**.</span></span> <span data-ttu-id="90efc-112">將腳本命名為 "SpatializeOnOff"。</span><span class="sxs-lookup"><span data-stu-id="90efc-112">Name your script "SpatializeOnOff".</span></span>

![建立腳本](images/spatial-audio/create-script.png)

<span data-ttu-id="90efc-114">按兩下 [ **專案** ] 窗格中的腳本，在 Visual Studio 中開啟它。</span><span class="sxs-lookup"><span data-stu-id="90efc-114">Double-click the script in the **Project** pane to open it in Visual Studio.</span></span> <span data-ttu-id="90efc-115">以下列內容取代預設腳本內容：</span><span class="sxs-lookup"><span data-stu-id="90efc-115">Replace the default script contents with the following:</span></span>

> [!NOTE]
> <span data-ttu-id="90efc-116">腳本的幾行批註化。這幾行將在 [第5章](unity-spatial-audio-ch5.md)中取消批註。</span><span class="sxs-lookup"><span data-stu-id="90efc-116">Several lines of the script are commented out. These lines will be uncommented in [Chapter 5](unity-spatial-audio-ch5.md).</span></span>

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
> <span data-ttu-id="90efc-117">若要啟用或停用 spatialization，腳本只會調整 **spatialBlend** 屬性，並啟用 **spatialization** 屬性。</span><span class="sxs-lookup"><span data-stu-id="90efc-117">To enable or disable spatialization, the script only adjusts the **spatialBlend** property, leaving the **spatialization** property enabled.</span></span> <span data-ttu-id="90efc-118">在此模式中，Unity 仍會套用 **音量** 曲線。</span><span class="sxs-lookup"><span data-stu-id="90efc-118">In this mode, Unity still applies the **Volume** curve.</span></span> <span data-ttu-id="90efc-119">否則，如果使用者從來源到目前為止都要停用 spatialization，他們會聽到大量增加。</span><span class="sxs-lookup"><span data-stu-id="90efc-119">Otherwise, if the user were to disable spatialization when far from the source, they would hear the volume increase abruptly.</span></span> <br> <br>
> <span data-ttu-id="90efc-120">如果您想要完全停用 spatialization，請修改腳本，以同時調整**SourceObject**變數的**spatialization**布林值屬性。</span><span class="sxs-lookup"><span data-stu-id="90efc-120">If you prefer to fully disable spatialization, modify the script to also adjust the **spatialization** boolean property of the **SourceObject** variable.</span></span>

## <a name="attach-your-script-and-drive-it-from-the-button"></a><span data-ttu-id="90efc-121">附加您的腳本，並從按鈕進行驅動</span><span class="sxs-lookup"><span data-stu-id="90efc-121">Attach your script and drive it from the button</span></span>
<span data-ttu-id="90efc-122">在 [] 的 [偵測 **器** ] 窗格 **中，按一下**[ **新增元件** ]，然後在 [關閉] 腳本 **上新增 Spatialize** ：</span><span class="sxs-lookup"><span data-stu-id="90efc-122">On the **Inspector** pane of the **Quad**, click **Add Component** and add the **Spatialize On Off** script:</span></span>

![將腳本新增至四個](images/spatial-audio/add-script-to-quad.png)

<span data-ttu-id="90efc-124">在 [ **Spatialize on** ] 元件的 [ **四**：</span><span class="sxs-lookup"><span data-stu-id="90efc-124">On the **Spatialize On Off** component of the **Quad**:</span></span>
1. <span data-ttu-id="90efc-125">尋找階層中的**PressableButtonHoloLens2-> IconAndText > TextMeshPro** **主旨：**</span><span class="sxs-lookup"><span data-stu-id="90efc-125">Find the **PressableButtonHoloLens2 -> IconAndText -> TextMeshPro** subject in the **Hierarchy**:</span></span>

![尋找階層中的 PressableButtonHoloLens2 物件](images/spatial-audio/pressable-button-object.png)

2. <span data-ttu-id="90efc-127">將**TextMeshPro**主體拖曳至**Spatialize On**元件的**ButtonTextObject**欄位</span><span class="sxs-lookup"><span data-stu-id="90efc-127">Drag the **TextMeshPro** subject onto the **ButtonTextObject** field of the **Spatialize On Off** component</span></span>

<span data-ttu-id="90efc-128">這些變更之後，**四個四**個**Spatialize 的關閉**元件看起來會像這樣：</span><span class="sxs-lookup"><span data-stu-id="90efc-128">After these changes, the **Spatialize On Off** component of the **Quad** will look like this:</span></span>

![Spatialize on basic](images/spatial-audio/spatialize-on-off-basic.png)

<span data-ttu-id="90efc-130">若要在放開按鈕時設定按鈕以呼叫**Spatialize On** script，請開啟**PressableButtonHoloLens2**物件的 [偵測**器**] 窗格，尋找**互動**元件，然後：</span><span class="sxs-lookup"><span data-stu-id="90efc-130">To set the button to call the **Spatialize On Off** script when the button is released, open the **Inspector** pane of the **PressableButtonHoloLens2** object, find the **Interactable** component, and:</span></span>
1. <span data-ttu-id="90efc-131">尋找**事件**子區段的**OnClick ( # B1**區域</span><span class="sxs-lookup"><span data-stu-id="90efc-131">Find the **OnClick ()** region of the **Events** subsection</span></span>
2. <span data-ttu-id="90efc-132">將 **四** 個從階層 **拖曳至目標** 物件位置。</span><span class="sxs-lookup"><span data-stu-id="90efc-132">Drag the **Quad** from the **Hierarchy** into the target object slot.</span></span>
3. <span data-ttu-id="90efc-133">從 [動作] 下拉式清單方塊中選取 [ **SpatializeOnOff. SwapSpatialization** ]。</span><span class="sxs-lookup"><span data-stu-id="90efc-133">Select **SpatializeOnOff.SwapSpatialization** from the action drop-down box.</span></span>

<span data-ttu-id="90efc-134">這些變更之後， **互動** 元件看起來會像這樣：</span><span class="sxs-lookup"><span data-stu-id="90efc-134">After these changes, the **Interactable** component will look like this:</span></span>

![按鈕動作設定](images/spatial-audio/button-action-settings.png)

## <a name="next-steps"></a><span data-ttu-id="90efc-136">後續步驟</span><span class="sxs-lookup"><span data-stu-id="90efc-136">Next steps</span></span>
<span data-ttu-id="90efc-137">在 HoloLens 2 或 Unity 編輯器中試用您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="90efc-137">Try out your app on a HoloLens 2 or in the Unity editor.</span></span> <span data-ttu-id="90efc-138">在應用程式中，您現在可以觸控按鈕來啟用和停用影片上的 spatialization。</span><span class="sxs-lookup"><span data-stu-id="90efc-138">In the app, you can now touch the button to activate and deactivate spatialization on the video.</span></span> <span data-ttu-id="90efc-139">在 Unity 編輯器中進行測試時，請按下空格鍵並以滾輪滾動，以啟動手動模擬。</span><span class="sxs-lookup"><span data-stu-id="90efc-139">When testing in the Unity editor, press the space bar and scroll with the scroll wheel to activate hand simulation.</span></span> 

> [!div class="nextstepaction"]
> [<span data-ttu-id="90efc-140">第5章</span><span class="sxs-lookup"><span data-stu-id="90efc-140">Chapter 5</span></span>](unity-spatial-audio-ch5.md) 

