---
title: README_HandJointChaser
description: MRTK 中的手聯合 chaser
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: 2417cf9c7710ef626d289089e4adc0635d983722
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/03/2021
ms.locfileid: "101779672"
---
# <a name="hand-joint-chaser-example"></a><span data-ttu-id="63002-104">手聯合 chaser 範例</span><span class="sxs-lookup"><span data-stu-id="63002-104">Hand joint chaser example</span></span>

<span data-ttu-id="63002-105">![手聯合 chasers ](Images/HandJointChaser/MRTK_HandJointChaser_Main.jpg) 這個範例場景示範如何使用「規劃求解」將物件附加至手接點。</span><span class="sxs-lookup"><span data-stu-id="63002-105">![Hand joint chasers](Images/HandJointChaser/MRTK_HandJointChaser_Main.jpg) This example scene demonstrates how to use Solver to attach objects to the hand joints.</span></span>

## <a name="example-scene"></a><span data-ttu-id="63002-106">範例場景</span><span class="sxs-lookup"><span data-stu-id="63002-106">Example scene</span></span>

<span data-ttu-id="63002-107">您可以在下的資料夾中找到範例場景 **HandJointChaserExample** 場景 `Assets/MRTK/Examples` `Demos/Input/Scenes/` 。</span><span class="sxs-lookup"><span data-stu-id="63002-107">You can find the example scene **HandJointChaserExample** scene in the `Assets/MRTK/Examples` folder under `Demos/Input/Scenes/`.</span></span>

## <a name="solver-handler"></a><span data-ttu-id="63002-108">規劃求解處理常式</span><span class="sxs-lookup"><span data-stu-id="63002-108">Solver handler</span></span>

<span data-ttu-id="63002-109">按一下 [ **追蹤的物件參考** ]，然後選取向 **左** 或向 **右** 聯結。</span><span class="sxs-lookup"><span data-stu-id="63002-109">Click **Tracked Object To Reference** and select **Hand Joint Left** or **Hand Joint Right**.</span></span> <span data-ttu-id="63002-110">您將能夠看到追蹤的「 **聯合** 」下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="63002-110">You will be able to see **Tracked Hand Joint** drop down.</span></span> <span data-ttu-id="63002-111">從下拉式清單中，您可以選取特定的聯合以進行追蹤。這個範例場景會使用星形 View 求解，讓物件跟隨在目標物件後面。</span><span class="sxs-lookup"><span data-stu-id="63002-111">From the drop down list, you can select specific joint to track. This example scene uses Radial View Solver to make an object follow the target object.</span></span> <span data-ttu-id="63002-112">如需詳細資料，請參閱 [ [規劃求解](README_Solver.md) ] 頁面。</span><span class="sxs-lookup"><span data-stu-id="63002-112">See [Solver](README_Solver.md) page for more details.</span></span>

![手上聯合規劃求解](Images/HandJointChaser/MRTK_Solver_HandJoint.jpg)
