---
ms.openlocfilehash: 7cd9400ddb83b95f145a9b962be51aaed30df47b
ms.sourcegitcommit: 114c304a416bfe9d9b294c4adbb4c23cbe60ea4e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2021
ms.locfileid: "114224396"
---
# <a name="unity-2020--openxr"></a>[Unity 2020 + OpenXR](#tab/openxr)

在 Unity 功能表中，選取 [ **window**  >  **封裝管理員** 開啟 [封裝管理員] 視窗，然後確認已安裝 [ **AR Foundation**  >  **4.1.7** 版本]。

![已選取 AR Foundation 的 Unity 套件管理員](../images/mr-learning-asa/asa-02-section3-step1-1-OpenXR.png)

> [!NOTE]
> 您正在安裝 AR Foundation 套件，因為 Azure Spatial Anchors SDK 需要此套件，您將在下一節中匯入。

## <a name="importing-the-tutorial-assets"></a>匯入教學課程資產

將 >azurespatialanchors.unitypackage SDK v3.0 新增至您的專案，若要新增套件，請遵循本[教學](/azure/spatial-anchors/how-tos/setup-unity-project?tabs=UPMPackage)課程

下載並 **依列出順序** 來 **匯入** 下列 Unity 自訂套件：

* [AzureStorageForUnity.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-cloud-services-v2.4.0/AzureStorageForUnity.unitypackage)
* [MRTK.AzureCloudServices. XRPlugginManagement. unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-cloud-services-v2.4.0/MRTK.Tutorials.AzureCloudServices.XRPlugginManagement.unitypackage)

匯入教學課程資產之後，您的專案視窗看起來應該會像這樣：

![匯入教學課程資產後的 Unity 階層、場景和專案視窗](../images/mr-learning-azure/tutorial1-section4-step1-1-OpenXR.png)

> [!TIP]
> 如需如何匯入 Unity 自訂套件的提示，您可以參考匯 [入混合現實工具](../mr-learning-base-04.md#importing-the-tutorial-assets)組的   指示。

# <a name="unity-2020--windows-xr-plugin"></a>[Unity 2020 + Windows XR 外掛程式](#tab/winxr)

在 Unity 功能表中，選取 [ **window**  >  **封裝管理員** 開啟 [封裝管理員] 視窗，然後選取 [ **AR Foundation > 4.0.12** 版本]，然後按一下 [**安裝**] 按鈕以安裝套件：

![已選取 AR Foundation 的 Unity 套件管理員](../images/mr-learning-asa/asa-02-section3-step1-1-XRSDK.png)

> [!NOTE]
> 您正在安裝 AR Foundation 套件，因為 Azure Spatial Anchors SDK 需要此套件，您將在下一節中匯入。

## <a name="importing-the-tutorial-assets"></a>匯入教學課程資產

將 >azurespatialanchors.unitypackage SDK v3.0 新增至您的專案，若要新增套件，請遵循本[教學](/azure/spatial-anchors/how-tos/setup-unity-project?tabs=UPMPackage)課程

下載並 **依列出順序** 來 **匯入** 下列 Unity 自訂套件：

* [AzureStorageForUnity.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-cloud-services-v2.4.0/AzureStorageForUnity.unitypackage)
* [MRTK.AzureCloudServices. XRPlugginManagement. unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-cloud-services-v2.4.0/MRTK.Tutorials.AzureCloudServices.XRPlugginManagement.unitypackage)

匯入教學課程資產之後，您的專案視窗看起來應該會像這樣：

![匯入教學課程資產後的 Unity 階層、場景和專案視窗](../images/mr-learning-azure/tutorial1-section4-step1-1-XRSDK.png)

> [!TIP]
> 如需如何匯入 Unity 自訂套件的提示，您可以參考匯 [入混合現實工具](../mr-learning-base-04.md#importing-the-tutorial-assets)組的   指示。

# <a name="legacy-wsa"></a>[舊版 WSA](#tab/wsa)

在 Unity 功能表中，選取 [ **window**  >  **封裝管理員** 開啟 [封裝管理員] 視窗，然後選取 [ **AR Foundation > 3.1.3** 版本]，然後按一下 [**安裝**] 按鈕以安裝套件：

![已選取 AR Foundation 的 Unity 套件管理員](../images/mr-learning-asa/asa-02-section3-step1-1-Legacy.png)

> [!NOTE]
> 您正在安裝 AR Foundation 套件，因為 Azure Spatial Anchors SDK 需要此套件，您將在下一節中匯入。

## <a name="importing-the-tutorial-assets"></a>匯入教學課程資產

將 >azurespatialanchors.unitypackage SDK V 2.7.2 新增至您的專案，若要新增套件，請遵循本[教學](/azure/spatial-anchors/how-tos/setup-unity-project?tabs=UPMPackage)課程

下載並 **依列出順序** 來 **匯入** 下列 Unity 自訂套件：

* [AzureStorageForUnity.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-cloud-services-v2.4.0/AzureStorageForUnity.unitypackage)
* [MRTK.AzureCloudServices. LegacyWSA. unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-cloud-services-v2.4.0/MRTK.Tutorials.AzureCloudServices.LegacyWSA.unitypackage)

匯入教學課程資產之後，您的專案視窗看起來應該會像這樣：

![匯入教學課程資產後的 Unity 階層、場景和專案視窗](../images/mr-learning-azure/tutorial1-section4-step1-1-Legacy.png)

> [!NOTE]
> 如果您看到任何有關於 'WorldAnchor.SetNativeSpatialAnchorPtr(IntPtr)' 和 'WorldAnchor.GetNativeSpatialAnchorPtr()' 已過時的 CS0618 警告，則可以忽略這些警告。

> [!TIP]
> 如需如何匯入 Unity 自訂套件的提示，您可以參考匯 [入混合現實工具](../mr-learning-base-04.md#importing-the-tutorial-assets)組的   指示。
