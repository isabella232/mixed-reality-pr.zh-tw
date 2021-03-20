---
title: ExampleHub
description: MRTK 中的範例場景總覽
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: 4f55718e0fe9bebca2ff9e2850057e83a3f4b6bb
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104681821"
---
# <a name="mrtk-examples-hub"></a><span data-ttu-id="08113-104">MRTK 範例中樞</span><span class="sxs-lookup"><span data-stu-id="08113-104">MRTK Examples Hub</span></span>

![MRTK 範例中樞](../images/examples-hub/MRTK_ExamplesHub.png)

<span data-ttu-id="08113-106">MRTK 範例中樞是 Unity 場景，可讓您輕鬆體驗多個場景。</span><span class="sxs-lookup"><span data-stu-id="08113-106">MRTK Examples Hub is a Unity scene that makes it easy to experience multiple scenes.</span></span> <span data-ttu-id="08113-107">它會使用 MRTK 的場景系統來載入 & 卸載幕後。</span><span class="sxs-lookup"><span data-stu-id="08113-107">It uses MRTK's Scene System to load & unload the scenes.</span></span>

<span data-ttu-id="08113-108">**MRTKExamplesHub** 是具有共用元件（包括和）的容器場景 ``MixedRealityToolkit`` 。 ``MixedRealityPlayspace``</span><span class="sxs-lookup"><span data-stu-id="08113-108">**MRTKExamplesHub.unity** is the container scene that has shared components including ``MixedRealityToolkit`` and ``MixedRealityPlayspace``.</span></span> <span data-ttu-id="08113-109">**MRTKExamplesHubMainMenu： unity** 場景具有 cube 按鈕。</span><span class="sxs-lookup"><span data-stu-id="08113-109">**MRTKExamplesHubMainMenu.unity** scene has the cube buttons.</span></span>

## <a name="prerequisite"></a><span data-ttu-id="08113-110">必要條件</span><span class="sxs-lookup"><span data-stu-id="08113-110">Prerequisite</span></span>

