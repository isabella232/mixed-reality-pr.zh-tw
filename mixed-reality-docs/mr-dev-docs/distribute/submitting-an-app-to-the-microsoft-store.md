---
title: 將應用程式提交到 Microsoft Store
description: 探索封裝、測試及提交混合現實應用程式到 Microsoft Store 的流程。
author: hferrone
ms.author: mazeller
ms.date: 11/13/2020
ms.topic: article
keywords: Microsoft Store、HoloLens、沉浸式耳機、應用程式、uwp、提交、提交、篩選、中繼資料、系統需求、關鍵字、wack、認證、套件、appx、商品、混合現實耳機、windows mixed reality 耳機、虛擬實境耳機
ms.openlocfilehash: 8597526d35aa7ac7afadec0dd33fd23ef82d668a
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583881"
---
# <a name="submitting-an-app-to-the-microsoft-store"></a><span data-ttu-id="e555e-104">將應用程式提交到 Microsoft Store</span><span class="sxs-lookup"><span data-stu-id="e555e-104">Submitting an app to the Microsoft Store</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e555e-105">如果您要提交 Unreal 應用程式，請務必遵循 **[發佈指示](../develop/unreal/unreal-publishing-to-store.md)** ，再繼續進行操作。</span><span class="sxs-lookup"><span data-stu-id="e555e-105">If you're submitting an Unreal application, make sure you follow the **[publishing instructions](../develop/unreal/unreal-publishing-to-store.md)** before continuing.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e555e-106">必要條件</span><span class="sxs-lookup"><span data-stu-id="e555e-106">Prerequisites</span></span>

