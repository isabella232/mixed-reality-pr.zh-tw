---
title: 在 Unreal 中升級專案
description: Unreal 專案中版本升級步驟和已淘汰 API 的概觀。
author: hferrone
ms.author: jacksonf
ms.date: 11/23/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 混合實境, 開發, 文件, 指南, 功能, 混合實境頭戴式裝置, windows 混合實境頭戴式裝置, 虛擬實境頭戴式裝置, 移植, 升級
ms.openlocfilehash: 0ba10b8ee1067da4494f147d43f8834010e1250f
ms.sourcegitcommit: 32cb81eee976e73cd661c2b347691c37865a60bc
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/04/2020
ms.locfileid: "96609659"
---
# <a name="upgrading-projects-in-unreal"></a><span data-ttu-id="1372f-104">在 Unreal 中升級專案</span><span class="sxs-lookup"><span data-stu-id="1372f-104">Upgrading projects in Unreal</span></span>

<span data-ttu-id="1372f-105">更新至新版本的 Unreal 時，已淘汰的函式會在編譯藍圖或封裝專案時顯示為警告。</span><span class="sxs-lookup"><span data-stu-id="1372f-105">When updating to a new version of Unreal, deprecated functions show up as warnings when compiling blueprints or packaging the project.</span></span>  <span data-ttu-id="1372f-106">新增了應改用的新函式時，舊函式就會淘汰。</span><span class="sxs-lookup"><span data-stu-id="1372f-106">Functions are deprecated when a new function has been added that should be used instead.</span></span> 

## <a name="426-upgrades"></a><span data-ttu-id="1372f-107">4.26 升級</span><span class="sxs-lookup"><span data-stu-id="1372f-107">4.26 upgrades</span></span>
 
<span data-ttu-id="1372f-108">在 4.26 中，所有 AR 和 VR 平台都已重構，以新增通用介面，並讓應用程式的程式碼平台不受限制，因此您可能會看到比平常更多的警告。</span><span class="sxs-lookup"><span data-stu-id="1372f-108">In 4.26, all AR and VR platforms have been refactored to add common interfaces and keep application code platform agnostic, so you may see more warnings than usual.</span></span>  <span data-ttu-id="1372f-109">建議您更新為新的 API，以讓專案更容易移植到其他平台。</span><span class="sxs-lookup"><span data-stu-id="1372f-109">Updating to the new APIs is recommended so the project can be more easily ported to other platforms.</span></span>

<span data-ttu-id="1372f-110">警告訊息會顯示哪個函式已淘汰，並指出要改用哪個函式。</span><span class="sxs-lookup"><span data-stu-id="1372f-110">Warning messages will show which function has been deprecated and indicate what function to use instead.</span></span>  <span data-ttu-id="1372f-111">所有已淘汰的函式在此版本中仍可繼續運作，但在未來的版本中可能就無法運作。</span><span class="sxs-lookup"><span data-stu-id="1372f-111">All deprecated functions will continue to work for this release but may not work in future releases.</span></span>  <span data-ttu-id="1372f-112">在藍圖中搜尋函式時，也不會再列出已淘汰的函式。</span><span class="sxs-lookup"><span data-stu-id="1372f-112">Deprecated functions will also no longer be listed when searching for functions in a blueprint.</span></span>

![建立具名 ARPin 函式的藍圖](images/unreal-porting-img-01.png)

### <a name="425-deprecations"></a><span data-ttu-id="1372f-114">4.25 淘汰</span><span class="sxs-lookup"><span data-stu-id="1372f-114">4.25 deprecations</span></span>

