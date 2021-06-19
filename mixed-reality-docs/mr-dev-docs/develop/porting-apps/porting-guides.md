---
title: 將 VR 應用程式移植到 Windows Mixed Reality
description: 逐步解說逐步解說，說明如何將現有的沉浸式應用程式移植至 Windows Mixed Reality。
author: JBrentJ
ms.author: alexturn
ms.date: 12/9/2020
ms.topic: article
keywords: 埠、unity、unreal、中介軟體、引擎、UWP、Win32、移植、HoloLens 第1代、混合現實耳機、windows mixed reality 耳機、遷移、Windows 10、輸入對應、
ms.openlocfilehash: bb76325c0a2d10150cff6604e29c7ead8a97df8e
ms.sourcegitcommit: 6ade7e8ebab7003fc24f9e0b5fa81d091369622c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2021
ms.locfileid: "112394462"
---
# <a name="porting-vr-apps-to-windows-mixed-reality"></a>將 VR 應用程式移植到 Windows Mixed Reality

Windows 10 包含沉浸式和全像攝影耳機的支援。 如果您已建立其他裝置的內容（例如 Oculus Rift 或 HTC Vive），它們就會相依于存在於作業系統平臺 API 之上的程式庫。 將現有的 Win32 Unity VR 應用程式帶入 Windows Mixed Reality 牽涉到將廠商專屬的 VR Sdk 重定目標使用於 Unity 的跨廠商 VR Api。

## <a name="porting-requirements"></a>移植需求

概括而言，下列步驟牽涉到移植現有的內容：
1. **確定您的電腦正在執行 Windows 10 Fall Creators Update (16299) 。** 我們不再建議從 Insider Skip 通道接收預覽版，因為這些組建對於混合現實開發來說不是最穩定的。
2. **升級至最新版本的圖形或遊戲引擎。** 遊戲引擎將需要支援2017年4月) 或更高版本的 Windows 10 SDK 版本 10.0.15063.0 (。
3. **升級任何中介軟體、外掛程式或元件。** 如果您的應用程式包含任何元件，最好是升級到最新版本。
4. **移除重複 sdk 的** 相依性。 視內容的目標裝置而定，您必須移除或有條件地編譯該 SDK，讓您可以改為以 Windows Api 為目標。 此案例的範例將會 SteamVR。
5. **解決組建問題。** 此時，移植練習是您的應用程式、引擎和您擁有的元件相依性所特有的。

## <a name="common-porting-steps"></a>常見的移植步驟

### <a name="1-make-sure-you-have-the-right-development-hardware"></a>1. 請確定您有正確的開發硬體

[ [VR 愛好者指南](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines) ] 頁面會列出建議的開發硬體。

### <a name="2-upgrade-to-the-latest-flight-of-windows-10"></a>2. 升級到 Windows 10 的最新航班

Windows Mixed Reality 平臺仍在積極開發中。 建議您 [加入 Windows 測試人員計畫](https://insider.windows.com/) ，以存取「Windows 測試人員快速」飛行。
1. 安裝 [Windows 10 Creators Update](https://www.microsoft.com/software-download/windows10)
2. [加入](https://insider.windows.com/) Windows 測試人員計畫。
3. 啟用 [開發人員模式](/windows/uwp/get-started/enable-your-device-for-development)
4. 透過 [**設定] > 更新 & 安全性] 區段** 切換至 [Windows 測試人員快速航班](/archive/blogs/uktechnet/joining-insider-preview)

### <a name="3-upgrade-to-the-most-recent-build-of-visual-studio"></a>3. 升級為最新組建的 Visual Studio
* 如果您是使用 Visual Studio，請升級至最新的組建
* 請參閱 Visual Studio 2019 下 [的安裝工具](../install-the-tools.md#installation-checklist) 頁面

### <a name="4-choose-the-correct-adapter"></a>4. 選擇正確的介面卡
* 在具有兩個 Gpu 的筆記本系統中，以 [正確的介面卡為目標](../native/rendering-in-directx.md#hybrid-graphics-pcs-and-mixed-reality-applications)。 這適用于 Unity 和原生 DirectX 應用程式，其中會以明確或隱含的方式 (媒體基礎) ）來建立 ID3D11Device，以供其功能使用。

## <a name="unity-porting-guidance"></a>Unity 移植指引

[!INCLUDE[](includes/unity-porting-guidance.md)]

## <a name="unreal-porting-guidance"></a>Unreal 移植指引

> [!IMPORTANT]
> 如果您使用的是 HP 回 G2 控制器，請參閱 [本文以取得其他](../unreal/unreal-reverb-g2-controllers.md) 輸入對應指示。

## <a name="see-also"></a>另請參閱
* [Windows Mixed Reality 最小電腦硬體相容性指導方針](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)
* [瞭解混合現實的效能](../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md)
* [Unity 的效能建議](../unity/performance-recommendations-for-unity.md)
* [運動控制器](../../design/motion-controllers.md)
* [Unity 中的動作控制器](../unity/motion-controllers-in-unity.md)
* [UnityEngine. XR。輸入](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.html)
* [UnityEngine. XR. InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)
* [移植指南](porting-guides.md)