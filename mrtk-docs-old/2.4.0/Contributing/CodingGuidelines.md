---
title: CodingGuidelines
description: 參與 MRTK 時要遵循的編碼準則和慣例。
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
ms.localizationpriority: medium
keywords: 'Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、c #、'
ms.openlocfilehash: fb32f3330b9f53978de5cc06cccbc47b3dd4b6b6
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104684431"
---
# <a name="coding-guidelines"></a><span data-ttu-id="14edc-104">程式碼撰寫指導方針</span><span class="sxs-lookup"><span data-stu-id="14edc-104">Coding guidelines</span></span>

<span data-ttu-id="14edc-105">本檔概述參與 MRTK 時要遵循的程式碼撰寫準則和慣例。</span><span class="sxs-lookup"><span data-stu-id="14edc-105">This document outlines coding principles and conventions to follow when contributing to MRTK.</span></span>

---

## <a name="philosophy"></a><span data-ttu-id="14edc-106">哲學</span><span class="sxs-lookup"><span data-stu-id="14edc-106">Philosophy</span></span>

### <a name="be-concise-and-strive-for-simplicity"></a><span data-ttu-id="14edc-107">簡潔且儘量簡化</span><span class="sxs-lookup"><span data-stu-id="14edc-107">Be concise and strive for simplicity</span></span>

<span data-ttu-id="14edc-108">最簡單的解決方案通常是最好的。</span><span class="sxs-lookup"><span data-stu-id="14edc-108">The simplest solution is often the best.</span></span> <span data-ttu-id="14edc-109">這是這些指導方針的覆寫目的，而且應該是所有程式碼撰寫活動的目標。</span><span class="sxs-lookup"><span data-stu-id="14edc-109">This is an overriding aim of these guidelines and should be the goal of all coding activity.</span></span> <span data-ttu-id="14edc-110">很簡單的部分很簡潔，而且與現有的程式碼一致。</span><span class="sxs-lookup"><span data-stu-id="14edc-110">Part of being simple is being concise, and consistent with existing code.</span></span> <span data-ttu-id="14edc-111">試著讓您的程式碼保持簡潔。</span><span class="sxs-lookup"><span data-stu-id="14edc-111">Try to keep your code simple.</span></span>

<span data-ttu-id="14edc-112">讀者應該只會遇到提供有用資訊的構件。</span><span class="sxs-lookup"><span data-stu-id="14edc-112">Readers should only encounter artifacts that provide useful information.</span></span> <span data-ttu-id="14edc-113">例如，重新聲明明顯內容的批註不會提供額外的資訊，也不會增加信號比例的雜訊。</span><span class="sxs-lookup"><span data-stu-id="14edc-113">For example, comments that restate what is obvious provide no extra information and increase the noise to signal ratio.</span></span>

<span data-ttu-id="14edc-114">讓程式碼邏輯保持簡易。</span><span class="sxs-lookup"><span data-stu-id="14edc-114">Keep code logic simple.</span></span> <span data-ttu-id="14edc-115">請注意，這並不是有關使用最少行數、將識別碼名稱或大括弧樣式的大小降到最低的語句，而是關於減少概念的數目，並透過熟悉的模式將它們的可見度最大化。</span><span class="sxs-lookup"><span data-stu-id="14edc-115">Note that this is not a statement about using the fewest number of lines, minimizing the size of identifier names or brace style, but about reducing the number of concepts and maximizing the visibility of those through familiar patterns.</span></span>

### <a name="produce-consistent-readable-code"></a><span data-ttu-id="14edc-116">產生一致且可讀取的程式碼</span><span class="sxs-lookup"><span data-stu-id="14edc-116">Produce consistent, readable code</span></span>

<span data-ttu-id="14edc-117">程式碼可讀性與低瑕疵率相關聯。</span><span class="sxs-lookup"><span data-stu-id="14edc-117">Code readability is correlated with low defect rates.</span></span> <span data-ttu-id="14edc-118">努力建立容易閱讀的程式碼。</span><span class="sxs-lookup"><span data-stu-id="14edc-118">Strive to create code that is easy to read.</span></span> <span data-ttu-id="14edc-119">努力建立具有簡單邏輯的程式碼，並重複使用現有的元件，因為它也會協助確保正確性。</span><span class="sxs-lookup"><span data-stu-id="14edc-119">Strive to create code that has simple logic and re-uses existing components as it will also help ensure correctness.</span></span>

<span data-ttu-id="14edc-120">您所產生之程式碼的所有詳細資料，從最基本的正確性詳細資料到一致的樣式和格式。</span><span class="sxs-lookup"><span data-stu-id="14edc-120">All details of the code you produce matter, from the most basic detail of correctness to consistent style and formatting.</span></span> <span data-ttu-id="14edc-121">保持您的程式碼樣式與已存在的樣式一致，即使它不符合您的喜好設定。</span><span class="sxs-lookup"><span data-stu-id="14edc-121">Keep your coding style consistent with what already exists, even if it is not matching your preference.</span></span> <span data-ttu-id="14edc-122">這會增加整體程式碼基底的可讀性。</span><span class="sxs-lookup"><span data-stu-id="14edc-122">This increases the readability of the overall codebase.</span></span>

### <a name="support-configuring-components-both-in-editor-and-at-run-time"></a><span data-ttu-id="14edc-123">支援在編輯器和執行時間設定元件</span><span class="sxs-lookup"><span data-stu-id="14edc-123">Support configuring components both in editor and at run-time</span></span>

<span data-ttu-id="14edc-124">MRTK 支援一組不同的使用者，也就是想要在 Unity 編輯器和 load prefabs 中設定元件的人員，以及需要在執行時間具現化和設定物件的人員。</span><span class="sxs-lookup"><span data-stu-id="14edc-124">MRTK supports a diverse set of users – people who prefer to configure components in the Unity editor and load prefabs, and people who need to instantiate and configure objects at run-time.</span></span>

<span data-ttu-id="14edc-125">您所有的程式碼都應可透過將元件新增至儲存場景中的 GameObject，以及在程式碼中具現化該元件的方式運作。</span><span class="sxs-lookup"><span data-stu-id="14edc-125">All your code should work by BOTH adding a component to a GameObject in a saved scene, and by instantiating that component in code.</span></span> <span data-ttu-id="14edc-126">測試應該包含用於具現化 prefabs 和具現化的測試案例，在執行時間設定元件。</span><span class="sxs-lookup"><span data-stu-id="14edc-126">Tests should include a test case both for instantiating prefabs and instantiating, configuring the component at runtime.</span></span>

### <a name="play-in-editor-is-your-first-and-primary-target-platform"></a><span data-ttu-id="14edc-127">內建編輯器是您的第一個和主要目標平臺</span><span class="sxs-lookup"><span data-stu-id="14edc-127">Play-in-editor is your first and primary target platform</span></span>

<span data-ttu-id="14edc-128">「內建編輯器」是在 Unity 中反覆運算的最快方式。</span><span class="sxs-lookup"><span data-stu-id="14edc-128">Play-In-Editor is the fastest way to iterate in Unity.</span></span> <span data-ttu-id="14edc-129">提供客戶快速反復執行的方式，讓他們能夠更快速地開發解決方案，並嘗試更多構想。</span><span class="sxs-lookup"><span data-stu-id="14edc-129">Providing ways for our customers to iterate quickly allows them to both develop solutions more quickly and try out more ideas.</span></span> <span data-ttu-id="14edc-130">換句話說，最大化反覆運算的速度可讓客戶達成更多目標。</span><span class="sxs-lookup"><span data-stu-id="14edc-130">In other words, maximizing the speed of iteration empowers our customers to achieve more.</span></span>

