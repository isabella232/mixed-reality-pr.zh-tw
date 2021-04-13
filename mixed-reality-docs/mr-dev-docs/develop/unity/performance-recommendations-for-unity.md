---
title: 對 Unity 的效能建議
description: 了解 Unity 特有秘訣，以使用您混合實境應用程式中的專案設定、分析、記憶體管理來改善效能。
author: hferrone
ms.author: v-hferrone
ms.date: 03/26/2019
ms.topic: article
keywords: 圖形, cpu, gpu, 轉譯, 記憶體回收行程, hololens
ms.localizationpriority: high
ms.openlocfilehash: 2ff766c3fb2c9f8a91c3c8cc81bb21adae9956e8
ms.sourcegitcommit: 1c9035487270af76c6eaba11b11f6fc56c008135
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/13/2021
ms.locfileid: "107300153"
---
# <a name="performance-recommendations-for-unity"></a><span data-ttu-id="0b41e-104">對 Unity 的效能建議</span><span class="sxs-lookup"><span data-stu-id="0b41e-104">Performance recommendations for Unity</span></span>

<span data-ttu-id="0b41e-105">本文雖以[混合實境的效能建議](../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md)為基礎，但內容著重在 Unity 特有的改良功能。</span><span class="sxs-lookup"><span data-stu-id="0b41e-105">This article builds on the [performance recommendations for mixed reality](../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md), but focuses on Unity-specific improvements.</span></span>

## <a name="use-recommended-unity-project-settings"></a><span data-ttu-id="0b41e-106">使用建議的 Unity 專案設定</span><span class="sxs-lookup"><span data-stu-id="0b41e-106">Use recommended Unity project settings</span></span>

<span data-ttu-id="0b41e-107">將 Unity 中的混合實境應用程式效能最佳化時，最重要的第一個步驟是確定您已使用 [Unity 的建議環境設定](recommended-settings-for-unity.md)。</span><span class="sxs-lookup"><span data-stu-id="0b41e-107">The most important first step when optimizing performance of mixed reality apps in Unity is to be sure you're using the [recommended environment settings for Unity](recommended-settings-for-unity.md).</span></span> <span data-ttu-id="0b41e-108">該文章包含的內容具有一些最重要的場景設定，適用於建立高效能的混合實境應用程式。</span><span class="sxs-lookup"><span data-stu-id="0b41e-108">That article contains content with some of the most important scene configurations for building performant Mixed Reality apps.</span></span> <span data-ttu-id="0b41e-109">其中一些建議的設定也會反白顯示，如下所示。</span><span class="sxs-lookup"><span data-stu-id="0b41e-109">Some of these recommended settings are highlighted below, as well.</span></span>

## <a name="how-to-profile-with-unity"></a><span data-ttu-id="0b41e-110">如何使用 Unity 進行分析</span><span class="sxs-lookup"><span data-stu-id="0b41e-110">How to profile with Unity</span></span>

