---
title: 發佈至 Microsoft Store
description: 了解如何封裝、認證 Unreal 混合實境應用程式，以及將這些應用程式發佈到 Microsoft Store。
author: hferrone
ms.author: jacksonf
ms.date: 12/3/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 混合實境, 開發, 文件, 指南, 功能, 混合實境頭戴式裝置, windows 混合實境頭戴式裝置, 虛擬實境頭戴式裝置, 發佈, 散發, Microsoft Store
ms.openlocfilehash: 41f081f11cdb9ac2fdf96a81bb761a1321d1776f
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2021
ms.locfileid: "98010018"
---
# <a name="publishing-to-the-microsoft-store"></a><span data-ttu-id="dd4d4-104">發佈至 Microsoft Store</span><span class="sxs-lookup"><span data-stu-id="dd4d4-104">Publishing to the Microsoft Store</span></span>

<span data-ttu-id="dd4d4-105">當您準備好要對外發佈您的 Unreal 應用程式時，在提交至 Microsoft Store 之前，必須先更新幾項專案設定。</span><span class="sxs-lookup"><span data-stu-id="dd4d4-105">When you're ready to get your Unreal app out to the world, there are a few project settings that need updating before you submit to the Microsoft Store.</span></span> <span data-ttu-id="dd4d4-106">這些設定全都有預設值，但應針對生產環境加以變更，讓應用程式獲得最佳展現。</span><span class="sxs-lookup"><span data-stu-id="dd4d4-106">All of these settings have default values, but should be changed for production to best represent the application.</span></span>

## <a name="project-settings-for-the-store-packaging"></a><span data-ttu-id="dd4d4-107">市集封裝的專案設定</span><span class="sxs-lookup"><span data-stu-id="dd4d4-107">Project settings for the store packaging</span></span>

1. <span data-ttu-id="dd4d4-108">首先，選取 [專案設定] > [說明]，並更新遊戲和發行者資訊：</span><span class="sxs-lookup"><span data-stu-id="dd4d4-108">First, select **Project Settings > Description** and update the game and publisher information:</span></span> 
    * <span data-ttu-id="dd4d4-109">[遊戲名稱] 會出現在 HoloLens 上的應用程式磚中</span><span class="sxs-lookup"><span data-stu-id="dd4d4-109">The **Game Name** will appear in the app tile on the HoloLens</span></span>
    * <span data-ttu-id="dd4d4-110">產生專案憑證時會使用 [公司辨別名稱]，而其格式應為：</span><span class="sxs-lookup"><span data-stu-id="dd4d4-110">The **Company Distinguished Name** is used when generating the project certificate and should be in the format:</span></span> 
        * <span data-ttu-id="dd4d4-111">**CN=CommonName, O=OrganizationName, L=LocalityName, S=StateOrProvinceName, C=CountryName**：</span><span class="sxs-lookup"><span data-stu-id="dd4d4-111">**CN=CommonName, O=OrganizationName, L=LocalityName, S=StateOrProvinceName, C=CountryName**:</span></span>

![Unreal 編輯器的螢幕擷取畫面，其中已展開專案設定中的 [說明] 區段](images/unreal-publishing-img-01.png)

2. <span data-ttu-id="dd4d4-113">展開專案設定的 [HoloLens] 區段，並更新封裝資源。</span><span class="sxs-lookup"><span data-stu-id="dd4d4-113">Expand the **HoloLens** section of the project settings and update the packaging resources.</span></span>  <span data-ttu-id="dd4d4-114">應用程式的市集頁面上會顯示下列資源名稱：</span><span class="sxs-lookup"><span data-stu-id="dd4d4-114">These resource names will be shown on the application’s store page:</span></span>

![Unreal 編輯器的螢幕擷取畫面，其中已展開專案設定中的 [封裝] 區段](images/unreal-publishing-img-02.png)

3. <span data-ttu-id="dd4d4-116">展開 [影像] 區段，並以顯示商店應用程式的材質來更新預設市集影像。</span><span class="sxs-lookup"><span data-stu-id="dd4d4-116">Expand the **Images** section and update the default store images with textures that represent the store app.</span></span>  <span data-ttu-id="dd4d4-117">選擇性地選取 [3D 標誌] 核取方塊，以上傳在啟動應用程式時作為 3D 即時立方體的 glb 檔案：</span><span class="sxs-lookup"><span data-stu-id="dd4d4-117">Optionally, select the **3D Logo** checkbox to upload a glb file to use as a 3D live cube when launching the application:</span></span>

![Unreal 編輯器的螢幕擷取畫面，其中已展開專案設定中的 [影像] 區段](images/unreal-publishing-img-03.png)

