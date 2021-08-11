---
title: HoloLens (第1代) 和 Azure 310-物件偵測
description: 完成本課程，以瞭解如何訓練和使用機器學習模型，以辨識類似的物件和其在真實世界中的位置。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure，自訂視覺，物件偵測，混合現實，學院，unity，教學課程，api，hololens，Windows 10，Visual Studio
ms.openlocfilehash: 85a99b676f6765696524bc42adf257b3430c00cc955413b4c299ddb58502cefb
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2021
ms.locfileid: "115216572"
---
# <a name="hololens-1st-gen-and-azure-310-object-detection"></a>HoloLens (第1代) 和 Azure 310：物件偵測

>[!NOTE]
>混合實境學院教學課程的設計是以 HoloLens (第 1 代) 和混合實境沉浸式頭戴裝置為準。  因此，對於仍在尋找這些裝置開發指引的開發人員而言，我們覺得這些教學課程很重要。  這些教學課程 **_不會_** 使用用於 HoloLens 2 的最新工具組或互動進行更新。  系統會保留這些資訊，以繼續在支援的裝置上運作。 未來將會有一系列新的教學課程，將會示範如何針對 HoloLens 2 進行開發。  當張貼這些教學課程時，將會使用這些教學課程的連結來更新此通知。

<br>

在此課程中，您將瞭解如何在混合現實應用程式中使用 Azure 自訂視覺「物件偵測」功能，來辨識所提供映射內的自訂視覺效果內容和其空間位置。

這種服務可讓您使用物件影像來定型機器學習模型。 然後，您將使用定型的模型來辨識類似的物件，並將其在真實世界中的位置（如 Microsoft HoloLens 的相機捕捉所提供）或攝影機連接到適用于沉浸式 (VR) 耳機的電腦。

![課程結果](images/AzureLabs-Lab310-00.png)

**Azure 自訂視覺，物件偵測** 是一項 Microsoft 服務，可讓開發人員建立自訂影像分類器。 然後，您可以在影像本身內提供方塊 **界限** ，將這些分類器用於新的影像，以偵測該新影像內的物件。 此服務提供簡單、容易使用的線上入口網站，以簡化此程式。 如需詳細資訊，請造訪下列連結：

* [Azure 自訂視覺頁面](/azure/cognitive-services/custom-vision-service/home)
* [限制和配額](/azure/cognitive-services/custom-vision-service/limits-and-quotas)

完成本課程之後，您將會有一個混合現實應用程式，可以執行下列動作：

1. 使用者可以使用 Azure 自訂視覺服務的物件偵測，來 *注視* 已定型的物件。 
2. 使用者會使用點一下 *手勢來* 捕捉其所查看內容的影像。
3. 應用程式會將映射傳送至 Azure 自訂視覺服務。
4. 服務會有回復，會將辨識結果顯示為世界空間文字。 這會透過使用 Microsoft HoloLens 的空間追蹤來完成，以瞭解辨識物件的世界位置，然後使用與影像中偵測到的相關聯的 *標記* 來提供標籤文字。

本課程也會說明如何手動上傳影像、建立標籤，以及訓練服務，以在所提供的範例中辨識不同的物件 (在所提供的範例中，這是杯) ，方法是在您提交的影像內設定 *界限* 方塊。 

> [!IMPORTANT]
> 在建立和使用應用程式之後，開發人員應該流覽回 Azure 自訂視覺服務，並找出服務所做的預測，並判斷其是否正確或不 (透過標記服務遺漏的任何內容，以及調整周 *框方塊*) 。 然後，您可以重新定型服務，這會增加 it 識別真實世界物件的可能性。

本課程將指導您如何將 Azure 自訂視覺服務、物件偵測的結果，取得至 Unity 型範例應用程式。 您必須將這些概念套用至您可能正在建立的自訂應用程式。

## <a name="device-support"></a>裝置支援

<table>
<tr>
<th>課程</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">沉浸式頭戴裝置</a></th>
</tr><tr>
<td> MR 和 Azure 310：物件偵測</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="prerequisites"></a>必要條件

> [!NOTE]
> 本教學課程是專為擁有 Unity 和 c # 基本經驗的開發人員所設計。 另外也請注意，本檔中的必要條件和書面指示，代表在撰寫 (2018 年7月) 時已經過測試和驗證的內容。 You are free to use the latest software, as listed within the [install the tools](../../install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you will find in newer software than what is listed below.

本課程建議您採用下列硬體和軟體：

