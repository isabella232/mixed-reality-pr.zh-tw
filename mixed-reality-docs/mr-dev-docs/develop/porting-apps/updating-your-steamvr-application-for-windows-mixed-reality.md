---
title: 更新您的 SteamVR 應用程式
description: 更新 SteamVR 應用程式，以充分利用 Windows Mixed Reality 耳機進行相容性的最佳做法。
author: thmignon
ms.author: thmignon
ms.date: 03/21/2018
ms.topic: article
keywords: SteamVR、相容性、移植、HoloLens 第1代、混合現實耳機、windows mixed reality 耳機、遷移、Windows 10、串流、移動控制器、haptics
ms.openlocfilehash: be510203b928cc1871b505d184e1aba05ec99abc
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2020
ms.locfileid: "94677657"
---
# <a name="updating-your-steamvr-application"></a>更新您的 SteamVR 應用程式
我們鼓勵開發人員測試 SteamVR 體驗，並將其優化，以在 Windows Mixed Reality 耳機上執行。 本檔涵蓋開發人員可進行的一般改進，以確保他們的體驗在 Windows Mixed Reality 上執行得很棒。

## <a name="initial-setup-instructions"></a>初始安裝指示

若要開始在 Windows Mixed Reality 上測試您的遊戲或應用程式，請務必先遵循我們的 [快速入門手冊。](https://aka.ms/WindowsMixedRealitySteamVR)

## <a name="controller-models"></a>控制器模型
1. 如果您的應用程式呈現控制器模型：
    * 使用 [Windows Mixed Reality 運動控制器模型](../../design/motion-controllers.md#rendering-the-motion-controller-model)
    * 使用 IVRRenderModel：： GetComponentState 來取得元件部分的本機轉換 (例如 指標姿勢) 
2. 具有 handedness 概念的體驗應從輸入 Api 取得提示，以區分控制器 [ (Unity 範例) ](../unity/gestures-and-motion-controllers-in-unity.md#unity-buttonaxis-mapping-table)

## <a name="controls"></a>控制項

設計或調整控制項版面配置時，請記住下列保留的命令集：
1. 按一下向下 **和向右類比操縱杆** 會保留給 **流儀表板**。

> [!NOTE]
> 如果您使用的是「HP 回音」 G2 控制器，則按一下右邊的功能表按鈕會保留給「 **流」儀表板**。

2. **Windows 按鈕** 一律會將使用者傳回到 Windows Mixed Reality 首頁。

可能的話，預設為以 thumb 為基礎的遙傳，以符合 [Windows Mixed Reality home](../../discover/navigating-the-windows-mixed-reality-home.md#getting-around-your-home) 遙傳行為

## <a name="tooltips-and-ui"></a>工具提示和 UI

許多的 VR 遊戲都利用移動控制器工具提示和覆迭，來告訴使用者他們的遊戲或應用程式最重要的命令。 當您調整應用程式的 Windows Mixed reality 時，建議您複習這部分的體驗，以確定工具提示會對應到 Windows 控制器模型。

此外，如果您的體驗中有任何點顯示控制器影像，請務必使用 Windows Mixed Reality 的動作控制器來提供更新的影像。

## <a name="haptics"></a>Haptics

從 [Windows 10 2018 年4月更新](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/release-notes-april-2018)開始，現在支援在 Windows Mixed Reality 上使用 Haptics 的 SteamVR 體驗。 如果您的 SteamVR 應用程式或遊戲已包含對 haptics 的支援，現在應該就能 (與 Windows Mixed Reality 的 [動作控制器](../../design/motion-controllers.md)沒有額外的工作) 。

Windows Mixed Reality 移動控制器使用標準 haptics 馬達，而不是在其他某些 SteamVR 運動控制器中找到的線性傳動器，這可能會導致與預期的使用者體驗稍微不同。 因此，我們建議您使用 Windows Mixed Reality 的動作控制器來測試及調整您的 haptics 設計。 例如，有時候短 haptic 脈衝 (5-10 ms) 在 Windows Mixed Reality 的移動控制器上比較不明顯。 若要產生更顯著的脈衝，請試著傳送較長的「按一下」 (40 70ms) ，讓馬達更多時間啟動，然後再被告知電源關閉。

## <a name="launching-steamvr-apps-from-windows-mixed-reality-start-menu"></a>從 Windows Mixed Reality [開始] 功能表啟動 SteamVR 應用程式

針對透過串流散發的 VR 體驗，我們已 [更新 SteamVR Beta 的 Windows Mixed Reality](https://steamcommunity.com/games/719950/announcements/detail/1687045485866139800) ，以及最新的 [Windows 測試人員](https://insider.windows.com) RS5 航班，讓 SteamVR 標題現在會自動顯示在 [所有應用程式] 清單的 Windows Mixed Reality [開始] 功能表中。 安裝這些軟體版本之後，您的客戶現在可以直接從 Windows Mixed Reality 首頁內啟動 SteamVR 標題，而不需要移除其耳機。

## <a name="windows-mixed-reality-logo"></a>Windows Mixed Reality 標誌

若要顯示標題的 Windows Mixed Reality 支援，請移至應用程式登陸頁面上的 [編輯存放區] 頁面，按一下 [基本資訊] 索引標籤，並向下移至 [虛擬實境]。 取消核取 [隱藏 Windows Mixed Reality]，然後發佈至存放區。

## <a name="bugs-and-feedback"></a>Bug 和意見反應

在改善 Windows Mixed Reality SteamVR 體驗時，您的意見反應非常寶貴。 請透過 [Windows 意見反應中樞](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/filing-feedback)提交所有意見反應和 bug。 以下是一些有關 [如何讓您的 SteamVR 意見反應更有説明的秘訣](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/using-steamvr-with-windows-mixed-reality#sharing-feedback-on-steamvr)。

如果您有任何問題或意見可以共用，您也可以在我們的串流 [論壇](https://steamcommunity.com/app/719950/discussions/)上聯繫我們。

## <a name="faqs-and-troubleshooting"></a>常見問題和疑難排解

如果您遇到設定或播放體驗的一般問題，請 [參閱最新的疑難排解步驟](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#steamvr)。

## <a name="see-also"></a>另請參閱
* [安裝工具](../install-the-tools.md)
* [耳機和移動控制器驅動程式歷程記錄](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/mixed-reality-software)
* [Windows Mixed Reality 最小電腦硬體相容性指導方針](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)
