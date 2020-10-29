---
title: 案例研究-建立 HoloSketch、適用于 HoloLens 的空間配置和 UX 草圖應用程式
description: HoloSketch 是適用于 HoloLens 的裝置空間配置和 UX 草圖工具，可協助打造全像攝影體驗。
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: HoloSketch、HoloLens、Windows Mixed Reality、草圖、應用程式
ms.openlocfilehash: 4cb5b6a0a0e057bafb7820d8893b2561b44a2d7e
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2020
ms.locfileid: "91680577"
---
# <a name="case-study---building-holosketch-a-spatial-layout-and-ux-sketching-app-for-hololens"></a>案例研究-建立 HoloSketch、適用于 HoloLens 的空間配置和 UX 草圖應用程式

HoloSketch 是適用于 HoloLens 的裝置空間配置和 UX 草圖工具，可協助打造全像攝影體驗。 HoloSketch 適用于配對的藍牙鍵盤和滑鼠，以及手勢和語音命令。 HoloSketch 的目的是要提供簡單的 UX 版面組態工具，以進行快速的視覺效果和反復專案。

![HoloSketch：適用于 HoloLens 的空間配置和 UX 草圖應用程式。](images/holosketch-image-01-640px.png)<br>
*HoloSketch： HoloLens 的空間配置和 UX 草圖應用程式*

![適用于快速視覺化和反復專案的簡單 UX 版面組態工具。](images/holosketch-image-02.png)<br>
*適用于快速視覺化和反復專案的簡單 UX 版面組態工具*

## <a name="features"></a>特性

### <a name="primitives-for-quick-studies-and-scale-prototyping"></a>用於快速研究和調整原型的基本專案

![使用基本圖形](images/holosketch-primitives-giphy.gif)

使用基本圖形來進行快速 massing 研究和調整原型。

### <a name="import-objects-through-onedrive"></a>透過 OneDrive 匯入物件

![匯入物件](images/holosketch-importobjects-giphy.gif)

匯入 PNG/JPG 影像或 3D FBX 物件 (需要透過 OneDrive 將 Unity) 封裝到混合現實空間中。

### <a name="manipulate-objects"></a>操作物件

![操作物件](images/manipulate-objects-640px.jpg)

使用熟悉的3D 物件介面，操作物件 (移動/旋轉/調整) 。

### <a name="bluetooth-mousekeyboard-gestures-and-voice-commands"></a>藍牙、滑鼠/鍵盤、手勢和語音命令

![支援藍牙](images/supports-bluetooth-640px.jpg)

HoloSketch 支援藍牙滑鼠/鍵盤、手勢和語音命令。

## <a name="background"></a>背景

### <a name="importance-of-experiencing-your-design-in-the-device"></a>在裝置中體驗您設計的重要性

當您針對 HoloLens 設計某項功能時，請務必在裝置中體驗您的設計。 混合現實應用程式設計中最大的挑戰之一，就是很難得到調整、定位和深度的意義，尤其是透過傳統2D 草圖。

### <a name="cost-of-2d-based-communication"></a>以2D 為基礎的通訊成本

為了有效地與其他人溝通 UX 流程和案例，設計人員可能會花很多時間使用傳統2D 工具（例如 Illustrator、Photoshop 和 PowerPoint）來建立資產。 這些2D 設計通常需要額外努力才能將其轉換成3D。 從2D 到3D 的這項轉譯會遺失某些想法。

### <a name="complex-deployment-process"></a>複雜的部署流程

由於混合現實是我們的新畫布，因此它的本質牽涉到許多設計反復專案和試用版和錯誤。 針對不熟悉 Unity 和 Visual Studio 等工具的設計工具，不容易在 HoloLens 中放入一些東西。 一般來說，您必須完成下列程式，才能查看裝置中的 2D/3D 插圖。 這是讓設計人員快速逐一查看構想和案例的大障礙。

![複雜的部署流程](images/holosketch-image-03-1000px.png)<br>
*部署程序*

