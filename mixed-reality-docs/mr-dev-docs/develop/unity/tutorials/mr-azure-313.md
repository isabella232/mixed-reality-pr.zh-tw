---
title: HoloLens (第1代) 和 Azure 313-IoT 中樞服務
description: 瞭解如何在執行 Ubuntu 16.4 的虛擬機器上執行 Azure IoT Hub 服務，並使用 Microsoft HoloLens 或 VR 耳機來視覺化訊息資料。
author: drneil
ms.author: jemccull
ms.date: 07/11/2018
ms.topic: article
keywords: azure，混合的現實，學術，邊緣，iot edge，教學課程，api，通知，函式，資料表，hololens，沉浸式，vr，iot，虛擬機器，ubuntu，python，Windows 10，Visual Studio
ms.openlocfilehash: fbd793a5941a5fa1b236403672680aa7df375f8d
ms.sourcegitcommit: 191c3d89c034714377d09fa91c07cbaa81301bae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/13/2021
ms.locfileid: "121905766"
---
# <a name="hololens-1st-gen-and-azure-313-iot-hub-service"></a>HoloLens (第1代) 和 Azure 313： IoT 中樞服務

>[!NOTE]
>混合實境學院教學課程的設計是以 HoloLens (第 1 代) 和混合實境沉浸式頭戴裝置為準。  因此，對於仍在尋找這些裝置開發指引的開發人員而言，我們覺得這些教學課程很重要。  這些教學課程 **_不會_** 使用用於 HoloLens 2 的最新工具組或互動進行更新。  系統會保留這些資訊，以繼續在支援的裝置上運作。 未來將會有一系列新的教學課程，將會示範如何針對 HoloLens 2 進行開發。  當張貼這些教學課程時，將會使用這些教學課程的連結來更新此通知。

![課程結果](images/AzureLabs-Lab313-00.png)

在此課程中，您將瞭解如何在執行 Ubuntu 16.4 作業系統的虛擬機器上執行 **Azure IoT Hub 服務**。 然後，Azure 函式 **應用程式** 會用來接收來自 Ubuntu VM 的訊息，並將結果儲存在 **Azure 表格服務** 中。 然後，您將能夠使用 Microsoft HoloLens 或沉浸式 (VR) 耳機上的 **Power BI** 來查看此資料。

本課程的內容 *適用* 于 IoT Edge 裝置，但基於本課程的目的，焦點會放在虛擬機器環境上，因此不需要存取實體邊緣裝置。

完成本課程之後，您將瞭解如何：

- 將 **IoT Edge 模組** 部署到 (UBUNTU 16 OS) 的虛擬機器，這會代表您的 IoT 裝置。
- 將 **Azure 自訂視覺 Tensorflow 模型** 新增至 Edge 模組，並使用程式碼來分析儲存在容器中的影像。
- 設定模組，以將分析結果訊息傳回給您的 **IoT 中樞服務**。
- 使用 **Azure 函數應用程式** 將訊息儲存在 **azure 資料表** 中。
- 設定 **Power BI** ，以收集已儲存的訊息並建立報表。
- 視覺化 **Power BI** 內的 IoT 訊息資料。

您將使用的服務包括：

