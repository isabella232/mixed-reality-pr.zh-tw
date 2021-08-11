---
title: MRTK 教學課程簡介
description: 本課程說明如何使用混合實境工具組 (MRTK) 從頭建立混合實境應用程式。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens, MRTK, 混合實境工具組, 解算器, 眼球追蹤, 語音命令
ms.localizationpriority: high
ms.openlocfilehash: e8eb878e7ab2fecf27defc5f28e045c4d4768682e95a3a42cda7f324a21617e5
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2021
ms.locfileid: "115224784"
---
# <a name="1-introduction-to-the-mrtk-tutorials"></a>1.MRTK 教學課程簡介

歡迎使用入門教學課程系列！ 在這些教學課程中，您將了解混合實境工具組 (MRTK) 及其所提供的一些功能。 您也會建立一個混合實境體驗，讓使用者可以探索模仿 NASA Mars Curiosity Rover (好奇號火星探測車) 的全像投影。 在此系列結束時，您將完全了解 MRTK，以及其如何加速您的開發流程。

此系列中的教學課程都是連續的，因此請以正確的順序逐一查看：

1. [簡介](mr-learning-base-01.md) (您正在此教學課程中)
2. [初始化您的專案並部署您的第一個應用程式](mr-learning-base-02.md)
3. [設定 MRTK 設定檔](mr-learning-base-03.md)
4. [將物件置放在場景中](mr-learning-base-04.md)
5. [使用解析器建立動態內容](mr-learning-base-05.md)
6. [建立使用者介面](mr-learning-base-06.md)
7. [與 3D 物件互動](mr-learning-base-07.md)
8. [使用眼球追蹤](mr-learning-base-08.md)
9. [使用語音命令](mr-learning-base-09.md)

## <a name="objectives"></a>目標

* 了解如何為 MRTK 設定 Unity
* 了解如何在您的裝置上建置和部署
* 了解如何使用 MRTK 的重要功能
* 建立完整的混合實境體驗

## <a name="prerequisites"></a>必要條件

* 已[安裝正確工具](../../install-the-tools.md)的 Windows 10 電腦
* [Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk/) 10.0.18362.0 或更新版本
* 已[針對開發而設定](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)的 HoloLens 2 裝置

* Unity <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">中樞</a>已安裝 UNITY 2020.3 LTS 或 UNITY 2019.4 LTS (**OpenXR 需要2020.3.8 或更新版本，以防止錯誤**) 

安裝 Unity 時，請務必檢查「 **平臺**」底下的下列元件。

* **通用 Windows 平臺組建支援**
* **Windows組建支援 (IL2CPP)**

<img src="../../../develop/images/Unity_Install_Option_UWP.png" alt="Unity Universal Windows Platform Build Support option" width="600px">

如果您已安裝 Unity 但未安裝這些選項，您可以透過 Unity Hub 中 **的 [新增模組** ] 功能表來新增這些選項。

<img src="../../../develop/images/Unity_Install_Option_UWP2.png" alt="Unity Hub - Add Module" width="600px">

> [!Important]
> 本教學課程系列的建議 MRTK 版本為 MRTK 2.7。2

> [!Important]
> 此教學課程系列支援 Unity 2020 LTS (目前的 2020.3) 如果您使用 Open XR 或 Windows XR 外掛程式，以及 unity 2019 LTS (目前 2019.4. x) 如果您使用舊版的 WSA 或 Windows XR 外掛程式。 這個版本能取代上述連結必要條件中所述的任何 Unity 版本需求。

> [!div class="nextstepaction"]
> [下一個教學課程：2.初始化您的專案並部署您的第一個應用程式](mr-learning-base-02.md)
