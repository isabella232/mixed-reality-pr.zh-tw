---
title: 在 Unreal 中部署至裝置
description: 在 Unreal 中部署至裝置以 HoloLens 2 的指南
author: sw5813
ms.author: suwu
ms.date: 7/10/2020
ms.topic: article
keywords: Unreal、Unreal Engine 4、UE4、HoloLens、HoloLens 2、mixed reality、部署至裝置、電腦、檔、混合現實耳機、windows mixed reality 耳機、虛擬實境耳機
appliesto:
- HoloLens 2
ms.openlocfilehash: e811bc1b82aa40e658f9c855b65446483dd8bef2
ms.sourcegitcommit: 32cb81eee976e73cd661c2b347691c37865a60bc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/04/2020
ms.locfileid: "96609429"
---
# <a name="deploy-to-device-in-unreal"></a>在 Unreal 中部署至裝置

有兩種方式可將 Unreal 應用程式部署至 HoloLens 2：
* 直接從 Unreal 編輯器
* 作為透過裝置入口網站上傳的套件

這兩個選項都需要您設定 HoloLens，才能使用 [裝置入口網站](../platform-capabilities-and-apis/using-the-windows-device-portal.md) 進行開發。

## <a name="deploying-to-device-from-the-unreal-editor"></a>從 Unreal 編輯器部署至裝置

1. 選取 [ **啟動** ] 按鈕旁的下拉式箭號。 一開始，HoloLens 裝置選項將會呈現灰色。

![啟動下拉式選項](images/unreal/launch-dropdown.png)

2. 開啟 **裝置管理員** ，請注意，您的 HoloLens 不會自動出現在裝置清單中。

3. 展開 [ **新增未列出的裝置** ] 區段。

4. 選取 [ **HoloLens** ] 作為您的 **平臺**。

5. 輸入裝置的 IP 位址和埠資訊（以冒號分隔）作為裝置識別碼。 例如，透過 USB) 連接時 ("127.0.0.1： 10080"。 使用您的裝置入口網站使用者名稱和密碼認證。

6. 點擊 [ **新增** ] 並關閉 [裝置管理員]。
    * 如果發生錯誤（例如錯誤的位址或使用者認證），則會將訊息列印至輸出記錄檔。

![新增未列出的裝置](images/unreal/add-unlisted-device.png)

7. 再次選取 [ **啟動** ] 按鈕旁的下拉箭號，這次您應該會看到您剛剛新增的 HoloLens 裝置。 選取要建立並部署到 HoloLens 的 HoloLens 裝置。

>[!NOTE]
>建立裝置可能需要重新編譯著色器 (特別是在第一次執行) 上-這可能需要一些時間。 請勿讓裝置進入睡眠狀態，直到應用程式正在執行 (您可能必須將其磨損) 。 否則著色器編譯將會失敗！

## <a name="deploying-to-device-via-device-portal"></a>透過裝置入口網站部署至裝置

您可以在 [Unreal 教學課程系列](tutorials/unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal)中找到封裝和部署應用程式的詳細指示。

## <a name="next-development-checkpoint"></a>下一個開發檢查點

如果您正遵循我們所配置的 Unreal 開發旅程，您就會在部署階段。 您可以從這裡繼續新增 advanced services：

> [!div class="nextstepaction"]
> [進階服務](unreal-development-overview.md#5-adding-services)

您可以隨時回到 [Unreal 開發檢查點](unreal-development-overview.md#4-streaming-and-deploying-to-a-device)。
