---
title: 在專案中新增空間音訊
description: 將 Microsoft 空間定位器外掛程式新增至您的 Unity 專案，以存取 HoloLens 2 HRTF 硬體卸載。
author: kegodin
ms.author: v-hferrone
ms.date: 12/01/2019
ms.topic: article
keywords: 混合的現實、unity、教學課程、hololens2、空間音訊、MRTK、混合現實工具組、UWP、Windows 10、HRTF、前端相關的傳送功能、回音、Microsoft 空間定位器
ms.openlocfilehash: 80bf19e8a091bd241e28afff0a42c13ca72e1d45
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2021
ms.locfileid: "98007468"
---
# <a name="adding-spatial-audio-to-your-unity-project"></a>將空間音訊新增至 Unity 專案

歡迎使用 HoloLens2 上適用于 Unity 的空間音訊教學課程。 此教學課程順序顯示：
* 如何在 Unity 的 HoloLens 2 上使用 head 相關的傳送函式 (HRTF) 卸載
* 如何在使用 HRTF 卸載時啟用回音

[Microsoft 空間定位器 GitHub 存放庫](https://github.com/microsoft/spatialaudio-unity)已完成此教學課程順序的 Unity 專案。 

若要瞭解使用以 HRTF 為基礎的 spatialization 技術來 spatialize 音效的意義，以及如何使用它有説明的建議，請參閱 [空間音效設計](https://docs.microsoft.com/windows/mixed-reality/spatial-sound-design)。

## <a name="what-is-hrtf-offload"></a>什麼是 HRTF 卸載？

使用以 HRTF 為基礎的演算法處理音訊需要大量的特製化計算。 HoloLens 2 包含專用硬體，可用來避免應用程式處理器額外負荷，進而「卸載」以 HRTF 為基礎的演算法處理。  Microsoft 空間定位器外掛程式提供簡單的方法，讓您的應用程式利用專用的 HRTF 硬體，讓您的應用程式可以使用更多應用程式處理器來執行空間音訊以外的作業。

## <a name="objectives"></a>目標

在第一章中，您將會：
* 建立 Unity 專案並匯入 MRTK
* 匯入 Microsoft 空間定位器外掛程式
* 啟用 Microsoft 空間定位器外掛程式
* 在開發人員工作站上啟用空間音訊

## <a name="create-a-project-and-add-nuget-for-unity"></a>建立專案並新增 Unity 的 NuGet

從空白的 Unity 專案開始，然後新增並設定適用于 Unity 的 NuGet：
1. 下載最新的 [NuGetForUnity。 unitypackage](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest)
2. 在 Unity 功能表列中，按一下 [ **資產]-> 匯入封裝-> 自訂套件 ...** ]，然後安裝 NuGetForUnity 套件：

![匯入自訂套件](images/spatial-audio/import-custom-package.png)

## <a name="add-the-windows-mixed-reality-package"></a>新增 Windows Mixed Reality 套件

Unity 2019 和更新版本中的 Windows Mixed Reality 支援包含在選用套件中。 若要將它新增至您的專案，請從 Unity 功能表列開啟 **視窗 > 封裝管理員** ：

![封裝管理員功能表](images/spatial-audio/package-manager-menu.png)

然後尋找並安裝 **Windows Mixed Reality** 套件：

![套件管理員視窗](images/spatial-audio/package-manager-window.png)

## <a name="install-mrtk-and-microsoft-spatializer"></a>安裝 MRTK 和 Microsoft 空間定位器

使用適用于 Unity 的 NuGet，安裝 MRTK 和 Microsoft 空間定位器外掛程式：
1. 在 Unity 功能表列中，按一下 [ **nuget-> 管理 Nuget 套件**]。

![管理 NuGet 套件](images/spatial-audio/manage-nuget-packages.png)

2. 在 **搜尋** 方塊中，輸入 "MixedReality"，並安裝 MRTK core 套件： **MixedReality。**

![MRTK NuGet 套件](images/spatial-audio/mrtk-nuget-package.png)

[MRTK NuGet 套件](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MRTKNuGetPackage.html) 具有其他內容和詳細資料。

4. 在 **搜尋** 方塊中，輸入 "SpatialAudio"，並安裝 microsoft 空間定位器 Package： **SpatialAudio. 空間定位器 Unity**

![空間定位器外掛程式 NuGet](images/spatial-audio/spatializer-plugin-nuget.png)

## <a name="set-up-mrtk-in-your-project"></a>在您的專案中設定 MRTK

1. 前往 [檔案 **-> 組建設定**]，開啟 [組建設定] 視窗。

2. 選取 _通用 Windows 平臺_ 然後按一下 [ **切換平臺**]。

3. 按一下 [**組建] 視窗** 中的 [**播放機設定**]，在 [偵測 **器**] 窗格中開啟 **player 設定** 屬性。
    * 在 [ **XR 設定**] 下，勾選 [ **支援虛擬實境** ] 核取方塊
    * 在 [ **XR 設定**] 下，將 [ **身歷聲轉譯模式]** 變更為 [ **單一傳遞實例**]。
    * 在 [**發行設定**] 下的 [**功能**] 區段中，選取 [**空間感知**] 核取方塊

4. 在功能表列上，按一下 [**混合現實工具組-> 加入場景並設定**]。 將 MRTK 新增至您的場景。

如需其他指引，包括如何建立您的應用程式並部署至 HoloLens 2，請參閱 [MR 學習基底課程模組的第1章](../../../mrlearning-base-ch1.md)。

## <a name="enable-the-microsoft-spatializer-plugin"></a>啟用 Microsoft 空間定位器外掛程式

啟用 **Microsoft 空間定位器** 外掛程式。 開啟 [ **編輯-> 專案設定-> 音訊**]，然後將 **空間定位器外掛程式** 變更為 "Microsoft 空間定位器"。 **專案設定** 的 [**音訊**] 區段現在會如下所示：

![顯示空間定位器外掛程式的專案設定](images/spatial-audio/project-settings.png)

## <a name="enable-spatial-audio-on-your-workstation"></a>在您的工作站上啟用空間音訊

在桌上出版本的 Windows 上，預設會停用空間音訊。 以滑鼠右鍵按一下工作列中的音量圖示來啟用它。 若要取得您在 HoloLens 2 上聽到的最佳表示，請選擇 [ **空間音效-> 耳機用 Windows Sonic**]。

![桌面空間音訊設定](images/spatial-audio/desktop-audio-settings.png)

> [!NOTE]
> 只有當您打算在 Unity 編輯器中測試專案時，才需要此設定。

## <a name="next-steps"></a>後續步驟

> [!div class="nextstepaction"]
> [Unity 空間音訊章節2](unity-spatial-audio-ch2.md)

