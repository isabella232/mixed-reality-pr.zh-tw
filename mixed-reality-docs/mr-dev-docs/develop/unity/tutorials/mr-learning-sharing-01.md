---
title: 多使用者功能教學課程簡介
description: 完成此課程以了解如何在 HoloLens 2 應用程式中實作共用的多使用者體驗。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens, 多使用者功能, Photon, MRTK, 混合實境工具組, UWP, Azure 空間錨點
ms.localizationpriority: high
ms.openlocfilehash: 90c5b2ee3f25c39fc644aee0fbbf49643f7d2a59
ms.sourcegitcommit: 68140e9ce84e69a99c2b3d970c7b8f2927a7fc93
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/05/2021
ms.locfileid: "99590170"
---
# <a name="1-introduction-to-the-multi-user-capabilities-tutorials"></a><span data-ttu-id="3748d-104">1.多使用者功能教學課程簡介</span><span class="sxs-lookup"><span data-stu-id="3748d-104">1. Introduction to the Multi-user capabilities tutorials</span></span>

<span data-ttu-id="3748d-105">歡迎使用多使用者功能教學課程！</span><span class="sxs-lookup"><span data-stu-id="3748d-105">Welcome to the Multi-User Capabilities tutorials!</span></span> <span data-ttu-id="3748d-106">透過本教學課程系列，您將了解使用 <a href="https://www.photonengine.com/PUN" target="_blank">Photon Unity 網路</a> (PUN) 建置多使用者體驗的基本概念。</span><span class="sxs-lookup"><span data-stu-id="3748d-106">Through this tutorial series, you will learn the fundamentals of building a multi-user experience using <a href="https://www.photonengine.com/PUN" target="_blank">Photon Unity Networking</a> (PUN).</span></span> <span data-ttu-id="3748d-107">PUN 是可讓混合實境開發人員用來建立共用體驗的眾多網路功能選項之一。</span><span class="sxs-lookup"><span data-stu-id="3748d-107">PUN is one of several networking options available to mixed reality developers to create shared experiences.</span></span>

<span data-ttu-id="3748d-108">本系列的教學課程：</span><span class="sxs-lookup"><span data-stu-id="3748d-108">Tutorials in this series:</span></span>

* [<span data-ttu-id="3748d-109">設定 Photon Unity 網路</span><span class="sxs-lookup"><span data-stu-id="3748d-109">Setting up Photon Unity Networking</span></span>](mr-learning-sharing-02.md)
* [<span data-ttu-id="3748d-110">連線多個使用者</span><span class="sxs-lookup"><span data-stu-id="3748d-110">Connecting multiple users</span></span>](mr-learning-sharing-03.md)
* [<span data-ttu-id="3748d-111">與多個使用者共用物件移動</span><span class="sxs-lookup"><span data-stu-id="3748d-111">Sharing object movements with multiple users</span></span>](mr-learning-sharing-04.md)
* [<span data-ttu-id="3748d-112">將 Azure Spatial Anchors 整合到共用體驗</span><span class="sxs-lookup"><span data-stu-id="3748d-112">Integrating Azure Spatial Anchors into a shared experience</span></span>](mr-learning-sharing-05.md)

## <a name="objectives"></a><span data-ttu-id="3748d-113">目標</span><span class="sxs-lookup"><span data-stu-id="3748d-113">Objectives</span></span>

* <span data-ttu-id="3748d-114">了解如何建立 PUN 應用程式以及將您的 Unity 專案連線至 PUN 應用程式</span><span class="sxs-lookup"><span data-stu-id="3748d-114">Learn how to create a PUN app and connect your Unity project to it</span></span>
* <span data-ttu-id="3748d-115">了解如何在共用體驗中連線多個使用者</span><span class="sxs-lookup"><span data-stu-id="3748d-115">Learn how to connect multiple users in a shared experience</span></span>
* <span data-ttu-id="3748d-116">了解如何與其他使用者共用物件移動</span><span class="sxs-lookup"><span data-stu-id="3748d-116">Learn how to share the object movements with other users</span></span>
* <span data-ttu-id="3748d-117">了解如何達到多個裝置之間的空間對齊</span><span class="sxs-lookup"><span data-stu-id="3748d-117">Learn how to achieve spatial alignment between multiple devices</span></span>

## <a name="prerequisites"></a><span data-ttu-id="3748d-118">必要條件</span><span class="sxs-lookup"><span data-stu-id="3748d-118">Prerequisites</span></span>

