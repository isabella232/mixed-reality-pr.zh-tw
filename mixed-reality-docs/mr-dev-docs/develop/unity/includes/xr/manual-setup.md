---
ms.openlocfilehash: c5276943bab0ddc961342f879c0cf4f8986aa7b4f67b16c9c8b5415ca6fc58fd
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2021
ms.locfileid: "115202714"
---
# <a name="openxr"></a>[OpenXR](#tab/openxr)

使用新的混合現實功能工具應用程式來安裝 OpenXR 外掛程式。 遵循 [安裝和使用方式指示](../../welcome-to-mr-feature-tool.md)，並在 **平臺支援** 類別中選取 **Mixed Reality OpenXR 外掛程式** 套件：

![醒目提示 open xr 外掛程式的混合現實功能工具套件視窗](../../images/feature-tool-openxr.png)

### <a name="setting-your-build-target"></a>設定您的組建目標

如果您的目標是 Desktop VR，建議您在新的 Unity 專案上使用預設選取的電腦獨立平臺：

![在 unity 編輯器中開啟的 [組建設定] 視窗螢幕擷取畫面，其中已醒目提示 [電腦]、[Mac & 獨立平臺](../../images/wmr-config-img-3.png)

如果您的目標是 HoloLens 2，則必須切換至通用 Windows 平臺：

1. 選取檔案 **> 組建設定**.。。
2. 選取 [平臺] 清單中的 [**通用 Windows 平臺**]，然後選取 [**切換平臺**]
3. 將 [架構] 設定為 [ARM64]
4. 將 **目標裝置** 設定為 **HoloLens**
5. 將 [組建類型] 設定為 [D3D 專案]
6. 將 **目標 SDK 版本** 設為 **最新安裝**

![在 unity 編輯器中開啟組建設定視窗的螢幕擷取畫面，其中已醒目提示通用 Windows 平臺](../../images/wmr-config-img-4.png)

### <a name="configuring-xr-plugin-management-for-openxr"></a>設定 OpenXR 的 XR 外掛程式管理

若要將 OpenXR 設定為 Unity 中的執行時間：

1. 在 Unity 編輯器中，流覽至 [**編輯] > Project 設定**
2. 在設定清單中，如果您已使用 MRFT 安裝 Mixed Reality OpenXR 外掛程式，請選取 [ **XR 外掛程式管理**] (的安裝) 
3. 勾選 [ **啟動時初始化 XR** ] 方塊
4. 如果以 Desktop VR 為目標，請停留在 [電腦獨立] 索引標籤 (監視器) 並檢查 **OpenXR** 和 **Windows Mixed Reality 功能集** 方塊
5. 如果以 HoloLens 2 為目標，請切換至 [通用 Windows 平臺] 索引標籤 (Windows 標誌) 然後選取 [ **OpenXR** ] 和 [ **Microsoft HoloLens 功能集**] 方塊。

![專案設定面板的螢幕擷取畫面，其中已醒目提示 XR 外掛程式管理的 Unity 編輯器中開啟](../../images/openxr-img-05.png)

> [!IMPORTANT]
> 如果您在 **OpenXR 外掛程式** 旁邊看到黃色警告圖示，請按一下圖示並選取 [ **全部修正** ]，然後再繼續。 Unity 編輯器可能需要自行重新開機，變更才會生效。

![OpenXR 專案驗證視窗的螢幕擷取畫面](../../images/openxr-img-06.png)

### <a name="optimization"></a>Optimization

如果您是針對 HoloLens 2 進行開發，請選取 [**混合現實] > Project > 套用 HoloLens 2 功能表項目的建議專案設定**，以取得更佳的應用程式效能。

![已選取 [OpenXR] 的 [混合現實] 功能表項目開啟的螢幕擷取畫面](../../images/openxr-img-08.png)

您現在已經準備好開始使用 Unity 中的 OpenXR 進行開發！  繼續進行下一節，以瞭解如何使用 OpenXR 範例。

### <a name="unity-sample-projects-for-openxr-and-hololens-2"></a>適用于 OpenXR 和 HoloLens 2 的 Unity 範例專案

查看範例 unity 專案的[OpenXR Mixed Reality 範例](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples)存放庫展示如何使用 mixed reality OpenXR 外掛程式建立 HoloLens 2 或混合現實耳機的 unity 應用程式。

或者，如果您已準備好從空白專案開始使用，請繼續進行 [攝影機安裝](../../camera-in-unity.md) 文章。

# <a name="windows-xr"></a>[WindowsXR](#tab/windowsxr)

> [!CAUTION]
> unity 2021.1 中的 Windows XR 外掛程式已淘汰，將會在 unity 2021.2 中移除。  針對 Unity 2020 開發，Microsoft 建議改用 OpenXR 外掛程式。

如果您的目標是 Desktop VR，建議您在新的 Unity 專案上使用預設選取的電腦獨立平臺：

![在 unity 編輯器中開啟的 [組建設定] 視窗螢幕擷取畫面，其中已醒目提示 [電腦]、[Mac & 獨立平臺](../../images/wmr-config-img-3.png)

如果您的目標是 HoloLens 2，則必須切換至通用 Windows 平臺：

1.  選取檔案 **> 組建設定**.。。
2.  選取 [平臺] 清單中的 [**通用 Windows 平臺**]，然後選取 [**切換平臺**]
3.  將 [架構] 設定為 [ARM64]
4.  將 **目標裝置** 設定為 **HoloLens**
5.  將 [組建類型] 設定為 [D3D 專案]
6.  將 **目標 SDK 版本** 設為 **最新安裝**
7.  將 **組建** 設定設為 **發行** ，因為 Debug 有已知的效能問題

![在 unity 編輯器中開啟組建設定視窗的螢幕擷取畫面，其中已醒目提示通用 Windows 平臺](../../images/wmr-config-img-4.png)

設定您的平臺之後，您需要讓 Unity 知道在匯出時建立一個 [沉浸式視圖](../../../../design/app-views.md) ，而不是2d 視圖：

1. 在 Unity 編輯器中，流覽至 [**編輯] > Project 設定**]，然後選取 [ **XR 外掛程式管理**]

2. 如果出現 **XR 外掛程式管理** ，請選取 [安裝]

![醒目提示 XR 外掛程式管理的 unity 編輯器中開啟 Project 設定視窗的螢幕擷取畫面](../../images/wmr-config-img-5.png)

3. 選取 [**啟動時初始化 XR** ] 和 **Windows Mixed Reality**

![醒目提示 XR 外掛程式管理的 unity 編輯器中開啟 Project 設定視窗的螢幕擷取畫面](../../images/wmr-config-img-7.png)

4. 選取 [ **XR 外掛程式管理**  >  **Windows Mixed Reality** ] 區段，檢查所有方塊，並將 **深度緩衝區格式** 設定為 **深度緩衝區16位**

![在 unity 編輯器中開啟 Project 設定視窗的螢幕擷取畫面，其中已醒目提示 Windows Mixed Reality 區段](../../images/wmr-config-img-8.png)

# <a name="legacy-xr"></a>[傳統 XR](#tab/legacy)

> [!CAUTION]
> Unity 2019 中的舊版 XR 已被取代，並已在 Unity 2020 中移除。

如果您的目標是 Desktop VR，建議您在新的 Unity 專案上使用預設選取的電腦獨立平臺：

![在 unity 編輯器中開啟的 [組建設定] 視窗螢幕擷取畫面，其中已醒目提示 [電腦]、[Mac & 獨立平臺](../../images/wmr-config-img-3.png)

如果您的目標是 HoloLens 2，則必須切換至通用 Windows 平臺：

1.  選取檔案 **> 組建設定**.。。
2.  選取 [平臺] 清單中的 [**通用 Windows 平臺**]，然後選取 [**切換平臺**]
3.  將 [架構] 設定為 [ARM64]
4.  將 **目標裝置** 設定為 **HoloLens**
5.  將 [組建類型] 設定為 [D3D 專案]
6.  將 **目標 SDK 版本** 設為 **最新安裝**
7.  將 **組建** 設定設為 **發行** ，因為 Debug 有已知的效能問題

![在 unity 編輯器中開啟組建設定視窗的螢幕擷取畫面，其中已醒目提示通用 Windows 平臺](../../images/wmr-config-img-4.png)

設定您的平臺之後，您需要讓 Unity 知道在匯出時建立一個 [沉浸式視圖](../../../../design/app-views.md) ，而不是2d 視圖。

1. 從組建設定開啟 **Player 設定**... **視窗** 並展開 **XR 設定** 群組
2. 在 [ **XR 設定**] 區段中，選取 [**支援的虛擬實境**] 以新增虛擬實境裝置清單
3. 將 **深度格式** 設定為 **16 位深度**，並勾選 [**啟用深度緩衝區共用**]
4. 將 [立體聲轉譯模式] 設定為 [單程執行個體]
5. 如果您想要使用全像攝影模式的遠端處理功能，請選取 [不 **支援的 WSA** 全像

![醒目提示 [播放程式設定] 區段的 unity 編輯器中開啟 Project 設定視窗的螢幕擷取畫面](../../images/wmr-config-img-9.png)
