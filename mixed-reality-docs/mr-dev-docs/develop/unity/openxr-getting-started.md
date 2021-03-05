---
title: 使用 Unity 的 Mixed Reality OpenXR 外掛程式
description: 瞭解如何啟用 Unity 專案的 Mixed Reality OpenXR 外掛程式。
author: hferrone
ms.author: alexturn
ms.date: 01/11/2021
ms.topic: article
keywords: openxr、unity、hololens、hololens 2、mixed reality、MRTK、Mixed Reality 工具組、增強的現實、虛擬實境、混合現實耳機、學習、教學課程、快速入門
ms.openlocfilehash: 9b95a0978522fb9fefaca3c4b96189131b88d0ec
ms.sourcegitcommit: 4647712788a91a2b26d4b01e62285c2942bb0bd2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102230845"
---
# <a name="using-the-mixed-reality-openxr-plugin-for-unity"></a>使用 Unity 的 Mixed Reality OpenXR 外掛程式

從 Unity 2020.2 版開始，可以使用 Unity 套件管理員 (UPM) 來使用 Microsoft 的 Mixed Reality OpenXR 外掛程式套件。

## <a name="prerequisites"></a>必要條件

* Unity 2020.2 或更新版本
* Unity OpenXR 外掛程式0.1.4 或更新版本
* Visual Studio 2019 或更新版本
* 在適用于 HoloLens 2 應用程式的 Unity 中安裝 **UWP** 平臺支援

> [!NOTE]
> 如果您是在 Windows 電腦上建立 VR 應用程式，則不一定需要混合現實 OpenXR 外掛程式。 但是，如果您要自訂適用于 HP-UX 的控制器對應，或建立可在 HoloLens 2 和 VR 耳機上運作的應用程式，則您會想要安裝外掛程式。

## <a name="installing-openxr-with-the-mixed-reality-feature-tool"></a>使用混合現實功能工具安裝 OpenXR

使用新的混合現實功能工具應用程式來安裝 OpenXR 外掛程式。 遵循 [安裝和使用](welcome-to-mr-feature-tool.md) 方式的指示，然後在混合現實工具組類別中選取 **Mixed reality OpenXR 外掛程式** 套件：

![醒目提示 open xr 外掛程式的混合現實功能工具套件視窗](images/feature-tool-openxr.png)

## <a name="configuring-xr-plugin-management-for-openxr"></a>設定 OpenXR 的 XR 外掛程式管理

若要將 OpenXR 設定為 Unity 中的執行時間：

1. 在 Unity 編輯器中，流覽至 [**編輯 > 專案設定**]
2. 在設定清單中，選取 [ **XR 外掛程式管理**]
3. 檢查 **啟動時初始化 XR** 和 **OpenXR (預覽)** 方塊
4. 如果以 HoloLens 2 為目標，請確定您是在 UWP 平臺上，然後選取 [ **Microsoft HoloLens 功能組**]。

![專案設定面板的螢幕擷取畫面，其中已醒目提示 XR 外掛程式管理的 Unity 編輯器中開啟](images/openxr-img-05.png)

> [!IMPORTANT]
> 如果您在 OpenXR 外掛程式旁邊看到紅色警告圖示 **(Preview)**，請按一下圖示並選取 [ **全部修正** ]，然後再繼續。 Unity 編輯器可能需要自行重新開機，變更才會生效。

![OpenXR 專案驗證視窗的螢幕擷取畫面](images/openxr-img-06.png)

您現在已經準備好開始使用 Unity 中的 OpenXR 進行開發！  繼續進行下一節，以瞭解如何使用 OpenXR 範例。

## <a name="optimization"></a>Optimization

如果您是針對 HoloLens 2 進行開發，請流覽至 **Mixed Reality> OpenXR > 套用適用于 hololens 2 的建議專案設定** ，以取得更佳的應用程式效能。

![已選取 [OpenXR] 的 [混合現實] 功能表項目開啟的螢幕擷取畫面](images/openxr-img-08.png)

## <a name="try-out-the-unity-sample-scenes"></a>試用 Unity 範例場景

若要利用一或多個範例，請從 **套件管理員** 安裝 [ARFoundation 4.0 +](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html#installing-ar-foundation) ：

![Unity 編輯器中開啟的 Unity 套件管理員的螢幕擷取畫面，其中已醒目提示 AR Foundation](images/openxr-img-09.png)

### <a name="hololens-2-samples"></a>HoloLens 2 範例

1. 在 Unity 編輯器中，流覽至 **Window > 套件管理員**
2. 在套件清單中，選取 **Mixed Reality OpenXR 外掛程式**
3. 在 **範例** 清單中找出範例，然後選取 [匯 **入**]

![Unity 編輯器中開啟的 Unity 套件管理員的螢幕擷取畫面，其中已選取混合現實 OpenXR 外掛程式，並醒目提示範例匯入按鈕](images/openxr-img-03.png)

<!-- ### For all other OpenXR samples

1. In the Unity Editor, navigate to **Window > Package Manager**
2. In the list of packages, select **OpenXR Plugin**
3. Locate the sample in the **Samples** list and select **Import**

![Screenshot of Unity Package Manager open in Unity editor with OpenXR Plugin selected and samples import button highlighted](images/openxr-img-10.png) -->

> [!NOTE]
> 更新套件時，Unity 會提供選項來更新匯入的範例。  更新匯入的範例將會覆寫對範例和相關資產所做的任何變更。

## <a name="using-mrtk-with-openxr-support"></a>搭配使用 MRTK 與 OpenXR 支援

MRTK-Unity 支援從2.5.3 版本開始的 Mixed Reality OpenXR 外掛程式。

1. 如果您還沒有這麼做，請再次開啟 [Mixed Reality 功能工具](welcome-to-mr-feature-tool.md) 以安裝混合現實工具組。 **基礎** 套件中的 OpenXR 支援。
2. 移至偵測器中的 MixedReality 工具組元件腳本，並切換至 **DefaultOpenXRConfigurationProfile** 設定檔：

    ![在偵測器的混合現實工具組元件中切換 MRTK 設定的螢幕擷取畫面](images/openxr-img-11.png)

    1. 如需有關 [遷移至 OpenXR 的深入資訊](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk#configuring-mrtk-for-the-xr-sdk-pipeline)，請參閱 MRTK 檔。

> [!NOTE]
> 從舊版 MRTK 進行升級時，請確定 **資產/MixedRealityToolkit. 產生/link.xml** 檔案中有下列這一行：
>
> ```xml
> <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>
> ```
>
> 如果您開始使用 MRTK 2.5.4 或更新版本，則預設會新增這一行。

## <a name="next-steps"></a>下一步

現在您已將專案設定為 OpenXR 並可存取範例，請查看我們的 OpenXR 外掛程式目前支援的 [功能](openxr-supported-features.md) 。

## <a name="have-feedback"></a>有任何意見反應嗎？

OpenXR 仍是實驗性的，因此我們會感謝您提供給我們的意見反應，以協助您更妥善地進行。 您可以透過 **Microsoft** [](https://aka.ms/unityforums)  +  **OpenXR** 和 **HoloLens 2** 或 **Windows Mixed Reality** 來標記您的論壇貼文，以在 Unity 論壇中找到我們。

## <a name="see-also"></a>另請參閱

* [在沒有 MRTK 的情況下設定專案](configure-unity-project.md)
* [Unity 的建議設定](recommended-settings-for-unity.md)
* [對 Unity 的效能建議](performance-recommendations-for-unity.md#how-to-profile-with-unity)
