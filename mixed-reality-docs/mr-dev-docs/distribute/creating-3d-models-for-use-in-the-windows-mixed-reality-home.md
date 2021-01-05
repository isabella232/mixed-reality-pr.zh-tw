---
title: 建立用於住家的 3D 模型
description: HoloLens 和沉浸式 (VR) 耳機上的 Windows Mixed Reality 首頁中使用之3D 模型的資產需求和撰寫指導方針。
author: thmignon
ms.author: thmignon
ms.date: 03/21/2018
ms.topic: article
keywords: 3D、模型化、模型化指引、資產需求、撰寫指導方針、啟動器、3D 啟動器、材質、材質、複雜度、三角形、網格、多邊形、polycount、限制、混合現實耳機、windows mixed reality 耳機、虛擬實境耳機
ms.openlocfilehash: 17014e3deaaa161dd7949a55679b916e872ad5a7
ms.sourcegitcommit: 8d3b84d2aa01f078ecf92cec001a252e3ea7b24d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2020
ms.locfileid: "97757782"
---
# <a name="create-3d-models-for-use-in-the-home"></a>建立用於住家的 3D 模型

[Windows Mixed Reality home](../discover/navigating-the-windows-mixed-reality-home.md)是使用者在啟動應用程式之前所居住的起點。 針對 Windows Mixed Reality 耳機設計您的應用程式時，請使用 [3d 模型作為應用程式啟動器](implementing-3d-app-launchers.md) ，並將 [3d 深層連結放入 Windows Mixed Reality 首頁](implementing-3d-app-launchers.md#3d-deep-links-secondarytiles)。 本文概述建立與 Windows Mixed Reality 首頁相容之3D 模型的指導方針。

## <a name="asset-requirements-overview"></a>資產需求總覽

建立 Windows Mixed Reality 的3D 模型時，有一些資產必須符合的需求： 
1. [匯出](#exporting-models) -資產必須以 glb 檔案格式傳遞 (二進位 glTF) 
2. [模型](#modeling-guidelines) 化-資產必須小於1萬個三角形，每個」 lod 不能超過64個節點和 32 submeshes
3. [材質-紋理](#material-guidelines) 不能大於 4096 x 4096，且最小的 mip 地圖在任一維度上都不能大於4
4. [動畫](#animation-guidelines) -動畫的長度不能超過20分鐘， (36000 的主要畫面格) 且必須包含 <= 8192 的變形目標頂點
5. [優化](#optimizations) -資產應使用 [WindowsMRAssetConverter](https://github.com/Microsoft/glTF-Toolkit/releases)進行優化。 *在 WINDOWS 作業系統版本 <= 1709** 上，建議在 windows 作業系統版本 >= 1803 上使用

本文的其餘部分將詳細說明這些需求和額外的指導方針，以確保您的模型可與 Windows Mixed Reality 首頁正常搭配運作。 

## <a name="detailed-guidance"></a>詳細指引

### <a name="exporting-models"></a>匯出模型

Windows Mixed Reality 首頁預期會使用 glb 檔案格式搭配內嵌影像和二進位資料來傳遞3D 資產。 Glb 是 glTF 格式的二進位版本，這是 Khronos 群組所維護之3D 資產傳遞的專利免費開放標準。 隨著 glTF 發展成為互通3D 內容的產業標準，Microsoft 會在 Windows 應用程式和經驗中支援此格式。 如果您尚未建立 glTF 資產，您可以在 [glTF 工作群組 github] 頁面上找到 [支援的匯出工具和轉換器清單](https://github.com/KhronosGroup/glTF/blob/master/README.md#converters-and-exporters) 。  

### <a name="modeling-guidelines"></a>模型指導方針

Windows 預期會使用下列模型化指導方針來產生資產，以確保與混合現實首頁體驗的相容性。 在您選擇的程式中建立模型時，請記住下列建議和限制：
1. 向上軸應設定為 "Y"。
2. 資產應「轉寄」朝正 Z 軸。
3. 所有資產都應建立于場景原點的地面平面 (0、0、0) 
4. 工作單位應該設定為計量和資產，以便能夠以全球規模撰寫資產
5. 所有網格都不需要合併，但如果您是以資源受限的裝置為目標，則建議使用此選項。
6. 所有網格都應該共用一份材質，只針對整個資產使用一個材質組
7. UVs 必須以0-1 空間中的正方形排列來配置。 避免將材質平平鋪，不過它們是允許的。
8. 不支援多 UVs
9. 不支援雙面材質

### <a name="triangle-counts-and-levels-of-detail-lods"></a> (LODs) 的三角形計數和詳細資料層級

Windows Mixed Reality home 不支援10000三角形以上的模型。 建議您先分成三角形網格再進行匯出，以確保它們不會超過此計數。 Windows MR 也支援選擇性幾何等級的詳細 (LODs) ，以確保效能和高品質的體驗。 [WindowsMRAssetConverter](https://github.com/Microsoft/glTF-Toolkit/releases) 可協助您將模型的三個版本結合成單一 glb 模型。 Windows 會根據模型所佔用的螢幕實際空間量來決定要顯示的」 LOD。 只有3個」 LOD 層級支援下列建議的三角形計數：
<br>

|  」 LOD 層級  |  建議的三角形計數  |  最大三角形計數 | 
|------|------|------|
|  」 LOD 0 |  10,000 |  10,000 | 
|  」 LOD 1 |  5,000  |  10,000 | 
|  」 LOD 2 |  2,500  |  10,000 | 

### <a name="node-counts-and-submesh-limits"></a>節點計數和 submesh 限制

Windows Mixed Reality home 不支援每個」 LOD 具有64節點或 32 submeshes 的模型。 節點是 [glTF 規格](https://github.com/KhronosGroup/glTF/tree/master/specification/2.0#nodes-and-hierarchy) 中的概念，可定義場景中的物件。 Submeshes 是在物件之網格的 [基本](https://github.com/KhronosGroup/glTF/tree/master/specification/2.0#meshes) 陣列中定義。 

|  功能 |  描述  |  支援的最大值 | 文件 |
|------|------|------|------|
|  節點 |  GlTF 場景中的物件 |  每個」 LOD 64 | [這裡](https://github.com/KhronosGroup/glTF/tree/master/specification/2.0#nodes-and-hierarchy)|
|  Submeshes |  所有網格上的基本專案總和 |  每個」 LOD 32 | [這裡](https://github.com/KhronosGroup/glTF/tree/master/specification/2.0#meshes)|

## <a name="material-guidelines"></a>材質指導方針

材質應使用 .PBR 裸機粗糙度工作流程來準備。 首先，建立一組完整的材質，包括 >albedo、Normal、遮蔽、金屬和粗糙度。 Windows Mixed Reality 支援使用解析度最高4096x4096 的材質，但建議您在512x512 撰寫。 紋理應以4倍數的解析度撰寫。 這是在匯出步驟中套用至材質之壓縮格式的要求，如下所述。 產生 mip map 或材質時，最低 mip 必須最多為4x4。
<br>

|  建議的材質大小  |  紋理大小上限 | 最低 Mip
|----|----|----|
|  512x512  |  4096x4096 | 最大4x4|

### <a name="albedo-base-color-map"></a>>albedo (基本色彩) 地圖

沒有光源資訊的原始色彩。 此地圖也包含金屬圖中金屬 (白色的反射率和擴散資訊，) 和 insulator 在金屬地圖) 表面中 (黑色。

### <a name="normal"></a>正常

正切空間一般地圖

### <a name="roughness-map"></a>粗糙度圖

描述物件的 microsurface。 白色1.0 的黑色0.0 很平滑。 此對應會為資產提供最多字元，因為它會真正描述表面。 例如，劃痕、指紋、汙跡、grime 等等。

### <a name="ambient-occlusion-map"></a>環境遮蔽對應

值小數位數地圖，顯示 pixels occluded 光線的區域，以封鎖反射

### <a name="metallic-map"></a>金屬圖

指出著色器是否為金屬。 原始金屬 = 1.0 白色非金屬 = 0.0 黑色。 可能會有過渡的灰色值，表示涵蓋 raw 金屬（例如灰塵）的內容，但一般而言，此地圖應該是黑色和白色。

## <a name="optimizations"></a>最佳化

Windows Mixed Reality home 在使用自訂延伸模組所定義的核心 glTF 規格之上，提供一系列的優化。 <= 1709 的 Windows 版本和建議在較新版本的 Windows 上，都需要進行這些優化。 您可以使用 [GitHub 上提供的 Windows Mixed Reality 資產轉換器](https://github.com/Microsoft/glTF-Toolkit/releases)，輕鬆地優化任何 glTF 2.0 模型。 此工具會執行正確的材質封裝和優化，如下所示。 針對一般使用方式，我們建議使用 WindowsMRAssetConverter，但如果您需要更充分掌控體驗，而且想要建立自己的優化管線，您可以參考以下的詳細規格。  

> [!NOTE]
> 如需確切的模型限制之可能性的完整清單，請參閱「 [3d 模型優化](https://docs.microsoft.com/dynamics365/mixed-reality/guides/3d-content-guidelines/optimize-models) 」一文，以在 Dynamics 365 應用程式中使用。

### <a name="materials"></a>材質

為了改善混合現實環境中的資產載入時間，Windows MR 支援根據本節中定義的材質封裝配置來呈現壓縮的 DDS 紋理。 使用 [MSFT_texture_dds 擴充](https://github.com/sbtron/glTF/tree/MSFT_lod/extensions/Vendor/MSFT_texture_dds)功能參考 DDS 紋理。 強烈建議您壓縮紋理。 

#### <a name="hololens"></a>HoloLens

HoloLens 型混合現實體驗預期會使用下列封裝規格，以使用雙紋理設定來封裝紋理：
<br>

|  glTF 屬性  |  紋理  |  封裝配置 | 
|----------|----------|----------|
|  pbrMetallicRoughness  |  baseColorTexture  |  紅色 (R) 、綠色 (G) 、藍色 (B)  | 
|  [MSFT_packing_normalRoughnessMetallic](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_normalRoughnessMetallic/README.md)  |  normalRoughnessMetallicTexture  |  一般 (RG) 、粗糙度 (B) 、金屬 ()  | 


壓縮 DDS 紋理時，每個對應預期會有下列壓縮：
<br>

|  紋理  |  預期的壓縮 | 
|------|------|
|  baseColorTexture, normalRoughnessMetallicTexture |  BC7 | 

#### <a name="immersive-vr-headsets"></a>沉浸式 (VR) 耳機

以電腦為 Windows Mixed Reality 的沉浸式 (VR) 耳機預期紋理會使用採用下列封裝規格的3紋理設定來封裝：

##### <a name="windows-os--1803"></a>Windows 作業系統 >= 1803

<br>

|  glTF 屬性  |  紋理  |  封裝配置 | 
|----------|----------|----------|
|  pbrMetallicRoughness  |  baseColorTexture  |  紅色 (R) 、綠色 (G) 、藍色 (B)  | 
|  [MSFT_packing_occlusionRoughnessMetallic](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_occlusionRoughnessMetallic/README.md)  |  occlusionRoughnessMetallicTexture  |  遮蔽 (R) 、粗糙度 (G) 、金屬 (B)  | 
|  [MSFT_packing_occlusionRoughnessMetallic](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_occlusionRoughnessMetallic/README.md)  |  normalTexture  |  一般 (RG)  | 

壓縮 DDS 紋理時，每個對應預期會有下列壓縮：
<br>

|  紋理  |  預期的壓縮 | 
|------|------|
|  normalTexture  |  BC5 | 
|  baseColorTexture, occlusionRoughnessMetallicTexture  |  BC7 | 

##### <a name="windows-os--1709"></a>Windows 作業系統 <= 1709
<br>

|  glTF 屬性  |  紋理  |  封裝配置 | 
|----------|----------|----------|
|  pbrMetallicRoughness  |  baseColorTexture  |  紅色 (R) 、綠色 (G) 、藍色 (B)  | 
|  [MSFT_packing_occlusionRoughnessMetallic](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_occlusionRoughnessMetallic/README.md)  |  roughnessMetallicOcclusionTexture  |  粗糙度 (R) 、金屬 (G) 、遮蔽 (B)  | 
|  [MSFT_packing_occlusionRoughnessMetallic](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_occlusionRoughnessMetallic/README.md)  |  normalTexture  |  一般 (RG)  | 

壓縮 DDS 紋理時，每個對應預期會有下列壓縮：
<br>

|  紋理  |  預期的壓縮 | 
|------|------|
|  normalTexture  |  BC5 | 
|  baseColorTexture, roughnessMetallicOcclusionTexture | BC7 |

### <a name="adding-mesh-lods"></a>新增網狀 LODs

Windows MR 使用幾何節點 LODs，根據螢幕上的涵蓋範圍，以不同的詳細資料層級呈現3D 模型。 雖然這項功能在技術上並不是必要的，但建議用於所有資產。 Windows 目前支援三個層級的詳細資料。 預設」 LOD 為0，表示最高品質。 其他 LODs 會依序編號，例如1、2，而且品質會逐漸降低。 [Windows Mixed Reality 資產轉換器](https://github.com/Microsoft/glTF-Toolkit/releases)可接受多個 glTF 模型，並將其合併至具有有效」 lod 層級的單一資產，藉此支援產生符合此」 lod 規格的資產。 下表概述預期的」 LOD 順序和三角形目標：
<br>

|  」 LOD 層級  |  建議的三角形計數  |  最大三角形計數 | 
|-------|-------|-------|
|  」 LOD 0 |  10,000 |  10,000 | 
|  」 LOD 1 |  5,000  |  10,000 | 
|  」 LOD 2 |  2,500  |  10,000 | 

使用 LODs 時，一律指定3個」 LOD 層級。 遺漏 LODs 會導致模型不會因為」 LOD 系統切換至遺失的」 LOD 層級而非預期地呈現。 glTF 2.0 目前不支援 LODs 作為核心規格的一部分。 LODs 應使用 [MSFT_LOD 擴充](https://github.com/sbtron/glTF/tree/MSFT_lod/extensions/Vendor/MSFT_lod)功能來定義。

### <a name="screen-coverage"></a>螢幕涵蓋範圍

LODs 會根據每個」 LOD 上設定的螢幕涵蓋範圍值所驅動的系統，在 Windows Mixed Reality 中顯示。 目前耗用較大部分螢幕空間的物件會顯示在較高的」 LOD 層級上。 螢幕涵蓋範圍不是核心 glTF 2.0 規格的一部分，而且必須使用 [MSFT_lod 擴充](https://github.com/sbtron/glTF/tree/MSFT_lod/extensions/Vendor/MSFT_lod)功能的 [額外專案] 區段中的 MSFT_ScreenCoverage 來指定。
<br>

|  」 LOD 層級  |  建議的範圍  |  預設範圍 | 
|-------|-------|-------|
|  」 LOD 0  |  100%-50% |  0.5 | 
|  」 LOD 1 |  低於 50%-20%  |  0.2 | 
|  」 LOD 2 |  低於 20%-1%  |  0.01 | 
|  」 LOD 4  |  低於1%  |  - | 

## <a name="animation-guidelines"></a>動畫指導方針

> [!NOTE]
> 這項功能已新增為 [Windows 10 2018 年4月更新](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/release-notes-april-2018)的一部分。 在舊版的 Windows 上，這些動畫不會播放，不過，如果是根據本文中的指導方針來撰寫，它們仍會載入。  

混合實境首頁支援 HoloLens 和沉浸式 (VR) 耳機上的動畫 glTF 物件。 如果您想要在模型上觸發動畫，您必須使用 glTF 格式的動畫地圖延伸模組。 此延伸模組可讓您根據使用者在世界中的目前狀態，在 glTF 模型中觸發動畫，例如，當使用者接近物件或正在查看動畫時，觸發動畫。 如果您 glTF 物件具有動畫，但未定義觸發程式，則不會播放動畫。 下一節描述將這些觸發程式新增至任何動畫 glTF 物件的工作流程。

### <a name="tools"></a>工具

首先，請下載下列工具（如果您還沒有的話）。 這些工具可讓您輕鬆地開啟任何 glTF 模型、預覽、變更，以及將其存回 glTF 或 glb：
1. [Visual Studio Code](https://code.visualstudio.com/)
2. [適用于 Visual Studio Code 的 glTF 工具](https://marketplace.visualstudio.com/items?itemName=cesium.gltf-vscode)


### <a name="opening-and-previewing-the-model"></a>開啟和預覽模型

首先，在 VSCode 中開啟 glTF 模型，方法是將 glTF 檔案拖曳至編輯器視窗。 如果您有 glb 而不是 glTF 檔案，您可以使用您下載的 glTF 工具附加元件，將其匯入 VSCode。 移至 [View-> 命令選擇區]，然後在命令選擇區中開始輸入 "glTF"，然後選取 [glTF： Import from glb]，這會顯示檔案選擇器，讓您用來匯入 glb。 

開啟 glTF 模型之後，您應該會在編輯器視窗中看到 JSON。 您也可以使用滑鼠右鍵按一下檔案名，然後選取右鍵功能表中的 [glTF： Preview 3D 模型] 命令快捷方式，以在即時3D 檢視器中預覽模型。 

### <a name="adding-the-triggers"></a>新增觸發程式

動畫觸發程式會使用動畫地圖延伸模組加入至 glTF 模型 JSON。 動畫地圖延伸模組會 [在 GitHub 上](https://github.com/msfeldstein/glTF/blob/04f7005206257cf97b215df5e3f469d7838c1fee/extensions/Vendor/FB_animation_map/README.md) 公開記載 (注意：這是) 的草稿延伸模組。 若要將擴充功能新增至您的模型，只需在編輯器中 glTF 檔案的結尾，並將 "extensionsUsed" 和 "extension" 區塊新增至檔案（如果它們還不存在的話）。 在 "extensionsUsed" 區段中，您會新增 "EXT_animation_map" 擴充功能的參考，而在 "extensions" 區塊中，您會將對應加入至模型中的動畫。

如同 [在規格中](https://github.com/msfeldstein/glTF/blob/04f7005206257cf97b215df5e3f469d7838c1fee/extensions/Vendor/FB_animation_map/README.md) 所述，您定義了在 "動畫" 清單上使用 "語義" 字串觸發動畫的結果，這是動畫索引的陣列。 在下列範例中，我們已指定在物件上撥雲見日使用者時要播放的動畫：

```json
  "extensionsUsed": [
    "EXT_animation_map"
  ],
  "extensions" : {
      "EXT_animation_map" : {
            "bindings": [
                {
                    "semantic": "GAZE",
                    "animations": [0]
                }
            ]
      }
  }
```
Windows Mixed Reality home 支援下列動畫觸發語義。  
* 「永遠」：持續迴圈動畫
* 「已保留」：在整個持續期間內，物件被抓取的迴圈。
* 「注視」：正在查看物件時迴圈
* 「鄰近性」：當檢視器接近物件時進行迴圈
* 「指向」：當使用者指向物件時迴圈

### <a name="saving-and-exporting"></a>儲存和匯出

變更 glTF 模型之後，您可以直接將其儲存為 glTF。 您也可以在編輯器中的檔案名上按一下滑鼠右鍵，然後選取 [glTF： Export to GLB (binary file) ] 以匯出 GLB。 

### <a name="restrictions"></a>限制

動畫的長度不能超過20分鐘，且不能包含超過36000的主要畫面格 (20 分鐘的 30 FPS) 。 此外，使用以平滑目標為基礎的動畫時，不會超過8192的變形目標頂點或較少。 超過這些計數會導致 Windows Mixed Reality 首頁不支援動畫資產。 

|功能|最大值|
|-----|-----|
|持續時間|20 分鐘|
|關鍵 幀|36000| 
|變形目標頂點|8192|

## <a name="gltf-implementation-notes"></a>glTF 執行注意事項

Windows MR 不支援使用負面比例來翻轉幾何。 具有負值縮放的幾何很可能會導致視覺效果成品。

GlTF 資產必須指向使用 Windows MR 轉譯的場景屬性的預設場景。 此外， [Windows 10 2018 年4月更新](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/release-notes-april-2018)之前的 Windows MR glTF 載入器 **需要** 存取子：
* 必須具有最小值和最大值。
* 型別純量必須為 componentType UNSIGNED_SHORT (5123) 或 UNSIGNED_INT (5125) 。
* 類型 VEC2 和 VEC3 必須是 componentType FLOAT (5126) 。

下列材質屬性是從 core glTF 2.0 規格中使用，但不是必要的：
* baseColorFactor, metallicFactor, roughnessFactor
* baseColorTexture：必須指向儲存在 dds 中的材質。
* emissiveTexture：必須指向儲存在 dds 中的材質。
* emissiveFactor
* AlphaMode

核心規格會忽略下列材質屬性：
* 所有多 UVs
* metalRoughnessTexture：必須改為使用下列定義的 Microsoft 優化材質封裝
* normalTexture：必須改為使用下列定義的 Microsoft 優化材質封裝
* normalScale
* occlusionTexture：必須改為使用下列定義的 Microsoft 優化材質封裝
* occlusionStrength

Windows MR 不支援基本模式線和點。 

僅支援單一 UV 頂點屬性。

## <a name="more-resources"></a>其他資源

* [glTF 匯出工具和轉換器](https://github.com/KhronosGroup/glTF#converters-and-exporters)
* [glTF 工具組](https://github.com/Microsoft/glTF-Toolkit)
* [glTF 2.0 規格](https://github.com/KhronosGroup/glTF/blob/master/README.md)
* [Microsoft glTF」 LOD 延伸模組規格](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_lod/README.md)
* [PC Mixed Reality 材質封裝延伸模組規格](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_occlusionRoughnessMetallic/README.md)
* [HoloLens 混合現實材質封裝延伸模組規格](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_normalRoughnessMetallic/README.md)
* [Microsoft DDS 紋理 glTF 延伸模組規格](https://github.com/KhronosGroup/glTF/tree/master/extensions/2.0/Vendor/MSFT_texture_dds)

## <a name="see-also"></a>請參閱

* [實作 3D 應用程式啟動器 (UWP 應用程式)](implementing-3d-app-launchers.md)
* [實作 3D 應用程式啟動器 (Win32 應用程式)](implementing-3d-app-launchers-win32.md)
* [瀏覽 Windows Mixed Reality 住家](../discover/navigating-the-windows-mixed-reality-home.md)
