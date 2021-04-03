---
ms.openlocfilehash: 5d3f5b1dd0600404e534023e3bf7b6fcaf7fe8f6
ms.sourcegitcommit: 8d386bf6c82ec9860815e873e1f2870ea410f40f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/31/2021
ms.locfileid: "106097918"
---
# <a name="unity-20192020--windows-xr-plugin"></a>[Unity 2019/2020 + Windows XR 外掛程式](#tab/winxr)

### <a name="1-clone-the-default-configuration-profile"></a>1.複製預設的組態設定檔

> [!NOTE]
> 組態設定檔是最上層的設定檔。 因此，若要編輯任何其他設定檔，您必須先複製組態設定檔。

在 [階層] 視窗中，選取 [ **MixedRealityToolkit** ] 物件，然後在 [偵測器] 視窗中，確認 **MixedRealityToolkit** 設定設定檔已設定為 **DefaultXRSDKConfigurationProfile**：

![已選取 DefaultHoloLens2ConfigurationProfile 的 Unity MixedRealityToolkit 元件](../images/mr-learning-base/base-03-section1-step1-1xrsdk.png)

在仍選取 **MixedRealityToolkit** 物件的情況下，在 [偵測器] 視窗中按一下 [複製與自訂] 按鈕來開啟 [複製設定檔] 視窗：

![Unity MixedRealityToolkit 元件的 [複製與自訂] 按鈕](../images/mr-learning-base/base-03-section1-step1-2xrsdk.png)

在 [複製設定檔] 視窗中，輸入適當的 **設定檔名稱**，例如 _GettingStarted_XRSDKConfigurationProfile_，然後按一下 [ **複製** ] 按鈕，以建立 **DefaultXRSDKConfigurationProfile** 的可編輯複本：

![Unity MixedRealityToolkit 複製的 [組態設定檔] 快顯視窗](../images/mr-learning-base/base-03-section1-step1-3xrsdk.png)

新建立的組態設定檔現在已指派為您場景的組態設定檔：

![已套用新建立自訂 HoloLens2ConfigurationProfile 的 Unity MixedRealityToolkit 元件](../images/mr-learning-base/base-03-section1-step1-4xrsdk.png)

在 Unity 功能表中，選取 [檔案] > [儲存]，即可儲存場景。

> [!TIP]
> 請記得在整個教學課程中儲存工作。

### <a name="2-enable-the-spatial-awareness-system"></a>2.啟用空間感知系統

在 [階層] 視窗中選取 **MixedRealityToolkit** 物件，在 [偵測器] 視窗中選取 [空間感知] 索引標籤，然後勾選 [啟用空間感知系統] 核取方塊：

![已啟用 [空間感知系統] 的 Unity MixedRealityToolkit 元件](../images/mr-learning-base/base-03-section1-step2-1xrsdk.png)

> [!NOTE]
> 針對未來的專案，如果您的應用程式不需要回應環境或與其互動，建議您讓空間感知保持關閉狀態，以降低效能成本。

### <a name="3-clone-the-default-spatial-awareness-system-profile"></a>3.複製預設的空間感知系統設定檔

在 [空間感知] 索引標籤中，按一下 [複製] 按鈕以開啟 [複製設定檔] 視窗：

![已選取 [空間感知] 索引標籤的 Unity MixedRealityToolkit 元件](../images/mr-learning-base/base-03-section1-step3-1xrsdk.png)

在 [複製設定檔] 視窗中，輸入適當的 **設定檔名稱**，例如 _GettingStarted_XRSDKSpatialAwarenessSystemProfile_，然後按一下 [ **複製** ] 按鈕，以建立 **DefaultXRSDKSpatialAwarenessSystemProfile** 的可編輯複本：

![Unity MixedRealityToolkit 複製的 [空間感知系統設定檔] 快顯視窗](../images/mr-learning-base/base-03-section1-step3-2xrsdk.png)

新建立的空間感知系統設定檔現在會自動指派給您的組態設定檔：

![已套用新建立自訂 MixedRealitySpatialAwarenessSystemProfile 的 Unity MixedRealityToolkit 元件](../images/mr-learning-base/base-03-section1-step3-3xrsdk.png)

### <a name="4-clone-the-default-spatial-awareness-mesh-observer-profile"></a>4.複製預設的空間感知網格觀察器設定檔

在仍選取 [ **空間感知** ] 索引標籤的情況下，展開 [ **XR SDK Windows Mixed Reality 空間網格觀察** 者] 區段，然後按一下 [ **複製** ] 按鈕以開啟 [複製設定檔] 視窗：

![已擴充 Windows Mixed Reality [空間網格觀察者] 區段的 Unity MixedRealityToolkit 元件](../images/mr-learning-base/base-03-section1-step4-1xrsdk.png)

