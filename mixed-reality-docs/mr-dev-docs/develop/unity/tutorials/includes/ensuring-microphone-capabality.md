---
ms.openlocfilehash: 202d96435c437bc7630e82ea99a61f3c2a91c826
ms.sourcegitcommit: 8d386bf6c82ec9860815e873e1f2870ea410f40f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/31/2021
ms.locfileid: "106097662"
---
# <a name="unity-20192020--windows-xr-plugin"></a>[<span data-ttu-id="21cc0-101">Unity 2019/2020 + Windows XR 外掛程式</span><span class="sxs-lookup"><span data-stu-id="21cc0-101">Unity 2019/2020 + Windows XR Plugin</span></span>](#tab/winxr)

## <a name="ensuring-microphone-capability-and-adding-speech-input-data-provider"></a><span data-ttu-id="21cc0-102">確保麥克風功能和新增語音輸入資料提供者</span><span class="sxs-lookup"><span data-stu-id="21cc0-102">Ensuring Microphone capability and adding Speech Input data provider</span></span>

<span data-ttu-id="21cc0-103">在 Unity 功能表中，選取 [混合實境工具組] > [公用程式] > [設定 Unity 專案] 以開啟 [MRTK 專案設定程式] 視窗，然後在 [UWP 功能] 區段中，確認 [啟用麥克風功能] 呈現灰色：</span><span class="sxs-lookup"><span data-stu-id="21cc0-103">In the Unity menu, select Mixed Reality Toolkit > Utilities > **Configure Unity Project** to open the **MRTK Project Configurator** window, then in the **UWP Capabilities** section, verify that **Enable Microphone Capability** is greyed out:</span></span>

![啟用麥克風功能](../images/mr-learning-base/base-09-section1-step1-1.png)

