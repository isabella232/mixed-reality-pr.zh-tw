---
title: HoloLens 研究模式
description: 在 HoloLens 上使用 Research 模式時，應用程式可以存取主要裝置感應器串流 (深度、環境追蹤和 IR 反射率) 。
author: hferrone
ms.author: v-hferrone
ms.date: 07/31/2020
ms.topic: article
keywords: 研究模式、cv、rs4、電腦視覺、研究、HoloLens、HoloLens 2
ms.openlocfilehash: 327ee932dce99a2559e406630611dcc3c69a0002
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2020
ms.locfileid: "91679904"
---
# <a name="hololens-research-mode"></a><span data-ttu-id="69b03-104">HoloLens 研究模式</span><span class="sxs-lookup"><span data-stu-id="69b03-104">HoloLens Research Mode</span></span>

<span data-ttu-id="69b03-105">Research 模式是在第1代的 HoloLens 中引進，可讓您存取裝置上的主要感應器，特別是研究不打算進行部署的應用程式。</span><span class="sxs-lookup"><span data-stu-id="69b03-105">Research Mode was introduced in the 1st Generation HoloLens to give access to key sensors on the device, specifically for research applications that are not intended for deployment.</span></span>  <span data-ttu-id="69b03-106">HoloLens 2 的研究模式會保留 HoloLens 1 的功能，並新增其他串流的存取權：</span><span class="sxs-lookup"><span data-stu-id="69b03-106">Research Mode for HoloLens 2 retains the capabilities of HoloLens 1, adding access to additional streams:</span></span>

* <span data-ttu-id="69b03-107">**可見的光線環境追蹤攝影機** -系統用來追蹤和地圖大樓的灰色縮放相機。</span><span class="sxs-lookup"><span data-stu-id="69b03-107">**Visible Light Environment Tracking Cameras** - Gray-scale cameras used by the system for head tracking and map building.</span></span>
* <span data-ttu-id="69b03-108">**深度相機** –以兩種模式運作：</span><span class="sxs-lookup"><span data-stu-id="69b03-108">**Depth Camera** – Operates in two modes:</span></span>  
    + <span data-ttu-id="69b03-109">AHAT、高頻率 (45 FPS) 用於手動追蹤的近深度感知。</span><span class="sxs-lookup"><span data-stu-id="69b03-109">AHAT, high-frequency (45 FPS) near-depth sensing used for hand tracking.</span></span> <span data-ttu-id="69b03-110">與第1版的簡短擲回模式不同的是，AHAT 提供的虛擬深度與1計量以外的階段換行。</span><span class="sxs-lookup"><span data-stu-id="69b03-110">Differently from the 1st version short-throw mode, AHAT gives pseudo-depth with phase wrap beyond 1 meter.</span></span> 
    + <span data-ttu-id="69b03-111">長時間擲回、低頻率 (1-5 FPS) [空間對應](../../design/spatial-mapping.md)所使用的深度感應</span><span class="sxs-lookup"><span data-stu-id="69b03-111">Long-throw, low-frequency (1-5 FPS) far-depth sensing used by [Spatial Mapping](../../design/spatial-mapping.md)</span></span>

* <span data-ttu-id="69b03-112">**兩個版本的 IR 反射率串流** -由 HoloLens 用來計算深度。</span><span class="sxs-lookup"><span data-stu-id="69b03-112">**Two versions of the IR-reflectivity stream** - Used by the HoloLens to compute depth.</span></span> <span data-ttu-id="69b03-113">這些影像會由紅外線發亮，並不受環境可見的光線影響。</span><span class="sxs-lookup"><span data-stu-id="69b03-113">These images are illuminated by infrared and unaffected by ambient visible light.</span></span>

<span data-ttu-id="69b03-114">如果您是使用 HoloLens 2 也可以存取下列其他輸入：</span><span class="sxs-lookup"><span data-stu-id="69b03-114">If you're using a HoloLens 2 you also have access to the additional inputs below:</span></span>

