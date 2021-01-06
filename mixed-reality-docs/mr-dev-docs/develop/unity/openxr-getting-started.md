---
title: 使用 Unity 的 Mixed Reality OpenXR 外掛程式
description: 瞭解如何啟用 Unity 專案的 Mixed Reality OpenXR 外掛程式。
author: hferrone
ms.author: alexturn
ms.date: 12/1/2020
ms.topic: article
keywords: openxr、unity、hololens、hololens 2、mixed reality、MRTK、Mixed Reality 工具組、增強的現實、虛擬實境、混合現實耳機、學習、教學課程、快速入門
ms.openlocfilehash: 7d28dd50e111da4b010bcae699b7451d967e8f35
ms.sourcegitcommit: 653ddcae6d7a1617c89da1153fa8e7b482ef6818
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/06/2021
ms.locfileid: "97905290"
---
# <a name="using-the-mixed-reality-openxr-plugin-for-unity"></a>使用 Unity 的 Mixed Reality OpenXR 外掛程式

從 Unity 2020.2 版開始，可以使用 Unity 封裝管理員 (UPM) 提供 Microsoft 的 Mixed Reality OpenXR 外掛程式套件。

## <a name="prerequisites"></a>先決條件

* Unity 2020.2 或更新版本
* Unity OpenXR 外掛程式0.1.1 或更新版本
* Visual Studio 2019 或更新版本
* 在 Unity 中為 HoloLens 2 應用程式安裝 **UWP** 平臺支援

> [!NOTE]
> 如果您是在 Windows 電腦上建立 VR 應用程式，則不一定需要混合現實 OpenXR 外掛程式。 但是，如果您要自訂適用于 HP 重設系的控制器對應，或建立可在 HoloLens 2 和 VR 耳機上運作的應用程式，則您會想要安裝外掛程式。

## <a name="installing-the-mixed-reality-openxr-plugin"></a>安裝 Mixed Reality OpenXR 外掛程式

您的專案必須先安裝 **OpenXR 外掛程式** 和 **XR 外掛程式管理** 套件，才能使用 Mixed Reality OpenXR 外掛程式。 如果您已經安裝這些專案，很棒！ 如果不是，安裝 Mixed Reality OpenXR 外掛程式會自動將它們安裝為相依性：

1. 在 Unity 編輯器中，流覽至 [ **編輯 > 專案設定] > 封裝管理員**
2. 展開 [限 **域** 登錄] 區段，輸入下列資訊，然後選取 [ **儲存**]：
    * 將 **名稱** 設定為 **Microsoft Mixed Reality**
    * 將 **URL** 設定為 **https://pkgs.dev.azure.com/aipmr/MixedReality-Unity-Packages/_packaging/Unity-packages/npm/registry/**
    * 將 **範圍 (s)** 設定為 **mixedreality**

3. 在 [ **Advanced Settings**] 底下，選取 [**啟用預覽套件**]

![在專案設定中開啟 Unity 封裝管理員視窗的螢幕擷取畫面](images/openxr-img-01.png)

Unity 封裝管理員使用名為 *manifest.js* 的資訊清單檔來決定要安裝的套件，以及可從中安裝的登錄。

> [!IMPORTANT]
> OpenXR 仍是 Unity 中的實驗性，而此程式可能會隨著時間而改變，因為我們會將開發人員體驗優化。

### <a name="registering-the-mixed-reality-dependency"></a>註冊混合現實相依性

一旦將 Microsoft Mixed Reality 範圍登錄新增至資訊清單之後，就可以指定 OpenXR 封裝。

若要新增 OpenXR 套件：

1. 在文字編輯器中開啟 **[projectRoot]/Packages/manifest.js** ，例如 Visual Studio Code
    1. 若要取得這裡，請在 [專案] 視窗的左面板中，以滑鼠右鍵按一下 **套件** 。 然後，按一下 [ **在 Explorer 中顯示**]。
    ![[專案] 視窗中的套件清單螢幕擷取畫面](images/packages.png)
1. 依照下列方式修改 *套件/manifest.js* 的 [相依性] 區段：

    > [!IMPORTANT]
    > 您的資訊清單檔中可能會有更多相依性，而不是此處所示。 請勿刪除其中任何一項，只要將 OpenXR 相依性新增至清單即可。

    ``` json
      "dependencies": {
        "com.microsoft.mixedreality.openxr": "0.1.1",
      }
    ```

