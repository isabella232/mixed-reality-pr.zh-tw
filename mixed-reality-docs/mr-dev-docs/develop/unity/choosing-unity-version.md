---
title: 選擇 Unity 版本和 XR 外掛程式
description: 隨時掌握最新的 Unity 與 XR 外掛程式建議，以進行 HoloLens 應用程式開發。
author: hferrone
ms.author: v-hferrone
ms.date: 03/26/2021
ms.topic: article
keywords: mixedrealitytoolkit、mixedrealitytoolkit-unity、mixed reality 耳機、windows mixed reality 耳機、虛擬實境耳機、unity
ms.openlocfilehash: b8f5f0131da811393ee053541e0c2fa0c735472e
ms.sourcegitcommit: 6272d086a2856e8b514a719e1f9e3b78554be5be
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/30/2021
ms.locfileid: "105938115"
---
# <a name="choosing-a-unity-version-and-xr-plugin"></a><span data-ttu-id="aba55-104">選擇 Unity 版本和 XR 外掛程式</span><span class="sxs-lookup"><span data-stu-id="aba55-104">Choosing a Unity version and XR plugin</span></span>

<span data-ttu-id="aba55-105">雖然我們目前 **建議您安裝 unity 2019.4 LTS，並使用舊版內建 XR** 進行混合現實開發，但您也可以使用其他 Unity 設定來建立應用程式。</span><span class="sxs-lookup"><span data-stu-id="aba55-105">While we currently **recommend installing Unity 2019.4 LTS and using Legacy Built-in XR** for Mixed Reality development, you can build apps with other Unity configurations as well.</span></span>

## <a name="unity-20194-lts-recommended"></a><span data-ttu-id="aba55-106">Unity 2019.4 LTS (建議的) </span><span class="sxs-lookup"><span data-stu-id="aba55-106">Unity 2019.4 LTS (Recommended)</span></span>

<span data-ttu-id="aba55-107">Microsoft 目前針對 HoloLens 2 和 Windows Mixed Reality 開發建議的 Unity 設定，是 **使用舊版內建 XR 支援的 unity 2019.4 LTS** 。</span><span class="sxs-lookup"><span data-stu-id="aba55-107">Microsoft’s current recommended Unity configuration for HoloLens 2 and Windows Mixed Reality development is **Unity 2019.4 LTS using Legacy Built-in XR** support.</span></span>

<span data-ttu-id="aba55-108">安裝和管理 Unity 的最佳方式是透過 <a href="https://unity3d.com/get-unity/download" target="_blank">[Unity 中樞]</a>。</span><span class="sxs-lookup"><span data-stu-id="aba55-108">The best way to install and manage Unity is through the <a href="https://unity3d.com/get-unity/download" target="_blank">[Unity Hub]</a>.</span></span> <span data-ttu-id="aba55-109">安裝之後，請開啟 Unity Hub：</span><span class="sxs-lookup"><span data-stu-id="aba55-109">When it's installed, open Unity Hub:</span></span>

1. <span data-ttu-id="aba55-110">選取 [**安裝**] 索引標籤，然後選擇 [**新增**]</span><span class="sxs-lookup"><span data-stu-id="aba55-110">Select the **Installs** tab and choose **ADD**</span></span>
2. <span data-ttu-id="aba55-111">選取 Unity 2019.4 LTS，然後按 **[下一步]**</span><span class="sxs-lookup"><span data-stu-id="aba55-111">Select Unity 2019.4 LTS and click **Next**</span></span>

![Unity 中樞定新版本](images/unity-hub-img-01.png)

3. <span data-ttu-id="aba55-113">檢查「平臺」底下 **的** 下列元件</span><span class="sxs-lookup"><span data-stu-id="aba55-113">Check following components under **'Platforms'**</span></span>
    * <span data-ttu-id="aba55-114">**通用 Windows 平臺組建支援**</span><span class="sxs-lookup"><span data-stu-id="aba55-114">**Universal Windows Platform Build Support**</span></span> 
    * <span data-ttu-id="aba55-115">**Windows Build 支援 (IL2CPP)**</span><span class="sxs-lookup"><span data-stu-id="aba55-115">**Windows Build Support (IL2CPP)**</span></span>

![Unity 通用 Windows 平臺組建支援選項](../images/Unity_Install_Option_UWP.png)

4. <span data-ttu-id="aba55-117">如果您已安裝 Unity 但未安裝這些選項，您可以透過 Unity Hub 中 **的 [新增模組** ] 功能表來新增這些選項：</span><span class="sxs-lookup"><span data-stu-id="aba55-117">If you installed Unity without these options, you can add them through **'Add Modules'** menu in Unity Hub:</span></span>

![Unity Windows Build 支援選項](../images/Unity_Install_Option_UWP2.png)

