---
title: 語音
description: 在 MRTK 中設定語音輸入
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、語音、
ms.openlocfilehash: d86b81a707c7ca47d9c98991a56e63531add4847
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104695335"
---
# <a name="speech"></a><span data-ttu-id="5e3b7-104">語音</span><span class="sxs-lookup"><span data-stu-id="5e3b7-104">Speech</span></span>

![近端功能表](../Images/Input/MRTK_Input_Speech.png)

<span data-ttu-id="5e3b7-106">語音輸入提供者（例如 *Windows 語音輸入*）不會建立任何控制器，而是可讓您定義可在辨識時引發語音輸入事件的關鍵字。</span><span class="sxs-lookup"><span data-stu-id="5e3b7-106">Speech input providers, like *Windows Speech Input*, don't create any controllers but instead allow you to define keywords that will raise speech input events when recognized.</span></span> <span data-ttu-id="5e3b7-107">*輸入系統設定檔* 中的 **語音命令設定檔** 可讓您設定要辨識的關鍵字。</span><span class="sxs-lookup"><span data-stu-id="5e3b7-107">The **Speech Commands Profile** in the *Input System Profile* is where you configure the keywords to recognize.</span></span> <span data-ttu-id="5e3b7-108">您也可以針對每個命令：</span><span class="sxs-lookup"><span data-stu-id="5e3b7-108">For each command you can also:</span></span>

- <span data-ttu-id="5e3b7-109">選取要對應的 **輸入動作** 。</span><span class="sxs-lookup"><span data-stu-id="5e3b7-109">Select an **input action** to map it to.</span></span> <span data-ttu-id="5e3b7-110">如此一來，您就可以藉由將這兩個動作對應到相同的動作，使用關鍵字 *Select* 來與滑鼠左鍵相同的效果。</span><span class="sxs-lookup"><span data-stu-id="5e3b7-110">This way you can for example use the keyword *Select* to have the same effect as a left mouse click, by mapping both to the same action.</span></span>
- <span data-ttu-id="5e3b7-111">指定在按下時會產生相同語音事件的 **按鍵碼** 。</span><span class="sxs-lookup"><span data-stu-id="5e3b7-111">Specify a **key code** that will produce the same speech event when pressed.</span></span>
- <span data-ttu-id="5e3b7-112">新增將在 UWP 應用程式中用來從應用程式資源取得當地語系化關鍵字的 **當地語系化金鑰** 。</span><span class="sxs-lookup"><span data-stu-id="5e3b7-112">Add a **localization key** that will be used in UWP apps to obtain the localized keyword from the app resources.</span></span>

<img src="../Images/Input/SpeechCommandsProfile.png" width="450px" alt="Speech command profile">

## <a name="handling-speech-input"></a><span data-ttu-id="5e3b7-113">處理語音輸入</span><span class="sxs-lookup"><span data-stu-id="5e3b7-113">Handling speech input</span></span>

<span data-ttu-id="5e3b7-114">您 [**`Speech Input Handler`**](xref:Microsoft.MixedReality.Toolkit.Input.SpeechInputHandler) 可以使用 [**UnityEvents**](https://docs.unity3d.com/Manual/UnityEvents.html)將腳本新增至 GameObject 來處理語音命令。</span><span class="sxs-lookup"><span data-stu-id="5e3b7-114">The [**`Speech Input Handler`**](xref:Microsoft.MixedReality.Toolkit.Input.SpeechInputHandler) script can be added to a GameObject to handle speech commands using [**UnityEvents**](https://docs.unity3d.com/Manual/UnityEvents.html).</span></span> <span data-ttu-id="5e3b7-115">它會自動顯示來自 **語音命令設定檔** 的已定義關鍵字清單。</span><span class="sxs-lookup"><span data-stu-id="5e3b7-115">It automatically shows the list of the defined keywords from the **Speech Commands Profile**.</span></span>

<img src="../Images/Input/SpeechCommands_SpeechInputHandler1.png" width="450px" alt="speech input handler 1">

<span data-ttu-id="5e3b7-116">指派選擇性的 **SpeechConfirmationTooltip 預製專案** ，以顯示辨識的動畫確認工具提示標籤。</span><span class="sxs-lookup"><span data-stu-id="5e3b7-116">Assign optional **SpeechConfirmationTooltip.prefab** to display animated confirmation tooltip label on recognition.</span></span>

<img src="../Images/Input/SpeechCommands_SpeechInputHandler2.png" alt="Speech input handler 2">

<span data-ttu-id="5e3b7-117">或者，開發人員可以 [`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) 在自訂腳本元件中執行介面，以 [處理語音輸入事件](InputEvents.md#input-event-interface-example)。</span><span class="sxs-lookup"><span data-stu-id="5e3b7-117">Alternatively, developers can implement the [`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) interface in a custom script component to [handle speech input events](InputEvents.md#input-event-interface-example).</span></span>

## <a name="example-scene"></a><span data-ttu-id="5e3b7-118">範例場景</span><span class="sxs-lookup"><span data-stu-id="5e3b7-118">Example scene</span></span>

<span data-ttu-id="5e3b7-119">中的 **SpeechInputExample** 場景 `MRTK/Examples/Demos/Input/Scenes/Speech` 顯示如何使用語音。</span><span class="sxs-lookup"><span data-stu-id="5e3b7-119">The **SpeechInputExample** scene, in `MRTK/Examples/Demos/Input/Scenes/Speech`, shows how to use speech.</span></span> <span data-ttu-id="5e3b7-120">您也可以藉由執行 [`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) (參閱 [事件處理常式](InputEvents.md)) 的表格，直接在您自己的腳本中接聽語音命令事件。</span><span class="sxs-lookup"><span data-stu-id="5e3b7-120">You can also listen to speech command events directly in your own script by implementing [`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) (see table of [event handlers](InputEvents.md)).</span></span>

<img src="../Images/Input/SpeechExampleScene.png" width="750px" alt="Speech Example scene">
