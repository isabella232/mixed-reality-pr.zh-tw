---
title: Unity 中的焦點
description: 瞭解如何藉由設定 HoloLens 的焦點點以及 Windows Mixed Reality 的沉浸式耳機，以手動調整 Unity 中的全像影像穩定性。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Unity、聚焦點、焦點平面、穩定平面、穩定點、reprojection、LSR、深度緩衝區、混合現實耳機、windows mixed reality 耳機、虛擬實境耳機
ms.openlocfilehash: 2ceb5f2b58cbd1571b2d9f4de79acfe45779bfea
ms.sourcegitcommit: be7473bbebc1872d8c9df6f2da837efd3279dee6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/15/2021
ms.locfileid: "98226397"
---
# <a name="focus-point-in-unity"></a>Unity 中的焦點

**命名空間：** *UnityEngine. XR*<br>
**類型**： *HolographicSettings*

使用 [焦點](../platform-capabilities-and-apis/hologram-stability.md#reprojection) 來提供 HoloLens，並提供有關如何最好穩定目前顯示的全像投影的提示。

如果您想要在 Unity 中設定焦點點，則必須使用 *HolographicSettings. SetFocusPointForFrame ( # B1* 來設定每個框架。 如果未設定框架的焦點點，則會使用預設穩定平面。

> [!NOTE]
> 依預設，新的 Unity 專案會設定「啟用深度緩衝區共用」選項。  使用此選項時，在沉浸式桌上型耳機或執行 Windows 10 2018 年4月更新 (RS4) 或更新版本的 HoloLens 上執行的 Unity 應用程式，會將您的深度緩衝區提交至 Windows，以自動優化全像影像穩定性，而不需要您的應用程式指定焦點點：
> * 在沉浸式桌面耳機上，這會啟用依圖元深度為基礎的 reprojection。
> * 在執行 Windows 10 2018 年4月更新或更新版本的 HoloLens 上，這會分析深度緩衝區以自動挑選最佳的穩定平面。
>
> 這兩種方法都應提供更佳的影像品質，而不會讓您的應用程式明確地為每個畫面格選取焦點點。  請注意，如果您要以手動方式提供焦點，這將會覆寫上述的自動行為，而且通常會減少全像全像全像是。  一般而言，當您的應用程式是在尚未更新為 Windows 10 2018 年4月更新的 HoloLens 上執行時，您應該只指定手動焦點點。

### <a name="example"></a>範例

有許多方式可以設定焦點點，如 *SetFocusPointForFrame* 靜態函式上提供的多載所建議。 以下是一個簡單的範例，可將焦點平面設定為每個框架所提供的物件：

```cs
public GameObject focusedObject;
void Update()
{
    // Normally the normal is best set to be the opposite of the main camera's
    // forward vector.
    // If the content is actually all on a plane (like text), set the normal to
    // the normal of the plane and ensure the user does not pass through the
    // plane.
    var normal = -Camera.main.transform.forward;     
    var position = focusedObject.transform.position;
    UnityEngine.XR.WSA.HolographicSettings.SetFocusPointForFrame(position, normal);
}
```

> [!NOTE]
> 上述的簡單程式碼可能會降低全像物件在使用者背後的焦點物件的穩定性。 我們通常會建議您設定 **[啟用深度緩衝區共用](camera-in-unity.md#sharing-your-depth-buffers-with-windows)** ，而不是手動指定焦點點。

## <a name="next-development-checkpoint"></a>下一個開發檢查點

如果您正在遵循我們所配置的 Unity 開發旅程圖，您將會在探索混合現實平臺功能和 Api。 接下來，您可以繼續進行下一個主題：

> [!div class="nextstepaction"]
> [追蹤遺失](tracking-loss-in-unity.md)

或者，直接跳到在裝置或模擬器上部署應用程式的主題：

> [!div class="nextstepaction"]
> [部署到 HoloLens 或 Windows Mixed Reality 沉浸式耳機](../platform-capabilities-and-apis/using-visual-studio.md)

您可以隨時回到 [Unity 開發檢查點](unity-development-overview.md#3-advanced-features)。

### <a name="see-also"></a>另請參閱

* [穩定平面](../platform-capabilities-and-apis/hologram-stability.md#reprojection)
