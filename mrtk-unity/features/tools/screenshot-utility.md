---
title: 螢幕擷取畫面公用程式
description: 在 MRTK 中使用螢幕擷取畫面工具的 hopw 檔
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: 59bf0df2a32030281c8bf0a1a8574b4dd9bf4607
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143798"
---
# <a name="screenshot-utility"></a><span data-ttu-id="fdb2f-104">螢幕擷取畫面公用程式</span><span class="sxs-lookup"><span data-stu-id="fdb2f-104">Screenshot utility</span></span>

<span data-ttu-id="fdb2f-105">通常會在 Unity 中針對檔和宣傳影像拍攝螢幕擷取畫面，這可能會很麻煩，而且輸出通常看起來不太理想。</span><span class="sxs-lookup"><span data-stu-id="fdb2f-105">Often taking screenshots in Unity for documentation and promotional imagery can be burdensome and the output often looks less than desirable.</span></span> <span data-ttu-id="fdb2f-106">這就是 `ScreenshotUtility` (x： MixedReality，ScreenshotUtility) 類別的其中一種。</span><span class="sxs-lookup"><span data-stu-id="fdb2f-106">This is where the `ScreenshotUtility` (xref:Microsoft.MixedReality.Toolkit.Utilities.Editor.ScreenshotUtility) class comes into play.</span></span>

<span data-ttu-id="fdb2f-107">ScreenshotUtility 類別有助於在 Unity 編輯器中透過功能表項目和公用 Api 拍攝螢幕擷取畫面。</span><span class="sxs-lookup"><span data-stu-id="fdb2f-107">The ScreenshotUtility class aides in taking screenshots via menu items and public APIs within the Unity editor.</span></span> <span data-ttu-id="fdb2f-108">您可以使用各種解析度來捕捉螢幕擷取畫面，並以透明的純文字色彩來使用，以方便貼上影像的貼文。</span><span class="sxs-lookup"><span data-stu-id="fdb2f-108">Screenshots can be captured at various resolutions and with transparent clear colors for use in easy post compositing of images.</span></span> <span data-ttu-id="fdb2f-109">此工具不支援從獨立組建拍攝螢幕擷取畫面。</span><span class="sxs-lookup"><span data-stu-id="fdb2f-109">Taking screenshots from a standalone build is not supported by this tool.</span></span>

## <a name="taking-screenshots"></a><span data-ttu-id="fdb2f-110">拍攝螢幕擷取畫面</span><span class="sxs-lookup"><span data-stu-id="fdb2f-110">Taking screenshots</span></span>

<span data-ttu-id="fdb2f-111">您可以在編輯器中選取 [ *混合現實工具組->公用程式->拍攝螢幕擷取畫面* ，然後選取您想要的選項，輕鬆地捕捉螢幕擷取畫面。</span><span class="sxs-lookup"><span data-stu-id="fdb2f-111">Screenshots can be easily capture while in the editor by selecting *Mixed Reality Toolkit->Utilities->Take Screenshot* and then selecting your desired option.</span></span> <span data-ttu-id="fdb2f-112">如果未播放，請務必顯示 [遊戲視窗] 索引標籤，否則可能不會儲存螢幕擷取畫面。</span><span class="sxs-lookup"><span data-stu-id="fdb2f-112">Make sure to have the game window tab visible if capturing while not playing, or a screenshot may not be saved.</span></span>

<span data-ttu-id="fdb2f-113">根據預設，所有螢幕擷取畫面都會儲存在您的暫存快取 [路徑](https://docs.unity3d.com/ScriptReference/Application-temporaryCachePath.html)中，並顯示在 Unity 主控台中的螢幕擷取畫面路徑。</span><span class="sxs-lookup"><span data-stu-id="fdb2f-113">By default, all screenshots are saved to your [temporary cache path](https://docs.unity3d.com/ScriptReference/Application-temporaryCachePath.html), the path to the screenshot will be displayed in the Unity console.</span></span>

![螢幕擷取畫面公用程式功能表項目](../images/screenshot-utility/MRTK_ScreenshotUtility_Menu_Item.png)

## <a name="example-screenshot-capture"></a><span data-ttu-id="fdb2f-115">範例螢幕擷取畫面</span><span class="sxs-lookup"><span data-stu-id="fdb2f-115">Example screenshot capture</span></span>

<span data-ttu-id="fdb2f-116">下列螢幕擷取畫面是以「 *4X 解析度 (透明背景)* 」選項來捕捉。</span><span class="sxs-lookup"><span data-stu-id="fdb2f-116">The below screenshot was captured with the *"4x Resolution (Transparent Background)"* option.</span></span> <span data-ttu-id="fdb2f-117">這會輸出高解析度的影像，其中包含一般以純文字形式儲存為透明圖元的任何圖元。</span><span class="sxs-lookup"><span data-stu-id="fdb2f-117">This outputs a high-resolution image with whatever pixels normally represented by the clear color saved as transparent pixels.</span></span> <span data-ttu-id="fdb2f-118">這項技術可協助開發人員藉由在其他影像上覆迭此影像，來展示其商店或其他媒體輸出的應用程式。</span><span class="sxs-lookup"><span data-stu-id="fdb2f-118">This technique helps developers showcase their application for the store, or other media outlets, by overlaying this image on top of other imagery.</span></span>

![螢幕擷取畫面公用程式抓取範例](../images/screenshot-utility/MRTK_ScreenshotUtility_Example_Capture.png)
