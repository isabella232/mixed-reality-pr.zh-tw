---
title: 使用 Unity 和 Visual Studio 的最佳作法
description: 使用 Unity 和 Visual Studio 來簡化建立混合現實應用程式之工作流程的秘訣和訣竅。
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: 部署、unity、visual studio、HoloLens、HoloLens 2、沉浸式耳機、最佳作法、混合現實耳機、windows mixed reality 耳機、虛擬實境耳機、UWP、Visual Studio Tools Windows SDK
ms.openlocfilehash: 5e00b24c7a36ae83a281800e2c7d8b2fc377f178
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2020
ms.locfileid: "94678843"
---
# <a name="best-practices-for-working-with-unity-and-visual-studio"></a>使用 Unity 和 Visual Studio 的最佳作法

使用 Unity 建立混合現實應用程式的開發人員必須在 Unity 與 Visual Studio 之間切換，才能建立部署到 HoloLens 和/或沉浸式耳機的應用程式套件。 根據預設，需要兩個 Visual Studio 實例 (一個用來修改 Unity 腳本，另一個則用於部署至裝置並進行) 的偵錯工具。 下列程式可讓您使用單一 Visual Studio 實例進行開發、減少匯出 Unity 專案的頻率，以及改善偵錯工具體驗。

## <a name="improving-iteration-time"></a>改善反復專案時間

Unity 2018 中的 .NET 腳本後端支援已被取代，並已在 Unity 2019 + 中移除。 因此，建議切換至 [IL2CPP](https://docs.unity3d.com/Manual/IL2CPP.html)。 不過，這可能會產生從 Unity 到 Visual Studio 的較長組建時間。 為了改進以加快反覆運算的速度，您應該設定其環境以獲得最佳編譯結果。

1) 每次在相同的目錄中建立您的專案，並在該處重複使用預先建立的檔案，以利用累加式大樓
2) 針對您的專案停用反惡意程式碼軟體掃描 & 組建資料夾
   - 在您的 Windows 10 設定應用程式下開啟 **病毒 & 威脅防護**
   - 選取 [**病毒 & 威脅防護設定**] 下的 [**管理設定**]
   - 選取 [**排除**] 區段底下的 [**新增或移除排除** 專案]
   - 按一下 [ **新增排除** ]，然後選取包含 Unity 專案程式碼和組建輸出的資料夾
3) 利用 SSD 來建立

如需詳細資訊，請參閱 [優化 IL2CPP 的組建時間](https://docs.unity3d.com/Manual/IL2CPP-OptimizingBuildTimes.html) 。 此外，請參閱 [IL2CPP 腳本後端的調試](https://docs.unity3d.com/Manual/windowsstore-debugging-il2cpp.html)。

此外，請考慮安裝 [ *UnityScriptAnalyzer* Visual Studio 擴充](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/UnityScriptAnalyzer)功能。 這項工具會分析您的 Unity c # 腳本，找出可以更優化的方式撰寫的程式碼。

## <a name="visual-studio-tools-for-unity"></a>Visual Studio Tools for Unity

下載 [Visual Studio Tools for Unity](https://docs.microsoft.com/visualstudio/cross-platform/getting-started-with-visual-studio-tools-for-unity?view=vs-2019)

**Visual Studio Tools for Unity 的優點**
* 藉由放置中斷點、評估變數和複雜運算式，從 Visual Studio 中調試 Unity in 編輯器播放模式。
* 使用 Unity Project Explorer 找出您的腳本，其與 Unity 所顯示的完全相同階層。
* 直接在 Visual Studio 內取得 Unity 主控台。
* 使用 [嚮導] 快速建立或流覽至腳本。

## <a name="expose-c-class-variables-for-easy-tuning"></a>公開 c # 類別變數以方便微調

有兩種方式可以公開類別變數。 建議的方式是將 [SerializeField] 屬性新增至您的私用變數。 這可讓他們從編輯器存取，但是無法以程式設計方式公開。  另一個選項是將 c # 類別變數設為公用，以在編輯器 UI 中公開這些變數。 

這兩種方法都可讓您在編輯器中播放時輕鬆地調整變數。 這特別適用于微調互動技師修理屬性。

## <a name="regenerate-uwp-visual-studio-solutions-after-windows-sdk-or-unity-upgrade"></a>在 Windows SDK 或 Unity 升級之後重新產生 UWP Visual Studio 解決方案

已簽入至原始檔控制的 UWP Visual Studio 解決方案，在升級至新的 Windows SDK 或 Unity 引擎之後可能會過期。 您可以在升級之後解決此問題，方法是從 Unity 建立新的 UWP 解決方案，然後將任何差異合併到簽入解決方案中。

## <a name="use-text-format-assets-for-easy-comparison-of-content-changes"></a>使用文字格式資產來輕鬆比較內容變更

以文字格式儲存資產可讓您更輕鬆地查看 Visual Studio 中的內容變更差異。 您可以藉由變更 **資產序列化** 模式來 **強制文字**，以在 [編輯 > 專案設定 > 編輯器] 中啟用此功能。 不過，合併文字資產檔案變更很容易出錯且不建議使用，因此請考慮在原始檔控制系統中啟用獨佔二進位簽出。

## <a name="see-also"></a>另請參閱
- [Visual Studio Tools for Unity](https://visualstudiogallery.msdn.microsoft.com/8d26236e-4a64-4d64-8486-7df95156aba9)
- [優化 IL2CPP 的組建時間](https://docs.unity3d.com/Manual/IL2CPP-OptimizingBuildTimes.html)
- [*UnityScriptAnalyzer* Visual Studio 擴充功能](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/UnityScriptAnalyzer)