* <span data-ttu-id="69b03-115">**加速** 計–由系統用來判斷沿著 X、Y 和 Z 軸和重力的線性加速。</span><span class="sxs-lookup"><span data-stu-id="69b03-115">**Accelerometer** – Used by the system to determine linear acceleration along the X, Y and Z axes and gravity.</span></span>
* <span data-ttu-id="69b03-116">**回轉** –系統用來判斷旋轉。</span><span class="sxs-lookup"><span data-stu-id="69b03-116">**Gyro** – Used by the system to determine rotations.</span></span>
* <span data-ttu-id="69b03-117">**磁力計** –由系統用來估計絕對方向。</span><span class="sxs-lookup"><span data-stu-id="69b03-117">**Magnetometer** – Used by the system to estimate absolute orientation.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="69b03-118">研究模式目前為公開預覽狀態。</span><span class="sxs-lookup"><span data-stu-id="69b03-118">Research Mode is currently in Public Preview.</span></span> 

<span data-ttu-id="69b03-119">![研究模式應用程式螢幕擷取畫面](images/sensor-stream-viewer.jpg)</span><span class="sxs-lookup"><span data-stu-id="69b03-119">![Research Mode app screenshot](images/sensor-stream-viewer.jpg)</span></span><br>
<span data-ttu-id="69b03-120">*測試應用程式的混合現實捕捉，可顯示研究模式中可用的八個感應器串流*</span><span class="sxs-lookup"><span data-stu-id="69b03-120">*A mixed reality capture of a test application that displays the eight sensor streams available in Research Mode*</span></span>

## <a name="usage"></a><span data-ttu-id="69b03-121">使用方式</span><span class="sxs-lookup"><span data-stu-id="69b03-121">Usage</span></span>

<span data-ttu-id="69b03-122">研究模式是專為學術和產業研究人員所設計，可在電腦視覺和機器人的領域中探索新構想。</span><span class="sxs-lookup"><span data-stu-id="69b03-122">Research Mode is designed for academic and industrial researchers exploring new ideas in the fields of Computer Vision and Robotics.</span></span>  <span data-ttu-id="69b03-123">它不適用於企業環境中部署的應用程式，或可透過 Microsoft Store 或其他散發通道使用的應用程式。</span><span class="sxs-lookup"><span data-stu-id="69b03-123">It's not intended for applications deployed in enterprise environments or available through the Microsoft Store or other distribution channels.</span></span>

<span data-ttu-id="69b03-124">此外，Microsoft 不保證未來的硬體或作業系統更新將會支援研究模式或同等功能。</span><span class="sxs-lookup"><span data-stu-id="69b03-124">Additionally, Microsoft doesn't provide assurances that Research Mode or equivalent functionality is going to be supported in future hardware or OS updates.</span></span> <span data-ttu-id="69b03-125">不過，這不應該阻止您使用它來開發和測試新的想法！</span><span class="sxs-lookup"><span data-stu-id="69b03-125">However, this shouldn't stop you from using it to develop and test new ideas!</span></span>

## <a name="security-and-performance"></a><span data-ttu-id="69b03-126">安全性和效能</span><span class="sxs-lookup"><span data-stu-id="69b03-126">Security and performance</span></span>

