---
title: 空間網格視覺效果
description: 深入瞭解 MRTK 中的空間網格視覺效果的設計方針和實體環境瞭解。
author: cre8ivepark
ms.author: dongpark
ms.date: 06/19/2020
ms.topic: article
keywords: 混合的現實、HoloLens、UI 控制項、互動、UI、ux、UX 設計、空間 UI、空間互動、3D UI、3D UX、混合現實耳機、windows mixed reality 耳機、虛擬實境耳機、HoloLens、MRTK、混合現實工具組
ms.openlocfilehash: 5bdcba60f38ac67bbf0f394337735f4a2d4ec423
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600627"
---
# <a name="spatial-mesh"></a>空間網格

![空間網格](images/MRTK_PulseShader_SpatialMesh.gif)

使用者瞭解裝置如何透過空間網格視覺效果來理解及瞭解實體環境。 適當的空間網格視覺效果可在提供空間內容時建立趣味性兼具和神奇體驗。  

## <a name="design-guideline"></a>設計指導方針

請務必讓使用者專注並與內容互動。 背景中空間網格的連續視覺效果可能會造成干擾。 建議您在初始啟動時，或當使用者清楚地顯示其想要依目標和空中點擊空間來查看環境網格時，謹慎地視覺化環境。 您可以在混合實境入口中觀察這項行為。
<br>

## <a name="spatial-mesh-visualization-in-mrtk-mixed-reality-toolkit-for-unity"></a>適用于 Unity 的 MRTK (混合現實工具組) 的空間網格視覺效果

MRTK 為空間網格視覺效果提供數種材質。

- **MRTK_Wireframe，MRTK_Wireframe** 的材質：預設的靜態空間網格材質，顯示沒有動畫的網格輪廓。 這項資料適用于偵錯工具，因為它會顯示整個空間網格幾何。 但是，不建議用於生產環境。
<br>
<img src="images/SurfaceReconstruction.jpg" alt="Wireframe spatial mesh visualization" width="640px">

- **MRTK_SurfaceReconstruction** 的材質：此材質提供您對空間網格的動畫脈衝效果。 您可以使用這份資料，在特定時間或使用者的按兩下輸入時，將環境視覺化。 如需範例，請參閱 **PulseShaderExamples unity** 場景。
<br>
<img src="images/MRTK_SRMesh_Pulse.jpg" alt="Pulse spatial mesh visualization" width="640px">

* 如需詳細資訊，請參閱 [MRTK-空間感知](/windows/mixed-reality/mrtk-unity/features/spatial-awareness/spatial-awareness-getting-started) 和 [MRTK-脈衝著色器](/windows/mixed-reality/mrtk-unity/features/experimental/pulse-shader)。

<br>

---

## <a name="see-also"></a>另請參閱

* [游標](cursors.md)
* [手部光線](point-and-commit.md)
* [Button](button.md)
* [可互動的物件](interactable-object.md)
* [週框方塊和應用程式列](app-bar-and-bounding-box.md)
* [操作](direct-manipulation.md)
* [手部功能表](hand-menu.md)
* [近端功能表](near-menu.md)
* [物件集合](object-collection.md)
* [語音命令](voice-input.md)
* [鍵盤](keyboard.md)
* [工具提示](tooltip.md)
* [平板](slate.md)
* [滑桿](slider.md)
* [著色器](shader.md)
* [佈告板和常駐標籤](billboarding-and-tag-along.md)
* [顯示進度](progress.md)
* [表面磁性](surface-magnetism.md)