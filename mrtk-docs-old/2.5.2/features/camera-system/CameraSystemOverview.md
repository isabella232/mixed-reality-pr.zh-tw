---
title: CameraSystemOverview
description: MRTK 中相機系統的登陸頁面
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、攝影機、
ms.openlocfilehash: d2c5a0a806d3f6fd6844eca716ca70ec233d1146
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104702214"
---
# <a name="camera-system"></a><span data-ttu-id="78fcc-104">攝影機系統</span><span class="sxs-lookup"><span data-stu-id="78fcc-104">Camera system</span></span>

<span data-ttu-id="78fcc-105">攝影機系統可讓 Microsoft Mixed Reality 工具組設定和優化應用程式的攝影機，以用於混合現實應用程式。</span><span class="sxs-lookup"><span data-stu-id="78fcc-105">The camera system enables the Microsoft Mixed Reality Toolkit to configure and optimize the application's camera for use in mixed reality applications.</span></span> <span data-ttu-id="78fcc-106">您可以使用相機系統來撰寫應用程式，以支援不透明的 (例如：虛擬實境) 和透明的 (例如： Microsoft HoloLens) 裝置，而不需要撰寫程式碼來區分和容納各種類型的顯示。</span><span class="sxs-lookup"><span data-stu-id="78fcc-106">Using the camera system, applications can be written to support both opaque (ex: virtual reality) and transparent (ex: Microsoft HoloLens) devices without needing to write code to distinguish between, and accommodate for, each type of display.</span></span>

## <a name="enabling-the-camera-system"></a><span data-ttu-id="78fcc-107">啟用相機系統</span><span class="sxs-lookup"><span data-stu-id="78fcc-107">Enabling the camera system</span></span>

<span data-ttu-id="78fcc-108">攝影機系統是由 MixedRealityToolkit 物件 (或另一個服務註冊機構元件) 管理。</span><span class="sxs-lookup"><span data-stu-id="78fcc-108">The Camera System is managed by the MixedRealityToolkit object (or another service registrar component).</span></span>

<span data-ttu-id="78fcc-109">下列步驟假設使用 MixedRealityToolkit 物件。</span><span class="sxs-lookup"><span data-stu-id="78fcc-109">The following steps presume use of the MixedRealityToolkit object.</span></span> <span data-ttu-id="78fcc-110">其他服務註冊機構所需的步驟可能會不同。</span><span class="sxs-lookup"><span data-stu-id="78fcc-110">Steps required for other service registrars may be different.</span></span>

1. <span data-ttu-id="78fcc-111">選取場景階層中的 MixedRealityToolkit 物件。</span><span class="sxs-lookup"><span data-stu-id="78fcc-111">Select the MixedRealityToolkit object in the scene hierarchy.</span></span>

    ![MRTK 設定的場景階層](../images/MRTK_ConfiguredHierarchy.png)

2. <span data-ttu-id="78fcc-113">將 [偵測器] 面板移至 [相機系統] 區段，並確定已核取 [ **啟用相機系統** ]。</span><span class="sxs-lookup"><span data-stu-id="78fcc-113">Navigate the Inspector panel to the camera system section and ensure that **Enable Camera System** is checked.</span></span>

    ![啟用相機系統](../images/camera-system/EnableCameraSystem.png)

3. <span data-ttu-id="78fcc-115">選取相機系統的執行。</span><span class="sxs-lookup"><span data-stu-id="78fcc-115">Select the camera system implementation.</span></span> <span data-ttu-id="78fcc-116">MRTK 提供的預設類別實作為 `MixedRealityCameraSystem` 。</span><span class="sxs-lookup"><span data-stu-id="78fcc-116">The default class implementation provided by the MRTK is the `MixedRealityCameraSystem`.</span></span>

    ![選取相機系統執行](../images/camera-system/SelectCameraSystemType.png)

4. <span data-ttu-id="78fcc-118">選取所需的設定設定檔</span><span class="sxs-lookup"><span data-stu-id="78fcc-118">Select the desired configuration profile</span></span>

    ![選取相機系統設定檔](../images/camera-system/SelectCameraProfile.png)

