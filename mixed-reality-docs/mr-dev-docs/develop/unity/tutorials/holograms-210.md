---
title: MR 輸入 210-注視
description: 遵循此程式碼逐步解說，使用 Unity、Visual Studio 和 HoloLens 來瞭解注視概念的詳細資料。
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit、mixedrealitytoolkit、mixedrealitytoolkit-unity、學院、教學課程、注視
ms.openlocfilehash: b513d304e78d51b447f0bbba4990fb7df0556707
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2020
ms.locfileid: "91680645"
---
# <a name="mr-input-210-gaze"></a>MR Input 210：注視

>[!NOTE]
>混合實境學院教學課程的設計是以 HoloLens (第 1 代) 和混合實境沉浸式頭戴裝置為準。  因此，對於仍在尋找這些裝置開發指引的開發人員而言，我們覺得這些教學課程很重要。  這些教學課程 **_不會_** 使用用於 HoloLens 2 的最新工具組或互動進行更新。  系統會保留這些資訊，以繼續在支援的裝置上運作。 已針對 HoloLens 2 公佈[一系列新的教學課程](../../../mr-learning-base-01.md)。

[注視](../../../design/gaze-and-commit.md) 是輸入的第一種形式，會顯示使用者的意圖和認知。 MR 輸入 210 (也稱為 Project Explorer) 是 Windows Mixed Reality 的注視相關概念深入探討。 我們會將內容感知新增至游標和全像投影，以充分利用您的應用程式對使用者的注視有何認識。

