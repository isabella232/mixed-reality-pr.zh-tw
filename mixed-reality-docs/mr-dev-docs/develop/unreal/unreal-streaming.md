---
title: Unreal 中的串流
description: Unreal 至 HoloLens 2 的串流指南
author: sw5813
ms.author: suwu
ms.date: 7/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 混合實境, 串流, 電腦, 全像攝影應用程式遠端處理, 全像攝影遠端播放程式, 文件, 混合實境頭戴式裝置, windows 混合實境頭戴式裝置, 虛擬實境頭戴式裝置
appliesto:
- HoloLens
- HoloLens 2
ms.openlocfilehash: 9cbde33ce7238d704d4b24b4afbed9d8306d4e4d
ms.sourcegitcommit: 32cb81eee976e73cd661c2b347691c37865a60bc
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/04/2020
ms.locfileid: "96609329"
---
# <a name="streaming-in-unreal"></a><span data-ttu-id="f0614-104">Unreal 中的串流</span><span class="sxs-lookup"><span data-stu-id="f0614-104">Streaming in Unreal</span></span>

<span data-ttu-id="f0614-105">從電腦串流至 HoloLens 可提供兩大優點：</span><span class="sxs-lookup"><span data-stu-id="f0614-105">Streaming from a PC to HoloLens provides two major advantages:</span></span> 
* <span data-ttu-id="f0614-106">可讓您的混合實境應用程式利用電腦的計算能力。</span><span class="sxs-lookup"><span data-stu-id="f0614-106">It lets your mixed reality app take advantage of your PCs computational power.</span></span> 
* <span data-ttu-id="f0614-107">有助於加快開發反覆運算的時間。</span><span class="sxs-lookup"><span data-stu-id="f0614-107">It helps speed up development iteration time.</span></span> 

<span data-ttu-id="f0614-108">若要開始使用，您必須將[全像攝影遠端播放程式](../platform-capabilities-and-apis/holographic-remoting-player.md)下載到您的 HoloLens 裝置。</span><span class="sxs-lookup"><span data-stu-id="f0614-108">To get started, you'll need to download the [Holographic Remoting Player](../platform-capabilities-and-apis/holographic-remoting-player.md) to your HoloLens device.</span></span> <span data-ttu-id="f0614-109">全像攝影遠端播放程式可讓您的應用程式從下列來源直接串流至 HoloLens 上的遠端播放程式：</span><span class="sxs-lookup"><span data-stu-id="f0614-109">The Holographic Remoting Player lets your app to stream  directly to the remoting player on your HoloLens from the following sources:</span></span>

* <span data-ttu-id="f0614-110">Unreal Engine 編輯器</span><span class="sxs-lookup"><span data-stu-id="f0614-110">The Unreal Engine editor</span></span>
* <span data-ttu-id="f0614-111">已封裝的 Windows 可執行檔</span><span class="sxs-lookup"><span data-stu-id="f0614-111">A packaged Windows executable</span></span> 

<span data-ttu-id="f0614-112">進行串流時，您可以存取您在裝置上執行應用程式時可用的絕大多數 HoloLens 功能。</span><span class="sxs-lookup"><span data-stu-id="f0614-112">When streaming, you have access to almost all of the same HoloLens capabilities as you would when running an application on a device.</span></span> <span data-ttu-id="f0614-113">其中包括[手部關節追蹤](unreal-hand-tracking.md) (如果您是在 HoloLens 2 上)、[空間對應](unreal-spatial-mapping.md)和[空間錨點](unreal-spatial-anchors.md)，但不包括此[清單](../platform-capabilities-and-apis/holographic-remoting-troubleshooting.md)上的功能。</span><span class="sxs-lookup"><span data-stu-id="f0614-113">This includes [hand joint tracking](unreal-hand-tracking.md) if you're on a HoloLens 2, [spatial mapping](unreal-spatial-mapping.md), and [spatial anchors](unreal-spatial-anchors.md), but leaves out the features on this [list](../platform-capabilities-and-apis/holographic-remoting-troubleshooting.md).</span></span> 

