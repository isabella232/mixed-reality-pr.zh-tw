---
title: MRTK 2.7 版本資訊
description: MRTK 2.7 版的版本資訊
author: RogPodge
ms.author: roliu
ms.date: 06/16/2021
keywords: Unity、HoloLens、HoloLens 2、Mixed Reality、開發、MRTK、XRSDK、舊版 XR、閏運動、Ultraleap
ms.localizationpriority: high
monikerRange: '>= mrtkunity-2021-05'
ms.openlocfilehash: 7e4ddc4b97a6e580a7832ff2e86ee267246cce0d
ms.sourcegitcommit: c9d52f9529cabeaf912fffa6efc6599a9041a929
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/17/2021
ms.locfileid: "112305232"
---
# <a name="microsoft-mixed-reality-toolkit-27-release-notes"></a>Microsoft Mixed Reality 工具組2.7 版本資訊

## <a name="whats-new-in-271"></a>2.7.1 的新功能

### <a name="show-version"></a>顯示版本

`Mixed Reality`  >  `Toolkit` 功能表現在包含一個 `Show version...` 專案，該專案會檢查混合現實工具組 Foundation 套件，以判斷專案所使用的 MRTK 版本。

![顯示版本功能表](images/ShowVersionMenu.png)

![MRTK 版本對話方塊](images/VersionDialog.png)

