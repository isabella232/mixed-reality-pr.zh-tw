---
title: 安裝指南
description: 在新專案中安裝 MRTK-Unity 的指南。
author: hferrone
ms.author: v-hferrone
ms.date: 09/9/2020
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: d87a19862dba9a50c963421fb9378f9befbe30c9
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104687478"
---
# <a name="installation-guide"></a><span data-ttu-id="be4df-104">安裝指南</span><span class="sxs-lookup"><span data-stu-id="be4df-104">Installation guide</span></span>

> [!CAUTION]
> <span data-ttu-id="be4df-105">如果您不熟悉 Unity 中的 MRTK 或混合現實開發，我們建議您從 [unity 開發旅程](https://docs.microsoft.com/windows/mixed-reality/unity-development-overview?tabs=mrtk%2Chl2)的開端開始著手。</span><span class="sxs-lookup"><span data-stu-id="be4df-105">If you're new to MRTK or Mixed Reality development in Unity, we recommend you start at the beginning of our [Unity development journey](https://docs.microsoft.com/windows/mixed-reality/unity-development-overview?tabs=mrtk%2Chl2).</span></span> <span data-ttu-id="be4df-106">Unity 開發旅程是建議的 **MRTK 起始點**，特別是為了引導您完成安裝、核心概念，以及 Unity 中的 MRTK 使用。</span><span class="sxs-lookup"><span data-stu-id="be4df-106">The Unity development journey is the **recommended starting point for MRTK**, specifically created to walk you through the installation, core concepts, and usage of MRTK in Unity.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="be4df-107">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="be4df-107">Prerequisites</span></span>

<span data-ttu-id="be4df-108">若要開始使用 Mixed Reality 工具組，您將需要：</span><span class="sxs-lookup"><span data-stu-id="be4df-108">To get started with the Mixed Reality Toolkit, you will need:</span></span>

* [<span data-ttu-id="be4df-109">Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="be4df-109">Visual Studio 2019</span></span>](https://visualstudio.microsoft.com/downloads/)
* [<span data-ttu-id="be4df-110">Unity 2018.4 或 Unity 2019。4</span><span class="sxs-lookup"><span data-stu-id="be4df-110">Unity 2018.4 or Unity 2019.4</span></span>](https://unity3d.com/get-unity/download/archive)

  <span data-ttu-id="be4df-111">MRTK 支援 Unity 2018 上的 IL2CPP 和 .NET 腳本後端。</span><span class="sxs-lookup"><span data-stu-id="be4df-111">MRTK supports both IL2CPP and .NET scripting backends on Unity 2018.</span></span>  
  <span data-ttu-id="be4df-112">**強烈建議您從 MRTK 2.5 unity 2018.4.13 f1 或更新版本**，以供使用 Unity 2018 的客戶使用。</span><span class="sxs-lookup"><span data-stu-id="be4df-112">Starting from MRTK 2.5 **Unity 2018.4.13f1 or later is strongly recommended** for customers using Unity 2018.</span></span> <span data-ttu-id="be4df-113">仍支援舊版 Unity 2018.4，但現在需要額外的步驟來設定和升級至 Unity 2019。</span><span class="sxs-lookup"><span data-stu-id="be4df-113">Earlier versions of Unity 2018.4 are still supported but now require extra steps to set up and to upgrade to Unity 2019.</span></span>

* <span data-ttu-id="be4df-114">[Windows SDK 18362 +](https://developer.microsoft.com/windows/downloads/windows-10-sdk)。</span><span class="sxs-lookup"><span data-stu-id="be4df-114">[Windows SDK 18362+](https://developer.microsoft.com/windows/downloads/windows-10-sdk).</span></span>

  <span data-ttu-id="be4df-115">如果您要建立適用于 WMR、HoloLens 1 或 HoloLens 2 的 UWP 應用程式，則這是必要的。</span><span class="sxs-lookup"><span data-stu-id="be4df-115">This is necessary if you are building a UWP app for WMR, HoloLens 1, or HoloLens 2.</span></span> <span data-ttu-id="be4df-116">這在建立 OpenVR 時並不是必要的。</span><span class="sxs-lookup"><span data-stu-id="be4df-116">This is not necessary when building for OpenVR.</span></span>

## <a name="add-mrtk-to-your-unity-project"></a><span data-ttu-id="be4df-117">將 MRTK 新增至您的 Unity 專案</span><span class="sxs-lookup"><span data-stu-id="be4df-117">Add MRTK to your Unity project</span></span>

> [!Note]
> <span data-ttu-id="be4df-118">Unity 2019.4 和更新版本的使用者可以使用 Unity 封裝管理員匯入 MRTK。</span><span class="sxs-lookup"><span data-stu-id="be4df-118">Users of Unity 2019.4 and newer, can use the Unity Package Manager to import MRTK.</span></span> <span data-ttu-id="be4df-119">如需詳細資訊，請參閱 [使用 Unity 封裝管理員](configuration/usingupm.md) 。</span><span class="sxs-lookup"><span data-stu-id="be4df-119">Please see [Using the Unity Package Manager](configuration/usingupm.md) for more information.</span></span>

### <a name="required"></a><span data-ttu-id="be4df-120">必要</span><span class="sxs-lookup"><span data-stu-id="be4df-120">Required</span></span>

1. [<span data-ttu-id="be4df-121">取得最新的 MRTK Unity 套件</span><span class="sxs-lookup"><span data-stu-id="be4df-121">Get the latest MRTK Unity packages</span></span>](#get-the-latest-mrtk-unity-packages)
1. [<span data-ttu-id="be4df-122">將 MRTK 套件匯入到您的 Unity 專案</span><span class="sxs-lookup"><span data-stu-id="be4df-122">Import MRTK packages into your Unity project</span></span>](#import-mrtk-packages-into-your-unity-project)
1. [<span data-ttu-id="be4df-123">將您的 Unity 專案切換到目標平台</span><span class="sxs-lookup"><span data-stu-id="be4df-123">Switch your Unity project to the target platform</span></span>](#switch-your-unity-project-to-the-target-platform)
1. [<span data-ttu-id="be4df-124">將 MRTK 新增至新場景或新專案</span><span class="sxs-lookup"><span data-stu-id="be4df-124">Add MRTK to a new scene or new project</span></span>](#add-mrtk-to-a-new-scene-or-new-project)

### <a name="optional"></a><span data-ttu-id="be4df-125">選擇性</span><span class="sxs-lookup"><span data-stu-id="be4df-125">Optional</span></span>

* [<span data-ttu-id="be4df-126">入門教學課程</span><span class="sxs-lookup"><span data-stu-id="be4df-126">Getting started tutorials</span></span>](#getting-started-tutorials)
* <span data-ttu-id="be4df-127">[XR SDK 快速入門手冊 (Unity 2019.3 或更新版本) ](configuration/GettingStartedWithMRTKAndXRSDK.md)。</span><span class="sxs-lookup"><span data-stu-id="be4df-127">[XR SDK getting started guide (Unity 2019.3 or later)](configuration/GettingStartedWithMRTKAndXRSDK.md).</span></span>
* [<span data-ttu-id="be4df-128">瞭解 MRTK 的核心構成要素</span><span class="sxs-lookup"><span data-stu-id="be4df-128">Learn about the core building blocks of MRTK</span></span>](#learn-about-the-core-building-blocks-of-mrtk)
* [<span data-ttu-id="be4df-129">在 Unity 編輯器中執行 HandInteractionExamples 場景</span><span class="sxs-lookup"><span data-stu-id="be4df-129">Run the HandInteractionExamples scene in the Unity Editor</span></span>](#run-the-handinteractionexamples-scene-in-the-unity-editor)

### <a name="get-the-latest-mrtk-unity-packages"></a><span data-ttu-id="be4df-130">取得最新的 MRTK Unity 套件</span><span class="sxs-lookup"><span data-stu-id="be4df-130">Get the latest MRTK Unity packages</span></span>

1. <span data-ttu-id="be4df-131">移至 [ <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity/releases" target="_blank">MRTK 發行] 頁面</a>。</span><span class="sxs-lookup"><span data-stu-id="be4df-131">Go to the <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity/releases" target="_blank">MRTK release page</a>.</span></span>
1. <span data-ttu-id="be4df-132">在 [資產] 底下，下載：</span><span class="sxs-lookup"><span data-stu-id="be4df-132">Under Assets, download:</span></span>
    * <span data-ttu-id="be4df-133">**Microsoft.MixedRealityToolkit.Unity.Foundation.unitypackage**</span><span class="sxs-lookup"><span data-stu-id="be4df-133">**Microsoft.MixedRealityToolkit.Unity.Foundation.unitypackage**</span></span>
    * <span data-ttu-id="be4df-134"> (**_選用_**) MixedRealityToolkit。 unitypackage</span><span class="sxs-lookup"><span data-stu-id="be4df-134">(**_Optional_**) Microsoft.MixedRealityToolkit.Unity.Extensions.unitypackage</span></span>
    * <span data-ttu-id="be4df-135"> (**_選擇性_** 的) MixedRealityToolkit，例如 unitypackage</span><span class="sxs-lookup"><span data-stu-id="be4df-135">(**_Optional_**) Microsoft.MixedRealityToolkit.Unity.Examples.unitypackage</span></span>
    * <span data-ttu-id="be4df-136"> (**_選擇性_**) MixedRealityToolkit TestUtilities. unitypackage</span><span class="sxs-lookup"><span data-stu-id="be4df-136">(**_Optional_**) Microsoft.MixedRealityToolkit.Unity.TestUtilities.unitypackage</span></span>
    * <span data-ttu-id="be4df-137"> (**_版本到版本的升級所需，否則請_**) unitypackage</span><span class="sxs-lookup"><span data-stu-id="be4df-137">(**_Required for version-to-version upgrades, Optional otherwise_**) Microsoft.MixedRealityToolkit.Unity.Tools.unitypackage</span></span>

<span data-ttu-id="be4df-138">如需封裝及其內容的詳細資訊，請參閱 [MRTK 套件](packages-releases/MRTK_Packages.md)。</span><span class="sxs-lookup"><span data-stu-id="be4df-138">For details on the packages and their contents, please see [MRTK Packages](packages-releases/MRTK_Packages.md).</span></span>

### <a name="import-mrtk-packages-into-your-unity-project"></a><span data-ttu-id="be4df-139">將 MRTK 套件匯入到您的 Unity 專案</span><span class="sxs-lookup"><span data-stu-id="be4df-139">Import MRTK packages into your Unity project</span></span>

1. <span data-ttu-id="be4df-140">建立新的 Unity 專案，或開啟現有的專案。</span><span class="sxs-lookup"><span data-stu-id="be4df-140">Create a new Unity project, or open an existing project.</span></span> <span data-ttu-id="be4df-141">建立專案時，請務必選取 [3D] 作為範本類型。</span><span class="sxs-lookup"><span data-stu-id="be4df-141">When creating a project, make sure to select "3D" as the template type.</span></span>
1. <span data-ttu-id="be4df-142">匯入您下載的 **MixedRealityToolkit** ，方法是前往 [資產-> 匯入封裝-> 自訂套件]，選取 unitypackage 檔案，確定已核取所有要匯入的專案，然後選取 [匯入]。</span><span class="sxs-lookup"><span data-stu-id="be4df-142">Import the **Microsoft.MixedRealityToolkit.Unity.Foundation.unitypackage** you downloaded by going into "Asset -> Import Package -> Custom Package", select the .unitypackage file, ensure all items to import are checked, and then select "Import".</span></span>
1. <span data-ttu-id="be4df-143"> (**_選擇性_**) 匯入 **MixedRealityToolkit** ，遵循與基礎封裝相同的步驟。</span><span class="sxs-lookup"><span data-stu-id="be4df-143">(**_Optional_**) Import the **Microsoft.MixedRealityToolkit.Unity.Extensions.unitypackage** following the same steps as the foundation package.</span></span> <span data-ttu-id="be4df-144">擴充功能套件提供一組適用于 MRTK 的實用選擇性元件。</span><span class="sxs-lookup"><span data-stu-id="be4df-144">The extensions package provides a set of useful optional components for the MRTK.</span></span>
1. <span data-ttu-id="be4df-145"> (**_選擇性_**) 匯入 **MixedRealityToolkit** ，遵循與上述相同的步驟。</span><span class="sxs-lookup"><span data-stu-id="be4df-145">(**_Optional_**) Import the **Microsoft.MixedRealityToolkit.Unity.Examples.unitypackage** following the same steps as above.</span></span> <span data-ttu-id="be4df-146">範例套件是選擇性的，包含目前 MRTK 功能的實用示範場景。</span><span class="sxs-lookup"><span data-stu-id="be4df-146">The examples package is optional and contains useful demonstration scenes for current MRTK features.</span></span> <span data-ttu-id="be4df-147">**請注意，範例套件需要副檔名套件。**</span><span class="sxs-lookup"><span data-stu-id="be4df-147">**Note that the Examples package requires the Extensions package.**</span></span>
1. <span data-ttu-id="be4df-148">**_版本到版本升級需要 (，否則請_**) 匯入與基礎套件相同的步驟來匯入 **MixedRealityToolkit** 。</span><span class="sxs-lookup"><span data-stu-id="be4df-148">(**_Required for version-to-version upgrades, Optional otherwise_**) Import the **Microsoft.MixedRealityToolkit.Unity.Tools.unitypackage** following the same steps as the foundation package.</span></span> <span data-ttu-id="be4df-149">工具套件是選擇性的，並且包含可增強 MRTK 開發人員體驗的公用程式（例如 ExtensionServiceCreator）。</span><span class="sxs-lookup"><span data-stu-id="be4df-149">The tools package is optional and contains useful tools, such as the ExtensionServiceCreator, that enhance the MRTK developer experience.</span></span>

> [!Note]
> <span data-ttu-id="be4df-150">如果您使用 Unity 2018.4.12 f1 或更早版本，請注意主控台會出現編譯錯誤。</span><span class="sxs-lookup"><span data-stu-id="be4df-150">If you are using Unity 2018.4.12f1 or earlier, note you will experience compilation errors shown in the console.</span></span> <span data-ttu-id="be4df-151">移至 `Assets\MRTK\Providers\XRSDK\Microsoft.MixedReality.Toolkit.Providers.XRSDK.asmdef` [專案] 視窗中的，並移除偵測器中遺漏的參考。</span><span class="sxs-lookup"><span data-stu-id="be4df-151">Go to `Assets\MRTK\Providers\XRSDK\Microsoft.MixedReality.Toolkit.Providers.XRSDK.asmdef` in the project window and remove the missing reference in the inspector.</span></span> <span data-ttu-id="be4df-152">使用和重複執行這些步驟 `Assets\MRTK\Providers\Oculus\XRSDK\Microsoft.MixedReality.Toolkit.Providers.XRSDK.Oculus.asmdef` `Assets\MRTK\Providers\WindowsMixedReality\XRSDK\Microsoft.MixedReality.Toolkit.Providers.XRSDK.WMR.asmdef` 。</span><span class="sxs-lookup"><span data-stu-id="be4df-152">Repeat those steps with `Assets\MRTK\Providers\Oculus\XRSDK\Microsoft.MixedReality.Toolkit.Providers.XRSDK.Oculus.asmdef` and `Assets\MRTK\Providers\WindowsMixedReality\XRSDK\Microsoft.MixedReality.Toolkit.Providers.XRSDK.WMR.asmdef`.</span></span> <span data-ttu-id="be4df-153">請注意，您必須將這三個 asmdef 檔案取代為原始 (（亦即，升級至 Unity 2019 時未修改的) ），以還原變更。</span><span class="sxs-lookup"><span data-stu-id="be4df-153">Note you must revert the changes by replacing those three asmdef files with original (i.e. unmodified) ones when upgrading to Unity 2019.</span></span>  

> [!Note]
> <span data-ttu-id="be4df-154">Android 和 iOS 開發需要額外的套件安裝。</span><span class="sxs-lookup"><span data-stu-id="be4df-154">Android and iOS development require additional package installations.</span></span> <span data-ttu-id="be4df-155">如需詳細資訊，請參閱 [如何設定適用于 iOS 和 Android 的 MRTK](features/CrossPlatform/UsingARFoundation.md)。</span><span class="sxs-lookup"><span data-stu-id="be4df-155">For more information, see [How to configure MRTK for iOS and Android](features/CrossPlatform/UsingARFoundation.md).</span></span>
<span data-ttu-id="be4df-156">匯入基礎套件之後，您可能會看到類似下列的提示：</span><span class="sxs-lookup"><span data-stu-id="be4df-156">After importing the Foundation package, you may see a prompt similar to the following:</span></span>

![UnitySetupPrompt](features/Images/MRTK_UnitySetupPrompt.png)

<span data-ttu-id="be4df-158">MRTK 正在嘗試設定您的專案，藉由執行下列動作來建立混合的現實解決方案：</span><span class="sxs-lookup"><span data-stu-id="be4df-158">MRTK is attempting to set up your project for building Mixed Reality solutions by doing the following:</span></span>

* <span data-ttu-id="be4df-159">為您目前的平臺啟用 XR 設定， (啟用 [XR] 核取方塊) 。</span><span class="sxs-lookup"><span data-stu-id="be4df-159">Enable XR Settings for your current platform (enabling the XR checkbox).</span></span>
* <span data-ttu-id="be4df-160">使用原始檔控制) 來強制執行對 Unity 專案的文字序列化/可見的中繼檔案 (建議。</span><span class="sxs-lookup"><span data-stu-id="be4df-160">Force Text Serialization / Visible Meta files (recommended for Unity projects using source control).</span></span>

<span data-ttu-id="be4df-161">接受這些選項完全是選擇性的，但建議使用。</span><span class="sxs-lookup"><span data-stu-id="be4df-161">Accepting these options is completely optional, but recommended.</span></span>

<span data-ttu-id="be4df-162">有些 prefabs 和資產需要 TextMesh Pro，這表示您需要安裝 TextMesh Pro 套件，且專案中的資產 (視窗-> TextMeshPro > 匯入 TMP 基本資源) 。</span><span class="sxs-lookup"><span data-stu-id="be4df-162">Some prefabs and assets require TextMesh Pro, meaning you need the TextMesh Pro package installed and the assets in your project (Window -> TextMeshPro -> Import TMP Essential Resources).</span></span> <span data-ttu-id="be4df-163">匯 **入 TMP Essentials 資源之後，您必須重新開機 Unity 才能看到變更**。</span><span class="sxs-lookup"><span data-stu-id="be4df-163">**After you import TMP Essentials Resources, you need to restart Unity to see changes**.</span></span>

### <a name="switch-your-unity-project-to-the-target-platform"></a><span data-ttu-id="be4df-164">將您的 Unity 專案切換到目標平台</span><span class="sxs-lookup"><span data-stu-id="be4df-164">Switch your Unity project to the target platform</span></span>

<span data-ttu-id="be4df-165">匯入封裝後，下一個步驟是為應用程式選取正確的平臺。</span><span class="sxs-lookup"><span data-stu-id="be4df-165">With the packages imported, the next step is to select the correct platform for the application.</span></span>

<span data-ttu-id="be4df-166">若要建立 **HoloLens 應用程式**，請切換至通用 Windows 平臺：</span><span class="sxs-lookup"><span data-stu-id="be4df-166">To create a **HoloLens application**, switch to the Universal Windows Platform:</span></span>

1. <span data-ttu-id="be4df-167">開啟功能表： File > 組建設定</span><span class="sxs-lookup"><span data-stu-id="be4df-167">Open menu : File > Build Settings</span></span>
1. <span data-ttu-id="be4df-168">在 [**平臺**] 清單中選取 **通用 Windows 平臺**</span><span class="sxs-lookup"><span data-stu-id="be4df-168">Select **Universal Windows Platform** in the **Platform** list</span></span>
1. <span data-ttu-id="be4df-169">按一下 [ **切換平臺** ] 按鈕</span><span class="sxs-lookup"><span data-stu-id="be4df-169">Click the **Switch Platform** button</span></span>

![切換平台](features/Images/getting_started/SwitchPlatform.png)

>[!NOTE]
> <span data-ttu-id="be4df-171">混合現實工具組會在選取平臺時，提示您將建議的變更套用至專案。</span><span class="sxs-lookup"><span data-stu-id="be4df-171">The Mixed Reality Toolkit will prompt to apply recommended changes to the project when the platform is selected.</span></span> <span data-ttu-id="be4df-172">當平臺切換時，如有必要，將會檢查並提示適當的設定。</span><span class="sxs-lookup"><span data-stu-id="be4df-172">Whenever the platform is switched, the appropriate settings will be checked and prompted, if necessary.</span></span>

### <a name="add-mrtk-to-a-new-scene-or-new-project"></a><span data-ttu-id="be4df-173">將 MRTK 新增至新場景或新專案</span><span class="sxs-lookup"><span data-stu-id="be4df-173">Add MRTK to a new scene or new project</span></span>

1. <span data-ttu-id="be4df-174">建立新的 Unity 專案，或在您目前的專案中啟動新的場景。</span><span class="sxs-lookup"><span data-stu-id="be4df-174">Create a new Unity project, or start a new scene in your current project.</span></span>

1. <span data-ttu-id="be4df-175">請確定您已匯入 MRTK 套件， (我們建議使用基礎和範例，但不需要) 遵循 [上述步驟](#import-mrtk-packages-into-your-unity-project)。</span><span class="sxs-lookup"><span data-stu-id="be4df-175">Make sure you have imported the MRTK packages (we recommend both Foundation and Examples, though Examples is not required) following [the steps above](#import-mrtk-packages-into-your-unity-project).</span></span>

1. <span data-ttu-id="be4df-176">從功能表列中，選取 [混合現實工具組-> 新增至場景並設定]</span><span class="sxs-lookup"><span data-stu-id="be4df-176">From the menu bar, select Mixed Reality Toolkit -> Add to Scene and Configure</span></span>

    ![設定為場景](features/Images/MRTK_ConfigureScene.png)

    <span data-ttu-id="be4df-178">偵測器現在會顯示目前使用中的 MRTK 設定檔和設定檔選取下拉式清單，其中已預先選取預設設定檔。</span><span class="sxs-lookup"><span data-stu-id="be4df-178">The inspector will now show the currently active MRTK configuration profile and the profile selection dropdown, where the default profile is already preselected.</span></span>
    <span data-ttu-id="be4df-179">設定檔會設定 MRTK 核心元件的行為，並在 [設定檔](features/Profiles/Profiles.md) 文章中有更詳細的說明。</span><span class="sxs-lookup"><span data-stu-id="be4df-179">Profiles configure the behavior of MRTK core components and are described in more detail in the [profiles](features/Profiles/Profiles.md) article.</span></span>

    > [!NOTE]
    >
    > * <span data-ttu-id="be4df-180">如果您是在 Unity 2019.3 或更新版本中使用 Unity 的 XR SDK，您應該選擇「DefaultXRSDKConfigurationProfile」。</span><span class="sxs-lookup"><span data-stu-id="be4df-180">If you're using Unity's XR SDK in Unity 2019.3 or later, you should choose the "DefaultXRSDKConfigurationProfile".</span></span> <span data-ttu-id="be4df-181">此設定檔會在需要時，使用 MRTK 的 XR SDK 系統和提供者來設定。</span><span class="sxs-lookup"><span data-stu-id="be4df-181">This profile is set up with MRTK's XR SDK systems and providers, where needed.</span></span>  
    > * <span data-ttu-id="be4df-182">如果您是在 HoloLens 或 HoloLens 2 上開始使用，您應該改為選擇 [DefaultHoloLens1ConfigurationProfile] 或 [DefaultHoloLens2ConfigurationProfile]。</span><span class="sxs-lookup"><span data-stu-id="be4df-182">If you're getting started on the HoloLens or HoloLens 2, you should choose the "DefaultHoloLens1ConfigurationProfile" or DefaultHoloLens2ConfigurationProfile" instead.</span></span>  
    > * <span data-ttu-id="be4df-183">如需 DefaultMixedRealityToolkitConfigurationProfile 與 DefaultHoloLens2ConfigurationProfile 之間差異的詳細資訊，請參閱 [設定檔](Profiles/Profiles.md#hololens-2-profile) 。</span><span class="sxs-lookup"><span data-stu-id="be4df-183">See the [profiles](Profiles/Profiles.md#hololens-2-profile) for more information on the differences between DefaultMixedRealityToolkitConfigurationProfile and DefaultHoloLens2ConfigurationProfile.</span></span>

    <span data-ttu-id="be4df-184">然後，您會在場景階層中看到下列內容：</span><span class="sxs-lookup"><span data-stu-id="be4df-184">You will then see the following in your Scene hierarchy:</span></span>

    ![MRTK 場景設定](features/Images/MRTK_SceneSetup.png)

    <span data-ttu-id="be4df-186">其中包含下列內容：</span><span class="sxs-lookup"><span data-stu-id="be4df-186">Which contains the following:</span></span>

    * <span data-ttu-id="be4df-187">**混合現實工具** 組-工具組本身，提供整個架構的集中設定進入點。</span><span class="sxs-lookup"><span data-stu-id="be4df-187">**Mixed Reality Toolkit** - The toolkit itself, providing the central configuration entry point for the entire framework.</span></span>
    * <span data-ttu-id="be4df-188">**MixedRealityPlayspace** -耳機的父物件，可確保在場景中正確地管理耳機/控制器和其他所需的系統。</span><span class="sxs-lookup"><span data-stu-id="be4df-188">**MixedRealityPlayspace** - The parent object for the headset, which ensures the headset / controllers and other required systems are managed correctly in the scene.</span></span>
    * <span data-ttu-id="be4df-189">主要相機會以子系的形式移至 Playspace，讓 Playspace 能夠與 Sdk 一起管理攝影機。</span><span class="sxs-lookup"><span data-stu-id="be4df-189">The Main Camera is moved as a child to the Playspace - Which allows the playspace to manage the camera in conjunction with the SDKs.</span></span>

    >[!NOTE]
    > <span data-ttu-id="be4df-190">在場景中工作時， **請勿移動主要攝影機** 或 **MixedRealityPlayspace**。</span><span class="sxs-lookup"><span data-stu-id="be4df-190">While working in your scene, **DO NOT move the Main Camera** or the **MixedRealityPlayspace**.</span></span> <span data-ttu-id="be4df-191">這些是由作用中 SDK 和 MRTK 分別控制。</span><span class="sxs-lookup"><span data-stu-id="be4df-191">These are controlled by the active SDK and the MRTK respectively.</span></span> <span data-ttu-id="be4df-192">您對主要攝影機或 MixedRealityPlayspace 轉換所做的任何設定都將會被覆寫，而且在最糟的情況下，會產生未定義的行為。</span><span class="sxs-lookup"><span data-stu-id="be4df-192">Any settings you make to the Main Camera or MixedRealityPlayspace transforms will at best be overwritten, and at worst result in undefined behavior.</span></span>
    >
    > <span data-ttu-id="be4df-193">您可以將其他 GameObject 新增至場景，並將其設為 MixedRealityPlayspace 的父系，以移動整個 rig、攝影機和 Playspace。</span><span class="sxs-lookup"><span data-stu-id="be4df-193">The entire rig, Camera and Playspace, can be moved by adding another GameObject to the scene, and making it the parent of the MixedRealityPlayspace.</span></span> <span data-ttu-id="be4df-194">當移動該物件時，Playspace 和相機會以鬆散的方式追蹤，受限於使用中 SDK 和 MRTK 所做的額外本機轉換變更。</span><span class="sxs-lookup"><span data-stu-id="be4df-194">When that object is moved, the Playspace and Camera will follow loosely behind, subject to the additional local transform changes made by the active SDK and the MRTK.</span></span>
    >
    > <span data-ttu-id="be4df-195">另一個選項是將場景內容相對於相機移動，不過這在包含導覽網格、地形或物件等內容的先進案例中會變成問題。</span><span class="sxs-lookup"><span data-stu-id="be4df-195">Another option is to move the scene contents relative to the camera, although this can become problematic in advanced scenarios incorporating content such as Nav Meshes, terrains, or particle systems.</span></span>
    >
    > <span data-ttu-id="be4df-196">您可以在 [Unity 的檔](https://docs.unity3d.com/Packages/com.unity.xr.legacyinputhelpers@2.1/manual/index.html#xr-rig-explanation) 和其他地方找到 AR/VR 相機 rig 的進一步討論。</span><span class="sxs-lookup"><span data-stu-id="be4df-196">Further discussion of AR/VR camera rigs can be found in [Unity's documentation](https://docs.unity3d.com/Packages/com.unity.xr.legacyinputhelpers@2.1/manual/index.html#xr-rig-explanation) and elsewhere.</span></span>

1. <span data-ttu-id="be4df-197">按下 **空格鍵**，然後按下 [播放] 和 [測試輸出]。</span><span class="sxs-lookup"><span data-stu-id="be4df-197">Press Play and test out hand simulation by pressing the **spacebar**.</span></span>

<span data-ttu-id="be4df-198">您現在可以開始建立及部署到裝置！</span><span class="sxs-lookup"><span data-stu-id="be4df-198">You are now ready to build and deploy to device!</span></span> <span data-ttu-id="be4df-199">遵循 [組建和部署 MRTK](updates-deployment/BuildAndDeploy.md)中的步驟指示。</span><span class="sxs-lookup"><span data-stu-id="be4df-199">Follow the steps instructions at [Build and Deploy MRTK](updates-deployment/BuildAndDeploy.md).</span></span>

### <a name="getting-started-tutorials"></a><span data-ttu-id="be4df-200">入門教學課程</span><span class="sxs-lookup"><span data-stu-id="be4df-200">Getting started tutorials</span></span>

<span data-ttu-id="be4df-201">如果您不熟悉 MRTK 或 MR 開發，我們建議您查看使用 MRTK v2 的使用者 [入門教學](https://docs.microsoft.com/windows/mixed-reality/develop/unity/tutorials/mr-learning-base-01) 課程。</span><span class="sxs-lookup"><span data-stu-id="be4df-201">If you are new to MRTK, or MR development, we recommend you check out the [Getting started tutorials](https://docs.microsoft.com/windows/mixed-reality/develop/unity/tutorials/mr-learning-base-01) which uses MRTK v2.</span></span>

### <a name="learn-about-the-core-building-blocks-of-mrtk"></a><span data-ttu-id="be4df-202">瞭解 MRTK 的核心構成要素</span><span class="sxs-lookup"><span data-stu-id="be4df-202">Learn about the core building blocks of MRTK</span></span>

<span data-ttu-id="be4df-203">請參閱 [MRTK 101：如何使用混合現實工具組 Unity 進行基本互動 (HoloLens 2、HoloLens、Windows Mixed Reality、OPEN VR) ， ](https://docs.microsoft.com/windows/mixed-reality/mrtk-101) 以瞭解核心建立區塊。</span><span class="sxs-lookup"><span data-stu-id="be4df-203">Check out [MRTK 101: How to use Mixed Reality Toolkit Unity for Basic Interactions (HoloLens 2, HoloLens, Windows Mixed Reality, Open VR)](https://docs.microsoft.com/windows/mixed-reality/mrtk-101) to learn about core building blocks.</span></span>

### <a name="run-the-handinteractionexamples-scene-in-the-unity-editor"></a><span data-ttu-id="be4df-204">在 Unity 編輯器中執行 HandInteractionExamples 場景</span><span class="sxs-lookup"><span data-stu-id="be4df-204">Run the HandInteractionExamples scene in the Unity Editor</span></span>

<span data-ttu-id="be4df-205">[手形互動範例場景](features/README_HandInteractionExamples.md)文章是深入瞭解 MRTK 中 UX 控制項和互動的絕佳位置。</span><span class="sxs-lookup"><span data-stu-id="be4df-205">The [hand interaction examples scene](features/README_HandInteractionExamples.md) article is a great place to learn more about the UX controls and interactions in MRTK.</span></span>

<span data-ttu-id="be4df-206">[![HandInteractionExample 場景](features/Images/MRTK_Examples.png)](README_HandInteractionExamples.md)</span><span class="sxs-lookup"><span data-stu-id="be4df-206">[![HandInteractionExample scene](features/Images/MRTK_Examples.png)](README_HandInteractionExamples.md)</span></span>

<span data-ttu-id="be4df-207">若要嘗試進行「手動互動」場景，請執行下列步驟。</span><span class="sxs-lookup"><span data-stu-id="be4df-207">To try the hand interaction scene, do the following steps.</span></span>

1. <span data-ttu-id="be4df-208">開啟下方的 **HandInteractionExamples** 場景 `Assets/MRTK/Examples/Demos/HandTracking/Scenes/HandInteractionExamples`</span><span class="sxs-lookup"><span data-stu-id="be4df-208">Open the **HandInteractionExamples** scene under `Assets/MRTK/Examples/Demos/HandTracking/Scenes/HandInteractionExamples`</span></span>

1. <span data-ttu-id="be4df-209">您可能會收到提示，要求您匯入 "TMP Essentials"。</span><span class="sxs-lookup"><span data-stu-id="be4df-209">You may get a prompt asking you to import "TMP Essentials".</span></span>

    ![TMP Essentials](features/Images/getting_started/MRTK_GettingStarted_TMPro.png)

    <span data-ttu-id="be4df-211">如果您收到這類提示，請選取 [匯入 TMP essentials] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="be4df-211">If you get such a prompt, select the "Import TMP essentials" button.</span></span> <span data-ttu-id="be4df-212">"TMP Essentials" 指的是文字網格 Pro 外掛程式，其中一些 MRTK 範例會用來改善文字轉譯。</span><span class="sxs-lookup"><span data-stu-id="be4df-212">"TMP Essentials" refers to Text Mesh Pro plugin, which some of the MRTK examples use for improved text rendering.</span></span> <span data-ttu-id="be4df-213"> (如需詳細資訊，請參閱 [Unity 中的文字](https://docs.microsoft.com/windows/mixed-reality/text-in-unity)) </span><span class="sxs-lookup"><span data-stu-id="be4df-213">(See [Text in Unity](https://docs.microsoft.com/windows/mixed-reality/text-in-unity) for more detailed information)</span></span>

1. <span data-ttu-id="be4df-214">關閉 TMP 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="be4df-214">Close the TMP dialog.</span></span> <span data-ttu-id="be4df-215">之後，您需要重載場景。</span><span class="sxs-lookup"><span data-stu-id="be4df-215">After this you need to reload the scene.</span></span> <span data-ttu-id="be4df-216">您可以按兩下 [專案] 索引標籤中的場景來完成這項作業。</span><span class="sxs-lookup"><span data-stu-id="be4df-216">You can do this by double-clicking the scene in the Project tab.</span></span>

1. <span data-ttu-id="be4df-217">在場景視圖的 [Gizmos] 索引標籤底下，取消選取或壓縮3d 圖示的大小，以減少場景雜亂</span><span class="sxs-lookup"><span data-stu-id="be4df-217">Uncheck or shrink the size of the 3d icons under the Gizmos tab in the Scene view to reduce scene clutter</span></span>

     ![Gizmos](https://user-images.githubusercontent.com/13754172/80819866-a8aed800-8b8a-11ea-8d7b-a3822fdfc907.png)

1. <span data-ttu-id="be4df-219">按下 [播放] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="be4df-219">Press the Play button.</span></span>

## <a name="using-the-in-editor-hand-input-simulation-to-test-a-scene"></a><span data-ttu-id="be4df-220">使用編輯器內的手寫輸入模擬來測試場景</span><span class="sxs-lookup"><span data-stu-id="be4df-220">Using the in-editor hand input simulation to test a scene</span></span>

<span data-ttu-id="be4df-221">編輯器內輸入模擬可讓您測試虛擬物件行為（例如 [，控制器 (，例如手、運動控制器) ](features/InputSimulation/InputSimulationService.md#controller-simulation) 或 [眼睛](features/EyeTracking/EyeTracking_BasicSetup.md#simulating-eye-tracking-in-the-unity-editor)）。</span><span class="sxs-lookup"><span data-stu-id="be4df-221">The in-editor input simulation allows you to test virtual object behavior given a specific type of input such as [controllers (i.e. hands, motion controllers)](features/InputSimulation/InputSimulationService.md#controller-simulation) or [eyes](features/EyeTracking/EyeTracking_BasicSetup.md#simulating-eye-tracking-in-the-unity-editor).</span></span>

<span data-ttu-id="be4df-222">如何在場景中四處移動：</span><span class="sxs-lookup"><span data-stu-id="be4df-222">How to move around in the scene:</span></span>

* <span data-ttu-id="be4df-223">使用 **W/A/S/D** 鍵，將觀景窗向前/向左/向後/向右移動。</span><span class="sxs-lookup"><span data-stu-id="be4df-223">Use **W/A/S/D** keys to move the camera forward/left/back/right.</span></span>
* <span data-ttu-id="be4df-224">使用 **Q/E** 鍵，以垂直方式移動觀景窗。</span><span class="sxs-lookup"><span data-stu-id="be4df-224">Use **Q/E** to move the camera vertically.</span></span>
* <span data-ttu-id="be4df-225">長按 **滑鼠右鍵** 以旋轉觀景窗。</span><span class="sxs-lookup"><span data-stu-id="be4df-225">Press and hold the **right mouse button** to rotate the camera.</span></span>

<span data-ttu-id="be4df-226">如何模擬手部輸入：</span><span class="sxs-lookup"><span data-stu-id="be4df-226">How to simulate hand input:</span></span>

* <span data-ttu-id="be4df-227">按住 **空格鍵** 以啟用右手邊。</span><span class="sxs-lookup"><span data-stu-id="be4df-227">Press and hold the **spacebar** to enable the right hand.</span></span>
* <span data-ttu-id="be4df-228">按住空格鍵時，移動滑鼠來移動右手。</span><span class="sxs-lookup"><span data-stu-id="be4df-228">While holding the space bar, move your mouse to move the hand.</span></span>
* <span data-ttu-id="be4df-229">使用 **滑鼠滾輪** 來調整手的深度。</span><span class="sxs-lookup"><span data-stu-id="be4df-229">Use the mouse **scroll wheel** to adjust the depth of the hand.</span></span>
* <span data-ttu-id="be4df-230">按一下 **滑鼠左鍵** 以模擬捏合手勢。</span><span class="sxs-lookup"><span data-stu-id="be4df-230">Click the **left mouse button** to simulate pinch gesture.</span></span>
* <span data-ttu-id="be4df-231">使用 **T/Y** 鍵，讓右手持續保持在檢視中。</span><span class="sxs-lookup"><span data-stu-id="be4df-231">Use **T/Y** keys to make the hand persistent in the view.</span></span>
* <span data-ttu-id="be4df-232">按住 **CTRL** 鍵，並移動滑鼠以旋轉右手。</span><span class="sxs-lookup"><span data-stu-id="be4df-232">Hold **CTRL** key and move the mouse to rotate the hand.</span></span>

<span data-ttu-id="be4df-233">盡情探索場景！</span><span class="sxs-lookup"><span data-stu-id="be4df-233">Have fun exploring the scene!</span></span> <span data-ttu-id="be4df-234">您可以深入瞭解 [《手形互動範例指南》中](features/README_HandInteractionExamples.md)的 UI 控制項。</span><span class="sxs-lookup"><span data-stu-id="be4df-234">You can learn more about the UI controls [in the hand interaction examples guide](features/README_HandInteractionExamples.md).</span></span> <span data-ttu-id="be4df-235">此外，請閱讀 [輸入模擬](features/InputSimulation/InputSimulationService.md) 檔，以深入瞭解 MRTK 中的編輯器內輸入模擬。</span><span class="sxs-lookup"><span data-stu-id="be4df-235">Also, read through [input simulation docs](features/InputSimulation/InputSimulationService.md) to learn more about in-editor hand input simulation in MRTK.</span></span>

<span data-ttu-id="be4df-236">恭喜，您剛使用了第一個 MRTK 場景。</span><span class="sxs-lookup"><span data-stu-id="be4df-236">Congratulations, you just used your first MRTK scene.</span></span> <span data-ttu-id="be4df-237">現在就開始建立您自己的經驗 .。。</span><span class="sxs-lookup"><span data-stu-id="be4df-237">Now onto creating your own experiences...</span></span>

## <a name="next-steps"></a><span data-ttu-id="be4df-238">下一步</span><span class="sxs-lookup"><span data-stu-id="be4df-238">Next steps</span></span>

<span data-ttu-id="be4df-239">以下是一些建議的後續步驟：</span><span class="sxs-lookup"><span data-stu-id="be4df-239">Here are some suggested next steps:</span></span>

* <span data-ttu-id="be4df-240">查看 [MRTK 101：如何使用混合現實工具組 Unity 進行基本互動](https://docs.microsoft.com/windows/mixed-reality/mrtk-101) ，以瞭解如何達成常見的空間互動，例如抓取、移動、調整和旋轉。</span><span class="sxs-lookup"><span data-stu-id="be4df-240">Check out [MRTK 101: How to use Mixed Reality Toolkit Unity for Basic Interactions](https://docs.microsoft.com/windows/mixed-reality/mrtk-101) to learn about how to achieve common spatial interactions such as grab, move, scale, and rotate.</span></span>
* <span data-ttu-id="be4df-241">深入瞭解 MRTK 中的 UX 控制項可在 [UI 和互動建立區塊](features/Experimental/README.md#ux-building-blocks)中使用。</span><span class="sxs-lookup"><span data-stu-id="be4df-241">Learn about the UX controls available in MRTK in [UI and interaction building blocks](features/Experimental/README.md#ux-building-blocks).</span></span>
* <span data-ttu-id="be4df-242">試用 [MRTK 範例中樞](features/README_ExampleHub.md) (預先建立的應用程式套件已包含在 [發行] 頁面中，方便您) </span><span class="sxs-lookup"><span data-stu-id="be4df-242">Try [MRTK Examples Hub](features/README_ExampleHub.md) (pre-built app packages are included in the release page for your convenience)</span></span>
* <span data-ttu-id="be4df-243">瞭解如何使用 [混合式事實設定指南](out-of-scope/MixedRealityConfigurationGuide.md)中的 MRTK 設定設定檔。</span><span class="sxs-lookup"><span data-stu-id="be4df-243">Learn how to work with the MRTK Configuration profile in the [mixed reality configuration guide](out-of-scope/MixedRealityConfigurationGuide.md).</span></span>
* <span data-ttu-id="be4df-244">瞭解 [MRTK 的架構](Architecture/Overview.md)</span><span class="sxs-lookup"><span data-stu-id="be4df-244">Learn about the [MRTK's Architecture](Architecture/Overview.md)</span></span>
* <span data-ttu-id="be4df-245">瞭解 [MRTK 的輸入系統](features/Input/Overview.md)</span><span class="sxs-lookup"><span data-stu-id="be4df-245">Learn about the [MRTK's Input System](features/Input/Overview.md)</span></span>
* <span data-ttu-id="be4df-246">瞭解可加強您的混合現實設計和開發的 [MRTK 工具](features/Experimental/README.md#tools) 。</span><span class="sxs-lookup"><span data-stu-id="be4df-246">Learn about the [MRTK's Tools](features/Experimental/README.md#tools) that will empower your mixed reality design and development.</span></span>
* <span data-ttu-id="be4df-247">請參閱 [輸入模擬指南](features/InputSimulation/InputSimulationService.md) ，以瞭解如何在編輯器中模擬手動輸入。</span><span class="sxs-lookup"><span data-stu-id="be4df-247">Read through [input simulation guide](features/InputSimulation/InputSimulationService.md) to learn how to simulate hand input in editor.</span></span>

## <a name="getting-help"></a><span data-ttu-id="be4df-248">取得說明</span><span class="sxs-lookup"><span data-stu-id="be4df-248">Getting help</span></span>

<span data-ttu-id="be4df-249">如果您遇到 MRTK 所造成的問題，或是有關于如何執行某些問題的問題，有一些資源可以提供協助：</span><span class="sxs-lookup"><span data-stu-id="be4df-249">If you run into issues caused by MRTK or otherwise have questions about how to do something, there are a few resources that can help:</span></span>

* <span data-ttu-id="be4df-250">針對錯誤報表，請在 GitHub 存放庫上提出 [問題](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/new/choose) 。</span><span class="sxs-lookup"><span data-stu-id="be4df-250">For bug reports, please [file an issue](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/new/choose) on the GitHub repo.</span></span>
* <span data-ttu-id="be4df-251">如有任何問題，請在 [StackOverflow](https://stackoverflow.com/questions/tagged/mrtk) 或「 [混合現實」工具組頻道](https://holodevelopers.slack.com/messages/C2H4HT858) 的時差上聯繫。</span><span class="sxs-lookup"><span data-stu-id="be4df-251">For questions, please reach out on either [StackOverflow](https://stackoverflow.com/questions/tagged/mrtk) or the [mixed-reality-toolkit channel](https://holodevelopers.slack.com/messages/C2H4HT858) on Slack.</span></span> <span data-ttu-id="be4df-252">您可以透過 [自動邀請寄件者](https://holodevelopersslack.azurewebsites.net/)來加入「時差」群。</span><span class="sxs-lookup"><span data-stu-id="be4df-252">You can join the Slack community via the [automatic invitation sender](https://holodevelopersslack.azurewebsites.net/).</span></span>

## <a name="upgrading-from-the-holotoolkit-htkmrtk-v1"></a><span data-ttu-id="be4df-253">從 HoloToolkit (HTK/MRTK v1) 升級</span><span class="sxs-lookup"><span data-stu-id="be4df-253">Upgrading from the HoloToolkit (HTK/MRTK v1)</span></span>

<span data-ttu-id="be4df-254">由於重建架構的緣故，沒有從 HoloToolkit 到混合現實工具組 v2 的直接升級路徑。</span><span class="sxs-lookup"><span data-stu-id="be4df-254">There is not a direct upgrade path from the HoloToolkit to Mixed Reality Toolkit v2 due to the rebuilt framework.</span></span> <span data-ttu-id="be4df-255">不過，您可以將 MRTK 匯入您的 HoloToolkit 專案中，並遷移您的執行。</span><span class="sxs-lookup"><span data-stu-id="be4df-255">However, it is possible to import the MRTK into your HoloToolkit project and migrate your implementation.</span></span> <span data-ttu-id="be4df-256">如需詳細資訊，請參閱 [HoloToolkit 至混合現實工具組移植指南](updates-deployment/HTKToMRTKPortingGuide.md)</span><span class="sxs-lookup"><span data-stu-id="be4df-256">For more information, see the [HoloToolkit to Mixed Reality Toolkit Porting Guide](updates-deployment/HTKToMRTKPortingGuide.md)</span></span>

## <a name="getting-started-with-unitys-xr-sdk"></a><span data-ttu-id="be4df-257">開始使用 Unity 的 XR SDK</span><span class="sxs-lookup"><span data-stu-id="be4df-257">Getting started with Unity's XR SDK</span></span>

<span data-ttu-id="be4df-258">您可以在我們的 [XR SDK 快速入門手冊](configuration/GettingStartedWithMRTKAndXRSDK.md)中找到完整的指示和資訊。</span><span class="sxs-lookup"><span data-stu-id="be4df-258">Complete instructions and information can be found in our [XR SDK getting started guide](configuration/GettingStartedWithMRTKAndXRSDK.md).</span></span>
