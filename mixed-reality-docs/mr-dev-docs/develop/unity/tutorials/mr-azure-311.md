---
title: HoloLens (第1代) 和 Azure 311-Microsoft Graph
description: 完成本課程，以瞭解如何利用 Microsoft Graph，並連接到混合現實應用程式中驅動生產力的資料。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure，mixed reality，學院，unity，教學課程，api，microsoft graph，hololens，沉浸，vr，Windows 10，Visual Studio
ms.openlocfilehash: 16fb7853d202c39399b48595a17e7e9b2edf224f18d5e315c5ddcf4a0054d8f7
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2021
ms.locfileid: "115215182"
---
# <a name="hololens-1st-gen-and-azure-311---microsoft-graph"></a>HoloLens (第1代) 和 Azure 311-Microsoft Graph

>[!NOTE]
>混合實境學院教學課程的設計是以 HoloLens (第 1 代) 和混合實境沉浸式頭戴裝置為準。  因此，對於仍在尋找這些裝置開發指引的開發人員而言，我們覺得這些教學課程很重要。  這些教學課程 **_不會_** 使用用於 HoloLens 2 的最新工具組或互動進行更新。  系統會保留這些資訊，以繼續在支援的裝置上運作。 未來將會有一系列新的教學課程，將會示範如何針對 HoloLens 2 進行開發。  當張貼這些教學課程時，將會使用這些教學課程的連結來更新此通知。

在此課程中，您將瞭解如何使用 *Microsoft Graph* ，在混合現實應用程式中使用安全驗證來登入您的 Microsoft 帳戶。 然後，您將會在應用程式介面中取出並顯示已排程的會議。

![](images/AzureLabs-Lab311-00.png)

