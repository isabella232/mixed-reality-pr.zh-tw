---
title: 將應用程式提交到 Microsoft Store
description: 本文提供提交混合現實應用程式給 Microsoft Store 的秘訣，包括如何封裝和測試您的應用程式，以及如何將認證傳遞給您的應用程式，並協助在存放區中探索應用程式。
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: 應用程式、uwp、提交、提交、篩選、中繼資料、系統需求、關鍵字、wack、認證、套件、appx、商品化
ms.openlocfilehash: d1b47366831ad46c889002f60dd13f98021a5690
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2020
ms.locfileid: "91676893"
---
# <a name="submitting-an-app-to-the-microsoft-store"></a>將應用程式提交到 Microsoft Store

[HoloLens](../hololens-hardware-details.md)和 Windows 10 PC 都能為您的[沉浸式耳機](../discover/immersive-headset-hardware-details.md)執行通用 Windows 平臺應用程式。 無論您是提交支援 HoloLens 或 PC 的應用程式 (或兩者) ，您都會透過 [合作夥伴中心](https://partner.microsoft.com/dashboard)將應用程式提交至 Microsoft Store。

如果您還沒有合作夥伴中心開發人員帳戶，可以 [立即註冊](https://developer.microsoft.com/store/register)。

## <a name="packaging-a-mixed-reality-app"></a>封裝混合現實應用程式

### <a name="prepare-image-assets-included-in-the-appx"></a>準備隨附于 appx 的映射資產

Appx 建立工具需要數個映射資產，才能將您的應用程式建立至 appx 套件，以提交至存放區。 您可以在 MSDN 上深入瞭解 [磚和圖示資產的指導方針](https://msdn.microsoft.com/library/windows/apps/mt412102.aspx) 。

| 必要資產 | 建議的調整 | 映像格式 | 這會顯示在哪裡？ | 
|----------|----------|----------|------------------|
| 正方形71x71 標誌 | 任意 |  PNG | N/A | 
| 正方形150x150 標誌 | 150x150 (100% scale) 或 225x225 (150% scale)  | PNG | 如果未提供310x310，則啟動釘選和所有應用程式 () 、商店搜尋建議、商店清單頁面、商店流覽、商店搜尋 | 
|  寬310x150 標誌 |  任意  |  PNG  |  N/A | 
|  市集標誌 |  75x75 (150% 規模)   |  PNG  |  合作夥伴中心，報表應用程式，撰寫評論，我的文件庫 | 
|  啟動顯示畫面 |  930x450 (150% 規模)   |  PNG  |  2D 應用程式啟動器 (平板)  | 

另外還有一些建議的資產，包括 HoloLens 可利用的資產。

| 建議的資產 | 建議的調整 | 這會顯示在哪裡？ | 
|----------|----------|----------|
|  正方形310x310 標誌 |  310x310 (150% 規模)  |  開始釘選和所有應用程式 | 

### <a name="live-tile-requirements"></a>動態磚需求

HoloLens 上的 [開始] 功能表將會使用最大內含的正方形圖格影像。

您可能會看到 Microsoft 發佈的一些應用程式，具有適用于其應用程式的3D 啟動器。 開發人員可以使用 [這些指示](implementing-3d-app-launchers.md)，為其應用程式新增3d 啟動器。

### <a name="specifying-target-and-minimum-version-of-windows"></a>指定 Windows 的目標和最小版本

如果您的混合現實應用程式包含特定 Windows 版本的特定功能，請務必指定您的通用 Windows 應用程式將支援的目標和最低平臺版本。

**尤其是針對以 [Windows Mixed Reality 沉浸式耳機](../discover/immersive-headset-hardware-details.md)的應用程式來說，這種情況特別適用于需要至少 Windows 10 Fall Creators Update (10.0;組建 16299) 可正常運作。**

當您在 Visual Studio 中建立新的通用 Windows 專案時，系統會提示您設定 Windows 的目標和最小版本。 您也可以在 [專案] 功能表中，針對現有的專案變更此設定，然後在下拉式功能表底部的 [<您的應用程式名稱的> 屬性]。

![在 Visual Studio 2019 中設定最低和目標平臺版本](images/visual-studio-min-version-500px.png)<br>
在 Visual Studio 中設定最低和目標平臺版本

### <a name="specifying-target-device-families"></a>指定目標裝置系列

適用于 [hololens](../hololens-hardware-details.md) 和 [沉浸式耳機](../discover/immersive-headset-hardware-details.md) 的 Windows Mixed Reality 應用程式 () 是通用 Windows 平臺的一部分，因此任何具有 [目標裝置系列](https://msdn.microsoft.com/library/windows/apps/dn986903.aspx) 「Windows 通用」的應用程式套件，都能在 HoloLens 或具有沉浸式耳機的 Windows 10 電腦上執行。 話雖如此，如果您未在應用程式資訊清單中指定目標裝置系列，您可能會不小心將應用程式開啟到非預期的 Windows 10 裝置。 遵循下列步驟來指定預期的 Windows 10 裝置系列，然後 [再次檢查當您在合作夥伴中心中上傳應用程式套件以提交至商店時，所選取的裝置系列是否正確。](submitting-an-app-to-the-microsoft-store.md#submitting-your-mixed-reality-app-to-the-store)

若要在 Visual Studio 中設定此欄位，請以滑鼠右鍵按一下 package.appxmanifest，然後選取 [View Code]，然後尋找 [y Name] 欄位。 依預設，它看起來可能如下所示：

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Universal" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10586.0" />
</Dependencies>
```

如果您的應用程式是針對 **hololens**建立的，則您可以藉由指定「Windows 全像」的目標裝置系列，確保它只會安裝在 hololens 上。 

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Holographic" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10586.0" />
</Dependencies>
```

如果您的應用程式需要特定 **HoloLens 2** 的功能，例如眼睛追蹤或手動追蹤，您可以藉由指定「windows 全像」的目標裝置系列和 MinVersion 10.0.18362.0，確定它是以 windows 18362 版或更新版本為目標。 

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Holographic" MinVersion="10.0.18362.0" MaxVersionTested="10.0.18362.0" />
</Dependencies>
```

如果您的應用程式是針對 **Windows Mixed Reality 沉浸式耳機**建立的，則您可以指定目標裝置系列為 "10.0.16299.0"，以確保它只會安裝在具有 Windows Mixed Reality) 所需 Windows 10 Fall Creators Update (的 Windows 10 電腦上。

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Desktop" MinVersion="10.0.16299.0" MaxVersionTested="10.0.16299.0" />
</Dependencies>
```

最後，如果您的應用程式要在 **HoloLens 和 Windows Mixed Reality 沉浸式耳機**上執行，您可以確保應用程式僅可供這兩個裝置系列使用，並同時針對每個目標裝置系列加上其各自的 MinVersion，以確保每個裝置的目標都是正確的最低 Windows 版本。

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Desktop" MinVersion="10.0.16299.0" MaxVersionTested="10.0.16299.0" />
   <TargetDeviceFamily Name="Windows.Holographic" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10586.0" />
</Dependencies>
```

您可以閱讀 [y UWP 檔](https://docs.microsoft.com/uwp/schemas/appxpackage/uapmanifestschema/element-targetdevicefamily)，以深入瞭解目標裝置系列。

### <a name="associate-app-with-the-store"></a>建立應用程式與存放區的關聯

從 Visual Studio 解決方案的 [專案] 功能表中，選擇 [商店 > 將應用程式與存放區建立關聯]。 若您執行此動作，您可以測試您應用程式中的購買與通知案例。 當您建立應用程式與存放區的關聯時，這些值會下載到本機電腦上目前專案的應用程式資訊清單檔中：
* 套件顯示名稱
* 封裝名稱
* 發行者識別碼
* 發行者顯示名稱
* 版本

如果您為資訊清單建立自訂 .xml 檔，以覆寫預設 package.appxmanifest 檔案，則無法將應用程式與市集建立關聯。 如果您嘗試將自訂資訊清單檔與市集建立關聯，您將會看到錯誤訊息。

### <a name="creating-an-upload-package"></a>建立上傳套件

遵循將 [通用 Windows 應用程式封裝 Windows 10 的](https://msdn.microsoft.com/library/hh454036.aspx#Anchor_2)指導方針。

建立上傳封裝的最後一個步驟是使用 [Windows 應用程式認證套件](#windows-app-certification-kit)來驗證封裝。

如果您要將專門用於 HoloLens 的封裝新增至其他 Windows 10 裝置系列上的現有產品，您也會想要瞭解 [版本號碼可能會如何影響傳遞給特定客戶的套件](https://msdn.microsoft.com/library/windows/apps/mt188602.aspx)，以及 [如何將套件散發到不同的作業系統](https://msdn.microsoft.com/library/windows/apps/mt188601.aspx)。

一般的指導方針是，適用于裝置的最高版本號碼套件將會是存放區所散發的套件。

如果有 Windows 通用套件和 Windows 的全像套件，且 Windows 通用套件的版本號碼較高，則 HoloLens 使用者將會下載較高版本號碼的 Windows 通用套件，而不是 Windows 的全像套件。 有幾個解決此問題的解決方案：
1. 確定您的平臺專屬套件（例如 Windows）的版本號碼，與平臺中立套件（例如 Windows）的版本號碼一樣高。
2. 如果您也擁有平臺專屬套件，請勿將應用程式封裝為 Windows 通用套件，改為針對您想要在其上使用的特定平臺封裝 Windows 通用套件

>[!NOTE]
> 若要在 HoloLens (第一代) 和 HoloLen 2 上支援您的應用程式，您必須上傳兩個應用程式套件;其中一個包含適用于 HoloLens 的 x86 (第一代) ，另一個則包含適用于 HoloLens 2 的 ARM 或 ARM64。 
> 
> 如果您在套件中同時包含 ARM 和 ARM64，則會在 HoloLens 2 上使用 ARM64 版本。 

>[!NOTE]
> 您可以宣告單一套件以適用于多個目標裝置系列

3. 建立可在所有平臺上運作的單一 Windows 通用套件。 這對此支援並不是很好的作法，因此建議使用上述的解決方案。

## <a name="testing-your-app"></a>測試應用程式

### <a name="windows-app-certification-kit"></a>Windows 應用程式認證套件

當您建立要透過 Visual Studio 提交至合作夥伴中心的應用程式套件時，[建立應用程式套件] 嚮導會提示您針對所建立的套件執行 Windows 應用程式認證套件。 為了讓存放區順利提交程式，最好先驗證 [Windows 應用程式認證套件測試](https://msdn.microsoft.com/library/windows/apps/jj657973.aspx) 是否會在本機電腦上通過您的應用程式，然後再提交至存放區。 目前不支援在遠端 HoloLens 上執行 Windows 應用程式認證套件。

### <a name="run-on-all-targeted-device-families"></a>在所有目標裝置系列上執行

Windows 通用平臺可讓您建立在所有 Windows 10 裝置系列上執行的單一應用程式。 但是，它並不保證通用 Windows 應用程式只會在所有裝置系列上運作。 在您選擇將應用程式提供給 HoloLens 或其他任何 Windows 10 目標裝置系列之前，請務必先在這些裝置系列上 [測試應用程式](../develop/platform-capabilities-and-apis/testing-your-app-on-hololens.md) ，以確保良好的體驗。

## <a name="submitting-your-mixed-reality-app-to-the-store"></a>將您的混合現實應用程式提交至商店

如果您要提交以 Unity 專案為基礎的混合現實應用程式，請先觀看這段 [影片](https://channel9.msdn.com/Blogs/One-Dev-Minute/How-to-publish-your-Unity-game-as-a-UWP-app) 。

一般情況下，提交適用于 HoloLens 和/或沉浸式耳機的 Windows Mixed Reality 應用程式，就像是將任何 UWP 應用程式提交至 Microsoft Store 一樣。 一旦您藉 [由保留名稱來建立應用程式](https://docs.microsoft.com/windows/uwp/publish/create-your-app-by-reserving-a-name)，您應該遵循 [UWP 提交檢查清單](https://docs.microsoft.com/windows/uwp/publish/app-submissions)。

您首先要做的其中一件事，就是為您的混合現實體驗 [選取類別目錄和子類別](https://docs.microsoft.com/windows/uwp/publish/category-and-subcategory-table) 。 **請務必為您的應用程式選擇最精確的類別**，讓我們可以將您的應用程式放在正確的商店類別中，並確保它會使用相關的搜尋查詢來顯示。 **將您的 VR 標題列為遊戲，將不會對您的應用程式造成更好的曝光，** 而且可能會讓它無法顯示在更適合且更擁擠的類別中。

不過，提交程式中有四個主要區域，您會想要進行混合的現實特定選擇：
1. 在 [[屬性](https://docs.microsoft.com/windows/uwp/publish/enter-app-properties)] 下的 [**[產品](submitting-an-app-to-the-microsoft-store.md#mixed-reality-product-declarations)** 宣告] 區段中。
2. 在 [[屬性](https://docs.microsoft.com/windows/uwp/publish/enter-app-properties)] 下的 [**[系統需求](submitting-an-app-to-the-microsoft-store.md#mixed-reality-system-requirements)**] 區段中。
3. 在 [[套件](https://docs.microsoft.com/windows/uwp/publish/upload-app-packages)] 下的 [**[裝置系列可用性](submitting-an-app-to-the-microsoft-store.md#device-family-availability)**] 區段中。
4. 在數個 **[Store 清單頁面](submitting-an-app-to-the-microsoft-store.md#store-listing-page)** 欄位中。

### <a name="mixed-reality-product-declarations"></a>混合現實產品聲明

在應用程式提交程式的 [ **[屬性](https://docs.microsoft.com/windows/uwp/publish/enter-app-properties)** ] 頁面上，您會在 [ **[產品](https://docs.microsoft.com/windows/uwp/publish/app-declarations)** 宣告] 區段中找到與混合現實相關的數個選項。

![混合現實產品聲明](images/product-declarations-900px.png)<br>
混合現實產品聲明

首先，您會想要識別應用程式提供混合現實體驗的裝置類型。 這可確保您的應用程式會包含在存放區中 Windows Mixed Reality 的集合中，而且會在連線到沉浸式耳機 (或在 HoloLens) 上流覽商店時，向流覽存放區的使用者呈現。

在「此體驗的設計目的是為了 Windows Mixed Reality：」
* 只有當您的應用程式在沉浸式耳機連接到使用者的電腦時提供 VR 體驗時，才檢查 [ **電腦** ] 方塊。 如果您的應用程式是專門用來在沉浸式耳機上執行，或者是標準電腦遊戲/應用程式，以在耳機連接時提供混合的現真實模式和/或額外的內容，則應勾選此方塊。
* 只有在您的應用程式在 HoloLens 上執行 **時，才** 會提供全像攝影體驗。
* 如果您的應用程式在這兩種裝置類型上都提供混合現實體驗，請檢查 **這兩個** 方塊。

如果您選取上述的「電腦」，則您會想要將「混合現實設定」 (活動層級) 。 這僅適用于連接到沉浸式耳機的電腦上所執行的混合現實體驗，因為 HoloLens 上的混合現實應用程式是全球規模，而使用者在安裝期間不會定義界限。
* 如果您的應用程式是以使用者停留在一個位置的目的來設計，請選擇 [ **站上 +** ]， (範例就是您坐在飛機) 的環境中的遊戲。
* 如果您的應用程式是以使用者在安裝期間所定義的界限內進行的意圖來設計，請選擇 [ **所有體驗** ]，例如，您可以在其中逐步執行，並將) 的攻擊 (。

### <a name="mixed-reality-system-requirements"></a>混合的現實系統需求

在應用程式提交程式的 [ **[屬性](https://docs.microsoft.com/windows/uwp/publish/enter-app-properties)** ] 頁面上，您會在 [ **[系統需求](https://docs.microsoft.com/windows/uwp/publish/enter-app-properties#system-requirements)** ] 區段中找到與混合現實相關的數個選項。

![系統需求](images/system-reqs-800px.png)<br>
系統需求

在本節中，您將識別) 硬體所需的最小 (，並建議您的混合現實應用程式使用 (選用) 硬體。

**輸入硬體：**

如果您的應用程式支援[語音輸入](../design/voice-input.md)) 、 **[Xbox 控制器或遊戲台](../discover/hardware-accessories.md#bluetooth-gamepads)**，以及/或**[Windows Mixed Reality 動作控制器](../design/motion-controllers.md)** 的**麥克風** (，請使用核取方塊來告訴潛在客戶。 這項資訊會顯示在您應用程式的 [產品詳細資料] 頁面上，並協助您的應用程式包含在適當的應用程式/遊戲集合中 (例如，支援動作控制器) 的所有遊戲都有可能存在集合。

請仔細針對輸入類型選取 [最小硬體] 或 [建議的硬體] 核取方塊。 

例如： 
* 如果您的遊戲需要移動控制器，但接受透過麥克風的語音輸入，請選取 [Windows Mixed Reality 動作控制器] 旁的 [最低硬體] 核取方塊，但在 [麥克風] 旁邊選取 [建議的硬體] 核取方塊。 
* 如果您的遊戲可以使用 Xbox 控制器/遊戲台或移動控制器來播放，您可以選取 [Xbox controller 或遊戲程式] 旁邊的 [最低硬體] 核取方塊，然後選取 [Windows Mixed Reality 動作控制器] 旁的 [建議的硬體] 核取方塊，因為動作控制器可能會在遊戲台中提供逐步解說。

**Windows Mixed Reality 沉浸式耳機：**

指出是否需要沉浸式耳機才能使用您的應用程式，或為選擇性的，對客戶滿意度和教育而言是不可或缺的。

如果您的應用 *程式只能透過* 沉浸式耳機使用，請選取 [Windows Mixed Reality 沉浸式耳機] 旁的 [最低硬體] 核取方塊。 這會顯示在 [商店] 的 [產品詳細資料] 頁面上，顯示為 [購買] 按鈕上方的警告，讓客戶不想要購買可在其電腦上運作的應用程式，例如傳統的桌面應用程式。

如果您的應用程式是在桌上型電腦上執行（例如傳統的電腦應用程式），但在沉浸式耳機連線時提供 VR 體驗 (您的應用程式的完整內容是否可用，或只有部分) ，請選取 [Windows Mixed Reality 沉浸式耳機] 旁的 [建議的硬體] 核取方塊。 如果您的應用程式是以傳統桌面應用程式的形式運作，而未連線到沉浸式耳機，則不會在應用程式產品詳細資料頁面上的 [購買] 按鈕上方出現警告。

**電腦規格：**

如果您想要讓應用程式盡可能觸及許多 Windows Mixed Reality 沉浸式耳機使用者，您可以將電腦規格的 [目標](../develop/platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md) 設為 [具有整合式圖形 Windows Mixed Reality 電腦](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)的電腦規格。

無論您的混合現實應用程式是否以最低 Windows Mixed Reality 電腦需求為目標，或需要特定的電腦設定 (例如 [WINDOWS MIXED REALITY ULTRA 電腦](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)的專用 GPU，您應該在 [最低硬體] 欄中指出相關的電腦規格。

如果您的混合現實應用程式是設計為執行效能更好，或是提供更高解析度的圖形，請在特定電腦設定或圖形配接器上，使用 [建議的硬體] 資料行中的相關電腦規格來表示。

只有當您的混合現實應用程式使用連接到電腦的沉浸式耳機時，才適用這種情況。 如果您的混合現實應用程式只在 HoloLens 上執行，您不需要指出電腦規格，因為 HoloLens 只有一個硬體設定。

### <a name="device-family-availability"></a>裝置系列可用性

如果您已在 Visual Studio 中 [正確封裝您的應用程式](https://docs.microsoft.com/windows/uwp/publish/app-package-requirements) ，則在應用程式提交程式的 [套件] 頁面上上傳它時，應該會產生一個表格，指出您的應用程式將可使用哪些裝置系列。

![裝置系列可用性資料表](images/device-family-table-900px.png)<br>
裝置系列可用性資料表

如果您的混合現實應用程式適用于沉浸式耳機，則至少應該在資料表中選取 [Windows 10 桌面]。 如果您的混合現實應用程式可在 HoloLens 上運作，則至少應選取 [Windows 10 全像攝影版]。 如果您的應用程式同時在兩個 Windows Mixed Reality 耳機類型上執行，則應該選取 [Windows 10 桌面] 和 [Windows 10 全像攝影版]。

>[!TIP]
>許多開發人員在上傳其應用程式套件與套件資訊清單和您在合作夥伴中心中的應用程式/發行者帳戶資訊相關的套件時，會遇到錯誤。 使用與您的 Windows 開發人員帳戶相關聯的相同帳戶登入 Visual Studio，通常可以避免這些錯誤， (用來登入合作夥伴中心) 的帳戶。 如果您使用相同的帳戶，您將能夠在封裝應用程式之前，先將應用程式與其在 Microsoft Store 中的身分識別建立關聯。

![將您的應用程式與 Microsoft Store 建立關聯](images/associate-your-app-700px.png)<br>
將您的應用程式與 Visual Studio 中的 Microsoft Store 建立關聯

### <a name="store-listing-page"></a>Store 清單頁面

在應用程式提交程式的 [ [Store 清單](https://docs.microsoft.com/windows/uwp/publish/create-app-store-listings) ] 頁面上，有幾個地方可新增您混合現實應用程式的實用資訊。

>[!IMPORTANT]
>為了確保您的應用程式已由商店正確分類，並可供 Windows Mixed Reality 客戶使用，您應該新增 **"Windows Mixed Reality"** 作為應用程式的其中一個「搜尋詞彙」 (您可以展開 [共用欄位] 區段) 來尋找搜尋字詞。

![將 Windows Mixed Reality 新增至搜尋詞彙](images/search-terms-800px.png)<br>
將 "Windows Mixed Reality" 新增至搜尋詞彙

## <a name="offering-a-free-trial-for-your-game-or-app"></a>為您的遊戲或應用程式提供免費試用

在購買 Windows Mixed Reality 的沉浸式耳機之前，許多消費者都不會有虛擬實境的體驗。 他們可能不知道要從密集遊戲獲得什麼預期，而且在沉浸式體驗中可能不熟悉自己的緩和閾值。 許多客戶也可以嘗試在未徽章為 [Windows Mixed Reality 電腦](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)的電腦上 Windows Mixed Reality 沉浸式耳機。 基於這些考慮，強烈建議您考慮為您的付費混合現實應用程式或遊戲提供 [免費試用](https://docs.microsoft.com/windows/uwp/publish/set-app-pricing-and-availability#free-trial) 。

## <a name="see-also"></a>另請參閱
* [混合實境](../discover/mixed-reality.md)
* [開發概觀](../develop/development.md)
* [應用程式檢視](../design/app-views.md)
* [瞭解混合現實的效能](../develop/platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md)
* [Unity 的效能建議](../develop/unity/performance-recommendations-for-unity.md)
* [測試 HoloLens 上的應用程式](../develop/platform-capabilities-and-apis/testing-your-app-on-hololens.md)
* [Windows Mixed Reality 最小電腦硬體相容性指導方針](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)
