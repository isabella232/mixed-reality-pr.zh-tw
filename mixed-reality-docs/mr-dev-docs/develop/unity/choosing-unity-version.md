---
title: 選擇 Unity 版本和 XR 外掛程式
description: 隨時掌握最新的 Unity 與 XR 外掛程式建議，以進行 HoloLens 應用程式開發。
author: hferrone
ms.author: v-hferrone
ms.date: 06/24/2021
ms.topic: article
keywords: mixedrealitytoolkit、mixedrealitytoolkit-unity、mixed reality 耳機、windows mixed reality 耳機、虛擬實境耳機、unity
ms.openlocfilehash: 646a0ec3b3b332b038509cba39caa085c1590c1a
ms.sourcegitcommit: 593e8f80297ac0b5eccb2488d3f333885eab9adf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2021
ms.locfileid: "112921420"
---
# <a name="choosing-a-unity-version-and-xr-plugin"></a><span data-ttu-id="4a513-104">選擇 Unity 版本和 XR 外掛程式</span><span class="sxs-lookup"><span data-stu-id="4a513-104">Choosing a Unity version and XR plugin</span></span>

<span data-ttu-id="4a513-105">雖然我們目前 **建議您安裝 unity 2020.3 LTS 與混合現實開發的最新 Mixed Reality OpenXR 外掛程式** ，但您也可以使用其他 Unity 設定來建立應用程式。</span><span class="sxs-lookup"><span data-stu-id="4a513-105">While we currently **recommend installing Unity 2020.3 LTS with the latest Mixed Reality OpenXR plugin** for Mixed Reality development, you can build apps with other Unity configurations as well.</span></span>

## <a name="unity-20203-lts-recommended"></a><span data-ttu-id="4a513-106">Unity 2020.3 LTS (建議的) </span><span class="sxs-lookup"><span data-stu-id="4a513-106">Unity 2020.3 LTS (Recommended)</span></span>

<span data-ttu-id="4a513-107">Microsoft 目前針對 HoloLens 2 和 Windows Mixed Reality 開發建議的 Unity 設定是 **unity 2020.3 LTS 與最新的 Mixed Reality OpenXR 外掛程式**。</span><span class="sxs-lookup"><span data-stu-id="4a513-107">Microsoft’s current recommended Unity configuration for HoloLens 2 and Windows Mixed Reality development is **Unity 2020.3 LTS with the latest Mixed Reality OpenXR plugin**.</span></span> <span data-ttu-id="4a513-108">您必須使用 Unity patch release 2020.3.8 f1 或更新版本，以避免早于2020.3 組建的已知效能問題。</span><span class="sxs-lookup"><span data-stu-id="4a513-108">You MUST use Unity patch release 2020.3.8f1 or later to avoid known performance issues with earlier 2020.3 builds.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4a513-109">Unity 2020 不支援以 HoloLens (第1代) 為目標。</span><span class="sxs-lookup"><span data-stu-id="4a513-109">Unity 2020 does not support targeting HoloLens (1st gen).</span></span> <span data-ttu-id="4a513-110">**[Unity 2019 LTS](#unity-20194-lts)** 中仍支援這些耳機，具有舊版內建 XR，可在 UNITY 2019 LTS 的完整生命週期內透過中2022。</span><span class="sxs-lookup"><span data-stu-id="4a513-110">These headsets remain supported in **[Unity 2019 LTS](#unity-20194-lts)** with Legacy Built-in XR for the full lifecycle of Unity 2019 LTS through mid-2022.</span></span>
>
> [!NOTE]
> <span data-ttu-id="4a513-111">某些封裝尚未與 Unity 2020 LTS 中的混合現實專案相容：</span><span class="sxs-lookup"><span data-stu-id="4a513-111">Some packages are not yet compatible with mixed reality projects in Unity 2020 LTS:</span></span>
> 
> * <span data-ttu-id="4a513-112">通用轉譯管線 (URP) 10.5.0 或較舊版本在 HoloLens 2 裝置上有已知的效能問題。</span><span class="sxs-lookup"><span data-stu-id="4a513-112">The Universal Rendering Pipeline (URP) 10.5.0 or older has a known performance issue on HoloLens 2 devices.</span></span> <span data-ttu-id="4a513-113">_(在下一個 URP 版本中修正)_</span><span class="sxs-lookup"><span data-stu-id="4a513-113">_(fixed in the next URP release)_</span></span>
> * <span data-ttu-id="4a513-114">Azure 遠端轉譯尚未隨附支援 Unity 2020 的更新版本。</span><span class="sxs-lookup"><span data-stu-id="4a513-114">Azure Remote Rendering has not yet shipped an updated release supporting Unity 2020.</span></span>
>
> <span data-ttu-id="4a513-115">如果您的 Unity 專案使用通用轉譯管線或 Azure 遠端轉譯，建議您將專案升級至 Unity 2020，直到有可用的更新套件為止。</span><span class="sxs-lookup"><span data-stu-id="4a513-115">If your Unity project uses the Universal Rendering Pipeline or Azure Remote Rendering, we recommend holding off on upgrading your project to Unity 2020 until updated packages are available.</span></span>

