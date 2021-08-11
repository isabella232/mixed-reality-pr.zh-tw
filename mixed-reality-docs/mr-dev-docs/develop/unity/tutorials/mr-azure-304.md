---
title: HoloLens (第1代) 和 Azure 304-臉部辨識
description: 完成此課程以了解如何在混合實境應用程式中實作 Azure 臉部辨識。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure，mixed reality，學院，unity，教學課程，api，臉部辨識，hololens，沉浸，vr，Windows 10，Visual Studio
ms.openlocfilehash: 2547b61669884c524fdd605240322dc9d568039b5a202d0a411317b0e83bd547
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2021
ms.locfileid: "115219443"
---
# <a name="hololens-1st-gen-and-azure-304-face-recognition"></a>HoloLens (第1代) 和 Azure 304：臉部辨識

<br>

>[!NOTE]
>混合實境學院教學課程的設計是以 HoloLens (第 1 代) 和混合實境沉浸式頭戴裝置為準。  因此，對於仍在尋找這些裝置開發指引的開發人員而言，我們覺得這些教學課程很重要。  這些教學課程 **_不會_** 使用用於 HoloLens 2 的最新工具組或互動進行更新。  系統會保留這些資訊，以繼續在支援的裝置上運作。 未來將會有一系列新的教學課程，將會示範如何針對 HoloLens 2 進行開發。  當張貼這些教學課程時，將會使用這些教學課程的連結來更新此通知。

<br>

![完成本課程的結果](images/AzureLabs-Lab4-00.png)

在此課程中，您將瞭解如何使用 Azure 認知服務搭配 Microsoft 臉部 API，將臉部辨識功能新增至混合現實應用程式。