### <a name="simplified-process-with-holosketch"></a>使用 HoloSketch 簡化的進程

有了 HoloSketch，我們想要簡化此程式，而不涉及開發工具和裝置入口網站配對。 使用 OneDrive，使用者可以輕鬆地將 2D/3D 資產放入 HoloLens。

![使用 HoloSketch 簡化的進程](images/holosketch-image-04-1000px.png)<br>
*使用 HoloSketch 簡化的進程*

### <a name="encouraging-three-dimensional-design-thinking-and-solutions"></a>鼓勵三維設計思考與解決方案

我們認為這項工具會讓設計人員有機會在真正的立體空間中探索解決方案，而不會停滯在2D 中。 他們不需要考慮為其 UI 建立3D 背景，因為在 HoloLens 的情況下，背景是真實世界。 HoloSketch 開啟了一個方法，讓設計人員可以輕鬆地在 HoloLens 上探索3D 設計。

## <a name="get-started"></a>開始使用

### <a name="how-to-import-2d-images-jpgpng-into-holosketch"></a>如何將 (JPG/PNG) 的2D 影像匯入 HoloSketch

* 將 JPG/PNG 影像上傳至您的 OneDrive 資料夾 ' Documents/HoloSketch '。
* 從 HoloSketch 的 [OneDrive] 功能表中，您將能夠選取並將映射放在環境中。

![匯入2D 影像](images/import-2d-images-1000px.jpg)<br>
*透過 OneDrive 匯入影像和3D 物件*

### <a name="how-to-import-3d-objects-into-holosketch"></a>如何將3D 物件匯入 HoloSketch

上傳至您的 OneDrive 資料夾之前，請遵循下列步驟，將您的3D 物件封裝至 Unity 資產套件組合。 您可以使用此程式從3D 軟體（例如 Maya、電影院4D 和 Microsoft 小畫家3D）匯入 FBX/OBJ 檔案。

>[!IMPORTANT]
>目前，Unity 版本5.4.5 節 f1 支援資產組合建立。