在 [複製設定檔] 視窗中，輸入適當的 **設定檔名稱**，例如 _GettingStarted_MixedRealitySpatialAwarenessMeshObserverProfile_，然後按一下 [複製] 按鈕，以建立 **DefaultMixedRealitySpatialAwarenessMeshObserverProfile** 的可編輯複本：

![Unity MixedRealityToolkit 複製的 [空間網格觀察者設定檔] 快顯視窗](../images/mr-learning-base/base-03-section1-step4-2xrsdk.png)

新建立的空間感知網格觀察器設定檔現在會自動指派給您的空間感知系統設定檔：

![已套用新建立自訂 MixedRealitySpatialAwarenessMeshObserverProfile 的 Unity MixedRealityToolkit 元件](../images/mr-learning-base/base-03-section1-step4-3xrsdk.png)

### <a name="5-change-the-visibility-of-the-spatial-awareness-mesh"></a>5.變更空間感知網格的顯示

在 [空間網格觀察器設定] 中，將 [顯示選項] 變更為 [遮蔽]，以隱藏仍在運作的空間對應網格：

![[空間網格觀察者顯示選項] 設定為 [遮蔽] 的 Unity MixedRealityToolkit 元件](../images/mr-learning-base/base-03-section1-step5-1xrsdk.png)

> [!NOTE]
> 雖然空間對應網格看不到，但仍存在且正常運作。 例如，空間對應網格後方的任何全像投影 (實體牆後方的全像投影等) 將不會顯示。

您方才已了解如何修改 MRTK 設定檔中的設定。 如您所見，為了自訂 MRTK 設定，您必須先建立預設設定檔的複本。 由於預設設定檔無法編輯，因此當您想要還原為預設設定時，一律可以參考這些設定。 若要深入了解 MRTK 設定檔及其架構，您可以參閱 [MRTK 文件入口網站](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity)中的 [MRTK 設定檔設定指南](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/configuration/mixed-reality-configuration-guide)。

# <a name="unity-2020--openxr"></a>[Unity 2020 + OpenXR](#tab/openxr)

### <a name="1-clone-the-default-configuration-profile"></a>1.複製預設的組態設定檔

> [!NOTE]
> 組態設定檔是最上層的設定檔。 因此，若要編輯任何其他設定檔，您必須先複製組態設定檔。

在 [階層] 視窗中，選取 [ **MixedRealityToolkit** ] 物件，然後在 [偵測器] 視窗中，確認 **MixedRealityToolkit** 設定設定檔已設定為 **DefaultOpenXRConfigurationProfile**：

![已選取預設 openXR 設定檔的 Unity MixedRealityToolkit 元件](../images/mr-learning-base/base-03-section1-step1-1openxr.png)

在仍選取 **MixedRealityToolkit** 物件的情況下，在 [偵測器] 視窗中按一下 [複製與自訂] 按鈕來開啟 [複製設定檔] 視窗：

![適用于 openxr 設定檔的 Unity MixedRealityToolkit 元件複製 & 自訂按鈕](../images/mr-learning-base/base-03-section1-step1-2openxr.png)

在 [複製設定檔] 視窗中，輸入適當的 **設定檔名稱**，例如 _GettingStarted_OpenXRConfigurationProfile_，然後按一下 [ **複製** ] 按鈕，以建立 **DefaultOpenXRConfigurationProfile** 的可編輯複本：

![適用于 openxr 設定檔的 Unity MixedRealityToolkit 複製設定設定檔快顯視窗](../images/mr-learning-base/base-03-section1-step1-3openxr.png)

新建立的組態設定檔現在已指派為您場景的組態設定檔：

![已套用新建立之自訂 OpenXR 的 Unity MixedRealityToolkit 元件](../images/mr-learning-base/base-03-section1-step1-4openxr.png)

在 Unity 功能表中，選取 [檔案] > [儲存]，即可儲存場景。

> [!TIP]
> 請記得在整個教學課程中儲存工作。

### <a name="2-enable-the-spatial-awareness-system"></a>2.啟用空間感知系統

在 [階層] 視窗中選取 **MixedRealityToolkit** 物件，在 [偵測器] 視窗中選取 [空間感知] 索引標籤，然後勾選 [啟用空間感知系統] 核取方塊：

![已啟用 [空間感知系統] 的 Unity MixedRealityToolkit 元件](../images/mr-learning-base/base-03-section1-step2-1xrsdk.png)

> [!NOTE]
> 針對未來的專案，如果您的應用程式不需要回應環境或與其互動，建議您讓空間感知保持關閉狀態，以降低效能成本。

### <a name="3-clone-the-default-spatial-awareness-system-profile"></a>3.複製預設的空間感知系統設定檔

在 [空間感知] 索引標籤中，按一下 [複製] 按鈕以開啟 [複製設定檔] 視窗：