4. <span data-ttu-id="dd4d4-119">最後，選取 [產生新的]，以從專案名稱和公司辨別名稱產生簽署憑證</span><span class="sxs-lookup"><span data-stu-id="dd4d4-119">Lastly, select **Generate New** to generate a signing certificate from the project name and company distinguished name</span></span>  
    * <span data-ttu-id="dd4d4-120">設定 [磚背景色彩]，此色彩會顯示在商店影像中任何透明像素的位置上。</span><span class="sxs-lookup"><span data-stu-id="dd4d4-120">Set a **Tile Background Color**, which will appear in place of any transparent pixels in the store images.</span></span>
    * <span data-ttu-id="dd4d4-121">展開下拉式清單，並啟用 [使用零售 Windows Store 環境]，使其在零售鎖定 (而非開發解除鎖定) 的裝置上執行。</span><span class="sxs-lookup"><span data-stu-id="dd4d4-121">Expand the dropdown and enable **Use Retail Windows Store Environment** to run on retail-locked, not dev-unlocked, devices.</span></span>

![Unreal 編輯器的螢幕擷取畫面，其中已展開專案設定中的 [憑證產生] 區段](images/unreal-publishing-img-04.png)

## <a name="optional-app-installer"></a><span data-ttu-id="dd4d4-123">選用應用程式安裝</span><span class="sxs-lookup"><span data-stu-id="dd4d4-123">Optional App Installer</span></span>

<span data-ttu-id="dd4d4-124">您可以從 [專案設定] > [HoloLens] 建立應用程式安裝程式檔案，用來在市集以外散發應用程式。</span><span class="sxs-lookup"><span data-stu-id="dd4d4-124">An App Installer file can be created from **Project Settings > HoloLens**, which can be used to distribute the application outside of the store.</span></span>  <span data-ttu-id="dd4d4-125">啟用 [應建立應用程式安裝程式] 核取方塊，並設定要用來儲存遊戲 appxbundle 的 URL 或網路路徑。</span><span class="sxs-lookup"><span data-stu-id="dd4d4-125">Enable the **Should Create App Installer** checkbox and set a URL or network path where you'd like the game’s appxbundle to be stored.</span></span>  

![Unreal 編輯器的螢幕擷取畫面，其中已展開專案設定中的 [應用程式安裝程式] 區段](images/unreal-publishing-img-05.png)

<span data-ttu-id="dd4d4-127">封裝應用程式時，將會產生 appxbundle 和 appinstaller。</span><span class="sxs-lookup"><span data-stu-id="dd4d4-127">When the app is being packaged, both the appxbundle and appinstaller will be generated.</span></span>  <span data-ttu-id="dd4d4-128">將 appxbundle 上傳至安裝 URL，然後啟動 appinstaller 以從網路位置安裝應用程式。</span><span class="sxs-lookup"><span data-stu-id="dd4d4-128">Upload the appxbundle to the installation URL, then launch the appinstaller to install the app from the network location.</span></span>

## <a name="windows-app-certification-kit"></a><span data-ttu-id="dd4d4-129">Windows 應用程式認證套件</span><span class="sxs-lookup"><span data-stu-id="dd4d4-129">Windows App Certification Kit</span></span>

<span data-ttu-id="dd4d4-130">Windows 10 SDK 隨附 Windows 應用程式認證套件 (WACK)，用以驗證可能影響到套件上傳至市集的常見問題。</span><span class="sxs-lookup"><span data-stu-id="dd4d4-130">The Windows 10 SDK ships with the Windows App Certification Kit (WACK) to validate common issues that could affect uploading a package to the store.</span></span>  <span data-ttu-id="dd4d4-131">您可以在 Windows Kits 目錄中找到 WACK，通常位於下列路徑下：</span><span class="sxs-lookup"><span data-stu-id="dd4d4-131">You can find the WACK in the Windows Kits directory, usually under the following path:</span></span> 

```
C:\Program Files (x86)\Windows Kits\10\App Certification Kit.
```

1. <span data-ttu-id="dd4d4-132">將 appx 檔案封裝以供發佈後，請執行 **appcertui.exe**，並依照提示對 appx 進行掃描：</span><span class="sxs-lookup"><span data-stu-id="dd4d4-132">After your appx file is packaged for publication, run **appcertui.exe** and follow the prompts to scan the appx:</span></span>

![此螢幕擷取畫面顯示 Windows 應用程式認證套件中經選取要驗證的應用程式](images/unreal-publishing-img-06.png)

2. <span data-ttu-id="dd4d4-134">選取 [驗證市集應用程式]：</span><span class="sxs-lookup"><span data-stu-id="dd4d4-134">Select **Validate Store App**:</span></span>

![在 Windows 應用程式認證套件中選取驗證項目的螢幕擷取畫面](images/unreal-publishing-img-07.png)

3. <span data-ttu-id="dd4d4-136">瀏覽頂端區段中的 appx，然後選取 [下一步]：</span><span class="sxs-lookup"><span data-stu-id="dd4d4-136">Browse for the appx in the top section and select **Next**:</span></span>

![在 Windows 應用程式認證套件中選取測試項目的螢幕擷取畫面](images/unreal-publishing-img-08.png)

4. <span data-ttu-id="dd4d4-138">選取 [下一步] 以執行測試並建立報表：</span><span class="sxs-lookup"><span data-stu-id="dd4d4-138">Select **Next** to run the tests and create a report:</span></span>
    * <span data-ttu-id="dd4d4-139">依預設會啟用可在主機電腦上執行的所有測試</span><span class="sxs-lookup"><span data-stu-id="dd4d4-139">All available tests that can be run on the host PC will be enabled by default</span></span>