| <span data-ttu-id="1372f-115">已淘汰的函式</span><span class="sxs-lookup"><span data-stu-id="1372f-115">Deprecated function</span></span> | <span data-ttu-id="1372f-116">新增函式</span><span class="sxs-lookup"><span data-stu-id="1372f-116">New function</span></span> |
| --- | --- |
| <span data-ttu-id="1372f-117">CreateNamedARPin</span><span class="sxs-lookup"><span data-stu-id="1372f-117">CreateNamedARPin</span></span> | ![「釘選元件」函式的藍圖](images/unreal-porting-img-02.png) |
| <span data-ttu-id="1372f-119">LoadWMRAnchorStoreARPins</span><span class="sxs-lookup"><span data-stu-id="1372f-119">LoadWMRAnchorStoreARPins</span></span> | ![「從本機存放區載入 ARPins」函式的藍圖](images/unreal-porting-img-03.png) |
| <span data-ttu-id="1372f-121">LoadWMRAnchorSaveARPinToWMRAnchorStoreStoreARPins</span><span class="sxs-lookup"><span data-stu-id="1372f-121">LoadWMRAnchorSaveARPinToWMRAnchorStoreStoreARPins</span></span> | ![「將 ARPin 儲存至本機存放區」函式的藍圖](images/unreal-porting-img-04.png) |
| <span data-ttu-id="1372f-123">RemoveARPinFromWMRAnchorStore</span><span class="sxs-lookup"><span data-stu-id="1372f-123">RemoveARPinFromWMRAnchorStore</span></span> | ![「從本機存放區移除 ARPin」函式的藍圖](images/unreal-porting-img-05.png) |
| <span data-ttu-id="1372f-125">SetEnabledMixedRealityCamera</span><span class="sxs-lookup"><span data-stu-id="1372f-125">SetEnabledMixedRealityCamera</span></span> | ![「設定已啟用的 XRCamera」函式的藍圖](images/unreal-porting-img-06.png) |
| <span data-ttu-id="1372f-127">ResizeMixedRealityCamera</span><span class="sxs-lookup"><span data-stu-id="1372f-127">ResizeMixedRealityCamera</span></span> | ![「調整 XRCamera 大小」函式的藍圖](images/unreal-porting-img-07.png) |
| <span data-ttu-id="1372f-129">StartCameraCapture</span><span class="sxs-lookup"><span data-stu-id="1372f-129">StartCameraCapture</span></span> | ![用於啟動相機擷取的「切換 ARCapture」函式藍圖](images/unreal-porting-img-08.png) |
| <span data-ttu-id="1372f-131">StopCameraCapture</span><span class="sxs-lookup"><span data-stu-id="1372f-131">StopCameraCapture</span></span> | ![用於停止相機擷取的「切換 ARCapture」函式藍圖](images/unreal-porting-img-09.png) |
| <span data-ttu-id="1372f-133">StartQRCodeCapture</span><span class="sxs-lookup"><span data-stu-id="1372f-133">StartQRCodeCapture</span></span> | ![用於啟動 QR 代碼擷取的「切換 ARCapture」函式藍圖](images/unreal-porting-img-10.png) |
| <span data-ttu-id="1372f-135">StopQRCodeCapture</span><span class="sxs-lookup"><span data-stu-id="1372f-135">StopQRCodeCapture</span></span> | ![用於停止 QR 代碼擷取的「切換 ARCapture」函式藍圖](images/unreal-porting-img-11.png) |
| <span data-ttu-id="1372f-137">以前在 4.25 中，空間對應會自動啟動，但現在在 4.26 中，則必須進行切換。</span><span class="sxs-lookup"><span data-stu-id="1372f-137">Spatial mapping previously automatically started in 4.25, but now needs to be toggled in 4.26.</span></span> | ![用於啟用空間對應的「切換 ARCapture」函式藍圖](images/unreal-porting-img-12.png) |
| <span data-ttu-id="1372f-139">ShowKeyboard</span><span class="sxs-lookup"><span data-stu-id="1372f-139">ShowKeyboard</span></span> | <span data-ttu-id="1372f-140">已在 4.26 中移除，因為當焦點放在文字小工具時，會自動顯示鍵盤。</span><span class="sxs-lookup"><span data-stu-id="1372f-140">Removed in 4.26 since the keyboard automatically shows when a text widget is focused on.</span></span> |
| <span data-ttu-id="1372f-141">HideKeyboard</span><span class="sxs-lookup"><span data-stu-id="1372f-141">HideKeyboard</span></span> | <span data-ttu-id="1372f-142">已在 4.26 中移除，因為當焦點不在文字小工具時，會自動隱藏鍵盤。</span><span class="sxs-lookup"><span data-stu-id="1372f-142">Removed in 4.26 since the keyboard will automatically hide when a text widget is unfocused.</span></span> |
| <span data-ttu-id="1372f-143">SupportsHandTracking</span><span class="sxs-lookup"><span data-stu-id="1372f-143">SupportsHandTracking</span></span> | ![「支援手部追蹤」屬性的藍圖](images/unreal-porting-img-13.png) |
| <span data-ttu-id="1372f-145">IsDisplayOpaque</span><span class="sxs-lookup"><span data-stu-id="1372f-145">IsDisplayOpaque</span></span> | ![IsDisplayOpaque 屬性的藍圖](images/unreal-porting-img-14.png) |
| <span data-ttu-id="1372f-147">GetHandJointTransform、GetPointerPoseInfo、GetControllerTrackingStatus</span><span class="sxs-lookup"><span data-stu-id="1372f-147">GetHandJointTransform, GetPointerPoseInfo, GetControllerTrackingStatus</span></span> | ![「取得運動控制器資料」函式的藍圖](images/unreal-porting-img-15.png) |
| <span data-ttu-id="1372f-149">GetVersionString</span><span class="sxs-lookup"><span data-stu-id="1372f-149">GetVersionString</span></span> | ![「取得版本字串」函式的藍圖](images/unreal-porting-img-16.png) |
| <span data-ttu-id="1372f-151">IsTrackingAvailable</span><span class="sxs-lookup"><span data-stu-id="1372f-151">IsTrackingAvailable</span></span> | ![IsTrackingAvailable 屬性的藍圖](images/unreal-porting-img-17.png) |
| <span data-ttu-id="1372f-153">IsButtonClicked、IsButtonDown、IsGrasped、IsSelectPressed</span><span class="sxs-lookup"><span data-stu-id="1372f-153">IsButtonClicked, IsButtonDown, IsGrasped, IsSelectPressed</span></span> | <span data-ttu-id="1372f-154">使用 Unreal 的輸入動作系統。</span><span class="sxs-lookup"><span data-stu-id="1372f-154">Use Unreal’s input action system.</span></span> |
| <span data-ttu-id="1372f-155">SetFocusPointForFrame</span><span class="sxs-lookup"><span data-stu-id="1372f-155">SetFocusPointForFrame</span></span> | <span data-ttu-id="1372f-156">已在 4.26 中移除。</span><span class="sxs-lookup"><span data-stu-id="1372f-156">Removed in 4.26.</span></span>  <span data-ttu-id="1372f-157">過去用於遠端處理時的重新投影，現在則支援深度重新投影。</span><span class="sxs-lookup"><span data-stu-id="1372f-157">Previously used for reprojection when remoting, which now supports depth reprojection.</span></span> |