---
ms.openlocfilehash: 202d96435c437bc7630e82ea99a61f3c2a91c826
ms.sourcegitcommit: 8d386bf6c82ec9860815e873e1f2870ea410f40f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/31/2021
ms.locfileid: "106097662"
---
# <a name="unity-20192020--windows-xr-plugin"></a>[Unity 2019/2020 + Windows XR 外掛程式](#tab/winxr)

## <a name="ensuring-microphone-capability-and-adding-speech-input-data-provider"></a>確保麥克風功能和新增語音輸入資料提供者

在 Unity 功能表中，選取 [混合實境工具組] > [公用程式] > [設定 Unity 專案] 以開啟 [MRTK 專案設定程式] 視窗，然後在 [UWP 功能] 區段中，確認 [啟用麥克風功能] 呈現灰色：

![啟用麥克風功能](../images/mr-learning-base/base-09-section1-step1-1.png)

> [!NOTE]
> 當您在本教學課程系列開頭設定 Unity 時，「麥克風」功能應該在[套用 MRTK 專案設定程式設定](../mr-learning-base-02.md#configuring-the-unity-project)指示期間啟用。 不過如果未啟用，請務必立即啟用。

在 [階層] 視窗中，選取 [MixedRealityToolkit] 物件，然後在 [偵測器] 視窗中，流覽至 [輸入] 索引標籤：

* 展開 **輸入資料提供者** ，然後按一下 [ **+ 新增] Data Provider** 按鈕，以新增 Data Provider

![用於新增語音命令的資料提供者](../images/mr-learning-base/base-09-section1-step1-2.png)

將 **MixedReality 輸入**  >  **WindowsSpeechInputProvider** 指派給新 Data Provider 的 [**類型**] 欄位。

![新增語音命令設定](../images/mr-learning-base/base-09-section1-step1-3.png)

# <a name="unity-2020--openxr"></a>[Unity 2020 + OpenXR](#tab/openxr)

## <a name="ensuring-microphone-capability-and-adding-speech-input-data-provider"></a>確保麥克風功能和新增語音輸入資料提供者

在 Unity 功能表中，選取 [混合實境工具組] > [公用程式] > [設定 Unity 專案] 以開啟 [MRTK 專案設定程式] 視窗，然後在 [UWP 功能] 區段中，確認 [啟用麥克風功能] 呈現灰色：

![啟用 OpenXR 的麥克風功能](../images/mr-learning-base/base-09-section1-step1-1.png)

> [!NOTE]
> 當您在本教學課程系列開頭設定 Unity 時，「麥克風」功能應該在[套用 MRTK 專案設定程式設定](../mr-learning-base-02.md#configuring-the-unity-project)指示期間啟用。 不過如果未啟用，請務必立即啟用。

在 [階層] 視窗中，選取 [MixedRealityToolkit] 物件，然後在 [偵測器] 視窗中，流覽至 [輸入] 索引標籤：

* 展開 **輸入資料提供者** ，然後按一下 [ **+ 新增] Data Provider** 按鈕，以新增 Data Provider

![新增 OpenXR 的語音命令](../images/mr-learning-base/base-09-section1-step1-2.png)

將 **MixedReality 輸入**  >  **WindowsSpeechInputProvider** 指派給新 Data Provider 的 [**類型**] 欄位。

![新增 OpenXR 設定的語音命令](../images/mr-learning-base/base-09-section1-step1-3.png)

# <a name="legacy-wsa"></a>[舊版 WSA](#tab/wsa)

## <a name="ensuring-the-microphone-capability-is-enabled"></a>確定已啟用麥克風功能

在 Unity 功能表中，選取 [混合實境工具組] > [公用程式] > [設定 Unity 專案] 以開啟 [MRTK 專案設定程式] 視窗，然後在 [UWP 功能] 區段中，確認 [啟用麥克風功能] 呈現灰色：

![啟用麥克風功能](../images/mr-learning-base/base-09-section1-step1-1.png)

> [!NOTE]
> 當您在本教學課程系列開頭設定 Unity 時，「麥克風」功能應該在[套用 MRTK 專案設定程式設定](../mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk)指示期間啟用。 不過如果未啟用，請務必立即啟用。
