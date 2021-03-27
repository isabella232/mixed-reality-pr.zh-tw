---
title: 將 HoloLens (第1代) 應用程式移植到 HoloLens 2
description: 適用對象為擁有可在 HoloLens (第一代) 和較舊 MRTK 版本上運作的現有應用程式，並想要移植到 MRTK 第 2 版和 HoloLens 2 的開發人員。
author: hferrone
ms.author: grbury
ms.date: 12/9/2020
ms.topic: article
ms.localizationpriority: high
keywords: Windows Mixed Reality, 測試, MRTK, MRTK 第 2 版, HoloLens 2, unity, 移植, HoloLens (第 1 代), 混合實境頭戴式裝置, windows 混合實境頭戴式裝置, 虛擬實境頭戴式裝置, 移轉, 最佳做法, ARM
ms.openlocfilehash: 52055f35df05c2cc69e960c681598adac7bd6f1c
ms.sourcegitcommit: 0db5777954697f1d738469363bbf385481204d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/27/2021
ms.locfileid: "105636230"
---
# <a name="porting-hololens-1st-gen-apps-to-hololens-2"></a>將 HoloLens (第1代) 應用程式移植到 HoloLens 2

本指南的宗旨是要協助開發人員將現有的 HoloLens (第 1 代) Unity 應用程式移植到 HoloLens 2 裝置使用。 將 HoloLens (第 1 代) Unity 應用程式移植到 HoloLens 2 的作業有四個重要步驟。 

下列各節將詳細說明每個階段的資訊：

| 步驟 1 | 步驟 2 | 步驟 3 | 步驟 4 |
|----------|-------------------|-------------------|-------------------|
| ![Visual Studio 標誌](../images/visualstudio_logo.png) | ![Unity 標誌](../../design/images/logo-unity.png)| ![Unity 圖示](../unity/images/hololens2_icon.jpg) | ![MRTK 標誌](../../design/images/74-12.png) |
| 下載最新工具 | 更新 Unity 專案 | 針對 ARM 進行編譯 | 遷移至 MRTK v2

## <a name="prerequisites"></a>必要條件

**強烈建議** 在開始移植程序之前，先利用原始檔控制來儲存您應用程式原始狀態的快照集。 此外，也建議在移植程序進行期間於不同時間「儲存」檢查點狀態。 為原始應用程式準備另一個 Unity 執行個體以便在移植程序進行期間兩相比較，也很有幫助。 

> [!NOTE]
> 在移植之前，請確定您已安裝可用於開發 Windows Mixed Reality 的最新工具。 對大部分現有的 HoloLens 開發人員來說，這涉及更新至最新版的 Visual Studio 2019，以及安裝適當的 Windows SDK。 以下內容將進一步說明不同的 Unity 版本和混合實境工具組 (MRTK) 第 2 版。
>
> 如需詳細資訊，請參閱[安裝工具](../install-the-tools.md)。

## <a name="migrate-project-to-the-latest-version-of-unity"></a>將專案遷移至最新版的 Unity

