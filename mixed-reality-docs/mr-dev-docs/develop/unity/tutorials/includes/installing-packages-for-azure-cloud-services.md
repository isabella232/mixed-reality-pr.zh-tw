---
ms.openlocfilehash: 7cd9400ddb83b95f145a9b962be51aaed30df47b
ms.sourcegitcommit: 114c304a416bfe9d9b294c4adbb4c23cbe60ea4e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2021
ms.locfileid: "114224396"
---
# <a name="unity-2020--openxr"></a>[<span data-ttu-id="ccb52-101">Unity 2020 + OpenXR</span><span class="sxs-lookup"><span data-stu-id="ccb52-101">Unity 2020 + OpenXR</span></span>](#tab/openxr)

<span data-ttu-id="ccb52-102">在 Unity 功能表中，選取 [ **window**  >  **封裝管理員** 開啟 [封裝管理員] 視窗，然後確認已安裝 [ **AR Foundation**  >  **4.1.7** 版本]。</span><span class="sxs-lookup"><span data-stu-id="ccb52-102">In the Unity menu, select **Window** > **Package Manager** to open the Package Manager window, then verify that **AR Foundation** > **4.1.7** version is installed.</span></span>

![已選取 AR Foundation 的 Unity 套件管理員](../images/mr-learning-asa/asa-02-section3-step1-1-OpenXR.png)

> [!NOTE]
> <span data-ttu-id="ccb52-104">您正在安裝 AR Foundation 套件，因為 Azure Spatial Anchors SDK 需要此套件，您將在下一節中匯入。</span><span class="sxs-lookup"><span data-stu-id="ccb52-104">You are installing the AR Foundation package because the Azure Spatial Anchors SDK requires it, which you will import in the next section.</span></span>

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="ccb52-105">匯入教學課程資產</span><span class="sxs-lookup"><span data-stu-id="ccb52-105">Importing the tutorial assets</span></span>

<span data-ttu-id="ccb52-106">將 >azurespatialanchors.unitypackage SDK v3.0 新增至您的專案，若要新增套件，請遵循本[教學](/azure/spatial-anchors/how-tos/setup-unity-project?tabs=UPMPackage)課程</span><span class="sxs-lookup"><span data-stu-id="ccb52-106">Add AzurespatialAnchors SDK V2.10 to your project, to add the packages please follow this [tutorial](/azure/spatial-anchors/how-tos/setup-unity-project?tabs=UPMPackage)</span></span>

<span data-ttu-id="ccb52-107">下載並 **依列出順序** 來 **匯入** 下列 Unity 自訂套件：</span><span class="sxs-lookup"><span data-stu-id="ccb52-107">Download and **import** the following Unity custom packages **in the order they are listed**:</span></span>

* [<span data-ttu-id="ccb52-108">AzureStorageForUnity.unitypackage</span><span class="sxs-lookup"><span data-stu-id="ccb52-108">AzureStorageForUnity.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-cloud-services-v2.4.0/AzureStorageForUnity.unitypackage)
* [<span data-ttu-id="ccb52-109">MRTK.AzureCloudServices. XRPlugginManagement. unitypackage</span><span class="sxs-lookup"><span data-stu-id="ccb52-109">MRTK.Tutorials.AzureCloudServices.XRPlugginManagement.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-cloud-services-v2.4.0/MRTK.Tutorials.AzureCloudServices.XRPlugginManagement.unitypackage)

<span data-ttu-id="ccb52-110">匯入教學課程資產之後，您的專案視窗看起來應該會像這樣：</span><span class="sxs-lookup"><span data-stu-id="ccb52-110">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![匯入教學課程資產後的 Unity 階層、場景和專案視窗](../images/mr-learning-azure/tutorial1-section4-step1-1-OpenXR.png)

> [!TIP]
> <span data-ttu-id="ccb52-112">如需如何匯入 Unity 自訂套件的提示，您可以參考匯 [入混合現實工具](../mr-learning-base-04.md#importing-the-tutorial-assets)組的   指示。</span><span class="sxs-lookup"><span data-stu-id="ccb52-112">For a reminder on how to import a Unity custom package, you can refer to the [Importing the Mixed Reality Toolkit](../mr-learning-base-04.md#importing-the-tutorial-assets) instructions.</span></span>

# <a name="unity-2020--windows-xr-plugin"></a>[<span data-ttu-id="ccb52-113">Unity 2020 + Windows XR 外掛程式</span><span class="sxs-lookup"><span data-stu-id="ccb52-113">Unity 2020 + Windows XR Plugin</span></span>](#tab/winxr)

<span data-ttu-id="ccb52-114">在 Unity 功能表中，選取 [ **window**  >  **封裝管理員** 開啟 [封裝管理員] 視窗，然後選取 [ **AR Foundation > 4.0.12** 版本]，然後按一下 [**安裝**] 按鈕以安裝套件：</span><span class="sxs-lookup"><span data-stu-id="ccb52-114">In the Unity menu, select **Window** > **Package Manager** to open the Package Manager window, then select **AR Foundation > 4.0.12** version and click the **Install** button to install the package:</span></span>

![已選取 AR Foundation 的 Unity 套件管理員](../images/mr-learning-asa/asa-02-section3-step1-1-XRSDK.png)

> [!NOTE]
> <span data-ttu-id="ccb52-116">您正在安裝 AR Foundation 套件，因為 Azure Spatial Anchors SDK 需要此套件，您將在下一節中匯入。</span><span class="sxs-lookup"><span data-stu-id="ccb52-116">You are installing the AR Foundation package because the Azure Spatial Anchors SDK requires it, which you will import in the next section.</span></span>

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="ccb52-117">匯入教學課程資產</span><span class="sxs-lookup"><span data-stu-id="ccb52-117">Importing the tutorial assets</span></span>

<span data-ttu-id="ccb52-118">將 >azurespatialanchors.unitypackage SDK v3.0 新增至您的專案，若要新增套件，請遵循本[教學](/azure/spatial-anchors/how-tos/setup-unity-project?tabs=UPMPackage)課程</span><span class="sxs-lookup"><span data-stu-id="ccb52-118">Add AzurespatialAnchors SDK V2.10 to your project, to add the packages please follow this [tutorial](/azure/spatial-anchors/how-tos/setup-unity-project?tabs=UPMPackage)</span></span>

<span data-ttu-id="ccb52-119">下載並 **依列出順序** 來 **匯入** 下列 Unity 自訂套件：</span><span class="sxs-lookup"><span data-stu-id="ccb52-119">Download and **import** the following Unity custom packages **in the order they are listed**:</span></span>

* [<span data-ttu-id="ccb52-120">AzureStorageForUnity.unitypackage</span><span class="sxs-lookup"><span data-stu-id="ccb52-120">AzureStorageForUnity.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-cloud-services-v2.4.0/AzureStorageForUnity.unitypackage)
* [<span data-ttu-id="ccb52-121">MRTK.AzureCloudServices. XRPlugginManagement. unitypackage</span><span class="sxs-lookup"><span data-stu-id="ccb52-121">MRTK.Tutorials.AzureCloudServices.XRPlugginManagement.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-cloud-services-v2.4.0/MRTK.Tutorials.AzureCloudServices.XRPlugginManagement.unitypackage)

<span data-ttu-id="ccb52-122">匯入教學課程資產之後，您的專案視窗看起來應該會像這樣：</span><span class="sxs-lookup"><span data-stu-id="ccb52-122">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![匯入教學課程資產後的 Unity 階層、場景和專案視窗](../images/mr-learning-azure/tutorial1-section4-step1-1-XRSDK.png)

> [!TIP]
> <span data-ttu-id="ccb52-124">如需如何匯入 Unity 自訂套件的提示，您可以參考匯 [入混合現實工具](../mr-learning-base-04.md#importing-the-tutorial-assets)組的   指示。</span><span class="sxs-lookup"><span data-stu-id="ccb52-124">For a reminder on how to import a Unity custom package, you can refer to the [Importing the Mixed Reality Toolkit](../mr-learning-base-04.md#importing-the-tutorial-assets) instructions.</span></span>

# <a name="legacy-wsa"></a>[<span data-ttu-id="ccb52-125">舊版 WSA</span><span class="sxs-lookup"><span data-stu-id="ccb52-125">Legacy WSA</span></span>](#tab/wsa)

<span data-ttu-id="ccb52-126">在 Unity 功能表中，選取 [ **window**  >  **封裝管理員** 開啟 [封裝管理員] 視窗，然後選取 [ **AR Foundation > 3.1.3** 版本]，然後按一下 [**安裝**] 按鈕以安裝套件：</span><span class="sxs-lookup"><span data-stu-id="ccb52-126">In the Unity menu, select **Window** > **Package Manager** to open the Package Manager window, then select **AR Foundation > 3.1.3** version and click the **Install** button to install the package:</span></span>

![已選取 AR Foundation 的 Unity 套件管理員](../images/mr-learning-asa/asa-02-section3-step1-1-Legacy.png)

> [!NOTE]
> <span data-ttu-id="ccb52-128">您正在安裝 AR Foundation 套件，因為 Azure Spatial Anchors SDK 需要此套件，您將在下一節中匯入。</span><span class="sxs-lookup"><span data-stu-id="ccb52-128">You are installing the AR Foundation package because the Azure Spatial Anchors SDK requires it, which you will import in the next section.</span></span>

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="ccb52-129">匯入教學課程資產</span><span class="sxs-lookup"><span data-stu-id="ccb52-129">Importing the tutorial assets</span></span>

<span data-ttu-id="ccb52-130">將 >azurespatialanchors.unitypackage SDK V 2.7.2 新增至您的專案，若要新增套件，請遵循本[教學](/azure/spatial-anchors/how-tos/setup-unity-project?tabs=UPMPackage)課程</span><span class="sxs-lookup"><span data-stu-id="ccb52-130">Add AzurespatialAnchors SDK V2.7.2 to your project, to add the packages please follow this [tutorial](/azure/spatial-anchors/how-tos/setup-unity-project?tabs=UPMPackage)</span></span>

<span data-ttu-id="ccb52-131">下載並 **依列出順序** 來 **匯入** 下列 Unity 自訂套件：</span><span class="sxs-lookup"><span data-stu-id="ccb52-131">Download and **import** the following Unity custom packages **in the order they are listed**:</span></span>

* [<span data-ttu-id="ccb52-132">AzureStorageForUnity.unitypackage</span><span class="sxs-lookup"><span data-stu-id="ccb52-132">AzureStorageForUnity.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-cloud-services-v2.4.0/AzureStorageForUnity.unitypackage)
* [<span data-ttu-id="ccb52-133">MRTK.AzureCloudServices. LegacyWSA. unitypackage</span><span class="sxs-lookup"><span data-stu-id="ccb52-133">MRTK.Tutorials.AzureCloudServices.LegacyWSA.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-cloud-services-v2.4.0/MRTK.Tutorials.AzureCloudServices.LegacyWSA.unitypackage)

<span data-ttu-id="ccb52-134">匯入教學課程資產之後，您的專案視窗看起來應該會像這樣：</span><span class="sxs-lookup"><span data-stu-id="ccb52-134">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![匯入教學課程資產後的 Unity 階層、場景和專案視窗](../images/mr-learning-azure/tutorial1-section4-step1-1-Legacy.png)

> [!NOTE]
> <span data-ttu-id="ccb52-136">如果您看到任何有關於 'WorldAnchor.SetNativeSpatialAnchorPtr(IntPtr)' 和 'WorldAnchor.GetNativeSpatialAnchorPtr()' 已過時的 CS0618 警告，則可以忽略這些警告。</span><span class="sxs-lookup"><span data-stu-id="ccb52-136">If you see any CS0618 warnings regarding 'WorldAnchor.SetNativeSpatialAnchorPtr(IntPtr)' and 'WorldAnchor.GetNativeSpatialAnchorPtr()' being obsolete, you can ignore these warnings.</span></span>

> [!TIP]
> <span data-ttu-id="ccb52-137">如需如何匯入 Unity 自訂套件的提示，您可以參考匯 [入混合現實工具](../mr-learning-base-04.md#importing-the-tutorial-assets)組的   指示。</span><span class="sxs-lookup"><span data-stu-id="ccb52-137">For a reminder on how to import a Unity custom package, you can refer to the [Importing the Mixed Reality Toolkit](../mr-learning-base-04.md#importing-the-tutorial-assets) instructions.</span></span>
