---
title: 建立全像攝影 DirectX 專案
description: 說明如何根據 Windows Mixed Reality 應用程式範本建立新的全像全像攝影應用程式。
author: mikeriches
ms.author: mriches
ms.date: 08/04/2020
ms.topic: article
keywords: Windows Mixed Reality，全像攝影應用程式、新的應用程式、UWP 應用程式、範本應用程式、全像投影、新專案、逐步解說、下載、範例程式碼、混合現實耳機、windows Mixed Reality 耳機、虛擬實境耳機
ms.openlocfilehash: f377ca5b8af08beb53c878e1ebf665b8074853f6
ms.sourcegitcommit: 2bf79eef6a9b845494484f458443ef4f89d7efc0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/17/2020
ms.locfileid: "97613082"
---
# <a name="creating-a-holographic-directx-project"></a><span data-ttu-id="77d4f-104">建立全像攝影 DirectX 專案</span><span class="sxs-lookup"><span data-stu-id="77d4f-104">Creating a holographic DirectX project</span></span>

> [!NOTE]
> <span data-ttu-id="77d4f-105">本文與舊版 WinRT 原生 Api 相關。</span><span class="sxs-lookup"><span data-stu-id="77d4f-105">This article relates to the legacy WinRT native APIs.</span></span>  <span data-ttu-id="77d4f-106">針對新的原生應用程式專案，建議使用 **[OPENXR API](openxr-getting-started.md)**。</span><span class="sxs-lookup"><span data-stu-id="77d4f-106">For new native app projects, we recommend using the **[OpenXR API](openxr-getting-started.md)**.</span></span>

<span data-ttu-id="77d4f-107">您為 HoloLens 建立的全像攝影應用程式將會是 <a href="https://docs.microsoft.com/windows/uwp/get-started/universal-application-platform-guide" target="_blank">通用 Windows 平臺 (UWP) 應用程式</a>。</span><span class="sxs-lookup"><span data-stu-id="77d4f-107">A holographic app you create for a HoloLens will be a <a href="https://docs.microsoft.com/windows/uwp/get-started/universal-application-platform-guide" target="_blank">Universal Windows Platform (UWP) app</a>.</span></span>  <span data-ttu-id="77d4f-108">如果以桌面為目標 Windows Mixed Reality 耳機，您可以建立 UWP 應用程式或 Win32 應用程式。</span><span class="sxs-lookup"><span data-stu-id="77d4f-108">If targeting desktop Windows Mixed Reality headsets, you can create a UWP app or a Win32 app.</span></span>

<span data-ttu-id="77d4f-109">DirectX 11 全像 UWP 應用程式範本非常類似于 DirectX 11 UWP 應用程式範本。</span><span class="sxs-lookup"><span data-stu-id="77d4f-109">The DirectX 11 holographic UWP app template is much like the DirectX 11 UWP app template.</span></span> <span data-ttu-id="77d4f-110">範本包含程式迴圈、用來管理 Direct3D 裝置和內容的 **DeviceResources** 類別，以及簡化的內容轉譯器類別。</span><span class="sxs-lookup"><span data-stu-id="77d4f-110">The template includes a program loop, a **DeviceResources** class to manage the Direct3D device and context, and a simplified content renderer class.</span></span> <span data-ttu-id="77d4f-111">它也有 <a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.iframeworkview" target="_blank">IFrameworkView</a>，就像任何其他 UWP 應用程式一樣。</span><span class="sxs-lookup"><span data-stu-id="77d4f-111">It also has an <a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.iframeworkview" target="_blank">IFrameworkView</a>, just like any other UWP app.</span></span>

