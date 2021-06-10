---
title: 連線多個使用者
description: 完成此課程，以了解如何連線 HoloLens 2 混合實境應用程式中的多個使用者。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens, 多使用者功能, Photon, MRTK, 混合實境工具組, UWP, Azure 空間錨點
ms.localizationpriority: high
ms.openlocfilehash: 976593fd2f107d456da4f04da19621dd253f2ae1
ms.sourcegitcommit: 943489923c69c3a28bc152f1cb516dcdcea2880a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2021
ms.locfileid: "111772421"
---
# <a name="3-connecting-multiple-users"></a><span data-ttu-id="c3a38-104">3.連線多個使用者</span><span class="sxs-lookup"><span data-stu-id="c3a38-104">3. Connecting multiple users</span></span>

<span data-ttu-id="c3a38-105">在此教學課程中，您將了解如何在即時共用體驗中連線多個使用者。</span><span class="sxs-lookup"><span data-stu-id="c3a38-105">In this tutorial, you will learn how to connect multiple users as part of a live shared experience.</span></span> <span data-ttu-id="c3a38-106">在本教學課程結束時，您將能夠在多個裝置上執行應用程式，並讓每位使用者看到其他使用者虛擬人偶的即時移動狀態。</span><span class="sxs-lookup"><span data-stu-id="c3a38-106">By the end of the tutorial, you will be able to run the app on multiple devices and have each user see the avatar of other users move in real-time.</span></span>

## <a name="objectives"></a><span data-ttu-id="c3a38-107">目標</span><span class="sxs-lookup"><span data-stu-id="c3a38-107">Objectives</span></span>

* <span data-ttu-id="c3a38-108">了解如何在共用體驗中連線多個使用者</span><span class="sxs-lookup"><span data-stu-id="c3a38-108">Learn how to connect multiple users in a shared experience</span></span>

## <a name="preparing-the-scene"></a><span data-ttu-id="c3a38-109">準備場景</span><span class="sxs-lookup"><span data-stu-id="c3a38-109">Preparing the scene</span></span>

<span data-ttu-id="c3a38-110">在本節中，您將藉由新增一些教學課程 Prefab 來準備場景。</span><span class="sxs-lookup"><span data-stu-id="c3a38-110">In this section, you will prepare the scene by adding some of the tutorial prefabs.</span></span>

<span data-ttu-id="c3a38-111">在 [專案] 視窗中，瀏覽至 [資產]  >  [MRTK.Tutorials.MultiUserCapabilities]  >  [Prefabs] 資料夾，然後按一下下列 Prefab 並將其拖曳到 [階層] 視窗中，將其新增到您的場景中：</span><span class="sxs-lookup"><span data-stu-id="c3a38-111">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Prefabs** folder, then click-and-drag the following prefabs into the Hierarchy window to add them to your scene:</span></span>

* <span data-ttu-id="c3a38-112">**NetworkLobby** prefab</span><span class="sxs-lookup"><span data-stu-id="c3a38-112">**NetworkLobby** prefab</span></span>
* <span data-ttu-id="c3a38-113">**SharedPlayground** prefab</span><span class="sxs-lookup"><span data-stu-id="c3a38-113">**SharedPlayground** prefab</span></span>

![已選取新增 NetworkLobby 和 SharedPlayground Prefabs 的 Unity](images/mr-learning-sharing/sharing-03-section1-step1-1.png)

<span data-ttu-id="c3a38-115">在 [專案] 視窗中，瀏覽至 [資產] > [MRTK.Tutorials.AzureSpatialAnchors] > [Prefabs] 資料夾，然後按一下下列 Prefab 並將其拖曳至 [階層] 視窗中，將其新增到您的場景中：</span><span class="sxs-lookup"><span data-stu-id="c3a38-115">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.AzureSpatialAnchors** > **Prefabs** folder, then click-and-drag the following prefab into the Hierarchy window to add it to your scene:</span></span>

* <span data-ttu-id="c3a38-116">**DebugWindow** prefab</span><span class="sxs-lookup"><span data-stu-id="c3a38-116">**DebugWindow** prefab</span></span>

![已選取新增 DebugWindow Prefab 的 Unity](images/mr-learning-sharing/sharing-03-section1-step1-2.png)

