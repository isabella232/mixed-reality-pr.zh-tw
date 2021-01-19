---
title: Unreal 中的 HoloLens 相片/影片相機
description: 了解如何在 Unreal 中使用 HoloLens 相機和攝影機來進行混合實境擷取和物件定位。
author: hferrone
ms.author: jacksonf
ms.date: 12/9/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 混合實境, 開發, 功能, 文件, 指南, 全像投影, 相機, PV 相機, MRC, 混合實境頭戴式裝置, windows 混合實境頭戴式裝置, 虛擬實境頭戴式裝置
ms.openlocfilehash: 6f1301e0daeb44521dfb4e93a915d49d9aea8443
ms.sourcegitcommit: e24715fffa815c24ca411fa93eed9576ae729337
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/16/2021
ms.locfileid: "98247761"
---
# <a name="hololens-photovideo-camera-in-unreal"></a><span data-ttu-id="345f3-104">Unreal 中的 HoloLens 相片/影片相機</span><span class="sxs-lookup"><span data-stu-id="345f3-104">HoloLens Photo/Video Camera in Unreal</span></span>

<span data-ttu-id="345f3-105">HoloLens 的面板上有相片/影片 (PV) 相機，不僅可用於混合實境擷取 (MRC)，也可用來透過相機框架中的像素座標定位 Unreal 世界空間中的物件。</span><span class="sxs-lookup"><span data-stu-id="345f3-105">The HoloLens has a Photo/Video (PV) Camera on the visor that can be used for both Mixed Reality Capture (MRC) and locating objects in Unreal world space from pixel coordinates in the camera frame.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="345f3-106">PV 攝影機不支援全像攝影遠端功能，但可以使用連接到您電腦的網路攝影機來模擬 HoloLens PV 攝影機功能。</span><span class="sxs-lookup"><span data-stu-id="345f3-106">The PV Camera isn't supported with Holographic Remoting, but it's possible to use a webcam attached to your PC to simulate the HoloLens PV Camera functionality.</span></span>

[!INCLUDE[](includes/tabs-pv-camera.md)]

## <a name="next-development-checkpoint"></a><span data-ttu-id="345f3-107">下一個開發檢查點</span><span class="sxs-lookup"><span data-stu-id="345f3-107">Next Development Checkpoint</span></span>

<span data-ttu-id="345f3-108">依循我們配置的 Unreal 開發旅程，此時您會探索混合實境平台功能和 API。</span><span class="sxs-lookup"><span data-stu-id="345f3-108">If you're following the Unreal development journey we've laid out, you're in the midst of exploring the Mixed Reality platform capabilities and APIs.</span></span> <span data-ttu-id="345f3-109">接下來，您可以繼續進行下一個主題：</span><span class="sxs-lookup"><span data-stu-id="345f3-109">From here, you can continue to the next topic:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="345f3-110">QR 代碼</span><span class="sxs-lookup"><span data-stu-id="345f3-110">QR codes</span></span>](unreal-qr-codes.md)

<span data-ttu-id="345f3-111">或者，直接跳到在裝置或模擬器上部署應用程式的主題：</span><span class="sxs-lookup"><span data-stu-id="345f3-111">Or jump directly to deploying your app on a device or emulator:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="345f3-112">部署至裝置</span><span class="sxs-lookup"><span data-stu-id="345f3-112">Deploying to device</span></span>](unreal-deploying.md)

<span data-ttu-id="345f3-113">您可以隨時回到 [Unreal 開發檢查點](unreal-development-overview.md#3-advanced-features)。</span><span class="sxs-lookup"><span data-stu-id="345f3-113">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#3-advanced-features) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="345f3-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="345f3-114">See also</span></span>

* [<span data-ttu-id="345f3-115">定位相機</span><span class="sxs-lookup"><span data-stu-id="345f3-115">Locatable camera</span></span>](../platform-capabilities-and-apis/locatable-camera.md)
* [<span data-ttu-id="345f3-116">適用於開發人員的混合實境擷取</span><span class="sxs-lookup"><span data-stu-id="345f3-116">Mixed reality capture for developers</span></span>](../platform-capabilities-and-apis/mixed-reality-capture-for-developers.md)