- **Azure IoT 中樞** 是一項 Microsoft Azure 服務，可讓開發人員連線、監視及管理 IoT 資產。 如需詳細資訊，請造訪 [ **Azure IoT Hub 服務** 頁面](https://azure.microsoft.com/services/iot-hub/)。

- **Azure Container Registry** 是一種 Microsoft Azure 服務，可讓開發人員儲存容器映射，以用於各種類型的容器。 如需詳細資訊，請造訪 [ **Azure Container Registry 服務** 頁面](https://azure.microsoft.com/services/container-registry/)。

- **azure 函數應用程式** 是一項 Microsoft Azure 服務，可讓開發人員在 Azure 中執行一小段程式碼「函式」。 這可提供將工作委派給雲端的方法，而不是您的本機應用程式，這可能有許多優點。 **Azure Functions** 支援數種開發語言，包括 C \# 、F \# 、Node.js、JAVA 和 PHP。 如需詳細資訊，請造訪 [ **Azure Functions** 頁面](/azure/azure-functions/functions-overview)。

- **Azure 儲存體：資料表** 是一種 Microsoft Azure 服務，可讓開發人員將結構化、非 SQL 的資料儲存在雲端中，讓它可以輕鬆地隨處存取。 此服務具有無架構的設計，可讓您視需要進行資料表的演進，因此非常有彈性。 如需詳細資訊，請造訪 [ **Azure 資料表** 頁面](/azure/cosmos-db/table-storage-overview)

本課程將告訴您如何設定和使用 IoT 中樞服務，然後將裝置所提供的回應視覺化。 您可自行將這些概念套用至您可能正在建立的自訂 IoT 中樞服務設定。

## <a name="device-support"></a>裝置支援

<table>
<tr>
<th>課程</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">沉浸式頭戴裝置</a></th>
</tr><tr>
<td> MR 和 Azure 313：IoT 中樞服務</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="prerequisites"></a>必要條件

如需使用混合現實進行開發的最新必要條件，包括使用 Microsoft HoloLens，請造訪[安裝工具](../../install-the-tools.md)文章。

> [!NOTE]
> 本教學課程是專為具有 Python 基本經驗的開發人員所設計。 另外也請注意，本檔中的必要條件和書面指示，代表在撰寫 (2018 年7月) 時已經過測試和驗證的內容。 You are free to use the latest software, as listed within the [install the tools](../../install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you will find in newer software than that listed below.

需要下列硬體和軟體：

- Windows 10 Fall Creators Update (或更新版本) ，**啟用開發人員模式**

    > [!WARNING]
    > 您無法在 Windows 10 家用版版上使用 hyper-v 來執行虛擬機器。

- Windows 10SDK (最新版本) 
- **已啟用 HoloLens 開發人員模式**
- Visual Studio 2017.15.4 (僅用來存取 Azure Cloud Explorer) 
- 適用于 Azure 的網際網路存取，以及適用于 IoT 中樞服務的網際網路存取。 如需詳細資訊，請遵循此 [連結來前往 IoT 中樞服務頁面](https://azure.microsoft.com/services/iot-hub/)
- 機器學習模型。 如果您沒有自己的現成可用模型， [您可以使用本課程所提供的模型](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20313%20-%20IoT%20Hub%20Service/Custom%20Vision%20Model.zip)。
- 您 Windows 10 開發電腦上已啟用 **hyper-v** 軟體。
- 執行 Ubuntu (16.4 或 18.4) 的虛擬機器，可在您的開發電腦上執行，或者您也可以使用執行 Linux (Ubuntu 16.4 或 18.4) 的個別電腦。 您可以在[「開始之前」一章](#before-you-start)中，找到有關如何使用 hyper-v 在 Windows 上建立 VM 的詳細資訊。 (https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/quick-create-virtual-machine) 。  



### <a name="before-you-start"></a>在您開始使用 Intune 之前

1. 設定及測試您的 HoloLens。 如果您需要設定 HoloLens 的支援，[請務必造訪 HoloLens 安裝程式文章](/hololens/hololens-setup)。
2. 在開始開發新的 HoloLens 應用程式時，最好先執行 **校正** 和 **感應器調整**， (有時它可以協助您為每個使用者) 執行這些工作。

如需有關校正的說明，請遵循此[連結來 HoloLens 校正文章](/hololens/hololens-calibration#hololens-2)。

如需有關感應器微調的說明，請依照此[連結前往 HoloLens 感應器微調文章](/hololens/hololens-updates)。

3. 使用 **hyper-v** 設定您的 **Ubuntu 虛擬機器**。 下列資源將協助您處理常式。
    1.  首先，請遵循此連結 [下載 Ubuntu 16.04.4 LTS (Xenial Xerus) ISO](https://au.releases.ubuntu.com/16.04/)。 選取 **64 位電腦 (AMD64) 桌面映射**。
    2.  確定您的 Windows 10 電腦上已啟用 **hyper-v** 。 您可以遵循此連結，以取得在[Windows 10 上安裝和啟用 hyper-v](/virtualization/hyper-v-on-windows/quick-start/enable-hyper-v)的指引。
    3.  啟動 Hyper-v 並建立新的 Ubuntu VM。 您可以遵循此連結，以取得 [如何使用 hyper-v 建立 VM 的逐步指南](/virtualization/hyper-v-on-windows/quick-start/create-virtual-machine)。 當要求「 **從可開機映射檔案安裝作業系統**」時，請選取您稍早下載的 **Ubuntu ISO** 。

    > [!NOTE]
    > 不建議使用 [ **Hyper-v 快速建立** ]。  

## <a name="chapter-1---retrieve-the-custom-vision-model"></a>第1章-取出自訂視覺模型

在此課程中，您將可以存取 [預先建立的自訂視覺模型](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20313%20-%20IoT%20Hub%20Service/Custom%20Vision%20Model.zip) ，以偵測影像中的鍵盤和滑鼠。 如果您使用此作業，請繼續進行 [第2章](#chapter-2---the-container-registry-service)。

但是，如果您想要使用自己的自訂視覺模型，您可以遵循下列步驟：

1. 在您的 **自訂視覺 Project** 移至 [**效能**] 索引標籤。

    > [!WARNING]
    > 您的模型必須使用 *compact* 網域來匯出模型。 您可以在專案的 [設定] 中變更模型網域。

    ![效能索引標籤](images/AzureLabs-Lab313-01.png)

2. 選取您要匯出的 **反復** 專案，然後按一下 [ **匯出**]。 將會出現一個分頁。

    ![匯出分頁](images/AzureLabs-Lab313-02.png)

3. 在 blade 中，按一下 [ **Docker** 檔案]。

    ![選取 docker](images/AzureLabs-Lab313-03.png)

4. 按一下下拉式功能表中的 [ **Linux** ]，然後按一下 [ **下載**]。

    ![按一下 [下載]](images/AzureLabs-Lab313-04.png)

5. 將內容解壓縮。 您稍後將在本課程中使用它。

## <a name="chapter-2---the-container-registry-service"></a>第2章-Container Registry 服務

**Container Registry 服務** 是用來裝載容器的存放庫。

您將在此課程中建立並使用的 **IoT 中樞服務** ，是指 **容器登錄服務** ，以取得要在 Edge 裝置中部署的容器。

1. 首先，請遵循 [Azure 入口網站的連結](https://portal.azure.com/)，然後使用您的認證登入。

2. 移至 [ **建立資源** ] 並尋找 **Container Registry**。

    ![container registry](images/AzureLabs-Lab313-05.png)

3. 按一下 [ **建立**]。

    ![](images/AzureLabs-Lab313-06.png)

4. 設定服務安裝程式參數：

    1. 插入專案的名稱，在此範例中稱為 **IoTCRegistry**。

    2. 選擇資源群組，或建立一個新的 **資源群組** 。 資源群組可讓您監視、控制存取、布建及管理 Azure 資產集合的計費方式。 建議您保留與單一專案相關聯的所有 Azure 服務 (例如，) 一般資源群組下的這些課程) 。

    3. 設定服務的位置。

    4. 設定要 **啟用** 的系統 **管理使用者**。

    5. 將 **SKU** 設定為 [ **基本**]。 

    ![](images/AzureLabs-Lab313-07.png)

5. 按一下 [ **建立** ] 並等候建立服務。 

6. 當通知彈出通知您成功建立 *容器* 登錄時，請按一下 [ **移至資源** ]，以重新導向至您的服務頁面。

    ![](images/AzureLabs-Lab313-08.png)

7. 在 [ *Container Registry* 服務] 頁面中，按一下 [ **存取金鑰**]。

8. 請注意 (您可以使用下列參數的記事本) ：
    1. **登入伺服器**
    2. **使用者名稱**
    3. **密碼**

    ![](images/AzureLabs-Lab313-09.png)

## <a name="chapter-3---the-iot-hub-service"></a>第3章-IoT 中樞服務

現在您將開始建立和設定 **IoT 中樞服務**。

1. 如果還沒有登入，請登入 [Azure 入口網站](https://portal.azure.com)。

2.  登入後，按一下左上角的 [ **建立資源** ]，並搜尋 **IoT 中樞**，然後按一下 **Enter**。

 ![搜尋儲存體帳戶](images/AzureLabs-Lab313-10.png)

3.  新頁面將提供 **儲存體帳戶** 服務的描述。 在此提示的左下方，按一下 [ **建立** ] 按鈕以建立此服務的實例。

    ![建立儲存體實例](images/AzureLabs-Lab313-11.png)

4.  一旦您按一下 [ **建立**]，將會出現一個面板：

    1. 選擇資源群組，或建立一個新的 **資源群組** 。 資源群組提供一種方式來監視、控制存取、布建及管理 Azure 資產集合的計費。 建議您保留與單一專案相關聯的所有 Azure 服務 (例如，) 一般資源群組下的這些課程) 。

        > 如果您想要深入瞭解 Azure 資源群組，請遵循此 [連結，以瞭解如何管理資源群組](/azure/azure-resource-manager/resource-group-portal)。


    2. 選取適當的 **位置** ， (在您于此課程中建立的所有服務上使用相同的位置) 。

    3. 為此服務實例插入您想要的 **名稱** 。    

5.  在頁面底部按一下 **[下一步：大小和小** 數位數]。

    ![建立儲存體實例](images/AzureLabs-Lab313-12.png)

6.  在此頁面中，選取您的 **定價和級別層** (如果這是您的第一個 IoT 中樞服務實例，則您可以) 使用免費層。  

7.  按一下 [ **審核 + 建立**]。

    ![建立儲存體實例](images/AzureLabs-Lab313-13.png)

8.  檢查您的設定，然後按一下 [ **建立**]。

    ![建立儲存體實例](images/AzureLabs-Lab313-14.png)

9. 一旦快顯通知，通知您已成功建立 *IoT 中樞* 服務，請按一下 [ **移至資源** ]，以重新導向至您的服務頁面。

    ![建立儲存體實例](images/AzureLabs-Lab313-15.png)

10. 將左邊的側邊面板向左移，直到您看到 [ *自動裝置管理*]，然後按一下 [ **IoT Edge**]。

    ![建立儲存體實例](images/AzureLabs-Lab313-16.png)

11. 在顯示于右側的視窗中，按一下 [ **新增 IoT Edge 裝置**]。 分頁會顯示在右側。

12. 在分頁中，為新裝置提供 **裝置識別碼** (您選擇的名稱) 。 然後按一下 [ **儲存**]。 如果您有 **自動產生** 核取，*主要* 和 *次要金鑰* 將會自動產生。

    ![建立儲存體實例](images/AzureLabs-Lab313-17.png)

13. 您將流覽回 [ *IoT Edge 裝置* ] 區段，其中會列出您的新裝置。 在下圖中，按一下您的新裝置 (下圖中所述的紅色) 。 

    ![建立儲存體實例](images/AzureLabs-Lab313-18.png)

14. 在出現的 [ *裝置詳細資料* ] 頁面上，取得 **連接字串** (主要金鑰) 的複本。

    ![建立儲存體實例](images/AzureLabs-Lab313-19.png)

15. 返回至左側的面板，然後按一下 [ *共用存取原則*] 將它開啟。 

16. 在出現的頁面上，按一下 [ **iothubowner**]，分頁將會出現在畫面右側。 

17. 請注意 (**連接字串** 的記事本)  (主鍵) ，以供稍後在將 *連接字串* 設定至裝置時使用。

    ![建立儲存體實例](images/AzureLabs-Lab313-20.png)

## <a name="chapter-4---setting-up-the-development-environment"></a>第4章-設定開發環境

若要建立及部署 *IoT 中樞邊緣* 的模組，您需要在執行 Windows 10 的開發電腦上安裝下列元件：

1.  [適用於 Windows 的 Docker](https://store.docker.com/editions/community/docker-ce-desktop-windows)，系統會要求您建立可供下載的帳戶。 

    [![下載適用于 windows 的 docker](images/AzureLabs-Lab313-21.png)](https://store.docker.com/editions/community/docker-ce-desktop-windows)

    > [!IMPORTANT]
    > Docker 需要 *Windows 10 PRO*、 *Enterprise 14393* 或 *Windows Server 2016 RTM*）才能執行。 如果您正在執行其他版本的 Windows 10，您可以使用[docker 工具箱](https://docs.docker.com/toolbox/toolbox_install_windows/)嘗試安裝 docker。

2.  [Python 3.6](https://www.python.org/downloads/)。

    [![下載 python 3。6](images/AzureLabs-Lab313-22.png)](https://www.python.org/downloads/)

3.  [Visual Studio Code (也稱為 VS Code) ](https://code.visualstudio.com/download)。

    [![下載 VS Code](images/AzureLabs-Lab313-23.png)](https://code.visualstudio.com/download)

安裝上述的軟體之後，您將需要重新開機電腦。

## <a name="chapter-5---setting-up-the-ubuntu-environment"></a>第5章-設定 Ubuntu 環境

現在您可以繼續設定執行 **UBUNTU OS** 的裝置。 遵循下列步驟來安裝必要的軟體，以在您的面板上部署您的容器：

> [!IMPORTANT]
> 您應一律在終端機命令前面加上 **sudo** ，以系統管理使用者身分執行。 即：
> 
>   ```bash
>   sudo docker \<option> \<command> \<argument>
>   ```

1.  開啟 **Ubuntu 終端** 機，並使用下列命令來安裝 **pip**：

    > [!提示] 您可以使用鍵盤快速鍵輕鬆地開啟 *終端* 機： **Ctrl + Alt + T**。

    ```bash
        sudo apt-get install python-pip
    ```

2.  在本章中，系統可能會提示您 *終端* 機，以取得使用裝置存放裝置的許可權，並讓您輸入 **y/n** (是或否) ，輸入 **' y '**，然後按下 **enter** 鍵接受。

3.  命令完成後，請使用下列命令來安裝 **捲曲**：

    ```bash
        sudo apt install curl
    ```

4.  安裝 **pip** 和 **捲曲** 之後，請使用下列命令來安裝 **IoT Edge 運行** 時間，這是部署和控制您面板上模組的必要步驟：

    ```bash
        curl https://packages.microsoft.com/config/ubuntu/16.04/prod.list > ./microsoft-prod.list

        sudo cp ./microsoft-prod.list /etc/apt/sources.list.d/

        curl https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.gpg

        sudo cp ./microsoft.gpg /etc/apt/trusted.gpg.d/

        sudo apt-get update

        sudo apt-get install moby-engine

        sudo apt-get install moby-cli

        sudo apt-get update

        sudo apt-get install iotedge
    ```

5. 此時，系統會提示您開啟 *執行時間設定檔*，以插入您在記事本) 中記下的 **裝置連接字串** (在第 [3 章的步驟 14](#chapter-3---the-iot-hub-service) (建立 **IoT 中樞服務**) 。 在終端機上執行下列程式程式碼以開啟該檔案：

    ```bash
        sudo nano /etc/iotedge/config.yaml
    ```

6. **Yaml** 檔案隨即顯示，可供您編輯：

    > [!WARNING]
    > 開啟此檔案時，可能會有點混淆。 您將會在 *終端* 機本身內編輯此檔案中的文字。 

    1.  您可以使用鍵盤上的方向鍵向下 (您將需要向下) ，以達到包含 "：

        "**\<ADD DEVICE CONNECTION STRING HERE>**".

    2. 以您先前記下的 **裝置連接字串** 取代行（**包括括弧**）。

7. 將連接字串放在您的鍵盤上，按 **Ctrl** 鍵以儲存檔案。 它會要求您輸入 **Y** 來確認。然後，按下 **enter** 鍵以確認。 您將會回到一般 *終端* 機。 

8. 一旦這些命令順利執行之後，您就會安裝 **IoT Edge 運行** 時間。 一旦初始化之後，執行時間就會在裝置每次開機時啟動，而且會在背景中等待從 **IoT 中樞服務** 部署模組。

9.  執行下列命令列，以初始化 *IoT Edge 運行* 時間：

    ```bash
        sudo systemctl restart iotedge
    ```

    > [!IMPORTANT]
    > 如果您對 yaml 檔案或上述設定進行變更，您將需要在 *終端* 機內再次執行上述重新開機行。

10. 執行下列命令列，以檢查 *IoT Edge 運行* 時間狀態。 執行時間應該會顯示狀態為「作用中」 (以綠色文字執行 **)** 。

    ```bash
        sudo systemctl status iotedge
    ```

11. 按 **Ctrl + C** 鍵，結束狀態頁面。 您可以輸入下列命令，確認 *IoT Edge 運行* 時間是否正確地提取容器：

    ```bash
        sudo docker ps
    ```

12. 應會顯示具有兩個 (2) 容器的清單。 這些是 IoT 中樞服務 (edgeAgent 和 edgeHub) 自動建立的預設模組。 一旦您建立並部署自己的模組，它們就會出現在這份清單中的預設下。

## <a name="chapter-6---install-the-extensions"></a>第6章-安裝擴充功能

> [!IMPORTANT]
> 接下來的幾章 (6-9) 要在您的 Windows 10 電腦上執行。

1. 開啟 **VS Code**。

2. 按一下 VS Code 左側工具列上的 [**延伸** 模組] (方塊) 按鈕，以開啟 [**擴充** 功能] 面板。

3. 搜尋並安裝下列擴充功能 (如下圖所示) ：

    1. Azure IoT Edge
    2. Azure IoT 工具組
    3. Docker   

    ![建立您的容器](images/AzureLabs-Lab313-24.png)

4. 安裝延伸模組之後，請關閉並重新開啟 VS Code。

5. VS Code 開啟一次，請流覽至 [ **View**  >  **整合式終端** 機]。

6. 您現在將會安裝 **Cookiecutter**。 在終端機中執行下列 bash 命令：

    ```bash
        pip install --upgrade --user cookiecutter
    ```

    > [!提示]：如果您遇到此命令的問題： 
    >1. 重新開機 VS Code 及/或您的電腦。
    >2. 您可能必須將 **VS Code 終端** 機切換到您用來安裝 python 的終端機，也就是 **Powershell** (尤其是在您的電腦上已安裝 python 環境) 時。 當終端機開啟時，您會在終端機右邊找到下拉式功能表。
     ![建立您的容器](images/AzureLabs-Lab313-24b.png) 
    >3. 請確定已在您的電腦上將 **Python** 安裝路徑新增為 **環境變數** 。 Cookiecutter 應該是相同位置路徑的一部分。 [如需環境變數的詳細資訊](/windows/win32/procthread/environment-variables)，請遵循此連結。 

7. **Cookiecutter** 完成安裝之後，您應該重新開機電腦，讓 **Cookiecutter** 在您的系統內容內被辨識為命令。

## <a name="chapter-7---create-your-container-solution"></a>第7章-建立您的容器解決方案

此時，您必須使用模組來建立容器，以推送至 *容器* 登錄。 推送您的容器之後，您將使用 *IoT 中樞 Edge* 服務，將其部署至執行 *IoT Edge 運行* 時間的裝置。

1. 在 VS Code 中，按一下 [ **View**  >  **命令** 選擇區]。

2. 在 [元件] 中，搜尋並執行 **Azure IoT Edge：新增 IoT Edge 解決方案**。

3. 流覽至您想要建立方案的位置。 按下 **enter** 鍵以接受位置。

4. 為您的方案提供名稱。 按下 **enter** 鍵，確認您提供的名稱。

5. 現在，系統會提示您選擇解決方案的範本架構。 按一下 [ **Python 模組**]。 按下 **enter** 鍵，確認這項選擇。

6. 為您的模組提供名稱。 按下 **enter** 鍵，確認您的模組名稱。 請務必記下您的記事本) 模組名稱 (，因為稍後會用到。

7. 您將會注意到，預先建立的 *Docker 映射存放庫* 位址會出現在 [選擇區] 中。 它看起來會像這樣：

    **localhost： 5000/-模組的名稱**。 

8. 刪除 **localhost： 5000**，並在其位置插入 *容器***登錄登入伺服器** 位址，此位址是您 [在步驟8中](#chapter-2---the-container-registry-service)建立 **容器登錄服務** 時所記下的 () 第2章。 按下 **enter** 鍵以確認位址。

9. 此時，將會建立包含 Python 模組範本的方案，而且其結構會顯示在畫面左側的 [**流覽]** 索引標籤中 VS Code。 如果 [ **流覽]** 索引標籤未開啟，您可以按一下左側列中最上方的按鈕來開啟它。

    ![建立您的容器](images/AzureLabs-Lab313-25.png)

10. 本章的最後一個步驟，是從 [**流覽]** 索引標籤中按一下並開啟 **env** 檔案，然後新增您的 *容器* 登錄使用者 **名稱** 和 **密碼**。 Git 會忽略此檔案，但在建立容器時，將會設定認證以存取 **Container Registry 服務**。

    ![建立您的容器](images/AzureLabs-Lab313-26.png)

## <a name="chapter-8---editing-your-container-solution"></a>第8章-編輯容器解決方案

您現在會更新下列檔案來完成容器解決方案：

- *<span></span> .py* python 腳本。
- *requirements.txt*。
- *deployment.template.js開啟*。
- *Dockerfile amd64*

然後，您將建立 [ *images* ] 資料夾，供 python 腳本用來檢查要符合 *自訂視覺模型* 的影像。 最後，您會新增 *labels.txt* 檔案，以協助您讀取模型，以及 *模型* 的檔案（即您的模型）。

1. 當 VS Code 開啟時，流覽至您的模組資料夾，然後尋找名為 **<span></span> .py** 的腳本。 按兩下將它開啟。

2. 刪除檔案的內容，然後插入下列程式碼：

    ```python
    # Copyright (c) Microsoft. All rights reserved.
    # Licensed under the MIT license. See LICENSE file in the project root for
    # full license information.

    import random
    import sched, time
    import sys
    import iothub_client
    from iothub_client import IoTHubModuleClient, IoTHubClientError, IoTHubTransportProvider
    from iothub_client import IoTHubMessage, IoTHubMessageDispositionResult, IoTHubError
    import json
    import os
    import tensorflow as tf
    import os
    from PIL import Image
    import numpy as np
    import cv2

    # messageTimeout - the maximum time in milliseconds until a message times out.
    # The timeout period starts at IoTHubModuleClient.send_event_async.
    # By default, messages do not expire.
    MESSAGE_TIMEOUT = 10000

    # global counters
    RECEIVE_CALLBACKS = 0
    SEND_CALLBACKS = 0

    TEMPERATURE_THRESHOLD = 25
    TWIN_CALLBACKS = 0

    # Choose HTTP, AMQP or MQTT as transport protocol.  Currently only MQTT is supported.
    PROTOCOL = IoTHubTransportProvider.MQTT


    # Callback received when the message that we're forwarding is processed.
    def send_confirmation_callback(message, result, user_context):
        global SEND_CALLBACKS
        print ( "Confirmation[%d] received for message with result = %s" % (user_context, result) )
        map_properties = message.properties()
        key_value_pair = map_properties.get_internals()
        print ( "    Properties: %s" % key_value_pair )
        SEND_CALLBACKS += 1
        print ( "    Total calls confirmed: %d" % SEND_CALLBACKS )


    def convert_to_opencv(image):
        # RGB -> BGR conversion is performed as well.
        r,g,b = np.array(image).T
        opencv_image = np.array([b,g,r]).transpose()
        return opencv_image

    def crop_center(img,cropx,cropy):
        h, w = img.shape[:2]
        startx = w//2-(cropx//2)
        starty = h//2-(cropy//2)
        return img[starty:starty+cropy, startx:startx+cropx]

    def resize_down_to_1600_max_dim(image):
        h, w = image.shape[:2]
        if (h < 1600 and w < 1600):
            return image

        new_size = (1600 * w // h, 1600) if (h > w) else (1600, 1600 * h // w)
        return cv2.resize(image, new_size, interpolation = cv2.INTER_LINEAR)

    def resize_to_256_square(image):
        h, w = image.shape[:2]
        return cv2.resize(image, (256, 256), interpolation = cv2.INTER_LINEAR)

    def update_orientation(image):
        exif_orientation_tag = 0x0112
        if hasattr(image, '_getexif'):
            exif = image._getexif()
            if (exif != None and exif_orientation_tag in exif):
                orientation = exif.get(exif_orientation_tag, 1)
                # orientation is 1 based, shift to zero based and flip/transpose based on 0-based values
                orientation -= 1
                if orientation >= 4:
                    image = image.transpose(Image.TRANSPOSE)
                if orientation == 2 or orientation == 3 or orientation == 6 or orientation == 7:
                    image = image.transpose(Image.FLIP_TOP_BOTTOM)
                if orientation == 1 or orientation == 2 or orientation == 5 or orientation == 6:
                    image = image.transpose(Image.FLIP_LEFT_RIGHT)
        return image


    def analyse(hubManager):

        messages_sent = 0;

        while True:
            #def send_message():
            print ("Load the model into the project")
            # These names are part of the model and cannot be changed.
            output_layer = 'loss:0'
            input_node = 'Placeholder:0'

            graph_def = tf.GraphDef()
            labels = []

            labels_filename = "labels.txt"
            filename = "model.pb"

            # Import the TF graph
            with tf.gfile.FastGFile(filename, 'rb') as f:
                graph_def.ParseFromString(f.read())
                tf.import_graph_def(graph_def, name='')

            # Create a list of labels
            with open(labels_filename, 'rt') as lf:
                for l in lf:
                    labels.append(l.strip())
            print ("Model loaded into the project")

            results_dic = dict()

            # create the JSON to be sent as a message
            json_message = ''

            # Iterate through images 
            print ("List of images to analyse:")
            for file in os.listdir('images'):
                print(file)

                image = Image.open("images/" + file)

                # Update orientation based on EXIF tags, if the file has orientation info.
                image = update_orientation(image)

                # Convert to OpenCV format
                image = convert_to_opencv(image)

                # If the image has either w or h greater than 1600 we resize it down respecting
                # aspect ratio such that the largest dimension is 1600
                image = resize_down_to_1600_max_dim(image)

                # We next get the largest center square
                h, w = image.shape[:2]
                min_dim = min(w,h)
                max_square_image = crop_center(image, min_dim, min_dim)

                # Resize that square down to 256x256
                augmented_image = resize_to_256_square(max_square_image)

                # The compact models have a network size of 227x227, the model requires this size.
                network_input_size = 227

                # Crop the center for the specified network_input_Size
                augmented_image = crop_center(augmented_image, network_input_size, network_input_size)

                try:
                    with tf.Session() as sess:     
                        prob_tensor = sess.graph.get_tensor_by_name(output_layer)
                        predictions, = sess.run(prob_tensor, {input_node: [augmented_image] })
                except Exception as identifier:
                    print ("Identifier error: ", identifier)

                print ("Print the highest probability label")
                highest_probability_index = np.argmax(predictions)
                print('FINAL RESULT! Classified as: ' + labels[highest_probability_index])

                l = labels[highest_probability_index]

                results_dic[file] = l

                # Or you can print out all of the results mapping labels to probabilities.
                label_index = 0
                for p in predictions:
                    truncated_probablity = np.float64(round(p,8))
                    print (labels[label_index], truncated_probablity)
                    label_index += 1

            print("Results dictionary")
            print(results_dic)

            json_message = json.dumps(results_dic)
            print("Json result")
            print(json_message)

            # Initialize a new message
            message = IoTHubMessage(bytearray(json_message, 'utf8'))
        
            hubManager.send_event_to_output("output1", message, 0)

            messages_sent += 1
            print("Message sent! - Total: " + str(messages_sent))      
            print('----------------------------')
            
            # This is the wait time before repeating the analysis
            # Currently set to 10 seconds
            time.sleep(10)


    class HubManager(object):
        
        def __init__(
                self,
                protocol=IoTHubTransportProvider.MQTT):
            self.client_protocol = protocol
            self.client = IoTHubModuleClient()
            self.client.create_from_environment(protocol)

            # set the time until a message times out
            self.client.set_option("messageTimeout", MESSAGE_TIMEOUT)

        # Forwards the message received onto the next stage in the process.
        def forward_event_to_output(self, outputQueueName, event, send_context):
            self.client.send_event_async(
                outputQueueName, event, send_confirmation_callback, send_context)

        def send_event_to_output(self, outputQueueName, event, send_context):
            self.client.send_event_async(outputQueueName, event, send_confirmation_callback, send_context)

    def main(protocol):
        try:
            hub_manager = HubManager(protocol)
            analyse(hub_manager)
            while True:
                time.sleep(1)

        except IoTHubError as iothub_error:
            print ( "Unexpected error %s from IoTHub" % iothub_error )
            return
        except KeyboardInterrupt:
            print ( "IoTHubModuleClient sample stopped" )

    if __name__ == '__main__':
        main(PROTOCOL)
    ```

3.  開啟稱為 **requirements.txt** 的檔案，並以下列內容取代其內容：

    ```
    azure-iothub-device-client==1.4.0.0b3
    opencv-python==3.3.1.11
    tensorflow==1.8.0
    pillow==5.1.0
    ```

4.  開啟稱為 **deployment.template.js** 的檔案，並將其內容取代為下列指導方針：

    1. 由於您將擁有自己的唯一 JSON 結構，因此您必須手動編輯它 (而不是複製範例) 。 若要這麼做，請使用下圖作為指南。
    2. 看起來會與您不同，但您 **不應該變更的區域會以黃色反白顯示**。
    3. **您需要刪除的區段會以反白顯示紅色。**
    4. 請小心刪除正確的括弧，同時移除逗號。

        ![建立您的容器](images/AzureLabs-Lab313-27.png)

    5. 完成的 JSON 看起來應該像下列映射 (但唯一的差異：使用者 *名稱/密碼/模組名稱/模組參考*) ：

        ![建立您的容器](images/AzureLabs-Lab313-28.png)

5.  開啟名為 **Dockerfile** 的檔案，並以下列內容取代其內容：

    ```
    FROM ubuntu:xenial

    WORKDIR /app

    RUN apt-get update && \
        apt-get install -y --no-install-recommends libcurl4-openssl-dev python-pip libboost-python-dev && \
        rm -rf /var/lib/apt/lists/* 
    RUN pip install --upgrade pip
    RUN pip install setuptools

    COPY requirements.txt ./
    RUN pip install -r requirements.txt

    RUN pip install pillow
    RUN pip install numpy

    RUN apt-get update && apt-get install -y \ 
        pkg-config \
        python-dev \ 
        python-opencv \ 
        libopencv-dev \ 
        libav-tools  \ 
        libjpeg-dev \ 
        libpng-dev \ 
        libtiff-dev \ 
        libjasper-dev \ 
        python-numpy \ 
        python-pycurl \ 
        python-opencv


    RUN pip install opencv-python
    RUN pip install tensorflow
    RUN pip install --upgrade tensorflow

    COPY . .

    RUN useradd -ms /bin/bash moduleuser
    USER moduleuser

    CMD [ "python", "-u", "./main.py" ]

    ```

6.  以滑鼠右鍵按一下 [ **模組** ] 下的資料夾 (它將擁有您先前提供的名稱;在此範例中，它稱為 *pythonmodule*) ，然後按一下 [ **新增資料夾**]。 命名資料夾 **映射**。

7.  在資料夾內，新增包含滑鼠或鍵盤的一些影像。 這些將會是 Tensorflow 模型將分析的影像。

    > [!WARNING]
    > 如果您要使用自己的模型，您必須變更此模型，以反映您自己的模型資料。

8.  您現在需要從 [模型] 資料夾中取出 **labels.txt** 和 **model. pb** 檔案，您先前已從 [第1章](#chapter-1---retrieve-the-custom-vision-model)中下載 (或從自己的 **自訂視覺服務**) 建立這些檔案。 擁有檔案之後，請將它們放在您的方案中，連同其他檔案。 最後的結果看起來應該如下圖所示：

    ![建立您的容器](images/AzureLabs-Lab313-29.png)

## <a name="chapter-9---package-the-solution-as-a-container"></a>第9章-將解決方案封裝為容器

1.  您現在已準備好將檔案「封裝」為容器，並將其推送到您的 **Azure Container Registry**。 在 VS Code 中，開啟 [*整合式終端* 機] (**View**  >  **整合式終端** 機或 **Ctrl** + **\`**) ，然後使用下列命令列登入 **Docker** (將命令的值取代為您 Azure Container Registry (**ACR)**) 的認證：

    ```bash
        docker login -u <ACR username> -p <ACR password> <ACR login server>
    ```

2. 以滑鼠右鍵按一下 **deployment.template.js** 的檔案，然後按一下 [ **建立 IoT Edge 方案**]。 視您的裝置) 而定，此組建程式需要一些時間 (，因此請準備等候。 組建程式完成之後，就會在名為 **config** 的新資料夾內建立檔案 **deployment.js** 。

    ![建立部署](images/AzureLabs-Lab313-30.png)

3. 再次開啟 **命令** 選擇區，然後搜尋 **Azure：登入**。 遵循使用您的 Azure 帳號憑證的提示;VS Code 會提供您 *複製和開啟* 的選項，這會複製您即將需要的裝置程式碼，並開啟您的預設網頁瀏覽器。 當系統詢問時，貼上裝置程式碼以驗證您的電腦。

    ![複製並開啟](images/AzureLabs-Lab313-31.png)

4. 登入後，您會在 [*探索*] 面板的底部看到一個稱為 **Azure IoT Hub 裝置**」的新區段。 按一下此區段將其展開。

    ![edge 裝置](images/AzureLabs-Lab313-32.png)

5. 如果您的裝置不在此，您必須以滑鼠右鍵按一下 *Azure IoT Hub 裝置*]，然後按一下 [**設定 IoT 中樞連接字串**]。 接著，您會看到 VS Code) 頂端 (的 **命令** 選擇區會提示您輸入 *連接字串*。 這是您在 [第3章](#chapter-3---the-iot-hub-service)結尾處記下的 *連接字串*。 當您在中複製字串之後，請按 **enter** 鍵。    

6. 您的裝置應該會載入並顯示。 以滑鼠右鍵按一下裝置名稱，然後按一下 [ **建立單一裝置的部署**]。

    ![建立部署](images/AzureLabs-Lab313-33b.png)

7. 您會收到 *檔案總管* 提示字元，您可以在其中流覽至 [ **config** ] 資料夾，然後選取 [檔案 **上的deployment.js** ]。 選取該檔案之後，按一下 [ **選取 Edge 部署資訊清單** ] 按鈕。

    ![建立部署](images/AzureLabs-Lab313-34.png)

8. 至此，您已為 **IoT 中樞服務** 提供資訊清單，以便從您的 **Azure Container Registry** 將容器部署為模組，以將其有效地部署到您的裝置。

9. 若要查看從您的裝置傳送到 IoT 中樞的訊息，請在 [D2C **Hub 裝置**] 區段的 [ **Explorer** ] 面板中，再次以滑鼠右鍵按一下裝置 Azure IoT 名稱，然後按一下 [**開始監視訊息**]。 從您的裝置傳送的訊息應該會出現在 VS 終端機中。 請耐心等候，因為這可能需要一些時間。 請參閱下一章以進行偵錯工具，並檢查部署是否成功。

此模組現在會在每次反復專案時，逐一查看 **images** 資料夾中的影像並分析它們。 這顯然只是示範如何讓基本的機器學習模型在 IoT Edge 的裝置環境中運作。 

若要擴充此範例的功能，您可以透過數種方式進行。 其中一種方式可能包括容器中的一些程式碼，該程式碼會從連線到裝置的網路攝影機捕獲相片，並將影像儲存在 images 資料夾中。 

另一種方式是將映射從 IoT 裝置複製到容器中。 作法是在 IoT 裝置 (終端機中執行下列命令，如此一來，如果您想要自動執行程式) ，那麼小型應用程式可能會執行此作業。 您可以從儲存檔案的資料夾位置，以手動方式執行此命令來測試此命令：

```bash
    sudo docker cp <filename> <modulename>:/app/images/<a name of your choice>
```

## <a name="chapter-10---debugging-the-iot-edge-runtime"></a>第10章-調試 IoT Edge 執行時間

以下是命令列清單和秘訣，可協助您從 **Ubuntu 裝置** 監視和偵測 *IoT Edge 運行* 時間的訊息活動。 

- 執行下列命令列，以檢查 *IoT Edge 運行* 時間狀態：

    ```bash
        sudo systemctl status iotedge
    ```

    > [!NOTE]
    > 請記得按 **Ctrl + C**，以完成狀態的查看。

- 列出目前已部署的容器。 如果 *IoT 中樞服務* 已成功部署容器，則會藉由執行下列命令列來顯示它們：

    ```bash
        sudo iotedge list
    ```

    Or

    ```bash
        sudo docker ps
    ```

    > [!NOTE]
    > 上述是檢查模組是否已成功部署的好方法，因為它會出現在清單中;否則，您 **只** 會看到 *edgeHub* 和 *edgeAgent*。

- 若要顯示容器的程式碼記錄，請執行下列命令列：

    ```bash
        journalctl -u iotedge
    ```

**用來管理 IoT Edge 執行時間的有用命令：**

-  若要刪除主機中的所有容器：

    ```bash
        sudo docker rm -f $(sudo docker ps -aq)
    ```

-  若要停止 *IoT Edge 運行* 時間：

    ```bash
        sudo systemctl stop iotedge
    ```

## <a name="chapter-11---create-table-service"></a>第11章-建立表格服務 

藉由建立儲存體資源，流覽回到您的 Azure 入口網站，您將在其中建立 Azure 資料表服務。

1. 如果還沒有登入，請登入 [Azure 入口網站](https://portal.azure.com)。

2. 登入後，按一下左上角的 [**建立資源**]，並搜尋 **儲存體帳戶**，然後按下 **enter** 鍵以開始搜尋。

3. 出現之後，請從清單中按一下 **儲存體帳戶-blob、檔案、資料表、佇列**。

    ![搜尋儲存體帳戶](images/AzureLabs-Lab313-35.png)

4. 新頁面將提供 **儲存體帳戶** 服務的描述。 在此提示的左下方，按一下 [ **建立** ] 按鈕以建立此服務的實例。

    ![建立儲存體實例](images/AzureLabs-Lab313-36.png)

5. 一旦您按一下 [ **建立**]，將會出現一個面板：

    1. 為此服務實例插入您想要的 **名稱** (*必須全部都是小寫*) 。

    2. 若為 **部署模型**，請按一下 [ **Resource manager**]。

    3. For **Account kind**, using the dropdown menu, click **Storage (general purpose v1)**.

    4. 按一下適當的 **位置**。
    
    5. **在 [** 複寫] 下拉式功能表中，按一下 [**讀取權限-異地-多餘儲存體] (GRS])**。

    6. 針對 [ **效能**]，請按一下 [ **標準**]。

    7. 在 [ **需要安全傳輸** ] 區段中，按一下 [ **已停用**]。

    8. 從 [ **訂** 用帳戶] 下拉式功能表中，按一下適當的訂用帳戶。

    9. 選擇資源群組，或建立一個新的 **資源群組** 。 資源群組可讓您監視、控制存取、布建及管理 Azure 資產集合的計費方式。 建議您保留與單一專案相關聯的所有 Azure 服務 (例如，) 一般資源群組下的這些課程) 。

        > 如果您想要深入瞭解 Azure 資源群組，請遵循此 [連結，以瞭解如何管理資源群組](/azure/azure-resource-manager/resource-group-portal)。

    10. 如果這是您可以選擇的選項，請將 **虛擬網路** 保留為 **已停用**。

    11. 按一下 [建立]。

        ![填入儲存體詳細資料](images/AzureLabs-Lab313-37.png)

6. 當您按一下 [ **建立**] 之後，就必須等待服務建立完成，這可能需要一分鐘的時間。

7. 建立服務實例之後，入口網站中就會出現通知。 按一下通知以探索新的服務實例。

    ![新儲存體通知](images/AzureLabs-Lab313-38.png)

8. 按一下通知中的 [**移至資源**] 按鈕，系統會將您帶到新的儲存體服務實例的 [總覽] 頁面。

    ![移至資源](images/AzureLabs-Lab313-39.png)

9. 從 [總覽] 頁面的右側，按一下 [ **資料表]**。
    
    ![資料表](images/AzureLabs-Lab313-40.png)

10. 右側的面板將會變更，以顯示 **資料表服務** 資訊，您需要在其中加入新的資料表。 若要這麼做，請按一下左上角的 [ **+ 資料表** ] 按鈕。

    ![開啟資料表](images/AzureLabs-Lab313-41.png)

11. 將會顯示新的頁面，您必須在其中輸入 **資料表名稱**。 這是您將在稍後的章節中用來參考應用程式中資料的名稱 (建立函數應用程式，並 Power BI) 。 將 **IoTMessages** 插入 (您可以自行選擇的名稱，只要在本檔稍後使用時記住它) 然後按一下 **[確定]**。 

12. 建立新的資料表之後，您將能夠在底部) 的 [ **表格服務** ] 頁面 (中看到它。

    ![已建立新的資料表](images/AzureLabs-Lab313-42.png)  

13. 現在，按一下 [**存取金鑰**]，並使用您的記事本) 複製 **儲存體的帳戶名稱** 和 **金鑰** (，稍後在本課程中建立 **Azure 函數應用程式** 時，將會使用這些值。

    ![已建立新的資料表](images/AzureLabs-Lab313-43.png) 

14. 使用左邊的面板，移至 [*表格服務* **]** 區段，然後按一下 [資料表] (或 **[流覽資料表]**，在較新的入口網站中) ，然後使用記事本) 取得 **資料表 URL** 的複本 (。 當您將資料表連結至 **Power BI** 應用程式時，您稍後會在本課程中使用此值。

    ![已建立新的資料表](images/AzureLabs-Lab313-44.png)

## <a name="chapter-12---completing-the-azure-table"></a>第12章-完成 Azure 資料表

現在您已設定 **表格服務** 儲存體帳戶，接下來可以將資料新增至其中，以用來儲存和取出資訊。 您可以透過 **Visual Studio** 來編輯資料表。

1. 開啟 **Visual Studio** (**不** Visual Studio Code) 。

2. 從功能表中，按一下 [ **View**  >  **Cloud Explorer**]。

    ![開啟 cloud explorer](images/AzureLabs-Lab313-45.png)

3. **Cloud Explorer** 會以停駐的專案開啟 (請耐心等候，因為載入可能需要一些時間) 。

    > [!WARNING] 
    > 如果看不到您用來建立 *儲存體帳戶* 的訂用帳戶，請確定您有： 
    > - 登入與您用於 Azure 入口網站的帳戶相同的帳戶。
    > - 從 [帳戶管理] 頁面中選取您的訂用帳戶 (您可能需要從帳戶設定套用篩選) ：  
    >
    >   ![尋找訂用帳戶](images/AzureLabs-Lab313-46.png)

4. 將會顯示您的 Azure 雲端服務。 尋找 **儲存體帳戶**，然後按一下左邊的箭號展開您的帳戶。

    ![開啟儲存體帳戶](images/AzureLabs-Lab313-47.png)

5. 展開之後，您就可以使用新建立的 **儲存體帳戶**。 按一下儲存體左邊的箭號，然後展開 [尋找 **資料表** ]，然後按一下旁邊的箭號，以顯示您在上一章所建立的 **資料表** 。 按兩下您的 **資料表**。

6. 您的資料表將會在 Visual Studio 視窗的中央開啟。 按一下包含 **+** (加) 的資料表圖示。

    ![加入新的資料表](images/AzureLabs-Lab313-48.png)

7. 系統會出現一個視窗，提示您 *加入實體*。 您只會建立一個實體，但它會有三個屬性。 您將會注意到已提供 *PartitionKey* 和 *RowKey* ，因為資料表會使用這些資料來尋找您的資料。 

    ![分割區和資料列索引鍵](images/AzureLabs-Lab313-49.png)

8. 更新下列值：

    - Name： **PartitionKey**，Value： **PK_IoTMessages** 

    - Name： **RowKey**，Value： **RK_1_IoTMessages** 

9. 然後，按一下 [*新增實體*] 視窗左下角的 [**新增屬性** (]) 並新增下列屬性：

    - 以 *字串* 的形式 **MessageContent**，將值保留空白。

10. 您的資料表應該與下圖中的資料表相符：

    ![新增正確的值](images/AzureLabs-Lab313-50.png)

    > [!NOTE] 
    > 當您想要進一步實驗此課程時，您可能會想要加入更多的訊息，這是因為您可能想要加入更多訊息的原因。

11. 當您完成時，請按一下 **[確定]** 。 您的資料表現在已可供使用。

## <a name="chapter-13---create-an-azure-function-app"></a>第13章-建立 Azure 函數應用程式 

現在，您可以建立 Azure 函 *式應用程式，此應用程式* 將由 *IoT 中樞服務* 呼叫，以將 *IoT Edge* 裝置訊息儲存在您在上一章所建立的 **表格** 服務中。

首先，您必須建立可讓您的 Azure 函式載入所需程式庫的檔案。

1.  開啟 **記事本** (按下 *Windows 鍵*，然後輸入 *記事本*) 。

    ![開啟 [記事本]](images/AzureLabs-Lab313-51.png)

2.  在記事本開啟時，將下列 JSON 結構插入其中。 完成之後，請將它儲存在您的桌面上，作為 **project.js**。 此檔案會定義您的函式將使用的程式庫。 如果您已經使用 NuGet，它看起來會很熟悉。
    
    > [!WARNING]
    > 命名必須正確;確定它沒有 **.txt的** 副檔名。 請參閱下文以取得參考：
    >
    > ![JSON 儲存](images/AzureLabs-Lab313-52.png)

    ```json
    {
    "frameworks": {
        "net46":{
        "dependencies": {
            "WindowsAzure.Storage": "9.2.0"
        }
        }
    }
    }
    ```

3.  登入 [Azure 入口網站](https://portal.azure.com)。

4.  登入後，按一下左上角的 [ **建立資源** ]，並搜尋函式 **應用程式**，然後按下 **enter** 鍵進行搜尋。 從結果按一下 [ *函數應用程式* ]，以開啟新的面板。

    ![搜尋函數應用程式](images/AzureLabs-Lab313-53.png)

5.  新的面板會提供 **函數應用程式** 服務的描述。 在此面板的左下方，按一下 [ **建立** ] 按鈕，以建立與此服務的關聯。

    ![函數應用程式實例](images/AzureLabs-Lab313-54.png)

6.  按一下 [ **建立**] 之後，請填寫下列內容：

    1. 針對 [ **應用程式名稱**]，插入您想要的此服務實例名稱。

    2. 選取 [訂用帳戶]  。

    3. 選取適合您的定價層，如果這是您第一次建立函式 **App Service**，則應可使用免費層。

    4. 選擇資源群組，或建立一個新的 **資源群組** 。 資源群組可讓您監視、控制存取、布建及管理 Azure 資產集合的計費方式。 建議您保留與單一專案相關聯的所有 Azure 服務 (例如，) 一般資源群組下的這些課程) 。

        > 如果您想要深入瞭解 Azure 資源群組，請遵循此 [連結，以瞭解如何管理資源群組](/azure/azure-resource-manager/resource-group-portal)。

    5. 針對 **OS**，請按一下 [Windows，因為這是預期的平臺。

    6.  (本教學課程使用取用 **方案**，請選取 **主控方案**。

    7. 選取 **位置** (選擇與您在上一個步驟中建立的儲存體相同的位置) 

    8. 在 [**儲存體**] 區段中，**您必須選取您在上一個步驟中建立的儲存體服務**。

    9. 您將不需要在此應用程式中 *Application Insights* ，因此請隨時將 **其保留**。

    10. 按一下 [建立]。

        ![建立新的實例](images/AzureLabs-Lab313-55.png)

7.  當您按一下 [ **建立**] 之後，就必須等待服務建立完成，這可能需要一分鐘的時間。

8.  建立服務實例之後，入口網站中就會出現通知。

    ![新通知](images/AzureLabs-Lab313-56.png)

9.  當部署成功之後，請按一下通知 (完成) 。

10. 按一下通知中的 [ **移至資源** ] 按鈕，以流覽您的新服務實例。 

    ![移至資源](images/AzureLabs-Lab313-57.png)

11. 在新面板的左側，按一下 [函式 **+** ] 旁的 (加號) 圖示，以建立新的函式。

    ![新增函數](images/AzureLabs-Lab313-58.png)

12. 在中央面板中，會出現 [ **函數** 建立] 視窗。 再向下滾動，然後按一下 [ **自訂** 函式]。

    ![自訂函式](images/AzureLabs-Lab313-59.png)

13. 向下一頁，直到您找到 **IoT 中樞 (事件中樞)**，然後按一下它。

    ![自訂函式](images/AzureLabs-Lab313-60.png)

14. 在 **IoT 中樞的 (事件中樞)** ] 分頁中， **將語言** 設定為 **c #** ，然後按一下 [ **新增**]。

    ![自訂函式](images/AzureLabs-Lab313-61.png)

15. 在出現的視窗中，確定已選取 [ **Iot 中樞**]，而 [ *iot 中樞*] 欄位的名稱對應至您先前 [在步驟8中建立的](#chapter-3---the-iot-hub-service) *Iot 中樞服務* 名稱 (第3章) 。 然後按一下 [ **選取** ] 按鈕。

    ![自訂函式](images/AzureLabs-Lab313-62.png)

16. 回到 **(事件中樞) 分頁的 IoT 中樞** ，然後按一下 [ **建立**]。

    ![自訂函式](images/AzureLabs-Lab313-63.png)

17. 系統會將您重新導向至函數編輯器。

    ![自訂函式](images/AzureLabs-Lab313-64.png)

18. 刪除其中的所有程式碼，並將它取代為下列程式碼：

    ```csharp
    #r "Microsoft.WindowsAzure.Storage"
    #r "NewtonSoft.Json"

    using System;
    using Microsoft.WindowsAzure.Storage;
    using Microsoft.WindowsAzure.Storage.Table;
    using Newtonsoft.Json;
    using System.Threading.Tasks;

    public static async Task Run(string myIoTHubMessage, TraceWriter log)
    {
        log.Info($"C# IoT Hub trigger function processed a message: {myIoTHubMessage}");
        
        //RowKey of the table object to be changed
        string tableName = "IoTMessages";
        string tableURL = "https://iothubmrstorage.table.core.windows.net/IoTMessages";

        // If you did not name your Storage Service as suggested in the course, change the name here with the one you chose.
        string storageAccountName = "iotedgestor"; 

        string storageAccountKey = "<Insert your Storage Key here>";   

        string partitionKey = "PK_IoTMessages";
        string rowKey = "RK_1_IoTMessages";

        Microsoft.WindowsAzure.Storage.Auth.StorageCredentials storageCredentials =
            new Microsoft.WindowsAzure.Storage.Auth.StorageCredentials(storageAccountName, storageAccountKey);

        CloudStorageAccount storageAccount = new CloudStorageAccount(storageCredentials, true);

        // Create the table client.
        CloudTableClient tableClient = storageAccount.CreateCloudTableClient();

        // Get a reference to a table named "IoTMessages"
        CloudTable messageTable = tableClient.GetTableReference(tableName);

        //Retrieve the table object by its RowKey
        TableOperation operation = TableOperation.Retrieve<MessageEntity>(partitionKey, rowKey);
        TableResult result = await messageTable.ExecuteAsync(operation);

        //Create a MessageEntity so to set its parameters
        MessageEntity messageEntity = (MessageEntity)result.Result;

        messageEntity.MessageContent = myIoTHubMessage;
        messageEntity.PartitionKey = partitionKey;
        messageEntity.RowKey = rowKey;

        //Replace the table appropriate table Entity with the value of the MessageEntity Ccass structure.
        operation = TableOperation.Replace(messageEntity);

        // Execute the insert operation.
        await messageTable.ExecuteAsync(operation);
    }

    // This MessageEntity structure which will represent a Table Entity
    public class MessageEntity : TableEntity
    {
        public string Type { get; set; }
        public string MessageContent { get; set; }   
    }
    ```

19. 變更下列變數，讓它們分別對應至第11章) 的適當值 (**資料表** 和 **儲存體** 值，[分別位於第11章的步驟11和 13](#chapter-11---create-table-service) ，您將會在 **儲存體帳戶** 中找到這些變數：

    - **tableName**，以您的 **資料表** 名稱位於您的 **儲存體帳戶** 中。
    - **tableURL**，並以您的 **儲存體帳戶** 中的 **資料表** URL 為開頭。
    - **storageAccountName**，加上與您的 **儲存體帳戶** 名稱名稱相對應的值名稱。
    - **storageAccountKey**，使用您在先前建立的儲存體服務中取得的金鑰。

    ![自訂函式](images/AzureLabs-Lab313-65.png)

20. 在程式碼就緒後，按一下 [ **儲存**]。

21. 接著，按一下 **\<** 頁面右手邊的 (箭號) 圖示。

    ![自訂函式](images/AzureLabs-Lab313-66.png)

22. 面板將會從右側滑入。 在該面板中，按一下 [ **Upload**]，[檔案 *瀏覽器*] 隨即出現。

23. 流覽至您在先前 **記事本** 中建立的 **project.json** 檔案，然後按一下 [**開啟**] 按鈕。 此檔案會定義您的函式將使用的程式庫。

    ![自訂函式](images/AzureLabs-Lab313-67.png)

24. 檔案上傳後，就會出現在右側面板中。 按一下它會在 **函數** 編輯器中開啟它。 它看起來必須與下一個影像 **完全** 相同。

    ![自訂函式](images/AzureLabs-Lab313-68.png)

25. 此時，測試您的函式將訊息儲存在 *資料表* 上的功能是很好的。 在視窗的右上角，按一下 [ **測試**]。

    ![自訂函式](images/AzureLabs-Lab313-69.png)

26. 在 **要求主體** 上插入訊息（如上圖所示），然後按一下 [ **執行**]。 

27. 函式將會執行，並顯示結果狀態 (您會注意到 [*輸出*] 視窗上方已 **接受綠色狀態 202**，這表示已成功呼叫) ：

    ![輸出結果](images/AzureLabs-Lab313-70.png)

## <a name="chapter-14---view-active-messages"></a>第14章-查看作用中的訊息

如果您現在開啟 Visual Studio (**不** Visual Studio Code) ，則可以將測試訊息結果視覺化，因為它會儲存在 *MessageContent* 字串區域中。

![自訂函式](images/AzureLabs-Lab313-71.png)

使用表格服務和函式應用程式時，您的 Ubuntu 裝置訊息將會出現在您的 *IoTMessages* 資料表中。 如果尚未執行，請重新開機您的裝置，您將能夠使用 Visual Studio *Cloud Explorer*，在您的資料表中看到來自您的裝置和模組的結果訊息。

![將資料視覺化](images/AzureLabs-Lab313-72.png)


## <a name="chapter-15---power-bi-setup"></a>第15章-Power BI 設定

若要將 IOT 裝置的資料視覺化，您將會設定 **Power BI** (desktop 版本) ）從您剛才建立的 *資料表* 服務中收集資料。 *HoloLens* 版的 Power BI 接著會使用該資料來將結果視覺化。

1.  開啟 Windows 10 上的 Microsoft Store 並搜尋 **Power BI Desktop**。

    ![Power BI](images/AzureLabs-Lab313-73.png)

2.  下載應用程式。 完成下載後，請開啟它。

3.  使用您的 **Microsoft 365 帳戶** 登入 *Power BI* 。 您可能會被重新導向至瀏覽器以進行註冊。 註冊之後，請回到 Power BI 的應用程式，然後再次登入。

4.  按一下 [ **取得資料** ]，然後按一下 [ **其他**]。

    ![Power BI](images/AzureLabs-Lab313-74.png)

5.  按一下 [ **azure**]、[ **azure 資料表儲存體**]，然後按一下 [**連線**]。

    ![Power BI](images/AzureLabs-Lab313-75.png)

6.  當您建立資料表服務時，系統會提示您插入 [第11章的步驟13中](#chapter-11---create-table-service)所收集的 **資料表 URL** () 。 插入 URL 之後，請在此課程) 中，刪除參考「子資料夾」 (資料表的部分。 最終結果應如下圖所示。 然後按一下 **[確定]**。

    ![Power BI](images/AzureLabs-Lab313-76.png)

7.  當您儲存體建立資料表時，系統會提示您插入 [第) 11 章的步驟11中](#chapter-11---create-table-service)所記下的 **儲存體機碼** (。 然後按一下 [**連線**]。

    ![Power BI](images/AzureLabs-Lab313-77.png)  

8. [導覽 **器] 面板** 隨即顯示，勾選您資料表旁的方塊，然後按一下 [ **載入**]。

    ![Power BI](images/AzureLabs-Lab313-78.png)  

9. 您的資料表現在已載入 Power BI，但需要查詢才能在其中顯示值。 若要這樣做，請以滑鼠右鍵按一下位於畫面右側 [ **欄位] 面板** 中的資料表名稱。 然後按一下 [ **編輯查詢**]。

    ![Power BI](images/AzureLabs-Lab313-79.png) 

10. **Power Query 編輯器** 會以新視窗的形式開啟，並顯示您的資料表。 按一下資料表 *內容* 資料行內的文字 **記錄**，將儲存的內容視覺化。

    ![Power BI](images/AzureLabs-Lab313-80.png)    

11. 按一下視窗左上方的 [移 **至資料表**]。 

    ![Power BI](images/AzureLabs-Lab313-81.png)

12. 按一下 [ **關閉] &**[套用]。

    ![Power BI](images/AzureLabs-Lab313-82.png)

13. 完成載入查詢之後，請在 [欄位] **面板** 中，將對應至 [參數 **名稱** ] 和 [ **值**] 的方塊勾選，以將 **MessageContent** 資料行內容視覺化。

    ![Power BI](images/AzureLabs-Lab313-83.png)

14. 按一下視窗左上角的 **藍色磁片圖示** ，將您的工作儲存在您選擇的資料夾中。

    ![Power BI](images/AzureLabs-Lab313-84.png)

15. 您現在可以按一下 [發佈] 按鈕，將您的資料表上傳至您的工作區。 提示時，按一下 [ **我的工作區** ]，然後按一下 [ *選取*]。 等候它顯示提交的成功結果。

    ![Power BI](images/AzureLabs-Lab313-85.png)

    ![Power BI](images/AzureLabs-Lab313-86.png)

> [!WARNING]
> 下一章是 HoloLens 特定的。 Power BI 目前無法做為沉浸式應用程式使用，不過您可以在 Windows Mixed Reality 入口網站中執行桌上出版本， (也可以透過桌面應用程式懸崖之屋) 。

## <a name="chapter-16---display-power-bi-data-on-hololens"></a>第16章-在 HoloLens 上顯示 Power BI 資料

1. 在您的 HoloLens 上，藉由在應用程式清單中使用其圖示來登入 **Microsoft Store**。

    ![Power BIH L](images/AzureLabs-Lab313-87.png)

2. 搜尋 **Power BI** 應用程式，然後加以下載。

    ![Power BIH L](images/AzureLabs-Lab313-88.png)

3. 從應用程式清單中開始 **Power BI** 。 

4. **Power BI** 可能會要求您登入 **Microsoft 365 帳戶**。

5. 在應用程式中，工作區預設應會顯示，如下圖所示。 如果沒有發生這種情況，只要按一下視窗左側的工作區圖示即可。

    ![Power BIH L](images/AzureLabs-Lab313-89.png)

## <a name="your-finished-your-iot-hub-application"></a>您已完成 IoT 中樞應用程式

恭喜，您已成功建立具有模擬虛擬機器 Edge 裝置的 IoT 中樞服務。 您的裝置可以將機器學習模型的結果傳達給 azure 資料表服務，並由 azure 函式應用程式所促進，此應用程式會讀取 Power BI，並在 Microsoft HoloLens 內進行視覺化。
 
![Power BI](images/AzureLabs-Lab313-00.png)

## <a name="bonus-exercises"></a>額外練習

### <a name="exercise-1"></a>練習 1

展開儲存在資料表中的訊息結構，並將其顯示為圖形。 您可能會想要收集更多資料，並將它儲存在相同的資料表中，以便稍後顯示。

### <a name="exercise-2"></a>練習 2

建立要在 IoT 板上部署的額外「相機捕捉」模組，讓它可以透過相機來捕捉影像以進行分析。
