---
title: 選擇 Unity 版本和 XR 外掛程式
description: 隨時掌握最新的 Unity 和 XR 外掛程式建議，以 HoloLens 應用程式開發。
author: hferrone
ms.author: v-hferrone
ms.date: 06/24/2021
ms.topic: article
keywords: mixedrealitytoolkit、mixedrealitytoolkit-unity、mixed reality 耳機、windows mixed reality 耳機、虛擬實境耳機、unity
ms.openlocfilehash: c69576e991f3fe32ae69fce10069ecdae65b3f9a
ms.sourcegitcommit: e380d56f5504be4e4f069394a58cf0147eb33b66
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2021
ms.locfileid: "113603679"
---
# <a name="choosing-a-unity-version-and-xr-plugin"></a><span data-ttu-id="141d1-104">選擇 Unity 版本和 XR 外掛程式</span><span class="sxs-lookup"><span data-stu-id="141d1-104">Choosing a Unity version and XR plugin</span></span>

<span data-ttu-id="141d1-105">雖然我們目前 **建議您安裝 unity 2020.3 LTS 與混合現實開發的最新 Mixed Reality OpenXR 外掛程式** ，但您也可以使用其他 Unity 設定來建立應用程式。</span><span class="sxs-lookup"><span data-stu-id="141d1-105">While we currently **recommend installing Unity 2020.3 LTS with the latest Mixed Reality OpenXR plugin** for Mixed Reality development, you can build apps with other Unity configurations as well.</span></span>

## <a name="unity-20203-lts-recommended"></a><span data-ttu-id="141d1-106">Unity 2020.3 LTS (建議的) </span><span class="sxs-lookup"><span data-stu-id="141d1-106">Unity 2020.3 LTS (Recommended)</span></span>

<span data-ttu-id="141d1-107">Microsoft 目前針對 HoloLens 2 和 Windows Mixed Reality 開發建議的 unity 設定是 **unity 2020.3 LTS 與最新的 Mixed Reality OpenXR 外掛程式**。</span><span class="sxs-lookup"><span data-stu-id="141d1-107">Microsoft’s current recommended Unity configuration for HoloLens 2 and Windows Mixed Reality development is **Unity 2020.3 LTS with the latest Mixed Reality OpenXR plugin**.</span></span> <span data-ttu-id="141d1-108">您 **必須** 使用 Unity patch release 2020.3.8 f1 或更新版本，以避免早于2020.3 組建的已知效能問題。</span><span class="sxs-lookup"><span data-stu-id="141d1-108">You **must** use Unity patch release 2020.3.8f1 or later to avoid known performance issues with earlier 2020.3 builds.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="141d1-109">Unity 2020 不支援將 HoloLens 的目標設為 (第一代) 。</span><span class="sxs-lookup"><span data-stu-id="141d1-109">Unity 2020 does not support targeting HoloLens (1st gen).</span></span> <span data-ttu-id="141d1-110">**[Unity 2019 LTS](#unity-20194-lts)** 中仍支援這些耳機，具有舊版內建 XR，可在 UNITY 2019 LTS 的完整生命週期內透過中2022。</span><span class="sxs-lookup"><span data-stu-id="141d1-110">These headsets remain supported in **[Unity 2019 LTS](#unity-20194-lts)** with Legacy Built-in XR for the full lifecycle of Unity 2019 LTS through mid-2022.</span></span>

<span data-ttu-id="141d1-111">安裝和管理 Unity 的最佳方式是透過 **Unity 中樞**：</span><span class="sxs-lookup"><span data-stu-id="141d1-111">The best way to install and manage Unity is through the **Unity Hub**:</span></span>

1. <span data-ttu-id="141d1-112">安裝 <a href="https://unity3d.com/get-unity/download" target="_blank">**Unity Hub**</a>。</span><span class="sxs-lookup"><span data-stu-id="141d1-112">Install <a href="https://unity3d.com/get-unity/download" target="_blank">**Unity Hub**</a>.</span></span>
2. <span data-ttu-id="141d1-113">選取 [ **安裝** ] 索引標籤，然後選擇 [ **新增**]。</span><span class="sxs-lookup"><span data-stu-id="141d1-113">Select the **Installs** tab and choose **Add**.</span></span>
3. <span data-ttu-id="141d1-114">選取 **Unity 2020.3 LTS** ，然後按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="141d1-114">Select **Unity 2020.3 LTS** and click **Next**.</span></span>

![Unity 中樞安裝新版本](images/unity-hub-img-01.png)

4. <span data-ttu-id="141d1-116">檢查「 **平臺**」底下的下列元件：</span><span class="sxs-lookup"><span data-stu-id="141d1-116">Check the following components under **'Platforms'**:</span></span>
    * <span data-ttu-id="141d1-117">**通用 Windows 平臺組建支援**</span><span class="sxs-lookup"><span data-stu-id="141d1-117">**Universal Windows Platform Build Support**</span></span>
    * <span data-ttu-id="141d1-118">**Windows組建支援 (IL2CPP)**</span><span class="sxs-lookup"><span data-stu-id="141d1-118">**Windows Build Support (IL2CPP)**</span></span>

![Unity 通用 Windows 平臺組建支援選項](../images/Unity_Install_Option_UWP.png)

5. <span data-ttu-id="141d1-120">如果您先前已安裝 Unity 但未安裝這些選項，您可以透過 Unity Hub 中 **的 [新增模組** ] 功能表來新增這些選項：</span><span class="sxs-lookup"><span data-stu-id="141d1-120">If you previously installed Unity without these options, you can add them through **'Add Modules'** menu in Unity Hub:</span></span>

![Unity Windows 組建支援選項](../images/Unity_Install_Option_UWP2.png)

<span data-ttu-id="141d1-122">安裝 Unity 2020.3 之後，請開始使用 Mixed Reality OpenXR 外掛程式建立專案或升級現有的專案：</span><span class="sxs-lookup"><span data-stu-id="141d1-122">Once you have Unity 2020.3 installed, get started creating a project or upgrading an existing project using the Mixed Reality OpenXR plugin:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="141d1-123">使用 OpenXR 外掛程式設定您的專案</span><span class="sxs-lookup"><span data-stu-id="141d1-123">Set up your project with the OpenXR plugin</span></span>](xr-project-setup.md?tabs=openxr)

