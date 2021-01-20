---
title: 散發您的應用程式
description: 概述各種支援平臺和發佈存放區的不同散發選項。
author: hferrone
ms.author: v-hferrone
ms.date: 12/9/2020
ms.topic: article
keywords: HoloLens、Mixed Reality、沉浸式耳機、應用程式、uwp、提交、提交、篩選、中繼資料、系統需求、關鍵字、wack、認證、套件、appx、商品化
ms.openlocfilehash: eb06ff46be6fbe6e480f9b43fa7f23ee47982192
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/20/2021
ms.locfileid: "98582855"
---
# <a name="distributing-your-apps"></a><span data-ttu-id="29bf6-104">散發您的應用程式</span><span class="sxs-lookup"><span data-stu-id="29bf6-104">Distributing your apps</span></span>

![WMR 首頁中的 Floaty 鳥3D 應用程式 lancher](images/distribute-hero-image.png)

<span data-ttu-id="29bf6-106">將您的應用程式帶入使用者或世界各地是最重要的，有時也是耗費，也就是任何開發工作的一部分。</span><span class="sxs-lookup"><span data-stu-id="29bf6-106">Getting your apps into the hands of your users or out into the world is the most important, and sometimes painstaking, part of any development effort.</span></span> <span data-ttu-id="29bf6-107">我們簡化了一組資源的程式，這取決於最適合您或您小組的散發和部署案例。</span><span class="sxs-lookup"><span data-stu-id="29bf6-107">We've simplified the process into a set of resources, which depend on the distribution and deployment scenario that's best suited for you or your team.</span></span>

[!INCLUDE[](includes/before-submission.md)]

## <a name="distribution-options"></a><span data-ttu-id="29bf6-108">散發選項</span><span class="sxs-lookup"><span data-stu-id="29bf6-108">Distribution options</span></span>

> [!IMPORTANT]
> * <span data-ttu-id="29bf6-109">如果您要與其他合作物件共用您的應用程式，您需要建立並提供 appx 檔案。</span><span class="sxs-lookup"><span data-stu-id="29bf6-109">If you're sharing your app with another party, you need to build and supply the appx file.</span></span> 
>     * <span data-ttu-id="29bf6-110">如果您是使用應用程式安裝程式，也需要與使用者共用憑證。</span><span class="sxs-lookup"><span data-stu-id="29bf6-110">If you're using App Installer, you'll also need to share the certificate with the user.</span></span>
> 
> * <span data-ttu-id="29bf6-111">如果您要與組織共用，您需要公司或學校帳戶，以及存取組織 [MDM (行動裝置管理) ](/hololens/hololens-enroll-mdm) 基礎結構。</span><span class="sxs-lookup"><span data-stu-id="29bf6-111">If you're sharing with an organization, you need a work or school account and access to the organizations [MDM (Mobile Device Management)](/hololens/hololens-enroll-mdm) infrastructure.</span></span>  
>    * <span data-ttu-id="29bf6-112">如果您是共用合作物件，您必須是租使用者中的系統管理員，並使用 [Microsoft 端點管理員系統管理中心](/mem/intune/apps/apps-deploy) 來讓應用程式可供使用。</span><span class="sxs-lookup"><span data-stu-id="29bf6-112">If you're the sharing party, you need to be an Admin in your tenant and use the [Microsoft Endpoint Manager admin center](/mem/intune/apps/apps-deploy) to make the app available.</span></span> <span data-ttu-id="29bf6-113">另一個選項是與您的終端使用者共用 appx 檔案和應用程式相依性。</span><span class="sxs-lookup"><span data-stu-id="29bf6-113">Another option is to share the appx file and the app dependencies with your end user.</span></span>
>    * <span data-ttu-id="29bf6-114">如果您是使用者，當您註冊共用組織的租使用者之後，應用程式會自動下載或可供下載。</span><span class="sxs-lookup"><span data-stu-id="29bf6-114">If you're the end user, the app will either automatically download or be available for download once you enroll with the sharing organization's tenant.</span></span> 

<table>
<colgroup>
    <col width="33%" />
    <col width="22%" />
    <col width="22%" />
    <col width="22%" />
