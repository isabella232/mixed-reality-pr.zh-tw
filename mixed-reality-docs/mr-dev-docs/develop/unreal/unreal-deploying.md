---
title: 在 Unreal 中部署至裝置
description: 在 Unreal 中部署至裝置以 HoloLens 2 的指南
author: sw5813
ms.author: suwu
ms.date: 7/10/2020
ms.topic: article
keywords: Unreal、Unreal Engine 4、UE4、HoloLens、HoloLens 2、mixed reality、部署至裝置、電腦、檔
appliesto:
- HoloLens 2
ms.openlocfilehash: abd5e5c28ec5e66c4f73df8edf5e0ac0212d170a
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2020
ms.locfileid: "91679816"
---
# <a name="deploy-to-device-in-unreal"></a><span data-ttu-id="6dec8-104">在 Unreal 中部署至裝置</span><span class="sxs-lookup"><span data-stu-id="6dec8-104">Deploy to device in Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="6dec8-105">概觀</span><span class="sxs-lookup"><span data-stu-id="6dec8-105">Overview</span></span>
<span data-ttu-id="6dec8-106">有兩種方式可將 Unreal 應用程式部署至 HoloLens 2：</span><span class="sxs-lookup"><span data-stu-id="6dec8-106">There are two ways to deploy an Unreal application to HoloLens 2:</span></span>
* <span data-ttu-id="6dec8-107">直接從 Unreal 編輯器</span><span class="sxs-lookup"><span data-stu-id="6dec8-107">Directly from the Unreal editor</span></span>
* <span data-ttu-id="6dec8-108">作為透過裝置入口網站上傳的套件</span><span class="sxs-lookup"><span data-stu-id="6dec8-108">As a package uploaded via the device portal</span></span>

<span data-ttu-id="6dec8-109">這兩個選項都需要您設定 HoloLens，才能使用 [裝置入口網站](../platform-capabilities-and-apis/using-the-windows-device-portal.md) 進行開發。</span><span class="sxs-lookup"><span data-stu-id="6dec8-109">Both options require you to set up your HoloLens to use the [device portal](../platform-capabilities-and-apis/using-the-windows-device-portal.md) for development.</span></span>

## <a name="deploying-to-device-from-the-unreal-editor"></a><span data-ttu-id="6dec8-110">從 Unreal 編輯器部署至裝置</span><span class="sxs-lookup"><span data-stu-id="6dec8-110">Deploying to device from the Unreal editor</span></span>

1. <span data-ttu-id="6dec8-111">按一下 [ **啟動** ] 按鈕旁的下拉式箭號。</span><span class="sxs-lookup"><span data-stu-id="6dec8-111">Click the dropdown arrow next to the **Launch** button.</span></span> <span data-ttu-id="6dec8-112">一開始，HoloLens 裝置選項將會呈現灰色。</span><span class="sxs-lookup"><span data-stu-id="6dec8-112">Initially, the HoloLens device option will be grayed out.</span></span>

![啟動下拉式選項](images/unreal/launch-dropdown.png)

2. <span data-ttu-id="6dec8-114">開啟 **裝置管理員** 。</span><span class="sxs-lookup"><span data-stu-id="6dec8-114">Open the **Device Manager** .</span></span> <span data-ttu-id="6dec8-115">請注意，您的 HoloLens 不會自動出現在裝置清單中。</span><span class="sxs-lookup"><span data-stu-id="6dec8-115">Note that your HoloLens won't automatically appear in the device list.</span></span>

3. <span data-ttu-id="6dec8-116">展開 [ **新增未列出的裝置** ] 區段。</span><span class="sxs-lookup"><span data-stu-id="6dec8-116">Expand the **Add An Unlisted Device** section.</span></span>

4. <span data-ttu-id="6dec8-117">選取 [ **HoloLens** ] 作為您的 **平臺** 。</span><span class="sxs-lookup"><span data-stu-id="6dec8-117">Select **HoloLens** as your **Platform** .</span></span>

