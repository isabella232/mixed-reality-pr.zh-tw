---
title: 建立全像攝影遠端處理的連線安全
description: 此頁面說明如何在使用全像的遠端功能時，建立安全的加密連線。
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 03/11/2020
ms.topic: article
keywords: HoloLens、遠端、全像攝影遠端
ms.openlocfilehash: 4006a317ed2ecfd7a1e67336a80a4e536d45e554
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2020
ms.locfileid: "91679244"
---
# <a name="establishing-a-secure-connection-with-holographic-remoting"></a>建立全像攝影遠端處理的連線安全

>[!IMPORTANT]
>本指南專為 HoloLens 2 上的全像攝影遠端所特有。

此頁面說明如何在使用全像的遠端功能時，建立安全的加密連線。

當您透過不安全的網路（例如開放式 WiFi 或網際網路）將內容串流處理至 HoloLens 2 時，強烈建議使用加密的連接。

>[!IMPORTANT]
>即使是使用受信任的本機 WiFi，也應考慮使用加密的連接。

若要能夠使用加密的連線，您必須同時執行[自訂播放](holographic-remoting-create-player.md)[程式和自訂遠端應用程式](holographic-remoting-create-host.md)。

加密是透過使用基礎平臺 TLS 執行來達成。

## <a name="basics-of-an-encrypted-connection"></a>加密連接的基本概念

您必須將下列物件實作為允許憑證交換。

>[!TIP]
>使用 c + +/Winrt 可以輕鬆地執行 WinRT 介面 [作者 api 與 c + +/WinRT](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/author-apis)章節會詳細說明這一點。

>[!IMPORTANT]
>```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl```NuGet 套件內的包含與安全連線相關的 API 詳細檔。

1) 憑證物件，需要執行 ```ICertificate``` 介面。

    * 透過方法傳回 pfx 憑證的二進位內容 ```GetCertificatePfx``` 。 與 .pfx 檔案的二進位內容相同。
    * 透過傳回憑證主體名稱 ```GetSubjectName``` 。
    * 透過傳回 pfx 密碼 ```GetPfxPassword``` 。 傳回未受保護 pfx 的空字串。

2) 憑證提供者，它會在 ```ICertificateProvider``` 透過方法要求時提供憑證，以提供憑證 ```GetCertificate``` 。

3) 執行介面的憑證驗證程式 ```ICertificateValidator``` 。 其工作是驗證傳入的憑證。
    * ```PerformSystemValidation``` ```true``` 當基礎平臺應該驗證傳入的憑證鏈時，方法應該會傳回，否則會傳回 ```false``` 。
    * ```ValidateCertificate``` 用戶端內容會呼叫以要求憑證驗證。 這個方法會接受憑證鏈 (，其中第一個憑證是主體憑證) 、建立連線的伺服器名稱，以及是否應該強制執行撤銷檢查。 如果已要求基礎系統驗證，則會提供系統驗證結果。 若要繼續處理，請 ```CertificateValidated``` 使用適當的結果，否則 ```Cancel``` 必須在傳遞的上呼叫取消驗證 ```ICertificateValidationCallback``` 。

此外，若要允許交換安全權杖，則必須執行下列物件。

1) 執行介面的驗證提供者 ```IAuthenticationProvider``` 。 ```GetToken```用戶端內容會呼叫其方法來要求權杖以進行用戶端驗證。 若要繼續 ```TokenReceived``` 提供驗證權杖，並繼續連接程式或 ```Cancel``` 取消處理常式，必須在傳遞的上呼叫 ```IAuthenticationProviderCallback``` 。
2) 執行介面的驗證接收者 ```IAuthenticationReceiver``` 。 其工作是驗證連入權杖。
    * ```GetRealm```方法應該會傳回驗證領域的名稱。
    * ```ValidateToken```伺服器網路內容會呼叫方法來要求驗證用戶端驗證權杖。 若要繼續呼叫 ```ValidationCompleted``` 驗證的信號完成或 ```Cancel``` 拒絕用戶端連接。 用戶端連接將會根據傳遞給的驗證結果來被確認或拒絕 ```ValidationCompleted``` 。 

一旦執行這些物件，就必須 ```ListenSecure``` 改為呼叫 ```Listen``` ，而 ```ConnectSecure``` 不是 ```Connect``` 在遠端內容和播放程式內容上呼叫。 ```ListenSecure``` 需要額外的憑證提供者和驗證接收者 ```Listen``` 。 ```ConnectSecure``` 需要額外的驗證提供者和憑證驗證程式 ```Connect``` 。

## <a name="see-also"></a>另請參閱
* [撰寫全像攝影遠端應用程式](holographic-remoting-create-host.md)
* [撰寫自訂全像攝影遠端播放應用程式](holographic-remoting-create-player.md)
* [全像遠端的疑難排解和限制](holographic-remoting-troubleshooting.md)
* [全像攝影遠端軟體授權條款](https://docs.microsoft.com//legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Microsoft 隱私權聲明](https://go.microsoft.com/fwlink/?LinkId=521839)
