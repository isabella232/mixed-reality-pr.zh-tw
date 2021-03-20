---
title: HoloLens (第1代) 和 Azure 302-電腦視覺
description: 完成本課程，以瞭解如何在混合現實應用程式中使用 Azure 電腦視覺，以在提供的影像中辨識視覺內容。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure，mixed reality，學院，unity，教學課程，api，電腦視覺，hololens，沉浸，vr，Windows 10，Visual Studio
ms.openlocfilehash: 119d83ec9fef97b4e4017b2226a9593404847a71
ms.sourcegitcommit: 35bd43624be33afdb1bf6ba4ddbe36d268eb9bda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/20/2021
ms.locfileid: "104730535"
---
# <a name="hololens-1st-gen-and-azure-302-computer-vision"></a>HoloLens (第1代) 和 Azure 302：電腦視覺

<br>

>[!NOTE]
>混合實境學院教學課程的設計是以 HoloLens (第 1 代) 和混合實境沉浸式頭戴裝置為準。  因此，對於仍在尋找這些裝置開發指引的開發人員而言，我們覺得這些教學課程很重要。  這些教學課程 **_不會_** 使用用於 HoloLens 2 的最新工具組或互動進行更新。  系統會保留這些資訊，以繼續在支援的裝置上運作。 未來將會有一系列新的教學課程，將會示範如何針對 HoloLens 2 進行開發。  當張貼這些教學課程時，將會使用這些教學課程的連結來更新此通知。

<br>

在此課程中，您將瞭解如何在混合現實應用程式中使用 Azure 電腦視覺功能，以在提供的影像中辨識視覺內容。

辨識結果會顯示為描述性標記。 您可以使用此服務，而不需要訓練機器學習模型。 如果您的實行需要訓練機器學習模型，請參閱 [MR 和 Azure 302b](mr-azure-302b.md)。

![實驗室結果](images/AzureLabs-Lab2-000.png)