## <a name="creating-the-user-prefab"></a><span data-ttu-id="c3a38-118">建立使用者預製物件</span><span class="sxs-lookup"><span data-stu-id="c3a38-118">Creating the user prefab</span></span>

<span data-ttu-id="c3a38-119">在本節中，您將建立一個預製物件來代表共用體驗中的使用者。</span><span class="sxs-lookup"><span data-stu-id="c3a38-119">In this section, you will create a prefab that will be used to represent the users in the shared experience.</span></span>

### <a name="1-create-and-configure-the-user"></a><span data-ttu-id="c3a38-120">1.建立並設定使用者</span><span class="sxs-lookup"><span data-stu-id="c3a38-120">1. Create and configure the user</span></span>

<span data-ttu-id="c3a38-121">在 [階層] 視窗中，以滑鼠右鍵按一下空白區域，然後選取 [建立空物件] 以將空的物件新增至場景，並將物件命名為 **PhotonUser**，然後進行下列設定：</span><span class="sxs-lookup"><span data-stu-id="c3a38-121">In the Hierarchy window, right-click on an empty area and select **Create Empty** to add an empty object to your scene, name the object **PhotonUser**, and configure it as follows:</span></span>

* <span data-ttu-id="c3a38-122">請確定變形的 **位置** 已設定為 X = 0、Y = 0、Z = 0：</span><span class="sxs-lookup"><span data-stu-id="c3a38-122">Ensure the Transform **Position** is set to X = 0, Y = 0, Z = 0:</span></span>

![已選取新建立 PhotonUser 物件的 Unity](images/mr-learning-sharing/sharing-03-section2-step1-1.png)

<span data-ttu-id="c3a38-124">在 [階層] 視窗中選取 [PhotonUser] 物件，在 [偵測器] 視窗中，使用 [新增元件] 按鈕，將 **Photon User (指令碼)** 元件新增至 PhotonUser 物件：</span><span class="sxs-lookup"><span data-stu-id="c3a38-124">In the Hierarchy window, select the **PhotonUser** object, then in the Inspector window, use the **Add Component** button to add the **Photon User (Script)** component to the PhotonUser object:</span></span>

![已新增 Photon 使用者元件的 Unity](images/mr-learning-sharing/sharing-03-section2-step1-2.png)

<span data-ttu-id="c3a38-126">在 [偵測器] 視窗中，使用 [新增元件] 按鈕，將 **Generic Net Sync (指令碼)** 元件新增至 PhotonUser 物件，並進行下列設定：</span><span class="sxs-lookup"><span data-stu-id="c3a38-126">In the Inspector window, use the **Add Component** button to add the **Generic Net Sync (Script)** component to the PhotonUser object and configure it as follows:</span></span>

* <span data-ttu-id="c3a38-127">勾選 [是使用者] 核取方塊</span><span class="sxs-lookup"><span data-stu-id="c3a38-127">Check the **Is User** checkbox</span></span>

![已新增和設定 Generic Net Sync 元件的 Unity](images/mr-learning-sharing/sharing-03-section2-step1-3.png)

<span data-ttu-id="c3a38-129">在 [偵測器] 視窗中，使用 [新增元件] 按鈕，將 **Photon View (指令碼)** 元件新增至 PhotonUser 物件，並進行下列設定：</span><span class="sxs-lookup"><span data-stu-id="c3a38-129">In the Inspector window, use the **Add Component** button to add the **Photon View (Script)** component to the PhotonUser object and configure it as follows:</span></span>

* <span data-ttu-id="c3a38-130">確定已將 **一般 Net Sync (腳本)** 元件指派給觀察到的 **元件** 欄位</span><span class="sxs-lookup"><span data-stu-id="c3a38-130">Ensure that the **Observed Components** field is assigned with the **Generic Net Sync (Script)** component</span></span>

![已新增和設定 Photon View 元件的 Unity](images/mr-learning-sharing/sharing-03-section2-step1-4.png)

### <a name="2-create-the-avatar"></a><span data-ttu-id="c3a38-132">2.建立虛擬人偶</span><span class="sxs-lookup"><span data-stu-id="c3a38-132">2. Create the avatar</span></span>

