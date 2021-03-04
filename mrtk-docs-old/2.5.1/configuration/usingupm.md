---
title: usingupm
description: 在 Unity pakage 管理員中使用 MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK 套件、
ms.openlocfilehash: e7089df1b1cf61e82ea076d46a27637a3cffdc58
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/03/2021
ms.locfileid: "101779781"
---
# <a name="mixed-reality-toolkit-and-unity-package-manager"></a><span data-ttu-id="127ae-104">混合現實工具組和 Unity 套件管理員</span><span class="sxs-lookup"><span data-stu-id="127ae-104">Mixed Reality Toolkit and Unity Package Manager</span></span>

<span data-ttu-id="127ae-105">從版本2.5.0 開始，您可以在 Unity 2019.4 和更新版本上使用 Unity 套件管理員 (UPM) 來使用 Microsoft Mixed Reality 工具組。</span><span class="sxs-lookup"><span data-stu-id="127ae-105">Starting with version 2.5.0, the Microsoft Mixed Reality Toolkit is available using the Unity Package Manager (UPM), on Unity 2019.4 and newer.</span></span>

## <a name="installing-mixed-reality-features-using-the-unity-package-manager"></a><span data-ttu-id="127ae-106">使用 Unity 套件管理員安裝混合現實功能</span><span class="sxs-lookup"><span data-stu-id="127ae-106">Installing Mixed Reality features using the Unity Package Manager</span></span>

