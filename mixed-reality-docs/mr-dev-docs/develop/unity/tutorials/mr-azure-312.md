---
title: HoloLens (第1代) 和 Azure 312-Bot 整合
description: 完成本課程，以瞭解如何使用 Microsoft Bot Framework v4 來建立和部署 bot，並在混合現實應用程式中與其通訊。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure，mixed reality，學術，unity，教學課程，api，電腦視覺，hololens，沉浸，vr，microsoft bot framework v4，web 應用程式 bot，bot framework，microsoft bot，Windows 10，Visual Studio
ms.openlocfilehash: 5bef129b9ccbbba6bf2bce835bd1567d4f596932
ms.sourcegitcommit: 35bd43624be33afdb1bf6ba4ddbe36d268eb9bda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/20/2021
ms.locfileid: "104730315"
---
# <a name="hololens-1st-gen-and-azure-312-bot-integration"></a>HoloLens (第1代) 和 Azure 312： Bot 整合

>[!NOTE]
>混合實境學院教學課程的設計是以 HoloLens (第 1 代) 和混合實境沉浸式頭戴裝置為準。  因此，對於仍在尋找這些裝置開發指引的開發人員而言，我們覺得這些教學課程很重要。  這些教學課程 **_不會_** 使用用於 HoloLens 2 的最新工具組或互動進行更新。  系統會保留這些資訊，以繼續在支援的裝置上運作。 未來將會有一系列新的教學課程，將會示範如何針對 HoloLens 2 進行開發。  當張貼這些教學課程時，將會使用這些教學課程的連結來更新此通知。

在此課程中，您將瞭解如何使用 Microsoft Bot Framework V4 來建立和部署 bot，並透過 Windows Mixed Reality 應用程式與其進行通訊。 

![](images/AzureLabs-Lab312-00.png)

