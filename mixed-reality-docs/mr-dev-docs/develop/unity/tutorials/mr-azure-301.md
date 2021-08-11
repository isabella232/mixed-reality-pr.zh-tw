---
title: HoloLens (第1代) 和 Azure 301-語言轉譯
description: 完成本課程，以瞭解如何在混合現實應用程式內執行 Azure 翻譯工具文字 API。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure，mixed reality，學術，unity，教學課程，api，翻譯工具文字、hololens、沉浸式、vr、語言翻譯、Windows 10、Visual Studio
ms.openlocfilehash: 8eeeab45c6e7d93c1b04afa4db811f220b0c2f9c85400fc93a81ac413164a6b7
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2021
ms.locfileid: "115229510"
---
# <a name="hololens-1st-gen-and-azure-301-language-translation"></a>HoloLens (第1代) 和 Azure 301：語言轉譯

<br>

>[!NOTE]
>混合實境學院教學課程的設計是以 HoloLens (第 1 代) 和混合實境沉浸式頭戴裝置為準。  因此，對於仍在尋找這些裝置開發指引的開發人員而言，我們覺得這些教學課程很重要。  這些教學課程 **_不會_** 使用用於 HoloLens 2 的最新工具組或互動進行更新。  系統會保留這些資訊，以繼續在支援的裝置上運作。 未來將會有一系列新的教學課程，將會示範如何針對 HoloLens 2 進行開發。  當張貼這些教學課程時，將會使用這些教學課程的連結來更新此通知。

<br>

在此課程中，您將瞭解如何使用 Azure 認知服務搭配翻譯工具文字 API，將翻譯功能新增至混合現實應用程式。

![最終產品](images/AzureLabs-Lab1-00.png)

