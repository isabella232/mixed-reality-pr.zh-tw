---
title: Unity 中的 HP 回音 G2 控制器
description: 使用 SteamVR 和 Windows Mixed Reality 中的 HP 回音 G2 控制器的指示。
author: hferrone
ms.author: v-hferrone
ms.date: 10/14/2020
ms.topic: article
keywords: Unity、回音、回音、HP 回音、mixed reality、開發、移動控制器、使用者輸入、功能、新專案、模擬器、檔、指南、功能、全像遊戲開發
ms.openlocfilehash: 17f373a3d94740bf103821b85ee5d6fe4dbaa11f
ms.sourcegitcommit: 8b16945d6a551f174a65fa3980ba392682ca45d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/28/2020
ms.locfileid: "92886251"
---
# <a name="hp-reverb-g2-controllers-in-unity"></a><span data-ttu-id="96c0b-104">Unity 中的 HP 回音 G2 控制器</span><span class="sxs-lookup"><span data-stu-id="96c0b-104">HP Reverb G2 Controllers in Unity</span></span>

<span data-ttu-id="96c0b-105">HP 運動控制器是一種全新的 Windows Mixed Reality 控制器類型：所有相同的追蹤技術都有一組稍微不同的可用輸入：</span><span class="sxs-lookup"><span data-stu-id="96c0b-105">HP Motion controllers are a brand new type of Windows Mixed Reality controllers: all the same tracking technology with a slightly different set of available inputs:</span></span> 

* <span data-ttu-id="96c0b-106">觸控板已由兩個按鈕取代：適用于右邊控制器的 A 和 B，以及左邊控制器的 X 和 Y。</span><span class="sxs-lookup"><span data-stu-id="96c0b-106">Touchpad has been replaced by two buttons: A and B for the right controller, and X and Y for the left controller.</span></span> 
* <span data-ttu-id="96c0b-107">我們現在已有一個觸發程式，此觸發程式會在0.0 和1.0 之間發行值的資料流程，而不是在按下和未按下狀態的按鈕。</span><span class="sxs-lookup"><span data-stu-id="96c0b-107">Grasp is now a trigger that publishes a stream of values between 0.0 and 1.0 instead of a button with Pressed and Not Pressed states.</span></span> 

<span data-ttu-id="96c0b-108">由於新的輸入無法透過現有的 Windows 和 Unity Api 來存取，因此您需要專用的 **MixedReality。輸入** UPM 套件。</span><span class="sxs-lookup"><span data-stu-id="96c0b-108">Since the new inputs aren't accessible through existing Windows and Unity APIs, you need the dedicated **Microsoft.MixedReality.Input** UPM Package.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="96c0b-109">**此套件中的類別不會取代現有的 Windows 和 Unity Api，但會加以補充。**</span><span class="sxs-lookup"><span data-stu-id="96c0b-109">**Classes in this package do not replace existing Windows and Unity APIs but complement them.**</span></span> <span data-ttu-id="96c0b-110">傳統 Windows Mixed Reality 控制器和 HP 運動控制器通常都可以使用的功能，可透過使用現有 Api 的相同程式碼路徑來存取。</span><span class="sxs-lookup"><span data-stu-id="96c0b-110">Features commonly available to both classic Windows Mixed Reality controllers and HP Motion Controllers are accessible through the same code path using existing APIs.</span></span> <span data-ttu-id="96c0b-111">只有新的輸入需要使用額外的 MixedReality 輸入套件。</span><span class="sxs-lookup"><span data-stu-id="96c0b-111">Only the new inputs require the use of the additional Microsoft.MixedReality.Input package.</span></span> 

## <a name="hp-motion-controller-overview"></a><span data-ttu-id="96c0b-112">HP 運動控制器總覽</span><span class="sxs-lookup"><span data-stu-id="96c0b-112">HP Motion Controller overview</span></span>

