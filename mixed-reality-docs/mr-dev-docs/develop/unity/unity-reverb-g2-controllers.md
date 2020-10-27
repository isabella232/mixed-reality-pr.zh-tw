---
title: Unity 中的 HP 回音 G2 控制器
description: 使用 SteamVR 和 Windows Mixed Reality 中的 HP 回音 G2 控制器的指示。
author: hferrone
ms.author: v-hferrone
ms.date: 10/14/2020
ms.topic: article
keywords: Unity、回音、回音、HP 回音、mixed reality、開發、移動控制器、使用者輸入、功能、新專案、模擬器、檔、指南、功能、全像遊戲開發
ms.openlocfilehash: 3add2ae52fbaba087da257212e1d8ddfdffe702a
ms.sourcegitcommit: 4bb5544a0c74ac4e9766bab3401c9b30ee170a71
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2020
ms.locfileid: "92638385"
---
# <a name="hp-reverb-g2-controllers-in-unity"></a>Unity 中的 HP 回音 G2 控制器

## <a name="getting-started"></a>開始使用

如果您正在針對 SteamVR 進行開發，或使用 Windows Mixed Reality 輸入 API (XR，則不需要額外的設定，就能使用「HP 回音」 G2 控制器。Wsa。輸入) 。 不過，除非您使用 SteamVR，否則無法透過輸入管理員存取 A、B、X、Y 按鈕和擠壓觸發程式。 在不久的將來，將可支援額外的「回音」 G2 輸入，因此請務必回來查看！

## <a name="porting-existing-applications"></a>移植現有的應用程式

如果您已經有正在為 Windows Mixed Reality 沉浸式耳機開發的現有應用程式，請參閱我們的 [移植指南](../porting-apps/porting-guides.md) 和 [專案設定](https://docs.microsoft.com/windows/mixed-reality/develop/porting-apps/porting-guides?tabs=project#unity-porting-guidance) 章節，以取得一般建議。

## <a name="mapping-input"></a>對應輸入

當您準備好要讓新控制器啟動並執行輸入對應時，請從「沉浸式移植指南」的 [ [輸入對應](https://docs.microsoft.com/windows/mixed-reality/develop/porting-apps/porting-guides?tabs=input#unity-porting-guidance) ] 區段開始。 [筆勢和移動控制器](gestures-and-motion-controllers-in-unity.md)會詳細說明如何在 Unity 中設定輸入的指示，以及用於參考的完整[按鈕和軸對應表](gestures-and-motion-controllers-in-unity.md#using-hp-reverb-g2-controllers)。

## <a name="see-also"></a>請參閱
* [更新 SteamVR](../porting-apps/updating-your-steamvr-application-for-windows-mixed-reality.md)