*Microsoft Graph* 是一組 api，其設計可讓您存取許多 Microsoft 的服務。 Microsoft 將 Microsoft Graph 描述為依關聯性連接的資源矩陣，這表示它可讓應用程式存取各種連線的使用者資料。 如需詳細資訊，請造訪[Microsoft Graph 頁面](https://developer.microsoft.com/graph)。

開發過程中會建立一個應用程式，其中使用者將會被指示，然後點一下球體，這會提示使用者安全地登入 Microsoft 帳戶。 登入他們的帳戶之後，使用者將能夠看到一天排定的會議清單。

完成本課程之後，您將會有 HoloLens 應用程式的混合現實，這將能夠執行下列作業：

1.  使用 [點一下手勢]，並按一下物件，該物件會提示使用者登入 Microsoft 帳戶， (移出應用程式以登入，然後再) 重新登入應用程式。
2.  查看一天排定的會議清單。 

在您的應用程式中，您可以自行決定如何將結果與您的設計整合。 本課程旨在告訴您如何整合 Azure 服務與您的 Unity 專案。 您的工作是使用您在本課程中所得到的知識，來增強您的混合現實應用程式。

## <a name="device-support"></a>裝置支援

<table>
<tr>
<th>課程</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">沉浸式頭戴裝置</a></th>
</tr><tr>
<td> MR 和 Azure 311：Microsoft Graph</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="prerequisites"></a>必要條件

> [!NOTE]
> 本教學課程是專為擁有 Unity 和 c # 基本經驗的開發人員所設計。 另外也請注意，本檔中的必要條件和書面指示，代表在撰寫 (2018 年7月) 時已經過測試和驗證的內容。 You are free to use the latest software, as listed within the [install the tools](../../install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you will find in newer software than what is listed below.

本課程建議您採用下列硬體和軟體：

- 開發電腦
- [啟用開發人員模式的 Windows 10 Fall Creators Update (或更新版本) ](../../install-the-tools.md#installation-checklist)
- [最新的 Windows 10 SDK](../../install-the-tools.md#installation-checklist)
- [Unity 2017。4](../../install-the-tools.md#installation-checklist)
- [Visual Studio 2017](../../install-the-tools.md#installation-checklist)
- 啟用開發人員模式的[Microsoft HoloLens](/hololens/hololens1-hardware)
- 適用于 Azure 設定的網際網路存取，以及 Microsoft Graph 資料抓取
- 有效的 **Microsoft 帳戶** (個人或公司/學校) 
- 使用相同的 Microsoft 帳戶，排定當天的一些會議

### <a name="before-you-start"></a>在您開始使用 Intune 之前

1.  為了避免在建立此專案時發生問題，強烈建議您在根或近端根資料夾中，建立本教學課程中所述的專案 (長的資料夾路徑可能會在組建階段) 時發生問題。
2.  設定及測試您的 HoloLens。 如果您需要設定 HoloLens 的支援，[請務必造訪 HoloLens 安裝程式文章](/hololens/hololens-setup)。 
3.  在開始開發新的 HoloLens 應用程式時，最好先執行校正和感應器調整， (有時它可以協助您為每個使用者) 執行這些工作。 

如需有關校正的說明，請遵循此[連結來 HoloLens 校正文章](/hololens/hololens-calibration#hololens-2)。

如需有關感應器微調的說明，請依照此[連結前往 HoloLens 感應器微調文章](/hololens/hololens-updates)。

## <a name="chapter-1---create-your-app-in-the-application-registration-portal"></a>第1章-在應用程式註冊入口網站中建立您的應用程式

若要開始，您必須在 **應用程式註冊入口網站** 中建立並註冊您的應用程式。

在本章中，您也會找到可讓您呼叫 *Microsoft Graph* 的服務金鑰，以存取您的帳戶內容。

1.  流覽至 [Microsoft 應用程式註冊入口網站](https://apps.dev.microsoft.com) ，並使用您的 Microsoft 帳戶登入。 登入之後，系統會將您重新導向至 **應用程式註冊入口網站**。

2.  在 [ **我的應用程式** ] 區段中，按一下 [ **新增應用程式**] 按鈕。

    ![](images/AzureLabs-Lab311-01.png)![](images/AzureLabs-Lab311-02.png)

    > [!IMPORTANT]
    > **應用程式註冊入口網站** 的外觀可能會不同，取決於您先前是否曾使用 *Microsoft Graph*。 下列螢幕擷取畫面顯示這些不同的版本。

3.  新增應用程式的名稱，然後按一下 [ **建立**]。

    ![](images/AzureLabs-Lab311-03.png)

4.  建立應用程式之後，系統會將您重新導向至應用程式的主頁面。 複製 **應用程式識別碼** ，並務必在安全的位置記下此值，您很快就會在程式碼中使用它。

    ![](images/AzureLabs-Lab311-04.png)

5.  在 [ **平臺** ] 區段中，確認是否顯示 [ **原生應用程式** ]。 如果 *沒有* ，請按一下 [ **新增平臺** ]，然後選取 [ **原生應用程式**]。

    ![](images/AzureLabs-Lab311-05.png)

6.  在相同的頁面上，或在稱為 **Microsoft Graph 許可權** 的區段中向下滾動，您將需要為應用程式新增額外的許可權。 按一下 [**委派的許可權**] 旁的 [**新增**]。

    ![](images/AzureLabs-Lab311-06.png)

7.  因為您想要讓應用程式存取使用者的行事曆，請核取 **稱為 [行事曆** ] 的方塊，然後按一下 **[確定]**。

    ![](images/AzureLabs-Lab311-07.png)

8.  滾動至底部，然後按一下 [ **儲存** ] 按鈕。

    ![](images/AzureLabs-Lab311-08.png)

9.  系統會確認您的儲存，您可以從 **應用程式註冊入口網站** 登出。

## <a name="chapter-2---set-up-the-unity-project"></a>第2章-設定 Unity 專案

以下是使用 mixed reality 進行開發的一般設定，因此，它是適用于其他專案的絕佳範本。

1.  開啟 *Unity* ，然後按一下 [ **新增**]。

    ![](images/AzureLabs-Lab311-09.png)

2.  您必須提供 Unity 專案名稱。 插入 **MSGraphMR**。 請確定專案範本已設定為 **3d**。 將 **位置** 設定為適合您 (記住，較接近根目錄的) 。 然後，按一下 [ **建立專案**]。

    ![](images/AzureLabs-Lab311-10.png)

3.  在 Unity 開啟的情況下，值得檢查預設 **腳本編輯器** 是否設定為 **Visual Studio**。 移至 [**編輯**  >  **喜好** 設定]，然後在新視窗中，流覽至 [**外部工具**]。 將 **外部腳本編輯器** 變更為 **Visual Studio 2017**。 關閉 [ **喜好** 設定] 視窗。

    ![](images/AzureLabs-Lab311-11.png)

4.  移至  >  [檔案 **組建設定** 並選取 [**通用 Windows 平臺**]，然後按一下 [**切換平臺**] 按鈕以套用您的選取專案。

    ![](images/AzureLabs-Lab311-12.png)

5.  當您仍 **在檔案**  >  **組建設定** 中時，請確定：

    1. **目標裝置** 設定為 **HoloLens**
    2. **組建類型** 設定為 **D3D**
    3. **SDK** 已設定為 **最新安裝**
    4. **Visual Studio 版本** 設定為 **最新安裝**
    5. **組建並執行** 設定為 **本機電腦**
    6. 儲存場景，並將其新增至組建。

        1. 若要這麼做，請選取 [ **新增開啟的場景**]。 [儲存] 視窗隨即出現。

            ![](images/AzureLabs-Lab311-13.png)

        2. 為此和任何未來的場景建立新資料夾。 選取 [ **新增資料夾** ] 按鈕，建立新的資料夾，將它命名為 **場景**。

            ![](images/AzureLabs-Lab311-14.png)

        3. 開啟新建立的 **場景** 資料夾，然後在 [ *檔案名*：文字] 欄位中，輸入 **MR_ComputerVisionScene**，然後按一下 [ **儲存**]。

            ![](images/AzureLabs-Lab311-15.png)

            > [!IMPORTANT] 
            > 請注意，您必須將 Unity 場景儲存在 [ *資產* ] 資料夾中，因為它們必須與 Unity 專案相關聯。 建立幕後資料夾 (和其他類似的資料夾) 是結構化 Unity 專案的典型方式。

    7.  [*組建設定*] 中的其餘設定，現在應該保持為預設值。

6.  在 [*組建設定*] 視窗中，按一下 [播放程式]**設定** 按鈕，這會開啟偵測 *器* 所在空間中的相關面板。 

    ![](images/AzureLabs-Lab311-16.png)

7. 在此面板中，需要驗證幾個設定：

    1. 在 [**其他設定**] 索引標籤中：

        1.  **腳本****執行階段版本** 應該是 **實驗** ( .net 4.6 對等) ，這會觸發重新開機編輯器的需求。

        2. **腳本後端** 應該是 **.net**

        3. **API 相容性層級** 應為 **.net 4.6**

            ![](images/AzureLabs-Lab311-17.png)

    2.  在 [**發行設定**] 索引標籤的 [**功能**] 下，選取：

        - **InternetClient**

            ![](images/AzureLabs-Lab311-18.png)

    3.  接下來的面板中，在 **XR 設定** (的 [**發佈設定**) ] 底下，檢查 **支援的虛擬實境**，確認已新增 **Windows Mixed Reality SDK** 。

        ![](images/AzureLabs-Lab311-19.png)

8.  回到 *Build 設定*， *Unity c # 專案* 不再呈現灰色;核取此方塊旁邊的核取方塊。

9.  關閉 [組建設定]  視窗。

10.  儲存場景和 project (**檔**  >  **儲存場景/** 檔案  >  **儲存專案**) 。

## <a name="chapter-3---import-libraries-in-unity"></a>第3章-在 Unity 中匯入程式庫

> [!IMPORTANT]
> 如果您想要略過此課程的 *Unity 設定* 元件，並直接繼續進行程式碼，您可以下載此 [unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20311%20-%20Microsoft%20Graph/Azure-MR-311.unitypackage)、將其匯入您的專案中做為 [**自訂套件**](https://docs.unity3d.com/Manual/AssetPackages.html)，然後繼續進行 [第5章](#chapter-5---create-meetingsui-class)。

若要在 Unity 中使用 *Microsoft Graph* ，您必須使用 **Microsoft 身分識別. 用戶端** DLL。 您可以使用 Microsoft Graph SDK，但在您建立 Unity 專案之後，將需要新增 NuGet 套件， (表示在組建) 後編輯專案。 將所需的 Dll 直接匯入 Unity 會比較容易。

> [!NOTE]
> Unity 中目前有已知的問題，需要在匯入之後重新設定外掛程式。 在解決 bug 之後，將不再需要這一節中的這些步驟 (4-7) 。

若要將 *Microsoft Graph* 匯入您自己的專案，請 [下載 MSGraph_LabPlugins.zip](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20311%20-%20Microsoft%20Graph/MSGraph_LabPlugins.unitypackage)檔。 已使用已測試的程式庫版本建立此套件。

如果您想要深入瞭解如何將自訂 Dll 新增至 Unity 專案，請 [遵循此連結](https://docs.unity3d.com/Manual/UsingDLL.html)。

若要匯入封裝：

1.  使用 [**資產** 匯  >  **入封裝**  >  **自訂套件**] 功能表選項，將 unity 套件新增至 unity。 選取您剛剛下載的套件。

2.  在彈出的 [匯 **入 Unity 套件** ] 方塊中，確定已選取 [ (] 下的所有專案，並包含) **外掛程式** 。

    ![](images/AzureLabs-Lab311-20.png)

3.  按一下 [匯 **入** ] 按鈕，將專案新增至您的專案。

4.  移至 *Project 面板* 中 [**外掛程式**] 下的 [ **MSGraph** ] 資料夾，然後選取名為 [**用戶端**] 的外掛程式。

    ![](images/AzureLabs-Lab311-21.png)

5.  選取 *外掛程式* 之後，請確定已取消選取 **任何平臺** ，然後確定 **WSAPlayer** 也未核取， **然後按一下 [** 套用]。 這只是為了確認檔案已正確設定。

    ![](images/AzureLabs-Lab311-22.png)

    > [!NOTE] 
    > 標記這些外掛程式會將它們設定為只在 Unity 編輯器中使用。 在 [WSA] 資料夾中有一組不同的 dll，會在專案從 Unity 匯出為通用 Windows 應用程式之後使用。

6.  接下來，您需要在 **MSGraph** 資料夾內開啟 [ **WSA** ] 資料夾。 您會看到您剛剛設定的相同檔案的複本。 選取檔案，然後在 [偵測器：

    -   確定未核取 **任何平臺** **，而且****只****檢查** **WSAPlayer** 。

    -   確定已將 **SDK** 設定為 **UWP**，而 **腳本後端** 設定為 **點淨**

    -   確定 **已核** 取 [**不處理**]。

        ![](images/AzureLabs-Lab311-23.png)

7.  按一下 [套用]。

## <a name="chapter-4---camera-setup"></a>第4章-攝影機設定

在本章中，您將設定場景的主要攝影機：

1.  在 [階層] *面板* 中，選取 [ **主要相機**]。

2.  一旦選取之後，您就可以在 [偵測 *器*] 面板中看到 **主要攝影機** 的所有元件。

    1.  **攝影機物件** 必須命名為 **主要攝影機** (請注意拼寫！ ) 

    2.  主要攝影機 **標記** 必須設定為 **MainCamera** (注意拼寫！ ) 

    3.  請確定 **轉換位置** 設定為 **0、0、0**

    4.  將純文字 **旗標** 設為 **純色**

    5.  將相機元件的 **背景色彩** 設定為 **黑色、Alpha 0** **(Hex 碼： #00000000)**

        ![](images/AzureLabs-Lab311-24.png)

3.  階層 *面板* 中的最後一個物件結構應如下圖所示：

    ![](images/AzureLabs-Lab311-25.png)

## <a name="chapter-5---create-meetingsui-class"></a>第5章-建立 MeetingsUI 類別

您需要建立的第一個腳本是 **MeetingsUI**，它負責裝載和填入應用程式的 UI (歡迎訊息、指示和會議詳細資料) 。

若要建立此類別：

1.  在 *Project 面板* 中的 [**資產**] 資料夾上按一下滑鼠右鍵，然後選取 [**建立**  >  **資料夾**]。 將資料夾命名為 **腳本**。

    ![](images/AzureLabs-Lab311-26.png)
    ![](images/AzureLabs-Lab311-27.png)

2.  開啟 [**腳本**] 資料夾，然後在該資料夾中，以滑鼠右鍵按一下 [**建立**  >  **c # 腳本**]。 將腳本命名為 **MeetingsUI。**

    ![](images/AzureLabs-Lab311-28.png)

3.  按兩下新的 **MeetingsUI** 腳本，以 *Visual Studio* 開啟。

4.  插入下列命名空間：

    ```csharp
    using System;
    using UnityEngine;
    ```

5.  在類別內插入下列變數：

    ```csharp    
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static MeetingsUI Instance;

        /// <summary>
        /// The 3D text of the scene
        /// </summary>
        private TextMesh _meetingDisplayTextMesh;
    ```

6.  然後取代 **Start ()** 方法，並加入一個 **喚醒的 ()** 方法。 當類別初始化時，就會呼叫這些內容：

    ```csharp    
        /// <summary>
        /// Called on initialization
        /// </summary>
        void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Called on initialization, after Awake
        /// </summary>
        void Start ()
        {
            // Creating the text mesh within the scene
            _meetingDisplayTextMesh = CreateMeetingsDisplay();
        }
    ```

7.  新增負責建立 *會議 UI* 的方法，並在要求時填入目前的會議：

    ```csharp    
        /// <summary>
        /// Set the welcome message for the user
        /// </summary>
        internal void WelcomeUser(string userName)
        {
            if(!string.IsNullOrEmpty(userName))
            {
                _meetingDisplayTextMesh.text = $"Welcome {userName}";
            }
            else 
            {
                _meetingDisplayTextMesh.text = "Welcome";
            }
        }

        /// <summary>
        /// Set up the parameters for the UI text
        /// </summary>
        /// <returns>Returns the 3D text in the scene</returns>
        private TextMesh CreateMeetingsDisplay()
        {
            GameObject display = new GameObject();
            display.transform.localScale = new Vector3(0.03f, 0.03f, 0.03f);
            display.transform.position = new Vector3(-3.5f, 2f, 9f);
            TextMesh textMesh = display.AddComponent<TextMesh>();
            textMesh.anchor = TextAnchor.MiddleLeft;
            textMesh.alignment = TextAlignment.Left;
            textMesh.fontSize = 80;
            textMesh.text = "Welcome! \nPlease gaze at the button" +
                "\nand use the Tap Gesture to display your meetings";

            return textMesh;
        }

        /// <summary>
        /// Adds a new Meeting in the UI by chaining the existing UI text
        /// </summary>
        internal void AddMeeting(string subject, DateTime dateTime, string location)
        {
            string newText = $"\n{_meetingDisplayTextMesh.text}\n\n Meeting,\nSubject: {subject},\nToday at {dateTime},\nLocation: {location}";

            _meetingDisplayTextMesh.text = newText;
        }
    ```

8. **刪除** **()** 方法的更新，並 **將您的變更儲存** 在 Visual Studio，然後再返回 Unity。 

## <a name="chapter-6---create-the-graph-class"></a>第6章-建立 Graph 類別

下一個要建立的腳本是 **Graph** 腳本。 此腳本負責進行呼叫以驗證使用者，並從使用者的行事曆取出當天的排程會議。

若要建立此類別：

1.  按兩下 [ **腳本** ] 資料夾以開啟它。

2.  在 [**腳本**] 資料夾內按一下滑鼠右鍵，然後按一下 [**建立**  >  **c # 腳本**]。 將腳本命名為 **Graph**。

3.  按兩下腳本，以 Visual Studio 開啟。

4.  插入下列命名空間：

    ```csharp
    using System.Collections.Generic;
    using UnityEngine;
    using Microsoft.Identity.Client;
    using System;
    using System.Threading.Tasks;
    
    #if !UNITY_EDITOR && UNITY_WSA
    using System.Net.Http;
    using System.Net.Http.Headers;
    using Windows.Storage;
    #endif
    ```

    > [!IMPORTANT]
    > 您將會注意到，此腳本中的部分程式碼會包裝在先行[編譯](https://docs.unity3d.com/Manual/PlatformDependentCompilation.html)指示詞周圍，這是為了避免在建立 Visual Studio 的解決方案時，程式庫發生問題。

5.  刪除 [ **開始 ()** ] 並 **更新 ()** 方法，因為它們不會使用。

6.  在 **Graph** 類別外部，插入下列物件，這是將代表每日排定會議的 JSON 物件還原序列化所需的物件：

    ```csharp
    /// <summary>
    /// The object hosting the scheduled meetings
    /// </summary>
    [Serializable]
    public class Rootobject
    {
        public List<Value> value;
    }

    [Serializable]
    public class Value
    {
        public string subject { get; set; }
        public StartTime start { get; set; }
        public Location location { get; set; }
    }

    [Serializable]
    public class StartTime
    {
        public string dateTime;

        private DateTime? _startDateTime;
        public DateTime StartDateTime
        {
            get
            {
                if (_startDateTime != null)
                    return _startDateTime.Value;
                DateTime dt;
                DateTime.TryParse(dateTime, out dt);
                _startDateTime = dt;
                return _startDateTime.Value;
            }
        }
    }

    [Serializable]
    public class Location
    {
        public string displayName { get; set; }
    }
    ```

7.  在 **Graph** 類別內，新增下列變數：

    ```csharp    
        /// <summary>
        /// Insert your Application Id here
        /// </summary>
        private string _appId = "-- Insert your Application Id here --";

        /// <summary>
        /// Application scopes, determine Microsoft Graph accessibility level to user account
        /// </summary>
        private IEnumerable<string> _scopes = new List<string>() { "User.Read", "Calendars.Read" };

        /// <summary>
        /// Microsoft Graph API, user reference
        /// </summary>
        private PublicClientApplication _client;

        /// <summary>
        /// Microsoft Graph API, authentication
        /// </summary>
        private AuthenticationResult _authResult;

    ```

    > [!NOTE]
    > 將 [ **appId** ] 值變更為您在 **第 [1 章](#chapter-1---create-your-app-in-the-application-registration-portal)步驟 4** 中記下的 **應用程式識別碼**。 此值應與應用程式註冊 **入口網站** 的應用程式註冊頁面中顯示的值相同。

8.  在 **Graph** 類別中，新增 **SignInAsync ()** 和 **AquireTokenAsync ()** 的方法，這會提示使用者插入登入認證。

    ```csharp
        /// <summary>
        /// Begin the Sign In process using Microsoft Graph Library
        /// </summary>
        internal async void SignInAsync()
        {
    #if !UNITY_EDITOR && UNITY_WSA
            // Set up Grap user settings, determine if needs auth
            ApplicationDataContainer localSettings = ApplicationData.Current.LocalSettings;
            string userId = localSettings.Values["UserId"] as string;
            _client = new PublicClientApplication(_appId);

            // Attempt authentication
            _authResult = await AcquireTokenAsync(_client, _scopes, userId);

            // If authentication is successful, retrieve the meetings
            if (!string.IsNullOrEmpty(_authResult.AccessToken))
            {
                // Once Auth as been completed, find the meetings for the day
                await ListMeetingsAsync(_authResult.AccessToken);
            }
    #endif
        }

        /// <summary>
        /// Attempt to retrieve the Access Token by either retrieving
        /// previously stored credentials or by prompting user to Login
        /// </summary>
        private async Task<AuthenticationResult> AcquireTokenAsync(
            IPublicClientApplication app, IEnumerable<string> scopes, string userId)
        {
            IUser user = !string.IsNullOrEmpty(userId) ? app.GetUser(userId) : null;
            string userName = user != null ? user.Name : "null";

            // Once the User name is found, display it as a welcome message
            MeetingsUI.Instance.WelcomeUser(userName);

            // Attempt to Log In the user with a pre-stored token. Only happens
            // in case the user Logged In with this app on this device previously
            try
            {
                _authResult = await app.AcquireTokenSilentAsync(scopes, user);
            }
            catch (MsalUiRequiredException)
            {
                // Pre-stored token not found, prompt the user to log-in 
                try
                {
                    _authResult = await app.AcquireTokenAsync(scopes);
                }
                catch (MsalException msalex)
                {
                    Debug.Log($"Error Acquiring Token: {msalex.Message}");
                    return _authResult;
                }
            }
            
            MeetingsUI.Instance.WelcomeUser(_authResult.User.Name);

    #if !UNITY_EDITOR && UNITY_WSA
            ApplicationData.Current.LocalSettings.Values["UserId"] = 
            _authResult.User.Identifier;
    #endif
            return _authResult;
        }
    ```

9.  新增下列兩個方法：

    1.  **BuildTodayCalendarEndpoint ()**，其會建立指定日期和時間範圍的 URI，並在其中抓取排定的會議。

    2.  **ListMeetingsAsync ()**，這會要求 *Microsoft Graph* 的排程會議。

    ```csharp
        /// <summary>
        /// Build the endpoint to retrieve the meetings for the current day.
        /// </summary>
        /// <returns>Returns the Calendar Endpoint</returns>
        public string BuildTodayCalendarEndpoint()
        {
            DateTime startOfTheDay = DateTime.Today.AddDays(0);
            DateTime endOfTheDay = DateTime.Today.AddDays(1);
            DateTime startOfTheDayUTC = startOfTheDay.ToUniversalTime();
            DateTime endOfTheDayUTC = endOfTheDay.ToUniversalTime();

            string todayDate = startOfTheDayUTC.ToString("o");
            string tomorrowDate = endOfTheDayUTC.ToString("o");
            string todayCalendarEndpoint = string.Format(
                "https://graph.microsoft.com/v1.0/me/calendarview?startdatetime={0}&enddatetime={1}",
                todayDate,
                tomorrowDate);

            return todayCalendarEndpoint;
        }

        /// <summary>
        /// Request all the scheduled meetings for the current day.
        /// </summary>
        private async Task ListMeetingsAsync(string accessToken)
        {
    #if !UNITY_EDITOR && UNITY_WSA
            var http = new HttpClient();

            http.DefaultRequestHeaders.Authorization = 
            new AuthenticationHeaderValue("Bearer", accessToken);
            var response = await http.GetAsync(BuildTodayCalendarEndpoint());

            var jsonResponse = await response.Content.ReadAsStringAsync();

            Rootobject rootObject = new Rootobject();
            try
            {
                // Parse the JSON response.
                rootObject = JsonUtility.FromJson<Rootobject>(jsonResponse);

                // Sort the meeting list by starting time.
                rootObject.value.Sort((x, y) => DateTime.Compare(x.start.StartDateTime, y.start.StartDateTime));

                // Populate the UI with the meetings.
                for (int i = 0; i < rootObject.value.Count; i++)
                {
                    MeetingsUI.Instance.AddMeeting(rootObject.value[i].subject,
                                                rootObject.value[i].start.StartDateTime.ToLocalTime(),
                                                rootObject.value[i].location.displayName);
                }
            }
            catch (Exception ex)
            {
                Debug.Log($"Error = {ex.Message}");
                return;
            }
    #endif
        }
    ```

10. 您現在已完成 **Graph** 腳本。 在回到 Unity 之前，請先 **將您的變更儲存** 在 Visual Studio 中。

## <a name="chapter-7---create-the-gazeinput-script"></a>第7章-建立 GazeInput 腳本

您現在將建立 **GazeInput**。 這個類別會使用來自 **主要攝影機** 的 **Raycast** 來處理並追蹤使用者的注視，以向前投射。

建立指令碼：

1.  按兩下 [ **腳本** ] 資料夾以開啟它。

2.  在 [**腳本**] 資料夾內按一下滑鼠右鍵，然後按一下 [**建立**  >  **c # 腳本**]。 將腳本命名為 **GazeInput**。

3.  按兩下腳本，以 Visual Studio 開啟。

4.  將命名空間的程式碼變更為符合下面的程式碼，並在您的 **GazeInput** 類別之上新增 **\[ \] ' system.string ' 標記**，以便將它序列化：

    ```csharp
    using UnityEngine;

    /// <summary>
    /// Class responsible for the User's Gaze interactions
    /// </summary>
    [System.Serializable]
    public class GazeInput : MonoBehaviour
    {
    ```

5.  在 **GazeInput** 類別中，新增下列變數：

    ```csharp    
        [Tooltip("Used to compare whether an object is to be interacted with.")]
        internal string InteractibleTag = "SignInButton";

        /// <summary>
        /// Length of the gaze
        /// </summary>
        internal float GazeMaxDistance = 300;

        /// <summary>
        /// Object currently gazed
        /// </summary>
        internal GameObject FocusedObject { get; private set; }

        internal GameObject oldFocusedObject { get; private set; }

        internal RaycastHit HitInfo { get; private set; }

        /// <summary>
        /// Cursor object visible in the scene
        /// </summary>
        internal GameObject Cursor { get; private set; }

        internal bool Hit { get; private set; }

        internal Vector3 Position { get; private set; }

        internal Vector3 Normal { get; private set; }

        private Vector3 _gazeOrigin;

        private Vector3 _gazeDirection;
    ```

6.  新增 **CreateCursor ()** 方法，以在場景中建立 HoloLens 資料指標，並從 **Start ()** 方法呼叫方法：

    ```csharp    
        /// <summary>
        /// Start method used upon initialisation.
        /// </summary>
        internal virtual void Start()
        {
            FocusedObject = null;
            Cursor = CreateCursor();
        }

        /// <summary>
        /// Method to create a cursor object.
        /// </summary>
        internal GameObject CreateCursor()
        {
            GameObject newCursor = GameObject.CreatePrimitive(PrimitiveType.Sphere);
            newCursor.SetActive(false);
            // Remove the collider, so it doesn't block raycast.
            Destroy(newCursor.GetComponent<SphereCollider>());
            newCursor.transform.localScale = new Vector3(0.05f, 0.05f, 0.05f);
            Material mat = new Material(Shader.Find("Diffuse"));
            newCursor.GetComponent<MeshRenderer>().material = mat;
            mat.color = Color.HSVToRGB(0.0223f, 0.7922f, 1.000f);
            newCursor.SetActive(true);

            return newCursor;
        }
    ```

7.  下列方法會啟用注視 Raycast 並追蹤焦點物件。

    ```csharp
    /// <summary>
    /// Called every frame
    /// </summary>
    internal virtual void Update()
    {
        _gazeOrigin = Camera.main.transform.position;

        _gazeDirection = Camera.main.transform.forward;

        UpdateRaycast();
    }
    /// <summary>
    /// Reset the old focused object, stop the gaze timer, and send data if it
    /// is greater than one.
    /// </summary>
    private void ResetFocusedObject()
    {
        // Ensure the old focused object is not null.
        if (oldFocusedObject != null)
        {
            if (oldFocusedObject.CompareTag(InteractibleTag))
            {
                // Provide the 'Gaze Exited' event.
                oldFocusedObject.SendMessage("OnGazeExited", SendMessageOptions.DontRequireReceiver);
            }
        }
    }
    ```

    ```csharp
        private void UpdateRaycast()
        {
            // Set the old focused gameobject.
            oldFocusedObject = FocusedObject;
            RaycastHit hitInfo;

            // Initialise Raycasting.
            Hit = Physics.Raycast(_gazeOrigin,
                _gazeDirection,
                out hitInfo,
                GazeMaxDistance);
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

            // Check whether the previous focused object is this same. If so, reset the focused object.
            if (FocusedObject != oldFocusedObject)
            {
                ResetFocusedObject();
                if (FocusedObject != null)
                {
                    if (FocusedObject.CompareTag(InteractibleTag))
                    {
                        // Provide the 'Gaze Entered' event.
                        FocusedObject.SendMessage("OnGazeEntered", 
                            SendMessageOptions.DontRequireReceiver);
                    }
                }
            }
        }
    ```

8.  在回到 Unity 之前，請先 **將您的變更儲存** 在 Visual Studio 中。

## <a name="chapter-8---create-the-interactions-class"></a>第8章-建立互動類別

您現在將需要建立 **互動** 腳本，其負責：

-   處理點 **一下互動和****攝影機注視**，可讓使用者與場景中的「按鈕」進行互動。

-   在場景中建立登入「按鈕」物件，讓使用者能夠與之互動。

建立指令碼：

1.  按兩下 [ **腳本** ] 資料夾以開啟它。

2.  在 [**腳本**] 資料夾內按一下滑鼠右鍵，然後按一下 [**建立**  >  **c # 腳本**]。 命名腳本的 **互動**。

3.  按兩下腳本，以 Visual Studio 開啟。

4.  插入下列命名空間：

    ```csharp
    using UnityEngine;
    using UnityEngine.XR.WSA.Input;
    ```

5.  將 **互動** 類別的繼承從 *MonoBehaviour* 變更為 **GazeInput**。

    ~~公用類別互動： MonoBehaviour~~

    ```csharp
    public class Interactions : GazeInput
    ```

6.  在 **互動** 類別中插入下列變數：

    ```csharp
        /// <summary>
        /// Allows input recognition with the HoloLens
        /// </summary>
        private GestureRecognizer _gestureRecognizer;
    ```

7.  取代 **Start** 方法;請注意，它是一個覆寫方法，它會呼叫「基底」注視類別方法。 **啟動 ()** 會在類別初始化時呼叫，並在場景中註冊輸入辨識和建立登入 *按鈕* ：

    ```csharp    
        /// <summary>
        /// Called on initialization, after Awake
        /// </summary>
        internal override void Start()
        {
            base.Start();

            // Register the application to recognize HoloLens user inputs
            _gestureRecognizer = new GestureRecognizer();
            _gestureRecognizer.SetRecognizableGestures(GestureSettings.Tap);
            _gestureRecognizer.Tapped += GestureRecognizer_Tapped;
            _gestureRecognizer.StartCapturingGestures();

            // Add the Graph script to this object
            gameObject.AddComponent<MeetingsUI>();
            CreateSignInButton();
        }
    ```

8.  新增 **CreateSignInButton ()** 方法，這會將場景中的登入 *按鈕* 具現化，並設定其屬性：

    ```csharp    
        /// <summary>
        /// Create the sign in button object in the scene
        /// and sets its properties
        /// </summary>
        void CreateSignInButton()
        {
            GameObject signInButton = GameObject.CreatePrimitive(PrimitiveType.Sphere);

            Material mat = new Material(Shader.Find("Diffuse"));
            signInButton.GetComponent<Renderer>().material = mat;
            mat.color = Color.blue;

            signInButton.transform.position = new Vector3(3.5f, 2f, 9f);
            signInButton.tag = "SignInButton";
            signInButton.AddComponent<Graph>();
        }
    ```

9.  新增 **GestureRecognizer_Tapped 的 ()** 方法，其會回應 *分攻* 使用者事件。

    ```csharp   
        /// <summary>
        /// Detects the User Tap Input
        /// </summary>
        private void GestureRecognizer_Tapped(TappedEventArgs obj)
        {
            if(base.FocusedObject != null)
            {
                Debug.Log($"TAP on {base.FocusedObject.name}");
                base.FocusedObject.SendMessage("SignInAsync", SendMessageOptions.RequireReceiver);
            }
        }
    ```

10. **刪除** () 方法的 **更新**，然後 **將變更儲存** 在 Visual Studio，然後再返回 Unity。

## <a name="chapter-9---set-up-the-script-references"></a>第9章-設定腳本參考

在本章中，您必須將 **互動** 腳本放在 **主要攝影機** 上。 該腳本接著會處理將其他腳本放在需要的位置。

-  從 *Project 面板* 中的 [**腳本**] 資料夾，將腳本 **互動** 拖曳至 **主要攝影機** 物件，如下圖所示。

    ![](images/AzureLabs-Lab311-29.png)

## <a name="chapter-10---setting-up-the-tag"></a>第10章-設定標記

處理注視的程式碼會使用標記 **SignInButton** 來識別使用者將與之互動以登入 *Microsoft Graph* 的物件。

若要建立標記：

1.  在 Unity 編輯器中，按一下 [階層]*面板* 中的 **主要攝影機**。

2.  在 [偵測 *器] 面板* 中，按一下 [ **MainCamera** ] *標記* 以開啟下拉式清單。 按一下 [**新增標記**]。

    ![](images/AzureLabs-Lab311-30.png)

3.  按一下 **+** 按鈕。

    ![](images/AzureLabs-Lab311-31.png)

4.  以 **SignInButton** 的形式寫入標記名稱，然後按一下 [儲存]。

    ![](images/AzureLabs-Lab311-32.png)

## <a name="chapter-11---build-the-unity-project-to-uwp"></a>第11章-將 Unity 專案建立到 UWP

此專案的 Unity 區段所需的所有專案現在都已完成，因此您可以從 Unity 建立它。

1.  流覽至 *build 設定* ( **File* > * build 設定 * * ) 。

    ![](images/AzureLabs-Lab311-33.png)

2.  如果尚未這麼做，請勾選 **Unity C \# 專案**。

3.  按一下 [建置]。 Unity 將會啟動一個 **檔案總管** 視窗，您需要在其中建立並選取要用來建立應用程式的資料夾。 立即建立該資料夾，並命名為 **應用程式**。 然後選取 [ **應用程式** ] 資料夾，然後按一下 [ **選取資料夾**]。

4.  Unity 將開始將您的專案建立到 **應用程式** 資料夾。

5.  Unity 完成組建之後 (可能需要一些時間) ，它會在您的組建位置開啟 **檔案總管** 視窗 (檢查您的工作列，因為它不一定會出現在您的視窗上方，但會通知您加入新的視窗) 。

## <a name="chapter-12---deploy-to-hololens"></a>第12章-部署到 HoloLens

若要在 HoloLens 上部署：

1.  您需要 HoloLens (的 IP 位址，才能進行遠端部署) ，並確保您的 HoloLens 處於 **開發人員模式。** 若要這樣做：

    1.  在 HoloLens 時，請開啟 **設定**。

    2.  前往 **Network & Internet**  >  **wi-fi**  >  **Advanced Options**

    3.  記下 **IPv4** 位址。

    4.  接下來，流覽回到 **設定**，然後為開發 **人員更新 & 安全性**  >  

    5.  設定 [ **開發人員模式]**。

2.  流覽至您的新 Unity 組建 (**應用程式** 資料夾) ，然後以 **Visual Studio** 開啟方案檔。

3.  在 [ **方案** 設定] 中選取 [ **Debug**]。

4.  在 **解決方案平臺** 中，選取 [ **x86]、[遠端電腦**]。 系統會提示您 (HoloLens 中插入遠端裝置的 **IP 位址**，在此案例中，您記) 。

    ![](images/AzureLabs-Lab311-34.png)

5.  移至 [**組建**] 功能表，然後按一下 [**部署方案**]，將應用程式側載到您的 HoloLens。

6.  您的應用程式現在應該會出現在您 HoloLens 上已安裝的應用程式清單中，準備好可供啟動！

## <a name="your-microsoft-graph-hololens-application"></a>您 Microsoft Graph HoloLens 應用程式

恭喜，您建立了一個利用 Microsoft Graph 的混合現實應用程式來讀取和顯示使用者行事歷數據。

![](images/AzureLabs-Lab311-00.png)

## <a name="bonus-exercises"></a>額外練習

### <a name="exercise-1"></a>練習 1

使用 Microsoft Graph 來顯示使用者的其他資訊

-   使用者電子郵件/電話號碼/個人資料圖片

### <a name="exercise-1"></a>練習 1

執行語音控制，以流覽 Microsoft Graph UI。