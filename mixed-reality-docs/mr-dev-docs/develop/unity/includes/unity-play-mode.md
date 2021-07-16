---
ms.openlocfilehash: f7a018d34ee17589ae2e12c2f50f744d736534e2
ms.sourcegitcommit: 7160843723ccd6567490e2f4222219603f184d76
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2021
ms.locfileid: "114339677"
---
# <a name="unity-2020--openxr"></a>[Unity 2020 + OpenXR](#tab/openxr)

1. 在您的 HoloLens 上，移至 **Microsoft Store** ，並安裝全像 **[遠端播放機](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)** 應用程式。
1. 在您的 HoloLens 上，啟動全像 **Remoting 的播放** 程式應用程式。
1. 在 Unity 中，移至 [**編輯**] 功能表，然後選取 [ **Project 設定**]。
1. 選取 **XR 外掛程式管理**。
1. 確定已選取 [ **Windows 獨立**] 索引標籤，並在清單中尋找 **OpenXR** 和 **Windows Mixed Reality 功能集**，然後檢查其核取方塊。
1. 接下來，移至 [ **視窗]** 功能表，展開 [ **XR** ] 子功能表，然後選取 [ **OpenXR 編輯器遠端**]。

    ![醒目提示 XR 外掛程式管理的 Unity 編輯器中開啟之 [專案設定] 面板的螢幕擷取畫面](../images/openxr-features-img-02.png)

1. 按一下 [ **啟用編輯器遠端** 功能]。

    ![在 Unity 編輯器中開啟專案設定面板的螢幕擷取畫面，其中已醒目提示功能](../images/openxr-features-img-03.png)

1. 如果出現 [ **啟用遺失** 相依性] 按鈕，請按一下該按鈕。 按鈕上方的錯誤方塊描述其啟用的功能以及原因。
1. 在 [**遠端主機名**] 中，輸入 HOLOLENS 的 IP 位址。
   1. 視需要變更其他設定。
   1. 在啟動播放模式之後，編輯器會嘗試連接。
1. 選取 [**播放**] 按鈕以啟動播放模式，並在您的 HoloLens 上體驗應用程式。 若要在播放模式中 debug c # 腳本，請[將 Visual Studio 附加至 Unity](/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows)。

> [!NOTE]
> 從0.1.0 版起，全像「全像」遠端執行時間不支援錨點，而 ARAnchorManager 功能將無法透過遠端處理。  這項功能會在未來的版本中推出。

# <a name="unity-20192020--windows-xr-plugin"></a>[Unity 2019/2020 + Windows XR 外掛程式](#tab/winxr)

1. 在您的 HoloLens 上，移至 **Microsoft Store** ，並安裝全像 **[遠端播放機](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)** 應用程式。
1. 在您的 HoloLens 上，啟動全像 **Remoting 的播放** 程式應用程式。
1. 在 Unity 中，移至 [**編輯**] 功能表，然後選取 [ **Project 設定**]。
1. 選取 **XR 外掛程式管理**。
1. 確定已選取 [**電腦、Mac & Linux 獨立**] 索引標籤、在清單中尋找 **Windows Mixed Reality** ，然後選取其核取方塊。
1. 接下來，移至 [**視窗]** 功能表，展開 [ **XR** ] 子功能表，然後選取 [ **Windows XR 外掛程式遠端**]。
1. 將 **模擬模式** 設定為 [ **遠端裝置**]。
1. 針對 [**遠端電腦**]，輸入 HOLOLENS 的 IP 位址。
1. 若要連接，請執行下列其中一項：
   1. 若要手動連線，請取消核取 [**播放] 連線**，然後選取 [**連線**]。 您應該會看到 [連線 **狀態**] 變更為 [**已連接**]，並在 HoloLens 中看到 [畫面] 空白。
   1. 若要自動連線，請 **在 [Play] 上檢查連線**。 在啟動播放模式之後，編輯器會嘗試連接。
1. 選取 [**播放**] 按鈕以啟動播放模式，並在您的 HoloLens 上體驗應用程式。 若要在播放模式中 debug c # 腳本，請[將 Visual Studio 附加至 Unity](/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows)。

# <a name="legacy-wsa"></a>[舊版 WSA](#tab/wsa)

1. 在您的 HoloLens 上，移至 **Microsoft Store** ，並安裝全像 **[遠端播放機](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)** 應用程式。
1. 在您的 HoloLens 上，啟動全像 **Remoting 的播放** 程式應用程式。
1. 在 Unity 中，移至 [ **視窗]** 功能表，展開 [ **XR** ] 子功能表，然後選取在 Unity 2019) 中標示為已淘汰 (的全像 **模擬** 。
1. 將 **模擬模式** 設定為 [ **遠端裝置**]。
1. 根據您使用的是第一代 HoloLens 或 HoloLens 2，設定 **裝置版本**。
1. 針對 [**遠端電腦**]，輸入 HOLOLENS 的 IP 位址。
1. 選取 [連線]。 您應該會看到 [連線 **狀態**] 變更為 [**已連接**]，並在 HoloLens 中看到 [畫面] 空白。
1. 選取 [**播放**] 按鈕以啟動播放模式，並在您的 HoloLens 上體驗應用程式。 若要在播放模式中 debug c # 腳本，請[將 Visual Studio 附加至 Unity](/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows)。
