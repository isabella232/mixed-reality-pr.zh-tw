---
title: Mixed Reality OpenXR 外掛程式版本資訊
description: 隨時掌握最新的版本資訊，並升級至 Mixed Reality OpenXR 外掛程式。
author: hferrone
ms.author: v-hferrone
ms.date: 06/18/2021
ms.topic: article
ms.localizationpriority: high
keywords: 最新狀態, 開始使用, 基本概念, unity, visual studio, 工具組, 混合實境頭戴式裝置, windows 混合實境頭戴式裝置, 虛擬實境頭戴式裝置, 安裝, Windows, HoloLens, 模擬器, unreal, openxr
ms.openlocfilehash: c926fbb758d7cfaa2e73b5357cacdab7a5d15e27
ms.sourcegitcommit: 6ade7e8ebab7003fc24f9e0b5fa81d091369622c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2021
ms.locfileid: "112394646"
---
# <a name="mixed-reality-openxr-plugin-release-notes"></a><span data-ttu-id="1f491-104">Mixed Reality OpenXR 外掛程式版本資訊</span><span class="sxs-lookup"><span data-stu-id="1f491-104">Mixed Reality OpenXR plugin release notes</span></span>

## <a name="100---current-release"></a><span data-ttu-id="1f491-105">1.0.0-目前版本</span><span class="sxs-lookup"><span data-stu-id="1f491-105">1.0.0 - Current release</span></span>

* <span data-ttu-id="1f491-106">修正了 XRAnchorSubsystem 一律在應用程式啟動時啟動的錯誤（bug），不論 ARAnchorManager 是否存在。</span><span class="sxs-lookup"><span data-stu-id="1f491-106">Fixed a bug where a the XRAnchorSubsystem was always started on app start regardless ARAnchorManager’s present.</span></span>
* <span data-ttu-id="1f491-107">修正 reprojection 模式無法正常運作的 bug。</span><span class="sxs-lookup"><span data-stu-id="1f491-107">Fixed a bug where the reprojection mode didn’t work properly.</span></span>

## <a name="100-preview2---2021-06-14"></a><span data-ttu-id="1f491-108">1.0.0-preview。 2-2021-06-14</span><span class="sxs-lookup"><span data-stu-id="1f491-108">1.0.0-preview.2 - 2021-06-14</span></span>

* <span data-ttu-id="1f491-109">相依于 Unity 的 1.2.2 OpenXR 外掛程式。</span><span class="sxs-lookup"><span data-stu-id="1f491-109">Depends on Unity’s 1.2.2 OpenXR plugin.</span></span>
* <span data-ttu-id="1f491-110">已將中的全像遠端功能變更為個別的功能群組。</span><span class="sxs-lookup"><span data-stu-id="1f491-110">Changed Holographic Remoting features in to individual feature groups.</span></span>
* <span data-ttu-id="1f491-111">修正 [套用 HoloLens 2 專案設定] 變更專案色彩空間的錯誤。</span><span class="sxs-lookup"><span data-stu-id="1f491-111">Fixed a bug where “Apply HoloLens 2 project settings” changes project color space.</span></span> <span data-ttu-id="1f491-112">Unity OpenXR 1.2.0 外掛程式之後不再需要此功能。</span><span class="sxs-lookup"><span data-stu-id="1f491-112">This is no longer needed after Unity OpenXR 1.2.0 plugin.</span></span>
* <span data-ttu-id="1f491-113">修正了在應用程式暫停和繼續之後，輸入裝置連線而沒有中斷連線的 bug。</span><span class="sxs-lookup"><span data-stu-id="1f491-113">Fixed a bug where a input device get connected without disconnect after application suspended and resumed.</span></span>
* <span data-ttu-id="1f491-114">已新增透過 ARSession 偵測外掛程式和目前追蹤狀態的支援。</span><span class="sxs-lookup"><span data-stu-id="1f491-114">Added support for detecting plugin and current tracking states via ARSession.</span></span>
* <span data-ttu-id="1f491-115">修正了 [AR Default 平面] ARFoundation 預製專案不會顯示的錯誤。</span><span class="sxs-lookup"><span data-stu-id="1f491-115">Fixed a bug where the “AR Default Plane” ARFoundation prefab wouldn’t be visible.</span></span>

