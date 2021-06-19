---
ms.openlocfilehash: be4a3243bc00f29f992957de0dfa29416c13284d
ms.sourcegitcommit: bdf4babd13e021f41fb04cdb3611bb759bd77537
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2021
ms.locfileid: "112392534"
---
# <a name="unity-2020--openxr"></a>[Unity 2020 + OpenXR](#tab/openxr)

### <a name="1-switching-build-platform"></a>1. 切換組建平臺

在 Unity 功能表中，選取 [檔案] > [建置設定] 來開啟 [建置設定] 視窗。

在 [組建設定] 視窗中，選取 [ **PC、Mac & Linux 獨立** 平臺]，然後按一下 [ **切換平臺** ] 按鈕以變更組建平臺：

![切換組建平臺](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-1.PNG)

當 Unity 完成切換平臺時，請按一下 x 圖示以關閉 [組建設定] 視窗。

### <a name="2-set-the-project-settings"></a>2. 設定專案設定

在 Unity 功能表中，選取 [**編輯**  >  **專案設定**  >  **XR 外掛程式管理**]，確定您位於 [Windows 獨立] 索引標籤，然後核取 [ **OpenXR** ] 和 [ **Windows Mixed Reality 功能集**] 核取方塊。

![啟用 OpenXR 和 Windows Mixed Reality 功能集](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-2.PNG)

在 [專案設定] 視窗中，選取 [ **OpenXR** ] 並確認您處於 [Windows 獨立] 索引標籤，並將 **深度提交模式** 從 [無] 變更為 [ **深度16位**]。

在 [互動設定檔] 索引標籤中，按一下 + 符號，以新增 **眼睛的眼睛互動設定檔** 和 **Microsoft 手互動設定檔** 。

![新增眼睛互動設定檔和 Microsoft 手互動設定檔](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-3.PNG)

在 [**開啟 XR 功能群組**  >  **所有功能**] 下 > 核取 [全像 **應用程式遠端處理**] 核取方塊

![啟用全像應用程式遠端處理](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-4.PNG)

接下來，選取 [ **Windows Mixed Reality** ] 核取方塊，然後在 [Windows Mixed Reality 群組] 下，選取 [全像]**應用程式遠端**

![啟用 Windows Mixed Reality 全息版應用程式遠端處理](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-5.PNG)

### <a name="3-build-the-unity-project"></a>3. 建立 Unity 專案

在 Unity 功能表中，選取 [檔案] > [建置設定] 來開啟 [建置設定] 視窗。

在 [組建設定] 視窗中，按一下 [**新增開啟的場景** _] 按鈕，將您目前的場景新增至幕後。 在 [組建] 清單中，按一下 [_ *組建*] 按鈕：

![已新增場景的 Unity [建置設定] 視窗](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-6.PNG)

選擇適當的位置來儲存您的組建，例如 Documents\MixedRealityLearning。 建立新的資料夾，並為其指定適當的名稱，例如 PCHolographicRemoting。 然後按一下 [選取資料夾] 按鈕來啟動建置程序：

![具有 [選取資料夾] 提示視窗的 Unity [建置設定] 視窗](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-7.png)

等候 Unity 完成建置程序。

![Unity 正在進行建置程序](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-8.png)

按兩下可執行檔，以在您的電腦上開啟電腦全像遠端應用程式。

> [!NOTE]
> 由於電腦上建作為 UWP 的電腦應用程式的一些已知問題，我們會將電腦應用程式建立為 Windows 獨立進行 OpenXR。


# <a name="legacy-wsa"></a>[舊版 WSA](#tab/wsa)

### <a name="1-set-the-player-settings"></a>1.設定玩家設定

在 [XR 設定] 區段中，選取 [支援的 WSA 全像攝影遠端處理] 核取方塊，並啟用全像攝影遠端處理。

![已啟用 WSA 全像攝影遠端處理支援的 Unity [XR 設定] 視窗](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step1-1.png)

### <a name="2-build-the-unity-project"></a>2.建置 Unity 專案

在 Unity 功能表中，選取 [檔案] > [建置設定] 來開啟 [建置設定] 視窗。

在 [組建設定] 視窗中，按一下 [**新增開啟的場景** _] 按鈕，將您目前的場景新增至幕後。 在 [組建] 清單中，按一下 [_ *_組建] 按鈕_** 以開啟組建通用 Windows 平臺視窗：

![已新增場景的 Unity [建置設定] 視窗](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step2-1.png)

在 [建置通用 Windows 平台] 視窗中，選擇適當的位置來儲存您的建置，例如 Documents\MixedRealityLearning。 建立新的資料夾，並為其指定適當的名稱，例如 PCHolographicRemoting。 然後按一下 [選取資料夾] 按鈕來啟動建置程序：

![具有 [選取資料夾] 提示視窗的 Unity [建置設定] 視窗](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step2-2.png)

等候 Unity 完成建置程序。

![Unity 正在進行建置程序](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step2-3.png)

### <a name="3-build-and-deploy-the-application"></a>3.組建和部署應用程式

當組建程序完成時，Unity 會提示 Windows 檔案總管開啟您儲存組建的位置。 瀏覽該資料夾，按兩下 .sln 檔案即可在 Visual Studio 中開啟該檔案：

![Windows 檔案總管，其中已選取新建立的 Visual Studio 解決方案](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step3-1.png)

> [!NOTE]
> 如果 Visual Studio 要求您安裝新元件，請花一些時間確認是否已安裝所有必要元件，如同＜安裝工具＞文件中所指定。

藉由選取 x64 架構的發行設定，以及選取本機電腦作為目標，來設定電腦的 Visual Studio：

![為本機電腦設定的 Visual Studio](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step3-2.png)

按一下顯示 [本機電腦] 的按鈕。 其會開始建置應用程式，並將其部署到您的電腦。 應用程式會預設安裝在您的電腦上。
