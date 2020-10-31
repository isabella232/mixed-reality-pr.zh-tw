---
title: 針對全像遠端功能啟用連接安全性
description: 此頁面說明如何設定全像遠端處理，以在播放程式和遠端應用程式之間使用加密和已驗證的連線。
author: markkeinz
ms.author: makei
ms.date: 10/29/2020
ms.topic: article
keywords: HoloLens、遠端、全像攝影遠端
ms.openlocfilehash: fcacac76e65fa884433afca9f568c5c0211dd570
ms.sourcegitcommit: 979967d6841d8fa64cf1d6cf3ae532b736ed3bd1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93102297"
---
# <a name="enabling-connection-security-for-holographic-remoting"></a><span data-ttu-id="b5e11-104">針對全像遠端功能啟用連接安全性</span><span class="sxs-lookup"><span data-stu-id="b5e11-104">Enabling connection security for Holographic Remoting</span></span>

>[!IMPORTANT]
><span data-ttu-id="b5e11-105">本指南專為 HoloLens 2 上的全像攝影遠端所特有。</span><span class="sxs-lookup"><span data-stu-id="b5e11-105">This guidance is specific to Holographic Remoting on HoloLens 2.</span></span>

<span data-ttu-id="b5e11-106">此頁面可讓您概述全像攝影遠端的網路安全性。</span><span class="sxs-lookup"><span data-stu-id="b5e11-106">This page gives you an overview of network security for Holographic Remoting.</span></span> <span data-ttu-id="b5e11-107">您可以找到有關</span><span class="sxs-lookup"><span data-stu-id="b5e11-107">You'll find information about</span></span>

* <span data-ttu-id="b5e11-108">全像攝影遠端的內容，以及您可能需要的安全性</span><span class="sxs-lookup"><span data-stu-id="b5e11-108">security in the context of Holographic Remoting and why you might need it</span></span>
* <span data-ttu-id="b5e11-109">根據不同使用案例的建議量值</span><span class="sxs-lookup"><span data-stu-id="b5e11-109">recommended measures based on different use cases</span></span>
* <span data-ttu-id="b5e11-110">在您的全像遠端處理解決方案中實施安全性</span><span class="sxs-lookup"><span data-stu-id="b5e11-110">implementing security in your Holographic Remoting solution</span></span>

## <a name="overview"></a><span data-ttu-id="b5e11-111">概觀</span><span class="sxs-lookup"><span data-stu-id="b5e11-111">Overview</span></span>

<span data-ttu-id="b5e11-112">全像網路的全像遠端交換資訊。</span><span class="sxs-lookup"><span data-stu-id="b5e11-112">Holographic Remoting exchanges information over a network.</span></span> <span data-ttu-id="b5e11-113">如果沒有任何安全性措施，在相同網路上敵人可能會危害通訊的完整性或存取機密資訊。</span><span class="sxs-lookup"><span data-stu-id="b5e11-113">If no security measures are in place, adversaries on the same network may compromise the integrity of the communication or access confidential information.</span></span>

<span data-ttu-id="b5e11-114">Windows 市集中的範例應用程式和全像全像遠端播放播放程式會停用安全性。</span><span class="sxs-lookup"><span data-stu-id="b5e11-114">The sample apps and the Holographic Remoting Player in the Windows Store come with security disabled.</span></span> <span data-ttu-id="b5e11-115">這樣做會讓範例更容易瞭解。</span><span class="sxs-lookup"><span data-stu-id="b5e11-115">Doing so makes the samples easier to understand.</span></span> <span data-ttu-id="b5e11-116">它也可協助您更快速地開始開發。</span><span class="sxs-lookup"><span data-stu-id="b5e11-116">It also helps you to get started more quickly with development.</span></span>

<span data-ttu-id="b5e11-117">不過，若要進行現場測試或生產環境，我們強烈建議在您的全像遠端處理解決方案中啟用安全性。</span><span class="sxs-lookup"><span data-stu-id="b5e11-117">For field testing or production use however, we strongly recommend enabling security in your Holographic Remoting solution.</span></span>

<span data-ttu-id="b5e11-118">全像全像是針對您的使用案例正確設定時，可提供下列保證：</span><span class="sxs-lookup"><span data-stu-id="b5e11-118">Security in Holographic Remoting, when set up correctly for your use case, gives you the following guarantees:</span></span>

