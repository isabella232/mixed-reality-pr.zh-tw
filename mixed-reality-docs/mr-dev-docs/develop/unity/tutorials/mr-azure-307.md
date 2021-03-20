---
title: HoloLens (第1代) 和 Azure 307-機器學習
description: 完成本課程，以瞭解如何在混合現實應用程式內執行 Azure Machine Learning Studio (傳統) 。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure，mixed reality，學術，unity，教學課程，api，機器學習，ml，machine learning studio，hololens，沉浸，vr，Windows 10，Visual Studio
ms.openlocfilehash: c9d6408d41340b1c0fcb1f41b61d84ba115258c3
ms.sourcegitcommit: 35bd43624be33afdb1bf6ba4ddbe36d268eb9bda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/20/2021
ms.locfileid: "104730515"
---
# <a name="hololens-1st-gen-and-azure-307-machine-learning"></a>HoloLens (第1代) 和 Azure 307：機器學習

<br>

>[!NOTE]
>混合實境學院教學課程的設計是以 HoloLens (第 1 代) 和混合實境沉浸式頭戴裝置為準。  因此，對於仍在尋找這些裝置開發指引的開發人員而言，我們覺得這些教學課程很重要。  這些教學課程 **_不會_** 使用用於 HoloLens 2 的最新工具組或互動進行更新。  系統會保留這些資訊，以繼續在支援的裝置上運作。 未來將會有一系列新的教學課程，將會示範如何針對 HoloLens 2 進行開發。  當張貼這些教學課程時，將會使用這些教學課程的連結來更新此通知。

<br>

![最終產品-開始](images/AzureLabs-Lab7-0.png)

在此課程中，您將瞭解如何使用 Azure Machine Learning Studio (傳統) ，將 Machine Learning (ML) 功能新增至混合現實應用程式。

