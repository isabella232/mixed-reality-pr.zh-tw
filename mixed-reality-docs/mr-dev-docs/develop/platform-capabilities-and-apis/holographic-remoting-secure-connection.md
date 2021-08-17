---
title: 針對全像遠端功能啟用連接安全性
description: 此頁面說明如何設定全像遠端處理，以在播放程式和遠端應用程式之間使用加密和已驗證的連線。
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 12/01/2020
ms.topic: article
keywords: HoloLens、遠端、全像全像遠端、混合現實耳機、windows mixed reality 耳機、虛擬實境耳機、安全性、驗證、伺服器對用戶端
ms.openlocfilehash: 6ac5284bdf9e5984fcf091b6502fb62a494e4fe8
ms.sourcegitcommit: 820f2dfe98065298f6978a651f838de12620dd45
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/14/2021
ms.locfileid: "122184645"
---
# <a name="enabling-connection-security-for-holographic-remoting-c"></a>針對全像是 (c + +) 的全像遠端啟用連接安全性

>[!IMPORTANT]
>本指南專為 HoloLens 2 上的全像攝影遠端所特有。

此頁面可讓您概述全像攝影遠端的網路安全性。 您可以找到有關

* 全像攝影遠端的內容，以及您可能需要的安全性
* 根據不同使用案例的建議量值
* 在您的全像遠端處理解決方案中實施安全性

## <a name="holographic-remoting-security"></a>全像遠端處理安全性

全像網路的全像遠端交換資訊。 如果沒有任何安全性措施，在相同網路上敵人可能會危害通訊的完整性或存取機密資訊。

Windows 存放區中的範例應用程式和全像攝影遠端播放程式會停用安全性。 這樣做會讓範例更容易瞭解。 它也可協助您更快速地開始開發。

對於現場測試或生產環境，我們強烈建議您在全像遠端處理解決方案中啟用安全性。

全像全像是針對您的使用案例正確設定時，可提供下列保證：

* **真實性：** 播放程式和遠端應用程式都可以確保另一端是他們宣稱的身分
* **機密性：** 沒有任何協力廠商可以讀取播放程式與遠端應用程式之間交換的資訊
* **完整性：** player 和 remote 可以偵測到對其通訊的任何傳輸中變更

>[!IMPORTANT]
>若要能夠使用安全性功能，您必須使用[Windows Mixed Reality](holographic-remoting-create-remote-wmr.md)或[OpenXR](holographic-remoting-create-remote-openxr.md) api 來執行[自訂播放](holographic-remoting-create-player.md)程式和自訂遠端應用程式。