<span data-ttu-id="aba55-119">若要開始使用 Unity 2019.4 LTS 中的舊版內建 XR，請按一下這裡：</span><span class="sxs-lookup"><span data-stu-id="aba55-119">To get started with Legacy Built-in XR in Unity 2019.4 LTS, click here:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="aba55-120">設定舊版內建 XR</span><span class="sxs-lookup"><span data-stu-id="aba55-120">Set up Legacy Built-in XR</span></span>](legacy-xr-support.md)

> [!NOTE]
> <span data-ttu-id="aba55-121">Unity 已淘汰自 Unity 2019 起的舊版內建 XR 支援。</span><span class="sxs-lookup"><span data-stu-id="aba55-121">Unity has deprecated its Legacy Built-in XR support as of Unity 2019.</span></span>  <span data-ttu-id="aba55-122">雖然 Unity 2019 提供新的 XR 外掛程式架構，但 Microsoft 目前不建議在 Unity 2019 中使用該路徑，因為 Azure 空間錨點與 AR Foundation 2 不相容。</span><span class="sxs-lookup"><span data-stu-id="aba55-122">While Unity 2019 does offer a new XR Plug-in framework, Microsoft is not currently recommending that path in Unity 2019 due to Azure Spatial Anchors incompatibilities with AR Foundation 2.</span></span>  <span data-ttu-id="aba55-123">在 Unity 2020 中，XR 外掛程式架構內支援 Azure 空間錨點。</span><span class="sxs-lookup"><span data-stu-id="aba55-123">In Unity 2020, Azure Spatial Anchors is supported within the XR Plug-in framework.</span></span>

<span data-ttu-id="aba55-124">如果您正在開發適用于 HoloLens (第一代) 的應用程式，則 Unity 2019 LTS 會持續支援這些耳機，並具備舊版內建 XR，可在 Unity 2019 LTS 的完整生命週期內透過中2022。</span><span class="sxs-lookup"><span data-stu-id="aba55-124">If you are developing apps for HoloLens (1st gen), these headsets remain supported in Unity 2019 LTS with Legacy Built-in XR for the full lifecycle of Unity 2019 LTS through mid-2022.</span></span>

## <a name="unity-20203-lts"></a><span data-ttu-id="aba55-125">Unity 2020.3 LTS</span><span class="sxs-lookup"><span data-stu-id="aba55-125">Unity 2020.3 LTS</span></span> 

<span data-ttu-id="aba55-126">如果您使用的是 **Unity 2020.3 LTS**，您可以使用 **Windows XR 外掛程式** 來開發 HoloLens 2 和 Windows Mixed Reality 應用程式。</span><span class="sxs-lookup"><span data-stu-id="aba55-126">If you’re using **Unity 2020.3 LTS**, you can use the **Windows XR plugin** to develop HoloLens 2 and Windows Mixed Reality applications.</span></span>

<span data-ttu-id="aba55-127">不過，有一些已知的問題會影響全息圖穩定性以及 HoloLens 2 上的其他功能：</span><span class="sxs-lookup"><span data-stu-id="aba55-127">However, there are known issues that affect hologram stability and other features on HoloLens 2:</span></span> 

* <span data-ttu-id="aba55-128">深度緩衝區提交回歸在最近的 Unity 2020 組建中，這會導致嚴重的全息圖不穩定。</span><span class="sxs-lookup"><span data-stu-id="aba55-128">Depth buffer submission has regressed in recent Unity 2020 builds, which results in severe hologram instability.</span></span>
* <span data-ttu-id="aba55-129">使用通用 Windows 平臺組建目標的全像應用程式遠端處理應用程式無法運作。</span><span class="sxs-lookup"><span data-stu-id="aba55-129">Holographic app remoting applications using the Universal Windows Platform build target are not working.</span></span>
* <span data-ttu-id="aba55-130">Unity 圖形工作系統預設為開啟，即使它與 HoloLens 專案不相容也是一樣。</span><span class="sxs-lookup"><span data-stu-id="aba55-130">The Unity graphics jobs system is defaulted on, even though it is not compatible with HoloLens projects.</span></span>

<span data-ttu-id="aba55-131">如果您選擇在目前的 Unity 2020 中開始新的專案，請務必在交付您的應用程式之前，先追蹤更新 Unity 組建和 Windows XR 外掛程式組建的未來數個月。</span><span class="sxs-lookup"><span data-stu-id="aba55-131">If you choose to start a new project in Unity 2020 today, be sure to follow up over the coming months for updated Unity builds and Windows XR plugin builds before shipping your app.</span></span>  <span data-ttu-id="aba55-132">這可確保您的使用者體驗適當的全息圖穩定性。</span><span class="sxs-lookup"><span data-stu-id="aba55-132">This will ensure that your users experience proper hologram stability.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="aba55-133">使用 Windows XR 外掛程式</span><span class="sxs-lookup"><span data-stu-id="aba55-133">Using the Windows XR plugin</span></span>](windows-xr-plugin.md)

### <a name="using-openxr"></a><span data-ttu-id="aba55-134">使用 OpenXR</span><span class="sxs-lookup"><span data-stu-id="aba55-134">Using OpenXR</span></span>