<span data-ttu-id="0b41e-111">Unity 提供內建的 **[Unity 分析工具](https://docs.unity3d.com/Manual/Profiler.html)** ，這是一項絕佳資源，可讓您針對特定應用程式收集寶貴的效能深入解析。</span><span class="sxs-lookup"><span data-stu-id="0b41e-111">Unity provides the **[Unity Profiler](https://docs.unity3d.com/Manual/Profiler.html)** built-in, which is a great resource to gather valuable performance insights for your particular app.</span></span> <span data-ttu-id="0b41e-112">雖然您可以在編輯器中執行分析工具，但這些計量並不代表真正的執行階段環境，因此請謹慎使用其結果。</span><span class="sxs-lookup"><span data-stu-id="0b41e-112">Although you can run the profiler in-editor, these metrics don't represent the true runtime environment so results should be used cautiously.</span></span> <span data-ttu-id="0b41e-113">當您在裝置上執行應用程式時，建議從遠端分析應用程式，以取得最精確且可採取動作的深入解析。</span><span class="sxs-lookup"><span data-stu-id="0b41e-113">We recommended remotely profiling your application while running on device for most accurate and actionable insights.</span></span> <span data-ttu-id="0b41e-114">此外，也可使用 Unity 的 [Frame Debugger](https://docs.unity3d.com/Manual/FrameDebugger.html)，這個工具既強大且能深入解析。</span><span class="sxs-lookup"><span data-stu-id="0b41e-114">Further, Unity's [Frame Debugger](https://docs.unity3d.com/Manual/FrameDebugger.html) is also a powerful and insight tool to use.</span></span>

<span data-ttu-id="0b41e-115">Unity 提供的絕佳文件：</span><span class="sxs-lookup"><span data-stu-id="0b41e-115">Unity provides great documentation for:</span></span>
1) <span data-ttu-id="0b41e-116">如何從遠端將 [Unity 分析工具連線到 UWP 應用程式](https://docs.unity3d.com/Manual/windowsstore-profiler.html)</span><span class="sxs-lookup"><span data-stu-id="0b41e-116">How to connect the [Unity profiler to UWP applications remotely](https://docs.unity3d.com/Manual/windowsstore-profiler.html)</span></span>
2) <span data-ttu-id="0b41e-117">如何使用 Unity 分析工具有效率地[診斷效能問題](https://unity3d.com/learn/tutorials/temas/performance-optimization/diagnosing-performance-problems-using-profiler-window)</span><span class="sxs-lookup"><span data-stu-id="0b41e-117">How to effectively [diagnose performance problems with the Unity Profiler](https://unity3d.com/learn/tutorials/temas/performance-optimization/diagnosing-performance-problems-using-profiler-window)</span></span>

>[!NOTE]
> <span data-ttu-id="0b41e-118">當 Unity 分析工具已連線並新增 GPU 分析工具之後 (請參閱右上角的「新增分析工具」)，使用者可以在分析工具的中間查看 CPU 與 GPU 分別花費了多少時間。</span><span class="sxs-lookup"><span data-stu-id="0b41e-118">With the Unity Profiler connected and after adding the GPU profiler (see *Add Profiler* in top right corner), one can see how much time is being spent on the CPU & GPU respectively in the middle of the profiler.</span></span> <span data-ttu-id="0b41e-119">這可讓開發人員在其應用程式為 CPU 或 GPU 限定時，取得快速近似值。</span><span class="sxs-lookup"><span data-stu-id="0b41e-119">This allows the developer to get a quick approximation if their application is CPU or GPU bounded.</span></span>
>
> ![Unity CPU 與 GPU](images/unity-profiler-cpu-gpu.png)

## <a name="cpu-performance-recommendations"></a><span data-ttu-id="0b41e-121">CPU 效能建議</span><span class="sxs-lookup"><span data-stu-id="0b41e-121">CPU performance recommendations</span></span>

<span data-ttu-id="0b41e-122">以下內容涵蓋更深入的效能實務，特別將目標放在 Unity 與 C# 開發。</span><span class="sxs-lookup"><span data-stu-id="0b41e-122">The content below covers more in-depth performance practices, especially targeted for Unity & C# development.</span></span>

#### <a name="cache-references"></a><span data-ttu-id="0b41e-123">快取參考</span><span class="sxs-lookup"><span data-stu-id="0b41e-123">Cache references</span></span>

<span data-ttu-id="0b41e-124">建議您在初始化時快取所有相關元件和 Gameobject 的參考，因為 *[GetComponent\<T>()](https://docs.unity3d.com/ScriptReference/GameObject.GetComponent.html)* 和 [Camera.main](https://docs.unity3d.com/ScriptReference/Camera-main.html) 之類的重複函式呼叫在儲存指標時所需的成本會比記憶體的成本更昂貴。</span><span class="sxs-lookup"><span data-stu-id="0b41e-124">We recommend caching references to all relevant components and GameObjects at initialization because repeating function calls such as *[GetComponent\<T>()](https://docs.unity3d.com/ScriptReference/GameObject.GetComponent.html)* and [Camera.main](https://docs.unity3d.com/ScriptReference/Camera-main.html) are more expensive relative to the memory cost to store a pointer.</span></span> <span data-ttu-id="0b41e-125">.</span><span class="sxs-lookup"><span data-stu-id="0b41e-125">.</span></span> <span data-ttu-id="0b41e-126">*Camera.main* 只會使用底下的 *[FindGameObjectsWithTag()](https://docs.unity3d.com/ScriptReference/GameObject.FindGameObjectsWithTag.html)* ，以高成本的方式搜尋場景圖形中含有 *"MainCamera"* 標記的相機物件。</span><span class="sxs-lookup"><span data-stu-id="0b41e-126">*Camera.main* just uses *[FindGameObjectsWithTag()](https://docs.unity3d.com/ScriptReference/GameObject.FindGameObjectsWithTag.html)* underneath, which expensively searches your scene graph for a camera object with the *"MainCamera"* tag.</span></span>

```CS
using UnityEngine;
using System.Collections;

public class ExampleClass : MonoBehaviour
{
    private Camera cam;
    private CustomComponent comp;

    void Start() 
    {
        cam = Camera.main;
        comp = GetComponent<CustomComponent>();
    }

    void Update()
    {
        // Good
        this.transform.position = cam.transform.position + cam.transform.forward * 10.0f;

        // Bad
        this.transform.position = Camera.main.transform.position + Camera.main.transform.forward * 10.0f;

        // Good
        comp.DoSomethingAwesome();

        // Bad
        GetComponent<CustomComponent>().DoSomethingAwesome();
    }
}
```

>[!NOTE] 
> <span data-ttu-id="0b41e-127">避免 GetComponent(字串)</span><span class="sxs-lookup"><span data-stu-id="0b41e-127">Avoid GetComponent(string)</span></span> <br/>
> <span data-ttu-id="0b41e-128">使用 *[GetComponent()](https://docs.unity3d.com/ScriptReference/GameObject.GetComponent.html)* 時，有少數不同的多載。</span><span class="sxs-lookup"><span data-stu-id="0b41e-128">When using *[GetComponent()](https://docs.unity3d.com/ScriptReference/GameObject.GetComponent.html)*, there are a handful of different overloads.</span></span> <span data-ttu-id="0b41e-129">請務必一律使用以類型為基礎的實作，而不是使用以字串為基礎的搜尋多載。</span><span class="sxs-lookup"><span data-stu-id="0b41e-129">It is important to always use the Type-based implementations and never the string-based searching overload.</span></span> <span data-ttu-id="0b41e-130">在場景中依字串搜尋會比依類型搜尋昂貴許多。</span><span class="sxs-lookup"><span data-stu-id="0b41e-130">Searching by string in your scene is significantly more costly than searching by Type.</span></span> <br/>
> <span data-ttu-id="0b41e-131">(良好) Component GetComponent(輸入類型)</span><span class="sxs-lookup"><span data-stu-id="0b41e-131">(Good) Component GetComponent(Type type)</span></span> <br/>
> <span data-ttu-id="0b41e-132">(良好) T GetComponent\<T>()</span><span class="sxs-lookup"><span data-stu-id="0b41e-132">(Good) T GetComponent\<T>()</span></span> <br/>
> <span data-ttu-id="0b41e-133">(不良) Component GetComponent(字串)></span><span class="sxs-lookup"><span data-stu-id="0b41e-133">(Bad) Component GetComponent(string)></span></span> <br/>

#### <a name="avoid-expensive-operations"></a><span data-ttu-id="0b41e-134">避免高成本的作業</span><span class="sxs-lookup"><span data-stu-id="0b41e-134">Avoid expensive operations</span></span>

1) <span data-ttu-id="0b41e-135">**避免使用 [LINQ](/dotnet/csharp/programming-guide/concepts/linq/getting-started-with-linq)**</span><span class="sxs-lookup"><span data-stu-id="0b41e-135">**Avoid use of [LINQ](/dotnet/csharp/programming-guide/concepts/linq/getting-started-with-linq)**</span></span>

    <span data-ttu-id="0b41e-136">雖然 LINQ 既簡潔有容易讀取和寫入，但所需的計算和記憶體數量一般會比手動撰寫演算法更多。</span><span class="sxs-lookup"><span data-stu-id="0b41e-136">Although LINQ can be clean and easy to read and write, it generally requires more computation and memory than if you wrote the algorithm manually.</span></span>

    ```CS
    // Example Code
    using System.Linq;

    List<int> data = new List<int>();
    data.Any(x => x > 10);

    var result = from x in data
                 where x > 10
                 select x;
    ```

2) <span data-ttu-id="0b41e-137">**通用 Unity API**</span><span class="sxs-lookup"><span data-stu-id="0b41e-137">**Common Unity APIs**</span></span>

    <span data-ttu-id="0b41e-138">某些 Unity API 雖然很有用，但執行的成本可能很高。</span><span class="sxs-lookup"><span data-stu-id="0b41e-138">Certain Unity APIs, although useful, can be expensive to execute.</span></span> <span data-ttu-id="0b41e-139">其中大部分牽涉到在整個場景圖形中搜尋一些相符的 Gameobject 清單。</span><span class="sxs-lookup"><span data-stu-id="0b41e-139">Most of these involve searching your entire scene graph for some matching list of GameObjects.</span></span> <span data-ttu-id="0b41e-140">這些作業通常可加以避免，方法是快取參考或針對 GameObject 實作管理員元件，以便在執行時間追蹤參考。</span><span class="sxs-lookup"><span data-stu-id="0b41e-140">These operations can generally be avoided by caching references or implementing a manager component for the GameObjects to track the references at runtime.</span></span>

    ```csharp
        GameObject.SendMessage()
        GameObject.BroadcastMessage()
        UnityEngine.Object.Find()
        UnityEngine.Object.FindWithTag()
        UnityEngine.Object.FindObjectOfType()
        UnityEngine.Object.FindObjectsOfType()
        UnityEngine.Object.FindGameObjectsWithTag()
        UnityEngine.Object.FindGameObjectsWithTag()
    ```

>[!NOTE]
> <span data-ttu-id="0b41e-141">應不計代價消除 *[SendMessage()](https://docs.unity3d.com/ScriptReference/GameObject.SendMessage.html)* 和 *[BroadcastMessage()](https://docs.unity3d.com/ScriptReference/GameObject.BroadcastMessage.html)* 。</span><span class="sxs-lookup"><span data-stu-id="0b41e-141">*[SendMessage()](https://docs.unity3d.com/ScriptReference/GameObject.SendMessage.html)* and *[BroadcastMessage()](https://docs.unity3d.com/ScriptReference/GameObject.BroadcastMessage.html)* should be eliminated at all costs.</span></span> <span data-ttu-id="0b41e-142">這些函式可能會比直接函式呼叫慢大約 1000 倍。</span><span class="sxs-lookup"><span data-stu-id="0b41e-142">These functions can be on the order of 1000x slower than direct function calls.</span></span>

3) <span data-ttu-id="0b41e-143">**注意 Box 處理**</span><span class="sxs-lookup"><span data-stu-id="0b41e-143">**Beware of boxing**</span></span>

    <span data-ttu-id="0b41e-144">[Box 處理](/dotnet/csharp/programming-guide/types/boxing-and-unboxing)是 C# 語言和執行時間的核心概念。</span><span class="sxs-lookup"><span data-stu-id="0b41e-144">[Boxing](/dotnet/csharp/programming-guide/types/boxing-and-unboxing) is a core concept of the C# language and runtime.</span></span> <span data-ttu-id="0b41e-145">這是將實值類型變數 (例如 `char`、`int`、`bool` 等) 包裝成參考類型變數的程序。</span><span class="sxs-lookup"><span data-stu-id="0b41e-145">It's the process of wrapping value-typed variables such as `char`, `int`, `bool`, etc. into reference-typed variables.</span></span> <span data-ttu-id="0b41e-146">實值類型變數為 "boxed" 時會包裝在儲存於 Managed 堆積上的 `System.Object` 中。</span><span class="sxs-lookup"><span data-stu-id="0b41e-146">When a value-typed variable is "boxed", it's wrapped in a `System.Object`, which is stored on the managed heap.</span></span> <span data-ttu-id="0b41e-147">系統會配置記憶體，且最終在處置時必須由記憶體回收行程處理。</span><span class="sxs-lookup"><span data-stu-id="0b41e-147">Memory is allocated and eventually when disposed must be processed by the garbage collector.</span></span> <span data-ttu-id="0b41e-148">這些配置和取消配置會產生效能成本，且在許多情況下並不需要，或是可以輕鬆地以較不昂貴的替代方案來取代。</span><span class="sxs-lookup"><span data-stu-id="0b41e-148">These allocations and deallocations incur a performance cost and in many scenarios are unnecessary or can be easily replaced by a less expensive alternative.</span></span>

    <span data-ttu-id="0b41e-149">若要避免 Box 處理，請確定您用來儲存數值類型和結構 (包括 `Nullable<T>`) 的變數、欄位和屬性已強型別化為特定類型 (例如 `int`、`float?` 或 `MyStruct`)，而不是使用物件。</span><span class="sxs-lookup"><span data-stu-id="0b41e-149">To avoid boxing, be sure that the variables, fields, and properties in which you store numeric types and structs (including `Nullable<T>`) are strongly typed as specific types such as `int`, `float?` or `MyStruct`, instead of using object.</span></span>  <span data-ttu-id="0b41e-150">如果將這些物件放入清單中，請務必使用強型別清單 (例如 `List<int>`)，而不是 `List<object>` 或 `ArrayList`。</span><span class="sxs-lookup"><span data-stu-id="0b41e-150">If putting these objects into a list, be sure to use a strongly typed list such as `List<int>` rather than `List<object>` or `ArrayList`.</span></span>

    <span data-ttu-id="0b41e-151">**C# 中的 Box 處理範例**</span><span class="sxs-lookup"><span data-stu-id="0b41e-151">**Example of boxing in C#**</span></span>

    ```csharp
    // boolean value type is boxed into object boxedMyVar on the heap
    bool myVar = true;
    object boxedMyVar = myVar;
    ```

#### <a name="repeating-code-paths"></a><span data-ttu-id="0b41e-152">重複的程式碼路徑</span><span class="sxs-lookup"><span data-stu-id="0b41e-152">Repeating code paths</span></span>

<span data-ttu-id="0b41e-153">任何重複的 Unity 回呼函式 (亦即</span><span class="sxs-lookup"><span data-stu-id="0b41e-153">Any repeating Unity callback functions (i.e</span></span> <span data-ttu-id="0b41e-154">Update)，每秒和/或每個畫面格會執行許多次，都應該小心地撰寫。</span><span class="sxs-lookup"><span data-stu-id="0b41e-154">Update) that are executed many times per second and/or frame should be written carefully.</span></span> <span data-ttu-id="0b41e-155">在此，任何高成本的作業都會對效能產生巨大且一致的影響。</span><span class="sxs-lookup"><span data-stu-id="0b41e-155">Any expensive operations here will have huge and consistent impact on performance.</span></span>

1) <span data-ttu-id="0b41e-156">**空白的回呼函式**</span><span class="sxs-lookup"><span data-stu-id="0b41e-156">**Empty callback functions**</span></span>

    <span data-ttu-id="0b41e-157">雖然在您的應用程式中保留下列程式碼可能看似無害，特別是因為每個 Unity 指令碼都會使用 Update 方法自動初始化，但這些空白回呼可能會變得昂貴。</span><span class="sxs-lookup"><span data-stu-id="0b41e-157">Although the code below may seem innocent to leave in your application, especially since every Unity script auto-initializes with an Update method, these empty callbacks can become expensive.</span></span> <span data-ttu-id="0b41e-158">Unity 會在未受管理與受管理的程式碼界限 (在 UnityEngine 程式碼與您的應用程式程式碼) 之間來回操作。</span><span class="sxs-lookup"><span data-stu-id="0b41e-158">Unity operates back and forth between an unmanaged and managed code boundary, between UnityEngine code and your application code.</span></span> <span data-ttu-id="0b41e-159">即使沒有要執行的內容，透過此橋接器切換內容的成本也相當高。</span><span class="sxs-lookup"><span data-stu-id="0b41e-159">Context switching over this bridge is fairly expensive, even if there's nothing to execute.</span></span> <span data-ttu-id="0b41e-160">如果您應用程式的數百個 GameObject 具有包含空白重複 Unity 回呼的元件，這會變得特別有問題。</span><span class="sxs-lookup"><span data-stu-id="0b41e-160">This becomes especially problematic if your app has 100s of GameObjects with components that have empty repeating Unity callbacks.</span></span>

    ```CS
    void Update()
    {
    }
    ```

