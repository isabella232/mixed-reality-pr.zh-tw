---
title: 安裝指南
description: 在新專案中安裝 MRTK-Unity 的指南。
author: hferrone
ms.author: v-hferrone
ms.date: 09/9/2020
ms.localizationpriority: high
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: a9d727f5e0416b5faf76caf4049b7391363ede2f
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "101780969"
---
# <a name="installation-guide"></a><span data-ttu-id="08b7f-104">安裝指南</span><span class="sxs-lookup"><span data-stu-id="08b7f-104">Installation guide</span></span>

> [!CAUTION]
> <span data-ttu-id="08b7f-105">如果您不熟悉 Unity 中的 MRTK 或混合現實開發，我們建議您從 [unity 開發旅程](https://docs.microsoft.com/windows/mixed-reality/unity-development-overview?tabs=mrtk%2Chl2)的開端開始著手。</span><span class="sxs-lookup"><span data-stu-id="08b7f-105">If you're new to MRTK or Mixed Reality development in Unity, we recommend you start at the beginning of our [Unity development journey](https://docs.microsoft.com/windows/mixed-reality/unity-development-overview?tabs=mrtk%2Chl2).</span></span> <span data-ttu-id="08b7f-106">Unity 開發旅程是建議的 **MRTK 起始點**，特別是為了引導您完成安裝、核心概念，以及 Unity 中的 MRTK 使用。</span><span class="sxs-lookup"><span data-stu-id="08b7f-106">The Unity development journey is the **recommended starting point for MRTK**, specifically created to walk you through the installation, core concepts, and usage of MRTK in Unity.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="08b7f-107">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="08b7f-107">Prerequisites</span></span>

<span data-ttu-id="08b7f-108">若要開始使用 Mixed Reality 工具組，您將需要：</span><span class="sxs-lookup"><span data-stu-id="08b7f-108">To get started with the Mixed Reality Toolkit, you will need:</span></span>

* [<span data-ttu-id="08b7f-109">Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="08b7f-109">Visual Studio 2019</span></span>](https://visualstudio.microsoft.com/downloads/)
* [<span data-ttu-id="08b7f-110">Unity 2018.4 或 Unity 2019。4</span><span class="sxs-lookup"><span data-stu-id="08b7f-110">Unity 2018.4 or Unity 2019.4</span></span>](https://unity3d.com/get-unity/download/archive)

  <span data-ttu-id="08b7f-111">MRTK 支援 Unity 2018 上的 IL2CPP 和 .NET 腳本後端。</span><span class="sxs-lookup"><span data-stu-id="08b7f-111">MRTK supports both IL2CPP and .NET scripting backends on Unity 2018.</span></span>  
  <span data-ttu-id="08b7f-112">**強烈建議您從 MRTK 2.5 unity 2018.4.13 f1 或更新版本**，以供使用 Unity 2018 的客戶使用。</span><span class="sxs-lookup"><span data-stu-id="08b7f-112">Starting from MRTK 2.5 **Unity 2018.4.13f1 or later is strongly recommended** for customers using Unity 2018.</span></span> <span data-ttu-id="08b7f-113">仍支援舊版 Unity 2018.4，但現在需要額外的步驟來設定和升級至 Unity 2019。</span><span class="sxs-lookup"><span data-stu-id="08b7f-113">Earlier versions of Unity 2018.4 are still supported but now require extra steps to set up and to upgrade to Unity 2019.</span></span>

* <span data-ttu-id="08b7f-114">[Windows SDK 18362 +](https://developer.microsoft.com/windows/downloads/windows-10-sdk)。</span><span class="sxs-lookup"><span data-stu-id="08b7f-114">[Windows SDK 18362+](https://developer.microsoft.com/windows/downloads/windows-10-sdk).</span></span>

  <span data-ttu-id="08b7f-115">如果您要建立適用于 WMR、HoloLens 1 或 HoloLens 2 的 UWP 應用程式，則這是必要的。</span><span class="sxs-lookup"><span data-stu-id="08b7f-115">This is necessary if you are building a UWP app for WMR, HoloLens 1, or HoloLens 2.</span></span> <span data-ttu-id="08b7f-116">這在建立 OpenVR 時並不是必要的。</span><span class="sxs-lookup"><span data-stu-id="08b7f-116">This is not necessary when building for OpenVR.</span></span>

## <a name="add-mrtk-to-your-unity-project"></a><span data-ttu-id="08b7f-117">將 MRTK 新增至您的 Unity 專案</span><span class="sxs-lookup"><span data-stu-id="08b7f-117">Add MRTK to your Unity project</span></span>

> [!Note]
> <span data-ttu-id="08b7f-118">Unity 2019.4 和更新版本的使用者可以使用 Unity 封裝管理員匯入 MRTK。</span><span class="sxs-lookup"><span data-stu-id="08b7f-118">Users of Unity 2019.4 and newer, can use the Unity Package Manager to import MRTK.</span></span> <span data-ttu-id="08b7f-119">如需詳細資訊，請參閱 [使用 Unity 封裝管理員](configuration/usingupm.md) 。</span><span class="sxs-lookup"><span data-stu-id="08b7f-119">Please see [Using the Unity Package Manager](configuration/usingupm.md) for more information.</span></span>

### <a name="required"></a><span data-ttu-id="08b7f-120">必要</span><span class="sxs-lookup"><span data-stu-id="08b7f-120">Required</span></span>

1. [<span data-ttu-id="08b7f-121">取得最新的 MRTK Unity 套件</span><span class="sxs-lookup"><span data-stu-id="08b7f-121">Get the latest MRTK Unity packages</span></span>](#1-get-the-latest-mrtk-unity-packages)
1. [<span data-ttu-id="08b7f-122">將 MRTK 套件匯入到您的 Unity 專案</span><span class="sxs-lookup"><span data-stu-id="08b7f-122">Import MRTK packages into your Unity project</span></span>](#2-import-mrtk-packages-into-your-unity-project)
1. [<span data-ttu-id="08b7f-123">將您的 Unity 專案切換到目標平台</span><span class="sxs-lookup"><span data-stu-id="08b7f-123">Switch your Unity project to the target platform</span></span>](#3-switch-your-unity-project-to-the-target-platform)
1. [<span data-ttu-id="08b7f-124">使用新場景新增和設定 MRTK</span><span class="sxs-lookup"><span data-stu-id="08b7f-124">Add and configure MRTK with a new scene</span></span>](#4-add-and-configure-mrtk-with-a-new-scene)

### <a name="optional"></a><span data-ttu-id="08b7f-125">選擇性</span><span class="sxs-lookup"><span data-stu-id="08b7f-125">Optional</span></span>

* [<span data-ttu-id="08b7f-126">在 Unity 編輯器中執行 HandInteractionExamples 場景</span><span class="sxs-lookup"><span data-stu-id="08b7f-126">Run the HandInteractionExamples scene in the Unity Editor</span></span>](#run-the-handinteractionexamples-scene-in-the-unity-editor)
* [<span data-ttu-id="08b7f-127">入門教學課程</span><span class="sxs-lookup"><span data-stu-id="08b7f-127">Getting started tutorials</span></span>](#getting-started-tutorials)
* [<span data-ttu-id="08b7f-128">瞭解 MRTK 的核心構成要素</span><span class="sxs-lookup"><span data-stu-id="08b7f-128">Learn about the core building blocks of MRTK</span></span>](#learn-about-the-core-building-blocks-of-mrtk)
* [<span data-ttu-id="08b7f-129">XR SDK 快速入門手冊 (Unity 2019.3 或更新版本) </span><span class="sxs-lookup"><span data-stu-id="08b7f-129">XR SDK getting started guide (Unity 2019.3 or later)</span></span>](configuration/GettingStartedWithMRTKAndXRSDK.md)

### <a name="1-get-the-latest-mrtk-unity-packages"></a><span data-ttu-id="08b7f-130">1. 取得最新的 MRTK Unity 套件</span><span class="sxs-lookup"><span data-stu-id="08b7f-130">1. Get the latest MRTK Unity packages</span></span>

1. <span data-ttu-id="08b7f-131">移至 [ <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity/releases" target="_blank">MRTK 發行] 頁面</a>。</span><span class="sxs-lookup"><span data-stu-id="08b7f-131">Go to the <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity/releases" target="_blank">MRTK release page</a>.</span></span>
1. <span data-ttu-id="08b7f-132">在 [資產] 底下，下載：</span><span class="sxs-lookup"><span data-stu-id="08b7f-132">Under Assets, download:</span></span>
    * <span data-ttu-id="08b7f-133">**Microsoft.MixedRealityToolkit.Unity.Foundation.unitypackage**</span><span class="sxs-lookup"><span data-stu-id="08b7f-133">**Microsoft.MixedRealityToolkit.Unity.Foundation.unitypackage**</span></span>
    * <span data-ttu-id="08b7f-134"> (**_選用_**) MixedRealityToolkit。 unitypackage</span><span class="sxs-lookup"><span data-stu-id="08b7f-134">(**_Optional_**) Microsoft.MixedRealityToolkit.Unity.Extensions.unitypackage</span></span>
    * <span data-ttu-id="08b7f-135"> (**_選擇性_** 的) MixedRealityToolkit，例如 unitypackage</span><span class="sxs-lookup"><span data-stu-id="08b7f-135">(**_Optional_**) Microsoft.MixedRealityToolkit.Unity.Examples.unitypackage</span></span>
    * <span data-ttu-id="08b7f-136"> (**_選擇性_**) MixedRealityToolkit TestUtilities. unitypackage</span><span class="sxs-lookup"><span data-stu-id="08b7f-136">(**_Optional_**) Microsoft.MixedRealityToolkit.Unity.TestUtilities.unitypackage</span></span>
    * <span data-ttu-id="08b7f-137"> (**_版本到版本的升級所需，否則請_**) unitypackage</span><span class="sxs-lookup"><span data-stu-id="08b7f-137">(**_Required for version-to-version upgrades, Optional otherwise_**) Microsoft.MixedRealityToolkit.Unity.Tools.unitypackage</span></span>

<span data-ttu-id="08b7f-138">如需封裝及其內容的詳細資訊，請參閱 [MRTK 套件](packages-releases/MRTK_Packages.md)。</span><span class="sxs-lookup"><span data-stu-id="08b7f-138">For details on the packages and their contents, please see [MRTK Packages](packages-releases/MRTK_Packages.md).</span></span>

### <a name="2-import-mrtk-packages-into-your-unity-project"></a><span data-ttu-id="08b7f-139">2. 將 MRTK 封裝匯入 Unity 專案中</span><span class="sxs-lookup"><span data-stu-id="08b7f-139">2. Import MRTK packages into your Unity project</span></span>

1. <span data-ttu-id="08b7f-140">建立新的 Unity 專案，或開啟現有的專案。</span><span class="sxs-lookup"><span data-stu-id="08b7f-140">Create a new Unity project, or open an existing project.</span></span> <span data-ttu-id="08b7f-141">建立專案時，請務必選取 [3D] 作為範本類型。</span><span class="sxs-lookup"><span data-stu-id="08b7f-141">When creating a project, make sure to select "3D" as the template type.</span></span>
1. <span data-ttu-id="08b7f-142">匯入您下載的 **MixedRealityToolkit** ，方法是前往 [資產-> 匯入封裝-> 自訂套件]，選取 unitypackage 檔案，確定已核取所有要匯入的專案，然後選取 [匯入]。</span><span class="sxs-lookup"><span data-stu-id="08b7f-142">Import the **Microsoft.MixedRealityToolkit.Unity.Foundation.unitypackage** you downloaded by going into "Asset -> Import Package -> Custom Package", select the .unitypackage file, ensure all items to import are checked, and then select "Import".</span></span>
1. <span data-ttu-id="08b7f-143"> (**_選擇性_**) 匯入 **MixedRealityToolkit** ，遵循與基礎封裝相同的步驟。</span><span class="sxs-lookup"><span data-stu-id="08b7f-143">(**_Optional_**) Import the **Microsoft.MixedRealityToolkit.Unity.Extensions.unitypackage** following the same steps as the foundation package.</span></span> <span data-ttu-id="08b7f-144">擴充功能套件提供一組適用于 MRTK 的實用選擇性元件。</span><span class="sxs-lookup"><span data-stu-id="08b7f-144">The extensions package provides a set of useful optional components for the MRTK.</span></span>
1. <span data-ttu-id="08b7f-145"> (**_選擇性_**) 匯入 **MixedRealityToolkit** ，遵循與上述相同的步驟。</span><span class="sxs-lookup"><span data-stu-id="08b7f-145">(**_Optional_**) Import the **Microsoft.MixedRealityToolkit.Unity.Examples.unitypackage** following the same steps as above.</span></span> <span data-ttu-id="08b7f-146">範例套件是選擇性的，包含目前 MRTK 功能的實用示範場景。</span><span class="sxs-lookup"><span data-stu-id="08b7f-146">The examples package is optional and contains useful demonstration scenes for current MRTK features.</span></span> <span data-ttu-id="08b7f-147">**請注意，範例套件需要副檔名套件。**</span><span class="sxs-lookup"><span data-stu-id="08b7f-147">**Note that the Examples package requires the Extensions package.**</span></span>
1. <span data-ttu-id="08b7f-148">**_版本到版本升級需要 (，否則請_**) 匯入與基礎套件相同的步驟來匯入 **MixedRealityToolkit** 。</span><span class="sxs-lookup"><span data-stu-id="08b7f-148">(**_Required for version-to-version upgrades, Optional otherwise_**) Import the **Microsoft.MixedRealityToolkit.Unity.Tools.unitypackage** following the same steps as the foundation package.</span></span> <span data-ttu-id="08b7f-149">工具套件是選擇性的，並且包含可增強 MRTK 開發人員體驗的公用程式（例如 ExtensionServiceCreator）。</span><span class="sxs-lookup"><span data-stu-id="08b7f-149">The tools package is optional and contains useful tools, such as the ExtensionServiceCreator, that enhance the MRTK developer experience.</span></span>

> [!Note]
> <span data-ttu-id="08b7f-150">如果您使用 Unity 2018.4.12 f1 或更早版本，請注意主控台會出現編譯錯誤。</span><span class="sxs-lookup"><span data-stu-id="08b7f-150">If you are using Unity 2018.4.12f1 or earlier, note you will experience compilation errors shown in the console.</span></span> <span data-ttu-id="08b7f-151">移至 `Assets\MRTK\Providers\XRSDK\Microsoft.MixedReality.Toolkit.Providers.XRSDK.asmdef` [專案] 視窗中的，並移除偵測器中遺漏的參考。</span><span class="sxs-lookup"><span data-stu-id="08b7f-151">Go to `Assets\MRTK\Providers\XRSDK\Microsoft.MixedReality.Toolkit.Providers.XRSDK.asmdef` in the project window and remove the missing reference in the inspector.</span></span> <span data-ttu-id="08b7f-152">使用和重複執行這些步驟 `Assets\MRTK\Providers\Oculus\XRSDK\Microsoft.MixedReality.Toolkit.Providers.XRSDK.Oculus.asmdef` `Assets\MRTK\Providers\WindowsMixedReality\XRSDK\Microsoft.MixedReality.Toolkit.Providers.XRSDK.WMR.asmdef` 。</span><span class="sxs-lookup"><span data-stu-id="08b7f-152">Repeat those steps with `Assets\MRTK\Providers\Oculus\XRSDK\Microsoft.MixedReality.Toolkit.Providers.XRSDK.Oculus.asmdef` and `Assets\MRTK\Providers\WindowsMixedReality\XRSDK\Microsoft.MixedReality.Toolkit.Providers.XRSDK.WMR.asmdef`.</span></span> <span data-ttu-id="08b7f-153">請注意，您必須將這三個 asmdef 檔案取代為原始 (（亦即，升級至 Unity 2019 時未修改的) ），以還原變更。</span><span class="sxs-lookup"><span data-stu-id="08b7f-153">Note you must revert the changes by replacing those three asmdef files with original (i.e. unmodified) ones when upgrading to Unity 2019.</span></span>  

> [!Note]
> <span data-ttu-id="08b7f-154">Android 和 iOS 開發需要額外的套件安裝。</span><span class="sxs-lookup"><span data-stu-id="08b7f-154">Android and iOS development require additional package installations.</span></span> <span data-ttu-id="08b7f-155">如需詳細資訊，請參閱 [如何設定適用于 iOS 和 Android 的 MRTK](features/cross-platform/UsingARFoundation.md)。</span><span class="sxs-lookup"><span data-stu-id="08b7f-155">For more information, see [How to configure MRTK for iOS and Android](features/cross-platform/UsingARFoundation.md).</span></span>
<span data-ttu-id="08b7f-156">匯入基礎套件之後，您可能會看到類似下列的提示：</span><span class="sxs-lookup"><span data-stu-id="08b7f-156">After importing the Foundation package, you may see a prompt similar to the following:</span></span>

<img src="features/images/MRTK_UnitySetupPrompt.png" width="600" alt="MRTK Unity Setup">

<span data-ttu-id="08b7f-157">MRTK 正在嘗試設定您的專案，藉由執行下列動作來建立混合的現實解決方案：</span><span class="sxs-lookup"><span data-stu-id="08b7f-157">MRTK is attempting to set up your project for building Mixed Reality solutions by doing the following:</span></span>

* <span data-ttu-id="08b7f-158">為您目前的平臺啟用 XR 設定， (啟用 [XR] 核取方塊) 。</span><span class="sxs-lookup"><span data-stu-id="08b7f-158">Enable XR Settings for your current platform (enabling the XR checkbox).</span></span>
* <span data-ttu-id="08b7f-159">使用原始檔控制) 來強制執行對 Unity 專案的文字序列化/可見的中繼檔案 (建議。</span><span class="sxs-lookup"><span data-stu-id="08b7f-159">Force Text Serialization / Visible Meta files (recommended for Unity projects using source control).</span></span>

<span data-ttu-id="08b7f-160">接受這些選項完全是選擇性的，但建議使用。</span><span class="sxs-lookup"><span data-stu-id="08b7f-160">Accepting these options is completely optional, but recommended.</span></span>

<span data-ttu-id="08b7f-161">有些 prefabs 和資產需要 TextMesh Pro，這表示您需要安裝 TextMesh Pro 套件，且專案中的資產 (視窗-> TextMeshPro > 匯入 TMP 基本資源) 。</span><span class="sxs-lookup"><span data-stu-id="08b7f-161">Some prefabs and assets require TextMesh Pro, meaning you need the TextMesh Pro package installed and the assets in your project (Window -> TextMeshPro -> Import TMP Essential Resources).</span></span> <span data-ttu-id="08b7f-162">匯 **入 TMP Essentials 資源之後，您必須重新開機 Unity 才能看到變更**。</span><span class="sxs-lookup"><span data-stu-id="08b7f-162">**After you import TMP Essentials Resources, you need to restart Unity to see changes**.</span></span>

### <a name="3-switch-your-unity-project-to-the-target-platform"></a><span data-ttu-id="08b7f-163">3. 將 Unity 專案切換至目標平臺</span><span class="sxs-lookup"><span data-stu-id="08b7f-163">3. Switch your Unity project to the target platform</span></span>

<span data-ttu-id="08b7f-164">匯入封裝後，下一個步驟是為應用程式選取正確的平臺。</span><span class="sxs-lookup"><span data-stu-id="08b7f-164">With the packages imported, the next step is to select the correct platform for the application.</span></span>

<span data-ttu-id="08b7f-165">若要建立 **HoloLens 應用程式**，請切換至通用 Windows 平臺：</span><span class="sxs-lookup"><span data-stu-id="08b7f-165">To create a **HoloLens application**, switch to the Universal Windows Platform:</span></span>

1. <span data-ttu-id="08b7f-166">開啟功能表： File > 組建設定</span><span class="sxs-lookup"><span data-stu-id="08b7f-166">Open menu : File > Build Settings</span></span>
1. <span data-ttu-id="08b7f-167">在 [**平臺**] 清單中選取 **通用 Windows 平臺**</span><span class="sxs-lookup"><span data-stu-id="08b7f-167">Select **Universal Windows Platform** in the **Platform** list</span></span>
1. <span data-ttu-id="08b7f-168">按一下 [ **切換平臺** ] 按鈕</span><span class="sxs-lookup"><span data-stu-id="08b7f-168">Click the **Switch Platform** button</span></span>

    <img src="features/images/getting-started/SwitchPlatform.png" width="600" alt="Platform Switch">

>[!NOTE]
> <span data-ttu-id="08b7f-169">混合現實工具組會在選取平臺時，提示您將建議的變更套用至專案。</span><span class="sxs-lookup"><span data-stu-id="08b7f-169">The Mixed Reality Toolkit will prompt to apply recommended changes to the project when the platform is selected.</span></span> <span data-ttu-id="08b7f-170">當平臺切換時，如有必要，將會檢查並提示適當的設定。</span><span class="sxs-lookup"><span data-stu-id="08b7f-170">Whenever the platform is switched, the appropriate settings will be checked and prompted, if necessary.</span></span>

### <a name="4-add-and-configure-mrtk-with-a-new-scene"></a><span data-ttu-id="08b7f-171">4. 使用新場景新增和設定 MRTK</span><span class="sxs-lookup"><span data-stu-id="08b7f-171">4. Add and configure MRTK with a new scene</span></span>

1. <span data-ttu-id="08b7f-172">建立新的 Unity 專案，或在您目前的專案中啟動新的場景。</span><span class="sxs-lookup"><span data-stu-id="08b7f-172">Create a new Unity project, or start a new scene in your current project.</span></span>

1. <span data-ttu-id="08b7f-173">請確定您已匯入 MRTK 套件， (我們建議使用基礎和範例，但不需要) 遵循 [上述步驟](#2-import-mrtk-packages-into-your-unity-project)。</span><span class="sxs-lookup"><span data-stu-id="08b7f-173">Make sure you have imported the MRTK packages (we recommend both Foundation and Examples, though Examples is not required) following [the steps above](#2-import-mrtk-packages-into-your-unity-project).</span></span>

1. <span data-ttu-id="08b7f-174">從功能表列中，選取 [混合現實工具組-> 新增至場景並設定]</span><span class="sxs-lookup"><span data-stu-id="08b7f-174">From the menu bar, select Mixed Reality Toolkit -> Add to Scene and Configure</span></span>

    <img src="features/images/MRTK_ConfigureScene.png" width="300" alt="MRTK ConfigureScene">

    <span data-ttu-id="08b7f-175">偵測器現在會顯示目前使用中的 MRTK 設定檔和設定檔選取下拉式清單，其中已預先選取預設設定檔。</span><span class="sxs-lookup"><span data-stu-id="08b7f-175">The inspector will now show the currently active MRTK configuration profile and the profile selection dropdown, where the default profile is already preselected.</span></span>
    <span data-ttu-id="08b7f-176">設定檔會設定 MRTK 核心元件的行為，並在 [設定檔](features/Profiles/Profiles.md) 文章中有更詳細的說明。</span><span class="sxs-lookup"><span data-stu-id="08b7f-176">Profiles configure the behavior of MRTK core components and are described in more detail in the [profiles](features/Profiles/Profiles.md) article.</span></span>

    > [!NOTE]
    >
    > * <span data-ttu-id="08b7f-177">如果您是在 Unity 2019.3 或更新版本中使用 Unity 的 XR SDK，您應該選擇「DefaultXRSDKConfigurationProfile」。</span><span class="sxs-lookup"><span data-stu-id="08b7f-177">If you're using Unity's XR SDK in Unity 2019.3 or later, you should choose the "DefaultXRSDKConfigurationProfile".</span></span> <span data-ttu-id="08b7f-178">此設定檔會在需要時，使用 MRTK 的 XR SDK 系統和提供者來設定。</span><span class="sxs-lookup"><span data-stu-id="08b7f-178">This profile is set up with MRTK's XR SDK systems and providers, where needed.</span></span>  
    > * <span data-ttu-id="08b7f-179">如果您是在 HoloLens 或 HoloLens 2 上開始使用，您應該改為選擇 [DefaultHoloLens1ConfigurationProfile] 或 [DefaultHoloLens2ConfigurationProfile]。</span><span class="sxs-lookup"><span data-stu-id="08b7f-179">If you're getting started on the HoloLens or HoloLens 2, you should choose the "DefaultHoloLens1ConfigurationProfile" or DefaultHoloLens2ConfigurationProfile" instead.</span></span>  
    > * <span data-ttu-id="08b7f-180">如需 DefaultMixedRealityToolkitConfigurationProfile 與 DefaultHoloLens2ConfigurationProfile 之間差異的詳細資訊，請參閱 [設定檔](features/profiles/Profiles.md#hololens-2-profile) 。</span><span class="sxs-lookup"><span data-stu-id="08b7f-180">See the [profiles](features/profiles/Profiles.md#hololens-2-profile) for more information on the differences between DefaultMixedRealityToolkitConfigurationProfile and DefaultHoloLens2ConfigurationProfile.</span></span>

    <span data-ttu-id="08b7f-181">然後，您會在場景階層中看到下列內容：  </span><span class="sxs-lookup"><span data-stu-id="08b7f-181">You will then see the following in your Scene hierarchy:  </span></span><img src="features/images/MRTK_SceneSetup.png" width="300" alt="SceneSetup Hierarchy">

    <span data-ttu-id="08b7f-182">其中包含下列內容：</span><span class="sxs-lookup"><span data-stu-id="08b7f-182">Which contains the following:</span></span>

    * <span data-ttu-id="08b7f-183">**混合現實工具** 組-工具組本身，提供整個架構的集中設定進入點。</span><span class="sxs-lookup"><span data-stu-id="08b7f-183">**Mixed Reality Toolkit** - The toolkit itself, providing the central configuration entry point for the entire framework.</span></span>
    * <span data-ttu-id="08b7f-184">**MixedRealityPlayspace** -耳機的父物件，可確保在場景中正確地管理耳機/控制器和其他所需的系統。</span><span class="sxs-lookup"><span data-stu-id="08b7f-184">**MixedRealityPlayspace** - The parent object for the headset, which ensures the headset / controllers and other required systems are managed correctly in the scene.</span></span>
    * <span data-ttu-id="08b7f-185">主要相機會以子系的形式移至 Playspace，讓 Playspace 能夠與 Sdk 一起管理攝影機。</span><span class="sxs-lookup"><span data-stu-id="08b7f-185">The Main Camera is moved as a child to the Playspace - Which allows the playspace to manage the camera in conjunction with the SDKs.</span></span>

    >[!NOTE]
    > <span data-ttu-id="08b7f-186">在場景中工作時， **請勿移動主要攝影機** 或 **MixedRealityPlayspace**。</span><span class="sxs-lookup"><span data-stu-id="08b7f-186">While working in your scene, **DO NOT move the Main Camera** or the **MixedRealityPlayspace**.</span></span> <span data-ttu-id="08b7f-187">這些是由作用中 SDK 和 MRTK 分別控制。</span><span class="sxs-lookup"><span data-stu-id="08b7f-187">These are controlled by the active SDK and the MRTK respectively.</span></span> <span data-ttu-id="08b7f-188">您對主要攝影機或 MixedRealityPlayspace 轉換所做的任何設定都將會被覆寫，而且在最糟的情況下，會產生未定義的行為。</span><span class="sxs-lookup"><span data-stu-id="08b7f-188">Any settings you make to the Main Camera or MixedRealityPlayspace transforms will at best be overwritten, and at worst result in undefined behavior.</span></span>
    >
    > <span data-ttu-id="08b7f-189">您可以將其他 GameObject 新增至場景，並將其設為 MixedRealityPlayspace 的父系，以移動整個 rig、攝影機和 Playspace。</span><span class="sxs-lookup"><span data-stu-id="08b7f-189">The entire rig, Camera and Playspace, can be moved by adding another GameObject to the scene, and making it the parent of the MixedRealityPlayspace.</span></span> <span data-ttu-id="08b7f-190">當移動該物件時，Playspace 和相機會以鬆散的方式追蹤，受限於使用中 SDK 和 MRTK 所做的額外本機轉換變更。</span><span class="sxs-lookup"><span data-stu-id="08b7f-190">When that object is moved, the Playspace and Camera will follow loosely behind, subject to the additional local transform changes made by the active SDK and the MRTK.</span></span>
    >
    > <span data-ttu-id="08b7f-191">另一個選項是將場景內容相對於相機移動，不過這在包含導覽網格、地形或物件等內容的先進案例中會變成問題。</span><span class="sxs-lookup"><span data-stu-id="08b7f-191">Another option is to move the scene contents relative to the camera, although this can become problematic in advanced scenarios incorporating content such as Nav Meshes, terrains, or particle systems.</span></span>
    >
    > <span data-ttu-id="08b7f-192">您可以在 [Unity 的檔](https://docs.unity3d.com/Packages/com.unity.xr.legacyinputhelpers@2.1/manual/index.html#xr-rig-explanation) 和其他地方找到 AR/VR 相機 rig 的進一步討論。</span><span class="sxs-lookup"><span data-stu-id="08b7f-192">Further discussion of AR/VR camera rigs can be found in [Unity's documentation](https://docs.unity3d.com/Packages/com.unity.xr.legacyinputhelpers@2.1/manual/index.html#xr-rig-explanation) and elsewhere.</span></span>

1. <span data-ttu-id="08b7f-193">按下 **空格鍵**，然後 **按下 [播放**] 和 [測試輸出]。</span><span class="sxs-lookup"><span data-stu-id="08b7f-193">**Press Play** and test out hand simulation by pressing the **spacebar**.</span></span> <span data-ttu-id="08b7f-194">您可以按下 **CTRL + H 鍵** 來開啟鍵盤快速鍵參考。</span><span class="sxs-lookup"><span data-stu-id="08b7f-194">You can open the keyboard shorcut reference by pressing **CTRL+H key**.</span></span>

<span data-ttu-id="08b7f-195">您現在可以開始建立及部署到裝置！</span><span class="sxs-lookup"><span data-stu-id="08b7f-195">You are now ready to build and deploy to device!</span></span> <span data-ttu-id="08b7f-196">遵循 [組建和部署 MRTK](updates-deployment/BuildAndDeploy.md)中的步驟指示。</span><span class="sxs-lookup"><span data-stu-id="08b7f-196">Follow the steps instructions at [Build and Deploy MRTK](updates-deployment/BuildAndDeploy.md).</span></span>

## <a name="run-the-handinteractionexamples-scene-in-the-unity-editor"></a><span data-ttu-id="08b7f-197">在 Unity 編輯器中執行 HandInteractionExamples 場景</span><span class="sxs-lookup"><span data-stu-id="08b7f-197">Run the HandInteractionExamples scene in the Unity Editor</span></span>

<span data-ttu-id="08b7f-198">手形互動範例場景是體驗核心空間互動和 UX 控制項的絕佳位置。</span><span class="sxs-lookup"><span data-stu-id="08b7f-198">The Hand Interaction Examples scene is a great place to experience core spatial interactions and UX controls.</span></span>

<span data-ttu-id="08b7f-199">[![HandInteractionExample 場景](features/Images/MRTK_Examples.png)](features/example-scenes/HandInteractionExamples.md)</span><span class="sxs-lookup"><span data-stu-id="08b7f-199">[![HandInteractionExample scene](features/Images/MRTK_Examples.png)](features/example-scenes/HandInteractionExamples.md)</span></span>

<span data-ttu-id="08b7f-200">若要試用場景，請執行下列步驟。</span><span class="sxs-lookup"><span data-stu-id="08b7f-200">To try the scene, do the following steps.</span></span>

1. <span data-ttu-id="08b7f-201">請務必將 **MixedRealityToolkit unitypackage** 套件匯入您的專案中。</span><span class="sxs-lookup"><span data-stu-id="08b7f-201">Make sure to import **Microsoft.MixedRealityToolkit.Unity.Examples.unitypackage** package into your project.</span></span>

1. <span data-ttu-id="08b7f-202">開啟下方的 **HandInteractionExamples** 場景 `Assets/MRTK/Examples/Demos/HandTracking/Scenes/HandInteractionExamples`</span><span class="sxs-lookup"><span data-stu-id="08b7f-202">Open the **HandInteractionExamples** scene under `Assets/MRTK/Examples/Demos/HandTracking/Scenes/HandInteractionExamples`</span></span>

1. <span data-ttu-id="08b7f-203">您可能會收到提示，要求您匯入 "TMP Essentials"。</span><span class="sxs-lookup"><span data-stu-id="08b7f-203">You may get a prompt asking you to import "TMP Essentials".</span></span>

    <span data-ttu-id="08b7f-204"><img src = "功能/影像/開始使用/MRTK_GettingStarted_TMPro.png" width = "600" alt = "開始使用 Tmp" ></span><span class="sxs-lookup"><span data-stu-id="08b7f-204"><img src="features/images/getting-started/MRTK_GettingStarted_TMPro.png" width="600"alt="Getting Started Tmp"></span></span>

    <span data-ttu-id="08b7f-205">如果您收到這類提示，請選取 [匯入 TMP essentials] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="08b7f-205">If you get such a prompt, select the "Import TMP essentials" button.</span></span> <span data-ttu-id="08b7f-206">"TMP Essentials" 指的是文字網格 Pro 外掛程式，其中一些 MRTK 範例會用來改善文字轉譯。</span><span class="sxs-lookup"><span data-stu-id="08b7f-206">"TMP Essentials" refers to Text Mesh Pro plugin, which some of the MRTK examples use for improved text rendering.</span></span> <span data-ttu-id="08b7f-207"> (如需詳細資訊，請參閱 [Unity 中的文字](https://docs.microsoft.com/windows/mixed-reality/text-in-unity)) </span><span class="sxs-lookup"><span data-stu-id="08b7f-207">(See [Text in Unity](https://docs.microsoft.com/windows/mixed-reality/text-in-unity) for more detailed information)</span></span>

1. <span data-ttu-id="08b7f-208">關閉 TMP 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="08b7f-208">Close the TMP dialog.</span></span> <span data-ttu-id="08b7f-209">之後，您需要重載場景。</span><span class="sxs-lookup"><span data-stu-id="08b7f-209">After this you need to reload the scene.</span></span> <span data-ttu-id="08b7f-210">您可以按兩下 [專案] 索引標籤中的場景來完成這項作業。</span><span class="sxs-lookup"><span data-stu-id="08b7f-210">You can do this by double-clicking the scene in the Project tab.</span></span>

1. <span data-ttu-id="08b7f-211">取消核取 (Unity 2019 或更高版本) 或使用場景視圖的 [Gizmos] 索引標籤下的滑杆 (Unity 2018) 來縮減3d 圖示的大小，以減少場景雜亂</span><span class="sxs-lookup"><span data-stu-id="08b7f-211">Uncheck (Unity 2019 or higher) or shrink the size of the 3d icons using the slider (Unity 2018) under the Gizmos tab in the Scene view to reduce scene clutter</span></span>

     ![Gizmos](https://user-images.githubusercontent.com/13754172/80819866-a8aed800-8b8a-11ea-8d7b-a3822fdfc907.png)

1. <span data-ttu-id="08b7f-213">按下 [播放] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="08b7f-213">Press the Play button.</span></span>

## <a name="using-the-in-editor-hand-input-simulation-to-test-a-scene"></a><span data-ttu-id="08b7f-214">使用編輯器內的手寫輸入模擬來測試場景</span><span class="sxs-lookup"><span data-stu-id="08b7f-214">Using the in-editor hand input simulation to test a scene</span></span>

<span data-ttu-id="08b7f-215">編輯器內輸入模擬可讓您測試虛擬物件行為（例如 [，控制器 (，例如手、運動控制器) ](features/input-simulation/InputSimulationService.md#controller-simulation) 或 [眼睛](features/eye-tracking/EyeTracking_BasicSetup.md#simulating-eye-tracking-in-the-unity-editor)）。</span><span class="sxs-lookup"><span data-stu-id="08b7f-215">The in-editor input simulation allows you to test virtual object behavior given a specific type of input such as [controllers (i.e. hands, motion controllers)](features/input-simulation/InputSimulationService.md#controller-simulation) or [eyes](features/eye-tracking/EyeTracking_BasicSetup.md#simulating-eye-tracking-in-the-unity-editor).</span></span>

<span data-ttu-id="08b7f-216">**您可以按下 CTRL + H 鍵來開啟鍵盤快速鍵參考。**</span><span class="sxs-lookup"><span data-stu-id="08b7f-216">**You can open the keyboard shorcut reference by pressing CTRL+H key.**</span></span>

<span data-ttu-id="08b7f-217">如何在場景中四處移動：</span><span class="sxs-lookup"><span data-stu-id="08b7f-217">How to move around in the scene:</span></span>

* <span data-ttu-id="08b7f-218">使用 **W/A/S/D** 鍵，將觀景窗向前/向左/向後/向右移動。</span><span class="sxs-lookup"><span data-stu-id="08b7f-218">Use **W/A/S/D** keys to move the camera forward/left/back/right.</span></span>
* <span data-ttu-id="08b7f-219">使用 **Q/E** 鍵，以垂直方式移動觀景窗。</span><span class="sxs-lookup"><span data-stu-id="08b7f-219">Use **Q/E** to move the camera vertically.</span></span>
* <span data-ttu-id="08b7f-220">長按 **滑鼠右鍵** 以旋轉觀景窗。</span><span class="sxs-lookup"><span data-stu-id="08b7f-220">Press and hold the **right mouse button** to rotate the camera.</span></span>

<span data-ttu-id="08b7f-221">如何模擬手部輸入：</span><span class="sxs-lookup"><span data-stu-id="08b7f-221">How to simulate hand input:</span></span>

* <span data-ttu-id="08b7f-222">按住 **空格鍵** 以啟用右手邊。</span><span class="sxs-lookup"><span data-stu-id="08b7f-222">Press and hold the **spacebar** to enable the right hand.</span></span>
* <span data-ttu-id="08b7f-223">按住空格鍵時，移動滑鼠來移動右手。</span><span class="sxs-lookup"><span data-stu-id="08b7f-223">While holding the space bar, move your mouse to move the hand.</span></span>
* <span data-ttu-id="08b7f-224">使用 **滑鼠滾輪** 來調整手的深度。</span><span class="sxs-lookup"><span data-stu-id="08b7f-224">Use the mouse **scroll wheel** to adjust the depth of the hand.</span></span>
* <span data-ttu-id="08b7f-225">按一下 **滑鼠左鍵** 以模擬捏合手勢。</span><span class="sxs-lookup"><span data-stu-id="08b7f-225">Click the **left mouse button** to simulate pinch gesture.</span></span>
* <span data-ttu-id="08b7f-226">使用 **T/Y** 鍵，讓右手持續保持在檢視中。</span><span class="sxs-lookup"><span data-stu-id="08b7f-226">Use **T/Y** keys to make the hand persistent in the view.</span></span>
* <span data-ttu-id="08b7f-227">按住 **CTRL** 鍵，並移動滑鼠以旋轉右手。</span><span class="sxs-lookup"><span data-stu-id="08b7f-227">Hold **CTRL** key and move the mouse to rotate the hand.</span></span>

<span data-ttu-id="08b7f-228">盡情探索場景！</span><span class="sxs-lookup"><span data-stu-id="08b7f-228">Have fun exploring the scene!</span></span> <span data-ttu-id="08b7f-229">您可以深入瞭解 [《手形互動範例指南》中](features/example-scenes/HandInteractionExamples.md)的 UI 控制項。</span><span class="sxs-lookup"><span data-stu-id="08b7f-229">You can learn more about the UI controls [in the hand interaction examples guide](features/example-scenes/HandInteractionExamples.md).</span></span> <span data-ttu-id="08b7f-230">此外，請閱讀 [輸入模擬](features/input-simulation/InputSimulationService.md) 檔，以深入瞭解 MRTK 中的編輯器內輸入模擬。</span><span class="sxs-lookup"><span data-stu-id="08b7f-230">Also, read through [input simulation docs](features/input-simulation/InputSimulationService.md) to learn more about in-editor hand input simulation in MRTK.</span></span>

<span data-ttu-id="08b7f-231">恭喜，您剛使用了第一個 MRTK 場景。</span><span class="sxs-lookup"><span data-stu-id="08b7f-231">Congratulations, you just used your first MRTK scene.</span></span> <span data-ttu-id="08b7f-232">現在就開始建立您自己的經驗 .。。</span><span class="sxs-lookup"><span data-stu-id="08b7f-232">Now onto creating your own experiences...</span></span>

## <a name="getting-started-tutorials"></a><span data-ttu-id="08b7f-233">入門教學課程</span><span class="sxs-lookup"><span data-stu-id="08b7f-233">Getting started tutorials</span></span>

<span data-ttu-id="08b7f-234">如果您不熟悉 MRTK 或 MR 開發，我們建議您查看使用 MRTK v2 的使用者 [入門教學](https://docs.microsoft.com/windows/mixed-reality/develop/unity/tutorials/mr-learning-base-01) 課程。</span><span class="sxs-lookup"><span data-stu-id="08b7f-234">If you are new to MRTK, or MR development, we recommend you check out the [Getting started tutorials](https://docs.microsoft.com/windows/mixed-reality/develop/unity/tutorials/mr-learning-base-01) which uses MRTK v2.</span></span>

## <a name="learn-about-the-core-building-blocks-of-mrtk"></a><span data-ttu-id="08b7f-235">瞭解 MRTK 的核心構成要素</span><span class="sxs-lookup"><span data-stu-id="08b7f-235">Learn about the core building blocks of MRTK</span></span>

* <span data-ttu-id="08b7f-236">請參閱 [MRTK 101：如何使用混合現實工具組 Unity 進行基本互動 (HoloLens 2、HoloLens、Windows Mixed Reality、OPEN VR) ， ](https://docs.microsoft.com/windows/mixed-reality/mrtk-101) 以瞭解核心建立區塊。</span><span class="sxs-lookup"><span data-stu-id="08b7f-236">Check out [MRTK 101: How to use Mixed Reality Toolkit Unity for Basic Interactions (HoloLens 2, HoloLens, Windows Mixed Reality, Open VR)](https://docs.microsoft.com/windows/mixed-reality/mrtk-101) to learn about core building blocks.</span></span>

* <span data-ttu-id="08b7f-237">查看 MRTK 的 MR Dev Day 講座影片 [簡介](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Intro-to-MRTK-Unity)</span><span class="sxs-lookup"><span data-stu-id="08b7f-237">Check out MR Dev Day 2020's session video [Introduction to MRTK](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Intro-to-MRTK-Unity)</span></span>

* <span data-ttu-id="08b7f-238">請參閱 MR Dev Day 的研討會影片[MRTK 的 UX 建築](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/MRTKs-UX-Building-Blocks)組塊</span><span class="sxs-lookup"><span data-stu-id="08b7f-238">Check out MR Dev Day 2020's session video [MRTK's UX Building Blocks](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/MRTKs-UX-Building-Blocks)</span></span>

## <a name="next-steps"></a><span data-ttu-id="08b7f-239">下一步</span><span class="sxs-lookup"><span data-stu-id="08b7f-239">Next steps</span></span>

<span data-ttu-id="08b7f-240">以下是一些建議的後續步驟：</span><span class="sxs-lookup"><span data-stu-id="08b7f-240">Here are some suggested next steps:</span></span>

* <span data-ttu-id="08b7f-241">查看 [MRTK 101：如何使用混合現實工具組 Unity 進行基本互動](https://docs.microsoft.com/windows/mixed-reality/mrtk-101) ，以瞭解如何達成常見的空間互動，例如抓取、移動、調整和旋轉。</span><span class="sxs-lookup"><span data-stu-id="08b7f-241">Check out [MRTK 101: How to use Mixed Reality Toolkit Unity for Basic Interactions](https://docs.microsoft.com/windows/mixed-reality/mrtk-101) to learn about how to achieve common spatial interactions such as grab, move, scale, and rotate.</span></span>
* <span data-ttu-id="08b7f-242">深入瞭解 MRTK 中的 UX 控制項可在 [UI 和互動建立區塊](features/experimental/README.md#ux-building-blocks)中使用。</span><span class="sxs-lookup"><span data-stu-id="08b7f-242">Learn about the UX controls available in MRTK in [UI and interaction building blocks](features/experimental/README.md#ux-building-blocks).</span></span>
* <span data-ttu-id="08b7f-243">嘗試 [MRTK 範例中樞](features/example-scenes/ExampleHub.md) 以及 [設計](https://www.microsoft.com/p/designing-holograms/9nxwnjklrzwd) 可從 HoloLens 2 的 Microsoft Store 應用程式下載的全像影像應用程式。</span><span class="sxs-lookup"><span data-stu-id="08b7f-243">Try [MRTK Examples Hub](features/example-scenes/ExampleHub.md) and [Designing Holograms](https://www.microsoft.com/p/designing-holograms/9nxwnjklrzwd) app which can be downloaded from Microsoft Store app in your HoloLens 2.</span></span>

* <span data-ttu-id="08b7f-244">瞭解如何使用 [混合式事實設定指南](configuration/MixedRealityConfigurationGuide.md)中的 MRTK 設定設定檔。</span><span class="sxs-lookup"><span data-stu-id="08b7f-244">Learn how to work with the MRTK Configuration profile in the [mixed reality configuration guide](configuration/MixedRealityConfigurationGuide.md).</span></span>
* <span data-ttu-id="08b7f-245">瞭解 [MRTK 的架構](architecture/Overview.md)</span><span class="sxs-lookup"><span data-stu-id="08b7f-245">Learn about the [MRTK's Architecture](architecture/Overview.md)</span></span>
* <span data-ttu-id="08b7f-246">瞭解 [MRTK 的輸入系統](features/input/Overview.md)</span><span class="sxs-lookup"><span data-stu-id="08b7f-246">Learn about the [MRTK's Input System](features/input/Overview.md)</span></span>
* <span data-ttu-id="08b7f-247">瞭解可加強您的混合現實設計和開發的 [MRTK 工具](features/experimental/README.md#tools) 。</span><span class="sxs-lookup"><span data-stu-id="08b7f-247">Learn about the [MRTK's Tools](features/experimental/README.md#tools) that will empower your mixed reality design and development.</span></span>
* <span data-ttu-id="08b7f-248">請參閱 [輸入模擬指南](features/input-simulation/InputSimulationService.md) ，以瞭解如何在編輯器中模擬手動輸入。</span><span class="sxs-lookup"><span data-stu-id="08b7f-248">Read through [input simulation guide](features/input-simulation/InputSimulationService.md) to learn how to simulate hand input in editor.</span></span>

## <a name="getting-help"></a><span data-ttu-id="08b7f-249">取得說明</span><span class="sxs-lookup"><span data-stu-id="08b7f-249">Getting help</span></span>

<span data-ttu-id="08b7f-250">如果您遇到 MRTK 所造成的問題，或是有關于如何執行某些問題的問題，有一些資源可以提供協助：</span><span class="sxs-lookup"><span data-stu-id="08b7f-250">If you run into issues caused by MRTK or otherwise have questions about how to do something, there are a few resources that can help:</span></span>

* <span data-ttu-id="08b7f-251">針對錯誤報表，請在 GitHub 存放庫上提出 [問題](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/new/choose) 。</span><span class="sxs-lookup"><span data-stu-id="08b7f-251">For bug reports, please [file an issue](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/new/choose) on the GitHub repo.</span></span>
* <span data-ttu-id="08b7f-252">如有任何問題，請在 [StackOverflow](https://stackoverflow.com/questions/tagged/mrtk) 或「 [混合現實」工具組頻道](https://holodevelopers.slack.com/messages/C2H4HT858) 的時差上聯繫。</span><span class="sxs-lookup"><span data-stu-id="08b7f-252">For questions, please reach out on either [StackOverflow](https://stackoverflow.com/questions/tagged/mrtk) or the [mixed-reality-toolkit channel](https://holodevelopers.slack.com/messages/C2H4HT858) on Slack.</span></span> <span data-ttu-id="08b7f-253">您可以透過 [自動邀請寄件者](https://holodevelopersslack.azurewebsites.net/)來加入「時差」群。</span><span class="sxs-lookup"><span data-stu-id="08b7f-253">You can join the Slack community via the [automatic invitation sender](https://holodevelopersslack.azurewebsites.net/).</span></span>

## <a name="upgrading-from-the-holotoolkit-htkmrtk-v1"></a><span data-ttu-id="08b7f-254">從 HoloToolkit (HTK/MRTK v1) 升級</span><span class="sxs-lookup"><span data-stu-id="08b7f-254">Upgrading from the HoloToolkit (HTK/MRTK v1)</span></span>

<span data-ttu-id="08b7f-255">由於重建架構的緣故，沒有從 HoloToolkit 到混合現實工具組 v2 的直接升級路徑。</span><span class="sxs-lookup"><span data-stu-id="08b7f-255">There is not a direct upgrade path from the HoloToolkit to Mixed Reality Toolkit v2 due to the rebuilt framework.</span></span> <span data-ttu-id="08b7f-256">不過，您可以將 MRTK 匯入您的 HoloToolkit 專案中，並遷移您的執行。</span><span class="sxs-lookup"><span data-stu-id="08b7f-256">However, it is possible to import the MRTK into your HoloToolkit project and migrate your implementation.</span></span> <span data-ttu-id="08b7f-257">如需詳細資訊，請參閱 [HoloToolkit 至混合現實工具組移植指南](updates-deployment/HTKToMRTKPortingGuide.md)</span><span class="sxs-lookup"><span data-stu-id="08b7f-257">For more information, see the [HoloToolkit to Mixed Reality Toolkit Porting Guide](updates-deployment/HTKToMRTKPortingGuide.md)</span></span>

## <a name="getting-started-with-unitys-xr-sdk"></a><span data-ttu-id="08b7f-258">開始使用 Unity 的 XR SDK</span><span class="sxs-lookup"><span data-stu-id="08b7f-258">Getting started with Unity's XR SDK</span></span>

<span data-ttu-id="08b7f-259">您可以在我們的 [XR SDK 快速入門手冊](configuration/GettingStartedWithMRTKAndXRSDK.md)中找到完整的指示和資訊。</span><span class="sxs-lookup"><span data-stu-id="08b7f-259">Complete instructions and information can be found in our [XR SDK getting started guide](configuration/GettingStartedWithMRTKAndXRSDK.md).</span></span>