## <a name="100-preview1---2021-06-02"></a><span data-ttu-id="1f491-116">1.0.0-preview。 1-2021-06-02</span><span class="sxs-lookup"><span data-stu-id="1f491-116">1.0.0-preview.1 - 2021-06-02</span></span>

* <span data-ttu-id="1f491-117">支援 OpenXR 場景理解 MSFT 擴充功能，而不是預覽延伸模組。</span><span class="sxs-lookup"><span data-stu-id="1f491-117">Supports OpenXR scene understanding MSFT extensions instead of preview extensions.</span></span>
* <span data-ttu-id="1f491-118">HoloLens 2 的平面偵測不再需要預覽版本的混合現實 OpenXR 執行時間。</span><span class="sxs-lookup"><span data-stu-id="1f491-118">Plane detection on HoloLens 2 no longer requires preview versions of the Mixed Reality OpenXR runtimes.</span></span>

## <a name="095---2021-05-21"></a><span data-ttu-id="1f491-119">0.9.5-2021-05-21</span><span class="sxs-lookup"><span data-stu-id="1f491-119">0.9.5 - 2021-05-21</span></span>

* <span data-ttu-id="1f491-120">相依于 Unity 的 1.2.0 OpenXR 外掛程式</span><span class="sxs-lookup"><span data-stu-id="1f491-120">Depends on Unity’s 1.2.0 OpenXR Plugin</span></span>
* <span data-ttu-id="1f491-121">適用于 OpenXR 外掛程式 1.2.0) 中的新功能 UI (，以進行設定。</span><span class="sxs-lookup"><span data-stu-id="1f491-121">Adapted to the new feature UI (in OpenXR Plugin 1.2.0) for configuration.</span></span>
* <span data-ttu-id="1f491-122">已修正找不到已定位相機提供者未正確取消註冊的 bug。</span><span class="sxs-lookup"><span data-stu-id="1f491-122">Fixed a bug where the locatable camera provider wasn’t properly unregistering.</span></span>
* <span data-ttu-id="1f491-123">清除 [Preserve] 的一些額外用法。</span><span class="sxs-lookup"><span data-stu-id="1f491-123">Cleaned up some extra usages of [Preserve].</span></span>
* <span data-ttu-id="1f491-124">更新輸入系統 UI 中的「HP 回音 G2 控制器 (OpenXR) 」名稱。</span><span class="sxs-lookup"><span data-stu-id="1f491-124">Update “HP Reverb G2 Controller (OpenXR)” name in the input system UI.</span></span>

## <a name="094---2021-05-20"></a><span data-ttu-id="1f491-125">0.9.4-2021-05-20</span><span class="sxs-lookup"><span data-stu-id="1f491-125">0.9.4 - 2021-05-20</span></span>

* <span data-ttu-id="1f491-126">相依于 Unity 的 1.2.0 OpenXR 外掛程式。</span><span class="sxs-lookup"><span data-stu-id="1f491-126">Depends on Unity’s 1.2.0 OpenXR Plugin.</span></span>
* <span data-ttu-id="1f491-127">已新增新的 c # API 來取得運動控制器 glTF 模型。</span><span class="sxs-lookup"><span data-stu-id="1f491-127">Added new C# API to get motion controller glTF model.</span></span>
* <span data-ttu-id="1f491-128">已新增新的 c # API，以取得啟用的視圖設定和設定 reprojection 設定。</span><span class="sxs-lookup"><span data-stu-id="1f491-128">Added new C# API to get enabled view configurations and set reprojection settings.</span></span>
* <span data-ttu-id="1f491-129">已新增新的 c # API，以使用 XRMeshSubsystem 來設定計算網格的其他設定。</span><span class="sxs-lookup"><span data-stu-id="1f491-129">Added new C# API to set additional settings for computing meshes with XRMeshSubsystem.</span></span>
* <span data-ttu-id="1f491-130">已新增新的 c # API 來設定和訂閱手勢辨識事件。</span><span class="sxs-lookup"><span data-stu-id="1f491-130">Added new C# API to configure and subscribe to gesture recognition events.</span></span>
* <span data-ttu-id="1f491-131">已新增 Windows->XR->編輯器遠端設定] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="1f491-131">Added Windows->XR->Editor Remoting settings dialog.</span></span>
* <span data-ttu-id="1f491-132">已新增適用于 HoloLens UWP 應用程式的 ARM 支援。</span><span class="sxs-lookup"><span data-stu-id="1f491-132">Added ARM support for HoloLens UWP applications.</span></span>