* <span data-ttu-id="b5e11-119">**真實性：** 播放程式和遠端應用程式都可以確保另一端是他們宣稱的身分</span><span class="sxs-lookup"><span data-stu-id="b5e11-119">**Authenticity:** both player and remote app can be sure the other side is who they claim to be</span></span>
* <span data-ttu-id="b5e11-120">**機密性：** 沒有任何協力廠商可以讀取播放程式與遠端應用程式之間交換的資訊</span><span class="sxs-lookup"><span data-stu-id="b5e11-120">**Confidentiality:** no third party can read the information exchanged between player and remote app</span></span>
* <span data-ttu-id="b5e11-121">**完整性：** player 和 remote 可以偵測到對其通訊的任何傳輸中變更</span><span class="sxs-lookup"><span data-stu-id="b5e11-121">**Integrity:** player and remote can detect any in-transit changes to their communication</span></span>

>[!TIP]
><span data-ttu-id="b5e11-122">若要能夠使用安全性功能，您必須同時執行[自訂播放](holographic-remoting-create-player.md)[程式和自訂遠端應用程式](holographic-remoting-create-host.md)。</span><span class="sxs-lookup"><span data-stu-id="b5e11-122">To be able to use security features, you will need to implement both a [custom player](holographic-remoting-create-player.md) and a [custom remote app](holographic-remoting-create-host.md).</span></span>

## <a name="planning-the-security-implementation"></a><span data-ttu-id="b5e11-123">規劃安全性實行</span><span class="sxs-lookup"><span data-stu-id="b5e11-123">Planning the security implementation</span></span>

<span data-ttu-id="b5e11-124">當您在全像遠端執行時啟用安全性時，遠端程式庫會自動為透過網路交換的所有資料啟用加密和完整性檢查。</span><span class="sxs-lookup"><span data-stu-id="b5e11-124">When you enable security in Holographic Remoting, the remoting library will automatically enable encryption and integrity checks for all data exchanged over the network.</span></span>

<span data-ttu-id="b5e11-125">不過，確保適當的驗證需要一些額外的工作。</span><span class="sxs-lookup"><span data-stu-id="b5e11-125">Ensuring proper authentication requires some extra work though.</span></span> <span data-ttu-id="b5e11-126">您需要執行的工作取決於您的使用案例，而本節的其餘部分則是要找出必要的步驟。</span><span class="sxs-lookup"><span data-stu-id="b5e11-126">What exactly you need to do depends on your use case, and the rest of this section is about figuring out the necessary steps.</span></span>

>[!IMPORTANT]
> <span data-ttu-id="b5e11-127">本文只能提供一般指引。</span><span class="sxs-lookup"><span data-stu-id="b5e11-127">This article can only provide general guidance.</span></span> <span data-ttu-id="b5e11-128">如果您不確定，請考慮諮詢安全性專家，以提供您使用案例的特定指引。</span><span class="sxs-lookup"><span data-stu-id="b5e11-128">If you feel unsure, consider consulting a security expert that can give you guidance specific to your use case.</span></span>

<span data-ttu-id="b5e11-129">首先，有些術語：當描述網路連線時，將會使用 _用戶端_ 和 _伺服器_ 的條款。</span><span class="sxs-lookup"><span data-stu-id="b5e11-129">First some terminology: when describing network connections, the terms _client_ and _server_ will be used.</span></span> <span data-ttu-id="b5e11-130">伺服器是在已知端點位址上接聽連入連線的端，而用戶端則是連接到伺服器端點的一端。</span><span class="sxs-lookup"><span data-stu-id="b5e11-130">The server is the side listening for incoming connections on a known endpoint address, and the client is the one connecting to the server's endpoint.</span></span>

>[!NOTE]
> <span data-ttu-id="b5e11-131">用戶端和伺服器角色並不會系結至應用程式是否扮演播放程式或遠端。</span><span class="sxs-lookup"><span data-stu-id="b5e11-131">The client and and server roles are not tied to whether an app is acting as a player or as a remote.</span></span> <span data-ttu-id="b5e11-132">雖然範例中的玩傢俱有伺服器角色，但如果更適合您的使用案例，則可以輕鬆地反轉角色。</span><span class="sxs-lookup"><span data-stu-id="b5e11-132">While the samples have the player in the server role, it's easy to reverse the roles if it better fits your use case.</span></span>