> [!NOTE]
> <span data-ttu-id="141d1-124">雖然我們建議您針對所有新的專案使用 OpenXR，但 Unity 2020.3 LTS 也支援[Windows 的 XR 外掛程式](xr-project-setup.md?tabs=windowsxr)。</span><span class="sxs-lookup"><span data-stu-id="141d1-124">While we recommend using OpenXR for all new projects, Unity 2020.3 LTS also supports the [Windows XR plugin](xr-project-setup.md?tabs=windowsxr).</span></span> <span data-ttu-id="141d1-125">此外掛程式完全受支援，但不會收到 AR Foundation 4.0 支援之類的新功能。</span><span class="sxs-lookup"><span data-stu-id="141d1-125">This plugin is fully supported, although it won't receive new features such as AR Foundation 4.0 support.</span></span>

## <a name="unity-20194-lts"></a><span data-ttu-id="141d1-126">Unity 2019.4 LTS</span><span class="sxs-lookup"><span data-stu-id="141d1-126">Unity 2019.4 LTS</span></span>

<span data-ttu-id="141d1-127">如果您需要使用 Unity 2019，您可以使用 **unity 2019 LTS 搭配舊版內建 XR**。</span><span class="sxs-lookup"><span data-stu-id="141d1-127">If you need to use Unity 2019, you can use **Unity 2019 LTS with Legacy Built-in XR**.</span></span> <span data-ttu-id="141d1-128">若要開始使用 Unity 2019.4 LTS 中的舊版內建 XR，請按一下這裡：</span><span class="sxs-lookup"><span data-stu-id="141d1-128">To get started with Legacy Built-in XR in Unity 2019.4 LTS, click here:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="141d1-129">使用舊版內建 XR 來設定您的專案</span><span class="sxs-lookup"><span data-stu-id="141d1-129">Set up your project with Legacy Built-in XR</span></span>](xr-project-setup.md?tabs=legacy)

