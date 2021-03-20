---
title: README_HandJointChaser
description: MRTK 中的手聯合 chaser
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: 3530a038296053989c70bd5a0ae49be43da77ca1
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104694455"
---
# <a name="hand-joint-chaser-example"></a><span data-ttu-id="8c590-104">手聯合 chaser 範例</span><span class="sxs-lookup"><span data-stu-id="8c590-104">Hand joint chaser example</span></span>

<span data-ttu-id="8c590-105">![手聯合 chasers ](../images/hand-joint-chaser/MRTK_HandJointChaser_Main.jpg) 這個範例場景示範如何使用「規劃求解」將物件附加至手接點。</span><span class="sxs-lookup"><span data-stu-id="8c590-105">![Hand joint chasers](../images/hand-joint-chaser/MRTK_HandJointChaser_Main.jpg) This example scene demonstrates how to use Solver to attach objects to the hand joints.</span></span>

## <a name="example-scene"></a><span data-ttu-id="8c590-106">範例場景</span><span class="sxs-lookup"><span data-stu-id="8c590-106">Example scene</span></span>

<span data-ttu-id="8c590-107">您可以在下的資料夾中找到範例場景 **HandJointChaserExample** 場景 `Assets/MRTK/Examples` `Demos/Input/Scenes/` 。</span><span class="sxs-lookup"><span data-stu-id="8c590-107">You can find the example scene **HandJointChaserExample** scene in the `Assets/MRTK/Examples` folder under `Demos/Input/Scenes/`.</span></span>

## <a name="solver-handler"></a><span data-ttu-id="8c590-108">規劃求解處理常式</span><span class="sxs-lookup"><span data-stu-id="8c590-108">Solver handler</span></span>

<span data-ttu-id="8c590-109">按一下 [ **追蹤的物件參考** ]，然後選取向 **左** 或向 **右** 聯結。</span><span class="sxs-lookup"><span data-stu-id="8c590-109">Click **Tracked Object To Reference** and select **Hand Joint Left** or **Hand Joint Right**.</span></span> <span data-ttu-id="8c590-110">您將能夠看到追蹤的「 **聯合** 」下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="8c590-110">You will be able to see **Tracked Hand Joint** drop down.</span></span> <span data-ttu-id="8c590-111">從下拉式清單中，您可以選取特定的聯合以進行追蹤。這個範例場景會使用星形 View 求解，讓物件跟隨在目標物件後面。</span><span class="sxs-lookup"><span data-stu-id="8c590-111">From the drop down list, you can select specific joint to track. This example scene uses Radial View Solver to make an object follow the target object.</span></span> <span data-ttu-id="8c590-112">如需詳細資料，請參閱 [ [規劃求解](../ux-building-blocks/solvers/solver.md) ] 頁面。</span><span class="sxs-lookup"><span data-stu-id="8c590-112">See [Solver](../ux-building-blocks/solvers/solver.md) page for more details.</span></span>

![手上聯合規劃求解](../images/hand-joint-chaser/MRTK_Solver_HandJoint.jpg)
