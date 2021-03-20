---
title: CodingGuidelines
description: 參與 MRTK 時要遵循的編碼準則和慣例。
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: 'Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、c #、'
ms.openlocfilehash: 59fac14bdcdb4c48950668d891426c0de2db37f7
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104688628"
---
# <a name="coding-guidelines"></a>程式碼撰寫指導方針

本檔概述參與 MRTK 時要遵循的程式碼撰寫準則和慣例。

---

## <a name="philosophy"></a>哲學

### <a name="be-concise-and-strive-for-simplicity"></a>簡潔且儘量簡化

最簡單的解決方案通常是最好的。 這是這些指導方針的覆寫目的，而且應該是所有程式碼撰寫活動的目標。 很簡單的部分很簡潔，而且與現有的程式碼一致。 試著讓您的程式碼保持簡潔。

讀者應該只會遇到提供有用資訊的構件。 例如，重新聲明明顯內容的批註不會提供額外的資訊，也不會增加信號比例的雜訊。

讓程式碼邏輯保持簡易。 請注意，這並不是有關使用最少行數、將識別碼名稱或大括弧樣式的大小降到最低的語句，而是關於減少概念的數目，並透過熟悉的模式將它們的可見度最大化。

### <a name="produce-consistent-readable-code"></a>產生一致且可讀取的程式碼

程式碼可讀性與低瑕疵率相關聯。 努力建立容易閱讀的程式碼。 努力建立具有簡單邏輯的程式碼，並重複使用現有的元件，因為它也會協助確保正確性。

您所產生之程式碼的所有詳細資料，從最基本的正確性詳細資料到一致的樣式和格式。 保持您的程式碼樣式與已存在的樣式一致，即使它不符合您的喜好設定。 這會增加整體程式碼基底的可讀性。

### <a name="support-configuring-components-both-in-editor-and-at-run-time"></a>支援在編輯器和執行時間設定元件

MRTK 支援一組不同的使用者，也就是想要在 Unity 編輯器和 load prefabs 中設定元件的人員，以及需要在執行時間具現化和設定物件的人員。

您所有的程式碼都應可透過將元件新增至儲存場景中的 GameObject，以及在程式碼中具現化該元件的方式運作。 測試應該包含用於具現化 prefabs 和具現化的測試案例，在執行時間設定元件。

### <a name="play-in-editor-is-your-first-and-primary-target-platform"></a>內建編輯器是您的第一個和主要目標平臺

「內建編輯器」是在 Unity 中反覆運算的最快方式。 提供客戶快速反復執行的方式，讓他們能夠更快速地開發解決方案，並嘗試更多構想。 換句話說，最大化反覆運算的速度可讓客戶達成更多目標。

讓所有專案都能在編輯器中運作，然後讓它在其他任何平臺上運作。 在編輯器中保持運作。 您可以輕鬆地將新平臺加入編輯器中。 如果您的應用程式只能在裝置上運作，則很難讓使用中的編輯器運作。

### <a name="add-new-public-fields-properties-methods-and-serialized-private-fields-with-care"></a>謹慎新增公用欄位、屬性、方法和序列化私用欄位

每次新增公用方法（field，property）時，它就會成為 MRTK 公用 API 介面的一部分。 標記為的私用欄位 `[SerializeField]` 也會將欄位公開給編輯器，而且是公用 API 介面的一部分。 其他人可能會使用該公用方法、使用您的公用欄位設定自訂 prefabs，並對其進行相依性。

應謹慎檢查新的公用成員。 未來將需要維護任何公用欄位。 請記住，如果公用欄位的類型 (或序列化私用欄位) 變更或從 MonoBehaviour 中移除，這可能會中斷其他人。 欄位必須先淘汰才能發行，而且需要提供程式碼來遷移已取得相依性之人員的變更。

### <a name="prioritize-writing-tests"></a>排定撰寫測試的優先順序

MRTK 是一個由各種不同參與者所修改的社區專案。 這些參與者可能不知道 bug 修正/功能的詳細資料，而且不小心中斷了您的功能。 MRTK 會在完成每個提取要求之前[執行持續整合測試](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_build?definitionId=16)。 無法簽入中斷測試的變更。 因此，測試是確保其他人不會中斷您的功能的最佳方式。

當您修正錯誤時，請撰寫測試，以確保它不會在未來回歸。 如果加入功能，請撰寫可驗證您的功能運作的測試。 這是實驗性功能以外所有 UX 功能的必要項。

## <a name="c-coding-conventions"></a>C # 編碼慣例

