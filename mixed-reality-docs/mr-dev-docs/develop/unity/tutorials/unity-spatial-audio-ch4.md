---
title: 空間音訊教學課程-4。 在執行時間啟用和停用空間音訊
description: 使用按鈕來啟用和停用在執行時間 spatialization 的音訊。
author: kegodin
ms.author: v-hferrone
ms.date: 12/01/2019
ms.topic: article
keywords: 混合的現實、unity、教學課程、hololens2、空間音訊、MRTK、混合現實工具組、UWP、Windows 10、HRTF、前端相關的傳送功能、回音、Microsoft 空間定位器
ms.openlocfilehash: c9e510e544962c5d1a4c462d20dafa222c6a5289
ms.sourcegitcommit: fbeff51cae92add88d2b960c9b7bbfb04d5a0291
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "97002603"
---
# <a name="enabling-and-disabling-spatialization-at-run-time"></a>在執行時間啟用和停用 spatialization

## <a name="objectives"></a>目標
在第4章中，您將會：
* 新增腳本來控制遊戲物件上的 spatialization
* 從按鈕動作驅動 spatialization 控制腳本

## <a name="add-spatialization-control-script"></a>新增 spatialization 控制項腳本
在 [ **專案** ] 窗格中按一下滑鼠右鍵，然後選擇 [ **建立-> c # 腳本**] 來建立新的 c # 腳本。 將腳本命名為 "SpatializeOnOff"。

![建立腳本](images/spatial-audio/create-script.png)

按兩下 [ **專案** ] 窗格中的腳本，在 Visual Studio 中開啟它。 以下列內容取代預設腳本內容：

> [!NOTE]
> 腳本的幾行批註化。這幾行將在 [第5章](unity-spatial-audio-ch5.md)中取消批註。

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
> 若要啟用或停用 spatialization，腳本只會調整 **spatialBlend** 屬性，並啟用 **spatialization** 屬性。 在此模式中，Unity 仍會套用 **音量** 曲線。 否則，如果使用者從來源到目前為止都要停用 spatialization，他們會聽到大量增加。 <br> <br>
> 如果您想要完全停用 spatialization，請修改腳本，以同時調整 **SourceObject** 變數的 **spatialization** 布林值屬性。

## <a name="attach-your-script-and-drive-it-from-the-button"></a>附加您的腳本，並從按鈕進行驅動
在 [] 的 [偵測 **器** ] 窗格 **中，按一下**[ **新增元件** ]，然後在 [關閉] 腳本 **上新增 Spatialize** ：

![將腳本新增至四個](images/spatial-audio/add-script-to-quad.png)

在 [ **Spatialize on** ] 元件的 [ **四**：
1. 尋找階層中的 **PressableButtonHoloLens2-> IconAndText > TextMeshPro** **主旨：**

![尋找階層中的 PressableButtonHoloLens2 物件](images/spatial-audio/pressable-button-object.png)

2. 將 **TextMeshPro** 主體拖曳至 **Spatialize On** 元件的 **ButtonTextObject** 欄位

這些變更之後，**四個四** 個 **Spatialize 的關閉** 元件看起來會像這樣：

![Spatialize on basic](images/spatial-audio/spatialize-on-off-basic.png)

若要在放開按鈕時設定按鈕以呼叫 **Spatialize On** script，請開啟 **PressableButtonHoloLens2** 物件的 [偵測 **器**] 窗格，尋找 **互動** 元件，然後：
1. 尋找 **事件** 子區段的 **OnClick ( # B1** 區域
2. 將 **四** 個從階層 **拖曳至目標** 物件位置。
3. 從 [動作] 下拉式清單方塊中選取 [ **SpatializeOnOff. SwapSpatialization** ]。

這些變更之後， **互動** 元件看起來會像這樣：

![按鈕動作設定](images/spatial-audio/button-action-settings.png)

## <a name="next-steps"></a>後續步驟
在 HoloLens 2 或 Unity 編輯器中試用您的應用程式。 在應用程式中，您現在可以觸控按鈕來啟用和停用影片上的 spatialization。 在 Unity 編輯器中進行測試時，請按下空格鍵並以滾輪滾動，以啟動手動模擬。 

> [!div class="nextstepaction"]
> [第5章](unity-spatial-audio-ch5.md) 

