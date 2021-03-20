---
title: 架構和執行時間
description: MRTK 中的架構和執行時間相關資訊。
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
ms.localizationpriority: medium
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: 96bf0501865c661e8ccfde1307eab967e8f8e978
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104692895"
---
# <a name="framework-and-runtime"></a><span data-ttu-id="132a2-104">架構和執行時間</span><span class="sxs-lookup"><span data-stu-id="132a2-104">Framework and runtime</span></span>

## <a name="changes-to-the-scene"></a><span data-ttu-id="132a2-105">場景的變更</span><span class="sxs-lookup"><span data-stu-id="132a2-105">Changes to the scene</span></span>

<span data-ttu-id="132a2-106">若要使用工具組，MixedRealityToolkit 腳本的實例必須在場景中。</span><span class="sxs-lookup"><span data-stu-id="132a2-106">To use the toolkit an instance of the MixedRealityToolkit script must be in your scene.</span></span>
<span data-ttu-id="132a2-107">若要加入一個，請使用功能表選項：混合現實工具組-> 新增至場景並進行設定。</span><span class="sxs-lookup"><span data-stu-id="132a2-107">To add one use the menu option: Mixed Reality Toolkit -> Add to Scene and Configure.</span></span> <span data-ttu-id="132a2-108">此實例負責註冊、更新及中斷服務。</span><span class="sxs-lookup"><span data-stu-id="132a2-108">This instance is responsible for registering, updating and tearing down services.</span></span> <span data-ttu-id="132a2-109">它也是您選擇設定設定檔的位置。</span><span class="sxs-lookup"><span data-stu-id="132a2-109">It's also where your configuration profile is chosen.</span></span>

<span data-ttu-id="132a2-110">除了將 MRTK GameObject 新增至場景之外，功能表選項也會：</span><span class="sxs-lookup"><span data-stu-id="132a2-110">Apart from adding the MRTK GameObject to the scene the menu option will also:</span></span>

- <span data-ttu-id="132a2-111">新增許多其他 MRTK 元件所使用的 MixedRealityPlayspace，以因應全球和區域空間轉換的原因。</span><span class="sxs-lookup"><span data-stu-id="132a2-111">Add the MixedRealityPlayspace, which is used by many other MRTK components to reason over world and local space transformations.</span></span>
- <span data-ttu-id="132a2-112">移動主要攝影機作為 MixedRealityPlayspace (的子系，也將一些輸入和注視相關的腳本新增至主要攝影機，以協助 UnityUI 和注視相關的輸入功能) 。</span><span class="sxs-lookup"><span data-stu-id="132a2-112">Move the main Camera as a child of the MixedRealityPlayspace (and also adding some input and gaze related scripts to the main Camera, which help power UnityUI and gaze related input functionality).</span></span>

## <a name="mixedrealitytoolkit-object-and-runtime"></a><span data-ttu-id="132a2-113">MixedRealityToolkit 物件和執行時間</span><span class="sxs-lookup"><span data-stu-id="132a2-113">MixedRealityToolkit object and runtime</span></span>

<span data-ttu-id="132a2-114">MRTK 有數個核心服務。</span><span class="sxs-lookup"><span data-stu-id="132a2-114">The MRTK has several core services.</span></span> <span data-ttu-id="132a2-115">彼此之間的座標;其他則是獨立的。</span><span class="sxs-lookup"><span data-stu-id="132a2-115">Some coordinate with one another; others are independent.</span></span>
<span data-ttu-id="132a2-116">全都共用相同的生命週期，也就是啟動、註冊、更新和終止，而這種生命週期與 Unity 的 MonoBehaviour 生命週期分開。</span><span class="sxs-lookup"><span data-stu-id="132a2-116">All share the same life cycle - startup, registration, update and teardown - and this life cycle stands apart from Unity's MonoBehaviour life cycle.</span></span> <span data-ttu-id="132a2-117">這段 [媒體文章](https://medium.com/@stephen_hodgson/the-mixed-reality-framework-6fdb5c11feb2) 會說明這種方法背後的一些背景和動機。</span><span class="sxs-lookup"><span data-stu-id="132a2-117">This [medium post](https://medium.com/@stephen_hodgson/the-mixed-reality-framework-6fdb5c11feb2) explains some of the background and motivation behind this approach.</span></span> <span data-ttu-id="132a2-118">MRTK 具有單一物件，可管理其服務的生命週期和執行時間。</span><span class="sxs-lookup"><span data-stu-id="132a2-118">MRTK has a single object that manages life and runtime of its services.</span></span>

<span data-ttu-id="132a2-119">此實體可確保：</span><span class="sxs-lookup"><span data-stu-id="132a2-119">This entity ensures that:</span></span>

- <span data-ttu-id="132a2-120">當遊戲開始時，會以預先定義的順序進行服務的探索和初始化。</span><span class="sxs-lookup"><span data-stu-id="132a2-120">when the game starts, discovery and initialization of services happens in a pre-defined order.</span></span>
- <span data-ttu-id="132a2-121">它提供一種機制，讓服務自行註冊 (也就是「我支援此服務！」) 和其他呼叫者取得這些服務的保留。</span><span class="sxs-lookup"><span data-stu-id="132a2-121">it provides a mechanism for services to register themselves (i.e. “I support this service!”) and for other callers to get a hold of those services.</span></span>
- <span data-ttu-id="132a2-122">它會提供更新 () /LateUpdate () 呼叫，然後將它們轉送至各種服務 (例如 via UpdateAllServices/LateUpdateAllServices) 。</span><span class="sxs-lookup"><span data-stu-id="132a2-122">it provides the Update()/LateUpdate() calls and forwards them onto the various services (i.e. via UpdateAllServices/LateUpdateAllServices).</span></span>
