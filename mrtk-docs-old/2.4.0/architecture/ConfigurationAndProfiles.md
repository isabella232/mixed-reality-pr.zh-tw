---
title: 設定和設定檔
description: 修改 MRTK 中的設定檔。
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
ms.localizationpriority: medium
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、MRTK 設定檔
ms.openlocfilehash: ea61c8c7cbdb526cbf8cc10d29008a97559474f5
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104692905"
---
# <a name="configuration-and-profiles"></a><span data-ttu-id="524ed-104">設定和設定檔</span><span class="sxs-lookup"><span data-stu-id="524ed-104">Configuration and profiles</span></span>

<span data-ttu-id="524ed-105">並非每個 MRTK 的單一取用者都希望它以相同方式運作，因為在支援 AR 裝置時，有些會想要讓空間網格執行。</span><span class="sxs-lookup"><span data-stu-id="524ed-105">Not every single consumer of the MRTK will want it to behave the same way - some will want to have the spatial mesh running when on AR devices that support it.</span></span> <span data-ttu-id="524ed-106">有些可能會想要在所有時間都有診斷視覺效果，而某些可能只會在使用者說出語音命令時，才需要它。</span><span class="sxs-lookup"><span data-stu-id="524ed-106">Some may want the diagnostic visualization on all the time, and some may only want it on when the user says a voice command.</span></span>

<span data-ttu-id="524ed-107">MRTK 必須可設定，才能支援各式各樣的需求，並使用稱為「設定檔」的概念來完成此動作。</span><span class="sxs-lookup"><span data-stu-id="524ed-107">The MRTK needs to be configurable in order to support a wide range of those requirements, and it uses a concept called 'profiles' to accomplish this.</span></span>

## <a name="what-is-a-profile"></a><span data-ttu-id="524ed-108">什麼是設定檔？</span><span class="sxs-lookup"><span data-stu-id="524ed-108">What is a profile?</span></span>

