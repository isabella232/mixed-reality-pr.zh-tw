---
title: MR Input 213
description: 遵循此編碼教學課程，使用 Unity、Visual Studio 和沉浸式耳機來瞭解運動控制器的詳細資料。
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit、mixedrealitytoolkit、mixedrealitytoolkit-unity、沉浸式、移動控制器、學院、教學課程
ms.openlocfilehash: 1f747c73846f59fdc62a0559068123a50f8a1b07
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583054"
---
# <a name="mr-input-213-motion-controllers"></a>MR Input 213：運動控制器

>[!NOTE]
>混合實境學院教學課程的設計是以 HoloLens (第 1 代) 和混合實境沉浸式頭戴裝置為準。  因此，對於仍在尋找這些裝置開發指引的開發人員而言，我們覺得這些教學課程很重要。  這些教學課程 **_不會_** 使用用於 HoloLens 2 的最新工具組或互動進行更新。  系統會保留這些資訊，以繼續在支援的裝置上運作。 已針對 HoloLens 2 公佈[一系列新的教學課程](../develop/unity/tutorials/mr-learning-base-01.md)。

混合現實世界中的運動控制器會新增另一個層級的互動。 有了 [運動控制器](../design/motion-controllers.md)，我們就能以更自然的方式直接與物件互動，類似于真實生活中的實際互動，在您的應用程式體驗中增加深度和取悅。

在 MR 輸入213中，我們會藉由建立簡單的空間繪製體驗來探索移動控制器的輸入事件。 使用此應用程式，使用者可以使用各種類型的筆刷和色彩，在三維空間中進行繪製。

## <a name="topics-covered-in-this-tutorial"></a>本教學課程中涵蓋的主題

|![MixedReality213 Topic1](images/mr213-topic1.png)|![MixedReality213 Topic2](images/mr213-topic2.png)|![MixedReality213 Topic3](images/mr213-topic3.png)|
| :--- | :--- | :--- |
|**控制器視覺效果**|**控制器輸入事件**|**自訂控制器和 UI**|
|瞭解如何在 Unity 的遊戲模式和執行時間中呈現移動控制器模型。|瞭解不同類型的按鈕事件和其應用程式。|瞭解如何將 UI 元素重迭在控制器上，或完全自訂。|

## <a name="device-support"></a>裝置支援

<table>
<tr>
<th>課程</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../discover/immersive-headset-hardware-details.md">沉浸式頭戴裝置</a></th>
</tr><tr>
<td>MR Input 213：運動控制器</td><td style="text-align: center;"> </td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="before-you-start"></a>在您開始使用 Intune 之前

### <a name="prerequisites"></a>必要條件

請參閱 [此頁面](../develop/install-the-tools.md)上的沉浸式耳機安裝檢查清單。

