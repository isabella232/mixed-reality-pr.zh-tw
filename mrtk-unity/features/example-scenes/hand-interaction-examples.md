---
title: 手上互動範例
description: MRTK 中的手邊互動範例
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、手互動、界限控制、Pressable 按鈕、
ms.openlocfilehash: 7926c8bdd525af24a26e2f4c87257dca7628956a
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177438"
---
# <a name="hand-interaction-examples"></a><span data-ttu-id="4f9d7-104">手上互動範例</span><span class="sxs-lookup"><span data-stu-id="4f9d7-104">Hand interaction examples</span></span>

![手形互動範例1](../images/hand-interaction-examples/MRTK_HandInteractionExamples.png)

<span data-ttu-id="4f9d7-106">**HandInteractionExamples** 範例場景包含各種類型的互動和 UI 控制項，可反白顯示明確的手輸入。</span><span class="sxs-lookup"><span data-stu-id="4f9d7-106">The **HandInteractionExamples** example scene contains various types of interactions and UI controls that highlight articulated hand input.</span></span> <span data-ttu-id="4f9d7-107">使用 MRTK 的輸入模擬，您可以在 Unity 編輯器中體驗手動追蹤互動。</span><span class="sxs-lookup"><span data-stu-id="4f9d7-107">With MRTK's input simulation, you can experience hand-tracking interactions in Unity editor.</span></span> 

<span data-ttu-id="4f9d7-108">**HandInteractionExamples** 場景包含在 MRTK 的範例套件中。</span><span class="sxs-lookup"><span data-stu-id="4f9d7-108">**HandInteractionExamples** scene is included in the MRTK's Examples package.</span></span> <span data-ttu-id="4f9d7-109">您可以透過 [混合現實功能工具](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool)下載並匯入 **混合現實** 工具組範例套件</span><span class="sxs-lookup"><span data-stu-id="4f9d7-109">You can download and import **Mixed Reality Toolkit Examples** package through [Mixed Reality Feature Tool](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool)</span></span>

<img src="../images/hand-interaction-examples/MRTK_Examples_Package_MRFT.png" width="550" alt="Example Package 1"><br/>

<span data-ttu-id="4f9d7-110">在 Unity 中，使用功能表視窗 > Project > 自訂中封裝管理員 >，然後選取 [**混合的現實工具組範例**]。</span><span class="sxs-lookup"><span data-stu-id="4f9d7-110">In Unity, use the menu Window > Package Manager > In Project > Custom and select **Mixed Reality Toolkit Examples**.</span></span> <span data-ttu-id="4f9d7-111">按一下 [HandTracking] 旁 **的**[匯 **入] Project** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="4f9d7-111">Click **Import into Project** button next to **Demos - HandTracking**.</span></span> <span data-ttu-id="4f9d7-112">您將可以在 [資產 > 範例] 資料夾下找到 **HandInteractionExamples** 場景。</span><span class="sxs-lookup"><span data-stu-id="4f9d7-112">You will be able to find **HandInteractionExamples** scene under Assets > Samples folder.</span></span>

<img src="../images/hand-interaction-examples/MRTK_Examples_Package_2.png" width="300" alt="Example Package 2"><br/>

<img src="../images/hand-interaction-examples/MRTK_Examples_Package_3.png" width="650" alt="Example Package 3"><br/>

<img src="../images/hand-interaction-examples/MRTK_Examples_Package_4.png" width="650" alt="Example Package 4"><br/>

* <span data-ttu-id="4f9d7-113">如果您未使用混合的現實功能工具，您可以直接從 [MRTK GitHub 的 [發行] 頁面](https://github.com/microsoft/MixedRealityToolkit-Unity/releases)下載並匯入 **unitypackage** 。</span><span class="sxs-lookup"><span data-stu-id="4f9d7-113">If you don't use Mixed Reality Feature Tool, you can directly download and import **Microsoft.MixedReality.Toolkit.Unity.Examples.unitypackage** from [MRTK GitHub's release page](https://github.com/microsoft/MixedRealityToolkit-Unity/releases)</span></span>

> [!NOTE]
> <span data-ttu-id="4f9d7-114">這個範例場景會使用 *TextMesh Pro*。</span><span class="sxs-lookup"><span data-stu-id="4f9d7-114">This example scene uses *TextMesh Pro*.</span></span> <span data-ttu-id="4f9d7-115">若要開啟場景，請在匯入場景期間顯示個別的提示時，按一下 [匯 *入 TMP 基本* ]。</span><span class="sxs-lookup"><span data-stu-id="4f9d7-115">To open the scene, click *'Import TMP Essentials'* when the respective prompt is shown during the import of the scene.</span></span> <span data-ttu-id="4f9d7-116">Unity 接著會匯入 TextMesh Pro 套件。</span><span class="sxs-lookup"><span data-stu-id="4f9d7-116">Unity will then import TextMesh Pro packages.</span></span>

<img src="../images/hand-interaction-examples/MRTK_Examples_TMP2.png" width="450" alt="Example TMP2">



<span data-ttu-id="4f9d7-117">您可以在 **HandInteractionExamples** 場景中體驗這些元件</span><span class="sxs-lookup"><span data-stu-id="4f9d7-117">You can experience these components in **HandInteractionExamples** scene</span></span>

- [<span data-ttu-id="4f9d7-118">可點按的按鈕</span><span class="sxs-lookup"><span data-stu-id="4f9d7-118">Pressable button</span></span>](../ux-building-blocks/button.md)
- [<span data-ttu-id="4f9d7-119">界限控制項</span><span class="sxs-lookup"><span data-stu-id="4f9d7-119">Bounds control</span></span>](../ux-building-blocks/bounds-control.md)
- [<span data-ttu-id="4f9d7-120">物件操作工具</span><span class="sxs-lookup"><span data-stu-id="4f9d7-120">Object manipulator</span></span>](../ux-building-blocks/object-manipulator.md)
- [<span data-ttu-id="4f9d7-121">平板</span><span class="sxs-lookup"><span data-stu-id="4f9d7-121">Slate</span></span>](../ux-building-blocks/slate.md)
- [<span data-ttu-id="4f9d7-122">滑桿</span><span class="sxs-lookup"><span data-stu-id="4f9d7-122">Slider</span></span>](../ux-building-blocks/sliders.md)
- [<span data-ttu-id="4f9d7-123">系統鍵盤</span><span class="sxs-lookup"><span data-stu-id="4f9d7-123">System keyboard</span></span>](../ux-building-blocks/system-keyboard.md)
