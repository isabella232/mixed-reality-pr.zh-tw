---
title: 使用 Windows XR 外掛程式
description: 瞭解如何使用 Windows XR 支援，在不使用 MRTK 的情況下設定 Unity 專案。
author: hferrone
ms.author: alexturn
ms.date: 03/26/2021
ms.topic: article
keywords: Unity，混合的現實，開發，使用者入門，新專案，Windows Mixed Reality，UWP，XR，效能，舊版，mrtk，Windows
ms.openlocfilehash: 24da4b5116b926cfd5eda12db6eedee2f9e85621
ms.sourcegitcommit: 6272d086a2856e8b514a719e1f9e3b78554be5be
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/30/2021
ms.locfileid: "105938105"
---
# <a name="using-windows-xr-plugin"></a>使用 Windows XR 外掛程式

針對以 Unity 2020 為目標的開發人員，Windows XR 外掛程式可讓您存取 HoloLens 2 和 Windows Mixed Reality 耳機上的混合現實功能。  Unity 2019 也支援此外掛程式，不過在該版本上使用此外掛程式時，Azure 空間錨點有一些已知的不相容性。

雖然 Microsoft 和社區建立了開放原始碼工具，例如 [混合現實工具組 (MRTK) ](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html) ，而這些工具會自動設定 WMR 的環境，但許多開發人員想要從頭開始建立他們的體驗。  當您使用 MRTK 時，下列檔將示範如何針對混合現實開發正確設定專案。  您需要變更的設定分為兩類：每個專案設定和個別場景設定。

## <a name="setting-up-your-project-with-mrtk"></a>使用 MRTK 設定您的專案

適用于 Unity 的 MRTK 會提供跨平臺輸入系統、基礎元件，以及空間互動的常見組建區塊。 MRTK 第 2 版主要用於加速開發適用於 Microsoft HoloLens、Windows Mixed Reality 沈浸式 (VR) 頭戴裝置和 OpenVR 平台的應用程式。 此專案的目標是減少進入障礙、建立混合實境應用程式，以及回饋伴著我們成長的社群。

> [!div class="nextstepaction"]
> [試用我們的 MRTK 教學課程](tutorials/mr-learning-base-01.md)

如需詳細的功能詳細資料，請參閱 [MRTK 的檔](/windows/mixed-reality/mrtk-unity) 。

## <a name="manual-setup-without-mrtk"></a>手動設定而不 MRTK

如果您的目標是 Desktop VR，建議您在新的 Unity 專案上使用預設選取的電腦獨立平臺：

![在 unity 編輯器中開啟 [組建設定] 視窗的螢幕擷取畫面，其中已醒目提示 [電腦]、[Mac & 獨立平臺](images/wmr-config-img-3.png)

如果您的目標是 HoloLens 2，則必須切換至通用 Windows 平臺：

1.  選取 [檔案 **> 組建設定 ...** ]
2.  選取 [平臺] 清單中的 [**通用 Windows 平臺**]，然後選取 [**切換平臺**]
3.  將 **架構** 設定為 **ARM 64**
4.  將 **目標裝置** 設定為 **HoloLens**
5.  將 **組建類型** 設定為 **D3D**
6.  將 **UWP SDK** 設定為 **最新安裝**
7.  將 **組建** 設定設為 **發行** ，因為 Debug 有已知的效能問題

![在 unity 編輯器中開啟 [組建設定] 視窗的螢幕擷取畫面，其中已醒目提示通用 Windows 平臺](images/wmr-config-img-4.png)

設定您的平臺之後，您需要讓 Unity 知道在匯出時建立一個 [沉浸式視圖](../../design/app-views.md) ，而不是2d 視圖：

1. 在 Unity 編輯器中，流覽至 [**編輯 > 專案設定**]，然後選取 [ **XR 外掛程式管理**]

2. 選取 [**安裝 XR 外掛程式管理**]

![醒目提示 XR 外掛程式管理的 unity 編輯器中開啟之 [專案設定] 視窗的螢幕擷取畫面](images/wmr-config-img-5.png)

3. 選取 [ **啟動時初始化 XR** ] 和 **Windows Mixed Reality**

![醒目提示 XR 外掛程式管理的 unity 編輯器中開啟之 [專案設定] 視窗的螢幕擷取畫面](images/wmr-config-img-7.png)

4. 展開 [ **XR 外掛程式管理** ] 區段，然後選取 [ **通用 Windows 平臺設定** ] 索引標籤
5. 如果您使用 Unity 2020 或更新版本，您會看到檢查 **OpenXR** 或 **Windows Mixed Reality** 的選項。 
    * 您可以選擇任一執行時間。  如果您要特別針對 HoloLens 2 或 HP 回條 G2 進行開發，並決定嘗試 **OpenXR**，請選取 [OpenXR] 方塊，並查看我們的指南，以 [使用 Unity 的 Mixed Reality OpenXR 外掛程式](openxr-getting-started.md) ，以在返回本教學課程之前，為這些裝置正確設定

> [!NOTE]
> 從 Unity 2020 LTS 開始，Microsoft 正採用 OpenXR 進行開發。  當我們遷移至此路徑時，在 Unity 2021.1 中，Windows XR 外掛程式將會被取代，並在2021.2 中移除，讓 OpenXR 唯一支援的路徑。 您可以在中找到更多有關 [使用 Mixed Reality OpenXR 外掛程式](openxr-getting-started.md)的資訊。

6. 如果您決定選擇 **Windows Mixed Reality** 外掛程式，請檢查所有方塊，並將 **深度提交模式** 設定為 **深度16位**

![在 unity 編輯器中開啟的 [專案設定] 視窗的螢幕擷取畫面，其中已醒目提示 Windows Mixed Reality 區段](images/wmr-config-img-8.png)
