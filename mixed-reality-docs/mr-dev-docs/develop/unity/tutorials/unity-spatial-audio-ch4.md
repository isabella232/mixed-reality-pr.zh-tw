---
title: 空間音訊教學課程-4。 在執行時間啟用和停用空間音訊
description: 使用按鈕來啟用和停用在執行時間 spatialization 的音訊。
author: kegodin
ms.author: v-hferrone
ms.date: 02/05/2021
ms.topic: article
keywords: 混合的現實、unity、教學課程、hololens2、空間音訊、MRTK、混合現實工具組、UWP、Windows 10、HRTF、前端相關的傳送功能、回音、Microsoft 空間定位器
ms.openlocfilehash: 9d0fa432f2e653cdd6820cb6c779cc1acc5c4b15
ms.sourcegitcommit: 4a6c26615d52776bdc4faab70391592092a471fc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2021
ms.locfileid: "110712745"
---
# <a name="4-enabling-and-disabling-spatialization-at-run-time"></a>4. 在執行時間啟用和停用 spatialization

## <a name="overview"></a>概觀

在本教學課程中，您將瞭解如何在執行時間啟用和停用 spatialization，並在 unity 編輯器和 HoloLens 2 中進行測試。

## <a name="objectives"></a>目標

* 新增腳本來控制遊戲物件上的 spatialization
* 從按鈕動作驅動 spatialization 控制腳本

## <a name="add-spatialization-control-script"></a>新增 spatialization 控制項腳本

 以滑鼠右鍵按一下 [專案] 視窗，然後選擇 [**建立**  >  **c # 腳本**] 來建立新的 c # 腳本，輸入適合腳本的名稱，例如 _SpatializeOnOff_：

![建立指令碼](images/spatial-audio/spatial-audio-04-section1-step1-1.PNG)

按兩下 [專案] 視窗中的腳本，在 Visual Studio 中開啟它。 以下列內容取代預設腳本內容：

> [!NOTE]
> 腳本的幾行批註化。下一章將取消批註這些行 [：使用回音來增加空間音訊的距離](unity-spatial-audio-ch5.md)。

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
> 若要啟用或停用 spatialization，腳本只會調整 **spatialBlend** 屬性，並啟用 **spatialization** 屬性。 在此模式中，Unity 仍會套用 **音量** 曲線。 否則，如果使用者從來源到目前為止都要停用 spatialization，他們會聽到大量增加。
> 如果您想要完全停用 spatialization，請修改腳本，以同時調整 **SourceObject** 變數的 **spatialization** 布林值屬性。

## <a name="attach-your-script-and-drive-it-from-the-button"></a>附加您的腳本，並從按鈕進行驅動

選取階層中的 [ **四** ]，然後在 [偵測器] 視窗中，使用 [新增元件] 按鈕來新增 **SpatializeOnOff (腳本)**

![將腳本新增至四個](images/spatial-audio/spatial-audio-04-section2-step1-1.PNG)

在階層中，找到 **PressableButtonHoloLens2**  >  **IconAndText**  >  **TextMeshPro**。

在階層中仍選取了 **四** 個物件時，請在 [偵測器] 視窗中，找 **出 (腳本)** 元件的 Spatialize，然後拖放 PressableButtonHoloLens2 的 **TextMeshPro** 元件。

![尋找階層中的 PressableButtonHoloLens2 物件](images/spatial-audio/spatial-audio-04-section2-step1-2.PNG)

若要在放開按鈕時設定按鈕以呼叫 **SpatializeOnOff** 腳本，您必須設定互動腳本。

在 [階層] 視窗中，選取 **PressableButtonHoloLens2**。 在 [偵測器] 視窗中，找出 [ **互動 (腳本)** 元件]，然後按一下 [OnClick () 事件] 底下的 + 圖示。

* 在 [階層] 視窗中仍選取 [ **PressableButtonHoloLens2** ] 物件，然後從 [階層] 視窗中，將 [ **四** 個物件] 拖曳至您剛剛加入之事件的 [ **無 (物件])** 欄位，讓 ButtonParent 物件從此按鈕接聽按鈕 click 事件：

* 按一下相同事件的 [沒有函式] 下拉式清單。 然後選取 [ **SpatializeOnOff**  >  **SwapSpatialization ()** 以開啟和關閉空間音訊

![按鈕動作設定](images/spatial-audio/spatial-audio-04-section2-step1-3.PNG)

## <a name="congratulations"></a>恭喜！

在本教學課程中，您已瞭解如何在執行時間啟用和停用 spatialization、在 HoloLens 2 上或在 Unity 編輯器中測試應用程式。 您現在可以在應用程式中按一下按鈕，以啟用和停用音訊的 spatialization。

在下一個教學課程中，您將會新增一個回音效果，讓音效成為距離的意義。

> [!TIP]
> 如需有關如何建立 Unity 專案並將其部署至 HoloLens 2 的提醒，您可以參閱[對您的 HoloLens 2 建置應用程式](mr-learning-base-02.md#building-your-application-to-your-hololens-2)的指示。

> [!div class="nextstepaction"]
> [下一個教學課程： 5. 使用回音將距離新增至空間音訊](unity-spatial-audio-ch5.md)
