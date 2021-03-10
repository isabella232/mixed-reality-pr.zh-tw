---
title: 歡迎使用 Mixed Reality 功能工具
description: 瞭解 HoloLens 和 VR 開發的 MR 功能工具的基本概念。
author: davidkline-ms
ms.author: v-hferrone
ms.date: 03/04/2021
ms.topic: article
ms.localizationpriority: high
keywords: 最新狀態, 開始使用, 基本概念, unity, visual studio, 工具組, 混合實境頭戴式裝置, windows 混合實境頭戴式裝置, 虛擬實境頭戴式裝置, 安裝, Windows, HoloLens, 模擬器, unreal, openxr
ms.openlocfilehash: 0244c3de51a44ed6d37137a3206b61ca4911f622
ms.sourcegitcommit: ece91dbba40981720fe7e1a7c3b93e8b75ff71ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/10/2021
ms.locfileid: "102547237"
---
# <a name="welcome-to-the-mixed-reality-feature-tool"></a>歡迎使用 Mixed Reality 功能工具

![混合現實功能工具橫幅影像](images/feature-tool-banner.png)

> [!IMPORTANT]
> Mixed Reality 功能工具目前僅適用于 Unity。 如果您是在 Unreal 中進行開發，請參閱 [工具安裝](../install-the-tools.md) 檔。

「混合現實」功能工具是一種新方法，可讓開發人員探索、更新和新增混合現實功能套件至 Unity 專案。 您可以依名稱或類別搜尋套件、查看其相依性，甚至在匯入之前查看專案資訊清單檔的建議變更。 如果您之前從未使用過資訊清單檔，它就是包含所有專案套件的 JSON 檔案。 驗證您想要的封裝之後，混合現實功能工具會將這些套件下載到您選擇的專案。

## <a name="system-requirements"></a>系統需求

在您可以執行混合現實功能工具之前，您需要：