### <a name="planning-the-server-to-client-authentication"></a><span data-ttu-id="b5e11-133">規劃伺服器對用戶端驗證</span><span class="sxs-lookup"><span data-stu-id="b5e11-133">Planning the server-to-client authentication</span></span>

<span data-ttu-id="b5e11-134">伺服器使用數位憑證向用戶端證明其身分識別。</span><span class="sxs-lookup"><span data-stu-id="b5e11-134">The server uses digital certificates to prove its identity to the client.</span></span> <span data-ttu-id="b5e11-135">用戶端會在連接交握階段期間驗證服務器的憑證。</span><span class="sxs-lookup"><span data-stu-id="b5e11-135">The client validates the server's certificate during the connection handshake phase.</span></span> <span data-ttu-id="b5e11-136">如果用戶端不信任伺服器，此時就會結束連接。</span><span class="sxs-lookup"><span data-stu-id="b5e11-136">If the client doesn't trust the server, it will end the connection at this point.</span></span>

<span data-ttu-id="b5e11-137">用戶端如何驗證伺服器憑證，以及可以使用哪些類型的伺服器憑證，取決於您的使用案例。</span><span class="sxs-lookup"><span data-stu-id="b5e11-137">How the client validates the server certificate, and what kinds of server certificates can be used, depends on your use case.</span></span>

<span data-ttu-id="b5e11-138">**使用案例1：** 伺服器主機名稱不是固定的，或伺服器完全不是由主機名稱所定址。</span><span class="sxs-lookup"><span data-stu-id="b5e11-138">**Use case 1:** The server hostname isn't fixed, or the server isn't addressed by host name at all.</span></span>

<span data-ttu-id="b5e11-139">在此使用案例中， (或甚至可能) 對伺服器的主機名稱發出憑證並不實用。</span><span class="sxs-lookup"><span data-stu-id="b5e11-139">In this use case, it isn't practical (or even possible) to issue a certificate for the server's host name.</span></span> <span data-ttu-id="b5e11-140">此處的建議是改為驗證憑證的指紋。</span><span class="sxs-lookup"><span data-stu-id="b5e11-140">The recommendation here is to validate the certificate's thumbprint instead.</span></span> <span data-ttu-id="b5e11-141">指紋和人為指紋一樣，可唯一識別憑證。</span><span class="sxs-lookup"><span data-stu-id="b5e11-141">Like a human fingerprint, the thumbprint uniquely identifies a certificate.</span></span>

<span data-ttu-id="b5e11-142">請務必將指紋傳達給超出範圍的用戶端。</span><span class="sxs-lookup"><span data-stu-id="b5e11-142">It's important to communicate the thumbprint to the client out-of-band.</span></span> <span data-ttu-id="b5e11-143">這表示，您無法透過用於遠端處理的相同網路連接來傳送它。</span><span class="sxs-lookup"><span data-stu-id="b5e11-143">That means, you can't send it over the same network connection that's used for remoting.</span></span> <span data-ttu-id="b5e11-144">相反地，您可以手動將它輸入用戶端的設定，或讓用戶端掃描 QR 代碼。</span><span class="sxs-lookup"><span data-stu-id="b5e11-144">Instead, you could manually enter it into the client's configuration, or to have the client scan a QR code.</span></span>

<span data-ttu-id="b5e11-145">**使用案例2：** 您可以透過穩定的主機名稱來連接伺服器。</span><span class="sxs-lookup"><span data-stu-id="b5e11-145">**Use case 2:** The server can be reached over a stable host name.</span></span>

<span data-ttu-id="b5e11-146">在此使用案例中，伺服器具有特定的主機名稱，而您知道此名稱不太可能變更。</span><span class="sxs-lookup"><span data-stu-id="b5e11-146">In this use case, the server has a specific host name, and you know this name isn't likely to change.</span></span> <span data-ttu-id="b5e11-147">然後，您可以使用發行至伺服器之主機名稱的憑證。</span><span class="sxs-lookup"><span data-stu-id="b5e11-147">You can then use a certificate issued to the server's host name.</span></span> <span data-ttu-id="b5e11-148">將根據主機名稱和憑證的信任鏈來建立信任。</span><span class="sxs-lookup"><span data-stu-id="b5e11-148">Trust will be established based on the host name and the certificate's chain of trust.</span></span>

<span data-ttu-id="b5e11-149">如果您選擇此選項，用戶端必須事先知道伺服器的主機名稱和根憑證。</span><span class="sxs-lookup"><span data-stu-id="b5e11-149">If you choose this option, the client needs to know the server's host name and the root certificate in advance.</span></span>

