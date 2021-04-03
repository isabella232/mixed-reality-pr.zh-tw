---
ms.openlocfilehash: 4b42b669e45181dec45cab2337d01488c77f77cb
ms.sourcegitcommit: 8d386bf6c82ec9860815e873e1f2870ea410f40f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/31/2021
ms.locfileid: "106097023"
---
# <a name="unity-20192020--windows-xr-plugin"></a>[<span data-ttu-id="38900-101">Unity 2019/2020 + Windows XR 外掛程式</span><span class="sxs-lookup"><span data-stu-id="38900-101">Unity 2019/2020 + Windows XR Plugin</span></span>](#tab/winxr)

## <a name="ensuring-eye-gaze-input-capability-and-adding-eye-gaze-data-provider"></a><span data-ttu-id="38900-102">確保眼睛的輸入功能，以及新增眼睛 Data Provider</span><span class="sxs-lookup"><span data-stu-id="38900-102">Ensuring Eye Gaze Input capability and adding Eye Gaze Data Provider</span></span>

<span data-ttu-id="38900-103">在 Unity 功能表中，選取 [混合實境工具組] > [公用程式] > [設定 Unity 專案] 以開啟 [MRTK 專案設定程式] 視窗，然後在 [UWP 功能] 區段中，確認 [啟用眼球注視輸入功能] 呈現灰色：</span><span class="sxs-lookup"><span data-stu-id="38900-103">In the Unity menu, select Mixed Reality Toolkit > Utilities > **Configure Unity Project** to open the **MRTK Project Configurator** window, then in the **UWP Capabilities** section, verify that **Enable Eye Gaze Input Capability** is greyed out:</span></span>

![Unity [MRTK 專案設定程式] 視窗](../images/mr-learning-base/base-08-section1-step1-1.png)

