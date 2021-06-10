---
title: 使用舊版內建 XR 支援
description: 瞭解如何使用舊版內建 XR 支援，在不使用 MRTK 的情況下設定 Unity 專案。
author: hferrone
ms.author: alexturn
ms.date: 03/26/2021
ms.topic: article
keywords: Unity，混合的現實，開發，使用者入門，新專案，Windows Mixed Reality，UWP，XR，效能，舊版，mrtk
ms.openlocfilehash: b5faa48ec913c5095b12361318729b6f14276f30
ms.sourcegitcommit: 719682f70a75f732b573442fae8987be1acaaf19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2021
ms.locfileid: "110743498"
---
# <a name="using-legacy-built-in-xr-support"></a><span data-ttu-id="9e211-104">使用舊版內建 XR 支援</span><span class="sxs-lookup"><span data-stu-id="9e211-104">Using Legacy built-in XR support</span></span>

## <a name="setting-up-your-project-with-mrtk"></a><span data-ttu-id="9e211-105">使用 MRTK 設定您的專案</span><span class="sxs-lookup"><span data-stu-id="9e211-105">Setting up your project with MRTK</span></span>

<span data-ttu-id="9e211-106">適用于 Unity 的 MRTK 會提供跨平臺輸入系統、基礎元件，以及空間互動的常見組建區塊。</span><span class="sxs-lookup"><span data-stu-id="9e211-106">MRTK for Unity provides a cross-platform input system, foundational components, and common building blocks for spatial interactions.</span></span> <span data-ttu-id="9e211-107">MRTK 第 2 版主要用於加速開發適用於 Microsoft HoloLens、Windows Mixed Reality 沈浸式 (VR) 頭戴裝置和 OpenVR 平台的應用程式。</span><span class="sxs-lookup"><span data-stu-id="9e211-107">MRTK version 2 intends to speed up application development for Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets, and OpenVR platform.</span></span> <span data-ttu-id="9e211-108">此專案的目標是減少進入障礙、建立混合實境應用程式，以及回饋伴著我們成長的社群。</span><span class="sxs-lookup"><span data-stu-id="9e211-108">The project is aimed at reducing barriers to entry, creating mixed reality applications, and contributing back to the community as we all grow.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="9e211-109">試用我們的 MRTK 教學課程</span><span class="sxs-lookup"><span data-stu-id="9e211-109">Try out our MRTK tutorials</span></span>](./tutorials/mr-learning-base-02.md?tabs=wsa)