![Windows 應用程式認證套件中的應用程式驗證進度的螢幕擷取畫面](images/unreal-publishing-img-09.png)

5. <span data-ttu-id="dd4d4-141">等候測試完成。</span><span class="sxs-lookup"><span data-stu-id="dd4d4-141">Wait for the tests to finish.</span></span> <span data-ttu-id="dd4d4-142">完成後，最後一個視窗會顯示通過或失敗的結果，您可以在儲存的報表中檢視該結果。</span><span class="sxs-lookup"><span data-stu-id="dd4d4-142">Once complete, the final window will show a pass or fail result, which can be viewed in the saved report.</span></span>

![Windows 應用程式認證套件中的最終報表結果的螢幕擷取畫面](images/unreal-publishing-img-10.png)

## <a name="known-wack-failure-with-425"></a><span data-ttu-id="dd4d4-144">4\.25 的已知 WACK 失敗</span><span class="sxs-lookup"><span data-stu-id="dd4d4-144">Known WACK failure with 4.25</span></span>

<span data-ttu-id="dd4d4-145">Unreal 4.25 中的 Windows Mixed Reality 外掛程式將無法通過 WACK，因為在封裝 HoloLens 時，其中包含了一些 x64 二進位檔。</span><span class="sxs-lookup"><span data-stu-id="dd4d4-145">The Windows Mixed Reality plugin in Unreal 4.25 will fail WACK because some x64 binaries are included while packaging for HoloLens.</span></span> <span data-ttu-id="dd4d4-146">失敗的情形顯示如下：</span><span class="sxs-lookup"><span data-stu-id="dd4d4-146">The failure will look like this:</span></span>

![在 Windows 應用程式認證套件中，由於二進位分析器和支援的 API 而導致失敗結果的螢幕擷取畫面](images/unreal-publishing-img-11.png)

<span data-ttu-id="dd4d4-148">若要修正此問題：</span><span class="sxs-lookup"><span data-stu-id="dd4d4-148">To fix the issue:</span></span>
1. <span data-ttu-id="dd4d4-149">開啟 Unreal 專案，以瀏覽至 Unreal 安裝或來源目錄的根目錄，並以滑鼠右鍵按一下工作列中的 Unreal 圖示。</span><span class="sxs-lookup"><span data-stu-id="dd4d4-149">Browse to the Unreal installation or source directory root by opening an Unreal project and right-click on the Unreal icon in the taskbar.</span></span>
2. <span data-ttu-id="dd4d4-150">以滑鼠右鍵按一下 UE4Editor，選取 [屬性]，然後瀏覽至 [位置] 項目中的路徑：</span><span class="sxs-lookup"><span data-stu-id="dd4d4-150">Right-click on UE4Editor, select properties, and browse to the path in the **Location** entry:</span></span>

```
Open Engine\Plugins\Runtime\WindowsMixedReality\Source\WindowsMixedRealityHMD\WindowsMixedRealityHMD.Build.cs.
```

3. <span data-ttu-id="dd4d4-151">在 **WindowsMixedRealityHMD.Build.cs** 中，將 **第 32行** 從：</span><span class="sxs-lookup"><span data-stu-id="dd4d4-151">In **WindowsMixedRealityHMD.Build.cs**, modify **line 32** from:</span></span>

```cpp
if(Target.Platform != UnrealTargetPlatform.Win32)
```

<span data-ttu-id="dd4d4-152">變更為：</span><span class="sxs-lookup"><span data-stu-id="dd4d4-152">to:</span></span>

```cpp
if(Target.Platform == UnrealTargetPlatform.Win64)

```

4. <span data-ttu-id="dd4d4-153">關閉 Unreal、重新開啟專案，然後重新封裝 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="dd4d4-153">Close Unreal, reopen the project, and repackage for HoloLens.</span></span>  <span data-ttu-id="dd4d4-154">重新執行 WACK，此錯誤就會消失。</span><span class="sxs-lookup"><span data-stu-id="dd4d4-154">Rerun WACK and the error will be gone.</span></span> 

## <a name="see-also"></a><span data-ttu-id="dd4d4-155">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dd4d4-155">See also</span></span>

* [<span data-ttu-id="dd4d4-156">將應用程式提交到 Microsoft Store</span><span class="sxs-lookup"><span data-stu-id="dd4d4-156">Submitting an app to the Microsoft Store</span></span>](../../distribute/submitting-an-app-to-the-microsoft-store.md)
* [<span data-ttu-id="dd4d4-157">Windows 應用程式認證套件</span><span class="sxs-lookup"><span data-stu-id="dd4d4-157">Windows App Certification Kit</span></span>](https://developer.microsoft.com/windows/downloads/app-certification-kit)
* [<span data-ttu-id="dd4d4-158">手動建立應用程式安裝程式檔案</span><span class="sxs-lookup"><span data-stu-id="dd4d4-158">Create an App Installer file manually</span></span>](https://docs.microsoft.com/windows/msix/app-installer/how-to-create-appinstaller-file)