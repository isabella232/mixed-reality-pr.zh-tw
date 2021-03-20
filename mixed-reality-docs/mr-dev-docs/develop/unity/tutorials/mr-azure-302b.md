---
title: HoloLens (第1代) 和 Azure 302b-自訂視覺
description: 完成本課程，以瞭解如何訓練機器學習模型，然後使用定型的模型來辨識混合現實應用程式中類似的物件。
author: drneil
ms.author: jemccull
ms.date: 07/03/2018
ms.topic: article
keywords: azure，mixed reality，學院，unity，教學課程，api，自訂視覺，hololens，沉浸，vr，Windows 10，Visual Studio
ms.openlocfilehash: 97fd0ae72401b67a83752cb2cf6799fa2b1ccc0c
ms.sourcegitcommit: 35bd43624be33afdb1bf6ba4ddbe36d268eb9bda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/20/2021
ms.locfileid: "104730525"
---
# <a name="hololens-1st-gen-and-azure-302b-custom-vision"></a>HoloLens (第1代) 和 Azure 302b：自訂視覺

<br>

>[!NOTE]
>混合實境學院教學課程的設計是以 HoloLens (第 1 代) 和混合實境沉浸式頭戴裝置為準。  因此，對於仍在尋找這些裝置開發指引的開發人員而言，我們覺得這些教學課程很重要。  這些教學課程 **_不會_** 使用用於 HoloLens 2 的最新工具組或互動進行更新。  系統會保留這些資訊，以繼續在支援的裝置上運作。 未來將會有一系列新的教學課程，將會示範如何針對 HoloLens 2 進行開發。  當張貼這些教學課程時，將會使用這些教學課程的連結來更新此通知。

<br>


在此課程中，您將瞭解如何在混合現實應用程式中使用 Azure 自訂視覺功能，以在提供的影像中辨識自訂視覺內容。

這種服務可讓您使用物件影像來定型機器學習模型。 然後，您將使用定型的模型來辨識類似的物件（Microsoft HoloLens 的相機捕捉，或連接到您的電腦以取得沉浸式 (VR) 耳機的相機）所提供的物件。

![課程結果](images/AzureLabs-Lab302b-00.png)

Azure 自訂視覺是一項 Microsoft 認知服務，可讓開發人員建立自訂影像分類器。 這些分類器接著可以與新影像搭配使用，以辨識或分類該新影像內的物件。 此服務提供簡單、容易使用的線上入口網站，以簡化程式。 如需詳細資訊，請造訪 [Azure 自訂視覺服務頁面](/azure/cognitive-services/custom-vision-service/home)。

完成本課程之後，您將會有一個混合的現實應用程式，可以在兩種模式下運作：

-   **分析模式**：以手動方式設定自訂視覺服務，方法是上傳影像、建立標記，以及將服務定型以辨識不同的物件 (在此案例中為滑鼠和鍵盤) 。 然後，您將建立 HoloLens 應用程式，以使用相機來捕捉影像，並嘗試辨識真實世界中的那些物件。

-   **定型模式**：您將會執行程式碼，以在您的應用程式中啟用「定型模式」。 定型模式可讓您使用 HoloLens 的相機來捕捉影像、將捕獲的影像上傳至服務，以及定型自訂視覺模型。

本課程將告訴您如何將自訂視覺服務的結果取得 Unity 型範例應用程式。 您必須將這些概念套用至您可能正在建立的自訂應用程式。

## <a name="device-support"></a>裝置支援

<table>
<tr>
<th>課程</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">沉浸式頭戴裝置</a></th>
</tr><tr>
<td> MR 和 Azure 302b：自訂視覺</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> 雖然本課程主要著重于 HoloLens，您也可以將本課程中所學到的內容套用到 Windows Mixed Reality 沉浸式 (VR) 耳機。 因為沉浸式 (VR) 耳機沒有可存取的攝影機，所以您需要有連接到電腦的外部攝影機。 當您依照課程的指示，您將會看到有關您可能需要採用以支援沉浸式 (VR) 耳機的任何變更的注意事項。

## <a name="prerequisites"></a>Prerequisites

> [!NOTE]
> 本教學課程是專為擁有 Unity 和 c # 基本經驗的開發人員所設計。 另外也請注意，本檔中的必要條件和書面指示，代表在撰寫 (2018 年7月) 時已經過測試和驗證的內容。 You are free to use the latest software, as listed within the [install the tools](../../install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you will find in newer software than what is listed below.

本課程建議您採用下列硬體和軟體：

