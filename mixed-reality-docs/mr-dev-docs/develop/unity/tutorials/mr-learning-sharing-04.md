---
title: 與多個使用者共用物件移動
description: 完成此課程，以了解如何在 HoloLens 2 應用程式中與多個使用者共用物件移動。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens, 多使用者功能, Photon, MRTK, 混合實境工具組, UWP, Azure 空間錨點
ms.localizationpriority: high
ms.openlocfilehash: d4dc943c8ca57331b4916e40db67df3cd3d6d2e6
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "99590060"
---
# <a name="4-sharing-object-movements-with-multiple-users"></a><span data-ttu-id="5532f-104">4.與多個使用者共用物件移動</span><span class="sxs-lookup"><span data-stu-id="5532f-104">4. Sharing object movements with multiple users</span></span>

<span data-ttu-id="5532f-105">在本教學課程中，您將了解如何共用物件的移動，讓共用體驗的所有參與者都可以共同作業及查看彼此的互動。</span><span class="sxs-lookup"><span data-stu-id="5532f-105">In this tutorial, you will learn how to share the movements of objects so that all participants of a shared experience can collaborate and view each other's interactions.</span></span>

## <a name="objectives"></a><span data-ttu-id="5532f-106">目標</span><span class="sxs-lookup"><span data-stu-id="5532f-106">Objectives</span></span>

* <span data-ttu-id="5532f-107">設定專案來共用物件的移動</span><span class="sxs-lookup"><span data-stu-id="5532f-107">Configure your project to share the movements of objects</span></span>
* <span data-ttu-id="5532f-108">了解如何建立基本的多使用者共同作業應用程式</span><span class="sxs-lookup"><span data-stu-id="5532f-108">Learn how to build a basic multi-user collaborative app</span></span>

## <a name="preparing-the-scene"></a><span data-ttu-id="5532f-109">準備場景</span><span class="sxs-lookup"><span data-stu-id="5532f-109">Preparing the scene</span></span>

<span data-ttu-id="5532f-110">在本節中，您將藉由新增教學課程預製物件 (Prefab) 來準備場景。</span><span class="sxs-lookup"><span data-stu-id="5532f-110">In this section, you will prepare the scene by adding the tutorial prefab.</span></span>

<span data-ttu-id="5532f-111">在 [專案] 視窗中，瀏覽至 [資產] > [MRTK.Tutorials.MultiUserCapabilities] > [Prefabs] 資料夾，並將 **TableAnchor** 預製物件 (Prefab) 拖曳到階層視窗中的 **SharedPlayground** 物件上方，以將其作為 SharedPlayground 物件的子系來新增至您的場景：</span><span class="sxs-lookup"><span data-stu-id="5532f-111">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Prefabs** folder and drag the **TableAnchor** prefab onto the **SharedPlayground** object in the Hierarchy window to add it to your scene as a child of the SharedPlayground object:</span></span>

![已選取新增 TableAnchor Prefab 的 Unity](images/mr-learning-sharing/sharing-04-section1-step1-1.png)

## <a name="configuring-pun-to-instantiate-the-objects"></a><span data-ttu-id="5532f-113">設定 PUN 以具現化物件</span><span class="sxs-lookup"><span data-stu-id="5532f-113">Configuring PUN to instantiate the objects</span></span>

<span data-ttu-id="5532f-114">在本節中，您會將專案設定為使用在[使用者入門教學課程](mr-learning-base-01.md)中建立的 Rover Explorer 體驗，並定義其將會具現化的位置。</span><span class="sxs-lookup"><span data-stu-id="5532f-114">In this section, you will configure the project to use the Rover Explorer experience created during the [Getting started tutorials](mr-learning-base-01.md) and define where it will be instantiated.</span></span>

<span data-ttu-id="5532f-115">在 [專案] 視窗中，瀏覽至 [資產] > [MRTK.Tutorials.MultiUserCapabilities] > [Resources] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="5532f-115">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Resources** folder.</span></span>

