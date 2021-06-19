---
ms.openlocfilehash: 2af7fd36e29ed9aca2c7f743a40dc7b9dad17f09
ms.sourcegitcommit: 6ade7e8ebab7003fc24f9e0b5fa81d091369622c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2021
ms.locfileid: "112394582"
---
# <a name="openxr"></a>[OpenXR](#tab/openxr)

使用新的混合現實功能工具應用程式來安裝 OpenXR 外掛程式。 遵循 [安裝和使用](../../welcome-to-mr-feature-tool.md) 方式的指示，然後在混合現實工具組類別中選取 **Mixed reality OpenXR 外掛程式** 套件：

![醒目提示 open xr 外掛程式的混合現實功能工具套件視窗](../../images/feature-tool-openxr.png)

### <a name="setting-your-build-target"></a>設定您的組建目標

如果您的目標是 Desktop VR，建議您在新的 Unity 專案上使用預設選取的電腦獨立平臺：

![在 unity 編輯器中開啟 [組建設定] 視窗的螢幕擷取畫面，其中已醒目提示 [電腦]、[Mac & 獨立平臺](../../images/wmr-config-img-3.png)

如果您的目標是 HoloLens 2，則必須切換至通用 Windows 平臺：

1. 選取 [檔案 **> 組建設定 ...** ]
2. 選取 [平臺] 清單中的 [**通用 Windows 平臺**]，然後選取 [**切換平臺**]
3. 將 **架構** 設定為 **ARM 64**
4. 將 **目標裝置** 設定為 **HoloLens**
5. 將 **組建類型** 設定為 **D3D**
6. 將 **UWP SDK** 設定為 **最新安裝**

![在 unity 編輯器中開啟 [組建設定] 視窗的螢幕擷取畫面，其中已醒目提示通用 Windows 平臺](../../images/wmr-config-img-4.png)

### <a name="configuring-xr-plugin-management-for-openxr"></a>設定 OpenXR 的 XR 外掛程式管理

若要將 OpenXR 設定為 Unity 中的執行時間：

1. 在 Unity 編輯器中，流覽至 [**編輯 > 專案設定**]
2. 在設定清單中，選取 [ **XR 外掛程式管理**]
3. 檢查 Startup 和 **OpenXR** 方塊的 **Initialize XR**
4. 如果以 HoloLens 2 為目標，請確定您是在 UWP 平臺上，然後選取 [ **Microsoft HoloLens 功能集**]

![專案設定面板的螢幕擷取畫面，其中已醒目提示 XR 外掛程式管理的 Unity 編輯器中開啟](../../images/openxr-img-05.png)

### <a name="optimization"></a>Optimization

如果您是針對 HoloLens 2 進行開發，請流覽至 **Mixed Reality> OpenXR > 套用建議的 HoloLens 2 專案設定** ，以取得更佳的應用程式效能。

![已選取 [OpenXR] 的 [混合現實] 功能表項目開啟的螢幕擷取畫面](../../images/openxr-img-08.png)

> [!IMPORTANT]
> 如果您在 **OpenXR 外掛程式** 旁邊看到黃色警告圖示，請按一下圖示並選取 [ **全部修正** ]，然後再繼續。 Unity 編輯器可能需要自行重新開機，變更才會生效。

![OpenXR 專案驗證視窗的螢幕擷取畫面](../../images/openxr-img-06.png)

您現在已經準備好開始使用 Unity 中的 OpenXR 進行開發！  繼續進行下一節，以瞭解如何使用 OpenXR 範例。

### <a name="unity-sample-projects-for-openxr-and-hololens-2"></a>適用于 OpenXR 和 HoloLens 2 的 Unity 範例專案

查看範例 unity 專案的 [OpenXR Mixed Reality 範例](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples) 存放庫展示如何使用 Mixed reality OpenXR 外掛程式建立 HoloLens 2 或混合現實耳機的 unity 應用程式。

# <a name="windows-xr"></a>[Windows XR](#tab/windowsxr)

如果您的目標是 Desktop VR，建議您在新的 Unity 專案上使用預設選取的電腦獨立平臺：

![在 unity 編輯器中開啟 [組建設定] 視窗的螢幕擷取畫面，其中已醒目提示 [電腦]、[Mac & 獨立平臺](../../images/wmr-config-img-3.png)

如果您的目標是 HoloLens 2，則必須切換至通用 Windows 平臺：

1.  選取 [檔案 **> 組建設定 ...** ]
2.  選取 [平臺] 清單中的 [**通用 Windows 平臺**]，然後選取 [**切換平臺**]
3.  將 **架構** 設定為 **ARM 64**
4.  將 **目標裝置** 設定為 **HoloLens**
5.  將 **組建類型** 設定為 **D3D**
6.  將 **UWP SDK** 設定為 **最新安裝**
7.  將 **組建** 設定設為 **發行** ，因為 Debug 有已知的效能問題

![在 unity 編輯器中開啟 [組建設定] 視窗的螢幕擷取畫面，其中已醒目提示通用 Windows 平臺](../../images/wmr-config-img-4.png)

設定您的平臺之後，您需要讓 Unity 知道在匯出時建立一個 [沉浸式視圖](../../../../design/app-views.md) ，而不是2d 視圖：

1. 在 Unity 編輯器中，流覽至 [**編輯 > 專案設定**]，然後選取 [ **XR 外掛程式管理**]

2. 選取 [**安裝 XR 外掛程式管理**]

![醒目提示 XR 外掛程式管理的 unity 編輯器中開啟之 [專案設定] 視窗的螢幕擷取畫面](../../images/wmr-config-img-5.png)

3. 選取 [ **啟動時初始化 XR** ] 和 **Windows Mixed Reality**

![醒目提示 XR 外掛程式管理的 unity 編輯器中開啟之 [專案設定] 視窗的螢幕擷取畫面](../../images/wmr-config-img-7.png)

4. 展開 [ **XR 外掛程式管理** ] 區段，然後選取 [ **通用 Windows 平臺設定** ] 索引標籤
5. 如果您使用 Unity 2020 或更新版本，您會看到檢查 **OpenXR** 或 **Windows Mixed Reality** 的選項。 
    * 您可以選擇任一執行時間。  如果您要特別針對 HoloLens 2 或 HP 回條 G2 進行開發，並決定嘗試 **OpenXR**，請選取 [OpenXR] 方塊，並查看我們的指南，以 [使用 Unity 的 Mixed Reality OpenXR 外掛程式](../../openxr-getting-started.md) ，以在返回本教學課程之前，為這些裝置正確設定

> [!NOTE]
> 從 Unity 2020 LTS 開始，Microsoft 正採用 OpenXR 進行開發。  當我們遷移至此路徑時，在 Unity 2021.1 中，Windows XR 外掛程式將會被取代，並在2021.2 中移除，讓 OpenXR 唯一支援的路徑。 您可以在中找到更多有關 [使用 Mixed Reality OpenXR 外掛程式](../../openxr-getting-started.md)的資訊。

6. 如果您決定選擇 **Windows Mixed Reality** 外掛程式，請檢查所有方塊，並將 **深度提交模式** 設定為 **深度16位**

![在 unity 編輯器中開啟的 [專案設定] 視窗的螢幕擷取畫面，其中已醒目提示 Windows Mixed Reality 區段](../../images/wmr-config-img-8.png)

# <a name="legacy-xr"></a>[傳統 XR](#tab/legacy)

如果您的目標是 Desktop VR，建議您在新的 Unity 專案上使用預設選取的電腦獨立平臺：

![在 unity 編輯器中開啟 [組建設定] 視窗的螢幕擷取畫面，其中已醒目提示 [電腦]、[Mac & 獨立平臺](../../images/wmr-config-img-3.png)

如果您的目標是 HoloLens 2，則必須切換至通用 Windows 平臺：

1.  選取 [檔案 **> 組建設定 ...** ]
2.  選取 [平臺] 清單中的 [**通用 Windows 平臺**]，然後選取 [**切換平臺**]
3.  將 **架構** 設定為 **ARM 64**
4.  將 **目標裝置** 設定為 **HoloLens**
5.  將 **組建類型** 設定為 **D3D**
6.  將 **UWP SDK** 設定為 **最新安裝**
7.  將 **組建** 設定設為 **發行** ，因為 Debug 有已知的效能問題

![在 unity 編輯器中開啟 [組建設定] 視窗的螢幕擷取畫面，其中已醒目提示通用 Windows 平臺](../../images/wmr-config-img-4.png)

設定您的平臺之後，您需要讓 Unity 知道在匯出時建立一個 [沉浸式視圖](../../../../design/app-views.md) ，而不是2d 視圖。

> [!CAUTION]
> Unity 2019 中的舊版 XR 已被取代，並已在 Unity 2020 中移除。

1. 從組建設定開啟 **播放機設定** ... **視窗** 並展開 [ **XR 設定** ] 群組
2. 在 [ **XR 設定** ] 區段中，選取 [ **支援的虛擬實境** 新增虛擬實境裝置] 清單
3. 將 **深度格式** 設定為 **16 位深度** ，並啟用 **深度緩衝區共用**
4. 將 **身歷聲轉譯模式** 設定為 **單一傳遞實例**
5. 如果您想要使用全像攝影的遠端處理，請選取 [不 **支援的 WSA** 全像 

![醒目提示 [播放程式設定] 區段的 [在 unity 編輯器中開啟專案設定] 視窗的螢幕擷取畫面](../../images/wmr-config-img-9.png)