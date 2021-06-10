---
title: 6. 封裝並部署至裝置或模擬器
description: 教學課程系列的第 6 部分 (共有 6 部分)，使用 Unreal Engine 4 和混合實境工具組 UX 工具外掛程式來建置國際象棋應用程式
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 混合實境, 教學課程, 開始使用, mrtk, uxt, UX 工具, 文件, 混合實境頭戴式裝置, windows 混合實境頭戴式裝置, 虛擬實境頭戴式裝置
ms.openlocfilehash: 7dbf72a477f376e338d346965b5276eba00ab543
ms.sourcegitcommit: 4a6c26615d52776bdc4faab70391592092a471fc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2021
ms.locfileid: "110711557"
---
# <a name="6-packaging--deploying-to-device-or-emulator"></a>6.封裝並部署至裝置或模擬器

在上一個教學課程中，您已新增一個簡單按鈕，將棋子重設為其原始位置。 在此最後一節中，您將會準備好要在 HoloLens 2 或模擬器上執行的應用程式。 若有 HoloLens 2，您可以從電腦串流或封裝應用程式，以直接在裝置上執行。 如果沒有裝置，您會封裝應用程式以在模擬器上執行。 本節結束時，您將會有一個可以播放的已部署混合實境應用程式，這是透過互動和 UI 完成的。

## <a name="objectives"></a>目標

* [僅限裝置] 利用全像應用程式遠端處理串流至 HoloLens 2
* 封裝應用程式並將其部署至 HoloLens 2 裝置或模擬器

## <a name="device-only-streaming"></a>[僅限裝置] 串流

[全像遠端處理](/windows/mixed-reality/add-holographic-remoting)表示將電腦或獨立 UWP 裝置中的資料串流至 HoloLens 2，而不是切換管道。 遠端主機應用程式會從 HoloLens 接收輸入資料流程、在虛擬沉浸式檢視中呈現內容，以及透過 Wi-fi 將內容框架串流回 HoloLens。 串流可讓您將遠端沉浸式檢視新增至現有的桌上型電腦軟體，並可存取更多系統資源。

如果您是使用國際象棋應用程式前往此路由，將需要進行一些事項：

1.  從您的 HoloLens 2 上的 Microsoft Store 安裝 **全像攝影遠端播放程式** 並執行應用程式。 請記下應用程式中顯示的 IP 位址。
    * 移至 [編輯] > [專案設定]，並確定將 Windows [預設 RHI] 設定為 [預設] 或 [D3D11]：

![預設 RHI](../images/unreal/performance-recommendations-img-09.png)

2.  回到 [Unreal 編輯器] 中，移至 [**編輯 > 專案設定**]，然後核取 [**開啟 XR** 全像 remoting] 區段中的 [**啟用遠端** 功能]。

3.  重新啟動編輯器，然後輸入您裝置的 IP 位址 (如全像遠端處理播放程式中所顯示)，接著按一下 [連線]。

連線之後，請按一下 [播放] 按鈕右邊的下拉箭號，然後選取 [VR 預覽]。 應用程式會在 [VR 預覽] 視窗中執行，進而串流至 HoloLens 頭戴式裝置。

## <a name="packaging-and-deploying-the-app-via-device-portal"></a>透過裝置入口網站封裝和部署應用程式

>[!NOTE]
>如果這是您第一次為適用於 HoloLens 的 Unreal 應用程式進行封裝，則需從 Epic Launcher 下載支援的檔案。
>- 移至 [編輯器喜好設定] > [一般] > [原始程式碼] > [原始程式碼編輯器]，並確認已選取 [Visual Studio 2019]。
>- 移至 Epic Games Launcher 中的 [程式庫] 索引標籤、選取 [啟動] 旁邊的下拉箭號，然後按一下 [選項]。
>- 在 [目標平台] 中，選取 **HoloLens 2**，然後按一下 [套用]。
>![變更專案設定中的目標平台](images/unreal-uxt/6-installationoptions.PNG)

