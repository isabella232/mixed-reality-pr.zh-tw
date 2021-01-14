---
title: Unreal 的效能建議
description: 了解如何使用我們建議的 Unreal 專案設定，讓混合實境應用程式發揮最佳效能。
author: hferrone
ms.author: v-hferrone
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 混合實境, 效能, 最佳化, 設定, 文件
ms.openlocfilehash: a1a8dacd0206882c7ebd67b2658fa2e6300aa66a
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009818"
---
# <a name="performance-recommendations-for-unreal"></a>Unreal 的效能建議

Unreal Engine 有幾項可提高應用程式效能的功能，全部都是以[混合實境效能建議](../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md)中的討論為基礎。 建議您先閱讀應用程式瓶頸、分析和剖析混合實境應用程式，並進行一般效能修正，再繼續進行。

## <a name="recommended-unreal-project-settings"></a>建議的 Unreal 專案設定

您可以在 [編輯] > [專案設定] 中找到下列每個設定。

1. 使用行動 VR 轉譯器：
    * 向下捲動至 [專案] 區段、選取 [目標硬體]，然後將目標平台設定為 [行動裝置/平板電腦]

![行動目標設定](images/unreal/performance-recommendations-img-01.png)

2. 使用前向轉譯器： 
    * 前向轉譯器可個別關閉的功能較多，因此在混合實境中的適用性遠優於預設的延遲轉譯管線。 
    * 您可以在 [Unreal 的文件](https://docs.unrealengine.com/Platforms/VR/DevelopVR/VRPerformance/index.html)中找到詳細資訊。

![前向轉譯](images/unreal/performance-recommendations-img-04.png)

3. 使用行動多重檢視：
    * 向下捲動至 [引擎] 區段、選取 [轉譯]、展開 [VR] 區段，然後同時啟用 [執行個體化立體聲] 和 [行動多重檢視]。 應取消核取行動設備 HDR。

![VR 轉譯設定](images/unreal/performance-recommendations-img-03.png)

4. **[僅 OpenXR]** 確保 [預設] 或 [D3D12] 是選取的 [預設 RHI]：
    * 選取 **D3D11** 會對效能造成負面影響，因為平台會執行額外的轉譯行程。 除了避免額外的轉譯行程，**D3D12** 應提供轉譯效能改善。

![預設 RHI](images/unreal/performance-recommendations-img-09.png)

5. 停用頂點霧化： 
    * 頂點霧化會在多邊形的每個頂點套用霧計算，然後在多邊形的整個表面上插補結果。 如果您的遊戲未使用霧，建議您停用頂點霧化以提高陰影效能。

![頂點霧化選項](images/unreal/performance-recommendations-img-05.png)

6. 停用遮蔽消除：
    * 向下捲動至 [引擎] 區段、選取 [轉譯]、展開 [消除] 區段，然後取消勾選 [遮蔽消除]。
        + 如果您需要針對轉譯的詳細場景進行遮蔽消除，建議您在 [引擎] > [轉譯] 中啟用 [支援軟體遮蔽消除]。 Unreal 將在 CPU 上執行此工作，並避免 GPU 的遮蔽查詢 (此功能在 HoloLens 2 上的執行效能不佳)。
    * 在行動裝置上，對 GPU 消除遮蔽的速度很慢。 一般來說，您會希望 GPU 主要用在轉譯上。 如果您覺得遮蔽有助於效能，請試著改為啟用軟體遮蔽。 

> [!NOTE]
> 如果您的 CPU 已受限於大量的繪製呼叫，啟用軟體遮蔽可能會使效能變差。

![停用遮蔽消除](images/unreal/performance-recommendations-img-02.png)

7. 停用自訂深度樣板傳遞：
    * 停用自訂深度樣板需要額外的傳遞，這表示速度會很慢。 透明度在 Unreal 上的執行速度也很慢。 您可以在 [Unreal 的文件](https://docs.unrealengine.com/Engine/Performance/Guidelines/index.html)中找到詳細資訊。

![深度樣板](images/unreal/performance-recommendations-img-06.png)

8. 減少重疊的陰影圖： 
    * 減少陰影圖的數目將可改善效能。 一般而言，若沒有可見的品質損失，則應將屬性設定為 1。 

![重疊的陰影圖](images/unreal/performance-recommendations-img-07.png)

## <a name="optional-settings"></a>選擇性設定

> [!NOTE]
> 下列設定可能會改善效能，但代價是某些功能須停用。 只有在您確定不需要這類功能時，才可使用這些設定。

1. 減少行動著色器排列
    * 如果您的燈光不會脫離相機獨立移動，則可以安全地將屬性值設定為 0。 其主要的優點是可以讓 Unreal 消除數個著色器排列，加快著色器編譯速度。

![減少行動著色器排列](images/unreal/performance-recommendations-img-08.png)

## <a name="see-also"></a>另請參閱

* [Unreal Engine 行動效能指導方針]( https://docs.unrealengine.com/Platforms/Mobile/Performance/index.html)