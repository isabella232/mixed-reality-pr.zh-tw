---
title: Unity 的輸入移植指南
description: 瞭解如何在 Unity 中處理 Windows Mixed Reality 的輸入。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: 輸入、unity、移植
ms.openlocfilehash: 4ad4b66b8238b3d00142fd14161113c6b912641c
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2020
ms.locfileid: "91679092"
---
# <a name="input-porting-guide-for-unity"></a>Unity 的輸入移植指南

您可以使用下列兩種方法之一來將輸入邏輯移植到 Windows Mixed Reality： Unity 的一般輸入。跨多個平臺的 GetButton/GetAxis Api，或 Windows 特定的 XR。Wsa。輸入 Api，專為運動控制器和 HoloLens 手提供更豐富的資料。

## <a name="general-inputgetbuttongetaxis-apis"></a>一般輸入. GetButton/GetAxis Api

Unity 目前使用其一般輸入. GetButton/GetAxis Api 來公開 [OCULUS SDK](https://docs.unity3d.com/Manual/OculusControllers.html) 和 [OpenVR SDK](https://docs.unity3d.com/Manual/OpenVRControllers.html)的輸入。 如果您的應用程式已經使用這些 Api 進行輸入，這是在 Windows Mixed Reality 中支援移動控制器最簡單的路徑：您應該只需要重新對應輸入管理員中的按鈕和軸。

如需詳細資訊，請參閱 [unity 按鈕/軸對應表](../unity/gestures-and-motion-controllers-in-unity.md#unity-buttonaxis-mapping-table) 和 [通用 Unity api 的總覽](../unity/gestures-and-motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis)。

## <a name="windows-specific-xrwsainput-apis"></a>Windows 特定 XR。Wsa。輸入 Api

如果您的應用程式已經為每個平臺建立自訂輸入邏輯，您可以選擇使用 **UnityEngine. XR** 命名空間底下的 Windows 特定空間輸入 api。 這可讓您存取額外的資訊，例如位置精確度或來源種類，讓您可以在 HoloLens 上分辨手和控制器。

如需詳細資訊，請參閱 [UnityEngine. XR. 輸入 api 的總覽](../unity/gestures-and-motion-controllers-in-unity.md#windows-specific-apis-xrwsainput)。

## <a name="grip-pose-vs-pointing-pose"></a>底姿勢與指標姿勢

Windows Mixed Reality 支援各種外型規格中的運動控制器，每個控制器的設計各有不同之處，就是使用者的位置與應用程式在轉譯控制器時應使用的自然「向前」方向之間的關聯性。

為了更妥善地表示這些控制器，您可以針對每個互動來源進行兩種調查：

* 底框 **姿勢** ，代表 HoloLens 所偵測到之掌上的位置，或是持有運動控制器的掌上。
    * 在沉浸式耳機上，這個姿勢最適合用 **來呈現使用者手** 或 **使用者手中所持有的物件** ，例如寶劍或機槍。
    * 把手 **位置** ：自然地按住控制器時的棕櫚距心，向左或向右調整以將位置置中置中。
    * 底 **圖方向的右軸** ：當您完全開啟手來形成平面的5形姿勢時，您的掌上光 (的光線會從左至右向前復原，從右邊的棕櫚) 
    * 底圖 **方向的向前軸** ：當您關閉手部分 (時，如同按住控制器) 一樣，也就是由非拇指手指所形成的電子管「轉寄」的光線。
    * 底圖 **方向的向上軸** ：右邊和向前定義所隱含的向上軸。
    * 您可以透過 Unity 的跨廠商輸入 API (XR 來存取抓住姿勢 **[。InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)。GetLocalPosition/輪替** ) 或透過 Windows 特定 API ( **SourceState. SourcePose. TryGetPosition/旋轉** ，要求底框姿勢) 。
* **指標姿勢** ，代表指向轉寄之控制器的秘訣。
    * 當您在呈現控制器模型本身時 **指向 UI** 時，最好使用這個姿勢來 raycast。
    * 目前，指標姿勢只能透過 Windows 特定 API 來使用 ( **sourceState. sourcePose. TryGetPosition/旋轉** ，要求指標姿勢) 。

這些姿勢座標全都以 Unity 全局座標表示。

## <a name="see-also"></a>另請參閱
* [移動控制器]().。。/../design/motion-controllers.md) 
* [Unity 中的筆勢和運動控制器](../unity/gestures-and-motion-controllers-in-unity.md)
* [UnityEngine. XR。輸入](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.html)
* [UnityEngine. XR. InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)
* [移植指南](porting-guides.md)