<span data-ttu-id="96c0b-113">*MixedReality。 MotionController* 代表移動控制器。</span><span class="sxs-lookup"><span data-stu-id="96c0b-113">*Microsoft.MixedReality.Input.MotionController* represents a motion controller.</span></span> <span data-ttu-id="96c0b-114">每個 *MotionController* 實例都有 *XR。Wsa。InteractionSource* 對等互連，可使用 handedness、廠商識別碼、產品識別碼和版本相互關聯。</span><span class="sxs-lookup"><span data-stu-id="96c0b-114">Each *MotionController* instance has an *XR.WSA.Input.InteractionSource* peer, which can be correlated using handedness, vendor ID, product ID, and version.</span></span> 

<span data-ttu-id="96c0b-115">您可以建立 *MotionControllerWatcher* 並訂閱其事件，以抓取 MotionController 實例，類似于使用 *InteractionManager* 事件來探索新的 *InteractionSource* 實例。</span><span class="sxs-lookup"><span data-stu-id="96c0b-115">You can grab MotionController instances by creating a *MotionControllerWatcher* and subscribing to its events, similar to using *InteractionManager* events to discover new *InteractionSource* instances.</span></span> <span data-ttu-id="96c0b-116">MotionController 的方法和屬性會描述控制器所支援的輸入，包括其按鈕、觸發程式、2D 軸和操縱杆。</span><span class="sxs-lookup"><span data-stu-id="96c0b-116">The MotionController’s methods and properties describe the inputs supported by the controller, including its buttons, triggers, 2D axis, and thumbstick.</span></span> <span data-ttu-id="96c0b-117">MotionController 類別也會公開透過 *MotionControllerReading* 類別存取輸入狀態的方法。</span><span class="sxs-lookup"><span data-stu-id="96c0b-117">The MotionController class also exposes methods for accessing input states through the *MotionControllerReading* class.</span></span> <span data-ttu-id="96c0b-118">MotionControllerReading 類別代表在給定時間的控制器狀態快照。</span><span class="sxs-lookup"><span data-stu-id="96c0b-118">The MotionControllerReading class represents a snapshot of the controller’s state at a given time.</span></span> 

## <a name="installing-microsoftmixedrealityinput-using-the-unity-package-manager"></a><span data-ttu-id="96c0b-119">使用 Unity 封裝管理員安裝 MixedReality</span><span class="sxs-lookup"><span data-stu-id="96c0b-119">Installing Microsoft.MixedReality.Input using the Unity Package Manager</span></span> 