> [!NOTE]
> <span data-ttu-id="38900-105">當您在本教學課程系列開頭設定 Unity 時，「注視輸入」功能應該在[套用 MRTK 專案設定程式設定](../mr-learning-base-02.md#configuring-the-unity-project)指示期間啟用。</span><span class="sxs-lookup"><span data-stu-id="38900-105">The Gaze Input capability should have been enabled during the [Apply the MRTK Project Configurator settings](../mr-learning-base-02.md#configuring-the-unity-project) instructions when you configured the Unity project at the beginning of this tutorial series.</span></span> <span data-ttu-id="38900-106">不過如果未啟用，請確定您立即啟用。</span><span class="sxs-lookup"><span data-stu-id="38900-106">However, if it is not enabled, make sure you enable it now.</span></span>

<span data-ttu-id="38900-107">在 [階層] 視窗中，選取 [MixedRealityToolkit] 物件，然後在 [偵測器] 視窗中，流覽至 [輸入] 索引標籤：</span><span class="sxs-lookup"><span data-stu-id="38900-107">In the Hierarchy window, select the MixedRealityToolkit object, then in the Inspector window, navigate to the Input tab:</span></span>

* <span data-ttu-id="38900-108">展開 **輸入資料提供者** ，然後按一下 [ **+ 新增] Data Provider** 按鈕，以新增 Data Provider</span><span class="sxs-lookup"><span data-stu-id="38900-108">Expand the **Input Data Providers** , click the **+ Add Data Provider** button to add a new Data Provider</span></span>

![新增眼睛資料提供者1](../images/mr-learning-base/base-08-section1-step1-2.png)

<span data-ttu-id="38900-110">將 **MixedReality**  >  **指派給** 新 Data Provider 的 [**類型**] 欄位。</span><span class="sxs-lookup"><span data-stu-id="38900-110">Assign **Microsoft.MixedReality.ToolKit.WindowsMixedReality.Input** > **WindowsMixedRealityEyeGazeProvider** to the **Type** field of the new Data Provider.</span></span>

![新增視覺資料提供者2](../images/mr-learning-base/base-08-section1-step1-3.png)

# <a name="unity-2020--openxr"></a>[<span data-ttu-id="38900-112">Unity 2020 + OpenXR</span><span class="sxs-lookup"><span data-stu-id="38900-112">Unity 2020 + OpenXR</span></span>](#tab/openxr)

## <a name="ensuring-eye-gaze-input-capability-and-adding-eye-gaze-data-provider"></a><span data-ttu-id="38900-113">確保眼睛的輸入功能，以及新增眼睛 Data Provider</span><span class="sxs-lookup"><span data-stu-id="38900-113">Ensuring Eye Gaze Input capability and adding Eye Gaze Data Provider</span></span>

<span data-ttu-id="38900-114">在 [階層] 視窗中，選取 [MixedRealityToolkit] 物件，然後在 [偵測器] 視窗中，流覽至 [輸入] 索引標籤：</span><span class="sxs-lookup"><span data-stu-id="38900-114">In the Hierarchy window, select the MixedRealityToolkit object, then in the Inspector window, navigate to the Input tab:</span></span>

* <span data-ttu-id="38900-115">展開 **輸入資料提供者** ，然後按一下 [ **+ 新增] Data Provider** 按鈕，以新增 Data Provider</span><span class="sxs-lookup"><span data-stu-id="38900-115">Expand the **Input Data Providers** , click the **+ Add Data Provider** button to add a new Data Provider</span></span>

![新增眼睛資料提供者1](../images/mr-learning-base/base-08-section1-step1-2openxr.png)

<span data-ttu-id="38900-117">將 **MixedReality** 指派  >  至新 Data Provider 的 [**類型**] 欄位 **中。**</span><span class="sxs-lookup"><span data-stu-id="38900-117">Assign **Microsoft.MixedReality.ToolKit.XRSDK.OpenXR.Input** > **WindowsMixedRealityEyeGazeProvider** to the **Type** field of the new Data Provider.</span></span>

![新增視覺資料提供者2](../images/mr-learning-base/base-08-section1-step1-3openxr.png)

# <a name="legacy-wsa"></a>[<span data-ttu-id="38900-119">舊版 WSA</span><span class="sxs-lookup"><span data-stu-id="38900-119">Legacy WSA</span></span>](#tab/wsa)

## <a name="ensuring-the-eye-gaze-input-capability-is-enabled"></a><span data-ttu-id="38900-120">確保已啟用「眼球注視輸入」功能</span><span class="sxs-lookup"><span data-stu-id="38900-120">Ensuring the Eye Gaze Input capability is enabled</span></span>

<span data-ttu-id="38900-121">在 Unity 功能表中，選取 [混合實境工具組] > [公用程式] > [設定 Unity 專案] 以開啟 [MRTK 專案設定程式] 視窗，然後在 [UWP 功能] 區段中，確認 [啟用眼球注視輸入功能] 呈現灰色：</span><span class="sxs-lookup"><span data-stu-id="38900-121">In the Unity menu, select Mixed Reality Toolkit > Utilities > **Configure Unity Project** to open the **MRTK Project Configurator** window, then in the **UWP Capabilities** section, verify that **Enable Eye Gaze Input Capability** is greyed out:</span></span>

![Unity [MRTK 專案設定程式] 視窗](../images/mr-learning-base/base-08-section1-step1-1.png)

> [!NOTE]
> <span data-ttu-id="38900-123">當您在本教學課程系列開頭設定 Unity 時，「注視輸入」功能應該在[套用 MRTK 專案設定程式設定](../mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk)指示期間啟用。</span><span class="sxs-lookup"><span data-stu-id="38900-123">The Gaze Input capability should have been enabled during the [Apply the MRTK Project Configurator settings](../mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk) instructions when you configured the Unity project at the beginning of this tutorial series.</span></span> <span data-ttu-id="38900-124">不過如果未啟用，請確定您立即啟用。</span><span class="sxs-lookup"><span data-stu-id="38900-124">However, if it is not enabled, make sure you enable it now.</span></span>
