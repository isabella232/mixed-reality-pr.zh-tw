---
title: 選擇 Unity 版本和 XR 外掛程式
description: 隨時掌握最新的 Unity 與 XR 外掛程式建議，以進行 HoloLens 應用程式開發。
author: hferrone
ms.author: v-hferrone
ms.date: 03/26/2021
ms.topic: article
keywords: mixedrealitytoolkit、mixedrealitytoolkit-unity、mixed reality 耳機、windows mixed reality 耳機、虛擬實境耳機、unity
ms.openlocfilehash: b8f5f0131da811393ee053541e0c2fa0c735472e
ms.sourcegitcommit: 6272d086a2856e8b514a719e1f9e3b78554be5be
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/30/2021
ms.locfileid: "105938115"
---
# <a name="choosing-a-unity-version-and-xr-plugin"></a>選擇 Unity 版本和 XR 外掛程式

雖然我們目前 **建議您安裝 unity 2019.4 LTS，並使用舊版內建 XR** 進行混合現實開發，但您也可以使用其他 Unity 設定來建立應用程式。

## <a name="unity-20194-lts-recommended"></a>Unity 2019.4 LTS (建議的) 

Microsoft 目前針對 HoloLens 2 和 Windows Mixed Reality 開發建議的 Unity 設定，是 **使用舊版內建 XR 支援的 unity 2019.4 LTS** 。

安裝和管理 Unity 的最佳方式是透過 <a href="https://unity3d.com/get-unity/download" target="_blank">[Unity 中樞]</a>。 安裝之後，請開啟 Unity Hub：

1. 選取 [**安裝**] 索引標籤，然後選擇 [**新增**]
2. 選取 Unity 2019.4 LTS，然後按 **[下一步]**

![Unity 中樞定新版本](images/unity-hub-img-01.png)

3. 檢查「平臺」底下 **的** 下列元件
    * **通用 Windows 平臺組建支援** 
    * **Windows Build 支援 (IL2CPP)**

![Unity 通用 Windows 平臺組建支援選項](../images/Unity_Install_Option_UWP.png)

4. 如果您已安裝 Unity 但未安裝這些選項，您可以透過 Unity Hub 中 **的 [新增模組** ] 功能表來新增這些選項：

![Unity Windows Build 支援選項](../images/Unity_Install_Option_UWP2.png)

若要開始使用 Unity 2019.4 LTS 中的舊版內建 XR，請按一下這裡：

> [!div class="nextstepaction"]
> [設定舊版內建 XR](legacy-xr-support.md)

> [!NOTE]
> Unity 已淘汰自 Unity 2019 起的舊版內建 XR 支援。  雖然 Unity 2019 提供新的 XR 外掛程式架構，但 Microsoft 目前不建議在 Unity 2019 中使用該路徑，因為 Azure 空間錨點與 AR Foundation 2 不相容。  在 Unity 2020 中，XR 外掛程式架構內支援 Azure 空間錨點。

如果您正在開發適用于 HoloLens (第一代) 的應用程式，則 Unity 2019 LTS 會持續支援這些耳機，並具備舊版內建 XR，可在 Unity 2019 LTS 的完整生命週期內透過中2022。

## <a name="unity-20203-lts"></a>Unity 2020.3 LTS 

如果您使用的是 **Unity 2020.3 LTS**，您可以使用 **Windows XR 外掛程式** 來開發 HoloLens 2 和 Windows Mixed Reality 應用程式。

不過，有一些已知的問題會影響全息圖穩定性以及 HoloLens 2 上的其他功能： 

* 深度緩衝區提交回歸在最近的 Unity 2020 組建中，這會導致嚴重的全息圖不穩定。
* 使用通用 Windows 平臺組建目標的全像應用程式遠端處理應用程式無法運作。
* Unity 圖形工作系統預設為開啟，即使它與 HoloLens 專案不相容也是一樣。

如果您選擇在目前的 Unity 2020 中開始新的專案，請務必在交付您的應用程式之前，先追蹤更新 Unity 組建和 Windows XR 外掛程式組建的未來數個月。  這可確保您的使用者體驗適當的全息圖穩定性。

> [!div class="nextstepaction"]
> [使用 Windows XR 外掛程式](windows-xr-plugin.md)

### <a name="using-openxr"></a>使用 OpenXR

Unity 2020.3 LTS 也支援 **Mixed Reality OpenXR** 外掛程式的公開預覽。

Mixed Reality OpenXR 外掛程式完全支援 AR Foundation 4.0，提供 ARPlaneManager 和 ARRaycastManager 執行。 如此一來，您就可以撰寫點擊測試程式碼，然後跨越 HoloLens 2 和 ARCore/ARKit 的手機和平板電腦。 

今年之後， **unity 2020.3 LTS 與 OpenXR 外掛程式** 會成為建議的 unity 設定，而 unity 中的未來 HoloLens 2 功能只會透過此外掛程式公開。  您現在可以在這裡開始您的專案-不過，如果您的專案是以 HoloLens 2 為目標，則您目前會遇到 Unity 2020 全息圖穩定性和上述的其他問題。  在交付您的應用程式之前，請務必先回來查看更新 Unity 組建和 OpenXR 外掛程式組建的未來幾個月。  這可確保您的使用者體驗適當的全息圖穩定性。 

> [!div class="nextstepaction"]
> [使用 OpenXR 外掛程式](openxr-getting-started.md)

## <a name="unity-20211"></a>Unity 2021。1

如果您正在嘗試早期的 **Unity 2021.1** 組建，您應該移至 **OpenXR 外掛程式**，因為 Windows XR 外掛程式已在該處淘汰。  從 Unity 2021.2 開始，OpenXR 外掛程式將是唯一開發混合現實的途徑，因為 Windows XR 外掛程式將不再受到支援。

## <a name="unity-20184-lts"></a>Unity 2018.4 LTS

如果您已經有使用 Unity 2018.4 LTS 的專案，則您的 Unity 引擎會在發行後的2年繼續受到支援。  Unity 2018 LTS 將于2021年春季結束服務。