<span data-ttu-id="96c0b-120">Unity 封裝管理員在) 上 ( # B0 使用 [資訊清單](https://docs.unity3d.com/Manual/upm-manifestPkg.html) 檔案來判斷要安裝的套件，以及可從中安裝的登錄 (伺服器) 。</span><span class="sxs-lookup"><span data-stu-id="96c0b-120">The Unity Package Manager uses a [manifest file](https://docs.unity3d.com/Manual/upm-manifestPkg.html) (manifest.json) to determine which packages to install and the registries (servers) they can be installed from.</span></span> <span data-ttu-id="96c0b-121">在您可以使用 MixedReality 輸入套件之前，您必須先註冊混合現實元件伺服器。</span><span class="sxs-lookup"><span data-stu-id="96c0b-121">Before you can use the Microsoft.MixedReality.Input package, you'll need to register the Mixed Reality component server.</span></span>

### <a name="registering-the-mixed-reality-component-server"></a><span data-ttu-id="96c0b-122">註冊混合現實元件伺服器</span><span class="sxs-lookup"><span data-stu-id="96c0b-122">Registering the Mixed Reality component server</span></span> 

<span data-ttu-id="96c0b-123">針對將使用 Mixed Reality 輸入套件的每個專案，[封裝] 資料夾中的 [檔案 (上的 manifest.js，) 需要新增混合的實際範圍登錄。</span><span class="sxs-lookup"><span data-stu-id="96c0b-123">For each project that will be using the Mixed Reality Input package, the manifest.json file (in the Packages folder) needs the Mixed Reality scoped registry added.</span></span> <span data-ttu-id="96c0b-124">若要適當地修改 manifest.js，以支援混合現實：</span><span class="sxs-lookup"><span data-stu-id="96c0b-124">To properly modify manifest.json to support Mixed Reality:</span></span> 
    1. <span data-ttu-id="96c0b-125"><projectRoot>在文字編輯器中開啟/Packages/manifest.js，例如 Visual Studio Code。</span><span class="sxs-lookup"><span data-stu-id="96c0b-125">Open <projectRoot>/Packages/manifest.json in a text editor, such as Visual Studio Code.</span></span> 
    2. <span data-ttu-id="96c0b-126">在資訊清單檔案的頂端，將 Mixed Reality 伺服器新增至範圍登錄區段，並儲存檔案。</span><span class="sxs-lookup"><span data-stu-id="96c0b-126">At the top of the manifest file, add the Mixed Reality server to the scoped registry section and save the file.</span></span> 
    
<pre>
{ 
  "scopedRegistries": [ 
    { 
      "name": "Microsoft Mixed Reality", 
      "url": "https://pkgs.dev.azure.com/aipmr/MixedReality-Unity-Packages/_packaging/Unity-packages/npm/registry/", 
      "scopes": [ 
        "com.microsoft.mixedreality" 
      ] 
    } 
  ], 
</pre>

### <a name="adding-the-microsoftmixedrealityinput-package"></a><span data-ttu-id="96c0b-127">新增 MixedReality 輸入套件</span><span class="sxs-lookup"><span data-stu-id="96c0b-127">Adding the Microsoft.MixedReality.Input package</span></span> 

<span data-ttu-id="96c0b-128">在文字編輯器中，修改/Packages/manifest.json 檔案的 [相依性] 區段， <projectRoot> 以新增 mixedreality，然後儲存檔案。</span><span class="sxs-lookup"><span data-stu-id="96c0b-128">Modify the dependencies section of the <projectRoot>/Packages/manifest.json file in the text editor to add com.microsoft.mixedreality.input package and save the file.</span></span> 

<pre>
  "dependencies": { 
    "com.microsoft.mixedreality.input": "0.9.2006", 
  }
</pre>

## <a name="using-microsoftmixedrealityinput"></a><span data-ttu-id="96c0b-129">使用 MixedReality. 輸入</span><span class="sxs-lookup"><span data-stu-id="96c0b-129">Using Microsoft.MixedReality.Input</span></span> 

### <a name="input-values"></a><span data-ttu-id="96c0b-130">輸入值</span><span class="sxs-lookup"><span data-stu-id="96c0b-130">Input values</span></span>

<span data-ttu-id="96c0b-131">MotionController 可以公開兩種類型的輸入：</span><span class="sxs-lookup"><span data-stu-id="96c0b-131">A MotionController can expose two kinds of inputs:</span></span> 

* <span data-ttu-id="96c0b-132">按鈕和觸發程式狀態是以介於0.0 到1.0 之間的唯一浮點值來表示，以表示按下的程度。</span><span class="sxs-lookup"><span data-stu-id="96c0b-132">Buttons and trigger states are expressed by a unique float value between 0.0 and 1.0 that indicates how much they're pressed.</span></span>
    * <span data-ttu-id="96c0b-133">當您按下) 時，按鈕只能傳回 0.0 () 或 1.0 (，而觸發程式可能會傳回 () 完整發行 (至 1.0) 完全按的連續0.0 值。</span><span class="sxs-lookup"><span data-stu-id="96c0b-133">A button can only return 0.0 (when not pressed) or 1.0 (when pressed) while a trigger can return continuous values between 0.0 (fully released) to 1.0 (fully pressed).</span></span> 
* <span data-ttu-id="96c0b-134">操縱杆狀態是由其 X 和 Y 元件介於-1.0 和1.0 之間的 Vector2 來表示。</span><span class="sxs-lookup"><span data-stu-id="96c0b-134">Thumbstick state is expressed by a Vector2 whose X and Y components are between -1.0 and 1.0.</span></span> 

<span data-ttu-id="96c0b-135">您可以使用 *MotionController. GetPressableInputs ( # B1* 傳回輸入值的清單， (按鈕和觸發程式傳回已按下的值) 或 *MotionController. GetXYInputs ( # B5* 方法，以傳回傳回2軸值的輸入清單。</span><span class="sxs-lookup"><span data-stu-id="96c0b-135">You can use *MotionController.GetPressableInputs()* to return a list of inputs returning a pressed value (buttons and triggers) or the *MotionController.GetXYInputs()* method to return a list of inputs returning a 2-axis value.</span></span> 

<span data-ttu-id="96c0b-136">MotionControllerReading 實例代表指定時間的控制器狀態：</span><span class="sxs-lookup"><span data-stu-id="96c0b-136">A MotionControllerReading instance represents the state of the controller at a given time:</span></span> 

* <span data-ttu-id="96c0b-137">*GetPressedValue ( # B1* 會抓取按鈕或觸發程式的狀態。</span><span class="sxs-lookup"><span data-stu-id="96c0b-137">*GetPressedValue()* retrieves the state of a button or a trigger.</span></span> 
* <span data-ttu-id="96c0b-138">*GetXYValue ( # B1* 會抓取操縱杆的狀態。</span><span class="sxs-lookup"><span data-stu-id="96c0b-138">*GetXYValue()* retrieves the state of a thumbstick.</span></span> 

### <a name="creating-a-cache-to-maintain-a-collection-of-motioncontroller-instances-and-their-states"></a><span data-ttu-id="96c0b-139">建立快取以維護 MotionController 實例及其狀態的集合</span><span class="sxs-lookup"><span data-stu-id="96c0b-139">Creating a cache to maintain a collection of MotionController instances and their states</span></span> 

<span data-ttu-id="96c0b-140">首先，具現化 MotionControllerWatcher 並註冊其 *MotionControllerAdded* 和 *MotionControllerRemoved* 事件的處理常式，以保留可用 MotionController 實例的快取。</span><span class="sxs-lookup"><span data-stu-id="96c0b-140">Start by instantiating a MotionControllerWatcher and registering handlers for its *MotionControllerAdded* and *MotionControllerRemoved* events to keep a cache of available MotionController instances.</span></span> <span data-ttu-id="96c0b-141">此快取應該是附加至 GameObject 的 MonoBehavior，如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="96c0b-141">This cache should be a MonoBehavior attached to a GameObject as demonstrated in the following code:</span></span>

```csharp
public class MotionControllerStateCache : MonoBehaviour 
{ 
    /// <summary> 
    /// Internal helper class which associates a Motion Controller 
    /// and its known state 
    /// </summary> 
    private class MotionControllerState 
    { 
        /// <summary> 
        /// Construction 
        /// </summary> 
        /// <param name="mc">motion controller</param>` 
        public MotionControllerState(MotionController mc) 
        { 
            this.MotionController = mc; 
        } 

        /// <summary> 
        /// Motion Controller that the state represents 
        /// </summary> 
        public MotionController MotionController { get; private set; } 
        … 
    } 

    private MotionControllerWatcher _watcher; 
    private Dictionary<Handedness, MotionControllerState> 
        _controllers = new Dictionary<Handedness, MotionControllerState>(); 

    /// <summary> 
    /// Starts monitoring controller's connections and disconnections 
    /// </summary> 
    public void Start() 
    { 
        _watcher = new MotionControllerWatcher(); 
        _watcher.MotionControllerAdded += _watcher_MotionControllerAdded; 
        _watcher.MotionControllerRemoved += _watcher_MotionControllerRemoved; 
        var nowait = _watcher.StartAsync(); 
    } 

    /// <summary> 
    /// Stops monitoring controller's connections and disconnections 
    /// </summary> 
    public void Stop() 
    { 
        if (_watcher != null) 
        { 
            _watcher.MotionControllerAdded -= _watcher_MotionControllerAdded; 
            _watcher.MotionControllerRemoved -= _watcher_MotionControllerRemoved; 
            _watcher.Stop(); 
        } 
    }

    /// <summary> 
    /// called when a motion controller has been removed from the system: 
    /// Remove a motion controller from the cache 
    /// </summary> 
    /// <param name="sender">motion controller watcher</param> 
    /// <param name="e">motion controller </param> 
    private void _watcher_MotionControllerRemoved(object sender, MotionController e) 
    { 
        lock (_controllers) 
        { 
            _controllers.Remove(e.Handedness); 
        } 
    }

    /// <summary> 
    /// called when a motion controller has been added to the system: 
    /// Remove a motion controller from the cache 
    /// </summary> 
    /// <param name="sender">motion controller watcher</param> 
    /// <param name="e">motion controller </param> 
    private void _watcher_MotionControllerAdded(object sender, MotionController e) 
    { 
        lock (_controllers) 
        { 
            _controllers[e.Handedness] = new MotionControllerState(e); 
        } 
    } 
} 
```

### <a name="reading-new-inputs-by-polling"></a><span data-ttu-id="96c0b-142">藉由輪詢讀取新的輸入</span><span class="sxs-lookup"><span data-stu-id="96c0b-142">Reading new inputs by polling</span></span> 

<span data-ttu-id="96c0b-143">您可以在 MonoBehavior 類別的 *Update* 方法期間，透過 *MotionController TryGetReadingAtTime* 每個已知控制器的目前狀態。</span><span class="sxs-lookup"><span data-stu-id="96c0b-143">You can read the current state of each known controller through *MotionController.TryGetReadingAtTime* during the *Update* method of the MonoBehavior class.</span></span> <span data-ttu-id="96c0b-144">您想要傳遞 *DateTime。現在* 為 timestamp 參數，以確保會讀取控制器的最新狀態。</span><span class="sxs-lookup"><span data-stu-id="96c0b-144">You want to pass *DateTime.Now* as the timestamp parameter to ensure that the latest state of the controller is read.</span></span> 

```csharp
public class MotionControllerStateCache : MonoBehaviour 
{ 
    … 

    private class MotionControllerState 
    {
        … 

        /// <summary> 
        /// Update the current state of the motion controller 
        /// </summary> 
        /// <param name="when">time of the reading</param> 
        public void Update(DateTime when) 
        { 
            this.CurrentReading = this.MotionController.TryGetReadingAtTime(when); 
        } 

        /// <summary> 
        /// Last reading from the controller 
        /// </summary> 
        public MotionControllerReading CurrentReading { get; private set; } 
    } 

    /// <summary> 
    /// Updates the input states of the known motion controllers 
    /// </summary> 
    public void Update() 
    { 
        var now = DateTime.Now; 

        lock (_controllers) 
        { 
            foreach (var controller in _controllers) 
            { 
                controller.Value.Update(now); 
            } 
        } 
    } 
} 
```

<span data-ttu-id="96c0b-145">您可以使用控制器的 Handedness 抓取控制器目前的輸入值：</span><span class="sxs-lookup"><span data-stu-id="96c0b-145">You can grab the controllers current input value using the Handedness of the controller:</span></span> 

```csharp
public class MotionControllerStateCache : MonoBehaviour 
{ 
    … 
    /// <summary> 
    /// Returns the current value of a controller input such as button or trigger 
    /// </summary> 
    /// <param name="handedness">Handedness of the controller</param> 
    /// <param name="input">Button or Trigger to query</param> 
    /// <returns>float value between 0.0 (not pressed) and 1.0 
    /// (fully pressed)</returns> 
    public float GetValue(Handedness handedness, ControllerInput input) 
    { 
        MotionControllerReading currentReading = null; 

        lock (_controllers) 
        { 
            if (_controllers.TryGetValue(handedness, out MotionControllerState mc)) 
            { 
                currentReading = mc.CurrentReading; 
            } 
        } 

        return (currentReading == null) ? 0.0f : currentReading.GetPressedValue(input); 
    } 

    /// <summary> 
    /// Returns the current value of a controller input such as button or trigger 
    /// </summary> 
    /// <param name="handedness">Handedness of the controller</param> 
    /// <param name="input">Button or Trigger to query</param> 
    /// <returns>float value between 0.0 (not pressed) and 1.0 
    /// (fully pressed)</returns> 
    public float GetValue(UnityEngine.XR.WSA.Input.InteractionSourceHandedness handedness, ControllerInput input) 
    { 
        return GetValue(Convert(handedness), input); 
    } 

    /// <summary> 
    /// Returns a boolean indicating whether a controller input such as button or trigger is pressed 
    /// </summary> 
    /// <param name="handedness">Handedness of the controller</param> 
    /// <param name="input">Button or Trigger to query</param> 
    /// <returns>true if pressed, false if not pressed</returns> 
    public bool IsPressed(Handedness handedness, ControllerInput input) 
    { 
        return GetValue(handedness, input) >= PressedThreshold; 
    } 
} 
```

<span data-ttu-id="96c0b-146">例如，若要讀取 InteractionSource 的類比理解值：</span><span class="sxs-lookup"><span data-stu-id="96c0b-146">For example, to read the analog grasp value of an InteractionSource:</span></span> 

```csharp
/// Read the analog grasp value of all connected interaction sources 
void Update() 
{ 
    … 
    var stateCache = gameObject.GetComponent<MotionControllerStateCache>(); 
    foreach (var sourceState in InteractionManager.GetCurrentReading()) 
    { 
        float graspValue = stateCache.GetValue(sourceState.source.handedness, 
            Microsoft.MixedReality.Input.ControllerInput.Grasp);
        … 
    }
} 
```

### <a name="generating-events-from-the-new-inputs"></a><span data-ttu-id="96c0b-147">從新的輸入產生事件</span><span class="sxs-lookup"><span data-stu-id="96c0b-147">Generating events from the new inputs</span></span> 

<span data-ttu-id="96c0b-148">您可以選擇將所有狀態變更作為事件來處理，而不是輪詢控制器的狀態一次，讓您可以處理最快速的動作，使其維持小於框架。</span><span class="sxs-lookup"><span data-stu-id="96c0b-148">Instead of polling for a controller's state once per frame, you have the option of handling all state changes as events, which lets you handle even the quickest actions lasting less than a frame.</span></span> <span data-ttu-id="96c0b-149">為了讓這個方法能夠運作，行動電話控制器的快取需要處理自最後一個畫面格之後由控制器所發行的所有狀態，您可以將最後一次 MotionControllerReading 的時間戳記儲存在 MotionController 中，然後呼叫 *MotionController. TryGetReadingAfterTime ( # B1* ：</span><span class="sxs-lookup"><span data-stu-id="96c0b-149">In order for this approach to work, the cache of motion controllers needs to process all states published by a controller since the last frame, which you can do by storing the timestamp of the last MotionControllerReading retrieved from a MotionController and calling *MotionController.TryGetReadingAfterTime()* :</span></span> 

```csharp
private class MotionControllerState 
{ 
    … 
    /// <summary> 
    /// Returns an array representng buttons which are pressed 
    /// </summary> 
    /// <param name="reading">motion controller reading</param> 
    /// <returns>array of booleans</returns> 
    private bool[] GetPressed(MotionControllerReading reading) 
    { 
        if (reading == null) 
        { 
            return null; 
        } 
        else 
        { 
            bool[] ret = new bool[this.pressableInputs.Length]; 
            for (int i = 0; i < pressableInputs.Length; ++i) 
            { 
                ret[i] = reading.GetPressedValue(pressableInputs[i]) >= PressedThreshold; 
            } 

            return ret; 
        } 
    } 

    /// <summary> 
    /// Get the next available state of the motion controller 
    /// </summary> 
    /// <param name="lastReading">previous reading</param> 
    /// <param name="newReading">new reading</param> 
    /// <returns>true is a new reading was available</returns> 
    private bool GetNextReading(MotionControllerReading lastReading, out MotionControllerReading newReading) 
    { 
        if (lastReading == null) 
        { 
            // Get the first state published by the controller 
            newReading = this.MotionController.TryGetReadingAfterSystemRelativeTime(TimeSpan.FromSeconds(0.0)); 
        } 
        else 
        { 
            // Get the next state published by the controller 
            newReading = this.MotionController.TryGetReadingAfterTime(lastReading.InputTime); 
        } 

        return newReading != null; 
    } 

    /// <summary> 
    /// Processes all the new states published by the controller since the last call 
    /// </summary> 
    public IEnumerable<MotionControllerEventArgs> GetNextEvents() 
    {
        MotionControllerReading lastReading = this.CurrentReading; 
        bool[] lastPressed = GetPressed(lastReading); 
        MotionControllerReading newReading; 
        bool[] newPressed; 

        while (GetNextReading(lastReading, out newReading)) 
        { 
            newPressed = GetPressed(newReading); 

            // If we have two readings, compare and generate events 
            if (lastPressed != null) 
            { 
                for (int i = 0; i < pressableInputs.Length; ++i) 
                { 
                    if (newPressed[i] != lastPressed[i]) 
                    { 
                        yield return new MotionControllerEventArgs(this.MotionController.Handedness, newPressed[i], this.pressableInputs[i], newReading.InputTime); 
                    } 
                } 
            } 

            lastPressed = newPressed; 
            lastReading = newReading; 
        } 

        // No more reading 
        this.CurrentReading = lastReading; 
    } 
} 
```

<span data-ttu-id="96c0b-150">現在您已更新快取內部類別，MonoBehavior 類別可以公開兩個事件–已按下並釋出，並從其更新 ( # A1 方法中引發它們：</span><span class="sxs-lookup"><span data-stu-id="96c0b-150">Now that you've updated the cache internal classes, the MonoBehavior class can expose two events – Pressed and Released – and raise them from its Update() method:</span></span> 

```csharp
/// <summary> 
/// Event argument class for InputPressed and InputReleased events 
/// </summary> 
public class MotionControllerEventArgs : EventArgs 
{ 
    public MotionControllerEventArgs(Handedness handedness, bool isPressed, rollerInput input, DateTime inputTime) 
    { 
        this.Handedness = handedness; 
        this.Input = input; 
        this.InputTime = inputTime; 
        this.IsPressed = isPressed; 
    } 

    /// <summary> 
    /// Handedness of the controller raising the event 
    /// </summary> 
    public Handedness Handedness { get; private set; } 

    /// <summary> 
    /// Button pressed or released 
    /// </summary> 
    public ControllerInput Input { get; private set; } 

    /// <summary> 
    /// Time of the event 
    /// </summary> 
    public DateTime InputTime { get; private set; } 

    /// <summary> 
    /// true if button is pressed, false otherwise 
    /// </summary> 
    public bool IsPressed { get; private set; } 
} 

/// <summary> 
/// Event raised when a button is pressed 
/// </summary> 
public event EventHandler<MotionControllerEventArgs> InputPressed; 

/// <summary> 
/// Event raised when a button is released 
/// </summary> 
public event EventHandler<MotionControllerEventArgs> InputReleased; 

/// <summary> 
/// Updates the input states of the known motion controllers 
/// </summary> 
public void Update() 
{ 
    // If some event handler has been registered, we need to process all states  
    // since the last update, to avoid missing a quick press / release 
    if ((InputPressed != null) || (InputReleased != null)) 
    { 
        List<MotionControllerEventArgs> events = new <MotionControllerEventArgs>(); 

        lock (_controllers) 
        { 
            foreach (var controller in _controllers) 
            { 
                events.AddRange(controller.Value.GetNextEvents()); 
            } 
        } 
 
        // Sort the events by time 
        events.Sort((e1, e2) => DateTime.Compare(e1.InputTime, e2.InputTime)); 

        foreach (MotionControllerEventArgs evt in events) 
        { 
            if (evt.IsPressed && (InputPressed != null)) 
            { 
                InputPressed(this, evt); 
            } 
            else if (!evt.IsPressed && (InputReleased != null)) 
            { 
                InputReleased(this, evt); 
            } 
        } 
    } 
    else 
    { 
        // As we do not predict button presses and the timestamp of the next e is in the future 
        // DateTime.Now is correct in this context as it will return the latest e of controllers 
        // which is the best we have at the moment for the frame. 
        var now = DateTime.Now; 
        lock (_controllers) 
        { 
            foreach (var controller in _controllers) 
            { 
                controller.Value.Update(now); 
            } 
        } 
    } 
} 
```

<span data-ttu-id="96c0b-151">上述程式碼範例中的結構讓註冊事件更容易閱讀：</span><span class="sxs-lookup"><span data-stu-id="96c0b-151">The structure in the above code examples makes registering events much more readable:</span></span> 

```csharp
public InteractionSourceHandedness handedness; 
public Microsoft.MixedReality.Input.ControllerInput redButton;

// Start of the Mono Behavior: register handlers for events from cache 
void Start() 
{ 
    var stateCache = gameObject.GetComponent<MotionControllerStateCache>(); 
    stateCache.InputPressed += stateCache_InputPressed; 
    stateCache.InputReleased += stateCache_InputReleased; 
    … 
} 

// Called when a button is released 
private void stateCache_InputReleased(object sender, MotionControllerStateCache.MotionControllerEventArgs e) 
{ 
    if ((e.SourceHandedness == handedness) && (e.Input == redButton)) 
    { 
        … 
    } 
} 

// Called when a button is pressed 
private void stateCache_InputPressed(object sender, MotionControllerStateCache.MotionControllerEventArgs e) 
{ 
    if ((e.SourceHandedness == handedness) && (e.Input == redButton)) 
    { 
        … 
    } 
} 
```

## <a name="see-also"></a><span data-ttu-id="96c0b-152">另請參閱</span><span class="sxs-lookup"><span data-stu-id="96c0b-152">See also</span></span>

<!-- ## Getting started

There's no additional setup required to use the HP Reverb G2 controller if you're developing for SteamVR or using the Windows Mixed Reality Input API (XR.WSA.Input). However, the A, B, X, Y buttons and the squeeze trigger are not currently accessible through the Input Manager unless you're using SteamVR. Support for the extra Reverb G2 inputs will be available in the near future, so be sure to check back!

## Porting existing applications

If you already have an existing app that you're developing for Windows Mixed Reality immersive headsets, check out our [porting guide](../porting-apps/porting-guides.md) and [project settings](https://docs.microsoft.com/windows/mixed-reality/develop/porting-apps/porting-guides?tabs=project#unity-porting-guidance) sections for general suggestions.

## Mapping input

When you're ready to get your input mapping up and running for your new controllers, start at the [input mapping](https://docs.microsoft.com/windows/mixed-reality/develop/porting-apps/porting-guides?tabs=input#unity-porting-guidance) section of the immersive porting guide. Instructions on how to configure inputs in Unity is detailed in [Gestures and motion controllers](gestures-and-motion-controllers-in-unity.md), along with a full [button and axis mapping table](gestures-and-motion-controllers-in-unity.md#using-hp-reverb-g2-controllers) for reference.

## See also
* [Updating for SteamVR](../porting-apps/updating-your-steamvr-application-for-windows-mixed-reality.md) -->