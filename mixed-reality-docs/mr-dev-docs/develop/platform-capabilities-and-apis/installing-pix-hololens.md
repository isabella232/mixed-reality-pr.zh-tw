---
title: 安裝適用于 HoloLens 2 的 PIX
description: 瞭解如何安裝適用于 HoloLens 2 裝置的 PIX。
author: hferrone
ms.author: flbagar
ms.date: 12/02/2020
ms.topic: article
keywords: HoloLens、HoloLens 2、PIX、捕獲、混合現實耳機、windows mixed reality 耳機、虛擬實境耳機
ms.openlocfilehash: 4554600414784b2644006e6e891f16f8ce3a79f5
ms.sourcegitcommit: 924f8c1ceb93c378f800cf88d82944cf80f092bc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/04/2020
ms.locfileid: "96615330"
---
# <a name="installing-pix-for-hololens-2"></a><span data-ttu-id="ffa9d-104">安裝適用于 HoloLens 2 的 PIX</span><span class="sxs-lookup"><span data-stu-id="ffa9d-104">Installing PIX for HoloLens 2</span></span>

<span data-ttu-id="ffa9d-105">[PIX](https://devblogs.microsoft.com/pix) 是 Windows 上 DirectX 12 應用程式的效能微調和偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="ffa9d-105">[PIX](https://devblogs.microsoft.com/pix) is a performance tuning and debugging tool for DirectX 12 applications on Windows.</span></span> 

## <a name="setup"></a><span data-ttu-id="ffa9d-106">設定</span><span class="sxs-lookup"><span data-stu-id="ffa9d-106">Setup</span></span>

1. <span data-ttu-id="ffa9d-107">從您的主機電腦抓取最新的 PIX [版本]( https://devblogs.microsoft.com/pix/download) ，並透過 USB 纜線將您的 HoloLens 2 連接到您的電腦。</span><span class="sxs-lookup"><span data-stu-id="ffa9d-107">Grab the latest PIX [release]( https://devblogs.microsoft.com/pix/download) from your host PC and connect your HoloLens 2 to your PC via a USB cable.</span></span>

2. <span data-ttu-id="ffa9d-108">如果您的 HoloLens 2 是在 [Windows 測試人員組建](https://insider.windows.com) 上，或具有會中斷 PIX 的設定，請  [重新快閃裝置](https://docs.microsoft.com/hololens/hololens-recovery) 以清除所有資料。</span><span class="sxs-lookup"><span data-stu-id="ffa9d-108">If your HoloLens 2 is on a [Windows Insider build](https://insider.windows.com) or has a configuration that breaks PIX,  [re-flash your device](https://docs.microsoft.com/hololens/hololens-recovery) to erase all data.</span></span>

3. <span data-ttu-id="ffa9d-109">啟用 **開發人員模式** 和 **裝置入口網站**：</span><span class="sxs-lookup"><span data-stu-id="ffa9d-109">Enable **Developer Mode** and **Device Portal**:</span></span>

* <span data-ttu-id="ffa9d-110">從 Shell 開啟 **設定** ：</span><span class="sxs-lookup"><span data-stu-id="ffa9d-110">Open **Settings** from Shell:</span></span>

![反白顯示 [設定] 按鈕的 HoloLens 功能表螢幕擷取畫面](images/pix-img-01.jpg)

* <span data-ttu-id="ffa9d-112">選取 [ **更新 & 安全性**：</span><span class="sxs-lookup"><span data-stu-id="ffa9d-112">Select **Update & Security**:</span></span>

![醒目提示 [更新] 和 [安全性] 按鈕的 HoloLens 開啟 [設定] 視窗的螢幕擷取畫面](images/pix-img-02.jpg)

* <span data-ttu-id="ffa9d-114">**針對開發人員** 按一下：</span><span class="sxs-lookup"><span data-stu-id="ffa9d-114">Click **For Developers**:</span></span>

![已反白顯示 [開發人員] 按鈕的 [安全性和更新] 視窗的螢幕擷取畫面](images/pix-img-03.jpg)

* <span data-ttu-id="ffa9d-116">開啟 **使用開發人員功能** 並 **啟用裝置入口網站**</span><span class="sxs-lookup"><span data-stu-id="ffa9d-116">Turn on **Use Developer Features** and **Enable Device Portal**</span></span>

![已反白顯示 [啟用裝置入口網站] 按鈕的 [開發人員] 視窗螢幕擷取畫面](images/pix-img-04.jpg)

![[開發人員] 視窗的螢幕擷取畫面，其中已醒目提示 [使用開發功能] 切換](images/pix-img-05.jpg)

* <span data-ttu-id="ffa9d-119">如果裝置仍連線、喚醒，以及使用者登入，請啟動 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="ffa9d-119">With the device still connected, awake, and with the user logged in, launch Visual Studio.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ffa9d-120">請確定您的裝置不在待命模式或睡眠狀態。</span><span class="sxs-lookup"><span data-stu-id="ffa9d-120">Make sure your device isn't in standby mode or asleep.</span></span> <span data-ttu-id="ffa9d-121">如果您在此步驟中遇到問題，請參閱 [Windows 裝置入口網站的指示](https://docs.microsoft.com/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-windows-device-portal)。</span><span class="sxs-lookup"><span data-stu-id="ffa9d-121">If you're having trouble with this step, refer to the [Windows Device Portal instructions](https://docs.microsoft.com/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-windows-device-portal).</span></span>

## <a name="preparing-for-deployment"></a><span data-ttu-id="ffa9d-122">準備部署</span><span class="sxs-lookup"><span data-stu-id="ffa9d-122">Preparing for deployment</span></span>

1. <span data-ttu-id="ffa9d-123">在 Visual Studio 中，將 **ARM64** 設定為裝置的平臺和 **裝置** ：</span><span class="sxs-lookup"><span data-stu-id="ffa9d-123">In Visual Studio, set **ARM64** as the platform and **Device** as the device:</span></span>

![醒目提示平臺和裝置設定的 visual studio 解決方案螢幕擷取畫面](images/pix-img-06.png)

2. <span data-ttu-id="ffa9d-125">當 Visual Studio 提示您輸入來自裝置的 **PIN** 時：</span><span class="sxs-lookup"><span data-stu-id="ffa9d-125">When Visual Studio prompts you for a **PIN** from the device:</span></span>

![Visual studio 快顯視窗的螢幕擷取畫面，要求提供 PIN](images/pix-img-07.png)

* <span data-ttu-id="ffa9d-127">從 Shell 選取 **設定**</span><span class="sxs-lookup"><span data-stu-id="ffa9d-127">Select **Settings** from Shell</span></span>
* <span data-ttu-id="ffa9d-128">選取 **更新 & 安全性**</span><span class="sxs-lookup"><span data-stu-id="ffa9d-128">Select **Update & Security**</span></span>
* <span data-ttu-id="ffa9d-129">**針對開發人員** 按一下，然後在 **裝置探索** 下按配對</span><span class="sxs-lookup"><span data-stu-id="ffa9d-129">Click **For Developers** and press Pair under **Device Discovery**</span></span> 

![[開發人員] 視窗的螢幕擷取畫面，其中已醒目提示裝置探索來開啟 [設定]](images/pix-img-08.jpg)

![醒目提示註冊程式碼的付費裝置快顯螢幕擷取畫面](images/pix-img-09.jpg)

* <span data-ttu-id="ffa9d-132">在 Visual Studio 中輸入產生的 PIN 碼</span><span class="sxs-lookup"><span data-stu-id="ffa9d-132">Enter the generated PIN number in Visual Studio</span></span>

3. <span data-ttu-id="ffa9d-133">Visual Studio 會將應用程式部署到連接的 HoloLens 2，視應用程式而定，可能需要幾分鐘的時間。</span><span class="sxs-lookup"><span data-stu-id="ffa9d-133">Visual Studio will deploy the app to the connected HoloLens 2, which may take a few minutes depending on the app.</span></span>

## <a name="launching-pix"></a><span data-ttu-id="ffa9d-134">啟動 PIX</span><span class="sxs-lookup"><span data-stu-id="ffa9d-134">Launching PIX</span></span>

<span data-ttu-id="ffa9d-135">首先，使用裝置入口網站來確認 HoloLens 2 上未執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="ffa9d-135">First, use Device Portal to verify the app is not running on the HoloLens 2.</span></span> <span data-ttu-id="ffa9d-136">然後，啟動 PIX、連線到您的裝置，然後按一下 [ **首頁**]：</span><span class="sxs-lookup"><span data-stu-id="ffa9d-136">Then, launch PIX, connect to your device, and click **Home**:</span></span>

![PIX 應用程式主畫面的螢幕擷取畫面](images/pix-img-10.png)

* <span data-ttu-id="ffa9d-138">從左側功能表中選取 **[連線]** ：</span><span class="sxs-lookup"><span data-stu-id="ffa9d-138">Select **Connect** from the left-side menu:</span></span>

![已反白顯示 [連線] 按鈕的 PIX 應用程式左側功能表的螢幕擷取畫面](images/pix-img-11.png)

2. <span data-ttu-id="ffa9d-140">在 [ **電腦** ] 索引標籤中，按一下 [ **新增** ]，然後輸入下列認證：</span><span class="sxs-lookup"><span data-stu-id="ffa9d-140">From the **Computer** tab, click **Add** and enter the following credentials:</span></span>
    * <span data-ttu-id="ffa9d-141">別名：由使用者自行決定</span><span class="sxs-lookup"><span data-stu-id="ffa9d-141">Alias: Up to user’s discretion</span></span>
    * <span data-ttu-id="ffa9d-142">主機名稱或 IP 位址：127.0.0。1</span><span class="sxs-lookup"><span data-stu-id="ffa9d-142">Host Name or IP Address: 127.0.0.1</span></span>

3. <span data-ttu-id="ffa9d-143">按一下 [**電腦**] 索引標籤右下角的 **[** 連線]：</span><span class="sxs-lookup"><span data-stu-id="ffa9d-143">Click **Connect** in the lower-right of the **Computer** tab:</span></span>

![已反白顯示 [別名]、[主機名稱]、[IP 位址] 和 [新增] 按鈕的 PIX 應用程式連線視窗](images/pix-img-12.png)

> [!NOTE]
> <span data-ttu-id="ffa9d-145">第一個連接一律會變慢，因為正在複製二進位檔。</span><span class="sxs-lookup"><span data-stu-id="ffa9d-145">The first connection is always slower because binaries are being copied.</span></span>

4. <span data-ttu-id="ffa9d-146">當 PIX 連接到 HoloLens 2 時，請在 [啟動 UWP] 索引標籤的 [ **選取目標進程** ] 區段中尋找您的應用程式，然後按一下 [ **啟動**]：</span><span class="sxs-lookup"><span data-stu-id="ffa9d-146">When PIX has connected to the HoloLens 2, find your app in the **Select Target Process** section in the Launch UWP tab, and click **Launch**:</span></span>

![已反白顯示 [選取目標進程] 視窗和 [啟動] 按鈕的 PIX 應用程式螢幕擷取畫面](images/pix-img-13.png)

## <a name="gpu-captured"></a><span data-ttu-id="ffa9d-148">已捕獲 GPU</span><span class="sxs-lookup"><span data-stu-id="ffa9d-148">GPU captured</span></span>

1. <span data-ttu-id="ffa9d-149">按一下 [ **Gpu 捕捉**] 區段中的 [**相片**]，以啟動 gpu 捕獲：</span><span class="sxs-lookup"><span data-stu-id="ffa9d-149">Start the GPU capture by clicking **Photo** in the **GPU Capture** section:</span></span>

![已反白顯示 GPU 捕捉的 [電腦] 連接面板開啟的 PIX 應用程式螢幕擷取畫面](images/pix-img-14.png)

2. <span data-ttu-id="ffa9d-151">在 **GPU 捕捉** 面板中按一下產生的螢幕擷取畫面，以開啟要分析的捕獲：</span><span class="sxs-lookup"><span data-stu-id="ffa9d-151">Open the capture for analysis by clicking on the generated screen shot in the **GPU Capture** panel:</span></span>

![已反白顯示 GPU 捕捉面板的 [GPU 捕捉] 區段開啟的 PIX 應用程式螢幕擷取畫面](images/pix-img-15.png)

3. <span data-ttu-id="ffa9d-153">按 [ **開始** ] 開始分析：</span><span class="sxs-lookup"><span data-stu-id="ffa9d-153">Press **Start** to begin the analysis:</span></span>

![已反白顯示 [開始] 按鈕的 PIX 應用程式螢幕擷取畫面](images/pix-img-16.png)

> [!IMPORTANT]
> <span data-ttu-id="ffa9d-155">如果您在取得 GPU 捕捉之後收集計時資料，將需要重新開機耳機。</span><span class="sxs-lookup"><span data-stu-id="ffa9d-155">If you collect timing data after taking a GPU capture, you'll be required to reboot the headset.</span></span> <span data-ttu-id="ffa9d-156">這是一次重新開機裝置，而且是計時資料收集的必要項。</span><span class="sxs-lookup"><span data-stu-id="ffa9d-156">This is a one-time restart of the device and is required for timing data collection.</span></span>

<span data-ttu-id="ffa9d-157">PIX 現在已備妥可供使用！</span><span class="sxs-lookup"><span data-stu-id="ffa9d-157">PIX is now ready for use!</span></span>

## <a name="see-also"></a><span data-ttu-id="ffa9d-158">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ffa9d-158">See also</span></span>
* [<span data-ttu-id="ffa9d-159">PIX 首頁</span><span class="sxs-lookup"><span data-stu-id="ffa9d-159">PIX homepage</span></span>](https://devblogs.microsoft.com/pix)