翻譯工具文字 API 是一種可近乎即時運作的轉譯服務。 服務是以雲端為基礎，且使用 REST API 呼叫，應用程式可以使用類神經機器翻譯技術，將文字翻譯成另一種語言。 如需詳細資訊，請造訪[Azure 翻譯工具文字 API 頁面](https://azure.microsoft.com/services/cognitive-services/translator-text-api/)。

完成本課程之後，您將會有一個混合現實應用程式，可以執行下列動作：

1.  使用者會說到連接到沉浸式 (VR) 耳機 (或 HoloLens) 內建麥克風的麥克風。
2.  應用程式將會捕捉聽寫，並將其傳送至 Azure 翻譯工具文字 API。
3.  轉譯結果將會顯示在 Unity 場景的簡單 UI 群組中。

本課程將告訴您如何將翻譯工具服務的結果取得 Unity 型範例應用程式。 您必須將這些概念套用至您可能正在建立的自訂應用程式。

## <a name="device-support"></a>裝置支援

<table>
<tr>
<th>課程</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">沉浸式頭戴裝置</a></th>
</tr><tr>
<td> MR 和 Azure 301：語言翻譯</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> 雖然本課程主要著重于 Windows Mixed Reality 沉浸式 (VR) 耳機，您也可以將在本課程中學到的內容套用至 Microsoft HoloLens。 當您依照課程的指示進行時，您將會看到有關您可能需要採用以支援 HoloLens 的任何變更注意事項。 使用 HoloLens 時，您可能會注意到語音捕捉期間的一些回應。

## <a name="prerequisites"></a>必要條件

> [!NOTE]
> 本教學課程是專為擁有 Unity 和 c # 基本經驗的開發人員所設計。 另外也請注意，本檔中的必要條件和撰寫的指示，代表在撰寫 (可能是 2018) 時經過測試和驗證的內容。 You are free to use the latest software, as listed within the [install the tools](../../install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.

本課程建議您採用下列硬體和軟體：

- 開發電腦，與適用于沉浸式 (VR) 耳機開發的[Windows Mixed Reality 相容](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines)
- [啟用開發人員模式的 Windows 10 Fall Creators Update (或更新版本) ](../../install-the-tools.md#installation-checklist)
- [最新的 Windows 10 SDK](../../install-the-tools.md#installation-checklist)
- [Unity 2017。4](../../install-the-tools.md#installation-checklist)
- [Visual Studio 2017](../../install-the-tools.md#installation-checklist)
- [Windows Mixed Reality 沉浸式 (VR) 耳機](../../../discover/immersive-headset-hardware-details.md)，或已啟用開發人員模式的[Microsoft HoloLens](/hololens/hololens1-hardware)
- 一組具有內建麥克風的耳機 (如果耳機沒有內建的 mic 和喇叭) 
- 適用于 Azure 設定和轉譯抓取的網際網路存取

## <a name="before-you-start"></a>在您開始使用 Intune 之前

- 為了避免在建立此專案時發生問題，強烈建議您在根或近端根資料夾中，建立本教學課程中所述的專案 (長的資料夾路徑可能會在組建階段) 時發生問題。
- 本教學課程中的程式碼可讓您從連接到您電腦的預設麥克風裝置記錄。 請確定預設的麥克風裝置已設定為您打算用來捕捉聲音的裝置。
- 若要允許您的電腦啟用聽寫，請移至 **設定 > 隱私權 > 語音，筆墨 & 輸入**，然後選取 [**開啟語音服務] 和 [輸入建議**] 按鈕。
- 如果您使用連接到 (或內建的麥克風和耳機) 耳機，請在設定中開啟 [當我磨損耳機時，切換到耳機 mic] 選項， **> 混合現實 > 音訊和語音**。

   ![混合現實設定](images/AzureLabs-Lab1-00-5.png)

   ![麥克風設定](images/AzureLabs-Lab1-01.png)

> [!WARNING]
> 請注意，如果您正在開發此實驗室的沉浸式耳機，您可能會遇到音訊輸出裝置問題。 這是因為 Unity 的問題，在較新版 Unity (Unity 2018.2) 中已修正。 此問題會防止 Unity 在執行時間變更預設音訊輸出裝置。 因應措施是，請確定您已完成上述步驟，並在此問題呈現時，關閉並重新開啟編輯器。

## <a name="chapter-1--the-azure-portal"></a>第1章-Azure 入口網站

若要使用 Azure 翻譯工具 API，您必須將服務的實例設定為可供應用程式使用。

1.  登入  [Azure 入口網站](https://portal.azure.com)。

    > [!NOTE]
    > 如果您還沒有 Azure 帳戶，您將需要建立一個帳戶。 如果您在課堂或實驗室的情況下進行本教學課程，請洽詢講師或其中一個 proctors，協助您設定新的帳戶。

2.  登入後，按一下左上角的 [**新增**]，並搜尋「翻譯工具文字 API」。 選取 **Enter**。

    ![新增資源](images/AzureLabs-Lab1-02.png)

    > [!NOTE]
    > 在較新的入口網站中，[**建立資源**] 可能已取代 **新** 的文字。

3.  新頁面將提供 *翻譯工具文字 API* 服務的描述。 在此頁面的左下方，選取 [ **建立** ] 按鈕，以建立與此服務的關聯。

    ![建立翻譯工具文字 API 服務](images/AzureLabs-Lab1-03.png)

4.  當您按一下 [ **建立**] 之後：

    1. 為此服務實例插入您想要的 **名稱** 。
    2. 選取適當的 **訂** 用帳戶。
    3. 選取適合您的 **定價層**，如果這是您第一次建立 *翻譯工具文字服務*，則應可使用名為 F0) 的免費層 (。
    4. 選擇資源群組，或建立一個新的 **資源群組** 。 資源群組提供一種方式來監視、控制存取、布建及管理 Azure 資產集合的計費。 建議您保留與單一專案相關聯的所有 Azure 服務 (例如，) 一般資源群組下的實驗室，) 。

        > 如果您想要閱讀更多有關 Azure 資源群組的資訊，請 [造訪資源群組文章](/azure/azure-resource-manager/resource-group-portal)。

    5. 如果您要建立新的資源群組) ，請判斷資源群組 (的 **位置** 。 位置最好是在應用程式執行所在的區域中。 某些 Azure 資產僅適用于某些區域。
    6. 您也必須確認您已瞭解套用到此服務的條款及條件。
    7. 選取 [建立]  。

        ![選取 [建立] 按鈕。](images/AzureLabs-Lab1-04.png)

5.  當您按一下 [ **建立**] 之後，就必須等待服務建立完成，這可能需要一分鐘的時間。
6.  建立服務實例之後，入口網站中就會出現通知。 

    ![Azure 服務建立通知](images/AzureLabs-Lab1-05.png)

7.  按一下通知以探索新的服務實例。 

    ![移至 [資源] 快顯視窗。](images/AzureLabs-Lab1-06.png)

8.  按一下通知中的 [ **移至資源** ] 按鈕，以流覽您的新服務實例。 您將會進入新的翻譯工具文字 API 服務實例。 

    ![翻譯工具文字 API 服務頁面](images/AzureLabs-Lab1-07.png)

9.  在本教學課程中，您的應用程式將需要呼叫您的服務，這是透過使用服務的訂用帳戶金鑰來完成。 
10. 在 *翻譯工具文字* 服務的 [*快速入門*] 頁面中，流覽至第一個步驟、*抓取您的金鑰*，然後按一下 [機 **碼**] (您也可以按一下位於 [服務] 導覽功能表中，以按鍵圖示) 表示的藍色超連結鍵來達成此目的。 這會顯示您的服務 *金鑰*。
11. 複製其中一個顯示的金鑰，您稍後會在專案中使用。 

## <a name="chapter-2--set-up-the-unity-project"></a>第2章-設定 Unity 專案

設定及測試您的混合現實沉浸式耳機。

> [!NOTE]
> 在此課程中，您將不需要移動控制器。 如果您需要設定沉浸式耳機的支援，請 [遵循下列步驟](https://support.microsoft.com/help/4043101/windows-10-set-up-windows-mixed-reality)。

以下是使用 mixed reality 進行開發的一般設定，因此，它是適用于其他專案的良好範本：

1.  開啟 *Unity* ，然後按一下 [ **新增**]。 

    ![開始新的 Unity 專案。](images/AzureLabs-Lab1-08.png)

2.  現在您將需要提供 Unity Project 名稱。 插入 **MR_Translation**。 請確定專案類型設定為 **3d**。 將 *位置* 設定為適合您 (記住，較接近根目錄的) 。 然後，按一下 [ **建立專案**]。

    ![提供新 Unity 專案的詳細資料。](images/AzureLabs-Lab1-09.png)

3.  在 Unity 開啟的情況下，值得檢查預設 **腳本編輯器** 是否設定為 **Visual Studio**。 移至 [ **編輯] > 喜好** 設定，然後在新視窗中，流覽至 [ **外部工具**]。 將 **外部腳本編輯器** 變更為 **Visual Studio 2017**。 關閉 [ **喜好** 設定] 視窗。

    ![更新腳本編輯器喜好設定。](images/AzureLabs-Lab1-10.png)

4.  接下來，移至 [檔案 **> 建立設定**]，然後按一下 [**切換平臺**] 按鈕，將平臺切換至 **通用 Windows 平臺**。

    ![建立設定視窗、將平臺切換至 UWP。](images/AzureLabs-Lab1-11.png)

5.  移至 [檔案 **> 組建設定** 並確定：

    1. **目標裝置** 設定為 **任何裝置**。

        > 針對 Microsoft HoloLens，請將 **目標裝置** 設定為 *HoloLens*。

    2. **組建類型** 設定為 **D3D**
    3. **SDK** 已設定為 **最新安裝**
    4. **Visual Studio 版本** 設定為 **最新安裝**
    5. **組建並執行** 設定為 **本機電腦**
    6. 儲存場景，並將其新增至組建。

        1. 若要這麼做，請選取 [ **新增開啟的場景**]。 [儲存] 視窗隨即出現。

            ![按一下 [新增開啟場景] 按鈕](images/AzureLabs-Lab1-12.png)

        2. 為此和任何未來的場景建立新的資料夾，然後選取 [ **新增資料夾** ] 按鈕，建立新的資料夾，將它命名為 **場景**。

            ![建立新的腳本資料夾](images/AzureLabs-Lab1-13.png)

        3. 開啟新建立的 **場景** 資料夾，然後在 [ *檔案名*：文字] 欄位中輸入 **MR_TranslationScene**，然後按 [ **儲存**]。

            ![提供新場景的名稱。](images/AzureLabs-Lab1-14.png)

            > 請注意，您必須將 Unity 場景儲存在 [*資產*] 資料夾中，因為它們必須與 Unity Project 相關聯。 建立幕後資料夾 (和其他類似的資料夾) 是結構化 Unity 專案的典型方式。

    7. [*組建設定*] 中的其餘設定，現在應該保持為預設值。

6. 在 [*組建設定*] 視窗中，按一下 [播放程式]**設定** 按鈕，這會開啟偵測 *器* 所在空間中的相關面板。 

    ![開啟 [播放玩家設定]。](images/AzureLabs-Lab1-15.png)

7. 在此面板中，需要驗證幾個設定：

    1. 在 [**其他設定**] 索引標籤中：

        1. **腳本執行階段版本** 應該是 **穩定** 的 ( .net 3.5 對等) 。
        2. **腳本後端** 應該是 **.net**
        3. **API 相容性層級** 應為 **.net 4.6**

            ![更新其他設定。](images/AzureLabs-Lab1-16.png)
      
    2. 在 [**發行設定**] 索引標籤的 [**功能**] 下，選取：

        1. **InternetClient**
        2. **麥克風**

            ![正在更新發行設定。](images/AzureLabs-Lab1-17.png)

    3. 接下來的面板中，在 **XR 設定** (的 [**發佈設定**) ]、[滴答 **虛擬實境支援**]，請確定已新增 **Windows Mixed Reality SDK** 。

        ![更新 X R 設定。](images/AzureLabs-Lab1-18.png)

8.  回到 **Build 設定**， *Unity c # 專案* 不再呈現灰色;勾選此方塊旁邊的核取方塊。 
9.  關閉 [建置設定] 視窗。
10. 儲存場景並 Project (檔 **> 儲存場景/檔案 > 儲存專案**) 。

## <a name="chapter-3--main-camera-setup"></a>第3章-主要攝影機設定

> [!IMPORTANT]
> 如果您想要略過此課程的 *Unity 設定* 元件，並直接繼續進行程式碼，請隨意 [下載 unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20301%20-%20Language%20translation/Azure-MR-301.unitypackage)，並將其匯入到您的專案中做為 [*自訂套件*](https://docs.unity3d.com/Manual/AssetPackages.html)，然後繼續進行 [第5章](#chapter-5--create-the-results-class)。 您仍然需要建立 Unity Project。

1.  在 [階層] *面板* 中，您會找到一個稱為「 **主要攝影機**」的物件，此物件代表您在應用程式「內」之後的「頭部」觀點。
2.  使用 Unity 儀表板，選取 **主要攝影機 GameObject**。 您將會注意到，在儀錶) 板內 (的 [偵測 *器] 面板* 通常會顯示該 *GameObject* 的各種元件，並在頂端、*相機* 和一些其他元件中顯示 *轉換*。 您必須重設主要攝影機的轉換，才能正確定位。
3.  若要這樣做，請選取相機 *轉換* 元件旁邊的 **齒輪** 圖示，然後選取 [**重設**]。 

    ![重設主要相機轉換。](images/AzureLabs-Lab1-19.png)
 
4.  接著， *轉換* 元件看起來應該像這樣：

    1. 此 *位置* 設定為 **0、0、0**
    2. *旋轉* 設定為 **0、0、0**
    3. 和 *小* 數位數設定為 **1，1，1**

        ![相機的轉換資訊](images/AzureLabs-Lab1-20.png)

5.  接下來，選取 [**主要攝影機**] 物件，然後在 [偵測 *器] 面板* 的最下方，查看 [**新增元件**] 按鈕。 
6.  選取該按鈕，然後在 [搜尋] 欄位中輸入 *音訊來源* 來搜尋 (，或如下所示，流覽稱為 **音訊來源** 的元件) 的區段，並選取它 (在其上按下 enter 鍵也可以) 。
7.  *音訊來源* 元件將會新增至 **主要攝影機**，如下所示。

    ![新增音訊來源元件。](images/AzureLabs-Lab1-21.png)

    > [!NOTE]
    > 針對 Microsoft HoloLens，您也必須變更下列內容，這是您 **主要攝影機** 上 **相機** 元件的一部分：
    > - **清除旗標：** 純色。
    > - **背景** ' 黑色，Alpha 0 ' –十六進位色彩： #00000000。

## <a name="chapter-4--setup-debug-canvas"></a>第4章-設定偵錯工具畫布

若要顯示翻譯的輸入和輸出，必須建立基本的 UI。 在此課程中，您將建立畫布 UI 物件，其中包含數個「文字」物件來顯示資料。

1.  以滑鼠右鍵按一下 [階層] *面板* 的空白區域，然後在 [ **UI**] 下加入 **畫布**。

    ![加入新的畫布 UI 物件。](images/AzureLabs-Lab1-22.png)

2.  選取畫布物件之後，在 [偵測 *器] 面板* 中 () 的 [畫布] 元件內，將轉譯模式變更為 [**世界空間** **]** 。 
3.  接下來，在 [偵測器] *面板的 Rect 轉換* 中變更下列參數：

    1. *POS*  -  **X** 0 **Y** 0 **Z** 40
    2. *寬度* -500
    3. *高度* -300
    4. *調整規模*  - **X** 0.13 **Y** 0.13 **Z** 0.13

        ![更新畫布的 rect 轉換。](images/AzureLabs-Lab1-23.png)
 
4.  以滑鼠右鍵按一下 [階層]*面板* 中 [ **UI**] 下的 **畫布**，然後新增 **面板**。 此 **面板** 會提供您將在場景中顯示之文字的背景。
5.  以滑鼠右鍵按一下 [階層]*面板* 中 [ **UI**] 下的 **面板**，然後新增 **文字物件**。 重複相同的程式，直到您已在 total (提示中建立四個 UI 文字物件為止：如果您已選取第一個 ' Text ' 物件，只要按下 **Ctrl + '**，即可複製它，直到總) 中有四個為止。 
6.  針對每個 **文字物件** 選取它，並使用下表在 [偵測 *器] 面板* 中設定參數。

    1. 若為 *Rect 轉換* 元件：

        | Name                   | 轉換- *位置*             | 寬度      | 高度    |
        |:----------------------:|:----------------------------------:|:----------:|:---------:|
        | MicrophoneStatusLabel  | **X** -80 **Y** 90 **Z** 0         | 300        | 30        |
        | AzureResponseLabel     | **X** -80 **Y** 30 **Z** 0         | 300        | 30        |
        | DictationLabel         | **X** -80 **Y** -30 **Z** 0        | 300        | 30        |
        | TranslationResultLabel | **X** -80 **Y** -90 **Z** 0        | 300        | 30        |


    2. 針對 **(腳本)** 元件的文字：


        | Name                   | Text               | 字型大小    |
        |:----------------------:|:------------------:|:------------:|
        | MicrophoneStatusLabel  | 麥克風狀態： | 20           |
        | AzureResponseLabel     | Azure Web 回應 | 20           |
        | DictationLabel         |   您剛才說過：   | 20           |
        | TranslationResultLabel |    轉譯：    | 20           |

        ![輸入 UI 標籤的對應值。](images/AzureLabs-Lab1-24.png)

    3. 此外，將字型樣式設為 **粗體**。 這樣可讓文字更容易閱讀。

        ![粗體字型。](images/AzureLabs-Lab1-25.png)

7.  針對 [第5章](#chapter-5--create-the-results-class)所建立的每個 *UI 文字物件*，建立新的 *子* **ui 文字物件**。 這些子系會顯示應用程式的輸出。 以滑鼠右鍵按一下您想要的父系 (（例如 *MicrophoneStatusLabel*) 然後選取 [ **UI** ]，然後選取 [**文字**]，以建立 *子* 物件。
8.  針對每個子系選取它，並使用下表在 [偵測器] 面板中設定參數。

    1. 若為 **Rect 轉換** 元件：

        | Name                  | 轉換- *位置* | 寬度      | 高度    |
        |:---------------------:|:----------------------:|:----------:|:---------:|
        | MicrophoneStatusText  | X 0 Y-30 Z 0          | 300        | 30        |
        | AzureResponseText     | X 0 Y-30 Z 0          | 300        | 30        |
        | DictationText         | X 0 Y-30 Z 0          | 300        | 30        |
        | TranslationResultText | X 0 Y-30 Z 0          | 300        | 30        |

    2. 針對 **(腳本)** 元件的文字：

        | Name                  | Text          | 字型大小    |
        |:---------------------:|:-------------:|:------------:|
        | MicrophoneStatusText  |      ??       | 20           |
        | AzureResponseText     |      ??       | 20           |
        | DictationText         |      ??       | 20           |
        | TranslationResultText |      ??       | 20           |

9. 接下來，選取每個文字元件的「中心」對齊選項：

    ![對齊文字。](images/AzureLabs-Lab1-26.png)

10. 若要確保 **子 UI 文字** 物件可以輕易讀取，請變更其 *色彩*。 若要這麼做，請按一下 [ *色彩*] 旁邊 (目前為 [黑色] ) 的橫條。 

    ![輸入 UI 文字輸出的對應值。](images/AzureLabs-Lab1-27.png)
 
11. 然後，在 [新增]、[小]、[ *色彩* ] 視窗中，將 [ *十六進位色彩* ] 變更為： **0032EAFF**

    ![將色彩更新為藍色。](images/AzureLabs-Lab1-28.png)
 
12. 以下是 **UI** 的外觀。
    1.  在 [階層] *面板* 中：

        ![具有提供之結構中的階層。](images/AzureLabs-Lab1-29.png)

    2.  在 *場景* 和 *遊戲視圖* 中：

        ![讓場景和遊戲視圖位於相同的結構中。](images/AzureLabs-Lab1-30.png)

## <a name="chapter-5--create-the-results-class"></a>第5章-建立結果類別

您需要建立的第一個腳本是「 *結果* 」類別，其負責提供查看轉譯結果的方式。 類別會儲存並顯示下列內容： 

- Azure 的回應結果。
- 麥克風狀態。 
- 聽寫 (語音文字) 的結果。
- 轉譯的結果。

若要建立此類別： 

1.  在 *Project 面板* 中按一下滑鼠右鍵，然後 **建立 > 資料夾**。 將資料夾命名為 **腳本**。 
 
    ![建立腳本資料夾。](images/AzureLabs-Lab1-31.png)

    ![開啟 [腳本] 資料夾。](images/AzureLabs-Lab1-32.png)
 
2.  在 [ **腳本** ] 資料夾建立後，按兩下以開啟。 然後，在該資料夾中，以滑鼠右鍵按一下，然後選取 [ **建立] >** 然後選取 [ **c # 腳本**]。 將腳本命名為 *結果*。 

    ![建立第一個腳本。](images/AzureLabs-Lab1-33.png)
 
3.  按兩下新的 *結果* 腳本，以 **Visual Studio** 開啟。
4.  插入下列命名空間：

    ```cs
        using UnityEngine;
        using UnityEngine.UI;
    ```

5.  在類別內插入下列變數：

    ```cs
        public static Results instance;
   
        [HideInInspector] 
        public string azureResponseCode;
   
        [HideInInspector] 
        public string translationResult;
   
        [HideInInspector] 
        public string dictationResult;
   
        [HideInInspector] 
        public string micStatus;
   
        public Text microphoneStatusText;
   
        public Text azureResponseText;
   
        public Text dictationText;
   
        public Text translationResultText;
    ```

6.  然後新增 *喚醒的 ()* 方法，當類別初始化時，就會呼叫這個方法。 

    ```csharp
        private void Awake() 
        { 
            // Set this class to behave similar to singleton 
            instance = this;           
        } 
    ```

7.  最後，新增負責將各種結果資訊輸出至 UI 的方法。 

    ```csharp
        /// <summary>
        /// Stores the Azure response value in the static instance of Result class.
        /// </summary>
        public void SetAzureResponse(string result)
        {
            azureResponseCode = result;
            azureResponseText.text = azureResponseCode;
        }
   
        /// <summary>
        /// Stores the translated result from dictation in the static instance of Result class. 
        /// </summary>
        public void SetDictationResult(string result)
        {
            dictationResult = result;
            dictationText.text = dictationResult;
        }
   
        /// <summary>
        /// Stores the translated result from Azure Service in the static instance of Result class. 
        /// </summary>
        public void SetTranslatedResult(string result)
        {
            translationResult = result;
            translationResultText.text = translationResult;
        }
   
        /// <summary>
        /// Stores the status of the Microphone in the static instance of Result class. 
        /// </summary>
        public void SetMicrophoneStatus(string result)
        {
            micStatus = result;
            microphoneStatusText.text = micStatus;
        }
    ```

8.  返回 *Unity* 之前，請務必將您的變更儲存在 *Visual Studio* 中。

## <a name="chapter-6--create-the-microphonemanager-class"></a>第6章-建立 *MicrophoneManager* 類別

您即將建立的第二個類別是 *MicrophoneManager*。

此類別負責：

- 偵測連接到耳機或電腦的錄製裝置 (以預設) 為准。
- 捕捉音訊 (語音) 並使用聽寫將其儲存為字串。
- 聲音暫停之後，請將聽寫提交至翻譯工具類別。
- 裝載可在需要時停止語音捕捉的方法。

若要建立此類別： 
1.  按兩下 [ **腳本** ] 資料夾以開啟它。 
2.  在 [ **腳本** ] 資料夾內按一下滑鼠右鍵，然後按一下 [ **建立 > c # 腳本**]。 將腳本命名為 *MicrophoneManager*。 
3.  按兩下新的腳本，以 Visual Studio 開啟。
4.  在 *MicrophoneManager* 類別的頂端，將命名空間更新為與下列相同：

    ```csharp
        using UnityEngine; 
        using UnityEngine.Windows.Speech;
    ```

5.  然後，在 *MicrophoneManager* 類別內新增下列變數：

    ```csharp
        // Help to access instance of this object 
        public static MicrophoneManager instance; 
     
        // AudioSource component, provides access to mic 
        private AudioSource audioSource; 
   
        // Flag indicating mic detection 
        private bool microphoneDetected; 
   
        // Component converting speech to text 
        private DictationRecognizer dictationRecognizer; 
    ```

6.  現在需要新增 *喚醒 ()* 和 *啟動 ()* 方法的程式碼。 當類別初始化時，就會呼叫這些內容：

    ```csharp
        private void Awake() 
        { 
            // Set this class to behave similar to singleton 
            instance = this; 
        } 
    
        void Start() 
        { 
            //Use Unity Microphone class to detect devices and setup AudioSource 
            if(Microphone.devices.Length > 0) 
            { 
                Results.instance.SetMicrophoneStatus("Initialising..."); 
                audioSource = GetComponent<AudioSource>(); 
                microphoneDetected = true; 
            } 
            else 
            { 
                Results.instance.SetMicrophoneStatus("No Microphone detected"); 
            } 
        } 
    ```

7.  您可以 *刪除**更新 ()* 方法，因為此類別不會使用它。
8.  現在您需要應用程式用來啟動和停止語音捕捉的方法，並將它傳遞給 *翻譯工具* 類別，您很快就會建立這些方法。 複製下列程式碼，並將它貼到 *Start ()* 方法底下。

    ```csharp
        /// <summary> 
        /// Start microphone capture. Debugging message is delivered to the Results class. 
        /// </summary> 
        public void StartCapturingAudio() 
        { 
            if(microphoneDetected) 
            {               
                // Start dictation 
                dictationRecognizer = new DictationRecognizer(); 
                dictationRecognizer.DictationResult += DictationRecognizer_DictationResult; 
                dictationRecognizer.Start(); 
    
                // Update UI with mic status 
                Results.instance.SetMicrophoneStatus("Capturing..."); 
            }      
        } 
 
        /// <summary> 
        /// Stop microphone capture. Debugging message is delivered to the Results class. 
        /// </summary> 
        public void StopCapturingAudio() 
        { 
            Results.instance.SetMicrophoneStatus("Mic sleeping"); 
            Microphone.End(null); 
            dictationRecognizer.DictationResult -= DictationRecognizer_DictationResult; 
            dictationRecognizer.Dispose(); 
        }
    ```

    > [!TIP]
    > 雖然此應用程式不會使用它，但如果您想要在應用程式中執行停止捕獲音訊的能力，也可以在這裡提供 *StopCapturingAudio ()* 方法。

9.  您現在需要加入語音停止時將叫用的聽寫處理常式。 然後，這個方法會將聽寫的文字傳遞給 *翻譯工具* 類別。

    ```csharp
        /// <summary>
        /// This handler is called every time the Dictation detects a pause in the speech. 
        /// Debugging message is delivered to the Results class.
        /// </summary>
        private void DictationRecognizer_DictationResult(string text, ConfidenceLevel confidence)
        {
            // Update UI with dictation captured
            Results.instance.SetDictationResult(text);
   
            // Start the coroutine that process the dictation through Azure 
            StartCoroutine(Translator.instance.TranslateWithUnityNetworking(text));   
        }
    ```

10. 返回 Unity 之前，請務必將您的變更儲存在 Visual Studio 中。

> [!WARNING]  
> 此時您會注意到 *Unity 編輯器主控台* 面板中出現錯誤 ( 「名稱 ' 翻譯工具 ' 不存在 ...」 ) 。 這是因為程式碼會參考您將在下一章中建立的 *翻譯工具* 類別。

## <a name="chapter-7--call-to-azure-and-translator-service"></a>第7章-對 Azure 和 translator service 的呼叫

您需要建立的最後一個腳本是 *翻譯工具* 類別。 

此類別負責：

-   使用 *Azure* 在 **驗證權杖** 的 Exchange 中驗證應用程式。
-   使用 **驗證權杖** 來提交從 *MicrophoneManager* 類別收到的文字 (要翻譯) 。
-   接收翻譯的結果，並將其傳遞至要在 UI 中視覺化的 *結果* 類別。

若要建立此類別： 
1.  移至您先前建立的 **腳本** 資料夾。 
2.  在 **Project 面板** 中按一下滑鼠右鍵，**建立 > c # 腳本**。 呼叫腳本 *翻譯工具*。
3.  按兩下新的 *翻譯工具* 腳本，以 **Visual Studio** 開啟。
4.  將下列命名空間新增至檔案頂端：

    ```csharp
        using System;
        using System.Collections;
        using System.Xml.Linq;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

5.  然後，在 *翻譯工具* 類別內新增下列變數：

    ```csharp
        public static Translator instance; 
        private string translationTokenEndpoint = "https://api.cognitive.microsoft.com/sts/v1.0/issueToken"; 
        private string translationTextEndpoint = "https://api.microsofttranslator.com/v2/http.svc/Translate?"; 
        private const string ocpApimSubscriptionKeyHeader = "Ocp-Apim-Subscription-Key"; 
    
        //Substitute the value of authorizationKey with your own Key 
        private const string authorizationKey = "-InsertYourAuthKeyHere-"; 
        private string authorizationToken; 
    
        // languages set below are: 
        // English 
        // French 
        // Italian 
        // Japanese 
        // Korean 
        public enum Languages { en, fr, it, ja, ko }; 
        public Languages from = Languages.en; 
        public Languages to = Languages.it; 
    ```

    > [!NOTE]
    > - 插入語言 **列舉** 的語言只是範例。 如果您想要的話，可以隨意新增更多; [API 支援60種以上的語言](/azure/cognitive-services/translator/languages) (包括克林貢) ！
    > - 有 [更多的互動式頁面涵蓋可用的語言](https://www.microsoft.com/translator/business/languages/)，但請注意，只有當網站語言設定為 ' ' (且 Microsoft 網站可能會重新導向至您的原生語言) 時，頁面才會運作。 您可以變更頁面底部的網站語言，或修改 URL。
    > - 上述程式碼片段中的 **authorizationKey** 值必須是您訂閱 *Azure 翻譯工具文字 API* 時所收到的 **金鑰**。 這是在 [第1章](#chapter-1--the-azure-portal)中所述。

6.  現在需要新增 *喚醒 ()* 和 *啟動 ()* 方法的程式碼。 
7.  在此情況下，此程式碼會使用授權金鑰來呼叫 *Azure* ，以取得 *權杖*。

    ```csharp
        private void Awake() 
        { 
            // Set this class to behave similar to singleton  
            instance = this; 
        } 
    
        // Use this for initialization  
        void Start() 
        { 
            // When the application starts, request an auth token 
            StartCoroutine("GetTokenCoroutine", authorizationKey); 
        }
    ```

    > [!NOTE]
    > 權杖將在10分鐘後到期。 視您的應用程式案例而定，您可能必須多次進行相同的協同程式呼叫。

8.  取得權杖的協同程式如下所示：

    ```csharp
        /// <summary> 
        /// Request a Token from Azure Translation Service by providing the access key. 
        /// Debugging result is delivered to the Results class. 
        /// </summary> 
        private IEnumerator GetTokenCoroutine(string key)
        {
            if (string.IsNullOrEmpty(key))
            {
                throw new InvalidOperationException("Authorization key not set.");
            }

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Post(translationTokenEndpoint, string.Empty))
            {
                unityWebRequest.SetRequestHeader("Ocp-Apim-Subscription-Key", key);
                yield return unityWebRequest.SendWebRequest();

                long responseCode = unityWebRequest.responseCode;

                // Update the UI with the response code 
                Results.instance.SetAzureResponse(responseCode.ToString());

                if (unityWebRequest.isNetworkError || unityWebRequest.isHttpError)
                {
                    Results.instance.azureResponseText.text = unityWebRequest.error;
                    yield return null;
                }
                else
                {
                    authorizationToken = unityWebRequest.downloadHandler.text;
                }
            }

            // After receiving the token, begin capturing Audio with the MicrophoneManager Class 
            MicrophoneManager.instance.StartCapturingAudio();
        }
    ```

    > [!WARNING]
    > 如果您編輯 **GetTokenCoroutine ()** 的 IEnumerator 方法名稱，則必須更新上述程式碼中的 *StartCoroutine* 和 *StopCoroutine* 呼叫字串值。 [根據 Unity 檔](https://docs.unity3d.com/ScriptReference/MonoBehaviour.StartCoroutine.html)，若要停止特定的 *協同程式*，您必須使用字串值方法。

9.  接下來，新增協同程式 (，並在其下方的「支援」資料流程方法) ，以取得 *MicrophoneManager* 類別所接收之文字的轉譯。 此程式碼會建立要傳送至 *Azure 翻譯工具文字 API* 的查詢字串，然後使用內部 Unity UnityWebRequest 類別，對具有查詢字串的端點進行「Get」呼叫。 然後，結果會用來設定結果物件中的翻譯。 下列程式碼顯示執行：

    ```csharp
        /// <summary> 
        /// Request a translation from Azure Translation Service by providing a string.  
        /// Debugging result is delivered to the Results class. 
        /// </summary> 
        public IEnumerator TranslateWithUnityNetworking(string text)
        {
            // This query string will contain the parameters for the translation 
            string queryString = string.Concat("text=", Uri.EscapeDataString(text), "&from=", from, "&to=", to);

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Get(translationTextEndpoint + queryString))
            {
                unityWebRequest.SetRequestHeader("Authorization", "Bearer " + authorizationToken);
                unityWebRequest.SetRequestHeader("Accept", "application/xml");
                yield return unityWebRequest.SendWebRequest();

                if (unityWebRequest.isNetworkError || unityWebRequest.isHttpError)
                {
                    Debug.Log(unityWebRequest.error);
                    yield return null;
                }

                // Parse out the response text from the returned Xml
                string result = XElement.Parse(unityWebRequest.downloadHandler.text).Value;
                Results.instance.SetTranslatedResult(result);
            }
        }
    ```

10. 返回 *Unity* 之前，請務必將您的變更儲存在 *Visual Studio* 中。

## <a name="chapter-8--configure-the-unity-scene"></a>第8章-設定 Unity 場景

1.  返回 Unity 編輯器中，*從*[**腳本**] 資料夾中，按一下 [*結果*] 類別，並將其拖曳至 [階層]*面板* 中的 [**主要攝影機**] 物件。
2.  按一下 **主要攝影機** ，然後查看 [偵測 *器] 面板*。 您會發現，在新加入的 *腳本* 元件中，有四個欄位具有空白值。 這些是程式碼中屬性的輸出參考。 
3.  將適當的 **文字** 物件從 [階層] *面板* 拖曳到這四個插槽，如下圖所示。

    ![使用指定的值來更新目標參考。](images/AzureLabs-Lab1-34.png)
  
4.  接著，按一下 [**腳本**] 資料夾中的 [*翻譯工具*] 類別，並將其拖曳至 [階層]*面板* 中的 [**主要攝影機**] 物件。 
5.  然後，按一下 [**腳本**] 資料夾中的 [ *MicrophoneManager* ] 類別，並將其拖曳至 [階層]*面板* 中的 [**主要攝影機**] 物件。 
6.  最後，按一下 **主要攝影機** ，然後查看 [偵測 *器] 面板*。 您會發現，您在拖曳的腳本中有兩個下拉式方塊，可讓您設定語言。
 
    ![確定所需的翻譯語言為輸入。](images/AzureLabs-Lab1-35.png)

## <a name="chapter-9--test-in-mixed-reality"></a>第9章–測試混合現實

此時您必須測試場景是否已正確執行。

請確定：

- [第1章](#chapter-1--the-azure-portal)中所述的所有設定都已正確設定。 
- *結果*、*翻譯工具* 和 *MicrophoneManager*，腳本會附加至 **主要攝影機** 物件。 
- 您已將 *Azure 翻譯工具文字 API* 服務 **金鑰** 放在 *翻譯工具* 腳本內的 **authorizationKey** 變數內。  
- *主要相機偵測器面板* 中的所有欄位都已正確指派。
- 您的麥克風在執行場景時正在運作 (如果未執行，請檢查連結的麥克風是否為 *預設* 裝置，並在 [Windows) 中正確設定](https://support.microsoft.com/help/4027981/windows-how-to-set-up-and-test-microphones-in-windows-10)。

您可以在 *Unity 編輯器* 中按下 [**播放**] 按鈕，以測試沉浸式耳機。
應用程式應該透過附加的沉浸式耳機運作。

> [!WARNING]  
> 如果您在 Unity 主控台中看到關於預設音訊裝置變更的錯誤，場景可能無法如預期般運作。 這是因為混合現實入口網站處理有內建麥克風的方式。 如果您看到此錯誤，只需停止場景並重新啟動，就應該會如預期般運作。

## <a name="chapter-10--build-the-uwp-solution-and-sideload-on-local-machine"></a>第10章–在本機電腦上建立 UWP 方案和側載

此專案的 Unity 區段所需的所有專案現在都已完成，因此您可以從 Unity 建立它。

1.  流覽至 **build 設定**： **File > build 設定 ...**
2.  從 [**組建設定**] 視窗中，按一下 [**建立**]。

    ![建立 Unity 場景。](images/AzureLabs-Lab1-36.png)
  
3.  如果尚未這麼做，請勾選 **Unity c # 專案**。
4.  按一下 [建置]。 Unity 將會啟動一個 *檔案總管* 視窗，您需要在其中建立並選取要用來建立應用程式的資料夾。 立即建立該資料夾，並命名為 *應用程式*。 然後選取 [ *應用程式* ] 資料夾，然後按 [ **選取資料夾**]。 
5.  Unity 將開始將您的專案建立到 *應用程式* 資料夾。 
6.  Unity 完成組建之後 (可能需要一些時間) ，它會在您的組建位置開啟 *檔案總管* 視窗 (檢查您的工作列，因為它不一定會出現在您的視窗上方，但會通知您加入新的視窗) 。

## <a name="chapter-11--deploy-your-application"></a>第11章-部署您的應用程式

若要部署您的應用程式：

1.  流覽至您的新 Unity 組建 (*應用程式* 資料夾) ，然後以 *Visual Studio* 開啟方案檔。
2.  在 [方案設定] 中選取 [ **Debug**]。
3.  在 [方案平臺] 中，選取 [ **x86**]、[ **本機電腦**]。 

    > 在 Microsoft HoloLens 中，您可能會發現將此設定為 *遠端電腦* 較容易，因此不會行動網卡到您的電腦。 不過，您也必須執行下列動作：
    > - 知道您 HoloLens 的 **IP 位址**，您可以在 *設定 > 網路 & Internet > Wi-Fi > Advanced 選項* 中找到此位址;IPv4 是您應該使用的位址。 
    > - 確定已 **開啟***開發人員模式*;*設定 > 為開發人員更新 & 安全性 >*。

    ![從 Visual Studio 部署方案。](images/AzureLabs-Lab1-37.png)
    
 
4.  移至 [ **組建] 功能表** ，然後按一下 [ **部署方案** ]，將應用程式側載至您的電腦。
5.  您的應用程式現在應該會出現在已安裝的應用程式清單中，準備好要啟動。
6.  啟動後，應用程式會提示您授權麥克風的存取權。 請務必按一下 [ **是]** 按鈕。
7.  您現在已準備好開始翻譯！

## <a name="your-finished-translation-text-api-application"></a>您完成的翻譯文字 API 應用程式

恭喜，您建立了一個混合現實應用程式，利用 Azure 翻譯文字 API 將語音轉換成翻譯的文字。

![最終產品。](images/AzureLabs-Lab1-00.png)

## <a name="bonus-exercises"></a>額外練習

### <a name="exercise-1"></a>練習 1

您是否可以在應用程式中新增文字轉換語音功能，以便說出傳回的文字？

### <a name="exercise-2"></a>練習 2

讓使用者可以在應用程式本身變更來源和輸出語言 ( ' from ' 和 ' to ' ) ，因此應用程式不需要在每次想要變更語言時重建。