### <a name="script-license-information-headers"></a>腳本授權資訊標頭

所有參與新檔案的 Microsoft 員工都應該在任何新檔案的頂端新增下列標準授權標頭，完全如下所示：

```c#
// Copyright (c) Microsoft Corporation.
// Licensed under the MIT License.
```

### <a name="function--method-summary-headers"></a>函數/方法摘要標頭

張貼至 MRTK 的所有公用類別、結構、列舉、函式、屬性、欄位都應描述為其用途和使用，完全如下所示：

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

這可確保為所有類別、方法和屬性正確產生和簡易性檔。

任何未適當摘要標記提交的腳本檔案都會遭到拒絕。

### <a name="mrtk-namespace-rules"></a>MRTK 命名空間規則

「混合現實」工具組使用以功能為基礎的命名空間模型，其中所有基礎命名空間的開頭都是 "MixedReality"。 一般而言，您不需要在命名空間中指定工具組層 (例如： Core、Providers、Services) 。

目前定義的命名空間為：

- MixedReality 工具組
- MixedReality：界限
- MixedReality 工具組
- MixedReality 編輯工具
- MixedReality。輸入
- MixedReality 工具組. SpatialAwareness
- MixedReality. 傳送工具
- MixedReality 工具組

對於具有大量類型的命名空間，可接受建立有限數目的子命名空間，以協助範圍使用。

省略介面、類別或資料類型的命名空間，將會導致您的變更遭到封鎖。

### <a name="adding-new-monobehaviour-scripts"></a>加入新的 MonoBehaviour 腳本