<span data-ttu-id="4a513-116">安裝和管理 Unity 的最佳方式是透過 <a href="https://unity3d.com/get-unity/download" target="_blank">Unity 中樞</a>。</span><span class="sxs-lookup"><span data-stu-id="4a513-116">The best way to install and manage Unity is through the <a href="https://unity3d.com/get-unity/download" target="_blank">Unity Hub</a>.</span></span> <span data-ttu-id="4a513-117">安裝之後，請開啟 Unity Hub：</span><span class="sxs-lookup"><span data-stu-id="4a513-117">When it's installed, open Unity Hub:</span></span>

1. <span data-ttu-id="4a513-118">選取 [**安裝**] 索引標籤，然後選擇 [**新增**]</span><span class="sxs-lookup"><span data-stu-id="4a513-118">Select the **Installs** tab and choose **ADD**</span></span>
2. <span data-ttu-id="4a513-119">選取 Unity 2020.3 LTS，然後按 **[下一步]**</span><span class="sxs-lookup"><span data-stu-id="4a513-119">Select Unity 2020.3 LTS and click **Next**</span></span>

![Unity 中樞定新版本](images/unity-hub-img-01.png)

3. <span data-ttu-id="4a513-121">檢查「平臺」底下 **的** 下列元件</span><span class="sxs-lookup"><span data-stu-id="4a513-121">Check following components under **'Platforms'**</span></span>
    * <span data-ttu-id="4a513-122">**通用 Windows 平臺組建支援**</span><span class="sxs-lookup"><span data-stu-id="4a513-122">**Universal Windows Platform Build Support**</span></span>
    * <span data-ttu-id="4a513-123">**Windows Build 支援 (IL2CPP)**</span><span class="sxs-lookup"><span data-stu-id="4a513-123">**Windows Build Support (IL2CPP)**</span></span>

![Unity 通用 Windows 平臺組建支援選項](../images/Unity_Install_Option_UWP.png)

4. <span data-ttu-id="4a513-125">如果您已安裝 Unity 但未安裝這些選項，您可以透過 Unity Hub 中 **的 [新增模組** ] 功能表來新增這些選項：</span><span class="sxs-lookup"><span data-stu-id="4a513-125">If you installed Unity without these options, you can add them through **'Add Modules'** menu in Unity Hub:</span></span>

![Unity Windows Build 支援選項](../images/Unity_Install_Option_UWP2.png)

> [!div class="nextstepaction"]
> [<span data-ttu-id="4a513-127">使用 OpenXR 外掛程式</span><span class="sxs-lookup"><span data-stu-id="4a513-127">Using the OpenXR plugin</span></span>](/windows/mixed-reality/develop/unity/xr-project-setup?tabs=openxr)

> [!NOTE]
> <span data-ttu-id="4a513-128">雖然我們建議您針對所有新的專案使用 OpenXR，但 Unity 2020.3 LTS 也支援 [WINDOWS XR 外掛程式](/windows/mixed-reality/develop/unity/xr-project-setup?tabs=windowsxr)。</span><span class="sxs-lookup"><span data-stu-id="4a513-128">While we recommend using OpenXR for all new projects, Unity 2020.3 LTS also supports the [Windows XR plugin](/windows/mixed-reality/develop/unity/xr-project-setup?tabs=windowsxr).</span></span> <span data-ttu-id="4a513-129">此外掛程式完全受支援，但不會收到 AR Foundation 4.0 支援之類的新功能。</span><span class="sxs-lookup"><span data-stu-id="4a513-129">This plugin is fully supported, although it won't receive new features such as AR Foundation 4.0 support.</span></span>

## <a name="unity-20194-lts"></a><span data-ttu-id="4a513-130">Unity 2019.4 LTS</span><span class="sxs-lookup"><span data-stu-id="4a513-130">Unity 2019.4 LTS</span></span>