<span data-ttu-id="69b03-127">請注意，在正常情況下，啟用 Research 模式所使用的電池電力會比使用 HoloLens 2 更高。</span><span class="sxs-lookup"><span data-stu-id="69b03-127">Be aware that enabling Research Mode uses more battery power than using the HoloLens 2 under normal conditions.</span></span> <span data-ttu-id="69b03-128">即使使用研究模式功能的應用程式不在執行中，也是如此。</span><span class="sxs-lookup"><span data-stu-id="69b03-128">This is true even if the application using the Research Mode features is not running.</span></span>  <span data-ttu-id="69b03-129">啟用此模式也會降低裝置的整體安全性，因為應用程式可能會誤用感應器資料。</span><span class="sxs-lookup"><span data-stu-id="69b03-129">Enabling this mode can also lower the overall security of your device because applications may misuse sensor data.</span></span>  <span data-ttu-id="69b03-130">您可以在 [HoloLens 安全性常見問題](https://docs.microsoft.com/hololens/hololens-faq-security)中找到裝置安全性的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="69b03-130">You can find more information on device security in the [HoloLens security FAQ](https://docs.microsoft.com/hololens/hololens-faq-security).</span></span>  

## <a name="device-support"></a><span data-ttu-id="69b03-131">裝置支援</span><span class="sxs-lookup"><span data-stu-id="69b03-131">Device support</span></span>
<table><span data-ttu-id="69b03-132">
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" /> </colgroup>
    </span><span class="sxs-lookup"><span data-stu-id="69b03-132">
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" /> </colgroup>
    </span></span><tr>
        <td><span data-ttu-id="69b03-133"><strong>功能</strong></span><span class="sxs-lookup"><span data-stu-id="69b03-133"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="69b03-134"><a href="https://docs.microsoft.com/hololens/hololens1-hardware"><strong>HoloLens (第 1 代)</strong></a></span><span class="sxs-lookup"><span data-stu-id="69b03-134"><a href="https://docs.microsoft.com/hololens/hololens1-hardware"><strong>HoloLens 1st Gen</strong></a></span></span></td>
        <td><span data-ttu-id="69b03-135"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></a></span><span class="sxs-lookup"><span data-stu-id="69b03-135"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="69b03-136">Head 追蹤攝影機</span><span class="sxs-lookup"><span data-stu-id="69b03-136">Head Tracking Cameras</span></span></td>
        <td><span data-ttu-id="69b03-137">✔️</span><span class="sxs-lookup"><span data-stu-id="69b03-137">✔️</span></span></td>
        <td><span data-ttu-id="69b03-138">✔️</span><span class="sxs-lookup"><span data-stu-id="69b03-138">✔️</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="69b03-139">IR 攝影機的深度 &</span><span class="sxs-lookup"><span data-stu-id="69b03-139">Depth & IR Camera</span></span></td>
        <td><span data-ttu-id="69b03-140">✔️</span><span class="sxs-lookup"><span data-stu-id="69b03-140">✔️</span></span></td>
        <td><span data-ttu-id="69b03-141">✔️</span><span class="sxs-lookup"><span data-stu-id="69b03-141">✔️</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="69b03-142">加速計</span><span class="sxs-lookup"><span data-stu-id="69b03-142">Accelerometer</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="69b03-143">✔️</span><span class="sxs-lookup"><span data-stu-id="69b03-143">✔️</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="69b03-144">迴轉儀</span><span class="sxs-lookup"><span data-stu-id="69b03-144">Gyroscope</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="69b03-145">✔️</span><span class="sxs-lookup"><span data-stu-id="69b03-145">✔️</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="69b03-146">磁力計</span><span class="sxs-lookup"><span data-stu-id="69b03-146">Magnetometer</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="69b03-147">✔️</span><span class="sxs-lookup"><span data-stu-id="69b03-147">✔️</span></span></td>
    </tr>
</table>

## <a name="enabling-research-mode-hololens-1st-gen-and-hololens-2"></a><span data-ttu-id="69b03-148">啟用 Research 模式 (HoloLens 1 Gen 和 HoloLens 2) </span><span class="sxs-lookup"><span data-stu-id="69b03-148">Enabling Research Mode (HoloLens 1st Gen and HoloLens 2)</span></span>

<span data-ttu-id="69b03-149">研究模式是開發人員模式的延伸模組。</span><span class="sxs-lookup"><span data-stu-id="69b03-149">Research Mode is an extension of Developer Mode.</span></span> <span data-ttu-id="69b03-150">開始之前，必須先啟用裝置的開發人員功能，才能存取研究模式設定：</span><span class="sxs-lookup"><span data-stu-id="69b03-150">Before starting, the developer features of the device need to be enabled to access the Research Mode settings:</span></span> 

* <span data-ttu-id="69b03-151">開啟 [ **開始] 功能表 > 設定** ]，然後選取 [ **更新** ]。</span><span class="sxs-lookup"><span data-stu-id="69b03-151">Open **Start Menu > Settings** and select **Updates** .</span></span>
* <span data-ttu-id="69b03-152">**針對開發人員** 選取並啟用 **開發人員模式** 。</span><span class="sxs-lookup"><span data-stu-id="69b03-152">Select **For Developers** and enable **Developer Mode** .</span></span>
* <span data-ttu-id="69b03-153">向下捲動並啟用 **裝置入口網站** 。</span><span class="sxs-lookup"><span data-stu-id="69b03-153">Scroll down and enable **Device Portal** .</span></span>