1.  移至 [編輯] > [專案設定]。
    * 在 [專案] > [描述] > [關於] > [專案名稱] 底下，新增專案名稱。
    * 在 [專案] > [描述] > [發行者] > [公司辨別名稱] 底下，新增 **CN=YourCompanyName**。
    * 在 [專案] > [描述] > [設定] 底下，選取 [在 VR 中啟動]。

> [!IMPORTANT]
> 當您嘗試在步驟 3 中產生新的憑證時，將其中一個欄位留空會導致錯誤。

> [!IMPORTANT]
> 發行者的名稱必須採用 [LADPv3 辨別名稱格式](https://www.ietf.org/rfc/rfc2253.txt)。 若發行者名稱的格式不正確，在封裝時將會導致「找不到簽署金鑰。 無法以數位方式簽署應用程式。」 錯誤。

> [!IMPORTANT]
> 若未選取 [在 VR 中啟動]，將導致應用程式嘗試在平板中啟動

![專案設定 - 描述](images/unreal-uxt/6-cn-new.PNG)

2.  在 [平台] > [HoloLens] 底下，啟用 [針對 HoloLens 模擬進行建置] 和/或 [針對 HoloLens 裝置進行建置]。

3.  按一下 [封裝] 區段 (在 [簽署憑證] 旁邊) 中的 [產生新項目]。

> [!IMPORTANT]
> 如果您使用的是已產生的憑證，則憑證的發行者名稱必須與應用程式的發行者名稱相同。 否則將會導致「找不到簽署金鑰。 無法以數位方式簽署應用程式。」 錯誤內容。

![專案設定 - 平台 - HoloLens](images/unreal-uxt/6-packaging.PNG)

4. 當系統提示您建立私密金鑰密碼時，請按一下 [無] 以供測試之用。

![產生新的憑證](images/unreal-uxt/6-private-key-testing.png)

5. 移至 [檔案] > [封裝專案]，然後選取 [HoloLens]。
    * 建立新資料夾來儲存您的封裝，然後按一下 [選取資料夾]。

6.  一旦封裝了應用程式後，請開啟 [Windows 裝置入口網站](/windows/mixed-reality/using-the-windows-device-portal)移至 [檢視] > [應用程式]，然後尋找 [部署應用程式] 區段。

7.  按一下 [瀏覽 ...]、移至您的 **ChessApp.appxbundle** 檔案，然後按一下 [開啟]。

    * 如果這是您第一次在裝置上安裝應用程式，請勾選 [允許我選取架構套件] 旁的方塊。
    * 在下一個對話方塊中，包含適當的 **VCLibs** 和 **appx** 檔案 (若為裝置則為 **arm64**，若為模擬器則為 **x64**)。 您可以在儲存套件的資料夾內 **HoloLens** 底下找到這些檔案。

8.  按一下 [安裝]
    * 您現在可以移至 [所有應用程式]，然後點選新安裝的應用程式來執行，或直接從 **Windows 裝置入口網站** 啟動應用程式。 

恭喜！ 您的 HoloLens 混合實境應用程式已完成，且已可開始使用。 不過，您的體驗尚未結束。 MRTK 有許多獨立功能，您可以將其新增至專案，包括空間對應、注視和語音輸入，甚至是 QR 代碼。 如需這些功能的詳細資訊，請參閱 [Unreal 開發概觀](/windows/mixed-reality/unreal-development-overview)。

## <a name="next-development-checkpoint"></a>下一個開發檢查點

依循我們配置的 Unreal 開發旅程，此時您會探索 MRTK核心建置組塊。 接下來，您可以繼續進行下一個建置組塊：

> [!div class="nextstepaction"]
> [注視輸入](../unreal-gaze-input.md)

或者，直接跳到混合實境平台功能和 API 的主題：

> [!div class="nextstepaction"]
> [HoloLens 相機](../unreal-hololens-camera.md)

您可以隨時回到 [Unreal 開發檢查點](../unreal-development-overview.md#2-core-building-blocks)。