1. 下載並開啟 Unity 專案 [' AssetBunlder_Unity '](https://github.com/Microsoft/MRDesignLabs/tree/master/ReleasedApps/HoloSketch/AssetBundler_Unity)。 此 Unity 專案包含產生配套資產的腳本。
2. 建立新的 GameObject。
3. 以內容為基礎來命名 GameObject。
4. 在 [偵測器] 面板中，按一下 [新增元件]，然後新增 [方塊碰撞器]。 

   ![在 [偵測器] 面板中，按一下 [新增元件]，然後新增 [方塊碰撞器]](images/holosketch-10a-assetbundles-1000px.png)
   
   ![在 [偵測器] 面板中，按一下 [新增元件]，然後新增 [方塊碰撞器] #2](images/holosketch-10b-assetbundles-1000px.png)

5. 將 3D FBX 檔案拖曳至 [專案] 面板中，以匯入該檔案。
6. 將物件拖曳至 **新 GameObject 下** 的 [階層] 面板中。

   ![將物件拖曳至新 GameObject 底下的階層面板](images/holosketch-12-assetbundles-1000px.png)

7. 如果碰撞項維度不符合物件，則調整其大小。 將物件旋轉為臉部 **Z 軸** 。

   ![調整碰撞維度（如果它不符合物件）。](images/holosketch-13-assetbundles-1000px.png)

8. 將物件從 [階層] 面板拖曳至 [專案] 面板， **讓它預製專案** 。
9. 在 [偵測器] 面板底部，按一下下拉式清單，建立並指派新的唯一名稱。 下列範例顯示如何為 AssetBundle 名稱新增和指派 ' brownchair '。 

   ![在 [偵測器] 面板底部，按一下下拉式清單，然後指派新的唯一名稱。](images/holosketch-14-assetbundles-1000px.png)

10. 準備模型物件的縮圖影像。 
   ![將影像拖曳至 [專案] 面板中，並指派用於物件的名稱。](images/holosketch-15-assetbundles-1000px.png)

11. 在 Unity 專案的 [資產] 資料夾下建立名為 ' Assetbundles ' 的資料夾。

12. 在 [資產] 功能表中，選取 [組建 AssetBundles] 以產生檔案。 
   ![在 [資產] 功能表中，選取 [組建 AssetBundles] 以產生檔案。](images/holosketch-15a-assetbundles.png)


13. **將產生的檔案上傳至 OneDrive 上的/Files/Documents/HoloSketch 資料夾。** 僅上傳 asset_unique_name 檔案。 您不需要上傳資訊清單檔案或 AssetBundles 檔案。 <br>
![將檔案新增至檔案/檔/HoloSketch/資料夾 ](images/holosketch-onedriveupload-1000px.png)
 ![ 您會在 HoloSketch 的 OneDrive 功能表中看到新增的3d 物件](images/holosketch-14-onedriveexample-1000px.jpg)

## <a name="how-to-manipulate-the-objects"></a>如何操作物件

HoloSketch 支援廣泛用於3D 軟體的傳統介面。 您可以使用移動、旋轉、使用筆勢和滑鼠來縮放物件。 您可以使用語音或鍵盤在不同模式之間快速切換。

### <a name="object-manipulation-modes"></a>物件操作模式

![如何操作物件](images/holosketch-image-06-1000px.png)<br>
*如何操作物件*

### <a name="contextual-and-tool-belt-menus"></a>內容和工具皮帶功能表

**使用操作功能表**

按兩下以開啟內容功能表。 

功能表項目：
* **版面配置介面：** 這是3D 格線系統，您可以在其中配置多個物件，並以群組方式管理它們。 按兩下版面配置介面，將物件新增至其中。
* **基本：** 使用 cube、球體、圓柱和圓錐 massing 研究。
* **OneDrive：** 開啟 OneDrive 功能表以匯入物件。
* 說明 **：** 顯示說明畫面。

![操作功能表](images/holosketch-image-07.png)<br>
*操作功能表*

**使用工具功能表**

您可以從工具功能表使用移動、旋轉、縮放、儲存和載入場景。 

## <a name="using-keyboard-gestures-and-voice-commands"></a>使用鍵盤、手勢和語音命令

![鍵盤、手勢和語音命令](images/holosketch-image-08-1000px.png)<br>
*鍵盤、手勢和語音命令*

## <a name="download-the-app"></a>下載此應用程式

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="HoloSketch app icon" width="60" height="60" src="images/holosketch-app-icon.png">
</td>
<td style="border-style: none"><a href="https://www.microsoft.com/store/p/holosketch/9p3br4t5m4tv">從 Microsoft Store 免費下載並安裝 HoloSketch 應用程式</a>
</td>
</tr>
</table>

## <a name="known-issues"></a>已知問題
* **Unity 版本5.4.5 節 f1** 支援目前的資產套件組合建立。
* 視 OneDrive 中的資料量而定，應用程式可能會顯示為在載入 OneDrive 內容時停止
* 目前，儲存和載入功能只支援基本物件
* 在內容功能表上停用文字、音效、影片和相片功能表
* 工具功能表上的 [播放] 按鈕會清除操作 gizmos

## <a name="sharing-your-sketches"></a>共用您的草圖

您可以藉由說出「嗨 Cortana、開始/停止錄製」來使用 HoloLens 中的影片錄製功能。 同步選取音量向上/向下鍵，以拍攝草圖的圖片。

## <a name="about-the-authors"></a>關於作者

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="../develop/unity/images/dongyoonpark.jpg"></td>
<td style="border-style: none"><b>盾 Yoon 公園</b><br>UX 設計工具 @Microsoft</td>
</tr>
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Patrick Sebring" width="60" height="60" src="images/paseb-60px.jpg"></td>
<td style="border-style: none"><b>派翠克 Sebring</b><br>開發 人員 @Microsoft</td>
</tr>
</table> 
