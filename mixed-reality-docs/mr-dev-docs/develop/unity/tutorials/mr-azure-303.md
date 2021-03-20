---
title: 'HoloLens (第1代) 和 Azure 303-自然語言理解 (LUIS) '
description: 完成本課程，以瞭解如何在混合現實應用程式中 (LUIS) 來實行 Azure Language Understanding 智慧服務。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure，混合的現實，學術，unity，教學課程，api，語言理解智慧服務，luis，hololens，沉浸，vr，Windows 10，Visual Studio
ms.openlocfilehash: 663ac44dbf15ce2db63d7ffe0ecc605d3555857f
ms.sourcegitcommit: 35bd43624be33afdb1bf6ba4ddbe36d268eb9bda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/20/2021
ms.locfileid: "104730555"
---
# <a name="hololens-1st-gen-and-azure-303-natural-language-understanding-luis"></a>HoloLens (第1代) 和 Azure 303：自然語言理解 (LUIS) 

<br>

>[!NOTE]
>混合實境學院教學課程的設計是以 HoloLens (第 1 代) 和混合實境沉浸式頭戴裝置為準。  因此，對於仍在尋找這些裝置開發指引的開發人員而言，我們覺得這些教學課程很重要。  這些教學課程 **_不會_** 使用用於 HoloLens 2 的最新工具組或互動進行更新。  系統會保留這些資訊，以繼續在支援的裝置上運作。 未來將會有一系列新的教學課程，將會示範如何針對 HoloLens 2 進行開發。  當張貼這些教學課程時，將會使用這些教學課程的連結來更新此通知。

<br>

在此課程中，您將瞭解如何使用 Azure 認知服務搭配 Language Understanding API，將 Language Understanding 整合至混合現實應用程式。

![實驗室結果](images/AzureLabs-Lab3-000.png)

