---
ms.openlocfilehash: 4b42b669e45181dec45cab2337d01488c77f77cb
ms.sourcegitcommit: 8d386bf6c82ec9860815e873e1f2870ea410f40f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/31/2021
ms.locfileid: "106097023"
---
# <a name="unity-20192020--windows-xr-plugin"></a>[Unity 2019/2020 + Windows XR 外掛程式](#tab/winxr)

## <a name="ensuring-eye-gaze-input-capability-and-adding-eye-gaze-data-provider"></a>確保眼睛的輸入功能，以及新增眼睛 Data Provider

在 Unity 功能表中，選取 [混合實境工具組] > [公用程式] > [設定 Unity 專案] 以開啟 [MRTK 專案設定程式] 視窗，然後在 [UWP 功能] 區段中，確認 [啟用眼球注視輸入功能] 呈現灰色：

![Unity [MRTK 專案設定程式] 視窗](../images/mr-learning-base/base-08-section1-step1-1.png)

> [!NOTE]
> 當您在本教學課程系列開頭設定 Unity 時，「注視輸入」功能應該在[套用 MRTK 專案設定程式設定](../mr-learning-base-02.md#configuring-the-unity-project)指示期間啟用。 不過如果未啟用，請確定您立即啟用。

在 [階層] 視窗中，選取 [MixedRealityToolkit] 物件，然後在 [偵測器] 視窗中，流覽至 [輸入] 索引標籤：

* 展開 **輸入資料提供者** ，然後按一下 [ **+ 新增] Data Provider** 按鈕，以新增 Data Provider

![新增眼睛資料提供者1](../images/mr-learning-base/base-08-section1-step1-2.png)

將 **MixedReality**  >  **指派給** 新 Data Provider 的 [**類型**] 欄位。

![新增視覺資料提供者2](../images/mr-learning-base/base-08-section1-step1-3.png)

# <a name="unity-2020--openxr"></a>[Unity 2020 + OpenXR](#tab/openxr)

## <a name="ensuring-eye-gaze-input-capability-and-adding-eye-gaze-data-provider"></a>確保眼睛的輸入功能，以及新增眼睛 Data Provider

在 [階層] 視窗中，選取 [MixedRealityToolkit] 物件，然後在 [偵測器] 視窗中，流覽至 [輸入] 索引標籤：

* 展開 **輸入資料提供者** ，然後按一下 [ **+ 新增] Data Provider** 按鈕，以新增 Data Provider

![新增眼睛資料提供者1](../images/mr-learning-base/base-08-section1-step1-2openxr.png)

將 **MixedReality** 指派  >  至新 Data Provider 的 [**類型**] 欄位 **中。**

![新增視覺資料提供者2](../images/mr-learning-base/base-08-section1-step1-3openxr.png)

# <a name="legacy-wsa"></a>[舊版 WSA](#tab/wsa)

## <a name="ensuring-the-eye-gaze-input-capability-is-enabled"></a>確保已啟用「眼球注視輸入」功能

在 Unity 功能表中，選取 [混合實境工具組] > [公用程式] > [設定 Unity 專案] 以開啟 [MRTK 專案設定程式] 視窗，然後在 [UWP 功能] 區段中，確認 [啟用眼球注視輸入功能] 呈現灰色：

![Unity [MRTK 專案設定程式] 視窗](../images/mr-learning-base/base-08-section1-step1-1.png)

> [!NOTE]
> 當您在本教學課程系列開頭設定 Unity 時，「注視輸入」功能應該在[套用 MRTK 專案設定程式設定](../mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk)指示期間啟用。 不過如果未啟用，請確定您立即啟用。
