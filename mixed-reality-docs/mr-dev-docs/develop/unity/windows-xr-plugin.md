---
title: 使用 Windows XR 外掛程式
description: 瞭解如何使用 Windows XR 支援，在不使用 MRTK 的情況下設定 Unity 專案。
author: hferrone
ms.author: alexturn
ms.date: 03/26/2021
ms.topic: article
keywords: Unity，混合的現實，開發，使用者入門，新專案，Windows Mixed Reality，UWP，XR，效能，舊版，mrtk，Windows
ms.openlocfilehash: 44de6b418995b75d9e199f03922f89016b76c5cd
ms.sourcegitcommit: 719682f70a75f732b573442fae8987be1acaaf19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2021
ms.locfileid: "110743644"
---
# <a name="using-windows-xr-plugin"></a><span data-ttu-id="b4480-104">使用 Windows XR 外掛程式</span><span class="sxs-lookup"><span data-stu-id="b4480-104">Using Windows XR plugin</span></span>

<span data-ttu-id="b4480-105">針對以 Unity 2020 為目標的開發人員，Windows XR 外掛程式可讓您存取 HoloLens 2 和 Windows Mixed Reality 耳機上的混合現實功能。</span><span class="sxs-lookup"><span data-stu-id="b4480-105">For developers targeting Unity 2020, the Windows XR plugin enables access to mixed reality features on HoloLens 2 and Windows Mixed Reality headsets.</span></span>  <span data-ttu-id="b4480-106">Unity 2019 也支援此外掛程式，不過在該版本上使用此外掛程式時，Azure 空間錨點有一些已知的不相容性。</span><span class="sxs-lookup"><span data-stu-id="b4480-106">This plugin is also supported on Unity 2019, although there are some known incompatibilities with Azure Spatial Anchors when using this plugin on that version.</span></span>

<span data-ttu-id="b4480-107">雖然 Microsoft 和社區建立了開放原始碼工具，例如 [混合現實工具組 (MRTK) ](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html) ，而這些工具會自動設定 WMR 的環境，但許多開發人員想要從頭開始建立他們的體驗。</span><span class="sxs-lookup"><span data-stu-id="b4480-107">While Microsoft and the community have created opensource tools such as the [Mixed Reality Toolkit (MRTK)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html) that will automatically set up the WMR environment, many developers wish to build their experiences from the ground up.</span></span>  <span data-ttu-id="b4480-108">當您使用 MRTK 時，下列檔將示範如何針對混合現實開發正確設定專案。</span><span class="sxs-lookup"><span data-stu-id="b4480-108">The following documentation will demonstrate how to properly set up a project for Mixed Reality development whether you are using MRTK or not.</span></span>  <span data-ttu-id="b4480-109">您需要變更的設定分為兩類：每個專案設定和個別場景設定。</span><span class="sxs-lookup"><span data-stu-id="b4480-109">The settings you need to change are broken down into two categories: per-project settings and per-scene settings.</span></span>

## <a name="setting-up-your-project-with-mrtk"></a><span data-ttu-id="b4480-110">使用 MRTK 設定您的專案</span><span class="sxs-lookup"><span data-stu-id="b4480-110">Setting up your project with MRTK</span></span>

<span data-ttu-id="b4480-111">適用于 Unity 的 MRTK 會提供跨平臺輸入系統、基礎元件，以及空間互動的常見組建區塊。</span><span class="sxs-lookup"><span data-stu-id="b4480-111">MRTK for Unity provides a cross-platform input system, foundational components, and common building blocks for spatial interactions.</span></span> <span data-ttu-id="b4480-112">MRTK 第 2 版主要用於加速開發適用於 Microsoft HoloLens、Windows Mixed Reality 沈浸式 (VR) 頭戴裝置和 OpenVR 平台的應用程式。</span><span class="sxs-lookup"><span data-stu-id="b4480-112">MRTK version 2 intends to speed up application development for Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets, and OpenVR platform.</span></span> <span data-ttu-id="b4480-113">此專案的目標是減少進入障礙、建立混合實境應用程式，以及回饋伴著我們成長的社群。</span><span class="sxs-lookup"><span data-stu-id="b4480-113">The project is aimed at reducing barriers to entry, creating mixed reality applications, and contributing back to the community as we all grow.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="b4480-114">試用我們的 MRTK 教學課程</span><span class="sxs-lookup"><span data-stu-id="b4480-114">Try out our MRTK tutorials</span></span>](./tutorials/mr-learning-base-02.md?tabs=winxr)