<span data-ttu-id="524ed-109">設定檔儲存服務的設定。</span><span class="sxs-lookup"><span data-stu-id="524ed-109">Profiles store configuration settings for services.</span></span> <span data-ttu-id="524ed-110">您可以使用它們來控制要執行哪些服務，以及這些服務在執行時的行為。</span><span class="sxs-lookup"><span data-stu-id="524ed-110">You use them to control which services are run and how those services behave while running.</span></span> <span data-ttu-id="524ed-111">它們在您的專案中是儲存為 [ScriptableObject](https://docs.unity3d.com/Manual/class-ScriptableObject.html) 資產。</span><span class="sxs-lookup"><span data-stu-id="524ed-111">They're stored as [ScriptableObject](https://docs.unity3d.com/Manual/class-ScriptableObject.html) assets in your project.</span></span> <span data-ttu-id="524ed-112">您可以在 [專案] 視窗中選取設定檔來加以查看和編輯。</span><span class="sxs-lookup"><span data-stu-id="524ed-112">You can view and edit a profile by selecting it in your project window.</span></span>

<span data-ttu-id="524ed-113">例如，MRTK 有一個攝影機服務，這會根據顯示器是否為透明而定，將不同的屬性套用至主要相機 (例如 HoloLens) 或不透明 (例如 VR 耳機) 的情況。</span><span class="sxs-lookup"><span data-stu-id="524ed-113">For example, the MRTK has a camera service, which will apply different properties to the main camera, depending on whether or not the display is transparent (like in the case of a HoloLens) or opaque (like in the case of a VR headset).</span></span> <span data-ttu-id="524ed-114">攝影機服務會獲得 [相機設定檔](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Assets/MixedRealityToolkit/Definitions/MixedRealityCameraProfile.cs)，其中包含不同的透明與不透明的設定。</span><span class="sxs-lookup"><span data-stu-id="524ed-114">The camera service is given a [camera profile](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Assets/MixedRealityToolkit/Definitions/MixedRealityCameraProfile.cs), which contains those different transparent vs. opaque settings.</span></span>

<span data-ttu-id="524ed-115">更複雜的設定檔範例是 [InputSystem](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Assets/MixedRealityToolkit/Definitions/InputSystem/MixedRealityInputSystemProfile.cs)。</span><span class="sxs-lookup"><span data-stu-id="524ed-115">An example of a more complex profile is the the [InputSystem](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Assets/MixedRealityToolkit/Definitions/InputSystem/MixedRealityInputSystemProfile.cs).</span></span>
<span data-ttu-id="524ed-116">該設定檔上的部分屬性 (例如 MixedRealityInputDataProviderConfiguration 實體) 控制將在執行時間具現化的物件，這是輸入系統知道如何建立 OpenVR、WMR 和 Unity 輸入子系統的方式。</span><span class="sxs-lookup"><span data-stu-id="524ed-116">Some of the properties on that profile (such as the MixedRealityInputDataProviderConfiguration entities) control the objects that will be instantiated at runtime - this is how the input system knows how to create OpenVR, WMR and Unity input subsystems.</span></span> <span data-ttu-id="524ed-117">此設定檔不只是一組屬性，可設定是否啟用或停用特定的輸入子功能，這也是 MRTK 在執行時間用來「新增」其他類別的插入機制 (例如，輸入系統設定檔包含具有序列化型別資訊的「輸入資料提供者」清單。這些物件是由輸入系統在執行時間具現化的) </span><span class="sxs-lookup"><span data-stu-id="524ed-117">This profile is not just a set of properties that configures if a particular input sub-feature is enabled or disabled - it's also an injection mechanism that the MRTK will use to "new" other classes at runtime (for example, the input system profile contains a list of 'Input Data Providers' which has serialized type information - these objects are instantiated by the input system at runtime)</span></span>

<span data-ttu-id="524ed-118">設定檔設定一開始會呈現灰色，因為它們是使用 MRTK 的預設設定檔來設定的。</span><span class="sxs-lookup"><span data-stu-id="524ed-118">Profile configurations are initially greyed out because they're set up with MRTK's default profiles.</span></span>
<span data-ttu-id="524ed-119">它們只能在複製之後修改，以確保自訂的設定檔在 MRTK 版本更新之後不會遺失。</span><span class="sxs-lookup"><span data-stu-id="524ed-119">They can only be modified after cloning to ensure that customized profiles won't be lost after a MRTK version update.</span></span>

## <a name="modifying-profiles"></a><span data-ttu-id="524ed-120">修改設定檔</span><span class="sxs-lookup"><span data-stu-id="524ed-120">Modifying profiles</span></span>

<span data-ttu-id="524ed-121">雖然您可以藉由前往 ScriptableObject) 的序列化資產來個別修改設定檔 (，但是通常會透過根 MixedRealityToolkit 場景物件的 MRTK 偵測器來存取設定檔。</span><span class="sxs-lookup"><span data-stu-id="524ed-121">While profiles can be individually modified (by going to the serialized asset of the ScriptableObject), they are generally accessed through the MRTK inspector of the root MixedRealityToolkit scene object.</span></span>

![設定檔](../features/Images/Profiles/input_profile.png)

<span data-ttu-id="524ed-123">上圖顯示大量的設定-請注意，左側的每個選項都會顯示其對應服務的設定。</span><span class="sxs-lookup"><span data-stu-id="524ed-123">The picture above shows the sheer volume of settings - note that each option on the left will show the configuration for its corresponding service.</span></span>

### <a name="camera"></a><span data-ttu-id="524ed-124">相機</span><span class="sxs-lookup"><span data-stu-id="524ed-124">Camera</span></span>

<span data-ttu-id="524ed-125">包含每個顯示類型的設定。</span><span class="sxs-lookup"><span data-stu-id="524ed-125">Contains per-display type settings.</span></span> <span data-ttu-id="524ed-126">用來根據應用程式執行所在的顯示類型，套用不同層級的品質、剪輯和轉譯設定 (也就是 AR 與 VR) 。</span><span class="sxs-lookup"><span data-stu-id="524ed-126">Used to apply different levels of quality, clip, and rendering settings based on the type of display that the application is run on (i.e. AR vs VR).</span></span>

### <a name="input"></a><span data-ttu-id="524ed-127">輸入</span><span class="sxs-lookup"><span data-stu-id="524ed-127">Input</span></span>

<span data-ttu-id="524ed-128">MRTK 最複雜子系統的最大設定檔。</span><span class="sxs-lookup"><span data-stu-id="524ed-128">The largest profile for the most complex subsystem of the MRTK.</span></span> <span data-ttu-id="524ed-129">輸入 [系統](InputSystem/Terminology.md) 檔本身將涵蓋輸入的各種子系統。</span><span class="sxs-lookup"><span data-stu-id="524ed-129">The various subsystems of input will be covered in the [Input System](InputSystem/Terminology.md) documentation itself.</span></span>

### <a name="teleport"></a><span data-ttu-id="524ed-130">傳送</span><span class="sxs-lookup"><span data-stu-id="524ed-130">Teleport</span></span>

<span data-ttu-id="524ed-131">此設定檔會控制遙傳系統的運作方式，而這主要是 VR 的概念。</span><span class="sxs-lookup"><span data-stu-id="524ed-131">This profile controls how the teleportation system works, which is primarily a VR concept.</span></span>

### <a name="spatial-mapping"></a><span data-ttu-id="524ed-132">空間對應</span><span class="sxs-lookup"><span data-stu-id="524ed-132">Spatial mapping</span></span>

<span data-ttu-id="524ed-133">此設定檔會控制空間網格系統的運作方式 (亦即，此系統負責啟動系統，以在 AR 裝置) 上轉譯空間網格。</span><span class="sxs-lookup"><span data-stu-id="524ed-133">This profile controls how the spatial mesh system works (i.e. this system is responsible for starting the system that will render the spatial meshes on an AR device).</span></span> <span data-ttu-id="524ed-134">主要是 AR 概念。</span><span class="sxs-lookup"><span data-stu-id="524ed-134">Primarily an AR concept.</span></span>

### <a name="diagnostics"></a><span data-ttu-id="524ed-135">診斷</span><span class="sxs-lookup"><span data-stu-id="524ed-135">Diagnostics</span></span>

<span data-ttu-id="524ed-136">這會控制顯示畫面播放速率計數器的視覺化效能工具，以及基本的記憶體使用量。</span><span class="sxs-lookup"><span data-stu-id="524ed-136">This controls the visual performance tool that shows a framerate counter, along with basic memory utilization.</span></span>

### <a name="scene-system"></a><span data-ttu-id="524ed-137">場景系統</span><span class="sxs-lookup"><span data-stu-id="524ed-137">Scene system</span></span>

<span data-ttu-id="524ed-138">這會控制目前未啟用預設的系統，其設計目的是要讓多場景案例更容易使用。</span><span class="sxs-lookup"><span data-stu-id="524ed-138">This controls a currently not-enabled-by-default system that is designed to make multi-scene scenarios easier to work with.</span></span>

### <a name="extensions"></a><span data-ttu-id="524ed-139">延伸模組</span><span class="sxs-lookup"><span data-stu-id="524ed-139">Extensions</span></span>

<span data-ttu-id="524ed-140">這個預設的預設設定檔是可供取用者寫入的擴充點，然後插入其本身的物件，MRTK 執行時間會將其具現化並執行。</span><span class="sxs-lookup"><span data-stu-id="524ed-140">This empty-by-default profile is the extension point where consumers can write and then plug in their own objects that will be instantiated and run by the MRTK runtime.</span></span>

### <a name="editor"></a><span data-ttu-id="524ed-141">編輯器</span><span class="sxs-lookup"><span data-stu-id="524ed-141">Editor</span></span>

<span data-ttu-id="524ed-142">包含 MRTK 的僅限編輯器行為的一般設定。</span><span class="sxs-lookup"><span data-stu-id="524ed-142">Contains general settings for editor-only behaviors of the MRTK.</span></span>