<span data-ttu-id="77d4f-112">不過，混合現實應用程式中有一些其他功能不存在於一般的 Direct3D UWP 應用程式中。</span><span class="sxs-lookup"><span data-stu-id="77d4f-112">The mixed reality app, however, has some additional capabilities that aren't present in a typical Direct3D UWP app.</span></span> <span data-ttu-id="77d4f-113">Windows Mixed Reality 應用程式範本可以：</span><span class="sxs-lookup"><span data-stu-id="77d4f-113">The Windows Mixed Reality app template can:</span></span>
* <span data-ttu-id="77d4f-114">處理與全像攝影攝影機相關聯的 Direct3D 裝置資源。</span><span class="sxs-lookup"><span data-stu-id="77d4f-114">Handle Direct3D device resources associated with holographic cameras.</span></span>
* <span data-ttu-id="77d4f-115">從系統取出相機背面緩衝區。</span><span class="sxs-lookup"><span data-stu-id="77d4f-115">Retrieve camera back buffers from the system.</span></span> <span data-ttu-id="77d4f-116">在 Direct3D12 的案例中，請建立全像背景緩衝區資源，並管理資源存留期。</span><span class="sxs-lookup"><span data-stu-id="77d4f-116">In the case of Direct3D12, create holographic back buffer resources and manage resource lifetimes.</span></span>
* <span data-ttu-id="77d4f-117">處理 [注視](../../design/gaze-and-commit.md) 輸入，並辨識 [手勢](../../design/gaze-and-commit.md#composite-gestures)。</span><span class="sxs-lookup"><span data-stu-id="77d4f-117">Handle [gaze](../../design/gaze-and-commit.md) input, and recognize a [gesture](../../design/gaze-and-commit.md#composite-gestures).</span></span>
* <span data-ttu-id="77d4f-118">進入全螢幕身歷聲轉譯模式。</span><span class="sxs-lookup"><span data-stu-id="77d4f-118">Go into full-screen stereo rendering mode.</span></span>

## <a name="how-do-i-get-started"></a><span data-ttu-id="77d4f-119">如何開始？</span><span class="sxs-lookup"><span data-stu-id="77d4f-119">How do I get started?</span></span>

<span data-ttu-id="77d4f-120">請先依照下載 Visual Studio 2019 和 Windows Mixed Reality 應用程式範本的指示， [安裝這些工具](../install-the-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="77d4f-120">First [install the tools](../install-the-tools.md), following the instructions on downloading Visual Studio 2019 and the Windows Mixed Reality app templates.</span></span> <span data-ttu-id="77d4f-121">混合現實應用程式範本可在 Visual Studio marketplace 上以 [網路下載](https://marketplace.visualstudio.com/items?itemName=WindowsMixedRealityteam.WindowsMixedRealityAppTemplatesVSIX)的形式提供，或透過 Visual Studio UI 安裝為擴充功能。</span><span class="sxs-lookup"><span data-stu-id="77d4f-121">The mixed reality app templates are available on the Visual Studio marketplace as a [web download](https://marketplace.visualstudio.com/items?itemName=WindowsMixedRealityteam.WindowsMixedRealityAppTemplatesVSIX), or by installing them as an extension through the Visual Studio UI.</span></span>

<span data-ttu-id="77d4f-122">現在您已經準備好建立 DirectX 11 Windows Mixed Reality 應用程式！</span><span class="sxs-lookup"><span data-stu-id="77d4f-122">Now you're ready to create your DirectX 11 Windows Mixed Reality app!</span></span> <span data-ttu-id="77d4f-123">請注意，若要移除範例內容，請將 *pch* 中的 **DRAW_SAMPLE_CONTENT** 預處理器指示詞標記為批註。</span><span class="sxs-lookup"><span data-stu-id="77d4f-123">Note, to remove the sample content, comment out the **DRAW_SAMPLE_CONTENT** preprocessor directive in *pch.h*.</span></span>

## <a name="creating-a-uwp-project"></a><span data-ttu-id="77d4f-124">建立 UWP 專案</span><span class="sxs-lookup"><span data-stu-id="77d4f-124">Creating a UWP project</span></span>

<span data-ttu-id="77d4f-125">安裝工具之後，請 (]。install-the-tools.md) 您接著可以建立全像的 DirectX UWP 專案。</span><span class="sxs-lookup"><span data-stu-id="77d4f-125">Once the tools are installed,](../install-the-tools.md) you can then create a holographic DirectX UWP project.</span></span>

<span data-ttu-id="77d4f-126">若要在 Visual Studio 2019 中建立新專案：</span><span class="sxs-lookup"><span data-stu-id="77d4f-126">To create a new project in Visual Studio 2019:</span></span>
1. <span data-ttu-id="77d4f-127">開始 **Visual Studio**。</span><span class="sxs-lookup"><span data-stu-id="77d4f-127">Start **Visual Studio**.</span></span>
2. <span data-ttu-id="77d4f-128">在右邊的 **開始** 區段中，選取 [ **建立新專案**]。</span><span class="sxs-lookup"><span data-stu-id="77d4f-128">In the **Get Started** section on the right, select **Create a new project**.</span></span>
3. <span data-ttu-id="77d4f-129">在 [ **建立新專案** ] 對話方塊的下拉式功能表中，選取 [ **c + +**]、[ **Windows Mixed Reality**] 和 [ **UWP**]。</span><span class="sxs-lookup"><span data-stu-id="77d4f-129">In the drop-down menus in the **Create a new project** dialog, select **C++**, **Windows Mixed Reality**, and **UWP**.</span></span>
4. <span data-ttu-id="77d4f-130">選取 **(通用 Windows)  (c + +/WinRT) 的全像 DirectX 11 應用程式**。</span><span class="sxs-lookup"><span data-stu-id="77d4f-130">Select **Holographic DirectX 11 App (Universal Windows) (C++/WinRT)**.</span></span>
   <span data-ttu-id="77d4f-131">![Visual Studio 2019 中全像 DirectX 11 c + +/WinRT UWP 應用程式專案範本的螢幕擷取畫面](images/holographic-directx-app-cpp-new-project-2019.png)</span><span class="sxs-lookup"><span data-stu-id="77d4f-131">![Screenshot of the Holographic DirectX 11 C++/WinRT UWP app project template in Visual Studio 2019](images/holographic-directx-app-cpp-new-project-2019.png)</span></span><br>
   <span data-ttu-id="77d4f-132">*Visual Studio 2019 的全像 DirectX 11 c + +/WinRT UWP 應用程式專案範本*</span><span class="sxs-lookup"><span data-stu-id="77d4f-132">*Holographic DirectX 11 C++/WinRT UWP app project template in Visual Studio 2019*</span></span>
   >[!IMPORTANT]
   ><span data-ttu-id="77d4f-133">請確定專案範本的名稱包含 " (c + +/WinRT) "。</span><span class="sxs-lookup"><span data-stu-id="77d4f-133">Be sure that the project template's name includes "(C++/WinRT)".</span></span>  <span data-ttu-id="77d4f-134">如果沒有，則會安裝較舊版本的全像攝影專案範本。</span><span class="sxs-lookup"><span data-stu-id="77d4f-134">If not, you have an older version of the holographic project templates installed.</span></span>  <span data-ttu-id="77d4f-135">若要取得最新的專案範本，請將 [其安裝](../install-the-tools.md) 為 Visual Studio 2019 的擴充功能。</span><span class="sxs-lookup"><span data-stu-id="77d4f-135">To get the latest project templates, [install them](../install-the-tools.md) as an extension to Visual Studio 2019.</span></span>
5. <span data-ttu-id="77d4f-136">選取 [下一步]。</span><span class="sxs-lookup"><span data-stu-id="77d4f-136">Select **Next**.</span></span>
5. <span data-ttu-id="77d4f-137">填寫 [ **專案名稱** ] 和 [ **位置** ] 文字方塊，然後選取或按一下 [ **建立**]。</span><span class="sxs-lookup"><span data-stu-id="77d4f-137">Fill in the **Project name** and **Location** text boxes, and select or tap **Create**.</span></span> <span data-ttu-id="77d4f-138">建立全像應用程式專案。</span><span class="sxs-lookup"><span data-stu-id="77d4f-138">The holographic app project is created.</span></span>
6. <span data-ttu-id="77d4f-139">針對僅限 HoloLens 2 的開發目標，請確定 **目標版本** 和 **最低版本** 都設為 **Windows 10 1903 版**。</span><span class="sxs-lookup"><span data-stu-id="77d4f-139">For development targeting only HoloLens 2, ensure that the **Target version** and **Minimum version** are set to **Windows 10, version 1903**.</span></span>  <span data-ttu-id="77d4f-140">如果您也將目標設為 HoloLens (第1代) 或桌面 Windows Mixed Reality 耳機，您可以將 **最低版本** 設定為 **Windows 10 版本 1809**。</span><span class="sxs-lookup"><span data-stu-id="77d4f-140">If you're also targeting HoloLens (1st gen) or desktop Windows Mixed Reality headsets, you can set **Minimum version** to **Windows 10, version 1809**.</span></span> <span data-ttu-id="77d4f-141">當您使用 HoloLens 2 的新功能時，您的程式碼中將需要一些 <a href="https://docs.microsoft.com/windows/uwp/debug-test-perf/version-adaptive-code" target="_blank">版本的自我調整性檢查</a> 。</span><span class="sxs-lookup"><span data-stu-id="77d4f-141">This will require some <a href="https://docs.microsoft.com/windows/uwp/debug-test-perf/version-adaptive-code" target="_blank">version adaptive checks</a> in your code when using new features of HoloLens 2.</span></span>
   <span data-ttu-id="77d4f-142">![將 Windows 10 1903 版設定為目標和最小版本的螢幕擷取畫面](images/new-uwp-project.png)</span><span class="sxs-lookup"><span data-stu-id="77d4f-142">![Screenshot of setting Windows 10, version 1903 as the target and minimum versions](images/new-uwp-project.png)</span></span><br>
   <span data-ttu-id="77d4f-143">*將 **Windows 10 1903 版** 設定為目標和最小版本*</span><span class="sxs-lookup"><span data-stu-id="77d4f-143">*Setting **Windows 10, version 1903** as the target and minimum versions*</span></span>
   >[!IMPORTANT]
   ><span data-ttu-id="77d4f-144">如果您沒有看到 **Windows 10，版本 1903** 是一個選項，則未安裝最新的 Windows 10 SDK。</span><span class="sxs-lookup"><span data-stu-id="77d4f-144">If you do not see **Windows 10, version 1903** as an option, you do not have the latest Windows 10 SDK installed.</span></span>  <span data-ttu-id="77d4f-145">若要讓此選項出現，請 <a href="https://developer.microsoft.com/windows/downloads/windows-10-sdk" target="_blank">安裝 WINDOWS 10 SDK 的版本10.0.18362.0 或更新版本</a>。</span><span class="sxs-lookup"><span data-stu-id="77d4f-145">To get this option to appear, <a href="https://developer.microsoft.com/windows/downloads/windows-10-sdk" target="_blank">install version 10.0.18362.0 or later of the Windows 10 SDK</a>.</span></span>

<span data-ttu-id="77d4f-146">若要在 Visual Studio 2017 中建立新專案：</span><span class="sxs-lookup"><span data-stu-id="77d4f-146">To create a new project in Visual Studio 2017:</span></span>
1. <span data-ttu-id="77d4f-147">開始 **Visual Studio**。</span><span class="sxs-lookup"><span data-stu-id="77d4f-147">Start **Visual Studio**.</span></span>
2. <span data-ttu-id="77d4f-148">**在 [檔案] 功能表中**，指向 [**新增**]，然後從內容功能表中選取 [**專案**]。</span><span class="sxs-lookup"><span data-stu-id="77d4f-148">From the **File** menu, point to **New** and select **Project** from the context menu.</span></span> <span data-ttu-id="77d4f-149">[新增專案]  對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="77d4f-149">The **New Project** dialog opens.</span></span>
3. <span data-ttu-id="77d4f-150">展開左側的 [ **已安裝** ]，然後展開 **Visual C++** 語言節點。</span><span class="sxs-lookup"><span data-stu-id="77d4f-150">Expand **Installed** on the left and expand the **Visual C++** language node.</span></span>
4. <span data-ttu-id="77d4f-151">流覽至 [ **Windows 通用 >** 全像] 節點，然後選取 [全像] **DirectX 11 應用程式 (通用 Windows)  (c + +/WinRT])**。</span><span class="sxs-lookup"><span data-stu-id="77d4f-151">Navigate to the **Windows Universal > Holographic** node and select **Holographic DirectX 11 App (Universal Windows) (C++/WinRT)**.</span></span>
   <span data-ttu-id="77d4f-152">![Visual Studio 2017 中全像 DirectX 11 c + +/WinRT UWP 應用程式專案範本的螢幕擷取畫面](images/holographic-directx-app-cpp-new-project.png)</span><span class="sxs-lookup"><span data-stu-id="77d4f-152">![Screenshot of the Holographic DirectX 11 C++/WinRT UWP app project template in Visual Studio 2017](images/holographic-directx-app-cpp-new-project.png)</span></span><br>
   <span data-ttu-id="77d4f-153">*Visual Studio 2017 的全像 DirectX 11 c + +/WinRT UWP 應用程式專案範本*</span><span class="sxs-lookup"><span data-stu-id="77d4f-153">*Holographic DirectX 11 C++/WinRT UWP app project template in Visual Studio 2017*</span></span>
   >[!IMPORTANT]
   ><span data-ttu-id="77d4f-154">請確定專案範本的名稱包含 " (c + +/WinRT) "。</span><span class="sxs-lookup"><span data-stu-id="77d4f-154">Be sure that the project template's name includes "(C++/WinRT)".</span></span>  <span data-ttu-id="77d4f-155">如果沒有，則會安裝較舊版本的全像攝影專案範本。</span><span class="sxs-lookup"><span data-stu-id="77d4f-155">If not, you have an older version of the holographic project templates installed.</span></span>  <span data-ttu-id="77d4f-156">若要取得最新的專案範本，請將 [其安裝](../install-the-tools.md) 為 Visual Studio 2017 的擴充功能。</span><span class="sxs-lookup"><span data-stu-id="77d4f-156">To get the latest project templates, [install them](../install-the-tools.md) as an extension to Visual Studio 2017.</span></span>
