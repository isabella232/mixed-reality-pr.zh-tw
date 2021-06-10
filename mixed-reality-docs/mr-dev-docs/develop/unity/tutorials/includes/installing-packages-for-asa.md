---
ms.openlocfilehash: 62475f32ac0a91583bc80456c1b9d1b0d8bbb539
ms.sourcegitcommit: b4fd969b9c2e6313aa728b0dbee4b25014668720
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2021
ms.locfileid: "111403477"
---
# <a name="unity-2020--openxr"></a>[<span data-ttu-id="35b41-101">Unity 2020 + OpenXR</span><span class="sxs-lookup"><span data-stu-id="35b41-101">Unity 2020 + OpenXR</span></span>](#tab/openxr)

<span data-ttu-id="35b41-102">在 Unity 功能表中，選取 [ **window**  >  **封裝管理員** 開啟 [封裝管理員] 視窗，然後確認已安裝 [ **AR Foundation**  >  **4.1.7** 版本]。</span><span class="sxs-lookup"><span data-stu-id="35b41-102">In the Unity menu, select **Window** > **Package Manager** to open the Package Manager window, then verify that **AR Foundation** > **4.1.7** version is installed.</span></span>

![已選取 AR Foundation 的 Unity 套件管理員](../images/mr-learning-asa/asa-02-section3-step1-1-OpenXR.png)

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="35b41-104">匯入教學課程資產</span><span class="sxs-lookup"><span data-stu-id="35b41-104">Importing the tutorial assets</span></span>

<span data-ttu-id="35b41-105">將 >azurespatialanchors.unitypackage SDK v3.0 新增至您的專案，若要新增套件，請遵循本[教學](/azure/spatial-anchors/how-tos/setup-unity-project?tabs=UPMPackage)課程</span><span class="sxs-lookup"><span data-stu-id="35b41-105">Add AzurespatialAnchors SDK V2.10 to your project, to add the packages please follow this [tutorial](/azure/spatial-anchors/how-tos/setup-unity-project?tabs=UPMPackage)</span></span>

<span data-ttu-id="35b41-106">下載並 **依列出順序** 來 **匯入** 下列 Unity 自訂套件：</span><span class="sxs-lookup"><span data-stu-id="35b41-106">Download and **import** the following Unity custom packages **in the order they are listed**:</span></span>

* [<span data-ttu-id="35b41-107">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage</span><span class="sxs-lookup"><span data-stu-id="35b41-107">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage)
* [<span data-ttu-id="35b41-108">MRTK.HoloLens2. >azurespatialanchors.unitypackage. XRplugginManagement. 2.5.3. unitypackage</span><span class="sxs-lookup"><span data-stu-id="35b41-108">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.XRplugginManagement.2.5.3.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.5.3.1/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.XRplugginManagement.2.5.3.unitypackage)

<span data-ttu-id="35b41-109">匯入教學課程資產之後，您的專案視窗看起來應該會像這樣：</span><span class="sxs-lookup"><span data-stu-id="35b41-109">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![匯入教學課程資產後的 Unity 階層、場景和專案視窗](../images/mr-learning-asa/asa-02-section3-step1-2-OpenXR.png)

> [!TIP]
> <span data-ttu-id="35b41-111">如需有關如何匯入 Unity 自訂套件的提醒，您可以參考匯 [入教學課程資產](../mr-learning-base-02.md#importing-the-tutorial-assets)的   指示。</span><span class="sxs-lookup"><span data-stu-id="35b41-111">For a reminder on how to import a Unity custom package, you can refer to the [Importing the tutorial assets](../mr-learning-base-02.md#importing-the-tutorial-assets) instructions.</span></span>

# <a name="unity-2020--windows-xr-plugin"></a>[<span data-ttu-id="35b41-112">Unity 2020 + Windows XR 外掛程式</span><span class="sxs-lookup"><span data-stu-id="35b41-112">Unity 2020 + Windows XR Plugin</span></span>](#tab/winxr)

<span data-ttu-id="35b41-113">在 Unity 功能表中，選取 [ **window**  >  **封裝管理員** 開啟 [封裝管理員] 視窗，然後選取 [ **AR Foundation > 4.0.12** 版本]，然後按一下 [**安裝**] 按鈕以安裝套件：</span><span class="sxs-lookup"><span data-stu-id="35b41-113">In the Unity menu, select **Window** > **Package Manager** to open the Package Manager window, then select **AR Foundation > 4.0.12** version and click the **Install** button to install the package:</span></span>

![已選取 AR Foundation 的 Unity 套件管理員](../images/mr-learning-asa/asa-02-section3-step1-1-XRSDK.png)

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="35b41-115">匯入教學課程資產</span><span class="sxs-lookup"><span data-stu-id="35b41-115">Importing the tutorial assets</span></span>

<span data-ttu-id="35b41-116">將 >azurespatialanchors.unitypackage SDK v3.0 新增至您的專案，若要新增套件，請遵循本[教學](/azure/spatial-anchors/how-tos/setup-unity-project?tabs=UPMPackage)課程</span><span class="sxs-lookup"><span data-stu-id="35b41-116">Add AzurespatialAnchors SDK V2.10 to your project, to add the packages please follow this [tutorial](/azure/spatial-anchors/how-tos/setup-unity-project?tabs=UPMPackage)</span></span>

<span data-ttu-id="35b41-117">下載並 **依列出順序** 來 **匯入** 下列 Unity 自訂套件：</span><span class="sxs-lookup"><span data-stu-id="35b41-117">Download and **import** the following Unity custom packages **in the order they are listed**:</span></span>

* [<span data-ttu-id="35b41-118">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage</span><span class="sxs-lookup"><span data-stu-id="35b41-118">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage)
* [<span data-ttu-id="35b41-119">MRTK.HoloLens2. >azurespatialanchors.unitypackage. XRplugginManagement. 2.5.3. unitypackage</span><span class="sxs-lookup"><span data-stu-id="35b41-119">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.XRplugginManagement.2.5.3.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.5.3.1/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.XRplugginManagement.2.5.3.unitypackage)

<span data-ttu-id="35b41-120">匯入教學課程資產之後，您的專案視窗看起來應該會像這樣：</span><span class="sxs-lookup"><span data-stu-id="35b41-120">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![匯入教學課程資產後的 Unity 階層、場景和專案視窗](../images/mr-learning-asa/asa-02-section3-step1-2-XRSDK.PNG)

> [!TIP]
> <span data-ttu-id="35b41-122">如需有關如何匯入 Unity 自訂套件的提醒，您可以參考匯 [入教學課程資產](../mr-learning-base-02.md#importing-the-tutorial-assets)的   指示。</span><span class="sxs-lookup"><span data-stu-id="35b41-122">For a reminder on how to import a Unity custom package, you can refer to the [Importing the tutorial assets](../mr-learning-base-02.md#importing-the-tutorial-assets) instructions.</span></span>

# <a name="legacy-wsa"></a>[<span data-ttu-id="35b41-123">舊版 WSA</span><span class="sxs-lookup"><span data-stu-id="35b41-123">Legacy WSA</span></span>](#tab/wsa)

<span data-ttu-id="35b41-124">在 Unity 功能表中，選取 [ **window**  >  **封裝管理員** 開啟 [封裝管理員] 視窗，然後選取 [ **AR Foundation > 3.1.3** 版本]，然後按一下 [**安裝**] 按鈕以安裝套件：</span><span class="sxs-lookup"><span data-stu-id="35b41-124">In the Unity menu, select **Window** > **Package Manager** to open the Package Manager window, then select **AR Foundation > 3.1.3** version and click the **Install** button to install the package:</span></span>

![已選取 AR Foundation 的 Unity 套件管理員](../images/mr-learning-asa/asa-02-section3-step1-1-Legacy.png)

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="35b41-126">匯入教學課程資產</span><span class="sxs-lookup"><span data-stu-id="35b41-126">Importing the tutorial assets</span></span>

<span data-ttu-id="35b41-127">將 >azurespatialanchors.unitypackage SDK V 2.7.2 新增至您的專案，若要新增套件，請遵循本[教學](/azure/spatial-anchors/how-tos/setup-unity-project?tabs=UPMPackage)課程</span><span class="sxs-lookup"><span data-stu-id="35b41-127">Add AzurespatialAnchors SDK V2.7.2 to your project, to add the packages please follow this [tutorial](/azure/spatial-anchors/how-tos/setup-unity-project?tabs=UPMPackage)</span></span>

<span data-ttu-id="35b41-128">下載並 **依列出順序** 來 **匯入** 下列 Unity 自訂套件：</span><span class="sxs-lookup"><span data-stu-id="35b41-128">Download and **import** the following Unity custom packages **in the order they are listed**:</span></span>

* [<span data-ttu-id="35b41-129">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage</span><span class="sxs-lookup"><span data-stu-id="35b41-129">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage)
* [<span data-ttu-id="35b41-130">MRTK.HoloLens2. >azurespatialanchors.unitypackage. LegacyWSA. 2.5.3. unitypackage</span><span class="sxs-lookup"><span data-stu-id="35b41-130">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.LegacyWSA.2.5.3.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.5.3.1/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.LegacyWSA.2.5.3.unitypackage)

<span data-ttu-id="35b41-131">匯入教學課程資產之後，您的專案視窗看起來應該會像這樣：</span><span class="sxs-lookup"><span data-stu-id="35b41-131">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![匯入教學課程資產後的 Unity 階層、場景和專案視窗](../images/mr-learning-asa/asa-02-section3-step1-2-Legacy.png)

> [!NOTE]
> <span data-ttu-id="35b41-133">如果您看到任何有關於 'WorldAnchor.SetNativeSpatialAnchorPtr(IntPtr)' 已過時的 CS0618 警告，您可以忽略這些警告。</span><span class="sxs-lookup"><span data-stu-id="35b41-133">If you see any CS0618 warnings regarding 'WorldAnchor.SetNativeSpatialAnchorPtr(IntPtr)' is obsolete, you can ignore these warnings.</span></span>

> [!TIP]
> <span data-ttu-id="35b41-134">如需有關如何匯入 Unity 自訂套件的提醒，您可以參考匯 [入教學課程資產](../mr-learning-base-02.md#importing-the-tutorial-assets)的   指示。</span><span class="sxs-lookup"><span data-stu-id="35b41-134">For a reminder on how to import a Unity custom package, you can refer to the [Importing the tutorial assets](../mr-learning-base-02.md#importing-the-tutorial-assets) instructions.</span></span>
