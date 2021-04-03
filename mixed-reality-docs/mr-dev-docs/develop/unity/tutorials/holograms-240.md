---
title: HoloLens (第1代) 共用 240-多個 HoloLens 裝置
description: 遵循此程式碼逐步解說，使用 Unity、Visual Studio 和 HoloLens 來學習共用全像影像的詳細資料。
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit、mixedrealitytoolkit、mixedrealitytoolkit-unity、共用、網路、學術、教學課程、HoloLens、混合現實學術、unity、混合現實耳機、windows Mixed reality 耳機、虛擬實境耳機、Windows 10
ms.openlocfilehash: 446f82558781e47b5381ee3f59af70953954ad2a
ms.sourcegitcommit: 3236abcba27335fe3d52e38423d2b265ca883355
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2021
ms.locfileid: "106269914"
---
# <a name="hololens-1st-gen-sharing-240-multiple-hololens-devices"></a>HoloLens (第1代) 共用240：多個 HoloLens 裝置

>[!IMPORTANT]
>混合的現實學術教學課程是以 HoloLens (第一代) 、Unity 2017 和混合現實的沉浸式耳機來設計的。  因此，對於仍在尋找這些裝置開發指引的開發人員而言，我們覺得這些教學課程很重要。 這些教學課程 **_不_** 會使用最新的工具組或互動進行 HoloLens 2，而且可能與較新版本的 Unity 不相容。  系統會保留這些資訊，以繼續在支援的裝置上運作。 已針對 HoloLens 2 公佈[一系列新的教學課程](mrlearning-base.md)。

當我們在空間中移動時，我們會在世界各地提供全像投影。 HoloLens 會使用不同的 [座標系統](../../../design/coordinate-systems.md) 來追蹤物件的位置和方向，以就地保存全像影像。 當我們在裝置之間共用這些座標系統時，我們可以建立共用的體驗，讓我們參與共用的全像世界。

在此教學課程中，我們將：

* 設定共用體驗的網路。
* 跨 HoloLens 裝置共用全像影像。
* 探索共用全像全球的其他人。
* 建立可讓您以其他播放程式為目標的共用互動式體驗，並在其上啟動炮彈！

## <a name="device-support"></a>裝置支援

<table>
<tr>
<th>課程</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">沉浸式頭戴裝置</a></th>
</tr><tr>
<td>MR Sharing 240：多個 HoloLens 裝置</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a>在您開始使用 Intune 之前

### <a name="prerequisites"></a>必要條件

* 使用隨網際網路存取安裝的正確 [工具](../../../develop/install-the-tools.md) 設定的 Windows 10 電腦。
* 至少有兩個 HoloLens 裝置 [設定用於開發](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)。

### <a name="project-files"></a>專案檔

* 下載專案 [所需的](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-240-SharedHolograms.zip) 檔案。 需要 Unity 2017.2 或更新版本。
  * 如果您仍然需要 Unity 5.6 支援，請使用 [此版本](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-240.zip)。
  * 如果您仍然需要 Unity 5.5 支援，請使用 [此版本](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-240.zip)。
  * 如果您仍然需要 Unity 5.4 支援，請使用 [此版本](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-240.zip)。
* 取消將檔案封存到您的桌面或其他易於觸及的位置。 將資料夾名稱保留為 **SharedHolograms**。

>[!NOTE]
>如果您想要在下載之前查看原始程式碼， [可在 GitHub 上](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-240-SharedHolograms)取得。

## <a name="chapter-1---holo-world"></a>第1章-Hololens World

