---
title: 場景系統場景類型
description: MRTK 中不同場景類型的檔
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: 06bfd1dbad3986044f099510c2de4d36cda50fc0
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144577"
---
# <a name="scene-types"></a><span data-ttu-id="9dc38-104">場景類型</span><span class="sxs-lookup"><span data-stu-id="9dc38-104">Scene types</span></span>

<span data-ttu-id="9dc38-105">場景已分成三種類型，而且每種類型都有不同的函式。</span><span class="sxs-lookup"><span data-stu-id="9dc38-105">Scenes have been divided into three types, and each type has a different function.</span></span>

![階層中的場景系統](../images/scene-system/MRTK_SceneSystemEditorSceneHierarchy.PNG)

## <a name="content-scenes"></a><span data-ttu-id="9dc38-107">內容場景</span><span class="sxs-lookup"><span data-stu-id="9dc38-107">Content scenes</span></span>

<span data-ttu-id="9dc38-108">這些是您用來處理的場景。</span><span class="sxs-lookup"><span data-stu-id="9dc38-108">These are the scenes you're used to dealing with.</span></span> <span data-ttu-id="9dc38-109">任何種類的內容都可以儲存在其中，而且可以任何組合載入或卸載。</span><span class="sxs-lookup"><span data-stu-id="9dc38-109">Any kind of content can be stored in them, and they can be loaded or unloaded in any combination.</span></span>

<span data-ttu-id="9dc38-110">預設會啟用內容幕後。</span><span class="sxs-lookup"><span data-stu-id="9dc38-110">Content scenes are enabled by default.</span></span> <span data-ttu-id="9dc38-111">您設定檔陣列中包含的任何場景 `Content Scenes` 都可以由服務載入/卸載。</span><span class="sxs-lookup"><span data-stu-id="9dc38-111">Any scenes included in your profile's `Content Scenes` array can be loaded / unloaded by the service.</span></span>

___

## <a name="manager-scenes"></a><span data-ttu-id="9dc38-112">管理員場景</span><span class="sxs-lookup"><span data-stu-id="9dc38-112">Manager scenes</span></span>

<span data-ttu-id="9dc38-113">具有必要 MixedRealityToolkit 實例的單一場景。</span><span class="sxs-lookup"><span data-stu-id="9dc38-113">A single scene with a required MixedRealityToolkit instance.</span></span> <span data-ttu-id="9dc38-114">這個場景會在啟動時先載入，並且會在應用程式存留期內維持載入狀態。</span><span class="sxs-lookup"><span data-stu-id="9dc38-114">This scene will be loaded first on launch and will remain loaded for the lifetime of the app.</span></span> <span data-ttu-id="9dc38-115">管理員場景也可以裝載不應終結的其他物件。</span><span class="sxs-lookup"><span data-stu-id="9dc38-115">The manager scene can also host other objects that should never be destroyed.</span></span> <span data-ttu-id="9dc38-116">這是 DontDestroyOnLoad 的慣用替代方法。</span><span class="sxs-lookup"><span data-stu-id="9dc38-116">This is the preferred alternative to DontDestroyOnLoad.</span></span>

<span data-ttu-id="9dc38-117">若要啟用這項功能，請簽 `Use Manager Scene` 入您的設定檔，並將場景物件拖曳到 `Manager Scene` 欄位中。</span><span class="sxs-lookup"><span data-stu-id="9dc38-117">To enable this feature, check `Use Manager Scene` in your profile and drag a scene object into the `Manager Scene` field.</span></span>

___

## <a name="lighting-scenes"></a><span data-ttu-id="9dc38-118">燈光場景</span><span class="sxs-lookup"><span data-stu-id="9dc38-118">Lighting scenes</span></span>

<span data-ttu-id="9dc38-119">一組用來儲存光源資訊和光源物件的場景。</span><span class="sxs-lookup"><span data-stu-id="9dc38-119">A set of scenes which store lighting information and lighting objects.</span></span> <span data-ttu-id="9dc38-120">一次只能載入一個，而其設定可以在載入時混合，以進行平滑的光源轉換。</span><span class="sxs-lookup"><span data-stu-id="9dc38-120">Only one can be loaded at a time, and their settings can be blended during loads for smooth lighting transitions.</span></span>

<span data-ttu-id="9dc38-121">Unity 的光源設定-環境光源、skyboxes 等，在使用加法式載入時，可能難以管理，因為它們會系結至個別的場景，而覆寫行為則不直接。</span><span class="sxs-lookup"><span data-stu-id="9dc38-121">Unity's lighting settings - ambient light, skyboxes, etc - can be tricky to manage when using additive loading because they're tied to individual scenes and override behavior is not straightforward.</span></span> <span data-ttu-id="9dc38-122">在實務上，如果在執行時間未取得的照明條件中撰寫資產，則會造成混淆。</span><span class="sxs-lookup"><span data-stu-id="9dc38-122">In practice this can cause confusion when assets are authored in lighting conditions that don't obtain at runtime.</span></span>

![場景系統光源設定](../images/scene-system/MRTK_SceneSystemLightingSettings.PNG)

