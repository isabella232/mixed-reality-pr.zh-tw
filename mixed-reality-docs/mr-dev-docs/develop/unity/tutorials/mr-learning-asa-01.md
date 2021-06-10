---
title: Azure Spatial Anchors 教學課程簡介
description: 完成此課程以了解如何在混合實境應用程式中實作 Azure Spatial Anchors。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens, MRTK, 混合實境工具組, UWP, Azure 空間錨點, ios, android, Windows 10, ARCore, macOS, Android 建置支援, ARKit
ms.localizationpriority: high
ms.openlocfilehash: 2d664c79c0e2d111dc4a0b7b449399682cda1f06
ms.sourcegitcommit: b4fd969b9c2e6313aa728b0dbee4b25014668720
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2021
ms.locfileid: "111403449"
---
# <a name="1-introduction-to-the-azure-spatial-anchors-tutorials"></a><span data-ttu-id="e68e2-104">1.Azure Spatial Anchors 教學課程簡介</span><span class="sxs-lookup"><span data-stu-id="e68e2-104">1. Introduction to the Azure Spatial Anchors tutorials</span></span>

<span data-ttu-id="e68e2-105">歡迎使用 Azure Spatial Anchors 教學課程！</span><span class="sxs-lookup"><span data-stu-id="e68e2-105">Welcome to the Azure Spatial Anchors tutorials!</span></span> <span data-ttu-id="e68e2-106">透過本教學課程系列，您將了解 <a href="https://azure.microsoft.com/services/spatial-anchors" target="_blank">Azure Spatial Anchors</a> (ASA) 的基本概念，以及如何在真實世界中錨定完整的混合實境體驗。</span><span class="sxs-lookup"><span data-stu-id="e68e2-106">Through this tutorial series, you will learn the fundamentals of <a href="https://azure.microsoft.com/services/spatial-anchors" target="_blank">Azure Spatial Anchors</a> (ASA) and how to anchor a complete mixed reality experience in the real world.</span></span> <span data-ttu-id="e68e2-107">您也將了解如何將專案部署至 Android 和 iOS。</span><span class="sxs-lookup"><span data-stu-id="e68e2-107">You will also learn how to deploy your project to Android and iOS.</span></span>

<span data-ttu-id="e68e2-108">本系列的教學課程：</span><span class="sxs-lookup"><span data-stu-id="e68e2-108">Tutorials in this series:</span></span>

