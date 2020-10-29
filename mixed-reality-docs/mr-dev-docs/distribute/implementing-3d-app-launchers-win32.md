---
title: 實作 3D 應用程式啟動器 (Win32 應用程式)
description: 如何建立適用于 Win32 VR 應用程式和遊戲的3D 應用程式啟動器和標誌 (分散于串流) ，因此它們會顯示在 Windows Mixed Reality [開始] 功能表和家用環境中。
author: thmignon
ms.author: thmignon
ms.date: 07/12/2018
ms.topic: article
keywords: 3D，標誌，圖示，模型，啟動器，3D 啟動器，磚，即時 cube，win32
ms.openlocfilehash: 4b22c78e651687c293a1e47ff8e4e9106de631bf
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2020
ms.locfileid: "91679665"
---
# <a name="implement-3d-app-launchers-win32-apps"></a><span data-ttu-id="45162-104">實作 3D 應用程式啟動器 (Win32 應用程式)</span><span class="sxs-lookup"><span data-stu-id="45162-104">Implement 3D app launchers (Win32 apps)</span></span>

> [!NOTE]
> <span data-ttu-id="45162-105">這項功能僅適用于執行最新 [Windows 測試人員](https://insider.windows.com) 航班 (RS5) 、組建17704和更新版本的電腦。</span><span class="sxs-lookup"><span data-stu-id="45162-105">This feature is only available to PCs running the latest [Windows Insider](https://insider.windows.com) flights (RS5), build 17704 and newer.</span></span>

<span data-ttu-id="45162-106">[Windows Mixed Reality home](../discover/navigating-the-windows-mixed-reality-home.md)是使用者在啟動應用程式之前所居住的起點。</span><span class="sxs-lookup"><span data-stu-id="45162-106">The [Windows Mixed Reality home](../discover/navigating-the-windows-mixed-reality-home.md) is the starting point where users land before launching applications.</span></span> <span data-ttu-id="45162-107">根據預設，您必須從耳機外部啟動沉浸式 Win32 VR 應用程式和遊戲，而不會出現在 Windows Mixed Reality [開始] 功能表的「所有應用程式」清單中。</span><span class="sxs-lookup"><span data-stu-id="45162-107">By default, immersive Win32 VR apps and games have to be launched from outside the headset and won't appear in the "All apps" list on the Windows Mixed Reality Start menu.</span></span> <span data-ttu-id="45162-108">不過，依照本文中的指示來執行3D 應用程式啟動程式，您可以從 Windows Mixed Reality [開始] 功能表和家用環境內啟動您的沉浸式 Win32 VR 體驗。</span><span class="sxs-lookup"><span data-stu-id="45162-108">However, by following the instructions in this article to implement a 3D app launcher, your immersive Win32 VR experience can be launched from within the Windows Mixed Reality Start menu and home environment.</span></span>

<span data-ttu-id="45162-109">這僅適用于在流外 distributied 的沉浸式 Win32 VR 體驗。</span><span class="sxs-lookup"><span data-stu-id="45162-109">This is only true for immersive Win32 VR experiences distributied outside of Steam.</span></span> <span data-ttu-id="45162-110">針對 [透過](../develop/porting-apps/updating-your-steamvr-application-for-windows-mixed-reality.md)串流處理的 VR 體驗，我們已 [更新 SteamVR Beta 的 Windows Mixed Reality](https://steamcommunity.com/games/719950/announcements/detail/1687045485866139800) ，以及最新的 Windows 測試人員 RS5 航班，讓 SteamVR 標題使用預設啟動器自動顯示在 "所有應用程式" 清單的 Windows Mixed Reality [開始] 功能表中。</span><span class="sxs-lookup"><span data-stu-id="45162-110">For VR experiences [distributed through Steam](../develop/porting-apps/updating-your-steamvr-application-for-windows-mixed-reality.md), we've [updated the Windows Mixed Reality for SteamVR Beta](https://steamcommunity.com/games/719950/announcements/detail/1687045485866139800) along with the latest Windows Insider RS5 flights so that SteamVR titles show up in the Windows Mixed Reality Start menu in the "All apps" list automatically using a default launcher.</span></span> <span data-ttu-id="45162-111">換句話說，這篇文章中所述的方法對 SteamVR 標題是不必要的，而且將會由 Windows Mixed Reality SteamVR Beta 版功能來覆寫。</span><span class="sxs-lookup"><span data-stu-id="45162-111">In other words, the method described in this article is unnecessary for SteamVR titles and will be overridden by the Windows Mixed Reality for SteamVR Beta functionality.</span></span>

## <a name="3d-app-launcher-creation-process"></a><span data-ttu-id="45162-112">3D 應用程式啟動器建立流程</span><span class="sxs-lookup"><span data-stu-id="45162-112">3D app launcher creation process</span></span>

<span data-ttu-id="45162-113">建立3D 應用程式啟動器有3個步驟：</span><span class="sxs-lookup"><span data-stu-id="45162-113">There are 3 steps to creating a 3D app launcher:</span></span>
1. [<span data-ttu-id="45162-114">設計和 concepting</span><span class="sxs-lookup"><span data-stu-id="45162-114">Designing and concepting</span></span>](3d-app-launcher-design-guidance.md)
2. [<span data-ttu-id="45162-115">模型化和匯出</span><span class="sxs-lookup"><span data-stu-id="45162-115">Modeling and exporting</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
3. <span data-ttu-id="45162-116"> (本文中將其整合到您的應用程式) </span><span class="sxs-lookup"><span data-stu-id="45162-116">Integrating it into your application (this article)</span></span>

<span data-ttu-id="45162-117">要做為應用程式的啟動器使用的3D 資產，應使用 [Windows Mixed Reality 撰寫指導方針](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) ，以確保相容性。</span><span class="sxs-lookup"><span data-stu-id="45162-117">3D assets to be used as launchers for your application should be authored using the [Windows Mixed Reality authoring guidelines](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) to ensure compatibility.</span></span> <span data-ttu-id="45162-118">無法符合此撰寫規格的資產將不會在 Windows Mixed Reality 首頁轉譯。</span><span class="sxs-lookup"><span data-stu-id="45162-118">Assets that fail to meet this authoring specification will not be rendered in the Windows Mixed Reality home.</span></span>

## <a name="configuring-the-3d-launcher"></a><span data-ttu-id="45162-119">設定3D 啟動器</span><span class="sxs-lookup"><span data-stu-id="45162-119">Configuring the 3D launcher</span></span>

<span data-ttu-id="45162-120">如果您為這些應用程式建立了3D 應用程式啟動器，Win32 應用程式將會出現在 Windows Mixed Reality [開始] 功能表的「所有應用程式」清單中。</span><span class="sxs-lookup"><span data-stu-id="45162-120">Win32 applications will appear in the "All apps" list on the Windows Mixed Reality Start menu if you create a 3D app launcher for them.</span></span> <span data-ttu-id="45162-121">若要這樣做，請依照下列步驟，建立參考3D 應用程式啟動器的 [視覺元素資訊清單](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx) XML 檔案：</span><span class="sxs-lookup"><span data-stu-id="45162-121">To do that, create a [Visual Elements Manifest](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx) XML file referencing the 3D App Launcher by following these steps:</span></span>

1. <span data-ttu-id="45162-122">建立 **3D 應用程式啟動器資產 GLB** 檔 (查看 [模型和匯出](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)) 。</span><span class="sxs-lookup"><span data-stu-id="45162-122">Create a **3D App Launcher asset GLB file** (See [Modeling and exporting](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)).</span></span>
2. <span data-ttu-id="45162-123">為您的應用程式建立 **[視覺元素資訊清單](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx)** 。</span><span class="sxs-lookup"><span data-stu-id="45162-123">Create a **[Visual Elements Manifest](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx)** for your application.</span></span>
    1. <span data-ttu-id="45162-124">您可以從 [下列範例](#sample-visual-elements-manifest)開始。</span><span class="sxs-lookup"><span data-stu-id="45162-124">You can start with the [sample below](#sample-visual-elements-manifest).</span></span>  <span data-ttu-id="45162-125">如需詳細資訊，請參閱完整的 [Visual Elements 資訊清單](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx) 檔。</span><span class="sxs-lookup"><span data-stu-id="45162-125">See the full [Visual Elements Manifest](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx) documentation for more details.</span></span>
    2. <span data-ttu-id="45162-126">針對您的應用程式使用 PNG/JPG/GIF 更新 **Square150x150Logo** 和 **Square70x70Logo** 。</span><span class="sxs-lookup"><span data-stu-id="45162-126">Update **Square150x150Logo** and **Square70x70Logo** with a PNG/JPG/GIF for your app.</span></span>
        * <span data-ttu-id="45162-127">這些將用於應用程式在 Windows Mixed Reality [所有應用程式] 清單和桌面的 [開始] 功能表中的2D 標誌。</span><span class="sxs-lookup"><span data-stu-id="45162-127">These will be used for the app’s 2D logo in the Windows Mixed Reality All Apps list and for the Start Menu on desktop.</span></span>
        * <span data-ttu-id="45162-128">檔案路徑是相對於包含視覺元素資訊清單的資料夾。</span><span class="sxs-lookup"><span data-stu-id="45162-128">The file path is relative to the folder containing the Visual Elements Manifest.</span></span>
        * <span data-ttu-id="45162-129">您仍然需要透過標準機制提供應用程式的桌面 [開始] 功能表圖示。</span><span class="sxs-lookup"><span data-stu-id="45162-129">You still need to provide a desktop Start Menu icon for your app through the standard mechanisms.</span></span> <span data-ttu-id="45162-130">這可以直接在可執行檔或您建立的快捷方式中 (例如 via IShellLink：： SetIconLocation) 。</span><span class="sxs-lookup"><span data-stu-id="45162-130">This can either be directly in the executable or in the shortcut you create (e.g. via IShellLink::SetIconLocation).</span></span>
        * <span data-ttu-id="45162-131">*選用：* 如果您想要讓 MRT.LOG 針對不同的解析度比例和高對比主題提供多個資產大小，您可以使用 .resources pri 檔案。</span><span class="sxs-lookup"><span data-stu-id="45162-131">*Optional:* You can use a resources.pri file if you would like for MRT to provide multiple asset sizes for different resolution scales and high contrast themes.</span></span>
    3. <span data-ttu-id="45162-132">更新 **MixedRealityModel 路徑** 以指向您3D 應用程式啟動器的 GLB</span><span class="sxs-lookup"><span data-stu-id="45162-132">Update the **MixedRealityModel Path** to point to the GLB for your 3D App Launcher</span></span>
    4. <span data-ttu-id="45162-133">使用與您的可執行檔相同的名稱來儲存檔案，副檔名為 ".VisualElementsManifest.xml"，並將它儲存在相同的目錄中。</span><span class="sxs-lookup"><span data-stu-id="45162-133">Save the file with the same name as your executable file, with an extension of ".VisualElementsManifest.xml" and save it in the same directory.</span></span> <span data-ttu-id="45162-134">例如，針對可執行檔 "contoso.exe"，隨附的 XML 檔案會命名為 "contoso.visualelementsmanifest.xml"。</span><span class="sxs-lookup"><span data-stu-id="45162-134">For example, for the executable file "contoso.exe", the accompanying XML file is named "contoso.visualelementsmanifest.xml".</span></span>
3. <span data-ttu-id="45162-135">**將應用程式的快捷方式新增** 至桌面 Windows [開始] 功能表。</span><span class="sxs-lookup"><span data-stu-id="45162-135">**Add a shortcut** to your application to the desktop Windows Start Menu.</span></span> <span data-ttu-id="45162-136">如需 c + + 的範例，請參閱 [下列範例](#sample-app-launcher-shortcut-creation) 。</span><span class="sxs-lookup"><span data-stu-id="45162-136">See the [sample below](#sample-app-launcher-shortcut-creation) for an example C++ implementation.</span></span> 
    * <span data-ttu-id="45162-137">在%ALLUSERSPROFILE%\Microsoft\Windows\Start Menu\Programs (machine) 或%APPDATA%\Microsoft\Windows\Start Menu\Programs (使用者) 中建立它</span><span class="sxs-lookup"><span data-stu-id="45162-137">Create it in %ALLUSERSPROFILE%\Microsoft\Windows\Start Menu\Programs (machine) or %APPDATA%\Microsoft\Windows\Start Menu\Programs (user)</span></span>
    * <span data-ttu-id="45162-138">如果更新變更您的視覺元素資訊清單或它所參考的資產，更新程式或安裝程式應該會更新快捷方式，以便重新剖析資訊清單，並更新快取的資產。</span><span class="sxs-lookup"><span data-stu-id="45162-138">If an update changes your visual elements manifest or the assets referenced by it, the updater or installer should update the shortcut such that the manifest is reparsed and cached assets are updated.</span></span>
4. <span data-ttu-id="45162-139">*選用：* 如果您的桌面快捷方式沒有直接指向應用程式的 EXE (例如，如果叫用像是 "myapp://" ) 的自訂通訊協定處理常式，則 [開始] 功能表將不會自動找到應用程式的 VisualElementsManifest.xml 檔。</span><span class="sxs-lookup"><span data-stu-id="45162-139">*Optional:* If your desktop shortcut does not point directly to your application’s EXE (e.g., if it invokes a custom protocol handler like “myapp://”), the Start Menu won’t automatically find the app’s VisualElementsManifest.xml file.</span></span> <span data-ttu-id="45162-140">若要解決這個問題，快速鍵應使用 AppUserModel. VisualElementsManifestHintPath ( # A1 來指定視覺元素資訊清單的檔案路徑。</span><span class="sxs-lookup"><span data-stu-id="45162-140">To resolve this, the shortcut should specify the file path of the Visual Elements Manifest using System.AppUserModel.VisualElementsManifestHintPath ().</span></span> <span data-ttu-id="45162-141">您可以使用與 System.AppUserModel.ID 相同的技術，在快速鍵中設定這個設定。</span><span class="sxs-lookup"><span data-stu-id="45162-141">This can be set in the shortcut using the same techniques as System.AppUserModel.ID.</span></span> <span data-ttu-id="45162-142">您不一定要使用 System.AppUserModel.ID，但如果您想要讓快捷方式符合應用程式的明確應用程式使用者模型識別碼（如果使用的話），則您可能會這麼做。</span><span class="sxs-lookup"><span data-stu-id="45162-142">You are not required to use System.AppUserModel.ID but you may do so if you wish for the shortcut to match the explicit Application User Model ID of the application if one is used.</span></span>  <span data-ttu-id="45162-143">如需 c + + 範例，請參閱下面的 [範例應用程式啟動程式快捷方式建立](#sample-app-launcher-shortcut-creation) 一節。</span><span class="sxs-lookup"><span data-stu-id="45162-143">See the [sample app launcher shortcut creation](#sample-app-launcher-shortcut-creation) section below for a C++ sample.</span></span>

### <a name="sample-visual-elements-manifest"></a><span data-ttu-id="45162-144">範例視覺元素資訊清單</span><span class="sxs-lookup"><span data-stu-id="45162-144">Sample Visual Elements Manifest</span></span>

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

### <a name="sample-app-launcher-shortcut-creation"></a><span data-ttu-id="45162-145">範例應用程式啟動程式快捷方式建立</span><span class="sxs-lookup"><span data-stu-id="45162-145">Sample app launcher shortcut creation</span></span>

<span data-ttu-id="45162-146">下列範例程式碼顯示如何在 c + + 中建立快捷方式，包括覆寫 Visual Elements 資訊清單 XML 檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="45162-146">The sample code below shows how you can create a shortcut in C++, including overriding the path to the Visual Elements Manifest XML file.</span></span> <span data-ttu-id="45162-147">請注意，只有當您的快捷方式未直接指向與資訊清單相關聯的 EXE 時，才需要覆寫 (例如</span><span class="sxs-lookup"><span data-stu-id="45162-147">Note the override is only required in cases where your shortcut does not point directly to the EXE associated with the manifest (eg.</span></span> <span data-ttu-id="45162-148">您的快捷方式會使用自訂通訊協定處理常式，例如 "myapp://" ) 。</span><span class="sxs-lookup"><span data-stu-id="45162-148">your shortcut uses a custom protocol handler like "myapp://").</span></span>

#### <a name="sample-lnk-shortcut-creation-c"></a><span data-ttu-id="45162-149">樣品。 (c + +) 的 .LNK 快速鍵建立</span><span class="sxs-lookup"><span data-stu-id="45162-149">Sample .LNK shortcut creation (C++)</span></span>

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

#### <a name="sample-url-launcher-shortcut"></a><span data-ttu-id="45162-150">樣品。URL 啟動器快捷方式</span><span class="sxs-lookup"><span data-stu-id="45162-150">Sample .URL launcher shortcut</span></span> 

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

## <a name="see-also"></a><span data-ttu-id="45162-151">另請參閱</span><span class="sxs-lookup"><span data-stu-id="45162-151">See also</span></span>

* <span data-ttu-id="45162-152">包含3D 應用程式啟動器的[混合現實模型範例](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/MixedRealityModel)。</span><span class="sxs-lookup"><span data-stu-id="45162-152">[Mixed reality model sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/MixedRealityModel) containing a 3D app launcher.</span></span>
* [<span data-ttu-id="45162-153">3D 應用程式啟動程式設計指引</span><span class="sxs-lookup"><span data-stu-id="45162-153">3D app launcher design guidance</span></span>](3d-app-launcher-design-guidance.md)
* [<span data-ttu-id="45162-154">建立要在 Windows Mixed Reality 首頁中使用的3D 模型</span><span class="sxs-lookup"><span data-stu-id="45162-154">Creating 3D models for use in the Windows Mixed Reality home</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [<span data-ttu-id="45162-155"> (UWP 應用程式執行3D 應用程式啟動器) </span><span class="sxs-lookup"><span data-stu-id="45162-155">Implementing 3D app launchers (UWP apps)</span></span>](implementing-3d-app-launchers.md)
* [<span data-ttu-id="45162-156">瀏覽 Windows Mixed Reality 住家</span><span class="sxs-lookup"><span data-stu-id="45162-156">Navigating the Windows Mixed Reality home</span></span>](../discover/navigating-the-windows-mixed-reality-home.md)