<span data-ttu-id="14edc-131">讓所有專案都能在編輯器中運作，然後讓它在其他任何平臺上運作。</span><span class="sxs-lookup"><span data-stu-id="14edc-131">Make everything work in editor, then make it work on any other platform.</span></span> <span data-ttu-id="14edc-132">在編輯器中保持運作。</span><span class="sxs-lookup"><span data-stu-id="14edc-132">Keep it working in the editor.</span></span> <span data-ttu-id="14edc-133">您可以輕鬆地將新平臺加入編輯器中。</span><span class="sxs-lookup"><span data-stu-id="14edc-133">It is easy to add a new platform to Play-In-Editor.</span></span> <span data-ttu-id="14edc-134">如果您的應用程式只能在裝置上運作，則很難讓使用中的編輯器運作。</span><span class="sxs-lookup"><span data-stu-id="14edc-134">It is very difficult to get Play-In-Editor working if your app only works on a device.</span></span>

### <a name="add-new-public-fields-properties-methods-and-serialized-private-fields-with-care"></a><span data-ttu-id="14edc-135">謹慎新增公用欄位、屬性、方法和序列化私用欄位</span><span class="sxs-lookup"><span data-stu-id="14edc-135">Add new public fields, properties, methods and serialized private fields with care</span></span>

<span data-ttu-id="14edc-136">每次新增公用方法（field，property）時，它就會成為 MRTK 公用 API 介面的一部分。</span><span class="sxs-lookup"><span data-stu-id="14edc-136">Every time you add a public method, field, property, it becomes part of MRTK’s public API surface.</span></span> <span data-ttu-id="14edc-137">標記為的私用欄位 `[SerializeField]` 也會將欄位公開給編輯器，而且是公用 API 介面的一部分。</span><span class="sxs-lookup"><span data-stu-id="14edc-137">Private fields marked with `[SerializeField]` also expose fields to the editor and are part of the public API surface.</span></span> <span data-ttu-id="14edc-138">其他人可能會使用該公用方法、使用您的公用欄位設定自訂 prefabs，並對其進行相依性。</span><span class="sxs-lookup"><span data-stu-id="14edc-138">Other people might use that public method, configure custom prefabs with your public field, and take a dependency on it.</span></span>

<span data-ttu-id="14edc-139">應謹慎檢查新的公用成員。</span><span class="sxs-lookup"><span data-stu-id="14edc-139">New public members should be carefully examined.</span></span> <span data-ttu-id="14edc-140">未來將需要維護任何公用欄位。</span><span class="sxs-lookup"><span data-stu-id="14edc-140">Any public field will need to be maintained in the future.</span></span> <span data-ttu-id="14edc-141">請記住，如果公用欄位的類型 (或序列化私用欄位) 變更或從 MonoBehaviour 中移除，這可能會中斷其他人。</span><span class="sxs-lookup"><span data-stu-id="14edc-141">Remember that if the type of a public field (or serialized private field) changes or gets removed from a MonoBehaviour, that could break other people.</span></span> <span data-ttu-id="14edc-142">欄位必須先淘汰才能發行，而且需要提供程式碼來遷移已取得相依性之人員的變更。</span><span class="sxs-lookup"><span data-stu-id="14edc-142">The field will need to first be deprecated for a release, and code to migrate changes for people that have taken dependencies would need to be provided.</span></span>

### <a name="prioritize-writing-tests"></a><span data-ttu-id="14edc-143">排定撰寫測試的優先順序</span><span class="sxs-lookup"><span data-stu-id="14edc-143">Prioritize writing tests</span></span>

<span data-ttu-id="14edc-144">MRTK 是一個由各種不同參與者所修改的社區專案。</span><span class="sxs-lookup"><span data-stu-id="14edc-144">MRTK is a community project, modified by a diverse range of contributors.</span></span> <span data-ttu-id="14edc-145">這些參與者可能不知道 bug 修正/功能的詳細資料，而且不小心中斷了您的功能。</span><span class="sxs-lookup"><span data-stu-id="14edc-145">These contributors may not know the details of your bug fix / feature, and accidentally break your feature.</span></span> <span data-ttu-id="14edc-146">MRTK 會在完成每個提取要求之前[執行持續整合測試](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_build?definitionId=16)。</span><span class="sxs-lookup"><span data-stu-id="14edc-146">[MRTK runs continuous integration tests](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_build?definitionId=16) before completing every pull request.</span></span> <span data-ttu-id="14edc-147">無法簽入中斷測試的變更。</span><span class="sxs-lookup"><span data-stu-id="14edc-147">Changes that break tests cannot be checked in.</span></span> <span data-ttu-id="14edc-148">因此，測試是確保其他人不會中斷您的功能的最佳方式。</span><span class="sxs-lookup"><span data-stu-id="14edc-148">Therefore, tests are the best way to ensure that other people do not break your feature.</span></span>

<span data-ttu-id="14edc-149">當您修正錯誤時，請撰寫測試，以確保它不會在未來回歸。</span><span class="sxs-lookup"><span data-stu-id="14edc-149">When you fix a bug, write a test to ensure it does not regress in the future.</span></span> <span data-ttu-id="14edc-150">如果加入功能，請撰寫可驗證您的功能運作的測試。</span><span class="sxs-lookup"><span data-stu-id="14edc-150">If adding a feature, write tests that verify your feature works.</span></span> <span data-ttu-id="14edc-151">這是實驗性功能以外所有 UX 功能的必要項。</span><span class="sxs-lookup"><span data-stu-id="14edc-151">This is required for all UX features except experimental features.</span></span>

## <a name="c-coding-conventions"></a><span data-ttu-id="14edc-152">C # 編碼慣例</span><span class="sxs-lookup"><span data-stu-id="14edc-152">C# Coding conventions</span></span>

### <a name="script-license-information-headers"></a><span data-ttu-id="14edc-153">腳本授權資訊標頭</span><span class="sxs-lookup"><span data-stu-id="14edc-153">Script license information headers</span></span>

<span data-ttu-id="14edc-154">所有參與新檔案的 Microsoft 員工都應該在任何新檔案的頂端新增下列標準授權標頭，完全如下所示：</span><span class="sxs-lookup"><span data-stu-id="14edc-154">All Microsoft employees contributing new files should add the following standard License header at the top of any new files, exactly as shown below:</span></span>

```c#
// Copyright (c) Microsoft Corporation.
// Licensed under the MIT License.
```

### <a name="function--method-summary-headers"></a><span data-ttu-id="14edc-155">函數/方法摘要標頭</span><span class="sxs-lookup"><span data-stu-id="14edc-155">Function / method summary headers</span></span>

<span data-ttu-id="14edc-156">張貼至 MRTK 的所有公用類別、結構、列舉、函式、屬性、欄位都應描述為其用途和使用，完全如下所示：</span><span class="sxs-lookup"><span data-stu-id="14edc-156">All public classes, structs, enums, functions, properties, fields posted to the MRTK should be described as to its purpose and use, exactly as shown below:</span></span>

```c#
/// <summary>
/// The Controller definition defines the Controller as defined by the SDK / Unity.
/// </summary>
public struct Controller
{
    /// <summary>
    /// The ID assigned to the Controller
    /// </summary>
    public string ID;
}
```

<span data-ttu-id="14edc-157">這可確保為所有類別、方法和屬性正確產生和簡易性檔。</span><span class="sxs-lookup"><span data-stu-id="14edc-157">This ensures documentation is properly generated and disseminated for all all classes, methods, and properties.</span></span>

<span data-ttu-id="14edc-158">任何未適當摘要標記提交的腳本檔案都會遭到拒絕。</span><span class="sxs-lookup"><span data-stu-id="14edc-158">Any script files submitted without proper summary tags will be rejected.</span></span>

### <a name="mrtk-namespace-rules"></a><span data-ttu-id="14edc-159">MRTK 命名空間規則</span><span class="sxs-lookup"><span data-stu-id="14edc-159">MRTK namespace rules</span></span>