1. <span data-ttu-id="e68e2-109">[簡介](mr-learning-asa-01.md) (您正在此教學課程中)</span><span class="sxs-lookup"><span data-stu-id="e68e2-109">[Introduction](mr-learning-asa-01.md) (You're already here)</span></span>
2. [<span data-ttu-id="e68e2-110">開始使用 Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="e68e2-110">Getting started with Azure Spatial Anchors</span></span>](mr-learning-asa-02.md)
3. [<span data-ttu-id="e68e2-111">儲存、擷取和共用 Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="e68e2-111">Saving, retrieving, and sharing Azure Spatial Anchors</span></span>](mr-learning-asa-03.md)
4. [<span data-ttu-id="e68e2-112">顯示 Azure Spatial Anchor 意見反應</span><span class="sxs-lookup"><span data-stu-id="e68e2-112">Displaying Azure Spatial Anchor feedback</span></span>](mr-learning-asa-04.md)
5. [<span data-ttu-id="e68e2-113">適用於 Android 和 iOS 的 Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="e68e2-113">Azure Spatial Anchors for Android and iOS</span></span>](mr-learning-asa-05.md)

## <a name="objectives"></a><span data-ttu-id="e68e2-114">目標</span><span class="sxs-lookup"><span data-stu-id="e68e2-114">Objectives</span></span>

* <span data-ttu-id="e68e2-115">了解如何建立空間錨點，並從 Azure 提取這些錨點</span><span class="sxs-lookup"><span data-stu-id="e68e2-115">Learn how to create spatial anchors and fetch them from Azure</span></span>
* <span data-ttu-id="e68e2-116">了解如何跨多個應用程式工作階段來對齊空間</span><span class="sxs-lookup"><span data-stu-id="e68e2-116">Learn how to achieve spatial alignment across app sessions</span></span>
* <span data-ttu-id="e68e2-117">了解如何在多個裝置之間對齊空間</span><span class="sxs-lookup"><span data-stu-id="e68e2-117">Learn how to achieve spatial alignment between multiple devices</span></span>
* <span data-ttu-id="e68e2-118">了解如何準備和置專案，並部署至 Android 和 iOS</span><span class="sxs-lookup"><span data-stu-id="e68e2-118">Learn how to prepare, build, and deploy your project to Android and iOS</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e68e2-119">必要條件</span><span class="sxs-lookup"><span data-stu-id="e68e2-119">Prerequisites</span></span>

* <span data-ttu-id="e68e2-120">已[安裝正確工具](../../install-the-tools.md)的 Windows 10 電腦</span><span class="sxs-lookup"><span data-stu-id="e68e2-120">A Windows 10 computer configured with the correct [tools installed](../../install-the-tools.md)</span></span>
* <span data-ttu-id="e68e2-121">Windows 10 SDK 10.0.18362.0 或更新版本</span><span class="sxs-lookup"><span data-stu-id="e68e2-121">Windows 10 SDK 10.0.18362.0 or later version</span></span>
* <span data-ttu-id="e68e2-122">已[針對開發而設定](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)的 HoloLens 2 裝置</span><span class="sxs-lookup"><span data-stu-id="e68e2-122">A HoloLens 2 device [configured for development](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="e68e2-123">已安裝 unity<a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">中樞</a>與 unity 2020/2019 LTS，並已新增通用 Windows 平臺組建支援模組</span><span class="sxs-lookup"><span data-stu-id="e68e2-123"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2020 / 2019 LTS installed and the Universal Windows Platform Build Support module added</span></span>
* <span data-ttu-id="e68e2-124">完成[建立空間錨點資源](/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource)一節，其位於[教學課程：建立使用 Azure Spatial Anchors 的 Unity HoloLens 應用程式](/azure/spatial-anchors/quickstarts/get-started-unity-hololens)</span><span class="sxs-lookup"><span data-stu-id="e68e2-124">Completed the [Create a Spatial Anchors resource](/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) section of the [Quickstart: Create a Unity HoloLens app that uses Azure Spatial Anchors](/azure/spatial-anchors/quickstarts/get-started-unity-hololens) tutorial</span></span>
* <span data-ttu-id="e68e2-125">完成[使用者入門教學課程](mr-learning-base-01.md)系列或一些基本的 Unity 和 MRTK 體驗</span><span class="sxs-lookup"><span data-stu-id="e68e2-125">Finished the [Getting started tutorials](mr-learning-base-01.md) series or some basic prior experience with Unity and MRTK</span></span>
* <span data-ttu-id="e68e2-126">如果想要部署至 Android 及 HoloLens</span><span class="sxs-lookup"><span data-stu-id="e68e2-126">If you intend to deploy to Android as well as HoloLens</span></span>
  * <span data-ttu-id="e68e2-127">已啟用<a href="https://developer.android.com/studio/debug/dev-options" target="_blank">開發人員</a>和具有 <a href="https://developers.google.com/ar/discover/supported-devices" target="_blank">ARCore 功能</a>的 Android 裝置，可透過 USB 連接至您的 Windows 或 macOS 電腦</span><span class="sxs-lookup"><span data-stu-id="e68e2-127">A <a href="https://developer.android.com/studio/debug/dev-options" target="_blank">developer enabled</a> and <a href="https://developers.google.com/ar/discover/supported-devices" target="_blank">ARCore capable</a> Android device with USB connection to your Windows or macOS computer</span></span>
  * <span data-ttu-id="e68e2-128">已安裝 unity<a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">中樞</a>與 unity 2020/2019 LTS，並已新增 Android 組建支援模組</span><span class="sxs-lookup"><span data-stu-id="e68e2-128"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2020 / 2019 LTS installed and the Android Build Support module added</span></span>
* <span data-ttu-id="e68e2-129">如果想要部署至 iOS 及 HoloLens</span><span class="sxs-lookup"><span data-stu-id="e68e2-129">If you intend to deploy to iOS as well as HoloLens</span></span>
  * <span data-ttu-id="e68e2-130">已安裝最新版 <a href="https://geo.itunes.apple.com/us/app/xcode/id497799835?mt=12" target="_blank">Xcode</a> 和 <a href="https://cocoapods.org" target="_blank">CocoaPods</a> 的 macOS 電腦</span><span class="sxs-lookup"><span data-stu-id="e68e2-130">A macOS computer with the latest version of <a href="https://geo.itunes.apple.com/us/app/xcode/id497799835?mt=12" target="_blank">Xcode</a> and <a href="https://cocoapods.org" target="_blank">CocoaPods</a> installed</span></span>
  * <span data-ttu-id="e68e2-131"><a href="https://developer.apple.com/documentation/arkit/verifying_device_support_and_user_permission" target="_blank">ARKit 相容</a>的 iOS 裝置可透過 USB 連接至您的 macOS 電腦</span><span class="sxs-lookup"><span data-stu-id="e68e2-131">An <a href="https://developer.apple.com/documentation/arkit/verifying_device_support_and_user_permission" target="_blank">ARKit compatible</a> iOS device with USB connection to your macOS computer</span></span>
  * <span data-ttu-id="e68e2-132">已安裝 unity<a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">中樞</a>與 unity 2020/2019 LTS，並已新增 IOS 組建支援模組</span><span class="sxs-lookup"><span data-stu-id="e68e2-132"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2020 / 2019 LTS installed and the iOS Build Support module added</span></span>

> [!Important]
> <span data-ttu-id="e68e2-133">此教學課程系列支援 Unity 2020 LTS (目前的 2020.3) 如果您使用 Open XR 或 Windows XR 外掛程式，以及 Unity 2019 LTS (目前的 2019.4. x) 如果您使用舊版的 WSA。</span><span class="sxs-lookup"><span data-stu-id="e68e2-133">This tutorial series supports Unity 2020 LTS(currently 2020.3.x) if you are using Open XR or Windows XR Plugin and also Unity 2019 LTS (currently 2019.4.x) if you are using Legacy WSA.</span></span> <span data-ttu-id="e68e2-134">這個版本能取代上述連結必要條件中所述的任何 Unity 版本需求。</span><span class="sxs-lookup"><span data-stu-id="e68e2-134">This supersedes any Unity version requirements stated in the prerequisites linked above.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="e68e2-135">下一個教學課程：2.開始使用 Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="e68e2-135">Next Tutorial: 2. Getting started with Azure Spatial Anchors</span></span>](mr-learning-asa-02.md)