5. <span data-ttu-id="77d4f-157">填寫 [ **名稱** ] 和 [ **位置** ] 文字方塊，然後選取或按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="77d4f-157">Fill in the **Name** and **Location** text boxes, and select or tap **OK**.</span></span> <span data-ttu-id="77d4f-158">建立全像應用程式專案。</span><span class="sxs-lookup"><span data-stu-id="77d4f-158">The holographic app project is created.</span></span>
6. <span data-ttu-id="77d4f-159">針對僅限 HoloLens 2 的開發目標，請確定 **目標版本** 和 **最低版本** 都設為 **Windows 10 1903 版**。</span><span class="sxs-lookup"><span data-stu-id="77d4f-159">For development targeting only HoloLens 2, ensure that the **Target version** and **Minimum version** are set to **Windows 10, version 1903**.</span></span>  <span data-ttu-id="77d4f-160">如果您也將目標設為 HoloLens (第1代) 或桌面 Windows Mixed Reality 耳機，您可以將 **最低版本** 設定為 **Windows 10 版本 1809**。</span><span class="sxs-lookup"><span data-stu-id="77d4f-160">If you're also targeting HoloLens (1st gen) or desktop Windows Mixed Reality headsets, you can set **Minimum version** to **Windows 10, version 1809**.</span></span> <span data-ttu-id="77d4f-161">當您使用 HoloLens 2 的新功能時，您的程式碼中將需要一些 <a href="https://docs.microsoft.com/windows/uwp/debug-test-perf/version-adaptive-code" target="_blank">版本的自我調整性檢查</a> 。</span><span class="sxs-lookup"><span data-stu-id="77d4f-161">This will require some <a href="https://docs.microsoft.com/windows/uwp/debug-test-perf/version-adaptive-code" target="_blank">version adaptive checks</a> in your code when using new features of HoloLens 2.</span></span>
   <span data-ttu-id="77d4f-162">![將 Windows 10 1903 版設定為目標和最小版本的螢幕擷取畫面](images/new-uwp-project.png)</span><span class="sxs-lookup"><span data-stu-id="77d4f-162">![Screenshot of setting Windows 10, version 1903 as the target and minimum versions](images/new-uwp-project.png)</span></span><br>
   <span data-ttu-id="77d4f-163">*將 **Windows 10 1903 版** 設定為目標和最小版本*</span><span class="sxs-lookup"><span data-stu-id="77d4f-163">*Setting **Windows 10, version 1903** as the target and minimum versions*</span></span>
   >[!IMPORTANT]
   ><span data-ttu-id="77d4f-164">如果您沒有看到 **Windows 10，版本 1903** 是一個選項，則未安裝最新的 Windows 10 SDK。</span><span class="sxs-lookup"><span data-stu-id="77d4f-164">If you do not see **Windows 10, version 1903** as an option, you do not have the latest Windows 10 SDK installed.</span></span>  <span data-ttu-id="77d4f-165">若要讓此選項出現，請 <a href="https://developer.microsoft.com/windows/downloads/windows-10-sdk" target="_blank">安裝 WINDOWS 10 SDK 的版本10.0.18362.0 或更新版本</a>。</span><span class="sxs-lookup"><span data-stu-id="77d4f-165">To get this option to appear, <a href="https://developer.microsoft.com/windows/downloads/windows-10-sdk" target="_blank">install version 10.0.18362.0 or later of the Windows 10 SDK</a>.</span></span>