>[!VIDEO https://www.youtube.com/embed/yKAttGduVp0]

我們在這裡有一個很好用的太空人，可協助您瞭解一些概念。 在 [MR 基本的 101](../../../develop/unity/tutorials/holograms-101.md)中，我們有一個簡單的游標，也就是您的注視。 今天，我們要將一個步驟移至簡單資料指標之外：

* 我們會將游標和我們的全像是注視：這兩者都會根據使用者的查看位置，或 *使用者不在尋找的* 位置而變更。 這樣就能感知它們的內容。
* 我們會將意見反應新增至游標和全像影像，以提供使用者更多有關目標的內容。 這種意見反應可以是音訊和視覺效果。
* 我們將為您示範以協助使用者達到較小目標的目標技術。
* 我們將示範如何使用方向指標將使用者的注意力吸引到您的全像投影。
* 我們將會教您如何在您的世界各地，讓您的隨用隨之移動。

>[!IMPORTANT]
>下列各章節中內嵌的影片是使用較舊版本的 Unity 和混合現實工具組所記錄。 雖然逐步指示是正確且最新的，但您可能會在相對應的影片中看到已過期的腳本和視覺效果。 影片仍隨附于 posterity，因為所涵蓋的概念仍然適用。

## <a name="device-support"></a>裝置支援

<table>
<tr>
<th>課程</th><th style="width:150px"> <a href="../../../hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">沉浸式頭戴裝置</a></th>
</tr><tr>
<td>MR Input 210：注視</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="before-you-start"></a>開始之前

### <a name="prerequisites"></a>Prerequisites

* [已安裝正確工具](../../../develop/install-the-tools.md)的 Windows 10 電腦。
* 一些基本的 c # 程式設計功能。
* 您應已完成 [MR 基本的 101](../../../develop/unity/tutorials/holograms-101.md)。
* [針對開發設定](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)的 HoloLens 裝置。

### <a name="project-files"></a>專案檔

* 下載專案 [所需的](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-210-Gaze.zip) 檔案。 需要 Unity 2017.2 或更新版本。
* 取消將檔案封存到您的桌面或其他易於觸及的位置。

>[!NOTE]
>如果您想要在下載之前查看原始程式碼， [可在 GitHub 上](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-210-Gaze)取得。

### <a name="errata-and-notes"></a>勘誤表和記事

* 在 Visual Studio 中，必須停用 [工具]-[>選項] 下的 [Just My Code] (未核取) ，才能在程式碼中叫用中斷點。

## <a name="chapter-1---unity-setup"></a>第1章-Unity 設定

>[!VIDEO https://www.youtube.com/embed/_Ccn6riQ6vU]

### <a name="objectives"></a>目標

* 最佳化 Unity 以用於 HoloLens 開發。
* 匯入資產並設定場景。
* 查看 HoloLens 中的太空人。

### <a name="instructions"></a>Instructions

1. 啟動 Unity。
2. 選取 [新增專案]  。
3. 將專案命名為 **ModelExplorer** 。
4. 輸入 [位置] 作為先前未封存的 [ **注視** ] 資料夾。
5. 確定專案已設定為 **3D** 。
6. 按一下 [ **建立專案** ]。

### <a name="unity-settings-for-hololens"></a>HoloLens 的 Unity 設定

我們需要讓 Unity 知道我們想要匯出的應用程式應該建立一個 [沉浸式視圖](../../../design/app-views.md) ，而不是2d 視圖。 做法是將 HoloLens 新增為虛擬實境裝置。

1. 移至 **> Player 的 [編輯 > 專案設定** ]。
2. 在 [播放程式設定] 的 [偵測 **器] 面板** 中，選取 [ **Windows Store** ] 圖示。
3. 展開 [XR 設定] 群組。
4. 在 [轉譯] 區段中核取 [支援虛擬實境] 核取方塊，以新增 [虛擬實境 SDK] 清單。
5. 確認 **Windows Mixed Reality** 出現在清單中。 如果沒有，請選取 **+** 清單底部的按鈕，然後選擇 [ **Windows** 全像]。

接下來，我們需要將腳本後端設定為 .NET。

1. 移至 **> Player 的 [編輯] > 專案設定** (您可能仍已從上一個步驟) 。
2. 在 [播放程式設定] 的 [偵測 **器] 面板** 中，選取 [ **Windows Store** ] 圖示。
3. 在 [ **其他設定** ] 設定區段中，確定 [ **腳本後端** ] 設定為 [ **.net** ]

最後，我們會更新品質設定，以在 HoloLens 上達成更快速的效能。

1. 移至 [ **編輯 > 專案設定 > 品質** ]。
2. 按一下 [Windows 市集中] 圖示底下 **預設** 資料列中的向下箭號。
3. 針對 **Windows Store 應用程式** 選取 [ **非常低** ]。

### <a name="import-project-assets"></a>匯入專案資產

1. 以滑鼠右鍵按一下 [ **專案** ] 面板中的 [ **資產** ] 資料夾。
2. 按一下 [匯 **入封裝 > 自訂套件** ]。
3. 流覽至您所下載的專案檔，然後按一下 [ **ModelExplorer unitypackage** ]。
4. 按一下 [開啟]。
5. 載入封裝之後，請按一下 [匯 **入** ] 按鈕。

### <a name="setup-the-scene"></a>設定場景

1. 在階層中，刪除 **主要攝影機** 。
2. 在 **HoloToolkit** 資料夾中，開啟 **輸入** 資料夾，然後開啟 **Prefabs** 資料夾。
3. 將 **MixedRealityCameraParent** 預製專案從 **Prefabs** 資料夾拖 **放到階層中。**
4. 以滑鼠右鍵按一下階層中的 **方向燈** ，然後選取 [ **刪除** ]。
5. 在 [全像 **] 資料夾中** ，將下列資產拖放到 **階層的根目錄中：**
    * **AstroMan**
    * **光線**
    * **SpaceAudioSource**
    * **SpaceBackground**
6. 啟動 **播放模式** ▶以查看太空人。
7. 按一下 [ **播放模式▶]** 以 **停止** 。
8. 在 [全像 **] 資料夾中** ，尋找 **Fitbox** 資產，然後將它拖曳到 **階層的根目錄。**
9. **在 [階層] 面板中** 選取 **Fitbox** 。
10. 將 **AstroMan** 集合從階層拖曳 **至 [** 偵測 **器** ] 面板中 Fitbox 的 [ **全息圖集合** ] 屬性。

### <a name="save-the-project"></a>儲存專案

1. 儲存新場景： **File > 另存場景** 。
2. 按一下 [ **新增資料夾** ]，然後將資料夾命名為 **幕後** 。
3. 將檔案命名為 " **ModelExplorer** "，並將它儲存在 **幕後** 資料夾中。

### <a name="build-the-project"></a>建置專案

1. 在 Unity 中，選取 [ **File > Build Settings** ]。
2. 按一下 [ **新增開啟場景** ] 以加入場景。
3. 在 [ **平臺** ] 清單中選取 **通用 Windows 平臺** ，然後按一下 [ **切換平臺** ]。
4. 如果您是特別針對 HoloLens 進行開發，請將 **目標裝置** 設定為 **hololens** 。 否則，請將它保留在 **任何裝置** 上。
5. 請確定 **組建類型** 設定為 [ **D3D** ]，並將 [ **Sdk** ] 設定為 [ **最新安裝** 的 (，其應為 SDK 16299 或更新版本的) 。
6. 按一下 [建置]  。
7. 建立名為 "App" 的 **新資料夾** 。
8. 按一下 **應用程式** 資料夾。
9. 按下 [ **選取資料夾** ]。

當 Unity 完成時，將會出現檔案總管視窗。

1. 開啟 **應用程式** 資料夾。
2. 開啟 **ModelExplorer Visual Studio 方案** 。

如果要部署到 HoloLens：

1. 使用 Visual Studio 中的頂端工具列，將目標從 Debug 變更為 **Release** ，以及從 ARM 變更為 **x86** 。
2. 按一下 [本機電腦] 按鈕旁的下拉箭號，然後選取 [ **遠端電腦** ]。
3. 輸入 **您的 HoloLens 裝置 IP 位址** ，並將驗證模式設定為 **通用 (未加密的通訊協定)** 。 按一下 [選取]。  如果您不知道您的裝置 IP 位址，請查看 [ **設定] > Network & Internet > Advanced 選項** 。
4. 在頂端功能表列中，按一下 [ **Debug-> 啟動但不進行調試** ]，或按 **Ctrl + F5** 。 如果這是您第一次部署至您的裝置，您必須將 [它與 Visual Studio 配對](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#pairing-your-device)。
5. 部署應用程式之後，請使用 **選取手勢** 來關閉 **Fitbox** 。

如果部署到沉浸式耳機：

1. 使用 Visual Studio 中的頂端工具列，將目標從 Debug 變更為 **Release** ，以及從 ARM 變更為 **x64** 。
2. 請確定部署目標設定為 [ **本機電腦** ]。
3. 在頂端功能表列中，按一下 [ **Debug-> 啟動但不進行調試** ]，或按 **Ctrl + F5** 。
4. 部署應用程式之後，請在動作控制器上提取觸發程式來關閉 **Fitbox** 。

## <a name="chapter-2---cursor-and-target-feedback"></a>第2章-游標和目標意見反應

>[!VIDEO https://www.youtube.com/embed/S24u0V_T7ZI]

### <a name="objectives"></a>目標

* 資料指標視覺化設計和行為。
* 以注視為基礎的資料指標意見反應。
* 注視的全像影像意見反應。

我們將以一些資料指標設計原則做為基礎，也就是：

* 資料指標一律會存在。
* 不要讓資料指標變得太小或太大。
* 避免阻礙內容。

### <a name="instructions"></a>Instructions

1. 在 [ **HoloToolkit\Input\Prefabs** ] 資料夾中，尋找 **InputManager** 資產。
2. 將 **InputManager** 拖放到階層上 **。**
3. 在 [ **HoloToolkit\Input\Prefabs** ] 資料夾中，尋找資料 **指標** 資產。
4. 將 **游標** 拖放到階層上 **。**
5. 選取階層中的 **InputManager** 物件 **。**
6. 將資料 **指標** 物件從階層 **拖曳至偵測****器** 底部的 InputManager **SimpleSinglePointerSelector** 資料 **指標** 欄位。

![簡單的單一指標選取器設定](images/holograms210-ssps.png)

### <a name="build-and-deploy"></a>建置和部署

1. 從檔案 **> 組建設定** 重建應用程式。
2. 開啟 **應用程式資料夾** 。
3. 開啟 **ModelExplorer Visual Studio 方案** 。
4. 按一下 [ **Debug-> 啟動但不進行調試]，** 或按 **Ctrl + F5** 。
5. 觀察資料指標的繪製方式，以及它如何在觸碰全像影像時變更外觀。

### <a name="instructions"></a>Instructions

1. **在 [階層] 面板中** ，展開 [ **AstroMan** -> **GEO_G** ] -> **Back_Center** 物件。
2. 按兩下 [ **Interactible.cs** ]，在 Visual Studio 中開啟。
3. 將 IFocusable. OnFocusEnter 中的行取消批註 **( # B1** 和 **IFocusable. OnFocusExit ( # B3** 回呼 in **Interactible.cs** 。 當焦點 (于) 進入和結束特定 GameObject 的碰撞器時，混合現實工具組的 InputManager 就會呼叫這些方法。

```cs
/* TODO: DEVELOPER CODING EXERCISE 2.d */

void IFocusable.OnFocusEnter()
{
    for (int i = 0; i < defaultMaterials.Length; i++)
    {
        // 2.d: Uncomment the below line to highlight the material when gaze enters.
        defaultMaterials[i].EnableKeyword("_ENVIRONMENT_COLORING");
    }
}

void IFocusable.OnFocusExit()
{
    for (int i = 0; i < defaultMaterials.Length; i++)
    {
        // 2.d: Uncomment the below line to remove highlight on material when gaze exits.
        defaultMaterials[i].DisableKeyword("_ENVIRONMENT_COLORING");
    }
}
```

>[!NOTE]
>我們使用 `EnableKeyword` 和更新版本 `DisableKeyword` 。 為了在您自己的應用程式中使用工具組的標準著色器來使用這些功能，您必須遵循 [Unity 指導方針，透過腳本存取材質](https://docs.unity3d.com/Manual/MaterialsAccessingViaScript.html)。 在此情況下，我們已在 [資源] 資料夾中包含三個醒目提示 [的材質](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-210-Gaze/Completed/ModelExplorer/Assets/Resources/Models/AstroMan/Materials) 變化 (尋找名稱) 中醒目提示的三個材質。

### <a name="build-and-deploy"></a>建置和部署

1. 同樣地，建立專案並部署到 HoloLens。
2. 觀察當注視的目標物件和不是時，會發生什麼事。

## <a name="chapter-3---targeting-techniques"></a>第3章-目標技術

>[!VIDEO https://www.youtube.com/embed/TFnuLva4VJ0]

### <a name="objectives"></a>目標

* 讓您更輕鬆地鎖定全像影像。
* 穩定的自然標頭移動。

### <a name="instructions"></a>Instructions

1. **在 [階層] 面板中** ，選取 [ **InputManager** ] 物件。
2. 在 [偵測 **器** ] 面板中，尋找「 **注視的穩定** 」腳本。 如果您想要查看，請按一下該檔案以在 Visual Studio 中開啟。
    * 此腳本會反復查看 Raycast 資料的範例，並協助穩定使用者的注視精確度目標。
3. 在偵測 **器** 中，您可以編輯已 **儲存的穩定性範例** 值。 此值代表穩定程式反覆運算以計算穩定值的樣本數。

## <a name="chapter-4---directional-indicator"></a>第4章-方向指標

>[!VIDEO https://www.youtube.com/embed/htVbJCMlj64]

### <a name="objectives"></a>目標

* 在游標處新增方向指標，以協助尋找全像影像。

### <a name="instructions"></a>Instructions

我們將使用 **DirectionIndicator.cs** 檔案，此檔案將：

1. 如果使用者不是在全像撥雲見日，則顯示方向指標。
2. 如果使用者是在全像撥雲見日，則隱藏方向指標。
3. 更新方向指標以指向全像影像。

讓我們開始這次的教學。

1. 按一下 [階層 **] 面板中的 [** **AstroMan** ] 物件，然後 **按一下箭** 號將其展開。
2. **在 [階層** ] 面板中，選取 [ **AstroMan** ] 底下的 [ **DirectionalIndicator** ] 物件。
3. 在 [偵測 **器** ] 面板中，按一下 [ **新增元件** ] 按鈕。
4. 在功能表中，輸入搜尋方塊 **方向指標** 。 選取搜尋結果。
5. **在 [階層] 面板中** ，將資料 **指標** 物件拖放至偵測 **器** 中的資料 **指標** 屬性。
6. 在 [ **專案** ] 面板的 [全像 **] 資料夾中** ，將 **DirectionalIndicator** 資產拖放到偵測 **器** 的 **方向指標** 屬性。
7. 建立並部署應用程式。
8. 觀賞方向指標物件如何協助您尋找太空人。

## <a name="chapter-5---billboarding"></a>第5章-Billboarding

>[!VIDEO https://www.youtube.com/embed/qFiLr_LUACE]

### <a name="objectives"></a>目標

* 使用 billboarding 讓全像投影都能朝您面對。

我們將使用 **Billboard.cs** 檔案來維持 GameObject 導向，使其隨時都能與使用者互動。

1. **在 [階層] 面板中** ，選取 [ **AstroMan** ] 物件。
2. 在 [偵測 **器** ] 面板中，按一下 [ **新增元件** ] 按鈕。
3. 在功能表中，輸入搜尋方塊 **佈告欄** 。 選取搜尋結果。
4. 在 [偵測 **器** ] 中，將 **Pivot 軸** 設定為 **Y** 。
5. 試試看！ 如同之前一樣建立及部署應用程式。
6. 無論您如何改變觀點，都能看到佈告欄物件的臉部。
7. 請立即從 **AstroMan** 刪除腳本。

## <a name="chapter-6---tag-along"></a>第6章-標記-沿著

>[!VIDEO https://www.youtube.com/embed/Ct8ORZAX5JU]

### <a name="objectives"></a>目標

* 使用標籤-一併使用標籤，讓我們的全像是在房間周圍。

當我們處理此問題時，我們將會以下列設計條件約束為導向：

* 內容應該一律一目了然。
* 內容不能以這種方式進行。
* 標頭鎖定內容不舒服。

此處所用的解決方案是使用「加上標籤」的方法。

標記物件永遠不會完全離開使用者的觀點。 您可以將標籤與使用者的標頭相關聯的物件視為使用者的標頭。 當使用者移動時，內容會在觀看視野的邊緣時保持不變，而不需要完全離開。 當使用者 gazes 到加上標籤的物件時，它會更完整地顯示。

我們將使用 **SimpleTagalong.cs** 檔案，此檔案將：

1. 判斷加上標籤的物件是否位於相機界限內。
2. 如果不在視圖的 [分隔] 內，請將標記放在視圖的 [截維] 中。
3. 否則，請將標記放置在與使用者的預設距離之間。

若要這樣做，我們必須先變更 **Interactible.cs** 腳本來呼叫 **TagalongAction** 。

1. 完成編碼練習6來編輯 **Interactible.cs** 。 a (取消批註行84至 87) 。

```cs
/* TODO: DEVELOPER CODING EXERCISE 6.a */
// 6.a: Uncomment the lines below to perform a Tagalong action.
if (interactibleAction != null)
{
    interactibleAction.PerformAction();
}
```

**InteractibleAction.cs** 腳本（與 **Interactible.cs** 配對）會在您點擊全像影像時執行自訂動作。 在此情況下，我們將特別針對標記使用一個。

* 在 [ **腳本** ] 資料夾中，按一下 [ **TagalongAction.cs** 資產] 以在 Visual Studio 中開啟。
* 完成程式碼撰寫練習，或將其變更為：
  * 在階層 **頂端的搜尋列中，輸入** **ChestButton_Center** 並選取結果。
  * 在 [偵測 **器** ] 面板中，按一下 [ **新增元件** ] 按鈕。
  * 在功能表中，輸入搜尋方塊 **Tagalong 動作** 。 選取搜尋結果。
  * 在 [全像 **] 資料夾中** 尋找 **Tagalong** 資產。
  * 選取階層中的 **ChestButton_Center** 物件 **。** 將 **TagAlong** 物件從 **專案** 面板拖放到偵測 **器** 的 [ **要 TagAlong 的物件** ] 屬性中。
  * 將 **Tagalong 動作** 物件從偵測 **器** 拖曳到 **Interactible** 腳本的 **Interactible 動作** 欄位中。
* 按兩下 **TagalongAction** 腳本，在 Visual Studio 中開啟它。

![Interactible 設定](images/holograms210-interactible.png)

我們需要新增下列內容：

* 將功能加入至 TagalongAction 腳本中的 PerformAction 函式， (繼承自 InteractibleAction) 。
* 將 billboarding 加入至 gazed 物件，並將 pivot 軸設定為 XY。
* 然後將簡單標記新增至物件。

以下是來自 **TagalongAction.cs** 的解決方案：

```cs
// Copyright (c) Microsoft Corporation. All rights reserved.
// Licensed under the MIT License. See LICENSE in the project root for license information.

using HoloToolkit.Unity;
using UnityEngine;

public class TagalongAction : InteractibleAction
{
    [SerializeField]
    [Tooltip("Drag the Tagalong prefab asset you want to display.")]
    private GameObject objectToTagalong;

    private void Awake()
    {
        if (objectToTagalong != null)
        {
            objectToTagalong = Instantiate(objectToTagalong);
            objectToTagalong.SetActive(false);

            /* TODO: DEVELOPER CODING EXERCISE 6.b */

            // 6.b: AddComponent Billboard to objectToTagAlong,
            // so it's always facing the user as they move.
            Billboard billboard = objectToTagalong.AddComponent<Billboard>();

            // 6.b: AddComponent SimpleTagalong to objectToTagAlong,
            // so it's always following the user as they move.
            objectToTagalong.AddComponent<SimpleTagalong>();

            // 6.b: Set any public properties you wish to experiment with.
            billboard.PivotAxis = PivotAxis.XY; // Already the default, but provided in case you want to edit
        }
    }

    public override void PerformAction()
    {
        // Recommend having only one tagalong.
        if (objectToTagalong == null || objectToTagalong.activeSelf)
        {
            return;
        }

        objectToTagalong.SetActive(true);
    }
}
```

* 試試看！ 建立並部署應用程式。
* 觀賞內容如何沿著注視點的中心，但不會持續而不會封鎖。