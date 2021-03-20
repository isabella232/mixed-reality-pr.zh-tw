---
title: 對話
description: 對話方塊控制項的描述。
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: aa054e304640ece2ee7346fc573ef869946c8905
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104681411"
---
# <a name="dialog"></a><span data-ttu-id="a599b-104">對話</span><span class="sxs-lookup"><span data-stu-id="a599b-104">Dialog</span></span>

![對話](../../images/dialog/MRTK_UX_Dialog_Main.png)

<span data-ttu-id="a599b-106">對話方塊控制項是提供內容相關應用程式資訊的 UI 重迭。</span><span class="sxs-lookup"><span data-stu-id="a599b-106">Dialog controls are UI overlays that provide contextual app information.</span></span> <span data-ttu-id="a599b-107">而且它們通常會需要使用者執行某種動作。</span><span class="sxs-lookup"><span data-stu-id="a599b-107">They often request some kind of action from the user.</span></span> <span data-ttu-id="a599b-108">使用對話方塊來通知使用者重要的資訊，或是在完成動作之前要求確認或其他資訊。</span><span class="sxs-lookup"><span data-stu-id="a599b-108">Use dialogs to notify users of important information or to request confirmation or additional info before an action can be completed.</span></span>

## <a name="example-scene"></a><span data-ttu-id="a599b-109">範例場景</span><span class="sxs-lookup"><span data-stu-id="a599b-109">Example scene</span></span>

<span data-ttu-id="a599b-110">您可以在 **DialogExample** 場景的 [ [MRTK/範例/實驗/] 對話方塊](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MRTK/SDK/Experimental/Dialog)中找到範例。</span><span class="sxs-lookup"><span data-stu-id="a599b-110">You can find examples in the **DialogExample** scene under: [MRTK/Examples/Experimental/Dialog](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MRTK/SDK/Experimental/Dialog)</span></span>

## <a name="how-to-use-dialog-control"></a><span data-ttu-id="a599b-111">如何使用對話方塊控制項</span><span class="sxs-lookup"><span data-stu-id="a599b-111">How to use Dialog control</span></span>

<span data-ttu-id="a599b-112">MRTK 提供三個對話方塊 prefabs：</span><span class="sxs-lookup"><span data-stu-id="a599b-112">MRTK provides three Dialog prefabs:</span></span>

- <span data-ttu-id="a599b-113">DialogSmall_192x96. 預製專案</span><span class="sxs-lookup"><span data-stu-id="a599b-113">DialogSmall_192x96.prefab</span></span>
- <span data-ttu-id="a599b-114">DialogMedium_192x128. 預製專案</span><span class="sxs-lookup"><span data-stu-id="a599b-114">DialogMedium_192x128.prefab</span></span>
- <span data-ttu-id="a599b-115">DialogLarge_192x192. 預製專案</span><span class="sxs-lookup"><span data-stu-id="a599b-115">DialogLarge_192x192.prefab</span></span>

<span data-ttu-id="a599b-116">使用對話方塊。開啟 () 以開啟新的對話方塊。</span><span class="sxs-lookup"><span data-stu-id="a599b-116">Use Dialog.Open() to open a new dialog.</span></span> <span data-ttu-id="a599b-117">指定對話方塊預製專案、按鈕數目、標題文字、郵件內文、放置距離 (近或遠) 、其他變數) 。</span><span class="sxs-lookup"><span data-stu-id="a599b-117">Specify the dialog prefab, number of buttons, title text, message text, placement distance(near or far), additional variables).</span></span> <span data-ttu-id="a599b-118">對話方塊會提供「確認 (單一按鈕) 」和「選擇 (雙按鈕) 」對話方塊選項。</span><span class="sxs-lookup"><span data-stu-id="a599b-118">Dialog provides 'Confirmation(single button)' and 'Choice(two-buttons)' dialog options.</span></span>

```c#
public static Dialog Open(GameObject dialogPrefab, DialogButtonType buttons, string title, string message, bool placeForNearInteraction, System.Object variable = null)
```

### <a name="example-of-opening-large-dialog-with-single-ok-button-placed-at-far-interaction-range-gaze-hand-ray-motion-controller"></a><span data-ttu-id="a599b-119">以單一 [確定] 按鈕開啟大型對話的範例，放在最遠的互動範圍 (注視、手光線、移動控制器) </span><span class="sxs-lookup"><span data-stu-id="a599b-119">Example of opening Large dialog with single 'OK' button, placed at far interaction range (gaze, hand ray, motion controller)</span></span>

```c#
Dialog.Open(DialogPrefabLarge, DialogButtonType.OK, "Confirmation Dialog, Large, Far", "This is an example of a large dialog with only one button, placed at far interaction range", false);
```

### <a name="example-of-opening-small-dialog-with-single-ok-button-placed-at-near-interaction-range-direct-hand-interaction"></a><span data-ttu-id="a599b-120">以單一 [確定] 按鈕開啟小型對話的範例，放在接近互動範圍 (直接手互動) </span><span class="sxs-lookup"><span data-stu-id="a599b-120">Example of opening Small dialog with single 'OK' button, placed at near interaction range (direct hand interaction)</span></span>

```c#
Dialog.Open(DialogPrefabSmall, DialogButtonType.Yes | DialogButtonType.No, "Confirmation Dialog, Small, Far", "This is an example of a small dialog with a choice message, placed at near interaction range", true);
```

<span data-ttu-id="a599b-121">如需詳細資訊，請參閱 `DialogExampleController.cs` DialogExample unity 場景。</span><span class="sxs-lookup"><span data-stu-id="a599b-121">For more details, please see `DialogExampleController.cs` in DialogExample.unity scene.</span></span>
