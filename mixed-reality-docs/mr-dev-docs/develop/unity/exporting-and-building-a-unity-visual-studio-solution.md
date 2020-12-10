---
title: 匯出和建置 Unity Visual Studio 解決方案
description: 本文概述如何從 Unity 匯出您的混合現實專案，讓您可以在 Visual Studio 中建立和部署。
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: unity、visual studio、匯出、組建、部署、HoloLens、混合現實耳機、windows mixed reality 耳機、虛擬實境耳機、UWP、部署
ms.openlocfilehash: 4da20a30375c7204c532a19c129c9265c0fa27d9
ms.sourcegitcommit: 87b54c75044f433cfadda68ca71c1165608e2f4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "97010409"
---
# <a name="exporting-and-building-a-unity-visual-studio-solution"></a><span data-ttu-id="3fba8-104">匯出和建置 Unity Visual Studio 解決方案</span><span class="sxs-lookup"><span data-stu-id="3fba8-104">Exporting and building a Unity Visual Studio solution</span></span>

<span data-ttu-id="3fba8-105">如果您的應用程式不需要系統鍵盤，我們的建議是使用 *D3D* ，讓您的應用程式使用較少的記憶體，並縮短啟動時間。</span><span class="sxs-lookup"><span data-stu-id="3fba8-105">If your app doesn't need the system keyboard, our recommendation is to use *D3D* so that your app uses slightly less memory and a faster launch time.</span></span> <span data-ttu-id="3fba8-106">不過，如果您是透過 TouchScreenKeyboard API 使用系統鍵盤，您需要將專案匯出為 *XAML*。</span><span class="sxs-lookup"><span data-stu-id="3fba8-106">However, if you're using the system keyboard through the TouchScreenKeyboard API, you need to export the project as *XAML*.</span></span>

## <a name="how-to-export-from-unity"></a><span data-ttu-id="3fba8-107">如何從 Unity 匯出</span><span class="sxs-lookup"><span data-stu-id="3fba8-107">How to export from Unity</span></span>

<span data-ttu-id="3fba8-108">![Unity 組建設定](images/unitybuildsettings-300px.png)</span><span class="sxs-lookup"><span data-stu-id="3fba8-108">![Unity build settings](images/unitybuildsettings-300px.png)</span></span><br>
<span data-ttu-id="3fba8-109">*Unity 編輯器中的組建設定*</span><span class="sxs-lookup"><span data-stu-id="3fba8-109">*Build settings in Unity editor*</span></span>

1. <span data-ttu-id="3fba8-110">當您準備好從 Unity 匯出專案時，請 **開啟 [檔案**] 功能表，然後選取 [**組建設定 ...** ]。</span><span class="sxs-lookup"><span data-stu-id="3fba8-110">When you're ready to export your project from Unity, open the **File** menu and select **Build Settings...**</span></span>
2. <span data-ttu-id="3fba8-111">選取 [ **新增開啟的場景** ]，將您的場景新增至組建。</span><span class="sxs-lookup"><span data-stu-id="3fba8-111">Select **Add Open Scenes** to add your scene to the build.</span></span>
3. <span data-ttu-id="3fba8-112">在 [ **組建設定** ] 對話方塊中，選擇下列選項以匯出 HoloLens：</span><span class="sxs-lookup"><span data-stu-id="3fba8-112">In the **Build Settings** dialog, choose the following options to export for HoloLens:</span></span>
   * <span data-ttu-id="3fba8-113">**平臺：** *通用 Windows 平臺* 並務必選取 [ **切換平臺** ]，讓您的選擇生效。</span><span class="sxs-lookup"><span data-stu-id="3fba8-113">**Platform:** *Universal Windows Platform* and be sure to select **Switch Platform** for your selection to take effect.</span></span>
   * <span data-ttu-id="3fba8-114">**SDK：** *通用 10*。</span><span class="sxs-lookup"><span data-stu-id="3fba8-114">**SDK:** *Universal 10*.</span></span>
   * <span data-ttu-id="3fba8-115">**UWP 組建類型：** *D3D*。</span><span class="sxs-lookup"><span data-stu-id="3fba8-115">**UWP Build Type:** *D3D*.</span></span>
4. <span data-ttu-id="3fba8-116">**選用**： **Unity c # 專案：** 已核取。</span><span class="sxs-lookup"><span data-stu-id="3fba8-116">**Optional**: **Unity C# Projects:** Checked.</span></span>

>[!NOTE]
><span data-ttu-id="3fba8-117">勾選此方塊可讓您：</span><span class="sxs-lookup"><span data-stu-id="3fba8-117">Checking this box allows you to:</span></span>
>* <span data-ttu-id="3fba8-118">在 Visual Studio 遠端偵錯程式中，為您的應用程式進行偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="3fba8-118">Debug your app in the Visual Studio remote debugger.</span></span>
>* <span data-ttu-id="3fba8-119">使用 IntelliSense 進行 WinRT Api 時，請編輯 Unity c # 專案中的腳本。</span><span class="sxs-lookup"><span data-stu-id="3fba8-119">Edit scripts in the Unity C# project while using IntelliSense for WinRT APIs.</span></span>