<span data-ttu-id="9e211-110">如需詳細的功能詳細資料，請參閱 [MRTK 的檔](/windows/mixed-reality/mrtk-unity) 。</span><span class="sxs-lookup"><span data-stu-id="9e211-110">Take a look at [MRTK's documentation](/windows/mixed-reality/mrtk-unity) for more feature details.</span></span>

## <a name="manual-setup-without-mrtk"></a><span data-ttu-id="9e211-111">手動設定而不 MRTK</span><span class="sxs-lookup"><span data-stu-id="9e211-111">Manual setup without MRTK</span></span>

<span data-ttu-id="9e211-112">如果您的目標是 Desktop VR，建議您在新的 Unity 專案上使用預設選取的電腦獨立平臺：</span><span class="sxs-lookup"><span data-stu-id="9e211-112">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![在 unity 編輯器中開啟 [組建設定] 視窗的螢幕擷取畫面，其中已醒目提示 [電腦]、[Mac & 獨立平臺](images/wmr-config-img-3.png)

<span data-ttu-id="9e211-114">如果您的目標是 HoloLens 2，則必須切換至通用 Windows 平臺：</span><span class="sxs-lookup"><span data-stu-id="9e211-114">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1.  <span data-ttu-id="9e211-115">選取 [檔案 **> 組建設定 ...** ]</span><span class="sxs-lookup"><span data-stu-id="9e211-115">Select **File > Build Settings...**</span></span>
2.  <span data-ttu-id="9e211-116">選取 [平臺] 清單中的 [**通用 Windows 平臺**]，然後選取 [**切換平臺**]</span><span class="sxs-lookup"><span data-stu-id="9e211-116">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3.  <span data-ttu-id="9e211-117">將 **架構** 設定為 **ARM 64**</span><span class="sxs-lookup"><span data-stu-id="9e211-117">Set **Architecture** to **ARM 64**</span></span>
4.  <span data-ttu-id="9e211-118">將 **目標裝置** 設定為 **HoloLens**</span><span class="sxs-lookup"><span data-stu-id="9e211-118">Set **Target device** to **HoloLens**</span></span>
5.  <span data-ttu-id="9e211-119">將 **組建類型** 設定為 **D3D**</span><span class="sxs-lookup"><span data-stu-id="9e211-119">Set **Build Type** to **D3D**</span></span>
6.  <span data-ttu-id="9e211-120">將 **UWP SDK** 設定為 **最新安裝**</span><span class="sxs-lookup"><span data-stu-id="9e211-120">Set **UWP SDK** to **Latest installed**</span></span>
7.  <span data-ttu-id="9e211-121">將 **組建** 設定設為 **發行** ，因為 Debug 有已知的效能問題</span><span class="sxs-lookup"><span data-stu-id="9e211-121">Set **Build configuration** to **Release** because there are known performance issues with Debug</span></span>

![在 unity 編輯器中開啟 [組建設定] 視窗的螢幕擷取畫面，其中已醒目提示通用 Windows 平臺](images/wmr-config-img-4.png)

<span data-ttu-id="9e211-123">設定您的平臺之後，您需要讓 Unity 知道在匯出時建立一個 [沉浸式視圖](../../design/app-views.md) ，而不是2d 視圖。</span><span class="sxs-lookup"><span data-stu-id="9e211-123">After setting your platform, you need to let Unity know to create an [immersive view](../../design/app-views.md) instead of a 2D view when exported.</span></span>

> [!CAUTION]
> <span data-ttu-id="9e211-124">Unity 2019 中的舊版 XR 已被取代，並已在 Unity 2020 中移除。</span><span class="sxs-lookup"><span data-stu-id="9e211-124">Legacy XR is deprecated in Unity 2019 and removed in Unity 2020.</span></span>

1. <span data-ttu-id="9e211-125">從組建設定開啟 **播放機設定** ... **視窗** 並展開 [ **XR 設定** ] 群組</span><span class="sxs-lookup"><span data-stu-id="9e211-125">Open **Player Settings...** from the **Build Settings... window** and expand the **XR Settings** group</span></span>
2. <span data-ttu-id="9e211-126">在 [ **XR 設定** ] 區段中，選取 [ **支援的虛擬實境** 新增虛擬實境裝置] 清單</span><span class="sxs-lookup"><span data-stu-id="9e211-126">In the **XR Settings** section, select **Virtual Reality Supported** to add the Virtual Reality Devices list</span></span>
3. <span data-ttu-id="9e211-127">將 **深度格式** 設定為 **16 位深度** ，並啟用 **深度緩衝區共用**</span><span class="sxs-lookup"><span data-stu-id="9e211-127">Set **Depth Format** to **16-bit Depth** and enable **Depth Buffer Sharing**</span></span>
4. <span data-ttu-id="9e211-128">將 **身歷聲轉譯模式** 設定為 **單一傳遞實例**</span><span class="sxs-lookup"><span data-stu-id="9e211-128">Set **Stereo Rendering Mode** to **Single Pass Instance**</span></span>
5. <span data-ttu-id="9e211-129">如果您想要使用全像攝影的遠端處理，請選取 [不 **支援的 WSA** 全像</span><span class="sxs-lookup"><span data-stu-id="9e211-129">Select **WSA Holographic Remoting Supported** if you'd like to use Holographic remoting</span></span> 

![醒目提示 [播放程式設定] 區段的 [在 unity 編輯器中開啟專案設定] 視窗的螢幕擷取畫面](images/wmr-config-img-9.png)