*Azure 臉部 API* 是一項 Microsoft 服務，可為開發人員提供最先進的臉部演算法，全都在雲端中。 *臉部 API* 有兩個主要功能：使用屬性進行臉部偵測，以及臉部辨識。 這可讓開發人員只為臉部設定一組群組，然後在稍後將查詢影像傳送至服務，以判斷臉部所屬的人。 如需詳細資訊，請造訪 [Azure 臉部辨識頁面](https://azure.microsoft.com/services/cognitive-services/face/)。

完成本課程之後，您將會有 HoloLens 應用程式的混合現實，這將能夠執行下列作業：

1. 使用點一下 **手勢**，利用 HoloLens 攝影機來起始影像的捕獲。 
2. 將已捕獲的映射傳送至 *Azure 臉部 API* 服務。
3. 接收 *臉部 API* 演算法的結果。
4. 使用簡單的消費者介面，以顯示相符人員的名稱。

這將告訴您如何將臉部 API 服務的結果取得至 Unity 型混合現實應用程式。

在您的應用程式中，您可以自行決定如何將結果與您的設計整合。 本課程旨在告訴您如何將 Azure 服務與 Unity Project 整合。 您的工作是使用您在本課程中所得到的知識，來增強您的混合現實應用程式。

## <a name="device-support"></a>裝置支援

<table>
<tr>
<th>課程</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">沉浸式頭戴裝置</a></th>
</tr><tr>
<td> MR 和 Azure 304：臉部辨識</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> 雖然本課程主要著重于 HoloLens，但您也可以在本課程中套用您學到的內容，以 Windows Mixed Reality 沉浸式 (VR) 耳機。 因為沉浸式 (VR) 耳機沒有可存取的攝影機，所以您需要有連接到電腦的外部攝影機。 當您依照課程的指示，您將會看到有關您可能需要採用以支援沉浸式 (VR) 耳機的任何變更的注意事項。

## <a name="prerequisites"></a>必要條件

> [!NOTE]
> 本教學課程是專為擁有 Unity 和 c # 基本經驗的開發人員所設計。 另外也請注意，本檔中的必要條件和撰寫的指示，代表在撰寫 (可能是 2018) 時經過測試和驗證的內容。 You are free to use the latest software, as listed within the [install the tools](../../install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.

本課程建議您採用下列硬體和軟體：

- 開發電腦，與適用于沉浸式 (VR) 耳機開發的[Windows Mixed Reality 相容](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines)
- [啟用開發人員模式的 Windows 10 Fall Creators Update (或更新版本) ](../../install-the-tools.md)
- [最新的 Windows 10 SDK](../../install-the-tools.md)
- [Unity 2017。4](../../install-the-tools.md)
- [Visual Studio 2017](../../install-the-tools.md)
- [Windows Mixed Reality 沉浸式 (VR) 耳機](../../../discover/immersive-headset-hardware-details.md)，或已啟用開發人員模式的[Microsoft HoloLens](/hololens/hololens1-hardware)
- 連接到您 PC (的攝影機，適用于沉浸式耳機開發) 
- 適用于 Azure 安裝程式和臉部 API 抓取的網際網路存取

## <a name="before-you-start"></a>在您開始使用 Intune 之前

1.  為了避免在建立此專案時發生問題，強烈建議您在根或近端根資料夾中，建立本教學課程中所述的專案 (長的資料夾路徑可能會在組建階段) 時發生問題。
2.  設定及測試您的 HoloLens。 如果您需要設定 HoloLens 的支援，[請務必造訪 HoloLens 安裝程式文章](/hololens/hololens-setup)。 
3.  在開始開發新的 HoloLens 應用程式時，最好先執行校正和感應器調整， (有時它可以協助您為每個使用者) 執行這些工作。 

如需有關校正的說明，請遵循此[連結來 HoloLens 校正文章](/hololens/hololens-calibration#hololens-2)。

如需有關感應器微調的說明，請依照此[連結前往 HoloLens 感應器微調文章](/hololens/hololens-updates)。

## <a name="chapter-1---the-azure-portal"></a>第1章-Azure 入口網站

若要在 Azure 中使用 *臉部 API* 服務，您必須將服務的實例設定為可供應用程式使用。

1.  首先，登入 [Azure 入口網站](https://portal.azure.com)。 

    > [!NOTE]
    > 如果您還沒有 Azure 帳戶，您將需要建立一個帳戶。 如果您在課堂或實驗室的情況下進行本教學課程，請洽詢講師或其中一個 proctors，協助您設定新的帳戶。

2.  登入後，按一下左上角的 [ **新增** ]，然後搜尋 *臉部 API*，按 **enter**。

    ![搜尋臉部 api](images/AzureLabs-Lab4-01.png)

    > [!NOTE]
    > 在較新的入口網站中，[**建立資源**] 可能已取代 **新** 的文字。

3.  新頁面將提供 *臉部 API* 服務的描述。 在此提示的左下方，選取 [ **建立** ] 按鈕，以建立與此服務的關聯。

    ![臉部 api 資訊](images/AzureLabs-Lab4-02.png)

4.  當您按一下 [ **建立**] 之後：

    1. 為此服務實例插入您想要的名稱。

    2. 選取一個訂用帳戶。

    3. 選取適合您的定價層，如果這是您第一次建立 *臉部 API 服務*，則應可使用名為 F0) 的免費層 (。

    4. 選擇資源群組，或建立一個新的 **資源群組** 。 資源群組提供一種方式來監視、控制存取、布建及管理 Azure 資產集合的計費。 建議您保留與單一專案相關聯的所有 Azure 服務 (例如，) 一般資源群組下的實驗室，) 。 

        > 如果您想要閱讀更多有關 Azure 資源群組的資訊，請 [造訪資源群組文章](/azure/azure-resource-manager/resource-group-portal)。

    5. 您稍後使用的 UWP 應用程式（ **Person Maker**）需要使用「美國西部」作為位置。

    6. 您也必須確認您已瞭解套用到此服務的條款及條件。

    7. 選取 [ **建立 *]。**

        ![建立臉部 api 服務](images/AzureLabs-Lab4-03.png)

5.  按一下 [ **建立] * 之後，** 您必須等候服務建立完成，這可能需要一分鐘的時間。

6.  建立服務實例之後，入口網站中就會出現通知。

    ![服務建立通知](images/AzureLabs-Lab4-04.png)

7.  按一下通知以探索新的服務實例。

    ![前往資源通知](images/AzureLabs-Lab4-05.png)

8.  當您準備好時，請按一下通知中的 [ **移至資源** ] 按鈕，以探索新的服務實例。

    ![存取臉部 api 金鑰](images/AzureLabs-Lab4-06.png)

9.  在本教學課程中，您的應用程式必須呼叫您的服務，這是透過使用您服務的訂用帳戶「金鑰」來完成。 從您 *臉部 API* 服務的 [*快速入門*] 頁面中，第一個點是編號1，以 *抓取您的金鑰。*

10. 在 [ *服務* ] 頁面上，選取 [快速入門] 頁面上的 [藍色 **按鍵** ] 超連結 (如果) ，或 (左邊的 [服務] 導覽功能表中的 [ **金鑰** ] 連結) ，則會顯示您的金鑰。

    > [!NOTE] 
    > 請記下其中一個金鑰並加以保護，因為您稍後將會用到。

## <a name="chapter-2---using-the-person-maker-uwp-application"></a>第2章-使用「Person Maker」 UWP 應用程式

請務必下載稱為 [Person Maker](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/PersonMaker.zip)的預建 UWP 應用程式。 此應用程式不是此課程的結束產品，只是協助您建立 Azure 專案的工具，稍後的專案將會依賴此工具。

**Person Maker** 可讓您建立與人員和人員群組相關聯的 Azure 專案。 應用程式會將所有必要的資訊都放在稍後供 FaceAPI 使用的格式中，以便辨識您已新增的人員臉部。 

> 須知 **Person Maker** 會使用一些基本的節流，以協助確保您不會超過 **免費訂** 用帳戶層的每分鐘服務呼叫數目。 當節流發生時，頂端的綠色文字會變更為紅色，並更新為「作用中」。如果發生這種情況，只要等候應用程式 (它就會等到它可以繼續存取臉部辨識服務，然後在) 時更新為「主動」。

此應用程式會使用 *>microsoft.projectoxford.face* 程式庫，可讓您充分利用臉部 API。 此程式庫可免費作為 NuGet 套件。 如需此程式和類似 Api 的詳細資訊， [請務必造訪 api 參考文章](/azure/cognitive-services/face/apireference)。

> [!NOTE] 
> 這些只是所需的步驟，也就是如何執行這些作業的指示。 **Person Maker** 應用程式可讓您：
>
> - 建立 *人員群組*，此群組是由數個您想要與其相關聯的人員所組成。 使用您的 Azure 帳戶，您可以裝載多個人員群組。
>
> - 建立 *person*，這是 person 群組的成員。 每個人都有許多相關聯的 *臉部* 影像。
>
> -  將 *臉部影像* 指派給 *人員*，以允許您的 Azure 臉部 API 服務依據對應的 *臉部* 辨識 *人員*。
>
> -  *訓練* 您的 *Azure 臉部 API 服務*。

請注意，若要將此應用程式定型以辨識人員，您將需要 10 (10) 您想要新增至人員群組的每個人的近接相片。 Windows 10 凸輪應用程式可協助您進行這些工作。 您必須確保每個相片都清楚明瞭 (避免模糊、遮蔽或太遠，從主題) ，以 jpg 或 png 檔案格式的相片，而且影像檔案的大小不會超過 **4 MB**，而且不小於 **1 KB**。

> [!NOTE]
> 如果您遵循本教學課程，請勿使用您自己的臉部進行訓練，如同當您將 HoloLens 開啟時，您無法自行查看。 使用同事或學生的臉部。

正在執行 **Person Maker**：

1.  開啟 [ **PersonMaker** ] 資料夾，然後按兩下 [ *PersonMaker] 方案*，以 *Visual Studio* 開啟該資料夾。

2.  *PersonMaker 解決方案* 開啟後，請確定：

    1. *解決方案* 設定會設定為 **Debug**。

    2. *解決方案平臺* 設定為 **x86**

    3. *目標平臺* 是 **本機電腦**。

    4.  您也可能需要 *還原 NuGet 套件* (以滑鼠右鍵按一下 *方案*，然後選取 [**還原 NuGet 封裝**]) 。

3.  按一下 [ *本機電腦* ]，應用程式就會啟動。 請注意，在較小的螢幕上，所有內容都可能無法顯示，不過您可以進一步向下移動以查看。

    ![person maker 使用者介面](images/AzureLabs-Lab4-07.png)

4.  從 Azure 內的 *臉部 API* 服務插入您的 **azure 驗證金鑰**。

5.  插入：

    1. 您要指派給 *Person 群組* 的 *識別碼*。 識別碼必須是小寫，而且沒有空格。 請記下此識別碼，因為稍後會在您的 Unity 專案中需要此識別碼。
    2. 您要指派給 *Person 群組* (的 *名稱* 可以有空格) 。


6.  按下 [ **建立人員群組** ] 按鈕。 確認訊息應該會出現在按鈕下方。

> [!NOTE]
> 如果您有「拒絕存取」錯誤，請檢查您為 Azure 服務設定的位置。 如上所述，此應用程式是針對「美國西部」所設計。

> [!IMPORTANT]
> 您將會注意到，您也可以按一下 [ **提取已知的群組** ] 按鈕：如果您已經建立人員群組，且想要使用該群組，而不是建立新的群組，您也可以使用此按鈕。 請注意，如果您按一下 [建立具有已知群組的 *人員群組* ]，這也會提取群組。

7.  插入您想要建立之 *人員* 的 *名稱*。

    1. 按一下 [ **建立人員** ] 按鈕。

    2. 確認訊息應該會出現在按鈕下方。

    3. 如果您想要刪除先前建立的人員，可以將名稱寫入文字方塊中，然後按 [**刪除人員**]

8.  確定您知道想要新增至群組之人員的 10 (10) 相片的位置。

9.  按下 [**建立] 和 [開啟資料夾**] 以開啟與該人員相關聯之資料夾的 Windows 檔案總管。 將 10 (10) 影像新增至資料夾。 這些必須是 *JPG* 或 *PNG* 檔案格式。

10. 按一下 [ **提交至 Azure**]。 計數器會顯示提交的狀態，後面接著訊息完成時的訊息。

11. 一旦計數器完成，並顯示確認訊息，請按一下 [ **定型** ] 以定型您的服務。

程式完成之後，您就可以開始移至 Unity。

## <a name="chapter-3---set-up-the-unity-project"></a>第3章-設定 Unity 專案

以下是使用 mixed reality 進行開發的一般設定，因此，它是適用于其他專案的絕佳範本。

1.  開啟 *Unity* ，然後按一下 [ **新增**]。 

    ![開始新的 Unity 專案。](images/AzureLabs-Lab4-08.png)

2.  現在您將需要提供 Unity Project 名稱。 插入 **MR_FaceRecognition**。 請確定專案類型設定為 **3d**。 將 **位置** 設定為適合您 (記住，較接近根目錄的) 。 然後，按一下 [ **建立專案**]。

    ![提供新 Unity 專案的詳細資料。](images/AzureLabs-Lab4-09.png)

3.  在 Unity 開啟的情況下，值得檢查預設 **腳本編輯器** 是否設定為 **Visual Studio**。 移至 [ **編輯] > 喜好** 設定，然後在新視窗中，流覽至 [ **外部工具**]。 將 **外部腳本編輯器** 變更為 **Visual Studio 2017**。 關閉 [ **喜好** 設定] 視窗。

    ![更新腳本編輯器喜好設定。](images/AzureLabs-Lab4-10.png)

4.  接下來，移至 [檔案 **> 建立設定**]，然後按一下 [**切換平臺**] 按鈕，將平臺切換至 **通用 Windows 平臺**。

    ![建立設定視窗、將平臺切換至 UWP。](images/AzureLabs-Lab4-11.png)

5.  移至 [檔案 **> 組建設定** 並確定：

    1. **目標裝置** 設定為 **HoloLens**

        > 針對沉浸式耳機，將 **目標裝置** 設為 *任何裝置*。

    2. **組建類型** 設定為 **D3D**
    3. **SDK** 已設定為 **最新安裝**
    4. **Visual Studio 版本** 設定為 **最新安裝**
    5. **組建並執行** 設定為 **本機電腦**
    6. 儲存場景，並將其新增至組建。 

        1. 若要這麼做，請選取 [ **新增開啟的場景**]。 [儲存] 視窗隨即出現。

            ![按一下 [新增開啟場景] 按鈕](images/AzureLabs-Lab4-12.png)

        2. 選取 [ **新增資料夾** ] 按鈕，建立新的資料夾，將它命名為 **場景**。

            ![建立新的腳本資料夾](images/AzureLabs-Lab4-13.png)

        3. 開啟新建立的 **場景** 資料夾，然後在 [ **檔案名**：文字] 欄位中輸入 **FaceRecScene**，然後按 [ **儲存**]。

            ![提供新場景的名稱。](images/AzureLabs-Lab4-14.png)

    7. [*組建設定*] 中的其餘設定，現在應該保持為預設值。

6. 在 [*組建設定*] 視窗中，按一下 [播放程式]**設定** 按鈕，這會開啟偵測 *器* 所在空間中的相關面板。 

    ![開啟 [播放玩家設定]。](images/AzureLabs-Lab4-15.png)

7. 在此面板中，需要驗證幾個設定：

    1. 在 [**其他設定**] 索引標籤中：

        1. **腳本****執行階段版本** 應該是 **實驗** ( .net 4.6 對等) 。 變更此變更將會觸發重新開機編輯器的需求。
        2. **腳本後端** 應該是 **.net**
        3. **API 相容性層級** 應為 **.net 4.6**

            ![更新其他設定。](images/AzureLabs-Lab4-16.png)
      
    2. 在 [**發行設定**] 索引標籤的 [**功能**] 下，選取：

        - **InternetClient**
        - **網路攝影機**

            ![正在更新發行設定。](images/AzureLabs-Lab4-17.png)

    3. 接下來的面板中，在 **XR 設定** (的 [**發佈設定**) ]、[滴答 **虛擬實境支援**]，請確定已新增 **Windows Mixed Reality SDK** 。

        ![更新 X R 設定。](images/AzureLabs-Lab4-18.png)

8.  回到 *Build 設定*， **Unity c # 專案** 不再呈現灰色;勾選此方塊旁邊的核取方塊。 
9.  關閉 [建置設定] 視窗。
10. 儲存場景並 Project (檔 **> 儲存場景/檔案 > 儲存專案**) 。

## <a name="chapter-4---main-camera-setup"></a>第4章-主要攝影機設定

> [!IMPORTANT]
> 如果您想要略過此課程的 *Unity 設定* 元件，並直接繼續進行程式碼，請隨意 [下載 unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/Azure-MR-304.unitypackage)，並將它匯入至您的專案中做為 [自訂套件](https://docs.unity3d.com/Manual/AssetPackages.html)。 請注意，此套件也包含 *NEWTONSOFT DLL* 的匯入，如 [第5章](#chapter-5--import-the-newtonsoftjson-library)所述。 匯入之後，您可以從 [第6章](#chapter-6---create-the-faceanalysis-class)繼續。

1.  *在 [階層] 面板中*，選取 [**主要相機**]。

2.  一旦選取之後，您就可以在 [偵測 *器] 面板* 中看到 **主要攝影機** 的所有元件。

    1. **攝影機物件** 必須命名為 **主要攝影機** (請注意拼寫！ ) 

    2. 主要攝影機 **標記** 必須設定為 **MainCamera** (注意拼寫！ ) 

    3. 請確定 **轉換位置** 設定為 **0、0、0**

    4. 將純文字 **旗標** 設為 **純色**

    5. 將相機元件的 **背景** 色彩設定為 **黑色、Alpha 0 (Hex 碼： #00000000)**

        ![設定攝影機元件](images/AzureLabs-Lab4-19.png) 

## <a name="chapter-5--import-the-newtonsoftjson-library"></a>第5章–匯入程式庫上的 Newtonsoft.Js

> [!IMPORTANT]
> 如果您在 [上一章](#chapter-4---main-camera-setup)匯入了 '. unitypackage '，您可以跳過這一章。

為了協助您還原序列化和序列化接收和傳送至 Bot 服務的物件，您需要下載程式庫 *上的Newtonsoft.Js* 。 您會在此 [Unity 套件](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/newtonsoftDLL.unitypackage)檔案中找到已使用正確 unity 資料夾結構組織的相容版本。 

匯入程式庫：

1.  下載 Unity 套件。
2.  按一下 [ **資產**]、[匯 **入封裝**]、[ **自訂套件**]。

    ![匯入 Newtonsoft.Js開啟](images/AzureLabs-Lab4-20.png)

3.  尋找您已下載的 Unity 套件，然後按一下 [開啟]。
4.  請確定封裝的所有元件都是核取，然後按一下 [匯 **入**]。

    ![匯入資產上的 Newtonsoft.Js](images/AzureLabs-Lab4-21.png)

## <a name="chapter-6---create-the-faceanalysis-class"></a>第6章-建立 FaceAnalysis 類別

FaceAnalysis 類別的目的是裝載與您的 Azure 臉部辨識服務通訊所需的方法。 

- 將服務傳送至 capture 映射之後，它會分析並識別其中的臉部，並判斷是否有任何人屬於已知人員。 
- 如果找到已知人員，這個類別會將其名稱顯示為場景中的 UI 文字。

若要建立 *FaceAnalysis* 類別：

 1. 在位於 Project 面板中的 [*資產] 資料夾* 上按一下滑鼠右鍵，然後按一下 [**建立**  >  **資料夾**]。 呼叫資料夾 **腳本**。 

    ![建立 FaceAnalysis 類別。](images/AzureLabs-Lab4-22.png)

2.  按兩下剛才建立的資料夾，將它開啟。 
3.  在資料夾內按一下滑鼠右鍵，然後按一下 [**建立**  >  **c # 腳本**]。 呼叫腳本 *FaceAnalysis*。 
4.  按兩下新的 *FaceAnalysis* 腳本，以 Visual Studio 2017 開啟。
5.  在 *FaceAnalysis* 類別上方輸入下列命名空間：

    ```csharp
        using Newtonsoft.Json;
        using System.Collections;
        using System.Collections.Generic;
        using System.IO;
        using System.Text;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

6.  您現在需要新增 deserialising 所使用的所有物件。 這些物件必須加入至 *FaceAnalysis* 腳本 **之外**， (在下大括弧) 下。 

    ```csharp
        /// <summary>
        /// The Person Group object
        /// </summary>
        public class Group_RootObject
        {
            public string personGroupId { get; set; }
            public string name { get; set; }
            public object userData { get; set; }
        }

        /// <summary>
        /// The Person Face object
        /// </summary>
        public class Face_RootObject
        {
            public string faceId { get; set; }
        }

        /// <summary>
        /// Collection of faces that needs to be identified
        /// </summary>
        public class FacesToIdentify_RootObject
        {
            public string personGroupId { get; set; }
            public List<string> faceIds { get; set; }
            public int maxNumOfCandidatesReturned { get; set; }
            public double confidenceThreshold { get; set; }
        }

        /// <summary>
        /// Collection of Candidates for the face
        /// </summary>
        public class Candidate_RootObject
        {
            public string faceId { get; set; }
            public List<Candidate> candidates { get; set; }
        }

        public class Candidate
        {
            public string personId { get; set; }
            public double confidence { get; set; }
        }

        /// <summary>
        /// Name and Id of the identified Person
        /// </summary>
        public class IdentifiedPerson_RootObject
        {
            public string personId { get; set; }
            public string name { get; set; }
        }
    ```
7. [ *開始 ()* ] 和 [ *更新 ()* ] 方法將不會使用，因此請立即將其刪除。 

8.  在 *FaceAnalysis* 類別中，新增下列變數：

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static FaceAnalysis Instance;

        /// <summary>
        /// The analysis result text
        /// </summary>
        private TextMesh labelText;

        /// <summary>
        /// Bytes of the image captured with camera
        /// </summary>
        internal byte[] imageBytes;

        /// <summary>
        /// Path of the image captured with camera
        /// </summary>
        internal string imagePath;

        /// <summary>
        /// Base endpoint of Face Recognition Service
        /// </summary>
        const string baseEndpoint = "https://westus.api.cognitive.microsoft.com/face/v1.0/";

        /// <summary>
        /// Auth key of Face Recognition Service
        /// </summary>
        private const string key = "- Insert your key here -";

        /// <summary>
        /// Id (name) of the created person group 
        /// </summary>
        private const string personGroupId = "- Insert your group Id here -";
    ```

    > [!NOTE]
    > 將 **金鑰** 和 **personGroupId** 取代為您的服務金鑰，以及您先前建立之群組的識別碼。

9.  新增 *喚醒的 ()* 方法，initialises 類別、將 *ImageCapture* 類別新增至主要相機，並呼叫標籤建立方法：

    ```csharp
        /// <summary>
        /// Initialises this class
        /// </summary>
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            Instance = this;

            // Add the ImageCapture Class to this Game Object
            gameObject.AddComponent<ImageCapture>();

            // Create the text label in the scene
            CreateLabel();
        }
    ```

10. 新增 *CreateLabel ()* 方法，它會建立 *標籤* 物件來顯示分析結果：

    ```csharp
        /// <summary>
        /// Spawns cursor for the Main Camera
        /// </summary>
        private void CreateLabel()
        {
            // Create a sphere as new cursor
            GameObject newLabel = new GameObject();

            // Attach the label to the Main Camera
            newLabel.transform.parent = gameObject.transform;
            
            // Resize and position the new cursor
            newLabel.transform.localScale = new Vector3(0.4f, 0.4f, 0.4f);
            newLabel.transform.position = new Vector3(0f, 3f, 60f);

            // Creating the text of the Label
            labelText = newLabel.AddComponent<TextMesh>();
            labelText.anchor = TextAnchor.MiddleCenter;
            labelText.alignment = TextAlignment.Center;
            labelText.tabSize = 4;
            labelText.fontSize = 50;
            labelText.text = ".";       
        }
    ```

11. 新增 *DetectFacesFromImage ()* 和 *GetImageAsByteArray ()* 方法。 前者會要求臉部辨識服務偵測提交影像中的任何可能臉部，而後者則是將捕獲的影像轉換成位元組陣列的必要條件：

    ```csharp
        /// <summary>
        /// Detect faces from a submitted image
        /// </summary>
        internal IEnumerator DetectFacesFromImage()
        {
            WWWForm webForm = new WWWForm();
            string detectFacesEndpoint = $"{baseEndpoint}detect";

            // Change the image into a bytes array
            imageBytes = GetImageAsByteArray(imagePath);

            using (UnityWebRequest www = 
                UnityWebRequest.Post(detectFacesEndpoint, webForm))
            {
                www.SetRequestHeader("Ocp-Apim-Subscription-Key", key);
                www.SetRequestHeader("Content-Type", "application/octet-stream");
                www.uploadHandler.contentType = "application/octet-stream";
                www.uploadHandler = new UploadHandlerRaw(imageBytes);
                www.downloadHandler = new DownloadHandlerBuffer();

                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;
                Face_RootObject[] face_RootObject = 
                    JsonConvert.DeserializeObject<Face_RootObject[]>(jsonResponse);

                List<string> facesIdList = new List<string>();
                // Create a list with the face Ids of faces detected in image
                foreach (Face_RootObject faceRO in face_RootObject)
                {
                    facesIdList.Add(faceRO.faceId);
                    Debug.Log($"Detected face - Id: {faceRO.faceId}");
                }
                
                StartCoroutine(IdentifyFaces(facesIdList));
            }
        }

        /// <summary>
        /// Returns the contents of the specified file as a byte array.
        /// </summary>
        static byte[] GetImageAsByteArray(string imageFilePath)
        {
            FileStream fileStream = new FileStream(imageFilePath, FileMode.Open, FileAccess.Read);
            BinaryReader binaryReader = new BinaryReader(fileStream);
            return binaryReader.ReadBytes((int)fileStream.Length);
        }
    ```

12. 新增 *IdentifyFaces ()* 方法，這會要求 *臉部辨識服務* 識別先前在提交的影像中偵測到的任何已知臉部。 要求會傳回已識別之人員的識別碼，但不會傳回名稱：

    ```csharp
        /// <summary>
        /// Identify the faces found in the image within the person group
        /// </summary>
        internal IEnumerator IdentifyFaces(List<string> listOfFacesIdToIdentify)
        {
            // Create the object hosting the faces to identify
            FacesToIdentify_RootObject facesToIdentify = new FacesToIdentify_RootObject();
            facesToIdentify.faceIds = new List<string>();
            facesToIdentify.personGroupId = personGroupId;
            foreach (string facesId in listOfFacesIdToIdentify)
            {
                facesToIdentify.faceIds.Add(facesId);
            }
            facesToIdentify.maxNumOfCandidatesReturned = 1;
            facesToIdentify.confidenceThreshold = 0.5;

            // Serialize to Json format
            string facesToIdentifyJson = JsonConvert.SerializeObject(facesToIdentify);
            // Change the object into a bytes array
            byte[] facesData = Encoding.UTF8.GetBytes(facesToIdentifyJson);

            WWWForm webForm = new WWWForm();
            string detectFacesEndpoint = $"{baseEndpoint}identify";

            using (UnityWebRequest www = UnityWebRequest.Post(detectFacesEndpoint, webForm))
            {
                www.SetRequestHeader("Ocp-Apim-Subscription-Key", key);
                www.SetRequestHeader("Content-Type", "application/json");
                www.uploadHandler.contentType = "application/json";
                www.uploadHandler = new UploadHandlerRaw(facesData);
                www.downloadHandler = new DownloadHandlerBuffer();

                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;
                Debug.Log($"Get Person - jsonResponse: {jsonResponse}");
                Candidate_RootObject [] candidate_RootObject = JsonConvert.DeserializeObject<Candidate_RootObject[]>(jsonResponse);

                // For each face to identify that ahs been submitted, display its candidate
                foreach (Candidate_RootObject candidateRO in candidate_RootObject)
                {
                    StartCoroutine(GetPerson(candidateRO.candidates[0].personId));
                    
                    // Delay the next "GetPerson" call, so all faces candidate are displayed properly
                    yield return new WaitForSeconds(3);
                }           
            }
        }
    ```

13. 新增 *GetPerson ()* 方法。 藉由提供人員識別碼，此方法接著會要求 *臉部辨識服務* 傳回已識別人員的名稱：

    ```csharp
        /// <summary>
        /// Provided a personId, retrieve the person name associated with it
        /// </summary>
        internal IEnumerator GetPerson(string personId)
        {
            string getGroupEndpoint = $"{baseEndpoint}persongroups/{personGroupId}/persons/{personId}?";
            WWWForm webForm = new WWWForm();

            using (UnityWebRequest www = UnityWebRequest.Get(getGroupEndpoint))
            {
                www.SetRequestHeader("Ocp-Apim-Subscription-Key", key);
                www.downloadHandler = new DownloadHandlerBuffer();
                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;

                Debug.Log($"Get Person - jsonResponse: {jsonResponse}");
                IdentifiedPerson_RootObject identifiedPerson_RootObject = JsonConvert.DeserializeObject<IdentifiedPerson_RootObject>(jsonResponse);

                // Display the name of the person in the UI
                labelText.text = identifiedPerson_RootObject.name;
            }
        }
    ```

14.  請記得先 **儲存** 變更，然後再返回 Unity 編輯器。
15.  在 Unity 編輯器中，將 FaceAnalysis 腳本從 Project 面板中的 [腳本] 資料夾，拖曳至 [階層]*面板* 中的 [主要攝影機] 物件。 新的腳本元件將會新增到主要攝影機中。 

![將 FaceAnalysis 放在主要攝影機上](images/AzureLabs-Lab4-23.png)


## <a name="chapter-7---create-the-imagecapture-class"></a>第7章-建立 ImageCapture 類別

*ImageCapture* 類別的目的是裝載與您的 *Azure 臉部辨識服務* 通訊所需的方法，以分析您將會捕捉的影像、識別其中的臉部，並判斷它是否屬於已知人員。 如果找到已知人員，這個類別會將其名稱顯示為場景中的 UI 文字。

若要建立 *ImageCapture* 類別：
 
1.  以滑鼠右鍵按一下您先前建立的 **腳本** 資料夾內部，然後按一下 [ **建立**]、[ **c # 腳本**]。 呼叫腳本 *ImageCapture*。 
2.  按兩下新的 *ImageCapture* 腳本，以 Visual Studio 2017 開啟。
3.  在 ImageCapture 類別上方輸入下列命名空間：

    ```csharp
        using System.IO;
        using System.Linq;
        using UnityEngine;
        using UnityEngine.XR.WSA.Input;
        using UnityEngine.XR.WSA.WebCam;
    ```

4.  在 *ImageCapture* 類別中，新增下列變數：

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static ImageCapture instance;

        /// <summary>
        /// Keeps track of tapCounts to name the captured images 
        /// </summary>
        private int tapsCount;

        /// <summary>
        /// PhotoCapture object used to capture images on HoloLens 
        /// </summary>
        private PhotoCapture photoCaptureObject = null;

        /// <summary>
        /// HoloLens class to capture user gestures
        /// </summary>
        private GestureRecognizer recognizer;
    ```

5.  新增 *喚醒的 ()* ，並啟動初始化類別所需的 *()* 方法，並允許 HoloLens 捕捉使用者的手勢：

    ```csharp
        /// <summary>
        /// Initialises this class
        /// </summary>
        private void Awake()
        {
            instance = this;
        }

        /// <summary>
        /// Called right after Awake
        /// </summary>
        void Start()
        {
            // Initialises user gestures capture 
            recognizer = new GestureRecognizer();
            recognizer.SetRecognizableGestures(GestureSettings.Tap);
            recognizer.Tapped += TapHandler;
            recognizer.StartCapturingGestures();
        }
    ```

6.  新增 *TapHandler ()* ，這會在使用者執行點 *按手勢時* 呼叫：

    ```csharp
        /// <summary>
        /// Respond to Tap Input.
        /// </summary>
        private void TapHandler(TappedEventArgs obj)
        {
            tapsCount++;
            ExecuteImageCaptureAndAnalysis();
        }
    ```

7.  新增 *ExecuteImageCaptureAndAnalysis ()* 方法，這將會開始進行映射捕獲：

    ```csharp
        /// <summary>
        /// Begin process of Image Capturing and send To Azure Computer Vision service.
        /// </summary>
        private void ExecuteImageCaptureAndAnalysis()
        {
            Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending
                ((res) => res.width * res.height).First();
            Texture2D targetTexture = new Texture2D(cameraResolution.width, cameraResolution.height);

            PhotoCapture.CreateAsync(false, delegate (PhotoCapture captureObject)
            {
                photoCaptureObject = captureObject;

                CameraParameters c = new CameraParameters();
                c.hologramOpacity = 0.0f;
                c.cameraResolutionWidth = targetTexture.width;
                c.cameraResolutionHeight = targetTexture.height;
                c.pixelFormat = CapturePixelFormat.BGRA32;

                captureObject.StartPhotoModeAsync(c, delegate (PhotoCapture.PhotoCaptureResult result)
                {
                    string filename = string.Format(@"CapturedImage{0}.jpg", tapsCount);
                    string filePath = Path.Combine(Application.persistentDataPath, filename);

                    // Set the image path on the FaceAnalysis class
                    FaceAnalysis.Instance.imagePath = filePath;

                    photoCaptureObject.TakePhotoAsync
                    (filePath, PhotoCaptureFileOutputFormat.JPG, OnCapturedPhotoToDisk);
                });
            });
        }
    ```

8.  新增在完成相片抓取程式時所呼叫的處理常式：

    ```csharp
        /// <summary>
        /// Called right after the photo capture process has concluded
        /// </summary>
        void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
        {
            photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
        }

        /// <summary>
        /// Register the full execution of the Photo Capture. If successful, it will begin the Image Analysis process.
        /// </summary>
        void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
        {
            photoCaptureObject.Dispose();
            photoCaptureObject = null;

            // Request image caputer analysis
            StartCoroutine(FaceAnalysis.Instance.DetectFacesFromImage());
        }
    ```

9. 請記得先 **儲存** 變更，然後再返回 Unity 編輯器。

## <a name="chapter-8---building-the-solution"></a>第8章-建立解決方案

若要執行應用程式的完整測試，您必須將它側載到您的 HoloLens。

在執行之前，請確定：

-   第3章中所述的所有設定都已正確設定。 
-   腳本 *FaceAnalysis* 會附加至主要攝影機物件。 
-   **驗證金鑰** 和 **群組識別碼** 都是在 *FaceAnalysis* 腳本中設定。

答：現在您已準備好建立解決方案。 一旦建立解決方案之後，您就可以開始部署應用程式。

若要開始建立程式：

1.  按一下 [檔案]、[儲存]，以儲存目前的場景。
2.  移至 [檔案]、[建立設定]，然後按一下 [新增開啟的場景]。
3.  請務必勾選 Unity c # 專案。

    ![部署 Visual Studio 解決方案](images/AzureLabs-Lab4-24.png)

4.  按下 [建立]。 當您這樣做時，Unity 將會啟動一個檔案總管視窗，您需要在其中建立並選取要用來建立應用程式的資料夾。 立即在 Unity 專案中建立該資料夾，並呼叫它應用程式。 然後選取 [應用程式] 資料夾，然後按 [選取資料夾]。 
5.  Unity 將會開始建立您的專案，並將其移至應用程式資料夾。 
6.  Unity 完成組建之後 (可能需要一些時間) ，它會在您的組建位置開啟檔案總管視窗。

    ![從 Visual Studio 部署解決方案](images/AzureLabs-Lab4-25.png)

7.  開啟您的應用程式資料夾，然後開啟新的 Project 方案 (如上所示，MR_FaceRecognition .sln) 。


## <a name="chapter-9---deploying-your-application"></a>第9章-部署應用程式

若要在 HoloLens 上部署：

1.  您需要 HoloLens (的 IP 位址，才能進行遠端部署) ，並確保您的 HoloLens 處於 **開發人員模式**。 若要這樣做：

    1. 在 HoloLens 時，請開啟 **設定**。
    2. 前往 **Network & Internet > Wi-Fi > Advanced Options**
    3. 記下 **IPv4** 位址。
    4. 接下來，流覽回到 **設定**，然後為 **開發人員更新 & 安全性 >** 
    5. 設定 [開發人員模式]。

2.  流覽至您的新 Unity 組建 (*應用程式* 資料夾) ，然後以 *Visual Studio* 開啟方案檔。
3.  在 [方案設定] 中選取 [ **Debug**]。
4.  在解決方案平臺中，選取 [ **x86**]、[ **遠端電腦**]。 

    ![變更解決方案設定](images/AzureLabs-Lab4-26.png)
 
5.  移至 [**組建] 功能表**，然後按一下 [**部署方案**]，將應用程式側載到您的 HoloLens。
6.  您的應用程式現在應該會出現在您 HoloLens 上已安裝的應用程式清單中，準備好可供啟動！

> [!NOTE]
> 若要部署到沉浸式耳機，請將 **解決方案平臺****設定為 [** *本機電腦*]，並將 [設定] 設定為 [以 *x86* 作為 **平臺**] 來進行 *Debug*。 然後使用 [ **組建] 功能表** 選取 [ *部署方案*]，部署到本機電腦。 


## <a name="chapter-10---using-the-application"></a>第10章-使用應用程式

1.  戴 HoloLens，啟動應用程式。
2.  查看您向 *臉部 API* 註冊的人員。 請務必達成以下事項：

    -  人物的臉部不太遠，而且看得清楚
    -  環境光源不太暗

3.  使用 [點一下手勢] 來捕捉人員的圖片。
4.  等待應用程式傳送分析要求並接收回應。
5.  如果已成功辨識人員，該人員的名稱將會顯示為 UI 文字。
6.  您可以使用每幾秒鐘的點一下手勢來重複執行捕捉程式。

## <a name="your-finished-azure-face-api-application"></a>您已完成的 Azure 臉部 API 應用程式

恭喜，您建立了一個混合現實應用程式，利用 Azure 臉部辨識服務來偵測影像中的臉部，並找出任何已知的臉部。

![完成本課程的結果](images/AzureLabs-Lab4-00.png)

## <a name="bonus-exercises"></a>額外練習

### <a name="exercise-1"></a>練習 1

**Azure 臉部 API** 的功能強大，足以偵測單一映射中最多64的臉部。 擴充應用程式，讓它能夠辨識出兩個或三個臉部，在其他許多人之間。

### <a name="exercise-2"></a>練習 2

**Azure 臉部 API** 也可以提供回所有種類的屬性資訊。 將此整合至應用程式。 相較于 [表情 API](https://azure.microsoft.com/services/cognitive-services/emotion/)，這可能更有趣。