<span data-ttu-id="69b03-154">啟用開發人員功能之後，請連線 [到裝置入口網站](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-hololens) 以啟用研究模式功能：</span><span class="sxs-lookup"><span data-stu-id="69b03-154">After the developer features  are enabled, [connect to the device portal](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-hololens) to enable the Research Mode features:</span></span>

* <span data-ttu-id="69b03-155">移至 **裝置入口網站** 中的 **系統 > 研究模式** 。</span><span class="sxs-lookup"><span data-stu-id="69b03-155">Go to **System > Research Mode** in the **Device Portal** .</span></span>
* <span data-ttu-id="69b03-156">選取 [ **允許存取感應器串流** ]。</span><span class="sxs-lookup"><span data-stu-id="69b03-156">Select **Allow access to sensor stream** .</span></span>
* <span data-ttu-id="69b03-157">從頁面頂端的 [ **電源** ] 功能表項目目重新開機裝置。</span><span class="sxs-lookup"><span data-stu-id="69b03-157">Restart the device from the **Power** menu item at the top of the page.</span></span>

<span data-ttu-id="69b03-158">當您重新開機裝置之後，透過 **裝置入口網站** 載入的應用程式就可以存取研究模式串流。</span><span class="sxs-lookup"><span data-stu-id="69b03-158">Once you've restarted the device, the applications loaded through the **Device Portal** can access Research Mode streams.</span></span>

<span data-ttu-id="69b03-159">![HoloLens 裝置入口網站的 [研究模式] 索引標籤](images/ResearchModeDevPortal.png)</span><span class="sxs-lookup"><span data-stu-id="69b03-159">![Research Mode tab of HoloLens Device Portal](images/ResearchModeDevPortal.png)</span></span><br>
<span data-ttu-id="69b03-160">*HoloLens 裝置入口網站中的研究強制回應視窗*</span><span class="sxs-lookup"><span data-stu-id="69b03-160">*Research Mode window in the HoloLens Device Portal*</span></span>

