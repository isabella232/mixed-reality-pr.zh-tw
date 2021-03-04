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
# <a name="microsoft-mixed-reality-toolkit-release-notes"></a><span data-ttu-id="c57a8-104">Microsoft Mixed Reality 工具組版本資訊</span><span class="sxs-lookup"><span data-stu-id="c57a8-104">Microsoft Mixed Reality Toolkit release notes</span></span>

- [<span data-ttu-id="c57a8-105">新功能</span><span class="sxs-lookup"><span data-stu-id="c57a8-105">What's new</span></span>](#whats-new-in-240)
- [<span data-ttu-id="c57a8-106">重大變更</span><span class="sxs-lookup"><span data-stu-id="c57a8-106">Breaking changes</span></span>](#breaking-changes-in-240)
- [<span data-ttu-id="c57a8-107">更新指導方針</span><span class="sxs-lookup"><span data-stu-id="c57a8-107">Updating guidance</span></span>](upgrading.md#upgrading-to-a-new-version-of-mrtk)
- [<span data-ttu-id="c57a8-108">已知問題</span><span class="sxs-lookup"><span data-stu-id="c57a8-108">Known issues</span></span>](#known-issues-in-240)

<span data-ttu-id="c57a8-109">這一版的 Microsoft Mixed Reality 工具組支援下列裝置和平臺。</span><span class="sxs-lookup"><span data-stu-id="c57a8-109">This release of the Microsoft Mixed Reality Toolkit supports the following devices and platforms.</span></span>

- <span data-ttu-id="c57a8-110">Microsoft HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="c57a8-110">Microsoft HoloLens 2</span></span>
- <span data-ttu-id="c57a8-111">Microsoft HoloLens (第1代) </span><span class="sxs-lookup"><span data-stu-id="c57a8-111">Microsoft HoloLens (1st gen)</span></span>
- <span data-ttu-id="c57a8-112">Windows Mixed Reality 沉浸式耳機</span><span class="sxs-lookup"><span data-stu-id="c57a8-112">Windows Mixed Reality Immersive headsets</span></span>
- <span data-ttu-id="c57a8-113">OpenVR</span><span class="sxs-lookup"><span data-stu-id="c57a8-113">OpenVR</span></span>
- <span data-ttu-id="c57a8-114"> (實驗性) Unity 2019.3 XR 平臺</span><span class="sxs-lookup"><span data-stu-id="c57a8-114">(Experimental) Unity 2019.3 XR platform</span></span>
- <span data-ttu-id="c57a8-115">透過 Unity AR Foundation 的 Mobile AR</span><span class="sxs-lookup"><span data-stu-id="c57a8-115">Mobile AR via Unity AR Foundation</span></span>
  - <span data-ttu-id="c57a8-116">Android</span><span class="sxs-lookup"><span data-stu-id="c57a8-116">Android</span></span>
  - <span data-ttu-id="c57a8-117">iOS</span><span class="sxs-lookup"><span data-stu-id="c57a8-117">iOS</span></span>
- <span data-ttu-id="c57a8-118">Ultraleap 手部追蹤</span><span class="sxs-lookup"><span data-stu-id="c57a8-118">Ultraleap Hand Tracking</span></span>

<span data-ttu-id="c57a8-119">需要下列軟體。</span><span class="sxs-lookup"><span data-stu-id="c57a8-119">The following software is required.</span></span>

- <span data-ttu-id="c57a8-120">[Microsoft Visual Studio](https://visualstudio.microsoft.com) (2017 或 2019) 3.x 版或更高版本</span><span class="sxs-lookup"><span data-stu-id="c57a8-120">[Microsoft Visual Studio](https://visualstudio.microsoft.com) (2017 or 2019) Community Edition or higher</span></span>
- <span data-ttu-id="c57a8-121">Visual Studio 安裝程式安裝的[Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) 18362 或更新版本 () </span><span class="sxs-lookup"><span data-stu-id="c57a8-121">[Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) 18362 or later (installed by the Visual Studio Installer)</span></span>
- <span data-ttu-id="c57a8-122">[Unity](https://unity3d.com/get-unity/download) 2018.4 LTS 或 2019 (2019.3 建議的) </span><span class="sxs-lookup"><span data-stu-id="c57a8-122">[Unity](https://unity3d.com/get-unity/download) 2018.4 LTS or 2019 (2019.3 recommended)</span></span>

<span data-ttu-id="c57a8-123">**下載**</span><span class="sxs-lookup"><span data-stu-id="c57a8-123">**Download**</span></span>

<span data-ttu-id="c57a8-124">[MixedReality. 2.4.0. unitypackage](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.4.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.4.0.unitypackage) 
 。[MixedReality. 2.4.0. unitypackage](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.4.0/Microsoft.MixedReality.Toolkit.Unity.Extensions.2.4.0.unitypackage) 
 。[MixedReality. 2.4.0. unitypackage](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.4.0/Microsoft.MixedReality.Toolkit.Unity.Examples.2.4.0.unitypackage) 
 。[MixedReality. 2.4.0. unitypackage](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.4.0/Microsoft.MixedReality.Toolkit.Unity.Tools.2.4.0.unitypackage) 。</span><span class="sxs-lookup"><span data-stu-id="c57a8-124">[Microsoft.MixedReality.Toolkit.Unity.Foundation.2.4.0.unitypackage](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.4.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.4.0.unitypackage)
[Microsoft.MixedReality.Toolkit.Unity.Extensions.2.4.0.unitypackage](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.4.0/Microsoft.MixedReality.Toolkit.Unity.Extensions.2.4.0.unitypackage)
[Microsoft.MixedReality.Toolkit.Unity.Examples.2.4.0.unitypackage](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.4.0/Microsoft.MixedReality.Toolkit.Unity.Examples.2.4.0.unitypackage)
[Microsoft.MixedReality.Toolkit.Unity.Tools.2.4.0.unitypackage](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.4.0/Microsoft.MixedReality.Toolkit.Unity.Tools.2.4.0.unitypackage)</span></span>

<span data-ttu-id="c57a8-125">您可以在[GitHub 版本頁面](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/tag/v2.4.0)找到其他檔案</span><span class="sxs-lookup"><span data-stu-id="c57a8-125">Other files can be found on the [GitHub release page](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/tag/v2.4.0)</span></span>

<span data-ttu-id="c57a8-126">**NuGet 需求**</span><span class="sxs-lookup"><span data-stu-id="c57a8-126">**NuGet requirements**</span></span>

<span data-ttu-id="c57a8-127">如果匯入 [混合現實工具組 NuGet 套件](../reference-docs/MRTKNuGetPackage.md)，建議使用下列軟體。</span><span class="sxs-lookup"><span data-stu-id="c57a8-127">If importing the [Mixed Reality Toolkit NuGet packages](../reference-docs/MRTKNuGetPackage.md), the following software is recommended.</span></span>

- [<span data-ttu-id="c57a8-128">適用于 Unity 2.0.0 或更新版本的 NuGet</span><span class="sxs-lookup"><span data-stu-id="c57a8-128">NuGet for Unity 2.0.0 or newer</span></span>](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest)

### <a name="whats-new-in-240"></a><span data-ttu-id="c57a8-129">2.4.0 的新功能</span><span class="sxs-lookup"><span data-stu-id="c57a8-129">What's new in 2.4.0</span></span>

<span data-ttu-id="c57a8-130">**Ultraleap 手追蹤支援**</span><span class="sxs-lookup"><span data-stu-id="c57a8-130">**Ultraleap Hand Tracking Support**</span></span>

<span data-ttu-id="c57a8-131">[閏運動資料提供者](../features/CrossPlatform/LeapMotionMRTK.md)可讓您針對 VR 應用程式進行明確的追蹤，也適用于在編輯器中快速建立原型。</span><span class="sxs-lookup"><span data-stu-id="c57a8-131">The [Leap Motion Data Provider](../features/CrossPlatform/LeapMotionMRTK.md) enables articulated hand tracking for VR applications and is also useful for rapid prototyping in the editor.</span></span>  <span data-ttu-id="c57a8-132">您可以將資料提供者設定為使用在耳機上掛接的 Leap 運動控制器，或放在桌上的上架。</span><span class="sxs-lookup"><span data-stu-id="c57a8-132">The data provider can be configured to use the Leap Motion Controller mounted on a headset or placed on a desk face up.</span></span>

<span data-ttu-id="c57a8-133">需要 [Leap 移動控制器](https://www.ultraleap.com/product/leap-motion-controller/) 才能使用此資料提供者。</span><span class="sxs-lookup"><span data-stu-id="c57a8-133">A [Leap Motion Controller](https://www.ultraleap.com/product/leap-motion-controller/) is required to use this data provider.</span></span>

![LeapMotionIntroGif](../features/Images/CrossPlatform/LeapMotion/LeapMotionSideBySide2.gif)

<span data-ttu-id="c57a8-135">**遷移視窗**</span><span class="sxs-lookup"><span data-stu-id="c57a8-135">**Migration window**</span></span>

![遷移視窗](../features/Images/MigrationWindow/MRTK_Migration_Window.png)

<span data-ttu-id="c57a8-137">MRTK 現在隨附的遷移工具可協助您將已淘汰的元件升級至較新的版本，並讓現有的程式碼即使在 MRTK 進行重大變更時仍能運作。</span><span class="sxs-lookup"><span data-stu-id="c57a8-137">MRTK now comes with a migration tool that will help you upgrade deprecated components to their newer versions and to keep existing code working even as MRTK makes breaking changes.</span></span>

<span data-ttu-id="c57a8-138">**通常建議您在提取新版本的 MRTK 之後執行遷移工具** ，以確保您的專案會自動調整至最新的 MRTK 程式碼。</span><span class="sxs-lookup"><span data-stu-id="c57a8-138">**It is generally recommended to run the migration tool after pulling a new version of MRTK** to ensure that as much of your project will be auto-adjusted to the latest MRTK code.</span></span>

<span data-ttu-id="c57a8-139">您可以在「混合式現實工具組 > 公用程式 > 遷移視窗」中找到 [ [遷移] 視窗](../features/Tools/MigrationWindow.md) 。</span><span class="sxs-lookup"><span data-stu-id="c57a8-139">The [migration window](../features/Tools/MigrationWindow.md) can be found in 'Mixed Reality Toolkit > Utilities > Migration Window'.</span></span> <span data-ttu-id="c57a8-140">它是 **Tools** 封裝的一部分。</span><span class="sxs-lookup"><span data-stu-id="c57a8-140">It it part of the **Tools** package.</span></span>

<span data-ttu-id="c57a8-141">它目前支援：</span><span class="sxs-lookup"><span data-stu-id="c57a8-141">It currently supports:</span></span>

- <span data-ttu-id="c57a8-142">將 ManipulationHandler 和 BoundingBox 升級至較新版本的 ObjectManipulator 和 BoundsControl。</span><span class="sxs-lookup"><span data-stu-id="c57a8-142">Upgrading ManipulationHandler and BoundingBox to their newer versions ObjectManipulator and BoundsControl.</span></span>
- <span data-ttu-id="c57a8-143">更新自訂按鈕圖示，以便在新的按鈕設定協助程式中正確運作。</span><span class="sxs-lookup"><span data-stu-id="c57a8-143">Updating custom button icons to work correctly with the new Button Config Helper.</span></span>

<span data-ttu-id="c57a8-144">請注意，BoundsControl 仍在實驗階段中，因此在下一個版本中，API 或屬性可能仍會變更。</span><span class="sxs-lookup"><span data-stu-id="c57a8-144">Note that BoundsControl is still in experimental phase and therefore API or properties might still change in the next version.</span></span>

<span data-ttu-id="c57a8-145">**MRTK 資料夾版面配置變更**</span><span class="sxs-lookup"><span data-stu-id="c57a8-145">**MRTK folder layout changes**</span></span>

<span data-ttu-id="c57a8-146">此版本的 MRTK 會修改 MRTK 資料夾結構的版面配置。</span><span class="sxs-lookup"><span data-stu-id="c57a8-146">This version of MRTK modifies the layout of the MRTK folder structure.</span></span> <span data-ttu-id="c57a8-147">這項變更會將所有 MRTK 程式碼封裝成單一資料夾階層，並減少所有 MRTK 檔案的路徑總長度。</span><span class="sxs-lookup"><span data-stu-id="c57a8-147">This change encapsulates all MRTK code into a single folder hierarchy and reduces the total path length of all MRTK files.</span></span>

| <span data-ttu-id="c57a8-148">上一個資料夾</span><span class="sxs-lookup"><span data-stu-id="c57a8-148">Previous Folder</span></span> | <span data-ttu-id="c57a8-149">新增資料夾</span><span class="sxs-lookup"><span data-stu-id="c57a8-149">New Folder</span></span> |
| --- | --- |
| <span data-ttu-id="c57a8-150">MixedRealityToolkit</span><span class="sxs-lookup"><span data-stu-id="c57a8-150">MixedRealityToolkit</span></span> | <span data-ttu-id="c57a8-151">MRTK\Core</span><span class="sxs-lookup"><span data-stu-id="c57a8-151">MRTK\Core</span></span> |
| <span data-ttu-id="c57a8-152">MixedRealityToolkit 範例</span><span class="sxs-lookup"><span data-stu-id="c57a8-152">MixedRealityToolkit.Examples</span></span> | <span data-ttu-id="c57a8-153">MRTK\Examples</span><span class="sxs-lookup"><span data-stu-id="c57a8-153">MRTK\Examples</span></span> |
| <span data-ttu-id="c57a8-154">MixedRealityToolkit 副檔名</span><span class="sxs-lookup"><span data-stu-id="c57a8-154">MixedRealityToolkit.Extensions</span></span> | <span data-ttu-id="c57a8-155">MRTK\Extensions</span><span class="sxs-lookup"><span data-stu-id="c57a8-155">MRTK\Extensions</span></span> |
| <span data-ttu-id="c57a8-156">MixedRealityToolkit。提供者</span><span class="sxs-lookup"><span data-stu-id="c57a8-156">MixedRealityToolkit.Providers</span></span> | <span data-ttu-id="c57a8-157">MRTK\Providers</span><span class="sxs-lookup"><span data-stu-id="c57a8-157">MRTK\Providers</span></span> |
| <span data-ttu-id="c57a8-158">MixedRealityToolkit SDK</span><span class="sxs-lookup"><span data-stu-id="c57a8-158">MixedRealityToolkit.SDK</span></span> | <span data-ttu-id="c57a8-159">MRTK\SDK</span><span class="sxs-lookup"><span data-stu-id="c57a8-159">MRTK\SDK</span></span> |
| <span data-ttu-id="c57a8-160">MixedRealityToolkit 服務</span><span class="sxs-lookup"><span data-stu-id="c57a8-160">MixedRealityToolkit.Services</span></span> | <span data-ttu-id="c57a8-161">MRTK\Services</span><span class="sxs-lookup"><span data-stu-id="c57a8-161">MRTK\Services</span></span> |
| <span data-ttu-id="c57a8-162">MixedRealityToolkit。測試</span><span class="sxs-lookup"><span data-stu-id="c57a8-162">MixedRealityToolkit.Tests</span></span> | <span data-ttu-id="c57a8-163">MRTK\Tests</span><span class="sxs-lookup"><span data-stu-id="c57a8-163">MRTK\Tests</span></span> |
| <span data-ttu-id="c57a8-164">MixedRealityToolkit 工具</span><span class="sxs-lookup"><span data-stu-id="c57a8-164">MixedRealityToolkit.Tools</span></span> | <span data-ttu-id="c57a8-165">MRTK\Tools</span><span class="sxs-lookup"><span data-stu-id="c57a8-165">MRTK\Tools</span></span> |

> [!IMPORTANT]
> <span data-ttu-id="c57a8-166">`MixedRealityToolkit.Generated`包含客戶產生的檔案，且保持不變。</span><span class="sxs-lookup"><span data-stu-id="c57a8-166">The `MixedRealityToolkit.Generated` contains customer generated files and remains unchanged.</span></span>

<span data-ttu-id="c57a8-167">**MRTK 工具箱**</span><span class="sxs-lookup"><span data-stu-id="c57a8-167">**MRTK Toolbox**</span></span>

![MRTK 工具箱](../features/Images/Tools/MRTKToolboxWindow.png)

<span data-ttu-id="c57a8-169">[MRTK 工具箱](../features/README_Toolbox.md)是 Unity 編輯器視窗公用程式，可讓您輕鬆地探索 MRTK UX 預製專案元件並產生到目前的場景中。</span><span class="sxs-lookup"><span data-stu-id="c57a8-169">The [MRTK Toolbox](../features/README_Toolbox.md) is a Unity editor window utility that makes it easy to discover and spawn MRTK UX prefab components into the current scene.</span></span> <span data-ttu-id="c57a8-170">您可以使用視窗頂端的搜尋列，在 view 中篩選項目。</span><span class="sxs-lookup"><span data-stu-id="c57a8-170">Items can be filtered in view by using the search bar at the top of the window.</span></span> <span data-ttu-id="c57a8-171">[工具箱] 視窗的設計目的是要將 MRTK 的現成 prefabs 產生到目前的場景中。</span><span class="sxs-lookup"><span data-stu-id="c57a8-171">The toolbox window is designed to spawn MRTK out-of-box prefabs into the current scene.</span></span>

<span data-ttu-id="c57a8-172">**點一下以放置**</span><span class="sxs-lookup"><span data-stu-id="c57a8-172">**Tap to Place**</span></span>

<span data-ttu-id="c57a8-173">點[一下，就是用](../features/README_TapToPlace.md)來輕鬆地將遊戲物件放在表面上的互動元件。</span><span class="sxs-lookup"><span data-stu-id="c57a8-173">[Tap to Place](../features/README_TapToPlace.md) is a far interaction component used to easily place a game object on surface.</span></span> <span data-ttu-id="c57a8-174">點一下以使用兩個按鍵的組合，並使用前端移動來放置物件。</span><span class="sxs-lookup"><span data-stu-id="c57a8-174">Tap to Place uses a combination of two clicks and head movement to place an object.</span></span>

![TapToPlace](../features/Images/Solver/TapToPlace/TapToPlaceIntroGif.gif)

<span data-ttu-id="c57a8-176">按鈕設定協助程式 **已新增至 Pressable 按鈕** 
 ![按鈕設定協助程式 ](https://user-images.githubusercontent.com/9789716/70167111-e3175600-167a-11ea-9c52-444509c06105.gif) 這項新功能可讓您輕鬆地變更按鈕的圖示和文字。</span><span class="sxs-lookup"><span data-stu-id="c57a8-176">**Button Config Helper added to Pressable Buttons**
![Button Config Helper](https://user-images.githubusercontent.com/9789716/70167111-e3175600-167a-11ea-9c52-444509c06105.gif) This new feature makes it easy to change the icon and text of the buttons.</span></span> <span data-ttu-id="c57a8-177">圖示支援四、sprite 和 TextMesh Pro 的 .SDF 字型材質。</span><span class="sxs-lookup"><span data-stu-id="c57a8-177">Icon supports quad, sprite, and TextMesh Pro's SDF font texture.</span></span> <span data-ttu-id="c57a8-178">如需詳細資料，請參閱 MRTK 的 [按鈕檔](../features/README_Button.md#how-to-change-the-icon-and-text) 。</span><span class="sxs-lookup"><span data-stu-id="c57a8-178">See MRTK's [Button documentation](../features/README_Button.md#how-to-change-the-icon-and-text) for the details.</span></span>

<span data-ttu-id="c57a8-179">**新的 HoloLens 2 樣式切換按鈕-核取方塊、切換、無線電**</span><span class="sxs-lookup"><span data-stu-id="c57a8-179">**New HoloLens 2-style Toggle Buttons - Checkbox, Switch, Radio**</span></span>
<br/><img src="https://user-images.githubusercontent.com/13754172/75299797-df631d80-57ea-11ea-8857-8ef647df0aca.gif" width="450" alt="Button Config Helper">
<br/><img src="https://user-images.githubusercontent.com/13754172/75299783-d6724c00-57ea-11ea-88b1-85e4a585212f.gif" width="450" alt="Pressabe button">

<span data-ttu-id="c57a8-180">**功能表的增強功能**</span><span class="sxs-lookup"><span data-stu-id="c57a8-180">**Hand Menu Improvements**</span></span>

<span data-ttu-id="c57a8-181">在許多應用程式中，已調整了手中的功能表。</span><span class="sxs-lookup"><span data-stu-id="c57a8-181">Hand menu has been adapted in many applications.</span></span> <span data-ttu-id="c57a8-182">我們發現的最大問題之一，是在操作物件或與其他內容互動等情況下，發生意外的錯誤啟用。已將新的「注視啟用」選項新增至 HandConstraintPalmUp.cs，以防止啟用錯誤。</span><span class="sxs-lookup"><span data-stu-id="c57a8-182">One of the biggest issue we found is the accidental false activation while manipulating objects or interacting with other content, etc. New 'Gaze Activation' option added to HandConstraintPalmUp.cs to prevent false activations.</span></span> <span data-ttu-id="c57a8-183">使用這個選項時，功能表不會不慎顯示，直到使用者查看為止。</span><span class="sxs-lookup"><span data-stu-id="c57a8-183">With this option, the menu does not accidentally show up, until the user look at the hand.</span></span><br/>
<span data-ttu-id="c57a8-184">![0416_HandMenu_02](https://user-images.githubusercontent.com/13754172/79507261-4aabbd80-7fec-11ea-95c4-6e3f4bd18c11.gif)</span><span class="sxs-lookup"><span data-stu-id="c57a8-184">![0416_HandMenu_02](https://user-images.githubusercontent.com/13754172/79507261-4aabbd80-7fec-11ea-95c4-6e3f4bd18c11.gif)</span></span>

<span data-ttu-id="c57a8-185">**手動功能表範例更新**</span><span class="sxs-lookup"><span data-stu-id="c57a8-185">**Hand Menu Examples update**</span></span>

<span data-ttu-id="c57a8-186">新增大型功能表互動範例1：抓取 & 的提取功能表以進行世界鎖定</span><span class="sxs-lookup"><span data-stu-id="c57a8-186">[New] Large menu interaction example 1: Grab & Pull menu to world-lock</span></span><br/>
<span data-ttu-id="c57a8-187">![0416_HandMenu_03](https://user-images.githubusercontent.com/13754172/79507983-90b55100-7fed-11ea-9062-630c892950cb.gif)</span><span class="sxs-lookup"><span data-stu-id="c57a8-187">![0416_HandMenu_03](https://user-images.githubusercontent.com/13754172/79507983-90b55100-7fed-11ea-9062-630c892950cb.gif)</span></span>

<span data-ttu-id="c57a8-188">新增大型功能表互動範例 2-自動世界-鎖定丟手</span><span class="sxs-lookup"><span data-stu-id="c57a8-188">[New] Large menu interaction example 2 - Auto world-lock on hand drop</span></span><br/>
<span data-ttu-id="c57a8-189">![0416_HandMenu_04](https://user-images.githubusercontent.com/13754172/79508227-f9043280-7fed-11ea-995f-ac3cfe42fe65.gif)</span><span class="sxs-lookup"><span data-stu-id="c57a8-189">![0416_HandMenu_04](https://user-images.githubusercontent.com/13754172/79508227-f9043280-7fed-11ea-995f-ac3cfe42fe65.gif)</span></span>

<span data-ttu-id="c57a8-190">**實驗)  (對話方塊**</span><span class="sxs-lookup"><span data-stu-id="c57a8-190">**Dialog (Experimental)**</span></span>
<br/><img src="../features/Images/Dialog/MRTK_UX_Dialog_Main.png" width="450" alt="UX Dialog Box">

<span data-ttu-id="c57a8-191">對話方塊 UI 已使用新的 HoloLens 2 shell 樣式設計更新從 HoloToolkit 移植。</span><span class="sxs-lookup"><span data-stu-id="c57a8-191">Dialog UI has been ported over from HoloToolkit with new HoloLens 2 shell-style design updates.</span></span>

<span data-ttu-id="c57a8-192">**停駐 (實驗)**</span><span class="sxs-lookup"><span data-stu-id="c57a8-192">**Dock (Experimental)**</span></span>
<br/><img src="https://user-images.githubusercontent.com/621574/76669327-65e86080-6548-11ea-85a3-f84f6b367f97.gif" width="450" alt="Dock">

<span data-ttu-id="c57a8-193">此控制項可讓您將物件移入和移出預定的位置，以建立調色板、貨架和導覽列。</span><span class="sxs-lookup"><span data-stu-id="c57a8-193">This control enables moving objects in and out of predetermined positions, to create palettes, shelves and navigation bars.</span></span>

<span data-ttu-id="c57a8-194">**Unity Profiler 標記**</span><span class="sxs-lookup"><span data-stu-id="c57a8-194">**Unity Profiler markers**</span></span>

<span data-ttu-id="c57a8-195">此版本的 MRTK 已將 Unity Profiler 標記新增至輸入系統和資料提供者。</span><span class="sxs-lookup"><span data-stu-id="c57a8-195">This version of MRTK has added Unity Profiler markers to the input system and data providers.</span></span> <span data-ttu-id="c57a8-196">這些標記提供在 MRTK 輸入系統中花費時間的詳細資訊，可以用來協助優化應用程式。</span><span class="sxs-lookup"><span data-stu-id="c57a8-196">These markers provide detailed information on where time is spent in the MRTK input system that can be used to help optimize applications.</span></span>

<span data-ttu-id="c57a8-197">標記採用 "[MRTK] ClassWithoutNamespace 方法" 的格式。</span><span class="sxs-lookup"><span data-stu-id="c57a8-197">Markers take the format of "[MRTK] ClassWithoutNamespace.Method".</span></span>

![Profiler 標記](../features/Images/ReleaseNotes/ProfilerMarkers.png)

<span data-ttu-id="c57a8-199">**WindowsApiChecker： IsMethodAvailable () 、IsPropertyAvailable () 和 IsTypeAvailable ()**</span><span class="sxs-lookup"><span data-stu-id="c57a8-199">**WindowsApiChecker: IsMethodAvailable(), IsPropertyAvailable() and IsTypeAvailable()**</span></span>

<span data-ttu-id="c57a8-200">此版本的 MRTK 會將三個新方法新增至 [`WindowsApiChecker`](xref:Microsoft.MixedReality.Toolkit.Windows.Utilities.WindowsApiChecker) 類別： `IsMethodAvailable` 、 `IsPropertyAvailable` 和 `IsTypeAvailable` 。</span><span class="sxs-lookup"><span data-stu-id="c57a8-200">This version of MRTK adds three new methods to the [`WindowsApiChecker`](xref:Microsoft.MixedReality.Toolkit.Windows.Utilities.WindowsApiChecker) class: `IsMethodAvailable`, `IsPropertyAvailable` and `IsTypeAvailable`.</span></span> <span data-ttu-id="c57a8-201">這些方法可讓您檢查 Windows 10 上的功能支援，而且偏好使用這些 `UniversalApiContractV#_IsAvailable` 屬性。</span><span class="sxs-lookup"><span data-stu-id="c57a8-201">These methods allow for checking for feature support on Windows 10 and are preferred over using the `UniversalApiContractV#_IsAvailable` properties.</span></span>

<span data-ttu-id="c57a8-202">**協助程式取得文字輸入欄位，以使用 MixedRealityKeyboard for UnityUI、TextMeshPro (實驗性)**</span><span class="sxs-lookup"><span data-stu-id="c57a8-202">**Helpers to get text input fields working with MixedRealityKeyboard for UnityUI, TextMeshPro (Experimental)**</span></span>

<img src="https://user-images.githubusercontent.com/168492/77582981-86e07800-6e9d-11ea-86e5-bf2c0840296c.png" width="300" alt="MRTK Keyboard for unity" />

<span data-ttu-id="c57a8-203">我們引進了兩個協助程式元件， [`UI_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.UI_KeyboardInputField) [`TMP_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.TMP_KeyboardInputField) 可新增至 Unity UI 中的文字輸入欄位，讓 HoloLens 2 和 Windows Mixed Reality 鍵盤在按一下欄位時顯示。</span><span class="sxs-lookup"><span data-stu-id="c57a8-203">We have introduced two helper components, [`UI_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.UI_KeyboardInputField) and [`TMP_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.TMP_KeyboardInputField) that can be added to text input fields in Unity UI to enable the HoloLens 2 and Windows Mixed Reality Keyboard to show up when the fields are clicked.</span></span>

<span data-ttu-id="c57a8-204">如需詳細資訊，請參閱- [Mixed Reality 鍵盤](../reference-docs/MixedRealityKeyboard/README_MixedRealityKeyboard.md)協助程式。</span><span class="sxs-lookup"><span data-stu-id="c57a8-204">For more information, see - [Mixed Reality Keyboard Helpers](../reference-docs/MixedRealityKeyboard/README_MixedRealityKeyboard.md).</span></span>

<span data-ttu-id="c57a8-205">**方格物件集合對齊選項**</span><span class="sxs-lookup"><span data-stu-id="c57a8-205">**Grid Object Collection Alignment Options**</span></span>

<img src="https://user-images.githubusercontent.com/39840334/79289136-5c228780-7e7d-11ea-82b4-07959e42c3ed.gif" width="300" alt="Alignment Options" />

<span data-ttu-id="c57a8-206">我們新增了可選擇如何對齊格線中的元素、在執行資料列 then 資料行配置時，是在中央軸或沿著左/右軸對齊的功能 (頂端/底部軸) </span><span class="sxs-lookup"><span data-stu-id="c57a8-206">We have added the ability to choose how the elements in the grid are aligned, whether they are aligned in the center or along the left/right axis (top/bottom axis when doing row then column layout)</span></span>

<span data-ttu-id="c57a8-207">**方格物件集合錨點變更**</span><span class="sxs-lookup"><span data-stu-id="c57a8-207">**Grid Object Collection Anchor Changes**</span></span>

<img src="https://user-images.githubusercontent.com/39840334/79516745-17bff480-8001-11ea-8492-cfa953c451da.gif" width="300" alt="Anchor Changes" />

<span data-ttu-id="c57a8-208">我們變更了格線物件集合行為，使其與 Unity 的版面配置群組行為更趨一致，方法是沿著物件的中央軸對齊錨點。</span><span class="sxs-lookup"><span data-stu-id="c57a8-208">We made changes to Grid Object Collection behavior to be more in line with Unity's layout group behaviors by aligning the anchor along an object's central axis.</span></span> <span data-ttu-id="c57a8-209">舊的方格物件集合行為可以使用欄位來切換 `AnchorAlongAxis` 。</span><span class="sxs-lookup"><span data-stu-id="c57a8-209">The old Grid Object Collection behavior can be toggled with the `AnchorAlongAxis` field.</span></span>

<span data-ttu-id="c57a8-210">**調整輸入模擬攝影機控制項**</span><span class="sxs-lookup"><span data-stu-id="c57a8-210">**Adjusted input simulation camera control**</span></span>

<span data-ttu-id="c57a8-211">使用編輯器內輸入模擬的相機控制速度較慢，以提供更流暢的體驗，而且現在從幀 untied。</span><span class="sxs-lookup"><span data-stu-id="c57a8-211">Camera control speed using in-editor input simulation is slower for a smoother experience and is now untied from framerate.</span></span> <span data-ttu-id="c57a8-212">快速相機控制項現在以右移的方式啟動，而不是按右 Shift 鍵</span><span class="sxs-lookup"><span data-stu-id="c57a8-212">Fast camera control now activated with Right Shift instead of Right Ctrl</span></span>

<span data-ttu-id="c57a8-213">**免參與 GGV 輸入模擬**</span><span class="sxs-lookup"><span data-stu-id="c57a8-213">**Hands-free GGV input simulation**</span></span>

<img src="https://user-images.githubusercontent.com/39840334/79164615-40908180-7d96-11ea-8195-6be34d4df8d6.gif" width="300" alt="Hands-free GGV input"/>

<span data-ttu-id="c57a8-214">我們已啟用與物件互動的能力，而不需要在編輯器內輸入模擬服務中攜帶手。</span><span class="sxs-lookup"><span data-stu-id="c57a8-214">We've enabled the ability to interact with objects without bringing hands within the in-editor input simulation service.</span></span> <span data-ttu-id="c57a8-215">旋轉相機，讓注視游標停留在互動物件上方，然後按一下滑鼠左鍵來與其互動。</span><span class="sxs-lookup"><span data-stu-id="c57a8-215">Rotate the camera so that the gaze cursor is over an interactable object, and click on the left mouse button to interact with it.</span></span>

<span data-ttu-id="c57a8-216">**按鈕設定協助程式**</span><span class="sxs-lookup"><span data-stu-id="c57a8-216">**Button Config Helper**</span></span>

<img src="https://user-images.githubusercontent.com/168492/81211778-bb5d4e80-8f88-11ea-94c7-33cf265586df.png" width="300" alt="Button Config Helper" />

<span data-ttu-id="c57a8-217">按鈕設定協助程式是一項編輯器功能，可讓您更輕鬆地自訂 MRTK 按鈕。</span><span class="sxs-lookup"><span data-stu-id="c57a8-217">The Button Config Helper is an editor feature that makes it easier to customize MRTK buttons.</span></span> <span data-ttu-id="c57a8-218">現在可以更輕鬆地：</span><span class="sxs-lookup"><span data-stu-id="c57a8-218">It's now much easier to:</span></span>

- <span data-ttu-id="c57a8-219">更新按鈕標籤文字</span><span class="sxs-lookup"><span data-stu-id="c57a8-219">Update the button label text</span></span>
- <span data-ttu-id="c57a8-220">新增按鈕 click 事件接聽程式</span><span class="sxs-lookup"><span data-stu-id="c57a8-220">Add a button click event listener</span></span>
- <span data-ttu-id="c57a8-221">變更按鈕圖示</span><span class="sxs-lookup"><span data-stu-id="c57a8-221">Change the button icon</span></span>

<span data-ttu-id="c57a8-222">**[MRTK 設定] 對話方塊中的音訊空間定位器選取專案**</span><span class="sxs-lookup"><span data-stu-id="c57a8-222">**Audio Spatializer Selection in MRTK configuration dialog**</span></span>

<span data-ttu-id="c57a8-223">您現在可以在 [MRTK 設定] 對話方塊中指定音訊空間定位器。</span><span class="sxs-lookup"><span data-stu-id="c57a8-223">The audio spatializer can now be specified in the MRTK configuration dialog.</span></span> <span data-ttu-id="c57a8-224">安裝新的 spatializers （例如 [Microsoft 空間定位器](https://www.nuget.org/packages/Microsoft.SpatialAudio.Spatializer.Unity/)）時，將會重新提示允許您輕鬆地選取。</span><span class="sxs-lookup"><span data-stu-id="c57a8-224">Installing new spatializers, such as the [Microsoft Spatializer](https://www.nuget.org/packages/Microsoft.SpatialAudio.Spatializer.Unity/), will re-prompt to allow for easy selection.</span></span>

![MRTK 設定 Select 空間定位器](../features/Images/ReleaseNotes/SpatializerSelection.png)

<span data-ttu-id="c57a8-226">**物件操作工具已分級為 SDK**</span><span class="sxs-lookup"><span data-stu-id="c57a8-226">**Object manipulator graduated to SDK**</span></span>

![物件操作工具](../features//Images/ManipulationHandler/MRTK_Manipulation_Main.png)

<span data-ttu-id="c57a8-228">ObjectManipulator 現在已針對 SDK 進行了分級，不再是實驗性功能。</span><span class="sxs-lookup"><span data-stu-id="c57a8-228">ObjectManipulator now graduated to SDK and is no longer an experimental feature.</span></span> <span data-ttu-id="c57a8-229">此控制項會取代現在已被取代的現有 ManipulationHandler 類別。</span><span class="sxs-lookup"><span data-stu-id="c57a8-229">This control is replacing the existing ManipulationHandler class which is now deprecated.</span></span> <span data-ttu-id="c57a8-230">ObjectManipulator 隨附新的更具彈性的條件約束系統，並正確地回應物理。</span><span class="sxs-lookup"><span data-stu-id="c57a8-230">ObjectManipulator comes with a new more flexible constraint system and correctly responds to physics.</span></span> <span data-ttu-id="c57a8-231">您可以在物件操作工具 [檔](../features/README_ObjectManipulator.md)中找到完整的功能清單和指南，以瞭解如何進行設定。</span><span class="sxs-lookup"><span data-stu-id="c57a8-231">A full feature list and guide how to set up can be found in [object manipulator documentation](../features/README_ObjectManipulator.md).</span></span>
<span data-ttu-id="c57a8-232">使用者可以利用新的 [遷移視窗](../features/Tools/MigrationWindow.md) ，使用 ManipulationHandler 將其現有的 gameobject 升級至 ObjectManipulator</span><span class="sxs-lookup"><span data-stu-id="c57a8-232">Users can take advantage of the new [migration window](../features/Tools/MigrationWindow.md) to upgrade their existing gameobject using ManipulationHandler to ObjectManipulator</span></span>

<span data-ttu-id="c57a8-233">**界限控制項改善**</span><span class="sxs-lookup"><span data-stu-id="c57a8-233">**Bounds control improvements**</span></span>

<span data-ttu-id="c57a8-234">我們已大幅增加測試涵蓋範圍來控制此版本，並解決了周框方塊使用者的其中一個最大痛點：界限控制項現在不會再重新建立其對設定變更的視覺效果。</span><span class="sxs-lookup"><span data-stu-id="c57a8-234">We extensively increased test coverage for bounds control this version and addressed one of the biggest pain points of users of bounding box: bounds control will now no longer recreate its visuals on configuration changes.</span></span> <span data-ttu-id="c57a8-235">此外，它現在支援在執行時間期間重新設定任何屬性。</span><span class="sxs-lookup"><span data-stu-id="c57a8-235">Also it now supports reconfiguring any property during runtime.</span></span> <span data-ttu-id="c57a8-236">此外，DrawTetherWhenManipulating 和 HandlesIgnoreCollider 屬性現在可設定為每個控制碼類型。</span><span class="sxs-lookup"><span data-stu-id="c57a8-236">Also the properties DrawTetherWhenManipulating and HandlesIgnoreCollider are now configurable per handle type.</span></span>

### <a name="breaking-changes-in-240"></a><span data-ttu-id="c57a8-237">2.4.0 中的重大變更</span><span class="sxs-lookup"><span data-stu-id="c57a8-237">Breaking changes in 2.4.0</span></span>

<span data-ttu-id="c57a8-238">**目視注視 API**</span><span class="sxs-lookup"><span data-stu-id="c57a8-238">**Eye Gaze API**</span></span>

<span data-ttu-id="c57a8-239">`UseEyeTracking`從執行的屬性 `GazeProvider` 已重新 `IMixedRealityEyeGazeProvider` 命名為 `IsEyeTrackingEnabled` 。</span><span class="sxs-lookup"><span data-stu-id="c57a8-239">The `UseEyeTracking` property from `GazeProvider` implementation of `IMixedRealityEyeGazeProvider` was renamed to `IsEyeTrackingEnabled`.</span></span>

<span data-ttu-id="c57a8-240">如果您先前已執行此操作 .。。</span><span class="sxs-lookup"><span data-stu-id="c57a8-240">If you did this previously...</span></span>

```csharp
if (CoreServices.InputSystem.GazeProvider is GazeProvider gazeProvider)
{
    gazeProvider.UseEyeTracking = true;
}
```

<span data-ttu-id="c57a8-241">現在就完成了 .。。</span><span class="sxs-lookup"><span data-stu-id="c57a8-241">Do this now...</span></span>

```csharp
if (CoreServices.InputSystem.GazeProvider is GazeProvider gazeProvider)
{
    gazeProvider.IsEyeTrackingEnabled = true;
}
```

<span data-ttu-id="c57a8-242">**眼睛設定**</span><span class="sxs-lookup"><span data-stu-id="c57a8-242">**Eye gaze setup**</span></span>

<span data-ttu-id="c57a8-243">此版本的 MRTK 會修改眼睛設定所需的步驟。</span><span class="sxs-lookup"><span data-stu-id="c57a8-243">This version of MRTK modifies the steps required for eye gaze setup.</span></span> <span data-ttu-id="c57a8-244">您可以在輸入指標設定檔的注視設定中找到 [ _IsEyeTrackingEnabled_ ] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="c57a8-244">The _'IsEyeTrackingEnabled'_ checkbox can be found in the gaze settings of the input pointer profile.</span></span> <span data-ttu-id="c57a8-245">核取此方塊將會啟用以眼睛為基礎的眼睛，而不是預設的標頭。</span><span class="sxs-lookup"><span data-stu-id="c57a8-245">Checking this box will enable eye based gaze, rather then the default head based gaze.</span></span>

<span data-ttu-id="c57a8-246">如需有關這些變更的詳細資訊，以及適用于眼睛追蹤設定的完整指示，請參閱 [眼睛追蹤](../features/EyeTracking/EyeTracking_BasicSetup.md) 文章。</span><span class="sxs-lookup"><span data-stu-id="c57a8-246">For more information on these changes and complete instructions for eye tracking setup, please see the [eye tracking](../features/EyeTracking/EyeTracking_BasicSetup.md) article.</span></span>

### <a name="known-issues-in-240"></a><span data-ttu-id="c57a8-247">2.4.0 中的已知問題</span><span class="sxs-lookup"><span data-stu-id="c57a8-247">Known issues in 2.4.0</span></span>

<span data-ttu-id="c57a8-248">**Unity 2019.3 中的 [MRTK 配置器] 對話方塊未顯示 [啟用適用于 Unity 的 MSBuild]**</span><span class="sxs-lookup"><span data-stu-id="c57a8-248">**MRTK Configurator dialog does not show 'Enable MSBuild for Unity' in Unity 2019.3**</span></span>

<span data-ttu-id="c57a8-249">有一個問題，就是在2019.3 中啟用 Unity 的 MSBuild 可能會導致無限迴圈， ([#7239](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/7239)) 的封裝還原。</span><span class="sxs-lookup"><span data-stu-id="c57a8-249">An issue exists where enabling MSBuild for Unity in 2019.3 may result in an infinite loop restoring packages ([#7239](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/7239)).</span></span>

<span data-ttu-id="c57a8-250">因應措施是，可以使用 [適用于 Unity 的 NuGet](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest)來匯入 DotNetWinRT 套件。</span><span class="sxs-lookup"><span data-stu-id="c57a8-250">As a workaround, the Microsoft.Windows.DotNetWinRT package can be imported using [NuGet for Unity](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest).</span></span>

<span data-ttu-id="c57a8-251">**重複的元件版本和多個先行編譯的元件 Unity 2018。4**</span><span class="sxs-lookup"><span data-stu-id="c57a8-251">**Duplicate Assembly Version and Multiple Precompiled Assemblies Unity 2018.4**</span></span>

<span data-ttu-id="c57a8-252">如果平臺從獨立切換至 UWP，然後回到 Unity 2018.4 中的獨立，則主控台可能會出現下列錯誤：</span><span class="sxs-lookup"><span data-stu-id="c57a8-252">If the platform is switched from Standalone to UWP and then back to Standalone in Unity 2018.4, the following errors might be in the console:</span></span>

```
PrecompiledAssemblyException: Multiple precompiled assemblies with the same name Microsoft.Windows.MixedReality.DotNetWinRT.dll included for the current platform. Only one assembly with the same name is allowed per platform. Assembly paths
```

```
Assets\MRTK\Examples\Demos\HandTracking\Scenes\Utilities\InspectorFields\AssemblyInfo.cs(6,12): error CS0579: Duplicate 'AssemblyVersion' attribute
```

<span data-ttu-id="c57a8-253">這些錯誤是因為 MSBuildForUnity 的刪除程式有問題。</span><span class="sxs-lookup"><span data-stu-id="c57a8-253">These errors are due to issues in the deletion process with MSBuildForUnity.</span></span>  <span data-ttu-id="c57a8-254">若要解決此問題，在獨立的情況下，請刪除資產根目錄中的 [相依性] 資料夾，然後重新開機 unity。</span><span class="sxs-lookup"><span data-stu-id="c57a8-254">To resolve the issue, while in Standalone, delete the Dependencies folder at the root of Assets and restart unity.</span></span>

<span data-ttu-id="c57a8-255">如需詳細資訊，請參閱 [問題 7948](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/7948)。</span><span class="sxs-lookup"><span data-stu-id="c57a8-255">For a more details see [Issue 7948](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/7948).</span></span>

<span data-ttu-id="c57a8-256">**在 Unity 2019.3 上顯示為2D 平板的應用程式**</span><span class="sxs-lookup"><span data-stu-id="c57a8-256">**Applications appearing as a 2D slate on Unity 2019.3**</span></span>

<span data-ttu-id="c57a8-257">使用 Unity 2019.3 時，啟用 XR 支援不會將預設 SDK (舊版) 或外掛程式 (XR 管理) 。</span><span class="sxs-lookup"><span data-stu-id="c57a8-257">When using Unity 2019.3, enabling XR support does not configure a default SDK (legacy) or plugin (XR Mangement).</span></span> <span data-ttu-id="c57a8-258">這會導致應用程式受限於2D 石板。</span><span class="sxs-lookup"><span data-stu-id="c57a8-258">This results in applications being constrained to a 2D slate.</span></span> <span data-ttu-id="c57a8-259">有關解決此情況的詳細資訊，請參閱 [ 組建和部署 MRTK 一文](../updates-deployment/BuildAndDeploy.md#unity-20193-and-hololens)。</span><span class="sxs-lookup"><span data-stu-id="c57a8-259">Details on resolving this can be found in the [Building and Deploying MRTK article](../updates-deployment/BuildAndDeploy.md#unity-20193-and-hololens).</span></span>

<span data-ttu-id="c57a8-260">**Unity 2019.3： ARM 組建架構**</span><span class="sxs-lookup"><span data-stu-id="c57a8-260">**Unity 2019.3: ARM build architecture**</span></span>

<span data-ttu-id="c57a8-261">Unity 2019.3 中有一個 [已知問題](https://issuetracker.unity3d.com/issues/enabling-graphics-jobs-in-2019-dot-3-x-results-in-a-crash-or-nothing-rendering-on-hololens-2) ，會在 Visual Studio 中選取 ARM 作為組建架構時發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="c57a8-261">There is a [known issue](https://issuetracker.unity3d.com/issues/enabling-graphics-jobs-in-2019-dot-3-x-results-in-a-crash-or-nothing-rendering-on-hololens-2) in Unity 2019.3 that causes errors when selecting ARM as the build architecture in Visual Studio.</span></span> <span data-ttu-id="c57a8-262">建議的解決辦法是建立 ARM64。</span><span class="sxs-lookup"><span data-stu-id="c57a8-262">The recommended work around is to build for ARM64.</span></span> <span data-ttu-id="c57a8-263">如果這不是選項，請停用 [**編輯**   >  **專案設定**  >  **播放機**  >  **其他設定**] 中的圖形作業。</span><span class="sxs-lookup"><span data-stu-id="c57a8-263">If that is not an option, please disable **Graphics Jobs** in **Edit** > **Project Settings** > **Player** > **Other Settings**.</span></span> <span data-ttu-id="c57a8-264">如需詳細資訊，請參閱 [建立和部署](../updates-deployment/BuildAndDeploy.md#unity-20193-and-hololens)。</span><span class="sxs-lookup"><span data-stu-id="c57a8-264">For more information see [Building and Deploying](../updates-deployment/BuildAndDeploy.md#unity-20193-and-hololens).</span></span>

<span data-ttu-id="c57a8-265">**執行時間設定檔交換**</span><span class="sxs-lookup"><span data-stu-id="c57a8-265">**Runtime profile swapping**</span></span>

<span data-ttu-id="c57a8-266">MRTK 不完全支援在執行時間交換設定檔。</span><span class="sxs-lookup"><span data-stu-id="c57a8-266">MRTK does not fully support profile swapping at runtime.</span></span> <span data-ttu-id="c57a8-267">這項功能會在未來的版本中進行調查。</span><span class="sxs-lookup"><span data-stu-id="c57a8-267">This feature is being investigated for a future release.</span></span> <span data-ttu-id="c57a8-268">如需詳細資訊，請參閱 [4289](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/4289)、 [5465](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/5465) 和 [5466](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/5466) 問題。</span><span class="sxs-lookup"><span data-stu-id="c57a8-268">Please see issues [4289](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/4289), [5465](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/5465) and [5466](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/5466) for more information.</span></span>

<span data-ttu-id="c57a8-269">**Unity 2018： .NET 後端和 AR Foundation**</span><span class="sxs-lookup"><span data-stu-id="c57a8-269">**Unity 2018: .NET Backend and AR Foundation**</span></span>

<span data-ttu-id="c57a8-270">Unity 2018 有問題，在此使用 .NET 腳本後端建立通用 Windows 平臺專案時，Unity AR Foundation 套件將會失敗。</span><span class="sxs-lookup"><span data-stu-id="c57a8-270">There is an issue in Unity 2018 where, building a Universal Windows Platform project using the .NET scripting backend, the Unity AR Foundation package will fail.</span></span>

<span data-ttu-id="c57a8-271">若要解決此問題，請執行下列其中一個步驟：</span><span class="sxs-lookup"><span data-stu-id="c57a8-271">To work around this issue, please perform one of the following steps:</span></span>

- <span data-ttu-id="c57a8-272">將腳本後端切換至 IL2CPP</span><span class="sxs-lookup"><span data-stu-id="c57a8-272">Switch the scripting backend to IL2CPP</span></span>
- <span data-ttu-id="c57a8-273">在 [組建設定] 視窗中，取消核取 [Unity c # 專案]</span><span class="sxs-lookup"><span data-stu-id="c57a8-273">In the Build Settings window, uncheck \*\*Unity C# Projects"</span></span>
