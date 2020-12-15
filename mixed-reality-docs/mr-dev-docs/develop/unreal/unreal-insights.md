---
title: 使用 Unreal Insights 進行程式碼剖析
description: 瞭解如何在 HoloLens 2 上使用 Unreal 深入解析。
author: sajidfarooq
ms.author: v-hferrone
ms.date: 12/10/2020
ms.topic: article
keywords: Unreal、Unreal Engine 4、UE4、HoloLens、HoloLens 2、開發、分析、Unreal 見解、檔、指南、功能、全像投影、遊戲開發、混合現實耳機、windows mixed reality 耳機、虛擬實境耳機
ms.openlocfilehash: 20e620f147f2cf5ee05073467c8ce7335340d59d
ms.sourcegitcommit: 53bde413a174712cb9d3794d02d96363a2d599cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/14/2020
ms.locfileid: "97486339"
---
# <a name="profiling-with-unreal-insights"></a>使用 Unreal Insights 進行程式碼剖析 

[Unreal Insights](https://docs.unrealengine.com/TestingAndOptimization/PerformanceAndProfiling/UnrealInsights/Overview/index.html) 是一種分析系統，可從 Unreal 引擎收集、分析及視覺化資料。 程式碼剖析系統可協助您找出優化瓶頸和您的應用程式效能可能會提升的區域。 一般來說，您可以直接從編輯器啟用 Unreal Insights，但 HoloLens 2 您需要使用命令列。  

## <a name="setup"></a>安裝程式

Unreal 可讓您使用可啟用 Unreal Insights 的命令列參數，在 HoloLens 啟動器中建立及設定「自訂設定檔」。

1.  在命令提示字元中，使用 **ipconfig** 命令尋找電腦的 IP 位址。 IP 位址是由 ipconfig 列出的 IPv4 位址。 當您稍後設定命令列參數時，請記住這一點。

> [!IMPORTANT]
> 如果您是在 VPN 後方，您可能必須改為提供透過 VPN 提供的 IP 位址。

![Ipconfig 命令的命令列結果螢幕擷取畫面](images/unreal-insights-img-01.png)

2.  移至 [Unreal 引擎] 面板的頂端，然後開啟 [**啟動**] 按鈕底下的 **裝置管理員**：

![已反白顯示裝置管理員的啟動選項螢幕擷取畫面](images/unreal-insights-img-02.png)

3.  在 [裝置管理員中，選取 [ **新增未列出的裝置**：

![在 Unreal 引擎中開啟的裝置管理員螢幕擷取畫面](images/unreal-insights-img-03.png)

4. 按一下 [ **選取平臺** ]，然後選擇 [ **HoloLens**：

![[新增未列出裝置] 下拉式清單的螢幕擷取畫面，其中已醒目提示 HoloLens](images/unreal-insights-img-04.png)

5.  如果您使用的是 IPoverUSB，請輸入127.0.0.1：10080作為裝置識別碼。 在各自的欄位中輸入 HoloLens 使用者和密碼，並依您的需要填寫 **顯示名稱** 。

> [!IMPORTANT]
> 裝置識別碼是 HoloLens 的 IP 位址，而不是執行您在步驟1中找到之 Unreal Insights 的電腦。

![裝置管理員中 HoloLens 裝置詳細資料的螢幕擷取畫面](images/unreal-insights-img-05.png)

6.  選取 [ **新增** ]，您的 HoloLens 應該會出現在 [裝置管理員] 的 [裝置] 清單中：

![已新增至裝置清單的 HoloLens 螢幕擷取畫面](images/unreal-insights-img-06.png)

## <a name="launch"></a>啟動

1. 從 [**啟動**] 按鈕底下的 [UE4] 面板開啟 [**專案啟動** 程式]：

![反白顯示專案啟動器的啟動選項螢幕擷取畫面](images/unreal-insights-img-07.png)

2. 選取 **+** 按鈕，在 [ **自訂啟動設定檔**] 下建立自訂設定檔。 一旦建立之後，您隨時都可以編輯此設定檔：

![醒目提示自訂啟動設定檔的專案啟動顯示專案螢幕擷取畫面](images/unreal-insights-img-08.png)

3. 選取 HoloLens 自訂啟動設定檔上的 [ **編輯設定檔** ] 按鈕，並設定：
    * 依書籍選取要啟用複製到裝置 **的 [** **庫**]
    * 您可能想要檢查 **是否** 要封存？在 [封存] **區段中** ，保留產生的 .appxbundle 而不是刪除來儲存磁碟空間。 如果您想要的話，請指定 .appxbundle 的位置並切換至開發組建

![[設定檔] 中的 [使用] 選項的螢幕擷取畫面，其中已醒目提示書籍和 HoloLens](images/unreal-insights-img-09.png)

4. 設定 **您想要如何部署組建？** 若要 **複製到裝置** ，以啟用 UI 的 **啟動** 區段：

![專案啟動程式的螢幕擷取畫面，其中已醒目提示 [複製到裝置] 的部署選項](images/unreal-insights-img-10.png)

5. 在 **啟動** 區段中設定 **其他命令列參數**。 這些參數將會寫入 ue4commandline.txt 檔案中，並封裝到套件組合，並在啟動時使用。 
    <!-- TODO: Need more detail on what this parameter does and where to find others. -->
    * 試試看這些初學者： **-tracehost = IP_OF_YOUR_PC-trace = Log、Bookmark、Frame、CPU、GPU、LoadTime、File、Net**
    * 您可以在 [Unreal Insights 參考檔](https://docs.unrealengine.com/TestingAndOptimization/PerformanceAndProfiling/UnrealInsights/Reference/index.html)中找到可用啟動參數的完整清單。

> [!NOTE]
> 「IP_OF_YOUR_PC」是我們在步驟1中找到的 IP 位址。 這是執行 Unreal Insights 之電腦的 IP 位址，而非 HoloLens 的 IP 位址。

> [!IMPORTANT]
> 追蹤可能會非常快速地變得很大。 只啟用您需要的通道，讓追蹤大小保持在低。

![啟動設定選項的螢幕擷取畫面](images/unreal-insights-img-11.png)

6. 在應用程式啟動之前啟動 Unreal Insights，否則 Unreal Insights 將無法在應用程式之前適當地進行初始化：
    * Unreal Insights 可執行檔會儲存在二進位檔引擎資料夾中，通常如下所示： "C:\Program Files\Epic Games\UE_4.26\Engine\Binaries\Win64\UnrealInsights.exe"

![Unreal insights 可執行檔執行的螢幕擷取畫面](images/unreal-insights-img-12.png)

6.  選取 [ **上一步** ] 返回 **專案啟動** 程式對話方塊的根目錄
7.  回到編輯器，按一下您自訂啟動設定檔上的 [ **啟動** ]

![自訂啟動設定檔的螢幕擷取畫面](images/unreal-insights-img-13.png)

8.  當您的專案封裝、安裝在您的裝置上，並啟動時監看

## <a name="profiling"></a>程式碼剖析

回到 Unreal Insights，選取您裝置的 **即時** 連線以開始分析

自訂設定檔會在專案之間共用。 從這裡開始，您可以使用您所建立的自訂設定檔，而不需要每次都執行此動作。 每次開始 Unreal 時，您只需要重新建立與裝置的連線，並在 [安裝區段](#setup)中執行步驟3到6。

## <a name="see-also"></a>另請參閱
* [Unreal Insights 檔](https://docs.unrealengine.com/TestingAndOptimization/PerformanceAndProfiling/UnrealInsights/index.html)