<span data-ttu-id="77d4f-166">此範本會使用 <a href="https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/" target="_blank">c + +/WinRT</a>來產生專案，這是支援任何符合標準的 c + + 17 編譯器之 Windows 執行階段 Api 的 c + + 17 語言投射。</span><span class="sxs-lookup"><span data-stu-id="77d4f-166">The template generates a project using <a href="https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/" target="_blank">C++/WinRT</a>, a C++17 language projection of the Windows Runtime APIs that supports any standards-compliant C++17 compiler.</span></span>  <span data-ttu-id="77d4f-167">專案會顯示如何建立由使用者放置2個計量的全球鎖定 cube。</span><span class="sxs-lookup"><span data-stu-id="77d4f-167">The project shows how to create a world-locked cube that's placed 2 meters from the user.</span></span> <span data-ttu-id="77d4f-168">使用者可以 [按一下](../../design/gaze-and-commit.md#composite-gestures) 或按下控制器上的按鈕，將 cube 放在使用者的 [注視](../../design/gaze-and-commit.md)所指定的不同位置。</span><span class="sxs-lookup"><span data-stu-id="77d4f-168">The user can [air-tap](../../design/gaze-and-commit.md#composite-gestures) or press a button on the controller to place the cube in a different position specified by the user's [gaze](../../design/gaze-and-commit.md).</span></span> <span data-ttu-id="77d4f-169">您可以修改此專案來建立任何混合現實應用程式。</span><span class="sxs-lookup"><span data-stu-id="77d4f-169">You can modify this project to create any mixed reality app.</span></span>