>[!NOTE]
> <span data-ttu-id="0b41e-161">Update() 是這個效能問題最常見的表現，但其他重複的 Unity 回呼 (例如下列情況) 可能會同樣不良 (若非更差狀況)：FixedUpdate()、LateUpdate()、OnPostRender"、OnPreRender()、OnRenderImage() 等等。</span><span class="sxs-lookup"><span data-stu-id="0b41e-161">Update() is the most common manifestation of this performance issue but other repeating Unity callbacks, such as the following can be equally as bad, if not worse: FixedUpdate(), LateUpdate(), OnPostRender", OnPreRender(), OnRenderImage(), etc.</span></span> 

2) <span data-ttu-id="0b41e-162">**偏好每個畫面格執行一次的作業**</span><span class="sxs-lookup"><span data-stu-id="0b41e-162">**Operations to favor running once per frame**</span></span>

    <span data-ttu-id="0b41e-163">下列 Unity API 是許多全像攝影應用程式的常見作業。</span><span class="sxs-lookup"><span data-stu-id="0b41e-163">The following Unity APIs are common operations for many Holographic Apps.</span></span> <span data-ttu-id="0b41e-164">雖然不一定能夠這麼做，但這些函式的結果通常可計算一次，且結果會在指定畫面格的整個應用程式中重複使用。</span><span class="sxs-lookup"><span data-stu-id="0b41e-164">Although not always possible, the results from these functions can commonly be computed once and the results reutilized across the application for a given frame.</span></span>

    <span data-ttu-id="0b41e-165">a) 最好具有專用的單一類別或服務來處理場景中的注視 Raycast，然後在所有其他場景元件中重複使用這個結果，而不是每個元件都進行重複且相同的 Raycast 作業。</span><span class="sxs-lookup"><span data-stu-id="0b41e-165">a) It's good practice to have a dedicated Singleton class or service to handle your gaze Raycast into the scene and then reuse this result in all other scene components, instead of making repeated and identical Raycast operations by each component.</span></span> <span data-ttu-id="0b41e-166">有些應用程式可能需要不同來源，或是針對不同 [LayerMasks](https://docs.unity3d.com/ScriptReference/LayerMask.html) 的 Raycast。</span><span class="sxs-lookup"><span data-stu-id="0b41e-166">Some applications may require raycasts from different origins or against different [LayerMasks](https://docs.unity3d.com/ScriptReference/LayerMask.html).</span></span>
    
    ```csharp
        UnityEngine.Physics.Raycast()
        UnityEngine.Physics.RaycastAll()
    ```

    <span data-ttu-id="0b41e-167">b) 避免重複 Unity 回呼 (例如 Update()) 中的 GetComponent() 作業，方法是在 Start() 或 Awake() 中[快取參考](#cache-references)</span><span class="sxs-lookup"><span data-stu-id="0b41e-167">b) Avoid GetComponent() operations in repeated Unity callbacks like Update() by [caching references](#cache-references) in Start() or Awake()</span></span>
    
    ```csharp
        UnityEngine.Object.GetComponent()
    ```

    <span data-ttu-id="0b41e-168">c) 最佳做法是在初始化時將所有物件具現化 (若可能)，並使用[物件集區](#object-pooling)，以在應用程式的整個執行時間回收並重複使用 GameObject</span><span class="sxs-lookup"><span data-stu-id="0b41e-168">c) It's good practice to instantiate all objects, if possible, at initialization and use [object pooling](#object-pooling) to recycle and reuse GameObjects throughout runtime of your application</span></span>

    ```csharp
        UnityEngine.Object.Instantiate()
    ```

3) <span data-ttu-id="0b41e-169">**避免介面和虛擬結構**</span><span class="sxs-lookup"><span data-stu-id="0b41e-169">**Avoid interfaces and virtual constructs**</span></span>

    <span data-ttu-id="0b41e-170">透過介面與直接物件來叫用函式呼叫或呼叫虛擬函式，通常比使用直接結構或直接函式呼叫的成本更高。</span><span class="sxs-lookup"><span data-stu-id="0b41e-170">Invoking function calls through interfaces vs direct objects or calling virtual functions can often be much more expensive than using direct constructs or direct function calls.</span></span> <span data-ttu-id="0b41e-171">如果虛擬函式或介面不是必要的，則應該將其移除。</span><span class="sxs-lookup"><span data-stu-id="0b41e-171">If the virtual function or interface is unnecessary, then it should be removed.</span></span> <span data-ttu-id="0b41e-172">不過，如果利用這些方法可簡化開發共同作業、程式碼可讀性和程式碼維護性，則取捨之下，這些方法所造成的效能影響就有其價值了。</span><span class="sxs-lookup"><span data-stu-id="0b41e-172">However, the performance hit for these approaches is worth the trade-off if using them simplifies development collaboration, code readability, and code maintainability.</span></span>

    <span data-ttu-id="0b41e-173">一般來說，建議不要將欄位和函式標示為虛擬，除非有清楚的預期需要覆寫這個成員。</span><span class="sxs-lookup"><span data-stu-id="0b41e-173">Generally, the recommendation is to not mark fields and functions as virtual unless there's a clear expectation that this member needs to be overwritten.</span></span> <span data-ttu-id="0b41e-174">對於在每個畫面格上呼叫多次的高頻率程式碼路徑，或甚至是每個畫面格呼叫一次 (例如 `UpdateUI()` 方法)，都應該特別小心。</span><span class="sxs-lookup"><span data-stu-id="0b41e-174">One should be especially careful around high-frequency code paths that are called many times per frame or even once per frame such as an `UpdateUI()` method.</span></span>

4) <span data-ttu-id="0b41e-175">**避免以傳值方式傳遞結構**</span><span class="sxs-lookup"><span data-stu-id="0b41e-175">**Avoid passing structs by value**</span></span>

    <span data-ttu-id="0b41e-176">不同於類別，結構是實值類型，而當直接傳遞至函式時，會將其內容複製到新建立的實例。</span><span class="sxs-lookup"><span data-stu-id="0b41e-176">Unlike classes, structs are value-types and when passed directly to a function, their contents are copied into a newly created instance.</span></span> <span data-ttu-id="0b41e-177">此複本會增加 CPU 成本，以及堆疊上的額外記憶體。</span><span class="sxs-lookup"><span data-stu-id="0b41e-177">This copy adds CPU cost, as well as additional memory on the stack.</span></span> <span data-ttu-id="0b41e-178">針對小型結構，影響很小，因此可接受。</span><span class="sxs-lookup"><span data-stu-id="0b41e-178">For small structs, the effect is minimal and thus acceptable.</span></span> <span data-ttu-id="0b41e-179">不過，對於每個畫面格重複叫用的函式，以及接受大型結構的函式，如果可能，請將函式定義修改為以傳址方式傳遞。</span><span class="sxs-lookup"><span data-stu-id="0b41e-179">However, for functions repeatedly invoked every frame as well as functions taking large structs, if possible modify the function definition to pass by reference.</span></span> [<span data-ttu-id="0b41e-180">請於此處深入了解</span><span class="sxs-lookup"><span data-stu-id="0b41e-180">Learn more here</span></span>](/dotnet/csharp/programming-guide/classes-and-structs/how-to-know-the-difference-passing-a-struct-and-passing-a-class-to-a-method)

#### <a name="miscellaneous"></a><span data-ttu-id="0b41e-181">其他</span><span class="sxs-lookup"><span data-stu-id="0b41e-181">Miscellaneous</span></span>