<span data-ttu-id="08113-111">MRTK 範例中樞使用 [場景轉換服務](../extensions/scene-transition-service.md) 和相關的腳本。</span><span class="sxs-lookup"><span data-stu-id="08113-111">MRTK Examples Hub uses [Scene Transition Service](../extensions/scene-transition-service.md) and related scripts.</span></span> <span data-ttu-id="08113-112">如果您是透過 Unity 套件使用 MRTK，請匯入 MixedReality 的 [發行套件](https://github.com/microsoft/MixedRealityToolkit-Unity/releases)中所包含的 node.js.. x. **unitypackage** 。</span><span class="sxs-lookup"><span data-stu-id="08113-112">If you are using MRTK through Unity packages, please import **Microsoft.MixedReality.Toolkit.Unity.Extensions.x.x.x.unitypackage** which is part of the [release packages](https://github.com/microsoft/MixedRealityToolkit-Unity/releases).</span></span> <span data-ttu-id="08113-113">如果您是透過儲存機制複製來使用 MRTK，您的專案中應該已經有 **MRTK/Extensions** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="08113-113">If you are using MRTK through the repository clone, you should already have the **MRTK/Extensions** folder in your project.</span></span>

## <a name="mrtkexampleshub-scene-and-the-scene-system"></a><span data-ttu-id="08113-114">MRTKExamplesHub 場景和場景系統</span><span class="sxs-lookup"><span data-stu-id="08113-114">MRTKExamplesHub scene and the scene system</span></span>

<span data-ttu-id="08113-115">開啟 **MRTKExamplesHub** ，其位於 `MRTK/Examples/Experimental/Demos/ExamplesHub/Scenes/` MixedRealityToolkit、MixedRealityPlayspace 和 LoadHubOnStartup 的空白場景中。</span><span class="sxs-lookup"><span data-stu-id="08113-115">Open **MRTKExamplesHub.unity** which is located at `MRTK/Examples/Experimental/Demos/ExamplesHub/Scenes/` It is an empty scene with MixedRealityToolkit, MixedRealityPlayspace and LoadHubOnStartup.</span></span> <span data-ttu-id="08113-116">此場景已設定為使用 MRTK 的場景系統。</span><span class="sxs-lookup"><span data-stu-id="08113-116">This scene is configured to use MRTK's Scene System.</span></span> <span data-ttu-id="08113-117">按一下 [MixedRealityToolkit] 底下的 [] `MixedRealitySceneSystem` 。</span><span class="sxs-lookup"><span data-stu-id="08113-117">Click `MixedRealitySceneSystem` under MixedRealityToolkit.</span></span> <span data-ttu-id="08113-118">它會在 [偵測器] 面板中顯示場景系統的資訊。</span><span class="sxs-lookup"><span data-stu-id="08113-118">It will display the Scene System's information in the Inspector panel.</span></span>

<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_Hierarchy.png" width="300" alt="Example Hub Hierarchy">
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_Inspector1.png" width="450" alt="Inspector 1">

<span data-ttu-id="08113-119">在偵測器底部，會顯示場景系統設定檔中定義的場景清單。</span><span class="sxs-lookup"><span data-stu-id="08113-119">On the bottom of the Inspector, it displays the list of the scenes defined in the Scene System Profile.</span></span> <span data-ttu-id="08113-120">您可以按一下場景名稱以載入/卸載它們。</span><span class="sxs-lookup"><span data-stu-id="08113-120">You can click the scene names to load/unload them.</span></span>

<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_Inspector2.png" width="550" alt="Inspector 2">
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem3.png" alt="Scene system 3"><span data-ttu-id="08113-121">按一下清單中的場景名稱載入 _MRTKExamplesHub_ 場景的範例。</span><span class="sxs-lookup"><span data-stu-id="08113-121">Example of loading _MRTKExamplesHub_ scene by clicking the scene name in the list.</span></span>
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem4.png" alt="Scene system 4"><span data-ttu-id="08113-122">載入 _HandInteractionExamples_ 場景的範例。</span><span class="sxs-lookup"><span data-stu-id="08113-122">Example of loading _HandInteractionExamples_ scene.</span></span>
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem5.png" alt="Scene system 5">
<span data-ttu-id="08113-123">載入多個場景的範例。</span><span class="sxs-lookup"><span data-stu-id="08113-123">Example of loading multiple scenes.</span></span>

## <a name="running-the-scene"></a><span data-ttu-id="08113-124">執行場景</span><span class="sxs-lookup"><span data-stu-id="08113-124">Running the scene</span></span>

<span data-ttu-id="08113-125">此場景適用于 Unity 的遊戲模式和裝置。</span><span class="sxs-lookup"><span data-stu-id="08113-125">The scene works in both Unity's game mode and on device.</span></span> <span data-ttu-id="08113-126">在 Unity 編輯器中執行 **MRTKExamplesHub** 場景，並使用 MRTK 的輸入模擬來與場景內容互動。</span><span class="sxs-lookup"><span data-stu-id="08113-126">Run the **MRTKExamplesHub** scene in the Unity editor and use MRTK's input simulation to interact with the scene contents.</span></span> <span data-ttu-id="08113-127">若要建立和部署，只要使用場景系統清單中所包含的其他場景來建立 **MRTKExamplesHub** 場景即可。</span><span class="sxs-lookup"><span data-stu-id="08113-127">To build and deploy, simply build **MRTKExamplesHub** scene with other scenes that are included in the Scene System's list.</span></span> <span data-ttu-id="08113-128">偵測器也可讓您輕鬆地將場景新增至組建設定。</span><span class="sxs-lookup"><span data-stu-id="08113-128">The inspector also makes it easy to add scenes to the Build Settings.</span></span> <span data-ttu-id="08113-129">在 [建築設定] 中，確定 **MRTKExamplesHub** 場景位於清單的最上方（索引0）。</span><span class="sxs-lookup"><span data-stu-id="08113-129">In the Building Settings, make sure **MRTKExamplesHub** scene is on the top of the list at index 0.</span></span>

<img src="../images/examples-hub/MRTK_ExamplesHub_BuildSettings.png" width="450" alt="Build settings">

## <a name="how-mrtkexampleshub-loads-a-scene"></a><span data-ttu-id="08113-130">MRTKExamplesHub 如何載入場景</span><span class="sxs-lookup"><span data-stu-id="08113-130">How MRTKExamplesHub loads a scene</span></span>

<span data-ttu-id="08113-131">在 **MRTKExamplesHub** 場景中，您可以找到 ``ExamplesHubButton`` 預製專案。</span><span class="sxs-lookup"><span data-stu-id="08113-131">In the **MRTKExamplesHub** scene, you can find the ``ExamplesHubButton`` prefab.</span></span>
<span data-ttu-id="08113-132">預製專案中有一個 **FrontPlate** 物件，其中包含 ``Interactable`` 。</span><span class="sxs-lookup"><span data-stu-id="08113-132">There is a **FrontPlate** object in the prefab which contains ``Interactable``.</span></span>
<span data-ttu-id="08113-133">使用互動的 ``OnClick()`` 和 ``OnTouch()`` 事件，它會觸發 **LoadContentScene** 腳本的 **LoadContent ()** 函式。</span><span class="sxs-lookup"><span data-stu-id="08113-133">Using the Interactable's ``OnClick()`` and ``OnTouch()`` event, it triggers the **LoadContentScene** script's **LoadContent()** function.</span></span>
<span data-ttu-id="08113-134">在 **LoadContentScene** 腳本的偵測器中，您可以定義要載入的場景名稱。</span><span class="sxs-lookup"><span data-stu-id="08113-134">In the **LoadContentScene** script's Inspector, you can define the scene name to load.</span></span>

<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem6.png" alt="Scene system 6">
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem8.png" width="450" alt="Scene System 8">
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem7.png" width="450" alt="Scene System 7">

<span data-ttu-id="08113-135">腳本會使用場景系統的 LoadContent () 函式來載入場景。</span><span class="sxs-lookup"><span data-stu-id="08113-135">The script uses the Scene System's LoadContent() function to load the scene.</span></span>
<span data-ttu-id="08113-136">如需詳細資訊，請參閱 [場景系統](../scene-system/scene-system-getting-started.md) 頁面。</span><span class="sxs-lookup"><span data-stu-id="08113-136">Please refer to the [Scene System](../scene-system/scene-system-getting-started.md) page for more details.</span></span>

```c#
MixedRealityToolkit.SceneSystem.LoadContent(contentName, loadSceneMode);
```

## <a name="returning-to-the-main-menu-scene"></a><span data-ttu-id="08113-137">返回主功能表場景</span><span class="sxs-lookup"><span data-stu-id="08113-137">Returning to the main menu scene</span></span>

<span data-ttu-id="08113-138">若要返回主功能表場景 (MRTKExamplesHubMainMenu 場景) ，您可以使用相同的場景系統 `LoadContent()` 方法。</span><span class="sxs-lookup"><span data-stu-id="08113-138">To return to the main menu scene (MRTKExamplesHubMainMenu scene), you can use the same Scene System `LoadContent()` method.</span></span> <span data-ttu-id="08113-139">**ToggleFeaturesPanelExamplesHub. 預製專案** 會提供包含 **LoadContentScene** 腳本的 [Home （首頁）] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="08113-139">The **ToggleFeaturesPanelExamplesHub.prefab** provides the 'Home' button which contains the **LoadContentScene** script.</span></span> <span data-ttu-id="08113-140">您可以使用此預製專案，或在每個場景中提供自訂的 [首頁] 按鈕，以允許使用者返回主要場景。</span><span class="sxs-lookup"><span data-stu-id="08113-140">Use this prefab or provide a custom home button in each scene to allow the user to return to the main scene.</span></span> <span data-ttu-id="08113-141">您可以將 **ToggleFeaturesPanelExamplesHub 預製專案** 在 **MRTKExamplesHub** 場景中，讓它永遠可見，因為 **MRTKExamplesHub** 是共用的容器場景。</span><span class="sxs-lookup"><span data-stu-id="08113-141">One can put the **ToggleFeaturesPanelExamplesHub.prefab** in the **MRTKExamplesHub** scene to make it always visible since **MRTKExamplesHub** is a shared container scene.</span></span> <span data-ttu-id="08113-142">請務必在每個範例場景中隱藏/停用 **ToggleFeaturesPanel。預製專案。**</span><span class="sxs-lookup"><span data-stu-id="08113-142">Make sure to hide/deactivate **ToggleFeaturesPanel.prefab** in each example scene.</span></span>

<img src="../images/examples-hub/MRTK_ExamplesHubToggleFeaturesPanel.png" alt="Toggle feature Panel">

<img src="../images/examples-hub/MRTK_ExamplesHubHomeButton.png" width="450" alt="Example Hub home button">

## <a name="adding-additional-buttons"></a><span data-ttu-id="08113-143">新增其他按鈕</span><span class="sxs-lookup"><span data-stu-id="08113-143">Adding additional buttons</span></span>

<span data-ttu-id="08113-144">在 **CubeCollection** 物件中，重複 (或新增) _ExampleHubButton_ prefabs，然後按一下中的 [ **更新集合** ] `GridObjectCollection` 。</span><span class="sxs-lookup"><span data-stu-id="08113-144">In the **CubeCollection** object, duplicate (or add) _ExampleHubButton_ prefabs and click **Update Collection** in the `GridObjectCollection`.</span></span>
<span data-ttu-id="08113-145">這會根據新的按鈕總數來更新圓柱版面配置。</span><span class="sxs-lookup"><span data-stu-id="08113-145">This will update the cylinder layout based on the new total number of buttons.</span></span>
<span data-ttu-id="08113-146">如需詳細資料，請參閱 [ [物件集合](../ux-building-blocks/object-collection.md) ] 頁面。</span><span class="sxs-lookup"><span data-stu-id="08113-146">Please refer to the [Object Collection](../ux-building-blocks/object-collection.md) page for more details.</span></span>

<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem9.png" alt="Scene System 9">
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem10.png" alt="Scene System 10">

<span data-ttu-id="08113-147">新增按鈕之後，請更新 **LoadContentScene** 腳本中的場景名稱， (上述) 所述。</span><span class="sxs-lookup"><span data-stu-id="08113-147">After adding the buttons, update the scene name in the **LoadContentScene** script(explained above).</span></span>
<span data-ttu-id="08113-148">將其他場景新增至場景系統的設定檔。</span><span class="sxs-lookup"><span data-stu-id="08113-148">Add additional scenes to the Scene System's profile.</span></span>