- 開發電腦
- [啟用開發人員模式的 Windows 10 Fall Creators Update (或更新版本) ](/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- [最新的 Windows 10 SDK](/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- [Unity 2017.4 LTS](/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- [Visual Studio 2017](/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- 啟用開發人員模式的[Microsoft HoloLens](/windows/mixed-reality/hololens-hardware-details)
- 適用于 Azure 安裝和自訂視覺服務抓取的網際網路存取
-  針對您想要自訂視覺辨識的每個物件，至少) 需要一系列 15 (15) 映射。 如果您想要的話，可以使用本課程所提供的映射，也就 [是一系列的 cup](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Cup%20Images.zip)) 。

## <a name="before-you-start"></a>在您開始使用 Intune 之前

1.  為了避免在建立此專案時發生問題，強烈建議您在根或近端根資料夾中，建立本教學課程中所述的專案 (長的資料夾路徑可能會在組建階段) 時發生問題。
2.  設定及測試您的 HoloLens。 如果您需要設定 HoloLens 的支援，[請務必造訪 HoloLens 安裝程式文章](/hololens/hololens-setup)。 
3.  在開始開發新的 HoloLens 應用程式時，最好先執行校正和感應器調整， (有時它可以協助您為每個使用者) 執行這些工作。 

如需有關校正的說明，請遵循此[連結來 HoloLens 校正文章](/hololens/hololens-calibration#hololens-2)。

如需有關感應器微調的說明，請依照此[連結前往 HoloLens 感應器微調文章](/hololens/hololens-updates)。

## <a name="chapter-1---the-custom-vision-portal"></a>第1章-自訂視覺入口網站

若要使用 **Azure 自訂視覺服務**，您必須將它的實例設定為可供您的應用程式使用。

1.  流覽 [至 **自訂視覺服務** 主頁面](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/)。

2.  按一下 [ **開始使用**]。

    ![](images/AzureLabs-Lab310-01.png)

3.  登入自訂視覺入口網站。

    ![](images/AzureLabs-Lab310-02.png)

4.  如果您還沒有 Azure 帳戶，您將需要建立一個帳戶。 如果您在課堂或實驗室的情況下進行本教學課程，請洽詢講師或其中一個 proctors，協助您設定新的帳戶。

5.  當您第一次登入之後，系統會提示您提供 *服務條款* 面板。 按一下核取方塊以 *同意條款*。 然後按一下 [ **我同意**]。

    ![](images/AzureLabs-Lab310-03.png)

6.  同意條款之後，您現在就可以在 [ *我的專案* ] 區段中。 按一下 [**新增 Project**]。

    ![](images/AzureLabs-Lab310-04.png)

7.  右側將會出現一個索引標籤，提示您指定專案的某些欄位。

    1.  為您的專案插入名稱

    2.  為您的專案插入描述 (**選擇性**) 

    3.  選擇資源群組，或建立一個新的 **資源群組** 。 資源群組提供一種方式來監視、控制存取、布建及管理 Azure 資產集合的計費。 建議您保留與單一專案相關聯的所有 Azure 服務 (例如，) 一般資源群組下的這些課程) 。

        ![](images/AzureLabs-Lab310-05.png)

        > [!NOTE]
        > 如果您想要[閱讀更多有關 Azure 資源群組的資訊，請流覽至相關聯的](/azure/azure-resource-manager/resource-group-portal)檔

    4.  將 **Project 類型** 設定為 **物件偵測 (預覽)**。

8.  完成之後，按一下 [ **建立專案**]，系統就會將您重新導向至自訂視覺服務專案] 頁面。


## <a name="chapter-2---training-your-custom-vision-project"></a>第2章-訓練自訂視覺專案

在自訂視覺入口網站中，您的主要目標是將您的專案定型，以辨識影像中的特定物件。

針對您想要讓應用程式辨識的每個物件，至少需要 15 (15) 的影像。 您可以使用本課程所提供的影像 ([一連串的 cup](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Cup%20Images.zip)) 。

定型您的自訂視覺專案：

1.  按一下 [ **+** **標記**] 旁的按鈕。

    ![](images/AzureLabs-Lab310-06.png)

2.  針對將用來與您的影像建立關聯的標記新增 **名稱** 。 在此範例中，我們會使用 cup 的影像進行辨識，因此請為這個 **杯杯** 命名標記。 按一下 [ **儲存** 完成]。

    ![](images/AzureLabs-Lab310-07.png)

3.  您會注意到 **您的標籤已新增** (您可能需要重載頁面，才能讓它顯示) 。 

    ![](images/AzureLabs-Lab310-08.png)

4.  按一下頁面中央的 [ **加入影像** ]。

    ![](images/AzureLabs-Lab310-09.png)

5.  按一下 **[流覽本機檔案]**，然後流覽至您想要上傳一個物件的影像，其最少為 15 (15) 。

    > [!TIP]
    >  您可以一次選取多個影像，以便上傳。

    ![](images/AzureLabs-Lab310-10.png)

6.  一旦選取您要用來定型專案的所有影像，請按 **Upload** 檔案。 檔案將會開始上傳。 確認上傳之後，請按一下 [ **完成**]。

    ![](images/AzureLabs-Lab310-11.png)

7.  此時您的影像已上傳，但未標記。

    ![](images/AzureLabs-Lab310-12.png)

8.  若要標記您的映射，請使用滑鼠。 當您將滑鼠停留在影像上時，選取專案醒目提示將會透過自動在物件周圍繪製選取專案來協助您。 如果不正確，您可以自行繪製。 若要完成此動作，請按住滑鼠左鍵，然後拖曳選取區域以包含您的物件。 

    ![](images/AzureLabs-Lab310-13.png) 

9. 在影像中選取您的物件之後，小提示會要求您 *新增區域標記*。 選取先前建立的標籤 ( ' 杯 '，在上述範例中) ，或如果您要新增更多標籤，請在中輸入，然後按一下 **+ (再加)** 按鈕。

    ![](images/AzureLabs-Lab310-14.png) 

10. 若要標記下一個影像，您可以按一下分頁右邊的箭號，或按一下分頁的右上) 角的 **X** ，關閉標記分頁 (，然後按一下下一個影像。 當您準備好下一個映射之後，請重複相同的程式。 針對您已上傳的所有影像進行此操作，直到全部標記為止。 

    > [!NOTE]
    >  您可以在同一個影像中選取數個物件，如下圖所示： 
    > 
    > ![](images/AzureLabs-Lab310-15.png)

11. 一旦您標記全部，請按一下畫面左側的 [ **標記** ] 按鈕，以顯示已標記的影像。 

    ![](images/AzureLabs-Lab310-16.png)

12. 您現在已準備好定型您的服務。 按一下 [ **定型** ] 按鈕，就會開始第一個定型反復專案。

    ![](images/AzureLabs-Lab310-17.png)

    ![](images/AzureLabs-Lab310-18.png)

13. 一旦建立之後，您就可以看到兩個按鈕，稱為「 **建立預設值** 和 **預測 URL**」。 先按一下 [ **設為預設值** ]，然後按一下 [ **預測 URL**]。

    ![](images/AzureLabs-Lab310-19.png)

    > [!NOTE] 
    > 由此提供的端點會設定為已標示為預設值的任何 *反復* 專案。 因此，如果您稍後建立新的 *反復* 專案，並將其更新為預設值，您就不需要變更程式碼。

14. 當您按一下 [**預測 URL**] 之後，請開啟 *記事本*，然後複製並貼上 **URL** (也稱為您的 **預測端點**) 和 **服務預測金鑰**，以便稍後在程式碼中需要時加以取出。

    ![](images/AzureLabs-Lab310-20.png)

## <a name="chapter-3---set-up-the-unity-project"></a>第3章-設定 Unity 專案

以下是使用 mixed reality 進行開發的一般設定，因此，它是適用于其他專案的絕佳範本。

1.  開啟 **Unity** ，然後按一下 [ **新增**]。

    ![](images/AzureLabs-Lab310-21.png)

2.  您現在將需要提供 Unity 專案名稱。 插入 **CustomVisionObjDetection**。 請確定專案類型設定為 **3d**，並將 **位置** 設定為適合您 (記住，更接近根目錄的) 。 然後，按一下 [ **建立專案**]。

    ![](images/AzureLabs-Lab310-22.png)

3.  在 Unity 開啟的情況下，值得檢查預設 **腳本編輯器** 是否設定為 **Visual Studio**。 移至 [ **編輯*  >  *喜好** 設定]，然後在新視窗中，流覽至 [**外部工具**]。 將 **外部腳本編輯器** 變更為 **Visual Studio**。 關閉 [ **喜好** 設定] 視窗。

    ![](images/AzureLabs-Lab310-23.png)

4.  接下來，移至 [檔案 **> 組建] 設定** 並將 **平臺** 切換至 [*通用 Windows 平臺*]，然後按一下 [**切換平臺**] 按鈕。

    ![](images/AzureLabs-Lab310-24.png)

5.  在相同的 **組建設定** 視窗中，確定已設定下列各項：

    1.  **目標裝置** 設定為 **HoloLens**        
    2.  **組建類型** 設定為 **D3D**
    3.  **SDK** 已設定為 **最新安裝**
    4.  **Visual Studio 版本** 設定為 **最新安裝**
    5.  **組建並執行** 設定為 **本機電腦**            
    6.  [**組建設定**] 中的其餘設定，現在應該保持為預設值。

        ![](images/AzureLabs-Lab310-25.png)

6.  在相同的 **組建設定** 視窗中，按一下 [**播放** 程式] 設定按鈕，這會開啟偵測 **器** 所在空間中的相關面板。

7. 在此面板中，需要驗證幾個設定：

    1.  在 [**其他設定**] 索引標籤中：

        1.  **腳本執行階段版本** 應該是 **實驗** ( .net 4.6 對等) ，這會觸發重新開機編輯器的需求。

        2. **腳本後端** 應該是 **.net**。

        3. **API 相容性層級** 應為 **.net 4.6**。

            ![](images/AzureLabs-Lab310-26.png)

    2.  在 [**發行設定**] 索引標籤的 [**功能**] 下，選取：

        1. **InternetClient**

        2.  **網路攝影機**

        3. **SpatialPerception**

            ![](images/AzureLabs-Lab310-27.png) ![](images/AzureLabs-Lab310-28.png)

    3.  接下來的面板中，在 **XR 設定** (的 [**發佈設定**) ]、[滴答 **虛擬實境支援**]，並確定已新增 **Windows Mixed Reality SDK** 。

        ![](images/AzureLabs-Lab310-29.png)

8.  回到 **Build 設定**， *Unity C \# 專案* 不再呈現灰色：勾選這個旁邊的核取方塊。

9.  關閉 [組建設定]  視窗。

10. 在 **編輯器** 中，按一下 [**編輯**]  >  **Project 設定**  >  **圖形**]。

    ![](images/AzureLabs-Lab310-30.png)