<span data-ttu-id="aba55-135">Unity 2020.3 LTS 也支援 **Mixed Reality OpenXR** 外掛程式的公開預覽。</span><span class="sxs-lookup"><span data-stu-id="aba55-135">Unity 2020.3 LTS also supports a public preview of the **Mixed Reality OpenXR** plugin.</span></span>

<span data-ttu-id="aba55-136">Mixed Reality OpenXR 外掛程式完全支援 AR Foundation 4.0，提供 ARPlaneManager 和 ARRaycastManager 執行。</span><span class="sxs-lookup"><span data-stu-id="aba55-136">The Mixed Reality OpenXR plugin fully supports AR Foundation 4.0, providing ARPlaneManager and ARRaycastManager implementations.</span></span> <span data-ttu-id="aba55-137">如此一來，您就可以撰寫點擊測試程式碼，然後跨越 HoloLens 2 和 ARCore/ARKit 的手機和平板電腦。</span><span class="sxs-lookup"><span data-stu-id="aba55-137">This enables you to write hit-testing code once that then spans HoloLens 2 and ARCore/ARKit phones and tablets.</span></span> 

<span data-ttu-id="aba55-138">今年之後， **unity 2020.3 LTS 與 OpenXR 外掛程式** 會成為建議的 unity 設定，而 unity 中的未來 HoloLens 2 功能只會透過此外掛程式公開。</span><span class="sxs-lookup"><span data-stu-id="aba55-138">Later this year, **Unity 2020.3 LTS with the OpenXR plugin** will become the recommended Unity configuration, and future HoloLens 2 features in Unity will be exposed only through this plugin.</span></span>  <span data-ttu-id="aba55-139">您現在可以在這裡開始您的專案-不過，如果您的專案是以 HoloLens 2 為目標，則您目前會遇到 Unity 2020 全息圖穩定性和上述的其他問題。</span><span class="sxs-lookup"><span data-stu-id="aba55-139">You can start your project here for now - however, if your project targets HoloLens 2, you will currently encounter the Unity 2020 hologram stability and other issues listed above.</span></span>  <span data-ttu-id="aba55-140">在交付您的應用程式之前，請務必先回來查看更新 Unity 組建和 OpenXR 外掛程式組建的未來幾個月。</span><span class="sxs-lookup"><span data-stu-id="aba55-140">Be sure to check back in the coming months for updated Unity builds and OpenXR plugin builds before shipping your app.</span></span>  <span data-ttu-id="aba55-141">這可確保您的使用者體驗適當的全息圖穩定性。</span><span class="sxs-lookup"><span data-stu-id="aba55-141">This will ensure that your users experience proper hologram stability.</span></span> 

> [!div class="nextstepaction"]
> [<span data-ttu-id="aba55-142">使用 OpenXR 外掛程式</span><span class="sxs-lookup"><span data-stu-id="aba55-142">Using the OpenXR plugin</span></span>](openxr-getting-started.md)

## <a name="unity-20211"></a><span data-ttu-id="aba55-143">Unity 2021。1</span><span class="sxs-lookup"><span data-stu-id="aba55-143">Unity 2021.1</span></span>

<span data-ttu-id="aba55-144">如果您正在嘗試早期的 **Unity 2021.1** 組建，您應該移至 **OpenXR 外掛程式**，因為 Windows XR 外掛程式已在該處淘汰。</span><span class="sxs-lookup"><span data-stu-id="aba55-144">If you are trying out early **Unity 2021.1** builds, you should move forward to the **OpenXR plugin**, as the Windows XR plugin is deprecated there.</span></span>  <span data-ttu-id="aba55-145">從 Unity 2021.2 開始，OpenXR 外掛程式將是唯一開發混合現實的途徑，因為 Windows XR 外掛程式將不再受到支援。</span><span class="sxs-lookup"><span data-stu-id="aba55-145">Starting in Unity 2021.2, the OpenXR plugin will be the only path for Mixed Reality development, as the Windows XR plugin will no longer be supported.</span></span>

## <a name="unity-20184-lts"></a><span data-ttu-id="aba55-146">Unity 2018.4 LTS</span><span class="sxs-lookup"><span data-stu-id="aba55-146">Unity 2018.4 LTS</span></span>

<span data-ttu-id="aba55-147">如果您已經有使用 Unity 2018.4 LTS 的專案，則您的 Unity 引擎會在發行後的2年繼續受到支援。</span><span class="sxs-lookup"><span data-stu-id="aba55-147">If you already have a project using Unity 2018.4 LTS, your Unity engine continues to be supported for 2 years after its release.</span></span>  <span data-ttu-id="aba55-148">Unity 2018 LTS 將于2021年春季結束服務。</span><span class="sxs-lookup"><span data-stu-id="aba55-148">Unity 2018 LTS will reach end of service in the spring of 2021.</span></span>