<span data-ttu-id="14edc-160">「混合現實」工具組使用以功能為基礎的命名空間模型，其中所有基礎命名空間的開頭都是 "MixedReality"。</span><span class="sxs-lookup"><span data-stu-id="14edc-160">The Mixed Reality Toolkit uses a feature based namespace model, where all foundational namespaces begin with "Microsoft.MixedReality.Toolkit".</span></span> <span data-ttu-id="14edc-161">一般而言，您不需要在命名空間中指定工具組層 (例如： Core、Providers、Services) 。</span><span class="sxs-lookup"><span data-stu-id="14edc-161">In general, you need not specify the toolkit layer (ex: Core, Providers, Services) in your namespaces.</span></span>

<span data-ttu-id="14edc-162">目前定義的命名空間為：</span><span class="sxs-lookup"><span data-stu-id="14edc-162">The currently defined namespaces are:</span></span>

- <span data-ttu-id="14edc-163">MixedReality 工具組</span><span class="sxs-lookup"><span data-stu-id="14edc-163">Microsoft.MixedReality.Toolkit</span></span>
- <span data-ttu-id="14edc-164">MixedReality：界限</span><span class="sxs-lookup"><span data-stu-id="14edc-164">Microsoft.MixedReality.Toolkit.Boundary</span></span>
- <span data-ttu-id="14edc-165">MixedReality 工具組</span><span class="sxs-lookup"><span data-stu-id="14edc-165">Microsoft.MixedReality.Toolkit.Diagnostics</span></span>
- <span data-ttu-id="14edc-166">MixedReality 編輯工具</span><span class="sxs-lookup"><span data-stu-id="14edc-166">Microsoft.MixedReality.Toolkit.Editor</span></span>
- <span data-ttu-id="14edc-167">MixedReality。輸入</span><span class="sxs-lookup"><span data-stu-id="14edc-167">Microsoft.MixedReality.Toolkit.Input</span></span>
- <span data-ttu-id="14edc-168">MixedReality 工具組. SpatialAwareness</span><span class="sxs-lookup"><span data-stu-id="14edc-168">Microsoft.MixedReality.Toolkit.SpatialAwareness</span></span>
- <span data-ttu-id="14edc-169">MixedReality. 傳送工具</span><span class="sxs-lookup"><span data-stu-id="14edc-169">Microsoft.MixedReality.Toolkit.Teleport</span></span>
- <span data-ttu-id="14edc-170">MixedReality 工具組</span><span class="sxs-lookup"><span data-stu-id="14edc-170">Microsoft.MixedReality.Toolkit.Utilities</span></span>

<span data-ttu-id="14edc-171">對於具有大量類型的命名空間，可接受建立有限數目的子命名空間，以協助範圍使用。</span><span class="sxs-lookup"><span data-stu-id="14edc-171">For namespaces with a large amount of types, it is acceptable to create a limited number of sub-namespaces to aid in scoping usage.</span></span>

<span data-ttu-id="14edc-172">省略介面、類別或資料類型的命名空間，將會導致您的變更遭到封鎖。</span><span class="sxs-lookup"><span data-stu-id="14edc-172">Omitting the namespace for an interface, class or data type will cause your change to be blocked.</span></span>

### <a name="adding-new-monobehaviour-scripts"></a><span data-ttu-id="14edc-173">加入新的 MonoBehaviour 腳本</span><span class="sxs-lookup"><span data-stu-id="14edc-173">Adding new MonoBehaviour scripts</span></span>