<span data-ttu-id="9dc38-124">場景系統會使用光源來確保無論在編輯模式中和在播放模式中，這些設定都維持一致。</span><span class="sxs-lookup"><span data-stu-id="9dc38-124">The Scene System uses lighting scenes to ensure that these settings remain consistent regardless of what scenes are loaded or active, both in edit mode and in play mode.</span></span>

<span data-ttu-id="9dc38-125">若要啟用這項功能，請簽 `Use Lighting Scene` 入您的設定檔並填入 `Lighting Scenes` 陣列。</span><span class="sxs-lookup"><span data-stu-id="9dc38-125">To enable this feature, check `Use Lighting Scene` in your profile and populate the `Lighting Scenes` array.</span></span>

### <a name="cached-lighting-settings"></a><span data-ttu-id="9dc38-126">快取光源設定</span><span class="sxs-lookup"><span data-stu-id="9dc38-126">Cached lighting settings</span></span>

<span data-ttu-id="9dc38-127">您的設定檔會儲存光源設定的快取複本，並保留在燈光場景中。</span><span class="sxs-lookup"><span data-stu-id="9dc38-127">Your profile stores cached copies of the lighting settings kept in your lighting scenes.</span></span> <span data-ttu-id="9dc38-128">如果這些設定在您的燈光場景中變更，您將需要更新快取，以確保光源在播放模式中如預期般顯示。</span><span class="sxs-lookup"><span data-stu-id="9dc38-128">If those settings change in your lighting scenes, you will need to update your cache to ensure lighting appears as expected in play mode.</span></span> <span data-ttu-id="9dc38-129">當您的設定檔懷疑快取設定已過期時，就會顯示警告。</span><span class="sxs-lookup"><span data-stu-id="9dc38-129">Your profile will display a warning when it suspects your cached settings are out of date.</span></span> <span data-ttu-id="9dc38-130">按一下 `Update Cached Lighting Settings` 會載入每個光源場景、將其設定解壓縮，然後將它們儲存在您的設定檔中。</span><span class="sxs-lookup"><span data-stu-id="9dc38-130">Clicking `Update Cached Lighting Settings` will load each of your lighting scenes, extract their settings, then store them in your profile.</span></span>

![場景系統快取光源設定](../images/scene-system/MRTK_SceneSystemCachedLightingSettings.PNG)

### <a name="editor-behavior"></a><span data-ttu-id="9dc38-132">編輯器行為</span><span class="sxs-lookup"><span data-stu-id="9dc38-132">Editor behavior</span></span>

<span data-ttu-id="9dc38-133">使用燈光場景的其中一個優點是，在編輯時，您的內容會正確地發亮。</span><span class="sxs-lookup"><span data-stu-id="9dc38-133">One benefit of using lighting scenes is knowing your content is lit correctly while editing.</span></span> <span data-ttu-id="9dc38-134">為了達到這個目的，場景服務會隨時載入燈光場景，並將該場景的光源設定複製到目前使用中的場景。\*</span><span class="sxs-lookup"><span data-stu-id="9dc38-134">To this end, the Scene Service will keep a lighting scene loaded at all times, and will copy that scene's lighting settings to the current active scene.\*</span></span>

<span data-ttu-id="9dc38-135">您可以藉由開啟場景系統的[服務偵測器](../../configuration/mixed-reality-configuration-guide.md#editor-utilities)來變更所載入的燈光場景。</span><span class="sxs-lookup"><span data-stu-id="9dc38-135">You can change which lighting scene is loaded by opening the Scene System's [service inspector.](../../configuration/mixed-reality-configuration-guide.md#editor-utilities)</span></span> <span data-ttu-id="9dc38-136">在編輯模式中，您可以立即在燈光場景之間轉換。</span><span class="sxs-lookup"><span data-stu-id="9dc38-136">In edit mode you can instantaneously transition between lighting scenes.</span></span> <span data-ttu-id="9dc38-137">在 [播放] 模式中，您可以預覽轉換。</span><span class="sxs-lookup"><span data-stu-id="9dc38-137">In play mode, you can preview transitions.</span></span>

![場景系統偵測器](../images/scene-system/MRTK_SceneSystemServiceInspector.PNG)

<span data-ttu-id="9dc38-139">\**注意：使用中場景通常會判斷編輯器中的光源設定。不過，我們選擇不使用這項功能來強制執行光源設定，因為使用中的場景也是新建立的物件預設放置位置，而光源場景則只允許包含光源元件。相反地，目前光源場景的設定會自動複製到使用中場景的設定。請記住，這會導致內容場景的光源設定過度寫入。*</span><span class="sxs-lookup"><span data-stu-id="9dc38-139">\**Note: Typically the active scene determines your lighting settings in editor. However we choose not to use this feature to enforce lighting settings, because the active scene is also where newly created objects are placed by default, and lighting scenes are only permitted to contain lighting components. Instead, the current lighting scene's settings are automatically copied to the active scene's settings instead. Keep in mind that this will result in your content scene's lighting settings being over-written.*</span></span>
