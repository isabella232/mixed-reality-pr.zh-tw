---
title: 散發您的應用程式
description: 概述各種支援平臺和發佈存放區的不同散發選項。
author: hferrone
ms.author: v-hferrone
ms.date: 12/9/2020
ms.topic: article
keywords: HoloLens、Mixed Reality、沉浸式耳機、應用程式、uwp、提交、提交、篩選、中繼資料、系統需求、關鍵字、wack、認證、套件、appx、商品化
ms.openlocfilehash: b729bd65413587d3ad3b05bef495349b60a6fffd
ms.sourcegitcommit: 47a5c86b4694449c825902631777a9962a40e332
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/14/2021
ms.locfileid: "98215973"
---
# <a name="distributing-your-apps"></a>散發您的應用程式

![WMR 首頁中的 Floaty 鳥3D 應用程式 lancher](images/distribute-hero-image.png)

將您的應用程式帶入使用者或世界各地是最重要的，有時也是耗費，也就是任何開發工作的一部分。 我們簡化了一組資源的程式，這取決於最適合您或您小組的散發和部署案例。

[!INCLUDE[](includes/before-submission.md)]

## <a name="distribution-options"></a>散發選項

> [!IMPORTANT]
> * 如果您要與其他合作物件共用您的應用程式，您需要建立並提供 appx 檔案。 
>     * 如果您是使用應用程式安裝程式，也需要與使用者共用憑證。
> 
> * 如果您要與組織共用，您需要公司或學校帳戶，以及存取組織 [MDM (行動裝置管理) ](https://docs.microsoft.com/hololens/hololens-enroll-mdm) 基礎結構。  
>    * 如果您是共用合作物件，您必須是租使用者中的系統管理員，並使用 [Microsoft 端點管理員系統管理中心](https://docs.microsoft.com/mem/intune/apps/apps-deploy) 來讓應用程式可供使用。 另一個選項是與您的終端使用者共用 appx 檔案和應用程式相依性。
>    * 如果您是使用者，當您註冊共用組織的租使用者之後，應用程式會自動下載或可供下載。 

<table>
<colgroup>
    <col width="33%" />
    <col width="22%" />
    <col width="22%" />
    <col width="22%" />
</colgroup>
<tr>
    <td><strong>案例</strong></td>
    <td><strong>本機裝置安裝</strong></td>
    <td><strong>與任何人共用</strong></td>
    <td><strong>與組織共用</strong></td>
</tr>
<tr>
    <td><a href="https://docs.microsoft.com/hololens/app-deploy-app-installer"><strong>應用程式安裝程式</strong></td>
    <td>✔️</td>
    <td>✔️</td>
    <td>❌</td>
</tr>
<tr>
    <td><a href="https://docs.microsoft.com/hololens/app-deploy-app-installer"><strong>MDM-公司入口網站</strong></a></td>
    <td>❌</td>
    <td>❌</td>
    <td>✔️</td>
</tr>
<tr>
    <td><a href="https://docs.microsoft.com/hololens/app-deploy-intune"><strong>MDM-必要的應用程式安裝</strong></a></td>
    <td>❌</td>
    <td>❌</td>
    <td>✔️</td>
</tr>
<tr>
    <td><a href="submitting-an-app-to-the-microsoft-store.md"><strong>Microsoft Store</strong></a></td>
    <td>❌</td>
    <td>✔️</td>
    <td>✔️</td>
</tr>
<tr>
    <td><a href="https://docs.microsoft.com/hololens/app-deploy-store-business"><strong>商務用 Microsoft Store</strong></a></td>
    <td>❌</td>
    <td>❌</td>
    <td>✔️</td>
</tr>
<tr>
    <td><a href="https://docs.microsoft.com/hololens/app-deploy-provisioning-package"><strong>布建套件</strong></a></td>
    <td>✔️</td>
    <td>✔️</td>
    <td>✔️</td>
</tr>
<tr>
    <td>HoloLens 裝置無法使用<a href="#other-scenarios"><strong>自訂的 Win32 部署</strong></a> (-請參閱以下) </td>
    <td>✔️</td>
    <td>✔️</td>
    <td>❌</td>
</tr>
</table>

> [!IMPORTANT]
> 應用程式安裝程式目前不適用於受管理的裝置，或 (第1代) 裝置的 HoloLens。

## <a name="other-scenarios"></a>其他案例

* 您可以產生 Win32。EXE 檔案：使用來自 Unity 的電腦獨立組建目標進行 Win32 應用程式部署，包括流和遊戲通過。 一旦您擁有。EXE，您可以像平常一樣將應用程式提交至您選擇的平臺。 

* 如果您在離線時需要安裝 HoloLens 2 的應用程式，請參閱 [離線安全 HoloLens 2](https://docs.microsoft.com/hololens/hololens-common-scenarios-offline-secure) 指示，或透過布建套件安裝應用程式，而不需啟用開發人員模式。

* 您也可以將組建部署到您的裝置，並與其他已啟用開發人員模式的開發人員共用，方法是 [使用 Visual Studio 部署和偵錯工具，](../develop/platform-capabilities-and-apis/using-visual-studio.md) 或 [使用裝置入口網站安裝應用程式套件](../develop/platform-capabilities-and-apis/using-the-windows-device-portal.md#sideloading-applications)。

## <a name="see-also"></a>請參閱
* [從 Microsoft Store 尋找、安裝和卸載應用程式](https://docs.microsoft.com/hololens/holographic-store-apps)

