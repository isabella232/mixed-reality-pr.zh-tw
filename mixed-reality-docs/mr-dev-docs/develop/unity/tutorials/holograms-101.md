---
title: HoloLens (第1代) 基本概念 101-使用裝置完成專案
description: 遵循此程式碼逐步解說，使用 Unity、Visual Studio 和 HoloLens 來瞭解 Windows Mixed Reality 的基本概念。
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: mixed reality、Windows Mixed Reality、HoloLens、全息圖、學術、教學課程、HoloLens、混合的現實學術、unity、混合現實耳機、Windows Mixed reality 耳機、虛擬實境耳機、Windows 10
ms.openlocfilehash: 0ebfeb017271b7f98093a8ba6cac59dccae2a440
ms.sourcegitcommit: 3236abcba27335fe3d52e38423d2b265ca883355
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2021
ms.locfileid: "106269944"
---
# <a name="hololens-1st-gen-basics-101-complete-project-with-device"></a>HoloLens (第1代) 基本概念101：使用裝置完成專案

<br>

>[!IMPORTANT]
>混合的現實學術教學課程是以 HoloLens (第一代) 、Unity 2017 和混合現實的沉浸式耳機來設計的。  因此，對於仍在尋找這些裝置開發指引的開發人員而言，我們覺得這些教學課程很重要。 這些教學課程 **_不_** 會使用最新的工具組或互動進行 HoloLens 2，而且可能與較新版本的 Unity 不相容。  系統會保留這些資訊，以繼續在支援的裝置上運作。 已針對 HoloLens 2 公佈[一系列新的教學課程](mrlearning-base.md)。

<br>

