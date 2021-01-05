---
title: 安裝使用於 HoloLens 2 的 PIX
description: 瞭解如何安裝適用于 HoloLens 2 裝置的 PIX。
author: hferrone
ms.author: flbagar
ms.date: 12/02/2020
ms.topic: article
keywords: HoloLens、HoloLens 2、PIX、捕獲、混合現實耳機、windows mixed reality 耳機、虛擬實境耳機
ms.openlocfilehash: 598a6b891798be7059eae2eff578c6bbbae442f6
ms.sourcegitcommit: 9d79aaa313f003dd42d5610d458031890776ee8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/30/2020
ms.locfileid: "97822925"
---
# <a name="installing-pix-for-hololens-2"></a>安裝使用於 HoloLens 2 的 PIX

[PIX](https://devblogs.microsoft.com/pix) 是 Windows 上 DirectX 12 應用程式的效能微調和偵錯工具。 

## <a name="setup"></a>安裝程式

1. 從您的主機電腦抓取最新的 PIX [版本]( https://devblogs.microsoft.com/pix/download) ，並透過 USB 纜線將您的 HoloLens 2 連接到您的電腦。

2. 如果您的 HoloLens 2 是在 [Windows 測試人員組建](https://insider.windows.com) 上，或具有會中斷 PIX 的設定，請  [重新刷新您的裝置](https://docs.microsoft.com/hololens/hololens-recovery) 以清除所有資料。

3. 啟用 **開發人員模式** 和 **裝置入口網站**：

* 從混合現實首頁開啟 **設定** ：

![反白顯示 [設定] 按鈕的 HoloLens 功能表螢幕擷取畫面](images/pix-img-01.jpg)

* 選取 [ **更新 & 安全性**：

![醒目提示 [更新] 和 [安全性] 按鈕的 HoloLens 開啟 [設定] 視窗的螢幕擷取畫面](images/pix-img-02.jpg)

* **針對開發人員** 選取：

![已反白顯示 [開發人員] 按鈕的 [安全性和更新] 視窗的螢幕擷取畫面](images/pix-img-03.jpg)

* 開啟 **使用開發人員功能** 並 **啟用裝置入口網站**

![已反白顯示 [啟用裝置入口網站] 按鈕的 [開發人員] 視窗螢幕擷取畫面](images/pix-img-04.jpg)

![[開發人員] 視窗的螢幕擷取畫面，其中已醒目提示 [使用開發功能] 切換](images/pix-img-05.jpg)

* 如果裝置仍連線、喚醒，以及使用者登入，請啟動 Visual Studio。

> [!IMPORTANT]
> 請確定您的裝置不在待命模式或睡眠狀態。 如果您在此步驟中遇到問題，請參閱 [Windows 裝置入口網站的指示](https://docs.microsoft.com/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-windows-device-portal)。

## <a name="preparing-for-deployment"></a>準備部署

1. 在 Visual Studio 中，將 **ARM64** 設定為裝置的平臺和 **裝置** ：

![醒目提示平臺和裝置設定的 visual studio 解決方案螢幕擷取畫面](images/pix-img-06.png)

2. 當 Visual Studio 提示您輸入來自裝置的 **PIN** 時：

![Visual studio 快顯視窗的螢幕擷取畫面，要求提供 PIN](images/pix-img-07.png)

* 從 Shell 選取 **設定**
* 選取 **更新 & 安全性**
* **針對開發人員** 選取，並在 **裝置探索** 下按配對 

![[開發人員] 視窗的螢幕擷取畫面，其中已醒目提示裝置探索來開啟 [設定]](images/pix-img-08.jpg)

![醒目提示註冊程式碼的付費裝置快顯螢幕擷取畫面](images/pix-img-09.jpg)

* 在 Visual Studio 中輸入產生的 PIN 碼

3. Visual Studio 會將應用程式部署到連接的 HoloLens 2，視應用程式而定，可能需要幾分鐘的時間。

## <a name="launching-pix"></a>啟動 PIX

首先，使用裝置入口網站來確認應用程式未在 HoloLens 2 上執行。 然後，啟動 PIX、連線到您的裝置，然後選取 [ **首頁**]：

![PIX 應用程式主畫面的螢幕擷取畫面](images/pix-img-10.png)

* 從左側功能表中選取 **[連線]** ：

![已反白顯示 [連線] 按鈕的 PIX 應用程式左側功能表的螢幕擷取畫面](images/pix-img-11.png)

2. 從 [ **電腦** ] 索引標籤中，選取 [ **新增**]，然後輸入下列認證：
    * 別名：由使用者自行決定
    * 主機名稱或 IP 位址：127.0.0。1

3. 選取 [**電腦**] 索引標籤右下角的 **[** 連線]：

![已反白顯示 [別名]、[主機名稱]、[IP 位址] 和 [新增] 按鈕的 PIX 應用程式連線視窗](images/pix-img-12.png)

> [!NOTE]
> 第一個連接一律會變慢，因為正在複製二進位檔。

4. 當 PIX 連接到 HoloLens 2 時，請在 [啟動 UWP] 索引標籤的 [ **選取目標進程** ] 區段中尋找您的應用程式，然後選取 [ **啟動**]：

![已反白顯示 [選取目標進程] 視窗和 [啟動] 按鈕的 PIX 應用程式螢幕擷取畫面](images/pix-img-13.png)

## <a name="gpu-captured"></a>已捕獲 GPU

1. 按一下 [ **Gpu 捕捉**] 區段中的 [**相片**]，以啟動 gpu 捕獲：

![已反白顯示 GPU 捕捉的 [電腦] 連接面板開啟的 PIX 應用程式螢幕擷取畫面](images/pix-img-14.png)

2. 按一下 **GPU 捕捉** 面板中產生的螢幕擷取畫面，以開啟要分析的捕獲：

![已反白顯示 GPU 捕捉面板的 [GPU 捕捉] 區段開啟的 PIX 應用程式螢幕擷取畫面](images/pix-img-15.png)

3. 按 [ **開始** ] 開始分析：

![已反白顯示 [開始] 按鈕的 PIX 應用程式螢幕擷取畫面](images/pix-img-16.png)

> [!IMPORTANT]
> 如果您在取得 GPU 捕捉之後收集計時資料，將需要重新開機耳機。 這是一次重新開機裝置，而且是計時資料收集的必要項。

PIX 現在已備妥可供使用！

## <a name="see-also"></a>請參閱
* [PIX 首頁](https://devblogs.microsoft.com/pix)