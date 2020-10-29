---
title: Unity 中的焦點
description: 藉由設定焦點點，在 Unity 中手動調整全息圖穩定性
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Unity、聚焦點、焦點平面、穩定平面、穩定點、reprojection、LSR、深度緩衝區
ms.openlocfilehash: 4d8c8a232d12a8d6f0a7694fbc0ed8f66395163a
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2020
ms.locfileid: "91676914"
---
# <a name="focus-point-in-unity"></a>Unity 中的焦點

**命名空間：** *UnityEngine. XR*<br>
**類型** ： *HolographicSettings*

您可以設定 [焦點點](../platform-capabilities-and-apis/hologram-stability.md#reprojection) 來提供 HoloLens 提示，以提供有關如何在目前顯示的全像上執行穩定的提示。

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

請注意，上述的簡單程式碼可能會在焦點物件最後成為使用者的背後時，減少全像影像的穩定性。  這就是為什麼您通常應該設定「啟用深度緩衝區共用」，而不是以手動方式指定焦點點。

## <a name="next-development-checkpoint"></a>下一個開發檢查點

如果您要遵循我們所配置的 Unity 開發檢查點旅程，您將會在探索混合現實平臺功能和 Api。 您可以從這裡繼續進行下一個主題：

> [!div class="nextstepaction"]
> [追蹤遺失](tracking-loss-in-unity.md)

或直接跳到在裝置或模擬器上部署您的應用程式：

> [!div class="nextstepaction"]
> [部署到 HoloLens 或 Windows Mixed Reality 沉浸式耳機](../platform-capabilities-and-apis/using-visual-studio.md)

您隨時都可以回到 [Unity 開發檢查點](unity-development-overview.md#3-platform-capabilities-and-apis) 。

### <a name="see-also"></a>另請參閱
* [穩定平面](../platform-capabilities-and-apis/hologram-stability.md#reprojection)
