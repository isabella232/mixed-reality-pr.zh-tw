---
title: MRTKNuGetPakages
description: MRTK 中的 NuGet 套件。
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: f4f4ceb48b9987f6a964879e95a75f8db58c145f
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/03/2021
ms.locfileid: "101780716"
---
# <a name="mixed-reality-toolkit-nuget-package"></a>混合現實工具組 NuGet 套件

混合現實工具組 (MRTK) 現已在 NuGet.org 上以 NuGet 套件的形式提供。使用 NuGet 版本的 MRTK 而不是 unitypackage 時，有一些差異，請參閱下面的 [Nuget 套件考慮](#nuget-package-considerations) 。 如果遇到任何問題，請使用此 [範本](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/new?assignees=&labels=Bug,Package%20Management%20-%20NuGet&template=bug-report.md&title=)提出問題。

> [!NOTE]
> 尚不支援將現有專案遷移至使用 MRTK 作為 NuGet 套件。 僅針對新的專案使用 MRTK via NuGet。

## <a name="installing-the-nuget-package"></a>安裝 NuGet 封裝

遵循這些指示，將混合現實工具組新增為您專案的 NuGet 套件。

1. 下載最新的 [NuGetForUnity](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest) . unitypackage。
    1. 如果已安裝 *NuGetForUnity* ，請確定其版本為 **2.0.0 或更新** 版本。
1. 將封裝匯入 Unity 專案中， [指示](https://docs.unity3d.com/Manual/AssetPackages.html)。
1. 在 Unity 功能表列中，按一下 [ **nuget**  >  **管理 nuget 封裝**]。

    ![Manage NuGet Packages](../Images/NuGet/ManageNuGetPackages.png)
1. 在搜尋方塊中，輸入 **MixedReality 工具** 組。

    ![Manage NuGet Packages](../Images/NuGet/SearchBox.png)
1. 選擇 MRTK core 套件：
    - **MixedReality** – MRTK 的核心套件。
1.  (選擇性的) 選擇 MRTK 選用套件。
    - **MixedReality-範例** -包含所有範例的封裝。
    - **MixedReality** ：包含擴充服務和（或）資料提供者的封裝。
    - **MixedReality** ：包含一些 MRTK (組建視窗等等的工具，也就是) 。

### <a name="updating-mrtk-nuget-packages"></a>更新 MRTK NuGet 套件

上述步驟1-2 只需要針對專案執行一次，而更新是更簡單的步驟。 一旦 NuGet.org 上有較新的套件可用 (（包括發行前版本) ），請遵循下列步驟：

1. 在 Unity 功能表列中，按一下 [ **nuget**  >  **管理 nuget 套件**]
1. 切換至 [ **更新** ] 索引標籤。
    - 如果您想要取得最新的發行前版本，請勾選 [ **顯示發行** 前版本] 方塊。
1. 更新所需的套件。

## <a name="nuget-package-considerations"></a>NuGet 套件考慮

以 NuGet 套件的形式發行 MRTK 是一種新的傳遞機制，而且在選擇是否要使用 NuGet 版本的 MRTK 時，有幾個重要的優點和考慮需要進行。

### <a name="migrating-to-nuget-from-unitypackage-or-source-not-yet-supported"></a>尚未支援從 unitypackage 或來源遷移至 NuGet () 

NuGet 封裝包含編譯過的二進位檔，而不是鬆散的腳本檔案，而且 c # 腳本資產識別碼不同。 因此，MRTK 套件中的 prefabs 等資產已更新為參考適當的已編譯腳本。 使用 unitypackage 或 MRTK 來源版本的專案也必須重新設定其資產的目標，雖然有程式碼，但這並不是支援的案例。

> [!IMPORTANT]
> 目前不支援從 unitypackage 或來源遷移至 NuGet 的方式。 當我們繼續開發此傳遞機制時，這將會改變。

### <a name="compiled-binaries-nuget-vs-source-files-unitypackage"></a>已編譯的二進位檔 (NuGet) 與來源檔案 (. unitypackage) 

由於 NuGet 套件包含已編譯的二進位檔，而不是腳本，因此有兩個主要優點：

- 縮短編譯時間
- Visual Studio 中的 c # 專案檔大幅減少

### <a name="debugging-mixed-reality-toolkit"></a>調試混合現實工具組

Unity & Visual Studio Tools for Unity 有已知的問題，可防止在 Visual Studio 偵錯工具中輕鬆地進行 PDB 的偵錯工具。 因此，雖然封裝隨附 Pdb 和來源內嵌，但如果 Dll 是在本機建立的 (讀取) ，就可能會進行偵錯工具的偵錯工具。 有一項因應措施是建立為 [MSBuildForUnity](https://github.com/microsoft/MSBuildForUnity/)的一部分，稍後會有更多更新。

## <a name="locally-building-the-nuget-package"></a>在本機建立 NuGet 套件

使用 MRTK 的最新來源，您可以在本機建立 NuGet 套件，並設定 NuGetForUnity 來挑選它。

1. 下載最新的 MRTK 來源。
1. 執行 `scripts\packaging\createnugetpackages.ps1` powershell 腳本。
    - 藉 `-UnityDirectory` 由傳遞 Unity 安裝的編輯器資料夾來指定旗標
    - 以 `-Version` x.x 格式指定要建立之封裝的。 **請確定版本高於 NuGet.org 的可用版本**
    - **範例：** `.\createnugetpackages.ps1 -UnityDirectory "C:\Program Files\Unity\Hub\Editor\2018.4.14f1\Editor" -Version 2.3.2`
1. 組建成功之後，請使用 NuGet 套件開啟目的地專案。
    - 按一下功能表 **編輯**  >  **喜好** 設定 .。。

        ![編輯喜好設定功能表項目](../Images/NuGet/ProjectPreferences.png)
    - 在左側尋找 [ **適用于 Unity 的 NuGet** ] 索引標籤。

        ![編輯喜好設定功能表項目](../Images/NuGet/NuGetForUnityPreferencesTab.png)
    - 按下 [ **新增來源** ]，並將 **source_path** 取代為 `<Path to your Repository>\NuGet\artifacts`

        ![編輯喜好設定功能表項目](../Images/NuGet/AddNewSource.png)
    - 按一下底部的 [ **儲存** ] 按鈕。

        ![編輯喜好設定功能表項目](../Images/NuGet/SaveNewSource.png)
1. 如果這是您第一次建立或版本已遞增，請遵循更新程式：
    1. 在 Unity 功能表列中，按一下 [ **nuget**  >  **管理 nuget 封裝**]。

        ![Manage NuGet Packages](../Images/NuGet/ManageNuGetPackages.png)
    1. 切換至 [ **更新** ] 索引標籤。

        ![Manage NuGet Packages](../Images/NuGet/UpdatesTab.png)
    1. 將套件更新為您剛剛所建立的版本。
1. 否則，只需刪除 `Assets\Packages` 資料夾並讓 NuGetForUnity 還原封裝即可。

## <a name="see-also"></a>另請參閱

- [建立和部署 MRTK](../../updates-deployment/BuildAndDeploy.md)
- [MRTK 套件內容](MRTK_PackageContents.md)
