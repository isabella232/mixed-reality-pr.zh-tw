---
ms.openlocfilehash: 3306a9925c55c24c4d72ecb58d7c744dd64b283e
ms.sourcegitcommit: 0db5777954697f1d738469363bbf385481204d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/27/2021
ms.locfileid: "105636270"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

[MRTK 的 [設定] 對話方塊](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/configuration/mrtk-configuration-dialog) 會嘗試設定 XR SDK 和舊版 WSA 的深度緩衝區設定，但最好是檢查這些索引標籤，並確認 Unity 中的設定。

# <a name="xr-sdk"></a>[XR SDK](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

設定您的 Unity 應用程式是否會提供 Windows 的深度緩衝區：

1. 移至 [**編輯**  >  **專案設定**  >  **XR 外掛程式管理]** ，並確定功能表項目已展開。
2. 按一下對應到您所選 XR 執行時間的功能表項目（Windows Mixed Reality 或 OpenXR）。 此外，請確定已選取正確的組建平臺，因為可以使用 Windows 獨立和通用 Windows 平臺的索引標籤。
3. 若要啟用和設定：
    1. 針對 [OpenXR]，在 [ **深度提交模式** ] 下拉式清單中選取深度格式或 [無]。
    2. 針對 Windows Mixed Reality，請核取或取消核取 [ **共用深度緩衝區** ] 核取方塊。 然後，從 [ **深度緩衝區格式** ] 下拉式清單中選取格式。

![Windows XR 外掛程式深度設定 ](../../images/xrsdk-winxr-depth.png)
 ![ OpenXR 深度設定](../../images/xrsdk-openxr-depth.png)

> [!NOTE]
> 通常建議使用16位深度緩衝區來改善效能。 但是，如果使用16位深度格式，樣板緩衝區所需的效果 (像是某些 Unity UI 捲軸) 將無法運作，因為 Unity 不會在此設定中 [建立樣板緩衝區](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html) 。 相反地，選取 *24 位深度格式* 通常會建立 [8 位的樣板緩衝區（](https://docs.unity3d.com/Manual/SL-Stencil.html) 如果適用于端點圖形平台）。

# <a name="legacy-wsa"></a>[舊版 WSA](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

設定您的 Unity 應用程式是否會提供 Windows 的深度緩衝區：

1. 移至 [**編輯**  >  **專案設定**  >  **播放機**  >  **] 通用 Windows 平臺** 索引標籤  >  **XR 設定**]。
2. 展開 **WINDOWS MIXED REALITY SDK** 專案。
3. 核取或取消核取 [ **啟用深度緩衝區共用** ] 核取方塊。 預設會在新的專案中核取 [啟用深度緩衝區共用]，但在較舊的專案中可能預設為未核取。

![舊版 XR 深度設定](../../images/wmr-depth.png)

深度緩衝區可以改善視覺品質，只要 Windows 可以精確地將深度緩衝區中的正規化的每個圖元深度值對應到量值，就可以使用您在主要攝影機上的 Unity 中所設定的近距離和最遠的平面。 如果您的轉譯階段以一般方式處理深度值，您通常應該會在這裡進行，不過在顯示到現有的色彩圖元時，透明轉譯會寫入深度緩衝區的行程可能會使 reprojection 混淆。  如果您知道您的轉譯行程將會離開許多具有不正確深度值的最終深度圖元，您可能會藉由取消核取 [啟用深度緩衝區共用]，以取得更佳的視覺品質。

> [!NOTE]
> 通常建議使用16位深度緩衝區來改善效能。 但是，如果使用16位深度格式，樣板緩衝區所需的效果 (像是某些 Unity UI 捲軸) 將無法運作，因為 Unity 不會在此設定中 [建立樣板緩衝區](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html) 。 相反地，選取 *24 位深度格式* 通常會建立 [8 位的樣板緩衝區（](https://docs.unity3d.com/Manual/SL-Stencil.html) 如果適用于端點圖形平台）。