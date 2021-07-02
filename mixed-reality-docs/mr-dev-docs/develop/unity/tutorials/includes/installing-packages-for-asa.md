---
ms.openlocfilehash: 0a89ef77bee7eff83d4599c46ffd2681c99b2165
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175568"
---
# <a name="unity-2020--openxr"></a>[<span data-ttu-id="69ba6-101">Unity 2020 + OpenXR</span><span class="sxs-lookup"><span data-stu-id="69ba6-101">Unity 2020 + OpenXR</span></span>](#tab/openxr)

<span data-ttu-id="69ba6-102">在 Unity 功能表中，選取 [ **window**  >  **封裝管理員** 開啟 [封裝管理員] 視窗，然後確認已安裝 [ **AR Foundation**  >  **4.1.7** 版本]。</span><span class="sxs-lookup"><span data-stu-id="69ba6-102">In the Unity menu, select **Window** > **Package Manager** to open the Package Manager window, then verify that **AR Foundation** > **4.1.7** version is installed.</span></span>

![已選取 AR Foundation 的 Unity 套件管理員](../images/mr-learning-asa/asa-02-section3-step1-1-OpenXR.png)

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="69ba6-104">匯入教學課程資產</span><span class="sxs-lookup"><span data-stu-id="69ba6-104">Importing the tutorial assets</span></span>

<span data-ttu-id="69ba6-105">將 >azurespatialanchors.unitypackage SDK v3.0 新增至您的專案，若要新增套件，請遵循本[教學](/azure/spatial-anchors/how-tos/setup-unity-project?tabs=UPMPackage)課程</span><span class="sxs-lookup"><span data-stu-id="69ba6-105">Add AzurespatialAnchors SDK V2.10 to your project, to add the packages please follow this [tutorial](/azure/spatial-anchors/how-tos/setup-unity-project?tabs=UPMPackage)</span></span>

<span data-ttu-id="69ba6-106">下載並 **依列出順序** 來 **匯入** 下列 Unity 自訂套件：</span><span class="sxs-lookup"><span data-stu-id="69ba6-106">Download and **import** the following Unity custom packages **in the order they are listed**:</span></span>

* [<span data-ttu-id="69ba6-107">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage</span><span class="sxs-lookup"><span data-stu-id="69ba6-107">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage)
* [<span data-ttu-id="69ba6-108">MRTK.HoloLens2. >azurespatialanchors.unitypackage. XRplugginManagement. 2.5.3. unitypackage</span><span class="sxs-lookup"><span data-stu-id="69ba6-108">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.XRplugginManagement.2.5.3.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.5.3.1/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.XRplugginManagement.2.5.3.unitypackage)

<span data-ttu-id="69ba6-109">匯入教學課程資產之後，您的專案視窗看起來應該會像這樣：</span><span class="sxs-lookup"><span data-stu-id="69ba6-109">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![匯入教學課程資產後的 Unity 階層、場景和專案視窗](../images/mr-learning-asa/asa-02-section3-step1-2-OpenXR.png)

> [!TIP]
> <span data-ttu-id="69ba6-111">如需有關如何匯入 Unity 自訂套件的提醒，您可以參考匯 [入教學課程資產](../mr-learning-base-04.md#importing-the-tutorial-assets)的   指示。</span><span class="sxs-lookup"><span data-stu-id="69ba6-111">For a reminder on how to import a Unity custom package, you can refer to the [Importing the tutorial assets](../mr-learning-base-04.md#importing-the-tutorial-assets) instructions.</span></span>

# <a name="unity-2020--windows-xr-plugin"></a>[<span data-ttu-id="69ba6-112">Unity 2020 + Windows XR 外掛程式</span><span class="sxs-lookup"><span data-stu-id="69ba6-112">Unity 2020 + Windows XR Plugin</span></span>](#tab/winxr)

<span data-ttu-id="69ba6-113">在 Unity 功能表中，選取 [ **window**  >  **封裝管理員** 開啟 [封裝管理員] 視窗，然後選取 [ **AR Foundation > 4.0.12** 版本]，然後按一下 [**安裝**] 按鈕以安裝套件：</span><span class="sxs-lookup"><span data-stu-id="69ba6-113">In the Unity menu, select **Window** > **Package Manager** to open the Package Manager window, then select **AR Foundation > 4.0.12** version and click the **Install** button to install the package:</span></span>

![已選取 AR Foundation 的 Unity 套件管理員](../images/mr-learning-asa/asa-02-section3-step1-1-XRSDK.png)

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="69ba6-115">匯入教學課程資產</span><span class="sxs-lookup"><span data-stu-id="69ba6-115">Importing the tutorial assets</span></span>

<span data-ttu-id="69ba6-116">將 >azurespatialanchors.unitypackage SDK v3.0 新增至您的專案，若要新增套件，請遵循本[教學](/azure/spatial-anchors/how-tos/setup-unity-project?tabs=UPMPackage)課程</span><span class="sxs-lookup"><span data-stu-id="69ba6-116">Add AzurespatialAnchors SDK V2.10 to your project, to add the packages please follow this [tutorial](/azure/spatial-anchors/how-tos/setup-unity-project?tabs=UPMPackage)</span></span>

<span data-ttu-id="69ba6-117">下載並 **依列出順序** 來 **匯入** 下列 Unity 自訂套件：</span><span class="sxs-lookup"><span data-stu-id="69ba6-117">Download and **import** the following Unity custom packages **in the order they are listed**:</span></span>

* [<span data-ttu-id="69ba6-118">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage</span><span class="sxs-lookup"><span data-stu-id="69ba6-118">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage)
* [<span data-ttu-id="69ba6-119">MRTK.HoloLens2. >azurespatialanchors.unitypackage. XRplugginManagement. 2.5.3. unitypackage</span><span class="sxs-lookup"><span data-stu-id="69ba6-119">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.XRplugginManagement.2.5.3.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.5.3.1/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.XRplugginManagement.2.5.3.unitypackage)

<span data-ttu-id="69ba6-120">匯入教學課程資產之後，您的專案視窗看起來應該會像這樣：</span><span class="sxs-lookup"><span data-stu-id="69ba6-120">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![匯入教學課程資產後的 Unity 階層、場景和專案視窗](../images/mr-learning-asa/asa-02-section3-step1-2-XRSDK.PNG)

> [!TIP]
> <span data-ttu-id="69ba6-122">如需有關如何匯入 Unity 自訂套件的提醒，您可以參考匯 [入教學課程資產](../mr-learning-base-04.md#importing-the-tutorial-assets)的   指示。</span><span class="sxs-lookup"><span data-stu-id="69ba6-122">For a reminder on how to import a Unity custom package, you can refer to the [Importing the tutorial assets](../mr-learning-base-04.md#importing-the-tutorial-assets) instructions.</span></span>

# <a name="legacy-wsa"></a>[<span data-ttu-id="69ba6-123">舊版 WSA</span><span class="sxs-lookup"><span data-stu-id="69ba6-123">Legacy WSA</span></span>](#tab/wsa)

<span data-ttu-id="69ba6-124">在 Unity 功能表中，選取 [ **window**  >  **封裝管理員** 開啟 [封裝管理員] 視窗，然後選取 [ **AR Foundation > 3.1.3** 版本]，然後按一下 [**安裝**] 按鈕以安裝套件：</span><span class="sxs-lookup"><span data-stu-id="69ba6-124">In the Unity menu, select **Window** > **Package Manager** to open the Package Manager window, then select **AR Foundation > 3.1.3** version and click the **Install** button to install the package:</span></span>

![已選取 AR Foundation 的 Unity 套件管理員](../images/mr-learning-asa/asa-02-section3-step1-1-Legacy.png)

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="69ba6-126">匯入教學課程資產</span><span class="sxs-lookup"><span data-stu-id="69ba6-126">Importing the tutorial assets</span></span>

<span data-ttu-id="69ba6-127">將 >azurespatialanchors.unitypackage SDK V 2.7.2 新增至您的專案，若要新增套件，請遵循本[教學](/azure/spatial-anchors/how-tos/setup-unity-project?tabs=UPMPackage)課程</span><span class="sxs-lookup"><span data-stu-id="69ba6-127">Add AzurespatialAnchors SDK V2.7.2 to your project, to add the packages please follow this [tutorial](/azure/spatial-anchors/how-tos/setup-unity-project?tabs=UPMPackage)</span></span>

<span data-ttu-id="69ba6-128">下載並 **依列出順序** 來 **匯入** 下列 Unity 自訂套件：</span><span class="sxs-lookup"><span data-stu-id="69ba6-128">Download and **import** the following Unity custom packages **in the order they are listed**:</span></span>

* [<span data-ttu-id="69ba6-129">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage</span><span class="sxs-lookup"><span data-stu-id="69ba6-129">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage)
* [<span data-ttu-id="69ba6-130">MRTK.HoloLens2. >azurespatialanchors.unitypackage. LegacyWSA. 2.5.3. unitypackage</span><span class="sxs-lookup"><span data-stu-id="69ba6-130">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.LegacyWSA.2.5.3.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.5.3.1/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.LegacyWSA.2.5.3.unitypackage)

<span data-ttu-id="69ba6-131">匯入教學課程資產之後，您的專案視窗看起來應該會像這樣：</span><span class="sxs-lookup"><span data-stu-id="69ba6-131">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![匯入教學課程資產後的 Unity 階層、場景和專案視窗](../images/mr-learning-asa/asa-02-section3-step1-2-Legacy.png)

> [!NOTE]
> <span data-ttu-id="69ba6-133">如果您看到任何有關於 'WorldAnchor.SetNativeSpatialAnchorPtr(IntPtr)' 已過時的 CS0618 警告，您可以忽略這些警告。</span><span class="sxs-lookup"><span data-stu-id="69ba6-133">If you see any CS0618 warnings regarding 'WorldAnchor.SetNativeSpatialAnchorPtr(IntPtr)' is obsolete, you can ignore these warnings.</span></span>

> [!TIP]
> <span data-ttu-id="69ba6-134">如需有關如何匯入 Unity 自訂套件的提醒，您可以參考匯 [入教學課程資產](../mr-learning-base-04.md#importing-the-tutorial-assets)的   指示。</span><span class="sxs-lookup"><span data-stu-id="69ba6-134">For a reminder on how to import a Unity custom package, you can refer to the [Importing the tutorial assets](../mr-learning-base-04.md#importing-the-tutorial-assets) instructions.</span></span>
