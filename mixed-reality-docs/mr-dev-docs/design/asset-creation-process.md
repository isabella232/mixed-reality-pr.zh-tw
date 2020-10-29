---
title: 資產建立程序
description: 針對混合現實體驗建立資產的指引。
author: shengkait
ms.author: shentan
ms.date: 03/21/2018
ms.topic: article
keywords: 資產、建立、處理、預算、多邊形、紋理、著色器、效能
ms.openlocfilehash: 56be236086a6947549af6199dc3d01ba7c555375
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2020
ms.locfileid: "91680008"
---
# <a name="asset-creation-process"></a>資產建立程序

Windows Mixed Reality 是以 Microsoft 在 DirectX 中所做的投資數十年為基礎。 這表示，開發人員在建立3D 圖形時，所擁有的所有經驗和技能，會持續對 HoloLens 有價值。

您為專案建立的資產有許多圖形和表單。 它們可以由一連串的材質/影像、音訊、影片、3D 模型和動畫組成。 我們無法開始討論可用來建立專案中不同類型資產的所有工具。 在本文中，我們將著重于3D 資產建立方法。

![概念、建立、整合和反復專案流程](images/concept-creation-integration-iteration-flow-640px.jpg)<br>
*概念、建立、整合和反復專案流程*

## <a name="things-to-consider"></a>考量事項

查看您嘗試建立的體驗時，您想要將它視為 **預算** ，您可以花在嘗試建立最佳體驗。 在您的資產中使用的 **多邊形** 或資料 **類型** 數目不一定會有固定限制，但是有一組預算的取捨。

以下是您體驗的範例預算。 效能通常不是單一失敗點，而是每個 se 會有上千個剪下。
<br>

<table style="float:right; margin-left: 10px;">
<tr>
<th style="text-align:left;"><b>資產</b></th><th style="text-align:right;"> CPU</th><th> GPU</th><th> 記憶體</th>
</tr><tr>
<td> 多邊形</td><td> 0%</td><td> 5%</td><td> 10%</td>
</tr><tr>
<td> 紋理</td><td> 5%</td><td> 15%</td><td>25%</td>
</tr><tr>
<td> 著色器</td><td> 15%</td><td> 35%</td><td> 0%</td>
</tr><tr>
<td> <b>Dynamics</b></td><td></td><td></td><td></td>
</tr><tr>
<td> 物理特性</td><td> 5%</td><td> 15%</td><td> 0%</td>
</tr><tr>
<td> 即時光源</td><td> 10%</td><td> 0%</td><td> 0%</td>
</tr><tr>
<td> 媒體 (音訊/影片) </td><td> -</td><td> 15%</td><td> 25%</td>
</tr><tr>
<td> 腳本/邏輯</td><td> 25%</td><td> 0%</td><td> 5%</td>
</tr><tr>
<td> 一般負荷</td><td> 5%</td><td> 5%</td><td> 5%</td>
</tr><tr>
<td> <b>總計</b></td><td> <b>65%</b></td><td> <b>90%</b></td><td> <b>70%</b></td>
</tr>
</table>

**總資產數**
* 場景中有多少可用的資產？

**資產的複雜度**
* 有多少三角形/多邊形？
* 著色器有多複雜？ 使用混合現實工具組時，建議使用 [混合現實工具組標準著色器](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_MRTKStandardShader.md) 來減少著色器的複雜度。

開發人員和演出者都必須考慮裝置和圖形引擎的功能。 Microsoft HoloLens 具有裝置內建的所有計算和圖形。 它會共用開發人員可在行動平臺上找到的功能。