* <span data-ttu-id="3748d-119">已[安裝正確工具](../../install-the-tools.md)的 Windows 10 電腦</span><span class="sxs-lookup"><span data-stu-id="3748d-119">A Windows 10 computer configured with the correct [tools installed](../../install-the-tools.md)</span></span>
* <span data-ttu-id="3748d-120">Windows 10 SDK 10.0.18362.0 或更新版本</span><span class="sxs-lookup"><span data-stu-id="3748d-120">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="3748d-121">已[針對開發而設定](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)的 HoloLens 2 裝置</span><span class="sxs-lookup"><span data-stu-id="3748d-121">A HoloLens 2 device [configured for development](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="3748d-122">已安裝 Unity 2019 LTS 的 <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a>，且已新增通用 Windows 平台組建支援模組</span><span class="sxs-lookup"><span data-stu-id="3748d-122"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019 LTS installed and the Universal Windows Platform Build Support module added</span></span>
* <span data-ttu-id="3748d-123">完成[建立空間錨點資源](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource)區段，其位於[教學課程：建立使用 Azure Spatial Anchors 的 Unity HoloLens 應用程式](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens)</span><span class="sxs-lookup"><span data-stu-id="3748d-123">Completed the [Create a Spatial Anchors resource](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) section of the [Quickstart: Create a Unity HoloLens app that uses Azure Spatial Anchors](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens) tutorial</span></span>
* <span data-ttu-id="3748d-124">完成[使用者入門教學課程](mr-learning-base-01.md)系列或一些基本的 Unity 和 MRTK 體驗</span><span class="sxs-lookup"><span data-stu-id="3748d-124">Completed the [Getting started tutorials](mr-learning-base-01.md) series or some basic prior experience with Unity and MRTK</span></span>
* <span data-ttu-id="3748d-125">完成 [Azure 空間錨點教學課程](mr-learning-asa-01.md)系列，或建立 Azure 空間錨點帳戶的體驗</span><span class="sxs-lookup"><span data-stu-id="3748d-125">Completed the [Azure Spatial Anchors tutorials](mr-learning-asa-01.md) series or prior experience creating an Azure Spatial Anchors Account</span></span>
* <span data-ttu-id="3748d-126">如果想要部署至 Android 及 HoloLens</span><span class="sxs-lookup"><span data-stu-id="3748d-126">If you intend to deploy to Android as well as HoloLens</span></span>
  * <span data-ttu-id="3748d-127">已啟用<a href="https://developer.android.com/studio/debug/dev-options" target="_blank">開發人員</a>和具有 <a href="https://developers.google.com/ar/discover/supported-devices" target="_blank">ARCore 功能</a>的 Android 裝置，可透過 USB 連接至您的 Windows 或 macOS 電腦</span><span class="sxs-lookup"><span data-stu-id="3748d-127">A <a href="https://developer.android.com/studio/debug/dev-options" target="_blank">developer enabled</a> and <a href="https://developers.google.com/ar/discover/supported-devices" target="_blank">ARCore capable</a> Android device with USB connection to your Windows or macOS computer</span></span>
  * <span data-ttu-id="3748d-128">已安裝 unity 2019 LTS 的<a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity 中樞</a>，並已新增 Android 組建支援模組</span><span class="sxs-lookup"><span data-stu-id="3748d-128"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019 LTS installed and the Android Build Support module added</span></span>
* <span data-ttu-id="3748d-129">如果想要部署至 iOS 及 HoloLens</span><span class="sxs-lookup"><span data-stu-id="3748d-129">If you intend to deploy to iOS as well as HoloLens</span></span>
  * <span data-ttu-id="3748d-130">已安裝最新版 <a href="https://geo.itunes.apple.com/us/app/xcode/id497799835?mt=12" target="_blank">Xcode</a> 和 <a href="https://cocoapods.org" target="_blank">CocoaPods</a> 的 macOS 電腦</span><span class="sxs-lookup"><span data-stu-id="3748d-130">A macOS computer with the latest version of <a href="https://geo.itunes.apple.com/us/app/xcode/id497799835?mt=12" target="_blank">Xcode</a> and <a href="https://cocoapods.org" target="_blank">CocoaPods</a> installed</span></span>
  * <span data-ttu-id="3748d-131"><a href="https://developer.apple.com/documentation/arkit/verifying_device_support_and_user_permission" target="_blank">ARKit 相容</a>的 iOS 裝置可透過 USB 連接至您的 macOS 電腦</span><span class="sxs-lookup"><span data-stu-id="3748d-131">An <a href="https://developer.apple.com/documentation/arkit/verifying_device_support_and_user_permission" target="_blank">ARKit compatible</a> iOS device with USB connection to your macOS computer</span></span>
  * <span data-ttu-id="3748d-132">已安裝 unity 2019 LTS 的<a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity 中樞</a>，並已新增 IOS 組建支援模組</span><span class="sxs-lookup"><span data-stu-id="3748d-132"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019 LTS installed and the iOS Build Support module added</span></span>

> [!CAUTION]
> <span data-ttu-id="3748d-133">本教學課程系列的建議混合現實工具組版本是 MRTK 2.5.3。</span><span class="sxs-lookup"><span data-stu-id="3748d-133">The recommended Mixed Reality Toolkit version for this tutorial series is MRTK 2.5.3.</span></span>

> [!CAUTION]
> <span data-ttu-id="3748d-134">本教學課程系列的建議 Unity 版本是 Unity 2019 LTS 這會取代上述必要條件中所述的任何 Unity 版本需求。</span><span class="sxs-lookup"><span data-stu-id="3748d-134">The recommended Unity version for this tutorial series is Unity 2019 LTS This supersedes any Unity version requirements stated in the prerequisites linked above.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="3748d-135">下一個教學課程：2.設定 Photon Unity 網路</span><span class="sxs-lookup"><span data-stu-id="3748d-135">Next Tutorial: 2. Setting up Photon Unity Networking</span></span>](mr-learning-sharing-02.md)
