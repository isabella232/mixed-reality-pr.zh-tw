---
title: 輸入概觀
description: MRTK 中的輸入系統總覽
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: ec8ebced1f7faea04e88068612cd642e15fb165f
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/03/2021
ms.locfileid: "101780005"
---
# <a name="input-overview"></a><span data-ttu-id="be48e-104">輸入總覽</span><span class="sxs-lookup"><span data-stu-id="be48e-104">Input overview</span></span>

<span data-ttu-id="be48e-105">MRTK 中的輸入系統可讓您：</span><span class="sxs-lookup"><span data-stu-id="be48e-105">The Input System in MRTK allows you to:</span></span>

- <span data-ttu-id="be48e-106">透過輸入事件，使用各種輸入來源的輸入，例如6個 DOF 控制器、明確表述的手或語音。</span><span class="sxs-lookup"><span data-stu-id="be48e-106">Consume inputs from a variety of input sources, such as 6 DOF controllers, articulated hands or speech, via input events.</span></span>
- <span data-ttu-id="be48e-107">定義抽象動作，例如 *選取* 或 *功能表*，並將它們關聯至不同的輸入。</span><span class="sxs-lookup"><span data-stu-id="be48e-107">Define abstract actions, like *Select* or *Menu*, and associate them to different inputs.</span></span>
- <span data-ttu-id="be48e-108">透過焦點和指標事件連接至控制器的設定指標，以驅動 UI 元件。</span><span class="sxs-lookup"><span data-stu-id="be48e-108">Setup pointers attached to controllers to drive UI components via focus and pointer events.</span></span>

<img src="../images/input/MRTK_InputSystem.png" alt="Input System" style="display:block;margin-left:auto;margin-right:auto;">
<span data-ttu-id="be48e-109"><sup>MRTK 輸入系統的總覽</sup></span><span class="sxs-lookup"><span data-stu-id="be48e-109"><sup>Overview of MRTK Input System</sup></span></span>

<span data-ttu-id="be48e-110">[**輸入資料提供者會 (裝置管理員)**](input-providers.md)產生輸入。</span><span class="sxs-lookup"><span data-stu-id="be48e-110">Inputs are produced by [**Input Data Providers(Device Manager)**](input-providers.md).</span></span> <span data-ttu-id="be48e-111">每個提供者都對應至特定的輸入來源： Open VR、Windows Mixed Reality (WMR) 、Unity 搖桿、Windows 語音等等。提供者會透過 *混合現實工具* 組元件中 **已註冊的服務提供者設定檔** 新增至專案，並會在提供對應的輸入來源時自動產生 [**輸入事件**](input-events.md) (例如，偵測到 WMR 控制器或遊戲台連線) 時。</span><span class="sxs-lookup"><span data-stu-id="be48e-111">Each provider corresponds to a particular source of input: Open VR, Windows Mixed Reality (WMR), Unity Joystick, Windows Speech, etc. Providers are added to your project via the **Registered Service Providers Profile** in the *Mixed Reality Toolkit* component and will produce [**Input Events**](input-events.md) automatically when the corresponding input sources are available (e.g. when a WMR controller is detected or a gamepad connected).</span></span>

<span data-ttu-id="be48e-112">[**輸入動作**](input-actions.md) 是原始輸入的抽象概念，目的是要協助隔離應用程式邏輯與產生輸入的特定輸入來源。</span><span class="sxs-lookup"><span data-stu-id="be48e-112">[**Input Actions**](input-actions.md) are abstractions over raw inputs meant to help isolate application logic from the specific input sources producing an input.</span></span> <span data-ttu-id="be48e-113">例如，它可能很有用，例如，定義 *選取* 動作並將它對應至滑鼠左鍵、遊戲台中的按鈕，以及6個 DOF 控制器中的觸發程式。</span><span class="sxs-lookup"><span data-stu-id="be48e-113">It can be useful, for example, to define a *Select* action and map it to the left mouse button, a button in a gamepad and a trigger in a 6 DOF controller.</span></span> <span data-ttu-id="be48e-114">然後，您可以讓應用程式邏輯接聽 *選取* 的輸入動作事件，而不需要知道可以產生的所有不同輸入。</span><span class="sxs-lookup"><span data-stu-id="be48e-114">You can then have your application logic listen for *Select* input action events instead of having to be aware of all the different inputs that can produce it.</span></span> <span data-ttu-id="be48e-115">輸入動作會定義在 **輸入動作設定檔** 中，可在 *混合現實工具* 組元件的 *輸入系統設定檔* 中找到。</span><span class="sxs-lookup"><span data-stu-id="be48e-115">Input Actions are defined in the **Input Actions Profile**, found within the *Input System Profile* in the *Mixed Reality Toolkit* component.</span></span>

