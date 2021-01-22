---
title: 發佈至 Microsoft Store
description: 了解如何封裝、認證 Unreal 混合實境應用程式，以及將這些應用程式發佈到 Microsoft Store。
author: hferrone
ms.author: jacksonf
ms.date: 12/3/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 混合實境, 開發, 文件, 指南, 功能, 混合實境頭戴式裝置, windows 混合實境頭戴式裝置, 虛擬實境頭戴式裝置, 發佈, 散發, Microsoft Store
ms.openlocfilehash: 3a975d9c66e64f56919163e9d3aa65a3126d6379
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583596"
---
# <a name="publishing-to-the-microsoft-store"></a>發佈至 Microsoft Store

當您準備好要對外發佈您的 Unreal 應用程式時，在提交至 Microsoft Store 之前，必須先更新幾項專案設定。 這些設定全都有預設值，但應針對生產環境加以變更，讓應用程式獲得最佳展現。

## <a name="project-settings-for-the-store-packaging"></a>市集封裝的專案設定

1. 首先，選取 [專案設定] > [說明]，並更新遊戲和發行者資訊： 
    * [遊戲名稱] 會出現在 HoloLens 上的應用程式磚中
    * 產生專案憑證時會使用 [公司辨別名稱]，而其格式應為： 
        * **CN=CommonName, O=OrganizationName, L=LocalityName, S=StateOrProvinceName, C=CountryName**：

![Unreal 編輯器的螢幕擷取畫面，其中已展開專案設定中的 [說明] 區段](images/unreal-publishing-img-01.png)

2. 展開專案設定的 [HoloLens] 區段，並更新封裝資源。  應用程式的市集頁面上會顯示下列資源名稱：

![Unreal 編輯器的螢幕擷取畫面，其中已展開專案設定中的 [封裝] 區段](images/unreal-publishing-img-02.png)

3. 展開 [影像] 區段，並以顯示商店應用程式的材質來更新預設市集影像。  選擇性地選取 [3D 標誌] 核取方塊，以上傳在啟動應用程式時作為 3D 即時立方體的 glb 檔案：

![Unreal 編輯器的螢幕擷取畫面，其中已展開專案設定中的 [影像] 區段](images/unreal-publishing-img-03.png)

4. 最後，選取 [產生新的]，以從專案名稱和公司辨別名稱產生簽署憑證  
    * 設定 [磚背景色彩]，此色彩會顯示在商店影像中任何透明像素的位置上。
    * 展開下拉式清單，並啟用 [使用零售 Windows Store 環境]，使其在零售鎖定 (而非開發解除鎖定) 的裝置上執行。

![Unreal 編輯器的螢幕擷取畫面，其中已展開專案設定中的 [憑證產生] 區段](images/unreal-publishing-img-04.png)

## <a name="optional-app-installer"></a>選用應用程式安裝

您可以從 [專案設定] > [HoloLens] 建立應用程式安裝程式檔案，用來在市集以外散發應用程式。  啟用 [應建立應用程式安裝程式] 核取方塊，並設定要用來儲存遊戲 appxbundle 的 URL 或網路路徑。  

![Unreal 編輯器的螢幕擷取畫面，其中已展開專案設定中的 [應用程式安裝程式] 區段](images/unreal-publishing-img-05.png)

封裝應用程式時，將會產生 appxbundle 和 appinstaller。  將 appxbundle 上傳至安裝 URL，然後啟動 appinstaller 以從網路位置安裝應用程式。

## <a name="windows-app-certification-kit"></a>Windows 應用程式認證套件

Windows 10 SDK 隨附 Windows 應用程式認證套件 (WACK)，用以驗證可能影響到套件上傳至市集的常見問題。  您可以在 Windows Kits 目錄中找到 WACK，通常位於下列路徑下： 

```
C:\Program Files (x86)\Windows Kits\10\App Certification Kit.
```

1. 將 appx 檔案封裝以供發佈後，請執行 **appcertui.exe**，並依照提示對 appx 進行掃描：

![此螢幕擷取畫面顯示 Windows 應用程式認證套件中經選取要驗證的應用程式](images/unreal-publishing-img-06.png)

2. 選取 [驗證市集應用程式]：

![在 Windows 應用程式認證套件中選取驗證項目的螢幕擷取畫面](images/unreal-publishing-img-07.png)

3. 瀏覽頂端區段中的 appx，然後選取 [下一步]：

![在 Windows 應用程式認證套件中選取測試項目的螢幕擷取畫面](images/unreal-publishing-img-08.png)

4. 選取 [下一步] 以執行測試並建立報表：
    * 依預設會啟用可在主機電腦上執行的所有測試

![Windows 應用程式認證套件中的應用程式驗證進度的螢幕擷取畫面](images/unreal-publishing-img-09.png)

5. 等候測試完成。 完成後，最後一個視窗會顯示通過或失敗的結果，您可以在儲存的報表中檢視該結果。

![Windows 應用程式認證套件中的最終報表結果的螢幕擷取畫面](images/unreal-publishing-img-10.png)

## <a name="known-wack-failure-with-425"></a>4\.25 的已知 WACK 失敗

Unreal 4.25 中的 Windows Mixed Reality 外掛程式將無法通過 WACK，因為在封裝 HoloLens 時，其中包含了一些 x64 二進位檔。 失敗的情形顯示如下：

![在 Windows 應用程式認證套件中，由於二進位分析器和支援的 API 而導致失敗結果的螢幕擷取畫面](images/unreal-publishing-img-11.png)

若要修正此問題：
1. 開啟 Unreal 專案，以瀏覽至 Unreal 安裝或來源目錄的根目錄，並以滑鼠右鍵按一下工作列中的 Unreal 圖示。
2. 以滑鼠右鍵按一下 UE4Editor，選取 [屬性]，然後瀏覽至 [位置] 項目中的路徑：

```
Open Engine\Plugins\Runtime\WindowsMixedReality\Source\WindowsMixedRealityHMD\WindowsMixedRealityHMD.Build.cs.
```

3. 在 **WindowsMixedRealityHMD.Build.cs** 中，將 **第 32行** 從：

```cpp
if(Target.Platform != UnrealTargetPlatform.Win32)
```

變更為：

```cpp
if(Target.Platform == UnrealTargetPlatform.Win64)

```

4. 關閉 Unreal、重新開啟專案，然後重新封裝 HoloLens。  重新執行 WACK，此錯誤就會消失。 

## <a name="see-also"></a>另請參閱

* [將應用程式提交到 Microsoft Store](../../distribute/submitting-an-app-to-the-microsoft-store.md)
* [Windows 應用程式認證套件](https://developer.microsoft.com/windows/downloads/app-certification-kit)
* [手動建立應用程式安裝程式檔案](/windows/msix/app-installer/how-to-create-appinstaller-file)