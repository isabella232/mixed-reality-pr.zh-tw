---
title: InputProviders
description: MRTK 中不同類型的輸入提供者相關檔
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: c262a9bddcddcc0756bc62a08712ccaf2bb7fd01
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/03/2021
ms.locfileid: "101780938"
---
# <a name="input-providers"></a><span data-ttu-id="fe344-104">輸入提供者</span><span class="sxs-lookup"><span data-stu-id="fe344-104">Input providers</span></span>

<span data-ttu-id="fe344-105">輸入提供者會在 **已註冊的服務提供者設定檔** 中註冊，可在混合現實工具組元件中找到：</span><span class="sxs-lookup"><span data-stu-id="fe344-105">Input providers are registered in the **Registered Service Providers Profile**, found in the Mixed Reality Toolkit component:</span></span>

<img src="../Images/Input/RegisteredServiceProviders.PNG" width="650px" alt="Registerd Service providers" style="display:block;">

<span data-ttu-id="fe344-106">這些是現成可用的輸入提供者，以及其對應的控制器：</span><span class="sxs-lookup"><span data-stu-id="fe344-106">These are the input providers available out of the box, together with their corresponding controllers:</span></span>

| <span data-ttu-id="fe344-107">輸入提供者</span><span class="sxs-lookup"><span data-stu-id="fe344-107">Input Provider</span></span> | <span data-ttu-id="fe344-108">控制器</span><span class="sxs-lookup"><span data-stu-id="fe344-108">Controllers</span></span> |
| --- | --- |
| [`Input Simulation Service`](xref:Microsoft.MixedReality.Toolkit.Input.InputSimulationService) | <span data-ttu-id="fe344-109">模擬的手</span><span class="sxs-lookup"><span data-stu-id="fe344-109">Simulated Hand</span></span> |
| [`Mouse Device Manager`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput.MouseDeviceManager) | <span data-ttu-id="fe344-110">滑鼠</span><span class="sxs-lookup"><span data-stu-id="fe344-110">Mouse</span></span>  |
| [`OpenVR Device Manager`](xref:Microsoft.MixedReality.Toolkit.OpenVR.Input.OpenVRDeviceManager) | <span data-ttu-id="fe344-111">一般 OpenVR、Vive 棒、Vive Knuckles、Oculus Touch、Oculus Remote、Windows Mixed Reality OpenVR</span><span class="sxs-lookup"><span data-stu-id="fe344-111">Generic OpenVR, Vive Wand, Vive Knuckles, Oculus Touch, Oculus Remote, Windows Mixed Reality OpenVR</span></span>  |
| [`Unity Joystick Manager`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput.UnityJoystickManager) | <span data-ttu-id="fe344-112">一般搖桿</span><span class="sxs-lookup"><span data-stu-id="fe344-112">Generic Joystick</span></span>  |
| [`Unity Touch Device Manager`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput.UnityTouchDeviceManager) | <span data-ttu-id="fe344-113">Unity 觸控控制器</span><span class="sxs-lookup"><span data-stu-id="fe344-113">Unity Touch Controller</span></span>  |
| [`Windows Dictation Input Provider`](xref:Microsoft.MixedReality.Toolkit.Windows.Input.WindowsDictationInputProvider) | <span data-ttu-id="fe344-114">*None*</span><span class="sxs-lookup"><span data-stu-id="fe344-114">*None*</span></span>  |
| [`Windows Mixed Reality Device Manager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager) | <span data-ttu-id="fe344-115">WMR 清楚的手、WMR 控制器、WMR GGV (注視、手勢和 Voice) 手</span><span class="sxs-lookup"><span data-stu-id="fe344-115">WMR Articulated Hand, WMR Controller, WMR GGV (Gaze, Gesture, and Voice) Hand</span></span> |
| [`Windows Speech Input Provider`](xref:Microsoft.MixedReality.Toolkit.Windows.Input.WindowsSpeechInputProvider) | <span data-ttu-id="fe344-116">*None*</span><span class="sxs-lookup"><span data-stu-id="fe344-116">*None*</span></span> |

<span data-ttu-id="fe344-117">聽寫和語音提供者不會建立任何控制器，而是會直接引發自己的特製化輸入事件。</span><span class="sxs-lookup"><span data-stu-id="fe344-117">Dictation and Speech providers don't create any controllers, they raise their own specialized input events directly.</span></span>

<span data-ttu-id="fe344-118">自訂輸入提供者可透過實作為 [`IMixedRealityInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputDeviceManager) 介面來建立。</span><span class="sxs-lookup"><span data-stu-id="fe344-118">Custom input providers can be created by implementing the [`IMixedRealityInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputDeviceManager) interface.</span></span>

<span data-ttu-id="fe344-119">如需詳細資訊，請參閱 [建立輸入系統資料提供者](CreateDataProvider.md)。</span><span class="sxs-lookup"><span data-stu-id="fe344-119">For more information, please see [creating an input system data provider](CreateDataProvider.md).</span></span>