</colgroup>
<tr>
    <td><span data-ttu-id="29bf6-115"><strong>案例</strong></span><span class="sxs-lookup"><span data-stu-id="29bf6-115"><strong>Scenario</strong></span></span></td>
    <td><span data-ttu-id="29bf6-116"><strong>本機裝置安裝</strong></span><span class="sxs-lookup"><span data-stu-id="29bf6-116"><strong>Local device installs</strong></span></span></td>
    <td><span data-ttu-id="29bf6-117"><strong>與任何人共用</strong></span><span class="sxs-lookup"><span data-stu-id="29bf6-117"><strong>Share with anyone</strong></span></span></td>
    <td><span data-ttu-id="29bf6-118"><strong>與組織共用</strong></span><span class="sxs-lookup"><span data-stu-id="29bf6-118"><strong>Share with an organization</strong></span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="29bf6-119"><a href="https://docs.microsoft.com/hololens/app-deploy-app-installer"><strong>應用程式安裝程式</strong></span><span class="sxs-lookup"><span data-stu-id="29bf6-119"><a href="https://docs.microsoft.com/hololens/app-deploy-app-installer"><strong>App Installer</strong></span></span></td>
    <td><span data-ttu-id="29bf6-120">✔️</span><span class="sxs-lookup"><span data-stu-id="29bf6-120">✔️</span></span></td>
    <td><span data-ttu-id="29bf6-121">✔️</span><span class="sxs-lookup"><span data-stu-id="29bf6-121">✔️</span></span></td>
    <td>❌</td>
</tr>
<tr>
    <td><span data-ttu-id="29bf6-122"><a href="/hololens/app-deploy-app-installer"><strong>MDM-公司入口網站</strong></a></span><span class="sxs-lookup"><span data-stu-id="29bf6-122"><a href="/hololens/app-deploy-app-installer"><strong>MDM - Company Portal</strong></a></span></span></td>
    <td>❌</td>
    <td>❌</td>
    <td><span data-ttu-id="29bf6-123">✔️</span><span class="sxs-lookup"><span data-stu-id="29bf6-123">✔️</span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="29bf6-124"><a href="/hololens/app-deploy-intune"><strong>MDM-必要的應用程式安裝</strong></a></span><span class="sxs-lookup"><span data-stu-id="29bf6-124"><a href="/hololens/app-deploy-intune"><strong>MDM - Required App Install</strong></a></span></span></td>
    <td>❌</td>
    <td>❌</td>
    <td><span data-ttu-id="29bf6-125">✔️</span><span class="sxs-lookup"><span data-stu-id="29bf6-125">✔️</span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="29bf6-126"><a href="submitting-an-app-to-the-microsoft-store.md"><strong>Microsoft Store</strong></a></span><span class="sxs-lookup"><span data-stu-id="29bf6-126"><a href="submitting-an-app-to-the-microsoft-store.md"><strong>Microsoft Store</strong></a></span></span></td>
    <td>❌</td>
    <td><span data-ttu-id="29bf6-127">✔️</span><span class="sxs-lookup"><span data-stu-id="29bf6-127">✔️</span></span></td>
    <td><span data-ttu-id="29bf6-128">✔️</span><span class="sxs-lookup"><span data-stu-id="29bf6-128">✔️</span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="29bf6-129"><a href="/hololens/app-deploy-store-business"><strong>商務用 Microsoft Store</strong></a></span><span class="sxs-lookup"><span data-stu-id="29bf6-129"><a href="/hololens/app-deploy-store-business"><strong>Microsoft Store for Business</strong></a></span></span></td>
    <td>❌</td>
    <td>❌</td>
    <td><span data-ttu-id="29bf6-130">✔️</span><span class="sxs-lookup"><span data-stu-id="29bf6-130">✔️</span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="29bf6-131"><a href="/hololens/app-deploy-provisioning-package"><strong>布建套件</strong></a></span><span class="sxs-lookup"><span data-stu-id="29bf6-131"><a href="/hololens/app-deploy-provisioning-package"><strong>Provisioning Package</strong></a></span></span></td>
    <td><span data-ttu-id="29bf6-132">✔️</span><span class="sxs-lookup"><span data-stu-id="29bf6-132">✔️</span></span></td>
    <td><span data-ttu-id="29bf6-133">✔️</span><span class="sxs-lookup"><span data-stu-id="29bf6-133">✔️</span></span></td>
    <td><span data-ttu-id="29bf6-134">✔️</span><span class="sxs-lookup"><span data-stu-id="29bf6-134">✔️</span></span></td>