*Language Understanding (LUIS)* 是 Microsoft Azure 服務，可讓應用程式從使用者輸入中提出意義，例如透過以自己的單字來解壓縮人物可能想要的內容。 這是透過機器學習來達成，它會瞭解並學習輸入資訊，然後可以使用詳細、相關的資訊來回複。 如需詳細資訊，請造訪 [Azure Language Understanding (LUIS) 頁面](https://azure.microsoft.com/services/cognitive-services/language-understanding-intelligent-service/)。

完成本課程之後，您將會有一個混合現實的沉浸式耳機應用程式，可以執行下列動作：

1.  使用連接到沉浸式耳機的麥克風來捕捉使用者輸入語音。 
2.  將 *Azure Language Understanding 智慧型服務* 的已捕捉聽寫傳送 (*LUIS*) 。 
3.  讓 LUIS 從傳送資訊中解壓縮意義，這會進行分析，並嘗試判斷使用者要求的意圖。

開發過程中會建立應用程式，讓使用者能夠使用語音和/或注視來變更場景中物件的大小和色彩。 將不會涵蓋移動控制器的使用。

在您的應用程式中，您可以自行決定如何將結果與您的設計整合。 本課程旨在告訴您如何整合 Azure 服務與您的 Unity 專案。 您的工作是使用您在本課程中所得到的知識，來增強您的混合現實應用程式。

準備訓練 LUIS 數次，其涵蓋于第 [12 章](#chapter-12--improving-your-luis-service)。 LUIS 定型的次數愈多，您將會得到更好的結果。

## <a name="device-support"></a>裝置支援

<table>
<tr>
<th>課程</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">沉浸式頭戴裝置</a></th>
</tr><tr>
<td>MR 和 Azure 303：自然語言理解 (LUIS) </td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> 雖然本課程主要著重于 Windows Mixed Reality 沉浸式 (VR) 耳機，您也可以將在本課程中學到的內容套用至 Microsoft HoloLens。 當您依照課程的指示進行時，您將會看到有關您可能需要採用以支援 HoloLens 的任何變更的注意事項。 使用 HoloLens 時，您可能會注意到語音捕捉期間的一些回應。

## <a name="prerequisites"></a>Prerequisites

> [!NOTE]
> 本教學課程是專為擁有 Unity 和 c # 基本經驗的開發人員所設計。 另外也請注意，本檔中的必要條件和撰寫的指示，代表在撰寫 (可能是 2018) 時經過測試和驗證的內容。 You are free to use the latest software, as listed within the [install the tools](../../install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.

本課程建議您採用下列硬體和軟體：

- 開發電腦，與適用于沉浸式 (VR) 耳機開發的[Windows Mixed Reality 相容](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines)
- [啟用開發人員模式的 Windows 10 Fall Creators Update (或更新版本) ](../../install-the-tools.md)
- [最新的 Windows 10 SDK](../../install-the-tools.md)
- [Unity 2017。4](../../install-the-tools.md)
- [Visual Studio 2017](../../install-the-tools.md)
- [Windows Mixed Reality 沉浸式 (VR) 耳機](../../../discover/immersive-headset-hardware-details.md)，或已啟用開發人員模式的[Microsoft HoloLens](/hololens/hololens1-hardware)
- 一組具有內建麥克風的耳機 (如果耳機沒有內建的 mic 和喇叭) 
- 適用于 Azure 設定和 LUIS 抓取的網際網路存取

## <a name="before-you-start"></a>在您開始使用 Intune 之前

1.  為了避免在建立此專案時發生問題，強烈建議您在根或近端根資料夾中，建立本教學課程中所述的專案 (長的資料夾路徑可能會在組建階段) 時發生問題。 
2.  若要允許您的電腦啟用聽寫，請移至 [ **Windows 設定] > 隱私權 > 語音]、筆墨 & 輸入** ，然後按下按鈕 **開啟語音服務和輸入建議**。
3.  本教學課程中的程式碼可讓您從電腦上的 **預設麥克風裝置** 集錄製。 請確定預設的麥克風裝置已設定為您想要用來捕捉聲音的裝置。
4.  如果您的耳機有內建的麥克風，請在 *混合實境入口* 設定中，確定已開啟 [*當我磨損耳機、切換到耳機 mic]* 選項。

    ![設定沉浸式耳機](images/AzureLabs-Lab3-00.png)

## <a name="chapter-1--setup-azure-portal"></a>第1章-設定 Azure 入口網站

若要在 Azure 中使用 *Language Understanding* 服務，您必須將服務的實例設定為可供應用程式使用。

1.  登入 [Azure 入口網站](https://portal.azure.com)。

    > [!NOTE]
    > 如果您還沒有 Azure 帳戶，您將需要建立一個帳戶。 如果您在課堂或實驗室的情況下進行本教學課程，請洽詢講師或其中一個 proctors，協助您設定新的帳戶。

2.  登入後，按一下左上角的 [ **新增** ]，並搜尋 *Language Understanding*，然後按一下 **Enter 鍵**。 

    ![建立 LUIS 資源](images/AzureLabs-Lab3-01.png)

    > [!NOTE]
    > 在較新的入口網站中，[**建立資源**] 可能已取代 **新** 的文字。
 
3.  右側的新頁面將提供 Language Understanding 服務的描述。 在此頁面的左下方，選取 [ **建立** ] 按鈕，以建立此服務的實例。

    ![LUIS 服務建立-法律注意事項](images/AzureLabs-Lab3-02.png)
 
4.  當您按一下 [建立] 之後：

    1. 為此服務實例插入您想要的 **名稱** 。
    2. 選取 [訂用帳戶]  。
    3. 選取適合您的 **定價層** ，如果這是您第一次建立 *LUIS 服務*，您應該可以使用名為 F0) 的免費層 (。 在此課程中，免費配置應已足夠。
    4. 選擇資源群組，或建立一個新的 **資源群組** 。 資源群組提供一種方式來監視、控制存取、布建及管理 Azure 資產集合的計費。 建議您保留與單一專案相關聯的所有 Azure 服務 (例如，) 一般資源群組下的這些課程) 。 

        > 如果您想要閱讀更多有關 Azure 資源群組的資訊，請 [造訪資源群組文章](/azure/azure-resource-manager/resource-group-portal)。

    5. 如果您要建立新的資源群組) ，請判斷資源群組 (的 **位置** 。 位置最好是在應用程式執行所在的區域中。 某些 Azure 資產僅適用于某些區域。
    6. 您也必須確認您已瞭解套用到此服務的條款及條件。
    7. 選取 [建立]  。

        ![建立 LUIS 服務-使用者輸入](images/AzureLabs-Lab3-03.png)
 
5.  當您按一下 [ **建立**] 之後，就必須等待服務建立完成，這可能需要一分鐘的時間。
6.  建立服務實例之後，入口網站中就會出現通知。 
 
    ![新的 Azure 通知影像](images/AzureLabs-Lab3-04.png)

7.  按一下通知以探索新的服務實例。

    ![成功建立資源通知](images/AzureLabs-Lab3-05.png)
 
8.  按一下通知中的 [ **移至資源** ] 按鈕，以流覽您的新服務實例。 您將會進入新的 LUIS 服務實例。 
 
    ![存取 LUIS 金鑰](images/AzureLabs-Lab3-06.png)

9.  在本教學課程中，您的應用程式將需要呼叫您的服務，這是透過使用服務的訂用帳戶金鑰來完成。
10. 在 *LUIS API* 服務的 [*快速入門*] 頁面中，流覽至第一個步驟、*抓取您的金鑰*，然後按一下 [機 **碼**] (您也可以按一下位於 [服務] 導覽功能表中的藍色超連結鍵（以按鍵圖示) 表示）來達成此目的。 這會顯示您的服務 *金鑰*。
11. 複製其中一個顯示的金鑰，您稍後會在專案中使用。 
12. 在 [ *服務* ] 頁面中，按一下 *Language Understanding 入口網站* ，以重新導向至您將在 LUIS 應用程式中用來建立新服務的網頁。 

## <a name="chapter-2--the-language-understanding-portal"></a>第2章-Language Understanding 入口網站

在本節中，您將瞭解如何在 LUIS 入口網站中建立 LUIS 應用程式。 

> [!IMPORTANT]
> 請注意，在本章節中設定 *實體*、 *意圖* 和 *語句* 的第一個步驟是建立 LUIS 服務的第一個步驟：您也需要重新定型服務數次，以使其更精確。 本課程的 [最後一章](#chapter-12--improving-your-luis-service) 涵蓋了重新訓練您的服務，因此請確定您已完成。

1.  到達 *Language Understanding 入口網站* 時，您可能需要登入（如果尚未登入），其認證與您的 Azure 入口網站相同。 

    ![LUIS 登入頁面](images/AzureLabs-Lab3-07.png)
 
2.  如果這是您第一次使用 LUIS，您將需要向下滾動至 [歡迎使用] 頁面的底部，以尋找並按一下 [ **建立 LUIS 應用程式** ] 按鈕。

    ![建立 LUIS 應用程式頁面](images/AzureLabs-Lab3-08.png)
 
3.  登入之後，如果您目前不在該區段中) ，請按一下 [ **我的應用程式** (。 然後，您可以按一下 [ **建立新的應用程式**]。

    ![LUIS-我的應用程式影像](images/AzureLabs-Lab3-09.png)
 
4.  為您的應用程式 *命名*。
5.  如果您的應用程式應該瞭解與英文不同的語言，您應該將 *文化* 特性變更為適當的語言。
6.  您也可以在這裡新增新 LUIS 應用程式的 *描述* 。

    ![LUIS-建立新的應用程式](images/AzureLabs-Lab3-10.png)

7.  當您按下 [**完成**] 之後，您將會進入新 *LUIS* 應用程式的 [*組建*] 頁面。
8.  這裡有幾個重要的概念需要瞭解：

    -   *意圖*，代表將在使用者的查詢之後呼叫的方法。 *意圖* 可能會有一或多個 *實體*。
    -   *實體* 是查詢的元件，可描述與 *意圖* 相關的資訊。
    -   *語句* 是開發人員提供的查詢範例，LUIS 將使用它來定型本身。

如果這些概念並非完全清楚，請別擔心，因為本課程將在本章進一步說明這些概念。

首先，您會建立建立此課程所需的 *實體* 。

9.  在頁面的左側，按一下 [ *實體*]，然後按一下 [ **建立新實體**]。

    ![建立新的實體](images/AzureLabs-Lab3-11.png)

10. 呼叫新的實體 *色彩*，將其類型設定為 *Simple*，然後按下 [ **完成**]。

    ![建立簡單實體-色彩](images/AzureLabs-Lab3-12.png)
 
11. 重複此程式，以建立三個 (3) 更簡單的實體，名為：

    -   *將*
    -   *縮小*
    -   *目標*

結果看起來應該如下圖所示：

![建立實體的結果](images/AzureLabs-Lab3-13.png)
 
您現在可以開始建立 *意圖*。 

> [!WARNING]
> 請勿刪除「 **無** 」意圖。

12. 在頁面左側按一下 [ **意圖**]，然後按一下 [ **建立新意圖**]。

    ![建立新的意圖](images/AzureLabs-Lab3-14.png)

13. 呼叫新 *意圖* **ChangeObjectColor**。

    > [!IMPORTANT]
    > 這個 *意圖* 名稱是在本課程稍後的程式碼中使用，因此為了獲得最佳結果，請完全依照提供的方式使用此名稱。

一旦您確認名稱，系統會將您導向 [意圖] 頁面。

![LUIS-意圖頁面](images/AzureLabs-Lab3-15.png)

您會發現有一個文字方塊要求您輸入5個以上的不同 *語句*。

> [!NOTE]
> LUIS 會將所有語句轉換成小寫。

14. 在頂端的文字方塊中插入下列 *語句*， (目前具有 *大約5個範例* 的文字類型 .。。 ) ，然後按 **enter**：

```
The color of the cylinder must be red
```

您將會注意到，新的 *語句* 會顯示在下方清單中。

遵循相同的程式，插入下列六個 (6) 語句：

```
make the cube black

make the cylinder color white

change the sphere to red

change it to green

make this yellow

change the color of this object to blue
```

針對您已建立的每個語句，您必須識別 LUIS 做為實體應使用哪些字組。 在此範例中，您必須將所有色彩標示為 *色彩* 實體，並將所有的可能參考標示為 *目標* 實體。

15. 若要這樣做，請嘗試在第一個語句中按一下 [單字 *圓柱* ]，然後選取 [ *目標*]。

    ![識別語句目標](images/AzureLabs-Lab3-16.png)
 
16. 現在按一下第一個語句中的 *紅色* 文字，然後選取 [ *色彩*]。

    ![識別語句實體](images/AzureLabs-Lab3-17.png)
 
17. 為下一行加上標籤，其中 *cube* 應該是 *目標*，而 *黑色* 應為 *色彩*。 另外也請注意，我們所提供的「 *this*」、「 *it*」和「 *這個物件*」這幾個字，因此也有非特定的目標型別可供使用。 

18. 重複上述程式，直到所有語句都已標示實體為止。 如果您需要協助，請參閱下圖。

    > [!TIP]
    > 選取字組將其標示為實體時：
    > - 若為單一單字，請按一下它們。
    > - 針對一組兩個或多個字組，按一下開頭，然後在集合結尾。

    > [!NOTE]
    > 您可以使用 [ *標記視圖* ] 切換按鈕，在 **實體/標記視圖** 之間切換！

19. 結果應該如下列影像所示，顯示 [ **實體/權杖] 視圖**：

    ![& 實體視圖的權杖](images/AzureLabs-Lab3-18.png)
  
20. 此時按下頁面右上方的 [ **定型** ] 按鈕，並等候其上的小圓形指標變成綠色。 這表示 LUIS 已成功定型以辨識此意圖。

    ![訓練 LUIS](images/AzureLabs-Lab3-19.png)
 
21. 做為您的練習，使用實體 *目標*、*升遷* 和 *縮減*，建立名為 **ChangeObjectSize** 的新意圖。
22. 遵循先前意圖的相同程式，插入下列八個 (8) 語句以進行 *大小* 變更：

    ```
    increase the dimensions of that

    reduce the size of this

    i want the sphere smaller

    make the cylinder bigger

    size down the sphere

    size up the cube

    decrease the size of that object

    increase the size of this object
    ```

23. 結果應該類似下圖中的結果：

    ![設定 ChangeObjectSize 權杖/實體](images/AzureLabs-Lab3-20.png) 

24. 一旦建立並定型了 **ChangeObjectColor** 和 **ChangeObjectSize** 這兩個意圖，請按一下頁面頂端的 [ **發行** ] 按鈕。

    ![發佈 LUIS 服務](images/AzureLabs-Lab3-21.png)

25. 在 [ *發佈* ] 頁面上，您將會完成併發布您的 LUIS 應用程式，讓您的程式碼可以存取它。

    1. 將 [ *發行* ] 下拉式清單設定為 [ **生產**]。
    2. 將 *時區* 設定為時區。
    3. 核取 [ **包含所有預測的意圖分數**] 核取方塊。
    4. 按一下 [ **發行至生產** 位置]。

        ![發行設定](images/AzureLabs-Lab3-22.png)

26. 在 [ *資源和金鑰*] 區段中：

    1.  在 Azure 入口網站中，選取您為服務實例設定的區域。
    2.  您會注意到以下的 **Starter_Key** 元素，請忽略它。
    3.  按一下 [ **新增金鑰** ]，然後插入您在 Azure 入口網站中建立服務實例時所取得的 *金鑰* 。 如果您的 Azure 和 LUIS 入口網站已登入相同的使用者，您將會得到 *租使用者名稱*、訂用帳戶 *名稱* 和您想要使用之 *金鑰* 的下拉式功能表， (將會與您先前在 Azure 入口網站中提供的名稱相同。

    > [!IMPORTANT] 
    > 在 [ *端點*] 底下，取得對應至您所插入金鑰的端點複本，您很快就會在程式碼中使用它。
 
## <a name="chapter-3--set-up-the-unity-project"></a>第3章-設定 Unity 專案

以下是使用混合式開發進行開發的一般設定，因此，它是適用于其他專案的絕佳範本。

1.  開啟 *Unity* ，然後按一下 [ **新增**]。 

    ![開始新的 Unity 專案。](images/AzureLabs-Lab3-24.png)

2.  您現在將需要提供 Unity 專案名稱、插入 **MR_LUIS**。 請確定專案類型設定為 **3d**。 將 **位置** 設定為適合您 (記住，較接近根目錄的) 。 然後，按一下 [ **建立專案**]。

    ![提供新 Unity 專案的詳細資料。](images/AzureLabs-Lab3-25.png)
 
3.  在 Unity 開啟的情況下，值得檢查預設 **腳本編輯器** 是否設定為 **Visual Studio**。 移至 [編輯] > 喜好設定，然後在新視窗中，流覽至 [ **外部工具**]。 將 **外部腳本編輯器** 變更為 **Visual Studio 2017**。 關閉 [ **喜好** 設定] 視窗。

    ![更新腳本編輯器喜好設定。](images/AzureLabs-Lab3-26.png)
 
4.  接著，移至 [檔案 **> 組建設定**]，然後按一下 [**切換平臺**] 按鈕，將平臺切換至 **通用 Windows 平臺**。

    ![[組建設定] 視窗，將平臺切換至 UWP。](images/AzureLabs-Lab3-27.png)
 
5.  移至 [檔案 **> 組建設定** ]，並確定：

    1. **目標裝置** 已設定為 **任何裝置**

        > 針對 Microsoft HoloLens，請將 **目標裝置** 設定為 *HoloLens*。

    2. **組建類型** 設定為 **D3D**
    3. **SDK** 已設定為 **最新安裝**
    4. **Visual Studio 版本** 設定為 **最新安裝**
    5. **組建並執行** 設定為 **本機電腦**
    6. 儲存場景，並將其新增至組建。

        1. 若要這麼做，請選取 [ **新增開啟的場景**]。 [儲存] 視窗隨即出現。
        
            ![按一下 [新增開啟場景] 按鈕](images/AzureLabs-Lab3-28.png)

        2. 為此和任何未來的場景建立新的資料夾，然後選取 [ **新增資料夾** ] 按鈕，建立新的資料夾，將它命名為 **場景**。

            ![建立新的腳本資料夾](images/AzureLabs-Lab3-29.png)

        3. 開啟新建立的 **場景** 資料夾，然後在 [ *檔案名*：文字] 欄位中輸入 **MR_LuisScene**，然後按 [ **儲存**]。

            ![提供新場景的名稱。](images/AzureLabs-Lab3-30.png)

    7. [ *組建設定*] 中的其餘設定，現在應該保持為預設值。

6. 在 [ *組建設定* ] 視窗中，按一下 [ **播放程式設定** ] 按鈕，這會開啟偵測 *器* 所在空間中的相關面板。 

    ![開啟 [播放玩家設定]。](images/AzureLabs-Lab3-31.png) 
 
7. 在此面板中，需要驗證幾個設定：

    1. 在 [ **其他設定** ] 索引標籤中：

        1. **腳本執行階段版本** 應該是 **穩定** 的 ( .net 3.5 對等) 。
        2. **腳本後端** 應該是 **.net**
        3. **API 相容性層級** 應為 **.net 4.6**

            ![更新其他設定。](images/AzureLabs-Lab3-32.png)
      
    2. 在 [ **發行設定** ] 索引標籤的 [ **功能**] 下，選取：

        1. **InternetClient**
        2. **麥克風**

            ![正在更新發行設定。](images/AzureLabs-Lab3-33.png)

    3. 在面板的 [XR 設定] 中，在 [ **設定** ] (找到的 [ **發佈設定** ]) 、[滴答 **虛擬實境支援**]，請確定已新增 **Windows Mixed Reality SDK** 。

        ![更新 X R 設定。](images/AzureLabs-Lab3-34.png)

8.  回到 *組建設定*： _Unity c #_ 專案不再呈現灰色;勾選此方塊旁邊的核取方塊。 
9.  關閉 [建置設定] 視窗。
10. 將場景和專案儲存 (檔 **> 儲存場景/檔案 > 儲存專案**) 。

## <a name="chapter-4--create-the-scene"></a>第4章-建立場景

> [!IMPORTANT]
> 如果您想要略過此課程的 *Unity 設定* 元件，並直接繼續進行程式碼，請隨意下載 [unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20303%20-%20Natural%20language%20understanding/Azure-MR-303.unitypackage)，並將其匯入到您的專案中做為 [自訂套件](https://docs.unity3d.com/Manual/AssetPackages.html)，然後繼續進行 [第5章](#chapter-5--create-the-microphonemanager-class)。 

1.  在 [階層] *面板* 的空白區域中，以滑鼠右鍵按一下 [ **3d 物件**] 下的 [加入 **平面**]。

    ![建立平面。](images/AzureLabs-Lab3-35.png)

2.  請注意，當您以滑鼠右鍵按一下階層內以建立更多物件時，如果您仍然選取最後一個物件，則選取的物件將會是新物件的父系。 請避免在階層內的空白處按一下滑鼠左鍵，然後以滑鼠右鍵按一下。

3.  重複上述程式來新增下列物件：

    1. *Sphere*
    2. *圓柱*
    3. *Cube*
    4. *3D 文字*

4.  產生 *的場景階層* 應如下圖所示：

    ![場景階層設定。](images/AzureLabs-Lab3-36.png)
 
5.  以滑鼠左鍵按一下 **主要攝影機** 來選取它，然後查看 [偵測 *器] 面板* ，您將會看到攝影機物件及其所有元件。
6.  按一下位於 [偵測 *器] 面板* 最底部的 [**新增元件**] 按鈕。

    ![新增音訊來源](images/AzureLabs-Lab3-37.png)
 
7.  搜尋稱為 *音訊來源* 的元件，如上所示。
8.  此外，請確定主要攝影機的 *轉換* 元件已設定為 (0、0、0) ，您可以按下相機 *轉換* 元件旁邊的 **齒輪** 圖示，然後選取 [**重設**] 來完成此操作。 接著， *轉換* 元件看起來應該像這樣：

    1.  *Position* 設定為 **0、0、0**。
    2.  *旋轉* 設定為 **0、0、0**。

    > [!NOTE] 
    > 針對 Microsoft HoloLens，您也必須變更下列內容，這是 **相機** 元件的一部分，也就是您的 **主要攝影機**：
    > - **清除旗標：** 純色。
    > - **背景** ' 黑色，Alpha 0 ' –十六進位色彩： #00000000。

9.  以滑鼠左鍵按一下 **平面** 即可選取。 在 [偵測 *器] 面板* 中，使用下列值設定 *轉換* 元件：

    |   X 軸    | Y 軸 |   Z 軸    |
    |:-----:|:----------------------:|:-----:|
    | 0     | -1                     | 0     |


10. 以滑鼠左鍵按一下 **球體** 以選取它。 在 [偵測 *器] 面板* 中，使用下列值設定 *轉換* 元件：

    |   X 軸    | Y 軸 |   Z 軸    |
    |:-----:|:----------------------:|:-----:|
    | 2     | 1                      | 2     |

11. 以滑鼠左鍵按一下 **圓柱** 以選取它。 在 [偵測 *器] 面板* 中，使用下列值設定 *轉換* 元件：

    |   X 軸    | Y 軸 |   Z 軸    |
    |:-----:|:----------------------:|:-----:|
    | -2    | 1                      | 2     |

12. 在 **Cube** 上按一下滑鼠左鍵即可選取它。 在 [偵測 *器] 面板* 中，使用下列值設定 *轉換* 元件：

    |        | 轉換- *位置* |       |  \| |       | 轉換- *旋轉* |       |
    |:------:|:----------------------:|:-----:|:---:|:-----:|:----------------------:|:-----:|
    | **X** | **Y**                   | **Z** |  \| | **X** | **Y**                  | **Z** |
    | 0     | 1                       | 4     |  \| | 45    | 45                     | 0     | 

13. 以滑鼠左鍵按一下 **新的文字** 物件，即可選取它。 在 [偵測 *器] 面板* 中，使用下列值設定 *轉換* 元件：

    |       | 轉換- *位置* |       |  \| |       | 轉換- *調整規模* |       |
    |:-----:|:----------------------:|:-----:|:---:|:-----:|:-------------------:|:-----:|
    | **X** | **Y**                  | **Z** |  \| | **X** | **Y**               | **Z** |
    | -2    | 6                      | 9     |  \| | 0.1   | 0.1                 | 0.1   | 

14. 將 **文字網格** 元件中的 **字型大小** 變更為 **50**。
15. 將 **文字網格** 物件的 *名稱* 變更為 **聽寫文字**。

    ![建立3D 文字物件](images/AzureLabs-Lab3-38.png)
 
16. 階層面板結構現在看起來應該像這樣：

    ![場景視圖中的文字網格](images/AzureLabs-Lab3-38b.png)


17. 最後的場景看起來應該如下圖所示：

    ![場景視圖。](images/AzureLabs-Lab3-39.png)
    
 
## <a name="chapter-5--create-the-microphonemanager-class"></a>第5章-建立 MicrophoneManager 類別

您即將建立的第一個腳本是 *MicrophoneManager* 類別。 接下來，您將建立 *LuisManager*、 *行為* 類別和最後一個 *注視* 類別 (歡迎您立即建立這些類別，不過您會在每一章) 討論。

*MicrophoneManager* 類別負責：

-   偵測連接到耳機或電腦的錄製裝置 (以預設的) 為准。
-   捕捉音訊 (語音) 並使用聽寫將其儲存為字串。
-   聲音暫停之後，請將聽寫提交至 *LuisManager* 類別。 

若要建立此類別： 

1.  在 [ *專案] 面板* 中按一下滑鼠右鍵， **建立 > 資料夾**。 呼叫資料夾 **腳本**。 

    ![建立腳本資料夾。](images/AzureLabs-Lab3-40.png)
 
2.  在 [ **腳本** ] 資料夾建立後，按兩下以開啟。 然後，在該資料夾中，以滑鼠右鍵按一下， **建立 > c # 腳本**。 將腳本命名為 *MicrophoneManager*。 

3.  按兩下 [ *MicrophoneManager* ] 以 *Visual Studio* 開啟。
4.  將下列命名空間新增至檔案頂端：

    ```csharp
        using UnityEngine;
        using UnityEngine.Windows.Speech;
    ```

5.  然後，在 *MicrophoneManager* 類別內新增下列變數：

    ```csharp
        public static MicrophoneManager instance; //help to access instance of this object
        private DictationRecognizer dictationRecognizer;  //Component converting speech to text
        public TextMesh dictationText; //a UI object used to debug dictation result
    ``` 

6.  現在需要新增 *喚醒 ()* 和 *啟動 ()* 方法的程式碼。 當類別初始化時，就會呼叫這些內容：

    ```csharp
        private void Awake()
        {
            // allows this class instance to behave like a singleton
            instance = this;
        }

        void Start()
        {
            if (Microphone.devices.Length > 0)
            {
                StartCapturingAudio();
                Debug.Log("Mic Detected");
            }
        }
    ```
 
7.  現在您需要應用程式用來啟動和停止語音捕捉的方法，並將它傳遞給 *LuisManager* 類別，您很快就會建立。 

    ```csharp
        /// <summary>
        /// Start microphone capture, by providing the microphone as a continual audio source (looping),
        /// then initialise the DictationRecognizer, which will capture spoken words
        /// </summary>
        public void StartCapturingAudio()
        {
            if (dictationRecognizer == null)
            {
                dictationRecognizer = new DictationRecognizer
                {
                    InitialSilenceTimeoutSeconds = 60,
                    AutoSilenceTimeoutSeconds = 5
                };

                dictationRecognizer.DictationResult += DictationRecognizer_DictationResult;
                dictationRecognizer.DictationError += DictationRecognizer_DictationError;
            }
            dictationRecognizer.Start();
            Debug.Log("Capturing Audio...");
        }

        /// <summary>
        /// Stop microphone capture
        /// </summary>
        public void StopCapturingAudio()
        {
            dictationRecognizer.Stop();
            Debug.Log("Stop Capturing Audio...");
        }
    ```

8.  新增語音暫停時將叫用的 *聽寫處理常式* 。 這個方法會將聽寫文字傳遞至 *LuisManager* 類別。

    ```csharp
        /// <summary>
        /// This handler is called every time the Dictation detects a pause in the speech. 
        /// This method will stop listening for audio, send a request to the LUIS service 
        /// and then start listening again.
        /// </summary>
        private void DictationRecognizer_DictationResult(string dictationCaptured, ConfidenceLevel confidence)
        {
            StopCapturingAudio();
            StartCoroutine(LuisManager.instance.SubmitRequestToLuis(dictationCaptured, StartCapturingAudio));
            Debug.Log("Dictation: " + dictationCaptured);
            dictationText.text = dictationCaptured;
        }

        private void DictationRecognizer_DictationError(string error, int hresult)
        {
            Debug.Log("Dictation exception: " + error);
        }
    ```
 
    > [!IMPORTANT]
    > 刪除 *更新 ()* 方法，因為此類別不會使用它。

9.  返回 *Unity* 之前，請務必將您的變更儲存在 *Visual Studio* 中。

    > [!NOTE]
    > 此時您會注意到 *Unity 編輯器主控台面板* 中出現錯誤。 這是因為程式碼會參考您將在下一章中建立的 *LuisManager* 類別。

## <a name="chapter-6--create-the-luismanager-class"></a>第6章-建立 LUISManager 類別

您現在可以建立 *LuisManager* 類別，這會呼叫 Azure LUIS 服務。 

此類別的目的是要接收來自 *MicrophoneManager* 類別的聽寫文字，並將它傳送到要分析的 *Azure Language Understanding API* 。

此類別會將 *JSON* 回應還原序列化，並呼叫 *行為* 類別的適當方法來觸發動作。

若要建立此類別： 

1.  按兩下 [ **腳本** ] 資料夾以開啟它。 
2.  在 [ **腳本** ] 資料夾內按一下滑鼠右鍵，然後按一下 [ **建立 > c # 腳本**]。 將腳本命名為 *LuisManager*。 
3.  按兩下腳本，以 Visual Studio 來開啟它。
4.  將下列命名空間新增至檔案頂端：

    ```csharp
        using System;
        using System.Collections;
        using System.Collections.Generic;
        using System.IO;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

5.  您一開始會在 *LuisManager* 類別 **內建立三個類別，** (在相同腳本檔中的相同腳本檔案內 *()* ，) 將代表從 Azure 還原序列化的 JSON 回應。

    ```csharp
        [Serializable] //this class represents the LUIS response
        public class AnalysedQuery
        {
            public TopScoringIntentData topScoringIntent;
            public EntityData[] entities;
            public string query;
        }

        // This class contains the Intent LUIS determines 
        // to be the most likely
        [Serializable]
        public class TopScoringIntentData
        {
            public string intent;
            public float score;
        }

        // This class contains data for an Entity
        [Serializable]
        public class EntityData
        {
            public string entity;
            public string type;
            public int startIndex;
            public int endIndex;
            public float score;
        }
    ```

6.  接下來，在 *LuisManager* 類別內新增下列變數：
 
    ```csharp
        public static LuisManager instance;

        //Substitute the value of luis Endpoint with your own End Point
        string luisEndpoint = "https://westus.api.cognitive... add your endpoint from the Luis Portal";
    ```

7.  請務必將您的 LUIS 端點立即放入您的 LUIS 入口網站)  (。

8.  現在需要新增 *喚醒 ()* 方法的程式碼。 當類別初始化時，會呼叫這個方法：

    ```csharp
        private void Awake()
        {
            // allows this class instance to behave like a singleton
            instance = this;
        }
    ```

9.  現在您需要此應用程式用來將接收自 *MicrophoneManager* 類別的聽寫傳送給 *LUIS*，然後接收和還原序列化回應的方法。 
10. 一旦決定意圖的值和相關聯的實體之後，就會將它們傳遞給 *行為* 類別的實例，以觸發預期的動作。

    ```csharp
        /// <summary>
        /// Call LUIS to submit a dictation result.
        /// The done Action is called at the completion of the method.
        /// </summary>
        public IEnumerator SubmitRequestToLuis(string dictationResult, Action done)
        {
            string queryString = string.Concat(Uri.EscapeDataString(dictationResult));

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Get(luisEndpoint + queryString))
            {
                yield return unityWebRequest.SendWebRequest();

                if (unityWebRequest.isNetworkError || unityWebRequest.isHttpError)
                {
                    Debug.Log(unityWebRequest.error);
                }
                else
                {
                    try
                    {
                        AnalysedQuery analysedQuery = JsonUtility.FromJson<AnalysedQuery>(unityWebRequest.downloadHandler.text);

                        //analyse the elements of the response 
                        AnalyseResponseElements(analysedQuery);
                    }
                    catch (Exception exception)
                    {
                        Debug.Log("Luis Request Exception Message: " + exception.Message);
                    }
                }

                done();
                yield return null;
            }
        }
    ```
 
11. 建立稱為 *AnalyseResponseElements ()* 的新方法，它會讀取產生的 *AnalysedQuery* 並判斷實體。 一旦決定這些實體，就會將它們傳遞給 *行為* 類別的實例，以在動作中使用。

    ```csharp
        private void AnalyseResponseElements(AnalysedQuery aQuery)
        {
            string topIntent = aQuery.topScoringIntent.intent;

            // Create a dictionary of entities associated with their type
            Dictionary<string, string> entityDic = new Dictionary<string, string>();

            foreach (EntityData ed in aQuery.entities)
            {
                entityDic.Add(ed.type, ed.entity);
            }

            // Depending on the topmost recognized intent, read the entities name
            switch (aQuery.topScoringIntent.intent)
            {
                case "ChangeObjectColor":
                    string targetForColor = null;
                    string color = null;

                    foreach (var pair in entityDic)
                    {
                        if (pair.Key == "target")
                        {
                            targetForColor = pair.Value;
                        }
                        else if (pair.Key == "color")
                        {
                            color = pair.Value;
                        }
                    }

                    Behaviours.instance.ChangeTargetColor(targetForColor, color);
                    break;

                case "ChangeObjectSize":
                    string targetForSize = null;
                    foreach (var pair in entityDic)
                    {
                        if (pair.Key == "target")
                        {
                            targetForSize = pair.Value;
                        }
                    }

                    if (entityDic.ContainsKey("upsize") == true)
                    {
                        Behaviours.instance.UpSizeTarget(targetForSize);
                    }
                    else if (entityDic.ContainsKey("downsize") == true)
                    {
                        Behaviours.instance.DownSizeTarget(targetForSize);
                    }
                    break;
            }
        }
    ```
 
    > [!IMPORTANT]
    > 刪除 *開始 ()* 並 *更新 ()* 方法，因為此類別不會使用它們。

12. 返回 *Unity* 之前，請務必將您的變更儲存在 *Visual Studio* 中。

> [!NOTE]
> 此時您會注意到 *Unity 編輯器主控台面板* 中出現數個錯誤。 這是因為程式碼會參考您將在下一章中建立的 *行為* 類別。

## <a name="chapter-7--create-the-behaviours-class"></a>第7章-建立行為類別

*行為* 類別會使用 *LuisManager* 類別所提供的實體來觸發動作。

若要建立此類別： 

1.  按兩下 [ **腳本** ] 資料夾以開啟它。 
2.  在 [ **腳本** ] 資料夾內按一下滑鼠右鍵，然後按一下 [ **建立 > c # 腳本**]。 將腳本命名為 *行為*。 
3.  按兩下腳本，以 *Visual Studio* 來開啟它。
4.  然後，在 *行為* 類別內新增下列變數：

    ```csharp
        public static Behaviours instance;

        // the following variables are references to possible targets
        public GameObject sphere;
        public GameObject cylinder;
        public GameObject cube;
        internal GameObject gazedTarget;
    ```
 
5.  新增 *喚醒的 ()* 方法程式碼。 當類別初始化時，會呼叫這個方法：

    ```csharp
        void Awake()
        {
            // allows this class instance to behave like a singleton
            instance = this;
        }
    ```
 
6.  您) 先前建立的 *LuisManager* 類別 (會呼叫下列方法，以判斷哪一個物件是查詢的目標，然後觸發適當的動作。

    ```csharp
        /// <summary>
        /// Changes the color of the target GameObject by providing the name of the object
        /// and the name of the color
        /// </summary>
        public void ChangeTargetColor(string targetName, string colorName)
        {
            GameObject foundTarget = FindTarget(targetName);
            if (foundTarget != null)
            {
                Debug.Log("Changing color " + colorName + " to target: " + foundTarget.name);

                switch (colorName)
                {
                    case "blue":
                        foundTarget.GetComponent<Renderer>().material.color = Color.blue;
                        break;

                    case "red":
                        foundTarget.GetComponent<Renderer>().material.color = Color.red;
                        break;

                    case "yellow":
                        foundTarget.GetComponent<Renderer>().material.color = Color.yellow;
                        break;

                    case "green":
                        foundTarget.GetComponent<Renderer>().material.color = Color.green;
                        break;

                    case "white":
                        foundTarget.GetComponent<Renderer>().material.color = Color.white;
                        break;

                    case "black":
                        foundTarget.GetComponent<Renderer>().material.color = Color.black;
                        break;
                }          
            }
        }

        /// <summary>
        /// Reduces the size of the target GameObject by providing its name
        /// </summary>
        public void DownSizeTarget(string targetName)
        {
            GameObject foundTarget = FindTarget(targetName);
            foundTarget.transform.localScale -= new Vector3(0.5F, 0.5F, 0.5F);
        }

        /// <summary>
        /// Increases the size of the target GameObject by providing its name
        /// </summary>
        public void UpSizeTarget(string targetName)
        {
            GameObject foundTarget = FindTarget(targetName);
            foundTarget.transform.localScale += new Vector3(0.5F, 0.5F, 0.5F);
        }
    ```
 
7.  新增 *FindTarget ()* 方法，以判斷哪一個 *Gameobject* 是目前意圖的目標。 如果未在實體中定義明確的目標，則這個方法會將目標設為 "gazed" 的 *GameObject* 。

    ```csharp
        /// <summary>
        /// Determines which object reference is the target GameObject by providing its name
        /// </summary>
        private GameObject FindTarget(string name)
        {
            GameObject targetAsGO = null;

            switch (name)
            {
                case "sphere":
                    targetAsGO = sphere;
                    break;

                case "cylinder":
                    targetAsGO = cylinder;
                    break;

                case "cube":
                    targetAsGO = cube;
                    break;

                case "this": // as an example of target words that the user may use when looking at an object
                case "it":  // as this is the default, these are not actually needed in this example
                case "that":
                default: // if the target name is none of those above, check if the user is looking at something
                    if (gazedTarget != null) 
                    {
                        targetAsGO = gazedTarget;
                    }
                    break;
            }
            return targetAsGO;
        }
    ```
 
    > [!IMPORTANT]
    > 刪除 *開始 ()* 並 *更新 ()* 方法，因為此類別不會使用它們。

8.  返回 *Unity* 之前，請務必將您的變更儲存在 *Visual Studio* 中。

## <a name="chapter-8--create-the-gaze-class"></a>第8章-建立注視類別

完成此應用程式所需的最後一個類別是 *注視* 類別。 此類別會更新目前在使用者視覺效果焦點中之 *GameObject* 的參考。

若要建立此類別： 

1.  按兩下 [ **腳本** ] 資料夾以開啟它。 
2.  在 [ **腳本** ] 資料夾內按一下滑鼠右鍵，然後按一下 [ **建立 > c # 腳本**]。 將腳本命名為 *注視*。 
3.  按兩下腳本，以 *Visual Studio* 來開啟它。
4.  針對此類別插入下列程式碼：

    ```csharp
        using UnityEngine;

        public class Gaze : MonoBehaviour
        {        
            internal GameObject gazedObject;
            public float gazeMaxDistance = 300;

            void Update()
            {
                // Uses a raycast from the Main Camera to determine which object is gazed upon.
                Vector3 fwd = gameObject.transform.TransformDirection(Vector3.forward);
                Ray ray = new Ray(Camera.main.transform.position, fwd);
                RaycastHit hit;
                Debug.DrawRay(Camera.main.transform.position, fwd);

                if (Physics.Raycast(ray, out hit, gazeMaxDistance) && hit.collider != null)
                {
                    if (gazedObject == null)
                    {
                        gazedObject = hit.transform.gameObject;

                        // Set the gazedTarget in the Behaviours class
                        Behaviours.instance.gazedTarget = gazedObject;
                    }
                }
                else
                {
                    ResetGaze();
                }         
            }

            // Turn the gaze off, reset the gazeObject in the Behaviours class.
            public void ResetGaze()
            {
                if (gazedObject != null)
                {
                    Behaviours.instance.gazedTarget = null;
                    gazedObject = null;
                }
            }
        }
    ```
 
5.  返回 *Unity* 之前，請務必將您的變更儲存在 *Visual Studio* 中。

## <a name="chapter-9--completing-the-scene-setup"></a>第9章–完成場景設定

1.  若要完成場景的設定，請將您在 [腳本] 資料夾中建立的每個腳本拖曳至 [階層]*面板* 中的 [**主要攝影機**] 物件。
2.  選取 **主要攝影機** ，然後查看 [偵測 *器] 面板*，您應該可以看到您已附加的每個腳本，而您會發現每個尚未設定的腳本都有參數。

    ![設定相機參考目標。](images/AzureLabs-Lab3-41.png)

3.  若要正確設定這些參數，請遵循下列指示：

    1. *MicrophoneManager*：

        - 從 [階層] *面板* 中，將 [ **聽寫文字** ] 物件拖曳到 [ **聽寫文字** 參數] 值方塊中。

    2. *行為*，從 [階層] *面板*：

        - 將 **球體** 物件拖曳到 [ *球體* 參考目標] 方塊中。
        - 將 **圓柱** 拖曳至 [ *圓柱* 參考目標] 方塊。
        - 將 **cube** 拖曳至 [ *cube* 參考目標] 方塊中。

    3. *注視*：

        - 將 [ *注視最大距離* ] 設定為 [ **300** ] (如果尚未) 。 

4.  結果看起來應該如下圖所示：

    ![現在已設定相機參考目標。](images/AzureLabs-Lab3-42.png)
 
## <a name="chapter-10--test-in-the-unity-editor"></a>第10章-在 Unity 編輯器中測試

測試是否已正確實行場景設定。

請確定：

-   所有的腳本都會附加至 **主要攝影機** 物件。 
-   *主要相機偵測器面板* 中的所有欄位都已正確指派。

1.  按下 *Unity 編輯器* 中的 [**播放**] 按鈕。 應用程式應該在附加的沉浸式耳機內執行。

2.  請嘗試幾個語句，例如：

    ```
    make the cylinder red

    change the cube to yellow

    I want the sphere blue

    make this to green

    change it to white
    ```

    > [!NOTE]
    > 如果您在 Unity 主控台中看到關於預設音訊裝置變更的錯誤，場景可能無法如預期般運作。 這是因為混合現實入口網站處理有內建麥克風的方式。 如果您看到此錯誤，只需停止場景並重新啟動，就應該會如預期般運作。

## <a name="chapter-11--build-and-sideload-the-uwp-solution"></a>第11章-建立並側載 UWP 解決方案

確定應用程式在 Unity 編輯器中運作之後，您就可以開始建立和部署。

若要建立：

1.  按一下 [檔案] **> 儲存**]，以儲存目前的場景。
2.  移至 [檔案 **> 組建設定**]。
3.  勾選稱為「 **Unity c # 專案** 」的方塊 (在建立 UWP 專案之後，用來查看和偵錯工具代碼。
4.  按一下 [ **新增開啟的場景**]，然後按一下 [ **建立**]。

    ![[組建設定] 視窗](images/AzureLabs-Lab3-43.png)

4.  系統會提示您選取要在其中建立解決方案的資料夾。 

5.  建立 *組建* 資料夾，然後在該資料夾內使用您選擇的適當名稱建立另一個資料夾。 
6.  按一下 [ **選取資料夾** ]，在該位置開始組建。
 
    ![建立組建資料夾 ](images/AzureLabs-Lab3-44.png)
     ![ 選取組建資料夾](images/AzureLabs-Lab3-45.png)
 
7.  Unity 完成組建之後 (可能需要一些時間) ，它應該會在您的組建位置開啟 **檔案總管** 視窗。

若要在本機電腦上部署：

1.  在 *Visual Studio* 中，開啟 [上一章](#chapter-10--test-in-the-unity-editor)所建立的方案檔。
2.  在 [ **方案平臺**] 中，選取 [ **x86**]、[ **本機電腦**]。
3.  在 [ **方案** 設定] 中選取 [ **Debug**]。

    > 在 Microsoft HoloLens 中，您可能會發現將此設定為 *遠端電腦* 較容易，因此不會行動網卡到您的電腦。 不過，您也必須執行下列動作：
    > - 知道您 HoloLens 的 **IP 位址** ，您可以在 *設定 > 網路 & 網際網路 > Wi-Fi > Advanced 選項* 中找到此位址;IPv4 是您應該使用的位址。 
    > - 確定已 **開啟****開發人員模式**;在 [設定] 中找到 *> 為開發人員更新 & 安全性 >*。

    ![部署應用程式](images/AzureLabs-Lab3-46.png)
 
4.  移至 [ **組建] 功能表** ，然後按一下 [ **部署方案** ]，將應用程式側載至您的電腦。
5.  您的應用程式現在應該會出現在已安裝的應用程式清單中，準備好可供啟動！
6.  啟動後，應用程式會提示您授權 _麥克風_ 的存取權。 使用 *移動控制器*、 *語音輸入* 或 *鍵盤* 按 [ **是]** 按鈕。 

## <a name="chapter-12--improving-your-luis-service"></a>第12章–改善您的 LUIS 服務

>[!IMPORTANT] 
> 這一章十分重要，而且可能需要反復執行數次，因為它可協助改善 LUIS 服務的精確度：請確定您已完成這項工作。

若要改善 LUIS 所提供的理解層級，您需要捕捉新的語句，並使用它們來重新定型您的 LUIS 應用程式。

例如，您可能已訓練 LUIS 來瞭解「增加」和「升遷」，但您不希望應用程式也能瞭解「放大」這類的文字嗎？

一旦使用您的應用程式數次之後，您所說的所有專案都將由 LUIS 收集，並可在 LUIS 入口網站中取得。

1.  移至您的入口網站應用程式，並在此 [連結](https://www.luis.ai/home)之後登入。
2.  使用您的 MS 認證登入後，請按一下您的 *應用程式名稱*。
3.  按一下頁面左側的 [ **審核端點語句** ] 按鈕。

    ![複習語句](images/AzureLabs-Lab3-47.png)
 
4.  您將會看到您的混合現實應用程式傳送給 LUIS 的語句清單。

    ![語句清單](images/AzureLabs-Lab3-48.png)
 
您將會注意到一些醒目提示的 *實體*。 

藉由將滑鼠游標停留在每個醒目提示的單字上方，您就可以檢查每個語句並判斷正確辨識的實體、哪些實體錯誤，以及遺漏了哪些實體。

在上述範例中，發現 "魚叉式" 一字已反白顯示為目標，因此必須更正錯誤，方法是將滑鼠游標移到單字上，然後按一下 [ **移除標籤**]。

![檢查語句 ](images/AzureLabs-Lab3-49.png)
 ![ 移除標籤影像](images/AzureLabs-Lab3-50.png)
 
5.  如果您找到完全錯誤的語句，您可以使用畫面右側的 [ **刪除** ] 按鈕將它們刪除。

    ![刪除錯誤的語句](images/AzureLabs-Lab3-51.png)

6.  或者，如果您覺得 LUIS 已正確地解讀語句，您可以使用 [ **加入至對齊意圖** ] 按鈕來驗證它的理解。

    ![新增至對齊的意圖](images/AzureLabs-Lab3-52.png)

7.  當您將所有顯示的語句排序之後，請嘗試並重載頁面，以查看是否有更多可用。
8.  請務必盡可能重複此程式，以改善您的應用程式理解。 

**祝您順利！**

## <a name="your-finished-luis-integrated-application"></a>您完成的 LUIS 整合式應用程式

恭喜您，您建立了一個利用 Azure Language Understanding 智慧服務的混合現實應用程式，以瞭解使用者所說的內容，並對該資訊採取行動。

![實驗室結果](images/AzureLabs-Lab3-000.png)

## <a name="bonus-exercises"></a>額外練習

### <a name="exercise-1"></a>練習1

在使用此應用程式時，您可能會注意到，如果您看著 Floor 物件，並要求變更其色彩，則會這樣做。 您是否可以用來避免應用程式變更地面色彩？

### <a name="exercise-2"></a>練習2

嘗試擴充 LUIS 和應用程式功能，為場景中的物件新增額外的功能;例如，根據使用者顯示的內容，在注視的位置建立新的物件，然後透過現有的命令，將這些物件與目前的場景物件一起使用。