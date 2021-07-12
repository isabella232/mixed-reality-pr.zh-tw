---
ms.openlocfilehash: dbaace96246f28050ff6fb189d9b626be6b0ec9e
ms.sourcegitcommit: e380d56f5504be4e4f069394a58cf0147eb33b66
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2021
ms.locfileid: "113603706"
---
# <a name="openxr"></a>[OpenXR](#tab/openxr)

若要使用 MRTK 開始使用 **新的 Unity 專案** ，請從 MRTK 教學課程中的步驟2開始：

> [!div class="nextstepaction"]
> [使用 MRTK 設定新的 OpenXR 專案](../../tutorials/mr-learning-base-02.md?tabs=openxr)

如果您要將 **現有的 MRTK 專案升級至 OpenXR**，您必須先將 MRTK-Unity 升級為最新版本， (版本2.7.2 或更新版本) 以取得與混合現實 OpenXR 外掛程式相容的金鑰修正。  使用「 [混合現實」功能工具](../../welcome-to-mr-feature-tool.md) 升級至最新版本的 MRTK，然後遵循 [下列手動 OpenXR 設定步驟](#manual-setup-without-mrtk)。 [若要深入瞭解如何將現有的 MRTK 專案遷移至 OpenXR](/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk#configuring-mrtk-for-the-xr-sdk-pipeline)，請參閱 MRTK 檔。

> [!NOTE]
> 從早于 **2.5.3** 的舊版 MRTK 進行升級時，請確定 [資產/MixedRealityToolkit] 中的下列程式程式碼位於 [ **資產/] 中。產生/link.xml** 檔案：
>
> ```xml
> <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>
> ```
>
> 如果您開始使用 MRTK 2.5.4 或更新版本，則預設會新增這一行。

# <a name="windows-xr"></a>[WindowsXR](#tab/windowsxr)

若要使用 MRTK 開始使用 **新的 Unity 專案** ，請從 MRTK 教學課程中的步驟2開始：

> [!div class="nextstepaction"]
> [使用 MRTK 設定新的 Windows XR 專案](../../tutorials/mr-learning-base-02.md?tabs=winxr)

# <a name="legacy-xr"></a>[傳統 XR](#tab/legacy)

若要使用 MRTK 開始使用 **新的 Unity 專案** ，請從 MRTK 教學課程中的步驟2開始：

> [!div class="nextstepaction"]
> [使用 MRTK 設定新的舊版 XR 專案](../../tutorials/mr-learning-base-02.md?tabs=wsa)