<span data-ttu-id="14edc-174">使用提取要求新增 MonoBehaviour 腳本時，請確定 [`AddComponentMenu`](https://docs.unity3d.com/ScriptReference/AddComponentMenu.html) 屬性已套用至所有適用的檔案。</span><span class="sxs-lookup"><span data-stu-id="14edc-174">When adding new MonoBehaviour scripts with a pull request, ensure the [`AddComponentMenu`](https://docs.unity3d.com/ScriptReference/AddComponentMenu.html) attribute is applied to all applicable files.</span></span> <span data-ttu-id="14edc-175">這可確保在編輯器的 [ *新增元件* ] 按鈕下，可輕鬆找到元件。</span><span class="sxs-lookup"><span data-stu-id="14edc-175">This ensures the component is easily discoverable in the editor under the *Add Component* button.</span></span> <span data-ttu-id="14edc-176">如果元件無法顯示在編輯器（例如抽象類別）中，則不需要屬性旗標。</span><span class="sxs-lookup"><span data-stu-id="14edc-176">The attribute flag is not necessary if the component cannot show up in editor such as an abstract class.</span></span>

<span data-ttu-id="14edc-177">在下列範例中，您應該使用元件的套件位置填入 *套件* 。</span><span class="sxs-lookup"><span data-stu-id="14edc-177">In the example below, the *Package here* should be filled with the package location of the component.</span></span> <span data-ttu-id="14edc-178">如果將專案放在 *MRTK/SDK* 資料夾中，則套件將會是 *SDK*。</span><span class="sxs-lookup"><span data-stu-id="14edc-178">If placing an item in *MRTK/SDK* folder, then the package will be *SDK*.</span></span>

```c#
[AddComponentMenu("Scripts/MRTK/{Package here}/MyNewComponent")]
public class MyNewComponent : MonoBehaviour
```

### <a name="adding-new-unity-inspector-scripts"></a><span data-ttu-id="14edc-179">新增 Unity inspector 腳本</span><span class="sxs-lookup"><span data-stu-id="14edc-179">Adding new Unity inspector scripts</span></span>

<span data-ttu-id="14edc-180">一般情況下，請嘗試避免建立 MRTK 元件的自訂偵測器腳本。</span><span class="sxs-lookup"><span data-stu-id="14edc-180">In general, try to avoid creating custom inspector scripts for MRTK components.</span></span> <span data-ttu-id="14edc-181">它增加了可由 Unity 引擎處理的程式碼基底額外負荷和管理。</span><span class="sxs-lookup"><span data-stu-id="14edc-181">It adds additional overhead and management of the codebase that could be handled by the Unity engine.</span></span>

<span data-ttu-id="14edc-182">如果需要偵測器類別，請嘗試使用 Unity [`DrawDefaultInspector()`](https://docs.unity3d.com/ScriptReference/Editor.DrawDefaultInspector.html) 。</span><span class="sxs-lookup"><span data-stu-id="14edc-182">If an inspector class is necessary, try to use Unity's [`DrawDefaultInspector()`](https://docs.unity3d.com/ScriptReference/Editor.DrawDefaultInspector.html).</span></span> <span data-ttu-id="14edc-183">這會再次簡化偵測器類別，並將大部分的工作保留在 Unity 中。</span><span class="sxs-lookup"><span data-stu-id="14edc-183">This again simplifies the inspector class and leaves much of the work to Unity.</span></span>

```c#
public override void OnInspectorGUI()
{
    // Do some custom calculations or checks
    // ....
    DrawDefaultInspector();
}
```

<span data-ttu-id="14edc-184">如果在偵測器類別中需要自訂轉譯，請嘗試利用 [`SerializedProperty`](https://docs.unity3d.com/ScriptReference/SerializedProperty.html) 和 [`EditorGUILayout.PropertyField`](https://docs.unity3d.com/ScriptReference/EditorGUILayout.PropertyField.html) 。</span><span class="sxs-lookup"><span data-stu-id="14edc-184">If custom rendering is required in the inspector class, try to utilize [`SerializedProperty`](https://docs.unity3d.com/ScriptReference/SerializedProperty.html) and [`EditorGUILayout.PropertyField`](https://docs.unity3d.com/ScriptReference/EditorGUILayout.PropertyField.html).</span></span> <span data-ttu-id="14edc-185">這可確保 Unity 正確處理轉譯的嵌套 prefabs 和修改的值。</span><span class="sxs-lookup"><span data-stu-id="14edc-185">This will ensure Unity correctly handles rendering nested prefabs and modified values.</span></span>

<span data-ttu-id="14edc-186">如果 [`EditorGUILayout.PropertyField`](https://docs.unity3d.com/ScriptReference/EditorGUILayout.PropertyField.html) 因為自訂邏輯需求而無法使用，請確定所有使用方式均包裝在周圍 [`EditorGUI.PropertyScope`](https://docs.unity3d.com/ScriptReference/EditorGUI.PropertyScope.html) 。</span><span class="sxs-lookup"><span data-stu-id="14edc-186">If [`EditorGUILayout.PropertyField`](https://docs.unity3d.com/ScriptReference/EditorGUILayout.PropertyField.html) cannot be used due to a requirement in custom logic, ensure all usage is wrapped around a [`EditorGUI.PropertyScope`](https://docs.unity3d.com/ScriptReference/EditorGUI.PropertyScope.html).</span></span> <span data-ttu-id="14edc-187">這可確保 Unity 針對嵌套 prefabs 和已修改的值，以指定的屬性正確地呈現偵測器。</span><span class="sxs-lookup"><span data-stu-id="14edc-187">This will ensure Unity renders the inspector correctly for nested prefabs and modified values with the given property.</span></span>

<span data-ttu-id="14edc-188">此外，請嘗試使用裝飾自訂偵測器類別 [`CanEditMultipleObjects`](https://docs.unity3d.com/ScriptReference/CanEditMultipleObjects.html) 。</span><span class="sxs-lookup"><span data-stu-id="14edc-188">Furthermore, try to decorate the custom inspector class with a [`CanEditMultipleObjects`](https://docs.unity3d.com/ScriptReference/CanEditMultipleObjects.html).</span></span> <span data-ttu-id="14edc-189">此標記可確保場景中具有此元件的多個物件可以同時選取和修改。</span><span class="sxs-lookup"><span data-stu-id="14edc-189">This tag ensure multiple objects with this component in the scene can be selected and modified together.</span></span> <span data-ttu-id="14edc-190">任何新的偵測器類別都應該測試其程式碼是否適用于場景中的這種情況。</span><span class="sxs-lookup"><span data-stu-id="14edc-190">Any new inspector classes should test that their code works in this situation in the scene.</span></span>

```c#
    // Example inspector class demonstrating usage of SerializedProperty & EditorGUILayout.PropertyField
    // as well as use of EditorGUI.PropertyScope for custom property logic
    [CustomEditor(typeof(MyComponent))]
    public class MyComponentInspector : UnityEditor.Editor
    {
        private SerializedProperty myProperty;
        private SerializedProperty handedness;

        protected virtual void OnEnable()
        {
            myProperty = serializedObject.FindProperty("myProperty");
            handedness = serializedObject.FindProperty("handedness");
        }

        public override void OnInspectorGUI()
        {
            EditorGUILayout.PropertyField(destroyOnSourceLost);

            Rect position = EditorGUILayout.GetControlRect();
            var label = new GUIContent(handedness.displayName);
            using (new EditorGUI.PropertyScope(position, label, handedness))
            {
                var currentHandedness = (Handedness)handedness.enumValueIndex;

                handedness.enumValueIndex = (int)(Handedness)EditorGUI.EnumPopup(
                    position,
                    label,
                    currentHandedness,
                    (value) => {
                        // This function is executed by Unity to determine if a possible enum value
                        // is valid for selection in the editor view
                        // In this case, only Handedness.Left and Handedness.Right can be selected
                        return (Handedness)value == Handedness.Left
                        || (Handedness)value == Handedness.Right;
                    });
            }
        }
    }
```

### <a name="adding-new-scriptableobjects"></a><span data-ttu-id="14edc-191">正在加入新的 ScriptableObjects</span><span class="sxs-lookup"><span data-stu-id="14edc-191">Adding new ScriptableObjects</span></span>

<span data-ttu-id="14edc-192">新增 ScriptableObject 腳本時，請確定 [`CreateAssetMenu`](https://docs.unity3d.com/ScriptReference/CreateAssetMenu.html) 屬性已套用至所有適用的檔案。</span><span class="sxs-lookup"><span data-stu-id="14edc-192">When adding new ScriptableObject scripts, ensure the [`CreateAssetMenu`](https://docs.unity3d.com/ScriptReference/CreateAssetMenu.html) attribute is applied to all applicable files.</span></span> <span data-ttu-id="14edc-193">這可確保在編輯器中透過資產建立功能表輕鬆地探索元件。</span><span class="sxs-lookup"><span data-stu-id="14edc-193">This ensures the component is easily discoverable in the editor via the asset creation menus.</span></span> <span data-ttu-id="14edc-194">如果元件無法顯示在編輯器（例如抽象類別）中，則不需要屬性旗標。</span><span class="sxs-lookup"><span data-stu-id="14edc-194">The attribute flag is not necessary if the component cannot show up in editor such as an abstract class.</span></span>

<span data-ttu-id="14edc-195">在下列範例中， *子資料夾* 應填入 MRTK 子資料夾（如果適用）。</span><span class="sxs-lookup"><span data-stu-id="14edc-195">In the example below, the *Subfolder* should be filled with the MRTK subfolder, if applicable.</span></span> <span data-ttu-id="14edc-196">如果將專案放在 *MRTK/Providers* 資料夾中，則套件將會是 *提供者*。</span><span class="sxs-lookup"><span data-stu-id="14edc-196">If placing an item in *MRTK/Providers* folder, then the package will be *Providers*.</span></span> <span data-ttu-id="14edc-197">如果將專案放在 *MRTK/Core* 資料夾中，請將它設定為「設定檔」。</span><span class="sxs-lookup"><span data-stu-id="14edc-197">If placing an item in the *MRTK/Core* folder, set this to "Profiles".</span></span>

<span data-ttu-id="14edc-198">在下列範例中， *MyNewService |MyNewProvider* 應該填入新的類別名稱（如果適用）。</span><span class="sxs-lookup"><span data-stu-id="14edc-198">In the example below, the *MyNewService | MyNewProvider* should be filled with the your new class' name, if applicable.</span></span> <span data-ttu-id="14edc-199">如果將專案放在 *MixedRealityToolkit* 資料夾中，請將此字串退出。</span><span class="sxs-lookup"><span data-stu-id="14edc-199">If placing an item in the *MixedRealityToolkit* folder, leave this string out.</span></span>

```c#
[CreateAssetMenu(fileName = "MyNewProfile", menuName = "Mixed Reality Toolkit/{Subfolder}/{MyNewService | MyNewProvider}/MyNewProfile")]
public class MyNewProfile : ScriptableObject
```

### <a name="spaces-vs-tabs"></a><span data-ttu-id="14edc-200">空格 vs tab</span><span class="sxs-lookup"><span data-stu-id="14edc-200">Spaces vs tabs</span></span>

<span data-ttu-id="14edc-201">參與此專案時，請務必使用4個空格，而不是索引標籤。</span><span class="sxs-lookup"><span data-stu-id="14edc-201">Please be sure to use 4 spaces instead of tabs when contributing to this project.</span></span>

### <a name="spacing"></a><span data-ttu-id="14edc-202">間距</span><span class="sxs-lookup"><span data-stu-id="14edc-202">Spacing</span></span>

<span data-ttu-id="14edc-203">請勿在方括弧和括弧之間新增額外的空格：</span><span class="sxs-lookup"><span data-stu-id="14edc-203">Do not to add additional spaces between square brackets and parenthesis:</span></span>

#### <a name="dont"></a><span data-ttu-id="14edc-204">禁止事項</span><span class="sxs-lookup"><span data-stu-id="14edc-204">Don't</span></span>

```c#
private Foo()
{
    int[ ] var = new int [ 9 ];
    Vector2 vector = new Vector2 ( 0f, 10f );
}

```

#### <a name="do"></a><span data-ttu-id="14edc-205">可行事項</span><span class="sxs-lookup"><span data-stu-id="14edc-205">Do</span></span>

```c#
private Foo()
{
    int[] var = new int[9];
    Vector2 vector = new Vector2(0f, 10f);
}
```

### <a name="naming-conventions"></a><span data-ttu-id="14edc-206">命名規範</span><span class="sxs-lookup"><span data-stu-id="14edc-206">Naming conventions</span></span>

<span data-ttu-id="14edc-207">一律用於 `PascalCase` 屬性。</span><span class="sxs-lookup"><span data-stu-id="14edc-207">Always use `PascalCase` for properties.</span></span> <span data-ttu-id="14edc-208">使用 `camelCase` 于大部分的欄位，但 `PascalCase` 使用 `static readonly` 和 `const` 欄位除外。</span><span class="sxs-lookup"><span data-stu-id="14edc-208">Use `camelCase` for most fields, except use `PascalCase` for `static readonly` and `const` fields.</span></span> <span data-ttu-id="14edc-209">唯一的例外是針對需要由序列化欄位的資料結構 `JsonUtility` 。</span><span class="sxs-lookup"><span data-stu-id="14edc-209">The only exception to this is for data structures that require the fields to be serialized by the `JsonUtility`.</span></span>

#### <a name="dont"></a><span data-ttu-id="14edc-210">禁止事項</span><span class="sxs-lookup"><span data-stu-id="14edc-210">Don't</span></span>

```c#
public string myProperty; // <- Starts with a lowercase letter
private string MyField; // <- Starts with an uppercase letter
```

#### <a name="do"></a><span data-ttu-id="14edc-211">可行事項</span><span class="sxs-lookup"><span data-stu-id="14edc-211">Do</span></span>

```c#
public string MyProperty;
protected string MyProperty;
private static readonly string MyField;
private string myField;
```

### <a name="access-modifiers"></a><span data-ttu-id="14edc-212">存取修飾詞</span><span class="sxs-lookup"><span data-stu-id="14edc-212">Access modifiers</span></span>

<span data-ttu-id="14edc-213">一律宣告所有欄位、屬性和方法的存取修飾詞。</span><span class="sxs-lookup"><span data-stu-id="14edc-213">Always declare an access modifier for all fields, properties and methods.</span></span>

- <span data-ttu-id="14edc-214">`private`除非您需要在衍生類別中覆寫，否則所有 UNITY API 方法都應該預設為。</span><span class="sxs-lookup"><span data-stu-id="14edc-214">All Unity API Methods should be `private` by default, unless you need to override them in a derived class.</span></span> <span data-ttu-id="14edc-215">在此情況下， `protected` 應該使用。</span><span class="sxs-lookup"><span data-stu-id="14edc-215">In this case `protected` should be used.</span></span>

- <span data-ttu-id="14edc-216">欄位應一律為 `private` ，具有 `public` 或 `protected` 屬性存取子。</span><span class="sxs-lookup"><span data-stu-id="14edc-216">Fields should always be `private`, with `public` or `protected` property accessors.</span></span>

- <span data-ttu-id="14edc-217">盡可能使用[運算式主體的成員](https://github.com/dotnet/roslyn/wiki/New-Language-Features-in-C%23-6#expression-bodied-function-members)和[auto 屬性](https://github.com/dotnet/roslyn/wiki/New-Language-Features-in-C%23-6#auto-property-enhancements)</span><span class="sxs-lookup"><span data-stu-id="14edc-217">Use [expression-bodied members](https://github.com/dotnet/roslyn/wiki/New-Language-Features-in-C%23-6#expression-bodied-function-members) and [auto properties](https://github.com/dotnet/roslyn/wiki/New-Language-Features-in-C%23-6#auto-property-enhancements) where possible</span></span>

#### <a name="dont"></a><span data-ttu-id="14edc-218">禁止事項</span><span class="sxs-lookup"><span data-stu-id="14edc-218">Don't</span></span>

```c#
// protected field should be private
protected int myVariable = 0;

// property should have protected setter
public int MyVariable => myVariable;

// No public / private access modifiers
void Foo() { }
void Bar() { }
```

#### <a name="do"></a><span data-ttu-id="14edc-219">可行事項</span><span class="sxs-lookup"><span data-stu-id="14edc-219">Do</span></span>

```c#
public int MyVariable { get; protected set; } = 0;

private void Foo() { }
public void Bar() { }
protected virtual void FooBar() { }
```

### <a name="use-braces"></a><span data-ttu-id="14edc-220">使用大括弧</span><span class="sxs-lookup"><span data-stu-id="14edc-220">Use braces</span></span>

<span data-ttu-id="14edc-221">請一律在每個語句區塊之後使用大括弧，並將它們放在下一行。</span><span class="sxs-lookup"><span data-stu-id="14edc-221">Always use braces after each statement block, and place them on the next line.</span></span>

#### <a name="dont"></a><span data-ttu-id="14edc-222">禁止事項</span><span class="sxs-lookup"><span data-stu-id="14edc-222">Don't</span></span>

```c#
private Foo()
{
    if (Bar==null) // <- missing braces surrounding if action
        DoThing();
    else
        DoTheOtherThing();
}
```

#### <a name="dont"></a><span data-ttu-id="14edc-223">禁止事項</span><span class="sxs-lookup"><span data-stu-id="14edc-223">Don't</span></span>

```c#
private Foo() { // <- Open bracket on same line
    if (Bar==null) DoThing(); <- if action on same line with no surrounding brackets
    else DoTheOtherThing();
}
```

#### <a name="do"></a><span data-ttu-id="14edc-224">可行事項</span><span class="sxs-lookup"><span data-stu-id="14edc-224">Do</span></span>

```c#
private Foo()
{
    if (Bar==true)
    {
        DoThing();
    }
    else
    {
        DoTheOtherThing();
    }
}
```

### <a name="public-classes-structs-and-enums-should-all-go-in-their-own-files"></a><span data-ttu-id="14edc-225">公用類別、結構和列舉應該全都放入自己的檔案</span><span class="sxs-lookup"><span data-stu-id="14edc-225">Public classes, structs, and enums should all go in their own files</span></span>

<span data-ttu-id="14edc-226">如果類別、結構或列舉可以設為私用，則可以將它包含在相同的檔案中。</span><span class="sxs-lookup"><span data-stu-id="14edc-226">If the class, struct, or enum can be made private then it's okay to be included in the same file.</span></span>  <span data-ttu-id="14edc-227">這可避免與 Unity 相關的問題，並確保發生適當的程式碼抽象化，也可在程式碼需要變更時減少衝突和重大變更。</span><span class="sxs-lookup"><span data-stu-id="14edc-227">This avoids compilations issues with Unity and ensure that proper code abstraction occurs, it also reduces conflicts and breaking changes when code needs to change.</span></span>

#### <a name="dont"></a><span data-ttu-id="14edc-228">禁止事項</span><span class="sxs-lookup"><span data-stu-id="14edc-228">Don't</span></span>

```c#
public class MyClass
{
    public struct MyStruct() { }
    public enum MyEnumType() { }
    public class MyNestedClass() { }
}
```

#### <a name="do"></a><span data-ttu-id="14edc-229">可行事項</span><span class="sxs-lookup"><span data-stu-id="14edc-229">Do</span></span>

```c#
 // Private references for use inside the class only
public class MyClass
{
    private struct MyStruct() { }
    private enum MyEnumType() { }
    private class MyNestedClass() { }
}
```

#### <a name="do"></a><span data-ttu-id="14edc-230">可行事項</span><span class="sxs-lookup"><span data-stu-id="14edc-230">Do</span></span>

<span data-ttu-id="14edc-231">Mystruct>) .cs</span><span class="sxs-lookup"><span data-stu-id="14edc-231">MyStruct.cs</span></span>

```c#
// Public Struct / Enum definitions for use in your class.  Try to make them generic for reuse.
public struct MyStruct
{
    public string Var1;
    public string Var2;
}
```

<span data-ttu-id="14edc-232">MyEnumType .cs</span><span class="sxs-lookup"><span data-stu-id="14edc-232">MyEnumType.cs</span></span>

```c#
public enum MuEnumType
{
    Value1,
    Value2 // <- note, no "," on last value to denote end of list.
}
```

<span data-ttu-id="14edc-233">MyClass</span><span class="sxs-lookup"><span data-stu-id="14edc-233">MyClass.cs</span></span>

```c#
public class MyClass
{
    private MyStruct myStructReference;
    private MyEnumType myEnumReference;
}
```

### <a name="initialize-enums"></a><span data-ttu-id="14edc-234">初始化列舉</span><span class="sxs-lookup"><span data-stu-id="14edc-234">Initialize enums</span></span>

<span data-ttu-id="14edc-235">為了確保從0開始正確初始化所有列舉，.NET 會提供您整齊的快捷方式，藉由直接新增第一個 (入門) 值來自動初始化列舉。</span><span class="sxs-lookup"><span data-stu-id="14edc-235">To ensure all enums are initialized correctly starting at 0, .NET gives you a tidy shortcut to automatically initialize the enum by just adding the first (starter) value.</span></span> <span data-ttu-id="14edc-236"> (，例如值 1 = 0 不需要剩餘的值) </span><span class="sxs-lookup"><span data-stu-id="14edc-236">(e.g Value 1 = 0 Remaining values are not required)</span></span>

#### <a name="dont"></a><span data-ttu-id="14edc-237">禁止事項</span><span class="sxs-lookup"><span data-stu-id="14edc-237">Don't</span></span>

```c#
public enum Value
{
    Value1, <- no initializer
    Value2,
    Value3
}
```

#### <a name="do"></a><span data-ttu-id="14edc-238">可行事項</span><span class="sxs-lookup"><span data-stu-id="14edc-238">Do</span></span>

```c#
public enum ValueType
{
    Value1 = 0,
    Value2,
    Value3
}
```

### <a name="order-enums-for-appropriate-extension"></a><span data-ttu-id="14edc-239">排序適當擴充的列舉</span><span class="sxs-lookup"><span data-stu-id="14edc-239">Order enums for appropriate extension</span></span>

<span data-ttu-id="14edc-240">如果未來可能會延長列舉，以排序列舉頂端的預設值，這可確保列舉索引不會影響新的新增專案。</span><span class="sxs-lookup"><span data-stu-id="14edc-240">It is critical that if an Enum is likely to be extended in the future, to order defaults at the top of the Enum, this ensures Enum indexes are not affected with new additions.</span></span>

#### <a name="dont"></a><span data-ttu-id="14edc-241">禁止事項</span><span class="sxs-lookup"><span data-stu-id="14edc-241">Don't</span></span>

```c#
public enum SDKType
{
    WindowsMR,
    OpenVR,
    OpenXR,
    None, <- default value not at start
    Other <- anonymous value left to end of enum
}
```

#### <a name="do"></a><span data-ttu-id="14edc-242">可行事項</span><span class="sxs-lookup"><span data-stu-id="14edc-242">Do</span></span>

```c#
/// <summary>
/// The SDKType lists the VR SDKs that are supported by the MRTK
/// Initially, this lists proposed SDKs, not all may be implemented at this time (please see ReleaseNotes for more details)
/// </summary>
public enum SDKType
{
    /// <summary>
    /// No specified type or Standalone / non-VR type
    /// </summary>
    None = 0,
    /// <summary>
    /// Undefined SDK.
    /// </summary>
    Other,
    /// <summary>
    /// The Windows 10 Mixed reality SDK provided by the Universal Windows Platform (UWP), for Immersive MR headsets and HoloLens.
    /// </summary>
    WindowsMR,
    /// <summary>
    /// The OpenVR platform provided by Unity (does not support the downloadable SteamVR SDK).
    /// </summary>
    OpenVR,
    /// <summary>
    /// The OpenXR platform. SDK to be determined once released.
    /// </summary>
    OpenXR
}
```

### <a name="review-enum-use-for-bitfields"></a><span data-ttu-id="14edc-243">審核位欄位的列舉用途</span><span class="sxs-lookup"><span data-stu-id="14edc-243">Review enum use for bitfields</span></span>

<span data-ttu-id="14edc-244">如果列舉可能需要使用多個狀態作為值，例如 Handedness = Left & Right。</span><span class="sxs-lookup"><span data-stu-id="14edc-244">If there is a possibility for an enum to require multiple states as a value, e.g. Handedness = Left & Right.</span></span> <span data-ttu-id="14edc-245">接著，必須使用位旗標正確裝飾列舉，才能讓它正確地使用</span><span class="sxs-lookup"><span data-stu-id="14edc-245">Then the Enum needs to be decorated correctly with BitFlags to enable it to be used correctly</span></span>

<span data-ttu-id="14edc-246">Handedness .cs 檔案有此的具體執行</span><span class="sxs-lookup"><span data-stu-id="14edc-246">The Handedness.cs file has a concrete implementation for this</span></span>

### <a name="dont"></a><span data-ttu-id="14edc-247">禁止事項</span><span class="sxs-lookup"><span data-stu-id="14edc-247">Don't</span></span>

```c#
public enum Handedness
{
    None,
    Left,
    Right
}
```

### <a name="do"></a><span data-ttu-id="14edc-248">可行事項</span><span class="sxs-lookup"><span data-stu-id="14edc-248">Do</span></span>

```c#
[Flags]
public enum Handedness
{
    None = 0 << 0,
    Left = 1 << 0,
    Right = 1 << 1,
    Both = Left | Right
}
```

### <a name="hard-coded-file-paths"></a><span data-ttu-id="14edc-249">硬式編碼的檔案路徑</span><span class="sxs-lookup"><span data-stu-id="14edc-249">Hard-coded file paths</span></span>

<span data-ttu-id="14edc-250">產生字串檔案路徑時，特別是撰寫硬式編碼的字串路徑時，請執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="14edc-250">When generating string file paths, and in particular writing hard-coded string paths, do the following:</span></span>

1. <span data-ttu-id="14edc-251">盡可能使用 c # 的[ `Path` api](https://docs.microsoft.com/dotnet/api/system.io.path?view=netframework-4.8) ，例如 `Path.Combine` 或 `Path.GetFullPath` 。</span><span class="sxs-lookup"><span data-stu-id="14edc-251">Use C#'s [`Path` APIs](https://docs.microsoft.com/dotnet/api/system.io.path?view=netframework-4.8) whenever possible such as `Path.Combine` or `Path.GetFullPath`.</span></span>
1. <span data-ttu-id="14edc-252">使用/或 [`Path.DirectorySeparatorChar`](https://docs.microsoft.com/dotnet/api/system.io.path.directoryseparatorchar?view=netframework-4.8) ，而不是 \ 或 \\ \\ 。</span><span class="sxs-lookup"><span data-stu-id="14edc-252">Use / or [`Path.DirectorySeparatorChar`](https://docs.microsoft.com/dotnet/api/system.io.path.directoryseparatorchar?view=netframework-4.8) instead of \ or \\\\.</span></span>

<span data-ttu-id="14edc-253">這些步驟可確保 MRTK 可在 Windows 和 Unix 系統上運作。</span><span class="sxs-lookup"><span data-stu-id="14edc-253">These steps ensure that MRTK works on both Windows and Unix-based systems.</span></span>

### <a name="dont"></a><span data-ttu-id="14edc-254">禁止事項</span><span class="sxs-lookup"><span data-stu-id="14edc-254">Don't</span></span>

```c#
private const string FilePath = "MyPath\\to\\a\\file.txt";
private const string OtherFilePath = "MyPath\to\a\file.txt";

string filePath = myVarRootPath + myRelativePath;
```

### <a name="do"></a><span data-ttu-id="14edc-255">可行事項</span><span class="sxs-lookup"><span data-stu-id="14edc-255">Do</span></span>

```c#
private const string FilePath = "MyPath/to/a/file.txt";
private const string OtherFilePath = "folder{Path.DirectorySeparatorChar}file.txt";

string filePath = Path.Combine(myVarRootPath,myRelativePath);

// Path.GetFullPath() will return the full length path of provided with correct system directory separators
string cleanedFilePath = Path.GetFullPath(unknownSourceFilePath);
```

## <a name="best-practices-including-unity-recommendations"></a><span data-ttu-id="14edc-256">最佳做法，包括 Unity 建議</span><span class="sxs-lookup"><span data-stu-id="14edc-256">Best practices, including Unity recommendations</span></span>

<span data-ttu-id="14edc-257">此專案的某些目標平臺需要將效能納入考慮。</span><span class="sxs-lookup"><span data-stu-id="14edc-257">Some of the target platforms of this project require to take performance into consideration.</span></span> <span data-ttu-id="14edc-258">如此一來，在嚴格的更新迴圈或演算法中配置經常稱為程式碼的記憶體時，一定要特別小心。</span><span class="sxs-lookup"><span data-stu-id="14edc-258">With this in mind always be careful when allocating memory in frequently called code in tight update loops or algorithms.</span></span>

### <a name="encapsulation"></a><span data-ttu-id="14edc-259">封裝</span><span class="sxs-lookup"><span data-stu-id="14edc-259">Encapsulation</span></span>

<span data-ttu-id="14edc-260">如果需要從類別或結構外部存取欄位，請一律使用私用欄位和公用屬性。</span><span class="sxs-lookup"><span data-stu-id="14edc-260">Always use private fields and public properties if access to the field is needed from outside the class or struct.</span></span>  <span data-ttu-id="14edc-261">請務必共同找出私用欄位和公用屬性。</span><span class="sxs-lookup"><span data-stu-id="14edc-261">Be sure to co-locate the private field and the public property.</span></span> <span data-ttu-id="14edc-262">這可讓您更輕鬆地查看屬性的內容，以及腳本可修改欄位。</span><span class="sxs-lookup"><span data-stu-id="14edc-262">This makes it easier to see, at a glance, what backs the property and that the field is modifiable by script.</span></span>

> [!NOTE]
> <span data-ttu-id="14edc-263">唯一的例外是針對需要由序列化欄位的資料結構 `JsonUtility` ，其中資料類別需要有所有公用欄位，序列化才能運作。</span><span class="sxs-lookup"><span data-stu-id="14edc-263">The only exception to this is for data structures that require the fields to be serialized by the `JsonUtility`, where a data class is required to have all public fields for the serialization to work.</span></span>

#### <a name="dont"></a><span data-ttu-id="14edc-264">禁止事項</span><span class="sxs-lookup"><span data-stu-id="14edc-264">Don't</span></span>

```c#
private float myValue1;
private float myValue2;

public float MyValue1
{
    get{ return myValue1; }
    set{ myValue1 = value }
}

public float MyValue2
{
    get{ return myValue2; }
    set{ myValue2 = value }
}
```

#### <a name="do"></a><span data-ttu-id="14edc-265">可行事項</span><span class="sxs-lookup"><span data-stu-id="14edc-265">Do</span></span>

```c#
// Enable field to be configurable in the editor and available externally to other scripts (field is correctly serialized in Unity)
[SerializeField]
[ToolTip("If using a tooltip, the text should match the public property's summary documentation, if appropriate.")]
private float myValue; // <- Notice we co-located the backing field above our corresponding property.

/// <summary>
/// If using a tooltip, the text should match the public property's summary documentation, if appropriate.
/// </summary>
public float MyValue
{
    get => myValue;
    set => myValue = value;
}

/// <summary>
/// Getter/Setters not wrapping a value directly should contain documentation comments just as public functions would
/// </summary>
public float AbsMyValue
{
    get
    {
        if (MyValue < 0)
        {
            return -MyValue;
        }

        return MyValue
    }
}
```

### <a name="cache-values-and-serialize-them-in-the-sceneprefab-whenever-possible"></a><span data-ttu-id="14edc-266">快取值，並盡可能在場景/預製專案中將它們序列化</span><span class="sxs-lookup"><span data-stu-id="14edc-266">Cache values and serialize them in the scene/prefab whenever possible</span></span>

<span data-ttu-id="14edc-267">在 HoloLens 的考慮下，最好是將場景或預製專案中的效能和快取參考優化，以限制執行時間記憶體配置。</span><span class="sxs-lookup"><span data-stu-id="14edc-267">With the HoloLens in mind, it's best to optimize for performance and cache references in the scene or prefab to limit runtime memory allocations.</span></span>

#### <a name="dont"></a><span data-ttu-id="14edc-268">禁止事項</span><span class="sxs-lookup"><span data-stu-id="14edc-268">Don't</span></span>

```c#
void Update()
{
    gameObject.GetComponent<Renderer>().Foo(Bar);
}
```

#### <a name="do"></a><span data-ttu-id="14edc-269">可行事項</span><span class="sxs-lookup"><span data-stu-id="14edc-269">Do</span></span>

```c#
[SerializeField] // To enable setting the reference in the inspector.
private Renderer myRenderer;

private void Awake()
{
    // If you didn't set it in the inspector, then we cache it on awake.
    if (myRenderer == null)
    {
        myRenderer = gameObject.GetComponent<Renderer>();
    }
}

private void Update()
{
    myRenderer.Foo(Bar);
}
```

### <a name="cache-references-to-materials-do-not-call-the-material-each-time"></a><span data-ttu-id="14edc-270">資料的快取參考，請勿每次都呼叫 ". 材質"</span><span class="sxs-lookup"><span data-stu-id="14edc-270">Cache references to materials, do not call the ".material" each time</span></span>

<span data-ttu-id="14edc-271">Unity 將會在您每次使用「材質」時建立新的材質，如果未正確清除，將會造成記憶體流失。</span><span class="sxs-lookup"><span data-stu-id="14edc-271">Unity will create a new material each time you use ".material", which will cause a memory leak if not cleaned up properly.</span></span>

#### <a name="dont"></a><span data-ttu-id="14edc-272">禁止事項</span><span class="sxs-lookup"><span data-stu-id="14edc-272">Don't</span></span>

```c#
public class MyClass
{
    void Update()
    {
        Material myMaterial = GetComponent<Renderer>().material;
        myMaterial.SetColor("_Color", Color.White);
    }
}
```

#### <a name="do"></a><span data-ttu-id="14edc-273">可行事項</span><span class="sxs-lookup"><span data-stu-id="14edc-273">Do</span></span>

```c#
// Private references for use inside the class only
public class MyClass
{
    private Material cachedMaterial;

    private void Awake()
    {
        cachedMaterial = GetComponent<Renderer>().material;
    }

    void Update()
    {
        cachedMaterial.SetColor("_Color", Color.White);
    }

    private void OnDestroy()
    {
        Destroy(cachedMaterial);
    }
}
```

> [!NOTE]
> <span data-ttu-id="14edc-274">或者，您也可以使用 Unity 的 "SharedMaterial" 屬性，此屬性不會在每次參考時建立新的內容。</span><span class="sxs-lookup"><span data-stu-id="14edc-274">Alternatively, use Unity's "SharedMaterial" property which does not create a new material each time it is referenced.</span></span>

### <a name="use-platform-dependent-compilation-to-ensure-the-toolkit-wont-break-the-build-on-another-platform"></a><span data-ttu-id="14edc-275">使用 [平臺相依編譯](https://docs.unity3d.com/Manual/PlatformDependentCompilation.html) 來確保工具組不會在另一個平臺上中斷組建</span><span class="sxs-lookup"><span data-stu-id="14edc-275">Use [platform dependent compilation](https://docs.unity3d.com/Manual/PlatformDependentCompilation.html) to ensure the Toolkit won't break the build on another platform</span></span>

- <span data-ttu-id="14edc-276">使用 `WINDOWS_UWP` 以使用 UWP 特定的非 Unity api。</span><span class="sxs-lookup"><span data-stu-id="14edc-276">Use `WINDOWS_UWP` in order to use UWP-specific, non-Unity APIs.</span></span> <span data-ttu-id="14edc-277">這會讓他們無法嘗試在編輯器或不支援的平臺上執行。</span><span class="sxs-lookup"><span data-stu-id="14edc-277">This will prevent them from trying to run in the Editor or on unsupported platforms.</span></span> <span data-ttu-id="14edc-278">這相當於 `UNITY_WSA && !UNITY_EDITOR` ，而且應該改用。</span><span class="sxs-lookup"><span data-stu-id="14edc-278">This is equivalent to `UNITY_WSA && !UNITY_EDITOR` and should be used in favor of.</span></span>
- <span data-ttu-id="14edc-279">使用 `UNITY_WSA` 以使用 UWP 特定的 Unity api，例如 `UnityEngine.XR.WSA` 命名空間。</span><span class="sxs-lookup"><span data-stu-id="14edc-279">Use `UNITY_WSA` to use UWP-specific Unity APIs, such as the `UnityEngine.XR.WSA` namespace.</span></span> <span data-ttu-id="14edc-280">當平臺設定為 UWP，以及在建立的 UWP 應用程式中時，這會在編輯器中執行。</span><span class="sxs-lookup"><span data-stu-id="14edc-280">This will run in the Editor when the platform is set to UWP, as well as in built UWP apps.</span></span>

<span data-ttu-id="14edc-281">此圖表可協助您決定要使用哪一種 `#if` ，取決於您的使用案例和您預期的組建設定。</span><span class="sxs-lookup"><span data-stu-id="14edc-281">This chart can help you decide which `#if` to use, depending on your use cases and the build settings you expect.</span></span>

| | <span data-ttu-id="14edc-282">UWP IL2CPP</span><span class="sxs-lookup"><span data-stu-id="14edc-282">UWP IL2CPP</span></span> | <span data-ttu-id="14edc-283">UWP .NET</span><span class="sxs-lookup"><span data-stu-id="14edc-283">UWP .NET</span></span> | <span data-ttu-id="14edc-284">編輯器</span><span class="sxs-lookup"><span data-stu-id="14edc-284">Editor</span></span> |
| --- | --- | --- | --- |
| `UNITY_EDITOR` | <span data-ttu-id="14edc-285">False</span><span class="sxs-lookup"><span data-stu-id="14edc-285">False</span></span> | <span data-ttu-id="14edc-286">False</span><span class="sxs-lookup"><span data-stu-id="14edc-286">False</span></span> | <span data-ttu-id="14edc-287">True</span><span class="sxs-lookup"><span data-stu-id="14edc-287">True</span></span> |
| `UNITY_WSA` | <span data-ttu-id="14edc-288">True</span><span class="sxs-lookup"><span data-stu-id="14edc-288">True</span></span> | <span data-ttu-id="14edc-289">True</span><span class="sxs-lookup"><span data-stu-id="14edc-289">True</span></span> | <span data-ttu-id="14edc-290">True</span><span class="sxs-lookup"><span data-stu-id="14edc-290">True</span></span> |
| `WINDOWS_UWP` | <span data-ttu-id="14edc-291">True</span><span class="sxs-lookup"><span data-stu-id="14edc-291">True</span></span> | <span data-ttu-id="14edc-292">True</span><span class="sxs-lookup"><span data-stu-id="14edc-292">True</span></span> | <span data-ttu-id="14edc-293">False</span><span class="sxs-lookup"><span data-stu-id="14edc-293">False</span></span> |
| `UNITY_WSA && !UNITY_EDITOR` | <span data-ttu-id="14edc-294">True</span><span class="sxs-lookup"><span data-stu-id="14edc-294">True</span></span> | <span data-ttu-id="14edc-295">True</span><span class="sxs-lookup"><span data-stu-id="14edc-295">True</span></span> | <span data-ttu-id="14edc-296">False</span><span class="sxs-lookup"><span data-stu-id="14edc-296">False</span></span> |
| `ENABLE_WINMD_SUPPORT` | <span data-ttu-id="14edc-297">True</span><span class="sxs-lookup"><span data-stu-id="14edc-297">True</span></span> | <span data-ttu-id="14edc-298">True</span><span class="sxs-lookup"><span data-stu-id="14edc-298">True</span></span> | <span data-ttu-id="14edc-299">False</span><span class="sxs-lookup"><span data-stu-id="14edc-299">False</span></span> |
| `NETFX_CORE` | <span data-ttu-id="14edc-300">False</span><span class="sxs-lookup"><span data-stu-id="14edc-300">False</span></span> | <span data-ttu-id="14edc-301">True</span><span class="sxs-lookup"><span data-stu-id="14edc-301">True</span></span> | <span data-ttu-id="14edc-302">否</span><span class="sxs-lookup"><span data-stu-id="14edc-302">False</span></span> |

### <a name="prefer-datetimeutcnow-over-datetimenow"></a><span data-ttu-id="14edc-303">偏好 UtcNow 超過 DateTime。現在</span><span class="sxs-lookup"><span data-stu-id="14edc-303">Prefer DateTime.UtcNow over DateTime.Now</span></span>

<span data-ttu-id="14edc-304">UtcNow 比 DateTime 更快。現在。</span><span class="sxs-lookup"><span data-stu-id="14edc-304">DateTime.UtcNow is faster than DateTime.Now.</span></span> <span data-ttu-id="14edc-305">在先前的效能調查中，我們發現使用 DateTime。現在增加了很大的負擔，特別是在 Update () 迴圈中使用時。</span><span class="sxs-lookup"><span data-stu-id="14edc-305">In previous performance investigations we've found that using DateTime.Now adds significant overhead especially when used in the Update() loop.</span></span> <span data-ttu-id="14edc-306">[其他人遇到相同的問題](https://stackoverflow.com/questions/1561791/optimizing-alternatives-to-datetime-now)。</span><span class="sxs-lookup"><span data-stu-id="14edc-306">[Others have hit the same issue](https://stackoverflow.com/questions/1561791/optimizing-alternatives-to-datetime-now).</span></span>

<span data-ttu-id="14edc-307">偏好使用 DateTime. UtcNow，除非您真的需要當地語系化的時間 (合理的原因可能是您想要在使用者時區) 中顯示目前的時間。</span><span class="sxs-lookup"><span data-stu-id="14edc-307">Prefer using DateTime.UtcNow unless you actually need the localized times (a legitimate reason may be you wanting to show the current time in the user's time zone).</span></span> <span data-ttu-id="14edc-308">如果您正在處理相對時間 (也就是最後一個更新和現在) 之間的差異，最好使用 UtcNow 來避免執行時區轉換的額外負荷。</span><span class="sxs-lookup"><span data-stu-id="14edc-308">If you are dealing with relative times (i.e. the delta between some last update and now), it's best to use DateTime.UtcNow to avoid the overhead of doing timezone conversions.</span></span>

## <a name="powershell-coding-conventions"></a><span data-ttu-id="14edc-309">PowerShell 編碼慣例</span><span class="sxs-lookup"><span data-stu-id="14edc-309">PowerShell coding conventions</span></span>

<span data-ttu-id="14edc-310">MRTK 程式碼基底的子集會使用 PowerShell 來進行管線基礎結構和各種腳本和公用程式。</span><span class="sxs-lookup"><span data-stu-id="14edc-310">A subset of the MRTK codebase uses PowerShell for pipeline infrastructure and various scripts and utilities.</span></span> <span data-ttu-id="14edc-311">新的 PowerShell 程式碼應該遵循 [PoshCode 樣式](https://poshcode.gitbooks.io/powershell-practice-and-style/)。</span><span class="sxs-lookup"><span data-stu-id="14edc-311">New PowerShell code should follow the [PoshCode style](https://poshcode.gitbooks.io/powershell-practice-and-style/).</span></span>

## <a name="see-also"></a><span data-ttu-id="14edc-312">另請參閱</span><span class="sxs-lookup"><span data-stu-id="14edc-312">See also</span></span>

 [<span data-ttu-id="14edc-313">MSDN 的 c # 編碼慣例</span><span class="sxs-lookup"><span data-stu-id="14edc-313">C# coding conventions from MSDN</span></span>](https://docs.microsoft.com/dotnet/csharp/programming-guide/inside-a-program/coding-conventions)