無論您是以全像全像 [裝置或沉浸式裝置](../discover/mixed-reality.md#the-mixed-reality-spectrum)的體驗為目標，資產的建立程式都相同。 要注意的主要事項是上述的裝置功能以及調整規模，因為您可以在混合現實中看到真實世界，所以您會想要根據體驗來維持正確的規模。

## <a name="authoring-assets"></a>撰寫資產

我們將從取得專案資產的方法開始：
1. 建立資產 (Authoring tools 和物件捕捉) 
2. 購買資產 (線上購買資產) 
3.  (取得現有資產) 來移植資產
4. 從協力廠商匯入資產 (外包資產) 

### <a name="creating-assets"></a>建立資產

**Authoring tools**<br>
首先，您可以使用數種不同的方式來建立自己的資產。 3D 演出者使用許多應用程式和工具來建立包含 **網格** 、 **材質** 和 **材質** 的模型。 然後，這會以檔案格式儲存，讓應用程式使用的圖形引擎可以匯入或使用，例如 **。FBX** 或 **。OBJ** 。 任何產生您所選圖形引擎支援之模型的工具，都可以在 **HoloLens** 上運作。 在3D 演出者之間，許多選擇使用 [Autodesk 的 Maya，其本身可以使用 HoloLens](https://www.youtube.com/watch?v=q0K3n0Gf8mA) 來轉換資產的建立方式。 如果您想要快速取得東西，也可以使用 Windows 所附的 [3D Builder](https://developer.microsoft.com/windows/hardware/3d-print/3d-builder-resources) 來匯出。要在應用程式中使用的 OBJ。

**物件捕獲**<br>
另外還有在3D 中捕捉物件的選項。 使用數位內容建立軟體來捕捉3D 中的無生命物件，並使用數位內容建立軟體進行編輯，在3D 列印的增加方面越來越普遍。 使用 **Kinect 2** 感應器和 [3D Builder](https://developer.microsoft.com/windows/hardware/3d-print/3d-builder-resources) 您可以使用「捕捉」功能，從真實世界的物件建立資產。 這也是一 [套工具](https://en.wikipedia.org/wiki/Comparison_of_photogrammetry_software) ，可透過處理一些影像來拼接以及網格和材質，來與 **攝影測量** 相同。

### <a name="purchasing-assets"></a>購買資產

另一個絕佳的選項是購買資產以供您體驗。 有許多資產可透過 [Unity 資產存放區](https://www.assetstore.unity3d.com/) 或 [TurboSquid](https://www.turbosquid.com/) 等服務使用。

當您從協力廠商購買資產時，一律要檢查下列各項：
* **Poly 計數為何？**
  * 它是否適合您的預算？
* **模型有 (LODs) 的詳細資料層級嗎？**
  * 模型的詳細資料層級可讓您針對效能調整模型的詳細資料。
* **來源檔案是否可供使用？**
  * 通常不會隨附于 [Unity 資產存放區](https://www.assetstore.unity3d.com/) ，但一律會包含在服務（例如 [TurboSquid](https://www.turbosquid.com/)）中。
  * 如果沒有來源檔案，您將無法修改資產。
  * 請確定您的3D 工具可以匯入所提供的原始程式檔。
* **知道您要取得的內容**
  * 是否提供動畫？
  * 請務必檢查您所購買資產的內容清單。

### <a name="porting-assets"></a>移植資產

在某些情況下，您將會取得原本為其他裝置和不同應用程式建立的現有資產。 在大部分情況下，這些資產可以轉換成與應用程式所使用之圖形引擎相容的格式。

在您的 HoloLens 應用程式中移植要使用的資產時，您會想要詢問下列各項：
* **您可以直接匯入或需要轉換成另一種格式嗎？** 使用您所使用的圖形引擎來檢查您要匯入的格式。
* **如果轉換成相容的格式，是否有任何遺失？** 有時詳細資料可能會遺失或匯入，可能會導致需要在 3D authoring tool 中清除的成品。
* **資產的三角形/多邊形計數為何？** 根據您的應用程式預算，您可以使用 [Simplygon](https://www.simplygon.com/) 或類似的工具來刪減 (cti，或手動減少) 原始資產的 poly 計數，以符合您的應用程式預算。

### <a name="outsourcing-assets"></a>外包資產

如果大型專案需要比您的小組更多的資產，則另一個選項是建立資產建立。 外包的程式牽涉到尋找專門參與外包資產的適當 studio 或機構。 這可能是最昂貴的選項，但也是最具彈性的選項。
* **清楚地定義您所要求的內容**
  * 盡可能提供最多詳細資料
  * 前端和後端概念影像
  * 顯示內容中資產的參考圖片
  * 物件的小數位數 (通常以公分為單位指定) 
* **提供預算**
  * Poly 計數範圍
  * 紋理數目
  * Unity 和 HoloLens 的著色器 (類型，一律預設為行動著色器優先) 
* **瞭解成本**
  * 變更要求的外包原則是什麼？

外包可以根據您的專案時程表來運作得非常順利，但需要更多監督才能保證您第一次就能取得所需的正確資產。
