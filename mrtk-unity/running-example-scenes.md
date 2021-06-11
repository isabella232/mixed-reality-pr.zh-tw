---
title: 執行範例場景
description: 瞭解如何取得和使用 MRTK 的範例場景。
author: cre8ivepark
ms.author: dongpark
ms.date: 06/07/2021
ms.topic: article
keywords: 混合現實工具組、MRTK、範例、HoloLens、HoloLens 2、著色器、工具提示、手互動、剪輯、周框方塊、按鈕、手形功能表、平板、滑杆
ms.openlocfilehash: 8ba4df237189f0de3bd869bc05bdf7e3c5451490
ms.sourcegitcommit: 2f69fb62eb81f91e655d7b55306b0550a1162496
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/10/2021
ms.locfileid: "111911860"
---
# <a name="example-scenes"></a><span data-ttu-id="19a36-104">範例場景</span><span class="sxs-lookup"><span data-stu-id="19a36-104">Example scenes</span></span>

<span data-ttu-id="19a36-105">MRTK 提供各種類型的範例場景，可示範 MRTK 的功能，以及空間使用者體驗的建立區塊。</span><span class="sxs-lookup"><span data-stu-id="19a36-105">MRTK provides various types of example scenes that demonstrate MRTK's features and building blocks for spatial user experience.</span></span> <span data-ttu-id="19a36-106">遇到並剖析範例場景可能有助於瞭解這些功能，並將其套用至您的專案。</span><span class="sxs-lookup"><span data-stu-id="19a36-106">Experiencing and dissecting example scenes could be helpful to understand the features and apply them to your projects.</span></span> 

## <a name="how-to-acquire-example-scenes"></a><span data-ttu-id="19a36-107">如何取得範例場景</span><span class="sxs-lookup"><span data-stu-id="19a36-107">How to acquire example scenes</span></span>

### <a name="using-mixed-reality-feature-tool-and-unity-package-manager"></a><span data-ttu-id="19a36-108">使用混合現實功能工具和 Unity 套件管理員</span><span class="sxs-lookup"><span data-stu-id="19a36-108">Using Mixed Reality Feature Tool and Unity package manager</span></span>

<span data-ttu-id="19a36-109">您可以透過 [混合現實功能工具](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool)下載並匯入 **混合現實** 工具組範例套件</span><span class="sxs-lookup"><span data-stu-id="19a36-109">You can download and import **Mixed Reality Toolkit Examples** package through [Mixed Reality Feature Tool](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool)</span></span>

<img src="features/images/hand-interaction-examples/MRTK_Examples_Package_MRFT.png" width="550" alt="Example Package 1"><br/>

<span data-ttu-id="19a36-110">在 Unity 中，使用功能表 **視窗 > 專案中的封裝管理員 > > 自訂** ，並選取 **混合的現實工具組範例**。</span><span class="sxs-lookup"><span data-stu-id="19a36-110">In Unity, use the menu **Window > Package Manager > In Project > Custom** and select **Mixed Reality Toolkit Examples**.</span></span> 

<img src="features/images/hand-interaction-examples/MRTK_Examples_Package_2.png" width="300" alt="Example Package 2"><br/>

<span data-ttu-id="19a36-111">從面板右邊的清單中，按一下範例場景名稱旁邊的 [匯 **入專案** ] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="19a36-111">From the list on the right side of the panel, click **Import into Project** button next to the example scene names.</span></span>  <span data-ttu-id="19a36-112">例如，您可以按一下 [**示範-HandTracking**] 旁邊的 [匯 **入專案**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="19a36-112">For example, you can click **Import into Project** button next to **Demos - HandTracking**.</span></span> 

<img src="features/images/hand-interaction-examples/MRTK_Examples_Package_3.png" width="650" alt="Example Package 3"><br/>

<span data-ttu-id="19a36-113">匯入之後，您就可以在 [ **資產 > 範例** ] 資料夾下找到它們。</span><span class="sxs-lookup"><span data-stu-id="19a36-113">Once imported, you will be able to find them under **Assets > Samples** folder.</span></span>
<span data-ttu-id="19a36-114">**HandInteractionExamples** 場景是開始遇到 MRTK 空間互動和 UI 構成組塊的絕佳位置。</span><span class="sxs-lookup"><span data-stu-id="19a36-114">**HandInteractionExamples** scene is a great place to start experiencing MRTK's spatial interactions and UI building blocks.</span></span>

<img src="features/images/hand-interaction-examples/MRTK_Examples_Package_4.png" width="650" alt="Example Package 4"><br/>

### <a name="directly-downloading-and-importing-packages-from-github"></a><span data-ttu-id="19a36-115">直接從 GitHub 下載並匯入套件</span><span class="sxs-lookup"><span data-stu-id="19a36-115">Directly downloading and importing packages from GitHub</span></span>

<span data-ttu-id="19a36-116">如果您未使用混合的現實功能工具，您可以直接從 [MRTK GitHub 的 [發行] 頁面](https://github.com/microsoft/MixedRealityToolkit-Unity/releases)下載並匯入 **MixedReality unitypackage** 。</span><span class="sxs-lookup"><span data-stu-id="19a36-116">If you don't use Mixed Reality Feature Tool, you can directly download and import **Microsoft.MixedReality.Toolkit.Unity.Examples.unitypackage** from [MRTK GitHub's release page](https://github.com/microsoft/MixedRealityToolkit-Unity/releases)</span></span>

<span data-ttu-id="19a36-117">使用 **資產 > 匯入套件 > 自訂套件** 功能表匯入已下載的 unitypackage。</span><span class="sxs-lookup"><span data-stu-id="19a36-117">Use **Assets > Import Package > Custom Package** menu to import downloaded .unitypackage.</span></span> <span data-ttu-id="19a36-118">匯入之後，您就可以在 [資產] 下找到範例場景 **> MRTK > 範例 > 示範**。</span><span class="sxs-lookup"><span data-stu-id="19a36-118">Once it is imported, you will be able to find example scenes under **Assets > MRTK > Examples > Demos**.</span></span>

<img src="features/images/hand-interaction-examples/MRTK_Examples_Package_Manual1.png" width="650" alt="Example Manual 1"><br/>

<img src="features/images/hand-interaction-examples/MRTK_Examples_Package_Manual2.png" width="650" alt="Example Manual 2"><br/>