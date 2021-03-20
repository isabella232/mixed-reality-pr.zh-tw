---
title: ScreenshotUtility
description: 在 MRTK 中使用螢幕擷取畫面工具的 hopw 檔
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: 2f5110e0ad4cbad42dcbfef93a21dc34644bfe8d
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104694665"
---
# <a name="screenshot-utility"></a>螢幕擷取畫面公用程式

通常會在 Unity 中針對檔和宣傳影像拍攝螢幕擷取畫面，這可能會很麻煩，而且輸出通常看起來不太理想。 這就是 `ScreenshotUtility` (x： MixedReality，ScreenshotUtility) 類別的其中一種。

ScreenshotUtility 類別有助於在 Unity 編輯器中透過功能表項目和公用 Api 拍攝螢幕擷取畫面。 您可以使用各種解析度來捕捉螢幕擷取畫面，並以透明的純文字色彩來使用，以方便貼上影像的貼文。 此工具不支援從獨立組建拍攝螢幕擷取畫面。

## <a name="taking-screenshots"></a>拍攝螢幕擷取畫面

您可以在編輯器中選取 [ *混合現實工具組->公用程式->拍攝螢幕擷取畫面* ，然後選取您想要的選項，輕鬆地捕捉螢幕擷取畫面。 如果未播放，請務必顯示 [遊戲視窗] 索引標籤，否則可能不會儲存螢幕擷取畫面。

根據預設，所有螢幕擷取畫面都會儲存在您的暫存快取 [路徑](https://docs.unity3d.com/ScriptReference/Application-temporaryCachePath.html)中，並顯示在 Unity 主控台中的螢幕擷取畫面路徑。

![螢幕擷取畫面公用程式功能表項目](../Images/ScreenshotUtility/MRTK_ScreenshotUtility_Menu_Item.png)

## <a name="example-screenshot-capture"></a>範例螢幕擷取畫面

下列螢幕擷取畫面是以「 *4X 解析度 (透明背景)* 」選項來捕捉。 這會輸出高解析度的影像，其中包含一般以純文字形式儲存為透明圖元的任何圖元。 這項技術可協助開發人員藉由在其他影像上覆迭此影像，來展示其商店或其他媒體輸出的應用程式。

![螢幕擷取畫面公用程式抓取範例](../Images/ScreenshotUtility/MRTK_ScreenshotUtility_Example_Capture.png)
