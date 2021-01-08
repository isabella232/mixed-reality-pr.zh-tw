---
title: 實作 3D 應用程式啟動器 (Win32 應用程式)
description: 瞭解如何建立適用于 [開始] 功能表和家用環境之 Win32 VR 應用程式和遊戲的3D 應用程式啟動器和標誌。
author: thmignon
ms.author: thmignon
ms.date: 07/12/2018
ms.topic: article
keywords: 3D，標誌，圖示，模型，啟動器，3D 啟動器，磚，即時 cube，win32，混合現實耳機，windows mixed reality 耳機，虛擬實境耳機，資訊清單
ms.openlocfilehash: 63b07664cb09f51e6d0588fdc50d141ad8985093
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009667"
---
# <a name="implement-3d-app-launchers-win32-apps"></a>實作 3D 應用程式啟動器 (Win32 應用程式)

> [!NOTE]
> 這項功能僅適用于執行最新 [Windows 測試人員](https://insider.windows.com) 航班 (RS5) 、組建17704和更新版本的電腦。

[Windows Mixed Reality home](../discover/navigating-the-windows-mixed-reality-home.md)是使用者在啟動應用程式之前所居住的起點。 根據預設，您需要從耳機外部啟動沉浸式 Win32 VR 應用程式和遊戲，而不會出現在 [Windows Mixed Reality [開始] 功能表] 的 [所有應用程式] 清單中。 如果您遵循這篇文章中的指示來執行3D 應用程式啟動程式，您可以從 Windows Mixed Reality [開始] 功能表和家用環境內啟動您的沉浸式 Win32 VR 體驗。

這僅適用于散佈在流外的沉浸式 Win32 VR 體驗。 針對 [透過](../develop/porting-apps/updating-your-steamvr-application-for-windows-mixed-reality.md)串流處理的 VR 體驗，我們已 [更新 SteamVR Beta 的 Windows Mixed Reality](https://steamcommunity.com/games/719950/announcements/detail/1687045485866139800) ，以及最新的 Windows 測試人員 RS5 航班，讓 SteamVR 標題使用預設啟動器自動顯示在 "所有應用程式" 清單的 Windows Mixed Reality [開始] 功能表中。 換句話說，這篇文章中所述的方法對 SteamVR 標題是不必要的，而且將會由 Windows Mixed Reality SteamVR Beta 版功能來覆寫。

## <a name="3d-app-launcher-creation-process"></a>3D 應用程式啟動器建立流程

建立3D 應用程式啟動器有三個步驟：
1. [設計和 concepting](3d-app-launcher-design-guidance.md)
2. [模型化和匯出](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
3.  (本文中將其整合到您的應用程式) 

要做為應用程式的啟動器使用的3D 資產，應使用 [Windows Mixed Reality 撰寫指導方針](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) ，以確保相容性。 無法符合此撰寫規格的資產不會在 Windows Mixed Reality 首頁轉譯。

## <a name="configuring-the-3d-launcher"></a>設定3D 啟動器

如果您為這些應用程式建立了3D 應用程式啟動器，Win32 應用程式將會出現在 Windows Mixed Reality [開始] 功能表的「所有應用程式」清單中。 若要這樣做，請依照下列步驟，建立參考3D 應用程式啟動器的 [視覺元素資訊清單](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx) XML 檔案：

1. 建立 **3D 應用程式啟動器資產 GLB** 檔 (查看 [模型和匯出](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)) 。
2. 為您的應用程式建立 **[視覺元素資訊清單](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx)** 。
    1. 您可以從 [下列範例](#sample-visual-elements-manifest)開始。  如需詳細資訊，請參閱完整的 [Visual Elements 資訊清單](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx) 檔。
    2. 針對您的應用程式使用 PNG/JPG/GIF 更新 **Square150x150Logo** 和 **Square70x70Logo** 。
        * 這些將用於應用程式在 Windows Mixed Reality [所有應用程式] 清單和桌面的 [開始] 功能表中的2D 標誌。
        * 檔案路徑是以包含視覺元素資訊清單的資料夾為基礎。
        * 您仍然需要透過標準機制提供應用程式的桌面 [開始] 功能表圖示。 這可以直接在可執行檔中，也可以在您建立的快捷方式中。 例如，via IShellLink：： SetIconLocation。
        * *選用：* 如果您想要讓 MRT.LOG 針對不同的解析度比例和高對比主題提供多個資產大小，您可以使用 .resources pri 檔案。
    3. 更新 **MixedRealityModel 路徑** 以指向您3D 應用程式啟動器的 GLB
    4. 使用與您的可執行檔相同的名稱來儲存檔案，副檔名為 ".VisualElementsManifest.xml"，並將它儲存在相同的目錄中。 例如，針對可執行檔 "contoso.exe"，隨附的 XML 檔案會命名為 "contoso.visualelementsmanifest.xml"。
3. **將應用程式的快捷方式新增** 至桌面 Windows [開始] 功能表。 如需 c + + 的範例，請參閱 [下列範例](#sample-app-launcher-shortcut-creation) 。 
    * 在%ALLUSERSPROFILE%\Microsoft\Windows\Start Menu\Programs (machine) 或%APPDATA%\Microsoft\Windows\Start Menu\Programs (使用者) 中建立它
    * 如果更新變更您的視覺元素資訊清單或它所參考的資產，更新程式或安裝程式應該會更新快捷方式，以便重新剖析資訊清單，並更新快取的資產。
4. *選用：* 如果您的桌面快捷方式未直接指向應用程式的 EXE (例如，如果叫用自訂通訊協定處理常式（例如 "myapp://" ) ），[開始] 功能表將不會自動找到應用程式的 VisualElementsManifest.xml 檔。 若要解決這個問題，快速鍵應使用 AppUserModel. VisualElementsManifestHintPath ( # A1 來指定視覺元素資訊清單的檔案路徑。 您可以使用與 System.AppUserModel.ID 相同的技術，在快速鍵中設定這個設定。 您不需要使用 System.AppUserModel.ID，但如果您想要讓快捷方式符合應用程式的明確應用程式使用者模型識別碼（如果使用的話），則您可能會這麼做。  如需 c + + 範例，請參閱下面的 [範例應用程式啟動程式快捷方式建立](#sample-app-launcher-shortcut-creation) 一節。

### <a name="sample-visual-elements-manifest"></a>範例視覺元素資訊清單

```xml
<Application xmlns:xsi="https://www.w3.org/2001/XMLSchema-instance">
  <VisualElements
    ShowNameOnSquare150x150Logo="on"
    Square150x150Logo="YOUR_APP_LOGO_150X150.png"
    Square70x70Logo=" YOUR_APP_LOGO_70X70.png"
    ForegroundText="light"
    BackgroundColor="#000000">
    <MixedRealityModel Path="YOUR_3D_APP_LAUNCHER_ASSET.glb">
        <SpatialBoundingBox Center="0,0,0" Extents="Auto" />
    </MixedRealityModel>
  </VisualElements>
</Application>
```

### <a name="sample-app-launcher-shortcut-creation"></a>範例應用程式啟動程式快捷方式建立

下列範例程式碼顯示如何在 c + + 中建立快捷方式，包括覆寫 Visual Elements 資訊清單 XML 檔案的路徑。 請注意，只有當您的快捷方式未直接指向與資訊清單相關聯的 EXE 時，才需要覆寫 (例如，您的快捷方式會使用自訂通訊協定處理常式，例如 "myapp://" ) 。

#### <a name="sample-lnk-shortcut-creation-c"></a>樣品。 (c + +) 的 .LNK 快速鍵建立

```cpp
#include <windows.h>
#include <propkey.h>
#include <shlobj_core.h>
#include <shlwapi.h>
#include <propvarutil.h>
#include <wrl.h>

#include <memory>

using namespace Microsoft::WRL;

#define RETURN_IF_FAILED(x) do { HRESULT hr = x; if (FAILED(hr)) { return hr; } } while(0)
#define RETURN_IF_WIN32_BOOL_FALSE(x) do { DWORD res = x; if (res == 0) { return HRESULT_FROM_WIN32(GetLastError()); } } while(0)

int wmain()
{
    RETURN_IF_FAILED(CoInitializeEx(nullptr, COINIT_APARTMENTTHREADED));

    ComPtr<IShellLink> shellLink;
    RETURN_IF_FAILED(CoCreateInstance(__uuidof(ShellLink), nullptr, CLSCTX_INPROC_SERVER, IID_PPV_ARGS(&shellLink)));
    RETURN_IF_FAILED(shellLink->SetPath(L"MyLauncher://launch/app-identifier"));

    // It is also possible to use an icon file in another location. For example, "C:\Program Files (x86)\MyLauncher\assets\app-identifier.ico".
    RETURN_IF_FAILED(shellLink->SetIconLocation(L"C:\\Program Files (x86)\\MyLauncher\\apps\\app-identifier\\game.exe", 0 /*iIcon*/));

    ComPtr<IPropertyStore> propStore;
    RETURN_IF_FAILED(shellLink.As(&propStore));

    {
        // Optional: If the application has an explict Application User Model ID, then you should usually specify it in the shortcut.
        PROPVARIANT propVar;
        RETURN_IF_FAILED(InitPropVariantFromString(L"ExplicitAppUserModelID", &propVar));
        RETURN_IF_FAILED(propStore->SetValue(PKEY_AppUserModel_ID, propVar));
        PropVariantClear(&propVar);
    }

    {
        // A hint path to the manifest is only necessary if the target path of the shortcut is not a file path to the executable.
        // By convention the manifest is named <executable name>.VisualElementsManifest.xml and is in the same folder as the executable
        // (and resources.pri if applicable). Assets referenced by the manifest are relative to the folder containing the manifest.

        //
        // PropKey.h
        //
        //  Name:     System.AppUserModel.VisualElementsManifestHintPath -- PKEY_AppUserModel_VisualElementsManifestHintPath
        //  Type:     String -- VT_LPWSTR  (For variants: VT_BSTR)
        //  FormatID: {9F4C2855-9F79-4B39-A8D0-E1D42DE1D5F3}, 31
        //  
        //  Suggests where to look for the VisualElementsManifest for a Win32 app
        //
        // DEFINE_PROPERTYKEY(PKEY_AppUserModel_VisualElementsManifestHintPath, 0x9F4C2855, 0x9F79, 0x4B39, 0xA8, 0xD0, 0xE1, 0xD4, 0x2D, 0xE1, 0xD5, 0xF3, 31);
        // #define INIT_PKEY_AppUserModel_VisualElementsManifestHintPath { { 0x9F4C2855, 0x9F79, 0x4B39, 0xA8, 0xD0, 0xE1, 0xD4, 0x2D, 0xE1, 0xD5, 0xF3 }, 31 }

        PROPVARIANT propVar;
        RETURN_IF_FAILED(InitPropVariantFromString(L"C:\\Program Files (x86)\\MyLauncher\\apps\\app-identifier\\game.visualelementsmanifest.xml", &propVar));
        RETURN_IF_FAILED(propStore->SetValue(PKEY_AppUserModel_VisualElementsManifestHintPath, propVar));
        PropVariantClear(&propVar);
    }

    constexpr PCWSTR shortcutPath = L"%APPDATA%\\Microsoft\\Windows\\Start Menu\\Programs\\game.lnk";
    const DWORD requiredBufferLength = ExpandEnvironmentStrings(shortcutPath, nullptr, 0);
    RETURN_IF_WIN32_BOOL_FALSE(requiredBufferLength);

    const auto expandedShortcutPath = std::make_unique<wchar_t[]>(requiredBufferLength);
    RETURN_IF_WIN32_BOOL_FALSE(ExpandEnvironmentStrings(shortcutPath, expandedShortcutPath.get(), requiredBufferLength));

    ComPtr<IPersistFile> persistFile;
    RETURN_IF_FAILED(shellLink.As(&persistFile));
    RETURN_IF_FAILED(persistFile->Save(expandedShortcutPath.get(), FALSE));

    return 0;
}
```

#### <a name="sample-url-launcher-shortcut"></a>樣品。URL 啟動器快捷方式 

```
[{9F4C2855-9F79-4B39-A8D0-E1D42DE1D5F3}]
Prop31=C:\Program Files (x86)\MyLauncher\apps\app-identifier\game.visualelementsmanifest.xml
Prop5=ExplicitAppUserModelID

[{000214A0-0000-0000-C000-000000000046}]
Prop3=19,0

[InternetShortcut]
IDList=
URL=MyLauncher://launch/app-identifier
IconFile=C:\Program Files (x86)\MyLauncher\apps\app-identifier\game.exe
IconIndex=0
```

## <a name="see-also"></a>請參閱

* 包含3D 應用程式啟動器的[混合現實模型範例](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/MixedRealityModel)。
* [3D 應用程式啟動程式設計指引](3d-app-launcher-design-guidance.md)
* [建立要在 Windows Mixed Reality 首頁中使用的3D 模型](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [ (UWP 應用程式執行3D 應用程式啟動器) ](implementing-3d-app-launchers.md)
* [瀏覽 Windows Mixed Reality 住家](../discover/navigating-the-windows-mixed-reality-home.md)