> [!IMPORTANT]
> <span data-ttu-id="69b03-161">從組建19041.1356 開始提供 HoloLens 2 的研究模式。</span><span class="sxs-lookup"><span data-stu-id="69b03-161">Research Mode for HoloLens 2 is available beginning with build 19041.1356.</span></span> <span data-ttu-id="69b03-162">如果您需要在先前的組建中存取，請註冊我們的 [Insider preview](https://docs.microsoft.com/hololens/hololens-insider) 計畫。</span><span class="sxs-lookup"><span data-stu-id="69b03-162">If you need access in an earlier build, sign up for our [Insider Preview](https://docs.microsoft.com/hololens/hololens-insider) program.</span></span>

### <a name="using-sensor-data-in-your-apps"></a><span data-ttu-id="69b03-163">在您的應用程式中使用感應器資料</span><span class="sxs-lookup"><span data-stu-id="69b03-163">Using sensor data in your apps</span></span>

<span data-ttu-id="69b03-164">應用程式可存取感應器串流資料的方式，與透過 [媒體基礎](https://msdn.microsoft.com/library/windows/desktop/ms694197)存取相片和攝影機串流的方式相同。</span><span class="sxs-lookup"><span data-stu-id="69b03-164">Applications can access the sensor stream data in the same way that photo and video camera streams are accessed through [Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197).</span></span> 

<span data-ttu-id="69b03-165">所有適用于 HoloLens 開發的 Api 也都可在研究模式中取得。</span><span class="sxs-lookup"><span data-stu-id="69b03-165">All APIs that work for HoloLens development are also available in Research Mode.</span></span> <span data-ttu-id="69b03-166">尤其是，應用程式會準確知道 HoloLens 在每個感應器畫面格捕獲時間的6DoF 空間中。</span><span class="sxs-lookup"><span data-stu-id="69b03-166">In particular, the application  knows precisely where HoloLens is in 6DoF space at each sensor frame capture time.</span></span>

<span data-ttu-id="69b03-167">您可以使用內建 [和 extrinsics](https://docs.microsoft.com/windows/mixed-reality/locatable-camera#locating-the-device-camera-in-the-world)來尋找存取各種研究模式串流的範例應用程式，並在個別的研究模式存放庫中記錄資料流程：</span><span class="sxs-lookup"><span data-stu-id="69b03-167">You can find sample applications on accessing the various Research Mode streams, using the [intrinsics and extrinsics](https://docs.microsoft.com/windows/mixed-reality/locatable-camera#locating-the-device-camera-in-the-world), and recording streams in the respective Research Mode repos:</span></span>
* [<span data-ttu-id="69b03-168">HoloLens (第 1 代)</span><span class="sxs-lookup"><span data-stu-id="69b03-168">HoloLens (1st gen)</span></span>](https://github.com/Microsoft/HoloLensForCV)
* [<span data-ttu-id="69b03-169">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="69b03-169">HoloLens 2</span></span>](https://github.com/microsoft/HoloLens2ForCV)

## <a name="support"></a><span data-ttu-id="69b03-170">支援</span><span class="sxs-lookup"><span data-stu-id="69b03-170">Support</span></span>

<span data-ttu-id="69b03-171">針對 HoloLens (第1代) ，請使用 HoloLensForCV 存放庫中的 [問題追蹤](https://github.com/Microsoft/HololensForCV/issues) 程式張貼意見反應，並追蹤已知問題。</span><span class="sxs-lookup"><span data-stu-id="69b03-171">For HoloLens (1st gen), please use the [issue tracker](https://github.com/Microsoft/HololensForCV/issues) in the HoloLensForCV repository to post feedback and track known issues.</span></span>

<span data-ttu-id="69b03-172">針對 HoloLens 2，請使用 HoloLens2ForCV 存放庫中的 [問題追蹤](https://github.com/microsoft/HoloLens2ForCV/issues) 程式張貼意見反應，並追蹤已知問題。</span><span class="sxs-lookup"><span data-stu-id="69b03-172">For HoloLens 2, please use the [issue tracker](https://github.com/microsoft/HoloLens2ForCV/issues) in the HoloLens2ForCV repository to post feedback and track known issues.</span></span>

## <a name="see-also"></a><span data-ttu-id="69b03-173">另請參閱</span><span class="sxs-lookup"><span data-stu-id="69b03-173">See also</span></span>

* [<span data-ttu-id="69b03-174">Microsoft 媒體基礎</span><span class="sxs-lookup"><span data-stu-id="69b03-174">Microsoft Media Foundation</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms694197)
* [<span data-ttu-id="69b03-175">HoloLensForCV GitHub 存放庫</span><span class="sxs-lookup"><span data-stu-id="69b03-175">HoloLensForCV GitHub repo</span></span>](https://github.com/Microsoft/HoloLensForCV)
* [<span data-ttu-id="69b03-176">HoloLens2ForCV GitHub 存放庫</span><span class="sxs-lookup"><span data-stu-id="69b03-176">HoloLens2ForCV GitHub repo</span></span>](https://github.com/microsoft/HoloLens2ForCV)
* [<span data-ttu-id="69b03-177">使用 Windows 裝置入口網站</span><span class="sxs-lookup"><span data-stu-id="69b03-177">Using the Windows Device Portal</span></span>](using-the-windows-device-portal.md)