> [!NOTE]
> 如果 MRTK 是從 GitHub 存放 [庫](https://aka.ms/mrtk)複製的，則不會設定版本資訊。
>
> ![無法判斷版本](images/CannotDetermineVersion.png)

### <a name="authors-list"></a>作者清單

從 MRTK 2.7.1 開始，作者清單檔案包含在 Mixed Reality 工具組 Foundation 套件中。

### <a name="notable-bugfixes-and-changes"></a>值得注意的錯誤修正與變更

- 已標示 XR SDK 管線[#9954](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9954)支援的 Unity 操縱杆管理員
- 已新增檢查以互動偵測器程式碼，以防止 null 錯誤 [#9943](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9943)
- 將 OpenXR 網狀提供者新增至脈衝著色器範例場景 [#9902](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9902)
- 將手型物理配置檔案還原至範例場景 [#9915](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9915)
- HandConstraint * 腳本的一些清除 [#9935](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9935)
- 體驗設定設定檔現在可設定為 None [#9982](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9982)


## <a name="whats-new-in-270"></a>2.7.0 的新功能

### <a name="openxr-is-now-officially-supported-in-mrtk"></a>OpenXR 現已正式支援 MRTK

由於新的 OpenXR 外掛程式變得越來越成熟，MRTK 現在正式支援 OpenXR。 相較于先前的版本，我們使用 OpenXR 將下列功能新增至專案：

- [支援系統提供的移動控制器模型](#support-for-the-system-provided-motion-controller-model-on-openxr)
- 支援 WinMR 手勢 (選取、保存、操作和流覽) [#9843](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9843)
- [控制器 haptics 的支援](#support-for-controller-haptics-across-legacy-wmr-windows-xr-plugin-and-openxr)
- [支援 HoloLens 2 上的已表達的手網格](#support-for-hololens-2-articulated-hand-mesh-on-openxr)
- 支援 HoloLens 2 [#9567](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9567)上的空間對應， [#9827](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9827)
- HoloLens 2 [#9744](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9744)上的場景理解支援

如果您的目標是透過 OpenXR HoloLens 2 或 Windows Mixed Reality 耳機，請務必透過 [混合現實功能工具](https://aka.ms/MRFeatureTool)安裝/更新至 **混合現實 OpenXR 外掛程式版本0.9.5 或** 更新版本，否則您可能會錯過上述一些改良功能。

### <a name="legacy-xr-and-xr-sdk-data-providers-can-now-be-used-within-the-same-profile"></a>舊版 XR 和 XR SDK 資料提供者現在可在相同的設定檔中使用

現在也會在選取適當的管線時載入資料提供者，讓舊版 XR 和 XR SDK 資料提供者在相同設定檔內並存存在。 為了達到此目的，舊版 XR 和 XR SDK 資料提供者現在會組織在設定檔視圖內的不同索引標籤底下，協助使用者判斷他們是否擁有其目標 XR 管線的正確設定檔。

![舊版與 XR SDK 資料提供者現在可以在單一設定檔下整合](../features/images/xrsdk/LegacyAndXrsdkUnified.png)

為了符合此值，現在不會再載入和顯示設定檔偵測器中的 null 資料提供者。 使用者可以 `Show null data providers in the profile inspector` 在 **編輯 > 專案設定下切換-> Mixed Reality 工具** 組，以使用遺漏的資料提供者來偵測非預期的行為。

![Null 資料提供者現在會隱藏在 ](https://user-images.githubusercontent.com/39840334/115093658-ead24600-9ecf-11eb-91c2-486a37f69aba.png)
 ![ 設定檔偵測器中的預設值切換顯示 null 資料提供者](https://user-images.githubusercontent.com/39840334/115093670-f6257180-9ecf-11eb-96ec-ffe44a225a55.png)

### <a name="added-experience-settings-and-an-associated-mixed-reality-scene-content-behavior"></a>新增經驗設定和相關聯的混合現實場景內容行為

使用者現在可以設定 [體驗設定](../features/experience-settings/experience-settings.md)，這可讓 MRTK 根據目標體驗適當地顯示 [混合現實場景內容](../features/experience-settings/scene-content.md) 。

如果使用者先前的經驗調整設定不符合新的體驗設定設定檔，系統會提示他們在偵測器中加以修正

![體驗規模遷移](https://user-images.githubusercontent.com/39840334/114946863-d70bde80-9e00-11eb-9859-fa40d40d2b36.gif)

### <a name="the-redesigned-configurator-now-guides-the-user-through-the-setup-process"></a>重新設計的設定程式現在會引導使用者完成設定流程

新的 MRTK 設定程式會提供使用者逐步指引，以正確設定專案以進行 XR 開發，並與 MRTK 搭配使用。 它涵蓋了選取的 XR 管線、取得平臺專屬外掛程式、匯入 TextMeshPro、顯示使用 UPM) 的範例 (，以及其他先前包含專案的建議設定。

![顯示管線清單的配置器](images/Configurator.png)

### <a name="graduated-teleport-hotspot"></a>分級的傳送熱點

新的「 [傳送」熱點元件](../features/teleport-system/teleport-hotspot.md) 已經過分級。 您可以將「傳送」熱點新增至 GameObject，以確保使用者在傳送至該位置時，在特定的位置和方向。

![傳送熱點範例](images/TeleportHotspot.gif)

### <a name="graduated-dwell"></a>過渡的停留

停留功能和範例現在已從實驗中開始。 範例場景中包含體積型 HoloLens 2 樣式按鈕的新範例。

![停留主圖](../features/images/dwell/MRTK_UX_Dwell.png)

### <a name="added-support-for-leap-motion-unity-modules-version-460-470-471-and-480"></a>已新增對4.6.0、4.7.0、4.7.1 和4.8.0 之 Leap 動作 Unity 模組的支援

最新版本的 [Leap 動作 Unity 模組](https://developer.leapmotion.com/unity) 支援現在與 MRTK 2.7.0 相容。  如需詳細資訊，請參閱 [如何設定 MRTK 以進行 Leap 動作](../supported-devices/leap-motion-mrtk.md) 。

感謝您 @jackyangzzh 參與新的 LeapMotionOrientationExample 場景！

### <a name="targeted-speech-events-raised-no-longer-restricted-to-gaze-pointers"></a>鎖定的目標語音事件不會再受限於注視指標

先前，目標語音事件只能在以注視指標為焦點的物件上引發。 現在，如果物件是以任何指標為焦點，便可以接收語音事件。

![具有太多指標的語音事件](https://user-images.githubusercontent.com/39840334/117516612-6fa00500-af4e-11eb-94ba-d5fb2ed4e7de.gif)

### <a name="ported-texttospeech-from-htk-to-mrtk"></a>從 HTK 移植 TextToSpeech 至 MRTK

又陷入 TextToSpeech 腳本現在已在 MRTK 中正式推出，可協助您使用從 UWP 平臺上的文字產生語音 [`SpeechSynthesizer`](/uwp/api/windows.media.speechsynthesis.speechsynthesizer) 。 也加入了範例場景來示範此功能。

### <a name="support-for-the-system-provided-motion-controller-model-on-openxr"></a>在 OpenXR 上支援系統提供的移動控制器模型

在 OpenXR 上針對系統提供的移動控制器模型，新增了在編輯器和執行時間中的支援。

![顯示兩個移動控制器模型的編輯器視窗](https://user-images.githubusercontent.com/3580640/116493405-89a55d80-a853-11eb-95ae-d430e6fdc8b4.png)

### <a name="support-for-hololens-2-articulated-hand-mesh-on-openxr"></a>支援在 OpenXR 上 HoloLens 2 表達的手網格

![MRTK 範例場景中在裝置上執行的手網格](https://user-images.githubusercontent.com/3580640/112909923-32bb3580-90a7-11eb-925d-464b135edc61.png)

### <a name="support-for-controller-haptics-across-legacy-wmr-windows-xr-plugin-and-openxr"></a>跨舊版 WMR、Windows XR 外掛程式和 OpenXR 的控制器 haptics 支援

已新增跨舊版 WMR、Windows XR 外掛程式和 OpenXR 的控制器 haptics 支援。 [#9735](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9735)

### <a name="support-for-eye-tracking-on-windows-xr-plugin"></a>Windows XR 外掛程式上的眼睛追蹤支援

在使用 Windows XR 外掛程式的最小2.7.0 版本時，新增了眼睛的支援 (Unity 2019) 、4.4.2 (Unity 2020) 和 5.2.2 (Unity 2021) 。 [#9609](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9609)

### <a name="notable-bugfixes-and-changes"></a>值得注意的錯誤修正與變更

- 縮小偵測變得更平滑。 現在難以意外地卸載縮小手勢。 [#9576](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9576)
- 具有物件操作工具元件的物件現在會在設定旗標時一致地維持版本的速度。 [#9733](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9733)
- Strafing 現在會檢查樓層，以協助防止相機可裁剪至環境或使用者停留在空白空間的情況。[#9697](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9697)
- IsNearObject 現在是虛擬屬性，可在擴充球體或取得指標時提供更大的彈性。 [#9803](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9803)
- 按鈕現在會在顯示可用的語音命令時顯示適當的關鍵字。 [#9824](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9824)
- Oculus 控制器現在會使用它自己的獨立視覺化程式，防止衝突的 MRTK 視覺效果與 Oculus 整合套件的視覺效果。 [#9589](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9589)
- 鍵盤相關腳本已變更，以配合最新 Unity 版本的行為 (2019.4.25 + & 2020.3.2 +) 。 在發行時，仍有自動完成錯誤和 TMP 輸入欄位 bug (兩者都是 MRTK) 影響 HoloLens 的外部。 如需詳細資訊，請參閱 [#9056](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9056) 和 [#9724](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9724)。
- 改進了滾動物件集合的效能。 也修正了導致集合內的 GameObject 在重複時遺失材質的問題。 [#9813](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9813)， [#9718](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9718)
- 在場景理解示範腳本中，新增函式 `GetSceneObjectsOfType` 以取得特定種類的所有觀察場景物件。 [#9524](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9524)， [#9744](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9744)
- 在命令列建立工具中，只有 `sceneList` `sceneListFile` 當有任何旗標存在時，或旗標所指定的場景 () 將會包含在組建中。 [#9695](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9695)
- 在 build tool 中，有一個新的選項可指定 `nuget.exe` 和使用該路徑來執行封裝還原，而不是使用 `msbuild` (預設選項) 。 [#9556](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9556)
- 已修正使用 Windows XR 外掛程式的問題可能會導致過時的接點和雙手勢網格。 [#9890](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9890)
- 已修正使用 Windows XR 外掛程式的自動遠端功能導致遺失輸入和互動的問題。 [#9868](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9868)
- 已修正 BuildDeployWindow 嘗試查詢不正確登錄機碼以取得 Windows SDK 路徑的問題。 [#9664](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9664)
- MRTK 的 glTF 匯入工具現在是選擇性的。 如果有多個 glTF 匯入工具，您可以藉由新增 `MRTK_GLTF_IMPORTER_OFF` 至自訂腳本定義符號來停用 MRTK。 [#9658](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9658)
- 已修正未正確偵測到 OpenVR 上 Knuckles 控制器的問題。 [#9881](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9881)
- 減少視覺化手中的每個畫面格配置數目 [#9756](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9756)
- 新增功能表項目以啟動 Unity 中的 MRTK 範例套件 (封裝管理員) ，讓您更輕鬆地匯入範例 [#9798](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9798)
- 減少使用 Unity 2020.3 時的載入時間警告數目。
- 已新增組建視窗功能檔： [造訪頁面](/windows/mixed-reality/mrtk-unity/features/tools/build-window)

## <a name="known-issues"></a>已知問題

### <a name="audio-demos-are-missing-an-asmdef-file-upm-package"></a>音訊示範缺少 asmdef 檔案 (UPM 套件) 

透過混合現實功能工具匯入 MRTK 時，會使用 Unity 封裝管理員 UI 將範例和示範新增至專案。 匯入音訊示範之後， `WindowsMicrophoneStreamDemo.unity` 場景將無法正常運作。 這是範例的 asmdef 檔案遺失的結果。

若要解決此 [問題](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9908)，請執行下列步驟：

- Copy Library/PackageCache/com.microsoft.mixedreality.toolkit.examples@ [...]/MRTK.範例： asmdef 至您的「資產/範例/混合現實工具組範例」資料夾
- 將複製的檔案重新命名為範例
- 開啟範例檔案
- 在 [名稱] 方塊中，將內容取代為範例
- 按一下 [套用]
- 建置及部署

即將推出的 MRTK 版本將會修正此問題。

### <a name="mrtk-build-window-triggers-indefinite-importing-assets-dialog-in-unity-20203"></a>Unity 2020.3 中的 MRTK 組建視窗觸發程式未限制的「匯入資產」對話方塊

Unity 2020.3 上的 MRTK build 視窗有一個已知 [問題](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9723) ，在成功執行 UWP 組建之後，[匯入資產] 對話方塊就不會完成。 正在與 Unity 合作調查此問題。

### <a name="text-mesh-pro-canvas-renderer-warnings-in-unity-2020"></a>Unity 2020 中的文字網格 Pro 畫布轉譯器警告

使用 Unity 2020 時，最 MRTK 的範例場景中會記錄下列警告：

```txt
Please remove the CanvasRenderer component from the [TextMeshPro] GameObject as this component is no longer necessary.
```

[TextMeshPro 版本 3.0.3](https://docs.unity3d.com/Packages/com.unity.textmeshpro@3.0/changelog/CHANGELOG.html#changes-3)中新增了 Canvas 轉譯器警告。  這些警告不會影響 MRTK 的範例場景，而且可以從主控台中清除。 如需詳細資訊，請參閱 [問題 9811](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9811) 。
