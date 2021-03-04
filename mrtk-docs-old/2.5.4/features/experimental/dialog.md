---
title: 對話
description: 對話方塊控制項的描述。
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: 7c381cfd000d2f939889cffa8c4f2a47f0b4a2fe
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/03/2021
ms.locfileid: "101781431"
---
# <a name="dialog"></a>對話

![對話](../images/dialog/MRTK_UX_Dialog_Main.png)

對話方塊控制項是提供內容相關應用程式資訊的 UI 重迭。 而且它們通常會需要使用者執行某種動作。 使用對話方塊來通知使用者重要的資訊，或是在完成動作之前要求確認或其他資訊。

## <a name="example-scene"></a>範例場景

您可以在 **DialogExample** 場景的 [ [MRTK/範例]/[示範]/[UX/] 對話方塊](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MRTK/Examples/Demos/UX/Dialog)中找到範例。

## <a name="how-to-use-dialog-control"></a>如何使用對話方塊控制項

MRTK 提供三個對話方塊 prefabs：

- DialogSmall_192x96. 預製專案
- DialogMedium_192x128. 預製專案
- DialogLarge_192x192. 預製專案

使用對話方塊。開啟 () 以開啟新的對話方塊。 指定對話方塊預製專案、按鈕數目、標題文字、郵件內文、放置距離 (近或遠) 、其他變數) 。 對話方塊會提供「確認 (單一按鈕) 」和「選擇 (雙按鈕) 」對話方塊選項。

```c#
public static Dialog Open(GameObject dialogPrefab, DialogButtonType buttons, string title, string message, bool placeForNearInteraction, System.Object variable = null)
```

### <a name="example-of-opening-large-dialog-with-single-ok-button-placed-at-far-interaction-range-gaze-hand-ray-motion-controller"></a>以單一 [確定] 按鈕開啟大型對話的範例，放在最遠的互動範圍 (注視、手光線、移動控制器) 

```c#
Dialog.Open(DialogPrefabLarge, DialogButtonType.OK, "Confirmation Dialog, Large, Far", "This is an example of a large dialog with only one button, placed at far interaction range", false);
```

### <a name="example-of-opening-small-dialog-with-single-ok-button-placed-at-near-interaction-range-direct-hand-interaction"></a>以單一 [確定] 按鈕開啟小型對話的範例，放在接近互動範圍 (直接手互動) 

```c#
Dialog.Open(DialogPrefabSmall, DialogButtonType.Yes | DialogButtonType.No, "Confirmation Dialog, Small, Far", "This is an example of a small dialog with a choice message, placed at near interaction range", true);
```

如需詳細資訊，請參閱 `DialogExampleController.cs` DialogExample unity 場景。