<span data-ttu-id="be48e-116">當偵測到輸入裝置時，以及當輸入裝置遺失或中斷連線時，這些 [**控制器**](controllers.md)會由 *輸入提供者* 建立。</span><span class="sxs-lookup"><span data-stu-id="be48e-116">[**Controllers**](controllers.md) are created by *input providers* when input devices are detected and destroyed when they're lost or disconnected.</span></span> <span data-ttu-id="be48e-117">例如，WMR 輸入提供者將會為 6 DOF 裝置建立 *WMR 控制器* ，並針對有向的 *手勢建立 WMR* 的明確控制器。</span><span class="sxs-lookup"><span data-stu-id="be48e-117">The WMR input provider, for example, will create *WMR controllers* for 6 DOF devices and *WMR articulated hand controllers* for articulated hands.</span></span> <span data-ttu-id="be48e-118">您可以透過 **控制器對應設定檔**，在 *輸入系統設定檔* 中，將控制器輸入對應至輸入動作。</span><span class="sxs-lookup"><span data-stu-id="be48e-118">Controller inputs can be mapped to input actions via the **Controller Mapping Profile**, inside the *Input System Profile*.</span></span> <span data-ttu-id="be48e-119">控制器所引發的輸入事件會包含相關聯的輸入動作（如果有的話）。</span><span class="sxs-lookup"><span data-stu-id="be48e-119">Inputs events raised by controllers will include the associated input action, if any.</span></span>

<span data-ttu-id="be48e-120">控制器可以將 [**指標**](pointers.md) 附加至它們，以查詢場景來判斷具有焦點的遊戲物件，並在其上引發 [**指標事件**](pointers.md#pointer-event-interfaces) 。</span><span class="sxs-lookup"><span data-stu-id="be48e-120">Controllers can have [**Pointers**](pointers.md) attached to them that query the scene to determine the game object with focus and raise [**Pointer Events**](pointers.md#pointer-event-interfaces) on it.</span></span> <span data-ttu-id="be48e-121">例如，我們的 *線指標* 會使用控制器姿勢來計算光線的原點和方向，對場景執行 raycast。</span><span class="sxs-lookup"><span data-stu-id="be48e-121">As an example, our *line pointer* performs a raycast against the scene using the controller pose to compute the origin and direction of the ray.</span></span> <span data-ttu-id="be48e-122">在 **指標設定檔** 的 *輸入系統設定檔* 下，會設定為每個控制器建立的指標。</span><span class="sxs-lookup"><span data-stu-id="be48e-122">The pointers created for each controller are set up in the **Pointer Profile**, under the *Input System Profile*.</span></span>

<img src="../images/input/MRTK_Input_EventFlow.png" width="200px" alt="Event Flow" style="display:block;margin-left:auto;margin-right:auto;">
<span data-ttu-id="be48e-123"><sup>事件流程。</sup></span><span class="sxs-lookup"><span data-stu-id="be48e-123"><sup>Event flow.</sup></span></span>

<span data-ttu-id="be48e-124">雖然您可以 [直接在 UI 元件中處理輸入事件](input-events.md)，但建議使用 [指標事件](pointers.md#pointer-event-interfaces) 來讓執行裝置保持獨立。</span><span class="sxs-lookup"><span data-stu-id="be48e-124">While you can handle [input events directly in UI components](input-events.md), it is recommended to use [pointer events](pointers.md#pointer-event-interfaces) to keep the implementation device-independent.</span></span>

<span data-ttu-id="be48e-125">MRTK 也提供數種便利的方法，可讓您直接以與裝置無關的方式查詢輸入狀態。</span><span class="sxs-lookup"><span data-stu-id="be48e-125">MRTK also provides several convenience methods to query input state directly in a device-independent way.</span></span> <span data-ttu-id="be48e-126">See [Accessing input state in MRTK](input-state.md) for more details.</span><span class="sxs-lookup"><span data-stu-id="be48e-126">See [Accessing input state in MRTK](input-state.md) for more details.</span></span>