>[!NOTE]
> 從版本 [2.4.0](holographic-remoting-version-history.md#v2.4.0) 使用 [OpenXR API](../native/openxr.md) 的遠端應用程式可以建立。 如需如何在 OpenXR 環境中建立安全連線的總覽，請參閱 [下方](#secure-connection-using-the-openxr-api)。

## <a name="planning-the-security-implementation"></a>規劃安全性實行

當您在全像遠端執行時啟用安全性時，遠端程式庫會自動為透過網路交換的所有資料啟用加密和完整性檢查。

不過，確保適當的驗證需要一些額外的工作。 您需要執行的工作取決於您的使用案例，而本節的其餘部分則是要找出必要的步驟。

>[!IMPORTANT]
> 本文只能提供一般指引。 如果您不確定，請考慮諮詢安全性專家，以提供您使用案例的特定指引。

首先，有些術語：當描述網路連線時，將會使用 _用戶端_ 和 _伺服器_ 的條款。 伺服器是在已知端點位址上接聽連入連線的端，而用戶端則是連接到伺服器端點的一端。

>[!NOTE]
> 用戶端和伺服器角色並不會系結至應用程式是否扮演播放程式或遠端。 雖然範例中的玩傢俱有伺服器角色，但如果更適合您的使用案例，則可以輕鬆地反轉角色。

### <a name="planning-the-server-to-client-authentication"></a>規劃伺服器對用戶端驗證

伺服器使用數位憑證向用戶端證明其身分識別。 用戶端會在連接交握階段期間驗證服務器的憑證。 如果用戶端不信任伺服器，此時就會結束連接。

用戶端如何驗證伺服器憑證，以及可以使用哪些類型的伺服器憑證，取決於您的使用案例。

**使用案例1：** 伺服器主機名稱不是固定的，或伺服器完全不是由主機名稱所定址。

在此使用案例中， (或甚至可能) 對伺服器的主機名稱發出憑證並不實用。 建議您改為驗證憑證的指紋。 指紋和人為指紋一樣，可唯一識別憑證。

請務必將指紋傳達給超出範圍的用戶端。 這表示，您無法透過用於遠端處理的相同網路連接來傳送它。 相反地，您可以手動將它輸入用戶端的設定，或讓用戶端掃描 QR 代碼。

**使用案例2：** 您可以透過穩定的主機名稱來連接伺服器。

在此使用案例中，伺服器具有特定的主機名稱，而您知道此名稱不太可能變更。 然後，您可以使用發行至伺服器之主機名稱的憑證。 將根據主機名稱和憑證的信任鏈來建立信任。

如果您選擇此選項，用戶端必須事先知道伺服器的主機名稱和根憑證。

### <a name="planning-the-client-to-server-authentication"></a>規劃用戶端對伺服器驗證

用戶端會使用自由格式權杖來對伺服器進行驗證。 此權杖應該包含的內容將會再次取決於您的使用案例：

**使用案例1：** 您只需要確認用戶端應用程式的身分識別。

在此使用案例中，共用密碼可能已足夠。 這個秘密必須夠複雜，才能猜不到。

良好的共用密碼是隨機的 GUID，這是在伺服器和用戶端的設定中手動輸入的。 例如，您可以在 PowerShell 中使用命令，以建立一個 `New-Guid` 。

請確定此共用密碼永遠不會透過不安全的通道進行通訊。 遠端程式庫可確保共用密碼一律會加密傳送，而且只會傳送至信任的對等。

**使用案例2：** 您也需要確認用戶端應用程式使用者的身分識別。

共用的密碼將不足以涵蓋此使用案例。 相反地，您可以使用身分識別提供者所建立的權杖。 使用身分識別提供者的驗證工作流程看起來像這樣：

* 用戶端會對身分識別提供者進行授權，並要求權杖
* 身分識別提供者會產生權杖，並將它傳送至用戶端
* 用戶端會透過全像的遠端處理將此權杖傳送給伺服器
* 伺服器會根據身分識別提供者來驗證用戶端的權杖

身分識別提供者的其中一個範例是[Microsoft 身分識別平臺](/azure/active-directory/develop/)。

如同在先前的使用案例中，請確定這些權杖不會透過不安全的通道傳送或公開。

## <a name="implementing-holographic-remoting-security"></a>實現全像遠端處理安全性

請記住，如果您想要啟用連接安全性，就必須執行自訂遠端和播放機應用程式。 您可以使用提供的範例做為您自己應用程式的起點。

若要啟用安全性，請呼叫而不是 `ListenSecure()` `Listen()` ，而不是 `ConnectSecure()` `Connect()` 建立遠端連線。

這些呼叫需要您提供特定介面的實作為，以提供和驗證安全性相關資訊：

* 伺服器必須執行憑證提供者和驗證驗證程式
* 用戶端必須執行驗證提供者和憑證驗證程式。

所有介面都有一個要求您採取動作的函式，它會以參數的形式接收回呼物件。 使用這個物件，您就可以輕鬆地執行要求的非同步處理。 保留這個物件的參考，並在非同步動作完成時呼叫完成函式。 您可以從任何執行緒呼叫完成函數。

>[!TIP]
>使用 c + +/Winrt 可以輕鬆地執行 WinRT 介面 [作者 api 與 c + +/WinRT](/windows/uwp/cpp-and-winrt-apis/author-apis)章節會詳細說明這一點。

>[!IMPORTANT]
>`build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl`NuGet 套件內的會包含與安全連線相關的 API 詳細檔。

### <a name="implementing-a-certificate-provider"></a>執行憑證提供者

憑證提供者會提供伺服器應用程式與要使用的憑證。 此執行包含兩個部分：

1) 憑證物件，它會 `ICertificate` 執行介面：

    * `GetCertificatePfx()` 應傳回憑證存放區的二進位內容 `PKCS#12` 。 檔案 `.pfx` 包含 `PKCS#12` 資料，因此可以直接在這裡使用其內容。
    * `GetSubjectName()` 應傳回識別要使用之憑證的易記名稱。 如果未將易記名稱指派給憑證，此函式應該會傳回憑證的主體名稱。
    * `GetPfxPassword()` 應該會傳回開啟憑證存放區 (所需的密碼，如果沒有需要密碼) ，則為空字串。

2) 執行介面的憑證提供者 `ICertificateProvider` ：
    * `GetCertificate()` 應該會建立憑證物件，並呼叫回呼物件來將它傳回 `CertificateReceived()` 。

### <a name="implementing-an-authentication-validator"></a>執行驗證驗證程式

驗證驗證程式會接收用戶端所傳送的驗證權杖，並使用驗證結果回復。

執行介面，如下所示 `IAuthenticationReceiver` ：

* `GetRealm()` 應傳回驗證領域的名稱， (在遠端連線交握) 期間使用的 HTTP 領域。
* `ValidateToken()` 應驗證用戶端驗證權杖，並 `ValidationCompleted()` 使用驗證結果呼叫回呼物件。

### <a name="implementing-an-authentication-provider"></a>執行驗證提供者

