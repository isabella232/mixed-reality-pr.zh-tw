---
title: 使用舊版內建 XR 支援
description: 瞭解如何使用舊版內建 XR 支援，在不使用 MRTK 的情況下設定 Unity 專案。
author: hferrone
ms.author: alexturn
ms.date: 03/26/2021
ms.topic: article
keywords: Unity，混合的現實，開發，使用者入門，新專案，Windows Mixed Reality，UWP，XR，效能，舊版，mrtk
ms.openlocfilehash: 0860154034a63d5058da09a3b842e70bc3775dc5
ms.sourcegitcommit: 6272d086a2856e8b514a719e1f9e3b78554be5be
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/30/2021
ms.locfileid: "105938114"
---
# <a name="using-legacy-built-in-xr-support"></a>使用舊版內建 XR 支援

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

設定您的平臺之後，您需要讓 Unity 知道在匯出時建立一個 [沉浸式視圖](../../design/app-views.md) ，而不是2d 視圖。

> [!CAUTION]
> Unity 2019 中的舊版 XR 已被取代，並已在 Unity 2020 中移除。

1. 從組建設定開啟 **播放機設定** ... **視窗** 並展開 [ **XR 設定** ] 群組
2. 在 [ **XR 設定** ] 區段中，選取 [ **支援的虛擬實境** 新增虛擬實境裝置] 清單
3. 將 **深度格式** 設定為 **16 位深度** ，並啟用 **深度緩衝區共用**
4. 將 **身歷聲轉譯模式** 設定為 **單一傳遞實例**
5. 如果您想要使用全像攝影的遠端處理，請選取 [不 **支援的 WSA** 全像 

![醒目提示 [播放程式設定] 區段的 [在 unity 編輯器中開啟專案設定] 視窗的螢幕擷取畫面](images/wmr-config-img-9.png)