![已選取 [空間感知] 索引標籤的 Unity MixedRealityToolkit 元件](../images/mr-learning-base/base-03-section1-step3-1xrsdk.png)

在 [複製設定檔] 視窗中，輸入適當的 **設定檔名稱**，例如 GettingStarted_OpenXRSpatialAwarenessSystemProfile，然後按一下 [ **複製** ] 按鈕，以建立 **DefaultXRSDKSpatialAwarenessSystemProfile** 的可編輯複本：

![Unity MixedRealityToolkit 複製的 [空間感知系統設定檔] 快顯視窗](../images/mr-learning-base/base-03-section1-step3-2xrsdk.png)

新建立的空間感知系統設定檔現在會自動指派給您的組態設定檔：

![已套用新建立自訂 MixedRealitySpatialAwarenessSystemProfile 的 Unity MixedRealityToolkit 元件](../images/mr-learning-base/base-03-section1-step3-3xrsdk.png)

### <a name="4-clone-the-default-spatial-awareness-mesh-observer-profile"></a>4.複製預設的空間感知網格觀察器設定檔

在仍選取 [ **空間感知** ] 索引標籤的情況下，展開 [ **XR SDK Windows Mixed Reality 空間網格觀察** 者] 區段，然後按一下 [ **複製** ] 按鈕以開啟 [複製設定檔] 視窗：

![已擴充 Windows Mixed Reality [空間網格觀察者] 區段的 Unity MixedRealityToolkit 元件](../images/mr-learning-base/base-03-section1-step4-1xrsdk.png)

在 [複製設定檔] 視窗中，輸入適當的 **設定檔名稱**，例如 _GettingStarted_MixedRealitySpatialAwarenessMeshObserverProfile_，然後按一下 [複製] 按鈕，以建立 **DefaultMixedRealitySpatialAwarenessMeshObserverProfile** 的可編輯複本：

![Unity MixedRealityToolkit 複製的 [空間網格觀察者設定檔] 快顯視窗](../images/mr-learning-base/base-03-section1-step4-2xrsdk.png)

新建立的空間感知網格觀察器設定檔現在會自動指派給您的空間感知系統設定檔：

![已套用新建立自訂 MixedRealitySpatialAwarenessMeshObserverProfile 的 Unity MixedRealityToolkit 元件](../images/mr-learning-base/base-03-section1-step4-3xrsdk.png)

### <a name="5-change-the-visibility-of-the-spatial-awareness-mesh"></a>5.變更空間感知網格的顯示

在 [空間網格觀察器設定] 中，將 [顯示選項] 變更為 [遮蔽]，以隱藏仍在運作的空間對應網格：

![[空間網格觀察者顯示選項] 設定為 [遮蔽] 的 Unity MixedRealityToolkit 元件](../images/mr-learning-base/base-03-section1-step5-1xrsdk.png)

> [!NOTE]
> 雖然空間對應網格看不到，但仍存在且正常運作。 例如，空間對應網格後方的任何全像投影 (實體牆後方的全像投影等) 將不會顯示。

您方才已了解如何修改 MRTK 設定檔中的設定。 如您所見，為了自訂 MRTK 設定，您必須先建立預設設定檔的複本。 由於預設設定檔無法編輯，因此當您想要還原為預設設定時，一律可以參考這些設定。 若要深入了解 MRTK 設定檔及其架構，您可以參閱 [MRTK 文件入口網站](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity)中的 [MRTK 設定檔設定指南](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/configuration/mixed-reality-configuration-guide)。


# <a name="legacy-wsa"></a>[舊版 WSA](#tab/wsa)

### <a name="1-clone-the-default-configuration-profile"></a>1.複製預設的組態設定檔

> [!NOTE]
> 組態設定檔是最上層的設定檔。 因此，若要編輯任何其他設定檔，您必須先複製組態設定檔。

在 [階層] 視窗中選取 **MixedRealityToolkit** 物件，然後在 [偵測器] 視窗中，將 **MixedRealityToolkit** 組態設定檔變更為 **DefaultHoloLens2ConfigurationProfile**：

![已選取 DefaultHoloLens2ConfigurationProfile 的 Unity MixedRealityToolkit 元件](../images/mr-learning-base/base-03-section1-step1-1.png)

在仍選取 **MixedRealityToolkit** 物件的情況下，在 [偵測器] 視窗中按一下 [複製與自訂] 按鈕來開啟 [複製設定檔] 視窗：

![Unity MixedRealityToolkit 元件的 [複製與自訂] 按鈕](../images/mr-learning-base/base-03-section1-step1-2.png)

在 [複製設定檔] 視窗中，輸入適當的 **設定檔名稱**，例如 _GettingStarted_HoloLens2ConfigurationProfile_，然後按一下 [複製] 按鈕，以建立 **DefaultHololens2ConfigurationProfile** 的可編輯複本：