驗證提供者會產生或取出要傳送至伺服器的驗證權杖。

執行介面，如下所示 `IAuthenticationProvider` ：

* `GetToken()` 應產生或取出要傳送的驗證權杖。 一旦權杖就緒，請 `TokenReceived()` 在回呼物件上呼叫方法。

### <a name="implementing-a-certificate-validator"></a>執行憑證驗證程式

憑證驗證程式會接收伺服器所傳送的憑證鏈，並判斷伺服器是否可信任。

若要驗證憑證，您可以使用基礎系統的驗證邏輯。 此系統驗證可以支援您自己的驗證邏輯，或將其取代為全部。 如果您在要求安全連線時未傳遞自己的憑證驗證程式，系統會自動使用系統驗證。

在 Windows 上，系統驗證將會檢查：

* 憑證鏈的完整性：憑證形成以受信任根憑證結尾的一致鏈
* 憑證有效性：伺服器的憑證在其有效時間範圍內，並且針對伺服器驗證發出
* 撤銷：尚未撤銷憑證
* 名稱相符：伺服器的主機名稱符合憑證發出的其中一個主機名稱

執行介面，如下所示 `ICertificateValidator` ：

 * `PerformSystemValidation()``true`如果應該執行如上所述的系統驗證，則應傳回。 在此情況下，系統驗證結果會以輸入的形式傳遞給 `ValidateCertificate()` 方法。
* `ValidateCertificate()` 應該驗證憑證鏈，然後 `CertificateValidated()` 在傳遞的回呼上呼叫最後的驗證結果。 這個方法會接受憑證鏈、建立連線的伺服器名稱，以及是否應該強制執行撤銷檢查。 如果憑證鏈包含多個憑證，則第一個是主體憑證。

>[!NOTE]
>如果您的使用案例需要不同形式的驗證 (請參閱上述) 的憑證使用案例 #1，完全略過系統驗證。 相反地，請使用任何可以處理以 DER 編碼的 x.509 憑證的 API 或程式庫，以解碼憑證鏈，並執行您的使用案例所需的檢查。

## <a name="secure-connection-using-the-openxr-api"></a>使用 OpenXR API 的安全連線

使用 [OPENXR API](../native/openxr.md) 時，所有安全連線相關的 API 都可作為 OpenXR 擴充功能的一部分 `XR_MSFT_holographic_remoting` 。

>[!IMPORTANT]
>To learn about the Holographic Remoting OpenXR extension API, check out the [specification](https://htmlpreview.github.io/?https://github.com/microsoft/MixedReality-HolographicRemoting-Samples/blob/master/remote_openxr/specification.html) which can be found in the [Holographic Remoting samples github repository](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).

使用 OpenXR 擴充功能的安全連線的重要元素 `XR_MSFT_holographic_remoting` 是下列回呼。
- `xrRemotingRequestAuthenticationTokenCallbackMSFT`、產生或抓取要傳送的驗證權杖。
- `xrRemotingValidateServerCertificateCallbackMSFT`，驗證憑證鏈。
- `xrRemotingValidateAuthenticationTokenCallbackMSFT`，驗證用戶端驗證 token。
- `xrRemotingRequestServerCertificateCallbackMSFT`，為伺服器應用程式提供要使用的憑證。

您可以透過和將這些回呼提供給遠端 OpenXR 執行時間 `xrRemotingSetSecureConnectionClientCallbacksMSFT` `xrRemotingSetSecureConnectionServerCallbacksMSFT` 。 此外，您必須透過結構或結構上的 secureConnection 參數來啟用安全連線， `XrRemotingConnectInfoMSFT` `XrRemotingListenInfoMSFT` 這取決於您使用 `xrRemotingConnectMSFT` 的是或 `xrRemotingListenMSFT` 。

此 API 與以 IDL 為基礎的 API 類似，此 API 是在實裡建的 [遠端安全性](#implementing-holographic-remoting-security)中所述。 不過，您應該提供回呼，而不是執行介面。 您可以在 [OpenXR 範例應用程式](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples)中找到詳細的範例。

## <a name="see-also"></a>另請參閱
* [全像遠端處理總覽](holographic-remoting-overview.md)
* [使用 Windows Mixed Reality api 撰寫全像遠端執行遠端應用程式](holographic-remoting-create-remote-wmr.md)
* [使用 OpenXR Api 撰寫全像遠端執行遠端應用程式](holographic-remoting-create-remote-openxr.md)
* [撰寫自訂全像攝影遠端播放應用程式](holographic-remoting-create-player.md)
* [全像遠端的疑難排解和限制](holographic-remoting-troubleshooting.md)
* [全像攝影遠端軟體授權條款](/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Microsoft 隱私權聲明](https://go.microsoft.com/fwlink/?LinkId=521839)