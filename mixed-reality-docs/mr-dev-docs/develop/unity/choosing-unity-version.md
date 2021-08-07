---
title: 選擇 Unity 版本和 XR 外掛程式
description: 隨時掌握最新的 Unity 和 XR 外掛程式建議，以 HoloLens 應用程式開發。
author: hferrone
ms.author: v-hferrone
ms.date: 06/24/2021
ms.topic: article
keywords: mixedrealitytoolkit、mixedrealitytoolkit-unity、mixed reality 耳機、windows mixed reality 耳機、虛擬實境耳機、unity
ms.openlocfilehash: 7d22ccee301345352ae384f8b237415f925bbd254e0923197130caf48540c171
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2021
ms.locfileid: "115210856"
---
# <a name="choosing-a-unity-version-and-xr-plugin"></a>選擇 Unity 版本和 XR 外掛程式

雖然我們目前 **建議您安裝 unity 2020.3 LTS 與混合現實開發的最新 Mixed Reality OpenXR 外掛程式** ，但您也可以使用其他 Unity 設定來建立應用程式。

## <a name="unity-20203-lts-recommended"></a>Unity 2020.3 LTS (建議的) 

Microsoft 目前針對 HoloLens 2 和 Windows Mixed Reality 開發建議的 unity 設定是 **unity 2020.3 LTS 與最新的 Mixed Reality OpenXR 外掛程式**。 您 **必須** 使用 Unity patch release 2020.3.8 f1 或更新版本，以避免早于2020.3 組建的已知效能問題。

> [!IMPORTANT]
> Unity 2020 不支援將 HoloLens 的目標設為 (第一代) 。 **[Unity 2019 LTS](#unity-20194-lts)** 中仍支援這些耳機，具有舊版內建 XR，可在 UNITY 2019 LTS 的完整生命週期內透過中2022。

安裝和管理 Unity 的最佳方式是透過 **Unity 中樞**：

1. 安裝 <a href="https://unity3d.com/get-unity/download" target="_blank">**Unity Hub**</a>。
2. 選取 [ **安裝** ] 索引標籤，然後選擇 [ **新增**]。
3. 選取 **Unity 2020.3 LTS** ，然後按 **[下一步]**。

![Unity 中樞安裝新版本](images/unity-hub-img-01.png)

4. 檢查「 **平臺**」底下的下列元件：
    * **通用 Windows 平臺組建支援**
    * **Windows組建支援 (IL2CPP)**

![Unity 通用 Windows 平臺組建支援選項](../images/Unity_Install_Option_UWP.png)

5. 如果您先前已安裝 Unity 但未安裝這些選項，您可以透過 Unity Hub 中 **的 [新增模組** ] 功能表來新增這些選項：

![Unity Windows 組建支援選項](../images/Unity_Install_Option_UWP2.png)

安裝 Unity 2020.3 之後，請開始使用 Mixed Reality OpenXR 外掛程式建立專案或升級現有的專案：

> [!div class="nextstepaction"]
> [使用 OpenXR 外掛程式設定您的專案](xr-project-setup.md?tabs=openxr)

> [!NOTE]
> 雖然我們建議您針對所有新的專案使用 OpenXR，但 Unity 2020.3 LTS 也支援[Windows 的 XR 外掛程式](xr-project-setup.md?tabs=windowsxr)。 此外掛程式完全受支援，但不會收到 AR Foundation 4.0 支援之類的新功能。

## <a name="unity-20194-lts"></a>Unity 2019.4 LTS

如果您需要使用 Unity 2019，您可以使用 **unity 2019 LTS 搭配舊版內建 XR**。 若要開始使用 Unity 2019.4 LTS 中的舊版內建 XR，請按一下這裡：

> [!div class="nextstepaction"]
> [使用舊版內建 XR 來設定您的專案](xr-project-setup.md?tabs=legacy)

> [!NOTE]
> Unity 已淘汰自 Unity 2019 起的舊版內建 XR 支援。  雖然 Unity 2019 提供新的 XR 外掛程式架構，但 Microsoft 目前不建議在 Unity 2019 中使用該路徑，因為 Azure 空間錨點與 AR Foundation 2 不相容。  在 Unity 2020 中，XR 外掛程式架構內支援 Azure 空間錨點。

如果您正在開發適用于 HoloLens (第1代) 的應用程式，則 unity 2019 LTS 會持續支援這些耳機，並具備舊版內建 XR，可在 unity 2019 LTS 的完整生命週期內透過中2022。

## <a name="unity-20212"></a>Unity 2021。2

如果您要試用早期的 **Unity 2021.2** 組建，請從 [**Mixed Reality OpenXR 外掛程式**](xr-project-setup.md?tabs=openxr)開始著手。 OpenXR 外掛程式是 unity 2021.2 和更新版本中混合現實開發的唯一途徑，因為支援 Windows XR 外掛程式的最終 unity 版本是 Unity 2021.1。

## <a name="unity-20184-lts"></a>Unity 2018.4 LTS

Unity 2018.4 LTS 已達到 Unity 的兩年 Long-Term 支援期間的結尾，但因為您的專案將會繼續執行，所以不會再接收來自 Unity 的更新。

如果您有 Unity 2018 專案，您應該考慮規劃向前遷移至 Unity 2020.3 LTS 和 Mixed Reality OpenXR 外掛程式。