* 本教學課程需要 [Unity 2017.2.1 p2](https://beta.unity3d.com/download/1dc514532f08/UnityDownloadAssistant-2017.2.1p2.exe)

### <a name="project-files"></a>專案檔

* [下載](https://github.com/Microsoft/MixedReality213/archive/master.zip) 專案所需的檔案，並將檔案解壓縮至桌面。

>[!NOTE]
>如果您想要在下載之前查看原始程式碼， [可在 GitHub 上](https://github.com/Microsoft/MixedReality213)取得。

## <a name="unity-setup"></a>Unity 設定

>[!VIDEO https://www.youtube.com/embed/cBAOALaHys4]

### <a name="objectives"></a>目標

* 針對 Windows Mixed Reality 開發優化 Unity
* 安裝混合實境相機
* 設定環境

### <a name="instructions"></a>指示

* 啟動 Unity。
* 選取 [開啟]  。
* 流覽至您的桌面，並尋找您先前 unarchived 的 **MixedReality213 主** 資料夾。
* 按一下 [選擇資料夾]。
* Unity 完成載入專案檔之後，您就能夠看到 Unity 編輯器。
* 在 Unity 中，選取 [ **File > Build Settings**]。

    ![MR213_BuildSettings](images/mr213-buildsettings-450px.png)

* 在 [**平臺**] 清單中選取 **通用 Windows 平臺**，然後按一下 [**切換平臺**] 按鈕。
* 將目標裝置設定為 **任何裝置**
* 將組建類型設定為 **D3D**
* 將 SDK 設定為 **最新安裝**
* 檢查 **Unity c # 專案**
    * 這可讓您修改 Visual Studio 專案中的指令檔，而不需要重建 Unity 專案。
* 按一下 [ **玩家設定**]。
* 在 [偵測 **器** ] 面板中，向下滾動至底部
* 在 [XR 設定] 中，檢查 **支援的虛擬實境**
* 在 [虛擬實境 Sdk] 下，選取 **Windows Mixed Reality**

    ![MR213_XRSettings](images/mr213-xrsettings-500px.png)

* 關閉 [ **組建設定** ] 視窗。

### <a name="project-structure"></a>專案結構

本教學課程使用 **[混合現實工具組-Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)**。 您可以在 [此頁面](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases)上找到這些版本。

![ProjectStructure](images/mr213-projectstructure-650px.png)

**針對您的參考完成的場景**

* 您會在 **幕後** 資料夾中找到兩個已完成的 Unity 幕後。
    * **MixedReality213**：已完成場景與單一筆刷
    * **MixedReality213Advanced**：使用多筆刷完成適用于 advanced design 的場景

**教學課程的新場景設定**

* 在 Unity 中，按一下 [檔案] **> 新增場景**
* 刪除 **主要攝影機** 和 **方向光線**
* 在 [ **專案] 面板** 中，搜尋下列 prefabs，並將 **其拖曳** 到 [階層] 面板中：
    * 資產/HoloToolkit/Input/Prefabs/**MixedRealityCamera**
    * 資產/AppPrefabs/**環境**

    ![攝影機和環境](images/mr213-cameraenvironment-300px.jpg)

* 混合現實工具組中有兩種攝影機 prefabs：
    * **MixedRealityCamera. 預製專案**：僅限相機
    * **MixedRealityCameraParent. 預製專案**：相機 + 遙傳 + 界限
    * 在本教學課程中，我們將使用 **MixedRealityCamera** 而不使用遙傳功能。 因此，我們新增了簡單的 **環境** 預製專案，其中包含讓使用者感覺更接地的基本樓層。
    * 若要深入瞭解遙傳 with **MixedRealityCameraParent**，請參閱 [Advanced design-遙傳 and locomotion](#advanced-design---teleportation-and-locomotion)

**Skybox 設定**

* 按一下 [ **視窗] > 光源 > 設定**
* 按一下 [ **Skybox 材質] 欄位** 右邊的圓形
* 輸入「灰色」並選取 **SkyboxGray** (資產/AppPrefabs/支援/材質/SkyboxGray) 

    ![設定 skybox](images/mr123-skyboxsetting-400px.jpg)

* 檢查 **Skybox** 選項，以查看指派的灰色漸層 Skybox

    ![切換 skybox 選項](images/mr213-skyboxcheck-400px.jpg)

* 具有 MixedRealityCamera、環境和灰色 skybox 的場景看起來會像這樣。

    ![MixedReality213 環境](images/mr213-environment-600px.jpg)

* 按一下 [檔案] **> 另存場景**
* 以任何名稱 **將場景儲存** 在場景資料夾下

## <a name="chapter-1---controller-visualization"></a>第1章-控制器視覺效果

>[!VIDEO https://www.youtube.com/embed/Kw0bf5NqyRg]

### <a name="objectives"></a>目標

* 瞭解如何在 Unity 的遊戲模式和執行時間轉譯移動控制器模型。

Windows Mixed Reality 提供適用于控制器視覺效果的動畫控制器模型。 您可以針對應用程式中的控制器視覺效果採用幾種方法：

* 預設-使用預設控制器而不修改
* 混合式使用預設控制器，但自訂其部分元素或覆迭 UI 元件
* 取代-為控制器使用您自己的自訂3D 模型

在本章中，我們將瞭解這些控制器自訂的範例。

### <a name="instructions"></a>指示

* 在 [ **專案** ] 面板的 [搜尋] 方塊中，輸入 **MotionControllers** 。 您也可以在 [資產/HoloToolkit/輸入/Prefabs/] 下找到它。
* 將 **MotionControllers** 預製專案拖曳到 [階層 **] 面板中** 。
* 按一下 [階層 **] 面板中的 [** **MotionControllers** ] 預製專案。

**MotionControllers 預製專案**

**MotionControllers** 預製專案具有 **MotionControllerVisualizer** 腳本，可提供替代控制器模型的位置。 如果您指派自己的自訂3D 模型（例如手或寶劍）並核取 [一律使用替代模型]，則會看到它們，而不是預設模型。 我們將在第4章中使用這個位置，以筆刷取代控制器模型。

![MR213_ControllerVisualizer](images/mr213-controllervisualizer-600px.png)

**指示**

* 在 [偵測 **器** ] 面板中，按兩下 [ **MotionControllerVisualizer** 腳本] 以查看 Visual Studio 中的程式碼

**MotionControllerVisualizer 腳本**

**MotionControllerVisualizer** 和 **MotionControllerInfo** 類別提供存取 & 修改預設控制器模型的方法。 **MotionControllerVisualizer** 會訂閱 Unity 的 **InteractionSourceDetected** 事件，並且在找到控制器模型時自動將其具現化。

```cs
protected override void Awake()
{
    ...
    InteractionManager.InteractionSourceDetected += InteractionManager_InteractionSourceDetected;
    InteractionManager.InteractionSourceLost += InteractionManager_InteractionSourceLost;
    ...
}
```

控制器模型是根據 [glTF 規格](https://github.com/KhronosGroup/glTF)來傳遞。 這種格式的建立是為了提供通用格式，同時改進了傳輸和解除包裝3D 資產的程式。 在此情況下，我們需要在執行時間取出和載入控制器模型，因為我們想要讓使用者的體驗盡可能順暢，而且不保證使用者可能使用的動作控制器版本。 此課程透過混合現實工具組，使用 Khronos 群組的 [UnityGLTF 專案](https://github.com/KhronosGroup/UnityGLTF)版本。

一旦傳遞控制器，腳本就可以使用 **MotionControllerInfo** 來尋找特定控制器元素的轉換，讓它們可以正確地定位。

在稍後的章節中，我們將瞭解如何使用這些腳本，將 UI 元素附加至控制器。

*在某些腳本中，您會發現具有 #if 的程式碼區塊 **！UNITY_EDITOR** 或 **UNITY_WSA**。這些程式碼區塊只會在您部署至 Windows 時于 UWP 執行時間上執行。這是因為 Unity 編輯器和 UWP 應用程式執行時間所使用的 Api 集不同。*

* **儲存** 場景，然後按一下 [ **播放** ] 按鈕。

您將能夠在耳機中看到有移動控制器的場景。 您可以看到按鈕點擊、操縱杆移動和觸控板觸控醒目提示的詳細動畫。

![MR213_Controller 視覺效果預設](images/mr213-controllervisualizationdefault-500px.jpg)

## <a name="chapter-2---attaching-ui-elements-to-the-controller"></a>第2章-將 UI 元素附加至控制器

>[!VIDEO https://www.youtube.com/embed/e-mLlwmTzJo]

### <a name="objectives"></a>目標

* 瞭解動作控制器的元素
* 瞭解如何將物件附加至控制器的特定部分

在本章中，您將瞭解如何將使用者介面專案新增至控制器，讓使用者隨時都能輕鬆地存取和操作。 您也將瞭解如何使用觸控板輸入來新增簡單的色彩選擇器 UI。

### <a name="instructions"></a>指示

* 在 [ **專案** ] 面板中，搜尋 **MotionControllerInfo** 腳本。
* 從搜尋結果中，按兩下 [ **MotionControllerInfo** 腳本] 以查看 Visual Studio 中的程式碼。

**MotionControllerInfo 腳本**

第一個步驟是選擇您要讓 UI 附加至哪個控制器元素。 這些元素是在 **MotionControllerInfo.cs** 的 **ControllerElementEnum** 中定義。

![MR213 MotionControllerElements](images/mr213-motioncontrollerelements-1000px.jpg)

* **首頁**
* **功能表**
* **把握**
* **操縱杆**
* **選取**
* **觸控板**
* **指標姿勢** –此元素表示控制器指向正向方向的秘訣。

**指示**

* 在 [ **專案** ] 面板中，搜尋 **AttachToController** 腳本。
* 從搜尋結果中，按兩下 [ **AttachToController** 腳本] 以查看 Visual Studio 中的程式碼。

**AttachToController 腳本**

**AttachToController** 腳本提供簡單的方式，將任何物件附加至指定的控制器 handedness 和元素。

在 **AttachElementToController ( # B1** 中，

* 使用 **MotionControllerInfo. handedness** 檢查 handedness
* 使用 MotionControllerInfo. TryGetElement 取得控制器的特定元素 **( # B1**
* 從控制器模型中抓取專案的轉換之後，父物件下的物件和設定物件的本機位置 & 旋轉為零。

```cs
public MotionControllerInfo.ControllerElementEnum Element { get { return element; } }

private void AttachElementToController(MotionControllerInfo newController)
{
     if (!IsAttached && newController.Handedness == handedness)
     {
          if (!newController.TryGetElement(element, out elementTransform))
          {
               Debug.LogError("Unable to find element of type " + element + " under controller " + newController.ControllerParent.name + "; not attaching.");
               return;
          }

          controller = newController;

          SetChildrenActive(true);

          // Parent ourselves under the element and set our offsets
          transform.parent = elementTransform;
          transform.localPosition = positionOffset;
          transform.localEulerAngles = rotationOffset;
          if (setScaleOnAttach)
          {
               transform.localScale = scale;
          }

          // Announce that we're attached
          OnAttachToController();
          IsAttached = true;
     }
}
```

使用 **AttachToController** 腳本最簡單的方式就是從它繼承，如同我們在 ColorPickerWheel 的案例中所做的一樣 **。** 只要覆寫 **OnAttachToController** 和 **OnDetachFromController** 函式，就可以在偵測到控制器/中斷連線時執行您的設定/細目。

**指示**

* 在 [ **專案** ] 面板中，輸入搜尋方塊 **ColorPickerWheel**。 您也可以在 [資產/AppPrefabs/] 下找到它。
* 將 **ColorPickerWheel** 預製專案拖曳到 **[階層** ] 面板中。
* 按一下 [階層 **] 面板中的 [** **ColorPickerWheel** ] 預製專案。
* 在 [偵測 **器** ] 面板中，按兩下 [ **ColorPickerWheel** 腳本] 以查看 Visual Studio 中的程式碼。

![ColorPickerWheel 預製專案](images/mr213-colorpickerwheel-1000px.jpg)

**ColorPickerWheel 腳本**

因為 **ColorPickerWheel** 會繼承 **AttachToController**，所以它會在 [偵測 **器**] 面板中顯示 **Handedness** 和 **元素**。 我們會將 UI 附加至左方控制器上的「觸控板」元素。

![ColorPickerWheel 腳本](images/mr213-attachtocontroller-300px.jpg)

**ColorPickerWheel** 會覆寫 **OnAttachToController** 和 **OnDetachFromController** ，以訂閱將在下一章中用來選取觸控板輸入之色彩的輸入事件。

```cs
public class ColorPickerWheel : AttachToController, IPointerTarget
{
    protected override void OnAttachToController()
    {
        // Subscribe to input now that we're parented under the controller
        InteractionManager.InteractionSourceUpdated += InteractionSourceUpdated;
    }

    protected override void OnDetachFromController()
    {
        Visible = false;

        // Unsubscribe from input now that we've detached from the controller
        InteractionManager.InteractionSourceUpdated -= InteractionSourceUpdated;
    }
    ...
}
```

* **儲存** 場景，然後按一下 [ **播放** ] 按鈕。

**將物件附加至控制器的替代方法**

建議您的腳本繼承自 **AttachToController** 並覆寫 **OnAttachToController**。 不過，這可能不一定可行。 替代方法是使用它作為獨立元件。 當您想要在不重構腳本的情況下，將現有的預製專案附加至控制器時，這會很有用。 您只需在執行任何安裝程式之前，讓您的類別等待 IsAttached 設為 true。 最簡單的方法是使用協同程式作為「開始」。

```cs
private IEnumerator Start() {
    AttachToController attach = gameObject.GetComponent<AttachToController>();

    while (!attach.IsAttached) {
        yield return null;
    }

    // Perform setup here
}
```

## <a name="chapter-3---working-with-touchpad-input"></a>第3章-使用觸控板輸入

>[!VIDEO https://www.youtube.com/embed/SUyw0kxZPFw]

### <a name="objectives"></a>目標

* 瞭解如何取得觸控板輸入資料事件
* 瞭解如何為您的應用程式體驗使用觸控板軸位置資訊

### <a name="instructions"></a>指示

* **在 [階層**] 面板中，按一下 [ **ColorPickerWheel** ]
* 在 [偵測 **器**] 面板的 [ **Animator**] 底下，按兩下 [ **ColorPickerWheelController** ]
* 您將能夠看到開啟的 **Animator** 索引標籤

**使用 Unity 的動畫控制器顯示/隱藏 UI**

若要使用動畫來顯示及隱藏 **ColorPickerWheel** UI，我們會使用 [Unity 的動畫系統](https://docs.unity3d.com/Manual/AnimationOverview.html)。 將 **ColorPickerWheel** 的 **Visible** 屬性設定為 true 或 false 時，觸發程式會 **顯示** 並 **隱藏** 動畫觸發程式。 **顯示** 和 **隱藏** 參數定義于 **ColorPickerWheelController** 動畫控制器中。

![Unity 動畫控制器](images/mr123-animationcontroller-550px.jpg)

**指示**

* **在 [階層**] 面板中，選取 [ **ColorPickerWheel** 預製專案
* 在 [偵測 **器** ] 面板中，按兩下 [ **ColorPickerWheel** 腳本] 以查看 Visual Studio 中的程式碼

**ColorPickerWheel 腳本**

**ColorPickerWheel** 訂閱 Unity 的 **InteractionSourceUpdated** 事件以接聽觸控板事件。

在 **InteractionSourceUpdated ( # B1** 中，腳本會先檢查以確定它：

* 實際上是 (obj 的「觸控板」事件。**touchpadTouched**) 
* 源自左方控制器 (的 obj。**handedness**) 

如果兩者都是 true，表示觸控板位置 (obj。**touchpadPosition**) 會指派給 **selectorPosition**。

```cs
private void InteractionSourceUpdated(InteractionSourceUpdatedEventArgs obj)
{
    if (obj.state.source.handedness == handedness && obj.state.touchpadTouched)
    {
        Visible = true;
        selectorPosition = obj.state.touchpadPosition;
    }
}
```

在 **Update ( # B1** 中，根據 **visible** 屬性，它會觸發在色彩選擇器的 animator 元件中顯示和隱藏動畫觸發程式

```cs
if (visible != visibleLastFrame)
{
    if (visible)
    {
        animator.SetTrigger("Show");
    }
    else
    {
        animator.SetTrigger("Hide");
    }
}
```

在 **Update ( # B1** 中， **selectorPosition** 是用來將光線轉換成色輪的網格碰撞器，它會傳回一個 UV 位置。 然後，您可以使用這個位置來尋找色輪材質的圖元座標和色彩值。 透過 **SelectedColor** 屬性可存取其他腳本的這個值。

![色彩選擇器滾輪 Raycasting](images/mr213-colorpickerwheel-raycast-700px.png)

```cs
...
    // Clamp selector position to a radius of 1
    Vector3 localPosition = new Vector3(selectorPosition.x * inputScale, 0.15f, selectorPosition.y * inputScale);
    if (localPosition.magnitude > 1)
    {
        localPosition = localPosition.normalized;
    }
    selectorTransform.localPosition = localPosition;

    // Raycast the wheel mesh and get its UV coordinates
    Vector3 raycastStart = selectorTransform.position + selectorTransform.up * 0.15f;
    RaycastHit hit;
    Debug.DrawLine(raycastStart, raycastStart - (selectorTransform.up * 0.25f));

    if (Physics.Raycast(raycastStart, -selectorTransform.up, out hit, 0.25f, 1 << colorWheelObject.layer, QueryTriggerInteraction.Ignore))
    {
        // Get pixel from the color wheel texture using UV coordinates
        Vector2 uv = hit.textureCoord;
        int pixelX = Mathf.FloorToInt(colorWheelTexture.width * uv.x);
        int pixelY = Mathf.FloorToInt(colorWheelTexture.height * uv.y);
        selectedColor = colorWheelTexture.GetPixel(pixelX, pixelY);
        selectedColor.a = 1f;
    }
    // Set the selector's color and blend it with white to make it visible on top of the wheel
    selectorRenderer.material.color = Color.Lerp (selectedColor, Color.white, 0.5f);
}
```

## <a name="chapter-4---overriding-controller-model"></a>第4章-覆寫控制器模型

>[!VIDEO https://www.youtube.com/embed/8gBFqA_DZ_U]

### <a name="objectives"></a>目標

* 瞭解如何使用自訂3D 模型覆寫控制器模型。

![MR213_BrushToolOverride](images/mr213-brushtooloverride-500px.jpg)

### <a name="instructions"></a>指示

* 按一下 **[階層**] 面板中的 [ **MotionControllers** ]。
* 按一下 **替代右邊控制器** 欄位右邊的圓形。
* 輸入 **' BrushController**'，然後從結果中選取預製專案。 您可以在資產/AppPrefabs/**BrushController** 中找到它。
* 勾選 [**一律使用替代模型**]

![MR213_BrushToolOverrideSlot](images/mr213-motioncontrollersoverride-700px.jpg)

**BrushController** 預製專案不一定要 **包含在階層面板中**。 不過，若要簽出其子元件：

* 在 [ **專案** ] 面板中，輸入 **BrushController** ，並將 **BrushController** 預製專案拖曳 **到 [階層** ] 面板中。

![MR213_BrushTool_Prefab2](images/mr213-brushtool-prefab-1000px.jpg)

您將會在 **BrushController** 中找到 **Tip** 元件。 我們會使用其轉換來啟動/停止繪製線條。

* 從 **階層面板中** 刪除 **BrushController** 。
* **儲存** 場景，然後按一下 [ **播放** ] 按鈕。 您將能夠看到筆刷模型取代右手邊的移動控制器。

## <a name="chapter-5---painting-with-select-input"></a>第5章-使用選取輸入進行繪製

>[!VIDEO https://www.youtube.com/embed/QTrYaMHIs7w]

### <a name="objectives"></a>目標

* 瞭解如何使用選取按鈕事件來啟動和停止線條繪圖

### <a name="instructions"></a>指示

* 在 [**專案**] 面板中搜尋 **BrushController** 預製專案。
* 在 [偵測 **器** ] 面板中，按兩下 [ **BrushController** 腳本] 以查看 Visual Studio 中的程式碼

**BrushController 腳本**

**BrushController** 訂閱 InteractionManager 的 **InteractionSourcePressed** 和 **InteractionSourceReleased** 事件。 觸發 **InteractionSourcePressed** 事件時，筆刷的 **Draw** 屬性會設定為 true;觸發 **InteractionSourceReleased** 事件時，筆刷的 **Draw** 屬性會設定為 false。

```cs
private void InteractionSourcePressed(InteractionSourcePressedEventArgs obj)
{
    if (obj.state.source.handedness == InteractionSourceHandedness.Right && obj.pressType == InteractionSourcePressType.Select)
    {
        Draw = true;
    }
}

private void InteractionSourceReleased(InteractionSourceReleasedEventArgs obj)
{
    if (obj.state.source.handedness == InteractionSourceHandedness.Right && obj.pressType == InteractionSourcePressType.Select)
    {
        Draw = false;
    }
}
```

當 **Draw** 設定為 true 時，筆刷會在具現化的 Unity **LineRenderer** 中產生點。 此預製專案的參考會保留在筆刷的 [ **筆觸預製專案** ] 欄位中。

```cs
private IEnumerator DrawOverTime()
{
    // Get the position of the tip
    Vector3 lastPointPosition = tip.position;

    ...

    // Create a new brush stroke
    GameObject newStroke = Instantiate(strokePrefab);
    LineRenderer line = newStroke.GetComponent<LineRenderer>();
    newStroke.transform.position = startPosition;
    line.SetPosition(0, tip.position);
    float initialWidth = line.widthMultiplier;

    // Generate points in an instantiated Unity LineRenderer
    while (draw)
    {
        // Move the last point to the draw point position
        line.SetPosition(line.positionCount - 1, tip.position);
        line.material.color = colorPicker.SelectedColor;
        brushRenderer.material.color = colorPicker.SelectedColor;
        lastPointAddedTime = Time.unscaledTime;
        // Adjust the width between 1x and 2x width based on strength of trigger pull
        line.widthMultiplier = Mathf.Lerp(initialWidth, initialWidth * 2, width);

        if (Vector3.Distance(lastPointPosition, tip.position) > minPositionDelta || Time.unscaledTime > lastPointAddedTime + maxTimeDelta)
        {
            // Spawn a new point
            lastPointAddedTime = Time.unscaledTime;
            lastPointPosition = tip.position;
            line.positionCount += 1;
            line.SetPosition(line.positionCount - 1, lastPointPosition);
        }
        yield return null;
    }
}
```

若要從色彩選擇器滾輪 UI 使用目前選取的色彩， **BrushController** 需要有 **ColorPickerWheel** 物件的參考。 因為 **BrushController** 預製專案在執行時間具現化為取代控制器，所以在執行時間必須設定任何對場景中物件的參考。 在此情況下，我們會使用 **GameObject FindObjectOfType** 來找出 **ColorPickerWheel**：

```cs
private void OnEnable()
{
    // Locate the ColorPickerWheel
    colorPicker = FindObjectOfType<ColorPickerWheel>();

    // Assign currently selected color to the brush’s material color
    brushRenderer.material.color = colorPicker.SelectedColor;
    ...
}
```

* **儲存** 場景，然後按一下 [ **播放** ] 按鈕。 您將可以使用右邊控制器上的 [選取] 按鈕來繪製線條和繪圖。

## <a name="chapter-6---object-spawning-with-select-input"></a>第6章-使用 Select 輸入的物件產生

>[!VIDEO https://www.youtube.com/embed/z4IxyzFHP0U]

### <a name="objectives"></a>目標

* 瞭解如何使用 Select 和抓住按鈕輸入事件
* 瞭解如何將物件具現化

### <a name="instructions"></a>指示

* 在 [ **專案** ] 面板的 [搜尋] 方塊中，輸入 **ObjectSpawner** 。 您也可以在資產/AppPrefabs/上找到它
* 將 **ObjectSpawner** 預製專案拖曳到 [階層 **] 面板中** 。
* 按一下 **[階層**] 面板中的 [ **ObjectSpawner** ]。
* **ObjectSpawner** 有一個名為 **Color Source** 的欄位。
* 從 [階層 **] 面板中** ，將 [ **ColorPickerWheel** ] 參考拖曳到此欄位中。

    ![物件 Spawner 偵測器](images/mr213-objectspawnercolorpickerwheel-650px.jpg)

* 按一下 [階層 **] 面板中的 [** **ObjectSpawner** ] 預製專案。
* 在 [偵測 **器** ] 面板中，按兩下 [ **ObjectSpawner** 腳本] 以查看 Visual Studio 中的程式碼。

**ObjectSpawner 腳本**

**ObjectSpawner** 會將基本網格 (cube、球體、圓柱) 的複本具現化到空間中。 偵測到 **InteractionSourcePressed** 時，它會檢查 handedness，如果是 **InteractionSourcePressType** ， **請選取** [事件]。

針對 **理解** 事件，它會將目前網格類型的索引遞增 (球體、cube、圓柱) 

```cs
private void InteractionSourcePressed(InteractionSourcePressedEventArgs obj)
{
    // Check handedness, see if it is left controller
    if (obj.state.source.handedness == handedness)
    {
        switch (obj.pressType)
        {
            // If it is Select button event, spawn object
            case InteractionSourcePressType.Select:
                if (state == StateEnum.Idle)
                {
                    // We've pressed the grasp - enter spawning state
                    state = StateEnum.Spawning;
                    SpawnObject();
                }
                break;

            // If it is Grasp button event
            case InteractionSourcePressType.Grasp:

                // Increment the index of current mesh type (sphere, cube, cylinder)
                meshIndex++;
                if (meshIndex >= NumAvailableMeshes)
                {
                    meshIndex = 0;
                }
                break;

            default:
                break;
        }
    }
}
```

針對 **Select** 事件，在 **SpawnObject ( # B1** 中，會具現化新的物件，並將其具現化，並釋出到全世界。

```cs
private void SpawnObject()
{
    // Instantiate the spawned object
    GameObject newObject = Instantiate(displayObject.gameObject, spawnParent);
    // Detach the newly spawned object
    newObject.transform.parent = null;
    // Reset the scale transform to 1
    scaleParent.localScale = Vector3.one;
    // Set its material color so its material gets instantiated
    newObject.GetComponent<Renderer>().material.color = colorSource.SelectedColor;
}
```

**ObjectSpawner** 會使用 **ColorPickerWheel** 來設定顯示物件材質的色彩。 產生的物件會被授與此材質的實例，以保留其色彩。

* **儲存** 場景，然後按一下 [ **播放** ] 按鈕。

您將可以使用 [理解] 按鈕來變更物件，並使用 [選取] 按鈕產生物件。

## <a name="build-and-deploy-app-to-mixed-reality-portal"></a>建立應用程式並部署到混合實境入口

* 在 Unity 中，選取 [ **File > Build Settings**]。
* 按一下 [ **新增開啟的場景** ]，將目前的場景加入 **組建中的場景**。
* 按一下 [建置]。
* 建立名為 "App" 的 **新資料夾** 。
* 按一下 **應用程式** 資料夾。
* 按一下 [選擇資料夾]。
* 當 Unity 完成時，將會出現檔案總管視窗。
* 開啟 **應用程式** 資料夾。
* 按兩下 [ **YourSceneName** ] Visual Studio 方案檔。
* 使用 Visual Studio 中的頂端工具列，將目標從 Debug 變更為 **Release** ，以及從 ARM 變更為 **X64**。
* 按一下 [裝置] 按鈕旁邊的下拉箭號，然後選取 [ **本機電腦**]。
* 按一下 [ **Debug-> 啟動但不** 在功能表中進行調試]，或按 **Ctrl + F5**。

現在，應用程式已建立並安裝在混合實境入口中。 您可以透過混合實境入口中的 [開始] 功能表再次啟動它。

## <a name="advanced-design---brush-tools-with-radial-layout"></a>先進的設計-具有放射狀配置的筆刷工具

![MixedReality213 Main](images/mr213-main-600px.jpg)

在本章中，您將瞭解如何使用自訂筆刷工具集合來取代預設的動作控制器模型。 針對您的參考，您可以在 [**場景**] 資料夾下找到完成的場景 **MixedReality213Advanced** 。

### <a name="instructions"></a>指示

* 在 [ **專案** ] 面板的 [搜尋] 方塊中，輸入 **BrushSelector** 。 您也可以在資產/AppPrefabs/上找到它
* 將 **BrushSelector** 預製專案拖曳到 [階層 **] 面板中** 。
* 針對組織，建立稱為 **筆刷** 的空白 GameObject
* 將下列 prefabs 從 [ **專案** ] 面板拖曳至 **筆刷**
    * 資產/AppPrefabs/**BrushFat**
    * 資產/AppPrefabs/**BrushThin**
    * 資產/AppPrefabs/**橡皮擦**
    * 資產/AppPrefabs/**MarkerFat**
    * 資產/AppPrefabs/**MarkerThin**
    * 資產/AppPrefabs/**鉛筆**

    ![筆刷](images/mixedreality213-brushes-250px.png)

* 按一下 **[階層**] 面板中的 [ **MotionControllers** 預製專案]。
* 在 [偵測 **器**] 面板中，取消核取 [**移動控制器] 視覺化檢視** 上的 [**永遠使用替代模型**]
* **在 [階層**] 面板中，按一下 [ **BrushSelector** ]
* **BrushSelector** 有一個名為 **ColorPicker** 的欄位
* 從 [階層] 面板中，將 [ **ColorPickerWheel** ] 拖曳至 [偵測 **器** **] 面板中** 的 [ **ColorPicker** ] 欄位。

    ![將 ColorPickerWheel 指派給筆刷選取器](images/mr213-brushselector-500px.jpg)

* 在 [ **階層** ] 面板中，選取 [ **BrushSelector** 預製專案] 底下的 **功能表** 物件。
* 在 [偵測 **器** ] 面板的 [ **LineObjectCollection** ] 元件底下，開啟 [ **物件** 陣列] 下拉式清單。 您會看到6個空的插槽。
* 從 [階層 **] 面板中** ，將 [ **筆刷** ] GameObject 下的每個 prefabs 以任何順序拖曳至這些位置。  (確定您是從場景拖曳 prefabs，而不是從專案資料夾中的 prefabs。 ) 

![筆刷選取器](images/mr213-brushselectorbrushes-700px.jpg)

**BrushSelector 預製專案**

因為 **BrushSelector** 會繼承 **AttachToController**，所以它會在 [偵測 **器**] 面板中顯示 **Handedness** 和 **元素** 選項。 我們選取了 [ **右** ]，並 **指向** [順向]，將筆刷工具附加至右邊控制器。

**BrushSelector** 會使用兩個公用程式：

* **橢圓形**：用來沿著橢圓形圖形來產生空間中的點。
* **LineObjectCollection**：使用任何線條類別產生的點來散發物件 (例如橢圓形) 。 這是我們將用來沿著橢圓形圖形來放置筆刷的內容。

結合之後，這些公用程式可以用來建立放射狀功能表。

**LineObjectCollection 腳本**

**LineObjectCollection** 具有控制項的大小、位置和旋轉，以及沿著線條分佈的物件。 這對於建立星形功能表（例如筆刷選取器）很有用。 若要建立筆刷的外觀，而不會在接近中心選取的位置時相應增加，則 **ObjectScale** 曲線會尖峰于中間，並在邊緣 tapers。

**BrushSelector 腳本**

在 **BrushSelector** 的案例中，我們選擇使用程式動畫。 首先， **LineObjectCollection** 腳本會將筆刷模型散發在橢圓形中。 然後，每個筆刷都會根據選取專案，負責 **維護其在** 使用者手中的位置（視選取專案而定）。 我們選擇了程式性方法，因為當使用者選取筆刷時，筆刷位置轉換會中斷的機率很高。 Mecanim 動畫可以正常地處理中斷情形，但通常比簡單的 Lerp 作業更複雜。

**BrushSelector** 會使用這兩者的組合。 當偵測到觸控板輸入時，筆刷選項會變成可見，並沿著放射狀功能表向上擴充。 在超時期間 (，表示使用者已進行選取) 筆刷選項調整大小，只留下選取的筆刷。

**視覺化觸控板輸入**

即使已完全取代控制器模型，在原始模型輸入上顯示輸入可能會很有説明。 這有助於實現使用者的動作。 針對 **BrushSelector** ，我們選擇讓觸控板在收到輸入時短暫顯示。 這是藉由從控制器中取出觸控板元素、將其材質取代為自訂材質來完成，然後根據收到的前次觸控板輸入將漸層套用至該材質的色彩。

```cs
protected override void OnAttachToController()
{
    // Turn off the default controller's renderers
    controller.SetRenderersVisible(false);

    // Get the touchpad and assign our custom material to it
    Transform touchpad;
    if (controller.TryGetElement(MotionControllerInfo.ControllerElementEnum.Touchpad, out touchpad))
    {
        touchpadRenderer = touchpad.GetComponentInChildren<MeshRenderer>();
        originalTouchpadMaterial = touchpadRenderer.material;
        touchpadRenderer.material = touchpadMaterial;
        touchpadRenderer.enabled = true;
    }

    // Subscribe to input now that we're parented under the controller
    InteractionManager.InteractionSourceUpdated += InteractionSourceUpdated;
}

private void Update()
{
    ...
    // Update our touchpad material
    Color glowColor = touchpadColor.Evaluate((Time.unscaledTime - touchpadTouchTime) / touchpadGlowLossTime);
    touchpadMaterial.SetColor("_EmissionColor", glowColor);
    touchpadMaterial.SetColor("_Color", glowColor);
    ...
}
```

**使用觸控板輸入的筆刷工具選項**

當筆刷選取器偵測到觸控板的已按下輸入時，它會檢查輸入的位置，以判斷其是否為左方或右方。

**使用 selectPressedAmount 的筆觸粗細**

而不是 **InteractionSourcePressType。請選取** **InteractionSourcePressed ( # B1** 中的事件，您可以透過 **selectPressedAmount** 取得按下數量的類比值。 您可以在 **InteractionSourceUpdated ( # B1** 中取出此值。

```cs
private void InteractionSourceUpdated(InteractionSourceUpdatedEventArgs obj)
{
    if (obj.state.source.handedness == handedness)
    {
        if (obj.state.touchpadPressed)
        {
            // Check which side we clicked
            if (obj.state.touchpadPosition.x < 0)
            {
                currentAction = SwipeEnum.Left;
            }
            else
            {
                currentAction = SwipeEnum.Right;
            }

            // Ping the touchpad material so it gets bright
            touchpadTouchTime = Time.unscaledTime;
        }

        if (activeBrush != null)
        {
            // If the pressed amount is greater than our threshold, draw
            if (obj.state.selectPressedAmount >= selectPressedDrawThreshold)
            {
                activeBrush.Draw = true;
                activeBrush.Width = ProcessSelectPressedAmount(obj.state.selectPressedAmount);
            }
            else
            {
                // Otherwise, stop drawing
                activeBrush.Draw = false;
                selectPressedSmooth = 0f;
            }
        }
    }
}
```

**橡皮擦腳本**

**橡皮擦** 是一種特殊類型的筆刷，會覆寫基底 **筆刷** 的 **DrawOverTime ( # B1** 函數。 當 Draw 為 true 時，橡皮擦會檢查其提示是否與任何現有的筆刷筆劃相交。 如果有，則會將它們加入至要壓縮和刪除的佇列。

## <a name="advanced-design---teleportation-and-locomotion"></a>Advanced design-遙傳和 locomotion

如果您想要允許使用者透過遙傳使用操縱杆來移動場景，請使用 **MixedRealityCameraParent** 而不是 **MixedRealityCamera**。 您也需要新增 **InputManager** 和 **DefaultCursor**。 因為 **MixedRealityCameraParent** 已經將 **MotionControllers** 和 **界限** 包含為子元件，所以您應該移除現有的 **MotionControllers** 和 **環境** 預製專案。

### <a name="instructions"></a>指示

* **在 [階層**] 面板中，刪除 [ **MixedRealityCamera**]、[**環境**] 和 [ **MotionControllers** ]
* 在 [ **專案] 面板** 中，搜尋下列 prefabs，並將 **其拖曳** 到 [階層] 面板中：
    * 資產/AppPrefabs/Input/Prefabs/**MixedRealityCameraParent**
    * 資產/AppPrefabs/Input/Prefabs/**InputManager**
    * 資產/AppPrefabs/Input/Prefabs/Cursor/**DefaultCursor**

    ![混合實境相機父系](images/mr213-cameraparent-300px.png)

* **在 [階層**] 面板中，按一下 [**輸入管理員**]
* 在 [偵測 **器** ] 面板中，向下滾動至 **簡單的單一指標選取器** 區段
* 從 [ **階層** ] 面板中，將 [ **DefaultCursor** ] 拖曳至 [ **游標** ] 欄位

    ![指派 DefaultCursor](images/mr213-defaultcursor-500px.png)

* **儲存** 場景，然後按一下 [ **播放** ] 按鈕。 您將能夠使用操縱杆來旋轉左右或傳送。

## <a name="the-end"></a>結束

這就是本教學課程的結尾！ 您已了解︰

* 如何在 Unity 的遊戲模式和執行時間中使用移動控制器模型。
* 如何使用不同類型的按鈕事件和其應用程式。
* 如何覆迭控制器頂端的 UI 元素或完全自訂。

您現在已準備好開始使用移動控制器來建立您自己的沉浸式體驗！

## <a name="completed-scenes"></a>完成的場景

* 在 Unity 的 [ **專案** ] 面板中，按一下 [ **場景** ] 資料夾。
* 您會發現兩個 Unity 場景 **MixedReality213** 和 **MixedReality213Advanced**。
    * **MixedReality213**：已完成場景與單一筆刷
    * **MixedReality213Advanced**：已完成場景，具有具有 select 按鈕的按量範例的多筆刷

## <a name="see-also"></a>另請參閱

* [MR 輸入213專案檔](https://github.com/Microsoft/MixedReality213)
* [混合現實工具組-移動控制器測試場景](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/Input/Scenes)
* [混合現實工具組-抓取機制](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/MotionControllers-GrabMechanics)
* [移動控制器開發指導方針](../design/motion-controllers.md)