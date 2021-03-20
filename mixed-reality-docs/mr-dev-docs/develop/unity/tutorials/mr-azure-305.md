---
title: HoloLens (第1代) 和 Azure 305-功能和儲存體
description: 完成本課程，以瞭解如何在混合現實應用程式內實行 Azure 儲存體和功能。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure，mixed reality，學院，unity，教學課程，api，函式，儲存體，hololens，沉浸，vr，Windows 10，Visual Studio
ms.openlocfilehash: b55acaf003a1cdf50a5a78e48fdf05a9ab07d0d6
ms.sourcegitcommit: 35bd43624be33afdb1bf6ba4ddbe36d268eb9bda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/20/2021
ms.locfileid: "104730545"
---
# <a name="hololens-1st-gen-and-azure-305-functions-and-storage"></a>HoloLens (第1代) 和 Azure 305：功能和儲存體

<br>

>[!NOTE]
>混合實境學院教學課程的設計是以 HoloLens (第 1 代) 和混合實境沉浸式頭戴裝置為準。  因此，對於仍在尋找這些裝置開發指引的開發人員而言，我們覺得這些教學課程很重要。  這些教學課程 **_不會_** 使用用於 HoloLens 2 的最新工具組或互動進行更新。  系統會保留這些資訊，以繼續在支援的裝置上運作。 未來將會有一系列新的教學課程，將會示範如何針對 HoloLens 2 進行開發。  當張貼這些教學課程時，將會使用這些教學課程的連結來更新此通知。

<br> 

![最終產品-開始](images/AzureLabs-Lab5-00.png)

在此課程中，您將瞭解如何在混合現實應用程式中建立和使用 Azure Functions，並將資料與 Azure 儲存體資源儲存在一起。

*Azure Functions* 是一項 Microsoft 服務，可讓開發人員在 Azure 中執行一小段程式碼，也就是「函數」。 這可提供將工作委派給雲端的方法，而不是您的本機應用程式，這可能有許多優點。 *Azure Functions* 支援數種開發語言，包括 C \# 、F \# 、Node.js、JAVA 和 PHP。 如需詳細資訊，請造訪 [Azure Functions 文章](/azure/azure-functions/functions-overview)。

*Azure 儲存體* 是一項 Microsoft 雲端服務，可讓開發人員儲存資料，並確保其高度可用、安全、持久、可調整和重複。 這表示 Microsoft 會為您處理所有維護和重大問題。 如需詳細資訊，請造訪 [Azure 儲存體文章](/azure/storage/common/storage-introduction)。

完成本課程之後，您將會有一個混合現實的沉浸式耳機應用程式，可以執行下列動作：

1.  允許使用者在場景周圍看著。
2.  當使用者 gazes 于3D 「按鈕」時，觸發物件的產生。
3.  衍生的物件將會由 Azure 函式選擇。
4.  當產生每個物件時，應用程式會將物件類型儲存在 *Azure* 檔案中，該檔案位於 *Azure 儲存體* 中。
5.  第二次載入時，將會抓取 *Azure* 檔案資料，並使用該資料從先前的應用程式實例重新執行產生動作。

在您的應用程式中，您可以自行決定如何將結果與您的設計整合。 本課程旨在告訴您如何整合 Azure 服務與您的 Unity 專案。 您的工作是使用您在本課程中所得到的知識，來增強您的混合現實應用程式。

## <a name="device-support"></a>裝置支援

<table>
<tr>
<th>課程</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">沉浸式頭戴裝置</a></th>
</tr><tr>
<td>MR 和 Azure 305：功能與儲存空間</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> 雖然本課程主要著重于 Windows Mixed Reality 沉浸式 (VR) 耳機，您也可以將在本課程中學到的內容套用至 Microsoft HoloLens。 當您依照課程的指示進行時，您將會看到有關您可能需要採用以支援 HoloLens 的任何變更的注意事項。

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
- 用來建立 Azure 資源之 Azure 帳戶的訂用帳戶
- 適用于 Azure 設定和資料抓取的網際網路存取

## <a name="before-you-start"></a>在您開始使用 Intune 之前

為了避免在建立此專案時發生問題，強烈建議您在根或近端根資料夾中，建立本教學課程中所述的專案 (長的資料夾路徑可能會在組建階段) 時發生問題。

## <a name="chapter-1---the-azure-portal"></a>第1章-Azure 入口網站

若要使用 **Azure 儲存體服務**，您將需要在 Azure 入口網站中建立及設定 **儲存體帳戶** 。

1.  登入  [Azure 入口網站](https://portal.azure.com)。

    > [!NOTE]
    > 如果您還沒有 Azure 帳戶，您將需要建立一個帳戶。 如果您在課堂或實驗室的情況下進行本教學課程，請洽詢講師或其中一個 proctors，協助您設定新的帳戶。

2.  登入後，按一下左上角的 [ **新增** ]，並搜尋 [ *儲存體帳戶*]，然後按一下 [ **輸入**]。

    ![azure 儲存體搜尋](images/AzureLabs-Lab5-01.png)

    > [!NOTE]
    > 在較新的入口網站中，[**建立資源**] 可能已取代 **新** 的文字。

3.  新頁面將提供 *Azure 儲存體帳戶* 服務的描述。 在此提示的左下方，選取 [ **建立** ] 按鈕，以建立與此服務的關聯。

    ![建立服務](images/AzureLabs-Lab5-02.png)

4.  當您按一下 [ **建立**] 之後：

    1.  為您的帳戶插入 *名稱* ，請注意，此欄位只接受數位和小寫字母。

    2.  在 [ *部署模型*] 中，選取 [ **資源管理員**]。

    3.  針對 [ *帳戶類型*]，選取 **[儲存體 (一般用途 v1)**。

    4.  如果您要建立新的資源群組) ，請判斷資源群組 (的 *位置* 。 位置最好是在應用程式執行所在的區域中。 某些 Azure 資產僅適用于某些區域。

    5.  若 *為複寫* ，請選取 [ **讀取權限-異地-多餘儲存體] (GRS])**。

    6.  針對 [效能]，請選取 [標準]。

    7.  將 [ *需要安全傳輸* ] 保留為 **停用**。

    8.  選取 [訂用帳戶]  。

    9. 選擇資源群組，或建立一個新的 *資源群組* 。 資源群組提供一種方式來監視、控制存取、布建及管理 Azure 資產集合的計費。 建議您保留與單一專案相關聯的所有 Azure 服務 (例如，) 一般資源群組下的實驗室，) 。 

        > 如果您想要閱讀更多有關 Azure 資源群組的資訊，請 [造訪資源群組文章](/azure/azure-resource-manager/resource-group-portal)。

    10. 您也必須確認您已瞭解套用到此服務的條款及條件。

    11. 選取 [建立]  。

        ![輸入服務資訊](images/AzureLabs-Lab5-03.png)

