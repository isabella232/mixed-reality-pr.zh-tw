---
title: ScreenshotUtility
description: 在 MRTK 中使用螢幕擷取畫面工具的 hopw 檔
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: 4fbd5457dd0af502ddedf30a10482690cd8e1a1d
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104683961"
---
# <a name="screenshot-utility"></a><span data-ttu-id="6d62d-104">螢幕擷取畫面公用程式</span><span class="sxs-lookup"><span data-stu-id="6d62d-104">Screenshot utility</span></span>

<span data-ttu-id="6d62d-105">通常會在 Unity 中針對檔和宣傳影像拍攝螢幕擷取畫面，這可能會很麻煩，而且輸出通常看起來不太理想。</span><span class="sxs-lookup"><span data-stu-id="6d62d-105">Often taking screenshots in Unity for documentation and promotional imagery can be burdensome and the output often looks less than desirable.</span></span> <span data-ttu-id="6d62d-106">這就是 `ScreenshotUtility` (x： MixedReality，ScreenshotUtility) 類別的其中一種。</span><span class="sxs-lookup"><span data-stu-id="6d62d-106">This is where the `ScreenshotUtility` (xref:Microsoft.MixedReality.Toolkit.Utilities.Editor.ScreenshotUtility) class comes into play.</span></span>

<span data-ttu-id="6d62d-107">ScreenshotUtility 類別有助於在 Unity 編輯器中透過功能表項目和公用 Api 拍攝螢幕擷取畫面。</span><span class="sxs-lookup"><span data-stu-id="6d62d-107">The ScreenshotUtility class aides in taking screenshots via menu items and public APIs within the Unity editor.</span></span> <span data-ttu-id="6d62d-108">您可以使用各種解析度來捕捉螢幕擷取畫面，並以透明的純文字色彩來使用，以方便貼上影像的貼文。</span><span class="sxs-lookup"><span data-stu-id="6d62d-108">Screenshots can be captured at various resolutions and with transparent clear colors for use in easy post compositing of images.</span></span> <span data-ttu-id="6d62d-109">此工具不支援從獨立組建拍攝螢幕擷取畫面。</span><span class="sxs-lookup"><span data-stu-id="6d62d-109">Taking screenshots from a standalone build is not supported by this tool.</span></span>

## <a name="taking-screenshots"></a><span data-ttu-id="6d62d-110">拍攝螢幕擷取畫面</span><span class="sxs-lookup"><span data-stu-id="6d62d-110">Taking screenshots</span></span>

<span data-ttu-id="6d62d-111">您可以在編輯器中選取 [ *混合現實工具組->公用程式->拍攝螢幕擷取畫面* ，然後選取您想要的選項，輕鬆地捕捉螢幕擷取畫面。</span><span class="sxs-lookup"><span data-stu-id="6d62d-111">Screenshots can be easily capture while in the editor by selecting *Mixed Reality Toolkit->Utilities->Take Screenshot* and then selecting your desired option.</span></span> <span data-ttu-id="6d62d-112">如果未播放，請務必顯示 [遊戲視窗] 索引標籤，否則可能不會儲存螢幕擷取畫面。</span><span class="sxs-lookup"><span data-stu-id="6d62d-112">Make sure to have the game window tab visible if capturing while not playing, or a screenshot may not be saved.</span></span>

<span data-ttu-id="6d62d-113">根據預設，所有螢幕擷取畫面都會儲存在您的暫存快取 [路徑](https://docs.unity3d.com/ScriptReference/Application-temporaryCachePath.html)中，並顯示在 Unity 主控台中的螢幕擷取畫面路徑。</span><span class="sxs-lookup"><span data-stu-id="6d62d-113">By default, all screenshots are saved to your [temporary cache path](https://docs.unity3d.com/ScriptReference/Application-temporaryCachePath.html), the path to the screenshot will be displayed in the Unity console.</span></span>

![螢幕擷取畫面公用程式功能表項目](../images/screenshot-utility/MRTK_ScreenshotUtility_Menu_Item.png)

## <a name="example-screenshot-capture"></a><span data-ttu-id="6d62d-115">範例螢幕擷取畫面</span><span class="sxs-lookup"><span data-stu-id="6d62d-115">Example screenshot capture</span></span>

<span data-ttu-id="6d62d-116">下列螢幕擷取畫面是以「 *4X 解析度 (透明背景)* 」選項來捕捉。</span><span class="sxs-lookup"><span data-stu-id="6d62d-116">The below screenshot was captured with the *"4x Resolution (Transparent Background)"* option.</span></span> <span data-ttu-id="6d62d-117">這會輸出高解析度的影像，其中包含一般以純文字形式儲存為透明圖元的任何圖元。</span><span class="sxs-lookup"><span data-stu-id="6d62d-117">This outputs a high-resolution image with whatever pixels normally represented by the clear color saved as transparent pixels.</span></span> <span data-ttu-id="6d62d-118">這項技術可協助開發人員藉由在其他影像上覆迭此影像，來展示其商店或其他媒體輸出的應用程式。</span><span class="sxs-lookup"><span data-stu-id="6d62d-118">This technique helps developers showcase their application for the store, or other media outlets, by overlaying this image on top of other imagery.</span></span>

![螢幕擷取畫面公用程式抓取範例](../images/screenshot-utility/MRTK_ScreenshotUtility_Example_Capture.png)
