---
title: 使用 Unreal Insights 進行剖析
description: 瞭解如何在 HoloLens 2 上使用 Unreal Insights。
author: sajidfarooq
ms.author: v-hferrone
ms.date: 12/10/2020
ms.topic: article
keywords: Unreal、Unreal Engine 4、UE4、HoloLens、HoloLens 2、開發、分析、Unreal 見解、檔、指南、功能、全像投影、遊戲開發、混合現實耳機、windows mixed reality 耳機、虛擬實境耳機
ms.openlocfilehash: a77d7795cd7e8c281ebaa2ef89bb6bc9152f5f9c
ms.sourcegitcommit: 5d13ff165f4d08a3b028935fb39539a45a30f7e8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2021
ms.locfileid: "127779367"
---
# <a name="profiling-with-unreal-insights"></a>使用 Unreal Insights 進行剖析

[Unreal Insights](https://docs.unrealengine.com/TestingAndOptimization/PerformanceAndProfiling/UnrealInsights/Overview/index.html)是一種分析系統，可從 Unreal 引擎收集、分析及視覺化資料。 程式碼剖析系統可協助您找出優化瓶頸和您的應用程式效能可能會提升的區域。 一般來說，您可以直接從編輯器啟用 Unreal Insights，但針對 HoloLens 2，您必須使用命令列。

## <a name="setup"></a>安裝程式

Unreal 可讓您使用啟用 Unreal Insights 的命令列參數，在 HoloLens 啟動器中建立及設定「自訂設定檔」。

1. 在命令提示字元中，使用 **ipconfig** 命令尋找電腦的 IP 位址。 IP 位址是由 ipconfig 列出的 IPv4 位址。 當您稍後設定命令列參數時，請記住這一點。

> [!IMPORTANT]
> 如果您是在 VPN 後方，您可能必須改為提供透過 VPN 提供的 IP 位址。

![Ipconfig 命令的命令列結果螢幕擷取畫面](images/unreal-insights-img-01.png)

2. 從主編輯器視窗中的 [編輯] 工具列開啟 **Project 設定**。

![醒目提示 Project 設定的 [編輯] 下拉式清單的螢幕擷取畫面](images/unreal-insights-img-15.png)

3. 在左面板中向下移動，直到您找到 [**平臺**] 標頭，然後選取 [ **HoloLens**]。

![[Project 設定左面板中的 [平臺] 區段的螢幕擷取畫面，其中 HoloLens 反白顯示](images/unreal-insights-img-15.png)

4. 確認 [ **功能** ] 區段已選取 [網際網路用戶端]、[網際網路用戶端伺服器] 和 [私人網路用戶端伺服器]。

![已選取網際網路用戶端、網際網路用戶端伺服器和私人網路用戶端伺服器的功能選項螢幕擷取畫面](images/unreal-insights-img-14.png)

## <a name="launch"></a>啟動

1. 從 [**啟動**] 按鈕底下的 [UE4] 面板開啟 **Project Launcher** ：

![反白顯示專案啟動器的啟動選項螢幕擷取畫面](images/unreal-insights-img-07.png)

2. 選取 **+** 按鈕，在 [ **自訂啟動設定檔**] 下建立自訂設定檔。 一旦建立之後，您隨時都可以編輯此設定檔：

![醒目提示自訂啟動設定檔的專案啟動顯示專案螢幕擷取畫面](images/unreal-insights-img-08.png)

3. 選取 HoloLens 自訂啟動設定檔上的 [**編輯設定檔**] 按鈕。 在 [ **組建** ] 區段中，檢查 [ **組建 UAT** ] 並設定 **其他命令列參數**。
   - 試試看這些初學者： **-tracehost = IP_OF_YOUR_PC-trace = Log、Bookmark、Frame、CPU、GPU、LoadTime、File、Net**
   - 您可以在[Unreal Insights 參考檔](https://docs.unrealengine.com/TestingAndOptimization/PerformanceAndProfiling/UnrealInsights/Reference/index.html)中找到可用啟動參數的完整清單。

> [!NOTE]
> 「IP_OF_YOUR_PC」是我們在步驟1中找到的 IP 位址。 這是執行 Unreal Insights 電腦的 ip 位址，而不是 HoloLens 的 ip 位址。

> [!IMPORTANT]
> 追蹤可能會非常快速地變得很大。 只啟用您需要的通道，讓追蹤大小保持在低。

![設定檔設定中的組建選項螢幕擷取畫面](images/unreal-insights-img-17.png)

4. 請選取 **書籍的 [擁有者**]，以啟用複製到裝置。  請確定已在 **處理後地圖** 中選取您的地圖。

![書籍的設定檔設定中的 [使用] 選項的螢幕擷取畫面，並反白顯示 HoloLens](images/unreal-insights-img-09.png)

5. 設定 **您要如何將組建封裝** 至 **本機封裝 & 存放區**。 請注意您所選擇的檔案路徑，因為您稍後將會用到。

![設定檔設定中套件選項設定為 [封裝並儲存于本機] 的螢幕擷取畫面](images/unreal-insights-img-18.png)

6. 設定 **您要如何部署組建？** **不要部署**。

![螢幕擷取畫面：設定檔設定中部署設定為 [不要部署] 的部署選項](images/unreal-insights-img-19.png)

8. 選取 [**上一步**] 返回 **Project Launcher** 對話方塊的根目錄
9. 回到編輯器，按一下您自訂啟動設定檔上的 [ **啟動** ]

![自訂啟動設定檔的螢幕擷取畫面](images/unreal-insights-img-13.png)

10. 在建立專案時監看，然後透過裝置入口網站，將第5個步驟) 的套件路徑中的 .appxbundle (部署到您的 HoloLens

11. 啟動 Unreal Insights。 Unreal Insights 可執行檔會儲存在二進位檔引擎資料夾中，通常如下所示： "C:\Program Files\Epic Games\UE_4.26\Engine\Binaries\Win64\UnrealInsights.exe"

![Unreal insights 可執行檔執行的螢幕擷取畫面](images/unreal-insights-img-12.png)

12. 在您的 HoloLens 上啟動應用程式。

## <a name="profiling"></a>程式碼剖析

回到 Unreal Insights 中，選取裝置的 **即時** 連線以開始分析

自訂設定檔會在專案之間共用。 從這裡開始，您可以使用您所建立的自訂設定檔，而不需要每次都執行此動作。 每次開始 Unreal 時，您只需要重新建立與裝置的連線，並在 [安裝區段](#setup)中執行步驟3到6。

## <a name="see-also"></a>另請參閱

- [Unreal Insights 檔](https://docs.unrealengine.com/TestingAndOptimization/PerformanceAndProfiling/UnrealInsights/index.html)
