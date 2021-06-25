---
title: 設定您的 XR 設定
description: 隨時掌握最新的 Unity XR 設定建議，以進行 HoloLens 應用程式開發。
author: hferrone
ms.author: v-hferrone
ms.date: 04/22/2021
ms.topic: article
keywords: mixedrealitytoolkit、mixedrealitytoolkit-unity、mixed reality 耳機、windows mixed reality 耳機、虛擬實境耳機、unity
ms.openlocfilehash: d265725caf95379dfa01baa6dad1b7927fbeca5c
ms.sourcegitcommit: 72970dbe6674e28c250f741e50a44a238bb162d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2021
ms.locfileid: "112906936"
---
# <a name="setting-up-your-xr-configuration"></a><span data-ttu-id="419b4-104">設定您的 XR 設定</span><span class="sxs-lookup"><span data-stu-id="419b4-104">Setting up your XR configuration</span></span>

<span data-ttu-id="419b4-105">當您啟動新的 Unity 專案時，您有三個不同的選項可處理您的 XR 需求：</span><span class="sxs-lookup"><span data-stu-id="419b4-105">When you start a new Unity project, you have three different options for handling your XR needs:</span></span> 
* <span data-ttu-id="419b4-106">OpenXR 外掛程式</span><span class="sxs-lookup"><span data-stu-id="419b4-106">OpenXR plugin</span></span>
* <span data-ttu-id="419b4-107">Windows XR 外掛程式</span><span class="sxs-lookup"><span data-stu-id="419b4-107">Windows XR plugin</span></span>
* <span data-ttu-id="419b4-108">舊版 XR 外掛程式</span><span class="sxs-lookup"><span data-stu-id="419b4-108">Legacy XR plugin</span></span>

[!INCLUDE[](includes/xr/intro.md)]

## <a name="setting-up-your-project-with-mrtk"></a><span data-ttu-id="419b4-109">使用 MRTK 設定您的專案</span><span class="sxs-lookup"><span data-stu-id="419b4-109">Setting up your project with MRTK</span></span>

<span data-ttu-id="419b4-110">適用于 Unity 的 MRTK 會提供跨平臺輸入系統、基礎元件，以及空間互動的常見組建區塊。</span><span class="sxs-lookup"><span data-stu-id="419b4-110">MRTK for Unity provides a cross-platform input system, foundational components, and common building blocks for spatial interactions.</span></span> <span data-ttu-id="419b4-111">MRTK 第 2 版主要用於加速開發適用於 Microsoft HoloLens、Windows Mixed Reality 沈浸式 (VR) 頭戴裝置和 OpenVR 平台的應用程式。</span><span class="sxs-lookup"><span data-stu-id="419b4-111">MRTK version 2 intends to speed up application development for Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets, and OpenVR platform.</span></span> <span data-ttu-id="419b4-112">此專案的目標是減少進入障礙、建立混合實境應用程式，以及回饋伴著我們成長的社群。</span><span class="sxs-lookup"><span data-stu-id="419b4-112">The project is aimed at reducing barriers to entry, creating mixed reality applications, and contributing back to the community as we all grow.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="419b4-113">試用我們的 MRTK 教學課程</span><span class="sxs-lookup"><span data-stu-id="419b4-113">Try out our MRTK tutorials</span></span>](./tutorials/mr-learning-base-02.md?tabs=winxr)

<span data-ttu-id="419b4-114">如需詳細的功能詳細資料，請參閱 [MRTK 的檔](/windows/mixed-reality/mrtk-unity) 。</span><span class="sxs-lookup"><span data-stu-id="419b4-114">Take a look at [MRTK's documentation](/windows/mixed-reality/mrtk-unity) for more feature details.</span></span>

### <a name="using-mrtk-with-openxr-support"></a><span data-ttu-id="419b4-115">搭配使用 MRTK 與 OpenXR 支援</span><span class="sxs-lookup"><span data-stu-id="419b4-115">Using MRTK with OpenXR support</span></span>

<span data-ttu-id="419b4-116">MRTK-Unity 2.7 版可針對 Mixed Reality OpenXR 外掛程式提供更佳的支援。</span><span class="sxs-lookup"><span data-stu-id="419b4-116">MRTK-Unity 2.7 release provides better supports for the Mixed Reality OpenXR plugin.</span></span>

<span data-ttu-id="419b4-117">如果您還沒有這麼做，請再次開啟 [Mixed Reality 功能工具](welcome-to-mr-feature-tool.md) 以安裝混合現實工具組。</span><span class="sxs-lookup"><span data-stu-id="419b4-117">Open the [Mixed Reality Feature Tool](welcome-to-mr-feature-tool.md) again to install the Mixed Reality Toolkit, if you haven't already.</span></span> <span data-ttu-id="419b4-118">**基礎** 套件中的 OpenXR 支援。</span><span class="sxs-lookup"><span data-stu-id="419b4-118">OpenXR support is in the **Foundation** package.</span></span>

<span data-ttu-id="419b4-119">如需有關 [遷移至 OpenXR 的深入資訊](/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk#configuring-mrtk-for-the-xr-sdk-pipeline)，請參閱 MRTK 檔。</span><span class="sxs-lookup"><span data-stu-id="419b4-119">See the MRTK documentation for [more in-depth information on migrating to OpenXR](/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk#configuring-mrtk-for-the-xr-sdk-pipeline).</span></span>

> [!NOTE]
> <span data-ttu-id="419b4-120">從早于 **2.5.3** 的舊版 MRTK 進行升級時，請確定 [資產/MixedRealityToolkit] 中的下列程式程式碼位於 [ **資產/] 中。產生/link.xml** 檔案：</span><span class="sxs-lookup"><span data-stu-id="419b4-120">When upgrading from a previous version of MRTK older than **2.5.3**, ensure the following line is in the **Assets/MixedRealityToolkit.Generated/link.xml** file:</span></span>
>
> ```xml
> <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>
> ```
>
> <span data-ttu-id="419b4-121">如果您開始使用 MRTK 2.5.4 或更新版本，則預設會新增這一行。</span><span class="sxs-lookup"><span data-stu-id="419b4-121">This line will be added by default if you started with MRTK 2.5.4 or newer.</span></span>

## <a name="manual-setup-without-mrtk"></a><span data-ttu-id="419b4-122">手動設定而不 MRTK</span><span class="sxs-lookup"><span data-stu-id="419b4-122">Manual setup without MRTK</span></span>

<span data-ttu-id="419b4-123">雖然 Microsoft 和社區建立了開放原始碼工具，例如 [混合現實工具組 (MRTK) ](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html) ，而這些工具會自動設定 WMR 的環境，但許多開發人員想要從頭開始建立他們的體驗。</span><span class="sxs-lookup"><span data-stu-id="419b4-123">While Microsoft and the community have created opensource tools such as the [Mixed Reality Toolkit (MRTK)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html) that will automatically set up the WMR environment, many developers wish to build their experiences from the ground up.</span></span>

[!INCLUDE[](includes/xr/manual-setup.md)]