>[!VIDEO https://www.youtube.com/embed/XKIIEC5BMWg]

本教學課程將逐步引導您完成內建 Unity 的完整專案，以示範 HoloLens 上的核心 Windows Mixed Reality 功能，包括 [注視](../../../design/gaze-and-commit.md)、 [手勢](../../../design/gaze-and-commit.md#composite-gestures)、 [語音輸入](../../../design/voice-input.md)、 [空間音效](../../../design/spatial-sound.md) 和 [空間對應](../../../design/spatial-mapping.md)。

本教學課程需要大約1小時才能完成。

## <a name="device-support"></a>裝置支援

<table>
<tr>
<th>課程</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">沉浸式頭戴裝置</a></th>
</tr><tr>
<td>MR Basics 101：使用裝置完成專案</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a>在您開始使用 Intune 之前

### <a name="prerequisites"></a>必要條件

* [已安裝正確工具](../../install-the-tools.md)的 Windows 10 電腦。
* [針對開發設定](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)的 HoloLens 裝置。

### <a name="project-files"></a>專案檔

* 下載專案 [所需的](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-101.zip) 檔案。 需要 Unity 2017.2 或更新版本。
  * 如果您仍然需要 Unity 5.6 支援，請使用 [此版本](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-101.zip)。
  * 如果您仍然需要 Unity 5.5 支援，請使用 [此版本](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-101.zip)。
  * 如果您仍然需要 Unity 5.4 支援，請使用 [此版本](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-101.zip)。
* 取消將檔案封存到您的桌面或其他易於觸及的位置。 將資料夾名稱保留為 **日式**。

>[!NOTE]
>如果您想要在下載之前查看原始程式碼， [可在 GitHub 上](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-101)取得。

## <a name="chapter-1---holo-world"></a>第1章-「Hololens」世界

>[!VIDEO https://www.youtube.com/embed/PmtZGjYFroY]

在本章中，我們將設定第一個 Unity 專案，並逐步執行組建和部署程式。

### <a name="objectives"></a>目標

* 設定 Unity 進行全像開發。
* 製作全像影像。
* 查看您製作的全像影像。

### <a name="instructions"></a>指示

* 啟動 Unity。
* 選取 [開啟]  。
* 輸入 [位置] 作為您先前取消封存的 [ **折紙** ] 資料夾。
* 選取 [ **折紙** ]，然後按一下 [ **選取資料夾**]。
* 由於 **日式** 投影專案不包含場景，請使用： **file**  /  **save 場景 As**，將空的預設場景儲存至新檔案。
* 將新的場景命名為 **日式** ，然後按下 [ **儲存** ] 按鈕。

#### <a name="setup-the-main-virtual-camera"></a>設定主要虛擬攝影機

* 在 [階層面板] 中，選取 [主要相機]。
* 在偵測 **器** 中，將其轉換位置設定為 **0、0、0**。
* 尋找 [ **清除旗標** ] 屬性，並將下拉式清單從 [ **Skybox** ] 變更為 [ **純色**]。
* 按一下 [背景] 欄位，以開啟色彩選擇器。
* 將 **R、G、B 和 A** 設為 **0**。

#### <a name="setup-the-scene"></a>設定場景

* 在 [階層] **面板** 中，按一下 [ **建立** ] 並 **建立空白**。
* 以滑鼠右鍵按一下新的 **GameObject** ，然後選取 [重新命名]。 將 GameObject 重新命名為 **OrigamiCollection**。
* 從 [專案] 面板中 **的 [全** 像] 資料夾 (展開 [資產]，然後選取 [全選]，然後在 [專案]) 面板中，按兩下 [全像
  * 將 [ **階段** ] 拖曳到階層中，成為 **OrigamiCollection** 的子系。
  * 將 **Sphere1** 拖曳到階層中，以成為 **OrigamiCollection** 的子系。
  * 將 **Sphere2** 拖曳到階層中，以成為 **OrigamiCollection** 的子系。
* 以滑鼠右鍵按一下 [階層]**面板** 中的 **方向光源** 物件，然後選取 [**刪除**]。
* 從 [全像 **] 資料夾，將****燈光** 拖曳到階層 **面板** 的根目錄中。
* **在階層中，選取** **OrigamiCollection**。
* 在偵測 **器** 中，將轉換位置設定為 **0、-0.5、2.0**。
* 按下 Unity 中的 [ **播放** ] 按鈕，以預覽您的全像影像。
* 您應該會在預覽視窗中看到 [折紙] 物件。
* 按第二次 [ **播放** ] 以停止預覽模式。

#### <a name="export-the-project-from-unity-to-visual-studio"></a>將專案從 Unity 匯出至 Visual Studio

* 在 Unity 中，選取 [ **File > Build Settings**]。
* 在 [**平臺**] 清單中選取 **通用 Windows 平臺**，然後按一下 [**切換平臺**]。
* 將 **SDK** 設定為 **通用 10** ，並將 **組建類型** 設定為 **D3D**。
* 檢查 **Unity c # 專案**。
* 按一下 [ **新增開啟場景** ] 以加入場景。
* 按一下 [建置]。
* 在出現的 [檔案瀏覽器] 視窗中，建立名為 "App" 的 **新資料夾** 。
* 按一下 **應用程式資料夾**。
* 按下 [ **選取資料夾**]。
* 當 Unity 完成時，將會出現檔案總管視窗。
* 開啟 **應用程式** 資料夾。
* 開啟 (按兩下) **的折紙**。
* 使用 Visual Studio 中的頂端工具列，將目標從 Debug 變更為 **Release** ，以及從 ARM 變更為 **X86**。
* 按一下 [裝置] 按鈕旁邊的箭號，然後選取 [ **遠端電腦** ] 以透過 wi-fi 進行部署。
  * 將 **位址** 設定為 HoloLens 的名稱或 IP 位址。 如果您不知道您的裝置 IP 位址，請查看 [ **設定] > 網路 & 網際網路 > [Advanced Options** ] 或 [問 Cortana **] 嗨 Cortana，我的 IP 位址為何？**
  * 如果 HoloLens 是透過 USB 連接，您可以改為選取要透過 USB 部署的 **裝置** 。
  * 將 [ **驗證模式]** 設定為 [ **通用**]。
  * 按一下 [**選取**]

* 按一下 [ **Debug > 啟動但不進行調試** ]，或按 **Ctrl + F5**。 如果這是您第一次部署至您的裝置，您必須將 [它與 Visual Studio 配對](../../platform-capabilities-and-apis/using-visual-studio.md#pairing-your-device)。

* 現在，將會建立日式的專案，並部署到您的 HoloLens，然後執行。
* 放在 HoloLens 上，看看看看您的新全息。

## <a name="chapter-2---gaze"></a>第2章-注視

>[!VIDEO https://www.youtube.com/embed/MSO2BoFSQbM]

在本章中，我們將介紹三種與您的全像的影像互動的第一種方式： [注視](../../../design/gaze-and-commit.md)。

### <a name="objectives"></a>目標

* 使用世界鎖定的資料指標將您的注視視覺化。

### <a name="instructions"></a>指示

* 返回至您的 Unity 專案，如果仍然開啟 [組建設定] 視窗，請加以關閉。
* 在 [**專案] 面板** 中，選取 [全像 **] 資料夾。**
* 將資料 **指標** 物件拖曳至根層級的階層 **面板** 中。
* 按兩下資料 **指標** 物件，深入瞭解它。
* 以滑鼠右鍵按一下 [專案] 面板中的 [ **腳本** ] 資料夾。
* 按一下 [ **建立** ] 子功能表。
* 選取 **c # 腳本**。
* 將腳本命名為 **WorldCursor**。 注意：名稱會區分大小寫。 您不需要新增 .cs 副檔名。
* 在 [階層]**面板** 中選取資料 **指標** 物件。
* 將 **WorldCursor** 腳本拖放到 [ **檢查] 面板** 中。
* 按兩下 **WorldCursor** 腳本，在 Visual Studio 中開啟它。
* 將此程式碼複製並貼到 **WorldCursor** 中，並 **全部儲存**。

```cs
using UnityEngine;

public class WorldCursor : MonoBehaviour
{
    private MeshRenderer meshRenderer;

    // Use this for initialization
    void Start()
    {
        // Grab the mesh renderer that's on the same object as this script.
        meshRenderer = this.gameObject.GetComponentInChildren<MeshRenderer>();
    }

    // Update is called once per frame
    void Update()
    {
        // Do a raycast into the world based on the user's
        // head position and orientation.
        var headPosition = Camera.main.transform.position;
        var gazeDirection = Camera.main.transform.forward;

        RaycastHit hitInfo;

        if (Physics.Raycast(headPosition, gazeDirection, out hitInfo))
        {
            // If the raycast hit a hologram...
            // Display the cursor mesh.
            meshRenderer.enabled = true;

            // Move the cursor to the point where the raycast hit.
            this.transform.position = hitInfo.point;

            // Rotate the cursor to hug the surface of the hologram.
            this.transform.rotation = Quaternion.FromToRotation(Vector3.up, hitInfo.normal);
        }
        else
        {
            // If the raycast did not hit a hologram, hide the cursor mesh.
            meshRenderer.enabled = false;
        }
    }
}
```

* 從檔案 **> 組建設定** 重建應用程式。
* 返回先前用來部署到 HoloLens 的 Visual Studio 方案。
* 出現提示時，請選取 [全部重載]。
* 按一下 [ **Debug-> 啟動但不進行調試]，** 或按 **Ctrl + F5**。
* 現在看看場景，並注意游標如何與物件的形狀互動。

## <a name="chapter-3---gestures"></a>第3章-手勢

>[!VIDEO https://www.youtube.com/embed/kW3ThJ2MbvQ]

在本章中，我們將新增 [手勢](../../../design/gaze-and-commit.md#composite-gestures)的支援。 當使用者選取紙球體時，我們會使用 Unity 的物理引擎來開啟重力來使球體落在心。

### <a name="objectives"></a>目標

* 使用選取手勢來控制您的全像影像。

### <a name="instructions"></a>指示

我們將從建立腳本開始，然後偵測到選取的手勢。

* 在 [ **腳本** ] 資料夾中，建立名為 **GazeGestureManager** 的腳本。
* 將 **GazeGestureManager** 腳本拖曳至階層中的 **OrigamiCollection** 物件。
* 在 Visual Studio 中開啟 **GazeGestureManager** 腳本，並加入下列程式碼：

```cs
using UnityEngine;
using UnityEngine.XR.WSA.Input;

public class GazeGestureManager : MonoBehaviour
{
    public static GazeGestureManager Instance { get; private set; }

    // Represents the hologram that is currently being gazed at.
    public GameObject FocusedObject { get; private set; }

    GestureRecognizer recognizer;

    // Use this for initialization
    void Awake()
    {
        Instance = this;

        // Set up a GestureRecognizer to detect Select gestures.
        recognizer = new GestureRecognizer();
        recognizer.Tapped += (args) =>
        {
            // Send an OnSelect message to the focused object and its ancestors.
            if (FocusedObject != null)
            {
                FocusedObject.SendMessageUpwards("OnSelect", SendMessageOptions.DontRequireReceiver);
            }
        };
        recognizer.StartCapturingGestures();
    }

    // Update is called once per frame
    void Update()
    {
        // Figure out which hologram is focused this frame.
        GameObject oldFocusObject = FocusedObject;

        // Do a raycast into the world based on the user's
        // head position and orientation.
        var headPosition = Camera.main.transform.position;
        var gazeDirection = Camera.main.transform.forward;

        RaycastHit hitInfo;
        if (Physics.Raycast(headPosition, gazeDirection, out hitInfo))
        {
            // If the raycast hit a hologram, use that as the focused object.
            FocusedObject = hitInfo.collider.gameObject;
        }
        else
        {
            // If the raycast did not hit a hologram, clear the focused object.
            FocusedObject = null;
        }

        // If the focused object changed this frame,
        // start detecting fresh gestures again.
        if (FocusedObject != oldFocusObject)
        {
            recognizer.CancelGestures();
            recognizer.StartCapturingGestures();
        }
    }
}
```

* 在腳本資料夾中建立另一個腳本，這次名為 **SphereCommands**。
* 展開階層視圖中的 [ **OrigamiCollection** ] 物件。
* 將 **SphereCommands** 腳本拖曳至 [階層] 面板中的 **Sphere1** 物件。
* 將 **SphereCommands** 腳本拖曳至 [階層] 面板中的 **Sphere2** 物件。
* 在 Visual Studio 中開啟腳本進行編輯，並將預設程式碼取代為下列程式碼：

```cs
using UnityEngine;

public class SphereCommands : MonoBehaviour
{
    // Called by GazeGestureManager when the user performs a Select gesture
    void OnSelect()
    {
        // If the sphere has no Rigidbody component, add one to enable physics.
        if (!this.GetComponent<Rigidbody>())
        {
            var rigidbody = this.gameObject.AddComponent<Rigidbody>();
            rigidbody.collisionDetectionMode = CollisionDetectionMode.Continuous;
        }
    }
}
```

* 匯出、建立應用程式，並將其部署到 HoloLens。
* 查看其中一個球體。
* 執行 [選取手勢]，並監看下圖上的球體。

## <a name="chapter-4---voice"></a>第4章-語音

>[!VIDEO https://www.youtube.com/embed/1-Aq0VVtHM8]

在本章中，我們將新增兩個 [語音命令](../../../design/voice-input.md)的支援：「重設世界」以將捨棄的球體傳回其原始位置，以及「捨棄球體」以使球體落在外。

### <a name="objectives"></a>目標

* 新增一律在背景中接聽的語音命令。
* 建立可回應語音命令的全像影像。

### <a name="instructions"></a>指示

* 在 [ **腳本** ] 資料夾中，建立名為 **SpeechManager** 的腳本。
* 將 **SpeechManager** 腳本拖曳至階層中的 **OrigamiCollection** 物件
* 在 Visual Studio 中開啟 **SpeechManager** 腳本。
* 將此程式碼複製並貼到 **SpeechManager** 中，並 **全部儲存**：

```cs
using System.Collections.Generic;
using System.Linq;
using UnityEngine;
using UnityEngine.Windows.Speech;

public class SpeechManager : MonoBehaviour
{
    KeywordRecognizer keywordRecognizer = null;
    Dictionary<string, System.Action> keywords = new Dictionary<string, System.Action>();

    // Use this for initialization
    void Start()
    {
        keywords.Add("Reset world", () =>
        {
            // Call the OnReset method on every descendant object.
            this.BroadcastMessage("OnReset");
        });

        keywords.Add("Drop Sphere", () =>
        {
            var focusObject = GazeGestureManager.Instance.FocusedObject;
            if (focusObject != null)
            {
                // Call the OnDrop method on just the focused object.
                focusObject.SendMessage("OnDrop", SendMessageOptions.DontRequireReceiver);
            }
        });

        // Tell the KeywordRecognizer about our keywords.
        keywordRecognizer = new KeywordRecognizer(keywords.Keys.ToArray());

        // Register a callback for the KeywordRecognizer and start recognizing!
        keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
        keywordRecognizer.Start();
    }

    private void KeywordRecognizer_OnPhraseRecognized(PhraseRecognizedEventArgs args)
    {
        System.Action keywordAction;
        if (keywords.TryGetValue(args.text, out keywordAction))
        {
            keywordAction.Invoke();
        }
    }
}
```

* 在 Visual Studio 中開啟 **SphereCommands** 腳本。
* 更新腳本以進行讀取，如下所示：

```cs
using UnityEngine;

public class SphereCommands : MonoBehaviour
{
    Vector3 originalPosition;

    // Use this for initialization
    void Start()
    {
        // Grab the original local position of the sphere when the app starts.
        originalPosition = this.transform.localPosition;
    }

    // Called by GazeGestureManager when the user performs a Select gesture
    void OnSelect()
    {
        // If the sphere has no Rigidbody component, add one to enable physics.
        if (!this.GetComponent<Rigidbody>())
        {
            var rigidbody = this.gameObject.AddComponent<Rigidbody>();
            rigidbody.collisionDetectionMode = CollisionDetectionMode.Continuous;
        }
    }

    // Called by SpeechManager when the user says the "Reset world" command
    void OnReset()
    {
        // If the sphere has a Rigidbody component, remove it to disable physics.
        var rigidbody = this.GetComponent<Rigidbody>();
        if (rigidbody != null)
        {
            rigidbody.isKinematic = true;
            Destroy(rigidbody);
        }

        // Put the sphere back into its original local position.
        this.transform.localPosition = originalPosition;
    }

    // Called by SpeechManager when the user says the "Drop sphere" command
    void OnDrop()
    {
        // Just do the same logic as a Select gesture.
        OnSelect();
    }
}
```

* 匯出、建立應用程式，並將其部署到 HoloLens。
* 查看其中一個球體，然後說出「**捨棄球體**」。
* 說「**重設世界**」將它們帶回其初始位置。

## <a name="chapter-5---spatial-sound"></a>第5章-空間音效

>[!VIDEO https://www.youtube.com/embed/Aj4de5Ncbfo]

在本章中，我們會將音樂新增至應用程式，然後觸發對某些動作的音效效果。 我們會使用 [空間音效](../../../design/spatial-sound.md) ，在3d 空間中提供音效的特定位置。

### <a name="objectives"></a>目標

* 聽聽您的全球全像投影。

### <a name="instructions"></a>指示

* 在 Unity 中，從頂端功能表中選取 [ **編輯] > 專案設定 > 音訊**
* 在右側的 [偵測器] 面板中，尋找 **空間定位器外掛程式** 設定，然後選取 **MS HRTF 空間定位器**。
* 從 [專案] 面板中的 [全像 **] 資料夾，** 將 [ **環境** ] 物件拖曳至 [階層] 面板中的 [ **OrigamiCollection** ] 物件。
* 選取 [ **OrigamiCollection** ]，然後在 [偵測器] 面板中尋找 **音訊來源** 元件。 變更這些屬性：
  * 檢查 **Spatialize** 屬性。
  * 檢查是否 **在喚醒時播放**。
  * 將滑杆向右拖曳，以將 **空間 Blend** 變更為 **3d** 。 當您移動滑杆時，值應該會從0變更為1。
  * 檢查 **迴圈** 屬性。
  * 展開 [ **3D 音效設定**]，然後輸入 **0.1** 作為 **Doppler 等級**。
  * 將 **Volume Rolloff** 設為 **對數 Rolloff**。
  * 將 **最大距離** 設定為 **20**。
* 在 [ **腳本** ] 資料夾中，建立名為 **SphereSounds** 的腳本。
* 將 **SphereSounds** 拖放到階層中的 **Sphere1** 和 **Sphere2** 物件。
* 在 Visual Studio 中開啟 **SphereSounds** ，更新下列程式碼並 **全部儲存**。

```cs
using UnityEngine;

public class SphereSounds : MonoBehaviour
{
    AudioSource impactAudioSource = null;
    AudioSource rollingAudioSource = null;

    bool rolling = false;

    void Start()
    {
        // Add an AudioSource component and set up some defaults
        impactAudioSource = gameObject.AddComponent<AudioSource>();
        impactAudioSource.playOnAwake = false;
        impactAudioSource.spatialize = true;
        impactAudioSource.spatialBlend = 1.0f;
        impactAudioSource.dopplerLevel = 0.0f;
        impactAudioSource.rolloffMode = AudioRolloffMode.Logarithmic;
        impactAudioSource.maxDistance = 20f;

        rollingAudioSource = gameObject.AddComponent<AudioSource>();
        rollingAudioSource.playOnAwake = false;
        rollingAudioSource.spatialize = true;
        rollingAudioSource.spatialBlend = 1.0f;
        rollingAudioSource.dopplerLevel = 0.0f;
        rollingAudioSource.rolloffMode = AudioRolloffMode.Logarithmic;
        rollingAudioSource.maxDistance = 20f;
        rollingAudioSource.loop = true;

        // Load the Sphere sounds from the Resources folder
        impactAudioSource.clip = Resources.Load<AudioClip>("Impact");
        rollingAudioSource.clip = Resources.Load<AudioClip>("Rolling");
    }

    // Occurs when this object starts colliding with another object
    void OnCollisionEnter(Collision collision)
    {
        // Play an impact sound if the sphere impacts strongly enough.
        if (collision.relativeVelocity.magnitude >= 0.1f)
        {
            impactAudioSource.Play();
        }
    }

    // Occurs each frame that this object continues to collide with another object
    void OnCollisionStay(Collision collision)
    {
        Rigidbody rigid = gameObject.GetComponent<Rigidbody>();

        // Play a rolling sound if the sphere is rolling fast enough.
        if (!rolling && rigid.velocity.magnitude >= 0.01f)
        {
            rolling = true;
            rollingAudioSource.Play();
        }
        // Stop the rolling sound if rolling slows down.
        else if (rolling && rigid.velocity.magnitude < 0.01f)
        {
            rolling = false;
            rollingAudioSource.Stop();
        }
    }

    // Occurs when this object stops colliding with another object
    void OnCollisionExit(Collision collision)
    {
        // Stop the rolling sound if the object falls off and stops colliding.
        if (rolling)
        {
            rolling = false;
            impactAudioSource.Stop();
            rollingAudioSource.Stop();
        }
    }
}
```

* 儲存腳本，並回到 Unity。
* 匯出、建立應用程式，並將其部署到 HoloLens。
* 從這個階段中更深入且更進一步的移動，然後輪流以聆聽音效的變化。

## <a name="chapter-6---spatial-mapping"></a>第6章-空間對應

>[!VIDEO https://www.youtube.com/embed/Pkt1_wNLLXY]

現在我們要使用 [空間對應](../../../design/spatial-mapping.md) ，將遊戲台放在真實世界中的真實物件上。

### <a name="objectives"></a>目標

* 將您的真實世界帶入虛擬世界。
* 將您的全像放在最重要的地方。

### <a name="instructions"></a>指示

* 在 Unity 中，按一下 [專案] 面板中的 [ **全息** 全像] 資料夾。
* 將 **空間對應** 資產拖曳至 **階層的根目錄。**
* 按一下階層中的 **空間對應** 物件。
* 在 [偵測 **器] 面板** 中，變更下列屬性：
  * 選取 [ **繪製視覺網格** ] 方塊。
  * 找出 **繪製材質** ，然後按一下右側的圓形。 在頂端的搜尋欄位中輸入「**線框**」。 按一下結果，然後關閉視窗。 當您這樣做時，繪製材質的值應該會設定為線框。
* 匯出、建立應用程式，並將其部署到 HoloLens。
* 當應用程式執行時，線框網格會與您的真實世界重迭。
* 觀賞輪流球體將如何落在此階段，並進入地面上！

現在，我們將示範如何將 OrigamiCollection 移至新位置：

* 在 [ **腳本** ] 資料夾中，建立名為 **TapToPlaceParent** 的腳本。
* 在階層 **中，展開**[ **OrigamiCollection** ]，然後選取 [ **階段** ] 物件。
* 將 **TapToPlaceParent** 腳本拖曳至階段物件。
* 在 Visual Studio 中開啟 **TapToPlaceParent** 腳本，並將其更新為下列內容：

```cs
using UnityEngine;

public class TapToPlaceParent : MonoBehaviour
{
    bool placing = false;

    // Called by GazeGestureManager when the user performs a Select gesture
    void OnSelect()
    {
        // On each Select gesture, toggle whether the user is in placing mode.
        placing = !placing;

        // If the user is in placing mode, display the spatial mapping mesh.
        if (placing)
        {
            SpatialMapping.Instance.DrawVisualMeshes = true;
        }
        // If the user is not in placing mode, hide the spatial mapping mesh.
        else
        {
            SpatialMapping.Instance.DrawVisualMeshes = false;
        }
    }

    // Update is called once per frame
    void Update()
    {
        // If the user is in placing mode,
        // update the placement to match the user's gaze.

        if (placing)
        {
            // Do a raycast into the world that will only hit the Spatial Mapping mesh.
            var headPosition = Camera.main.transform.position;
            var gazeDirection = Camera.main.transform.forward;

            RaycastHit hitInfo;
            if (Physics.Raycast(headPosition, gazeDirection, out hitInfo,
                30.0f, SpatialMapping.PhysicsRaycastMask))
            {
                // Move this object's parent object to
                // where the raycast hit the Spatial Mapping mesh.
                this.transform.parent.position = hitInfo.point;

                // Rotate this object's parent object to face the user.
                Quaternion toQuat = Camera.main.transform.localRotation;
                toQuat.x = 0;
                toQuat.z = 0;
                this.transform.parent.rotation = toQuat;
            }
        }
    }
}
```

* 匯出、建立及部署應用程式。
* 現在，您應該可以使用 Select 手勢，然後移至新位置，然後再使用 [選取手勢]，將遊戲放在特定的位置撥雲見日。

## <a name="chapter-7---holographic-fun"></a>第7章-全像愉快

### <a name="objectives"></a>目標

* 顯示全像 underworld 的進入。

### <a name="instructions"></a>指示

現在，我們將示範如何發掘全像 underworld：

* 從 [專案] 面板中 **的 [全** 像全像] 資料夾：
  * 將 **Underworld** 拖曳到階層中，以成為 **OrigamiCollection** 的子系。
* 在 [ **腳本** ] 資料夾中，建立名為 **HitTarget** 的腳本。
* **在階層中，展開**[ **OrigamiCollection**]。
* 展開 [ **階段** ] 物件，然後選取 [ **目標** 物件] (藍色風扇) 。
* 將 **HitTarget** 腳本拖曳至 **目標** 物件。
* 在 Visual Studio 中開啟 **HitTarget** 腳本，並將其更新為下列內容：

```cs
using UnityEngine;

public class HitTarget : MonoBehaviour
{
    // These public fields become settable properties in the Unity editor.
    public GameObject underworld;
    public GameObject objectToHide;

    // Occurs when this object starts colliding with another object
    void OnCollisionEnter(Collision collision)
    {
        // Hide the stage and show the underworld.
        objectToHide.SetActive(false);
        underworld.SetActive(true);

        // Disable Spatial Mapping to let the spheres enter the underworld.
        SpatialMapping.Instance.MappingEnabled = false;
    }
}
```

* 在 Unity 中，選取 **目標** 物件。
* 兩個公用屬性現在會顯示在 **點擊目標** 元件中，而且必須參考場景中的物件：
  * 將 [ **Underworld** ] 從 [階層 **] 面板拖曳** 至 [**點擊目標**] 元件上的 **Underworld** 屬性。
  * 將 [階層]**面板中的 [** **階段**] 拖曳至 **物件，以隱藏****點擊目標** 元件上的屬性。
* 匯出、建立及部署應用程式。
* 將折紙集合放在樓層，然後使用 Select 手勢來放置球體。
* 當球體達到目標 (藍色風扇) 時，將會發生爆炸。 將會隱藏此集合，並顯示 underworld 的孔洞。

## <a name="the-end"></a>結束

這就是本教學課程的結尾！

您已了解︰

* 如何在 Unity 中建立全像內建應用程式。
* 如何利用注視、手勢、語音、音效和空間對應。
* 如何使用 Visual Studio 來建立和部署應用程式。

您現在已準備好開始建立自己的全像攝影體驗！

## <a name="see-also"></a>另請參閱

* [MR Basics 101E：使用模擬器完成專案](holograms-101e.md)
* [目光](../../../design/gaze-and-commit.md)
* [頭部目光和行動](../../../design/gaze-and-commit.md)
* [語音輸入](../../../design/voice-input.md)
* [空間音效](../../../design/spatial-sound.md)
* [空間對應](../../../design/spatial-mapping.md)