---
title: 對話
description: 對話方塊控制項的描述。
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: 729c3f6a6b9bc63a498c5d76205a0730f52c678a
ms.sourcegitcommit: e89431d12b5fe480c9bc40e176023798fc35001b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2021
ms.locfileid: "109489188"
---
# <a name="dialog"></a><span data-ttu-id="2f88d-104">對話</span><span class="sxs-lookup"><span data-stu-id="2f88d-104">Dialog</span></span>

![對話](../images/dialog/MRTK_UX_Dialog_Main.png)

<span data-ttu-id="2f88d-106">對話方塊控制項是提供內容相關應用程式資訊的 UI 重迭。</span><span class="sxs-lookup"><span data-stu-id="2f88d-106">Dialog controls are UI overlays that provide contextual app information.</span></span> <span data-ttu-id="2f88d-107">而且它們通常會需要使用者執行某種動作。</span><span class="sxs-lookup"><span data-stu-id="2f88d-107">They often request some kind of action from the user.</span></span> <span data-ttu-id="2f88d-108">使用對話方塊來通知使用者重要的資訊，或是在完成動作之前要求確認或其他資訊。</span><span class="sxs-lookup"><span data-stu-id="2f88d-108">Use dialogs to notify users of important information or to request confirmation or additional info before an action can be completed.</span></span>

## <a name="example-scene"></a><span data-ttu-id="2f88d-109">範例場景</span><span class="sxs-lookup"><span data-stu-id="2f88d-109">Example scene</span></span>

<span data-ttu-id="2f88d-110">您可以在 **DialogExample** 場景的 [ [MRTK/範例]/[示範]/[UX/] 對話方塊](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/Examples/Demos/UX/Dialog)中找到範例。</span><span class="sxs-lookup"><span data-stu-id="2f88d-110">You can find examples in the **DialogExample** scene under: [MRTK/Examples/Demo/UX/Dialog](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/Examples/Demos/UX/Dialog)</span></span>

## <a name="how-to-use-dialog-control"></a><span data-ttu-id="2f88d-111">如何使用對話方塊控制項</span><span class="sxs-lookup"><span data-stu-id="2f88d-111">How to use Dialog control</span></span>

<span data-ttu-id="2f88d-112">MRTK 提供三個對話方塊 prefabs：</span><span class="sxs-lookup"><span data-stu-id="2f88d-112">MRTK provides three Dialog prefabs:</span></span>

- <span data-ttu-id="2f88d-113">DialogSmall_192x96. 預製專案</span><span class="sxs-lookup"><span data-stu-id="2f88d-113">DialogSmall_192x96.prefab</span></span>
- <span data-ttu-id="2f88d-114">DialogMedium_192x128. 預製專案</span><span class="sxs-lookup"><span data-stu-id="2f88d-114">DialogMedium_192x128.prefab</span></span>
- <span data-ttu-id="2f88d-115">DialogLarge_192x192. 預製專案</span><span class="sxs-lookup"><span data-stu-id="2f88d-115">DialogLarge_192x192.prefab</span></span>

<span data-ttu-id="2f88d-116">使用對話方塊。開啟 () 以開啟新的對話方塊。</span><span class="sxs-lookup"><span data-stu-id="2f88d-116">Use Dialog.Open() to open a new dialog.</span></span> <span data-ttu-id="2f88d-117">指定對話方塊預製專案、按鈕數目、標題文字、郵件內文、放置距離 (近或遠) 、其他變數) 。</span><span class="sxs-lookup"><span data-stu-id="2f88d-117">Specify the dialog prefab, number of buttons, title text, message text, placement distance(near or far), additional variables).</span></span> <span data-ttu-id="2f88d-118">對話方塊會提供「確認 (單一按鈕) 」和「選擇 (雙按鈕) 」對話方塊選項。</span><span class="sxs-lookup"><span data-stu-id="2f88d-118">Dialog provides 'Confirmation(single button)' and 'Choice(two-buttons)' dialog options.</span></span>

```c#
public static Dialog Open(GameObject dialogPrefab, DialogButtonType buttons, string title, string message, bool placeForNearInteraction, System.Object variable = null)
```

### <a name="example-of-opening-a-large-dialog-with-a-single-ok-button-placed-at-far-interaction-range-gaze-hand-ray-motion-controller"></a><span data-ttu-id="2f88d-119">開啟具有單一 [確定] 按鈕的大型對話範例，放在最遠的互動範圍 (注視、手光線、移動控制器) </span><span class="sxs-lookup"><span data-stu-id="2f88d-119">Example of opening a Large dialog with a single 'OK' button, placed at far interaction range (gaze, hand ray, motion controller)</span></span>

```c#
Dialog.Open(DialogPrefabLarge, DialogButtonType.OK, "Confirmation Dialog, Large, Far", "This is an example of a large dialog with only one button, placed at far interaction range", false);
```

### <a name="example-of-opening-a-small-dialog-containing-a-choice-message-for-the-user-placed-at-near-interaction-range-direct-hand-interaction"></a><span data-ttu-id="2f88d-120">開啟包含使用者選擇訊息的小型對話範例，放在接近互動範圍 (直接操作) </span><span class="sxs-lookup"><span data-stu-id="2f88d-120">Example of opening a Small dialog containing a choice message for the user, placed at near interaction range (direct hand interaction)</span></span>

```c#
Dialog.Open(DialogPrefabSmall, DialogButtonType.Yes | DialogButtonType.No, "Confirmation Dialog, Small, Near", "This is an example of a small dialog with a choice message, placed at near interaction range", true);
```

<span data-ttu-id="2f88d-121">如需詳細資訊，請參閱 `DialogExampleController.cs` DialogExample unity 場景。</span><span class="sxs-lookup"><span data-stu-id="2f88d-121">For more details, please see `DialogExampleController.cs` in DialogExample.unity scene.</span></span>