<span data-ttu-id="4a513-131">如果您需要使用 Unity 2019，您可以使用 **unity 2019 LTS 搭配舊版內建 XR**。</span><span class="sxs-lookup"><span data-stu-id="4a513-131">If you need to use Unity 2019, you can use **Unity 2019 LTS with Legacy Built-in XR**.</span></span> <span data-ttu-id="4a513-132">若要開始使用 Unity 2019.4 LTS 中的舊版內建 XR，請按一下這裡：</span><span class="sxs-lookup"><span data-stu-id="4a513-132">To get started with Legacy Built-in XR in Unity 2019.4 LTS, click here:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="4a513-133">設定舊版內建 XR</span><span class="sxs-lookup"><span data-stu-id="4a513-133">Set up Legacy Built-in XR</span></span>](/windows/mixed-reality/develop/unity/xr-project-setup?tabs=legacy)

> [!NOTE]
> <span data-ttu-id="4a513-134">Unity 已淘汰自 Unity 2019 起的舊版內建 XR 支援。</span><span class="sxs-lookup"><span data-stu-id="4a513-134">Unity has deprecated its Legacy Built-in XR support as of Unity 2019.</span></span>  <span data-ttu-id="4a513-135">雖然 Unity 2019 提供新的 XR 外掛程式架構，但 Microsoft 目前不建議在 Unity 2019 中使用該路徑，因為 Azure 空間錨點與 AR Foundation 2 不相容。</span><span class="sxs-lookup"><span data-stu-id="4a513-135">While Unity 2019 does offer a new XR Plug-in framework, Microsoft is not currently recommending that path in Unity 2019 due to Azure Spatial Anchors incompatibilities with AR Foundation 2.</span></span>  <span data-ttu-id="4a513-136">在 Unity 2020 中，XR 外掛程式架構內支援 Azure 空間錨點。</span><span class="sxs-lookup"><span data-stu-id="4a513-136">In Unity 2020, Azure Spatial Anchors is supported within the XR Plug-in framework.</span></span>

<span data-ttu-id="4a513-137">如果您正在開發適用于 HoloLens (第一代) 的應用程式，則 Unity 2019 LTS 會持續支援這些耳機，並具備舊版內建 XR，可在 Unity 2019 LTS 的完整生命週期內透過中2022。</span><span class="sxs-lookup"><span data-stu-id="4a513-137">If you are developing apps for HoloLens (1st gen), these headsets remain supported in Unity 2019 LTS with Legacy Built-in XR for the full lifecycle of Unity 2019 LTS through mid-2022.</span></span>

## <a name="unity-20211"></a><span data-ttu-id="4a513-138">Unity 2021。1</span><span class="sxs-lookup"><span data-stu-id="4a513-138">Unity 2021.1</span></span>

<span data-ttu-id="4a513-139">如果您正在嘗試早期的 **Unity 2021.1** 組建，您應該移至 **OpenXR 外掛程式**，因為 Windows XR 外掛程式已在該處淘汰。</span><span class="sxs-lookup"><span data-stu-id="4a513-139">If you are trying out early **Unity 2021.1** builds, you should move forward to the **OpenXR plugin**, as the Windows XR plugin is deprecated there.</span></span>  <span data-ttu-id="4a513-140">從 Unity 2021.2 開始，OpenXR 外掛程式將是唯一開發混合現實的途徑，因為 Windows XR 外掛程式將不再受到支援。</span><span class="sxs-lookup"><span data-stu-id="4a513-140">Starting in Unity 2021.2, the OpenXR plugin will be the only path for Mixed Reality development, as the Windows XR plugin will no longer be supported.</span></span>

## <a name="unity-20184-lts"></a><span data-ttu-id="4a513-141">Unity 2018.4 LTS</span><span class="sxs-lookup"><span data-stu-id="4a513-141">Unity 2018.4 LTS</span></span>

<span data-ttu-id="4a513-142">如果您已經有使用 Unity 2018.4 LTS 的專案，則您的 Unity 引擎會在發行後的2年繼續受到支援。</span><span class="sxs-lookup"><span data-stu-id="4a513-142">If you already have a project using Unity 2018.4 LTS, your Unity engine continues to be supported for 2 years after its release.</span></span>  <span data-ttu-id="4a513-143">Unity 2018 LTS 將于2021年春季結束服務。</span><span class="sxs-lookup"><span data-stu-id="4a513-143">Unity 2018 LTS will reach end of service in the spring of 2021.</span></span>