<span data-ttu-id="c3a38-133">在 [專案] 視窗中，流覽至 [**封裝**  >  **混合現實工具組標準資產**  >  **材質**] 資料夾，以找出 MRTK 的材質。</span><span class="sxs-lookup"><span data-stu-id="c3a38-133">In the Project window, navigate to the **Packages** > **Mixed Reality Toolkit Standard Assets** > **Materials** folder to locate the MRTK materials.</span></span>

<span data-ttu-id="c3a38-134">然後在 [階層] 視窗中，以滑鼠右鍵按一下 [PhotonUser] 物件，然後選取 [3D 物件]  >  [球體]，將球體物件建立為 PhotonUser 物件的子系，並依照下列方式進行設定：</span><span class="sxs-lookup"><span data-stu-id="c3a38-134">Then, in the Hierarchy window, right-click on the **PhotonUser** object and select **3D Object** > **Sphere** to create a sphere object as a child of the PhotonUser object and configure it as follows:</span></span>

* <span data-ttu-id="c3a38-135">請確定變形的 **位置** 已設定為 X = 0、Y = 0、Z = 0</span><span class="sxs-lookup"><span data-stu-id="c3a38-135">Ensure the Transform **Position** is set to X = 0, Y = 0, Z = 0</span></span>
* <span data-ttu-id="c3a38-136">將變形 **縮放** 變更為適當大小，例如 X = 0.15、Y = 0.15 和 Z = 0.15</span><span class="sxs-lookup"><span data-stu-id="c3a38-136">Change the Transform **Scale** to a suitable size, for example, X = 0.15, Y = 0.15, Z = 0.15</span></span>
* <span data-ttu-id="c3a38-137">對 [MeshRenderer] > [材質] > [元素 0] 欄位，指派 **MRTK_Standard_White** 材質</span><span class="sxs-lookup"><span data-stu-id="c3a38-137">To the MeshRenderer > Materials > **Element 0** field, assign the **MRTK_Standard_White** material</span></span>

![具有新建立和已設定頭像球體的 Unity](images/mr-learning-sharing/sharing-03-section2-step2-1.png)

### <a name="3-create-the-prefab"></a><span data-ttu-id="c3a38-139">3.建立預製物件</span><span class="sxs-lookup"><span data-stu-id="c3a38-139">3. Create the prefab</span></span>

<span data-ttu-id="c3a38-140">在 [專案] 視窗中，瀏覽至 [資產] > [MRTK.Tutorials.MultiUserCapabilities] > [Resources] 資料夾：</span><span class="sxs-lookup"><span data-stu-id="c3a38-140">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Resources** folder:</span></span>

![已選取 [資源] 資料夾的 Unity [專案] 視窗](images/mr-learning-sharing/sharing-03-section2-step3-1.png)

<span data-ttu-id="c3a38-142">在仍選取 [資源] 資料夾的情況下，從 [階層] 視窗中 **按一下並拖曳** **PhotonUser** 物件到 [Resources] 資料夾，讓 PhotonUser 物件成為預製物件：</span><span class="sxs-lookup"><span data-stu-id="c3a38-142">With the Resources folder still selected, **click-and-drag** the **PhotonUser** object from the Hierarchy window into the **Resources** folder to make the PhotonUser object a prefab:</span></span>

![已選取新建立 PhotonUser Prefab 的 Unity](images/mr-learning-sharing/sharing-03-section2-step3-2.png)

<span data-ttu-id="c3a38-144">在 [階層] 視窗中，以滑鼠右鍵按一下 [PhotonUser] 物件，然後選取 [刪除]，從場景中將其移除：</span><span class="sxs-lookup"><span data-stu-id="c3a38-144">In the Hierarchy window, right-click on the **PhotonUser** object and select **Delete** to remove it from the scene:</span></span>

![已從場景中移除新建立 PhotonUser Prefab 物件的 Unity](images/mr-learning-sharing/sharing-03-section2-step3-3.png)

## <a name="configuring-pun-to-instantiate-the-user-prefab"></a><span data-ttu-id="c3a38-146">設定 PUN 以具現化使用者預製物件</span><span class="sxs-lookup"><span data-stu-id="c3a38-146">Configuring PUN to instantiate the user prefab</span></span>

