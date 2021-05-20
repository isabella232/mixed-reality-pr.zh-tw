---
title: MRTK 組建視窗
description: 使用 MRTK for Unity 中的 [組建] 視窗的相關檔。
author: cre8ivepark
ms.author: dongpark
ms.date: 04/06/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、組建、組建視窗、工具
ms.openlocfilehash: 00ccbc5cfbb3b034771585a1263c624309b08465
ms.sourcegitcommit: 8f141a843bcfc57e1b18cc606292186b8ac72641
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2021
ms.locfileid: "110196845"
---
# <a name="build-window"></a>組建視窗
![組建 & 部署流程](images/MRTK_BuildWindow0.png)

MRTK 的 [組建] 視窗可讓您輕鬆地建立 & 部署 MRTK-Unity 專案。 只要按一下滑鼠按鍵，您就可以建立 Unity 專案並產生 Visual Studio 的解決方案 (。.SLN) 、UWP 應用程式套件 (。APPX) ，並在裝置上安裝應用程式套件。 


## <a name="unity-build-options"></a>Unity 組建選項
![組建視窗-Unity 組建選項1](images/MRTK_BuildWindow1.png)

這些場景來自 Unity 組建設定。 您可以使用下拉式功能表來變更目標裝置類型。

## <a name="appx-build-options"></a>Appx 組建選項
![組建視窗-Appx 組建選項2](images/MRTK_BuildWindow2.png)

此索引標籤會顯示 Visual Studio 解決方案的設定。 若要啟用 HoloLens 2 的眼睛追蹤輸入功能，請核取 [ **注視輸入功能** ] 選項。 

您可以在 [ **3D 應用程式啟動程式模型** ] 欄位中，為自訂的3d 應用程式啟動器圖示指派 glb 檔案。 如需詳細資訊，請參閱 [3d 應用程式啟動器設計指導](/windows/mixed-reality/distribute/3d-app-launcher-design-guidance) 方針。

依預設，會在版本控制選項中檢查 **自動遞增** 。 AppX 版本將會自動遞增。


## <a name="deploy-options"></a>部署選項
![組建視窗-部署選項3](images/MRTK_BuildWindow3.png)

在此索引標籤中，您可以輸入裝置入口網站的使用者名稱和密碼來連接到裝置。 

在頁面底部，您可以找到已建立的應用程式套件清單。 