**Microsoft Bot Framework V4** 是一組 api，旨在為開發人員提供工具，以建立可擴充且可調整的 Bot 應用程式。 如需詳細資訊，請造訪 [Microsoft Bot Framework 頁面](https://dev.botframework.com/) 或 [V4 Git 儲存](https://github.com/Microsoft/botbuilder-dotnet/wiki)機制。

完成本課程之後，您將會建立 Windows Mixed Reality 的應用程式，讓您能夠執行下列作業：

1. 使用點一下 **手勢** 來啟動接聽使用者語音的 bot。
2. 當使用者已說過某個問題時，bot 會嘗試提供回應。
3. 在 Unity 場景中，以文字（位於 bot 附近）顯示 bot 回復。

在您的應用程式中，您可以自行決定如何將結果與您的設計整合。 本課程旨在告訴您如何整合 Azure 服務與您的 Unity 專案。 您的工作是使用您在本課程中所得到的知識，來增強您的混合現實應用程式。

## <a name="device-support"></a>裝置支援

<table>
<tr>
<th>課程</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">沉浸式頭戴裝置</a></th>
</tr><tr>
<td> MR 和 Azure 312：Bot 整合</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
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
- 適用于 Azure 的網際網路存取，以及適用于 Azure Bot 抓取的網際網路存取。 如需詳細資訊， [請遵循此連結](https://dev.botframework.com/)。

### <a name="before-you-start"></a>在您開始使用 Intune 之前

1.  為了避免在建立此專案時發生問題，強烈建議您在根或近端根資料夾中，建立本教學課程中所述的專案 (長的資料夾路徑可能會在組建階段) 時發生問題。
2.  設定及測試 HoloLens。 如果您需要設定 HoloLens 的支援， [請務必造訪 HoloLens 安裝文章](/hololens/hololens-setup)。 
3.  開始開發新的 HoloLens 應用程式時，最好先執行校正和感應器調整， (有時它可以協助針對每個使用者) 執行這些工作。 

如需有關校正的說明，請遵循此 [與 HoloLens 校正文章相關的連結](/hololens/hololens-calibration#hololens-2)。

如需有關感應器微調的說明，請依照此 [連結來進行「HoloLens 感應器微調」文章](/hololens/hololens-updates)。

## <a name="chapter-1--create-the-bot-application"></a>第1章-建立 Bot 應用程式

第一個步驟是將您的 bot 建立為本機 ASP.Net Core Web 應用程式。 完成並測試之後，您會將它發佈至 Azure 入口網站。

1.  開啟 Visual Studio。 建立新的專案，選取 [ **ASP NET Core Web 應用程式** ] 作為專案類型 (您將會在 [.Net) Core] 子區段下找到它，並將其命名為 **MyBot**。 按一下 [確定]  。

2.  在將出現的視窗中，選取 [ **空白**]。 此外，請確定目標設定為 [ **ASP NET Core 2.0** ]，並將 [驗證] 設定為 [ **無驗證**]。 按一下 [確定]  。  

    ![建立 bot 應用程式](images/AzureLabs-Lab312-01.png)

3.  方案現在將會開啟。 以滑鼠右鍵按一下 **方案總管** 中的 [方案 **Mybot** ]，然後按一下 [**管理方案的 NuGet 套件**]。 

    ![建立 Bot 應用程式](images/AzureLabs-Lab312-02.png)

4.  在 [ **流覽** ] 索引標籤中， **搜尋 (確定** 您已核取 [ **包含發行前版本** ]) 。 選取套件版本 **4.0.1-preview**，然後將專案方塊勾選。 然後按一下 [ **安裝**]。 您現在已安裝 **Bot Framework v4** 所需的程式庫。 關閉 [NuGet] 頁面。

    ![建立 bot 應用程式](images/AzureLabs-Lab312-03.png)

5.  以滑鼠右鍵按一下您在方案總管 **中的***專案*， 然後按一下 [**加入** **|** **類別**]。

    ![建立 Bot 應用程式](images/AzureLabs-Lab312-04.png)

6.  將類別命名為 **MyBot** ，然後按一下 [ **新增**]。

    ![建立 bot 應用程式](images/AzureLabs-Lab312-05.png)

7.  重複先前的點，以建立另一個名為 **ConversationCoNtext** 的類別。 

8.  以滑鼠右鍵按一下 **方案總管** 中的 **wwwroot** ，然後按一下 [**加入** **|** **新專案**]。 選取 [  **HTML 網頁** ] (您將會在 Web) 小節下找到它。 將檔案命名為 **default.html**。 按一下 **[新增]** 。

    ![建立 bot 應用程式](images/AzureLabs-Lab312-06.png)

9.  **方案總管** 中的類別/物件清單應如下圖所示。

    ![建立 bot 應用程式](images/AzureLabs-Lab312-07.png)

10. 按兩下 **ConversationCoNtext** 類別。 此類別負責保存 bot 用來維護交談內容的變數。 這些交談內容值會保留在這個類別的實例中，因為每次收到活動時， **MyBot** 類別的任何實例都會重新整理。 將下列程式碼新增至類別：

    ```csharp
    namespace MyBot
    {
        public static class ConversationContext
        {
            internal static string userName;

            internal static string userMsg;
        }
    }
    ```

11. 按兩下 **MyBot** 類別。 此類別會裝載客戶的任何傳入活動所呼叫的處理常式。 在此類別中，您將會新增用來建立 bot 與客戶之間交談的程式碼。 如先前所述，每次收到活動時，就會初始化這個類別的實例。 將下列程式碼新增至此類別：

    ```csharp
    using Microsoft.Bot;
    using Microsoft.Bot.Builder;
    using Microsoft.Bot.Schema;
    using System.Threading.Tasks;

    namespace MyBot
    {
        public class MyBot : IBot
        {       
            public async Task OnTurn(ITurnContext context)
            {
                ConversationContext.userMsg = context.Activity.Text;

                if (context.Activity.Type is ActivityTypes.Message)
                {
                    if (string.IsNullOrEmpty(ConversationContext.userName))
                    {
                        ConversationContext.userName = ConversationContext.userMsg;
                        await context.SendActivity($"Hello {ConversationContext.userName}. Looks like today it is going to rain. \nLuckily I have umbrellas and waterproof jackets to sell!");
                    }
                    else
                    {
                        if (ConversationContext.userMsg.Contains("how much"))
                        {
                            if (ConversationContext.userMsg.Contains("umbrella")) await context.SendActivity($"Umbrellas are $13.");
                            else if (ConversationContext.userMsg.Contains("jacket")) await context.SendActivity($"Waterproof jackets are $30.");
                            else await context.SendActivity($"Umbrellas are $13. \nWaterproof jackets are $30.");
                        }
                        else if (ConversationContext.userMsg.Contains("color") || ConversationContext.userMsg.Contains("colour"))
                        {
                            await context.SendActivity($"Umbrellas are black. \nWaterproof jackets are yellow.");
                        }
                        else
                        {
                            await context.SendActivity($"Sorry {ConversationContext.userName}. I did not understand the question");
                        }
                    }
                }
                else
                {

                    ConversationContext.userMsg = string.Empty;
                    ConversationContext.userName = string.Empty;
                    await context.SendActivity($"Welcome! \nI am the Weather Shop Bot \nWhat is your name?");
                }

            }
        }
    }
    ```

12. 按兩下 **啟動** 類別。 此類別會初始化 bot。 將下列程式碼新增至類別：

    ```csharp
    using Microsoft.AspNetCore.Builder;
    using Microsoft.AspNetCore.Hosting;
    using Microsoft.Bot.Builder.BotFramework;
    using Microsoft.Bot.Builder.Integration.AspNet.Core;
    using Microsoft.Extensions.Configuration;
    using Microsoft.Extensions.DependencyInjection;

    namespace MyBot
    {
    public class Startup
        {
            public IConfiguration Configuration { get; }

            public Startup(IHostingEnvironment env)
            {
                var builder = new ConfigurationBuilder()
                    .SetBasePath(env.ContentRootPath)
                    .AddJsonFile("appsettings.json", optional: true, reloadOnChange: true)
                    .AddJsonFile($"appsettings.{env.EnvironmentName}.json", optional: true)
                    .AddEnvironmentVariables();
                Configuration = builder.Build();
            }

            // This method gets called by the runtime. Use this method to add services to the container.
            public void ConfigureServices(IServiceCollection services)
            {
                services.AddSingleton(_ => Configuration);
                services.AddBot<MyBot>(options =>
                {
                    options.CredentialProvider = new ConfigurationCredentialProvider(Configuration);
                });
            }

            // This method gets called by the runtime. Use this method to configure the HTTP request pipeline.
            public void Configure(IApplicationBuilder app, IHostingEnvironment env)
            {
                if (env.IsDevelopment())
                {
                    app.UseDeveloperExceptionPage();
                }

                app.UseDefaultFiles();
                app.UseStaticFiles();
                app.UseBotFramework();
            }
        }
    }
    ```

13. 開啟 Program 類別檔案，並確認其中的 **程式** 代碼與下列相同：

    ```csharp
    using Microsoft.AspNetCore;
    using Microsoft.AspNetCore.Hosting;

    namespace MyBot
    {
        public class Program
        {
            public static void Main(string[] args)
            {
                BuildWebHost(args).Run();
            }

            public static IWebHost BuildWebHost(string[] args) =>
                WebHost.CreateDefaultBuilder(args)
                    .UseStartup<Startup>()
                    .Build();
        }
    }
    ```

14. 請記得儲存您的變更 **，若要** 這樣做，請  >  從 Visual Studio 頂端的工具列中，移至 [**全部儲存**]。

## <a name="chapter-2---create-the-azure-bot-service"></a>第2章-建立 Azure Bot Service

既然您已建立 bot 的程式碼，您必須將它發佈至 Azure 入口網站上的 *Web 應用程式 bot* 服務實例。 本章將示範如何在 Azure 上建立及設定 Bot 服務，然後將您的程式碼發佈至該服務。

1.  首先，登入 Azure 入口網站 (https://portal.azure.com) 。 

    1. 如果您還沒有 Azure 帳戶，您將需要建立一個帳戶。 如果您在課堂或實驗室的情況下進行本教學課程，請洽詢講師或其中一個 proctors，協助您設定新的帳戶。

2.  登入後，按一下左上角的 [ **建立資源** ]，並搜尋 *Web 應用程式 bot*，然後按一下 **Enter**。

    ![建立 Azure Bot 服務](images/AzureLabs-Lab312-08.png)
 
3.  新頁面將提供 *Web 應用程式 Bot* 服務的描述。 在此頁面的左下方，選取 [ **建立** ] 按鈕，以建立與此服務的關聯。

    ![建立 Azure Bot 服務](images/AzureLabs-Lab312-09.png)
 
4.  當您按一下 [ **建立**] 之後：

    1. 為此服務實例插入您想要的 **名稱** 。
    2. 選取 [訂用帳戶]  。
    3. 選擇資源群組，或建立一個新的 **資源群組** 。 資源群組提供一種方式來監視、控制存取、布建及管理 Azure 資產集合的計費。 建議您保留與單一專案相關聯的所有 Azure 服務 (例如，) 一般資源群組下的這些課程) 。

        > 如果您想要閱讀更多有關 Azure 資源群組的資訊， [請遵循此連結](/azure/azure-resource-manager/resource-group-portal)

    4. 如果您要建立新的資源群組) ，請判斷資源群組 (的位置。 位置最好是在應用程式執行所在的區域中。 某些 Azure 資產僅適用于某些區域。
    5. 選取適合您的 **定價層** ，如果這是您第一次建立 *Web 應用程式 Bot* 服務，則應可使用名為 F0) 的免費層 (
    6. **應用程式名稱** 可以與 *Bot 名稱* 一樣保持不變。 
    7. 將 *Bot 範本* 保留為 **基本 (c # )**。
    8. *App service 方案/位置* 應該已自動填入您的帳戶。
    9. 設定您想要用來裝載 Bot 的 **Azure 儲存體** 。 如果您還沒有帳戶，可以在此建立。
    10. 您也必須確認您已瞭解套用到此服務的條款及條件。
    11. 按一下 [建立]。
 
        ![建立 Azure Bot 服務](images/AzureLabs-Lab312-10.png)

5.  當您按一下 [ **建立**] 之後，就必須等待服務建立完成，這可能需要一分鐘的時間。

6.  建立服務實例之後，入口網站中就會出現通知。

    ![建立 Azure Bot 服務](images/AzureLabs-Lab312-11.png) 
 
7.  按一下通知以探索新的服務實例。 

    ![建立 Azure Bot 服務](images/AzureLabs-Lab312-12.png)
 
8. 按一下通知中的 [ **移至資源** ] 按鈕，以流覽您的新服務實例。 您將會進入新的 Azure 服務實例。 

    ![建立 Azure Bot 服務](images/AzureLabs-Lab312-13.png)
 
9.  此時您必須設定稱為 **Direct Line** 的功能，讓您的用戶端應用程式能夠與此 Bot 服務進行通訊。 按一下 [ **頻道**]，然後在 [ **新增精選頻道** ] 區段中，按一下 [ **設定 Direct Line 頻道**]。

    ![建立 Azure Bot 服務](images/AzureLabs-Lab312-14.png)

10. 在此頁面中，您會找到可讓用戶端應用程式使用 bot 進行驗證的 **秘密金鑰** 。 按一下 [ **顯示** ] 按鈕並複製其中一個所顯示的按鍵，因為您稍後會在專案中使用。 

    ![建立 Azure Bot 服務](images/AzureLabs-Lab312-15.png)

## <a name="chapter-3--publish-the-bot-to-the-azure-web-app-bot-service"></a>第3章-將 Bot 發佈至 Azure Web 應用程式 Bot 服務

現在您的服務已準備就緒，您必須將先前建立的 Bot 程式碼發佈至新建立的 Web 應用程式 Bot 服務。

> [!NOTE] 
> 您必須在每次對 Bot 解決方案/程式碼進行變更時，將 Bot 發佈至 Azure 服務。

1.  返回您先前建立的 Visual Studio 解決方案。 
2.  以滑鼠右鍵按一下 **MyBot** 專案，在 **方案總管** 中，按一下 [ **發行**]。

    ![將 Bot 發佈至 Azure Web 應用程式 Bot 服務](images/AzureLabs-Lab312-16.png)

3.  在 [ *挑選發行目標* ] 頁面上，按一下 [ **App Service**]，然後 **選取 [現有** 的]，最後按一下 [ **建立設定檔** ] (您可能需要按一下 [ *發佈* ] 按鈕旁的下拉式箭號（如果沒有顯示) ）。

    ![將 Bot 發佈至 Azure Web 應用程式 Bot 服務](images/AzureLabs-Lab312-17.png)

4. 如果您尚未登入您的 Microsoft 帳戶，您必須在此進行。
5. 在 [**發佈**] 頁面上，您將會發現必須設定用於 *Web 應用程式 Bot* 服務建立的相同 **訂** 用帳戶。 然後，將 **View** 設定為 **資源群組** ，然後在下拉式資料夾結構中，選取您先前建立的 **資源群組** 。 按一下 [確定]  。 

    ![將 Bot 發佈至 Azure Web 應用程式 Bot 服務](images/AzureLabs-Lab312-18.png)

6.  現在按一下 [ **發佈** ] 按鈕，並等候 Bot 發佈 (可能需要幾分鐘的時間) 。

    ![將 Bot 發佈至 Azure Web 應用程式 Bot 服務](images/AzureLabs-Lab312-19.png)


## <a name="chapter-4--set-up-the-unity-project"></a>第4章-設定 Unity 專案

以下是使用 mixed reality 進行開發的一般設定，因此，它是適用于其他專案的絕佳範本。

1.  開啟 *Unity* ，然後按一下 [ **新增**]。 

    ![設定 Unity 專案](images/AzureLabs-Lab312-20.png)

2.  您現在將需要提供 Unity 專案名稱。 插入 **HoloLens Bot**。 請確定專案範本已設定為 **3d**。 將 **位置** 設定為適合您 (記住，較接近根目錄的) 。 然後，按一下 [ **建立專案**]。

    ![設定 Unity 專案](images/AzureLabs-Lab312-21.png)

3.  在 Unity 開啟的情況下，值得檢查預設 **腳本編輯器** 是否設定為 **Visual Studio**。 移至 [ **編輯] > 喜好** 設定，然後在新視窗中，流覽至 [ **外部工具**]。 將 **外部腳本編輯器** 變更為 **Visual Studio 2017**。 關閉 [ **喜好** 設定] 視窗。

    ![設定 Unity 專案](images/AzureLabs-Lab312-22.png)

4.  接下來，移至 [檔案 **> 組建設定** ]，選取 [ **通用 Windows 平臺**]，然後按一下 [ **切換平臺** ] 按鈕以套用您的選取專案。

    ![設定 Unity 專案](images/AzureLabs-Lab312-23.png)

5.  在檔案中仍 **> 組建設定** ，並確定：

    1.  **目標裝置** 設定為 **HoloLens**

        > 針對沉浸式耳機，將 **目標裝置** 設為 *任何裝置*。

    2.  **組建類型** 設定為 **D3D**

    3.  **SDK** 已設定為 **最新安裝**

    4.  **Visual Studio 版本** 設定為 **最新安裝**

    5.  **組建並執行** 設定為 **本機電腦**

    6.  儲存場景，並將其新增至組建。 

        1. 若要這麼做，請選取 [ **新增開啟的場景**]。 [儲存] 視窗隨即出現。
        
            ![設定 Unity 專案](images/AzureLabs-Lab312-24.png)

        2. 為此和任何未來的場景建立新的資料夾，然後選取 [ **新增資料夾** ] 按鈕，建立新的資料夾，將它命名為 **場景**。

             ![設定 Unity 專案](images/AzureLabs-Lab312-25.png)

        3. 開啟新建立的 **場景** 資料夾，然後在 [ *檔案名*：文字] 欄位中輸入 **BotScene**，然後按一下 [ **儲存**]。

            ![設定 Unity 專案](images/AzureLabs-Lab312-26.png)

    7. [ **組建設定**] 中的其餘設定，現在應該保持為預設值。

6. 在 [ *組建設定* ] 視窗中，按一下 [ **播放程式設定** ] 按鈕，這會開啟偵測 *器* 所在空間中的相關面板。 

    ![設定 Unity 專案](images/AzureLabs-Lab312-27.png)

7. 在此面板中，需要驗證幾個設定：

    1. 在 [ **其他設定** ] 索引標籤中：

        1. **腳本執行階段版本** 應該是 **實驗 (NET 4.6 對等)**;變更此項將需要重新開機編輯器。
        2. **腳本後端** 應該是 **.net**
        3. **API 相容性層級** 應為 **.net 4.6**

            ![設定 Unity 專案](images/AzureLabs-Lab312-28.png)
      
    2. 在 [ **發行設定** ] 索引標籤的 [ **功能**] 下，選取：

        - **InternetClient**
        - **麥克風**

            ![設定 Unity 專案](images/AzureLabs-Lab312-29.png)

    3. 在面板的 [XR 設定] 中，在 [ **設定** ] (找到的 [ **發佈設定** ]) 、[滴答 **虛擬實境支援**]，請確定已新增 **Windows Mixed Reality SDK** 。

        ![設定 Unity 專案](images/AzureLabs-Lab312-30.png)

8.  回到 *組建設定*： _Unity c #_ 專案不再呈現灰色;勾選此方塊旁邊的核取方塊。 
9.  關閉 [建置設定] 視窗。
10. 將場景和專案儲存 (檔 **> 儲存場景/檔案 > 儲存專案**) 。


## <a name="chapter-5--camera-setup"></a>第5章-攝影機設定

> [!IMPORTANT]
> 如果您想要略過此課程的 *Unity 設定* 元件，並直接繼續進行程式碼，請隨意下載此 [Azure-MR-312-unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20312%20-%20Bot%20integration/Azure-MR-312.unitypackage)，將其匯入到您的專案中做為 [**自訂套件**](https://docs.unity3d.com/Manual/AssetPackages.html)，然後繼續進行 [第7章](#chapter-8--create-the-botobjects-class)。

1.  在 [階層] *面板* 中，選取 [ **主要相機**]。 
2.  一旦選取之後，您就可以在 [偵測 *器] 面板* 中看到 **主要攝影機** 的所有元件。

    1. **攝影機物件** 必須命名為 **主要攝影機** (注意拼寫) 
    2. 主要攝影機 **標記** 必須設定為 **MainCamera** (注意拼寫) 
    3. 請確定 **轉換位置** 設定為 **0、0、0**
    4. 將 [ **清除] 旗標** 設定為 [ **純色**]。
    5. 將相機元件的 **背景** 色彩設定為 **黑色、Alpha 0 (Hex 碼： #00000000)**

    ![攝影機設定](images/AzureLabs-Lab312-31.png)
 

## <a name="chapter-6--import-the-newtonsoft-library"></a>第6章–匯入 Newtonsoft 程式庫

為了協助您還原序列化和序列化接收和傳送至 Bot 服務的物件，您需要下載 **Newtonsoft** 程式庫。 您會在 [這裡找到已使用正確 Unity 資料夾結構組織的相容版本](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20312%20-%20Bot%20integration/NewtonsoftDLL.unitypackage)。 

若要將 Newtonsoft 程式庫匯入您的專案，請使用本課程隨附的 Unity 套件。

1.  使用 [  **資產** 匯  >  **入封裝**  >  **自訂套件**] 功能表選項，將 unitypackage 新增至 Unity。

    ![匯入 Newtonsoft 程式庫](images/AzureLabs-Lab312-34.png)

2.  在彈出的 [匯 **入 Unity 套件** ] 方塊中，確定已選取 [ (] 下的所有專案，並包含) **外掛程式** 。

    ![匯入 Newtonsoft 程式庫](images/AzureLabs-Lab312-35.png)

3.  按一下 [匯 **入** ] 按鈕，將專案新增至您的專案。

4.  移至專案視圖中 [**外掛程式**] 下的 [ **Newtonsoft** ] 資料夾，然後選取 Newtonsoft 外掛程式。

    ![](images/AzureLabs-Lab312-35b.png)

5.  選取 Newtonsoft 外掛程式之後，請確定已 **取消** 選取 **任何平臺**，然後確定也未 **選取**[ **WSAPlayer** ]，然後 **按一下 [** 套用]。 這只是為了確認檔案已正確設定。

    ![](images/AzureLabs-Lab312-35c.png)

    > [!NOTE]
    > 標記這些外掛程式會將它們設定為只在 Unity 編輯器中使用。 在 [WSA] 資料夾中有一組不同的集合，會在從 Unity 匯出專案之後使用。

6.  接下來，您需要在 **Newtonsoft** 資料夾內開啟 [ **WSA** ] 資料夾。 您會看到您剛剛設定的相同檔案的複本。 選取檔案，然後在偵測器中，確定
    -   **未核** 取 **任何平臺** 
    -   **只****檢查** **WSAPlayer**
    -   不 **檢查****進程**

    ![](images/AzureLabs-Lab312-35d.png)

## <a name="chapter-7--create-the-bottag"></a>第7章-建立 BotTag

1.  建立名為 **BotTag** 的新 **標記** 物件。 選取場景中的主要攝影機。 按一下 [檢查] 面板中的 [標記] 下拉式功能表。 按一下 [ **新增標記**]。

    ![攝影機設定](images/AzureLabs-Lab312-32.png)
 
2.  按一下 **+** 符號。 將新 **標記** 命名為 **BotTag**， *儲存*。

    ![攝影機設定](images/AzureLabs-Lab312-33.png)

> [!WARNING] 
> **請勿** 將 **BotTag** 套用至主要攝影機。 如果您不小心這麼做，請務必將主要攝影機標記變更回 *MainCamera*。

## <a name="chapter-8--create-the-botobjects-class"></a>第8章-建立 BotObjects 類別

您需要建立的第一個腳本是 **BotObjects** 類別，這是一個建立的空類別，可讓一系列的其他類別物件儲存在相同的腳本內，並由場景中的其他腳本存取。

建立此類別純粹是架構選擇，這些物件可以改為裝載在您稍後將在本課程中建立的 Bot 腳本中。

若要建立此類別： 

1.  在 [ *專案] 面板* 中按一下滑鼠右鍵，然後 **建立 > 資料夾**。 將資料夾命名為 **腳本**。 

    ![建立腳本資料夾。](images/AzureLabs-Lab312-36.png)

2.  按兩下 [ **腳本** ] 資料夾以開啟它。 然後，在該資料夾中，以滑鼠右鍵按一下，然後選取 [ **建立 > c # 腳本**]。 將腳本命名為 **BotObjects**。 

3.  按兩下新的 **BotObjects** 腳本，以 **Visual Studio** 開啟。

4.  刪除腳本的內容，並將它取代為下列程式碼：

    ```csharp
    using System;
    using System.Collections;
    using System.Collections.Generic;
    using UnityEngine;

    public class BotObjects : MonoBehaviour{}

    /// <summary>
    /// Object received when first opening a conversation
    /// </summary>
    [Serializable]
    public class ConversationObject
    {
        public string ConversationId;
        public string token;
        public string expires_in;
        public string streamUrl;
        public string referenceGrammarId;
    }

    /// <summary>
    /// Object including all Activities
    /// </summary>
    [Serializable]
    public class ActivitiesRootObject
    {
        public List<Activity> activities { get; set; }
        public string watermark { get; set; }
    }
    [Serializable]
    public class Conversation
    {
        public string id { get; set; }
    }
    [Serializable]
    public class From
    {
        public string id { get; set; }
        public string name { get; set; }
    }
    [Serializable]
    public class Activity
    {
        public string type { get; set; }
        public string channelId { get; set; }
        public Conversation conversation { get; set; }
        public string id { get; set; }
        public From from { get; set; }
        public string text { get; set; }
        public string textFormat { get; set; }
        public DateTime timestamp { get; set; }
        public string serviceUrl { get; set; }
    }
    ```

6.  返回 *Unity* 之前，請務必將您的變更儲存在 *Visual Studio* 中。

## <a name="chapter-9--create-the-gazeinput-class"></a>第9章–建立 GazeInput 類別

您即將建立的下一個類別是 **GazeInput** 類別。 此類別負責：

- 建立將表示播放程式 *注視* 的游標。
- 偵測播放程式注視的物件，並保存偵測到之物件的參考。

若要建立此類別： 

1.  移至您先前建立的 **腳本** 資料夾。 
2.  以滑鼠右鍵按一下資料夾內的， **建立 > c # 腳本**。 呼叫腳本 **GazeInput**。 
3.  按兩下新的 **GazeInput** 腳本，以 **Visual Studio** 開啟。
4.  在類別名稱的頂端插入下面這行：

    ```csharp
    /// <summary>
    /// Class responsible for the User's gaze interactions
    /// </summary>
    [System.Serializable]
    public class GazeInput : MonoBehaviour
    ```

5.  然後，在 **GazeInput** 類別內，于 **Start ()** 方法的上方新增下列變數：

    ```csharp
        [Tooltip("Used to compare whether an object is to be interacted with.")]
        internal string InteractibleTag = "BotTag";

        /// <summary>
        /// Length of the gaze
        /// </summary>
        internal float GazeMaxDistance = 300;

        /// <summary>
        /// Object currently gazed
        /// </summary>
        internal GameObject FocusedObject { get; private set; }

        internal GameObject _oldFocusedObject { get; private set; }

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

6.  應新增 **開始 ()** 方法的程式碼。 當類別初始化時，就會呼叫：

    ```csharp
        /// <summary>
        /// Start method used upon initialization.
        /// </summary>
        internal virtual void Start()
        {
            FocusedObject = null;
            Cursor = CreateCursor();
        }
    ```

7.  執行將會具現化並設定注視游標的方法： 

    ```csharp
        /// <summary>
        /// Method to create a cursor object.
        /// </summary>
        internal GameObject CreateCursor()
        {
            GameObject newCursor = GameObject.CreatePrimitive(PrimitiveType.Sphere);
            newCursor.SetActive(false);
            // Remove the collider, so it does not block Raycast.
            Destroy(newCursor.GetComponent<SphereCollider>());
            newCursor.transform.localScale = new Vector3(0.05f, 0.05f, 0.05f);
            Material mat = new Material(Shader.Find("Diffuse"));
            newCursor.GetComponent<MeshRenderer>().material = mat;
            mat.color = Color.HSVToRGB(0.0223f, 0.7922f, 1.000f);
            newCursor.SetActive(true);

            return newCursor;
        }
    ```

8.  執行會從主要攝影機設定 Raycast 的方法，並追蹤目前焦點的物件。

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
            if (_oldFocusedObject != null)
            {
                if (_oldFocusedObject.CompareTag(InteractibleTag))
                {
                    // Provide the OnGazeExited event.
                    _oldFocusedObject.SendMessage("OnGazeExited", 
                        SendMessageOptions.DontRequireReceiver);
                }
            }
        }


        private void UpdateRaycast()
        {
            // Set the old focused gameobject.
            _oldFocusedObject = FocusedObject;
            RaycastHit hitInfo;

            // Initialize Raycasting.
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
            if (FocusedObject != _oldFocusedObject)
            {
                ResetFocusedObject();
                if (FocusedObject != null)
                {
                    if (FocusedObject.CompareTag(InteractibleTag))
                    {
                        // Provide the OnGazeEntered event.
                        FocusedObject.SendMessage("OnGazeEntered",
                            SendMessageOptions.DontRequireReceiver);
                    }
                }
            }
        }
    ```
 
9.  返回 *Unity* 之前，請務必將您的變更儲存在 *Visual Studio* 中。

## <a name="chapter-10--create-the-bot-class"></a>第10章-建立 Bot 類別

您要建立的腳本現在稱為 **Bot**。 這是您應用程式的核心類別，它會儲存： 

- 您的 Web 應用程式 Bot 認證
- 收集使用者心聲命令的方法
- 使用您的 Web 應用程式 Bot 起始交談所需的方法 
- 將訊息傳送至 Web 應用程式 Bot 所需的方法 

為了將訊息傳送至 Bot 服務， **SendMessageToBot ()** 協同程式會建立活動，此活動是由使用者所傳送的資料 Bot Framework 所辨識的物件。 
 
若要建立此類別： 

1. 按兩下 [ **腳本** ] 資料夾以開啟它。 
2. 在 [ **腳本** ] 資料夾內按一下滑鼠右鍵，然後按一下 [ **建立 > c # 腳本**]。 為腳本 **Bot** 命名。 
3. 按兩下新的腳本，以 Visual Studio 開啟。
4. 在 **Bot** 類別的頂端，將命名空間更新為與下列相同：

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.Text;
    using UnityEngine;
    using UnityEngine.Networking;
    using UnityEngine.Windows.Speech;
    ```
 
5. 在 **Bot** 類別內新增下列變數：

    ```csharp
        /// <summary>
        /// Static instance of this class
        /// </summary>
        public static Bot Instance;

        /// <summary>
        /// Material of the sphere representing the Bot in the scene
        /// </summary>
        internal Material botMaterial;

        /// <summary>
        /// Speech recognizer class reference, which will convert speech to text.
        /// </summary>
        private DictationRecognizer dictationRecognizer;

        /// <summary>
        /// Use this variable to identify the Bot Id
        /// Can be any value
        /// </summary>
        private string botId = "MRBotId";

        /// <summary>
        /// Use this variable to identify the Bot Name
        /// Can be any value
        /// </summary>
        private string botName = "MRBotName";

        /// <summary>
        /// The Bot Secret key found on the Web App Bot Service on the Azure Portal
        /// </summary>
        private string botSecret = "-- Add your Secret Key here --"; 

        /// <summary>
        /// Bot Endpoint, v4 Framework uses v3 endpoint at this point in time
        /// </summary>
        private string botEndpoint = "https://directline.botframework.com/v3/directline";

        /// <summary>
        /// The conversation object reference
        /// </summary>
        private ConversationObject conversation;

        /// <summary>
        /// Bot states to regulate the application flow
        /// </summary>
        internal enum BotState {ReadyToListen, Listening, Processing}

        /// <summary>
        /// Flag for the Bot state
        /// </summary>
        internal BotState botState;

        /// <summary>
        /// Flag for the conversation status
        /// </summary>
        internal bool conversationStarted = false;
    ```

    > [!NOTE] 
    > 請確定您將 **Bot 秘密金鑰** 插入 **botSecret** 變數中。 您將在本課程的開頭注明您的 **Bot 秘密金鑰**，第 **[2 章](#chapter-2---create-the-azure-bot-service)步驟 10**。

7. 現在需要新增 **喚醒 ()** 的程式碼，並 **開始 ()** 。 

    ```csharp
        /// <summary>
        /// Called on Initialization
        /// </summary>
        void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Called immediately after Awake method
        /// </summary>
        void Start()
        {
            botState = BotState.ReadyToListen;
        }
    ```

8. 當語音捕捉開始和結束時，新增兩個由語音程式庫呼叫的處理常式。 當使用者停止說話時， *DictationRecognizer* 會自動停止捕捉使用者心聲。

    ```csharp
        /// <summary>
        /// Start microphone capture.
        /// </summary>
        public void StartCapturingAudio()
        {
            botState = BotState.Listening;
            botMaterial.color = Color.red;

            // Start dictation
            dictationRecognizer = new DictationRecognizer();
            dictationRecognizer.DictationResult += DictationRecognizer_DictationResult;
            dictationRecognizer.Start();
        }
        

        /// <summary>
        /// Stop microphone capture.
        /// </summary>
        public void StopCapturingAudio()
        {
            botState = BotState.Processing;
            dictationRecognizer.Stop();
        }
        
    ```

1. 下列處理常式會收集使用者語音輸入的結果，並呼叫負責將訊息傳送至 Web 應用程式 Bot 服務的協同程式。

    ```csharp
        /// <summary>
        /// This handler is called every time the Dictation detects a pause in the speech. 
        /// </summary>
        private void DictationRecognizer_DictationResult(string text, ConfidenceLevel confidence)
        {
            // Update UI with dictation captured
            Debug.Log($"User just said: {text}");      

            // Send dictation to Bot
            StartCoroutine(SendMessageToBot(text, botId, botName, "message"));
            StopCapturingAudio();
        }     
    ```

10. 呼叫下列協同程式來開始與 Bot 的對話。 您將會注意到在對話呼叫完成後，它會藉由傳遞一系列的參數來呼叫 **SendMessageToCoroutine ()** ，這些參數會將活動設定為以空白訊息的形式傳送至 Bot 服務。 這麼做是為了提示 Bot 服務起始對話。

    ```csharp
        /// <summary>
        /// Request a conversation with the Bot Service
        /// </summary>
        internal IEnumerator StartConversation()
        {
            string conversationEndpoint = string.Format("{0}/conversations", botEndpoint);

            WWWForm webForm = new WWWForm();

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Post(conversationEndpoint, webForm))
            {
                unityWebRequest.SetRequestHeader("Authorization", "Bearer " + botSecret);
                unityWebRequest.downloadHandler = new DownloadHandlerBuffer();

                yield return unityWebRequest.SendWebRequest();
                string jsonResponse = unityWebRequest.downloadHandler.text;
            
                conversation = new ConversationObject();
                conversation = JsonConvert.DeserializeObject<ConversationObject>(jsonResponse);
                Debug.Log($"Start Conversation - Id: {conversation.ConversationId}");
                conversationStarted = true; 
            }

            // The following call is necessary to create and inject an activity of type //"conversationUpdate" to request a first "introduction" from the Bot Service.
            StartCoroutine(SendMessageToBot("", botId, botName, "conversationUpdate"));
        }    
    ```

11. 呼叫下列協同程式來建立要傳送至 Bot 服務的活動。 

    ```csharp
        /// <summary>
        /// Send the user message to the Bot Service in form of activity
        /// and call for a response
        /// </summary>
        private IEnumerator SendMessageToBot(string message, string fromId, string fromName, string activityType)
        {
            Debug.Log($"SendMessageCoroutine: {conversation.ConversationId}, message: {message} from Id: {fromId} from name: {fromName}");

            // Create a new activity here
            Activity activity = new Activity();
            activity.from = new From();
            activity.conversation = new Conversation();
            activity.from.id = fromId;
            activity.from.name = fromName;
            activity.text = message;
            activity.type = activityType;
            activity.channelId = "DirectLineChannelId";
            activity.conversation.id = conversation.ConversationId;     

            // Serialize the activity
            string json = JsonConvert.SerializeObject(activity);

            string sendActivityEndpoint = string.Format("{0}/conversations/{1}/activities", botEndpoint, conversation.ConversationId);
            
            // Send the activity to the Bot
            using (UnityWebRequest www = new UnityWebRequest(sendActivityEndpoint, "POST"))
            {
                www.uploadHandler = new UploadHandlerRaw(Encoding.UTF8.GetBytes(json));

                www.downloadHandler = new DownloadHandlerBuffer();
                www.SetRequestHeader("Authorization", "Bearer " + botSecret);
                www.SetRequestHeader("Content-Type", "application/json");

                yield return www.SendWebRequest();

                // extrapolate the response Id used to keep track of the conversation
                string jsonResponse = www.downloadHandler.text;
                string cleanedJsonResponse = jsonResponse.Replace("\r\n", string.Empty);
                string responseConvId = cleanedJsonResponse.Substring(10, 30);

                // Request a response from the Bot Service
                StartCoroutine(GetResponseFromBot(activity));
            }
        }
    ```

12. 在將活動傳送至 Bot 服務之後，會呼叫下列協同程式來要求回應。 

    ```csharp
        /// <summary>
        /// Request a response from the Bot by using a previously sent activity
        /// </summary>
        private IEnumerator GetResponseFromBot(Activity activity)
        {
            string getActivityEndpoint = string.Format("{0}/conversations/{1}/activities", botEndpoint, conversation.ConversationId);

            using (UnityWebRequest unityWebRequest1 = UnityWebRequest.Get(getActivityEndpoint))
            {
                unityWebRequest1.downloadHandler = new DownloadHandlerBuffer();
                unityWebRequest1.SetRequestHeader("Authorization", "Bearer " + botSecret);

                yield return unityWebRequest1.SendWebRequest();

                string jsonResponse = unityWebRequest1.downloadHandler.text;

                ActivitiesRootObject root = new ActivitiesRootObject();
                root = JsonConvert.DeserializeObject<ActivitiesRootObject>(jsonResponse);

                foreach (var act in root.activities)
                {
                    Debug.Log($"Bot Response: {act.text}");
                    SetBotResponseText(act.text);
                }

                botState = BotState.ReadyToListen;
                botMaterial.color = Color.blue;
            }
        } 
    ```

13. 要加入這個類別的最後一個方法，必須在場景中顯示訊息：

    ```csharp
        /// <summary>
        /// Set the UI Response Text of the bot
        /// </summary>
        internal void SetBotResponseText(string responseString)
        {        
            SceneOrganiser.Instance.botResponseText.text =  responseString;
        }
    ```

    > [!NOTE] 
    > 您可能會在 Unity 編輯器主控台中看到錯誤，缺少 **SceneOrganiser** 類別。 請忽略此訊息，因為您稍後會在本教學課程中建立此類別。

14.  返回 *Unity* 之前，請務必將您的變更儲存在 *Visual Studio* 中。

## <a name="chapter-11--create-the-interactions-class"></a>第11章-建立互動類別

您即將建立的類別稱為 **互動**。 此類別用來偵測來自使用者的 HoloLens 點擊輸入。 

如果使用者在查看場景中的 *bot* 物件時點擊，且 bot 已準備好接聽語音輸入，則 bot 物件會將色彩變更為 **紅色** ，並開始接聽語音輸入。 

這個類別繼承自 **GazeInput** 類別，因此可以從該類別參考 **開始 ()** 方法和變數，以使用 **base** 表示。 
 
若要建立此類別：

1.  按兩下 [ **腳本** ] 資料夾以開啟它。 
2.  在 [ **腳本** ] 資料夾內按一下滑鼠右鍵，然後按一下 [ **建立 > c # 腳本**]。 命名腳本的 **互動**。 
3.  按兩下新的腳本，以 Visual Studio 開啟。
4.  在 **互動** 類別的頂端，將命名空間和類別繼承更新為與下列相同：

    ```csharp
    using UnityEngine.XR.WSA.Input;

    public class Interactions : GazeInput
    {
    ```

5.  在 [ **互動** ] 類別內新增下列變數：

    ```csharp
        /// <summary>
        /// Allows input recognition with the HoloLens
        /// </summary>
        private GestureRecognizer _gestureRecognizer;
    ```
6.  然後，新增 **Start ()** 方法：

    ```csharp
        /// <summary>
        /// Called on initialization, after Awake
        /// </summary>
        internal override void Start()
        {
            base.Start();

            //Register the application to recognize HoloLens user inputs
            _gestureRecognizer = new GestureRecognizer();
            _gestureRecognizer.SetRecognizableGestures(GestureSettings.Tap);
            _gestureRecognizer.Tapped += GestureRecognizer_Tapped;
            _gestureRecognizer.StartCapturingGestures();
        }
    ```

7.  新增當使用者在 HoloLens 攝影機前方執行點按手勢時，將觸發的處理常式

    ```csharp
        /// <summary>
        /// Detects the User Tap Input
        /// </summary>
        private void GestureRecognizer_Tapped(TappedEventArgs obj)
        {
            // Ensure the bot is being gazed upon.
            if(base.FocusedObject != null)
            {
                // If the user is tapping on Bot and the Bot is ready to listen
                if (base.FocusedObject.name == "Bot" && Bot.Instance.botState == Bot.BotState.ReadyToListen)
                {
                    // If a conversation has not started yet, request one
                    if(Bot.Instance.conversationStarted)
                    {
                        Bot.Instance.SetBotResponseText("Listening...");
                        Bot.Instance.StartCapturingAudio();
                    }
                    else
                    {
                        Bot.Instance.SetBotResponseText("Requesting Conversation...");
                        StartCoroutine(Bot.Instance.StartConversation());
                    }                                  
                }
            }
        }
    ```

8. 返回 *Unity* 之前，請務必將您的變更儲存在 *Visual Studio* 中。

## <a name="chapter-12--create-the-sceneorganiser-class"></a>第12章-建立 SceneOrganiser 類別

此實驗室所需的最後一個類別稱為 **SceneOrganiser**。 此類別會以程式設計方式設定場景，方法是將元件和腳本新增至主要相機，並在場景中建立適當的物件。
 
若要建立此類別：

1.  按兩下 [ **腳本** ] 資料夾以開啟它。 
2.  在 [ **腳本** ] 資料夾內按一下滑鼠右鍵，然後按一下 [ **建立 > c # 腳本**]。 將腳本命名為 **SceneOrganiser**。 
3.  按兩下新的腳本，以 Visual Studio 開啟。
4.  在 **SceneOrganiser** 類別中，新增下列變數：

    ```csharp
        /// <summary>
        /// Static instance of this class
        /// </summary>
        public static SceneOrganiser Instance;

        /// <summary>
        /// The 3D text representing the Bot response
        /// </summary>
        internal TextMesh botResponseText;
    ```

6.  然後，新增 **喚醒的 ()** 並 **啟動 ()** 方法：

    ```csharp
        /// <summary>
        /// Called on Initialization
        /// </summary>
        private void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Called immediately after Awake method
        /// </summary>
        void Start ()
        {
            // Add the GazeInput class to this object
            gameObject.AddComponent<GazeInput>();

            // Add the Interactions class to this object
            gameObject.AddComponent<Interactions>();

            // Create the Bot in the scene
            CreateBotInScene();
        }
    ```

7.  新增下列方法，負責在場景中建立 Bot 物件，並設定參數和元件：

    ```csharp
        /// <summary>
        /// Create the Sign In button object in the scene
        /// and sets its properties
        /// </summary>
        private void CreateBotInScene()
        {
            GameObject botObjInScene = GameObject.CreatePrimitive(PrimitiveType.Sphere);
            botObjInScene.name = "Bot";
            
            // Add the Bot class to the Bot GameObject
            botObjInScene.AddComponent<Bot>();

            // Create the Bot UI
            botResponseText = CreateBotResponseText();

            // Set properties of Bot GameObject
            Bot.Instance.botMaterial = new Material(Shader.Find("Diffuse"));
            botObjInScene.GetComponent<Renderer>().material = Bot.Instance.botMaterial;
            Bot.Instance.botMaterial.color = Color.blue;
            botObjInScene.transform.position = new Vector3(0f, 2f, 10f);
            botObjInScene.tag = "BotTag";
        }
    ```

7.  新增下列方法，負責在場景中建立 UI 物件，代表來自 Bot 的回應：

    ```csharp
        /// <summary>
        /// Spawns cursor for the Main Camera
        /// </summary>
        private TextMesh CreateBotResponseText()
        {
            // Create a sphere as new cursor
            GameObject textObject = new GameObject();
            textObject.transform.parent = Bot.Instance.transform;
            textObject.transform.localPosition = new Vector3(0,1,0);

            // Resize the new cursor
            textObject.transform.localScale = new Vector3(0.1f, 0.1f, 0.1f);

            // Creating the text of the Label
            TextMesh textMesh = textObject.AddComponent<TextMesh>();
            textMesh.anchor = TextAnchor.MiddleCenter;
            textMesh.alignment = TextAlignment.Center;
            textMesh.fontSize = 50;
            textMesh.text = "Hi there, tap on me and I will start listening.";
            
            return textMesh;
        }
    ```

8.  返回 *Unity* 之前，請務必將您的變更儲存在 *Visual Studio* 中。
9.  在 Unity 編輯器中，將 [腳本] 資料夾中的 **SceneOrganiser** 腳本拖曳至主要攝影機。 場景 Organiser 元件現在應該會出現在主要攝影機物件上，如下圖所示。

    ![建立 Azure Bot 服務](images/AzureLabs-Lab312-37.png)

## <a name="chapter-13--before-building"></a>第13章-建立之前

若要執行應用程式的完整測試，您必須將它側載到 HoloLens。
在執行之前，請確定：

-   [**第4章**](#chapter-4--set-up-the-unity-project)中所述的所有設定都已正確設定。 
-   腳本 **SceneOrganiser** 會附加至 **主要攝影機** 物件。 
-   在 **Bot** 類別中，請確定您已將 **Bot 秘密金鑰** 插入 **botSecret** 變數中。

## <a name="chapter-14--build-and-sideload-to-the-hololens"></a>第14章–組建並側載至 HoloLens

此專案的 Unity 區段所需的所有專案現在都已完成，因此您可以從 Unity 建立它。

1.  流覽至 [ **組建設定**]、[檔案 **> 組建設定 ...**]。
2.  從 [ **組建設定** ] 視窗中，按一下 [ **建立**]。

    ![從 Unity 建立應用程式](images/AzureLabs-Lab312-38.png)

3.  如果尚未這麼做，請勾選 **Unity c # 專案**。
4.  按一下 [建置]。 Unity 將會啟動一個 **檔案總管** 視窗，您需要在其中建立並選取要用來建立應用程式的資料夾。 立即建立該資料夾，並命名為 **應用程式**。 然後選取 [ **應用程式** ] 資料夾，然後按一下 [ **選取資料夾**]。 
5.  Unity 將開始將您的專案建立到 **應用程式** 資料夾。 
6.  Unity 完成組建之後 (可能需要一些時間) ，它會在您的組建位置開啟 **檔案總管** 視窗 (檢查您的工作列，因為它不一定會出現在您的視窗上方，但會通知您加入新的視窗) 。

## <a name="chapter-15--deploy-to-hololens"></a>第15章-部署到 HoloLens

若要在 HoloLens 上部署：

1.  您將需要 HoloLens (的 IP 位址，才能進行遠端部署) ，並確保 HoloLens 處於 **開發人員模式**。 若要這樣做：

    1. 在設置 HoloLens 的同時，開啟 **設定**。
    2. 前往 **Network & Internet > Wi-Fi > Advanced Options**
    3. 記下 **IPv4** 位址。
    4. 接下來，流覽回到 [ **設定**]，然後 **更新開發人員 & 的安全性 >** 
    5. 設定 [開發人員模式]。

2.  流覽至您的新 Unity 組建 (**應用程式** 資料夾) ，然後以 **Visual Studio** 開啟方案檔。
3.  在 [ **方案** 設定] 中選取 [ **Debug**]。
4.  在 **解決方案平臺** 中，選取 [ **x86**]、[ **遠端電腦**]。 

    ![從 Visual Studio 部署方案。](images/AzureLabs-Lab312-39.png)
 
5.  移至 [ **組建] 功能表** ，然後按一下 [ **部署方案**]，將應用程式側載至 HoloLens。
6.  您的應用程式現在應該會出現在 HoloLens 上已安裝的應用程式清單中，準備好可供啟動！

    > [!NOTE]
    > 若要部署到沉浸式耳機，請將 **解決方案平臺****設定為 [** *本機電腦*]，並將 [設定] 設定為 [以 *x86* 作為 **平臺**] 來進行 *Debug*。 然後使用 [ **組建] 功能表** 選取 [ *部署方案*]，部署到本機電腦。 

## <a name="chapter-16--using-the-application-on-the-hololens"></a>第16章–在 HoloLens 上使用應用程式

- 當您啟動應用程式之後，您會在前方看到 Bot 成為藍色球體。

- 當您在球體上撥雲見日時，請使用點一下 **手勢** 來起始對話。 
 
- 等候對話開始 (當) 發生訊息時，UI 會顯示訊息。 當您收到來自 Bot 的簡介訊息之後，請在 Bot 上再次點一下，讓它變成紅色並開始聆聽您的聲音。 

- 當您停止交談之後，您的應用程式會將您的訊息傳送至 Bot，且您會立即收到將顯示在 UI 中的回應。 

- 重複此程式，將更多訊息傳送至您的 Bot (您必須在每次想要 sen 訊息) 時按一下。

此交談會示範 Bot 如何保留 (您的名稱) 的資訊，同時也提供已知的資訊 (例如已儲存) 的專案。

#### <a name="some-questions-to-ask-the-bot"></a>要求 Bot 的一些問題：

```
what do you sell? 

how much are umbrellas?

how much are raincoats?
```

## <a name="your-finished-web-app-bot-v4-application"></a>您已完成的 Web 應用程式 Bot (v4) 應用程式

恭喜，您建立了一個利用 Azure Web 應用程式 Bot Microsoft Bot Framework v4 的混合現實應用程式。

![最終產品](images/AzureLabs-Lab312-00.png)

## <a name="bonus-exercises"></a>額外練習

### <a name="exercise-1"></a>練習1

此實驗室中的交談結構非常基本。 使用 Microsoft LUIS 為您的 bot 提供自然語言理解功能。

### <a name="exercise-2"></a>練習2

此範例不包含終止交談並重新啟動新的交談。 若要讓 Bot 功能完成，請嘗試將結束的情況執行到交談。