## <a name="configuring-the-camera-system"></a><span data-ttu-id="78fcc-120">設定相機系統</span><span class="sxs-lookup"><span data-stu-id="78fcc-120">Configuring the camera system</span></span>

### <a name="settings-providers"></a><span data-ttu-id="78fcc-121">設定提供者</span><span class="sxs-lookup"><span data-stu-id="78fcc-121">Settings providers</span></span>

![攝影機設定提供者](../images/camera-system/CameraSettingsProviders.png)

<span data-ttu-id="78fcc-123">攝影機設定提供者會啟用相機的平臺特定設定。</span><span class="sxs-lookup"><span data-stu-id="78fcc-123">Camera setting providers enable platform specific configuration of the camera.</span></span> <span data-ttu-id="78fcc-124">這些設定可能包含自訂設定步驟和/或元件。</span><span class="sxs-lookup"><span data-stu-id="78fcc-124">These settings may include custom configuration steps and/or components.</span></span>

<span data-ttu-id="78fcc-125">您可以按一下 [ **新增相機設定提供者** ] 按鈕來加入提供者。</span><span class="sxs-lookup"><span data-stu-id="78fcc-125">Providers can be added by clicking the **Add Camera Settings Provider** button.</span></span> <span data-ttu-id="78fcc-126">您可以按一下 **-** 提供者名稱右邊的按鈕來移除它們。</span><span class="sxs-lookup"><span data-stu-id="78fcc-126">They can be removed by clicking the **-** button to the right of the provider's name.</span></span>

> [!Note]
> <span data-ttu-id="78fcc-127">並非所有平臺都需要相機設定提供者。</span><span class="sxs-lookup"><span data-stu-id="78fcc-127">Not all platforms will require a camera settings provider.</span></span> <span data-ttu-id="78fcc-128">如果沒有任何提供者與應用程式執行所在的平臺相容，Microsoft Mixed Reality 工具組將會套用基本的預設值。</span><span class="sxs-lookup"><span data-stu-id="78fcc-128">If there are no providers that are compatible with the platform on which the application is running, the Microsoft Mixed Reality Toolkit will apply basic defaults.</span></span>

### <a name="display-settings"></a><span data-ttu-id="78fcc-129">顯示器設定</span><span class="sxs-lookup"><span data-stu-id="78fcc-129">Display settings</span></span>

![攝影機顯示設定](../images/camera-system/CameraDisplaySettings.png)

<span data-ttu-id="78fcc-131">顯示設定是針對不透明的 (（例如：虛擬實境) 和透明的 (例如： Microsoft HoloLens) 顯示兩者指定的。</span><span class="sxs-lookup"><span data-stu-id="78fcc-131">Display settings are specified for both opaque (ex: Virtual Reality) and transparent (ex: Microsoft HoloLens) displays.</span></span> <span data-ttu-id="78fcc-132">相機是在執行時間使用這些設定來設定。</span><span class="sxs-lookup"><span data-stu-id="78fcc-132">The camera is configured, at run time, using these settings.</span></span>

<span data-ttu-id="78fcc-133">**近距離剪輯**</span><span class="sxs-lookup"><span data-stu-id="78fcc-133">**Near Clip**</span></span>

<span data-ttu-id="78fcc-134">近接的裁剪平面是虛擬物件可以指向相機但仍呈現的最接近量（以量為單位）。</span><span class="sxs-lookup"><span data-stu-id="78fcc-134">The near clip plane is the closest, in meters, that a virtual object can be to the camera and still be rendered.</span></span> <span data-ttu-id="78fcc-135">為了讓使用者更容易緩和，建議將此值設為大於零。</span><span class="sxs-lookup"><span data-stu-id="78fcc-135">For greatest user comfort, it is recommended to make this value greater than zero.</span></span> <span data-ttu-id="78fcc-136">先前的映射包含已發現的值，可在各種裝置上感到滿意。</span><span class="sxs-lookup"><span data-stu-id="78fcc-136">The previous image contains values that have been found to be comfortable on a variety of devices.</span></span>