## <a name="093---2021-04-29"></a><span data-ttu-id="1f491-133">0.9.3-2021-04-29</span><span class="sxs-lookup"><span data-stu-id="1f491-133">0.9.3 - 2021-04-29</span></span>

* <span data-ttu-id="1f491-134">修正了全息型遠端連線不可靠的 bug</span><span class="sxs-lookup"><span data-stu-id="1f491-134">Fixed a bug where Holographic remoting connection is not reliable</span></span>
* <span data-ttu-id="1f491-135">修正了在升級至 Unity 的 1.1.1 OpenXR 外掛程式之後，VR 轉譯效能是次最佳的錯誤。</span><span class="sxs-lookup"><span data-stu-id="1f491-135">Fixed a bug where the VR rendering performance is sub-optimum after upgrade to Unity’s 1.1.1 OpenXR plugin.</span></span>

## <a name="092---2021-04-21"></a><span data-ttu-id="1f491-136">0.9.2-2021-04-21</span><span class="sxs-lookup"><span data-stu-id="1f491-136">0.9.2 - 2021-04-21</span></span>

* <span data-ttu-id="1f491-137">外掛程式版本0.9.1 中 HoloLens 2 的平面偵測將可搭配105版的 Mixed Reality OpenXR preview 執行時間使用。</span><span class="sxs-lookup"><span data-stu-id="1f491-137">Plane detection on HoloLens 2 in plugin version 0.9.1 will work with version 105 of the Mixed Reality OpenXR preview runtime.</span></span>
* <span data-ttu-id="1f491-138">外掛程式版本0.9.2 中 HoloLens 2 的平面偵測將可搭配106版的 Mixed Reality OpenXR preview 執行時間使用。</span><span class="sxs-lookup"><span data-stu-id="1f491-138">Plane detection on HoloLens 2 in plugin version 0.9.2 will work with version 106 of the Mixed Reality OpenXR preview runtime.</span></span>
* <span data-ttu-id="1f491-139">已從 InputProvider 中移除一些未使用的回呼，以防止像 XRInputSubsystem. \* GetTrackingOriginMode (不是由我們的輸入系統管理，) 無法傳回具有誤導值的成功。</span><span class="sxs-lookup"><span data-stu-id="1f491-139">Removed some unused callbacks from InputProvider to prevent calls like XRInputSubsystem.\* GetTrackingOriginMode (which aren’t managed by our input system) from returning success with misleading values.</span></span>
* <span data-ttu-id="1f491-140">將已淘汰的 XRAnchorStore 版本分割成自己的檔案，以防止 Unity 主控台出現警告。</span><span class="sxs-lookup"><span data-stu-id="1f491-140">Split out deprecated version of XRAnchorStore into its own file to prevent Unity console warning.</span></span>

## <a name="091---2021-04-20"></a><span data-ttu-id="1f491-141">0.9.1-2021-04-20</span><span class="sxs-lookup"><span data-stu-id="1f491-141">0.9.1 - 2021-04-20</span></span>

* <span data-ttu-id="1f491-142">相依于 Unity 的 1.1.1 OpenXR 外掛程式。</span><span class="sxs-lookup"><span data-stu-id="1f491-142">Depends on Unity’s 1.1.1 OpenXR Plugin.</span></span>
* <span data-ttu-id="1f491-143">新增 UWP 平臺的全像遠端應用程式支援。</span><span class="sxs-lookup"><span data-stu-id="1f491-143">Added support for Holographic Remoting application for UWP platform.</span></span>
* <span data-ttu-id="1f491-144">修正 XRAnchorStore 嘗試在主要執行緒外部取得設定實例的 UnityException。</span><span class="sxs-lookup"><span data-stu-id="1f491-144">Fix UnityException where XRAnchorStore was trying to get a settings instance outside the main thread.</span></span>