<span data-ttu-id="77d4f-170">您也可以使用以 SharpDX 為基礎的 **Visual c #** 全像投影專案範本來建立新專案。</span><span class="sxs-lookup"><span data-stu-id="77d4f-170">You can also create a new project using the **Visual C#** holographic project template, which is based on SharpDX.</span></span>  <span data-ttu-id="77d4f-171">如果您的全像 c # 專案不是從 Windows 全像應用程式範本開始，則必須從 Windows Mixed Reality c # 範本專案中複製 fxcompile 檔，並將它匯入 .csproj 檔案，以編譯您新增至專案的 HLSL 檔案。</span><span class="sxs-lookup"><span data-stu-id="77d4f-171">If your holographic C# project didn't start from the Windows Holographic app template, you'll need to copy the ms.fxcompile.targets file from a Windows Mixed Reality C# template project and import it in your.csproj file to compile HLSL files that you add to your project.</span></span> <span data-ttu-id="77d4f-172">您也可以在 Windows Mixed Reality 應用程式範本延伸模組中提供 Direct3D 12 範本，以 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="77d4f-172">A Direct3D 12 template is also provided in the Windows Mixed Reality app templates extension to Visual Studio.</span></span>

<span data-ttu-id="77d4f-173">請參閱 [使用 Visual Studio 部署和調試](../platform-capabilities-and-apis/using-visual-studio.md) 程式，以取得如何建立範例，並將其部署至您的 HoloLens、具有沉浸式裝置連接的電腦或模擬器的資訊。</span><span class="sxs-lookup"><span data-stu-id="77d4f-173">Review [Using Visual Studio to deploy and debug](../platform-capabilities-and-apis/using-visual-studio.md) for information on how to build and deploy the sample to your HoloLens, PC with immersive device attached, or an emulator.</span></span>

<span data-ttu-id="77d4f-174">下列其餘指示將假設您使用 c + + 來建立應用程式。</span><span class="sxs-lookup"><span data-stu-id="77d4f-174">The rest of the instructions below will assume that you're using C++ to build your app.</span></span>

### <a name="uwp-app-entry-point"></a><span data-ttu-id="77d4f-175">UWP 應用程式進入點</span><span class="sxs-lookup"><span data-stu-id="77d4f-175">UWP app entry point</span></span>

<span data-ttu-id="77d4f-176">您的全像 UWP 應用程式會在 AppView 中的 **wWinMain** 函式開始。</span><span class="sxs-lookup"><span data-stu-id="77d4f-176">Your holographic UWP app starts in the **wWinMain** function in AppView.cpp.</span></span> <span data-ttu-id="77d4f-177">**WWinMain** 函式會建立應用程式的 <a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.iframeworkview" target="_blank">IFrameworkView</a> ，並使用它來啟動 <a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.coreapplication" target="_blank">CoreApplication</a> 。</span><span class="sxs-lookup"><span data-stu-id="77d4f-177">The **wWinMain** function creates the app's <a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.iframeworkview" target="_blank">IFrameworkView</a> and starts the <a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.coreapplication" target="_blank">CoreApplication</a> with it.</span></span>

<span data-ttu-id="77d4f-178">從 **AppView .cpp**：</span><span class="sxs-lookup"><span data-stu-id="77d4f-178">From **AppView.cpp**:</span></span>

```cpp
// The main function bootstraps into the IFrameworkView.
int __stdcall wWinMain(HINSTANCE, HINSTANCE, PWSTR, int)
{
    winrt::init_apartment();
    CoreApplication::Run(AppViewSource());
    return 0;
}
```

<span data-ttu-id="77d4f-179">從該時間點開始，AppView 類別會處理與 Windows 基本輸入事件、CoreWindow 事件和訊息等的互動。</span><span class="sxs-lookup"><span data-stu-id="77d4f-179">From that point on, the AppView class handles interaction with Windows basic input events, CoreWindow events and messaging, and so on.</span></span> <span data-ttu-id="77d4f-180">它也會建立您的應用程式所使用的 HolographicSpace。</span><span class="sxs-lookup"><span data-stu-id="77d4f-180">It will also create the HolographicSpace used by your app.</span></span>

## <a name="creating-a-win32-project"></a><span data-ttu-id="77d4f-181">建立 Win32 專案</span><span class="sxs-lookup"><span data-stu-id="77d4f-181">Creating a Win32 project</span></span>