> [!NOTE]
> * <span data-ttu-id="f0614-114">串流品質高度取決於您的 wifi 網路強度。</span><span class="sxs-lookup"><span data-stu-id="f0614-114">Streaming quality is highly dependent on the strength of your wifi network.</span></span>
> * <span data-ttu-id="f0614-115">全像攝影遠端處理播放程式會自動啟用所有功能。</span><span class="sxs-lookup"><span data-stu-id="f0614-115">All capabilities are automatically enabled for the holographic remoting player.</span></span> <span data-ttu-id="f0614-116">如果您發現某個功能需要使用者權限 (例如：眼睛追蹤)，才能透過串流方式來使用，但在裝置上執行時則不用，請檢查並確定您已在專案設定下啟用適當的功能。</span><span class="sxs-lookup"><span data-stu-id="f0614-116">If you find a capability that requires user permission (ex: eye tracking) to be working over streaming but not when running on device, check to ensure you've enabled the proper capabilities under your project settings.</span></span>

## <a name="device-support"></a><span data-ttu-id="f0614-117">裝置支援</span><span class="sxs-lookup"><span data-stu-id="f0614-117">Device support</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="f0614-118"><strong>來源</strong></span><span class="sxs-lookup"><span data-stu-id="f0614-118"><strong>Source</strong></span></span></td>
        <td><span data-ttu-id="f0614-119"><a href="https://docs.microsoft.com/hololens/hololens1-hardware"><strong>HoloLens 第一代</strong></a></span><span class="sxs-lookup"><span data-stu-id="f0614-119"><a href="https://docs.microsoft.com/hololens/hololens1-hardware"><strong>HoloLens first Gen</strong></a></span></span></td>
        <td><span data-ttu-id="f0614-120"><a href="https://www.microsoft.com/hololens/hardware"><strong>HoloLens 2</strong></a></span><span class="sxs-lookup"><span data-stu-id="f0614-120"><a href="https://www.microsoft.com/hololens/hardware"><strong>HoloLens 2</strong></a></span></span></td>
        <td><span data-ttu-id="f0614-121"><strong>沉浸式頭戴裝置</strong></span><span class="sxs-lookup"><span data-stu-id="f0614-121"><strong>Immersive Headsets</strong></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="f0614-122">Unreal 編輯器</span><span class="sxs-lookup"><span data-stu-id="f0614-122">Unreal editor</span></span></td>
        <td><span data-ttu-id="f0614-123">✔️</span><span class="sxs-lookup"><span data-stu-id="f0614-123">✔️</span></span></td>
        <td><span data-ttu-id="f0614-124">✔️</span><span class="sxs-lookup"><span data-stu-id="f0614-124">✔️</span></span></td>
        <td>❌</td>
    </tr>
    <tr>
        <td><span data-ttu-id="f0614-125">Windows 套件</span><span class="sxs-lookup"><span data-stu-id="f0614-125">Windows package</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="f0614-126">✔️</span><span class="sxs-lookup"><span data-stu-id="f0614-126">✔️</span></span></td>
        <td>❌</td>
    </tr>

</table>

## <a name="streaming-from-the-unreal-editor"></a><span data-ttu-id="f0614-127">從 Unreal 編輯器進行串流</span><span class="sxs-lookup"><span data-stu-id="f0614-127">Streaming from the Unreal editor</span></span>

<span data-ttu-id="f0614-128">身為開發人員，您會發現從 Unreal 編輯器串流至 HoloLens 裝置可在測試時提供很大的好處，也就是您不再需要等到應用程式完成建置和部署，才能試用您的更新。</span><span class="sxs-lookup"><span data-stu-id="f0614-128">As a developer, you'll find that streaming from the Unreal editor to your HoloLens device provides significant benefits when testing, namely that you no longer have to wait for your app to build and deploy before trying out your updates.</span></span>