使用提取要求新增 MonoBehaviour 腳本時，請確定 [`AddComponentMenu`](https://docs.unity3d.com/ScriptReference/AddComponentMenu.html) 屬性已套用至所有適用的檔案。 這可確保在編輯器的 [ *新增元件* ] 按鈕下，可輕鬆找到元件。 如果元件無法顯示在編輯器（例如抽象類別）中，則不需要屬性旗標。

在下列範例中，您應該使用元件的套件位置填入 *套件* 。 如果將專案放在 *MRTK/SDK* 資料夾中，則套件將會是 *SDK*。

```c#
[AddComponentMenu("Scripts/MRTK/{Package here}/MyNewComponent")]
public class MyNewComponent : MonoBehaviour
```

### <a name="adding-new-unity-inspector-scripts"></a>新增 Unity inspector 腳本

一般情況下，請嘗試避免建立 MRTK 元件的自訂偵測器腳本。 它增加了可由 Unity 引擎處理的程式碼基底額外負荷和管理。

如果需要偵測器類別，請嘗試使用 Unity [`DrawDefaultInspector()`](https://docs.unity3d.com/ScriptReference/Editor.DrawDefaultInspector.html) 。 這會再次簡化偵測器類別，並將大部分的工作保留在 Unity 中。

```c#
public override void OnInspectorGUI()
{
    // Do some custom calculations or checks
    // ....
    DrawDefaultInspector();
}
```

如果在偵測器類別中需要自訂轉譯，請嘗試利用 [`SerializedProperty`](https://docs.unity3d.com/ScriptReference/SerializedProperty.html) 和 [`EditorGUILayout.PropertyField`](https://docs.unity3d.com/ScriptReference/EditorGUILayout.PropertyField.html) 。 這可確保 Unity 正確處理轉譯的嵌套 prefabs 和修改的值。

如果 [`EditorGUILayout.PropertyField`](https://docs.unity3d.com/ScriptReference/EditorGUILayout.PropertyField.html) 因為自訂邏輯需求而無法使用，請確定所有使用方式均包裝在周圍 [`EditorGUI.PropertyScope`](https://docs.unity3d.com/ScriptReference/EditorGUI.PropertyScope.html) 。 這可確保 Unity 針對嵌套 prefabs 和已修改的值，以指定的屬性正確地呈現偵測器。

此外，請嘗試使用裝飾自訂偵測器類別 [`CanEditMultipleObjects`](https://docs.unity3d.com/ScriptReference/CanEditMultipleObjects.html) 。 此標記可確保場景中具有此元件的多個物件可以同時選取和修改。 任何新的偵測器類別都應該測試其程式碼是否適用于場景中的這種情況。

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

### <a name="adding-new-scriptableobjects"></a>正在加入新的 ScriptableObjects

新增 ScriptableObject 腳本時，請確定 [`CreateAssetMenu`](https://docs.unity3d.com/ScriptReference/CreateAssetMenu.html) 屬性已套用至所有適用的檔案。 這可確保在編輯器中透過資產建立功能表輕鬆地探索元件。 如果元件無法顯示在編輯器（例如抽象類別）中，則不需要屬性旗標。

在下列範例中， *子資料夾* 應填入 MRTK 子資料夾（如果適用）。 如果將專案放在 *MRTK/Providers* 資料夾中，則套件將會是 *提供者*。 如果將專案放在 *MRTK/Core* 資料夾中，請將它設定為「設定檔」。

在下列範例中， *MyNewService |MyNewProvider* 應該填入新的類別名稱（如果適用）。 如果將專案放在 *MixedRealityToolkit* 資料夾中，請將此字串退出。

```c#
[CreateAssetMenu(fileName = "MyNewProfile", menuName = "Mixed Reality Toolkit/{Subfolder}/{MyNewService | MyNewProvider}/MyNewProfile")]
public class MyNewProfile : ScriptableObject
```

### <a name="logging"></a>記錄

當您新增新功能或更新現有的功能時，請考慮將 DebugUtilities LogVerbose 記錄新增至有趣的程式碼，這可能會對未來的偵錯工具很有用。 在這種情況中，我們會在新增記錄和新增的雜訊之間進行取捨，而不是足夠的記錄 (這會導致診斷困難) 。

有一個有趣的範例，其中記錄可用於 (以及有趣的承載) ：

```c#
DebugUtilities.LogVerboseFormat("RaiseSourceDetected: Source ID: {0}, Source Type: {1}", source.SourceId, source.SourceType);
```

這種類型的記錄可協助攔截 [問題](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8016) ，這是因為偵測到不相符的來源和來源遺失事件所造成。

避免針對每個畫面格上所發生的資料和事件新增記錄，這些記錄應涵蓋由不同使用者輸入所驅動的「有趣」事件 (亦即，使用者的「按一下」，以及來自于記錄) 感興趣之變更和事件的集合。 「使用者仍保有手勢」的持續狀態不會太有趣，而且會造成記錄檔太嚴重。

請注意，根據預設，此詳細資訊記錄不會開啟 (必須在 [診斷系統設定](../features/diagnostics/ConfiguringDiagnostics.md#enable-verbose-logging) 中啟用) 

### <a name="spaces-vs-tabs"></a>空格 vs tab

參與此專案時，請務必使用4個空格，而不是索引標籤。

### <a name="spacing"></a>間距

請勿在方括弧和括弧之間新增額外的空格：

#### <a name="dont"></a>禁止事項

```c#
private Foo()
{
    int[ ] var = new int [ 9 ];
    Vector2 vector = new Vector2 ( 0f, 10f );
}

```

#### <a name="do"></a>可行事項

```c#
private Foo()
{
    int[] var = new int[9];
    Vector2 vector = new Vector2(0f, 10f);
}
```

### <a name="naming-conventions"></a>命名規範

一律用於 `PascalCase` 屬性。 使用 `camelCase` 于大部分的欄位，但 `PascalCase` 使用 `static readonly` 和 `const` 欄位除外。 唯一的例外是針對需要由序列化欄位的資料結構 `JsonUtility` 。

#### <a name="dont"></a>禁止事項

```c#
public string myProperty; // <- Starts with a lowercase letter
private string MyField; // <- Starts with an uppercase letter
```

#### <a name="do"></a>可行事項

```c#
public string MyProperty;
protected string MyProperty;
private static readonly string MyField;
private string myField;
```

### <a name="access-modifiers"></a>存取修飾詞

一律宣告所有欄位、屬性和方法的存取修飾詞。

- `private`除非您需要在衍生類別中覆寫，否則所有 UNITY API 方法都應該預設為。 在此情況下， `protected` 應該使用。

- 欄位應一律為 `private` ，具有 `public` 或 `protected` 屬性存取子。

- 盡可能使用[運算式主體的成員](https://github.com/dotnet/roslyn/wiki/New-Language-Features-in-C%23-6#expression-bodied-function-members)和[auto 屬性](https://github.com/dotnet/roslyn/wiki/New-Language-Features-in-C%23-6#auto-property-enhancements)

#### <a name="dont"></a>禁止事項

```c#
// protected field should be private
protected int myVariable = 0;

// property should have protected setter
public int MyVariable => myVariable;

// No public / private access modifiers
void Foo() { }
void Bar() { }
```

#### <a name="do"></a>可行事項

```c#
public int MyVariable { get; protected set; } = 0;

private void Foo() { }
public void Bar() { }
protected virtual void FooBar() { }
```

### <a name="use-braces"></a>使用大括弧

請一律在每個語句區塊之後使用大括弧，並將它們放在下一行。

#### <a name="dont"></a>禁止事項

```c#
private Foo()
{
    if (Bar==null) // <- missing braces surrounding if action
        DoThing();
    else
        DoTheOtherThing();
}
```

#### <a name="dont"></a>禁止事項

```c#
private Foo() { // <- Open bracket on same line
    if (Bar==null) DoThing(); <- if action on same line with no surrounding brackets
    else DoTheOtherThing();
}
```

#### <a name="do"></a>可行事項

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

### <a name="public-classes-structs-and-enums-should-all-go-in-their-own-files"></a>公用類別、結構和列舉應該全都放入自己的檔案

如果類別、結構或列舉可以設為私用，則可以將它包含在相同的檔案中。  這可避免與 Unity 相關的問題，並確保發生適當的程式碼抽象化，也可在程式碼需要變更時減少衝突和重大變更。

#### <a name="dont"></a>禁止事項

```c#
public class MyClass
{
    public struct MyStruct() { }
    public enum MyEnumType() { }
    public class MyNestedClass() { }
}
```

#### <a name="do"></a>可行事項

```c#
 // Private references for use inside the class only
public class MyClass
{
    private struct MyStruct() { }
    private enum MyEnumType() { }
    private class MyNestedClass() { }
}
```

#### <a name="do"></a>可行事項

Mystruct>) .cs

```c#
// Public Struct / Enum definitions for use in your class.  Try to make them generic for reuse.
public struct MyStruct
{
    public string Var1;
    public string Var2;
}
```

MyEnumType .cs

```c#
public enum MuEnumType
{
    Value1,
    Value2 // <- note, no "," on last value to denote end of list.
}
```

MyClass

```c#
public class MyClass
{
    private MyStruct myStructReference;
    private MyEnumType myEnumReference;
}
```

### <a name="initialize-enums"></a>初始化列舉

為了確保從0開始正確初始化所有列舉，.NET 會提供您整齊的快捷方式，藉由直接新增第一個 (入門) 值來自動初始化列舉。  (，例如值 1 = 0 不需要剩餘的值) 

#### <a name="dont"></a>禁止事項

```c#
public enum Value
{
    Value1, <- no initializer
    Value2,
    Value3
}
```

#### <a name="do"></a>可行事項

```c#
public enum ValueType
{
    Value1 = 0,
    Value2,
    Value3
}
```

### <a name="order-enums-for-appropriate-extension"></a>排序適當擴充的列舉

如果未來可能會延長列舉，以排序列舉頂端的預設值，這可確保列舉索引不會影響新的新增專案。

#### <a name="dont"></a>禁止事項

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

#### <a name="do"></a>可行事項

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

### <a name="review-enum-use-for-bitfields"></a>審核位欄位的列舉用途

如果列舉可能需要使用多個狀態作為值，例如 Handedness = Left & Right。 接著，必須使用位旗標正確裝飾列舉，才能讓它正確地使用

Handedness .cs 檔案有此的具體執行

### <a name="dont"></a>禁止事項

```c#
public enum Handedness
{
    None,
    Left,
    Right
}
```

### <a name="do"></a>可行事項

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

### <a name="hard-coded-file-paths"></a>硬式編碼的檔案路徑

產生字串檔案路徑時，特別是撰寫硬式編碼的字串路徑時，請執行下列動作：

1. 盡可能使用 c # 的[ `Path` api](https://docs.microsoft.com/dotnet/api/system.io.path?view=netframework-4.8&preserve-view=true) ，例如 `Path.Combine` 或 `Path.GetFullPath` 。
1. 使用/或 [`Path.DirectorySeparatorChar`](https://docs.microsoft.com/dotnet/api/system.io.path.directoryseparatorchar?view=netframework-4.8&preserve-view=true) ，而不是 \ 或 \\ \\ 。

這些步驟可確保 MRTK 可在 Windows 和 Unix 系統上運作。

### <a name="dont"></a>禁止事項

```c#
private const string FilePath = "MyPath\\to\\a\\file.txt";
private const string OtherFilePath = "MyPath\to\a\file.txt";

string filePath = myVarRootPath + myRelativePath;
```

### <a name="do"></a>可行事項

```c#
private const string FilePath = "MyPath/to/a/file.txt";
private const string OtherFilePath = "folder{Path.DirectorySeparatorChar}file.txt";

string filePath = Path.Combine(myVarRootPath,myRelativePath);

// Path.GetFullPath() will return the full length path of provided with correct system directory separators
string cleanedFilePath = Path.GetFullPath(unknownSourceFilePath);
```

## <a name="best-practices-including-unity-recommendations"></a>最佳做法，包括 Unity 建議

此專案的某些目標平臺需要將效能納入考慮。 如此一來，在嚴格的更新迴圈或演算法中配置經常稱為程式碼的記憶體時，一定要特別小心。

### <a name="encapsulation"></a>封裝

如果需要從類別或結構外部存取欄位，請一律使用私用欄位和公用屬性。  請務必共同找出私用欄位和公用屬性。 這可讓您更輕鬆地查看屬性的內容，以及腳本可修改欄位。

> [!NOTE]
> 唯一的例外是針對需要由序列化欄位的資料結構 `JsonUtility` ，其中資料類別需要有所有公用欄位，序列化才能運作。

#### <a name="dont"></a>禁止事項

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

#### <a name="do"></a>可行事項

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

### <a name="cache-values-and-serialize-them-in-the-sceneprefab-whenever-possible"></a>快取值，並盡可能在場景/預製專案中將它們序列化

在 HoloLens 的考慮下，最好是將場景或預製專案中的效能和快取參考優化，以限制執行時間記憶體配置。

#### <a name="dont"></a>禁止事項

```c#
void Update()
{
    gameObject.GetComponent<Renderer>().Foo(Bar);
}
```

#### <a name="do"></a>可行事項

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

### <a name="cache-references-to-materials-do-not-call-the-material-each-time"></a>資料的快取參考，請勿每次都呼叫 ". 材質"

Unity 將會在您每次使用「材質」時建立新的材質，如果未正確清除，將會造成記憶體流失。

#### <a name="dont"></a>禁止事項

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

#### <a name="do"></a>可行事項

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
> 或者，您也可以使用 Unity 的 "SharedMaterial" 屬性，此屬性不會在每次參考時建立新的內容。

### <a name="use-platform-dependent-compilation-to-ensure-the-toolkit-wont-break-the-build-on-another-platform"></a>使用 [平臺相依編譯](https://docs.unity3d.com/Manual/PlatformDependentCompilation.html) 來確保工具組不會在另一個平臺上中斷組建

- 使用 `WINDOWS_UWP` 以使用 UWP 特定的非 Unity api。 這會讓他們無法嘗試在編輯器或不支援的平臺上執行。 這相當於 `UNITY_WSA && !UNITY_EDITOR` ，而且應該改用。
- 使用 `UNITY_WSA` 以使用 UWP 特定的 Unity api，例如 `UnityEngine.XR.WSA` 命名空間。 當平臺設定為 UWP，以及在建立的 UWP 應用程式中時，這會在編輯器中執行。

此圖表可協助您決定要使用哪一種 `#if` ，取決於您的使用案例和您預期的組建設定。

|平台 | UWP IL2CPP | UWP .NET | 編輯器 |
| --- | --- | --- | --- |
| `UNITY_EDITOR` | False | False | True |
| `UNITY_WSA` | True | True | True |
| `WINDOWS_UWP` | True | True | False |
| `UNITY_WSA && !UNITY_EDITOR` | True | True | False |
| `ENABLE_WINMD_SUPPORT` | True | True | False |
| `NETFX_CORE` | False | True | 否 |

### <a name="prefer-datetimeutcnow-over-datetimenow"></a>偏好 UtcNow 超過 DateTime。現在

UtcNow 比 DateTime 更快。現在。 在先前的效能調查中，我們發現使用 DateTime。現在增加了很大的負擔，特別是在 Update () 迴圈中使用時。 [其他人遇到相同的問題](https://stackoverflow.com/questions/1561791/optimizing-alternatives-to-datetime-now)。

偏好使用 DateTime. UtcNow，除非您真的需要當地語系化的時間 (合理的原因可能是您想要在使用者時區) 中顯示目前的時間。 如果您正在處理相對時間 (也就是最後一個更新和現在) 之間的差異，最好使用 UtcNow 來避免執行時區轉換的額外負荷。

## <a name="powershell-coding-conventions"></a>PowerShell 編碼慣例

MRTK 程式碼基底的子集會使用 PowerShell 來進行管線基礎結構和各種腳本和公用程式。 新的 PowerShell 程式碼應該遵循 [PoshCode 樣式](https://poshcode.gitbooks.io/powershell-practice-and-style/)。

## <a name="see-also"></a>另請參閱

 [MSDN 的 c # 編碼慣例](https://docs.microsoft.com/dotnet/csharp/programming-guide/inside-a-program/coding-conventions)
