---
title: Unreal 中的串流
description: Unreal 至 HoloLens 2 的串流指南
author: sw5813
ms.author: suwu
ms.date: 12/7/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 混合實境, 串流, 電腦, 全像攝影應用程式遠端處理, 全像攝影遠端播放程式, 文件, 混合實境頭戴式裝置, windows 混合實境頭戴式裝置, 虛擬實境頭戴式裝置
appliesto:
- HoloLens
- HoloLens 2
ms.openlocfilehash: 3638f07753355061f251bb2d6fa47233872d5b90
ms.sourcegitcommit: 0509cf6c57067cffd75a0189106e3369e9ecc5c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/08/2020
ms.locfileid: "96855878"
---
# <a name="streaming-in-unreal"></a><span data-ttu-id="2a6bc-104">Unreal 中的串流</span><span class="sxs-lookup"><span data-stu-id="2a6bc-104">Streaming in Unreal</span></span>

<span data-ttu-id="2a6bc-105">從電腦串流至 HoloLens 可提供兩大優點：</span><span class="sxs-lookup"><span data-stu-id="2a6bc-105">Streaming from a PC to HoloLens provides two major advantages:</span></span> 
* <span data-ttu-id="2a6bc-106">可讓您的混合實境應用程式利用電腦的計算能力。</span><span class="sxs-lookup"><span data-stu-id="2a6bc-106">It lets your mixed reality app take advantage of your PCs computational power.</span></span> 
* <span data-ttu-id="2a6bc-107">有助於加快開發反覆運算的時間。</span><span class="sxs-lookup"><span data-stu-id="2a6bc-107">It helps speed up development iteration time.</span></span> 

<span data-ttu-id="2a6bc-108">若要開始使用，您必須將[全像攝影遠端播放程式](../platform-capabilities-and-apis/holographic-remoting-player.md)下載到您的 HoloLens 裝置。</span><span class="sxs-lookup"><span data-stu-id="2a6bc-108">To get started, you'll need to download the [Holographic Remoting Player](../platform-capabilities-and-apis/holographic-remoting-player.md) to your HoloLens device.</span></span> <span data-ttu-id="2a6bc-109">全像攝影遠端播放程式可讓您的應用程式從下列來源直接串流至 HoloLens 上的遠端播放程式：</span><span class="sxs-lookup"><span data-stu-id="2a6bc-109">The Holographic Remoting Player lets your app to stream  directly to the remoting player on your HoloLens from the following sources:</span></span>

* <span data-ttu-id="2a6bc-110">Unreal Engine 編輯器</span><span class="sxs-lookup"><span data-stu-id="2a6bc-110">The Unreal Engine editor</span></span>
* <span data-ttu-id="2a6bc-111">已封裝的 Windows 可執行檔</span><span class="sxs-lookup"><span data-stu-id="2a6bc-111">A packaged Windows executable</span></span> 

<span data-ttu-id="2a6bc-112">進行串流時，您可以存取您在裝置上執行應用程式時可用的絕大多數 HoloLens 功能。</span><span class="sxs-lookup"><span data-stu-id="2a6bc-112">When streaming, you have access to almost all of the same HoloLens capabilities as you would when running an application on a device.</span></span> <span data-ttu-id="2a6bc-113">其中包括[手部關節追蹤](unreal-hand-tracking.md) (如果您是在 HoloLens 2 上)、[空間對應](unreal-spatial-mapping.md)和[空間錨點](unreal-spatial-anchors.md)，但不包括此[清單](../platform-capabilities-and-apis/holographic-remoting-troubleshooting.md)上的功能。</span><span class="sxs-lookup"><span data-stu-id="2a6bc-113">This includes [hand joint tracking](unreal-hand-tracking.md) if you're on a HoloLens 2, [spatial mapping](unreal-spatial-mapping.md), and [spatial anchors](unreal-spatial-anchors.md), but leaves out the features on this [list](../platform-capabilities-and-apis/holographic-remoting-troubleshooting.md).</span></span> 

> [!NOTE]
> * <span data-ttu-id="2a6bc-114">串流品質高度取決於您的 wifi 網路強度。</span><span class="sxs-lookup"><span data-stu-id="2a6bc-114">Streaming quality is highly dependent on the strength of your wifi network.</span></span>
> * <span data-ttu-id="2a6bc-115">全像攝影遠端處理播放程式會自動啟用所有功能。</span><span class="sxs-lookup"><span data-stu-id="2a6bc-115">All capabilities are automatically enabled for the holographic remoting player.</span></span> <span data-ttu-id="2a6bc-116">如果您發現某個功能需要使用者權限 (例如：眼睛追蹤)，才能透過串流方式來使用，但在裝置上執行時則不用，請檢查並確定您已在專案設定下啟用適當的功能。</span><span class="sxs-lookup"><span data-stu-id="2a6bc-116">If you find a capability that requires user permission (ex: eye tracking) to be working over streaming but not when running on device, check to ensure you've enabled the proper capabilities under your project settings.</span></span>

