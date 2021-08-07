---
title: 硬體配件
description: 描述可搭配 Windows Mixed Reality 使用的配件類型，以及如何進行設定。
author: mattzmsft
ms.author: mazeller
ms.date: 05/20/2020
ms.topic: article
keywords: 作法、配件、藍牙、bt、控制器、遊戲台、clicker、xbox、硬體、混合現實耳機、windows mixed reality 耳機、虛擬實境耳機、移動控制器
ms.openlocfilehash: a6776df9374fce3f1399de944be06c93ff6fdcb3e6f4a38dcc92453556857376
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2021
ms.locfileid: "115188450"
---
# <a name="hardware-accessories"></a>硬體配件

Windows Mixed Reality 裝置支援配件。 您可以使用藍牙或 USB 埠，將支援的配件與您電腦上的沉浸式耳機配對。

如需搭配 HoloLens 使用藍牙附屬元件的相關資訊，請參閱[連線至藍牙和 USB-C 裝置](/hololens/hololens-connect-devices)。

Windows Mixed Reality 沉浸式耳機需要[輸入的附屬和](../design/gaze-and-commit.md)[聲音](../design/voice-input.md)以外的配件。 支援的配件包括 **鍵盤和滑鼠**、 **遊戲台** 和 **[移動控制器](../design/motion-controllers.md)**。

## <a name="pairing-bluetooth-accessories"></a>配對藍牙配件

將藍牙外設與沉浸式耳機配對，類似于將藍牙的周邊與 Windows 10 桌面或行動裝置配對：

1. 在 [開始] 功能表中，開啟 **設定** 應用程式
2. 移至 **裝置**
3. 使用滑杆開關開啟藍牙無線電
4. 將您的藍牙裝置放在配對模式中。 此程式會因裝置而異，但在大部分的藍牙裝置上，請按住一或多個按鈕。
5. 等候裝置的名稱顯示在藍牙裝置清單中。 當它完成時，請選取裝置，然後選取 [ **配對** ] 按鈕。 如果您附近有許多藍牙裝置，您可能需要滾動至 [藍牙裝置] 清單底部，以查看您嘗試配對的裝置。
6. 將藍牙週邊設備與輸入功能配對時 (例如：藍牙鍵盤) ，可能會顯示6位數或8位數的 pin。 請務必在週邊設備上輸入 pin，然後按 enter 鍵以完成與耳機的配對。

## <a name="motion-controllers"></a>運動控制器

沉浸式耳機支援 Windows Mixed Reality[動作控制器](../design/motion-controllers.md)，但無法 HoloLens。 這些控制器會在您的視野中提供精確且有回應的移動追蹤。 沉浸式耳機中的感應器會進行追蹤，也就是說，您不需要在空間的牆上安裝硬體。 每個控制器都有數種輸入方法。

![Windows Mixed Reality 動作控制器](../design/images/winmr-ck-1080x1080-350px.jpg)

## <a name="bluetooth-keyboards"></a>藍牙鍵盤

英文版的英文版藍牙鍵盤可以配對，並且可以在任何地方使用全像鍵盤。 取得高品質的鍵盤會產生差異，因此建議使用[Microsoft 通用](https://www.microsoft.com/accessories/products/keyboards/universal-foldable-keyboard/gu5-00001)的可折迭鍵盤或[microsoft Designer 藍牙 Desktop](https://www.microsoft.com/accessories/products/keyboards/designer-bluetooth-desktop/7n9-00001)。

## <a name="bluetooth-gamepads"></a>藍牙 gamepads

您可以使用具有應用程式的控制器，以及專門啟用遊戲台支援的遊戲。 Gamepads 不能用來控制 HoloLens 的使用者介面。

附隨 Xbox One S 或作為 Xbox One S 功能的配件銷售的 Xbox 無線控制器藍牙連線能力，因此您可以搭配 HoloLens 和沉浸式耳機使用它們。 Xbox 無線控制器[必須先更新](https://support.xbox.com/xbox-one/accessories/update-controller-for-stereo-headset-adapter)，才能搭配 HoloLens 使用。

其他品牌的藍牙 gamepads 可以與 Windows Mixed Reality 裝置搭配運作，但支援會因應用程式而異。

## <a name="other-bluetooth-accessories"></a>其他藍牙配件

只要週邊設備支援藍牙的 HID 或 GATT 設定檔，它就可以與 HoloLens 配對。 除了鍵盤、滑鼠和 HoloLens Clicker 以外的其他藍牙 HID 和 GATT 裝置可能需要 Microsoft HoloLens 上的隨附應用程式才能完整運作。

不支援的週邊設備包括：

* 不支援藍牙音訊設定檔中的週邊設備。
* 藍牙的音訊裝置（例如喇叭和耳機）可在設定應用程式中使用，但 Microsoft HoloLens 不支援作為音訊端點。
* 配對和檔案傳輸不支援藍牙啟用的電話和電腦。

## <a name="unpairing-a-bluetooth-peripheral"></a>取消配對藍牙週邊

1. 在 [開始] 功能表中，開啟 **設定** 應用程式
2. 移至 **裝置**
3. 開啟藍牙無線電（如果已關閉）
4. 在可用藍牙裝置清單中尋找您的裝置
5. 從清單中選取您的裝置，然後選取 [ **移除** ] 按鈕