<span data-ttu-id="5532f-116">在 [階層] 視窗中，展開 **NetworkLobby** 物件，然後選取 **NetworkRoom** 子物件，接著在 [偵測器] 視窗中找出 **Photon Room (指令碼)** 元件，並依照下列方式進行設定：</span><span class="sxs-lookup"><span data-stu-id="5532f-116">In the Hierarchy window, expand the **NetworkLobby** object and select the **NetworkRoom** child object, then in the Inspector window, locate the **Photon Room (Script)** component and configure it as follows:</span></span>

* <span data-ttu-id="5532f-117">在 [Rover Explorer Prefab] 欄位中，從 [資源] 資料夾指派 **RoverExplorer_Complete_Variant** Prefab</span><span class="sxs-lookup"><span data-stu-id="5532f-117">To the **Rover Explorer Prefab** field, assign the **RoverExplorer_Complete_Variant** prefab from the Resources folder</span></span>

![已部分設定 Photon Room 元件的 Unity](images/mr-learning-sharing/sharing-04-section2-step1-1.png)

<span data-ttu-id="5532f-119">在仍選取 **NetworkRoom** 子物件的情況下，在 [階層] 視窗中，展開 **TableAnchor** 物件，然後在 [偵測器] 視窗中找出 **Photon Room (指令碼)** 元件，並依照下列方式進行設定：</span><span class="sxs-lookup"><span data-stu-id="5532f-119">With the **NetworkRoom** child object still selected, in the Hierarchy window, expand the **TableAnchor** object, then in the Inspector window, locate the **Photon Room (Script)** component and configure it as follows:</span></span>

* <span data-ttu-id="5532f-120">在 [Rover Explorer 位置] 欄位中，從 [階層] 視窗指派 TableAnchor > **Table** 子物件</span><span class="sxs-lookup"><span data-stu-id="5532f-120">To the **Rover Explorer Location** field, assign the TableAnchor > **Table** child object from the Hierarchy window</span></span>

![已設定 Photon Room 元件的 Unity](images/mr-learning-sharing/sharing-04-section2-step1-2.png)

## <a name="trying-the-experience-with-shared-object-movement"></a><span data-ttu-id="5532f-122">嘗試共用物件移動的體驗</span><span class="sxs-lookup"><span data-stu-id="5532f-122">Trying the experience with shared object movement</span></span>

<span data-ttu-id="5532f-123">如果您現在建立了 Unity 專案並將其部署至 HoloLens，然後回到 Unity，並在應用程式於 HoloLens 上執行時，按下 [開始遊戲] 按鈕進入遊戲模式，當您在 HoloLens 中移動物件時，您將會看到物件在 Unity 中移動：</span><span class="sxs-lookup"><span data-stu-id="5532f-123">If you now build and deploy the Unity project to your HoloLens, and then, back in Unity, press the Play button to enter Game mode while the app is running on your HoloLens, you will see the object move in Unity when you move the object in HoloLens:</span></span>

![動畫，顯示具有網路物件的 Unity](images/mr-learning-sharing/sharing-04-section3-step1-1.gif)

## <a name="congratulations"></a><span data-ttu-id="5532f-125">恭喜！</span><span class="sxs-lookup"><span data-stu-id="5532f-125">Congratulations</span></span>

<span data-ttu-id="5532f-126">您已成功設定專案來同步物件移動，因此使用者可以在其他使用者移動物件時，看到物件移動。</span><span class="sxs-lookup"><span data-stu-id="5532f-126">You have successfully configured your project to synchronize object movements so users can see the objects move when other users move them.</span></span> <span data-ttu-id="5532f-127">在下一個教學課程中，您將會實作功能來配合實體世界中的體驗。</span><span class="sxs-lookup"><span data-stu-id="5532f-127">In the next tutorial, you will implement functionality to align the experience in the physical world.</span></span> <span data-ttu-id="5532f-128">這可確保使用者在實際的實體位置看到彼此，因此物件會出現在相同實體位置，並且針對所有使用者旋轉。</span><span class="sxs-lookup"><span data-stu-id="5532f-128">This will ensure the users see each other in their actual physical location, and so the objects appear in the same physical position and rotation for all users.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="5532f-129">下一個教學課程：5.將 Azure Spatial Anchors 整合到共用體驗</span><span class="sxs-lookup"><span data-stu-id="5532f-129">Next Tutorial: 5. Integrating Azure Spatial Anchors into a shared experience</span></span>](mr-learning-sharing-05.md)
