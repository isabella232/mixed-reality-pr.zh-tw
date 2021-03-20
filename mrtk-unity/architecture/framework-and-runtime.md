---
title: 架構和執行時間
description: MRTK 中的架構和執行時間相關資訊。
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、
ms.openlocfilehash: 27247a6a6bf8cbe89417a794217da34fcf5e5e34
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104701894"
---
# <a name="framework-and-runtime"></a>架構和執行時間

## <a name="changes-to-the-scene"></a>場景的變更

若要使用工具組，MixedRealityToolkit 腳本的實例必須在場景中。
若要加入一個，請使用功能表選項：混合現實工具組-> 新增至場景並進行設定。 此實例負責註冊、更新及中斷服務。 它也是您選擇設定設定檔的位置。

除了將 MRTK GameObject 新增至場景之外，功能表選項也會：

- 新增許多其他 MRTK 元件所使用的 MixedRealityPlayspace，以因應全球和區域空間轉換的原因。
- 移動主要攝影機作為 MixedRealityPlayspace (的子系，也將一些輸入和注視相關的腳本新增至主要攝影機，以協助 UnityUI 和注視相關的輸入功能) 。

## <a name="mixedrealitytoolkit-object-and-runtime"></a>MixedRealityToolkit 物件和執行時間

MRTK 有數個核心服務。 彼此之間的座標;其他則是獨立的。
全都共用相同的生命週期，也就是啟動、註冊、更新和終止，而這種生命週期與 Unity 的 MonoBehaviour 生命週期分開。 這段 [媒體文章](https://medium.com/@stephen_hodgson/the-mixed-reality-framework-6fdb5c11feb2) 會說明這種方法背後的一些背景和動機。 MRTK 具有單一物件，可管理其服務的生命週期和執行時間。

此實體可確保：

- 當遊戲開始時，會以預先定義的順序進行服務的探索和初始化。
- 它提供一種機制，讓服務自行註冊 (也就是「我支援此服務！」) 和其他呼叫者取得這些服務的保留。
- 它會提供更新 () /LateUpdate () 呼叫，然後將它們轉送至各種服務 (例如 via UpdateAllServices/LateUpdateAllServices) 。