### <a name="planning-the-client-to-server-authentication"></a><span data-ttu-id="b5e11-150">規劃用戶端對伺服器驗證</span><span class="sxs-lookup"><span data-stu-id="b5e11-150">Planning the client-to-server authentication</span></span>

<span data-ttu-id="b5e11-151">用戶端會使用自由格式權杖來對伺服器進行驗證。</span><span class="sxs-lookup"><span data-stu-id="b5e11-151">Clients authenticate against the server using a free-form token.</span></span> <span data-ttu-id="b5e11-152">此權杖應該包含的內容將會再次取決於您的使用案例：</span><span class="sxs-lookup"><span data-stu-id="b5e11-152">What this token should contain will again depend on your use case:</span></span>

<span data-ttu-id="b5e11-153">**使用案例1：** 您只需要確認用戶端應用程式的身分識別。</span><span class="sxs-lookup"><span data-stu-id="b5e11-153">**Use case 1:** You only need to verify the client app's identity.</span></span>

<span data-ttu-id="b5e11-154">在此使用案例中，共用密碼可能已足夠。</span><span class="sxs-lookup"><span data-stu-id="b5e11-154">In this use case, a shared secret can be sufficient.</span></span> <span data-ttu-id="b5e11-155">這個秘密必須夠複雜，才能猜不到。</span><span class="sxs-lookup"><span data-stu-id="b5e11-155">This secret must be complex enough that it can't be guessed.</span></span>

<span data-ttu-id="b5e11-156">良好的共用密碼是隨機的 GUID，這是在伺服器和用戶端的設定中手動輸入的。</span><span class="sxs-lookup"><span data-stu-id="b5e11-156">A good shared secret is a random GUID, which is manually entered in both the server's and client's configuration.</span></span> <span data-ttu-id="b5e11-157">例如，您可以在 PowerShell 中使用命令，以建立一個 `New-Guid` 。</span><span class="sxs-lookup"><span data-stu-id="b5e11-157">To create one you can, for example, use the `New-Guid` command in PowerShell.</span></span>

<span data-ttu-id="b5e11-158">請確定此共用密碼永遠不會透過不安全的通道進行通訊。</span><span class="sxs-lookup"><span data-stu-id="b5e11-158">Make sure this shared secret is never communicated over insecure channels.</span></span> <span data-ttu-id="b5e11-159">遠端程式庫可確保共用密碼一律會加密傳送，而且只會傳送至信任的對等。</span><span class="sxs-lookup"><span data-stu-id="b5e11-159">The remoting library ensures that the shared secret is always sent encrypted, and only to trusted peers.</span></span>

<span data-ttu-id="b5e11-160">**使用案例2：** 您也需要確認用戶端應用程式使用者的身分識別。</span><span class="sxs-lookup"><span data-stu-id="b5e11-160">**Use case 2:** You also need to verify the identity of the client app's user.</span></span>

<span data-ttu-id="b5e11-161">共用的密碼將不足以涵蓋此使用案例。</span><span class="sxs-lookup"><span data-stu-id="b5e11-161">A shared secret won't be enough to cover this use case.</span></span> <span data-ttu-id="b5e11-162">相反地，您可以使用身分識別提供者所建立的權杖。</span><span class="sxs-lookup"><span data-stu-id="b5e11-162">Instead, you can use tokens created by an identity provider.</span></span> <span data-ttu-id="b5e11-163">使用身分識別提供者的驗證工作流程看起來像這樣：</span><span class="sxs-lookup"><span data-stu-id="b5e11-163">An authentication workflow using an identity provider would look like this:</span></span>

* <span data-ttu-id="b5e11-164">用戶端會對身分識別提供者進行授權，並要求權杖</span><span class="sxs-lookup"><span data-stu-id="b5e11-164">The client authorizes against the identity provider and requests a token</span></span>
* <span data-ttu-id="b5e11-165">身分識別提供者會產生權杖，並將它傳送至用戶端</span><span class="sxs-lookup"><span data-stu-id="b5e11-165">The identity provider generates a token and sends it to the client</span></span>
* <span data-ttu-id="b5e11-166">用戶端會透過全像的遠端處理將此權杖傳送給伺服器</span><span class="sxs-lookup"><span data-stu-id="b5e11-166">The client sends this token to the server through Holographic Remoting</span></span>
* <span data-ttu-id="b5e11-167">伺服器會根據身分識別提供者來驗證用戶端的權杖</span><span class="sxs-lookup"><span data-stu-id="b5e11-167">The server validates the client's token against the identity provider</span></span>

