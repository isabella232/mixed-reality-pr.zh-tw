---
title: 住
description: 停留互動
author: cre8ivepark
ms.author: dongpark
ms.date: 05/20/2021
keywords: 停留、Unity、HoloLens、HoloLens 2、混合現實、開發、MRTK
monikerRange: '>= mrtkunity-2021-05'
ms.openlocfilehash: 18e69f001c8989234d1b75fb713796f079cacbdf
ms.sourcegitcommit: a5afc24a4887880e394ef57216b8fd9de9760004
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/28/2021
ms.locfileid: "110647767"
---
# <a name="dwell"></a><span data-ttu-id="ac2db-104">住</span><span class="sxs-lookup"><span data-stu-id="ac2db-104">Dwell</span></span>

![停留主圖](../images/dwell/MRTK_UX_Dwell.png)

<span data-ttu-id="ac2db-106">當人的手中有其他工作忙碌的情況下，前端和停留很好用。</span><span class="sxs-lookup"><span data-stu-id="ac2db-106">Head-gaze and dwell are great in scenarios where a person's hands are busy with other tasks.</span></span> <span data-ttu-id="ac2db-107">當語音不是100% 可靠或因為環境或社交條件約束而無法使用時，此功能也很有用。</span><span class="sxs-lookup"><span data-stu-id="ac2db-107">The feature is also useful when voice isn't 100% reliable or available because of environmental or social constraints.</span></span>
<span data-ttu-id="ac2db-108">MRTK 的停留範例會示範不同類型的 UI 元件，並提供可設定的回應時間和視覺效果的意見反應。</span><span class="sxs-lookup"><span data-stu-id="ac2db-108">MRTK's dwell examples demonstrate different types of UI components with configurable response time and visual feedback.</span></span>

<span data-ttu-id="ac2db-109">請參閱 [前端和停留指導](/windows/mixed-reality/design/gaze-and-dwell-head) 方針頁面，以取得設計建議。</span><span class="sxs-lookup"><span data-stu-id="ac2db-109">Please see [Head-gaze and dwell guideline](/windows/mixed-reality/design/gaze-and-dwell-head) page for the design recommendations.</span></span>

## <a name="dwell-scripts"></a><span data-ttu-id="ac2db-110">停留腳本</span><span class="sxs-lookup"><span data-stu-id="ac2db-110">Dwell scripts</span></span>

- <span data-ttu-id="ac2db-111">**DwellHandler**：將停留樣式新增至 UI 目標。</span><span class="sxs-lookup"><span data-stu-id="ac2db-111">**DwellHandler**: Adds a dwell modality to the UI target.</span></span>
- <span data-ttu-id="ac2db-112">**DwellStateType**：停留處理常式的狀態。</span><span class="sxs-lookup"><span data-stu-id="ac2db-112">**DwellStateType**: The states of the dwell handler.</span></span>
- <span data-ttu-id="ac2db-113">**DwellUnityEvent**：停留事件的 Unity 事件。</span><span class="sxs-lookup"><span data-stu-id="ac2db-113">**DwellUnityEvent**: Unity event for a dwell event.</span></span> <span data-ttu-id="ac2db-114">包含指標參考。</span><span class="sxs-lookup"><span data-stu-id="ac2db-114">Contains the pointer reference.</span></span>
- <span data-ttu-id="ac2db-115">**BaseDwellPressableButton** ：在 PressableButtonHoloLens2 prefabs 中觸發 OnClick () 事件的腳本。 `Interactable`</span><span class="sxs-lookup"><span data-stu-id="ac2db-115">**BaseDwellPressableButton.cs** : A script that triggers OnClick() event in `Interactable` of PressableButtonHoloLens2 prefabs.</span></span>
- <span data-ttu-id="ac2db-116">**ToggleDwellPressableButton** ：此腳本 `_BorderWidth` `dwellVisualImage` 會修改使用 MRTK 標準著色器之的屬性。</span><span class="sxs-lookup"><span data-stu-id="ac2db-116">**ToggleDwellPressableButton.cs** : This script modifies `_BorderWidth` property of the `dwellVisualImage` which is using MRTK Standard Shader.</span></span>

## <a name="dwell-profiles"></a><span data-ttu-id="ac2db-117">停留設定檔</span><span class="sxs-lookup"><span data-stu-id="ac2db-117">Dwell profiles</span></span>
<span data-ttu-id="ac2db-118">停留 **處理常式** 會使用停留設定檔來設定各種閾值。</span><span class="sxs-lookup"><span data-stu-id="ac2db-118">Dwell profiles are used by the **Dwell Handler** to configure the various thresholds.</span></span>
- <span data-ttu-id="ac2db-119">**ButtonDwellProfile 資產**</span><span class="sxs-lookup"><span data-stu-id="ac2db-119">**ButtonDwellProfile.asset**</span></span>
- <span data-ttu-id="ac2db-120">**InstandDwellProfile 資產**</span><span class="sxs-lookup"><span data-stu-id="ac2db-120">**InstandDwellProfile.asset**</span></span>
- <span data-ttu-id="ac2db-121">**DwellProfileWithDecay 資產**</span><span class="sxs-lookup"><span data-stu-id="ac2db-121">**DwellProfileWithDecay.asset**</span></span>