*Azure Machine Learning Studio (傳統)* 是一項 Microsoft 服務，可為開發人員提供大量的機器學習演算法，協助您進行資料輸入、輸出、準備和視覺化。 您可以從這些元件開發預測性分析實驗、逐一查看，並使用它來定型您的模型。 在訓練之後，您可以讓您的模型在 Azure 雲端中運作，讓它可以對新資料進行評分。 如需詳細資訊，請造訪 [Azure Machine Learning Studio (傳統) 頁面](https://azure.microsoft.com/services/machine-learning-studio/)。

完成本課程之後，您將會有混合現實的沉浸式耳機應用程式，並已瞭解如何執行下列動作：

1.  提供 *Azure Machine Learning Studio (傳統)* 入口網站的銷售資料表格，並設計演算法來預測熱門專案的未來銷售。
2.  建立 **Unity 專案**，它可以接收和解讀來自 ML 服務的預測資料。
3.  透過在貨架上提供最受歡迎的銷售專案，以視覺化方式在 **Unity 專案** 中顯示 predication 的資料。

在您的應用程式中，您可以自行決定如何將結果與您的設計整合。 本課程旨在告訴您如何整合 Azure 服務與您的 Unity 專案。 您的工作是使用您在本課程中所得到的知識，來增強您的混合現實應用程式。

本課程是獨立的教學課程，不會直接牽涉到任何其他混合的現實實驗室。

## <a name="device-support"></a>裝置支援

<table>
<tr>
<th>課程</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">沉浸式頭戴裝置</a></th>
</tr><tr>
<td> MR 和 Azure 307：機器學習</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> 雖然本課程主要著重于 Windows Mixed Reality 沉浸式 (VR) 耳機，您也可以將在本課程中學到的內容套用至 Microsoft HoloLens。 當您依照課程的指示進行時，您將會看到有關您可能需要採用以支援 HoloLens 的任何變更的注意事項。 使用 HoloLens 時，您可能會注意到語音捕捉期間的一些回應。

## <a name="prerequisites"></a>Prerequisites

> [!NOTE]
> 本教學課程是專為擁有 Unity 和 c # 基本經驗的開發人員所設計。 另外也請注意，本檔中的必要條件和撰寫的指示，代表在撰寫 (可能是 2018) 時經過測試和驗證的內容。 您可以隨意使用最新的軟體（如 [ 安裝工具文章](../../install-the-tools.md)中所列），但不應假設此課程中的資訊會完全符合您在較新軟體中找到的資訊，而不是以下所列的資訊。

本課程建議您採用下列硬體和軟體：

- 開發電腦，與適用于沉浸式 (VR) 耳機開發的[Windows Mixed Reality 相容](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines)
- [啟用開發人員模式的 Windows 10 Fall Creators Update (或更新版本) ](../../install-the-tools.md#installation-checklist)
- [最新的 Windows 10 SDK](../../install-the-tools.md#installation-checklist)
- [Unity 2017。4](../../install-the-tools.md#installation-checklist)
- [Visual Studio 2017](../../install-the-tools.md#installation-checklist)
- [Windows Mixed Reality 沉浸式 (VR) 耳機](../../../discover/immersive-headset-hardware-details.md)，或已啟用開發人員模式的[Microsoft HoloLens](/hololens/hololens1-hardware)
- 適用于 Azure 設定和 ML 資料抓取的網際網路存取

## <a name="before-you-start"></a>在您開始使用 Intune 之前

為了避免在建立此專案時發生問題，強烈建議您在根或近端根資料夾中，建立本教學課程中所述的專案 (長的資料夾路徑可能會在組建階段) 時發生問題。 

## <a name="chapter-1---azure-storage-account-setup"></a>第1章-Azure 儲存體帳戶設定

若要使用 Azure Translator API，您必須將服務的實例設定為可供應用程式使用。
1.  登入  [Azure 入口網站](https://portal.azure.com)。

    > [!NOTE]
    > 如果您還沒有 Azure 帳戶，您將需要建立一個帳戶。 如果您在課堂或實驗室的情況下進行本教學課程，請洽詢講師或其中一個 proctors，協助您設定新的帳戶。

2.  登入後，按一下左側功能表中的 [ **儲存體帳戶** ]。

    ![Azure 儲存體帳戶設定](images/AzureLabs-Lab7-1.png)

    > [!NOTE]
    > 在較新的入口網站中，[**建立資源**] 可能已取代 **新** 的文字。

3.  在 [ **儲存體帳戶** ] 索引標籤上，按一下 [ **新增**]。

    ![Azure 儲存體帳戶設定](images/AzureLabs-Lab7-2.png)

4.  在 [ **建立儲存體帳戶** ] 面板中：

    1.  為您的帳戶插入 **名稱** ，請注意，此欄位只接受數位和小寫字母。
    2.  在 [ **部署模型] 中，** 選取 [ **資源管理員**]。
    3.  針對 [ **帳戶類型**]，選取 **[儲存體 (一般用途 v1)**。
    4.  針對 [效能]，請選取 [標準]。
    5.  若 **為複寫** ，請選取 [ **讀取權限-異地-多餘儲存體] (GRS])**。
    6.  將 [ **需要安全傳輸** ] 保留為 **停用**。
    7.  選取 [訂用帳戶]  。
    4. 選擇資源群組，或建立一個新的 **資源群組** 。 資源群組提供一種方式來監視、控制存取、布建及管理 Azure 資產集合的計費。 建議您保留與單一專案相關聯的所有 Azure 服務 (例如，) 一般資源群組下的實驗室，) 。

        > 如果您想要閱讀更多有關 Azure 資源群組的資訊，請 [造訪資源群組文章](/azure/azure-resource-manager/resource-group-portal)。
    
    5.  如果您要建立新的資源群組) ，請判斷資源群組 (的 **位置** 。 位置最好是在應用程式執行所在的區域中。 某些 Azure 資產僅適用于某些區域。

5.  您也必須確認您已瞭解套用到此服務的條款及條件。

    ![Azure 儲存體帳戶設定](images/AzureLabs-Lab7-3.png)

6.  當您按一下 [ **建立**] 之後，就必須等待服務建立完成，這可能需要一分鐘的時間。

7.  建立服務實例之後，入口網站中就會出現通知。

    ![Azure 儲存體帳戶設定](images/AzureLabs-Lab7-4.png)

## <a name="chapter-2---the-azure-machine-learning-studio--classic"></a>第2章-Azure Machine Learning Studio (傳統) 

若要使用 *Azure Machine Learning*，您必須將 Machine Learning 服務的實例設定為可供應用程式使用。

1.  在 Azure 入口網站中，按一下左上角的 [ **新增** ]，然後搜尋 **Machine Learning Studio 工作區**，按 **enter**。

    ![Azure Machine Learning Studio (傳統) ](images/AzureLabs-Lab7-5.png)

2.  新頁面將提供 **Machine Learning Studio 工作區**  服務的描述。 在此提示的左下方，按一下 [ **建立** ] 按鈕，以建立與此服務的關聯。

3.  當您按一下 [ **建立**] 之後，就會出現一個面板，您必須在其中提供有關新 **Machine Learning Studio 服務** 的一些詳細資料：

    1.  為此服務實例插入您想要的 **工作區名稱** 。

    2.  選取 [訂用帳戶]  。

    3. 選擇資源群組，或建立一個新的 **資源群組** 。 資源群組提供一種方式來監視、控制存取、布建及管理 Azure 資產集合的計費。 建議您保留與單一專案相關聯的所有 Azure 服務 (例如，) 一般資源群組下的實驗室，) 。 

        > 如果您想要閱讀更多有關 Azure 資源群組的資訊，請 [造訪資源群組文章](/azure/azure-resource-manager/resource-group-portal)。

    4.  如果您要建立新的資源群組) ，請判斷資源群組 (的 **位置** 。 位置最好是在應用程式執行所在的區域中。 某些 Azure 資產僅適用于某些區域。 您應該使用您在上一章中用來建立 Azure 儲存體的相同資源群組。

    5.  在 [ **儲存體帳戶** ] 區段中，按一下 [ **使用現有** 的]，然後按一下下拉式功能表，然後按一下您在上一章所建立的 **儲存體帳戶** 。

    6.  從下拉式功能表中，為您選取適當的 **工作區定價層** 。

    7.  在 [ **Web 服務方案**] 區段中，按一下 [**建立****新** 的]，然後在文字欄位中插入它的名稱。

    8.  從 [ **Web 服務方案定價層** ] 區段中，選取您選擇的定價層。 您可以免費使用稱為 **DEVTEST Standard** 的開發測試層。

    9.  您也必須確認您已瞭解套用到此服務的條款及條件。

    10. 按一下頁面底部的 [新增]  。

        ![Azure Machine Learning Studio (傳統) ](images/AzureLabs-Lab7-6.png)

4.  當您按一下 [ **建立**] 之後，就必須等待服務建立完成，這可能需要一分鐘的時間。

5.  建立服務實例之後，入口網站中就會出現通知。

    ![Azure Machine Learning Studio (傳統) ](images/AzureLabs-Lab7-7.png)

6.  按一下通知以探索新的服務實例。

    ![Azure Machine Learning Studio (傳統) ](images/AzureLabs-Lab7-8.png)

7.  按一下通知中的 [ **移至資源** ] 按鈕，以流覽您的新服務實例。

8.  在顯示的頁面中，按一下 [ **其他連結** ] 區段下的 [ **啟動 Machine Learning Studio**]，這會將您的瀏覽器導向 **Machine Learning studio** 入口網站。

    ![Azure Machine Learning Studio (傳統) ](images/AzureLabs-Lab7-9.png)

9.  使用右上角或中央的 [登 **入** ] 按鈕，登入您的 Machine Learning Studio (傳統) 。

    ![Azure Machine Learning Studio (傳統) ](images/AzureLabs-Lab7-10.png)


## <a name="chapter-3---the-machine-learning-studio-classic-dataset-setup"></a>第3章-Machine Learning Studio (傳統) ：資料集設定

Machine Learning 演算法的其中一種方式就是分析現有的資料，然後根據現有的資料集嘗試預測未來的結果。 這通常表示您擁有的資料愈多，演算法在預測未來結果時的效能就越好。

系統會為您提供範例資料表，在此課程中稱為 [ProductsTableCSV，可在此下載](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20307%20-%20Machine%20learning/MR%20and%20Azure%20307%20-%20Machine%20learning.zip)。

> [!IMPORTANT]
> 上述 .zip 檔案包含 **ProductsTableCSV** 和 **unitypackage**，您將在 [第6章](#chapter-6---importing-the-mlproducts-unity-package)中所需的檔案。 這一章也會提供此封裝，但與 csv 檔案分開。

此範例資料集會在2017年每天的每個小時，包含最佳銷售物件的記錄。
        
![Machine Learning Studio (傳統) ：資料集設定](images/AzureLabs-Lab7-11.png)

例如，在2017的第1天，下午 (小時 13) ，最暢銷的專案是 salt 和辣椒。

此範例資料表包含9998個專案。

1.  回到 **Machine Learning Studio (傳統)** 入口網站，並新增此資料表作為 ML 的 **資料集** 。 若要這麼做，請按一下螢幕左下角的 [ **+ 新增** ] 按鈕。

    ![Machine Learning Studio (傳統) ：資料集設定](images/AzureLabs-Lab7-12.png)

2.  區段會從底端開始，而左側會有導覽面板。 按一下 [資料集]，然後按一下 [**本機** 檔案] 中的 [**資料集**]。

    ![Machine Learning Studio (傳統) ：資料集設定](images/AzureLabs-Lab7-13.png)

3.  遵循下列步驟來上傳新的 **資料集** ：

    1. [上傳] 視窗隨即出現，您可以在其中 **流覽** 硬碟以取得新的資料集。

        ![Machine Learning Studio (傳統) ：資料集設定](images/AzureLabs-Lab7-14.png)

    2.  一旦選取後，再返回 [上傳] 視窗，請將核取方塊保留為未核取。

    3.  在下方的文字欄位中，輸入 **ProductsTableCSV.csv** 作為資料集的名稱， (不過應該自動新增) 。

    4.  使用 [ **類型**] 的下拉式功能表，選取 **標頭 ( .csv) 的 [一般 csv** 檔案]。

    5.  按下 [上傳] 視窗右下角的刻度，將會上傳您的 **資料集** 。

## <a name="chapter-4---the-machine-learning-studio-classic-the-experiment"></a>第4章-Machine Learning Studio (傳統) ：實驗

建立您的機器學習系統之前，您必須先建立實驗，以驗證您的資料理論。 有了結果，您將知道您是否需要更多資料，或是資料和可能的結果之間沒有相互關聯。

若要開始建立實驗：

1.  再次按一下頁面左下方的 [ **+ 新增**] 按鈕，然後按一下 [**實驗**  >  **空白實驗**]。

    ![Machine Learning Studio (傳統) ：實驗](images/AzureLabs-Lab7-15.png)

2.  新的頁面會顯示為空白實驗：

3.  從左側面板中，展開 [**儲存的資料集**  >  **我的資料集**]，並將 [ **ProductsTableCSV** ] 拖曳至 **實驗畫布**。

    ![Machine Learning Studio (傳統) ：實驗](images/AzureLabs-Lab7-16.png)

4.  在左側面板中，展開 [**資料轉換**  >  **範例和分割**]。 然後將 **分割資料** 專案拖曳至 **實驗畫布**。 分割資料項目會將資料集分割成兩個部分。 您將用來定型機器學習演算法的一個部分。 第二個部分將用來評估所產生之演算法的精確度。

    ![Machine Learning Studio (傳統) ：實驗](images/AzureLabs-Lab7-17.png)

5.  在右面板中， (選取畫布上的分割資料項目時) ，將 **第一個輸出資料集中的資料列分數** 編輯為 **0.7**。 這會將資料分割成兩個部分，第一個部分會是70% 的資料，而第二個部分則是剩餘的30%。 若要確保資料會隨機分割，請確定已核取 [ **隨機分割** ] 核取方塊。

    ![Machine Learning Studio (傳統) ：實驗](images/AzureLabs-Lab7-18.png)

6.  將連接從畫布上的 **ProductsTableCSV** 專案基底拖曳至分割資料項目頂端。 這會連接專案，並將 **ProductsTableCSV** 資料集輸出 (資料) 傳送至分割資料輸入。  

    ![Machine Learning Studio (傳統) ：實驗](images/AzureLabs-Lab7-19.png)

7.  在左側的 **實驗** 面板中，展開 [ **Machine Learning**  >  **訓練**]。 將 [ **定型模型** ] 專案拖曳至實驗畫布。 您的畫布看起來應該像下面這樣。

    ![Machine Learning Studio (傳統) ：實驗](images/AzureLabs-Lab7-20.png)

8.  從 _ *分割資料** 專案的 ***左下方** _ 將連接拖曳至 **定型模型** 專案的 **右上** 方。 定型模型會使用資料集的前70% 分割來訓練演算法。

    ![Machine Learning Studio (傳統) ：實驗](images/AzureLabs-Lab7-21.png)

9.  選取畫布上的 [ **定型模型** ] 專案，然後在瀏覽器視窗右側的 [ **屬性** ] 面板中 () 按一下 [啟動資料 **行選取器** ] 按鈕。

10. 在文字方塊中輸入 **product** ，然後按下 **enter**， *product* 將設定為數據行來定型預測。 在此之後，請按一下右下角的 **刻度** ，以關閉選取對話方塊。

    ![Machine Learning Studio (傳統) ：實驗](images/AzureLabs-Lab7-22.png)

11. 您將定型 **多元羅吉斯回歸** 演算法，以根據當天的小時和日期來預測最暢銷的 **產品** 。 這份檔涵蓋了 Azure Machine Learning studio 所提供之不同演算法的詳細資料，但您可以從[Machine Learning 演算法](/azure/machine-learning/studio/algorithm-cheat-sheet)的功能提要中找到更多詳細資料

12. 從左側的實驗專案面板中，展開 [ **Machine Learning**  >  **初始化模型**  >  **分類**]，然後將 [**多元羅吉斯回歸**] 專案拖曳至實驗畫布。

13. 將 **多元羅吉斯回歸** 底部的輸出連接到 **定型模型** 專案的左上角輸入。

    ![Machine Learning Studio (傳統) ：實驗](images/AzureLabs-Lab7-23.png)

14. 在左側面板中的實驗專案清單中，展開 [ **Machine Learning**  >  **分數**]，然後將 [**評分模型**] 專案拖曳至畫布上。

15. 將 **定型模型** 底部的輸出連接到 **評分模型** 的左上角輸入。

16. 將 **分割資料** 的右下角輸出連接到 **評分模型** 專案的右上角輸入。

    ![Machine Learning Studio (傳統) ：實驗](images/AzureLabs-Lab7-24.png)

17. 在左側面板中的 **實驗** 專案清單中，展開 [ **Machine Learning**  >  **評估**]，然後將 [**評估模型**] 專案拖曳至畫布上。

18. 將 **評分模型** 的輸出連接到 **評估模型** 的左上角輸入。

    ![Machine Learning Studio (傳統) ：實驗](images/AzureLabs-Lab7-25.png)

19. 您已建立第一個 Machine Learning 實驗。 您現在可以儲存並執行實驗。 在頁面底部的功能表中，按一下 [ **儲存** ] 按鈕以儲存您的實驗，然後按一下 [ **執行** ] 以開始實驗。

    ![Machine Learning Studio (傳統) ：實驗](images/AzureLabs-Lab7-26.png)

20. 您可以在畫布右上方看到實驗的 **狀態** 。 等候幾分鐘，讓實驗完成。

    > 如果您有很大的 (實際) 資料集，可能是實驗可能需要數小時的時間才能執行。

    ![Machine Learning Studio (傳統) ：實驗](images/AzureLabs-Lab7-27.png)

21. 以滑鼠右鍵按一下畫布中的 [ **評估模型** ] 專案，然後從內容功能表中將滑鼠停留在 **評估結果** 上方，然後選取 [ **視覺化**]。

    ![Machine Learning Studio (傳統) ：實驗](images/AzureLabs-Lab7-28.png)

22. 將會顯示評估結果，顯示預測的結果與實際結果。 這會使用先前分割的原始資料集30% 來評估模型。 您可以看到結果並不理想，最好是每個資料列中的最大數位都是資料行中反白顯示的專案。

    ![Machine Learning Studio (傳統) ：實驗](images/AzureLabs-Lab7-29.png)

23. 關閉 **結果**。

24. 若要使用新定型的 Machine Learning 模型，您需要將它公開為 **Web 服務**。 若要這樣做，請在頁面底部的功能表中按一下 [ **設定 Web 服務** ] 功能表項目，然後按一下 [預測性 **Web 服務**]。

    ![Machine Learning Studio (傳統) ：實驗](images/AzureLabs-Lab7-30.png)

25. 將會建立新的索引標籤，併合並定型模型來建立新的 web 服務。 

26. 在頁面底部的功能表中，按一下 [ **儲存**]，然後按一下 [ **執行**]。 您會看到實驗畫布右上角的狀態更新。

    ![Machine Learning Studio (傳統) ：實驗](images/AzureLabs-Lab7-31.png)

27. 完成執行之後，頁面底部會出現 [ **部署 Web 服務** ] 按鈕。 您可以開始部署 web 服務。 按一下頁面底部功能表中的 [ **部署 Web 服務** (傳統) 。

    ![Machine Learning Studio (傳統) ：實驗](images/AzureLabs-Lab7-32.png)

    > 您的瀏覽器可能會提示您允許快顯視窗，您應該 **允許** 該快顯視窗，但如果 [部署] 頁面未顯示，您可能需要再次按 [ **部署 Web 服務** ]。 

28. 一旦建立實驗之後，您會被重新導向至您將在其中顯示 **API 金鑰** 的 **儀表板** 頁面。 現在將它複製到「記事本」中，您很快就會在程式碼中需要它。 記下您的 API 金鑰之後，請在金鑰底下的 [**預設端點**] 區段中，按一下 [**要求/回應**] 按鈕。

    ![Machine Learning Studio (傳統) ：實驗](images/AzureLabs-Lab7-33.png)

    > [!NOTE] 
    > 如果您按一下此頁面中的 [測試]，就可以輸入輸入資料並查看輸出。 輸入 **日** 和 **小時**。 將 **產品** 專案保留空白。 然後按一下 [ **確認** ] 按鈕。 頁面底部的輸出會顯示 JSON，代表每項產品選擇的可能性。

29. 新的網頁隨即開啟，其中會顯示 Machine Learning Studio (傳統) 所需之要求結構的指示和一些範例。 將此頁面中顯示的 **要求 URI** 複製到您的 [記事本] 中。

    ![Machine Learning Studio (傳統) ：實驗](images/AzureLabs-Lab7-34.png)

您現在已建立機器學習系統，以根據歷程記錄購買資料提供最可能的產品，並與一年中的時間和日的時間產生關聯。

若要呼叫 web 服務，您將需要服務端點的 URL 和服務的 API 金鑰。 從頂端功能表 **中，按一下 [取用] 索引** 標籤。

[ **取用** 資訊] 頁面會顯示從您的程式碼呼叫 web 服務所需的資訊。 取得 **主要金鑰** 和 **要求-回應** URL 的複本。 您將在下一章中需要這些功能。

## <a name="chapter-5---setting-up-the-unity-project"></a>第5章-設定 Unity 專案

設定及測試您的混合現實沉浸式耳機。

> [!NOTE]
>  在此課程中，您將 **不** 需要移動控制器。 如果您需要設定沉浸式耳機的支援，請按一下 [這裡](https://support.microsoft.com/help/4043101/windows-10-set-up-windows-mixed-reality)。

1.  開啟 **unity** ，然後建立名為 **MR \_ MachineLearning** 的新 unity 專案。 請確定專案類型設定為 **3d**。

2.  在 Unity 開啟的情況下，值得檢查預設 **腳本編輯器** 是否設定為 **Visual Studio**。 移至 [**編輯**  >  **喜好** 設定]，然後在新視窗中，流覽至 [**外部工具**]。 將 **外部腳本編輯器** 變更為 **Visual Studio 2017**。 關閉 [ **喜好** 設定] 視窗。

3.  接下來，移 **至 [** 檔案  >  **組建設定**]，然後按一下 [**_切換平臺_**] 按鈕，將平臺切換至 **通用 Windows 平臺**。

4.  也請確定：

    1.  **目標裝置** 設定為 **任何裝置**。

        > 針對 Microsoft HoloLens，請將 **目標裝置** 設定為 *HoloLens*。

    2.  **組建類型** 設定為 **D3D**。

    3.  **SDK** 設定為 [ **最新安裝**]。

    4.  **Visual Studio 版本** 設定為 [ **最新安裝**]。

    5.  **組建並執行** 設定為 [ **本機電腦**]。

    6.  請不要擔心立即設定 **幕後** ，因為稍後會提供。

    7.  其餘設定應該保留為預設值。

        ![設定 Unity 專案](images/AzureLabs-Lab7-35.png)

5.  在 [ **組建設定** ] 視窗中，按一下 [ **播放程式設定** ] 按鈕，這會開啟偵測 **器** 所在空間中的相關面板。 

6. 在此面板中，需要驗證幾個設定：

    1.  在 [ **其他設定** ] 索引標籤中：

        1.  **腳本****執行階段版本** 應該是 **實驗** ( .net 4.6 對等) 

        2. **腳本後端** 應該是 **_.net_**

        3. **API 相容性層級** 應為 **.net 4.6**

            ![設定 Unity 專案](images/AzureLabs-Lab7-36.png)

    2.  在 [ **發行設定** ] 索引標籤的 [ **功能**] 下，選取：

        - **InternetClient**

            ![設定 Unity 專案](images/AzureLabs-Lab7-37.png)

    3.  在面板的 [ **XR 設定**] 中，在 [設定] (找到的 [**發佈設定**]) 、[支援的滴答 **虛擬事實**]，確定已新增 **Windows Mixed Reality SDK**

        ![設定 Unity 專案](images/AzureLabs-Lab7-38.png)

    

6.  回到 **組建設定**： *Unity c #* 專案不再呈現灰色;勾選此方塊旁邊的核取方塊。 

7.  關閉 [建置設定] 視窗。

8.  將專案儲存 (檔 **> 儲存專案**) 。

## <a name="chapter-6---importing-the-mlproducts-unity-package"></a>第6章-匯入 MLProducts Unity 套件

在此課程中，您將需要下載名為 [**Azure-MR-307. unitypackage**](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20307%20-%20Machine%20learning/307-Scene-Setup.unitypackage)的 Unity 資產套件。 這個套件會在場景中完成，其中包含該預建中的所有物件，因此您可以專注于讓它全部運作。 由於場景設定結構的目的，只會保留公用變數，因此會提供 **ShelfKeeper** 腳本。 您將需要進行其他所有章節。 

若要匯入此套件：

1.  使用 Unity 儀表板，然後在畫面頂端的功能表中按一下 [ **資產** ]，再按一下 [匯 **入封裝]、[自訂套件**]。

    ![匯入 MLProducts Unity 套件](images/AzureLabs-Lab7-39.png)

2.  使用檔案選擇器選取 **Azure unitypackage** 套件，然後按一下 [ **開啟**]。

3.  系統會向您顯示此資產的元件清單。 按一下 [匯 **入**] 以確認匯入。

    ![匯入 MLProducts Unity 套件](images/AzureLabs-Lab7-40.png)

4.  匯入完成後，您會注意到您的 Unity **專案面板** 中出現一些新的資料夾。 這些是3D 模型，以及屬於您將使用之預先製作場景一部分的個別材質。 您將在本課程中撰寫大部分的程式碼。

    ![匯入 MLProducts Unity 套件](images/AzureLabs-Lab7-41.png)

5.  在 [ **專案面板** ] 資料夾中，按一下 [ **場景** ] 資料夾，然後按兩下 (中稱為 **MR_MachineLearningScene**) 的場景。 場景會開啟 (請參閱下圖) 。 如果紅色菱形遺失，只要按一下 [**遊戲] 面板** 右上方的 [ **Gizmos** ] 按鈕即可。

    ![匯入 MLProducts Unity 套件](images/AzureLabs-Lab7-44.png)

## <a name="chapter-7---checking-the-dlls-in-unity"></a>第7章-在 Unity 中檢查 Dll

若要利用 JSON 程式庫 (用於序列化和還原序列化) ，Newtonsoft DLL 已使用您帶入的封裝來執行。 程式庫應該具有正確的設定，但值得檢查 (特別是當您遇到無法) 的程式碼問題時。 

操作方法：

-  以滑鼠左鍵按一下 [外掛程式] 資料夾內的 Newtonsoft 檔案，然後查看 [偵測 **器] 面板**。 請確定 **任何平臺** 都核取。 移至 [ **UWP]** 索引標籤，並確定 [ **不處理** ] 為 [核取]。

    ![匯入 Unity 中的 Dll](images/AzureLabs-Lab7-48.png)

## <a name="chapter-8---create-the-shelfkeeper-class"></a>第8章-建立 ShelfKeeper 類別

**ShelfKeeper** 類別裝載的方法會控制在場景中衍生的 UI 和產品。

在匯入的套件中，您將被授與這個類別，但它並不完整。 現在完成該類別的時機：

1.  按兩下 [**腳本**] 資料夾中的 **ShelfKeeper** 腳本，以 **Visual Studio 2017** 來開啟它。

2.  將腳本中的所有程式碼取代為下列程式碼，此程式碼會設定時間和日期，並且具有可顯示產品的方法。

    ```csharp
    using UnityEngine;

    public class ShelfKeeper : MonoBehaviour
    {
        /// <summary>
        /// Provides this class Singleton-like behavior
        /// </summary>
        public static ShelfKeeper instance;

        /// <summary>
        /// Unity Inspector accessible Reference to the Text Mesh object needed for data
        /// </summary>
        public TextMesh dateText;

        /// <summary>
        /// Unity Inspector accessible Reference to the Text Mesh object needed for time
        /// </summary>
        public TextMesh timeText;

        /// <summary>
        /// Provides references to the spawn locations for the products prefabs
        /// </summary>
        public Transform[] spawnPoint;

        private void Awake()
        {
            instance = this;
        }

        /// <summary>
        /// Set the text of the date in the scene
        /// </summary>
        public void SetDate(string day, string month)
        {
            dateText.text = day + " " + month;
        }

        /// <summary>
        /// Set the text of the time in the scene
        /// </summary>
        public void SetTime(string hour)
        {
            timeText.text = hour + ":00";
        }

        /// <summary>
        /// Spawn a product on the shelf by providing the name and selling grade
        /// </summary>
        /// <param name="name"></param>
        /// <param name="sellingGrade">0 being the best seller</param>
        public void SpawnProduct(string name, int sellingGrade)
        {
            Instantiate(Resources.Load(name),
                spawnPoint[sellingGrade].transform.position, spawnPoint[sellingGrade].transform.rotation);
        }
    }
    ```

3.  返回 **Unity** 之前，請務必將您的變更儲存在 **Visual Studio** 中。

4.  回到 Unity 編輯器，確認 **ShelfKeeper** 類別看起來如下所示：

    ![建立 ShelfKeeper 類別](images/AzureLabs-Lab7-51.png)

    > [!IMPORTANT]
    > 如果您的腳本沒有參考目標 (亦即 *日期 (文字網格)*) ，只要將對應的物件從 [階層] **面板** 拖曳到目標欄位即可。 如有需要，請參閱下面的說明：
    > 
    > 1.  在 **ShelfKeeper** 元件腳本內，以滑鼠左鍵按一下產生 **點** 陣列來開啟它。 子區段會顯示為 [ **大小**]，指出陣列的大小。 在 [**大小**] 旁的文字方塊中輸入 **3** ，然後按 **enter** 鍵，即可在下方建立三個位置。
    > 2. **在階層** 中，以滑鼠左鍵按一下) 旁邊的箭號，以展開 **時間顯示** 物件 (。 接著按一下 _ 階層中的 **_主要攝影機_*_***，讓偵測 **器** 顯示其資訊。
    > 3. 在 [階層]**面板** 中選取 **主要攝影機**。 將 [**日期**] 和 [**時間**] 物件從 [階層]**面板** 拖曳到 **ShelfKeeper** 元件中的 **主攝影機** 偵測 **器** 內的 **日期文字** 和 **時間文字** 位置。
    > 4. 將 [階層]**面板** 中的 [產生 **點**] (從 [*貨架*] 物件底下，) 到產生 **點** 陣列底下的 **3** 個 **專案參考目標**，如影像所示。
    > 
    >     ![建立 ShelfKeeper 類別](images/AzureLabs-Lab7-52.png)

## <a name="chapter-9---create-the-productprediction-class"></a>第9章-建立 ProductPrediction 類別

您即將建立的下一個類別是 **ProductPrediction** 類別。

此類別負責：

-   查詢 **Machine Learning 服務** 實例，並提供目前的日期和時間。

-   將 JSON 回應還原序列化成可用的資料。

-   解讀資料，並抓取3個建議的產品。

-   呼叫 **ShelfKeeper** 類別方法來顯示場景中的資料。

若要建立此類別：

1.  移至 [**專案] 面板** 中的 [**腳本**] 資料夾。

2.  以滑鼠右鍵按一下資料夾內的 [**建立**  >  **c # 腳本**]。 呼叫腳本 **ProductPrediction**。

3.  按兩下新的 **ProductPrediction** 腳本，以 **Visual Studio 2017** 開啟。

4.  如果出現 [偵測 **到檔案修改** ] 對話方塊，請按一下 [*_重載方案_*]。

5.  將下列命名空間新增至 ProductPrediction 類別的頂端：

    ```csharp
    using System;
    using System.Collections.Generic;
    using UnityEngine;
    using System.Linq;
    using Newtonsoft.Json;
    using UnityEngine.Networking;
    using System.Runtime.Serialization;
    using System.Collections;
    ```

6.  在 **ProductPrediction** 類別內插入下列兩個物件，這些物件是由一些嵌套類別所組成。 這些類別是用來將 Machine Learning 服務的 JSON 序列化和還原序列化。

    ```csharp
        /// <summary>
        /// This object represents the Prediction request
        /// It host the day of the year and hour of the day
        /// The product must be left blank when serialising
        /// </summary>
        public class RootObject
        {
            public Inputs Inputs { get; set; }
        }

        public class Inputs
        {
            public Input1 input1 { get; set; }
        }

        public class Input1
        {
            public List<string> ColumnNames { get; set; }
            public List<List<string>> Values { get; set; }
        }
    ```

    ```csharp
        /// <summary>
        /// This object containing the deserialised Prediction result
        /// It host the list of the products
        /// and the likelihood of them being sold at current date and time
        /// </summary>
        public class Prediction
        {
            public Results Results { get; set; }
        }

        public class Results
        {
            public Output1 output1;
        }

        public class Output1
        {
            public string type;
            public Value value;
        }

        public class Value
        {
            public List<string> ColumnNames { get; set; }
            public List<List<string>> Values { get; set; }
        }
    ```

7.  然後，將下列變數新增至上述程式碼的上方 (，讓 JSON 相關程式碼位於腳本底部、所有其他程式碼底下，而不是) ：

    ```csharp
        /// <summary>
        /// The 'Primary Key' from your Machine Learning Portal
        /// </summary>
        private string authKey = "-- Insert your service authentication key here --";

        /// <summary>
        /// The 'Request-Response' Service Endpoint from your Machine Learning Portal
        /// </summary>
        private string serviceEndpoint = "-- Insert your service endpoint here --";

        /// <summary>
        /// The Hour as set in Windows
        /// </summary>
        private string thisHour;

        /// <summary>
        /// The Day, as set in Windows
        /// </summary>
        private string thisDay;

        /// <summary>
        /// The Month, as set in Windows
        /// </summary>
        private string thisMonth;

        /// <summary>
        /// The Numeric Day from current Date Conversion
        /// </summary>
        private string dayOfTheYear;

        /// <summary>
        /// Dictionary for holding the first (or default) provided prediction 
        /// from the Machine Learning Experiment
        /// </summary>    
        private Dictionary<string, string> predictionDictionary;

        /// <summary>
        /// List for holding product prediction with name and scores
        /// </summary>
        private List<KeyValuePair<string, double>> keyValueList;
    ```

    > [!IMPORTANT]
    > 請務必將 Machine Learning 入口網站中的 **主要金鑰** 和 **要求-回應端點** 插入這裡的變數中。 下列影像顯示您從哪裡取得金鑰和端點的位置。 
    >  
    > ![Machine Learning Studio (傳統) ：實驗](images/AzureLabs-Lab7-53-1.png)
    >
    > ![Machine Learning Studio (傳統) ：實驗](images/AzureLabs-Lab7-53-2.png)

8.  在 **Start ()** 方法中插入此程式碼。 當類別初始化時，會呼叫 **Start ()** 方法：

    ```csharp
        void Start()
        {
            // Call to get the current date and time as set in Windows
            GetTodayDateAndTime();

            // Call to set the HOUR in the UI
            ShelfKeeper.instance.SetTime(thisHour);

            // Call to set the DATE in the UI
            ShelfKeeper.instance.SetDate(thisDay, thisMonth);

            // Run the method to Get Predication from Azure Machine Learning
            StartCoroutine(GetPrediction(thisHour, dayOfTheYear));
        }
    ```

9.  以下是從 Windows 收集日期和時間的方法，並將它轉換成我們的 Machine Learning 實驗可以用來與資料表中儲存的資料進行比較的格式。

    ```csharp
        /// <summary>
        /// Get current date and hour
        /// </summary>
        private void GetTodayDateAndTime()
        {
            // Get today date and time
            DateTime todayDate = DateTime.Now;

            // Extrapolate the HOUR
            thisHour = todayDate.Hour.ToString();

            // Extrapolate the DATE
            thisDay = todayDate.Day.ToString();
            thisMonth = todayDate.ToString("MMM");

            // Extrapolate the day of the year
            dayOfTheYear = todayDate.DayOfYear.ToString();
        }
    ```

10. 您可以 **刪除****更新 ()** 方法，因為此類別不會使用它。

11. 新增下列方法，以將目前的日期和時間傳達給 Machine Learning 端點，並接收 JSON 格式的回應。

    ```csharp
        private IEnumerator GetPrediction(string timeOfDay, string dayOfYear)
        {
            // Populate the request object 
            // Using current day of the year and hour of the day
            RootObject ro = new RootObject
            {
                Inputs = new Inputs
                {
                    input1 = new Input1
                    {
                        ColumnNames = new List<string>
                        {
                            "day",
                            "hour",
                        "product"
                        },
                        Values = new List<List<string>>()
                    }
                }
            };

            List<string> l = new List<string>
            {
                dayOfYear,
                timeOfDay,
                ""
            };

            ro.Inputs.input1.Values.Add(l);

            Debug.LogFormat("Score request built");

            // Serialize the request
            string json = JsonConvert.SerializeObject(ro);

            using (UnityWebRequest www = UnityWebRequest.Post(serviceEndpoint, "POST"))
            {
                byte[] jsonToSend = new System.Text.UTF8Encoding().GetBytes(json);
                www.uploadHandler = new UploadHandlerRaw(jsonToSend);

                www.downloadHandler = new DownloadHandlerBuffer();
                www.SetRequestHeader("Authorization", "Bearer " + authKey);
                www.SetRequestHeader("Content-Type", "application/json");
                www.SetRequestHeader("Accept", "application/json");

                yield return www.SendWebRequest();
                string response = www.downloadHandler.text;

                // Deserialize the response
                DataContractSerializer serializer;
                serializer = new DataContractSerializer(typeof(string));
                DeserialiseJsonResponse(response);
            }
        }
    ```

12. 新增下列方法，其負責將 JSON 回應還原序列化，並將還原序列化的結果傳達給 **ShelfKeeper** 類別。 此結果將會是預測為最新日期和時間銷售的三個專案的名稱。 將下列程式碼插入至 **ProductPrediction** 類別，在先前的方法下方。

    ```csharp
        /// <summary>
        /// Deserialize the response received from the Machine Learning portal
        /// </summary>
        public void DeserialiseJsonResponse(string jsonResponse)
        {
            // Deserialize JSON
            Prediction prediction = JsonConvert.DeserializeObject<Prediction>(jsonResponse);
            predictionDictionary = new Dictionary<string, string>();

            for (int i = 0; i < prediction.Results.output1.value.ColumnNames.Count; i++)
            {
                if (prediction.Results.output1.value.Values[0][i] != null)
                {
                    predictionDictionary.Add(prediction.Results.output1.value.ColumnNames[i], prediction.Results.output1.value.Values[0][i]);
                }
            }

            keyValueList = new List<KeyValuePair<string, double>>();

            // Strip all non-results, by adding only items of interest to the scoreList
            for (int i = 0; i < predictionDictionary.Count; i++)
            {
                KeyValuePair<string, string> pair = predictionDictionary.ElementAt(i);
                if (pair.Key.StartsWith("Scored Probabilities"))
                {
                    // Parse string as double then simplify the string key so to only have the item name
                    double scorefloat = 0f;
                    double.TryParse(pair.Value, out scorefloat);
                    string simplifiedName =
                        pair.Key.Replace("\"", "").Replace("Scored Probabilities for Class", "").Trim();
                    keyValueList.Add(new KeyValuePair<string, double>(simplifiedName, scorefloat));
                }
            }

            // Sort Predictions (results will be lowest to highest)
            keyValueList.Sort((x, y) => y.Value.CompareTo(x.Value));

            // Spawn the top three items, from the keyValueList, which we have sorted
            for (int i = 0; i < 3; i++)
            {
                ShelfKeeper.instance.SpawnProduct(keyValueList[i].Key, i);
            }

            // Clear lists in case of reuse
            keyValueList.Clear();
            predictionDictionary.Clear();
        }
    ```

13. 儲存 **Visual Studio** 並回到 **Unity**。

14. 將 [ **ProductPrediction** ] 類別腳本從 [ **腳本** ] 資料夾拖曳至 [ **主要攝影機** ] 物件。

15. 儲存場景和專案 **檔**  >  **儲存場景/** 檔案  >  **儲存專案**。

## <a name="chapter-10---build-the-uwp-solution"></a>第10章-建立 UWP 解決方案

現在將您的專案建立為 UWP 解決方案，讓它可以獨立應用程式的形式執行。

若要建立：

1.  按一下 [檔案  >  **儲存場景**] 以儲存目前的場景。

2.  移至 **檔案**  >  **組建設定**

3.  核取稱為 **Unity c # 專案** 的方塊 (這很重要，因為它可讓您在組建完成) 之後編輯類別。

4.  按一下 [ **新增開啟的場景**]，

5.  按一下 [建置]。

    ![打造 UWP 解決方案](images/AzureLabs-Lab7-54.png)

6.  系統會提示您選取要在其中建立解決方案的資料夾。

7.  建立 **組建** 資料夾，然後在該資料夾內使用您選擇的適當名稱建立另一個資料夾。

8.  按一下新資料夾，然後按一下 [ **選取資料夾**]，在該位置開始組建。

    ![打造 UWP 解決方案](images/AzureLabs-Lab7-55.png)

    ![打造 UWP 解決方案](images/AzureLabs-Lab7-56.png)

9.  Unity 完成組建之後 (可能需要一些時間) ，它會在您的組建位置開啟 **檔案總管** 視窗 (檢查您的工作列，因為它不一定會出現在您的視窗上方，但會通知您加入新的視窗) 。

## <a name="chapter-11---deploy-your-application"></a>第11章-部署應用程式

若要部署您的應用程式：

1.  流覽至您的新 Unity 組建 (**應用程式** 資料夾) ，然後以 **Visual Studio** 開啟方案檔。

2.  當 Visual Studio 開啟時，您需要還原 NuGet 套件，只要以滑鼠右鍵按一下您的 MachineLearningLab_Build 解決方案，從 Visual Studio) 右邊的方案總管 (，然後按一下 [還原 NuGet 套件] 即可完成：

    ![新增 NuGet 套件](images/AzureLabs-Lab7-57.png)

3.  在 [方案設定] 中選取 [ **Debug**]。

4.  在 [方案平臺] 中，選取 [ **x86**]、[ **本機電腦**]。 

    > 在 Microsoft HoloLens 中，您可能會發現將此設定為 *遠端電腦* 較容易，因此不會行動網卡到您的電腦。 不過，您也必須執行下列動作：
    > - 知道您 HoloLens 的 **IP 位址** ，您可以在 *設定 > 網路 & 網際網路 > Wi-Fi > Advanced 選項* 中找到此位址;IPv4 是您應該使用的位址。 
    > - 確定已 **開啟****開發人員模式**;在 [設定] 中找到 *> 為開發人員更新 & 安全性 >*。

    ![新增 NuGet 套件](images/AzureLabs-Lab7-58.png)

5.  移至 [ **組建] 功能表** ，然後按一下 [ **部署方案** ]，將應用程式側載至您的電腦。

6.  您的應用程式現在應該會出現在已安裝的應用程式清單中，準備好要啟動。

當您執行混合現實應用程式時，您將會看到在 Unity 場景中設定的基準，而且從初始化，將會提取您在 Azure 中設定的資料。 資料將會在您的應用程式中還原序列化，而您目前日期和時間的三個主要結果將以視覺化方式提供，做為三種模型。


## <a name="your-finished-machine-learning-application"></a>您完成的 Machine Learning 應用程式
 
恭喜您，您建立了一個混合現實應用程式，利用 Azure Machine Learning 進行資料預測並顯示在您的場景中。

![新增 NuGet 套件](images/AzureLabs-Lab7-0.png)

## <a name="exercise"></a>練習

**練習1**

以您應用程式的排序次序進行實驗，並在貨架上顯示三個最下方的預測，因為這項資料可能也很有用。

**練習2**

使用 **Azure 資料表** 會以氣象資訊填入新的資料表，並使用資料來建立新的實驗。