1. 儲存檔案、切換回 Unity 編輯器，然後開啟 **封裝管理員** 來確認已安裝外掛程式：

    ![Unity 封裝管理員的螢幕擷取畫面，其中已反白顯示混合現實 OpenXR 外掛程式的 Unity 編輯器中開啟](images/openxr-img-03.png)

    > [!Note]
    > 如果使用 Unity 封裝管理員移除 OpenXR 封裝，您必須使用先前所述的步驟重新新增它。

## <a name="configuring-xr-plugin-management-for-openxr"></a>設定 OpenXR 的 XR 外掛程式管理

若要將 OpenXR 設定為 Unity 中的執行時間：

1. 在 Unity 編輯器中，流覽至 [**編輯 > 專案設定**]
2. 在設定清單中，選取 [ **XR 外掛程式管理**]
3. 檢查 **啟動時初始化 XR** 和 **OpenXR (預覽)** 方塊
4. 如果以 HoloLens 2 為目標，請確定您是在 UWP 平臺上，然後選取 [ **Microsoft HoloLens 功能集**]

![專案設定面板的螢幕擷取畫面，其中已醒目提示 XR 外掛程式管理的 Unity 編輯器中開啟](images/openxr-img-05.png)

> [!IMPORTANT]
> 如果您在 OpenXR 外掛程式旁邊看到紅色警告圖示 **(Preview)**，請按一下圖示並選取 [ **全部修正** ]，然後再繼續。 Unity 編輯器可能需要自行重新開機，變更才會生效。

![OpenXR 專案驗證視窗的螢幕擷取畫面](images/openxr-img-06.png)

您現在已經準備好開始使用 Unity 中的 OpenXR 進行開發！  繼續進行下一節，以瞭解如何使用 OpenXR 範例。

## <a name="optimization"></a>Optimization

如果您是針對 HoloLens 2 進行開發，請流覽至 **Mixed Reality> OpenXR > 套用建議的 HoloLens 2 專案設定** ，以取得更佳的應用程式效能。

![已選取 [OpenXR] 的 [混合現實] 功能表項目開啟的螢幕擷取畫面](images/openxr-img-08.png)

## <a name="try-out-the-unity-sample-scenes"></a>試用 Unity 範例場景

若要利用一或多個範例，請從 **封裝管理員** 安裝 [ARFoundation 4.0 +](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html#installing-ar-foundation) ：

![Unity 封裝管理員在 Unity 編輯器中開啟，並醒目提示 AR Foundation 的螢幕擷取畫面](images/openxr-img-09.png)

### <a name="hololens-2-samples"></a>HoloLens 2 範例

1. 在 Unity 編輯器中，流覽至 [ **Window >] 封裝管理員**
2. 在套件清單中，選取 **Mixed Reality OpenXR 外掛程式**
3. 在 **範例** 清單中找出範例，然後選取 [匯 **入**]

![Unity 封裝管理員在 Unity 編輯器中開啟的螢幕擷取畫面，其中已選取混合的現實 OpenXR 外掛程式，並醒目提示範例匯入按鈕](images/openxr-img-10.png)

<!-- ### For all other OpenXR samples

1. In the Unity Editor, navigate to **Window > Package Manager**
2. In the list of packages, select **OpenXR Plugin**
3. Locate the sample in the **Samples** list and select **Import**

![Screenshot of Unity Package Manager open in Unity editor with OpenXR Plugin selected and samples import button highlighted](images/openxr-img-10.png) -->

> [!NOTE]
> 更新套件時，Unity 會提供選項來更新匯入的範例。  更新匯入的範例將會覆寫對範例和相關資產所做的任何變更。

## <a name="next-steps"></a>後續步驟

現在您已將專案設定為 OpenXR 並可存取範例，請查看我們的 OpenXR 外掛程式目前支援的 [功能](openxr-supported-features.md) 。

## <a name="have-feedback"></a>有任何意見反應嗎？

OpenXR 仍是實驗性的，因此我們會感謝您提供給我們的意見反應，以協助您更妥善地進行。 您可以使用 **Microsoft** OpenXR 標記您的論壇文章，並 [](https://aka.ms/unityforums)  +   **HoloLens 2** 或 **Windows Mixed Reality**，在 Unity 論壇中找到我們。

## <a name="see-also"></a>另請參閱

* [在沒有 MRTK 的情況下設定專案](configure-unity-project.md)
* [Unity 的建議設定](recommended-settings-for-unity.md)
* [對 Unity 的效能建議](performance-recommendations-for-unity.md#how-to-profile-with-unity)
