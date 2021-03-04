---
title: README_HandJointChaser
description: MRTK 中的手聯合 chaser
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: 0790606ad8ac977d812bf47379c5cd6fdb5db489
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/03/2021
ms.locfileid: "101781204"
---
# <a name="hand-joint-chaser-example"></a>手聯合 chaser 範例

![手聯合 chasers ](images/hand-joint-chaser/MRTK_HandJointChaser_Main.jpg) 這個範例場景示範如何使用「規劃求解」將物件附加至手接點。

## <a name="example-scene"></a>範例場景

您可以在下的資料夾中找到範例場景 **HandJointChaserExample** 場景 `Assets/MRTK/Examples` `Demos/Input/Scenes/` 。

## <a name="solver-handler"></a>規劃求解處理常式

按一下 [ **追蹤的物件參考** ]，然後選取向 **左** 或向 **右** 聯結。 您將能夠看到追蹤的「 **聯合** 」下拉式清單。 從下拉式清單中，您可以選取特定的聯合以進行追蹤。這個範例場景會使用星形 View 求解，讓物件跟隨在目標物件後面。 如需詳細資料，請參閱 [ [規劃求解](ux-building-blocks/solvers/Solver.md) ] 頁面。

![手上聯合規劃求解](images/hand-joint-chaser/MRTK_Solver_HandJoint.jpg)
