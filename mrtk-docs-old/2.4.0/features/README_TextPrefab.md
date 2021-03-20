---
title: README_TextPrefab
description: MRTK 中的 TextPrefab 總覽
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
ms.localizationpriority: medium
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、TMP、
ms.openlocfilehash: 259c5fbfafc258ff2e165677e8daebc32ba4e891
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104695665"
---
# <a name="text-prefab"></a>文字預製專案

這些 prefabs 已針對 Windows Mixed Reality 中的轉譯品質進行優化。 如需詳細資訊，請參閱 Microsoft Windows 開發人員中心上 [Unity 中](https://docs.microsoft.com/windows/mixed-reality/text-in-unity) 的指導方針文字。

## <a name="prefabs"></a>Prefabs

### <a name="3dtextprefab"></a>3DTextPrefab

3D 文字網格預製專案 (資產/MRTK/SDK/StandardAssets/Prefabs/文字) ，並以雙計量距離的優化調整因數。  (請閱讀下列指示) 

### <a name="uitextprefab"></a>UITextPrefab

UI 文字網格預製專案 (資產/MRTK/SDK/StandardAssets/Prefabs/文字) ，其中具有在2個計量之間的優化調整係數。  (請閱讀下列指示) 

## <a name="fonts"></a>字型

開放原始碼字型 (資產/MRTK/核心/StandardAssets/字型) 包含在混合現實工具組中。

> [!IMPORTANT]
> 文字預製專案使用開放原始碼字型 ' Selawik '。 若要使用具有不同字型的文字預製專案，請匯入字型檔案，然後遵循下列指示。 下列範例顯示如何使用 ' Segoe UI ' 字型搭配文字預製專案。

![匯入 Segoe UI 字型檔案](Images/TextPrefab/TextPrefabInstructions01.png)

1. 指派字型材質給3DTextSegoeUI 材質。

    ![指派字型材質](Images/TextPrefab/TextPrefabInstructions02.png)

1. 在 [3DTextSegoeUI] 材質上，選取著色器自訂/3DTextShader。

    ![指派著色器](Images/TextPrefab/TextPrefabInstructions03.png)

1. 將 Segoe UI 字型和3DTextSegoeUI 材質指派給 prefabs 中的文字元件。

    ![指派字型檔案和材質](Images/TextPrefab/TextPrefabInstructions04.png)

### <a name="working-with-fonts-in-unity"></a>使用 Unity 中的字型

當您將新的 3D TextMesh 新增至 Unity 中的場景時，有兩個視覺效果明顯的問題。 一個，字型出現很大，而兩個字型出現很模糊的外觀。 另外也請注意，在偵測器中，預設的字型大小值會設定為零。 將此零值取代為13，將不會顯示大小的差異，因為13實際上是預設值。

Unity 會假設新增至場景的所有新元素都是1個 Unity 單位，或100% 的轉換縮放比例，這會在 HoloLens 上轉譯為約1個計量。 在字型的案例中，3D TextMesh 的周框方塊預設會出現在大約1個度量的高度。

### <a name="font-scale-and-font-sizes"></a>字型比例和字型大小

大部分的視覺化設計工具會使用點來定義真實世界中的字型大小，以及其設計程式。 1計量中有大約 2835 (2，834.645666399962) 點。 根據指向1計量的點系統轉換，以及 Unity 的預設 TextMesh 字型大小13，13的簡單數學運算（13）除以2835等於 0.0046 (0.004586111116 是精確的) 提供良好的標準尺規來開始使用，但有些可能想要舍入至0.005。

無論何種方式，將文字物件或容器調整為這些值，不僅可讓您從設計程式轉換成1:1 的字型大小，也提供標準來維持整個應用程式或遊戲的一致性。

### <a name="ui-text"></a>UI 文字

將 UI 或畫布型文字元素新增至場景時，大小差異仍會大於。 這兩種大小的差異大約是1000%，這會將以 UI 為基礎之文字元件的縮放比例帶到 0.00046 (0.0004586111116 為舍入值的精確) 或0.0005。

**免責聲明**：任何字型的預設值可能會受到該字型的材質大小或字型匯入 Unity 的影響。 這些測試是根據 Unity 中的預設 Arial 字型，還有另一個匯入的字型來執行。

![具有縮放比例的字型大小](Images/TextPrefab/TextPrefabInstructions07.png)

### <a name="text3dselawikmat"></a>[Text3DSelawik](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MRTK/Core/StandardAssets/Materials)

具有遮蔽支援的3DTextPrefab 教材。 需要3DTextShader

![預設字型材質與3DTextSegoeUI 材質](Images/TextPrefab/TextPrefabInstructions06.png)

### <a name="text3dshadershader"></a>[Text3DShader 著色器](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MRTK/Core/StandardAssets/Shaders)

具有遮蔽支援之3DTextPrefab 的著色器。