5. <span data-ttu-id="6dec8-118">輸入裝置的 IP 位址和埠資訊（以冒號分隔）作為裝置識別碼。</span><span class="sxs-lookup"><span data-stu-id="6dec8-118">Enter your devices' IP address and port information separated by a colon as the device identifier.</span></span> <span data-ttu-id="6dec8-119">例如，透過 USB) 連接時 ("127.0.0.1： 10080"。</span><span class="sxs-lookup"><span data-stu-id="6dec8-119">For example, "127.0.0.1:10080" (when connected via USB).</span></span> <span data-ttu-id="6dec8-120">使用您的裝置入口網站使用者名稱和密碼認證。</span><span class="sxs-lookup"><span data-stu-id="6dec8-120">Use your Device Portal username and password credentials.</span></span>

6. <span data-ttu-id="6dec8-121">點擊 [ **新增** ] 並關閉 [裝置管理員]。</span><span class="sxs-lookup"><span data-stu-id="6dec8-121">Hit **Add** and close the device manager.</span></span>
    * <span data-ttu-id="6dec8-122">如果發生錯誤 (例如錯誤的位址、使用者名稱或密碼) ，則會將訊息列印到輸出記錄檔。</span><span class="sxs-lookup"><span data-stu-id="6dec8-122">In the case of an error (such as wrong address, user name or password), a message will be printed to the Output Log.</span></span>

![新增未列出的裝置](images/unreal/add-unlisted-device.png)

7. <span data-ttu-id="6dec8-124">再次按一下 [ **啟動** ] 按鈕旁的下拉箭號，此時您應該會看到您剛剛新增的 HoloLens 裝置。</span><span class="sxs-lookup"><span data-stu-id="6dec8-124">Click the dropdown arrow next to the **Launch** button again - this time you should see the HoloLens device you just added.</span></span> <span data-ttu-id="6dec8-125">選取要建立並部署到 HoloLens 的 HoloLens 裝置。</span><span class="sxs-lookup"><span data-stu-id="6dec8-125">Select the HoloLens device to build and deploy to your HoloLens.</span></span>

>[!NOTE]
><span data-ttu-id="6dec8-126">建立裝置可能需要重新編譯著色器 (特別是在第一次執行) 上-這可能需要一些時間。</span><span class="sxs-lookup"><span data-stu-id="6dec8-126">Building for the device may involve recompiling shaders (especially on the first run)- this can take a while.</span></span> <span data-ttu-id="6dec8-127">請勿讓裝置進入睡眠狀態，直到應用程式正在執行 (您可能必須將其磨損) 。</span><span class="sxs-lookup"><span data-stu-id="6dec8-127">Don't let the device go to sleep until the app is running (you may have to wear it).</span></span> <span data-ttu-id="6dec8-128">否則著色器編譯將會失敗！</span><span class="sxs-lookup"><span data-stu-id="6dec8-128">Otherwise shader compilation will fail!</span></span>

## <a name="deploying-to-device-via-device-portal"></a><span data-ttu-id="6dec8-129">透過裝置入口網站部署至裝置</span><span class="sxs-lookup"><span data-stu-id="6dec8-129">Deploying to device via device portal</span></span>

<span data-ttu-id="6dec8-130">您可以在消費者入門 with Unreal 教學課程系列的最後一節中，找到 [封裝和部署應用程式](tutorials/unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal) 的詳細指示。</span><span class="sxs-lookup"><span data-stu-id="6dec8-130">You can find detailed instructions on [packaging and deploying an app](tutorials/unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal) in the last section of the Getting Started with Unreal tutorial series.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="6dec8-131">下一個開發檢查點</span><span class="sxs-lookup"><span data-stu-id="6dec8-131">Next Development Checkpoint</span></span>

<span data-ttu-id="6dec8-132">如果您正在遵循我們所配置的 Unreal 開發檢查點旅程，您就會在部署階段。</span><span class="sxs-lookup"><span data-stu-id="6dec8-132">If you're following the Unreal development checkpoint journey we've laid out, you're in the midst of the deployment stage.</span></span> <span data-ttu-id="6dec8-133">您可以從這裡繼續新增 advanced services：</span><span class="sxs-lookup"><span data-stu-id="6dec8-133">From here, you can proceed to adding advanced services:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="6dec8-134">Advanced services</span><span class="sxs-lookup"><span data-stu-id="6dec8-134">Advanced services</span></span>](unreal-development-overview.md#5-adding-services)

<span data-ttu-id="6dec8-135">您隨時都可以回到 [Unreal 開發檢查點](unreal-development-overview.md#4-deploying-to-a-device) 。</span><span class="sxs-lookup"><span data-stu-id="6dec8-135">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#4-deploying-to-a-device) at any time.</span></span>