</tr>
<tr>
    <td><span data-ttu-id="29bf6-135">HoloLens 裝置無法使用<a href="#other-scenarios"><strong>自訂的 Win32 部署</strong></a> (-請參閱以下) </span><span class="sxs-lookup"><span data-stu-id="29bf6-135"><a href="#other-scenarios"><strong>Custom Win32 deployment</strong></a> (Not available for HoloLens devices - see below)</span></span></td>
    <td><span data-ttu-id="29bf6-136">✔️</span><span class="sxs-lookup"><span data-stu-id="29bf6-136">✔️</span></span></td>
    <td><span data-ttu-id="29bf6-137">✔️</span><span class="sxs-lookup"><span data-stu-id="29bf6-137">✔️</span></span></td>
    <td>❌</td>
</tr>
</table>

> [!IMPORTANT]
> <span data-ttu-id="29bf6-138">應用程式安裝程式目前不適用於受管理的裝置，或 (第1代) 裝置的 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="29bf6-138">App Installer isn't currently available for managed devices or HoloLens (1st Gen) devices.</span></span>

## <a name="other-scenarios"></a><span data-ttu-id="29bf6-139">其他案例</span><span class="sxs-lookup"><span data-stu-id="29bf6-139">Other scenarios</span></span>

* <span data-ttu-id="29bf6-140">您可以產生 Win32。EXE 檔案：使用來自 Unity 的電腦獨立組建目標進行 Win32 應用程式部署，包括流和遊戲通過。</span><span class="sxs-lookup"><span data-stu-id="29bf6-140">You can produce a Win32 .EXE file using the PC Standalone build target from Unity for Win32 application deployment, including Steam and Game Pass.</span></span> <span data-ttu-id="29bf6-141">一旦您擁有。EXE，您可以像平常一樣將應用程式提交至您選擇的平臺。</span><span class="sxs-lookup"><span data-stu-id="29bf6-141">Once you have the .EXE, you can submit your apps as normal to your chosen platform.</span></span> 

* <span data-ttu-id="29bf6-142">如果您在離線時需要安裝 HoloLens 2 的應用程式，請參閱 [離線安全 HoloLens 2](/hololens/hololens-common-scenarios-offline-secure) 指示，或透過布建套件安裝應用程式，而不需啟用開發人員模式。</span><span class="sxs-lookup"><span data-stu-id="29bf6-142">If you need to install a HoloLens 2 application while you're offline, refer to the [offline secure HoloLens 2](/hololens/hololens-common-scenarios-offline-secure) instructions or install the app through a Provisioning Package without enabling developer mode.</span></span>

* <span data-ttu-id="29bf6-143">您也可以將組建部署到您的裝置，並與其他已啟用開發人員模式的開發人員共用，方法是 [使用 Visual Studio 部署和偵錯工具，](../develop/platform-capabilities-and-apis/using-visual-studio.md) 或 [使用裝置入口網站安裝應用程式套件](../develop/platform-capabilities-and-apis/using-the-windows-device-portal.md#sideloading-applications)。</span><span class="sxs-lookup"><span data-stu-id="29bf6-143">You can also deploy builds to your device and share them with other developers who have Developer Mode enabled by [deploying and debugging with Visual Studio](../develop/platform-capabilities-and-apis/using-visual-studio.md) or [installing an application package with the Device Portal](../develop/platform-capabilities-and-apis/using-the-windows-device-portal.md#sideloading-applications).</span></span>

## <a name="see-also"></a><span data-ttu-id="29bf6-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="29bf6-144">See also</span></span>
* [<span data-ttu-id="29bf6-145">從 Microsoft Store 尋找、安裝和卸載應用程式</span><span class="sxs-lookup"><span data-stu-id="29bf6-145">Finding, installing, and uninstalling applications from the Microsoft Store</span></span>](/hololens/holographic-store-apps)