<span data-ttu-id="77d4f-182">開始建立 Win32 全像專案的最簡單方式，就是調整 <a href="https://github.com/Microsoft/Windows-classic-samples/tree/master/Samples/BasicHologram" target="_blank"> *BasicHologram* win32 範例</a>。</span><span class="sxs-lookup"><span data-stu-id="77d4f-182">The easiest way to get started building a Win32 holographic project is to adapt the <a href="https://github.com/Microsoft/Windows-classic-samples/tree/master/Samples/BasicHologram" target="_blank">*BasicHologram* Win32 sample</a>.</span></span>

<span data-ttu-id="77d4f-183">這個 Win32 範例使用 <a href="https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/" target="_blank">c + +/WinRT</a>，這是支援任何符合標準的 c + + 17 編譯器之 Windows 執行階段 Api 的 c + + 17 語言投射。</span><span class="sxs-lookup"><span data-stu-id="77d4f-183">This Win32 sample uses <a href="https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/" target="_blank">C++/WinRT</a>, a C++17 language projection of the Windows Runtime APIs that supports any standards-compliant C++17 compiler.</span></span>  <span data-ttu-id="77d4f-184">專案會顯示如何建立由使用者放置2個計量的全球鎖定 cube。</span><span class="sxs-lookup"><span data-stu-id="77d4f-184">The project shows how to create a world-locked cube that's placed 2 meters from the user.</span></span> <span data-ttu-id="77d4f-185">使用者可以按下控制器上的按鈕，將 cube 放在使用者的 [注視](../../design/gaze-and-commit.md)所指定的不同位置。</span><span class="sxs-lookup"><span data-stu-id="77d4f-185">The user can press a button on the controller to place the cube in a different position that's specified by the user's [gaze](../../design/gaze-and-commit.md).</span></span> <span data-ttu-id="77d4f-186">您可以修改此專案來建立任何混合現實應用程式。</span><span class="sxs-lookup"><span data-stu-id="77d4f-186">You can modify this project to create any mixed reality app.</span></span>

### <a name="win32-app-entry-point"></a><span data-ttu-id="77d4f-187">Win32 應用程式進入點</span><span class="sxs-lookup"><span data-stu-id="77d4f-187">Win32 app entry point</span></span>

<span data-ttu-id="77d4f-188">您的全像 Win32 應用程式會在 AppMain 中的 **wWinMain** 函式開始。</span><span class="sxs-lookup"><span data-stu-id="77d4f-188">Your holographic Win32 app starts in the **wWinMain** function in AppMain.cpp.</span></span> <span data-ttu-id="77d4f-189">**WWinMain** 函式會建立應用程式的 HWND，並啟動其訊息迴圈。</span><span class="sxs-lookup"><span data-stu-id="77d4f-189">The **wWinMain** function creates the app's HWND and starts its message loop.</span></span>

<span data-ttu-id="77d4f-190">從 **AppMain .cpp**：</span><span class="sxs-lookup"><span data-stu-id="77d4f-190">From **AppMain.cpp**:</span></span>

```cpp
int APIENTRY wWinMain(
    _In_     HINSTANCE hInstance,
    _In_opt_ HINSTANCE hPrevInstance,
    _In_     LPWSTR    lpCmdLine,
    _In_     int       nCmdShow)
{
    UNREFERENCED_PARAMETER(hPrevInstance);
    UNREFERENCED_PARAMETER(lpCmdLine);

    winrt::init_apartment();

    App app;

    // Initialize global strings, and perform application initialization.
    app.Initialize(hInstance);

    // Create the HWND and the HolographicSpace.
    app.CreateWindowAndHolographicSpace(hInstance, nCmdShow);

    // Main message loop:
    app.Run(hInstance);

    // Perform application teardown.
    app.Uninitialize();

    return 0;
}
```

<span data-ttu-id="77d4f-191">從該時間點開始，AppMain 類別會處理與基本視窗訊息的互動等等。</span><span class="sxs-lookup"><span data-stu-id="77d4f-191">From that point on, the AppMain class handles interaction with basic window messages, and so on.</span></span> <span data-ttu-id="77d4f-192">它也會建立您的應用程式所使用的 HolographicSpace。</span><span class="sxs-lookup"><span data-stu-id="77d4f-192">It will also create the HolographicSpace used by your app.</span></span>

## <a name="render-holographic-content"></a><span data-ttu-id="77d4f-193">轉譯全息內容</span><span class="sxs-lookup"><span data-stu-id="77d4f-193">Render holographic content</span></span>

<span data-ttu-id="77d4f-194">專案的 **Content** 資料夾包含用來轉譯全像攝影 [空間](getting-a-holographicspace.md)中之全息的類別。</span><span class="sxs-lookup"><span data-stu-id="77d4f-194">The project's **Content** folder contains classes for rendering holograms in the [holographic space](getting-a-holographicspace.md).</span></span> <span data-ttu-id="77d4f-195">範本中的預設全息圖是放置2個計量離開使用者的旋轉 cube。</span><span class="sxs-lookup"><span data-stu-id="77d4f-195">The default hologram in the template is a spinning cube that's placed 2 meters away from the user.</span></span> <span data-ttu-id="77d4f-196">繪圖這個 cube 是在 **SpinningCubeRenderer** 中執行，其中包含下列主要方法：</span><span class="sxs-lookup"><span data-stu-id="77d4f-196">Drawing this cube is implemented in **SpinningCubeRenderer.cpp**, which has these key methods:</span></span>