<span data-ttu-id="b5e11-168">身分識別提供者的其中一個範例是 [Microsoft 身分識別平臺](https://docs.microsoft.com/azure/active-directory/develop/)。</span><span class="sxs-lookup"><span data-stu-id="b5e11-168">One example of an identity provider is the [Microsoft identity platform](https://docs.microsoft.com/azure/active-directory/develop/).</span></span>

<span data-ttu-id="b5e11-169">如同在先前的使用案例中，請確定這些權杖不會透過不安全的通道傳送或公開。</span><span class="sxs-lookup"><span data-stu-id="b5e11-169">Like in the previous use case, make sure these tokens aren't sent through insecure channels or otherwise exposed.</span></span>

## <a name="implementing-holographic-remoting-security"></a><span data-ttu-id="b5e11-170">實現全像遠端處理安全性</span><span class="sxs-lookup"><span data-stu-id="b5e11-170">Implementing holographic remoting security</span></span>

<span data-ttu-id="b5e11-171">請記住，如果您想要啟用連接安全性，就必須執行自訂遠端和播放機應用程式。</span><span class="sxs-lookup"><span data-stu-id="b5e11-171">Remember that you need to implement custom remote and player apps if you want to enable connection security.</span></span> <span data-ttu-id="b5e11-172">您可以使用提供的範例做為您自己應用程式的起點。</span><span class="sxs-lookup"><span data-stu-id="b5e11-172">You can use the provided samples as starting points for your own apps.</span></span>

<span data-ttu-id="b5e11-173">若要啟用安全性，請呼叫而不是 `ListenSecure()` `Listen()` ，而不是 `ConnectSecure()` `Connect()` 建立遠端連線。</span><span class="sxs-lookup"><span data-stu-id="b5e11-173">To enable security, call `ListenSecure()` instead of `Listen()`, and `ConnectSecure()` instead of `Connect()` to establish the remoting connection.</span></span>

<span data-ttu-id="b5e11-174">這些呼叫需要您提供特定介面的實作為，以提供和驗證安全性相關資訊：</span><span class="sxs-lookup"><span data-stu-id="b5e11-174">These calls require you to provide implementations of certain interfaces for providing and validating security-related information:</span></span>

* <span data-ttu-id="b5e11-175">伺服器必須執行憑證提供者和驗證驗證程式</span><span class="sxs-lookup"><span data-stu-id="b5e11-175">The server needs to implement a certificate provider and an authentication validator</span></span>
* <span data-ttu-id="b5e11-176">用戶端必須執行驗證提供者和憑證驗證程式。</span><span class="sxs-lookup"><span data-stu-id="b5e11-176">The client needs to implement an authentication provider and a certificate validator.</span></span>

<span data-ttu-id="b5e11-177">所有介面都有一個要求您採取動作的函式，它會以參數的形式接收回呼物件。</span><span class="sxs-lookup"><span data-stu-id="b5e11-177">All interfaces have a function requesting you to take action, which receives a callback object as parameter.</span></span> <span data-ttu-id="b5e11-178">使用這個物件，您就可以輕鬆地執行要求的非同步處理。</span><span class="sxs-lookup"><span data-stu-id="b5e11-178">Using this object, you can easily implement asynchronous handling of the request.</span></span> <span data-ttu-id="b5e11-179">保留這個物件的參考，並在非同步動作完成時呼叫完成函式。</span><span class="sxs-lookup"><span data-stu-id="b5e11-179">Keep a reference to this object, and call the completion function when the asynchronous action is complete.</span></span> <span data-ttu-id="b5e11-180">您可以從任何執行緒呼叫完成函數。</span><span class="sxs-lookup"><span data-stu-id="b5e11-180">The completion function may be called from any thread.</span></span>

>[!TIP]
><span data-ttu-id="b5e11-181">使用 c + +/Winrt 可以輕鬆地執行 WinRT 介面</span><span class="sxs-lookup"><span data-stu-id="b5e11-181">Implementing WinRT interfaces can easily be done using C++/WinRT.</span></span> <span data-ttu-id="b5e11-182">[作者 api 與 c + +/WinRT](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/author-apis)章節會詳細說明這一點。</span><span class="sxs-lookup"><span data-stu-id="b5e11-182">The [Author APIs with C++/WinRT](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/author-apis) chapter describes this in detail.</span></span>

>[!IMPORTANT]
><span data-ttu-id="b5e11-183">`build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl`NuGet 套件內的包含與安全連線相關的 API 詳細檔。</span><span class="sxs-lookup"><span data-stu-id="b5e11-183">The `build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl` inside the NuGet package contains detailed documentation for the API related to secure connections.</span></span>

### <a name="implementing-a-certificate-provider"></a><span data-ttu-id="b5e11-184">執行憑證提供者</span><span class="sxs-lookup"><span data-stu-id="b5e11-184">Implementing a certificate provider</span></span>

<span data-ttu-id="b5e11-185">憑證提供者會提供伺服器應用程式與要使用的憑證。</span><span class="sxs-lookup"><span data-stu-id="b5e11-185">Certificate providers supply the server application with the certificate to use.</span></span> <span data-ttu-id="b5e11-186">此執行包含兩個部分：</span><span class="sxs-lookup"><span data-stu-id="b5e11-186">The implementation consists of two parts:</span></span>

1) <span data-ttu-id="b5e11-187">憑證物件，它會 `ICertificate` 執行介面：</span><span class="sxs-lookup"><span data-stu-id="b5e11-187">A certificate object, which implements the `ICertificate` interface:</span></span>

    * <span data-ttu-id="b5e11-188">`GetCertificatePfx()` 應傳回憑證存放區的二進位內容 `PKCS#12` 。</span><span class="sxs-lookup"><span data-stu-id="b5e11-188">`GetCertificatePfx()` should return the binary contents of a `PKCS#12` certificate store.</span></span> <span data-ttu-id="b5e11-189">檔案 `.pfx` 包含 `PKCS#12` 資料，因此可以直接在這裡使用其內容。</span><span class="sxs-lookup"><span data-stu-id="b5e11-189">A `.pfx` file contains `PKCS#12` data, so its contents can be used directly here.</span></span>
    * <span data-ttu-id="b5e11-190">`GetSubjectName()` 應傳回識別要使用之憑證的易記名稱。</span><span class="sxs-lookup"><span data-stu-id="b5e11-190">`GetSubjectName()` should return the friendly name that identifies the certificate to use.</span></span> <span data-ttu-id="b5e11-191">如果未將易記名稱指派給憑證，此函式應該會傳回憑證的主體名稱。</span><span class="sxs-lookup"><span data-stu-id="b5e11-191">If no friendly name is assigned to the certificate, this function should return the certificate's subject name.</span></span>
    * <span data-ttu-id="b5e11-192">`GetPfxPassword()` 應該會傳回開啟憑證存放區 (所需的密碼，如果沒有需要密碼) ，則為空字串。</span><span class="sxs-lookup"><span data-stu-id="b5e11-192">`GetPfxPassword()` should return the password required to open the certificate store (or an empty string if no password is required).</span></span>