5. <span data-ttu-id="3fba8-120">從 [**組建設定 ...** ] 視窗中，開啟 [**播放玩家設定**]。</span><span class="sxs-lookup"><span data-stu-id="3fba8-120">From the **Build Settings...** window, open **Player Settings...**</span></span>
6. <span data-ttu-id="3fba8-121">選取 [ **通用 Windows 平臺** ] 索引標籤的設定。</span><span class="sxs-lookup"><span data-stu-id="3fba8-121">Select the **Settings for Universal Windows Platform** tab.</span></span>
7. <span data-ttu-id="3fba8-122">展開 [XR 設定] 群組。</span><span class="sxs-lookup"><span data-stu-id="3fba8-122">Expand the **XR Settings** group.</span></span>
8. <span data-ttu-id="3fba8-123">在 [ **XR 設定** ] 區段中，核取 [ **支援虛擬事實** ] 核取方塊以新增 **虛擬實境裝置** 清單，並確認 **[Windows Mixed Reality]** 列為支援的裝置。</span><span class="sxs-lookup"><span data-stu-id="3fba8-123">In the **XR Settings** section, check the **Virtual Reality Supported** checkbox to add a new **Virtual Reality Devices** list and confirm **"Windows Mixed Reality"** is listed as a supported device.</span></span>
9. <span data-ttu-id="3fba8-124">返回 [ **組建設定** ] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="3fba8-124">Return to the **Build Settings** dialog.</span></span>
10. <span data-ttu-id="3fba8-125">選取 [組建]  。</span><span class="sxs-lookup"><span data-stu-id="3fba8-125">Select **Build**.</span></span>
11. <span data-ttu-id="3fba8-126">在出現的 [Windows 檔案總管] 對話方塊中，建立新的資料夾來保存 Unity 的組建輸出。</span><span class="sxs-lookup"><span data-stu-id="3fba8-126">In the Windows Explorer dialog that appears, create a new folder to hold Unity's build output.</span></span> <span data-ttu-id="3fba8-127">一般來說，我們會將資料夾命名為 "App"。</span><span class="sxs-lookup"><span data-stu-id="3fba8-127">Generally, we name the folder "App".</span></span>
12. <span data-ttu-id="3fba8-128">選取新建立的資料夾，然後選取 [ **選取資料夾**]。</span><span class="sxs-lookup"><span data-stu-id="3fba8-128">Select the newly created folder and select **Select Folder**.</span></span>
13. <span data-ttu-id="3fba8-129">Unity 完成建立之後，會開啟專案根目錄的 Windows 檔案總管視窗。</span><span class="sxs-lookup"><span data-stu-id="3fba8-129">Once Unity has finished building, a Windows Explorer window will open to the project root directory.</span></span> <span data-ttu-id="3fba8-130">流覽至新建立的資料夾。</span><span class="sxs-lookup"><span data-stu-id="3fba8-130">Navigate into the newly created folder.</span></span>
14. <span data-ttu-id="3fba8-131">開啟位於此資料夾內產生的 Visual Studio 方案檔。</span><span class="sxs-lookup"><span data-stu-id="3fba8-131">Open the generated Visual Studio solution file located inside this folder.</span></span>

## <a name="when-to-re-export-from-unity"></a><span data-ttu-id="3fba8-132">從 Unity 重新匯出的時機</span><span class="sxs-lookup"><span data-stu-id="3fba8-132">When to re-export from Unity</span></span>

<span data-ttu-id="3fba8-133">從 Unity 匯出您的應用程式時，檢查 **c # 專案** 核取方塊會建立包含所有 Unity 腳本檔案的 Visual Studio 解決方案。</span><span class="sxs-lookup"><span data-stu-id="3fba8-133">Checking the **C# Projects** checkbox when exporting your app from Unity creates a Visual Studio solution that includes all your Unity script files.</span></span> <span data-ttu-id="3fba8-134">將您的所有腳本都放在一個位置，可讓您逐一查看，而不需要從 Unity 重新匯出。</span><span class="sxs-lookup"><span data-stu-id="3fba8-134">Having all your scripts in one place lets you iterate without re-exporting from Unity.</span></span> <span data-ttu-id="3fba8-135">但是，如果您對專案進行變更，而不只是變更腳本的內容，您必須從 Unity 重新匯出。</span><span class="sxs-lookup"><span data-stu-id="3fba8-135">However, if you make changes to your project that aren't just changing the contents of scripts, you'll need to re-export from Unity.</span></span> <span data-ttu-id="3fba8-136">您需要從 Unity 重新匯出的一些時間範例如下：</span><span class="sxs-lookup"><span data-stu-id="3fba8-136">Some examples of times you need to re-export from Unity are:</span></span>
* <span data-ttu-id="3fba8-137">您可以在 [專案] 索引標籤中新增或移除資產。</span><span class="sxs-lookup"><span data-stu-id="3fba8-137">You add or remove assets in the Project tab.</span></span>
* <span data-ttu-id="3fba8-138">您可以在 [偵測器] 索引標籤中變更任何值。</span><span class="sxs-lookup"><span data-stu-id="3fba8-138">You change any value in the Inspector tab.</span></span>
* <span data-ttu-id="3fba8-139">您可以從 [階層] 索引標籤新增或移除物件。</span><span class="sxs-lookup"><span data-stu-id="3fba8-139">You add or remove objects from the Hierarchy tab.</span></span>
* <span data-ttu-id="3fba8-140">您變更任何 Unity 專案設定</span><span class="sxs-lookup"><span data-stu-id="3fba8-140">You change any Unity project settings</span></span>