|  <span data-ttu-id="77d4f-197">方法</span><span class="sxs-lookup"><span data-stu-id="77d4f-197">Method</span></span>  |  <span data-ttu-id="77d4f-198">說明</span><span class="sxs-lookup"><span data-stu-id="77d4f-198">Explanation</span></span> | 
|----------|----------|
|  `CreateDeviceDependentResources` |  <span data-ttu-id="77d4f-199">載入著色器並建立立方體網格。</span><span class="sxs-lookup"><span data-stu-id="77d4f-199">Loads shaders and creates the cube mesh.</span></span> | 
|  `PositionHologram` |  <span data-ttu-id="77d4f-200">將全像放置於所提供 <a href="https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerpose" target="_blank">SpatialPointerPose</a>所指定的位置。</span><span class="sxs-lookup"><span data-stu-id="77d4f-200">Places the hologram at the location specified by the provided <a href="https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerpose" target="_blank">SpatialPointerPose</a>.</span></span> | 
|  `Update` |  <span data-ttu-id="77d4f-201">旋轉 cube，並設定模型矩陣。</span><span class="sxs-lookup"><span data-stu-id="77d4f-201">Rotates the cube, and sets the model matrix.</span></span> | 
|  `Render` |  <span data-ttu-id="77d4f-202">使用頂點和圖元著色器呈現框架。</span><span class="sxs-lookup"><span data-stu-id="77d4f-202">Renders a frame using the vertex and pixel shaders.</span></span> | 

<span data-ttu-id="77d4f-203">**著色** 子資料夾包含四個預設著色器執行：</span><span class="sxs-lookup"><span data-stu-id="77d4f-203">The **Shaders** subfolder contains four default shader implementations:</span></span>

|  <span data-ttu-id="77d4f-204">著色器</span><span class="sxs-lookup"><span data-stu-id="77d4f-204">Shader</span></span>  |  <span data-ttu-id="77d4f-205">說明</span><span class="sxs-lookup"><span data-stu-id="77d4f-205">Explanation</span></span> | 
|----------|----------|
|  `GeometryShader.hlsl` |  <span data-ttu-id="77d4f-206">將幾何保留未修改狀態的傳遞。</span><span class="sxs-lookup"><span data-stu-id="77d4f-206">A pass-through that leaves the geometry unmodified.</span></span> | 
|  `PixelShader.hlsl` |  <span data-ttu-id="77d4f-207">通過色彩資料。</span><span class="sxs-lookup"><span data-stu-id="77d4f-207">Passes through the color data.</span></span> <span data-ttu-id="77d4f-208">色彩資料會在點陣化步驟中插補並指派給圖元。</span><span class="sxs-lookup"><span data-stu-id="77d4f-208">The color data is interpolated and assigned to a pixel at the rasterization step.</span></span> | 
|  `VertexShader.hlsl` |  <span data-ttu-id="77d4f-209">在 GPU 上進行頂點處理的簡單著色器。</span><span class="sxs-lookup"><span data-stu-id="77d4f-209">Simple shader to do vertex processing on the GPU.</span></span> | 
|  `VPRTVertexShader.hlsl` |  <span data-ttu-id="77d4f-210">在 GPU 上進行頂點處理的簡單著色器，已針對 Windows Mixed Reality 身歷聲轉譯進行優化。</span><span class="sxs-lookup"><span data-stu-id="77d4f-210">Simple shader to do vertex processing on the GPU, that is optimized for Windows Mixed Reality stereo rendering.</span></span> | 

<span data-ttu-id="77d4f-211">`VertexShaderShared.hlsl` 包含與之間共用的通用程式碼 `VertexShader.hlsl` `VPRTVertexShader.hlsl` 。</span><span class="sxs-lookup"><span data-stu-id="77d4f-211">`VertexShaderShared.hlsl` contains common code shared between `VertexShader.hlsl` and `VPRTVertexShader.hlsl`.</span></span>

<span data-ttu-id="77d4f-212">注意： Direct3D 12 應用程式範本也包含 `ViewInstancingVertexShader.hlsl` 。</span><span class="sxs-lookup"><span data-stu-id="77d4f-212">Note: The Direct3D 12 app template also includes `ViewInstancingVertexShader.hlsl`.</span></span> <span data-ttu-id="77d4f-213">此變異使用 D3D12 選用功能來更有效率地轉譯身歷聲影像。</span><span class="sxs-lookup"><span data-stu-id="77d4f-213">This variant uses D3D12 optional features to render stereo images more efficiently.</span></span>

<span data-ttu-id="77d4f-214">著色器會在建立專案時編譯，並且載入至 **SpinningCubeRenderer：： CreateDeviceDependentResources** 方法。</span><span class="sxs-lookup"><span data-stu-id="77d4f-214">The shaders compile when the project is built, and loaded in the **SpinningCubeRenderer::CreateDeviceDependentResources** method.</span></span>

## <a name="interact-with-your-holograms"></a><span data-ttu-id="77d4f-215">與您的全像影像互動</span><span class="sxs-lookup"><span data-stu-id="77d4f-215">Interact with your holograms</span></span>

<span data-ttu-id="77d4f-216">使用者輸入是在 **SpatialInputHandler** 類別中處理，它會取得 <a href="https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionmanager" target="_blank">SpatialInteractionManager</a> 實例並訂閱 <a href="https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed" target="_blank">SourcePressed</a> 事件。</span><span class="sxs-lookup"><span data-stu-id="77d4f-216">User input is processed in the **SpatialInputHandler** class, which gets a <a href="https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionmanager" target="_blank">SpatialInteractionManager</a> instance and subscribes to the <a href="https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed" target="_blank">SourcePressed</a> event.</span></span> <span data-ttu-id="77d4f-217">這可讓您偵測輕量手勢和其他空間輸入事件。</span><span class="sxs-lookup"><span data-stu-id="77d4f-217">This enables detecting the air-tap gesture and other spatial input events.</span></span>

