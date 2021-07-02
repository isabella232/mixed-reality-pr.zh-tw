---
title: 眼睛和手
description: 如何搭配 MRTK 中的手運動使用眼睛目標作為主要指標
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、EyeTracking、
ms.openlocfilehash: ff464c6f2381a9df020a9ccf807672d4463d662c
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175115"
---
# <a name="eyes-and-hands"></a>眼睛和手

## <a name="how-to-support-_look--hand-motions_-eye-gaze--hand-gestures"></a>如何支援 _外觀 + 手運動_ (眼睛 & 手勢) 

此頁面說明如何使用眼睛目標作為與手運動組合的主要指標。
在我們的 [MRTK 眼追蹤示範](../../example-scenes/eye-tracking-examples-overview.md)中，我們會說明使用眼睛 + 手的數個範例，例如：

- [選擇](eye-tracking-target-selection.md)：查看遙遠的全像全像，然後執行縮小的手勢來快速選取它。
- **(本文的定位)**：流暢在您的場景中移動全像，只要查看一下，就可以捏合您的食指，然後將它放在一起來抓取，然後使用您的手四處移動。
- [導覽](eye-tracking-navigation.md)：只需查看您想要放大的位置，並將您的索引手指與 thumb 一起放大 _，並朝_ 您手上一步。

請注意，MRTK 目前的設計方式，是以距離光線作為優先的焦點指標。
這表示當偵測到手邊時，即會自動隱藏 head 和眼睛的指標，並在表示「選取」之後再次顯示。
不過，這可能不是您想要在某處互動的方式，而是比您的觀點來看單純的「 _注視和認可_ 」互動。

### <a name="how-to-disable-the-hand-ray"></a>如何停用手光線

若要停用手光線指標，只要移除 _輸入 > 指標_ MRTK 設定中的 _' DefaultControllerPointer '_ 。
若要在您的應用程式中使用眼睛和手（如上所述），也請確定您符合 [使用眼睛追蹤](eye-tracking-basic-setup.md)的所有需求。

![如何卸下手光線](../../images/eye-tracking/mrtk_setup_removehandray.jpg)

您也可以查看，從眼睛追蹤範例套件 _EyeTrackingDemoPointerProfile_ 的輸入設定檔如何設定為參考。

### <a name="how-to-keep-gaze-pointer-always-on"></a>如何保持注視指標永遠開啟

若要避免在偵測到手邊時自動抑制前端或眼睛指標，請指定眼睛 [`PointerBehavior`](xref:Microsoft.MixedReality.Toolkit.Input.PointerBehavior) 來控制是否應該開啟或關閉。

```c#
// Turn on gaze pointer
PointerUtils.SetGazePointerBehavior(PointerBehavior.AlwaysOn);
```

請參閱 [`Controllers Pointers and Focus`](../../../architecture/controllers-pointers-and-focus.md)

---
[回到「MixedRealityToolkit 中的眼睛追蹤」](eye-tracking-main.md)