## <a name="building-and-deploying-a-unity-visual-studio-solution"></a><span data-ttu-id="3fba8-141">建立及部署 Unity Visual Studio 解決方案</span><span class="sxs-lookup"><span data-stu-id="3fba8-141">Building and deploying a Unity Visual Studio solution</span></span>

<span data-ttu-id="3fba8-142">建立和部署應用程式的其餘部分會在 [Visual Studio](../platform-capabilities-and-apis/using-visual-studio.md)中進行。</span><span class="sxs-lookup"><span data-stu-id="3fba8-142">The remainder of building and deploying apps happens in [Visual Studio](../platform-capabilities-and-apis/using-visual-studio.md).</span></span> <span data-ttu-id="3fba8-143">您將需要指定 Unity 組建設定。</span><span class="sxs-lookup"><span data-stu-id="3fba8-143">You will need to specify a Unity build configuration.</span></span> <span data-ttu-id="3fba8-144">Unity 的命名慣例可能與您在 Visual Studio 中使用的不同：</span><span class="sxs-lookup"><span data-stu-id="3fba8-144">Unity's naming conventions may differ from what you're used to in Visual Studio:</span></span>

|  <span data-ttu-id="3fba8-145">組態</span><span class="sxs-lookup"><span data-stu-id="3fba8-145">Configuration</span></span>  |  <span data-ttu-id="3fba8-146">說明</span><span class="sxs-lookup"><span data-stu-id="3fba8-146">Explanation</span></span> | 
|----------|----------|
|  <span data-ttu-id="3fba8-147">偵錯</span><span class="sxs-lookup"><span data-stu-id="3fba8-147">Debug</span></span>  |  <span data-ttu-id="3fba8-148">關閉所有優化，並啟用分析工具。</span><span class="sxs-lookup"><span data-stu-id="3fba8-148">All optimizations off and the profiler is enabled.</span></span> <span data-ttu-id="3fba8-149">用來對腳本進行調試。</span><span class="sxs-lookup"><span data-stu-id="3fba8-149">Used to debug scripts.</span></span> | 
|  <span data-ttu-id="3fba8-150">Master</span><span class="sxs-lookup"><span data-stu-id="3fba8-150">Master</span></span>  |  <span data-ttu-id="3fba8-151">所有優化都會開啟，並停用分析工具。</span><span class="sxs-lookup"><span data-stu-id="3fba8-151">All optimizations are turned on and the profiler is disabled.</span></span> <span data-ttu-id="3fba8-152">用來將應用程式提交到存放區。</span><span class="sxs-lookup"><span data-stu-id="3fba8-152">Used to submit apps to the Store.</span></span> | 
|  <span data-ttu-id="3fba8-153">版本</span><span class="sxs-lookup"><span data-stu-id="3fba8-153">Release</span></span>  |  <span data-ttu-id="3fba8-154">所有優化都已開啟，並且已啟用分析工具。</span><span class="sxs-lookup"><span data-stu-id="3fba8-154">All optimizations are turned on and the profiler is enabled.</span></span> <span data-ttu-id="3fba8-155">用來評估應用程式效能。</span><span class="sxs-lookup"><span data-stu-id="3fba8-155">Used to evaluate app performance.</span></span> | 

<span data-ttu-id="3fba8-156">請注意，上述清單是常見觸發程式的子集，這些觸發程式會導致 Visual Studio 專案需要產生。</span><span class="sxs-lookup"><span data-stu-id="3fba8-156">Note, the above list is a subset of the common triggers that will cause the Visual Studio project to need to be generated.</span></span> <span data-ttu-id="3fba8-157">一般而言，從 Visual Studio 中編輯 .cs 檔案不需要從 Unity 內重新產生專案。</span><span class="sxs-lookup"><span data-stu-id="3fba8-157">In general, editing .cs files from within Visual Studio won't require the project to be regenerated from within Unity.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="3fba8-158">疑難排解</span><span class="sxs-lookup"><span data-stu-id="3fba8-158">Troubleshooting</span></span>

<span data-ttu-id="3fba8-159">如果您在 Visual Studio 專案中發現無法辨識 .cs 檔案的編輯，請確定當您從 Unity 的 [組建] 功能表產生 VS 專案時，會檢查 **Unity c # 專案** 。</span><span class="sxs-lookup"><span data-stu-id="3fba8-159">If you find that edits to your .cs files aren't being recognized in your Visual Studio project, ensure that **Unity C# Projects** is checked when you generate the VS project from Unity's Build menu.</span></span>