## <a name="update-holographic-content"></a><span data-ttu-id="77d4f-218">更新全像內容</span><span class="sxs-lookup"><span data-stu-id="77d4f-218">Update holographic content</span></span>

<span data-ttu-id="77d4f-219">遊戲迴圈中的混合現實應用程式更新，預設會在的 **Update** 方法中執行 `AppMain.cpp` 。</span><span class="sxs-lookup"><span data-stu-id="77d4f-219">Your mixed reality app updates in a game loop, which by default is implemented in the **Update** method in `AppMain.cpp`.</span></span> <span data-ttu-id="77d4f-220">**Update** 方法會更新場景物件（例如旋轉 cube），並傳回用來取得最新的視圖和投射矩陣，以及呈現交換鏈的 <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>物件。</span><span class="sxs-lookup"><span data-stu-id="77d4f-220">The **Update** method updates scene objects, like the spinning cube, and returns a <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> object that is used to get up-to-date view and projection matrices and to present the swap chain.</span></span>

<span data-ttu-id="77d4f-221">中的轉譯方法 `AppMain.cpp` 會接受<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> ，並根據目前的應用程式和空間定位狀態，將目前的畫面格轉譯為每個全像攝影相機。</span><span class="sxs-lookup"><span data-stu-id="77d4f-221">The **Render** method in `AppMain.cpp` takes the <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> and renders the current frame to each holographic camera, according to the current app and spatial positioning state.</span></span>

## <a name="notes"></a><span data-ttu-id="77d4f-222">備忘錄</span><span class="sxs-lookup"><span data-stu-id="77d4f-222">Notes</span></span>

<span data-ttu-id="77d4f-223">Windows Mixed Reality 應用程式範本現在支援使用已啟用 Spectre 防護旗標的編譯 (/Qspectre) 。</span><span class="sxs-lookup"><span data-stu-id="77d4f-223">The Windows Mixed Reality app template now supports compilation with the Spectre mitigation flag enabled (/Qspectre).</span></span> <span data-ttu-id="77d4f-224">在編譯設定 Spectre 緩和功能的設定之前，請務必先安裝 Spectre 緩和版的 Microsoft Visual C++ (MSVC) 執行時間程式庫。</span><span class="sxs-lookup"><span data-stu-id="77d4f-224">Make sure to install the Spectre-mitigated version of the Microsoft Visual C++ (MSVC) runtime libraries before compiling a configuration with Spectre mitigation enabled.</span></span> <span data-ttu-id="77d4f-225">若要安裝 Spectre 降低的 c + + 程式庫，請啟動 Visual Studio 安裝程式，然後選取 [ **修改**]。</span><span class="sxs-lookup"><span data-stu-id="77d4f-225">To install the Spectre-mitigated C++ libraries, launch the Visual Studio Installer and select **Modify**.</span></span> <span data-ttu-id="77d4f-226">流覽至 **個別元件** ，並搜尋 "spectre"。</span><span class="sxs-lookup"><span data-stu-id="77d4f-226">Navigate to **Individual components** and search for "spectre".</span></span> <span data-ttu-id="77d4f-227">選取對應至您需要編譯 Spectre 緩和程式碼之目標平臺和 MSVC 版本的方塊，然後按一下 [ **修改** ] 開始安裝。</span><span class="sxs-lookup"><span data-stu-id="77d4f-227">Select the boxes corresponding to the target platforms and MSVC version that you need to compile Spectre-mitigated code for, and click **Modify** to begin the install.</span></span>

## <a name="see-also"></a><span data-ttu-id="77d4f-228">另請參閱</span><span class="sxs-lookup"><span data-stu-id="77d4f-228">See also</span></span>
* [<span data-ttu-id="77d4f-229">取得 HolographicSpace</span><span class="sxs-lookup"><span data-stu-id="77d4f-229">Getting a HolographicSpace</span></span>](getting-a-holographicspace.md)
* <span data-ttu-id="77d4f-230"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspaceh" target="_blank">HolographicSpace</a></span><span class="sxs-lookup"><span data-stu-id="77d4f-230"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspaceh" target="_blank">HolographicSpace</a></span></span>
* [<span data-ttu-id="77d4f-231">DirectX 中的呈現</span><span class="sxs-lookup"><span data-stu-id="77d4f-231">Rendering in DirectX</span></span>](rendering-in-directx.md)
* [<span data-ttu-id="77d4f-232">使用 Visual Studio 來部署和偵錯</span><span class="sxs-lookup"><span data-stu-id="77d4f-232">Using Visual Studio to deploy and debug</span></span>](../platform-capabilities-and-apis/using-visual-studio.md)
* [<span data-ttu-id="77d4f-233">使用 HoloLens 模擬器</span><span class="sxs-lookup"><span data-stu-id="77d4f-233">Using the HoloLens emulator</span></span>](../platform-capabilities-and-apis/using-the-hololens-emulator.md)
* [<span data-ttu-id="77d4f-234">使用全像攝影 DirectX 應用程式中的 XAML</span><span class="sxs-lookup"><span data-stu-id="77d4f-234">Using XAML with holographic DirectX apps</span></span>](../platform-capabilities-and-apis/using-xaml-with-holographic-directx-apps.md)