> [!NOTE]
> <span data-ttu-id="141d1-130">Unity 已淘汰自 Unity 2019 起的舊版內建 XR 支援。</span><span class="sxs-lookup"><span data-stu-id="141d1-130">Unity has deprecated its Legacy Built-in XR support as of Unity 2019.</span></span>  <span data-ttu-id="141d1-131">雖然 Unity 2019 提供新的 XR 外掛程式架構，但 Microsoft 目前不建議在 Unity 2019 中使用該路徑，因為 Azure 空間錨點與 AR Foundation 2 不相容。</span><span class="sxs-lookup"><span data-stu-id="141d1-131">While Unity 2019 does offer a new XR Plug-in framework, Microsoft is not currently recommending that path in Unity 2019 due to Azure Spatial Anchors incompatibilities with AR Foundation 2.</span></span>  <span data-ttu-id="141d1-132">在 Unity 2020 中，XR 外掛程式架構內支援 Azure 空間錨點。</span><span class="sxs-lookup"><span data-stu-id="141d1-132">In Unity 2020, Azure Spatial Anchors is supported within the XR Plug-in framework.</span></span>

<span data-ttu-id="141d1-133">如果您正在開發適用于 HoloLens (第1代) 的應用程式，則 unity 2019 LTS 會持續支援這些耳機，並具備舊版內建 XR，可在 unity 2019 LTS 的完整生命週期內透過中2022。</span><span class="sxs-lookup"><span data-stu-id="141d1-133">If you are developing apps for HoloLens (1st gen), these headsets remain supported in Unity 2019 LTS with Legacy Built-in XR for the full lifecycle of Unity 2019 LTS through mid-2022.</span></span>

## <a name="unity-20212"></a><span data-ttu-id="141d1-134">Unity 2021。2</span><span class="sxs-lookup"><span data-stu-id="141d1-134">Unity 2021.2</span></span>

<span data-ttu-id="141d1-135">如果您要試用早期的 **Unity 2021.2** 組建，請從 [**Mixed Reality OpenXR 外掛程式**](xr-project-setup.md?tabs=openxr)開始著手。</span><span class="sxs-lookup"><span data-stu-id="141d1-135">If you are trying out early **Unity 2021.2** builds, get started with the [**Mixed Reality OpenXR plugin**](xr-project-setup.md?tabs=openxr).</span></span> <span data-ttu-id="141d1-136">OpenXR 外掛程式是 unity 2021.2 和更新版本中混合現實開發的唯一途徑，因為支援 Windows XR 外掛程式的最終 unity 版本是 Unity 2021.1。</span><span class="sxs-lookup"><span data-stu-id="141d1-136">The OpenXR plugin is the only path for mixed reality development in Unity 2021.2 and later, as the final Unity version to support the Windows XR plugin was Unity 2021.1.</span></span>

## <a name="unity-20184-lts"></a><span data-ttu-id="141d1-137">Unity 2018.4 LTS</span><span class="sxs-lookup"><span data-stu-id="141d1-137">Unity 2018.4 LTS</span></span>

<span data-ttu-id="141d1-138">Unity 2018.4 LTS 已達到 Unity 的兩年 Long-Term 支援期間的結尾，但因為您的專案將會繼續執行，所以不會再接收來自 Unity 的更新。</span><span class="sxs-lookup"><span data-stu-id="141d1-138">Unity 2018.4 LTS has reached the end of Unity's two-year Long-Term Support window and is no longer receiving updates from Unity, although your projects will continue to run.</span></span>

<span data-ttu-id="141d1-139">如果您有 Unity 2018 專案，您應該考慮規劃向前遷移至 Unity 2020.3 LTS 和 Mixed Reality OpenXR 外掛程式。</span><span class="sxs-lookup"><span data-stu-id="141d1-139">If you have a Unity 2018 project, you should consider planning for a migration forward to Unity 2020.3 LTS and the Mixed Reality OpenXR plugin.</span></span>