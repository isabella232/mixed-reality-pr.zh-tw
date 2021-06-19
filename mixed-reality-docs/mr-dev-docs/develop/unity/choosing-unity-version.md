---
title: 選擇 Unity 版本和 XR 外掛程式
description: 隨時掌握最新的 Unity 與 XR 外掛程式建議，以進行 HoloLens 應用程式開發。
author: hferrone
ms.author: v-hferrone
ms.date: 06/18/2021
ms.topic: article
keywords: mixedrealitytoolkit、mixedrealitytoolkit-unity、mixed reality 耳機、windows mixed reality 耳機、虛擬實境耳機、unity
ms.openlocfilehash: 452692b1be98459cc242833149b1cfd91f0f4d4a
ms.sourcegitcommit: 6ade7e8ebab7003fc24f9e0b5fa81d091369622c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2021
ms.locfileid: "112394408"
---
# <a name="choosing-a-unity-version-and-xr-plugin"></a>選擇 Unity 版本和 XR 外掛程式

雖然我們目前 **建議您安裝 unity 2019.4 LTS，並使用舊版內建 XR** 進行混合現實開發，但您也可以使用其他 Unity 設定來建立應用程式。

## <a name="unity-20194-lts-recommended"></a>Unity 2019.4 LTS (建議的) 

Microsoft 目前針對 HoloLens 2 和 Windows Mixed Reality 開發建議的 Unity 設定，是 **使用舊版內建 XR 支援的 unity 2019.4 LTS** 。

安裝和管理 Unity 的最佳方式是透過 <a href="https://unity3d.com/get-unity/download" target="_blank">[Unity 中樞]</a>。 安裝之後，請開啟 Unity Hub：

1. 選取 [**安裝**] 索引標籤，然後選擇 [**新增**]
2. 選取 Unity 2019.4 LTS，然後按 **[下一步]**

![Unity 中樞定新版本](images/unity-hub-img-2019.png)

3. 檢查「平臺」底下 **的** 下列元件
    * **通用 Windows 平臺組建支援** 
    * **Windows Build 支援 (IL2CPP)**

![Unity 通用 Windows 平臺組建支援選項](images/Unity_Install_Option_UWP_2019.png)

4. 如果您已安裝 Unity 但未安裝這些選項，您可以透過 Unity Hub 中 **的 [新增模組** ] 功能表來新增這些選項：

![Unity Windows Build 支援選項](images/Unity_Install_Option_UWP2_2019.png)

若要開始使用 Unity 2019.4 LTS 中的舊版內建 XR，請按一下這裡：

> [!div class="nextstepaction"]
> [設定舊版內建 XR](/windows/mixed-reality/develop/unity/xr-project-setup?tabs=legacy)

> [!NOTE]
> Unity 已淘汰自 Unity 2019 起的舊版內建 XR 支援。  雖然 Unity 2019 提供新的 XR 外掛程式架構，但 Microsoft 目前不建議在 Unity 2019 中使用該路徑，因為 Azure 空間錨點與 AR Foundation 2 不相容。  在 Unity 2020 中，XR 外掛程式架構內支援 Azure 空間錨點。

如果您正在開發適用于 HoloLens (第一代) 的應用程式，則 Unity 2019 LTS 會持續支援這些耳機，並具備舊版內建 XR，可在 Unity 2019 LTS 的完整生命週期內透過中2022。

## <a name="unity-20203-lts"></a>Unity 2020.3 LTS 

如果您是使用 **Unity 2020.3 LTS**，Microsoft 目前的建議是最新的 **混合現實 OpenXR 外掛程式**。 您必須使用 Unity patch release 2020.3.8 f1 或更新版本，以避免早于2020.3 組建的已知效能問題。

Mixed Reality OpenXR 外掛程式完全支援 AR Foundation 4.0，提供 ARPlaneManager 和 ARRaycastManager 執行。 如此一來，您就可以撰寫點擊測試程式碼，然後跨越 HoloLens 2 和 ARCore/ARKit 的手機和平板電腦。

不過，有一些已知的問題會影響 Unity 2020 LTS 專案：

*  (URP) 10.5.0 或較舊版本的通用轉譯管線，在 HoloLens 2 裝置上的效能會受到負面影響。

如果您選擇在目前的 Unity 2020 中開始新的專案，請務必在推出您的應用程式之前，先追蹤更新 Unity 組建和 URP 套件的後續幾周。  這可確保您的使用者體驗適當的全息圖穩定性。

> [!div class="nextstepaction"]
> [使用 OpenXR 外掛程式](/windows/mixed-reality/develop/unity/xr-project-setup?tabs=openxr)

## <a name="unity-20211"></a>Unity 2021。1

如果您正在嘗試早期的 **Unity 2021.1** 組建，您應該移至 **OpenXR 外掛程式**，因為 Windows XR 外掛程式已在該處淘汰。  從 Unity 2021.2 開始，OpenXR 外掛程式將是唯一開發混合現實的途徑，因為 Windows XR 外掛程式將不再受到支援。

## <a name="unity-20184-lts"></a>Unity 2018.4 LTS

如果您已經有使用 Unity 2018.4 LTS 的專案，則您的 Unity 引擎會在發行後的2年繼續受到支援。  Unity 2018 LTS 將于2021年春季結束服務。