### <a name="streaming-limitations"></a><span data-ttu-id="2a6bc-117">串流限制</span><span class="sxs-lookup"><span data-stu-id="2a6bc-117">Streaming limitations</span></span>

<span data-ttu-id="2a6bc-118">手部網格、HoloLens 相機和系統鍵盤無法透過串流來使用。</span><span class="sxs-lookup"><span data-stu-id="2a6bc-118">Hand meshes, the HoloLens camera, and the system keyboard are unavailable over streaming.</span></span> <span data-ttu-id="2a6bc-119">請注意，您可以從串流來源電腦的麥克風獲得串流應用程式的語音輸入。</span><span class="sxs-lookup"><span data-stu-id="2a6bc-119">Note that speech input for streamed apps can be acquired via the microphone of the PC you are streaming from.</span></span>

#### <a name="openxr"></a><span data-ttu-id="2a6bc-120">OpenXR</span><span class="sxs-lookup"><span data-stu-id="2a6bc-120">OpenXR</span></span>

<span data-ttu-id="2a6bc-121">在 OpenXR 上執行的 Unreal 4.26 支援串流到全像攝影遠端播放程式的 2.4.0+ 版本。</span><span class="sxs-lookup"><span data-stu-id="2a6bc-121">Unreal 4.26 running on OpenXR supports streaming to versions 2.4.0+ of the Holographic Remoting Player.</span></span> <span data-ttu-id="2a6bc-122">在 2.4.0 中串流的 OpenXR 會失去對於空間對應和空間錨點的支援。</span><span class="sxs-lookup"><span data-stu-id="2a6bc-122">OpenXR streaming in 2.4.0 is missing support for spatial mapping and spatial anchors.</span></span> 

## <a name="device-support"></a><span data-ttu-id="2a6bc-123">裝置支援</span><span class="sxs-lookup"><span data-stu-id="2a6bc-123">Device support</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="2a6bc-124"><strong>來源</strong></span><span class="sxs-lookup"><span data-stu-id="2a6bc-124"><strong>Source</strong></span></span></td>
        <td><span data-ttu-id="2a6bc-125"><a href="https://docs.microsoft.com/hololens/hololens1-hardware"><strong>HoloLens 第一代</strong></a></span><span class="sxs-lookup"><span data-stu-id="2a6bc-125"><a href="https://docs.microsoft.com/hololens/hololens1-hardware"><strong>HoloLens first Gen</strong></a></span></span></td>
        <td><span data-ttu-id="2a6bc-126"><a href="https://www.microsoft.com/hololens/hardware"><strong>HoloLens 2</strong></a></span><span class="sxs-lookup"><span data-stu-id="2a6bc-126"><a href="https://www.microsoft.com/hololens/hardware"><strong>HoloLens 2</strong></a></span></span></td>
        <td><span data-ttu-id="2a6bc-127"><strong>沉浸式頭戴裝置</strong></span><span class="sxs-lookup"><span data-stu-id="2a6bc-127"><strong>Immersive Headsets</strong></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="2a6bc-128">Unreal 編輯器</span><span class="sxs-lookup"><span data-stu-id="2a6bc-128">Unreal editor</span></span></td>
        <td><span data-ttu-id="2a6bc-129">✔️</span><span class="sxs-lookup"><span data-stu-id="2a6bc-129">✔️</span></span></td>
        <td><span data-ttu-id="2a6bc-130">✔️</span><span class="sxs-lookup"><span data-stu-id="2a6bc-130">✔️</span></span></td>
        <td>❌</td>
    </tr>
    <tr>
        <td><span data-ttu-id="2a6bc-131">Windows 套件</span><span class="sxs-lookup"><span data-stu-id="2a6bc-131">Windows package</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="2a6bc-132">✔️</span><span class="sxs-lookup"><span data-stu-id="2a6bc-132">✔️</span></span></td>
        <td>❌</td>
    </tr>

</table>

## <a name="streaming-from-the-unreal-editor"></a><span data-ttu-id="2a6bc-133">從 Unreal 編輯器進行串流</span><span class="sxs-lookup"><span data-stu-id="2a6bc-133">Streaming from the Unreal editor</span></span>

<span data-ttu-id="2a6bc-134">身為開發人員，您會發現從 Unreal 編輯器串流至 HoloLens 裝置可在測試時提供很大的好處，也就是您不再需要等到應用程式完成建置和部署，才能試用您的更新。</span><span class="sxs-lookup"><span data-stu-id="2a6bc-134">As a developer, you'll find that streaming from the Unreal editor to your HoloLens device provides significant benefits when testing, namely that you no longer have to wait for your app to build and deploy before trying out your updates.</span></span>