11. 在 [偵測 **器] 面板** 中，*圖形設定* 將會開啟。 向下鍵，直到您看到名為 [ **永遠包含著色** 器] 的陣列為止。 在此範例中，藉由將 **大小** 變數增加一個 (來新增位置，這是8，因此我們將它設為 9) 。 新的位置會出現在陣列的最後一個位置，如下所示：

    ![](images/AzureLabs-Lab310-31.png)

12. 在位置中，按一下位置旁的小目標圓形以開啟著色器清單。 尋找 **舊版著色器/透明/擴散** 著色器，然後按兩下它。 

    ![](images/AzureLabs-Lab310-32.png)

## <a name="chapter-4---importing-the-customvisionobjdetection-unity-package"></a>第4章-匯入 CustomVisionObjDetection Unity 套件

在此課程中，您會提供名為 **Azure-MR-310. unitypackage** 的 Unity 資產套件。 

> 提醒Unity 支援的任何物件（包括整個場景）都可以封裝至 **unitypackage** 檔案，並在其他專案中匯出/匯入。 這是在不同 **Unity 專案** 之間移動資產最安全且最有效率的方式。

您可以在 [這裡找到您需要下載的 Azure-MR-310 套件](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Azure-MR-310.unitypackage)。

1.  使用 Unity 儀表板，在畫面頂端的功能表中按一下 [ **資產** ]，然後按一下 [匯 **入封裝 > 自訂套件**]。

    ![](images/AzureLabs-Lab310-33.png)

2.  使用檔案選擇器選取 **Azure-MR. unitypackage** 套件，然後按一下 [ **開啟**]。 系統會向您顯示此資產的元件清單。 按一下 [匯 **入** ] 按鈕以確認匯入。

    ![](images/AzureLabs-Lab310-34.png)

3.  匯入完成後，您會注意到套件中的資料夾現在已新增至 [ **資產** ] 資料夾。 這種資料夾結構一般適用于 Unity 專案。

    ![](images/AzureLabs-Lab310-35.png)

    1.  [ **材質** ] 資料夾包含 **注視游標** 所使用的材質。 

    2.  [ **外掛程式** ] 資料夾包含程式碼用來還原序列化服務 web 回應的 Newtonsoft DLL。 包含在資料夾和子資料夾中的兩個 (2) 不同的版本是必要的，可讓 Unity 編輯器和 UWP 組建使用和建立程式庫。 

    3.  **Prefabs** 資料夾包含場景中包含的 Prefabs。 這些是：

        1.  **GazeCursor**，在應用程式中使用的資料指標。 將與 SpatialMapping 預製專案搭配運作，以將場景放在實體物件的上方。
        2.  **標籤**，這是在必要時用來在場景中顯示物件標記的 UI 物件。
        3.  **SpatialMapping**，這是可讓應用程式使用 Microsoft HoloLens 的空間追蹤來建立虛擬對應的物件。

    4.  目前包含此課程之預先建立場景的 **場景** 資料夾。

4.  開啟 [**場景**] 資料夾，然後在 [ **Project] 面板** 中按兩下 **ObjDetectionScene**，載入您將在此課程中使用的場景。

    ![](images/AzureLabs-Lab310-36.png)

    > [!NOTE] 
    >  **未包含任何程式碼**，您將遵循本課程來撰寫程式碼。

## <a name="chapter-5---create-the-customvisionanalyser-class"></a>第5章-建立 CustomVisionAnalyser 類別。

至此，您已準備好撰寫一些程式碼。 您將開始使用 **CustomVisionAnalyser** 類別。