<span data-ttu-id="e555e-107">[HoloLens](/hololens/hololens1-hardware)和 Windows 10 PC 都能為您的[沉浸式耳機](../discover/immersive-headset-hardware-details.md)執行通用 Windows 平臺應用程式。</span><span class="sxs-lookup"><span data-stu-id="e555e-107">Both [HoloLens](/hololens/hololens1-hardware) and the Windows 10 PC powering your [immersive headset](../discover/immersive-headset-hardware-details.md) run Universal Windows Platform apps.</span></span> <span data-ttu-id="e555e-108">無論您是提交支援 HoloLens、電腦或兩者的應用程式，提交應用程式都會經歷 [合作夥伴中心](https://partner.microsoft.com/dashboard)。</span><span class="sxs-lookup"><span data-stu-id="e555e-108">Whether you're submitting an app that supports HoloLens, PC, or both, app submission goes through the [Partner Center](https://partner.microsoft.com/dashboard).</span></span>

<span data-ttu-id="e555e-109">如果您還沒有合作夥伴中心開發人員帳戶，請先 [註冊](https://developer.microsoft.com/store/register) 一個帳戶，再繼續進行。</span><span class="sxs-lookup"><span data-stu-id="e555e-109">If you don't already have a Partner Center developer account, [sign up](https://developer.microsoft.com/store/register) for one before moving on.</span></span> <span data-ttu-id="e555e-110">您可以在此 [應用程式提交文章](/windows/uwp/publish/app-submissions)中找到有關提交指導方針和檢查清單的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="e555e-110">You can find more information about submission guidelines and checklists in this [app submissions article](/windows/uwp/publish/app-submissions).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e555e-111">如果您的合作夥伴中心開發人員帳戶無法進行雇用驗證檢查，您將無法將任何應用程式提交至 Microsoft Store。</span><span class="sxs-lookup"><span data-stu-id="e555e-111">You won't be able to submit any applications to the Microsoft Store if your Partner Center developer account fails the employment verification check.</span></span> <span data-ttu-id="e555e-112">如需詳細資訊，請洽詢合作夥伴中心 [支援小組](https://developer.microsoft.com/windows/support) 。</span><span class="sxs-lookup"><span data-stu-id="e555e-112">Please contact the Partner Center [support team](https://developer.microsoft.com/windows/support) for more details.</span></span>

## <a name="packaging-a-mixed-reality-app"></a><span data-ttu-id="e555e-113">封裝混合現實應用程式</span><span class="sxs-lookup"><span data-stu-id="e555e-113">Packaging a Mixed Reality app</span></span>

<span data-ttu-id="e555e-114">封裝混合現實應用程式有幾個步驟，包括：</span><span class="sxs-lookup"><span data-stu-id="e555e-114">There are several steps to packaging a Mixed Reality application, including:</span></span>

* <span data-ttu-id="e555e-115">正確準備所有映射資產</span><span class="sxs-lookup"><span data-stu-id="e555e-115">Correctly preparing all image assets</span></span>
* <span data-ttu-id="e555e-116">選擇 HoloLens [開始] 功能表中顯示的磚影像</span><span class="sxs-lookup"><span data-stu-id="e555e-116">Choosing the tile image displayed in the HoloLens Start menu</span></span>
* <span data-ttu-id="e555e-117">設定應用程式的目標和最低 Windows 版本</span><span class="sxs-lookup"><span data-stu-id="e555e-117">Setting the target and minimum Windows version for the app</span></span>
* <span data-ttu-id="e555e-118">設定應用程式相依性中的目標裝置系列</span><span class="sxs-lookup"><span data-stu-id="e555e-118">Setting the target device families in the app dependencies</span></span>
* <span data-ttu-id="e555e-119">新增中繼資料以建立應用程式與 Microsoft Store 的關聯</span><span class="sxs-lookup"><span data-stu-id="e555e-119">Adding metadata to associate the app with the Microsoft Store</span></span>
* <span data-ttu-id="e555e-120">建立上傳套件</span><span class="sxs-lookup"><span data-stu-id="e555e-120">Creating an upload package</span></span>

<span data-ttu-id="e555e-121">每個提交階段都涵蓋在下一節中，我們建議您依序執行，您不會在第一次提交嘗試時繼續進行。</span><span class="sxs-lookup"><span data-stu-id="e555e-121">Each of these submission stages is covered in its own section below - we recommend going through them sequentially you don't leave any out on your first submission attempt.</span></span>

### <a name="prepare-image-assets-included-in-the-appx"></a><span data-ttu-id="e555e-122">準備隨附于 appx 的映射資產</span><span class="sxs-lookup"><span data-stu-id="e555e-122">Prepare image assets included in the appx</span></span>

<span data-ttu-id="e555e-123">若要將您的應用程式建立至 appx 套件（提交給 Microsoft Store 所需的 appx 套件），appx 建立工具需要下列映射資產。</span><span class="sxs-lookup"><span data-stu-id="e555e-123">The following image assets are required for the appx building tools to build your application into an appx package, which is required for submission to the Microsoft Store.</span></span> <span data-ttu-id="e555e-124">您可以在 MSDN 上深入瞭解 [磚和圖示資產的指導方針](/windows/uwp/app-resources/images-tailored-for-scale-theme-contrast) 。</span><span class="sxs-lookup"><span data-stu-id="e555e-124">You can learn more about [guidelines for tile and icon assets](/windows/uwp/app-resources/images-tailored-for-scale-theme-contrast) on MSDN.</span></span>

| <span data-ttu-id="e555e-125">必要資產</span><span class="sxs-lookup"><span data-stu-id="e555e-125">Required Asset</span></span> | <span data-ttu-id="e555e-126">建議的調整</span><span class="sxs-lookup"><span data-stu-id="e555e-126">Recommended Scale</span></span> | <span data-ttu-id="e555e-127">映像格式</span><span class="sxs-lookup"><span data-stu-id="e555e-127">Image Format</span></span> | <span data-ttu-id="e555e-128">資產顯示在哪裡？</span><span class="sxs-lookup"><span data-stu-id="e555e-128">Where is the asset displayed?</span></span> | 
|----------|----------|----------|------------------|
| <span data-ttu-id="e555e-129">正方形71x71 標誌</span><span class="sxs-lookup"><span data-stu-id="e555e-129">Square 71x71 Logo</span></span> | <span data-ttu-id="e555e-130">任意</span><span class="sxs-lookup"><span data-stu-id="e555e-130">Any</span></span> |  <span data-ttu-id="e555e-131">PNG</span><span class="sxs-lookup"><span data-stu-id="e555e-131">PNG</span></span> | <span data-ttu-id="e555e-132">不適用</span><span class="sxs-lookup"><span data-stu-id="e555e-132">N/A</span></span> | 
| <span data-ttu-id="e555e-133">正方形150x150 標誌</span><span class="sxs-lookup"><span data-stu-id="e555e-133">Square 150x150 Logo</span></span> | <span data-ttu-id="e555e-134">150x150 (100% scale) 或 225x225 (150% scale) </span><span class="sxs-lookup"><span data-stu-id="e555e-134">150x150 (100% scale) or 225x225 (150% scale)</span></span> | <span data-ttu-id="e555e-135">PNG</span><span class="sxs-lookup"><span data-stu-id="e555e-135">PNG</span></span> | <span data-ttu-id="e555e-136">如果未提供310x310，則啟動釘選和所有應用程式 () 、商店搜尋建議、商店清單頁面、商店流覽、商店搜尋</span><span class="sxs-lookup"><span data-stu-id="e555e-136">Start pins and All Apps (if 310x310 isn't provided), Store Search Suggestions, Store Listing Page, Store Browse, Store Search</span></span> | 
|  <span data-ttu-id="e555e-137">寬310x150 標誌</span><span class="sxs-lookup"><span data-stu-id="e555e-137">Wide 310x150 Logo</span></span> |  <span data-ttu-id="e555e-138">任意</span><span class="sxs-lookup"><span data-stu-id="e555e-138">Any</span></span>  |  <span data-ttu-id="e555e-139">PNG</span><span class="sxs-lookup"><span data-stu-id="e555e-139">PNG</span></span>  |  <span data-ttu-id="e555e-140">不適用</span><span class="sxs-lookup"><span data-stu-id="e555e-140">N/A</span></span> | 
|  <span data-ttu-id="e555e-141">市集標誌</span><span class="sxs-lookup"><span data-stu-id="e555e-141">Store Logo</span></span> |  <span data-ttu-id="e555e-142">75x75 (150% 規模) </span><span class="sxs-lookup"><span data-stu-id="e555e-142">75x75 (150% scale)</span></span>  |  <span data-ttu-id="e555e-143">PNG</span><span class="sxs-lookup"><span data-stu-id="e555e-143">PNG</span></span>  |  <span data-ttu-id="e555e-144">合作夥伴中心，報表應用程式，撰寫評論，我的文件庫</span><span class="sxs-lookup"><span data-stu-id="e555e-144">Partner Center, Report App, Write a Review, My Library</span></span> | 
|  <span data-ttu-id="e555e-145">啟動顯示畫面</span><span class="sxs-lookup"><span data-stu-id="e555e-145">Splash Screen</span></span> |  <span data-ttu-id="e555e-146">930x450 (150% 規模) </span><span class="sxs-lookup"><span data-stu-id="e555e-146">930x450 (150% scale)</span></span>  |  <span data-ttu-id="e555e-147">PNG</span><span class="sxs-lookup"><span data-stu-id="e555e-147">PNG</span></span>  |  <span data-ttu-id="e555e-148">2D 應用程式啟動器 (平板) </span><span class="sxs-lookup"><span data-stu-id="e555e-148">2D app launcher (slate)</span></span> | 

<span data-ttu-id="e555e-149">如果您正在針對 HoloLens 進行開發，還有其他建議的資產可供您利用：</span><span class="sxs-lookup"><span data-stu-id="e555e-149">If you're developing for HoloLens, there are other recommended assets that you can take advantage of:</span></span>

| <span data-ttu-id="e555e-150">建議的資產</span><span class="sxs-lookup"><span data-stu-id="e555e-150">Recommended Assets</span></span> | <span data-ttu-id="e555e-151">建議的調整</span><span class="sxs-lookup"><span data-stu-id="e555e-151">Recommended Scale</span></span> | <span data-ttu-id="e555e-152">資產顯示在哪裡？</span><span class="sxs-lookup"><span data-stu-id="e555e-152">Where is the asset displayed?</span></span> | 
|----------|----------|----------|
|  <span data-ttu-id="e555e-153">正方形310x310 標誌</span><span class="sxs-lookup"><span data-stu-id="e555e-153">Square 310x310 Logo</span></span> |  <span data-ttu-id="e555e-154">310x310 (150% 規模) </span><span class="sxs-lookup"><span data-stu-id="e555e-154">310x310 (150% scale)</span></span> |  <span data-ttu-id="e555e-155">開始釘選和所有應用程式</span><span class="sxs-lookup"><span data-stu-id="e555e-155">Start pins and All Apps</span></span> | 

### <a name="live-tile-requirements"></a><span data-ttu-id="e555e-156">動態磚需求</span><span class="sxs-lookup"><span data-stu-id="e555e-156">Live Tile requirements</span></span>

<span data-ttu-id="e555e-157">根據預設，HoloLens 上的 [開始] 功能表將會使用最大內含的正方形圖格影像。</span><span class="sxs-lookup"><span data-stu-id="e555e-157">The Start menu on HoloLens will use the largest included square tile image by default.</span></span> <span data-ttu-id="e555e-158">Microsoft 發佈的應用程式有選擇性的3D 啟動器，可讓您遵循 [3d 應用程式啟動器的執行](implementing-3d-app-launchers.md) 指示，將其新增至您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="e555e-158">Apps published by Microsoft have an optional 3D launcher, which you can add to your app by following the [3D app launcher implementation](implementing-3d-app-launchers.md) instructions.</span></span>

### <a name="specifying-target-and-minimum-version-of-windows"></a><span data-ttu-id="e555e-159">指定 Windows 的目標和最小版本</span><span class="sxs-lookup"><span data-stu-id="e555e-159">Specifying target and minimum version of Windows</span></span>

<span data-ttu-id="e555e-160">如果您的混合現實應用程式包含 Windows 版本特有的功能，請務必指定支援的目標和最低平臺版本。</span><span class="sxs-lookup"><span data-stu-id="e555e-160">If your Mixed Reality app includes features that are specific to a Windows version, it's important to specify the supported target and minimum platform versions.</span></span>

<span data-ttu-id="e555e-161">**特別注意以 [Windows Mixed Reality 沉浸式耳機](../discover/immersive-headset-hardware-details.md)為目標的應用程式，其至少需要 Windows 10 Fall Creators Update (10.0;組建 16299) 可正常運作。**</span><span class="sxs-lookup"><span data-stu-id="e555e-161">**Pay special attention for apps targeting [Windows Mixed Reality immersive headsets](../discover/immersive-headset-hardware-details.md), which require at least the Windows 10 Fall Creators Update (10.0; Build 16299) to function properly.**</span></span>

<span data-ttu-id="e555e-162">當您在 Visual Studio 中建立新的通用 Windows 專案時，系統會提示您設定 Windows 的目標和最小版本。</span><span class="sxs-lookup"><span data-stu-id="e555e-162">You'll be prompted to set the target and minimum version of Windows when you create a new Universal Windows Project in Visual Studio.</span></span> <span data-ttu-id="e555e-163">針對現有的專案，您可以在下拉式功能表中選取 [ **<您的應用程式名稱>** 內容，來變更 [**專案**] 功能表中的這個設定。</span><span class="sxs-lookup"><span data-stu-id="e555e-163">For existing projects, you can change this setting in the **Project** menu by selecting the **<Your app name's> Properties** at the bottom of the drop-down menu.</span></span>

<span data-ttu-id="e555e-164">![在 Visual Studio 2019 中設定最低和目標平臺版本](images/visual-studio-min-version-500px.png)</span><span class="sxs-lookup"><span data-stu-id="e555e-164">![Setting minimum and target platform versions in Visual Studio 2019](images/visual-studio-min-version-500px.png)</span></span><br>
<span data-ttu-id="e555e-165">*在 Visual Studio 中設定最低和目標平臺版本*</span><span class="sxs-lookup"><span data-stu-id="e555e-165">*Setting minimum and target platform versions in Visual Studio*</span></span>

### <a name="specifying-target-device-families"></a><span data-ttu-id="e555e-166">指定目標裝置系列</span><span class="sxs-lookup"><span data-stu-id="e555e-166">Specifying target device families</span></span>

<span data-ttu-id="e555e-167">適用于 [hololens](/hololens/hololens1-hardware)和 [沉浸式耳機](../discover/immersive-headset-hardware-details.md)的 Windows Mixed Reality 應用程式 () 是通用 Windows 平臺的一部分，因此任何具有 **Windows 通用**[目標裝置系列](/uwp/schemas/appxpackage/uapmanifestschema/element-targetdevicefamily)的應用程式套件，都可以在 HoloLens 或具有沉浸式耳機的 Windows 10 電腦上執行。</span><span class="sxs-lookup"><span data-stu-id="e555e-167">Windows Mixed Reality applications (for both [HoloLens](/hololens/hololens1-hardware) and [immersive headsets](../discover/immersive-headset-hardware-details.md)) are part of the Universal Windows Platform, so any app package with a **Windows.Universal** [target device family](/uwp/schemas/appxpackage/uapmanifestschema/element-targetdevicefamily) can run on HoloLens or Windows 10 PCs with immersive headsets.</span></span> <span data-ttu-id="e555e-168">如果您未在應用程式資訊清單中指定目標裝置系列，您可能會不小心開啟您的應用程式，而非預期的 Windows 10 裝置。</span><span class="sxs-lookup"><span data-stu-id="e555e-168">If you don't specify a target device family in your app manifest, you may inadvertently open your app up to unintended Windows 10 devices.</span></span> <span data-ttu-id="e555e-169">遵循下列步驟來指定預期的 Windows 10 裝置系列，然後 [再次檢查您在合作夥伴中心中上傳應用程式套件以進行 Microsoft Store 提交時，已設定正確的裝置系列。](submitting-an-app-to-the-microsoft-store.md#submitting-your-mixed-reality-app-to-the-store)</span><span class="sxs-lookup"><span data-stu-id="e555e-169">Follow the steps below to specify the intended Windows 10 device family, then [double-check you've set the correct device families when you upload your app package in Partner Center for Microsoft Store submission.](submitting-an-app-to-the-microsoft-store.md#submitting-your-mixed-reality-app-to-the-store)</span></span>

* <span data-ttu-id="e555e-170">若要在 Visual Studio 中設定此欄位，請以滑鼠右鍵按一下 **package.appxmanifest** ，然後選取 [ **View Code**]，然後尋找 [ **y Name** ] 欄位。</span><span class="sxs-lookup"><span data-stu-id="e555e-170">To set this field in Visual Studio, right-click on the **Package.appxmanifest** and select **View Code**, then find the **TargetDeviceFamily Name** field.</span></span> <span data-ttu-id="e555e-171">依預設，它看起來應該類似下列專案：</span><span class="sxs-lookup"><span data-stu-id="e555e-171">By default, it should look like the following entry:</span></span>

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Universal" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10586.0" />
</Dependencies>
```

* <span data-ttu-id="e555e-172">如果您要建立 **hololens** 應用程式，可以將目標裝置系列設定為 Windows，以確定它只會安裝在 hololens 上 **。** 全像：</span><span class="sxs-lookup"><span data-stu-id="e555e-172">If you're creating a **HoloLens** app, you can make sure it's only installed on HoloLens by setting the target device family to **Windows.Holographic**:</span></span> 

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Holographic" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10586.0" />
</Dependencies>
```

* <span data-ttu-id="e555e-173">如果您的應用程式需要 **HoloLens 2** 功能，例如眼睛或手動追蹤，您可以藉由將目標裝置系列 **設定為 windows，以確定** 其為 windows 18362 版或更新版本的目標 ：10.0.18362.0：</span><span class="sxs-lookup"><span data-stu-id="e555e-173">If your app requires **HoloLens 2** functionality, like eye or hand-tracking, you can make sure it's targeted to Windows versions 18362 or greater by setting the target device family to **Windows.Holographic** with a **MinVersion** of 10.0.18362.0:</span></span>

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Holographic" MinVersion="10.0.18362.0" MaxVersionTested="10.0.18362.0" />
</Dependencies>
```

* <span data-ttu-id="e555e-174">如果您的應用程式是針對 **Windows Mixed Reality 沉浸式耳機** 建立的，您可以將目標裝置系列設定為 Windows，以確定它只會安裝在具有 Windows Mixed Reality) 所需 Windows 10 Fall Creators Update (的 Windows 10 電腦上 **。** 10.0.16299.0 的 **MinVersion** ：</span><span class="sxs-lookup"><span data-stu-id="e555e-174">If your app is created for **Windows Mixed Reality immersive headsets**, you can make sure it's only installed on Windows 10 PCs with the Windows 10 Fall Creators Update (necessary for Windows Mixed Reality) by setting the target device family to **Windows.Desktop** with a **MinVersion** of 10.0.16299.0:</span></span>

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Desktop" MinVersion="10.0.16299.0" MaxVersionTested="10.0.16299.0" />
</Dependencies>
```

* <span data-ttu-id="e555e-175">最後，如果您的應用程式是要在 **HoloLens** 和 **Windows Mixed Reality 沉浸式耳機** 上執行，您可以確定應用程式僅適用于這兩個裝置系列，同時確保每個目標都有正確的最低 Windows 版本，方法是為每個目標裝置系列加入一行，以及各自的 MinVersion：</span><span class="sxs-lookup"><span data-stu-id="e555e-175">Finally, if your app is intended to run on both **HoloLens** and **Windows Mixed Reality immersive headsets**, you can make sure the app is only available to those two device families and simultaneously ensure that each target has the correct minimum Windows version by including a line for each target device family with its respective MinVersion:</span></span>

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Desktop" MinVersion="10.0.16299.0" MaxVersionTested="10.0.16299.0" />
   <TargetDeviceFamily Name="Windows.Holographic" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10586.0" />
</Dependencies>
```

<span data-ttu-id="e555e-176">您可以閱讀 [y UWP 檔](/uwp/schemas/appxpackage/uapmanifestschema/element-targetdevicefamily)，以深入瞭解目標裝置系列。</span><span class="sxs-lookup"><span data-stu-id="e555e-176">You can learn more about targeting device families by reading the [TargetDeviceFamily UWP documentation](/uwp/schemas/appxpackage/uapmanifestschema/element-targetdevicefamily).</span></span>

### <a name="associate-app-with-the-store"></a><span data-ttu-id="e555e-177">建立應用程式與存放區的關聯</span><span class="sxs-lookup"><span data-stu-id="e555e-177">Associate app with the Store</span></span>

<span data-ttu-id="e555e-178">當您建立應用程式與 Microsoft Store 的關聯時，會將下列值下載至目前專案的本機應用程式資訊清單檔：</span><span class="sxs-lookup"><span data-stu-id="e555e-178">When you associate your app with the Microsoft Store, the following values are downloaded to the current projects local app manifest file:</span></span>

* <span data-ttu-id="e555e-179">套件顯示名稱</span><span class="sxs-lookup"><span data-stu-id="e555e-179">Package Display Name</span></span>
* <span data-ttu-id="e555e-180">封裝名稱</span><span class="sxs-lookup"><span data-stu-id="e555e-180">Package Name</span></span>
* <span data-ttu-id="e555e-181">發行者識別碼</span><span class="sxs-lookup"><span data-stu-id="e555e-181">Publisher ID</span></span>
* <span data-ttu-id="e555e-182">發行者顯示名稱</span><span class="sxs-lookup"><span data-stu-id="e555e-182">Publisher Display Name</span></span>
* <span data-ttu-id="e555e-183">版本</span><span class="sxs-lookup"><span data-stu-id="e555e-183">Version</span></span>

<span data-ttu-id="e555e-184">如果您要使用自己的自訂 .xml 檔案來覆寫預設的 package.appxmanifest 檔案，則無法將應用程式與 Microsoft Store 產生關聯。</span><span class="sxs-lookup"><span data-stu-id="e555e-184">If you're overriding the default package.appxmanifest file with your own custom .xml file, you can’t associate your app with the Microsoft Store.</span></span> <span data-ttu-id="e555e-185">將自訂資訊清單檔與存放區產生關聯將會產生錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="e555e-185">Associating a custom manifest file with the Store will result in an error message.</span></span>

<span data-ttu-id="e555e-186">您也可以藉由前往您的 Visual Studio 解決方案，然後選取 **[專案] > [儲存] > 將應用程式與存放區建立關聯**，來測試購買和通知案例。</span><span class="sxs-lookup"><span data-stu-id="e555e-186">You can also test purchase and notification scenarios by going to your Visual Studio solution and selecting **Project > Store > Associate App with the Store**.</span></span>

### <a name="creating-an-upload-package"></a><span data-ttu-id="e555e-187">建立上傳套件</span><span class="sxs-lookup"><span data-stu-id="e555e-187">Creating an upload package</span></span>

<span data-ttu-id="e555e-188">遵循將 [通用 Windows 應用程式封裝 Windows 10 的](/previous-versions/windows/apps/hh454036(v=vs.140)#Anchor_2)指導方針。</span><span class="sxs-lookup"><span data-stu-id="e555e-188">Follow guidelines at [Packaging Universal Windows apps for Windows 10](/previous-versions/windows/apps/hh454036(v=vs.140)#Anchor_2).</span></span>

<span data-ttu-id="e555e-189">建立上傳封裝的最後一個步驟是使用 [Windows 應用程式認證套件](#windows-app-certification-kit)來驗證封裝。</span><span class="sxs-lookup"><span data-stu-id="e555e-189">The final step of creating an upload package is validating the package using the [Windows App Certification Kit](#windows-app-certification-kit).</span></span>

<span data-ttu-id="e555e-190">如果您要將 HoloLens 專屬套件新增至其他 Windows 10 裝置系列上可用的現有產品，請注意：</span><span class="sxs-lookup"><span data-stu-id="e555e-190">If you're adding a HoloLens-specific package to an existing product that's available on other Windows 10 device families, pay attention to:</span></span> 

* [<span data-ttu-id="e555e-191">版本號碼可能會如何影響傳遞給特定客戶的套件</span><span class="sxs-lookup"><span data-stu-id="e555e-191">How version numbers may impact which packages are delivered to specific customers</span></span>](/windows/uwp/publish/package-version-numbering)
* [<span data-ttu-id="e555e-192">封裝如何散發到不同的作業系統</span><span class="sxs-lookup"><span data-stu-id="e555e-192">How packages are distributed to different operating systems</span></span>](/windows/uwp/publish/guidance-for-app-package-management)

<span data-ttu-id="e555e-193">一般指引是具有裝置最高版本號碼的套件是存放區所散發的套件。</span><span class="sxs-lookup"><span data-stu-id="e555e-193">The general guidance is that the package with the highest version number for a device is the one distributed by the Store.</span></span>

<span data-ttu-id="e555e-194">在有 **Windows 通用** 套件和 **windows** 全像套件的案例中，而 windows 通用套件的版本號碼較高時，HoloLens 使用者將會下載較高版本號碼的 windows 通用套件，而不是使用 windows 的全像套件。</span><span class="sxs-lookup"><span data-stu-id="e555e-194">In a scenario where there's a **Windows.Universal** package and a **Windows.Holographic** package, and the Windows.Universal package has a higher version number, a HoloLens user will download the higher version number Windows.Universal package instead of the Windows.Holographic package.</span></span> 

<span data-ttu-id="e555e-195">如果上述案例不是您要尋找的結果，則有數個可用的解決方案：</span><span class="sxs-lookup"><span data-stu-id="e555e-195">In cases where the above scenario isn't the outcome you're looking for, there are several available solutions:</span></span>

* <span data-ttu-id="e555e-196">確定您的平臺專屬套件（例如，Windows）的版本號碼一律比您的平臺中立套件（例如 Windows 通用）更高。</span><span class="sxs-lookup"><span data-stu-id="e555e-196">Ensure your platform-specific packages, such as Windows.Holographic, always have a higher version number than your platform agnostic packages like Windows.Universal</span></span>
* <span data-ttu-id="e555e-197">如果您也擁有平臺特定套件，請不要將應用程式封裝為 Windows 通用套件，改為將 Windows 通用套件封裝到您想要使用的特定平臺</span><span class="sxs-lookup"><span data-stu-id="e555e-197">Don't package apps as Windows.Universal if you also have platform-specific packages - instead package the Windows.Universal package for the specific platforms you want it available on</span></span>
* <span data-ttu-id="e555e-198">建立可在所有平臺上運作的單一 Windows 通用套件。</span><span class="sxs-lookup"><span data-stu-id="e555e-198">Create a single Windows.Universal package that works across all platforms.</span></span> <span data-ttu-id="e555e-199">此選項的支援目前並不適用，因此建議使用上述的解決方案。</span><span class="sxs-lookup"><span data-stu-id="e555e-199">Support for this option isn't great right now so the above solutions are recommended.</span></span>

>[!NOTE]
> <span data-ttu-id="e555e-200">若要在 HoloLens (第一代) 和 HoloLen 2 上支援您的應用程式，您需要上傳兩個應用程式套件;其中一個包含適用于 HoloLens 的 x86 (第一代) ，另一個則包含適用于 HoloLens 2 的 ARM 或 ARM64。</span><span class="sxs-lookup"><span data-stu-id="e555e-200">To support your app on both HoloLens (1st Gen) and HoloLen 2, you need to upload two app packages; one containing x86 for HoloLens (1st Gen) and one containing ARM or ARM64 for HoloLens 2.</span></span> 
> 
> <span data-ttu-id="e555e-201">如果您在套件中同時包含 ARM 和 ARM64，ARM64 版本將會是 HoloLens 2 上使用的版本。</span><span class="sxs-lookup"><span data-stu-id="e555e-201">If you include both ARM and ARM64 in your package, the ARM64 version will be the one used on HoloLens 2.</span></span> 

>[!NOTE]
> <span data-ttu-id="e555e-202">您可以宣告單一套件以適用于多個目標裝置系列</span><span class="sxs-lookup"><span data-stu-id="e555e-202">You can declare a single package to be applicable to multiple target device families</span></span>

## <a name="testing-your-app"></a><span data-ttu-id="e555e-203">測試應用程式</span><span class="sxs-lookup"><span data-stu-id="e555e-203">Testing your app</span></span>

### <a name="windows-app-certification-kit"></a><span data-ttu-id="e555e-204">Windows 應用程式認證套件</span><span class="sxs-lookup"><span data-stu-id="e555e-204">Windows App Certification Kit</span></span>

<span data-ttu-id="e555e-205">當您建立要透過 Visual Studio 提交至合作夥伴中心的應用程式套件時，[建立應用程式套件] 嚮導會提示您針對所建立的套件執行 Windows 應用程式認證套件。</span><span class="sxs-lookup"><span data-stu-id="e555e-205">When you create app packages to submit to Partner Center through Visual Studio, the Create App Packages wizard prompts you to run the Windows App Certification Kit against the packages that get created.</span></span> <span data-ttu-id="e555e-206">若要以順暢的方式將程式提交至商店，最好先確認應用程式的本機複本是否通過 [Windows 應用程式認證套件測試](/previous-versions/windows/apps/jj657973(v=win.10)) ，再將其提交到存放區。</span><span class="sxs-lookup"><span data-stu-id="e555e-206">To have a smooth submission process to the Store, it's best to verify that the local copy of your app passes the [Windows App Certification Kit tests](/previous-versions/windows/apps/jj657973(v=win.10)) before submitting them to the Store.</span></span> <span data-ttu-id="e555e-207">目前不支援在遠端 HoloLens 上執行 Windows 應用程式認證套件。</span><span class="sxs-lookup"><span data-stu-id="e555e-207">Running the Windows App Certification Kit on a remote HoloLens isn't currently supported.</span></span>

### <a name="run-on-all-targeted-device-families"></a><span data-ttu-id="e555e-208">在所有目標裝置系列上執行</span><span class="sxs-lookup"><span data-stu-id="e555e-208">Run on all targeted device families</span></span>

<span data-ttu-id="e555e-209">Windows 通用平臺可讓您建立在所有 Windows 10 裝置系列上執行的單一應用程式。</span><span class="sxs-lookup"><span data-stu-id="e555e-209">The Windows Universal Platform allows you to create a single application that runs across all of the Windows 10 device families.</span></span> <span data-ttu-id="e555e-210">但是，它並不保證通用 Windows 應用程式只會在所有裝置系列上運作。</span><span class="sxs-lookup"><span data-stu-id="e555e-210">However, it doesn't guarantee that Universal Windows apps will just work on all device families.</span></span> <span data-ttu-id="e555e-211">請務必在您選擇的每個裝置系列上 [測試您的應用程式](../develop/platform-capabilities-and-apis/testing-your-app-on-hololens.md) ，以確保良好的體驗。</span><span class="sxs-lookup"><span data-stu-id="e555e-211">It's important to [test your app](../develop/platform-capabilities-and-apis/testing-your-app-on-hololens.md) on each of your chosen device families to ensure a good experience.</span></span>

## <a name="submitting-your-mixed-reality-app-to-the-store"></a><span data-ttu-id="e555e-212">將您的混合現實應用程式提交至商店</span><span class="sxs-lookup"><span data-stu-id="e555e-212">Submitting your Mixed Reality app to the Store</span></span>

<span data-ttu-id="e555e-213">如果您要提交以 Unity 專案為基礎的混合現實應用程式，請先參閱這段 [影片](https://channel9.msdn.com/Blogs/One-Dev-Minute/How-to-publish-your-Unity-game-as-a-UWP-app) 。</span><span class="sxs-lookup"><span data-stu-id="e555e-213">If you're submitting a Mixed Reality app that is based on a Unity project, see this [video](https://channel9.msdn.com/Blogs/One-Dev-Minute/How-to-publish-your-Unity-game-as-a-UWP-app) first.</span></span>

<span data-ttu-id="e555e-214">一般情況下，提交適用于 HoloLens 或沉浸式耳機的 Windows Mixed Reality 應用程式，就像是將任何 UWP 應用程式提交至 Microsoft Store 一樣。</span><span class="sxs-lookup"><span data-stu-id="e555e-214">In general, submitting a Windows Mixed Reality app that works on HoloLens or immersive headsets is just like submitting any UWP app to the Microsoft Store.</span></span> <span data-ttu-id="e555e-215">一旦您藉 [由保留名稱來建立應用程式](/windows/uwp/publish/create-your-app-by-reserving-a-name)，請遵循 [UWP 提交檢查清單](/windows/uwp/publish/app-submissions)。</span><span class="sxs-lookup"><span data-stu-id="e555e-215">Once you've [created your app by reserving its name](/windows/uwp/publish/create-your-app-by-reserving-a-name), follow the [UWP submission checklist](/windows/uwp/publish/app-submissions).</span></span>

<span data-ttu-id="e555e-216">您首先要做的其中一件事，就是為您的混合現實體驗 [選取類別和子類別](/windows/uwp/publish/category-and-subcategory-table) 。</span><span class="sxs-lookup"><span data-stu-id="e555e-216">One of the first things you'll do is [select a category and subcategory](/windows/uwp/publish/category-and-subcategory-table) for your Mixed Reality experience.</span></span> <span data-ttu-id="e555e-217">**請務必為您的應用程式選擇最精確的類別**。</span><span class="sxs-lookup"><span data-stu-id="e555e-217">It's important that you **choose the most accurate category for your app**.</span></span> <span data-ttu-id="e555e-218">類別可協助您將應用程式放在正確的商店類別中，並確保它會使用相關的搜尋查詢來顯示。</span><span class="sxs-lookup"><span data-stu-id="e555e-218">Categories help merchandise your application in the right Store categories and ensure it shows up using relevant search queries.</span></span> <span data-ttu-id="e555e-219">將 **您的 VR 標題列為遊戲，將不會對您的應用程式造成更好的曝光，** 而且可能會讓它無法顯示在更適合且更擁擠的類別中。</span><span class="sxs-lookup"><span data-stu-id="e555e-219">**Listing your VR title as a game won't result in better exposure for your app,** and may prevent it from showing up in categories that are more fitting and less crowded.</span></span>

<span data-ttu-id="e555e-220">不過，提交程式中有四個主要區域，您會想要進行混合的現實特定選擇：</span><span class="sxs-lookup"><span data-stu-id="e555e-220">However, there are four key areas in the submission process where you'll want to make Mixed Reality-specific selections:</span></span>
1. <span data-ttu-id="e555e-221">在 [[屬性](/windows/uwp/publish/enter-app-properties)] 下的 [**[產品](submitting-an-app-to-the-microsoft-store.md#mixed-reality-product-declarations)** 宣告] 區段中。</span><span class="sxs-lookup"><span data-stu-id="e555e-221">In the **[Product declarations](submitting-an-app-to-the-microsoft-store.md#mixed-reality-product-declarations)** section under [Properties](/windows/uwp/publish/enter-app-properties).</span></span>
2. <span data-ttu-id="e555e-222">在 [[屬性](/windows/uwp/publish/enter-app-properties)] 下的 [**[系統需求](submitting-an-app-to-the-microsoft-store.md#mixed-reality-system-requirements)**] 區段中。</span><span class="sxs-lookup"><span data-stu-id="e555e-222">In the **[System requirements](submitting-an-app-to-the-microsoft-store.md#mixed-reality-system-requirements)** section under [Properties](/windows/uwp/publish/enter-app-properties).</span></span>
3. <span data-ttu-id="e555e-223">在 [[套件](/windows/uwp/publish/upload-app-packages)] 下的 [**[裝置系列可用性](submitting-an-app-to-the-microsoft-store.md#device-family-availability)**] 區段中。</span><span class="sxs-lookup"><span data-stu-id="e555e-223">In the **[Device family availability](submitting-an-app-to-the-microsoft-store.md#device-family-availability)** section under [Packages](/windows/uwp/publish/upload-app-packages).</span></span>
4. <span data-ttu-id="e555e-224">在數個 **[Store 清單頁面](submitting-an-app-to-the-microsoft-store.md#store-listing-page)** 欄位中。</span><span class="sxs-lookup"><span data-stu-id="e555e-224">In several of the **[Store listing page](submitting-an-app-to-the-microsoft-store.md#store-listing-page)** fields.</span></span>

### <a name="mixed-reality-product-declarations"></a><span data-ttu-id="e555e-225">混合現實產品聲明</span><span class="sxs-lookup"><span data-stu-id="e555e-225">Mixed Reality product declarations</span></span>

<span data-ttu-id="e555e-226">在應用程式提交程式的 [ **[屬性](/windows/uwp/publish/enter-app-properties)** ] 頁面上，您會在 [ **[產品](/windows/uwp/publish/app-declarations)** 宣告] 區段中找到與混合現實相關的數個選項。</span><span class="sxs-lookup"><span data-stu-id="e555e-226">On the **[Properties](/windows/uwp/publish/enter-app-properties)** page of the app submission process, you'll find several options related to Mixed Reality in the **[Product declarations](/windows/uwp/publish/app-declarations)** section.</span></span>

<span data-ttu-id="e555e-227">![混合現實產品聲明](images/product-declarations-900px.png)</span><span class="sxs-lookup"><span data-stu-id="e555e-227">![Mixed Reality product declarations](images/product-declarations-900px.png)</span></span><br>
<span data-ttu-id="e555e-228">混合現實產品聲明</span><span class="sxs-lookup"><span data-stu-id="e555e-228">Mixed Reality product declarations</span></span>

<span data-ttu-id="e555e-229">首先，您必須識別您的應用程式提供混合現實體驗的裝置類型。</span><span class="sxs-lookup"><span data-stu-id="e555e-229">First, you need to identify the device types for which your app offers a Mixed Reality experience.</span></span> <span data-ttu-id="e555e-230">識別裝置類型可確保您的應用程式包含在存放區中 Windows Mixed Reality 的集合中。</span><span class="sxs-lookup"><span data-stu-id="e555e-230">Identifying device types ensures that your app is included in Windows Mixed Reality collections in the Store.</span></span>

<span data-ttu-id="e555e-231">在「此體驗的設計目的是為了 Windows Mixed Reality：」</span><span class="sxs-lookup"><span data-stu-id="e555e-231">Next to "This experience is designed for Windows Mixed Reality on:"</span></span>
* <span data-ttu-id="e555e-232">如果您的應用程式在沉浸式耳機連接到使用者的電腦時提供 VR 體驗，請核取 [ **電腦** ] 方塊。</span><span class="sxs-lookup"><span data-stu-id="e555e-232">Check the **PC** box if your app offers a VR experience when an immersive headset is connected to the user's PC.</span></span> <span data-ttu-id="e555e-233">建議您核取此方塊，確定您的應用程式設定為在沉浸式耳機上以獨佔方式執行，或者是標準電腦遊戲或應用程式，在耳機連線時提供混合的現真實模式或額外的內容。</span><span class="sxs-lookup"><span data-stu-id="e555e-233">We recommend checking this box whether your app is set to run exclusively on an immersive headset or if it's a standard PC game or app offering a Mixed Reality mode or bonus content when a headset is connected.</span></span>
* <span data-ttu-id="e555e-234">只有在您的應用程式在 HoloLens 上執行 **時，才** 會提供全像攝影體驗。</span><span class="sxs-lookup"><span data-stu-id="e555e-234">Check the **HoloLens** box only if your app offers a holographic experience when it's run on HoloLens.</span></span>
* <span data-ttu-id="e555e-235">如果您的應用程式在這兩種裝置類型上都提供混合現實體驗，請檢查 **這兩個** 方塊。</span><span class="sxs-lookup"><span data-stu-id="e555e-235">Check **both** boxes if your app offers a Mixed Reality experience on both device types.</span></span>

<span data-ttu-id="e555e-236">如果您選取上述的「電腦」，則您會想要將「混合現實設定」 (活動層級) 。</span><span class="sxs-lookup"><span data-stu-id="e555e-236">If you selected "PC" above, you'll want to set the "Mixed Reality setup" (activity level).</span></span> <span data-ttu-id="e555e-237">這僅適用于連接到沉浸式耳機的電腦上所執行的混合現實體驗，因為 HoloLens 上的混合現實應用程式是全球規模，而使用者在安裝期間不會定義界限。</span><span class="sxs-lookup"><span data-stu-id="e555e-237">This only applies to Mixed Reality experiences that run on PCs connected to immersive headsets, as Mixed Reality apps on HoloLens are world-scale and the user doesn't define a boundary during setup.</span></span>
* <span data-ttu-id="e555e-238">如果您將應用程式設計成讓使用者保持在一個位置，請選擇 [已 **待命 + 固定** ]。</span><span class="sxs-lookup"><span data-stu-id="e555e-238">Choose **Seated + standing** if you designed your app to have the user stay in one position.</span></span> <span data-ttu-id="e555e-239">例如，在您要控制飛機環境的遊戲中。</span><span class="sxs-lookup"><span data-stu-id="e555e-239">For example, in a game where you're in control of an aircraft cockpit.</span></span>
* <span data-ttu-id="e555e-240">如果您的應用程式是以使用者在設定期間所定義的集合界限內進行的意圖來設計，請選擇 **所有體驗** 。</span><span class="sxs-lookup"><span data-stu-id="e555e-240">Choose **All experiences** if your app is designed with the intention that the user walks around within a set boundary defined during setup.</span></span> <span data-ttu-id="e555e-241">例如，您可能會是一種遊戲，您可以在其中進行側邊和操作，以減到減的攻擊。</span><span class="sxs-lookup"><span data-stu-id="e555e-241">For example, might be a game where you side-step and duck to dodge attacks.</span></span>

### <a name="mixed-reality-system-requirements"></a><span data-ttu-id="e555e-242">混合的現實系統需求</span><span class="sxs-lookup"><span data-stu-id="e555e-242">Mixed Reality system requirements</span></span>

<span data-ttu-id="e555e-243">在應用程式提交程式的 [ **[屬性](/windows/uwp/publish/enter-app-properties)** ] 頁面上，您會在 [ **[系統需求](/windows/uwp/publish/enter-app-properties#system-requirements)** ] 區段中找到與混合現實相關的數個選項。</span><span class="sxs-lookup"><span data-stu-id="e555e-243">On the **[Properties](/windows/uwp/publish/enter-app-properties)** page of the app submission process, you'll find several options related to Mixed Reality in the **[System requirements](/windows/uwp/publish/enter-app-properties#system-requirements)** section.</span></span>

<span data-ttu-id="e555e-244">![系統需求](images/system-reqs-800px.png)</span><span class="sxs-lookup"><span data-stu-id="e555e-244">![System requirements](images/system-reqs-800px.png)</span></span><br>
<span data-ttu-id="e555e-245">系統需求</span><span class="sxs-lookup"><span data-stu-id="e555e-245">System requirements</span></span>

<span data-ttu-id="e555e-246">在本節中，您將識別) 硬體所需的最小 (，並建議您的混合現實應用程式使用 (選用) 硬體。</span><span class="sxs-lookup"><span data-stu-id="e555e-246">In this section, you'll identify minimum (required) hardware and recommended (optional) hardware for your Mixed Reality app.</span></span>

<span data-ttu-id="e555e-247">**輸入硬體：**</span><span class="sxs-lookup"><span data-stu-id="e555e-247">**Input hardware:**</span></span>

<span data-ttu-id="e555e-248">如果您的應用程式支援 [語音輸入](../design/voice-input.md)) 、 **[Xbox 控制器或遊戲台](../discover/hardware-accessories.md#bluetooth-gamepads)** 或 **[Windows Mixed Reality 運動控制器](../design/motion-controllers.md)** 的 **麥克風**，請使用核取方塊來告訴潛在客戶。</span><span class="sxs-lookup"><span data-stu-id="e555e-248">Use the checkboxes to tell potential customers if your app supports **microphone** for [voice input](../design/voice-input.md)), **[Xbox controller or gamepad](../discover/hardware-accessories.md#bluetooth-gamepads)**, or **[Windows Mixed Reality motion controllers](../design/motion-controllers.md)**.</span></span> <span data-ttu-id="e555e-249">這項資訊會顯示在您應用程式的 [產品詳細資料] 頁面上，並可協助您的應用程式包含在適當的應用程式/遊戲集合中。</span><span class="sxs-lookup"><span data-stu-id="e555e-249">This information will be surfaced on your app's product detail page in the Store and will help your app get included in the appropriate app/game collections.</span></span> <span data-ttu-id="e555e-250">例如，所有支援動作控制器的遊戲都可能會有一個集合。</span><span class="sxs-lookup"><span data-stu-id="e555e-250">For example, a collection may exist for all games that support motion controllers.</span></span>

<span data-ttu-id="e555e-251">請仔細針對輸入類型選取 [最小硬體] 或 [建議的硬體] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="e555e-251">Be thoughtful about selecting checkboxes for "minimum hardware" or "recommended hardware" for input types.</span></span> 

<span data-ttu-id="e555e-252">例如：</span><span class="sxs-lookup"><span data-stu-id="e555e-252">For example:</span></span> 
* <span data-ttu-id="e555e-253">如果您的遊戲需要移動控制器，但接受透過麥克風的語音輸入，請選取 [Windows Mixed Reality 動作控制器] 旁的 [最低硬體] 核取方塊，但在 [麥克風] 旁邊選取 [建議的硬體] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="e555e-253">If your game requires motion controllers, but accepts voice input via microphone, select the "minimum hardware" checkbox next to "Windows Mixed Reality motion controllers," but the "recommended hardware" checkbox next to "Microphone."</span></span> 
* <span data-ttu-id="e555e-254">如果您的遊戲可以使用 Xbox 控制器、遊戲台或移動控制器來播放，您可以選取 [Xbox 控制器或遊戲程式] 旁邊的 [最低硬體] 核取方塊，然後選取 [Windows Mixed Reality 動作控制器] 旁的 [建議的硬體] 核取方塊，因為動作控制器可能會在遊戲台中提供逐步解說。</span><span class="sxs-lookup"><span data-stu-id="e555e-254">If your game can be played with either an Xbox controller, gamepad, or motion controllers, you might select the "minimum hardware" checkbox next to "Xbox controller or gamepad" and select the "recommended hardware" checkbox next to "Windows Mixed Reality motion controllers" as motion controllers will likely offer a step-up in experience from the gamepad.</span></span>

<span data-ttu-id="e555e-255">**Windows Mixed Reality 沉浸式耳機：**</span><span class="sxs-lookup"><span data-stu-id="e555e-255">**Windows Mixed Reality immersive headset:**</span></span>

<span data-ttu-id="e555e-256">指出是否需要沉浸式耳機才能使用您的應用程式，或為選擇性的，對客戶滿意度和教育而言是不可或缺的。</span><span class="sxs-lookup"><span data-stu-id="e555e-256">Indicating whether an immersive headset is required to use your app, or is optional, is critical to customer satisfaction and education.</span></span>

<span data-ttu-id="e555e-257">如果您的應用 *程式只能透過* 沉浸式耳機使用，請選取 [Windows Mixed Reality 沉浸式耳機] 旁的 [最低硬體] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="e555e-257">If your app can *only* be used through an immersive headset, select the "minimum hardware" checkbox next to "Windows Mixed Reality immersive headset."</span></span> <span data-ttu-id="e555e-258">這會顯示在 [商店] 的 [產品詳細資料] 頁面上，顯示為 [購買] 按鈕上方的警告，讓客戶不想要購買可在其電腦上運作的應用程式，例如傳統的桌面應用程式。</span><span class="sxs-lookup"><span data-stu-id="e555e-258">This will be surfaced on your app's product detail page in Store as a warning above the purchase button so customers don't think they're purchasing an app that will function on their PC like a traditional desktop app.</span></span>

<span data-ttu-id="e555e-259">如果您的應用程式是在桌上型電腦上執行（例如傳統的電腦應用程式），但在沉浸式耳機連線時提供 VR 體驗 (您的應用程式的完整內容是否可用，或只有部分) ，請選取 [Windows Mixed Reality 沉浸式耳機] 旁的 [建議的硬體] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="e555e-259">If your app runs on the desktop like a traditional PC app, but offers a VR experience when an immersive headset is connected (whether the full content of your app is available, or only a portion), select the "recommended hardware" checkbox next to "Windows Mixed Reality immersive headset."</span></span> <span data-ttu-id="e555e-260">如果您的應用程式是以傳統桌面應用程式的形式運作，而未連線到沉浸式耳機，則不會在應用程式產品詳細資料頁面上的 [購買] 按鈕上方出現警告。</span><span class="sxs-lookup"><span data-stu-id="e555e-260">No warning will be surfaced above the purchase button on your app's product detail page if your app functions as a traditional desktop app without an immersive headset connected.</span></span>

<span data-ttu-id="e555e-261">**電腦規格：**</span><span class="sxs-lookup"><span data-stu-id="e555e-261">**PC specifications:**</span></span>

<span data-ttu-id="e555e-262">如果您想要讓應用程式盡可能觸及許多 Windows Mixed Reality 沉浸式耳機使用者，請以[具有整合式圖形的 Windows Mixed Reality pc](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)的電腦規格為[目標](../develop/platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md)。</span><span class="sxs-lookup"><span data-stu-id="e555e-262">If you want your app to reach as many Windows Mixed Reality immersive headset users as possible, [target](../develop/platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md) the PC specifications for [Windows Mixed Reality PCs with integrated graphics](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines).</span></span>

<span data-ttu-id="e555e-263">無論您的混合現實應用程式是否以最低 Windows Mixed Reality 電腦需求為目標，或需要特定的電腦設定，例如 [Windows Mixed Reality Ultra PC] (的專用 GPU https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines ，您應該在 [最小硬體] 資料行中新增相關的電腦規格。</span><span class="sxs-lookup"><span data-stu-id="e555e-263">Whether your Mixed Reality app targets the minimum Windows Mixed Reality PC requirements, or needs a specific PC configuration like the dedicated GPU of a [Windows Mixed Reality Ultra PC](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines, you should add the relevant PC specifications in the "minimum hardware" column.</span></span>

<span data-ttu-id="e555e-264">如果您的混合現實應用程式是針對較佳的效能所設計，或是在特定電腦設定或圖形配接器上提供更高解析度的圖形，您應該在 [建議的硬體] 資料行中包含相關的電腦規格。</span><span class="sxs-lookup"><span data-stu-id="e555e-264">If your Mixed Reality app is designed for better performance or offers higher-resolution graphics on a particular PC configuration or graphics card, you should include the relevant PC specifications in the "recommended hardware" column.</span></span>

<span data-ttu-id="e555e-265">只有當您的混合現實應用程式使用連接到電腦的沉浸式耳機時，才適用這種情況。</span><span class="sxs-lookup"><span data-stu-id="e555e-265">This only applies if your Mixed Reality app uses an immersive headset connected to a PC.</span></span> <span data-ttu-id="e555e-266">如果您的混合現實應用程式只在 HoloLens 上執行，您不需要指出電腦規格，因為 HoloLens 只有一個硬體設定。</span><span class="sxs-lookup"><span data-stu-id="e555e-266">If your Mixed Reality app only runs on HoloLens, you won't need to indicate PC specifications as HoloLens has only one hardware configuration.</span></span>

### <a name="device-family-availability"></a><span data-ttu-id="e555e-267">裝置系列可用性</span><span class="sxs-lookup"><span data-stu-id="e555e-267">Device family availability</span></span>

<span data-ttu-id="e555e-268">如果您已在 Visual Studio 中 [正確封裝您的應用程式](https://docs.microsoft.com/windows/uwp/publish/app-package-requirements) ，則在 [套件] 頁面上傳它時，應該會產生具有可用裝置系列的資料表。</span><span class="sxs-lookup"><span data-stu-id="e555e-268">If you've [packaged your app correctly](https://docs.microsoft.com/windows/uwp/publish/app-package-requirements) in Visual Studio, uploading it on the Packages page should produce a table with the available device families.</span></span>

<span data-ttu-id="e555e-269">![裝置系列可用性資料表](images/device-family-table-900px.png)</span><span class="sxs-lookup"><span data-stu-id="e555e-269">![Device family availability table](images/device-family-table-900px.png)</span></span><br>
<span data-ttu-id="e555e-270">裝置系列可用性資料表</span><span class="sxs-lookup"><span data-stu-id="e555e-270">Device family availability table</span></span>

<span data-ttu-id="e555e-271">如果您的混合現實應用程式適用于沉浸式耳機，則至少應該在資料表中選取 [Windows 10 桌面]。</span><span class="sxs-lookup"><span data-stu-id="e555e-271">If your Mixed Reality app works on immersive headsets, then at least "Windows 10 Desktop" should be selected in the table.</span></span> <span data-ttu-id="e555e-272">如果您的混合現實應用程式可在 HoloLens 上運作，則至少應選取 [Windows 10 全像攝影版]。</span><span class="sxs-lookup"><span data-stu-id="e555e-272">If your Mixed Reality app works on HoloLens, then at least "Windows 10 Holographic" should be selected.</span></span> <span data-ttu-id="e555e-273">如果您的應用程式同時在兩個 Windows Mixed Reality 耳機類型上執行，則應該選取 [Windows 10 桌面] 和 [Windows 10 全像攝影版]。</span><span class="sxs-lookup"><span data-stu-id="e555e-273">If your app runs on both Windows Mixed Reality headset types, both "Windows 10 Desktop" and "Windows 10 Holographic" should be selected.</span></span>

>[!TIP]
><span data-ttu-id="e555e-274">許多開發人員在上傳其應用程式套件與套件資訊清單和您在合作夥伴中心中的應用程式/發行者帳戶資訊相關的套件時，會遇到錯誤。</span><span class="sxs-lookup"><span data-stu-id="e555e-274">Many developers run into errors when uploading their app's package related to mismatches between the package manifest and your app/publisher account information in Partner Center.</span></span> <span data-ttu-id="e555e-275">使用與您的 Windows 開發人員帳戶相關聯的相同帳戶登入 Visual Studio，通常可以避免這些錯誤， (用來登入合作夥伴中心) 的帳戶。</span><span class="sxs-lookup"><span data-stu-id="e555e-275">These errors can often be avoided by signing into Visual Studio with the same account associated with your Windows developer account (the one you use to sign into Partner Center).</span></span> <span data-ttu-id="e555e-276">如果您使用相同的帳戶，您將能夠在封裝應用程式之前，先將應用程式與其在 Microsoft Store 中的身分識別建立關聯。</span><span class="sxs-lookup"><span data-stu-id="e555e-276">If you use the same account, you'll be able to associate your app with its identity in the Microsoft Store before you package it.</span></span>

<span data-ttu-id="e555e-277">![將您的應用程式與 Microsoft Store 建立關聯](images/associate-your-app-700px.png)</span><span class="sxs-lookup"><span data-stu-id="e555e-277">![Associate your app with the Microsoft Store](images/associate-your-app-700px.png)</span></span><br>
<span data-ttu-id="e555e-278">將您的應用程式與 Visual Studio 中的 Microsoft Store 建立關聯</span><span class="sxs-lookup"><span data-stu-id="e555e-278">Associate your app with the Microsoft Store in Visual Studio</span></span>

### <a name="store-listing-page"></a><span data-ttu-id="e555e-279">Store 清單頁面</span><span class="sxs-lookup"><span data-stu-id="e555e-279">Store listing page</span></span>

<span data-ttu-id="e555e-280">在應用程式提交程式的 [ [Store 清單](/windows/uwp/publish/create-app-store-listings) ] 頁面上，有幾個地方可新增您混合現實應用程式的實用資訊。</span><span class="sxs-lookup"><span data-stu-id="e555e-280">On the [Store listing](/windows/uwp/publish/create-app-store-listings) page of the app submission process, there are several places you can add useful information about your Mixed Reality app.</span></span>

>[!IMPORTANT]
><span data-ttu-id="e555e-281">為了確保您的應用程式已由商店正確分類，並可供 Windows Mixed Reality 客戶使用，您應該新增 **"Windows Mixed Reality"** 作為應用程式的其中一個「搜尋詞彙」 (您可以展開 [共用欄位] 區段) 來尋找搜尋字詞。</span><span class="sxs-lookup"><span data-stu-id="e555e-281">To ensure your app is correctly categorized by the Store and made discoverable to Windows Mixed Reality customers, you should add **"Windows Mixed Reality"** as one of your "Search terms" for the app (you can find search terms by expanding the "Shared fields" section).</span></span>

<span data-ttu-id="e555e-282">![將 Windows Mixed Reality 新增至搜尋詞彙](images/search-terms-800px.png)</span><span class="sxs-lookup"><span data-stu-id="e555e-282">![Add Windows Mixed Reality to search terms](images/search-terms-800px.png)</span></span><br>
<span data-ttu-id="e555e-283">將 "Windows Mixed Reality" 新增至搜尋詞彙</span><span class="sxs-lookup"><span data-stu-id="e555e-283">Add "Windows Mixed Reality" to search terms</span></span>

## <a name="offering-a-free-trial-for-your-game-or-app"></a><span data-ttu-id="e555e-284">為您的遊戲或應用程式提供免費試用</span><span class="sxs-lookup"><span data-stu-id="e555e-284">Offering a free trial for your game or app</span></span>

<span data-ttu-id="e555e-285">在許多情況下，您的取用者在購買 Windows Mixed Reality 的沉浸式耳機之前，將會受到限制，不會有虛擬實境的體驗。</span><span class="sxs-lookup"><span data-stu-id="e555e-285">In many cases, your consumers will have limited to no experience with virtual reality before they buy a Windows Mixed Reality immersive headset.</span></span> <span data-ttu-id="e555e-286">他們可能不知道要從密集遊戲的期望，或是想要在沉浸式體驗中熟悉他們自己的緩和閾值。</span><span class="sxs-lookup"><span data-stu-id="e555e-286">They may not know what to expect from intense games or be familiar with their own comfort threshold in immersive experiences.</span></span> <span data-ttu-id="e555e-287">許多客戶也可以嘗試在未徽章為 [Windows Mixed Reality 電腦](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)的電腦上 Windows Mixed Reality 沉浸式耳機。</span><span class="sxs-lookup"><span data-stu-id="e555e-287">Many customers may also try a Windows Mixed Reality immersive headset on PCs that aren't badged as [Windows Mixed Reality PCs](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines).</span></span> <span data-ttu-id="e555e-288">基於這些考慮，強烈建議您考慮為您的付費混合現實應用程式或遊戲提供 [免費試用](/windows/uwp/publish/set-app-pricing-and-availability#free-trial) 。</span><span class="sxs-lookup"><span data-stu-id="e555e-288">Because of these considerations, we strongly recommend you consider offering a [free trial](/windows/uwp/publish/set-app-pricing-and-availability#free-trial) for your paid Mixed Reality app or game.</span></span>

## <a name="see-also"></a><span data-ttu-id="e555e-289">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e555e-289">See also</span></span>
* [<span data-ttu-id="e555e-290">什麼是混合實境？</span><span class="sxs-lookup"><span data-stu-id="e555e-290">What is Mixed Reality?</span></span>](../discover/mixed-reality.md)
* [<span data-ttu-id="e555e-291">開發概觀</span><span class="sxs-lookup"><span data-stu-id="e555e-291">Development overview</span></span>](../develop/development.md)
* [<span data-ttu-id="e555e-292">應用程式檢視</span><span class="sxs-lookup"><span data-stu-id="e555e-292">App views</span></span>](../design/app-views.md)
* [<span data-ttu-id="e555e-293">瞭解混合現實的效能</span><span class="sxs-lookup"><span data-stu-id="e555e-293">Understanding Performance for Mixed Reality</span></span>](../develop/platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md)
* [<span data-ttu-id="e555e-294">Unity 的效能建議</span><span class="sxs-lookup"><span data-stu-id="e555e-294">Performance Recommendations for Unity</span></span>](../develop/unity/performance-recommendations-for-unity.md)
* [<span data-ttu-id="e555e-295">測試 HoloLens 上的應用程式</span><span class="sxs-lookup"><span data-stu-id="e555e-295">Testing your app on HoloLens</span></span>](../develop/platform-capabilities-and-apis/testing-your-app-on-hololens.md)
* [<span data-ttu-id="e555e-296">Windows Mixed Reality 最小電腦硬體相容性指導方針</span><span class="sxs-lookup"><span data-stu-id="e555e-296">Windows Mixed Reality minimum PC hardware compatibility guidelines</span></span>](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)