<span data-ttu-id="78fcc-137">**最遠的剪輯**</span><span class="sxs-lookup"><span data-stu-id="78fcc-137">**Far Clip**</span></span>

<span data-ttu-id="78fcc-138">最遠的剪輯平面是在計量中，虛擬物件可以是相機的最遠，而且仍會呈現。</span><span class="sxs-lookup"><span data-stu-id="78fcc-138">The far clip plane is the furthest, in meters, that a virtual object can be to the camera and still be rendered.</span></span> <span data-ttu-id="78fcc-139">針對透明裝置，建議此值相對較接近真實世界空間，並中斷應用程式的沉浸式品質。</span><span class="sxs-lookup"><span data-stu-id="78fcc-139">For transparent devices, it is recommended that this value be relatively close as not to overly exceed the real world space and break the application's immersive qualities.</span></span>

<span data-ttu-id="78fcc-140">**清除旗標**</span><span class="sxs-lookup"><span data-stu-id="78fcc-140">**Clear Flags**</span></span>

<span data-ttu-id="78fcc-141">「清除旗標」值表示在繪製時如何清除顯示。</span><span class="sxs-lookup"><span data-stu-id="78fcc-141">The clear flags value indicates how the display is cleared as it is drawn.</span></span> <span data-ttu-id="78fcc-142">針對虛擬實境經驗，此值最常設為 Skybox。</span><span class="sxs-lookup"><span data-stu-id="78fcc-142">For virtual reality experiences, this value is most often set to Skybox.</span></span> <span data-ttu-id="78fcc-143">針對透明顯示，建議將此設定為 [色彩]。</span><span class="sxs-lookup"><span data-stu-id="78fcc-143">For transparent displays, it is recommended to set this to Color.</span></span>

<span data-ttu-id="78fcc-144">**背景色彩**</span><span class="sxs-lookup"><span data-stu-id="78fcc-144">**Background Color**</span></span>

<span data-ttu-id="78fcc-145">如果清除旗標未設定為 Skybox，則會顯示背景色彩屬性。</span><span class="sxs-lookup"><span data-stu-id="78fcc-145">If the clear flags are not set to Skybox, the background color property will be displayed.</span></span>

<span data-ttu-id="78fcc-146">**品質設定**</span><span class="sxs-lookup"><span data-stu-id="78fcc-146">**Quality Settings**</span></span>

<span data-ttu-id="78fcc-147">[品質設定] 值表示 Unity 在呈現場景時應該使用的圖形品質。</span><span class="sxs-lookup"><span data-stu-id="78fcc-147">The quality settings value indicates the graphics quality that Unity should use when it renders the scene.</span></span> <span data-ttu-id="78fcc-148">品質層級是專案層級設定，不是任何一張相機特有的。</span><span class="sxs-lookup"><span data-stu-id="78fcc-148">The quality level is a project level setting and is not specific to any one camera.</span></span> <span data-ttu-id="78fcc-149">如需詳細資訊，請參閱 Unity 檔中的 [品質](https://docs.unity3d.com/Manual/class-QualitySettings.html) 文章。</span><span class="sxs-lookup"><span data-stu-id="78fcc-149">For more information, please see the [Quality](https://docs.unity3d.com/Manual/class-QualitySettings.html) article in Unity's documentation.</span></span>

## <a name="see-also"></a><span data-ttu-id="78fcc-150">另請參閱</span><span class="sxs-lookup"><span data-stu-id="78fcc-150">See also</span></span>

- [<span data-ttu-id="78fcc-151">攝影機系統 API 檔</span><span class="sxs-lookup"><span data-stu-id="78fcc-151">Camera System API Documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.CameraSystem)
- [<span data-ttu-id="78fcc-152">建立相機設定提供者</span><span class="sxs-lookup"><span data-stu-id="78fcc-152">Creating a Camera Settings Provider</span></span>](CreateSettingsProvider.md)
