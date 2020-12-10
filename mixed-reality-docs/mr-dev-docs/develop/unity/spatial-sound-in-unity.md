---
title: Unity 中的空間音效
description: 從 Unity 場景內的特定3D 點播放空間音效。
author: kegodin
ms.author: v-hferrone
ms.date: 11/07/2019
ms.topic: article
keywords: Unity、空間音效、HRTF、房間大小、混合現實耳機、windows mixed reality 耳機、虛擬實境耳機、MRTK、混合現實工具組、空間定位器、回音
ms.openlocfilehash: 1efe287855cc5b7738069c6d8183c2ecb5bd6d59
ms.sourcegitcommit: 87b54c75044f433cfadda68ca71c1165608e2f4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "97010139"
---
# <a name="spatial-sound-in-unity"></a>Unity 中的空間音效

此頁面會連結至 Unity 中空間音效的資源。

## <a name="spatializer-options"></a>空間定位器選項
混合現實應用程式的空間定位器選項包括：
* Unity 提供 *MS HRTF 空間定位器* 做為 *Windows Mixed Reality* 選用套件的一部分。
  * 以較高成本的「單一來源」架構在 CPU 上執行。
  * 提供與原始 HoloLens 應用程式的回溯相容性。
* Microsoft *空間定位器* 可從 [microsoft 空間定位器 GitHub 存放庫](https://github.com/microsoft/spatialaudio-unity)取得。
  * 使用較低成本的「多來源」架構。
  * 卸載 HoloLens 2 上的硬體加速器。 

針對新的應用程式，我們建議 *Microsoft 空間定位器*。

## <a name="enable-spatialization"></a>啟用 spatialization

使用 [適用于 unity 的 NuGet](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest) 來安裝 _SpatialAudio 空間定位器_ ，並在專案的 [音訊] 設定中選擇 [ **microsoft 空間定位器** ]。 然後：
* 將 **音訊來源** 附加至階層中的物件
* 勾選 [ **啟用 spatialization** ] 核取方塊
* 將 **空間 Blend** 滑杆移至 ' 1 '
* 確定您的開發人員工作站上已啟用空間音訊。 
    * 以滑鼠右鍵按一下工作列中的音量圖示，並確定 [空間音效] 設定為 [關閉] 以外的地方。 
    * 選擇 **耳機用 Windows Sonic** ，以取得您將在 HoloLens 2 上聽到的最大表現。

>[!NOTE]
>如果您在 Unity 中收到錯誤，指出無法載入外掛程式 SpatialAudio，因為其中一個相依性遺失，請確認您的電腦上已安裝最新版的 [Microsoft Visual C++](https://support.microsoft.com/en-us/help/2977003/the-latest-supported-visual-c-downloads) 可轉散發套件。

如需詳細資訊，請參閱
* [Microsoft 空間定位器 GitHub 存放庫](https://github.com/microsoft/spatialaudio-unity)
* [Microsoft 的空間定位器教學課程](tutorials/unity-spatial-audio-ch1.md)
* [Unity 的音訊來原始檔案](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html)
* [Unity 的空間定位器檔](https://docs.unity3d.com/Manual/VRAudioSpatializer.html)

## <a name="distance-based-attenuation"></a>距離型衰減
Unity 的預設距離為基礎的衰減最小距離為1個計量，最大距離為500計量，並具有對數 rolloff。 這些設定可能適用于您的案例，或者您可能會發現來源 attenuate 太快或太慢。 如需詳細資訊，請參閱
* 適用于建議設定的[混合現實音效設計](../../design/spatial-sound-design.md)。
* [Unity 的音訊來原始檔案](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html) ，以取得設定這些曲線的指示。

## <a name="reverb"></a>混響
根據預設， _Microsoft 空間定位器_ 會停用空間定位器後的效果。 若要啟用 hrtf 來源的回音和其他效果：
* 將 **會議室效果的傳送層級** 元件附加至每個來源
* 調整每個來源的傳送層級曲線，以控制傳送回圖形以進行效果處理的音訊增益

如需詳細資訊，請參閱 [空間定位器教學課程的第5章](tutorials/unity-spatial-audio-ch5.md) 。

## <a name="unity-spatial-sound-examples"></a>Unity 空間音效範例
如需 Unity 中空間音效的範例，請參閱：
* [MRTK 示範](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.Examples/Demos/Audio)
* [Microsoft 空間定位器範例專案](https://github.com/microsoft/spatialaudio-unity/tree/master/Samples/MicrosoftSpatializerSample)

## <a name="next-development-checkpoint"></a>下一個開發檢查點

如果您遵循我們所配置的 Unity 開發旅程圖，就會在探索 Mixed Reality 核心構成要素。 您可以從這裡繼續進行下一個組建區塊：

> [!div class="nextstepaction"]
> [Text](text-in-unity.md)

或者，直接跳到混合實境平台功能和 API 的主題：

> [!div class="nextstepaction"]
> [共用體驗](shared-experiences-in-unity.md)

您可以隨時回到 [Unity 開發檢查點](unity-development-overview.md#2-core-building-blocks)。

## <a name="see-also"></a>另請參閱
* [混合現實的音效設計](../../design/spatial-sound-design.md)
* [Microsoft 的空間定位器教學課程](tutorials/unity-spatial-audio-ch1.md)
