---
title: usingupm
description: 在 Unity pakage 管理員中使用 MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK 套件、
ms.openlocfilehash: ac7a0cbb994cfc66aaf296620bffc2514aaa77d4
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104688678"
---
# <a name="mixed-reality-toolkit-and-unity-package-manager"></a>混合現實工具組和 Unity 封裝管理員

從版本2.5.0 開始，您可以在 Unity 2019.4 和更新版本上使用 Unity 封裝管理員 (UPM) 提供 Microsoft Mixed Reality 工具組。

## <a name="installing-mixed-reality-features-using-the-unity-package-manager"></a>使用 Unity 封裝管理員安裝混合現實功能

Unity 封裝管理員使用) 上 (manifest.js的 [資訊清單](https://docs.unity3d.com/Manual/upm-manifestPkg.html) 檔案來判斷要安裝的套件，以及可從中安裝的登錄 (伺服器) 。

> [!Note]
> 自 MRTK 版開始，伺服器和套件的初始註冊是每個專案的手動程式，請閱讀下列各節以取得詳細指示。
>
> 因為 UPM 使用舊版 npm 搜尋功能 (/-/all) 不受 Azure DevOps 支援，所以需要此程式。

### <a name="registering-the-mixed-reality-component-server"></a>註冊混合現實元件伺服器

針對將使用 Microsoft Mixed Reality 工具組的每個專案，[ `manifest.json` 套件] 資料夾中的檔案 () 必須新增混合的現實範圍登錄。 以下說明如何適當地修改 `manifest.json` 以支援 Mixed 事實。

1. `<projectRoot>/Packages/manifest.json`在文字編輯器中開啟，例如[Visual Studio Code](https://code.visualstudio.com/)。
1. 在資訊清單檔案的頂端，將 Mixed Reality 伺服器新增至範圍登錄區段，並儲存檔案。

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

### <a name="adding-mrtk-packages"></a>新增 MRTK 套件

一旦將 Microsoft Mixed Reality 範圍登錄新增至資訊清單之後，就可以指定 MRTK 封裝。

[混合現實工具](../packages-releases/MRTK_Packages.md)組套件文章的[Unity 封裝管理員](../packages-releases/MRTK_Packages.md#unity-package-manager)一節說明可用的 MRTK 套件、其內容，以及其使用案例。

若要加入 MRTK 封裝，請修改檔案的 [相依性] 區段 `Packages/manifest.json` 。 下列範例說明如何新增基礎、工具和範例套件，標準資產套件將會自動新增為基礎的相依性。

```
  "dependencies": {
    "com.microsoft.mixedreality.toolkit.foundation": "2.5.1",
    "com.microsoft.mixedreality.toolkit.tools": "2.5.1",
    "com.microsoft.mixedreality.toolkit.examples": "2.5.1",
```

> [!IMPORTANT]
> 有一個已知的編譯器問題，會影響使用 ARM64 針對 Microsoft HoloLens 2 所建立的應用程式。 Visual Studio 2019 即將推出的16.8 更新會解決此問題。 在更新可用之前，請匯入套件以套用因應措施 `com.microsoft.mixedreality.toolkit.tools` 。

## <a name="managing-mixed-reality-features-with-the-unity-package-manager"></a>利用 Unity 封裝管理員管理混合的現實功能

一旦將混合現實工具組套件新增至套件資訊清單之後，就可以使用 Unity 封裝管理員使用者介面進行管理。

![MRTK Foundation UPM 套件](../features/images/packaging/MRTK_FoundationUPM.png)

> [!Note]
> 如果使用 Unity 封裝管理員移除混合現實工具組套件，就必須使用 [先前所述的步驟](#adding-mrtk-packages)重新新增。

### <a name="using-mixed-reality-toolkit-examples"></a>使用混合現實工具組範例

不同于使用資產套件 ( unitypackage) 檔案， `com.microsoft.mixedreality.toolkit.examples` 而且 `com.microsoft.mixedreality.toolkit.handphysicsservice` 不會自動匯入範例場景和資產。

若要利用一或多個範例，請使用下列步驟：

1. 在 Unity 編輯器中，流覽至 `Window` > `Package Manager`
1. 在套件清單中，選取 `Mixed Reality Toolkit Examples`
1. 在清單中找出所需的範例 (s) `Samples`
1. 按一下 `Import into Project`

![匯入範例](../features/images/packaging/MRTK_ExamplesUpm.png)

更新範例套件時，Unity 會提供選項來更新匯入的範例。

> [!Note]
> 更新匯入的範例將會覆寫對該範例所做的任何變更，以及相關聯的資產。

## <a name="see-also"></a>另請參閱

- [混合現實工具組套件](../packages-releases/MRTK_Packages.md)