![Unity MixedRealityToolkit 複製的 [組態設定檔] 快顯視窗](../images/mr-learning-base/base-03-section1-step1-3.png)

新建立的組態設定檔現在已指派為您場景的組態設定檔：

![已套用新建立自訂 HoloLens2ConfigurationProfile 的 Unity MixedRealityToolkit 元件](../images/mr-learning-base/base-03-section1-step1-4.png)

在 Unity 功能表中，選取 [檔案] > [儲存]，即可儲存場景。

> [!TIP]
> 請記得在整個教學課程中儲存工作。

### <a name="2-enable-the-spatial-awareness-system"></a>2.啟用空間感知系統

在 [階層] 視窗中選取 **MixedRealityToolkit** 物件，在 [偵測器] 視窗中選取 [空間感知] 索引標籤，然後勾選 [啟用空間感知系統] 核取方塊：

![已啟用 [空間感知系統] 的 Unity MixedRealityToolkit 元件](../images/mr-learning-base/base-03-section1-step2-1.png)

> [!NOTE]
> 針對未來的專案，如果您的應用程式不需要回應環境或與其互動，建議您讓空間感知保持關閉狀態，以降低效能成本。

### <a name="3-clone-the-default-spatial-awareness-system-profile"></a>3.複製預設的空間感知系統設定檔

在 [空間感知] 索引標籤中，按一下 [複製] 按鈕以開啟 [複製設定檔] 視窗：

![已選取 [空間感知] 索引標籤的 Unity MixedRealityToolkit 元件](../images/mr-learning-base/base-03-section1-step3-1.png)

在 [複製設定檔] 視窗中，輸入適當的 **設定檔名稱**，例如 _GettingStarted_MixedRealitySpatialAwarenessSystemProfile_，然後按一下 [複製] 按鈕，以建立 **DefaultMixedRealitySpatialAwarenessSystemProfile** 的可編輯複本：

![Unity MixedRealityToolkit 複製的 [空間感知系統設定檔] 快顯視窗](../images/mr-learning-base/base-03-section1-step3-2.png)

新建立的空間感知系統設定檔現在會自動指派給您的組態設定檔：

![已套用新建立自訂 MixedRealitySpatialAwarenessSystemProfile 的 Unity MixedRealityToolkit 元件](../images/mr-learning-base/base-03-section1-step3-3.png)

### <a name="4-clone-the-default-spatial-awareness-mesh-observer-profile"></a>4.複製預設的空間感知網格觀察器設定檔

在仍選取 [空間感知] 索引標籤的情況下，展開 [Windows Mixed Reality 空間網格觀察器] 區段，然後按一下 [複製] 按鈕來開啟 [複製設定檔] 視窗：

![已擴充 Windows Mixed Reality [空間網格觀察者] 區段的 Unity MixedRealityToolkit 元件](../images/mr-learning-base/base-03-section1-step4-1.png)

在 [複製設定檔] 視窗中，輸入適當的 **設定檔名稱**，例如 _GettingStarted_MixedRealitySpatialAwarenessMeshObserverProfile_，然後按一下 [複製] 按鈕，以建立 **DefaultMixedRealitySpatialAwarenessMeshObserverProfile** 的可編輯複本：

![Unity MixedRealityToolkit 複製的 [空間網格觀察者設定檔] 快顯視窗](../images/mr-learning-base/base-03-section1-step4-2.png)

新建立的空間感知網格觀察器設定檔現在會自動指派給您的空間感知系統設定檔：

![已套用新建立自訂 MixedRealitySpatialAwarenessMeshObserverProfile 的 Unity MixedRealityToolkit 元件](../images/mr-learning-base/base-03-section1-step4-3.png)

### <a name="5-change-the-visibility-of-the-spatial-awareness-mesh"></a>5.變更空間感知網格的顯示

在 [空間網格觀察器設定] 中，將 [顯示選項] 變更為 [遮蔽]，以隱藏仍在運作的空間對應網格：

![[空間網格觀察者顯示選項] 設定為 [遮蔽] 的 Unity MixedRealityToolkit 元件](../images/mr-learning-base/base-03-section1-step5-1.png)

> [!NOTE]
> 雖然空間對應網格看不到，但仍存在且正常運作。 例如，空間對應網格後方的任何全像投影 (實體牆後方的全像投影等) 將不會顯示。

您方才已了解如何修改 MRTK 設定檔中的設定。 如您所見，為了自訂 MRTK 設定，您必須先建立預設設定檔的複本。 由於預設設定檔無法編輯，因此當您想要還原為預設設定時，一律可以參考這些設定。 若要深入了解 MRTK 設定檔及其架構，您可以參閱 [MRTK 文件入口網站](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity)中的 [MRTK 設定檔設定指南](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/configuration/mixed-reality-configuration-guide)。
