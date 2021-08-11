---
title: HoloLens (第1代) 和 Azure 306-串流影片
description: 完成本課程，以瞭解如何在混合現實應用程式內執行 Azure 媒體服務。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure，混合的現實，學術，unity，教學課程，api，媒體服務，串流影片，360，沉浸，vr，Windows 10，Visual Studio
ms.openlocfilehash: 3f3567c140c3162258475c28c2ef149039e3c40ed418ed2801ac8c40dda00a8f
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2021
ms.locfileid: "115224135"
---
# <a name="hololens-1st-gen-and-azure-306-streaming-video"></a>HoloLens (第1代) 和 Azure 306：串流影片

<br>

>[!NOTE]
>混合實境學院教學課程的設計是以 HoloLens (第 1 代) 和混合實境沉浸式頭戴裝置為準。  因此，對於仍在尋找這些裝置開發指引的開發人員而言，我們覺得這些教學課程很重要。  這些教學課程 **_不會_** 使用用於 HoloLens 2 的最新工具組或互動進行更新。  系統會保留這些資訊，以繼續在支援的裝置上運作。 未來將會有一系列新的教學課程，將會示範如何針對 HoloLens 2 進行開發。  當張貼這些教學課程時，將會使用這些教學課程的連結來更新此通知。

<br> 

![最終產品-開始 ](images/AzureLabs-Lab6-00.png)
 ![ 最終產品-開始](images/AzureLabs-Lab6-01.png)

在此課程中，您將瞭解如何將您的 Azure 媒體服務連線到 Windows Mixed Reality 的 VR 體驗，以允許在沉浸式耳機上播放串流360度的影片。 