1) <span data-ttu-id="0b41e-182">**物理特性**</span><span class="sxs-lookup"><span data-stu-id="0b41e-182">**Physics**</span></span>

    <span data-ttu-id="0b41e-183">a) 一般而言，改善物理特性最簡單的方式，是限制花費在「物理特性」上的時間量，或每秒的反覆運算次數。</span><span class="sxs-lookup"><span data-stu-id="0b41e-183">a) Generally, the easiest way to improve physics is to limit the amount of time spent on Physics or the number of iterations per second.</span></span> <span data-ttu-id="0b41e-184">這會降低模擬準確度。</span><span class="sxs-lookup"><span data-stu-id="0b41e-184">This will reduce simulation accuracy.</span></span> <span data-ttu-id="0b41e-185">請參閱 Unity 中的 [TimeManager](https://docs.unity3d.com/Manual/class-TimeManager.html)</span><span class="sxs-lookup"><span data-stu-id="0b41e-185">See [TimeManager](https://docs.unity3d.com/Manual/class-TimeManager.html) in Unity</span></span>

    <span data-ttu-id="0b41e-186">b) Unity 中的碰撞器類型具有廣泛不同的效能特性。</span><span class="sxs-lookup"><span data-stu-id="0b41e-186">b) The types of colliders in Unity have widely different performance characteristics.</span></span> <span data-ttu-id="0b41e-187">下列順序從左至右列出最高效能的碰撞器到最低效能的碰撞器。</span><span class="sxs-lookup"><span data-stu-id="0b41e-187">The order below lists the most performant colliders to least performant colliders from left to right.</span></span> <span data-ttu-id="0b41e-188">請務必避免網格碰撞器，這比基本碰撞器的成本高出許多。</span><span class="sxs-lookup"><span data-stu-id="0b41e-188">It's important to avoid Mesh Colliders, which are substantially more expensive than the primitive colliders.</span></span>

    <span data-ttu-id="0b41e-189">球紋 < 膠囊 < 方塊 <<< 網格 (凸面) < 網格 (非凸面)</span><span class="sxs-lookup"><span data-stu-id="0b41e-189">Sphere < Capsule < Box <<< Mesh (Convex) < Mesh (non-Convex)</span></span>

    <span data-ttu-id="0b41e-190">如需詳細資訊，請參閱 [Unity 物理特性最佳做法](https://unity3d.com/learn/tutorials/topics/physics/physics-best-practices)</span><span class="sxs-lookup"><span data-stu-id="0b41e-190">See [Unity Physics Best Practices](https://unity3d.com/learn/tutorials/topics/physics/physics-best-practices) for more info</span></span>

2) <span data-ttu-id="0b41e-191">**動畫**</span><span class="sxs-lookup"><span data-stu-id="0b41e-191">**Animations**</span></span>

    <span data-ttu-id="0b41e-192">停用閒置動畫，方法是停用 Animator 元件 (停用遊戲物件不會有相同的效果)。</span><span class="sxs-lookup"><span data-stu-id="0b41e-192">Disable idle animations by disabling the Animator component (disabling the game object won't have the same effect).</span></span> <span data-ttu-id="0b41e-193">避免設計出 Animator 所在迴圈將值設定為相同內容的模式。</span><span class="sxs-lookup"><span data-stu-id="0b41e-193">Avoid design patterns where an animator sits in a loop setting a value to the same thing.</span></span> <span data-ttu-id="0b41e-194">這項技術會有相當大的負擔，對應用程式則沒有任何影響。</span><span class="sxs-lookup"><span data-stu-id="0b41e-194">There's considerable overhead for this technique, with no effect on the application.</span></span> [<span data-ttu-id="0b41e-195">請於此處深入了解。</span><span class="sxs-lookup"><span data-stu-id="0b41e-195">Learn more here.</span></span>](https://docs.unity3d.com/Manual/MecanimPeformanceandOptimization.html)

3) <span data-ttu-id="0b41e-196">**複雜演算法**</span><span class="sxs-lookup"><span data-stu-id="0b41e-196">**Complex algorithms**</span></span>

    <span data-ttu-id="0b41e-197">如果您的應用程式是使用複雜演算法，例如反向運動、路徑尋找等等，請試著尋找較簡單的方法，或調整其效能的相關設定</span><span class="sxs-lookup"><span data-stu-id="0b41e-197">If your application is using complex algorithms such as inverse kinematics, path finding, etc, look to find a simpler approach or adjust relevant settings for their performance</span></span>

## <a name="cpu-to-gpu-performance-recommendations"></a><span data-ttu-id="0b41e-198">CPU 對 GPU 效能建議</span><span class="sxs-lookup"><span data-stu-id="0b41e-198">CPU-to-GPU performance recommendations</span></span>

<span data-ttu-id="0b41e-199">一般來說，CPU 對 GPU 的效能會降至提交到圖形卡的 **繪製呼叫**。</span><span class="sxs-lookup"><span data-stu-id="0b41e-199">Generally, CPU-to-GPU performance comes down to the **draw calls** submitted to the graphics card.</span></span> <span data-ttu-id="0b41e-200">為改善效能，必須策略性地將繪製呼叫 **降低** 或 **重建**，以獲得最佳結果。</span><span class="sxs-lookup"><span data-stu-id="0b41e-200">To improve performance, draw calls need to be strategically **a) reduced** or **b) restructured** for optimal results.</span></span> <span data-ttu-id="0b41e-201">由於繪製呼叫本身會耗用大量資源，因此減少繪製呼叫會降低所需的整體工作量。</span><span class="sxs-lookup"><span data-stu-id="0b41e-201">Since draw calls themselves are resource-intensive, reducing them will reduce overall work required.</span></span> <span data-ttu-id="0b41e-202">此外，在繪製呼叫之間的狀態變更需要在圖形驅動程式中進行高成本驗證和轉譯步驟，因此，重建應用程式的繪製呼叫來限制狀態變更 (亦即</span><span class="sxs-lookup"><span data-stu-id="0b41e-202">Further, state changes between draw calls require costly validation and translation steps in the graphics driver and thus, restructuring of your application's draw calls to limit state changes (i.e</span></span> <span data-ttu-id="0b41e-203">不同的資料等) 可以提升效能。</span><span class="sxs-lookup"><span data-stu-id="0b41e-203">different materials, etc) can boost performance.</span></span>

<span data-ttu-id="0b41e-204">Unity 有一篇很棒的文章，可讓您大致瞭解並探討其平台的批次繪製呼叫。</span><span class="sxs-lookup"><span data-stu-id="0b41e-204">Unity has a great article that gives an overview and dives into batching draw calls for their platform.</span></span>
- [<span data-ttu-id="0b41e-205">Unity 繪製呼叫批次處理</span><span class="sxs-lookup"><span data-stu-id="0b41e-205">Unity Draw Call Batching</span></span>](https://docs.unity3d.com/Manual/DrawCallBatching.html)

#### <a name="single-pass-instanced-rendering"></a><span data-ttu-id="0b41e-206">單通道執行個體化轉譯</span><span class="sxs-lookup"><span data-stu-id="0b41e-206">Single pass instanced rendering</span></span>

<span data-ttu-id="0b41e-207">Unity 中的 [單通道執行個體化轉譯] 可讓您將每個眼球的繪製呼叫降低至一個執行個體化的繪製呼叫。</span><span class="sxs-lookup"><span data-stu-id="0b41e-207">Single Pass Instanced Rendering in Unity allows for draw calls for each eye to be reduced down to one instanced draw call.</span></span> <span data-ttu-id="0b41e-208">由於兩個繪製呼叫之間的快取一致性，GPU 上也有一些效能改善。</span><span class="sxs-lookup"><span data-stu-id="0b41e-208">Because of cache coherency between two draw calls, there's also some performance improvement on the GPU as well.</span></span>

<span data-ttu-id="0b41e-209">若要在 Unity 專案中啟用這項功能</span><span class="sxs-lookup"><span data-stu-id="0b41e-209">To enable this feature in your Unity Project</span></span>
1)  <span data-ttu-id="0b41e-210">開啟 [Player XR 設定] (移至 [編輯] > [專案設定] > [播放器] > [XR 設定])</span><span class="sxs-lookup"><span data-stu-id="0b41e-210">Open **Player XR Settings** (go to **Edit** > **Project Settings** > **Player** > **XR Settings**)</span></span>
2) <span data-ttu-id="0b41e-211">從 [立體聲轉譯方法] 下拉式功能表中，選取 [單通道執行個體化] (必須核取 [支援的虛擬實境] 核取方塊)</span><span class="sxs-lookup"><span data-stu-id="0b41e-211">Select **Single Pass Instanced** from the **Stereo Rendering Method** drop-down menu (**Virtual Reality Supported** checkbox must be checked)</span></span>

