---
title: EyeTracking_EyesAndHands
description: 如何搭配 MRTK 中的手運動使用眼睛目標作為主要指標
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
ms.localizationpriority: medium
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、EyeTracking、
ms.openlocfilehash: e3436bb361f0407c8a3b7a57cdf5f52f2a9a910a
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104690865"
---
# <a name="eyes--hand-interaction"></a>眼睛 + 手互動

## <a name="how-to-support-_look--hand-motions_-eye-gaze--hand-gestures"></a>如何支援 _外觀 + 手運動_ (眼睛 & 手勢) 

此頁面說明如何使用眼睛目標作為與手運動組合的主要指標。
在我們的 [MRTK 眼追蹤示範](EyeTracking_ExamplesOverview.md)中，我們會說明使用眼睛 + 手的數個範例，例如：

- [選擇](EyeTracking_TargetSelection.md)：查看遙遠的全像全像，然後執行縮小的手勢來快速選取它。
- [定位](EyeTracking_Positioning.md)：流暢在您的場景中移動全像投影、捏合您的食指和 thumb 以抓取，然後使用您的手四處移動。
- [導覽](EyeTracking_Navigation.md)：只需查看您想要放大的位置，並將您的索引手指與 thumb 一起放大 _，並朝_ 您手上一步。

請注意，MRTK 目前的設計方式，是以距離光線作為優先的焦點指標。
這表示在偵測到手上時，就會自動隱藏 head 和眼睛的指標。
不過，這可能不是您想要在某處互動的方式，而是比您的觀點來看單純的「 _注視和認可_ 」互動。

### <a name="how-to-disable-the-hand-ray"></a>如何停用手光線

若要停用手光線指標，只要移除 _輸入 > 指標_ MRTK 設定中的 _' DefaultControllerPointer '_ 。
若要在您的應用程式中使用眼睛和手（如上所述），也請確定您符合 [使用眼睛追蹤](EyeTracking_BasicSetup.md)的所有需求。

![如何卸下手光線](../Images/EyeTracking/mrtk_setup_removehandray.jpg)

您也可以查看，從眼睛追蹤範例套件 _EyeTrackingDemoPointerProfile_ 的輸入設定檔如何設定為參考。

---
[回到「MixedRealityToolkit 中的眼睛追蹤」](EyeTracking_Main.md)
