---
title: ReleaseNotes
description: 目前 MRTK 版本的發行 nots
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: 850605855ff756939c334bf8116022a1340aa9f6
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/03/2021
ms.locfileid: "101781087"
---
# <a name="microsoft-mixed-reality-toolkit-release-notes"></a>Microsoft Mixed Reality 工具組版本資訊

- [新功能](#whats-new-in-240)
- [重大變更](#breaking-changes-in-240)
- [更新指導方針](upgrading.md#upgrading-to-a-new-version-of-mrtk)
- [已知問題](#known-issues-in-240)

這一版的 Microsoft Mixed Reality 工具組支援下列裝置和平臺。

- Microsoft HoloLens 2
- Microsoft HoloLens (第1代) 
- Windows Mixed Reality 沉浸式耳機
- OpenVR
-  (實驗性) Unity 2019.3 XR 平臺
- 透過 Unity AR Foundation 的 Mobile AR
  - Android
  - iOS
- Ultraleap 手部追蹤

需要下列軟體。

- [Microsoft Visual Studio](https://visualstudio.microsoft.com) (2017 或 2019) 3.x 版或更高版本
- Visual Studio 安裝程式安裝的[Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) 18362 或更新版本 () 
- [Unity](https://unity3d.com/get-unity/download) 2018.4 LTS 或 2019 (2019.3 建議的) 

**下載**

[MixedReality. 2.4.0. unitypackage](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.4.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.4.0.unitypackage) 
 。[MixedReality. 2.4.0. unitypackage](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.4.0/Microsoft.MixedReality.Toolkit.Unity.Extensions.2.4.0.unitypackage) 
 。[MixedReality. 2.4.0. unitypackage](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.4.0/Microsoft.MixedReality.Toolkit.Unity.Examples.2.4.0.unitypackage) 
 。[MixedReality. 2.4.0. unitypackage](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.4.0/Microsoft.MixedReality.Toolkit.Unity.Tools.2.4.0.unitypackage) 。

您可以在[GitHub 版本頁面](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/tag/v2.4.0)找到其他檔案

**NuGet 需求**

如果匯入 [混合現實工具組 NuGet 套件](../reference-docs/MRTKNuGetPackage.md)，建議使用下列軟體。

- [適用于 Unity 2.0.0 或更新版本的 NuGet](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest)

### <a name="whats-new-in-240"></a>2.4.0 的新功能

**Ultraleap 手追蹤支援**

[閏運動資料提供者](../features/CrossPlatform/LeapMotionMRTK.md)可讓您針對 VR 應用程式進行明確的追蹤，也適用于在編輯器中快速建立原型。  您可以將資料提供者設定為使用在耳機上掛接的 Leap 運動控制器，或放在桌上的上架。

需要 [Leap 移動控制器](https://www.ultraleap.com/product/leap-motion-controller/) 才能使用此資料提供者。

![LeapMotionIntroGif](../features/Images/CrossPlatform/LeapMotion/LeapMotionSideBySide2.gif)

**遷移視窗**

![遷移視窗](../features/Images/MigrationWindow/MRTK_Migration_Window.png)

MRTK 現在隨附的遷移工具可協助您將已淘汰的元件升級至較新的版本，並讓現有的程式碼即使在 MRTK 進行重大變更時仍能運作。

**通常建議您在提取新版本的 MRTK 之後執行遷移工具** ，以確保您的專案會自動調整至最新的 MRTK 程式碼。

您可以在「混合式現實工具組 > 公用程式 > 遷移視窗」中找到 [ [遷移] 視窗](../features/Tools/MigrationWindow.md) 。 它是 **Tools** 封裝的一部分。

它目前支援：

- 將 ManipulationHandler 和 BoundingBox 升級至較新版本的 ObjectManipulator 和 BoundsControl。
- 更新自訂按鈕圖示，以便在新的按鈕設定協助程式中正確運作。

請注意，BoundsControl 仍在實驗階段中，因此在下一個版本中，API 或屬性可能仍會變更。

**MRTK 資料夾版面配置變更**

此版本的 MRTK 會修改 MRTK 資料夾結構的版面配置。 這項變更會將所有 MRTK 程式碼封裝成單一資料夾階層，並減少所有 MRTK 檔案的路徑總長度。

| 上一個資料夾 | 新增資料夾 |
| --- | --- |
| MixedRealityToolkit | MRTK\Core |
| MixedRealityToolkit 範例 | MRTK\Examples |
| MixedRealityToolkit 副檔名 | MRTK\Extensions |
| MixedRealityToolkit。提供者 | MRTK\Providers |
| MixedRealityToolkit SDK | MRTK\SDK |
| MixedRealityToolkit 服務 | MRTK\Services |
| MixedRealityToolkit。測試 | MRTK\Tests |
| MixedRealityToolkit 工具 | MRTK\Tools |

> [!IMPORTANT]
> `MixedRealityToolkit.Generated`包含客戶產生的檔案，且保持不變。

**MRTK 工具箱**

![MRTK 工具箱](../features/Images/Tools/MRTKToolboxWindow.png)

[MRTK 工具箱](../features/README_Toolbox.md)是 Unity 編輯器視窗公用程式，可讓您輕鬆地探索 MRTK UX 預製專案元件並產生到目前的場景中。 您可以使用視窗頂端的搜尋列，在 view 中篩選項目。 [工具箱] 視窗的設計目的是要將 MRTK 的現成 prefabs 產生到目前的場景中。

**點一下以放置**

點[一下，就是用](../features/README_TapToPlace.md)來輕鬆地將遊戲物件放在表面上的互動元件。 點一下以使用兩個按鍵的組合，並使用前端移動來放置物件。

![TapToPlace](../features/Images/Solver/TapToPlace/TapToPlaceIntroGif.gif)

按鈕設定協助程式 **已新增至 Pressable 按鈕** 
 ![按鈕設定協助程式 ](https://user-images.githubusercontent.com/9789716/70167111-e3175600-167a-11ea-9c52-444509c06105.gif) 這項新功能可讓您輕鬆地變更按鈕的圖示和文字。 圖示支援四、sprite 和 TextMesh Pro 的 .SDF 字型材質。 如需詳細資料，請參閱 MRTK 的 [按鈕檔](../features/README_Button.md#how-to-change-the-icon-and-text) 。

**新的 HoloLens 2 樣式切換按鈕-核取方塊、切換、無線電**
<br/><img src="https://user-images.githubusercontent.com/13754172/75299797-df631d80-57ea-11ea-8857-8ef647df0aca.gif" width="450" alt="Button Config Helper">
<br/><img src="https://user-images.githubusercontent.com/13754172/75299783-d6724c00-57ea-11ea-88b1-85e4a585212f.gif" width="450" alt="Pressabe button">

**功能表的增強功能**

在許多應用程式中，已調整了手中的功能表。 我們發現的最大問題之一，是在操作物件或與其他內容互動等情況下，發生意外的錯誤啟用。已將新的「注視啟用」選項新增至 HandConstraintPalmUp.cs，以防止啟用錯誤。 使用這個選項時，功能表不會不慎顯示，直到使用者查看為止。<br/>
![0416_HandMenu_02](https://user-images.githubusercontent.com/13754172/79507261-4aabbd80-7fec-11ea-95c4-6e3f4bd18c11.gif)

**手動功能表範例更新**

新增大型功能表互動範例1：抓取 & 的提取功能表以進行世界鎖定<br/>
![0416_HandMenu_03](https://user-images.githubusercontent.com/13754172/79507983-90b55100-7fed-11ea-9062-630c892950cb.gif)

新增大型功能表互動範例 2-自動世界-鎖定丟手<br/>
![0416_HandMenu_04](https://user-images.githubusercontent.com/13754172/79508227-f9043280-7fed-11ea-995f-ac3cfe42fe65.gif)

**實驗)  (對話方塊**
<br/><img src="../features/Images/Dialog/MRTK_UX_Dialog_Main.png" width="450" alt="UX Dialog Box">

對話方塊 UI 已使用新的 HoloLens 2 shell 樣式設計更新從 HoloToolkit 移植。

**停駐 (實驗)**
<br/><img src="https://user-images.githubusercontent.com/621574/76669327-65e86080-6548-11ea-85a3-f84f6b367f97.gif" width="450" alt="Dock">

此控制項可讓您將物件移入和移出預定的位置，以建立調色板、貨架和導覽列。

**Unity Profiler 標記**

此版本的 MRTK 已將 Unity Profiler 標記新增至輸入系統和資料提供者。 這些標記提供在 MRTK 輸入系統中花費時間的詳細資訊，可以用來協助優化應用程式。

標記採用 "[MRTK] ClassWithoutNamespace 方法" 的格式。

![Profiler 標記](../features/Images/ReleaseNotes/ProfilerMarkers.png)

**WindowsApiChecker： IsMethodAvailable () 、IsPropertyAvailable () 和 IsTypeAvailable ()**

此版本的 MRTK 會將三個新方法新增至 [`WindowsApiChecker`](xref:Microsoft.MixedReality.Toolkit.Windows.Utilities.WindowsApiChecker) 類別： `IsMethodAvailable` 、 `IsPropertyAvailable` 和 `IsTypeAvailable` 。 這些方法可讓您檢查 Windows 10 上的功能支援，而且偏好使用這些 `UniversalApiContractV#_IsAvailable` 屬性。

**協助程式取得文字輸入欄位，以使用 MixedRealityKeyboard for UnityUI、TextMeshPro (實驗性)**

<img src="https://user-images.githubusercontent.com/168492/77582981-86e07800-6e9d-11ea-86e5-bf2c0840296c.png" width="300" alt="MRTK Keyboard for unity" />

我們引進了兩個協助程式元件， [`UI_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.UI_KeyboardInputField) [`TMP_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.TMP_KeyboardInputField) 可新增至 Unity UI 中的文字輸入欄位，讓 HoloLens 2 和 Windows Mixed Reality 鍵盤在按一下欄位時顯示。

如需詳細資訊，請參閱- [Mixed Reality 鍵盤](../reference-docs/MixedRealityKeyboard/README_MixedRealityKeyboard.md)協助程式。

**方格物件集合對齊選項**

<img src="https://user-images.githubusercontent.com/39840334/79289136-5c228780-7e7d-11ea-82b4-07959e42c3ed.gif" width="300" alt="Alignment Options" />

我們新增了可選擇如何對齊格線中的元素、在執行資料列 then 資料行配置時，是在中央軸或沿著左/右軸對齊的功能 (頂端/底部軸) 

**方格物件集合錨點變更**

<img src="https://user-images.githubusercontent.com/39840334/79516745-17bff480-8001-11ea-8492-cfa953c451da.gif" width="300" alt="Anchor Changes" />

我們變更了格線物件集合行為，使其與 Unity 的版面配置群組行為更趨一致，方法是沿著物件的中央軸對齊錨點。 舊的方格物件集合行為可以使用欄位來切換 `AnchorAlongAxis` 。

**調整輸入模擬攝影機控制項**

使用編輯器內輸入模擬的相機控制速度較慢，以提供更流暢的體驗，而且現在從幀 untied。 快速相機控制項現在以右移的方式啟動，而不是按右 Shift 鍵

**免參與 GGV 輸入模擬**

<img src="https://user-images.githubusercontent.com/39840334/79164615-40908180-7d96-11ea-8195-6be34d4df8d6.gif" width="300" alt="Hands-free GGV input"/>

我們已啟用與物件互動的能力，而不需要在編輯器內輸入模擬服務中攜帶手。 旋轉相機，讓注視游標停留在互動物件上方，然後按一下滑鼠左鍵來與其互動。

**按鈕設定協助程式**

<img src="https://user-images.githubusercontent.com/168492/81211778-bb5d4e80-8f88-11ea-94c7-33cf265586df.png" width="300" alt="Button Config Helper" />

按鈕設定協助程式是一項編輯器功能，可讓您更輕鬆地自訂 MRTK 按鈕。 現在可以更輕鬆地：

- 更新按鈕標籤文字
- 新增按鈕 click 事件接聽程式
- 變更按鈕圖示

**[MRTK 設定] 對話方塊中的音訊空間定位器選取專案**

您現在可以在 [MRTK 設定] 對話方塊中指定音訊空間定位器。 安裝新的 spatializers （例如 [Microsoft 空間定位器](https://www.nuget.org/packages/Microsoft.SpatialAudio.Spatializer.Unity/)）時，將會重新提示允許您輕鬆地選取。

![MRTK 設定 Select 空間定位器](../features/Images/ReleaseNotes/SpatializerSelection.png)

**物件操作工具已分級為 SDK**

![物件操作工具](../features//Images/ManipulationHandler/MRTK_Manipulation_Main.png)

ObjectManipulator 現在已針對 SDK 進行了分級，不再是實驗性功能。 此控制項會取代現在已被取代的現有 ManipulationHandler 類別。 ObjectManipulator 隨附新的更具彈性的條件約束系統，並正確地回應物理。 您可以在物件操作工具 [檔](../features/README_ObjectManipulator.md)中找到完整的功能清單和指南，以瞭解如何進行設定。
使用者可以利用新的 [遷移視窗](../features/Tools/MigrationWindow.md) ，使用 ManipulationHandler 將其現有的 gameobject 升級至 ObjectManipulator

**界限控制項改善**

我們已大幅增加測試涵蓋範圍來控制此版本，並解決了周框方塊使用者的其中一個最大痛點：界限控制項現在不會再重新建立其對設定變更的視覺效果。 此外，它現在支援在執行時間期間重新設定任何屬性。 此外，DrawTetherWhenManipulating 和 HandlesIgnoreCollider 屬性現在可設定為每個控制碼類型。

### <a name="breaking-changes-in-240"></a>2.4.0 中的重大變更

**目視注視 API**

`UseEyeTracking`從執行的屬性 `GazeProvider` 已重新 `IMixedRealityEyeGazeProvider` 命名為 `IsEyeTrackingEnabled` 。

如果您先前已執行此操作 .。。

```csharp
if (CoreServices.InputSystem.GazeProvider is GazeProvider gazeProvider)
{
    gazeProvider.UseEyeTracking = true;
}
```

現在就完成了 .。。

```csharp
if (CoreServices.InputSystem.GazeProvider is GazeProvider gazeProvider)
{
    gazeProvider.IsEyeTrackingEnabled = true;
}
```

**眼睛設定**

此版本的 MRTK 會修改眼睛設定所需的步驟。 您可以在輸入指標設定檔的注視設定中找到 [ _IsEyeTrackingEnabled_ ] 核取方塊。 核取此方塊將會啟用以眼睛為基礎的眼睛，而不是預設的標頭。

如需有關這些變更的詳細資訊，以及適用于眼睛追蹤設定的完整指示，請參閱 [眼睛追蹤](../features/EyeTracking/EyeTracking_BasicSetup.md) 文章。

### <a name="known-issues-in-240"></a>2.4.0 中的已知問題

**Unity 2019.3 中的 [MRTK 配置器] 對話方塊未顯示 [啟用適用于 Unity 的 MSBuild]**

有一個問題，就是在2019.3 中啟用 Unity 的 MSBuild 可能會導致無限迴圈， ([#7239](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/7239)) 的封裝還原。

因應措施是，可以使用 [適用于 Unity 的 NuGet](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest)來匯入 DotNetWinRT 套件。

**重複的元件版本和多個先行編譯的元件 Unity 2018。4**

如果平臺從獨立切換至 UWP，然後回到 Unity 2018.4 中的獨立，則主控台可能會出現下列錯誤：

```
PrecompiledAssemblyException: Multiple precompiled assemblies with the same name Microsoft.Windows.MixedReality.DotNetWinRT.dll included for the current platform. Only one assembly with the same name is allowed per platform. Assembly paths
```

```
Assets\MRTK\Examples\Demos\HandTracking\Scenes\Utilities\InspectorFields\AssemblyInfo.cs(6,12): error CS0579: Duplicate 'AssemblyVersion' attribute
```

這些錯誤是因為 MSBuildForUnity 的刪除程式有問題。  若要解決此問題，在獨立的情況下，請刪除資產根目錄中的 [相依性] 資料夾，然後重新開機 unity。

如需詳細資訊，請參閱 [問題 7948](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/7948)。

**在 Unity 2019.3 上顯示為2D 平板的應用程式**

使用 Unity 2019.3 時，啟用 XR 支援不會將預設 SDK (舊版) 或外掛程式 (XR 管理) 。 這會導致應用程式受限於2D 石板。 有關解決此情況的詳細資訊，請參閱 [ 組建和部署 MRTK 一文](../updates-deployment/BuildAndDeploy.md#unity-20193-and-hololens)。

**Unity 2019.3： ARM 組建架構**

Unity 2019.3 中有一個 [已知問題](https://issuetracker.unity3d.com/issues/enabling-graphics-jobs-in-2019-dot-3-x-results-in-a-crash-or-nothing-rendering-on-hololens-2) ，會在 Visual Studio 中選取 ARM 作為組建架構時發生錯誤。 建議的解決辦法是建立 ARM64。 如果這不是選項，請停用 [**編輯**   >  **專案設定**  >  **播放機**  >  **其他設定**] 中的圖形作業。 如需詳細資訊，請參閱 [建立和部署](../updates-deployment/BuildAndDeploy.md#unity-20193-and-hololens)。

**執行時間設定檔交換**

MRTK 不完全支援在執行時間交換設定檔。 這項功能會在未來的版本中進行調查。 如需詳細資訊，請參閱 [4289](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/4289)、 [5465](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/5465) 和 [5466](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/5466) 問題。

**Unity 2018： .NET 後端和 AR Foundation**

Unity 2018 有問題，在此使用 .NET 腳本後端建立通用 Windows 平臺專案時，Unity AR Foundation 套件將會失敗。

若要解決此問題，請執行下列其中一個步驟：

- 將腳本後端切換至 IL2CPP
- 在 [組建設定] 視窗中，取消核取 [Unity c # 專案]