2) <span data-ttu-id="b5e11-193">執行介面的憑證提供者 `ICertificateProvider` ：</span><span class="sxs-lookup"><span data-stu-id="b5e11-193">A certificate provider implementing the `ICertificateProvider` interface:</span></span>
    * <span data-ttu-id="b5e11-194">`GetCertificate()` 應該會建立憑證物件，並呼叫回呼物件來將它傳回 `CertificateReceived()` 。</span><span class="sxs-lookup"><span data-stu-id="b5e11-194">`GetCertificate()` should construct a certificate object and return it by calling `CertificateReceived()` on the callback object.</span></span>

### <a name="implementing-an-authentication-validator"></a><span data-ttu-id="b5e11-195">執行驗證驗證程式</span><span class="sxs-lookup"><span data-stu-id="b5e11-195">Implementing an authentication validator</span></span>

<span data-ttu-id="b5e11-196">驗證驗證程式會接收用戶端所傳送的驗證權杖，並使用驗證結果回復。</span><span class="sxs-lookup"><span data-stu-id="b5e11-196">Authentication validators receive the authentication token sent by the client, and answer back with the validation result.</span></span>

<span data-ttu-id="b5e11-197">執行介面，如下所示 `IAuthenticationReceiver` ：</span><span class="sxs-lookup"><span data-stu-id="b5e11-197">Implement the `IAuthenticationReceiver` interface as follows:</span></span>

