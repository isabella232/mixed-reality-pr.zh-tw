---
ms.openlocfilehash: dbaace96246f28050ff6fb189d9b626be6b0ec9e
ms.sourcegitcommit: e380d56f5504be4e4f069394a58cf0147eb33b66
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2021
ms.locfileid: "113603706"
---
# <a name="openxr"></a>[<span data-ttu-id="f1a59-101">OpenXR</span><span class="sxs-lookup"><span data-stu-id="f1a59-101">OpenXR</span></span>](#tab/openxr)

<span data-ttu-id="f1a59-102">若要使用 MRTK 開始使用 **新的 Unity 專案** ，請從 MRTK 教學課程中的步驟2開始：</span><span class="sxs-lookup"><span data-stu-id="f1a59-102">To get started with a **new Unity project** using MRTK, start from step 2 in the MRTK tutorial:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="f1a59-103">使用 MRTK 設定新的 OpenXR 專案</span><span class="sxs-lookup"><span data-stu-id="f1a59-103">Set up a new OpenXR project with MRTK</span></span>](../../tutorials/mr-learning-base-02.md?tabs=openxr)

<span data-ttu-id="f1a59-104">如果您要將 **現有的 MRTK 專案升級至 OpenXR**，您必須先將 MRTK-Unity 升級為最新版本， (版本2.7.2 或更新版本) 以取得與混合現實 OpenXR 外掛程式相容的金鑰修正。</span><span class="sxs-lookup"><span data-stu-id="f1a59-104">If you're upgrading an **existing MRTK project to OpenXR**, you'll first want to upgrade MRTK-Unity to the latest version (version 2.7.2 or later) to get key fixes for compatibility with the Mixed Reality OpenXR plugin.</span></span>  <span data-ttu-id="f1a59-105">使用「 [混合現實」功能工具](../../welcome-to-mr-feature-tool.md) 升級至最新版本的 MRTK，然後遵循 [下列手動 OpenXR 設定步驟](#manual-setup-without-mrtk)。</span><span class="sxs-lookup"><span data-stu-id="f1a59-105">Use the [Mixed Reality Feature Tool](../../welcome-to-mr-feature-tool.md) to upgrade to the latest version of MRTK and then follow the [manual OpenXR setup steps below](#manual-setup-without-mrtk).</span></span> <span data-ttu-id="f1a59-106">[若要深入瞭解如何將現有的 MRTK 專案遷移至 OpenXR](/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk#configuring-mrtk-for-the-xr-sdk-pipeline)，請參閱 MRTK 檔。</span><span class="sxs-lookup"><span data-stu-id="f1a59-106">See the MRTK documentation for [more in-depth information on migrating an existing MRTK project to OpenXR](/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk#configuring-mrtk-for-the-xr-sdk-pipeline).</span></span>

> [!NOTE]
> <span data-ttu-id="f1a59-107">從早于 **2.5.3** 的舊版 MRTK 進行升級時，請確定 [資產/MixedRealityToolkit] 中的下列程式程式碼位於 [ **資產/] 中。產生/link.xml** 檔案：</span><span class="sxs-lookup"><span data-stu-id="f1a59-107">When upgrading from a previous version of MRTK older than **2.5.3**, ensure the following line is in the **Assets/MixedRealityToolkit.Generated/link.xml** file:</span></span>
>
> ```xml
> <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>
> ```
>
> <span data-ttu-id="f1a59-108">如果您開始使用 MRTK 2.5.4 或更新版本，則預設會新增這一行。</span><span class="sxs-lookup"><span data-stu-id="f1a59-108">This line will be added by default if you started with MRTK 2.5.4 or newer.</span></span>

# <a name="windows-xr"></a>[<span data-ttu-id="f1a59-109">WindowsXR</span><span class="sxs-lookup"><span data-stu-id="f1a59-109">Windows XR</span></span>](#tab/windowsxr)

<span data-ttu-id="f1a59-110">若要使用 MRTK 開始使用 **新的 Unity 專案** ，請從 MRTK 教學課程中的步驟2開始：</span><span class="sxs-lookup"><span data-stu-id="f1a59-110">To get started with a **new Unity project** using MRTK, start from step 2 in the MRTK tutorial:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="f1a59-111">使用 MRTK 設定新的 Windows XR 專案</span><span class="sxs-lookup"><span data-stu-id="f1a59-111">Set up a new Windows XR project with MRTK</span></span>](../../tutorials/mr-learning-base-02.md?tabs=winxr)

# <a name="legacy-xr"></a>[<span data-ttu-id="f1a59-112">傳統 XR</span><span class="sxs-lookup"><span data-stu-id="f1a59-112">Legacy XR</span></span>](#tab/legacy)

<span data-ttu-id="f1a59-113">若要使用 MRTK 開始使用 **新的 Unity 專案** ，請從 MRTK 教學課程中的步驟2開始：</span><span class="sxs-lookup"><span data-stu-id="f1a59-113">To get started with a **new Unity project** using MRTK, start from step 2 in the MRTK tutorial:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="f1a59-114">使用 MRTK 設定新的舊版 XR 專案</span><span class="sxs-lookup"><span data-stu-id="f1a59-114">Set up a new Legacy XR project with MRTK</span></span>](../../tutorials/mr-learning-base-02.md?tabs=wsa)