Microsoft 電腦視覺是一組 Api，其設計目的是要為開發人員提供影像處理和分析 (，其中包含從雲端使用的最先進演算法) 的傳回信息。 開發人員上傳影像或影像 URL，而 Microsoft 電腦視覺 API 演算法會根據輸入使用者的輸入，分析視覺內容，然後傳回信息，包括識別影像的類型和品質、偵測人臉 (傳回其座標) 、標記或分類影像。 如需詳細資訊，請造訪 [Azure 電腦視覺 API 頁面](https://azure.microsoft.com/services/cognitive-services/computer-vision/)。

完成本課程之後，您將會有混合現實 HoloLens 應用程式，它將能夠執行下列作業：

1.  使用點一下手勢，HoloLens 的攝影機將會捕獲映射。
2.  映射將會傳送至 Azure 電腦視覺 API 服務。 
3.  辨識的物件將會列在位於 Unity 場景中的簡單 UI 群組中。

在您的應用程式中，您可以自行決定如何將結果與您的設計整合。 本課程旨在告訴您如何整合 Azure 服務與您的 Unity 專案。 您的工作是使用您在本課程中所得到的知識，來增強您的混合現實應用程式。

## <a name="device-support"></a>裝置支援

<table>
<tr>
<th>課程</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">沉浸式頭戴裝置</a></th>
</tr><tr>
<td> MR 和 Azure 302：電腦視覺</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> 雖然本課程主要著重于 HoloLens，您也可以將本課程中所學到的內容套用到 Windows Mixed Reality 沉浸式 (VR) 耳機。 因為沉浸式 (VR) 耳機沒有可存取的攝影機，所以您需要有連接到電腦的外部攝影機。 當您依照課程的指示，您將會看到有關您可能需要採用以支援沉浸式 (VR) 耳機的任何變更的注意事項。

## <a name="prerequisites"></a>Prerequisites

> [!NOTE]
> 本教學課程是專為擁有 Unity 和 c # 基本經驗的開發人員所設計。 另外也請注意，本檔中的必要條件和撰寫的指示，代表在撰寫 (可能是 2018) 時經過測試和驗證的內容。 You are free to use the latest software, as listed within the [install the tools](../../install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.

本課程建議您採用下列硬體和軟體：

- 開發電腦，與適用于沉浸式 (VR) 耳機開發的[Windows Mixed Reality 相容](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines)
- [啟用開發人員模式的 Windows 10 Fall Creators Update (或更新版本) ](../../install-the-tools.md#installation-checklist)
- [最新的 Windows 10 SDK](../../install-the-tools.md#installation-checklist)
- [Unity 2017。4](../../install-the-tools.md#installation-checklist)
- [Visual Studio 2017](../../install-the-tools.md#installation-checklist)
- [Windows Mixed Reality 沉浸式 (VR) 耳機](../../../discover/immersive-headset-hardware-details.md)，或已啟用開發人員模式的[Microsoft HoloLens](/hololens/hololens1-hardware)
- 連接到您 PC (的攝影機，適用于沉浸式耳機開發) 
- 適用于 Azure 安裝程式和電腦視覺 API 抓取的網際網路存取

## <a name="before-you-start"></a>在您開始使用 Intune 之前

1.  為了避免在建立此專案時發生問題，強烈建議您在根或近端根資料夾中，建立本教學課程中所述的專案 (長的資料夾路徑可能會在組建階段) 時發生問題。
2.  設定及測試 HoloLens。 如果您需要設定 HoloLens 的支援， [請務必造訪 HoloLens 安裝文章](/hololens/hololens-setup)。 
3.  開始開發新的 HoloLens 應用程式時，最好先執行校正和感應器調整， (有時它可以協助針對每個使用者) 執行這些工作。 

如需有關校正的說明，請遵循此 [與 HoloLens 校正文章相關的連結](/hololens/hololens-calibration#hololens-2)。

如需有關感應器微調的說明，請依照此 [連結來進行「HoloLens 感應器微調」文章](/hololens/hololens-updates)。

## <a name="chapter-1--the-azure-portal"></a>第1章-Azure 入口網站

若要在 Azure 中使用 *電腦視覺 API* 服務，您必須將服務的實例設定為可供應用程式使用。

1.  首先，登入 [Azure 入口網站](https://portal.azure.com)。 

    > [!NOTE]
    > 如果您還沒有 Azure 帳戶，您將需要建立一個帳戶。 如果您在課堂或實驗室的情況下進行本教學課程，請洽詢講師或其中一個 proctors，協助您設定新的帳戶。

2.  登入後，按一下左上角的 [ **新增** ]，並搜尋 *電腦視覺 API*，然後按一下 [ **輸入**]。

    ![在 Azure 中建立新的資源](images/AzureLabs-Lab2-00.png)

    > [!NOTE]
    > 在較新的入口網站中，[**建立資源**] 可能已取代 **新** 的文字。
 
3.  新頁面將提供 *電腦視覺 API* 服務的描述。 在此頁面的左下方，選取 [ **建立** ] 按鈕，以建立與此服務的關聯。

    ![關於電腦視覺 api 服務](images/AzureLabs-Lab2-01.png)
 
4.  當您按一下 [ **建立**] 之後：

    1. 為此服務實例插入您想要的 **名稱** 。
    2. 選取 [訂用帳戶]  。
    3. 選取適合您的 **定價層** ，如果這是您第一次建立 *電腦視覺 API* 服務，則應可使用名為 F0) 的免費層 (。
    4. 選擇資源群組，或建立一個新的 **資源群組** 。 資源群組提供一種方式來監視、控制存取、布建及管理 Azure 資產集合的計費。 建議您保留與單一專案相關聯的所有 Azure 服務 (例如，) 一般資源群組下的實驗室，) 。 

        > 如果您想要閱讀更多有關 Azure 資源群組的資訊，請 [造訪資源群組文章](/azure/azure-resource-manager/resource-group-portal)。

    5. 如果您要建立新的資源群組) ，請判斷資源群組 (的位置。 位置最好是在應用程式執行所在的區域中。 某些 Azure 資產僅適用于某些區域。

    6. 您也必須確認您已瞭解套用到此服務的條款及條件。
    7. 按一下 [建立]。

        ![服務建立資訊](images/AzureLabs-Lab2-02.png)

5.  當您按一下 [ **建立**] 之後，就必須等待服務建立完成，這可能需要一分鐘的時間。
6.  建立服務實例之後，入口網站中就會出現通知。

    ![查看新服務的新通知](images/AzureLabs-Lab2-03.png) 
 
7.  按一下通知以探索新的服務實例。 

    ![選取 [移至資源] 按鈕。](images/AzureLabs-Lab2-04.png)
 
8. 按一下通知中的 [ **移至資源** ] 按鈕，以流覽您的新服務實例。 您將會進入新的電腦視覺 API 服務實例。 

    ![新的電腦視覺 API 服務映射](images/AzureLabs-Lab2-05.png)
 
9.  在本教學課程中，您的應用程式將需要呼叫您的服務，這是透過使用服務的訂用帳戶金鑰來完成。
10. 從 [ *快速入門* ] 頁面，在您的 *電腦視覺 API* 服務中，流覽至第一個步驟、 *抓取您的金鑰*，然後按一下 [機 **碼** ] (您也可以按一下位於 [服務] 導覽功能表中，以按鍵圖示) 表示的藍色超連結鍵，以達成此目的。 這會顯示您的服務 *金鑰*。
11. 複製其中一個顯示的金鑰，您稍後會在專案中使用。 

12. 返回到 [ *快速入門* ] 頁面，然後從該處提取您的端點。 請注意，您可能會有不同的不同，視您的區域而定 (如果是的話，您稍後將需要變更程式碼) 。 取得此端點的複本以供稍後使用：

    ![新的電腦視覺 API 服務](images/AzureLabs-Lab2-05-5.png)

    > [!TIP]
    > 您可以在 [這裡](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa)檢查各種不同的端點。 

## <a name="chapter-2--set-up-the-unity-project"></a>第2章-設定 Unity 專案

以下是使用 mixed reality 進行開發的一般設定，因此，它是適用于其他專案的絕佳範本。

1.  開啟 *Unity* ，然後按一下 [ **新增**]。 

    ![開始新的 Unity 專案。](images/AzureLabs-Lab2-06.png)

2.  您現在將需要提供 Unity 專案名稱。 插入 **MR_ComputerVision**。 請確定專案類型設定為 **3d**。 將 **位置** 設定為適合您 (記住，較接近根目錄的) 。 然後，按一下 [ **建立專案**]。

    ![提供新 Unity 專案的詳細資料。](images/AzureLabs-Lab2-07.png)

3.  在 Unity 開啟的情況下，值得檢查預設 **腳本編輯器** 是否設定為 **Visual Studio**。 移至 [ **編輯] > 喜好** 設定，然後在新視窗中，流覽至 [ **外部工具**]。 將 **外部腳本編輯器** 變更為 **Visual Studio 2017**。 關閉 [ **喜好** 設定] 視窗。

    ![更新腳本編輯器喜好設定。](images/AzureLabs-Lab2-08.png)

4.  接下來，移至 [檔案 **> 組建設定** ]，選取 [ **通用 Windows 平臺**]，然後按一下 [ **切換平臺** ] 按鈕以套用您的選取專案。

    ![[組建設定] 視窗，將平臺切換至 UWP。](images/AzureLabs-Lab2-10.png)

5.  在檔案中仍 **> 組建設定** ，並確定：

    1. **目標裝置** 設定為 **HoloLens**

        > 針對沉浸式耳機，將 **目標裝置** 設為 *任何裝置*。

    2. **組建類型** 設定為 **D3D**
    3. **SDK** 已設定為 **最新安裝**
    4. **Visual Studio 版本** 設定為 **最新安裝**
    5. **組建並執行** 設定為 **本機電腦**
    6. 儲存場景，並將其新增至組建。

        1. 若要這麼做，請選取 [ **新增開啟的場景**]。 [儲存] 視窗隨即出現。
        
            ![按一下 [新增開啟場景] 按鈕](images/AzureLabs-Lab2-11.png)

        2. 為此和任何未來的場景建立新的資料夾，然後選取 [ **新增資料夾** ] 按鈕，建立新的資料夾，將它命名為 **場景**。

            ![建立新的腳本資料夾](images/AzureLabs-Lab2-12.png)

        3. 開啟新建立的 **場景** 資料夾，然後在 [ *檔案名*：文字] 欄位中，輸入 **MR_ComputerVisionScene**，然後按一下 [ **儲存**]。

            ![提供新場景的名稱。](images/AzureLabs-Lab2-13.png)

            > 請注意，您必須將 Unity 場景儲存在 [ *資產* ] 資料夾中，因為它們必須與 Unity 專案相關聯。 建立幕後資料夾 (和其他類似的資料夾) 是結構化 Unity 專案的典型方式。

    7. [ *組建設定*] 中的其餘設定，現在應該保持為預設值。

6. 在 [ *組建設定* ] 視窗中，按一下 [ **播放程式設定** ] 按鈕，這會開啟偵測 *器* 所在空間中的相關面板。 

    ![開啟 [播放玩家設定]。](images/AzureLabs-Lab2-14.png)

7. 在此面板中，需要驗證幾個設定：

    1. 在 [ **其他設定** ] 索引標籤中：

        1. **腳本執行階段版本** 應該是 **穩定** 的 ( .net 3.5 對等) 。
        2. **腳本後端** 應該是 **.net**
        3. **API 相容性層級** 應為 **.net 4.6**

            ![更新其他設定。](images/AzureLabs-Lab2-15.png)
      
    2. 在 [ **發行設定** ] 索引標籤的 [ **功能**] 下，選取：

        1. **InternetClient**
        2. **網路攝影機**

            ![正在更新發行設定。](images/AzureLabs-Lab2-16.png)

    3. 在面板的 [XR 設定] 中，在 [ **設定** ] (找到的 [ **發佈設定** ]) 、[滴答 **虛擬實境支援**]，請確定已新增 **Windows Mixed Reality SDK** 。

        ![更新 X R 設定。](images/AzureLabs-Lab2-17.png)

8.  回到 *組建設定*： _Unity c #_ 專案不再呈現灰色;勾選此方塊旁邊的核取方塊。 
9.  關閉 [建置設定] 視窗。
10. 將場景和專案儲存 (檔 **> 儲存場景/檔案 > 儲存專案**) 。

## <a name="chapter-3--main-camera-setup"></a>第3章-主要攝影機設定

> [!IMPORTANT]
> 如果您想要略過此課程的 *Unity 設定* 元件，並直接繼續進行程式碼，請隨意下載 [unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302%20-%20Computer%20vision/Azure-MR-302.unitypackage)，並將其匯入到您的專案中做為 [自訂套件](https://docs.unity3d.com/Manual/AssetPackages.html)，然後繼續進行 [第5章](#chapter-5--create-the-resultslabel-class)。

1.  在 [階層] *面板* 中，選取 [ **主要相機**]。 
2.  一旦選取之後，您就可以在 [偵測 *器] 面板* 中看到 **主要攝影機** 的所有元件。

    1. **攝影機物件** 必須命名為 **主要攝影機** (請注意拼寫！ ) 
    2. 主要攝影機 **標記** 必須設定為 **MainCamera** (注意拼寫！ ) 
    3. 請確定 **轉換位置** 設定為 **0、0、0**
    4. 將 [ **清除旗標** ] 設定為 [ **純色** ] (針對沉浸式耳機) 略過此設定。
    5. 將相機元件的 **背景** 色彩設定為 **黑色、Alpha 0 (Hex 碼： #00000000)** (略過此項，以取得沉浸式耳機) 。

        ![更新相機元件。](images/AzureLabs-Lab2-18.png)
 
3.  接下來，您必須建立連接到 **主要攝影機** 的簡單「游標」物件，這可協助您在應用程式執行時定位影像分析輸出。 此游標會決定相機焦點的中心點。

若要建立資料指標：

1.  在 [階層] *面板* 中，以滑鼠右鍵按一下 **主要攝影機**。 在 [ **3D 物件**] 下，按一下 [ **球體**]。

    ![選取資料指標物件。](images/AzureLabs-Lab2-19.png)
 
2.  將 **球體** 重新命名為 **游標** (按兩下游標物件，或按下 [F2] 鍵盤按鈕並選取) 的物件，並確定它是位於 **主要攝影機** 的子系。

3.  在 [階層] *面板* 中，以滑鼠左鍵按一下 **游標**。 選取資料指標之後，請在 [偵測器] *面板* 中調整下列變數：

    1. 將 *轉換位置* 設定為 **0、0、5**
    2. 將 *刻度* 設定為 **0.02、0.02、0.02**

        ![更新轉換位置和小數位數。](images/AzureLabs-Lab2-20.png)
  
## <a name="chapter-4--setup-the-label-system"></a>第4章-設定標籤系統

一旦您已使用 HoloLens 的相機來取得映射，該映射將會傳送至您的 *Azure 電腦視覺 API* 服務實例進行分析。 

該分析的結果將會是已辨識的物件清單，稱為 **標記**。 

您將會使用標籤 (作為世界空間中的3D 文字) 在拍攝相片的位置顯示這些標記。

下列步驟將示範如何設定 **Label** 物件。

1.  以滑鼠右鍵按一下 [階層] 面板中的任何位置 (位置並不重要) 在 [ **3D 物件**] 下，加入 **3d 文字**。 將它命名為 **LabelText**。

    ![建立3D 文字物件。](images/AzureLabs-Lab2-21.png)
 
2.  在 [階層] *面板* 中，以滑鼠左鍵按一下 **LabelText**。 選取 **LabelText** 之後，在 [偵測 *器] 面板* 中調整下列變數：

    1. 將 **位置** 設定為 **0、0、0**
    2. 將 **刻度** 設定為 **0.01、0.01、0.01**
    3. 在元件 **文字網格** 中：
    4. 以 "..." 取代 **文字** 內的所有文字        
    5. 將 **錨點** 設定為 **中間中心**
    6. 將 **對齊方式** 設定為 **置** 中
    7. 將索引標籤 **大小** 設定為 **4**
    8. 將 **字型大小** 設定為 **50**
    9. 將 **色彩** 設定為 **#FFFFFFFF**

    ![文字元件](images/AzureLabs-Lab2-21-5.png)

3.  將 **LabelText** 從 [階層]*面板* 拖曳至 [*專案] 面板* 中的 [資產]*資料夾* 內。 這會使 **LabelText** 成為預製專案，讓它可以在程式碼中具現化。

    ![建立 LabelText 物件的預製專案。](images/AzureLabs-Lab2-22.png)
 
4.  您應該從 [階層]*面板* 中刪除 **LabelText** ，使其不會顯示在開啟的場景中。 因為它現在是預製專案，所以您會在 [資產] 資料夾中針對個別的實例呼叫，而不需要將其保留在場景中。 
5.  階層 *面板* 中的最後一個物件結構應如下圖所示：

    ![階層面板的最終結構。](images/AzureLabs-Lab2-23.png)

## <a name="chapter-5--create-the-resultslabel-class"></a>第5章-建立 ResultsLabel 類別

您需要建立的第一個腳本是 *ResultsLabel* 類別，負責下列各項： 

- 在適當的世界空間中建立標籤（相對於相機的位置）。
- 顯示影像擺脫中的標記。

若要建立此類別： 

1.  在 [ *專案] 面板* 中按一下滑鼠右鍵，然後 **建立 > 資料夾**。 將資料夾命名為 **腳本**。 

    ![建立腳本資料夾。](images/AzureLabs-Lab2-24.png)

2.  在 [ **腳本** ] 資料夾建立後，按兩下以開啟。 然後，在該資料夾中，以滑鼠右鍵按一下，然後選取 [ **建立] >** 然後選取 [ **c # 腳本**]。 將腳本命名為 *ResultsLabel*。 

3.  按兩下新的 *ResultsLabel* 腳本，以 **Visual Studio** 開啟。

4.  在類別中，將下列程式碼插入 *ResultsLabel* 類別中：

    ```csharp
        using System.Collections.Generic;
        using UnityEngine;

        public class ResultsLabel : MonoBehaviour
        {   
            public static ResultsLabel instance;

            public GameObject cursor;

            public Transform labelPrefab;

            [HideInInspector]
            public Transform lastLabelPlaced;

            [HideInInspector]
            public TextMesh lastLabelPlacedText;

            private void Awake()
            {
                // allows this instance to behave like a singleton
                instance = this;
            }

            /// <summary>
            /// Instantiate a Label in the appropriate location relative to the Main Camera.
            /// </summary>
            public void CreateLabel()
            {
                lastLabelPlaced = Instantiate(labelPrefab, cursor.transform.position, transform.rotation);

                lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();

                // Change the text of the label to show that has been placed
                // The final text will be set at a later stage
                lastLabelPlacedText.text = "Analysing...";
            }

            /// <summary>
            /// Set the Tags as Text of the last Label created. 
            /// </summary>
            public void SetTagsToLastLabel(Dictionary<string, float> tagsDictionary)
            {
                lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();

                // At this point we go through all the tags received and set them as text of the label
                lastLabelPlacedText.text = "I see: \n";

                foreach (KeyValuePair<string, float> tag in tagsDictionary)
                {
                    lastLabelPlacedText.text += tag.Key + ", Confidence: " + tag.Value.ToString("0.00 \n");
                }    
            }
        }
    ```

6.  返回 *Unity* 之前，請務必將您的變更儲存在 *Visual Studio* 中。
7.  返回 *Unity 編輯器* 中，按一下 [**腳本**] 資料夾中的 [ *ResultsLabel* ] 類別，並將其拖曳至 [階層]*面板* 中的 [**主要攝影機**] 物件。
8.  按一下 **主要攝影機** ，然後查看 [偵測 *器] 面板*。

您會發現，從您剛剛拖曳至相機的腳本中，有兩個欄位： **Cursor** 和 **Label 預製專案**。

9.  將名為 **cursor** 的物件從階層 *面板* 拖曳至名為 **cursor** 的位置，如下圖所示。
10. 從 [*專案] 面板* 中的 [*資產] 資料夾*，將名為 **LabelText** 的物件拖曳至名為 **Label 預製專案** 的位置，如下圖所示。 

    ![設定 Unity 中的參考目標。](images/AzureLabs-Lab2-25.png)

## <a name="chapter-6--create-the-imagecapture-class"></a>第6章-建立 ImageCapture 類別

您即將建立的下一個類別是 *ImageCapture* 類別。 此類別負責：

-   使用 HoloLens 攝影機來捕捉影像，並將它儲存在應用程式資料夾中。
-   捕獲使用者的點擊手勢。

若要建立此類別： 

1.  移至您先前建立的 **腳本** 資料夾。 
2.  以滑鼠右鍵按一下資料夾內的， **建立 > c # 腳本**。 呼叫腳本 *ImageCapture*。 
3.  按兩下新的 *ImageCapture* 腳本，以 **Visual Studio** 開啟。
4.  將下列命名空間新增至檔案頂端：

    ```csharp
        using System.IO;
        using System.Linq;
        using UnityEngine;
        using UnityEngine.XR.WSA.Input;
        using UnityEngine.XR.WSA.WebCam;
    ```

5.  然後，在 *ImageCapture* 類別內，于 *Start ()* 方法的上方新增下列變數：

    ```csharp
        public static ImageCapture instance; 
        public int tapsCount;
        private PhotoCapture photoCaptureObject = null;
        private GestureRecognizer recognizer;
        private bool currentlyCapturing = false;
    ```
 
**TapsCount** 變數會儲存從使用者所捕獲的點擊手勢數目。 此數位用於所捕捉的映射命名。

6.  現在需要新增 *喚醒 ()* 和 *啟動 ()* 方法的程式碼。 當類別初始化時，就會呼叫這些內容：

    ```csharp
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            instance = this;
        }

        void Start()
        {
            // subscribing to the HoloLens API gesture recognizer to track user gestures
            recognizer = new GestureRecognizer();
            recognizer.SetRecognizableGestures(GestureSettings.Tap);
            recognizer.Tapped += TapHandler;
            recognizer.StartCapturingGestures();
        }
    ```

7.  執行將在點一下手勢發生時呼叫的處理常式。 

    ```csharp
        /// <summary>
        /// Respond to Tap Input.
        /// </summary>
        private void TapHandler(TappedEventArgs obj)
        {
            // Only allow capturing, if not currently processing a request.
            if(currentlyCapturing == false)
            {
                currentlyCapturing = true;
            
                // increment taps count, used to name images when saving
                tapsCount++;

                // Create a label in world space using the ResultsLabel class
                ResultsLabel.instance.CreateLabel();

                // Begins the image capture and analysis procedure
                ExecuteImageCaptureAndAnalysis();
            }
        }
    ```
 
*TapHandler ()* 方法會遞增從使用者所捕獲的點擊次數，並使用目前的資料指標位置來決定新標籤的位置。

然後，這個方法會呼叫 *ExecuteImageCaptureAndAnalysis ()* 方法來開始此應用程式的核心功能。

8.  一旦捕獲並儲存映射之後，就會呼叫下列處理常式。 如果程式成功，則會將結果傳遞至 *VisionManager* (，但您尚未建立) 進行分析。

    ```csharp
        /// <summary>
        /// Register the full execution of the Photo Capture. If successful, it will begin 
        /// the Image Analysis process.
        /// </summary>
        void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
        {
            // Call StopPhotoMode once the image has successfully captured
            photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
        }

        void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
        {
            // Dispose from the object in memory and request the image analysis 
            // to the VisionManager class
            photoCaptureObject.Dispose();
            photoCaptureObject = null;
            StartCoroutine(VisionManager.instance.AnalyseLastImageCaptured()); 
        }
    ```
 
9.  然後新增應用程式用來啟動映射捕獲進程的方法，並儲存映射。

    ```csharp    
        /// <summary>    
        /// Begin process of Image Capturing and send To Azure     
        /// Computer Vision service.   
        /// </summary>    
        private void ExecuteImageCaptureAndAnalysis()  
        {    
            // Set the camera resolution to be the highest possible    
            Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending((res) => res.width * res.height).First();    

            Texture2D targetTexture = new Texture2D(cameraResolution.width, cameraResolution.height);
    
            // Begin capture process, set the image format    
            PhotoCapture.CreateAsync(false, delegate (PhotoCapture captureObject)    
            {    
                photoCaptureObject = captureObject;    
                CameraParameters camParameters = new CameraParameters();    
                camParameters.hologramOpacity = 0.0f;    
                camParameters.cameraResolutionWidth = targetTexture.width;    
                camParameters.cameraResolutionHeight = targetTexture.height;    
                camParameters.pixelFormat = CapturePixelFormat.BGRA32;
    
                // Capture the image from the camera and save it in the App internal folder    
                captureObject.StartPhotoModeAsync(camParameters, delegate (PhotoCapture.PhotoCaptureResult result)
                {    
                    string filename = string.Format(@"CapturedImage{0}.jpg", tapsCount);
    
                    string filePath = Path.Combine(Application.persistentDataPath, filename);

                    VisionManager.instance.imagePath = filePath;
    
                    photoCaptureObject.TakePhotoAsync(filePath, PhotoCaptureFileOutputFormat.JPG, OnCapturedPhotoToDisk);

                    currentlyCapturing = false;
                });   
            });    
        }
    ```
 
> [!WARNING] 
> 此時您會注意到 *Unity 編輯器主控台面板* 中出現錯誤。 這是因為程式碼會參考您將在下一章中建立的 *VisionManager* 類別。

## <a name="chapter-7--call-to-azure-and-image-analysis"></a>第7章-呼叫 Azure 和影像分析

您需要建立的最後一個腳本是 *VisionManager* 類別。 

此類別負責：

-   載入以位元組陣列形式捕獲的最新映射。
-   將位元組陣列傳送至您的 *Azure 電腦視覺 API* 服務實例以進行分析。
-   以 JSON 字串的形式接收回應。
-   將回應還原序列化，並將產生的標記傳遞至 *ResultsLabel* 類別。
 
若要建立此類別：

1.  按兩下 [ **腳本** ] 資料夾以開啟它。 
2.  在 [ **腳本** ] 資料夾內按一下滑鼠右鍵，然後按一下 [ **建立 > c # 腳本**]。 將腳本命名為 *VisionManager*。 
3.  按兩下新的腳本，以 Visual Studio 開啟。
4.  在 *VisionManager* 類別的頂端，將命名空間更新為與下列相同：

    ```csharp
        using System;
        using System.Collections;
        using System.Collections.Generic;
        using System.IO;
        using UnityEngine;
        using UnityEngine.Networking;
    ```
 
5.  在腳本頂端的 *VisionManager* 類別 *中*， (*開始 ()* 方法) 的上方，您現在需要建立兩個 *類別*，以代表來自 Azure 的已還原序列化 JSON 回應：

    ```csharp
        [System.Serializable]
        public class TagData
        {
            public string name;
            public float confidence;
        }

        [System.Serializable]
        public class AnalysedObject
        {
            public TagData[] tags;
            public string requestId;
            public object metadata;
        }
    ```

    > [!NOTE] 
    > *TagData* 和 *AnalysedObject* 類別必須在宣告之前新增 *[system.string]* 屬性，才能使用 Unity 程式庫將其還原序列化。

6.  在 VisionManager 類別中，您應該新增下列變數：

    ```csharp
        public static VisionManager instance;

        // you must insert your service key here!    
        private string authorizationKey = "- Insert your key here -";    
        private const string ocpApimSubscriptionKeyHeader = "Ocp-Apim-Subscription-Key";
        private string visionAnalysisEndpoint = "https://westus.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags";   // This is where you need to update your endpoint, if you set your location to something other than west-us.
  
        internal byte[] imageBytes;

        internal string imagePath;
    ```

    > [!WARNING] 
    > 請確定您將 **驗證金鑰** 插入 **authorizationKey** 變數中。 您將在本課程 [第1章](#chapter-1--the-azure-portal)的開頭注明您的 **驗證金鑰**。

    > [!WARNING] 
    > **VisionAnalysisEndpoint** 變數可能與此範例中指定的變數不同。 **美國西部** 絕對是指標對美國西部區域所建立的服務實例。 使用您的 [端點 URL](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa)來更新此值;以下是一些可能看起來像這樣的範例：
    > - 西歐： `https://westeurope.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`
    > - 東南亞： `https://southeastasia.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`
    > - 澳大利亞東部： `https://australiaeast.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`

7.  現在需要新增喚醒的程式碼。 

    ```csharp
        private void Awake()
        {
            // allows this instance to behave like a singleton
            instance = this;
        }
    ```

8.  接下來，新增協同程式 (，並在其底下的靜態資料流程方法) ，它會取得 ImageCapture 類別所之影像的分析結果。 

    ```csharp
        /// <summary>
        /// Call the Computer Vision Service to submit the image.
        /// </summary>
        public IEnumerator AnalyseLastImageCaptured()
        {
            WWWForm webForm = new WWWForm();
            using (UnityWebRequest unityWebRequest = UnityWebRequest.Post(visionAnalysisEndpoint, webForm))
            {
                // gets a byte array out of the saved image
                imageBytes = GetImageAsByteArray(imagePath);
                unityWebRequest.SetRequestHeader("Content-Type", "application/octet-stream");
                unityWebRequest.SetRequestHeader(ocpApimSubscriptionKeyHeader, authorizationKey);

                // the download handler will help receiving the analysis from Azure
                unityWebRequest.downloadHandler = new DownloadHandlerBuffer();

                // the upload handler will help uploading the byte array with the request
                unityWebRequest.uploadHandler = new UploadHandlerRaw(imageBytes);
                unityWebRequest.uploadHandler.contentType = "application/octet-stream";

                yield return unityWebRequest.SendWebRequest();

                long responseCode = unityWebRequest.responseCode;     

                try
                {
                    string jsonResponse = null;
                    jsonResponse = unityWebRequest.downloadHandler.text;

                    // The response will be in Json format
                    // therefore it needs to be deserialized into the classes AnalysedObject and TagData
                    AnalysedObject analysedObject = new AnalysedObject();
                    analysedObject = JsonUtility.FromJson<AnalysedObject>(jsonResponse);

                    if (analysedObject.tags == null)
                    {
                        Debug.Log("analysedObject.tagData is null");
                    }
                    else
                    {
                        Dictionary<string, float> tagsDictionary = new Dictionary<string, float>();

                        foreach (TagData td in analysedObject.tags)
                        {
                            TagData tag = td as TagData;
                            tagsDictionary.Add(tag.name, tag.confidence);                            
                        }

                        ResultsLabel.instance.SetTagsToLastLabel(tagsDictionary);
                    }
                }
                catch (Exception exception)
                {
                    Debug.Log("Json exception.Message: " + exception.Message);
                }

                yield return null;
            }
        }
    ```

    ```csharp
        /// <summary>
        /// Returns the contents of the specified file as a byte array.
        /// </summary>
        private static byte[] GetImageAsByteArray(string imageFilePath)
        {
            FileStream fileStream = new FileStream(imageFilePath, FileMode.Open, FileAccess.Read);
            BinaryReader binaryReader = new BinaryReader(fileStream);
            return binaryReader.ReadBytes((int)fileStream.Length);
        }  
    ```

9.  返回 *Unity* 之前，請務必將您的變更儲存在 *Visual Studio* 中。
10. 返回 Unity 編輯器中，按一下 [**腳本**] 資料夾中的 [ *VisionManager* ] 和 [ *ImageCapture* ] 類別，並將其拖曳至 [階層]*面板* 中的 [**主要攝影機**] 物件。 

## <a name="chapter-8--before-building"></a>第8章-建立之前

若要執行應用程式的完整測試，您必須將它側載到 HoloLens。
在執行之前，請確定：

-   [第2章](#chapter-2--set-up-the-unity-project)中所述的所有設定都已正確設定。 
-   所有的腳本都會附加至 **主要攝影機** 物件。 
-   *主要相機偵測器面板* 中的所有欄位都已正確指派。
-   請確定您將 **驗證金鑰** 插入 **authorizationKey** 變數中。
-   確定您也已在 *VisionManager* 腳本中檢查您的端點，且該端點符合 *您* 的區域 (本檔預設會使用 *美國西部*) 。

## <a name="chapter-9--build-the-uwp-solution-and-sideload-the-application"></a>第9章–建立 UWP 解決方案並側載應用程式
此專案的 Unity 區段所需的所有專案現在都已完成，因此您可以從 Unity 建立它。

1.  流覽至 *組建* 配置  -  **檔案 > 組建設定 ...**
2.  從 [ *組建設定* ] 視窗中，按一下 [ **建立**]。

    ![從 Unity 建立應用程式](images/AzureLabs-Lab2-26.png)

3.  如果尚未這麼做，請勾選 **Unity c # 專案**。
4.  按一下 [建置]。 Unity 將會啟動一個 *檔案總管* 視窗，您需要在其中建立並選取要用來建立應用程式的資料夾。 立即建立該資料夾，並命名為 *應用程式*。 然後選取 [ *應用程式* ] 資料夾，然後按 [ **選取資料夾**]。 
5.  Unity 將開始將您的專案建立到 *應用程式* 資料夾。 
6.  Unity 完成組建之後 (可能需要一些時間) ，它會在您的組建位置開啟 *檔案總管* 視窗 (檢查您的工作列，因為它不一定會出現在您的視窗上方，但會通知您加入新的視窗) 。

## <a name="chapter-10--deploy-to-hololens"></a>第10章–部署到 HoloLens

若要在 HoloLens 上部署：

1.  您將需要 HoloLens (的 IP 位址，才能進行遠端部署) ，並確保 HoloLens 處於 **開發人員模式**。 若要這樣做：

    1. 在設置 HoloLens 的同時，開啟 **設定**。
    2. 前往 **Network & Internet > Wi-Fi > Advanced Options**
    3. 記下 **IPv4** 位址。
    4. 接下來，流覽回到 [ **設定**]，然後 **更新開發人員 & 的安全性 >** 
    5. 設定 [開發人員模式]。

2.  流覽至您的新 Unity 組建 (*應用程式* 資料夾) ，然後以 *Visual Studio* 開啟方案檔。
3.  在 [方案設定] 中選取 [ **Debug**]。
4.  在解決方案平臺中，選取 [ **x86**]、[ **遠端電腦**]。 

    ![從 Visual Studio 部署方案。](images/AzureLabs-Lab2-27.png)
 
5.  移至 [ **組建] 功能表** ，然後按一下 [ **部署方案**]，將應用程式側載至 HoloLens。
6.  您的應用程式現在應該會出現在 HoloLens 上已安裝的應用程式清單中，準備好可供啟動！

> [!NOTE]
> 若要部署到沉浸式耳機，請將 **解決方案平臺****設定為 [** *本機電腦*]，並將 [設定] 設定為 [以 *x86* 作為 **平臺**] 來進行 *Debug*。 然後使用 [ **組建] 功能表** 選取 [ *部署方案*]，部署到本機電腦。 

## <a name="your-finished-computer-vision-api-application"></a>您完成的電腦視覺 API 應用程式

恭喜，您已建立混合的現實應用程式，利用 Azure 電腦視覺 API 來辨識真實世界物件，並顯示已看到內容的可信度。

![實驗室結果](images/AzureLabs-Lab2-000.png)

## <a name="bonus-exercises"></a>額外練習

### <a name="exercise-1"></a>練習1

就像您在 *VisionManager*) 內使用的 *端點* 中使用 *標記* 參數 (為證明，請擴充應用程式以偵測其他資訊;看看您在 [這裡](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa)可以存取的其他參數。

### <a name="exercise-2"></a>練習2

以更有對話、更容易閱讀的方式來顯示傳回的 Azure 資料，或許隱藏了數位。 如同 bot 可能對使用者說話。