> [!NOTE]
> <span data-ttu-id="21cc0-105">當您在本教學課程系列開頭設定 Unity 時，「麥克風」功能應該在[套用 MRTK 專案設定程式設定](../mr-learning-base-02.md#configuring-the-unity-project)指示期間啟用。</span><span class="sxs-lookup"><span data-stu-id="21cc0-105">The Microphone capability should have been enabled during the [Apply the MRTK Project Configurator settings](../mr-learning-base-02.md#configuring-the-unity-project) instructions when you configured the Unity project at the beginning of this tutorial series.</span></span> <span data-ttu-id="21cc0-106">不過如果未啟用，請務必立即啟用。</span><span class="sxs-lookup"><span data-stu-id="21cc0-106">However, if it is not enabled, make sure you enable it now.</span></span>

<span data-ttu-id="21cc0-107">在 [階層] 視窗中，選取 [MixedRealityToolkit] 物件，然後在 [偵測器] 視窗中，流覽至 [輸入] 索引標籤：</span><span class="sxs-lookup"><span data-stu-id="21cc0-107">In the Hierarchy window, select the MixedRealityToolkit object, then in the Inspector window, navigate to the Input tab:</span></span>

* <span data-ttu-id="21cc0-108">展開 **輸入資料提供者** ，然後按一下 [ **+ 新增] Data Provider** 按鈕，以新增 Data Provider</span><span class="sxs-lookup"><span data-stu-id="21cc0-108">Expand the **Input Data Providers** , click the **+ Add Data Provider** button to add a new Data Provider</span></span>

![用於新增語音命令的資料提供者](../images/mr-learning-base/base-09-section1-step1-2.png)

<span data-ttu-id="21cc0-110">將 **MixedReality 輸入**  >  **WindowsSpeechInputProvider** 指派給新 Data Provider 的 [**類型**] 欄位。</span><span class="sxs-lookup"><span data-stu-id="21cc0-110">Assign **Microsoft.MixedReality.ToolKit.Windows.Input** > **WindowsSpeechInputProvider** to the **Type** field of the new Data Provider.</span></span>

![新增語音命令設定](../images/mr-learning-base/base-09-section1-step1-3.png)

# <a name="unity-2020--openxr"></a>[<span data-ttu-id="21cc0-112">Unity 2020 + OpenXR</span><span class="sxs-lookup"><span data-stu-id="21cc0-112">Unity 2020 + OpenXR</span></span>](#tab/openxr)

## <a name="ensuring-microphone-capability-and-adding-speech-input-data-provider"></a><span data-ttu-id="21cc0-113">確保麥克風功能和新增語音輸入資料提供者</span><span class="sxs-lookup"><span data-stu-id="21cc0-113">Ensuring Microphone capability and adding Speech Input data provider</span></span>

<span data-ttu-id="21cc0-114">在 Unity 功能表中，選取 [混合實境工具組] > [公用程式] > [設定 Unity 專案] 以開啟 [MRTK 專案設定程式] 視窗，然後在 [UWP 功能] 區段中，確認 [啟用麥克風功能] 呈現灰色：</span><span class="sxs-lookup"><span data-stu-id="21cc0-114">In the Unity menu, select Mixed Reality Toolkit > Utilities > **Configure Unity Project** to open the **MRTK Project Configurator** window, then in the **UWP Capabilities** section, verify that **Enable Microphone Capability** is greyed out:</span></span>

![啟用 OpenXR 的麥克風功能](../images/mr-learning-base/base-09-section1-step1-1.png)

> [!NOTE]
> <span data-ttu-id="21cc0-116">當您在本教學課程系列開頭設定 Unity 時，「麥克風」功能應該在[套用 MRTK 專案設定程式設定](../mr-learning-base-02.md#configuring-the-unity-project)指示期間啟用。</span><span class="sxs-lookup"><span data-stu-id="21cc0-116">The Microphone capability should have been enabled during the [Apply the MRTK Project Configurator settings](../mr-learning-base-02.md#configuring-the-unity-project) instructions when you configured the Unity project at the beginning of this tutorial series.</span></span> <span data-ttu-id="21cc0-117">不過如果未啟用，請務必立即啟用。</span><span class="sxs-lookup"><span data-stu-id="21cc0-117">However, if it is not enabled, make sure you enable it now.</span></span>

<span data-ttu-id="21cc0-118">在 [階層] 視窗中，選取 [MixedRealityToolkit] 物件，然後在 [偵測器] 視窗中，流覽至 [輸入] 索引標籤：</span><span class="sxs-lookup"><span data-stu-id="21cc0-118">In the Hierarchy window, select the MixedRealityToolkit object, then in the Inspector window, navigate to the Input tab:</span></span>

* <span data-ttu-id="21cc0-119">展開 **輸入資料提供者** ，然後按一下 [ **+ 新增] Data Provider** 按鈕，以新增 Data Provider</span><span class="sxs-lookup"><span data-stu-id="21cc0-119">Expand the **Input Data Providers** , click the **+ Add Data Provider** button to add a new Data Provider</span></span>

![新增 OpenXR 的語音命令](../images/mr-learning-base/base-09-section1-step1-2.png)

<span data-ttu-id="21cc0-121">將 **MixedReality 輸入**  >  **WindowsSpeechInputProvider** 指派給新 Data Provider 的 [**類型**] 欄位。</span><span class="sxs-lookup"><span data-stu-id="21cc0-121">Assign **Microsoft.MixedReality.ToolKit.Windows.Input** > **WindowsSpeechInputProvider** to the **Type** field of the new Data Provider.</span></span>

![新增 OpenXR 設定的語音命令](../images/mr-learning-base/base-09-section1-step1-3.png)

# <a name="legacy-wsa"></a>[<span data-ttu-id="21cc0-123">舊版 WSA</span><span class="sxs-lookup"><span data-stu-id="21cc0-123">Legacy WSA</span></span>](#tab/wsa)

## <a name="ensuring-the-microphone-capability-is-enabled"></a><span data-ttu-id="21cc0-124">確定已啟用麥克風功能</span><span class="sxs-lookup"><span data-stu-id="21cc0-124">Ensuring the Microphone capability is enabled</span></span>

<span data-ttu-id="21cc0-125">在 Unity 功能表中，選取 [混合實境工具組] > [公用程式] > [設定 Unity 專案] 以開啟 [MRTK 專案設定程式] 視窗，然後在 [UWP 功能] 區段中，確認 [啟用麥克風功能] 呈現灰色：</span><span class="sxs-lookup"><span data-stu-id="21cc0-125">In the Unity menu, select Mixed Reality Toolkit > Utilities > **Configure Unity Project** to open the **MRTK Project Configurator** window, then in the **UWP Capabilities** section, verify that **Enable Microphone Capability** is greyed out:</span></span>

![啟用麥克風功能](../images/mr-learning-base/base-09-section1-step1-1.png)

> [!NOTE]
> <span data-ttu-id="21cc0-127">當您在本教學課程系列開頭設定 Unity 時，「麥克風」功能應該在[套用 MRTK 專案設定程式設定](../mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk)指示期間啟用。</span><span class="sxs-lookup"><span data-stu-id="21cc0-127">The Microphone capability should have been enabled during the [Apply the MRTK Project Configurator settings](../mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk) instructions when you configured the Unity project at the beginning of this tutorial series.</span></span> <span data-ttu-id="21cc0-128">不過如果未啟用，請務必立即啟用。</span><span class="sxs-lookup"><span data-stu-id="21cc0-128">However, if it is not enabled, make sure you enable it now.</span></span>