<span data-ttu-id="f0614-129">您可以在教學課程系列中找到[從 Unreal 編輯器進行串流](tutorials/unreal-uxt-ch6.md#device-only-streaming)的詳細指示。</span><span class="sxs-lookup"><span data-stu-id="f0614-129">You can find detailed instructions for [streaming from the Unreal editor](tutorials/unreal-uxt-ch6.md#device-only-streaming) in our tutorial series.</span></span>

## <a name="streaming-from-a-packaged-windows-executable"></a><span data-ttu-id="f0614-130">從已封裝的 Windows 可執行檔進行串流</span><span class="sxs-lookup"><span data-stu-id="f0614-130">Streaming from a packaged Windows executable</span></span>

<span data-ttu-id="f0614-131">在 Unreal 4.25.1 和後續版本中，您可以從已封裝的 Windows 可執行檔將應用程式串流至 HoloLens 2 裝置：</span><span class="sxs-lookup"><span data-stu-id="f0614-131">In Unreal 4.25.1 and onwards, you can stream your app to a HoloLens 2 device from a packaged Windows executable:</span></span> 

1. <span data-ttu-id="f0614-132">在 [編輯器] 功能表中，移至 [檔案] > [封裝專案] > [Windows]。</span><span class="sxs-lookup"><span data-stu-id="f0614-132">Go to **File > Package Project > Windows** in the editor menu.</span></span> 
    * <span data-ttu-id="f0614-133">選擇要儲存套件的位置，然後選取 [選取資料夾]。</span><span class="sxs-lookup"><span data-stu-id="f0614-133">Choose a location to save your package and select **Select Folder**.</span></span>

2. <span data-ttu-id="f0614-134">套件完成建置後，請在 HoloLens 2 上開啟 [全像攝影遠端播放程式]，並記下 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="f0614-134">Once the package has finished building, open the **Holographic Remoting Player** on your HoloLens 2 and make note of the IP Address.</span></span> 
3. <span data-ttu-id="f0614-135">將 [全像攝影遠端播放程式] 保持開啟，並使用命令列提示字元執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="f0614-135">Leave the **Holographic Remoting Player** open and use the command line prompt to:</span></span> 
    * <span data-ttu-id="f0614-136">切換至套件儲存所在的本機目錄中。</span><span class="sxs-lookup"><span data-stu-id="f0614-136">cd into the local directory where you saved your package.</span></span>
    * <span data-ttu-id="f0614-137">輸入下列命令：```<App Name>.exe -vr -HoloLensRemoting=<IP Address>```</span><span class="sxs-lookup"><span data-stu-id="f0614-137">Enter the following command: ```<App Name>.exe -vr -HoloLensRemoting=<IP Address>```</span></span>

> [!NOTE]
> <span data-ttu-id="f0614-138">系統應該會自動使用您專案設定中的應用程式名稱來建立 Windows 套件。</span><span class="sxs-lookup"><span data-stu-id="f0614-138">The application name in your project settings should be automatically used to create the Windows package.</span></span> <span data-ttu-id="f0614-139">如果這些設定因某些原因而有所不同，請在命令提示字元中使用 Windows 可執行檔名稱。</span><span class="sxs-lookup"><span data-stu-id="f0614-139">If these are different for some reason, use the Windows executable name in the command prompt.</span></span>

<span data-ttu-id="f0614-140">按 Enter 鍵，您的應用程式即會開始串流！</span><span class="sxs-lookup"><span data-stu-id="f0614-140">Hit enter and watch your application start streaming!</span></span>

## <a name="see-also"></a><span data-ttu-id="f0614-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f0614-141">See also</span></span>

* [<span data-ttu-id="f0614-142">全像攝影遠端處理版本歷程記錄</span><span class="sxs-lookup"><span data-stu-id="f0614-142">Holographic remoting version history</span></span>](../platform-capabilities-and-apis/holographic-remoting-version-history.md)
* [<span data-ttu-id="f0614-143">撰寫自訂全像攝影遠端播放應用程式</span><span class="sxs-lookup"><span data-stu-id="f0614-143">Writing a custom Holographic Remoting player app</span></span>](../platform-capabilities-and-apis/holographic-remoting-create-player.md)
* [<span data-ttu-id="f0614-144">建立全像攝影遠端處理的連線安全</span><span class="sxs-lookup"><span data-stu-id="f0614-144">Establishing a secure connection with Holographic Remoting</span></span>](../platform-capabilities-and-apis/holographic-remoting-secure-connection.md)