* [.NET 5.0 執行時間](https://dotnet.microsoft.com/download/dotnet/5.0)
* [Windows 10](https://www.microsoft.com/software-download/windows10ISO)

> [!NOTE]
> Mixed Reality 功能工具目前僅在 Windows 上執行，但 MacOS 支援即將推出！

## <a name="download"></a>下載

設定好環境之後：

* 請從 Microsoft 下載中心[下載最新版本的混合現實功能工具](https://aka.ms/MRFeatureTool)。
* 當下載完成時，請將檔案解壓縮，並將它儲存到您的桌面
    * 建議您建立可執行檔的快捷方式，以加快存取的速度

> [!NOTE]
> 如果您不熟悉使用 Unity 套件管理員，請遵循我們的 [UPM 指示](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/configuration/usingupm#managing-mixed-reality-features-with-the-unity-package-manager)。

## <a name="changes-in-this-release"></a>此版本中的變更

版本 1.0.2103 Beta 包含下列修正：

* 下載錯誤偵測的改進。
* 更新資訊清單如何寫入，以避免無法正確更新。
* Escpaing 已從專案資訊清單中的檔案路徑移除。

此版本已新增下列功能：

* 現在會快取功能目錄。 若要檢查是否有新功能和更新，請使用探索中的 [重新整理] 按鈕。
* 將專案選取從匯入步驟移至探索之前。
* 可用的套件會依專案的指定 Unity 版本進行篩選。
* 探索視圖現在會顯示目前已安裝的套件。

## <a name="1-getting-started"></a>1.開始使用

從可執行檔啟動「混合現實」功能工具，其會在第一次啟動時顯示起始頁：

![開始使用](images/FeatureToolStart.png)

從 [開始] 頁面，您可以：

* 使用 **齒輪圖示** 按鈕 [設定](configuring-feature-tool.md)工具設定
* 使用 **問號** 按鈕來啟動預設的網頁瀏覽器，並顯示我們的檔
* 選取 [ **開始** ] 以開始探索功能套件

## <a name="2-selecting-your-unity-project"></a>2. 選取您的 Unity 專案

為確保您專案的 Unity 版本支援所有探索到的功能，第一個步驟是使用 [專案路徑] 欄位) 左邊的 **省略號** 按鈕 (，將 [Mixed Reality] 功能工具指向您的專案。

![選取 Unity 專案](images/FeatureToolSelectUnityProject.png)

> [!NOTE]
> 流覽 Unity 專案資料夾時顯示的對話方塊會包含 ' _ ' 作為檔案名。 檔案名必須有一個值，才能選取該資料夾。

當您找到專案的資料夾時，請按一下 [開啟] 按鈕以返回 [混合現實] 功能工具。

> [!IMPORTANT]
> 「混合現實」功能工具會執行驗證，以確保它已導向至 Unity 專案資料夾。 資料夾必須包含 `Assets` `Packages` 和 `Project Settings` 資料夾。

## <a name="3-discovering-and-acquiring-feature-packages"></a>3. 探索和取得功能套件

> [!NOTE]
> 版本 1.0.2103 Beta 現在會在每次存取伺服器時，快取功能目錄內容。 這項變更可讓您快速存取可用的功能，代價是顯示絕對最新的資料。 若要更新目錄，請 **使用 [重新** 整理] 按鈕。

功能會依類別目錄分組，讓您更容易找到專案。 例如， **Mixed Reality 工具** 組類別有數個功能可供您選擇：

![探索和收購](images/FeatureToolDiscovery.png)

當「混合現實」功能工具辨識先前匯入的功能 (s) 時，它會顯示通知訊息。

![匯入功能的通知](images/feature-tool-imported-note.png)


完成選擇之後，請選取 [ **取得功能** ]，從目錄中提取所有必要的套件。 如需詳細資訊，請參閱 [探索和取得功能](discovering-features.md)。

## <a name="4-importing-feature-packages"></a>4. 匯入功能套件

取得後，會顯示一組完整的封裝，以及必要的相依性清單。 如果您需要變更任何功能或封裝選項，這是時間：

![匯入封裝](images/FeatureToolImport.png)

強烈建議使用 [ **驗證** ] 按鈕，以確保 Unity 專案可以成功匯入選取的功能。 驗證之後，您會看到一個快顯對話方塊，其中包含成功訊息或已識別問題的清單。

選取 [匯 **入** ] 以繼續。

> [!NOTE]
> 按一下 [匯 **入** ] 按鈕之後，如果有任何問題，則會顯示簡單的訊息。 建議您按一下 [否]，並使用 [ **驗證** ] 按鈕來查看和解決問題。

如需詳細資訊，請參閱匯 [入功能](importing-features.md)。

## <a name="5-reviewing-and-approving-project-changes"></a>5. 審核和核准專案變更

最後一個步驟是檢查並核准資訊清單和專案檔案的建議變更：

* 建議的資訊清單變更會顯示在左側
* 要加入至專案的檔案會列在右邊
* [ **比較** ] 按鈕允許並排查看目前的資訊清單和建議的變更

![授權](images/FeatureToolApprovalRequest.png)

如需詳細資訊，請參閱 [審核和核准專案修改](reviewing-changes.md)。

## <a name="6-project-updated"></a>6. 更新專案

當建議的變更經過核准後，您的目標 Unity 專案就會更新，以參考選取的混合現實功能。

![專案已更新](images/FeatureToolProjectUpdated.png)

Unity 專案的 [ **套件** ] 資料夾現在有一個 **MixedReality** 子資料夾，其中包含功能套件檔案 (s) ，資訊清單會包含適當的參考 (s) 。

返回 Unity、等候新選取的功能載入，然後開始建立！

## <a name="see-also"></a>另請參閱

- [設定功能工具](configuring-feature-tool.md)
- [探索和收購](discovering-features.md)
- [查看功能套件詳細資料](viewing-package-details.md)
- [匯入選取的封裝](importing-features.md)
- [審核和核准專案修改](reviewing-changes.md)