5.  當您按一下 [ **建立**] 之後，就必須等待服務建立完成，這可能需要一分鐘的時間。

6.  建立服務實例之後，入口網站中就會出現通知。

    ![azure 入口網站中的新通知](images/AzureLabs-Lab5-04.png)

7.  按一下通知以探索新的服務實例。

    ![移至資源](images/AzureLabs-Lab5-05.png)

8.  按一下通知中的 [ **移至資源** ] 按鈕，以流覽您的新服務實例。 您將會進入新的 *儲存體帳戶* 服務實例。

    ![access keys](images/AzureLabs-Lab5-06.png)

9.  按一下 [ *存取金鑰*]，以顯示此雲端服務的端點。 使用「 *記事本* 」或類似的，複製其中一個金鑰以供稍後使用。 此外，請記下 *連接字串* 值，因為它將用於 *AzureServices* 類別，您稍後將會建立此值。

    ![複製連接字串](images/AzureLabs-Lab5-07.png)

## <a name="chapter-2---setting-up-an-azure-function"></a>第2章-設定 Azure 函數

您現在會在 Azure 服務中撰寫 **azure** **函數** 。

您可以使用 **Azure** 函式來執行幾乎任何您在程式碼中使用傳統函式時所執行的作業，差別在於具有可存取 Azure 帳戶之認證的任何應用程式都可以存取此函式。

若要建立 Azure 函數：

1.  從 *Azure 入口網站* 中，按一下左上角的 [ **新增** ]，並搜尋函式 *應用程式*，然後按一下 **Enter**。

    ![建立函數應用程式](images/AzureLabs-Lab5-08.png)

    > [!NOTE]
    > 在較新的入口網站中，[**建立資源**] 可能已取代 **新** 的文字。

2.  新的頁面會提供 *Azure 函數應用程式* 服務的描述。 在此提示的左下方，選取 [ **建立** ] 按鈕，以建立與此服務的關聯。

    ![函數應用程式資訊](images/AzureLabs-Lab5-09.png)

3.  當您按一下 [ **建立**] 之後：

    1.  提供 *應用程式名稱*。 此處只可使用字母和數位 () 允許大寫或小寫。

    2.  選取您偏好的 *訂* 用帳戶。

    3. 選擇資源群組，或建立一個新的 *資源群組* 。 資源群組提供一種方式來監視、控制存取、布建及管理 Azure 資產集合的計費。 建議您保留與單一專案相關聯的所有 Azure 服務 (例如，) 一般資源群組下的實驗室，) 。 

        > 如果您想要閱讀更多有關 Azure 資源群組的資訊，請 [造訪資源群組文章](/azure/azure-resource-manager/resource-group-portal)。

    4.  針對此練習，請選取 [ *Windows* ] 做為選擇的 **作業系統**。

    5.  選取 **主控方案** 的取用 *方案*。

    6.  如果您要建立新的資源群組) ，請判斷資源群組 (的 *位置* 。 位置最好是在應用程式執行所在的區域中。 某些 Azure 資產僅適用于某些區域。 為了達到最佳效能，請選取與儲存體帳戶相同的區域。

    7.  針對 [ *儲存體*]，選取 [ **使用現有** 的]，然後使用下拉式功能表來尋找您先前建立的儲存體。

    8.  請勿在此練習中 *Application Insights* 關閉。

        ![輸入函數應用程式詳細資料](images/AzureLabs-Lab5-10.png)

4.  按一下 [ **建立** ] 按鈕。

5.  當您按一下 [ **建立**] 之後，就必須等待服務建立完成，這可能需要一分鐘的時間。

6.  建立服務實例之後，入口網站中就會出現通知。

    ![新的 azure 入口網站通知](images/AzureLabs-Lab5-11.png)

7.  按一下通知以探索新的服務實例。 

    ![移至資源函式應用程式](images/AzureLabs-Lab5-12.png)

8.  按一下通知中的 [ **移至資源** ] 按鈕，以流覽您的新服務實例。 您將會進入新的 *函數應用程式* 服務實例。

9.  在 [ *函數應用程式* ] 儀表板上，將滑鼠停留在左側面板中的 [函式 *] 上方，* 然後按一下 **+ (加號)** 符號]。

    ![建立新函數](images/AzureLabs-Lab5-13.png)

10. 在下一個頁面上，確定已選取 [ **Webhook + API** ]，然後選取 *[* **CSharp**]，因為這會是本教學課程所使用的語言。 最後，按一下 [ **建立此函數** ] 按鈕。

    ![選取網路攔截 csharp](images/AzureLabs-Lab5-14.png)

11. 您應該會進入字碼頁 (.csx) ，如果沒有，請在左側面板中的 [函數] 清單中，按一下新建立的函數。

    ![開啟新函數](images/AzureLabs-Lab5-15.png)

12. 將下列程式碼複製到您的函式中。 呼叫時，此函式只會傳回0和2之間的隨機整數。 不要擔心現有的程式碼，您可以隨意貼到它的最上方。

    ```csharp
        using System.Net;
        using System.Threading.Tasks;

        public static int Run(CustomObject req, TraceWriter log)
        {
            Random rnd = new Random();
            int randomInt = rnd.Next(0, 3);
            return randomInt;
        }

        public class CustomObject
        {
            public String name {get; set;}
        }
    ```

13. 選取 [儲存]。

14. 結果看起來應該如下圖所示。

15. 按一下 [ **取得** 函式 URL]，並記下顯示的 *端點* 。 您必須將它插入您稍後將在本課程中建立的 *AzureServices* 類別。

    ![取得函式端點](images/AzureLabs-Lab5-16.png)

    ![插入函數端點](images/AzureLabs-Lab5-16-5.png)

## <a name="chapter-3---setting-up-the-unity-project"></a>第3章-設定 Unity 專案

以下是使用 Mixed Reality 進行開發的一般設定，因此，它是適用于其他專案的絕佳範本。

設定及測試您的混合現實沉浸式耳機。