## <a name="090---2021-03-29"></a><span data-ttu-id="1f491-145">0.9.0-2021-03-29</span><span class="sxs-lookup"><span data-stu-id="1f491-145">0.9.0 - 2021-03-29</span></span>

* <span data-ttu-id="1f491-146">已新增透過 XRMeshSubsystem 和 ARMeshManager 的空間對應支援。</span><span class="sxs-lookup"><span data-stu-id="1f491-146">Added support for spatial mapping via XRMeshSubsystem and ARMeshManager.</span></span>
* <span data-ttu-id="1f491-147">已新增新的 c # API 來取得 OpenXR 控制碼，以支援其他 Unity 套件使用 OpenXR 擴充功能。</span><span class="sxs-lookup"><span data-stu-id="1f491-147">Added new C# API to get OpenXR handles to support other Unity packages consumes OpenXR extensions.</span></span>
* <span data-ttu-id="1f491-148">已新增新的 c # API 與 Windows 的互通性。認知 Api 可支援使用認知 WinRT Api 的其他 Unity 套件。</span><span class="sxs-lookup"><span data-stu-id="1f491-148">Added new C# API to interop with Windows.Perception APIs to support other Unity packages consuming Perception WinRT APIs.</span></span>
* <span data-ttu-id="1f491-149">從 Windows Mixed Reality 功能集中的必要功能移除互動設定檔，讓開發人員可以選擇所測試的動作控制器。</span><span class="sxs-lookup"><span data-stu-id="1f491-149">Removed interaction profiles from required features in Windows Mixed Reality feature set, so developers can choose the motion controllers they tested with.</span></span>
* <span data-ttu-id="1f491-150">已新增全像「編輯遠端功能」驗證程式，可協助使用者正確設定編輯器的遠端功能。</span><span class="sxs-lookup"><span data-stu-id="1f491-150">Added Holographic editor remoting feature validator to help users to setup editor remoting properly.</span></span>
* <span data-ttu-id="1f491-151">修正當連線失敗後，Unity 編輯器在離開全像 editor 遠端處理模式時損毀的 bug。</span><span class="sxs-lookup"><span data-stu-id="1f491-151">Fixed a bug where Unity editor crashes when exiting Holographic editor remoting mode after connection failure.</span></span>
* <span data-ttu-id="1f491-152">修正了 unpremultipled Alpha 紋理在 HoloLens 2 上導致次效能的 bug。</span><span class="sxs-lookup"><span data-stu-id="1f491-152">Fixed a bug where unpremultipled alpha textures leads to sub-optimum performance on HoloLens 2.</span></span>
* <span data-ttu-id="1f491-153">修正了當場景原點位於地面層級時，無法正確找出手追蹤的錯誤。</span><span class="sxs-lookup"><span data-stu-id="1f491-153">Fixed a bug where hand tracking was not located correctly when the scene origin was at floor level.</span></span>
* <span data-ttu-id="1f491-154">修正了在離開和載入新場景後，會消失的手上網格追蹤的錯誤。</span><span class="sxs-lookup"><span data-stu-id="1f491-154">Fixed a bug where hand mesh tracking disappear after leaving and loading a new scene.</span></span>
* <span data-ttu-id="1f491-155">修正了可定位的相機提供者未正確清除的 bug。</span><span class="sxs-lookup"><span data-stu-id="1f491-155">Fixed a bug where locatable camera provider didn’t properly clean up.</span></span>
* <span data-ttu-id="1f491-156">已將 XRAnchorStore API 的命名空間修改為 MixedReality. OpenXR。</span><span class="sxs-lookup"><span data-stu-id="1f491-156">Revised the namespace of XRAnchorStore API into Microsoft.MixedReality.OpenXR.</span></span>