<span data-ttu-id="127ae-107">Unity 套件管理員會使用 (manifest.js于) 的 [資訊清單](https://docs.unity3d.com/Manual/upm-manifestPkg.html) 檔來決定要安裝的套件，以及可從中安裝的登錄 (伺服器) 。</span><span class="sxs-lookup"><span data-stu-id="127ae-107">The Unity Package Manager uses a [manifest file](https://docs.unity3d.com/Manual/upm-manifestPkg.html) (manifest.json) to determine which packages to install and the registries (servers) from which they can be installed.</span></span>

> [!Note]
> <span data-ttu-id="127ae-108">自 MRTK 版開始，伺服器和套件的初始註冊是每個專案的手動程式，請閱讀下列各節以取得詳細指示。</span><span class="sxs-lookup"><span data-stu-id="127ae-108">As of version 2.5.1 of the MRTK, initial registration of the server and packages is a per-project, manual procedure, please read the following sections for detailed instructions.</span></span>
>
> <span data-ttu-id="127ae-109">此程式是必要的，因為 UPM 使用舊版 npm 搜尋功能 (/-/all) 不受 Azure DevOps 支援。</span><span class="sxs-lookup"><span data-stu-id="127ae-109">This process is required due to UPM's use of legacy npm search functionality (/-/all) that is not supported by Azure DevOps.</span></span>

### <a name="registering-the-mixed-reality-component-server"></a><span data-ttu-id="127ae-110">註冊混合現實元件伺服器</span><span class="sxs-lookup"><span data-stu-id="127ae-110">Registering the Mixed Reality component server</span></span>

<span data-ttu-id="127ae-111">針對將使用 Microsoft Mixed Reality 工具組的每個專案，[ `manifest.json` 套件] 資料夾中的檔案 () 必須新增混合的現實範圍登錄。</span><span class="sxs-lookup"><span data-stu-id="127ae-111">For each project that will be using the Microsoft Mixed Reality Toolkit, the `manifest.json` file (in the Packages folder) will need to have the Mixed Reality scoped registry added.</span></span> <span data-ttu-id="127ae-112">以下說明如何適當地修改 `manifest.json` 以支援 Mixed 事實。</span><span class="sxs-lookup"><span data-stu-id="127ae-112">The following illustrate how to properly modify `manifest.json` to support Mixed Reality.</span></span>

1. <span data-ttu-id="127ae-113">`<projectRoot>/Packages/manifest.json`在文字編輯器（例如[Visual Studio Code](https://code.visualstudio.com/)）中開啟。</span><span class="sxs-lookup"><span data-stu-id="127ae-113">Open `<projectRoot>/Packages/manifest.json` in a text editor, such as [Visual Studio Code](https://code.visualstudio.com/).</span></span>
1. <span data-ttu-id="127ae-114">在資訊清單檔案的頂端，將 Mixed Reality 伺服器新增至範圍登錄區段，並儲存檔案。</span><span class="sxs-lookup"><span data-stu-id="127ae-114">At the top of the manifest file, add the Mixed Reality server to the scoped registry section and save the file.</span></span>

```
{
  "scopedRegistries": [
    {
      "name": "Microsoft Mixed Reality",
      "url": "https://pkgs.dev.azure.com/aipmr/MixedReality-Unity-Packages/_packaging/Unity-packages/npm/registry/",
      "scopes": [
        "com.microsoft.mixedreality",
        "com.microsoft.spatialaudio"
      ]
    }
  ],
```

### <a name="adding-mrtk-packages"></a><span data-ttu-id="127ae-115">新增 MRTK 套件</span><span class="sxs-lookup"><span data-stu-id="127ae-115">Adding MRTK packages</span></span>

<span data-ttu-id="127ae-116">一旦將 Microsoft Mixed Reality 範圍登錄新增至資訊清單之後，就可以指定 MRTK 封裝。</span><span class="sxs-lookup"><span data-stu-id="127ae-116">Once the Microsoft Mixed Reality scoped registry has been added to the manifest, the MRTK packages can be specified.</span></span>

<span data-ttu-id="127ae-117">[混合現實工具](../packages-releases/MRTK_Packages.md)組套件文章的[Unity 套件管理員](../packages-releases/MRTK_Packages.md#unity-package-manager)區段說明可用的 MRTK 套件、其內容以及其使用案例。</span><span class="sxs-lookup"><span data-stu-id="127ae-117">The [Unity Package Manager](../packages-releases/MRTK_Packages.md#unity-package-manager) section of the [Mixed Reality Toolkit package](../packages-releases/MRTK_Packages.md) article describes the available MRTK packages, their contents and the scenarios for their use.</span></span>

<span data-ttu-id="127ae-118">若要加入 MRTK 封裝，請修改檔案的 [相依性] 區段 `Packages/manifest.json` 。</span><span class="sxs-lookup"><span data-stu-id="127ae-118">To add an MRTK package, modify the dependencies section of the `Packages/manifest.json` file.</span></span> <span data-ttu-id="127ae-119">下列範例說明如何新增基礎、工具和範例套件，標準資產套件將會自動新增為基礎的相依性。</span><span class="sxs-lookup"><span data-stu-id="127ae-119">The following example illustrates adding the foundation, tools and examples packages, the standard assets package will be added automatically as a dependency of the foundation.</span></span>

```
  "dependencies": {
    "com.microsoft.mixedreality.toolkit.foundation": "2.5.1",
    "com.microsoft.mixedreality.toolkit.tools": "2.5.1",
    "com.microsoft.mixedreality.toolkit.examples": "2.5.1",
```

> [!IMPORTANT]
> <span data-ttu-id="127ae-120">有一個已知的編譯器問題，會影響使用 ARM64 針對 Microsoft HoloLens 2 所建立的應用程式。</span><span class="sxs-lookup"><span data-stu-id="127ae-120">There is a known compiler issue that impacts applications built for Microsoft HoloLens 2 using ARM64.</span></span> <span data-ttu-id="127ae-121">Visual Studio 2019 即將推出的16.8 更新會解決此問題。</span><span class="sxs-lookup"><span data-stu-id="127ae-121">This issue is addressed in the forthcoming 16.8 update for Visual Studio 2019.</span></span> <span data-ttu-id="127ae-122">在更新可用之前，請匯入套件以套用因應措施 `com.microsoft.mixedreality.toolkit.tools` 。</span><span class="sxs-lookup"><span data-stu-id="127ae-122">Until the update is available, please import the `com.microsoft.mixedreality.toolkit.tools` package to apply a workaround.</span></span>

## <a name="managing-mixed-reality-features-with-the-unity-package-manager"></a><span data-ttu-id="127ae-123">使用 Unity 套件管理員管理混合的現實功能</span><span class="sxs-lookup"><span data-stu-id="127ae-123">Managing Mixed Reality features with the Unity Package Manager</span></span>

<span data-ttu-id="127ae-124">一旦將混合現實工具組套件新增至套件資訊清單之後，就可以使用 Unity 套件管理員使用者介面進行管理。</span><span class="sxs-lookup"><span data-stu-id="127ae-124">Once a Mixed Reality Toolkit package has been added to the package manifest, it can be managed using the Unity Package Manager user interface.</span></span>

![MRTK Foundation UPM 套件](../features/images/packaging/MRTK_FoundationUPM.png)

> [!Note]
> <span data-ttu-id="127ae-126">如果使用 Unity 套件管理員移除混合現實工具組套件，就必須使用 [先前所述的步驟](#adding-mrtk-packages)重新新增。</span><span class="sxs-lookup"><span data-stu-id="127ae-126">If a Mixed Reality Toolkit package is removed using the Unity Package Manager, it will have to be re-added using the [previously described steps](#adding-mrtk-packages).</span></span>

### <a name="using-mixed-reality-toolkit-examples"></a><span data-ttu-id="127ae-127">使用混合現實工具組範例</span><span class="sxs-lookup"><span data-stu-id="127ae-127">Using Mixed Reality Toolkit examples</span></span>

<span data-ttu-id="127ae-128">不同于使用資產套件 ( unitypackage) 檔案， `com.microsoft.mixedreality.toolkit.examples` 而且 `com.microsoft.mixedreality.toolkit.handphysicsservice` 不會自動匯入範例場景和資產。</span><span class="sxs-lookup"><span data-stu-id="127ae-128">Unlike when using asset package (.unitypackage) files, `com.microsoft.mixedreality.toolkit.examples` and `com.microsoft.mixedreality.toolkit.handphysicsservice` do not automatically import the example scenes and assets.</span></span>

<span data-ttu-id="127ae-129">若要利用一或多個範例，請使用下列步驟：</span><span class="sxs-lookup"><span data-stu-id="127ae-129">To utilize one or more of the examples, please use the following steps:</span></span>

1. <span data-ttu-id="127ae-130">在 Unity 編輯器中，流覽至 `Window` > `Package Manager`</span><span class="sxs-lookup"><span data-stu-id="127ae-130">In the Unity Editor, navigate to `Window` > `Package Manager`</span></span>
1. <span data-ttu-id="127ae-131">在套件清單中，選取 `Mixed Reality Toolkit Examples`</span><span class="sxs-lookup"><span data-stu-id="127ae-131">In the list of packages, select `Mixed Reality Toolkit Examples`</span></span>
1. <span data-ttu-id="127ae-132">在清單中找出所需的範例 (s) `Samples`</span><span class="sxs-lookup"><span data-stu-id="127ae-132">Locate the desired sample(s) in the `Samples` list</span></span>
1. <span data-ttu-id="127ae-133">按一下 `Import into Project`</span><span class="sxs-lookup"><span data-stu-id="127ae-133">Click `Import into Project`</span></span>

![匯入範例](../features/images/packaging/MRTK_ExamplesUpm.png)

<span data-ttu-id="127ae-135">更新範例套件時，Unity 會提供選項來更新匯入的範例。</span><span class="sxs-lookup"><span data-stu-id="127ae-135">When an example package is updated, Unity provides the option to update imported samples.</span></span>

> [!Note]
> <span data-ttu-id="127ae-136">更新匯入的範例將會覆寫對該範例所做的任何變更，以及相關聯的資產。</span><span class="sxs-lookup"><span data-stu-id="127ae-136">Updating an imported sample will overwrite any changes that have been made to that sample and the associated assets.</span></span>

## <a name="see-also"></a><span data-ttu-id="127ae-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="127ae-137">See Also</span></span>

- [<span data-ttu-id="127ae-138">混合現實工具組套件</span><span class="sxs-lookup"><span data-stu-id="127ae-138">Mixed Reality Toolkit packages</span></span>](../packages-releases/MRTK_Packages.md)