* <span data-ttu-id="b5e11-198">`GetRealm()` 應傳回驗證領域的名稱， (在遠端連線交握) 期間使用的 HTTP 領域。</span><span class="sxs-lookup"><span data-stu-id="b5e11-198">`GetRealm()` should return the name of the authentication realm (an HTTP realm  used during the remoting connection handshake).</span></span>
* <span data-ttu-id="b5e11-199">`ValidateToken()` 應驗證用戶端驗證權杖，並 `ValidationCompleted()` 使用驗證結果呼叫回呼物件。</span><span class="sxs-lookup"><span data-stu-id="b5e11-199">`ValidateToken()` should validate the client authentication token and call `ValidationCompleted()` on the callback object with the validation result.</span></span>

### <a name="implementing-an-authentication-provider"></a><span data-ttu-id="b5e11-200">執行驗證提供者</span><span class="sxs-lookup"><span data-stu-id="b5e11-200">Implementing an authentication provider</span></span>

<span data-ttu-id="b5e11-201">驗證提供者會產生或取出要傳送至伺服器的驗證權杖。</span><span class="sxs-lookup"><span data-stu-id="b5e11-201">Authentication providers generate or retrieve the authentication token to be sent to the server.</span></span>

<span data-ttu-id="b5e11-202">執行介面，如下所示 `IAuthenticationProvider` ：</span><span class="sxs-lookup"><span data-stu-id="b5e11-202">Implement the `IAuthenticationProvider` interface as follows:</span></span>

* <span data-ttu-id="b5e11-203">`GetToken()` 應產生或取出要傳送的驗證權杖。</span><span class="sxs-lookup"><span data-stu-id="b5e11-203">`GetToken()` should generate or retrieve the authentication token to be sent.</span></span> <span data-ttu-id="b5e11-204">一旦權杖就緒，請 `TokenReceived()` 在回呼物件上呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="b5e11-204">Once the token is ready, call the `TokenReceived()` method on the callback object.</span></span>

### <a name="implementing-a-certificate-validator"></a><span data-ttu-id="b5e11-205">執行憑證驗證程式</span><span class="sxs-lookup"><span data-stu-id="b5e11-205">Implementing a certificate validator</span></span>

<span data-ttu-id="b5e11-206">憑證驗證程式會接收伺服器所傳送的憑證鏈，並判斷伺服器是否可信任。</span><span class="sxs-lookup"><span data-stu-id="b5e11-206">Certificate validators receive the certificate chain sent by the server and determine whether the server can be trusted.</span></span>

<span data-ttu-id="b5e11-207">若要驗證憑證，您可以使用基礎系統的驗證邏輯。</span><span class="sxs-lookup"><span data-stu-id="b5e11-207">To validate certificates, you can use the validation logic of the underlying system.</span></span> <span data-ttu-id="b5e11-208">此系統驗證可以支援您自己的驗證邏輯，或將其取代為全部。</span><span class="sxs-lookup"><span data-stu-id="b5e11-208">This system validation can either support your own validation logic, or replace it altogether.</span></span> <span data-ttu-id="b5e11-209">如果您在要求安全連線時未傳遞自己的憑證驗證程式，系統會自動使用系統驗證。</span><span class="sxs-lookup"><span data-stu-id="b5e11-209">If you don't pass your own certificate validator when requesting a secure connection, system validation will be used automatically.</span></span>

<span data-ttu-id="b5e11-210">在 Windows 中，系統驗證將會檢查：</span><span class="sxs-lookup"><span data-stu-id="b5e11-210">On Windows, the system validation will check for:</span></span>

* <span data-ttu-id="b5e11-211">憑證鏈的完整性：憑證形成以受信任根憑證結尾的一致鏈</span><span class="sxs-lookup"><span data-stu-id="b5e11-211">Integrity of the certificate chain: the certificates form a consistent chain that ends at a trusted root certificate</span></span>
* <span data-ttu-id="b5e11-212">憑證有效性：伺服器的憑證在其有效時間範圍內，並基於伺服器驗證的目的發出</span><span class="sxs-lookup"><span data-stu-id="b5e11-212">Certificate validity: the server's certificate is within its validity timespan, and is issued for the purpose of server authentication</span></span>
* <span data-ttu-id="b5e11-213">撤銷：尚未撤銷憑證</span><span class="sxs-lookup"><span data-stu-id="b5e11-213">Revocation: The certificate hasn't been revoked</span></span>
* <span data-ttu-id="b5e11-214">名稱相符：伺服器的主機名稱符合憑證發出的其中一個主機名稱</span><span class="sxs-lookup"><span data-stu-id="b5e11-214">Name match: The host name of the server matches one of the host names the certificate was issued for</span></span>

