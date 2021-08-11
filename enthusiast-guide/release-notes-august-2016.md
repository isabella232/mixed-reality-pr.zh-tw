---
title: 版本資訊 - 2016 年 8 月
description: 請隨時掌握 Windows 10 適用于2016年秋季發行版本的 HoloLens 版本資訊。
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens，版本資訊，os，平臺，功能，商用套件
ms.openlocfilehash: 2cb6153877b27ce0e1260696447bd4c5c851c6f00a20a7889b855c5646e8871f
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2021
ms.locfileid: "115202454"
---
# <a name="release-notes---august-2016"></a>版本資訊 - 2016 年 8 月

HoloLens 團隊正在聆聽來自 Windows 測試人員計畫開發人員的意見反應，以排定工作的優先順序。 繼續透過意見反應中樞、[開發人員論壇](https://forums.hololens.com) [ @HoloLens 和 Twitter ](https://twitter.com/hololens)[提供意見](/windows/mixed-reality/give-us-feedback)反應給我們。 隨著 Windows 10 在年度的更新中，HoloLens 的團隊很高興能更能改善全像全像全像全像全像全像全像 在這項更新中，我們將焦點放在企業要求的主要修正、改進和推出功能，並可在 Microsoft HoloLens Commercial Suite 中使用。

**最新版本：** Windows 2016 年8月更新 (**10.0.14393.0**，Windows 10 周年版) 

>[!VIDEO https://www.youtube.com/embed/tNd0e2CiAkE]

若要 [更新為最新版本](/windows/mixed-reality/updating-hololens)，請開啟 *設定* 應用程式，移至 [*更新 & 安全性*]，然後選取 [*檢查更新*] 按鈕。

## <a name="new-features"></a>新功能

**附加至進程的調試** 程式 HoloLens 現在支援附加至進程的偵錯工具。 您可以使用 Visual Studio 2015 Update 3 連接到 HoloLens 上執行的應用程式，並[開始進行調試](/windows/mixed-reality/develop/platform-capabilities-and-apis/using-visual-studio#debugging-an-installed-or-running-app)程式。 這種運作方式不需要從 Visual Studio 專案進行部署。

**更新 HoloLens Emulator** 我們也發行了 HoloLens Emulator 的更新版本。

**遊戲台支援** 您現在可以將藍牙 gamepads 與 HoloLens 配對！ 新發行的 Xbox 無線控制器 S 功能藍牙的功能，可用來播放您最愛的遊戲和應用程式。 必須先套用[控制器更新](https://support.xbox.com/xbox-one/accessories/update-controller-for-stereo-headset-adapter)，才能將 Xbox 無線控制器與 HoloLens 連線。 [XInput](/windows/win32/xinput/xinput-game-controller-apis-portal)和 Windows 支援 Xbox 無線控制器 S [。遊戲：輸入](/uwp/api/Windows.Gaming.Input)api。 您可以透過 Windows 存取更多藍牙控制器模型[。遊戲。輸入](/uwp/api/Windows.Gaming.Input)API。

## <a name="improvements-and-fixes"></a>改良功能與修正

我們會與其余的 Windows 10 周年更新進行同步處理，因此除了 HoloLens 的特定修正之外，您還可以從 Windows 更新獲得最高的效能，以提升平臺的可靠性和效能。 您的意見反應對於發行中的修正具有高度價值和優先。

我們已改善下列體驗：
* 登入體驗。
* 工作場所聯結。
* 裝置電源狀態轉換的電源效率。
* 混合現實的穩定性。
* 藍牙連線能力的可靠性
* 多個應用程式案例中的全息圖持續性。

我們已修正下列問題：
* Visual Studio 分析工具和圖形偵錯工具無法連接。
* 相片 & 檔不會顯示在裝置入口網站的 [檔案瀏覽器] 中。
* 當游標放在調整模式時，應用程式行可以閃爍。
* 當處於調整模式時，眼睛的點游標會變更為4箭號的游標。
* 「嗨 Cortana 播放音樂」未啟動 Groove。
* 在上一次更新之後，「Go Home」就不會正確地顯示釘選面板。

## <a name="introducing-microsoft-hololens-commercial-suite"></a>Microsoft HoloLens Commercial Suite 簡介

Microsoft HoloLens Commercial Suite 已準備好進行企業部署。 我們為早期商務夥伴新增了數個高度要求的 [商業功能](/windows/mixed-reality/commercial-features) 。

請洽詢您的當地 Microsoft 帳戶管理員，購買 Microsoft HoloLens Commercial Suite。

### <a name="key-commercial-features"></a>重要的商業功能 

* **Kiosk 模式。** 使用 HoloLens kiosk 模式時，您可以限制要執行的應用程式，以啟用示範或展示體驗。<br>
  ![在 kiosk 模式中，HoloLens 直接在您選擇的應用程式中啟動。](images/201608-kioskmode-400px.png)
* **適用于 HoloLens 的行動裝置管理 (MDM) 。** 您的 IT 部門可以使用 Microsoft Intune 之類的解決方案，同時管理多部 HoloLens 裝置。 您可以管理設定、選取要安裝的應用程式，以及設定專為組織需求量身打造的安全性設定。<br>
  ![HoloLens 上的行動裝置管理可提供跨多個裝置的企業級裝置管理。](images/201608-enterprisemanagement-400px.png)
* **Windows商務更新。** 裝置的受控作業系統更新和長期維護分支的支援。
* **資料安全性。** HoloLens 上啟用 BitLocker 資料加密，以提供與任何其他 Windows 裝置相同等級的安全性保護。
* **公司存取。** 您組織中的任何人都可以透過 HoloLens 上的虛擬私人網路，從遠端連線到公司網路。 HoloLens 也可以存取需要認證的 Wi-Fi 網路。
* **商務用 Microsoft Store。** 您的 IT 部門也可以設定企業私用存放區，其中只包含公司的應用程式，以符合您的特定 HoloLens 使用方式。 安全地將企業軟體散發給選定的企業使用者群組。

### <a name="development-edition-vs-commercial-suite"></a>開發版與商用套件

<table>
<tr>
<th>功能</th><th>Development 版</th><th>商業套件</th>
</tr><tr>
<td>裝置加密 (Bitlocker) </td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>虛擬私人網路 (VPN)</td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td><a href="/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-windows-device-portal#kiosk-mode">Kiosk 模式</a></td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<th colspan="3" style="text-align: left;"> 管理和部署</th>
</tr><tr>
<td>行動裝置管理 (MDM)</td><td style="text-align: center;"></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>封鎖取消註冊的功能</td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>以憑證為基礎的公司 Wi-Fi 存取</td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Microsoft Store (取用者) </td><td style="text-align: center;">消費者</td><td style="text-align: center;">透過 MDM 篩選</td>
</tr><tr>
<td><a href="/microsoft-store/working-with-line-of-business-apps">Business Store 入口網站</a></td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<th colspan="3" style="text-align: left;"> 安全性及身分識別</th>
</tr><tr>
<td>使用 Azure Active Directory (AAD) 登入</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>使用 Microsoft 帳戶登入 (MSA) </td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>使用 PIN 解除鎖定的新一代認證</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td><a href="/windows-hardware/design/device-experiences/oem-secure-boot">安全開機</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<th colspan="3" style="text-align: left;"> 服務與支援</th>
</tr><tr>
<td>系統自動更新到達時</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td><a href="/windows/deployment/update/waas-manage-updates-wufb">Windows Update for Business</a></td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>長期維護分支</td><td></td><td style="text-align: center;">✔️</td>
</tr>
</table>

## <a name="prior-release-notes"></a>先前的版本資訊
* [版本資訊 - 2016 年 5 月](release-notes-may-2016.md)
* [版本資訊 - 2016 年 3 月](release-notes-march-2016.md)

## <a name="see-also"></a>另請參閱
* [HoloLens 的已知問題](/windows/mixed-reality/hololens-known-issues)
* [商業功能](/windows/mixed-reality/commercial-features)
* [安裝工具](/windows/mixed-reality/develop/install-the-tools)
* [使用 HoloLens 模擬器](/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-hololens-emulator)