<span data-ttu-id="c3a38-147">在本節中，您會將專案設定為使用上一節中建立的 PhotonUser 預製物件。</span><span class="sxs-lookup"><span data-stu-id="c3a38-147">In this section, you will configure the project to use the PhotonUser prefab you created in the previous section.</span></span>

<span data-ttu-id="c3a38-148">在 [專案] 視窗中，瀏覽至 [資產] > [MRTK.Tutorials.MultiUserCapabilities] > [Resources] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="c3a38-148">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Resources** folder.</span></span>

<span data-ttu-id="c3a38-149">在 [階層] 視窗中，展開 **NetworkLobby** 物件，然後選取 **NetworkRoom** 子物件，接著在 [偵測器] 視窗中找出 **Photon Room (指令碼)** 元件，並依照下列方式進行設定：</span><span class="sxs-lookup"><span data-stu-id="c3a38-149">In the Hierarchy window, expand the **NetworkLobby** object and select the **NetworkRoom** child object, then in the Inspector window, locate the **Photon Room (Script)** component and configure it as follows:</span></span>

* <span data-ttu-id="c3a38-150">在 [Photon 使用者預製物件] 欄位中，從 [Resources] 資料夾指派 **PhotonUser** 預製物件</span><span class="sxs-lookup"><span data-stu-id="c3a38-150">To the **Photon User Prefab** field, assign the **PhotonUser** prefab from the Resources folder</span></span>

![已部分設定 Photon Room 元件的 Unity](images/mr-learning-sharing/sharing-03-section3-step1-1.png)

## <a name="trying-the-experience-with-multiple-users"></a><span data-ttu-id="c3a38-152">嘗試多位使用者的體驗</span><span class="sxs-lookup"><span data-stu-id="c3a38-152">Trying the experience with multiple users</span></span>

<span data-ttu-id="c3a38-153">如果您現在建立了 Unity 專案並將其部署至 HoloLens，則回到 Unity，並在應用程式於 HoloLens 上執行時進入遊戲模式，您會在移動頭部 (HoloLens) 時看到 HoloLens 使用者虛擬人偶跟著移動：</span><span class="sxs-lookup"><span data-stu-id="c3a38-153">If you now build and deploy the Unity project to your HoloLens, then, back in Unity, enter Game mode while the app is running on your HoloLens, you will see the HoloLens user avatar move when you move your head (HoloLens) around:</span></span>

![動畫，顯示具有網路使用者的 Unity](images/mr-learning-sharing/sharing-03-section4-step1-1.gif)

> [!TIP]
> <span data-ttu-id="c3a38-155">如需有關如何建立 Unity 專案並將其部署至 HoloLens 2 的提醒，您可以參閱[對您的 HoloLens 2 建置應用程式](mr-learning-base-02.md#building-your-application-to-your-hololens-2)的指示。</span><span class="sxs-lookup"><span data-stu-id="c3a38-155">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Building your app to your HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions.</span></span>

> [!CAUTION]
> <span data-ttu-id="c3a38-156">應用程式必須連線到 Photon，因此請確定您的電腦/裝置已連線到網際網路。</span><span class="sxs-lookup"><span data-stu-id="c3a38-156">The app needs to connect to Photon, so make sure your computer/device is connected to the internet.</span></span>

## <a name="congratulations"></a><span data-ttu-id="c3a38-157">恭喜！</span><span class="sxs-lookup"><span data-stu-id="c3a38-157">Congratulations</span></span>

<span data-ttu-id="c3a38-158">您已成功設定您的專案，可讓多個使用者連線到相同的體驗，並查看彼此的移動。</span><span class="sxs-lookup"><span data-stu-id="c3a38-158">You have successfully configured your project to allow multiple users to connect to the same experience and see each other's movements.</span></span> <span data-ttu-id="c3a38-159">在下一個教學課程中，您將會實作功能，讓物件的移動也能在多個裝置之間共用。</span><span class="sxs-lookup"><span data-stu-id="c3a38-159">In the next tutorial, you will implement functionality so that the movements of objects are also shared across multiple devices.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="c3a38-160">下一個教學課程：4.與多個使用者共用物件移動</span><span class="sxs-lookup"><span data-stu-id="c3a38-160">Next Tutorial: 4. Sharing object movements with multiple users</span></span>](mr-learning-sharing-04.md)
