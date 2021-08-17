---
title: 設定您的 Unreal 專案
description: 瞭解如何設定您的專案 wit 最新版本的 Unreal 引擎和混合現實功能工具。
author: hferrone
ms.author: v-hferrone
ms.date: 4/28/2021
ms.topic: tutorial
ms.localizationpriority: high
keywords: Unreal、Unreal Engine 4、UE4、HoloLens 2、mixed reality、開發、功能、新專案、模擬器、檔、指南、全像投影、遊戲開發、混合現實耳機、windows mixed reality 耳機、虛擬實境耳機、最新、工具、開始使用、基本、Unreal、工具組、中樞、安裝、Windows、HoloLens、openxr、mrtk
ms.openlocfilehash: fee0e9a9deb92dffca742e19ebe27d2dd4cb53c0
ms.sourcegitcommit: 191c3d89c034714377d09fa91c07cbaa81301bae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/13/2021
ms.locfileid: "121905565"
---
# <a name="setting-up-your-unreal-project"></a>設定您的 Unreal 專案

建議您安裝 [Unreal Engine 4.25 版](https://docs.unrealengine.com//GettingStarted/Installation/index.html)或更新版本，以充分利用內建的 HoloLens 支援。

移至長篇遊戲 Launcher 中的 [**媒體** 櫃] 索引標籤，選取 [**啟動**] 旁的下拉箭號，然後按一下 [**選項**]。 在 [目標平台] 中，選取 **HoloLens 2**，然後按一下 [套用]。
![Unreal 安裝選項 HoloLens 2](../images/Unreal_Install_Option_HoloLens2.png)

## <a name="import-mixed-reality-toolkit-for-unreal"></a>匯入 Unreal 的混合現實工具組

![MRTK](../../design/images/MRTK_UX_Hero.png)

混合實境工具組 (MRTK) 是混合實境應用程式的開放原始碼跨平台開發套件。 MRTK 提供跨平台輸入系統、基礎元件，以及空間互動的常見基本要素。 該工具組主要用於加速開發以 Microsoft HoloLens、Windows Mixed Reality 沈浸式 (VR) 頭戴裝置和 OpenVR 平台為目標的應用程式。

如果您還沒有混合的現實專案，請遵循[HoloLens 2 開始使用教學](tutorials/unreal-uxt-ch1.md)課程的前三個部分，以準備好 MRTK 的專案。

### <a name="introducing-the-mrtk-hub-for-unreal"></a>適用于 Unreal 的 MRTK Hub 簡介

建議您使用 MRTK 中樞來取得 MRTK 外掛程式。 它是一種新的方法，讓開發人員能夠探索和更新 Microsoft Mixed Reality 外掛程式，並將其新增至其 Unreal 專案。 您可以查看外掛程式、查看其相依性，並將其安裝到您的專案中，而不需要離開 Unreal 編輯器。

- 探索新的 Microsoft Mixed Reality 外掛程式，並將其及其相依性安裝到您的 Unreal 專案。
- 將您的 Microsoft Mixed Reality 外掛程式保持在最新狀態。
- 如果您不再需要 Microsoft 混合現實外掛程式，請從專案中移除。

> [!NOTE]
> 適用于 Unreal 的 MRTK Hub 僅適用于 Unreal 引擎4.26 版或更新版本。 針對 Unreal 引擎4.25 版，您可以從 Unreal 引擎 Marketplace 或 GitHub 取得 MRTK 外掛程式，如[開始使用一節](unreal-development-overview.md#1-getting-started)中所述。

#### <a name="installing-the-mrtk-hub"></a>安裝 MRTK 中樞

從 [Unreal 引擎 Marketplace](https://www.unrealengine.com/marketplace/en-US/product/mixed-reality-toolkit-hub)下載外掛程式，然後開啟您的專案，然後從 [_外掛程式_] 功能表的 [_混合現實_] 區段中啟用該外掛程式。 出現提示時，重新開機編輯器。

![啟用 MRTK Hub 外掛程式](images/hub-enable-plugin.png)

為您的專案啟用外掛程式之後，您就可以從工具列按鈕存取該中樞。

![開啟 MRTK 中樞視窗](images/hub-toolbar.png)

#### <a name="installing-mixed-reality-plugins"></a>安裝混合現實外掛程式

若要使用中樞安裝外掛程式，請選取您要新增至專案的外掛程式，然後按 [ _安裝_ ] 按鈕。 若要下載外掛程式，請確認 _問題_ 方塊中沒有任何衝突，然後按 [ _確認_]。 下載外掛程式之後，系統會提示您重新開機編輯器。 可惜的是，我們無法為您自動重新開機編輯器;有時候，在安裝完成之前，新的編輯器實例將會啟動。

![使用 MRTK 中樞安裝外掛程式](images/hub-download.png)

關閉編輯器之後，您會看到命令提示字元出現，其中包含用來將已下載外掛程式解壓縮的進度列。 每個要安裝的外掛程式會出現一個命令提示字元。 完成解壓縮之後，您可以重新開啟編輯器，然後繼續進行 [混合的現實開發旅程](unreal-quickstart.md)。

![MRTK Hub 透過命令提示字元解壓縮外掛程式](images/hub-unpack.png)

> [!IMPORTANT]
> 安裝外掛程式之後，必須將它簽入原始檔控制中，就像任何其他專案層級外掛程式一樣。

#### <a name="updating-mixed-reality-plugins"></a>更新混合現實外掛程式

若要使用中樞更新外掛程式，請從清單中選取您想要更新的外掛程式，然後按 [ _安裝_ ] 按鈕。 若要下載更新的外掛程式，請確認 _問題_ 方塊中沒有任何衝突，然後按 [ _確認_]。 系統會提示您重新開機編輯器來完成更新。 外掛程式更新是在編輯器啟動期間完成，因此在您重新開啟編輯器之前，不需要等待任何解壓縮完成。

![透過 MRTK Hub 更新外掛程式](images/hub-update.png)

#### <a name="removing-mixed-reality-plugins"></a>移除混合現實外掛程式

若要使用中樞卸載外掛程式，請選取您要移除的外掛程式，然後從下拉式清單中選取您已安裝的版本。 若要移除外掛程式，請確認 _問題_ 方塊中沒有任何衝突，然後按 [ _確認_]。 系統會提示您重新開機編輯器，以完成移除。

![透過 MRTK 中樞移除外掛程式](images/hub-remove.png)

#### <a name="reviewing-changes-and-detecting-incompatibilities"></a>查看變更和偵測不相容性

您可以在中樞視窗的底部區段中，查看對專案所做的確切變更。 您可以從這裡看到將從專案新增或移除的外掛程式，以及任何可能會在進行變更時造成問題的潛在不相容問題。

> [!NOTE]
> _問題_ 清單會呈現 Unreal 引擎版本和外掛程式相依性版本的不相容性，但不會自動修正或建議問題的修正。

![嘗試安裝不相容的外掛程式](images/hub-issues.png)

:::row:::
    :::column:::
        <a href="https://github.com/Microsoft/MixedRealityToolkit-Unreal" target="_blank">![Unreal 標誌影像](../images/MRTK-Unreal-Banner.png)<br>**混合實境工具組-Unreal (GitHub)** </a><br>
    :::column-end:::
:::row-end:::

> [!NOTE]
> 如果您不想使用適用於 Unreal 的 MRTK，則必須自行撰寫所有互動和行為的指令碼。