- 開發電腦，與適用于沉浸式 (VR) 耳機開發的[Windows Mixed Reality 相容](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines)
- [啟用開發人員模式的 Windows 10 Fall Creators Update (或更新版本) ](../../install-the-tools.md#installation-checklist)
- [最新的 Windows 10 SDK](../../install-the-tools.md#installation-checklist)
- [Unity 2017。4](../../install-the-tools.md#installation-checklist)
- [Visual Studio 2017](../../install-the-tools.md#installation-checklist)
- [Windows Mixed Reality 沉浸式 (VR) 耳機](../../../discover/immersive-headset-hardware-details.md)，或已啟用開發人員模式的[Microsoft HoloLens](/hololens/hololens1-hardware)
- 連接到您 PC (的攝影機，適用于沉浸式耳機開發) 
- 適用于 Azure 安裝程式和自訂視覺 API 抓取的網際網路存取
- 一系列至少五 (5) 映射 (10 (10) 建議) 服務辨識的每個物件自訂視覺。 如果您想要的話，可以使用 [本課程中已提供的影像 (電腦滑鼠和鍵盤) ](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/ComputerVision_Images.zip)。

## <a name="before-you-start"></a>在您開始使用 Intune 之前

1.  為了避免在建立此專案時發生問題，強烈建議您在根或近端根資料夾中，建立本教學課程中所述的專案 (長的資料夾路徑可能會在組建階段) 時發生問題。
2.  設定及測試 HoloLens。 如果您需要設定 HoloLens 的支援， [請務必造訪 HoloLens 安裝文章](/hololens/hololens-setup)。 
3.  開始開發新的 HoloLens 應用程式時，最好先執行校正和感應器調整， (有時它可以協助針對每個使用者) 執行這些工作。 

如需有關校正的說明，請遵循此 [與 HoloLens 校正文章相關的連結](/hololens/hololens-calibration#hololens-2)。

如需有關感應器微調的說明，請依照此 [連結來進行「HoloLens 感應器微調」文章](/hololens/hololens-updates)。

## <a name="chapter-1---the-custom-vision-service-portal"></a>第1章-自訂視覺 Service 入口網站

若要在 Azure 中使用 *自訂視覺服務* ，您必須將服務的實例設定為可供應用程式使用。

1.  首先， [流覽至 *自訂視覺服務* 主頁面](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/)。

2.  按一下 [ **開始** ] 按鈕。

    ![開始使用自訂視覺服務](images/AzureLabs-Lab302b-01.png)

3.  登入 *自訂視覺服務* 入口網站。

    ![登入入口網站](images/AzureLabs-Lab302b-02.png)

    > [!NOTE]
    > 如果您還沒有 Azure 帳戶，您將需要建立一個帳戶。 如果您在課堂或實驗室的情況下進行本教學課程，請洽詢講師或其中一個 proctors，協助您設定新的帳戶。

4.  當您第一次登入之後，系統會提示您提供 *服務條款* 面板。 按一下核取方塊以同意條款。 然後按一下 [ **我同意**]。

    ![服務條款](images/AzureLabs-Lab302b-03.png)

5.  同意條款之後，您將會流覽至入口網站的 [ *專案* ] 區段。 按一下 [ **新增專案**]。

    ![建立新專案](images/AzureLabs-Lab302b-04.png)

6.  右側將會出現一個索引標籤，提示您指定專案的某些欄位。

    1.  插入專案的 *名稱* 。

    2.  為您的專案插入 *描述* (*選擇性*) 。

    3.  選擇資源群組，或建立一個新的 *資源群組* 。 資源群組提供一種方式來監視、控制存取、布建及管理 Azure 資產集合的計費。 建議您保留與單一專案相關聯的所有 Azure 服務 (例如，) 一般資源群組下的這些課程) 。

    4. 將 *專案類型* 設定為 **分類**
    
    5. 將 *網域* 設定為 **[一般**]。

        ![設定網域](images/AzureLabs-Lab302b-05.png)

        > 如果您想要閱讀更多有關 Azure 資源群組的資訊，請 [造訪資源群組文章](/azure/azure-resource-manager/resource-group-portal)。

7.  完成之後，按一下 [ **建立專案**]，系統會將您重新導向至自訂視覺服務的 [專案] 頁面。

## <a name="chapter-2---training-your-custom-vision-project"></a>第2章-訓練自訂視覺專案

在自訂視覺入口網站中，您的主要目標是將您的專案定型，以辨識影像中的特定物件。 您需要至少五個 (5) 的映射，但最好是針對您希望應用程式辨識的每個物件都有10個 (10) 。 [您可以使用本課程所提供的影像 (電腦滑鼠和鍵盤) ](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/ComputerVision_Images.zip)。 

定型您的自訂視覺服務專案：

1.  按一下 [ **+** 標記] 旁的 **按鈕。**

    ![新增標籤](images/AzureLabs-Lab302b-06.png)

2.  新增您想要辨識的物件 **名稱** 。 按一下 [ **儲存**]。

    ![新增物件名稱並儲存](images/AzureLabs-Lab302b-07.png)

3.  您會注意到 **您的標籤已新增** (您可能需要重載頁面，才能讓它顯示) 。 在新標記旁邊按一下核取方塊（如果尚未核取）。

    ![啟用新標記](images/AzureLabs-Lab302b-08.png)

4.  按一下頁面中央的 [ **加入影像** ]。

    ![新增影像](images/AzureLabs-Lab302b-09.png)

5.  按一下 **[流覽本機檔案]**，然後搜尋並選取您想要上傳的影像，其最少為五 (5) 。 請記住，這些影像都應該包含您正在定型的物件。

    > [!NOTE]
    >  您可以一次選取多個影像，以便上傳。

6.  當您可以在索引標籤中看到影像之後，請在 [ **我的標記** ] 方塊中選取適當的標籤。

    ![選取標記](images/AzureLabs-Lab302b-10.png)

7.  按一下 **[上傳** 檔案]。 檔案將會開始上傳。 確認上傳之後，請按一下 [ **完成**]。

    ![上傳檔案](images/AzureLabs-Lab302b-11.png)

8.  重複相同的程式，建立名為 **鍵盤** 的新 **標記**，並為其上傳適當的相片。 當您建立新標籤之後，請務必 **取消** 核取 *滑鼠* ，以顯示 [新增 *影像* ] 視窗。

9.  當您設定這兩個標籤之後，請按一下 [ **定型**]，第一個定型反復專案將會開始建立。

    ![啟用定型反復專案](images/AzureLabs-Lab302b-12.png)

10. 一旦建立之後，您就可以看到兩個按鈕，稱為「 **建立預設值** 和 **預測 URL**」。 先按一下 [ **設為預設值** ]，然後按一下 [ **預測 URL**]。

    ![製作預設值和預測 URL](images/AzureLabs-Lab302b-13.png)

    > [!NOTE] 
    > 由此提供的端點 URL 會設定為已標示為預設值的任何 *反復* 專案。 因此，如果您稍後建立新的 *反復* 專案，並將其更新為預設值，您就不需要變更程式碼。

11. 當您按一下 [ *預測 URL*] 之後，請開啟 [ *記事本*]，然後複製並貼上 **URL** 和 **預測金鑰**，以便稍後在程式碼中需要時加以取出。

    ![複製並貼上 URL 和 Prediction-Key](images/AzureLabs-Lab302b-14.png)

12. 按一下畫面右上方的 [ **齒輪** ]。

    ![按一下 [齒輪] 圖示以開啟 [設定]](images/AzureLabs-Lab302b-15.png)

13. 將 **定型金鑰** 複製並貼到 *記事本* 中，以供稍後使用。

    ![複製訓練金鑰](images/AzureLabs-Lab302b-16.png)

14. 此外，也請複製您的 **專案 Id**，並將其貼到您的 *記事本* 檔案中，以供稍後使用。

    ![複製專案識別碼](images/AzureLabs-Lab302b-16a.png)

## <a name="chapter-3---set-up-the-unity-project"></a>第3章-設定 Unity 專案

以下是使用 mixed reality 進行開發的一般設定，因此，它是適用于其他專案的絕佳範本。

1.  開啟 *Unity* ，然後按一下 [ **新增**]。

    ![建立新的 Unity 專案](images/AzureLabs-Lab302b-17.png)

2.  您現在將需要提供 Unity 專案名稱。 插入 **AzureCustomVision。** 請確定專案範本已設定為 **3d**。 將 **位置** 設定為適合您 (記住，較接近根目錄的) 。 然後，按一下 [ **建立專案**]。

    ![設定專案設定](images/AzureLabs-Lab302b-18.png)

3.  在 Unity 開啟的情況下，值得檢查預設 **腳本編輯器** 是否設定為 **Visual Studio**。 移至 [ **編輯*  >  *喜好** 設定]，然後在新視窗中，流覽至 [**外部工具**]。 將 **外部腳本編輯器** 變更為 **Visual Studio 2017**。 關閉 [ **喜好** 設定] 視窗。

    ![設定外部工具](images/AzureLabs-Lab302b-19.png)

4.  接下來，移至 [檔案 **> 組建設定** ]，選取 [ **通用 Windows 平臺**]，然後按一下 [ **切換平臺** ] 按鈕以套用您的選取專案。

    ![設定組建設定 ](images/AzureLabs-Lab302b-20.png)

5.  在檔案中仍 **> 組建設定** ，並確定：

    1.  **目標裝置** 設定為 **HoloLens**

        > 針對沉浸式耳機，將 **目標裝置** 設為 *任何裝置*。
        
    2.  **組建類型** 設定為 **D3D**
    3.  **SDK** 已設定為 **最新安裝**
    4.  **Visual Studio 版本** 設定為 **最新安裝**
    5.  **組建並執行** 設定為 **本機電腦**
    6.  儲存場景，並將其新增至組建。 

        1. 若要這麼做，請選取 [ **新增開啟的場景**]。 [儲存] 視窗隨即出現。

            ![將開啟的場景新增至組建清單](images/AzureLabs-Lab302b-21.png)

        2. 為此和任何未來的場景建立新的資料夾，然後選取 [ **新增資料夾** ] 按鈕，建立新的資料夾，將它命名為 **場景**。

            ![建立新的場景資料夾](images/AzureLabs-Lab302b-22.png)

        3. 開啟新建立的 **場景** 資料夾，然後在 [ *檔案名：* 文字] 欄位中輸入 **CustomVisionScene**，然後按一下 [ **儲存**]。

            ![命名新的場景檔案](images/AzureLabs-Lab302b-23.png)

            > 請注意，您必須將 Unity 場景儲存在 [ *資產* ] 資料夾中，因為它們必須與 Unity 專案相關聯。 建立幕後資料夾 (和其他類似的資料夾) 是結構化 Unity 專案的典型方式。
            
    7.  [ *組建設定*] 中的其餘設定，現在應該保持為預設值。

        ![預設組建設定](images/AzureLabs-Lab302b-24.png)

6.  在 [ *組建設定* ] 視窗中，按一下 [ **播放程式設定** ] 按鈕，這會開啟偵測 *器* 所在空間中的相關面板。

7. 在此面板中，需要驗證幾個設定：

    1.  在 [ **其他設定** ] 索引標籤中：

        1.  **腳本執行階段版本** 應該是 **實驗 ( .Net 4.6 對等)**，這會觸發重新開機編輯器的需求。

        2. **腳本後端** 應該是 **.net**

        3. **API 相容性層級** 應為 **.net 4.6**

        ![設定 API compantiblity](images/AzureLabs-Lab302b-25.png)

    2.  在 [ **發行設定** ] 索引標籤的 [ **功能**] 下，選取：

        1. **InternetClient**

        2.  **網路攝影機**

        3. **麥克風**

        ![設定發佈設定](images/AzureLabs-Lab302b-26.png)

    3.  在面板的 [XR 設定] 中，在 [ **設定** ] (找到的 [ **發佈設定** ]) 、[滴答 **虛擬實境支援**]，請確定已新增 **Windows Mixed Reality SDK** 。

    ![設定 XR 設定](images/AzureLabs-Lab302b-27.png)

8.  回到 *組建設定*： *Unity C \# 專案* 不再呈現灰色; 勾選此方塊旁邊的核取方塊。

9.  關閉 [建置設定] 視窗。

10.  將場景和專案儲存 (檔 **> 儲存場景/檔案 > 儲存專案**) 。


## <a name="chapter-4---importing-the-newtonsoft-dll-in-unity"></a>第4章-匯入 Unity 中的 Newtonsoft DLL

> [!IMPORTANT]
> 如果您想要跳過此課程的 *Unity 設定* 元件，並直接繼續進行程式碼，您可以下載此 [Azure-MR-302b. unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/Azure-MR-302b.unitypackage)，將其匯入到您的專案中做為 [**自訂套件**](https://docs.unity3d.com/Manual/AssetPackages.html)，然後繼續進行 [第6章](#chapter-6---create-the-customvisionanalyser-class)。

本課程需要使用 **Newtonsoft** 程式庫，您可以將其以 DLL 的形式新增至您的資產。 您可以從此 [連結下載包含此程式庫](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/NewtonsoftDLL.unitypackage)的套件。
若要將 Newtonsoft 程式庫匯入您的專案，請使用本課程隨附的 Unity 套件。

1.  使用 [ **資產* 匯  >  *入**封裝*  >  *自訂**套件** ] 功能表選項，將 *unitypackage* 新增至 Unity。

2.  在彈出的 [匯 **入 Unity 套件** ] 方塊中，確定已選取 [ (] 下的所有專案，並包含) **外掛程式** 。

    ![匯入所有封裝專案](images/AzureLabs-Lab302b-28.png)

3.  按一下 [匯 **入** ] 按鈕，將專案新增至您的專案。

4.  移至專案視圖中 [**外掛程式**] 下的 [ **Newtonsoft** ] 資料夾，然後選取 [*在外掛程式上Newtonsoft.Js*]。

    ![選取 Newtonsoft 外掛程式](images/AzureLabs-Lab302b-29.png)

5.  選取 *Newtonsoft.Json 外掛程式* 時，請確定已 **取消** 核取 **任何平臺**，然後確定 **WSAPlayer** **也未** 核取，然後 **按一下 [** 套用]。 這只是為了確認檔案已正確設定。

    ![設定 Newtonsoft 外掛程式](images/AzureLabs-Lab302b-30.png)

    > [!NOTE]
    > 標記這些外掛程式會將它們設定為只在 Unity 編輯器中使用。 在 [WSA] 資料夾中有一組不同的集合，會在從 Unity 匯出專案之後使用。

6.  接下來，您需要在 **Newtonsoft** 資料夾內開啟 [ **WSA** ] 資料夾。 您會看到您剛剛設定的相同檔案的複本。 選取檔案，然後在偵測器中，確定
    -   **未核** 取 **任何平臺** 
    -   **只****檢查** **WSAPlayer**
    -   不 **檢查****進程**

    ![設定 Newtonsoft 外掛程式平臺設定](images/AzureLabs-Lab302b-31.png)

## <a name="chapter-5---camera-setup"></a>第5章-攝影機設定

1.  在 [階層] 面板中，選取 [ *主要相機*]。

2.  一旦選取之後，您就可以在 [偵測 *器] 面板* 中看到 *主要攝影機* 的所有元件。

    1.  *攝影機* 物件必須命名為 **主要攝影機** (請注意拼寫！ ) 

    2.  主要攝影機 **標記** 必須設定為 **MainCamera** (注意拼寫！ ) 

    3.  請確定 **轉換位置** 設定為 **0、0、0**

    4.  將 [ **清除旗標** ] 設定為 [ **純色** ] (針對沉浸式耳機) 略過此設定。

    5.  將相機元件的 **背景** 色彩設定為 **黑色、Alpha 0 (Hex 碼： #00000000)** (略過此項，以取得沉浸式耳機) 。

    ![設定相機元件屬性](images/AzureLabs-Lab302b-32.png)


## <a name="chapter-6---create-the-customvisionanalyser-class"></a>第6章-建立 CustomVisionAnalyser 類別。

至此，您已準備好撰寫一些程式碼。

您將開始使用 *CustomVisionAnalyser* 類別。

> [!NOTE]
> 下列程式碼中所示的 **自訂視覺服務** 呼叫會使用 **自訂視覺 REST API** 進行。 透過這種方式，您將瞭解如何實行和使用此 API (有助於瞭解如何在您自己的) 上執行類似的操作。 請注意，Microsoft 提供的 **自訂視覺服務 SDK** 也可以用來對服務進行呼叫。 如需詳細資訊，請造訪 [自訂視覺 SERVICE SDK](https://github.com/Microsoft/Cognitive-CustomVision-Windows/) 文章。

此類別負責：

-   載入以位元組陣列形式捕獲的最新映射。

-   將位元組陣列傳送至您的 Azure *自訂視覺服務* 實例以進行分析。

-   以 JSON 字串的形式接收回應。

-   將回應還原序列化，並將產生的 *預測* 傳遞給 *SceneOrganiser* 類別，這將會負責顯示回應的方式。

若要建立此類別：

1.  以滑鼠右鍵按一下位於 [*專案] 面板* 中的 [*資產] 資料夾*，然後按一下 [**建立] > 資料夾**。 呼叫資料夾 **腳本**。

    ![建立腳本資料夾](images/AzureLabs-Lab302b-33.png)

2.  按兩下剛才建立的資料夾，將它開啟。

3.  在資料夾內按一下滑鼠右鍵，然後按一下 [**建立**  >  **C \# 腳本**]。 將腳本命名為 *CustomVisionAnalyser*。

4.  按兩下新的 *CustomVisionAnalyser* 腳本，以 **Visual Studio** 開啟。

5.  更新檔案頂端的命名空間，以符合下列各項：

    ```csharp
    using System.Collections;
    using System.IO;
    using UnityEngine;
    using UnityEngine.Networking;
    using Newtonsoft.Json;
    ```

6.  在 *CustomVisionAnalyser* 類別中，新增下列變數：

    ```csharp
        /// <summary>
        /// Unique instance of this class
        /// </summary>
        public static CustomVisionAnalyser Instance;

        /// <summary>
        /// Insert your Prediction Key here
        /// </summary>
        private string predictionKey = "- Insert your key here -";

        /// <summary>
        /// Insert your prediction endpoint here
        /// </summary>
        private string predictionEndpoint = "Insert your prediction endpoint here";

        /// <summary>
        /// Byte array of the image to submit for analysis
        /// </summary>
        [HideInInspector] public byte[] imageBytes;
    ```

    > [!NOTE]
    > 請務必將您的 **預測金鑰** 插入至 **predictionKey** 變數，並將 **預測端點** 插入至 **predictionEndpoint** 變數。 您稍早在課程中將這些複製到 [ *記事本* ]。

7.  現在需要新增 **喚醒 ()** 的程式碼，以初始化執行個體變數：

    ```csharp
        /// <summary>
        /// Initialises this class
        /// </summary>
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            Instance = this;
        }
    ```

8.  刪除方法 **開始 ()** 和 **更新 ()**。

9.  接下來，新增協同程式 (，並在其下方加入靜態 **GetImageAsByteArray ()** 方法) ，它會取得 *ImageCapture* 類別所捕獲之影像的分析結果。

    > [!NOTE]
    > 在 [ **AnalyseImageCapture** ] 協同程式中，您還必須呼叫 *SceneOrganiser* 類別。 因此，請 **暫時將這些行** 加上批註。

    ```csharp    
        /// <summary>
        /// Call the Computer Vision Service to submit the image.
        /// </summary>
        public IEnumerator AnalyseLastImageCaptured(string imagePath)
        {
            WWWForm webForm = new WWWForm();
            using (UnityWebRequest unityWebRequest = UnityWebRequest.Post(predictionEndpoint, webForm))
            {
                // Gets a byte array out of the saved image
                imageBytes = GetImageAsByteArray(imagePath);

                unityWebRequest.SetRequestHeader("Content-Type", "application/octet-stream");
                unityWebRequest.SetRequestHeader("Prediction-Key", predictionKey);

                // The upload handler will help uploading the byte array with the request
                unityWebRequest.uploadHandler = new UploadHandlerRaw(imageBytes);
                unityWebRequest.uploadHandler.contentType = "application/octet-stream";

                // The download handler will help receiving the analysis from Azure
                unityWebRequest.downloadHandler = new DownloadHandlerBuffer();

                // Send the request
                yield return unityWebRequest.SendWebRequest();

                string jsonResponse = unityWebRequest.downloadHandler.text;

                // The response will be in JSON format, therefore it needs to be deserialized    
    
                // The following lines refers to a class that you will build in later Chapters
                // Wait until then to uncomment these lines

                //AnalysisObject analysisObject = new AnalysisObject();
                //analysisObject = JsonConvert.DeserializeObject<AnalysisObject>(jsonResponse);
                //SceneOrganiser.Instance.SetTagsToLastLabel(analysisObject);
            }
        }

        /// <summary>
        /// Returns the contents of the specified image file as a byte array.
        /// </summary>
        static byte[] GetImageAsByteArray(string imageFilePath)
        {
            FileStream fileStream = new FileStream(imageFilePath, FileMode.Open, FileAccess.Read);

            BinaryReader binaryReader = new BinaryReader(fileStream);

            return binaryReader.ReadBytes((int)fileStream.Length);
        }
    ```

10.  返回 **Unity** 之前，請務必將您的變更儲存在 **Visual Studio** 中。

## <a name="chapter-7---create-the-customvisionobjects-class"></a>第7章-建立 CustomVisionObjects 類別

您將建立的類別現在是 *CustomVisionObjects* 類別。

此腳本包含其他類別用來序列化和還原序列化對 *自訂視覺服務* 進行之呼叫的物件數。

> [!WARNING]
> 請務必記下自訂視覺服務提供給您的端點，因為下列 JSON 結構已設定為可搭配 [*自訂視覺預測*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/450e4ba4d72542e889d93fd7b8e960de/operations/5a6264bc40d86a0ef8b2c290)v2.0 使用。 如果您有不同的版本，您可能需要更新下列結構。

若要建立此類別：

1.  在 [**腳本**] 資料夾內按一下滑鼠右鍵，然後按一下 [**建立**  >  **C \# 腳本**]。 呼叫腳本 *CustomVisionObjects*。

2.  按兩下新的 **CustomVisionObjects** 腳本，以 **Visual Studio** 開啟。

3.  將下列命名空間新增至檔案頂端：

    ```csharp
    using System;
    using System.Collections.Generic;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

4.  刪除 [**開始 ()** ]，並更新 *CustomVisionObjects* 類別內的 **()** 方法;這個類別現在應該是空的。

5.  將下列類別新增至 *CustomVisionObjects* 類別 **之外**。 *Newtonsoft* 程式庫會使用這些物件，將回應資料序列化和還原序列化：

    ```csharp
    // The objects contained in this script represent the deserialized version
    // of the objects used by this application 

    /// <summary>
    /// Web request object for image data
    /// </summary>
    class MultipartObject : IMultipartFormSection
    {
        public string sectionName { get; set; }

        public byte[] sectionData { get; set; }

        public string fileName { get; set; }

        public string contentType { get; set; }
    }

    /// <summary>
    /// JSON of all Tags existing within the project
    /// contains the list of Tags
    /// </summary> 
    public class Tags_RootObject
    {
        public List<TagOfProject> Tags { get; set; }
        public int TotalTaggedImages { get; set; }
        public int TotalUntaggedImages { get; set; }
    }

    public class TagOfProject
    {
        public string Id { get; set; }
        public string Name { get; set; }
        public string Description { get; set; }
        public int ImageCount { get; set; }
    }

    /// <summary>
    /// JSON of Tag to associate to an image
    /// Contains a list of hosting the tags,
    /// since multiple tags can be associated with one image
    /// </summary> 
    public class Tag_RootObject
    {
        public List<Tag> Tags { get; set; }
    }

    public class Tag
    {
        public string ImageId { get; set; }
        public string TagId { get; set; }
    }

    /// <summary>
    /// JSON of Images submitted
    /// Contains objects that host detailed information about one or more images
    /// </summary> 
    public class ImageRootObject
    {
        public bool IsBatchSuccessful { get; set; }
        public List<SubmittedImage> Images { get; set; }
    }

    public class SubmittedImage
    {
        public string SourceUrl { get; set; }
        public string Status { get; set; }
        public ImageObject Image { get; set; }
    }

    public class ImageObject
    {
        public string Id { get; set; }
        public DateTime Created { get; set; }
        public int Width { get; set; }
        public int Height { get; set; }
        public string ImageUri { get; set; }
        public string ThumbnailUri { get; set; }
    }

    /// <summary>
    /// JSON of Service Iteration
    /// </summary> 
    public class Iteration
    {
        public string Id { get; set; }
        public string Name { get; set; }
        public bool IsDefault { get; set; }
        public string Status { get; set; }
        public string Created { get; set; }
        public string LastModified { get; set; }
        public string TrainedAt { get; set; }
        public string ProjectId { get; set; }
        public bool Exportable { get; set; }
        public string DomainId { get; set; }
    }

    /// <summary>
    /// Predictions received by the Service after submitting an image for analysis
    /// </summary> 
    [Serializable]
    public class AnalysisObject
    {
        public List<Prediction> Predictions { get; set; }
    }

    [Serializable]
    public class Prediction
    {
        public string TagName { get; set; }
        public double Probability { get; set; }
    }
    ```

## <a name="chapter-8---create-the-voicerecognizer-class"></a>第8章-建立 VoiceRecognizer 類別

此類別會辨識使用者的語音輸入。

若要建立此類別：

1.  在 [**腳本**] 資料夾內按一下滑鼠右鍵，然後按一下 [**建立**  >  **C \# 腳本**]。 呼叫腳本 *VoiceRecognizer*。

2.  按兩下新的 **VoiceRecognizer** 腳本，以 **Visual Studio** 開啟。

3.  在 *VoiceRecognizer* 類別的上方新增下列命名空間：

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Linq;
    using UnityEngine;
    using UnityEngine.Windows.Speech;
    ```

4.  然後，在 *VoiceRecognizer* 類別內，于 *Start ()* 方法的上方新增下列變數：

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static VoiceRecognizer Instance;

        /// <summary>
        /// Recognizer class for voice recognition
        /// </summary>
        internal KeywordRecognizer keywordRecognizer;

        /// <summary>
        /// List of Keywords registered
        /// </summary>
        private Dictionary<string, Action> _keywords = new Dictionary<string, Action>();
    ```

5.  新增 **喚醒的 ()** 並 **啟動 ()** 方法，後者將會設定將標籤與影像建立關聯時要辨識的使用者 *關鍵字* ：

    ```csharp
        /// <summary>
        /// Called on initialization
        /// </summary>
        private void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Runs at initialization right after Awake method
        /// </summary>
        void Start ()
        {

            Array tagsArray = Enum.GetValues(typeof(CustomVisionTrainer.Tags));

            foreach (object tagWord in tagsArray)
            {
                _keywords.Add(tagWord.ToString(), () =>
                {
                    // When a word is recognized, the following line will be called
                    CustomVisionTrainer.Instance.VerifyTag(tagWord.ToString());
                });
            }

            _keywords.Add("Discard", () =>
            {
                // When a word is recognized, the following line will be called
                // The user does not want to submit the image
                // therefore ignore and discard the process
                ImageCapture.Instance.ResetImageCapture();
                keywordRecognizer.Stop();
            });

            //Create the keyword recognizer 
            keywordRecognizer = new KeywordRecognizer(_keywords.Keys.ToArray());

            // Register for the OnPhraseRecognized event 
            keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
        }
    ```

6.  刪除 **更新 ()** 方法。

7.  新增下列處理常式，每次辨識語音輸入時就會呼叫此處理程式：

    ```csharp    
        /// <summary>
        /// Handler called when a word is recognized
        /// </summary>
        private void KeywordRecognizer_OnPhraseRecognized(PhraseRecognizedEventArgs args)
        {
            Action keywordAction;
            // if the keyword recognized is in our dictionary, call that Action.
            if (_keywords.TryGetValue(args.text, out keywordAction))
            {
                keywordAction.Invoke();
            }
        }
    ```

8.  返回 **Unity** 之前，請務必將您的變更儲存在 **Visual Studio** 中。

> [!NOTE]
> 不要擔心可能出現錯誤的程式碼，因為您很快就會提供進一步的類別，這將會修正這些問題。

## <a name="chapter-9---create-the-customvisiontrainer-class"></a>第9章-建立 CustomVisionTrainer 類別

這個類別會建立一連串的 web 呼叫來訓練 *自訂視覺服務*。 在程式碼上方會詳細說明每個呼叫。

若要建立此類別：

1.  在 [**腳本**] 資料夾內按一下滑鼠右鍵，然後按一下 [**建立**  >  **C \# 腳本**]。 呼叫腳本 *CustomVisionTrainer*。

2.  按兩下新的 *CustomVisionTrainer* 腳本，以 **Visual Studio** 開啟。

3.  在 *CustomVisionTrainer* 類別的上方新增下列命名空間：

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.Collections.Generic;
    using System.IO;
    using System.Text;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

4.  然後，在 *CustomVisionTrainer* 類別內，于 **Start ()** 方法的上方新增下列變數。 

    > [!NOTE]
    > 此處所使用的定型 URL 是在 *自訂視覺訓練 1.2* 檔中提供，其結構如下： https://southcentralus.api.cognitive.microsoft.com/customvision/v1.2/Training/projects/{projectId}/  
    > 如需詳細資訊，請流覽 [*自訂視覺訓練/1.2 參考 API*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/f2d62aa3b93843d79e948fe87fa89554/operations/5a3044ee08fa5e06b890f11f)。

    > [!WARNING]
    > 請務必記下自訂視覺服務為您提供定型模式的端點，因為在 **CustomVisionObjects** 類別內使用 (的 JSON 結構) 已設定為使用 [*自訂視覺定型 1.2*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/f2d62aa3b93843d79e948fe87fa89554/operations/5a3044ee08fa5e06b890f11f)版。 如果您有不同的版本，您可能需要更新 *物件* 結構。

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static CustomVisionTrainer Instance;

        /// <summary>
        /// Custom Vision Service URL root
        /// </summary>
        private string url = "https://southcentralus.api.cognitive.microsoft.com/customvision/v1.2/Training/projects/";

        /// <summary>
        /// Insert your prediction key here
        /// </summary>
        private string trainingKey = "- Insert your key here -";

        /// <summary>
        /// Insert your Project Id here
        /// </summary>
        private string projectId = "- Insert your Project Id here -";

        /// <summary>
        /// Byte array of the image to submit for analysis
        /// </summary>
        internal byte[] imageBytes;

        /// <summary>
        /// The Tags accepted
        /// </summary>
        internal enum Tags {Mouse, Keyboard}

        /// <summary>
        /// The UI displaying the training Chapters
        /// </summary>
        private TextMesh trainingUI_TextMesh;
    ```

    > [!IMPORTANT]
    > 請確定您將 **服務金鑰** 新增 (定型金鑰) 值和 **專案識別碼** 值（您先前記下的值）;這些是您稍 [早在課程中從入口網站收集的值 (第2章：步驟 10)](#chapter-2---training-your-custom-vision-project)。

5.  新增下列 **開始 ()** 和 **喚醒的 ()** 方法。 這些方法會在初始化時呼叫，並包含設定 UI 的呼叫：

    ```csharp
        /// <summary>
        /// Called on initialization
        /// </summary>
        private void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Runs at initialization right after Awake method
        /// </summary>
        private void Start()
        { 
            trainingUI_TextMesh = SceneOrganiser.Instance.CreateTrainingUI("TrainingUI", 0.04f, 0, 4, false);
        }
    ```

6.  刪除 **更新 ()** 方法。 此類別將不需要它。

7.  新增 **RequestTagSelection ()** 方法。 當映射已被捕獲並儲存在裝置中，並且現在已準備好提交給 *自訂視覺服務* 來定型時，就會先呼叫這個方法。 這個方法會在定型 UI 中顯示一組關鍵字，讓使用者用來標記已被捕獲的影像。 它也會警示 *VoiceRecognizer* 類別，以開始接聽使用者進行語音輸入。

    ```csharp
        internal void RequestTagSelection()
        {
            trainingUI_TextMesh.gameObject.SetActive(true);
            trainingUI_TextMesh.text = $" \nUse voice command \nto choose between the following tags: \nMouse\nKeyboard \nor say Discard";

            VoiceRecognizer.Instance.keywordRecognizer.Start();
        }
    ```

8.  新增 **VerifyTag ()** 方法。 這個方法會接收 **VoiceRecognizer** 類別所辨識的語音輸入，並確認其有效性，然後開始定型程式。

    ```csharp
        /// <summary>
        /// Verify voice input against stored tags.
        /// If positive, it will begin the Service training process.
        /// </summary>
        internal void VerifyTag(string spokenTag)
        {
            if (spokenTag == Tags.Mouse.ToString() || spokenTag == Tags.Keyboard.ToString())
            {
                trainingUI_TextMesh.text = $"Tag chosen: {spokenTag}";
                VoiceRecognizer.Instance.keywordRecognizer.Stop();
                StartCoroutine(SubmitImageForTraining(ImageCapture.Instance.filePath, spokenTag));
            }
        }
    ```

9.  新增 **SubmitImageForTraining ()** 方法。 此方法將開始自訂視覺服務訓練程式。 第一個步驟是從與使用者驗證的語音輸入相關聯的服務中取出 **標記識別項** 。 然後，將會連同映射一起上傳 **標記識別項** 。

    ```csharp
        /// <summary>
        /// Call the Custom Vision Service to submit the image.
        /// </summary>
        public IEnumerator SubmitImageForTraining(string imagePath, string tag)
        {
            yield return new WaitForSeconds(2);
            trainingUI_TextMesh.text = $"Submitting Image \nwith tag: {tag} \nto Custom Vision Service";
            string imageId = string.Empty;
            string tagId = string.Empty;

            // Retrieving the Tag Id relative to the voice input
            string getTagIdEndpoint = string.Format("{0}{1}/tags", url, projectId);
            using (UnityWebRequest www = UnityWebRequest.Get(getTagIdEndpoint))
            {
                www.SetRequestHeader("Training-Key", trainingKey);
                www.downloadHandler = new DownloadHandlerBuffer();
                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;

                Tags_RootObject tagRootObject = JsonConvert.DeserializeObject<Tags_RootObject>(jsonResponse);

                foreach (TagOfProject tOP in tagRootObject.Tags)
                {
                    if (tOP.Name == tag)
                    {
                        tagId = tOP.Id;
                    }             
                }
            }

            // Creating the image object to send for training
            List<IMultipartFormSection> multipartList = new List<IMultipartFormSection>();
            MultipartObject multipartObject = new MultipartObject();
            multipartObject.contentType = "application/octet-stream";
            multipartObject.fileName = "";
            multipartObject.sectionData = GetImageAsByteArray(imagePath);
            multipartList.Add(multipartObject);

            string createImageFromDataEndpoint = string.Format("{0}{1}/images?tagIds={2}", url, projectId, tagId);

            using (UnityWebRequest www = UnityWebRequest.Post(createImageFromDataEndpoint, multipartList))
            {
                // Gets a byte array out of the saved image
                imageBytes = GetImageAsByteArray(imagePath);           

                //unityWebRequest.SetRequestHeader("Content-Type", "application/octet-stream");
                www.SetRequestHeader("Training-Key", trainingKey);

                // The upload handler will help uploading the byte array with the request
                www.uploadHandler = new UploadHandlerRaw(imageBytes);

                // The download handler will help receiving the analysis from Azure
                www.downloadHandler = new DownloadHandlerBuffer();

                // Send the request
                yield return www.SendWebRequest();

                string jsonResponse = www.downloadHandler.text;

                ImageRootObject m = JsonConvert.DeserializeObject<ImageRootObject>(jsonResponse);
                imageId = m.Images[0].Image.Id;
            }
            trainingUI_TextMesh.text = "Image uploaded";
            StartCoroutine(TrainCustomVisionProject());
        }
    ```

10. 新增 **TrainCustomVisionProject ()** 方法。 一旦提交並標記映射之後，就會呼叫這個方法。 它會建立新的反復專案，其會使用提交至服務的所有先前映射以及剛上傳的影像來定型。 定型完成之後，這個方法會呼叫方法，將新建立的 **反復** 專案設定為 **預設值**，讓您用來進行分析的端點成為最新定型的反復專案。

    ```csharp
        /// <summary>
        /// Call the Custom Vision Service to train the Service.
        /// It will generate a new Iteration in the Service
        /// </summary>
        public IEnumerator TrainCustomVisionProject()
        {
            yield return new WaitForSeconds(2);

            trainingUI_TextMesh.text = "Training Custom Vision Service";

            WWWForm webForm = new WWWForm();

            string trainProjectEndpoint = string.Format("{0}{1}/train", url, projectId);

            using (UnityWebRequest www = UnityWebRequest.Post(trainProjectEndpoint, webForm))
            {
                www.SetRequestHeader("Training-Key", trainingKey);
                www.downloadHandler = new DownloadHandlerBuffer();
                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;
                Debug.Log($"Training - JSON Response: {jsonResponse}");

                // A new iteration that has just been created and trained
                Iteration iteration = new Iteration();
                iteration = JsonConvert.DeserializeObject<Iteration>(jsonResponse);

                if (www.isDone)
                {
                    trainingUI_TextMesh.text = "Custom Vision Trained";

                    // Since the Service has a limited number of iterations available,
                    // we need to set the last trained iteration as default
                    // and delete all the iterations you dont need anymore
                    StartCoroutine(SetDefaultIteration(iteration)); 
                }
            }
        }
    ```

11. 新增 **SetDefaultIteration ()** 方法。 這個方法會將先前建立和定型的反復專案設定為 *預設值*。 完成之後，這個方法就必須刪除服務中現有的先前反復專案。 在撰寫本課程時，最多可以在服務中同時存在 10 (10) 次反覆運算。

    ```csharp
        /// <summary>
        /// Set the newly created iteration as Default
        /// </summary>
        private IEnumerator SetDefaultIteration(Iteration iteration)
        {
            yield return new WaitForSeconds(5);
            trainingUI_TextMesh.text = "Setting default iteration";

            // Set the last trained iteration to default
            iteration.IsDefault = true;

            // Convert the iteration object as JSON
            string iterationAsJson = JsonConvert.SerializeObject(iteration);
            byte[] bytes = Encoding.UTF8.GetBytes(iterationAsJson);

            string setDefaultIterationEndpoint = string.Format("{0}{1}/iterations/{2}", 
                                                            url, projectId, iteration.Id);

            using (UnityWebRequest www = UnityWebRequest.Put(setDefaultIterationEndpoint, bytes))
            {
                www.method = "PATCH";
                www.SetRequestHeader("Training-Key", trainingKey);
                www.SetRequestHeader("Content-Type", "application/json");
                www.downloadHandler = new DownloadHandlerBuffer();

                yield return www.SendWebRequest();

                string jsonResponse = www.downloadHandler.text;

                if (www.isDone)
                {
                    trainingUI_TextMesh.text = "Default iteration is set \nDeleting Unused Iteration";
                    StartCoroutine(DeletePreviousIteration(iteration));
                }
            }
        }
    ```

12. 新增 **DeletePreviousIteration ()** 方法。 這個方法會尋找並刪除先前的非預設反復專案：

    ```csharp
        /// <summary>
        /// Delete the previous non-default iteration.
        /// </summary>
        public IEnumerator DeletePreviousIteration(Iteration iteration)
        {
            yield return new WaitForSeconds(5);

            trainingUI_TextMesh.text = "Deleting Unused \nIteration";

            string iterationToDeleteId = string.Empty;

            string findAllIterationsEndpoint = string.Format("{0}{1}/iterations", url, projectId);

            using (UnityWebRequest www = UnityWebRequest.Get(findAllIterationsEndpoint))
            {
                www.SetRequestHeader("Training-Key", trainingKey);
                www.downloadHandler = new DownloadHandlerBuffer();
                yield return www.SendWebRequest();

                string jsonResponse = www.downloadHandler.text;

                // The iteration that has just been trained
                List<Iteration> iterationsList = new List<Iteration>();
                iterationsList = JsonConvert.DeserializeObject<List<Iteration>>(jsonResponse);

                foreach (Iteration i in iterationsList)
                {
                    if (i.IsDefault != true)
                    {
                        Debug.Log($"Cleaning - Deleting iteration: {i.Name}, {i.Id}");
                        iterationToDeleteId = i.Id;
                        break;
                    }
                }
            }

            string deleteEndpoint = string.Format("{0}{1}/iterations/{2}", url, projectId, iterationToDeleteId);

            using (UnityWebRequest www2 = UnityWebRequest.Delete(deleteEndpoint))
            {
                www2.SetRequestHeader("Training-Key", trainingKey);
                www2.downloadHandler = new DownloadHandlerBuffer();
                yield return www2.SendWebRequest();
                string jsonResponse = www2.downloadHandler.text;

                trainingUI_TextMesh.text = "Iteration Deleted";
                yield return new WaitForSeconds(2);
                trainingUI_TextMesh.text = "Ready for next \ncapture";

                yield return new WaitForSeconds(2);
                trainingUI_TextMesh.text = "";
                ImageCapture.Instance.ResetImageCapture();
            }
        }
    ```

13. 要在這個類別中加入的最後一個方法是 **GetImageAsByteArray ()** 方法，用於 web 呼叫，以將捕獲的影像轉換成位元組陣列。

    ```csharp
        /// <summary>
        /// Returns the contents of the specified image file as a byte array.
        /// </summary>
        static byte[] GetImageAsByteArray(string imageFilePath)
        {
            FileStream fileStream = new FileStream(imageFilePath, FileMode.Open, FileAccess.Read);
            BinaryReader binaryReader = new BinaryReader(fileStream);
            return binaryReader.ReadBytes((int)fileStream.Length);
        }
    ```

14. 返回 **Unity** 之前，請務必將您的變更儲存在 **Visual Studio** 中。

## <a name="chapter-10---create-the-sceneorganiser-class"></a>第10章-建立 SceneOrganiser 類別

此類別將會：

-   建立要附加至主要攝影機的資料 **指標** 物件。

-   建立會在服務辨識真實世界物件時出現的 **標籤** 物件。

-   藉由將適當的元件附加至主要攝影機來設定。

-   在 **分析模式** 中，會在執行時間產生標籤，在相對於主要攝影機位置的適當世界空間中產生標籤，並顯示從自訂視覺服務收到的資料。

-   處於 **定型模式** 時，會產生 UI，以顯示定型流程的不同階段。

若要建立此類別：

1.  在 [**腳本**] 資料夾內按一下滑鼠右鍵，然後按一下 [**建立**  >  **C \# 腳本**]。 將腳本命名為 *SceneOrganiser*。

2.  按兩下新的 *SceneOrganiser* 腳本，以 **Visual Studio** 開啟。

3.  您只需要一個命名空間，請將其他命名空間從 *SceneOrganiser* 類別的上方移除：

    ```csharp
    using UnityEngine;
    ```

4.  然後，在 *SceneOrganiser* 類別內，于 **Start ()** 方法的上方新增下列變數：

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static SceneOrganiser Instance;

        /// <summary>
        /// The cursor object attached to the camera
        /// </summary>
        internal GameObject cursor;

        /// <summary>
        /// The label used to display the analysis on the objects in the real world
        /// </summary>
        internal GameObject label;

        /// <summary>
        /// Object providing the current status of the camera.
        /// </summary>
        internal TextMesh cameraStatusIndicator;

        /// <summary>
        /// Reference to the last label positioned
        /// </summary>
        internal Transform lastLabelPlaced;

        /// <summary>
        /// Reference to the last label positioned
        /// </summary>
        internal TextMesh lastLabelPlacedText;

        /// <summary>
        /// Current threshold accepted for displaying the label
        /// Reduce this value to display the recognition more often
        /// </summary>
        internal float probabilityThreshold = 0.5f;
    ```

5.  刪除 [ **開始 ()** ]，並 **更新 ()** 方法。

6.  在變數下方，新增喚醒的 **()** 方法，這會初始化類別並設定場景。

    ```csharp
        /// <summary>
        /// Called on initialization
        /// </summary>
        private void Awake()
        {
            // Use this class instance as singleton
            Instance = this;

            // Add the ImageCapture class to this GameObject
            gameObject.AddComponent<ImageCapture>();

            // Add the CustomVisionAnalyser class to this GameObject
            gameObject.AddComponent<CustomVisionAnalyser>();

            // Add the CustomVisionTrainer class to this GameObject
            gameObject.AddComponent<CustomVisionTrainer>();

            // Add the VoiceRecogniser class to this GameObject
            gameObject.AddComponent<VoiceRecognizer>();

            // Add the CustomVisionObjects class to this GameObject
            gameObject.AddComponent<CustomVisionObjects>();

            // Create the camera Cursor
            cursor = CreateCameraCursor();

            // Load the label prefab as reference
            label = CreateLabel();

            // Create the camera status indicator label, and place it above where predictions
            // and training UI will appear.
            cameraStatusIndicator = CreateTrainingUI("Status Indicator", 0.02f, 0.2f, 3, true);

            // Set camera status indicator to loading.
            SetCameraStatus("Loading");
        }
    ```

7.  現在，請新增 **CreateCameraCursor ()** 方法，以建立並放置主要攝影機游標，以及 **CreateLabel ()** 方法來建立 **分析標籤** 物件。

    ```csharp
        /// <summary>
        /// Spawns cursor for the Main Camera
        /// </summary>
        private GameObject CreateCameraCursor()
        {
            // Create a sphere as new cursor
            GameObject newCursor = GameObject.CreatePrimitive(PrimitiveType.Sphere);

            // Attach it to the camera
            newCursor.transform.parent = gameObject.transform;

            // Resize the new cursor
            newCursor.transform.localScale = new Vector3(0.02f, 0.02f, 0.02f);

            // Move it to the correct position
            newCursor.transform.localPosition = new Vector3(0, 0, 4);

            // Set the cursor color to red
            newCursor.GetComponent<Renderer>().material = new Material(Shader.Find("Diffuse"));
            newCursor.GetComponent<Renderer>().material.color = Color.green;

            return newCursor;
        }

        /// <summary>
        /// Create the analysis label object
        /// </summary>
        private GameObject CreateLabel()
        {
            // Create a sphere as new cursor
            GameObject newLabel = new GameObject();

            // Resize the new cursor
            newLabel.transform.localScale = new Vector3(0.01f, 0.01f, 0.01f);

            // Creating the text of the label
            TextMesh t = newLabel.AddComponent<TextMesh>();
            t.anchor = TextAnchor.MiddleCenter;
            t.alignment = TextAlignment.Center;
            t.fontSize = 50;
            t.text = "";

            return newLabel;
        }
    ```

8. 新增 **SetCameraStatus ()** 方法，這個方法會處理適用于提供相機狀態之文字網格的訊息。

    ```csharp
        /// <summary>
        /// Set the camera status to a provided string. Will be coloured if it matches a keyword.
        /// </summary>
        /// <param name="statusText">Input string</param>
        public void SetCameraStatus(string statusText)
        {
            if (string.IsNullOrEmpty(statusText) == false)
            {
                string message = "white";

                switch (statusText.ToLower())
                {
                    case "loading":
                        message = "yellow";
                        break;

                    case "ready":
                        message = "green";
                        break;

                    case "uploading image":
                        message = "red";
                        break;

                    case "looping capture":
                        message = "yellow";
                        break;

                    case "analysis":
                        message = "red";
                        break;
                }

                cameraStatusIndicator.GetComponent<TextMesh>().text = $"Camera Status:\n<color={message}>{statusText}..</color>";
            }
        }
    ```

9. 新增 **PlaceAnalysisLabel ()** 和 **SetTagsToLastLabel ()** 方法，這會產生自訂視覺服務中的資料，並將其顯示在場景中。

    ```csharp
        /// <summary>
        /// Instantiate a label in the appropriate location relative to the Main Camera.
        /// </summary>
        public void PlaceAnalysisLabel()
        {
            lastLabelPlaced = Instantiate(label.transform, cursor.transform.position, transform.rotation);
            lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();
        }

        /// <summary>
        /// Set the Tags as Text of the last label created. 
        /// </summary>
        public void SetTagsToLastLabel(AnalysisObject analysisObject)
        {
            lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();

            if (analysisObject.Predictions != null)
            {
                foreach (Prediction p in analysisObject.Predictions)
                {
                    if (p.Probability > 0.02)
                    {
                        lastLabelPlacedText.text += $"Detected: {p.TagName} {p.Probability.ToString("0.00 \n")}";
                        Debug.Log($"Detected: {p.TagName} {p.Probability.ToString("0.00 \n")}");
                    }
                }
            }
        }
    ```

10. 最後，新增 **CreateTrainingUI ()** 方法，這將會產生 UI，以在應用程式處於定型模式時，顯示定型程式的多個階段。 此方法也會和轉型，以建立相機狀態物件。

    ```csharp
        /// <summary>
        /// Create a 3D Text Mesh in scene, with various parameters.
        /// </summary>
        /// <param name="name">name of object</param>
        /// <param name="scale">scale of object (i.e. 0.04f)</param>
        /// <param name="yPos">height above the cursor (i.e. 0.3f</param>
        /// <param name="zPos">distance from the camera</param>
        /// <param name="setActive">whether the text mesh should be visible when it has been created</param>
        /// <returns>Returns a 3D text mesh within the scene</returns>
        internal TextMesh CreateTrainingUI(string name, float scale, float yPos, float zPos, bool setActive)
        {
            GameObject display = new GameObject(name, typeof(TextMesh));
            display.transform.parent = Camera.main.transform;
            display.transform.localPosition = new Vector3(0, yPos, zPos);
            display.SetActive(setActive);
            display.transform.localScale = new Vector3(scale, scale, scale);
            display.transform.rotation = new Quaternion();
            TextMesh textMesh = display.GetComponent<TextMesh>();
            textMesh.anchor = TextAnchor.MiddleCenter;
            textMesh.alignment = TextAlignment.Center;
            return textMesh;
        }
    ```

11. 返回 **Unity** 之前，請務必將您的變更儲存在 **Visual Studio** 中。

> [!IMPORTANT]
> 繼續之前，請先開啟 **CustomVisionAnalyser** 類別，然後在 **AnalyseLastImageCaptured ()** 方法中，將下列幾行 *取消* 批註：
>
> ```csharp
>   AnalysisObject analysisObject = new AnalysisObject();
>   analysisObject = JsonConvert.DeserializeObject<AnalysisObject>(jsonResponse);
>   SceneOrganiser.Instance.SetTagsToLastLabel(analysisObject);
> ```

## <a name="chapter-11---create-the-imagecapture-class"></a>第11章-建立 ImageCapture 類別

您即將建立的下一個類別是 *ImageCapture* 類別。

此類別負責：

-   使用 HoloLens 攝影機來捕捉影像，並將它儲存在 *應用程式* 資料夾中。

-   處理使用者的點擊手勢。

-   維護 *列舉* 值，以決定應用程式將會在 *分析* 模式或 *定型* 模式中執行。

若要建立此類別：

1.  移至您先前建立的 **腳本** 資料夾。

2.  在資料夾內按一下滑鼠右鍵，然後按一下 [ **建立 > C \# 腳本**]。 將腳本命名為 *ImageCapture*。

3.  按兩下新的 **ImageCapture** 腳本，以 **Visual Studio** 開啟。

4.  以下列內容取代檔案頂端的命名空間：

    ```csharp
    using System;
    using System.IO;
    using System.Linq;
    using UnityEngine;
    using UnityEngine.XR.WSA.Input;
    using UnityEngine.XR.WSA.WebCam;
    ```

5.  然後，在 *ImageCapture* 類別內，于 **Start ()** 方法的上方新增下列變數：

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static ImageCapture Instance;

        /// <summary>
        /// Keep counts of the taps for image renaming
        /// </summary>
        private int captureCount = 0;

        /// <summary>
        /// Photo Capture object
        /// </summary>
        private PhotoCapture photoCaptureObject = null;

        /// <summary>
        /// Allows gestures recognition in HoloLens
        /// </summary>
        private GestureRecognizer recognizer;

        /// <summary>
        /// Loop timer
        /// </summary>
        private float secondsBetweenCaptures = 10f;

        /// <summary>
        /// Application main functionalities switch
        /// </summary>
        internal enum AppModes {Analysis, Training }
        
        /// <summary>
        /// Local variable for current AppMode
        /// </summary>
        internal AppModes AppMode { get; private set; }

        /// <summary>
        /// Flagging if the capture loop is running
        /// </summary>
        internal bool captureIsActive;
        
        /// <summary>
        /// File path of current analysed photo
        /// </summary>
        internal string filePath = string.Empty;
    ```

6.  現在需要新增 **喚醒 ()** 和 **啟動 ()** 方法的程式碼：

    ```csharp
        /// <summary>
        /// Called on initialization
        /// </summary>
        private void Awake()
        {
            Instance = this;

            // Change this flag to switch between Analysis Mode and Training Mode 
            AppMode = AppModes.Training;
        }

        /// <summary>
        /// Runs at initialization right after Awake method
        /// </summary>
        void Start()
        {
            // Clean up the LocalState folder of this application from all photos stored
            DirectoryInfo info = new DirectoryInfo(Application.persistentDataPath);
            var fileInfo = info.GetFiles();
            foreach (var file in fileInfo)
            {
                try
                {
                    file.Delete();
                }
                catch (Exception)
                {
                    Debug.LogFormat("Cannot delete file: ", file.Name);
                }
            } 

            // Subscribing to the HoloLens API gesture recognizer to track user gestures
            recognizer = new GestureRecognizer();
            recognizer.SetRecognizableGestures(GestureSettings.Tap);
            recognizer.Tapped += TapHandler;
            recognizer.StartCapturingGestures();

            SceneOrganiser.Instance.SetCameraStatus("Ready");
        }
    ```

7.  執行將在點一下手勢發生時呼叫的處理常式。

    ```csharp
        /// <summary>
        /// Respond to Tap Input.
        /// </summary>
        private void TapHandler(TappedEventArgs obj)
        {
            switch (AppMode)
            {
                case AppModes.Analysis:
                    if (!captureIsActive)
                    {
                        captureIsActive = true;

                        // Set the cursor color to red
                        SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.red;
                        
                        // Update camera status to looping capture.
                        SceneOrganiser.Instance.SetCameraStatus("Looping Capture");

                        // Begin the capture loop
                        InvokeRepeating("ExecuteImageCaptureAndAnalysis", 0, secondsBetweenCaptures);
                    }
                    else
                    {
                        // The user tapped while the app was analyzing 
                        // therefore stop the analysis process
                        ResetImageCapture();
                    }
                    break;

                case AppModes.Training:
                    if (!captureIsActive)
                    {
                        captureIsActive = true;

                        // Call the image capture
                        ExecuteImageCaptureAndAnalysis();

                        // Set the cursor color to red
                        SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.red;

                        // Update camera status to uploading image.
                        SceneOrganiser.Instance.SetCameraStatus("Uploading Image");
                    }              
                    break;
            }     
        }
    ```

    > [!NOTE] 
    > 在 *分析* 模式中， **TapHandler** 方法會作為啟動或停止相片捕捉迴圈的參數。
    >
    > 在 *定型* 模式中，它會從相機抓取影像。
    >
    > 當游標為綠色時，表示相機可用來取得影像。
    >
    > 當游標是紅色時，表示相機正在忙碌中。

8.  新增應用程式用來啟動映射捕獲進程並儲存映射的方法。

    ```csharp
        /// <summary>
        /// Begin process of Image Capturing and send To Azure Custom Vision Service.
        /// </summary>
        private void ExecuteImageCaptureAndAnalysis()
        {
            // Update camera status to analysis.
            SceneOrganiser.Instance.SetCameraStatus("Analysis");

            // Create a label in world space using the SceneOrganiser class 
            // Invisible at this point but correctly positioned where the image was taken
            SceneOrganiser.Instance.PlaceAnalysisLabel();

            // Set the camera resolution to be the highest possible
            Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending((res) => res.width * res.height).First();

            Texture2D targetTexture = new Texture2D(cameraResolution.width, cameraResolution.height);

            // Begin capture process, set the image format
            PhotoCapture.CreateAsync(false, delegate (PhotoCapture captureObject)
            {
                photoCaptureObject = captureObject;

                CameraParameters camParameters = new CameraParameters
                {
                    hologramOpacity = 0.0f,
                    cameraResolutionWidth = targetTexture.width,
                    cameraResolutionHeight = targetTexture.height,
                    pixelFormat = CapturePixelFormat.BGRA32
                };

                // Capture the image from the camera and save it in the App internal folder
                captureObject.StartPhotoModeAsync(camParameters, delegate (PhotoCapture.PhotoCaptureResult result)
                {
                    string filename = string.Format(@"CapturedImage{0}.jpg", captureCount);
                    filePath = Path.Combine(Application.persistentDataPath, filename);          
                    captureCount++;              
                    photoCaptureObject.TakePhotoAsync(filePath, PhotoCaptureFileOutputFormat.JPG, OnCapturedPhotoToDisk);              
                });
            });   
        }
    ```

9.  新增在拍攝相片時所要呼叫的處理常式，並在準備進行分析時進行呼叫。 結果接著會根據程式碼的設定模式，傳遞給 *CustomVisionAnalyser* 或 *CustomVisionTrainer* 。

    ```csharp
        /// <summary>
        /// Register the full execution of the Photo Capture. 
        /// </summary>
        void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
        {
                // Call StopPhotoMode once the image has successfully captured
                photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
        }


        /// <summary>
        /// The camera photo mode has stopped after the capture.
        /// Begin the Image Analysis process.
        /// </summary>
        void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
        {
            Debug.LogFormat("Stopped Photo Mode");
        
            // Dispose from the object in memory and request the image analysis 
            photoCaptureObject.Dispose();
            photoCaptureObject = null;

            switch (AppMode)
            {
                case AppModes.Analysis:
                    // Call the image analysis
                    StartCoroutine(CustomVisionAnalyser.Instance.AnalyseLastImageCaptured(filePath));
                    break;

                case AppModes.Training:
                    // Call training using captured image
                    CustomVisionTrainer.Instance.RequestTagSelection();
                    break;
            }
        }

        /// <summary>
        /// Stops all capture pending actions
        /// </summary>
        internal void ResetImageCapture()
        {
            captureIsActive = false;

            // Set the cursor color to green
            SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.green;

            // Update camera status to ready.
            SceneOrganiser.Instance.SetCameraStatus("Ready");

            // Stop the capture loop if active
            CancelInvoke();
        }
    ```

10. 返回 **Unity** 之前，請務必將您的變更儲存在 **Visual Studio** 中。

11. 現在所有的腳本都已完成，請返回 Unity 編輯器，然後按一下 [**腳本**] 資料夾中的 [ **SceneOrganiser** ] 類別，並將其拖曳至 [階層]*面板* 中的 [**主要攝影機**] 物件。

## <a name="chapter-12---before-building"></a>第12章-建立前

若要執行應用程式的完整測試，您必須將它側載到 HoloLens。

在執行之前，請確定：

- [第2章](#chapter-2---training-your-custom-vision-project)中所述的所有設定都已正確設定。

- 系統會正確指派 **主要攝影機**（偵測器面板）中的所有欄位。

- 腳本 **SceneOrganiser** 會附加至 **主要攝影機** 物件。

- 請務必將您的 **預測索引鍵** 插入 **predictionKey** 變數中。

- 您已將 **預測端點** 插入至 **predictionEndpoint** 變數。

- 您已將 **定型金鑰** 插入 *CustomVisionTrainer* 類別的 **trainingKey** 變數中。

- 您已在 *CustomVisionTrainer* 類別的 **projectId** 變數中插入您的 **專案識別碼**。

## <a name="chapter-13---build-and-sideload-your-application"></a>第13章-建立並側載您的應用程式

若要開始 *建立* 程式：

1.  移至 [檔案 **> 組建設定**]。

2.  勾選 **Unity C \# 專案**。

3.  按一下 [建置]。 Unity 將會啟動一個 **檔案總管** 視窗，您需要在其中建立並選取要用來建立應用程式的資料夾。 立即建立該資料夾，並命名為 **應用程式**。 然後選取 [ **應用程式** ] 資料夾，然後按一下 [ **選取資料夾**]。

4.  Unity 將開始將您的專案建立到 **應用程式** 資料夾。

5.  Unity 完成組建之後 (可能需要一些時間) ，它會在您的組建位置開啟 **檔案總管** 視窗 (檢查您的工作列，因為它不一定會出現在您的視窗上方，但會通知您加入新的視窗) 。

若要在 HoloLens 上部署：

1.  您將需要 HoloLens (的 IP 位址，才能進行遠端部署) ，並確保 HoloLens 處於 **開發人員模式**。 若要這樣做：

    1.  在設置 HoloLens 的同時，開啟 **設定**。

    2.  前往 **Network & Internet**  >  **wi-fi**  >  **Advanced Options**

    3.  記下 **IPv4** 位址。

    4.  接下來，流覽回到 [**設定**]，然後 **更新**  >  **開發人員 & 的** 安全性

    5.  設定 [ **開發人員模式]**。

2.  流覽至您的新 Unity 組建 (**應用程式** 資料夾) ，然後以 **Visual Studio** 開啟方案檔。

3.  在 [ *方案* 設定] 中選取 [ **Debug**]。

4.  在 *解決方案平臺* 中，選取 [ **x86]、[遠端電腦**]。 系統會提示您將遠端裝置的 **IP 位址** 插入 (HoloLens，在此案例中，您會記下) 。

    ![設定 IP 位址](images/AzureLabs-Lab302b-34.png)

5. 移至 [ **組建** ] 功能表，然後按一下 [ **部署方案** ]，將應用程式側載至 HoloLens。

6. 您的應用程式現在應該會出現在 HoloLens 上已安裝的應用程式清單中，準備好可供啟動！

> [!NOTE]
> 若要部署到沉浸式耳機，請將 **解決方案平臺****設定為 [** *本機電腦*]，並將 [設定] 設定為 [以 *x86* 作為 **平臺**] 來進行 *Debug*。 然後使用 [ **組建** ] 功能表項目選取 [ *部署方案*]，部署到本機電腦。 

## <a name="to-use-the-application"></a>若要使用應用程式：

若要在 *定型* 模式與 *預測* 模式之間切換應用程式功能，您必須更新位於 *ImageCapture* 類別內的 **喚醒 ()** 方法中的 **AppMode** 變數。

```
        // Change this flag to switch between Analysis mode and Training mode 
        AppMode = AppModes.Training;
```
或
```
        // Change this flag to switch between Analysis mode and Training mode 
        AppMode = AppModes.Analysis;
```

在 *定型* 模式中：

- 查看 **滑鼠** 或 **鍵盤** ，然後使用 [點一下 **手勢**]。

- 接下來會出現文字，要求您提供標記。

- 說的是 **滑鼠** 或 **鍵盤**。


在 *預測* 模式中：

- 查看物件，並使用 **點擊手勢**。

- 文字將會出現，並提供偵測到的物件，機率最高 (這是正規化) 。

## <a name="chapter-14---evaluate-and-improve-your-custom-vision-model"></a>第14章-評估及改善您的自訂視覺模型

若要讓您的服務更加精確，您必須繼續定型用於預測的模型。 這是透過使用您的新應用程式（包含 *定型* 和 *預測* 模式）來完成，而後者則需要您造訪入口網站，這是本章所涵蓋的內容。 準備重新流覽您的入口網站多次，以持續改善您的模型。

1. 再次前往您的 Azure 自訂視覺入口網站，並在您的專案中選取 [ *預測* ] 索引標籤， (從頁面的左上角開始) ：

    ![選取 [預測] 索引標籤](images/AzureLabs-Lab302b-35.png)

2. 當您的應用程式執行時，您會看到所有已傳送至服務的影像。 如果您將滑鼠停留在影像上，則會為您提供針對該影像所做的預測：

    ![預測影像清單](images/AzureLabs-Lab302b-36.png)

3. 選取其中一個影像來開啟它。 開啟之後，您將會看到對該影像所做的預測是在右邊。 如果您的預測正確無誤，而且您想要將此影像新增至服務的定型模型，請按一下 [ *我的標記* ] 輸入方塊，然後選取您想要建立關聯的標記。 當您完成時，請按一下右下角的 [ *儲存並關閉* ] 按鈕，然後繼續進行下一個影像。

    ![選取要開啟的影像](images/AzureLabs-Lab302b-37.png)

4. 回到影像的方格之後，您會注意到，您已將標記新增至 (並儲存) 的影像將會被移除。 如果您找到任何您認為沒有標記的項目的影像，則可以將其刪除，方法是按一下該影像上的刻度， (可以針對數個影像進行這項作業) 然後按一下格線頁右上角的 [ *刪除* ]。 在接下來的快顯視窗中，您可以按一下 *[是]、[刪除]* 或 [ *否*]，以分別確認刪除或取消。 

    ![刪除映像](images/AzureLabs-Lab302b-38.png)

5. 當您準備好繼續進行時，請按一下右上方的綠色 [ *定型* ] 按鈕。 您的服務模型將會使用您現在提供的所有影像來定型， (如此可讓) 更準確。 定型完成後，請務必按一下 [ *設為預設值* ] 按鈕，讓您的 *預測 URL* 繼續使用您服務的最新反復專案。

    ![開始訓練服務模型 ](images/AzureLabs-Lab302b-39.png) ![ 選取 [設為預設值] 選項](images/AzureLabs-Lab302b-40.png)

## <a name="your-finished-custom-vision-api-application"></a>您完成的自訂視覺 API 應用程式

恭喜，您已建立混合的現實應用程式，利用 Azure 自訂視覺 API 來辨識真實世界物件、訓練服務模型，以及顯示已看到內容的信心。

![完成的專案範例](images/AzureLabs-Lab302b-00.png)

## <a name="bonus-exercises"></a>額外練習

### <a name="exercise-1"></a>練習1

訓練您的 **自訂視覺服務** ，以辨識更多物件。

### <a name="exercise-2"></a>練習2

若要展開您學到的內容，請完成下列練習：

辨識物件時播放音效。

### <a name="exercise-3"></a>練習3

使用 API 以您的應用程式所分析的相同影像來重新定型您的服務，以便讓服務更準確 (同時) 預測和定型。