<span data-ttu-id="b4480-115">如需詳細的功能詳細資料，請參閱 [MRTK 的檔](/windows/mixed-reality/mrtk-unity) 。</span><span class="sxs-lookup"><span data-stu-id="b4480-115">Take a look at [MRTK's documentation](/windows/mixed-reality/mrtk-unity) for more feature details.</span></span>

## <a name="manual-setup-without-mrtk"></a><span data-ttu-id="b4480-116">手動設定而不 MRTK</span><span class="sxs-lookup"><span data-stu-id="b4480-116">Manual setup without MRTK</span></span>

<span data-ttu-id="b4480-117">如果您的目標是 Desktop VR，建議您在新的 Unity 專案上使用預設選取的電腦獨立平臺：</span><span class="sxs-lookup"><span data-stu-id="b4480-117">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![在 unity 編輯器中開啟 [組建設定] 視窗的螢幕擷取畫面，其中已醒目提示 [電腦]、[Mac & 獨立平臺](images/wmr-config-img-3.png)

<span data-ttu-id="b4480-119">如果您的目標是 HoloLens 2，則必須切換至通用 Windows 平臺：</span><span class="sxs-lookup"><span data-stu-id="b4480-119">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1.  <span data-ttu-id="b4480-120">選取 [檔案 **> 組建設定 ...** ]</span><span class="sxs-lookup"><span data-stu-id="b4480-120">Select **File > Build Settings...**</span></span>
2.  <span data-ttu-id="b4480-121">選取 [平臺] 清單中的 [**通用 Windows 平臺**]，然後選取 [**切換平臺**]</span><span class="sxs-lookup"><span data-stu-id="b4480-121">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3.  <span data-ttu-id="b4480-122">將 **架構** 設定為 **ARM 64**</span><span class="sxs-lookup"><span data-stu-id="b4480-122">Set **Architecture** to **ARM 64**</span></span>
4.  <span data-ttu-id="b4480-123">將 **目標裝置** 設定為 **HoloLens**</span><span class="sxs-lookup"><span data-stu-id="b4480-123">Set **Target device** to **HoloLens**</span></span>
5.  <span data-ttu-id="b4480-124">將 **組建類型** 設定為 **D3D**</span><span class="sxs-lookup"><span data-stu-id="b4480-124">Set **Build Type** to **D3D**</span></span>
6.  <span data-ttu-id="b4480-125">將 **UWP SDK** 設定為 **最新安裝**</span><span class="sxs-lookup"><span data-stu-id="b4480-125">Set **UWP SDK** to **Latest installed**</span></span>
7.  <span data-ttu-id="b4480-126">將 **組建** 設定設為 **發行** ，因為 Debug 有已知的效能問題</span><span class="sxs-lookup"><span data-stu-id="b4480-126">Set **Build configuration** to **Release** because there are known performance issues with Debug</span></span>

![在 unity 編輯器中開啟 [組建設定] 視窗的螢幕擷取畫面，其中已醒目提示通用 Windows 平臺](images/wmr-config-img-4.png)

<span data-ttu-id="b4480-128">設定您的平臺之後，您需要讓 Unity 知道在匯出時建立一個 [沉浸式視圖](../../design/app-views.md) ，而不是2d 視圖：</span><span class="sxs-lookup"><span data-stu-id="b4480-128">After setting your platform, you need to let Unity know to create an [immersive view](../../design/app-views.md) instead of a 2D view when exported:</span></span>

1. <span data-ttu-id="b4480-129">在 Unity 編輯器中，流覽至 [**編輯 > 專案設定**]，然後選取 [ **XR 外掛程式管理**]</span><span class="sxs-lookup"><span data-stu-id="b4480-129">In the Unity Editor, navigate to **Edit > Project settings** and select **XR Plugin Management**</span></span>

2. <span data-ttu-id="b4480-130">選取 [**安裝 XR 外掛程式管理**]</span><span class="sxs-lookup"><span data-stu-id="b4480-130">Select **Install XR Plugin Management**</span></span>

![醒目提示 XR 外掛程式管理的 unity 編輯器中開啟之 [專案設定] 視窗的螢幕擷取畫面](images/wmr-config-img-5.png)

3. <span data-ttu-id="b4480-132">選取 [ **啟動時初始化 XR** ] 和 **Windows Mixed Reality**</span><span class="sxs-lookup"><span data-stu-id="b4480-132">Select **Initialize XR on Startup** and **Windows Mixed Reality**</span></span>

![醒目提示 XR 外掛程式管理的 unity 編輯器中開啟之 [專案設定] 視窗的螢幕擷取畫面](images/wmr-config-img-7.png)

4. <span data-ttu-id="b4480-134">展開 [ **XR 外掛程式管理** ] 區段，然後選取 [ **通用 Windows 平臺設定** ] 索引標籤</span><span class="sxs-lookup"><span data-stu-id="b4480-134">Expand the **XR Plug-in Management** section and select **Univeral Windows Platform Settings** tab</span></span>
5. <span data-ttu-id="b4480-135">如果您使用 Unity 2020 或更新版本，您會看到檢查 **OpenXR** 或 **Windows Mixed Reality** 的選項。</span><span class="sxs-lookup"><span data-stu-id="b4480-135">If you're using Unity 2020 or later, you'll see the options to check **OpenXR** or **Windows Mixed Reality**.</span></span> 
    * <span data-ttu-id="b4480-136">您可以選擇任一執行時間。</span><span class="sxs-lookup"><span data-stu-id="b4480-136">You can choose either runtime.</span></span>  <span data-ttu-id="b4480-137">如果您要特別針對 HoloLens 2 或 HP 回條 G2 進行開發，並決定嘗試 **OpenXR**，請選取 [OpenXR] 方塊，並查看我們的指南，以 [使用 Unity 的 Mixed Reality OpenXR 外掛程式](openxr-getting-started.md) ，以在返回本教學課程之前，為這些裝置正確設定</span><span class="sxs-lookup"><span data-stu-id="b4480-137">If you're specifically developing for the HoloLens 2 or the HP Reverb G2 and decide to try the **OpenXR**, select the OpenXR box and review our guide to [Using the Mixed Reality OpenXR Plugin for Unity](openxr-getting-started.md) to get yourself set up correctly for these devices before returning to this tutorial</span></span>

> [!NOTE]
> <span data-ttu-id="b4480-138">從 Unity 2020 LTS 開始，Microsoft 正採用 OpenXR 進行開發。</span><span class="sxs-lookup"><span data-stu-id="b4480-138">Starting in Unity 2020 LTS, Microsoft is embracing development with OpenXR.</span></span>  <span data-ttu-id="b4480-139">當我們遷移至此路徑時，在 Unity 2021.1 中，Windows XR 外掛程式將會被取代，並在2021.2 中移除，讓 OpenXR 唯一支援的路徑。</span><span class="sxs-lookup"><span data-stu-id="b4480-139">As we migrate to this path, in Unity 2021.1 the Windows XR plugin will be deprecated and removed in 2021.2 making OpenXR the only supported path.</span></span> <span data-ttu-id="b4480-140">您可以在中找到更多有關 [使用 Mixed Reality OpenXR 外掛程式](openxr-getting-started.md)的資訊。</span><span class="sxs-lookup"><span data-stu-id="b4480-140">You can find more information in [Using the Mixed Reality OpenXR plugin](openxr-getting-started.md).</span></span>

6. <span data-ttu-id="b4480-141">如果您決定選擇 **Windows Mixed Reality** 外掛程式，請檢查所有方塊，並將 **深度提交模式** 設定為 **深度16位**</span><span class="sxs-lookup"><span data-stu-id="b4480-141">If you decide to choose the **Windows Mixed Reality** plugin, check all boxes and set **Depth Submission Mode** to **Depth 16 Bit**</span></span>

![在 unity 編輯器中開啟的 [專案設定] 視窗的螢幕擷取畫面，其中已醒目提示 Windows Mixed Reality 區段](images/wmr-config-img-8.png)