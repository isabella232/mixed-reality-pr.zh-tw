---
title: 空間音訊教學課程-1。 在專案中新增空間音訊
description: 將 Microsoft 空間定位器外掛程式新增至您的 Unity 專案，以存取 HoloLens 2 HRTF 硬體卸載。
author: kegodin
ms.author: v-hferrone
ms.date: 02/05/2021
ms.topic: article
keywords: 混合的現實、unity、教學課程、hololens2、空間音訊、MRTK、混合現實工具組、UWP、Windows 10、HRTF、前端相關的傳送功能、回音、Microsoft 空間定位器
ms.openlocfilehash: 7ed1355e3c522fcd94a96dd761a8a9ebb01c4c4c
ms.sourcegitcommit: 68140e9ce84e69a99c2b3d970c7b8f2927a7fc93
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/05/2021
ms.locfileid: "99590040"
---
# <a name="1-adding-spatial-audio-to-your-unity-project"></a>1. 將空間音訊新增至 Unity 專案

## <a name="overview"></a>概觀

歡迎使用 HoloLens2 上適用于 Unity 的空間音訊教學課程。 透過本教學課程系列，您將瞭解如何在 HoloLens 2 上使用 head 相關的傳送功能 (HRTF) 卸載，以及如何在使用 HRTF 卸載時啟用回音。

[Microsoft 空間定位器 GitHub 存放庫](https://github.com/microsoft/spatialaudio-unity)已完成此教學課程順序的 Unity 專案。

若要瞭解使用以 HRTF 為基礎的 spatialization 技術來 spatialize 音效的意義，以及它可能有説明的建議，請參閱 [空間音效設計](/windows/mixed-reality/spatial-sound-design)。

## <a name="what-is-hrtf-offload"></a>什麼是 HRTF 卸載？

使用以 HRTF 為基礎的演算法處理音訊需要大量的特製化計算。 HoloLens 2 包含專用硬體，可用來避免應用程式處理器額外負荷，進而「卸載」以 HRTF 為基礎的演算法處理。  Microsoft 空間定位器外掛程式提供簡單的方法，讓您的應用程式利用專用的 HRTF 硬體，讓您的應用程式可以使用更多應用程式處理器來執行空間音訊以外的作業。

## <a name="objectives"></a>目標

* 匯入和啟用 Microsoft 空間定位器外掛程式
* 在開發人員工作站上啟用空間音訊

## <a name="prerequisites"></a>必要條件

* 已[安裝正確工具](../../install-the-tools.md)的 Windows 10 電腦
* 基本 C# 程式設計知識
* 已[針對開發而設定](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)的 HoloLens 2 裝置
* <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a>，已掛接 Unity 2019 LTS，且已新增通用 Windows 平台組建支援模組

我們 **強烈建議您** 先完成 [快速](mr-learning-base-01.md) 入門教學課程系列，或先利用 Unity 和 MRTK 的一些基本經驗，再繼續進行。

> [!IMPORTANT]
>
> * 本教學課程系列的建議 Unity 版本是 Unity 2019 LTS。 這個版本能取代上述連結必要條件中所述的任何 Unity 版本需求或建議。

## <a name="creating-and-preparing-the-unity-project"></a>建立和準備 Unity 專案

在本節中，您將建立新的 Unity 專案，並使該專案準備好進行 MRTK 開發。

為此，請先遵循[初始化您的專案和第一個應用程式](mr-learning-base-02.md) (但不包括[對您的裝置建置應用程式](mr-learning-base-02.md#building-your-application-to-your-hololens-2)的指示)，其中包括下列步驟：

1. [建立 Unity 專案](mr-learning-base-02.md#creating-the-unity-project)，並為其提供適當的名稱，例如「MRTK 教學課程」

1. [切換建置平台](mr-learning-base-02.md#configuring-the-unity-project)

1. [匯入 TextMeshPro 基本資源](mr-learning-base-02.md#importing-the-textmeshpro-essential-resources)

1. [匯入混合實境工具組](mr-learning-base-02.md#importing-the-mixed-reality-toolkit)

1. [設定 Unity 專案](mr-learning-base-02.md#configuring-the-unity-project)

1. [建立和設定場景](mr-learning-base-02.md#creating-and-configuring-the-scene) ，並為場景提供適當的名稱，例如 *SpatialAudio*

然後，遵循 [變更空間感知顯示選項](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) 的指示，以確定您場景的 MRTK 設定檔是 **DefaultHoloLens2ConfigurationProfile** ，並將空間感知網格的顯示選項變更為 **遮蔽**。

## <a name="adding-microsoft-spatializer-to-the-project"></a>將 Microsoft 空間定位器新增至專案

下載並匯入 Microsoft 空間定位器  <a href="https://github.com/microsoft/spatialaudio-unity/releases/download/v1.0.18/Microsoft.SpatialAudio.Spatializer.Unity.1.0.18.unitypackage" target="_blank">SpatialAudio. 空間定位器. 1.0.18. unitypackage </a>

>[!TIP]
> 如需有關如何匯入 Unity 自訂套件的提醒，您可以參考匯 [入教學課程資產](mr-learning-base-04.md#importing-the-tutorial-assets) 的指示。

## <a name="enable-the-microsoft-spatializer-plugin"></a>啟用 Microsoft 空間定位器外掛程式

匯入 **Microsoft 空間定位器** 之後，您必須加以啟用。 開啟 [ **編輯-> 專案設定-> 音訊**]，然後將 **空間定位器外掛程式** 變更為 "Microsoft 空間定位器"。

![顯示空間定位器外掛程式的專案設定](images/spatial-audio/spatial-audio-01-section3-step1-1.png)

## <a name="enable-spatial-audio-on-your-workstation"></a>在您的工作站上啟用空間音訊

在桌上出版本的 Windows 上，預設會停用空間音訊。 以滑鼠右鍵按一下工作列中的音量圖示來啟用它。 若要取得您在 HoloLens 2 上聽到的最佳表示，請選擇 [ **空間音效-> 耳機用 Windows Sonic**]。

![桌面空間音訊設定](images/spatial-audio/spatial-audio-01-section4-step1-1.png)

> [!NOTE]
> 只有當您打算在 Unity 編輯器中測試專案時，才需要此設定。

## <a name="congratulations"></a>恭喜！

在本教學課程中，您已學會如何匯入和啟用 Microsoft 空間定位器外掛程式，也可以在您的工作站上啟用空間音訊。
在下一個教學課程中，您將瞭解如何在 unity 專案中新增空間音訊。

> [!div class="nextstepaction"]
> [下一個教學課程： 2. Spatializing 按鈕互動音效](unity-spatial-audio-ch2.md)