**Azure 媒體服務** 是一組服務，可為您提供廣播品質的影片串流服務，以觸及現今最受歡迎的行動裝置上的更大觀眾。 如需詳細資訊，請造訪[Azure 媒體服務頁面](https://azure.microsoft.com/services/media-services)。

完成本課程之後，您將會有一個混合現實的沉浸式耳機應用程式，它將能夠執行下列作業：

1. 透過 **Azure 媒體服務**，從 **Azure 儲存體** 取出360度的影片。

2. 顯示 Unity 場景內的已抓取360度影片。

3. 使用兩個不同的影片在兩個場景之間流覽。

在您的應用程式中，您可以自行決定如何將結果與您的設計整合。 本課程旨在告訴您如何將 Azure 服務與 Unity Project 整合。 您的工作是使用您在本課程中所得到的知識，來增強您的混合現實應用程式。

## <a name="device-support"></a>裝置支援

<table>
<tr>
<th>課程</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">沉浸式頭戴裝置</a></th>
</tr><tr>
<td> MR 和 Azure 306：串流視訊</td><td style="text-align: center;"> </td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="prerequisites"></a>必要條件

> [!NOTE]
> 本教學課程是專為擁有 Unity 和 c # 基本經驗的開發人員所設計。 另外也請注意，本檔中的必要條件和撰寫的指示，代表在撰寫 (可能是 2018) 時經過測試和驗證的內容。 您可以隨意使用最新的軟體（如 [ 安裝工具文章](../../install-the-tools.md)中所列），但不應假設此課程中的資訊會完全符合您在較新軟體中找到的資訊，而不是以下所列的資訊。

本課程建議您採用下列硬體和軟體：

- 開發電腦，與適用于沉浸式 (VR) 耳機開發的[Windows Mixed Reality 相容](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines)
- [啟用開發人員模式的 Windows 10 Fall Creators Update (或更新版本) ](../../install-the-tools.md#installation-checklist)
- [最新的 Windows 10 SDK](../../install-the-tools.md#installation-checklist)
- [Unity 2017。4](../../install-the-tools.md#installation-checklist)
- [Visual Studio 2017](../../install-the-tools.md#installation-checklist)
- [Windows Mixed Reality 沉浸式 (VR) 耳機](../../../discover/immersive-headset-hardware-details.md)
- 適用于 Azure 設定和資料抓取的網際網路存取
- 2 360 度影片採用的格式為， (您可以 [在此下載頁面](https://www.mettle.com/360vr-master-series-free-360-downloads-page) 找到一些免權利的影片) 

## <a name="before-you-start"></a>在您開始使用 Intune 之前

1.  為了避免在建立此專案時發生問題，強烈建議您在根或近端根資料夾中，建立本教學課程中所述的專案 (長的資料夾路徑可能會在組建階段) 時發生問題。
2.  設定及測試您的混合現實沉浸式耳機。

    > [!NOTE]
    > 在此課程中，您將 **不** 需要移動控制器。 如果您需要設定沉浸式耳機的支援，請按一下[如何設定 Windows Mixed Reality 的連結](https://support.microsoft.com/help/4043101/windows-10-set-up-windows-mixed-reality)。

## <a name="chapter-1---the-azure-portal-creating-the-azure-storage-account"></a>第1章-Azure 入口網站：建立 Azure 儲存體帳戶

若要使用 **Azure 儲存體服務**，您將需要在 Azure 入口網站中建立並設定 **儲存體帳戶**。

1.  登入 [Azure 入口網站](https://portal.azure.com)。

    > [!NOTE]
    > 如果您還沒有 Azure 帳戶，您將需要建立一個帳戶。 如果您在課堂或實驗室的情況下進行本教學課程，請洽詢講師或其中一個 proctors，協助您設定新的帳戶。

2.  登入後，按一下左側功能表中的 **儲存體帳戶**。

    ![Azure 儲存體帳戶設定](images/AzureLabs-Lab6-02.png)

3.  在 [**儲存體帳戶**] 索引標籤上，按一下 [**新增**]。

    ![Azure 儲存體帳戶設定](images/AzureLabs-Lab6-03.png)

4.  在 [ **建立儲存體帳戶** ] 索引標籤中：

    1.  為您的帳戶插入 **名稱** ，請注意，此欄位只接受數位和小寫字母。

    2.  在 [ **部署模型] 中，** 選取 [ **資源管理員**]。

    3.  For **Account kind**, select **Storage (general purpose v1)**.

    4.  針對 [ **效能**]，請選取 [ **標準 *]。**

    5.  針對 **複寫** ，請選取 **本機-多餘的儲存體 (LRS)**。

    6.  將 [ **需要安全傳輸** ] 保留為 **停用**。

    7.  選取 [訂用帳戶]  。

    8.  選擇資源群組，或建立一個新的 **資源群組** 。 資源群組提供一種方式來監視、控制存取、布建及管理 Azure 資產集合的計費。

    9.  如果您要建立新的資源群組) ，請判斷資源群組 (的 **位置** 。 位置最好是在應用程式執行所在的區域中。 某些 Azure 資產僅適用于某些區域。

5.  您必須確認您已瞭解套用到此服務的條款及條件。

    ![Azure 儲存體帳戶設定](images/AzureLabs-Lab6-04.png)

6.  當您按一下 [ **建立**] 之後，就必須等待服務建立完成，這可能需要一分鐘的時間。

7.  建立服務實例之後，入口網站中就會出現通知。

    ![Azure 儲存體帳戶設定](images/AzureLabs-Lab6-05.png)

8.  此時您不需要遵循資源，只要移至下一章即可。

## <a name="chapter-2---the-azure-portal-creating-the-media-service"></a>第2章-Azure 入口網站：建立媒體服務

若要使用 Azure 媒體服務，您必須將服務的實例設定為可供您的應用程式使用 (其中帳戶持有者必須是系統管理員) 。

1.  在 Azure 入口網站中，按一下左上角的 [ **建立資源** ]，並搜尋 **媒體服務，** 然後按 **enter**。 您目前想要的資源有粉紅色圖示;按一下此，以顯示新的頁面。

    ![Azure 入口網站](images/AzureLabs-Lab6-06.png)

2.  新頁面將提供 **媒體服務** 的描述。 在此提示的左下方，按一下 [ **建立** ] 按鈕，以建立與此服務的關聯。

    ![Azure 入口網站](images/AzureLabs-Lab6-07.png)

3.  當您按一下 [ **建立** 面板] 之後，就會出現您需要提供有關新媒體服務的一些詳細資料的位置：

    1.  為此服務實例插入您想要的 **帳戶名稱** 。

    2.  選取 [訂用帳戶]  。

    3. 選擇資源群組，或建立一個新的 **資源群組** 。 資源群組提供一種方式來監視、控制存取、布建及管理 Azure 資產集合的計費。 建議您保留與單一專案相關聯的所有 Azure 服務 (例如，) 一般資源群組下的實驗室，) 。 
    
    > 如果您想要深入瞭解 Azure 資源群組，請遵循此 [連結，以瞭解如何管理 Azure 資源群組](/azure/azure-resource-manager/resource-group-portal)。

    4.  如果您要建立新的資源群組) ，請判斷資源群組 (的 **位置** 。 位置最好是在應用程式執行所在的區域中。 某些 Azure 資產僅適用于某些區域。

    5.  在 [**儲存體帳戶**] 區段中，按一下 [**請選取 ...** ] 區段，然後按一下您在上一章中建立的 **儲存體帳戶**。

    6.  您也必須確認您已瞭解套用到此服務的條款及條件。

    7.  按一下 [建立]。

        ![Azure 入口網站](images/AzureLabs-Lab6-08.png)

4.  當您按一下 [ **建立**] 之後，就必須等待服務建立完成，這可能需要一分鐘的時間。

5.  建立服務實例之後，入口網站中就會出現通知。

    ![Azure 入口網站](images/AzureLabs-Lab6-09.png)

6.  按一下通知以探索新的服務實例。

    ![Azure 入口網站](images/AzureLabs-Lab6-10.png)

7.  按一下通知中的 [ **移至資源** ] 按鈕，以流覽您的新服務實例。

8.  在 [新的媒體服務] 頁面中，按一下左側面板中的 [ **資產** ] 連結，這是大約的一半。

9.  在下一個頁面的頁面左上角，按一下 [ **Upload**]。

    ![Azure 入口網站](images/AzureLabs-Lab6-11.png)

10. 按一下 **資料夾** 圖示以流覽您的檔案，然後選取您想要串流的第一部360影片。 
    
    > 您可以遵循此 [連結下載影片範例](https://vimeo.com/214401712)。

    ![Azure 入口網站](images/AzureLabs-Lab6-12.png)

> [!WARNING]
> 長檔名可能會造成編碼器的問題：為了確保影片沒有問題，請考慮縮短影片檔案名的長度。

11. 當影片完成上傳時，進度列就會變成綠色。

    ![Azure 入口網站](images/AzureLabs-Lab6-13.png)

12. 按一下上方的文字 (**yourservicename-資產** ]) 返回 [ **資產** ] 頁面。

13. 您將會注意到您的影片已成功上傳。 按一下它。

    ![Azure 入口網站](images/AzureLabs-Lab6-14.png)

14. 您要重新導向的頁面會顯示有關您影片的詳細資訊。 若要能夠使用您的影片，您必須按一下頁面左上角的 [ **編碼** ] 按鈕進行編碼。

    ![Azure 入口網站](images/AzureLabs-Lab6-15.png)

15. 新的面板會顯示在右側，您可以在其中設定檔案的編碼選項。 設定下列屬性 (有些預設值已設定) ：

    1.  **媒體編碼器名稱 *媒體編碼器標準***

    2.  **編碼預設 *內容自動調整多重位元速率* 的值**

    3.  ***Video1.mp4的作業名稱媒體編碼器標準處理***

    4.  **輸出媒體資產名稱 *Video1.mp4--媒體編碼器標準編碼***

        ![Azure 入口網站](images/AzureLabs-Lab6-16.png)

16. 按一下 [ **建立** ] 按鈕。

17. 您會看到 **已新增編碼作業** 的橫條，請按一下該列，隨即會出現一個面板，其中顯示編碼進度。

    ![Azure 入口網站](images/AzureLabs-Lab6-17.png)

    ![Azure 入口網站](images/AzureLabs-Lab6-18.png)

18. 等候作業完成。 完成之後，您可以使用該面板右上方的 ' X ' 來關閉面板。

    ![Azure 入口網站](images/AzureLabs-Lab6-19.png)

    ![Azure 入口網站](images/AzureLabs-Lab6-20.png)

    > [!IMPORTANT]
    > 所需的時間取決於您的影片檔案大小。 此程式可能需要相當長的時間。

19. 現在已建立影片的編碼版本，您可以將其發佈，使其可供存取。 若要這樣做，請按一下藍色連結 **資產** 以返回 [資產] 頁面。

    ![Azure 入口網站](images/AzureLabs-Lab6-21.png)

20. 您將會看到您的影片與另一個，也就是 **_多位元率_ 的資產類型**。

    ![Azure 入口網站](images/AzureLabs-Lab6-22.png)

    > [!NOTE] 
    > 您可能會注意到，新的資產與您的初始影片是 *未知* 的，且其 **大小** 為 ' 0 ' 個位元組，只要重新整理您的視窗，即可進行更新。

21. 按一下此新資產。

    ![Azure 入口網站](images/AzureLabs-Lab6-23.png)

22. 您將會看到與先前所用的面板類似的面板，只是這是不同的資產。 按一下位於頁面頂端的 [ **發佈** ] 按鈕。

    ![Azure 入口網站](images/AzureLabs-Lab6-24.png)

23. 系統會提示您將 **定位器**（即進入點）設定為您資產中的檔案。 針對您的案例，請設定下列屬性：

    1.  **定位器類型**  > **漸進式**。

    2.  在此案例中，會將您的 **日期** 和 **時間** 設定為您目前的日期，到未來的時間 (100 年) 。 保持原狀，或將它變更為 [符合]。

    > [!NOTE]
    > 如需定位器的詳細資訊，以及您可以選擇的內容，請造訪[Azure 媒體服務檔](/azure/media-services/media-services-concepts)。

24. 在該面板的底部，按一下 [ **新增** ] 按鈕。

    ![Azure 入口網站](images/AzureLabs-Lab6-25.png)

25. 您的影片現在已發佈，可以使用其端點進行串流處理。 頁面上的下一頁是 [檔案 **] 區段。** 這是您影片的不同編碼版本的位置。 選取下圖中的最高可能解析度一個 (在下圖中，它是1920x960 檔案) ，然後將會出現右側面板。 您會在該處找到 **下載 URL**。 複製此 **端點** ，因為您稍後會在程式碼中使用它。

    ![Azure 入口網站](images/AzureLabs-Lab6-26.png)    

    ![Azure 入口網站](images/AzureLabs-Lab6-27.png)

    > [!NOTE] 
    > 您也可以按下 [ **播放** ] 按鈕播放影片並進行測試。

26. 您現在必須上傳您將在此實驗中使用的第二部影片。 遵循上述步驟，為第二部影片重複相同的程式。 請確定您也複製了第二個 **端點** 。 使用下列 [連結下載第二部影片](https://vimeo.com/214402865)。

27. 這兩個影片都發佈之後，您就可以開始進行下一章。

## <a name="chapter-3---setting-up-the-unity-project"></a>第3章-設定 Unity Project

以下是使用混合式開發進行開發的一般設定，因此，它是適用于其他專案的絕佳範本。

1.  開啟 **Unity** ，然後按一下 [ **新增**]。 

    ![Azure 入口網站](images/AzureLabs-Lab6-28.png)

2.  您現在將需要提供 Unity Project 名稱，請插入 **MR \_ 360VideoStreaming。** 請確定專案類型設定為 **3d**。 將位置設定為適合您 (記住，較接近根目錄的) 。 然後，按一下 [ **建立專案**]。

    ![Azure 入口網站](images/AzureLabs-Lab6-29.png)

3.  在 Unity 開啟的情況下，值得檢查預設 **腳本編輯器** 是否設定為 **Visual Studio。** 移至 [ **_編輯_*喜好*** 設定]，然後在新視窗中，流覽至 [**外部工具**]。 將 **外部腳本編輯器** 變更為 **Visual Studio 2017**。 關閉 [ **喜好** 設定] 視窗。

    ![Azure 入口網站](images/AzureLabs-Lab6-30.png)

4.  接下來，移至 [檔案 ***組建設定*** ]，然後按一下 [**切換平臺**] 按鈕，將平臺切換至 [**通用 Windows 平臺**]。

5.  也請確定：

    1. **目標裝置** 設定為 **任何裝置。**
    
    2.  **組建類型** 設定為 **D3D。**

    3.  **SDK** 設定為 [ **最新安裝]。**

    4.  **Visual Studio 版本** 設定為 [**最新安裝]。**

    5.  **組建並執行** 設定為 [ **本機電腦]。**

    6.  請不要擔心立即設定 **幕後** 的工作，因為您稍後將會進行設定。

    7.  其餘設定應該保留為預設值。

        ![設定 Unity Project](images/AzureLabs-Lab6-31.png)

6.  在 [**組建設定**] 視窗中，按一下 [播放程式]**設定** 按鈕，這會開啟偵測 **器** 所在空間中的相關面板。 

7. 在此面板中，需要驗證幾個設定：

    1.  在 [**其他設定**] 索引標籤中：

        1.  **腳本****執行階段版本** 應該是 **穩定** 的 ( .net 3.5 對等) 。

        2. **腳本後端** 應該是 **.net。**

        3. **API 相容性層級** 應為 **.net 4.6。**

            ![設定 Unity Project](images/AzureLabs-Lab6-32.png)

    2.  接下來的面板中，在 **XR 設定** (的 [**發佈設定**) ]、[滴答 **虛擬實境支援**]，請確定已新增 **Windows Mixed Reality SDK** 。

        ![設定 Unity Project](images/AzureLabs-Lab6-33.png)

    3.  在 [**發行設定**] 索引標籤的 [**功能**] 下，選取：

        - **InternetClient**

            ![設定 Unity Project](images/AzureLabs-Lab6-34.png)

8.  進行這些變更之後，請關閉 **組建設定** 視窗。

9.  儲存您的 Project **File* * save Project * *。



## <a name="chapter-4---importing-the-insideoutsphere-unity-package"></a>第4章-匯入 InsideOutSphere Unity 套件

> [!IMPORTANT]
> 如果您想要略過此課程的 *Unity 設定* 元件，並直接繼續進行程式碼，請隨意下載 [unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20306%20-%20Streaming%20video/Azure-MR-306.unitypackage)，並將其匯入到您的專案中做為 [**自訂套件**](https://docs.unity3d.com/Manual/AssetPackages.html)，然後繼續進行 **第5章**。 您仍然需要建立 Unity Project。

在此課程中，您將需要下載名為 [**InsideOutSphere. unitypackage**](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20306%20-%20Streaming%20video/InsideOutSphere.unitypackage)的 Unity 資產套件。

如何匯入 **unitypackage**：

1.  使用 Unity 儀表板，在畫面頂端的功能表中按一下 [ **資產** ]，然後按一下 [匯 **入封裝 > 自訂套件**]。

    ![匯入 InsideOutSphere Unity 套件](images/AzureLabs-Lab6-35.png)

2.  使用檔案選擇器選取 **InsideOutSphere unitypackage** 封裝，然後按一下 [ **開啟**]。 系統會向您顯示此資產的元件清單。 按一下 [匯 **入**] 以確認匯入。

    ![匯入 InsideOutSphere Unity 套件](images/AzureLabs-Lab6-36.png)

3.  匯入完成後，您會注意到您的 **資產** 資料夾中有三個新的資料夾、**材質**、**模型** 和 **Prefabs**。 這種資料夾結構一般適用于 Unity 專案。

    ![匯入 InsideOutSphere Unity 套件](images/AzureLabs-Lab6-37.png)

    1.  開啟 [ **模型** ] 資料夾，您會看到 **InsideOutSphere** 模型已匯入。

    2.  在 [ **材質] 資料夾內** ，您會發現 **InsideOutSpheres** 材質  *Lambert1*，以及一個稱為 *ButtonMaterial* 的材質，這是 GazeButton 所使用的資料，您很快就會看到。

    3.  **Prefabs** 資料夾包含 **InsideOutSphere** 預製專案，其中包含 **InsideOutSphere** *模型* 和 *GazeButton*。

    4.  **未包含任何程式碼**，您將遵循本課程來撰寫程式碼。


4.  **在階層中，選取****主要攝影機** 物件，並更新下列元件：

    1.  **轉換**

        1.  Position = **X**：0， **Y**：0， **Z**：0。

        2. 旋轉 = **X**：0， **Y**：0， **Z**：0。

        3. Scale **X**：1， **Y**：1， **Z**：1。

    2.  **相機**

        1. **清除旗標**：單色。

        2.  **裁剪平面**：近：0.1，遠：6。

            ![匯入 InsideOutSphere Unity 套件](images/AzureLabs-Lab6-38.png)

5.  流覽至 [ **預製專案** ] 資料夾，然後將 [ **InsideOutSphere** 預製專案] 拖曳至 [階層 **] 面板中** 。

    ![匯入 InsideOutSphere Unity 套件](images/AzureLabs-Lab6-39.png)

6.  按一下其旁邊的小箭號，以展開階層 **內的** **InsideOutSphere** 物件。 您將會在其底下看到稱為 **GazeButton** 的 **子** 物件。 這會用來變更幕後和影片。

    ![匯入 InsideOutSphere Unity 套件](images/AzureLabs-Lab6-40.png)

7.  在 [偵測器] 視窗中，按一下 **InsideOutSphere** 的 [轉換] 元件，確定已設定下列屬性：

    |            |    轉換-位置   |           |
    | :---------:| :-----------------------: | :--------:|
    |   **X** 0  |          **Y** 0          |  **Z** 0  |

    |            |    轉換-旋轉   |           |
    | :---------:| :-----------------------: | :--------:|
    |   **X** 0  |          **Y** -50        |  **Z** 0  |

    |            |     轉換-調整規模     |           |
    | :---------:| :-----------------------: | :--------:|
    |  **X** 1   |          **Y** 1          |  **Z** 1  |

    ![匯入 InsideOutSphere Unity 套件](images/AzureLabs-Lab6-41.png)

8.  按一下 [ **GazeButton** ] 子物件，並設定其 **轉換** ，如下所示：

    |            |    轉換-位置   |           |
    | :---------:| :-----------------------: | :--------:|
    |   **X** 3。6|          **Y** 1。3        |  **Z** 0  |

    |            |    轉換-旋轉   |           |
    | :---------:| :-----------------------: | :--------:|
    |   **X** 0  |          **Y** 0          |  **Z** 0  |

    |            |     轉換-調整規模     |           |
    | :---------:| :-----------------------: | :--------:|
    |  **X** 1   |          **Y** 1          |  **Z** 1  |

    ![匯入 InsideOutSphere Unity 套件](images/AzureLabs-Lab6-42.png)


## <a name="chapter-5---create-the-videocontroller-class"></a>第5章-建立 VideoController 類別

**VideoController** 類別裝載兩個將用來從 Azure 媒體服務串流內容的影片端點。

若要建立此類別：

1.  以滑鼠右鍵按一下 [**資產] 資料夾**，位於 **Project** 面板中，然後按一下 [**建立] > 資料夾**。 將資料夾命名為 **腳本**。

    ![建立 VideoController 類別](images/AzureLabs-Lab6-43.png)

    ![建立 VideoController 類別](images/AzureLabs-Lab6-44.png)

2.  按兩下 [ **腳本** ] 資料夾以開啟它。

3.  在資料夾內按一下滑鼠右鍵，然後按一下 [ **建立 > C \# 腳本**]。 將腳本命名為 **VideoController**。

    ![建立 VideoController 類別](images/AzureLabs-Lab6-45.png)

4.  按兩下新的 **VideoController** 腳本，以 **Visual Studio 2017 開啟。**

    ![建立 VideoController 類別](images/AzureLabs-Lab6-46.png)

5.  更新程式碼檔案頂端的命名空間，如下所示：

    ```csharp
    using System.Collections;
    using UnityEngine;
    using UnityEngine.SceneManagement;
    using UnityEngine.Video;
    ```

6.  在 **VideoController** 類別中輸入下列變數，以及 **喚醒的 ()** 方法：

    ```csharp
        /// <summary> 
        /// Provides Singleton-like behaviour to this class. 
        /// </summary> 
        public static VideoController instance; 
        
        /// <summary> 
        /// Reference to the Camera VideoPlayer Component.
        /// </summary> 
        private VideoPlayer videoPlayer; 
        
        /// <summary>
        /// Reference to the Camera AudioSource Component.
        /// </summary> 
        private AudioSource audioSource; 
        
        /// <summary> 
        /// Reference to the texture used to project the video streaming 
        /// </summary> 
        private RenderTexture videoStreamRenderTexture;

        /// <summary>
        /// Insert here the first video endpoint
        /// </summary>
        private string video1endpoint = "-- Insert video 1 Endpoint here --";

        /// <summary>
        /// Insert here the second video endpoint
        /// </summary>
        private string video2endpoint = "-- Insert video 2 Endpoint here --";

        /// <summary> 
        /// Reference to the Inside-Out Sphere. 
        /// </summary> 
        public GameObject sphere;

        void Awake()
        {
            instance = this;
        }
    ```

7.  現在是從您的 Azure 媒體服務影片進入端點的時間：

    1.  *Video1endpoint* 變數中的第一個。
    
    2.  *Video2endpoint* 變數中的第二個。

    > [!WARNING]
    > 在 Unity 中使用 *HTTPs* 的已知問題，版本 2017.4.1 f1。 如果影片在播放時發生錯誤，請嘗試改為使用 ' HTTP '。

8.  接下來，必須編輯 **開始 ()** 方法。 每次使用者切換場景時都會觸發這個方法， (藉由查看注視按鈕來切換影片) 。

    ```csharp
        // Use this for initialization
        void Start()
        {
            Application.runInBackground = true;
            StartCoroutine(PlayVideo());
        }
    ```

9.  在 **Start ()** 方法之後，插入 **>playvideo ()** *IEnumerator* 方法，此方法將用來順暢地啟動影片 (因此) 不會出現任何斷斷續續。

    ```csharp
        private IEnumerator PlayVideo()
        {
            // create a new render texture to display the video 
            videoStreamRenderTexture = new RenderTexture(2160, 1440, 32, RenderTextureFormat.ARGB32);

            videoStreamRenderTexture.Create();

            // assign the render texture to the object material 
            Material sphereMaterial = sphere.GetComponent<Renderer>().sharedMaterial;

            //create a VideoPlayer component 
            videoPlayer = gameObject.AddComponent<VideoPlayer>();

            // Set the video to loop. 
            videoPlayer.isLooping = true;

            // Set the VideoPlayer component to play the video from the texture 
            videoPlayer.renderMode = VideoRenderMode.RenderTexture;

            videoPlayer.targetTexture = videoStreamRenderTexture;

            // Add AudioSource 
            audioSource = gameObject.AddComponent<AudioSource>();

            // Pause Audio play on Awake 
            audioSource.playOnAwake = true;
            audioSource.Pause();

            // Set Audio Output to AudioSource 
            videoPlayer.audioOutputMode = VideoAudioOutputMode.AudioSource;
            videoPlayer.source = VideoSource.Url;

            // Assign the Audio from Video to AudioSource to be played 
            videoPlayer.EnableAudioTrack(0, true);
            videoPlayer.SetTargetAudioSource(0, audioSource);

            // Assign the video Url depending on the current scene 
            switch (SceneManager.GetActiveScene().name)
            {
                case "VideoScene1":
                    videoPlayer.url = video1endpoint;
                    break;

                case "VideoScene2":
                    videoPlayer.url = video2endpoint;
                    break;

                default:
                    break;
            }

            //Set video To Play then prepare Audio to prevent Buffering 
            videoPlayer.Prepare();

            while (!videoPlayer.isPrepared)
            {
                yield return null;
            }

            sphereMaterial.mainTexture = videoStreamRenderTexture;

            //Play Video 
            videoPlayer.Play();

            //Play Sound 
            audioSource.Play();

            while (videoPlayer.isPlaying)
            {
                yield return null;
            }
        }
    ```

10. 這個類別所需的最後一個方法是 **ChangeScene ()** 方法，它會用來在場景之間交換。

    ```csharp
        public void ChangeScene()
        {
            SceneManager.LoadScene(SceneManager.GetActiveScene().name == "VideoScene1" ? "VideoScene2" : "VideoScene1");
        }
    ```

    > [!TIP] 
    > **ChangeScene ()** 方法會使用一個方便 \# 的 C 功能，稱為 *條件運算子*。 如此一來，就可以檢查條件，然後根據檢查結果傳回值，全都在單一語句內。 請遵循此 [連結來深入瞭解條件運算子](/dotnet/csharp/language-reference/operators/conditional-operator)。

11. 在回到 Unity 之前，請先將您的變更儲存在 Visual Studio 中。

12. 回到 Unity 編輯器中，按一下 [from] {. 底線} [ **VideoController** ] 類別，然後將 [ **Scripts** ] 資料夾拖曳至 [階層]**面板中** 的 [**主要攝影機**] 物件。

13. 按一下 **主要攝影機** ，然後查看 [偵測 **器] 面板**。 您會發現，在新加入的腳本元件中，有一個具有空白值的欄位。 這是參考欄位，以程式碼中的公用變數為目標。

14. 將 **InsideOutSphere** 物件從 [階層] **面板** 拖曳至 **球體** 位置，如下圖所示。

    ![建立 VideoController 類別 ](images/AzureLabs-Lab6-47.png)
     ![ 建立 VideoController 類別](images/AzureLabs-Lab6-48.png)

## <a name="chapter-6---create-the-gaze-class"></a>第6章-建立注視類別

此類別負責建立將從 **主要相機** 向前投影的 **Raycast** ，以偵測使用者所查看的物件。 在此情況下， **Raycast** 將需要識別使用者是否正在查看場景中的 **GazeButton** 物件，並觸發行為。

若要建立此類別：

1.  移至您先前建立的 **腳本** 資料夾。

2.  在 **Project** 面板中按一下滑鼠右鍵，**建立** C \# 腳本 * *。 將腳本命名為 **注視**。

3.  按兩下新的 ***注視** _ 腳本，使用 _ *Visual Studio 2017* 來開啟它。*

4.  請確定下列命名空間位於腳本頂端，並移除任何其他命名空間：

    ```csharp
    using UnityEngine;
    ```

5.  然後，在 **注視** 類別內新增下列變數：

    ```csharp
        /// <summary> 
        /// Provides Singleton-like behaviour to this class. 
        /// </summary> 
        public static Gaze instance;

        /// <summary> 
        /// Provides a reference to the object the user is currently looking at. 
        /// </summary> 
        public GameObject FocusedGameObject { get; private set; }

        /// <summary> 
        /// Provides a reference to compare whether the user is still looking at 
        /// the same object (and has not looked away). 
        /// </summary> 
        private GameObject oldFocusedObject = null;

        /// <summary> 
        /// Max Ray Distance 
        /// </summary> 
        float gazeMaxDistance = 300;

        /// <summary> 
        /// Provides whether an object has been successfully hit by the raycast. 
        /// </summary> 
        public bool Hit { get; private set; }
    ```

6.  現在需要新增 **喚醒 ()** 和 **啟動 ()** 方法的程式碼。

    ```csharp
        private void Awake()
        {
            // Set this class to behave similar to singleton 
            instance = this;
        }

        void Start()
        {
            FocusedGameObject = null;
        }
    ```

7.  在 **Update ()** 方法中新增下列程式碼，以投影 Raycast 並偵測目標點擊：

    ```csharp
        void Update()
        {
            // Set the old focused gameobject. 
            oldFocusedObject = FocusedGameObject;
            RaycastHit hitInfo;

            // Initialise Raycasting. 
            Hit = Physics.Raycast(Camera.main.transform.position, Camera.main.transform.forward, out hitInfo, gazeMaxDistance);

            // Check whether raycast has hit. 
            if (Hit == true)
            {
                // Check whether the hit has a collider. 
                if (hitInfo.collider != null)
                {
                    // Set the focused object with what the user just looked at. 
                    FocusedGameObject = hitInfo.collider.gameObject;
                }
                else
                {
                    // Object looked on is not valid, set focused gameobject to null. 
                    FocusedGameObject = null;
                }
            }
            else
            {
                // No object looked upon, set focused gameobject to null.
                FocusedGameObject = null;
            }

            // Check whether the previous focused object is this same 
            // object (so to stop spamming of function). 
            if (FocusedGameObject != oldFocusedObject)
            {
                // Compare whether the new Focused Object has the desired tag we set previously. 
                if (FocusedGameObject.CompareTag("GazeButton"))
                {
                    FocusedGameObject.SetActive(false);
                    VideoController.instance.ChangeScene();
                }
            }
        }
    ```

8.  在回到 Unity 之前，請先將您的變更儲存在 Visual Studio 中。

9.  按一下 [腳本] 資料夾中的 [ **注視** ] 類別，並將其拖曳至 [階層 **] 面板中** 的 [主要攝影機] 物件。

## <a name="chapter-7---setup-the-two-unity-scenes"></a>第7章-設定兩個 Unity 場景

本章的目的是要設定兩個場景，每個都裝載要串流的影片。 您將複製已建立的場景，如此您就不需要再設定一次，不過您接著會編輯新的場景，讓 *GazeButton* 物件位於不同的位置，並具有不同的外觀。 這是為了示範如何在幕後變更。

1.  若要這麼做，請前往 [檔案 **> 將場景另存為**...]。[儲存] 視窗隨即出現。 按一下 [ **新增資料夾** ] 按鈕。

    ![第7章-設定兩個 Unity 場景](images/AzureLabs-Lab6-49.png)

2.  將資料夾命名為 **幕後**。

3.  [ **儲存場景** ] 視窗仍會開啟。 開啟新建立的 **場景** 資料夾。

4.  在 [ **檔案名：** 文字] 欄位中，輸入 **VideoScene1**，然後按 [ **儲存**]。

5.  回到 Unity，開啟您的 **場景** 資料夾，然後以滑鼠左鍵按一下您的 **VideoScene1** 檔案。 使用鍵盤，然後按 **Ctrl + D** ，即可複製該場景

    > [!TIP]
    > 您也可以藉由流覽來 **編輯 > 複製** 來執行 **重複** 的命令。

6.  Unity 會自動遞增場景名稱，但仍請檢查，以確保它符合先前插入的程式碼。

    >  您應具備 **VideoScene1** 和 **VideoScene2**。

7.  使用您的兩個場景，移至 [檔案 **> 組建設定**。 在 [**組建設定**] 視窗開啟時，將您的場景拖曳至 [組建] 區段 **中的場景**。

    ![第7章--設定兩個 Unity 場景](images/AzureLabs-Lab6-50.png)

    > [!TIP] 
    > 您可以透過按住 **Ctrl** 鍵，然後在每個場景上按一下滑鼠左鍵，然後將兩者拖曳，以從您的 **場景** 資料夾選取這兩個場景。

8.  關閉 **組建設定** 視窗，然後按兩下 **VideoScene2**。

9.  開啟第二個場景時，按一下 **InsideOutSphere** 的 **GazeButton** 子物件，並設定其轉換，如下所示：

    |            |    轉換-位置   |           |
    | :---------:| :-----------------------: | :--------:|
    |   **X** 0  |         **Y** 1。3         | **Z** 3。6 |

    |            |    轉換-旋轉   |           |
    | :---------:| :-----------------------: | :--------:|
    |   **X** 0  |          **Y** 0          |  **Z** 0  |

    |            |     轉換-調整規模     |           |
    | :---------:| :-----------------------: | :--------:|
    |  **X** 1   |          **Y** 1          |  **Z** 1  |

10. 在仍選取 **GazeButton** 子 **系的情況** 下，查看偵測器和 **網格篩選**。 按一下 **網格** 參考欄位旁的小小目標：

    ![第7章--設定兩個 Unity 場景](images/AzureLabs-Lab6-51.png)

11. [ **選取網格** ] 快顯視窗隨即出現。 按兩下 **資產** 清單中的 **Cube** 網格。

    ![第7章--設定兩個 Unity 場景](images/AzureLabs-Lab6-52.png)

12. **網格篩選器** 將會更新，現在是一個 **Cube**。 現在，按一下 [**球體碰撞**] 旁的 **齒輪** 圖示，然後按一下 [**移除元件**]，即可從這個物件中刪除碰撞。

    ![第7章--設定兩個 Unity 場景](images/AzureLabs-Lab6-53.png)

13. 在仍選取 **GazeButton** 的情況下，按一下位於偵測 **器** 底部的 [**新增元件**] 按鈕。 在 [搜尋] 欄位中 **，輸入方塊**，方塊 **碰撞** 者將會是選項，請按一下此選項，將方塊 **碰撞** 程式新增至您的 **GazeButton** 物件。

    ![第7章--設定兩個 Unity 場景](images/AzureLabs-Lab6-54.png)

14. **GazeButton** 現在已部分更新，看起來會不同，不過，您現在會建立新的 **材質**，讓它看起來完全不同，而且比第一個場景中的物件更容易辨識為不同的物件。

15. 流覽至 [ **Project 面板** 中的 [**材質**] 資料夾。 複製 **ButtonMaterial** 材質 (按下鍵盤上的 **Ctrl**  +  **D** ，或以滑鼠左鍵按一下 **材質**，然後從 [**編輯** 檔案] 功能表選項中，選取 [**複製**) 。

    ![第7章--設定兩個 Unity 場景 ](images/AzureLabs-Lab6-55.png)
     ![ 第7章--設定兩個 unity 場景](images/AzureLabs-Lab6-56.png)

16. 選取名為 **ButtonMaterial 1**) 的新 **ButtonMaterial** 材質 (，然後在 [偵測 **器**] 中，按一下 [ **>albedo** 色彩] 視窗。 快顯視窗隨即出現，您可以在其中選取另一種色彩 (選擇任何您喜歡的) ，然後關閉快顯視窗。 材質將會是自己的實例，而且不同于原始的實例。

    ![第7章--設定兩個 Unity 場景](images/AzureLabs-Lab6-57.png)

17. 將新的 **材質** 拖曳至 **GazeButton** 子系上，以完整更新其外觀，以便從第一個場景按鈕輕鬆地辨別。

    ![第7章--設定兩個 Unity 場景](images/AzureLabs-Lab6-58.png)

18. 至此，您可以在建立 UWP 專案之前，先在編輯器中測試專案。

    -  在 **編輯器** 中按下 [**播放**] 按鈕，並磨損您的耳機。

        ![第7章--設定兩個 Unity 場景](images/AzureLabs-Lab6-59.png)

19. 查看兩個 **GazeButton** 物件，以在第一和第二部影片之間切換。

## <a name="chapter-8---build-the-uwp-solution"></a>第8章-建立 UWP 解決方案

確定編輯器沒有任何錯誤之後，您就可以開始建立。

若要建立：

1.  按一下 [檔案] **> 儲存**]，以儲存目前的場景。

2.  核取稱為 **Unity C \# Projects** 的方塊 (這很重要，因為它可讓您在組建完成) 之後編輯類別。

3.  移至 [檔案 **> 組建] 設定** 中，按一下 [**組建**]。

4.  系統會提示您選取要在其中建立解決方案的資料夾。

5.  建立 **組建** 資料夾，然後在該資料夾內使用您選擇的適當名稱建立另一個資料夾。

6.  按一下新資料夾，然後按一下 [ **選取資料夾**]，選擇該資料夾，在該位置開始組建。

    ![第8章--建立 UWP 解決方案 ](images/AzureLabs-Lab6-60.png)
     ![ 第8章--建立 uwp 解決方案](images/AzureLabs-Lab6-61.png)

7.  Unity 完成組建之後 (可能需要一些時間) ，它會在您的組建位置開啟 **檔案總管** 視窗。

## <a name="chapter-9---deploy-on-local-machine"></a>第9章-在本機電腦上部署

組建完成後， **檔案總管** 視窗會出現在組建的位置。 開啟您命名和建立的資料夾，然後按兩下該資料夾內的方案 ( .sln) 檔案，以 Visual Studio 2017 開啟您的解決方案。

唯一要做的事，就是將您的應用程式部署到電腦 (或 *本機電腦*) 。

若要部署到本機電腦：

1.  在 **Visual Studio 2017** 中，開啟剛建立的方案檔。

2.  在 [ **方案平臺**] 中，選取 [ **x86]、[本機電腦**]。

3.  在 [ **方案** 設定] 中選取 [ **Debug**]。

    ![第9章--在本機電腦上部署](images/AzureLabs-Lab6-62.png)

4.  您現在需要將任何套件還原至您的解決方案。 以滑鼠右鍵按一下您的 **方案**，然後按一下 [**還原解決方案的 NuGet 套件**]。

    > [!NOTE] 
    > 這是因為 Unity 所建立的套件必須以您的本機電腦參考為目標。

5.  移至 [ **組建] 功能表** ，然後按一下 [ **部署方案** ]，將應用程式側載至您的電腦。 Visual Studio 將會先建立您的應用程式，然後再加以部署。

6.  您的應用程式現在應該會出現在已安裝的應用程式清單中，準備好要啟動。

    ![第9章--在本機電腦上部署](images/AzureLabs-Lab6-63.png)

當您執行混合現實應用程式時，您會在應用程式中使用的 **InsideOutSphere** 模型內。 此球體將是影片串流處理的位置，可提供 filmed 的內送影片的360度觀點， (這種) 的觀點。 如果影片需要幾秒鐘的時間才能載入，您的應用程式會受到您的可用網際網路速度的要求，因為影片需要先取出再下載，以串流至您的應用程式。
當您準備好時，請以紅色球體撥雲見日來變更場景，並開啟第二個影片！ 然後，您可以在第二個場景中使用藍色立方體來自由返回！

## <a name="your-finished-azure-media-service-application"></a>您已完成的 Azure 媒體服務應用程式
 
恭喜，您建立了一個混合現實應用程式，利用 Azure 媒體服務來串流360的影片。

![實驗室結果](images/AzureLabs-Lab6-00.png)

![實驗室結果](images/AzureLabs-Lab6-01.png)

## <a name="bonus-exercises"></a>額外練習

**練習 1**

您可以在本教學課程中，只使用單一場景來變更影片。 試驗您的應用程式，並使其進入單一場景！ 或許甚至可以將另一部影片新增至混合。

**練習 2**

使用 Azure 和 Unity 進行實驗，並嘗試執行應用程式自動選取不同檔案大小的影片，視網際網路連線的強度而定。