> [!NOTE]
> 在此課程中，您將 **不** 需要移動控制器。 如果您需要設定沉浸式耳機的支援，請 [造訪「混合現實設定」一文](https://support.microsoft.com/help/4043101/windows-10-set-up-windows-mixed-reality)。

1.  開啟 Unity，然後按一下 [ **新增**]。

    ![建立新的 unity 專案](images/AzureLabs-Lab5-17.png)

2.  您現在將需要提供 Unity 專案名稱。 插入 **MR_Azure_Functions**。 請確定專案類型設定為 **3d**。 將 *位置* 設定為適合您 (記住，較接近根目錄的) 。 然後，按一下 [ **建立專案**]。

    ![提供新的 unity 專案名稱](images/AzureLabs-Lab5-18.png)

3.  在 Unity 開啟的情況下，值得檢查預設 **腳本編輯器** 是否設定為 **Visual Studio**。 移至 [**編輯**  >  **喜好** 設定]，然後在新視窗中，流覽至 [**外部工具**]。 將 **外部腳本編輯器** 變更為 **Visual Studio 2017**。 關閉 [ **喜好** 設定] 視窗。

    ![將 visual studio 設定為腳本編輯器](images/AzureLabs-Lab5-19.png)

4.  接下來，移 **至 [** 檔案  >  **組建設定**]，然後按一下 [**切換平臺**] 按鈕，將平臺切換至 **通用 Windows 平臺**。

    ![將平臺切換至 uwp](images/AzureLabs-Lab5-20.png)

5.  移至 **檔案**  >  **組建設定**，並確定：

    1. **目標裝置** 設定為 **任何裝置**。

        > 針對 Microsoft HoloLens，請將 **目標裝置** 設定為 *HoloLens*。

    2. **組建類型** 設定為 **D3D**

    3. **SDK** 已設定為 **最新安裝**

    4. **Visual Studio 版本** 設定為 **最新安裝**

    5. **組建並執行** 設定為 **本機電腦**

    6. 儲存場景，並將其新增至組建。

        1.  若要這麼做，請選取 [ **新增開啟的場景**]。 [儲存] 視窗隨即出現。

            ![新增開啟的場景](images/AzureLabs-Lab5-21.png)

        2.  為此和任何未來的場景建立新的資料夾，然後選取 [ **新增資料夾** ] 按鈕，建立新的資料夾，將它命名為 **場景**。

            ![建立場景資料夾](images/AzureLabs-Lab5-22.png)

        3.  開啟新建立的 **場景** 資料夾，然後在 [ **檔案名：** 文字] 欄位中輸入 **FunctionsScene**，然後按 [ **儲存**]。

            ![儲存函式場景](images/AzureLabs-Lab5-23.png)

6.  [ **組建設定**] 中的其餘設定，現在應該保持為預設值。

    ![保留預設組建設定](images/AzureLabs-Lab5-24.png)

7.  在 [ *組建設定* ] 視窗中，按一下 [ **播放程式設定** ] 按鈕，這會開啟偵測 *器* 所在空間中的相關面板。

    ![偵測器中的播放機設定](images/AzureLabs-Lab5-25.png)

8.  在此面板中，需要驗證幾個設定：

    1.  在 [ **其他設定** ] 索引標籤中：

        1.  **腳本執行階段版本** 應該是 **實驗** ( .net 4.6 對等) ，這會觸發重新開機編輯器的需求。
        2.  **腳本後端** 應該是 **.net**
        3.  **API 相容性層級** 應為 **.net 4.6**

    2.  在 [ **發行設定** ] 索引標籤的 [ **功能**] 下，選取：
        
        -  **InternetClient**

            ![設定功能](images/AzureLabs-Lab5-26.png)

    3.  在面板的 [ **XR 設定** ] 中，在 [設定] () 的 [ **發佈設定** ] 下方找到 [支援的滴答 **虛擬事實**]，請確定已新增 **Windows Mixed Reality SDK** 。

        ![設定 XR 設定](images/AzureLabs-Lab5-27.png)

9.  回到 *組建設定*： *Unity c # 專案* 不再呈現灰色;勾選此方塊旁邊的核取方塊。

    ![刻度 c # 專案](images/AzureLabs-Lab5-28.png)

10.  關閉 [建置設定] 視窗。

11. 儲存場景和專案 (**檔**  >  **儲存場景/** 檔案  >  **儲存專案**) 。

## <a name="chapter-4---setup-main-camera"></a>第4章-設定主要攝影機

> [!IMPORTANT]
> 如果您想要略過 *Unity 設定* 此課程的元件，並直接繼續進行程式碼，請隨意 [下載 unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20305%20-%20Functions%20and%20storage/Azure-MR-305.unitypackage)，並將它匯入至您的專案中做為 [自訂套件](https://docs.unity3d.com/Manual/AssetPackages.html)。 這也會包含下一章中的 Dll。 匯入之後，請繼續進行 [第7章](#chapter-7---create-the-azureservices-class)。 

1.  在 [階層] *面板* 中，您會找到一個稱為「 **主要攝影機**」的物件，此物件代表您在應用程式「內」之後的「頭部」觀點。

2.  使用 Unity 儀表板，選取 **主要攝影機 GameObject**。 您將會注意到，在儀錶) 板內 (的 [偵測 *器] 面板* 通常會顯示該 *GameObject* 的各種元件，並在頂端、*相機* 和一些其他元件中顯示 *轉換*。 您必須重設主要攝影機的轉換，才能正確定位。

3.  若要這樣做，請選取相機 *轉換* 元件旁邊的 **齒輪** 圖示，然後選取 [**重設**]。

    ![重設轉換](images/AzureLabs-Lab5-29.png)

4.  然後，將 **轉換** 元件更新為如下所示：

    |         |    轉換-位置   |       |
    | :-----: | :-----------------------: | :----:|
    | **X**   | **Y**                     | **Z** |
    | 0       | 1                         | 0     |    

    |       | 轉換-旋轉 |       |
    | :---: | :------------------: | :----:|
    | **X** | **Y**                | **Z** |
    | 0     | 0                    | 0     |

    |       | 轉換-調整規模 |       |
    | :---: | :---------------: | :---: |
    | **X** | **Y**             | **Z** |
    | 1     | 1                 | 1     |

    ![設定相機轉換](images/AzureLabs-Lab5-30.png)

## <a name="chapter-5---setting-up-the-unity-scene"></a>第5章-設定 Unity 場景

1.  在 [階層] *面板* 的空白區域中，以滑鼠右鍵按一下 [ **3d 物件**] 下的 [加入 **平面**]。

    ![建立新的平面](images/AzureLabs-Lab5-31.png)

2.  選取 **平面** 物件之後，在 [偵測 *器] 面板* 中變更下列參數：

    |       | 轉換-位置 |       |
    | :---: | :------------------: | :---: |
    | **X** | **Y**                | **Z** |
    | 0     | 0                    | 4     |

    |       | 轉換-調整規模 |       |
    | :---: | :---------------: | :---: |
    | **X** | **Y**             | **Z** |
    | 10    | 1                 | 10    |

    ![設定平面位置和小數位數](images/AzureLabs-Lab5-32.png)

    ![平面的場景視圖](images/AzureLabs-Lab5-33.png)

3.  在 [階層] *面板* 的空白區域中，以滑鼠右鍵按一下 [ **3d 物件**] 下的 [加入 **Cube**]。

    1.  將 Cube 重新命名為 **GazeButton** (已選取 cube，請按 ' F2 ' ) 。

    2.  在 [偵測 *器] 面板* 中變更下列參數：

        |       | 轉換-位置 |       |
        | :---: | :------------------: |:-----:|
        | **X** | **Y**                | **Z** |
        | 0     | 3                    | 5     |


        ![設定注視按鈕轉換](images/AzureLabs-Lab5-34.png)

        ![注視按鈕場景視圖](images/AzureLabs-Lab5-35.png)

    3.  按一下 [ **標記** ] 下拉式按鈕，然後按一下 [ **新增** 標籤]，即可開啟 [ *標記 & 圖層] 窗格*。

        ![新增標記](images/AzureLabs-Lab5-36.png)

        ![選取加號](images/AzureLabs-Lab5-37.png)

    4.  選取 **+ (加號)** ] 按鈕，然後在 [ *新* 標籤名稱] 欄位中，輸入 **GazeButton**，然後按 [ **儲存**]。

        ![命名新標記](images/AzureLabs-Lab5-38.png)

    5.  按一下 [階層]*面板* 中的 [ **GazeButton** ] 物件，然後在 [偵測 *器] 面板* 中，指派新建立的 **GazeButton** 標記。

        ![將新標籤指派給注視按鈕](images/AzureLabs-Lab5-39.png)

4.  以滑鼠右鍵按一下 [階層]*面板* 中的 [ **GazeButton** ] 物件，然後新增 **空白的 GameObject** (將會新增為 *子* 物件) 。

5.  選取新的物件，並將它重新命名為 **ShapeSpawnPoint**。

    1.  在 [偵測 *器] 面板* 中變更下列參數：

        |       | 轉換-位置 |       |
        | :---: | :------------------: |:----: |
        | **X** |**Y**                 | **Z** |
        | 0     | -1                   | 0     |

        ![更新圖形產生點轉換](images/AzureLabs-Lab5-40.png)

        ![圖形產生點場景視圖](images/AzureLabs-Lab5-41.png)

6.  接下來，您將建立 **3D 文字** 物件，以提供 Azure 服務狀態的相關意見反應。

    再以滑鼠右鍵按一下 [階層] 面板中的 [ **GazeButton** ]，並新增 **3d 物件**  >  **3d 文字** 物件做為 *子* 系。

    ![建立新的3D 文字物件](images/AzureLabs-Lab5-42.png)

7.  將 **3D 文字** 物件重新命名為 **AzureStatusText**。

8.  變更 **AzureStatusText** 物件轉換，如下所示：

    |       | 轉換-位置 |       |
    | :---: | :------------------: | :---: |
    | **X** | **Y**                | **Z** |
    | 0     | 0                    | -0.6  |

    |       | 轉換-調整規模 |       |
    | :---: | :---------------: | :---: |
    | **X** | **Y**             | **Z** |
    | 0.1   | 0.1               | 0.1   |


    > [!NOTE]
    > 如果看起來像是下層，請不要擔心，因為在更新下列文字網格元件時，將會修正此問題。

9.  變更 **文字網格** 元件以符合下列各項：

    ![設定文字網格元件](images/AzureLabs-Lab5-43.png)

    > [!TIP]
    > 在這裡選取的色彩是十六進位色彩： **000000FF**，不過您可以自行選擇，只需確保它可供閱讀。

10. 階層面板結構現在看起來應該像這樣：

    ![階層中的文字網格](images/AzureLabs-Lab5-43b.png)

10. 您的場景現在看起來應該像這樣：

    ![場景視圖中的文字網格](images/AzureLabs-Lab5-44.png)


## <a name="chapter-6---import-azure-storage-for-unity"></a>第6章-匯入 Unity 的 Azure 儲存體

您將使用適用于 Unity (的 Azure 儲存體，其本身會利用 .Net SDK for Azure) 。 您可以在 [Unity 文章的 Azure 儲存體](/sandbox/gamedev/unity/azure-storage-unity)閱讀詳細資訊。

Unity 中目前有已知的問題，需要在匯入之後重新設定外掛程式。 在解決 bug 之後，將不再需要這一節中的這些步驟 (4-7) 。

若要將 SDK 匯入您自己的專案中，請確定您已從 GitHub 下載最新的 ['. unitypackage '](https://aka.ms/azstorage-unitysdk)。 然後執行下列動作：

1.  使用 [  **資產** 匯  >  **入封裝**  >  **自訂套件**] 功能表選項，將 unitypackage 檔案新增至 Unity。

2.  在快顯的 [匯 **入 Unity 套件**] 方塊中，您可以選取 **外掛程式**  >  **儲存體** 下的所有專案。 取消核取其他所有專案，因為此課程不需要。

    ![匯入至封裝](images/AzureLabs-Lab5-45.png)

3.  按一下 [匯 **入** ] 按鈕，將專案新增至您的專案。

4.  移至 [*外掛程式*] 下的 [*儲存體*] 資料夾，在 [專案] 視圖中，*只* 選取下列外掛程式：

    -   Microsoft.Data.Edm
    -   Microsoft.Data.OData
    -   Microsoft.WindowsAzure.Storage
    -   Newtonsoft.Json
    -   System.Spatial

        ![取消核取任何平臺](images/AzureLabs-Lab5-46.png)

5.  選取 *這些特定的外掛程式* 之後， **取消** 核取 *任何平臺* ，然後 **取消** 核取 *WSAPlayer* ， **然後按一下 [** 套用]。

    ![套用平臺 dll](images/AzureLabs-Lab5-47.png)

    > [!NOTE]
    > 我們會將這些特定外掛程式標示為僅用於 Unity 編輯器。 這是因為在 [WSA] 資料夾中有不同版本的相同外掛程式，在從 Unity 匯出專案之後，將會使用這些相同的外掛程式。

6.  在 [ *儲存體* 外掛程式] 資料夾中，只選取：

    -   Microsoft.Data.Services.Client

        ![set 不要處理 dll](images/AzureLabs-Lab5-48.png)

7.  勾選 [*平臺設定*] 下的 [**不處理**] 方塊，**然後按一下 [** 套用]。

    ![套用無處理](images/AzureLabs-Lab5-49.png)

    > [!NOTE]
    > 因為 Unity 元件 patcher 在處理此外掛程式時遇到困難，所以我們將此外掛程式標示為「不要處理」。 雖然外掛程式不會進行處理，但仍可運作。

## <a name="chapter-7---create-the-azureservices-class"></a>第7章-建立 AzureServices 類別

您即將建立的第一個類別是 *AzureServices* 類別。

*AzureServices* 類別將負責：

-   儲存 Azure 帳號憑證。

-   呼叫您的 Azure App 函數。

-   上傳和下載 Azure 雲端儲存體中的資料檔案。

若要建立此類別：

1.  以滑鼠右鍵按一下 [專案] 面板中的 [*資產*] 資料夾，然後 **建立**  >  **資料夾**。 將資料夾命名為 **腳本**。

    ![建立新資料夾](images/AzureLabs-Lab5-50.png)

    ![呼叫資料夾-腳本](images/AzureLabs-Lab5-51.png)

2.  按兩下剛才建立的資料夾，將它開啟。

3.  以滑鼠右鍵按一下資料夾內的 [**建立**  >  **c # 腳本**]。 呼叫腳本 *AzureServices*。

4.  按兩下新的 *AzureServices* 類別，以 *Visual Studio* 開啟。

5.  將下列命名空間新增至 *AzureServices* 的頂端：

    ```csharp
        using System;
        using System.Threading.Tasks;
        using UnityEngine;
        using Microsoft.WindowsAzure.Storage;
        using Microsoft.WindowsAzure.Storage.File;
        using System.IO;
        using System.Net;
    ```

6.  在 *AzureServices* 類別內新增下列偵測器欄位：

    ```csharp
        /// <summary>
        /// Provides Singleton-like behavior to this class.
        /// </summary>
        public static AzureServices instance;

        /// <summary>
        /// Reference Target for AzureStatusText Text Mesh object
        /// </summary>
        public TextMesh azureStatusText;
    ```

7.  然後，在 *AzureServices* 類別內新增下列成員變數：

    ```csharp
        /// <summary>
        /// Holds the Azure Function endpoint - Insert your Azure Function
        /// Connection String here.
        /// </summary>

        private readonly string azureFunctionEndpoint = "--Insert here you AzureFunction Endpoint--";

        /// <summary>
        /// Holds the Storage Connection String - Insert your Azure Storage
        /// Connection String here.
        /// </summary>
        private readonly string storageConnectionString = "--Insert here you AzureStorage Connection String--";

        /// <summary>
        /// Name of the Cloud Share - Hosts directories.
        /// </summary>
        private const string fileShare = "fileshare";

        /// <summary>
        /// Name of a Directory within the Share
        /// </summary>
        private const string storageDirectory = "storagedirectory";

        /// <summary>
        /// The Cloud File
        /// </summary>
        private CloudFile shapeIndexCloudFile;

        /// <summary>
        /// The Linked Storage Account
        /// </summary>
        private CloudStorageAccount storageAccount;

        /// <summary>
        /// The Cloud Client
        /// </summary>
        private CloudFileClient fileClient;

        /// <summary>
        /// The Cloud Share - Hosts Directories
        /// </summary>
        private CloudFileShare share;

        /// <summary>
        /// The Directory in the share that will host the Cloud file
        /// </summary>
        private CloudFileDirectory dir;
    ```

    > [!IMPORTANT]
    > 請務必使用 azure 入口網站中的 Azure 儲存體值來取代 *端點* 和 *連接字串* 值

8.  現在需要新增 *喚醒 ()* 和 *啟動 ()* 方法的程式碼。 當類別初始化時，會呼叫這些方法：

    ```csharp
        private void Awake()
        {
            instance = this;
        }

        // Use this for initialization
        private void Start()
        {
            // Set the Status text to loading, whilst attempting connection to Azure.
            azureStatusText.text = "Loading...";
        }

        /// <summary>
        /// Call to the Azure Function App to request a Shape.
        /// </summary>
        public async void CallAzureFunctionForNextShape()
        {

        }
    ```

    > [!IMPORTANT]
    > 我們將在 [未來的章節](#chapter-10---completing-the-azureservices-class)中，填入 *CallAzureFunctionForNextShape ()* 的程式碼。

9.  刪除 *更新 ()* 方法，因為此類別不會使用它。

10. 將您的變更儲存在 Visual Studio 中，然後回到 Unity。

11. 按一下 [腳本] 資料夾中的 [ *AzureServices* ] 類別，並將其拖曳至 [階層] *面板* 中的 [主要攝影機] 物件。

12. 選取主要攝影機，然後從 **GazeButton** 物件底下抓取 **AzureStatusText** 子物件，並將它放在偵測 *器* 的 [ **AzureStatusText** 參考目標] 欄位中，以提供 *AzureServices* 腳本的參考。

    ![指派 azure 狀態文字參考目標](images/AzureLabs-Lab5-52.png)

## <a name="chapter-8---create-the-shapefactory-class"></a>第8章-建立 ShapeFactory 類別

下一個要建立的腳本是 *ShapeFactory* 類別。 此類別的角色是在要求時建立新的圖形，並保留在 *圖形歷程記錄清單* 中建立之圖形的歷程記錄。 每次建立圖形時，圖形歷程 *記錄清單* 都會在 *AzureService* 類別中更新，然後儲存在 *Azure 儲存體* 中。 當應用程式啟動時，如果在 *Azure 儲存體* 中找到儲存的檔案，則會取出並重新執行 *圖形歷程記錄清單* ，其中包含提供產生的圖形是從儲存體或新的 **3d 文字** 物件。

若要建立此類別：

1.  移至您先前建立的 **腳本** 資料夾。

2.  以滑鼠右鍵按一下資料夾內的 [**建立**  >  **c # 腳本**]。 呼叫腳本 *ShapeFactory*。

3.  按兩下新的 *ShapeFactory* 腳本，以 *Visual Studio* 開啟。

4.  確定 *ShapeFactory* 類別包含下列命名空間：

    ```csharp
        using System.Collections.Generic;
        using UnityEngine;
    ```

5.  將如下所示的變數新增至 *ShapeFactory* 類別，並將 *Start ()* 和 *喚醒的 ()* 函式取代如下：

    ```csharp
        /// <summary>
        /// Provide this class Singleton-like behaviour
        /// </summary>
        [HideInInspector]
        public static ShapeFactory instance;

        /// <summary>
        /// Provides an Inspector exposed reference to ShapeSpawnPoint
        /// </summary>
        [SerializeField]
        public Transform spawnPoint;

        /// <summary>
        /// Shape History Index
        /// </summary>
        [HideInInspector]
        public List<int> shapeHistoryList;

        /// <summary>
        /// Shapes Enum for selecting required shape
        /// </summary>
        private enum Shapes { Cube, Sphere, Cylinder }

        private void Awake()
        {
            instance = this;
        }

        private void Start()
        {
            shapeHistoryList = new List<int>();
        }
    ```

6.  *CreateShape ()* 方法會根據提供的 *整數* 參數產生基本圖案。 布林值參數是用來指定目前建立的圖形是從儲存體或新的。 在您的 *ShapeFactory* 類別中，將下列程式碼放在先前的方法底下：

    ```csharp
        /// <summary>
        /// Use the Shape Enum to spawn a new Primitive object in the scene
        /// </summary>
        /// <param name="shape">Enumerator Number for Shape</param>
        /// <param name="storageShape">Provides whether this is new or old</param>
        internal void CreateShape(int shape, bool storageSpace)
        {
            Shapes primitive = (Shapes)shape;
            GameObject newObject = null;
            string shapeText = storageSpace == true ? "Storage: " : "New: ";

            AzureServices.instance.azureStatusText.text = string.Format("{0}{1}", shapeText, primitive.ToString());

            switch (primitive)
            {
                case Shapes.Cube:
                newObject = GameObject.CreatePrimitive(PrimitiveType.Cube);
                break;

                case Shapes.Sphere:
                newObject = GameObject.CreatePrimitive(PrimitiveType.Sphere);
                break;

                case Shapes.Cylinder:
                newObject = GameObject.CreatePrimitive(PrimitiveType.Cylinder);
                break;
            }

            if (newObject != null)
            {
                newObject.transform.position = spawnPoint.position;

                newObject.transform.localScale = new Vector3(0.5f, 0.5f, 0.5f);

                newObject.AddComponent<Rigidbody>().useGravity = true;

                newObject.GetComponent<Renderer>().material.color = UnityEngine.Random.ColorHSV(0f, 1f, 1f, 1f, 0.5f, 1f);
            }
        }
    ```

7.  返回 Unity 之前，請務必將您的變更儲存在 Visual Studio 中。

8.  返回 Unity 編輯器中，按一下 [**腳本**] 資料夾中的 [ *ShapeFactory* ] 類別，並將其拖曳至 [階層]*面板* 中的 [**主要攝影機**] 物件。

9. 選取主要攝影機之後，您會注意到 *ShapeFactory* 腳本元件缺少產生 *點* 參考。 若要修正此問題，請將 [ **ShapeSpawnPoint** ] 物件從 [階層] *面板* 拖曳至 [產生 **點** 參考] 目標。

    ![設定圖形 factory 參考目標](images/AzureLabs-Lab5-53.png)

## <a name="chapter-9---create-the-gaze-class"></a>第9章-建立注視類別

您需要建立的最後一個腳本是 *注視* 類別。

此類別負責建立將從主要相機向前投影的 **Raycast** ，以偵測使用者所查看的物件。 在此情況下，Raycast 將需要識別使用者是否正在查看場景中的 **GazeButton** 物件，並觸發行為。

若要建立此類別：

1.  移至您先前建立的 **腳本** 資料夾。

2.  以滑鼠右鍵按一下 [專案] 面板中的 [**建立**  >  **c # 腳本**]。 呼叫腳本 *注視*。

3.  按兩下新的 *注視* 腳本，使用 *Visual Studio 開啟。*

4.  確定腳本的頂端包含下列命名空間：

    ```csharp
        using UnityEngine;
    ```

5.  然後，在 *注視* 類別內新增下列變數：

    ```csharp
        /// <summary>
        /// Provides Singleton-like behavior to this class.
        /// </summary>
        public static Gaze instance;

        /// <summary>
        /// The Tag which the Gaze will use to interact with objects. Can also be set in editor.
        /// </summary>
        public string InteractibleTag = "GazeButton";

        /// <summary>
        /// The layer which will be detected by the Gaze ('~0' equals everything).
        /// </summary>
        public LayerMask LayerMask = ~0;

        /// <summary>
        /// The Max Distance the gaze should travel, if it has not hit anything.
        /// </summary>
        public float GazeMaxDistance = 300;

        /// <summary>
        /// The size of the cursor, which will be created.
        /// </summary>
        public Vector3 CursorSize = new Vector3(0.05f, 0.05f, 0.05f);

        /// <summary>
        /// The color of the cursor - can be set in editor.
        /// </summary>
        public Color CursorColour = Color.HSVToRGB(0.0223f, 0.7922f, 1.000f);

        /// <summary>
        /// Provides when the gaze is ready to start working (based upon whether
        /// Azure connects successfully).
        /// </summary>
        internal bool GazeEnabled = false;

        /// <summary>
        /// The currently focused object.
        /// </summary>
        internal GameObject FocusedObject { get; private set; }

        /// <summary>
        /// The object which was last focused on.
        /// </summary>
        internal GameObject _oldFocusedObject { get; private set; }

        /// <summary>
        /// The info taken from the last hit.
        /// </summary>
        internal RaycastHit HitInfo { get; private set; }

        /// <summary>
        /// The cursor object.
        /// </summary>
        internal GameObject Cursor { get; private set; }

        /// <summary>
        /// Provides whether the raycast has hit something.
        /// </summary>
        internal bool Hit { get; private set; }

        /// <summary>
        /// This will store the position which the ray last hit.
        /// </summary>
        internal Vector3 Position { get; private set; }

        /// <summary>
        /// This will store the normal, of the ray from its last hit.
        /// </summary>
        internal Vector3 Normal { get; private set; }

        /// <summary>
        /// The start point of the gaze ray cast.
        /// </summary>
        private Vector3 _gazeOrigin;

        /// <summary>
        /// The direction in which the gaze should be.
        /// </summary>
        private Vector3 _gazeDirection;
    ```

> [!IMPORTANT]
> 這些變數中有一些可以在 *編輯器* 中編輯。

6.  現在需要新增 *喚醒 ()* 和 *啟動 ()* 方法的程式碼。

    ```csharp
        /// <summary>
        /// The method used after initialization of the scene, though before Start().
        /// </summary>
        private void Awake()
        {
            // Set this class to behave similar to singleton
            instance = this;
        }

        /// <summary>
        /// Start method used upon initialization.
        /// </summary>
        private void Start()
        {
            FocusedObject = null;
            Cursor = CreateCursor();
        }
    ```

7.  新增下列程式碼，此程式碼會在開始時建立資料指標物件，以及 *更新 ()* 方法，這會執行 Raycast 方法，以及 GazeEnabled 布林值的切換位置：

    ```csharp
        /// <summary>
        /// Method to create a cursor object.
        /// </summary>
        /// <returns></returns>
        private GameObject CreateCursor()
        {
            GameObject newCursor = GameObject.CreatePrimitive(PrimitiveType.Sphere);
            newCursor.SetActive(false);

            // Remove the collider, so it doesn't block raycast.
            Destroy(newCursor.GetComponent<SphereCollider>());
            newCursor.transform.localScale = CursorSize;

            newCursor.GetComponent<MeshRenderer>().material = new Material(Shader.Find("Diffuse"))
            {
                color = CursorColour
            };

            newCursor.name = "Cursor";

            newCursor.SetActive(true);

            return newCursor;
        }

        /// <summary>
        /// Called every frame
        /// </summary>
        private void Update()
        {
            if(GazeEnabled == true)
            {
                _gazeOrigin = Camera.main.transform.position;

                _gazeDirection = Camera.main.transform.forward;

                UpdateRaycast();
            }
        }
    ```

8. 接著，新增 *UpdateRaycast ()* 方法，它會投影 Raycast 並偵測點擊目標。

    ```csharp
        private void UpdateRaycast()
        {
            // Set the old focused gameobject.
            _oldFocusedObject = FocusedObject;

            RaycastHit hitInfo;

            // Initialise Raycasting.
            Hit = Physics.Raycast(_gazeOrigin,
                _gazeDirection,
                out hitInfo,
                GazeMaxDistance, LayerMask);

            HitInfo = hitInfo;

            // Check whether raycast has hit.
            if (Hit == true)
            {
                Position = hitInfo.point;

                Normal = hitInfo.normal;

                // Check whether the hit has a collider.
                if (hitInfo.collider != null)
                {
                    // Set the focused object with what the user just looked at.
                    FocusedObject = hitInfo.collider.gameObject;
                }
                else
                {
                    // Object looked on is not valid, set focused gameobject to null.
                    FocusedObject = null;
                }
            }
            else
            {
                // No object looked upon, set focused gameobject to null.
                FocusedObject = null;

                // Provide default position for cursor.
                Position = _gazeOrigin + (_gazeDirection * GazeMaxDistance);

                // Provide a default normal.
                Normal = _gazeDirection;
            }

            // Lerp the cursor to the given position, which helps to stabilize the gaze.
            Cursor.transform.position = Vector3.Lerp(Cursor.transform.position, Position, 0.6f);

            // Check whether the previous focused object is this same 
            //    object. If so, reset the focused object.
            if (FocusedObject != _oldFocusedObject)
            {
                ResetFocusedObject();

                if (FocusedObject != null)
                {
                if (FocusedObject.CompareTag(InteractibleTag.ToString()))
                {
                        // Set the Focused object to green - success!
                        FocusedObject.GetComponent<Renderer>().material.color = Color.green;

                        // Start the Azure Function, to provide the next shape!
                        AzureServices.instance.CallAzureFunctionForNextShape();
                    }
                }
            }
        }
    ```

9. 最後，加入 *ResetFocusedObject ()* 方法，這會切換 GazeButton 物件目前的色彩，指出是否正在建立新的圖形。

    ```csharp
        /// <summary>
        /// Reset the old focused object, stop the gaze timer, and send data if it
        /// is greater than one.
        /// </summary>
        private void ResetFocusedObject()
        {
            // Ensure the old focused object is not null.
            if (_oldFocusedObject != null)
            {
                if (_oldFocusedObject.CompareTag(InteractibleTag.ToString()))
                {
                    // Set the old focused object to red - its original state.
                    _oldFocusedObject.GetComponent<Renderer>().material.color = Color.red;
                }
            }
        }
    ```

10.  在回到 Unity 之前，請先將您的變更儲存在 Visual Studio 中。

11.  按一下 [腳本] 資料夾中的 [*注視*] 類別，並將其拖曳至 [階層]*面板* 中的 [**主要攝影機**] 物件。

## <a name="chapter-10---completing-the-azureservices-class"></a>第10章-完成 AzureServices 類別

有了其他腳本之後，現在就可以 *完成* *AzureServices* 類別。 這可透過下列途徑達成：

1.  新增名為 *CreateCloudIdentityAsync ()* 的新方法，以設定與 Azure 進行通訊所需的驗證變數。

    > 這個方法也會檢查先前儲存的檔案是否包含圖形清單。
    >
    > **如果找到該** 檔案，則會根據圖形模式（儲存在 **Azure 儲存體** 檔案中），停用使用者的 *注視* 和觸發圖形建立。 使用者可以看到這種情況，因為 **文字網格** 會提供顯示 [儲存] 或 [新增]，視圖形的來源而定。
    >
    > **如果找不到任何** 檔案，則會啟用 *注視*，讓使用者在查看場景中的 **GazeButton** 物件時建立圖形。

    ```csharp
        /// <summary>
        /// Create the references necessary to log into Azure
        /// </summary>
        private async void CreateCloudIdentityAsync()
        {
            // Retrieve storage account information from connection string
            storageAccount = CloudStorageAccount.Parse(storageConnectionString);

            // Create a file client for interacting with the file service.
            fileClient = storageAccount.CreateCloudFileClient();

            // Create a share for organizing files and directories within the storage account.
            share = fileClient.GetShareReference(fileShare);

            await share.CreateIfNotExistsAsync();

            // Get a reference to the root directory of the share.
            CloudFileDirectory root = share.GetRootDirectoryReference();

            // Create a directory under the root directory
            dir = root.GetDirectoryReference(storageDirectory);

            await dir.CreateIfNotExistsAsync();

            //Check if the there is a stored text file containing the list
            shapeIndexCloudFile = dir.GetFileReference("TextShapeFile");

            if (!await shapeIndexCloudFile.ExistsAsync())
            {
                // File not found, enable gaze for shapes creation
                Gaze.instance.GazeEnabled = true;

                azureStatusText.text = "No Shape\nFile!";
            }
            else
            {
                // The file has been found, disable gaze and get the list from the file
                Gaze.instance.GazeEnabled = false;

                azureStatusText.text = "Shape File\nFound!";

                await ReplicateListFromAzureAsync();
            }
        }
    ```

2.  下一個程式碼片段是來自 *Start ()* 方法內;其中會對 *CreateCloudIdentityAsync ()* 方法進行呼叫。 您可以透過下列方式，隨意複製您目前的 *Start ()* 方法：

    ```csharp
        private void Start()
        {
            // Disable TLS cert checks only while in Unity Editor (until Unity adds support for TLS)
    #if UNITY_EDITOR
            ServicePointManager.ServerCertificateValidationCallback = delegate { return true; };
    #endif

            // Set the Status text to loading, whilst attempting connection to Azure.
            azureStatusText.text = "Loading...";

            //Creating the references necessary to log into Azure and check if the Storage Directory is empty
            CreateCloudIdentityAsync();
        }
    ```

3.  填入 *CallAzureFunctionForNextShape ()* 方法的程式碼。 您將使用先前建立的 *Azure 函數應用程式* 來要求圖形索引。 一旦收到新的圖形之後，這個方法會將圖形傳送至 *ShapeFactory* 類別，以便在場景中建立新的圖形。 使用下列程式碼來完成 *CallAzureFunctionForNextShape ()* 的主體。

    ```csharp
        /// <summary>
        /// Call to the Azure Function App to request a Shape.
        /// </summary>
        public async void CallAzureFunctionForNextShape()
        {
            int azureRandomInt = 0;

            // Call Azure function
            HttpWebRequest webRequest = WebRequest.CreateHttp(azureFunctionEndpoint);

            WebResponse response = await webRequest.GetResponseAsync();

            // Read response as string
            using (Stream stream = response.GetResponseStream())
            {
                StreamReader reader = new StreamReader(stream);

                String responseString = reader.ReadToEnd();

                //parse result as integer
                Int32.TryParse(responseString, out azureRandomInt);
            }

            //add random int from Azure to the ShapeIndexList
            ShapeFactory.instance.shapeHistoryList.Add(azureRandomInt);

            ShapeFactory.instance.CreateShape(azureRandomInt, false);

            //Save to Azure storage
            await UploadListToAzureAsync();
        }
    ```

4.  藉由串連儲存在圖形歷程記錄清單中的整數，並將其儲存在 *Azure 儲存體* 檔案中，來新增方法來建立字串。

    ```csharp
        /// <summary>
        /// Upload the locally stored List to Azure
        /// </summary>
        private async Task UploadListToAzureAsync()
        {
            // Uploading a local file to the directory created above
            string listToString = string.Join(",", ShapeFactory.instance.shapeHistoryList.ToArray());

            await shapeIndexCloudFile.UploadTextAsync(listToString);
        }
    ```

5.  新增方法，以抓取 *Azure 儲存體* 檔案中儲存的檔案中所儲存的 *文字，並* 將其還原序列化為清單。

6.  完成此程式之後，方法會重新啟用注視，讓使用者可以在場景中新增更多圖形。

    ```csharp
        ///<summary>
        /// Get the List stored in Azure and use the data retrieved to replicate 
        /// a Shape creation pattern
        ///</summary>
        private async Task ReplicateListFromAzureAsync()
        {
            string azureTextFileContent = await shapeIndexCloudFile.DownloadTextAsync();

            string[] shapes = azureTextFileContent.Split(new char[] { ',' });

            foreach (string shape in shapes)
            {
                int i;

                Int32.TryParse(shape.ToString(), out i);

                ShapeFactory.instance.shapeHistoryList.Add(i);

                ShapeFactory.instance.CreateShape(i, true);

                await Task.Delay(500);
            }

            Gaze.instance.GazeEnabled = true;

            azureStatusText.text = "Load Complete!";
        }
    ```

7.  在回到 Unity 之前，請先將您的變更儲存在 Visual Studio 中。

## <a name="chapter-11---build-the-uwp-solution"></a>第11章-打造 UWP 解決方案

若要開始建立程式：

1.  移至 **[** 檔案  >  **組建設定**]。

    ![建立應用程式](images/AzureLabs-Lab5-54.png)

2.  按一下 [建置]。 Unity 將會啟動一個 *檔案總管* 視窗，您需要在其中建立並選取要用來建立應用程式的資料夾。 立即建立該資料夾，並命名為 *應用程式*。 然後選取 [ *應用程式* ] 資料夾，然後按 [ **選取資料夾**]。

3.  Unity 將開始將您的專案建立到 *應用程式* 資料夾。

4.  Unity 完成組建之後 (可能需要一些時間) ，它會在您的組建位置開啟 *檔案總管* 視窗 (檢查您的工作列，因為它不一定會出現在您的視窗上方，但會通知您加入新的視窗) 。

## <a name="chapter-12---deploying-your-application"></a>第12章-部署應用程式

若要部署您的應用程式：

1.  流覽至 [上一章](#chapter-11---build-the-uwp-solution)所建立的 *應用程式* 資料夾。 您會看到含有您應用程式名稱的檔案，其中包含 ' .sln ' 副檔名，您應按兩下該檔案，以便在 *Visual Studio* 中開啟。

2.  在 [ **方案平臺**] 中，選取 [ **x86]、[本機電腦**]。

3.  在 [ **方案** 設定] 中選取 [ **Debug**]。

    > 在 Microsoft HoloLens 中，您可能會發現將此設定為 *遠端電腦* 較容易，因此不會行動網卡到您的電腦。 不過，您也必須執行下列動作：
    > - 知道您 HoloLens 的 **IP 位址**，您可以在 **設定**  >  **網路 & 網際網路**  >  **wi-fi**  >  **Advanced Options** 中找到此位址; IPv4 是您應該使用的位址。 
    > - 確定已 **開啟****開發人員模式**;在「**設定** 更新」中找到  >    >  **開發人員的**& 安全性。

    ![部署解決方案](images/AzureLabs-Lab5-55.png)

4.  移至 [ **組建** ] 功能表，然後按一下 [ **部署方案** ]，將應用程式側載至您的電腦。

5.  您的應用程式現在應該會出現在已安裝的應用程式清單中，準備好進行啟動及測試！

## <a name="your-finished-azure-functions-and-storage-application"></a>您完成的 Azure Functions 和儲存應用程式

恭喜您，您建立了一個同時運用 Azure Functions 和 Azure 儲存體服務的混合現實應用程式。 您的應用程式將能夠在儲存的資料上繪製，並根據該資料來提供動作。

![最終產品-結束](images/AzureLabs-Lab5-00.png)

## <a name="bonus-exercises"></a>額外練習

### <a name="exercise-1"></a>練習1

建立第二個產生點，並記錄建立物件的產生點。 當您載入資料檔案時，請重新執行從原本建立的位置產生的圖形。

### <a name="exercise-2"></a>練習2

建立重新開機應用程式的方法，而不需要每次重新開啟應用程式。 **載入場景** 是不錯的起點。 這麼做之後，請建立一個方法來清除 *Azure 儲存體* 中的已儲存清單，讓您可以輕鬆地從應用程式重設。