>[!VIDEO https://www.youtube.com/embed/c7qHYYW8rxQ]

在本章中，我們將設定第一個 Unity 專案，並逐步執行組建和部署程式。

### <a name="objectives"></a>目標

* 設定 Unity 以開發全息型應用程式。
* 查看您的全像影像！

### <a name="instructions"></a>指示

* 啟動 Unity。
* 選取 [開啟]  。
* 輸入位置作為您先前 unarchived 的 **SharedHolograms** 資料夾。
* 選取 [ **專案名稱** ]，然後按一下 [ **選取資料夾**]。
* **在階層中，以** 滑鼠右鍵按一下 **主要攝影機**，然後選取 [**刪除**]。
* 在 [ **HoloToolkit-共用-240/Prefabs/攝影機** ] 資料夾中，尋找 **主要相機** 預製專案。
* 將 [**主要攝影機**] 拖放到階層 **中。**
* 在階層 **中，按一下**[ **建立** ] 並 **建立空白**。
* 以滑鼠右鍵按一下新的 **GameObject** ，然後選取 [ **重新命名**]。
* 將 GameObject 重新命名為 **HologramCollection**。
* 選取階層中的 **HologramCollection** 物件 **。**
* 在偵測 **器** 中，將 **轉換位置** 設定為： **X：0，Y：-0.25，Z： 2**。
* 在 [**專案] 面板** 的 [全像全像 **] 資料夾中**，尋找 **EnergyHub** 資產。
* 將 **EnergyHub** 物件從 **專案面板** 拖放到階層中， **做為** **HologramCollection 的子** 系。
* 選取 [檔案 **> 另存場景為**...]
* 命名場景 **SharedHolograms** ，然後按一下 [ **儲存**]。
* 按下 Unity 中的 [ **播放** ] 按鈕，以預覽您的全像影像。
* 按第二次 [ **播放** ] 以停止預覽模式。

**將專案從 Unity 匯出至 Visual Studio**

* 在 Unity 中，選取 [ **File > Build Settings**]。
* 按一下 [ **新增開啟場景** ] 以加入場景。
* 在 [**平臺**] 清單中選取 **通用 Windows 平臺**，然後按一下 [**切換平臺**]。
* 將 **SDK** 設定為 **通用 10**。
* 將 **目標裝置** 設定為 **HoloLens** ，並將 **UWP 組建類型** 設定為 **D3D**。
* 檢查 **Unity c # 專案**。
* 按一下 [建置]。
* 在出現的 [檔案瀏覽器] 視窗中，建立名為 "App" 的 **新資料夾** 。
* 按一下 **應用程式** 資料夾。
* 按下 [ **選取資料夾**]。
* 當 Unity 完成時，將會出現檔案總管視窗。
* 開啟 **應用程式** 資料夾。
* 開啟 **SharedHolograms** 以啟動 Visual Studio。
* 使用 Visual Studio 中的頂端工具列，將目標從 Debug 變更為 **Release** ，以及從 ARM 變更為 **X86**。
* 按一下 [本機電腦] 旁的下拉箭號，然後選取 [ **遠端裝置**]。
    * 將 **位址** 設定為 HoloLens 的名稱或 IP 位址。 如果您不知道您的裝置 IP 位址，請查看 [ **設定] > 網路 & 網際網路 > [Advanced Options** ] 或 [問 Cortana **] 嗨 Cortana，我的 IP 位址為何？**
    * 將 [ **驗證模式]** 設定為 [ **通用**]。
    * 按一下 [**選取**]
* 按一下 [ **Debug > 啟動但不進行調試** ]，或按 **Ctrl + F5**。 如果這是您第一次部署至您的裝置，您必須將 [它與 Visual Studio 配對](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#pairing-your-device)。
* 放在 HoloLens 上，找出 EnergyHub 的全息圖。

## <a name="chapter-2---interaction"></a>第2章-互動

>[!VIDEO https://www.youtube.com/embed/W60xG15a8gc]

在本章中，我們將會與我們的全像投影互動。 首先，我們會新增一個資料指標來視覺化我們的 [注視](../../../design/gaze-and-commit.md)。 接著，我們將新增 [手勢](../../../design/gaze-and-commit.md#composite-gestures) ，並使用我們的手將全息的空間放在空間中。

### <a name="objectives"></a>目標

* 使用「注視輸入」來控制資料指標。
* 使用手勢輸入與全像影像互動。

### <a name="instructions"></a>指示

**目光**

* 在 [階層] **面板** 中，選取 [ **HologramCollection** ] 物件。
* 在 [偵測 **器] 面板** 中，按一下 [ **新增元件** ] 按鈕。
* 在功能表中，于 [搜尋] 方塊中輸入 **注視 Manager**。 選取搜尋結果。
* 在 [ **HoloToolkit-Sharing-240\Prefabs\Input** ] 資料夾中，尋找資料 **指標** 資產。
* 將資料 **指標** 資產拖放到階層 **上。**

**手勢**

* 在 [階層] **面板** 中，選取 [ **HologramCollection** ] 物件。
* 按一下 [ **新增元件** ]，然後在 [搜尋] 欄位中輸入 **手勢管理員** 。 選取搜尋結果。
* 在 [階層] **面板** 中，展開 [ **HologramCollection**]。
* 選取子 **EnergyHub** 物件。
* 在 [偵測 **器] 面板** 中，按一下 [ **新增元件** ] 按鈕。
* 在功能表中，輸入搜尋方塊全息圖 **放置**。 選取搜尋結果。
* 選取 [檔案] **> 儲存場景** 來儲存場景。

**部署及享用**

* 使用上一章的指示，建立並部署至您的 HoloLens。
* 在您的 HoloLens 上啟動應用程式後，請移至您的開端，並留意 EnergyHub 接在您注視的方式。
* 請注意，當您注視全像全像投影時，游標會如何出現，並在不撥雲見日于全像點時變更點燈。
* 執行點一下來放置全像。 目前，在我們的專案中，您只可以在 (重新部署時放置全像) ，然後再試一次。

## <a name="chapter-3---shared-coordinates"></a>第3章-共用座標

>[!VIDEO https://www.youtube.com/embed/Ey8yBgWiqtg]

您可以輕鬆查看全像影像，並與之互動，但讓我們繼續進行。 我們會設定我們的第一個共用體驗，每個人都可以一起查看。

### <a name="objectives"></a>目標

* 設定共用體驗的網路。
* 建立共同的參考點。
* 跨裝置共用座標系統。
* 每個人都看到相同的全息圖！

>[!NOTE]
>您必須為應用程式宣告 **InternetClientServer** 和 **PrivateNetworkClientServer** 功能，才能連接到共用伺服器。 這是針對您已在全像240的電腦上完成的，但請記住您自己的專案。

>1. 在 Unity 編輯器中，流覽至 [> Player 編輯 > 專案設定]，移至播放機設定
>2. 按一下 [Windows 市存放區] 索引標籤
>3. 在 [發佈設定 > 功能] 區段中，檢查 **InternetClientServer** 功能和 **PrivateNetworkClientServer** 功能

### <a name="instructions"></a>指示

* 在 [ **專案] 面板** 中，流覽至 [ **HoloToolkit-Sharing-240\Prefabs\Sharing** ] 資料夾。
* 將 **共用** 預製專案拖放到 [階層] **面板** 中。

接下來我們需要啟動共用服務。 只有 **一部電腦** 在共用體驗中需要執行這個步驟。

* 在 Unity 中-在最上層功能表中，選取 [ **HoloToolkit-共用-240] 功能表**。
* 在下拉式清單中選取 [ **啟動共用服務** ] 專案。
* 核取 [ **私人網路** ] 選項，然後在出現防火牆提示時按一下 [ **允許存取** ]。
* 記下 [共用服務主控台] 視窗中顯示的 IPv4 位址。 這與執行服務的電腦是相同的 IP。

遵循將加入共用體驗的 **所有電腦** 上的其他指示。

* **在階層中，選取****共用** 物件。
* 在偵測 **器** 的 **共用階段** 元件上，將 **伺服器位址** 從 ' localhost ' 變更為執行 SharingService.exe 之電腦的 IPv4 位址。
* **在階層中選取**[ **HologramCollection** ] 物件。
* 在 [偵測 **器** ] 中，按一下 [ **新增元件** ] 按鈕。
* 在搜尋方塊中，輸入匯 **入匯出錨點管理員**。 選取搜尋結果。
* 在 [ **專案] 面板** 中，流覽至 [ **腳本** ] 資料夾。
* 按兩下 **HologramPlacement** 腳本，在 Visual Studio 中開啟它。
* 使用以下列程式碼取代內容。

```cs
using UnityEngine;
using System.Collections.Generic;
using UnityEngine.Windows.Speech;
using Academy.HoloToolkit.Unity;
using Academy.HoloToolkit.Sharing;

public class HologramPlacement : Singleton<HologramPlacement>
{
    /// <summary>
    /// Tracks if we have been sent a transform for the anchor model.
    /// The anchor model is rendered relative to the actual anchor.
    /// </summary>
    public bool GotTransform { get; private set; }

    private bool animationPlayed = false;

    void Start()
    {
        // We care about getting updates for the anchor transform.
        CustomMessages.Instance.MessageHandlers[CustomMessages.TestMessageID.StageTransform] = this.OnStageTransform;

        // And when a new user join we will send the anchor transform we have.
        SharingSessionTracker.Instance.SessionJoined += Instance_SessionJoined;
    }

    /// <summary>
    /// When a new user joins we want to send them the relative transform for the anchor if we have it.
    /// </summary>
    /// <param name="sender"></param>
    /// <param name="e"></param>
    private void Instance_SessionJoined(object sender, SharingSessionTracker.SessionJoinedEventArgs e)
    {
        if (GotTransform)
        {
            CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
        }
    }

    void Update()
    {
        if (GotTransform)
        {
            if (ImportExportAnchorManager.Instance.AnchorEstablished &&
                animationPlayed == false)
            {
                // This triggers the animation sequence for the anchor model and 
                // puts the cool materials on the model.
                GetComponent<EnergyHubBase>().SendMessage("OnSelect");
                animationPlayed = true;
            }
        }
        else
        {
            transform.position = Vector3.Lerp(transform.position, ProposeTransformPosition(), 0.2f);
        }
    }

    Vector3 ProposeTransformPosition()
    {
        // Put the anchor 2m in front of the user.
        Vector3 retval = Camera.main.transform.position + Camera.main.transform.forward * 2;

        return retval;
    }

    public void OnSelect()
    {
        // Note that we have a transform.
        GotTransform = true;

        // And send it to our friends.
        CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
    }

    /// <summary>
    /// When a remote system has a transform for us, we'll get it here.
    /// </summary>
    /// <param name="msg"></param>
    void OnStageTransform(NetworkInMessage msg)
    {
        // We read the user ID but we don't use it here.
        msg.ReadInt64();

        transform.localPosition = CustomMessages.Instance.ReadVector3(msg);
        transform.localRotation = CustomMessages.Instance.ReadQuaternion(msg);

        // The first time, we'll want to send the message to the anchor to do its animation and
        // swap its materials.
        if (GotTransform == false)
        {
            GetComponent<EnergyHubBase>().SendMessage("OnSelect");
        }

        GotTransform = true;
    }

    public void ResetStage()
    {
        // We'll use this later.
    }
}
```

* 回到 Unity，在 [階層]**面板** 中選取 **HologramCollection** 。
* 在 [偵測 **器] 面板** 中，按一下 [ **新增元件** ] 按鈕。
* 在功能表中，輸入搜尋 box **應用程式狀態管理員**。 選取搜尋結果。

**部署及享用**

* 建立 HoloLens 裝置的專案。
* 指定一個 HoloLens 以先部署到其中。 您必須等待錨點上傳至服務，才能放置 EnergyHub (這可能需要大約30-60 秒的時間) 。 在上傳完成之前，您的分流手勢將會被忽略。
* 放置 EnergyHub 之後，其位置會上傳至服務，然後您就可以部署到所有其他 HoloLens 裝置。
* 當新的 HoloLens 首次加入會話時，該裝置上的 EnergyHub 位置可能不正確。 不過，一旦從服務下載錨點和 EnergyHub 位置，EnergyHub 應該會跳至新的共用位置。 如果這不是在 ~ 30-60 秒內發生，請在設定錨點以收集更多環境線索時，逐步解說原始 HoloLens 的所在位置。 如果位置仍未鎖定，請重新部署至裝置。
* 當裝置都已就緒且正在執行應用程式時，請尋找 EnergyHub。 您是否同意全像全像全像全像全像全像全庫存的位置，以及文字面向的方向？

## <a name="chapter-4---discovery"></a>第4章-探索

>[!VIDEO https://www.youtube.com/embed/5NxJWMV4BP8]

每個人現在都可以看到相同的全息圖！ 現在讓我們看看其他人連線到我們分享的全像全球。 在本章中，我們將在相同的共用會話中抓取所有其他 HoloLens 裝置的前端位置和旋轉。

### <a name="objectives"></a>目標

* 在我們的共用體驗中找到彼此。
* 選擇並分享玩家頭像。
* 將玩家頭像附加到每個人的標題旁邊。

### <a name="instructions"></a>指示

* 在 [ **專案] 面板** 中，流覽至 [ **全息** 全像] 資料夾。
* 將 **PlayerAvatarStore** 拖放到階層中 **。**
* 在 [ **專案] 面板** 中，流覽至 [ **腳本** ] 資料夾。
* 按兩下 **AvatarSelector** 腳本，在 Visual Studio 中開啟它。
* 使用以下列程式碼取代內容。

```cs
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Script to handle the user selecting the avatar.
/// </summary>
public class AvatarSelector : MonoBehaviour
{
    /// <summary>
    /// This is the index set by the PlayerAvatarStore for the avatar.
    /// </summary>
    public int AvatarIndex { get; set; }

    /// <summary>
    /// Called when the user is gazing at this avatar and air-taps it.
    /// This sends the user's selection to the rest of the devices in the experience.
    /// </summary>
    void OnSelect()
    {
        PlayerAvatarStore.Instance.DismissAvatarPicker();

        LocalPlayerManager.Instance.SetUserAvatar(AvatarIndex);
    }

    void Start()
    {
        // Add Billboard component so the avatar always faces the user.
        Billboard billboard = gameObject.GetComponent<Billboard>();
        if (billboard == null)
        {
            billboard = gameObject.AddComponent<Billboard>();
        }

        // Lock rotation along the Y axis.
        billboard.PivotAxis = PivotAxis.Y;
    }
}
```

* **在階層中選取**[ **HologramCollection** ] 物件。
* 在 [偵測 **器** ] 中按一下 [ **新增元件**]。
* 在 [搜尋] 方塊中，輸入「 **本機播放機管理員**」。 選取搜尋結果。
* **在階層中選取**[ **HologramCollection** ] 物件。
* 在 [偵測 **器** ] 中按一下 [ **新增元件**]。
* 在 [搜尋] 方塊中，輸入 **Remote Player Manager**。 選取搜尋結果。
* 在 Visual Studio 中開啟 **HologramPlacement** 腳本。
* 使用以下列程式碼取代內容。

```cs
using UnityEngine;
using System.Collections.Generic;
using UnityEngine.Windows.Speech;
using Academy.HoloToolkit.Unity;
using Academy.HoloToolkit.Sharing;

public class HologramPlacement : Singleton<HologramPlacement>
{
    /// <summary>
    /// Tracks if we have been sent a transform for the model.
    /// The model is rendered relative to the actual anchor.
    /// </summary>
    public bool GotTransform { get; private set; }

    /// <summary>
    /// When the experience starts, we disable all of the rendering of the model.
    /// </summary>
    List<MeshRenderer> disabledRenderers = new List<MeshRenderer>();

    void Start()
    {
        // When we first start, we need to disable the model to avoid it obstructing the user picking a hat.
        DisableModel();

        // We care about getting updates for the model transform.
        CustomMessages.Instance.MessageHandlers[CustomMessages.TestMessageID.StageTransform] = this.OnStageTransform;

        // And when a new user join we will send the model transform we have.
        SharingSessionTracker.Instance.SessionJoined += Instance_SessionJoined;
    }

    /// <summary>
    /// When a new user joins we want to send them the relative transform for the model if we have it.
    /// </summary>
    /// <param name="sender"></param>
    /// <param name="e"></param>
    private void Instance_SessionJoined(object sender, SharingSessionTracker.SessionJoinedEventArgs e)
    {
        if (GotTransform)
        {
            CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
        }
    }

    /// <summary>
    /// Turns off all renderers for the model.
    /// </summary>
    void DisableModel()
    {
        foreach (MeshRenderer renderer in gameObject.GetComponentsInChildren<MeshRenderer>())
        {
            if (renderer.enabled)
            {
                renderer.enabled = false;
                disabledRenderers.Add(renderer);
            }
        }

        foreach (MeshCollider collider in gameObject.GetComponentsInChildren<MeshCollider>())
        {
            collider.enabled = false;
        }
    }

    /// <summary>
    /// Turns on all renderers that were disabled.
    /// </summary>
    void EnableModel()
    {
        foreach (MeshRenderer renderer in disabledRenderers)
        {
            renderer.enabled = true;
        }

        foreach (MeshCollider collider in gameObject.GetComponentsInChildren<MeshCollider>())
        {
            collider.enabled = true;
        }

        disabledRenderers.Clear();
    }


    void Update()
    {
        // Wait till users pick an avatar to enable renderers.
        if (disabledRenderers.Count > 0)
        {
            if (!PlayerAvatarStore.Instance.PickerActive &&
            ImportExportAnchorManager.Instance.AnchorEstablished)
            {
                // After which we want to start rendering.
                EnableModel();

                // And if we've already been sent the relative transform, we will use it.
                if (GotTransform)
                {
                    // This triggers the animation sequence for the model and
                    // puts the cool materials on the model.
                    GetComponent<EnergyHubBase>().SendMessage("OnSelect");
                }
            }
        }
        else if (GotTransform == false)
        {
            transform.position = Vector3.Lerp(transform.position, ProposeTransformPosition(), 0.2f);
        }
    }

    Vector3 ProposeTransformPosition()
    {
        // Put the model 2m in front of the user.
        Vector3 retval = Camera.main.transform.position + Camera.main.transform.forward * 2;

        return retval;
    }

    public void OnSelect()
    {
        // Note that we have a transform.
        GotTransform = true;

        // And send it to our friends.
        CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
    }

    /// <summary>
    /// When a remote system has a transform for us, we'll get it here.
    /// </summary>
    /// <param name="msg"></param>
    void OnStageTransform(NetworkInMessage msg)
    {
        // We read the user ID but we don't use it here.
        msg.ReadInt64();

        transform.localPosition = CustomMessages.Instance.ReadVector3(msg);
        transform.localRotation = CustomMessages.Instance.ReadQuaternion(msg);

        // The first time, we'll want to send the message to the model to do its animation and
        // swap its materials.
        if (disabledRenderers.Count == 0 && GotTransform == false)
        {
            GetComponent<EnergyHubBase>().SendMessage("OnSelect");
        }

        GotTransform = true;
    }

    public void ResetStage()
    {
        // We'll use this later.
    }
}
```

* 在 Visual Studio 中開啟 **AppStateManager** 腳本。
* 使用以下列程式碼取代內容。

```cs
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Keeps track of the current state of the experience.
/// </summary>
public class AppStateManager : Singleton<AppStateManager>
{
    /// <summary>
    /// Enum to track progress through the experience.
    /// </summary>
    public enum AppState
    {
        Starting = 0,
        WaitingForAnchor,
        WaitingForStageTransform,
        PickingAvatar,
        Ready
    }

    /// <summary>
    /// Tracks the current state in the experience.
    /// </summary>
    public AppState CurrentAppState { get; set; }

    void Start()
    {
        // We start in the 'picking avatar' mode.
        CurrentAppState = AppState.PickingAvatar;

        // We start by showing the avatar picker.
        PlayerAvatarStore.Instance.SpawnAvatarPicker();
    }

    void Update()
    {
        switch (CurrentAppState)
        {
            case AppState.PickingAvatar:
                // Avatar picking is done when the avatar picker has been dismissed.
                if (PlayerAvatarStore.Instance.PickerActive == false)
                {
                    CurrentAppState = AppState.WaitingForAnchor;
                }
                break;
            case AppState.WaitingForAnchor:
                if (ImportExportAnchorManager.Instance.AnchorEstablished)
                {
                    CurrentAppState = AppState.WaitingForStageTransform;
                    GestureManager.Instance.OverrideFocusedObject = HologramPlacement.Instance.gameObject;
                }
                break;
            case AppState.WaitingForStageTransform:
                // Now if we have the stage transform we are ready to go.
                if (HologramPlacement.Instance.GotTransform)
                {
                    CurrentAppState = AppState.Ready;
                    GestureManager.Instance.OverrideFocusedObject = null;
                }
                break;
        }
    }
}
```

**部署及享用**

* 建立專案，並將其部署到您的 HoloLens 裝置。
* 當您聽到 ping 音效時，請尋找 [顯示圖片] 的 [選取專案] 功能表，並選取具有 [點一下] 手勢的圖片。
* 如果您不想查看任何全息體，則當 HoloLens 與服務進行通訊時，游標周圍的點燈將會變成不同的色彩：初始化 (深紫色) 、將錨點下載 (綠色) 、匯入/匯出位置資料 (黃色) 、將錨點上傳 (藍色) 。 如果游標周圍的點燈是預設色彩 (淺紫色) ，您就可以開始與會話中的其他玩家互動！
* 查看連接到您空間的其他人-將會有一位全像的機器人，並模擬其頭部運動！

## <a name="chapter-5---placement"></a>第5章-放置

>[!VIDEO https://www.youtube.com/embed/afFTwHQIw0s]

在本章中，我們會讓錨點放在實際的表面上。 我們將使用共用座標，將該錨點放在所有連線到共用體驗的人之間的中間點。

### <a name="objectives"></a>目標

* 根據玩家的標頭位置，在空間對應網格上放置全像影像。

### <a name="instructions"></a>指示

* 在 [ **專案] 面板** 中，流覽至 [ **全息** 全像] 資料夾。
* 將 **CustomSpatialMapping** 預製專案拖放到階層上 **。**
* 在 [ **專案] 面板** 中，流覽至 [ **腳本** ] 資料夾。
* 按兩下 **AppStateManager** 腳本，在 Visual Studio 中開啟它。
* 使用以下列程式碼取代內容。

```cs
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Keeps track of the current state of the experience.
/// </summary>
public class AppStateManager : Singleton<AppStateManager>
{
    /// <summary>
    /// Enum to track progress through the experience.
    /// </summary>
    public enum AppState
    {
        Starting = 0,
        PickingAvatar,
        WaitingForAnchor,
        WaitingForStageTransform,
        Ready
    }

    // The object to call to make a projectile.
    GameObject shootHandler = null;

    /// <summary>
    /// Tracks the current state in the experience.
    /// </summary>
    public AppState CurrentAppState { get; set; }

    void Start()
    {
        // The shootHandler shoots projectiles.
        if (GetComponent<ProjectileLauncher>() != null)
        {
            shootHandler = GetComponent<ProjectileLauncher>().gameObject;
        }

        // We start in the 'picking avatar' mode.
        CurrentAppState = AppState.PickingAvatar;

        // Spatial mapping should be disabled when we start up so as not
        // to distract from the avatar picking.
        SpatialMappingManager.Instance.StopObserver();
        SpatialMappingManager.Instance.gameObject.SetActive(false);

        // On device we start by showing the avatar picker.
        PlayerAvatarStore.Instance.SpawnAvatarPicker();
    }

    public void ResetStage()
    {
        // If we fall back to waiting for anchor, everything needed to
        // get us into setting the target transform state will be setup.
        if (CurrentAppState != AppState.PickingAvatar)
        {
            CurrentAppState = AppState.WaitingForAnchor;
        }

        // Reset the underworld.
        if (UnderworldBase.Instance)
        {
            UnderworldBase.Instance.ResetUnderworld();
        }
    }

    void Update()
    {
        switch (CurrentAppState)
        {
            case AppState.PickingAvatar:
                // Avatar picking is done when the avatar picker has been dismissed.
                if (PlayerAvatarStore.Instance.PickerActive == false)
                {
                    CurrentAppState = AppState.WaitingForAnchor;
                }
                break;
            case AppState.WaitingForAnchor:
                // Once the anchor is established we need to run spatial mapping for a
                // little while to build up some meshes.
                if (ImportExportAnchorManager.Instance.AnchorEstablished)
                {
                    CurrentAppState = AppState.WaitingForStageTransform;
                    GestureManager.Instance.OverrideFocusedObject = HologramPlacement.Instance.gameObject;

                    SpatialMappingManager.Instance.gameObject.SetActive(true);
                    SpatialMappingManager.Instance.DrawVisualMeshes = true;
                    SpatialMappingDeformation.Instance.ResetGlobalRendering();
                    SpatialMappingManager.Instance.StartObserver();
                }
                break;
            case AppState.WaitingForStageTransform:
                // Now if we have the stage transform we are ready to go.
                if (HologramPlacement.Instance.GotTransform)
                {
                    CurrentAppState = AppState.Ready;
                    GestureManager.Instance.OverrideFocusedObject = shootHandler;
                }
                break;
        }
    }
}
```

* 在 [ **專案] 面板** 中，流覽至 [ **腳本** ] 資料夾。
* 按兩下 **HologramPlacement** 腳本，在 Visual Studio 中開啟它。
* 使用以下列程式碼取代內容。

```cs
using UnityEngine;
using System.Collections.Generic;
using UnityEngine.Windows.Speech;
using Academy.HoloToolkit.Unity;
using Academy.HoloToolkit.Sharing;

public class HologramPlacement : Singleton<HologramPlacement>
{
    /// <summary>
    /// Tracks if we have been sent a transform for the model.
    /// The model is rendered relative to the actual anchor.
    /// </summary>
    public bool GotTransform { get; private set; }

    /// <summary>
    /// When the experience starts, we disable all of the rendering of the model.
    /// </summary>
    List<MeshRenderer> disabledRenderers = new List<MeshRenderer>();

    /// <summary>
    /// We use a voice command to enable moving the target.
    /// </summary>
    KeywordRecognizer keywordRecognizer;

    void Start()
    {
        // When we first start, we need to disable the model to avoid it obstructing the user picking a hat.
        DisableModel();

        // We care about getting updates for the model transform.
        CustomMessages.Instance.MessageHandlers[CustomMessages.TestMessageID.StageTransform] = this.OnStageTransform;

        // And when a new user join we will send the model transform we have.
        SharingSessionTracker.Instance.SessionJoined += Instance_SessionJoined;

        // And if the users want to reset the stage transform.
        CustomMessages.Instance.MessageHandlers[CustomMessages.TestMessageID.ResetStage] = this.OnResetStage;

        // Setup a keyword recognizer to enable resetting the target location.
        List<string> keywords = new List<string>();
        keywords.Add("Reset Target");
        keywordRecognizer = new KeywordRecognizer(keywords.ToArray());
        keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
        keywordRecognizer.Start();
    }

    /// <summary>
    /// When the keyword recognizer hears a command this will be called.  
    /// In this case we only have one keyword, which will re-enable moving the
    /// target.
    /// </summary>
    /// <param name="args">information to help route the voice command.</param>
    private void KeywordRecognizer_OnPhraseRecognized(PhraseRecognizedEventArgs args)
    {
        ResetStage();
    }

    /// <summary>
    /// Resets the stage transform, so users can place the target again.
    /// </summary>
    public void ResetStage()
    {
        GotTransform = false;

        // AppStateManager needs to know about this so that
        // the right objects get input routed to them.
        AppStateManager.Instance.ResetStage();

        // Other devices in the experience need to know about this as well.
        CustomMessages.Instance.SendResetStage();

        // And we need to reset the object to its start animation state.
        GetComponent<EnergyHubBase>().ResetAnimation();
    }

    /// <summary>
    /// When a new user joins we want to send them the relative transform for the model if we have it.
    /// </summary>
    /// <param name="sender"></param>
    /// <param name="e"></param>
    private void Instance_SessionJoined(object sender, SharingSessionTracker.SessionJoinedEventArgs e)
    {
        if (GotTransform)
        {
            CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
        }
    }

    /// <summary>
    /// Turns off all renderers for the model.
    /// </summary>
    void DisableModel()
    {
        foreach (MeshRenderer renderer in gameObject.GetComponentsInChildren<MeshRenderer>())
        {
            if (renderer.enabled)
            {
                renderer.enabled = false;
                disabledRenderers.Add(renderer);
            }
        }

        foreach (MeshCollider collider in gameObject.GetComponentsInChildren<MeshCollider>())
        {
            collider.enabled = false;
        }
    }

    /// <summary>
    /// Turns on all renderers that were disabled.
    /// </summary>
    void EnableModel()
    {
        foreach (MeshRenderer renderer in disabledRenderers)
        {
            renderer.enabled = true;
        }

        foreach (MeshCollider collider in gameObject.GetComponentsInChildren<MeshCollider>())
        {
            collider.enabled = true;
        }

        disabledRenderers.Clear();
    }


    void Update()
    {
        // Wait till users pick an avatar to enable renderers.
        if (disabledRenderers.Count > 0)
        {
            if (!PlayerAvatarStore.Instance.PickerActive &&
            ImportExportAnchorManager.Instance.AnchorEstablished)
            {
                // After which we want to start rendering.
                EnableModel();

                // And if we've already been sent the relative transform, we will use it.
                if (GotTransform)
                {
                    // This triggers the animation sequence for the model and
                    // puts the cool materials on the model.
                    GetComponent<EnergyHubBase>().SendMessage("OnSelect");
                }
            }
        }
        else if (GotTransform == false)
        {
            transform.position = Vector3.Lerp(transform.position, ProposeTransformPosition(), 0.2f);
        }
    }

    Vector3 ProposeTransformPosition()
    {
        Vector3 retval;
        // We need to know how many users are in the experience with good transforms.
        Vector3 cumulatedPosition = Camera.main.transform.position;
        int playerCount = 1;
        foreach (RemotePlayerManager.RemoteHeadInfo remoteHead in RemotePlayerManager.Instance.remoteHeadInfos)
        {
            if (remoteHead.Anchored && remoteHead.Active)
            {
                playerCount++;
                cumulatedPosition += remoteHead.HeadObject.transform.position;
            }
        }

        // If we have more than one player ...
        if (playerCount > 1)
        {
            // Put the transform in between the players.
            retval = cumulatedPosition / playerCount;
            RaycastHit hitInfo;

            // And try to put the transform on a surface below the midpoint of the players.
            if (Physics.Raycast(retval, Vector3.down, out hitInfo, 5, SpatialMappingManager.Instance.LayerMask))
            {
                retval = hitInfo.point;
            }
        }
        // If we are the only player, have the model act as the 'cursor' ...
        else
        {
            // We prefer to put the model on a real world surface.
            RaycastHit hitInfo;

            if (Physics.Raycast(Camera.main.transform.position, Camera.main.transform.forward, out hitInfo, 30, SpatialMappingManager.Instance.LayerMask))
            {
                retval = hitInfo.point;
            }
            else
            {
                // But if we don't have a ray that intersects the real world, just put the model 2m in
                // front of the user.
                retval = Camera.main.transform.position + Camera.main.transform.forward * 2;
            }
        }
        return retval;
    }

    public void OnSelect()
    {
        // Note that we have a transform.
        GotTransform = true;

        // And send it to our friends.
        CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
    }

    /// <summary>
    /// When a remote system has a transform for us, we'll get it here.
    /// </summary>
    /// <param name="msg"></param>
    void OnStageTransform(NetworkInMessage msg)
    {
        // We read the user ID but we don't use it here.
        msg.ReadInt64();

        transform.localPosition = CustomMessages.Instance.ReadVector3(msg);
        transform.localRotation = CustomMessages.Instance.ReadQuaternion(msg);

        // The first time, we'll want to send the message to the model to do its animation and
        // swap its materials.
        if (disabledRenderers.Count == 0 && GotTransform == false)
        {
            GetComponent<EnergyHubBase>().SendMessage("OnSelect");
        }

        GotTransform = true;
    }

    /// <summary>
    /// When a remote system has a transform for us, we'll get it here.
    /// </summary>
    void OnResetStage(NetworkInMessage msg)
    {
        GotTransform = false;

        GetComponent<EnergyHubBase>().ResetAnimation();
        AppStateManager.Instance.ResetStage();
    }
}
```

**部署及享用**

* 建立專案，並將其部署到您的 HoloLens 裝置。
* 當應用程式準備就緒時，請將其放在圓形中，並注意 EnergyHub 如何顯示在每個人的中心。
* 點擊以放置 EnergyHub。
* 請嘗試語音命令「重設目標」來挑選 EnergyHub 備份，並以群組方式一起工作，以將全息圖移至新位置。

## <a name="chapter-6---real-world-physics"></a>第6章-Real-World 物理

>[!VIDEO https://www.youtube.com/embed/XNpQVSyXwMo]

在本章中，我們將新增可從真實世界表面中跳動的全息影像。 觀賞您和您的朋友所推出的專案，看看您的空間填滿！

### <a name="objectives"></a>目標

* 啟動炮彈，以將實際表面彈開。
* 共用炮彈，讓其他玩家可以看到它們。

### <a name="instructions"></a>指示

* **在階層中選取**[ **HologramCollection** ] 物件。
* 在 [偵測 **器** ] 中按一下 [ **新增元件**]。
* 在搜尋方塊中，輸入 **Projectile 啟動器**。 選取搜尋結果。

**部署及享用**

* 建立並部署到您的 HoloLens 裝置。
* 當應用程式在所有裝置上執行時，請執行點一下以在真實世界表面上啟動 projectile。
* 查看當 projectile 與另一個玩家的頭像衝突時，會發生什麼事！

## <a name="chapter-7---grand-finale"></a>第7章-總計 Finale

>[!VIDEO https://www.youtube.com/embed/kDUPUvZEqRg]

在本章中，我們將發現只能透過共同作業探索的入口網站。

### <a name="objectives"></a>目標

* 共同作業以在錨點上啟動足夠的炮彈來發現秘密入口網站！

### <a name="instructions"></a>指示

* 在 [ **專案] 面板** 中，流覽至 [ **全息** 全像] 資料夾。
* 將 **Underworld** 資產拖放為 HologramCollection 的 **子** 系。
* 選取 **HologramCollection** 後，按一下 [**檢查**] 中的 [**新增元件**] 按鈕。
* 在功能表的 [搜尋] 方塊中，輸入 **ExplodeTarget**。 選取搜尋結果。
* 選取 **HologramCollection** 後，從階層中，將 **EnergyHub** **物件拖曳至** 偵測 **器** 中的 **目標** 欄位。
* 選取 **HologramCollection** 後，從階層中，將 **Underworld** **物件拖曳至** 偵測 **器** 中的 [ **Underworld** ] 欄位。

**部署及享用**

* 建立並部署到您的 HoloLens 裝置。
* 當應用程式啟動時，請共同合作，以在 EnergyHub 上啟動炮彈。
* 當 underworld 出現時，請在 underworld 機器人上啟動炮彈 (按下機器人三次，以提供更有趣的) 。