## <a name="prefabs"></a><span data-ttu-id="ac2db-122">Prefabs</span><span class="sxs-lookup"><span data-stu-id="ac2db-122">Prefabs</span></span>

<span data-ttu-id="ac2db-123">這些 prefabs 是 HoloLens 2 style pressable 按鈕 prefabs 的變體，具有可支援停留互動的額外元件。</span><span class="sxs-lookup"><span data-stu-id="ac2db-123">These prefabs are variants of the HoloLens 2 style pressable button prefabs that have additional components to support dwell interactions.</span></span>

- <span data-ttu-id="ac2db-124">**PressableButtonHoloLens2_Dwell. 預製專案**</span><span class="sxs-lookup"><span data-stu-id="ac2db-124">**PressableButtonHoloLens2_Dwell.prefab**</span></span>
- <span data-ttu-id="ac2db-125">**PressableButtonHoloLens2_32x96_Dwell. 預製專案**</span><span class="sxs-lookup"><span data-stu-id="ac2db-125">**PressableButtonHoloLens2_32x96_Dwell.prefab**</span></span>
- <span data-ttu-id="ac2db-126">**PressableButtonHoloLens2ToggleDwell. 預製專案**</span><span class="sxs-lookup"><span data-stu-id="ac2db-126">**PressableButtonHoloLens2ToggleDwell.prefab**</span></span>
- <span data-ttu-id="ac2db-127">**PressableButtonHoloLens2Toggle_32x96_Dwell. 預製專案**</span><span class="sxs-lookup"><span data-stu-id="ac2db-127">**PressableButtonHoloLens2Toggle_32x96_Dwell.prefab**</span></span>

<span data-ttu-id="ac2db-128">這些 prefabs 有額外的 backplate 元件 **QuadDwellVisual** 可將停留輸入狀態視覺化。</span><span class="sxs-lookup"><span data-stu-id="ac2db-128">These prefabs have an additional backplate component **QuadDwellVisual** to visualize the dwell input state.</span></span> <span data-ttu-id="ac2db-129">它已指派 **HolographicBackPlateDwellVisual** 的材質。</span><span class="sxs-lookup"><span data-stu-id="ac2db-129">It has **HolographicBackPlateDwellVisual.mat** material assigned.</span></span> <span data-ttu-id="ac2db-130">**ToggleDwellPressableButton** 會更新 MRTK 標準著色器的 **_BorderWidth** 屬性，以視覺化停留輸入。</span><span class="sxs-lookup"><span data-stu-id="ac2db-130">**ToggleDwellPressableButton.cs** updates the **_BorderWidth** property of MRTK Standard shader to visualize the dwell input.</span></span>

<img src="../images/dwell/MRTK_UX_Dwell_Prefabs_Structure.png" alt="Dwell prefabs structure" width="550px">
<img src="../images/dwell/MRTK_UX_Dwell_Prefabs.png" alt="Dwell prefabs" width="350px">

## <a name="example-scene"></a><span data-ttu-id="ac2db-131">範例場景</span><span class="sxs-lookup"><span data-stu-id="ac2db-131">Example scene</span></span>

<span data-ttu-id="ac2db-132">您可以在場景中找到範例 `DwellExample` 。</span><span class="sxs-lookup"><span data-stu-id="ac2db-132">You can find examples in the `DwellExample` scene.</span></span> <span data-ttu-id="ac2db-133">範例場景會顯示體積型 UI 範例和 Unity UI 範例。</span><span class="sxs-lookup"><span data-stu-id="ac2db-133">The example scene shows both volumetric UI examples and Unity UI examples.</span></span>

<img src="../images/dwell/MRTK_UX_Dwell_Examples.png" alt="Near Menu Example">

## <a name="see-also"></a><span data-ttu-id="ac2db-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ac2db-134">See also</span></span>

- [<span data-ttu-id="ac2db-135">**按鈕**</span><span class="sxs-lookup"><span data-stu-id="ac2db-135">**Buttons**</span></span>](button.md)
- [<span data-ttu-id="ac2db-136">**互動**</span><span class="sxs-lookup"><span data-stu-id="ac2db-136">**Interactable**</span></span>](interactable.md)
