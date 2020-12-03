---
title: Unreal 中的 HoloLens 相片/影片相機
description: 在 Unreal 中使用 HoloLens 相片/影片相機的指南
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 混合實境, 開發, 功能, 文件, 指南, 全像投影, 相機, PV 相機, MRC, 混合實境頭戴式裝置, windows 混合實境頭戴式裝置, 虛擬實境頭戴式裝置
ms.openlocfilehash: ef557bc6492ced6bb9b3c47a8cccc897e33b76c1
ms.sourcegitcommit: 09522ab15a9008ca4d022f9e37fcc98f6eaf6093
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/30/2020
ms.locfileid: "96354583"
---
# <a name="hololens-photovideo-camera-in-unreal"></a><span data-ttu-id="d6a66-104">Unreal 中的 HoloLens 相片/影片相機</span><span class="sxs-lookup"><span data-stu-id="d6a66-104">HoloLens Photo/Video Camera in Unreal</span></span>

<span data-ttu-id="d6a66-105">HoloLens 的面板上有相片/影片 (PV) 相機，不僅可用於混合實境擷取 (MRC)，也可供應用程式用來透過相機框架中的像素座標定位 Unreal 世界空間中的物件。</span><span class="sxs-lookup"><span data-stu-id="d6a66-105">The HoloLens has a Photo/Video (PV) Camera on the visor that can be used for both Mixed Reality Capture (MRC) and by an app to locate objects in Unreal world space from pixel coordinates in the camera frame.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d6a66-106">PV 攝影機不支援全像攝影遠端功能，但可以使用連接到您電腦的網路攝影機來模擬 HoloLens PV 攝影機功能。</span><span class="sxs-lookup"><span data-stu-id="d6a66-106">The PV Camera isn't supported with Holographic Remoting, but it's possible to use a webcam attached to your PC to simulate the HoloLens PV Camera functionality.</span></span>

[!INCLUDE[](includes/tabs-pv-camera.md)]

## <a name="next-development-checkpoint"></a><span data-ttu-id="d6a66-107">下一個開發檢查點</span><span class="sxs-lookup"><span data-stu-id="d6a66-107">Next Development Checkpoint</span></span>

<span data-ttu-id="d6a66-108">依循我們配置的 Unreal 開發檢查點旅程，此時您會探索混合實境平台功能和 API。</span><span class="sxs-lookup"><span data-stu-id="d6a66-108">If you're following the Unreal development checkpoint journey we've laid out, you're in the midst of exploring the Mixed Reality platform capabilities and APIs.</span></span> <span data-ttu-id="d6a66-109">接下來，您可以繼續進行下一個主題：</span><span class="sxs-lookup"><span data-stu-id="d6a66-109">From here, you can proceed to the next topic:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="d6a66-110">QR 代碼</span><span class="sxs-lookup"><span data-stu-id="d6a66-110">QR codes</span></span>](unreal-qr-codes.md)

<span data-ttu-id="d6a66-111">或者，直接跳到在裝置或模擬器上部署應用程式的主題：</span><span class="sxs-lookup"><span data-stu-id="d6a66-111">Or jump directly to deploying your app on a device or emulator:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="d6a66-112">部署至裝置</span><span class="sxs-lookup"><span data-stu-id="d6a66-112">Deploying to device</span></span>](unreal-deploying.md)

<span data-ttu-id="d6a66-113">您可以隨時回到 [Unreal 開發檢查點](unreal-development-overview.md#3-platform-capabilities-and-apis)。</span><span class="sxs-lookup"><span data-stu-id="d6a66-113">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#3-platform-capabilities-and-apis) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="d6a66-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d6a66-114">See also</span></span>
* [<span data-ttu-id="d6a66-115">定位相機</span><span class="sxs-lookup"><span data-stu-id="d6a66-115">Locatable camera</span></span>](../platform-capabilities-and-apis/locatable-camera.md)
* [<span data-ttu-id="d6a66-116">適用於開發人員的混合實境擷取</span><span class="sxs-lookup"><span data-stu-id="d6a66-116">Mixed reality capture for developers</span></span>](../platform-capabilities-and-apis/mixed-reality-capture-for-developers.md)
