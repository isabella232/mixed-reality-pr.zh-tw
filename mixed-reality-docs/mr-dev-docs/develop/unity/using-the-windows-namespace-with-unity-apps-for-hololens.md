---
title: 使用 Unity 進行 HoloLens 的 WinRT Api
description: Leanr 如何在 Unity mixed reality 專案中使用 WinRT api 和 Windows 命名空間進行 HoloLens。
author: mikeriches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Unity、WinRT、windows mixed reality、API、逐步解說、混合現實耳機、windows mixed reality 耳機、虛擬實境耳機、混合現實 Api
ms.openlocfilehash: 158c28d9186269108442226bbfcfc90a3c235a71336fdab9dbf9eadc21a309a1
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2021
ms.locfileid: "115215604"
---
# <a name="winrt-apis-with-unity-for-hololens"></a>使用 Unity 進行 HoloLens 的 WinRT Api

本頁面說明如何在您的 Unity 專案中使用 WinRT Api 進行 HoloLens。

## <a name="mixed-reality-apis"></a>混合現實 Api

Windows SDK 的混合現實焦點子集已在 .NET Standard 2.0 相容投射中提供，您可以在專案中使用，而不需要預處理器指示詞。 Windows 中的大部分 Api。 認知及 Windows。Ui。輸入。空間命名空間包含在內，未來可能會擴充以包含其他 Api。 在編輯器中執行時，可以使用所投射的 Api，以啟用 [播放模式](/windows/mixed-reality/unity-play-mode)。 若要使用這項投射，請對您的專案進行下列修改：

1) 將參考加入至[Microsoft. Windows。](https://www.nuget.org/packages/Microsoft.Windows.MixedReality.DotNetWinRT)使用[NuGet for Unity 的](https://github.com/GlitchEnzo/NuGetForUnity)MixedReality NuGet 套件。
2) 命名空間的前置詞參考 `Windows` `Microsoft.` ：
```cs
using namespace Microsoft.Windows.Perception.Spatial;
```
3) 以下列內容取代原生指標轉換 `FromNativePtr` ：
```cs
var worldOrigin = SpatialCoordinateSystem.FromNativePtr(unityWorldOriginPtr);
```

## <a name="conditionally-include-winrt-api-calls"></a>有條件地包含 WinRT API 呼叫

您也可以使用預處理器指示詞，在針對通用 Windows 平臺和 Xbox One 平臺建立的 Unity 專案中使用 WinRT api。 您在以 WinRT Api 為目標的 Unity 腳本中撰寫的任何程式碼，都必須有條件地包含在這些組建中。 

這可以透過 Unity 中的兩個步驟來完成：
1) API 相容性層級必須設定為 [播放機] 設定中的 [ **.net 4.6** ] 或 [ **.NET Standard 2.0** ]
    - **編輯**  > **Project 設定**  > **播放機**  > 設定  > 將 **Api 相容性層級** 設為 **.net 4.6** 或 **.NET Standard 2.0**
2) 預處理器指示詞 **ENABLE_WINMD_SUPPORT** 必須包裝在任何 WinRT 的程式碼周圍

下列程式碼片段來自 Unity manual 頁面，適用于[c # 腳本中的通用 Windows 平臺： WinRT API](https://docs.unity3d.com/Manual/windowsstore-scripts.html)。 在此範例中，會傳回廣告識別碼，但只會傳回 UWP 和 Xbox One 組建：

```
using UnityEngine;
public class WinRTAPI : MonoBehaviour {
    void Update() {
        auto adId = GetAdvertisingId();
        // ...
    }

    string GetAdvertisingId() {
        #if ENABLE_WINMD_SUPPORT
            return Windows.System.UserProfile.AdvertisingManager.AdvertisingId;
        #else
            return "";
        #endif
    }
}
```

## <a name="edit-your-scripts-in-a-unity-c-project"></a>在 Unity c # 專案中編輯您的腳本

當您按兩下 Unity 編輯器中的腳本時，它預設會在編輯器專案中啟動您的腳本。 WinRT api 會顯示為未知，因為 Visual Studio 專案未參考 Windows 執行階段。 **ENABLE_WINMD_SUPPORT** 指示詞未定義，而且會忽略任何 *#if* 包裝程式碼，直到您將專案建立到 UWP Visual Studio 解決方案為止。

## <a name="see-also"></a>另請參閱
* [匯出和建置 Unity Visual Studio 解決方案](exporting-and-building-a-unity-visual-studio-solution.md)
* [Windows執行時間支援 Unity](https://docs.unity3d.com/Manual/IL2CPP-WindowsRuntimeSupport.html)