<span data-ttu-id="b5e11-215">執行介面，如下所示 `ICertificateValidator` ：</span><span class="sxs-lookup"><span data-stu-id="b5e11-215">Implement the `ICertificateValidator` interface as follows:</span></span>

 * <span data-ttu-id="b5e11-216">`PerformSystemValidation()``true`如果應該執行如上所述的系統驗證，則應傳回。</span><span class="sxs-lookup"><span data-stu-id="b5e11-216">`PerformSystemValidation()` should return `true` if a system validation as described above should be performed.</span></span> <span data-ttu-id="b5e11-217">在此情況下，系統驗證結果會以輸入的形式傳遞給 `ValidateCertificate()` 方法。</span><span class="sxs-lookup"><span data-stu-id="b5e11-217">In this case, the system validation result is passed as an input to the `ValidateCertificate()` method.</span></span>
* <span data-ttu-id="b5e11-218">`ValidateCertificate()` 應該驗證憑證鏈，然後 `CertificateValidated()` 在傳遞的回呼上呼叫最後的驗證結果。</span><span class="sxs-lookup"><span data-stu-id="b5e11-218">`ValidateCertificate()` should validate the certificate chain and then call `CertificateValidated()` on the passed callback with the final validation result.</span></span> <span data-ttu-id="b5e11-219">這個方法會接受憑證鏈、建立連線的伺服器名稱，以及是否應該強制執行撤銷檢查。</span><span class="sxs-lookup"><span data-stu-id="b5e11-219">This method accepts the certificate chain, the name of the server the connection is being established with, and whether a revocation check should be forced.</span></span> <span data-ttu-id="b5e11-220">如果憑證鏈包含多個憑證，則第一個是主體憑證。</span><span class="sxs-lookup"><span data-stu-id="b5e11-220">If the certificate chain contains multiple certificates, the first one is the subject certificate.</span></span>

>[!NOTE]
><span data-ttu-id="b5e11-221">如果您的使用案例需要不同形式的驗證 (請參閱上述) 的憑證使用案例 #1，完全略過系統驗證。</span><span class="sxs-lookup"><span data-stu-id="b5e11-221">If your use case requires a different form of validation (see certificate use case #1 above), bypass system validation entirely.</span></span> <span data-ttu-id="b5e11-222">相反地，請使用任何可以處理以 DER 編碼的 x.509 憑證的 API 或程式庫，以解碼憑證鏈，並執行您的使用案例所需的檢查。</span><span class="sxs-lookup"><span data-stu-id="b5e11-222">Instead, use any API or library that can handle DER-encoded X.509 certificates to decode the certificate chain and perform the checks needed for your use case.</span></span>

## <a name="see-also"></a><span data-ttu-id="b5e11-223">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b5e11-223">See Also</span></span>
* [<span data-ttu-id="b5e11-224">撰寫全像攝影遠端應用程式</span><span class="sxs-lookup"><span data-stu-id="b5e11-224">Writing a Holographic Remoting remote app</span></span>](holographic-remoting-create-host.md)
* [<span data-ttu-id="b5e11-225">撰寫自訂全像攝影遠端播放應用程式</span><span class="sxs-lookup"><span data-stu-id="b5e11-225">Writing a custom Holographic Remoting player app</span></span>](holographic-remoting-create-player.md)
* [<span data-ttu-id="b5e11-226">全像遠端的疑難排解和限制</span><span class="sxs-lookup"><span data-stu-id="b5e11-226">Holographic Remoting troubleshooting and limitations</span></span>](holographic-remoting-troubleshooting.md)
* [<span data-ttu-id="b5e11-227">全像攝影遠端軟體授權條款</span><span class="sxs-lookup"><span data-stu-id="b5e11-227">Holographic Remoting software license terms</span></span>](https://docs.microsoft.com//legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [<span data-ttu-id="b5e11-228">Microsoft 隱私權聲明</span><span class="sxs-lookup"><span data-stu-id="b5e11-228">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)
