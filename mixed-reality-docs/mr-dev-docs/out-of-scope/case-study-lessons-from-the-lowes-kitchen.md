---
title: 案例研究-Lowe 廚房的課程
description: HoloLens 團隊想要分享衍生自 Lowe HoloLens 專案的一些最佳作法。
author: brandonbray
ms.author: kevincol
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality、Lowe、HoloLens、廚房、個案研究
ms.openlocfilehash: a6bd7a09f77fb71dc23dc640525ff250abac8f12
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2020
ms.locfileid: "91681140"
---
# <a name="case-study---lessons-from-the-lowes-kitchen"></a>案例研究-Lowe 廚房的課程

HoloLens 團隊想要分享衍生自 Lowe HoloLens 專案的一些最佳作法。 以下是 Lowe 的 HoloLens 投射影片，其示範于 Satya 的 2016 Ignite 專題演講。
<br>
>[!VIDEO https://www.youtube.com/embed/gC_4JxF0e_k]

## <a name="lowes-hololens-best-practices"></a>Lowe 的 HoloLens 最佳作法

這兩段影片涵蓋的最佳作法是衍生自2016年4月起，已在兩個 Lowe 存放區中的 Lowe HoloLens 試驗。 重要主題如下：
* 將行動裝置的效能最大化
* 使用全像全像全像全像全像全像的框架來建立 UX 方法)  (
* 精確度對齊 (第二個交談) 
* 共用的全像攝影體驗 (第二談) 
* 與客戶互動 (第二談) 

## <a name="video-1"></a>影片1

**將行動裝置的效能最大化** HoloLens 是在裝置上進行所有處理的非網路共用裝置。 這需要行動平臺，而且需要類似于建立行動應用程式的思維。 Microsoft 建議您的 HoloLens 應用程式維護60FPS，以為您的使用者提供美味體驗。 具有低 FPS 可能會導致不穩定的全像影像。

在 HoloLens 上進行開發時，您可以查看的一些最重要的事項是資產優化/減去，使用 [HoloLens 工具](https://github.com/Microsoft/HoloToolkit-Unity) 組) 免費提供的自訂著色器 (。 另一個重要的考慮是從專案的最開頭測量畫面播放速率。 根據專案而定，顯示資產的順序也可能是很大的參與者
<br>
>[!VIDEO https://www.youtube.com/embed/o0QIPwgiP9A]

## <a name="video-2"></a>影片2

**使用全像全像全像全像的框架** 請務必瞭解在實體世界中放置全息的位置。 有了 Lowe，我們會討論不同的 UX 方法，以協助使用者在看起來更大的全像投影環境時，能更貼近使用者體驗。

有效 **位數對齊** 在 Lowe 的案例中，最重要的是要讓全像是在實體廚房之間精確地對齊全像投影。 我們討論的技術可協助確保說服使用者實體環境已變更的體驗。

**共用** 的全像攝影體驗結合是使用 Lowe 經驗的主要方式。 一個人可以變更檯面，另一個人會看到變更。 我們稱之為「共用體驗」。

**與客戶互動** Lowe 的設計人員不是使用 HoloLens，但需要查看客戶看到的內容。 我們會示範如何抓住客戶在 UWP 應用程式上看到的內容。
<br>
>[!VIDEO https://www.youtube.com/embed/LceMdyKZ4PI]
