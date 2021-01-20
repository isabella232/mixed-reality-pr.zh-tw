---
title: 使用 Unreal Insights 進行剖析
description: 瞭解如何在 HoloLens 2 上使用 Unreal 深入解析。
author: sajidfarooq
ms.author: v-hferrone
ms.date: 12/10/2020
ms.topic: article
keywords: Unreal、Unreal Engine 4、UE4、HoloLens、HoloLens 2、開發、分析、Unreal 見解、檔、指南、功能、全像投影、遊戲開發、混合現實耳機、windows mixed reality 耳機、虛擬實境耳機
ms.openlocfilehash: b41d36679adfb35b5cc3561b8d5e7734654e7fb5
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/20/2021
ms.locfileid: "98580833"
---
# <a name="profiling-with-unreal-insights"></a><span data-ttu-id="7665d-104">使用 Unreal Insights 進行剖析</span><span class="sxs-lookup"><span data-stu-id="7665d-104">Profiling with Unreal Insights</span></span> 

<span data-ttu-id="7665d-105">[Unreal Insights](https://docs.unrealengine.com/TestingAndOptimization/PerformanceAndProfiling/UnrealInsights/Overview/index.html) 是一種分析系統，可從 Unreal 引擎收集、分析及視覺化資料。</span><span class="sxs-lookup"><span data-stu-id="7665d-105">[Unreal Insights](https://docs.unrealengine.com/TestingAndOptimization/PerformanceAndProfiling/UnrealInsights/Overview/index.html) is a profiling system that collects, analyzes, and visualizes data from Unreal Engine.</span></span> <span data-ttu-id="7665d-106">程式碼剖析系統可協助您找出優化瓶頸和您的應用程式效能可能會提升的區域。</span><span class="sxs-lookup"><span data-stu-id="7665d-106">The profiling system can help you find optimization bottlenecks and areas where you apps performance could use a boost.</span></span> <span data-ttu-id="7665d-107">一般來說，您可以直接從編輯器啟用 Unreal Insights，但 HoloLens 2 您需要使用命令列。</span><span class="sxs-lookup"><span data-stu-id="7665d-107">Normally, you enable Unreal Insights right from the editor, but for HoloLens 2 you'll need to use the command line.</span></span>  

## <a name="setup"></a><span data-ttu-id="7665d-108">安裝程式</span><span class="sxs-lookup"><span data-stu-id="7665d-108">Setup</span></span>

<span data-ttu-id="7665d-109">Unreal 可讓您使用可啟用 Unreal Insights 的命令列參數，在 HoloLens 啟動器中建立及設定「自訂設定檔」。</span><span class="sxs-lookup"><span data-stu-id="7665d-109">Unreal lets you to create and configure a "Custom Profile" in the HoloLens launcher with the command line parameters that enable Unreal Insights.</span></span>

1.  <span data-ttu-id="7665d-110">在命令提示字元中，使用 **ipconfig** 命令尋找電腦的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="7665d-110">Find the IP address of your computer using the **ipconfig** command on the command prompt.</span></span> <span data-ttu-id="7665d-111">IP 位址是由 ipconfig 列出的 IPv4 位址。</span><span class="sxs-lookup"><span data-stu-id="7665d-111">The IP address is the IPv4 address listed by ipconfig.</span></span> <span data-ttu-id="7665d-112">當您稍後設定命令列參數時，請記住這一點。</span><span class="sxs-lookup"><span data-stu-id="7665d-112">Keep this in mind for later when you set Command Line Parameters.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7665d-113">如果您是在 VPN 後方，您可能必須改為提供透過 VPN 提供的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="7665d-113">If you're behind a VPN, you may need to provide the IP address provided via the VPN instead.</span></span>

![Ipconfig 命令的命令列結果螢幕擷取畫面](images/unreal-insights-img-01.png)

2.  <span data-ttu-id="7665d-115">移至 [Unreal 引擎] 面板的頂端，然後開啟 [**啟動**] 按鈕底下的 **裝置管理員**：</span><span class="sxs-lookup"><span data-stu-id="7665d-115">Go to the top of the Unreal Engine panel and open **Device Manager** under the **Launch** button:</span></span>

![已反白顯示裝置管理員的啟動選項螢幕擷取畫面](images/unreal-insights-img-02.png)

3.  <span data-ttu-id="7665d-117">在 [裝置管理員中，選取 [ **新增未列出的裝置**：</span><span class="sxs-lookup"><span data-stu-id="7665d-117">In the Device Manager, select **Add an Unlisted Device**:</span></span>

![在 Unreal 引擎中開啟的裝置管理員螢幕擷取畫面](images/unreal-insights-img-03.png)

4. <span data-ttu-id="7665d-119">按一下 [ **選取平臺** ]，然後選擇 [ **HoloLens**：</span><span class="sxs-lookup"><span data-stu-id="7665d-119">Click **Select a platform** and choose **HoloLens**:</span></span>

![[新增未列出裝置] 下拉式清單的螢幕擷取畫面，其中已醒目提示 HoloLens](images/unreal-insights-img-04.png)

5.  <span data-ttu-id="7665d-121">如果您使用的是 IPoverUSB，請輸入127.0.0.1：10080作為裝置識別碼。</span><span class="sxs-lookup"><span data-stu-id="7665d-121">If you're using IPoverUSB, enter 127.0.0.1:10080 as the Device Identifier.</span></span> <span data-ttu-id="7665d-122">在各自的欄位中輸入 HoloLens 使用者和密碼，並依您的需要填寫 **顯示名稱** 。</span><span class="sxs-lookup"><span data-stu-id="7665d-122">Enter your HoloLens user and password in their respective fields and fill **Display Name** as you wish.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7665d-123">裝置識別碼是 HoloLens 的 IP 位址，而不是執行您在步驟1中找到之 Unreal Insights 的電腦。</span><span class="sxs-lookup"><span data-stu-id="7665d-123">The Device Identifier is the IP address of the HoloLens, NOT of the computer running Unreal Insights you found in step 1.</span></span>

![裝置管理員中 HoloLens 裝置詳細資料的螢幕擷取畫面](images/unreal-insights-img-05.png)

6.  <span data-ttu-id="7665d-125">選取 [ **新增** ]，您的 HoloLens 應該會出現在 [裝置管理員] 的 [裝置] 清單中：</span><span class="sxs-lookup"><span data-stu-id="7665d-125">Select **Add** and your HoloLens should appear in the device list of the device manager:</span></span>

![已新增至裝置清單的 HoloLens 螢幕擷取畫面](images/unreal-insights-img-06.png)

## <a name="launch"></a><span data-ttu-id="7665d-127">啟動</span><span class="sxs-lookup"><span data-stu-id="7665d-127">Launch</span></span>

1. <span data-ttu-id="7665d-128">從 [**啟動**] 按鈕底下的 [UE4] 面板開啟 [**專案啟動** 程式]：</span><span class="sxs-lookup"><span data-stu-id="7665d-128">Open **Project Launcher** from the UE4 panel under the **Launch** button:</span></span>

![反白顯示專案啟動器的啟動選項螢幕擷取畫面](images/unreal-insights-img-07.png)

2. <span data-ttu-id="7665d-130">選取 **+** 按鈕，在 [ **自訂啟動設定檔**] 下建立自訂設定檔。</span><span class="sxs-lookup"><span data-stu-id="7665d-130">Select the **+** button to create a custom profile under **Custom Launch Profiles**.</span></span> <span data-ttu-id="7665d-131">一旦建立之後，您隨時都可以編輯此設定檔：</span><span class="sxs-lookup"><span data-stu-id="7665d-131">Once created, you can always edit this profile later:</span></span>

![醒目提示自訂啟動設定檔的專案啟動顯示專案螢幕擷取畫面](images/unreal-insights-img-08.png)

3. <span data-ttu-id="7665d-133">選取 HoloLens 自訂啟動設定檔上的 [ **編輯設定檔** ] 按鈕，並設定：</span><span class="sxs-lookup"><span data-stu-id="7665d-133">Select **edit profile** button on the HoloLens custom launch profile and configure:</span></span>
    * <span data-ttu-id="7665d-134">依書籍選取要啟用複製到裝置 **的 [** **庫**]</span><span class="sxs-lookup"><span data-stu-id="7665d-134">Select **Cook** to **By the Book** to enable copying to device</span></span>
    * <span data-ttu-id="7665d-135">您可能想要檢查 **是否** 要封存？在 [封存] **區段中** ，保留產生的 .appxbundle 而不是刪除來儲存磁碟空間。</span><span class="sxs-lookup"><span data-stu-id="7665d-135">You may want to check **Do you wish to archive?** in the **Archive** section to retain the generated .appxbundle rather than deleting to save disk space.</span></span> <span data-ttu-id="7665d-136">如果您想要的話，請指定 .appxbundle 的位置並切換至開發組建</span><span class="sxs-lookup"><span data-stu-id="7665d-136">Specify a location for the .appxbundle and switch to a development build if you wish</span></span>

![[設定檔] 中的 [使用] 選項的螢幕擷取畫面，其中已醒目提示書籍和 HoloLens](images/unreal-insights-img-09.png)

4. <span data-ttu-id="7665d-138">設定 **您想要如何部署組建？** 若要 **複製到裝置** ，以啟用 UI 的 **啟動** 區段：</span><span class="sxs-lookup"><span data-stu-id="7665d-138">Set **How would you like to deploy the build?** to **Copy to device** to activate the **Launch** section of the UI:</span></span>

![專案啟動程式的螢幕擷取畫面，其中已醒目提示 [複製到裝置] 的部署選項](images/unreal-insights-img-10.png)

5. <span data-ttu-id="7665d-140">在 **啟動** 區段中設定 **其他命令列參數**。</span><span class="sxs-lookup"><span data-stu-id="7665d-140">Set **Additional Command Line Parameters** in the **Launch** section.</span></span> <span data-ttu-id="7665d-141">這些參數將會寫入 ue4commandline.txt 檔案中，並封裝到套件組合，並在啟動時使用。</span><span class="sxs-lookup"><span data-stu-id="7665d-141">The parameters will be written into a ue4commandline.txt file, packaged into the bundle, and used at launch.</span></span> 
    <!-- TODO: Need more detail on what this parameter does and where to find others. -->
    * <span data-ttu-id="7665d-142">試試看這些初學者： **-tracehost = IP_OF_YOUR_PC-trace = Log、Bookmark、Frame、CPU、GPU、LoadTime、File、Net**</span><span class="sxs-lookup"><span data-stu-id="7665d-142">Try these for starters: **-tracehost=IP_OF_YOUR_PC -trace=Log,Bookmark,Frame,CPU,GPU,LoadTime,File,Net**</span></span>
    * <span data-ttu-id="7665d-143">您可以在 [Unreal Insights 參考檔](https://docs.unrealengine.com/TestingAndOptimization/PerformanceAndProfiling/UnrealInsights/Reference/index.html)中找到可用啟動參數的完整清單。</span><span class="sxs-lookup"><span data-stu-id="7665d-143">You can find a complete list of available launch parameters in the [Unreal Insights reference documentation](https://docs.unrealengine.com/TestingAndOptimization/PerformanceAndProfiling/UnrealInsights/Reference/index.html).</span></span>

> [!NOTE]
> <span data-ttu-id="7665d-144">「IP_OF_YOUR_PC」是我們在步驟1中找到的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="7665d-144">"IP_OF_YOUR_PC" is the IP address we found in step 1.</span></span> <span data-ttu-id="7665d-145">這是執行 Unreal Insights 之電腦的 IP 位址，而非 HoloLens 的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="7665d-145">This is the IP address of the computer running Unreal Insights, NOT the IP address of the HoloLens.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7665d-146">追蹤可能會非常快速地變得很大。</span><span class="sxs-lookup"><span data-stu-id="7665d-146">Traces can get large very quickly.</span></span> <span data-ttu-id="7665d-147">只啟用您需要的通道，讓追蹤大小保持在低。</span><span class="sxs-lookup"><span data-stu-id="7665d-147">Enable only those channels you need to keep trace size low.</span></span>

![啟動設定選項的螢幕擷取畫面](images/unreal-insights-img-11.png)

6. <span data-ttu-id="7665d-149">在應用程式啟動之前啟動 Unreal Insights，否則 Unreal Insights 將無法在應用程式之前適當地進行初始化：</span><span class="sxs-lookup"><span data-stu-id="7665d-149">Launch Unreal Insights BEFORE app launch, otherwise Unreal Insights wont be able to initialize appropriately before the app:</span></span>
    * <span data-ttu-id="7665d-150">Unreal Insights 可執行檔會儲存在二進位檔引擎資料夾中，通常如下所示： "C:\Program Files\Epic Games\UE_4.26\Engine\Binaries\Win64\UnrealInsights.exe"</span><span class="sxs-lookup"><span data-stu-id="7665d-150">The Unreal Insights executable is stored in the binaries engine folder, usually as follows: "C:\Program Files\Epic Games\UE_4.26\Engine\Binaries\Win64\UnrealInsights.exe"</span></span>

![Unreal insights 可執行檔執行的螢幕擷取畫面](images/unreal-insights-img-12.png)

6.  <span data-ttu-id="7665d-152">選取 [ **上一步** ] 返回 **專案啟動** 程式對話方塊的根目錄</span><span class="sxs-lookup"><span data-stu-id="7665d-152">Select **Back** to return to the root of the **Project Launcher** dialog</span></span>
7.  <span data-ttu-id="7665d-153">回到編輯器，按一下您自訂啟動設定檔上的 [ **啟動** ]</span><span class="sxs-lookup"><span data-stu-id="7665d-153">Back in the editor, Click **Launch** on your custom launch profile</span></span>

![自訂啟動設定檔的螢幕擷取畫面](images/unreal-insights-img-13.png)

8.  <span data-ttu-id="7665d-155">當您的專案封裝、安裝在您的裝置上，並啟動時監看</span><span class="sxs-lookup"><span data-stu-id="7665d-155">Watch as your project is packaged up, installed on your device, and launched</span></span>

## <a name="profiling"></a><span data-ttu-id="7665d-156">程式碼剖析</span><span class="sxs-lookup"><span data-stu-id="7665d-156">Profiling</span></span>

<span data-ttu-id="7665d-157">回到 Unreal Insights，選取您裝置的 **即時** 連線以開始分析</span><span class="sxs-lookup"><span data-stu-id="7665d-157">Back in Unreal Insights, select the **Live** connection to your device to start profiling</span></span>

<span data-ttu-id="7665d-158">自訂設定檔會在專案之間共用。</span><span class="sxs-lookup"><span data-stu-id="7665d-158">The custom profile is shared between projects.</span></span> <span data-ttu-id="7665d-159">從這裡開始，您可以使用您所建立的自訂設定檔，而不需要每次都執行此動作。</span><span class="sxs-lookup"><span data-stu-id="7665d-159">From here on out, you can use the custom profile you created instead of having to do this every time.</span></span> <span data-ttu-id="7665d-160">每次開始 Unreal 時，您只需要重新建立與裝置的連線，並在 [安裝區段](#setup)中執行步驟3到6。</span><span class="sxs-lookup"><span data-stu-id="7665d-160">You only need to recreate the connection to the device every time you start Unreal with steps 3 to 6 in the [setup section](#setup).</span></span>

## <a name="see-also"></a><span data-ttu-id="7665d-161">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7665d-161">See also</span></span>
* [<span data-ttu-id="7665d-162">Unreal Insights 檔</span><span class="sxs-lookup"><span data-stu-id="7665d-162">Unreal Insights documentation</span></span>](https://docs.unrealengine.com/TestingAndOptimization/PerformanceAndProfiling/UnrealInsights/index.html)