<span data-ttu-id="0b41e-212">如需此轉譯方法的詳細資料，請在 Unity 中參閱下列文章。</span><span class="sxs-lookup"><span data-stu-id="0b41e-212">Read the following articles from Unity for details with this rendering approach.</span></span>
- [<span data-ttu-id="0b41e-213">如何使用進階的立體聲轉譯將 AR 和 VR 效能最大化</span><span class="sxs-lookup"><span data-stu-id="0b41e-213">How to maximize AR and VR performance with advanced stereo rendering</span></span>](https://blogs.unity3d.com/2017/11/21/how-to-maximize-ar-and-vr-performance-with-advanced-stereo-rendering/)
- [<span data-ttu-id="0b41e-214">單通道執行個體</span><span class="sxs-lookup"><span data-stu-id="0b41e-214">Single Pass Instancing</span></span>](https://docs.unity3d.com/Manual/SinglePassInstancing.html) 

>[!NOTE]
> <span data-ttu-id="0b41e-215">如果開發人員已經有非針對執行個體撰寫的現有自訂著色器，就會發生單通道執行個體化轉譯的一個常見問題。</span><span class="sxs-lookup"><span data-stu-id="0b41e-215">One common issue with Single Pass Instanced Rendering occurs if developers already have existing custom shaders not written for instancing.</span></span> <span data-ttu-id="0b41e-216">啟用這項功能之後，開發人員可能會注意到，有些 GameObject 只會在單一眼球中轉譯。</span><span class="sxs-lookup"><span data-stu-id="0b41e-216">After enabling this feature, developers may notice some GameObjects only render in one eye.</span></span> <span data-ttu-id="0b41e-217">這是因為相關聯的自訂著色器沒有適當的執行個體屬性。</span><span class="sxs-lookup"><span data-stu-id="0b41e-217">This is because the associated custom shaders do not have the appropriate properties for instancing.</span></span>
>
> <span data-ttu-id="0b41e-218">如需解決此問題的方法，請參閱 Unity 中的[適用於 HoloLens 的單通道立體聲轉譯](https://docs.unity3d.com/Manual/SinglePassStereoRenderingHoloLens.html)</span><span class="sxs-lookup"><span data-stu-id="0b41e-218">See [Single Pass Stereo Rendering for HoloLens](https://docs.unity3d.com/Manual/SinglePassStereoRenderingHoloLens.html) from Unity for how to address this problem</span></span>

#### <a name="static-batching"></a><span data-ttu-id="0b41e-219">靜態批次處理</span><span class="sxs-lookup"><span data-stu-id="0b41e-219">Static batching</span></span>

<span data-ttu-id="0b41e-220">Unity 能夠批次處理許多靜態物件，以減少對 GPU 的繪製呼叫。</span><span class="sxs-lookup"><span data-stu-id="0b41e-220">Unity is able to batch many static objects to reduce draw calls to the GPU.</span></span> <span data-ttu-id="0b41e-221">靜態批次處理適用於 Unity 中大部分的 [轉譯器](https://docs.unity3d.com/ScriptReference/Renderer.html)物件，這些物件會 **1) 共用相同的資料** 且 **2) 全部標示為 [靜態]** (在 Unity 中選取物件，然後選取偵測器右上方的核取方塊)。</span><span class="sxs-lookup"><span data-stu-id="0b41e-221">Static Batching works for most [Renderer](https://docs.unity3d.com/ScriptReference/Renderer.html) objects in Unity that **1) share the same material** and **2) are all marked as *Static*** (Select an object in Unity and select the checkbox in the top right of the inspector).</span></span> <span data-ttu-id="0b41e-222">標記為「靜態」的 GameObject 無法在整個應用程式的執行時間移動。</span><span class="sxs-lookup"><span data-stu-id="0b41e-222">GameObjects marked as *Static* cannot be moved throughout your application's runtime.</span></span> <span data-ttu-id="0b41e-223">因此，靜態批次處理可能很容易在 HoloLens 上運用，因為幾乎每個物件都必須放置、移動、調整等等。針對沉浸式頭戴裝置，靜態批次處理可以大幅減少繪製呼叫，因而改善效能。</span><span class="sxs-lookup"><span data-stu-id="0b41e-223">Thus, static batching can be difficult to leverage on HoloLens where virtually every object needs to be placed, moved, scaled, etc. For immersive headsets, static batching can dramatically reduce draw calls and thus improve performance.</span></span>

<span data-ttu-id="0b41e-224">如需詳細資料，請參閱[在 Unity 中繪製呼叫批次處理](https://docs.unity3d.com/Manual/DrawCallBatching.html)中的「靜態批次處理」。</span><span class="sxs-lookup"><span data-stu-id="0b41e-224">Read *Static Batching* under [Draw Call Batching in Unity](https://docs.unity3d.com/Manual/DrawCallBatching.html) for more details.</span></span>

#### <a name="dynamic-batching"></a><span data-ttu-id="0b41e-225">動態批次處理</span><span class="sxs-lookup"><span data-stu-id="0b41e-225">Dynamic batching</span></span>

<span data-ttu-id="0b41e-226">由於將 HoloLens 開發的物件標示為「靜態」會有問題，因此動態批次處理可能是彌補這項缺乏功能的絕佳工具。</span><span class="sxs-lookup"><span data-stu-id="0b41e-226">Since it's problematic to mark objects as *Static* for HoloLens development, dynamic batching can be a great tool to compensate for this lacking feature.</span></span> <span data-ttu-id="0b41e-227">該功能也適用於沉浸式頭戴裝置。</span><span class="sxs-lookup"><span data-stu-id="0b41e-227">It can also be useful on immersive headsets, as well.</span></span> <span data-ttu-id="0b41e-228">不過，Unity 中的動態批次處理可能難以啟用，因為 GameObject 必須 **a) 共用相同的資料** 且 **b) 符合一長串的其他條件**。</span><span class="sxs-lookup"><span data-stu-id="0b41e-228">However, dynamic batching in Unity can be difficult to enable because GameObjects must **a) share the same Material** and **b) meet a long list of other criteria**.</span></span>

<span data-ttu-id="0b41e-229">如需完整清單，請參閱[在 Unity 中繪製呼叫批次處理](https://docs.unity3d.com/Manual/DrawCallBatching.html)中的「動態批次處理」。</span><span class="sxs-lookup"><span data-stu-id="0b41e-229">Read *Dynamic Batching* under [Draw Call Batching in Unity](https://docs.unity3d.com/Manual/DrawCallBatching.html) for the full list.</span></span> <span data-ttu-id="0b41e-230">最常見的情況是，因為相關聯的網格資料不能超過 300 個頂點，所以 GameObject 會變成無效而無法動態地進行批次處理。</span><span class="sxs-lookup"><span data-stu-id="0b41e-230">Most commonly, GameObjects become invalid to be batched dynamically, because the associated mesh data can be no more than 300 vertices.</span></span>

#### <a name="other-techniques"></a><span data-ttu-id="0b41e-231">其他技術</span><span class="sxs-lookup"><span data-stu-id="0b41e-231">Other techniques</span></span>

<span data-ttu-id="0b41e-232">只有在多個 GameObject 可以共用相同的資料時，才會進行批次處理。</span><span class="sxs-lookup"><span data-stu-id="0b41e-232">Batching can only occur if multiple GameObjects are able to share the same material.</span></span> <span data-ttu-id="0b41e-233">一般而言，這會因為需要 GameObject 而受到封鎖，使其各自的材質獲得獨特的紋理。</span><span class="sxs-lookup"><span data-stu-id="0b41e-233">Typically, this will be blocked by the need for GameObjects to have a unique texture for their respective Material.</span></span> <span data-ttu-id="0b41e-234">通常會將「紋理」結合成一個大「紋理」，這是一種稱為[紋理圖集](https://en.wikipedia.org/wiki/Texture_atlas)的方法。</span><span class="sxs-lookup"><span data-stu-id="0b41e-234">It's common to combine Textures into one big Texture, a method known as [Texture Atlasing](https://en.wikipedia.org/wiki/Texture_atlas).</span></span>

<span data-ttu-id="0b41e-235">此外，最好是在可能且合理的情況下，將網格結合成一個 GameObject。</span><span class="sxs-lookup"><span data-stu-id="0b41e-235">Furthermore, it's preferable to combine meshes into one GameObject where possible and reasonable.</span></span> <span data-ttu-id="0b41e-236">Unity 中的每個轉譯器都會有其相關聯的繪製呼叫，而不會在單一轉譯器下提交合併的網格。</span><span class="sxs-lookup"><span data-stu-id="0b41e-236">Each Renderer in Unity will have its associated draw call(s) versus submitting a combined mesh under one Renderer.</span></span>

>[!NOTE]
> <span data-ttu-id="0b41e-237">在執行時間修改 Renderer.material 的屬性，會建立一份資料複本，因此可能會中斷批次處理。</span><span class="sxs-lookup"><span data-stu-id="0b41e-237">Modifying properties of Renderer.material at runtime will create a copy of the Material and thus potentially break batching.</span></span> <span data-ttu-id="0b41e-238">使用 Renderer.sharedMaterial 來修改 Gameobject 之間的共用材質屬性。</span><span class="sxs-lookup"><span data-stu-id="0b41e-238">Use Renderer.sharedMaterial to modify shared material properties across GameObjects.</span></span>

## <a name="gpu-performance-recommendations"></a><span data-ttu-id="0b41e-239">GPU 效能建議</span><span class="sxs-lookup"><span data-stu-id="0b41e-239">GPU performance recommendations</span></span>

<span data-ttu-id="0b41e-240">深入瞭解如何[將 Unity 中的圖形轉譯進行最佳化](https://unity3d.com/learn/tutorials/temas/performance-optimization/optimizing-graphics-rendering-unity-games)</span><span class="sxs-lookup"><span data-stu-id="0b41e-240">Learn more about [optimizing graphics rendering in Unity](https://unity3d.com/learn/tutorials/temas/performance-optimization/optimizing-graphics-rendering-unity-games)</span></span>

### <a name="optimize-depth-buffer-sharing"></a><span data-ttu-id="0b41e-241">將深度緩衝區共用進行最佳化</span><span class="sxs-lookup"><span data-stu-id="0b41e-241">Optimize depth buffer sharing</span></span>

<span data-ttu-id="0b41e-242">建議您啟用 [Player XR 設定] 下的 [深度緩衝區共用]，以將[全像投影穩定性](../platform-capabilities-and-apis/Hologram-stability.md)進行最佳化。</span><span class="sxs-lookup"><span data-stu-id="0b41e-242">It's recommended to enable **Depth buffer sharing** under **Player XR Settings** to optimize for [hologram stability](../platform-capabilities-and-apis/Hologram-stability.md).</span></span> <span data-ttu-id="0b41e-243">不過，使用此設定來啟用深度延遲階段重新投影時，建議選取 [16 位元深度格式]，而不是 [24 位元深度格式]。</span><span class="sxs-lookup"><span data-stu-id="0b41e-243">When enabling depth-based late-stage reprojection with this setting however, it's recommended to select **16-bit depth format** instead of **24-bit depth format**.</span></span> <span data-ttu-id="0b41e-244">16 位元深度緩衝區會大幅降低與深度緩衝區流量相關聯的頻寬 (和電源)。</span><span class="sxs-lookup"><span data-stu-id="0b41e-244">The 16-bit depth buffers will drastically reduce the bandwidth (and thus power) associated with depth buffer traffic.</span></span> <span data-ttu-id="0b41e-245">這在降低電源和改善效能方面都是一大優勢。</span><span class="sxs-lookup"><span data-stu-id="0b41e-245">This can be a big win both in power reduction and performance improvement.</span></span> <span data-ttu-id="0b41e-246">不過，使用「16 位元深度格式」可能會有兩個負面結果。</span><span class="sxs-lookup"><span data-stu-id="0b41e-246">However, there are two possible negative outcomes by using *16-bit depth format*.</span></span>

<span data-ttu-id="0b41e-247">**Z 衝突**</span><span class="sxs-lookup"><span data-stu-id="0b41e-247">**Z-Fighting**</span></span>

<span data-ttu-id="0b41e-248">降低的深度範圍精確度會使 [z 衝突](https://en.wikipedia.org/wiki/Z-fighting)較可能發生在 16 位元而非 24 位元。</span><span class="sxs-lookup"><span data-stu-id="0b41e-248">The reduced depth range fidelity makes [z-fighting](https://en.wikipedia.org/wiki/Z-fighting) more likely to occur with 16 bit than 24-bit.</span></span> <span data-ttu-id="0b41e-249">若要避免這些成品，請修改 [Unity 攝影機](https://docs.unity3d.com/Manual/class-Camera.html)的近/遠裁剪平面，以降低精確度。</span><span class="sxs-lookup"><span data-stu-id="0b41e-249">To avoid these artifacts, modify the near/far clip planes of the [Unity camera](https://docs.unity3d.com/Manual/class-Camera.html) to account for the lower precision.</span></span> <span data-ttu-id="0b41e-250">對於 HoloLens 型應用程式，50 m 的遠裁剪平面而非 Unity 預設的 1000 m 裁剪平面通常可以排除任何 z 衝突。</span><span class="sxs-lookup"><span data-stu-id="0b41e-250">For HoloLens-based applications, a far clip plane of 50 m instead of the Unity default 1000 m can generally eliminate any z-fighting.</span></span>

<span data-ttu-id="0b41e-251">**已停用的樣板緩衝區**</span><span class="sxs-lookup"><span data-stu-id="0b41e-251">**Disabled Stencil Buffer**</span></span>

<span data-ttu-id="0b41e-252">當 Unity 建立[具有 16 位元深度的轉譯紋理](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html)時，並不會建立樣板緩衝區。</span><span class="sxs-lookup"><span data-stu-id="0b41e-252">When Unity creates a [Render Texture with 16-bit depth](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html), there's no stencil buffer created.</span></span> <span data-ttu-id="0b41e-253">根據 Unity 文件選取 24 位元深度格式，將會建立 24 位元的 z 緩衝區，以及 [8 位元樣板緩衝區] (https://docs.unity3d.com/Manual/SL-Stencil.html) (如果裝置適用 32 位元，這通常是 HoloLens 之類的情況)。</span><span class="sxs-lookup"><span data-stu-id="0b41e-253">Selecting 24-bit depth format, per Unity documentation, will create a 24-bit z-buffer, as well as an [8-bit stencil buffer] (https://docs.unity3d.com/Manual/SL-Stencil.html) (if 32-bit is applicable on a device, which is generally the case such as HoloLens).</span></span>

### <a name="avoid-full-screen-effects"></a><span data-ttu-id="0b41e-254">避免全螢幕效果</span><span class="sxs-lookup"><span data-stu-id="0b41e-254">Avoid full-screen effects</span></span>

<span data-ttu-id="0b41e-255">在全螢幕上操作的技術可能很昂貴，因為其數量級是每個畫面格數百萬個作業。</span><span class="sxs-lookup"><span data-stu-id="0b41e-255">Techniques that operate on the full screen can be expensive since their order of magnitude is millions of operations every frame.</span></span> <span data-ttu-id="0b41e-256">建議您避免[後置處理效果](https://docs.unity3d.com/Manual/PostProcessingOverview.html) (例如消除鋸齒、綻開等等)。</span><span class="sxs-lookup"><span data-stu-id="0b41e-256">It's recommended to avoid [post-processing effects](https://docs.unity3d.com/Manual/PostProcessingOverview.html) such as anti-aliasing, bloom, and more.</span></span>

### <a name="optimal-lighting-settings"></a><span data-ttu-id="0b41e-257">最佳光源設定</span><span class="sxs-lookup"><span data-stu-id="0b41e-257">Optimal lighting settings</span></span>

<span data-ttu-id="0b41e-258">Unity 中的[即時全域照明](https://docs.unity3d.com/Manual/GIIntro.html)可以提供優異的視覺結果，但牽涉到高成本的光源計算。</span><span class="sxs-lookup"><span data-stu-id="0b41e-258">[Real-time Global Illumination](https://docs.unity3d.com/Manual/GIIntro.html) in Unity can provide outstanding visual results but involves expensive lighting calculations.</span></span> <span data-ttu-id="0b41e-259">建議您透過 [視窗] > [轉譯] > [光源設定] > 取消核取 [即時全域照明]，停用每個 Unity 場景檔案的即時全域照明。</span><span class="sxs-lookup"><span data-stu-id="0b41e-259">We recommended disabling real-time Global Illumination for every Unity scene file via **Window** > **Rendering** > **Lighting Settings** > Uncheck **Real-time Global Illumination**.</span></span>

<span data-ttu-id="0b41e-260">此外，建議停用所有陰影轉換，因為這些也會在 Unity 場景上增加高成本的 GPU 通道。</span><span class="sxs-lookup"><span data-stu-id="0b41e-260">Furthermore, it's recommended to disable all shadow casting as these also add expensive GPU passes onto a Unity scene.</span></span> <span data-ttu-id="0b41e-261">可針對光源停用陰影，也可以透過 [品質] 設定進行全面性控制。</span><span class="sxs-lookup"><span data-stu-id="0b41e-261">Shadows can be disable per light but can also be controlled holistically via Quality settings.</span></span>

<span data-ttu-id="0b41e-262">[編輯] > [專案設定]，然後選取 [品質] 類別 > 針對 UWP 平台，選取 [低品質]。</span><span class="sxs-lookup"><span data-stu-id="0b41e-262">**Edit** > **Project Settings**, then select the **Quality** category > Select **Low Quality** for the UWP Platform.</span></span> <span data-ttu-id="0b41e-263">使用者也可以只將 [陰影] 屬性設定為 [停用陰影]。</span><span class="sxs-lookup"><span data-stu-id="0b41e-263">One can also just set the **Shadows** property to **Disable Shadows**.</span></span>

<span data-ttu-id="0b41e-264">在 Unity 中建議您對模型使用烘焙光源。</span><span class="sxs-lookup"><span data-stu-id="0b41e-264">We recommended that you use baked lighting with your models in Unity.</span></span>

### <a name="reduce-poly-count"></a><span data-ttu-id="0b41e-265">減少多邊形計數</span><span class="sxs-lookup"><span data-stu-id="0b41e-265">Reduce poly count</span></span>

<span data-ttu-id="0b41e-266">多邊形計數會縮減，方法是</span><span class="sxs-lookup"><span data-stu-id="0b41e-266">Polygon count is reduced by either</span></span>
1) <span data-ttu-id="0b41e-267">從場景移除物件</span><span class="sxs-lookup"><span data-stu-id="0b41e-267">Removing objects from a scene</span></span>
2) <span data-ttu-id="0b41e-268">減去資產，以減少指定網格的多邊形數目</span><span class="sxs-lookup"><span data-stu-id="0b41e-268">Asset decimation, which reduces the number of polygons for a given mesh</span></span>
3) <span data-ttu-id="0b41e-269">將[詳細資料的層級 (LOD) 系統](https://docs.unity3d.com/Manual/LevelOfDetail.html)實作到您的應用程式中，以相同幾何的較低多邊形版本呈現遙遠的物件</span><span class="sxs-lookup"><span data-stu-id="0b41e-269">Implementing a [Level of Detail (LOD) System](https://docs.unity3d.com/Manual/LevelOfDetail.html) into your application, which renders far away objects with lower-polygon version of the same geometry</span></span>

### <a name="understanding-shaders-in-unity"></a><span data-ttu-id="0b41e-270">瞭解 Unity 中的著色器</span><span class="sxs-lookup"><span data-stu-id="0b41e-270">Understanding shaders in Unity</span></span>

<span data-ttu-id="0b41e-271">比較效能中著色器的簡單近似值，是識別在執行時間每個執行的平均作業數目。</span><span class="sxs-lookup"><span data-stu-id="0b41e-271">An easy approximation to compare shaders in performance is to identify the average number of operations each executes at runtime.</span></span> <span data-ttu-id="0b41e-272">這可以在 Unity 中輕鬆完成。</span><span class="sxs-lookup"><span data-stu-id="0b41e-272">This can be done easily in Unity.</span></span>

1) <span data-ttu-id="0b41e-273">選取您的著色器資產或選取材質，然後在偵測器視窗的右上角，選取後接 [選取著色器] 的齒輪圖示</span><span class="sxs-lookup"><span data-stu-id="0b41e-273">Select your shader asset or select a material, then in the top-right corner of the inspector window, select the gear icon followed by **"Select Shader"**</span></span>

    ![選取 Unity 中的著色器](images/Select-shader-unity.png)
2) <span data-ttu-id="0b41e-275">選取著色器資產後，選取偵測器視窗下的 [編譯並顯示程式碼] 按鈕</span><span class="sxs-lookup"><span data-stu-id="0b41e-275">With the shader asset selected, select the **"Compile and show code"** button under the inspector window</span></span>

    ![在 Unity 中編譯著色器程式碼](images/compile-shader-code-unity.PNG)

3) <span data-ttu-id="0b41e-277">編譯之後，在結果中尋找統計資料區段，其中包含頂點和像素著色器的不同作業數目 (注意：像素著色器通常也稱為片段著色器)</span><span class="sxs-lookup"><span data-stu-id="0b41e-277">After compiling, look for the statistics section in the results with the number of different operations for both the vertex and pixel shader (Note: pixel shaders are often also called fragment shaders)</span></span>

    ![Unity 標準著色器作業](images/unity-standard-shader-compilation.png)

#### <a name="optimize-pixel-shaders"></a><span data-ttu-id="0b41e-279">最佳化像素著色器</span><span class="sxs-lookup"><span data-stu-id="0b41e-279">Optimize pixel shaders</span></span>

<span data-ttu-id="0b41e-280">使用上述方法查看編譯的統計資料結果，[片段著色器](https://en.wikipedia.org/wiki/Shader#Pixel_shaders)通常會比 [頂點著色器](https://en.wikipedia.org/wiki/Shader#Vertex_shaders)平均執行更多作業。</span><span class="sxs-lookup"><span data-stu-id="0b41e-280">Looking at the compiled statistic results using the method above, the [fragment shader](https://en.wikipedia.org/wiki/Shader#Pixel_shaders) will generally execute more operations than the [vertex shader](https://en.wikipedia.org/wiki/Shader#Vertex_shaders), on average.</span></span> <span data-ttu-id="0b41e-281">片段著色器 (也稱為像素著色器) 會針對螢幕輸出上的每個像素執行，而頂點著色器只會針對繪製到螢幕的所有網格中每個頂點來執行。</span><span class="sxs-lookup"><span data-stu-id="0b41e-281">The fragment shader, also known as the pixel shader, is executed per pixel on the screen output while the vertex shader is only executed per-vertex of all meshes being drawn to the screen.</span></span>

<span data-ttu-id="0b41e-282">因此，片段著色器不只會因所有光源計算而比頂點著色器有更多的指示，片段著色器通常還會在較大的資料集上執行。</span><span class="sxs-lookup"><span data-stu-id="0b41e-282">Thus, not only do fragment shaders have more instructions than vertex shaders because of all the lighting calculations, fragment shaders are almost always executed on a larger dataset.</span></span> <span data-ttu-id="0b41e-283">例如，如果螢幕輸出是 2k 比 2k 影像，則片段著色器可執行 2,000\*2,000 = 4,000,000 次。</span><span class="sxs-lookup"><span data-stu-id="0b41e-283">For example, if the screen output is a 2k by 2k image, then the fragment shader can get executed 2,000\*2,000 = 4,000,000 times.</span></span> <span data-ttu-id="0b41e-284">如果呈現兩眼，這個數字會加倍，因為有兩個畫面。</span><span class="sxs-lookup"><span data-stu-id="0b41e-284">If rendering two eyes, this number doubles since there are two screens.</span></span> <span data-ttu-id="0b41e-285">如果混合實境應用程式有多個通道、全螢幕後置處理效果，或將多個網格轉譯為相同的像素，這個數字就會大幅增加。</span><span class="sxs-lookup"><span data-stu-id="0b41e-285">If a mixed reality application has multiple passes, full-screen post-processing effects, or rendering multiple meshes to the same pixel, this number will increase dramatically.</span></span>

<span data-ttu-id="0b41e-286">因此，減少片段著色器中的作業數目，通常可以在端點著色器中提供比最佳化更佳的效能提升。</span><span class="sxs-lookup"><span data-stu-id="0b41e-286">Therefore, reducing the number of operations in the fragment shader can generally give far greater performance gains over optimizations in the vertex shader.</span></span>

#### <a name="unity-standard-shader-alternatives"></a><span data-ttu-id="0b41e-287">Unity 標準著色器作業</span><span class="sxs-lookup"><span data-stu-id="0b41e-287">Unity Standard shader alternatives</span></span>

<span data-ttu-id="0b41e-288">您不需要使用以實體為基礎的轉譯 (PBR) 或其他高品質的著色器，而是瞭解如何利用更高的效能及更低成本的著色器。</span><span class="sxs-lookup"><span data-stu-id="0b41e-288">Instead of using a physically based rendering (PBR) or another high-quality shader, look at utilizing a more performant and cheaper shader.</span></span> <span data-ttu-id="0b41e-289">[混合實境工具組](https://github.com/Microsoft/MixedRealityToolkit-Unity)提供已針對混合實境專案進行最佳化的 [MRTK 標準著色器](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/rendering/mrtk-standard-shader)。</span><span class="sxs-lookup"><span data-stu-id="0b41e-289">The [Mixed Reality Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity) provides the [MRTK standard shader](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/rendering/mrtk-standard-shader) that has been optimized for mixed reality projects.</span></span>

<span data-ttu-id="0b41e-290">Unity 也提供無光、頂點光、擴散和其他簡化的著色器選項，相較於 Unity 標準著色器，速度會有所提升。</span><span class="sxs-lookup"><span data-stu-id="0b41e-290">Unity also provides an unlit, vertex lit, diffuse, and other simplified shader options that are faster compared to the Unity Standard shader.</span></span> <span data-ttu-id="0b41e-291">如需詳細資訊，請參閱[內建著色器的用法和效能](https://docs.unity3d.com/Manual/shader-Performance.html)。</span><span class="sxs-lookup"><span data-stu-id="0b41e-291">See [Usage and Performance of Built-in Shaders](https://docs.unity3d.com/Manual/shader-Performance.html) for more detailed information.</span></span>

#### <a name="shader-preloading"></a><span data-ttu-id="0b41e-292">著色器預先載入</span><span class="sxs-lookup"><span data-stu-id="0b41e-292">Shader preloading</span></span>

<span data-ttu-id="0b41e-293">使用「著色器預先載入」和其他訣竅，將[著色器載入時間](https://docs.unity3d.com/Manual/OptimizingShaderLoadTime.html)進行最佳化。</span><span class="sxs-lookup"><span data-stu-id="0b41e-293">Use *Shader preloading* and other tricks to optimize [shader load time](https://docs.unity3d.com/Manual/OptimizingShaderLoadTime.html).</span></span> <span data-ttu-id="0b41e-294">特別是，著色器預先載入表示您不會因為執行時間著色器編譯而看到任何停頓。</span><span class="sxs-lookup"><span data-stu-id="0b41e-294">In particular, shader preloading means you won't see any hitches due to runtime shader compilation.</span></span>

### <a name="limit-overdraw"></a><span data-ttu-id="0b41e-295">限制過度繪製</span><span class="sxs-lookup"><span data-stu-id="0b41e-295">Limit overdraw</span></span>

<span data-ttu-id="0b41e-296">在 Unity 中，使用者可以顯示其場景的過度繪製，方法是切換 [場景視圖] 左上角的 [[繪製模式] 功能表](https://docs.unity3d.com/Manual/ViewModes.html)，然後選取 [過度繪製]。</span><span class="sxs-lookup"><span data-stu-id="0b41e-296">In Unity, one can display overdraw for their scene, by toggling the [**draw mode menu**](https://docs.unity3d.com/Manual/ViewModes.html) in the top-left corner of the **Scene view** and selecting **Overdraw**.</span></span>

<span data-ttu-id="0b41e-297">一般來說，在將物件傳送至 GPU 之前，您可以將這些物件先行剔除，藉以減輕過度繪製。</span><span class="sxs-lookup"><span data-stu-id="0b41e-297">Generally, overdraw can be mitigated by culling objects ahead of time before they're sent to the GPU.</span></span> <span data-ttu-id="0b41e-298">Unity 提供針對其引擎實作[遮蔽剔除](https://docs.unity3d.com/Manual/OcclusionCulling.html)的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="0b41e-298">Unity provides details on implementing [Occlusion Culling](https://docs.unity3d.com/Manual/OcclusionCulling.html) for their engine.</span></span>

## <a name="memory-recommendations"></a><span data-ttu-id="0b41e-299">記憶體建議</span><span class="sxs-lookup"><span data-stu-id="0b41e-299">Memory recommendations</span></span>

<span data-ttu-id="0b41e-300">記憶體過度配置及解除配置的作業可能會對您的全像攝影應用程式造成不良的影響，因而導致效能不一致、凍結的畫面格和其他不利的行為。</span><span class="sxs-lookup"><span data-stu-id="0b41e-300">Excessive memory allocation & deallocation operations can have adverse effects on your holographic application, resulting in inconsistent performance, frozen frames, and other detrimental behavior.</span></span> <span data-ttu-id="0b41e-301">在 Unity 中開發時，請務必瞭解記憶體考慮，因為記憶體管理是由記憶體回收行程所控制。</span><span class="sxs-lookup"><span data-stu-id="0b41e-301">It's especially important to understand memory considerations when developing in Unity since memory management is controlled by the garbage collector.</span></span>

#### <a name="garbage-collection"></a><span data-ttu-id="0b41e-302">記憶體回收</span><span class="sxs-lookup"><span data-stu-id="0b41e-302">Garbage collection</span></span>

<span data-ttu-id="0b41e-303">當記憶體回收行程 (GC) 啟動以分析不在執行期間範圍中的物件，且需要釋放其記憶體時，全像攝影應用程式將會遺失處理記憶體回收行程的計算時間，因此可供重複使用。</span><span class="sxs-lookup"><span data-stu-id="0b41e-303">Holographic apps will lose processing compute time to the garbage collector (GC) when the GC is activated to analyze objects that are no longer in scope during execution and their memory needs to be released, so it can be made available for reuse.</span></span> <span data-ttu-id="0b41e-304">常數配置和取消配置通常需要更頻繁地執行記憶體回收行程，因而會影響效能和使用者體驗。</span><span class="sxs-lookup"><span data-stu-id="0b41e-304">Constant allocations and de-allocations will generally require the garbage collector to run more frequently, thus hurting performance and user experience.</span></span>

<span data-ttu-id="0b41e-305">Unity 提供了絕佳的頁面，詳細說明記憶體回收行程的運作方式，以及在記憶體管理方面撰寫更有效率程式碼的秘訣。</span><span class="sxs-lookup"><span data-stu-id="0b41e-305">Unity has provided an excellent page that explains in detail how the garbage collector works and tips to write more efficient code in regards to memory management.</span></span>
- [<span data-ttu-id="0b41e-306">將 Unity 遊戲中的記憶體回收行程進行最佳化</span><span class="sxs-lookup"><span data-stu-id="0b41e-306">Optimizing garbage collection in Unity games</span></span>](https://unity3d.com/learn/tutorials/topics/performance-optimization/optimizing-garbage-collection-unity-games?playlist=44069)

<span data-ttu-id="0b41e-307">導致過多記憶體回收行程最常見的做法之一，是不會快取 Unity 開發中元件和類別的參考。</span><span class="sxs-lookup"><span data-stu-id="0b41e-307">One of the most common practices that leads to excessive garbage collection isn't caching references to components and classes in Unity development.</span></span> <span data-ttu-id="0b41e-308">任何參考都應該在 Start() 或 Awake() 期間加以擷取，然後在 Update() 或 LateUpdate() 等函式中重複使用。</span><span class="sxs-lookup"><span data-stu-id="0b41e-308">Any references should be captured during Start() or Awake() and reused in later functions such as Update() or LateUpdate().</span></span>

<span data-ttu-id="0b41e-309">其他快速提示：</span><span class="sxs-lookup"><span data-stu-id="0b41e-309">Other quick tips:</span></span>
- <span data-ttu-id="0b41e-310">使用 [StringBuilder](/dotnet/api/system.text.stringbuilder) C# 類別，在執行時間以動態方式建置複雜字串</span><span class="sxs-lookup"><span data-stu-id="0b41e-310">Use the [StringBuilder](/dotnet/api/system.text.stringbuilder) C# class to dynamically build complex strings at runtime</span></span>
- <span data-ttu-id="0b41e-311">當您不再需要 Debug.Log() 的呼叫時，請加以移除，因為該函式仍會在應用程式的所有組建版本中執行</span><span class="sxs-lookup"><span data-stu-id="0b41e-311">Remove calls to Debug.Log() when no longer needed, as they still execute in all build versions of an app</span></span>
- <span data-ttu-id="0b41e-312">如果您的全像攝影應用程式通常需要大量的記憶體，請考慮在載入階段 (例如，呈現載入或轉換畫面時) 呼叫 [_**System.GC.Collect()**_](/dotnet/api/system.gc.collect)</span><span class="sxs-lookup"><span data-stu-id="0b41e-312">If your holographic app generally requires lots of memory, consider calling  [_**System.GC.Collect()**_](/dotnet/api/system.gc.collect) during loading phases such as when presenting a loading or transition screen</span></span>

#### <a name="object-pooling"></a><span data-ttu-id="0b41e-313">物件集區</span><span class="sxs-lookup"><span data-stu-id="0b41e-313">Object pooling</span></span>

<span data-ttu-id="0b41e-314">物件集區是一項熱門技術，可降低配置和取消配置連續物件時所耗用的成本。</span><span class="sxs-lookup"><span data-stu-id="0b41e-314">Object pooling is a popular technique for reducing the cost of continuous object allocation and deallocations.</span></span> <span data-ttu-id="0b41e-315">這是藉由配置相同物件的大型集區，並重複使用此集區中非使用中的可用實例來完成，而不是在一段時間內不斷產生和終結物件。</span><span class="sxs-lookup"><span data-stu-id="0b41e-315">This is done by allocating a large pool of identical objects and reusing inactive, available instances from this pool instead of constantly spawning and destroying objects over time.</span></span> <span data-ttu-id="0b41e-316">物件集區非常適合在應用程式期間有變數存留期的重複使用元件。</span><span class="sxs-lookup"><span data-stu-id="0b41e-316">Object pools are great for reuseable components that have variable lifetime during an app.</span></span>

- [<span data-ttu-id="0b41e-317">Unity 中的物件集區教學課程</span><span class="sxs-lookup"><span data-stu-id="0b41e-317">Object Pooling Tutorial in Unity</span></span>](https://unity3d.com/learn/tutorials/topics/scripting/object-pooling) 

## <a name="startup-performance"></a><span data-ttu-id="0b41e-318">啟動效能</span><span class="sxs-lookup"><span data-stu-id="0b41e-318">Startup performance</span></span>

<span data-ttu-id="0b41e-319">請考慮使用較小的場景來啟動您的應用程式，然後使用 *[SceneManager.LoadSceneAsync](https://docs.unity3d.com/ScriptReference/SceneManagement.SceneManager.LoadSceneAsync.html)* 載入場景的其餘部分。</span><span class="sxs-lookup"><span data-stu-id="0b41e-319">Consider starting your app with a smaller scene, then using *[SceneManager.LoadSceneAsync](https://docs.unity3d.com/ScriptReference/SceneManagement.SceneManager.LoadSceneAsync.html)* to load the rest of the scene.</span></span> <span data-ttu-id="0b41e-320">這可讓您的應用程式盡可能快速地進入互動狀態。</span><span class="sxs-lookup"><span data-stu-id="0b41e-320">This allows your app to get to an interactive state as fast as possible.</span></span> <span data-ttu-id="0b41e-321">當新的場景啟動時，可能會有大型的 CPU 尖峰，而且任何轉譯的內容可能會斷斷續續或是停頓。</span><span class="sxs-lookup"><span data-stu-id="0b41e-321">There may be a large CPU spike while the new scene is being activated and that any rendered content might stutter or hitch.</span></span> <span data-ttu-id="0b41e-322">解決這個情況的方法之一，就是在要載入的場景上，將 AsyncOperation.allowSceneActivation 屬性設為 "false"，等待場景載入，將畫面清除為黑色，然後將其設回 "true"，以完成場景啟用。</span><span class="sxs-lookup"><span data-stu-id="0b41e-322">One way to work around this is to set the AsyncOperation.allowSceneActivation property to "false" on the scene being loaded, wait for the scene to load, clear the screen too black, and then set it back to "true" to complete the scene activation.</span></span>

<span data-ttu-id="0b41e-323">請記住，當啟動場景在載入時，會向使用者顯示全像攝影畫面。</span><span class="sxs-lookup"><span data-stu-id="0b41e-323">Remember that while the startup scene is loading, the holographic splash screen will be displayed to the user.</span></span>

## <a name="see-also"></a><span data-ttu-id="0b41e-324">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0b41e-324">See also</span></span>
- [<span data-ttu-id="0b41e-325">將 Unity 遊戲中的圖形轉譯進行最佳化</span><span class="sxs-lookup"><span data-stu-id="0b41e-325">Optimizing graphics rendering in Unity games</span></span>](https://unity3d.com/learn/tutorials/temas/performance-optimization/optimizing-graphics-rendering-unity-games?playlist=44069)
- [<span data-ttu-id="0b41e-326">將 Unity 遊戲中的記憶體回收行程進行最佳化</span><span class="sxs-lookup"><span data-stu-id="0b41e-326">Optimizing garbage collection in Unity games</span></span>](https://unity3d.com/learn/tutorials/topics/performance-optimization/optimizing-garbage-collection-unity-games?playlist=44069)
- <span data-ttu-id="0b41e-327">[物理特性最佳做法 [Unity]](https://unity3d.com/learn/tutorials/topics/physics/physics-best-practices)</span><span class="sxs-lookup"><span data-stu-id="0b41e-327">[Physics Best Practices [Unity]](https://unity3d.com/learn/tutorials/topics/physics/physics-best-practices)</span></span>
- <span data-ttu-id="0b41e-328">[將指令碼進行最佳化 [Unity]](https://docs.unity3d.com/Manual/MobileOptimizationPracticalScriptingOptimizations.html)</span><span class="sxs-lookup"><span data-stu-id="0b41e-328">[Optimizing Scripts [Unity]](https://docs.unity3d.com/Manual/MobileOptimizationPracticalScriptingOptimizations.html)</span></span>