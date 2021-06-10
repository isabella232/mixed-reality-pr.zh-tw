---
title: 空間音訊教學課程-5。 使用殘響增加空間音訊的距離
description: 新增回音效果，以增強距離變化與空間音訊的意義。
author: kegodin
ms.author: v-hferrone
ms.date: 02/05/2021
ms.topic: article
keywords: 混合的現實、unity、教學課程、hololens2、空間音訊、MRTK、混合現實工具組、UWP、Windows 10、HRTF、前端相關的傳送功能、回音、Microsoft 空間定位器、音訊混音器、SFX 回音
ms.openlocfilehash: 6f41fe904c21591915e0ef13b61dc6bff04527fe
ms.sourcegitcommit: 4a6c26615d52776bdc4faab70391592092a471fc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2021
ms.locfileid: "110712679"
---
# <a name="5-using-reverb-to-add-distance-to-spatial-audio"></a>5.使用殘響增加空間音訊的距離

## <a name="overview"></a>概觀

在上一個教學課程中，您已新增音效的 spatialization，讓他們在本教學課程中有意義的方向，您將會新增一個回音效果，讓音效具有距離。

## <a name="objectives"></a>目標

* 藉由新增回音來改善音效來源的認知距離。
* 使用接聽程式與全像投影之間的距離，控制音效的感覺。

## <a name="add-a-mixer-group-and-a-reverb-effect"></a>新增混音器群組和回音效果

在 [Spatializing 按鈕互動音效教學](unity-spatial-audio-ch2.md)課程中，我們新增了混音器。 混音器依預設會包含一個名為 **Master** 的 **群組**。 因為我們只想要將回音效果套用至某些音效，所以讓我們為這些音效新增第二個群組。 若要加入群組，請以滑鼠右鍵按一下 **音訊混音** 器中的主要群組，選擇 [ **新增子群組** ]，然後提供適當的名稱來取得範例 _房間效果_：

![新增子群組](images/spatial-audio/spatial-audio-05-section1-step1-1.PNG)

每個 **群組** 都有自己的一組效果。 按一下新群組上的 [新增 **...** ]，然後選擇 [ **SFX 回音**：

![新增 SFX 回音](images/spatial-audio/spatial-audio-05-section1-step1-2.PNG)

在音訊術語中，原始的 unreverberated 音訊稱為「 _乾路徑_」，而以「回音」篩選篩選之後的音訊則稱為「 _潮濕」路徑_。 這兩個路徑都會傳送至音訊輸出，而其在這種混合中的相對強度稱為 _濕/幹組合_。 濕/幹混合對距離的意義有強烈的影響。

**SFX 的回音** 包含可調整效果中濕/幹混合的控制項。 因為 **Microsoft 空間定位器** 外掛程式會處理試路徑，所以我們只會針對潮濕的路徑使用 **SFX 的回音** 。 在您的 **SFX 回音** 的偵測器窗格上：

* 將 [ **乾等級** ] 屬性設定為最低的設定 (-10000 mB) 
* 將 [ **空間] 屬性** 設定為最高的設定 (0 mB) 

![SFX 回音屬性](images/spatial-audio/spatial-audio-05-section1-step1-3.PNG)

其他設定則控制模擬房間的感覺。 尤其是， **衰減時間** 與認知的房間大小有關。

## <a name="enable-reverb-on-the-video-playback"></a>啟用影片播放時的回音

有兩個步驟可在音訊來源上啟用回音：

* 將 **音訊來源** 路由傳送至適當的 **群組**
* 設定 **Microsoft 空間定位器** 外掛程式，以將音訊傳遞到 **群組** 進行處理

在下列步驟中，您將調整腳本來控制音訊路由，並附加 **Microsoft 空間定位器** 外掛程式所提供的控制項腳本，將資料送入回送。

在階層中選取的 **四** 個步驟中，按一下 [偵測器] 視窗上的 [ **新增元件** ]，然後將 **房間效果的傳送層級 (腳本)**：

![新增傳送層級腳本](images/spatial-audio/spatial-audio-05-section2-step1-1.PNG)

> [!NOTE]
> 除非您啟用 **Microsoft 空間定位器** 外掛程式的 **房間效果傳送層級** 功能，否則它不會將任何音訊傳回至 Unity 音訊引擎以進行效果處理。

**房間效果傳送層級** 元件包含圖形控制項，可將傳送至 Unity 音訊引擎的音訊層級設定為進行回音處理。 若要開啟圖形控制項，請按一下 **房間效果傳送層級**。  按一下並向下拖曳綠色曲線，將層級設定為 [30dB]：

![調整回音曲線](images/spatial-audio/spatial-audio-05-section2-step1-2.PNG)

接下來，將 **SpatializeOnOff** 腳本中的4個批註行取消批註。 腳本現在看起來會像這樣：

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

這些行會取消批註之後，它會將兩個屬性新增至 **SpatializeOnOff 腳本** 的偵測器。 在 **四** 個 **SpatializeOnOff** 元件的 [偵測器] 視窗上指派這些資訊。

在階層中仍選取了四個物件時，在 [偵測器] 視窗中找到 **SpatializeOnOff 腳本** 元件和：

* 將 [ **會議室效果群組** ] 屬性設定為新的房間效果混音器群組
* 將 [ **主要群組** ] 屬性設定為主要混音器群組

![Spatialize 關閉擴充](images/spatial-audio/spatial-audio-05-section2-step1-3.PNG)

## <a name="congratulations"></a>恭喜！

您已完成適用于 Unity 的 HoloLens 2 空間音訊教學課程。 試用 HoloLens 2 或 Unity 上的應用程式。 當您按一下應用程式中的按鈕來啟動 spatialization 時，腳本會將影片的音訊路由傳送至房間效果群組，以新增回音。 切換至身歷聲時，會將音訊路由傳送至主要群組，並避免新增回音。

> [!TIP]
> 如需有關如何建立 Unity 專案並將其部署至 HoloLens 2 的提醒，您可以參閱[對您的 HoloLens 2 建置應用程式](mr-learning-base-02.md#building-your-application-to-your-hololens-2)的指示。