> [!NOTE]
> 在如下所示的程式碼中，對 **自訂視覺服務** 的呼叫會使用 **自訂視覺 REST API** 進行。 透過這種方式，您將瞭解如何實行和使用此 API (有助於瞭解如何在您自己的) 上執行類似的操作。 請注意，Microsoft 提供的 **自訂視覺 SDK** 也可以用來對服務進行呼叫。 如需詳細資訊，請造訪 [自訂視覺 SDK 文章](https://github.com/Microsoft/Cognitive-CustomVision-Windows/)。

此類別負責：

- 載入以位元組陣列形式捕獲的最新映射。

- 將位元組陣列傳送至您的 Azure **自訂視覺服務** 實例以進行分析。

- 以 JSON 字串的形式接收回應。

- 將回應還原序列化，並將產生的 **預測** 傳遞給 **SceneOrganiser** 類別，這將會負責顯示回應的方式。

若要建立此類別：

1.  以滑鼠右鍵按一下 [**資產] 資料夾**，位於 **Project 面板** 中，然後按一下 [**建立**  >  **資料夾**]。 呼叫資料夾 **腳本**。

    ![](images/AzureLabs-Lab310-37.png)

2.  按兩下新建立的資料夾，將它開啟。

3.  在資料夾內按一下滑鼠右鍵，然後按一下 [**建立**  >  **C \# 腳本**]。 將腳本命名為 **CustomVisionAnalyser。**

4.  按兩下新的 **CustomVisionAnalyser** 腳本，以 **Visual Studio 開啟。**

5.  請確定您已在檔案頂端參考下列命名空間：

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.IO;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

6.  在 **CustomVisionAnalyser** 類別中，新增下列變數：

    ```csharp
        /// <summary>
        /// Unique instance of this class
        /// </summary>
        public static CustomVisionAnalyser Instance;

        /// <summary>
        /// Insert your prediction key here
        /// </summary>
        private string predictionKey = "- Insert your key here -";

        /// <summary>
        /// Insert your prediction endpoint here
        /// </summary>
        private string predictionEndpoint = "Insert your prediction endpoint here";

        /// <summary>
        /// Bite array of the image to submit for analysis
        /// </summary>
        [HideInInspector] public byte[] imageBytes;
    ```

    > [!NOTE]
    > 務必將您的 **服務預測金鑰** 插入至 **predictionKey** 變數，並將您的 **預測端點** 插入至 **predictionEndpoint** 變數。 您已將這些[記事本複製到先前第2章步驟14中的](#chapter-2---training-your-custom-vision-project)。

7.  現在需要新增 **喚醒 ()** 的程式碼，以初始化執行個體變數：

    ```csharp
        /// <summary>
        /// Initializes this class
        /// </summary>
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            Instance = this;
        }
    ```

8.  新增協同程式 (，並在其下方加入靜態 **GetImageAsByteArray ()** 方法) ，它會取得 **ImageCapture** 類別所捕捉的影像分析結果。

    > [!NOTE]
    > 在 [ **AnalyseImageCapture** ] 協同程式中，您還必須呼叫 **SceneOrganiser** 類別。 因此，請 **暫時將這些行** 加上批註。

    ```csharp    
        /// <summary>
        /// Call the Computer Vision Service to submit the image.
        /// </summary>
        public IEnumerator AnalyseLastImageCaptured(string imagePath)
        {
            Debug.Log("Analyzing...");

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

                Debug.Log("response: " + jsonResponse);

                // Create a texture. Texture size does not matter, since
                // LoadImage will replace with the incoming image size.
                //Texture2D tex = new Texture2D(1, 1);
                //tex.LoadImage(imageBytes);
                //SceneOrganiser.Instance.quadRenderer.material.SetTexture("_MainTex", tex);

                // The response will be in JSON format, therefore it needs to be deserialized
                //AnalysisRootObject analysisRootObject = new AnalysisRootObject();
                //analysisRootObject = JsonConvert.DeserializeObject<AnalysisRootObject>(jsonResponse);

                //SceneOrganiser.Instance.FinaliseLabel(analysisRootObject);
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

9. 刪除 [ **開始 ()** ] 並 **更新 ()** 方法，因為它們不會使用。 

10.  返回 **Unity** 之前，請務必將您的變更儲存在 **Visual Studio** 中。

> [!IMPORTANT]
> 如先前所述，請不要擔心可能出現錯誤的程式碼，因為您很快就會提供進一步的類別，這將會修正這些問題。

## <a name="chapter-6---create-the-customvisionobjects-class"></a>第6章-建立 CustomVisionObjects 類別

您將建立的類別現在是 **CustomVisionObjects** 類別。

此腳本包含其他類別用來序列化和還原序列化對自訂視覺服務進行之呼叫的物件數。

若要建立此類別：

1.  在 [**腳本**] 資料夾內按一下滑鼠右鍵，然後按一下 [**建立**  >  **C \# 腳本**]。 呼叫腳本 **CustomVisionObjects。**

2.  按兩下新的 **CustomVisionObjects** 腳本，以 **Visual Studio 開啟。**

3.  請確定您已在檔案頂端參考下列命名空間：

    ```csharp
    using System;
    using System.Collections.Generic;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

4.  刪除 **開始 ()** ，並 **更新** **CustomVisionObjects** 類別內的 () 方法，這個類別現在應該是空的。

    > [!WARNING]
    > 請務必小心遵循下一個指示。 如果您將新的類別宣告放在 **CustomVisionObjects** 類別內，您將會在第 [10 章](#chapter-10---create-the-imagecapture-class)取得編譯錯誤，指出找不到 **AnalysisRootObject** 和 **BoundingBox** 。

5.  將下列類別新增至 **CustomVisionObjects** 類別 *之外*。 **Newtonsoft** 程式庫會使用這些物件，將回應資料序列化和還原序列化：

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
    /// JSON of images submitted
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
    /// Predictions received by the Service
    /// after submitting an image for analysis
    /// Includes Bounding Box
    /// </summary>
    public class AnalysisRootObject
    {
        public string id { get; set; }
        public string project { get; set; }
        public string iteration { get; set; }
        public DateTime created { get; set; }
        public List<Prediction> predictions { get; set; }
    }

    public class BoundingBox
    {
        public double left { get; set; }
        public double top { get; set; }
        public double width { get; set; }
        public double height { get; set; }
    }

    public class Prediction
    {
        public double probability { get; set; }
        public string tagId { get; set; }
        public string tagName { get; set; }
        public BoundingBox boundingBox { get; set; }
    }
    ```

6.  返回 **Unity** 之前，請務必將您的變更儲存在 **Visual Studio** 中。

## <a name="chapter-7---create-the-spatialmapping-class"></a>第7章-建立 SpatialMapping 類別

這個類別會在場景中設定 **空間對應碰撞** ，以便能夠偵測虛擬物件與真實物件之間的衝突。

若要建立此類別：

1.  在 [**腳本**] 資料夾內按一下滑鼠右鍵，然後按一下 [**建立**  >  **C \# 腳本**]。 呼叫腳本 **SpatialMapping。**

2.  按兩下新的 **SpatialMapping** 腳本，以 **Visual Studio 開啟。**

3.  請確定您在 **SpatialMapping** 類別上方參考了下列命名空間：

    ```csharp
    using UnityEngine;
    using UnityEngine.XR.WSA;
    ```

4.  然後，在 **SpatialMapping** 類別內新增下列變數，並在 **Start ()** 方法的上方：

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static SpatialMapping Instance;

        /// <summary>
        /// Used by the GazeCursor as a property with the Raycast call
        /// </summary>
        internal static int PhysicsRaycastMask;

        /// <summary>
        /// The layer to use for spatial mapping collisions
        /// </summary>
        internal int physicsLayer = 31;

        /// <summary>
        /// Creates environment colliders to work with physics
        /// </summary>
        private SpatialMappingCollider spatialMappingCollider;
    ```

5.  新增 **喚醒的 ()** 並 **開始 ()**：

    ```csharp
        /// <summary>
        /// Initializes this class
        /// </summary>
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            Instance = this;
        }

        /// <summary>
        /// Runs at initialization right after Awake method
        /// </summary>
        void Start()
        {
            // Initialize and configure the collider
            spatialMappingCollider = gameObject.GetComponent<SpatialMappingCollider>();
            spatialMappingCollider.surfaceParent = this.gameObject;
            spatialMappingCollider.freezeUpdates = false;
            spatialMappingCollider.layer = physicsLayer;

            // define the mask
            PhysicsRaycastMask = 1 << physicsLayer;

            // set the object as active one
            gameObject.SetActive(true);
        }
    ```

6.  刪除 **更新 ()** 方法。

7.  返回 **Unity** 之前，請務必將您的變更儲存在 **Visual Studio** 中。


## <a name="chapter-8---create-the-gazecursor-class"></a>第8章-建立 GazeCursor 類別

這個類別負責利用上一章所建立的 **SpatialMappingCollider**，在實際空間的正確位置設定資料指標。

若要建立此類別：

1.  在 [**腳本**] 資料夾內按一下滑鼠右鍵，然後按一下 [**建立**  >  **C \# 腳本**]。 呼叫腳本 **GazeCursor**

2.  按兩下新的 **GazeCursor** 腳本，以 **Visual Studio 開啟。**

3.  請確定您在 **GazeCursor** 類別上方參考了下列命名空間：

    ```csharp
    using UnityEngine;
    ```

4.  然後，在 **GazeCursor** 類別內，于 **Start ()** 方法的上方新增下列變數。 

    ```csharp
        /// <summary>
        /// The cursor (this object) mesh renderer
        /// </summary>
        private MeshRenderer meshRenderer;
    ```

5.  以下列程式碼更新 **啟動 ()** 方法：

    ```csharp
        /// <summary>
        /// Runs at initialization right after the Awake method
        /// </summary>
        void Start()
        {
            // Grab the mesh renderer that is on the same object as this script.
            meshRenderer = gameObject.GetComponent<MeshRenderer>();

            // Set the cursor reference
            SceneOrganiser.Instance.cursor = gameObject;
            gameObject.GetComponent<Renderer>().material.color = Color.green;

            // If you wish to change the size of the cursor you can do so here
            gameObject.transform.localScale = new Vector3(0.01f, 0.01f, 0.01f);
        }
    ```

6.  使用下列程式碼更新 **更新 ()** 方法：

    ```csharp
        /// <summary>
        /// Update is called once per frame
        /// </summary>
        void Update()
        {
            // Do a raycast into the world based on the user's head position and orientation.
            Vector3 headPosition = Camera.main.transform.position;
            Vector3 gazeDirection = Camera.main.transform.forward;

            RaycastHit gazeHitInfo;
            if (Physics.Raycast(headPosition, gazeDirection, out gazeHitInfo, 30.0f, SpatialMapping.PhysicsRaycastMask))
            {
                // If the raycast hit a hologram, display the cursor mesh.
                meshRenderer.enabled = true;
                // Move the cursor to the point where the raycast hit.
                transform.position = gazeHitInfo.point;
                // Rotate the cursor to hug the surface of the hologram.
                transform.rotation = Quaternion.FromToRotation(Vector3.up, gazeHitInfo.normal);
            }
            else
            {
                // If the raycast did not hit a hologram, hide the cursor mesh.
                meshRenderer.enabled = false;
            }
        }
    ```

    > [!NOTE]
    > 請不要擔心找不到 **SceneOrganiser** 類別的錯誤，您將在下一章中建立它。

7. 返回 **Unity** 之前，請務必將您的變更儲存在 **Visual Studio** 中。

## <a name="chapter-9---create-the-sceneorganiser-class"></a>第9章-建立 SceneOrganiser 類別

此類別將會：

-   藉由將適當的元件附加至 *主要攝影機* 來設定。

-   當偵測到物件時，它會負責計算其在真實世界中的位置，並使用適當的 **標記名稱** 將 **標記標籤** 放在其附近。    

若要建立此類別：

1.  在 [**腳本**] 資料夾內按一下滑鼠右鍵，然後按一下 [**建立**  >  **C \# 腳本**]。 將腳本命名為 **SceneOrganiser**。

2.  按兩下新的 **SceneOrganiser** 腳本，以 **Visual Studio 開啟。**

3.  請確定您在 **SceneOrganiser** 類別上方參考了下列命名空間：

    ```csharp
    using System.Collections.Generic;
    using System.Linq;
    using UnityEngine;
    ```

4.  然後，在 **SceneOrganiser** 類別內，于 **Start ()** 方法的上方新增下列變數：

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static SceneOrganiser Instance;

        /// <summary>
        /// The cursor object attached to the Main Camera
        /// </summary>
        internal GameObject cursor;

        /// <summary>
        /// The label used to display the analysis on the objects in the real world
        /// </summary>
        public GameObject label;

        /// <summary>
        /// Reference to the last Label positioned
        /// </summary>
        internal Transform lastLabelPlaced;

        /// <summary>
        /// Reference to the last Label positioned
        /// </summary>
        internal TextMesh lastLabelPlacedText;

        /// <summary>
        /// Current threshold accepted for displaying the label
        /// Reduce this value to display the recognition more often
        /// </summary>
        internal float probabilityThreshold = 0.8f;

        /// <summary>
        /// The quad object hosting the imposed image captured
        /// </summary>
        private GameObject quad;

        /// <summary>
        /// Renderer of the quad object
        /// </summary>
        internal Renderer quadRenderer;
    ```

5.  刪除 [ **開始 ()** ]，並 **更新 ()** 方法。

6.  在變數底下，加入 **喚醒的 ()** 方法，這會初始化類別並設定場景。

    ```csharp
        /// <summary>
        /// Called on initialization
        /// </summary>
        private void Awake()
        {
            // Use this class instance as singleton
            Instance = this;

            // Add the ImageCapture class to this Gameobject
            gameObject.AddComponent<ImageCapture>();

            // Add the CustomVisionAnalyser class to this Gameobject
            gameObject.AddComponent<CustomVisionAnalyser>();

            // Add the CustomVisionObjects class to this Gameobject
            gameObject.AddComponent<CustomVisionObjects>();
        }
    ```

7.  新增 **PlaceAnalysisLabel ()** 方法，這個方法會在場景中具現 *化* 標籤 (這一點不會讓使用者) 看不見。 此外，它也會將四個 (也不可見，) 影像放置位置，並與真實世界重迭。 這點很重要，因為在分析之後從服務中取出的方塊座標會追溯到這個四個，以判定物件在真實世界中的大概位置。 

    ```csharp
        /// <summary>
        /// Instantiate a Label in the appropriate location relative to the Main Camera.
        /// </summary>
        public void PlaceAnalysisLabel()
        {
            lastLabelPlaced = Instantiate(label.transform, cursor.transform.position, transform.rotation);
            lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();
            lastLabelPlacedText.text = "";
            lastLabelPlaced.transform.localScale = new Vector3(0.005f,0.005f,0.005f);

            // Create a GameObject to which the texture can be applied
            quad = GameObject.CreatePrimitive(PrimitiveType.Quad);
            quadRenderer = quad.GetComponent<Renderer>() as Renderer;
            Material m = new Material(Shader.Find("Legacy Shaders/Transparent/Diffuse"));
            quadRenderer.material = m;

            // Here you can set the transparency of the quad. Useful for debugging
            float transparency = 0f;
            quadRenderer.material.color = new Color(1, 1, 1, transparency);

            // Set the position and scale of the quad depending on user position
            quad.transform.parent = transform;
            quad.transform.rotation = transform.rotation;

            // The quad is positioned slightly forward in font of the user
            quad.transform.localPosition = new Vector3(0.0f, 0.0f, 3.0f);

            // The quad scale as been set with the following value following experimentation,  
            // to allow the image on the quad to be as precisely imposed to the real world as possible
            quad.transform.localScale = new Vector3(3f, 1.65f, 1f);
            quad.transform.parent = null;
        }
    ```

8.  新增 **FinaliseLabel ()** 方法。 它負責：

    *   以具有最高信賴度的預測 *標記* 來設定 *標籤* 文字。
    *   呼叫四個物件的周 *框* 方塊計算，並在先前定位，並將標籤放置在場景中。
    *   使用 Raycast 朝向周 *框* 方塊來調整標籤深度，這應該會與真實世界中的物件發生衝突。
    * 重設 capture 進程，讓使用者可以捕獲另一個映射。

    ```csharp
        /// <summary>
        /// Set the Tags as Text of the last label created. 
        /// </summary>
        public void FinaliseLabel(AnalysisRootObject analysisObject)
        {
            if (analysisObject.predictions != null)
            {
                lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();
                // Sort the predictions to locate the highest one
                List<Prediction> sortedPredictions = new List<Prediction>();
                sortedPredictions = analysisObject.predictions.OrderBy(p => p.probability).ToList();
                Prediction bestPrediction = new Prediction();
                bestPrediction = sortedPredictions[sortedPredictions.Count - 1];

                if (bestPrediction.probability > probabilityThreshold)
                {
                    quadRenderer = quad.GetComponent<Renderer>() as Renderer;
                    Bounds quadBounds = quadRenderer.bounds;

                    // Position the label as close as possible to the Bounding Box of the prediction 
                    // At this point it will not consider depth
                    lastLabelPlaced.transform.parent = quad.transform;
                    lastLabelPlaced.transform.localPosition = CalculateBoundingBoxPosition(quadBounds, bestPrediction.boundingBox);

                    // Set the tag text
                    lastLabelPlacedText.text = bestPrediction.tagName;

                    // Cast a ray from the user's head to the currently placed label, it should hit the object detected by the Service.
                    // At that point it will reposition the label where the ray HL sensor collides with the object,
                    // (using the HL spatial tracking)
                    Debug.Log("Repositioning Label");
                    Vector3 headPosition = Camera.main.transform.position;
                    RaycastHit objHitInfo;
                    Vector3 objDirection = lastLabelPlaced.position;
                    if (Physics.Raycast(headPosition, objDirection, out objHitInfo, 30.0f,   SpatialMapping.PhysicsRaycastMask))
                    {
                        lastLabelPlaced.position = objHitInfo.point;
                    }
                }
            }
            // Reset the color of the cursor
            cursor.GetComponent<Renderer>().material.color = Color.green;

            // Stop the analysis process
            ImageCapture.Instance.ResetImageCapture();        
        }
    ```

9.  新增 **CalculateBoundingBoxPosition ()** 方法，它會裝載一些需要的計算，以轉譯從服務抓取的周 *框* 方塊座標，並在四個按比例重新建立。

    ```csharp
        /// <summary>
        /// This method hosts a series of calculations to determine the position 
        /// of the Bounding Box on the quad created in the real world
        /// by using the Bounding Box received back alongside the Best Prediction
        /// </summary>
        public Vector3 CalculateBoundingBoxPosition(Bounds b, BoundingBox boundingBox)
        {
            Debug.Log($"BB: left {boundingBox.left}, top {boundingBox.top}, width {boundingBox.width}, height {boundingBox.height}");

            double centerFromLeft = boundingBox.left + (boundingBox.width / 2);
            double centerFromTop = boundingBox.top + (boundingBox.height / 2);
            Debug.Log($"BB CenterFromLeft {centerFromLeft}, CenterFromTop {centerFromTop}");

            double quadWidth = b.size.normalized.x;
            double quadHeight = b.size.normalized.y;
            Debug.Log($"Quad Width {b.size.normalized.x}, Quad Height {b.size.normalized.y}");

            double normalisedPos_X = (quadWidth * centerFromLeft) - (quadWidth/2);
            double normalisedPos_Y = (quadHeight * centerFromTop) - (quadHeight/2);

            return new Vector3((float)normalisedPos_X, (float)normalisedPos_Y, 0);
        }
    ```

10. 返回 **Unity** 之前，請務必將您的變更儲存在 **Visual Studio** 中。

    > [!IMPORTANT]
    > 繼續之前，請先開啟 **CustomVisionAnalyser** 類別，然後在 **AnalyseLastImageCaptured ()** 方法中，將下列幾行 *取消* 批註：
    >
    >   ```csharp
    >   // Create a texture. Texture size does not matter, since 
    >   // LoadImage will replace with the incoming image size.
    >   Texture2D tex = new Texture2D(1, 1);
    >   tex.LoadImage(imageBytes);
    >   SceneOrganiser.Instance.quadRenderer.material.SetTexture("_MainTex", tex);
    >
    >   // The response will be in JSON format, therefore it needs to be deserialized
    >   AnalysisRootObject analysisRootObject = new AnalysisRootObject();
    >   analysisRootObject = JsonConvert.DeserializeObject<AnalysisRootObject>(jsonResponse);
    >
    >   SceneOrganiser.Instance.FinaliseLabel(analysisRootObject);
    >   ```

> [!NOTE]
> 不要擔心 **ImageCapture** 類別「找不到」訊息，您將在下一章中建立它。


## <a name="chapter-10---create-the-imagecapture-class"></a>第10章-建立 ImageCapture 類別

您即將建立的下一個類別是 **ImageCapture** 類別。

此類別負責：

*   使用 HoloLens 攝影機來捕捉影像，並將它儲存在 *應用程式* 資料夾中。
*   處理使用者的 *點擊* 手勢。

若要建立此類別：

1.  移至您先前建立的 **腳本** 資料夾。

2.  在資料夾內按一下滑鼠右鍵，然後按一下 [**建立**  >  **C \# 腳本**]。 將腳本命名為 **ImageCapture**。

3.  按兩下新的 **ImageCapture** 腳本，以 **Visual Studio 開啟。**

4.  以下列內容取代檔案頂端的命名空間：

    ```csharp
    using System;
    using System.IO;
    using System.Linq;
    using UnityEngine;
    using UnityEngine.XR.WSA.Input;
    using UnityEngine.XR.WSA.WebCam;
    ```

5.  然後，在 **ImageCapture** 類別內，于 **Start ()** 方法的上方新增下列變數：

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

            // Subscribing to the Microsoft HoloLens API gesture recognizer to track user gestures
            recognizer = new GestureRecognizer();
            recognizer.SetRecognizableGestures(GestureSettings.Tap);
            recognizer.Tapped += TapHandler;
            recognizer.StartCapturingGestures();
        }
    ```

7.  執行將在點一下手勢發生時呼叫的處理常式：

    ```csharp
        /// <summary>
        /// Respond to Tap Input.
        /// </summary>
        private void TapHandler(TappedEventArgs obj)
        {
            if (!captureIsActive)
            {
                captureIsActive = true;

                // Set the cursor color to red
                SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.red;

                // Begin the capture loop
                Invoke("ExecuteImageCaptureAndAnalysis", 0);
            }
        }
    ```

    > [!IMPORTANT]
    > 當游標為 **綠色** 時，表示相機可用來取得影像。 當游標是 **紅色** 時，表示相機正在忙碌中。

8.  新增應用程式用來啟動映射捕獲進程的方法，並儲存映射：

    ```csharp
        /// <summary>
        /// Begin process of image capturing and send to Azure Custom Vision Service.
        /// </summary>
        private void ExecuteImageCaptureAndAnalysis()
        {
            // Create a label in world space using the ResultsLabel class 
            // Invisible at this point but correctly positioned where the image was taken
            SceneOrganiser.Instance.PlaceAnalysisLabel();

            // Set the camera resolution to be the highest possible
            Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending
                ((res) => res.width * res.height).First();
            Texture2D targetTexture = new Texture2D(cameraResolution.width, cameraResolution.height);

            // Begin capture process, set the image format
            PhotoCapture.CreateAsync(true, delegate (PhotoCapture captureObject)
            {
                photoCaptureObject = captureObject;

                CameraParameters camParameters = new CameraParameters
                {
                    hologramOpacity = 1.0f,
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

9.  新增在拍攝相片時所要呼叫的處理常式，並在準備進行分析時進行呼叫。 結果接著會傳遞至 **CustomVisionAnalyser** 進行分析。

    ```csharp
        /// <summary>
        /// Register the full execution of the Photo Capture. 
        /// </summary>
        void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
        {
            try
            {
                // Call StopPhotoMode once the image has successfully captured
                photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
            }
            catch (Exception e)
            {
                Debug.LogFormat("Exception capturing photo to disk: {0}", e.Message);
            }
        }

        /// <summary>
        /// The camera photo mode has stopped after the capture.
        /// Begin the image analysis process.
        /// </summary>
        void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
        {
            Debug.LogFormat("Stopped Photo Mode");
        
            // Dispose from the object in memory and request the image analysis 
            photoCaptureObject.Dispose();
            photoCaptureObject = null;

            // Call the image analysis
            StartCoroutine(CustomVisionAnalyser.Instance.AnalyseLastImageCaptured(filePath)); 
        }

        /// <summary>
        /// Stops all capture pending actions
        /// </summary>
        internal void ResetImageCapture()
        {
            captureIsActive = false;

            // Set the cursor color to green
            SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.green;

            // Stop the capture loop if active
            CancelInvoke();
        }
    ```

10. 返回 **Unity** 之前，請務必將您的變更儲存在 **Visual Studio** 中。

## <a name="chapter-11---setting-up-the-scripts-in-the-scene"></a>第11章-在場景中設定腳本

既然您已撰寫此專案所需的所有程式碼，就可以開始在場景中設定腳本，並在 prefabs 上設定腳本，讓它們正常運作。

1.  在 **Unity 編輯器** 中，選取 [階層] **面板** 中的 [ **主要相機**]。
2.  在 [偵測 **器] 面板** 中，選取 **主要攝影機** ，然後按一下 [ **新增元件**]，然後搜尋 **SceneOrganiser** 腳本並按兩下，以將其新增。

    ![](images/AzureLabs-Lab310-38.png)

3.  在 [ **Project] 面板** 中，開啟 [ **Prefabs] 資料夾**，將 **標籤** 預製專案拖曳到您剛剛新增至 *主要攝影機* 之 **SceneOrganiser** 腳本中的 *卷* 標空白參考目標輸入區域，如下圖所示：

    ![](images/AzureLabs-Lab310-39.png)

4.  在 [階層]**面板** 中，選取 **主要攝影機** 的 **GazeCursor** 子系。
5.  在 [偵測 **器] 面板** 中，選取 [ **GazeCursor** ]，按一下 [ **新增元件**]，然後搜尋 **GazeCursor** 腳本並按兩下，以將其新增。

    ![](images/AzureLabs-Lab310-40.png)

6.  同樣地，在 [階層]**面板** 中，選取 **主要攝影機** 的 **SpatialMapping** 子系。
7.  在 [偵測 **器] 面板** 中，選取 [ **SpatialMapping** ]，按一下 [ **新增元件**]，然後搜尋 **SpatialMapping** 腳本並按兩下，以將其新增。

    ![](images/AzureLabs-Lab310-41.png)

**SceneOrganiser** 腳本中的程式碼會在執行時間期間，新增您未設定的其餘腳本。

## <a name="chapter-12---before-building"></a>第12章-建立前

若要執行應用程式的完整測試，您必須將它側載到您的 Microsoft HoloLens。

在執行之前，請確定：

-  [第3章](#chapter-3---set-up-the-unity-project)中所述的所有設定都已正確設定。
- 腳本 **SceneOrganiser** 會附加至 **主要攝影機** 物件。
- 腳本 **GazeCursor** 會附加到 **GazeCursor** 物件。
- 腳本 **SpatialMapping** 會附加到 **SpatialMapping** 物件。
- 在第 [5 章](#chapter-5---create-the-customvisionanalyser-class)步驟6：

    - 請務必將您的 **服務預測金鑰** 插入 **predictionKey** 變數中。
    - 您已將 **預測端點** 插入至 **predictionEndpoint** 類別。

## <a name="chapter-13---build-the-uwp-solution-and-sideload-your-application"></a>第13章-建立 UWP 解決方案並側載您的應用程式

您現在已準備好將您的應用程式建立為 UWP 解決方案，您將能夠部署至 Microsoft HoloLens。 若要開始建立程式：

1.  移至 [檔案 **> 組建] 設定**。

2.  勾選 **Unity C \# 專案**。

3.  按一下 [ **新增開啟的場景**]。 這會將目前開啟的場景加入組建中。

    ![](images/AzureLabs-Lab310-42.png)

4.  按一下 [建置]。 Unity 將會啟動一個 *檔案總管* 視窗，您需要在其中建立並選取要用來建立應用程式的資料夾。 立即建立該資料夾，並命名為 **應用程式**。 然後選取 [ **應用程式** ] 資料夾，然後按一下 [ **選取資料夾**]。

5.  Unity 將開始將您的專案建立到 **應用程式** 資料夾。

6.  Unity 完成組建之後 (可能需要一些時間) ，它會在您的組建位置開啟 **檔案總管** 視窗 (檢查您的工作列，因為它不一定會出現在您的視窗上方，但會通知您加入新的視窗) 。

7.  若要部署到 Microsoft HoloLens，您將需要該裝置的 IP 位址 (用於遠端部署) ，並確定它也已設定 **開發人員模式**。 若要這樣做：

    1.  在 HoloLens 時，請開啟 **設定**。

    2.  前往 **Network & Internet**  >  **wi-fi**  >  **Advanced Options**

    3.  記下 **IPv4** 位址。

    4.  接下來，流覽回到 **設定**，然後為開發 **人員更新 & 安全性**  >  

    5.  設定 [**開發人員模式]** *。*

8.  流覽至您的新 Unity 組建 (**應用程式** 資料夾) ，然後以 **Visual Studio** 開啟方案檔。

9.  在 [方案設定] 中選取 [ **Debug**]。

10. 在解決方案平臺中，選取 [ **x86]、[遠端電腦**]。 系統會提示您 (Microsoft HoloLens 中插入遠端裝置的 **IP 位址**，在此案例中，您記) 。

    ![](images/AzureLabs-Lab310-43.png)

11. 移至 [**組建**] 功能表，然後按一下 [**部署方案**]，將應用程式側載到您的 HoloLens。

12. 您的應用程式現在應該會出現在您 Microsoft HoloLens 上已安裝的應用程式清單中，準備好可供啟動！

### <a name="to-use-the-application"></a>若要使用應用程式：

* 查看您使用 **Azure 自訂視覺服務（物件偵測**）定型的物件，並使用 **點擊手勢**。
* 如果成功偵測到物件，則會出現具有標記名稱的全球空間 *標籤文字* 。

> [!IMPORTANT]
> 每次您捕獲相片並將其傳送至服務時，您可以返回 [服務] 頁面，然後以新捕獲的影像重新定型服務。 一開始，您可能也必須更正周 *框方塊* ，以更精確地重新定型服務。

> [!NOTE]
> 當 Unity 中的 Microsoft HoloLens 感應器和/或 SpatialTrackingComponent 無法放置適當的 colliders （相對於真實世界的物件）時，放置的標籤文字可能不會出現在物件附近。 如果是這種情況，請嘗試在不同的介面上使用應用程式。

## <a name="your-custom-vision-object-detection-application"></a>您自訂視覺的物件偵測應用程式

恭喜，您已建立混合的現實應用程式，以利用 Azure 自訂視覺的物件偵測 API，該 API 可辨識影像中的物件，然後在3D 空間中為該物件提供大約的位置。

![](images/AzureLabs-Lab310-00.png)

## <a name="bonus-exercises"></a>額外練習

### <a name="exercise-1"></a>練習 1

加入至文字標籤時，請使用半透明 cube，將真實物件包裝在3D 周 *框* 方塊中。

### <a name="exercise-2"></a>練習 2

訓練您的自訂視覺服務，以辨識更多物件。

### <a name="exercise-3"></a>練習3

辨識物件時播放音效。

### <a name="exercise-4"></a>練習4

使用 API 以您的應用程式所分析的相同影像來重新定型您的服務，以便讓服務更準確 (同時) 預測和定型。