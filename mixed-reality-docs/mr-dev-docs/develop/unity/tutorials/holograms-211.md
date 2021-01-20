---
title: MR Input 211 - 手勢
description: 遵循此程式碼逐步解說，使用 Unity、Visual Studio 和 HoloLens 來學習手勢概念的詳細資料。
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit、mixedrealitytoolkit、mixedrealitytoolkit-unity、學術、教學課程、手勢、HoloLens、混合現實學術、unity、混合現實耳機、windows Mixed Reality 耳機、虛擬實境耳機、Windows 10
ms.openlocfilehash: dfb31901001f760abd60bda3022902267b7c05cf
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583705"
---
# <a name="mr-input-211-gesture"></a>MR Input 211：手勢

>[!NOTE]
>混合實境學院教學課程的設計是以 HoloLens (第 1 代) 和混合實境沉浸式頭戴裝置為準。  因此，對於仍在尋找這些裝置開發指引的開發人員而言，我們覺得這些教學課程很重要。  這些教學課程 **_不會_** 使用用於 HoloLens 2 的最新工具組或互動進行更新。  系統會保留這些資訊，以繼續在支援的裝置上運作。 已針對 HoloLens 2 公佈[一系列新的教學課程](./mr-learning-base-01.md)。

[手勢](../../../design/gaze-and-commit.md#composite-gestures) 將使用者意圖變成行動。 透過手勢，使用者可以與全像投影互動。 在此課程中，我們將瞭解如何追蹤使用者的手、回應使用者輸入，並根據手邊的州和地點將意見反應提供給使用者。

>[!VIDEO https://www.youtube.com/embed/c9zlpfFeEtc]

在 [MR 基本的 101](../../../develop/unity/tutorials/holograms-101.md)中，我們使用了簡單的點一下手勢來與我們的全像投影互動。 現在，我們將移至 [輕量] 手勢之外，並探索新的概念以：

* 偵測使用者的手，並提供意見反應給使用者。
* 使用導覽手勢來旋轉我們的全像投影。
* 當使用者的手即將消失時，請提供意見反應。
* 使用操作事件，讓使用者能夠以手移入全像移動影像。

在此課程中，我們將重新流覽 Unity 專案 **模型瀏覽器**，這是我們在 [MR 輸入 210](holograms-210.md)中建立的。 我們太空人的朋友會回頭協助我們探索這些新的手勢概念。

>[!IMPORTANT]
>下列各章節中內嵌的影片是使用較舊版本的 Unity 和混合現實工具組所記錄。 雖然逐步指示是正確且最新的，但您可能會在相對應的影片中看到已過期的腳本和視覺效果。 影片仍隨附于 posterity，因為所涵蓋的概念仍然適用。

## <a name="device-support"></a>裝置支援

<table>
<tr>
<th>課程</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">沉浸式頭戴裝置</a></th>
</tr><tr>
<td>MR Input 211：手勢</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="before-you-start"></a>在您開始使用 Intune 之前

### <a name="prerequisites"></a>必要條件

* [已安裝正確工具](../../../develop/install-the-tools.md)的 Windows 10 電腦。
* 一些基本的 c # 程式設計功能。
* 您應已完成 [MR 基本的 101](../../../develop/unity/tutorials/holograms-101.md)。
* 您應已完成 [MR 輸入 210](holograms-210.md)。
* [針對開發設定](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)的 HoloLens 裝置。

### <a name="project-files"></a>專案檔

* 下載專案 [所需的](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-211-Gesture.zip) 檔案。 需要 Unity 2017.2 或更新版本。
* 取消將檔案封存到您的桌面或其他易於觸及的位置。

>[!NOTE]
>如果您想要在下載之前查看原始程式碼， [可在 GitHub 上](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-211-Gesture)取得。

### <a name="errata-and-notes"></a>勘誤表和記事

* 您必須在 [工具]-[>選項] 下的 Visual Studio 中停用 [啟用 Just My Code] (*未* 核取) ，才能在程式碼中叫用中斷點。

## <a name="chapter-0---unity-setup"></a>第0章-Unity 設定

### <a name="instructions"></a>指示

1. 啟動 Unity。
2. 選取 [開啟]  。
3. 流覽至您先前取消封存的 **手勢** 資料夾。
4. 尋找並選取 [**啟動** / **模型瀏覽器**] 資料夾。
5. 按一下 [ **選取資料夾** ] 按鈕。
6. 在 [ **專案** ] 面板中，展開 [ **場景** ] 資料夾。
7. 按兩下 [ **ModelExplorer** 場景]，以在 Unity 中載入。

### <a name="building"></a>建置

1. 在 Unity 中，選取 [ **File > Build Settings**]。
2. 如果 **場景/ModelExplorer** 未列在 **組建的場景** 中，請按一下 [ **新增開啟場景** ] 以加入場景。
3. 如果您是特別針對 HoloLens 進行開發，請將 **目標裝置** 設定為 **hololens**。 否則，請將它保留在 **任何裝置** 上。
4. 請確定 **組建類型** 設定為 [ **D3D** ]，並將 [ **Sdk** ] 設定為 [ **最新安裝** 的 (，其應為 SDK 16299 或更新版本的) 。
5. 按一下 [建置]。
6. 建立名為 "App" 的 **新資料夾** 。
7. 按一下 **應用程式** 資料夾。
8. 按下 [ **選取資料夾** ]，Unity 就會開始建立 Visual Studio 的專案。

當 Unity 完成時，將會出現檔案總管視窗。

1. 開啟 **應用程式** 資料夾。
2. 開啟 **ModelExplorer Visual Studio 方案**。

如果要部署到 HoloLens：

1. 使用 Visual Studio 中的頂端工具列，將目標從 Debug 變更為 **Release** ，以及從 ARM 變更為 **x86**。
2. 按一下 [本機電腦] 按鈕旁的下拉箭號，然後選取 [ **遠端電腦**]。
3. 輸入 **您的 HoloLens 裝置 IP 位址** ，並將驗證模式設定為 **通用 (未加密的通訊協定)**。 按一下 [選取]。 如果您不知道您的裝置 IP 位址，請查看 [ **設定] > Network & Internet > Advanced 選項**。
4. 在頂端功能表列中，按一下 [ **Debug-> 啟動但不進行調試** ]，或按 **Ctrl + F5**。 如果這是您第一次部署至您的裝置，您必須將 [它與 Visual Studio 配對](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#pairing-your-device)。
5. 部署應用程式之後，請使用 **選取手勢** 來關閉 **Fitbox** 。

如果部署到沉浸式耳機：

1. 使用 Visual Studio 中的頂端工具列，將目標從 Debug 變更為 **Release** ，以及從 ARM 變更為 **x64**。
2. 請確定部署目標設定為 [ **本機電腦**]。
3. 在頂端功能表列中，按一下 [ **Debug-> 啟動但不進行調試** ]，或按 **Ctrl + F5**。
4. 部署應用程式之後，請在動作控制器上提取觸發程式來關閉 **Fitbox** 。

>[!NOTE]
>您可能會注意到 Visual Studio 錯誤面板中有一些紅色錯誤。 您可以放心地忽略它們。 切換至 [輸出] 面板以查看實際的組建進度。 輸出面板中的錯誤會要求您進行修正 (最常見的原因是腳本) 中發生錯誤。

## <a name="chapter-1---hand-detected-feedback"></a>第1章-手動偵測到的意見反應

>[!VIDEO https://www.youtube.com/embed/D1FcIyuFTZQ]

### <a name="objectives"></a>目標

* 訂閱手邊的追蹤事件。
* 使用資料指標意見反應，在追蹤手時顯示使用者。

>[!NOTE]
>在 HoloLens 2 上，只要手指出現時，就會引發 (，而不只是手指指向) 。

### <a name="instructions"></a>指示

* **在 [階層] 面板中**，展開 [ **InputManager** ] 物件。
* 尋找並選取 [ **GesturesInput** ] 物件。

**InteractionInputSource.cs** 腳本會執行這些步驟：

1. 訂閱 InteractionSourceDetected 和 InteractionSourceLost 事件。
2. 設定 HandDetected 狀態。
3. 從 InteractionSourceDetected 和 InteractionSourceLost 事件取消訂閱。

接下來，我們會根據使用者的動作，將我們的資料指標從 [MR 輸入 210](holograms-210.md) 升級為一個顯示意見反應的資料指標。

1. **在 [階層**] 面板中，選取資料 **指標** 物件，並將其刪除。
2. 在 [ **專案** ] 面板中，搜尋 **CursorWithFeedback** ，然後將它拖曳 **至 [階層** ] 面板中。
3. 按一下 [階層 **] 面板中的 [** **InputManager** ]，然後將 [ **CursorWithFeedback** ] 物件從階層 **拖曳至偵測****器** 底部的 InputManager **SimpleSinglePointerSelector** 資料 **指標** 欄位中。
4. 按一下階層 **中的** **CursorWithFeedback** 。
5. 在 [偵測 **器**] 面板中，展開物件資料 **指標** 腳本上的 **資料指標狀態資料**。

**資料指標狀態資料** 的運作方式如下：

* 任何 **觀察** 狀態都表示未偵測到任何東西，而使用者只需要四處尋找。
* 任何 **互動** 狀態表示偵測到手或控制器。
* 任何 **暫** 止狀態都表示使用者正在查看全像影像。

### <a name="build-and-deploy"></a>建置和部署

* 在 Unity 中，使用檔案 **> 組建設定** 來重建應用程式。
* 開啟 **應用程式** 資料夾。
* 如果尚未開啟，請開啟 **ModelExplorer Visual Studio 方案**。
  *  (如果您已在安裝期間于 Visual Studio 中建立或部署此專案，則您可以開啟 VS 的實例，然後在出現) 提示時按一下 [全部重載]。
* 在 Visual Studio 中，按一下 [ **Debug-> 啟動但不進行調試** ]，或按 **Ctrl + F5**。
* 將應用程式部署到 HoloLens 之後，請使用 [點一下手勢] 來關閉 fitbox。
* 將您的手移至視野，並將您的索引手指指向天空以開始進行追蹤。
* 將您的手靠左、靠右、向上和向下移動。
* 觀賞偵測到您手上的游標變更，然後從 view 遺失。
* 如果您是在沉浸式耳機上，則必須連接並中斷控制器的連線。 這種意見反應在沉浸式裝置上變得較不有趣，因為連接的控制器一律會「可用」。

## <a name="chapter-2---navigation"></a>第2章-導覽

>[!VIDEO https://www.youtube.com/embed/sm-kxtKksSo]

### <a name="objectives"></a>目標

* 使用導覽手勢事件來旋轉太空人。

### <a name="instructions"></a>指示

若要在我們的應用程式中使用導覽手勢，我們將會在導覽手勢發生時，編輯 **GestureAction.cs** 來旋轉物件。 此外，我們會將意見反應新增至游標，以在流覽可供使用時顯示。

1. **在 [階層**] 面板中，展開 [ **CursorWithFeedback**]。
2. 在 [全像 **] 資料夾中** ，尋找 **ScrollFeedback** 資產。
3. 將 **ScrollFeedback** 預製專案拖放到階層中的 **CursorWithFeedback** **GameObject。**
4. 按一下 [ **CursorWithFeedback**]。
5. 在 [偵測 **器** ] 面板中，按一下 [ **新增元件** ] 按鈕。
6. 在功能表的 [搜尋] 方塊中，輸入 **CursorFeedback**。 選取搜尋結果。
7. 從階層中，將 **ScrollFeedback** **物件拖放至偵測****器** 中 **游標回饋** 元件的 [ **Scroll 偵測到的遊戲物件**] 屬性。
8. **在 [階層] 面板中**，選取 [ **AstroMan** ] 物件。
9. 在 [偵測 **器** ] 面板中，按一下 [ **新增元件** ] 按鈕。
10. 在功能表中，輸入搜尋方塊的 **手勢動作**。 選取搜尋結果。

接下來，在 Visual Studio 中開啟 **GestureAction.cs** 。 在編碼練習 2. c 中，編輯腳本以執行下列動作：

1. 每當執行導覽手勢時 **，旋轉 AstroMan** 物件。
2. 計算 **rotationFactor** 以控制套用至物件的旋轉量。
3. 當使用者向左或向右移動時，旋轉 y 軸周圍的 **物件**。

在腳本中完成編碼練習 2. c，或以下列完成的解決方案取代程式碼：

```cs
using HoloToolkit.Unity.InputModule;
using UnityEngine;

/// <summary>
/// GestureAction performs custom actions based on
/// which gesture is being performed.
/// </summary>
public class GestureAction : MonoBehaviour, INavigationHandler, IManipulationHandler, ISpeechHandler
{
    [Tooltip("Rotation max speed controls amount of rotation.")]
    [SerializeField]
    private float RotationSensitivity = 10.0f;

    private bool isNavigationEnabled = true;
    public bool IsNavigationEnabled
    {
        get { return isNavigationEnabled; }
        set { isNavigationEnabled = value; }
    }

    private Vector3 manipulationOriginalPosition = Vector3.zero;

    void INavigationHandler.OnNavigationStarted(NavigationEventData eventData)
    {
        InputManager.Instance.PushModalInputHandler(gameObject);
    }

    void INavigationHandler.OnNavigationUpdated(NavigationEventData eventData)
    {
        if (isNavigationEnabled)
        {
            /* TODO: DEVELOPER CODING EXERCISE 2.c */

            // 2.c: Calculate a float rotationFactor based on eventData's NormalizedOffset.x multiplied by RotationSensitivity.
            // This will help control the amount of rotation.
            float rotationFactor = eventData.NormalizedOffset.x * RotationSensitivity;

            // 2.c: transform.Rotate around the Y axis using rotationFactor.
            transform.Rotate(new Vector3(0, -1 * rotationFactor, 0));
        }
    }

    void INavigationHandler.OnNavigationCompleted(NavigationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void INavigationHandler.OnNavigationCanceled(NavigationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void IManipulationHandler.OnManipulationStarted(ManipulationEventData eventData)
    {
        if (!isNavigationEnabled)
        {
            InputManager.Instance.PushModalInputHandler(gameObject);

            manipulationOriginalPosition = transform.position;
        }
    }

    void IManipulationHandler.OnManipulationUpdated(ManipulationEventData eventData)
    {
        if (!isNavigationEnabled)
        {
            /* TODO: DEVELOPER CODING EXERCISE 4.a */

            // 4.a: Make this transform's position be the manipulationOriginalPosition + eventData.CumulativeDelta
        }
    }

    void IManipulationHandler.OnManipulationCompleted(ManipulationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void IManipulationHandler.OnManipulationCanceled(ManipulationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void ISpeechHandler.OnSpeechKeywordRecognized(SpeechEventData eventData)
    {
        if (eventData.RecognizedText.Equals("Move Astronaut"))
        {
            isNavigationEnabled = false;
        }
        else if (eventData.RecognizedText.Equals("Rotate Astronaut"))
        {
            isNavigationEnabled = true;
        }
        else
        {
            return;
        }

        eventData.Use();
    }
}
```

您將會注意到其他導覽事件已填入部分資訊。 我們會將 GameObject 推送至工具組的 InputSystem's 強制回應堆疊，如此一來，使用者就不需要在旋轉開始之後，將焦點放在太空人上。 同樣地，當手勢完成時，我們會將 GameObject 從堆疊中取出。

### <a name="build-and-deploy"></a>建置和部署

1. 在 Unity 中重建應用程式，然後從 Visual Studio 建立和部署應用程式，以在 HoloLens 中執行該應用程式。
2. 在太空人中，兩個箭號應該會出現在游標的任一邊。 這個新的視覺效果表示可以旋轉太空人。
3. 將您的手移至天空 (的索引手指) ，讓 HoloLens 開始追蹤您的手。
4. 若要旋轉太空人，請將您的索引指向較低的位置，然後向左或向右移動以觸發 NavigationX 手勢。

## <a name="chapter-3---hand-guidance"></a>第3章-手指引

>[!VIDEO https://www.youtube.com/embed/ULzlVw4e14I]

### <a name="objectives"></a>目標

* 使用 **手動指引分數** 來協助預測何時會遺失手動追蹤。
* 提供資料 **指標的意見** 反應，以在使用者的手中接近相機的視圖邊緣時顯示。

### <a name="instructions"></a>指示

1. **在 [階層] 面板中**，選取 [ **CursorWithFeedback** ] 物件。
2. 在 [偵測 **器** ] 面板中，按一下 [ **新增元件** ] 按鈕。
3. 在功能表中，輸入搜尋方塊 **手動指引**。 選取搜尋結果。
4. 在 [ **專案** ] **面板的** [全像] 資料夾中，尋找 **HandGuidanceFeedback** 資產。
5. 將 **HandGuidanceFeedback** 資產拖放到 [偵測 **器**] 面板中的 [**手形指導指標**] 屬性。

### <a name="build-and-deploy"></a>建置和部署

* 在 Unity 中重建應用程式，然後從 Visual Studio 建立並部署，以在 HoloLens 上體驗應用程式。
* 將您的手移至視野，並提升您的食指以進行追蹤。
* 使用導覽手勢開始旋轉太空人 (將您的索引手指和) 一起縮小。
* 將您的手上移、靠右、向上和向下移動。
* 當您手接近手勢框架的邊緣時，游標旁邊應該會出現箭號，以警告您將會遺失手動追蹤。 箭號會指出移動手的方向，以防止追蹤遺失。

## <a name="chapter-4---manipulation"></a>第4章-操作

>[!VIDEO https://www.youtube.com/embed/f3m8MvU60-I]

### <a name="objectives"></a>目標

* 使用操作事件以您的手移太空人。
* 提供資料指標的意見反應，讓使用者知道可以使用操作的時機。

### <a name="instructions"></a>指示

GestureManager.cs 和 AstronautManager.cs 可讓我們執行下列作業：

1. 使用語音關鍵字 "**Move 太空人**" 來啟用 **操作** 手勢和「**旋轉太空人**」以停用它們。
2. 切換以回應 **操作手勢辨識器**。

讓我們開始這次的教學。

1. **在 [階層**] 面板中，建立新的空白 GameObject。 將它命名為 "**AstronautManager**"。
2. 在 [偵測 **器** ] 面板中，按一下 [ **新增元件** ] 按鈕。
3. 在功能表中，于 [搜尋 box **太空人管理員**] 中輸入。 選取搜尋結果。
4. 在 [偵測 **器** ] 面板中，按一下 [ **新增元件** ] 按鈕。
5. 在功能表中，輸入搜尋方塊 **語音輸入來源**。 選取搜尋結果。

我們現在會新增控制太空人互動狀態所需的語音命令。

1. 展開 [**檢查**] 中的 [**關鍵字**] 區段。
2. 按一下右側的， **+** 以加入新的關鍵字。
3. 輸入關鍵字做為 **移動太空人**。 如有需要，請隨意新增按鍵快捷方式。
4. 按一下右側的， **+** 以加入新的關鍵字。
5. 將關鍵字輸入為 **旋轉太空人**。 如有需要，請隨意新增按鍵快捷方式。
6. 對應的處理常式程式碼可以在 **GestureAction.cs** 的 **ISpeechHandler. OnSpeechKeywordRecognized** 處理常式中找到。

![如何設定第4章的語音輸入來源](images/holograms211-speech.png)

接下來，我們將設定資料指標的操作意見反應。

1. 在 [ **專案** ] **面板的** [全像] 資料夾中，尋找 **PathingFeedback** 資產。
2. 將 **PathingFeedback** 預製專案拖放到階層中的 **CursorWithFeedback** **物件。**
3. **在 [階層**] 面板中，按一下 [ **CursorWithFeedback**]。
4. 從階層中，將 **PathingFeedback** **物件拖放至偵測****器** 的 [資料 **指標意見**] 元件中的 [偵測 **到的遊戲物件**] 屬性。

現在，我們需要將程式碼新增至 **GestureAction.cs** ，以啟用下列各項：

1. 將程式碼加入至 **IManipulationHandler. OnManipulationUpdated** 函式，這會在偵測到 **操作** 手勢時移動太空人。
2. 計算 **移動向量** ，以根據手上的位置決定應將太空人移至何處。
3. **將太空人移** 至新的位置。

完成編碼練習 4. **GestureAction.cs**，或使用我們完成的解決方案：

```cs
using HoloToolkit.Unity.InputModule;
using UnityEngine;

/// <summary>
/// GestureAction performs custom actions based on
/// which gesture is being performed.
/// </summary>
public class GestureAction : MonoBehaviour, INavigationHandler, IManipulationHandler, ISpeechHandler
{
    [Tooltip("Rotation max speed controls amount of rotation.")]
    [SerializeField]
    private float RotationSensitivity = 10.0f;

    private bool isNavigationEnabled = true;
    public bool IsNavigationEnabled
    {
        get { return isNavigationEnabled; }
        set { isNavigationEnabled = value; }
    }

    private Vector3 manipulationOriginalPosition = Vector3.zero;

    void INavigationHandler.OnNavigationStarted(NavigationEventData eventData)
    {
        InputManager.Instance.PushModalInputHandler(gameObject);
    }

    void INavigationHandler.OnNavigationUpdated(NavigationEventData eventData)
    {
        if (isNavigationEnabled)
        {
            /* TODO: DEVELOPER CODING EXERCISE 2.c */

            // 2.c: Calculate a float rotationFactor based on eventData's NormalizedOffset.x multiplied by RotationSensitivity.
            // This will help control the amount of rotation.
            float rotationFactor = eventData.NormalizedOffset.x * RotationSensitivity;

            // 2.c: transform.Rotate around the Y axis using rotationFactor.
            transform.Rotate(new Vector3(0, -1 * rotationFactor, 0));
        }
    }

    void INavigationHandler.OnNavigationCompleted(NavigationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void INavigationHandler.OnNavigationCanceled(NavigationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void IManipulationHandler.OnManipulationStarted(ManipulationEventData eventData)
    {
        if (!isNavigationEnabled)
        {
            InputManager.Instance.PushModalInputHandler(gameObject);

            manipulationOriginalPosition = transform.position;
        }
    }

    void IManipulationHandler.OnManipulationUpdated(ManipulationEventData eventData)
    {
        if (!isNavigationEnabled)
        {
            /* TODO: DEVELOPER CODING EXERCISE 4.a */

            // 4.a: Make this transform's position be the manipulationOriginalPosition + eventData.CumulativeDelta
            transform.position = manipulationOriginalPosition + eventData.CumulativeDelta;
        }
    }

    void IManipulationHandler.OnManipulationCompleted(ManipulationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void IManipulationHandler.OnManipulationCanceled(ManipulationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void ISpeechHandler.OnSpeechKeywordRecognized(SpeechEventData eventData)
    {
        if (eventData.RecognizedText.Equals("Move Astronaut"))
        {
            isNavigationEnabled = false;
        }
        else if (eventData.RecognizedText.Equals("Rotate Astronaut"))
        {
            isNavigationEnabled = true;
        }
        else
        {
            return;
        }

        eventData.Use();
    }
}
```

### <a name="build-and-deploy"></a>建置和部署

* 在 Unity 中重建，然後從 Visual Studio 建立並部署，以在 HoloLens 中執行應用程式。
* 將您手上的手移至 HoloLens 之前，並提起您的食指以進行追蹤。
* 將游標放在太空人上。
* 說 ' Move 太空人 ' 可將太空人與操作手勢移動。
* 游標周圍應該會出現四個箭號，以指出程式現在會回應操作事件。
* 將您的索引向下移至您的 thumb，並讓它們 pinched 在一起。
* 當您手上四處移動時，太空人也會移動 (這是) 的操作。
* 提高您的索引手指，以停止操作太空人。
* 注意：如果您在移動手之前沒有說「移動太空人」，則會改用導覽手勢。
* 說「旋轉太空人」以返回 rotatable 狀態。

## <a name="chapter-5---model-expansion"></a>第5章-模型擴充

>[!VIDEO https://www.youtube.com/embed/dA11P4P0VO8]

### <a name="objectives"></a>目標

* 將太空人模型擴充為多個較小的片段，讓使用者可以與之互動。
* 使用導覽和操作手勢來個別移動每個片段。

### <a name="instructions"></a>指示

在本節中，我們將完成下列工作：

1. 加入新的關鍵字「**展開模型**」以展開太空人模型。
2. 加入新的關鍵字 [**重設模型**]，將模型傳回至其原始表單。

我們會藉由將兩個以上的關鍵字新增至上一章中的語音輸入來源來完成這項作業。 我們也將示範另一個處理辨識事件的方式。

1. 在 [偵測 **器**] 中按一下 [上一步]，然後在 [**檢查** **] 中展開**[**關鍵字**] 區段。
2. 按一下右側的， **+** 以加入新的關鍵字。
3. 輸入關鍵字做為 **展開模型**。 如有需要，請隨意新增按鍵快捷方式。
4. 按一下右側的， **+** 以加入新的關鍵字。
5. 輸入關鍵字做為 **重設模型**。 如有需要，請隨意新增按鍵快捷方式。
6. 在 [偵測 **器** ] 面板中，按一下 [ **新增元件** ] 按鈕。
7. 在功能表中，輸入搜尋方塊 **語音輸入處理常式**。 選取搜尋結果。
8. 檢查 **是否為全域接聽程式**，因為我們想要讓這些命令運作，而不論我們所關注的 GameObject 為何。
9. 按一下該 **+** 按鈕，然後從 [關鍵字] 下拉式清單中選取 [ **展開模型** ]。
10. 按一下 [ **+** 回應] 下的 [AstronautManager]，然後將階層中的 [  ] 拖曳到 [**無 (物件)** ] 欄位中。
11. 現在，按一下 [ **沒有** 函式] 下拉式清單，選取 [ **AstronautManager**]，然後按一下 [ **ExpandModelCommand**]。
12. 按一下 [語音輸入處理常式 **+** ] 按鈕，然後從 [關鍵字] 下拉式清單中選取 [ **重設模型** ]。
13. 按一下 [ **+** 回應] 下的 [AstronautManager]，然後將階層中的 [  ] 拖曳到 [**無 (物件)** ] 欄位中。
14. 現在，按一下 [ **沒有** 函式] 下拉式清單，選取 [ **AstronautManager**]，然後按一下 [ **ResetModelCommand**]。

![如何設定第5章的語音輸入來源和處理常式](images/holograms211-speechhandler.png)

### <a name="build-and-deploy"></a>建置和部署

* 試試看！ 建立應用程式，並將其部署到 HoloLens。
* **展開 [展開模型**] 以查看展開的太空人模型。
* 使用 **導覽** 來旋轉太空人花色的個別部分。
* 假設 **Move 太空人** ，然後使用 **操作** 來移動太空人花色的個別部分。
* 例如， **旋轉太空人** 可再次旋轉零件。
* 假設 **重設模型** 將太空人傳回其原始表單。

## <a name="the-end"></a>結束

恭喜！ 您現在已完成 **MR 輸入211：手勢**。

* 您知道如何偵測和回應手動追蹤、流覽和操作事件。
* 您瞭解導覽和操作手勢之間的差異。
* 您知道如何變更資料指標，以提供有關何時偵測到手的視覺回應、當手即將遺失，以及物件支援不同互動 (導覽與操作) 之間的視覺化意見反應。