<span data-ttu-id="2a6bc-135">您可以在教學課程系列中找到[從 Unreal 編輯器進行串流](tutorials/unreal-uxt-ch6.md#device-only-streaming)的詳細指示。</span><span class="sxs-lookup"><span data-stu-id="2a6bc-135">You can find detailed instructions for [streaming from the Unreal editor](tutorials/unreal-uxt-ch6.md#device-only-streaming) in our tutorial series.</span></span>

## <a name="streaming-from-a-packaged-windows-executable"></a><span data-ttu-id="2a6bc-136">從已封裝的 Windows 可執行檔進行串流</span><span class="sxs-lookup"><span data-stu-id="2a6bc-136">Streaming from a packaged Windows executable</span></span>

<span data-ttu-id="2a6bc-137">在 Unreal 4.25.1 和後續版本中，您可以從已封裝的 Windows 可執行檔將應用程式串流至 HoloLens 2 裝置：</span><span class="sxs-lookup"><span data-stu-id="2a6bc-137">In Unreal 4.25.1 and onwards, you can stream your app to a HoloLens 2 device from a packaged Windows executable:</span></span> 

1. <span data-ttu-id="2a6bc-138">在 [編輯器] 功能表中，移至 [檔案] > [封裝專案] > [Windows]。</span><span class="sxs-lookup"><span data-stu-id="2a6bc-138">Go to **File > Package Project > Windows** in the editor menu.</span></span> 
    * <span data-ttu-id="2a6bc-139">選擇要儲存套件的位置，然後選取 [選取資料夾]。</span><span class="sxs-lookup"><span data-stu-id="2a6bc-139">Choose a location to save your package and select **Select Folder**.</span></span>

2. <span data-ttu-id="2a6bc-140">套件完成建置後，請在 HoloLens 2 上開啟 [全像攝影遠端播放程式]，並記下 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="2a6bc-140">Once the package has finished building, open the **Holographic Remoting Player** on your HoloLens 2 and make note of the IP Address.</span></span> 
3. <span data-ttu-id="2a6bc-141">將 [全像攝影遠端播放程式] 保持開啟，並使用命令列提示字元執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="2a6bc-141">Leave the **Holographic Remoting Player** open and use the command line prompt to:</span></span> 
    * <span data-ttu-id="2a6bc-142">切換至套件儲存所在的本機目錄中。</span><span class="sxs-lookup"><span data-stu-id="2a6bc-142">cd into the local directory where you saved your package.</span></span>
    * <span data-ttu-id="2a6bc-143">輸入下列命令：`<App Name>.exe -vr -HoloLensRemoting=<IP Address>`</span><span class="sxs-lookup"><span data-stu-id="2a6bc-143">Enter the following command: `<App Name>.exe -vr -HoloLensRemoting=<IP Address>`</span></span>

> [!NOTE]
> <span data-ttu-id="2a6bc-144">系統應該會自動使用您專案設定中的應用程式名稱來建立 Windows 套件。</span><span class="sxs-lookup"><span data-stu-id="2a6bc-144">The application name in your project settings should be automatically used to create the Windows package.</span></span> <span data-ttu-id="2a6bc-145">如果這些設定因某些原因而有所不同，請在命令提示字元中使用 Windows 可執行檔名稱。</span><span class="sxs-lookup"><span data-stu-id="2a6bc-145">If these are different for some reason, use the Windows executable name in the command prompt.</span></span>

<span data-ttu-id="2a6bc-146">按 Enter 鍵，您的應用程式即會開始串流！</span><span class="sxs-lookup"><span data-stu-id="2a6bc-146">Hit enter and watch your application start streaming!</span></span>

### <a name="command-line-options"></a><span data-ttu-id="2a6bc-147">命令列選項</span><span class="sxs-lookup"><span data-stu-id="2a6bc-147">Command line options</span></span>

<span data-ttu-id="2a6bc-148">您可以在下表中找到可從 Unreal Engine 4.26+ 中的每個平台進行串流的其他命令列選項。</span><span class="sxs-lookup"><span data-stu-id="2a6bc-148">Additional command line options for streaming from each platform in Unreal Engine 4.26+ can be found in the table below.</span></span> 

[!INCLUDE[](includes/tabs-streaming-args.md)]

## <a name="see-also"></a><span data-ttu-id="2a6bc-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2a6bc-149">See also</span></span>

* [<span data-ttu-id="2a6bc-150">全像攝影遠端處理版本歷程記錄</span><span class="sxs-lookup"><span data-stu-id="2a6bc-150">Holographic remoting version history</span></span>](../platform-capabilities-and-apis/holographic-remoting-version-history.md)
* [<span data-ttu-id="2a6bc-151">撰寫自訂全像攝影遠端播放應用程式</span><span class="sxs-lookup"><span data-stu-id="2a6bc-151">Writing a custom Holographic Remoting player app</span></span>](../platform-capabilities-and-apis/holographic-remoting-create-player.md)
* [<span data-ttu-id="2a6bc-152">建立全像攝影遠端處理的連線安全</span><span class="sxs-lookup"><span data-stu-id="2a6bc-152">Establishing a secure connection with Holographic Remoting</span></span>](../platform-capabilities-and-apis/holographic-remoting-secure-connection.md)