如果您使用 [MRTK v2](https://github.com/microsoft/MixedRealityToolkit-Unity)，則 [Unity 2019 LTS](https://unity3d.com/unity/qa/lts-releases) 會是最佳的長期支援途徑，因為 Unity 或 MRTK 沒有重大變更。 評估任何目前存在於您專案中的[外掛程式相依性](https://docs.unity3d.com/Manual/Plugins.html)，並決定是否可針對 ARM64 建置這些 DLL。 針對具有硬性 ARM64 相依外掛程式的專案，您可能需要繼續針對 ARM 建置您的應用程式。

<!-- MRTK v2 always guarantees support for Unity 2018 LTS, but does not necessarily guarantee support for every iteration of Unity 2019.x.

To help clarify additional differences between [Unity 2018 LTS](https://unity3d.com/unity/qa/lts-releases) and Unity 2019.x, the following table outlines the trade-offs between the two versions. The primary difference between the two is the ability to compile for ARM64 in Unity 2019.

| Unity 2018 LTS | Unity 2019.x |
|----------|-------------------|
| ARM32 build support | ARM32 and ARM64 build support |
| Stable LTS build release | Beta stability |
| [.NET Scripting back-end](https://docs.unity3d.com/2018.4/Documentation/Manual/windowsstore-dotnet.html) *deprecated* | [.NET Scripting back-end](https://docs.unity3d.com/2018.4/Documentation/Manual/windowsstore-dotnet.html) *removed* |
| UNET Networking *deprecated* | UNET Networking *deprecated* |

-->

## <a name="update-sceneproject-settings-in-unity"></a>更新 Unity 中的場景/專案設定

在更新至 [Unity 2019 LTS](https://unity3d.com/unity/qa/lts-releases) 之後，建議您更新 Unity 中的特殊設定，以便在裝置上獲得最佳結果。 [Unity 的建議設定](../unity/Recommended-settings-for-Unity.md)底下會詳述這些設定。

再次重申，[.NET 指令碼處理後端](https://docs.unity3d.com/Manual/windowsstore-dotnet.html)在 Unity 2018 中即將過時，且在 Unity 2019 中「已移除」。 開發人員應積極考慮將其專案轉換至 [IL2CPP](https://docs.unity3d.com/Manual/IL2CPP.html)。

> [!NOTE]
> IL2CPP 指令碼處理後端會讓從 Unity 到 Visual Studio 的建置時間變長，開發人員應設定其開發人員機器，以[最佳化 IL2CPP 建置時間](https://docs.unity3d.com/Manual/IL2CPP-OptimizingBuildTimes.html)。
> 設定[快取伺服器](https://docs.unity3d.com/Manual/CacheServer.html)也可能會有幫助，對於有大量資產 (排除指令檔) 或不斷變更場景和資產的 Unity 專案來說，更是如此。 開啟專案時，Unity 會將符合資格的資產以內部快取格式儲存在開發機器上。 項目必須重新匯入，且在修改後必須重新處理。 此程序可以執行一次後就儲存在快取伺服器中，之後再與其他開發人員共用以節省時間，而不是每個開發人員都在本機處理新變更的重新匯入工作。

解決移至已更新 Unity 版本中的任何重大變更之後，在 HoloLens (第一代) 上建置並測試您目前的應用程式。 這是建立認可並儲存至原始檔控制的好時機。

## <a name="compile-dependenciesplugins-for-arm-processor"></a>針對 ARM 處理器編譯相依性/外掛程式

HoloLens (第 1 代) 會在 x86 處理器上執行應用程式，HoloLens 2 則會使用 ARM 處理器。 現有的 HoloLens 應用程式必須移植過去才能支援 ARM。 如前所述，Unity 2018 LTS 支援編譯 ARM32 的應用程式，而 Unity 2019.x 則支援編譯 ARM32 和 ARM64 的應用程式。 偏好開發 ARM64 應用程式，因為效能差異極大。 但要這麼做，所有的[外掛程式相依性](https://docs.unity3d.com/Manual/Plugins.html)也必須針對 ARM64 來建置。

請檢閱您的應用程式中所有的 DLL 相依性。 建議移除專案不再需要的相依性。 至於其餘的必要外掛程式，則請將個別的 ARM32 或 ARM64 二進位檔案嵌入至您的 Unity 專案中。

嵌入相關的 DLL 之後，請從 Unity 建置 Visual Studio 解決方案，在 Visual Studio 中針對 ARM 進行編譯 AppX，以測試是否可針對 ARM 處理器建置您的應用程式。 建議您在原始檔控制解決方案中將應用程式儲存為認可。

> [!IMPORTANT]
> 將建置目標變更為 ARM 之後，使用 MRTK v1 的應用程式可以在 HoloLens 2 上執行，前提是已符合所有其他需求。 這包括確定您具有所有外掛程式的 ARM 版本。 不過，您的應用程式將無法存取 HoloLens 2 特有功能，例如以關節連接的手部和眼球追蹤。 MRTK v1 和 MRTK v2 有不同的命名空間，可讓兩個版本位於相同專案中，這對於不同版本的轉換很有幫助。

## <a name="update-to-mrtk-version-2"></a>更新至 MRTK 第 2 版

[MRTK 第 2 版](https://github.com/microsoft/MixedRealityToolkit-Unity) 是 Unity 上的新工具組，支援 HoloLens (第1代) 和 HoloLens 2。 其也是 HoloLens 2 所有新增功能的所在位置，例如手動互動和眼球追蹤。

如需使用 MRTK 第 2 版的詳細資訊，請查看下列資源：

- [MRTK-檔首頁](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs)
- [安裝指南 (GitHub)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html)
- [MRTK - 手部追蹤 (GitHub)](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/input/hand-tracking.md)
- [MRTK - 眼球追蹤 (GitHub)](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/eye-tracking/eye-tracking-main.md)

### <a name="prepare-for-the-migration"></a>準備移轉

在嵌入新的 [*.unitypackage 檔案 (適用於 MRTK v2)](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases) 之前，建議您清查 **1) 與 MRTK v1 整合的任何自訂建置程式碼** 和 **2) 用於輸入互動或 UX 元件的任何自訂建置程式碼**。 內嵌 MRTK v2 的混合實境開發人員會在輸入和互動方面遇到最常見也最普遍的衝突。 建議您開始閱讀並了解 [MRTK v2 輸入模型](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/input/overview.md)。

終於，新的 [MRTK v2](https://github.com/microsoft/MixedRealityToolkit-Unity) 已從指令碼和場景中管理員物件的模型轉換為設定和服務提供者架構。 這會讓場景階層和架構模型更為簡潔，但需要花一段時間學習才能了解新的組態設定檔。 請閱讀[混合實境工具組設定指南](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/configuration/mixed-reality-configuration-guide.md)來開始熟悉重要設定和設定檔，以調整為符合應用程式的需求。

### <a name="migrating-the-project"></a>遷移專案

匯入 [MRTK v2](https://github.com/microsoft/MixedRealityToolkit-Unity) 之後，Unity 專案很可能會有許多編譯器相關錯誤。 之所以有這些錯誤，通常是因為使用了新的命名空間結構和新的元件名稱。 請繼續藉由將指令碼修改為新的命名空間和元件，來解決這些錯誤。

如需 HTK/MRTK 和 MRTK 第 2 版之間特定 API 差異的詳細資訊，請參閱 [MRTK 第 2 版 Wiki](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/updates-deployment/hrtk-to-mrtk-porting-guide.md) 上的移植指南。

### <a name="best-practices"></a>最佳作法

- 最好使用 [MRTK 標準著色器](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/rendering/mrtk-standard-shading.md)。
- 一次處理一個重大變更類型 (例如：IFocusable to [IMixedRealityFocusHandler](https://microsoft.github.io/MixedRealityToolkit-Unity/api/Microsoft.MixedReality.Toolkit.Input.IMixedRealityFocusHandler.html))。
- 每次變更後都進行測試，並使用原始檔控制。
- 盡可能使用預設的 MRTK UX (按鈕、靜態圖像等)。
- 避免直接修改 MRTK 檔案；請建立 MRTK 元件的包裝函式。
    - 這麼做可減少日後需要內嵌和更新 MRTK。
- 檢閱和探索 MRTK 中提供的場景範例，尤其是 HandInteractionExamples.scene。
- 重建有四色、collider 和 TextMeshPro 文字的畫布式 UI。
- 啟用[深度緩衝區共用](../unity/camera-in-unity.md#sharing-depth-buffers)或[設定焦點點](../unity/focus-point-in-unity.md)；最好使用 16 位元深度緩衝區以提升效能。 在轉譯色彩時，請務必同時轉譯深度。 對於透明和文字 gameobject，Unity 通常不會寫入深度。 
- 設定單一階段執行個體化轉譯路徑。
- 使用 [Hololens 2 的 MRTK 組態設定檔](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/profiles/profiles.md#hololens-2-profile)

### <a name="testing-your-application"></a>測試您的應用程式

在 MRTK 第 2 版中，您可以直接在 Unity 中模擬手部互動，並對新的 API 開發手部互動和眼球追蹤。 必須要有 HoloLens 2 裝置，才能建立令人滿意的使用者體驗。 建議您開始研究相關文件和工具以進一步了解。 [MRTK v2](https://github.com/microsoft/MixedRealityToolkit-Unity) 支援在 HoloLens (第 1 代) 上進行開發，且傳統的輸入模型 (例如，透過空中點選來進行選取) 仍可在 HoloLens (第 1 代) 裝置上進行測試。 

## <a name="updating-your-interaction-model-for-hololens-2"></a>更新 HoloLens 2 的互動模型

> [!CAUTION]
> 如果您的專案使用任何 XR.WSA API，在未來的 Unity 版本中，這些 API 將會取代為 Unity 的新 XR 輸入 API。 您可以在[這裡](https://docs.unity3d.com/Manual/xr_input.html)找到更多關於 XR 輸入 API 的資訊。

移植應用程式並讓其做好使用 HoloLens 2 的準備之後，您就可以開始考慮更新互動模型和全像投影設計/位置。
在 HoloLens (第 1 代) 中，應用程式的注視並認可互動模型所使用的全像投影可能太遠而無法融入視野。

下列步驟可更新您的應用程式設計，使其適用於 HoloLens 2：
1.  MRTK 元件：根據事前工作，如果您已新增 [MRTK v2](https://github.com/microsoft/MixedRealityToolkit-Unity)，則其中會有各種已針對 HoloLens 2 來設計及最佳化的元件/指令碼可供運用。

2.  互動模型：請考慮更新互動模型。 大部分情況下，建議您從注視和認可切換至手部。 一般來說，全像投影會在比手臂可及範圍還遠的地方，因此切換為手部會讓互動指標光線和抓取手勢變遠。

3.  全像投影位置：切換到手部互動模型之後，請考慮使用近距離互動抓取手勢用手將某些全像投影移得近一些，以便直接與全像投影互動。 建議可移得近一些以便能直接抓取或互動的全像投影類型包括，可在抓取和檢查全像投影時融入到 HoloLens 2 視野內的小型目標功能表、控制項、按鈕和較小型的全像投影。
<br>
每個應用程式和情境各不相同，所以我們會持續地根據意見反應和不斷地學習來改善和發佈設計指導方針。


## <a name="additional-caveats-and-learnings-about-moving-applications-from-x86-to-arm"></a>將應用程式從 x86 移至 ARM 的其他相關注意事項和學習

- 直截了當的 Unity 應用程式很簡單，因為您可以建置 ARM 應用程式套件組合，或直接部署至裝置供套件組合執行。 部分 Unity 原生外掛程式在開發上可能會有某些挑戰。 因此，您必須將所有 Unity 原生外掛程式升級至 Visual Studio 2019，並針對 ARM64 進行重建。

- 一個應用程式使用 Unity AudioKinetic Wwise 外掛程式，而該版本的 Unity 沒有 UWP ARM 外掛程式，導致必須耗費許多心力在有問題的應用程式中重新設計音效功能，使其能夠在 ARM 上執行。 請確定您已在 Unity 中安裝開發計畫所需的所有必要外掛程式，且可供使用。

- 在某些情況下，應用程式所需的外掛程式可能沒有 UWP/ARM 外掛程式，因此無法將應用程式移植到 HoloLens 2 並執行。 請連絡您的外掛程式提供者以解決問題，並提供對 ARM 的支援。

- 著色器中的 minfloat (和 min16float、minint 等變化) 在 HoloLens 2 上和在 HoloLens (第一代) 上的行為可能會不一樣。 具體來說，這些數字會保證至少會使用指定的位元數。 在 Intel/Nvidia GPU 上，minfloat 多半會當作 32 位元來處理。 在 ARM 上則會實際採用指定的位元數。 這表示實際上這些數字在 HoloLens 2 上的精確度或範圍，可能會比在 HoloLens (第 1 代) 上來得少。

- _asm 指令似乎無法在 ARM 上運作，這表示任何使用 _asm 指令的程式碼必須重寫。

- ARM 不支援 SIMD 指令集，因為在 ARM 上無法使用 xmmintrin.h、emmintrin.h、tmmintrin.h 和 immintrin.h 等多種標頭。

- ARM 上的著色器編譯器會在第一次繪製呼叫期間，於著色器已載入或著色器所相依的某個項目有所變更後執行，而不是在著色器載入時執行。 視需要編譯的著色器數目而定，對畫面播放速率的影響可能很明顯，且暗示在 HoloLens 2 與 HoloLens (第1代) 上處理、封裝、更新著色器的方式應該不同。

## <a name="see-also"></a>另請參閱
* [安裝工具](../install-the-tools.md)
* [MRTK - 安裝指南 (GitHub)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html)
* [MRTK-檔首頁](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs)
* [從 HoloToolkit/MRTK 移植到 MRTK 第2版 (GitHub) ] ([MRTK-檔首頁](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/updates-deployment/hrtk-to-mrtk-porting-guide.md)
* [Unity 的建議設定](../unity/recommended-settings-for-unity.md)
* [了解混合實境的效能](../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md)

